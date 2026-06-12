---
title: "Ubuntu server hangs at &quot;Starting up...&quot;"
date: 2009-07-06
forum: Installation &amp; Upgrades
---

### Post by heller_barde on 2009-07-06
Hi guys!

I have an [ALIX 1D]("http://pcengines.ch/alix1d.htm") ssh/git/svn server. At first, I had arch linux on it, but because the AMD Geode in the server only has an i586 architecture, I had to compile everything for myself. Recently I installed Ubuntu on it, and everything went fine for a few weeks, and I was very happy with it.

Yesterday I upgraded and restarted, but the Server wouldn't come up again. It is stuck right after I press <enter> in GRUB.
```
Starting Linux (hdX,Y) <some UUID>
Starting Up...
```
And that's all. It hangs there for at least 20 minutes, I always broke it off after that. 
Can someone tell me whether that is still GRUB unable to load the kernel or the initramfs, or already the init system failing?

I looked through the threads I found on google about ubuntu and hanging at that stage. Nothing worked so far.
I connected the Compact Flash Card to my Desktop Computer. I mounted it, chrooted into it, and I tried the following things:
[LIST]
[*]appending those options to the kernel line in menu.lst: ```
noquiet nosplash verbose
``` and removing these: ```
quiet splash
```
[*]reinstall Grub by ```
grub> root (hd3,0)
grub> setup (hd3)
grub> quit
```
[*]aptitude reinstall linux-2.6.28-13-generic
[*]update-initramfs -u all (or something like that, it updated the initramfs)
[/LIST]
Nothing helped, it's always the same. Does anybody have an idea what i could do?

cheerio 
Phil

---

### Post by ajgreeny on 2009-07-06
I occasionally had the same problem with my desktop, and suspected that for some weird reason it related to the use of UUID in the /boot/grub/menu.lst, so I changed my menu.lst back to the old system of using ```
root   (hd0,1)
```and have not had the problem since.

I honestly have absolutely no idea why it should make any difference to booting, the UUID was correct, as mostly it worked OK, and I checked it, anyway, but the edit seems to have got rid of the problem.

Give it a try, or post your menu.lst (menu only, not all the stuff at the top, just the list at the bottom) so we can check that, along with the output of ```
sudo blkid
``` and ```
sudo fdisk -l
```just to be sure everything is correct.

---

### Post by heller_barde on 2009-07-06
Wow, replacing the "uuid <uuid>" thing with the "root (hdX,Y)" thing worked right away. I could have thought of that myself *head-table* 

I wonder what strange bug that is... Oh well, it's working again :)
Thanks a lot for the quick response!

cheerio Barde

---

### Post by ajgreeny on 2009-07-06
I'm so glad this worked for you, but I wonder why it has for you and me.  I have two ide disks on my oldish machine, not sata, and wonder if this has any bearing on the problem.  What type of disks do you have heller_barde?

Has anybody got an explanation for this?  If grub is going to cause this problem in the future it would be good for others to know about it, as it is so simple to overcome.  I shall now go and search launchpad for any mention of this in bugs already known about.

---

