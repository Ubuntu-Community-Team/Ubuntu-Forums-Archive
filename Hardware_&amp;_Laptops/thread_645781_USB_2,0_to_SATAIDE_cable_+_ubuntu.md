---
title: "USB 2,0 to SATA/IDE cable + ubuntu"
date: 2007-12-20
forum: Hardware &amp; Laptops
---

### Post by Salazar420 on 2007-12-20
So, here's the thing. I have a could of 400GB sata hardrives (seagate), but I didn't have a means of hooking them up ( no sata ). So now I bought a USB 2.0 to SATA/IDE cable. I've noticed that all works perfectly without the installation of drivers when using Windows XP (figures), but when I'm using ubuntu, it doesn't seem to register, be it my laptop of my desktop. I'm just wondering, did I buy this for nothing. Actually, I bought two, both different brands and styles. Only tested one. Will see how the other goes.

---

### Post by Salazar420 on 2007-12-20
So, neither are working. This is becoming a problem because I do not wish to dual boot windows and ubuntu just to utilize the capacities at my disposal (strictly ubuntu by choice), and I don't want to sell the drives. If there are secluded or shrouded drivers available that I'm not aware of, links would be awesome, but I googled to no avail. I'll list the links to the devices I purchased:

[http://www.newegg.com/Product/Product.asp?Item=N82E16812156014]("http://www.newegg.com/Product/Product.asp?Item=N82E16812156014")

[http://www.newegg.com/Product/Product.asp?Item=N82E16812189169]("http://www.newegg.com/Product/Product.asp?Item=N82E16812189169")

Any assistance, advice or knowledge on this matter is greatly appreciated. Will check back.

---

### Post by Phurious on 2007-12-20
Out of curiosity, how are the drives formatted?  NTFS?  EXT3?  Once you attach the drive via USB, I would run GParted to see if the OS may have actually recognized the drive, but not mounted it.

---

### Post by Salazar420 on 2007-12-21
The drives are NTFS. I will try the Gparted, though I'm not sure what it is yet -- manual pages should be pretty explanatory. As a footnote, I have got ubuntu to mount the drives now (though not very consistently); however, I can't seem to format it with mkfs.****, and after deleting all of the contents, there is a particular folder that won't budge, no matter the file permissions or my status as root user. The contents of the drive were an XP variant, and the particular directory that won't budge is -- wouldn't ya figure -- Documents and Settings. Also, I can't seem to access my bios, and although this is a seperate issue in it's own -- probably a pretty outstanding one -- it does relate to the issue at hand, because I was wondering if I can boot from an external usb device. When I try to access my drivers it does something pertaining to my broadcom wireless network card, mentions DHCP, attempts some sort of connection, lists my mac address, etc, and fails. I've only managed to access my bios once since having bought the laptop, using (F12), but now it just does the steps listed therein. Anyway, feedback welcomed. I'll be checking back soon. Thanks for the input thus far.

Oh yeah, is there any quick explanation of how to find identifiers for all of the devices listed in /dev? For instance, say I were wanting to find my camera device, or say a usb flash drive, is there a way of finding it other than, say, lsusb?

---

### Post by Phurious on 2007-12-21
I am fairly new to this also, but I remember when I was working with my fstab file I used the following command to get a list of drives:
```
fdisk -l
```

Hope it works for you!

---

