---
title: "How to setup DKMS and Highpoint RocketRaid 276x"
date: 2012-10-11
forum: Hardware
---

### Post by NetGO on 2012-10-11
Hello, 

I think that I might help someone with this. I was playing with HighPoint RocketRaid 2760A card and finally created patch to work with DKMS. 

I've tested with 12.04. And it works.

If someone needs...

Downloads the attached. and unzip and untar it.

then

# apt-get install dkms
# cp -r rr276x-linux-src-v1.1/ /usr/src/rr276x-1.1
# mv /usr/src/rr276x-1.1/lib /usr/src/rr276x-1.1/real_lib
# ln -s /usr/src/rr276x-1.1/real_lib/ /usr/src/rr276x-1.1/lib
# dkms add -m rr276x -v 1.1
# uname -a

put your kernel name here.
# dkms build -k 3.2.0-31-generic -m rr276x -v 1.1 

After build success, 
# dkms install -k 3.2.0-31-generic -m rr276x -v 1.1

And then, you do

# mkinitramfs -o /boot/initrd.img-3.2.0-31-generic  initrd.img-3.2.0-31-generic

To remove this module

# dkms remove rr276x/1.1 --all

Hope this could help someone.

---

### Post by d3mia7 on 2012-12-07
Did you try the card with just the mvsas driver?  Since there is no XOR engine in the card there is not really any compelling reason to use the Highpoint driver if the card is recognized by mvsas properly.

I have one of these cards on order but I am planning on running it with mvsas and then OS RAID instead of whatever Highpoint is doing.  The Marvell chips on this card are definitely just plain HBAs - their driver is doing all the RAID stuff on the system CPU.

---

### Post by Flynsarmy on 2013-03-24
> **d3mia7 said:**
> there is not really any compelling reason to use the Highpoint driver if the card is recognized by mvsas properly.

The drivers let you power down the drives after x minutes. Do you know how to do that without them? As per [my stackoverflow post]("http://stackoverflow.com/questions/15595076/hdio-drive-cmdsetidle-failed-operation-not-permitted") hdparm -S is of no use.

---

### Post by d3mia7 on 2013-04-01
> **Flynsarmy said:**
> The drivers let you power down the drives after x minutes. Do you know how to do that without them? As per [my stackoverflow post]("http://stackoverflow.com/questions/15595076/hdio-drive-cmdsetidle-failed-operation-not-permitted") hdparm -S is of no use.

Strange, using mvsas I have no issue with hdparm -S using mvsas...  

```
$ sudo hdparm -S 180 /dev/disk/by-path/pci-0000:0a:00.0-sas-0x0600000000000000-lun-0

/dev/disk/by-path/pci-0000:0a:00.0-sas-0x0600000000000000-lun-0:
 setting standby to 180 (15 minutes)
$
```

```
$ sudo hdparm -S 0 /dev/disk/by-path/pci-0000:0a:00.0-sas-0x0600000000000000-lun-0

/dev/disk/by-path/pci-0000:0a:00.0-sas-0x0600000000000000-lun-0:
 setting standby to 0 (off)
$
```

Perhaps you are having some other issue?

---

### Post by Flynsarmy on 2013-04-02
> **d3mia7 said:**
> Strange, using mvsas I have no issue with hdparm -S using mvsas...  

Ahh, that was my problem. I had installed the drivers using [this method described on my blog]("http://www.flynsarmy.com/2012/11/installing-rocketraid-2760a-drivers-on-ubuntu-12-10/"). I did a reformat for unrelated reasons a couple of days ago, didn't reinstall the drivers (now just using the built in ones) and it's working like a charm!

---

