---
title: "Is it safe to install *Ubuntu on Dell laptops?"
date: 2006-09-25
forum: Hardware &amp; Laptops
---

### Post by MirdautasVras on 2006-09-25
Hello everyone. 
I've been interested in trying out linux for quite a while, and just recently got a Dell Inspiron 640m (1405 in the US, I think). It would be very interesting to try kubuntu/ubuntu on this laptop. I have, however, heard of problems with Ubuntu on this laptop (as well as other dell laptops). 

The most critical is probably the "real-time clock stopped" error some people have been getting, which prevents the laptop from booting and prevents the user from entering the bios. ([https://launchpad.net/distros/ubuntu/+source/linux-source-2.6.15/+bug/43745](https://launchpad.net/distros/ubuntu/+source/linux-source-2.6.15/+bug/43745))

Does anyone know if this error has been fixed, or if it's common? I've heard you might remedy the problem by removing the coin cell battery, but it's a bit out of reach on my laptop (below the keyboard). 

I'm also wondering if my mediadirect functionality will be left alone (a limited media player that can be booted without windows, with a row of buttons below the keyboard for volume, play, stop etc). I've heard GRUB will treat it like any other partition, and that you'll get to choose which partition you want to boot when Ubuntu is installed on the laptop. 

Are there any other things I should know before trying to install *ubuntu, especially if they are related to my own laptop, or Dells in general.

I'm thankful for any help!

---

### Post by blx_286 on 2006-09-25
> **MirdautasVras said:**
> Hello everyone. 
I've been interested in trying out linux for quite a while, and just recently got a Dell Inspiron 640m (1405 in the US, I think). It would be very interesting to try kubuntu/ubuntu on this laptop. I have, however, heard of problems with Ubuntu on this laptop (as well as other dell laptops). 

The most critical is probably the "real-time clock stopped" error some people have been getting, which prevents the laptop from booting and prevents the user from entering the bios. ([https://launchpad.net/distros/ubuntu/+source/linux-source-2.6.15/+bug/43745](https://launchpad.net/distros/ubuntu/+source/linux-source-2.6.15/+bug/43745))

Does anyone know if this error has been fixed, or if it's common? I've heard you might remedy the problem by removing the coin cell battery, but it's a bit out of reach on my laptop (below the keyboard). 

I'm also wondering if my mediadirect functionality will be left alone (a limited media player that can be booted without windows, with a row of buttons below the keyboard for volume, play, stop etc). I've heard GRUB will treat it like any other partition, and that you'll get to choose which partition you want to boot when Ubuntu is installed on the laptop. 

Are there any other things I should know before trying to install *ubuntu, especially if they are related to my own laptop, or Dells in general.

I'm thankful for any help!


I am running it on a Dell Inspiron 4150 (US) and haven't had any probs. I don't know anything about the mediadirect, so I can't answer that question. Also, you could use the LiveCD and try it first without making any changes to your laptop.

---

### Post by ridgerunner7 on 2006-09-25
I'm running Dapper on 700m. No issues.

---

### Post by lonce on 2006-09-25
I had xubuntu running on my dell inspiron 8500 with a P3 433 with no issues.  Gave it to my son and he uses it daily.

---

### Post by jISh on 2006-09-25
Xubuntu on a Dell latitude 667mhz...no problems here.

---

### Post by lonce on 2006-09-25
I would guess media direct would not still work.  Unless you can isolate how its done.  Whether its a partition on your hard drive or what not.  If its a partition then just leave that one alone and it should be ok.

---

### Post by madcow72 on 2006-09-25
I installed Kubuntu 6.06 on my Inspiron 8600 about 3-4 weeks ago for the first time - absolutely no issues.  Works beautifully.  However, if you just want to get a flavor of linux, blx_286's suggestion about the Live CD is a good one.  Your machine will load into a fully functional (K)Ubuntu OS and let you play around!  

(If you're like me, though, it'll get you hooked and you'll do the install regardless.)

---

### Post by bigken on 2006-09-25
I run edgy dapper suse 10.1 freespire and winxp on my dell inspiron 9200 no probs ;)

---

### Post by NooneReally on 2006-09-25
I've got a 1405 with ubuntu 6.06.1 on it. Almost everything worked perfectly immediately, except i had to get the 915resolution package for native resolution.

only things that don't currently work:
xD card reader - libraries are catching up
s-video out - i'm sure I could figure this out if i really wanted to
headphones - for some reason plugging in phones switches the audio out to the phones until i reboot...still trying to figure out what is being modified in only one direction.


as for media direct: I left their partitions intact, but pressing the media direct button just brings up grub really fast.

For that matter my suspended 1405 resumes in <5s...and I have a hotkey to kill the display so there is no need for their shabby program. this gives me a vastly more featured media center than dell.

---

### Post by Indref on 2006-09-25
Running Dapper on a Dell Latitude C800, a few strange bugs, nothing serious.

The Live CD is highly recommended.

---

### Post by ogu on 2006-09-26
I'm running Ubuntu on an inspiron E1505 with media center (double boot, ubuntu as main).

No problems at all, at first i had some problems with resolution but they were easy to fix.

I have everything working: bluetooth, the media center (with mythtv), wireless ...

it doesn't seem so bad, but it's still a risk you must take ;) :D

---

### Post by MirdautasVras on 2006-09-27
Thanks for all the replies! I've tried the live cd, and it works as long as you keep it in safe mode (ubuntu has issues with the widescreen, apparently).

I'm going to try to install Kubuntu today. I ran into some problems when I tried it a day or two ago (I shrunk my NTFS partition, but I couldn't format the free space afterwards..). I'm thinking I might have to move all of the free space into one part (I have a 7.3 meg freespace at the end of the harddrive). Maybe I break the "No more than four partitions on a single harddrive" otherwise? Well, I'm looking into it. Wish me luck!

---

