---
title: "Thermal information and fan control"
date: 2011-03-05
forum: Hardware
---

### Post by Call_M on 2011-03-05
[B]Summary:
I cannot monitor temperature of my CPU and motherboard and I cannot control my fans. Do you have a solution or maybe similar problems? Please leave a message![/B]

Hi,
I made myself a new system. I bought a CPU with a nice cooler, a GPU with integrated cooler and my case has 3 fans. (I want to do some over clocking in the future) With all this cooling violence_ I actually want to see what the temperature of my components are and also control my fans for noise reduction. _

In my BIOS a can set a target temperature for my CPU and for the case fans I can only set one value. For my GPU I have no clue to control it. 

_In Ubuntu my fans are all running at the same speed the whole time._ Even when the system goes to sleep (and I never get it out BTW). This results in a lot of noise and probably unnecessary power consumption. 

So I searched a bit in the Ubuntu forum and I am not the only one with fan and temperature controlling problems. The last 3 days these topics came where active:

[LIST]
[*]Ubuntu not Adjusting Fan Speed [http://ubuntuforums.org/showthread.php?t=1631519](http://ubuntuforums.org/showthread.php?t=1631519)
[*]problem with lm-sensors and temperature [http://ubuntuforums.org/showthread.php?t=1699121](http://ubuntuforums.org/showthread.php?t=1699121)
[*]ATI mobility radeon 5730 HD fan is running all the time, GPU is cold [http://ubuntuforums.org/showthread.php?t=1566728](http://ubuntuforums.org/showthread.php?t=1566728)
[*]Acer Aspire 5742 i3 Intel HD - cpu fan speed [http://ubuntuforums.org/showthread.php?t=1643069&highlight=fan+speed+control](http://ubuntuforums.org/showthread.php?t=1643069&highlight=fan+speed+control)
[*]Cooling problems under Ubuntu  [http://ubuntuforums.org/showthread.php?t=1696654](http://ubuntuforums.org/showthread.php?t=1696654)
[*]dmesg: "CPU power or thermal limit exceeded" [http://ubuntuforums.org/showthread.php?t=1672407](http://ubuntuforums.org/showthread.php?t=1672407)
[/LIST]
_Non of these topics resulted in a workable solution!_

What I learned from the topics are the following commands:
```
sensors
``` the command opens lm-sensors and lists the detected sensors. For me the output is: 
> k10temp-pci-00c3
Adapter: PCI adapter
temp1:       +16.6°C  (high = +70.0°C)  This does not give a lot of answers.. Actually it brings me to my first questions:

_Q1. Is this my soundcard or my GPU? My GPU is btw installed on a PCI-E slot._
_Q2. How do I control the temperature of this component? 16 degrees is pretty cold --> is this correct?_

The next command I performed was:
```
sudo sensors-detect
``` this detects sensors. (not all btw)
The eventual summary it gave was:
> Driver `to-be-written':
  * ISA bus, address 0x290
    Chip `Nuvoton W83677HG-I Super IO Sensors' (confidence: 9)

Driver `k10temp' (autoloaded):
  * Chip `AMD Family 10h thermal sensors' (confidence: 9)

Note: there is no driver for Nuvoton W83677HG-I Super IO Sensors yet.
Check [http://www.lm-sensors.org/wiki/Devices](http://www.lm-sensors.org/wiki/Devices) for updates.

No modules to load, skipping modules configuration.

Unloading i2c-dev... OKSo there is no driver yet.. They are busy with it. But this results also give me questions:

[U]Q3: What is a Super IO Sensor and what does it detect?
Q4: Are there alternative programs for lm-sensors that work around this problem?[/U]

So now I know that I cannot read what the sensors are detecting. But why can't I control fans??
In one topic, forum member intuited, came with a possible explanation of the problems:
> **intuited said:**
> PS I'm guessing that the lack of support for temperature readings and fan control in Linux itself is because of the unsupported HECI and SMBus chips. When I do ```
$ sudo lshw | grep -A15 UNCLAIMED
``` I see those two controllers listed as unclaimed; I gather that this means that drivers are not available for them.


For me the command gave the following result:
> *-serial UNCLAIMED
             description: SMBus
             product: SBx00 SMBus Controller
             vendor: ATI Technologies Inc
             physical id: 14
             bus info: pci@0000:00:14.0
             version: 41
             width: 32 bits
             clock: 66MHz
             configuration: latency=0
        *-ide
             description: IDE interface
             product: SB700/SB800 IDE Controller
             vendor: ATI Technologies Inc
             physical id: 14.1
             bus info: pci@0000:00:14.1So no drivers for SMBus and IDE. And that leads me to my final questions:

[U]Q5: what is are SMBus and IDE controllers?
Q6: What is the fasted way to get support for these two things?

[/U]I hope someone can help me working to a solution or can give some tips. If you have/had similar problems please let me know. 

My specs are:
mobo: Asrock 890GX Extreme 3
CPU: AMD Phenom II X3 720
GPU: ATI Radeon HD 5770
CPU cooler: Cooler Master Hyper 212 Plus
Case: Cooler Master CM 690

---

### Post by An Sanct on 2011-03-05
I'm unable to have any of the temperature read, except for the SMART HDD one...

My specs
OS: Ubuntu Maverick Meerkat
mobo: ASUS P7P55D-E
CPU: Intel I5-750
GPU: ATI Radeon HD 4300/4500 series (no ventilator)

---

### Post by P . P . L . on 2011-03-05
Hi Call_M.

Quote// k10temp-pci-00c3
Adapter: PCI adapter
temp1: +16.6°C (high = +70.0°C) //EQ
__________________________________________________

This temp is from your CPU core, it could be the right reading it depends.

Hard to say without seeing other temp readings.

If  the room temp is low.

If cpu is idle & how good of a cooler you have on it.

FYI. My x6 1055T idles around 20c.

---

### Post by Call_M on 2011-03-06
> **Peter Leman said:**
> Hi Call_M.

Quote// k10temp-pci-00c3
Adapter: PCI adapter
temp1: +16.6°C (high = +70.0°C) //EQ
__________________________________________________

This temp is from your CPU core, it could be the right reading it depends.

Hard to say without seeing other temp readings.

If  the room temp is low.

If cpu is idle & how good of a cooler you have on it.

FYI. My x6 1055T idles around 20c.

Hi,

Thanks for your replay!
I am not sure about this sensor because if I check in my BIOS my CPU and mobo temp are always around 34 degrees. What I think is a bit high with a cooler that is most of the time full on. 

But if it is my CPU than I only need to find our how to control it.

---

### Post by cascade9 on 2011-03-06
Serial-UNCLAIMED is not a problem. IDE, thats because the SB850 doesnt have IDE support, so IDE is provided by an addon chip. (if you have an IDE drive, its working right? and if you dont, it doesnt matter anyway) 

Just listing the temps doesnt help much, as long as you arent overheating its the 'delta' (difference between the ambient temp and chipset/CPU temp) that matters more. 

34C is pretty good with normal room temp (about 20-25C).  

I dont know how Peter Leman is getting 20C, unless the computer lives in an icebox.

---

### Post by Yellow Pasque on 2011-03-06
> So there is no driver yet.. They are busy with it.
Unfortunately, you'll have to wait until the driver is completed before you can see all the other temps and (maybe) use the fan control. No, there is no lm-sensors alternative. Unless you can write low-level C code, you can't do anything to speed the process as a system with your particular SuperIO chip has already been donated to an lm-sensors dev.

---

### Post by Call_M on 2011-03-07
> **cascade9 said:**
> Serial-UNCLAIMED is not a problem. IDE, thats because the SB850 doesnt have IDE support, so IDE is provided by an addon chip. (if you have an IDE drive, its working right? and if you dont, it doesnt matter anyway) 

I don't have an IDE drive so yeah, nothing to worry. 

> **cascade9 said:**
> 
Just listing the temps doesnt help much, as long as you arent overheating its the 'delta' (difference between the ambient temp and chipset/CPU temp) that matters more. 

34C is pretty good with normal room temp (about 20-25C).  

I dont know how Peter Leman is getting 20C, unless the computer lives in an icebox.

You are right. But im just bothered by the fact that my fans are always at the same speed. Instead it would be nice if they would only run if needed. Seems I need to wait. 
But now I still do not know what k10temp-pci-00c3 sensor measures. 

> **Temüjin said:**
> Unfortunately, you'll have to wait until the  driver is completed before you can see all the other temps and (maybe)  use the fan control. No, there is no lm-sensors alternative. Unless you  can write low-level C code, you can't do anything to speed the process  as a system with your particular SuperIO chip has already been donated  to an lm-sensors dev.

Seems that I have to be patience. Which is very hard for me #-o.

---

### Post by cascade9 on 2011-03-07
You do have cool'n'quiet enabled in the BIOS, right? 

BTW, case fans cannot be controlled by sofware if they are hooked up to the power supply, only from the motherboard ports.

---

### Post by Call_M on 2011-03-07
> **cascade9 said:**
> You do have cool'n'quiet enabled in the BIOS, right? 

BTW, case fans cannot be controlled by sofware if they are hooked up to the power supply, only from the motherboard ports.

Yeah I have that enabled. I now enabled automatic fan control for my CPU. It will maintain a desired temperature (between 45 and 65 degrees). And I set the minimal fan speed to 1. The pc is now a lot quieter. 

My case fans are all attached to my motherboard. I can only set one value in my BIOS. They are now all set to one speed. I don't like to every time go into my BIOS to change the fan speeds when I want to play a game or run a model or just want to silently surf the Internet. 

 But maybe I can buy a separate fan controller since these things are not very expensive. My eye fell on [this one]("http://www.newegg.com/Product/Product.aspx?Item=N82E16811992005").

---

### Post by P . P . L . on 2011-03-08
> **cascade9 said:**
> Serial-UNCLAIMED is not a problem. IDE, thats because the SB850 doesnt have IDE support, so IDE is provided by an addon chip. (if you have an IDE drive, its working right? and if you dont, it doesnt matter anyway) 

Just listing the temps doesnt help much, as long as you arent overheating its the 'delta' (difference between the ambient temp and chipset/CPU temp) that matters more. 

34C is pretty good with normal room temp (about 20-25C).  

I dont know how Peter Leman is getting 20C, unless the computer lives in an icebox.

To cascade9

Well with a room temp at ~18c in the morning and all cores idling at 800mhz then why can't it be 20c?

Yes when i use it the temp goes up a bit but i have a large Zalman cooler on it.
---------------------------------------------------------

To Call_M

The BIOS can't read the cpu core temp that's why you need the k10temp module loaded and you may have to add 7 to 10c to the reading it depends on your cpu type AMD have said this.

The temp in the BIOS is from the socket under the cpu the temp doesn't change as much as the core temp from what i've seen, Like if you use cpu with a good/heavy load on it and then let it go back to idle the cores will/should cool down more then the socket or at least faster, that's why the reading in the BIOS is higher.

And if/when you get drivers for your M/B you will see the difference good luck.

---

### Post by Call_M on 2011-03-08
> **Peter Leman said:**
> To cascade9

Well with a room temp at ~18c in the morning and all cores idling at 800mhz then why can't it be 20c?

Yes when i use it the temp goes up a bit but i have a large Zalman cooler on it.
---------------------------------------------------------

To Call_M

The BIOS can't read the cpu core temp that's why you need the k10temp module loaded and you may have to add 7 to 10c to the reading it depends on your cpu type AMD have said this.

The temp in the BIOS is from the socket under the cpu the temp doesn't change as much as the core temp from what i've seen, Like if you use cpu with a good/heavy load on it and then let it go back to idle the cores will/should cool down more then the socket or at least faster, that's why the reading in the BIOS is higher.

And if/when you get drivers for your M/B you will see the difference good luck.

Do have a source where I can find how much I must add for my CPU? 

Since I set my CPU fan to automatic in the BIOS my k10temp reads tend to variate more and also the read is higher. After playing Nexuiz for a while it went up to 30 degrees (+10 is 40). I must say it didn't cool down very fast. Maybe I have to set my minimum fan speed a bit higher. 

But what I do not get is: I have 3 cores and only one core temperature...

---

### Post by cascade9 on 2011-03-09
> **Peter Leman said:**
> To cascade9

Well with a room temp at ~18c in the morning and all cores idling at 800mhz then why can't it be 20c?

Yes when i use it the temp goes up a bit but i have a large Zalman cooler on it. 

2C delta at idle? Possible, but highly unlikely. 

> **Peter Leman said:**
> The BIOS can't read the cpu core temp that's why you need the k10temp module loaded and you may have to add 7 to 10c to the reading it depends on your cpu type AMD have said this.

The temp in the BIOS is from the socket under the cpu the temp doesn't change as much as the core temp from what i've seen, Like if you use cpu with a good/heavy load on it and then let it go back to idle the cores will/should cool down more then the socket or at least faster, that's why the reading in the BIOS is higher.

BIOS cant read the core temp? BIOS temp is from a socket thermistor? Outdated information AFAIK. It was true, ohh, 6years ago. 

I cant speak for ALL the current setups, maybe some do still have socket thermistors.

> **Call_M said:**
>  But what I do not get is: I have 3 cores and only one core temperature...

Thats probably not 'core' temp, its 'TCase' temp. 

30-40 its not even close to where you should be concerned.....if you hit 60C, then worry.

---

### Post by Call_M on 2011-03-09
> **cascade9 said:**
> 
Thats probably not 'core' temp, its 'TCase' temp. 

30-40 its not even close to where you should be concerned.....if you hit 60C, then worry.

So there is one sensor that measures something.. But what that's not clear. 

I now already had a few times that I played Nexus or OpenArena (Yes gaming on Linux is great and highly addictive). After a while the game ends in a freeze. I restart, and after 10-20 minutes an other freeze. Restart and again a freeze. Then I go to my BIOS and put al my fans and CPU fan on FULL ON and the freezes are gone. 

Not anywhere in Ubuntu I can see if the freezes where caused by maybe to much heat.. I know there could be tonnes of reasons why the OS could freeze, maybe my hardware is broken or whatever. 

I hoped my hardware could replace my macbook. No I first have to install that darned Windows to check if random freezes also occur. And to get a proper read of the hardware performance.

---

### Post by cascade9 on 2011-03-09
With cool'n'quiet, and 3 case fans you shouldnt be overheating. 

Drivers maybe. Tried getting the newest ATI/AMD GPU drivers? They are much improved from all I've heard.

---

### Post by Call_M on 2011-03-09
> **cascade9 said:**
> 

Drivers maybe. Tried getting the newest ATI/AMD GPU drivers? They are much improved from all I've heard.

Yeah I also do not think I'm overheating. 

I have the latest ati drivers installed. 

I tried to get a temperature read from the GPU but it does not seem to work. (I already posted this in [http://ubuntuforums.org/showthread.php?t=1669087](http://ubuntuforums.org/showthread.php?t=1669087) ) 

I'm working on it at the moment. But the temperatuur command gives me:

[HTML]No layout section was found in the file: '/etc/X11/xorg.conf'.
Please run 'aticonfig --initial' first or modify your configurationfile manually and run aticonfig again.
aticonfig: parsing the command-line failed. 			 		[/HTML]

Do you have suggestions?

---

### Post by cascade9 on 2011-03-09
Which 'latest drivers'?. The ones ubuntu gives you from jockey-gtk?

---

### Post by Call_M on 2011-03-09
The proprietary driver. Fglrx is installed together with ATI Catalyst Control Centre. 

But I now have a temperature read for my GPU. 

I had to run:
```
sudo aticonfig --initial -f
```Did a restart and now 

```
aticonfig --adapter=0 --od-gettemperature

```Gives:

> Adapter 0 - ATI Radeon HD 5700 Series
            Sensor 0: Temperature - 33.50 C
And the fan command:
```
aticonfig --pplib-cmd "get fanspeed 0"

```> Fan speed query: 
Query Index: 0, Speed in percent
Result: Fan Speed: 35%So that seems to work now. Now I would like to see these reads also in lm-sensors.

---

### Post by Call_M on 2011-03-09
Meanwhile I also figured out that getting a temperature read from my hard-disk I needed to enable S.M.A.R.T in my BIOS. 

With the command 

```
sudo hddtemp /dev/[name of hdd] 
```It gave me a read for my Samsung spinpoint drive but for my intel postville x25-m it says:

> WARNING: Drive /dev/sdf doesn't seem to have a temperature sensor.
WARNING: This doesn't mean it hasn't got one.
WARNING: If you are sure it has one, please contact me (hddtemp@guzu.net).
WARNING: See --help, --debug and --drivebase options.
/dev/sdf: INTEL SSDSA2M080G2GC:  no sensor
I do not know where I can find if the drive has a sensor.

BTW temp reads do not show up in the sensor-applet and in lm-sensors

---

### Post by Yellow Pasque on 2011-03-09
Assuming you have hddtemp installed, you may just need to configure the sensors-applet to display the temp of the Spinpoint. Not sure if SSD;s have temp sensors. As for the GPU temp, I don't think the aticonfig output is compatible with the standard sensors, but don't quote me on that. BTW, open-source GPU drivers temp sensing is working nicely in Natty on my RadeonHD4550. Relevant part of sensors:
```
radeon-pci-0100
Adapter: PCI adapter
temp1:       +48.5°C 
```

---

### Post by Call_M on 2011-03-09
> **Temüjin said:**
> Assuming you have hddtemp installed, you may just need to configure the sensors-applet to display the temp of the Spinpoint. Not sure if SSD;s have temp sensors. As for the GPU temp, I don't think the aticonfig output is compatible with the standard sensors, but don't quote me on that. BTW, open-source GPU drivers temp sensing is working nicely in Natty on my RadeonHD4550. Relevant part of sensors:
```
radeon-pci-0100
Adapter: PCI adapter
temp1:       +48.5°C 
```

Thanks for your replay. 
Yeah I have hddtemp installed. I already tried to restart, reinstall and killall sensors-applet, but hddtemp does not seem to appear in the sensor list. Or is there an other way to configure the sensors-applet?

In [this]("http://ubuntuforums.org/showthread.php?t=952374") forum someone states that I need to compile the sensors-applet from source to enable the GPU read. But I do not know how this works.

---

### Post by Yellow Pasque on 2011-03-09
Something like this:
```
cd ~/; mkdir senseapp; cd senseapp
wget http://downloads.sourceforge.net/sensors-applet/sensors-applet-2.2.7.tar.gz
tar xzf sensors-applet-2.2.7.tar.gz
sudo apt-get build-dep sensors-applet
cd sensors-applet-2.2.7
debuild -i -us -uc -b
cd ..
sudo dpkg -i *.deb
```

The build-dep command should get most of the dependencies. If debuild bugs you about missing dependencies, install them with apt-get or synaptic.

---

### Post by Call_M on 2011-03-09
> **Temüjin said:**
> Something like this:
```
cd ~/; mkdir senseapp; cd senseapp
wget http://downloads.sourceforge.net/sensors-applet/sensors-applet-2.2.7.tar.gz
tar xzf sensors-applet-2.2.7.tar.gz
sudo apt-get build-dep sensors-applet
cd sensors-applet-2.2.7
debuild -i -us -uc -b
cd ..
sudo dpkg -i *.deb
```The build-dep command should get most of the dependencies. If debuild bugs you about missing dependencies, install them with apt-get or synaptic.

Thanks for your replay

However after sudo apt-get build-dep sensors-applet  I get something (because I had to translate)like 
E: cannot find source package for sensors-applet

---

### Post by Yellow Pasque on 2011-03-09
Oh, you may have to enable source repositories in synaptic (Settings -> Repositories, check source code box, reload or apt-get update)

---

### Post by Call_M on 2011-03-09
> **Temüjin said:**
> Oh, you may have to enable source repositories in synaptic (Settings -> Repositories, check source code box, reload or apt-get update)

I think almost there.. I had to install some other thing but get error after:

 debuild -i -us -uc -b

debuild: fatal error at line 627:
cannot find readable debian/changelog anywhere!
Are you in the source code tree?

and then after sudo dpkg -i *.deb
it gives some 
dpkg: [error message] *.deb (--install):
cannot approach archive: file or folder does not exist
[Error message]:
 *.deb

---

### Post by Yellow Pasque on 2011-03-09
You are in the sensors-applet-2.2.7 directory, right?

---

### Post by Call_M on 2011-03-09
> **Temüjin said:**
> You are in the sensors-applet-2.2.7 directory, right?

yes:

~/senseapp/sensors-applet-2.2.7 $ debuild -i -us -uc -b
debuild: fatal error at line 627:
cannot find readable debian/changelog anywhere!
Are you in the source code tree?

---

### Post by Yellow Pasque on 2011-03-09
Does dch command open the changelog?
```
dch
```

---

### Post by Call_M on 2011-03-09
No doesn't work: 

~/senseapp/sensors-applet-2.2.7 $ dch
dch: fatal error at line 478:
Cannot find debian/changelog anywhere!
Are you in the source code tree?
(You could use --create if you wish to create this file.)

if I do dch --create then I get:

~/senseapp/sensors-applet-2.2.7 $ dch --create
dch: fatal error at line 500:
Cannot find debian directory!
Are you in the correct directory?

---

### Post by Yellow Pasque on 2011-03-09
I had a debian dir, I'm not sure where it came from? Anyway, you can skip building .deb packages
```
./configure --prefix=/usr
make
sudo make install
```

---

### Post by Call_M on 2011-03-10
> **Temüjin said:**
> I had a debian dir, I'm not sure where it came from? Anyway, you can skip building .deb packages
```
./configure --prefix=/usr
make
sudo make install
```

(partly) succes! I also had to install a some requirements: [http://sensors-applet.sourceforge.net/index.php?content=requirements](http://sensors-applet.sourceforge.net/index.php?content=requirements)

I have now the following sensors:
i2c-sys --> I don't know what it is
aticonfig --> my GPU!

The k10temp-pci-00c3 sensor is gone however.
hddtemp is also not showing. In the requirements it says I need to run hddtemp as a daemon. 

So (after install) I did:
```
hddtemp -d /dev/sd[af]
```
But nothing came up in the sensors-applet also not after a restart. 
Do you think a re-install will help?

Next question is where did I install the sensors-applet? I have it now on my bar but if I open synaptic it says it is not installed.

---

### Post by Call_M on 2011-03-10
> 
hddtemp is also not showing. In the requirements it says I need to run hddtemp as a daemon. 

So (after install) I did:
```
hddtemp -d /dev/sd[af]
```But nothing came up in the sensors-applet also not after a restart. 
Do you think a re-install will help?

Next question is where did I install the sensors-applet? I have it now on my bar but if I open synaptic it says it is not installed.

I now first ran:
```
hddtemp -d /dev/sd[af]
``` 
(because I have an sda and a sdf drive)

then installed the sensors-applet and did a new install. 

And now the temp of my samsung drive is also showing in the sensors-applet. The Intel drive is not showing up.

I am going to check now how I can get the k10 back. 

Now I have to wait until I can properly read my core temps and look for a trick to control my fans for a nice and quiet system.

---

### Post by cascade9 on 2011-03-10
> **Call_M said:**
> The proprietary driver. Fglrx is installed together with ATI Catalyst Control Centre. 

To be more exact, I meant 'did you install the drivers with jockey-gtk' (system-> administration...etc)? 

If you've got the drivers with jockey, they aren't that new. The newer versions of the closed ATI drivers are more stable from what I've heard.

---

### Post by Call_M on 2011-03-10
> **cascade9 said:**
> To be more exact, I meant 'did you install the drivers with jockey-gtk' (system-> administration...etc)? 

If you've got the drivers with jockey, they aren't that new. The newer versions of the closed ATI drivers are more stable from what I've heard.

Hi cascade,

I tried to update to a newer version. As a result I totally ruined my system. I am back on my macbook now. :popcorn:

I posted my problems here: [http://ubuntuforums.org/showthread.php?t=1704275](http://ubuntuforums.org/showthread.php?t=1704275)

You have a suggestion to fix this?

---

### Post by leeshaub on 2011-03-10
i just ran a test to tell if need any drivers no drivers needed
-lee email [email]cjshaub@gmail.com[/email]

---

### Post by Call_M on 2011-03-10
> **Call_M said:**
> Hi cascade,

I tried to update to a newer version. As a result I totally ruined my system. I am back on my macbook now. :popcorn:

I posted my problems here: [http://ubuntuforums.org/showthread.php?t=1704275](http://ubuntuforums.org/showthread.php?t=1704275)

You have a suggestion to fix this?

Fixed it. Whit help of [Temüjin]("http://ubuntuforums.org/member.php?u=327594")

So no I have the latest ATI driver installed. For sure!

---

