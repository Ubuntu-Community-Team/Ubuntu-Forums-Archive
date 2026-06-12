---
title: "Headphones not working Ubuntu 10.04 LTS"
date: 2010-08-11
forum: Hardware
---

### Post by fierdor on 2010-08-11
Hello,
I am using Ubuntu 10.04 on my Dell inspiron 14r N4010 laptop.
My laptop internal speaker sounds are working..But there is no sound through the headphones..
I think I have read like 15 posts on this issue...But i havent got a solution..
My codec is Realtek ALC259...
My alsamixer version is 1.0.22
In my alsamixer window I see the master volume full.
But next to it in the headphones section, it shows 0 level and I am not able to increase the volume..It stays at zero level..
Any suggestions? I have been racking my brains over the last two days and I am relatively new to Ubuntu..
Thanks in advance!

---

### Post by ramkumarh on 2010-08-14
I am having the same problem with Inspiron N4010 with Ubuntu 10.04. I am able to hear sound from the speakers. Please help.

---

### Post by mike909 on 2010-08-30
Same hardware, same issue here.
I've tried: [http://ubuntuforums.org/showthread.php?p=6589810#post6589810](http://ubuntuforums.org/showthread.php?p=6589810#post6589810)
but that didn't work (fixed headphone jack, but broke mic input)

---

### Post by javershal on 2010-08-31
I was having the same problem, although headphones didn't show up in my alsa mixer. I just reinstalled alsa and things work fine now. This is the website I used for the reinstall [http://monespaceperso.org/blog-en/2010/05/02/upgrade-alsa-1-0-23-on-ubuntu-lucid-lynx-10-04/](http://monespaceperso.org/blog-en/2010/05/02/upgrade-alsa-1-0-23-on-ubuntu-lucid-lynx-10-04/) . Hope that helps

---

### Post by mike909 on 2010-09-01
javershal,
Thanks dude, that worked perfectly. I'm going to post a new thread related to all the N4010 issues and how to fix them. I've got networking (both wired and wireless) and now sound figured out. Only remaining thing is the sleep/brightness issue. need to figure out how to patch existing kernel (2.6.32-24).

---

### Post by _minnE on 2010-09-01
Thanks jav, does this work for mic as well?

---

### Post by javershal on 2010-09-01
Note/warning: It was working fine, then the next time I restarted the computer it was back to the way it was before. Also when it was working the mic was working fine.

my setup: Asus U43
Ubuntu 10.04
Codec: realtek ALC269 and Intel G45 DEVIBX

---

### Post by _minnE on 2010-09-01
Any other ideas?

---

### Post by mike909 on 2010-09-01
it has survived a reboot for me...will update if it fails again. I'm on kernel 2.6.32-24

---

### Post by _minnE on 2010-09-01
Thanks Mike, guess I'll go ahead and give it a shot then.

---

### Post by nikeysunfire on 2010-09-07
Same Issue here...Using an Asus G60vx , not even upgrading to version 1.0.23 gave the option to turn the volume up on the headphone level inside the alsamixer, hope it can be fixed soon XP

---

### Post by ramkumarh on 2010-09-12
Awesome. This worked for me.. Now I am happy and enjoying songs on from my earphones.....=D>

---

### Post by sNeb on 2010-11-19
> **javershal said:**
> I was having the same problem, although headphones didn't show up in my alsa mixer. I just reinstalled alsa and things work fine now. This is the website I used for the reinstall [http://monespaceperso.org/blog-en/2010/05/02/upgrade-alsa-1-0-23-on-ubuntu-lucid-lynx-10-04/](http://monespaceperso.org/blog-en/2010/05/02/upgrade-alsa-1-0-23-on-ubuntu-lucid-lynx-10-04/) . Hope that helps

Thanks Javershal, the instructions you linked to worked for me too, Ubuntu 10.04 on a Dell box. Still works after a restart. 

Just a guess, but it looks like the alsa driver gets compiled into the kernel, so might need to recompile for each kernel upgrade.

---

