---
title: "Mount using sshfs as read-only"
date: 2008-11-08
forum: General Help
---

### Post by rich86 on 2008-11-08
Hi, just a quick (hopefully simple) question. I need to mount a directory using sshfs on a laptop from my main pc and i would like to give it read-only permissions on the laptop. Is this possible? If so how do i do it? I've had a play with -o umask=222 but that doesn't seem to work.
I really need answer asap as need it for tonight.

Thanks in advance,
Richard

---

### Post by kidders on 2008-11-09
Hi there,

Try the "ro" mount option.

---

### Post by rich86 on 2008-11-09
Thanks for that it worked, i don't know why i didn't think of that, apart from it wasn't mentioned in the manual for sshfs. Thanks again.

---

### Post by chowanec on 2010-07-04
yeah -- that is pretty silly indeed.  I spent hours searching the web for this to end it on:

```

sshfs -o idmap=user -o ro user@example.com:public_html/ /home/chow/Website/

```

The important bit is the **-o ro** part if anyone else is looking for this in the future.

-Chow

---

### Post by Azyx on 2011-05-26
:) also didn't think about it and didn't find it in manual :)

---

