---
title: "Dapper and Edgy can't mount my CD-Rom !!"
date: 2006-11-23
forum: Hardware &amp; Laptops
---

### Post by adam0509 on 2006-11-23
Hello all !



I got a big trouble with my CD-Rom drive...

In fact, I realize that I HAVE NEVER HAVE BEEN ABLE to mount this drive on dapper (and following : edgy...).

When using Live-CD, it freezes in the beginning of the process (mouting root files or sth like that...)
When using Alternate/server CD, it freezes after checking driver for the CD...


So, to install Ubuntu, I have to install **Breezy (who do not have problem with my drive)**, and then update to Dapper.



After dapper installation I can't mount any CDs. It even happens dapper to freeze completely at the beginning of X (I use Xubuntu btw) with an original CD of Gabriel Knight 3 !!!


So, I guess something, somewhere has been modified in the source-code...

My CD-Rom drive is a "**MITSUMI CR-4801TE**"


So, If you have any clue/idea...
Thanks in advance !

---

### Post by ingo on 2006-11-25
the whole mounting system has changed in 6.10

seems like you should stay in 6.06 and wait for the next release...

---

### Post by adam0509 on 2006-11-25
Hey

Thanks for the answer

Since the whole mouting system has change in 6.10, why am I unable to mount the CD on 6.06 ?

---

### Post by adam0509 on 2006-11-25
Errr


Just tested the dapper live-CD on a VAIO (SONY) Laptop from a friend, and seems it got exactly the same problem...


This is very worrying and anoying...

---

### Post by ingo on 2006-12-01
that is something I never fully understood, but I ran on Suse for a couple of years with never ending mounting problems. Even 10.1 wasn't perfect, although a  lot better than its predecessors. Then I changed to Kubuntu and things worked perfectly... Have you tried a different distro?

---

### Post by jbsra on 2006-12-01
Same thing happened with my Panasonic Toughbook. Earlier Ubuntus (5.10 & earlier) work fine. The 6.06 & 6.10 crash my CD. Its difficult to workaround.

---

### Post by adam0509 on 2006-12-03
seriously, so few answers, but that's a big trouble !

If a noob wants to try ubuntu, and the process stops at the beginning, he won't get further...

Couldn't we get something to choose betwin the 2 mouting system ?

---

### Post by adam0509 on 2006-12-09
[https://bugs.launchpad.net/distros/ubuntu/+bug/75097](https://bugs.launchpad.net/distros/ubuntu/+bug/75097)

---

### Post by ingo on 2006-12-09
that's what I call positive action :)

---

### Post by adam0509 on 2006-12-10
yeah...

but if you can reply IN the bug thread, I think it will be better and help the bug to become "Confirmed" and then "Critical" ;)

---

### Post by adam0509 on 2006-12-26
bug is still here ](*,) 


It seems I can't get ANY log or ANY report, because, when I try "sudo mount /media/cdrom", It don't display anything, 

Same for "disks-admin"... launching the program but beeing timed out. I can kill him with command "sudo killall disks-admin" (no -9 option...)


Here you got my lsmod | grep cd :


```
$ lsmod | grep cd
uhci_hcd               35536  0
usbcore               139172  2 uhci_hcd
ide_cd                 35780  11
cdrom                  41408  1 ide_cd

```

If I try to remove a module :

```

$ sudo modprobe -r ide_cd
FATAL: Module ide_cd is in use.
$ sudo modprobe -r cdrom
FATAL: Module cdrom is in use.

```

Okay, seems there are in use...




here is my lsmod :

```

Module                  Size  Used by
udf                    94756  5
ppdev                   9668  0
cpufreq_userspace       6496  0
cpufreq_stats           6688  0
freq_table              4928  1 cpufreq_stats
cpufreq_powersave       1920  0
cpufreq_ondemand        7752  0
cpufreq_conservative     9000  0
video                  16324  0
tc1100_wmi              6884  0
sony_acpi               5580  0
pcc_acpi               12416  0
hotkey                 11492  0
dev_acpi               11236  0
container               4608  0
button                  6704  0
acpi_sbs               20172  0
battery                 9988  1 acpi_sbs
ac                      5220  1 acpi_sbs
i2c_acpi_ec             5120  1 acpi_sbs
ipv6                  286976  20
nls_iso8859_1           4224  2
nls_cp437               5888  2
vfat                   14496  2
fat                    55548  1 vfat
dm_mod                 63256  0
md_mod                 76052  0
af_packet              24520  2
guillemot               5536  0
lp                     12356  0
tsdev                   8032  0
snd_ens1371            26464  2
gameport               16776  3 guillemot,snd_ens1371
snd_rawmidi            26848  1 snd_ens1371
snd_seq_device          9228  1 snd_rawmidi
snd_ac97_codec        100224  1 snd_ens1371
snd_pcm_oss            56448  0
snd_mixer_oss          20544  1 snd_pcm_oss
snd_pcm                96708  3 snd_ens1371,snd_ac97_codec,snd_pcm_oss
snd_timer              26884  1 snd_pcm
parport_pc             37988  1
parport                39400  3 ppdev,lp,parport_pc
snd                    60004  12 snd_ens1371,snd_rawmidi,snd_seq_device,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer
soundcore              10784  1 snd
snd_page_alloc         11304  1 snd_pcm
snd_ac97_bus            2400  1 snd_ac97_codec
pcspkr                  2244  0
floppy                 64676  0
via_rhine              25988  0
mii                     6176  1 via_rhine
nvidia               3923676  12
i2c_core               22848  1 i2c_acpi_ec
psmouse                40004  0
serio_raw               7748  0
hw_random               5716  0
shpchp                 49504  0
pci_hotplug            30788  1 shpchp
intel_agp              24700  1
agpgart                36784  2 nvidia,intel_agp
evdev                  10176  1
ext3                  148296  1
jbd                    65876  1 ext3
ide_generic             1504  0
uhci_hcd               35536  0
usbcore               139172  2 uhci_hcd
ide_cd                 35780  11
cdrom                  41408  1 ide_cd
ide_disk               19136  6
piix                   11652  1
generic                 5124  0
thermal                13768  0
processor              26888  1 thermal
fan                     4836  0
capability              4968  0
commoncap               7328  1 capability
vga16fb                13992  1
vgastate               10208  1 vga16fb
fbcon                  43904  72
tileblit                2784  1 fbcon
font                    8320  1 fbcon
bitblit                 6464  1 fbcon
softcursor              2304  1 bitblit

```



If you got any other things I can report (logs, whatever...), please post

---

### Post by adam0509 on 2006-12-26
Okay, I found a solution, not 100% viable, but it works a little bit better...


By modifiying Grub's command boot (e + e) and then adding "irqpoll" (then "b" to boot), it works a little bit better.


I've seen quite few other commands to solve these type of problem (**type "lost interrupt" in google**), like "hdc=noprobe hdc=cdrom"...


I will edit my launchpad bug report, but won't delete it, cause this seems to be a famous bug that should absolutely be took in consideration....

---

### Post by isaric on 2006-12-27
In French : [Lecteur DVD+RW bloqué]("http://forum.ubuntu-fr.org/viewtopic.php?id=74749"), we have also some problems for mount CD or (and) DVD.
Is this the same thing as that indicated on this post ?
What solution, because I look here, but i understand nothing.

Can you explain more  your solution ?

---

### Post by adam0509 on 2006-12-27
I've created a new page on french wiki :


[http://doc.ubuntu-fr.org/installation/rescue](http://doc.ubuntu-fr.org/installation/rescue)


;)

---

