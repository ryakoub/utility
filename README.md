# Assignment 1: Parsing a String

Given a string that could take one of these two formats:

```text
form1_str = "var = val1, val2, val3, x = val, rz = var, ..."
form2_str = "var = val1, val2, val3, x = val y = val rz = var, ..."
```

Each `val` in the expression is a float value except for the parameters `var, x, y, rz, ...`

Write a Python class satisfying the following requirements:

1. The class is initialized with the input string as a class member
2. Add a function to parse the string following these rules:

    a. The substring `var` appears in the beginning is parsed out and assigned to a member of the class of string type
  
    b. The `val1, val2, val3` are parsed out to floats and assigned as a tuple member of the class
    
    c. Whatever comes after `val3,` should be combined as a subexpression separated by comma even if space is used as in `form2_str`.  The comma should be used to separate a pair of parameter-value which is defined as `x = something`, `y = something`, ..., etc.  The sub expression should be assigned to a class member of string type.
2. Add a class member function to print the parsed parts
2. The program should be tested out using some sample examples like:
  ```text
    sample1 =  "var = 2, 15, 0.5, x = 2, rz = var, y = 30"
    sample2 =  "s = -2, -15, -0.5, x = 2, rz = s y = 30"
    sample3 =  "theta = 2, 15, 0.05, x = 2 rz = theta, y = 30 z = 10"
    sample4 =  "d = 20, 15, -0.01, x = 2 rz = var y = 30*d"
    ...
  ```

The expected output of `sample3` should be:
```Python
o.var = 'theta'
o.vals = (2,15,0.05)
o.subexpr = 'x = 2, rz = theta, y = 30, z = 10'
```  
where `o` is an instance of the class object.

# Assignment 2: Finding Rotation Sequence

Given a 3D vector defined by the Cartesian components $x, y, z$, it is required to write a Python algorithm to find the rotation sequence that a coordinate frame would make to have its $z$ axis aligned with the given vector.  For examples, $(1,0,0)$ represents the $x$ in the original frame, in order for the $z$ axis to be aligned with it, the coordinate frame has to rotate $90^o$ around the $y$ axis, i.e `ry = 90`.  Another example $(0,1,0)$ should lead to `rx = -90`.  The algorithm must satisfy the following rules:
1. Assume the given 3D vector is not normalized
2. The sequence of rotation is around the new generated frame.  For example, if 2 rotations are needed, the second rotation is performed on the results of the previous operation, i.e `rx = 45, rz = 90`, the first rotation is performed on the original frame $x$ by $45^o$, then the new frame goes through another rotation around its own (new) $z$ axis by $90^o$.
3.  There shouldn't be redundant rotations, i.e. `rx = 90, rx = -90` is redundant.  The maximum number of rotation in a sequence is 2, if your algorithm yields 3 or more rotations, this is an indication that you have unnecessary operations or there is a bug.
4. The output of the algorithm should be in degrees defined in a rotation sequence as `rotation_sequence(rx = , ry = , rz =)`.  The order of the rotation must be preserved.
5. Add several unit tests to verify the math.

**Bonus:** Visualize the given 3D vector and the rotation sequence for the original frame has to make to get is $z$ axis aligned with the input vector.

# General Rules
1. Do not copy other people code even if it is in the public domain.  You may consult web resources to understand algorithms but implement your own.
2. Please be clear in your commit history and add documentation is this file or in the code.
