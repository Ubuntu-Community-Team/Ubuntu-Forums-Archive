---
title: "Upgraded to Jaunty, unable to get into GDM"
date: 2009-09-08
forum: Installation &amp; Upgrades
---

### Post by BassKozz on 2009-09-08
I recently upgraded my laptop (Dell Inspiron e1505) from Intrepid (8.10) to Jaunty (9.04). I ignored the warnings ([http://www.ubuntu.com/getubuntu/releasenotes/904](http://www.ubuntu.com/getubuntu/releasenotes/904)) and dove in head first, thinking that these problems must have resolved themselves since the April release of Jaunty, only to find out... Thats not the case.

The splash screen shows fine but after that all I get is a couple of pixels in a row or two across the screen, instead of what usually would be the login screen.
**EDIT**: I just uploaded a video to better help describe the problem: [http://www.youtube.com/watch?v=7vLEi68wrQI](http://www.youtube.com/watch?v=7vLEi68wrQI)

After trying all of the suggestions mentioned in the release notes (including this one: [RevertingIntelDriverTo2.4]("https://wiki.ubuntu.com/ReinhardTartler/X/RevertingIntelDriverTo2.4")), I did some googling and searching of the forums and I gave this a shot: [HOWTO: Jaunty Intel Graphics Performance Guide]("http://ubuntuforums.org/showthread.php?p=7104256#post7104256")

And yet, nothing has worked... So I come to you the great people of the community for support. [-o< Can someone please help me?

---

### Post by RabidWeezle on 2009-09-08
If you have another computer handy, try burning a jaunty cd and see if you can go live with it, and if you can, you might have just had an error during the update process. I would try to backup my files to a usb hard drive and do a fresh install.

---

### Post by BassKozz on 2009-09-08
RabidWeezle,

I'd really rather not have to format and fresh install if I don't have to.
I just uploaded a video to better help describe & diagnose the problem.
Check it out here: [http://www.youtube.com/watch?v=7vLEi68wrQI](http://www.youtube.com/watch?v=7vLEi68wrQI)
Or to jump right to the part that shows the problems: [1minute and 5seconds in](http://www.youtube.com/watch?v=7vLEi68wrQI#t=1m5s)

I also did as you suggested and downloaded and burned a Jaunty LiveCD, and gave that a go.  While I was able to get it to fully boot the desktop, I did notice that during the bootup process it is experiencing the same issue, yet it is able to get past the problem on it's own with out any intervention from the user.
Checkout the full video here: [http://www.youtube.com/watch?v=auEn5-QJDEQ](http://www.youtube.com/watch?v=auEn5-QJDEQ)
Or jump right to the spot that shows the problem here: [2minutes and 4seconds in]("http://www.youtube.com/watch?v=auEn5-QJDEQ#t=2m4s")

So how come the Live BootCD can get past it, but the installed version (on my hard drive) can't?
TiA,
-BassKozz

---

### Post by BassKozz on 2009-09-09
:Bump:

---

### Post by BassKozz on 2009-09-09
:bump-again:
I really don't want to have to format and re-install, is there someone who can PLEASE help me [-o<

---

### Post by dreadnought1906 on 2009-09-09
I am having a very similar problem, also with an Intel chipset, but in my case on a desktop machine.  My thread was here: <[http://ubuntuforums.org/showthread.php?t=1262284]("http://ubuntuforums.org/showthread.php?t=1262284")>.

Mulligan also seems to be having a similar problem: <[http://ubuntuforums.org/showthread.php?t=1262360]("http://ubuntuforums.org/showthread.php?t=1262360")>, although he/she doesn't specify whether or not an intel graphics card is involved.

Could this rash of new problems be caused by a recent update, perhaps?

---

### Post by dreadnought1906 on 2009-09-09
This person seems to have had a very similar problem back in June:
<[https://lists.ubuntu.com/archives/universe-bugs/2009-June/099493.html]("https://lists.ubuntu.com/archives/universe-bugs/2009-June/099493.html")>

He posts a 'workaround' here, but I don't understand how it works or how it's different from my machine:
<[https://lists.ubuntu.com/archives/universe-bugs/2009-June/099550.html]("https://lists.ubuntu.com/archives/universe-bugs/2009-June/099550.html")>

Does anybody know what's going on in this example?

---

### Post by BassKozz on 2009-09-09
> **dreadnought1906 said:**
> I am having a very similar problem, also with an Intel chipset, but in my case on a desktop machine.  My thread was here: <[http://ubuntuforums.org/showthread.php?t=1262284]("http://ubuntuforums.org/showthread.php?t=1262284")>.

Mulligan also seems to be having a similar problem: <[http://ubuntuforums.org/showthread.php?t=1262360]("http://ubuntuforums.org/showthread.php?t=1262360")>, although he/she doesn't specify whether or not an intel graphics card is involved.

Could this rash of new problems be caused by a recent update, perhaps?

Does your problem look the same as mine does on the youtube video I posted: [http://www.youtube.com/watch?v=7vLEi68wrQI](http://www.youtube.com/watch?v=7vLEi68wrQI)
?

> **dreadnought1906 said:**
> This person seems to have had a very similar problem back in June:
<[https://lists.ubuntu.com/archives/universe-bugs/2009-June/099493.html]("https://lists.ubuntu.com/archives/universe-bugs/2009-June/099493.html")>

He posts a 'workaround' here, but I don't understand how it works or how it's different from my machine:
<[https://lists.ubuntu.com/archives/universe-bugs/2009-June/099550.html]("https://lists.ubuntu.com/archives/universe-bugs/2009-June/099550.html")>

Does anybody know what's going on in this example?

Thanks for the info, I updated the bug report on Launchpad: [https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/385551](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/385551)

---

### Post by mulligan on 2009-09-10
you stated on our problem might be the same. i do not think it is. i can get it to work until i install the graphic card then it crashes. it works perfectly until then. i will do some research then see what i can do. if i solve my problem i will tell you how. if i solve my problem.

---

### Post by BassKozz on 2009-09-10
New Bug Report Filed: [https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/427531](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/427531)

---

### Post by rgsteele on 2009-09-10
I've seen a similar issue in a computer with bad RAM. Have you tried running Memtest86+ from the live CD or the boot menu?

---

### Post by dreadnought1906 on 2009-09-10
Having ascertained that the live CD version of Jaunty works on my computer I have cleared the error by taking the rather drastic step of completely re-installing Kubuntu from scratch.  Fortunately, I had already taken the precaution of keeping [root] and [home] on different partitions, so it was possible to do this without effecting my files or settings.  My computer now works properly, more or less.

This would seem to imply that this problem is caused by the upgrade from Intrepid, rather than by the default setup of Jaunty itself.

---

### Post by arashispencer on 2009-09-10
I'm having a Kubuntu Hardy Heron version installed in my external hdd... I was unable to update it (no internet connection) for quite sometimes and when I finally able to do so, it was, by itself, downloading and upgrading to new version, of course, which is Jaunty...

But after it prompted me to restart, I am unable to bypass to boot.. Compared to your youtube, mine is 2.6.24-24... I can't seem to get it to search for new updates although I manage to get in with lower ones (2.6.22-22)...:confused:

---

### Post by BassKozz on 2009-09-11
> **rgsteele said:**
> I've seen a similar issue in a computer with bad RAM. Have you tried running Memtest86+ from the live CD or the boot menu?
Just ran memtest for 3+ hrs (3passes) and no errors

---

### Post by BassKozz on 2009-09-11
FIXED !!!

I was looking for the answer in all the wrong places, the video card I have is an ATI video card, not intel...
So first I reverted the settings I made from this guide: [HOWTO: Jaunty Intel Graphics Performance Guide]("http://ubuntuforums.org/showthread.php?p=7104256#post7104256")

Then I used this wiki to fix my ATI graphics x1400 driver settings: [http://wiki.cchtml.com/index.php/Ubuntu_Jaunty_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Jaunty_Installation_Guide)
Problem Solved

---

### Post by XDevHald on 2009-09-11
> **BassKozz said:**
> FIXED !!!

I was looking for the answer in all the wrong places, the video card I have is an ATI video card, not intel...
So first I reverted the settings I made from this guide: [HOWTO: Jaunty Intel Graphics Performance Guide]("http://ubuntuforums.org/showthread.php?p=7104256#post7104256")

Then I used this wiki to fix my ATI graphics x1400 driver settings: [http://wiki.cchtml.com/index.php/Ubuntu_Jaunty_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Jaunty_Installation_Guide)
Problem Solved

Excellent job and researching your issue by yourself! Enjoy your desktop.

---

### Post by BassKozz on 2009-09-11
> **Steven Myers said:**
> Excellent job and researching your issue by yourself! Enjoy your desktop.

Yeah, except I must say I am quite embarrassed I was barking up the Intel tree, when I should've been looking for an ATI solution... :DOH: ](*,)
Next time I'll make sure to check the vendor of my video card prior to looking for a fix.

---

### Post by BassKozz on 2009-09-28
Just a quick update...
I noticed that I couldn't get compiz working and my graphics were VERY laggy, so I went on IRC #ubuntu and found a great person to help me out :KS soreau :KS
After switching the conversation over to the much quieter #compiz, he helped me figure out that I still had old fglrx drivers installed by running:
```
dpkg -l | grep fglrx
```
and then 
```
sudo aptitude purge fglrx-amdcccle fglrx-kernel-source fglrx-modaliases xorg-driver-fglrx
```
After a quick cold-boot, my graphics were back up and running smoothly.  And compiz was working to boot.
Just to confirm: ```
glxinfo|grep renderer
OpenGL renderer string: Mesa DRI R300 20060815 x86/MMX/SSE2 TCL
```
Thanks :KS soreau :KS !!!

---

### Post by rreese6 on 2009-09-29
LOL,:lolflag: A classic mistake we have all made at one time or another..

"I just can't understand why Intel doesn't make a better ATI driver!"

I had been watching this thread to see the outcome, I never expected this one, I laughed so hard when I read your "SOLVED" Post...reminds me of my self a few times in the wee hours of the morning trying to get Linux to install on my microwave
....Thanks for the Videos and your honest post about the mistake...

Cheers!
:popcorn:

---

