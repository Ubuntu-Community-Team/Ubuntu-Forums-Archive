---
title: "Can't Enable Wireless Internet"
date: 2008-05-27
forum: Hardware
---

### Post by rossmc92 on 2008-05-27
Just installed Xubuntu on my laptop. I was having trouble using the wireless internet so I installed my windows wlan drivers using Windows Wireless Drivers. Now there is a new connection in network called wireless connection. It is picking up my wireless router (belkin 54g), I have no password and I've set it to automatic configuration (DHCP). I have also enabled roaming mode as I don't have a clue when it comes to internet setup.

Any ideas?

---

### Post by pytheas22 on 2008-05-27
Please post the output of the following commands:

```
iwconfig
ifconfig
iwlist scan
lspci
lsusb
```

This will give us a better idea of what to try.

---

### Post by rossmc92 on 2008-05-28
> **pytheas22 said:**
> Please post the output of the following commands:

```
iwconfig
ifconfig
iwlist scan
lspci
lsusb
```

This will give us a better idea of what to try.

anne@anne-laptop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11g  ESSID:off/any  
          Mode:Managed  Frequency:389.543 GHz  Access Point: Not-Associated   
          Bit Rate:11 Mb/s   
          RTS thr=2347 B   Fragment thr=2346 B   
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

anne@anne-laptop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:40:d0:7f:56:20  
          inet addr:192.168.2.5  Bcast:192.168.2.255  Mask:255.255.255.0
          inet6 addr: fe80::240:d0ff:fe7f:5620/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1492  Metric:1
          RX packets:234 errors:0 dropped:0 overruns:0 frame:0
          TX packets:269 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:201321 (196.6 KB)  TX bytes:31771 (31.0 KB)
          Interrupt:20 Base address:0xc200 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:22 errors:0 dropped:0 overruns:0 frame:0
          TX packets:22 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:1100 (1.0 KB)  TX bytes:1100 (1.0 KB)

wlan0     Link encap:Ethernet  HWaddr 00:60:b3:da:5b:02  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:21 

anne@anne-laptop:~$ iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wlan0     Scan completed :
          Cell 01 - Address: 00:11:50:FF:10:82
                    ESSID:"belkin54g"
                    Protocol:IEEE 802.11g
                    Mode:Managed
                    Frequency:2.462 GHz (Channel 11)
                    Quality:100/100  Signal level:-12 dBm  Noise level:-96 dBm
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0

anne@anne-laptop:~$ lspci
00:00.0 Host bridge: Intel Corporation Mobile 915GM/PM/GMS/910GML Express Processor to DRAM Controller (rev 04)
00:02.0 VGA compatible controller: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller (rev 04)
00:02.1 Display controller: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller (rev 04)
00:1b.0 Audio device: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) High Definition Audio Controller (rev 04)
00:1d.0 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1 (rev 04)
00:1d.1 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2 (rev 04)
00:1d.2 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3 (rev 04)
00:1d.7 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller (rev 04)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev d4)
00:1f.0 ISA bridge: Intel Corporation 82801FBM (ICH6M) LPC Interface Bridge (rev 04)
00:1f.2 IDE interface: Intel Corporation 82801FBM (ICH6M) SATA Controller (rev 04)
00:1f.3 SMBus: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) SMBus Controller (rev 04)
01:02.0 CardBus bridge: Texas Instruments PCIxx21/x515 Cardbus Controller
01:02.2 FireWire (IEEE 1394): Texas Instruments OHCI Compliant IEEE 1394 Host Controller
01:04.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
01:05.0 Ethernet controller: Winbond Electronics Corp W89C33D 802.11 a/b/g BB/MAC
anne@anne-laptop:~$ lsusb

hope that helps :S

---

### Post by pytheas22 on 2008-05-28
Everything appears to be in order based on the output above.  What specifically were you having problems with?  Are you unable to connect to your router?

---

### Post by rossmc92 on 2008-05-30
> **pytheas22 said:**
> Everything appears to be in order based on the output above.  What specifically were you having problems with?  Are you unable to connect to your router?

yeah. It just doesn't connect for some reason unless I use a wired connection. I'm pretty sure it's not a hardware problem because it worked fine when I was using windows.

---

### Post by pytheas22 on 2008-05-30
Are you using Network Manager to connect?  If so, what happens when you try to connect--do the green dots light up at all?  Have you tried using a different wireless utility, like [wicd]("http://wicd.sourceforge.net")?  Network Manager is pretty buggy sometimes...

Another thing to try is to connect using the command-line.  Try these commands:
```

sudo -s
ifconfig wlan0 down
iwconfig wlan0 mode managed
iwconfig wlan0 channel 11
iwconfig wlan0 essid "belkin54g"
ifconfig wlan0 up
dhclient wlan0
```

Please post the output of each of these commands, and hopefully they'll indicate what's going wrong.

---

### Post by rossmc92 on 2008-05-31
Yes I am using network manager and I'm about to try wicd, in the meantime here are the results of the commands you posted:

root@anne-laptop:~# ifconfig wlan0 down
root@anne-laptop:~# iwconfig wlan0 mode managed
root@anne-laptop:~# iwconfig wlan0 channel 11
root@anne-laptop:~# iwconfig wlan0 essid "belkin54g"
root@anne-laptop:~# ifconfig wlan0 up
root@anne-laptop:~# dhclient wlan0
There is already a pid file /var/run/dhclient.pid with pid 6660
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.0.6
Copyright 2004-2007 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/wlan0/00:60:b3:da:5b:02
Sending on   LPF/wlan0/00:60:b3:da:5b:02
Sending on   Socket/fallback
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 9
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 8
No DHCPOFFERS received.
No working leases in persistent database - sleeping.

---

### Post by pytheas22 on 2008-06-01
The output above indicates that the card is trying to connect but is not getting an IP address.  This could be some problem with your router--make sure it's set to give out IP addresses--but I suspect that the problem lies with the Linux wireless card.

I did some research on your card (Winbond W89C33D) and it looks like it's very, very difficult to get it working under Linux.  There's no native driver, and even with ndiswrapper, several people seem to have the same problem as you: they can see networks but not connect.  The only mention that I found of someone having success was at [http://ubuntuforums.org/showthread.php?t=484728&highlight=W89C33D](http://ubuntuforums.org/showthread.php?t=484728&highlight=W89C33D) (see post number 6), but it's not clear what the poster did.  You could try private messaging and maybe he or she would tell you.

You could also try compiling ndiswrapper from source, which may or may not do the trick.  To do that, you would:

0. install a compiler:
```

sudo apt-get install build-essential
```

1. purge the version of ndiswrapper that you installed through the repositories:
```

sudo apt-get remove --purge ndiswrapper
sudo rmmod ndiswrapper
```

2. download and build ndiswrapper from the latest stable release:

download the source from [http://sourceforge.net/project/downloading.php?group_id=93482&use_mirror=internap&filename=ndiswrapper-1.53.tar.gz&21491019](http://sourceforge.net/project/downloading.php?group_id=93482&use_mirror=internap&filename=ndiswrapper-1.53.tar.gz&21491019)
```

cd Desktop
tar -xzvf ndis*
cd ndis*
make
sudo make install
```

Then install the Windows drivers again--you will need to use the command-line to do it because the GUI will be gone, but if you don't know how to use the command-line to do it, feel free to ask.

This will hopefully solve the problem, but there's no guarantee, unfortunately.

You could also try setting an IP address statically using either wicd or the utility at System>Administration>Network and see if it makes the card work.

---

### Post by rossmc92 on 2008-06-16
> **pytheas22 said:**
> The output above indicates that the card is trying to connect but is not getting an IP address.  This could be some problem with your router--make sure it's set to give out IP addresses--but I suspect that the problem lies with the Linux wireless card.

I did some research on your card (Winbond W89C33D) and it looks like it's very, very difficult to get it working under Linux.  There's no native driver, and even with ndiswrapper, several people seem to have the same problem as you: they can see networks but not connect.  The only mention that I found of someone having success was at [http://ubuntuforums.org/showthread.php?t=484728&highlight=W89C33D](http://ubuntuforums.org/showthread.php?t=484728&highlight=W89C33D) (see post number 6), but it's not clear what the poster did.  You could try private messaging and maybe he or she would tell you.

You could also try compiling ndiswrapper from source, which may or may not do the trick.  To do that, you would:

0. install a compiler:
```

sudo apt-get install build-essential
```

1. purge the version of ndiswrapper that you installed through the repositories:
```

sudo apt-get remove --purge ndiswrapper
sudo rmmod ndiswrapper
```

2. download and build ndiswrapper from the latest stable release:

download the source from [http://sourceforge.net/project/downloading.php?group_id=93482&use_mirror=internap&filename=ndiswrapper-1.53.tar.gz&21491019](http://sourceforge.net/project/downloading.php?group_id=93482&use_mirror=internap&filename=ndiswrapper-1.53.tar.gz&21491019)
```

cd Desktop
tar -xzvf ndis*
cd ndis*
make
sudo make install
```

Then install the Windows drivers again--you will need to use the command-line to do it because the GUI will be gone, but if you don't know how to use the command-line to do it, feel free to ask.

This will hopefully solve the problem, but there's no guarantee, unfortunately.

You could also try setting an IP address statically using either wicd or the utility at System>Administration>Network and see if it makes the card work.

I only did codes 0 & 1 as they both produced errors, here's the results:

sudo apt-get remove --purge ndiswrapper
sudo rmmod ndiswrapper

Hope this helps.

---

### Post by pytheas22 on 2008-06-16
I'm a little confused; I don't see any error messages in your last post.  Please run the command:
```
sudo apt-get install build-essential
sudo apt-get remove --purge ndiswrapper
```

and if you get errors, please post the output here.  As long as you have a working Internet connection (via the ethernet wire) these commands should run with no problems.

Or if I'm missing something, please point it out.

---

### Post by rossmc92 on 2008-06-22
> **pytheas22 said:**
> I'm a little confused; I don't see any error messages in your last post.  Please run the command:
```
sudo apt-get install build-essential
sudo apt-get remove --purge ndiswrapper
```

and if you get errors, please post the output here.  As long as you have a working Internet connection (via the ethernet wire) these commands should run with no problems.

Or if I'm missing something, please point it out.

Sorry there was a lot of errors but for some reason it didn't copy/paste everything I highlighted. I had to do a fresh install because when I started up the laptop there was some problem and it wouldn't start up. I'm updating the laptop at the moment so I'll post the results when I've finished.

---

### Post by rossmc92 on 2008-06-22
sorry for some reason not everything I highlighted in the terminal pasted. Updating laptop just now so I will post the results of the code later

---

### Post by rossmc92 on 2008-06-22
here they are:

anne@anne-laptop:~$ sudo apt-get install build-essential
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run &#8216;apt-get -f install&#8217; to correct these:
The following packages have unmet dependencies.
  build-essential: Depends: libc6-dev but it is not going to be installed or
                            libc-dev
                   Depends: g++ (>= 4:4.1.1) but it is not going to be installed
                   Depends: dpkg-dev (>= 1.13.5) but it is not going to be installed
  linux-restricted-modules-generic: Depends: linux-restricted-modules-2.6.24-19-generic but it is not going to be installed
E: Unmet dependencies. Try &#8216;apt-get -f install&#8217; with no packages (or specify a solution).
anne@anne-laptop:~$ sudo apt-get remove --purge ndiswrapper
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package ndiswrapper
anne@anne-laptop:~$

---

### Post by pytheas22 on 2008-06-22
apt-get is failing because it can't find necessary dependencies.  Please do this to make sure it has the resources it needs:

1. if you can get a wired Internet connection to your machine without too much difficulty, please do that.  This isn't essential, so if it's too much trouble don't worry about it.

2. go to System>Administration>Software Sources, and make sure that all of the boxes under the first tab are checked.  Then close the utility.  You'll be asked if you want to update the sources list; say yes.

3. make sure your Ubuntu installation CD is in the drive and try these commands again:

```
sudo apt-get install build-essential
```

---

### Post by psundar on 2008-07-13
Hi,

I cannot connect to my wireless internet. But I was able to do it till yesterday.
The output of my iwconfig doesnt list "wlan0".

Pl help.

Psundar

---

### Post by pytheas22 on 2008-07-13
> I cannot connect to my wireless internet. But I was able to do it till yesterday.
The output of my iwconfig doesnt list "wlan0".

You may want to start a new thread for this issue, since it's not really related to the topic of this one, but either way, please provide this information so we can figure out the problem.  Open a terminal and type:
```

dmesg
lshw -C Network
lspci
lsusb
```

and please post the output here (or in a new thread).  If you start a new thread let me know where it is.

Also, which version of Ubuntu are you using, and have you installed updates?

---

### Post by psundar on 2008-08-06
Hi,

thanks for the reply. I have created a new thread and included the output of those commands. 
The thread link is given below:(title: problem in wireless connection)
[http://ubuntuforums.org/showthread.php?p=5538573#post5538573](http://ubuntuforums.org/showthread.php?p=5538573#post5538573)

Thanks,
psundar

---

