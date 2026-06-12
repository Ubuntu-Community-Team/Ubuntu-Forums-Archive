---
title: "Acer Aspire 4530 wireless"
date: 2008-08-06
forum: Hardware
---

### Post by kris99466 on 2008-08-06
Hi, i just installed ubuntu in my laptop Aspire 4530 and it having problem with the wireless, i don't know how i activate the wireless.. please help if there is a solution of it.. THX... ^^

---

### Post by pytheas22 on 2008-08-06
Please open up a terminal (Applications>Accessories menu), run these commands (one per line) and post the output here:
```

lspci -nn
lshw -C Network
uname -m
```

That will help us figure out what you need to do to make the wireless work.

---

### Post by kris99466 on 2008-08-06
lsci -nn
bash: lsci: command not found

lshw -C Network
WARNING: you should run this program as super-user.
  *-network               
       description: Ethernet interface
       product: NetXtreme BCM5764M Gigabit Ethernet PCIe
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:08:00.0
       logical name: eth0
       version: 10
       serial: 00:1e:68:83:e6:d1
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=tg3 driverversion=3.86 

ip=192.168.1.101 latency=0 module=tg3 multicast=yes
  *-network UNCLAIMED
       description: Ethernet controller
       product: AR242x 802.11abg Wireless PCI Express Adapter
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:0b:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: cap_list
       configuration: latency=0

uname -m
i686

---

### Post by pytheas22 on 2008-08-06
> lsci -nn
bash: lsci: command not found

You made a typo there; it should be "lspci -nn" :)

It would still be good to see the "lspci -nn" output, but I think I know which chipset you have and how to make it work.  Please see this [post]("http://ubuntuforums.org/showpost.php?p=5525672&postcount=73") and the Word document attached to it, which has instructions on how to make your card work (don't worry if you don't have the same computer model mentioned there; your wireless chipset is the same).

Please let me know how it goes.  Please also post:
```

lspci -nn | grep -i atheros
```

when you get a chance so that I can be sure that your chipset is the same as the one for which that guide was written.

---

### Post by kris99466 on 2008-08-06
Hahaha.. I sleep last night, and just wake up, still blur ^^

lspci -nn | grep -i atheros
0b:00.0 Ethernet controller [0200]: Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter [168c:001c] (rev 01)

Ok.. Iam trying to follow the word document instruction there ^^

---

### Post by kris99466 on 2008-08-06
Hi, i already done the installing the problem now is that i not even know wheter my wireless is on or off, because i have this easy-launch buttons that seems doesn't work including the wireless button...

---

### Post by pytheas22 on 2008-08-06
> 0b:00.0 Ethernet controller [0200]: Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter [168c:001c] (rev 01)


You have the right chipset, so that guide should work for you.
> 
Hi, i already done the installing the problem now is that i not even know wheter my wireless is on or off, because i have this easy-launch buttons that seems doesn't work including the wireless button...

If you don't know whether the switch is on or off, just press it again and see if the wireless comes on.  If not, press the switch a second time, and try then.

If you still can't get wireless to come on, please post the output of:
```

lshw -C Network
ndiswrapper -l
iwlist scan
```

---

### Post by kris99466 on 2008-08-06
lshw -C Network
WARNING: you should run this program as super-user.
PCI (sysfs)  
  *-network               
       description: Ethernet interface
       product: NetXtreme BCM5764M Gigabit Ethernet PCIe
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:08:00.0
       logical name: eth0
       version: 10
       serial: 00:1e:68:83:e6:d1
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=tg3 driverversion=3.86 ip=192.168.1.101 latency=0 module=tg3 multicast=yes
  *-network UNCLAIMED
       description: Ethernet controller
       product: AR242x 802.11abg Wireless PCI Express Adapter
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:0b:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: cap_list
       configuration: latency=0


ndiswrapper -l
net5211 : driver installed
	device (168C:001C) present (alternate driver: ath_pci)

iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

---

### Post by pytheas22 on 2008-08-06
Thanks for the information.  Please try running:
```

lsmod | grep ndiswrapper
sudo modprobe -v ndiswrapper
sudo ifconfig wlan0 up
iwlist scan
```

and please post the output.  That should lead to the solution.

---

### Post by kris99466 on 2008-08-06
ERmm... i tried run it 2 times, and resulting hangs... and then i restarted my computer...

---

### Post by pytheas22 on 2008-08-06
That's not good; something bad must be going on if it hangs when you try to insert the ndiswrapper module (it was hanging on the "sudo modprobe -v ndiswrapper" step, right?).  Please try running this to install the wireless again (make sure you are plugged into ethernet for these steps):

```
sudo -s
apt-get remove --purge ndiswrapper*
apt-get install ndiswrapper*
echo 'blacklist ath_pci' >> /etc/modprobe.d/blacklist
```

Now reboot, then continue with:

```
sudo -s
wget ftp://ftp.work.acer-euro.com/notebook/aspire_4710/driver/Wireless_Atheros.zip
unzip Wireless_Atheros.zip
cd Atheros
unzip HR2H01WW.zip
ndiswrapper -i net5211.inf
echo 'ndiswrapper' | sudo tee -a /etc/modules
modprobe ndiswrapper
```

At this point your wireless should work.  If not, turn the wireless switch on.  If it still doesn't work, please post the output of:
```

lsmod | grep ndis
ndiswrapper -l
cat /etc/modprobe.d/blacklist
iwlist scan
```

---

### Post by kris99466 on 2008-08-07
Wow... it's working, i cant detect wireless now, but Iam not sure how i connect to it.. like in windows i can see wheter it connected or not in the right bottom icon, but how i check in ubuntu???

---

### Post by pytheas22 on 2008-08-07
That it's working is a good sign.  To connect, left-click on the Network Manager applet in the top-right corner of the screen (it looks like two computer monitors when it's not connected), and you should see a list of networks.  Click the one you want to connect to and it will ask you for the passphrase if necessary, then hopefully get you online.

---

### Post by kris99466 on 2008-08-07
hmm.. at the top right corner (after right click) what i can see is only this list:

Enable Networking
Edit wireless networks
about

---

### Post by kris99466 on 2008-08-07
FInally i can connect using the wireless.. thank u very much ^^ now iam using my wireless already... i owe u alot man... ^^

anyway i just bought this laptop, do you know how can i get my drivers? graphic and audio.. thx ^^

---

### Post by zipperback on 2008-08-07
I have an Acer Aspire 5050-3371 and I believe it uses the same wifi chip as yours. 

The output of lspci for my system shows the following with Ubuntu 8.04.1 Hardy.

[quote]
lspci | grep Atheros
02:00.0 Ethernet controller: Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter (rev 01)
[/quote\

I am using the current madwifi driver and works fine.
The following should work for you.

Uninstall the ndiswrapper and remove the windows drivers before attempting to use the following.


Open a terminal and do the following

```


sudo apt-get update 

sudo apt-get install install build-essential

wget -c http://snapshots.madwifi.org/special/madwifi-ng-r2756+ar5007.tar.gz

tar xvf madwifi-ng-r2756+ar5007.tar.gz

cd madwifi-ng-r2756+ar5007

sudo make

sudo make install

sudo modprobe ath_pci

sudo modprobe wlan_scan_sta


```

Now reboot your computer and your wifi should be working.

- zipperback
:popcorn:

---

### Post by zipperback on 2008-08-07
> **kris99466 said:**
> do you know how can i get my drivers? graphic and audio.. thx ^^



Please provide the output of:

```
lspci
```

- zipperback
:popcorn:

---

### Post by kris99466 on 2008-08-07
lspci

00:00.0 RAM memory: nVidia Corporation Unknown device 0754 (rev a2)
00:01.0 ISA bridge: nVidia Corporation Unknown device 075e (rev a2)
00:01.1 SMBus: nVidia Corporation Unknown device 0752 (rev a1)
00:01.3 Co-processor: nVidia Corporation Unknown device 0753 (rev a2)
00:01.4 RAM memory: nVidia Corporation Unknown device 0568 (rev a1)
00:02.0 USB Controller: nVidia Corporation Unknown device 077b (rev a1)
00:02.1 USB Controller: nVidia Corporation Unknown device 077c (rev a1)
00:04.0 USB Controller: nVidia Corporation Unknown device 077d (rev a1)
00:04.1 USB Controller: nVidia Corporation Unknown device 077e (rev a1)
00:07.0 Audio device: nVidia Corporation Unknown device 0774 (rev a1)
00:08.0 PCI bridge: nVidia Corporation Unknown device 075a (rev a1)
00:09.0 SATA controller: nVidia Corporation Unknown device 0ad5 (rev a2)
00:0b.0 PCI bridge: nVidia Corporation Unknown device 0569 (rev a1)
00:13.0 PCI bridge: nVidia Corporation Unknown device 077a (rev a1)
00:14.0 PCI bridge: nVidia Corporation Unknown device 077a (rev a1)
00:15.0 PCI bridge: nVidia Corporation Unknown device 077a (rev a1)
00:18.0 Host bridge: Advanced Micro Devices [AMD] Family 11h HyperTransport Configuration (rev 40)
00:18.1 Host bridge: Advanced Micro Devices [AMD] Family 11h Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] Family 11h DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] Family 11h Miscellaneous Control
00:18.4 Host bridge: Advanced Micro Devices [AMD] Family 11h Link Control
02:00.0 VGA compatible controller: nVidia Corporation Unknown device 0844 (rev a2)
08:00.0 Ethernet controller: Broadcom Corporation NetXtreme BCM5764M Gigabit Ethernet PCIe (rev 10)
0b:00.0 Ethernet controller: Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter (rev 01)

---

### Post by kris99466 on 2008-08-07
One more question here, i installed aMSN but i can't connect to it.. is it required to install something else to make it can sign in???

---

### Post by pytheas22 on 2008-08-07
> I have an Acer Aspire 5050-3371 and I believe it uses the same wifi chip as yours.

The output of lspci for my system shows the following with Ubuntu 8.04.1 Hardy.


lspci | grep Atheros
02:00.0 Ethernet controller: Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter (rev 01)


I am using the current madwifi driver and works fine.
The following should work for you.

Uninstall the ndiswrapper and remove the windows drivers before attempting to use the following.

I think that the latest madwifi code supports this chipset, but only on 32-bit kernels.  The poster here has 64-bit, so I'm pretty sure that ndiswrapper is the only way to make it work.  If it's working now with ndiswrapper, I don't think it's a good idea to uninstall ndiswrapper and start playing around with madwifi again.
> 
One more question here, i installed aMSN but i can't connect to it.. is it required to install something else to make it can sign in???

I've never used MSN messaging but can't you just connect to it using Pidgin, the normal instant-messaging client that comes installed in Ubuntu?  See the [Pidgin FAQ]("http://developer.pidgin.im/wiki/Using%20Pidgin#HowdoIuseAIMMSNYahooGoogleTalkJabberXMPPICQoranyotherprotocol") for more information.
> 
do you know how can i get my drivers? graphic and audio

Audio usually works out-of-the-box on Ubuntu; do you not have any sound?  If so you may want to start a new thread to look into that.  I don't have any experience troubleshooting sound so I can't make many suggestions there.

As for video, try using [envy]("http://albertomilone.com/nvidia_scripts1.html"); it doesn't work 100% of the time, but for most people it installs the video drivers very easily and automatically.

---

### Post by hackeye on 2008-08-08
I have a weird issue with hardy on an acer aspire 5920. The Wi-Fi button (it's in a separate column of keys on the left of the main key-pad) doesn't seem to work. Why i call this weird is that i had installed feisty on it earlier, and with a few package upgrades and stuff, the button had started working perfectly with the LED blinking and going out when it was pressed, like it happens on Windows. Now it doesn't seem to work. I have to manually go to 'System -> Administration -> Network' and enable/ disable the wireless connection from there.

I also have other quick-launch buttons in that set (to launch browser, mail client and to activate/deactivate bluetooth) and all of them work.

Any ideas? Any help would be greatly appreciated.

- cheers,
hackeye.

---

### Post by gootoo on 2008-09-23
I have same pc, but fail in loading, is there any kernel parameter? Looks like can not recognize CD.
thank you very much.

---

### Post by pytheas22 on 2008-09-23
> I have same pc, but fail in loading, is there any kernel parameter? Looks like can not recognize CD.
thank you very much.

What exactly is wrong?  How far does the loading get before it fails?  Did you check the CD for defects?

---

### Post by dreamsong on 2008-10-24
hello :)



may i ask how did you install ubuntu on the acer aspire 4530?
(2.0ghz amd 64 turionx2, nvidia geforce 9100M G) i've tried using both intrepid betas 32 and and amd64 bit to no avail.

the 64 one just beeps and blinks on a blank screen after 
selecting install ubuntu.
when installing the 32bit one,
first it goes on low graphics mode warning:
(EE) device not found. then it goes into a selection menu where you can pick something like a)use default b)use new setting c)used saved setting...

every option just seems to go back to that choice menu.
even resetting afterwards, it just goes back to the same menu.
does anyone know how to solve this problem?
it'll be much appreciated


p.s. i'm a real ubuntu / linux newbie. previous experiences was
just installing hardy on older laptops which worked great out
of the box. haven't done or know anything fancy yet on the terminal except a few get-apps.

i'vw posted in another thread 4530, but it doesn't seem that
active.



many thanks! :)

---

### Post by pytheas22 on 2008-10-25
dreamsong: there's a bug report about this issue [here]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/275159").  It's not really solved, but someone says that it worked to use the alternate (text-based) installation CD.  So you might want to try burning an alternate CD and installing with that.

It might also work to install from [wubi]("wubi-installer.org").

---

### Post by antonio_helder2002 on 2008-10-25
Recently i bought a ACER Aspire 4530 laptop but cant install any OS in it. as soon as i boot my laptop from the Ububtu CD it shows an error & goes into the ternimal & accepts no commands :(
please help

---

### Post by pytheas22 on 2008-10-26
> Recently i bought a ACER Aspire 4530 laptop but cant install any OS in it. as soon as i boot my laptop from the Ububtu CD it shows an error & goes into the ternimal & accepts no commands
please help

Please see my post above (#25) with the link to the bug report regarding this issue.  You should be able to work around it by using the alternative CD to install Ubuntu instead of the live CD.  If you don't know what the alternate CD is and can't figure it out by googling, let me know and I'll find the link.

---

### Post by nikolaiortiz on 2008-11-01
hi.. pytheas22

i read and make all that you say.. only change the driver inf  for my inf windows inf file
please if you can help me

~$ lspci |grep Atheros
0b:00.0 Network controller: Atheros Communications Inc. Unknown device 002a (rev 01)
~$ ndiswrapper -l
netathw : driver installed
        device (168C:002A) present
~$ lshw -C Network
WARNING: you should run this program as super-user.
  *-network
       description: Ethernet interface
       product: NetXtreme BCM5764M Gigabit Ethernet PCIe
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:08:00.0
       logical name: eth0
       version: 10
       serial: 00:1e:68:ca:f8:21
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=tg3 driverversion=3.86 ip=190.240.1.56 latency=0 module=tg3 multicast=yes
  *-network
       description: Network controller
       product: Atheros Communications Inc.
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:0b:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: driver=ndiswrapper latency=0 module=ndiswrapper


thanx

---

### Post by pytheas22 on 2008-11-01
nikolaiortiz: it looks like things should be working.  Are you unable to connect to networks?  It may help to try using [wicd]("http://wicd.sourceforge.net") instead of Network Manager.

---

### Post by nikolaiortiz on 2008-11-01
well i use now wicd, very nice but.. still dont work the wireless...
i dont know if i have the problem of easy-launch buttons (maybe kris99466 can help with the buttons thing...)
Umm the iwlist scan say this
$ iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.


the wireless still missed :S

and my full lspci

~$ lspci
00:00.0 RAM memory: nVidia Corporation Unknown device 0754 (rev a2)
00:01.0 ISA bridge: nVidia Corporation Unknown device 075e (rev a2)
00:01.1 SMBus: nVidia Corporation Unknown device 0752 (rev a1)
00:01.3 Co-processor: nVidia Corporation Unknown device 0753 (rev a2)
00:01.4 RAM memory: nVidia Corporation Unknown device 0568 (rev a1)
00:02.0 USB Controller: nVidia Corporation Unknown device 077b (rev a1)
00:02.1 USB Controller: nVidia Corporation Unknown device 077c (rev a1)
00:04.0 USB Controller: nVidia Corporation Unknown device 077d (rev a1)
00:04.1 USB Controller: nVidia Corporation Unknown device 077e (rev a1)
00:07.0 Audio device: nVidia Corporation Unknown device 0774 (rev a1)
00:08.0 PCI bridge: nVidia Corporation Unknown device 075a (rev a1)
00:09.0 IDE interface: nVidia Corporation Unknown device 0ad0 (rev a2)
00:0b.0 PCI bridge: nVidia Corporation Unknown device 0569 (rev a1)
00:13.0 PCI bridge: nVidia Corporation Unknown device 077a (rev a1)
00:14.0 PCI bridge: nVidia Corporation Unknown device 077a (rev a1)
00:15.0 PCI bridge: nVidia Corporation Unknown device 077a (rev a1)
00:18.0 Host bridge: Advanced Micro Devices [AMD] Family 11h HyperTransport Configuration (rev 40)
00:18.1 Host bridge: Advanced Micro Devices [AMD] Family 11h Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] Family 11h DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] Family 11h Miscellaneous Control
00:18.4 Host bridge: Advanced Micro Devices [AMD] Family 11h Link Control
02:00.0 VGA compatible controller: nVidia Corporation Unknown device 0844 (rev a2)
08:00.0 Ethernet controller: Broadcom Corporation NetXtreme BCM5764M Gigabit Ethernet PCIe (rev 10)
0b:00.0 Network controller: Atheros Communications Inc. Unknown device 002a (rev 01)

and have to say that the audio doesnt work too
all look like a storm of..
i will try a dist upgrade.. i dont know if i have to uninstall the ndis for that and  take out ath_pci from the black list?
too many questions but sorry :S

pdta: i'm using kubuntu, but im think is the same as ubuntu anyway.. i hope ;)

---

### Post by pytheas22 on 2008-11-01
nikolaiortiz: it would probably work if you upgraded to Kubuntu 8.10.  You can download that [here]("http://www.kubuntu.org/getkubuntu").

If that doesn't help, please post the output of:
```

uname -m
lshw -C Network
sudo iwlist scan
dmesg | grep -e ndis -e wlan -e adio
```

---

### Post by nikolaiortiz on 2008-11-01
thanx i will try compile a new kernel, i dont want kde4  :P
but if doesnt  work i will try the Ubuntu 8.10
i will post the progress
:)

---

### Post by nikolaiortiz on 2008-11-03
ok.. after a peace full night i compile a new kernel the things going better the new module ath9k detect the wireless and look like have to work but .. isn't so i going to give the chance to the distro upgrade
the last report with my new kernel is

# uname -a
Linux THRUST 2.6.27.4 #1 SMP Sun Nov 2 08:39:35 COT 2008 i686 GNU/Linux
# lshw -C Network
  *-network               
       description: Ethernet interface
       product: NetXtreme BCM5764M Gigabit Ethernet PCIe
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:08:00.0
       logical name: eth0
       version: 10
       serial: 00:1e:68:ca:f8:21
       size: 100MB/s
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical
 tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=tg3 driverversion=
3.94 duplex=full ip=200.122.205.30 latency=0 link=yes module=tg3 multicast=yes p
ort=twisted pair speed=100MB/s
  *-network
       description: Wireless interface
       product: Atheros Communications Inc.
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:0b:00.0
       logical name: wmaster0
       version: 01
       serial: 00:22:69:56:2b:f0
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix bus_master cap_list logical ethernet
 physical wireless
       configuration: broadcast=yes driver=ath9k latency=0 module=ath9k multicas
t=yes wireless=IEEE 802.11bgn
# sudo iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wmaster0  Interface doesn't support scanning.

wlan0     No scan results
# dmesg | grep -e ndis -e wlan -e adio
[   79.820765] ADDRCONF(NETDEV_UP): wlan0: link is not ready

well.. i'm going for the distro upgrade now :)

---

### Post by pytheas22 on 2008-11-03
I think the upgrade to Kubuntu 8.10 will help.  Other people are reporting that this card works much better in 8.10.

---

### Post by vtom80 on 2008-11-05
hackeye, in order to activate the wireless LED, you could use acerhk. See  [http://ubuntuforums.org/showthread.php?t=971636]("http://ubuntuforums.org/showthread.php?t=971636") to solve this.

Hope this helps,

tom

---

### Post by skdangi on 2008-11-18
Mine output is as follows:- 
Could somebody help ??

```
uname -m
i686
root@Robotcop:/# lshw -C Network
  *-network               
       description: Ethernet interface
       product: NetXtreme BCM5764M Gigabit Ethernet PCIe
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:08:00.0
       logical name: eth0
       version: 10
       serial: 00:1e:68:be:64:60
       size: 100MB/s
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=tg3 driverversion=3.86 duplex=full ip=10.0.0.3 latency=0 link=yes module=tg3 multicast=yes port=twisted pair speed=100MB/s
  *-network UNCLAIMED
       description: Ethernet controller
       product: AR242x 802.11abg Wireless PCI Express Adapter
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:0b:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix bus_master cap_list
       configuration: latency=0
root@Robotcop:/# sudo iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

root@Robotcop:/# dmesg | grep -e ndis -e wlan -e adio
[ 1780.843344] ndiswrapper version 1.52 loaded (smp=yes, preempt=no)
[ 1780.883201] usbcore: registered new interface driver ndiswrapper

```

---

### Post by pytheas22 on 2008-11-18
skdangi: are you using Ubuntu 8.04 or 8.10?  In 8.10, this card should 'just work,' I think.

Either way, if it's not working, please try running these commands, which will download and run a script to install the latest madwifi drivers for you (the script is from [this thread]("http://ubuntuforums.org/showthread.php?t=798485")):
```

wget http://kolmoskone.homelinux.org/~kaja/kamaa/madwifi.sh -O madwifi.sh
chmod +x madwifi.sh
sudo ./madwifi.sh
```

After finishing that, reboot, and in principle your wireless card should work.  If not, please post the output of:

```
cat /etc/modprobe.d/blacklist
lshw -C Network
dmesg | grep -e wlan -e ath
ndiswrapper -l
lspci -nn | grep -i atheros
```

---

### Post by nikolaiortiz on 2008-11-18
OK...
after a long time..
i finally install kubuntu 8.10
all works fine.. i feel the video a little slow.. but the rest it's ok... 
the wireless and audio work instantaneously, I will try to active the blink led for wireless following this guide
[http://ubuntuforums.org/showthread.php?t=971636](http://ubuntuforums.org/showthread.php?t=971636)
thanx for all support...

---

### Post by skdangi on 2008-11-18
Mine is 8.04 ubuntu Hardy version

---

### Post by pytheas22 on 2008-11-18
> Mine is 8.04 ubuntu Hardy version

Please follow the instructions in post #37 to install madwifi drivers using that script, and if that doesn't solve the problem, please post the information I ask for in post #37.

Alternatively, upgrading to Ubuntu 8.10 would probably fix it.

---

### Post by skdangi on 2008-11-18
pytheas22:::

when i executed the madwifi.sh script my output is

 > sudo ./madwifi.sh
Found at least one Atheros device.
Checking build dependencies...
...build dependencies OK
Checking for updates..svn: PROPFIND request failed on '/ath_info/trunk'
svn: PROPFIND of '/ath_info/trunk': Could not resolve hostname `svn.madwifi-project.org': No address associated with hostname ([http://svn.madwifi-project.org](http://svn.madwifi-project.org))



And after that my output for the commands specified by you is as follows:-

> sanjeev@Robotcop:~$ cat /etc/modprobe.d/blacklist
# This file lists those modules which we don't want to be loaded by
# alias expansion, usually so some other driver will be loaded for the
# device instead.

# evbug is a debug tool that should be loaded explicitly
blacklist evbug

# these drivers are very simple, the HID drivers are usually preferred
blacklist usbmouse
blacklist usbkbd

# replaced by e100
blacklist eepro100

# replaced by tulip
blacklist de4x5

# causes no end of confusion by creating unexpected network interfaces
blacklist eth1394

# snd_intel8x0m can interfere with snd_intel8x0, doesn't seem to support much
# hardware on its own (Ubuntu bug #2011, #6810)
blacklist snd_intel8x0m

# causes failure to suspend on HP compaq nc6000 (Ubuntu: #10306)
blacklist i2c_i801

# replaced by p54pci
blacklist prism54

# replaced by b43 and ssb.
blacklist bcm43xx

# most apps now use garmin usb driver directly (Ubuntu: #114565)
blacklist garmin_gps

# replaced by asus-laptop (Ubuntu: #184721)
blacklist asus_acpi

blacklist ath_pci
sanjeev@Robotcop:~$ lshw -C Network
WARNING: you should run this program as super-user.
  *-network               
       description: Ethernet interface
       product: NetXtreme BCM5764M Gigabit Ethernet PCIe
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:08:00.0
       logical name: eth0
       version: 10
       serial: 00:1e:68:be:64:60
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=tg3 driverversion=3.86 ip=10.0.0.3 latency=0 module=tg3 multicast=yes
  *-network UNCLAIMED
       description: Ethernet controller
       product: AR242x 802.11abg Wireless PCI Express Adapter
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:0b:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: latency=0
sanjeev@Robotcop:~$ dmesg | grep -e wlan -e ath
sanjeev@Robotcop:~$ ndiswrapper -l
sanjeev@Robotcop:~$ lspci -nn | grep -i atheros
0b:00.0 Ethernet controller [0200]: Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter [168c:001c] (rev 01)
sanjeev@Robotcop:~$ 



---

### Post by pytheas22 on 2008-11-18
skdangi: seems like there's a bug in that script; my apologies.  Please try running these commands to grab the madwifi source and compile it manually:
```

sudo apt-get install build-essential
wget http://downloads.sourceforge.net/madwifi/madwifi-0.9.4.tar.gz
tar -xzvf madwifi-0.9.4.tar.gz
cd madwifi-0.9.4
make
sudo make install
echo ath_pci | sudo tee -a /etc/modules
sudo sed 's/blacklist ath_pci//' /etc/modprobe.d/blacklist
```

Then reboot.  This should do it.  If not, please post the output of:
```

lshw -C Network
dmesg | grep -e ath -e wlan
modinfo ath_pci
sudo iwlist scan
```

---

### Post by nikolaiortiz on 2008-11-19
Well..
i fail with the blink led :(
but in the process i realize that i have this error, alert on syslog

kernel	[12924.421987] ForceXPAon: 0

this thing happen and happen over and over every minute ](*,)
i read some things on google but the answers exceed my abilities of understanding :confused:
some help please :)

---

### Post by pytheas22 on 2008-11-19
nikolaiortiz: did you try following the guide [here]("http://ubuntuforums.org/showthread.php?t=971636")?  Did you complete it without error messages?

I don't think that the 'ForceXPAon' messages are related to the LED, actually.

---

### Post by nikolaiortiz on 2008-11-20
Ok i will try the guide step by step.. and place the result 
the 'ForceXPAon' warning is because the wireless lose and reconnect, I have to improve my english here, i don't get the rights words. :lolflag:
i think is from the kernel module :confused:
in some place i read that compile the kernel could skip this but i'm not sure about it...
 i keep on touch

... update..
 ok i finally end.. the wireless led is off.. nothing works
and the wireless still gwt thw ForceXPAon warning or alert
:(
i think i'm going to surrender

---

### Post by skdangi on 2008-11-21
My output is:

```
lshw -C Network
WARNING: you should run this program as super-user.
  *-network               
       description: Ethernet interface
       product: NetXtreme BCM5764M Gigabit Ethernet PCIe
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:08:00.0
       logical name: eth0
       version: 10
       serial: 00:1e:68:be:64:60
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=tg3 driverversion=3.86 ip=10.0.0.5 latency=0 module=tg3 multicast=yes
  *-network UNCLAIMED
       description: Ethernet controller
       product: AR242x 802.11abg Wireless PCI Express Adapter
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:0b:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: cap_list
       configuration: latency=0
sanjeev@sanjeev:~$ dmesg | grep -e ath -e wlan
[   34.003316] ath_hal: 0.9.18.0 (AR5210, AR5211, AR5212, RF5111, RF5112, RF2413, RF5413)
[   34.059031] wlan: 0.9.4
[   34.085957] ath_pci: 0.9.4
sanjeev@sanjeev:~$ modinfo ath_pci
filename:       /lib/modules/2.6.24-21-generic/net/ath_pci.ko
license:        Dual BSD/GPL
version:        0.9.4
description:    Support for Atheros 802.11 wireless LAN cards.
author:         Errno Consulting, Sam Leffler
srcversion:     D3FD3BD11169A96DBCFF8DE
alias:          pci:v0000168Cd00009013sv*sd*bc*sc*i*
alias:          pci:v0000168Cd0000001Dsv*sd*bc*sc*i*
alias:          pci:v0000168Cd0000001Csv*sd*bc*sc*i*
alias:          pci:v0000168Cd0000001Bsv*sd*bc*sc*i*
alias:          pci:v0000168Cd0000001Asv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000019sv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000018sv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000017sv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000016sv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000015sv*sd*bc*sc*i*
alias:          pci:v0000168Cd0000101Asv*sd*bc*sc*i*
alias:          pci:v0000168Cd00001014sv*sd*bc*sc*i*
alias:          pci:v000010B7d00000013sv*sd*bc*sc*i*
alias:          pci:v0000A727d00000013sv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000013sv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000012sv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000007sv*sd*bc*sc*i*
depends:        ath_hal,wlan
vermagic:       2.6.24-21-generic SMP mod_unload 586 
parm:           countrycode:Override default country code (int)
parm:           maxvaps:Maximum VAPs (int)
parm:           outdoor:Enable/disable outdoor use (int)
parm:           xchanmode:Enable/disable extended channel mode (int)
parm:           rfkill:Enable/disable RFKILL capability (int)
parm:           autocreate:Create ath device in [sta|ap|wds|adhoc|ahdemo|monitor] mode. defaults to sta, use 'none' to disable (charp)
parm:           ratectl:Rate control algorithm [amrr|minstrel|onoe|sample], defaults to 'sample' (charp)
parm:           ath_debug:Load-time debug output enable (int)
sanjeev@sanjeev:~$ sudo iwlist scan
[sudo] password for sanjeev: 
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.


```

---

### Post by pytheas22 on 2008-11-21
skdangi: sorry it's still not working.  What is the output of:
```

cat /etc/modprobe.d/blacklist | grep ath
sudo modprobe ath_pci
dmesg | grep -e ath -e wlan
lshw -C Network
```

---

### Post by skdangi on 2008-11-25
My output is:


```
sanjeev@sanjeev:~$ cat /etc/modprobe.d/blacklist | grep ath
blacklist ath_pci
sanjeev@sanjeev:~$ sudo modprobe ath_pci
sanjeev@sanjeev:~$ dmesg | grep -e ath -e wlan
[   32.454619] ath_hal: 0.9.18.0 (AR5210, AR5211, AR5212, RF5111, RF5112, RF2413, RF5413)
[   32.510288] wlan: 0.9.4
[   32.537214] ath_pci: 0.9.4
sanjeev@sanjeev:~$ lshw -C Network
WARNING: you should run this program as super-user.
  *-network               
       description: Ethernet interface
       product: NetXtreme BCM5764M Gigabit Ethernet PCIe
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:08:00.0
       logical name: eth0
       version: 10
       serial: 00:1e:68:be:64:60
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=tg3 driverversion=3.86 ip=10.0.0.3 latency=0 module=tg3 multicast=yes
  *-network UNCLAIMED
       description: Ethernet controller
       product: AR242x 802.11abg Wireless PCI Express Adapter
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:0b:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: cap_list
       configuration: latency=0

```

---

### Post by pytheas22 on 2008-11-25
skdangi: the problem seems to be that the ath_pci module is on the kernel blacklist.  Please open up the blacklist by typing:
```

sudo gedit /etc/modprobe.d/blacklist
```

Look for the line that reads:
```

blacklist ath_pci
```

Then delete that line, and save and close the file.  Then reboot.  Do things work now?  If not, what's the output of:
```

dmesg | grep -e ath -e wlan
lsmod | grep ath
sudo iwlist scan
```

---

### Post by skdangi on 2008-11-26
After removing the atheros chipset from the blacklist, a new icon shows a  network by the name -  "connect to 802.1X Protected Wired Network". My ```
normal lan connection is by the name "Wired Network." Is the new one is referring to the wireless connection? Somebody pointed out the same thing  in the previous model of Acer Aspire 4520 the same thing. Link here:  http://ubuntuforums.org/showthread.php?t=715187&page=5
This seems to be bug too.

By the way my output is 

sanjeev@sanjeev:~$ dmesg | grep -e ath -e wlan
[   32.011409] ath_hal: module license 'Proprietary' taints kernel.
[   32.033592] ath_hal: 0.9.18.0 (AR5210, AR5211, AR5212, RF5111, RF5112, RF2413, RF5413)
[   32.145282] wlan: 0.9.4
[   32.172407] ath_pci: 0.9.4
sanjeev@sanjeev:~$ lsmod | grep ath
ath_pci               100896  0 
wlan                  206960  1 ath_pci
ath_hal               192592  1 ath_pci
sanjeev@sanjeev:~$ sudo iwlist scan
[sudo] password for sanjeev: 
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.
```

---

### Post by pytheas22 on 2008-11-27
skdangi: sorry it's still not working.  To be honest I'm not positive what's wrong, because everything looks like it should work.  But I'm willing to keep trying until we can figure it out.  It should definitely be possible to get this card to work on Linux one way or another.

One suggestion for you is to upgrade to Ubuntu 8.10.  Your card should work 'out-of-the-box' there.

It would also be helpful if you could please post the output of:
```

lspci -nn
```

so that we can look up the exact model of your wireless card.  Maybe you have a strange chipset.

As for the stuff about the 802.1X network, unfortunately, that only refers to a wired connection.  Your wireless driver seems to still not be working for some reason.

---

### Post by ashik_8.10 on 2008-12-18
Is this thread still alive?
I have lost most of my hopes with madwifi and ndiswrapper. 
I think it's the same card that skdangi has. the results are the same.
skdanki, you got some good news?

---

### Post by pytheas22 on 2008-12-19
ashik_8.10: please post the output of these commands and I'll try to help:
```

lspci -nn
lshw -C Network
cat /etc/modprobe.d/blacklist
ndiswrapper -l
uname -m
sudo iwlist scan
lsb_release -a

```

---

### Post by otezz on 2008-12-21
Hello,

First of all, i'm sorry for my poor english

I'm using 4530-721G16Mn with Atheros AR928X. I' have followed all the instruction mentioned here but still it seems my wlan is not working. Can you please help me ?

I'm using Ubuntu 8.10 64.

---

### Post by pytheas22 on 2008-12-22
otezz: please also post the output of these commands:
```

lspci -nn
lshw -C Network
cat /etc/modprobe.d/blacklist
ndiswrapper -l
uname -m
sudo iwlist scan
```

---

### Post by otezz on 2008-12-22
Well, now i can finally make the wifi works. But the LED is not blinking.
Now i don't know wether my wifi is activated or not. :/

The instruction [here]("http://ubuntuforums.org/showthread.php?t=971636") only work for 32 Bit system.

---

### Post by pytheas22 on 2008-12-22
otezz: please see [this thread]("http://ubuntuforums.org/showthread.php?t=971636") about getting the LED to work.

---

### Post by l_synapse_l on 2009-01-11
> **zipperback said:**
> I have an Acer Aspire 5050-3371 and I believe it uses the same wifi chip as yours. 

The output of lspci for my system shows the following with Ubuntu 8.04.1 Hardy.

[quote]
lspci | grep Atheros
02:00.0 Ethernet controller: Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter (rev 01)
[/quote\

I am using the current madwifi driver and works fine.
The following should work for you.

Uninstall the ndiswrapper and remove the windows drivers before attempting to use the following.


Open a terminal and do the following

```


sudo apt-get update 

sudo apt-get install install build-essential

wget -c http://snapshots.madwifi.org/special/madwifi-ng-r2756+ar5007.tar.gz

tar xvf madwifi-ng-r2756+ar5007.tar.gz

cd madwifi-ng-r2756+ar5007

sudo make

sudo make install

sudo modprobe ath_pci

sudo modprobe wlan_scan_sta


```

Now reboot your computer and your wifi should be working.

- zipperback
:popcorn:

My Wifi works great when I perform the above steps. However, the problem is after a restart it no longer works. I have to **modprobe ath_pci** each time for it to work. Anyone know how I can keep the wifi from stopping after a restart.

---

### Post by pytheas22 on 2009-01-11
> My Wifi works great when I perform the above steps. However, the problem is after a restart it no longer works. I have to modprobe ath_pci each time for it to work. Anyone know how I can keep the wifi from stopping after a restart.

Running this command once should take care of it:
```

echo ath_pci | sudo tee -a /etc/modules
```

If not, let us know.

---

### Post by l_synapse_l on 2009-01-12
Sorry I didn't post earlier. But I found the exact same command above [adding to /etc/modules] on this thread and it worked [Should have read the thread properly :)]. This community is really great. Thanks pytheas22.

OT : Can someone point me to a good link which explains the linux configuration files and things like how the kernel loads diff. modules etc. I am a programmer I should pick it up fast.

---

### Post by pytheas22 on 2009-01-12
> Can someone point me to a good link which explains the linux configuration files and things like how the kernel loads diff. modules etc. I am a programmer I should pick it up fast.

[This site]("http://tldp.org/LDP/lkmpg/2.6/html/") is a nice guide.  It's old but most of it is still accurate.  Section 1.2 in particular explains how the kernel knows to load modules.

---

### Post by l_synapse_l on 2009-01-12
> **pytheas22 said:**
> [This site]("http://tldp.org/LDP/lkmpg/2.6/html/") is a nice guide.  It's old but most of it is still accurate.  Section 1.2 in particular explains how the kernel knows to load modules.

Thanks again. I have got most things working smoothly on this laptop now. Time to fire up remastersys and make a custom backup iso.

---

### Post by arm-c on 2009-02-02
All, while it sounds like the users here are doing fine with the hardware buttons (with one exception), I thought I would post a link to a python/gui utility that I created to turn on/off the wireless/bluetooth hardware.  It requires the AcerHK driver.

[http://acerhkgui.sourceforge.net](http://acerhkgui.sourceforge.net)

Hope it helps someone.  Any suggestions/contributions, please let me know. :)

Oh, the readme file there addresses the wireless LED setting if someone is missing that.

---

### Post by nikolaiortiz on 2009-04-15
well i back.. has been long time..

well my wireless is working fine..
the only thing is that annoying message 

ForceXPAon: 0

on dmesg

i try to catch other bugs and things but dmesg is full of this 

ForceXPAon: 0

some help please.

---

### Post by pytheas22 on 2009-04-15
**nikolaiortiz**: according to this [bug report]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/325469"), the issue with spamming in dmesg was fixed in February on Ubuntu 8.10.  Make sure you have the interpid-backports repository enabled (go to System>Administration>Software Sources and click on the 'Updates' tab to enable it), then update your system.  Alternatively, if you wait a week, you can upgrade to Ubuntu 9.04 and the issue should not exist there.

If none of the above helps, we can look into other options.

---

### Post by hanzo_kunai on 2009-05-30
i've brought acer 4535 both wireless and ethernet is not working
wireless is using AR5B91.. can someone help me??:(

---

### Post by pytheas22 on 2009-05-30
**hanzo_kunai**: please open a terminal, run the following commands and post the output:
```

lshw -C Network
lspci -nn
dmesg | grep -e ath -e wlan
sudo iwlist scan
uname -rm
```

You can copy the terminal output into a text file (Applications>Accessories>Text Editor), then use a USB drive to transfer the text file to a computer with Internet access, so that you can easily copy and paste it here.

---

### Post by hanzo_kunai on 2009-05-30
lshw -C Network
 *-network UNCLAIMED     
       description: Network controller
       product: Atheros Communications Inc.
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:05:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix bus_master cap_list
       configuration: latency=0
  *-network UNCLAIMED
       description: Ethernet controller
       product: Attansic Technology Corp.
       vendor: Attansic Technology Corp.
       physical id: 0
       bus info: pci@0000:06:00.0
       version: c0
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress vpd bus_master cap_list
       configuration: latency=0
lspci -nn
00:00.0 Host bridge [0600]: Advanced Micro Devices [AMD] RS780 Host Bridge [1022:9600]
00:01.0 PCI bridge [0604]: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (int gfx) [1022:9602]
00:06.0 PCI bridge [0604]: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 2) [1022:9606]
00:07.0 PCI bridge [0604]: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 3) [1022:9607]
00:11.0 SATA controller [0106]: ATI Technologies Inc SB700/SB800 SATA Controller [AHCI mode] [1002:4391]
00:12.0 USB Controller [0c03]: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller [1002:4397]
00:12.1 USB Controller [0c03]: ATI Technologies Inc SB700/SB800 USB OHCI1 Controller [1002:4398]
00:12.2 USB Controller [0c03]: ATI Technologies Inc SB700/SB800 USB EHCI Controller [1002:4396]
00:13.0 USB Controller [0c03]: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller [1002:4397]
00:13.2 USB Controller [0c03]: ATI Technologies Inc SB700/SB800 USB EHCI Controller [1002:4396]
00:14.0 SMBus [0c05]: ATI Technologies Inc SBx00 SMBus Controller [1002:4385] (rev 3a)
00:14.2 Audio device [0403]: ATI Technologies Inc SBx00 Azalia [1002:4383]
00:14.3 ISA bridge [0601]: ATI Technologies Inc SB700/SB800 LPC host controller [1002:439d]
00:14.4 PCI bridge [0604]: ATI Technologies Inc SBx00 PCI to PCI Bridge [1002:4384]
00:14.5 USB Controller [0c03]: ATI Technologies Inc SB700/SB800 USB OHCI2 Controller [1002:4399]
00:18.0 Host bridge [0600]: Advanced Micro Devices [AMD] Family 11h HyperTransport Configuration [1022:1300] (rev 40)
00:18.1 Host bridge [0600]: Advanced Micro Devices [AMD] Family 11h Address Map [1022:1301]
00:18.2 Host bridge [0600]: Advanced Micro Devices [AMD] Family 11h DRAM Controller [1022:1302]
00:18.3 Host bridge [0600]: Advanced Micro Devices [AMD] Family 11h Miscellaneous Control [1022:1303]
00:18.4 Host bridge [0600]: Advanced Micro Devices [AMD] Family 11h Link Control [1022:1304]
01:05.0 VGA compatible controller [0300]: ATI Technologies Inc RS780M/RS780MN [Radeon HD 3200 Graphics] [1002:9612]
01:05.1 Audio device [0403]: ATI Technologies Inc RS780 Azalia controller [1002:960f]
05:00.0 Network controller [0280]: Atheros Communications Inc. Unknown device [168c:002a] (rev 01)
06:00.0 Ethernet controller [0200]: Attansic Technology Corp. Unknown device [1969:1063] (rev c0)
dmesg | grep -e ath -e wlan
got nothing
sudo iwlist scan
lo        Interface doesn't support scanning.
uname -rm
2.6.24-16-generic i686

---

### Post by pytheas22 on 2009-05-31
It looks like no driver is claiming either your wireless or ethernet interfaces; I'm not sure why because they both should have good Linux drivers built into the kernel.  But you can try inserting drivers manually by following the instructions below.

To get the ethernet working, please try running this command:
```

sudo modprobe atl1
```

Then plug in an ethernet cable and see if you're able to connect (or at least check to see if the 'ifconfig' command or the NetworkManager applet recognizes an ethernet device).  If not, you can try a second driver by typing:
```

sudo rmmod atl1
sudo modprobe atl2
```

As for the wireless, try typing:
```

sudo modprobe ath5k
```

If that doesn't work, try running:
```

sudo rmmod ath5k
sudo modprobe ath9k
```

If this doesn't solve the problem, please post the output of these commands (before rebooting your computer):
```

lshw -C Network
lsmod | grep -e ath -e atl
dmesg | grep -e ath -e atl -e wlan -e eth
```

---

### Post by Beware The Birchmen on 2009-07-01
Hi guys :guitar:

I am on this laptop and the wireless detects networks but every time I tried to connect it keeps booting back to the screen where you put your key in like it can't connect. Ethernet works fine but I really need to use wifi. Thanks for your help!

---

### Post by Beware The Birchmen on 2009-07-01
oh yeah Im on 9.04:KS

---

### Post by Beware The Birchmen on 2009-07-01
> **pytheas22 said:**
> It looks like no driver is claiming either your wireless or ethernet interfaces; I'm not sure why because they both should have good Linux drivers built into the kernel.  But you can try inserting drivers manually by following the instructions below.

To get the ethernet working, please try running this command:
```

sudo modprobe atl1
```Then plug in an ethernet cable and see if you're able to connect (or at least check to see if the 'ifconfig' command or the NetworkManager applet recognizes an ethernet device).  If not, you can try a second driver by typing:
```

sudo rmmod atl1
sudo modprobe atl2
```As for the wireless, try typing:
```

sudo modprobe ath5k
```If that doesn't work, try running:
```

sudo rmmod ath5k
sudo modprobe ath9k
```If this doesn't solve the problem, please post the output of these commands (before rebooting your computer):
```

lshw -C Network
lsmod | grep -e ath -e atl
dmesg | grep -e ath -e atl -e wlan -e eth
```
I tried this and it got two green dots for a little while (usual stays at one)
using the sudo modprobe ath5k command. any advice?

---

### Post by pytheas22 on 2009-07-02
Beware The Birchmen: what kind of encryption is your network using?  Can you connect if you turn security off?

You may have better luck if you use wicd instead of NetworkManager to connect.  You can install wicd by typing:
```

sudo apt-get install wicd
```

(you will need to be connected to the Internet for that command to work; if ít's impossible for you to plug in temporarily, let me know).

Then launch wicd from the Applications>Internet menu and try connecting with it.

If wicd doesn't help, please post the output of these commands so I'll know more about your setup:
```

sudo iwlist scan
lshw -C Network
lspci -nn
uname -rm
```

Plesae also tell me the name of the network you're trying to connect to.

---

### Post by Beware The Birchmen on 2009-07-02
Hi pytheas22 thanks for the reply
wicd seems to want to remove my network connection when I tried to install it? if wicd ends up not working is there any easy way to recover the default network manager?

---

### Post by Beware The Birchmen on 2009-07-02
pytheas22 thank you for the suggestion!
went ahead and tried it anyway and it connected first try.

anything I should know about this new network manager?

---

### Post by pytheas22 on 2009-07-02
Yes, you can't have both wicd and NetworkManager installed at the same time.  If you ever want NM back, you can type:
```

sudo apt-get install network-manager-gnome
```

But since wicd works, I don't suppose you'll ever need to do that.

There's not really anything special you need to know about wicd.  It lacks some of the features of NetworkManager, like VPN support or being able to connect to multiple networks at once, but for normal use it should be fine.

---

### Post by Beware The Birchmen on 2009-07-03
> **pytheas22 said:**
> Yes, you can't have both wicd and NetworkManager installed at the same time.  If you ever want NM back, you can type:
```

sudo apt-get install network-manager-gnome
```But since wicd works, I don't suppose you'll ever need to do that.

There's not really anything special you need to know about wicd.  It lacks some of the features of NetworkManager, like VPN support or being able to connect to multiple networks at once, but for normal use it should be fine.
Awesome. Thanks again for the help, finally up and running and everything seems smooth now that the wireless is working.8-)

---

### Post by hanzo_kunai on 2009-08-20
help me on this please

*-network UNCLAIMED
       description: Ethernet controller
       product: Attansic Technology Corp.
       vendor: Attansic Technology Corp.
       physical id: 0
       bus info: pci@0000:06:00.0
       version: c0
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress vpd bus_master cap_list
       configuration: latency=0
00:00.0 Host bridge: Advanced Micro Devices [AMD] RS780 Host Bridge
00:01.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (int gfx)
00:06.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 2)
00:07.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 3)
00:11.0 SATA controller: ATI Technologies Inc SB700/SB800 SATA Controller [AHCI mode]
00:12.0 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller
00:12.1 USB Controller: ATI Technologies Inc SB700 USB OHCI1 Controller
00:12.2 USB Controller: ATI Technologies Inc SB700/SB800 USB EHCI Controller
00:13.0 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller
00:13.2 USB Controller: ATI Technologies Inc SB700/SB800 USB EHCI Controller
00:14.0 SMBus: ATI Technologies Inc SBx00 SMBus Controller (rev 3a)
00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia (Intel HDA)
00:14.3 ISA bridge: ATI Technologies Inc SB700/SB800 LPC host controller
00:14.4 PCI bridge: ATI Technologies Inc SBx00 PCI to PCI Bridge
00:14.5 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI2 Controller
00:18.0 Host bridge: Advanced Micro Devices [AMD] Family 11h HyperTransport Configuration (rev 40)
00:18.1 Host bridge: Advanced Micro Devices [AMD] Family 11h Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] Family 11h DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] Family 11h Miscellaneous Control
00:18.4 Host bridge: Advanced Micro Devices [AMD] Family 11h Link Control
01:05.0 VGA compatible controller: ATI Technologies Inc RS780M/RS780MN [Radeon HD 3200 Graphics]
01:05.1 Audio device: ATI Technologies Inc RS780 Azalia controller
05:00.0 Network controller: Atheros Communications Inc. AR928X Wireless Network Adapter (PCI-Express) (rev 01)
06:00.0 Ethernet controller: Attansic Technology Corp. Device 1063 (rev c0)

2.6.28-15-generic
 i'm using jaunty

---

### Post by pytheas22 on 2009-08-20
hanzo_kunai: I assume you want the ethernet to work?  Wireless is not the problem?  Either way, I'll need a little more information.  Please post the output of:
```

lshw -C Network
uname -r
dmesg | grep -e atl -e eth -e wlan -e ath
lspci -nn | grep -ie ethernet -e network
```

---

### Post by Statik on 2009-08-21
New 4530 running 9.04 AMD64.
NDISWRAPPER installed.
Wireless shows as disabled. Not able to enable.

```
statik@statik-laptop:~/Atheros$ lshw -C Network
WARNING: you should run this program as super-user.
  *-network               
       description: Ethernet interface
       product: NetXtreme BCM5764M Gigabit Ethernet PCIe
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:08:00.0
       logical name: eth3
       version: 10
       serial: 00:23:8b:46:90:1a
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=tg3 driverversion=3.94 ip=192.168.2.104 latency=0 module=tg3 multicast=yes
  *-network DISABLED
       description: Wireless interface
       product: AR928X Wireless Network Adapter (PCI-Express)
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:0b:00.0
       logical name: wmaster0
       version: 01
       serial: 00:17:c4:56:06:c4
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=ath9k latency=0 module=ath9k multicast=yes wireless=IEEE 802.11bgn
  *-network DISABLED
       description: Ethernet interface
       physical id: 2
       logical name: pan0
       serial: 62:e7:01:64:c3:6c
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A multicast=yes

```

```
statik@statik-laptop:~/Atheros$ uname -r
2.6.28-13-generic
```

```
statik@statik-laptop:~/Atheros$ dmesg | grep -e atl -e eth -e wlan -e ath
[    1.830673] Driver 'sd' needs updating - please use bus_type methods
[    1.830682] Driver 'sr' needs updating - please use bus_type methods
[    4.769657] device-mapper: multipath: version 1.0.5 loaded
[    4.769660] device-mapper: multipath round-robin: version 1.0.0 loaded
[    5.684955] eth0: Tigon3 [partno(BCM95764M) rev 5784100 PHY(5784)] (PCI Express) 10/100/1000Base-T Ethernet 00:23:8b:46:90:1a
[    5.684960] eth0: RXcsums[1] LinkChgREG[0] MIirq[0] ASF[0] WireSpeed[1] TSOcap[1]
[    5.684962] eth0: dma_rwctrl[76180000] dma_mask[64-bit]
[   10.327586] udev: renamed network interface eth0 to eth3
[   11.310166] ath9k: 0.1
[   11.310221] ath9k 0000:0b:00.0: PCI INT A -> Link[Z00O] -> GSI 21 (level, low) -> IRQ 21
[   11.310231] ath9k 0000:0b:00.0: setting latency timer to 64
[   11.737676] phy0: Selected rate control algorithm 'ath9k_rate_control'
[   11.764658] Registered led device: ath9k-phy0:radio
[   11.764702] Registered led device: ath9k-phy0:assoc
[   11.764740] Registered led device: ath9k-phy0:tx
[   11.764775] Registered led device: ath9k-phy0:rx
[   11.807846] udev: renamed network interface wlan0 to wlan1
[  350.440809] ADDRCONF(NETDEV_UP): eth3: link is not ready
[  350.817022] ADDRCONF(NETDEV_UP): wlan1: link is not ready
[  352.065969] tg3: eth3: Link is up at 100 Mbps, full duplex.
[  352.065973] tg3: eth3: Flow control is on for TX and on for RX.
[  352.154250] ADDRCONF(NETDEV_CHANGE): eth3: link becomes ready
[  362.680029] eth3: no IPv6 routers present
```

```
statik@statik-laptop:~/Atheros$ lspci -nn | grep -ie ethernet -e network
08:00.0 Ethernet controller [0200]: Broadcom Corporation NetXtreme BCM5764M Gigabit Ethernet PCIe [14e4:1684] (rev 10)
0b:00.0 Network controller [0280]: Atheros Communications Inc. AR928X Wireless Network Adapter (PCI-Express) [168c:002a] (rev 01)

```

Can anyone assist me?

Thanks,
Statik

---

### Post by pytheas22 on 2009-08-21
Statik: according to 'lshw -C Network', your card is DISABLED.  Most often that means the radio is turned off via a physical switch on your computer or a hotkey (like function_F2).  Please make sure this is not the problem.

If you're certain the card isn't simply turned off, please run the following commands (in this order) and post the output:

```
sudo rmmod ath9k
sudo rmmod ndiswrapper
sudo modprobe ndiswrapper
lshw -C Network
dmesg | grep -e ndis -e wlan
sudo iwlist scan
ndiswrapper -l
uname -rm
```

---

### Post by Statik on 2009-08-22
Yes, the card is disabled. There isn't a slide switch to enable it, only the 5-hot keys on the side. Since I'm running AMD64, acerHK isn't supposed to work (Although I haven't installed it yet) so I don't know how to enable the card otherwise. That is what I'm trying to find out.

A previous poster mentioned System->administration->network, but I only have network tools there which doesn't offer the option to enable.

Any other ideas?

Statik

---

### Post by pytheas22 on 2009-08-22
> Yes, the card is disabled. There isn't a slide switch to enable it, only the 5-hot keys on the side. Since I'm running AMD64, acerHK isn't supposed to work (Although I haven't installed it yet) so I don't know how to enable the card otherwise. That is what I'm trying to find out.

A previous poster mentioned System->administration->network, but I only have network tools there which doesn't offer the option to enable.

Any other ideas?

ndiswrapper is worth a try.  You said you already installed it, but according to the output you posted above, ath9k is still controlling your card.  If you could please run the commands from my last post (#81), they'll remove the ath9k module and replace it with ndiswrapper, which will let you know whether ndiswrapper is going to work better, or try compiling a more recent version of ath9k, or a more recent kernel.

You could also try using 32-bit Ubuntu, where ath9k might work better.

---

### Post by Statik on 2009-08-22
OK, this is weird. I had the laptop turned off last night, and when I turned it on this morning, not only does the wireless work, but the wireless LED is flickering with data transfer. Its off otherwise, but everything seems to work.

My problem is apparently solved, but would you like me to post any command line outputs?

Statik

---

### Post by Statik on 2009-08-22
OK, had a few other issues so I thought I'd reinstall 9.04 64bit. Everything seems smoother, except for wireless. I tried setting up ndiswrapper as in this thread, but now I have no wireless. Here is my outputs, again. :)

```
statik@statik-laptop:~$ lshw -C Network
WARNING: you should run this program as super-user.
  *-network               
       description: Ethernet interface
       product: NetXtreme BCM5764M Gigabit Ethernet PCIe
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:08:00.0
       logical name: eth0
       version: 10
       serial: 00:23:8b:46:90:1a
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=tg3 driverversion=3.94 ip=192.168.2.104 latency=0 module=tg3 multicast=yes
  *-network UNCLAIMED
       description: Network controller
       product: AR928X Wireless Network Adapter (PCI-Express)
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:0b:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: latency=0
  *-network DISABLED
       description: Ethernet interface
       physical id: 2
       logical name: pan0
       serial: 5e:f4:1b:d0:53:f6
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A multicast=yes

```

```
statik@statik-laptop:~$ uname -r
2.6.28-15-generic

```

```
statik@statik-laptop:~$ dmesg | grep -e atl -e eth -e wlan -e ath
[    1.810700] Driver 'sd' needs updating - please use bus_type methods
[    1.810709] Driver 'sr' needs updating - please use bus_type methods
[    4.749491] device-mapper: multipath: version 1.0.5 loaded
[    4.749494] device-mapper: multipath round-robin: version 1.0.0 loaded
[    5.676958] eth0: Tigon3 [partno(BCM95764M) rev 5784100 PHY(5784)] (PCI Express) 10/100/1000Base-T Ethernet 00:23:8b:46:90:1a
[    5.676963] eth0: RXcsums[1] LinkChgREG[0] MIirq[0] ASF[0] WireSpeed[1] TSOcap[1]
[    5.676966] eth0: dma_rwctrl[76180000] dma_mask[64-bit]
[   22.384636] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   24.030768] tg3: eth0: Link is up at 100 Mbps, full duplex.
[   24.030772] tg3: eth0: Flow control is on for TX and on for RX.
[   24.031220] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[   34.101013] eth0: no IPv6 routers present

```

I also have ath9k blacklisted.

statik

---

### Post by pytheas22 on 2009-08-23
> I also have ath9k blacklisted.

Did you install ndiswrapper again and load the Windows drivers into it since reinstalling Ubuntu?  You would need to do that before ndiswrapper can drive the device (assuming ndiswrapper will work).

If you did install ndiswrapper but it's still not working, please post the output of:
```

lsmod | grep ndis
sudo modprobe ndiswrapper
ndiswrapper -l
dmesg | grep -e ndis -e wlan
uname -rm
```

---

### Post by Statik on 2009-08-23
```
statik@statik-laptop:~$ lsmod | grep ndis
ndiswrapper           250624  0 
statik@statik-laptop:~$ sudo modprobe ndiswrapper
[sudo] password for statik: 
WARNING: All config files need .conf: /etc/modprobe.d/blacklist, it will be ignored in a future release.
statik@statik-laptop:~$ ndiswrapper -l
WARNING: All config files need .conf: /etc/modprobe.d/blacklist, it will be ignored in a future release.
netathwx : driver installed
	device (168C:002A) present (alternate driver: ath9k)
statik@statik-laptop:~$ dmesg | grep -e ndis -e wlan
[   11.942515] ndiswrapper version 1.53 loaded (smp=yes, preempt=no)
[   12.050761] ndiswrapper (link_pe_images:575): fixing KI_USER_SHARED_DATA address in the driver
[   12.056958] ndiswrapper (link_pe_images:603): DLL initialize failed for athwx.sys
[   12.057063] ndiswrapper: driver netathwx (,03/13/2009,7.7.0.259) loaded
[   12.057435] ndiswrapper 0000:0b:00.0: PCI INT A -> Link[Z00O] -> GSI 21 (level, low) -> IRQ 21
[   12.057444] ndiswrapper (mp_init:210): assuming WDM (non-NDIS) driver
[   12.057510] usbcore: registered new interface driver ndiswrapper
statik@statik-laptop:~$ uname -rm
2.6.28-15-generic x86_64
```

I had to go looking for the driver as I had followed the instructions at the beginning of this thread but they were for the ath5211 driver. This one reports ok, but nothing appears in network manager yet.

Statik

edit:
```
statik@statik-laptop:~$ lshw -C Network
WARNING: you should run this program as super-user.
  *-network               
       description: Ethernet interface
       product: NetXtreme BCM5764M Gigabit Ethernet PCIe
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:08:00.0
       logical name: eth0
       version: 10
       serial: 00:23:8b:46:90:1a
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=tg3 driverversion=3.94 ip=192.168.2.102 latency=0 module=tg3 multicast=yes
  *-network
       description: Network controller
       product: AR928X Wireless Network Adapter (PCI-Express)
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:0b:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: driver=ndiswrapper latency=0 module=ndiswrapper
  *-network DISABLED
       description: Ethernet interface
       physical id: 2
       logical name: pan0
       serial: 82:da:58:a7:13:59
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A multicast=yes

```

---

### Post by pytheas22 on 2009-08-23
hmmm, this is strange.  It looks like there are problems with ndiswrapper bringing up the card, but it's not clear exactly what's wrong.  Can you see any networks if you type:
```

sudo iwlist scan
```

---

### Post by Statik on 2009-08-23
```
statik@statik-laptop:~$ sudo iwlist scan
[sudo] password for statik: 
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

pan0      Interface doesn't support scanning.

```

Statik

---

### Post by cimbom on 2009-08-23
Hi everyone - 

I am new to Ubuntu. I have recently put together a desktop and i cannot get a connection via ethernet. From what I can tell, you all have been discussing similar problems here (plus wireless issues). If I need to post somewhere else, please let me know. 

I have a GIGABYTE G31M-ES2L Version 2 Mobo. I have installed Ubuntu 9.04 2 days ago. Cannot get a wired connection though. Here is my setup


 uname -rm
2.6.28-11-generic i686

lspci -nn

00:00.0 Host bridge [0600]: Intel Corporation 82G33/G31/P35/P31 Express DRAM Controller [8086:29c0] (rev 10)
00:02.0 VGA compatible controller [0300]: Intel Corporation 82G33/G31 Express Integrated Graphics Controller [8086:29c2] (rev 10)
00:1b.0 Audio device [0403]: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller [8086:27d8] (rev 01)
00:1c.0 PCI bridge [0604]: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 [8086:27d0] (rev 01)
00:1c.1 PCI bridge [0604]: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 [8086:27d2] (rev 01)
00:1d.0 USB Controller [0c03]: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 [8086:27c8] (rev 01)
00:1d.1 USB Controller [0c03]: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 [8086:27c9] (rev 01)
00:1d.2 USB Controller [0c03]: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 [8086:27ca] (rev 01)
00:1d.3 USB Controller [0c03]: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 [8086:27cb] (rev 01)
00:1d.7 USB Controller [0c03]: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller [8086:27cc] (rev 01)
00:1e.0 PCI bridge [0604]: Intel Corporation 82801 PCI Bridge [8086:244e] (rev e1)
00:1f.0 ISA bridge [0601]: Intel Corporation 82801GB/GR (ICH7 Family) LPC Interface Bridge [8086:27b8] (rev 01)
00:1f.2 IDE interface [0101]: Intel Corporation 82801GB/GR/GH (ICH7 Family) SATA IDE Controller [8086:27c0] (rev 01)
00:1f.3 SMBus [0c05]: Intel Corporation 82801G (ICH7 Family) SMBus Controller [8086:27da] (rev 01)
02:00.0 Ethernet controller [0200]: Attansic Technology Corp. Device [1969:1063] (rev c0)

ifconfig -a
lo        

Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:24 errors:0 dropped:0 overruns:0 frame:0
          TX packets:24 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:1700 (1.7 KB)  TX bytes:1700 (1.7 KB)
pan0      

Link encap:Ethernet  HWaddr a2:c0:31:31:2d:0d  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

lshw -C network

  *-network UNCLAIMED     
            description: Ethernet controller
            product: Attansic Technology Corp.
            vendor: Attansic Technology Corp.
            physical id: 0
       bus info: pci@0000:02:00.0
            version: c0
            width: 64 bits
            clock: 33MHz
            capabilities: pm msi pciexpress vpd bus_master cap_list
            configuration: latency=0
  *-network DISABLED
            description: Ethernet interface
            physical id: 1
            logical name: pan0
            serial: a2:c0:31:31:2d:0d
            capabilities: ethernet physical
            configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes


As you can see no eth0, I cannot enable the network. Ethernet controller is attansic device 1063. 

If anyone can point me to the right direction, I would appreciate it. 

Cimbom...

---

### Post by Statik on 2009-08-23
Tried adding the backports as mentioned in another thread but it didn't fix anything. Still have everything looking like its working, but no wlan0 or similar device. Any ideas yet?

```
statik@statik-laptop:~$ lshw -C network
WARNING: you should run this program as super-user.
  *-network               
       description: Ethernet interface
       product: NetXtreme BCM5764M Gigabit Ethernet PCIe
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:08:00.0
       logical name: eth0
       version: 10
       serial: 00:23:8b:46:90:1a
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=tg3 driverversion=3.94 ip=192.168.2.102 latency=0 module=tg3 multicast=yes
  *-network
       description: Network controller
       product: AR928X Wireless Network Adapter (PCI-Express)
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:0b:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: driver=ndiswrapper latency=0 module=ndiswrapper
  *-network DISABLED
       description: Ethernet interface
       physical id: 2
       logical name: pan0
       serial: 36:95:69:42:5c:a4
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A multicast=yes

```

BTW, thanks for all the help you are doing not only for me but for so many others, pytheas22!

Statik

---

### Post by pytheas22 on 2009-08-24
**cimbom**: yes, please start a new thread for your issue so that things don't become too confusing here.  In your new thread, please include the output you've already posted, as well as:
```

dmesg | grep -e eth -e atl
```

Statik: I'm not sure what's going on with ndiswrapper, but it looks like it's probably not going to work.  I think the next best thing to try is to recompile your ath9k driver using the latest code.  To do that, first go to [http://linuxwireless.org/download/compat-wireless-2.6](http://linuxwireless.org/download/compat-wireless-2.6) and download the file named "compat-wireless-2.6.tar.bz2."  Save it to your desktop. Then run these commands:
```

cd ~/Desktop
sudo apt-get install build-essential
tar -xjvf compat-wireless-2.6.tar.bz2
cd compat-wireless*
make
sudo make unload
sudo make load
sudo make install
```

Then unblacklist ath9k, and reboot.  Does this help?  If not, what is the output of:
```

dmesg | grep -e ath -e wlan
modinfo ath9k
```

---

### Post by Statik on 2009-08-24
Nothing for wireless seems to be loaded.
I noticed that while it was compiling, the compat drivers complained of madwifi being installed and disabled madwifi. I didn't install madwifi.

Here is the output:
```
statik@statik-laptop:~$ dmesg | grep -e ath -e wlan
[    5.057528] device-mapper: multipath: version 1.0.5 loaded
[    5.057531] device-mapper: multipath round-robin: version 1.0.0 loaded
[   12.631978] ndiswrapper (link_pe_images:603): DLL initialize failed for athwx.sys
[   12.632043] ndiswrapper: driver netathwx (,03/13/2009,7.7.0.259) loaded
statik@statik-laptop:~$ modinfo ath9k
filename:       /lib/modules/2.6.28-15-generic/updates/ath9k.ko
license:        Dual BSD/GPL
description:    Support for Atheros 802.11n wireless LAN cards.
author:         Atheros Communications
srcversion:     B066EA404154EA4DD8862D0
alias:          pci:v0000168Cd0000002Bsv*sd*bc*sc*i*
alias:          pci:v0000168Cd0000002Asv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000029sv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000027sv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000024sv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000023sv*sd*bc*sc*i*
depends:        lbm_cw-cfg80211,lbm_cw-mac80211,led-class
vermagic:       2.6.28-15-generic SMP mod_unload modversions 
parm:           nohwcrypt:Disable hardware encryption (int)
parm:           btcoex_enable:Enable Bluetooth coexistence support (bool)
```

Thanks,

Statik

---

### Post by pytheas22 on 2009-08-24
It looks like ath9k is not loading.  Did you unblacklist it?  If you did, try running this command to tell the system also to load it explicitly:
```

echo ath9k | sudo tee -a /etc/modules
```

Then reboot and see if anything changes.

---

### Post by Statik on 2009-08-24
No, nothing has changed. I'm now worse off than before. There are no wireless devices at all. Hopefully we can get this working. :)

```
statik@statik-laptop:~$ lshw -C Network
WARNING: you should run this program as super-user.
  *-network               
       description: Ethernet interface
       product: NetXtreme BCM5764M Gigabit Ethernet PCIe
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:08:00.0
       logical name: eth0
       version: 10
       serial: 00:23:8b:46:90:1a
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=tg3 driverversion=3.94 ip=192.168.2.102 latency=0 module=tg3 multicast=yes
  *-network
       description: Network controller
       product: AR928X Wireless Network Adapter (PCI-Express)
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:0b:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: driver=ndiswrapper latency=0 module=ndiswrapper
  *-network DISABLED
       description: Ethernet interface
       physical id: 2
       logical name: pan0
       serial: de:4b:fe:9b:dc:4d
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A multicast=yes
statik@statik-laptop:~$ dmesg | grep -e atl -e eth -e wlan -e ath
[    1.814675] Driver 'sd' needs updating - please use bus_type methods
[    1.814683] Driver 'sr' needs updating - please use bus_type methods
[    4.749483] device-mapper: multipath: version 1.0.5 loaded
[    4.749486] device-mapper: multipath round-robin: version 1.0.0 loaded
[    5.688966] eth0: Tigon3 [partno(BCM95764M) rev 5784100 PHY(5784)] (PCI Express) 10/100/1000Base-T Ethernet 00:23:8b:46:90:1a
[    5.688971] eth0: RXcsums[1] LinkChgREG[0] MIirq[0] ASF[0] WireSpeed[1] TSOcap[1]
[    5.688973] eth0: dma_rwctrl[76180000] dma_mask[64-bit]
[   12.328693] ndiswrapper (link_pe_images:603): DLL initialize failed for athwx.sys
[   12.328775] ndiswrapper: driver netathwx (,03/13/2009,7.7.0.259) loaded
[   22.412596] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   24.037986] tg3: eth0: Link is up at 100 Mbps, full duplex.
[   24.037990] tg3: eth0: Flow control is on for TX and on for RX.
[   24.038933] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[   34.361031] eth0: no IPv6 routers present
statik@statik-laptop:~$ sudo iwlist scan
[sudo] password for statik: 
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

pan0      Interface doesn't support scanning.

statik@statik-laptop:~$ lspci -nn | grep -ie ethernet -e network
08:00.0 Ethernet controller [0200]: Broadcom Corporation NetXtreme BCM5764M Gigabit Ethernet PCIe [14e4:1684] (rev 10)
0b:00.0 Network controller [0280]: Atheros Communications Inc. AR928X Wireless Network Adapter (PCI-Express) [168c:002a] (rev 01)
statik@statik-laptop:~$
```

Statik

---

### Post by pytheas22 on 2009-08-24
It looks like ath9k is still not even trying to claim the card, but I'm not sure why.  What happens if you type:
```

lsmod | grep -e ndis -e ath
sudo rmmod ndiswrapper
sudo rmmod ath9k
sudo modprobe ath9k
dmesg | grep -e ath -e wlan
```

---

### Post by Statik on 2009-08-25
```
statik@statik-laptop:~$ lsmod | grep -e ndis -e ath
ndiswrapper           250624  0 
statik@statik-laptop:~$ sudo rmmod ndiswrapper
[sudo] password for statik: 
Killed
statik@statik-laptop:~$ sudo rmmod ath9k
ERROR: Module ath9k does not exist in /proc/modules
statik@statik-laptop:~$ sudo modprobe ath9k
WARNING: All config files need .conf: /etc/modprobe.d/blacklist, it will be ignored in a future release.
WARNING: Error inserting lbm_cw_mac80211 (/lib/modules/2.6.28-15-generic/updates/lbm_cw-mac80211.ko): Invalid module format
FATAL: Error inserting ath9k (/lib/modules/2.6.28-15-generic/updates/ath9k.ko): Invalid module format
statik@statik-laptop:~$ dmesg | grep -e ath -e wlan
[    4.749483] device-mapper: multipath: version 1.0.5 loaded
[    4.749486] device-mapper: multipath round-robin: version 1.0.0 loaded
[   12.328693] ndiswrapper (link_pe_images:603): DLL initialize failed for athwx.sys
[   12.328775] ndiswrapper: driver netathwx (,03/13/2009,7.7.0.259) loaded
[52812.725348]  [<ffffffff8021253a>] system_call_fastpath+0x16/0x1b
statik@statik-laptop:~$
```

That doesn't look good. Perhaps the module didn't compile right. I'll recompile and post the output . . .
As you can see, I redirected the output from stdout to a text file. Here are the errors that appeared in stderr as well:
```
statik@statik-laptop:~/Desktop/compat-wireless-2009-08-24$ make > make.txt
/home/statik/Desktop/compat-wireless-2009-08-24/drivers/net/wireless/b43/main.c: In function ‘b43_request_firmware’:
/home/statik/Desktop/compat-wireless-2009-08-24/drivers/net/wireless/b43/main.c:2248: warning: format not a string literal and no format arguments
/home/statik/Desktop/compat-wireless-2009-08-24/drivers/net/wireless/b43/phy_lp.c:386: warning: ‘lpphy_restore_dig_flt_state’ defined but not used
/home/statik/Desktop/compat-wireless-2009-08-24/drivers/net/wireless/b43/phy_lp.c:894: warning: ‘lpphy_disable_rx_gain_override’ defined but not used
/home/statik/Desktop/compat-wireless-2009-08-24/drivers/net/wireless/ipw2x00/libipw_wx.c: In function ‘libipw_wx_set_encodeext’:
/home/statik/Desktop/compat-wireless-2009-08-24/drivers/net/wireless/ipw2x00/libipw_wx.c:622: warning: format not a string literal and no format arguments
/home/statik/Desktop/compat-wireless-2009-08-24/drivers/net/wireless/iwlwifi/iwl-power.c: In function ‘__check_no_sleep_autoadjust’:
/home/statik/Desktop/compat-wireless-2009-08-24/drivers/net/wireless/iwlwifi/iwl-power.c:57: warning: return from incompatible pointer type
/home/statik/Desktop/compat-wireless-2009-08-24/net/wireless/scan.c: In function ‘cfg80211_bss_update’:
/home/statik/Desktop/compat-wireless-2009-08-24/net/wireless/scan.c:422: warning: unused variable ‘used’

```

The text file is too big to upload in one piece, so I've had to compress it.

I did not proceed with the unload, etc. at this point, since I had already done that before. Perhaps there is something in the errors?

Statik

---

### Post by pytheas22 on 2009-08-25
The warnings you receive while compiling compat-wireless should be alright, as long as they're just warnings and not errors.

Have you rebooted since doing the recompile?  In my experience, the "invalid module format" problem goes away after a reboot.

You should also take ath9k off your /etc/modprobe.d/blacklist.conf file; that shouldn't be a problem here, but it can't hurt.

---

### Post by Statik on 2009-08-25
```
statik@statik-laptop:~$ dmesg | grep -e ath -e wlan
[    4.741481] device-mapper: multipath: version 1.0.5 loaded
[    4.741485] device-mapper: multipath round-robin: version 1.0.0 loaded
```
```
statik@statik-laptop:~$ modinfo ath9k
filename:       /lib/modules/2.6.28-15-generic/updates/ath9k.ko
license:        Dual BSD/GPL
description:    Support for Atheros 802.11n wireless LAN cards.
author:         Atheros Communications
srcversion:     B066EA404154EA4DD8862D0
alias:          pci:v0000168Cd0000002Bsv*sd*bc*sc*i*
alias:          pci:v0000168Cd0000002Asv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000029sv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000027sv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000024sv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000023sv*sd*bc*sc*i*
depends:        lbm_cw-cfg80211,lbm_cw-mac80211,led-class
vermagic:       2.6.28-15-generic SMP mod_unload modversions 
parm:           nohwcrypt:Disable hardware encryption (int)
parm:           btcoex_enable:Enable Bluetooth coexistence support (bool)
```
```
statik@statik-laptop:~$ lshw -C Network
WARNING: you should run this program as super-user.
  *-network               
       description: Ethernet interface
       product: NetXtreme BCM5764M Gigabit Ethernet PCIe
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:08:00.0
       logical name: eth0
       version: 10
       serial: 00:23:8b:46:90:1a
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=tg3 driverversion=3.94 ip=192.168.2.102 latency=0 module=tg3 multicast=yes
  *-network UNCLAIMED
       description: Network controller
       product: AR928X Wireless Network Adapter (PCI-Express)
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:0b:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: latency=0
  *-network DISABLED
       description: Ethernet interface
       physical id: 2
       logical name: pan0
       serial: 12:05:0b:05:e1:04
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A multicast=yes
```
```
statik@statik-laptop:~$ cat /etc/modprobe.d/blacklist

statik@statik-laptop:~$ 

```

```
statik@statik-laptop:~$ cat /etc/modules
# /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.

lp
rtc
ath9k

```

Doesn't look like the Ath9k driver is working.

```
statik@statik-laptop:~/Desktop/compat-wireless-2009-08-24$ sudo make unload
[sudo] password for statik: 
statik@statik-laptop:~/Desktop/compat-wireless-2009-08-24$ sudo make load
Loading ipw2100...
WARNING: All config files need .conf: /etc/modprobe.d/blacklist, it will be ignored in a future release.
WARNING: Error inserting mac80211 (/lib/modules/2.6.28-15-generic/updates/net/mac80211/mac80211.ko): Invalid module format
WARNING: Error inserting libipw (/lib/modules/2.6.28-15-generic/updates/libipw.ko): Invalid module format
FATAL: Error inserting ipw2100 (/lib/modules/2.6.28-15-generic/updates/ipw2100.ko): Invalid module format
Loading ipw2200...
WARNING: All config files need .conf: /etc/modprobe.d/blacklist, it will be ignored in a future release.
WARNING: Error inserting mac80211 (/lib/modules/2.6.28-15-generic/updates/net/mac80211/mac80211.ko): Invalid module format
WARNING: Error inserting libipw (/lib/modules/2.6.28-15-generic/updates/libipw.ko): Invalid module format
FATAL: Error inserting ipw2200 (/lib/modules/2.6.28-15-generic/updates/ipw2200.ko): Invalid module format
Loading libertas_cs...
WARNING: All config files need .conf: /etc/modprobe.d/blacklist, it will be ignored in a future release.
FATAL: Error inserting libertas_cs (/lib/modules/2.6.28-15-generic/updates/libertas_cs.ko): Unknown symbol in module, or unknown parameter (see dmesg)
Loading usb8xxx...
WARNING: All config files need .conf: /etc/modprobe.d/blacklist, it will be ignored in a future release.
FATAL: Error inserting usb8xxx (/lib/modules/2.6.28-15-generic/updates/usb8xxx.ko): Unknown symbol in module, or unknown parameter (see dmesg)
Loading p54pci...
WARNING: All config files need .conf: /etc/modprobe.d/blacklist, it will be ignored in a future release.
WARNING: Error inserting lbm_cw_mac80211 (/lib/modules/2.6.28-15-generic/updates/lbm_cw-mac80211.ko): Invalid module format
WARNING: Error inserting p54common (/lib/modules/2.6.28-15-generic/updates/p54common.ko): Invalid module format
FATAL: Error inserting p54pci (/lib/modules/2.6.28-15-generic/updates/p54pci.ko): Invalid module format
Loading p54usb...
WARNING: All config files need .conf: /etc/modprobe.d/blacklist, it will be ignored in a future release.
WARNING: Error inserting lbm_cw_cfg80211 (/lib/modules/2.6.28-15-generic/updates/lbm_cw-cfg80211.ko): Invalid module format
WARNING: Error inserting lbm_cw_mac80211 (/lib/modules/2.6.28-15-generic/updates/lbm_cw-mac80211.ko): Invalid module format
WARNING: Error inserting p54common (/lib/modules/2.6.28-15-generic/updates/p54common.ko): Invalid module format
FATAL: Error inserting p54usb (/lib/modules/2.6.28-15-generic/updates/p54usb.ko): Invalid module format
Loading adm8211...
WARNING: All config files need .conf: /etc/modprobe.d/blacklist, it will be ignored in a future release.
WARNING: Error inserting eeprom_93cx6 (/lib/modules/2.6.28-15-generic/updates/eeprom_93cx6.ko): Invalid module format
WARNING: Error inserting mac80211 (/lib/modules/2.6.28-15-generic/updates/net/mac80211/mac80211.ko): Invalid module format
FATAL: Error inserting adm8211 (/lib/modules/2.6.28-15-generic/updates/drivers/net/wireless/adm8211.ko): Invalid module format
Loading zd1211rw...
WARNING: All config files need .conf: /etc/modprobe.d/blacklist, it will be ignored in a future release.
WARNING: Error inserting lbm_cw_mac80211 (/lib/modules/2.6.28-15-generic/updates/lbm_cw-mac80211.ko): Invalid module format
FATAL: Error inserting zd1211rw (/lib/modules/2.6.28-15-generic/updates/zd1211rw.ko): Invalid module format
Loading rtl8180...
WARNING: All config files need .conf: /etc/modprobe.d/blacklist, it will be ignored in a future release.
WARNING: Error inserting lbm_cw_cfg80211 (/lib/modules/2.6.28-15-generic/updates/lbm_cw-cfg80211.ko): Invalid module format
WARNING: Error inserting lbm_cw_mac80211 (/lib/modules/2.6.28-15-generic/updates/lbm_cw-mac80211.ko): Invalid module format
FATAL: Error inserting rtl8180 (/lib/modules/2.6.28-15-generic/updates/rtl8180.ko): Invalid module format
Loading rtl8187...
WARNING: All config files need .conf: /etc/modprobe.d/blacklist, it will be ignored in a future release.
WARNING: Error inserting lbm_cw_cfg80211 (/lib/modules/2.6.28-15-generic/updates/lbm_cw-cfg80211.ko): Invalid module format
WARNING: Error inserting lbm_cw_mac80211 (/lib/modules/2.6.28-15-generic/updates/lbm_cw-mac80211.ko): Invalid module format
FATAL: Error inserting rtl8187 (/lib/modules/2.6.28-15-generic/updates/rtl8187.ko): Invalid module format
Loading p54pci...
WARNING: All config files need .conf: /etc/modprobe.d/blacklist, it will be ignored in a future release.
WARNING: Error inserting lbm_cw_mac80211 (/lib/modules/2.6.28-15-generic/updates/lbm_cw-mac80211.ko): Invalid module format
WARNING: Error inserting p54common (/lib/modules/2.6.28-15-generic/updates/p54common.ko): Invalid module format
FATAL: Error inserting p54pci (/lib/modules/2.6.28-15-generic/updates/p54pci.ko): Invalid module format
Loading p54usb...
WARNING: All config files need .conf: /etc/modprobe.d/blacklist, it will be ignored in a future release.
WARNING: Error inserting lbm_cw_cfg80211 (/lib/modules/2.6.28-15-generic/updates/lbm_cw-cfg80211.ko): Invalid module format
WARNING: Error inserting lbm_cw_mac80211 (/lib/modules/2.6.28-15-generic/updates/lbm_cw-mac80211.ko): Invalid module format
WARNING: Error inserting p54common (/lib/modules/2.6.28-15-generic/updates/p54common.ko): Invalid module format
FATAL: Error inserting p54usb (/lib/modules/2.6.28-15-generic/updates/p54usb.ko): Invalid module format
Loading iwl3945...
WARNING: All config files need .conf: /etc/modprobe.d/blacklist, it will be ignored in a future release.
WARNING: Error inserting led_class (/lib/modules/2.6.28-15-generic/kernel/drivers/leds/led-class.ko): Invalid module format
WARNING: Error inserting mac80211 (/lib/modules/2.6.28-15-generic/updates/net/mac80211/mac80211.ko): Invalid module format
WARNING: Error inserting lbm_cw_cfg80211 (/lib/modules/2.6.28-15-generic/updates/lbm_cw-cfg80211.ko): Invalid module format
WARNING: Error inserting lbm_cw_mac80211 (/lib/modules/2.6.28-15-generic/updates/lbm_cw-mac80211.ko): Invalid module format
WARNING: Error inserting iwlcore (/lib/modules/2.6.28-15-generic/updates/iwlcore.ko): Invalid module format
FATAL: Error inserting iwl3945 (/lib/modules/2.6.28-15-generic/updates/drivers/net/wireless/iwlwifi/iwl3945.ko): Invalid module format
Loading iwlagn...
WARNING: All config files need .conf: /etc/modprobe.d/blacklist, it will be ignored in a future release.
WARNING: Error inserting mac80211 (/lib/modules/2.6.28-15-generic/updates/net/mac80211/mac80211.ko): Invalid module format
WARNING: Error inserting led_class (/lib/modules/2.6.28-15-generic/kernel/drivers/leds/led-class.ko): Invalid module format
WARNING: Error inserting lbm_cw_cfg80211 (/lib/modules/2.6.28-15-generic/updates/lbm_cw-cfg80211.ko): Invalid module format
WARNING: Error inserting lbm_cw_mac80211 (/lib/modules/2.6.28-15-generic/updates/lbm_cw-mac80211.ko): Invalid module format
WARNING: Error inserting iwlcore (/lib/modules/2.6.28-15-generic/updates/iwlcore.ko): Invalid module format
FATAL: Error inserting iwlagn (/lib/modules/2.6.28-15-generic/updates/drivers/net/wireless/iwlwifi/iwlagn.ko): Invalid module format
Loading ath...
WARNING: All config files need .conf: /etc/modprobe.d/blacklist, it will be ignored in a future release.
FATAL: Error inserting ath (/lib/modules/2.6.28-15-generic/updates/drivers/net/wireless/ath/ath.ko): Invalid module format
Loading ar9170usb...
WARNING: All config files need .conf: /etc/modprobe.d/blacklist, it will be ignored in a future release.
WARNING: Error inserting ath (/lib/modules/2.6.28-15-generic/updates/drivers/net/wireless/ath/ath.ko): Invalid module format
WARNING: Error inserting led_class (/lib/modules/2.6.28-15-generic/kernel/drivers/leds/led-class.ko): Invalid module format
WARNING: Error inserting mac80211 (/lib/modules/2.6.28-15-generic/updates/net/mac80211/mac80211.ko): Invalid module format
FATAL: Error inserting ar9170usb (/lib/modules/2.6.28-15-generic/updates/drivers/net/wireless/ath/ar9170/ar9170usb.ko): Invalid module format
Loading rtl8180...
WARNING: All config files need .conf: /etc/modprobe.d/blacklist, it will be ignored in a future release.
WARNING: Error inserting lbm_cw_cfg80211 (/lib/modules/2.6.28-15-generic/updates/lbm_cw-cfg80211.ko): Invalid module format
WARNING: Error inserting lbm_cw_mac80211 (/lib/modules/2.6.28-15-generic/updates/lbm_cw-mac80211.ko): Invalid module format
FATAL: Error inserting rtl8180 (/lib/modules/2.6.28-15-generic/updates/rtl8180.ko): Invalid module format
Loading rtl8187...
WARNING: All config files need .conf: /etc/modprobe.d/blacklist, it will be ignored in a future release.
WARNING: Error inserting lbm_cw_cfg80211 (/lib/modules/2.6.28-15-generic/updates/lbm_cw-cfg80211.ko): Invalid module format
WARNING: Error inserting lbm_cw_mac80211 (/lib/modules/2.6.28-15-generic/updates/lbm_cw-mac80211.ko): Invalid module format
FATAL: Error inserting rtl8187 (/lib/modules/2.6.28-15-generic/updates/rtl8187.ko): Invalid module format
Loading rt2400pci...
WARNING: All config files need .conf: /etc/modprobe.d/blacklist, it will be ignored in a future release.
WARNING: Error inserting lbm_cw_cfg80211 (/lib/modules/2.6.28-15-generic/updates/lbm_cw-cfg80211.ko): Invalid module format
WARNING: Error inserting lbm_cw_mac80211 (/lib/modules/2.6.28-15-generic/updates/lbm_cw-mac80211.ko): Invalid module format
WARNING: Error inserting input_polldev (/lib/modules/2.6.28-15-generic/kernel/drivers/input/input-polldev.ko): Invalid module format
WARNING: Error inserting led_class (/lib/modules/2.6.28-15-generic/kernel/drivers/leds/led-class.ko): Invalid module format
WARNING: Error inserting rt2x00lib (/lib/modules/2.6.28-15-generic/updates/rt2x00lib.ko): Invalid module format
WARNING: Error inserting rt2x00pci (/lib/modules/2.6.28-15-generic/updates/rt2x00pci.ko): Invalid module format
FATAL: Error inserting rt2400pci (/lib/modules/2.6.28-15-generic/updates/rt2400pci.ko): Invalid module format
Loading rt2500pci...
WARNING: All config files need .conf: /etc/modprobe.d/blacklist, it will be ignored in a future release.
WARNING: Error inserting lbm_cw_cfg80211 (/lib/modules/2.6.28-15-generic/updates/lbm_cw-cfg80211.ko): Invalid module format
WARNING: Error inserting lbm_cw_mac80211 (/lib/modules/2.6.28-15-generic/updates/lbm_cw-mac80211.ko): Invalid module format
WARNING: Error inserting input_polldev (/lib/modules/2.6.28-15-generic/kernel/drivers/input/input-polldev.ko): Invalid module format
WARNING: Error inserting led_class (/lib/modules/2.6.28-15-generic/kernel/drivers/leds/led-class.ko): Invalid module format
WARNING: Error inserting rt2x00lib (/lib/modules/2.6.28-15-generic/updates/rt2x00lib.ko): Invalid module format
WARNING: Error inserting rt2x00pci (/lib/modules/2.6.28-15-generic/updates/rt2x00pci.ko): Invalid module format
FATAL: Error inserting rt2500pci (/lib/modules/2.6.28-15-generic/updates/drivers/net/wireless/rt2x00/rt2500pci.ko): Invalid module format
Loading rt61pci...
WARNING: All config files need .conf: /etc/modprobe.d/blacklist, it will be ignored in a future release.
WARNING: Error inserting lbm_cw_cfg80211 (/lib/modules/2.6.28-15-generic/updates/lbm_cw-cfg80211.ko): Invalid module format
WARNING: Error inserting lbm_cw_mac80211 (/lib/modules/2.6.28-15-generic/updates/lbm_cw-mac80211.ko): Invalid module format
WARNING: Error inserting input_polldev (/lib/modules/2.6.28-15-generic/kernel/drivers/input/input-polldev.ko): Invalid module format
WARNING: Error inserting led_class (/lib/modules/2.6.28-15-generic/kernel/drivers/leds/led-class.ko): Invalid module format
WARNING: Error inserting rt2x00lib (/lib/modules/2.6.28-15-generic/updates/rt2x00lib.ko): Invalid module format
WARNING: Error inserting rt2x00pci (/lib/modules/2.6.28-15-generic/updates/rt2x00pci.ko): Invalid module format
WARNING: Error inserting crc_itu_t (/lib/modules/2.6.28-15-generic/kernel/lib/crc-itu-t.ko): Invalid module format
FATAL: Error inserting rt61pci (/lib/modules/2.6.28-15-generic/updates/rt61pci.ko): Invalid module format
Loading rt2500usb...
WARNING: All config files need .conf: /etc/modprobe.d/blacklist, it will be ignored in a future release.
WARNING: Error inserting lbm_cw_cfg80211 (/lib/modules/2.6.28-15-generic/updates/lbm_cw-cfg80211.ko): Invalid module format
WARNING: Error inserting lbm_cw_mac80211 (/lib/modules/2.6.28-15-generic/updates/lbm_cw-mac80211.ko): Invalid module format
WARNING: Error inserting input_polldev (/lib/modules/2.6.28-15-generic/kernel/drivers/input/input-polldev.ko): Invalid module format
WARNING: Error inserting led_class (/lib/modules/2.6.28-15-generic/kernel/drivers/leds/led-class.ko): Invalid module format
WARNING: Error inserting rt2x00lib (/lib/modules/2.6.28-15-generic/updates/rt2x00lib.ko): Invalid module format
WARNING: Error inserting rt2x00usb (/lib/modules/2.6.28-15-generic/updates/rt2x00usb.ko): Invalid module format
FATAL: Error inserting rt2500usb (/lib/modules/2.6.28-15-generic/updates/rt2500usb.ko): Invalid module format
Loading rt73usb...
WARNING: All config files need .conf: /etc/modprobe.d/blacklist, it will be ignored in a future release.
WARNING: Error inserting lbm_cw_cfg80211 (/lib/modules/2.6.28-15-generic/updates/lbm_cw-cfg80211.ko): Invalid module format
WARNING: Error inserting lbm_cw_mac80211 (/lib/modules/2.6.28-15-generic/updates/lbm_cw-mac80211.ko): Invalid module format
WARNING: Error inserting input_polldev (/lib/modules/2.6.28-15-generic/kernel/drivers/input/input-polldev.ko): Invalid module format
WARNING: Error inserting led_class (/lib/modules/2.6.28-15-generic/kernel/drivers/leds/led-class.ko): Invalid module format
WARNING: Error inserting rt2x00lib (/lib/modules/2.6.28-15-generic/updates/rt2x00lib.ko): Invalid module format
WARNING: Error inserting rt2x00usb (/lib/modules/2.6.28-15-generic/updates/rt2x00usb.ko): Invalid module format
WARNING: Error inserting crc_itu_t (/lib/modules/2.6.28-15-generic/kernel/lib/crc-itu-t.ko): Invalid module format
FATAL: Error inserting rt73usb (/lib/modules/2.6.28-15-generic/updates/rt73usb.ko): Invalid module format
Loading rndis_wlan...
WARNING: All config files need .conf: /etc/modprobe.d/blacklist, it will be ignored in a future release.
FATAL: Error inserting rndis_wlan (/lib/modules/2.6.28-15-generic/updates/rndis_wlan.ko): Unknown symbol in module, or unknown parameter (see dmesg)
Loading at76_usb...
WARNING: All config files need .conf: /etc/modprobe.d/blacklist, it will be ignored in a future release.
Loading mwl8k...
WARNING: All config files need .conf: /etc/modprobe.d/blacklist, it will be ignored in a future release.
WARNING: Error inserting lbm_cw_mac80211 (/lib/modules/2.6.28-15-generic/updates/lbm_cw-mac80211.ko): Invalid module format
FATAL: Error inserting mwl8k (/lib/modules/2.6.28-15-generic/updates/mwl8k.ko): Invalid module format
Loading mac80211_hwsim...
WARNING: All config files need .conf: /etc/modprobe.d/blacklist, it will be ignored in a future release.
WARNING: Error inserting lbm_cw_mac80211 (/lib/modules/2.6.28-15-generic/updates/lbm_cw-mac80211.ko): Invalid module format
FATAL: Error inserting mac80211_hwsim (/lib/modules/2.6.28-15-generic/updates/mac80211_hwsim.ko): Invalid module format
Loading at76c50x_usb...
WARNING: All config files need .conf: /etc/modprobe.d/blacklist, it will be ignored in a future release.
WARNING: Error inserting lbm_cw_cfg80211 (/lib/modules/2.6.28-15-generic/updates/lbm_cw-cfg80211.ko): Invalid module format
WARNING: Error inserting lbm_cw_mac80211 (/lib/modules/2.6.28-15-generic/updates/lbm_cw-mac80211.ko): Invalid module format
FATAL: Error inserting at76c50x_usb (/lib/modules/2.6.28-15-generic/updates/at76c50x-usb.ko): Invalid module format
Module ath_pci not detected -- this is fine
WARNING: All config files need .conf: /etc/modprobe.d/blacklist, it will be ignored in a future release.
WARNING: Error inserting lbm_cw_mac80211 (/lib/modules/2.6.28-15-generic/updates/lbm_cw-mac80211.ko): Invalid module format
FATAL: Error inserting ath5k (/lib/modules/2.6.28-15-generic/updates/ath5k.ko): Invalid module format
ath5k loaded successfully
WARNING: All config files need .conf: /etc/modprobe.d/blacklist, it will be ignored in a future release.
WARNING: Error inserting lbm_cw_mac80211 (/lib/modules/2.6.28-15-generic/updates/lbm_cw-mac80211.ko): Invalid module format
FATAL: Error inserting ath9k (/lib/modules/2.6.28-15-generic/updates/ath9k.ko): Invalid module format
ath9k loaded successfully
Module bcm43xx not detected -- this is fine

```

Continued from the make of yesterday.

```
statik@statik-laptop:~/Desktop/compat-wireless-2009-08-24$ sudo make install

Your old wireless subsystem modules were left intact:

kernel/net/mac80211/mac80211.ko
kernel/net/wireless/cfg80211.ko
updates/lib80211.ko
updates/adm8211.ko
updates/at76c50x-usb.ko
updates/ath5k.ko
updates/ath9k.ko
updates/b43.ko
updates/b43legacy.ko
updates/b44.ko
updates/cdc_ether.ko
updates/eeprom_93cx6.ko
updates/ipw2100.ko
updates/ipw2200.ko
updates/iwl3945.ko
updates/iwlagn.ko
updates/iwlcore.ko
updates/lib80211_crypt_ccmp.ko
updates/lib80211_crypt_tkip.ko
updates/lib80211_crypt_wep.ko
updates/libertas.ko
updates/libertas_cs.ko
updates/libertas_sdio.ko
updates/libertas_tf.ko
updates/libertas_tf_usb.ko
updates/libipw.ko
updates/mac80211_hwsim.ko
updates/mwl8k.ko
updates/p54common.ko
updates/p54pci.ko
updates/p54usb.ko
updates/rndis_host.ko
updates/rndis_wlan.ko
updates/rt2400pci.ko
updates/rt2500pci.ko
updates/rt2500usb.ko
updates/rt2x00lib.ko
updates/rt2x00pci.ko
updates/rt2x00usb.ko
updates/rt61pci.ko
updates/rt73usb.ko
updates/rtl8180.ko
updates/rtl8187.ko
updates/ssb.ko
updates/usb8xxx.ko
updates/usbnet.ko
updates/zd1211rw.ko

make -C /lib/modules/2.6.28-15-generic/build M=/home/statik/Desktop/compat-wireless-2009-08-24 "INSTALL_MOD_DIR=updates"  \
		modules_install
make[1]: Entering directory `/usr/src/linux-headers-2.6.28-15-generic'
  INSTALL /home/statik/Desktop/compat-wireless-2009-08-24/drivers/misc/eeprom/eeprom_93cx6.ko
  INSTALL /home/statik/Desktop/compat-wireless-2009-08-24/drivers/net/usb/cdc_ether.ko
  INSTALL /home/statik/Desktop/compat-wireless-2009-08-24/drivers/net/usb/rndis_host.ko
  INSTALL /home/statik/Desktop/compat-wireless-2009-08-24/drivers/net/usb/usbnet.ko
  INSTALL /home/statik/Desktop/compat-wireless-2009-08-24/drivers/net/wireless/adm8211.ko
  INSTALL /home/statik/Desktop/compat-wireless-2009-08-24/drivers/net/wireless/at76c50x-usb.ko
  INSTALL /home/statik/Desktop/compat-wireless-2009-08-24/drivers/net/wireless/ath/ar9170/ar9170usb.ko
  INSTALL /home/statik/Desktop/compat-wireless-2009-08-24/drivers/net/wireless/ath/ath.ko
  INSTALL /home/statik/Desktop/compat-wireless-2009-08-24/drivers/net/wireless/ath/ath5k/ath5k.ko
  INSTALL /home/statik/Desktop/compat-wireless-2009-08-24/drivers/net/wireless/ath/ath9k/ath9k.ko
  INSTALL /home/statik/Desktop/compat-wireless-2009-08-24/drivers/net/wireless/b43/b43.ko
  INSTALL /home/statik/Desktop/compat-wireless-2009-08-24/drivers/net/wireless/b43legacy/b43legacy.ko
  INSTALL /home/statik/Desktop/compat-wireless-2009-08-24/drivers/net/wireless/ipw2x00/ipw2100.ko
  INSTALL /home/statik/Desktop/compat-wireless-2009-08-24/drivers/net/wireless/ipw2x00/ipw2200.ko
  INSTALL /home/statik/Desktop/compat-wireless-2009-08-24/drivers/net/wireless/ipw2x00/libipw.ko
  INSTALL /home/statik/Desktop/compat-wireless-2009-08-24/drivers/net/wireless/iwlwifi/iwl3945.ko
  INSTALL /home/statik/Desktop/compat-wireless-2009-08-24/drivers/net/wireless/iwlwifi/iwlagn.ko
  INSTALL /home/statik/Desktop/compat-wireless-2009-08-24/drivers/net/wireless/iwlwifi/iwlcore.ko
  INSTALL /home/statik/Desktop/compat-wireless-2009-08-24/drivers/net/wireless/libertas/libertas.ko
  INSTALL /home/statik/Desktop/compat-wireless-2009-08-24/drivers/net/wireless/libertas/libertas_cs.ko
  INSTALL /home/statik/Desktop/compat-wireless-2009-08-24/drivers/net/wireless/libertas/libertas_sdio.ko
  INSTALL /home/statik/Desktop/compat-wireless-2009-08-24/drivers/net/wireless/libertas/libertas_spi.ko
  INSTALL /home/statik/Desktop/compat-wireless-2009-08-24/drivers/net/wireless/libertas/usb8xxx.ko
  INSTALL /home/statik/Desktop/compat-wireless-2009-08-24/drivers/net/wireless/libertas_tf/libertas_tf.ko
  INSTALL /home/statik/Desktop/compat-wireless-2009-08-24/drivers/net/wireless/libertas_tf/libertas_tf_usb.ko
  INSTALL /home/statik/Desktop/compat-wireless-2009-08-24/drivers/net/wireless/mac80211_hwsim.ko
  INSTALL /home/statik/Desktop/compat-wireless-2009-08-24/drivers/net/wireless/mwl8k.ko
  INSTALL /home/statik/Desktop/compat-wireless-2009-08-24/drivers/net/wireless/p54/p54common.ko
  INSTALL /home/statik/Desktop/compat-wireless-2009-08-24/drivers/net/wireless/p54/p54pci.ko
  INSTALL /home/statik/Desktop/compat-wireless-2009-08-24/drivers/net/wireless/p54/p54spi.ko
  INSTALL /home/statik/Desktop/compat-wireless-2009-08-24/drivers/net/wireless/p54/p54usb.ko
  INSTALL /home/statik/Desktop/compat-wireless-2009-08-24/drivers/net/wireless/rndis_wlan.ko
  INSTALL /home/statik/Desktop/compat-wireless-2009-08-24/drivers/net/wireless/rt2x00/rt2400pci.ko
  INSTALL /home/statik/Desktop/compat-wireless-2009-08-24/drivers/net/wireless/rt2x00/rt2500pci.ko
  INSTALL /home/statik/Desktop/compat-wireless-2009-08-24/drivers/net/wireless/rt2x00/rt2500usb.ko
  INSTALL /home/statik/Desktop/compat-wireless-2009-08-24/drivers/net/wireless/rt2x00/rt2800usb.ko
  INSTALL /home/statik/Desktop/compat-wireless-2009-08-24/drivers/net/wireless/rt2x00/rt2x00lib.ko
  INSTALL /home/statik/Desktop/compat-wireless-2009-08-24/drivers/net/wireless/rt2x00/rt2x00pci.ko
  INSTALL /home/statik/Desktop/compat-wireless-2009-08-24/drivers/net/wireless/rt2x00/rt2x00usb.ko
  INSTALL /home/statik/Desktop/compat-wireless-2009-08-24/drivers/net/wireless/rt2x00/rt61pci.ko
  INSTALL /home/statik/Desktop/compat-wireless-2009-08-24/drivers/net/wireless/rt2x00/rt73usb.ko
  INSTALL /home/statik/Desktop/compat-wireless-2009-08-24/drivers/net/wireless/rtl818x/rtl8180.ko
  INSTALL /home/statik/Desktop/compat-wireless-2009-08-24/drivers/net/wireless/rtl818x/rtl8187.ko
  INSTALL /home/statik/Desktop/compat-wireless-2009-08-24/drivers/net/wireless/wl12xx/wl1251.ko
  INSTALL /home/statik/Desktop/compat-wireless-2009-08-24/drivers/net/wireless/wl12xx/wl1251_sdio.ko
  INSTALL /home/statik/Desktop/compat-wireless-2009-08-24/drivers/net/wireless/wl12xx/wl1251_spi.ko
  INSTALL /home/statik/Desktop/compat-wireless-2009-08-24/drivers/net/wireless/wl12xx/wl1271.ko
  INSTALL /home/statik/Desktop/compat-wireless-2009-08-24/drivers/net/wireless/zd1211rw/zd1211rw.ko
  INSTALL /home/statik/Desktop/compat-wireless-2009-08-24/drivers/ssb/ssb.ko
  INSTALL /home/statik/Desktop/compat-wireless-2009-08-24/net/mac80211/mac80211.ko
  INSTALL /home/statik/Desktop/compat-wireless-2009-08-24/net/rfkill/rfkill_backport.ko
  INSTALL /home/statik/Desktop/compat-wireless-2009-08-24/net/wireless/cfg80211.ko
  INSTALL /home/statik/Desktop/compat-wireless-2009-08-24/net/wireless/lib80211.ko
  INSTALL /home/statik/Desktop/compat-wireless-2009-08-24/net/wireless/lib80211_crypt_ccmp.ko
  INSTALL /home/statik/Desktop/compat-wireless-2009-08-24/net/wireless/lib80211_crypt_tkip.ko
  INSTALL /home/statik/Desktop/compat-wireless-2009-08-24/net/wireless/lib80211_crypt_wep.ko
  DEPMOD  2.6.28-15-generic
make[1]: Leaving directory `/usr/src/linux-headers-2.6.28-15-generic'

Note: madwifi detected, we're going to disable it. If you would like to enable it later you can run:
    sudo athenable madwifi

Running athenable ath5k...
Disabling ath_pci ...	[OK]	Module disabled:
volatile/ath_pci.ko
depmod will prefer updates/ over kernel/ -- OK!

Currently detected wireless subsystem modules:

updates/net/mac80211/mac80211.ko
updates/net/wireless/cfg80211.ko
updates/net/wireless/lib80211.ko
updates/drivers/net/wireless/adm8211.ko
updates/drivers/net/wireless/ath/ar9170/ar9170usb.ko
updates/at76c50x-usb.ko
updates/drivers/net/wireless/ath/ath.ko
updates/ath5k.ko
updates/ath9k.ko
updates/b43.ko
updates/b43legacy.ko
updates/b44.ko
updates/cdc_ether.ko
updates/eeprom_93cx6.ko
updates/ipw2100.ko
updates/ipw2200.ko
updates/drivers/net/wireless/iwlwifi/iwl3945.ko
updates/drivers/net/wireless/iwlwifi/iwlagn.ko
updates/iwlcore.ko
updates/net/wireless/lib80211_crypt_ccmp.ko
updates/net/wireless/lib80211_crypt_tkip.ko
updates/net/wireless/lib80211_crypt_wep.ko
updates/libertas.ko
updates/libertas_cs.ko
updates/libertas_sdio.ko
updates/drivers/net/wireless/libertas/libertas_spi.ko
updates/libertas_tf.ko
updates/drivers/net/wireless/libertas_tf/libertas_tf_usb.ko
updates/libipw.ko
updates/mac80211_hwsim.ko
updates/mwl8k.ko
updates/p54common.ko
updates/p54pci.ko
updates/drivers/net/wireless/p54/p54spi.ko
updates/p54usb.ko
updates/drivers/net/usb/rndis_host.ko
updates/rndis_wlan.ko
updates/rt2400pci.ko
updates/drivers/net/wireless/rt2x00/rt2500pci.ko
updates/rt2500usb.ko
updates/rt2x00lib.ko
updates/rt2x00pci.ko
updates/rt2x00usb.ko
updates/rt61pci.ko
updates/rt73usb.ko
updates/rtl8180.ko
updates/rtl8187.ko
updates/ssb.ko
updates/usb8xxx.ko
updates/usbnet.ko
updates/zd1211rw.ko

Now run:

make unload

And then load the wireless module you need. If unsure reboot.

statik@statik-laptop:~/Desktop/compat-wireless-2009-08-24$
```

I'm not sure if something is working right here or not. :)

Statik

---

### Post by pytheas22 on 2009-08-25
I think the problem is that you need to reboot **after** compling compat-wireless.  So now that you have it compiled, reboot your computer (don't compile it again after rebooting).  After the reboot, just type:
```

sudo modprobe ath9k
```

and the module should be inserted without error.  If so, hopefully your connection will work.  If it still doesn't, please post the output of:

```
dmesg | grep -e ath -e wlan
```

---

### Post by Statik on 2009-08-25
```
statik@statik-laptop:~$ sudo modprobe ath9k
[sudo] password for statik: 
WARNING: All config files need .conf: /etc/modprobe.d/blacklist, it will be ignored in a future release.
WARNING: Error inserting lbm_cw_mac80211 (/lib/modules/2.6.28-15-generic/updates/lbm_cw-mac80211.ko): Invalid module format
FATAL: Error inserting ath9k (/lib/modules/2.6.28-15-generic/updates/ath9k.ko): Invalid module format
statik@statik-laptop:~$ 

```

```
statik@statik-laptop:~$ dmesg | grep -e ath -e wlan
[    4.749483] device-mapper: multipath: version 1.0.5 loaded
[    4.749486] device-mapper: multipath round-robin: version 1.0.0 loaded
statik@statik-laptop:~$ 

```

Looks like that module, ath9k, is broken. *sigh*

Statik

---

### Post by Statik on 2009-08-25
Did a little digging and I might have found part of the problem. The error mentions a bad module format for 
```
/lib/modules/2.6.28-15-generic/updates/ath9k.ko
```
however, the correct path for that file is:
```
/lib/modules/2.6.28-15-generic/updates/drivers/net/wireless/ath/ath9k/ath9k.ko
```

Could this be the problem? Should I have a link here?

Statik

---

### Post by pytheas22 on 2009-08-26
hmmm, strange that the module ended up being installed there.  What happens if you run:
```

sudo insmod /lib/modules/2.6.28-15-generic/updates/drivers/net/wireless/ath/ath9k/ath9k.ko
```

---

### Post by Statik on 2009-08-26
```
statik@statik-laptop:~$ sudo insmod /lib/modules/2.6.28-15-generic/updates/drivers/net/wireless/ath/ath9k/ath9k.ko
[sudo] password for statik: 
insmod: error inserting '/lib/modules/2.6.28-15-generic/updates/drivers/net/wireless/ath/ath9k/ath9k.ko': -1 Unknown symbol in module
statik@statik-laptop:~$ 

```

I also read that trying to install compat could fail if backport was installed. So, I removed it and redid the make, etc procedure again. Make seemed to go better this time, but on sudo make load . . .
```
statik@statik-laptop:~/Desktop/compat-wireless-2009-08-24$ sudo make load
Loading ipw2100...
WARNING: All config files need .conf: /etc/modprobe.d/blacklist, it will be ignored in a future release.
Loading ipw2200...
WARNING: All config files need .conf: /etc/modprobe.d/blacklist, it will be ignored in a future release.
Loading libertas_cs...
WARNING: All config files need .conf: /etc/modprobe.d/blacklist, it will be ignored in a future release.
Loading usb8xxx...
WARNING: All config files need .conf: /etc/modprobe.d/blacklist, it will be ignored in a future release.
Loading p54pci...
WARNING: All config files need .conf: /etc/modprobe.d/blacklist, it will be ignored in a future release.
WARNING: Error inserting mac80211 (/lib/modules/2.6.28-15-generic/updates/net/mac80211/mac80211.ko): Invalid module format
WARNING: Error inserting led_class (/lib/modules/2.6.28-15-generic/kernel/drivers/leds/led-class.ko): Invalid module format
WARNING: Error inserting p54common (/lib/modules/2.6.28-15-generic/updates/drivers/net/wireless/p54/p54common.ko): Invalid module format
FATAL: Error inserting p54pci (/lib/modules/2.6.28-15-generic/updates/drivers/net/wireless/p54/p54pci.ko): Invalid module format
Loading p54usb...
WARNING: All config files need .conf: /etc/modprobe.d/blacklist, it will be ignored in a future release.
WARNING: Error inserting mac80211 (/lib/modules/2.6.28-15-generic/updates/net/mac80211/mac80211.ko): Invalid module format
WARNING: Error inserting led_class (/lib/modules/2.6.28-15-generic/kernel/drivers/leds/led-class.ko): Invalid module format
WARNING: Error inserting p54common (/lib/modules/2.6.28-15-generic/updates/drivers/net/wireless/p54/p54common.ko): Invalid module format
FATAL: Error inserting p54usb (/lib/modules/2.6.28-15-generic/updates/drivers/net/wireless/p54/p54usb.ko): Invalid module format
Loading adm8211...
WARNING: All config files need .conf: /etc/modprobe.d/blacklist, it will be ignored in a future release.
WARNING: Error inserting eeprom_93cx6 (/lib/modules/2.6.28-15-generic/updates/drivers/misc/eeprom/eeprom_93cx6.ko): Invalid module format
WARNING: Error inserting mac80211 (/lib/modules/2.6.28-15-generic/updates/net/mac80211/mac80211.ko): Invalid module format
FATAL: Error inserting adm8211 (/lib/modules/2.6.28-15-generic/updates/drivers/net/wireless/adm8211.ko): Invalid module format
Loading zd1211rw...
WARNING: All config files need .conf: /etc/modprobe.d/blacklist, it will be ignored in a future release.
WARNING: Error inserting mac80211 (/lib/modules/2.6.28-15-generic/updates/net/mac80211/mac80211.ko): Invalid module format
FATAL: Error inserting zd1211rw (/lib/modules/2.6.28-15-generic/updates/drivers/net/wireless/zd1211rw/zd1211rw.ko): Invalid module format
Loading rtl8180...
WARNING: All config files need .conf: /etc/modprobe.d/blacklist, it will be ignored in a future release.
WARNING: Error inserting eeprom_93cx6 (/lib/modules/2.6.28-15-generic/updates/drivers/misc/eeprom/eeprom_93cx6.ko): Invalid module format
WARNING: Error inserting mac80211 (/lib/modules/2.6.28-15-generic/updates/net/mac80211/mac80211.ko): Invalid module format
FATAL: Error inserting rtl8180 (/lib/modules/2.6.28-15-generic/updates/drivers/net/wireless/rtl818x/rtl8180.ko): Invalid module format
Loading rtl8187...
WARNING: All config files need .conf: /etc/modprobe.d/blacklist, it will be ignored in a future release.
WARNING: Error inserting eeprom_93cx6 (/lib/modules/2.6.28-15-generic/updates/drivers/misc/eeprom/eeprom_93cx6.ko): Invalid module format
WARNING: Error inserting mac80211 (/lib/modules/2.6.28-15-generic/updates/net/mac80211/mac80211.ko): Invalid module format
FATAL: Error inserting rtl8187 (/lib/modules/2.6.28-15-generic/updates/drivers/net/wireless/rtl818x/rtl8187.ko): Invalid module format
Loading p54pci...
WARNING: All config files need .conf: /etc/modprobe.d/blacklist, it will be ignored in a future release.
WARNING: Error inserting mac80211 (/lib/modules/2.6.28-15-generic/updates/net/mac80211/mac80211.ko): Invalid module format
WARNING: Error inserting led_class (/lib/modules/2.6.28-15-generic/kernel/drivers/leds/led-class.ko): Invalid module format
WARNING: Error inserting p54common (/lib/modules/2.6.28-15-generic/updates/drivers/net/wireless/p54/p54common.ko): Invalid module format
FATAL: Error inserting p54pci (/lib/modules/2.6.28-15-generic/updates/drivers/net/wireless/p54/p54pci.ko): Invalid module format
Loading p54usb...
WARNING: All config files need .conf: /etc/modprobe.d/blacklist, it will be ignored in a future release.
WARNING: Error inserting mac80211 (/lib/modules/2.6.28-15-generic/updates/net/mac80211/mac80211.ko): Invalid module format
WARNING: Error inserting led_class (/lib/modules/2.6.28-15-generic/kernel/drivers/leds/led-class.ko): Invalid module format
WARNING: Error inserting p54common (/lib/modules/2.6.28-15-generic/updates/drivers/net/wireless/p54/p54common.ko): Invalid module format
FATAL: Error inserting p54usb (/lib/modules/2.6.28-15-generic/updates/drivers/net/wireless/p54/p54usb.ko): Invalid module format
Loading iwl3945...
WARNING: All config files need .conf: /etc/modprobe.d/blacklist, it will be ignored in a future release.
WARNING: Error inserting led_class (/lib/modules/2.6.28-15-generic/kernel/drivers/leds/led-class.ko): Invalid module format
WARNING: Error inserting mac80211 (/lib/modules/2.6.28-15-generic/updates/net/mac80211/mac80211.ko): Invalid module format
WARNING: Error inserting iwlcore (/lib/modules/2.6.28-15-generic/updates/drivers/net/wireless/iwlwifi/iwlcore.ko): Invalid module format
FATAL: Error inserting iwl3945 (/lib/modules/2.6.28-15-generic/updates/drivers/net/wireless/iwlwifi/iwl3945.ko): Invalid module format
Loading iwlagn...
WARNING: All config files need .conf: /etc/modprobe.d/blacklist, it will be ignored in a future release.
WARNING: Error inserting mac80211 (/lib/modules/2.6.28-15-generic/updates/net/mac80211/mac80211.ko): Invalid module format
WARNING: Error inserting led_class (/lib/modules/2.6.28-15-generic/kernel/drivers/leds/led-class.ko): Invalid module format
WARNING: Error inserting iwlcore (/lib/modules/2.6.28-15-generic/updates/drivers/net/wireless/iwlwifi/iwlcore.ko): Invalid module format
FATAL: Error inserting iwlagn (/lib/modules/2.6.28-15-generic/updates/drivers/net/wireless/iwlwifi/iwlagn.ko): Invalid module format
Loading ath...
WARNING: All config files need .conf: /etc/modprobe.d/blacklist, it will be ignored in a future release.
FATAL: Error inserting ath (/lib/modules/2.6.28-15-generic/updates/drivers/net/wireless/ath/ath.ko): Invalid module format
Loading ar9170usb...
WARNING: All config files need .conf: /etc/modprobe.d/blacklist, it will be ignored in a future release.
WARNING: Error inserting ath (/lib/modules/2.6.28-15-generic/updates/drivers/net/wireless/ath/ath.ko): Invalid module format
WARNING: Error inserting led_class (/lib/modules/2.6.28-15-generic/kernel/drivers/leds/led-class.ko): Invalid module format
WARNING: Error inserting mac80211 (/lib/modules/2.6.28-15-generic/updates/net/mac80211/mac80211.ko): Invalid module format
FATAL: Error inserting ar9170usb (/lib/modules/2.6.28-15-generic/updates/drivers/net/wireless/ath/ar9170/ar9170usb.ko): Invalid module format
Loading rtl8180...
WARNING: All config files need .conf: /etc/modprobe.d/blacklist, it will be ignored in a future release.
WARNING: Error inserting eeprom_93cx6 (/lib/modules/2.6.28-15-generic/updates/drivers/misc/eeprom/eeprom_93cx6.ko): Invalid module format
WARNING: Error inserting mac80211 (/lib/modules/2.6.28-15-generic/updates/net/mac80211/mac80211.ko): Invalid module format
FATAL: Error inserting rtl8180 (/lib/modules/2.6.28-15-generic/updates/drivers/net/wireless/rtl818x/rtl8180.ko): Invalid module format
Loading rtl8187...
WARNING: All config files need .conf: /etc/modprobe.d/blacklist, it will be ignored in a future release.
WARNING: Error inserting eeprom_93cx6 (/lib/modules/2.6.28-15-generic/updates/drivers/misc/eeprom/eeprom_93cx6.ko): Invalid module format
WARNING: Error inserting mac80211 (/lib/modules/2.6.28-15-generic/updates/net/mac80211/mac80211.ko): Invalid module format
FATAL: Error inserting rtl8187 (/lib/modules/2.6.28-15-generic/updates/drivers/net/wireless/rtl818x/rtl8187.ko): Invalid module format
Loading rt2400pci...
WARNING: All config files need .conf: /etc/modprobe.d/blacklist, it will be ignored in a future release.
WARNING: Error inserting mac80211 (/lib/modules/2.6.28-15-generic/updates/net/mac80211/mac80211.ko): Invalid module format
WARNING: Error inserting led_class (/lib/modules/2.6.28-15-generic/kernel/drivers/leds/led-class.ko): Invalid module format
WARNING: Error inserting rt2x00lib (/lib/modules/2.6.28-15-generic/updates/drivers/net/wireless/rt2x00/rt2x00lib.ko): Invalid module format
WARNING: Error inserting rt2x00pci (/lib/modules/2.6.28-15-generic/updates/drivers/net/wireless/rt2x00/rt2x00pci.ko): Invalid module format
FATAL: Error inserting rt2400pci (/lib/modules/2.6.28-15-generic/updates/drivers/net/wireless/rt2x00/rt2400pci.ko): Invalid module format
Loading rt2500pci...
WARNING: All config files need .conf: /etc/modprobe.d/blacklist, it will be ignored in a future release.
WARNING: Error inserting mac80211 (/lib/modules/2.6.28-15-generic/updates/net/mac80211/mac80211.ko): Invalid module format
WARNING: Error inserting led_class (/lib/modules/2.6.28-15-generic/kernel/drivers/leds/led-class.ko): Invalid module format
WARNING: Error inserting rt2x00lib (/lib/modules/2.6.28-15-generic/updates/drivers/net/wireless/rt2x00/rt2x00lib.ko): Invalid module format
WARNING: Error inserting rt2x00pci (/lib/modules/2.6.28-15-generic/updates/drivers/net/wireless/rt2x00/rt2x00pci.ko): Invalid module format
FATAL: Error inserting rt2500pci (/lib/modules/2.6.28-15-generic/updates/drivers/net/wireless/rt2x00/rt2500pci.ko): Invalid module format
Loading rt61pci...
WARNING: All config files need .conf: /etc/modprobe.d/blacklist, it will be ignored in a future release.
WARNING: Error inserting mac80211 (/lib/modules/2.6.28-15-generic/updates/net/mac80211/mac80211.ko): Invalid module format
WARNING: Error inserting led_class (/lib/modules/2.6.28-15-generic/kernel/drivers/leds/led-class.ko): Invalid module format
WARNING: Error inserting rt2x00lib (/lib/modules/2.6.28-15-generic/updates/drivers/net/wireless/rt2x00/rt2x00lib.ko): Invalid module format
WARNING: Error inserting rt2x00pci (/lib/modules/2.6.28-15-generic/updates/drivers/net/wireless/rt2x00/rt2x00pci.ko): Invalid module format
WARNING: Error inserting crc_itu_t (/lib/modules/2.6.28-15-generic/kernel/lib/crc-itu-t.ko): Invalid module format
FATAL: Error inserting rt61pci (/lib/modules/2.6.28-15-generic/updates/drivers/net/wireless/rt2x00/rt61pci.ko): Invalid module format
Loading rt2500usb...
WARNING: All config files need .conf: /etc/modprobe.d/blacklist, it will be ignored in a future release.
WARNING: Error inserting mac80211 (/lib/modules/2.6.28-15-generic/updates/net/mac80211/mac80211.ko): Invalid module format
WARNING: Error inserting led_class (/lib/modules/2.6.28-15-generic/kernel/drivers/leds/led-class.ko): Invalid module format
WARNING: Error inserting rt2x00lib (/lib/modules/2.6.28-15-generic/updates/drivers/net/wireless/rt2x00/rt2x00lib.ko): Invalid module format
WARNING: Error inserting rt2x00usb (/lib/modules/2.6.28-15-generic/updates/drivers/net/wireless/rt2x00/rt2x00usb.ko): Invalid module format
FATAL: Error inserting rt2500usb (/lib/modules/2.6.28-15-generic/updates/drivers/net/wireless/rt2x00/rt2500usb.ko): Invalid module format
Loading rt73usb...
WARNING: All config files need .conf: /etc/modprobe.d/blacklist, it will be ignored in a future release.
WARNING: Error inserting mac80211 (/lib/modules/2.6.28-15-generic/updates/net/mac80211/mac80211.ko): Invalid module format
WARNING: Error inserting led_class (/lib/modules/2.6.28-15-generic/kernel/drivers/leds/led-class.ko): Invalid module format
WARNING: Error inserting rt2x00lib (/lib/modules/2.6.28-15-generic/updates/drivers/net/wireless/rt2x00/rt2x00lib.ko): Invalid module format
WARNING: Error inserting rt2x00usb (/lib/modules/2.6.28-15-generic/updates/drivers/net/wireless/rt2x00/rt2x00usb.ko): Invalid module format
WARNING: Error inserting crc_itu_t (/lib/modules/2.6.28-15-generic/kernel/lib/crc-itu-t.ko): Invalid module format
FATAL: Error inserting rt73usb (/lib/modules/2.6.28-15-generic/updates/drivers/net/wireless/rt2x00/rt73usb.ko): Invalid module format
Loading rndis_wlan...
WARNING: All config files need .conf: /etc/modprobe.d/blacklist, it will be ignored in a future release.
FATAL: Error inserting rndis_wlan (/lib/modules/2.6.28-15-generic/updates/drivers/net/wireless/rndis_wlan.ko): Invalid module format
Loading at76_usb...
WARNING: All config files need .conf: /etc/modprobe.d/blacklist, it will be ignored in a future release.
Loading mwl8k...
WARNING: All config files need .conf: /etc/modprobe.d/blacklist, it will be ignored in a future release.
WARNING: Error inserting mac80211 (/lib/modules/2.6.28-15-generic/updates/net/mac80211/mac80211.ko): Invalid module format
FATAL: Error inserting mwl8k (/lib/modules/2.6.28-15-generic/updates/drivers/net/wireless/mwl8k.ko): Invalid module format
Loading mac80211_hwsim...
WARNING: All config files need .conf: /etc/modprobe.d/blacklist, it will be ignored in a future release.
WARNING: Error inserting mac80211 (/lib/modules/2.6.28-15-generic/updates/net/mac80211/mac80211.ko): Invalid module format
FATAL: Error inserting mac80211_hwsim (/lib/modules/2.6.28-15-generic/updates/drivers/net/wireless/mac80211_hwsim.ko): Invalid module format
Loading at76c50x_usb...
WARNING: All config files need .conf: /etc/modprobe.d/blacklist, it will be ignored in a future release.
WARNING: Error inserting mac80211 (/lib/modules/2.6.28-15-generic/updates/net/mac80211/mac80211.ko): Invalid module format
FATAL: Error inserting at76c50x_usb (/lib/modules/2.6.28-15-generic/updates/drivers/net/wireless/at76c50x-usb.ko): Invalid module format
Disabling ath_pci ...	[OK]	Module disabled:
volatile/ath_pci.ko
WARNING: All config files need .conf: /etc/modprobe.d/blacklist, it will be ignored in a future release.
WARNING: Error inserting ath (/lib/modules/2.6.28-15-generic/updates/drivers/net/wireless/ath/ath.ko): Invalid module format
WARNING: Error inserting mac80211 (/lib/modules/2.6.28-15-generic/updates/net/mac80211/mac80211.ko): Invalid module format
FATAL: Error inserting ath5k (/lib/modules/2.6.28-15-generic/updates/drivers/net/wireless/ath/ath5k/ath5k.ko): Invalid module format
ath5k loaded successfully
WARNING: All config files need .conf: /etc/modprobe.d/blacklist, it will be ignored in a future release.
WARNING: Error inserting ath (/lib/modules/2.6.28-15-generic/updates/drivers/net/wireless/ath/ath.ko): Invalid module format
WARNING: Error inserting mac80211 (/lib/modules/2.6.28-15-generic/updates/net/mac80211/mac80211.ko): Invalid module format
FATAL: Error inserting ath9k (/lib/modules/2.6.28-15-generic/updates/drivers/net/wireless/ath/ath9k/ath9k.ko): Invalid module format
ath9k loaded successfully
Module bcm43xx not detected -- this is fine
Disabling wl ...	[OK]	Module disabled:
volatile/wl.ko
WARNING: All config files need .conf: /etc/modprobe.d/blacklist, it will be ignored in a future release.
WARNING: Error inserting mac80211 (/lib/modules/2.6.28-15-generic/updates/net/mac80211/mac80211.ko): Invalid module format
WARNING: Error inserting pcmcia (/lib/modules/2.6.28-15-generic/kernel/drivers/pcmcia/pcmcia.ko): Invalid module format
WARNING: Error inserting ssb (/lib/modules/2.6.28-15-generic/updates/drivers/ssb/ssb.ko): Invalid module format
FATAL: Error inserting b43 (/lib/modules/2.6.28-15-generic/updates/drivers/net/wireless/b43/b43.ko): Invalid module format
WARNING: All config files need .conf: /etc/modprobe.d/blacklist, it will be ignored in a future release.
WARNING: Error inserting mac80211 (/lib/modules/2.6.28-15-generic/updates/net/mac80211/mac80211.ko): Invalid module format
WARNING: Error inserting pcmcia_core (/lib/modules/2.6.28-15-generic/kernel/drivers/pcmcia/pcmcia_core.ko): Invalid module format
WARNING: Error inserting pcmcia (/lib/modules/2.6.28-15-generic/kernel/drivers/pcmcia/pcmcia.ko): Invalid module format
WARNING: Error inserting ssb (/lib/modules/2.6.28-15-generic/updates/drivers/ssb/ssb.ko): Invalid module format
FATAL: Error inserting b43legacy (/lib/modules/2.6.28-15-generic/updates/drivers/net/wireless/b43legacy/b43legacy.ko): Invalid module format
b43 loaded successfully
b43legacy loaded successfully

```

the main line in there being:
```
FATAL: Error inserting ath9k (/lib/modules/2.6.28-15-generic/updates/drivers/net/wireless/ath/ath9k/ath9k.ko): Invalid module format
ath9k loaded successfully
```

Statik

---

### Post by Statik on 2009-08-26
Woot!

Rebooted after the make/make unload/make load/make install, after removing backports and I have working wireless with WEP. Not sure how long its going to last yet, but I'll test it when I get home tonight and let you know!

Thanks,

Statik

---

### Post by wjamoore on 2009-08-26
Hi, Related to this can someone tell me if the ath9k driver will allow my AR242x card to talk to my wirelessN router.

I believe that quite a number of wireless problems lately could also be traced to wireless N compatibility (or lack of)

If ath9k will work what do i need to do to install it in preference to the ath5k and crucially how do I get back if it doesn't work??

thanks in advance

Aaron

---

### Post by pytheas22 on 2009-08-26
**Statik**: I'm not sure what actually went on, but I suspect that after rebooting, the module was able to be inserted properly.  Hopefully this will stick and you'll be set from here on out.  Just keep in mind that whenever you install a new kernel, ath9k will need to be recompiled against that new kernel (unless the stock ath9k module that comes with the new kernel works alright).
[B]
wjamoore[/B]: both your router and your wireless card need to be 802.11n-compatible in order to work in that mode.  Are you sure the AR242x supports 802.11n mode?  I thought it was only a/b/g, but I could be wrong.  In any case, I don't think the ath9k driver will support AR242x, but if you want to try, run these commands:
```

sudo rmmod ath5k
sudo rmmod ath9k
sudo modprobe ath9k
```

That will simply remove the ath5k driver and load ath9k.  If you have a wireless interface after running those commands, then it means ath9k supports your card.  But I suspect that it doesn't.

---

### Post by Statik on 2009-08-26
pytheas22: Yes, it seems to be sticking. I took the laptop to work today where there is no wireless access. When I brought it back home, I had a wireless card, but no wireless networks in the detected list. PANIC! So, I went to add it in manually and started by taking the card out of roaming mode . . . and it automatically connected. Woot! This seems to be fixed. I didn't go through the make report line by line, but it seemed to compile better with the backports removed and the evidence seems to back that up.

Thanks again!

Statik

---

### Post by Statik on 2009-08-27
Just when you thought you were rid of me! :)

It seems that the wireless driver is having some issues with lag or something. When it is downloading, it is full speed, but it 'takes a break' or something occasionally. It will either wait something like 5-10 seconds before loading a web page, no network activity noticed, and then load the entire page quickly, or load part of the page quickly, and then wait 5-10 seconds before completing it.

I'm hoping its a setting and not that the new laptop is overloading the router.

Any ideas?

Statik

---

### Post by pytheas22 on 2009-08-27
There could be a lot of different issues that would cause behavior like that.  It could be a flaky DNS server, problems with your router, your computer being overloaded, or, of course, wireless-driver issues.  The latter seems like the most likely candidate, but I wouldn't assume it's the case without more evidence.

The next time it "takes a break," run "dmesg | tail" and see if there's anything mentioned about the wireless.  This will hopefully provide some clues, especially if it's a driver issue.  Also pay attention to the system load (you can add an applet to your Gnome panel to display that information, or run the 'top' command) to see if that might be a factor.

Short of this, the only thing I can think to do is run a packet dump to try to see what's going on with the traffic during the hang ups, but that would be a lot of work, so let's not do it unless we have to.

---

### Post by Statik on 2009-08-28
Well, I booted the laptop, got it connected, and opened up Eternal Lands where I can see the lag by my character pausing in walking many times, which doesn't happen on the wired connection. Running dmesg | tail only gives one possible error.

```
[  255.386295] wlan0: direct probe to AP ffff88005f1a4848 (try 1)
[  255.388585] wlan0 direct probe responded
[  255.388590] wlan0: authenticate with AP ffff88005f1a4848 (try 1)
[  255.399258] wlan0: authenticated
[  255.399308] wlan0: associate with AP ffff88005f1a4848 (try 1)
[  255.401733] wlan0: RX AssocResp from ffff88006dc9204a (capab=0x431 status=0 aid=3)
[  255.401739] wlan0: associated
[  255.410178] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[  265.816038] wlan0: no IPv6 routers present
[  377.825765] hda-intel: IRQ timing workaround is activated for card #0. Suggest a bigger bdl_pos_adj.

```

I'm thinking its the hda-intel but I haven't looked into it yet.

Edit: Looked into the hda-intel and it seems to be a sound related issue. Don't think its related to my problem. Tried dmesg | tail a few times here and there as I used the computer and now I'm seeing:
```
statik@statik-laptop:~/Desktop/HL2$ dmesg | tail
[ 3075.733581] Too big adjustment 32
[ 3075.772635] Too big adjustment 32
[ 3240.479300] Too big adjustment 32
[ 3240.515136] Too big adjustment 32
[ 3302.258363] Too big adjustment 32
[ 3302.292797] Too big adjustment 32
[ 3306.676198] Too big adjustment 32
[ 3306.709879] Too big adjustment 32
[ 3312.799343] Too big adjustment 32
[ 3312.852203] Too big adjustment 32

```

researching that now. :)

Statik

---

### Post by Statik on 2009-08-28
OK, this is weird. My network monitor applet thingy shows no active connections, but I'm using the net right now.

```
statik@statik-laptop:~$ dmesg | grep -e ath -e wlan
[    4.753491] device-mapper: multipath: version 1.0.5 loaded
[    4.753494] device-mapper: multipath round-robin: version 1.0.0 loaded
[   13.702049] ath9k 0000:0b:00.0: PCI INT A -> Link[Z00O] -> GSI 21 (level, low) -> IRQ 21
[   13.702062] ath9k 0000:0b:00.0: setting latency timer to 64
[   14.131137] ath: EEPROM regdomain: 0x65
[   14.131139] ath: EEPROM indicates we should expect a direct regpair map
[   14.131144] ath: Country alpha2 being used: 00
[   14.131146] ath: Regpair used: 0x65
[   14.188850] phy0: Selected rate control algorithm 'ath9k_rate_control'
[   14.189546] Registered led device: ath9k-phy0::radio
[   14.189564] Registered led device: ath9k-phy0::assoc
[   14.189587] Registered led device: ath9k-phy0::tx
[   14.189608] Registered led device: ath9k-phy0::rx
[   20.504653] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   21.521940] wlan0: direct probe to AP ffff88006e901448 (try 1)
[   21.524682] wlan0 direct probe responded
[   21.524685] wlan0: authenticate with AP ffff88006e901448 (try 1)
[   21.526590] wlan0: direct probe to AP ffff88006e901448 (try 1)
[   21.529320] wlan0 direct probe responded
[   21.529322] wlan0: authenticate with AP ffff88006e901448 (try 1)
[   21.540131] wlan0: authenticated
[   21.540169] wlan0: associate with AP ffff88006e901448 (try 1)
[   21.542486] wlan0: RX AssocResp from ffff88006e8ca04a (capab=0x431 status=0 aid=3)
[   21.542492] wlan0: associated
[   21.543147] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[   32.337017] wlan0: no IPv6 routers present
[  180.089637] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  181.093934] wlan0: direct probe to AP ffff880065c57c48 (try 1)
[  181.096224] wlan0 direct probe responded
[  181.096226] wlan0: authenticate with AP ffff880065c57c48 (try 1)
[  181.099978] wlan0: direct probe to AP ffff880065c57c48 (try 1)
[  181.102764] wlan0 direct probe responded
[  181.102770] wlan0: authenticate with AP ffff880065c57c48 (try 1)
[  181.113878] wlan0: authenticated
[  181.113904] wlan0: associate with AP ffff880065c57c48 (try 1)
[  181.116234] wlan0: RX AssocResp from ffff88006e5be04a (capab=0x431 status=0 aid=3)
[  181.116237] wlan0: associated
[  181.116872] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[  191.345029] wlan0: no IPv6 routers present

```

```
statik@statik-laptop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:23:8b:46:90:1a  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:23 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1623 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1623 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:85832 (85.8 KB)  TX bytes:85832 (85.8 KB)

wlan0     Link encap:Ethernet  HWaddr 00:17:c4:56:06:c4  
          inet addr:192.168.2.105  Bcast:192.168.2.255  Mask:255.255.255.0
          inet6 addr: fe80::217:c4ff:fe56:6c4/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:619011 errors:0 dropped:0 overruns:0 frame:0
          TX packets:322948 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:892874777 (892.8 MB)  TX bytes:28512480 (28.5 MB)

```

```
statik@statik-laptop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:"statik_home"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: 00:14:D1:47:23:BC   
          Bit Rate=12 Mb/s   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:on
          Link Quality=58/70  Signal level=-52 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

pan0      no wireless extensions.

```

```
statik@statik-laptop:~$ lshw -C network
WARNING: you should run this program as super-user.
  *-network               
       description: Ethernet interface
       product: NetXtreme BCM5764M Gigabit Ethernet PCIe
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:08:00.0
       logical name: eth0
       version: 10
       serial: 00:23:8b:46:90:1a
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=tg3 driverversion=3.94 latency=0 module=tg3 multicast=yes
  *-network
       description: Wireless interface
       product: AR928X Wireless Network Adapter (PCI-Express)
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:0b:00.0
       logical name: wlan0
       version: 01
       serial: 00:17:c4:56:06:c4
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ath9k ip=192.168.2.105 latency=0 module=ath9k multicast=yes wireless=IEEE 802.11bgn
  *-network DISABLED
       description: Ethernet interface
       physical id: 2
       logical name: pan0
       serial: c2:ce:8d:bf:00:aa
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A multicast=yes

```

Funny thing is it seems to be working better for a while. I was downloading at 500kb/s with no hiccups for 20 minutes before the downloads just stopped. No errors or anything. Just stopped.

This thing is weird. :)

Statik

---

### Post by pytheas22 on 2009-08-29
Statik: I think the "Too big adjustment 32" stuff is related to sound as well, not networking.

You're using NetworkManager, right?  You might have better luck with wicd, which you can install with:
```

sudo apt-get install wicd
```

Sometimes NM does flaky things that make the connection drop.

If wicd doesn't help, the only other thing I can think to do is take a packet dump using Wireshark and see if that provides a clue.

---

### Post by Statik on 2009-08-29
OK, this is just really weird. It looks like something between the driver and the applications is messed up. WiCD is reporting no wireless devices found. yet:

```
statik@statik-laptop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:23:8b:46:90:1a  
          inet addr:192.168.2.102  Bcast:192.168.2.255  Mask:255.255.255.0
          inet6 addr: fe80::223:8bff:fe46:901a/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2563 errors:0 dropped:0 overruns:0 frame:0
          TX packets:5698 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:559664 (559.6 KB)  TX bytes:8151949 (8.1 MB)
          Interrupt:23 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:4 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:240 (240.0 B)  TX bytes:240 (240.0 B)

wlan0     Link encap:Ethernet  HWaddr 00:17:c4:56:06:c4  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

wlan0:avahi Link encap:Ethernet  HWaddr 00:17:c4:56:06:c4  
          inet addr:169.254.6.142  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1

statik@statik-laptop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:"statik_home"  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=off   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:on
          
pan0      no wireless extensions.

statik@statik-laptop:~$ dmesg | grep -e ath -e wlan
[    4.749471] device-mapper: multipath: version 1.0.5 loaded
[    4.749475] device-mapper: multipath round-robin: version 1.0.0 loaded
[   11.310029] ath9k 0000:0b:00.0: PCI INT A -> Link[Z00O] -> GSI 21 (level, low) -> IRQ 21
[   11.310042] ath9k 0000:0b:00.0: setting latency timer to 64
[   11.736862] ath: EEPROM regdomain: 0x65
[   11.736864] ath: EEPROM indicates we should expect a direct regpair map
[   11.736869] ath: Country alpha2 being used: 00
[   11.736870] ath: Regpair used: 0x65
[   11.782167] phy0: Selected rate control algorithm 'ath9k_rate_control'
[   11.782895] Registered led device: ath9k-phy0::radio
[   11.782934] Registered led device: ath9k-phy0::assoc
[   11.782971] Registered led device: ath9k-phy0::tx
[   11.783010] Registered led device: ath9k-phy0::rx
[   15.093589] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   79.345598] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  182.132975] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  251.169204] ADDRCONF(NETDEV_UP): wlan0: link is not ready

statik@statik-laptop:~$ lshw -C network
WARNING: you should run this program as super-user.
  *-network               
       description: Ethernet interface
       product: NetXtreme BCM5764M Gigabit Ethernet PCIe
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:08:00.0
       logical name: eth0
       version: 10
       serial: 00:23:8b:46:90:1a
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=tg3 driverversion=3.94 ip=192.168.2.102 latency=0 module=tg3 multicast=yes
  *-network
       description: Wireless interface
       product: AR928X Wireless Network Adapter (PCI-Express)
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:0b:00.0
       logical name: wlan0
       version: 01
       serial: 00:17:c4:56:06:c4
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ath9k latency=0 module=ath9k multicast=yes wireless=IEEE 802.11bgn
  *-network DISABLED
       description: Ethernet interface
       physical id: 2
       logical name: pan0
       serial: ea:f0:06:95:d1:a3
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A multicast=yes

statik@statik-laptop:~$ dmesg | tail
[  184.029646] tg3: eth0: Link is up at 100 Mbps, full duplex.
[  184.029652] tg3: eth0: Flow control is on for TX and on for RX.
[  184.030571] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[  193.428398] tg3 0000:08:00.0: irq 2299 for MSI/MSI-X
[  193.577027] ADDRCONF(NETDEV_UP): eth0: link is not ready
[  195.131559] tg3: eth0: Link is up at 100 Mbps, full duplex.
[  195.131565] tg3: eth0: Flow control is on for TX and on for RX.
[  195.132401] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[  205.652030] eth0: no IPv6 routers present
[  251.169204] ADDRCONF(NETDEV_UP): wlan0: link is not ready

```

ath9k seems to be working, but something else is off.

statik

---

### Post by pytheas22 on 2009-08-29
Yeah, that's really bizarre.  What exactly is the error message wicd is giving you?  If you specify 'wlan0' as the wireless interface in the wicd preferences, does it work or does it still think wlan0 doesn't exist?

---

### Post by Statik on 2009-08-30
wlan0 is specified as the wireless interface. There is no error. On the main screen of wicd, it shows the wireless interface with options to disconnect and a down arrow to changed wired profile, scripts, advanced settings. Under it is the message: 
```
No Wireless Networks Found
```
there are no options that go with that.

Statik

Edit: Tried to setup the wlan0 connection manually. Weird:

```
statik@statik-laptop:~$ iwconfig wlan0 essid statik-home mode managed txpower auto key s:************* commit
Error for wireless request "Set ESSID" (8B1A) :
    SET failed on device wlan0 ; Operation not permitted.

```

( thats not the real key, of course )

---

### Post by pytheas22 on 2009-08-30
Try bringing wlan0 down before setting the connection manually, and also kill the wicd daemon.  So:
```

sudo /etc/init.d/wicd stop
sudo ifconfig wlan0 down
sudo iwconfig wlan0 essid statik-home mode managed txpower auto key s:************* commit
sudo ifconfig wlan0 up
sudo dhclient wlan0
```

Sometimes that makes a difference for some reason.  It would be good to know if you can hold a stable connection when you connect manually.

Ohterwise, the behavior you describe in wicd seems very strange and I'm not really sure why it would do that.

---

### Post by Statik on 2009-08-30
So, I did a full re-install, formatting the drive, but keeping my /home partition safe.

After doing the updates I followed the directions for the compat wireless drivers and the network comes up, associates fine, even survives the one reboot I've done so far.

However, the network continues to take breaks. The best I can find for information during the breaks is:
```
statik@statik-laptop:~$ dmesg | tail
[   40.618654] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[   51.361028] wlan0: no IPv6 routers present
[ 1666.304052] No probe response from AP ffff88006d971e20 after 500ms, disconnecting.
[ 1667.414910] wlan0: direct probe to AP ffff88006752bc48 (try 1)
[ 1667.417603] wlan0 direct probe responded
[ 1667.417609] wlan0: authenticate with AP ffff88006752bc48 (try 1)
[ 1667.432637] wlan0: authenticated
[ 1667.432669] wlan0: associate with AP ffff88006752bc48 (try 1)
[ 1667.435063] wlan0: RX ReassocResp from ffff88004c51e04a (capab=0x431 status=0 aid=1)
[ 1667.435067] wlan0: associated

```

Not sure yet if its a router or a wireless issue yet.

BTW, I think the compat-wireless instructions are wrong. I think its supposed to be make install, make unload and then make load.

Statik

---

### Post by pytheas22 on 2009-08-31
hmmm, that dmesg output doesn't really tell much.  The only thing that stands out is the bit about "No probe response from AP..."  Sometimes this happens if you're far from the router and/or there's a lot of interference from other sources.  It could help to change your wireless channel if there are other networks in range on the same one, or move the router away from appliances that could interfere with it.  Apart from that, I'm not sure what to do.  It would be interesting to see if the connection drops on all routers, or just this one.

> BTW, I think the compat-wireless instructions are wrong. I think its supposed to be make install, make unload and then make load.

Yes, I think you're right about that.

---

### Post by Statik on 2009-08-31
Well, I don't have another router to test with, but I did take my laptop to work and setup a network between my laptop and another. It was limited to 802.11g, but it didn't have any trouble and worked great. I'm thinking the new ath9k driver is working as its supposed to and the router might be the trouble.

I'm going to see if changing the laptop location, as well as changing the protocal from n-draft to g, makes a difference.

Statik

---

### Post by hanzo_kunai on 2009-09-01
here the code pytheas 
**lshw -C network**
 *-network
       description: Wireless interface
       product: AR928X Wireless Network Adapter (PCI-Express)
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:05:00.0
       logical name: wmaster0
       version: 01
       serial: 00:17:c4:81:4e:59
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=ath9k ip=10.134.10.113 latency=0 module=ath9k multicast=yes wireless=IEEE 802.11bgn
  *-network UNCLAIMED
       description: Ethernet controller
       product: Attansic Technology Corp.
       vendor: Attansic Technology Corp.
       physical id: 0
       bus info: pci@0000:06:00.0
       version: c0
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress vpd bus_master cap_list
       configuration: latency=0
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: 2a:25:41:16:f4:db
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes
**uname -r**
2.6.28-11-generic
**dmesg | grep -e atl -e eth -e wlan -e ath**
[    2.446726] Driver 'sd' needs updating - please use bus_type methods
[    2.446741] Driver 'sr' needs updating - please use bus_type methods
[    5.241560] device-mapper: multipath: version 1.0.5 loaded          
[    5.241563] device-mapper: multipath round-robin: version 1.0.0 loaded
[    9.690219] ath9k: 0.1                                                
[    9.690270] ath9k 0000:05:00.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    9.690280] ath9k 0000:05:00.0: setting latency timer to 64               
[   10.122531] phy0: Selected rate control algorithm 'ath9k_rate_control'    
[   10.326618] Registered led device: ath9k-phy0:radio                       
[   10.326634] Registered led device: ath9k-phy0:assoc                       
[   10.326649] Registered led device: ath9k-phy0:tx                          
[   10.326665] Registered led device: ath9k-phy0:rx                          
[   18.758605] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   19.440505] wlan0: direct probe to AP 00:02:6f:47:99:67 try 1
[   19.636040] wlan0: direct probe to AP 00:02:6f:47:99:67 try 2
[   19.836033] wlan0: direct probe to AP 00:02:6f:47:99:67 try 3
[   20.037073] wlan0: direct probe to AP 00:02:6f:47:99:67 timed out
[  180.526452] wlan0: direct probe to AP 00:02:6f:47:99:67 try 1
[  180.725048] wlan0: direct probe to AP 00:02:6f:47:99:67 try 2
[  180.925077] wlan0: direct probe to AP 00:02:6f:47:99:67 try 3
[  181.125033] wlan0: direct probe to AP 00:02:6f:47:99:67 timed out
[  210.969993] wlan0: authenticate with AP 00:18:f8:33:60:46
[  210.971539] wlan0: authenticated
[  210.971551] wlan0: associate with AP 00:18:f8:33:60:46
[  210.974525] wlan0: RX AssocResp from 00:18:f8:33:60:46 (capab=0x431 status=0aid=3)
[  210.974535] wlan0: associated
[  210.986851] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[  221.940056] wlan0: no IPv6 routers present
[  271.423386] wlan0 direct probe responded
[  271.423405] wlan0: authenticate with AP 00:18:f8:33:60:46
[  271.425953] wlan0: authenticated
[  271.425965] wlan0: associate with AP 00:18:f8:33:60:46
[  271.430492] wlan0: RX ReassocResp from 00:18:f8:33:60:46 (capab=0x431 status=0 aid=3)
[  271.430501] wlan0: associated
[  275.389907] wlan0: deauthenticated
[  276.388045] wlan0: direct probe to AP 00:18:f8:33:60:46 try 1
[  276.588090] wlan0: direct probe to AP 00:18:f8:33:60:46 try 2
[  276.589999] wlan0 direct probe responded
[  276.590011] wlan0: authenticate with AP 00:18:f8:33:60:46
[  276.591760] wlan0: authenticated
[  276.591770] wlan0: associate with AP 00:18:f8:33:60:46
[  276.595242] wlan0: RX ReassocResp from 00:18:f8:33:60:46 (capab=0x431 status=0 aid=3)
[  276.595252] wlan0: associated
**lspci -nn | grep -ie ethernet -e network**
05:00.0 Network controller [0280]: Atheros Communications Inc. AR928X Wireless Network Adapter (PCI-Express) [168c:002a] (rev 01)
06:00.0 Ethernet controller [0200]: Attansic Technology Corp. Device [1969:1063] (rev c0)

---

### Post by pytheas22 on 2009-09-01
**hanzo_kunai**: please try following the instructions in [this thread]("http://ubuntuforums.org/showthread.php?t=1255082").  They should make the ethernet work.  If it still doesn't work after that, please post the output of:
```

dmesg | grep -e arl -e eth
lshw -C Network
ifconfig -a
```

---

### Post by hanzo_kunai on 2009-09-02
wow thanks pytheas:):):)

---

