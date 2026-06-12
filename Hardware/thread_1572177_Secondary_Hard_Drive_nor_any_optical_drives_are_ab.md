---
title: "Secondary Hard Drive nor any optical drives are able to be mounted."
date: 2010-09-10
forum: Hardware
---

### Post by fallendown on 2010-09-10
I've had Ubuntu 10.04 installed for about a month now and all of a sudden, within the last 2 hours, I can no longer open any of my optical drives or access my secondary 350GB Hard Drive. I've checked system->Administration->User's&Groups and made sure I was the Administrator and had rights to everything. Though I had to do it through the terminal with:

```

sudo users-admin

```Also when I try to select restart it just dumps me to the login screen without restarting.

My config is 

Intel 2.4GHZ Quad Core
3GB Ram
Nvidia Geforce 8500GT
2X350GB HDD non-raid
1X CD/DVD-rw
1XHDDVD-ROM

Like I said, Ubuntu has ran flawlessly until now.......I did install desktop theming apps Emerald and Compiz Fusion Icon just before it happened.

---

### Post by coffeecat on 2010-09-10
When you say you can't access your secondary hard drive, do you mean that it doesn't appear in the Places menu any more, or that it does and that it won't mount when you click on it?

First thing to do is to go into your BIOS and check that the BIOS can still see the second drive and the optical drive.

---

### Post by fallendown on 2010-09-10
Yes everything show's in the Bios, yes you can see them in Place's......no I cannot see the secondary drive in System Monitor, when I click on it in Places it says: (note the drive name is New_Volume)


Unable to mount New_Volume
Not Authorized

Like I said this morning everything worked fine.

---

### Post by TimEnid on 2010-09-10
is the drive formatted? do you have anything on it? go to system>admin>disk utility, and see if the drive appears there. it may need to be formatted.

---

### Post by axyelp on 2010-09-11
i'm no expert but here's what i'd have done, check #fdisk -l and /etc/fstab

post the output of
**$sudo fdisk -l**

and of

**$ls -al /dev/cdr**

and contents of

/etc/fstab

---

### Post by coffeecat on 2010-09-11
> **fallendown said:**
>  when I click on it in Places it says: (note the drive name is New_Volume)


Unable to mount New_Volume
Not Authorized

Clearly the system is still seeing the secondary drive (and presumably the optical drive) but this is a mounting problem which has just occurred.

> **fallendown said:**
> ILike I said, Ubuntu has ran flawlessly until now.......I did install desktop theming apps Emerald and Compiz Fusion Icon just before it happened.

Compiz can do strange things, but interfering with drive mounting would be a new one on me. If you've enabled Emerald with Fusion Icon, try going back to Metacity. If that doesn't help, try disabling compiz. At least then we'll see if that's the problem.

---

### Post by Timothy Taylor on 2010-09-20
I've just noticed this happening.

When I boot into Ubuntu, my other (NTFS) drives are visible / accessible in Places.
After some time, they become either not listed or not accessible. Restarting the system seems to solve the problem - until the drives disappear again.

I have never had this problem until recently.

---

