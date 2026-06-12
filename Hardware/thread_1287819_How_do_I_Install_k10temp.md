---
title: "How do I Install k10temp?"
date: 2009-10-10
forum: Hardware
---

### Post by Penguin Guy on 2009-10-10
[LIST=1]
[*]Make a new directory and open it:
```
mkdir -p 'k10temp'
cd 'k10temp'
```
[*]Download the file as [FONT="Courier New"]k10temp.c[/FONT]:
```
wget -O 'k10temp.c' 'http://lists.lm-sensors.org/pipermail/lm-sensors/attachments/20080718/d51be536/attachment.bin'
```
[*]Create a makefile:
```
echo 'obj-m := k10temp.o
KDIR := /lib/modules/$(shell uname -r)/build
PWD := $(shell pwd)
default:
$(MAKE) -C $(KDIR) SUBDIRS=$(PWD) modules' > Makefile
```
[*]Download the Linux headers [(you may need to specify the version)]("http://ubuntuforums.org/showthread.php?p=9777345#post9777345"):
```
sudo apt-get install linux-headers
```
[*]Run the make file:
```
sudo make -C /lib/modules/$(uname -r)/build M=$(pwd) modules
```
[*]Temporarily add the [FONT="Courier New"]k10temp[/FONT] module:
```
sudo insmod k10temp.ko
```
[*]Test if the sensors work ([COLOR="Red"]do not continue if the sensors do not work[/COLOR]):
```
sensors
```
[*]Permanently add the [FONT="Courier New"]k10temp[/FONT] module:
```
sudo cp k10temp.ko /lib/modules/$(uname -r)/kernel/drivers/hwmon
```
[*]Rebuild [FONT="Courier New"]modules.dep[/FONT] file:
```
sudo depmod
```
[*]Do some modprobing stuff:
```
sudo modprobe k10temp
```
[*]Add [FONT="Courier New"]k10temp[/FONT] to the startup list:
```
echo 'k10temp' | sudo tee -a /etc/modules >/dev/null
```
[*]Restart your computer.
[*]Test if the sensors work:
```
sensors
```
[/LIST]


Original Question:
----------------------------------------

I'm trying to get my fans to adjust their speed according to the temperature in my computer. I followed a guide and installed lm-senesors, but when I ran it (and after answering yes to all the questions) I receive this output:
```

#----cut here----
# Chip drivers
# no driver for AMD K10 thermal sensors yet
#----cut here----

```
But I can see a lot about k10temp 'patches' on the internet, I was wondering if installing one of these will get the sensor working and if so, how I can actually install the patch. I'm asking because I don't know much about any of this and would rather not have my CPU melt because of some stupid mistake I made with the fan driver.

**My Hardware:**
[LIST]
[*] Case: Antec 300
[*] PSU: Antec EarthWatts 750W
[*] Motherboard: Gigabyte GA-MA790FXT-UD5P 790FX
**[*] CPU: AMD Phenom II X3 710 2.6GHz**
[*] GPU: ATi Radeon 3850
[/LIST]

---

### Post by Tiedemate on 2009-11-28
Me too! I found a patch and tried to compile it, but *make* quits for some reason I can't understand. Does anyone have some info on this?

---

### Post by Tiedemate on 2009-11-28
Followed again very striclty this guide, and now it works!
[http://forum.ubuntuusers.de/topic/howto-cpu-temperatur-im-amd-ii-x4-phenom/?highlight=k10temp](http://forum.ubuntuusers.de/topic/howto-cpu-temperatur-im-amd-ii-x4-phenom/?highlight=k10temp)

---

### Post by Penguin Guy on 2009-11-29
I don't speak Dutch... :sad:

---

### Post by nstenz on 2010-07-12
You DO NOT NEED to get the entire kernel source. The kernel-headers package is sufficient.

---

### Post by Penguin Guy on 2010-07-12
> **nstenz said:**
> You DO NOT NEED to get the entire kernel source. The kernel-headers package is sufficient.
Thanks for the advice, I've updated the original post.

---

### Post by shane2peru on 2010-07-13
Can this be undone?  I think my machine ran cooler before doing this?  here is what sensors say:
sensors
acpitz-virtual-0
Adapter: Virtual device
temp1:       +90.0°C  (crit = +105.0°C)                  

k10temp-pci-00c3
Adapter: PCI adapter
temp1:       +84.2°C  (high = +70.0°C, crit = +100.0°C)

or can I cause the fan to kick on sooner, or to run more often?  I have always attributed my overheating problem to my ATI Radeon HD3100 card in this laptop, but perhaps we are on track here, not sure.  Any thoughts, ideas would be appreciated, I'm running some testing kernels, because normal kernels it overheats.  Thanks for the how to, worked fine.

Shane

---

### Post by Penguin Guy on 2010-07-14
> **shane2peru said:**
> Can this be undone?
Find the line [FONT="Courier New"]k10temp[/FONT] in [FONT="Courier New"]/etc/modules[/FONT] - remove that line and k10temp shouldn't start.

---

### Post by shane2peru on 2010-07-14
> **Penguin Guy said:**
> Find the line [FONT="Courier New"]k10temp[/FONT] in [FONT="Courier New"]/etc/modules[/FONT] - remove that line and k10temp shouldn't start.

Thanks!  That is simple enough, I thought it was something like that but couldn't remember. Nice guide!

Shane

**EDIT:**  Actually with the newest kernel that I installed .35rc1 that seemed to work better than anything.  Thanks.

---

### Post by wetinwales on 2010-07-25
Hi
Tonight's nightly update of Ubuntu 10.04 may have thrown up this problem:-

I have k10temp installed and working (showing only four of the six cores) on my Phenom II x6 1090T.
This evening after update I now have a constant flashing message on screen which I cannot close saying 
'Error Updating Sensor Temp1 
An error occurred while trying to 
update the value of the sensor temp1 
located at sensor://k10temp-pci-00c3/0 '

I commented out k10temp in etc/modules but it has not disabled k10temp and the flashing warning above still shows.

can anyone help with this one.
Thanks
D

---

### Post by P . P . L . on 2010-07-26
> **wetinwales said:**
> Hi
Tonight's nightly update of Ubuntu 10.04 may have thrown up this problem:-

I have k10temp installed and working (showing only four of the six cores) on my Phenom II x6 1090T.
This evening after update I now have a constant flashing message on screen which I cannot close saying 
'Error Updating Sensor Temp1 
An error occurred while trying to 
update the value of the sensor temp1 
located at sensor://k10temp-pci-00c3/0 '

I commented out k10temp in etc/modules but it has not disabled k10temp and the flashing warning above still shows.

can anyone help with this one.
Thanks
D

Hi wetinwales.

I can only get 1 temp for my X6 1055T to show, i can't seem to find a fix for it, i have all the latest updates installed at least you've got 4 cores to show, how can i ask.

---

### Post by wetinwales on 2010-07-26
Hi
I followed the instructions in the first post above and it worked.
The 'sensors-applet' was in synaptic.

BTW I tried to reinstall sensors applet today, after removal, and re-enabled k10temp .... but nothing works!

---

### Post by P . P . L . on 2010-07-27
Hi.

I've had a look at my etc/modules file and there is no reference to the

k10 driver only it87, so before i do the install at the top of this thread 

is there some way to see if i have that driver somewhere on this system.

And if it's there how to get it to work, or do i just follow those 

instructions.

---

### Post by P . P . L . on 2010-07-27
Hi all.

Well i followed the instructions (to the letter), at the start of this 

thread and i still only have one extra temp showing now in Gkrellm. So does 

someone know whats wrong and how to fix it. I mean to get all six cores to 

show, it does under winblows!

Help.

---

### Post by P . P . L . on 2010-07-28
Looks like nobody knows or they don't care to fix this, i'm sure i'm not 

the only one to have this problem, not good for a new O.S. :(

---

### Post by Penguin Guy on 2010-07-29
Sorry about the slow response, haven't been on Ubuntu Forums for a week or so.

To be honest, I copied the steps from a website only making minor changes and don't actually know much about temperature monitoring myself. It may be that six-core CPUs are quite rare (I'd only ever heard of four-cores before now) and that there is simply no support for it yet. Are you sure you have six temperature monitors? I have a quad-core CPU, but all four cores share a single temperature monitor.

I would try [Googling "X6 1055T k10temp"]("http://www.google.com/search?q=X6+1055T+k10temp"), but the first result is this page.

---

### Post by P . P . L . on 2010-07-29
Hi Penguin Guy.

Pretty sure they all do, app's that i have seen for windows like speed fan, 

hardware monitor & AMD O.D. shows 6 core temps.

Then people with the new 12 core Opteron 6174 will have a big problem!

---

### Post by P . P . L . on 2010-08-01
Hi all.

This is part of the answer i got on the AMD forums when i asked about the 

core temp reading, so it looks like it's a software problem, wonder if 

someone can/will fix it?

======================================================================

Quote/ There are no actual sensors on each core. The core temps are 

calculated based on frequency/voltage/load/temp. 

For this reason I and many only go based on the single cpu (not core). /End

---

### Post by Penguin Guy on 2010-08-01
[QUOTE="slaveondope"]**There are no actual sensors on each core.** The core temps are calculated based on frequency/voltage/load/temp. diode found under the integrated heat sink. 
For this reason I and many only go based on the single cpu (not core) but the diode under the IHS because when overclocking the equation thats used gets some very inconsistent since voltages and clock speeds get so far out of the parameters. 
How to get the actual diode reading under Ubuntu I havent a clue. [/QUOTE]
There you go - Ubuntu shows one temperature because there is only one thermometer, the other temperatures are guessed. I'd call this a design choice rather than a bug. Is there a reason you want separate core temperatures?

---

### Post by P . P . L . on 2010-08-01
Hi Penguin Guy.

Well i guess i'm just fussy if Gkrellm can show the load on six cores or 

more, then why not show the temps for all cores if possible. I'm sure i'm 

not the only one that wants to see that happen.

Just needs someone with the programming knowledge and will to do it.

---

### Post by Clever_Username on 2010-08-09
> **Penguin Guy said:**
> [LIST=1]
[*]Make a new directory and open it:
```
mkdir -p 'k10temp'
cd 'k10temp'
```
[*]Download the file as [FONT="Courier New"]k10temp.c[/FONT]:
```
wget -O 'k10temp.c' 'http://lists.lm-sensors.org/pipermail/lm-sensors/attachments/20080718/d51be536/attachment.bin'
```
[*]Create a makefile:
```
echo 'obj-m := k10temp.o
KDIR := /lib/modules/$(shell uname -r)/build
PWD := $(shell pwd)
default:
$(MAKE) -C $(KDIR) SUBDIRS=$(PWD) modules' > Makefile
```
[*]Download the Linux headers:
```
sudo apt-get install linux-headers
```
[*]Run the make file:
```
sudo make -C /lib/modules/$(uname -r)/build M=$(pwd) modules
```
[*]Temporarily add the [FONT="Courier New"]k10temp[/FONT] module:
```
sudo insmod k10temp.ko
```
[*]Test if the sensors work ([COLOR="Red"]do not continue if the sensors do not work[/COLOR]):
```
sensors
```
[*]Permanently add the [FONT="Courier New"]k10temp[/FONT] module:
```
sudo cp k10temp.ko /lib/modules/$(uname -r)/kernel/drivers/hwmon
```
[*]Rebuild [FONT="Courier New"]modules.dep[/FONT] file:
```
sudo depmod
```
[*]Do some modprobing stuff:
```
sudo modprobe k10temp
```
[*]Add [FONT="Courier New"]k10temp[/FONT] to the startup list:
```
echo 'k10temp' | sudo tee -a /etc/modules >/dev/null
```
[*]Restart your computer.
[*]Test if the sensors work:
```
sensors
```
[/LIST]

----------------------------------------

I'm trying to get my fans to adjust their speed according to the temperature in my computer. I followed a guide and installed lm-senesors, but when I ran it (and after answering yes to all the questions) I receive this output:
```

#----cut here----
# Chip drivers
# no driver for AMD K10 thermal sensors yet
#----cut here----

```
But I can see a lot about k10temp 'patches' on the internet, I was wondering if installing one of these will get the sensor working and if so, how I can actually install the patch. I'm asking because I don't know much about any of this and would rather not have my CPU melt because of some stupid mistake I made with the fan driver.

**My Hardware:**
[LIST]
[*] Case: Antec 300
[*] PSU: Antec EarthWatts 750W
[*] Motherboard: Gigabyte GA-MA790FXT-UD5P 790FX
**[*] CPU: AMD Phenom II X3 710 2.6GHz**
[*] GPU: ATi Radeon 3850
[/LIST]




Hi, I've been trying to get this thing to work for a while now. When I do the apt-get install linux-headers, I get :
You should explicitly select one to install.
E: Package linux-headers has no installation candidate

And then when I issue the 'sensors' command, I get this:
mcdonald@mcdonald-desktop:~/k10temp$ sensors
No sensors found!
Make sure you loaded all the kernel drivers you need.
Try sensors-detect to find out which these are.

Any ideas?

---

### Post by sreeharsha.t on 2010-08-10
Hi,

I am using Acer Aspire 4530 laptop which has AMD Athlon X2 processor and Nvidia nForce MCP77MH.

My laptop overheats. It doesn't reboot but it is evident from the heat it produces. Also, the fan always run at the same speed. I learnt from this forum that my laptop requires the k10temp module for managing the fan speed automatically to cool the system. I did the steps for building the kernel module and inserted the module. However, the 'sensors' command shows the following output:

```
harsha@harsha-laptop:~/build/k10temp$ sudo insmod k10temp.ko
harsha@harsha-laptop:~/build/k10temp$ sensors
acpitz-virtual-0
Adapter: Virtual device
temp1:       +61.0°C  (crit = +105.0°C)            
```

Does the above output mean that k10temp isn't working with my motherboard?

Thanks,
Harsha.

---

### Post by theleftofsatan on 2010-08-21
I don't think this is giving me the correct temperature.

```
$ sensors
k10temp-pci-00c3
Adapter: PCI adapter
temp1:       +22.0°C 
```

---

### Post by 2hot6ft2 on 2010-08-23
Thanks for the guide Penguin Guy, it worked fine on Ultimate Edition 2.7 x64 which is based on Ubuntu 10.04 x64.
I downloaded the k10temp.c directly from here
[http://khali.linux-fr.org/devel/misc/k10temp/](http://khali.linux-fr.org/devel/misc/k10temp/)
Other than that I just followed your guide skipping "4. Download the Linux headers:" part.

And added it to the sensors applet on the top panel.
AMD Phenom II 955x4 BE with C3 revision
34 degrees C. Plugging away on boinc set at 80% of CPU time.
:guitar:
From what it says here: [http://www.lm-sensors.org/wiki/Devices](http://www.lm-sensors.org/wiki/Devices)
it looks like it will be included in the 2.6.33 kernel and up.
:popcorn:

---

### Post by Borromini on 2010-08-26
Just so you know, this also works with the k10temp source code in 2.6.35, and the advantage is you get an updated driver ;).

---

### Post by Penguin Guy on 2010-08-28
> **Clever_Username said:**
> 
[QUOTE=Penguin Guy;8084008]Snip.
Hi, I've been trying to get this thing to work for a while now. When I do the apt-get install linux-headers, I get :
You should explicitly select one to install.
E: Package linux-headers has no installation candidate

And then when I issue the 'sensors' command, I get this:
mcdonald@mcdonald-desktop:~/k10temp$ sensors
No sensors found!
Make sure you loaded all the kernel drivers you need.
Try sensors-detect to find out which these are.

Any ideas?[/QUOTE]
In that case choose the latest appropriate version from the list (most people will want a [FONT="Courier New"]generic[/FONT] kernel):
```
$ **sudo apt-get install linux-headers**
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package linux-headers is a virtual package provided by:
  linux-headers-2.6.32-24-server 2.6.32-24.42
  linux-headers-2.6.32-24-preempt 2.6.32-24.42
  **linux-headers-2.6.32-24-generic** 2.6.32-24.42
  linux-headers-2.6.32-24 2.6.32-24.42
  linux-headers-2.6.31-11-rt 2.6.31-11.154
  linux-headers-2.6.32-23-server 2.6.32-23.37
  linux-headers-2.6.32-23-preempt 2.6.32-23.37
  linux-headers-2.6.32-23-generic 2.6.32-23.37
  linux-headers-2.6.32-23 2.6.32-23.37
  linux-headers-2.6.32-22-server 2.6.32-22.36
  linux-headers-2.6.32-22-preempt 2.6.32-22.36
  linux-headers-2.6.32-22-generic 2.6.32-22.36
  linux-headers-2.6.32-22 2.6.32-22.36
  linux-headers-2.6.31-10-rt 2.6.31-10.153
  linux-headers-2.6.32-21-server 2.6.32-21.32
  linux-headers-2.6.32-21-preempt 2.6.32-21.32
  linux-headers-2.6.32-21-generic 2.6.32-21.32
  linux-headers-2.6.32-21 2.6.32-21.32
You should explicitly select one to install.
E: Package linux-headers has no installation candidate
$ **sudo apt-get install linux-headers-2.6.32-24-generic**

```

P.S. To make your post more readable please avoid quoting huge posts in your response, try to only quote the relevant parts. It would also help if you put your terminal output in code boxes. Thanks.

---

### Post by qbxk on 2010-09-10
Seems like I have to redo this process this every time I get a kernel upgrade.

Anybody know a way around that?  

I guess I can just do it while I'm in the console mode reinstalling my NVIDIA drivers too....

---

### Post by P . P . L . on 2010-09-11
Hi.

I hope someone knows how to fix this, the problem is nearly every time i 

restart my rig the sensors config file resets to the default and i have to 

go in and rename everything for temps, fans, volts the lot how to stop it 

happening, my other rig doesn't do it!

The one playing up is on 10.04lts if that helps, the other rig is still on 8.04lts.

---

### Post by james000222 on 2010-09-21
This was cool to run across (pun intended lol).

Yes indeed, it does look like it's going to be released with the next kernel. Aamof, you can download the most recent kernel and get a more recent version of k10temp.c. I dl'd 2.6.35 from linux.org, found the k10temp.c, and used it for the excellent howto by Penguin Guy, using the most recent linux-headers (linux-headers-2.6.32-24-generic).

Outpt from sensors for an AMD 1055T 6-core on an M4A88TD-V EVO/USB3:

atk0110-acpi-0
Adapter: ACPI interface
Vcore Voltage:     +1.18 V  (min =  +0.85 V, max =  +1.60 V)
 +3.3 Voltage:     +3.40 V  (min =  +2.97 V, max =  +3.63 V)
 +5 Voltage:       +5.02 V  (min =  +4.50 V, max =  +5.50 V)
 +12 Voltage:     +12.28 V  (min = +10.20 V, max = +13.80 V)
CPU FAN Speed:    3552 RPM  (min =  600 RPM)
CHASSIS FAN Speed:   0 RPM  (min =  600 RPM)
POWER FAN Speed:     0 RPM  (min =  600 RPM)
CPU Temperature:   +31.0°C  (high = +60.0°C, crit = +95.0°C)  
MB Temperature:    +30.0°C  (high = +45.0°C, crit = +75.0°C)  

k10temp-pci-00c3
Adapter: PCI adapter
temp1:       +19.5°C  (high = +70.0°C, crit = +99.5°C)  

So yeah, it only shows one core - but the CPU is one solid chunk - not six chunks. It makes sense to have one temp.

Thanks penguin guy!

---

### Post by P . P . L . on 2010-10-04
Hi.

Well since the update for 10.04 the other day the k10temp module has 

stopped working, so do i have to run threw the whole install thing again or 

is there a simple way/short cut to get it going again since all the files 

should still be their.

help please.

---

### Post by P . P . L . on 2010-10-07
"BUMP"

So no one knows how to get this going again.

---

### Post by qbxk on 2010-10-07
aww pete, you just gotta go follow all the directions from the start again basically.  if you still have the files from last time just do a make && sudo make install and you'll be all set

this thread sucks though, i'm outta here, good luck

---

### Post by P . P . L . on 2010-10-08
> **qbxk said:**
> aww pete, you just gotta go follow all the directions from the start again basically.  if you still have the files from last time just do a make && sudo make install and you'll be all set

this thread sucks though, i'm outta here, good luck

==============================================================

Sorry to say that's not much help, I don't read minds. :confused:

The steps would be more helpful, if known!

---

### Post by Ayuthia on 2010-10-09
If you still have the k10temp folder, you just need to go back into there and then start at step 4 (in case the linux header files are not there).

---

### Post by pcolamar on 2010-10-09
Hi,
 I have compiled and inserted k10temp but the temperature it reads is 0C.
Is there any file I have to configure ?
Here below some additional info:

$ uname -a
Linux HomeX6 2.6.32-25-generic #44-Ubuntu SMP Fri Sep 17 20:05:27 UTC 2010 x86_64 GNU/Linux

----

$ sensors
k10temp-pci-00c3
Adapter: PCI adapter
temp1:        +0.0°C  (high = +70.0°C)     
----

$ lsmod | grep k10
k10temp                 3447  0 

-------
Hardware:
ASrock 880g Extreme3
CPU AMD x6 1055T

Thanks
Palmer

---

### Post by Penguin Guy on 2010-10-09
> **Peter Leman said:**
> The steps would be more helpful, if known!
I think he means the steps in the first post.

> **qbxk said:**
> this thread sucks though, i'm outta here, good luck
Sorry, I just posted the instructions because I thought they might be helpful to someone - apart from understanding the commands themselves, I know very little about the subject. I gave up on temperature monitoring myself a while back.

---

### Post by Ayuthia on 2010-10-09
> **pcolamar said:**
> Hi,
 I have compiled and inserted k10temp but the temperature it reads is 0C.
Is there any file I have to configure ?
Here below some additional info:

$ uname -a
Linux HomeX6 2.6.32-25-generic #44-Ubuntu SMP Fri Sep 17 20:05:27 UTC 2010 x86_64 GNU/Linux

----

$ sensors
k10temp-pci-00c3
Adapter: PCI adapter
temp1:        +0.0°C  (high = +70.0°C)     
----

$ lsmod | grep k10
k10temp                 3447  0 

-------
Hardware:
ASrock 880g Extreme3
CPU AMD x6 1055T

Thanks
Palmer

Can you check the results of:
```

cat /sys/class/hwmon/hwmon0/device/temp1_input

```
I think that is where it is located.

---

### Post by smuggly on 2010-10-10
This thread is marked solved? can you please explain. thanks

---

### Post by Penguin Guy on 2010-10-10
> **smuggly said:**
> This thread is marked solved? can you please explain. thanks
I no longer want information on the subject. If you want information on the subject, feel free to start a new thread.

---

### Post by Ayuthia on 2010-10-11
The most recent version of the k10 kernel module along with a sensors (and lm_sensors) version of 3.1.2 or greater should get it to work.  I have not tested it in Maverick or Lucid, but sensors is reporting the information for me in Gentoo.  I am currently using a 2.6.35 kernel which is the same as Maverick.

EDIT: The k10temp module is in Maverick (without having to build it) and sensors seems to read it fine for the temp.  I have not been able to get sensors read the sensors.conf file for Lucid though.

---

### Post by mahmoodn on 2010-10-25
This is what I get at step 5:
```
mahmood@localhost:k10temp$ sudo make -C /lib/modules/$(uname -r)/build M=$(pwd) modules
make: Entering directory `/usr/src/linux-headers-2.6.32-25-generic'
/usr/src/linux-headers-2.6.32-25-generic/arch/x86/Makefile:81: stack protector enabled but no compiler support
  Building modules, stage 2.
  MODPOST 0 modules
make: Leaving directory `/usr/src/linux-headers-2.6.32-25-generic'
```

After that:
```
mahmood@orca:k10temp$ sudo insmod k10temp.ko
insmod: can't read 'k10temp.ko': No such file or directory
```
Any idea for that?

---

### Post by ShakeyJake on 2010-11-14
Just to say that this works great for me. Phenom II 955, MSI 770-C45, 2.6.33-generic, Lucid 64-bit. I now have the temp displayed in conky.

Thanks Penguin!

---

### Post by MestreLion on 2011-02-09
I have Linux Mint 10 (based on Ubuntu 10.10 Maverick) and sensors work perfectly out-of-the-box. Here are my results:

Motherboard: ASUS M4A89GTD-PRO/USB3 (890GX chipset)
CPU: AMD Phenom II x4 955

```

k10temp-pci-00c3
Adapter: PCI adapter
temp1:       +38.5°C  (high = +70.0°C, crit = +90.0°C)  

atk0110-acpi-0
Adapter: ACPI interface
Vcore Voltage:      +1.00 V  (min =  +0.80 V, max =  +1.60 V)
+3.3V Voltage:      +3.36 V  (min =  +2.97 V, max =  +3.63 V)
+5V Voltage:        +5.14 V  (min =  +4.50 V, max =  +5.50 V)
+12V Voltage:      +11.97 V  (min = +10.20 V, max = +13.80 V)
CPU Fan Speed:     1956 RPM  (min =  600 RPM)
Chassis Fan Speed: 2129 RPM  (min =  600 RPM)
Chassis2 Fan Speed:2824 RPM  (min =  600 RPM)
Power Fan Speed:      0 RPM  (min =  600 RPM)
CPU Temperature:    +37.0°C  (high = +60.0°C, crit = +95.0°C)  
MB Temperature:     +31.0°C  (high = +45.0°C, crit = +75.0°C)  

```Noob question here: what is the difference between **k10temp-pci-00c3 **and **atk0110-acpi-0** ? Temp1 from k10temp is always very close to CPU Temperature from atk0110, but they are not the same. Are they both CPU readings? How come? And which is more reliable?

Thanks!

---

### Post by P . P . L . on 2011-02-10
> **MestreLion said:**
> I have Linux Mint 10 (based on Ubuntu 10.10 Maverick) and sensors work perfectly out-of-the-box. Here are my results:

Motherboard: ASUS M4A89GTD-PRO/USB3 (890GX chipset)
CPU: AMD Phenom II x4 955

```

k10temp-pci-00c3
Adapter: PCI adapter
temp1:       +38.5°C  (high = +70.0°C, crit = +90.0°C)  

atk0110-acpi-0
Adapter: ACPI interface
Vcore Voltage:      +1.00 V  (min =  +0.80 V, max =  +1.60 V)
+3.3V Voltage:      +3.36 V  (min =  +2.97 V, max =  +3.63 V)
+5V Voltage:        +5.14 V  (min =  +4.50 V, max =  +5.50 V)
+12V Voltage:      +11.97 V  (min = +10.20 V, max = +13.80 V)
CPU Fan Speed:     1956 RPM  (min =  600 RPM)
Chassis Fan Speed: 2129 RPM  (min =  600 RPM)
Chassis2 Fan Speed:2824 RPM  (min =  600 RPM)
Power Fan Speed:      0 RPM  (min =  600 RPM)
CPU Temperature:    +37.0°C  (high = +60.0°C, crit = +95.0°C)  
MB Temperature:     +31.0°C  (high = +45.0°C, crit = +75.0°C)  

```Noob question here: what is the difference between **k10temp-pci-00c3 **and **atk0110-acpi-0** ? Temp1 from k10temp is always very close to CPU Temperature from atk0110, but they are not the same. Are they both CPU readings? How come? And which is more reliable?

Thanks!

Hi MestreLion.

From what i've found out the K10temp comes from inside the CPU it's self

and the other CPU temp comes from under/inside the socket on the M/B.

They call k10temp the core temp(yes only one shows up)& the other is socket temp.

Hope that explains it.

---

### Post by TechZilla on 2011-02-11
OK, for the guy who doesn't want k10temp to start, if you ever want a module to not start, add its name to 
/etc/modprobe.d/blacklist.conf

you could do that by entering this command

```
$ sudo echo k10temp >> /etc/modprobe.d/blacklist.conf 
```

also remember these modules just monitor, regardless if you load k10temp or not, your actual temperature will the same. regardless of what sensors reports, its an interpretation from the temperature sensors. Many models are incorrect as well.

my BIOS says my CPU temp at idle is 34 C
k10temp says it around 15 C

my temperature didn't lower by running Linux, k10temp is either reading incorrectly or "more likely" libsensors doesn't have a correct configuration for my proc.

speaking of which if anyone also has this issue, or found a good config for /etc/sensors*, would love to hear about it.

---

### Post by MestreLion on 2011-02-11
> **Peter Leman said:**
> Hi MestreLion.

From what i've found out the K10temp comes from inside the CPU it's self

and the other CPU temp comes from under/inside the socket on the M/B.

They call k10temp the core temp(yes only one shows up)& the other is socket temp.

Hope that explains it.

Yes it does! Thank you very much!

Another noobish question: ive googled about atk0110 and found a LOT of material about a similar, **asus_atk0110. **As my board is an Asus one, should i use this instead of the "regular" atk? How? Or is this outdated info?

Another important question, maybe a lil off-topic: how to get PWM fan control to work? After a lot of googling and seaching here, all the proposed solutions using fancontrol didnt work. All i get is something like "no devices found". Ive also read that currently kernel has no drivers for PMW for current 890GX chipset. Is thisdd true? Should i just wait, or is there anything i can do?

Last but not least: **sensrors-applet RULEZ**!!!! Ive managed to add a new pannel with dozens of meters.. temps, volts, fan speed, even hdd temp! But hddtemp must run as a daemon for it to work, so... what is the "proper" way to run hddtemp as a daemon when system boots? I dont want to type **sudo hddtemp /dev/sd[a-z] -d** everytime i log in

Ill stop here, im getting waaaay off topic!

Thanks!

---

### Post by G4mick on 2011-02-15
Hello !

I have an HP pavilion dv5 on Ubuntu 10.04 LTS. He doesn't detect any sensors with "sensors" command, but "sensors-detect" tells me that I have to instal the k10temp driver.
I have downloaded k10temp.c, and I am following your instructions.

However, I have a problem when I want to create the makefile:

first step: "echo 'obj-m := k10temp.o'"
result: "obj-m := k10temp.o"
I think this first step is OK.

second step: "KDIR := /lib/modules/$(shell uname -r)/build"
result: "No command 'shell' found, did you mean:
 Command 'lshell' from package 'lshell' (universe)
 Command 'kshell' from package 'kdelibs4c2a' (universe)
 Command 'spell' from package 'spell' (universe)
 Command 'bshell' from package 'avahi-ui-utils' (universe)
shell*: commande introuvable
KDIR*: commande introuvable"

So, this second step is not working ... What can I do ?

---

### Post by HankB on 2011-02-15
> **G4mick said:**
> ...
However, I have a problem when I want to create the makefile:

first step: "echo 'obj-m := k10temp.o[COLOR="Red"]**'**[/COLOR]"
result: "obj-m := k10temp.o"
I think this first step is OK.
...

Step 3 is all one step. The single quote (apostrophe => ') on what you list on the line above should not be matched until the last line. You should just copy and paste what is in the entire panel into a terminal window and execute it. That should create a file named [FONT="Courier New"]Makefile[/FONT] with the contents between the first single quote and the last single quote. (In other words, the single quote highlighted above does not belong.)

---

### Post by jm2 on 2011-12-22
I could not execute the  insmod k10temp.ko

What I did was sudo su

and re-typed step 5 at a # and then I could do step 6.

---

### Post by evilbrent on 2012-10-31
booyah.

worked perfectly. cheers.

---

