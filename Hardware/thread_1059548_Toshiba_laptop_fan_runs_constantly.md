---
title: "Toshiba laptop fan runs constantly"
date: 2009-02-03
forum: Hardware
---

### Post by crstring on 2009-02-03
Hello Everyone... I'm a new Ubuntu user (first post) and enjoying my new Linux world immensely.  With one exception... the fan on my laptop runs at high speed constantly.  This doesn't seem right... machine is idle, no load, and fan is running full bore.  The constant noise is annoying, the constant breeze across my knees makes me cold, and at this rate I'll burn out my fan and then I'll really be stuck.

I'm running Ubuntu 8.10 Intrepid on a recently purchased Toshiba Satellite L355D laptop.  Everything works well except for the fan thing and the special keyboard function keys (like brightness control).  Volume control works OK.

I've read with interest various posts in this forum about fan and ACPI issues with Toshiba laptops, but now I'm stuck.  I've fiddled with a couple things like toshset and fnfxd, but neither worked... both complained about kernel toshiba support, but I don't know what to do about that.  I read about something called omnibook, but it sounds like that is for HP laptops, and mine is a Toshiba.

Any suggestions are truly appreciated... I'll happily post a summary of the fix if one exists.

FYI, here's the output of the acpi command (fan is blowing like crazy right now)...
```
~$ acpi -c -t
     Battery 0: Discharging, 67%, 00:02:14 remaining
     Thermal 0: ok, 28.0 degrees C
     Cooling 0: LCD 3 of 7
     Cooling 1: Processor 0 of 3
     Cooling 2: Processor 0 of 10
     Cooling 3: Fan 0 of 1
```

Here's the output of lsmod...
```
~$ lsmod
Module                  Size  Used by
ipv6                  314312  14 
af_packet              29568  4 
binfmt_misc            18700  1 
rfcomm                 51104  0 
sco                    20612  2 
bridge                 64544  0 
stp                    11268  1 bridge
bnep                   23168  2 
l2cap                  33280  6 rfcomm,bnep
bluetooth              70820  6 rfcomm,sco,bnep,l2cap
ppdev                  16904  0 
powernow_k8            23812  1 
cpufreq_userspace      12420  0 
cpufreq_ondemand       16400  1 
cpufreq_stats          14468  0 
freq_table             13568  3 powernow_k8,cpufreq_ondemand,cpufreq_stats
cpufreq_conservative    16392  0 
cpufreq_powersave      10368  0 
container              12288  0 
pci_slot               13704  0 
sbs                    22288  0 
sbshc                  14592  1 sbs
wmi                    15808  0 
iptable_filter         11520  0 
ip_tables              28176  1 iptable_filter
x_tables               31752  1 ip_tables
parport_pc             44200  0 
lp                     19588  0 
parport                50096  3 ppdev,parport_pc,lp
joydev                 20736  0 
snd_hda_intel         492336  6 
snd_pcm_oss            52608  0 
snd_mixer_oss          25088  1 snd_pcm_oss
snd_pcm                99208  2 snd_hda_intel,snd_pcm_oss
snd_seq_dummy          11524  0 
snd_seq_oss            42368  0 
snd_seq_midi           15872  0 
snd_rawmidi            34176  1 snd_seq_midi
ath_pci               109168  0 
wlan                  234784  1 ath_pci
ath_hal               225904  1 ath_pci
arc4                   10368  2 
ecb                    11520  2 
crypto_blkcipher       27780  1 ecb
snd_seq_midi_event     16768  2 snd_seq_oss,snd_seq_midi
snd_seq                67168  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
serio_raw              14596  0 
snd_timer              34320  2 snd_pcm,snd_seq
ath5k                 126852  0 
psmouse                51612  0 
evdev                  20512  9 
k8temp                 13568  0 
snd_seq_device         16404  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
i2c_piix4              17936  0 
pcspkr                 11136  0 
snd                    79432  21 snd_hda_intel,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore              16800  1 snd
snd_page_alloc         17680  2 snd_hda_intel,snd_pcm
mac80211              255416  1 ath5k
i2c_core               36128  1 i2c_piix4
led_class              13192  1 ath5k
cfg80211               52912  2 ath5k,mac80211
fglrx                2082944  63 
video                  29204  0 
output                 11776  1 video
battery                21128  0 
ac                     13448  0 
button                 15904  0 
shpchp                 42140  0 
pci_hotplug            39216  1 shpchp
ext3                  150544  1 
jbd                    66856  1 ext3
mbcache                17924  1 ext3
sr_mod                 24644  0 
cdrom                  47784  1 sr_mod
usb_storage            94784  0 
libusual               35752  1 usb_storage
sd_mod                 45864  3 
crc_t10dif             10240  1 sd_mod
sg                     45408  0 
pata_atiixp            14208  0 
pata_acpi              13568  0 
ata_generic            14212  0 
ehci_hcd               49548  0 
ohci_hcd               35100  0 
ahci                   43148  2 
usbcore               175888  5 usb_storage,libusual,ehci_hcd,ohci_hcd
libata                201312  4 pata_atiixp,pata_acpi,ata_generic,ahci
scsi_mod              183160  5 sr_mod,usb_storage,sd_mod,sg,libata
dock                   18464  1 libata
r8169                  40452  0 
mii                    14592  1 r8169
thermal                27424  0 
processor              47800  2 powernow_k8,thermal
fan                    13576  0 
fbcon                  51200  0 
tileblit               11264  1 fbcon
font                   17152  1 fbcon
bitblit                14592  1 fbcon
softcursor             10496  1 bitblit
fuse                   68288  5 

```
Thank you to all helpers!.... Rob

---

### Post by rozbarwinek on 2009-02-12
Try installing fnfxd package from ubuntu repo

---

### Post by Hachi-Roku on 2009-02-16
Hey im having almost the exact same problem. Ive done the fnfx thing but havent got far enough into it to tell if its worked or not.

I didnt notice u couldnt  use the fnF6/7 keys until i read this thread, but i did find that the stock brightness was pretty alarming!!!

You can get around the brightness part by right clicking the taskbar and adding a brightness icon to it using the "add to panel". Then you can alter brightness. It works fine and the brightness level seems to be remembered on the next boot. 



cheers

---

### Post by crstring on 2009-02-21
Hachi-Roku.... thanks for your tip about the brightness icon.... I tried it and it works nicely.  On the fan issue, no success yet... I installed and ran "fnfxd" but it complained:

fatal error: Could open /proc/acpi/toshiba/keys.
Please make sure that your kernel has enabled the Toshiba option in the ACPI section.

I have no idea how to enable this option... does it involve rebuilding the kernel?  Or is it something I specify at boot time?  Any suggestions appreciated.... Rob

---

### Post by en soph on 2009-05-03
i have the same exact problem - i'm on a toshiba satellite L300. i tried *everything*.

here's some info:

toshset
```
giacomo@Trust:~$ sudo toshset
required kernel toshiba support not enabled.
```

sensors-detect
```
giacomo@Trust:~$ sudo sensors-detect
# sensors-detect revision 5249 (2008-05-11 22:56:25 +0200)

This program will help you determine which kernel modules you need
to load to use lm_sensors most effectively. It is generally safe
and recommended to accept the default answers to all questions,
unless you know what you're doing.

We can start with probing for (PCI) I2C or SMBus adapters.
Do you want to probe now? (YES/no): 
Probing for PCI bus adapters...
Use driver `i2c-i801' for device 0000:00:1f.3: Intel ICH9

We will now try to load each adapter module in turn.
Module `i2c-i801' already loaded.
If you have undetectable or unsupported I2C/SMBus adapters, you can have
them scanned by manually loading the modules before running this script.

We are now going to do the I2C/SMBus adapter probings. Some chips may
be double detected; we choose the one with the highest confidence
value in that case.
If you found that the adapter hung after probing a certain address,
you can specify that address to remain unprobed.

Next adapter: SMBus I801 adapter at 5000 (i2c-0)
Do you want to scan it? (YES/no/selectively): 
Client found at address 0x50
Probing for `Analog Devices ADM1033'...                     No
Probing for `Analog Devices ADM1034'...                     No
Probing for `SPD EEPROM'...                                 Yes
    (confidence 8, not a hardware monitoring chip)
Probing for `EDID EEPROM'...                                No
Client found at address 0x52
Probing for `Analog Devices ADM1033'...                     No
Probing for `Analog Devices ADM1034'...                     No
Probing for `SPD EEPROM'...                                 Yes
    (confidence 8, not a hardware monitoring chip)
Probing for `EDID EEPROM'...                                No

Some chips are also accessible through the ISA I/O ports. We have to
write to arbitrary I/O ports to probe them. This is usually safe though.
Yes, you do have ISA I/O ports even if you do not have any ISA slots!
Do you want to scan the ISA I/O ports? (YES/no): 
Probing for `National Semiconductor LM78' at 0x290...       No
Probing for `National Semiconductor LM78-J' at 0x290...     No
Probing for `National Semiconductor LM79' at 0x290...       No
Probing for `Winbond W83781D' at 0x290...                   No
Probing for `Winbond W83782D' at 0x290...                   No
Probing for `IPMI BMC KCS' at 0xca0...                      No
Probing for `IPMI BMC SMIC' at 0xca8...                     No

Some Super I/O chips may also contain sensors. We have to write to
standard I/O ports to probe them. This is usually safe.
Do you want to scan for Super I/O sensors? (YES/no): 
Probing for Super-I/O at 0x2e/0x2f
Trying family `National Semiconductor'...                   Yes
Found unknown chip with ID 0xfc11
Probing for Super-I/O at 0x4e/0x4f
Trying family `National Semiconductor'...                   No
Trying family `SMSC'...                                     No
Trying family `VIA/Winbond/Fintek'...                       No
Trying family `ITE'...                                      No

Some south bridges, CPUs or memory controllers may also contain
embedded sensors. Do you want to scan for them? (YES/no): 
Silicon Integrated Systems SIS5595...                       No
VIA VT82C686 Integrated Sensors...                          No
VIA VT8231 Integrated Sensors...                            No
AMD K8 thermal sensors...                                   No
AMD K10 thermal sensors...                                  No
Intel Core family thermal sensor...                         Success!
    (driver `coretemp')
Intel AMB FB-DIMM thermal sensor...                         No

Now follows a summary of the probes I have just done.
Just press ENTER to continue: 

Driver `coretemp' (should be inserted):
  Detects correctly:
  * Chip `Intel Core family thermal sensor' (confidence: 9)

I will now generate the commands needed to load the required modules.
Just press ENTER to continue: 

To load everything that is needed, add this to /etc/modules:

#----cut here----
# Chip drivers
coretemp
#----cut here----

Do you want to add these lines automatically? (yes/NO)

```

sensors
```
giacomo@Trust:~$ sensors
acpitz-virtual-0
Adapter: Virtual device
temp1:       +46.0°C  (crit = +104.0°C)                  

coretemp-isa-0000
Adapter: ISA adapter
Core 0:      +38.0°C  (high = +85.0°C, crit = +85.0°C)  

coretemp-isa-0001
Adapter: ISA adapter
Core 1:      +38.0°C  (high = +85.0°C, crit = +85.0°C)  
```

pmwconfig
```
giacomo@Trust:/etc$ pwmconfig
This program will search your sensors for pulse width modulation (pwm)
controls, and test each one to see if it controls a fan on
your motherboard. Note that many motherboards do not have pwm
circuitry installed, even if your sensor chip supports pwm.

We will attempt to briefly stop each fan using the pwm controls.
The program will attempt to restore each fan to full speed
after testing. However, it is ** very important ** that you
physically verify that the fans have been to full speed
after the program has completed.

/usr/sbin/pwmconfig: There are no pwm-capable sensor modules installed

```

modprobe
```
giacomo@Trust:~$ sudo modprobe toshiba_acpi 
FATAL: Error inserting toshiba_acpi (/lib/modules/2.6.28-11-generic/kernel/drivers/acpi/toshiba_acpi.ko): No such device
```

40-50 minutes after the boot, the fans start running, and they won't stop, even if i'm doing nothing, even if the computer is _really_ cold!  usually i have to reboot for them to stop.

can somebody help me?

---

### Post by ColdFusionEESG on 2009-05-14
Toshiba A300

Jaunty

Same issue reported when trying to modprobe toshiba-acpi and when trying to run fnfxd.

Still investigating, but sure is odd (and annoying).

Cheers

---

### Post by davidmohammed on 2009-05-15
>  I read about something called omnibook, but it sounds like that is for HP laptops, and mine is a Toshiba.

The omnibook module is for both Toshiba's and HP Laptops - give it a try - it works for my Toshiba Satellite Pro A30

- try this [link]("http://ubuntuforums.org/showthread.php?t=316358") for installation instructions

---

### Post by Hachi-Roku on 2009-05-16
hmm. I tried a solution and it turned the fan off permanently.

so ive deleted what i did, and now think.... id rather replace the fan in time rather than cook the poor thing!

J

---

### Post by Hachi-Roku on 2009-09-03
hey guys. any luck with fixes?

ive upgraded to jaunty and now have the opposite problem of the fan not switching on at all!!

tried gkrellm, and using lm sensors only semi well.

some outputs:



not sure how to intereret this first output. thermal comes up as 0!!!! wtf

acpi -t -c
```
 
     Battery 0: Full, 100%
     Thermal 0: ok, 0.0 degrees C
     Cooling 0: LCD 0 of 7
     Cooling 1: Processor 0 of 10
     Cooling 2: Processor 0 of 10
     Cooling 3: Fan 1 of 1

```


sensors
```
acpitz-virtual-0
Adapter: Virtual device
temp1:        +0.0°C  (crit = +106.0°C)                  

coretemp-isa-0000
Adapter: ISA adapter
Core 0:      +30.0°C  (high = +100.0°C, crit = +100.0°C)  

coretemp-isa-0001
Adapter: ISA adapter
Core 1:      +31.0°C  (high = +100.0°C, crit = +100.0°C)
```


not really sure what to do now :(

any help appreciated.

---

### Post by sergiom99 on 2009-09-03
I would start by compiling my own DSDT file. Its easy and it helped a lot in mine. It now runs cooler and quieter. Read the whole thread:
[http://ubuntuforums.org/showthread.php?t=1036051](http://ubuntuforums.org/showthread.php?t=1036051)

---

### Post by Sethun on 2009-09-04
I just followed this thread: [http://ubuntuforums.org/showthread.php?t=1232887&highlight=Laptop+fan](http://ubuntuforums.org/showthread.php?t=1232887&highlight=Laptop+fan) and it seems to be working properly, I had the same issues with my fan on my system. Hope it helps :]

---

### Post by Pirolocito on 2009-09-06
Well i had the same problem on a toshiba a300-1rw. I solved it by adding the following to /boot/grub/menu.lst

On the 1st Kernel line add "*acpi_osi="Linux"*" so it look something like:

kernel		/boot/vmlinuz-2.6.28-15-generic root=UUID=ca8d6106-b54d-4f4c-a27b-aba3584dcc8b ro quiet splash acpi_osi="Linux"

Note that all that numbers are specific to my hardware, in your pc it should be different

Best regards

[http://linuxmadeasy.blogspot.com/](http://linuxmadeasy.blogspot.com/)

---

### Post by Cuba71 on 2009-09-23
Suddenly, my Toshiba Satellite A135-S4527, running Jaunty 9.04, runs with the fan at hight speed. This started happening yesterday.

Interesting enough is the fact that it runs normal under Vista, Jaunty 9.04 LiveCD and Karmic 9.10 Alpha 6 LiveCD

I haven't installed anything other that the regular Ubuntu Jaunty updates.

Any ideas?

I tried the acpi_osi="Linux" suggestion, and didn't make any difference

```

title		Ubuntu 9.04, kernel 2.6.28-15-generic
root		()/ubuntu/disks
kernel		/boot/vmlinuz-2.6.28-15-generic root=UUID=EC52458E52455F08 loop=/ubuntu/disks/root.disk ro quiet splash acpi_osi="Linux"
initrd		/boot/initrd.img-2.6.28-15-generic 

```

---

### Post by BitJunkie on 2009-09-23
> **Pirolocito said:**
> Well i had the same problem on a toshiba a300-1rw. I solved it by adding the following to /boot/grub/menu.lst

On the 1st Kernel line add "*acpi_osi="Linux"*" so it look something like:

kernel        /boot/vmlinuz-2.6.28-15-generic root=UUID=ca8d6106-b54d-4f4c-a27b-aba3584dcc8b ro quiet splash acpi_osi="Linux"

Note that all that numbers are specific to my hardware, in your pc it should be different

Best regards

I had a similar problem on my Toshiba Satellite L505 a few weeks ago. The modification above fixed my problem.

---

### Post by Cuba71 on 2009-09-23
I tried the acpi_osi="Linux" fix and didn't work.

What's surprising, that I've been running Jaunty 9.4 for 6 months without any problems, a now, since yesterday, the fans is running not stop.

It doesn't happen with the LiveCD or Windows Vista.

Go figure

---

### Post by mkwa on 2009-10-03
I have had a Toshiba laptop running Linux for 3 years. My fan does not run nonstop, but now it seems to run more often than it did 3 years ago. I think that is because of the dust in the heat sink.

---

### Post by davesmith on 2009-10-05
Toshiba notebooks are notorious for having overheating issues. The fans suck air in at the bottom of the casing and blow it over the heatsink vanes from the inside. Unless you run your m/c in a cleanroom this will deposit dust and crapite on them and eventually clog them up. 
 
Tosh hard-wire a temperature sensor in the CPU, this changes the fan speed incrementally and cools it down acording to the CPU heat output. Until the h/s vanes are so clogged it won't cool properly that is, then the m/c will suddenly shut itself down to prevent damage.
 
Here is a simple solution. Turn the m/c off completely. Get a can of air and a vacuum cleaner. Put the vacuum cleaner nozzle up against the fan covers and switch the suction on. This will get the fans running in reverse, then blow air using the can's thin tube through the rear casing slots over the heatsink vanes. With a bit of luck the accumulated dust will detach and get sucked out. Be carefull not to contact the vanes with the thin tube.
 
If the dust is well and truly caked on, more drastic means are called for. This procedure will invalidate your guarantee, be carefull....!
 
With the m/c switched off, unscrew the base plate cover over the CPU and expose the heatsink etc from the inside. Very carefully blow air over the dust mat and dislodge it, gently use a fine paintbrush if necessary. Suck the dust out. Then replace the cover. Boot up, and hope for the best!
 
 
Good luck:)

---

### Post by voidzero on 2009-10-16
I'm having this exact same problem: fan speeding up is much more common in Linux than Windows. I checked, but my fan is very clean! So something else must be up. Have you some more suggestions perhaps, because the bootloader line acpi_osi also does not work. Thanks!

---

### Post by davesmith on 2009-10-18
Its not the fans that have to be clean, its the vanes on the heatsink that sits on the big cpu chip. The hotter the cpu gets, the more air gets blown over the vanes and the more dust gets trapped. This can severely reduce the cooling efficiency so the fans run longer/faster......

With most tosh notebooks, you can see the back of the vanes through the vent slots at the rear of the m/c. The dust collects on the inside of the cooling vanes not on the outside, visible bits. Thats why you blow the canned air from the back to loosen it.

---

### Post by ex-windowuser on 2009-10-22
I'm new to Ubuntu, and I am having the same problem.  Can some please write up a step by step method on how to do the fix.  Like I said I am a newbie and very new to Ubuntu.  I am running the 64 bit version.  thnks.

---

### Post by en soph on 2009-10-28
just wanted to say that karmic fixed the problem :D

---

### Post by Juno Eclipse on 2009-11-01
Karmic did NOT fix this problem for me...
I have a Toshiba L505-10P

---

### Post by Juno Eclipse on 2009-11-11
Up :D

---

### Post by snblitz on 2010-01-01
I have the same problem with a Toshiba L305D except that the fan worked correctly under 8.10 but works incorrectly in 9.10.

As of the upgrade to 9.10 the fan starts off after a power up off.
Then it eventually decides to turn on full speed and never turn off.

---

### Post by SanguineIllusion on 2010-01-26
> **snblitz said:**
> I have the same problem with a Toshiba L305D except that the fan worked correctly under 8.10 but works incorrectly in 9.10.

As of the upgrade to 9.10 the fan starts off after a power up off.
Then it eventually decides to turn on full speed and never turn off.

Same thing for me. It doesn't seem too unreasonable request that my laptop both be able to suspend and not only engage the fan once the CPU reaches a critical temperature :(

---

### Post by Juno Eclipse on 2010-01-27
Actually I found a solution : to install fglrx driver. PowerPlay is needed to reduce gpu clock frequency on demand and it is not supported in open source driver yet...

---

### Post by cbecker78 on 2010-03-18
> **Juno Eclipse said:**
> Actually I found a solution : to install fglrx driver. PowerPlay is needed to reduce gpu clock frequency on demand and it is not supported in open source driver yet...

Hi, I have an open post on a similar issue with a satellite L505.  Could you expand on the fglrx driver? What is it and How would I go about installing it?  Someone on the [bug report ]("https://bugs.launchpad.net/ubuntu/+source/acpi/+bug/321578?comments=all")said something about powerplay too...  Seems something to do with amd... would this not apply to intel CPU systems?

Edit:  Ok, after digging around, it seems the powerplay and ATI bit apply to the specific AMD cpu/gpu chip, and will not help at all if you are running a intel processor like me.  I'm really starting to hate toshiba.

---

### Post by JoaoMachado on 2010-03-24
It's not Toshiba, my HP G60 with Intel Core2 is doing the same thing. I have narrowed the problem to the coretemp module, actually the moduled loads just fine but there is no reference to in to the /etc/sensors3.conf file...I can't find anything on why that is?

---

### Post by debian_andy on 2010-03-26
acpi_osi="Linux" works fine on Satellite L300 with the latest kernel 2.6.31-20-generic

---

### Post by debian_andy on 2010-03-27
> **Juno Eclipse said:**
> Actually I found a solution : to install fglrx driver. PowerPlay is needed to reduce gpu clock frequency on demand and it is not supported in open source driver yet...

Does your fan work or is it just that the temperature of the CPU is kept lower by reducing the clock frequency?

---

### Post by cbecker78 on 2010-03-30
> **JoaoMachado said:**
> It's not Toshiba, my HP G60 with Intel Core2 is doing the same thing. I have narrowed the problem to the coretemp module, actually the moduled loads just fine but there is no reference to in to the /etc/sensors3.conf file...I can't find anything on why that is?

Yep, when I check my message logs, it says something like "coretemp module loaded, no driver found" for every time I boot (been a while since i looked, but its something like that).

---

### Post by DougZ on 2010-05-19
Have we come up with any fix for this?

Just (re)installed Lucid on my Toshiba Tecra S10.  The fan goes constantly full out and the machine runs HOT!!!

Tried installing the sensor applet (don't have exact package names in front of me) and told me core temp was 104 degrees C.  Yikes!!!

Dual booting into XP (where I type this from) the fan is blissfully quiet and the core temp is a comfortable 54 degrees. (Cpu 0: 45, Cpu 1: 46)  What a difference!

This just isn't usable as is.  Might get brave and try a previous release of Ubuntu and see if issue is still there.  Suspect it will be.


EDIT: Adding the line **acpi_osi="Linux"** at boot solved the issue for me.  Now running at about 50 C idle.

---

