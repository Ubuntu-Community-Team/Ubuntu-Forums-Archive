---
title: "Have a few questions about installing Ubuntu"
date: 2009-02-22
forum: Installation &amp; Upgrades
---

### Post by Jimmy1 on 2009-02-22
Hello,
When I first downloaded the Ubuntu Live CD it would not work on my computer, it would give a Segmentation fault error when loading up. So I downloaded the alternate ISO and installed it to a Virtual machine just to make sure it would work on my system, and it does.
So I was going to install it to my hard drive, I downloaded GParted to use but when I boot that up in the Live CD it will not load. It gives this error.
**Kernel panic- not syncing: Attempted to kill the idle task**

It will just sit there, I have to turn off my computer to get back on it. I went ahead and tryed to boot up GParted on my Virtual machine just to see if it works there, and it does. It boots up just fine.


So my questions are.
1). Since Gparted works in the Virtual machine and does not work with my computer, will Ubuntu work if I install it to my computer?


2). Does anyone know why Gparted is doing that and how to be able to fix it?



Thank you for any help you can give.

---

### Post by taurus on 2009-02-22
What's the spec of your machine?  Are you trying to install Ubuntu on it own partition, dualbooting with windows?

---

### Post by Jimmy1 on 2009-02-22
Hello taurus,
Thanks for the reply.


> What's the spec of your machine?
Intel Pentium 4 processor, 3.06GHz
1016MB RAM
The graphics card is a NVIDIA GeForce FX 5500 with 256MB of memory.
If you need any other specs, please let me know.
> Are you trying to install Ubuntu on it own partition, dualbooting with windows? 
Right now my hard drive has Windows XP and the recovery part for XP. So my plan was to shrink the part with Windows XP and use that for the linux swap and for Ubuntu. So I could still use my Windows XP with Ubuntu.

---

### Post by taurus on 2009-02-22
Boot into windows and defrag your harddrive a couple of times.  Then,

1.  run a checksum to check the integrity of the ISO image after you've download it,

2.  burn it at a slow speed like 4x,

3.  run the check cd for defects at the initial screen from the LiveCD,

4.  or press F4 at the initial screen and use the safe graphic mode option to boot the LiveCD.

---

### Post by Jimmy1 on 2009-02-22
Hello,
Did everything till step 3.
I did not see that option at the GParted screen.

And for step 4, I did the safe graphic mode and GParted still gave this error.
**Kernel panic- not syncing: Attempted to kill the idle task**

---

### Post by taurus on 2009-02-22
Did you download the GParted LiveCD?

---

### Post by Jimmy1 on 2009-02-22
Yes.

The strange thing is, that it will work in the Virtual machine but when I try it in my computer it gives that error.

---

### Post by Jimmy1 on 2009-02-25
Does anyone have any ideas why this is doing this and how to try to fix it?


Thanks :)

---

### Post by Jimmy1 on 2009-02-27
Just a update.

I have ran memtest86 and it said it found no errors.

---

### Post by iulian2009 on 2009-02-27
Hi !
My name is Iulian and i need your help:
I install Squid 3.0 and don't work of https site.
Error is:
"The requested URL could not be retrieved
While trying to retrieve the URL: [www.google.com:443](www.google.com:443)
The following error was encountered:
    Unable to determine IP address from host name for 
The dnsserver returned:
    Name Error: The domain name does not exist. 
This means that:
 The cache was not able to resolve the hostname presented in the URL. 
 Check if the address is correct. 
Your cache administrator is [email]iulian.ion2008@gmail.com[/email]
Generated 27 Feb 2009 15:34:34 GMT by Linux-Proxy (squid/3.0.STABLE13)"

The configure command is:
./configure --prefix-/Squid-3.0 --enable-ssl

Please help me !

---

