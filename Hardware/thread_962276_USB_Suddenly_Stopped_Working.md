---
title: "USB Suddenly Stopped Working"
date: 2008-10-29
forum: Hardware
---

### Post by luvr on 2008-10-29
I'm running Ubuntu 8.04, and since earlier this week, USB disk drives no longer get mounted. There's not even any entries added to the system log when I hook up a USB disk.

I tried the earlier kernels that are still present on my system, but they all have the same problem; yesterday, I got a kernel update, but even with this updated kernel, the problem remains.

Firewire disks still work fine, though.

To verify whether it's, perhaps, a hardware problem, I booted the Windows XP partition that still sits on the system, and that discovers USB disks just fine. I also started the Ubuntu Live CD, and that has no problems with USB disks either.

Now, I don't really mind simply reinstalling Ubuntu, since I won't lose any user data anyway, and installing plus updating doesn't take that awfully long. (Furthermore, I have clearly documented any further configuration steps that I need to take, so that's no problem either.)

Still, I do wonder what could have gone wrong, and if there might be any chance to solve this problem without reinstalling?

---

### Post by UtopiaTheory on 2008-10-29
Reinstalling is generally a last ditch effort for me.  I prefer troubleshooting just for the sake of learning something!  Try connecting your USB drive and opening a terminal and trying some of the following commands.

From the terminal type
```
lsusb
```
Check to see if your drive is listed.  

```
cd /proc/bus/usb
```
Make sure that this directory exists!  I've seen it go missing before!

```
dmesg | grep usb
```
Check for error messages here.

```
sudo mount -a
```
This mounts all devices listed in your fstab.  

That's about the extent of which I can help you without further info!  Maybe you could reply with the output of the dmesg | grep usb command!

Tom

---

### Post by luvr on 2008-10-29
Thanks for your quick reply. I'll try the commands when I get home.

I had already done the
```
sudo mount -a
```
but the USB drive does not show up in the output.

I had also done
```
sudo lshw
```
once **without,** and once **with** a USB disk connected, and the output was identical in both cases (I did a *"diff"* on both output files, and no differences showed up).

I'll post more results as I get them.

And, yes, you're absolutely right: Even though I may still decide to do a clean reinstall in the end, I prefer to do a little troubleshooting first, just to see if I learn anything from it.

---

### Post by UtopiaTheory on 2008-10-29
Cool...This way, if you solve the problem and someone else posts here with the same problem you can help them!

Tom

---

### Post by luvr on 2008-10-29
Boy, **now** I'm confused... USB is suddenly *working* again?!?!?

The kids were playing (under Windows XP) when the batteries of my wireless mouse went dead. I didn't immediately have replacement batteries handy, so I connected my USB laptop mouse to the computer to let them continue their games.

When the kids stopped, I rebooted into Ubuntu, with the USB mouse still hooked up. While the system was booting, I thought: *"Oops! This will, in all likelyhood, not work, since Ubuntu no longer sees USB..."*

Then, once Ubuntu had finished booting, the mouse *did* turn out to work after all--much to my surprise. So, I connected a USB stick, ... and that worked, too!

How mysterious... :confused:

---

### Post by luvr on 2008-10-29
Hmmm... Now I'm even **more** confused...

I decided to reboot, but this time *without* the USB mouse connected. The system came up, I connected the USB stick, ... and nothing happened. I then connected to mouse, ... and even *that* didn't work.

Since I didn't have access to a mouse, I found it kind of hard to operate the GUI. Thus, I hit *<Ctrl>-<Alt>-<F1>* to call up a console, and logged in to that.

The first thing I noticed, was that the **/proc/bus/usb** directory did exist (but was empty).

I then typed the **lsusb** command, ... and all of a sudden, the USB stick got recognised and mounted. When I subsequently connected the USB mouse, that worked, too.

Let me first get replacement batteries for the wireless mouse, and I'll then take another look at this problem.

---

### Post by anamorgan on 2008-10-29
I have a better idea, USE A BALL MOUSE !!!!!!!!!!!
IF I WERE IN YOUR POSITION, I WOULD DEFINITELY DO SO, I  really hate when the mouse speacially destracts inbetween work.

---

### Post by UtopiaTheory on 2008-10-30
> **luvr said:**
> Hmmm... Now I'm even **more** confused...

I decided to reboot, but this time *without* the USB mouse connected. The system came up, I connected the USB stick, ... and nothing happened. I then connected to mouse, ... and even *that* didn't work.

Since I didn't have access to a mouse, I found it kind of hard to operate the GUI. Thus, I hit *<Ctrl>-<Alt>-<F1>* to call up a console, and logged in to that.

The first thing I noticed, was that the **/proc/bus/usb** directory did exist (but was empty).

I then typed the **lsusb** command, ... and all of a sudden, the USB stick got recognised and mounted. When I subsequently connected the USB mouse, that worked, too.

Let me first get replacement batteries for the wireless mouse, and I'll then take another look at this problem.


If it comes down to it, you can have the system run the lsusb command at startup...that sounds like it might work.  Very bizarre though!

---

### Post by 080801jk on 2008-10-30
&#33521;&#22269;ITE&#20844;&#21496;&#21019;&#24314;&#20110;1991&#24180;&#12290;&#29616;&#22312;&#65292;[**&#26032;&#20852;&#24066;&#22330;&#23637;&#35272;**](http://www.ite-china.com.cn)ITE&#24050;&#25104;&#20026;&#26032;&#20852;&#24066;&#22330;&#21644;&#21457;&#23637;&#20013;&#24066;&#22330;&#30340;&#20250;&#23637;&#19994;&#20808;&#38155;&#65292;[&#20013;**&#20122;&#36152;&#26131;&#26426;&#20250;**](http://www.ite-china.com.cn)&#22312;&#20420;&#32599;&#26031;&#36825;&#20010;&#19990;&#30028;&#19978;&#26368;&#22823;&#12289;[**&#26032;&#20852;&#24066;&#22330;&#23637;&#35272;**](http://www.ite-china.com.cn)&#26368;&#20855;&#27963;&#21147;&#30340;&#24066;&#22330;&#19978;&#65292;[**&#20013;&#20122;&#23637;&#35272;**](http://www.ite-china.com.cn)ITE&#22312;&#35813;&#22320;&#21306;&#30340;&#23637;&#35272;&#33310;&#21488;&#19978;&#24050;&#32463;&#25104;&#20026;&#26368;&#20855;&#39046;&#23548;&#22320;&#20301;&#30340;&#39046;&#22836;&#20891;&#12290;&#20844;&#21496;&#20110;2001&#24180;&#20262;&#25958;&#35777;&#21048;&#20132;&#26131;&#25152;&#25104;&#21151;&#19978;&#24066;&#12290;&#12288;&#12288;ITE &#20844;&#21496;&#22312;&#26032;&#20852;&#24066;&#22330;&#30340;&#21331;&#36234;&#21457;&#23637;&#20026;&#29616;&#26377;&#23637;&#20250;&#30340;&#25104;&#38271;&#21644; [**&#20013;&#20122;&#36152;&#26131;&#26426;&#20250;**](http://www.ite-china.com.cn)&#26032;&#20852;&#24066;&#22330;&#23637;&#35272;&#30340;&#25193;&#23637;&#21450;&#20844;&#21496;&#30340;&#21457;&#23637;&#25112;&#30053;&#25552;&#20379;&#20102;&#22362;&#22266;&#30340;&#22522;&#30784;

---

### Post by luvr on 2008-10-30
After I boot the system (with no USB devices connected):
```
$ dmesg | grep "usb"
[   37.028198] usbcore: registered new interface driver usbfs
[   37.028215] usbcore: registered new interface driver hub
[   37.028240] usbcore: registered new device driver usb
[   39.712710] usb usb1: configuration #1 chosen from 1 choice
[   39.868441] usb usb2: configuration #1 chosen from 1 choice
[   39.976097] usb usb3: configuration #1 chosen from 1 choice
[   40.131009] usb usb4: configuration #1 chosen from 1 choice
[   40.286753] usb usb5: configuration #1 chosen from 1 choice
[   40.304650] usb 3-4: new high speed USB device using ehci_hcd and address 2
[   40.413373] usb usb6: configuration #1 chosen from 1 choice
[   40.419510] usb 3-4: configuration #1 chosen from 1 choice
[   40.830785] usb 6-3: new high speed USB device using ehci_hcd and address 2
[   40.945560] usb 6-3: configuration #1 chosen from 1 choice
[   41.772324] usb usb7: configuration #1 chosen from 1 choice
$ lsusb
Bus 004 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  
Bus 007 Device 001: ID 0000:0000  
Bus 003 Device 002: ID 0409:0058 NEC Corp. HighSpeed Hub
Bus 003 Device 001: ID 0000:0000  
Bus 006 Device 002: ID 0409:0058 NEC Corp. HighSpeed Hub
Bus 006 Device 001: ID 0000:0000  
Bus 005 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
```

After I connect a USB stick, there's no change whatsoever to the output from the *dmesg* command. When I subsequently execute the *lsusb* command, the output is also unchanged, but the stick does get activated and mounted.

Once the device is mounted, the commands produce the following output:
```
$ dmesg | grep "usb"
[   37.028198] usbcore: registered new interface driver usbfs
[   37.028215] usbcore: registered new interface driver hub
[   37.028240] usbcore: registered new device driver usb
[   39.712710] usb usb1: configuration #1 chosen from 1 choice
[   39.868441] usb usb2: configuration #1 chosen from 1 choice
[   39.976097] usb usb3: configuration #1 chosen from 1 choice
[   40.131009] usb usb4: configuration #1 chosen from 1 choice
[   40.286753] usb usb5: configuration #1 chosen from 1 choice
[   40.304650] usb 3-4: new high speed USB device using ehci_hcd and address 2
[   40.413373] usb usb6: configuration #1 chosen from 1 choice
[   40.419510] usb 3-4: configuration #1 chosen from 1 choice
[   40.830785] usb 6-3: new high speed USB device using ehci_hcd and address 2
[   40.945560] usb 6-3: configuration #1 chosen from 1 choice
[   41.772324] usb usb7: configuration #1 chosen from 1 choice
[  270.276325] usb 3-4.1: new high speed USB device using ehci_hcd and address 3
[  270.343195] usb 3-4.1: configuration #1 chosen from 1 choice
[  270.395640] usbcore: registered new interface driver libusual
[  270.410637] usbcore: registered new interface driver usb-storage
[  270.411019] usb-storage: device found at 3
[  270.411118] usb-storage: waiting for device to settle before scanning
[  272.075581] usb-storage: device scan complete
$ lsusb
Bus 004 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  
Bus 007 Device 001: ID 0000:0000  
Bus 003 Device 003: ID 058f:6387 Alcor Micro Corp. Transcend JetFlash 110 USB 2.0 Flash Drive (2GB)
Bus 003 Device 002: ID 0409:0058 NEC Corp. HighSpeed Hub
Bus 003 Device 001: ID 0000:0000  
Bus 006 Device 002: ID 0409:0058 NEC Corp. HighSpeed Hub
Bus 006 Device 001: ID 0000:0000  
Bus 005 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
```

But then, when I **unmount** the stick and connect another USB storage device, again, nothing happens. To get the system to discover and mount it, I have to repeat the **lsusb** command.

So, it looks like the USB subsystem stops operating whenever I remove all USB devices; to make it work again, I have to execute the **lsusb** command after I connect a device.

**_Update:_** It turns out that even the **lsusb** command will stop working after two or three times. Here's the messages that appear in the *dmesg* output when this problem begins:
```
[  927.349584] hub 3-4:1.0: cannot reset port 4 (err = -110)
[  927.685704] hub 3-4:1.0: cannot reset port 4 (err = -110)
[  928.021812] hub 3-4:1.0: cannot reset port 4 (err = -110)
[  928.357924] hub 3-4:1.0: cannot reset port 4 (err = -110)
[  928.694038] hub 3-4:1.0: cannot reset port 4 (err = -110)
[  928.694041] hub 3-4:1.0: Cannot enable port 4.  Maybe the USB cable is bad?
[  929.030154] hub 3-4:1.0: cannot disable port 4 (err = -110)
[  929.366290] hub 3-4:1.0: cannot reset port 4 (err = -110)
[  929.702384] hub 3-4:1.0: cannot reset port 4 (err = -110)
[  930.038498] hub 3-4:1.0: cannot reset port 4 (err = -110)
[  930.374613] hub 3-4:1.0: cannot reset port 4 (err = -110)
[  930.710727] hub 3-4:1.0: cannot reset port 4 (err = -110)
[  930.710732] hub 3-4:1.0: Cannot enable port 4.  Maybe the USB cable is bad?
[  931.046841] hub 3-4:1.0: cannot disable port 4 (err = -110)
[  931.382956] hub 3-4:1.0: cannot reset port 4 (err = -110)
[  931.719071] hub 3-4:1.0: cannot reset port 4 (err = -110)
[  932.055186] hub 3-4:1.0: cannot reset port 4 (err = -110)
[  932.391299] hub 3-4:1.0: cannot reset port 4 (err = -110)
[  932.727412] hub 3-4:1.0: cannot reset port 4 (err = -110)
[  932.727416] hub 3-4:1.0: Cannot enable port 4.  Maybe the USB cable is bad?
[  933.063527] hub 3-4:1.0: cannot disable port 4 (err = -110)
[  933.399641] hub 3-4:1.0: cannot reset port 4 (err = -110)
[  933.735755] hub 3-4:1.0: cannot reset port 4 (err = -110)
[  934.071870] hub 3-4:1.0: cannot reset port 4 (err = -110)
[  934.407984] hub 3-4:1.0: cannot reset port 4 (err = -110)
[  934.744098] hub 3-4:1.0: cannot reset port 4 (err = -110)
[  934.744102] hub 3-4:1.0: Cannot enable port 4.  Maybe the USB cable is bad?
[  935.080214] hub 3-4:1.0: cannot disable port 4 (err = -110)
[  935.416326] hub 3-4:1.0: cannot disable port 4 (err = -110)
[  935.416508] sd 5:0:0:0: Device offlined - not ready after error recovery
[  937.096898] hub 3-4:1.0: hub_port_status failed (err = -110)
```
A bad USB cable seems highly unlikely, because this error only happens when I'm running this particular Ubuntu instance--any other Operating System that I tried (Windows XP, Ubuntu Live CD, Slackware) accesses my USB devices just fine.

---

### Post by luvr on 2008-11-02
I think I'll leave it at that and not put any further energy into this problem.

For the time being, I can circumvent the problem by connecting a USB device and running the **lsusb** command once, and subsequently making sure that at least one USB device remains connected. Once I disconnect all USB devices, I cannot be sure that the **lsusb** command will re-enable USB without a reboot.

I'm currently evaluating Ubuntu 8.10 on another computer, and once I decide whether or not it works well enough for me, I'll make up my mind about reinstalling 8.04, or replacing it with 8.10 on my main computer.

---

### Post by KrazyPenguin on 2008-11-02
Just had the same problem with my laptop, by enabling the touch pad, even with my mouse plugged in the usb drive worked.  When the touchpad is disabled the usb device will NOT mount.

Weird!!!

:confused:

---

### Post by sarthorks on 2008-11-22
I have a similar problem to luvr. Only doing "lsusb" after plugging in the usb drive doesn't mount it even once.

Here's my output for ```
dmesg | grep usb
```

```
sarthak@sarthorks:/proc/bus/usb$ dmesg | grep usb
[   20.649895] usbcore: registered new interface driver usbfs
[   20.649918] usbcore: registered new interface driver hub
[   20.650457] usbcore: registered new device driver usb
[   20.673553] usb usb1: configuration #1 chosen from 1 choice
[   20.797336] usb usb2: configuration #1 chosen from 1 choice
[   20.901483] usb usb3: configuration #1 chosen from 1 choice
[   21.005203] usb usb4: configuration #1 chosen from 1 choice
[   21.109016] usb usb5: configuration #1 chosen from 1 choice
[   21.202631] usb usb6: configuration #1 chosen from 1 choice
[   21.213323] usb 1-4: new high speed USB device using ehci_hcd and address 3
[   21.272492] usb usb7: configuration #1 chosen from 1 choice
[   21.353344] usb 1-4: configuration #1 chosen from 1 choice
[   21.549006] usb 4-1: new full speed USB device using uhci_hcd and address 2
[   21.571226] usb 4-1: configuration #1 chosen from 1 choice
[   21.629402] usb 6-2: new full speed USB device using uhci_hcd and address 2
[   21.657476] usb 6-2: configuration #1 chosen from 1 choice
[   33.137967] usbcore: registered new interface driver hci_usb
[   33.156428] usbcore: registered new interface driver uvcvideo

```

Its the same for both USB plugged in/not plugged in.
```
lsusb
```:

```
sarthak@sarthorks:/proc/bus/usb$ lsusb
Bus 007 Device 001: ID 0000:0000  
Bus 006 Device 002: ID 0a5c:2101 Broadcom Corp. 
Bus 006 Device 001: ID 0000:0000  
Bus 004 Device 002: ID 08ff:2580 AuthenTec, Inc. 
Bus 004 Device 001: ID 0000:0000  
Bus 005 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 003: ID 04f2:b013 Chicony Electronics Co., Ltd 
Bus 001 Device 001: ID 0000:0000  

```

Also,
```
sudo mount -a
```
doesn't work.

My usb partition was sdb. I realised that the sdb and sdb1 files present in /dev have suddenly disappeared. 
Although they are THERE in the Live CD, and maybe thats why my usb work over there. What should I do?
I reall ythink the problem is the missing sdb and sdb1 files in /dev

---

### Post by sarthorks on 2008-11-22
More precisely, doing a 
```
ls /dev/sd*

```

results into 
```
sarthak@sarthorks:/proc/bus/usb$ ls /dev/sd*
/dev/sda  /dev/sda1  /dev/sda2  /dev/sda3

```

while it also used to list 
```

/dev/sdb   /dev/sdb1

``` when my usb drive was working.

It does list sdb and sdb1 in Live CD right now.

---

### Post by sarthorks on 2008-11-22
please help!!!

---

### Post by sarthorks on 2008-11-23
HOOORAY!

My usb drive started working on its own!

```

sarthak@sarthorks:~$ ls /dev/sd*
/dev/sda  /dev/sda1  /dev/sda2  /dev/sda3  /dev/sdb  /dev/sdb1

```

```

sarthak@sarthorks:~$ dmesg | grep usb
[   21.459457] usbcore: registered new interface driver usbfs
[   21.459482] usbcore: registered new interface driver hub
[   21.464629] usbcore: registered new device driver usb
[   21.485879] usb usb1: configuration #1 chosen from 1 choice
[   21.957118] usb usb2: configuration #1 chosen from 1 choice
[   22.053305] usb usb3: configuration #1 chosen from 1 choice
[   22.055159] usb 1-4: new high speed USB device using ehci_hcd and address 3
[   22.152260] usb usb4: configuration #1 chosen from 1 choice
[   22.196335] usb 1-4: configuration #1 chosen from 1 choice
[   22.256087] usb usb5: configuration #1 chosen from 1 choice
[   22.345943] usb usb6: configuration #1 chosen from 1 choice
[   22.359905] usb usb7: configuration #1 chosen from 1 choice
[   22.467584] usb 4-1: new full speed USB device using uhci_hcd and address 2
[   22.486900] usb 4-1: configuration #1 chosen from 1 choice
[   22.535232] usb 6-2: new full speed USB device using uhci_hcd and address 2
[   22.558807] usb 6-2: configuration #1 chosen from 1 choice
[   34.073243] usbcore: registered new interface driver hci_usb
[   34.103123] usbcore: registered new interface driver uvcvideo
[ 5861.627246] usb 5-1: new full speed USB device using uhci_hcd and address 2
[ 5861.712650] usb 5-1: not running at top speed; connect to a high speed hub
[ 5861.744758] usb 5-1: configuration #1 chosen from 1 choice
[ 5862.112082] usbcore: registered new interface driver libusual
[ 5862.158401] usbcore: registered new interface driver usb-storage
[ 5862.158997] usb-storage: device found at 2
[ 5862.159001] usb-storage: waiting for device to settle before scanning
[ 5865.270203] usb-storage: device scan complete

```

```

sarthak@sarthorks:~$ lsusb
Bus 007 Device 001: ID 0000:0000  
Bus 006 Device 002: ID 0a5c:2101 Broadcom Corp. 
Bus 006 Device 001: ID 0000:0000  
Bus 005 Device 002: ID 13fe:1d00 Kingston Technology Company Inc. DataTraveler 2.0 1GB Flash Drive
Bus 005 Device 001: ID 0000:0000  
Bus 004 Device 002: ID 08ff:2580 AuthenTec, Inc. 
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 003: ID 04f2:b013 Chicony Electronics Co., Ltd 
Bus 001 Device 001: ID 0000:0000  

```

All the outputs seem normal.
I have no clue what really happened.
Cud be an issue with the kernel (i did not update or do anything with it. Everything happened without any new addition/deletetion]

---

### Post by luvr on 2008-11-24
[SIZE="4"]**WOW!** This **MUST** be a bug![/SIZE]

I have two computers with nearly identical hardware--both have a *Gigabyte GA-MA78G-DS3H motherboard,* both have an *AMD Athlon(tm) 64 X2 Dual Core Processor 6000+,* and both have three USB hubs connected to them:
[LIST]
[*]An **STLab** four-port USB 2.0 hub, connected to a USB port on the back of the case;
[*]A **Sitecom** FW-006 Combo Hub, with 4 USB 2.0 ports and 2 Firewire ports, connected to motherboard headers;
[*]A **Silverstone** Combo Hub, with 4 USB 2.0 ports and 1 Firewire port (plus audio), also connected to motherboard headers.
[/LIST]
Now, when I boot an Ubuntu 8.04 LiveCD on either computer, then USB works fine--whenever I attach a USB device to any of the hubs, it gets picked up and mounted as it should.

**HOWEVER,** when I boot the Ubuntu 8.04 copy that I installed on the harddisk (and to which I applied all available updates), then USB will **NOT** work as it should. Whenever I attach a USB device to either the *STLab* or the *Sitecom* hub, the device will **not** be seen until I run the *lsusb* command (though even that won't always work). If, on the other hand, I connect a USB device to the ***Silverstone,*** then it does **sometimes** get properly picked up, but sometimes not.

**MUST** be a bug! Time to perform some data collection and file a bug report...

Now, I'd upgrade to Ubuntu 8.10 (which--so far--does not have this problem), were it not for a problem with video playback--any movie player program suffers from bad flickering (giving me a headache), and corrupts the display of the progam's menu; also, dragging the window leaves the movie display behind (still flickering) until I release the mouse button. *****SIGH*****

---

### Post by luvr on 2008-11-29
As it turned out, there was no need for me to file a new bug report; instead, I simply subscibed to [Bug #254589: ubuntu doesn't recognise usb drives.]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/254589")

**_OFF-TOPIC:_**

[INDENT]The video playback problems have already been reported as a bug, as well: [Bug #179042: Videos tear and "blink" when enabling compiz [AMD Feature #7647] [EPR#257833].]("https://bugs.launchpad.net/ubuntu/+source/fglrx-installer/+bug/179042") Turns out to be a problem with the ATI proprietary drivers.

It's high time that AMD/ATI makes good on its promises to support fully open-sourced drivers! *(If they don't, then I can only hope that **Intel** releases good graphics boards that are properly supported by open-source drivers sometime soon, at which time I'll dump ATI. I don't mean to say that ATI is crap--it isn't--but if I have a choice, I'll go for the best option available to me.)*

Anyway, while we wait for a solution from AMD/ATI, there is a workaround described in [comment 25]("https://bugs.launchpad.net/ubuntu/+source/fglrx-installer/+bug/179042/comments/25") to the bug report. Works for me, so it looks like I can upgrade to the Intrepid Ibex after all.[/INDENT]

---

### Post by GlennW on 2008-12-06
This is nuts! I'm running Ibex with all the updates in place, no major or crazy alterations. My situation is not altogether dissimilar to the posters above.

I don't have any usb drives just printer, webcam, palm, mp3 player. Frequently, any of these, most noticeably the printer since it's used most often, will not mount. If I unplug the offending and corresponding cable and plug it in again, it works! 

What is up with that? Being a n00b, I'm a bit nonplussed with this bugginess. It was intriguing to read about the lsusb command being a temporary fix. There must be a better fix than running a script to mount all usb connections. Dirty fixes like that are MS fare!

Please, if you have any insight into this share your knowledge!!

Thanks.

---

### Post by anv on 2009-01-17
I'm new "happy" owner of this motherboard ga-ma78g-ds3h and I had to return the first board two weeks ago because it didn't work on usb, usb bootup, and it just had some major hardware failure, and this morning after setting this new motherboard which I received instead, it seems that there's abit same kind of problem så I know while running all these hardwares (disks, keyboards, etc.) with my Asus MOBO no problems. If we could collect enough international clients around world to complain to Gigabit, those individuals in normal conditions might get problems in front of reseller after second or third change of hardware during guarantee period. I'm pissed of just now, I have to try to configure this more If I can see is it actually Hardware which is crappy.

---

