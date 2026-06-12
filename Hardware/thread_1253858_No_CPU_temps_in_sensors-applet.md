---
title: "No CPU temps in sensors-applet"
date: 2009-08-30
forum: Hardware
---

### Post by magicmax0 on 2009-08-30
Ok my motherboard is an AMD 790X series made by Gigabyte, model GA-MA790X-UD4P. My CPU model is an AMD Phenom II X4 940. When i run sensors-detect and enter yes to all i finally get this:

[I]To load everything that is needed, add this to /etc/modules:

#----cut here----
# Chip drivers
# no driver for AMD K10 thermal sensors yet
#----cut here----

Do you want to add these lines automatically? (yes/NO)yes[/I]

But that seems to do nothing. I noticed it says no drivers there, how can i install them manually? Or do they not exist? The only sensors i get are for my hard drive. PLEASE HELP!

---

### Post by mechdave on 2009-08-30
There is a fix, you need the [k10temp module code from here]("http://lists.lm-sensors.org/pipermail/lm-sensors/attachments/20080718/d51be536/attachment.bin"). Put this in it's own folder named k10temp_module. Rename the downloaded file to k10temp.c Now for the makefile... Here is one I prepared earlier :) 

```
obj-m += k10temp.o
all :
	make -C /lib/modules/$(shell uname -r)/build M=$(PWD) modules
clean:
	make -C /lib/modules/$(shell uname -r)/build M=$(PWD) clean 
```

Save this as Makefile and put in the same directory as k10temp.c

The next file you need is the install file for the module, here is one I whipped up earlier...

```
#!/bin/sh
install -m 644 k10temp.ko /lib/modules/`uname -r`/kernel/drivers/k10temp.ko
/sbin/depmod -a
```

Name this install.sh and put it in the same directory as k10temp.c

Now we are almost ready...
Install build-essential
```
sudo apt-get install build-essential
```

Then install your relevant kernel headers, use uname -r to sort out which headers you have
```
sudo apt-get install linux-headers-`uname -r`
``` 
Now we can build the module... navigate to the k10temp_module directory in a terminal and type make
This will make the kernel module, if all goes well you should get similar to the following:
```
make -C /lib/modules/2.6.28-15-generic/build M=/home/dave/kernel_modules/k10temp modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.28-15-generic'
  CC [M]  /home/dave/kernel_modules/k10temp/k10temp.o
/home/dave/kernel_modules/k10temp/k10temp.c: In function &#8216;k10temp_update_device&#8217;:
/home/dave/kernel_modules/k10temp/k10temp.c:54: warning: unused variable &#8216;tmp&#8217;
/home/dave/kernel_modules/k10temp/k10temp.c: In function &#8216;show_temp&#8217;:
/home/dave/kernel_modules/k10temp/k10temp.c:91: warning: unused variable &#8216;place&#8217;
/home/dave/kernel_modules/k10temp/k10temp.c:90: warning: unused variable &#8216;core&#8217;
/home/dave/kernel_modules/k10temp/k10temp.c: In function &#8216;k10temp_probe&#8217;:
/home/dave/kernel_modules/k10temp/k10temp.c:150: warning: label &#8216;exit_free&#8217; defined but not used
/home/dave/kernel_modules/k10temp/k10temp.c:115: warning: unused variable &#8216;temp&#8217;
/home/dave/kernel_modules/k10temp/k10temp.c:114: warning: unused variable &#8216;scfg&#8217;
  Building modules, stage 2.
  MODPOST 1 modules
  CC      /home/dave/kernel_modules/k10temp/k10temp.mod.o
  LD [M]  /home/dave/kernel_modules/k10temp/k10temp.ko
make[1]: Leaving directory `/usr/src/linux-headers-2.6.28-15-generic'

```
after that run the install script...
```
sudo sh install.sh
```
Now reboot your machine...

After reboot open a terminal and type...
```
lsmod | grep k10temp
```
you should have something like this:
```
k10temp                10880  0
```
if not, then your module isn't running and you need to add the following line to /etc/modules then reboot.
```
#k10 AMD temp module
k10temp

```
This will insert the module at boot up if the system didn't automatically do it for you.
Now in your sensors applet you should have your cpu temp... YAY

---

### Post by magicmax0 on 2009-08-30
This worked perfectly for me. All i get is a "temp1" sensor, i have a quad core so im assuming this is an average temp over all my cores. I have seen many posts about problems with AMD K10 sensors, and i couldn't find a fix anywhere. Finally, its fixed! Thank you for taking the time to do this mechdave. I hope this post gets a sticky or something because i know im not the only one who has this problem.

---

### Post by CheresZabor on 2010-01-29
I'm getting the same issue as magic, shouldnt there be much more then just one dinky sensors on this motherboard, for example the fan speeds and so forth. 

Does anyone have any more tweaks for the K10 drivers/sensors

Thanks

---

### Post by mr clark25 on 2010-01-29
that looks like the long way around. i made a youtube video some time ago on how to get this to work.

[http://www.youtube.com/watch?v=kaVcWtraWAs](http://www.youtube.com/watch?v=kaVcWtraWAs)

---

### Post by theNitsud on 2010-01-29
I have a situation where lsmod shows k10temp, but sensors doesn't show any installed sensors.  Any suggestions?

Thx

---

### Post by VideoRoy on 2010-01-30
I was able to get some sensors installed using the source files from here 

[http://www.lm-sensors.org/wiki/Devices](http://www.lm-sensors.org/wiki/Devices)

[http://khali.linux-fr.org/devel/misc/k10temp/](http://khali.linux-fr.org/devel/misc/k10temp/)

but after running the Makefile and installing I do not get CPU temp which is what I am most interested in.  I get one temp that is obviously my MOBO because it is too low and matches what I see in BIOS.  My Nvidia card shows up too but I think that is coming from my Nvidia applet not K10temp.

Close but not quite there.

---

### Post by Mark_in_Hollywood on 2010-02-16
The following took some figuring to get to. Yet I'm still not able to sort all this out. After some gaffs at the -install -headers stuff - I got the following, but I have NO clue as to which is which for installing this K10 modules. Posters, especially MECHDAVE, please be literal in giving instructions. xd.

mark@Lexington-19-Karmic:/usr/src/k10temp-module$ sudo apt-get install linux-headers 2.6.31.19-generic
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package linux-headers is a virtual package provided by:
  linux-headers-2.6.31-19-generic-pae 2.6.31-19.56
  linux-headers-2.6.31-19-generic 2.6.31-19.56
  linux-headers-2.6.31-19-386 2.6.31-19.56
  linux-headers-2.6.31-19 2.6.31-19.56
  linux-headers-2.6.31-17-generic-pae 2.6.31-17.54
  linux-headers-2.6.31-17-generic 2.6.31-17.54
  linux-headers-2.6.31-17-386 2.6.31-17.54
  linux-headers-2.6.31-17 2.6.31-17.54
  linux-headers-2.6.31-16-generic-pae 2.6.31-16.53
  linux-headers-2.6.31-16-generic 2.6.31-16.53
  linux-headers-2.6.31-16-386 2.6.31-16.53
  linux-headers-2.6.31-16 2.6.31-16.53
  linux-headers-2.6.31-15-generic-pae 2.6.31-15.50
  linux-headers-2.6.31-15-generic 2.6.31-15.50
  linux-headers-2.6.31-15-386 2.6.31-15.50
  linux-headers-2.6.31-15 2.6.31-15.50
  linux-headers-2.6.31-9-rt 2.6.31-9.152
  linux-headers-2.6.31-14-generic-pae 2.6.31-14.48
  linux-headers-2.6.31-14-generic 2.6.31-14.48
  linux-headers-2.6.31-14-386 2.6.31-14.48
  linux-headers-2.6.31-14 2.6.31-14.48
You should explicitly select one to install.
E: Package linux-headers has no installation candidate

So, do I use:


 linux-headers-2.6.31-19-generic-pae 2.6.31-19.56 

or

  linux-headers-2.6.31-19-generic 2.6.31-19.56

and is that then to be:

sudo apt-get install linux-headers- 2.6.31.19-generic 2.6.31-19.56 ???

---

### Post by miegiel on 2010-02-16
> **Mark_in_Hollywood said:**
> The following took some figuring to get to. Yet I'm still not able to sort all this out. After some gaffs at the -install -headers stuff - I got the following, but I have NO clue as to which is which for installing this K10 modules. Posters, especially MECHDAVE, please be literal in giving instructions. xd.

mark@Lexington-19-Karmic:/usr/src/k10temp-module$ sudo apt-get install linux-headers 2.6.31.19-generic
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package linux-headers is a virtual package provided by:
  linux-headers-2.6.31-19-generic-pae 2.6.31-19.56
...
  linux-headers-2.6.31-14 2.6.31-14.48
You should explicitly select one to install.
E: Package linux-headers has no installation candidate

So, do I use:


 linux-headers-2.6.31-19-generic-pae 2.6.31-19.56 

or

  linux-headers-2.6.31-19-generic 2.6.31-19.56

and is that then to be:

sudo apt-get install linux-headers- 2.6.31.19-generic 2.6.31-19.56 ???

The PAE kernel gives 32bit kernels the ability to use more than 3GB memory (normal 32bit kernels are limited to a little less than 3GB).

---

### Post by Mark_in_Hollywood on 2010-02-16
So I don't use the **pae** but I still have no idea of the 21 listed "kernels" which one to use. Sorry for my obstinacy, but I'm lost here.

---

### Post by miegiel on 2010-02-16
> **Mark_in_Hollywood said:**
> So I don't use the **pae** but I still have no idea of the 21 listed "kernels" which one to use. Sorry for my obstinacy, but I'm lost here.

2.6.31-19 is the most recent kernel. To keep it short; I'm using the 2.6.31-19-generic 2.6.31-19.56 kernel.

---

### Post by Mark_in_Hollywood on 2010-02-16
Nope, I cannot do this alone:

mark@Lexington-19-Karmic:/usr/src/k10temp-module$ sudo aptitude install linux-headers-2.6.31-19-generic 2.6.31-19.56[sudo] password for mark: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Couldn't find any package whose name or description matched "2.6.31-19.56"
Couldn't find any package whose name or description matched "2.6.31-19.56"
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

---

### Post by miegiel on 2010-02-16
> **Mark_in_Hollywood said:**
> Nope, I cannot do this alone:

mark@Lexington-19-Karmic:/usr/src/k10temp-module$ sudo aptitude install linux-headers-2.6.31-19-generic 2.6.31-19.56[sudo] password for mark: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Couldn't find any package whose name or description matched "2.6.31-19.56"
Couldn't find any package whose name or description matched "2.6.31-19.56"
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

Do
```
sudo apt-get install linux-headers-2.6.31-19-generic
```

---

### Post by Mark_in_Hollywood on 2010-02-16
mark@Lexington-19-Karmic:/usr/src/k10temp-module$ sudo apt-get install linux-headers-2.6.31-19-generic
Reading package lists... Done
Building dependency tree       
Reading state information... Done
linux-headers-2.6.31-19-generic is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

---

### Post by miegiel on 2010-02-16
> **Mark_in_Hollywood said:**
> mark@Lexington-19-Karmic:/usr/src/k10temp-module$ sudo apt-get install linux-headers-2.6.31-19-generic
Reading package lists... Done
Building dependency tree       
Reading state information... Done
linux-headers-2.6.31-19-generic is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

That means it's installed already 8)

---

### Post by Mark_in_Hollywood on 2010-02-16
Next, this happened:

mark@Lexington-19-Karmic:/usr/src/k10temp-module$ make -C /lib/modules/2.6.31-19-generic/build M=/usr/src/k10temp-module/kernel_modules/k10temp modules
make: Entering directory `/usr/src/linux-headers-2.6.31-19-generic'
mkdir: cannot create directory `/usr/src/k10temp-module/kernel_modules': Permission denied
scripts/Makefile.build:44: /usr/src/k10temp-module/kernel_modules/k10temp/Makefile: No such file or directory
make[1]: *** No rule to make target `/usr/src/k10temp-module/kernel_modules/k10temp/Makefile'.  Stop.
make: *** [_module_/usr/src/k10temp-module/kernel_modules/k10temp] Error 2
make: Leaving directory `/usr/src/linux-headers-2.6.31-19-generic'

---

### Post by miegiel on 2010-02-16
> **Mark_in_Hollywood said:**
> Next, this happened:

mark@Lexington-19-Karmic:/usr/src/k10temp-module$ make -C /lib/modules/2.6.31-19-generic/build M=/usr/src/k10temp-module/kernel_modules/k10temp modules
make: Entering directory `/usr/src/linux-headers-2.6.31-19-generic'
mkdir: cannot create directory `/usr/src/k10temp-module/kernel_modules': Permission denied
scripts/Makefile.build:44: /usr/src/k10temp-module/kernel_modules/k10temp/Makefile: No such file or directory
make[1]: *** No rule to make target `/usr/src/k10temp-module/kernel_modules/k10temp/Makefile'.  Stop.
make: *** [_module_/usr/src/k10temp-module/kernel_modules/k10temp] Error 2
make: Leaving directory `/usr/src/linux-headers-2.6.31-19-generic'

I could be wrong, but I think you need to run that with *sudo* (I don't really have experience with "making" stuff).

---

### Post by Mark_in_Hollywood on 2010-02-16
miegel,

I've queried the forums and make DOES NOT require sudo. I have not even tried this as I've never seen make with sudo. I have seen sudo make install or something like that, however. 

Anybody know what's wrong here? Do I need to create a 

kernel_modules

in (or under) /usr/src/k10temp-module, and more importantly why didn't make do this?

a little more digging and I've determined that sudo make install is (more or less) forbidden. The command is more likely to be sudo checkinstall

---

### Post by miegiel on 2010-02-16
> **Mark_in_Hollywood said:**
> miegel,

I've queried the forums and make DOES NOT require sudo. I have not even tried this as I've never seen make with sudo. I have seen sudo make install or something like that, however. 

Anybody know what's wrong here? Do I need to create a 

kernel_modules

in (or under) /usr/src/k10temp-module, and more importantly why didn't make do this?

a little more digging and I've determined that sudo make install is (more or less) forbidden. The command is more likely to be sudo checkinstall

Ok, you've moved on beyond my expertize now. :D I hope you find your answers or help.

---

### Post by Mark_in_Hollywood on 2010-02-27
mark@Lexington-19-Karmic:/usr/src/k10temp_module$ ls
install.sh  k10temp.c  Makefile
mark@Lexington-19-Karmic:/usr/src/k10temp_module$ make
make: Nothing to be done for `all'.

Now what, please?

---

### Post by Ayuthia on 2010-02-27
> **Mark_in_Hollywood said:**
> miegel,

I've queried the forums and make DOES NOT require sudo. I have not even tried this as I've never seen make with sudo. I have seen sudo make install or something like that, however. 

Anybody know what's wrong here? Do I need to create a 

kernel_modules

in (or under) /usr/src/k10temp-module, and more importantly why didn't make do this?

a little more digging and I've determined that sudo make install is (more or less) forbidden. The command is more likely to be sudo checkinstall
You are correct that make does not need sudo privilege to run.  However, your kernel module source is located in /usr/src and that directory will not let you create any files without sudo privileges.  So if you want to compile the module, you will need to use sudo:
```

sudo make -C /lib/modules/2.6.31-19-generic/build M=/usr/src/k10temp-module/kernel_modules/k10temp modules
```

In theory, that should create the kernel module for you.  If it does not, please post the error message.

---

### Post by Mark_in_Hollywood on 2010-02-27
> In theory, that should create the kernel module for you.  If it does not, please post the error message.

Is it better to move the k10temp_module to /home/ and then run make?

---

### Post by Mark_in_Hollywood on 2010-02-27
Is it better to move the directory with the make file, the install.sh and the k10temp.c to another, non-root-privileged directory?

---

### Post by Ayuthia on 2010-02-27
It would be better to move it to a non-root privileged directory so that you don't accidentally write over something that might be important.  

EDIT:  In this case, it is not too big of a deal since you have it building in its own folder.  All of the items that it will build will be contained in that directory until you do the install.

---

### Post by gfuggs on 2010-03-06
> **theNitsud said:**
> I have a situation where lsmod shows k10temp, but sensors doesn't show any installed sensors.  Any suggestions?

Thx
I have a solution to this problem. Sort of.

I see this in dmesg:
[   16.256628] k10temp 0000:00:18.3: unreliable CPU thermal sensor; monitoring disabled

It is related to this: [http://support.amd.com/us/Processor_TechDocs/41322.pdf]("http://support.amd.com/us/Processor_TechDocs/41322.pdf"), relevant portion of which is below.
```
319 Inaccurate Temperature Measurement
Description
The internal thermal sensor used for CurTmp (F3xA4[31:21]), hardware thermal control (HTC),
software thermal control (STC) thermal zone, and the sideband temperature sensor interface (SB-TSI)
may report inconsistent values.
Potential Effect on System
HTC, STC thermal zone, and SB-TSI do not provide reliable thermal protection. This does not affect
THERMTRIP or the use of the STC-active state through StcPstateLimit or StcPstateEn
(F3x68[30:28, 5]).
Suggested Workaround
None. Systems should be designed with conventional thermal control and throttling methods or
utilize PROCHOT_L functionality based on temperature measurements from an analog thermal diode
(THERMDA/THERMDC).
Systems should not rely on the HTC features, STC thermal zone features, or use SB-TSI.
Software should not modify HtcTmpLmt (F3x64[22:16]) or enable any of the STC thermal zone
features by setting StcApcTmpLoEn, StcApcTmpHiEn, StcSbcTmpLoEn, or StcSpcTmpHiEn
(F3x68[3:0]).
Fix Planned
Yes

```

Do this:
sudo rmmod k10temp
sudo modprobe k10temp force=1

Now instead of nothing, get a temperature that's inaccurate (BIOS shows a temp of 33°C).  Sorry, that's all I got.

$ sensors
k10temp-pci-00c3
Adapter: PCI adapter
temp1:       +19.4°C  (high = +70.0°C)

---

### Post by santhony on 2010-04-18
NOTE:

You have to do this from your home directory.  

Anywhere else, you will have permission issues and will not process properly.


Follow the instructions very closely, verbatim and it will work...

---

### Post by santhony on 2010-04-18
This worked for me... allot easier..

[http://ubuntumanual.org/posts/126/how-to-detect-cpu-temperature-fan-speeds-and-voltages-lm-sensors-in-ubuntu](http://ubuntumanual.org/posts/126/how-to-detect-cpu-temperature-fan-speeds-and-voltages-lm-sensors-in-ubuntu)

---

### Post by Mark_in_Hollywood on 2010-04-24
> **santhony said:**
> This worked for me... allot easier..

[http://ubuntumanual.org/posts/126/how-to-detect-cpu-temperature-fan-speeds-and-voltages-lm-sensors-in-ubuntu](http://ubuntumanual.org/posts/126/how-to-detect-cpu-temperature-fan-speeds-and-voltages-lm-sensors-in-ubuntu)


While a nice explanation, it does not make the K10temp module.

---

### Post by WXN on 2010-04-27
Have you had any luck yet, Mr. Mark?  I'm working on this one too....

---

### Post by Intrepid Ibex on 2010-04-28
I only have this problem with my custom kernel. I guess I just need to add the i2c_nforce2 driver, which is needed for hardware sensors support...

---

### Post by mechdave on 2010-06-05
Mark, You have the correct headers installed? I have changed my instructions to run a little better. You also need to install build-essential. Where have you got to in compiling? You shouldn't need sudo to do this one :) Can you reply with your problems and I will do my best to help you out with it...

---

### Post by armoftheland on 2010-08-22
Thanks to mechdave I can now view temps in the Shell, however still nothing in the sensors for some reason. Has there been any movement on this? I'm running 10.04 on a Toshiba Satellite A200-mr4. Have been working on overheating (have got the fan running now!) but still have overheating issue and monitoring would be my ace in the hole.

---

### Post by Hakunka-Matata on 2011-01-18
My bootlog contains the following line: "**k10temp 0000:00:18.3: unreliable CPU thermal sensor; monitoring disabled"**

after installing lm-sensors and the other apps listed, all my temps show up, only one temp for CPU though, instead of the 3 cores this BIOS allows to run, but motherboard, fan speeds, voltages, all works fine.

---

