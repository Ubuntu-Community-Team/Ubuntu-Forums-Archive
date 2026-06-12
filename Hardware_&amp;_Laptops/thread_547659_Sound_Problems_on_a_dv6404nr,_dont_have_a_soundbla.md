---
title: "Sound Problems on a dv6404nr, dont have a soundblasterr card ...."
date: 2007-09-10
forum: Hardware &amp; Laptops
---

### Post by Dirksy on 2007-09-10
I have been trying all the threads posted about sound problems for about a week and some worked until I rebooted.   I am stuck on how to fix the issue.

I have a conextant digital/analog sound card built in that runs off of HDA Nvidia technology
Nothing I have done seems to work, can anyone give any ideas,.....im all out.


HP dv6406ntr
running Ubuntu 7.04

---

### Post by linuxwizard on 2007-09-10
Look over these see if anything will help.

[https://help.ubuntu.com/community/SoundTroubleshooting](https://help.ubuntu.com/community/SoundTroubleshooting)

[https://help.ubuntu.com/community/DebuggingSoundProblems](https://help.ubuntu.com/community/DebuggingSoundProblems)

Also if you installed the latest Ubuntu updates you might want to look at Launchpad and see if a bug has been reported. Look for sound issues and by your sound card.

[https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20)

---

### Post by ZX3Junglist on 2007-10-17
> **Dirksy said:**
> I have been trying all the threads posted about sound problems for about a week and some worked until I rebooted.   I am stuck on how to fix the issue.

I have a conextant digital/analog sound card built in that runs off of HDA Nvidia technology
Nothing I have done seems to work, can anyone give any ideas,.....im all out.


HP dv6406ntr
running Ubuntu 7.04

Did you ever get this working?
I notice you have the same laptop that I do.. and I had a similar issue.
On mine, my sound just stopped working. this was during the "try ubuntu and see if I like it" stage. on my second install, sound worked again, but I was more careful updating/installing packages. I discovered something that I installed had broken the sound. Somehow this worked itself out, and a few days later it just 'worked' again.

On install #3, I didn't install nearly as many packages, most notably, no beryl. The sound never broke. So, I have a clue but I won't make any assumptions without knowing for sure.

Problem really is, Ubuntu has a critical bug with our laptop. SMP is broken, and it causes IRQ errors like wild. unfortunately, I scrubbed ubuntu and went to PCLinuxOS. it's much better (sorry, buntu!!) as far as stability goes. The only downside is I had to deal with KDE when I had just gotten used to gnome. Still is very pretty though.

Now if only we could get broadcom ACTUALLY worked out, life would be peachy.

:)

---

