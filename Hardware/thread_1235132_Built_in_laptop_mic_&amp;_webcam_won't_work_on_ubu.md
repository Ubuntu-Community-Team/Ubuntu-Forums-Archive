---
title: "Built in laptop mic &amp; webcam won't work on ubuntu"
date: 2009-08-08
forum: Hardware
---

### Post by mikethedj4 on 2009-08-08
Well I have an Acer Aspire 5520-5912, with built in webcam (Acer CrystalEye Webcam) and mic, and my hardware in listed below.

Acer Aspire 5520-5912 (Where I bought it)
[http://www.walmart.com/catalog/product.do?product_id=7812646](http://www.walmart.com/catalog/product.do?product_id=7812646)

speed@ubuntu:~$ lspci
00:00.0 RAM memory: nVidia Corporation MCP67 Memory Controller (rev a2)
00:01.0 ISA bridge: nVidia Corporation MCP67 ISA Bridge (rev a2)
00:01.1 SMBus: nVidia Corporation MCP67 SMBus (rev a2)
00:01.2 RAM memory: nVidia Corporation MCP67 Memory Controller (rev a2)
00:01.3 Co-processor: nVidia Corporation MCP67 Co-processor (rev a2)
00:02.0 USB Controller: nVidia Corporation MCP67 OHCI USB 1.1 Controller (rev a2)
00:02.1 USB Controller: nVidia Corporation MCP67 EHCI USB 2.0 Controller (rev a2)
00:04.0 USB Controller: nVidia Corporation MCP67 OHCI USB 1.1 Controller (rev a2)
00:04.1 USB Controller: nVidia Corporation MCP67 EHCI USB 2.0 Controller (rev a2)
00:06.0 IDE interface: nVidia Corporation MCP67 IDE Controller (rev a1)
00:07.0 Audio device: nVidia Corporation MCP67 High Definition Audio (rev a1)
00:08.0 PCI bridge: nVidia Corporation MCP67 PCI Bridge (rev a2)
00:09.0 IDE interface: nVidia Corporation MCP67 AHCI Controller (rev a2)
00:0a.0 Ethernet controller: nVidia Corporation MCP67 Ethernet (rev a2)
00:0c.0 PCI bridge: nVidia Corporation MCP67 PCI Express Bridge (rev a2)
00:0d.0 PCI bridge: nVidia Corporation MCP67 PCI Express Bridge (rev a2)
00:12.0 VGA compatible controller: nVidia Corporation GeForce 7000M (rev a2) (rev a2)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:04.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 05)
01:04.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 22)
01:04.2 System peripheral: Ricoh Co Ltd R5C843 MMC Host Controller (rev 12)
01:04.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 12)
01:04.4 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev ff)
05:00.0 Ethernet controller: Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter (rev 01)

The only thing I got to work with my webcam is Cheese Webcam Booth, although the mic didn't get captured.

So if anyone could help me out with this it'd be a great help.

---

### Post by Vakman on 2009-08-08
Try this, found this on [http://ubuntuforums.org/showthread.php?t=715366](http://ubuntuforums.org/showthread.php?t=715366)
Quote from natirips.
"- download the files to your desktop
- extract the files (right-click the icon and click extract here (or something like that, I'm not sure since I have localized version))
- open console (ALT+F2 (to run a program) than enter "gnome-terminal" without the quotes)
- now go to your Desktop directory from console: "cd ~/Desktop" (without the quotes again, mind the capitalisation/case and notice that it might be called something else if you have a localized (non-english) version, type "ls" in console to check up - it will list all non-hidden directories and files there are)
- now go into the linux-uvc directory: "cd linux-uvc", or what ever it is called if you renamed it
- now enter the following commands:
Code:
./svn-version.sh
sudo make
sudo make install"
Note: I have attached the files he had attached. Let me know how it goes.

---

### Post by mikethedj4 on 2009-08-08
ok well I installed the tarball, and extracted it on my desktop.

When I put cd ~/Desktop into the terminal nothing came up.

Then when I put down "ls" (of course without the quotes) I got.

Default COD4 Files  examples.desktop  MySpace Layouts  Videos
Desktop             ISO Images        Pictures         v-pic powerpoint.odp
Documents           lmms              Public
dwhelper            Music             Templates

Then when I put down "./svn-version.sh" (of course without the quotes) I got
./svn-version.sh: No such file or directory

Is it possible to get a PS3 Headset to work with Linux???

All I know about my headset is that it's a Logitech.

---

### Post by neu2buntu on 2009-08-08
try ```
cd Desktop
``` as you are already in your home when 1st opening the terminal

~/ is home dir from any other location

---

### Post by neu2buntu on 2009-08-08
actually scrap my above comment,i should have tried this before posting....cd ~/Desktop does work...from the terminal in home...have learned something new myself here!!!

---

### Post by mikethedj4 on 2009-08-08
When I put down cd Desktop all I got was ~/Desktop$

I apologize if I'm making this difficult for anyone, I feel like an idiot.

---

### Post by neu2buntu on 2009-08-08
from here do code ls -a (this shows all files,including hidden) .. ....hmmm can you see the file on your desktop? if not it is most likely in /tmp

---

### Post by mikethedj4 on 2009-08-08
Yeah I see the file on my desktop, hasn't moved.

---

### Post by neu2buntu on 2009-08-08
from your reply:- When I put down cd Desktop all I got was ~/Desktop$ ... you are at your desktop.... the command "cd" has to be used in  every stepthrough folders.....   right we will start again follow me do code ```
cd Desktop && ls
``` from your terminal..and paste the output as a reply here.

---

### Post by mikethedj4 on 2009-08-08
speed@ubuntu:~$ cd Desktop && ls
linux-uvc
speed@ubuntu:~/Desktop$

---

### Post by neu2buntu on 2009-08-08
ok now we see the file.... keep this terminal open (or if you have closed it run the previous command) so you see "speed@ubuntu:~/Desktop$".

now run this command (using enter/return when required,and also your password for the install) ```
cd linux-uvc && ./svn-version.sh && make && sudo make install
```    now hopefully this will run all the commands in a row ...let me know how you get on with it, or if you are still unsure dont be afraid to ask,... as we were all unsure at one timehow to do all this ,..i will look up some tutorials for you to get u 2 know linux a bit better...ok

---

### Post by neu2buntu on 2009-08-08
heres some sites to check over [http://linux.org.mt/article/terminal](http://linux.org.mt/article/terminal)
[http://ubuntuforums.org/showthread.php?t=171507](http://ubuntuforums.org/showthread.php?t=171507)
actually just google > linux tutorial terminal commands or something like this and also read any books you can get your hands on too!!

---

### Post by mikethedj4 on 2009-08-20
This is what I got running the command in the terminal.

[COLOR=Blue]speed@ubuntu:~$ cd linux-uvc && ./svn-version.sh && make && sudo make install
bash: ./svn-version.sh: Permission denied
speed@ubuntu:~/linux-uvc$ [/COLOR]

---

### Post by neu2buntu on 2009-08-20
oops forgot about changing ownership of an executable file   do command ```
cd linux-uvc && chmod 755 svn-version.sh && ./svn-version.sh && make && sudo make install
```      the 755 in chmod gives user(you) read write and execute permissions of the file and group and others only read and execute permissions,...hopefully this should work now.

---

### Post by mikethedj4 on 2009-08-21
I got this

./svn-version.sh: 3: svn: not found
Building USB Video Class driver...
make[1]: Entering directory `/usr/src/linux-headers-2.6.28-15-generic'
  CC [M]  /home/speed/linux-uvc/uvc_driver.o
/home/speed/linux-uvc/uvc_driver.c: In function ‘uvc_register_video’:
/home/speed/linux-uvc/uvc_driver.c:1443: error: incompatible types in assignment
/home/speed/linux-uvc/uvc_driver.c:1444: error: ‘struct video_device’ has no member named ‘type’
/home/speed/linux-uvc/uvc_driver.c:1445: error: ‘struct video_device’ has no member named ‘type2’
make[2]: *** [/home/speed/linux-uvc/uvc_driver.o] Error 1
make[1]: *** [_module_/home/speed/linux-uvc] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.28-15-generic'
make: *** [uvcvideo] Error 2

---

### Post by neu2buntu on 2009-08-22
from your error it looks like you need subversion installed first run command ```
sudo apt-get install subversion
``` ,then run the command (post #14) again

---

### Post by mikethedj4 on 2009-10-14
after I installed that subversion thing.

I ran the sudo make and sudo make install commands, and I get these errors.

```
speed@ubuntu:~/Desktop/linux-uvc$ ./svn-version.sh
bash: ./svn-version.sh: Permission denied
speed@ubuntu:~/Desktop/linux-uvc$ sudo make
[sudo] password for speed: 
Building USB Video Class driver...
make[1]: Entering directory `/usr/src/linux-headers-2.6.28-15-generic'
  CC [M]  /home/speed/Desktop/linux-uvc/uvc_driver.o
/home/speed/Desktop/linux-uvc/uvc_driver.c: In function ‘uvc_register_video’:
/home/speed/Desktop/linux-uvc/uvc_driver.c:1443: error: incompatible types in assignment
/home/speed/Desktop/linux-uvc/uvc_driver.c:1444: error: ‘struct video_device’ has no member named ‘type’
/home/speed/Desktop/linux-uvc/uvc_driver.c:1445: error: ‘struct video_device’ has no member named ‘type2’
make[2]: *** [/home/speed/Desktop/linux-uvc/uvc_driver.o] Error 1
make[1]: *** [_module_/home/speed/Desktop/linux-uvc] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.28-15-generic'
make: *** [uvcvideo] Error 2
speed@ubuntu:~/Desktop/linux-uvc$ sudo make install
Installing USB Video Class driver...
make[1]: Entering directory `/usr/src/linux-headers-2.6.28-15-generic'
  DEPMOD  2.6.28-15-generic
make[1]: Leaving directory `/usr/src/linux-headers-2.6.28-15-generic'
depmod -ae
speed@ubuntu:~/Desktop/linux-uvc$ 
```

---

