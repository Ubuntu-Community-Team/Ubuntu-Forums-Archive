---
title: "guide to install G Link usb modem in UBUNTU 7.10"
date: 2008-12-27
forum: Installation &amp; Upgrades
---

### Post by ashokshrestha on 2008-12-27
Hello!!!
i have installed Ubuntu 7.10 in my pc. Now i want to use G link CDMA USB modem. can anyone provide me copmlete step by step guuide for installation

---

### Post by namdung on 2008-12-27
Firstly, what are u doing still using 7.10? Pls upgrade to Hardy 8.04.1 or Intrepid 8.10 immediately.

Hardy is LTS and its next version 8.04.2 is out in 1/1/2009. Intrepid has more features but may also have more bugs.

These new versions will definitely have support for more & newer hardware.

Ashok, pls avoid cross posting.
The other post : [http://ubuntuforums.org/showthread.php?t=1021168](http://ubuntuforums.org/showthread.php?t=1021168)

Can anyone pls merge the two threads?

---

### Post by balaknair on 2008-12-27
I can't promise this will work in Gutsy, but it's worth a shot.

Open a terminal and type in 

```
wvdialconf
```

If your modem is supported by Gutsy, wvdial should detect it. Thereafter you can use either wvdialconf to configure it via the command line, or you can use Gnome-PPP(sudo apt-get install gnome-ppp) to configure it with a GUI.


If wvdialconf doesn't find your modem, I suggest you upgrade to either Ubuntu 8.04 or 8.10, since both these versions have much better hardware support for USB devices, especially 8.10. Ubuntu 7.10 and older versions do not load the USB kernel modules automatically. I know for sure that Intrepid can handle most USB CDMA modems out of the box.

You can download 8.04 or 8.10 or request a free 8.10 CD here
[http://www.ubuntu.com/getubuntu](http://www.ubuntu.com/getubuntu)


If you want to stick with 7.10, I suggest you read these pages

[https://help.ubuntu.com/7.10/internet/C/modems-adsl-usb.html](https://help.ubuntu.com/7.10/internet/C/modems-adsl-usb.html)

[http://wiki.fossnepal.org/index.php?title=FAQ#Run_a_USB_CDMA_modem_in_Linux](http://wiki.fossnepal.org/index.php?title=FAQ#Run_a_USB_CDMA_modem_in_Linux)

You might also want to check this post

[http://ubuntuforums.org/showpost.php?p=6221563&postcount=7](http://ubuntuforums.org/showpost.php?p=6221563&postcount=7)

though he got it working on 8.04.

I did find this for 7.10

[http://abish.wordpress.com/2008/04/18/using-cdma-wireless-modem-in-ubuntu/](http://abish.wordpress.com/2008/04/18/using-cdma-wireless-modem-in-ubuntu/)

---

