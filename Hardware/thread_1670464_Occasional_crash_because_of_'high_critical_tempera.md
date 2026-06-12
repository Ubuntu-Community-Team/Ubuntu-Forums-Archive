---
title: "Occasional crash because of 'high critical temperature'"
date: 2011-01-19
forum: Hardware
---

### Post by BKbroila on 2011-01-19
Alright, this has happened to me twice now, and it's worrying me.

While doing minimal memory-using processes, my laptop has crashed. I can't remember what I was doing during the first crash, but during the 2nd crash, I was doing homework online and listening to some music. So only Firefox and Rhythmbox were running.

Anyways, after restarting (or booting up) again, when I went into Ubuntu, the first screen that came up after my Burg startup page was black with a statement saying something along the lines of, '######## reached high critical temperature of 104.0 Celsius.'

What's going on? I feel like Ubuntu is a very high-power OS; my laptop sounds louder than when I run Win7, much louder.

Is there a way to see an event viewer or something, to possibly see what went wrong?

---

### Post by slooksterpsv on 2011-01-19
Each computer is different, with OpenSuSE, my laptop, doing nothing, would overheat past 95 C, and shut itself down.

In ubuntu in the terminal, I run the program: sensors

Which shows:
```

acpitz-virtual-0
Adapter: Virtual device
temp1:       +53.0°C  (crit = +95.0°C)                  
temp2:       +48.0°C  (crit = +95.0°C)                  

k10temp-pci-00c3
Adapter: PCI adapter
temp1:       +56.0°C  (high = +70.0°C)   

```

So my temp1 and temp2 are way low, but those if they get past 95 the OS knows to shut it down.

Umm... maybe someone has some more insight on what you could do, but my only guess to help resolve the overheating problem is making sure your computer is well ventilated, doesn't have dust blocking air-vents, and not running cpu intensive items in the background. (Check top and see if anything runs over 75% constantly, e.g. Xorg or that - flash causes my computer to overheat quite a bit too)

Use AdBlock to block ads, especially flash ads that may use more CPU. Use flashblock and block flash elements on pages you go to that you don't need (e.g. Ads).

The only other recommendation is to try another distro.

---

### Post by skion76 on 2011-01-19
We're suddenly seeing random crashes on both a MacBookPro6,2 and a Sony Vaio here too... both run Intel graphics on Maverick, but not sure whether that's it. Crashes happen with the stock kernels, as well as with 2.3.36 from the kernel PPA.

---

### Post by gradinaruvasile on 2011-01-19
> **skion76 said:**
> We're suddenly seeing random crashes on both a MacBookPro6,2 and a Sony Vaio here too... both run Intel graphics on Maverick, but not sure whether that's it. Crashes happen with the stock kernels, as well as with 2.3.36 from the kernel PPA.

Check the temperatures with "sudo sensors".

---

### Post by Laysan_A on 2011-01-19
Man, your system should never overheat. I lost a processor to overheating on our old I8000. The processor, a PIII, 850MHz copperhead, was very resilient, but without a running system monitor, I had no idea what was going on when it would just suddenly stop and go dark. After a time, the crashes became more frequent, until I finally couldn't keep the computer on for more than a few minutes. Then it wouldn't even finish booting.

Eventually I bought a used processor for it on ebay, and when I opened the case I discovered that the heat sink had sprung a leak and most of the anti-freeze had drained from it. If yours is overheating, you should definitely consider that it could be something mechanical.

Getting into the habit of running htop, and always having a temp. monitor on your desktop would be my first steps. If you have no persistent high-resources processes that coincide with the rises in temp., I would strongly suggest either opening it up yourself, or taking it somewhere and having it looked at. New fans and heat sinks are a lot cheaper than a new processor (I'm assuming it's your processor - if it;s your gpu or hd, I hope you have a warranty).

You might also want to consider finding out exactly what chip (or  component) is involved and going to the manufacturer's site to see  exactly what the maximum allowable temperature is, and either monitor it  yourself, or reset the critical temperature in ubuntu for system  shutdown (I have absolutely no idea how to do that). I do know that both  gkrellm and cairo-dock have the ability to set alarms for some temps, but I wouldn't recommend using gkrellm right now unless you [compile it yourself ]("https://bugs.launchpad.net/ubuntu/+source/gkrellm/+bug/688944"). 

Okay, I just reread your original post. Your laptop may sound "much louder" in windows because it's operating as it should in windows, and not in ubuntu. The noise is your fans, of course, and they, together with your heat sink are responsible for cooling your components. If the fans are not working as they should (and it sounds as if they're not), your machine will overheat. 

Some motherboards have the capacity for manual fan speed adjustment. You can run sensors-detect, followed by pwmconfig ([see here](http://ubuntuforums.org/showthread.php?t=42737)) to see if yours does. If it does, you'll still need to find an applet or program that will actually do it, but that shouldn't be too hard. You might want to have a glance at the [lm-sensors configuration thread]("http://ubuntuforums.org/showthread.php?t=2780").

One little tid-bit about the fans: They're very easy to damage, so be careful when you clean around them. If you do any blowing or vacuuming, make sure you don't over-speed them, by gently holding the blades stationary as you do it (computer off).

Good luck with this. There's nothing fun about losing a computer to temperature damage.

---

### Post by BKbroila on 2011-01-22
I'm still curious as to why my laptop overheats, or thinks it's overheating when it's running Ubuntu but not when in Win7. 

Because of the problem, I've been in Win7 a lot more recently. Is there any way to open some Windows-equivalent of Task Manager and see if there are odd processes running in the background?

---

### Post by Yellow Pasque on 2011-01-22
```
sudo apt-get install htop
htop
```
104C is extremely hot and dangerous to a CPU. If that's the actual temp and you keep overheating it, your CPU won't last long. I kind of have a feeling it's a bad sensor though. Check:
```
sudo sensors-detect
sensors
```

---

### Post by trinitydan on 2011-01-22
I know this is always the first suggested thing, but still, clean the fan.  I had overheating problems on my laptop and tried blowing out the dust, it didn't work.  I had to actually physically remove the fan on my Gateway MX6455(under the heatsink) and remove the shroud from the fan to get at the solid mass of dust that was blocking the fins on my heat sink, but by this time permanent damage was done to my chips.  :(

---

### Post by BKbroila on 2011-01-23
Alright so I ran HTOP and sensors-detect, and here are the results:

sensors-detect: 
```
# sensors-detect revision 5818 (2010-01-18 17:22:07 +0100)
# System: Dell Inc. Studio 1555
# Board: Dell Inc. 0J276M

This program will help you determine which kernel modules you need
to load to use lm_sensors most effectively. It is generally safe
and recommended to accept the default answers to all questions,
unless you know what you're doing.

Some south bridges, CPUs or memory controllers contain embedded sensors.
Do you want to scan for them? This is totally safe. (YES/no): Y
Silicon Integrated Systems SIS5595...                       No
VIA VT82C686 Integrated Sensors...                          No
VIA VT8231 Integrated Sensors...                            No
AMD K8 thermal sensors...                                   No
AMD Family 10h thermal sensors...                           No
AMD Family 11h thermal sensors...                           No
Intel Core family thermal sensor...                         Success!
    (driver `coretemp')
Intel Atom thermal sensor...                                No
Intel AMB FB-DIMM thermal sensor...                         No
VIA C7 thermal sensor...                                    No
VIA Nano thermal sensor...                                  No

Some Super I/O chips contain embedded sensors. We have to write to
standard I/O ports to probe them. This is usually safe.
Do you want to scan for Super I/O sensors? (YES/no): y
Probing for Super-I/O at 0x2e/0x2f
Trying family `National Semiconductor'...                   No
Trying family `SMSC'...                                     No
Trying family `VIA/Winbond/Nuvoton/Fintek'...               No
Trying family `ITE'...                                      No
Probing for Super-I/O at 0x4e/0x4f
Trying family `National Semiconductor'...                   Yes
Found unknown chip with ID 0x8512

Some systems (mainly servers) implement IPMI, a set of common interfaces
through which system health data may be retrieved, amongst other things.
We first try to get the information from SMBIOS. If we don't find it
there, we have to read from arbitrary I/O ports to probe for such
interfaces. This is normally safe. Do you want to scan for IPMI
interfaces? (YES/no): y
Probing for `IPMI BMC KCS' at 0xca0...                      No
Probing for `IPMI BMC SMIC' at 0xca8...                     No

Some hardware monitoring chips are accessible through the ISA I/O ports.
We have to write to arbitrary I/O ports to probe them. This is usually
safe though. Yes, you do have ISA I/O ports even if you do not have any
ISA slots! Do you want to scan the ISA I/O ports? (YES/no): y
Probing for `National Semiconductor LM78' at 0x290...       No
Probing for `National Semiconductor LM79' at 0x290...       No
Probing for `Winbond W83781D' at 0x290...                   No
Probing for `Winbond W83782D' at 0x290...                   No

Lastly, we can probe the I2C/SMBus adapters for connected hardware
monitoring devices. This is the most risky part, and while it works
reasonably well on most systems, it has been reported to cause trouble
on some systems.
Do you want to probe the I2C/SMBus adapters now? (YES/no): y
Using driver `i2c-i801' for device 0000:00:1f.3: Intel ICH9
Module i2c-i801 loaded successfully.
Module i2c-dev loaded successfully.

Next adapter: Radeon i2c bit bus VGA (i2c-0)
Do you want to scan it? (YES/no/selectively): y

Next adapter: Radeon i2c bit bus HDMI (i2c-1)
Do you want to scan it? (YES/no/selectively): y

Next adapter: Radeon i2c bit bus LVDS (i2c-2)
Do you want to scan it? (YES/no/selectively): y
Client found at address 0x50
Probing for `Analog Devices ADM1033'...                     No
Probing for `Analog Devices ADM1034'...                     No
Probing for `SPD EEPROM'...                                 No
Probing for `EDID EEPROM'...                                Yes
    (confidence 8, not a hardware monitoring chip)

Now follows a summary of the probes I have just done.
Just press ENTER to continue: 

Driver `coretemp':
  * Chip `Intel Core family thermal sensor' (confidence: 9)

To load everything that is needed, add this to /etc/modules:
#----cut here----
# Chip drivers
coretemp
#----cut here----
If you have some drivers built into your kernel, the list above will
contain too many modules. Skip the appropriate ones!

Do you want to add these lines automatically to /etc/modules? (yes/NO)

```

It asked me to add the last lines to /etc/modules, and I didn't say anything
And HTOP in the pic

---

### Post by Laysan_A on 2011-01-23
Hi,

You should probably check to see if the module is already being loaded. Run

```
lsmod
``` Look for coretemp in the list. If it doesn't show-up, you'll need to add it to /etc/modules. /etc/modules is owned by root, so you'll have to edit it with a rooted gedit. It's a graphical program, so you should use gksu instead of sudo.

```
gksu gedit
```Just add the lines specified. I'd include the commented one above, too (#____) as a reminder. You'll need to reboot to insure it works. After you're back up, run the lsmod command above again, to check that the module has been loaded.

There's something I'd like to check - run

```
lsmod
``` Look for i8k. If this module shows-up, you might want to have a look at [this page]("http://manpages.ubuntu.com/manpages/maverick/man1/i8kctl.1.html"). Also, if it shows-up, try running this: (might have to use sudo)

```
i8kctl
```In any case, also run this:

```
sensors
```You're using a dell laptop, right?

If i8k didn't show-up in your list of loaded modules, search the forums using the model of your laptop and the term "temp" or "temperature" or "sensors" and see if folks are using the i8kutils, or i8kmon to control their temps and fan speeds. What is your laptop model?

---

### Post by BKbroila on 2011-01-23
Thanks for the help so far.
 
My knowledge in Linux systems is limited, so I'm confused as to how I should add the coretemp line to /etc/modules

Should the file look like this: ```
# /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.

lp
rtc
coretemp
```

Is it just simply adding that line of coretemp?

---

### Post by Laysan_A on 2011-01-24
Yep. That should do it. You can also add a line above it (not a bad idea whenever you modify a system config. file) to identify what you did - something like #Added sensor module, or whatever you want. Just make sure each line starts with # so it's not read by the system.

What kind of computer do you have?

---

### Post by BKbroila on 2011-01-25
Alright, I edited /etc/modules, and ran Sensors in Terminal. Here's what came up:
```
acpitz-virtual-0
Adapter: Virtual device
temp1:       +39.0°C  (crit = +100.0°C)                  
temp2:       +44.0°C  (crit = +100.0°C)                  
temp3:       +67.0°C  (crit = +100.0°C)                  

coretemp-isa-0000
Adapter: ISA adapter
Core 0:      +36.0°C  (high = +105.0°C, crit = +105.0°C)  

coretemp-isa-0001
Adapter: ISA adapter
Core 1:      +34.0°C  (high = +105.0°C, crit = +105.0°C)
```And I didn't find i8k when I ran lsmod. 

I'm running a Dell Studio 1555, if that helps

----------------EDIT-------------------------------

I never thought of the Dell forums here, and I just read that some people installed binary ATI drivers. I was poking around to see my hardware, when I found that I never installed my proprietary graphics drivers.
After restarting, I don't hear my fan at all. The temperature is relatively the same (around 40 celsius), but hearing no fan makes me content. 

Still, would I need the binary drivers (whatever that means)?

---

### Post by Laysan_A on 2011-01-25
>  The temperature is relatively the same (around 40 celsius), but hearing no fan makes me content. It should be just the opposite. No fans means no cooling, and it seems your laptop model is plagued with cooling problems. My advice is to get used to the sound of the fans and learn to relish it. You may not have your laptop very long if you don't. Someone at dell should probably be placed up against a wall and shot for this one.

From what little I could glean from the dell (dell's) forums (that place has really changed - I imagine it was easier to get reliable information in the old soviet union than the dell forums these days. I didn't see any sign of the old guys who used to hang-out there, and knew just about anything you wanted to know.) Anyway,  from looking through posts on the dell forums, it seems likely it's the gpu that overheats. At least one person claimed he got his fixed by dell, but he gave no details about what it was they may've done to fix it - probably didn't know.

Yeah, it looks like your cpu temps are good (I assume that's what they are - looks about right), but that 67deg. temp is too high, for idling. I would bet that's your gpu.

I would suggest you install a system monitoring applet right away, and get used to watching it. Off-hand I can't remember the name of the gnome applet, so I suggest you use synaptic and put gnome system monitor in the search box. 

The other thing I would suggest is that you check your bios for any fan related settings and make sure none of them slow or stop your fans - nothing like cool & quiet - that is not what you need with this machine (if you want to keep it).

Oh yes, I looked around and it seems your laptop isn't supported by the i8k module, so you won't be able to use it. 

That's about all I've got. Let me know if you have any more questions. If I can, I will try to help.

Oh, you should probably install hddtemp. That will monitor your hard drive temp.

```
sudo apt-get install hddtemp
```When the set-up program asks if you want to run it as root, answer YES.

---

### Post by slooksterpsv on 2011-01-26
To run, type in:

gksudo hddtemp /dev/sda - for SATA
gksudo hddtemp /dev/hda - for IDE

---

### Post by Yellow Pasque on 2011-01-26
> **Laysan_A said:**
> My advice is to get used to the sound of the fans and learn to relish it. You may not have your laptop very long if you don't.
Bad advice. User installed ATI binary driver, which allowed GPU downvolting/clocking and quieter operation. (Similar features for open source drivers are found in newer Linux kernels.)

> Someone at dell should probably be placed up against a wall and shot for this one.
I put your username in my contacts. If I ever need someone to raise support for a misguided witch hunt, I'll PM you first.

---

### Post by Yellow Pasque on 2011-01-26
Oh, to check the temp of the GPU with binary driver:
```
aticonfig --adapter=0 --od-gettemperature
```

---

### Post by BKbroila on 2011-01-26
Actually, what I wrote was misleading...

I installed ATI proprietary drivers, if that's a big difference

---

### Post by Yellow Pasque on 2011-01-26
Same thing, and you should still check the output of the aticonfig command.

---

### Post by Laysan_A on 2011-01-26
> **Temüjin said:**
> Bad advice. User installed ATI binary driver, which allowed GPU downvolting/clocking and quieter operation. (Similar features for open source drivers are found in newer Linux kernels.)

[COLOR=RoyalBlue]Well, I hope that's enough. He had gpu speed-stepping on windows, too, but there his fans were on.
[/COLOR] 
I put your username in my contacts. If I ever need someone to raise support for a misguided witch hunt, I'll PM you first.
 
Hmm...very funny.

I've done a lot of reading about your 1550 (and it's siblings), and I have to say the picture isn't at all clear. Dell isn't talking - probably out of concern for liability, so all I've been able to find are user's reports. The unfortunate thing is that most of the folks who complain seem to be like I was, unaware of the dangers of excessive temperatures, and unaware of just what excessive might look and feel like. Most just complain that their fans are making a lot of noise. A few mention heat on the touchpad and keyboard. One guy even reported that his fan comes on and his computer immediately crashes - but claims it's not overheating. It's hard to make any real sense of so many disparate reports.

It seems almost as if some of the studio 15 and 17 hundreds operate normally, while others routinely overheat. I don't know why that might be. At first, I thought it might be the earlier ones that overheated, and the later ones that ran cool, but that didn't seem to be the case, as there were reports from 2010 that complained of overheating.

There were lots of reports of problems with the touchpad, the keyboard and the media keys. I wouldn't be at all surprised if the touchpad and keyboard problems were heat related also (the keyboard has a lot of thin plastic sheeting and rubber, which don't get along well with heat). 

While it seems most likely that the main culprit is your gpu, at least a couple people said the wireless unit is right under the touchpad, and that it gets hot. I don't know what to think about that, I've never heard of a wireless unit overheating, but interestingly, dell stopped offering built-in wireless in at least some of their studio models (probably just a marketing/price control measure - but who knows). You can always shut your wireless off to test, if you're of a mind.

I wish I had something of more substance to offer you. Perhaps you can do some of your own research and find out more than I did.

At least now you can monitor your temps in ubuntu (assuming there isn't a bad sensor, as Temüjin suggested), so you won't be caught off-guard. Most of the folks I read suggested using a cooling pad to ward-off overheating. Some suggested only using it on a hard surface and propping-up the back-end slightly to improve airflow. My advice to you about the fans still stands - depending, of course, on the readings you're getting from your sensors. It's far better, in my opinion, to keep things at a reasonable temperature, than try to cool things down once they're too hot.

---

### Post by rocthrttle on 2011-01-26
just thought i would add this:

sudo apt-get install sensors-applet
adds thermal sensors to right click add to panel menu

---

