---
title: "Aborted 9.04 Install, now XP won't start"
date: 2009-04-30
forum: Installation &amp; Upgrades
---

### Post by Fleshtone on 2009-04-30
Hey all,

I was installing 9.04 and got in over my head with disk partitioning.  I want to put Ubuntu on a secondary drive and couldn't figure out how.  I partitioned 12gb on my F: drive, selected ntfs, and kept getting a "No root file system defined" error.  So I went back and selected the side-by-side installation option.  Then realizing that it wasn't going to let me choose the install drive (and there's only 2gb free on C:) I quit the installation.

Now when XP tries to start it just powers down.  I'm OS-less.  I ran chkdsk from the windows recovery console with no luck.  I'm not trying to ask XP support questions here, I'm just wondering if anyone has seen this.

[UPDATE]  XP seems to have fixed itself, so now I'm back to the original problem.  How do I change the location of the ubuntu install?

---

### Post by obocho on 2009-04-30
Hey, 

I am not an advance ubuntu user, but I guess I can give you some info. 
after you partitioned your HDD, select a format [it sould be ext3 as default, I prefer ext4], then you should select this partition as "root file system" which looks like this: "/". Then, you will be fine. [do not forget to create a swap partition though.]

have fun! [be careful by the way, do not delete your data :)]

---

### Post by Fleshtone on 2009-04-30
Thanks!  My problem was that I didn't know "/" meant root.  Pretty basic!

But now, after it installed, it won't start.  It says "Grub loading, please wait...  Error 22" and just hangs there.  Once again, I can't start windows or ubuntu.  I've tried a few solutions in these forums but to no avail.

---

### Post by upchucky on 2009-04-30
Get Supergrub to set up/repair Grub here:

[http://www.supergrubdisk.org/](http://www.supergrubdisk.org/)

after you have downloaded and created the supergrub disk boot from it then use it to fix grub.

you must read the instructions carefully and understand them, google what you do not understand. You will not hurt anything with this but can get very confused if you do not understand what it does.

---

### Post by zvacet on 2009-04-30
Maybe [this]("http://users.bigpond.net.au/hermanzone/p15.htm#22") will put some light.

---

### Post by Fleshtone on 2009-05-01
Thanks so much for the advice.  I booted to SGD, but got an error (15?) for every option on the menu.  I went to a page here called "[recovering ubuntu after installing windows]("https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows")", which contains a lot of GRUB help despite being named for a situation different than mine.

At some point, I realized I could start Ubuntu by hitting F12 at startup and selecting the drive that contained Ubuntu.  If I did this, I got a normal boot menu that had all the OSs (windows included) but only Ubuntu would boot from that menu.  I have no idea why any of this is true.

I followed instructions on the "recovering ubuntu" page, specifically overwriting the windows bootloader.  After initially breaking things again by writing the wrong (hdx,y) value for windows, things are back in the pink. 

It starts up to GRUB, which loads without error (a beautiful sight) and both windows and ubuntu start perfectly.

It's still a little befuddling not knowing exactly WHY this worked, but I guess that will come with time.

Now I'm wading through wireless issues, trying to get ndiswrapper to make something make something else read my wireless card drivers.  This problem is what lead me to remove the previous version of ubuntu, and I had hoped that 9.04 would be different.  Last time around, I was absolutely stumped...  hopefully I know enough now, after gaining some experience with the MBR issue.

Thanks again!

---

### Post by Fleshtone on 2009-05-01
OK, I was trying unsuccessfully to get my wireless working and decided to restart ubuntu to see if anything would change.  And just like that, I got the old GRUB error 22 and nothing would start.  So I rebooted again and got the same result.

I popped in SGD and let it do its thing, but it just hung while locating /boot/grub/stage1

I restarted again and now SGD just returns error 15 for all choices but one.  The one thing it can do is boot windows.

I could go through the same steps that fixed it last time, but it seems futile because I assume this will just keep happening.  Does anyone know what is going on?

---

### Post by Fleshtone on 2009-05-01
The GRUB error 22 problem seems to have gone away on its own, for now, but the really good news is ndiswrapper is in effect, I'm writing this from ubuntu and I'm pretty stoked about it.  The problem I was having was there was a competing wireless driver.  I must have missed this until now.  I ran *lshw -c network* and there was one more driver in there that I had to blacklist.  Now that ubuntu connects, I can spend a lot more time with it.

One thing I'm still confused about is that "windows wireless drivers", which I believe is ndistk, reads "unable to see if hardware is present".  Then I hit OK and it shows the driver and says "hardware present: yes".  Strange.

---

