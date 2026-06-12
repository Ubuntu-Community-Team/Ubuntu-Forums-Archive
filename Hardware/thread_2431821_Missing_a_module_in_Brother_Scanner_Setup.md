---
title: "Missing a module in Brother Scanner Setup"
date: 2019-11-20
forum: Hardware
---

### Post by sansebar on 2019-11-20
Hello him610,

I am experiencing similar problems as the original author of this thread. May I ask you for help? 

I have installed a fresh Lubuntu 19.10 Eoan Ermine (Lubuntu!) from a DVD and want to get my brother scanner running. (On Lubuntu 16.10 LTS it worked fine). 

Then I did the following steps: 

As the directory did not exist:
```
[COLOR=#000000][FONT=Arial]~$ sudo mkdir /var/spool/lpd[/FONT][/COLOR]
```

Executed the "Driver Install Tool" from Brother (downloaded from here: [https://support.brother.com/g/b/downloadlist.aspx?c=de&lang=de&prod=mfc9180_eu&os=128&flang=English](https://support.brother.com/g/b/downloadlist.aspx?c=de&lang=de&prod=mfc9180_eu&os=128&flang=English))
 ```
[COLOR=#000000][FONT=Arial]~$ [/FONT][/COLOR]

[COLOR=#000000][FONT=Arial]Input model name ->MFC-9180[/FONT][/COLOR]

[COLOR=#000000][FONT=Arial]You are going to install following packages.[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]   mfc9180lpr-1.1.2-1.i386.deb[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]   cupswrapperMFC9180-1.0.2-1.i386.deb[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]   brscan-0.2.4-0.amd64.deb[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]   brscan-skey-0.2.4-1.amd64.deb                                        [/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]OK? [y/N] ->y                                                           [/FONT][/COLOR]

[COLOR=#000000][FONT=Arial]OK:1 http://de.archive.ubuntu.com/ubuntu eoan InRelease[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]OK:2 http://de.archive.ubuntu.com/ubuntu eoan-updates InRelease[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]OK:3 http://de.archive.ubuntu.com/ubuntu eoan-backports InRelease[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]OK:4 http://security.ubuntu.com/ubuntu eoan-security InRelease[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]Paketlisten werden gelesen... Fertig[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]Paketlisten werden gelesen... Fertig[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]Abhängigkeitsbaum wird aufgebaut.  [/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]Statusinformationen werden eingelesen.... Fertig[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]Paket ia32-libs ist nicht verfügbar, wird aber von einem anderen Paket[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]referenziert. Das kann heißen, dass das Paket fehlt, dass es abgelöst[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]wurde oder nur aus einer anderen Quelle verfügbar ist.[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]Doch die folgenden Pakete ersetzen es:[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]  lib32z1[/FONT][/COLOR]

[COLOR=#000000][FONT=Arial]E: Für Paket »ia32-libs« existiert kein Installationskandidat.[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]dpkg -x mfc9180lpr-1.1.2-1.i386.deb /[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]dpkg -x cupswrapperMFC9180-1.0.2-1.i386.deb /[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]dpkg-deb: Paket »mfc9180lpr« wird in »mfc9180lpr-1.1.2-1a.i386.deb« gebaut.[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]dpkg -b ./brother_driver_packdir mfc9180lpr-1.1.2-1a.i386.deb[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]dpkg-deb: Paket »cupswrappermfc9180« wird in »cupswrapperMFC9180-1.0.2-1a.i386.deb« gebaut.[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]dpkg -b ./brother_driver_packdir cupswrapperMFC9180-1.0.2-1a.i386.deb[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]dpkg -i --force-all mfc9180lpr-1.1.2-1a.i386.deb[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]dpkg: Warnung: Problem wird übergangen, weil --force angegeben ist:     [/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]dpkg: Warnung: Paket-Architektur (i386) passt nicht zum System (amd64)[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial](Lese Datenbank ... 265607 Dateien und Verzeichnisse sind derzeit installiert.)[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]Vorbereitung zum Entpacken von mfc9180lpr-1.1.2-1a.i386.deb ...[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]Entpacken von mfc9180lpr:i386 (1.1.2-1) über (1.1.2-1) ...[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]mfc9180lpr:i386 (1.1.2-1) wird eingerichtet ...[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]dpkg -i --force-all cupswrapperMFC9180-1.0.2-1a.i386.deb[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]dpkg: Warnung: Problem wird übergangen, weil --force angegeben ist:     [/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]dpkg: Warnung: Paket-Architektur (i386) passt nicht zum System (amd64)[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial](Lese Datenbank ... 265607 Dateien und Verzeichnisse sind derzeit installiert.)[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]Vorbereitung zum Entpacken von cupswrapperMFC9180-1.0.2-1a.i386.deb ...[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]Restarting cups (via systemctl): cups.service.[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]Entpacken von cupswrappermfc9180:i386 (1.0.2-1) über (1.0.2-1) ...[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]cupswrappermfc9180:i386 (1.0.2-1) wird eingerichtet ...[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]rm -f /usr/lib/cups/filter/brlpdwrapperMFC9180[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]Restarting cups (via systemctl): cups.service.[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]#[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]Will you specify the Device URI? [Y/n] ->n[/FONT][/COLOR]

[COLOR=#000000][FONT=Arial]Test Print? [y/N] ->y[/FONT][/COLOR]

[COLOR=#000000][FONT=Arial]wait 5s.[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]lpr -P MFC9180 /usr/share/cups/data/testprint[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]You are going to install following packages.[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]   brscan-0.2.4-0.amd64.deb[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]dpkg -i --force-all brscan-0.2.4-0.amd64.deb[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial](Lese Datenbank ... 265607 Dateien und Verzeichnisse sind derzeit installiert.)[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]Vorbereitung zum Entpacken von brscan-0.2.4-0.amd64.deb ...[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]Entpacken von brscan (0.2.4) über (0.2.4) ...[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]brscan (0.2.4) wird eingerichtet ...[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]You are going to install following packages.[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]   brscan-skey-0.2.4-1.amd64.deb[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]dpkg -i --force-all brscan-skey-0.2.4-1.amd64.deb[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial](Lese Datenbank ... 265607 Dateien und Verzeichnisse sind derzeit installiert.)[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]Vorbereitung zum Entpacken von brscan-skey-0.2.4-1.amd64.deb ...[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]Entpacken von brscan-skey (0.2.4-1) über (0.2.4-1) ...[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]brscan-skey (0.2.4-1) wird eingerichtet ...[/FONT][/COLOR]

```

So this worked fine except from the following that Lubuntu complains:[COLOR=#000000][FONT=Arial] (as I dont know if you understand german, I translated it to english)[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]package ia32-libs is not available, but is referenced from another package. This can mean , that the package is missing or is superseded or is only available from another source. But the following package[/FONT][/COLOR] is replacing it:
[COLOR=#000000][FONT=Arial]  lib32z[/FONT][/COLOR]

Restarted the PC.

Made me a participant in the scanner group: (where seb is my username)

```
[COLOR=#0000ff][FONT=Arial]~$ sudo usermod -a -G scanner seb[/FONT][/COLOR]
```

Edit config file: (whereas I add these two lines ***right above*** that line: [COLOR=blue]LABEL="libsane_rules_end"[/COLOR].)
```
[COLOR=#0000ff][FONT=Arial]# Brother scanners[/FONT][/COLOR]

[COLOR=#0000ff][FONT=Arial]ATTRS{idVendor}=="04f9", ENV{libsane_matched}="yes"[/FONT][/COLOR]



```


The printer is working fine now, but the scanner not. Simple-scan reports: [COLOR=#000000][FONT=Arial]Additional software needed. You need to install driver software for your scanner.

What to do?

[/FONT][/COLOR]

---

### Post by slickymaster on 2019-11-22
Moved to a thread of its own and thread title edited.

Please don't hijack other people's threads. Not only it dilutes community effort but it's also the wrong way to get the proper and adequate help to your problem.

---

### Post by him610 on 2019-11-22
Hallo sansebar,
I came upon your post as I was scrolling through the Hardware Forum just killing time. Your MFC9180 is a newer model than mine, but Brother does a pretty good job supporting Linux with its software. During all of my installations using Brother's *Driver Install Tool*, I have never found it necessary to modify any files. 
Let's see what you are working with...
From a terminal, post the results of these commands within code tags
```

inxi -Fz
dpkg -l | grep Brother
scanimage -L

```
Maybe we can figure this out and get your scanner working.

---

### Post by him610 on 2019-11-23
Well sansebar,
Today, on a fresh installation of Xubuntu 19.10, I downloaded the Brother Driver Install Tool. I followed the instructions to install the Driver Install Tool. 
> How to Install Driver Install Tool
Step1. Download the tool.(linux-brprinter-installer-*.*.*-*.gz)

The tool will be downloaded into the default "Download" directory.
(The directory location varies depending on your Linux distribution.)
e.g. /home/(LoginName)/Download

Step2. Open a terminal window.

Step3. Go to the directory you downloaded the file to in the last step. By using the cd command.

e.g. cd Downloads

Step4. Enter this command to extract the downloaded file:

Command: gunzip linux-brprinter-installer-*.*.*-*.gz

e.g. gunzip linux-brprinter-installer-2.1.1-1.gz

Step5. Get superuser authorization with the "su" command or "sudo su" command.

Step6. Run the tool:

Command: bash linux-brprinter-installer-*.*.*-* Brother machine name
e.g. bash linux-brprinter-installer-2.1.1-1 MFC-J880DW

Step7. The driver installation will start. Follow the installation screen directions.
 

 When you see the message "Will you specify the DeviceURI ?",

 For USB Users: Choose N(No)
 For Network Users: Choose Y(Yes) and DeviceURI number.

The install process may take some time. Please wait until it is complete.
Mine is a network printer so I did enter the DeviceURI number. 
Printed out a test page and scanned a page without ever rebooting. It just worked.
I don't know how else to advise you. Just follow the instructions to the letter. There is no need to modify files or add directories; the driver install tool does everything for you.
```
hugh@x1910:~$ dpkg -l | grep Brother
ii  brscan-skey                           0.2.4-1                             amd64        Brother Linux scanner S-KEY tool
ii  brscan4                               0.4.8-1                             amd64        Brother Scanner Driver
ii  cupswrappermfc7360n:i386              2.0.4-2                             i386         Brother MFC7360N CUPS wrapper driver
ii  mfc7360nlpr:i386                      2.1.0-1                             i386         Brother MFC-7360N LPR driver
ii  printer-driver-brlaser                5-1                                 amd64        printer driver for (some) Brother laser printers
ii  printer-driver-ptouch                 1.4.2-3                             amd64        printer driver Brother P-touch label printers

```
```
hugh@x1910:~$ scanimage -L
device `brother4:net1;dev0' is a Brother MFC-7360N MFC-7360N

```

---

### Post by sansebar on 2019-11-27
Hello him610,

thank you for your help.

In order to get the Brother MFC running, I followed this advice: [https://easylinuxtipsproject.blogspot.com/p/brother-printers.html](https://easylinuxtipsproject.blogspot.com/p/brother-printers.html)

This is what you asked me for:

```
~$ inxi -Fz
System:    Host: LenovoM72e Kernel: 5.3.0-23-generic x86_64 bits: 64 Desktop: LXQt 0.14.1 
           Distro: Ubuntu 19.10 (Eoan Ermine) 
Machine:   Type: Desktop System: LENOVO product: 3664AD7 v: ThinkCentre M72e serial: <filter> 
           Mobo: LENOVO model: N/A v: NO DPK serial: <filter> BIOS: LENOVO v: F1KT27AUS date: 10/19/2012 
CPU:       Topology: Dual Core model: Intel Pentium G630 bits: 64 type: MCP L2 cache: 3072 KiB 
           Speed: 1596 MHz min/max: 1600/2700 MHz Core speeds (MHz): 1: 1596 2: 1596 
Graphics:  Device-1: Intel 2nd Generation Core Processor Family Integrated Graphics driver: i915 v: kernel 
           Display: x11 server: X.Org 1.20.5 driver: modesetting unloaded: fbdev,vesa resolution: 1920x1080~60Hz 
           OpenGL: renderer: Mesa DRI Intel Sandybridge Desktop v: 3.3 Mesa 19.2.1 
Audio:     Device-1: Intel 6 Series/C200 Series Family High Definition Audio driver: snd_hda_intel 
           Sound Server: ALSA v: k5.3.0-23-generic 
Network:   Device-1: Realtek RTL8111/8168/8411 PCI Express Gigabit Ethernet driver: r8169 
           IF: enp2s0 state: up speed: 100 Mbps duplex: full mac: <filter> 
Drives:    Local Storage: total: 465.76 GiB used: 6.69 GiB (1.4%) 
           ID-1: /dev/sda vendor: Western Digital model: WD5000AAKX-08ERMA0 size: 465.76 GiB 
Partition: ID-1: / size: 39.12 GiB used: 6.63 GiB (16.9%) fs: ext4 dev: /dev/sda5 
           ID-2: swap-1 size: 4.30 GiB used: 0 KiB (0.0%) fs: swap dev: /dev/sda6 
Sensors:   System Temperatures: cpu: 30.0 C mobo: N/A 
           Fan Speeds (RPM): N/A 
Info:      Processes: 143 Uptime: 29m Memory: 3.67 GiB used: 866.5 MiB (23.1%) Shell: bash inxi: 3.0.36 

~$ dpkg -l | grep Brother
ii  brscan                                        0.2.4                               amd64        Brother CUPS Printer Definitions
ii  brscan-skey                                   0.2.4-1                             amd64        Brother Linux scanner S-KEY tool
ii  cupswrappermfc9180:i386                       1.0.2-1                             i386         Brother MFC9180 CUPS wrapper driver
ii  mfc9180lpr:i386                               1.1.2-1                             i386         Brother lpr Printer Definitions
ii  printer-driver-brlaser                        5-1                                 amd64        printer driver for (some) Brother laser printers
ii  printer-driver-ptouch                         1.4.2-3                             amd64        printer driver Brother P-touch label printers

~$ scanimage -L

No scanners were identified. If you were expecting something different,
check that the scanner is plugged in, turned on and detected by the
sane-find-scanner tool (if appropriate). Please read the documentation
which came with this software (README, FAQ, manpages).


```

Do you have an idea? 

PS: In the past I had the same MFC printing and scanning with Lubuntu 16.04.1 LTS - it worked fine!

---

### Post by him610 on 2019-11-29
This is from the set of instructions you followed,
>  Note: don't use the installation how-to on the Brother website, but use the installation how-to on my website instead (see below)!
I don't know why the writer would advise that. Could be an out of date article.
I have never experienced any issues getting my Brother MFC operational using the instructions on the Brother website so I have never had to figure out a troublesome installation.
How is your MFC-9180 connected to your computer? Network or USB?
I suggest restoring your system to a pristine condition (as it was when you initially installed 19.10) Download the Brother Driver Install Tool then follow the Brother instructions to the letter (refer to post #4). The tool will do the work for you - no need to edit any files or create new directories.

---

