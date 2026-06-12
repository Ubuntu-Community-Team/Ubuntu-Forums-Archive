---
title: "Sound once again... seeking pointers"
date: 2005-02-26
forum: Hardware &amp; Laptops
---

### Post by Declan on 2005-02-26
I've searched and seen that I'm not the only one to have difficulty getting the sound to work.  
This same laptop's sound works under Mandrake 10, 10.1, SimplyMepis and ProMepis.  
But I'd be happier to get it running on the now installed Warty (or Hoary, if necessary).

From what other people have been saying, and from my own efforts, there is the curiosity that although the system knows that it is dealing with an AC97, it doesn't manage to make it work.  And although alsa is installed, it will not let us run alsaconfig.  

What are the normal troubleshooting steps, to figure out where the problem lies?
And what about an upgrade to Hoary?  (I'm not interested in testing, just in getting the sound to work).  Would there be any benefit in doing that?  Or only woe?

Thanks,

Declan

---

### Post by zeroz52 on 2005-02-27
I'm having the same exact problem. Can someone help us please!?! ](*,)

---

### Post by Declan on 2005-02-27
I see that I have no /dev/dsp

Why not?
How do I get one?
Would that help?

Thanks!

Declan

---

### Post by alastair on 2005-02-27
Logs :

Look at /var/log/syslog

and see any relevant sound entries.

Print out :

lspci
lsmod

When you say "will not let us run alsaconfig" - what error? Is it installed? It is in the "alsa-utils" package.

---

### Post by Declan on 2005-02-27
Thanks for the response.

I wouldn't really know what is relevant output of /var/log/syslog 
I looked through it, and saw this message:

Feb 27 09:00:17 localhost kernel: ATIIXP: IDE controller at PCI slot 0000:00:14.1
Feb 27 09:00:17 localhost kernel: ACPI: PCI interrupt 0000:00:14.1[A] -> GSI 16 (level, low) -> IRQ 185
Feb 27 09:00:17 localhost kernel: ATIIXP: chipset revision 0
Feb 27 09:00:17 localhost kernel: ATIIXP: not 100%% native mode: will probe irqs later

What would be relevant?


lspci says:

0000:00:00.0 Host bridge: ATI Technologies Inc: Unknown device cab3 (rev 05)
0000:00:01.0 PCI bridge: ATI Technologies Inc PCI Bridge [IGP 340M]
0000:00:13.0 USB Controller: ATI Technologies Inc: Unknown device 4347 (rev 01)
0000:00:13.1 USB Controller: ATI Technologies Inc: Unknown device 4348 (rev 01)
0000:00:13.2 USB Controller: ATI Technologies Inc: Unknown device 4345 (rev 01)
0000:00:14.0 SMBus: ATI Technologies Inc ATI SMBus (rev 18)
0000:00:14.1 IDE interface: ATI Technologies Inc: Unknown device 4349
0000:00:14.3 ISA bridge: ATI Technologies Inc: Unknown device 434c
0000:00:14.4 PCI bridge: ATI Technologies Inc: Unknown device 4342
0000:00:14.5 Multimedia audio controller: ATI Technologies Inc IXP150 AC'97 Audio Controller
0000:00:14.6 Modem: ATI Technologies Inc: Unknown device 434d (rev 01)
0000:01:05.0 VGA compatible controller: ATI Technologies Inc: Unknown device 4437
0000:02:06.0 CardBus bridge: Texas Instruments PCI1410 PC card Cardbus Controller (rev 02)
0000:02:07.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
0000:02:0a.0 FireWire (IEEE 1394): Texas Instruments TSB43AB21 IEEE-1394a-2000 Controller (PHY/Link)




lsmod says:
 
sb_lib                 49552  0
uart401                11556  1 sb_lib
sound                  81612  2 sb_lib,uart401
proc_intf               3776  0
freq_table              4196  0
cpufreq_userspace       5240  0
cpufreq_powersave       1728  0
ds                     18468  2
button                  6584  0
ac                      4812  0
battery                 9388  0
ipv6                  257060  8
af_packet              22088  2
ohci1394               34884  0
8139too                25568  0
8139cp                 20256  0
mii                     5056  2 8139too,8139cp
crc32                   4288  2 8139too,8139cp
yenta_socket           20992  0
pcmcia_core            68404  2 ds,yenta_socket
snd_atiixp             21160  0
snd_ac97_codec         67844  1 snd_atiixp
snd_pcm_oss            52968  0
snd_mixer_oss          19456  1 snd_pcm_oss
snd_pcm                95172  2 snd_atiixp,snd_pcm_oss
snd_timer              24964  1 snd_pcm
snd                    55332  6 snd_atiixp,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer
soundcore              10112  3 sb_lib,sound,snd
snd_page_alloc         11432  2 snd_atiixp,snd_pcm
ehci_hcd               30756  0
ohci_hcd               20996  0
usbcore               115716  4 ehci_hcd,ohci_hcd
pci_hotplug            33680  0
ati_agp                 8460  1
agpgart                33640  1 ati_agp
md                     48552  0
dm_mod                 57308  1
capability              4520  0
commoncap               7072  1 capability
parport_pc             34752  1
lp                     10724  0
parport                40712  2 parport_pc,lp
sbp2                   23816  0
ieee1394              108408  2 ohci1394,sbp2
tsdev                   7232  0
joydev                  9760  0
evdev                   9440  1
ide_cd                 41572  0
mousedev               10252  1
psmouse                19720  0
sr_mod                 16900  0
scsi_mod              122508  2 sbp2,sr_mod
cdrom                  39392  2 ide_cd,sr_mod
ext3                  123912  1
jbd                    60824  1 ext3
mbcache                 9092  1 ext3
ide_generic             1408  0
ide_disk               18752  3
atiixp                  8696  1
ide_core              136120  4 ide_cd,ide_generic,ide_disk,atiixp
unix                   28304  785
fan                     3980  0
thermal                12976  0
processor              17392  1 thermal
font                    8352  0
vesafb                  6560  0
cfbcopyarea             3712  1 vesafb
cfbimgblt               3072  1 vesafb
cfbfillrect             3616  1 vesafb


When I say that alsaconfig won't run, I mean that it appears not to recognise the command (alsa-base etc. are installed).  It simply responds "command not found".
Yes, I've done it with sudo, and as superuser.
This seems a bit unusual, perhaps, but I've read of a number of others who meet the same difficulty with the alsaconfig command.  

That's a lot of info I've posted up there, and I understand next to none of it.  
But I am glad to get an insight into the whole thing works/should work.  
When you look "under the hood" you see many unexpected layers, and it is not immediately apparent which layer is relevant.

Thanks Alastair (and any others that might be inspired to chip in),

Declan

---

### Post by alastair on 2005-02-27
The "lspci" (list PCI devices) shows an "AC'97 Audio Controller" - similar to mine.

The "lsmod" command shows what modules are loaded = "snd_atiixp" is the ATI sound module I assume.

Install "alsa-utils" and try "alsamixer" - to unmute and adjust channels i.e.

apt-get install alsa-utils

Then run alsamixer in a shell - use the cursor keys (<>) to select a channel and "m" to unmute - up/down cursor to adjust volume.

---

### Post by Declan on 2005-02-27
Great,

Thanks for coming back to me.
Anyway, here we're getting towards the heart of the problem, which is that the alsa-related commands don't work.

I did apt-get install alsa-utils, and it confirmed that mine were the latest.  So I have them.

Then I did alsamixer, and it responds:
 function snd_ctl_open failed for default: No such device

If I (we) go to the Gnome sound volume control, it doesn't open and complains that there are "no mixer elements and/or devices found."

It is a curious pancake, is it not!

Declan

---

### Post by r00 on 2005-02-28
i was having trouble getting my extigy working and i happen to stumble upon this particular thread..  and i've now got my internal ac97 going on.. still haven't quite got the mock-surround sound working from using the mixer..but i'm sure if i keep looking i can find something..  mebbe if i keep digging around i can get my usb extigy to work as well.. would be a shame not to be able to use it.... but thanks so much everyone for the help wif checking alsa's mixer app... at least it won't be so quiet in here anymore  :D

---

### Post by Declan on 2005-02-28
No thoughts?

I see another person has posted a (possibly) similar question today.  
What might be going on when alsa-utils is installed, but the thing refuses to run alsaconfig.

Any ideas?

Declan

---

