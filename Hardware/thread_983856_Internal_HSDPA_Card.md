---
title: "Internal HSDPA Card"
date: 2008-11-16
forum: Hardware
---

### Post by I-Broke-It on 2008-11-16
Hi, I have tried for two days now with little luck to get my Internal HSDP:confused:A card to work. I have a external E220 that works fine but it seem that the internal Mobile Broadband is not picked up. I have a travelmate 5730 with build in HSDPA card. I am running Ubuntu 8.10. I have attached a copy of my dmesg. Hope this is enough to solve it. please let me know if there is more info that I can provide.

Thanks

---

### Post by I-Broke-It on 2008-11-16
Bump:(:(:(:(:(

---

### Post by teaker1s on 2008-11-16
```
lspci -v
```

```
lsusb
```

depending how it's connected should see it with  the above commands.

vendor and product id if it doesn't state model in output.

if your not sure post output

---

### Post by I-Broke-It on 2008-11-16
Thanks for the help it is really appreciated:popcorn:

I have no idea if I am seeing it. but maybe your trained eye will pick it out.

You will see that with the lsusb there are two listings one with my external modem plucked in and the other with it plucked out. 

Thanks again for the help

---

### Post by I-Broke-It on 2008-11-16
Bump [-o<[-o<[-o<[-o<

---

### Post by I-Broke-It on 2008-11-16
Bump - any help will be appreciated. If you can just say it is not there or it is this line in this file. Thanks

---

### Post by finito on 2008-11-16
sorry double post

---

### Post by finito on 2008-11-16
Well, I can't seem to tell what HSDPA card you have from those, Manufacturer specifications don't seem to say which HSDPA chip is inside.

would you happen to know which manufacturer made it or the model number?

P.S. you can't bump more than once in 24 hours forum rules

---

### Post by teaker1s on 2008-11-16
> Bus 006 Device 002: ID 12d1:1003 Huawei Technologies Co., Ltd. E220 HSDPA Modem / E270 HSDPA/HSUPA Modem can see your external modem, can't seem to  see internal have you checked bios for any settings

---

### Post by brianbaru on 2008-11-16
i get identical results with lsusb

Bus 004 Device 003: ID 090c:1000 Feiya Technology Corp. Memory Bar
Bus 004 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 008 Device 005: [COLOR="Red"]ID 12d1:1003[/COLOR] Huawei Technologies Co., Ltd. E220 HSDPA Modem / E270 HSDPA/HSUPA Modem
Bus 008 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 003: ID 045e:0040 Microsoft Corp. Wheel Mouse Optical
Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
brian@ubuntu:~$ 

i am using a huawei 160g which i recieved from 3 uk this week
the tutorial i followed to install was origanaly posted by fingers and thumbs 

basically

sudo wvdialconf

creates wvdial.conf

then edit /etc/wvdial.conf

change phone number, username, password as below

my wvdial.conf

[Dialer Defaults]
Init1 = ATZ
Init2 = ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
Modem Type = Analog Modem
Baud = 9600
New PPPD = yes
Modem = /dev/ttyUSB0
ISDN = 0
Phone = *99#
Password = three
Username = three

i then manual edited network settings

select point to point

General

        tick enable this    connection
        connection type     gprs/umts
        access point name   3internet
        phone number      *99#
        dial prfix        BLANK

account data

        username          three
        password          three

modem tab
         modem port       /dev/ttyS0
         dial type        tones 
         volume           off

open a terminal type wvdial Defaults    (the capital D is important

wait a while open firefox

this worked for me less than twenty minutes ago but i have not been useing ubuntu/linux very long and this is the first post i have done so i am sorry for any mistakes etc i am using 3usb modem to reply tothis post hopefully when i switch off i will be able to repeat and get on internet


i have got back on but i had to unplug and plugin the modem to get it to work

---

### Post by I-Broke-It on 2008-11-17
Hi Thanks for all the help. :popcorn:

finito -> Sorry for the two bump I am still new at this will not do it again. Please see email below about card

teaker1s -> I found the Windows driver disc you think ndiswraper will work? It seem quite extreme -> for me any way still new at it.

brianbaru -> Thanks for the help

I have found some CD with all the other stuff I got with the PC (I was so exited when I got the PC that I booted with Ubuntu immediately, discarding all the software provided - I knew the new release cater for 3G -except for my internal 3G card:()

I found the window drivers and documentation for the HSPDA card. I did not think these would be important:(. Anyway the card is getting picked up it is this line in the lsusb -> Bus 003 Device 002: ID 0af0:7211 Option.

This I worked out from the docs that said Option wireless technologies. The modem is a Globe Trotter connect.

So the good news is Ubuntu is picking up the card. Bad news is it is not working. 

Any ideas on how to proceed from here?

Thanks.

---

### Post by teaker1s on 2008-11-17
[http://mybroadband.co.za/vb/showthread.php?t=52196]("http://mybroadband.co.za/vb/showthread.php?t=52196")
 description of operation
if you look in synaptic there is  ** nozomi-source          **
which is the source for GlobeTrotter HSDPA kernel driver.

if your not familiar with kernel modules
```
sudo apt-get install module-assistant
```
```
sudo module-assistant
``` will graphically build and install source kernel packages.

apologies for not seeing your modem previously- didn't occur that it was usb

---

### Post by I-Broke-It on 2008-11-19
Thanks teaker1s

I did install the  nozomi-source 2.1-5 and gcom 0.3-1 via synaptic

I tried to follow the tread on how to run it I created the two files.

I am afraid I do not understand the last two statements
[INDENT]Insert the module:

# insmod nozomi.ko

and then connect:

# pppd call globetrotter
[/INDENT]

But i think that I triped over something that needs to happen before I can run these if that is what needs to happen.

In the DEV folder (I assume this stands for devices) I am sure there need to be a file called dev/modem or in the globetrotter file it reveres to dev/noz0.

in my folder I have the following
[INDENT]:/dev$ dir
agpgart		    ptye0  ptyu9   rtc0        ttyb3   ttyr8	ttyxb
audio		    ptye1  ptyua   scd0        ttyb4   ttyr9	ttyxc
block		    ptye2  ptyub   scd1        ttyb5   ttyra	ttyxd
bus		    ptye3  ptyuc   sda	       ttyb6   ttyrb	ttyxe
cdrom		    ptye4  ptyud   sda1        ttyb7   ttyrc	ttyxf
cdrom1		    ptye5  ptyue   sda2        ttyb8   ttyrd	ttyy0
cdrw		    ptye6  ptyuf   sda5        ttyb9   ttyre	ttyy1
char		    ptye7  ptyv0   sequencer   ttyba   ttyrf	ttyy2
console		    ptye8  ptyv1   sequencer2  ttybb   ttys0	ttyy3
core		    ptye9  ptyv2   sg0	       ttybc   ttyS0	ttyy4
cpu_dma_latency     ptyea  ptyv3   sg1	       ttybd   ttys1	ttyy5
disk		    ptyeb  ptyv4   sg2	       ttybe   ttyS1	ttyy6
dri		    ptyec  ptyv5   shm	       ttybf   ttys2	ttyy7
dsp		    ptyed  ptyv6   snapshot    ttyc0   ttyS2	ttyy8
dvd		    ptyee  ptyv7   snd	       ttyc1   ttys3	ttyy9
dvdrw		    ptyef  ptyv8   sndstat     ttyc2   ttyS3	ttyya
fd		    ptyp0  ptyv9   sr0	       ttyc3   ttys4	ttyyb
full		    ptyp1  ptyva   sr1	       ttyc4   ttys5	ttyyc
fuse		    ptyp2  ptyvb   stderr      ttyc5   ttys6	ttyyd
hidraw0		    ptyp3  ptyvc   stdin       ttyc6   ttys7	ttyye
hidraw1		    ptyp4  ptyvd   stdout      ttyc7   ttys8	ttyyf
hpet		    ptyp5  ptyve   tty	       ttyc8   ttys9	ttyz0
initctl		    ptyp6  ptyvf   tty0        ttyc9   ttysa	ttyz1
input		    ptyp7  ptyw0   tty1        ttyca   ttysb	ttyz2
kmem		    ptyp8  ptyw1   tty10       ttycb   ttysc	ttyz3
kmsg		    ptyp9  ptyw2   tty11       ttycc   ttysd	ttyz4
log		    ptypa  ptyw3   tty12       ttycd   ttyse	ttyz5
loop0		    ptypb  ptyw4   tty13       ttyce   ttysf	ttyz6
MAKEDEV		    ptypc  ptyw5   tty14       ttycf   ttyt0	ttyz7
mem		    ptypd  ptyw6   tty15       ttyd0   ttyt1	ttyz8
mixer		    ptype  ptyw7   tty16       ttyd1   ttyt2	ttyz9
net		    ptypf  ptyw8   tty17       ttyd2   ttyt3	ttyza
network_latency     ptyq0  ptyw9   tty18       ttyd3   ttyt4	ttyzb
network_throughput  ptyq1  ptywa   tty19       ttyd4   ttyt5	ttyzc
null		    ptyq2  ptywb   tty2        ttyd5   ttyt6	ttyzd
oldmem		    ptyq3  ptywc   tty20       ttyd6   ttyt7	ttyze
port		    ptyq4  ptywd   tty21       ttyd7   ttyt8	ttyzf
ppp		    ptyq5  ptywe   tty22       ttyd8   ttyt9	urandom
psaux		    ptyq6  ptywf   tty23       ttyd9   ttyta	usbdev1.1_ep00
ptmx		    ptyq7  ptyx0   tty24       ttyda   ttytb	usbdev1.1_ep81
pts		    ptyq8  ptyx1   tty25       ttydb   ttytc	usbdev1.3_ep00
ptya0		    ptyq9  ptyx2   tty26       ttydc   ttytd	usbdev1.3_ep02
ptya1		    ptyqa  ptyx3   tty27       ttydd   ttyte	usbdev1.3_ep81
ptya2		    ptyqb  ptyx4   tty28       ttyde   ttytf	usbdev1.3_ep83
ptya3		    ptyqc  ptyx5   tty29       ttydf   ttyu0	usbdev2.1_ep00
ptya4		    ptyqd  ptyx6   tty3        ttye0   ttyu1	usbdev2.1_ep81
ptya5		    ptyqe  ptyx7   tty30       ttye1   ttyu2	usbdev3.1_ep00
ptya6		    ptyqf  ptyx8   tty31       ttye2   ttyu3	usbdev3.1_ep81
ptya7		    ptyr0  ptyx9   tty32       ttye3   ttyu4	usbdev3.2_ep00
ptya8		    ptyr1  ptyxa   tty33       ttye4   ttyu5	usbdev3.2_ep02
ptya9		    ptyr2  ptyxb   tty34       ttye5   ttyu6	usbdev3.2_ep03
ptyaa		    ptyr3  ptyxc   tty35       ttye6   ttyu7	usbdev3.2_ep04
ptyab		    ptyr4  ptyxd   tty36       ttye7   ttyu8	usbdev3.2_ep81
ptyac		    ptyr5  ptyxe   tty37       ttye8   ttyu9	usbdev3.2_ep82
ptyad		    ptyr6  ptyxf   tty38       ttye9   ttyua	usbdev3.2_ep83
ptyae		    ptyr7  ptyy0   tty39       ttyea   ttyub	usbdev3.2_ep84
ptyaf		    ptyr8  ptyy1   tty4        ttyeb   ttyuc	usbdev3.2_ep85
ptyb0		    ptyr9  ptyy2   tty40       ttyec   ttyud	usbdev4.1_ep00
ptyb1		    ptyra  ptyy3   tty41       ttyed   ttyue	usbdev4.1_ep81
ptyb2		    ptyrb  ptyy4   tty42       ttyee   ttyuf	usbdev4.3_ep00
ptyb3		    ptyrc  ptyy5   tty43       ttyef   ttyUSB0	usbdev4.3_ep83
ptyb4		    ptyrd  ptyy6   tty44       ttyHS0  ttyUSB1	usbdev5.1_ep00
ptyb5		    ptyre  ptyy7   tty45       ttyHS1  ttyv0	usbdev5.1_ep81
ptyb6		    ptyrf  ptyy8   tty46       ttyHS2  ttyv1	usbdev5.2_ep00
ptyb7		    ptys0  ptyy9   tty47       ttyHS3  ttyv2	usbdev5.2_ep81
ptyb8		    ptys1  ptyya   tty48       ttyp0   ttyv3	usbdev5.2_ep82
ptyb9		    ptys2  ptyyb   tty49       ttyp1   ttyv4	usbdev6.1_ep00
ptyba		    ptys3  ptyyc   tty5        ttyp2   ttyv5	usbdev6.1_ep81
ptybb		    ptys4  ptyyd   tty50       ttyp3   ttyv6	usbdev6.3_ep00
ptybc		    ptys5  ptyye   tty51       ttyp4   ttyv7	usbdev6.3_ep02
ptybd		    ptys6  ptyyf   tty52       ttyp5   ttyv8	usbdev6.3_ep04
ptybe		    ptys7  ptyz0   tty53       ttyp6   ttyv9	usbdev6.3_ep05
ptybf		    ptys8  ptyz1   tty54       ttyp7   ttyva	usbdev6.3_ep81
ptyc0		    ptys9  ptyz2   tty55       ttyp8   ttyvb	usbdev6.3_ep82
ptyc1		    ptysa  ptyz3   tty56       ttyp9   ttyvc	usbdev6.3_ep83
ptyc2		    ptysb  ptyz4   tty57       ttypa   ttyvd	usbdev6.3_ep85
ptyc3		    ptysc  ptyz5   tty58       ttypb   ttyve	usbdev7.1_ep00
ptyc4		    ptysd  ptyz6   tty59       ttypc   ttyvf	usbdev7.1_ep81
ptyc5		    ptyse  ptyz7   tty6        ttypd   ttyw0	usbdev8.1_ep00
ptyc6		    ptysf  ptyz8   tty60       ttype   ttyw1	usbdev8.1_ep81
ptyc7		    ptyt0  ptyz9   tty61       ttypf   ttyw2	vcs
ptyc8		    ptyt1  ptyza   tty62       ttyq0   ttyw3	vcs1
ptyc9		    ptyt2  ptyzb   tty63       ttyq1   ttyw4	vcs2
ptyca		    ptyt3  ptyzc   tty7        ttyq2   ttyw5	vcs3
ptycb		    ptyt4  ptyzd   tty8        ttyq3   ttyw6	vcs4
ptycc		    ptyt5  ptyze   tty9        ttyq4   ttyw7	vcs5
ptycd		    ptyt6  ptyzf   ttya0       ttyq5   ttyw8	vcs6
ptyce		    ptyt7  ram0    ttya1       ttyq6   ttyw9	vcs7
ptycf		    ptyt8  ram1    ttya2       ttyq7   ttywa	vcs8
ptyd0		    ptyt9  ram10   ttya3       ttyq8   ttywb	vcsa
ptyd1		    ptyta  ram11   ttya4       ttyq9   ttywc	vcsa1
ptyd2		    ptytb  ram12   ttya5       ttyqa   ttywd	vcsa2
ptyd3		    ptytc  ram13   ttya6       ttyqb   ttywe	vcsa3
ptyd4		    ptytd  ram14   ttya7       ttyqc   ttywf	vcsa4
ptyd5		    ptyte  ram15   ttya8       ttyqd   ttyx0	vcsa5
ptyd6		    ptytf  ram2    ttya9       ttyqe   ttyx1	vcsa6
ptyd7		    ptyu0  ram3    ttyaa       ttyqf   ttyx2	vcsa7
ptyd8		    ptyu1  ram4    ttyab       ttyr0   ttyx3	vcsa8
ptyd9		    ptyu2  ram5    ttyac       ttyr1   ttyx4	video0
ptyda		    ptyu3  ram6    ttyad       ttyr2   ttyx5	xconsole
ptydb		    ptyu4  ram7    ttyae       ttyr3   ttyx6	zero
ptydc		    ptyu5  ram8    ttyaf       ttyr4   ttyx7
ptydd		    ptyu6  ram9    ttyb0       ttyr5   ttyx8
ptyde		    ptyu7  random  ttyb1       ttyr6   ttyx9
ptydf		    ptyu8  rtc	   ttyb2       ttyr7   ttyxa
[/INDENT]

I think my device is missing from here and it should be present.

Thanks for all the help so far

---

### Post by teaker1s on 2008-11-19
far from being any kind of expert in this modem,  command ```
lsmod
``` will show if the module is loaded.
secondly have you tried some googling name of your modem and nozomi or name of your model and linux.
[http://ubuntuforums.org/showthread.php?t=325669]("http://ubuntuforums.org/showthread.php?t=325669") the poster suggests a link in their post and also has issue,maybe it's driver related.

if you have a think and a search I'll see if I can find anything else.

---

### Post by I-Broke-It on 2008-11-20
Thanks again teaker1s

I have tried a few things like createing the noz0 in dev using wvdail. I still think this is stuff that I need to do after what my problem is. Here is my lsmod. I will try some more in the morning but I have some important docs I need to go and search for for now and can not spend more time on this.

I do not see my modem if I plug the huawei in I see this look quite different.

Thanks again.

:~$ lsmod
Module                  Size  Used by
af_packet              25728  2 
i915                   38144  2 
drm                    86056  3 i915
binfmt_misc            16904  1 
rfcomm                 44432  0 
bridge                 56980  0 
stp                    10628  1 bridge
bnep                   20480  2 
sco                    18308  2 
l2cap                  30464  6 rfcomm,bnep
bluetooth              61924  6 rfcomm,bnep,sco,l2cap
ppdev                  15620  0 
acpi_cpufreq           15500  1 
cpufreq_powersave       9856  0 
cpufreq_stats          13188  0 
cpufreq_userspace      11396  0 
cpufreq_conservative    14600  0 
cpufreq_ondemand       14988  1 
freq_table             12672  3 acpi_cpufreq,cpufreq_stats,cpufreq_ondemand
pci_slot               12552  0 
container              11520  0 
sbs                    19464  0 
sbshc                  13440  1 sbs
iptable_filter         10752  0 
ip_tables              19600  1 iptable_filter
x_tables               22916  1 ip_tables
parport_pc             39204  0 
lp                     17156  0 
parport                42604  3 ppdev,parport_pc,lp
pcmcia                 43052  0 
snd_hda_intel         381488  3 
snd_pcm_oss            46848  0 
snd_mixer_oss          22784  1 snd_pcm_oss
acer_wmi               18880  0 
snd_pcm                83204  2 snd_hda_intel,snd_pcm_oss
arc4                    9984  2 
ecb                    10880  2 
crypto_blkcipher       25476  1 ecb
snd_seq_dummy          10884  0 
psmouse                45200  0 
serio_raw              13444  0 
snd_seq_oss            38528  0 
pcspkr                 10624  0 
snd_seq_midi           14336  0 
snd_rawmidi            29824  1 snd_seq_midi
snd_seq_midi_event     15232  2 snd_seq_oss,snd_seq_midi
iwlagn                 99588  0 
iwlcore                92740  1 iwlagn
evdev                  17696  14 
snd_seq                57776  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
joydev                 18368  0 
led_class              12164  2 acer_wmi,iwlcore
snd_timer              29960  2 snd_pcm,snd_seq
snd_seq_device         15116  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
mac80211              216820  2 iwlagn,iwlcore
cfg80211               32392  3 iwlagn,iwlcore,mac80211
snd                    63268  15 snd_hda_intel,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
yenta_socket           31756  1 
rsrc_nonstatic         19072  1 yenta_socket
sdhci_pci              15360  0 
sdhci                  23940  1 sdhci_pci
pcmcia_core            43412  3 pcmcia,yenta_socket,rsrc_nonstatic
mmc_core               58268  1 sdhci
soundcore              15328  1 snd
uvcvideo               62728  0 
snd_page_alloc         16136  2 snd_hda_intel,snd_pcm
shpchp                 37908  0 
pci_hotplug            35236  1 shpchp
compat_ioctl32          9344  1 uvcvideo
hso                    38496  0 
videodev               41344  1 uvcvideo
v4l1_compat            22404  2 uvcvideo,videodev
rfkill                 17176  4 iwlcore,hso
ac                     12292  0 
battery                18436  0 
video                  25104  0 
output                 11008  1 video
wmi                    14504  1 acer_wmi
button                 14224  0 
intel_agp              33724  1 
agpgart                42184  3 drm,intel_agp
ext3                  133384  1 
jbd                    55444  1 ext3
mbcache                16004  1 ext3
usbhid                 35840  0 
hid                    50560  1 usbhid
sd_mod                 42264  3 
crc_t10dif              9984  1 sd_mod
sr_mod                 22212  0 
cdrom                  43168  1 sr_mod
sg                     39732  0 
ahci                   37132  2 
libata                177312  1 ahci
scsi_mod              155212  4 sd_mod,sr_mod,sg,libata
dock                   16656  1 libata
tg3                   129924  0 
libphy                 27392  1 tg3
ehci_hcd               43276  0 
uhci_hcd               30736  0 
usbcore               148848  6 uvcvideo,hso,usbhid,ehci_hcd,uhci_hcd
thermal                23708  0 
processor              42156  4 acpi_cpufreq,thermal
fan                    12548  0 
fbcon                  47648  0 
tileblit               10880  1 fbcon
font                   16512  1 fbcon
bitblit                13824  1 fbcon
softcursor              9984  1 bitblit
fuse                   60828  3

---

### Post by I-Broke-It on 2008-11-20
OK one last try gave me something I change my wvdail.conf as follows:
# wvdial for Vodacom Data. Created by Tazz_tux
# Version 1.0

# Change Log:
#
# Added support for HSDPA.
# Added Headers and version control.

[Dialer Defaults]
Phone = *99***1#
Username = username
Password = password
Stupid Mode = 1
Dial Command = ATDT

[Dialer hsdpa]
Modem = /dev/ttyHS0
Baud = 460800
Init2 = ATZ
Init3 = ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
ISDN = 0
Modem Type = Analog Modem





#[Dialer Defaults]
#Phone = 
#Username = 
#Password = 
#New PPPD = yes


I got the following result:
:~$ wvdial hsdpa
--> WvDial: Internet dialer version 1.60
--> Cannot get information for serial port.
--> Initializing modem.
--> Sending: ATZ
ATZ
OK
--> Sending: ATZ
ATZ
OK
--> Sending: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
OK
--> Modem initialized.
--> Sending: ATDT*99***1#
--> Waiting for carrier.
--> Timed out while dialing.  Trying again.
--> Sending: ATDT*99***1#
--> Waiting for carrier.
--> Timed out while dialing.  Trying again.
--> Sending: ATDT*99***1#
--> Waiting for carrier.
--> Timed out while dialing.  Trying again.
--> Sending: ATDT*99***1#
--> Waiting for carrier.
--> Timed out while dialing.  Trying again.
--> Sending: ATDT*99***1#
--> Waiting for carrier.
--> Timed out while dialing.  Trying again.


I think the CTRL-Break got me out I was pressing a hole bunch of keys.

I hope this looks good and not like I am on the same spot.

Thanks

---

### Post by teaker1s on 2008-11-20
looking at your output it appears that the modem is dialing out, with the correct user name and password and settings, you should be well on your way.
if you need to stop something in terminal
ctrl  z

---

### Post by I-Broke-It on 2008-11-21
Today's effort is concentrated on the following URL

[http://www.pharscape.org/content/view/66/53/](http://www.pharscape.org/content/view/66/53/)

I got this from [https://launchpad.net/ubuntu/intrepid/+package/nozomi-source](https://launchpad.net/ubuntu/intrepid/+package/nozomi-source) 

Will let you know if there is any success. So far I had no luck with wvdial.

Thanks

---

### Post by I-Broke-It on 2008-11-23
Still no luck.

My wvdial.conf looks like this at the moment.
[Dialer hsdpa]
Phone = *99#
Username = vodafone
Password = vodafone
Stupid Mode = 1
Dial Command = ATDT
#Modem = /dev/ttyUSB0
Modem = /dev/ttyHS0
Baud = 460800
Init2 = ATZ
Init3 = ATE0V1&D2&C1S0=0+IFC=2,2
ISDN = 0
Modem Type = Analog Modem
#Init5 = AT+CGDCONT=1,"IP","internet";


#[Dialer Defaults]
#Phone = 
#Username = 
#Password = 
#New PPPD = yes

my wvdail in terminal give the following result:
:~$ wvdial hsdpa
--> WvDial: Internet dialer version 1.60
--> Cannot get information for serial port.
--> Initializing modem.
--> Sending: ATZ
ATZ
OK
--> Sending: ATZ
ATZ
OK
--> Sending: ATE0V1&D2&C1S0=0+IFC=2,2
ATE0V1&D2&C1S0=0+IFC=2,2
OK
--> Modem initialized.
--> Sending: ATDT*99#
--> Waiting for carrier.
--> Timed out while dialing.  Trying again.
--> Sending: ATDT*99#
--> Waiting for carrier.
--> Timed out while dialing.  Trying again.
--> Sending: ATDT*99#
--> Waiting for carrier.
--> Timed out while dialing.  Trying again.


I also tried the HSOconnect. It opens up it regester but it will not connect:

If you could please look at my wvdial.config and see that it is correct

Thanks

---

### Post by I-Broke-It on 2008-11-30
I have reloaded Ubuntu 8.10 again as I thought that I have fiddled so much I will never get all the things back to the start!?!

It seem that I had the most luck with the wvdail so far so I am down that route again. It seem that the problem to my limited understanding is the config file? 

I live in South Africa and I use a provider called Vodacom. It would be appreciated if someone can correct my file or say that they had success using the same settings.

All help much appreciated.

My wvdial.config:

[INDENT][Dialer hsdpa]
Phone = *99#
Username = vodafone
Password = vodafone
Stupid Mode = 1
Dial Command = ATDT
#Modem = /dev/ttyUSB0
Modem = /dev/ttyHS0
Baud = 460800
Init2 = ATZ
Init3 = ATE0V1&D2&C1S0=0+IFC=2,2
ISDN = 0
Modem Type = Analog Modem
Init5 = AT+CGDCONT=1,"IP","internet";



#[Dialer Defaults]
#Phone = 
#Username = 
#Password = 
#New PPPD = yes[/INDENT]

---

### Post by Pharscape on 2008-12-01
You can only use PPP with a device that uses hso.ko d if it has a modem port enabled. Have a look at the readme bundled with the 1.6 driver.

Not all devices have it enabled and if it is the port will not be ttyHS0.

Have a look at the readme bundled with the 1.6 driver.

Also note that the driver bundled with Ubuntu 8.04 is ver 1.2 and my site has 1.6 which may give better stability. 

Cheers,
Paul

---

### Post by Pharscape on 2008-12-01
Device ID 7211 does require hso and not nozomi:

[http://www.pharscape.org/hso.html#productID](http://www.pharscape.org/hso.html#productID)

---

### Post by I-Broke-It on 2008-12-01
Thanks Paul,

I have tried to install the driver again using the instructions as on [http://www.pharscape.org/HSOconnect-Ubuntu-8.04.html](http://www.pharscape.org/HSOconnect-Ubuntu-8.04.html). The process open and it say registered but it does not connect. I have put the debug log in the desktop.tar.gz as HSOcDbg the termenal output I saved as python_hso. I have also put in some other files dmesg, kern.log and lsmod hoping this will help.

My permissions looks as follows:

:~$ ls -al /dev/ttyHS*
crw-rw---- 1 root dialout 251, 0 2008-12-01 22:10 /dev/ttyHS0
crw-rw---- 1 root dialout 251, 1 2008-12-01 22:45 /dev/ttyHS1
crw-rw---- 1 root dialout 251, 2 2008-12-01 22:10 /dev/ttyHS2
crw-rw---- 1 root dialout 251, 3 2008-12-01 22:10 /dev/ttyHS3

if I do - :~$ grep dialout /etc/group
I am in the group

versions off my installs
Ubuntu 8.10
hsoconnect-py2.5  - 1.1.128
hsolink           - 1.0.118-1
hso-1.6.tar.gz
udev.tar.gz

Thanks

---

### Post by I-Broke-It on 2008-12-02
The Huawei e220 that I borrowed till I get my modem working has stop working on the ubuntu 8.10 since the install so this I am writing from another PC. Is this a bug.

I read something in the read-me that caught my eye it said the HSO driver create a /dev/wmodum0 so I put it in the wvdial.config file and gave it a spin. It looks a lot closer even though I would have liked it better for the HSO software to work.

I have attached the results off the wvdial there is the terminal output as well as the related message file messages. If some one can say if I am on the right track it would be appreciated. A good push in the right direction will help a lot as well.

Thanks.

---

### Post by Pharscape on 2008-12-03
I do not see any connect requests in the hso logs you  provided - it looks like HSOconnect restarts is that correct?

The wvdial script looks ok except I see you have used lots of init commands that are not normally needed at all.

I will try the same wvdial script my self and will let you know my results.

What wvdial ppp parameters are you using?

Paul

---

### Post by I-Broke-It on 2008-12-03
Thanks Paul

**_HSO_**

The HSO after connect just restarts that is correct :sad:. Is there a way that I can debug it or to get more info on the problem on my PC. I do not know Python but I have 10 years of experience coding (IBM Universe) - it is how I feed my family.

**_wvdial_**

I have no Idea what you mean by ppp parameters how do I get them for you?

I have tried to take the init commands out it made the situation worse. I got this config from the web. There was a site/thread that gave examples for the different countries. I took mine for South Africa

Thanks again for all the trouble.

---

### Post by I-Broke-It on 2008-12-05
We had a power outtage so no new developments. I am going to get python tools to see if I cannot see why the HSO is just restarting or at least where it is restarting. 

I also will try to get my Huawei e220 to work again.

---

### Post by I-Broke-It on 2008-12-10
It took a while but after the 4th install i had windows XP installed on my laptop. I had to reinstall Ubuntu as windows well is windows does not want to go second :( or let say cannot go second. 

Any way my card works ?!?. I wonder now if it is the driver or the switch that switch the card on or off that is the problem (the switch works in windows, The wireless and blue tooth switch work in Ubuntu).

I have updated all the software in the update manager now so I will reinstall the driver again and see what the outcome sill be. 

Please hold thumbs for me I would really like this to work

---

### Post by I-Broke-It on 2008-12-16
OK, I have reinstalled every thing my dmesg looks as follows for the HSO - not very promising. 

~$ dmesg |grep hso
[   15.065775] hso: /home/steven/Desktop/hso-1.6/hso.c: 1.6-Option Option Wireless
[   15.067476] usbcore: registered new interface driver hso
[  137.338048] hso0: Disabled Privacy Extensions


does this make any sense to anyone.

Thanks

---

### Post by Pharscape on 2008-12-16
According to your latest messges your driver is installed and working.

Compare what you get with my HOW-To
[http://pharscape.org/HSOconnect-Ubuntu-8.04.html](http://pharscape.org/HSOconnect-Ubuntu-8.04.html)

FYI: I have never needed any special init commands except ATE1. 

By the way Python tools are not required for the hso kernel module. But HSOconnect uses python.

So ```
python -m hsoc
``` should launch HSOconnect or produce some debug output for you.

---

### Post by I-Broke-It on 2008-12-16
Thanks for the reply it is much appreciated. I checked I can connect via Windows on that card so every thing work in the sense of hardware, sim ect.

I start the hsoc as you suggested but it does not work I get the following. Terminal and debug window output. This is after I press the connect button.

Hope you can make sense off it. 

Thanks.

##########################################################################################

$ python -m hsoc
False
Path to hsolinkcontrol: /usr/bin/hsolinkcontrol
36333
Mode 36333
<dbus.service.BusName org.pharscape.HSOconnect.Service on <dbus._dbus.SessionBus (session) at 0x8e10efc> at 0xb7e17d6c>
called init <hsoc.bin.userinterface.HSOGUI at /hsoc at 0xb7e17d0c>
init serial
ser done 
running
run
Serial<id=0x8e4b84c, open=True>(port='/dev/ttyHS1', baudrate=115200, bytesize=8, parity='N', stopbits=1, timeout=1, xonxoff=0, rtscts=0)
checkpin() returned: READY
pre status--------------
Closed port
Quit gtk.main
end run
Path to hsolinkcontrol: /usr/bin/hsolinkcontrol
36333
Mode 36333
<dbus.service.BusName org.pharscape.HSOconnect.Service on <dbus._dbus.SessionBus (session) at 0x8e10efc> at 0xb7e17d6c>
called init <hsoc.bin.userinterface.HSOGUI at /hsoc at 0x8e4b32c>
init serial
ser done 
running
run
Serial<id=0x8e50e8c, open=True>(port='/dev/ttyHS1', baudrate=115200, bytesize=8, parity='N', stopbits=1, timeout=1, xonxoff=0, rtscts=0)
checkpin() returned: READY
pre status--------------


#############################################################################################################################################
The Debug Window
Init serPort /dev/ttyHS1Detected
Port open
'AT'
'OK
''AT+CFUN?'
'+CFUN: 0
'
'
'
'OK
''AT+CFUN=1'
'+CME ERROR: operation not allowed
'

'ATE1'
'OK
''AT+CLCK="SC",2'
'+CLCK: 0
'
'
'
'OK
''AT+cpin?'
'+CPIN: READY
'
'
'
'OK
''AT_OBLS'
'_OBLS: 1,1,1
'
'
'
'OK
''AT_OBLS'
'_OBLS: 1,1,1
'
'
'
'OK
''AT_OWANCALL=1,0,0''OK''ATE1'
'OK
'(1, 'OK')'ATI'
'Manufacturer: Option N.V.
'
'Model: GTM380
'
'Revision: 2.12.0Hd (Date: May 27 2008, Time: 11:19:10)
'(1, 'Manufacturer: Option N.V.')'AT_OPMN'
'

'@'_OPMN: GTM380E
'
'
'
'OK
'(1, '_OPMN: GTM380E')'AT_OCTI=1'
'OK
'(1, 'OK')'AT_OSSYS=1'
'OK
'(1, 'OK')'AT_OPSYS=3,2'
'ERROR
'(1, 'ERROR')'AT_OSQI=1'
'OK
'(1, 'OK')'AT+CNMI=2,1,0,1,0'
'OK
'(1, 'OK')'AT+CREG=1'
'OK
'(1, 'OK')'AT+CGREG=1'
'OK
'(1, 'OK')'AT+COPS=3,0'
'OK
'(1, 'OK')'AT+CGMI'
'Option N.V.
'
'
'
'OK
'(1, 'Option N.V.')'AT+GMR'
'2.12.0Hd (Date: May 27 2008, Time: 11:19:10)
'
'
'
'OK
'(1, '2.12.0Hd (Date: May 27 2008, Time: 11:19:10)')'AT+CGSN'
'357564010479156,PE297BF2XS
'
'
'
'OK
'(1, '357564010479156,PE297BF2XS')Sending ->AT+csq<<AT+csq>>
<<+CSQ: 0,99>>
<<OK>>
Sending ->AT+cgreg?<<AT+cgreg?>>
<<+CGREG: 1,0>>
<<OK>>
Sending ->AT+COPS?<<AT+COPS?>>
<<+COPS: 0>>
<<OK>>
Sending ->AT_OPSYS?<<AT_OPSYS?>>
<<_OPSYS: 3,2>>
<<OK>>
Sending ->AT+CSQ<<AT+CSQ>>
<<+CSQ: 0,99>>
<<OK>>
Sending ->AT+CGREG?<<AT+CGREG?>>
<<+CGREG: 1,0>>
<<OK>>
Sending ->AT+cops?<<AT+cops?>>
<<+COPS: 0>>
<<OK>>
Sending ->AT+cops?<<AT+cops?>>
<<+COPS: 0>>
<<OK>>

---

### Post by TpyKv on 2009-02-02
Good morning,

Did anyone find a resolution to this problem?

I am having exactly the same issue... the HSIcDbg is running in the background... will not let me connect... it just grey's out.. and will not respond. 

It worked before in hardy! in fact am going to back to hardy after intrepid keeps locking my out with a caps lock blink, another issue that has gone unresolved....

I am finding problems I did not have before, so frustrating - has anyone reported this as a bug?

---

### Post by I-Broke-It on 2009-02-03
Sorry no workable solution supplied yet :(

---

### Post by edmond. on 2009-03-19
I resolved on linux4one!
[http://www.edmond.netsons.org/index.php/2009/03/19/aspire-one-linux-e-modem-hsdpa-hsupa-option-gtm380-globetrotter/](http://www.edmond.netsons.org/index.php/2009/03/19/aspire-one-linux-e-modem-hsdpa-hsupa-option-gtm380-globetrotter/)

ciao 
edmond

---

