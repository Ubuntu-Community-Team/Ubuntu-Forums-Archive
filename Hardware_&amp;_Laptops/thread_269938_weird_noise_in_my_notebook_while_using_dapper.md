---
title: "weird noise in my notebook while using dapper"
date: 2006-10-02
forum: Hardware &amp; Laptops
---

### Post by xianyun on 2006-10-02
I've successfully installed Dapper 6.0.1 in my notebook, dell 640m . After log in, I often heard a slight noise, 'ka~~ka~~', about 3-8 times per minute. would it damage my hard driver? Here's some related information:
  hd: wc sata ,120G
  memory: 1G
  linux swap: 300MB
  linux file system: ext2
  
  thank you!

---

### Post by AndrewB on 2006-10-02
Dapper Drake has Crows.

No help but maybe funny:)

---

### Post by Kateikyoushi on 2006-10-03
I think the noise means the heads park in your hdd.
I think I had something similar after I installed laptop mode, if it is installed try to check the settings.

---

### Post by xianyun on 2006-10-03
Yes, I thought there may be some programs which tried to visit my hdd regulaly. I've closed log serves, but the problem goes on.

---

### Post by MonsterDog on 2006-10-03
Hi,

I don't know what it is or why it happens so often.  I can tell you that it happens in windows and other linuces, too.  I've had two dell supplied HD's that both made the tap-tap sound and my brand new 80 WD Scorpio does it too, maybe a little louder.  The frequency does seem a little higher in Dapper, though.

---

### Post by MonsterDog on 2006-10-09
Hi again,

After a little more research I found these threads:
[http://ubuntuforums.org/showthread.php?t=79055](http://ubuntuforums.org/showthread.php?t=79055)
[http://www.thinkwiki.org/wiki/Problem_with_hard_drive_clicking](http://www.thinkwiki.org/wiki/Problem_with_hard_drive_clicking)

Start with the second one.  It talks about hitachi drives in thinkpads but I think it applies to most.  The first one's kind of long but has some things to consider if the hdparm command didn't work.

What seems to work for me is "sudo hdparm -B 255 /dev/hda" this stops almost all of the clicking.  It also turns off power management for the drive, that could be a problem if you aren't plugged in.

Much happier nnow that my HD shutup,
MD

---

### Post by cbm_redux on 2007-01-01
I've recently installed Ubuntu Dapper on my laptop. Every 10-15 seconds I hear a fait click. My hard drive is just a few weeks old. Additionally, when it's booted into XP, I _never_ hear this sound. 

My questions are is this something that is going to ruin my hard drive? And, what could be causing this in Ubuntu GNU/Linux but not WinXP?

Edit: I've since found out that this is a known issue with my Western Digital hd in laptops. The drive is incorrectly interpreting a signing from the laptop's power management. Western Digital has a firmware update on their site. However, when I attempted to use it, it said that I already have the latest firmware. So, I'm swapping out my current hd for one from another manufacturer. 

In the meantime, as many others have mentioned.  "sudo hdparm -B 254 /dev/hda" stops the clicking of my hd's telltale read arm.

---

