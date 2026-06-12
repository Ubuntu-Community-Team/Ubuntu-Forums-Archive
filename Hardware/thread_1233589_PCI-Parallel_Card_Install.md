---
title: "PCI-Parallel Card Install"
date: 2009-08-06
forum: Hardware
---

### Post by darolu on 2009-08-06
I bought a PCI Parallel controller card so I can use my printer (as my motherboard doesn't have parallel port); I had already installed Ubuntu 9.04 64-bit and now I need to configure the PCI-Card but I don't know how to do it. I read a [guide]("http://www.lavalink.com/index.php?id=472") that includes editing "/etc/conf.modules" file but Ubuntu doesn't use it and I'm completely out of ideas.

This is what "lspci -v" displays:
```
03:07.0 Parallel controller: NetMos Technology PCI 9865 Multi-I/O Controller (prog-if 03)
	Subsystem: Device a000:2000
	Flags: bus master, medium devsel, latency 32, IRQ 3
	I/O ports at cf00 [size=8]
	I/O ports at ce00 [size=8]
	Memory at fdeff000 (32-bit, non-prefetchable) [size=4K]
	Memory at fdefe000 (32-bit, non-prefetchable) [size=4K]
	Capabilities: [48] Power Management version 2
```

How can I install my PCI-Parallel Card?

Thanks.

---

### Post by shaileshjkumar on 2009-08-07
I was working on the serial connection.
Had this working with lot of researching on this..... was earlier using Ubuntu 9.04 with Kernel 2.6.28.
I also sent mails to Moschip Support and the below is ehat they replied:

[I]"I think you are using MCS9865 in 2.6.28 kernel. We have driver support up to 2.6.25 only and we will update the driver soon.

Thanks and Regards,

Moschip Support Team"[/I]

Then I went back to Ubuntu 8.04 with Kernel 2.6.24, but something was still missing and then I mailed back to the support, below is the reply:


[I]"Shailesh:
I installed Ubuntu 8.04 with kernel 2.6.24 and then installed MCS9865 driver. I have four of the serial pci cards so it will get me 2X4=8 Ports.

It seems that when installing the driver it created ttyD0 to ttyD7 in the dev directory.

I am able to connect to the onboard the motherboard serial ports device with no issues. 

Earlier I was not able to connect to the devices on MCS9865 cards, but after installing the 2.6.24 kernel I am able to connect, BUT it&#8217;s giving me garbled character set on the terminal. I test it with the ones which are on board and the same device is working OK, BUT the same device on the MCS9865 is not working right.

What setting would I have to do for the system to recognize the serial ports as &#8220;ttyS*&#8221;?

[COLOR="blue"]Moschip:       After installing the driver of MCS9865 use the below commands to convert /dev/ttyDx to /dev/ttySx 

# ln &#8211;sf /dev/ttyD0 /dev/ttyS2

To conform use the following command

# ll /dev/ttyD0

A link will be shown to ttyS2 like (/dev/ttyD0 --à /dev/ttyS2)

Note: Make sure the destination ports should free to occupy.[/COLOR]

Shailesh: What setting I have to do for the driver to be loaded properly, as after a reboot I have to install the drivers again?

[COLOR="blue"]Moschip:       No need to install again after reboot if you use &#8220;make install&#8221; command.[/COLOR]

What setting I have to do for the terminal to give me a proper connection?

[COLOR="Blue"]Moschip:       We didn&#8217;t understand this question. However use the attached latest driver and see whether you could overcome this problem or not.[/COLOR]"

I did install the drivers he sent and finally with a little tweaks on the settings end based on my devices the server is up and running.[/I]

Though its the same drivers available on their website, If you want let me know an email ID I can send you the drivers.

I am using this program to connect to the serial ports, amazing this it lets you connect all port at the same time in different terminals: [http://dl.getdropbox.com/u/738335/serial.c.txt](http://dl.getdropbox.com/u/738335/serial.c.txt)

---

### Post by darolu on 2009-08-07
Thanks for the reply; so basically I can't install it on Jaunty... that sucks; well I'll install 8.04 and try it.

---

### Post by joecrow on 2009-10-29
NetMos Technology PCI 9865 Parallel Controller card install how-to for Ubuntu

Well, I do not have a parallel port on my computer so I bought a cheap card on Ebay. It is a no name card that came with a driver cdrom and a Linux driver called msc9865_Linux. I couldn't "Make" or "compile" anything from the driver. The instructions were to vague and after googling, it seems the driver was to old and the manufacturer stopped supporting it. I eventually found a tutorial by Lazly at [http://lazly.hu/q/netmos-technology-pci-9865-parallel-controller-install-howto-ubuntu-904-english](http://lazly.hu/q/netmos-technology-pci-9865-parallel-controller-install-howto-ubuntu-904-english) which worked for me. It was not very detailed but I managed. Even though it is already in English, I modified and rewrote it here so it makes more sense and added more detailes.

Im using ubuntu 8.10 but this will work with 9.04 and others. As I explained above, I too tried to install an old printer with a parallel card and was going around in circles with the driver and installation instructions. I googled 'til my fingers were raw and still nothing. However, the following how-to solved my problem without using any driver!

First, make sure your system "sees" the card with the following:
    $ sudo lspci
      ...
      03:06.2 Parallel controller: NetMos Technology PCI 9865 Multi-I/O Controller
      ...
Scroll down until you see something similar to the above. As you can see, my system sees the card and identified the parallel port. By the way, there were two serial ports listed on the same card. Which I will not be using. Anyway,...

    $ sudo cat /proc/ioports | grep parport
      <nothing>

    $ sudo modprobe -r lp
    $ sudo modprobe -r parport_pc

    $ sudo lspci -v
       ...
       03:06.2 Parallel controller: NetMos Technology PCI 9865 Multi-I/O Controller (prog-if 03)
    Subsystem: Device a000:2000
    Flags: bus master, medium devsel, latency 64, IRQ 10
    I/O ports at e000 [size=8]
    I/O ports at d800 [size=8]
    Memory at febfb000 (32-bit, non-prefetchable) [size=4K]
    Memory at febfa000 (32-bit, non-prefetchable) [size=4K]
    Capabilities: [48] Power Management version 2
       ...
Note the I/O port above listed as being at e000. It will probably be different on yours. In the following command replace mine with whatever yours may be.

    $ sudo modprobe parport_pc io=0xe000
    $ sudo modprobe lp

    $ sudo /etc/init.d/cups restart

At this point, my printer started printing so I stopped, but you may need to install your printer drivers. If that is the case, Use the official Ubuntu printer setup GUI.

Before you reboot your system, you still need to edit a couple of files so you can keep printing when the system is restarted. The first file, has to be created and the info added to it. The second file should already exist so you just need to add the line to it. So go ahead and create the file "parport_pc" in the directory as indicated below. Then edit it with your fav text editor. I used Nano in my examples.

    $ sudo nano /etc/modprobe.d/parport_pc
    options parport_pc io=0xe000

Once the file "parport_pc" is created and the option above is added, edit the next file to make sure it all works after rebooting.
    $ sudo nano /etc/modules
    ...
    parport_pc
    lp
    ...

That's all. I've been using Ubuntu for a year now and love it but I'm not an expert so maybe other here can further help you along. I hope this method helps others. Later, JoeCrow

---

### Post by darolu on 2009-11-13
First sorry I replied until now, I couldn't use this computer until today.

And secondly, a big thank you. It worked perfectly, thanks a lot.

---

### Post by joecrow on 2009-11-24
You are welcome! I was beginning to wonder if it had worked for you. I'm glad it did.

---

### Post by chrone on 2010-10-27
> **joecrow said:**
> You are welcome! I was beginning to wonder if it had worked for you. I'm glad it did.

thanks dude, it really helps! :)

hope ubuntu will support this out of the box. since most of office still use parallel port for their business application, but newer motherboards don't support them no more. this pci to lpt card is a bless from the sky. :D

---

### Post by doug.metzler on 2011-08-04
I'm following Joe's great instructions but I notice when i do an lspci -v the ports are showing up as disabled:

02:0b.0 Parallel controller: NetMos Technology PCI 9865 Multi-I/O Controller (prog-if 03)
    Subsystem: Device a000:2000
    Flags: bus master, medium devsel, latency 32, IRQ 255
    I/O ports at a400 [disabled] [size=8]
    I/O ports at a000 [disabled] [size=8]
    Memory at eb000000 (32-bit, non-prefetchable) [disabled] [size=4K]
    Memory at ea800000 (32-bit, non-prefetchable) [disabled] [size=4K]
    Capabilities: <access denied>

02:0b.2 Parallel controller: NetMos Technology PCI 9865 Multi-I/O Controller (prog-if 03)
    Subsystem: Device a000:2000
    Flags: bus master, medium devsel, latency 32, IRQ 255
    I/O ports at 9800 [disabled] [size=8]
    I/O ports at 9400 [disabled] [size=8]
    Memory at ea000000 (32-bit, non-prefetchable) [disabled] [size=4K]
    Memory at e9800000 (32-bit, non-prefetchable) [disabled] [size=4K]
    Capabilities: <access denied>

I assume I missed a step somewhere - can anyone point me in the right direction?

Thanks,

DougM

---

### Post by david.jamieson@gmail.com on 2011-09-12
you need to run the lspci -v command as root

sudo lspci -v that gives you a different output under at the capabilities tag, caught me out then I found another post with the sudo option listed. Hope that helps.

---

### Post by pedricus on 2011-11-17
Thanks joecrow! your instructions are great, unfortunatly i'm still not quite there! i have my add on card installed, and ubuntu seems to detect it, but i can't get it loaded correctly and functional.  

echo "hello" > /dev/lp0" does nothing, and dmesg replies back with 

parport0: BUSY timeout (-4) in compat_write_block_pio

hope you can help!

here are some other outputs i ran:

# lsmod | grep lp
drm_kms_helper         30774  1 nouveau
drm                   198532  3 nouveau,ttm,drm_kms_helper
lp                      9336  0
parport                37160  3 ppdev,parport_pc,lp

# lsmod | grep ppdev
ppdev                   6375  0
parport                37160  3 ppdev,parport_pc,lp

# lsmod | grep parport_pc
parport_pc             29958  1
parport                37160  3 ppdev,parport_pc,lp

# dmesg | grep par
[    0.000000] Booting paravirtualized kernel on bare hardware
[    0.672930] pci 0000:00:04.0: transparent bridge
[    0.711921] hpet0: 3 comparators, 32-bit 25.000000 MHz counter
[    2.705066]  unknown partition table
[    2.705169]  md1: unknown partition table
[    6.079002] parport_pc 00:08: reported by Plug and Play ACPI
[    6.079060] parport0: PC-style at 0x378 (0x778), irq 7, dma 3 [PCSPP,TRISTATE,COMPAT,ECP,DMA]
[    6.091417] ppdev: user-space parallel port driver
[    6.094442]  unknown partition table
[    6.161434] lp0: using parport0 (interrupt-driven).
[    7.285811] nf_conntrack.acct=1 kernel parameter, acct=1 nf_conntrack module option or
[  138.803811] parport0: BUSY timeout (-4) in compat_write_block_pio

# ls -l /dev/lp* /dev/parport*
crw-rw---- 1 root lp  6, 0 2011-11-17 11:50 /dev/lp0
crw-rw---- 1 root lp 99, 0 2011-11-17 11:50 /dev/parport0

# lshw | less
~
        *-communication:2 UNCLAIMED
             description: Parallel controller
             product: PCI 9865 Multi-I/O Controller
             vendor: NetMos Technology
             physical id: 6.2
             bus info: pci@0000:01:06.2
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list
             configuration: latency=32
             resources: ioport:c400(size=8) ioport:c000(size=8) memory:fd8fb000-fd8fbfff memory:fd8fa000-fd8fafff

# lspci -v | less
~
01:06.2 Parallel controller: NetMos Technology PCI 9865 Multi-I/O Controller (prog-if 03)
        Subsystem: Device a000:2000
        Flags: bus master, medium devsel, latency 32, IRQ 5
        I/O ports at c400 [size=8]
        I/O ports at c000 [size=8]
        Memory at fd8fb000 (32-bit, non-prefetchable) [size=4K]
        Memory at fd8fa000 (32-bit, non-prefetchable) [size=4K]
        Capabilities: [48] Power Management version 2

---

