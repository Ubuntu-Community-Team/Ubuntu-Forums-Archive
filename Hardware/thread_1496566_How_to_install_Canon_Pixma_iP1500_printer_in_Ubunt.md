---
title: "How to install Canon Pixma iP1500 printer in Ubuntu 10.04"
date: 2010-05-29
forum: Hardware
---

### Post by richard24680 on 2010-05-29
Printer Canon Pixma iP1500 does not work in Ubuntu 10.04

I have tried many solutions in the web but all do not work in Ubuntu 10.04.
Printer install but does not print at all.


there are many people with this problem for what I can see on the WEB.

Please, does anybody can guide How to install Canon Pixma iP1500 printer in Ubuntu 10.04.

thanks,
Richard

---

### Post by frankb_1602 on 2010-05-29
I also had these problems, and I found the solution on the German Ubuntuusers wiki ([http://wiki.ubuntuusers.de/Canon-Drucker](http://wiki.ubuntuusers.de/Canon-Drucker), especially [http://wiki.ubuntuusers.de/Canon-Drucker?highlight=ip90%20canon#Links-setzen](http://wiki.ubuntuusers.de/Canon-Drucker?highlight=ip90%20canon#Links-setzen) - sorry, that article is in German only): The problem is that the PNG-DLL is now located in /lib instead of /usr/lib as it was obviously until Ubuntu 9.10.  

 Start as described here: [https://wiki.ubuntu.com/CanonPixmaIP1500](https://wiki.ubuntu.com/CanonPixmaIP1500). Alien will give you some error messages, but they did not have any adverse effect for me:

```
wget http://software.canon-europe.com/files/soft22415/software/iP1500Linux.tar.gz
tar -xzf iP1500Linux.tar.gz
sudo apt-get install alien
cd iP1500
sudo alien *i386.rpm
sudo dpkg -i *.deb
cd /usr/lib
sudo ln -s libpng12.so.0 libpng.so.2
sudo ln -s libtiff.so.4 libtiff.so.3
sudo ln -s libxml2.so.2 libxml.so.1
```That was step 6; I omitted the last ones. You may proceed with the remaining steps later, I think.

Now, find the name of the printer filter:
```
cd  /usr/local/bin
ls -l
```You will get an output like this one:
```

 [COLOR=Black][FONT=DejaVu Sans]-rwxr-xr-x 1 root root   3200 2005-04-08 09:11 bjcmdpixmaip1500[/FONT]
 [/COLOR][COLOR=Black][FONT=DejaVu Sans]-rwxr-xr-x 1 root root  13740 2005-04-08 09:11 bjcups[/FONT]
 [/COLOR][COLOR=Black][FONT=DejaVu Sans]-rwxr-xr-x 1 root root  42316 2005-04-08 09:11 bjcupsmon[/FONT]
 [/COLOR][COLOR=Black][FONT=DejaVu Sans]-rwxr-xr-x 1 root root  62604 2005-04-08 09:11 bjfilterpixmaip1500[/FONT]
 [/COLOR][COLOR=Black][FONT=DejaVu Sans]-rwxr-xr-x 1 root root  43884 2005-04-08 09:11 lgmonpixmaip1500[/FONT]
 [/COLOR][COLOR=Black][FONT=DejaVu Sans]-rwxr-xr-x 1 root root   2236 2005-04-08 09:11 pixmaip1500_ps[/FONT]
 [/COLOR][COLOR=Black][FONT=DejaVu Sans]-rwxr-xr-x 1 root root    374 2005-04-08 09:11 pixmaip1500_raw[/FONT]
 [/COLOR][COLOR=Black][FONT=DejaVu Sans]-rwxr-xr-x 1 root root 348844 2005-04-08 09:11 printuipixmaip1500[/FONT]
 [/COLOR][COLOR=Black][FONT=DejaVu Sans]-rwxr-xr-x 1 root root  51820 2005-04-08 09:11 stsmonpixmaip1500[/FONT][/COLOR]
```The filter needed is "[FONT=DejaVu Sans]bjfilterpixmaip1500" (row 4).[/FONT]

Find the tiff and png-dll needed: 

```
ldd bjfilterpixmaip1500
```My output was[COLOR=Black]:
[/COLOR]```
[COLOR=Black][COLOR=#808080][FONT=DejaVu Sans][COLOR=Black]linux-gate.so.1 =>  (0x00fdd000)
libcnbpcmcm214.so => /usr/lib/libcnbpcmcm214.so (0x00d06000)
libcnbpess214.so => /usr/lib/libcnbpess214.so (0x00bad000)
libm.so.6 => /lib/tls/i686/cmov/libm.so.6 (0x00735000)
libdl.so.2 => /lib/tls/i686/cmov/libdl.so.2 (0x00db1000)
libtiff.so.3 => /usr/lib/libtiff.so.3 (0x009b1000)
libpng.so.2 => not found
libcnbpcnclapi214.so => /usr/lib/libcnbpcnclapi214.so (0x007e2000)
libcnbpcnclbjcmd214.so => /usr/lib/libcnbpcnclbjcmd214.so (0x00c5f000)
libcnbpcnclui214.so => /usr/lib/libcnbpcnclui214.so (0x00a11000)
libpopt.so.0 => /lib/libpopt.so.0 (0x00134000)
libc.so.6 => /lib/tls/i686/cmov/libc.so.6 (0x0013f000)
libpthread.so.0 => /lib/tls/i686/cmov/libpthread.so.0 (0x00e47000)/lib/ld-linux.so.2 (0x00d51000)
libjpeg.so.62 => /usr/lib/libjpeg.so.62 (0x00328000)
libz.so.1 => /lib/libz.so.1 (0x00110000)[/COLOR][/FONT][/COLOR][/COLOR]
```[COLOR=Black][COLOR=#808080][FONT=DejaVu Sans]

[/FONT][/COLOR][/COLOR][COLOR=Black][COLOR=#808080][FONT=DejaVu Sans][COLOR=Black]As you can see in row 7 of the output, the driver libpng.so.2 is missing. You can find the missing dll files by entering
[/COLOR][/FONT][/COLOR][/COLOR]```
/usr/lib$ ls -l libtiff* libpng* 
```I got 
```
lrwxrwxrwx 1 root root     13 2010-05-24 16:10 libpng.so.2 -> libpng12.so.0     
lrwxrwxrwx 1 root root     12 2009-03-08 15:06 libtiff.so.3 -> libtiff.so.4
lrwxrwxrwx 1 root root     16 2010-05-01 11:37 libtiff.so.4 -> libtiff.so.4.3.2
-rw-r--r-- 1 root root 366580 2010-01-22 13:14 libtiff.so.4.3.2
```Well, we're almost done - the first row shows us the wrong link. Just go to the /lib directory and create a symbolic link to the dll needed:

```
cd /lib
sudo ln -s libpng12.so.0 libpng.so.2
sudo ldconfig
```That's all. The printer is installed. Go to System - Administration - Printing, and add the printer. The Pixma iP 1500 driver should be listed, and printing should work, at least after

```
sudo  /etc/init.d/cups restart
```If you connected the printer with your router (like me, I use a Fritz!Box router, its USB port is connected to the printer), you may choose in the relevant dialogue Appsocket/HP -> JetDirekt, and fill in 
[FONT=DejaVu Sans]    Host: 192.168.178.1 
    Port: 9100
Choose the relevant printer and print.

Last remarks: I am not an Ubuntu geek, and it is quite possible that there is a shorter or more elegant way to install the iP1500 printer. However, that procedure worked for me, an I hope it will help you, too. :)
[/FONT]

---

### Post by Dadaisme on 2011-06-15
Thanks for the tutorial; it worked like a charm on Linux Mint 10 (Ubuntu version).

Anyway, I managed to find out how to get more printing options once the driver is installed (Grayscale printing option, as well as quality options--economy,standard etc.) . (here)

You need to edit the canonpixmaip1500.ppd file:
```

cd /usr/share/cups/model/
sudo cp canonpixmaip1500.ppd canonpixmaip1500.ppd.install
gksudo gedit canonpixmaip1500.ppd

```change the ```
*NickName: quot;Canon PIXMA iP1500 Ver.2.50
``` to something like ```
*NickName: quot;Canon PIXMA iP1500 Ver.2.50 Grayscale
```and replace this:

```

* OpenUI *Resolution/Output Resolution: PickOne
* DefaultResolution: 600
* Resolution 600/600 dpi: quot;lt;lt;/HWResolution[600 600]gt;gt;setpagedevicequot;
* CloseUI: *Resolution

```with this:

```

*OpenUI *CNQuality/Quality: PickOne
*DefaultCNQuality: 3
*CNQuality 2/High: quot;2quot;
*CNQuality 3/Normal: quot;3quot;
*CNQuality 4/Standard: quot;4quot;
*CNQuality 5/Economy: quot;5quot;
*CloseUI: *CNQuality

*OpenUI *Resolution/Output Resolution: PickOne
*DefaultResolution: 600
*Resolution 300/300 dpi: quot;lt;lt;/HWResolution[300 300]gt;gt;setpagedevicequot;
*Resolution 600/600 dpi: quot;lt;lt;/HWResolution[600 600]gt;gt;setpagedevicequot;
*Resolution 1200/1200 dpi: quot;lt;lt;/HWResolution[1200 1200]gt;gt;setpagedevicequot;
*CloseUI: *Resolution

*OpenGroup: Color Adjustment

*OpenUI *CNGrayscale/Grayscale: PickOne
*DefaultCNGrayscale: true
*CNGrayscale false/Off: quot;falsequot;
*CNGrayscale true/On: quot;truequot;
*CloseUI: *CNGrayscale

*OpenUI *CNDensity/Density: PickOne
*DefaultCNDensity: 0
*CNDensity -50/-50: quot;lt;lt;/CNDensity(-50)gt;gt;setpagedevicequot;
*CNDensity -40/-40: quot;lt;lt;/CNDensity(-40)gt;gt;setpagedevicequot;
*CNDensity -30/-30: quot;lt;lt;/CNDensity(-30)gt;gt;setpagedevicequot;
*CNDensity -20/-20: quot;lt;lt;/CNDensity(-20)gt;gt;setpagedevicequot;
*CNDensity -10/-10: quot;lt;lt;/CNDensity(-10)gt;gt;setpagedevicequot;
*CNDensity 0/0: quot;lt;lt;/CNDensity(0)gt;gt;setpagedevicequot;
*CNDensity 10/10: quot;lt;lt;/CNDensity(10)gt;gt;setpagedevicequot;
*CNDensity 20/20: quot;lt;lt;/CNDensity(20)gt;gt;setpagedevicequot;
*CNDensity 30/30: quot;lt;lt;/CNDensity(30)gt;gt;setpagedevicequot;
*CNDensity 40/40: quot;lt;lt;/CNDensity(40)gt;gt;setpagedevicequot;
*CNDensity 50/50: quot;lt;lt;/CNDensity(50)gt;gt;setpagedevicequot;
*CloseUI: *CNDensity

*OpenUI *CNGamma/Gamma Adjustment: PickOne
*DefaultCNGamma: 1.8
*CNGamma 1.4/1.4: quot;lt;lt;/CNGamma(1.4)gt;gt;setpagedevicequot;
*CNGamma 1.8/1.8: quot;lt;lt;/CNGamma(1.8)gt;gt;setpagedevicequot;
*CNGamma 2.2/2.2: quot;lt;lt;/CNGamma(2.2)gt;gt;setpagedevicequot;
*CloseUI: *CNRenderIntent

*OpenUI *CNBalanceC/Balance Cyan: PickOne
*DefaultCNBalanceC: 0
*CNBalanceC -50/-50: quot;lt;lt;/CNBalanceC(-50)gt;gt;setpagedevicequot;
*CNBalanceC -40/-40: quot;lt;lt;/CNBalanceC(-40)gt;gt;setpagedevicequot;
*CNBalanceC -30/-30: quot;lt;lt;/CNBalanceC(-30)gt;gt;setpagedevicequot;
*CNBalanceC -20/-20: quot;lt;lt;/CNBalanceC(-20)gt;gt;setpagedevicequot;
*CNBalanceC -10/-10: quot;lt;lt;/CNBalanceC(-10)gt;gt;setpagedevicequot;
*CNBalanceC 0/0: quot;lt;lt;/CNBalanceC(0)gt;gt;setpagedevicequot;
*CNBalanceC 10/10: quot;lt;lt;/CNBalanceC(10)gt;gt;setpagedevicequot;
*CNBalanceC 20/20: quot;lt;lt;/CNBalanceC(20)gt;gt;setpagedevicequot;
*CNBalanceC 30/30: quot;lt;lt;/CNBalanceC(30)gt;gt;setpagedevicequot;
*CNBalanceC 40/40: quot;lt;lt;/CNBalanceC(40)gt;gt;setpagedevicequot;
*CNBalanceC 50/50: quot;lt;lt;/CNBalanceC(50)gt;gt;setpagedevicequot;
*CloseUI: *CNBalanceC

*OpenUI *CNBalanceM/Balance Magenta: PickOne
*DefaultCNBalanceM: 0
*CNBalanceM -50/-50: quot;lt;lt;/CNBalanceM(-50)gt;gt;setpagedevicequot;
*CNBalanceM -40/-40: quot;lt;lt;/CNBalanceM(-40)gt;gt;setpagedevicequot;
*CNBalanceM -30/-30: quot;lt;lt;/CNBalanceM(-30)gt;gt;setpagedevicequot;
*CNBalanceM -20/-20: quot;lt;lt;/CNBalanceM(-20)gt;gt;setpagedevicequot;
*CNBalanceM -10/-10: quot;lt;lt;/CNBalanceM(-10)gt;gt;setpagedevicequot;
*CNBalanceM 0/0: quot;lt;lt;/CNBalanceM(0)gt;gt;setpagedevicequot;
*CNBalanceM 10/10: quot;lt;lt;/CNBalanceM(10)gt;gt;setpagedevicequot;
*CNBalanceM 20/20: quot;lt;lt;/CNBalanceM(20)gt;gt;setpagedevicequot;
*CNBalanceM 30/30: quot;lt;lt;/CNBalanceM(30)gt;gt;setpagedevicequot;
*CNBalanceM 40/40: quot;lt;lt;/CNBalanceM(40)gt;gt;setpagedevicequot;
*CNBalanceM 50/50: quot;lt;lt;/CNBalanceM(50)gt;gt;setpagedevicequot;
*CloseUI: *CNBalanceM

*OpenUI *CNBalanceY/Balance Yellow: PickOne
*DefaultCNBalanceY: 0
*CNBalanceY -50/-50: quot;lt;lt;/CNBalanceY(-50)gt;gt;setpagedevicequot;
*CNBalanceY -40/-40: quot;lt;lt;/CNBalanceY(-40)gt;gt;setpagedevicequot;
*CNBalanceY -30/-30: quot;lt;lt;/CNBalanceY(-30)gt;gt;setpagedevicequot;
*CNBalanceY -20/-20: quot;lt;lt;/CNBalanceY(-20)gt;gt;setpagedevicequot;
*CNBalanceY -10/-10: quot;lt;lt;/CNBalanceY(-10)gt;gt;setpagedevicequot;
*CNBalanceY 0/0: quot;lt;lt;/CNBalanceY(0)gt;gt;setpagedevicequot;
*CNBalanceY 10/10: quot;lt;lt;/CNBalanceY(10)gt;gt;setpagedevicequot;
*CNBalanceY 20/20: quot;lt;lt;/CNBalanceY(20)gt;gt;setpagedevicequot;
*CNBalanceY 30/30: quot;lt;lt;/CNBalanceY(30)gt;gt;setpagedevicequot;
*CNBalanceY 40/40: quot;lt;lt;/CNBalanceY(40)gt;gt;setpagedevicequot;
*CNBalanceY 50/50: quot;lt;lt;/CNBalanceY(50)gt;gt;setpagedevicequot;
*CloseUI: *CNBalanceY

*OpenUI *CNBalanceK/Balance Black: PickOne
*DefaultCNBalanceK: 0
*CNBalanceK -50/-50: quot;lt;lt;/CNBalanceK(-50)gt;gt;setpagedevicequot;
*CNBalanceK -40/-40: quot;lt;lt;/CNBalanceK(-40)gt;gt;setpagedevicequot;
*CNBalanceK -30/-30: quot;lt;lt;/CNBalanceK(-30)gt;gt;setpagedevicequot;
*CNBalanceK -20/-20: quot;lt;lt;/CNBalanceK(-20)gt;gt;setpagedevicequot;
*CNBalanceK -10/-10: quot;lt;lt;/CNBalanceK(-10)gt;gt;setpagedevicequot;
*CNBalanceK 0/0: quot;lt;lt;/CNBalanceK(0)gt;gt;setpagedevicequot;
*CNBalanceK 10/10: quot;lt;lt;/CNBalanceK(10)gt;gt;setpagedevicequot;
*CNBalanceK 20/20: quot;lt;lt;/CNBalanceK(20)gt;gt;setpagedevicequot;
*CNBalanceK 30/30: quot;lt;lt;/CNBalanceK(30)gt;gt;setpagedevicequot;
*CNBalanceK 40/40: quot;lt;lt;/CNBalanceK(40)gt;gt;setpagedevicequot;
*CNBalanceK 50/50: quot;lt;lt;/CNBalanceK(50)gt;gt;setpagedevicequot;
*CloseUI: *CNBalanceK

*CloseGroup: Color Adjustment

```
Now add a new Canon printer with the new driver and set it as default.
Hope this helps.

---

