---
title: "Unsure how to upgrade to 9.04"
date: 2009-04-22
forum: Installation &amp; Upgrades
---

### Post by 5nak3 on 2009-04-22
Hi all,

I've searched the forums, but not really found what I wanted so am just posting my own thread to explain where I stand and what problem I am having.

With the 23rd right around the corner, I was thinking of upgrading to Jaunty (from Intrepid) however this is where I feel I am out of my depth.

When I upgraded to Intrepid a while back, I did so from a 100% working 8.04 and this caused me a few headaches (some which i cannot resolve). The main reason for these problems I have been informed was that instead of a fresh install I tried to upgrade the system. Since things were not going great I thought "nevermind" and cleared the hard drive and did a fresh install...

Currently in 8.10 fsck doesn't work properly on boot, so i've turned it off and run it from a live cd.

Also quite often the splash screen when loading distorts quite a bit, fracturing the bar, creating duplicate bars etc...

Also on occasion the actual startup loads everything, but wont load the GDM so I am forced to ctrl+alt+del twice to reset the system

The system also seems to alternate between direct rendering: yes and direct rendering: no, as and when it pleases....even though compiz is running all the time.

As you can imagine these little annoyances are, well, annoying, other than this the system seems to work well...

I'm lucky in that nothing of importance is stored on the PC, so i don't mind starting from scratch, my problem is that I do not want to mess with codec installs, and installing upgrading programs and setting up the themes etc the way I like.

I have read that if you have the /home partition on it's own separate from /root you should be able to upgrade and have everything (except the OS) the way you left it.

I ran fdisk -l and the output is as follows

```
Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00036f6d

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        9327    74919096   83  Linux
/dev/sda2            9328        9729     3229065    5  Extended
/dev/sda5            9328        9729     3229033+  82  Linux swap / Solaris

```

Now I don't remember setting up different partitions when I did the fresh install of intrepid. I do remember I allowed the installer to use the whole disk, as I was not comfortable creating a manual partition (i think this was a mistake), so I'm not sure if the above actually means my /home partition is separate or not (I also wasn't sure of a command to help me determine the home partition to see if it was separate)

My question basically boils down to two parts:

1) To upgrade from intrepid to jaunty should I risk the upgrade manager or do a full install from scratch, and if I have to do a full install can someone tell me from the information above whether my /home is safe, or if you need another code output please let me know. 

2) If you recommend a clean install, is there no way I can create a new /home partition to avoid all the time consuming program downloads and installs.

I can understand that sticking to intrepid might be best, but honestly I am thinking if that is the case, I might just start fresh and go back to hardy. It is supported for longer and seemed to work much better than intrepid.

I'm going to burn a live cd anyways and test jaunty, see if anything does strike me as a worthwhile upgrade. But I want some opinions on what you guys think is best given my situation.

For reference:

I'm running a 3.2GHz P4

2gb ram

VGA compatible controller: ATI Technologies Inc RS300M AGP [Radeon Mobility 9100IGP] (lspci)

---

### Post by tgra953 on 2009-04-22
To upgrade from Ubuntu 8.10 on a desktop system, press Alt+F2 and type in "update-manager -d" (without the quotes) into the command box. Update Manager should open up and tell you: New distribution release '9.04' is available. Click Upgrade and follow the on-screen instructions.

To upgrade from Ubuntu 8.10 on a server system: install the update-manager-core package if it is not already installed; edit /etc/update-manager/release-upgrades and set Prompt=normal; launch the upgrade tool with the command sudo do-release-upgrade; and follow the on-screen instructions.

---

### Post by 5nak3 on 2009-04-22
Hi there, 

Thanks for the reply, I should have made it clear in my post that I already knew that (my bad, sorry). My main concern is the process of running the "update-manager -d" this keeps the system files as they are and just upgrades the necessary components, but from what I've been told this is slightly less reliable than a clean install.

And if this is in fact true, is there anyway to implement the upgrade as a clean install while keeping the system files the same (as per the update-manager -d command).

---

