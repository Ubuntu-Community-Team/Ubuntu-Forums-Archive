---
title: "SATA/eSATA PCI Card --- How?"
date: 2008-05-31
forum: Hardware
---

### Post by yochaigal on 2008-05-31
I recently installed a Vantec esata adapter/pci card.
Specifically, it's Model UGT-ST300.
The chipset is Silicon Image ( Sil 3512).

It doesn't work out-of-the-box.  

My output of lsmod | grep sata :

sata_sil               12296  0 
libata                159344  5 pata_via,ahci,pata_acpi,ata_generic,sata_sil


My output of apt-file is :

yochai@yochai-desktop:~$ apt-file search sata_sil24.ko
linux-image-2.6.24-16-386: /lib/modules/2.6.24-16-386/kernel/drivers/ata/sata_sil24.ko
linux-image-2.6.24-16-generic: /lib/modules/2.6.24-16-generic/kernel/drivers/ata/sata_sil24.ko
linux-image-2.6.24-16-openvz: /lib/modules/2.6.24-16-openvz/kernel/drivers/ata/sata_sil24.ko
linux-image-2.6.24-16-rt: /lib/modules/2.6.24-16-rt/kernel/drivers/ata/sata_sil24.ko
linux-image-2.6.24-16-server: /lib/modules/2.6.24-16-server/kernel/drivers/ata/sata_sil24.ko
linux-image-2.6.24-16-xen: /lib/modules/2.6.24-16-xen/kernel/drivers/ata/sata_sil24.ko


Nothing to mount....

What do I do?

Thanks

---

### Post by yochaigal on 2008-06-01
Let me also say that I found this page:

[http://www.siliconimage.com/support/supportsearchresults.aspx?pid=32&cid=3&ctid=2](http://www.siliconimage.com/support/supportsearchresults.aspx?pid=32&cid=3&ctid=2)

It has FC4 module support but I assume this is already in the linux kernel...

and this

[http://ubuntuforums.org/showthread.php?t=499939](http://ubuntuforums.org/showthread.php?t=499939)


So I added irqpoll to the end of the boot options in grub; nothing happened.

---

### Post by yochaigal on 2008-06-01
Okay so I forgot to mention that I was trying to use the eSATA connector on the on the card----

After connecting a SATA drive via the card's internal sata port, the drive mounted fine.

I'm a bit confused; when I use my other eSATA adapter which connnects directly to my motherboard drives mount fine; only on this PCI card does the eSATA adapter not work.

Thanks

---

### Post by oobsniper2000 on 2008-06-05
Did you get this working?  I'm interesting in building a cheap pc w/old mobo and using this card (or one similar) to connect an external eSATA raid box.

---

### Post by yochaigal on 2008-06-05
I could not get the esata port working.
The internal port was not a problem, however.
It's odd: I was able to get an esata port working by attaching a regular esata adapter directly to a sata connector on the motherboard.  
It sucks, but you may be able to simply install a regular sata pci card, then attach to that an esata adapter bracket ($5 at your local computer store).
That should do it....

---

### Post by oobsniper2000 on 2008-06-05
Are you sure the esata port on that particular card is actually functional?  Did you try it in a mac/windows system?

---

### Post by yochaigal on 2008-06-05
yeah I'm sure.

I'm not saying you can't get it to work; only that it didn't work out of the box.

---

### Post by Clive McCarthy on 2008-06-12
I have the same SATA UGT-ST300 hardware on a brand-new installation of Ubuntu. Mine isn't recognized at all. I have a fat 500GB drive hooked up to the card but it's nowhere. The boot drive is a straightforward IDE disk.

I'm ultra-new and have NO idea what I'm letting myself in for.

BTW how do I disable the motherboard audio system and get everything to focus on the overkill fancy, fancy 24bit audio card I installed. I switch things over in the system>preferences>sound but the browser still dumps things to the old hardware.

How much RAM is needed to install Ubuntu? It seems 256MB is too little. The box thrashed like crazy during the installation from a CD until I gave it 512MB. Is this 'normal'?

---

### Post by yochaigal on 2008-06-12
For now, I don't think anyone has found a way to make this card work with eSATA. I would recommend simply getting an esata adapter --- a $7 cable with an adapter bracket found at most real computer stores (not best buy).  Plug it in to your sata port on your motherboard--- it will mount.  Unless of course, you don't have sata on your motherboard, then leave the card in, and connect it there.

To disable onboard audio, go into the BIOS.  You should be able to find an onboard audio switch there.

That, or blacklist it.  A howto:
[http://ubuntuforums.org/showthread.php?t=166624](http://ubuntuforums.org/showthread.php?t=166624)

About the RAM:
You shouldn't need more than 256MB, but if you're running GNOME (the default ubuntu desktop manager) than it might not be enough.  You could always switch to XFCE as your desktop manager, which has a much smaller memory stamp.

---

### Post by Clive McCarthy on 2008-06-12
Thanks for the advice. My problem isn't with the eSata port (which I haven't even tried) but with the internal, regular Sata port. I followed the lspci & lsmod instructions that you outlined in your earlier postings but no Sata driver shows up at all. You mention something about irqpoll in the boot options -- should I delve into this?

I tried the apt-file search sata_sil24.ko but got into some security barrier which was a dead end.

This is only my second Ubuntu installation so I'm just hacking around at the moment, however, I've been delightfully surprised by how electro-automatic things have been.

I picked up the UGT-ST300 at Fry's in Sunnyvale (I've shopped there since they first opened twenty years ago). The target machine is going to be used as a household music server.

---

### Post by yochaigal on 2008-06-12
What security barrier did you run into?  Always try with sudo (running as root).

Also, are you sure it isn't working? What is your output of :

sudo fdisk -l

You should see your regular partitions, then when you attach a drive there should be one more.
It should look like:
/dev/sdb1 or something.
When you're sure it's there, try:
sudo mkdir /media/music 
then sudo mount /dev/sdb1 /media/music

See if it appears on your desktop

A good tool: pysdm
sudo apt-get install pysdm

It's a nice gui for managing hard drives, mounts, etc.

The sata driver is built-in to the kernel, you just might need to do some tweaking.  

I bought mine from central computers, in downtown SF.
irqpoll actually made no difference.

---

### Post by yochaigal on 2008-06-12
One more thing:

If you are simply going to use it as a media server, you don't really need a desktop. You could just install ubuntu-server or to completely remove the gui run :

sudo apt-get remove ubuntu-desktop

This is all terminal, but there will be almost no memory footprint.

---

### Post by Clive McCarthy on 2008-06-12
Flipping the BIOS control to diable the on-board audio has fixed the sound issue -- the browser now connects to the add-in card's audio. I now have KCRW running loud & clear! Odd that the system's sound control preferences checked out but that apps don't exclusively funnel through the preference...

---

### Post by Clive McCarthy on 2008-06-12
Thanks again. No sign of the Sata drive, only the boot drive: sudo fdisk -l shows only my 'rehabilitated' PATA/IDE 34GB boot disk.

I wonder if I have a lower-level hardware problem such that Ubuntu never even sees the Sata card? The Sata card and the Audio card were both installed recently -- the rackmounted computer has a 90 degree PCI adapter so it's possible there is a mis-wired hardware slot problem.

Things actually run fine in 256MB it's just that when installing from a CD, when there was no defined HDD, the gui had to run in entirely in RAM with no swap space. The gui is only really needed to connect to web music and for the convenience of set-up.

---

### Post by VTT Alps on 2008-08-31
Yohaigal:   You wrote:   so I added irqpoll to the end of the boot options in grub; nothing happened.

Question: Where exactly in the /boot/grub/menu.lst file did you add irqpoll.  Did you add any options or other commands.   Just irqpoll at the very end of the file ???   

So far, I'm not having any success with the pci card and internal SATA drive

Please be very specific.  I'm new to Linux.  

Thanks

---

### Post by yochaigal on 2008-08-31
Here is an example:
Open /boot/grub/menu.lst
scroll down to the first entry like this:


title Ubuntu, kernel 2.6.20-15-generic
root (hd0,0)
kernel /boot/vmlinuz-2.6.20-15-generic root=UUID=fccafcc7-d7cc-4594-9459-a8f0db7b9f7f irqpoll ro quiet splash
initrd /boot/initrd.img-2.6.20-15-generic
quiet
savedefault

also, see here:
[http://sudan.ubuntuforums.com/showthread.php?t=504763](http://sudan.ubuntuforums.com/showthread.php?t=504763)
You can also do this from the grub boot up prompt by pressing 
"e" while it's still in the grub menu.  Here is a guide, hope it helps.  This page has some good information on both ways.

[http://grumpymole.blogspot.com/2007/05/ubuntu-how-to-edit-grub-boot-parameters.html](http://grumpymole.blogspot.com/2007/05/ubuntu-how-to-edit-grub-boot-parameters.html)

---

### Post by VTT Alps on 2008-08-31
Thanks for the extra information:  In the meantime I discovered the real problem was that my disk needed to be formatted.   It was:) brand new.  After I used mkfs, everything was fine.  In fact, I never added irqpoll to the menu.lst.

I have no idea if the esata port is working,  I'm just using the internal connector on the PCI card.   

Thanks again.

---

### Post by cometh4th on 2008-11-03
> **yochaigal said:**
> Okay so I forgot to mention that I was trying to use the eSATA connector on the on the card----

After connecting a SATA drive via the card's internal sata port, the drive mounted fine.

I'm a bit confused; when I use my other eSATA adapter which connnects directly to my motherboard drives mount fine; only on this PCI card does the eSATA adapter not work.

Thanks

I got the same problem with the eSATA connector on the UGT-ST300. I have an older HD enclosure with SATA connector so I too used a SATA to eSATA cable but no luck just as you. I put on my technician hat and discovered that the problem was due to the SATA side of the cable. When I bypassed the enclosure's SATA connector and plugged the cable directly into the SATA hard drive ... bingo, it worked. I'm using Hardy Heron and Hardy detects the hard drive without manually loading additional drivers. The SATA hard drive can be unplugged - after unmounting - and plugged in again without any problems i.e. hotswapped. It worked out of the box for me. :lolflag:

By-passing the HD enclosure is defeating the purpose of the enclosure, so I got the Vantec NST-360SU HD enclosure instead with eSATA to eSATA using the UGT-ST300. Again, no problems with this setup in Hardy.

Hope this helps. ;)

---

### Post by yochaigal on 2008-11-03
I used that exact enclosure, but the problem persisted. It may be a motherboard issue for me. No matter, the drive is internal now.

---

### Post by cometh4th on 2008-11-03
> **yochaigal said:**
> I used that exact enclosure, but the problem persisted. It may be a motherboard issue for me. No matter, the drive is internal now.

If it works as an internal drive connected to the internal SATA connection on the UGT-ST300 then this means the PCI card is functional and the issue should be on the eSATA side of the UGT-ST300 connection and the motherboard should not be an issue ... no ?

After you connected the external hard drive to eSATA port and powered on the computer does the UGT-ST300 identify itself after the bootup/initial screen and does it show your SATA drive on that screen ? If it does not then the problem should lie on the external hard drive side of the eSATA connection.

You said that when you used a bracket eSATA adaptor and connected it to the motherboard it work fine. This is what I did also when trouble-shooting the problem. It took me the better part of a day to figure out the problem: my HD enclosure had an incompatible SATA connection. :shock::sad: 

You may not recall exactly what you did a few months ago. If you still want to use an external SATA hard drive then you can give my suggestion a try: connect a cable directly into the SATA hard drive and on other end of cable connect it to the UGT-ST300's eSATA port and see if it is identified on boot up.

Hope this helps.

---

