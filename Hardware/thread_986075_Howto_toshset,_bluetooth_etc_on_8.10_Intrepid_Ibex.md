---
title: "Howto: toshset, bluetooth etc on 8.10 Intrepid Ibex"
date: 2008-11-18
forum: Hardware
---

### Post by adpsimpson on 2008-11-18
In certain Toshiba laptops the bluetooth will only work using the toshset utitlity. In previous versions of ubuntu, this worked flawlessly. Expect it be be fixed soon in 8.10, but in the mean time it's worth having this here.

There are 2 issues to solve.
1) 8.10 kernels are compiled without the toshiba_acpi module, which is required by toshset.
2) Versions of toshiba_acpi in recent kernels do not work with toshset

The solution is to patch and compile the toshiba_acpi kernel module and manually install it. This is easier, and should be more compatable, than compiling the whole kernel.

I am far from an expert, so the steps below could probably be done better - please do add further info.

Here are the steps I took:

Install required packages
```

sudo apt-get install build-essential linux-source libncurses5-dev kernel-package

```

Copy and extract the kernel sources to a working directory (check your version number)
```

cd ~
mkdir src
cp /usr/src/linux-source-2.6.27.tar.bz2 src
cd src
tar xvjf linux-source-2.6.27.tar.bz2

```

Download the patch from [here]("http://memebeam.org/free-software/toshiba_acpi/") that most closely matches your kernel version. the 2.6.26 patch works on kernel 2.6.27 currently used in ubuntu 8.10.
```
wget http://memebeam.org/free-software/toshiba_acpi/toshiba_acpi-dev_toshiba_test5-linux_2.6.26.patch
```

Apply the patch - the first command checks it will all work. Only continue if it gives no errors.
```
patch -p0 < toshiba_acpi-dev_toshiba_test5-linux_2.6.26.patch --dry-run
patch -p0 < toshiba_acpi-dev_toshiba_test5-linux_2.6.26.patch

```

Create a makefile:
```

nano Makefile

```

Copy the following contents in, then exit with Ctrl+X, type 'y' to save, and take the default location:
```

obj-m += toshiba_acpi.o

all:
	make -C /lib/modules/$(shell uname -r)/build M=$(PWD) modules

clean:
	make -C /lib/modules/$(shell uname -r)/build M=$(PWD) clean

```

Build the kernel module:
```

make

```

There should now be a whole lot of files in that folder. The important one is called toshiba_acpi.ko

To install the module by hand, you need to copy it to the correct directory and modify one file which tells the kernel what dependencies the module has.
```

sudo cp toshiba_acpi.ko /lib/modules/`uname -r`/kernel/drivers/acpi/
cd /lib/modules/`uname -r`

```

Using the following command should add the required line to the end of the file, but for some reason even as sudo and having modified file and directory permissions, I got a permission denied error:
```

echo "/lib/modules/`uname -r`/kernel/drivers/acpi/toshiba_acpi.ko:" >> modules.dep

```

It works with nano though:
```

echo "/lib/modules/`uname -r`/kernel/drivers/acpi/toshiba_acpi.ko:"

```
Copy this output, then:
```

sudo nano modules.dep

```
press page-down to end of file, then paste in the copied output. Save and exit (Ctrl-X, 'y', Enter)

That should be it done. You can then load the module using:
```

sudo modprobe toshiba_acpi

```

Bluetooth can be turned on and off using the commands:
```

sudo toshset -bluetooth on
sudo toshset -bluetooth off

```

Further info from toshset:
```

sudo toshset -a

```

Done!

Further info can be found at the following pages:
Bug reports:
[https://bugs.launchpad.net/ubuntu/+source/toshset/+bug/179728](https://bugs.launchpad.net/ubuntu/+source/toshset/+bug/179728)
[https://bugs.launchpad.net/ubuntu/+source/toshset/+bug/181374](https://bugs.launchpad.net/ubuntu/+source/toshset/+bug/181374)
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/269831](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/269831)
Kernel compiling:
[http://www.howtoforge.com/kernel_compilation_ubuntu_p2](http://www.howtoforge.com/kernel_compilation_ubuntu_p2)
Other:
[http://www.flurble.org/computers/toshset.pl](http://www.flurble.org/computers/toshset.pl)

As always, I'm a beginner in this game, but if this helps a few others until the official patch is released then it's worth it.

---

### Post by raztus on 2008-11-20
Thank you so much for this post!  This is exactly what I've been looking for.  However, when I try to execute the patch (with options --dry-run) I get the following error:

> <computer>:~/src$ patch -p0 < toshiba_acpi-dev_toshiba_test5-linux_2.6.26.patch --dry-run
can't find file to patch at input line 3
Perhaps you used the wrong -p or --strip option?
The text leading up to this was:
--------------------------
|--- toshiba_acpi.c.orig	2008-08-30 22:12:50.000000000 -0700
|+++ toshiba_acpi.c	2008-08-31 12:03:07.000000000 -0700
--------------------------
File to patch: 

Any idea why this might be happening?  I verified that toshiba_acpi.c does exist, it's in /drivers/acpi/toshiba_acpi.c.  How do I work through this?

Thanks!

---

### Post by rubentm on 2008-11-20
WOOOOOW!!!! THX. U are the best!! 
The only thing that needs to add is, before aplying the patch:

```
cp toshiba_acpi-dev_toshiba_test5-linux_2.6.26.patch linux-source-2.6.27/drivers/acpi
cd linux-source-2.6.27/drivers/acpi
```

:guitar: U ROCKS!!!

---

### Post by raztus on 2008-11-21
Thanks rubentm for the added step!  That solved the error from my first post.

adpsimpson: the only part of your steps that confused me was the line "Copy this output, then: sudo nano modules.dep".  I thought you were telling me to copy sudo nano modules.dep.  A better way to word it would be "copy the above code, then run the following: sudo nano modules.dep".

Unfortunately for me, it looks like I might be out of luck on a Toshiba Satellite A305.  My bios is v 1.50 InsydeH20.  Turns out this probably isn't suppoted by toshiba_acpi.  From [http://memebeam.org/toys/ToshibaAcpiDriver:](http://memebeam.org/toys/ToshibaAcpiDriver:)

> Another important note: This driver does not work on all Toshiba laptops, particularly those models which seem to have a BIOS or other firmware which was not developed by Toshiba itself. New reverse engineering work will have to be done on these machines, or Toshiba will have to disclose the necessary details. (For support of machines with Phoenx BIOS, try the [Omnibook driver].) The error you will see in this case is:

    $ modprobe toshiba_acpi
    FATAL: Error inserting toshiba_acpi
    (.../kernel/drivers/acpi/toshiba_acpi.ko): No such device

This is the exact error I got.  I guess I'll try the Omnibook driver!  Thanks for your help.

---

### Post by oligig on 2008-11-28
Hello,

thanks for this detailed procedure !
I've one problem when i execute this command : 
```
sudo modprobe toshiba_acpi
```
The result is :
```
FATAL: Error inserting toshiba_acpi (/lib/modules/2.6.27-9-generic/kernel/drivers/acpi/toshiba_acpi.ko): Unknown symbol in module, or unknown parameter (see dmesg)
```
And dmesg :
```
[ 2334.701916] toshiba_acpi: Unknown parameter `hotkeys_over_acpi'
```

Can i've help please ?

---

### Post by Paresh on 2008-12-01
I get this error also on my Toshiba Tecra A9


'dmesg | grep toshiba' gives this

```
[28067.064484] toshiba_acpi: Unknown parameter `hotkeys_over_acpi'
[28110.661291] toshiba_acpi: Unknown parameter `hotkeys_over_acpi'
[28138.558902] toshiba_acpi: Unknown parameter `iba_acpi'
[28169.318486] toshiba_acpi: Unknown parameter `hotkeys_over_acpi'

```

Any help would be appreciated

Paresh

---

### Post by Paresh on 2008-12-02
Well, I fixed my error by removing the line 

```
options toshiba_acpi hotkeys_over_acpi=1
```

from the 'toshiba_acpi.modprobe' file and it worked for me.

Not sure what this line does, but bluetooth is now working.

Only issue now is that I have to do
```
sudo toshset -bluetooth on
```
after each reboot or resume from suspend.

---

### Post by anjames on 2009-01-26
Seems to work well enough, including of course the fixes added by rubentm and Paresh. 

Now I'm roughing it out with toshset and xorg.conf trying to get my second monitor working...
toshset -v -video both
xorg.conf ...?

To the intergoogle.

---

### Post by Nareto on 2009-01-31
Hello, i have a problem with the patch:
```
renato@renato-laptop:~/src/linux-source-2.6.27/drivers/acpi$ patch -p0 < toshiba_acpi-dev_toshiba_test5-linux_2.6.26.patch --dry-run
patching file toshiba_acpi.c
Hunk #1 FAILED at 28.
Hunk #2 FAILED at 55.
Hunk #3 succeeded at 932 with fuzz 2 (offset 417 lines).
Hunk #4 succeeded at 1312 with fuzz 2 (offset 554 lines).
Hunk #5 FAILED at 1321.
Hunk #6 succeeded at 1345 with fuzz 2 (offset 561 lines).
3 out of 6 hunks FAILED -- saving rejects to file toshiba_acpi.c.rej

```

any ideas as to what may be the problem? I'm running on 8.10 intrepid fresh installed.

---

### Post by trundlenut on 2009-02-02
I have had exactly the same problem after reinstalling and updating intrepid.  It worked OK a week or so ago so I am assuming that a recent update has done something to stop it.  I have no idea what though.

---

### Post by trundlenut on 2009-02-02
had another go with a clean install.  I noticed that when all the source stuff was being downloaded that the kernel version was 2.6.27-11 rather than -9 so I'm assuming that could be the source of the problem. Presumably we need the older version of the kernel.

---

### Post by avdzm on 2009-02-13
I have the same problem as Nareto,
I get this
patching file toshiba_acpi.c
Hunk #1 FAILED at 28.
Hunk #2 FAILED at 55.
Hunk #3 succeeded at 747 with fuzz 2 (offset 232 lines).
Hunk #4 succeeded at 1125 with fuzz 2 (offset 367 lines).
Hunk #5 FAILED at 1134.
Hunk #6 succeeded at 1155 with fuzz 2 (offset 371 lines).
3 out of 6 hunks FAILED -- saving rejects to file toshiba_acpi.c.rej

I have ubuntu 8.10 updates from 8.04.

any help will be appreciated
thanks

---

### Post by Portending Ennui on 2009-02-16
For the ones having trouble patching:

If using kernel 2.6.26-11, i skipped the patch since it threw errors, and compiled and installed the kernel.  My Bluetooth works with my Fn key ("Fn" + "F8").  The included kernel module source works, but I did use your makefile. Thank You VERY much.  I've been working on this forever.

Toshiba Qosmio G35-AV600, btw.

Cheers! And Thanks, again!

Now, off to try to figure out RAID-0 again!

---

### Post by avdzm on 2009-02-16
hey all,

I have kernel 2.6.27-11-generic, 
i tried the tutorial skipping the patch, since i was getting errors.

I get stuck at 
```
sudo modprobe toshiba_acpi
```
I get this error msg
"FATAL: Error inserting toshiba_acpi (/lib/modules/2.6.27-11-generic/kernel/drivers/acpi/toshiba_acpi.ko): No such device"

I check the file is there.
any ideas?
I am gonna try to restart the laptop. 
BTW i have A200-10X

---

### Post by avdzm on 2009-02-20
u know what's funny,
my bluetooth worked on ubuntu 7.10.
then when i updated to 8.04 it stop.

has any1 had luck with 2.6.27-12?
or should i downgrade the kernel?

---

### Post by Sebjectivist on 2009-03-03
> **avdzm said:**
> I have the same problem as Nareto,
I get this
patching file toshiba_acpi.c
Hunk #1 FAILED at 28.
Hunk #2 FAILED at 55.
Hunk #3 succeeded at 747 with fuzz 2 (offset 232 lines).
Hunk #4 succeeded at 1125 with fuzz 2 (offset 367 lines).
Hunk #5 FAILED at 1134.
Hunk #6 succeeded at 1155 with fuzz 2 (offset 371 lines).
3 out of 6 hunks FAILED -- saving rejects to file toshiba_acpi.c.rej

I have ubuntu 8.10 updates from 8.04.

any help will be appreciated
thanks
I got this problem as well (running kernel 2.6.27-11), but when I read Portending Ennui skipped the patch and got it working I tried;

sudo modprobe toshiba_acpi

then installed toshset;

sudo apt-get install toshset

and switched on bluetooth succesfully;

sudo toshset -bluetooth on

:p

---

### Post by avdzm on 2009-03-10
hey Sebjectivist,

have u upgraded to the new kernel?
If so does the bluetooth still work?

---

### Post by andyni on 2009-03-23
OK, can anyone join in with problems?:

Satellite pro 2100, slow brain, small RAM.


like others, I get 

```
~/src/linux-source-2.6.27/drivers/acpi$ patch -p0 < toshiba_acpi-dev_toshiba_test5-linux_2.6.26.patch
patching file toshiba_acpi.c
Hunk #1 FAILED at 28.
Hunk #2 FAILED at 55.
Hunk #3 succeeded at 747 with fuzz 2 (offset 232 lines).
Hunk #4 succeeded at 1125 with fuzz 2 (offset 367 lines).
Hunk #5 FAILED at 1134.
Hunk #6 succeeded at 1155 with fuzz 2 (offset 371 lines).
3 out of 6 hunks FAILED -- saving rejects to file toshiba_acpi.c.rej

```

so, following the hint in some other posts, skipped the patch step and carried on with the MAKE.

Now we get as far as:

```
~/src/linux-source-2.6.27/drivers/acpi$ sudo cp toshiba_acpi.ko /lib/modules/`uname -r`/kernel/drivers/acpi/
cp: cannot stat `toshiba_acpi.ko': No such file or directory

```

and it's right, toshiba_acpi.ko doesn't exist.
i've trawled all suggestions now for the last 5 hours and everyone who's suggested a fix to get this internal Bluetooth hardware working has been a dead end. Is there ANY way to get this piece of junk to turn on it's inbuilt hardware? 

Where's that guy that told me Ubuntu just worked, and it was just like running Windows but faster and free? I'll kill him when I get my hands on him.

---

### Post by spinomod on 2009-06-25
Hi, I've a satellite u200, with Debian Lenny and Kernel 2.6.30, this patch work with it??

---

### Post by golzalo on 2009-07-09
I had the same problem as [Nareto]("http://ubuntuforums.org/member.php?u=759987") . I found [here]("http://linfox.es/24/04/2008/bluetooth-integrado-de-toshiba-satellite-u300-13h-en-gnulinux/") the solution. The only problem is that the explanation is in Spanish, but with the commands i think you will understand.


This is my first contribution, hope this work for you! Regards! ;)

---

### Post by vnieto on 2009-11-04
I have the same problem on Karmic, also the fan is not working and the temperature is up until restart the machine.

I NEED SOME HELP

---

### Post by avdzm on 2009-11-12
any luck with Karmic?

---

### Post by Delve on 2010-02-22
Please check the below.  The below post worked for me.  Thanks to Andrew Martin the author of this post.

[http://andrewm.info/software/guides/27-bluetooth-support-for-toshiba-laptops-on-ubuntu](http://andrewm.info/software/guides/27-bluetooth-support-for-toshiba-laptops-on-ubuntu)

---

### Post by linuxguru1 on 2010-06-03
> **Delve said:**
> Please check the below.  The below post worked for me.  Thanks to Andrew Martin the author of this post.

[http://andrewm.info/software/guides/27-bluetooth-support-for-toshiba-laptops-on-ubuntu](http://andrewm.info/software/guides/27-bluetooth-support-for-toshiba-laptops-on-ubuntu)


Awesome! Huge thanks!

---

### Post by jfpiret on 2011-04-17
Hi there,

Thanks for that great tuto about Toshset...

I have a problem : I installed an Ubuntu 10.10 on my Toshiba L300D. Everything seems to be working fine except the CPU fan.
My µP is always above 60°C I don't think it's good for it :-(

I've tried your method to get the toshiba_acpi patch but I get an error while patching : 
```

@Satellite-L300D:~/src/linux-source-2.6.35/drivers/acpi$ sudo patch -p0 < toshiba_acpi-dev_toshiba_test5-linux_2.6.29.patch --dry-runpatching file toshiba_acpi.c
Hunk #1 FAILED at 29.
Hunk #2 FAILED at 42.
Hunk #3 FAILED at 654.
Hunk #4 FAILED at 720.
Hunk #5 FAILED at 733.
Hunk #6 FAILED at 761.
6 out of 6 hunks FAILED -- saving rejects to file toshiba_acpi.c.rej

```Could you tell me what is wrong anf if I can resolve the problem ?

Thank you !

JF

---

