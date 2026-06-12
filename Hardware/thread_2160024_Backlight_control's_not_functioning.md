---
title: "Backlight control's not functioning"
date: 2013-07-05
forum: Hardware
---

### Post by DGINSD on 2013-07-05
I just installed 13.04 in my HP pavilion G6 about a week ago an I've gotten most everything working now, with the exception of the display backlight. The hot keys will bring up the brightness slider and show it moving but the actual brightness does not change.  

Issueing a  

[CODE echo 5 | sudo tee /sys/devices/pci0000:00/0000:00:01.0/backlight/acpi_video0/brightness][/CODE]

```
 echo 1 | sudo tee /sys/devices/pci0000:00/0000:00:01.0/backlight/acpi_video0/brightness
```

changes the control files just as using the hotkeys does but the brightness doesn't change, this function worked perfectly in 12.04 and 12.10. If I hold the up or down hotkeys eventually brightness will change, so I can achieve my desired brightness by toggling between the setting I want and the one above or below it.

I've also tried adding the grub command line perimeters  separately and together

```
[COLOR=#000000]acpi_osi=Linux      acpi_backlight=vendor      [/COLOR][COLOR=#000000]acpi_osi=[/COLOR]
```

these also had no effect on the backlight control, but bad effects in other areas. "[COLOR=#000000]acpi_osi=" caused the machine not to boot entirely, "[/COLOR][COLOR=#000000]acpi_backlight=vendor[/COLOR][COLOR=#000000]" caused the hotkeys to not even change the notify slider.

I can't even use use scripts as changing the control files  doesn't consistently change the actual brightness. I'm open to any ideas and very much would like to get this fixed[/COLOR]

---

### Post by Toz on 2013-07-05
> **DGINSD said:**
> I've also tried adding the grub command line perimeters  separately and together

```
[COLOR=#000000]acpi_osi=Linux      acpi_backlight=vendor      [/COLOR][COLOR=#000000]acpi_osi=[/COLOR]
```

As a quick first suggestion, can you try the **acpi_osi=\"!Windows 2012\"** kernel parameter? The relevant entries in /etc/default/grub should look like this:
```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX="acpi_osi=\"!windows 2012\""
```
...(make sure you get the correct number of quote symbols in that last line).

Don't forget to run:
```
sudo update-grub
```
...and reboot.

Once rebooted, try the brightness keys again as well as posting back:
```
cat /proc/cmdline
```
...and
```
sudo lspci -vnn | grep -A15 VGA
```

---

### Post by DGINSD on 2013-07-05
I'll get on it as soon as I get back home to my computer.

I was hoping I'd get a response from you, you seem to be involved in a lot of the threads I found regarding brightness control issues. If I may offer a compliment, you seem to have a lot of good and creative ideas to work around these problems.

---

### Post by DGINSD on 2013-07-05
OK I added the grub command line entry ```
[COLOR=#000000][FONT=Ubuntu Mono]"acpi_osi=\"!windows 2012\""[/FONT][/COLOR]
```[COLOR=#000000][FONT=Ubuntu Mono] 

and then ```
sudo update-grub  

sudo reboot
```


After the reboot the problem persists just as before, no control when the hotkeys are pressed, but if held down change will eventu[/FONT][/COLOR][COLOR=#000000][FONT=Ubuntu Mono]ally be made, but this happens with no regularity.

Here is the output of the other two commands

[/FONT][/COLOR]```
david@HP-G6:~$ cat /proc/cmdlineBOOT_IMAGE=/boot/vmlinuz-3.8.0-26-generic root=UUID=f0ff1ffc-ca4e-416a-b47d-a6b0c7c4bbf0 ro "acpi_osi=!windows 2012" quiet splash vt.handoff=7

```[COLOR=#000000][FONT=Ubuntu Mono]

[/FONT][/COLOR]```
david@HP-G6:~$ sudo lspci -vnn | grep -A15 VGA
[sudo] password for david: 
00:01.0 VGA compatible controller [0300]: Advanced Micro Devices [AMD] nee ATI Sumo [Radeon HD 6480G] [1002:9649] (prog-if 00 [VGA controller])
    Subsystem: Hewlett-Packard Company Device [103c:169b]
    Flags: bus master, fast devsel, latency 0, IRQ 45
    Memory at e0000000 (32-bit, prefetchable) [size=256M]
    I/O ports at 4000 [size=256]
    Memory at f0500000 (32-bit, non-prefetchable) [size=256K]
    Expansion ROM at <unassigned> [disabled]
    Capabilities: [50] Power Management version 3
    Capabilities: [58] Express Root Complex Integrated Endpoint, MSI 00
    Capabilities: [a0] MSI: Enable+ Count=1/1 Maskable- 64bit+
    Capabilities: [100] Vendor Specific Information: ID=0001 Rev=1 Len=010 <?>
    Kernel driver in use: fglrx_pci


00:01.1 Audio device [0403]: Advanced Micro Devices [AMD] nee ATI BeaverCreek HDMI Audio [Radeon HD 6500D and 6400G-6600G series] [1002:1714]
    Subsystem: Advanced Micro Devices [AMD] nee ATI BeaverCreek HDMI Audio [Radeon HD 6500D and 6400G-6600G series] [1002:1714]
    Flags: bus master, fast devsel, latency 0, IRQ 44



```[COLOR=#000000][FONT=Ubuntu Mono]
[/FONT][/COLOR]

---

### Post by Toz on 2013-07-05
Oops, my bad. Typo. It should be **acpi_osi=\"!Windows 2012\"** (note the capital W). Can you try it again?

Also, after reboot, can you show the results of the following command:
```
for i in /sys/class/backlight/*; do echo $i; cat $i/brightness; cat $i/max_brightness; done
```

Can I also see your dmesg log file?
```
pastebinit /var/log/dmesg
```
...and post back the link that is generated.

---

### Post by DGINSD on 2013-07-05
Changed the grub command line parameter and ran update-grub as root, no change in status.

Ran the command you gave and here is the results

```
david@HP-G6:~$ for i in /sys/class/backlight/*; do echo $i; cat $i/brightness; cat $i/max_brightness; done/sys/class/backlight/acpi_video0
3
10

```

[http://paste.ubuntu.com/5848557/](http://paste.ubuntu.com/5848557/)

---

### Post by DGINSD on 2013-07-06
This likely has nothing to do with my backlight issue, or perhaps it does, but one of the lines in the dmesg outputstruck me as odd.
```
[COLOR=#000000][ 1.275630] powernow-k8: this CPU is not supported anymore, using acpi-cpufreq instead.[/COLOR]
```
On my other partition/install I h[COLOR=#000000]ad a script to change and adjust the CPU governor, and part of making the script work required loading the "[/COLOR][COLOR=#000000]powernow-k8"
 module, by adding it to the /etc/modules file. I hadn't tried using the set up on this install, as it seems much more efficient and doesn't seem to need it.

Just some[/COLOR][COLOR=#000000]thing that caught my eye, and perhaps totally irrelevant, but maybe a clue to a larger more general issue of my system configuration not 100% as it should be.[/COLOR]

---

### Post by Toz on 2013-07-06
> **DGINSD said:**
> Changed the grub command line parameter and ran update-grub as root, no change in status.

Ran the command you gave and here is the results

```
david@HP-G6:~$ for i in /sys/class/backlight/*; do echo $i; cat $i/brightness; cat $i/max_brightness; done/sys/class/backlight/acpi_video0
3
10

```

[http://paste.ubuntu.com/5848557/](http://paste.ubuntu.com/5848557/)

From your dmesg log file:
> [    0.230803] [Firmware Bug]: ACPI: No _BQC method, cannot determine initial brightness
[    0.231051] [Firmware Bug]: ACPI: No _BQC method, cannot determine initial brightness
[    0.231309] [Firmware Bug]: ACPI: No _BQC method, cannot determine initial brightness
Can you try the kernel parameters **acpi_osi=Linux acpi_backlight=vendor** again and after reboot, post back again:
```
pastebinit /var/log/dmesg
```
...and
```
for i in /sys/class/backlight/*; do echo $i; cat $i/brightness; cat $i/max_brightness; done
```

---

### Post by DGINSD on 2013-07-06
Ok this time I get no brightness change or notification with the up or down hotkeys. Also now in system settings, brightness & lock, there is no brightness slider. 

The pastebin link [http://paste.ubuntu.com/5850249/](http://paste.ubuntu.com/5850249/)

The output of the command given

```
david@HP-G6:~$ for i in /sys/class/backlight/*; do echo $i; cat $i/brightness; cat $i/max_brightness; done/sys/class/backlight/*
cat: /sys/class/backlight/*/brightness: No such file or directory
cat: /sys/class/backlight/*/max_brightness: No such file or directory



```

---

### Post by dino99 on 2013-07-06
This is fixed upstream in the 3.10-rc4 kernel by this commit:

author Ash Willis 2013-05-29
committer Rafael J. Wysocki 2013-06-01
commit 780a6ec640a3fed671fc2c40e4dd30c03eca3ac3

    ACPI / video: ignore BIOS initial backlight value for HP Pavilion g6

[https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/1173059](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/1173059)
[http://ubuntu.5.x6.nabble.com/3-8-y-z-extended-stable-Patch-quot-ACPI-video-ignore-BIOS-initial-backlight-value-for-HP-Pavilion-g6e-td5028617.html](http://ubuntu.5.x6.nabble.com/3-8-y-z-extended-stable-Patch-quot-ACPI-video-ignore-BIOS-initial-backlight-value-for-HP-Pavilion-g6e-td5028617.html)

---

### Post by DGINSD on 2013-07-06
> **dino99 said:**
> This is fixed upstream in the 3.10-rc4 kernel by this commit:

author Ash Willis 2013-05-29
committer Rafael J. Wysocki 2013-06-01
commit 780a6ec640a3fed671fc2c40e4dd30c03eca3ac3

    ACPI / video: ignore BIOS initial backlight value for HP Pavilion g6

[https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/1173059](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/1173059)
[http://ubuntu.5.x6.nabble.com/3-8-y-z-extended-stable-Patch-quot-ACPI-video-ignore-BIOS-initial-backlight-value-for-HP-Pavilion-g6e-td5028617.html](http://ubuntu.5.x6.nabble.com/3-8-y-z-extended-stable-Patch-quot-ACPI-video-ignore-BIOS-initial-backlight-value-for-HP-Pavilion-g6e-td5028617.html)


Is there a way for me to apply this fix, or do I just have to wait till the Ubuntu kernel reaches 3.10-rc4. The links you provided seem a bit over my head, but I'm definitely down for learning something new if someones willing to walk me through it.

---

### Post by Toz on 2013-07-06
> **dino99 said:**
> This is fixed upstream in the 3.10-rc4 kernel by this commit:

author Ash Willis 2013-05-29
committer Rafael J. Wysocki 2013-06-01
commit 780a6ec640a3fed671fc2c40e4dd30c03eca3ac3

    ACPI / video: ignore BIOS initial backlight value for HP Pavilion g6

[https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/1173059](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/1173059)
[http://ubuntu.5.x6.nabble.com/3-8-y-z-extended-stable-Patch-quot-ACPI-video-ignore-BIOS-initial-backlight-value-for-HP-Pavilion-g6e-td5028617.html](http://ubuntu.5.x6.nabble.com/3-8-y-z-extended-stable-Patch-quot-ACPI-video-ignore-BIOS-initial-backlight-value-for-HP-Pavilion-g6e-td5028617.html)

I'm not so sure this is the same issue. The bug report refers to the system booting to a blank screen. The OP's problem is not the black screen, but inconsistent keyboard brightness control. In addition, according to the bug report, the kernel parameters "acpi_osi=Linux acpi_backlight=vendor" work around the problem, yet in this case, it totally eliminates the backlight interface. The symptoms are not the same.

EDIT: Also, the bug report is for an intel graphics-based G6. OP has an ATi card.

@DGINSD, just to confirm, do you have an issue with booting to a black screen?

---

### Post by Toz on 2013-07-06
@DGINSD,

Can you go back to the original kernel parameters? Then after reboot:

1. Open a terminal window and type in:
```
acpi_listen
```
...then press the key combination to increase brightness once, and then the key combination to decrease brightness once. Post back whatever shows up in the terminal.

2. Can you enter the following commands and post back whether they change the brightness:
```
echo 7 | sudo tee /sys/class/backlight/acpi_video0/brightness
echo 3 | sudo tee /sys/class/backlight/acpi_video0/brightness
```

---

### Post by DGINSD on 2013-07-06
> **Toz said:**
> I'm not so sure this is the same issue. The bug report refers to the system booting to a blank screen. The OP's problem is not the black screen, but inconsistent keyboard brightness control. In addition, according to the bug report, the kernel parameters "acpi_osi=Linux acpi_backlight=vendor" work around the problem, yet in this case, it totally eliminates the backlight interface. The symptoms are not the same.

@DGINSD, just to confirm, do you have an issue with booting to a black screen?

I think your right I don't have the boot to dark screen and I just checked my 12.10 partition/install and it has the same dmesg
```
[COLOR=#000000]*[Firmware Bug]: ACPI: No _BQC method, cannot determine initial brightness*[/COLOR]]
```

Incidentally on my 12.10 install the backlight controls work perfectly, so it's something that's changed  with 13.04. Also I should mention after doing this install and noticing this issue, I found out there was a bios update available for my machine, I did the bios update but the issues still remained.

---

### Post by Toz on 2013-07-06
> **DGINSD said:**
> Incidentally on my 12.10 install the backlight controls work perfectly, so it's something that's changed  with 13.04.
Did you use the proprietary ATI drivers on the 12.10 install as well? Or the open source ones?

> Also I should mention after doing this install and noticing this issue, I found out there was a bios update available for my machine, I did the bios update but the issues still remained.
Good, that was a suggestion I was going to make. 

Can you run the steps in my previous post regarding acpi_listen and manual brightness control and let me know the results?

---

### Post by DGINSD on 2013-07-06
Both installs are using manually installed FGLRX video drivers

The output of acpi_listen
```
david@HP-G6:~$ acpi_listenbattery BAT0 00000080 00000001
battery BAT0 00000081 00000001
video LCD 00000086 00000000
video LCD 00000087 00000000
battery BAT0 00000080 00000001
battery BAT0 00000081 00000001
battery BAT0 00000080 00000001
battery BAT0 00000081 00000001

```

The "video LCD 00000086 00000000, video LCD 00000087 00000000" entrys occurred when pressing the hotkeys, manual execution of 
```
david@HP-G6:~$ echo 3 | sudo tee /sys/class/backlight/acpi_video0/brightness
3
david@HP-G6:~$ echo 7 | sudo tee /sys/class/backlight/acpi_video0/brightness
7

```

in another bash session produced no output in the shell running acpi_listen, neither produced a change in backlight brightness.

---

### Post by Toz on 2013-07-06
> **DGINSD said:**
>  manual execution of 
```
david@HP-G6:~$ echo 3 | sudo tee /sys/class/backlight/acpi_video0/brightness
3
david@HP-G6:~$ echo 7 | sudo tee /sys/class/backlight/acpi_video0/brightness
7

```

in another bash session produced no output in the shell running acpi_listen, neither produced a change in backlight brightness.

This is interesting. It should have changed brightness. Can you post back again:
```
cat /proc/cmdline
```
...and
```
for i in /sys/class/backlight/*; do echo $i; cat $i/brightness; cat $i/max_brightness; done
```

Can you also try the following commands to see if they adjust brightness:
```
sudo setpci -s 00:01.0 f4.b=80
sudo setpci -s 00:01.0 f4.b=ff
```

If possible, can you check your 12.10 install and run the first two commands (don't run setpci) on that install for comparison purposes?

---

### Post by DGINSD on 2013-07-06
```
david@HP-G6:~$ cat /proc/cmdlineBOOT_IMAGE=/boot/vmlinuz-3.8.0-26-generic root=UUID=f0ff1ffc-ca4e-416a-b47d-a6b0c7c4bbf0 ro quiet splash vt.handoff=7

```
```
david@HP-G6:~$ for i in /sys/class/backlight/*; do echo $i; cat $i/brightness; cat $i/max_brightness; done
/sys/class/backlight/acpi_video0
2
10
```
The other two commands had no effect on the actual brightness
```
david@HP-G6:~$ sudo setpci -s 00:01.0 f4.b=80

david@HP-G6:~$ for i in /sys/class/backlight/*; do echo $i; cat $i/brightness; cat $i/max_brightness; done
/sys/class/backlight/acpi_video0
2
10

david@HP-G6:~$ sudo setpci -s 00:01.0 f4.b=ff

david@HP-G6:~$ for i in /sys/class/backlight/*; do echo $i; cat $i/brightness; cat $i/max_brightness; done
/sys/class/backlight/acpi_video0
2
10
```

---

### Post by DGINSD on 2013-07-06
Here is the output of those first two commands on my 12.04 install
```
david@HP-G6:~$ cat /proc/cmdline
BOOT_IMAGE=/boot/vmlinuz-3.5.0-34-generic root=UUID=124123b2-547f-45fa-bc5a-f90c094e444f ro quiet splash
```
```
david@HP-G6:~$ for i in /sys/class/backlight/*; do echo $i; cat $i/brightness; cat $i/max_brightness; done/sys/class/backlight/acpi_video0
3
10
```

---

### Post by Toz on 2013-07-06
> **DGINSD said:**
> ```
david@HP-G6:~$ cat /proc/cmdlineBOOT_IMAGE=/boot/vmlinuz-3.8.0-26-generic root=UUID=f0ff1ffc-ca4e-416a-b47d-a6b0c7c4bbf0 ro quiet splash vt.handoff=7

```
```
david@HP-G6:~$ for i in /sys/class/backlight/*; do echo $i; cat $i/brightness; cat $i/max_brightness; done
/sys/class/backlight/acpi_video0
2
10
```
The other two commands had no effect on the actual brightness
```
david@HP-G6:~$ sudo setpci -s 00:01.0 f4.b=80

david@HP-G6:~$ for i in /sys/class/backlight/*; do echo $i; cat $i/brightness; cat $i/max_brightness; done
/sys/class/backlight/acpi_video0
2
10

david@HP-G6:~$ sudo setpci -s 00:01.0 f4.b=ff

david@HP-G6:~$ for i in /sys/class/backlight/*; do echo $i; cat $i/brightness; cat $i/max_brightness; done
/sys/class/backlight/acpi_video0
2
10
```

Can you now try with the **acpi_backlight=vendor** kernel parameter. After reboot, run:
```
cat /proc/cmdline
```
...and
```
for i in /sys/class/backlight/*; do echo $i; cat $i/brightness; cat $i/max_brightness; done
```

Also, I don't have an ATI card. Is there a setting somewhere in the ATI driver that controls brightness? Maybe the proprietary driver is somehow interfering.

---

### Post by DGINSD on 2013-07-06
```
david@HP-G6:~$ cat /proc/cmdline
BOOT_IMAGE=/boot/vmlinuz-3.8.0-26-generic root=UUID=f0ff1ffc-ca4e-416a-b47d-a6b0c7c4bbf0 ro acpi_backlight=vendor quiet splash vt.handoff=7
```
```
david@HP-G6:~$ for i in /sys/class/backlight/*; do echo $i; cat $i/brightness; cat $i/max_brightness; done/sys/class/backlight/*
cat: /sys/class/backlight/*/brightness: No such file or director[COLOR=#000000]Is it possible with the bios update being done afete the initial install[/COLOR]y
cat: /sys/class/backlight/*/max_brightness: No such file or directory
```

[COLOR=#000000]No brightness change or notification with the up or down hotkeys, in system settings, brightness & lock, there is no brightness slider. [/COLOR]

[COLOR=#000000]As far as I know the only thing with the FGLRX driver that has to do with backlight is a feature called vari-Bright  that works with the power-play functions which I have completely shut off. Basically it's supposed to work like the dim display when inactive feature of Ubuntu, but it's very obnoxious and just continually moves brightness up and down.

I put the install disc back in and booted off it to see if the backlight functions worked with that, and while it still was buggy, it was significantly more resopnsive, seemed to move in steps of 2, so 5 steps instead of 10.

[/COLOR][COLOR=#000000][FONT=Verdana]Is it possible with the bios update being done after the initial install, something could of been configured incorrectly during install? I've had kernel updates since the bios update and I would think any issues would of been corrected then but I'm not sure that's the case[/FONT][/COLOR]

---

### Post by Toz on 2013-07-06
Okay. Lets try again the **acpi_osi=\"!Windows 2012\"** parameter.

Again:
```
cat /proc/cmdline
```
...and
```
for i in /sys/class/backlight/*; do echo $i; cat $i/brightness; cat $i/max_brightness; done
```

Check brightness slider, notifications and function keys.

> I put the install disc back in and booted off it to see if the backlight functions worked with that, and while it still was buggy, it was significantly more resopnsive, seemed to move in steps of 2, so 5 steps instead of 10.
There is obviously some sort of regression between 12.10 and 13.04.

---

### Post by DGINSD on 2013-07-06
```
david@HP-G6:~$ cat /proc/cmdlineBOOT_IMAGE=/boot/vmlinuz-3.8.0-26-generic root=UUID=f0ff1ffc-ca4e-416a-b47d-a6b0c7c4bbf0 ro "acpi_osi=!Windows 2012" quiet splash vt.handoff=7

```
```
david@HP-G6:~$ for i in /sys/class/backlight/*; do echo $i; cat $i/brightness; cat $i/max_brightness; done/sys/class/backlight/acpi_video0
2
10
```
Same as before hotkeys will bring up notification indicator and show changes, but no actual, consistent, change in display brightness. If held full up, full down, or toggled back and forth rapidly, a change will eventually get made. The slider in system settings, brightness & lock, produces no change when moved at all, even when sliding it up, down, up, down, etc.

---

### Post by Toz on 2013-07-07
Does manually manipulating the interface work with this kernel parameter?
```
echo 5 | sudo tee /sys/class/backlight/acpi_video0/brightness
echo 0 | sudo tee /sys/class/backlight/acpi_video0/brightness
echo 7 | sudo tee /sys/class/backlight/acpi_video0/brightness
```

What modules are loaded?
```
lsmod
```

Did you blacklist any modules?

If possible, can you try disabling the proprietary drivers and using the opensource drivers. It would be interesting to see if backlight control works with the opensource driver.

---

### Post by DGINSD on 2013-07-07
I haven't blacklisted any modules, though I had to on my old install of 12.04 and 12.10, but both modules were wireless drivers that were trying to load with the STA drivers and causing a conflict. Oddly enough I didn't have to do that this time around but I did have another wifi issue which I'm learning is related to the bios update. Here is lsmod.
 ```
david@HP-G6:~$ sudo lsmod[sudo] password for david: 
Module                  Size  Used by
michael_mic            12612  12 
arc4                   12615  6 
parport_pc             28152  0 
ppdev                  17073  0 
bnep                   18036  2 
rfcomm                 42641  12 
binfmt_misc            17500  1 
snd_hda_codec_idt      70256  1 
snd_hda_codec_hdmi     36913  1 
snd_hda_intel          39619  5 
snd_hda_codec         136453  3 snd_hda_codec_hdmi,snd_hda_codec_idt,snd_hda_intel
uvcvideo               80847  0 
snd_hwdep              13602  1 snd_hda_codec
snd_pcm                97451  3 snd_hda_codec_hdmi,snd_hda_codec,snd_hda_intel
videobuf2_vmalloc      13056  1 uvcvideo
videobuf2_memops       13202  1 videobuf2_vmalloc
joydev                 17377  0 
videobuf2_core         40513  1 uvcvideo
videodev              129260  2 uvcvideo,videobuf2_core
snd_page_alloc         18710  2 snd_pcm,snd_hda_intel
lib80211_crypt_tkip    17379  0 
fglrx                5294837  119 
btusb                  22474  0 
kvm_amd                59717  0 
wl                   3074449  0 
hp_wmi                 18048  0 
snd_seq_midi           13324  0 
kvm                   443165  1 kvm_amd
snd_seq_midi_event     14899  1 snd_seq_midi
bluetooth             228619  22 bnep,btusb,rfcomm
snd_rawmidi            30180  1 snd_seq_midi
snd_seq                61554  2 snd_seq_midi_event,snd_seq_midi
sparse_keymap          13890  1 hp_wmi
snd_seq_device         14497  3 snd_seq,snd_rawmidi,snd_seq_midi
snd_timer              29425  2 snd_pcm,snd_seq
lib80211               14352  2 wl,lib80211_crypt_tkip
microcode              22881  0 
snd                    68876  20 snd_hwdep,snd_timer,snd_hda_codec_hdmi,snd_hda_codec_idt,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec,snd_hda_intel,snd_seq_device
rtsx_pci_ms            13011  0 
psmouse                95870  0 
wmi                    19070  1 hp_wmi
memstick               16554  1 rtsx_pci_ms
i2c_piix4              13266  0 
k10temp                13126  0 
cfg80211              510937  1 wl
soundcore              12680  1 snd
mac_hid                13205  0 
amd_iommu_v2           19068  1 fglrx
video                  19390  0 
lp                     17759  0 
serio_raw              13215  0 
parport                46345  3 lp,ppdev,parport_pc
rtsx_pci_sdmmc         17475  0 
rtsx_pci               33355  2 rtsx_pci_ms,rtsx_pci_sdmmc
r8169                  67446  0 
ahci                   25731  4 
libahci                31364  1 ahci



```
I actually decided this morning to experiment a bit and get rid of my mint install and try re-installing 13.04 on that partition, so far so good I actually have backlight control, though is as I stated in an earlier post only 5 steps, but it works every time like clockwork. I just finished installing the FGLRX drivers and popped back over to my original 13.04 install to make a yppa backup file, and installed software list, in between the reboot for the graphics install.

If this ends up working perfectly, I'll be very curious why a reinstall was nessessary to fix the issue? I tried kernel re-installation and initrd reconfiguration using dpkg, though I'm not sure I did that correctly. In the interest of learning something I'd really like to continue to try and fix the original install. BTW I'm very appreciative of all the help you've offered me.

EDIT:  Interestingly enough turns out it is the video driver the backlight controls no longer work after the reboot, Think I should try an older version of the driver?

---

### Post by Toz on 2013-07-07
> EDIT: Interestingly enough turns out it is the video driver the backlight controls no longer work after the reboot, Think I should try an older version of the driver?  
You could (unfortunately I have very little experience with ati drivers to be of assistance). You might also want to submit a bug report against that version of the video driver. There is obviously some sort of regression happening here.

If you don't mind, I'd be interested in seeing:
```
modinfo fglrx
```

---

### Post by DGINSD on 2013-07-07
I guess I'm stuck with the problem till AMD or Ubuntu releases a fix for it, installing the Catalyst 12.10 driver produces an error (no kernel module named apport found) and causes X to break (the backlights do still work though, LOL) this causes almost a completely un-recoverable state where even tty1 is scrambled and the Xsession tty7 only produces a wallpaper. I suppose a new custom kernel could be compiled, but I'm not sure I'm up for that right now.

---

### Post by Toz on 2013-07-07
Not sure if this is helpful, but there are instructions [here]("https://help.ubuntu.com/community/BinaryDriverHowto/ATI") for installing the upstream drivers.

---

### Post by DGINSD on 2013-07-08
I actually installed the 13.6 beta version of the driver, didn't do anything for the backlight situation, but it did fix an issue I was having with the shutdown plymouth screen the "Ubuntu" on the purple background was smearing off to the right, for lack of a better way to describe it. 

I filed a bug with AMD, or at least tried to. I don't really know what information would be best to send, so I guess that will be my next project; learning to gather relevant bug info.

---

### Post by Toz on 2013-07-08
> **DGINSD said:**
> I filed a bug with AMD, or at least tried to. I don't really know what information would be best to send, so I guess that will be my next project; learning to gather relevant bug info.
I don't have an ati card to test with, but you should be able to:
```
apport-bug fglrx
```
...and it will lead you through the bug creation process and upload some basic information to kick start the process.

---

### Post by DGINSD on 2013-07-09
Oh do I feel stupid...

I've gotten in the habit of downloading and building my own graphics drivers direct from AMD, basically because every time I install Ubuntus they never seem to work. So just out of being thorough I purged my last installed FGLRX install and installed the Ubuntu FGLRX-Updates driver and no kidding, all works perfectly, go figure.

Thanks a lot for your time and help I really do appreciate it.

---

