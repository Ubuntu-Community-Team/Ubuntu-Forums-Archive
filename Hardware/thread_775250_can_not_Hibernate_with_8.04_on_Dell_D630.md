---
title: "can not Hibernate with 8.04 on Dell D630"
date: 2008-04-29
forum: Hardware
---

### Post by lulihummel on 2008-04-29
my laptop is Dell D630 with 2G RAM. with 7.10, it can hibernate normally. now , i update to 8.04, Hibernate does not work correctly. after i pressed Hibernate button, the screen turned t black, then display the following content:
   Code: Bad EIP value.
   EIP: [] .......
   ..................
   PM:suspend-to-disk mode set to 'platform'
   swsusp: Marking nosave pages:....
   swsusp: Basic memory bitmaps creates
   Syncing filesystems ... done.
   Freezing user space processes.....
   Freezing remaining freezable tasks....
   Shrinking memory ... done (0 pages freed)
   Freed 0 kbytes in 0.05 seconds (0.00 MB/s)
   Suspending console(s)
   i have spent a whole day on it, but it still does not work. what shou I do? thanks

---

### Post by simon350 on 2008-04-30
Hi,
I'm having the same problem on a Dell Latitude D600. It was working with ubuntu 7, too. I have no idea what to do. What does "Bad EIP value" mean? Thanks for any help!

---

### Post by simon350 on 2008-05-08
Hi,
after an ubuntu-update suspend and hibernate  now work fine

---

### Post by lulihummel on 2008-06-21
> **simon350 said:**
> Hi,
after an ubuntu-update suspend and hibernate  now work fine
I disabled Wi-Fi in BIOS of Dell D630, it worked now.while I do not think it is the best solution.

---

### Post by lulihummel on 2008-06-23
i updated my 8.04 with hardy-update,it dost not still work.:(

---

### Post by nogasbiker on 2008-07-25
> **simon350 said:**
> Hi,
after an ubuntu-update suspend and hibernate  now work fine

An update does not fix it for me on a D610.  Just to make sure my system wasn't hacky, I even wiped the hard disk, freshly installed Hardy, then did an update.  No go, hibernate failes on "suspending console(s)".

-- SOLUTION --
What does work is getting the firmware for your broadcom based wifi (which D610, D620, and D630 all apparently have).  The hibernate is failing on the wifi, which seems odd to me since I am using it with hardwired ethernet only.  If I don't have the wifi drivers, don't let me use wifi, but don't hang up the hibernate...

Anyhoo, to get the wifi drivers, goto
             system->administration->hardwaredrivers

For Dell D6[1-3]0, you should see "Broadcom B43 wireless driver".  It is probably unchecked on "Enabled.".  Check the box, it will ask if you want to pull the proprietary firmware.  Confirm it.  It will then get and install software.  After a reboot, and all should be well.  The hibernate should work.

---

### Post by lulihummel on 2008-07-26
> **nogasbiker said:**
> An update does not fix it for me on a D610.  Just to make sure my system wasn't hacky, I even wiped the hard disk, freshly installed Hardy, then did an update.  No go, hibernate failes on "suspending console(s)".

-- SOLUTION --
What does work is getting the firmware for your broadcom based wifi (which D610, D620, and D630 all apparently have).  The hibernate is failing on the wifi, which seems odd to me since I am using it with hardwired ethernet only.  If I don't have the wifi drivers, don't let me use wifi, but don't hang up the hibernate...

Anyhoo, to get the wifi drivers, goto
             system->administration->hardwaredrivers

For Dell D6[1-3]0, you should see "Broadcom B43 wireless driver".  It is probably unchecked on "Enabled.".  Check the box, it will ask if you want to pull the proprietary firmware.  Confirm it.  It will then get and install software.  After a reboot, and all should be well.  The hibernate should work.
thank u, i just do what u said , it works well

---

### Post by nogasbiker on 2008-09-01
Unfortunately, I updated Hardy a week ago, and now hibernate is broken again.

The Dell seems to hibernate fine.  I see the disk working as it is writing the image to swap.  But on resume, it just does a reboot...

:confused:

---

### Post by motin on 2008-10-07
Has anyone reported this in launchpad? This definitely looks like a bug...
Anybody experienced this and tried Intrepid and see if it is the same there?

---

### Post by igotnoluck on 2008-10-07
On my LG i had the same problem with Hibernate / standby. the way that i fixed it, is by removing the compiz.
the only problem i have now is that i have no sound after hibernate / standby.

---

