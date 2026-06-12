---
title: "Live USB for System Tools?"
date: 2008-10-22
forum: General Help
---

### Post by anotherdisciple on 2008-10-22
I often us a live cd of ubuntu to use gparted, or to mount a bad NTFS partition to backup the files, etc.

However, the ubuntu live cd is slow... I can put it on a flash drive and it would be faster, but I want to complicate things even further... haha.

Am I able to sort of "dual boot" a flash drive? Make a partition that runs Gparted live, a partition that holds some other utility, etc. That way I can run just Gparted when I need Gparted, or just another tool when I need it. That way I don't waste time loading other junk that I don't intend to use at the moment.

Or, is there a good utility that does all of this without all the extras that come with a typical live cd?

Thanks,
      Nick

---

### Post by pebo on 2008-10-22
[http://www.sysresccd.org/Sysresccd-manual-en_How_to_install_SystemRescueCd_on_an_USB-stick]("http://www.sysresccd.org/Sysresccd-manual-en_How_to_install_SystemRescueCd_on_an_USB-stick")> It is very easy to install SystemRescueCd on an USB stick. That's very useful in case you can't boot from the CD drive. You just have to copy several files to the stick and run syslinux. The install process can be done from Linux or Windows. Follow instructions from the Manual for more details. 
I haven't tried it on a usb stick but it has bailed me out as a cd more than once. May be worth a shot. It has a heap of utilities on it.
edit: updated link

---

### Post by C.S.Cameron on 2008-10-22
If you do a full install to flash drive you can download any tools to it that you can to hard drive.
Live USB's made using usb-creator will also save and run installed utilities, just ensure lots of "reserved extra space".

---

### Post by Mister.Vash on 2008-10-22
Check this site out [http://www.pendrivelinux.com/](http://www.pendrivelinux.com/) they have step by step guides which worked for me

---

### Post by dcstar on 2008-10-23
> **Mister.Vash said:**
> Check this site out [http://www.pendrivelinux.com/](http://www.pendrivelinux.com/) they have step by step guides which worked for me

[https://wiki.ubuntu.com/LiveUsbPendrivePersistent](https://wiki.ubuntu.com/LiveUsbPendrivePersistent)

I have just put 8.10 beta on a 8G stick - with a 3G "casper-rw" partition that holds all the changes you make.

I have found it is better to use the actual 8.10 system (fully updated) and use the inbuilt tool for creating a USB drive install.

I also use the 5G FAT32 partition for general file storage in case I have to move things to/from Windows machines.

---

