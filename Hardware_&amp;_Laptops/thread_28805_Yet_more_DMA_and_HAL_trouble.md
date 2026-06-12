---
title: "Yet more DMA and HAL trouble"
date: 2005-04-21
forum: Hardware &amp; Laptops
---

### Post by hobnob on 2005-04-21
Like many others here, I am having problems setting DMA on either of my optical drives (/dev/hda and /dev/hdc), getting the error "HDIO_SET_DMA failed: Operation not permitted". I have followed all the possible tricks posted, but I am getting *very* strange results. Here is a brief summary, and I would be very interested to hear if anyone is having similar problems, or has any suggestions for a fix!

If I place 'via82cxxx' at the top of /etc/modules, and reboot, I get the following outcomes:

i) it *sometimes* boots up without any problems and I can enable DMA on one of my drives. However, if I try 'hdparm -d1 /dev/hda', the process hangs and I cannot kill it.

ii) the computer boots into GNOME, but then I get no background, no panels and a "failed to initialize HAL" message appear. If I restart dbus-1, the desktop comes back, but the taskbar does not show open windows. Similar state of affairs with hdparm as above.

iii) the boot process hangs at "Starting Enterprise Volume Management System". I have had to boot a rescue live cd to edit /etc/modules before the system will reboot. Even more strangely, if I leave hda's cd tray open during bootup, it is closed at the same time as "Starting EVMS.." but if I catch it before it closes, the system continues to boot. Don't ask how I found this out!

Now I don't think it is EVMS causing the problems, as when I select the 'recovery mode' in GRUB, iii) happens when "Setting up LVM Volume Groups..." appears. I am guessing a backgrounded process, perhaps the loading of a module, is causing the hang.

I have read elsewhere that adding 'via82cxxx' to the top of /etc/modules gives a clean first reboot, but subsequent boots lead to problems. I get similar results, but cannot explain this.

If anyone has any idea where the problem may be coming from, I would love to hear them. I know it is not the CD drive itself, as it works perfectly well with DMA enabled in all other distributions I have tried.

Thanks!

Athlon64 3500 on Asus A8V Deluxe (similar problems on linux-386 and linux-k7 kernels).
hda: ASUS DVD-E616P2, ATAPI CD/DVD-ROM drive
hdc: _NEC DVD_RW ND-3500AG, ATAPI CD/DVD-ROM drive

---

### Post by Koxman on 2005-04-22
I have the same problems here:

0000:00:00.0 Host bridge: VIA Technologies, Inc.: Unknown device 0258
0000:00:00.1 Host bridge: VIA Technologies, Inc.: Unknown device 1258
0000:00:00.2 Host bridge: VIA Technologies, Inc.: Unknown device 2258
0000:00:00.3 Host bridge: VIA Technologies, Inc.: Unknown device 3258
0000:00:00.4 Host bridge: VIA Technologies, Inc.: Unknown device 4258
0000:00:00.7 Host bridge: VIA Technologies, Inc.: Unknown device 7258
0000:00:01.0 PCI bridge: VIA Technologies, Inc. VT8237 PCI Bridge
0000:00:0b.0 Multimedia audio controller: Creative Labs SB Live! EMU10k1 (rev 08)
0000:00:0b.1 Input device controller: Creative Labs SB Live! MIDI/Game Port (rev 08)
0000:00:0c.0 Multimedia video controller: Brooktree Corporation Bt878 Video Capture (rev 11)
0000:00:0c.1 Multimedia controller: Brooktree Corporation Bt878 Audio Capture (rev 11)
0000:00:0f.0 RAID bus controller: VIA Technologies, Inc. VIA VT6420 SATA RAID Controller (rev 80)
0000:00:0f.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 06)
0000:00:10.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
0000:00:10.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
0000:00:10.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
0000:00:10.3 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
0000:00:10.4 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 86)
0000:00:11.0 ISA bridge: VIA Technologies, Inc. VT8237 ISA bridge [K8T800 South]
0000:00:12.0 Ethernet controller: VIA Technologies, Inc. VT6102 [Rhine-II] (rev 78)
0000:01:00.0 VGA compatible controller: nVidia Corporation: Unknown device 00f1 (rev a2)

If I start ubuntu normally, I cannot enter gnome correctly because of the "failed to initialize HAL" Problem. So I start it with the kernelparameter NOAPIC which lets me use the system nearly normal

but when I want to enable DMA on my DVD+/-RW then I get

sudo hdparm -d1 /dev/hda

/dev/hda:
 setting using_dma to 1 (on)
 HDIO_SET_DMA failed: Operation not permitted
 using_dma    =  0 (off)

I use the normal 2.6.10-5-386 kernel (because the system is more unstable with the 2.6.11 686 kernel)

---

### Post by Koxman on 2005-04-22
Ok .. it seems that I have solved most of my problems.

first: DMA

this is my /etc/modules now

# ide-cd
# ide-disk
# ide-generic
lp
mousedev
psmouse
nvidia
bttv tuner=37

after this the 
sudo hdparm /dev/hda
works now. . I first had problems with my dvd+/-RW burner (like hanging) but after a restart it worked .. you might enable hdparm now in /etc/hdparm.conf

second .. the HAL problem was that the wacom tablet was connected to an usb2.0 device and I got funny messages

you can see this in "dmesg" with timeout from device ep0?? something repeatingly
also lsusb is hanging

when restarting the "hotplug" service you might get it running. I disconnected the wacom tablet and now it works without problems

---

### Post by hobnob on 2005-04-23
Well I have pulled the stalling CD drive out, and all works perfectly well. It's an Asus E616P2, which claims to be Linux compatible, so I think it is just faulty.

In the process I found that removing ide-generic and blacklisting it in hotplug enabled me to boot the system, but didn't get around hanging hdparm. Now I have just restored all back to the default Hoary install and preprended 'via82cxxx' to /etc/modules and all works well.

---

### Post by brj on 2005-05-25
hi,

my problems with HAL stopped after i removed the dma-settings for the dvd-rom and dvd-burner from /etc/hdparm.conf. 
when everything is running i can successfully set dma of the dvd-drives from command line.

jakob

---

### Post by milou on 2005-05-25
I have exactly the same troubles ! I tried another distribution : Fedora Core 4 Test 3 and I don't have these troubles. However I would like to stick with Ubuntu, but as I searched through the forums, I saw a lot of similar behaviour but no obvious solution, however there MUST be one, I mean at least an explanation, since other dist work out of the rock !

Eric

---

### Post by logan2004 on 2005-05-25
upgrade your firmware

---

### Post by brj on 2005-05-26
the same dvd-drives with exactly the same firmware run without problems with win XP !

jakob

---

### Post by milou on 2005-05-26
[QUOTE=logan2004]upgrade your firmware[/QUOTE]

1) There is no firmware upgrade for my 2 drives yet ( Pioneer DVD-RW K14RA and Panasonic DVDROM SR-8178 )

2) I have no problem with FC4 Test 3 which means it works with another linux distribution so ....

---

### Post by kwennemar on 2005-05-28
](*,) I have to agree with milou, there needs to be a resolution with this problem.  I find it hard to tell people with confidence that they will have no problems with their computer if they let me load Ubuntu on it.  

The resolution that I have found with the intermitent zombie HAL is to telinit 1 then enter gdm.  Everything works great then.  

Why do I get intermitent zombies?  If you want I will send copies of my config files.

---

### Post by ktogias on 2005-05-28
I had the same problem on a pc with one hard disk at /dev/hda , one cdrw at /dev/hdc and one dvdrom at /dev/hdd:

After boot and after logging in with gdm, gnome panel and nautilus failed to start (No icons or menus on panel and no icons on desktop) and after a while the message "Failed to initialize HAL" occured. When at that state, a ps aux gave me 3 or 4 hdparm prosseces niced -10 . Randomly sometimes the system bootted normaly with no such problem.

The system bootted normaly when I gave the nohdparm option on boot. By experimenting with /etc/hdparm.conf , I found out that the problem only occured when both 

```
/dev/hdc {
        dma = on
}

/dev/hdd {
        dma = on
}
```


where uncommented in **/etc/hdparm.conf** .

The solution to I made up is this:

1 .I commented out both the above sections about /dev/hdc and /dev/hdd in /etc/hdparm.conf . My **/etc/hdparm.conf** seems like that now:

```
......

#/dev/hdc {
#        dma = on
#}

#/dev/hdd {
#        dma = on
#}
```

2. I created an init script "**/etc/init.d/cdroms_dma**" that enables dma for /dev/hdc and  /dev/hdd :

```
#! /bin/sh
# /etc/init.d/cdroms_dma
#

# Carry out specific functions when asked to by the system
case "$1" in
  start)
    echo "Enable DMA for /dev/hdc ..."
    hdparm -d 1 /dev/hdc
    sleep 1
    echo "Enable DMA for /dev/hdd ..."
    hdparm -d 1 /dev/hdd
    echo "DONE!"
    ;;
  stop)
    echo "Disable DMA for /dev/hdc ..."
    hdparm -d 0 /dev/hdc
    sleep 1
    echo "Disable DMA for /dev/hdd ..."
    hdparm -d 0 /dev/hdd
    echo "DONE!"
    ;;
  *)
    echo "Usage: /etc/init.d/cdroms_dma {start|stop}"
    exit 1
    ;;
esac

exit 0
```

and added it to rc.d with:

```
# update-rc.d cdroms_dma defaults
```

This way the system boots up normaly and I have dma on cdroms enabled on boot.
I have not tested it hard (only 3-4 boots) but it seems to work.

---

### Post by ozeroc on 2005-06-01
Hey all...

  I've been researching this problem and I figured it out.  

- I have an AMD64 on a mobo with nforce3 and I boot off a SATA drive.  

- I was having problems burning DVDs and found I needed to turn on DMA and I got the 'HDIO_SET_DMA failed: Operation not permitted' error.

- I read in Bugzilla that it was due to the ide_* drivers grabbing the devices too soon and setting them to PIO

- The supposed fix was to put AMD74xx first in my /etc/modules file so that it would get  to these ide devices first...  This caused my system to hang on bootup

- My fix was to edit /etc/hotplug/blacklist and add AMD74xx.  This allowed AMD74xx to be assigned from /etc/modules.  

-Command line test of 'sudo hdparm /dev/hda' was successful so I edited /etc/hdparm.conf to turn on DMA automatically at bootup and it works!

Yeah!  \\:D/ 

Oz

---

### Post by tseliot on 2005-06-17
[QUOTE=ktogias]I had the same problem on a pc with one hard disk at /dev/hda , one cdrw at /dev/hdc and one dvdrom at /dev/hdd:

After boot and after logging in with gdm, gnome panel and nautilus failed to start (No icons or menus on panel and no icons on desktop) and after a while the message "Failed to initialize HAL" occured. When at that state, a ps aux gave me 3 or 4 hdparm prosseces niced -10 . Randomly sometimes the system bootted normaly with no such problem.

The system bootted normaly when I gave the nohdparm option on boot. By experimenting with /etc/hdparm.conf , I found out that the problem only occured when both 

```
/dev/hdc {
        dma = on
}

/dev/hdd {
        dma = on
}
```


where uncommented in **/etc/hdparm.conf** .

The solution to I made up is this:

1 .I commented out both the above sections about /dev/hdc and /dev/hdd in /etc/hdparm.conf . My **/etc/hdparm.conf** seems like that now:

```
......

#/dev/hdc {
#        dma = on
#}

#/dev/hdd {
#        dma = on
#}
```

2. I created an init script "**/etc/init.d/cdroms_dma**" that enables dma for /dev/hdc and  /dev/hdd :

```
#! /bin/sh
# /etc/init.d/cdroms_dma
#

# Carry out specific functions when asked to by the system
case "$1" in
  start)
    echo "Enable DMA for /dev/hdc ..."
    hdparm -d 1 /dev/hdc
    sleep 1
    echo "Enable DMA for /dev/hdd ..."
    hdparm -d 1 /dev/hdd
    echo "DONE!"
    ;;
  stop)
    echo "Disable DMA for /dev/hdc ..."
    hdparm -d 0 /dev/hdc
    sleep 1
    echo "Disable DMA for /dev/hdd ..."
    hdparm -d 0 /dev/hdd
    echo "DONE!"
    ;;
  *)
    echo "Usage: /etc/init.d/cdroms_dma {start|stop}"
    exit 1
    ;;
esac

exit 0
```

and added it to rc.d with:

```
# update-rc.d cdroms_dma defaults
```

This way the system boots up normaly and I have dma on cdroms enabled on boot.
I have not tested it hard (only 3-4 boots) but it seems to work.[/QUOTE]


Unfortunately this didn't work for me.

 How can I remove it, please?

P.S. Did you do the script by using a text editor?

---

### Post by ktogias on 2005-06-20
I made the script with VIM text editor.

To stop the script from loading on boot you should run 
#update-rc.d cdroms_dma remove
as root (or sudo update-rc.d cdroms_dma remove as normal user....).
See man update-rc.d for more details on update-rc.d script.

When you say that it doesn't work, what do you mean? Do you get any error messages? If you'd like post the error messages you get and some info about your system (what devices your cdroms are), so we could find out what goes wrong... At my system the above solution really solved the problem (I have no hangups since I made it, for about a month now...)

---

### Post by grinias on 2005-08-25
It worked for me, too! But i had to do

#sudo chmod 0755 /etc/init.d/cdroms_dma

before rebooting.

Thanx, anyway.

---

### Post by terotil on 2005-12-06
I have Asus A8V deluxe, 2 x sata drive and IDE DVD-drive.  I got "HDIO_SET_DMA failed: Operation not permitted" and solved it by commenting out ide-{cd,disk,generic} modules in /etc/modules and putting via82cxxx there, like this 

```

via82cxxx
#ide-cd
#ide-disk
#ide-generic

```

---

### Post by popeyeray on 2006-01-25
slippin', slippin', slippin' Slipping me away from you Ubuntu! Hal failed to initialize!!! What made MEPIS Linux successful? Unlike most of the major Linux distributions, MEPIS comes with many non-free, but highly useful applications, all pre-configured and ready to use, out of the box. These include the NVIDIA accelerated driver, Macromedia Flash plugin, Java, various multimedia codecs for playing popular audio and video files and other applications! That's all, i'll be back to Dapper Dave when he gets cleaned up.

---

