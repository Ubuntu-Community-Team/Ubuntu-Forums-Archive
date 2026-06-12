---
title: "freezes during installation"
date: 2009-02-22
forum: Installation &amp; Upgrades
---

### Post by flybyjoy on 2009-02-22
i am attempting to install ubuntu 8.10 Live CD on my computer. It freezes at the same place everytime, after partioning. 

I currently have suse10.1. installed. I have tried every install option. i am not sure I am partioning correctly. Here are some of the  system specs.

AMD Athlon(tm) XP 1800+ - assuming 64 bit, but not sure
ram = 2gb
disk space = 500gb
cat diskstats:

3  0 hda 25046 55618 890770 434944 22766 363248 3850256          4294966651 1811208 3559888156

3  1 hda1 34240 69692 21 120
3  2 hda2 29401 621246 13164 105200 
3  3 hda3 239 589 0 0
3  4 hda4 3 6 0 0
3  5 hda5 13576 194952 31603 252768 
3  6 hda6 629 629 0 0
3  7 hda7 587 587 0 0
3  8 hda8 587 587 0 0
3  9 hda9 587 587 0 0
3  10 hda10 149 596 0 0
3  11 hda11 587 587 0 0

Problem: I go thru the install process, but once partioning is finishes, the copying files freezes at %23.  Everytime %23.

There are no log files to look at as far as I know. Any ideas?

---

### Post by dstew on 2009-02-22
Are you sure the CD is good? Check the CD integrity (look for a menu item or options choice at the first screen when you boot the CD).

---

### Post by flybyjoy on 2009-02-22
yes. i have checked the integrity of both disks. I have downloaded the iso image and i bought a disk and the same thing happens on both disks. I have also tried booting up the live disk without installing and it just freezes. 

NOTE: I have tried these options on my windows vista box. the live cd just froze, but i was able to install it on the vista box. it appeared on boot menu, but froze during boot. 

On my linux box (suse 10.2) the live cd (no changes just run it off of the cd) it freezes when the logo appears. When I install ubuntu it freezes after the partioning during the "copying files" process. always at 23%. 

I wish there was some way of checking log files to see why it freezes. 

thanks!

---

### Post by dstew on 2009-02-23
You can boot the Live CD with a modified kernel line to see the kernel messages. I think at the first menu you pick "Options" by pressing F4 or F6. You can then edit the kernel line. Remove "quiet splash", press enter to save the edited line, then 'b' to boot. Maybe you can get a clue by looking at the messages.

---

### Post by flybyjoy on 2009-02-23
i'm about to give up. i booted up the live install and i deleted the quiet splash(thank you) and for some reason i was able to look at syslog while the installation was running.
First of all, it configures my hd as if it is scsi; it isn't. there are all kinds of errors, but it always freezes until it is configuring python.  this happened on my other machine also.

Now, the strange thing is that the next 4 times i tried rebooting,
it froze with "kernel panick: not synching: fatal exception in interupt. then i booted again and it started up. what the he--.?

i am having the same problem on my windows dual-core.
i did get ubuntu to install on the windows machine. after i choose ubuntu on dual boot menu it of course just freezes again. 

i have the syslog if interested, but only up until just before it freezes. 

i just wanted to try ubuntu and see if i like it.

i have a perfectly good version of suse 10.1 so i will stick with that.

thanks for responding. let me know if you come up with something.

thanks!

---

### Post by troegs on 2009-02-24
So I had this problem myself about two months ago. i searched EVERYWHERE for an answer. I burned cd after cd. each time the install would fail at different point. I finally ran into a post that mentioned my exact troubles and the guy said, "burn it at the slowest speed possible". So naturally I say to myself what an idiot, AS IF that could have anything to do with it. Well at the time I figured that since I was now down 4 or 5 dvds and as many cds I'd give it a shot. Sure enough it did the trick. Oh, and in case anyone was wondering, the MD5checksums were a spot on match for all the faulty cds. It was in fact the burn speed of the cd. 

I talked to one of my CS professors and he said that it had something to do with tags being coded into the cd when it's burned. When the rom sees the tags it says, "hey I can read it at 16x" when in actually because you are running on stripped down drivers, and your computer doesn't realize that it could stuff every last bit of the cd in ram and not think twice, it feels as it thinks its getting a buffer overrun. 

Anyhow, long story short, burn it at 1x if possible, 2 is okay and 4 is the limit, (at least for some systems such as mine). As far as my explanation, I'm sure I didn't get it quite right. It's 4am and I've been away for just under 48 hours. Flame all you want, I'll be the one laughing when this guy comes back to post that it did the trick. (hopefully, I'm pulling for ya bud).

Lemme know if that solved it for ya.

---

### Post by jimmyjazz951 on 2009-02-24
I had/have a similar problem with 8.10 as well.  Looking at your specs you may be having this same problem.  You might want to have a look here: [https://bugs.launchpad.net/ubuntu-release-notes/+bug/272247]("https://bugs.launchpad.net/ubuntu-release-notes/+bug/272247")

---

