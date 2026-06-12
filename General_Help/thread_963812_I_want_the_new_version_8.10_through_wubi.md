---
title: "I want the new version 8.10 through wubi"
date: 2008-10-30
forum: General Help
---

### Post by ontherooftop on 2008-10-30
I know this just got released today , but is there a way to 
get wubi to download the stable 8.10 ubuntu version, I have 
used ubuntu before but want it with both xp.

---

### Post by brandon88tube on 2008-10-30
Yes, go to this link [http://sourceforge.net/project/showfiles.php?group_id=198355](http://sourceforge.net/project/showfiles.php?group_id=198355) and download the 8.10 version of Wubi. If you already have 8.04 installed then you can just upgrade under Ubuntu by checking for updates.

---

### Post by mlentink on 2008-10-30
[http://releases.ubuntu.com/8.10/wubi.exe](http://releases.ubuntu.com/8.10/wubi.exe)

---

### Post by ontherooftop on 2008-10-30
Thanks.

---

### Post by ago on 2008-10-30
website updated, it is now pointing to wubi-8.10.exe

---

### Post by grinias on 2008-10-31
> **brandon88tube said:**
> Yes, go to this link [http://sourceforge.net/project/showfiles.php?group_id=198355](http://sourceforge.net/project/showfiles.php?group_id=198355) and download the 8.10 version of Wubi. If you already have 8.04 installed then you can just upgrade under Ubuntu by checking for updates.

Upgrading under Ubuntu is this the proper way to update wubi from 8.04. to 8.10? Or you have to update it in Windows?

---

### Post by brandon88tube on 2008-10-31
Updating through Ubuntu should be the way to go unless you want a clean/fresh install of 8.10, but then you lose anything you customized etc. in 8.04

---

### Post by Virtua-Touch on 2008-10-31
Is all my customization gonna be the same when I upgrade?

---

### Post by axelsvag on 2008-11-01
I had the network manager 0.7 configured on my wubi 8.04 installation, after upgrade to 8.10 all my network connections broke. (cable, wireless, wireless broadband etc). so I had to do a fresh wubi 8.10 install.

---

### Post by francis_ba on 2008-11-01
[IMG]http://tinyurl.com/rerunner/[/IMG]
love ubuntu!!!!

---

### Post by rhcm123 on 2008-11-01
> **Virtua-Touch said:**
> Is all my customization gonna be the same when I upgrade?

If you upgrade through ubuntu, then yes, assuming you keep all the old .conf files when it asks you during upgade.
If you do it through windows, then no.

I would probably do it through ubuntu, but be warned: somtimes wubi-based ubuntu handles upgrades very poorly. It destroyed my ubuntu system. be sure to backup files before upgrade.

---

### Post by Virtua-Touch on 2008-11-01
Okay.

---

### Post by catfished on 2008-11-01
> **rhcm123 said:**
> If you upgrade through ubuntu, then yes, assuming you keep all the old .conf files when it asks you during upgade.
If you do it through windows, then no.

I would probably do it through ubuntu, but be warned: somtimes wubi-based ubuntu handles upgrades very poorly. It destroyed my ubuntu system. be sure to backup files before upgrade.

So from what I'm reading, I probably should wait a few weeks to upgrade my Wubi 8.04 to 8.10 thru Ubuntu. Hopefully there will be a few more users that will share their experiences by then, good or bad.:popcorn:

---

### Post by Virtua-Touch on 2008-11-02
I'm gonna take the plunge probably tomorrow, so I'll let you know how it goes.

---

### Post by catfished on 2008-11-02
> **Virtua-Touch said:**
> I'm gonna take the plunge probably tomorrow, so I'll let you know how it goes.

OK thanks Virtua-Touch, I'll check back here tomorrow to see how it goes. Good luck to you.

---

### Post by catfished on 2008-11-05
> **Virtua-Touch said:**
> I'm gonna take the plunge probably tomorrow, so I'll let you know how it goes.

So how did it go?

---

### Post by PGHammer on 2008-11-06
Okay...the dual-boot is now a triple.

Windows Vista, Windows 7 (from the PDC) and now Ubuntu 8.10 (via Wubi).

The problem is that I had to disable the onboard Intel PRO1000CT Ethernet to get the Ubuntu install to run (known quirk with the current kernel and most e1000-driver-based Intel gigabit solutions, which is just about all Intel copper gigabit solutions, so it's just just Ubuntu that got bit by this).  I have *not* tried re-enabling the onboard gigabit to see if the quirk has been fixed (yet).

---

### Post by catfished on 2008-11-12
> **Virtua-Touch said:**
> I'm gonna take the plunge probably tomorrow, so I'll let you know how it goes.

We're still waiting for your verdict.:popcorn: Since you haven't returned, I hope it's not bad news?

---

### Post by catfished on 2008-11-22
> **Virtua-Touch said:**
> I'm gonna take the plunge probably tomorrow, so I'll let you know how it goes.
I guess we'll never know????:confused: 
[B]I really wish I knew how safe it would be to upgrade to 8.10 via Wubi.
[/B]

---

### Post by bobc4012 on 2009-07-20
> **catfished said:**
> I guess we'll never know????:confused: 
[B]I really wish I knew how safe it would be to upgrade to 8.10 via Wubi.
[/B]

I tried to update a Wubi install via the update manager and it scrogged my Windows MBR. I had to repair the MBR and boot record to get Windows back. I have the Windows XP CD that came with my system. It is a MS CD, not some cobbled OEM CD. I was able to restore those records. If the "Virtua Touch" was not aware, he probably got quite upset, especially if he didn't know the MBR and MS boot records had to be fixed. So far, I have not found a way to go from one Ubuntu release to the next on a Wubi install, other than backing up all your relevant data, doing a screen capture of the desktop (in case you forget), finding a list of all installed applications, re-installing them, etc. The more you have installed, the bigger PITA it is to upgrade. The Ubuntu CD does not provide any help either. It also assumes a dedicated HD (or at least a partitioned HD.

---

