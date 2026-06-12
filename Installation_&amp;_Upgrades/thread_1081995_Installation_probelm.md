---
title: "Installation probelm"
date: 2009-02-27
forum: Installation &amp; Upgrades
---

### Post by vivin_west on 2009-02-27
I want to partition 50% of my disk for windows and 50% for Ubuntu. I have selected manual partition in the installation option and a little confused how to partition here..
Any advice?

---

### Post by Shampyon on 2009-02-27
Do you already have Windows on the drive? If not you can use the Windows partition tool to create two partitions ([guide for XP]("http://support.microsoft.com/kb/313348") - you have to scroll down a bit). Once you've done that you can put in your ubuntu disc and start installing. At some point you'll get a prompt asking if you want to create partitions Automatically or Manually. Choose Manual and just tell it to put "/" on the empty partition. Which filesystem you format to is up to you. Most people these days seem to recommend Ext3. I've always used ReiserFS, but on my next install I'm trying out Ext3 too.

Once the whole installation is complete, the GRUB bootloader will automatically include both your Ubuntu and Windows partitions as options for booting at computer startup.

---

