---
title: "Linksys does not work..."
date: 2008-07-26
forum: General Help
---

### Post by dorrin200 on 2008-07-26
I recently installed linux for the first time.  I have a linksys router plugged in and working on a Windows Vista laptop.  I tried System -> Network and filled in all the information, but I still cannot connect.  I tried installing the linksys software, only to realize that Windows software does not work with linux (obviously).  Can somebody help me?  I am new to linux.

Thanks in advance!

---

### Post by cpetercarter on 2008-07-26
Are you trying to communicate with the router via an ethernet cable, or wirelessly?

---

### Post by dorrin200 on 2008-07-26
I'm trying to connect wirelessly.

---

### Post by spiderbatdad on 2008-07-26
I use a linksys router. They are are generally very friendly and in fact use linux firmware afaik.

Could you post the output of some terminal commands? Please paste the output inside code tags...the "#" symbol above.

```
ifconfig
netstat -r
```
Edit: just realized that was a dumb request, as you don't have internet access...

also helpful to know what wireless card you are working with:```
 sudo lshw -C net
```

---

### Post by dorrin200 on 2008-07-26
I think I repeated a command a couple times, but I'm not sure.

```
dan@dan-desktop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:07:e9:5f:6c:f7  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1392 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1392 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:72048 (70.3 KB)  TX bytes:72048 (70.3 KB)

dan@dan-desktop:~$ netstat -r
Kernel IP routing table
Destination     Gateway         Genmask         Flags   MSS Window  irtt Iface
dan@dan-desktop:~$ ifconfig netstat -r
-r: Unknown host
ifconfig: `--help' gives usage information.
dan@dan-desktop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:07:e9:5f:6c:f7  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1396 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1396 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:72296 (70.6 KB)  TX bytes:72296 (70.6 KB)

dan@dan-desktop:~$ sudo lshw -C net
[sudo] password for dan: 
  *-network:0             
       description: Network controller
       product: BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 2
       bus info: pci@0000:02:02.0
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master
       configuration: driver=b43-pci-bridge latency=64 module=ssb
  *-network:1
       description: Ethernet interface
       product: 82562EZ 10/100 Ethernet Controller
       vendor: Intel Corporation
       physical id: 8
       bus info: pci@0000:02:08.0
       logical name: eth0
       version: 02
       serial: 00:07:e9:5f:6c:f7
       size: 10MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e100 driverversion=3.5.23-k4-NAPI duplex=half firmware=N/A latency=64 link=no maxlatency=56 mingnt=8 module=e100 multicast=yes port=MII speed=10MB/s
  *-network DISABLED
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:1c:10:e5:31:7a
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11g



```



I hope this is helpful...

---

### Post by spiderbatdad on 2008-07-26
You'll have to enable a third party driver for that wireless card.

There are a number of how-tos on this site for doing that: [http://ubuntuforums.org/showthread.php?t=197102](http://ubuntuforums.org/showthread.php?t=197102)
for example. Not vouching for that specific one. Google a bit first...ubnutu broadcom 4318

---

### Post by cpetercarter on 2008-07-26
Look at the panel at the top of the screen. Is there an icon on there which looks lke a couple of blank computer screens. If so, right click on it. Is "enable wireless" checked?

---

### Post by dorrin200 on 2008-07-26
enable wireless is checked. Also I tried to do the hardy method the help thing showed me, but when I went to hardware drivers to check the Broadcom B43 wireless driver box, it was not there. The only box was for my ati graphics card driver. Does anyone know why that is?

---

### Post by xenolalia on 2008-07-30
[SIZE=3][COLOR=Red]**Sorry dorrin200!  Here are my revised instructions (see my response on the next page):**[/COLOR][/SIZE]

Hi dorrin200!

I am also new to linux; I, too, had a few difficulties getting my Linksys wireless card working.  Here is what worked for me:

1.) Using a computer (other than the target computer (as I'm assuming the target computer doesn't have access to the internet yet)) go to the following link, and click on the image of your wireless card (you may have to compare model numbers/specs):

[http://www.linksys.com/servlet/Satellite?c=L_Product_C1&childpagename=US%2FLayout&cid=1115416939789&pagename=Linksys%2FCommon%2FVisitorWrapper&lid=3978991233B01](http://www.linksys.com/servlet/Satellite?c=L_Product_C1&childpagename=US%2FLayout&cid=1115416939789&pagename=Linksys%2FCommon%2FVisitorWrapper&lid=3978991233B01)

2.) Click on the link entitled "Driver" (under the "More Information" header).

3.) Follow the instructions to download the correct driver/version for your wireless card.

4.) Extract the contents of the archive to any folder.

5.) If your computer has a 32-bit architecture, download and unzip the first zip archive I attached to this post.  Else if your computer has an AMD 64-bit architecture, download and unzip the second zip archive.  If in doubt, download the first one.

6.) Copy the driver folder and all of the .deb files from the zip archive you downloaded to a flash drive, or email them to yourself, or whatever (somehow, get everything to the target computer's desktop).

7.) ndisgtk is a graphical frontend to ndiswrapper (a utility which allows Windows wireless card drivers to run in Linux).   At the target computer, open up a Terminal and do the following:

```
cd Desktop
sudo dpkg -i ndis*.deb
```

Once everything is installed, exit out of the Terminal (you can delete all of the .deb files you downloaded), and go to System -> Administration -> Windows Wireless Drivers, and click on "Install New Driver."

8.) Click on the "location" bar, navigate to the folder containing the Wireless driver (steps 4 & 6), and double-click on the .inf file (***not*** autorun.inf).  It might be something like bcmwl5.inf.

9.) Now, click install.  Once finished, close the Windows Wireless Drivers dialog.  Now, when you click on the "double-monitor" icon in the top right-hand corner of your desktop, you should see a list of all available wireless networks.  Just click on the one you want and . . . you know the rest!

I hope that the above will prove at least . . . remotely . . . helpful, and that I didn't . . . completely misunderstand you (or completely screw up) :).

Good luck & happy internet-ing!

---

### Post by dorrin200 on 2008-08-02
hey I tried the method in the above post, but when I typed in sudo apt-get install ndisgtk it said it could not find ndisgtk. I tried searching for it in the synaptic package manager, but it could not find it either.

---

### Post by xenolalia on 2008-08-04
Oh -- right!  I forgot the target computer doesn't have internet yet.  DUH!   8-[  Really sorry.

I've edited my previous post.  Give it a try, now . . .

Good luck!

---

### Post by dorrin200 on 2008-08-04
When I try to install the new driver, I find two inf files. One is autorun.inf, and the other is bcmwl5.inf. When I tried to install autorun.inf it said there was an error. When I installed the other both showed up, the autorun driver had an X through it, while the bcmwl5 said there was no hardware present. 

Furthermore at system->administration->hardware drivers I found broadcom B43 wireless driver, the status said in use but the enabled box was not checked. I tried to check it but everytime I do the status changes to computer must be restarted, even after I already restarted teh computer. 

Any help you can give me would be appreciated.

---

### Post by AFarris01 on 2008-08-04
thats odd...and your wireless still isnt working?

---

### Post by dorrin200 on 2008-08-05
it is still not working

---

### Post by xenolalia on 2008-08-06
I'm sorry -- I should have been more specific; you should choose bcmwl5.inf.  I'm stumped, though, as to the "Hardware not present" thing. 
I'm not sure it'll make a difference, but you might try uninstalling and reinstalling ndiswrapper and ndisgtk.

To uninstall ndiswrapper and ndisgtk, do:
sudo apt-get autoremove ndisgtk

Upon reinstallation, choose to install bcmwl5.inf instead of autorun.inf.

Out of curiosity, what's the model number of your wireless card (e.g. WPC54G)?

---

