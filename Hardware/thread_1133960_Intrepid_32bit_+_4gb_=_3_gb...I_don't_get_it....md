---
title: "Intrepid 32bit + 4gb = 3 gb...I don't get it..."
date: 2009-04-23
forum: Hardware
---

### Post by Prosis on 2009-04-23
Hello

I just installed a two 2gb ram in my computer.  I'm on Ubuntu 8.10 (Intrepid).

But since it's a 32 bit system, I can only see 3.  But I paid for 4 so I want 4 lol.  So, given that a 64 bit Ubuntu would pretty much use more RAM and therefore wouldn't make a huge difference, I've tried this:

```
sudo apt-get install linux-headers-server linux-image-server linux-server
```

Then booted with this kernel but that didn't work either which is bizarre.

What can I do?

Thanks :)

---

### Post by Marlonsm on 2009-04-23
Any computer with a 32-bit OS is limited to around 3.2Gb, it's not only Ubuntu.

If you want to use the 4Gb of RAM, you'll need a 64-bit OS.

---

### Post by Bateluer on 2009-04-23
> **Marlonsm said:**
> Any computer with a 32-bit OS is limited to around 3.2Gb, it's not only Ubuntu.

If you want to use the 4Gb of RAM, you'll need a 64-bit OS.

Yep, this applies to ALL 32 bit operating systems. If you want the full 4GB, you're going to need the 64 bit version.

---

### Post by finer recliner on 2009-04-23
details:

[http://www.codinghorror.com/blog/archives/000811.html](http://www.codinghorror.com/blog/archives/000811.html)


yes the article focuses on Windows, but before all the windows haters chime in -- note this excerpt:
> To be perfectly clear, this isn't a Windows problem-- it's an x86 hardware problem. The memory hole is quite literally invisible to the CPU, no matter what 32-bit operating system you choose.

---

### Post by Prosis on 2009-04-23
Thanks all, but I have a question

Wouldn't the 64 bit version of Ubuntu use more RAM?

---

### Post by gfd on 2009-04-23
> **Prosis said:**
> But since it's a 32 bit system, I can only see 3.  But I paid for 4 so I want 4 lol.  So, given that a 64 bit Ubuntu would pretty much use more RAM and therefore wouldn't make a huge difference, I've tried this:

```
sudo apt-get install linux-headers-server linux-image-server linux-server
```

Then booted with this kernel but that didn't work either which is bizarre.


I have the same problem but haven't installed the server kernel yet.
Have you managed to get Ubuntu to recognise the full 4GB of RAM?

If I install the server kernel, will I have to change anything else to my system? Am I correct to believe that using the 32bit applications won't hurt?

Thanks

---

### Post by Prosis on 2009-04-23
It didn't change anything other than the weather applet crashing (which is minimal...)

But it didn't recognize the 4 gig either :(

---

### Post by Barry Carroll on 2009-04-24
My install of x64 Jaunty on my server machine is shown to be using about 560MB of RAM after booting the desktop and logging in and that's pretty similar to my x32 machine as well.

I'd weigh up if that 800MB was really really valuable to you and decide on a x64 upgrade then.  I know that there's the element of wanting to use it because you paid for it but sometimes it's better to keep your stable x32 based OS rather than leap to x64.

---

### Post by Marlonsm on 2009-04-24
> **Barry Carroll said:**
> My install of x64 Jaunty on my server machine is shown to be using about 560MB of RAM after booting the desktop and logging in and that's pretty similar to my x32 machine as well.

I'd weigh up if that 800MB was really really valuable to you and decide on a x64 upgrade then.  I know that there's the element of wanting to use it because you paid for it but sometimes it's better to keep your stable x32 based OS rather than leap to x64.

Actually it seems that 64 bits is now as stable as 32 bits.
I'm downloading Jaunty 64 bits although I only have 2Gbs of RAM.

---

### Post by Barry Carroll on 2009-04-24
Cool, good luck ;) I didn't mean that jaunty x64 was unstable, more that you might run into some unforeseen issues with drivers and apps so don't go formatting your x32 install too hastily :)

---

### Post by Mortus Pryde on 2009-04-24
Yes the 3.2GB limit IS hardware related, you can only address so many memory addresses within 32bits. It is really the differance between how many unique number combinations can you get out of 4 digits as aposed to 8 digits? This is why computers went from 8bit to 16bit to 32bit, the more bits you have, the longer your instructions can be in binary, this means more memory can be addressed and more complex instructions can be communicate in less steps.

---

### Post by Prosis on 2009-04-24
So on 32 bit system recent enough to use the 64 bit version, would I be better off installing the 64 bit?  What's the difference?

---

### Post by finer recliner on 2009-04-24
> **Prosis said:**
> So on 32 bit system recent enough to use the 64 bit version, would I be better off installing the 64 bit?  What's the difference?

maybe i'm misreading this, but it sounds like you said you have a 32bit computer. You NEED a 64-bit processor to install 64-bit software and 64-bit operating systems. Trying to install such software on a 32-bit system won't work. 

to put it simply: a 64-bit processor can execute much more complicated instructions per clock cycle than a 32-bit processor does. So it works faster and more efficiently. You dont get anything special out of 64-bit software other than better performance.

---

### Post by Prosis on 2009-04-25
Oh, I was told that recent processors could handle 64 bit systems...I was also able to boot with Jaunty's 64 bit LiveCD so I thought I could install it...

---

### Post by Barry Carroll on 2009-04-25
Ah, if you could boot the live cd you have a 64-bit processor so you can go ahead and install!  You can check out some lists if 64 bit processors here: [http://en.wikipedia.org/wiki/X86-64](http://en.wikipedia.org/wiki/X86-64)

---

### Post by Prosis on 2009-04-25
Hey I've had a 64 bit processor for 2 years and I didn't know lol!

My processor is an Intel Core 2 Duo so it's X86-64!

Alrighty Jaunty 64 bit, here I come! :D

---

### Post by lisati on 2009-04-25
> **Prosis said:**
> Thanks all, but I have a question

Wouldn't the 64 bit version of Ubuntu use more RAM?
Not necessarily. But I haven't looked into it that closely.
> **Prosis said:**
> Hey I've had a 64 bit processor for 2 years and I didn't know lol!

My processor is an Intel Core 2 Duo so it's X86-64!

Alrighty Jaunty 64 bit, here I come! :D
I have an AMD Sempron 3200+ in one of my machines, which I've had over 3 years. I only recently discovered that it was 64-bit capable. D'oh! I'm waiting for a 64-bit server version of Jaunty from Shipit......

---

