## Sum of all elements algorithm

```
ALGORITHM SumDistinctElements
VAR
    set1: ARRAY OF INTEGER := [3, 1, 7, 9];
    set2: ARRAY OF INTEGER := [2, 4, 1, 9, 3];
    i, j: INTEGER;
    found: BOOLEAN;
    sum: INTEGER := 0;
BEGIN
    // Check elements in set1 not present in set2
    FOR i := 0 TO LENGTH(set1) - 1 DO
        found := FALSE;
        FOR j := 0 TO LENGTH(set2) - 1 DO
            IF set1[i] = set2[j] THEN
                found := TRUE;
                BREAK;
            END_IF
        END_FOR;
        IF NOT found THEN
            sum := sum + set1[i];
        END_IF
    END_FOR;

    // Check elements in set2 not present in set1
    FOR i := 0 TO LENGTH(set2) - 1 DO
        found := FALSE;
        FOR j := 0 TO LENGTH(set1) - 1 DO
            IF set2[i] = set1[j] THEN
                found := TRUE;
                BREAK;
            END_IF
        END_FOR;
        IF NOT found THEN
            sum := sum + set2[i];
        END_IF
    END_FOR;

    Write(sum); // Output: 13
END
```

## The algorithm determines orthogonality using procedural.

```
PROCEDURE dot_product(v1, v2: ARRAY OF REAL; VAR ps: REAL);
VAR
    i: INTEGER;
BEGIN
    ps := 0;
    FOR i := 0 TO LENGTH(v1) - 1 DO
        ps := ps + (v1[i] * v2[i]);
    END_FOR;
END;

ALGORITHM CheckOrthogonality
VAR
    n, i: INTEGER;
    vectors: ARRAY[1..n] OF RECORD
        v1, v2: ARRAY OF REAL;
    END;
    ps: REAL;
BEGIN
    FOR i := 1 TO n DO
        // Assume vectors[i].v1 and vectors[i].v2 are initialized
        dot_product(vectors[i].v1, vectors[i].v2, ps);
        IF ps = 0 THEN
            WriteLn("Pair ", i, ": Orthogonal");
        ELSE
            WriteLn("Pair ", i, ": Not orthogonal");
        END_IF;
    END_FOR;
END;
```
