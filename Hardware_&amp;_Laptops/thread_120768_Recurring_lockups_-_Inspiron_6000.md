---
title: "Recurring lockups - Inspiron 6000"
date: 2006-01-23
forum: Hardware &amp; Laptops
---

### Post by ScatterBrain on 2006-01-23
For several weeks now, my laptop has been locking up at random just after boot.  I started a thread in desktop support ([See Here]("http://ubuntuforums.org/showthread.php?t=112872")) complaining about the issue.  At the time, the machine was only locking up shortly after GDM was loaded.  At the time, I could prevent the lockups by either having or not having my USB mouse plugged up.

Now, it doesn't matter what I do - it's gonna lock up.  Now it doesn't matter about the mouse, it doesn't matter about GDM, it doesn't matter about anything.  Shortly after a boot, the machine will freeze.  Usually I can power-cycle the machine once or twice and everything works.

But today was the last straw.  I was trying to diagnose a DHCP issue here and I had to restart the machine *at least* 6 times to get it play ball.  Once I had the machine running, I started a series of 'dhclient eth1' commands to watch my DHCP server as it worked and three different times during that round the machine froze.

Shortly after that I had to do a small presentation to 'management' about an intranet idea I'd been working on - 5 lock-up/boots then.  I can't take it anymore.  I'm just about convinced that I need to take the winblows way out and reload the machine, but I'l hoping that someone can rescue me from that path.

I don't know where to start with information, so I do the common stuff:

**lspci:**
```
0000:00:00.0 Host bridge: Intel Corp. Mobile Memory Controller Hub (rev 03)
0000:00:01.0 PCI bridge: Intel Corp. Mobile Memory Controller Hub PCI Express Port (rev 03)
0000:00:1d.0 USB Controller: Intel Corp. 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1 (rev 03)
0000:00:1d.1 USB Controller: Intel Corp. 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2 (rev 03)
0000:00:1d.2 USB Controller: Intel Corp. 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3 (rev 03)
0000:00:1d.3 USB Controller: Intel Corp. 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #4 (rev 03)
0000:00:1d.7 USB Controller: Intel Corp. 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller (rev 03)
0000:00:1e.0 PCI bridge: Intel Corp. 82801 PCI Bridge (rev d3)
0000:00:1e.2 Multimedia audio controller: Intel Corp. 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Audio Controller (rev 03)
0000:00:1e.3 Modem: Intel Corp. 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Modem Controller (rev 03)
0000:00:1f.0 ISA bridge: Intel Corp. 82801FBM (ICH6M) LPC Interface Bridge (rev 03)
0000:00:1f.2 IDE interface: Intel Corp. 82801FBM (ICH6M) SATA Controller (rev 03)
0000:00:1f.3 SMBus: Intel Corp. 82801FB/FBM/FR/FW/FRW (ICH6 Family) SMBus Controller (rev 03)
0000:01:00.0 VGA compatible controller: ATI Technologies Inc: Unknown device 5460
0000:03:00.0 Ethernet controller: Broadcom Corporation BCM4401-B0 100Base-TX (rev 02)
0000:03:01.0 CardBus bridge: Ricoh Co Ltd RL5c476 II (rev b3)
0000:03:01.1 FireWire (IEEE 1394): Ricoh Co Ltd R5C552 IEEE 1394 Controller (rev 08)
0000:03:01.2 0805: Ricoh Co Ltd: Unknown device 0822 (rev 17)
0000:03:03.0 Network controller: Intel Corp. PRO/Wireless 2200BG (rev 05)

```

**lsmod:**
```
Module                  Size  Used by
af_packet              20232  2
vmnet                  33316  13
vmmon                 103660  0
rfcomm                 34972  0
l2cap                  22404  5 rfcomm
bluetooth              43012  4 rfcomm,l2cap
ipv6                  217408  12
speedstep_centrino      7380  1
cpufreq_userspace       4444  1
cpufreq_stats           5124  0
freq_table              4484  2 speedstep_centrino,cpufreq_stats
cpufreq_powersave       1920  0
cpufreq_ondemand        5916  0
cpufreq_conservative     6820  0
pcmcia                 24584  2
video                  16004  0
tc1100_wmi              6916  0
sony_acpi               5516  0
pcc_acpi               11392  0
i2c_acpi_ec             5760  0
i2c_core               19728  1 i2c_acpi_ec
hotkey                  9508  0
dev_acpi               11396  0
container               4608  0
button                  6672  0
battery                 9604  0
ac                      4996  0
sg                     33696  0
sr_mod                 15652  0
cdrom                  33952  1 sr_mod
pcspkr                  3652  0
rtc                    11832  0
ipw2200                92680  0
firmware_class          9472  1 ipw2200
ieee80211              27012  1 ipw2200
ieee80211_crypt         5636  2 ipw2200,ieee80211
ohci1394               30644  0
yenta_socket           22540  1
rsrc_nonstatic         12032  1 yenta_socket
pcmcia_core            44932  3 pcmcia,yenta_socket,rsrc_nonstatic
tpm_nsc                 6528  0
tpm                     9504  1 tpm_nsc
snd_intel8x0           30144  1
snd_ac97_codec         72188  1 snd_intel8x0
snd_pcm_oss            46368  0
snd_mixer_oss          16128  1 snd_pcm_oss
snd_pcm                78344  3 snd_intel8x0,snd_ac97_codec,snd_pcm_oss
snd_timer              21764  1 snd_pcm
snd                    48644  8 snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer
soundcore               9184  1 snd
snd_page_alloc         10120  2 snd_intel8x0,snd_pcm
pci_hotplug            24628  0
intel_agp              21276  1
ext3                  115976  1
jbd                    48536  1 ext3
dm_mod                 50364  1
joydev                  9280  0
tsdev                   7616  0
ati_agp                 8716  0
fglrx                 424544  7
agpgart                32328  3 intel_agp,ati_agp,fglrx
evdev                   9088  1
sbp2                   21128  0
ieee1394               90936  2 ohci1394,sbp2
psmouse                26116  0
mousedev               10912  1
parport_pc             31812  0
lp                     11460  0
parport                32072  2 parport_pc,lp
md                     40656  0
xfs                   499256  3
exportfs                5376  1 xfs
thermal                13192  0
processor              23100  2 speedstep_centrino,thermal
fan                     4740  0
usbhid                 30688  0
b44                    19204  0
mii                     5248  1 b44
ehci_hcd               29448  0
uhci_hcd               28048  0
usbcore               104316  4 usbhid,ehci_hcd,uhci_hcd
sd_mod                 17424  6
ide_generic             1664  0
ide_core              125268  1 ide_generic
ata_piix                9476  10
ahci                   11268  0
libata                 47876  2 ata_piix,ahci
scsi_mod              124872  6 sg,sr_mod,sbp2,sd_mod,ahci,libata
unix                   24624  948
fbcon                  34176  73
tileblit                2560  1 fbcon
font                    8448  1 fbcon
bitblit                 5248  1 fbcon
vesafb                  8088  1
cfbcopyarea             4480  1 vesafb
cfbimgblt               2944  1 vesafb
cfbfillrect             3840  1 vesafb
softcursor              2432  1 vesafb
capability              5000  0
commoncap               6784  1 capability

```

I'd supply log files, but I can't get to them after the machine locks and nothing is recorded before the lock.

I can try to supply any other information as someone directs...as long I think there is a hope for salvaging the install I'll bang away on it looking for an answer.  As soon as I'm convinced that a reload is the only way, I'll take off down that path.

---

### Post by ScatterBrain on 2006-01-24
bump

---

### Post by markr on 2006-01-24
Not sure if this will help, but I have an inspiron 5150 and experienced some lockups (alougth nowhere near the frequency you are seeing).

I did not get full resolutions (sorry), but I was pretty certain that it was either the NVidia drivers/config or the NDISWrapper for my PCMCIA wireless card.  I did not have any problems when I removed both of these.

Mark.

---

### Post by ScatterBrain on 2006-01-24
[QUOTE=markr]I did not get full resolutions (sorry), but I was pretty certain that it was either the NVidia drivers/config or the NDISWrapper for my PCMCIA wireless card.  I did not have any problems when I removed both of these.

Mark.[/QUOTE]

Unfortunetly, my Inspiron 6000 doesn't have an nVidia card - it's got an ATI Radeon x300.  Nor could the problem be tied to NDISWwrapper/PCMCIA.  I don't use NDISWrapper for anything and (as yet) have not had to use the PCMCIA slot for anything either.

I am using the propriatary ATI Drivers, but I have used the machine with and without them and the problem is still there.

I'd be willing to blame it on the hardware except that after I do get it running, it runs just fine for several hours at a time - until I turn it off again.

This just really boggles the mind...

---

### Post by dixonstalbert on 2006-01-24
hi scatterbrain

I have been running ubuntu on my Inspiron 6000 for 6 months. 
Never had a lockup but could not do anything until downgraded my BIOS to A05 from A07
my inspiron has the 915 intel graphics which makes me wonder if the ATI graphics card is causing you grief.

Here is my lspci and lsmod for you to compare:
(I could not see usbhid in your lsmod- not sure if that is significant)
```
ixon@ubuntu:~$ lspci
0000:00:00.0 Host bridge: Intel Corp. Mobile Memory Controller Hub (rev 03)
0000:00:02.0 VGA compatible controller: Intel Corp. Mobile Graphics Controller ( rev 03)
0000:00:02.1 Display controller: Intel Corp. Mobile Graphics Controller (rev 03)
0000:00:1d.0 USB Controller: Intel Corp. 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB  UHCI #1 (rev 03)
0000:00:1d.1 USB Controller: Intel Corp. 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB  UHCI #2 (rev 03)
0000:00:1d.2 USB Controller: Intel Corp. 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB  UHCI #3 (rev 03)
0000:00:1d.3 USB Controller: Intel Corp. 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB  UHCI #4 (rev 03)
0000:00:1d.7 USB Controller: Intel Corp. 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB 2 EHCI Controller (rev 03)
0000:00:1e.0 PCI bridge: Intel Corp. 82801 PCI Bridge (rev d3)
0000:00:1e.2 Multimedia audio controller: Intel Corp. 82801FB/FBM/FR/FW/FRW (ICH 6 Family) AC'97 Audio Controller (rev 03)
0000:00:1e.3 Modem: Intel Corp. 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Modem Controller (rev 03)
0000:00:1f.0 ISA bridge: Intel Corp. 82801FBM (ICH6M) LPC Interface Bridge (rev 03)
0000:00:1f.2 IDE interface: Intel Corp. 82801FBM (ICH6M) SATA Controller (rev 03 )
0000:00:1f.3 SMBus: Intel Corp. 82801FB/FBM/FR/FW/FRW (ICH6 Family) SMBus Contro ller (rev 03)
0000:03:00.0 Ethernet controller: Broadcom Corporation BCM4401-B0 100Base-TX (re v 02)
0000:03:01.0 CardBus bridge: Ricoh Co Ltd RL5c476 II (rev b3)
0000:03:01.1 FireWire (IEEE 1394): Ricoh Co Ltd R5C552 IEEE 1394 Controller (rev  08)
0000:03:01.2 0805: Ricoh Co Ltd: Unknown device 0822 (rev 17)
0000:03:03.0 Network controller: Intel Corp. PRO/Wireless 2200BG (rev 05)
```

```
dixon@ubuntu:~$ lsmod
Module                  Size  Used by
usbhid                 30688  0
rfcomm                 34972  0
l2cap                  22404  5 rfcomm
bluetooth              43012  4 rfcomm,l2cap
speedstep_centrino      7380  1
cpufreq_userspace       4444  1
cpufreq_stats           5124  0
freq_table              4484  2 speedstep_centrino,cpufreq_stats
cpufreq_powersave       1920  0
cpufreq_ondemand        5916  0
cpufreq_conservative     6820  0
pcmcia                 24584  2
i915                   17920  1
drm                    58004  2 i915
video                  16004  0
tc1100_wmi              6916  0
sony_acpi               5516  0
pcc_acpi               11392  0
hotkey                  9508  0
dev_acpi               11396  0
i2c_acpi_ec             5760  0
i2c_core               19728  1 i2c_acpi_ec
button                  6672  0
battery                 9604  0
container               4608  0
ac                      4996  0
quickcam               68900  0
ipv6                  217408  6
af_packet              20232  2
arc4                    2048  1
ieee80211_crypt_wep     4864  1
sg                     33696  0
sr_mod                 15652  1
pcspkr                  3652  0
rtc                    11832  0
ohci1394               30644  0
yenta_socket           22540  1
rsrc_nonstatic         12032  1 yenta_socket
pcmcia_core            44932  3 pcmcia,yenta_socket,rsrc_nonstatic
tpm_nsc                 6528  0
tpm                     9504  1 tpm_nsc
snd_intel8x0           30144  1
snd_ac97_codec         72188  1 snd_intel8x0
snd_pcm_oss            46368  0
snd_mixer_oss          16128  1 snd_pcm_oss
snd_pcm                78344  3 snd_intel8x0,snd_ac97_codec,snd_pcm_oss
snd_timer              21764  1 snd_pcm
snd                    48644  8 snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer
soundcore               9184  1 snd
snd_page_alloc         10120  2 snd_intel8x0,snd_pcm
intel_agp              21276  1
agpgart                32328  3 drm,intel_agp
dm_mod                 50364  1
joydev                  9280  0
tsdev                   7616  0
ide_disk               16128  0
ide_cd                 36996  0
cdrom                  33952  2 sr_mod,ide_cd
piix                    9476  0
evdev                   9088  1
ipw2200                92680  0
firmware_class          9472  1 ipw2200
ieee80211              27012  1 ipw2200
ieee80211_crypt         5636  3 ieee80211_crypt_wep,ipw2200,ieee80211
videodev                9344  1 quickcam
sbp2                   21128  0
ieee1394               90936  2 ohci1394,sbp2
psmouse                26116  0
mousedev               10912  1
parport_pc             31812  0
lp                     11460  0
parport                32072  2 parport_pc,lp
md                     40656  0
ext3                  115976  2
jbd                    48536  1 ext3
thermal                13192  0
processor              23100  2 speedstep_centrino,thermal
fan                     4740  0
b44                    19204  0
mii                     5248  1 b44
ehci_hcd               29448  0
uhci_hcd               28048  0
usbcore               104316  5 usbhid,quickcam,ehci_hcd,uhci_hcd
sd_mod                 17424  5
ide_generic             1664  0
ide_core              125268  4 ide_disk,ide_cd,piix,ide_generic
ata_piix                9476  12
ahci                   11268  0
libata                 47876  2 ata_piix,ahci
scsi_mod              124872  6 sg,sr_mod,sbp2,sd_mod,ahci,libata
unix                   24624  697
vesafb                  8088  0
capability              5000  0
commoncap               6784  1 capability
vga16fb                12232  1
vgastate                8320  1 vga16fb
softcursor              2432  2 vesafb,vga16fb
cfbimgblt               2944  2 vesafb,vga16fb
cfbfillrect             3840  2 vesafb,vga16fb
cfbcopyarea             4480  2 vesafb,vga16fb
fbcon                  34176  72
tileblit                2560  1 fbcon
font                    8448  1 fbcon
bitblit                 5248  1 fbcon
```

Hope this helps

---

### Post by fissy on 2006-01-24
Hello,

I've got exactly the same problem running ubuntu breezy on my Inspiron 6000 (ati x300 chip, 1920x1200 resolution, 2.1GHz Centrino, abg wireless adaptor). It was doing hard lockups more than once a day, though sometimes it would go for several hours, sometimes I wouldn't get beyond logging in.

I couldn't work out what was doing it, though didn't try too hard. There seemed to be something wrong with the way the disk drive was working.

So... nothing to lose i thought, I upgraded to Dapper. Dapper sort of works, everything is working normally except for the CPU, which is permantly being punished by some unknown process. The CPU doesn't get throttled back and battery life is awful.

At some point I'll get round to filing a bug, busy busy at work though atm :(

-fissy

---

### Post by stream303 on 2006-01-25
Total stab in the dark - but my Dell Optiplex would spontaneously reboot when using any browser - found that dropping my default color depth in xorg.conf from 24 down to 16 cured my problems...

---

### Post by ScatterBrain on 2006-01-25
[QUOTE=fissy]
I've got exactly the same problem running ubuntu breezy on my Inspiron 6000 (ati x300 chip, 1920x1200 resolution, 2.1GHz Centrino, abg wireless adaptor). It was doing hard lockups more than once a day, though sometimes it would go for several hours, sometimes I wouldn't get beyond logging in.

I couldn't work out what was doing it, though didn't try too hard. There seemed to be something wrong with the way the disk drive was working.[/QUOTE]

Interesting.  Your machine and mine are very similiar - I've got the 2.0GHz Centino and Intel 2200 Pro(b/g) wifi, but other than that, they appear to be identical.  I can't say that I've even thought about the hard drive.  I have noticed that the during video playback from the DVD+R/W that there is a lag between the video and the audio - but I've contributed that to the new SATA controller in the machine.  Maybe the two are related?  Another question - were you running ATI's drivers or the X.org drivers?

[QUOTE=fissy]
So... nothing to lose i thought, I upgraded to Dapper. Dapper sort of works, everything is working normally except for the CPU, which is permantly being punished by some unknown process. The CPU doesn't get throttled back and battery life is awful.[/QUOTE]

Hmmmm...since you're running Dapper, I have to ask if Suspend to RAM is working.  If it is, even if the CPU get's hammered, I'd almost be willing to go for it.


[QUOTE=fissy]
At some point I'll get round to filing a bug, busy busy at work though atm :(

-fissy[/QUOTE]

Maybe this should be next step...

---

### Post by ScatterBrain on 2006-01-25
[QUOTE=stream303]Total stab in the dark - but my Dell Optiplex would spontaneously reboot when using any browser - found that dropping my default color depth in xorg.conf from 24 down to 16 cured my problems...[/QUOTE]

Hmmm...worth a shot.  I'll try that today.

---

### Post by fissy on 2006-01-25
[QUOTE=ScatterBrain]Interesting.  Your machine and mine are very similiar - I've got the 2.0GHz Centino and Intel 2200 Pro(b/g) wifi, but other than that, they appear to be identical.  I can't say that I've even thought about the hard drive.  I have noticed that the during video playback from the DVD+R/W that there is a lag between the video and the audio - but I've contributed that to the new SATA controller in the machine.  Maybe the two are related?  Another question - were you running ATI's drivers or the X.org drivers?

#quote removed

Hmmmm...since you're running Dapper, I have to ask if Suspend to RAM is working.  If it is, even if the CPU get's hammered, I'd almost be willing to go for it.

#quote removed

Maybe this should be next step...[/QUOTE]

I'd doubt a loss of A/V sync would be to do with the media device controller, the audio and video is stored together and the mpeg stream should get to memory in the same state if it's getting played. I imagine the loss of sync is something to do with either your decoding and viewing libraries (i.e. broken gstreamer) or your video and sound chips.

I think I tried with both ATI and the radeon drivers but neither stopped the machine freezing.

Suspend doesn't work here

---

### Post by ScatterBrain on 2006-01-26
[QUOTE=ScatterBrain]
[Quote=Stream303]Total stab in the dark - but my Dell Optiplex would spontaneously reboot when using any browser - found that dropping my default color depth in xorg.conf from 24 down to 16 cured my problems...[/quote]

Hmmm...worth a shot.  I'll try that today.[/QUOTE]


The lower color depth for X.org didn't help...

---

### Post by ScatterBrain on 2006-01-26
[QUOTE=fissy]I'd doubt a loss of A/V sync would be to do with the media device controller, the audio and video is stored together and the mpeg stream should get to memory in the same state if it's getting played. I imagine the loss of sync is something to do with either your decoding and viewing libraries (i.e. broken gstreamer) or your video and sound chips.

I think I tried with both ATI and the radeon drivers but neither stopped the machine freezing.

Suspend doesn't work here[/QUOTE]

I've tried both the ATI and radeon drivers as well, and as you said - no luck.

It's looking more and more like I just need to reload and see what happens.  I've already looked for things like BIOS updates and such - nothing there.

Sorry to here about suspend in Dapper.  I really wish this could be better for us.

I think that, if I don't find a viable solution, this weekend I'll reload the machine.  It'll only take a couple of hours.

---

### Post by almahtar on 2006-02-06
I also have a machine that has fairly poor hardware support under linux.  I know the first thing I'll do when looking for my next machine is find a model that's linux-friendly.  I *love* programs like Anjuta, Amarok, grip, gaim, firefox, the list goes on... Linux is worth it.  So I don't care if the laptop is more expensive, if the hardware's linux-friendly, sign me up.

---

### Post by drosky on 2006-02-07
Darn, I was just considering getting an Inspiron 6000!

One question that comes to mind is does this happen either running
windows or another Linux distro (or the Ubuntu Live CD for that
matter).  If it happens in another OS or distro, it is more likely
to be a hardware problem.  Sometimes, hardware problems can
be temperature dependent, causing it to work better (or sometimes
worse) after it's warmed up.

Another question is whether the reload helped that you were going
to do last weekend?
Dave


[QUOTE=ScatterBrain]I've tried both the ATI and radeon drivers as well, and as you said - no luck.

It's looking more and more like I just need to reload and see what happens.  I've already looked for things like BIOS updates and such - nothing there.

Sorry to here about suspend in Dapper.  I really wish this could be better for us.

I think that, if I don't find a viable solution, this weekend I'll reload the machine.  It'll only take a couple of hours.[/QUOTE]

---

### Post by lol on 2006-02-07
I had a lot of lockups with my Inspiron 6000, not anymore though. I cannot be 100% sure, but I believe it was related to the wifi network... Since I don't really need it, I simply disabled it (I not longer load the ipw2200 module at startup, and also turned it off in the bios).
If disabling wifi is not an option, try upgrading the ipw2200 driver and firmware. There is a good HOWTO thread on how to do so, and I must admit I never add lockups with the updated driver, although I haven't used it a lot.

[http://doc.gwos.org/index.php/Install_ipw2200](http://doc.gwos.org/index.php/Install_ipw2200)

You could also try to uninstall wpa if you don't need it and if the above doesn't solve the problem.

Good luck!

---

### Post by fissy on 2006-02-24
My CPU usage problems have been 'solved' in dapper by using the 386 brand of kernel.

Unfortunately, wireless seems to have stopped working recently. Will have to spend some time with it this weekend.

---

### Post by dkittle on 2006-06-05
I have an Inspiron 5150 (P4 3Ghz, 1GB RAM, Broadcom wired and wireless nics) and have similar symptoms.  I had no problems running RedHat and Fedora Core (up to 5.0) on the laptop.  I did a fresh install of Ubuntu last thursday, enabled the new Broadcom wireless driver and the NVidia binary driver and I get random lockups every once in a while.  I noticed that if I waited for a while and moved the mouse around, the pointer would move a little bit after a couple of minutes.  Keep moving the mouse around after a few minuets the pointer would move again a little bit.  The lockup could happen less than a minute after boot or it could be several hours after booting.  I'll experiment with different things mentioned in the thread and post if anything helps.

---

