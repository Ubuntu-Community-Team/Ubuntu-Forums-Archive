---
title: "Newbie Help requested: DMA Mode problems"
date: 2005-09-28
forum: Hardware &amp; Laptops
---

### Post by fred19242003 on 2005-09-28
I have been attempting to get my DVD player to play.  I have tried to put the player in DMA mode however, I get the following answer;

/dev/hdc:
 setting using_dma to 1 (on)
 HDIO_SET_DMA failed: Operation not permitted
 using_dma    =  0 (off)

If this helps, I have a pioneer DVD player in hda and a Sony DVD+/-R in hdc.  Neither of them are able to be turned into DMA mode.
My hardware is a Gigabyte 8ipe1000pro2 motherboard and a 160GB SATA Hard Drive.

Thanks in advance

Fred

---

### Post by rlange on 2005-10-05
see this page

[https://wiki.ubuntu.com/DMA?action=print](https://wiki.ubuntu.com/DMA?action=print)

---

### Post by Sabot on 2005-10-19
I was having the same problem with my Pioneer DVR-109 in Hoary 5.04.  After I followed the link rlange gave.  This was my solution for my computer.

I opened /etc/modules.

sudo gedit /etc/modules

I added via82cxxx above ide-cd.  I saved the file.  I then rebooted my machine, and I could then turn dma on using the below command:

sudo hdparm -d1 /dev/cdrom

My Hardware set up is:

AMD 64 3200+
MSI K8T Neo FSR  Via K8T800 Chipset Motherboard

Another interesting thing I noticed is in the device manager the DVD drive moved from its own heading to now being under the VT82C586A device.

---

