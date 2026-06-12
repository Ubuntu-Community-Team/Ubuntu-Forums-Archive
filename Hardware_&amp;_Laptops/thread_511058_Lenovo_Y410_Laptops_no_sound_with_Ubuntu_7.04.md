---
title: "Lenovo Y410 Laptops no sound with Ubuntu 7.04"
date: 2007-07-27
forum: Hardware &amp; Laptops
---

### Post by arthip on 2007-07-27
Hello !!!
i'm a newbies for Ubuntu Linux :(

i just install ubuntu 7.04 on my lenovo y410 laptops
everything going OK but my laptops no sound (all from speaker and header)

i tried to correct problem myself but not work !!!
follow [https://help.ubuntu.com/community/HdaIntelSoundHowto?highlight=(hda)]("https://help.ubuntu.com/community/HdaIntelSoundHowto?highlight=(hda)") it not work
and i tried to [http://ubuntuforums.org/showthread.php?t=314383]("http://ubuntuforums.org/showthread.php?t=314383") it still not work !!!!

This is lspci
```

00:00.0 Host bridge: Intel Corporation Mobile Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile Integrated Graphics Controller (rev 03)
00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI #4 (rev 03)
00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI #5 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 (rev 03)
00:1c.2 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 3 (rev 03)
00:1c.3 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 4 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f3)
00:1f.0 ISA bridge: Intel Corporation Mobile LPC Interface Controller (rev 03)
00:1f.2 IDE interface: Intel Corporation Mobile SATA IDE Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 03)
04:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG Network Connection (rev 02)
06:00.0 Ethernet controller: Broadcom Corporation Unknown device 1713 (rev 02)
08:06.0 FireWire (IEEE 1394): Ricoh Co Ltd Unknown device 0832 (rev 05)
08:06.1 Generic system peripheral [0805]: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 22)
08:06.2 System peripheral: Ricoh Co Ltd Unknown device 0843 (rev 12)
08:06.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 12)
08:06.4 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev 12)

```

This is lsmod
```

Module                  Size  Used by
binfmt_misc            12680  1 
rfcomm                 40856  0 
l2cap                  25856  5 rfcomm
bluetooth              55908  4 rfcomm,l2cap
ppdev                  10116  0 
acpi_cpufreq           10056  1 
cpufreq_conservative     8200  0 
cpufreq_stats           7360  0 
cpufreq_ondemand        9228  1 
freq_table              5792  3 acpi_cpufreq,cpufreq_stats,cpufreq_ondemand
cpufreq_powersave       2688  0 
cpufreq_userspace       5408  0 
tc1100_wmi              8068  0 
pcc_acpi               13184  0 
dev_acpi               12292  0 
sony_acpi               6284  0 
button                  8720  0 
ac                      6020  0 
dock                   10268  0 
video                  16388  0 
battery                10756  0 
container               5248  0 
sbs                    15652  0 
i2c_ec                  6016  1 sbs
i2c_core               22656  1 i2c_ec
asus_acpi              17308  0 
backlight               7040  1 asus_acpi
ipv6                  268960  10 
nls_utf8                3072  3 
ntfs                  107764  3 
sbp2                   23812  0 
parport_pc             36388  0 
lp                     12452  0 
parport                36936  3 ppdev,parport_pc,lp
fuse                   46612  0 
snd_hda_intel         244632  1 
xpad                    9988  0 
snd_pcm_oss            44672  0 
snd_mixer_oss          17792  1 snd_pcm_oss
snd_pcm                81028  2 snd_hda_intel,snd_pcm_oss
snd_seq_oss            35200  0 
snd_seq_midi_event      8576  1 snd_seq_oss
joydev                 10816  0 
ipw3945               118816  1 
uvcvideo               42500  0 
usbhid                 26592  0 
snd_seq                54000  4 snd_seq_oss,snd_seq_midi_event
snd_timer              24196  2 snd_pcm,snd_seq
snd_seq_device          9612  2 snd_seq_oss,snd_seq
videodev               28160  1 uvcvideo
v4l1_compat            15236  2 uvcvideo,videodev
v4l2_common            25216  2 uvcvideo,videodev
hid                    27392  1 usbhid
af_packet              23816  6 
ieee80211              34760  1 ipw3945
ieee80211_crypt         7040  1 ieee80211
snd                    56324  10 snd_hda_intel,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_seq,snd_timer,snd_seq_device
soundcore               8672  1 snd
snd_page_alloc         11272  2 snd_hda_intel,snd_pcm
psmouse                38920  0 
intel_agp              25244  1 
agpgart                35400  1 intel_agp
sdhci                  18700  0 
mmc_core               26756  1 sdhci
serio_raw               7940  0 
shpchp                 34324  0 
pci_hotplug            32576  1 shpchp
tsdev                   8768  0 
evdev                  11008  8 
ext3                  133128  1 
jbd                    59816  1 ext3
mbcache                 9604  1 ext3
sg                     36252  0 
sd_mod                 23428  6 
sr_mod                 17060  0 
cdrom                  37664  1 sr_mod
generic                 5124  0 [permanent]
ata_generic             9092  0 
ohci1394               36528  0 
ieee1394              299448  2 sbp2,ohci1394
ehci_hcd               34188  0 
tg3                   109700  0 
ata_piix               15492  5 
libata                125720  2 ata_generic,ata_piix
scsi_mod              142348  5 sbp2,sg,sd_mod,sr_mod,libata
uhci_hcd               25360  0 
usbcore               134280  6 xpad,uvcvideo,usbhid,ehci_hcd,uhci_hcd
thermal                14856  0 
processor              31048  2 acpi_cpufreq,thermal
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

This is my laptops detials ( Lenovo Y410 - 775733R )
```

[http://www-07.ibm.com/lenovoinfo/th/notebooks/3000hho/y-series/]("http://www-07.ibm.com/lenovoinfo/th/notebooks/3000hho/y-series/")

```

Help me please !!!
Thank you.

---

### Post by madmetal on 2007-07-28
well its a known problem and i think its fixed on forthcoming version of ubuntu 7.10
so you have to wait till official release (you can also install 7.10 but its at testing phase and its not recomended../ although you can run a live cd of 7.10 to see if you have sound with it ;) )

---

### Post by julian67 on 2007-07-28
I found that the the fix outlined at [http://ubuntuforums.org/showthread.php?t=314383]("http://ubuntuforums.org/showthread.php?t=314383") only works for me on my y400 with the 2.6.20-15 kernel. If you upgraded to 2.6.20-16 via the update manager then the fix won't work. Revert to 2.6.20-15 and you might be OK. Can't be sure as the y410 has several different components than the y400 so maybe the sound controller is set up differently.

---

### Post by arthip on 2007-07-29
Thank you very much madmetal and julian67 .

---

### Post by arthip on 2007-07-29
> **madmetal said:**
> well its a known problem and i think its fixed on forthcoming version of ubuntu 7.10
so you have to wait till official release (you can also install 7.10 but its at testing phase and its not recomended../ although you can run a live cd of 7.10 to see if you have sound with it ;) )

i just download and test run for ubuntu 7.10 test 3.
It still no sound at all.
but i use command alsamixer it show "Intel HD Audio" and "ALC262"

It's my sound card !!!

---

### Post by gboethius on 2007-10-03
Hi arthip  

I'm as much as a newbie as you can get to unix but we seem to have the same laptop, Lenovo Y410. I've just downloaded CentOS 5 to mine and I have the same problems with my sound card as you seem to have. 
On top of this, the latest CentOS 5 kernel update does not recognize my ethernet card.

I write this because you are the only case of someone using Linux on a Y410 I've come across. I'll follow this thread to see what happens with you and I might just copy what you do. 

What are the advantages of Ubuntu to CentOS/RedHat?

-gB

---

### Post by hellmet on 2007-12-03
Same problem. Everything else works completely out of the box, and works perfectly. Just the sound . :(

---

### Post by ambuj123 on 2007-12-05
Hey i had similar problem on my Lenovo y410 laptop , after searching various forums for solution i finally managed to get sound working here in this article i have documented those steps which made sound work on my lenvo y410 laptop

[http://linuxondesktop.blogspot.com/2007/12/getting-sound-to-work-on-your-ubuntu.html]("http://linuxondesktop.blogspot.com/2007/12/getting-sound-to-work-on-your-ubuntu.html")

---

### Post by hellmet on 2007-12-06
Thanks. My laptop has sound.. but headphones don't like you said. It sucks..this way.

---

### Post by maxxum on 2007-12-09
guys...I got the sound to work on my 410 but did anyone get the built-in webcam to work? if yes, how? camorama doesn't see it.

---

### Post by wyth on 2007-12-11
Just curious if anyone saw [this over at the ThinkWiki for Linux on Lenovos]("http://www.thinkwiki.org/wiki/Installing_Ubuntu_7.10_%28Gutsy_Gibbon%29_Release_Candidate_on_a_ThinkPad_T61#Inextricably_Linked_to_the_Modem"):

It seems on ThinkPads, you need to make sure the modem is activated in the BIOS in order to get the sound to work.  Seems the sound is "inextricably linked to the modem," so if the modem isn't activated in the BIOS, you won't get any sound.

I don't know if this works the same on the Y410's or other models, but I'd be curious to find out.  I'm about to get a new laptop, and am trying to decide between a Lenovo and a Dell.

---

### Post by sberan on 2007-12-16
> **maxxum said:**
> guys...I got the sound to work on my 410 but did anyone get the built-in webcam to work? if yes, how? camorama doesn't see it.

There is a program named Cheese that works great. Still haven't got the internal mic or headphone jack to work though :confused:

---

### Post by tlivingd on 2007-12-18
I'm re-hashing this here.. for future readers as there was another thread about the y410 here.  [http://ubuntuforums.org/showthread.php?t=611153&page=2](http://ubuntuforums.org/showthread.php?t=611153&page=2)

For the lenovo y410,  what we've hashed above has be republished here in an easy to read instructional format.
[http://linuxondesktop.blogspot.com/2007/12/getting-sound-to-work-on-your-ubuntu.html](http://linuxondesktop.blogspot.com/2007/12/getting-sound-to-work-on-your-ubuntu.html)

after doing some more reading.  I wish i was more comfortable with Ubuntu, Because 
this Ubuntu Wiki has some soundcard things to say about the lenovo 3000 and I'm thinking may work on the y410  [https://wiki.ubuntu.com/LaptopTestingTeam/Lenovo3000N100_0768](https://wiki.ubuntu.com/LaptopTestingTeam/Lenovo3000N100_0768)
but I'm afraid to try it as i'd kill off my sound.


I'm wondering if the 3000 has the optical-out thru the headphone jack like the y410.  I've never seen that before until this laptop.

---

### Post by ILM on 2008-04-10
> **ambuj123 said:**
> Hey i had similar problem on my Lenovo y410 laptop , after searching various forums for solution i finally managed to get sound working here in this article i have documented those steps which made sound work on my lenvo y410 laptop

[http://linuxondesktop.blogspot.com/2007/12/getting-sound-to-work-on-your-ubuntu.html]("http://linuxondesktop.blogspot.com/2007/12/getting-sound-to-work-on-your-ubuntu.html")


I have just bought a lenovo y410 and the sound works if you press the on buton before you start up the pc, however if you forget to press it the sound does not work ,am I missing something here or is there a way to get it to work?

ILM

---

