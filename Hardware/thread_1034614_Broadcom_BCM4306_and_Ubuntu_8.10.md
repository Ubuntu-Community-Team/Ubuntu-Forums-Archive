---
title: "Broadcom BCM4306 and Ubuntu 8.10"
date: 2009-01-08
forum: Hardware
---

### Post by The Funkbomb on 2009-01-08
Hello.  I am brand new to Ubuntu and all linux distros and I can't get my wireless set up.  I think a huge part of the problem is that I'm so new that I'm not exactly sure what I'm doing.

What I'm looking for is an idiot's guide to setting this up.  Just when you think you've dumbed it down enough, set your sites a little lower.

Here are some stats from my machine.

The machine itself is a HP Laptop model ZV5200.  AMD 64 3700+  2 gigs of ram.

The wireless card is the Broadcom BCM4306 Rev 03.

Here are some stats that I've gotten from running some commands in terminal.  (thanks to the guys in IRC)

From ifconfig -a:

```
funkbomb@funkbomb-laptop:~$ lspci
00:00.0 Host bridge: nVidia Corporation nForce3 Host Bridge (rev a4)
00:01.0 ISA bridge: nVidia Corporation nForce3 LPC Bridge (rev a6)
00:01.1 SMBus: nVidia Corporation nForce3 SMBus (rev a4)
00:02.0 USB Controller: nVidia Corporation nForce3 USB 1.1 (rev a5)
00:02.1 USB Controller: nVidia Corporation nForce3 USB 1.1 (rev a5)
00:02.2 USB Controller: nVidia Corporation nForce3 USB 2.0 (rev a2)
00:06.0 Multimedia audio controller: nVidia Corporation nForce3 Audio (rev a2)
00:06.1 Modem: nVidia Corporation nForce3 Audio (rev a2)
00:08.0 IDE interface: nVidia Corporation nForce3 IDE (rev a5)
00:0a.0 PCI bridge: nVidia Corporation nForce3 PCI Bridge (rev a2)
00:0b.0 PCI bridge: nVidia Corporation nForce3 AGP Bridge (rev a4)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:00.0 VGA compatible controller: nVidia Corporation NV17 [GeForce4 440 Go 64M] (rev a3)
02:00.0 FireWire (IEEE 1394): Texas Instruments TSB43AB21 IEEE-1394a-2000 Controller (PHY/Link)
02:01.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
02:02.0 Network controller: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller (rev 03)
02:04.0 CardBus bridge: Texas Instruments PCI1620 PC Card Controller (rev 01)
02:04.1 CardBus bridge: Texas Instruments PCI1620 PC Card Controller (rev 01)
02:04.2 System peripheral: Texas Instruments PCI1620 Firmware Loading Function (rev 01)
funkbomb@funkbomb-laptop:~$ clear

funkbomb@funkbomb-laptop:~$ ifconfig -a
eth0      Link encap:Ethernet  HWaddr 00:0f:b0:4b:50:6a  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:18 Base address:0x7000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:250 errors:0 dropped:0 overruns:0 frame:0
          TX packets:250 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:15684 (15.6 KB)  TX bytes:15684 (15.6 KB)

pan0      Link encap:Ethernet  HWaddr ba:f2:0f:56:fa:5c  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

wlan0     Link encap:Ethernet  HWaddr 00:90:4b:a1:60:c6  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

wmaster0  Link encap:UNSPEC  HWaddr 00-90-4B-A1-60-C6-00-00-00-00-00-00-00-00-00-00  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

funkbomb@funkbomb-laptop:~$ 

```

From lspci:

```
funkbomb@funkbomb-laptop:~$ lspci
00:00.0 Host bridge: nVidia Corporation nForce3 Host Bridge (rev a4)
00:01.0 ISA bridge: nVidia Corporation nForce3 LPC Bridge (rev a6)
00:01.1 SMBus: nVidia Corporation nForce3 SMBus (rev a4)
00:02.0 USB Controller: nVidia Corporation nForce3 USB 1.1 (rev a5)
00:02.1 USB Controller: nVidia Corporation nForce3 USB 1.1 (rev a5)
00:02.2 USB Controller: nVidia Corporation nForce3 USB 2.0 (rev a2)
00:06.0 Multimedia audio controller: nVidia Corporation nForce3 Audio (rev a2)
00:06.1 Modem: nVidia Corporation nForce3 Audio (rev a2)
00:08.0 IDE interface: nVidia Corporation nForce3 IDE (rev a5)
00:0a.0 PCI bridge: nVidia Corporation nForce3 PCI Bridge (rev a2)
00:0b.0 PCI bridge: nVidia Corporation nForce3 AGP Bridge (rev a4)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:00.0 VGA compatible controller: nVidia Corporation NV17 [GeForce4 440 Go 64M] (rev a3)
02:00.0 FireWire (IEEE 1394): Texas Instruments TSB43AB21 IEEE-1394a-2000 Controller (PHY/Link)
02:01.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
02:02.0 Network controller: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller (rev 03)
02:04.0 CardBus bridge: Texas Instruments PCI1620 PC Card Controller (rev 01)
02:04.1 CardBus bridge: Texas Instruments PCI1620 PC Card Controller (rev 01)
02:04.2 System peripheral: Texas Instruments PCI1620 Firmware Loading Function (rev 01)
funkbomb@funkbomb-laptop:~$ 

```

A nice guy in IRC told me to run ```
sudo ifconfig wlan0 on
```

The response I got was "SIOCSIFFLAGS: No such file or directory"

Can anyone help?  I kind of like ubuntu because it loads much faster than windows but if I can't get online, it isn't much use to me since I need the internet to learn more.

Thanks for your time.

---

### Post by The Funkbomb on 2009-01-09
I don't know if bumping is allowed on this site.  I'm just hoping for an answer.

---

### Post by cdtech on 2009-01-09
Your wireless is working (ifconfig). This shows the module is loaded and detecting the card. Try "sudo ifup wlan0" and see what it spits out

---

### Post by stchman on 2009-01-09
Load up ndisgtk.

```
sudo apt-get install ndisgtk
```

Get the Windows drivers for that card and launch ndisgtk.  Locate the .inf file and install it.  Your wireless should work.

You can also install the b43-fwcutter.

```
sudo apt-get install b43-fwcutter
```

I believe the cutter is on the LiveCD.

---

### Post by cdtech on 2009-01-09
Broadcom is supported with the Intrepid kernel using the b43 module......

---

### Post by The Funkbomb on 2009-01-09
Okay, I'm going to try these.  I'm still so new at this I can't determine which answer makes the most sense so I'll go from easiest to hardest.

You guys rock just for taking the time.  If any of these work, then you doubly rock.

---

### Post by The Funkbomb on 2009-01-09
I tried cdtech's command of "sudo ifup wlan0" and I got this response: "Ignoring unknown interface wlan0=wlan0."

I then went with stchman's advice.  I tried to install ndisgtk and had to install ndiswrapper.  After getting both installed, I used the GUI under System>Windows Wireless Drivers and installed bcm4306.inf.

Everything installed correctly but it still isn't working.  I'm still stumped.  I can't get it to turn on.

---

### Post by The Funkbomb on 2009-01-09
Oh, I also tried to put in bcm4306.sys but it said it wasn't a valid driver.  What do I do with that?

---

### Post by The Funkbomb on 2009-01-09
I'm sorry, those are BCMWL5.sys and BCMWL5.inf

---

### Post by stchman on 2009-01-09
> **The Funkbomb said:**
> I'm sorry, those are BCMWL5.sys and BCMWL5.inf

If you are going the ndiswrapper route then use the .inf file.

The easiest would be to just install the b43-fwcutter.

---

### Post by The Funkbomb on 2009-01-09
Can I do the fwcutter method now that I've done the nsidgtk/wrapper method?

---

### Post by The Funkbomb on 2009-01-09
okay, I installed the b43-fwcutter package but I'm not really sure how to use it yet.  Let me look around the forums and the net a bit.

---

### Post by The Funkbomb on 2009-01-09
So now after running b43-fwcutter, it shows up in the restricted drivers.

I clicked activate and entered my password.  The first time, a little green board showed up next to my network manager and said there was new hardware.

It still isn't activated or working at all.  I'm getting closer but just not there yet.  Anyone have more advice?

---

### Post by The Funkbomb on 2009-01-10
Guys, I just wanted to thank you.  I am now viewing the internet via ubuntu.  All it took was an ethernet cord to run the updates and it went beautifully.  :)

Thank you again.

---

### Post by cdtech on 2009-01-10
Good to hear you got it working...

Now on to the playground. Have fun.........

---

### Post by trajik78 on 2009-02-05
i think im basically having the same problem. did a fresh install of 8.10 on my desktop machine. It sees the broadcom wireless card i have installed in the PCI slot (BCM4306) and it knew to install fwcutter. Hardware manager has the green light and says its working properly.

Ubuntu says its installed fine but I entered all the Wireless info in network manager, i saves the profile but nothing happens. I've installed the regular and legacy firmware into the /lib but didnt really seem to do anything. 

wired network works just fine....

---

