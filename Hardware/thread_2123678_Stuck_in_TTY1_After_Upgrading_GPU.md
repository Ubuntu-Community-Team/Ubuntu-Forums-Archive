---
title: "Stuck in TTY1 After Upgrading GPU"
date: 2013-03-08
forum: Hardware
---

### Post by Xplorer4x4 on 2013-03-08
I swapped out my 4890 for my new 7770. However I am stuck in tty1. I have:
1. Tried to reconfigure xorg.
2. Made sure all xord-server-video- driver were installed.
3. I did sudo apt-get install gflrx
4. sudo apt-get install fglrx-updates

jockey-text -l reports the proprietary driver is installed and activated. 

When trying to go to tty7, I notice it says video driver fall back failed, but also hangs on something to do with the alsa sound mixer(I can reboot and grab the exact error message in a min).

Oh and I wonder if some remnants of my failed attempt to install the proprietary drivers is left over because since then, I see a grey Kubuntu boot screen for a split second. It only started after trying to install the driver for my 4890.


ty7 gets stuck at *starting timidity++ alsa midi emulation. [OK]

---

### Post by ManamiVixen on 2013-03-08
Whenever upgrading video cards, it's usually a good idea to remove the proprietary driver and reinstall after the new card is inserted since some cards have special flags needed thrown or put down when DKMS builds the ATI/Nvidia driver module. Also ALSA could be throwing a hissy fit due to the new HDA Audio codec in the new card if the card has HDMI.

---

### Post by Xplorer4x4 on 2013-03-08
Like I said the proprietary drivers failed to install. I thought I had cleaned up the left overs but I guess not. Either way I was not using the proprietary drivers prior to swapping cards. The propritary drivers, left over or not, were not enabled.

As for ASLA, both the old card and new card had/has HDMI ports.

---

