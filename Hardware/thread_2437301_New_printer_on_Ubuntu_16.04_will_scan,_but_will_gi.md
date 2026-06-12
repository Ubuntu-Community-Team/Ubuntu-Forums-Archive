---
title: "New printer on Ubuntu 16.04 will scan, but will give error message when try print"
date: 2020-02-21
forum: Hardware
---

### Post by crazybear on 2020-02-21
I had to revert to an older, but working printer. I have CUPS and XSANE installed and the other printer worked fine. Both printers show and the one now installed is listed as the default. However, I think the problem likely stems from a constant warning I see on the internet that there is a file somewhere that 'overrules' what is the default printer. I have searched high and low for this file and in all the many locations I have been told it would be, it is not to be found. If found, there is also no instruction of how exactly to change it - I would guess to remove name of old printer and put in name of new - but sometimes the name  is the model number, sometimes a model group and sometimes the brand and model/model group.

 So, if I send a file to be printed I sometimes get nothing and sometimes an error message that it cannot connect to printer. The computer is still looking for the old printer most likely even though elsewhere [like on  the print page] it shows correctly this printer and that print driver was [I'm almost sure] installed correctly.

Any ideas? This must be fixable.....if only I knew how.

Thanks much. It is scanning fine...but not using the Xsane program, which I'd prefer to use [that has the old printer name listed and I don't know how to change it]

---

### Post by brian_p on 2020-02-21
It is quite an achievement to post such detail and not mention the printer make and model. :)

---

### Post by him610 on 2020-02-21
Well crazybear, 
You have not provided much information about your system, your multi-function(?) printer models, specific error messages, nor connections between your system and printer/scanner.
Please show the results between the Code tags....
```

inxi -Fxz
lsusb
scanimage -L
apt list hplip

```
Drivers for new printer/scanner? Did you install the drivers? Where did you get the drivers from?
What have you accomplished to delete your old printer from CUPS configuration? The CUPS configuration utility can be found by Settings>Printers or from a terminal command line *system-config-printer*

---

### Post by him610 on 2020-02-21
This may apply to you [https://askubuntu.com/questions/1084235/scanner-not-detected-by-simple-scan]("https://askubuntu.com/questions/1084235/scanner-not-detected-by-simple-scan") if you happen to own a Canon device.

---

### Post by crazybear on 2020-02-21
Easy there guys and gals!......I was locked out of my flat by a rabid and illegal landlord.....my computer [and everything else seized inside.....homeless for some months and now barely back to life....with older stored equitment.]

Actually, this printer was installed on the system earlier and worked fine; later a newer printer [still seized, so not available]. The driver was still installed and it is an Ubuntu driver. Ancient Canon MP 540 is what I have to use until the Court battles.....months away in this country. In some places it lists this printer as the default now; other places it seems to be a hidden file [I forget the name now] that overrides what the default printer is, and still must have the newer [seized] one listed. That is what I think the problem is...[although not 100% sure]. How to find and change that override file....... It will print a test page from printers in system settings, but not print any document or photo, etc.

Sorry if I seem disorganized...my life is.....sorry.

```

$ inxi -Fxz
System:    Host: xxx-GA-X58A-UD7 Kernel: 4.15.0-88-generic x86_64 (64 bit gcc: 5.4.0)
           Desktop: Gnome 3.18.5 (Gtk 2.24.30) Distro: Ubuntu 16.04 xenial
Machine:   Mobo: Gigabyte model: X58A-UD7 Bios: Award v: F9d date: 09/01/2011
CPU:       Hexa core Intel Core i7 X 990 (-HT-MCP-) cache: 12288 KB
           flags: (lm nx sse sse2 sse3 sse4_1 sse4_2 ssse3 vmx) bmips: 41573
           clock speeds: max: 3459 MHz 1: 3612 MHz 2: 3575 MHz 3: 3608 MHz
           4: 3613 MHz 5: 3559 MHz 6: 3682 MHz 7: 3614 MHz 8: 3587 MHz
           9: 3562 MHz 10: 3605 MHz 11: 3553 MHz 12: 3616 MHz
Graphics:  Card: Advanced Micro Devices [AMD/ATI] Tahiti XT [Radeon HD 7970/8970 OEM / R9 280X]
           bus-ID: 03:00.0
           Display Server: X.Org 1.19.6 driver: N/A
           Resolution: 1920x1200@59.95hz, 1920x1200@59.95hz, 1920x1200@59.95hz
           GLX Renderer: AMD TAHITI (DRM 2.50.0 / 4.15.0-88-generic, LLVM 6.0.0)
           GLX Version: 3.0 Mesa 18.0.1 - padoka PPA Direct Rendering: Yes
Audio:     Card-1 Advanced Micro Devices [AMD/ATI] Tahiti HDMI Audio [Radeon HD 7870 XT / 7950/7970]
           driver: snd_hda_intel bus-ID: 03:00.1
           Card-2 Intel 82801JI (ICH10 Family) HD Audio Controller
           driver: snd_hda_intel bus-ID: 00:1b.0
           Card-3 Logitech HD Webcam C910 driver: USB Audio usb-ID: 002-003
           Sound: Advanced Linux Sound Architecture v: k4.15.0-88-generic
Network:   Card-1: Realtek RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
           driver: r8169 v: 2.3LK-NAPI port: be00 bus-ID: 07:00.0
           IF: enp7s0 state: down mac: <filter>
           Card-2: Realtek RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
           driver: r8169 v: 2.3LK-NAPI port: ae00 bus-ID: 08:00.0
           IF: enp8s0 state: up speed: 1000 Mbps duplex: full mac: <filter>
Drives:    HDD Total Size: 2508.3GB (37.0% used)
           ID-1: /dev/sda model: WDC_WD5000AAKB size: 500.1GB
           ID-2: USB /dev/sdb model: STORE_N_GO size: 7.7GB
           ID-3: /dev/sdd model: WDC_WD20EARS size: 2000.4GB
Partition: ID-1: / size: 917G used: 863G (100%) fs: ext4 dev: /dev/sdd1
RAID:      No RAID devices: /proc/mdstat, md_mod kernel module present
Sensors:   System Temperatures: cpu: 36.0C mobo: 27.0C gpu: 51.0
           Fan Speeds (in rpm): cpu: 684 fan-2: 856 fan-3: 1344 fan-4: 0
Info:      Processes: 406 Uptime: 2:14 Memory: 6723.1/23973.6MB
           Init: systemd runlevel: 5 Gcc sys: 5.5.0
           Client: Shell (bash 4.3.481) inxi: 2.2.35 
xxx-GA-X58A-UD7:~$ lsusb
Bus 002 Device 004: ID 18a5:0302 Verbatim, Ltd Flash Drive
Bus 002 Device 003: ID 046d:0821 Logitech, Inc. HD Webcam C910
Bus 002 Device 002: ID 04a9:1730 Canon, Inc. 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 002: ID e0ff:0002  
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 002: ID 1b1c:1b02 Corsair 
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 009 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 010 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
xxx-GA-X58A-UD7:~$ scanimage -L
Error my backend :    out of memory
device `pixma:04A91730_02280B' is a CANON Canon PIXMA MP540 multi-function peripheral
xxx-GA-X58A-UD7:~$ apt list hplip
Listing... Done
hplip/xenial,now 3.16.3+repack0-1 amd64 [installed]
W: Target Packages (main/binary-amd64/Packages) is configured multiple times in /etc/apt/sources.list.d/google-earth-pro.list:3 and /etc/apt/sources.list.d/google-earth.list:3
W: Target Packages (main/binary-i386/Packages) is configured multiple times in /etc/apt/sources.list.d/google-earth-pro.list:3 and /etc/apt/sources.list.d/google-earth.list:3
W: Target Packages (main/binary-all/Packages) is configured multiple times in /etc/apt/sources.list.d/google-earth-pro.list:3 and /etc/apt/sources.list.d/google-earth.list:3
W: Target Translations (main/i18n/Translation-en_US) is configured multiple times in /etc/apt/sources.list.d/google-earth-pro.list:3 and /etc/apt/sources.list.d/google-earth.list:3
W: Target Translations (main/i18n/Translation-en) is configured multiple times in /etc/apt/sources.list.d/google-earth-pro.list:3 and /etc/apt/sources.list.d/google-earth.list:3
W: Target DEP-11 (main/dep11/Components-amd64.yml) is configured multiple times in /etc/apt/sources.list.d/google-earth-pro.list:3 and /etc/apt/sources.list.d/google-earth.list:3
W: Target DEP-11-icons (main/dep11/icons-64x64.tar) is configured multiple times in /etc/apt/sources.list.d/google-earth-pro.list:3 and /etc/apt/sources.list.d/google-earth.list:3
N: There is 1 additional version. Please use the '-a' switch to see it


```

---

### Post by brian_p on 2020-02-21
Issue the command ```
lpinfo -m | grep MP540
``` in a terminal. Post what you get.

---

### Post by crazybear on 2020-02-21
$ lpinfo -m | grep MP540
gutenprint.5.2://bjc-MP540-series/expert Canon MP540 series - CUPS+Gutenprint v5.2.11
gutenprint.5.2://bjc-MULTIPASS-MP540/expert Canon PIXMA MP540 - CUPS+Gutenprint v5.2.11
gutenprint.5.2://bjc-PIXUS-MP540/expert Canon PIXUS MP540 - CUPS+Gutenprint v5.2.11

---

### Post by brian_p on 2020-02-21
> **crazybear said:**
> $ lpinfo -m | grep MP540
gutenprint.5.2://bjc-MP540-series/expert Canon MP540 series - CUPS+Gutenprint v5.2.11
gutenprint.5.2://bjc-MULTIPASS-MP540/expert Canon PIXMA MP540 - CUPS+Gutenprint v5.2.11
gutenprint.5.2://bjc-PIXUS-MP540/expert Canon PIXUS MP540 - CUPS+Gutenprint v5.2.11

There you are. Three PPDs. Yours might be the first one to use for printing. Use whatever you want to set up the print queue. The CUPS web interface at [http://localhost:631](http://localhost:631), perhaps.

---

### Post by crazybear on 2020-02-22
Great! Seems to be working somewhat. I think it just needs ink at this point....so will fill and find out. Seems to be going through motions of printing and scanning. There are two instances of this printer, but I don't see an option for deleting one. Perhaps it is not necessary.

---

### Post by crazybear on 2020-03-05
OK, you all helped some...but the system is still with faults and I still need help!
As I mentioned there is an override file and that caused GREAT problems. If I just print a document, it defaults to the printer that is not on the system now. Also, if I open a terminal and try to clear the print queue, it only will do so for that printer that is not there...
....so just now I can not print because of a problem I could fix if I could clear the print file of the printer actually on my system. I'd like to also correct that file that overrides the default printer. This problem has come up over and over...sometimes i can manually correct. Now, I can not - or do not know how to. Thanks.

---

### Post by CelticWarrior on 2020-03-05
Maybe you can set the (working) printer as the default?

---

### Post by crazybear on 2020-03-05
I have alread done that...BUT there are many different programs and places that 'set the default printer'. Everyone is ignoring this over-ride file. I see on the internet this is the problem, but I 1] can not locate it and 2] do not know how to modify it. Some programs see the printer attached as the default, but most do not, the computer/system do not!

---

### Post by crazybear on 2020-03-05
I think I just messed up everything. I deleted [in CUPS] the non-existant printer most often listed as default....and now nothingworks and CUPS is locked and won't work. I can't locate the name of this override file, but I've come accross it mentioned many many times and everytime it is said one MUST change what is in that file....but I never could find it and also when they say 'name of a printer' do not ever know what to put [e.g. do you put Canon MX-920 or Canon MX-920 series or MX-920?]...or does it matter and where does it matter?

---

### Post by crazybear on 2020-03-05
Printer [Canon_MP540_series]("http://localhost:631/printers/Canon_MP540_series") has been made the default printer on the server.
  [INDENT]**Note:** Any user default that has been set via the lpoptions command will override this default setting.


??????? - but this is not the file I'm referring to.
[/INDENT]

---

### Post by crazybear on 2020-03-05
$ lp
lp: Error - no default destination available.

$ lprm Camon-MP-540
lprm: Error - unknown destination "Camon-MP-540".


I can't find where this is misspelled...if that is the problem....

---

### Post by crazybear on 2020-03-05
I'm confused and this is confusing. one rule conflicts with another. one place on the system will set default printer, but it won't be recognized on/at another location.

---

