---
title: "[SOLVED] Atheros L2 - Installing Driver"
date: 2008-02-14
forum: Hardware &amp; Laptops
---

### Post by ivaylo_ch on 2008-02-14
I found a driver for my LAN card [here]("http://people.redhat.com/csnook/atl2/"), but I'm totally new to Linux and I don't know what to do with all those files I downloaded :lolflag:
P.S.: I installed Ubuntu with Wubi, maybe this might be happening because of this? :confused:

---

### Post by jan quark on 2008-02-14
well I do not recommend wubi 

it might be tempting in the beginning but it is only a virtaullization and will never be as stable as a install to the drive



to the drivers

navigate to the folder in terminal

so if you extracted the tar.bz folder to the Desktop type
```

cd Desktop
```
then

```
ls
```

this will list all folders and subfolders  in the current directory 
navigate to your drivers folder
```

cd atl...... whatever
```

and now type these commands one after the other


```
make
```

```
sudo make install
```

---

### Post by ivaylo_ch on 2008-02-14
I just used Wubi, because my CD drive is getting repaired, and I can't make a CD. Ok I'll try that and see if it works. Thanks.

---

### Post by ivaylo_ch on 2008-02-14
I did that a couple of times but after i type "sudo make install", it asks me for a password (my account password, right?) and I cant type in anything. Is this a bug or am I doing something wrong? :(

---

### Post by mrsteveman1 on 2008-02-14
Password prompts don't show what you are typing for security reasons, so just type the password and hit enter.

---

### Post by ivaylo_ch on 2008-02-15
> **mrsteveman1 said:**
> Password prompts don't show what you are typing for security reasons, so just type the password and hit enter.

I type in my password, but it gets some kind of error:
make: *** No rule to make target 'install'. Stop.

---

### Post by ivaylo_ch on 2008-02-15
Maybe if I install Ubuntu from a CD I wont have that problem?

---

### Post by ivaylo_ch on 2008-02-15
They told me to do this on some other forums:

Run Terminal
cd Desktop
tar jfx atl2-2.0.4.tar.bz2
cd atl2-2.0.4
make
sudo cp ./atl2.ko /lib/modules/`uname -r`/kernel/drivers/net
sudo modprobe atl2

And it tells me something like (I did not remember the exact message): FATAL: Module atl2 cannot be found.

---

### Post by ivaylo_ch on 2008-02-16
Can anyone help me? I'm getting desperate about this and if I can't have internet, I won't get a chance to see what really is Linux :(

---

### Post by oldsoundguy on 2008-02-16
my Atheros based chipset D-Link wireless cards installed in Gutsy right out of the box.  All I had to do was go to:

system>
administration>
network settings>
highlight wireless connections (make sure it is checked)>
properties>
fill in the blanks (select your network and password .. enable automatic configuration)>
click OK> 
close>

your network card should be working

---

### Post by mrsteveman1 on 2008-02-16
After you add a driver like that to the kernel you should run 

```
sudo depmod -a 
```

If that kernel module has been compiled and is in the directory you can insert it manually to make sure it works with:

```
sudo insmod atl2.ko
```

BTW, Wubi isn't virtualization, its an installer that lets you run linux from a disk image instead of a partition. It's still 100% native, just easier to install since no partitioning is required and no writing over the MBR. The ubuntu liveUSB works in a similar way, its a disk image sitting on a vfat partition etc. Wubi puts an uncompressed disk image on top of an NTFS partition and boots from it using the windows bootloader.

---

### Post by ivaylo_ch on 2008-02-17
Well I got it working, thanks to some fellas in another forum, but now my Windows drivers bugged and now I can only access the net from ubuntu, I hope my CD drive gets repaired soon so I can use my driver CD to fix it. Thread solved. Here's how I did it:
```

tar jfx atl2-2.0.4.tar.bz
cd atl2-2.0.4
make
sudo cp ./atl2.ko /lib/modules/`uname -r`/kernel/drivers/net
sudo depmod -a
sudo modprobe atl2
dmesg
ifconfig -a
```
And it tells me "Connected to the internet":):):):):):):):)

---

