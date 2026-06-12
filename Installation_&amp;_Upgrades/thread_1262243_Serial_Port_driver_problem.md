---
title: "Serial Port driver problem"
date: 2009-09-09
forum: Installation &amp; Upgrades
---

### Post by MickSulley on 2009-09-09
Hi,
I have just bought a serial port card for my desktop.  The CD supplied has Linux drivers, but when I try to install I get an error - 

mick@mick-desktop:~/temp/Serial Driver$ sudo make
rm -f *.mod.c *.o *.ko .*.cmd *.symvers
make -C /lib/modules/2.6.28-15-generic/build/  SUBDIRS= modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.28-15-generic'
  CHK     include/linux/version.h
  CHK     include/linux/utsrelease.h
  SYMLINK include/asm -> include/asm-x86
make[2]: *** No rule to make target `kernel/bounds.c', needed by `kernel/bounds.s'. Stop.
make[1]: *** [prepare0] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.28-15-generic'
make: *** [default] Error 2
mick@mick-desktop:~/temp/Serial Driver$ 

I have Googled it, most posts say that it needs the full kernel source installed, which I have done (I think!).  I have run - 

sudo apt-get install linux-headers-`uname -r`
sudo apt-get install linux-source
sudo apt-get install build-essential

I am running Ubuntu 9.04 64 bit

The makefile supplied is - 


KDIR:=/lib/modules/$(shell  uname -r)/build/ 

obj-m +=mcs9865.o
obj-m +=mcs9865-isa.o

default:
	$(RM) *.mod.c *.o *.ko .*.cmd *.symvers
	$(MAKE) -C $(KDIR) SUBDIRS=$(PWD) modules

install:
	cp mcs9865.ko mcs9865-isa.ko /lib/modules/$(shell uname -r)/kernel/drivers/serial/
	depmod -A
	chmod +x mcs9865
	cp mcs9865 /etc/init.d/
	ln -s /etc/init.d/mcs9865 /etc/rc.d/rc3.d/Smcs9865 || true  	
	ln -s /etc/init.d/mcs9865 /etc/rc.d/rc5.d/Smcs9865 || true
	modprobe mcs9865
	modprobe mcs9865-isa	

uninstall:
	modprobe -r mcs9865
	modprobe -r mcs9865-isa
	rm /lib/modules/$(shell uname -r)/kernel/drivers/serial/mcs9865*
	depmod -A
	rm -f /etc/init.d/mcs9865
	rm -f /etc/rc.d/rc3.d/Smcs9865
	rm -f /etc/rc.d/rc5.d/Smcs9865

clean:
	$(RM) *.mod.c *.o *.ko .*.cmd *.symvers

---

### Post by MickSulley on 2009-09-16
Can anyone give me any idea what to do here?

Thanks

Mick

---

### Post by kurt.kochendarfer on 2009-12-07
I had same issue with MCS9865 driver compile under Koala.  Try modifying the Makefile by adding this line:

```
PWD:= $(shell pwd)
```Under the line that says:

```
KDIR:=/lib/modules/$(shell  uname -r)/build/
```Compiled fine for me after that.

---

### Post by MickSulley on 2009-12-07
Thanks for the reply Kurt.

I should have updated this before.  I contacted Moschip and to my surprise they supplied updated drivers which compile fine.  I don't know if they are downloadable from their site, but if anyone has the same problem I can mail the drivers if you let me know.

Cheers

Mick

---

### Post by alternative on 2010-02-16
Hi.please send me this driver or binary you compile to radikas7ETAyahooDOTcom.thank you.

---

### Post by MickSulley on 2010-02-16
The driver is now available on the MosChip site [www.moschip.com](www.moschip.com) I think you have to register but it is free.

I have mailed the driver to you at what I think is your email address, let me know if you need any further help.

Mick

---

### Post by ps2chiper on 2010-03-11
I used the driver from the moschip website. They compiled and installed fine but after a reboot I get this message.

[   22.240996] serial-isa 0000:02:05.2: PCI INT C -> GSI 22 (level, low) -> IRQ 22
[   22.241166] 0000:02:05.2: ttyS1 at I/O 0xdd00 (irq = 22) is a 16550A
[   22.241321] 0000:02:05.2: ttyS2 at I/O 0xdc00 (irq = 22) is a 16550A
[   22.241462] 0000:02:05.2: ttyS3 at I/O 0xdb00 (irq = 22) is a 16550A
[   22.241487] Couldn't register serial port 0000:02:05.2: -28
[   22.241494] serial-isa 0000:02:05.2: PCI INT C disabled
[   22.241511] serial-isa: probe of 0000:02:05.2 failed with error -28
[   22.277978] ppdev: user-space parallel port driver

I thought the drivers were supposed to make them become ttyD0?
Can anyone help me out?

---

### Post by MickSulley on 2010-03-11
The ports should be /dev/ttyD0 and /dev/ttyD1
When installing I had run 'make' and 'make install' but I had to run one with sudo and one without, sorry can't remember which way around.

Cheers
Mick

---

### Post by ps2chiper on 2010-03-11
I ran make and sudo make install and it installed the modules to /lib/modules/mylinuxkernel/kernel/serial. but I dont get ttyd0 after i rebooted. I fiddled with it and still no change. I am using karmic with the 6 port version of the mcs9865 card. I will try installing full linux kernel source, but could you tell me where you read that from?

---

### Post by ps2chiper on 2010-03-11
Here is what I did to install the modules

jason@jason-desktop:~/Downloads/MCS9865_Linux/MCS9865_V1.0.0.6$ make
rm -f *.mod.c *.o *.ko .*.cmd *.symvers
make -C /lib/modules/2.6.31-20-generic/build/  SUBDIRS=/home/jason/Downloads/MCS9865_Linux/MCS9865_V1.0.0.6 modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.31-20-generic'
  CC [M]  /home/jason/Downloads/MCS9865_Linux/MCS9865_V1.0.0.6/mcs9865.o
/home/jason/Downloads/MCS9865_Linux/MCS9865_V1.0.0.6/mcs9865.c: In function &#8216;receive_chars&#8217;:
/home/jason/Downloads/MCS9865_Linux/MCS9865_V1.0.0.6/mcs9865.c:633: warning: comparison of distinct pointer types lacks a cast
/home/jason/Downloads/MCS9865_Linux/MCS9865_V1.0.0.6/mcs9865.c:707: warning: comparison of distinct pointer types lacks a cast
/home/jason/Downloads/MCS9865_Linux/MCS9865_V1.0.0.6/mcs9865.c: At top level:
/home/jason/Downloads/MCS9865_Linux/MCS9865_V1.0.0.6/mcs9865.c:758: warning: &#8216;transmit_chars_dma_stop_done&#8217; defined but not used
  CC [M]  /home/jason/Downloads/MCS9865_Linux/MCS9865_V1.0.0.6/mcs9865-isa.o
  Building modules, stage 2.
  MODPOST 2 modules
  CC      /home/jason/Downloads/MCS9865_Linux/MCS9865_V1.0.0.6/mcs9865-isa.mod.o
  LD [M]  /home/jason/Downloads/MCS9865_Linux/MCS9865_V1.0.0.6/mcs9865-isa.ko
  CC      /home/jason/Downloads/MCS9865_Linux/MCS9865_V1.0.0.6/mcs9865.mod.o
  LD [M]  /home/jason/Downloads/MCS9865_Linux/MCS9865_V1.0.0.6/mcs9865.ko
make[1]: Leaving directory `/usr/src/linux-headers-2.6.31-20-generic'
jason@jason-desktop:~/Downloads/MCS9865_Linux/MCS9865_V1.0.0.6$ sudo make install
cp mcs9865.ko mcs9865-isa.ko /lib/modules/2.6.31-20-generic/kernel/drivers/serial/
depmod -A
chmod +x mcs9865
cp mcs9865 /etc/init.d/
ln -s /etc/init.d/mcs9865 /etc/rc.d/rc3.d/Smcs9865 || true  	
ln: creating symbolic link `/etc/rc.d/rc3.d/Smcs9865': No such file or directory
ln -s /etc/init.d/mcs9865 /etc/rc.d/rc5.d/Smcs9865 || true
ln: creating symbolic link `/etc/rc.d/rc5.d/Smcs9865': No such file or directory
modprobe mcs9865
WARNING: All config files need .conf: /etc/modprobe.d/ndiswrapper, it will be ignored in a future release.
modprobe mcs9865-isa	
WARNING: All config files need .conf: /etc/modprobe.d/ndiswrapper, it 
will be ignored in a future release.
jason@jason-desktop:~/Downloads/MCS9865_Linux/MCS9865_V1.0.0.6$

Here is some more info from when I enable it 
[  153.505635] UDP: bad checksum. From 8.8.8.8:53 to 192.168.1.132:59500 ulen 57
[  413.884565] mcs9865-serial 0000:02:05.0: PCI INT A -> GSI 20 (level, low) -> IRQ 20
[  413.884592] 0000:02:05.0: ttyD0 at I/O 0xdf00 (irq = 20) is a mcs9865-serial
[  413.884722] mcs9865-serial 0000:02:05.1: PCI INT B -> GSI 21 (level, low) -> IRQ 21
[  413.884737] 0000:02:05.1: ttyD1 at I/O 0xde00 (irq = 21) is a mcs9865-serial
[  413.925272] serial-isa 0000:02:05.2: PCI INT C -> GSI 22 (level, low) -> IRQ 22
[  413.925447] 0000:02:05.2: ttyS1 at I/O 0xdd00 (irq = 22) is a 16550A
[  413.925609] 0000:02:05.2: ttyS2 at I/O 0xdc00 (irq = 22) is a 16550A
[  413.925754] 0000:02:05.2: ttyS3 at I/O 0xdb00 (irq = 22) is a 16550A
[  413.925781] Couldn't register serial port 0000:02:05.2: -28
[  413.925788] serial-isa 0000:02:05.2: PCI INT C disabled
[  413.925813] serial-isa: probe of 0000:02:05.2 failed with error -28

I think the drivers are using ttys* instead of ttyd*. and the kernel doesnt allow more then 4 uarts. How do I enable more uarts on karmic?

---

### Post by MickSulley on 2010-03-11
Sorry I don't know.  I suggest you contact MosChip [http://www.moschip.com/](http://www.moschip.com/) they were quite helpful when I was stuck
Best of Luck
Mick

---

### Post by ESimard on 2010-03-24
Hi, I am having the same problems attempting to install the two port serial card.  What were the drivers version#?  I downloaded what they had on their web site, but it fails and they have not responded to my queries. My woes are detailed in "[ubuntu] Cant install serial ports with MCS9865 instructions"

Thanks in advance for any light you may be able to shed.
_Ernie

---

### Post by MickSulley on 2010-03-24
Try the attached drivers.  I have also uploaded the notes that I made at the time.

I have since bought a new serial card, which just works out of the box, much easier and not expensive!

Cheers

Mick

---

### Post by ESimard on 2010-03-24
Thanks.  What was the maker of the new card?  That sound even better.

_Ernie

---

### Post by MickSulley on 2010-03-26
Hi,

Here is a link to another card I bought, again 2 serial ports, this one just worked on Karmic

[http://linitx.com/viewproduct.php?prodid=10438](http://linitx.com/viewproduct.php?prodid=10438)

An easier solution than installing drivers and still not expensive.

Mick

---

### Post by pkontopoulos on 2011-03-14
Please check also this scenario-solution
[Moschip-9865-serial-ports-setup]("http://www.pkontopoulos.com/technical-articles/moschip-9865-serial-ports-setup")
which was done recently and can be of great help.

It is too long to post here.

---

