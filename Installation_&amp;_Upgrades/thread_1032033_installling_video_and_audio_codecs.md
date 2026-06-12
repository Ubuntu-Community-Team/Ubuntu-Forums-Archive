---
title: "installling video and audio codecs"
date: 2009-01-05
forum: Installation &amp; Upgrades
---

### Post by thegamer on 2009-01-05
Hi..
I am new to ubuntu.:confused:I can't play video and audio files other than wav in my ubuntu system.Error prompt tells me about the need of extra codecs.
I have no internet conection at my place.I downloaded the gz packages but can't figure how to install it.

Please help....:confused::confused:

---

### Post by tuxxy on 2009-01-05
A lot of codecs are included in the ubuntu-restricted-extras package, this should solve the issue - if you have Internet open terminal and enter this command

```
sudo apt-get install ubuntu-restricted-extras
```Heres a http link to the same package

[http://packages.ubuntu.com/intrepid/ubuntu-restricted-extras](http://packages.ubuntu.com/intrepid/ubuntu-restricted-extras)

---

### Post by thegamer on 2009-01-06
> **tuxxy said:**
> A lot of codecs are included in the ubuntu-restricted-extras package, this should solve the issue - if you have Internet open terminal and enter this command

```
sudo apt-get install ubuntu-restricted-extras
```Heres a http link to the same package

[http://packages.ubuntu.com/intrepid/ubuntu-restricted-extras](http://packages.ubuntu.com/intrepid/ubuntu-restricted-extras)

Thanks Buddy,for that valuable bit of info.:P

But i think for doing so ,i would be needing an internet at my place,which i don't have....Can i download the package elsewhere and install in my pc

---

### Post by cariboo on 2009-01-06
You can go [here]("http://packages.ubuntu.com/intrepid/ubuntu-restricted-extras"), to download the packages in ubuntu-restricted-extras meta package. Once you have copied the files to your Ubuntu installation just double click on the a file, and gdebi will pop up and install it for you.

Jim

---

