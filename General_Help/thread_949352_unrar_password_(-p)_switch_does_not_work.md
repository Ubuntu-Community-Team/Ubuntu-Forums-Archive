---
title: "unrar password (-p) switch does not work"
date: 2008-10-16
forum: General Help
---

### Post by markus.s on 2008-10-16
hi,

i have a problem with a small script, where i want to use unrar with the password switch.

eg.: 
[FONT="Courier New"]unrar x -pMYPASS MYFILE.rar 
Encrypted file:  CRC failed in MYFILE.rar (password incorrect ?)
No files to extract[/FONT]

**without the switch (-p) the same password works!!!**

[FONT="Courier New"]unrar x MYFILE.rar
Enter password (will not be echoed) for MYFILE.rar:MYPASS

Extracting from MYFILE.rar

Extracting  file1.ext                                     OK 
Extracting  file2.ext                                     OK [/FONT]

i also tested with other switches (eg. -kb) in kombination


thx
markus

---

### Post by markus.s on 2008-10-17
further tests:

installer/rar/rar a -pTEST test.rar bin
[...]
unrar x -pTEST test.rar test

... is working

may there are problems because of special characters in the original password, which is Cw$eaf0ddn?

---

### Post by markus.s on 2008-10-17
the original problem file is ecrypted with the -hp option

rar: hp[password]  Encrypt both file data and headers

i also tested positive with this option

---

### Post by markus.s on 2008-10-20
no ideas?
nobody?

---

### Post by mali2297 on 2008-10-20
> **markus.s said:**
> further tests:

installer/rar/rar a -pTEST test.rar bin
[...]
unrar x -pTEST test.rar test

... is working

may there are problems because of special characters in the original password, which is Cw$eaf0ddn?

I think the dollar sign causes problem. Try putting the password in single quotes:
```

unrar x -p'Cw$eaf0ddn' MYFILE.rar 

```

---

### Post by markus.s on 2008-10-20
thx for reply!

yes, i agree
i also think the dollar sign is responsible

i tested:
* -p'Cw$eaf0ddn'
* -p"Cw$eaf0ddn"
* -pCw\$eaf0ddn

unfortunately without positive results ...

---

### Post by mali2297 on 2008-10-20
> **markus.s said:**
> thx for reply!

yes, i agree
i also think the dollar sign is responsible

i tested:
* -p'Cw$eaf0ddn'
* -p"Cw$eaf0ddn"
* -pCw\$eaf0ddn

unfortunately without positive results ...

Have you tried this?
```

'-pCw$eaf0ddn'

```

---

### Post by markus.s on 2008-10-21
hmmm

the solution:
it was a simple text conversion problem.
the password is in a textfile (edited in ms windows).

"In Windows, lines end with both the line feed and carriage return ASCII characters"

perl -p -e 's/\r$//' < winfile.txt > unixfile.txt

and all works fine ...

thank you mali2297 for your help and hints

markus

---

