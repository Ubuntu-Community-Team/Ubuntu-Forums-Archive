---
title: "Asus N10J-A1 -- No sound in Hardy"
date: 2008-10-19
forum: Hardware
---

### Post by Fish_Kungfu on 2008-10-19
This is driving me nuts!  I have an Asus N10J-A1 and it's freakin awesome!  BUT... I have tried about every thing that's been posted to get sound working for "Intel 82801G (ICH7 Family) High Definition Audio Controller (rev 02)" but nothing has worked.  Has anyone gotten sound working yet for the Asus N10J series?

Cheers...Fish
---------------------
~Second Life resident

---

### Post by flup on 2008-10-28
I have exactly the same problem. Unfortunately, it seems that nobody has tried to install linux on the N10j because there is absolutely nothing anywhere - I've driven myself crazy googling for this.

It seems the problem is not just with the soundcard, but with the UAA bus which requires a proprietary microsoft driver - it's one of those things vista compliant things if I'm not mistaken. see this [http://technology-muse.blogspot.com/2008/05/uaa-driver-for-linux.html](http://technology-muse.blogspot.com/2008/05/uaa-driver-for-linux.html)

I hope over time more people will get this netbook and we will have a solution. I've tried everything I could, but I just don't have the time and so I've just been using XP so far, which at least is far better than the vista which was pre-installed, but I would love to get ubuntu on working on this thing with sound!

---

### Post by ALLurGroceries on 2008-10-30
Thought I'd let you know that audio works in the latest 2.6.28-rc2. I made a post here:
[http://forum.notebookreview.com/showthread.php?t=315810]("http://forum.notebookreview.com/showthread.php?t=315810")

I'm on debian but it should work for you too! Good luck :guitar:

---

### Post by SavageMaster on 2008-11-14
I just made it work without compiling a new kernel.

Edit /etc/modprobe.d/alsa-base

Add the line at the end

options snd-hda-intel position_fix=1 model=3stack-6ch-dig

Save and reboot.

Damned if it didn't work.

BTW this is in Intrepid but I think it'll work.

I basically took step 5 from [http://209.85.173.132/search?q=cache:JuWACt0v8yEJ:thio4linux.wordpress.com/2007/10/06/intel-hda-intel-corporation-82801g/+snd-hda-intel+82801g+n10j&hl=en&ct=clnk&cd=1&gl=ca](http://209.85.173.132/search?q=cache:JuWACt0v8yEJ:thio4linux.wordpress.com/2007/10/06/intel-hda-intel-corporation-82801g/+snd-hda-intel+82801g+n10j&hl=en&ct=clnk&cd=1&gl=ca)
and arguments from [http://www.mjmwired.net/kernel/Documentation/sound/alsa/ALSA-Configuration.txt](http://www.mjmwired.net/kernel/Documentation/sound/alsa/ALSA-Configuration.txt) (look for snd-hda-intel)
and tried arguments under ALC662 - which is what the sound card appears as in Sound properties.

I haven't tried it with HDMI yet but maybe someone else will confirm my findings.

---

### Post by James- on 2008-11-14
Installed Ubuntu 8.10 in safe graphics mode
added:
> options snd-hda-intel position_fix=1 model=3stack-6ch-dig
Sound works.. although wireless drops a lot I might fallow that guide to upgrade kernel/wireless

---

### Post by SavageMaster on 2008-11-15
Yeah, the wireless doesn't work well for me either with the Gnome network manager.  I uninstalled it and used knetworkmanager instead.  Haven't had a drop since.

Scratch that, looks like I'm having the same problem.

---

### Post by ALLurGroceries on 2008-12-07
> **SavageMaster said:**
> Yeah, the wireless doesn't work well for me either with the Gnome network manager.  I uninstalled it and used knetworkmanager instead.  Haven't had a drop since.

Scratch that, looks like I'm having the same problem.

Sorry this reply is so late I haven't been watching this thread... 

There is a tweak for the wireless in my howtwo that involves editing a .c source file in the kernel before compilation. Look for the part that says 'optional part begins here':

[http://forum.notebookreview.com/showthread.php?t=315810]("http://forum.notebookreview.com/showthread.php?t=315810")

---

