---
title: "extracting usernames from a text file with sed/awk"
date: 2008-07-18
forum: General Help
---

### Post by x3roconf on 2008-07-18
I have a text file which contains a lot of usernames in this form

twhr34: x:1160:1150::/home/twhr34:/bin/bash cchy8: x:1161:1151::/home/cchy8:/bin/bash mugea: x:1162:1151::/home/mugea:/bin/bash svyy96: x:1163:1126::/home/svyy96:/bin/bash bnp5x4: x:1164:1153::/home/bnp5x4:/bin/bash twt24:x:1165:1154::/home/twt24:/bin/bash ard3k5:x:1166:1155::/home/ard3k5:/bin/bash sed5g9: x:1167:1157::/home/sed5g9:/bin/bash muic: x:1168:1158::/home/muic:/bin/bash vuc5gd: x:1169:1158::/home/vuc5gd:/bin/bash abdhf: x:1170:1159::/home/abdhf:/bin/bash dmgdg5:x:1171:1160::/home/dmgdg5:/bin/bash djmc48: x:1172:1160::/home/djmc48:/bin/bash mizzouforte: x:1173:1173::/home/mizzouforte:/bin/bash grsm84: x:1174:1174::/home/grsm84:/bin/bash macz7b: x:1175:1175::/home/macz7b:/bin/bash cjm6w3: x:1176:1175::/home/cjm6w3:/bin/bash ilggdd:x:1177:1019::/home/ilggdd:/bin/bash spamd:x:334:334::/var/log/spamd:/sbin/nologin lsgr: x:1178:1178::/home/lsgr:/bin/bash ssc: x:1179:1179::/home/ssc:/bin/bash

How i can extract usernames using sed or awk?

---

### Post by haegl on 2008-07-18
cat /etc/passwd | sed -e 's/^\([^:]*\).*/\1/'

---

### Post by stumac on 2008-07-18
You could try this instead of sed/awk

 ~$ cat datafile | cut --delimiter=: --fields=1

---

### Post by x3roconf on 2008-07-18
[QUOTE=| sed -e 's/^\([^:]*\).*/\1/'[/QUOTE]

for some reason this returns only 'root' and cut --delimiter=: --fields=1
has same problem. :(

---

### Post by stumac on 2008-07-18
oops.  Didn't look at the file properly.  This is a copy of a passwd file without the linefeeds and with a space after the first : delimiter.  Is this correct? Why not use the passwd file and the suggestions made?

Stumac

---

### Post by haegl on 2008-07-18
try this
```
sed -e 's/\([^:]*\)\(:[^:]*\)\{5\}\(:[^ ]* \)/\1\n/g'
```

---

### Post by x3roconf on 2008-07-18
> **stumac said:**
> oops.  Didn't look at the file properly.  This is a copy of a passwd file without the linefeeds and with a space after the first : delimiter.  Is this correct? Why not use the passwd file and the suggestions made?

Stumac

I don't have the original passwd file. There are no linefeeds but NO space
after the first : delimiter (i added it).

---

### Post by x3roconf on 2008-07-18
> **haegl said:**
> try this
```
sed -e 's/\([^:]*\)\(:[^:]*\)\{5\}\(:[^ ]* \)/\1\n/g'
```

That worked. Thank you very much!

---

### Post by haegl on 2008-07-18
:)

---

### Post by lswb on 2008-07-18
It looks like the text you posted is /etc/passwd but it has wrapped improperly when cut & pasted to the forum, so assuming it really is just /etc/passd, couldn't you just use

  cut -d : -f 1 </etc/passwd

---

### Post by haegl on 2008-07-18
> **lswb said:**
> It looks like the text you posted is /etc/passwd but it has wrapped improperly when cut & pasted to the forum, so assuming it really is just /etc/passd, couldn't you just use

  cut -d : -f 1 </etc/passwd

Give him a break, it's probably a homework and has to be done this way :P

---

### Post by x3roconf on 2008-07-18
> **lswb said:**
> It looks like the text you posted is /etc/passwd but it has wrapped improperly when cut & pasted to the forum, so assuming it really is just /etc/passd, couldn't you just use

  cut -d : -f 1 </etc/passwd

Like i said i have no original /etc/passwd file and this file was wrapped
improperly before i pasted it to forum.

---

### Post by x3roconf on 2008-07-18
> **haegl said:**
> Give him a break, it's probably a homework and has to be done this way :P

No it was no homework. :)

---

### Post by ghostdog74 on 2008-07-18
just personal taste, using sed with a lot of regular expression syntaxes really make code ugly and difficult to debug whens sh** happens.
@OP, for structured data such as those coming from /etc/passwd (i suppose) with fixed delimiters, you can use awk (or cut) with deals with fields effectively.
```

awk -F":" '{print $1}' /etc/passwd

```

---

