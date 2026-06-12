---
title: "Okay, how do I go about installing off a CD?"
date: 2009-01-08
forum: Installation &amp; Upgrades
---

### Post by KingAlanI on 2009-01-08
From what I've see of a Wubi-based install on another machine, I think I'm interested in installing Ubuntu on my other PC.

A full install on the 2nd computer is what I have in mind.

*Anything done wrong so far?*
I go fetch the ISO. (Since the target computer has a Pentium 4, I get the Ubuntu 8.10 i386 ISO) BitTorrented it, not that that should make a huge difference...
I go burn the ISO. (Yes, I made sure to do "Burn Image", rather than making a data disk)
I restart with the CD in the drive.
I get an Ubuntu screen.

Now I don't know where to go. I select the full install menu option; but it isn't clear what I do here. Not getting clear messages on whether the install's started, what I need to do, etc, or if it froze up.

I ran the computer through the disc check and memtest86, both of which it passed.

The target computer has XP Pro and 256 MB RAM. (it's the one I'm using right now to post this)

I can use the 2nd computer for help during the install itself.

---

### Post by KingAlanI on 2009-01-08
Obviously, this is an NTFS drive.
Do I need to partition it before I even reboot with the Ubuntu CD in?

It's 80 GB, with ~25 GB currently free.

Also, how can I set things up so that I can access my Windows-partition files from inside Linux? (On the previous computer that I Wubi-ed, I can find the Windows-partition files in /host.

On this machine, I connect to the Internet through a wired LAN (Ethernet to router, router to DSL modem, DSL modem to Internet)

---

### Post by Carl Hamlin on 2009-01-08
> **KingAlanI said:**
> 
Now I don't know where to go. I select the full install menu option; but it isn't clear what I do here. Not getting clear messages on whether the install's started, what I need to do, etc, or if it froze up.

-----BEGIN PGP SIGNED MESSAGE-----
Hash: RIPEMD160

What happens after you start the installation from the menu?

-----BEGIN PGP SIGNATURE-----
Version: GnuPG v1.4.9 (GNU/Linux)

iEYEAREDAAYFAklllsMACgkQyLm4ydrABve/zwCgvxkoausNzgK3zwoY2LtY9Isn
gbcAnR/pc1MgephGx/FggydsvcPH00zA
=se89
-----END PGP SIGNATURE-----

---

### Post by KingAlanI on 2009-01-08
I'll try again this weekend, and take notes.
However, I recall the following happening during various attempts:

* A graphic background with nothing on it [looked kinda like a brown skeleton to me]

* I got to a page that suggested I type "sudo man_root", which I did. It fed me the man page, but I didn't see how to exit of of the man page.

* Blank screens

I have not seen any DOS or BIOS interfaces pop up; this is apparently all from Ubuntu's installer.

Either the system froze up [wasn't doing anything] or it appeared to not be doing anything.

---

### Post by louieb on 2009-01-08
> **KingAlanI said:**
> The target computer has XP Pro and 256 MB RAM. (it's the one I'm using right now to post this)

The minimum needed for a live CD install is 384MB. Once installed it will run with 256MB.  Try the alternate install CD (text based installer). Not any harder to use, same questions just a text based interface.   

Its is an easier install if you partition 1st. Use the Gparted live CD or run Gparted from the [SystemRescueCd]("http://www.sysresccd.org/Main_Page"). Create a couple of partitions 1 of say 7GB  for the Ubuntu install and 2 a swap partition of 1/4GB to 1/2GB.

---

### Post by ugm6hr on 2009-01-08
> **louieb said:**
> The minimum needed for a live CD install is 384MB. Once installed it will run with 256MB.  Try the alternate install CD (text based installer). Not any harder to use, same questions just a text based interface.   

Exactly.

If you want an Ubuntu-based option, I'd suggest using the Xubuntu Alternate CD instead of Ubuntu.  It will be more usable with 256MB RAM.

If you have already partitioned (i.e. created a swap partition), you *could* use the Xubuntu Live CD, but that just complicates things.  I'd recommend a GParted Live CD too.

I've done an install on a similar machine with Xubuntu 8.04.1 - works fine.

---

### Post by KingAlanI on 2009-01-08
I'm thinking about upgrading the RAM to 512MB or 1GB or somethign anyway...

I see the SystemRescueCD.
I want to be careful with that, especially since I want to keep my existing Windows information. (Yes, my documents in userland have been backed up)

How do I go about using that CD?

Download it, burn it, then run the Ubuntu installer?
(I will download & burn the alternate-installer Ubuntu CD first.)

What do I need to run off of that systme CD and how?

Installing OSes is a weekend project, not an evening project. :P
I just want get all my penguins in a row now. :)

---

### Post by ugm6hr on 2009-01-08
If you upgrade to 512MB, you could just use the Ubuntu LiveCD to do both the repartioning, as well as the installation.

Otherwise, use any lightweight LiveCD with GParted ([Parted Magic]("http://partedmagic.com/") or [System Rescue CD]("http://www.sysresccd.org/Main_Page") are good options), and follow the partitioning advice here: [http://www.psychocats.net/ubuntu/partitioning](http://www.psychocats.net/ubuntu/partitioning)

Once the partitions are created, you can use any (X)ubuntu CD to install as RAM allows.

---

### Post by KingAlanI on 2009-01-09
Downloading a couple ISOs right now: Ubuntu 8.10 (alternate installer) and the System Rescue CD ISO.

---

