---
title: "Upgrade to 9.10 using alternate cd."
date: 2009-10-30
forum: Installation &amp; Upgrades
---

### Post by shankru85 on 2009-10-30
Hi,

I have an internet connection which is just 256Kbps and hence thought it is not wise to do a network upgrade since it would take a long time and i would not be able to interrupt it for any reason (say for example power cut, power cuts are frequent in India.) .

So i downloaded the alternate cd using torrents. and followed the instruction given in the ubuntu website. But it does download the files from internet just because i have internet connection even i though gave the answer no for it to look out for updates in the internet. I tried disabling my LAN and then tried to upgrade. It goes upto fetching the files it could from the cd and then trying for some time to fetch rest of the upgrades from the internet, says Failed to fetch index : blah blah and stops the upgrade.

I remember having done the upgrade from 8.10 to 9.04 successfully using alternate cd without having to worry about these network updates? Why now i am forced to do this ? Now the upgrade is saying 10 hours remaining which is a bad thing. Anybody have any bright idea ?

---

### Post by celem on 2009-10-30
For what it is worth, I downloaded the alternate install, burned it to a CD, popped into the drive of my running 9.04 machine. A dialog automatically popped up saying that there was an upgrade disk in the CD and asked if I wanted to upgrade using it. I clicked yes, said no to the update from the internet and I said No. Then the upgrade proceeded normally.

I never ran any arcane commands as shown on the web site. After popping in the CD it was all automatic.

---

### Post by krisgesling on 2009-10-30
Hey shankru

I'm having the same problem at the moment. I tried just pressing No to the internet access dialog but it starting downloading anyway so I switched off the wireless to see if it would revert back to the mounted disk image but no dice it just said it couldnt connect and exited.

I'll probably just head to uni and download it on their connection but it would be good if we could find a solution for anyone else encountering the same problem.

cheers
Kris

---

### Post by shankru85 on 2009-10-31
> **krisgesling said:**
> Hey shankru

I'm having the same problem at the moment. I tried just pressing No to the internet access dialog but it starting downloading anyway so I switched off the wireless to see if it would revert back to the mounted disk image but no dice it just said it couldnt connect and exited.

I'll probably just head to uni and download it on their connection but it would be good if we could find a solution for anyone else encountering the same problem.

cheers
Kris

Hey Kris, Thanks for caring to reply that you have a similar problem. Anybody know any solution to this problem ? :(

---

### Post by limejuice on 2009-10-31
I have run into the same problem. Looks like a major bug in the offline installation.

I downloaded ubuntu-9.10-alternate-amd64.iso using bittorrent which went very fast.  Then I mounted the ISO and ran the upgrade.
sudo mount -o loop ~/Desktop/ubuntu-9.10-alternate-i386.iso /media/cdrom0
gksu "sh /cdrom/cdromupgrade"

I also said No when it asked if I wanted to get the latest updates from the internet. The question dialog said that it would not access the internet.

But after upgrade started, it quickly got to file 1106 of 1751, but after that it started to download each file over the internet!!!

Seems like a major bug. Hopefully someone has a workaround.

---

### Post by limejuice on 2009-10-31
Just for the heck of it, I reran the upgrade, this time answering "Yes" to check for latest updates on the internet.

This is actually working even worse as I get an error:

W:Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/karmic-updates/restricted/binary-amd64/Packages](http://us.archive.ubuntu.com/ubuntu/dists/karmic-updates/restricted/binary-amd64/Packages)  404 Not Found [IP: 130.239.18.165 80]
, W:Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/karmic-updates/universe/binary-amd64/Packages](http://us.archive.ubuntu.com/ubuntu/dists/karmic-updates/universe/binary-amd64/Packages)  404 Not Found [IP: 130.239.18.165 80]
, E:Some index files failed to download, they have been ignored, or old ones used instead.

And then the upgrade exits. 

I give up for now. Too many showstopper issues for me. Better to wait a few days to see if some of these problems get fixed.

---

### Post by limejuice on 2009-10-31
One last thing I tried was to change the server in sources
System-Admin-Software Sources
Then hit Download From... dropdown... and I selected us server.

Then I reran cdrom upgrade and answered "Yes" to download latest source, and this time it went through.

Again it zoomed through first 1100+ packages, but then resumed downloading again.  Right now it is at 1146 of 1751,  About 10 hours remaining at 25 kb/sec.

So, right now I see the exact same behavior whether I select "No" or "Yes" to the question do I want to get the latest packages. It doesn't seem to make any difference.

---

### Post by limejuice on 2009-10-31
I let the upgrade run overnight, and when I woke up this morning it was on "Installing the upgrades".

However, there was an error message displayed:

----
Could not install '/cdrom//pool/main/d/devicekit-power/libdevkit-power-gobject1_011-1ubuntu1_amd64.deb'

The upgrade will continue but the '/cdrom//pool/main/d/devicekit-power/libdevkit-power-gobject1_011-1ubuntu1_amd64.deb' package may not be in a working state. Please consider submitting a bug report about it.
cannot access archive: No such file or directory
----

I hit OK, but then a similar error for the different package appeared, and then another error, and another, and another... eventually I got tired of hitting OK.  So, right now, but upgrade is @#$%ed up.  It looks like it can't find the packages where it is expected ... maybe because it is expecting them to be on the cdrom but they aren't?  It could be related to original problem that answering "No" to get latest packages doesn't seem to work.

---

### Post by Jesus_Valdez on 2009-10-31
I had a similar problem.

I tried to upgrade using the alternate CD and failed. The upgrade braked almost at the end, leaving a corrupt system, the a re-tried and face the internet-problem, I let it ran overnight and, again, nothing happens, the upgrade stopped at some point.

I endend up doing a format and a fresh install.

I hope there's a bug report, i tougth it was just me with bad luck.

---

### Post by don_xvi on 2009-10-31
Same problem here, I'll subscribe to see when/if someone much more knowledgeable than I can post a solution.
Mounted the alternate ISO x64 but, even when I tell it "no internet" and disabled the network, it tried 3 times to fetch the upgrades, then said "Could not download the upgrades"... "Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/..." for probably every package.

---

### Post by don_xvi on 2009-10-31
Hmmm, I went into Update Manager and changed my software source for downloads and also checked the box next to my ISO image, then tried the upgrade again and it seems to have worked properly.

**I'd suggest those having these problems go into Update Manager, then in the Settings button, you can check the "Installable from CD-ROM/DVD" box of the Ubuntu Software tab.**  Note that I had problems exiting Update Manager after I did this and had to open up System Monitor to kill the process, but now the upgrade is working.  If just checking the CD-ROM box doesn't fix it, you can try changing your software repository, although I'm pretty sure my system didn't download anything from the internet this time.

---

### Post by shankru85 on 2009-11-01
Sad to see so many with the same problem. Hope Ubuntu doesnt have such bugs in the next release. As for me, the upgrade finished and went thro smoothly. :D

---

### Post by hariks0 on 2009-11-02
I think, it is due to some corrupted download of the alternate iso. I will wait for a confirmation from you.

---

### Post by rbaleksandar on 2009-11-02
> **don_xvi said:**
> 
**I'd suggest those having these problems go into Update Manager, then in the Settings button, you can check the "Installable from CD-ROM/DVD" box of the Ubuntu Software tab.**

  Well, by me in the field for **Installable from CD-ROM/DVD** there's only **Cdrom with Ubuntu 9.04 'Jaunty Jackalope'**.
  I tried running the command **gksu "sh /cdrom/cdromupgrade"** in order to make the upgrade prompt window to appear, but nothing happened. :( Can't afford doing an internet-based upgrade during the day (I have a speed of the awesome 50kB/s so it takes approximately 10 hours to download it all), and I don't want to stay awake after 4 o'clock in order to do that (speed is 350kB/s).

  Help please. :)


EDIT: Ahhhh, I think problem's solved. I've downloaded the Ubuntu 9.10 desktop CD, but I have to download the alternate CD. Damn it... I advice people having problems first to check which ISO they've downloaded. :D

---

### Post by schenckel on 2009-11-07
hey guys!

i had a similar problem with using the alternate iso to upgrade to 9.10. as my internet connection is unrelieable and slow(really really slow) i cannot affort a netork upgrade...  so here is what i did to solve it:
*sudo mount -o loop *ubuntu.iso* /cdrom *
[I]sudo apt-cdrom -m -d /cdrom add /media/cdrom0/
sudo apt-get update 
sudo apt-get install build-essential[/I]

then go to the system/administration and choose the update manager.
and the 'third party software' tab there should an entry with karmic-somethingidontremember
uncheck all other sources!
then press alt+f2 and enter *gksu "sh /cdrom/cdromupgrade"* and if you are lucky it should work!

---

### Post by perdubug on 2009-11-29
Yes, it's works! schenckel's solution is good for my ubuntu 9.04 upgrading....

---

### Post by sblanzio on 2010-05-02
this bug is still present even in 10.04!

I cannot upgrade via alternate cd without a internet connection!
What's the point to download the alt-cd if it doesn't use that?

I relly hope we can get rid of this one day.

bye

---

### Post by flarkit on 2010-05-02
Same gripe here when upgrading from 9.10 via Alternate CD, with a 384K line. I downloaded the Alternate CD, did a full update (180Mb!!) rebooted and then ran the upgrade from the CD. It started reading files off the CD, then switched over to downloading software and wound up grabbing 700Mb online. This is insane!

So far, I'm once again disappointed by the shoddy upgrade to an existing OS installation. Compiz didn't work properly, nor did Wine and now I see that sound for Youtube clips in FF doesn't work either. The big concern is seeing FF freeze on video clips, whilst the Virtual Memory usage for "firefox-bin" ramps up to 2.5Gb. What the heck is going on?
:confused:

On the positive side, pretty much everything else seems to be working fine. Hopefully Lucid Lynx will grow on me.

---

### Post by sblanzio on 2010-05-02
I think i solved that. I tried the solution above but only messed everything even more.

This is what i did instead:

I downloaded and replaced sources.lst file with a fresh default one I got here: [http://ubuntuguide.org/wiki/Ubuntu:Karmic](http://ubuntuguide.org/wiki/Ubuntu:Karmic)

Then I went in system->admin->sources manager and clicked "Add CDROM", and deselected all others sources listed keeping only the cd source active.
Closed, updated, and launched:
gksu "sh /cdrom/cdromupgrade"
in console.

You can immediately notice the difference because at the upgrading confirmation query it doesn't show you any estimated download time anymore.

So far so good.. i'll let you know if I get any other trouble

---

