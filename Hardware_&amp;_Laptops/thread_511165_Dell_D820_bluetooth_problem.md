---
title: "Dell D820 bluetooth problem"
date: 2007-07-27
forum: Hardware &amp; Laptops
---

### Post by virtualj on 2007-07-27
Hi,

I am having trouble installing my build in bluetooth on my Dell Latitude D820.
I followed the [guide]("https://help.ubuntu.com/community/BluetoothSetup") in the ubuntu documentation but when i try hcitool dev to list my bluetooth devices I get an empty list.
> 
~$ sudo hcitool dev
Devices:

Bluetooth is enabled in the bios and it used to work in windows.
I allso found [this post]("http://www.len.ro/work/tools/ubuntu-feisty-fawn-on-a-dell-latitude-d820/use-the-bluetooth-port-with-ubuntu") of someone with a D820 and he uses the same steps as the guide, but with him it works.

Annyone have the same problem or knows what the problem can be?

thanks

---

### Post by noonereallycares on 2007-08-10
Check out [http://ubuntuforums.org/showthread.php?p=2308248](http://ubuntuforums.org/showthread.php?p=2308248)

---

### Post by virtualj on 2007-08-20
> **noonereallycares said:**
> Check out [http://ubuntuforums.org/showthread.php?p=2308248](http://ubuntuforums.org/showthread.php?p=2308248)

Thanks, that thread helped me a lot.
The problem was the old Vista driver for bluetooth.

---

