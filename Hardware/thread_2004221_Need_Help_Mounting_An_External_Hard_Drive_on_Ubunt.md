---
title: "Need Help: Mounting An External Hard Drive on Ubuntu 8.10"
date: 2012-06-15
forum: Hardware
---

### Post by Anyname on 2012-06-15
Need Help: Mounting An External Hard Drive on Ubuntu 8.10


Hi.

I'm using Ubuntu 8.10 on a HP Vista notebook because that version of Ubuntu boots up and recognizes an external HDD I have connected to my notebook via USB. I'm unable to mount location... Can't mount file, are the error messages I'm recieving. I need help, my brothers pictures for his house painting business are on this HDD and I'm trying to help him get them off of a dead XP Acer computer. Acer HDD is Windows OS XP.

Someone suggested when I find externals drive device ID, I could mount is using this command. But I don't know the external drive device ID. The external enclose case I'm using is a 

2.5" Portable USB2.0 by Masscool. Model#: UHB-UPS255

mkdir /media/usb
sudo mount -t ntfs-3g /dev/sdx /media/usb (replace sdx with the actual device ID)

---

