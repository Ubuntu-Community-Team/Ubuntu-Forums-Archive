---
title: "No sensors detected in lm-sensors but Speedfan detects one sensor"
date: 2007-05-01
forum: Hardware &amp; Laptops
---

### Post by mthakur2006 on 2007-05-01
Yes thats my problem. I have a Lenovo 3000 C100 0761 D7A and Speedfan on windows detects a hard disk temperature sensor but lm-sensors doesn't detect any.
Also, does this laptop have any cpu temperature sensors at all? I have a Intel 915 GM Chipset and a Celeron M 1.5Ghz...

Any help would be appreciated with hugs and kisses if possible as this is a problem that has been bugging me for ages :)

Thanks.

---

### Post by kilou on 2007-05-09
I can't help you but I can tell you you're not alone! I have an MSI S260 laptop (P-M 750 and i915GM) and all my sensors are detected in Windows (with notebook hardware control, CPU related and also HD temp) but nothing in Ubuntu.

I followed this HowTo: [http://ubuntuforums.org/showthread.php?t=2780](http://ubuntuforums.org/showthread.php?t=2780)

When I run sensors-detect there are something detected! The following lines were added to /etc/modules:

i2c-810
eeprom

However when I run sensors I get: "No sensor detected!" :(

---

### Post by buellman on 2007-05-09
> **mthakur2006 said:**
> Yes thats my problem. I have a Lenovo 3000 C100 0761 D7A and Speedfan on windows detects a hard disk temperature sensor but lm-sensors doesn't detect any.
For hard disk temperature you need hddtemp from the repositories.

Greets. Buellman

---

### Post by mthakur2006 on 2007-05-09
> **buellman said:**
> For hard disk temperature you need hddtemp from the repositories.

Greets. Buellman

thanks, that works. but what about the cpu temperature? is it possible that my laptop (which is only 1 yr old and has intel chipsets) has no sensors?

---

### Post by kilou on 2007-05-09
If you install sensor-applet package you should be able to read the CPU and HDD temperature on Gnome panel (add hardware sensor stuff). You have a CPU temp sensor for sure, try to type **acpi -t** in the terminal and it'll display the CPU temp.

---

### Post by mthakur2006 on 2007-05-09
thanks kilou, but when i do acpi -t, i get this:

>  mtha@LENOVO:~$ acpi -t
     Battery 1: discharging, 95%, 04:14:03 remaining
No support for device type: thermal
mtha@LENOVO:~$ 


:confused: :confused: :confused:

---

### Post by tturrisi on 2007-05-09
Most laptops won't show cpu temps using lm-sensors because the mb may have "support" for sensors but the actual sensors are not on the board, or lm-snsors does not recognize the hardware sensor itself.

---

### Post by kilou on 2007-05-10
> **mthakur2006 said:**
> thanks kilou, but when i do acpi -t, i get this:



:confused: :confused: :confused:


That's weird! Do you have something in your BIOS regarding temperature monitoring etc that is disabled???? What happens if you right click Gnome panel, select "Add to panel" and choose "Hardware sensors monitors"??

---

### Post by lolwhites on 2007-05-10
Having a similar problem. I know the sensors are there because Speedfan detects them in XP. However, Xsensors in Feisty shows nothing but a tiny vertical rectangle and typing *acpi -t* returns the message *No support for device type: thermal*

---

### Post by kilou on 2007-05-10
What is the content of your /etc/modules file?

---

### Post by lolwhites on 2007-05-10
> What is the content of your /etc/modules file?

lp
psmouse
fuse

---

### Post by kilou on 2007-05-10
OK so it's probably not the problem. My etc/modules file contain the same as yours but it also has sbp2 module loaded. However this module is a serial bus protocol for storage devices so nothing related to CPU sensors.

Have you done any kind of customization on the kernel (like applying a patch or recompiling the kernel)? If Speedfan works it means it is something related to software and not to the BIOS. You may want to try to check if your kernel is configured to load all kind of sensors. Have a look at this:

[http://gentoo-wiki.com/HARDWARE_Sensors](http://gentoo-wiki.com/HARDWARE_Sensors)

*****************************************************
Linux Kernel Configuration: Device Drivers

I2C support  --->
<M> I2C support
<M>   I2C device interface
      I2C Hardware Bus support  --->
      <M> Choose the appropriate module(s) for your hardware

If you can't find the right module for your hardware, also check:

Hardware Monitoring Support --->
<M> Hardware Monitoring support
<M> Choose the appropriate module(s) for your hardware


[COLOR="Red"]**Note: Even you Find the right module, Have to check that HWMON option. portage said : lm_sensors-2.10.1 requires CONFIG_HWMON to be enabled for 2.6.14+ kernels.**[/COLOR]
*******************************************************************

---

### Post by lolwhites on 2007-05-10
In answer to your question, I haven't been anywhere near the kernel, and I'm afraid the instructions you link to just go right over my head!

---

### Post by molnarcs on 2007-05-10
Just a quick confirmation - I also have this problem. No sensors detected. This is an all-Intel laptop (local variant of the Clevo m660x series). Bit of a problem, for it would be good to know, especially for laptops, the temperature of the CPU.
```

molinari@Helios:~$ acpi -t
     Battery 1: charged, 100%
No support for device type: thermal
```

---

### Post by mthakur2006 on 2007-05-10
hi,
my bios is an Insyde SCU and doesnot show anything regarding temp.
As for speedfan, it picks up only one sensor as well and that is the hard disk one.
Any ideas?

---

### Post by kilou on 2007-05-10
Do you all have the package libsensor3 installed in Synaptics?

To look at your kernel config do the following:
- type **cd /usr/src/linux-headers-2.6.20-15-generic** (this is for Feisty, modify the kernel number for Edgy)
- type **sudo make menuconfig**. This will launch the kernel configuration screen where you can look at all the kernel settings. Try to find if you have something similar to below with the same options (you must see M at the same locations):

Device drivers --->
     I2C support --->
        <M> I2C support
        <M> I2C device interface
        I2C Hardware Bus support ---> (check that everything inside this tree has an "M")
        Miscelaneous I2C chip support ----> (check that everything inside this tree has an "M")

and

Device drivers --->
     Hardware Monitoring Support --->
             check that everything has an "M" option (except the last line about debugging) and also check thet the following is loaded with an *
             <*> Hardware Monitoring support


If this is not so you may have to recompile a kernel to have the sensor working but first check if you have the same configuration as above.

---

### Post by mthakur2006 on 2007-05-10
> **kilou said:**
> Do you all have the package libsensor3 installed in Synaptics?

yes.....though it is libsensors3? and not libsensor3? i am just checkin with you.

---

### Post by kilou on 2007-05-10
Yes that's right, I forgot the "s". I really can't understand why you cannot read the CPU temp through acpi -t command though. That's weird, you don't seem to have a fancy laptop do you?

Check if your BIOS has an option to allow the OS to use ACPI. Maybe this is disabled in your BIOS and Ubuntu cannot access ACPI information. Speedfan may work if it uses another way to read sensors although I don't really know if that is possible. Anyway double-check your BIOS for an option as such.

Also, do you have some files in /proc/acpi/thermal_zone/THRM? You should have the following files (they are empty):

-cooling_mode
-polling_frequency
-state
-temperature
-trip_points

---

### Post by kilou on 2007-05-10
Oh I forgot one thing: try **sudo modprobe thermal** and then run **acpi -t** to see if that works. Alternatively print the output of **lsmod**

---

### Post by mthakur2006 on 2007-05-10
hi kiolu,
i don't think my bios has the option for ACPI...my bios is a really basic one. I have an all-Intel Lenovo 3000 c100 laptop (see sig). Speedfan cannot find any sensors other than the hard disk ones.
Any ideas?
Thanks

---

### Post by kilou on 2007-05-10
Sorry I don't really much more about this. Print the output of lsmod so that we can compare what module is loaded on your computer.

---

### Post by mthakur2006 on 2007-05-11
>  What is your /etc/modules file? 

```
 
# /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.

lp
sbp2
p4_clockmod
fuse

# Generated by sensors-detect on Thu May 10 21:07:16 2007
# I2C adapter drivers
i2c-i801
# Chip drivers
eeprom

```

>  Post the output of lsmod 

```
 Module                  Size  Used by
aes                    28608  2 
ieee80211_crypt_ccmp     8448  2 
af_packet              23816  4 
binfmt_misc            12680  1 
rfcomm                 40856  0 
l2cap                  25728  5 rfcomm
bluetooth              55908  4 rfcomm,l2cap
ppdev                  10116  0 
i915                   24448  3 
drm                    81044  4 i915
pcc_acpi               13184  0 
dev_acpi               12292  0 
sony_acpi               6284  0 
tc1100_wmi              8068  0 
asus_acpi              17308  0 
dock                   10268  0 
video                  16388  0 
ac                      6020  0 
backlight               7040  1 asus_acpi
battery                10756  0 
container               5248  0 
cpufreq_ondemand        9228  1 
button                  8720  0 
cpufreq_conservative     8200  0 
cpufreq_userspace       5408  0 
sbs                    15652  0 
i2c_ec                  5888  1 sbs
cpufreq_powersave       2688  0 
cpufreq_stats           7360  0 
eeprom                  8336  0 
i2c_i801                9356  0 
i2c_core               22784  3 i2c_ec,eeprom,i2c_i801
fuse                   46612  3 
p4_clockmod             6692  0 
speedstep_lib           6148  1 p4_clockmod
freq_table              5792  3 cpufreq_ondemand,cpufreq_stats,p4_clockmod
sbp2                   23812  0 
parport_pc             36388  0 
lp                     12452  0 
parport                36936  3 ppdev,parport_pc,lp
joydev                 10816  0 
snd_intel8x0           34204  1 
snd_ac97_codec         98336  1 snd_intel8x0
ac97_bus                3200  1 snd_ac97_codec
snd_pcm_oss            44544  0 
snd_mixer_oss          17408  1 snd_pcm_oss
snd_pcm                79876  3 snd_intel8x0,snd_ac97_codec,snd_pcm_oss
snd_seq_dummy           4740  0 
snd_seq_oss            32896  0 
pcmcia                 39212  0 
snd_seq_midi            9600  0 
snd_rawmidi            25472  1 snd_seq_midi
snd_seq_midi_event      8448  2 snd_seq_oss,snd_seq_midi
snd_seq                52592  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              23684  2 snd_pcm,snd_seq
snd_seq_device          9100  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
ipw2200               148040  0 
snd                    54020  12 snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
ieee80211              34760  1 ipw2200
ieee80211_crypt         7040  2 ieee80211_crypt_ccmp,ieee80211
psmouse                38920  0 
serio_raw               7940  0 
hsfmc97ich             72088  0 
hsfserial              24580  1 hsfmc97ich
hsfengine            1307148  2 hsfmc97ich,hsfserial
hsfosspec             105448  4 hsfmc97ich,hsfserial,hsfengine
soundcore               8672  1 snd
sdhci                  18700  0 
mmc_core               26756  1 sdhci
yenta_socket           27532  1 
rsrc_nonstatic         14080  1 yenta_socket
pcmcia_core            40852  3 pcmcia,yenta_socket,rsrc_nonstatic
snd_page_alloc         10888  2 snd_intel8x0,snd_pcm
hsfsoar                87304  1 hsfmc97ich
intel_agp              25116  1 
agpgart                35400  3 drm,intel_agp
iTCO_wdt               11812  0 
iTCO_vendor_support     4868  1 iTCO_wdt
tsdev                   8768  0 
evdev                  11008  4 
ext3                  133128  1 
jbd                    59816  1 ext3
mbcache                 9604  1 ext3
sg                     36252  0 
sr_mod                 17060  0 
cdrom                  37664  1 sr_mod
sd_mod                 23428  4 
8139too                27648  0 
ata_generic             9092  0 
ata_piix               15492  4 
libata                125720  2 ata_generic,ata_piix
scsi_mod              142348  5 sbp2,sg,sr_mod,sd_mod,libata
ehci_hcd               34188  0 
8139cp                 25088  0 
mii                     6528  2 8139too,8139cp
ohci1394               36528  0 
ieee1394              299448  2 sbp2,ohci1394
generic                 5124  0 [permanent]
uhci_hcd               25360  0 
usbcore               134280  4 hsfosspec,ehci_hcd,uhci_hcd
thermal                14856  8 
processor              31048  1 thermal
fan                     5636  0 
fbcon                  42656  0 
tileblit                3584  1 fbcon
font                    9216  1 fbcon
bitblit                 6912  1 fbcon
softcursor              3200  1 bitblit
vesafb                  9220  0 
capability              5896  0 
commoncap               8192  1 capability

```

There is nothing in my /proc/acpi/THERMAL_ZONE (or whatever that was)
Yeah, I also did ```
 sudo modprobe thermal 
``` but the result is still the same.
I am beginning to think that this laptop doesn't have any sensors.
However, any ideas will be welcome.
Thanks for your time.

---

### Post by kilou on 2007-05-11
You seem to have all required modules but as your /proc/acpi/thermal_zone is empty then **acpi -t** or **cat /proc/acpi/thermal_zone/THRM/temperature** cannot work. However since you have troubles even with Speedfan it's more than likely an issue with your BIOS that doesn't allow access to the sensors. Have you checked your BIOS version? According to Lenovo website the latest version of your BIOS is 1.05 (the update utility seems to include the BIOS: [http://www-307.ibm.com/pc/support/site.wss/document.do?sitestyle=lenovo&lndocid=MIGR-63673](http://www-307.ibm.com/pc/support/site.wss/document.do?sitestyle=lenovo&lndocid=MIGR-63673))...but the changelog doesn't mention anything related to ACPI or BIOS changes....so maybe there is no hope :(

Can you read the cpu temp directly in the bios (like under system health or similar if that exists)????

Have you asked Lenovo support about how to display cpu temperature (in XP, don't speak about Linux yet)?

---

### Post by tturrisi on 2007-05-11
> Speedfan cannot find any sensors other than the hard disk ones.
Any ideas?
Read my earlier post.  Most laptops cannot have cpu temps monitored by lm_sensors.  This is becauise the CPU supports sensors if they are present, and the mb itself may actually have support for the sensors, but the actual sensors may not be there on the mb.  This is common to about 90% of all laptops.  They don't put sensors on the mb.  Be contented just using hddtemp.  Rule of thumb is this:  if your laptop bios has no section w/ diagnostics where you can see the cpu temps, then the sensors are not on the mb.  Second rule of thumb is this:  if you have sensors on the mb and lm_sensors cannot detect them, then lm_sensors database does not include your mb devices.  Read the lm_sensors docs: supported & unsupported devices: [http://www.lm-sensors.org/wiki/Devices](http://www.lm-sensors.org/wiki/Devices)

---

### Post by kilou on 2007-05-11
tturisi, in my situation lmsensors do not work but I can read CPU temp with acpi -t. Mtahkur2006 cannot even access acpi -t. I thought that any modern laptop had sensors because if sensors are not present how does the fan know when to start to blow to cool down the CPU when it gets too hot?

---

### Post by mthakur2006 on 2007-05-11
to be honest, i agree with kilou...no offence intended :)

---

### Post by tturrisi on 2007-05-11
> **kilou said:**
> tturisi, in my situation lmsensors do not work but I can read CPU temp with acpi -t. Mtahkur2006 cannot even access acpi -t. I thought that any modern laptop had sensors because if sensors are not present how does the fan know when to start to blow to cool down the CPU when it gets too hot?
Not all motherboards have a sensor chip.  For example, on some systems the fan just runs constantly.  On systems w/ a sensors chip, the fan can be slowed down, speeded up, stopped or started, depending upon the sensor chip driver and support for it in the operating systems.  Sensors are read via a ISA bus or the SMBus.  Some systems, esp some laptops, don't have a I2C bus interface.  Some don't have integrated sensors, they may reside elsewhere on the motherboard, utilized only by power mgmt IF the os has support for that chipset's power mgmt's capabilities. 

lm-sensors drivers' don't support all motherboard chipsets.   Even if sensors-detect does not recognize the motherboard sensors, it doesn't mean there is no sensors, it means that there is no driver for that  particular motherboard chipset.  example is my laptop which has a SiS chipset:

v240:~# acpi -t
     Battery 1: charged, 96%
No support for device type: thermal

v240:~# acpi -V
     Battery 1: charged, 96%
No support for device type: thermal
  AC Adapter 1: on-line

---

### Post by mthakur2006 on 2007-05-11
does that mean that i cannot access the sensors at all???

---

### Post by kilou on 2007-05-11
> **tturrisi said:**
> Not all motherboards have a sensor chip....Some systems, esp some laptops, don't have a I2C bus interface.

I'm no expert but I must admit I'm quite surprised that a recent Lenovo laptop doesn't come with a CPU sensor. Could be possible but a celeron runs fairly hot too and having a constant blowing fan would render battery life almost inexistant. One other thing to consider in mthakur2006 case is that sensor-detect mention that i2c-810 does exist. On my laptop I have the same: sensor-detect find i2c-810 and eeprom but even after loading of these modules lm-sensors still cannot read any temperature. However I can read the CPU temp directly from acpi -t which doesn't rely on lm-sensors but mthakur2006 can't do that for some reason. Most probably there are compatibility issues with lm-sensors and some motherboards but the CPU temp sensor should always be directly accessible with acpi -t no? Since it seems he has i2c interface (it's been detected by sensor-detect), I strongly suspect his laptop has a CPU temp sensor (I don't know but I really suspect that on a recent laptop). Then the only problem I can think of is if the BIOS doesn't allow access to acpi to other programs. This is configurable on most BIOS but maybe some don't have any option for that. Now as you said if this laptop has a CPU sensor it should be readable from the BIOS because even minimalistic BIOS would display passive information such as CPU temp if the CPU/otherboard is equipped with a sensor.

So probably the best is to check in the BIOS to see if that information is available or just ask Lenovo if their laptops are not equipped with CPU temp sensors.

If an i2c interface is detected, does it automatically means that the motherboard is equipped with sensors??

---

### Post by tturrisi on 2007-05-11
lm-sensors, a good an app as it is, is still way way behind windows hardware monitoring apps.  One cannot dare to compare them.  Lm-sensors supports less than 30% of chips made today:

[i]march 2007
[http://pcburn.com/article.php?sid=247](http://pcburn.com/article.php?sid=247)
LM Sensors just released version 2.8.5. This release brings in a few more supported chipsets and cleans up some bugs. Check under "Add Comment" for a full listing. Currently they're porting support for chipsets from the 2.4 to the 2.6 kernel tree, with 29% or so of the chipsets completed.[/i]

Realize that the above report is an earlier version of lm-sensors, but it currently only supports a small percentage of chipsets.

---

### Post by mthakur2006 on 2007-05-12
i asked lenovo about the cou temp for xp, they are yet to reply. but, an intel processor, and intel chipset, the fan somehow knows how to control itself, and still it doesn't have a sensor? i think it is a bit intriguing :confused:

---

### Post by kilou on 2007-05-12
mthakur2006, did you check if you have something called "sytem health" in the BIOS that would display CPU temp (within the BIOS)? If you have a digital camera can you post pictures of your BIOS and all its subsections?

tturrisi, lm-sensors doesn't support many interfaces for sure but to read acpi -t you don't need lm-sensors at all. On my laptop, lm-sensors doesn't work but acpi -t does work because it reads the CPU temp directly from the BIOS.

---

### Post by mthakur2006 on 2007-05-12
hi,
my system has nothing labelled health-monitor or anything and i will post pictures of it tonight, but i do rememeber that when i bought the laptop and it had windows xp and the older version of xp, speedfan wouldn't even detect the hddtemp and lm-sensors would return no chips found. after i updated the bios in january/feb, the speedfan utility found the hddtemp and lm-sensors atleast detects something. I only just realized when I was reading my diary last night, and thought this might be useful to post.
Thanks,

---

### Post by tturrisi on 2007-05-12
> On my laptop, lm-sensors doesn't work but acpi -t does work because it reads the CPU temp directly from the BIOS.
Some laptop and some desktop bios don't have support for temps or fan speeds.  I've a laptop like that.  Often, on laptops, there is no acpi driver for thermal and fan.  To verify, have a look in /proc/acpi/thermal_zone & /proc/acpi/fan.  If those dirs are empty then the bios does not support those readings or the current installed acpi does not detect the chips if they exist.  (best to type the path in Nautilus and press enter key rather than try to view the entire huge /proc dir)

> after i updated the bios in january/feb, the speedfan utility found the hddtemp and lm-sensors atleast detects something
Try replacing your existing /usr/sbin/sensors-detect with the most current sensors-detect from lm-sensors.  backup your existing sensors-detect, download the latest, change the permissions and put it in /usr/sbin/.

[click on "latest version of sensors-detect"]("http://www.lm-sensors.org/wiki/Devices")

Permissions:
Owner:  read write execute
Group:   read _____ execute
Others:  read _____ execute

additional insight:
[http://lists.lm-sensors.org/pipermail/lm-sensors/2006-July/016997.html](http://lists.lm-sensors.org/pipermail/lm-sensors/2006-July/016997.html)

---

### Post by mthakur2006 on 2007-05-12
Hi,
attached are some pics of my BIOS. sorry about the bad quality of pics, i am no expert at photography. i could not attach all the pics in one post for some reason, though. they are in my next post.
thanks.

---

### Post by mthakur2006 on 2007-05-12
hi,
here are the rest of my BIOS pics. i apologize for the bad pic quality once again.
thanks.

---

### Post by tturrisi on 2007-05-12
Those pics show that the bios has no built in hardware monitoring for cpu or fans.

---

### Post by mthakur2006 on 2007-05-13
> **tturrisi said:**
> Those pics show that the bios has no built in hardware monitoring for cpu or fans.

what does that imply? my brother has a toshiba l30-101 and its bios hasn't got this hardware monitoring thing either, but his speedfan can detect the cpu core temp....and his laptop is a lower end one. Just thought i would let you know about that.
thanks.

---

### Post by tturrisi on 2007-05-13
> what does that imply? 
It implies only that there's no bios utility to monitor the cpu & fans, that's all it implies.  It also means that the app called Speedfan has support for the mb and the mb chips, that's all.  

The Speedfan utility is capable of detecting 125 hardware monitor chips and temperature sensors, whereas lm-sensors does not yet detect that many sensors or chips YET and as lm-sensors is developed further it will have support for more sensors & chips.
[http://www.almico.com/forumsensors.php](http://www.almico.com/forumsensors.php)

I dual boot my Winbook laptop w/ XP Pro & Etch.  Lm-sensors is not useful for me because my laptop doesn't have temp chips or chips for fans.  My hard drive is SMART capable thus hddtemp can detect & report my hard drive temp.  This is good enough for me as it givems me *some* indicator of the internal temp of this latop, which I display on my desktop bg in Conky.

I downlaoded and installed Speedfan for giggles.  It detects my busses, IO Super and hard disk.  It can only report my hard drive temp and cannot report the cpu temp or the fan speed because this info (cpu temp & fan speed) is nowhere to be found in any chip on the motherboard.

On some computers, these readings (cpu temp & fan speed) are regulated by the power supply.  The power supply may have its own sensor that reads a temp from its own chip and thusly regulates the fan speed and fan timing.  I suspect my laptop has such a power supply.  Remember, laptops are designed with the least amount of hardware possible so as to reduce heat, power consumption and most of all reduce cost.  So...comp manufacturer A designs a laptop using parts made by different components manufacturers and these components manufactures build motherboards that meet the desired specs at the lowest possible price by incorporating only what is needed w/ few options and fewest features.  Desktop motherboards do not have to be concerned about available power because the power supply can be changed easily and heat is not as big an issue.

Bottom line is this:  If lm-sensors does not detect & output a laptop's cpu temp & fan speed then (1) it never will because the laptop has no sensors or chips or (2) it may in the future if & when support for the laptop chips is added.  If Speedfan detects some info and lm-sensors does not, then that means that the laptop has the necessary chips but lm-sensors does not yet support it and it may or may not support it in the future.  This is why both apps (lm-sensors & Speedfan) ask for user info reports, so the apps can be developed further and support more chips.

On my laptop, Speedfan detects and identifies devices that lm-sensors does not detect & identify.  But neither can get any cpu temp or fan speed.  This just means that Speedfan's own internal database of chipset specs is more complete than lm-sensors database.  As much as I wish my laptop had the needed sensors & chips, I know it doesn't, and thus I must be contented with only the hddtemp utility.

---

### Post by mthakur2006 on 2007-05-13
oh. thanks for that.
but an intel chipset, an all intel laptop has sensors that even speedfan can't detect...seems a bit unlikely doesn't it?

---

### Post by tturrisi on 2007-05-13
> **mthakur2006 said:**
> oh. thanks for that.
but an intel chipset, an all intel laptop has sensors that even speedfan can't detect...seems a bit unlikely doesn't it?

How do you know the laptop actually has sensors?

---

### Post by mthakur2006 on 2007-05-13
> **tturrisi said:**
> How do you know the laptop actually has sensors?

i don't but i am guessing because the fan seems to know when to start, when to go full speed, when to run at a slower speed and when to cut off...and if it's doing thos without sensors then my laptop is a living thing lolll

---

### Post by mthakur2006 on 2007-05-13
hi,
i was looking for thermal management of celeron m processors on the internet when i cam across this: [http://www.intel.com/cd/channel/reseller/asmo-na/eng/products/mobile/processors/celeron_m/technical_reference/97374.htm]("http://www.intel.com/cd/channel/reseller/asmo-na/eng/products/mobile/processors/celeron_m/technical_reference/97374.htm")

a quote from the long excerpt is here, the appropriate bit is highlited:

>  The Intel Celeron M processor has built-in power management and features for processor thermal monitoring. It incorporates two methods of monitoring die temperature, the Thermal Monitor and the thermal diode. The Thermal Monitor must be used to determine when the maximum specified processor junction temperature (Tj) has been reached. **The second method, the thermal diode, can be read by an off-die A/D converter (a thermal sensor) located on the motherboard, or a standalone measurement kit.** The thermal diode may be used to monitor the die temperature of the processor for thermal mangement or instrumentation purpose but cannot be used to indicate if the maximum junction temperature of the processor has been reached. The output of the thermal sensor connected to the thermal diode does not reflect the temperature of the hottest location on the die (Tj). The offset between the hottest location of the die (Thermal Monitor) may be characterized using the Thermal Monitor's Automatic mode activiation of thermal control circuit. This temperature offset must be taken into account when using the processor thermal diode to implement power management events. 

what do you think?

---

### Post by kilou on 2007-05-13
Nothing new but I've seen ou post on another thread. You say:

> **mthakur2006 said:**
> Hi there,
I have this laptop Lenovo 3000 C100 0761 D7A. I installed Ubuntu Dapper Drake 6.06 on it and I have noticed that the fan would mostly remain switched on. It does switch off for a few seconds and then comes on again. This problem did not happen in windows Xp. ...

To me this means that you have a sensor and for some reason Dapper gets wrong information from it so it does power the fan. I'm not sure but I don't think that a fan can be directly controlled by an OS without going through a sensor...

Have you tried other CPU information software than speedfan in XP? Did you try Notebook hardware control to see if you can get CPU temp with it in XP ([http://www.pbus-167.com/nhc/nhc.htm)?](http://www.pbus-167.com/nhc/nhc.htm)?)

---

### Post by mthakur2006 on 2007-05-13
hi,
i think the problem was due to the fact that cpu frequency scaling could not be controlled in dapper (i didn't know how). In fiesty however, i have seen that the fan actually remains switched on for longer since windows cannot control the speedstep in celeron m and so the cpu runs hotter. I will try the utility you gave me and post you the results later.
thanks for your time,
M thakur

---

### Post by tturrisi on 2007-05-14
go here in Nautilus:
/proc/acpi/thermal_zone
if that dir is empty you have no sensors detected by the version of acpi installed OR you have no sensors or chips at all on the motherboard (could be on the power supply in notebooks) OR kernel has no support yet for the sensors-chips.

---

### Post by mthakur2006 on 2007-05-14
> **tturrisi said:**
> go here in Nautilus:
/proc/acpi/thermal_zone
if that dir is empty you have no sensors detected by the version of acpi installed OR you have no sensors or chips at all on the motherboard (could be on the power supply in notebooks) OR kernel has no support yet for the sensors-chips.

yep, there's nothing in them. any other way to see the temp?

---

### Post by kaede on 2007-05-15
try install the package name gnome-applet or emifreq from synaptic :D

or u can try acpi -t from terminal

---

### Post by mthakur2006 on 2007-05-15
> **kaede said:**
> try install the package name gnome-applet or emifreq from synaptic :D

or u can try acpi -t from terminal

no offence intended, but have u read the earlier posts? if you haven't then - i have tried all that and they don't work. any other ideas? its weird because Thermal Monitor 1 (which is in all celeron m processors)  is not detected in either windows or linux (although a software hwconfig2 or sumthing (in windows) reports that thermal monitor is OKAY and nothing else. It also tells me that my mobo is a Lenovo HEL00 (manufactured by a company called DYnamic in China (no typo there).
Any ideas?

---

### Post by tturrisi on 2007-05-16
There's no doubt that your cpu does have built in sensors, as do most all newer cpus today.  However, having a sensor is only part of the equation.  The sensor must be able to communicate the information it senses.  This info must be communicated via some type of bus or channel on the motherboard.  The cpu is not directly accessed or read by software, software accesses it via system busses or other hardware "layers" of communcation channeling.

The busses or channels on the motherboard must be "activated", either by some specific bios codes or by acpi or by software drivers utilizing acpi or other kernel drivers.  However, if the bios has no codes for activating sensors or busses, then acpi or other kernel drivers won't be able to do anything.  Get the idea of trying to boot a hard disk that is not recognized by the bios as having been added to the system, it can't be done.

---

### Post by mthakur2006 on 2007-05-16
> **tturrisi said:**
> There's no doubt that your cpu does have built in sensors, as do most all newer cpus today.  However, having a sensor is only part of the equation.  The sensor must be able to communicate the information it senses.  This info must be communicated via some type of bus or channel on the motherboard.  The cpu is not directly accessed or read by software, software accesses it via system busses or other hardware "layers" of communcation channeling.

The busses or channels on the motherboard must be "activated", either by some specific bios codes or by acpi or by software drivers utilizing acpi or other kernel drivers.  However, if the bios has no codes for activating sensors or busses, then acpi or other kernel drivers won't be able to do anything.  Get the idea of trying to boot a hard disk that is not recognized by the bios as having been added to the system, it can't be done.

ohhh, get it now.
so any chance to activate it?

---

### Post by tturrisi on 2007-05-16
I really don't know how to "activate" the unactivated.  I built & installed the latest lm-sensors as a test again and it reports the existence of an unknown super IO port but shows it as inactive.  To me, this means that my motherboard has capability for using this port but it also means that this system was built the way it was because that IO port is not needed for anything.  Or it means my cpu (p4 3.02 GHz w/ HT)  has sensors but they cannot communicate with this motherboard.  I am contented to just use hddtemp...

---

### Post by kilou on 2007-05-17
mthakur2006, IMHO you should first try to read CPU temp from XP rather than from Linux to see if you can access sensors. 

Can you try this utility called mobilemeter in XP: [http://www.geocities.co.jp/SiliconValley-Oakland/8259/release/0310/mm0310.zip](http://www.geocities.co.jp/SiliconValley-Oakland/8259/release/0310/mm0310.zip)

Simply unzip the file called mobmeter.exe and run it as an administrator in XP and see if it can read any information regarding CPU temp.

---

### Post by jbernardo on 2007-05-17
The problem for me and most centrino duo laptop owners, is that we need the latest lm_sensors and the **coretemp** module.  If I use the *sensors-detect* script from [http://www.lm-sensors.org/wiki/Devices](http://www.lm-sensors.org/wiki/Devices), it finds my sensors and asks for the **coretemp** module - which is included only in kernel 2.6.22 and above, while feisty ships with 2.6.20.
So, it seems we'll have to wait for the next ubuntu release...

---

### Post by jbernardo on 2007-05-17
[http://www.debianhelp.org/node/5156](http://www.debianhelp.org/node/5156)
We need to check the bugs if this is already there, and if not open a bug so that this patch will be added to the kernel.

---

### Post by mthakur2006 on 2007-05-17
> **kilou said:**
> mthakur2006, IMHO you should first try to read CPU temp from XP rather than from Linux to see if you can access sensors. 

Can you try this utility called mobilemeter in XP: [http://www.geocities.co.jp/SiliconValley-Oakland/8259/release/0310/mm0310.zip](http://www.geocities.co.jp/SiliconValley-Oakland/8259/release/0310/mm0310.zip)

Simply unzip the file called mobmeter.exe and run it as an administrator in XP and see if it can read any information regarding CPU temp.

i would try it out but it takes me to Yahoo Japan and unfortunately, my language skills are not that good. Can you post send me the file in any other way? i would be grateful for that.
Thanks.

---

### Post by mthakur2006 on 2007-05-17
> **jbernardo said:**
> [http://www.debianhelp.org/node/5156](http://www.debianhelp.org/node/5156)
We need to check the bugs if this is already there, and if not open a bug so that this patch will be added to the kernel.

hi,
thanks for the response.

1. is core solo the same as celeron m?
2. and, how do you apply a patch?
Thanks.

EDIT: Is it possible to read sensors if it is not present in the BIOS or something?
thanks.

---

### Post by jbernardo on 2007-05-18
AFAIK, Core Solo and Celeron M are very different CPUs. But I wouldn't be surprised if they had the same interface to the internal sensors.
To apply a kernel patch you need either to build your custom kernel, or convince the ubuntu developers to release a new kernel revision with the patch already applied.

In my case I can read the sensors either in XP or in ubuntu with a custom kernel, but in the BIOS there is no system health page or any mention to the sensors.

PS: I've added bug [#115386]("https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/115386") to launchpad.

---

### Post by kilou on 2007-05-18
> **mthakur2006 said:**
> i would try it out but it takes me to Yahoo Japan and unfortunately, my language skills are not that good. Can you post send me the file in any other way? i would be grateful for that.
Thanks.

sorry I didn't see the link was broken. Go here: [http://www.geocities.co.jp/SiliconValley-Oakland/8259/](http://www.geocities.co.jp/SiliconValley-Oakland/8259/) and under the green title click on the "here" where it says "You can download latest MobileMeter from here".

---

### Post by kilou on 2007-05-18
> **mthakur2006 said:**
> hi,
thanks for the response.

1. is core solo the same as celeron m?
2. and, how do you apply a patch?
Thanks.

EDIT: Is it possible to read sensors if it is not present in the BIOS or something?
thanks.

celeron-M is quite "old" IMHO and it is supported by the kernel since it is part of the 686 family. I don't know if you can read sensors if they don't appear in the BIOS. Did you get some news from Lenovo?

---

### Post by mthakur2006 on 2007-05-18
hi,
i haven't got any news from Lenovo as of yet but what I have found out that my laptop has a Lenovo HEL00 motherboard (see my earlier post) and a Insyde ACPI BIOS (whatever that means.) I would try the kernel in a couple of days and the mobilemeter fails to find a cpu sensor either. what now?
thanks.

---

### Post by pumpum on 2007-05-21
^Bump.
Please help. :)

---

### Post by DaveRowell on 2007-05-27
mistake - sorry

---

### Post by kilou on 2007-05-27
Mtahkur2006, found this here [http://www.zd7000forums.com/viewtopic.php?t=1826&highlight=vbs](http://www.zd7000forums.com/viewtopic.php?t=1826&highlight=vbs). Try the following in XP:

Open notepad and paste the following inside:

```
-----BEGIN CODE

strComputer = "localhost"

set wbemServices = GetObject("winmgmts:\\" & strComputer & "\root\wmi")
set wbemObjectSet = wbemServices.InstancesOf("MSAcpi_ThermalZoneTemperature")

For Each wbemObject In wbemObjectSet
WScript.Echo "InstanceName : " & wbemObject.InstanceName
WScript.Echo "Current Temperature (Kelvin): " & wbemObject.CurrentTemperature / 10
WScript.echo "Current Temperature (Celcius): " & (wbemObject.CurrentTemperature / 10) - 273.15
WScript.echo "Current Temperature (Farenheit): " & ((wbemObject.CurrentTemperature / 10) * 1.8) - 459.67
WScript.Echo ""
Next


-----END CODE
```

Now save this document as temperature.vbs in C:\. Then go in the command prompt, navigate to C:\ and type "cscript temperature.vbs and post the output. If you are able to read the HDD temp in XP do so to be sure that the HDD temp is different from the temp you get with the script. The script is supposed to give the CPU temp.....

If you can get a cpu temp in XP then it means you have sensors and there is possibly a way to read them from Linux as well. But now you must first know if your laptop really has sensors so first check this with XP.

---

### Post by mthakur2006 on 2007-05-28
cheers for that kilou, i salute you for your perseverance!
i will try the script when I get back home later and post the results.
regards,
mthakur2006

---

### Post by mthakur2006 on 2007-05-28
hi,
i tried the script but it comes up with somethint 6,1: (null) and then something like 0x0000dd83
i cannot post from xp because i cannot connect to my wireless network from it for some reason.
cheers.

---

### Post by kilou on 2007-05-28
I must say that I'm quite lost then. Maybe you would get more help on a forum dedicated to Lenovo notebooks. You should probably try to post your problem here:

 [http://forum.notebookreview.com/forumdisplay.php?f=2](http://forum.notebookreview.com/forumdisplay.php?f=2)

People on notebookreview are very responsive and know a lot of issue. They have a dedicated forum for Lenovo/IBM computer. I'm afraid I can't be of more help for you but probably that people there can tell you if your computer have sensors and if it has, how to read them. They're mostly using XP but I would say it's better to look on how to get the sensors working in XP since you'll have much more people able to help you. If you can achieve to read the CPU temp from XP, then you'll know you have sensors and you'll just have to find a way to do the same in Linux.

Hope this helps

---

### Post by mthakur2006 on 2007-05-29
cheers kilou,
i will have a look at the forums.
i salute you again!

---

