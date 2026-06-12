---
title: "Grub error 2 solution"
date: 2008-09-16
forum: General Help
---

### Post by Piraja on 2008-09-16
I found a couple of archived, unsolved threads with reference to Grub "Error 2" which often prevents booting from an external drive installation (either HDD or pendrive). Now I would like to share my solution which I originally adopted, *mutatis mutandis*, from DaBruGo's thread titled "[SUCCESS - Breezy loaded on external USB drive!]("http://ubuntuforums.org/showthread.php?t=80811")" (started in Oct. 2005); see also the thread "[Installing Hardy on external HDD]("http://ubuntuforums.org/showthread.php?t=885862")", with Logos34's valuable hints. 

**NB**: There is no need to follow DaBruGo's tutorial step by step in installing e.g. Hardy on an external USB device. You can do a lot, and do it a lot easier, with a recent LiveCD. Now let us presume you have already installed Ubuntu on a USB device and got stuck with Grub Error 2, trying to boot the new system.

The couple of simple steps below worked for me in installing Hardy on a partition of a 500 GB external HDD and also Fluxbuntu on a 4 GB pendrive. To be sure, you shall have to mount the external device partition from a LiveCD or another Linux installation in order to edit the files as shown below.

At least in older PCs, the bootloader must be given sufficient time to boot from USB (let us presume you have already enabled USB booting in your BIOS settings and changed the boot order so that the USB option comes before the hard drive). You can try the following: 

(1) Edit /etc/initramfs-tools/modules (in some earlier Ubuntu versions the folder was /etc/mkinitramfs) &#8212; you can replace "gedit" below with your favorite editor &#8212; e.g. by typing or pasting the following command in the terminal:

```
sudo gedit /etc/initramfs-tools/modules

```

These are the lines you should add below the last line of text in the modules file:

```
ehci-hcd
usb-storage
scsi_mod
sd_mod
```

Save the changes you just made.

(2) Next, edit the file initramfs.conf in the same folder:

```
sudo gedit /etc/initramfs-tools/initramfs.conf
```

As DaBruGo says, "At the very top of this file, add this line which tells UBUNTU to pause for 12 seconds before starting up":

```
WAIT=12
```

Save the changes. Still in the terminal, run the following command: 

```
sudo update-initramfs.conf
```

Now you can close the open windows and try booting from your external drive.

These couple of steps worked for me. For some more information, you might want to consult the mentioned tutorial, but the commands above were sufficient in my case to "teach" an older system to boot from an external USB drive (either HDD or flash), provided that the BIOS allows that. I have the 500 GB HDD plugged onto a Compaq Evo D510 with 512 MB RAM, and I have booted Fluxbuntu on the 4 GB pendrive with an Acer Travelmate 2354 (256 MB, running Intrepid but a bit slowly) and a brand new Dell Optiplex 755 (which didn't need the 12 sec delay or any other tweaks).

Be patient, though: possibly you must wait more than twelve seconds (I'd say 20-30 secs). I haven't tried to add a shorter delay to the initramfs.conf file (instead of WAIT=12), but some smaller value might work. Don't be afraid of the dark screen before and after the Grub menu screen. Just wait a while and the system should boot without problems.

---

