---
title: "Intel DG965RY Core 2 duo"
date: 2006-12-07
forum: Hardware &amp; Laptops
---

### Post by jlong27 on 2006-12-07
I got the 64Bit version of Ubuntu 6.1 server to install by putting a PCI IDE controller in and connecting the cdrom. I installed it to an 80GB sata II drive connected to the on board sata controller. Now when the computer boots it just stops after:

Decompressing Linux...done.
Booting the kernel.
[  37.638973] ACPI: Getting cpuindex for acpiid 0x3
[  37.6...
[  38.4...
[  38.5...

It was tough to install. I couldn't partition the drive manually or I would get an error during the install process.

Any ideas? I was able to install a copy of SLES 10 with no problem. I just don't like it that much. Though I only messed with it for half a day.

---

### Post by rpkehoe on 2006-12-07
Were you able to successfully boot into the live cd?  If you were, then you probably had some sort of corruption on your install (you have had a bad burn on the install disk).  You may also want to consider using the 32 bit version unless you really need the 64 bit, and go for the desktop version and installing the servers as the server version is command line only.

---

### Post by jlong27 on 2006-12-07
I haven't tried the live cd. I tried to install 6.06.1 64 & 32bit, 6.10 64bit. I guess I can try the live cd and the 32 bit version of 6.10 

Right now I am trying OpenSUSE 10.2 First attempt wouldn't boot after it finished the first half of the install.

](*,)

---

### Post by rpkehoe on 2006-12-07
Also with the problems you are having, you may want to opt for 6.06 instead of 6.10.  It is supposed to be more stable, but I haven't had any problems at all with Edgy.

---

### Post by jlong27 on 2006-12-08
Well open suse 10.2 doesn't work. It seams like there is a driver issue with ubuntu and this open suse.

The only thing I have gotten to work is sles 10.1 64bit. Funny thing is it is the only one I have tried that costs money:lol:  It uses gnome but the layout isn't like the one in ubuntu 6.06. I guess I will learn to use sles and wait for an ubuntu to support the dg965ry board.

---

### Post by jlong27 on 2006-12-08
Well I installed SLES 10 and got free VMware server installed. Guess I will check back later to see if Ubuntu works with my mobo.

Thanks.

---

### Post by egars on 2007-01-10
Hi,

Problems I'm experiencing are quite like the one described above.

I'm using a freshly bought Dell Dimension 9200 which contains an Intel E6400 2,13 GHz, 2Mb Cache 1066MHz FSB Intel Core 2 Duo processor.

Now, both Ubuntu Server version 6.10 AMD64 and i386 yield the same errors, 
something like:

[42949376.760000] ACPI: Getting cpuindex for acpiid 0x3
[42949376.760000] ACPI: Getting cpuindex for acpiid 0x4

Then the system hangs.

Furthermore: installation of Lilo or Grub combined with XFS fails miserably (Lilo is recommended in combination with XFS, but still fails). This was only tested using the AMD64 Ubuntu Server 6.10 version.

Using EXT3 (both the AMD64 and i386 version) results in the error messages about ACPI.

After using Linux for more than 10 years now, I'm stuck with Linux, for the first time!

My configuration:
boot.ini in the installed windows partition (which is what you get when you buy Dell) contains a line:
c:\linux.bin="Linux", which is a file that consists of the first 512 bytes copied from /dev/sde8 (which is the /boot partition of the Ubuntu installation), that was created with this statement:
dd if=/dev/sde8 of=/tmp/pen/linux.bin
and then copied from the USB stick (mounted on /tmp/pen) on the windows c: partition.

After windows boots, and I choose Linux, Grub correctly shows different kernel options. So it seems that using the linux.bin file to boot to the linux partition works fine.

Do I need special kernel parameters?????

Anyone?

Kind regards,

Jerrie

---

### Post by egars on 2007-01-10
Replying to myself.... Must be going mad.

To solve the issue above:
- should I fall back to Ubuntu Server 6.06 LTS?
- picking an older version of Ubuntu Server: is Intel EM64T compatible with AMD64????

---

### Post by brent.stephens on 2007-01-14
I have this board...it took a lot to get it going.  You need to pass the "all-generic-ide irqpoll pci=nommconf" options to most boot CDs, as well as any kernels you use.  The PATA controller has limited support in only the very latest kernel sources, so you'll have to deal with that as well.

---

### Post by Prof.Arronax on 2007-03-14
> **brent.stephens said:**
> I have this board...it took a lot to get it going.  You need to pass the "all-generic-ide irqpoll pci=nommconf" options to most boot CDs, as well as any kernels you use.  The PATA controller has limited support in only the very latest kernel sources, so you'll have to deal with that as well.

When I installed 6.10 (32bit) on an old clunker 550MHz machine with 256MB of ram, it went so smoothly I couldn't believe it...  THEN I tried installing it on my freshly built machine with the DG965RY board (with the Core2Duo 6600 processor)... **NOT**!  I tried several of the various solutions posted and none worked.  By some freak occurrence, one try with the 64bit version finally decided to load without the initial "can't access tty" junk.  (*What _does_ that mean?!)*

Though I'm using that machine right now, I'm a bit disappointed to find that I'm limited somewhat in which programs will work with this build.  It would appear that *much* continuing development must be done before this is ready for "prime time".  

Regrettably, contrary to the Ubuntu "(it should "Just Work", TM)" it simply does not - - unless you happen to be a Linux Whiz-Kid (which I most certainly am *not*, by any stretch of the imagination.  I am an absolute noob in the Linux environment, trying to find an MS alternative.)

Again, any views or suggestions (like for getting the 32bit version to work) will be much appreciated!

---

