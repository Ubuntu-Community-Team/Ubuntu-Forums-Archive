---
title: "Wubi 8.10 install / partition screen blank"
date: 2008-12-14
forum: Installation &amp; Upgrades
---

### Post by jhall_uk on 2008-12-14
Hi there,

I've installed Ubuntu 8.10 using the Wubi installer inside Win XP Pro on an HP nc6120 laptop (2GB RAM) which has a hard drive partitioned into 2 parts (approx 30gb c: and 50gb d:). Due to lack of disk space in c: I installed it on my d: partition of my hard drive (which had 30gb free).

All went ok (I allocated 10gb to ubuntu during the install process) and the reboot took me into Ubuntu where the install wizard kicked in.

On the partition screen on step 4 it shows no partitions and if I click 'forward' a message appears stating "no root file system is defined. please correct this from the partitioning menu"

I have no choice but the quit the installer.

I'm not sure what to do next - Ubuntu seems to work normally if I quit - the wireless connection configures ok, and I can surf the web etc. Open Office launches ok.

Do I even need to complete the rest of the install steps? -I seem to be logged in as root by default...

Cheers,
John

---

### Post by jhall_uk on 2008-12-15
I want to add a little more info to this:

It appears that as the Installer didn't complete (see the partioning issue mentioned above), when I boot ubuntu it logs me in as the 'Live Session User'.

Rebooting and hitting esc to get the menu shows me running in Installer Mode.

If I create a new account after exiting the installer, the user does not survive a reboot. Neither do any package updates I've applied (e.g., sox).

It seems my install is stuck in read-only mode!

How do I progress? 

Cheers,
John

---

### Post by greenart on 2009-03-03
I am getting the same exact problem except I am installing 8.10 on a Dell Mini 9 to my hard-drive from a live USB session user. My only option is to quit too - I dont see any partitions to prepare and I also get No root file system is defined.... this is also step 4 on the installation process. I dont want to keep running Ubuntu from "live" mode but from "harddrive" mode. I think it has to do with mounting a device.... if you get an answer, please forward to me and if I find something - I will forward to you....;)

---

