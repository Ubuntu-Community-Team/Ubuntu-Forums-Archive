---
title: "Dell Precision M4800 &amp; Bluetooth"
date: 2020-06-30
forum: Hardware
---

### Post by nuukamuiskunen on 2020-06-30
Hello! This is my first post! TLDR in the end 

**Preamble (Wifi)**

I got my [refurbished Dell]("https://www.notebookcheck.net/Review-Dell-Precision-M4800-Notebook.104416.0.html") a few months ago and have been distrohopping ever since! (MX / Manjaro / Zorin / Mint...) I like to try things out and I am trying to strike some sort of fragile balance between things working with this particular ageing hardware, music production, looks, ease of use and support, and casual gaming capabilities. All the problems with wireless internet connection have ceded if I've made sure:

[LIST=1]
[*]The physical kill-switch isn't activated 
[*]Anything isn't disabled in BIOS 
[*]The operating system has had a chance to update, via wired connection if needed, and reboot. (Many times wireless isn't yet working during installation or first boot). 
[/LIST]
 
[B]Preamble (Bluetooth)
[/B]
But **the thing that has never worked out-of-the-box** (nor even after using some GUIs for hardware configuration and driver installation) is the** Bluetooth connection**.
I had to use wayyyy too many hours trying to make it work but I finally managed to do it following [these instructions.]("https://github.com/winterheart/broadcom-bt-firmware#broadcom-bluetooth-firmware-for-linux-kernel")
I downloaded [this piece of firmware]("https://github.com/winterheart/broadcom-bt-firmware/blob/master/brcm/BCM20702A1-413c-8143.hcd") and copied it to /lib/firmware/brcm/ as suggested in the instructions and rebooted, and everything worked! :KS
I am grateful for the github user [winterheart]("https://github.com/winterheart") for maintaining that repository and writing those instructions. 

Since then I found [this launchpad question]("https://answers.launchpad.net/ubuntu/+source/linux-firmware/+question/660927") which tells how you can download a (large) driver bundle [from Dell]("https://www.dell.com/support/home/fi-fi/product-support/product/precision-m4800-workstation/drivers") and from there extract a certain .deb-file and from the .deb-file extract a certain .hcd-file, rename it and move it to /lib/firmware/brcm/ 

If you are like me (novice and a little paranoid), you might feel that downloading firmware from the hardware manufacturer is preferable to downloading some unknown file from some unknown guy from github (called Hackimov :p ) and just placing that file smack in the middle of your supposedly secure system. I have no reason to distrust this person but, well, you know!
(The needed file is tiny (34.3 KB) while the Dell bundle containing that file is 222,9 MB, so maybe that might be a reason for you to get it from github.)

[SIZE=4]**TLDR;**[/SIZE]

This is what I do after a clean install to fix the bluetooth on Dell Precision M4800 by downloading and using a firmware file from Dell:

# I like to download my loads to Downloads
```
cd /home/$USER/Downloads/

```
# Downloads the driver package
```
wget https://dl.dell.com/FOLDER02159710M/1/M6800_M4800_A05.fish.tar.gz

```
# Extracts bt-dw1550-firmware_0.1_all.deb from the package
```
tar -xzvf M6800_M4800_A05.fish.tar.gz debs/bt-dw1550-firmware_0.1_all.deb
```

# Extracts the innards of the deb file to ~/Downloads/debs/
```
dpkg -x debs/bt-dw1550-firmware_0.1_all.deb debs/

```
# Moves and renames the newly acquired firmware file fw-413c_8143.hcd to  /lib/firmware/brcm/BCM20702A1-413c-8143.hcd

**[COLOR=#ff0000]using sudo:[/COLOR]**
```
mv -i debs/lib/firmware/fw-413c_8143.hcd /lib/firmware/brcm/BCM20702A1-413c-8143.hcd
``` 

# Clean-up, remove the downloaded redundant files and folders
```
rm -R debs/ M6800_M4800_A05.fish.tar.gz
```

[B]Don't forget to reboot!
[/B]

I hope someone finds this helpful! :KS



bonus tags that I wish I would have known to google sooner #-o: BCM20702A1, BCM20702A1-413c-8143.hcd

---

