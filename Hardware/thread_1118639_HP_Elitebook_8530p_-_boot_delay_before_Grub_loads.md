---
title: "HP Elitebook 8530p - boot delay before Grub loads"
date: 2009-04-07
forum: Hardware
---

### Post by psychlic on 2009-04-07
Hi all

I'm leaning towards a hardware issue on my laptop with this one, but before I do what HP want (yep; please reinstall Vista, Ubuntu is not supported).  If anyone has any pointers which would mean I don't have to downgrade, even temporarily, and risk my Ubuntu install in the process, I'd really appreciate it.

So, HP Elitebook 8530p.  Installed Intrepid amd64 in December 08 and all worked brilliantly until about 2 weeks ago.  Now, when I power on, the BIOS screen appears, then goes blank.  About a minute later Grub finally loads and from then on all is well.

Is there any possible reason that Grub would delay for that long before loading, or should I accept the inevitable and go with the HP recommendation?  Sounds like they won't do anything else until I reinstall Vista.

Thanks in advance for any advice.

---

### Post by mhgsys on 2009-04-07
Hey, 
First of all:
 If this is a harware issue, I don't understand how installing windows will help and I don't think you'll be helped in any way with doing that.

Anyway:
Have you tried to go in to bios and check if all settings are ok?
Like first boot device etc..

Seems to me bios seems to wait to boot from other devices first.

---

### Post by psychlic on 2009-04-07
> **mhgsys said:**
> Hey, 
First of all:
 If this is a harware issue, I don't understand how installing windows will help and I don't think you'll be helped in any way with doing that.

Anyway:
Have you tried to go in to bios and check if all settings are ok?
Like first boot device etc..

Seems to me bios seems to wait to boot from other devices first.

Hi - I couldn't agree with you more, but the more I tried to point that out to HP the more they said "Please install the supported OS as this is an OS issue".  Very frustrating.

I have checked the BIOS, the boot order was the first thing I looked at.  It was set to DVD first (and had been all along), but to prove the point I set it to HDD first.  No luck.  Tried updating the BIOS from F.04 to F.09, still nothing.  I also did the usual first line "battery out, hold the power button" stuff.

I guess I'd really just like a way to prove to HP that it isn't Ubuntu in such a way that even they accept it, but it's looking like they're not for turning.  Anyway, any ideas would be most welcome.

---

### Post by smitz999 on 2009-12-18
Hi [psychlic]("http://ubuntuforums.org/member.php?u=722431")

Did you manage to fix this issue?  I'm getting the exact same problem on my HP Elitebook 2530p.  I've tried updating BIOS, changing EVERY setting in BIOS, re-installing OS all to no avail.  Any help would be greatly appreciated

---

### Post by richiebrewer on 2010-11-03
Bump.

I am having this same issue on a 2530p.  Worked fine for months, then one day, this 30-45 second delay between POST and the first boot device.  Tried different revisions of the BIOS, different boot devices (USB, CD, other HDD, etc) and all the same result.  I am leaning towards hardware, but I need to be sure before taking it in.

Thanks in advance.

---

### Post by psychlic on 2010-11-03
To confirm; the issue I had was that POST would happen and then I'd have a blank screen for almost a minute before Grub would appear.  If that's the same as your issue (i.e. the delay is before Grub appears) then it sounds exactly the same as mine.  I ended up sending my 8530p back to HP (they arranged a courier collection as it was still under warranty) but only after I installed Vista to satisfy their process :mad:

After all the time wasting it turned out they had to replace the system board.  I had it back within a couple of days and all was well again.  Good luck!

---

### Post by hp2530p on 2011-12-19
> **psychlic said:**
> To confirm; the issue I had was that POST would happen and then I'd have a blank screen for almost a minute before Grub would appear.  If that's the same as your issue (i.e. the delay is before Grub appears) then it sounds exactly the same as mine.  I ended up sending my 8530p back to HP (they arranged a courier collection as it was still under warranty) but only after I installed Vista to satisfy their process :mad:

After all the time wasting it turned out they had to replace the system board.  I had it back within a couple of days and all was well again.  Good luck!

I know what it is!!! After many hours of struggling / searching / playing etc.

Short version: Plug the ethernet port into a network that has a DHCP server and then cold boot it. The delay is now gone. After that you can disconnect it from the network and reboot as much as you like without delay.

Long version: It's the Intel Management Engine, which is an extension of the BIOS. It allows 'out of band' management (or platform independent management of the corporate laptop, regardless of what operating system it's running on top)

I found it when I enabled something to do with verbosity in the bios (in the AMT section) and then rebooted the laptop. Then it displayed "Intel Management Engine, bla bla, ME is initialising..." for the duration of the delay.

Then I did a bit of reading on the Intel Management Engine and discovered that it stores it's own network configuration on it's own little chip - that's when the penny dropped. So it seems to want to have an IP stored before it will initialize without delay. Thanks HP for wasting my time, and for not having any information of any kind in your knowledge base!

---

### Post by webcrawler42 on 2012-04-13
Was this problem on every boot? or every once and a while?

---

