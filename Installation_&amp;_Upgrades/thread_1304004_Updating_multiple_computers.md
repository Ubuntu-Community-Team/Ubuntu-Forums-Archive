---
title: "Updating multiple computers"
date: 2009-10-28
forum: Installation &amp; Upgrades
---

### Post by Stolea on 2009-10-28
I have 3 computers running Version 9.04 on a network.
Is there a way to update all 3 computers off a CD rather than 3 individual updates via the update manager?
I am sure there is, but I don't seem to be able to find anything on the subject:confused:

---

### Post by Stolea on 2009-10-29
I can't believe that I am the only one pondering this problem. Anyone, Please

---

### Post by Axos on 2009-10-29
I've never done this myself but here are the instructions I found using Google. These are for the 8.10 to 9.04 upgrade but they are probably the same for 9.04 to 9.10 (but I don't know that for a fact so you may want to wait until they've updated this page for 9.10).

[http://www.ubuntu.com/getubuntu/upgrading#Upgrading%20Using%20the%20Alternate%20CD/DVD](http://www.ubuntu.com/getubuntu/upgrading#Upgrading%20Using%20the%20Alternate%20CD/DVD)

---

### Post by Stolea on 2009-10-29
Thanks, will have a look at it. I am amazed that this is not part of the update arsenal. Surely there are lots of people in the same position.

---

### Post by Stolea on 2009-10-29
> **Axos said:**
> I've never done this myself but here are the instructions I found using Google. These are for the 8.10 to 9.04 upgrade but they are probably the same for 9.04 to 9.10 (but I don't know that for a fact so you may want to wait until they've updated this page for 9.10).

[http://www.ubuntu.com/getubuntu/upgrading#Upgrading%20Using%20the%20Alternate%20CD/DVD](http://www.ubuntu.com/getubuntu/upgrading#Upgrading%20Using%20the%20Alternate%20CD/DVD)

It would appear that this is the way to go. Attached is the relevant section of the above link:

> Upgrading Using the Alternate CD/DVD

Use this method if the system being upgraded is not connected to the Internet.

   1.

      Download the alternate installation CD
   2.

      Burn the ISO to a CD and insert it into the CD-ROM drive of the computer to be upgraded.
          *

            If the ISO file is on the computer to be upgraded, you could avoid wasting a CD by mounting the ISO as a drive with a command like:

            sudo mount -o loop ~/Desktop/ubuntu-9.04-alternate-i386.iso /media/cdrom0

   3. A dialog will be displayed offering you the opportunity to upgrade using that CD.
   4. Follow the on-screen instructions.

If the upgrade dialog is not displayed for any reason, you may also run the following command using Alt+F2:

gksu "sh /cdrom/cdromupgrade"

Or in Kubuntu run the following command using Alt+F2:

kdesudo "sh /cdrom/cdromupgrade"

---

### Post by Stolea on 2009-10-30
Updated the system with the method described.
I now have a system that does not recognize ANY sound card, onboard or Audigy2.
ATI display driver won't activate, just keeps going back to the same screen.
The "Sound" settings in "Preferences" is not there and the "Default Soundcard" in Preferences does nothing.
Any ideas how to fix this, or is this a complete reinstall?

---

