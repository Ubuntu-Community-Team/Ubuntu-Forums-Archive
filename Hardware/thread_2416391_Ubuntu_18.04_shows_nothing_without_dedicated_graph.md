---
title: "Ubuntu 18.04 shows nothing without dedicated graphics card"
date: 2019-04-09
forum: Hardware
---

### Post by thewrapper on 2019-04-09
Yesterday I turned on my computer to find out that my graphics card-a dedicated NVIDIA GeForce 8400 GS-broke. Right now I'm using the computer's built-in Intel HD Graphics 2000, but Ubuntu won't boot without the dedicated graphics. Actually it boots, but it shows nothing after it finishes: no login screen, no desktop, even no command-line interface (Ctrl+Alt+F3), so I can't do anything.

Can someone help me?
Thanks.

BIOSTAR Hi-Fi H61S3
Intel Core i3-2100
4GB of RAM
Intel HD Graphics 2000 + dedicated NVIDIA GeForce 8400 GS
Ubuntu 18.04.2 64-bit

---

### Post by oldfred on 2019-04-09
may be better to just use the Intel.

       [https://www.videocardbenchmark.net/compare/Intel-HD-2000-vs-GeForce-8400-GS/3264vs73](https://www.videocardbenchmark.net/compare/Intel-HD-2000-vs-GeForce-8400-GS/3264vs73) 
    
Intel passmark 213
Nvidia 8400 GS 113

Or Intel almost twice as fast as old nVidia card.

You may need to remove old nVidia drivers, or make sure UEFI/BIOS says to use Internal video not external.

---

### Post by thewrapper on 2019-04-09
Thanks for your answer, I think I'd better use the Intel instead. But, how do I remove the drivers? I can't open Software & Updates! However, is there any configuration file I can edit to remove them? If so, I just need to boot through the live USB and edit that file.

---

### Post by oldfred on 2019-04-09
Will it boot with recovery mode?
And if only Ubuntu, you need to hold shift key from BIOS until grub menu appears or if UEFI press escape key betweeen UEFI/BIOS and grub (perhaps more than once).

If you can get to terminal:
sudo apt-get remove --purge nvidia-*
sudo apt-get purge nvidia* bumblebee primus bbswitch-dkms

Or you may have to chroot into system to run those commands if you cannot recovery mode boot.

---

### Post by thewrapper on 2019-04-10
Just found a solution:

Boot a Live CD, then open a terminal.
Firstly, you have to mount the installed Ubuntu to /mnt and bind some other directories:
```
sudo mount /dev/sdXX /mnt
sudo mount --bind /dev /mnt/dev
sudo mount --bind /proc /mnt/proc
sudo mount --bind /sys /mnt/sys
```
/dev/sdXX is your Ubuntu partition (mine is sda5)
Now chroot to /mnt:
```
sudo chroot /mnt
```
Then purge the NVIDIA proprietary driver and every related packages:
```
apt purge nvidia*
```
Close the terminal and reboot after apt purged all the packages.
I finally got it to work again! So proprietary drivers was the problem.

Sources: [URL="https://askubuntu.com/questions/128113/how-do-you-remove-nvidias-proprietary-drivers"]https://askubuntu.com/questions/128113/how-do-you-remove-nvidias-proprietary-drivers
[/URL]             [URL="https://askubuntu.com/questions/145241/how-do-i-run-update-grub-from-a-livecd"]https://askubuntu.com/questions/145241/how-do-i-run-update-grub-from-a-livecd
[/URL]             (the first part explains how to chroot)
             [https://serverfault.com/questions/857474/install-package-via-apt-from-a-live-cd-to-the-real-system](https://serverfault.com/questions/857474/install-package-via-apt-from-a-live-cd-to-the-real-system)

Edit: Didn't see your answer was exactly the same.

---

