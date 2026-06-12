---
title: "ubuntu fresh install, cannot locate os?  8.04, 8.04.1 &amp; 8.10"
date: 2009-01-08
forum: Installation &amp; Upgrades
---

### Post by adam27 on 2009-01-08
Well, over the last week, I have installed the 3 mentioned versions of ubuntu (using 6 separate isos) onto an Asus eee1000(2 ssd drives, 8gb & 32gb).  Each time using unetbootin (versions 238, 276 and 304 from both winxp and ubuntu live, and once built by hand with custom bootloader and such).  For the first dozen or so installs, with various install changes, everything went fine until reboot at finish of install.  The pc hung here every time.  Upon hard reboot, single cursor flashed on the 2nd line of the dos screen, and hung again, every time.  

This time around, I am using 8.10.  Installed, rebooted as prompted, and it actually rebooted by itself this time, I thought all was well!  Upon reboot, it came up with the "[COLOR="SeaGreen"][SIZE="2"]reboot and select proper boot device or insert boot media in selected boot device...[/SIZE][/COLOR]" response.  I was pissed.  Got drunk, went to bed.  Today, I turned it on, grub came up, booted into ubuntu just fine, no problems.  (I think it was taunting me, the horrible little machine.)  Looked at some settings and stuff, restarted, and got the same '[COLOR="SeaGreen"]cannot find os[/COLOR]' error again.

What could be making this intermittent (though since then, its only given me the error, never again booted up correctly) error occur?  I've gone into menu.lst using a usb live boot, made some changes to the boot device (on suggestion from a user on a different forum), nothing has worked.  

Any help would be incredible.  I've been slaving on this thing constantly with no progress for the past 6 days, I'm seriously about to kill something.:mad:

---

### Post by Temposs on 2009-01-08
hi,
   Are you using ubuntu eee/easy peasy?

It's a derivative of ubuntu designed to work on the eeepc. Easy peasy is the new branding because they're not associated with ubuntu. I installed that and it worked fine on my asus eee 1000.

[http://www.geteasypeasy.com/](http://www.geteasypeasy.com/)

---

### Post by Temposs on 2009-01-08
Oh, and if you want to install Easy Peasy 1.0, please check this post on a few small kinks you might need to work out: [http://www.ubuntu-eee.com/forum/viewtopic.php?f=12&t=543](http://www.ubuntu-eee.com/forum/viewtopic.php?f=12&t=543)

Those issues are pretty small, though, so you should have a great experience with this distro :-) It's pretty nice!

---

### Post by Temposs on 2009-01-08
Double post, sorry, ubuntuforums is being wonky today

---

### Post by adam27 on 2009-01-08
Yes, the current version is actually eeebuntu (I think) the others were ubuntu eee.  Haven't tried easy peasy yet, waiting for a torrent version.

---

### Post by Temposs on 2009-01-08
Sweet, let me know how it goes!

---

### Post by adam27 on 2009-01-08
I'm doubting easy peasy will solve the issue, (it would be nice, but since each other os I tried failed, I'm skeptical).  I need to make *this* distro work, and soon.

---

### Post by Temposs on 2009-01-08
Oh yeah, there are some instructions to follow with how you install onto the partitions, too! You need to make sure you do it right, because there are two hard drives on the eeepc 1000.

Specifically, when you install, you need to do manual partitioning/formatting mode, then you need to reformat both hard drives as ext2 partitions, mount the smaller one to / and the bigger one to /home

I'm trying to find the wiki article on it, for more step by step instructions...

---

### Post by adam27 on 2009-01-08
Unfortunatly, I've tried that, same results.  Both with and without swap.  And with both as ext3.  And with boot option to hd0, /dev/sda, and /dev/sda1.  None worked.

---

### Post by Temposs on 2009-01-08
Here's a post on setting up your partitions: [http://www.ubuntu-eee.com/forum/viewtopic.php?f=11&t=293&p=1453&hilit=ext2+1000#p1453](http://www.ubuntu-eee.com/forum/viewtopic.php?f=11&t=293&p=1453&hilit=ext2+1000#p1453)

This partitioning business might have been your problem. See if you can follow this.

---

### Post by Temposs on 2009-01-08
Hmm, I'm not sure what's going on then...See if easy peasy works for you, still...

I have the same machine as you, so I'm not sure what's up...

---

### Post by adam27 on 2009-01-08
Yep, followed that exact post on one of my prior installs.  No go.  Later read that linux *always* needs a swap, so tried again with it used (as it is in the current, broken install).  Dunno which way is right, makes sense that it needs swap, after all windows *needs* a pagefile right?

---

### Post by Temposs on 2009-01-09
Well, I believe I disposed with the swap, and the machine seems to run just fine. I'm not an expert on file systems, so I can't answer that technical question very authoritatively. I don't think we went over different file systems in my computer architecture courses those few years ago...

I just have my own experience on this particular matter.

---

### Post by adam27 on 2009-01-09
I'm beginning to think the issue might start with the usb install.  Did you use this method or use an external cd drive?  Every time I did the '*check cd for defects*' it returned at least one error.  And I tried it at least 20 times, on different drives, with different loaders, ect, ect...  I'd like to try the cd boot/install method to see if it makes a difference.  Will try EP (found it on miniova, currently down:() and see if that can solve the issue.  If not, hopefully I can find someone local who will let me use their external cd for an hour or so...

---

### Post by Temposs on 2009-01-09
I believe I used the method described on [this page]("http://www.ubuntu-eee.com/wiki/index.php5?title=Install:_from_a_Live_Ubuntu_image_on_a_USB_stick") to write the installer to a USB drive. That seemed to work well for me.

I used a 1GB SanDisk Cruzer Titanium, though I doubt that makes a difference ;-)

EDIT: Oh, sorry, I used the "How to configure a USB stick manually" section of that page. I saw you used the Unetbootin or whatever it is.

---

