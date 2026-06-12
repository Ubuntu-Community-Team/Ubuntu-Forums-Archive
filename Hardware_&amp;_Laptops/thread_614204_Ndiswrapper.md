---
title: "Ndiswrapper"
date: 2007-11-15
forum: Hardware &amp; Laptops
---

### Post by qbox on 2007-11-15
I instaled wifi driver on ndiswrapper but I somehow unload ndiswrapper so I can try another drivers. How can I disable and enable ndiswrapper.
Thank you.

---

### Post by Digger78 on 2007-11-15
unload ndiswrapper

```
sudo rmmod ndiswrapper
```

load ndiswrapper

```
sudo modprobe ndiswrapper
```

---

### Post by qbox on 2007-11-16
Thank you ;)

---

### Post by qbox on 2007-11-17
hmmm its not working. Wifi Led going of and on. Ndiswrapper is working.

---

### Post by linuxonbute on 2007-11-17
Would you post the result of 
sudo lsmod

---

### Post by qbox on 2007-11-17
qbox@qbox:~$ sudo lsmod
[sudo] password for qbox:
Module                  Size  Used by
xt_TCPMSS               6656  1 
xt_tcpmss               3712  1 
xt_tcpudp               4864  1 
iptable_mangle          4352  1 
ip_tables              23464  1 iptable_mangle
x_tables               23432  4 xt_TCPMSS,xt_tcpmss,xt_tcpudp,ip_tables
i915                   30976  2 
drm                   106408  3 i915
binfmt_misc            14860  1 
rfcomm                 47656  2 
l2cap                  28672  11 rfcomm
bluetooth              63876  4 rfcomm,l2cap
vboxdrv              1648768  0 
nfsd                  272552  13 
exportfs                7808  1 nfsd
lockd                  76336  2 nfsd
sunrpc                198536  8 nfsd,lockd
ppdev                  11272  0 
ac                      7304  0 
video                  21140  0 
battery                12424  0 
sbs                    21520  0 
container               6400  0 
dock                   12264  0 
button                 10400  0 
acpi_cpufreq           10632  2 
cpufreq_ondemand       10896  0 
cpufreq_userspace       6048  1 
cpufreq_powersave       3072  0 
cpufreq_conservative     9608  0 
cpufreq_stats           8160  0 
freq_table              6464  3 acpi_cpufreq,cpufreq_ondemand,cpufreq_stats
pppoe                  18048  2 
pppox                   5648  1 pppoe
af_packet              28172  2 
ppp_generic            33440  6 pppoe,pppox
slhc                    8448  1 ppp_generic
ndiswrapper           243488  0 
sbp2                   27144  0 
parport_pc             41896  0 
lp                     15048  0 
parport                44172  3 ppdev,parport_pc,lp
joydev                 13440  0 
snd_hda_intel         378536  4 
snd_pcm_oss            48000  0 
snd_mixer_oss          20352  1 snd_pcm_oss
snd_pcm                94600  3 snd_hda_intel,snd_pcm_oss
snd_page_alloc         13584  2 snd_hda_intel,snd_pcm
snd_hwdep              12552  1 snd_hda_intel
snd_seq_oss            38912  0 
snd_seq_midi           11264  0 
snd_rawmidi            30336  1 snd_seq_midi
snd_seq_midi_event     10240  2 snd_seq_oss,snd_seq_midi
snd_seq                63648  5 snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              27656  3 snd_pcm,snd_seq
snd_seq_device         10772  4 snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
sdhci                  21004  0 
mmc_core               33416  1 sdhci
pcspkr                  4608  0 
intel_agp              30624  1 
psmouse                45596  0 
serio_raw               9092  0 
shpchp                 38300  0 
pci_hotplug            36612  1 shpchp
snd                    71720  16 snd_hda_intel,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_hwdep,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore              10272  1 snd
ipv6                  317192  12 
evdev                  13056  5 
ext3                  146576  1 
jbd                    69360  1 ext3
mbcache                11272  1 ext3
sg                     41384  0 
sr_mod                 19876  0 
sd_mod                 32512  3 
cdrom                  41768  1 sr_mod
ata_generic             9988  0 
b44                    32396  0 
ohci1394               38984  0 
ieee1394              109528  2 sbp2,ohci1394
mii                     7424  1 b44
ata_piix               20996  2 
libata                138928  2 ata_generic,ata_piix
scsi_mod              172856  5 sbp2,sg,sr_mod,sd_mod,libata
ehci_hcd               40076  0 
uhci_hcd               29600  0 
usbcore               161584  4 ndiswrapper,ehci_hcd,uhci_hcd
thermal                16528  0 
processor              36232  2 acpi_cpufreq,thermal
fan                     6920  0 
fuse                   52528  1 
apparmor               47008  0 
commoncap               9472  1 apparmor

---

### Post by linuxonbute on 2007-11-18
Sorry I have taken so long to reply.
I mean't to ask you to post the output from
```

ndiswrapper -l    

```

that's a lower case L

It should report a driver being loaded.
Mine says 
rt2500          driver installed, hardware present

---

### Post by qbox on 2007-11-18
> **linuxonbute said:**
> Sorry I have taken so long to reply.
I mean't to ask you to post the output from
```

ndiswrapper -l    

```


that's a lower case L

It should report a driver being loaded.
Mine says 
rt2500          driver installed, hardware present

qbox@qbox:~$ ndiswrapper -l
bcmwl5 : driver installed
        device (14E4:4328) present
qbox@qbox:~$ 

here is the output.
thank you

---

### Post by linuxonbute on 2007-11-18
> **qbox said:**
> qbox@qbox:~$ ndiswrapper -l
bcmwl5 : driver installed
        device (14E4:4328) present
qbox@qbox:~$ 

here is the output.
thank you

On my desktop PC I had an asus card which would not work with the bcmwl5 driver.

I seem to remember I had to use the bcmwl5a driver instead but I have also read that it is the Windows XP .inf and .sys files you need.

If you do the following 
```

ndiswrapper --help

```
it will show you the different options available and you can work from that.

Let me know how you get on and post back here when you are successful.

That way others can see what has worked for your PC and it may then help them.

---

### Post by qbox on 2007-11-18
the wifi card work but I cant do packet capture with ndiswrapper. so i want to test another drivers for my wifi card and i want to disable ndiswrapper when I testing.

---

### Post by linuxonbute on 2007-11-18
Then all you need to do is what digger78 said in the #2 post in this thread.

unload ndiswrapper

```


sudo rmmod ndiswrapper


```

try your other stuff out then when/if you finish with the other stuff unload it and then 
reload ndiswrapper
```


sudo modprobe ndiswrapper


```

---

### Post by malfist on 2007-11-18
what about 
```

sudo modprobe -r ndiswrapper
```

You can always remove the driver from ndiswrapper using```

sudo ndiswrapper -e drivername 
```

---

### Post by qbox on 2007-11-18
I dont want to remove driver I only want to disable it for a while

sudo modprobe -r ndiswrapper
sudo rmmod ndiswrapper
not working 
Wifi led going off and again on.

---

### Post by linuxonbute on 2007-11-18
> **qbox said:**
> I dont want to remove driver I only want to disable it for a while

sudo modprobe -r ndiswrapper
sudo rmmod ndiswrapper
not working 
Wifi led going off and again on.

Are you saying that the link AND the activity light go off and then come back on when you do either
```



sudo modprobe -r ndiswrapper


```
 or

```

sudo rmmod ndiswrapper

```

Try issuing one of those commands then try to ping some internet site

```

ping -c 4 152.46.7.80

```

let us know what happens.

---

### Post by linuxonbute on 2007-11-18
> **malfist said:**
> what about 
```

sudo modprobe -r ndiswrapper
```

You can always remove the driver from ndiswrapper using```

sudo ndiswrapper -e drivername 
```

Yes, you are right. rmmod doesn't remove the module from the kernel if it is in use.  ](*,)

---

### Post by qbox on 2007-11-18
I have DSL and wireless on my computer. I using only DSL for internet. I can remove ndiswrapper or remove driver but I dont want to do that. I only want to torn off for a while because if I dont have success with installing linux drivers for wifi I want to bring it back ndiswrapper when I need it.

---

### Post by linuxonbute on 2007-11-18
> **qbox said:**
> I have DSL and wireless on my computer. I using only DSL for internet. I can remove ndiswrapper or remove driver but I dont want to do that. I only want to torn off for a while because if I dont have success with installing linux drivers for wifi I want to bring it back ndiswrapper when I need it.

 Ah now I see your problem  :KS
```

modprobe -r ndiswrapper 

```
is taking it out of use. In other words turning it off!

you are not deleting it you are only stopping it

---

### Post by qbox on 2007-11-18
not working.
when I write sudo modprobe -r nndiswrapper wifi led going of and on.

---

### Post by linuxonbute on 2007-11-19
> **qbox said:**
> not working.
when I write sudo modprobe -r nndiswrapper wifi led going of and on.

Okay,

I am still not sure this has not worked. 

Try :
```

modprobe -r ndiswrapper

lsmod | grep ndiswrapper


```

If the lsmod command reports an output such as:
```

lsmod |grep ndiswrapper
ndiswrapper           187312  0 
usbcore               131480  4 ndiswrapper,ehci_hcd,uhci_hcd

```

Then ndiswrapper has not been unloaded ( i.e stopped)

If you get no output then it has unloaded.

---

### Post by qbox on 2007-11-24
sorry because Im late

qbox@qbox:~$ lsmod | grep ndiswrapper
ndiswrapper           243488  0 
usbcore               161584  4 ndiswrapper,ehci_hcd,uhci_hcd
qbox@qbox:~$ 

its isnt disabled.
another question. how can i activate and deactivate my wifi card?
Thank you

---

