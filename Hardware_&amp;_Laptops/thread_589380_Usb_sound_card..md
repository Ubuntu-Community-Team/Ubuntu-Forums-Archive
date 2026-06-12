---
title: "Usb sound card."
date: 2007-10-24
forum: Hardware &amp; Laptops
---

### Post by erchewy on 2007-10-24
Hello i have installed gibson recently. I have an m-audio mobilepre usb sound card, and in feisty iti works well. In gibson the system recognize the sound card, but in the mixer, when i try to increase the volume the volume is muted and the left and right channels brokes the link between theirs. Anybody have any idea about this problem? 

thanks in advance.

---

### Post by cfraenkel on 2007-10-24
Have the same problem with a Microsoft USB soundcard - was working fine in 7.04, now doesn't work in 7.10.

In my case - the volume control app sees the Microsoft card (but that may be leftover from the previous system)

But running asoundconf at the terminal only sees:
 $ asoundconf list
Names of available sound cards:
ICH5
default


I'm guessing I could get the sound working through the builtin sound, but then I lose my speakers - not a very good solution

still looking for a real solution.....

---

### Post by davepaque on 2007-10-24
I also have a mobile pre and am experiencing the same problem. The problem seems to lie in the volume applet itself. I just disable it and used alsamixer instead as a temporary fix. It works for now although this problem is slightly disconcerting.

---

### Post by erchewy on 2007-11-07
Ok, i try it. But i thought the volume applet is only a frontend for alsamixer, isn't it? How can i disable the volume applet?

---

### Post by etilli33 on 2007-11-14
Hi,

I got the problem solved by removing the files ".asoundrc" and ".asoundrc.asoundconf". Then it started working and also Skype which refused until that works! The files are in your home directory.

---

