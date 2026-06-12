---
title: "[SOLVED] How to get file names that has numbers, English characters and underscore?"
date: 2008-08-16
forum: General Help
---

### Post by abcuser on 2008-08-16
Hi,
in Ubuntu 8.04 from bash shell I would like to get all files using ls command that has the following characters in files name:
0-9 (all numbers)
a-z (only lower English alphabeth)
A-Z (only upper English alphabeth)
_ (underscore)

I know this can be done using regular expressions something like:
ls [0-9a-zA-z_]
but I can't figured out exact sintax.
Thanks,
Abcuser

---

### Post by scragar on 2008-08-16
```
ls | grep [0-9a-zA-z_]
```
will fetch file names one or more of those chars in.

---

### Post by abcuser on 2008-08-16
scragar, you command also displays files that uses spaces and other special characters. Check this out:
touch "my file ? * +-.txt"

I would just like to get numbers and English uppper/lower characters and underscore in file names.

---

### Post by scragar on 2008-08-16
if you only want those characters and nothing else use:
```

ls | grep ^[0-9a-zA-z_]*\$

```
the ^ means the start of the line
the \$ means the end of the line.
the * means any number, it's interchangeable with the +, but for some reason * is a tiny bit faster in this case.

---

### Post by abcuser on 2008-08-16
scragar, have you tried this out. It doesn't display any file at my terminal.

---

### Post by scragar on 2008-08-16
I tested it in a new directory on my system with the following file names:
```
Mixed
lower
UPPER
with_underscore
l33t
l33t_scored
dont match me
text.txt
```
and it lists
```
Mixed
lower
UPPER
with_underscore
l33t
l33t_scored
```
I did have to correct the case on a certain letter first though, sorry about earlier, I hadn't noticed it since I just copy and pasted your code with a couple of edits.```
ls | grep ^[0-9a-zA-**Z**_]*\$
```

---

### Post by abcuser on 2008-08-16
Hi,
in above code also non-English characters are displayed (this is what I don't like). Check:
touch "&#273;" (Slavic languages)
touch "&#353;" (Slavic languages)
touch "ü" (German)
touch é (French)

I changed you code to:
```
ls | grep ^[0-9abcdefghijklmnopqrstuvxyzABCDEFGHIJKLMNOPQRSTUVYXZ_]*\$
```
and now I think it works like I want.

Is there any short command for "abcdefghijklmnopqrstuvxyz" and "ABCDEFGHIJKLMNOPQRSTUVYX" so only English characters?
Thanks,
Abcuser

---

### Post by scragar on 2008-08-16
that's what a-zA-Z should be... I suppose you could half the length:
```
ls | grep -i ^[0-9abcdefghijklmnopqrstuvxyz_]*\$
```

I'm not sure how it would do against those characters, but try:
```
ls | grep ^[[:alnum:]_]*\$
```

---

### Post by abcuser on 2008-08-16
Hi,
it looks like [:alnum:] behaves the same way as "a-zA-Z" combination, so it also displays non-English characters.

So it looks like that there is only "all-letters" option that works like I want.

Don't bother any more. It is little more code, but it is working.
Thanks very much for help,
Abcuser

---

