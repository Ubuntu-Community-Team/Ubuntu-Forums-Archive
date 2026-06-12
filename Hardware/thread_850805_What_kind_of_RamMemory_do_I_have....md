---
title: "What kind of Ram/Memory do I have..."
date: 2008-07-06
forum: Hardware
---

### Post by morbid_bean on 2008-07-06
yes, a rather odd question but i forgot what kind of ram my pc uses and i had found that out by using Crucial.com...however it only works in windows and i no longer use that black abyss of an OS...how can I find out the type of ram i got so i can upgrade!?

---

### Post by Bubba64 on 2008-07-06
> **morbid_bean said:**
> yes, a rather odd question but i forgot what kind of ram my pc uses and i had found that out by using Crucial.com...however it only works in windows and i no longer use that black abyss of an OS...how can I find out the type of ram i got so i can upgrade!?

I don't know the terminal code to get that info but if you look your computer up on Google you can probably recognize the right info when you find it. You can also post your set up chances are somebody on the forums has the same set up. Here is a link that may help.
[http://www.cyberciti.biz/tips/how-much-ram-does-my-linux-system.html](http://www.cyberciti.biz/tips/how-much-ram-does-my-linux-system.html)
[http://forums.devshed.com/linux-help-33/check-the-amount-of-ram-52677.html](http://forums.devshed.com/linux-help-33/check-the-amount-of-ram-52677.html)

---

### Post by phidia on 2008-07-06
> **morbid_bean said:**
> yes, a rather odd question but i forgot what kind of ram my pc uses and i had found that out by using Crucial.com...however it only works in windows and i no longer use that black abyss of an OS...how can I find out the type of ram i got so i can upgrade!?

[This site]("http://www.4allmemory.com/index.cfm?pid=473&kwd=memory%20exact&gclid=CKHE5s3qmZQCFQECGgodcSUI7w") will determine what ram type your computer uses.

---

### Post by sdennie on 2008-07-06
You might be able to find what you are looking for with:

```

sudo dmidecode --type memory

```

---

### Post by kaligus on 2008-07-06
what did I break?

How do I fix it?

```
will@bigwill:~$ sudo dmidecode --type memory
# dmidecode 2.9
SMBIOS 2.2 present.

Invalid entry length (0). DMI table is broken! Stop.

will@bigwill:~$ 

```

Oh and do I really care that it is broken?

---

### Post by sdennie on 2008-07-06
> **kaligus said:**
> what did I break?

How do I fix it?

```
will@bigwill:~$ sudo dmidecode --type memory
# dmidecode 2.9
SMBIOS 2.2 present.

Invalid entry length (0). DMI table is broken! Stop.

will@bigwill:~$ 

```

Oh and do I really care that it is broken?

You probably didn't break anything.  Your BIOS just isn't reporting standard information.  It's not really a problem.  An alternative that might show you interesting information would be:

```

sudo lshw -C memory

```

---

### Post by kaligus on 2008-07-06
> **vor said:**
> You probably didn't break anything.  Your BIOS just isn't reporting standard information.  It's not really a problem.  An alternative that might show you interesting information would be:

```

sudo lshw -C memory

```

lshw from 'System Rescue CD' is my usual means of getting info, dmidecode is a new toy to play with and when I flipped an error I just needed to make sure I didn't break something with my fiddling with the gooey bits ;)

Thank you for the rapid response!

---

