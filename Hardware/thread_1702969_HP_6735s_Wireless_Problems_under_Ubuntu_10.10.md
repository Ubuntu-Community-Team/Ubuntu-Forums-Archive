---
title: "HP 6735s Wireless Problems under Ubuntu 10.10"
date: 2011-03-08
forum: Hardware
---

### Post by danijelg on 2011-03-08
After spending literally five days searching for a solution to my problems with wireless under Ubuntu 10.10, and nearly giving up on Ubuntu all together, I have finally got it to work flawlessly.

The thing that worked for me was simply removing the Network Manager and installing Wicd Network Manager instead, all done through the Synaptic Package Manager.

Here is the detailed process:

1. Go to System > Administration > Synaptic Package Manager
2. Enter your password if asked
3. Search for Network Manager
4. Mark for removal
5. Apply
6. Search for Wicd
7. Mark for installation
8. Apply
9. Reboot

I hope this solves other people's problems too, as I've seen countless threads about the problem on this forum.

---

### Post by perro_ninja on 2011-04-25
Hi Danijelg

I have the same HP laptop and I am trying to follow your instructions,
In the step 6:
6. Search for Wicd

What's "wicd"? No packages were found for wicd in the synaptic manager  ...
Thank you in advance
Rod

---

### Post by danijelg on 2011-04-26
Wicd is a network manager - an alternative to the default Network manager. 

I am using Ubuntu 10.10 and Wicd is included in the repository. Perhaps you need to add the Wicd repository to the Ubuntu package manager if you are using a different Ubuntu version. You can go to the official Wicd website for instructions: [http://wicd.sourceforge.net/download.php]("http://wicd.sourceforge.net/download.php")

Good luck!

---

