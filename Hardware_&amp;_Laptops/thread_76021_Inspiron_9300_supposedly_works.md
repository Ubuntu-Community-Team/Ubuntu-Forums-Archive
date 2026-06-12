---
title: "Inspiron 9300 supposedly works?"
date: 2005-10-14
forum: Hardware &amp; Laptops
---

### Post by Stealth on 2005-10-14
I have Kubuntu & Ubuntu installed on my Inspiron 9300. According to the wiki, this laptop is supported/known to work by Canonical guys. They say it works with suspend and hibernate. For some odd reason, hibernation doesn't work properly from KDE (using KLaptop) It'll hibernate down, but when trying to recover it has a blank screen. Before installing my NVIDIA drivers it would hang on some message about needing to unload blocks or something. However, using Gnome-power-manager hibernation works, problem is that the screen recovers with lines all across the screen. I'm guessing hibernation is causing some conflicts with my drivers NVIDIA drivers. :( Another thing is suspend still doesn't work me, just like in Hoary. Both hang at a black screen when trying to get back to my desktop after loading up. Any ideas why?

---

### Post by bryan986 on 2005-10-15
Suspend does not work with my inspiron 9300 / nvidia 6800, when I try to resume I just get a black screen...

---

### Post by Stealth on 2005-10-16
Exactly, hence why I'm wondering how the guy who put this in the wiki got it working...

---

### Post by mlord on 2005-10-18
I have Kubuntu 5.04 Hoary working perfectly on my i9300.

But with Breezy, there are issues.  We actually have two i9300 machines here, one 2GHz, the other 1.84GHz, otherwise "identical" (heh heh..).

The slower machine runs Breezy without a hitch, suspend/resume to ram/disk all works nicely.  But the faster machine (my own, as described at [http://rtr.ca/dell_i9300/](http://rtr.ca/dell_i9300/)) cannot suspend/resume to RAM with Breezy.  Hibernate (aka. suspend-to-disk) is fine.

Go figure.

---

### Post by Stealth on 2005-10-19
Do you have the GeforceGo 6800 in it w/ NVIDIA drivers installed in the other? :???: I see you have an X300 on that link...that must be it (on my hibernation problem), cuz I got everthing pretty much the same, cept some lower RAM and CPU ;)

---

### Post by bryan986 on 2005-10-19
.

---

### Post by Stealth on 2005-10-20
I tried the scripts on your site, but its still not working for me :(

---

### Post by marcj on 2005-10-20
Weirdly enough (?) I have the same issue as Stealth (Standby mode -> black screen, Hibernate gives some feedback).

My 9300, like mlord, but the 1.87 GHz processor and only 1 GB of memory (my DVD-RW seems to be different version, NEC ND6650A)

My config:
Ubuntu 5.04, kernel 2.6.13.4 patched with patches described at  [http://rtr.ca/dell_i9300](http://rtr.ca/dell_i9300), latest ATI driver (not the generic Ubuntu one).
Latest ipw220 driver & firmware.


Rgds,
Marc

---

### Post by HYoungren on 2005-11-16
Based largely on the Linux Laptops report of a working suspend/hibernate on the Dell 9300 (MLord), I recently bought a 9300 (2Ghz, 2Gb, Nvidia6800).  My results with Breezy are quite different than MLord's, even when I use his informational writeup, suspend script and mods.  I do not get working suspend/resume with Ubuntu Breezy, the machine hangs in a variety of ways, mostly with a dark screen.  I have tried the items in the MLord posts both with the nv X driver and the nvidia (accelerated) driver.   I am now on the second install (this time I installed Kubuntu first, then loaded the Gnome Ubuntu stuff).  I enabled the ACPI options in Kontrol, I enabled the /etc/defaults/acpi options for suspend/resume.  I get no resume from suspend to ram or resume from hibernation (with either the 386 or 686 kernels).  All the remaining issues with the machine appear to work with Ubuntu (networking, wireless, etc).

Are there alternative scripts that people have used on this machine to get suspend/resume to work?   Is something missing here?  Could the dark screen on resume be an issue with the video that can be addressed with vbetool (i.e. using post, vbemode, vgamode, etc)?

At this point I am getting concerned that suspend will not work with Breezy and I am considering trying an FC4 install to see what changes....

thanks,
Hal Y.

---

### Post by drosky on 2006-02-06
There is now a bug filed on this issue:

[https://launchpad.net/distros/ubuntu/+bug/30124](https://launchpad.net/distros/ubuntu/+bug/30124)

People having issues with hangs during resume may want
to look over the posts in the bug and add anything that may
be of value.  I'm having the same problem on an Inspiron
9400 with a Geforce go 7800.  SUSE 10.0 hibernates and
resumes fine, so hopefully it's a solvable problem ;)
Dave

---

### Post by echavet on 2006-02-16
Hi,
I have a 9300 with ATI. And ACPI hibernate to RAM or to disk does not work.
The screen cannot be restaured apparently. The System craches when trying to wake it up.
Eric

---

### Post by Vorian on 2006-02-16
[QUOTE=bryan986].[/QUOTE]

?

---

### Post by fh2level on 2006-02-16
Im trying to install on my Inspiron 9300 I get to the boot screen where it tells me to type 'install' and hit enter. I do, you can see it load a whole bunch of stuff on the screen then it goes blank and a second later you can here the cd drive stop turning and then im left sitting at a blank screen and nothing ever happens after that. Please help :(

---

### Post by Vorian on 2006-03-01
you dont have to type anything, just hit enter.

---

### Post by cshen12 on 2006-10-06
[This worked for me]("http://www.oreillynet.com/onlamp/blog/2006/04/suspend_to_disk_is_working_in.html").  I thought it was the Nvidia drivers, too but it turned out to be the wireless adapter.

---

### Post by randomnumber on 2006-10-25
my 9300 with geforcego 6800 comes back but has green vertical lines thru the screen. Is that what anyone else gets.? This from hibernate.

---

