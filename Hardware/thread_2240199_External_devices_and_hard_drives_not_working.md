---
title: "External devices and hard drives not working"
date: 2014-08-18
forum: Hardware
---

### Post by kiwipenguin on 2014-08-18
Hello,

Does anyone know how I can find the reason why my computer does not detect anything external that I have connected to it?

I have tried connecting external hard drives, memory sticks and disk drives by usb, and sd cards in their slot, but nothing happens. There is nothing detected - nothing to mount or unmount.
The drives and sd cards work ok on other computers.
They also previously worked on my computer but not any more. I am not sure what changed or when.
I have 2 usb ports and 1 sd card slot. None work.
I am still using Ubuntu 11.10 but as soon as I can connect a hard drive and back-up my files, I will upgrade.

How can I troubleshoot this and find out whether it is an internal hardware or software problem?

On a side note, another option (for a back-up) would be to file share by wifi using samba but I can't download samba unfortunately. - Probably because 11.10 is not supported anymore?

Thanks for your help!

---

### Post by yancek on 2014-08-18
When you have an external drive attached while booting the computer, check the BIOS to see if it is detected.  When you plug in an external drive, check to see if a new directory shows under /media, or have you done this already.

---

### Post by kiwipenguin on 2014-08-19
Hi,

Nothing shows under /media when I plug in any of the external drives.
I looked in the BIOS and couldn't see that the external drive was detected in any of the menus, - I assume it would be easy to find if it is detected... (unless there is a special location to find this)

Further update: a usb mouse does not work either.
Also, cheese no longer detects my built-in webcam - I wonder if this is related..?

Thanks,

---

### Post by yancek on 2014-08-19
If you looked in the BIOS with one or more of the external drives attached and it did not show, it seems more like a hardware problem.  I'm not a hardware person so don't have any suggestions.  You might post information on the specific machine you are using and someone may know which option in the BIOS you need to select to get that information.

---

### Post by kiwipenguin on 2014-08-19
Thanks yancek,
hopefully there is somebody out there who can help.

---

### Post by varunendra on 2014-08-19
It seems your kernel (and thus the USB driver/stack in it) is broken. Just a guess, but most likely.

You should try re-installing the kernel you are using. But first, you may need to modify your "sources.list" file to change the address of repositories (repositories of EOL releases are moved to "old-releases.ubuntu.com"). To do that with a single command -
```
sudo sed -i 's/archive.ubuntu/old-releases.ubuntu/' /etc/apt/sources.list
```

Then do -
```
sudo apt-get update
sudo apt-get install --reinstall $(uname -r)
```
Reboot and see if USB works now. If not, at least you should be able to install samba now.

---

### Post by kiwipenguin on 2014-08-19
Thanks Varun, your suggestion was very helpful.
I followed your instructions and although the USB still doesn't work, I was able to install Samba.
Now I will try to back everything up by wifi and then at least I can upgrade my version of Ubuntu.

---

### Post by varunendra on 2014-08-19
You're welcome :)

Although we could try to dig deeper and fix the USB issue, but it won't make much sense on an outdated Ubuntu version. Just download the ISO of 14.04 and test it in Live mode first, to make sure everything works and it was not really a hardware problem.

To download the ISO, torrents are always recommended due to higher download speed and guaranty of data integrity.
Official links for torrents : [http://www.ubuntu.com/download/alternative-downloads](http://www.ubuntu.com/download/alternative-downloads)

I have to make a correction regarding my previous post - The external devices not showing in the BIOS do suggest a possible hardware problem as **yancek** pointed out earlier. But then some BIOS I have seen do not show external devices anyway, or show them in a category where the device is unexpected to be found (for example, some Award Bios versions show external Hard Disks under the "Floppy Drive" category).

So testing the machine with a Live DVD/USB  of 12.04 or 14.04 should be the best way to confirm whether it is a hardware problem or not. If the USB works with them, the thread should be marked as [SOLVED].

---

### Post by kiwipenguin on 2014-08-20
Thanks for that,

I'm just in the process of backing up my files via wifi to another (windows) machine. It's rather slow but when I'm finished I will try to update to 14.04

I cannot test a live version of 14.04 by DVD/USB because my computer still won't detect anything connected externally. - not even a mouse or my built-in webcam work any more.

So, I guess I will have to download and run the update directly (if possible).

Will my settings and changes/tweaks/downloads/packages/etc automatically transfer over to the new version? Or, will I have to download all of them again..? Which would mean I will have to build a list of everything that I have ever had to do to get 11.10 to work properly... from where, I am not sure yet.

Hopefully I will find a simple way to carry over all necessary tweaks into the new version.

---

### Post by varunendra on 2014-08-21
Does even the DVD drive not work anymore? If it is only a USB issue, the optical drive should work.

Upgrading to 14.04 directly from 11.10 is NOT possible. You must do a clean install. You may create a list of installed packages (using "dpkg --get-selections" trick) so you can install them in one-go on the fresh install of Ubuntu (using "dpkg --set-selection" with the created list).

I'm not sure if there is a promising way to carry the tweaks/settings across a clean install, but if you need help with the "dpkg --get-selections/--set-selections" method to install the applications automatically, please search the forums/internet first, since I may not get time to post back the details in a reasonable time.

Or just post a new thread asking help with your objective, and hopefully someone may be able to suggest an even better way to keep/carry forward whatever possible.

---

### Post by kiwipenguin on 2014-08-25
Thanks Varun, you have been very helpful. Unfortunately I don´t have a built-in optical drive. It needs to be connected with USB.
Yes I think I will try to do clean install of 14.04.

---

### Post by varunendra on 2014-08-25
Some alternative ways to install Ubuntu on the system without CD/DVD/USB : [https://help.ubuntu.com/community/Installation](https://help.ubuntu.com/community/Installation) (particularly, [Network Installation]("https://help.ubuntu.com/community/Installation#Server_and_network_installations"))

Directly boot and install from ISO image on hard disk : [https://help.ubuntu.com/community/Grub2/ISOBoot](https://help.ubuntu.com/community/Grub2/ISOBoot)

Good Luck with your new installation !

---

### Post by Vladlenin5000 on 2014-08-26
Only an hardware problem could prevent you from booting, trying and installing from CD/DVD with an external USB drive... If the drive it isn't recognized when you try to select it as a boot device you can be sure IT IS a faulty hardware. If, however, it's recognized and boots the DVD then you should try the live environment and make sure everything else is working as it should.

---

