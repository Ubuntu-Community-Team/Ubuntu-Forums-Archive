---
title: "32 bit or 64 bit"
date: 2008-03-10
forum: Hardware &amp; Laptops
---

### Post by starfunker on 2008-03-10
I'm due to fit a new graphics card (Geforce 8800 GT) this week and I'll need to download the correct drivers.  I read that I'll need to make sure that I download the right ones depending on whether I have a 32 bit or 64 bit system.  Is there a simple way to find this out?  I've checked my documentation from  the shipping materials and I can't find it listed anywhere.

---

### Post by boredtechie on 2008-03-10
Hi,

I'm new myself but you could try typing the following at the terminal:

uname -a

Which should give you something like:

Linux host 2.6.22-14-generic #1 SMP Tue Feb 12 02:46:46 UTC 2008 [COLOR="Red"]x86_64[/COLOR] GNU/Linux

I've only got 64 bit systems but I'd expect a 32 bit system to kick out something like x86_32 in place of my x86_64.

Kind regards
saltera

---

### Post by Rocket2DMn on 2008-03-10
Where yours says "x86_64", it can appear for 32 bit systems as "i686" or some variety of that, like "i386" if you're using a kernel that doesn't autoadjust to 686 machines.

---

### Post by mrsteveman1 on 2008-03-10
Isn't this something the restricted driver manager can handle?

---

### Post by Rocket2DMn on 2008-03-10
> **mrsteveman1 said:**
> Isn't this something the restricted driver manager can handle?

Normally, yes, the OP should try that first.  I've been handling a number of threads recently with people having trouble getting their nvidia cards working correctly, perhaps because the drive Ubuntu gives is outdated.  Installing from nvidia's site can be rough, but if the OP is up to it, we can help out.

---

### Post by Ozzz on 2008-03-11
> **Rocket2DMn said:**
> Where yours says "x86_64", it can appear for 32 bit systems as "i686" or some variety of that, like "i386" if you're using a kernel that doesn't autoadjust to 686 machines.

I don't want to hijack this thread but I have been trying to determine which mine is as well, 32 or 64 bit. I want to install drivers for my cd/dvd player and I need to know this. I got the following results:
```
 uname -a
Linux trg-laptop 2.6.22-14-generic #1 SMP Tue Feb 12 07:42:25 UTC 2008 i686 GNU/Linux

```

---

### Post by jocko on 2008-03-11
> **Ozzz said:**
> I don't want to hijack this thread but I have been trying to determine which mine is as well, 32 or 64 bit. I want to install drivers for my cd/dvd player and I need to know this. I got the following results:
```
 uname -a
Linux trg-laptop 2.6.22-14-generic #1 SMP Tue Feb 12 07:42:25 UTC 2008[COLOR=Red] i686[/COLOR] GNU/Linux

```
That means you have a 32 bit os installed (otherwise it would say x86_64 instead of i686, as Rocket2DMn said a few posts ago).

---

### Post by Ozzz on 2008-03-11
> **jocko said:**
> That means you have a 32 bit os installed (otherwise it would say x86_64 instead of i686, as Rocket2DMn said a few posts ago).

Thanks. Guess I didn't enough coffee yet this morning to understand his post fully. Now I know. Appreciate your help.

---

### Post by starfunker on 2008-03-13
Thank you, that's a great help.

---

