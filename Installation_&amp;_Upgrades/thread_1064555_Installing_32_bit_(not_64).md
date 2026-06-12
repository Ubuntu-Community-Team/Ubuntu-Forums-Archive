---
title: "Installing 32 bit (not 64)"
date: 2009-02-08
forum: Installation &amp; Upgrades
---

### Post by Taigen on 2009-02-08
Ok I want to install 32 bit version of ubuntu, however my processor is a 64 bit processor, and I think ubuntu automatically switches to 64bit upon installation. Is this correct or not? And how can I fix this. I am currently using the 64 bit but would rather use the 32 bit. Oh and is there a way just to switch with out having to redownload again. Thanks

---

### Post by SuperSonic4 on 2009-02-08
No it's not correct, getting the 32 bit version will keep the 32bit version. You will have to download another iso if you want 32bit

```
uname -a
``` will tell you if you have 64 bit or 32bit

---

### Post by Taigen on 2009-02-09
nope it says its 64 bit: 

Linux ubuntu 2.6.27-11-generic #1 SMP Thu Jan 29 19:28:32 UTC 2009 x86_64 GNU/Linux

And I know both time I have installed ubuntu I selected 32 bit.. I think there is some auto bit selection upon installation, I was wondering if I can install 32 bit anyway, all the programs I want to use are 32 bit only.. thanks

---

### Post by Taigen on 2009-02-12
I just need the 32 bit for most of my programs and though I can code them in and install them on 64 bit its kind of a pain.. id rather switch to 32 bit if anyone can help.

Oh and I installed w/ vista if that helps anyone..

---

### Post by jrusso2 on 2009-02-12
You choose either a 64 bit installer or a 32 bit installer unless your doing Wubi which you should mention we can't read minds yet although I have gotten better at it on these forums.

---

### Post by howefield on 2009-02-12
> **Taigen said:**
> And I know both time I have installed ubuntu I selected 32 bit.. I think there is some auto bit selection upon installation,. thanks

Is this a Wubi install by any chance ?

---

### Post by Taigen on 2009-02-12
Well I selected 32 bit installation, and it installed 64 bit. So then I had my friend who is an 32 bit ubuntu user, give me the link and I downloaded and installed it, and same thing happened. Here is the place where I downloaded.

[http://www.ubuntu.com/getubuntu/download](http://www.ubuntu.com/getubuntu/download)

---

### Post by jrusso2 on 2009-02-12
We are both asking if you did a Wubi install?

---

### Post by Taigen on 2009-02-12
hmm im kind of a noob with it. I installed with windows vista then I rebooted and it did its own thing.

---

### Post by howefield on 2009-02-12
If it is a WUbi install, have a read at the Q&A here...

[https://wiki.ubuntu.com/WubiGuide#head-f08a3f4a79668f448aa172983f369799d9d1a008](https://wiki.ubuntu.com/WubiGuide#head-f08a3f4a79668f448aa172983f369799d9d1a008)

---

### Post by jrusso2 on 2009-02-12
Did you make partitions? Install into the empty space on the drive?

Or install on top of Windows?

---

### Post by Taigen on 2009-02-12
hmm I used i believe the instal shield, and no I ddint set up a partition before han but i think I went though some partition thing in install shield. From sound of it I need to download a wubi installer and install w/ wubi?

---

### Post by Taigen on 2009-02-12
Ok i looked at photos of a wubi installation and yes I did install with wubi

P.S. thanks for your replies

---

### Post by Taigen on 2009-02-12
Oh i just read in the link given by howefield this:

Can I force Wubi to download and install a 32 bit version of Ubuntu?

Yes either pre-download the appropriate 32 bit ISO manually and place it in the same folder as Wubi.exe or start Wubi with the "--32bit" argument.

---

### Post by Taigen on 2009-02-12
thank you all for your help

---

### Post by Taigen on 2009-02-13
Thank you all for you help and support. I did a force 32 bit install and it worked great thanks again.

---

