---
title: "laptop temperature/fan?"
date: 2009-01-17
forum: Hardware
---

### Post by ajy0852 on 2009-01-17
Hi,

I have a Toshiba Satellite L305 laptop. The fan frequently spins up (with high CPU usage) and won't spin back down until I reboot or shut down.

I don't think acpi -V is giving me the correct temperature:

```
     Battery 0: Full, 100%
  AC Adapter 0: on-line
     Thermal 0: ok, 0.0 degrees C
     Cooling 0: LCD 0 of 7
     Cooling 1: Processor 0 of 10
     Cooling 2: Processor 0 of 10
     Cooling 3: Fan 1 of 1
```

No matter when I check, it's 0.0 degrees Celsius. I'm guessing these problems are related, but I'm kind of a newbie in this area.

Any ideas? Let me know if I should post more information. Thanks!

---

### Post by linux_tech on 2009-01-17
You can install sensors-applet to show CPU, GPU, and HD temperatures.



```




sudo apt-get install sensors-applet


```

---

### Post by ajy0852 on 2009-01-17
Thanks, but this also shows 0 degrees Celsius. It installed hddtemp as one of the dependencies, though, and I'm able to get a temperature reading on my hard drive (currently 38 degrees C, though I just started up again since I was gone for a while).

Edit: I found [this blog post]("http://www.besy.co.uk/debian/how_to_use_lmsensors_to_show_cpu_temperature_and_voltages") and followed the instructions there, it loaded the "coretemp" module for me which says my cpu is around 67-68 degrees C most of the time. My hard drive has settled at 46 degrees C. From what I've been able to find, these numbers are warm but not terrible, so I'll be OK. I don't know if this will affect the fan at all.

---

### Post by mnd on 2009-02-04
I've got a Toshiba L305-S5933 running 64-bit 8.10 and I had the same problem. After much googling, I found this fix that worked for me. Add ```
acpi_osi="Linux"
``` to the kernel boot options in grub. My fan now turns on (low speed) at about 50°C and turns off around 35°C.

---

### Post by IlSeniore on 2009-02-06
hi, 

I just bought a Satellite L305-S5921 and experience the exact same problem. (Ubuntu 8.10 32bit) 
Fan comes on when CPU usage is higher and then never turns off again. Remains at this one speed. I am totally new to Linux and am glad I got it to dual boot. Could you please tell me where I can find instructions (that I can understand and follow) to get your suggestion:
   "acpi_osi="Linux"
installed? 

Thanks!

---

### Post by mnd on 2009-02-06
There's a good GRUB HowTo at [http://help.ubuntu.com/community/GrubHowto]("http://help.ubuntu.com/community/GrubHowto"). Look at the section "Setting kernel parameters".

---

### Post by IlSeniore on 2009-02-09
> **mnd said:**
> There's a good GRUB HowTo at [http://help.ubuntu.com/community/GrubHowto]("http://help.ubuntu.com/community/GrubHowto"). Look at the section "Setting kernel parameters".

Thank you for your response. I edited the Kernel boot section, but the temperature reading is still "0.0" C So far it doesn't seem like the fan speed is controlled at all. It seems more that it remains in whatever speed it was during boot up. Any ideas how I can get the temperature to be read correctly? 
Thanks.

---

### Post by mnd on 2009-02-09
Try installing the lm-sensors package.

```
sudo apt-get install lm-sensors
```

---

### Post by IlSeniore on 2009-02-10
I installed the lm-sensors package. It also reads 0.0 degree Celsius. 
When I run this laptop using Win Vista, the fan seems to be conrolled correctly. So I believe the internal sensor is working correctly.

---

### Post by mnd on 2009-02-10
How are you checking the CPU temperatures? Try running /usr/bin/sensors .

---

### Post by IlSeniore on 2009-02-11
To check the temp. I used "acpi -V"
Result => 0.0 C

I then ran /usr/bin/sensors using the command: ./sensors from the /usr/bin dir
Result:
acpitz-virutal-0
Adapter: virtual device
temp1: +0.0 C (crit = 106.0 C)
So for some reason, Linux can't read the temp sensor correctly.

---

### Post by IlSeniore on 2009-02-12
I did a quick reply and for some reason it didn't show up, so I replied again - sorry.

 Re: laptop temperature/fan?
To check the temp. I used "acpi -V"
Result => 0.0 C

I then ran /usr/bin/sensors using the command: ./sensors from the /usr/bin dir
Result:
acpitz-virutal-0
Adapter: virtual device
temp1: +0.0 C (crit = 106.0 C)
So for some reason, Linux can't read the temp sensor correctly.

---

### Post by mnd on 2009-02-15
After installing lm-sensors, did you try running /usr/sbin/sensors-detect ? You may find that you'll have to load one or more kernel modules.

---

### Post by IlSeniore on 2009-02-23
sorry that it took me so long to reply. Thanks for your continuous help.
I ran the script you mentioned above. Now Ubuntu shows at least the Core0 and Core1 temperature. However, "CPU" and "temp1" remains at 0 degrees C. 
When executing: acpi -V I get:
...
Thermal 0: ok, 0.0 degrees C
...

When executing: sensors, I get now:
Adapter: Virtual device
temp1:  +0.0 C (crit = 106.0C)

coretemp-isa-0000
Adapter: ISA-Adapter
Core 0:   +36 C (high = 100.0 C, crit = 100.0 C)

coretemp-isa-0001
Adapter: ISA-Adapter
Core 1:   +36 C (high = 100.0 C, crit = 100.0 C)

The fan seems to be still caught in one speed. Once turned ON, it runs and remains ON.

---

### Post by harman0 on 2009-02-26
Just dropping in to let you know that I have the seemingly exact same problem with the toshiba A305-S6872 : [http://ubuntuforums.org/showthread.php?p=6807182](http://ubuntuforums.org/showthread.php?p=6807182)

---

### Post by pevans91 on 2009-03-02
Hi there all, just to let you know i have the same problem too on a Toshiba Satellite L300, at first there would be no fan at all, followed by the fan running and staying on full.

After adding the acpi line to my GRUB boot menu, the fan does seem to vary, going on and off like in vista, however i am unable to read any CPU temperature values (having followed all of the steps highlighted) and is there anyway to enable CPU scaling on the Intel Celeron Dual Core?

Thanks!

---

### Post by IlSeniore on 2009-03-05
> **mnd said:**
> After installing lm-sensors, did you try running /usr/sbin/sensors-detect ? You may find that you'll have to load one or more kernel modules.

Hi all, just wanted to report that my fan is now finally controlled by Ubuntu. Here is how it workes:

1) Install lm-sensors package:
sudo apt-get install lm-sensors

2) run /usr/sbin/sensors-detect
(This is a dialog driven program -> answer yes and it will guide you through and tell you if you have to edit settings, how and where - great tool btw!)

3) at last, add: acpi_osi="Linux" to grub kernel boot entry
   how to do this? -> see here:
[http://grumpymole.blogspot.com/2007/05/ubuntu-how-to-edit-grub-boot-parameters.htm](http://grumpymole.blogspot.com/2007/05/ubuntu-how-to-edit-grub-boot-parameters.htm)

Hope that helps you guys too. 
Big thanks to mnd! 
(My fan now not only runs lower, but also even turns all the way OFF! :-)

---

### Post by amitbk on 2009-03-10
Hi,

I have a Toshiba Satellite A305-S6898, and I share the same problem.
I followed the instructions above, and installed lmsensors and ran sensors-detect.
After I loaded the kernel module it suggested (coretemp) the temperatures of the two cores started showing in the output of `sensors`, but the CPU temp was still 0c.
I added the ```
acpi_osi="Linux"
``` line to my kernel options, but the cpu temperature stays 0c:

```
$ /usr/bin/sensors
acpitz-virtual-0
Adapter: Virtual device
temp1:        +0.0°C  (crit = +92.0°C)                  

coretemp-isa-0000
Adapter: ISA adapter
Core 0:      +52.0°C  (high = +85.0°C, crit = +85.0°C)  

coretemp-isa-0001
Adapter: ISA adapter
Core 1:      +51.0°C  (high = +85.0°C, crit = +85.0°C)
```

Something that did happen after I added the "acpi_osi" kernel option is that the key combination I used to dim the LCD's backlight (FN-F6 and FN-F7) stopped working.

Any ideas?

Attaching the output of my `lspci -vv`.

Thanks :)

(I shared most of these details on a [similar thread]("http://ubuntuforums.org/showthread.php?t=1047640"), I hope it's ok)

---

### Post by amitbk on 2009-03-22
> **IlSeniore said:**
> Hi all, just wanted to report that my fan is now finally controlled by Ubuntu. Here is how it workes:


Hi IlSeniore,
It seems I have a similar hardware and also share the fan issue.

It looks to me like we both have the same problem, only you added the 'acpi_osi="Linux"' line to the kernel params and it solved the problem for you, as when i added it, it did not solve the problem.

So I thought maybe i'd ask you if possibly you did something else that solved it?
Can you show me what is the output now of your "sensors" utility?
What did you change the kernel param to?

I hope it is ok for me asking, as I really want to solve this fan issue..

---

### Post by scottchen on 2009-03-25
Hi amitbk,

I have exactly the same problem. I have done the three steps that listed. But my fan still continuously on once it is turned on. 

Did anyone else solve this problem?

scott

---

### Post by amitbk on 2009-03-25
I didn't find any solution to this problem. I think we need to file a bug on the lm-sensors project ([http://www.lm-sensors.org/]("http://www.lm-sensors.org/")), as the core temps are identified, but this acpitz-virutal-0, which I haven't been able to figure out what it means, stays 0.
If you do file that bug, please post with the link in this thread.

---

### Post by amitbk on 2009-03-25
I think we should try and use the latest stable lm-sensors before we approach them with this issue. It might have been solved already.
I see on their website that the latest version is 3.1.0, now I use Intrepid and my version is 3.0.2. I've been trying to find a way upgrade to the latest version, but haven't succeeded in doing that so far.

---

### Post by khiraly on 2009-04-02
I have a Toshiba L300-19J model, and I share the same issue. If the fan turn on once, never stopped.

A suspend/resume fix the problem until the laptop gets hot enough to turn on the fan. Just the problem with suspend-resume that it crash 1 of ten times, not reliable at all. (under crash I mean gdm restart, and I need to login again).

I use ubuntu 9.04 alpha. With a .29 kernel (what fixes many 3D issue for me and suspend/resume started almost working)

The temperature read out is the same 0deg as everyone noticing. In toshiba forum I read, that it is maybe insideH2O bios problem.
But as linux is unsupported on this laptop (only xp and vista) they do not provide any help.

I use lm-sensors 3.0.2-2ubuntu4 package. And acpi 1.2-1ubuntu1 package.

Any more findings/solution?

---

### Post by khiraly on 2009-04-02
> **khiraly said:**
> 
Any more findings/solution?

Adding the parameter ```
acpi_osi="Linux"
``` and reboot does NOT solve the problem for me. If it starts the fan (at full speed) never stops. (No matter that the air coming out of the laptop is around 20degree (definietly cold)).


So I think the problem is present and no solution is known (to me at least).

---

### Post by amitbk on 2009-04-02
> **khiraly said:**
> In toshiba forum I read, that it is maybe insideH2O bios problem.
But as linux is unsupported on this laptop (only xp and vista) they do not provide any help.

Could you add a link to that forum discussion?

It would have been so much better if the Toshiba engineers would have checked my laptop with Ubuntu before they released it.

I spent so much time so far trying to make this laptop give me on Ubuntu what is so trivial on Vista. (hope I'm not bordering off-topic here)
[LIST=1]
[*]Making the ATI Radeon HD3700 card give some 3D support and to work with my lcd tv with a resolution of 1360x768 (using fglrx for 3d, no luck with the tv so far, I must boot to Vista each time to watch a movie)
[*]Making the sound levels as high as on Vista (followed  [http://arbitraryusefulinfo.wordpress.com/2007/10/10/configuring-headphones-for-ubuntu-704-on-a-toshiba-a135-s2356/]("http://arbitraryusefulinfo.wordpress.com/2007/10/10/configuring-headphones-for-ubuntu-704-on-a-toshiba-a135-s2356/"). The sound levels are still too low, and the granularity of the volume dial turns is still to harsh. Also now I have an issue with the headphone jack not detecting the headphones being connected, and leaving the "front" speakes' volume the same, so sound plays on both the phones and the speakers)
[*]This fan control issue, when I can't understand how the fan decides to start, and it seems the fan shares my confusion as to when it should stop.
[*]NetworkManager having troubles getting an IP from my Cisco 800 router both on "auto LAN" and on the Wireless. Vista does it just fine.[/LIST]

Those are all issues that I hoped not to have to deal with when installing an OS. Let's just say, knowing all these issues exist, I wouldn't recommend anyone that want it to "just work" to install ubuntu on this type of laptop.

---

### Post by khiraly on 2009-04-05
> **amitbk said:**
> Could you add a link to that forum discussion?


Third hit on google btw:

[http://forums.computers.toshiba-europe.com/forums/thread.jspa?threadID=42094&tstart=0](http://forums.computers.toshiba-europe.com/forums/thread.jspa?threadID=42094&tstart=0)

---

### Post by compengi on 2009-04-13
Okay Toshiba followers.. this seems like a very wide spreaded issue that struck me too. I recently bought a Toshiba L300-214 laptop and had same symptoms as described by all posts, in all forums and in all mailing lists. Whatever I tried didn't work for me. After several days of searching and trying, I finally managed to solve the issue.

Before I get into details, I would like note to all, that the fan is controlled by "ACPI". No other utility, that in all the forums is posted solved it.

Our aim is to add:

1. Kernel CPU Frequency scaling.
2. Hardware Monitoring Support into your Kernel
3. Generic Thermal sysfs driver
4. Add acpi_osi="Linux" to your grub

**Note: Some of those modules could be already installed in your Kernel, just double check if it is and skip the step.

As you are probably already guessing, you need to recompile your Kernel. How? here's the Ubuntu wiki page for it: [https://help.ubuntu.com/community/Kernel/Compile](https://help.ubuntu.com/community/Kernel/Compile) and go through "Alternate Build Method: The Old-Fashioned Debian Way" compiling process.

Now you should go through all the steps listed in that wiki to prepare your environment to kernel compilation. I won't take you through all of them as they are already clear, rather we will start from the step where you need to "make menuconfig", here's what we will do next:

**Configuring your Kernel:**

1. CPU Frequency scaling:
```
Power management and ACPI options  --->
  CPU Frequency scaling  --->
    [*] CPU Frequency scaling
      *** CPUFreq processor drivers ***
      <M>   ACPI Processor P-States driver
```

2. Hardware Monitoring Support:
```
Device Drivers  --->
  {*} Hardware Monitoring support  --->
    (Load here your CPU module.**As Module** with flag M and not *)
    (In my case)
    <M>   Intel Core (2) Duo/Solo temperature sensor
```

3. Generic Thermal sysfs driver:
```
Device Drivers  --->
  {M} Generic Thermal sysfs driver  --->
    [*]   Hardware monitoring support
```

Make sure your processor family is selected correctly:
```
Processor type and features  --->
  (In my case)
  Processor family (Core 2/newer Xeon)  --->
    ( ) Opteron/Athlon64/Hammer/K8
    ( ) Intel P4 / older Netburst based Xeon
    (X) Core 2/newer Xeon
    ( ) Generic-x86-64
```

Now you are finished with the configuration. Double <ESC><ESC> till you get out of the menu and select < Yes > to save your configuration. Continue now through the rest of the kernel compiling process as stated in the wiki.

After you finished compiling, edit your grub menu.lst and add acpi_osi="Linux" as an additional parameter to your "kernel" line. If you are still confused how to do this, check this page: [https://help.ubuntu.com/community/GrubHowto#Setting%20kernel%20parameters](https://help.ubuntu.com/community/GrubHowto#Setting%20kernel%20parameters). Now you can safely reboot for the changes to take effect.

After those steps, my fan started to work as it should. This walkaround was tested on Kernel 2.6.28-r4 as well as on 2.6.29-r1 compiled on Gentoo. Good luck!

---

### Post by Ceyx on 2009-04-18
I've had my Toshiba L300D for a while running Ubuntu 8.10 64bit, and I too noticed that my fan was off initially, then it came on and stayed on no matter what.  I followed all of the advice above, to no avail.

I looked thru the Toshiba manual for fan control, and found one reference - in power options.  I got the idea that they (Toshiba) set the fan parameters dynamically, depending on the options you choose.  Given that, in the Ubuntu Power Management options I noticed that I had everything cranked - ie no sleep, no hibernation, etc.  I reset these to go to sleep, hibernate etc after half an hour of idleness.....and guess what ?  Maybe it is just a coincidence, but there is no problem with the fan now.  I've cranked the system as much as I can, and still the fans are fine.

Perhaps in the power management, if you have the sleep functions set to "never", it disables the fan management too?  Any how, it works, thought I'd pass it along for what it is worth....

---

### Post by compengi on 2009-04-24
cool! though, you could go on standby manually using:
```
# echo mem > /sys/power/state
```
Note, that sometimes the command on some distros doesn't run through sudo. Try logging in as root in terminal and type down the command. Works perfectly and nicely.

---

### Post by juppra on 2009-05-03
Jaunty 9.04 installed on Toshiba Satellite L300-OKW, fan is either nospeed or fullspeed (& stays on until restart) - this is what worked for me:

*In a terminal*

...laptop:~$ acpi -V

*returns*
     Battery 0: Full, 100%
     Battery 0: design capacity 4000 mAh.....
  AC Adapter 0: on-line
     Thermal 0: ok, 48.0 degrees C
     Cooling 0: LCD 0 of 7
     Cooling 1: Processor 0 of 7
     Cooling 2: Fan 1 of 1

...which suggests that sensors working OK.  Maybe I was just lucky there.

*In a terminal, do this:*

...laptop:~$ cd /boot/grub
...laptop:~$ sudo gedit menu.lst

*In menu.lst, modify *
# defoptions=quiet splash
*to*
# defoptions=quiet splash acpi_osi=Linux
*then save/quit menu.lst*

*Then do this:*
...laptop:~$ sudo update-grub
*then restart computer.*

Fan seems to do its fan-thing properly now.

Sorry if this all seems a bit dumbed-down - I'm a hardware engineer, used to working with software guys who struggle with anything bigger than a **'0'** or a **'1'** :) [Heh, only kidding dudes!  Just couldn't resist lobbing one over the imaginary software/hardware wall there - hehehe! :lolflag:]

*For the record, these forums are fantastic and the care that so many take in helping others they don't know and will likely never meet is brilliant. If only we could run the whole world like that!*

---

### Post by Ceyx on 2009-05-12
Update:

Disabling ACPID in System>Admin>Services finally did the trick for me...now have fan, brightness and mute keys, all perfect.

I have a Toshiba L300D with an Insyde H20 BIOS.  I suspect that it was the different bios that prevented all the other fixes from working...they work with Phoenix or whatever but not Insyde.  

Anyhow, laughing now, I can finally hear the keyboard over the fan which is off.  Thought to pass it along.

Ciao

---

