---
title: "Will it work with Lenovo ThinkBook 16 G6 16 WUXGA Ryzen 5 7530U 16GB SSD512?"
date: 2024-10-10
forum: Hardware
---

### Post by doze5 on 2024-10-10
I'm  thinking about buying a new laptop. Will the latest ubuntu 24.04 LTS  work with Lenovo ThinkBook 16 G6 16 WUXGA Ryzen 5 7530U 16GB SSD512  (there is windows 11 pro as standard). I didn't find the laptop on the  list of compatible/certified with ubuntu, maybe because it's a new  laptop? Has anyone had the opportunity to test it? Has he read anything  about it? Fingerprint reader, sound?

[https://www.lenovo.com/us/en/p/laptops/thinkbook/thinkbook-series/lenovo-thinkbook-16-gen-6-16-inch-amd/len101b0032](https://www.lenovo.com/us/en/p/laptops/thinkbook/thinkbook-series/lenovo-thinkbook-16-gen-6-16-inch-amd/len101b0032)

---

### Post by oldfred on 2024-10-10
You have to just try it.
Download the lastest 24.04.1 ISO and create a live installer and boot in live mode. You should then be able to test everything. While latest LTS long term support version is normally suggested, but if too new, then you need to install the latest version with only 9 month support. 

24.10 will be out the end of October but the beta version works. If you try 24.10, be sure to report any issues/bugs that you find, so the can add last minute fixes.

[https://ubuntu.com/tutorials/install-ubuntu-desktop#1-overview](https://ubuntu.com/tutorials/install-ubuntu-desktop#1-overview)

---

### Post by doze5 on 2024-10-11
I  bought it today and tomorrow, that is, Saturday, I should have it in a  parcel machine. Here is an interesting link with almost the same laptop,  I guess only the processor is different, because it is intel. Maybe it  will be useful for ubuntu developers or other forum users.

[https://linux-hardware.org/?probe=3d2abf7e0d](https://linux-hardware.org/?probe=3d2abf7e0d)

And there is:
[TABLE="class: tbl dev_info highlight"]
[TR]
[TD="class: vendor"]"Shenzhen Goodix Technology Co.,Ltd.[/TD]
[TD="class: device"]FingerPrint[/TD]
[TD="class: type"][/TD]
[TD="class: driver"]-[/TD]
[TD="class: failed pointer, align: center"][failed]("https://linux-hardware.org/?id=usb:27c6-550a")"[/TD]
[/TR]
[/TABLE]

but someone wrote:
"i downloaded the goodix driver from lenovo website" - works

---

### Post by doze5 on 2024-10-12
On  Ubuntu 24.04.1, practically everything works from the moment you  install it. I mean turning the sound up and down, turning the keyboard  backlight, changing the screen brightness - everything works from the  keyboard and function keys. For the fingerprint reader I had to install a  driver that I downloaded to HDD - libfprint-2-tod-goodix_amd64.deb,  i.e. goodix driver from lenovo website. Even the shortcut to the  calculator that is on the keyboard works. 
Of course, I have to test more, because maybe something else will come out.

The exact model of my laptop is the **Lenovo** **ThinkBook 16 G6 ABP**. There  are two things to keep in mind. Bios update only from under windows and  therefore you have to run it, because it is worth uploading the latest  bios. Then it is worth disabling BitLocker in windows to make installing  ubuntu easier.

---

