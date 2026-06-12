---
title: "resolution problems"
date: 2008-11-29
forum: General Help
---

### Post by konlord on 2008-11-29
My ubuntu (8.04) will only offer me 640x480 at the moment when I need 1024x768

note:I have an nvidia driver already installed in the restricted drivers but I dont see how that will help to change my screen resolution...If theres any manuals or anything for this please give me a link or just post some suggestions

Also..When I installed nvidia it brung my screen resolution down further to 640x480 which is even worse than what I had at 800x600.

---

### Post by eternalnewbee on 2008-11-29
Go to: **Main Menu > System > Preferences > Screen Resolution**, and try it from there.

---

### Post by konlord on 2008-11-30
Doesn't work or this problem would've been solved a really long time ago all that offers is 640x480(what I have now) & 360x240(no one will ever need that lol) 

more suggestions please

---

### Post by Keyper7 on 2008-11-30
It seems that something went wrong in the driver installation. It's possible that you are currently not using the nvidia driver at all, but a generic one.

Please post the output of

```
lsmod
```

and

```
xrandr
```

PS: it might take an entire day to check your reply to this, but I will

---

### Post by konlord on 2008-11-30
lsmod:


Module                  Size  Used by
ipv6                  267780  10 
af_packet              23812  2 
rfcomm                 41744  2 
l2cap                  25728  13 rfcomm
bluetooth              61156  4 rfcomm,l2cap
ppdev                  10372  0 
powernow_k8            16704  1 
cpufreq_ondemand        9740  1 
cpufreq_userspace       5284  0 
cpufreq_conservative     8712  0 
cpufreq_powersave       2688  0 
cpufreq_stats           7104  0 
freq_table              5536  3 powernow_k8,cpufreq_ondemand,cpufreq_stats
video                  19856  0 
output                  4736  1 video
dock                   11280  0 
sbs                    15112  0 
sbshc                   7680  1 sbs
container               5632  0 
battery                14212  0 
iptable_filter          3840  0 
ip_tables              14820  1 iptable_filter
x_tables               16132  1 ip_tables
ac                      6916  0 
sbp2                   24072  0 
lp                     12324  0 
joydev                 13120  0 
snd_hda_intel         344856  3 
snd_pcm_oss            42144  0 
snd_mixer_oss          17920  1 snd_pcm_oss
sky2                   47620  0 
snd_pcm                78596  2 snd_hda_intel,snd_pcm_oss
snd_page_alloc         11400  2 snd_hda_intel,snd_pcm
snd_hwdep              10500  1 snd_hda_intel
snd_seq_dummy           4868  0 
snd_seq_oss            35584  0 
snd_seq_midi            9376  0 
snd_rawmidi            25760  1 snd_seq_midi
snd_seq_midi_event      8320  2 snd_seq_oss,snd_seq_midi
nvidia               7825536  34 
snd_seq                54224  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              24836  2 snd_pcm,snd_seq
snd_seq_device          9612  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
led_class               6020  0 
button                  9232  0 
snd                    56996  17 snd_hda_intel,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_hwdep,snd_seq_dummy,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
agpgart                34760  1 nvidia
i2c_nforce2             7680  0 
wmi_acer                9644  0 
evdev                  13056  4 
k8temp                  6656  0 
soundcore               8800  1 snd
i2c_core               24832  2 nvidia,i2c_nforce2
parport_pc             36260  1 
parport                37832  3 ppdev,lp,parport_pc
shpchp                 34452  0 
pci_hotplug            30880  1 shpchp
pcspkr                  4224  0 
ext3                  136840  1 
jbd                    48404  1 ext3
mbcache                 9600  1 ext3
sr_mod                 17956  0 
cdrom                  37408  1 sr_mod
usb_storage            73664  0 
sg                     36880  0 
libusual               19108  1 usb_storage
sd_mod                 30720  5 
usbhid                 32128  0 
hid                    38784  1 usbhid
pata_amd               14212  0 
ata_generic             8324  0 
sata_nv                27528  3 
ehci_hcd               37900  0 
pata_acpi               8320  0 
ohci1394               33584  0 
ohci_hcd               26640  0 
libata                159344  4 pata_amd,ata_generic,sata_nv,pata_acpi
ieee1394               93752  2 sbp2,ohci1394
scsi_mod              151436  6 sbp2,sr_mod,usb_storage,sg,sd_mod,libata
usbcore               146412  6 usb_storage,libusual,usbhid,ehci_hcd,ohci_hcd
thermal                16796  0 
processor              37384  2 powernow_k8,thermal
fan                     5636  0 
fbcon                  42912  0 
tileblit                3456  1 fbcon
font                    9472  1 fbcon
bitblit                 6784  1 fbcon
softcursor              3072  1 bitblit
fuse                   50708  5 


xrandr:

Screen 0: minimum 320 x 240, current 640 x 480, maximum 640 x 480
default connected 640x480+0+0 0mm x 0mm
   640x480        50.0* 
   320x240        51.0

---

### Post by konlord on 2008-11-30
If anyone else had suggestions please post

---

### Post by Adanac on 2008-11-30
I seem to be having very similar problems, no idea how to fix it though. You can try getting rid of the restricted driver though, that might allow you to use a full resolution, at least thats how it works for me haha. When I install the driver though is when the screen resolution shrinks.

If you can you can also try another monitor. Is your monitor also a TV?

---

### Post by konlord on 2008-12-01
I don't have any other monitors and even when the driver is uninstalled I am only capable of having 800x600 resolution when I need 1024x768

---

### Post by slinkey1981 on 2008-12-01
You can try installing EnvyNG, (recommended)

```
 sudo aptitude install envyng-core envyng-gtk
```

Or, you can try to follow my (amusing) [trial by fire]("http://ubuntuforums.org/showthread.php?t=986460") for using the newer Nvidia 180 Beta driver.  (NOT RECOMMENDED)

---

### Post by blackened on 2008-12-01
Start with manually setting your monitor's available ranges in xorg.conf first, then if that doesn't fix it you can muck around with drivers. See [http://ubuntuforums.org/showthread.php?t=997482]("http://ubuntuforums.org/showthread.php?t=997482") Post #2. It's an easy and quick fix (also easily reversible if it doesn't do anything).

---

### Post by dariusdwtt on 2008-12-02
do you have nvidia-settings installed?
helped me a bunch.
but will show correct resolution and refresh rate in nvidia gui, and in screen resolution gui in system>preferences it shows bogus numbers...

---

### Post by loomsen on 2008-12-02
This all will not fix the problem. You probably have a messed up xorg.conf which cannot be parsed, you Xorg.log will tell you.

**cat /var/log/Xorg.0.log**

(If it doesn't tell you, just post your log here)

If you have an apropriate driver installed for your video dev run 
**nvidia-xconfig** 
from a terminal as root and restart your X-Server.
It might be a good idea to remove your current xorg.conf before running nvidia-xconfig cause nv-xc will try and merge the generic xorg.conf with your custom one. So step by step (!don't forget a step, and make sure you make EVERY step!) After you ensured you have the right driver installed:

```

sudo rm /etc/X11/xorg.conf
sudo nvidia-xconfig
sudo reboot   [color=blue] if your familiar with shells and howto initiate a x-server restart you might do that as well[/color]

```

---

