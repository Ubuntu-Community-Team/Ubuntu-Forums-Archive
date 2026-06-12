---
title: "[SOLVED] Bootable Ubuntu Flash Drive, Works On PC and Mac"
date: 2009-02-10
forum: Installation &amp; Upgrades
---

### Post by robinsn1 on 2009-02-10
RECOMMENDED: ADVANCED USERS ONLY

NOTE: THIS IS A FULL INSTALLATION OF UBUNTU. THIS IS NOT A LIVE USB STARTUP DISK.

Hello,

My roommate and I have successfully created a USB flash drive that runs Ubuntu and will boot on any PC or Intel Mac, capable of USB booting.


REQUIREMENTS:
1. One (1) Flash Drive with a minimum of 4GB of free space **
2. Ubuntu Live CD
3. Working disc drive
4. Intel Mac (only for compatibility with Intel Macs)

** Recommend: Do NOT use flash drives with U3 Smart capability (e.g. GeekSquad flash drives).


SOFTWARE:
[rEFIt]("http://refit.sourceforge.net") **

** Only required for making bootable on Intel Macs. Must use a Mac to install rEFIt initially.


PREPARATION:
1. Reformat entire flash drive to FAT32.
[INDENT]For Macs, use Disk Utility to format to FAT.[/INDENT]
[INDENT]For Windows, right-click on drive and select format to FAT32.[/INDENT]
[INDENT]For Ubuntu, use gparted and format to FAT32.[/INDENT]
2. Reboot with Live CD and USB flash drive in place.
3. On Live CD menu, select "Install Ubuntu."
4. Continue through installer until you reach the partitioning step, step 4 of 7.
5. Select "Guided - Use Entire Disk" and select flash drive.
[INDENT]WARNING: Do NOT select your internal hard drive.[/INDENT]
6. Continue until you reach step 7 or 7, Ready To Install, select "Advanced" before continuing.
7. Check "Install Boot Loader" and device set for installation is the USB flash drive.
8. Select "Okay" and then "Install."
9. Reboot and remove the CD.

FOR PC USERS (IF MAC USER, SKIP TO MAC SECTION BELOW):
10. Your drive is now capable of booting onto any PC (not Mac) capable of booting from a USB device.
11. Change BIOS to boot from USB.
12. To also make your drive capable of booting on Mac, continue to Mac section below.

FOR MAC USERS:
10. Reinsert Ubuntu Live CD.
11. Boot from CD by holding "C" on startup.
12. Select "Try Ubuntu."
13. Open a new terminal.
14. Run the command 'sudo apt-get install gparted'.
15. Within terminal, type 'gparted'.
16. Gparted GUI will open: select flash drive (in top right corner drop down menu).
17. Right click swap partition, and select 'Swap Off'.
18. Right click swap partition again, select 'Delete'.
19. Right click on extended partition, select 'Delete'.
20. There will now be two partitions, one containing Linux and the other unallocated.
21. Right click the unallocated partition, select 'format'.
22. Format partition to FAT32, and click 'Apply'.
23. Exit gparted.
24. Reboot, remove CD, and boot into Mac OS X.
25. Open Disk Utility (/Applications/Utilities/Disk Utility).
26. Format the unallocated partition (the one that was previously the swap) to 'Apple OS Extended - Journaled'.
27. Open the rEFIt disc image, and copy the folder 'efi' to the root directory of the unallocated partition.
28. Open Terminal (/Applications/Utilities/Terminal) and run the command 'cd /Volumes/MyDrive/efi/refit' where 'MyDrive' is the name of your USB flash drive.
29. Next run the command './enable.sh' in Terminal. NOTE: You must have administrator privileges to do this.
30. Quit Terminal, reboot the computer, and hold the Option key on startup. You will see Mac OS X and and rEFIt next  to each other. Select rEFIt, and you will be asked which OS you want to boot into. Select Linux and enjoy.

After following these steps, you will have a flash drive that is fully capable of loading Ubuntu onto any PC (that can boot from USB) and any Intel Mac.

NOTE: This drive will NOT work on PowerPC Macs (any Mac that is not using an Intel processor).

While this would likely work with many other Linux distros, it has only been tested with Ubuntu. The PCs used in testing this were a HP and a Dell. The Mac used in testing this drive was a 1st Gen MacBook Pro. After multiple boots on all three computers, and additional installations on other flash drives, this method has shown to be very reliable. Following the above steps exactly, there have been no apparent issues on any trial.

All drives used in the trials were PNY 8GB flash drives.

Since the swap partition no longer exists, it is recommended that you set turn swappiness off. You can do this by running a terminal in Ubuntu, opening the file '/etc/sysctl.conf' and adding the line 'vm.swapiness=0'.


About The Authors:
The two of us (Robin and Kellen) are roommates at Iowa State University. Robin is an undergraduate studying Psychology and Kellen is an undergraduate studying Aerospace Engineering. Our inspiration for this project was that we wanted a way to have a stable operating system be "plug 'n' play" and be usable on (almost) any computer. In addition, it is of particular use to Kellen, who can now do all his programming for engineering classes via his pocket-size operating system. It took one very long night, but we succeeded. Beforehand, though, we did search for quite some time and was not able to find any 'how to' on going about this task.

Enjoy,
Robin and Kellen

---

### Post by subdee on 2009-02-13
Very good guide. Have been looking for something like this for a while now.

Just one issue, when it comes to graphics, would I have to change it to the vesa driver to get a gui in different machines? Because I had many graphics glitches when using it on different machines.

---

### Post by Vinas on 2009-02-13
I guess you should use minibuntu for this since things can get heavy when running off a USB key... At least if you need more performance it's worth checking out: [http://ubuntu-mini-remix.crealabs.it/]("http://ubuntu-mini-remix.crealabs.it/")

Use the same steps above but instead use the minibuntu CD. Most of the apps you'll need are there plus it will run nicely off of a USB key. Thanks to the OP for posting this guide BTW.

---

### Post by mzahit29 on 2009-02-20
how fast does it work? is it clumsy, should we try minibuntu?

---

### Post by timcwilliams on 2009-02-20
Ok, I did something similar with a flash drive but it had problems at first. At the end of the install when it is configuring grub, it looks for other operating systems and it saw my other ubuntu partitions (an amd64 partition and a generic 32bit partition) and linked those and the new install on my usb drive together :0( My system would not boot without the drive inserted after that, gave grub error 21. Since I had just done a complete full disk install of ubuntu on a new machine and was just playing, I re-reinstalled and called it a learning experience. I guess I figured out how to make a crude hardware boot dongle like an ignition key for your computer. 

Take 2. I took the hard drive out of my notebook so the promiscuous install cd could only *dance* (self censor) with the drive I wanted it to. I booted with the install cd (xubuntu 8.10) inserted my flash drive and installed xubuntu on the flash drive without issue It works awesome. So much better than using the live cd or the usb startup disk. I can upgrade without bloat now. Its not as fast as a hard drive but I don't expect it to be. It takes less time to boot from my flash drive than it does to launch OpenOffice Portable or FireFox Portable in windows from the same drive.

It would be nice if the install cd noticed when you were installing ubuntu on a removable disk and at least asked you if you wanted to link it to the rest of your system or do an independent install. For now, unplugging other hard drives is a quick and dirty solution for installing ubuntu on a flash drive without messing up everything else.

---

### Post by Contrast on 2009-03-18
Very well-written guide, and a much needed one. Props for that.

I had actually tried this a month or two ago, and everything "worked" fine - no boot issues or anything like that. It was, however, unbearably slow - slower on my 2.3GHz C2D than a live CD on an old P4. I *think* the drive is U3-capable - could that be the reason for the sluggishness?

subdee - At least the past couple releases of Ubuntu don't require you to specify a graphics driver; everything is auto-configured upon recognition. If you're getting issues though, you could add this line:
Driver "vesa"
to the Device section of your xorg.conf.

---

### Post by kodachrome64 on 2009-04-24
Been trying to get this working without success on a macbook pro and a macbook both core duo 2. Could this be the problem? I've read that booting usb from these core duo 2 models does not work. Something about 64bit?

---

### Post by Jynxxander on 2009-04-27
2 questions...
What version of Ubuntu are we talking about? [I automagically assume all.]
What version of Mac OS X is used for the Mac version? [Cuz I don't think Tiger (10.4.11 specifically) can boot from a USB drive even with rEFIt]

---

### Post by deejay_45 on 2009-08-12
** Recommend: Do NOT use flash drives with U3 Smart capability (e.g. GeekSquad flash drives).

<<< What issues were encountered when using a flash drive with U3 smart capability? Why don't you recommend it? I just bought a 16GB flash drive with U3 capability and am thinking of using it to experiment with an Ubuntu installation.

---

### Post by MadBillyGoat on 2009-08-12
Hello,
 thanks This  worked, The only problem is that I am now stuck using my usb only,  The first time I did the Install to the flash drive I forgot to pick advanced tab and pick the drive to install grub, now i think that the wrong information on my hard drives, because I get error 21 or 17,  The last time I reinstalled on flash drive I remembered to do that last step before install, So now It will load to the grub but, If i pick ubuntu on the system drive, I get " error no file fiound "  Help Please.. I have no idea where to look, I found the grub in bood dir. but I do now know where to  mod.  I could fix this on windows.. Is it a simular situation just needs to be pointed to the right drive?.. 

Thanks for any help.

Mad Billy Goat

---

