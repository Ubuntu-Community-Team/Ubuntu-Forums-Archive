---
title: "Bootmanager"
date: 2009-04-10
forum: Installation &amp; Upgrades
---

### Post by TempleClause on 2009-04-10
Hello,

I've installed Ubuntu to my external HDD via usb. But now i'm just seeing Vista and Xp which I could start. But Linux isn't there. I heard that I could add it with EasyBCD but that didn't work.

Greets

---

### Post by meierfra. on 2009-04-10
See what happens if you set your bios to boot from the USB drive.

---

### Post by TempleClause on 2009-04-10
I've allready tried that but than it's showing just the normal bootmanager as usual

Greets

---

### Post by flyingsliverfin on 2009-04-10
can you boot from a cd?

otherwise, just as a test, you could install ubuntu onto ur USB memory stick, ([http://www.pendrivelinux.com/ubuntu-810-install-using-the-built-in-usb-installer/](http://www.pendrivelinux.com/ubuntu-810-install-using-the-built-in-usb-installer/)   if you don't know how), then boot from the mem stick. just erase everything afterward to get ur mem stick back to normal. you might need to format again though.

if that works it should tell u if its a problem with the HDD or the computer.

---

### Post by TempleClause on 2009-04-10
yes i can boot from a CD .. i'm not that stupid ;-) I'm allthough an IT student xD 

Greets

---

### Post by flyingsliverfin on 2009-04-10
how am I supposed to know how old or experienced you are? Just to make a point try to guess what my age is. what about the usb memory stick test? does it work>

---

### Post by TempleClause on 2009-04-10
didn't wanted to attack you or something ! i'm doing it in the moment..

---

### Post by flyingsliverfin on 2009-04-10
lol its fine. its actually a family trait to like argueing and making points. my mom, dad, grand parents on both sides all love to do that and debate too.

but still, I don't think that you would have thought im 13.

---

### Post by meierfra. on 2009-04-10
In order to get a clearer picture of your setup, I suggest to boot from the Ubuntu LiveCD and  download the Boot Info Script to  your desktop:

[https://sourceforge.net/projects/bootinfoscript/]("https://sourceforge.net/projects/bootinfoscript/")

Then open a terminal (Applications > Accessories > Terminal) and type:

```
sudo bash ~/Desktop/boot_info_script*.sh
```

That will create a "RESULTS.txt" file in the same directory from where the script is run, namely your desktop; please copy/paste the contents of the  RESULTS.txt file to your next post (use the code tags).

---

### Post by TempleClause on 2009-04-10
No I wouldn't xD
That's acctually a bit emberassing for me :D I'm 16 ^^

---

### Post by TempleClause on 2009-04-10
Probably it's easier when you tell me how to do it than when we try to fix my crappy work :D.

So that's what I would like to have. I would like the Laptop to boot automaticly into Ubuntu when I plugged in my external USB HDD. Otherwise Windows should boot up normally.

Greetings

---

### Post by flyingsliverfin on 2009-04-10
what was the result of the test that you did w/ theusb stick?

srry, I have to go do something. might be back in about 2 hours.

---

### Post by TempleClause on 2009-04-10
Emm acutally couldn't do it probably because my stick is formated as NTFS and not as Fat32 ...

---

### Post by flyingsliverfin on 2009-04-10
time for 1 more post:

back up ur files and format it again to fat32. its really easy from ubuntu live cd.       btw; don't format anything but ur memory stick. you'll probably lose ur vista or whatever else you have if you do.        use gparted (easiest)

also do what meierfra. said. he's probably more helpful than me. I really know very little. lol

---

### Post by TempleClause on 2009-04-10
I formated it as Fat32 but still i can't make a USB Startup Disk....

---

### Post by flyingsliverfin on 2009-04-11
[http://www.pendrivelinux.com/ubuntu-810-install-using-the-built-in-usb-installer/](http://www.pendrivelinux.com/ubuntu-810-install-using-the-built-in-usb-installer/)

should work...

---

