---
title: "bios update with usb stick"
date: 2011-09-30
forum: Hardware
---

### Post by martinyt on 2011-09-30
I have a lenovo x121e and some problems with the wifi. The solution seems to be resolved when updating the bios: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/812866?comments=all](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/812866?comments=all)

However, when I make a bootable usb stick with unetbootin with the downloaded .iso update image, it fails. I get the unetbootin "startpage" but it can not boot anything?

What am I doing wrong?

---

### Post by psrdotcom on 2011-09-30
Does the USB successfully burned with ISO?

---

### Post by martinyt on 2011-09-30
unetbootin does not report any errors..... but it finishes quiet fast. The startup disk creator in ubuntu wont recognise the .iso.

Is some way to test if it burned successfully?

---

### Post by dino99 on 2011-09-30
how does you might update that bios ? On my Asus motherboard bios, i can select a tab to find & read a new bios version stored somewhere (hdd/usb stick/floppy/...) and the bios is able to upgrade itself (AMI bios)

so check if you need to copy or burn it on the usb stick (read lenovo support/forum)

---

### Post by radio_listener on 2011-09-30
I had the exact same problem. I have a Thinkpad L520 and meant to update the BIOS and the Intel SSD 320 Firmware without wasting blank CDs.

I tried the 'Startup Disk Creator' included with Ubuntu but the ISO file that contains the BIOS update was not recognized. After searching for a solution I learned that the 'Startup Disk Creator' only accepts Ubuntu ISO images or ISO images of derivatives like Mint.

Next I tried UNetbootin. It put some files on the USB flash drive but all of them together were only about 100K in size. The ISO file had about 17M.

About to give up, I found the BIOS upgrade page on the thinkwiki which is a great source of information about running Linux on Thinkpads.
[http://www.thinkwiki.org](http://www.thinkwiki.org)

On the page referring to BIOS upgrades the grub4dos section contained the solution to my problem.
[http://www.thinkwiki.org/wiki/BIOS_Upgrade#Using_grub4dos_.28also_for_Linux.29](http://www.thinkwiki.org/wiki/BIOS_Upgrade#Using_grub4dos_.28also_for_Linux.29)

Here is what I just did:
Download [http://download.gna.org/grub4dos/grub4dos-0.4.4.zip](http://download.gna.org/grub4dos/grub4dos-0.4.4.zip)
(There are newer versions but I wasn't sure if these are alphas, betas or RCs or something similar).
Extract
Insert USB flash drive
Open terminal, cd into grub4dos directory
Run sudo ./bootlace.com /dev/sdX, where /dev/sdX is the device name of the USB flash drive. I used the 'Startup Disk Creator' to find out the name. I put in /dev/sdc, NOT /dev/sdc1. I wasn't sure about what makes more sense but the sdc without any numbers seems to be correct and now that I think of it makes more sense since the MBR of the whole flash drive should be used not the MBR location of the first partition which would be sdc1.

Copy the ISO to the flash drive

Open menu.lst with gedit and append the following to the end while changing the name of the ISO file in the second row (the XXXXXXXX) to the name of the ISO image you just copied to the flash drive in the previous step:
title thinkpad-bios
map (hd0,0)/XXXXXXXX.iso (hd32)
map --hook
chainloader (hd32)
boot

Close gedit
Unmount flash drive

This procedure worked flawlessly for the BIOS update.

The Intel SSD 320 Firmware update also worked but after selecting it from the boot menu it told me that the geometry was off. Notwithstanding, it booted and offered to apply the update which worked fine.

---

### Post by martinyt on 2011-09-30
Thank you radio_listener. This solved my issue with the Bios update. (although you forgot to tell about the copy of the to files - see link)

Unfortunately it did not solve my wifi problem, but that will be an issue for another post.

Thanks!

---

### Post by radio_listener on 2011-10-02
I'm glad that I was able to help.

I'm just curious. What exactly do you mean by "to files"?
I reread my little how to before posting it. Which step did I forget?

Edit:
Now I see what you mean :)
"Copy the files grldr and menu.lst to the root directory of your pendrive." is what I forgot.

---

