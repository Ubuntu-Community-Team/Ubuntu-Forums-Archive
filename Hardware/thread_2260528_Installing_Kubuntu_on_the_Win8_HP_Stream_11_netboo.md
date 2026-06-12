---
title: "Installing Kubuntu on the Win8 HP Stream 11 netbook"
date: 2015-01-12
forum: Hardware
---

### Post by oreofields on 2015-01-12
I have successfully installed Kubuntu on my HP Stream 11. First of all I found that it is not easy to find information about this netbook, since doing a search with a name like 'Stream' yields all sorts of extraneous stuff. To install Ubuntu, follow the instructions found on Windows 8 sites for turning off Quick Boot in the Power section of the Windows Control Panel. Then a Youtube video revealed to me the secret of how to get the bios and boot options: Upon boot (after a full shutdown), hit Esc repeatedly. Then the menu will appear. Choose F10 to get the bios settings. In the bios, turn on the Legacy boot option. 

With that done, after booting and getting a menu, you choose F9 to get the boot devices. 

I noted that some Linux distributions have the option to boot from an EFI file on the flash disk plus another choice for booting the live distro. The original Windows installation shows up in the boot menu as based on an EFI file, and I discovered that it usually worked better to boot live Linux from an EFI file. Distros that have this feature will have an EFI/efi subdirectory as part of the root directory of the live USB installation.

First I tried lots of different Linux's from Distrowatch.com, as I normally have not recently been using Ubuntu. I was experiencing crashes with almost all of them. I did not realize the source of the problem. It was that the button-less touchpad of this device will cause a crash in most distros the first time when you try to click! One of the first things I was trying to do was to log on to my wifi. So whenever I did that, the distros would crash. It was only when I happened to plug in an external mouse that I began to see that some distros were correctly recognizing the wireless adapter.

I think that most of my problems came from the trackpad, however I did notice some improvement on a couple of distros when I booted in Save Mode, or Safe Graphics mode.

If the HP Stream 11 has bluetooth, Kubuntu is not recognizing it. The SD card slot works. All the Fkey functions that I have tried work. The only thing that doesn't work well is the trackpad. By the way, when using Windows 8, I noticed that Windows had much better control of the trackpad than all Linux distros I have used. I could type with the trackpad enabled and I did not get the problems with the cursor jumping if I brushed the trackpad like I do in Linux. And various gestures and finger combinations worked. But since I have used netbooks with Linux now for a long time, I am used to using an external mouse and turning off the trackpad. So it is not really a problem for me to not use trackpad on this device. I like the price and everything else about it. Ubuntu has a great setting where you can disable the trackpad any time an external mouse is plugged in.

Besides the trackpad, there is a second major problem about this netbook: Several Linux distros did not recognize the SSD (hard) drive when I tried to install the distro from the live install on my flash drive. The newest LinuxMint KDE version did not recognize the hard drive. Now that Kubuntu is installed, if I start the Partition Manager, it refuses to open and the system starts showing signs of distress. I think it may have been a fluke that Kubuntu's install program recognized the SSD drive! (It so happened that Windows 8 was ready to install an update just when I aborted that process and rebooted to install Ubuntu.) Now that Kubuntu is installed, the SSD works perfectly for installing programs and moving files around, although the disk is not properly recognized in the Dolphin file manager. There the drive is listed as a "27.2 GiB Removable Memory." 

For whatever reason, the Kubuntu installation has been working great ever since. Closing the lid causes the machine to go to sleep. Opening the lid causes it to be immediately back to life. The programs load quickly and the performance is snappy with a browser and 2-3 other programs running. Kubuntu is NOT snappy in booting from scratch on this machine! It takes a full 2 minutes and 1 second for the log-in screen to appear. Then after giving my password, another 22 seconds before I can click to run a program in the panel.

I hope that someone else who needs this info will be able to find it. And I hope someone can give information on getting the hard drive to be properly recognized and perhaps getting the touchpad to work.

---

### Post by oreofields on 2015-01-12
Update: The sound on the HP Stream 11 running Kubuntu isn't working now, however I know I have heard it work before. It has lost it's device information.
Another update: Sound works fine. But I don't know why it stopped working earlier. I thought it was closing the lid and the machine going to sleep. But that has not caused it this time, after closing the lid 3 times.

---

### Post by oreofields on 2015-01-13
Built in Internet adaptor stops working rather quickly, and I think I have read that this is a weak element of this device, even using Win8. The only way to get it to connect again is to reboot. Using a USB wifi dongle works well and stays on. Does anyone know how to find and install the driver for the built in wifi?

---

### Post by Ollie30 on 2015-02-20
If the built in wifi is based on a relatively new chip, chances are you have to wait for a kernel or core update that supports it.  Have you tried booting from the microsd reader?

---

