---
title: "No GUI - no video after CD boot"
date: 2009-02-20
forum: Installation &amp; Upgrades
---

### Post by lachelp on 2009-02-20
(Well, not really _all_ variants...)

Hi all,

I have an admittedly _o_l_d_ Acer C100 Travelmate tablet. 256MB RAM (it's max) 40GB drive, external USB CD that I'm trying to get Xubuntu installed on. I've booted with both Xubunu & Ubuntu v8.10 CDs.

With both, the boot sequence goes like this:
Get boot menu, press F6 and remove "quiet" & change to "nosplash",
Choose "Run from CD" or "Install",
Startup sequence goes through to the point of starting Gnome,
Black screen.

The system has not frozen as it still finishes up a bit of CD activity and I can change the status of the Caps & Num lock keys.

I have searched quite a bit and found xorg.conf files that I could possibly use if I got it to boot usably, I have also tried various forms of "xforcevesa" & "xdriver=vesa" in grub's boot line - all to no avail.

I have here the HTML form of a PDF file with the xorg.conf file for Ubuntu v8.04 that worked for one guy (but of course I have to get it installed first to use it...):
[http://209.85.173.132/search?q=cache:UH76zhpEOZIJ:www.csd.uwo.ca/~rhu8/research/InstallUbuntuNote.pdf+%22xorg.conf%22+ubuntu+acer+c100&hl=en&ct=clnk&cd=3&gl=us&client=firefox-a](http://209.85.173.132/search?q=cache:UH76zhpEOZIJ:www.csd.uwo.ca/~rhu8/research/InstallUbuntuNote.pdf+%22xorg.conf%22+ubuntu+acer+c100&hl=en&ct=clnk&cd=3&gl=us&client=firefox-a)

Is there help for this old dog or is it time for the bone-yard?
(Speaking of which, Puppy Linux runs fine on this guy, but of course without the upgrades & Network Manager.)

---

### Post by taurus on 2009-02-20
256MB is just not enough memory to run the LiveCD to install Ubuntu.  Therefore, use the alternate CD to install it on your old Acer if you wish.  Better yet, use the Xubuntu alternate CD since XFce4 should run a little faster because it's a little easier on the system resources.

[http://www.xubuntu.org](http://www.xubuntu.org)[/code]

---

### Post by lachelp on 2009-02-20
Thanks taurus,  I've downloaded and am installing now.  Will report later.

But note that I had initially tried to install Xubuntu from live CD as I also thought that XFCE should be able to run on the old critter.

---

### Post by lachelp on 2009-02-20
That was a bloody mess.

Same problem after installation, with the addition that now my old dog will not boot from either external CD drive nor from any of the CDs that I've previously successfully booted with.

All CDs halt after the single ISOLinux line and never make it to the boot menu.

(Shades of a Windows virus...)

---

### Post by lachelp on 2009-02-20
Ok, no help there -- I downloaded Ubuntulite mini CD.  That was able to boot, running the install now...

---

### Post by lachelp on 2009-03-01
800x640 only, will not do 1024x768 (Cheating fix)

On many older laptops, after installing Ubuntu, and/or more likely, Xubuntu, the graphics adapter will not be detected correctly and you will be stuck with the 800x640 resolution on a monitor that can handle 1024x768.

I have figured out a cheating way of handling this that is simply booting with another Linux distribution (Puppy Linux - or more specifically, I used one of it's deriviatives called MacPup) that will be more likely to detect your video settings correctly, and then copying that configuration to your new installation.

It is very simple and pain free as can be proven by the fact that I, no Linux expert by any means, figured it out.  :-)

I have detailed it here if you need it:
[http://itdiaries.com/2009/03/01/800x640-maximum-display-with-ubuntu-linux/](http://itdiaries.com/2009/03/01/800x640-maximum-display-with-ubuntu-linux/)

---

