---
title: "installtion from USB impossible - operating system missing"
date: 2009-07-27
forum: Installation &amp; Upgrades
---

### Post by maxxtwayne on 2009-07-27
Hi, 

I've tried to install the Ubuntu Network Remix on a Samsung NC10 and was unable to.
I've got a "operating system missing" or just a blank screen, depends of the USB key i try.

Yes, i've tried with two differents USB key, tried with the official 9.04 and the nightly build.
I tried to fill the keys with a dd or with flashnul from Windows.

i even updated the BIOS, but none of these worked.

Did someone has an idea that would help ?

Thanks

---

### Post by moster on 2009-07-27
If you can select in your bios boot from usb then you are ok. It can say USB disk or something similar.

I will tell you how I do it. Format your USB stick to fat32. Download Ubuntu ISO and get this prog [http://unetbootin.sourceforge.net/]("http://unetbootin.sourceforge.net/") Just give ISO to that program and he will make your boot USB stick and copy files from ISO.

If you under linux and you do not know how to make that program to work. Go to terminal and in right directory where you download it and type ```
sudo a+x unetbootin-linux-356
``` It will give you rights for running that program. Now just double click on it and select run. Wish you luck :D

---

### Post by maxxtwayne on 2009-07-27
thanks.

Tried it but same result.

---

### Post by moster on 2009-07-28
I forgot one little thing. Damn. Your partition on stick must be boot. In gparted right click on partition , select manage flags and check "boot".

Now, to be sure check again what unetbootin did. Sometimes he do not copy all the files on USB stick. You can actually see that is smaller then Ubuntu ISO image.

It must work.

---

### Post by maxxtwayne on 2009-07-28
It works !

Thanks to you Moster, it works.

Well, it wasn't what you said (i already got the boot flag) but you put me on the right way ...
In Gparted, i saw 2 flags on my USB Key, boot and lba.

I was surprised to see lba, removed it, and magic, it worked.

Thanks again for your help !

---

### Post by moster on 2009-07-28
I am glad you made it :)

---

