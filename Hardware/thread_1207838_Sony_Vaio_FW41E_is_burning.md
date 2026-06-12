---
title: "Sony Vaio FW41E is burning"
date: 2009-07-08
forum: Hardware
---

### Post by ogregoire on 2009-07-08
Hi,

I just bought a new laptop, a Sony Vaio FW41E. As I was told the compatibility was good with FW31*, I thought I could buy one of the next generation.

However I got some annoying issue : my laptop is burning after 30 minutes. It seems that there is one component that heats up, and I don't know which one (it's my first laptop, so I'm not already in with laptops). I cannot touch my laptop afterwards. It seems to be related to ubuntu, because the few moments it was on Windows (while installing before I could refuse the EULA) before I install Linux, it didn't heat so much, even if disk usage seemed intensive.

I was wondering if one of you had the same issue and how you solved it.


Thank you,

---

### Post by shatterblast on 2009-07-09
My first two guesses would be either a wireless network card or most likely your graphics card.  If you're enjoying game software or using WINE, then the graphics card seems like the source of the heat issue.  Linux video drivers tend to run very efficiently, but in turn, it can suck up a lot more electricity.  That in turn can make short work of a battery's reserves.

---

### Post by ogregoire on 2009-07-09
Currently, I just installed Ubuntu and disabled the Wi-Fi. I haven't installed any game yet (and I don't think I will).

But anyway, my laptop starts heating even if I simply log-in without doing anything afterwards, with Wi-Fi mechanically disabled (using the integrated button to switch it on/off).

---

### Post by shatterblast on 2009-07-09
I see that your system should support the x64 variety of operating system.  Have you installed the x32 version instead of the x64 type?  A processor may over-work itself and cause excess heat when designed for x64 but function in x32 instead.

---

### Post by ogregoire on 2009-07-10
Indeed my Laptop is a 64 bits, and I installed the 32 bits. But the 64 bits version of Ubuntu image mentions AMD (file name is "ubuntu-9.04-desktop-amd64.iso") and I have an Intel.

I'll try this, and report back.

---

### Post by ogregoire on 2009-07-10
Thank you, it seems to be ok, now.  I've run it for one hour with ubuntu 64 bits, and it has a normal heat.

---

