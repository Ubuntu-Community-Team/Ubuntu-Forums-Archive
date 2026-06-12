---
title: "Problems installing Ubuntu on Asus eee 900"
date: 2009-01-20
forum: Installation &amp; Upgrades
---

### Post by creasyj on 2009-01-20
I just purchased a new Asus EEE pc 900.  I bought it so that I could put Ubuntu on it.  I do not have an external cd/dvd drive so I researched bootable flash drives.  I have followed countless tutorials on how to make this happen.  I have used a couple different Ubuntu versions, 3 different 1gb usb flash drives, and made the bootable drive on Ubuntu AND Windows XP.  So far I have had no luck getting the eee to boot from any of these drives.  I formatted these drives with FAT32 like everyone says.  I have been using unetbootin to make the live drives but it does not recognize the drive as a bootable drive.  I always get this error:

"Reboot and Select proper Boot device or Insert Boot Media in selected Boot device and press a key_"

The unetbootin instructions seem to be pretty easy so I don't see that being the problem.  I have also set the boot order many different ways in BIOS but nothing works.  If anyone can help or has this same problem please help quickly.  I need this working asap for work and I can't use the Xandros os.  Thanks

---

### Post by Will4 on 2009-01-20
did you set the BIOS to boot from your external flash drive? if not do so...
also, why don't you try installing Windows first and then Ubuntu?

i think if you install Windows first you should be able to reboot from it to the flash drive with the Ubuntu instalation.

---

### Post by vladu on 2009-02-13
Hi,

I had the same problem. I searched the forums and apparently I had no MBR on my stick (most usb sticks don't). So, after making a bootable stick with usb-creator, i ran 
```
sudo install-mbr /dev/sdd
```
Be careful, you should find out what is the name of your removable drive - it can be anything starting with sda, and yours almost certainly isn't named sdd.

---

### Post by ThomasDenmark on 2011-08-29
1) Is there a way to check if the USB drive actually has an mbr, instead of just assuming?

2) How do I tell the device name of my USB drive? When plugging it in, three new devices appear in /dev: sdb, sdb1 and sg2, so on which of these should I call the install-mbr command?

3) What could the consequences be for calling the install-mbr on the wrong one of these three devices?


Thomas

---

### Post by ThomasDenmark on 2011-08-29
I found the problem in my case. In the BIOS of my Asus eee 900, you can choose the boot order. I had chosen 1: Removable devices, 2: Harddisk. But it still did not boot. 

Then I realized another option in the Boot tab called Harddisks. In there I found both the builtin harddisk and the USB pen (obviously my USB pen was inserted when I was in the BIOS). So I am guessing, that for some reason, it did not consider my usb pen 3.0 drive (16GB) to be removable but instead to be a hd. 

In that Harddisks menu, you can change the boot order between harddisks with + and -. 

I also found an answer to one of my follow up questions 1), how to decide if there is an MBR. Look at [http://superuser.com/questions/329467/how-to-see-if-usb-stick-has-mbr](http://superuser.com/questions/329467/how-to-see-if-usb-stick-has-mbr).

---

### Post by lokoloco on 2012-02-20
Hi
I got same problem.

I tried a different USB creator than recomended on Ubuntu installation guide.
I used Lili usb creator.

But I'm not that sure if usb creator was the reason for many fails to boot properly.


When turn on computer, press ESC, then select USB in first option to boot.

Works !!!

(turn on computer from off state, so, do not just restart)



Before this , I went to BIOS, by pressing F2, never works :(

Hope works for you

---

