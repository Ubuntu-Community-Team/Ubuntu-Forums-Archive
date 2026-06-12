---
title: "Sound - snd_intel8x0 working sometimes"
date: 2007-04-26
forum: Hardware &amp; Laptops
---

### Post by ezaton on 2007-04-26
Hi.
I wanted to share this information with you.
Using IBM X41 with 7.04, after hibernation or restart there is no sound. Although the modules are loaded, and volume control seems to change something, the computer is mute.

While frustrated, I accidentally discovered that sleep mode restores sound to the computer. 
I will check this further, but it could be an issue with firmware, which might require upgrade.  

Still, at the time of writing this post, I was unable to upgrade BIOS. 
I have noticed that after sleep, when sound is on, it remains working even after restart. Hibernation makes it disabled, and sleep mode (again) will bring it back.

FYI.
Ez

---

### Post by annotei on 2007-04-28
Amazing your trick. After an hibernation I use Xmms : no sound. I put the computer into sleep and wake it up then I can listen the song !!!!

I've a Nec Versa S940 and use the snd_intel8x0 module. I don't think I comes from the bios.

Antoine.

---

### Post by K0LO on 2007-04-28
Ez:

I can confirm that your workaround works on my IBM X41T. Still trying to figure this one out...

---

### Post by K0LO on 2007-06-04
Here's the fix:
[https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/96230/comments/27](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/96230/comments/27)

---

