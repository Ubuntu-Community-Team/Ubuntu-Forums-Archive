---
title: "Soundcore missing"
date: 2009-09-26
forum: Installation &amp; Upgrades
---

### Post by xxxYYY on 2009-09-26
How do you install soundcore driver permanently?

My sound card works after running 

sudo aptitude --purge reinstall linux-sound-base alsa-base alsa-utils linux-image-`uname -r` linux-ubuntu-modules-`uname -r` libasound2

sudo modprobe snd-emu10k1

However, after rebooting the modules are gone.  Completely.  Where did they go?

----------------------------------------------------
Sort of solution (from my last post)
OK, here's what I did

After doing the

sudo aptitude --purge reinstall linux-sound-base alsa-base alsa-utils linux-image-`uname -r` linux-ubuntu-modules-`uname -r` libasound2

and

sudo modprobe snd-emu10k1

I then copied the directory tree
/lib/modules/2.6.24-xx-xxx/kernel/sounds/
to a safe place under my directory. (cp -r)

I guess the command would be
cd <safe directory>
cp -r /lib/modules/`uname -r`/kernel/sound .

(note: probably could just copy directly out of the ../kernel subdirectory)

Then copied it to
/lib/modules/2.6.24-xx-xxx/
sudo cp -r sound /lib/modules/`uname -r`/
(don't do this if you already have a "sound" directory there

Then I ran
sudo depmod

Then rebooted. The directory /lib/modules/`uname -r`/sound persisted, whereas the /lib/modules/`uname -r`/kernel/sound had not.

---

### Post by rreese6 on 2009-09-26
It has been quite a while since I have done this, but I think you
can do this:
```

cd /etc/modules.d
sudo nano alsa-base
```

Check for the floowing line. add it if you don't find it.

```
install snd-emu10k1 /sbin/modprobe --ignore-install snd-emu10k1 $CMDLINE_OPTS &&
 { /sbin/modprobe -Qb snd-emu10k1-synth ; }

```

hit CTRL X to exit, Save and try to reboot....it nags me a bit that I am missing something..but we will try this first.

I am back, do a lsmod and see if snd-emu10k1 is there
if not you may want add "snd-emu10k1" (no quoates) to /etc/modules
```
cd /etc
sudo nano modules

```
Add snd-emu10k1 to the end
CTRL X you exit, Save and ether restart Alsa or just reboot.

---

### Post by xxxYYY on 2009-09-26
Thank you, that line is there already

---

### Post by rreese6 on 2009-09-26
But when you did a reboot the module is missing?
from lsmod | grep snd

and is it listed in the modules file under /etc?

---

### Post by xxxYYY on 2009-09-26
Yes,
and soundcore (.ko) and the other modules it depends on

---

### Post by xxxYYY on 2009-09-26
Yes, after reboot they're all missing, I mean

---

### Post by rreese6 on 2009-09-26
could you post your lsmod here?

---

### Post by rreese6 on 2009-09-26
do  you mean the the driver file is missing from:
/lib/modules/2.6.24-xx-xxx/kernel/sounds/
?? or is it that the Module is not being loaded on reboot?

What your problem appears to me to be is that once you do the purge and reinstall then you insert the module into the kernel all is well. once you reboot and do a lsmod the snd-emu10k1 module is gone.
Am I correct?
If so then we just need to make sure the module loads at every boot is my thinking.
but if lsmod shows the module loaded, then it may just be a case of setting some options for the sound card.

---

### Post by xxxYYY on 2009-09-26
After reboot, lsmod:
Module                  Size  Used by
ac97_bus               11264  0
snd_page_alloc         21136  0
rfcomm                 54560  2
l2cap                  35968  13 rfcomm
bluetooth              74788  4 rfcomm,l2cap
oss_usb               137268  0
oss_sbxfi              54720  0
osscore               616260  2 oss_usb,oss_sbxfi
ppdev                  18568  0
acpi_cpufreq           18448  0
cpufreq_userspace      14468  0
cpufreq_conservative    17800  0
cpufreq_powersave      10368  0
cpufreq_stats          16032  0
cpufreq_ondemand       18320  2
freq_table             14080  3 acpi_cpufreq,cpufreq_stats,cpufreq_ondemand
container              13824  0
video                  30612  0
output                 12800  1 video
dock                   20128  0
sbs                    24976  0
sbshc                  16128  1 sbs
battery                23944  0
iptable_filter         11776  0
ip_tables              31720  1 iptable_filter
x_tables               30728  1 ip_tables
ipv6                  326280  30
aes_x86_64             34088  0
dm_crypt               23944  0
dm_mod                 78200  1 dm_crypt
ac                     15496  0
lp                     22084  0
loop                   28676  0
af_packet              34440  2
usblp                  24832  0
emu10k1_gp             12800  0
wmi_acer               18244  0
gameport               25104  2 emu10k1_gp
button                 18080  0
serio_raw              16260  0
parport_pc             48296  1
parport                51340  3 ppdev,lp,parport_pc
shpchp                 45340  0
pci_hotplug            41776  1 shpchp
iTCO_wdt               22480  0
iTCO_vendor_support    12932  1 iTCO_wdt
evdev                  22144  3
psmouse                53404  0
pcspkr                 12160  0
ext3                  156176  3
jbd                    64168  1 ext3
mbcache                18560  1 ext3
sg                     48920  0
sr_mod                 27300  0
cdrom                  48680  1 sr_mod
sd_mod                 40448  6
floppy                 76264  0
ahci                   40452  5
libata                183984  1 ahci
scsi_mod              185784  4 sg,sr_mod,sd_mod,libata
ehci_hcd               49164  0
uhci_hcd               37024  0
tg3                   131972  0
usbcore               177200  5 oss_usb,usblp,ehci_hcd,uhci_hcd
thermal                26912  0
processor              48712  4 acpi_cpufreq,thermal
fan                    13960  0
fbcon                  53504  0
tileblit               11392  1 fbcon
font                   17280  1 fbcon
bitblit                14592  1 fbcon
softcursor             10880  1 bitblit
fuse                   63280

---

### Post by xxxYYY on 2009-09-26
After the "aptitude --purge..." additional modules show up:
--------------------------------

Module                  Size  Used by
snd_emu10k1           175200  0
snd_ac97_codec        131544  1 snd_emu10k1
ac97_bus               11264  1 snd_ac97_codec
snd_util_mem           14592  1 snd_emu10k1
snd_hwdep              20232  1 snd_emu10k1
snd_pcm_oss            63136  0
snd_pcm               107528  3 snd_emu10k1,snd_ac97_codec,snd_pcm_oss
snd_page_alloc         21136  2 snd_emu10k1,snd_pcm
snd_mixer_oss          28032  1 snd_pcm_oss
snd_seq_oss            46592  0
snd_seq_midi           19392  0
snd_rawmidi            38560  2 snd_emu10k1,snd_seq_midi
snd_seq_midi_event     17408  2 snd_seq_oss,snd_seq_midi
snd_seq                74624  5 snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              36616  3 snd_emu10k1,snd_pcm,snd_seq
snd_seq_device         18068  5 snd_emu10k1,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    85864  14 snd_emu10k1,snd_ac97_codec,snd_util_mem,snd_hwdep,snd_pcm_oss,snd_pcm,snd_mixer_oss,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq_midi_event,snd_seq,snd_timer,snd_seq_device
soundcore              17568  1 snd

---

### Post by rreese6 on 2009-09-26
```
modprobe snd-emu10k1
sudo /etc/init.d/alsa-utils restart

```

test for sound

then post a new lsmod

---

### Post by rreese6 on 2009-09-26
Now that is strange
have you tried to do the purge
then just do a sudo alsa-utils restart?

---

### Post by xxxYYY on 2009-09-26
After I do the aptitude --purge etc, the soundcore.ko is in 

/lib/modules/2.6.24-xx-xxx/kernel/sounds/

The snd-emu10k1.ko is in 

/lib/modules/2.6.24-xx-xxx/updates/alsa/pci/emu10k1/ and also
/lib/modules/2.6.24-xx-xxx/ubuntu/sound/alsa-driver/pci/emu10k1/

However, after I reboot I'm pretty sure the soundcore.ko is nowhere on the disc.  I have to reboot (again) to be sure

---

### Post by rreese6 on 2009-09-26
You know sometimes (especially when it is late and I am tired) I forget the obvious solutions at times...
I remember a problem like this a few weeks back the guy and I worked through getting things installed and added modules. but still no sound..
it took us all the way to opening alsa-mixer in the terminal
and he noticed that PCM was set to zero from all of the changes we made.
this was with Ubuntu 9.04. Could this be true here?
I seem to remember it happened after the first reboot after an update.

---

### Post by xxxYYY on 2009-09-26
No, I can't open the mixer without the driver

---

### Post by xxxYYY on 2009-09-26
Sorry, the last lsmod was after the sudo modprobe snd-emu10k1


Before the modprobe and after the aptitude --purge reinstall, lsmod shows

Module                  Size  Used by
rfcomm                 54560  2
l2cap                  35968  13 rfcomm
bluetooth              74788  4 rfcomm,l2cap
oss_usb               137268  0
oss_sbxfi              54720  0
osscore               616260  2 oss_usb,oss_sbxfi
ppdev                  18568  0
acpi_cpufreq           18448  0
cpufreq_userspace      14468  0
cpufreq_conservative    17800  0
cpufreq_powersave      10368  0
cpufreq_stats          16032  0
cpufreq_ondemand       18320  2
freq_table             14080  3 acpi_cpufreq,cpufreq_stats,cpufreq_ondemand
container              13824  0
video                  30612  0
output                 12800  1 video
dock                   20128  0
sbs                    24976  0
sbshc                  16128  1 sbs
battery                23944  0
iptable_filter         11776  0
ip_tables              31720  1 iptable_filter
x_tables               30728  1 ip_tables
ipv6                  326280  30
aes_x86_64             34088  0
dm_crypt               23944  0
dm_mod                 78200  1 dm_crypt
ac                     15496  0
lp                     22084  0
loop                   28676  0
af_packet              34440  2
usblp                  24832  0
emu10k1_gp             12800  0
wmi_acer               18244  0
serio_raw              16260  0
gameport               25104  2 emu10k1_gp
button                 18080  0
iTCO_wdt               22480  0
iTCO_vendor_support    12932  1 iTCO_wdt
parport_pc             48296  1
parport                51340  3 ppdev,lp,parport_pc
evdev                  22144  3
psmouse                53404  0
pcspkr                 12160  0
shpchp                 45340  0
pci_hotplug            41776  1 shpchp
ext3                  156176  3
jbd                    64168  1 ext3
mbcache                18560  1 ext3
sg                     48920  0
sd_mod                 40448  6
sr_mod                 27300  0
cdrom                  48680  1 sr_mod
floppy                 76264  0
ahci                   40452  5
libata                183984  1 ahci
scsi_mod              185784  4 sg,sd_mod,sr_mod,libata
tg3                   131972  0
ehci_hcd               49164  0
uhci_hcd               37024  0
usbcore               177200  5 oss_usb,usblp,ehci_hcd,uhci_hcd
thermal                26912  0
processor              48712  4 acpi_cpufreq,thermal
fan                    13960  0
fbcon                  53504  0
tileblit               11392  1 fbcon
font                   17280  1 fbcon
bitblit                14592  1 fbcon
softcursor             10880  1 bitblit
fuse                   63280  3

---

### Post by rreese6 on 2009-09-26
now lsmod after sudo modprobe

---

### Post by xxxYYY on 2009-09-26
Thank you for your effort, its much appreciated.  I think I may try copying the soundcore tree tomorrow, but good night for now.

---

### Post by rreese6 on 2009-09-26
I am tired also..actually exhausted...lets' pick it up tomorrow..good night

---

### Post by xxxYYY on 2009-09-26
OK, here's what I did

After doing the 

sudo aptitude --purge reinstall linux-sound-base alsa-base alsa-utils linux-image-`uname -r` linux-ubuntu-modules-`uname -r` libasound2

and 

sudo modprobe snd-emu10k1

I then copied the directory tree
/lib/modules/2.6.24-xx-xxx/kernel/sounds/
to a safe place under my directory. (cp -r)

I guess the command would be 
cd <safe directory>
cp -r /lib/modules/`uname -r`/kernel/sound .

Then copied it to
/lib/modules/2.6.24-xx-xxx/
sudo cp -r sound /lib/modules/`uname -r`/
(don't do this if you already have a "sound" directory there

Then I ran
sudo depmod

Then rebooted.  The directory /lib/modules/`uname -r`/sound persisted, whereas the /lib/modules/`uname -r`/kernel/sound had not.

I can now successfully run 
sudo modprobe snd-emu10k1

And my sound card works.  Just have to figure out how to get it to load on boot.  Well this has been an education.:popcorn:

---

### Post by rreese6 on 2009-09-27
What is the make and model of your computer?
there is another method we might try/
also check to make sure Pulseaudio is not running
some people have trouble when using it/

Look at this post [http://ubuntuforums.org/showthread.php?t=1043568&highlight=intel+sound+database]("http://ubuntuforums.org/showthread.php?t=1043568&highlight=intel+sound+database")

---

