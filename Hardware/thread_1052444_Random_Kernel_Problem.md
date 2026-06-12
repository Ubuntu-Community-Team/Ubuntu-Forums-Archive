---
title: "Random Kernel Problem"
date: 2009-01-27
forum: Hardware
---

### Post by ethanova on 2009-01-27
I was talking to a friend about this and he informed me that a flashing caps lock button is a kernel problem and to ask about it on the forums so here I am!

For whatever reason this kernel problem keeps happening again and again and at very random times, I wouldn't be able to recreate it if I wanted to. It's done it when the computer is idle, when I'm looking through OpenOffice, and just now when I was doing vocab in KWordQuiz. 

I'm not sure whether this is helpful or not but here's the background on my installing Ubuntu and what I've done to modify and change my Ubuntu install: [http://ubuntuforums.org/showthread.php?t=1046874]("http://ubuntuforums.org/showthread.php?t=1046874") Since this post I'm not using a non-preinstalled theme, if that matters. 

Help? =(

Thanks!

---

### Post by Yellow Pasque on 2009-01-27
Before chasing a phantom software problem, run memtest. You can access this option by pressing 'Esc' when your laptop boots. Let it run for a while (make sure it gets at least one pass, preferably more.)

---

### Post by ethanova on 2009-01-28
I found it in Grub, it wasn't hitting esc when I booted up. I ran it 1.7 times before I had to use my computer. Hopefully that did something. I'll reply as soon as it reoccurs if it does.

---

### Post by Yellow Pasque on 2009-01-28
> Hopefully that did something.
memtest is a diagnostic tool. Running it won't fix/alter your system. It reads/writes to your RAM in different patterns and tells you if there are errors.

You need to run it again. This time, before you quit, look at the data column labeled 'Errors' and make sure it's '0'. Any other value means you probably have bad RAM that needs replaced.

---

### Post by ethanova on 2009-01-28
At the end of the 1.7 trials the errors did say 0, I did check. Bad RAM? As in I'd have to physically replace the RAM in my computer?

---

### Post by Yellow Pasque on 2009-01-29
> At the end of the 1.7 trials the errors did say 0, I did check.
Ah, well then you're good to go. If memtest had reported errors, then yes, it would indicate physically bad RAM.

---

### Post by drlmg on 2009-01-29
I think there is a problem with one of the updates. When I update my machine crashes.. I get error message 'kernel panic - not syncing - attempted to kill init' and my cap lock light is on and won't go off. It has happened twice on one laptop, each time after the update and on two different laptops. I cannot even boot in recovery mode. Several other people have had the same problem that seems to have started (based on times of posts) late this evening. When I re-install everything works fine until I update.

I have been having a lot of problems upon updating the laptops lately (I have four), all my desktops are running fine.

---

### Post by drlmg on 2009-01-29
After re-installing twice I have found what caused my two laptops to crash. It is one or all of the following updates..

[B]linux headers 2.6.24-23

linux headers 2.6.24-23-generic

linux-image-2.6.24-23-generic[/B]

All have to do with the Linux kernel.

When I re-installed for the second time I updated everything except these updates and it re-booted fine.

---

### Post by ethanova on 2009-02-03
Yeah I don't exactly know what's up. I don't guess this is a kernel problem anymore but I updated last week sometime. Then I added a new user 'workplace' After shutting off it Ubuntu didn't boot up anymore. Says some stuff that I forget and if I let it sit long enough it says:

" The GDM group 'gdm' does not exist. Please correct GDM configuration and restart GDM "

I tried userdel workplace from the command line and I think it got rid of the user but Ubuntu still won't boot up right. I also tried booting from an 8.04 live disk just so that I could recover my files and maybe just get rid of Ubuntu which is just not working on my computer for me at all... and as soon as Ubuntu 'loads up' it shuts down immediately and ejects the disk. What the heck???

---

