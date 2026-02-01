## Solution to Problem 1

(a)

The use of pi at line 4 is bound on line 3 because it is in the local 
scope of the circumference function.

The use of pi on line 7 is bound on line 1 because there is no other pi in the local scope of the area function.

(b)

The use of x at line 3 is bound at line 2, since it refers to the parameter x of the function f because it is in the 
local scope of the function.

The use of x at line 6 is bound at line 5 because there is a new variable x that takes over from the 
parameter since it is within the scope of the "case x=>" statement. 

The use of x at line 10 is also from line 5 because it is within the scope of the "case x =>" statement

The use of x at line 11 is bound at line 1, because it is not in the local scope of the function f so the only
x in scope is from line 1.
## Solution to Problem 2

(a) Execution trace:

```
def pow(x: Int, n: Int): Int =
if n > 0 then x * pow(x, n - 1) else 1

pow(2,3)
- if 3 > 0 then 2 * pow(2,2) else 1
- if true then 2 * pow(2,2) else 1
- 2 * pow(2, 2)
- 2 * (if 2 > 0 then 2 * pow(2,1) else 1)
- 2 * (if true then 2 * pow(2,1) else 1)
- 2 * 2 * pow(2,1)
- 2 * 2 * (if 1>0 then 2 * pow(2,0) else 1)
- 2 * 2 * (if true then 2 * pow(2,0) else 1)
- 2 * 2 * 2 * pow(2,0)
- 2 * 2 * 2 * (if 0>0 then 2 * pow(2,-1) else 1)
- 2 * 2 * (if false then 2 * pow(2,-1) else 1)
- 2 * 2 * 2 * 1
- 4 * 2 * 1
- 8 * 1 
- 8 

```

(b) Tail-recursive implementation

```scala
def powTailRec(x: Int, n: Int, acc: Int): Int = {
  if n == 0 then acc else powTailRec(x,n-1,acc*x)
}

def powTail(x: Int, n: Int): Int = {
  powTailRec(x, n, 1)
}

```

Execution trace:

```
powTail(2,3)
- powTailRec(2,3,1)
- if 3 == 0 then 1 else powTailRec(2,2,1*2)
- if false then 1 else powTailRec(2,2,2)
- powTailRec(2,2,2)
- if 2 == 0 then 2 else powTailRec(2,1,2*2)
- if false then 2 else powTailRec(2,1,4)
- powTailRec(2,1,4)
- if 1 == 0 then 4 else powTailRec(2, 0, 4*2)
- if false then 4 else powTailRec(2,0,8)
- if 0 == 0 then 8 else powTailRec(2, -1, 8*2)
- if true then 8 else powTailRec(2, -1, 8*2)
- 8


```