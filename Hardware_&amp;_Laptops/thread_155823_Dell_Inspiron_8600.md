---
title: "Dell Inspiron 8600"
date: 2006-04-05
forum: Hardware &amp; Laptops
---

### Post by gymsmoke on 2006-04-05
I promised to document my next "leap" into Ubuntu on a new platform, so here it is...
Dell Inspiron 8600
CD In... Away we go
All is well so far (language, keyboard, found both Broadcomm4400 and ipw2100 Wireless)
Select eth0 as primary
[!!] Configure the network
Network autoconfiguration failed
"Your network is probably not using the DHCP protocol (OH, YEA IT IS).  Alternatively, the DHCP server may be slow or some network hardware is not working properly. (AND HOW DO YOU THINK I D/L'd the Ubuntu ISO???)
<conitnue>
Retry Auto again... (hehe - maybe it's a DOS thing...)
Okay!
Hostname: Nebo
[!!] Partition disks
method:
Erase entire disk: IDE1 master (hda) - 40.0GB IC25N040ATMR04-0 (Bill G can kiss my axx)
#1 will be ext3 (wonder what reiser4 would be like on Ubuntu?)
#5 will be swap
I'd like to have decent slices, like /home, /tmp, /var separate, but 40Gb seems a bit wasteful to slice up the drive this way...
Write - Of course...
Creating ext3... Ok!
Installing the base system...
Installing remaining packages...
Time Zone - Eastern (for me)
[!!]
Set up users and passwords
Enter the name: gymsmoke , <continue>
(Not Sure Why, but this dialog came back with the user name already filled in and asked for it again...
[!!]
Set up users and passwords
Enter the name: gymsmoke, <continue>
[!!] Set up users and passwords
Choose a password: xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx
[!!] Set up users and passwords
Verify: xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx
Configuring apt...
Installing 'grub'
Finishing...
[!!] Finish installation
<remove cd>
reboot...
...Here comes virgin Ubuntu bootup
hotplug didn't get an OK ....
[Ubuntu Configuration]
Installing packages...
Logging on...
Ubuntu installed!
77 packages to install...
Installing updates...
done!
System is up to date...
(1:42) from scratch to done...
I'll post more with a few tweaks...

---

### Post by gymsmoke on 2006-04-05
First tweak - [https://wiki.ubuntu.com/FirefoxNewVersion](https://wiki.ubuntu.com/FirefoxNewVersion)
Firefox 1.5.1 ...
Installed clean, runs great

---

### Post by gymsmoke on 2006-04-05
Added FireFTP ... a handy little ftp client to have around in a pinch...
forgot the link...
[http://fireftp.mozdev.org](http://fireftp.mozdev.org)

---

### Post by gymsmoke on 2006-04-06
Alien and build-essentials (for all those little "extras") ...

---

### Post by gymsmoke on 2006-04-06
chkrootkit (for the paranoid in all of us)
debian-goodies (decent collection of package utils)

---

### Post by gymsmoke on 2006-04-06
gimp-browser and gimp-help files (for those who want to come up to speed on gimp)
gnupgp docs ...

---

### Post by gymsmoke on 2006-04-06
updated the repo files and setup skype...

---

### Post by teasum on 2006-04-07
I've got Breezy running on an Inspiron 8600 as well, and I'm having issues with power management--proper battery life indication, suspend to ram and to disk.  How is all that working for you?

---

### Post by gymsmoke on 2006-04-07
teasum~
I didn't do anything special to get acpi running properly.  Those functions ran 'out of the box' for me.

---

### Post by gymsmoke on 2006-04-07
Additions:
clamav - (and its dependencies)
clamtk (need to see what this really does for me - or anyone) - (And its dependencies)
-- Ok, all: clamav on Ubuntu 5.10 is BROKE! - this is the second time I've attempted to install this through synaptic and it DOES NOT WORK.  I'm going to check the Bugz list and file one if it hasn't been done yet. - DON'T INSTALL THIS
[http://ubuntuforums.org/showthread.php?p=899195](http://ubuntuforums.org/showthread.php?p=899195) (this is the thread i'm running to try and get this resolved)

---

### Post by gymsmoke on 2006-04-08
Not sure why but synaptic is broke atm for installing clamav automagically.
I got this running by running (sudo) apt-get install on the basic pieces, and then letting synaptic install the main package (clamav).
I also installed the gui front end to clamav, but there's no sign of it on any menu, even after a complete restart...

Just added firestarter (firewall)... that went smooth...
(outbound is permissive to blacklist traffic)
(inbound is restrictive to whitelist traffic)

---

### Post by Imrahil on 2006-04-20
Oh ubuntu how I love you. My 8600 now hibernates perfectly. It would not work on kernels prior to 2.6.15-20. May have something to do with the fact that I have 2 gigs ram. But now it works! Seems at least as fast as with xp, which btw never worked properly until a couple months ago when a patch was quietly released that fixes the notorious hibernate problems with 1gig or more ram. This was the last thing holding me back from using ubuntu on my 8600.

---

### Post by Imrahil on 2006-04-20
teasum, perhaps you will not have issues if you upgrade to dapper beta which uses a kernel that fixes power management issues.

---

### Post by m0nstr42 on 2006-05-10
> teasum, perhaps you will not have issues if you upgrade to dapper beta which uses a kernel that fixes power management issues.

I just thought I'd add my two cents.  I'm running ubuntu on an Inspiron 8600 and recently upgraded to dapper beta, but it did not fix hibernate or suspend :(  My wireless has never worked *quite* right, either.  It's usable, but some days it just doesn't seem to want to connect to certain networks.  The new drivers in dapper didn't fix it, in fact I reverted back to ndiswrapper, which seems to still be a little better.

The gnome battery monitor has always worked for me, but I did install the gdesklets acpi-desklet which didn't work quite right - I had to fudge with the .display file to get it to use the right units, etc and now it works just fine.

---

### Post by teasum on 2006-05-11
I've been using Dapper for a few weeks now (recently did a fresh install of Flight 7) and power management is still a huge issue, it seems.  My wireless is ok, but I haven't tried it out in public that much (i.e. coffee shops, school, etc.).  In any case, I am *really* hoping that the final Dapper release will work better on my 8600.  

I have two problems: 1) The battery monitor now is sketchy at best, and tends to drop drastically to near zero, followed by a forced shutdown.  Before you say it's the battery, it's not--this doesn't happen in XP.  2) The suspend-to-ram problem is just wierd.  It appears to go down correctly, but when I try to boot back up, I get full-screen colors, alternating one after the other.  Blue, red, green, gray, etc.  With Breezy, resuming from suspend brought up a wierd garbled screen.  In either case, a hard-reboot is necessary.  

I have to say this is the one thing holding me back from going 100% ubuntu... but I've still got my fingers crossed for the final release of Dapper.

---

### Post by m0nstr42 on 2006-07-06
[QUOTE=teasum]I have two problems: 1) The battery monitor now is sketchy at best, and tends to drop drastically to near zero, followed by a forced shutdown.  Before you say it's the battery, it's not--this doesn't happen in XP.  2) The suspend-to-ram problem is just wierd.  It appears to go down correctly, but when I try to boot back up, I get full-screen colors, alternating one after the other.  Blue, red, green, gray, etc.  With Breezy, resuming from suspend brought up a wierd garbled screen.  In either case, a hard-reboot is necessary. [/QUOTE]
I have basically the same problem with the battery monitor.  It gets to around 40% and then drops to, say, 5%.  That's not too unbearable for me, I just know I get ~1.5-2 hours of battery and plug it in when I need to.

As for the suspend problem - I have had the same problem previously, but followed this: [https://help.ubuntu.com/community/NvidiaLaptopBinaryDriverSuspend](https://help.ubuntu.com/community/NvidiaLaptopBinaryDriverSuspend) and have had good luck since.  I do suspend to memory which works pretty well (nice quick recovery... occaisionally have to ctrl-alt-backspace to recover X, but still better than shutting down and booting).  I haven't gotten the hibernate (to hard drive) to work yet - when I start back up it just boots normally.  Still quite happy that I got suspend to work.

---

