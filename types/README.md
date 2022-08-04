I was asked to write something about types and type theory even though I am not
an expert. I am a mathematician, not a type theorist, but because of my
extensive experience with types and type theory, I can confidently claim to be
an expert *user* of type theory.

Here I will give an informal introduction to types in general, and dependent types
in particular, from the perspective of someone who has used them extensively.

## What is a type?

That's a tough question, even for experts. It's a bit like asking "what is a
set?"  And if you have any intuition about sets, and the set membership relation (∈),
and you allow that to guide your intuition about types, and the type
membership relation (:), then I suspect nothing really terrible will happen to
you as a result (at least that has been my experience).

In the beginning, types were invented as a way to avoid the paradox that arises
in set theory if you take everything---even the collection of all sets---to be
a set.  (If you do that, then there's no way to decide whether the following
set X = { S | S ∉ S } contains.  If you think X ∈ X, then you're wrong,
since the condition of belonging to X is X ∉ X. If you think X ∉ X, then X ∈ X
and your wrong again!)

This is called Russel's Paradox and, in set theory, we avoid it by using the
term *set* only for collections that are "small" in some sense, and we use the
term *class* for collections that are too large to be a set (e.g., the
collection of all sets).

In type theory, by contrast, we have a hierarchy of collections of types.
The "base" types, which I'll label Type₀.  We throw into Type₀ types like `int`
(ℤ) or `nat` (ℕ), etc.  At the next level we have Type₁.  These are the types
that are built out of the types in Type₀.  From there we build types in the
collection Type₂, and so on, until we have a hierarchy of types.

Now, I know what you're thinking at this point.  You want to know whether this
hierarchy of types is "ramified," don't you?  That is, you're wondering whether
the following subset relations hold: Type₀ ⊆ Type₁ ⊆ Type₂ ⊆ ⋯  Great question,
thanks! But this is pretty technical and we don't need to settle it right now.
(Spoiler: in Coq "yes," in Agda "no.") 

## Syntax

### Every type belongs to a type

We write A : Typeᵢ to denote that the type A *has type* Typeᵢ.  We could also
say that "A inhabits Typeᵢ" or that "A is a type at universe level i."  In this
way, everything has a type. If we don't care about what universe level A
inhabits, and we just want to say that A is a type, we can write A : Type,
keeping in mind that there really is some (implicit) subscript on Type.

Now, suppose we start with a type, say, A : Type.  If A is not the *empty type*, then
there are *members* (or *elements* or *inhabitants*) of the type A and we write
x : A to denote that x *inhabits* the type A. We can also simply say "x has type A."

## Polymorphic and Dependent Types

A **polymorphic type** is a type that depends on another type.  Familiar examples
are lists (e.g., List[String], List[Int], List[Float], etc.).  Informally, we
might call List[_] a "type former"---it forms a type once we give it another
type inside the brackets.

In contrast, a **dependent type** is a type that depends on an *inhabitant* of
another type.  For example, if n is an integer (n : Int), then we might
represent the type of lists of integers of length n by List[Int] n.

Dependent types are *extrememly* useful and using them can be an unreasonably
satisfying experience. I'll show some examples below.  Unfortunately, while most
popular languages support polymorphic types, very few support dependent types.

...to be continued...

