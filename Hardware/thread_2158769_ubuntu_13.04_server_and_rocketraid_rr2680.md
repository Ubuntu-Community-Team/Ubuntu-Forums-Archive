---
title: "ubuntu 13.04 server and rocketraid rr2680"
date: 2013-06-30
forum: Hardware
---

### Post by scottie4442 on 2013-06-30
I have looked all over the net for help on this and no luck so far.  I have a rocketraid rr2680 in my home server and it was working fine under 12.10.  When I upgraded to 13.04 the driver is no longer compatible, I knew this would happen.  I have tried to recompile the driver for 13.04 and no luck, the few webpages that I found are either not clear on their fixes or they are for other rocketraid cards.  Any ideas on this? I have 6 1TB hdd connected through this card and would like to not lose the info on them.  If necessary I will move to a rocketraid rr2720 card, but want to try to get this working first.

---

### Post by loganfre on 2013-08-05
I have just been through this same issue and finally have it resolved. I will try to outline all the steps required, but if I miss one I apologize. 

To start off all of the answers can be found by following the errors in the make.log, but for a novice (like myself) the log is quite confusing. I started by following [this guide]("http://pastebin.com/54B86c0q") which worked on previous versions of Ubuntu Server. The first thing that must be corrected is the location of version.h. This is found in this error:
```
grep: /lib/modules/3.8.0-25-generic/build/include/linux/version.h: No such file or directory
```
This issue is referred to [here]("http://serverfault.com/questions/515855/cant-build-rocketraid-rr268x-on-ubuntu-13-04"). To correct this change the following in /usr/src/rr2680-1.9/inc/linux_32mpa/Makefile.def
Change this:
```
MAJOR := $(shell expr `grep LINUX_VERSION_CODE $(KERNELDIR)/include/linux/version.h | cut -d\  -f3` / 65536 % 65536)
MINOR := $(shell expr `grep LINUX_VERSION_CODE $(KERNELDIR)/include/linux/version.h | cut -d\  -f3` / 256 % 256)
```
To this:
```
MAJOR := $(shell expr `grep LINUX_VERSION_CODE $(KERNELDIR)/include/generated/uapi/linux/version.h | cut -d\  -f3` / 65536 % 65536)
MINOR := $(shell expr `grep LINUX_VERSION_CODE $(KERNELDIR)/include/generated/uapi/linux/version.h | cut -d\  -f3` / 256 % 256)
```

Next we get these errors:
```
/var/lib/dkms/rr2680/1.9/build/product/rr2680/linux/.build/osm_linux.c: In function ‘scsicmd_buf_get’:
/var/lib/dkms/rr2680/1.9/build/product/rr2680/linux/.build/osm_linux.c:452:39: error: ‘KM_BIO_SRC_IRQ’ undeclared (first use in this function)
/var/lib/dkms/rr2680/1.9/build/product/rr2680/linux/.build/osm_linux.c:452:39: note: each undeclared identifier is reported only once for each function it appears in
/var/lib/dkms/rr2680/1.9/build/product/rr2680/linux/.build/osm_linux.c:452:2: error: too many arguments to function ‘kmap_atomic’
```
I found an indirect solution on a website that I have forgotten, that refereed to a different card. In this case the main issue is with 'kmap_atomic' which is a kernel function that has changed the number of parameters that it takes. It used to take two now it takes one, hence the error. The solution is remove the second parameter from all instances of this function. Luckily this seems to be unneeded as all occurrences have the constant 'HPT_KMAP_TYPE' as the second parameter. Here are the changes:

In /usr/src/rr2680-1.9/osm/linux/osm_linux.c change these lines:
```
#if LINUX_VERSION_CODE >= KERNEL_VERSION(2,6,23)
	struct scatterlist *sg;
	sg = scsi_sglist(cmd);
	kunmap_atomic((char *)buf - sg->offset, HPT_KMAP_TYPE);
#else 

	if (cmd->use_sg) {
#if LINUX_VERSION_CODE >= KERNEL_VERSION(2,5,0)
		kunmap_atomic((char *)buf - ((struct scatterlist *)cmd->request_buffer)->offset, HPT_KMAP_TYPE);
#elif LINUX_VERSION_CODE >= KERNEL_VERSION(2,4,18)
		struct scatterlist *sg = (struct scatterlist *) cmd->request_buffer;
		if (sg->page)
			kunmap_atomic((char *)buf - sg->offset, HPT_KMAP_TYPE);

```
To this:
```
#if LINUX_VERSION_CODE >= KERNEL_VERSION(2,6,23)
	struct scatterlist *sg;
	sg = scsi_sglist(cmd);
	kunmap_atomic((char *)buf - sg->offset);
#else 

	if (cmd->use_sg) {
#if LINUX_VERSION_CODE >= KERNEL_VERSION(2,5,0)
		kunmap_atomic((char *)buf - ((struct scatterlist *)cmd->request_buffer)->offset);
#elif LINUX_VERSION_CODE >= KERNEL_VERSION(2,4,18)
		struct scatterlist *sg = (struct scatterlist *) cmd->request_buffer;
		if (sg->page)
			kunmap_atomic((char *)buf - sg->offset);
```
Then in /usr/src/rr2680-1.9/osm/linux/os_linux.c
```
		kunmap_atomic(ptr, HPT_KMAP_TYPE);
```
To this:
```
		kunmap_atomic(ptr);
```

Finally just for good measure I removed this line from /usr/src/rr2680-1.9/osm/linux/osm_linux.h
```
#define HPT_KMAP_TYPE KM_BIO_SRC_IRQ
```

After that just build and install and you are all set. Like I said at the beginning I may have missed a step, but I believe this is all that must be changed. Once you have it all sorted out, make sure you keep a copy of all the files in /usr/src/rr2680-1.9 so you won't have to go through this the next time you upgrade. ;)

---

### Post by samhamilton on 2013-08-07
Hey loganfre,

I followed your steps but I still get an error when building the module, do you have any ideas?

```
dkms build rr2680/1.9 -k 3.8.0-27-generic
```

```
DKMS make.log for rr2680-1.9 for kernel 3.8.0-27-generic (x86_64)Thu Aug  8 11:06:01 CST 2013
make: Entering directory `/var/lib/dkms/rr2680/1.9/build/product/rr2680/linux'
make[1]: Entering directory `/usr/src/linux-headers-3.8.0-27-generic'
  CC [M]  /var/lib/dkms/rr2680/1.9/build/product/rr2680/linux/.build/os_linux.o
  CC [M]  /var/lib/dkms/rr2680/1.9/build/product/rr2680/linux/.build/osm_linux.o
/var/lib/dkms/rr2680/1.9/build/product/rr2680/linux/.build/osm_linux.c: In function ‘scsicmd_buf_get’:
/var/lib/dkms/rr2680/1.9/build/product/rr2680/linux/.build/osm_linux.c:452:39: error: ‘HPT_KMAP_TYPE’ undeclared (first use in this function)
/var/lib/dkms/rr2680/1.9/build/product/rr2680/linux/.build/osm_linux.c:452:39: note: each undeclared identifier is reported only once for each function it appears in
/var/lib/dkms/rr2680/1.9/build/product/rr2680/linux/.build/osm_linux.c:452:2: error: too many arguments to function ‘kmap_atomic’
In file included from include/linux/pagemap.h:10:0,
                 from include/linux/blkdev.h:13,
                 from /var/lib/dkms/rr2680/1.9/build/osm/linux/osm_linux.h:61,
                 from /var/lib/dkms/rr2680/1.9/build/product/rr2680/linux/.build/osm_linux.c:6:
include/linux/highmem.h:66:21: note: declared here
make[2]: *** [/var/lib/dkms/rr2680/1.9/build/product/rr2680/linux/.build/osm_linux.o] Error 1
make[1]: *** [_module_/var/lib/dkms/rr2680/1.9/build/product/rr2680/linux/.build] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-3.8.0-27-generic'
make: *** [rr2680.ko] Error 2
make: Leaving directory `/var/lib/dkms/rr2680/1.9/build/product/rr2680/linux'
```

Thanks
Sam

---

### Post by loganfre on 2013-08-08
Sam,

Which files did you modify? The files at /var/lib/dkms (as listed in the error) are overwritten each time you build. All the files you are changing should be at  /usr/src/.

Logan

---

### Post by samhamilton on 2013-08-08
Hi Logan,

I thought it would be easier to wack up the changes on github so you can see better - [https://github.com/samhamilton/rr268x-linux-src-v1-1.9/commit/7c0e984d42b0c9a7955d26cffd0cc6efe36c90d5](https://github.com/samhamilton/rr268x-linux-src-v1-1.9/commit/7c0e984d42b0c9a7955d26cffd0cc6efe36c90d5)

The files are saved into /usr/src/rr2680-1.9 and it just occured to me that you might be using the 1.8 version of the driver and I am trying to change the 1.9 version, I upgraded a while back as the 1.8 was a bit buggy for me.

Thanks
Sam

---

### Post by loganfre on 2013-08-08
I commented at github. Based on the error (and I confirmed by reviewing the file) there is another occurrence of  'kmap_atomic' in line 452. It looks like this:

```
	*pbuf = kmap_atomic(HPT_SG_PAGE(sg), HPT_KMAP_TYPE) + sg->offset;

```


Logan

---

### Post by samhamilton on 2013-08-08
Hi Logan,

Yep that did it, I can now build the module. I only have some errors about cleaning up the build area, not sure if thats anything to worry about.

Here is the final list of [changes]("https://github.com/samhamilton/rr268x-linux-src-v1-1.9/compare/6f4aee6181998d8f9812d8ac63be134b4daf2e14...master")

```
root@nas:/usr/src/rr2680-1.9# dkms build rr2680/1.9 -k 3.8.0-27-generic

Kernel preparation unnecessary for this kernel.  Skipping...


Building module:
cleaning build area....(bad exit status: 2)
make KERNELRELEASE=3.8.0-27-generic -C product/rr2680/linux/ KERNELDIR=/lib/modules/3.8.0-27-generic/build......
cleaning build area....(bad exit status: 2)


DKMS: build completed.
root@nas:/usr/src/rr2680-1.9# dkms install rr2680/1.9 -k 3.8.0-27-generic


rr2680:
Running module version sanity check.
 - Original module
   - No original module exists within this kernel
 - Installation
   - Installing to /lib/modules/3.8.0-27-generic/updates/dkms/


depmod.......


Backing up initrd.img-3.8.0-27-generic to /boot/initrd.img-3.8.0-27-generic.old-dkms
Making new initrd.img-3.8.0-27-generic
(If next boot fails, revert to initrd.img-3.8.0-27-generic.old-dkms image)
update-initramfs.........................


DKMS: install completed.
```

---

### Post by loganfre on 2013-08-09
Looks good Sam. I am sure rocketraid owners around the globe appreciate you putting all the changes into one easy to find place!

Logan

---

### Post by CharlesA on 2013-08-09
I think all the rocketraid drivers have this problem with kernel higher than 3.0.

Glad you got it sorted out.

---

### Post by general-bartoon on 2013-08-17
> **loganfre said:**
> Looks good Sam. I am sure rocketraid owners around the globe appreciate you putting all the changes into one easy to find place!

Logan

As a RR2680 user, who gave up 2 weeks ago trying to do this, I do appreciate this.... Now to get it working for an amateur like me :)

Just documenting some steps that probably seem basic to everyone except me...  If i got it wrong, or didn't write it out neatly, or was confusing.. please correct me :)

```
sudo apt-get install git
sudo apt-get install dkms
git clone [https://github.com/samhamilton/rr268x-linux-src-v1-1.9.git](https://github.com/samhamilton/rr268x-linux-src-v1-1.9.git)
cd rr268x-linux-src-v1-1.9/
sudo cp -R . /usr/src/rr2680-1.9
sudo dkms add -m rr2680 -v 1.9
sudo dkms build -m rr2680 -v 1.9
sudo dkms install -m rr2680 -v 1.9

```

It appears i did get it wrong because i am not seeing the disks.  But i did not see any errors when i did the steps above.   Any suggestions?

---

### Post by CharlesA on 2013-08-18
That looks right. I don't really know why it isn't working, but I'm guessing it has to do with the driver from highpoint, which really sucks.

---

### Post by general-bartoon on 2013-08-19
> **CharlesA said:**
> That looks right. I don't really know why it isn't working, but I'm guessing it has to do with the driver from highpoint, which really sucks.

Good news... after rebooting for what i throught was the third time, all my drives showed up.

Excelent stuff :)

---

### Post by CharlesA on 2013-08-19
Glad you got it sorted out. What a pain!

---

### Post by ehlers320 on 2013-08-24
This is going to break again with kernel 3.10 and up so dont upgrade. They changed the proc_info variable, im not sure how to fix the code so it compiles.

---

### Post by scotjam1981 on 2013-08-28
Slightly off-topic, but I was very pleasantly surprised to find that the latest versions of the source code and web management tool seem to "just work" on Ubuntu 12.04.2 LTS (GNU/Linux 3.5.0-23-generic x86_64), which is wonderful news as far as I'm concerned. Steps are below, but all are trivial.

```

!#/bin/bash
wget http://www.highpoint-tech.com/BIOS_Driver/HRM/Linux/WebGUI-Linux-v2.1.5-130409.tgz
wget http://www.highpoint-tech.com/BIOS_Driver/rr26xx/RR268x/Linux/v1.8.12.0823/RR268x-Linux-Src-v1.9-120817-1639.tar.gz
tar -zxf RR268x-Linux-Src-v1.9-120817-1639.tar.gz
cd rr268x-linux-src-v1.9/product/rr2680/linux/
make
sudo make install
cd ../../../..
tar -zxf WebGUI-Linux-v2.1.5-130409.tgz
sudo apt-get install alien
sudo alien --script hptsvr-https-2.1.5-13.0409.x86_64.rpm #obviously use the i386 version if you're on 32 bit
sudo dpkg -r hptsvr-https
sudo dpkg -i hptsvr-https_2.1.5-14.0409_amd64.deb
cd ~/Desktop/
sudo chown [username] hptwebraid.desktop
sudo chmod a+x hptwebraid.desktop



```

Then reboot
Browse to [http://localhost:7402]("https://localhost:7402") 
user: RAID
pass: hpt

bingo!

It seems like highpoint are one major version number behind (but at least it's only one version number behind...)

---

### Post by misu3108 on 2013-11-10
For people who have rr2680 I installed the drivers for Ubuntu 12.04 after I cleared the complie error as [SIZE=4]"[**[COLOR=#000000]loganfre[/COLOR]**]("http://ubuntuforums.org/member.php?u=440559")"[/SIZE] says above! Make sure you remove [SIZE=4][COLOR=#ff0000]_**[FONT=century gothic]all[/FONT]**_[/COLOR][/SIZE] the insatnces of **HPT_KMAP_TYPE** from **usr/src/rr2680-1.9/osm/linux/osm_linux.c** then try to build and it will work.

 For the WebGui follow this [http://ubuntuforums.org/showthread.php?t=1737847](http://ubuntuforums.org/showthread.php?t=1737847) after you have the drivers installed.

I hope this helps those who spent a lot of time trying to install the drivers. It took me some time to get it to work.

---

### Post by bvanaerde on 2013-11-13
Please check [this thread]("http://ubuntuforums.org/showthread.php?t=1899544&page=2&p=12829370#post12829370") for a patch for a lot of rocketraid drivers, provided by camper2.

---

