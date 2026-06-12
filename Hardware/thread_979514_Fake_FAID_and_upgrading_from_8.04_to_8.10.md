---
title: "Fake FAID and upgrading from 8.04 to 8.10"
date: 2008-11-12
forum: Hardware
---

### Post by gabylastar on 2008-11-12
Hello,

I'm the owner of a Fujitsu-Siemens Amilo Xi 1554 and I installed Ubuntu 8.04 LTS on it, after 3 days of fighting with the RAID recognition (I have a fakeraid), and I have a dual boot with Windows XP.

Of course I was so lucky and with my laptop, the alternate CD did not work, neither did the tutorials we can find on this forums. I had to find the way by myself with dmraid and various things and that was not really the best setup experience an OS can offer. Since that, I forgot how did I do precisely.

Also my custom Grub menu.lst is overwritten after each kernel upgrade, prohibiting me to boot under my Windows partition. I had to manually edit the menu.lst after each kernel update.

The question : I would like to do a network upgrade to Ubuntu 8.10, but I really fear that on the next reboot my fakeraid is not recognized, and I don't want to loose anything, and last but not least : I do not want to spend 3 days to make it work. Does anybody already successfully upgraded from 8.04 to 8.10 with a fakeraid and without having to type some nightmarish command line ? Is it safe ?

---

### Post by cariboo on 2008-11-12
I did a clean install of Intrepid on my server with a raid 1 array using fakeraid. I have an ide drive for / and /home but the fake raid as recognized right away, I just had to set a mount point in /etc/fstab. Not exactly the same as your situation, but there doesn't seem to be any change between Hardy and Intrepid as far as dmraid is conerned.

Jim

---

### Post by gabylastar on 2008-11-13
There is massive differences between your situation and mine :)
- I want to upgrade, not reinstall everything
- My RAID is built with 2 SATA II disks

That's exactly what I said. For me, the normal way to install it didn't work, the RAID wasn't recognized as easily. Basically I had to install from the normal CD (the alternate CD would not work for me), just before or after choosing the keyboard layouts, to switch to the console and manually install the network in order to have internet, install dmraid & co, then back to the graphical installer, and right before the end I had to install the network and dmraid on the copied files manually, and manually install Grub. I must have forgotten something.

---

### Post by gabylastar on 2008-12-26
A little up after more than one month of no-answers at all. Does someone know the answer to my question ?

Merry Christmas by the way.

---

