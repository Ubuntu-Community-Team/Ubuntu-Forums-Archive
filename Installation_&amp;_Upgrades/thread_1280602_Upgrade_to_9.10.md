---
title: "Upgrade to 9.10"
date: 2009-10-02
forum: Installation &amp; Upgrades
---

### Post by FreakTech on 2009-10-02
I am attempting to upgrade from 9.04 to 9.10 beta.  I have followed the instructions found here:  [http://www.ubuntu.com/testing/karmic/beta#Upgrading%20from%20Ubuntu%209.04](http://www.ubuntu.com/testing/karmic/beta#Upgrading%20from%20Ubuntu%209.04)
But I am receiving and error that Could not download release notes.  I have verified that I do internet connection.  Any ideas on where to go from here?

---

### Post by BraedenNaylor on 2009-10-02
I have seen a few people have this and I am now suspicious that it is because of the heavy load on the server right now. I can't even do updates right now. It just locks up. You may want to wait until all the people grab the beta. I may be wrong though ;)

- Braeden

---

### Post by FreakTech on 2009-10-02
Yeah, I figured something like that.  Thanks for the confirmation.

---

### Post by FreakTech on 2009-10-02
Since the update servers are being pounded right now I have downloaded the ISO.  Is it possible to do an upgrade from the disk?

---

### Post by michaeld003 on 2009-10-02
I am not sure if this will work since it is for upgrading from 8.10 to 9.04 but it is probably similar.  I would make sure you back everything up though before you attempt this.  Maybe wait for someone with more experience to give their 2 cents as well.

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

### Post by jatinps on 2009-10-02
I am having the same issue when trying to upgrade to 9.10 beta. I guess need to wait a while and try again.

---

