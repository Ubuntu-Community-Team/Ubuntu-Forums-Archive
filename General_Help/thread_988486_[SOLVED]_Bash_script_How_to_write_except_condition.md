---
title: "[SOLVED] Bash script: How to write except condition between two files"
date: 2008-11-20
forum: General Help
---

### Post by abcuser on 2008-11-20
Hi,
on Ubuntu 8.10 I would like to write bash script to get all the values from first file that are not already existing in second file.

First file:
```

A
B
C

```

Second file:
```

B
C

```

Because value A is only in first file and does not exists in second file, that is desired value.

The result of script should be:
A

How to write such a bash script?
Regards,
Abcuser

---

### Post by Idefix82 on 2008-11-20
What do you mean by "values"? Words or lines? Or is it the same in your case since there is only one word per line?

---

### Post by abcuser on 2008-11-20
Hi,
I have solved the problem:
```
cat file1.txt | grep -v "$(cat file2.txt)"
```
Regards,
Abcuser

---

### Post by Idefix82 on 2008-11-20
A different way of solving it is to use the comm command which is made exactly for this case, but it needs the files to be sorted:
```
comm -23 <(sort file1.txt | uniq) <(sort file2.txt | uniq)
```
See man comm for the meaning of -23.

---

### Post by amauk on 2008-11-20
```
diff ./file1 ./file2 | grep '^<' | sed 's/< //g'
```

---

### Post by abcuser on 2008-11-20
> **abcuser said:**
> 
```
cat file1.txt | grep -v "$(cat file2.txt)"
```

Hi,
above command works fine if file2 is not empty. But if file2 is empty no result is returned. Any idea why?

And by the way, sorry, I have two variables to compare not two files...
Regards,
Abcuser

---

### Post by Idefix82 on 2008-11-20
I haven't tested amauk's code but if it works then it will equally well work with variables instead of files:
```
diff <(echo "$var1") <(echo "$var2") | grep '^<' | sed 's/< //g'
```
or alternatively write each variable into a file first, separating values by line breaks (easy using sed) and then run the code I have given you above.

---

### Post by abcuser on 2009-05-03
Hi,
just to let you know diff is not the best solution for this problem, because diff can return c-change, a-add or d-delete. Script above presumes diff always returns c which is wrong.

Solution is to use comm command. I have used the following command:
```

comm -23 <(echo "$var1" | sort -u) <(echo "$var2" | sort -u)

```
Regards

---

