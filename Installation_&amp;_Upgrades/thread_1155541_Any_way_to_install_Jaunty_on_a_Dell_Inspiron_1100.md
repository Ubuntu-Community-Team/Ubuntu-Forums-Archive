---
title: "Any way to install Jaunty on a Dell Inspiron 1100?"
date: 2009-05-10
forum: Installation &amp; Upgrades
---

### Post by michaelzap on 2009-05-10
Having a heckuva time with this old Dell. It has a working Hardy installation with LVM full-disk encryption, but I'd really like to update it to Jaunty with ext4 and an encrypted home directory. I can't even get the alternate installer CD to work on it, however.

I've tried booting from a CD and bootable USB stick, but I can never get past the first CD menu. I can't choose anything from that menu, and the installer crashes hard shortly thereafter. Sometimes I'm told to press F4 for alternate methods, and sometimes it just freezes and any key causes a system beep, but usually I get a black screen with "invalid compressed format (err=2)".

I've already got the A32 BIOS and shared video memory is set to 8MB (so please don't post links to those steps).

Is there a new trick to get the Jaunty alternate CD to load on this beast, or am I condemned to dwell in Hardy purgatory forever?

---

### Post by logos34 on 2009-05-10
You can't upgrade directly from hardy to jaunty, even using the alternate cd.  Either do a fresh install, or do a online dist upgrade to 8.10 first, then to 9.04. (You can only skip releases when upgrading from one LTS to the next)...

Not sure what the deal is with the ubuntu cds

---

### Post by michaelzap on 2009-05-11
> **logos34 said:**
> You can't upgrade directly from hardy to jaunty, even using the alternate cd.
Sorry if I wasn't clear: I'm not trying to upgrade. I want to reformat and reinstall from scratch. But I can't get the installer to run on this laptop...

---

### Post by syg00 on 2009-05-11
The 1100 is getting a bit old.
I had quite a bit of work to get Intrepid working, but eventually did - that video kludge they did is always going to be a problem.
I'll try Jaunty later - this is a reminder to myself.

---

### Post by michaelzap on 2009-05-11
> **syg00 said:**
> The 1100 is getting a bit old.

Old and cranky, but I've got two of them and I really want to get Jaunty running on them.

---

### Post by syg00 on 2009-05-11
Didn't have a 32-bit alternateCD around, so decided to see if the liveCD would work.
It did, but with a blank desktop ... :( 
Switch to F1 session and back to F7 brought up the desktop. Hmmm.
Decided to install, thinking I'd get an option for partitioning and boot-loader. Wrong on the latter - it creamed the MBR (still). Restart needed the F1-F7 trick, but a later re-boot didn't.
Go figure.

---

### Post by michaelzap on 2009-06-05
*BUMP!*

I'm now having the exact same issue with a Dell Latitude c510. The alternate CD dies after clicking install with "invalid compressed format (err=2)". None of the options (acpi=off, etc.) seems to help.

This is a very old system, I know, but the 1100 is a bit newer and has the same gripe.

---

