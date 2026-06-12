---
title: "How do I know if Ubuntu installed 32 bit or 64 bit?"
date: 2014-01-21
forum: Hardware
---

### Post by michael-piziak on 2014-01-21
How do I know if Ubuntu installed 32 bit or 64 bit?
I installed 12.04 onto a 2.8 ghz core 2 duo - Ubuntu never asked which to install (32 or 64)

How can I check

---

### Post by oldfred on 2014-01-21
You download either the 32bit or 64bit version.
On my core2 duo I converted from 32bit to 64bit with 10.10.

       Also instructions for DVD or USB flash drive
[http://www.ubuntu.com/desktop/get-ubuntu/download](http://www.ubuntu.com/desktop/get-ubuntu/download)


 uname -a
i386 or i686 = 32-bit
x86_64 = 64-bit

```
fred@A105-Precise:~$ uname -a
Linux A105-Precise 3.2.0-58-generic #88-Ubuntu SMP Tue Dec 3 17:37:58 UTC 2013 [COLOR=#ff0000]x86_64[/COLOR] x86_64 x86_64 GNU/Linux

```

---

### Post by michael-piziak on 2014-01-21
Perhaps tell me a simple command to type into terminal.  I didn't download Ubuntu, I purchased the install disk from canonical

---

### Post by oldfred on 2014-01-21
As posted above in terminal. I showed command and results from my terminal.

uname -a

---

### Post by michael-piziak on 2014-01-21
My computer reports:   (what does it mean)

michael@michael-HP-Compaq-dc5800-Small-Form-Factor:~$ uname -a
Linux michael-HP-Compaq-dc5800-Small-Form-Factor 3.2.0-58-generic-pae #88-Ubuntu SMP Tue Dec 3 18:00:02 UTC 2013 i686 i686 i386 GNU/Linux
michael@michael-HP-Compaq-dc5800-Small-Form-Factor:~$

No big deal if it's 32 bits, I sure don't see the "x86_64" like yours has

---

### Post by Bashing-om on 2014-01-21
michael-piziak; Hi !

That output says you are running 32 bits; Which is absolutely fine unless you have greater than 4 Gigs of ram installed AND doing some heave duty computing. Many advocate to run 32 bit on 64 bit operating systems with less endowed ram.(runs faster)

[INDENT][INDENT][INDENT]hope this helps
[/INDENT][/INDENT][/INDENT]

---

### Post by michael-piziak on 2014-01-21
Hi to you too,

I have 4 gigs ram and am not complaining about any speed issues - I use Gimp and browsing most

---

### Post by CharlesA on 2014-01-21
Should be fine with 32bit, especially since that version is using PAE, so it should have access to all 4GB of RAM.

---

