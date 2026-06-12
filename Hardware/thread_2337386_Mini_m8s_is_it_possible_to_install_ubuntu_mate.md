---
title: "Mini m8s: is it possible to install ubuntu mate?"
date: 2016-09-17
forum: Hardware
---

### Post by erotavlas on 2016-09-17
Hi,
I have a mini m8s device with android on board and I would like to install ubuntu mate or lubuntu instead. The SOC is an amlogic s905 which is an arm v8 64 bit CPU the same of odroid c2 while it is different from raspberry pi 3 (supported by ubuntu mate) even if both are arm v8 64 bit.
Is it possible? Do you have any suggestion?

Thank

---

### Post by mikewhatever on 2016-09-17
It's not impossible, but somewhat harder then on an intel/amd based device. ARM devices require specially crafted images, here is one: [http://freaktab.com/forum/tv-player-support/amlogic-based-tv-players/s905/beelink-ac/568654-minimx-s905-ubuntu-16-04-64bits-with-kodi-and-x-on-sdcard](http://freaktab.com/forum/tv-player-support/amlogic-based-tv-players/s905/beelink-ac/568654-minimx-s905-ubuntu-16-04-64bits-with-kodi-and-x-on-sdcard). ...and by the way, it was very easy to find, you should try searching.

---

### Post by erotavlas on 2016-09-17
> **mikewhatever said:**
> It's not impossible, but somewhat harder then on an intel/amd based device. ARM devices require specially crafted images, here is one: [http://freaktab.com/forum/tv-player-support/amlogic-based-tv-players/s905/beelink-ac/568654-minimx-s905-ubuntu-16-04-64bits-with-kodi-and-x-on-sdcard](http://freaktab.com/forum/tv-player-support/amlogic-based-tv-players/s905/beelink-ac/568654-minimx-s905-ubuntu-16-04-64bits-with-kodi-and-x-on-sdcard). ...and by the way, it was very easy to find, you should try searching.

Yes, I already found such solution. I would like to know if there was any official way.
Thank you

---

### Post by sukanime on 2016-09-17
Hi...
as far i know, there is no official way.

i will order Mini M8S , because i want to try to install Ubuntu Mate, and i will using this tutorial:
1. [http://freaktab.com/forum/tv-player-support/amlogic-based-tv-players/s905/tronsmart-ac/firmware-roms-tools-at/565449-running-linux-from-sd-card-or-usb-flash-drive-using-balbes150-method-and-files/](http://freaktab.com/forum/tv-player-support/amlogic-based-tv-players/s905/tronsmart-ac/firmware-roms-tools-at/565449-running-linux-from-sd-card-or-usb-flash-drive-using-balbes150-method-and-files/)
2. [http://forum.armbian.com/index.php/topic/1143-armbian-for-amlogic-s905/page-2#entry11747](http://forum.armbian.com/index.php/topic/1143-armbian-for-amlogic-s905/page-2#entry11747)

if you manage to install Ubuntu Mate, please share in here...
i will using Mini M8S for My Web Apps, it's will runing Lighttpd with PHP and Firefox.
i already using Raspberry Pi 3 but it's not comfortable for me, and i hope Mini M8S will much better.

Thanks...

---

### Post by sukanime on 2016-09-24
Hi, i just get Mini M8S.

I have try  ubuntu_multi_dtb_v3_20160625.img from [http://freaktab.com/forum/tv-player-support/amlogic-based-tv-players/s905/tronsmart-ac/firmware-roms-tools-at/565449-running-linux-from-sd-card-or-usb-flash-drive-using-balbes150-method-and-files/](http://freaktab.com/forum/tv-player-support/amlogic-based-tv-players/s905/tronsmart-ac/firmware-roms-tools-at/565449-running-linux-from-sd-card-or-usb-flash-drive-using-balbes150-method-and-files/)
I can run Ubuntu Mate, but Wifi not working, there is no module driver for RTL8723BS
and my Logitech MK260 Keyboard and Mouse not working.

Then i try Armbian ( Armbian_5.20_Vegas95_Ubuntu_xenial_3.14.79_desktop_20160922.img ) from here [http://forum.armbian.com/index.php/topic/1143-armbian-for-amlogic-s905/](http://forum.armbian.com/index.php/topic/1143-armbian-for-amlogic-s905/)
Wifi not working, no module driver.


I try LibreELEC 7.0.2.007 from here [7.0.2.007 build for S905 | LibreELEC]("https://forum.libreelec.tv/thread-1497.html") , wifi work and my logitech mk260 work, and remote work too...

i will try to solved the Armbian or Ubuntu Mate Problem....

---

### Post by sukanime on 2016-10-07
Thanks God....

after playing with Ubuntu Mate for Odroid C2, and with the help in forum Armbian and Freaktab.
i can make my Mini M8S to install Ubuntu Mate 16.04, its have Mali Accelerated X11, VLC with XCB, Sound and Wifi.

what i do is, compile the new kernel based on amlogic kernel source, with modification to make the AML M8 Sound card and Realtek RTL8723BS WiFi & BT chips to work.
and using MiniMX Ubuntu from Koxx in forum freaktab ( [http://freaktab.com/forum/tv-player-support/amlogic-based-tv-players/s905/beelink-ac/568654-minimx-s905-ubuntu-16-04-64bits-with-kodi-and-x-on-sdcard/](http://freaktab.com/forum/tv-player-support/amlogic-based-tv-players/s905/beelink-ac/568654-minimx-s905-ubuntu-16-04-64bits-with-kodi-and-x-on-sdcard/) )

you can see the screenshot in attachment.

---

### Post by erotavlas on 2017-09-03
> **sukanime said:**
> Thanks God....

after playing with Ubuntu Mate for Odroid C2, and with the help in forum Armbian and Freaktab.
i can make my Mini M8S to install Ubuntu Mate 16.04, its have Mali Accelerated X11, VLC with XCB, Sound and Wifi.

what i do is, compile the new kernel based on amlogic kernel source, with modification to make the AML M8 Sound card and Realtek RTL8723BS WiFi & BT chips to work.
and using MiniMX Ubuntu from Koxx in forum freaktab ( [http://freaktab.com/forum/tv-player-support/amlogic-based-tv-players/s905/beelink-ac/568654-minimx-s905-ubuntu-16-04-64bits-with-kodi-and-x-on-sdcard/](http://freaktab.com/forum/tv-player-support/amlogic-based-tv-players/s905/beelink-ac/568654-minimx-s905-ubuntu-16-04-64bits-with-kodi-and-x-on-sdcard/) )

you can see the screenshot in attachment.

Hi,
after almost an year, is there any update about ubuntu mate 16.04 with all stuff working?

---

### Post by sukanime on 2017-09-03
> **erotavlas said:**
> Hi,
after almost an year, is there any update about ubuntu mate 16.04 with all stuff working?

Hmm, i don't know with "All suff working".
Mini M8S is Android TV Box, so the Product Maker not release the Ubuntu Mate.
The best one to release Ubuntu Mate for AMLogic S905 is Odroid for Odroid C2, so you can follow and read release note from here [http://odroid.com/dokuwiki/doku.php?id=en:c2_release_linux_ubuntu](http://odroid.com/dokuwiki/doku.php?id=en:c2_release_linux_ubuntu)

After my post above, i just upgrade from Odroid C2 based Ubuntu Mate 16.04 to Ubuntu Mate 16.04.2 ( v2.3 ) , its more stable, but no Kodi with HW Video Decoder.
I just change the "Core System" but still use the same Kernel.

I hope you can understand.

FYI, I use my Mini M8S for my main computer, i use it every day, turn it on almost for 24/7.
Mostly for Routing my Internet to my TPLink Hotspot and for downloading alot of youtube video with youtube-dl
Using for browsing, and watch movie with VLC.

---

### Post by erotavlas on 2017-09-04
> **sukanime said:**
> Hmm, i don't know with "All suff working".
Mini M8S is Android TV Box, so the Product Maker not release the Ubuntu Mate.
The best one to release Ubuntu Mate for AMLogic S905 is Odroid for Odroid C2, so you can follow and read release note from here [http://odroid.com/dokuwiki/doku.php?id=en:c2_release_linux_ubuntu](http://odroid.com/dokuwiki/doku.php?id=en:c2_release_linux_ubuntu)

After my post above, i just upgrade from Odroid C2 based Ubuntu Mate 16.04 to Ubuntu Mate 16.04.2 ( v2.3 ) , its more stable, but no Kodi with HW Video Decoder.
I just change the "Core System" but still use the same Kernel.

I hope you can understand.

FYI, I use my Mini M8S for my main computer, i use it every day, turn it on almost for 24/7.
Mostly for Routing my Internet to my TPLink Hotspot and for downloading alot of youtube video with youtube-dl
Using for browsing, and watch movie with VLC.

First of all, thank you very much for your fast reply. Last year, I read about some features that did not work. I read [here]("https://wiki.odroid.com/odroid-c2/os_images/ubuntu/v2.3") about v2.3 of odroid C2 and apart from Kodi support, it seems nice image. 
I want to use my device as small server especially for nextcloud and local network storage. Do you recommend this usage? Or it is better a different OS?
Thank you

---

### Post by sukanime on 2017-09-04
> **erotavlas said:**
> First of all, thank you very much for your fast reply. Last year, I read about some features that did not work. I read [here]("https://wiki.odroid.com/odroid-c2/os_images/ubuntu/v2.3") about v2.3 of odroid C2 and apart from Kodi support, it seems nice image. 
I want to use my device as small server especially for nextcloud and local network storage. Do you recommend this usage? Or it is better a different OS?
Thank you

I don't know about nextcloud.
But i use my Mini M8S as FTP Bases Storage, i run ftp server for sharing and uploading in my local network.
i use USB External HDD with 2TB and install Ubuntu Mate on the USB Eksternal HDD, it make Ubuntu Mate much faster too.
i use ftp server because is lighweight and much simple compared to samba.
i put MiniDLNA to in Mini M8S.

i have TPLink MR3220 runing OpenWRT with 3TB External HDD running as Torrent downloader, ftp server and MiniDLNA.
So, this Mini M8S its much better the that.

I think Ubuntu Mate is good for you.

---

### Post by erotavlas on 2017-09-04
> **sukanime said:**
> I don't know about nextcloud.
But i use my Mini M8S as FTP Bases Storage, i run ftp server for sharing and uploading in my local network.
i use USB External HDD with 2TB and install Ubuntu Mate on the USB Eksternal HDD, it make Ubuntu Mate much faster too.
i use ftp server because is lighweight and much simple compared to samba.
i put MiniDLNA to in Mini M8S.

i have TPLink MR3220 runing OpenWRT with 3TB External HDD running as Torrent downloader, ftp server and MiniDLNA.
So, this Mini M8S its much better the that.

I think Ubuntu Mate is good for you.

[NextCloud]("https://en.wikipedia.org/wiki/Nextcloud") is self hosted cloud and provides more or less the same features of FTP with more added values (encryption, standard web port instead of FTP port for firewall, authentication log, etc.). NextCloud is a fork of OwnCloud and between them there is the same ratio of LibreOffice and OpenOffice.
So if Mini M8S works well for you, it should work well also for me. [NextCloud box]("https://nextcloud.com/box/") can be made with odroid c2.
Thank you

---

