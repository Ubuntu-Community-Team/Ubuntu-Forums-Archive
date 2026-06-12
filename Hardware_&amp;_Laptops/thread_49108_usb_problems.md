---
title: "usb problems"
date: 2005-07-15
forum: Hardware &amp; Laptops
---

### Post by sawjew on 2005-07-15
hi all,

I have a Gigabyte GA7DXE motherboard running an Athlon XP 2100+ processor. I have been running Windows XP and have just installed Ubuntu for another venture into LInux.  I am unable to access anything plugged into my usb ports.  I have a canon usb scanner which doesn't show up anywhere and a canon usb printer which is not detected by the new printer setup.  both of these functioned perfectly with a PCLinuxOS live CD and I have used the printer successfully with Suse 9.1 professional.   My mp3 player does not show up when plugged in either and my usb hub shows no lights and appears to be inactive.  hotplug also hangs for a while on boot.

I have used usbview to view the status but I am unable to copy and paste here.  it shows 0 bandwidth allocated and 0 power required which does not seem correct although I am not really up on what it should be.  

I read some similar problems in some forums and flashed a new bios, which was one of the suggested solutions, which made absolutely no difference.

can anyone please help me.  I really like Ubuntu and would like to keep using it if possible.

---

### Post by adrian440 on 2005-07-15
Rather drastic solution: remove hal. I used to have gnome startup problems, I wasn't sure whetherthe problem was hal, gnome-volume-manager, udev, or a combination of them, but since removing hal, everything has worked much better. Of course nothing comes up automatically anymore, but I'm fine with that. I have my doubts that hal is mature enough in its current state. You should still be able to use usb devices, but you may need to add a line in you /etc/fstab. I added this:

/dev/sda1       /media/usbdisk  vfat    rw,user,noauto,noatime  0       0

---

### Post by sawjew on 2005-07-17
thanks for the assist.  removing hal fixed the problem and also allowed my windows to mount at boot but I couldn't mount the network card.  seems like fixing one problem leads to another.

---

