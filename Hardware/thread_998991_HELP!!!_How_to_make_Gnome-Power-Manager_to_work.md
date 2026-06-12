---
title: "HELP!!! How to make Gnome-Power-Manager to work???"
date: 2008-12-01
forum: Hardware
---

### Post by dirac14 on 2008-12-01
Hello dear ubunters! I recently bought a new Toshiba Satellite A300D laptop (with amd athlon x2 64)and run Ubuntu 8.10(32bit) on it. My problem is that the battery icon always indicates that my laptop is on AC battery supply and does not even recognize the battery.It seems to me that something is being done wrongly by the system because power manager once (and only once!) did recognize the battery and the usual icon with remaining time etc appeared.
Is there any idea what should i do to fix that irritating problem??I am relatively new in ubuntu so please forgive my ignorance.
Thank you all in advance!

---

### Post by galv on 2008-12-01
> **dirac14 said:**
> Hello dear ubunters! I recently bought a new Toshiba Satellite A300D laptop (with amd athlon x2 64)and run Ubuntu 8.10(32bit) on it. My problem is that the battery icon always indicates that my laptop is on AC battery supply and does not even recognize the battery.It seems to me that something is being done wrongly by the system because power manager once (and only once!) did recognize the battery and the usual icon with remaining time etc appeared.
Is there any idea what should i do to fix that irritating problem??I am relatively new in ubuntu so please forgive my ignorance.
Thank you all in advance!

I have similar issues with my laptop, ASUS F5GL/X50GL with Intel CPU and a Nvidia card ...

---

### Post by dirac14 on 2008-12-03
Please can anybody help?

---

### Post by tommcd on 2008-12-03
Run lsmod in terminal to see what modules are loaded by the system. For the battery icon to work you need to have the **ac** and **battery** modules running. If you don't see them in the output of lsmod, you can load them with "sudo modprobe ac" and "sudo modprobe battery". 
Other modules you may need running are: **fan, processor, thermal, button**. Check lsmod for them also.

Run this in terminal:
```
 cat /proc/acpi/battery/BAT1/state
```
You may have BAT0 instead of BAT1 on your system. When on ac power the output will look something like:
```

tom@ubuntu:~$ cat /proc/acpi/battery/BAT1/state 
present:                 yes
capacity state:          ok
charging state:          charged
present rate:            65533 mA
remaining capacity:      6511 mAh
present voltage:         12526 mV

``` 
and when on battery power, if the battery is recognized:
```

tom@ubuntu:~$ cat /proc/acpi/battery/BAT1/state 
present:                 yes
capacity state:          ok
charging state:          discharging
present rate:            1953 mA
remaining capacity:      6507 mAh
present voltage:         12135 mV

```
Problems getting the battery monitor to work are usually acpi related.

---

### Post by dirac14 on 2008-12-03
Thank you for replying tommcd. Allow me one last question..How to run Ismod in the terminal??

---

### Post by tommcd on 2008-12-03
> **dirac14 said:**
> Thank you for replying tommcd. Allow me one last question..How to run Ismod in the terminal??

Just click on: applications > accesories > terminal. This will open the terminal on your desktop. Then run **lsmod**. 
The command lsmod = **l**i**s**t **mod**ules. It will output all the modules running on your system.
 Look to see if **ac** and **battery** are running. Also look for the modules: **fan proceesor thermal button**.

---

### Post by dirac14 on 2008-12-03
Module                  Size  Used by
ipv6                  263972  10 
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
powernow_k8            22148  0 
cpufreq_conservative    14600  0 
cpufreq_ondemand       14988  2 
cpufreq_userspace      11396  0 
cpufreq_stats          13188  0 
freq_table             12672  3 powernow_k8,cpufreq_ondemand,cpufreq_stats
cpufreq_powersave       9856  0 
container              11520  0 
pci_slot               12552  0 
sbs                    19464  0 
sbshc                  13440  1 sbs
iptable_filter         10752  0 
ip_tables              19600  1 iptable_filter
x_tables               22916  1 ip_tables
sbp2                   29324  0 
parport_pc             39204  0 
lp                     17156  0 
parport                42604  3 ppdev,parport_pc,lp
joydev                 18368  0 
snd_seq_dummy          10884  0 
snd_seq_oss            38528  0 
snd_seq_midi           14336  0 
snd_rawmidi            29824  1 snd_seq_midi
snd_hda_intel         381872  2 
snd_seq_midi_event     15232  2 snd_seq_oss,snd_seq_midi
snd_pcm_oss            46848  0 
snd_mixer_oss          22784  1 snd_pcm_oss
psmouse                45200  0 
i2c_piix4              16144  0 
serio_raw              13444  0 
pcspkr                 10624  0 
uvcvideo               62728  0 
snd_seq                57776  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
compat_ioctl32          9344  1 uvcvideo
videodev               41344  1 uvcvideo
evdev                  17696  12 
i2c_core               31892  1 i2c_piix4
v4l1_compat            22404  2 uvcvideo,videodev
snd_seq_device         15116  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd_pcm                83204  2 snd_hda_intel,snd_pcm_oss
sdhci_pci              15360  0 
sdhci                  23940  1 sdhci_pci
mmc_core               58268  1 sdhci
snd_timer              29960  2 snd_seq,snd_pcm
snd                    63268  13 snd_seq_oss,snd_rawmidi,snd_hda_intel,snd_pcm_oss,snd_mixer_oss,snd_seq,snd_seq_device,snd_pcm,snd_timer
soundcore              15328  1 snd
fglrx                1861644  32 
snd_page_alloc         16136  2 snd_hda_intel,snd_pcm
agpgart                42184  1 fglrx
video                  25104  0 
output                 11008  1 video
wmi                    14504  0 
battery                18436  0 
ac                     12292  0 
button                 14224  0 
shpchp                 37908  0 
pci_hotplug            35236  1 shpchp
usbhid                 35840  0 
hid                    50560  1 usbhid
ext3                  133256  1 
jbd                    55444  1 ext3
mbcache                16004  1 ext3
sr_mod                 22212  0 
cdrom                  43168  1 sr_mod
sd_mod                 42392  3 
crc_t10dif              9984  1 sd_mod
ata_generic            12932  0 
sg                     39732  0 
pata_acpi              12160  0 
ohci1394               37936  0 
ieee1394               96324  2 sbp2,ohci1394
ohci_hcd               32016  0 
ehci_hcd               43404  0 
ahci                   37132  2 
pata_atiixp            12800  0 
sky2                   53380  0 
usbcore               149360  5 uvcvideo,usbhid,ohci_hcd,ehci_hcd
libata                177440  4 ata_generic,pata_acpi,ahci,pata_atiixp
scsi_mod              155212  5 sbp2,sr_mod,sd_mod,sg,libata
dock                   16656  1 libata
thermal                23708  0 
processor              42156  2 powernow_k8,thermal
fan                    12548  0 
fbcon                  47648  0 
tileblit               10880  1 fbcon
font                   16512  1 fbcon
bitblit                13824  1 fbcon
softcursor              9984  1 bitblit
fuse                   60828  3

---

### Post by tommcd on 2008-12-03
You lsmod show that ac, battery, fan, button, processor, and thermal are running. So it looks like you have all of the modules running.
What is the output of this when running on battery:
 cat /proc/acpi/battery/BAT1/state (your system may use BAT0 instead of BAT1).

---

### Post by dirac14 on 2008-12-03
The output of "cat /proc/acpi/battery/BAT1/state" is : "present: no ".
Furthermore, if it is a useful comment, in the power manager window there is no battery tablet. I remind that the battery icon appeared only once (out of the blue) and seemed to function properly..Since then..nothing

---

### Post by tommcd on 2008-12-04
> **dirac14 said:**
> The output of "cat /proc/acpi/battery/BAT1/state" is : "present: no ".

Make sure you try that with BAT0 also.
1. You have all the required modules loaded as per the output of lsmod you posted.
2. cat /proc/acpi/battery/BAT1/state (and I presume BAT0 also) does not recognize your battery.

To see if this is an acpi problem, run "acpi -b" in terminal while running on battery. You should see something like this:
```

tom@ubuntu:~$ acpi -b
     Battery 0: Full, 100%

```
and for AC power:
```

tom@ubuntu:~$ acpi -a
     Battery 0: Full, 100%
  AC Adapter 0: on-line

```

The only other thing I can think of is to try adding **acpi=force** to the kernel line for booting Ubuntu in /boot/grub/menu.lst. This is just a guess, though it can't hurt to try it. 
First, back up menu.lst:
```
sudo cp /boot/grub/menu.lst /boot/grub/menu.lst.bak
```
Then run "gksudo gedit /boot/grub/menu.lst". Scroll down to the  ## End Default Options ## section, and just add acpi=force to the end of the kernel line. Then save and exit. Then reboott and see if the battery monitor works. If this doesn't help, then re-edit /boot/grub/menu.lst and remove acpi=force that you added.

---

### Post by dirac14 on 2008-12-04
> **tommcd said:**
> Make sure you try that with BAT0 also.
1. You have all the required modules loaded as per the output of lsmod you posted.
2. cat /proc/acpi/battery/BAT1/state (and I presume BAT0 also) does not recognize your battery.

To see if this is an acpi problem, run "acpi -b" in terminal while running on battery. You should see something like this:
```

tom@ubuntu:~$ acpi -b
     Battery 0: Full, 100%

```
and for AC power:
```

tom@ubuntu:~$ acpi -a
     Battery 0: Full, 100%
  AC Adapter 0: on-line

```


It gives me the following after running acpi-b and acpi-a :
```

ilias@ilias-laptop:~$ acpi -a
  AC Adapter 0: off-line
ilias@ilias-laptop:~$ acpi -b
ilias@ilias-laptop:~$ 

```

I can't understand..

---

### Post by tommcd on 2008-12-05
Well, I can't understand it either. Sorry, but I'm out of ideas. I tried searching for battery problems with your laptop in linux, but I did not find anything. Obviously, the acpi system in the kernel can't find your battery. This is likely due to some proprietary (secret) acpi implementation from Toshiba. I have the same sort of problem with the wireless on my Acer laptop. I had to buy a wireless card to get wireless working on this laptop.

---

### Post by dirac14 on 2008-12-05
Anyway, thanks a lot for your time and replies!

---

### Post by galv on 2008-12-05
> **dirac14 said:**
> Anyway, thanks a lot for your time and replies!

I think that issues are related do ACPI support in the kernel. I've seen some bug reports on this. I've been hopping for a new kernel version/update to solve this (I have a problem also).
If you activate the propose repositories you will get a new kernel sooner.

---

### Post by TheMaskedman on 2008-12-05
I can confirm that kernel 2.6.27-9-generic in Intrepid does not recognize the existence of my battery in my Toshiba A300D. Suspend/hibernate does work, however. The real strange thing is if you hibernate then resume, the battery is detected.

I could swear that my battery was recognized in the live cd when I installed Intrepid. When I get a chance I will reboot and confirm.

---

### Post by TheMaskedman on 2009-02-24
I seem to have solved this issue by using the kernel option acpi_osi="Linux"

I added it to my default GRUB options:

## ## Start Default Options ##
## default kernel options
## default kernel options for automagic boot options
## If you want special options for specific kernels use kopt_x_y_z
## where x.y.z is kernel version. Minor versions can be omitted.
## e.g. kopt=root=/dev/hda1 ro
##      kopt_2_6_8=root=/dev/hdc1 ro
##      kopt_2_6_8_2_686=root=/dev/hdc2 ro
# kopt=root=/dev/sda2 acpi_osi="Linux" ro

then ran sudo update-grub to update the menu.lst

Can somebody else confirm that this has solved their issue? I have tried a few things but this is what seems to have solved it for me.

---

### Post by tommcd on 2009-02-25
TheMaskedman,
Are you running a Toshiba laptop? And the same model as the OP?
> **TheMaskedman said:**
>  acpi_osi="Linux"

That is a new one on me. Just out of curiosity, where did you find it?
I will have to write that down for future reference.

---

### Post by TheMaskedman on 2009-02-25
I am running a Toshiba A300D-MK3 (psak9c-mk309c). 

I had the following issues:
[LIST]
[*]Battery would not show up in gnome-power-manager or in /proc/acpi/battery
[*]When I tried to shutdown using the shutdown button or shutdown -h 0 it would reboot instead of halting
[*]The Fn+F6/F7 keys would not adjust the screen brightness
[/LIST]

Adding acpi_osi="Linux" to the kernel options solved those ACPI issues. 

I found that option [**here**]("http://www.alexkidd.altervista.org/alien/debianizzato_a300d_14r.html") (Parametri speciali per il kernel: acpi_osi=”Linux” per evitare malfunzionamenti di ACPI) I assumed malfunzionamenti meant malfunction so I gave it a try and it seems to have cleared up my problems.

---

### Post by tommcd on 2009-02-26
Good find TheMaskedman!
Hopefully the OP Dirac14 will see this and try it.

---

