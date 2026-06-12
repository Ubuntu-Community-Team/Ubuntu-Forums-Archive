---
title: "New to Linux. Need Help getting Sound card set up"
date: 2005-10-04
forum: Hardware &amp; Laptops
---

### Post by waslost1 on 2005-10-04
I have installed UBUNTU 5.04 succesfully on an older Dell Optiplex PC with a Crystal Audio 4236b sound chipset built into the motherboard. Everything seems to work except the sound. About a year ago I tried to load a Mandrake version and before that a RedHat version. As I recall, I had problems with the sound card then as well. I never have gotten it working correctly with anything but Windows.
I have NEVER used Linux in any real capacity so please go easy on me. I have searched the forums here but to be honest, I don't understand a lot about the solutions that others have used. As I said, I am brand new to the Linux world. I know I have a steep learning curve ahead but I have no idea where to start righ now. 
So far I like what I see. I am very excited about learning more.
Any thoughts or suggestions are appreciated.
Tim

---

### Post by Biased turkey on 2005-10-04
1st, welcome to Ubuntuforums.
Getting the sound working with Ubuntu can be tricky sometime, it depends of your sound chip.

1) in a terminal window, run the following command:
lspci
It should display a list of what hardware is on your computer, such as chipset, graphic card and ... your sound chip ( or card ).
On my system, the interesting line says:
0000:00:0c.0 Multimedia audio controller: Ensoniq ES1371 [AudioPCI-97] (rev 06)

2) Now that you know that your sound hardware is detected, you should check if the software module to have it working is installed. Run the following command:
lsmod
some interesting lines are:

snd_ens1371            22624  2
snd_rawmidi            22944  1 snd_ens1371
snd_seq_device          8332  1 snd_rawmidi
snd_ac97_codec         64608  1 snd_ens1371
snd_pcm_oss            47652  1
snd_mixer_oss          16768  2 snd_pcm_oss
snd_pcm                84872  3 snd_ens1371,snd_ac97_codec,snd_pcm_oss
snd_timer              23300  1 snd_pcm
snd                    50276  8 snd_ens1371,snd_rawmidi,snd_seq_device,snd_ac97_codec,snd_pcm_oss ,snd_mixer_oss,snd_pcm,snd_timer
soundcore               9824  3 snd
snd_page_alloc          9604  1 snd_pcm

---

### Post by waslost1 on 2005-10-04
Thanks for responding. I really appreciate the opportunity to learn.

Looks like my hardware was not detected so I guess I need to start there...

I ran lspci and got the following (no mention of anything audio)

0000:00:00.0 Host bridge: Intel Corp. 440BX/ZX/DX - 82443BX/ZX/DX Host bridge (r ev 03)
0000:00:01.0 PCI bridge: Intel Corp. 440BX/ZX/DX - 82443BX/ZX/DX AGP bridge (rev  03)
0000:00:07.0 ISA bridge: Intel Corp. 82371AB/EB/MB PIIX4 ISA (rev 02)
0000:00:07.1 IDE interface: Intel Corp. 82371AB/EB/MB PIIX4 IDE (rev 01)
0000:00:07.2 USB Controller: Intel Corp. 82371AB/EB/MB PIIX4 USB (rev 01)
0000:00:07.3 Bridge: Intel Corp. 82371AB/EB/MB PIIX4 ACPI (rev 02)
0000:00:0f.0 PCI bridge: Digital Equipment Corporation DECchip 21152 (rev 03)
0000:00:11.0 Ethernet controller: 3Com Corporation 3c905B 100BaseTX [Cyclone] (r ev 24)
0000:01:00.0 VGA compatible controller: ATI Technologies Inc 3D Rage Pro AGP 1X/ 2X (rev 5c)

************************************************

Just in case you wanted the results of the lsmod

Module                  Size  Used by
proc_intf               4100  0
freq_table              4100  0
cpufreq_userspace       4572  0
cpufreq_ondemand        6172  0
cpufreq_powersave       1920  0
video                  16260  0
sony_acpi               6280  0
pcc_acpi               11264  0
button                  6800  0
battery                10244  0
container               4608  0
ac                      4996  0
ipv6                  229376  9
af_packet              20744  2
3c59x                  37160  0
i2c_piix4               8592  0
i2c_core               21264  1 i2c_piix4
uhci_hcd               30224  0
usbcore               107384  2 uhci_hcd
pci_hotplug            30512  0
intel_agp              20636  1
agpgart                31784  1 intel_agp
floppy                 54864  0
rtc                    12216  0
pcspkr                  3816  0
md                     43856  0
dm_mod                 53116  1
capability              5000  0
commoncap               7808  1 capability
tsdev                   7488  0
evdev                   9088  0
psmouse                19336  0
mousedev               11160  1
parport_pc             34372  1
lp                     10792  0
parport                33480  2 parport_pc,lp
ide_cd                 38532  0
cdrom                  36508  1 ide_cd
ext3                  120968  1
jbd                    54168  1 ext3
ide_generic             1664  0
piix                    9988  1
ide_disk               18176  4
ide_core              118988  4 ide_cd,ide_generic,piix,ide_disk
unix                   26164  787
thermal                13576  0
processor              22708  1 thermal
fan                     4612  0
fbcon                  34048  0
font                    8448  1 fbcon
bitblit                 5120  1 fbcon
vesafb                  6948  0
cfbcopyarea             3968  1 vesafb
cfbimgblt               3072  1 vesafb
cfbfillrect             3584  1 vesafb

What next?

---

### Post by az on 2005-10-05
[https://wiki.ubuntu.com/forum/hardware/OldSoundCard](https://wiki.ubuntu.com/forum/hardware/OldSoundCard)

snd-cs4236= Generic driver for CS4235/6/7/8/9 chips

sudo modprobe snd-cs4236

If that module loads, add it to your /etc/modules and reboot....

---

### Post by earthman on 2005-10-05
Azz you bear a striking resemblance to an old fat Captain Kirk.

---

### Post by waslost1 on 2005-10-12
[QUOTE=azz][https://wiki.ubuntu.com/forum/hardware/OldSoundCard](https://wiki.ubuntu.com/forum/hardware/OldSoundCard)

snd-cs4236= Generic driver for CS4235/6/7/8/9 chips

sudo modprobe snd-cs4236

If that module loads, add it to your /etc/modules and reboot....[/QUOTE]


Thanks Azz, that worked. Being new and all, it took me a little while to figure out what you were saying. In case someone else is in my shoes, I will explain...

sudo modprobe snd-cs4236 was a command line entry which loaded the module that pertained to my sound card. Since the module loaded, you had me open the /etc/modules file (logged in as root) and add this module so that it would load automatically upon a reboot. Obviously, if it had not loaded then I would have had to find out why and correct that first. Guess I was lucky.

It seems so obvious to me now, but like I said, being new, not everything is as obvious as it should be. I did learn a little more about how Linux boots up. 

I am assuming that the etc/modules file only pertains to the GUI such as KDE or gnome. Is that correct or does the operating system load these modules before (independent) of the GUI? I realize that the GUI is not the operating system so I am trying keep clear in my head how all of these things go together so I can better learn to troubleshoot things in the future.

Thanks very much for the help. Really enjoying the Linux experience. I am beginning to experiment with WINE now to see if I can get a few Windows Only apps to work. IF so, I may switch over to Linux as my primary OS. Would be nice to be less reliant on a single operating system. Windows isn't bad, but they could learn a lot from the open source example.

---

