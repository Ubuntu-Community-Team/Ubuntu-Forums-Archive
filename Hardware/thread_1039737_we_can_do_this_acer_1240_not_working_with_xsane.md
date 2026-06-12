---
title: "we can do this: acer 1240 not working with xsane"
date: 2009-01-14
forum: Hardware
---

### Post by PierreRussellStraddler on 2009-01-14
Hello everyone!

I have an acer scan prisa 1240

according to this website

[http://www.buzzard.me.uk/jonathan/scanners-usb.html](http://www.buzzard.me.uk/jonathan/scanners-usb.html)
 
"full SANE backend exists though it may not be included in the latest version of SANE yet. The scanner should function with few problems and image quality is as good as the native MS Windows/MacOS drivers."

that web site then tells me to go to this web site

[http://snapscan.sourceforge.net/](http://snapscan.sourceforge.net/)

which then tells me to go to this web site 

[http://www.sane-project.org/](http://www.sane-project.org/)

"to get the latest sane source"

This is where the problems begin.

I am presented with two options, HTTP and FTP.

when I chose HTTP, I arrive on this web page

[http://alioth.debian.org/frs/?group_id=30186](http://alioth.debian.org/frs/?group_id=30186)

and am presented with 

sane-backends-1.0.18-1.0.19.diff.gz
sane-backends-1.0.19.tar.gz

and 

sane-backends-1.0.19.tar.gz.md5

when I click on any of them I get an error:

/tmp/sane-backends-1.0.19.tar-1.gz could not be opened, because the associated helper application does not exist. Change the association in your preferences.

/tmp/sane-backends-1.0.18-1.0.19.diff-1.gz could not be opened, because the associated helper application does not exist. Change the association in your preferences.

/tmp/sane-backends-1.0.18-1.0.19.diff-2.gz could not be opened, because the associated helper application does not exist. Change the association in your preferences.

when I try to make it happen in FTP, I get the same error:

so question one is where/how can I get the "associated helper application" in question--or how can I change the association in my preferences?



I tried sane-find-scanner and got this:

found USB scanner (vendor=0x04a5 [Color], product=0x20c0 [ FlatbedScanner 13]) at libusb:003:003
  # Your USB scanner was (probably) detected. It may or may not be supported by
  # SANE. Try scanimage -L and read the backend's manpage.

then I did this

pierre@pierre-desktop:~$ scanimage -L
device `snapscan:libusb:003:003' is a Acer FlatbedScanner13 flatbed scanner


so far so good.  Then I did this

pierre@pierre-desktop:~$ usb 0x04a5 0x20c0
bash: usb: command not found



a little later, I did this

pierre@pierre-desktop:~$ sudo apt-get install libusb
[sudo] password for pierre: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package libusb


and then ended my evening with this

pierre@pierre-desktop:~$ lsmod
Module                  Size  Used by
ipv6                  263972  8 
af_packet              25728  2 
binfmt_misc            16904  1 
rfcomm                 44432  0 
sco                    18308  2 
bridge                 56980  0 
stp                    10628  1 bridge
bnep                   20480  2 
l2cap                  30464  6 rfcomm,bnep
bluetooth              61924  6 rfcomm,sco,bnep,l2cap
ppdev                  15620  0 
cpufreq_powersave       9856  0 
cpufreq_conservative    14600  0 
cpufreq_stats          13188  0 
cpufreq_ondemand       14988  0 
freq_table             12672  2 cpufreq_stats,cpufreq_ondemand
cpufreq_userspace      11396  0 
sbs                    19464  0 
sbshc                  13440  1 sbs
container              11520  0 
wmi                    14504  0 
video                  25104  0 
output                 11008  1 video
pci_slot               12552  0 
battery                18436  0 
iptable_filter         10752  0 
ip_tables              19600  1 iptable_filter
x_tables               22916  1 ip_tables
ac                     12292  0 
lp                     17156  0 
evdev                  17696  8 
psmouse                45200  0 
pcspkr                 10624  0 
serio_raw              13444  0 
snd_intel8x0           37532  6 
snd_usb_audio          89728  2 
snd_pcm_oss            46848  0 
snd_ac97_codec        111652  1 snd_intel8x0
snd_mixer_oss          22784  1 snd_pcm_oss
ac97_bus                9856  1 snd_ac97_codec
snd_pcm                83204  4 snd_intel8x0,snd_usb_audio,snd_pcm_oss,snd_ac97_codec
snd_usb_lib            24192  1 snd_usb_audio
snd_seq_dummy          10884  0 
snd_hwdep              15236  1 snd_usb_audio
snd_seq_oss            38528  0 
snd_seq_midi           14336  0 
snd_rawmidi            29824  2 snd_usb_lib,snd_seq_midi
parport_pc             39204  1 
parport                42604  3 ppdev,lp,parport_pc
snd_seq_midi_event     15232  2 snd_seq_oss,snd_seq_midi
snd_seq                57776  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              29960  2 snd_pcm,snd_seq
snd_seq_device         15116  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    63268  28 snd_intel8x0,snd_usb_audio,snd_pcm_oss,snd_ac97_codec,snd_mixer_oss,snd_pcm,snd_hwdep,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
button                 14224  0 
soundcore              15328  1 snd
snd_page_alloc         16136  2 snd_intel8x0,snd_pcm
i2c_sis96x             12420  0 
i2c_sis630             14476  0 
sis_agp                15232  1 
i2c_core               31892  2 i2c_sis96x,i2c_sis630
shpchp                 37908  0 
agpgart                42184  1 sis_agp
pci_hotplug            35236  1 shpchp
ext3                  133384  1 
jbd                    55444  1 ext3
mbcache                16004  1 ext3
sr_mod                 22212  0 
cdrom                  43168  1 sr_mod
sd_mod                 42264  3 
crc_t10dif              9984  1 sd_mod
usbhid                 35840  0 
hid                    50560  1 usbhid
sg                     39732  0 
ata_generic            12932  0 
pata_acpi              12160  0 
pata_sis               18436  2 
libata                177312  3 ata_generic,pata_acpi,pata_sis
ehci_hcd               43276  0 
uhci_hcd               30736  0 
sis900                 27904  0 
mii                    13440  1 sis900
scsi_mod              155212  4 sr_mod,sd_mod,sg,libata
dock                   16656  1 libata
ohci_hcd               31888  0 
usbcore               148848  7 snd_usb_audio,snd_usb_lib,usbhid,ehci_hcd,uhci_hcd,ohci_hcd
thermal                23708  0 
processor              42156  1 thermal
fan                    12548  0 
fbcon                  47648  0 
tileblit               10880  1 fbcon
font                   16512  1 fbcon
bitblit                13824  1 fbcon
softcursor              9984  1 bitblit
fuse                   60828  5 
pierre@pierre-desktop:~$ modprobe -v scanner
FATAL: Module scanner not found.



of course any help getting my scanner working would be greatly appreciated!

Thanks as always,

Pierre Russell Straddler

---

### Post by PierreRussellStraddler on 2009-02-04
Hi everyone

Please pardon the BUMP, but it has been a few weeks now and nary a peep vis a vis my apparently supported yet not working scanner.

Maybe this is a piece to the puzzle:


I ran sane-find-scanner -v  and here's what I got:

searching for USB scanners:
checking /dev/usb/scanner... failed to open (Invalid argument)
checking /dev/usb/scanner0... failed to open (Invalid argument)
checking /dev/usb/scanner1... failed to open (Invalid argument)
checking /dev/usb/scanner2... failed to open (Invalid argument)
checking /dev/usb/scanner3... failed to open (Invalid argument)
checking /dev/usb/scanner4... failed to open (Invalid argument)
checking /dev/usb/scanner5... failed to open (Invalid argument)
checking /dev/usb/scanner5... failed to open (Invalid argument)
checking /dev/usb/scanner7... failed to open (Invalid argument)
checking /dev/usb/scanner8... failed to open (Invalid argument)
checking /dev/usb/scanner9... failed to open (Invalid argument)
checking /dev/usb/scanner10... failed to open (Invalid argument)
checking /dev/usb/scanner11... failed to open (Invalid argument)
checking /dev/usb/scanner12... failed to open (Invalid argument)
checking /dev/usb/scanner13... failed to open (Invalid argument)
checking /dev/usb/scanner14... failed to open (Invalid argument)
checking /dev/usb/scanner15... failed to open (Invalid argument)
checking /dev/usbscanner... failed to open (Invalid argument)
checking /dev/usbscanner0... failed to open (Invalid argument)
checking /dev/usbscanner1... failed to open (Invalid argument)
checking /dev/usbscanner2... failed to open (Invalid argument)
checking /dev/usbscanner3... failed to open (Invalid argument)
checking /dev/usbscanner4... failed to open (Invalid argument)
checking /dev/usbscanner5... failed to open (Invalid argument)
checking /dev/usbscanner6... failed to open (Invalid argument)
checking /dev/usbscanner7... failed to open (Invalid argument)
checking /dev/usbscanner8... failed to open (Invalid argument)
checking /dev/usbscanner9... failed to open (Invalid argument)
checking /dev/usbscanner10... failed to open (Invalid argument)
checking /dev/usbscanner11... failed to open (Invalid argument)
checking /dev/usbscanner12... failed to open (Invalid argument)
checking /dev/usbscanner13... failed to open (Invalid argument)
checking /dev/usbscanner14... failed to open (Invalid argument)
checking /dev/usbscanner15... failed to open (Invalid argument)
found USB scanner (vendor=0x04a5 [Color], product=0x20c0 [ FlatbedScanner 13]) at libusb:005:002

  # Your USB scanner was (probably) detected. It may or may not be supported by
  # SANE. Try scanimage -L and read the backend's manpage.

  # Not checking for parallel port scanners.

  # Most Scanners connected to the parallel port or other proprietary ports
  # can't be detected by this program.

  # You may want to run this program as root to find all devices. Once you
  # found the scanner devices, be sure to adjust access permissions as
  # necessary.


done


Then I tried scanimage -L as suggested by the terminal:

pierre@pierre-desktop:~$ scanimage -L

No scanners were identified. If you were expecting something different,
check that the scanner is plugged in, turned on and detected by the
sane-find-scanner tool (if appropriate). Please read the documentation
which came with this software (README, FAQ, manpages).



so on the one hand, the usb scanner is found:

scanner = Benq/Acer/Vuego 1240U
usb 0x04a5 0x20c0
libusb:005:002



yet when I try and open Xsane image scanner I get

"No Devices available"

which is a change from the usual "Invalid Argument" error I usually get.

Does that mean I'm moving backwards towards problem and away from solution?




I haven't had much luck decoding the sane-project.org website, despite numerous efforts to do so.

I realize that scanners are a perinneal problem in Ubuntu (perhaps one that should be announced up front:  *Ubuntu is great, but chances are your scanner won't work and you will probably spend weeks and weeks trying to get it to operate* or something of the like), 

Yet it would appear that the Acer scan prisa 1240 is supported, and should work (despite my efforts to the contrary).  

Is there anyone in the entire Ubuntu community that could shed some light on this continuing nuisance?

Thank you again for your help and support,

Pierre Russell Straddler.

---

### Post by PierreRussellStraddler on 2009-03-01
Hi everyone!

I feel like I'm getting closer.

in the terminal, sudo scanimage -L results in the following:

found USB scanner (vendor=0x04a5 [Color], product=0x20c0 [ FlatbedScanner 13]) at libusb:005:002
  # Your USB scanner was (probably) detected. It may or may not be supported by
  # SANE. Try scanimage -L and read the backend's manpage.

in the terminal, sudo scanimage results in the following:

[snapscan] Cannot open firmware file /usr/share/sane/snapscan/your-firmwarefile.bin.
[snapscan] Edit the firmware file entry in snapscan.conf.
scanimage: open of device snapscan:libusb:005:002 failed: Invalid argument

so my guess is I need to go into /usr/share/sane/snapscan.conf/ and change "your-firmwarefile.bin" to something specific...but what?

do I change it to snapscan:libusb:005:002?
do I change it to # Benq/Acer/Vuego 1240U?
do I change it to usb 0x04a5 0x20c0?

anyone?

---

### Post by PierreRussellStraddler on 2009-03-01
ah, and also this:

when I do go to /usr/share/sane there is no "snapscan"--which I guess would answery why:

Cannot open firmware file /usr/share/sane/snapscan/your-firmwarefile.bin.

in the /usr/share/sane directory there are two sub directories:
gt68xx and xsane.

any guesses?  

any help gratefully accepted

pierre

---

### Post by PierreRussellStraddler on 2009-03-02
WOOOOOOOOO HOOOOOOOOOOO!!!!!!!!!!!

MY SCANNER WORKS!!!!!!!!!!!!!!!!!!


[http://ubuntuforums.org/archive/index.php/t-317685.html](http://ubuntuforums.org/archive/index.php/t-317685.html)

was the answer!!!!!!!!!!!!!!!

YAAAAAAAAAAAAAAYY!!!!!!!!!!!

problem SOLVED!!!!!!!

:)

---

