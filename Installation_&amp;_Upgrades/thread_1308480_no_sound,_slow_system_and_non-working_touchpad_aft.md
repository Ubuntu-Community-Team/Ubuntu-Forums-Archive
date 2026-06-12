---
title: "no sound, slow system and non-working touchpad after upgrading to karmic"
date: 2009-10-31
forum: Installation &amp; Upgrades
---

### Post by rusma on 2009-10-31
Hi. Today Iæve upgraded to Ubuntu 9.10 karmic, but it really gave me more problems than I had already: 

1. My sound is not working at all
2. the system in general is very slow, why is this? 
3. my touchpad is not working (I'm on a laptop) 

Hope to get good answers this time.

---

### Post by danielshewchuk on 2009-10-31
I also have no sound. My touch pad works. I also hope to get answers. I never seem to get the help i need here

---

### Post by samasat on 2009-10-31
For mee too .... Main issue is touchpad stopped working ! ... totally helpless now.

I guess touchpad issue may be system depepndent. 

Regarding sound, someone posted some suggestions in other threads in same forum. 

I can't do anything however ... waiting for touchpad issue solved.

-samasat

---

### Post by Andybr2000 on 2009-10-31
Same problem with my computer:
System slow
Upgraded from Ubuntu 9.04 to 9.10 Karmic
Kernel Linux 2.6.27-9-generic
GNOME 2.28.1
Dell laptop E1505
Memory: 2.5GiB
Processor 0: Intel T2300 @ 1.66GHz    25%
Processor 1: Intel T2300 @ 1.66GHz   100%
Available disk space: 8.5GiB

Process Name usplash 100%  
I killed the usplash process, but now the Xorg is 89% if I move any window.
system did not find the sound card
No mouse touch pad
I cannot change display visual effects or use compiz

---

### Post by Sudo Sumo on 2009-10-31
> **Andybr2000 said:**
> Same problem with my computer:
System slow
Upgraded from Ubuntu 9.04 to 9.10 Karmic
Kernel Linux 2.6.27-9-generic
GNOME 2.28.1
Dell laptop E1505
Memory: 2.5GiB
Processor 0: Intel T2300 @ 1.66GHz    25%
Processor 1: Intel T2300 @ 1.66GHz   100%
Available disk space: 8.5GiB

Process Name usplash 100%  
I killed the usplash process, but now the Xorg is 89% if I move any window.
system did not find the sound card
No mouse touch pad
I cannot change display visual effects or use compiz

Same here!  Although I don't use my touchpad (disabled in BIOS ... palms always drag and it's annoying), my sound is gone and browsing is INSANELY slow. 

Usplash was the #1 offender, killed it, stuck with XOrg.  Looked at xorg.conf, generic settings, running 

sudo dpkg-reconfigure xserver-xorg

does nothing ... that is to say, I've run it before to adjust my settings, but this time it just returns a cursor.

I've got a Thinkpad T61 with an Intel GM965/GL960.

Problems seem to occur when I attempt to switch pages in Firefox or open a full screened application.

Help!

---

### Post by balak on 2009-10-31
rusma, samasat:

check if this helps you:
[http://ubuntuforums.org/showthread.php?t=1308857](http://ubuntuforums.org/showthread.php?t=1308857)

---

### Post by samasat on 2009-11-02
Thanks Balak.

I found your HOW TO posting useful. I can use the touchpad now and I am really booting using Upgraded Ubuntu unlike earlier where I was still in Ubuntu 2.6.28-11 kernel.

However, the wireless internet is turned OFF and I am not able to turn it back ON using the keyboard touch key. (OTHER touchkeys for sound etc are working) 

-samasat

---

### Post by mherman on 2009-11-02
When I upgraded to 9.10, neither my touchpad nor sound were working. I did this, which seemed to work:

    sudo apt-get install grub2

After installing grub2, and rebooting, the newest kernel was available. I chose that one, and the touchpad and sound work now.

Toshiba Satellite M305-S4920

---

### Post by samasat on 2009-11-02
mherman's suggestion could be useful if someone has internet connection ... may not be possible for people like me who are still strugglling to get wireless working :(

---

### Post by TheForumTroll on 2009-11-02
Maybe [this will help]("http://ubuntuforums.org/showthread.php?p=8218261#post8218261").

---

