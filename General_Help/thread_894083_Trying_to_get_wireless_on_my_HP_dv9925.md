---
title: "Trying to get wireless on my HP dv9925"
date: 2008-08-18
forum: General Help
---

### Post by rosen561 on 2008-08-18
Hey,
 
I just loaded Ubuntu 8.04 64 bit version onto my HP Pavillion dv9925nr, AMD Turion X2 64-bit processor, and I can't for the life of me get wireless to work. It has a Broadcom wireless lan card (BCM4322 802.11a/b/g/n), for which many google searches has told me to use ndiswrapper. I followed the directions in this post  ([http://ubuntuforums.org/showthread.php?p=4808350#post4808350](http://ubuntuforums.org/showthread.php?p=4808350#post4808350)) verbatim (I realize it was with a different card, but it was the clearest directions i could find, and I figured it'd work) but still get nothing.

I'm pretty new to linux, started using it at the beginning of the summer, due to my complete frustration with windows (though I'm also running Vista alongside ubuntu), and was really happy with it on my old desktop, so I hope someone can help

Thanks

---

### Post by rosen561 on 2008-08-28
Got it--http://ubuntuforums.org/showthread.php?t=880218

---

### Post by Crafty Kisses on 2008-08-28
Post the results of this command:
```
lshw -C network
```

---

### Post by jonian_g on 2008-08-29
First, you must have the 64bit windows drivers of your wireless card.

Then, you need to install Windows Wireless Drivers (ndisgtk= gui tool for ndiswrapper). Install it from Applications>Add/Remove or open a terminal and type:

```
sudo apt-get install ndisgtk
```

Once installed go to System>Admin>Windows Wireless Drivers and click on Install new drivers. Navigate to the folder you have saved the drivers and select the .inf file and then click install and you are done.

---

### Post by dokuro on 2008-09-04
PROBLEM, i can't seem to find a link that would give me a .inf file i downloaded only .exe, how can this be?

you know, this laptops come with 3 different types of wireless cards! jejeje...

-broadcom
-intel
-atheros 

and a bluetooth thing

the command above gives the brand, in my model dv9925nr (see the nr at the end) is a Broadcom

---

### Post by xentrix1220 on 2008-09-12
ok tryed ndiswrapper  as mentioned on this post. Also the guide here [http://ubuntuforums.org/showthread.php?t=885847](http://ubuntuforums.org/showthread.php?t=885847). Apprently it can not load my driver heres the code i got any ideas?

```
mattandelise@mattandelise-laptop:~$ lshw -C network
WARNING: you should run this program as super-user.
  *-network               
       description: Ethernet interface
       product: MCP67 Ethernet
       vendor: nVidia Corporation
       physical id: a
       bus info: pci@0000:00:0a.0
       logical name: eth0
       version: a2
       serial: 00:1e:68:80:5b:8b
       width: 32 bits
       clock: 66MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=forcedeth driverversion=0.61 ip=192.168.0.186 latency=0 maxlatency=20 mingnt=1 module=forcedeth multicast=yes
  *-network UNCLAIMED
       description: Network controller
       product: BCM4328 802.11a/b/g/n
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       version: 03
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: latency=0
mattandelise@mattandelise-laptop:~$ ndiswrapper -l
bcmwl6 : driver installed
	device (14E4:4328) present
mattandelise@mattandelise-laptop:~$ uname-m
bash: uname-m: command not found
mattandelise@mattandelise-laptop:~$ uname -m
x86_64
mattandelise@mattandelise-laptop:~$ lshw -C
Hardware Lister (lshw) - B.02.12.01
usage: lshw [-format] [-options ...]
       lshw -version

	-version        print program version (B.02.12.01)

format can be
	-html           output hardware tree as HTML
	-xml            output hardware tree as XML
	-short          output hardware paths
	-businfo        output bus information

options can be
	-class CLASS    only show a certain class of hardware
	-C CLASS        same as '-class CLASS'
	-disable TEST   disable a test (like pci, isapnp, cpuid, etc. )
	-enable TEST    enable a test (like pci, isapnp, cpuid, etc. )
	-quiet          don't display status
	-sanitize       sanitize output (remove sensitive information like serial numbers, etc.)

mattandelise@mattandelise-laptop:~$ lshw-C
bash: lshw-C: command not found
mattandelise@mattandelise-laptop:~$ lshw -C Network
WARNING: you should run this program as super-user.
  *-network               
       description: Ethernet interface
       product: MCP67 Ethernet
       vendor: nVidia Corporation
       physical id: a
       bus info: pci@0000:00:0a.0
       logical name: eth0
       version: a2
       serial: 00:1e:68:80:5b:8b
       width: 32 bits
       clock: 66MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=forcedeth driverversion=0.61 ip=192.168.0.186 latency=0 maxlatency=20 mingnt=1 module=forcedeth multicast=yes
  *-network UNCLAIMED
       description: Network controller
       product: BCM4328 802.11a/b/g/n
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       version: 03
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: latency=0
mattandelise@mattandelise-laptop:~$ sudo gedit /etc/modprobe.d/blacklist
[sudo] password for mattandelise: 
mattandelise@mattandelise-laptop:~$ lsmod | grep ndis
ndiswrapper           243872  0 
usbcore               169904  5 uvcvideo,ndiswrapper,ohci_hcd,ehci_hcd
mattandelise@mattandelise-laptop:~$ sudo modprobe ndiswrapper
mattandelise@mattandelise-laptop:~$ dmesg | grep -e ndis -e wlan
[   34.912554] ndiswrapper version 1.52 loaded (smp=yes, preempt=no)
[   35.481518] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMSetBusData'
[   35.481532] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMRegisterInterruptEx'
[   35.481540] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMIndicateStatusEx'
[   35.481547] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisAllocateMdl'
[   35.481555] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMDeregisterInterruptEx'
[   35.481562] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisFreeMdl'
[   35.481572] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisFreeNetBufferList'
[   35.481579] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisAllocateNetBufferAndNetBufferList'
[   35.481597] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMSynchronizeWithInterruptEx'
[   35.481608] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMDeregisterScatterGatherDma'
[   35.481616] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMSetMiniportAttributes'
[   35.481623] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMRegisterMiniportDriver'
[   35.481631] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisFreeNetBufferListPool'
[   35.481643] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisFreeIoWorkItem'
[   35.481650] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMDeregisterMiniportDriver'
[   35.481658] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMRegisterScatterGatherDma'
[   35.481666] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMSendNetBufferListsComplete'
[   35.481681] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisAllocateIoWorkItem'
[   35.481692] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisAllocateMemoryWithTagPriority'
[   35.481702] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMOidRequestComplete'
[   35.481710] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisOpenConfigurationEx'
[   35.481717] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMGetBusData'
[   35.481724] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMIndicateReceiveNetBufferLists'
[   35.481731] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisQueueIoWorkItem'
[   35.481746] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisAllocateNetBufferListPool'
[   35.481754] ndiswrapper (load_sys_files:210): couldn't prepare driver 'bcmwl6'
[   35.482414] ndiswrapper (load_wrap_driver:112): couldn't load driver bcmwl6; check system log for messages from 'loadndisdriver'
[   35.482478] usbcore: registered new interface driver ndiswrapper
mattandelise@mattandelise-laptop:~$ 


```

---

### Post by anglina on 2009-07-16
I have been PLAGUED with the problem of getting all of my onboard hardware on my HP DV9925NR to work. 

I kept a small windows install on the side just to do simple wireless or Skype use as needed. I looked for WEEKS for a solution. Scoured the forums. There WAS nothing.

Onboard Mic didn't work, Wireless card didn't work properly

Those are kinda big issues for me. 

I run a small computer repair business and I would have to boot into my windows install just to check someone's wireless router for them. (No way I am carrying cable, I know I'm a snob)

I was able to get everything to work perfectly by upgrading to Karmic. To upgrade to Karmic, use update-manager -d
[http://www.ubuntu.com/testing/karmic/alpha2](http://www.ubuntu.com/testing/karmic/alpha2)
It mentioned using the run command hotkey (Alt-F2) but I just did it in terminal. [Yakuake actually :wink:] [http://en.wikipedia.org/wiki/Yakuake](http://en.wikipedia.org/wiki/Yakuake)


Remember Karmic is in Alpha and if you are not a fan of Alpha then your loss. I have NEVER had problems with Karmic. Everything works. You couldn't get me to believe that it is an Alpha and not a full release!!

Downloaded and Installed the updates followed by restarts then installed Skype like I usually do by adding the Medibuntu Repository followed by sudo apt-get install skype
[http://www.clububuntu.com/2009/04/ho...epository.html]("http://www.clububuntu.com/2009/04/how-to-add-medibuntu-repository.html")

Did my test call and it finally worked.

To get my NVIDIA Graphics and Wireless to Work I had to enable the use of the drivers.

System -> Administration -> Hardware Drivers

Click the balls to the left of the drivers to turn them green (meaning on) and restart. The Wireless drivers make the wireless card work great and you can use the switch too! I had found a way on a different post about using a command line thing to get it to work but you had to do a bunch of stuff to get it to work and you had to do it every time. UGH!

Hope this helps anybody!!

---

