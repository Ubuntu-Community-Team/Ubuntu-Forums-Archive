---
title: "[SOLVED] Bash script: how to display rows which appears only ones in file?"
date: 2008-08-20
forum: General Help
---

### Post by abcuser on 2008-08-20
Hi,
in Ubuntu 8.04 I have ascii file with content:
AAA
AAA
BBB
CCC
DDD
DDD

I would like to display only rows that appears only ones in a file. So BBB and CCC is result. How to write such bash script?
Thanks
Abcuser

---

### Post by ad_267 on 2008-08-20
I can't think of a way to do this in bash but it would be very simple in python:

```

#!/usr/bin/env python

infile = open("/home/username/file.txt",'r')
linelist = infile.readlines()
linelist = [line.strip() for line in linelist if linelist.count(line) == 1]
print "\n".join(linelist)

```

---

### Post by abcuser on 2008-08-20
Hi,
I have solved the problem little bit differently. I put in one file:
AAA
BBB
CCC
DDD
and in another file
AAA
DDD
then I have executed command: join -v1 file1.txt file2.txt
Thanks,
Abcuser

---

### Post by ghostdog74 on 2008-08-20
> **abcuser said:**
> Hi,
in Ubuntu 8.04 I have ascii file with content:
AAA
AAA
BBB
CCC
DDD
DDD

I would like to display only rows that appears only ones in a file. So BBB and CCC is result. How to write such bash script?
Thanks
Abcuser

```

# uniq -u file
BBB
CCC


```

---

