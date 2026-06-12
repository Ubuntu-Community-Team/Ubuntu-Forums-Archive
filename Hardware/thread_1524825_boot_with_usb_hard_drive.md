---
title: "boot with usb hard drive"
date: 2010-07-05
forum: Hardware
---

### Post by gunkle on 2010-07-05
Here goes. I have a Toshiba satellite A45-s121 laptop with no hard drive in it. Died a few years ago. the other day I dusted this thing off and said lets see what i can do with it. Ubuntu 9.1 or lower (tried Xubuntu also) will boot up from live Cd or from live usb (4gb stick) I was able to install to a 3.5" 40gb hard drive in a wall powered usb enclosure. The bios on this laptop doesn't support booting from usb so i am using Plop ( I think that's what it is called) on a Cd then choosing usb. No problems can run the installed version from the hard drive in the enclosure. Next I broke out my 500gb Toshiba usb hard drive (powered through usb) installed ubuntu 9.1 to it with 1 70gb ext2 partition (first partition on drive), 1 3gb(?) swap partition (second partition on drive) and the rest is on a ntfs partition for windows. I can boot no problem off of this drive on my PC whose bios supports usb booting. I can't on my laptop. even with the plop Cd which works with the thumb drive and hard drive enclosure. the error message i get is 

GRUB loading.
error: unknown file system
grub rescue>


Any help would be great as I don't want to sink any money into finding and buying an ide hard drive this thing but would like to have a native install and not the live version. The usb enclosure kinda defeats the benefits of it being a laptop.

Thank you for any help. Oh yeah I tried to create a usb boot Cd from ubuntu as detailed [here]("http://www.google.com/url?q=http%3A%2F%2Fwww.pendrivelinux.com%2Fmake-a-usb-boot-cd-for-ubuntu-9-10%2F%23more-2681&sa=D&sntz=1&usg=AFQjCNFbpqcTcOPHO4vKgysp46O7EAwBIg"). it gives me some errors about not finding something. Will have to find the Cd and try again so i can put up what the message was. 

If this problem has been answered already I am sorry for asking again but 2 days of searching hasn't yielded an answer that works for me. 

Thanks
Gunkle

---

### Post by gunkle on 2010-07-06
So I had some limited success last night. I reinstalled 9.1 onto the portable hard drive using my PC (much faster then the laptop) and installed grub to /dev/sda instead of default which I think was the problem. when i boot up the laptop to the portable hard drive i now get the grub menu but then is fails  BIOSdisk write error. It shows all my partitions on my Pc so I'm thinking tonight I try again this time installing from the laptop and see if that installs grub with the correct options.

---

### Post by gunkle on 2010-07-06
well I tried the install from the laptop itself and it doesn't seem to have changed anything. the Grub menu that I get is still the same one with references to windows vista partions that are no my pc not the laptop. gotta see how to get rid of them and try again

---

### Post by rizos on 2010-07-06
bump

---

### Post by C.S.Cameron on 2010-07-06
Have you tried reinstalling grub to it from the Live CD using the laptop.

---

### Post by gunkle on 2010-07-06
yes i tried sudo grub-install and i get an error stating that it cant find files. I'm reformatting the portable drive with gparted and gonna try install again with just one big ext2 partition and a swap partition.

---

