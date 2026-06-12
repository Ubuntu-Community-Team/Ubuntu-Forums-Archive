---
title: "Asus A9RP sound problem"
date: 2007-01-03
forum: Hardware &amp; Laptops
---

### Post by _Q_ on 2007-01-03
Greetings to everyone,...

I've turned to this forum, as a last resort, after extenssive search of net and self-tryed methods ...

Problem : very weak sound on the 3.5mm jack output
Using : Asus A9RP laptop (sound card : HDA ATI SB)
Running : Ubuntu Edgy

Alsa configuration reports using Realtek ALC 681 hardware
OSS mixer reports using Realtek ALC 660 mixer

In the mixer (using ALSA) , it's only possible to choose Headphones and Front switches,
when the Headphones switch is turned off, there is no sound...
When it's turn on there is, but it's very weak...
Built-in speakers work fine... and loud...

I noticed that on one other laptop (IBM R40), there are more switches in the mixer, like... headphone sense, line jack sense, external amp.....

Is this a crippled hardware problem , or ? ... Could it be compensated somehow ?
The only alternative I know atm. is buying a PCMCIA sound card (Creative) which is around 150 EU.... :neutral: 

any suggestion would be helpful, thnx !!

---

### Post by amirms on 2007-06-17
Ubuntu 6.10
ASUS A9Rp Laptop
1.8 Ghz Celeron,ATI Radeon Xpress 200M,ZyDAS 1211B Wireless,Realtek HDA Audio

Every thing is detected but WIRELSS,Audio(Built in speakers are OK but the 3.5 mm jack has weak sound),Modem

I could solve audio and wireless problems:D, users follow the instructions bellow:

1-Download and install kernel sources, I copied it to /usr/src/

2-Get this patch for audio and decompress to your kernel source root folder, mine is:/usr/src/linux-2.6.21-5
   [ftp://ftp.alsa-project.org/pub/kernel-patches/alsa-git-2007-05-03.patch.gz](ftp://ftp.alsa-project.org/pub/kernel-patches/alsa-git-2007-05-03.patch.gz)
   so, you should have alsa-git-2007-05-03.patch in your linux kernel source folder

3-Open console and run:
   patch -p1 <alsa-git-2007-05-03.patch
   OK, Now kernel is patched for audio, we proceed to wireless.

4-Say your kernel source folder is like mine, /usr/src/linux-2.6.21-5, open this file:
/usr/src/linux-2.6.21-5/drivers/net/wireless/zd_usb.c and add this line to the ZD1211-B section:
  { USB_DEVICE(0x0b05, 0x171b), .driver_info = DEVICE_ZD1211B }, 
  Save the file.

5-Now you should download this file and decompress the content into /lib/firmware/zd1211(if this directory does not exist, create it)
  [http://sourceforge.net/project/showfiles.php?group_id=129083](http://sourceforge.net/project/showfiles.php?group_id=129083)

OK,we are almost done!Now, you should compile the new kernel and install it.You can open /usr/src/linux-2.6.21-5/README.txt to find out how to do so. what I did:

cd /usr/src/linux-2.6.21-5
Make oldconfig
Make
Make modules_install
Make install

If using GRUB, you are done!Reboot and enjoy:)
If using LILO, reinstall LILO and reboot and enjoy!

The above procedures should work with other versions of ubuntu as well as other distributions. One of my friends has done it in OpenSUSE 10.2 without any problem.

---

### Post by raul_ on 2007-07-29
```
 [root@apolo linux-2.6.22-ARCH]# patch -p1 <alsa-git-2007-05-03.patch
can't find file to patch at input line 5
Perhaps you used the wrong -p or --strip option?
The text leading up to this was:
--------------------------
|diff --git a/Documentation/sound/alsa/ALSA-Configuration.txt b/Documentation/sound/alsa/ALSA-Configuration.txt
|index 73e9a17..d18e12b 100644
|--- a/Documentation/sound/alsa/ALSA-Configuration.txt
|+++ b/Documentation/sound/alsa/ALSA-Configuration.txt

```

:(

Using Arch

---

