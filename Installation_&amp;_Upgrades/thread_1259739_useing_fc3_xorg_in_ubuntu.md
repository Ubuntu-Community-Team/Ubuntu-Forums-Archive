---
title: "useing fc3 xorg in ubuntu"
date: 2009-09-06
forum: Installation &amp; Upgrades
---

### Post by dvdljns on 2009-09-06
Not a good title but here is the problem. I installed ubuntu on one comp. and  now I want it on a old hp. This hp has been running NT4 server but I found a page of howto's on linux that explains how to setup a linux server that will replace nt4. The problem is My 7500 radion ati card. ubuntu does not set it up right. Looking through my old linux disks I found a fedora core v3 that I have installed now. (using it for this post.)  Since it sets up the graphic card I was thinking maybe I could use the config files to set up ubuntu. Will that work? here is what I am working with.

A 333 mhz cpu
256 mb memory
128 mb ati vidio card.
ubuntu v3 live cd
ubuntu 5.10 install and live cd.

---

### Post by quixote on 2009-09-07
I had either that or a similar graphics card and had to totally customize my xorg.conf.  No harm in trying the fc3 settings.  The situation is so bad with that card, you have to try anything you can.  I'll dig out my old computer and post my old xorg here when I can. (Tomorrow?)

---

### Post by dvdljns on 2009-09-09
> **quixote said:**
> I had either that or a similar graphics card and had to totally customize my xorg.conf.  No harm in trying the fc3 settings.  The situation is so bad with that card, you have to try anything you can.  I'll dig out my old computer and post my old xorg here when I can. (Tomorrow?)

Good I put suse 10 on it for now. But I click the mouse button and go watch tv till it opens whatever I clicked. I have deb 3.1 here but only have disks 4 through 15. I lost 1.2and 3. Which if I remember right are the install disks.
maybe I can find a torrent Or get someone that has an old copy to donate it.

---

### Post by quixote on 2009-09-09
I've attached my old xorg.conf, and you can see that it's pretty unusual.  That was for my sharp MP30, which had lots of peculiarities.  Some of the xorg.conf won't apply for you, of course.  My screen resolution was 1024x768, running at 60Hz, and you'll want to be sure to substitute your own values as needed.

It took me about 8? 10? 15? tries to get it working, so be sure to keep backups of your old xorg, no matter how minimally it's working, because you may wind up with nothing but a black screen with this.

Hope it helps, though!

---

### Post by dvdljns on 2009-09-10
Thanks. And your right about that being diferant. Here is the one from fc3 I want to see if it works.

---

### Post by dvdljns on 2009-09-14
Is there a command that I can use to change the xorg.conf from the fd to the one my comp. I need it to replace the one on my comp.

---

### Post by quixote on 2009-09-15
Sorry, what's "fd"?

I'm not sure from what you've said, how familiar you are with editing xorg.conf, so this may all be very old hat for you.  Just for general info:

xorg.conf is an ordinary text file.  To replace it, you name your new file "xorg.conf" and put it in /etc/X11/.  ```
$sudo cp */path/to/new-xorg.conf* /etc/X11/xorg.conf
```

[COLOR="Red"]If there are mistakes in the new xorg.conf, it can make your display unreadable.[/COLOR]  Your barebones, text-based console display will still be available.  Being text-based, it doesn't need X windowing capability.

For that reason: 
 -- [COLOR="Red"]Always make a backup of your working xorg.conf before making changes[/COLOR].
 -- Know how to access it in a command line mode:

If your graphical display is totally messed up: 
1) Boot into recovery mode, and choose "root access with networking." You can destroy your system in this mode, so be sure not to make typos.
2) ```
#cp */etc/X11/xorg-conf-working-backup* /etc/X11/xorg.conf
``` (You're already root, so no need to use "sudo")

Then type "exit" at the command prompt, and you'll be back at the menu where the first choice is "continue with normal boot."

---

### Post by dvdljns on 2009-09-16
No! What I mean is I do not know enough command line to replace the old file with the new one in the floppy drive (fd). I looked up vi (thats the only editer I can get to open up, maybe the only one I have on here.) But for some reson after editing it will not close. The instructions said to push q to close it but that does not work. I have to reboot and I loose everything. What I need is something like the move command in dos. If you use the move command in dos it overwrites any file with the same name.

---

### Post by quixote on 2009-09-17
The copy command ("cp") will overwrite the destination file, like the DOS mv command.

If you're copying from a floppy, you will a) need to be sure the floppy is mounted first (ie visible to the computer), and b) if it mounts automatically, you'll need to know what linux is calling it.

To see what's mounted and where, you can use```
mount -l
```The output is confusing because it lists all sorts of system stuff you don't need.  But somewhere in there should be a few /dev/hd0, /dev/sda, and, if you're lucky, even a /dev/fd0.  The latter is the usual designation for a floppy, but by checking disk sizes, it should be possible to tell which one is your floppy.  Note the mount point.  Let's say it's /media/floppy.  Then the copy command would be ```
sudo cp /media/floppy/*xorg-new.conf* /etc/X11/xorg.conf
```

Vi is an interesting piece of work all on its own.  Are you sure you don't have nano?  That's a good bit simpler.  I guess you probably already know that there is a command mode (default when you start), and an insert mode (hit i to enter insert mode).  Hit esc (I think!  not sure) to get back to command mode.  In command mode, hit w to write, and then q to quit.  If you've made a mistake and just want to quit without saving, I think it's !q.  Type "man vi" in a terminal for the full story.

---

### Post by dvdljns on 2009-09-17
For some reason it did not install any man pages. but I went on the web and look up the manual. Vi is just not working right. Does anyone know why ubuntu has such a problem with ATI cards. nvidia and ATI is the most common cards in use. I will try the cp command tomorrow. Thanks!

---

### Post by quixote on 2009-09-18
It's actually the fault of the manufacturers.  They refuse to give the data necessary for the community to make open source drivers.  (The same problem also with Broadcom wireless.)  That means the drivers have to be reverse engineered, which is a tricky process and often has buggy results.

However, that doesn't help us users much, since we just want it to work! :/

Weird, that vi isn't working right.  I've never heard of that happening before.  It's generally bulletproof.

---

### Post by dvdljns on 2009-09-19
I understand that a lot of companies hold back info but that does not apply to drivers that other flavors of linux can setup. I noticed that the distros that setup this card use xfree86 not xorg. another thing, and I know this is only a problem for beginners like me but where are the tools  like superprobe and xfree86config. Linux has gained a lot but it has lost a lot too. All I needed is to open the config file and edit it. This card needs that ati {server?} using the old Mach64 specs. Everything is in xfree86.there is no secret drivers involved.

Sorry about the rant but linux pushes for new users to install and then seems to go out of their way to make it harder on us :lolflag:

---

### Post by quixote on 2009-09-19
*then seems to go out of their way to make it harder on us*

Seriously.  And I'm not sure I'd put a "lol" after that.  More like a :confused: [-o< :twisted:

---

### Post by dvdljns on 2009-09-19
> **quixote said:**
> *then seems to go out of their way to make it harder on us*

Seriously.  And I'm not sure I'd put a "lol" after that.  More like a :confused: [-o< :twisted:

 No it is funny! The first time I ran across linux I was running win95 and it only had the drivers that tarvold used. since then I have watched and downloaded diferant distros and checked them out every so often. The only thing I have found consistant is that development has been opposate of the stated mission of the advertisements. Oh well. this is getting off topic so I am marking the thread solved and moving on.
F.Y.I. I solved it by getting my hands on a 8.04 disk and loading that.:(

---

