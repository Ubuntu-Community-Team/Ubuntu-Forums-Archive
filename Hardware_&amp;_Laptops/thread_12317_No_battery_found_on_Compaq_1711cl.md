---
title: "No battery found on Compaq 1711cl"
date: 2005-01-23
forum: Hardware &amp; Laptops
---

### Post by stonhaus on 2005-01-23
Hi all,
 
 I have had Ubuntu installed for a bit and it is a great distro. I can't for the life of me get the battery app to detect how much battery is left. The battery app shows when the power cable is plugged in, but it says that there is not a battery installed. I have tried all the suggestions from previous threads to change to apm and also to try to force acpi, but  nothing seems to work.  Battery detection worked in suse, mepis and knoppix. Any suggestions? I dont want to have to switch distros because of this one flaw.

---

### Post by ming0 on 2005-01-23
Just out of curiousity, are you using Warty or Hoary?

Did you see my post:
[http://ubuntuforums.org/showthread.php?t=12309](http://ubuntuforums.org/showthread.php?t=12309)

If you are using Hoary, it might be that there is some sort of flaw in one of the upgrades...

How new is your laptop?

Don't give up yet--we might have the exact same problem... The battery used to work for me.

---

### Post by stonhaus on 2005-01-23
I am using warty now. It didnt work in hoary though. 
 
 The laptop is about 3 years old. 
 
 Yea, I saw your post. That looks like the same thing for me, except that battery was never detected for me.
 
 Here is a link to the product specifications for the laptop: [http://h10025.www1.hp.com/ewfrf/wc/document?dlc=en&tool=softwareCategory&lc=en&product=95277&cc=us&docname=c00009266](http://h10025.www1.hp.com/ewfrf/wc/document?dlc=en&tool=softwareCategory&lc=en&product=95277&cc=us&docname=c00009266)
 
 Thanks in advance for any help,
 
 stonhaus

---

### Post by ming0 on 2005-01-23
How long ago did you install Ubuntu on this laptop?

My problem showed up over X-mas break--sometime right after christmas, I think.

Maybe we should start a bug report? Then the devs might be able to look into it...

If anyone else has an older laptop (that hasn't got a 'smart battery') that has the same problem, please post here to let us know!

Thanks :o

---

### Post by stonhaus on 2005-01-23
I installed it over christmas break also. The distro cd that I used was just the warty 4.10 from the ubuntulinux.org site.

---

### Post by ming0 on 2005-01-23
I assume that you updated Ubuntu w/ synaptic? Did you happen to notice that it was broken before an update? Have you added the backports into your Warty install's repositories?

I downloaded the CD from ubuntulinux.com and installed it--and the batt. meter worked--so I updated to Hoary, and it worked some more... then it quit working (after an update?).

I'm still not sure if we are suffering from the same thing or not--I'll do a bug report when I get a little more information (and I'll post the link to the report here).

---

### Post by stonhaus on 2005-01-23
Honestly, I can't remember if the meter worked or not with the fresh install. I just installed, opened up all the repositories/added backports, and did an upgrade and dist-upgrade with apt-get.

---

### Post by ming0 on 2005-01-23
Okay, then we can assume that it might have worked--and that likely, we suffer from the same problems... I'll do a bug report right now.

---

### Post by ming0 on 2005-01-23
Okay, I added a bug report:

[https://bugzilla.ubuntu.com/show_bug.cgi?id=5807](https://bugzilla.ubuntu.com/show_bug.cgi?id=5807)


stonhaus, can you do one last test for me? will you give the output you get from the following command:

ls -l /proc/acpi/battery/

Thanks :)

---

### Post by stonhaus on 2005-01-24
[QUOTE=ming0]Okay, I added a bug report:

[https://bugzilla.ubuntu.com/show_bug.cgi?id=5807](https://bugzilla.ubuntu.com/show_bug.cgi?id=5807)


stonhaus, can you do one last test for me? will you give the output you get from the following command:

ls -l /proc/acpi/battery/

Thanks :)[/QUOTE]
 $ ls -l /proc/acpi/battery
total 0
dr-xr-xr-x    2 root     root            0 2005-01-23 22:52 CMB0

Thanks again for all your help.

---

### Post by ming0 on 2005-01-24
Good news! The problem has been isolated, and will be patched. 

Check it out:
[https://bugzilla.ubuntu.com/show_bug.cgi?id=5807](https://bugzilla.ubuntu.com/show_bug.cgi?id=5807)

---

### Post by stonhaus on 2005-01-24
Wow amazing. Talk about tech support and dedication. Thanks everyone for the fantastic support. Ubuntu totally takes top rank with me now.

---

### Post by ming0 on 2005-01-25
It looks like the bug hasn't been completely ironed out yet, but if you want to use your battery meter--just roll back to the 2.6.9-x kernel, and it'll work great. (just move the 2.6.9 entry to the top in /boot/grub/menu.lst)

Hey, I'm glad to have helped you--it's really the devs that are taking care of this one tho. I'm glad to have created a new Ubuntu zealot tho  :D

ps-just remember that you can do nearly anything in Ubuntu that you can in windows! sometimes it might take the help of wine or cedega or xover--but it can generally be done without! I'm almost ready to delete windows altogether (alas premiere only works in windows :()

---

### Post by kultex on 2005-01-27
I take your offer earlier in the thread - so I try to post my problems here.

I just  installed Warty (Install CD) on my Toshiba Portege 7200 (ca. 4 years old) - astonishing - my extern PCMCIA freecom CD-Rom was recognized, also my linksys usb2 networkcard  .... without making floppy and copying the CD to the harddisk, loading ACPI modules......

the only thing, the battery shows emtyness (0%) and it does not recognize, if the laptop is plugged to electricity - it says all the time, that the laptop is running on battery.

In Knoppix, the battery level works fine  and also if it is on electicity or battery - but I cant install Knoppix, because after installation its  :-( 

I have no acpi  directory in proc only in etc

I did upgrade today- but nothing changed

the second problem is - do you have any idea why I can not make linkage on files on windows partitions - I have all permissions (read, write, execute) on the partition - but whenever I try to make a linkage (I hope that this is the right english term) - it says "no permission" - and it happens only on mounted windows partitions.

do you have any idea?

---

### Post by ming0 on 2005-01-28
[QUOTE=kultex]do you have any idea?[/QUOTE]
kultex, 

I'm not in town right now, and won't be home for a bit... (i'm in an internet cafe right now). So I probably can't be of too much help right now.

I would post this to a new thread in the laptop section, and if you put a link to your post in this thread, then I should be able to help you when I return (as long as someone else hasn't already figured things out)!

talk to you soon :)

---

### Post by kultex on 2005-01-30
thanks for your offer - it is not that urgent, because it does not realy effect working with the laptop. 

New thread is:  [http://ubuntuforums.org/showthread.php?t=13264](http://ubuntuforums.org/showthread.php?t=13264)

nice time outside

---

