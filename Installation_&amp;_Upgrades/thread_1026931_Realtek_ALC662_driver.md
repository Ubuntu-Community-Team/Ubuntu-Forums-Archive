---
title: "Realtek ALC662 driver"
date: 2008-12-31
forum: Installation &amp; Upgrades
---

### Post by bmiller59 on 2008-12-31
Hello. I am a novice user and I need to install drivers for the Realtek ALC662 audio device. I cannot follow the manual instructions and the auto install does not work. Can anyone send me an auto installer for this card or walk me through the process? Thank you.

The driver files can be found here:
[http://www.realtek.com.tw/downloads/downloadsCheck.aspx?Langid=1&PNid=14&PFid=24&Level=4&Conn=3&DownTypeID=3&GetDown=false](http://www.realtek.com.tw/downloads/downloadsCheck.aspx?Langid=1&PNid=14&PFid=24&Level=4&Conn=3&DownTypeID=3&GetDown=false)

---

### Post by pytheas22 on 2008-12-31
First of all, please try running this command:
```

echo 'options snd-hda-intel model=laptop' | sudo tee -a /etc/modprobe.d/options
```

Then reboot.  Any chance your sound works now?  According to this [bug report]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/282116") which seems to relate to your issue, this might help.

If not, we can try installing Realtek's drivers.

---

### Post by bmiller59 on 2009-01-01
Thank you! That seems to have worked. 

I wanted to thank you, and all the technical wizards who support us Linux novices. It may seem annoying, but the more we are able to be successful in using Linux, the more the tide will shift away from competitors like Windows. :)

---

### Post by pytheas22 on 2009-01-01
Glad that did it :)

---

### Post by manjusri on 2009-05-24
I m trying to install the Realtek alc662driver but I don't understand the following lines of theprocess of installation:
"turn on sound support from kernel config
(soundcore module,default turn on)
how to make this? thanks for your help](*,)

---

### Post by manjusri on 2009-05-24
> **pytheas22 said:**
> First of all, please try running this command:
```

echo 'options snd-hda-intel model=laptop' | sudo tee -a /etc/modprobe.d/options
```

Then reboot.  Any chance your sound works now?  According to this [bug report]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/282116") which seems to relate to your issue, this might help.

If not, we can try installing Realtek's drivers.
I have tried the command line you replied to  bmiller59 but it doesn't work.thanks

---

### Post by pytheas22 on 2009-05-24
**manjusri**: please post the output of these commands:
```

cat /etc/modprobe.d/options
uname -rm
```

---

### Post by manjusri on 2009-06-01
can you explain to me the fourth step of the installation of teh realtek alc662 driver:
1how to edit my  /etc/modules.conf
2how to determinate mycard id(alc6622is not referenced);what controler do I use?
thanks of your help

---

### Post by pytheas22 on 2009-06-02
> **manjusri said:**
> can you explain to me the fourth step of the installation of teh realtek alc662 driver:
1how to edit my  /etc/modules.conf
2how to determinate mycard id(alc6622is not referenced);what controler do I use?
thanks of your help

1. you can edit /etc/modules by opening a terminal and typing:
```

sudo gedit /etc/modules
```

and the file will open in a text editor for you.

2. if you post the output of the command:
```

lspci -nn
```

I should be able to tell you which controller you have.

It would also be helpful if you posted a link to the instructions you're trying to follow.

Vous pouvez communiquer en français si c'est plus simple pour vous.

---

### Post by manjusri on 2009-06-08
voici la ptrocedure complete d'installation The source code copy from [www.alsa-project.org](www.alsa-project.org).      ver:3.3-4
Linux Source Code for ALC audio codec
Support Codec list:
====AC97 Codec=====
ALC100,100P
ALC200,200P
ALC650D
ALC650E
ALC650F
ALC650
ALC655
ALC653
ALC658
ALC658D
ALC850
ALC101
ALC202
ALC250
ALC203

====HD Audio codec ====
ALC260
ALC262
ALC267
ALC268
ALC269
ALC272
ALC660
ALC660VD
ALC662
ALC663
ALC861
ALC861VD
ALC880
ALC882
ALC883
ALC885
ALC888
ALC889A

Installation:
This Source Code is from [www.alsa-project.org](www.alsa-project.org).
For OS installation, please remember add the Development tool kit.
For driver installation, please follow below steps. 

Automatic install: (Recommend RedHat distribution)
execute

  ./install

Note: Ubuntu OS, please use manual install.
      Run commands need to add sudo at first words.   

Manual install:
Step 1. unzip source code
        tar xfvj alsa-driver-1.0.xx.tar.bz2

Step 2. Turn on sound support from kernel config 
    (soundcore module, default turn on)

Step 3. Complied source code
    a. cd alsa-driver-1.0.xx
    b. ./configure
    c. make
    d. make install
    e. alsaconf
    f. ./snddevices (Only kernel 2.4 does it)

Step 4. Edit your /etc/modules.conf or conf.modules depending on the distribution
     (Please refer to the attached modules.conf)
     
        snd-xxxx is the card ID.

    -- Azalia controller --ALC880 ALC882 ALC260 ALC262 ALC883 ALC885 ALC888
       --- Intel ICH6 ICH7 ---------
               snd-hda-intel

        -- AC97 controller --ALC655 ALC650 ALC250 ALC255
           --- Intel ICH6 ICH7 , SiS 7012 and NVidia----------
               snd-intel8x0
           --- Via8233 Via686a  -------------------------------    
           snd-via82xx
           --- ATI Chipset  -------------------------------
           snd-atiixp

        Copy and paste this to the bottom of your /etc/modules.conf or /etc/modprobe.conf file.
    # ALSA portion
          alias char-major-116 snd
          alias snd-card-0 snd-xxxx     
        # OSS/Free portion
          alias char-major-14 soundcore
          alias sound-slot-0 snd-card-0
        # card #1
          alias sound-service-0-0 snd-mixer-oss
          alias sound-service-0-1 snd-seq-oss
          alias sound-service-0-3 snd-pcm-oss
          alias sound-service-0-8 snd-seq-oss
          alias sound-service-0-12 snd-pcm-oss

Step 5. reboot your machine

Step 6. Use the alsamixer the disable mute (All audio line default is mute)
        *Must to compile and to install the ALSA library and utility. (Use automatic install is already install)
        excute alsamixer

Note:     1. The most detail information, can refer the alsa-kernel/Documenttation/ALSA-Configuration.txt in the azx-021705.tar.bz2.
    2. Kernel Version must be 2.2.14 or later.
    3. All mixer channels are muted by default. You must use a native
        or OSS mixer program to unmute appropriate channels.
    4. If can not compile the source code, try to rename the /usr/src/linux-2.x -> /usr/src/linux.
    5. The driver added to support the SPDIF functoin.     
    6. a. You can download the alsa-lib-1.0.9 and alsa-utils-1.0.9a form the [www.alsa-project.org](www.alsa-project.org), then unzip and install them. 
       b. Suggest use "alsamixer" to control mixer function.
       c. Used "alsaconf" can autodetect which drive you need to install (step 4).     
        7. SUSE Distribution must install the ncurses package. du driver
;je ne me sens pas tres pres d'y arriver...

---

### Post by manjusri on 2009-06-08
ce qui ne marche pas:
1)tar xfvj probleme au niveau des options ;je n'ai rien compris a tar --usage
2)je ne sais tjrs pas comment faire cette operation
3)ça ne devrait pas poser de problemes
4)je pense que les explications de pytheas marcheront.doije copier tout ou partie de "copy and paste
5)je sais faire:lolflag:
6)j'ai besoin d'explications
merci beaucoup;je suis ravi d'apprendre;vive ubuntu):P

---

### Post by manjusri on 2009-06-08
> **manjusri said:**
> ce qui ne marche pas:
1)tar xfvj probleme au niveau des options ;je n'ai rien compris a tar --usage
2)je ne sais tjrs pas comment faire cette operation
3)ça ne devrait pas poser de problemes
4)je pense que les explications de pytheas marcheront.doije copier tout ou partie de "copy and paste
5)je sais faire:lolflag:
6)j'ai besoin d'explications
merci beaucoup;je suis ravi d'apprendre;vive ubuntu):P
au lieu de tar xfvj j'ai utilise le gestionnaire d'archives en mode graphique

---

### Post by pytheas22 on 2009-06-08
manjusri: excuse ma réponse tardive.

Je pense que vous ne voulez pas installer ALSA, comme ALSA est déjà installé en Ubuntu.  Vous n'avez donc pas besoin des instructions de alsa-project.org.

Pour donner une solution à votre problème, j'ai besoin de voir le output de ces commandes:
```

lspci -nn
lshw
```

Si vous pourriez les fournir ici, je chercherai une solution.  Pour le moment, vous pouvez ignorer les instructions pour l'installation de ALSA.

---

### Post by manjusri on 2009-06-08
voici les reseignements demandes en piece jointe.merci beaucoup phyteas

---

### Post by manjusri on 2009-06-09
bon ca ne marche pas d'attacher le document en piece jointe ni le copier coller.va falloir que je le recopie manuellement aplus

---

### Post by manjusri on 2009-06-09
vrabgye@ubuntumaya:~$ lspci -nn
00:00.0 Host bridge [0600]: Silicon Integrated Systems [SiS] 671MX [1039:0671]
00:01.0 PCI bridge [0604]: Silicon Integrated Systems [SiS] SiS AGP Port (virtual PCI-to-PCI bridge) [1039:0003]
00:02.0 ISA bridge [0601]: Silicon Integrated Systems [SiS] SiS968 [MuTIOL Media IO] [1039:0968] (rev 01)
00:02.5 IDE interface [0101]: Silicon Integrated Systems [SiS] 5513 [IDE] [1039:5513] (rev 01)
00:03.0 USB Controller [0c03]: Silicon Integrated Systems [SiS] USB 1.1 Controller [1039:7001] (rev 0f)
00:03.1 USB Controller [0c03]: Silicon Integrated Systems [SiS] USB 1.1 Controller [1039:7001] (rev 0f)
00:03.3 USB Controller [0c03]: Silicon Integrated Systems [SiS] USB 2.0 Controller [1039:7002]
00:04.0 Ethernet controller [0200]: Silicon Integrated Systems [SiS] 191 Gigabit Ethernet Adapter [1039:0191] (rev 02)
00:05.0 IDE interface [0101]: Silicon Integrated Systems [SiS] SATA Controller / IDE mode [1039:1183] (rev 03)
00:06.0 PCI bridge [0604]: Silicon Integrated Systems [SiS] PCI-to-PCI bridge [1039:000a]
00:07.0 PCI bridge [0604]: Silicon Integrated Systems [SiS] PCI-to-PCI bridge [1039:000a]
00:0f.0 Audio device [0403]: Silicon Integrated Systems [SiS] Azalia Audio Controller [1039:7502]
00:1f.0 PCI bridge [0604]: Silicon Integrated Systems [SiS] PCI-to-PCI bridge [1039:0004]
01:00.0 VGA compatible controller [0300]: Silicon Integrated Systems [SiS] 771/671 PCIE VGA Display Adapter [1039:6351] (rev 10)
rabgye@ubuntumaya:~$ rabgye@ubuntumaya:~$ lspci -nn
-bash: rabgye@ubuntumaya:~$ : commande introuvable
rabgye@ubuntumaya:~$ 00:00.0 Host bridge [0600]: Silicon Integrated Systems [SiS] 671MX [1039:0671]
-bash: 00:00.0 : commande introuvable
rabgye@ubuntumaya:~$ 00:01.0 PCI bridge [0604]: Silicon Integrated Systems [SiS] SiS AGP Port (virtual PCI-to-PCI bridge) [1039:0003]
-bash: Erreur de syntaxe près du symbole inattendu « ( »
rabgye@ubuntumaya:~$ lshw
WARNING: you should run this program as super-user.
ubuntumaya                
    description: Computer
    width: 64 bits
    capabilities: vsyscall64 vsyscall32
  *-core
       description: Motherboard
       physical id: 0
     *-memory
          description: System memory
          physical id: 0
          size: 1791MiB
     *-cpu
          product: Intel(R) Pentium(R) Dual  CPU  E2160  @ 1.80GHz
          vendor: Intel Corp.
          physical id: 1
          bus info: cpu@0
          size: 1200MHz
          capacity: 1200MHz
          width: 64 bits
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx x86-64 constant_tsc arch_perfmon pebs bts rep_good pni dtes64 monitor ds_cpl est tm2 ssse3 cx16 xtpr pdcm lahf_lm cpufreq
     *-pci
          description: Host bridge
          product: 671MX
          vendor: Silicon Integrated Systems [SiS]
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 00
          width: 32 bits
          clock: 33MHz
          configuration: driver=agpgart-sis latency=64 module=sis_agp
        *-pci:0
             description: PCI bridge
             product: SiS AGP Port (virtual PCI-to-PCI bridge)
             vendor: Silicon Integrated Systems [SiS]
             physical id: 1
             bus info: pci@0000:00:01.0
             version: 00
est ce qu'il te faut les instructions de lshw en superuser?

---

### Post by pytheas22 on 2009-06-09
Merci des ces outputs.  Malheuresement je ne sais pas encore ce qui peut être le problème, donc je dois demander un peu plus d'information.  Merci de donner les outputs des commandes suivantes:
```

uname -rm
aplay -l
lspci -v
```
> 
est ce qu'il te faut les instructions de lshw en superuser? 

Non, c'est pas grave.

---

### Post by manjusri on 2009-06-12
tout d'abord qq precisions:le son marche sauf le generique de start-up et la capture;je suis un sentimental,le generique me manque bcp et la principale utilisation que je veux faire de mon ordi c'est de l'audio..les outputs que tu m'as demandes
rabgye@ubuntumaya:~$ lscpi --nn
-bash: lscpi : commande introuvable
rabgye@ubuntumaya:~$ lspci --nn
lspci: invalid option -- '-'
Usage: lspci [<switches>]

Basic display modes:
-mm        Produce machine-readable output (single -m for an obsolete format)
-t        Show bus tree

Display options:
-v        Be verbose (-vv for very verbose)
-k        Show kernel drivers handling each device
-x        Show hex-dump of the standard part of the config space
-xxx        Show hex-dump of the whole config space (dangerous; root only)
-xxxx        Show hex-dump of the 4096-byte extended config space (root only)
-b        Bus-centric view (addresses and IRQ's as seen by the bus)
-D        Always show domain numbers

Resolving of device ID's to names:
-n        Show numeric ID's
-nn        Show both textual and numeric ID's (names & numbers)
-q        Query the PCI ID database for unknown ID's via DNS
-qq        As above, but re-query locally cached entries
-Q        Query the PCI ID database for all ID's via DNS

Selection of devices:
-s [[[[<domain>]:]<bus>]:][<slot>][.[<func>]]    Show only devices in selected slots
-d [<vendor>]:[<device>]            Show only devices with specified ID's

Other options:
-i <file>    Use specified ID database instead of /usr/share/misc/pci.ids.gz
-p <file>    Look up kernel modules in a given file instead of default modules.pcimap
-M        Enable `bus mapping' mode (dangerous; root only)

PCI access options:
-A <method>    Use the specified PCI access method (see `-A help' for a list)
-O <par>=<val>    Set PCI access parameter (see `-O help' for a list)
-G        Enable PCI access debugging
-H <mode>    Use direct hardware access (<mode> = 1 or 2)
-F <file>    Read PCI configuration dump from a given file
rabgye@ubuntumaya:~$ uname -rm
2.6.28-3-rt x86_64
rabgye@ubuntumaya:~$ aplay -l
**** Liste des PLAYBACK périphériques ****
carte  0: SIS966 [HDA SIS966], périphérique 0 : ALC662 Analog [ALC662 Analog]
  Sous-périphériques: 1/1
  Sous-périphérique: #0: subdevice #0
carte  0: SIS966 [HDA SIS966], périphérique 1 : ALC662 Digital [ALC662 Digital]
  Sous-périphériques: 1/1
  Sous-périphérique: #0: subdevice #0
rabgye@ubuntumaya:~$ lspci -v
00:00.0 Host bridge: Silicon Integrated Systems [SiS] 671MX
    Subsystem: ASUSTeK Computer Inc. Device 82c9
    Flags: bus master, medium devsel, latency 64
    Memory at f0000000 (32-bit, non-prefetchable) [size=128M]
    Capabilities: <access denied>
    Kernel driver in use: agpgart-sis
    Kernel modules: sis-agp

00:01.0 PCI bridge: Silicon Integrated Systems [SiS] SiS AGP Port (virtual PCI-to-PCI bridge)
    Flags: bus master, 66MHz, fast devsel, latency 0
    Bus: primary=00, secondary=01, subordinate=01, sec-latency=0
    I/O behind bridge: 0000e000-0000efff
    Memory behind bridge: feb00000-febfffff
    Prefetchable memory behind bridge: d0000000-dfffffff
    Kernel modules: shpchp

00:02.0 ISA bridge: Silicon Integrated Systems [SiS] SiS968 [MuTIOL Media IO] (rev 01)
    Flags: bus master, medium devsel, latency 0

00:02.5 IDE interface: Silicon Integrated Systems [SiS] 5513 [IDE] (rev 01) (prog-if 80 [Master])
    Subsystem: ASUSTeK Computer Inc. Device 825e
    Flags: bus master, medium devsel, latency 128
    I/O ports at 01f0 [size=8]
    I/O ports at 03f4 [size=1]
    I/O ports at 0170 [size=8]
    I/O ports at 0374 [size=1]
    I/O ports at ffe0 [size=16]
    Capabilities: <access denied>
    Kernel driver in use: pata_sis

00:03.0 USB Controller: Silicon Integrated Systems [SiS] USB 1.1 Controller (rev 0f) (prog-if 10)
    Subsystem: ASUSTeK Computer Inc. Device 825e
    Flags: bus master, medium devsel, latency 64, IRQ 20
    Memory at feaff000 (32-bit, non-prefetchable) [size=4K]
    Kernel driver in use: ohci_hcd

00:03.1 USB Controller: Silicon Integrated Systems [SiS] USB 1.1 Controller (rev 0f) (prog-if 10)
    Subsystem: ASUSTeK Computer Inc. Device 825e
    Flags: bus master, medium devsel, latency 64, IRQ 21
    Memory at feafe000 (32-bit, non-prefetchable) [size=4K]
    Kernel driver in use: ohci_hcd

00:03.3 USB Controller: Silicon Integrated Systems [SiS] USB 2.0 Controller (prog-if 20)
    Subsystem: ASUSTeK Computer Inc. Device 825e
    Flags: bus master, medium devsel, latency 64, IRQ 22
    Memory at feafd000 (32-bit, non-prefetchable) [size=4K]
    Capabilities: <access denied>
    Kernel driver in use: ehci_hcd

00:04.0 Ethernet controller: Silicon Integrated Systems [SiS] 191 Gigabit Ethernet Adapter (rev 02)
    Subsystem: ASUSTeK Computer Inc. Device 825e
    Flags: bus master, medium devsel, latency 0, IRQ 19
    Memory at feafcc00 (32-bit, non-prefetchable) [size=128]
    I/O ports at dc00 [size=128]
    Capabilities: <access denied>
    Kernel driver in use: sis190
    Kernel modules: sis190

00:05.0 IDE interface: Silicon Integrated Systems [SiS] SATA Controller / IDE mode (rev 03) (prog-if 85 [Master SecO PriO])
    Subsystem: ASUSTeK Computer Inc. Device 825e
    Flags: bus master, medium devsel, latency 64, IRQ 17
    I/O ports at d800 [size=8]
    I/O ports at d400 [size=4]
    I/O ports at d000 [size=8]
    I/O ports at cc00 [size=4]
    I/O ports at c800 [size=16]
    I/O ports at c400 [size=128]
    Capabilities: <access denied>
    Kernel driver in use: sata_sis

00:06.0 PCI bridge: Silicon Integrated Systems [SiS] PCI-to-PCI bridge
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=02, subordinate=02, sec-latency=0
    Capabilities: <access denied>
    Kernel driver in use: pcieport-driver
    Kernel modules: shpchp

00:07.0 PCI bridge: Silicon Integrated Systems [SiS] PCI-to-PCI bridge
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=03, subordinate=03, sec-latency=0
    Capabilities: <access denied>
    Kernel driver in use: pcieport-driver
    Kernel modules: shpchp

00:0f.0 Audio device: Silicon Integrated Systems [SiS] Azalia Audio Controller
    Subsystem: ASUSTeK Computer Inc. Device 8290
    Flags: bus master, medium devsel, latency 0, IRQ 18
    Memory at feaf4000 (32-bit, non-prefetchable) [size=16K]
    Capabilities: <access denied>
    Kernel driver in use: HDA Intel
    Kernel modules: snd-hda-intel

00:1f.0 PCI bridge: Silicon Integrated Systems [SiS] PCI-to-PCI bridge
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=04, subordinate=04, sec-latency=0
    Capabilities: <access denied>
    Kernel driver in use: pcieport-driver
    Kernel modules: shpchp

01:00.0 VGA compatible controller: Silicon Integrated Systems [SiS] 771/671 PCIE VGA Display Adapter (rev 10)
    Subsystem: ASUSTeK Computer Inc. Device 82c9
    Flags: 66MHz, medium devsel
    BIST result: 00
    Memory at d0000000 (32-bit, prefetchable) [size=256M]
    Memory at febe0000 (32-bit, non-prefetchable) [size=128K]
    I/O ports at ec00 [size=128]
    Capabilities: <access denied>

rabgye@ubuntumaya:~$ 

# /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.

loop
lp
raw1394
rtc                                                                    c'est moi qui m'excuse d'avoir ete un peu long cette fois ci;qqfs ça me prend trop la tete aplus

---

### Post by pytheas22 on 2009-06-14
Bon, vu que le son marche sauf le génerique et la capture, je pense que ça vaut la peine de recompiler alsa.  Pour faire cela, entrez ces commandes:```


sudo apt-get -y install build-essential ncurses-dev gettext xmlto
sudo apt-get -y install linux-headers-`uname -r`
cd ~
wget ftp://ftp.alsa-project.org/pub/driver/alsa-driver-1.0.20.tar.bz2
wget ftp://ftp.alsa-project.org/pub/lib/alsa-lib-1.0.20.tar.bz2
wget ftp://ftp.alsa-project.org/pub/utils/alsa-utils-1.0.20.tar.bz2
sudo mkdir -p /usr/src/alsa
cd /usr/src/alsa
sudo cp ~/alsa* .
sudo tar xjf alsa-driver*
sudo tar xjf alsa-lib*
sudo tar xjf alsa-utils*
cd alsa-driver*
sudo ./configure --with-cards=hda-intel --with-kernel=/usr/src/linux-headers-$(uname -r)
sudo make
sudo make install
cd ../alsa-lib*
sudo ./configure
sudo make
sudo make install
cd ../alsa-utils*
sudo ./configure
sudo make
sudo make install
rm -f ~/alsa-driver*
rm -f ~/alsa-lib*
rm -f ~/alsa-utils*
```

Si vous recevez des erreurs, merci de montrer les outputs.  Sinon, redémarrez votre ordinateur et vous devrez avoir la version 1.0.20 de alsa.  Pour vérifier, entrez la commande 'cat /proc/asound/version'.

Avec la nouvelle version de alsa, est-ce que le son marche mieux?

Je pars demain en vacances (à Paris :)), donc je ne pourrai pas peut-être répondre très vite.  Mais je ferai le mieux possible.

---

### Post by manjusri on 2009-06-25
tout semble avoir marche avec quelques modifications sauf les trois dernieres lignes.voici les outputs:

































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































make[1]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/amixer »
if gcc -DHAVE_CONFIG_H -I. -I. -I../include -I../include    -g -O2 -MT amixer.o -MD -MP -MF ".deps/amixer.Tpo" -c -o amixer.o amixer.c; \
    then mv -f ".deps/amixer.Tpo" ".deps/amixer.Po"; else rm -f ".deps/amixer.Tpo"; exit 1; fi
amixer.c: In function ‘get_integer’:
amixer.c:244: attention : ignoring return value of ‘strtol’, declared with attribute warn_unused_result
amixer.c: In function ‘get_integer64’:
amixer.c:272: attention : ignoring return value of ‘strtol’, declared with attribute warn_unused_result
amixer.c: In function ‘set_volume_simple’:
amixer.c:358: attention : ignoring return value of ‘strtol’, declared with attribute warn_unused_result
gcc  -g -O2   -o amixer  amixer.o -lm -lasound -lm -ldl -lpthread
make[1]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/amixer »
Making all in amidi
make[1]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/amidi »
if gcc -DHAVE_CONFIG_H -I. -I. -I../include -I../include    -g -O2 -MT amidi.o -MD -MP -MF ".deps/amidi.Tpo" -c -o amidi.o amidi.c; \
    then mv -f ".deps/amidi.Tpo" ".deps/amidi.Po"; else rm -f ".deps/amidi.Tpo"; exit 1; fi
amidi.c: In function ‘main’:
amidi.c:658: attention : ignoring return value of ‘write’, declared with attribute warn_unused_result
gcc  -g -O2   -o amidi  amidi.o  -lasound -lm -ldl -lpthread
make[1]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/amidi »
Making all in alsaconf
make[1]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/alsaconf »
Making all in po
make[2]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/alsaconf/po »
35 messages traduits, 1 message non traduit.
34 messages traduits, 1 traduction approximative, 1 message non traduit.
make[2]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/alsaconf/po »
make[2]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/alsaconf »
make[2]: Rien à faire pour « all-am ».
make[2]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/alsaconf »
make[1]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/alsaconf »
Making all in aplay
make[1]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/aplay »
if gcc -DHAVE_CONFIG_H -I. -I. -I../include -I../include    -g -O2 -MT aplay.o -MD -MP -MF ".deps/aplay.Tpo" -c -o aplay.o aplay.c; \
    then mv -f ".deps/aplay.Tpo" ".deps/aplay.Po"; else rm -f ".deps/aplay.Tpo"; exit 1; fi
aplay.c: In function ‘end_voc’:
aplay.c:2158: attention : ignoring return value of ‘write’, declared with attribute warn_unused_result
aplay.c: In function ‘end_wave’:
aplay.c:2178: attention : ignoring return value of ‘write’, declared with attribute warn_unused_result
aplay.c:2180: attention : ignoring return value of ‘write’, declared with attribute warn_unused_result
aplay.c: In function ‘end_au’:
aplay.c:2193: attention : ignoring return value of ‘write’, declared with attribute warn_unused_result
gcc  -g -O2   -o aplay  aplay.o  -lrt -lasound -lm -ldl -lpthread
make[1]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/aplay »
Making all in iecset
make[1]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/iecset »
if gcc -DHAVE_CONFIG_H -I. -I. -I../include -I../include    -g -O2 -MT iecset.o -MD -MP -MF ".deps/iecset.Tpo" -c -o iecset.o iecset.c; \
    then mv -f ".deps/iecset.Tpo" ".deps/iecset.Po"; else rm -f ".deps/iecset.Tpo"; exit 1; fi
if gcc -DHAVE_CONFIG_H -I. -I. -I../include -I../include    -g -O2 -MT iecbits.o -MD -MP -MF ".deps/iecbits.Tpo" -c -o iecbits.o iecbits.c; \
    then mv -f ".deps/iecbits.Tpo" ".deps/iecbits.Po"; else rm -f ".deps/iecbits.Tpo"; exit 1; fi
gcc  -g -O2   -o iecset  iecset.o iecbits.o -lm -lasound -lm -ldl -lpthread
make[1]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/iecset »
Making all in speaker-test
make[1]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/speaker-test »
Making all in samples
make[2]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/speaker-test/samples »
make[2]: Rien à faire pour « all ».
make[2]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/speaker-test/samples »
make[2]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/speaker-test »
if gcc -DHAVE_CONFIG_H -I. -I. -I../include -I../include    -g -O2 -MT speaker-test.o -MD -MP -MF ".deps/speaker-test.Tpo" -c -o speaker-test.o speaker-test.c; \
    then mv -f ".deps/speaker-test.Tpo" ".deps/speaker-test.Po"; else rm -f ".deps/speaker-test.Tpo"; exit 1; fi
if gcc -DHAVE_CONFIG_H -I. -I. -I../include -I../include    -g -O2 -MT pink.o -MD -MP -MF ".deps/pink.Tpo" -c -o pink.o pink.c; \
    then mv -f ".deps/pink.Tpo" ".deps/pink.Po"; else rm -f ".deps/pink.Tpo"; exit 1; fi
gcc  -g -O2   -o speaker-test  speaker-test.o pink.o  -lm -lasound -lm -ldl -lpthread
make[2]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/speaker-test »
make[1]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/speaker-test »
Making all in seq
make[1]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/seq »
Making all in aconnect
make[2]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/seq/aconnect »
if gcc -DHAVE_CONFIG_H -I. -I. -I../../include -I../../include    -g -O2 -MT aconnect.o -MD -MP -MF ".deps/aconnect.Tpo" -c -o aconnect.o aconnect.c; \
    then mv -f ".deps/aconnect.Tpo" ".deps/aconnect.Po"; else rm -f ".deps/aconnect.Tpo"; exit 1; fi
gcc  -g -O2   -o aconnect  aconnect.o  -lasound -lm -ldl -lpthread
make[2]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/seq/aconnect »
Making all in aplaymidi
make[2]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/seq/aplaymidi »
if gcc -DHAVE_CONFIG_H -I. -I. -I../../include -I../../include    -g -O2 -MT aplaymidi.o -MD -MP -MF ".deps/aplaymidi.Tpo" -c -o aplaymidi.o aplaymidi.c; \
    then mv -f ".deps/aplaymidi.Tpo" ".deps/aplaymidi.Po"; else rm -f ".deps/aplaymidi.Tpo"; exit 1; fi
gcc  -g -O2   -o aplaymidi  aplaymidi.o  -lasound -lm -ldl -lpthread
if gcc -DHAVE_CONFIG_H -I. -I. -I../../include -I../../include    -g -O2 -MT arecordmidi.o -MD -MP -MF ".deps/arecordmidi.Tpo" -c -o arecordmidi.o arecordmidi.c; \
    then mv -f ".deps/arecordmidi.Tpo" ".deps/arecordmidi.Po"; else rm -f ".deps/arecordmidi.Tpo"; exit 1; fi
gcc  -g -O2   -o arecordmidi  arecordmidi.o  -lasound -lm -ldl -lpthread
make[2]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/seq/aplaymidi »
Making all in aseqdump
make[2]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/seq/aseqdump »
if gcc -DHAVE_CONFIG_H -I. -I. -I../../include -I../../include    -g -O2 -MT aseqdump.o -MD -MP -MF ".deps/aseqdump.Tpo" -c -o aseqdump.o aseqdump.c; \
    then mv -f ".deps/aseqdump.Tpo" ".deps/aseqdump.Po"; else rm -f ".deps/aseqdump.Tpo"; exit 1; fi
gcc  -g -O2   -o aseqdump  aseqdump.o  -lasound -lm -ldl -lpthread
make[2]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/seq/aseqdump »
Making all in aseqnet
make[2]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/seq/aseqnet »
if gcc -DHAVE_CONFIG_H -I. -I. -I../../include -I../../include    -g -O2 -MT aseqnet.o -MD -MP -MF ".deps/aseqnet.Tpo" -c -o aseqnet.o aseqnet.c; \
    then mv -f ".deps/aseqnet.Tpo" ".deps/aseqnet.Po"; else rm -f ".deps/aseqnet.Tpo"; exit 1; fi
aseqnet.c: In function ‘flush_writebuf’:
aseqnet.c:495: attention : ignoring return value of ‘write’, declared with attribute warn_unused_result
gcc  -g -O2   -o aseqnet  aseqnet.o  -lasound -lm -ldl -lpthread
make[2]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/seq/aseqnet »
make[2]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/seq »
make[2]: Rien à faire pour « all-am ».
make[2]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/seq »
make[1]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/seq »
make[1]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20 »
make[1]: Rien à faire pour « all-am ».
make[1]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20 »
rabgye@ubuntumaya:~/alsa-utils-1.0.20$ sudo make
Making all in include
make[1]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/include »
make  all-am
make[2]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/include »
make[2]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/include »
make[1]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/include »
Making all in alsactl
make[1]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/alsactl »
Making all in init
make[2]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/alsactl/init »
make[2]: Rien à faire pour « all ».
make[2]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/alsactl/init »
make[2]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/alsactl »
make[2]: Rien à faire pour « all-am ».
make[2]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/alsactl »
make[1]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/alsactl »
Making all in utils
make[1]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/utils »
make[1]: Rien à faire pour « all ».
make[1]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/utils »
Making all in m4
make[1]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/m4 »
make[1]: Rien à faire pour « all ».
make[1]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/m4 »
Making all in po
make[1]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/po »
make[1]: Rien à faire pour « all ».
make[1]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/po »
Making all in alsamixer
make[1]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/alsamixer »
make[1]: Rien à faire pour « all ».
make[1]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/alsamixer »
Making all in amixer
make[1]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/amixer »
make[1]: Rien à faire pour « all ».
make[1]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/amixer »
Making all in amidi
make[1]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/amidi »
make[1]: Rien à faire pour « all ».
make[1]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/amidi »
Making all in alsaconf
make[1]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/alsaconf »
Making all in po
make[2]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/alsaconf/po »
make[2]: Rien à faire pour « all ».
make[2]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/alsaconf/po »
make[2]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/alsaconf »
make[2]: Rien à faire pour « all-am ».
make[2]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/alsaconf »
make[1]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/alsaconf »
Making all in aplay
make[1]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/aplay »
make[1]: Rien à faire pour « all ».
make[1]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/aplay »
Making all in iecset
make[1]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/iecset »
make[1]: Rien à faire pour « all ».
make[1]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/iecset »
Making all in speaker-test
make[1]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/speaker-test »
Making all in samples
make[2]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/speaker-test/samples »
make[2]: Rien à faire pour « all ».
make[2]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/speaker-test/samples »
make[2]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/speaker-test »
make[2]: Rien à faire pour « all-am ».
make[2]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/speaker-test »
make[1]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/speaker-test »
Making all in seq
make[1]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/seq »
Making all in aconnect
make[2]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/seq/aconnect »
make[2]: Rien à faire pour « all ».
make[2]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/seq/aconnect »
Making all in aplaymidi
make[2]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/seq/aplaymidi »
make[2]: Rien à faire pour « all ».
make[2]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/seq/aplaymidi »
Making all in aseqdump
make[2]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/seq/aseqdump »
make[2]: Rien à faire pour « all ».
make[2]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/seq/aseqdump »
Making all in aseqnet
make[2]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/seq/aseqnet »
make[2]: Rien à faire pour « all ».
make[2]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/seq/aseqnet »
make[2]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/seq »
make[2]: Rien à faire pour « all-am ».
make[2]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/seq »
make[1]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/seq »
make[1]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20 »
make[1]: Rien à faire pour « all-am ».
make[1]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20 »
rabgye@ubuntumaya:~/alsa-utils-1.0.20$ sudo make install
Making install in include
make[1]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/include »
make[2]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/include »
make[2]: Rien à faire pour « install-exec-am ».
make[2]: Rien à faire pour « install-data-am ».
make[2]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/include »
make[1]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/include »
Making install in alsactl
make[1]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/alsactl »
Making install in init
make[2]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/alsactl/init »
make[3]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/alsactl/init »
make[3]: Rien à faire pour « install-exec-am ».
test -z "/usr/share/alsa/init" || mkdir -p -- "/usr/share/alsa/init"
 /usr/bin/install -c -m 644 '00main' '/usr/share/alsa/init/00main'
 /usr/bin/install -c -m 644 'default' '/usr/share/alsa/init/default'
 /usr/bin/install -c -m 644 'help' '/usr/share/alsa/init/help'
 /usr/bin/install -c -m 644 'info' '/usr/share/alsa/init/info'
 /usr/bin/install -c -m 644 'test' '/usr/share/alsa/init/test'
 /usr/bin/install -c -m 644 'hda' '/usr/share/alsa/init/hda'
make[3]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/alsactl/init »
make[2]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/alsactl/init »
make[2]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/alsactl »
make[3]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/alsactl »
test -z "/usr/sbin" || mkdir -p -- "/usr/sbin"
  /usr/bin/install -c 'alsactl' '/usr/sbin/alsactl'
test -z "/usr/share/man/man1" || mkdir -p -- "/usr/share/man/man1"
 /usr/bin/install -c -m 644 './alsactl.1' '/usr/share/man/man1/alsactl.1'
test -z "/usr/share/man/man7" || mkdir -p -- "/usr/share/man/man7"
 /usr/bin/install -c -m 644 './alsactl_init.7' '/usr/share/man/man7/alsactl_init.7'
make[3]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/alsactl »
make[2]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/alsactl »
make[1]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/alsactl »
Making install in utils
make[1]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/utils »
make[2]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/utils »
make[2]: Rien à faire pour « install-exec-am ».
make[2]: Rien à faire pour « install-data-am ».
make[2]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/utils »
make[1]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/utils »
Making install in m4
make[1]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/m4 »
make[2]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/m4 »
make[2]: Rien à faire pour « install-exec-am ».
make[2]: Rien à faire pour « install-data-am ».
make[2]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/m4 »
make[1]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/m4 »
Making install in po
make[1]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/po »
mkdir -p -- /usr/share
installing ja.gmo as /usr/share/locale/ja/LC_MESSAGES/alsa-utils.mo
if test "alsa-utils" = "gettext-tools"; then \
      mkdir -p -- /usr/share/gettext/po; \
      for file in Makefile.in.in remove-potcdate.sin quot.sed boldquot.sed [email]en@quot.header[/email] [email]en@boldquot.header[/email] insert-header.sin Rules-quot   Makevars.template; do \
        /usr/bin/install -c -m 644 ./$file \
                /usr/share/gettext/po/$file; \
      done; \
      for file in Makevars; do \
        rm -f /usr/share/gettext/po/$file; \
      done; \
    else \
      : ; \
    fi
make[1]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/po »
Making install in alsamixer
make[1]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/alsamixer »
make[2]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/alsamixer »
test -z "/usr/bin" || mkdir -p -- "/usr/bin"
  /usr/bin/install -c 'alsamixer' '/usr/bin/alsamixer'
test -z "/usr/share/man/man1" || mkdir -p -- "/usr/share/man/man1"
 /usr/bin/install -c -m 644 './alsamixer.1' '/usr/share/man/man1/alsamixer.1'
make[2]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/alsamixer »
make[1]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/alsamixer »
Making install in amixer
make[1]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/amixer »
make[2]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/amixer »
test -z "/usr/bin" || mkdir -p -- "/usr/bin"
  /usr/bin/install -c 'amixer' '/usr/bin/amixer'
test -z "/usr/share/man/man1" || mkdir -p -- "/usr/share/man/man1"
 /usr/bin/install -c -m 644 './amixer.1' '/usr/share/man/man1/amixer.1'
make[2]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/amixer »
make[1]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/amixer »
Making install in amidi
make[1]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/amidi »
make[2]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/amidi »
test -z "/usr/bin" || mkdir -p -- "/usr/bin"
  /usr/bin/install -c 'amidi' '/usr/bin/amidi'
test -z "/usr/share/man/man1" || mkdir -p -- "/usr/share/man/man1"
 /usr/bin/install -c -m 644 './amidi.1' '/usr/share/man/man1/amidi.1'
make[2]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/amidi »
make[1]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/amidi »
Making install in alsaconf
make[1]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/alsaconf »
Making install in po
make[2]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/alsaconf/po »
mkdir -p -- /usr/share
make[2]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/alsaconf/po »
make[2]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/alsaconf »
make[3]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/alsaconf »
test -z "/usr/sbin" || mkdir -p -- "/usr/sbin"
 /usr/bin/install -c 'alsaconf' '/usr/sbin/alsaconf'
 /usr/bin/install -c -m 644 alsaconf.8 /usr/share/man/man8/alsaconf.8
 /usr/bin/install -c -m 644 alsaconf.fr.8 /usr/share/man/fr/man8/alsaconf.8
make[3]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/alsaconf »
make[2]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/alsaconf »
make[1]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/alsaconf »
Making install in aplay
make[1]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/aplay »
make[2]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/aplay »
test -z "/usr/bin" || mkdir -p -- "/usr/bin"
  /usr/bin/install -c 'aplay' '/usr/bin/aplay'
make  install-exec-hook
make[3]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/aplay »
rm -f arecord
ln -s aplay arecord
rm -f /usr/bin/arecord
(cd /usr/bin && ln -s aplay arecord)
make[3]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/aplay »
test -z "/usr/share/man/man1" || mkdir -p -- "/usr/share/man/man1"
 /usr/bin/install -c -m 644 './aplay.1' '/usr/share/man/man1/aplay.1'
 /usr/bin/install -c -m 644 './arecord.1' '/usr/share/man/man1/arecord.1'
make  install-data-hook
make[3]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/aplay »
rm -f /usr/share/man/man1/arecord.1
(cd /usr/share/man/man1 && ln -s aplay.1 arecord.1)
make[3]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/aplay »
make[2]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/aplay »
make[1]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/aplay »
Making install in iecset
make[1]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/iecset »
make[2]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/iecset »
test -z "/usr/bin" || mkdir -p -- "/usr/bin"
  /usr/bin/install -c 'iecset' '/usr/bin/iecset'
test -z "/usr/share/man/man1" || mkdir -p -- "/usr/share/man/man1"
 /usr/bin/install -c -m 644 './iecset.1' '/usr/share/man/man1/iecset.1'
make[2]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/iecset »
make[1]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/iecset »
Making install in speaker-test
make[1]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/speaker-test »
Making install in samples
make[2]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/speaker-test/samples »
make[3]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/speaker-test/samples »
make[3]: Rien à faire pour « install-exec-am ».
test -z "/usr/share/alsa/speaker-test" || mkdir -p -- "/usr/share/alsa/speaker-test"
 /usr/bin/install -c -m 644 'sample_map.csv' '/usr/share/alsa/speaker-test/sample_map.csv'
test -z "/usr/share/sounds/alsa" || mkdir -p -- "/usr/share/sounds/alsa"
 /usr/bin/install -c -m 644 'Front_Left.wav' '/usr/share/sounds/alsa/Front_Left.wav'
 /usr/bin/install -c -m 644 'Rear_Center.wav' '/usr/share/sounds/alsa/Rear_Center.wav'
 /usr/bin/install -c -m 644 'Rear_Right.wav' '/usr/share/sounds/alsa/Rear_Right.wav'
 /usr/bin/install -c -m 644 'Side_Right.wav' '/usr/share/sounds/alsa/Side_Right.wav'
 /usr/bin/install -c -m 644 'Front_Center.wav' '/usr/share/sounds/alsa/Front_Center.wav'
 /usr/bin/install -c -m 644 'Front_Right.wav' '/usr/share/sounds/alsa/Front_Right.wav'
 /usr/bin/install -c -m 644 'Noise.wav' '/usr/share/sounds/alsa/Noise.wav'
 /usr/bin/install -c -m 644 'Rear_Left.wav' '/usr/share/sounds/alsa/Rear_Left.wav'
 /usr/bin/install -c -m 644 'Side_Left.wav' '/usr/share/sounds/alsa/Side_Left.wav'
make[3]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/speaker-test/samples »
make[2]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/speaker-test/samples »
make[2]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/speaker-test »
make[3]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/speaker-test »
test -z "/usr/bin" || mkdir -p -- "/usr/bin"
  /usr/bin/install -c 'speaker-test' '/usr/bin/speaker-test'
test -z "/usr/share/man/man1" || mkdir -p -- "/usr/share/man/man1"
 /usr/bin/install -c -m 644 './speaker-test.1' '/usr/share/man/man1/speaker-test.1'
make[3]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/speaker-test »
make[2]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/speaker-test »
make[1]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/speaker-test »
Making install in seq
make[1]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/seq »
Making install in aconnect
make[2]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/seq/aconnect »
make[3]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/seq/aconnect »
test -z "/usr/bin" || mkdir -p -- "/usr/bin"
  /usr/bin/install -c 'aconnect' '/usr/bin/aconnect'
test -z "/usr/share/man/man1" || mkdir -p -- "/usr/share/man/man1"
 /usr/bin/install -c -m 644 './aconnect.1' '/usr/share/man/man1/aconnect.1'
make[3]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/seq/aconnect »
make[2]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/seq/aconnect »
Making install in aplaymidi
make[2]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/seq/aplaymidi »
make[3]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/seq/aplaymidi »
test -z "/usr/bin" || mkdir -p -- "/usr/bin"
  /usr/bin/install -c 'aplaymidi' '/usr/bin/aplaymidi'
  /usr/bin/install -c 'arecordmidi' '/usr/bin/arecordmidi'
test -z "/usr/share/man/man1" || mkdir -p -- "/usr/share/man/man1"
 /usr/bin/install -c -m 644 './aplaymidi.1' '/usr/share/man/man1/aplaymidi.1'
 /usr/bin/install -c -m 644 './arecordmidi.1' '/usr/share/man/man1/arecordmidi.1'
make[3]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/seq/aplaymidi »
make[2]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/seq/aplaymidi »
Making install in aseqdump
make[2]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/seq/aseqdump »
make[3]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/seq/aseqdump »
test -z "/usr/bin" || mkdir -p -- "/usr/bin"
  /usr/bin/install -c 'aseqdump' '/usr/bin/aseqdump'
test -z "/usr/share/man/man1" || mkdir -p -- "/usr/share/man/man1"
 /usr/bin/install -c -m 644 './aseqdump.1' '/usr/share/man/man1/aseqdump.1'
make[3]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/seq/aseqdump »
make[2]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/seq/aseqdump »
Making install in aseqnet
make[2]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/seq/aseqnet »
make[3]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/seq/aseqnet »
test -z "/usr/bin" || mkdir -p -- "/usr/bin"
  /usr/bin/install -c 'aseqnet' '/usr/bin/aseqnet'
test -z "/usr/share/man/man1" || mkdir -p -- "/usr/share/man/man1"
 /usr/bin/install -c -m 644 './aseqnet.1' '/usr/share/man/man1/aseqnet.1'
make[3]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/seq/aseqnet »
make[2]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/seq/aseqnet »
make[2]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/seq »
make[3]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/seq »
make[3]: Rien à faire pour « install-exec-am ».
make[3]: Rien à faire pour « install-data-am ».
make[3]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/seq »
make[2]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/seq »
make[1]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/seq »
make[1]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20 »
make[2]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20 »
make[2]: Rien à faire pour « install-exec-am ».
make[2]: Rien à faire pour « install-data-am ».
make[2]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20 »
make[1]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20 »
rabgye@ubuntumaya:~/alsa-utils-1.0.20$ rm -f ~/alsa-driver*
rm: ne peut enlever `/home/rabgye/alsa-driver-1.0.20': est un dossier
rabgye@ubuntumaya:~/alsa-utils-1.0.20$ rm -f ~/alsa-lib*
rm: ne peut enlever `/home/rabgye/alsa-lib-1.0.20': est un dossier
rabgye@ubuntumaya:~/alsa-utils-1.0.20$ rm -f ~/alsa-utils*
rm: ne peut enlever `/home/rabgye/alsa-utils-1.0.20': est un dossier
rabgye@ubuntumaya:~/alsa-utils-1.0.20$ 

je n'ai pas teste ne sachant pas quoi faire pour les trois dernieres lignes.merci.j'espere que les vacances ont ete bonnes































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































make[1]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/amixer »
if gcc -DHAVE_CONFIG_H -I. -I. -I../include -I../include    -g -O2 -MT amixer.o -MD -MP -MF ".deps/amixer.Tpo" -c -o amixer.o amixer.c; \
    then mv -f ".deps/amixer.Tpo" ".deps/amixer.Po"; else rm -f ".deps/amixer.Tpo"; exit 1; fi
amixer.c: In function ‘get_integer’:
amixer.c:244: attention : ignoring return value of ‘strtol’, declared with attribute warn_unused_result
amixer.c: In function ‘get_integer64’:
amixer.c:272: attention : ignoring return value of ‘strtol’, declared with attribute warn_unused_result
amixer.c: In function ‘set_volume_simple’:
amixer.c:358: attention : ignoring return value of ‘strtol’, declared with attribute warn_unused_result
gcc  -g -O2   -o amixer  amixer.o -lm -lasound -lm -ldl -lpthread
make[1]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/amixer »
Making all in amidi
make[1]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/amidi »
if gcc -DHAVE_CONFIG_H -I. -I. -I../include -I../include    -g -O2 -MT amidi.o -MD -MP -MF ".deps/amidi.Tpo" -c -o amidi.o amidi.c; \
    then mv -f ".deps/amidi.Tpo" ".deps/amidi.Po"; else rm -f ".deps/amidi.Tpo"; exit 1; fi
amidi.c: In function ‘main’:
amidi.c:658: attention : ignoring return value of ‘write’, declared with attribute warn_unused_result
gcc  -g -O2   -o amidi  amidi.o  -lasound -lm -ldl -lpthread
make[1]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/amidi »
Making all in alsaconf
make[1]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/alsaconf »
Making all in po
make[2]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/alsaconf/po »
35 messages traduits, 1 message non traduit.
34 messages traduits, 1 traduction approximative, 1 message non traduit.
make[2]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/alsaconf/po »
make[2]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/alsaconf »
make[2]: Rien à faire pour « all-am ».
make[2]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/alsaconf »
make[1]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/alsaconf »
Making all in aplay
make[1]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/aplay »
if gcc -DHAVE_CONFIG_H -I. -I. -I../include -I../include    -g -O2 -MT aplay.o -MD -MP -MF ".deps/aplay.Tpo" -c -o aplay.o aplay.c; \
    then mv -f ".deps/aplay.Tpo" ".deps/aplay.Po"; else rm -f ".deps/aplay.Tpo"; exit 1; fi
aplay.c: In function ‘end_voc’:
aplay.c:2158: attention : ignoring return value of ‘write’, declared with attribute warn_unused_result
aplay.c: In function ‘end_wave’:
aplay.c:2178: attention : ignoring return value of ‘write’, declared with attribute warn_unused_result
aplay.c:2180: attention : ignoring return value of ‘write’, declared with attribute warn_unused_result
aplay.c: In function ‘end_au’:
aplay.c:2193: attention : ignoring return value of ‘write’, declared with attribute warn_unused_result
gcc  -g -O2   -o aplay  aplay.o  -lrt -lasound -lm -ldl -lpthread
make[1]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/aplay »
Making all in iecset
make[1]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/iecset »
if gcc -DHAVE_CONFIG_H -I. -I. -I../include -I../include    -g -O2 -MT iecset.o -MD -MP -MF ".deps/iecset.Tpo" -c -o iecset.o iecset.c; \
    then mv -f ".deps/iecset.Tpo" ".deps/iecset.Po"; else rm -f ".deps/iecset.Tpo"; exit 1; fi
if gcc -DHAVE_CONFIG_H -I. -I. -I../include -I../include    -g -O2 -MT iecbits.o -MD -MP -MF ".deps/iecbits.Tpo" -c -o iecbits.o iecbits.c; \
    then mv -f ".deps/iecbits.Tpo" ".deps/iecbits.Po"; else rm -f ".deps/iecbits.Tpo"; exit 1; fi
gcc  -g -O2   -o iecset  iecset.o iecbits.o -lm -lasound -lm -ldl -lpthread
make[1]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/iecset »
Making all in speaker-test
make[1]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/speaker-test »
Making all in samples
make[2]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/speaker-test/samples »
make[2]: Rien à faire pour « all ».
make[2]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/speaker-test/samples »
make[2]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/speaker-test »
if gcc -DHAVE_CONFIG_H -I. -I. -I../include -I../include    -g -O2 -MT speaker-test.o -MD -MP -MF ".deps/speaker-test.Tpo" -c -o speaker-test.o speaker-test.c; \
    then mv -f ".deps/speaker-test.Tpo" ".deps/speaker-test.Po"; else rm -f ".deps/speaker-test.Tpo"; exit 1; fi
if gcc -DHAVE_CONFIG_H -I. -I. -I../include -I../include    -g -O2 -MT pink.o -MD -MP -MF ".deps/pink.Tpo" -c -o pink.o pink.c; \
    then mv -f ".deps/pink.Tpo" ".deps/pink.Po"; else rm -f ".deps/pink.Tpo"; exit 1; fi
gcc  -g -O2   -o speaker-test  speaker-test.o pink.o  -lm -lasound -lm -ldl -lpthread
make[2]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/speaker-test »
make[1]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/speaker-test »
Making all in seq
make[1]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/seq »
Making all in aconnect
make[2]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/seq/aconnect »
if gcc -DHAVE_CONFIG_H -I. -I. -I../../include -I../../include    -g -O2 -MT aconnect.o -MD -MP -MF ".deps/aconnect.Tpo" -c -o aconnect.o aconnect.c; \
    then mv -f ".deps/aconnect.Tpo" ".deps/aconnect.Po"; else rm -f ".deps/aconnect.Tpo"; exit 1; fi
gcc  -g -O2   -o aconnect  aconnect.o  -lasound -lm -ldl -lpthread
make[2]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/seq/aconnect »
Making all in aplaymidi
make[2]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/seq/aplaymidi »
if gcc -DHAVE_CONFIG_H -I. -I. -I../../include -I../../include    -g -O2 -MT aplaymidi.o -MD -MP -MF ".deps/aplaymidi.Tpo" -c -o aplaymidi.o aplaymidi.c; \
    then mv -f ".deps/aplaymidi.Tpo" ".deps/aplaymidi.Po"; else rm -f ".deps/aplaymidi.Tpo"; exit 1; fi
gcc  -g -O2   -o aplaymidi  aplaymidi.o  -lasound -lm -ldl -lpthread
if gcc -DHAVE_CONFIG_H -I. -I. -I../../include -I../../include    -g -O2 -MT arecordmidi.o -MD -MP -MF ".deps/arecordmidi.Tpo" -c -o arecordmidi.o arecordmidi.c; \
    then mv -f ".deps/arecordmidi.Tpo" ".deps/arecordmidi.Po"; else rm -f ".deps/arecordmidi.Tpo"; exit 1; fi
gcc  -g -O2   -o arecordmidi  arecordmidi.o  -lasound -lm -ldl -lpthread
make[2]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/seq/aplaymidi »
Making all in aseqdump
make[2]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/seq/aseqdump »
if gcc -DHAVE_CONFIG_H -I. -I. -I../../include -I../../include    -g -O2 -MT aseqdump.o -MD -MP -MF ".deps/aseqdump.Tpo" -c -o aseqdump.o aseqdump.c; \
    then mv -f ".deps/aseqdump.Tpo" ".deps/aseqdump.Po"; else rm -f ".deps/aseqdump.Tpo"; exit 1; fi
gcc  -g -O2   -o aseqdump  aseqdump.o  -lasound -lm -ldl -lpthread
make[2]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/seq/aseqdump »
Making all in aseqnet
make[2]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/seq/aseqnet »
if gcc -DHAVE_CONFIG_H -I. -I. -I../../include -I../../include    -g -O2 -MT aseqnet.o -MD -MP -MF ".deps/aseqnet.Tpo" -c -o aseqnet.o aseqnet.c; \
    then mv -f ".deps/aseqnet.Tpo" ".deps/aseqnet.Po"; else rm -f ".deps/aseqnet.Tpo"; exit 1; fi
aseqnet.c: In function ‘flush_writebuf’:
aseqnet.c:495: attention : ignoring return value of ‘write’, declared with attribute warn_unused_result
gcc  -g -O2   -o aseqnet  aseqnet.o  -lasound -lm -ldl -lpthread
make[2]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/seq/aseqnet »
make[2]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/seq »
make[2]: Rien à faire pour « all-am ».
make[2]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/seq »
make[1]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/seq »
make[1]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20 »
make[1]: Rien à faire pour « all-am ».
make[1]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20 »
rabgye@ubuntumaya:~/alsa-utils-1.0.20$ sudo make
Making all in include
make[1]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/include »
make  all-am
make[2]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/include »
make[2]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/include »
make[1]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/include »
Making all in alsactl
make[1]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/alsactl »
Making all in init
make[2]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/alsactl/init »
make[2]: Rien à faire pour « all ».
make[2]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/alsactl/init »
make[2]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/alsactl »
make[2]: Rien à faire pour « all-am ».
make[2]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/alsactl »
make[1]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/alsactl »
Making all in utils
make[1]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/utils »
make[1]: Rien à faire pour « all ».
make[1]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/utils »
Making all in m4
make[1]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/m4 »
make[1]: Rien à faire pour « all ».
make[1]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/m4 »
Making all in po
make[1]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/po »
make[1]: Rien à faire pour « all ».
make[1]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/po »
Making all in alsamixer
make[1]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/alsamixer »
make[1]: Rien à faire pour « all ».
make[1]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/alsamixer »
Making all in amixer
make[1]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/amixer »
make[1]: Rien à faire pour « all ».
make[1]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/amixer »
Making all in amidi
make[1]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/amidi »
make[1]: Rien à faire pour « all ».
make[1]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/amidi »
Making all in alsaconf
make[1]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/alsaconf »
Making all in po
make[2]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/alsaconf/po »
make[2]: Rien à faire pour « all ».
make[2]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/alsaconf/po »
make[2]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/alsaconf »
make[2]: Rien à faire pour « all-am ».
make[2]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/alsaconf »
make[1]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/alsaconf »
Making all in aplay
make[1]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/aplay »
make[1]: Rien à faire pour « all ».
make[1]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/aplay »
Making all in iecset
make[1]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/iecset »
make[1]: Rien à faire pour « all ».
make[1]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/iecset »
Making all in speaker-test
make[1]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/speaker-test »
Making all in samples
make[2]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/speaker-test/samples »
make[2]: Rien à faire pour « all ».
make[2]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/speaker-test/samples »
make[2]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/speaker-test »
make[2]: Rien à faire pour « all-am ».
make[2]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/speaker-test »
make[1]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/speaker-test »
Making all in seq
make[1]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/seq »
Making all in aconnect
make[2]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/seq/aconnect »
make[2]: Rien à faire pour « all ».
make[2]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/seq/aconnect »
Making all in aplaymidi
make[2]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/seq/aplaymidi »
make[2]: Rien à faire pour « all ».
make[2]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/seq/aplaymidi »
Making all in aseqdump
make[2]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/seq/aseqdump »
make[2]: Rien à faire pour « all ».
make[2]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/seq/aseqdump »
Making all in aseqnet
make[2]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/seq/aseqnet »
make[2]: Rien à faire pour « all ».
make[2]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/seq/aseqnet »
make[2]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/seq »
make[2]: Rien à faire pour « all-am ».
make[2]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/seq »
make[1]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/seq »
make[1]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20 »
make[1]: Rien à faire pour « all-am ».
make[1]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20 »
rabgye@ubuntumaya:~/alsa-utils-1.0.20$ sudo make install
Making install in include
make[1]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/include »
make[2]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/include »
make[2]: Rien à faire pour « install-exec-am ».
make[2]: Rien à faire pour « install-data-am ».
make[2]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/include »
make[1]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/include »
Making install in alsactl
make[1]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/alsactl »
Making install in init
make[2]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/alsactl/init »
make[3]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/alsactl/init »
make[3]: Rien à faire pour « install-exec-am ».
test -z "/usr/share/alsa/init" || mkdir -p -- "/usr/share/alsa/init"
 /usr/bin/install -c -m 644 '00main' '/usr/share/alsa/init/00main'
 /usr/bin/install -c -m 644 'default' '/usr/share/alsa/init/default'
 /usr/bin/install -c -m 644 'help' '/usr/share/alsa/init/help'
 /usr/bin/install -c -m 644 'info' '/usr/share/alsa/init/info'
 /usr/bin/install -c -m 644 'test' '/usr/share/alsa/init/test'
 /usr/bin/install -c -m 644 'hda' '/usr/share/alsa/init/hda'
make[3]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/alsactl/init »
make[2]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/alsactl/init »
make[2]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/alsactl »
make[3]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/alsactl »
test -z "/usr/sbin" || mkdir -p -- "/usr/sbin"
  /usr/bin/install -c 'alsactl' '/usr/sbin/alsactl'
test -z "/usr/share/man/man1" || mkdir -p -- "/usr/share/man/man1"
 /usr/bin/install -c -m 644 './alsactl.1' '/usr/share/man/man1/alsactl.1'
test -z "/usr/share/man/man7" || mkdir -p -- "/usr/share/man/man7"
 /usr/bin/install -c -m 644 './alsactl_init.7' '/usr/share/man/man7/alsactl_init.7'
make[3]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/alsactl »
make[2]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/alsactl »
make[1]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/alsactl »
Making install in utils
make[1]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/utils »
make[2]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/utils »
make[2]: Rien à faire pour « install-exec-am ».
make[2]: Rien à faire pour « install-data-am ».
make[2]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/utils »
make[1]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/utils »
Making install in m4
make[1]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/m4 »
make[2]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/m4 »
make[2]: Rien à faire pour « install-exec-am ».
make[2]: Rien à faire pour « install-data-am ».
make[2]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/m4 »
make[1]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/m4 »
Making install in po
make[1]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/po »
mkdir -p -- /usr/share
installing ja.gmo as /usr/share/locale/ja/LC_MESSAGES/alsa-utils.mo
if test "alsa-utils" = "gettext-tools"; then \
      mkdir -p -- /usr/share/gettext/po; \
      for file in Makefile.in.in remove-potcdate.sin quot.sed boldquot.sed [email]en@quot.header[/email] [email]en@boldquot.header[/email] insert-header.sin Rules-quot   Makevars.template; do \
        /usr/bin/install -c -m 644 ./$file \
                /usr/share/gettext/po/$file; \
      done; \
      for file in Makevars; do \
        rm -f /usr/share/gettext/po/$file; \
      done; \
    else \
      : ; \
    fi
make[1]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/po »
Making install in alsamixer
make[1]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/alsamixer »
make[2]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/alsamixer »
test -z "/usr/bin" || mkdir -p -- "/usr/bin"
  /usr/bin/install -c 'alsamixer' '/usr/bin/alsamixer'
test -z "/usr/share/man/man1" || mkdir -p -- "/usr/share/man/man1"
 /usr/bin/install -c -m 644 './alsamixer.1' '/usr/share/man/man1/alsamixer.1'
make[2]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/alsamixer »
make[1]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/alsamixer »
Making install in amixer
make[1]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/amixer »
make[2]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/amixer »
test -z "/usr/bin" || mkdir -p -- "/usr/bin"
  /usr/bin/install -c 'amixer' '/usr/bin/amixer'
test -z "/usr/share/man/man1" || mkdir -p -- "/usr/share/man/man1"
 /usr/bin/install -c -m 644 './amixer.1' '/usr/share/man/man1/amixer.1'
make[2]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/amixer »
make[1]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/amixer »
Making install in amidi
make[1]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/amidi »
make[2]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/amidi »
test -z "/usr/bin" || mkdir -p -- "/usr/bin"
  /usr/bin/install -c 'amidi' '/usr/bin/amidi'
test -z "/usr/share/man/man1" || mkdir -p -- "/usr/share/man/man1"
 /usr/bin/install -c -m 644 './amidi.1' '/usr/share/man/man1/amidi.1'
make[2]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/amidi »
make[1]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/amidi »
Making install in alsaconf
make[1]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/alsaconf »
Making install in po
make[2]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/alsaconf/po »
mkdir -p -- /usr/share
make[2]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/alsaconf/po »
make[2]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/alsaconf »
make[3]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/alsaconf »
test -z "/usr/sbin" || mkdir -p -- "/usr/sbin"
 /usr/bin/install -c 'alsaconf' '/usr/sbin/alsaconf'
 /usr/bin/install -c -m 644 alsaconf.8 /usr/share/man/man8/alsaconf.8
 /usr/bin/install -c -m 644 alsaconf.fr.8 /usr/share/man/fr/man8/alsaconf.8
make[3]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/alsaconf »
make[2]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/alsaconf »
make[1]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/alsaconf »
Making install in aplay
make[1]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/aplay »
make[2]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/aplay »
test -z "/usr/bin" || mkdir -p -- "/usr/bin"
  /usr/bin/install -c 'aplay' '/usr/bin/aplay'
make  install-exec-hook
make[3]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/aplay »
rm -f arecord
ln -s aplay arecord
rm -f /usr/bin/arecord
(cd /usr/bin && ln -s aplay arecord)
make[3]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/aplay »
test -z "/usr/share/man/man1" || mkdir -p -- "/usr/share/man/man1"
 /usr/bin/install -c -m 644 './aplay.1' '/usr/share/man/man1/aplay.1'
 /usr/bin/install -c -m 644 './arecord.1' '/usr/share/man/man1/arecord.1'
make  install-data-hook
make[3]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/aplay »
rm -f /usr/share/man/man1/arecord.1
(cd /usr/share/man/man1 && ln -s aplay.1 arecord.1)
make[3]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/aplay »
make[2]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/aplay »
make[1]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/aplay »
Making install in iecset
make[1]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/iecset »
make[2]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/iecset »
test -z "/usr/bin" || mkdir -p -- "/usr/bin"
  /usr/bin/install -c 'iecset' '/usr/bin/iecset'
test -z "/usr/share/man/man1" || mkdir -p -- "/usr/share/man/man1"
 /usr/bin/install -c -m 644 './iecset.1' '/usr/share/man/man1/iecset.1'
make[2]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/iecset »
make[1]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/iecset »
Making install in speaker-test
make[1]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/speaker-test »
Making install in samples
make[2]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/speaker-test/samples »
make[3]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/speaker-test/samples »
make[3]: Rien à faire pour « install-exec-am ».
test -z "/usr/share/alsa/speaker-test" || mkdir -p -- "/usr/share/alsa/speaker-test"
 /usr/bin/install -c -m 644 'sample_map.csv' '/usr/share/alsa/speaker-test/sample_map.csv'
test -z "/usr/share/sounds/alsa" || mkdir -p -- "/usr/share/sounds/alsa"
 /usr/bin/install -c -m 644 'Front_Left.wav' '/usr/share/sounds/alsa/Front_Left.wav'
 /usr/bin/install -c -m 644 'Rear_Center.wav' '/usr/share/sounds/alsa/Rear_Center.wav'
 /usr/bin/install -c -m 644 'Rear_Right.wav' '/usr/share/sounds/alsa/Rear_Right.wav'
 /usr/bin/install -c -m 644 'Side_Right.wav' '/usr/share/sounds/alsa/Side_Right.wav'
 /usr/bin/install -c -m 644 'Front_Center.wav' '/usr/share/sounds/alsa/Front_Center.wav'
 /usr/bin/install -c -m 644 'Front_Right.wav' '/usr/share/sounds/alsa/Front_Right.wav'
 /usr/bin/install -c -m 644 'Noise.wav' '/usr/share/sounds/alsa/Noise.wav'
 /usr/bin/install -c -m 644 'Rear_Left.wav' '/usr/share/sounds/alsa/Rear_Left.wav'
 /usr/bin/install -c -m 644 'Side_Left.wav' '/usr/share/sounds/alsa/Side_Left.wav'
make[3]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/speaker-test/samples »
make[2]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/speaker-test/samples »
make[2]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/speaker-test »
make[3]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/speaker-test »
test -z "/usr/bin" || mkdir -p -- "/usr/bin"
  /usr/bin/install -c 'speaker-test' '/usr/bin/speaker-test'
test -z "/usr/share/man/man1" || mkdir -p -- "/usr/share/man/man1"
 /usr/bin/install -c -m 644 './speaker-test.1' '/usr/share/man/man1/speaker-test.1'
make[3]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/speaker-test »
make[2]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/speaker-test »
make[1]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/speaker-test »
Making install in seq
make[1]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/seq »
Making install in aconnect
make[2]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/seq/aconnect »
make[3]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/seq/aconnect »
test -z "/usr/bin" || mkdir -p -- "/usr/bin"
  /usr/bin/install -c 'aconnect' '/usr/bin/aconnect'
test -z "/usr/share/man/man1" || mkdir -p -- "/usr/share/man/man1"
 /usr/bin/install -c -m 644 './aconnect.1' '/usr/share/man/man1/aconnect.1'
make[3]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/seq/aconnect »
make[2]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/seq/aconnect »
Making install in aplaymidi
make[2]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/seq/aplaymidi »
make[3]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/seq/aplaymidi »
test -z "/usr/bin" || mkdir -p -- "/usr/bin"
  /usr/bin/install -c 'aplaymidi' '/usr/bin/aplaymidi'
  /usr/bin/install -c 'arecordmidi' '/usr/bin/arecordmidi'
test -z "/usr/share/man/man1" || mkdir -p -- "/usr/share/man/man1"
 /usr/bin/install -c -m 644 './aplaymidi.1' '/usr/share/man/man1/aplaymidi.1'
 /usr/bin/install -c -m 644 './arecordmidi.1' '/usr/share/man/man1/arecordmidi.1'
make[3]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/seq/aplaymidi »
make[2]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/seq/aplaymidi »
Making install in aseqdump
make[2]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/seq/aseqdump »
make[3]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/seq/aseqdump »
test -z "/usr/bin" || mkdir -p -- "/usr/bin"
  /usr/bin/install -c 'aseqdump' '/usr/bin/aseqdump'
test -z "/usr/share/man/man1" || mkdir -p -- "/usr/share/man/man1"
 /usr/bin/install -c -m 644 './aseqdump.1' '/usr/share/man/man1/aseqdump.1'
make[3]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/seq/aseqdump »
make[2]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/seq/aseqdump »
Making install in aseqnet
make[2]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/seq/aseqnet »
make[3]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/seq/aseqnet »
test -z "/usr/bin" || mkdir -p -- "/usr/bin"
  /usr/bin/install -c 'aseqnet' '/usr/bin/aseqnet'
test -z "/usr/share/man/man1" || mkdir -p -- "/usr/share/man/man1"
 /usr/bin/install -c -m 644 './aseqnet.1' '/usr/share/man/man1/aseqnet.1'
make[3]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/seq/aseqnet »
make[2]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/seq/aseqnet »
make[2]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/seq »
make[3]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/seq »
make[3]: Rien à faire pour « install-exec-am ».
make[3]: Rien à faire pour « install-data-am ».
make[3]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/seq »
make[2]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/seq »
make[1]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/seq »
make[1]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20 »
make[2]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20 »
make[2]: Rien à faire pour « install-exec-am ».
make[2]: Rien à faire pour « install-data-am ».
make[2]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20 »
make[1]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20 »
rabgye@ubuntumaya:~/alsa-utils-1.0.20$ rm -f ~/alsa-driver*
rm: ne peut enlever `/home/rabgye/alsa-driver-1.0.20': est un dossier
rabgye@ubuntumaya:~/alsa-utils-1.0.20$ rm -f ~/alsa-lib*
rm: ne peut enlever `/home/rabgye/alsa-lib-1.0.20': est un dossier
rabgye@ubuntumaya:~/alsa-utils-1.0.20$ rm -f ~/alsa-utils*
rm: ne peut enlever `/home/rabgye/alsa-utils-1.0.20': est un dossier
rabgye@ubuntumaya:~/alsa-utils-1.0.20$ 


































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































make[1]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/amixer »
if gcc -DHAVE_CONFIG_H -I. -I. -I../include -I../include    -g -O2 -MT amixer.o -MD -MP -MF ".deps/amixer.Tpo" -c -o amixer.o amixer.c; \
    then mv -f ".deps/amixer.Tpo" ".deps/amixer.Po"; else rm -f ".deps/amixer.Tpo"; exit 1; fi
amixer.c: In function ‘get_integer’:
amixer.c:244: attention : ignoring return value of ‘strtol’, declared with attribute warn_unused_result
amixer.c: In function ‘get_integer64’:
amixer.c:272: attention : ignoring return value of ‘strtol’, declared with attribute warn_unused_result
amixer.c: In function ‘set_volume_simple’:
amixer.c:358: attention : ignoring return value of ‘strtol’, declared with attribute warn_unused_result
gcc  -g -O2   -o amixer  amixer.o -lm -lasound -lm -ldl -lpthread
make[1]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/amixer »
Making all in amidi
make[1]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/amidi »
if gcc -DHAVE_CONFIG_H -I. -I. -I../include -I../include    -g -O2 -MT amidi.o -MD -MP -MF ".deps/amidi.Tpo" -c -o amidi.o amidi.c; \
    then mv -f ".deps/amidi.Tpo" ".deps/amidi.Po"; else rm -f ".deps/amidi.Tpo"; exit 1; fi
amidi.c: In function ‘main’:
amidi.c:658: attention : ignoring return value of ‘write’, declared with attribute warn_unused_result
gcc  -g -O2   -o amidi  amidi.o  -lasound -lm -ldl -lpthread
make[1]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/amidi »
Making all in alsaconf
make[1]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/alsaconf »
Making all in po
make[2]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/alsaconf/po »
35 messages traduits, 1 message non traduit.
34 messages traduits, 1 traduction approximative, 1 message non traduit.
make[2]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/alsaconf/po »
make[2]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/alsaconf »
make[2]: Rien à faire pour « all-am ».
make[2]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/alsaconf »
make[1]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/alsaconf »
Making all in aplay
make[1]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/aplay »
if gcc -DHAVE_CONFIG_H -I. -I. -I../include -I../include    -g -O2 -MT aplay.o -MD -MP -MF ".deps/aplay.Tpo" -c -o aplay.o aplay.c; \
    then mv -f ".deps/aplay.Tpo" ".deps/aplay.Po"; else rm -f ".deps/aplay.Tpo"; exit 1; fi
aplay.c: In function ‘end_voc’:
aplay.c:2158: attention : ignoring return value of ‘write’, declared with attribute warn_unused_result
aplay.c: In function ‘end_wave’:
aplay.c:2178: attention : ignoring return value of ‘write’, declared with attribute warn_unused_result
aplay.c:2180: attention : ignoring return value of ‘write’, declared with attribute warn_unused_result
aplay.c: In function ‘end_au’:
aplay.c:2193: attention : ignoring return value of ‘write’, declared with attribute warn_unused_result
gcc  -g -O2   -o aplay  aplay.o  -lrt -lasound -lm -ldl -lpthread
make[1]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/aplay »
Making all in iecset
make[1]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/iecset »
if gcc -DHAVE_CONFIG_H -I. -I. -I../include -I../include    -g -O2 -MT iecset.o -MD -MP -MF ".deps/iecset.Tpo" -c -o iecset.o iecset.c; \
    then mv -f ".deps/iecset.Tpo" ".deps/iecset.Po"; else rm -f ".deps/iecset.Tpo"; exit 1; fi
if gcc -DHAVE_CONFIG_H -I. -I. -I../include -I../include    -g -O2 -MT iecbits.o -MD -MP -MF ".deps/iecbits.Tpo" -c -o iecbits.o iecbits.c; \
    then mv -f ".deps/iecbits.Tpo" ".deps/iecbits.Po"; else rm -f ".deps/iecbits.Tpo"; exit 1; fi
gcc  -g -O2   -o iecset  iecset.o iecbits.o -lm -lasound -lm -ldl -lpthread
make[1]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/iecset »
Making all in speaker-test
make[1]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/speaker-test »
Making all in samples
make[2]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/speaker-test/samples »
make[2]: Rien à faire pour « all ».
make[2]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/speaker-test/samples »
make[2]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/speaker-test »
if gcc -DHAVE_CONFIG_H -I. -I. -I../include -I../include    -g -O2 -MT speaker-test.o -MD -MP -MF ".deps/speaker-test.Tpo" -c -o speaker-test.o speaker-test.c; \
    then mv -f ".deps/speaker-test.Tpo" ".deps/speaker-test.Po"; else rm -f ".deps/speaker-test.Tpo"; exit 1; fi
if gcc -DHAVE_CONFIG_H -I. -I. -I../include -I../include    -g -O2 -MT pink.o -MD -MP -MF ".deps/pink.Tpo" -c -o pink.o pink.c; \
    then mv -f ".deps/pink.Tpo" ".deps/pink.Po"; else rm -f ".deps/pink.Tpo"; exit 1; fi
gcc  -g -O2   -o speaker-test  speaker-test.o pink.o  -lm -lasound -lm -ldl -lpthread
make[2]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/speaker-test »
make[1]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/speaker-test »
Making all in seq
make[1]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/seq »
Making all in aconnect
make[2]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/seq/aconnect »
if gcc -DHAVE_CONFIG_H -I. -I. -I../../include -I../../include    -g -O2 -MT aconnect.o -MD -MP -MF ".deps/aconnect.Tpo" -c -o aconnect.o aconnect.c; \
    then mv -f ".deps/aconnect.Tpo" ".deps/aconnect.Po"; else rm -f ".deps/aconnect.Tpo"; exit 1; fi
gcc  -g -O2   -o aconnect  aconnect.o  -lasound -lm -ldl -lpthread
make[2]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/seq/aconnect »
Making all in aplaymidi
make[2]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/seq/aplaymidi »
if gcc -DHAVE_CONFIG_H -I. -I. -I../../include -I../../include    -g -O2 -MT aplaymidi.o -MD -MP -MF ".deps/aplaymidi.Tpo" -c -o aplaymidi.o aplaymidi.c; \
    then mv -f ".deps/aplaymidi.Tpo" ".deps/aplaymidi.Po"; else rm -f ".deps/aplaymidi.Tpo"; exit 1; fi
gcc  -g -O2   -o aplaymidi  aplaymidi.o  -lasound -lm -ldl -lpthread
if gcc -DHAVE_CONFIG_H -I. -I. -I../../include -I../../include    -g -O2 -MT arecordmidi.o -MD -MP -MF ".deps/arecordmidi.Tpo" -c -o arecordmidi.o arecordmidi.c; \
    then mv -f ".deps/arecordmidi.Tpo" ".deps/arecordmidi.Po"; else rm -f ".deps/arecordmidi.Tpo"; exit 1; fi
gcc  -g -O2   -o arecordmidi  arecordmidi.o  -lasound -lm -ldl -lpthread
make[2]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/seq/aplaymidi »
Making all in aseqdump
make[2]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/seq/aseqdump »
if gcc -DHAVE_CONFIG_H -I. -I. -I../../include -I../../include    -g -O2 -MT aseqdump.o -MD -MP -MF ".deps/aseqdump.Tpo" -c -o aseqdump.o aseqdump.c; \
    then mv -f ".deps/aseqdump.Tpo" ".deps/aseqdump.Po"; else rm -f ".deps/aseqdump.Tpo"; exit 1; fi
gcc  -g -O2   -o aseqdump  aseqdump.o  -lasound -lm -ldl -lpthread
make[2]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/seq/aseqdump »
Making all in aseqnet
make[2]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/seq/aseqnet »
if gcc -DHAVE_CONFIG_H -I. -I. -I../../include -I../../include    -g -O2 -MT aseqnet.o -MD -MP -MF ".deps/aseqnet.Tpo" -c -o aseqnet.o aseqnet.c; \
    then mv -f ".deps/aseqnet.Tpo" ".deps/aseqnet.Po"; else rm -f ".deps/aseqnet.Tpo"; exit 1; fi
aseqnet.c: In function ‘flush_writebuf’:
aseqnet.c:495: attention : ignoring return value of ‘write’, declared with attribute warn_unused_result
gcc  -g -O2   -o aseqnet  aseqnet.o  -lasound -lm -ldl -lpthread
make[2]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/seq/aseqnet »
make[2]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/seq »
make[2]: Rien à faire pour « all-am ».
make[2]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/seq »
make[1]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/seq »
make[1]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20 »
make[1]: Rien à faire pour « all-am ».
make[1]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20 »
rabgye@ubuntumaya:~/alsa-utils-1.0.20$ sudo make
Making all in include
make[1]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/include »
make  all-am
make[2]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/include »
make[2]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/include »
make[1]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/include »
Making all in alsactl
make[1]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/alsactl »
Making all in init
make[2]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/alsactl/init »
make[2]: Rien à faire pour « all ».
make[2]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/alsactl/init »
make[2]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/alsactl »
make[2]: Rien à faire pour « all-am ».
make[2]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/alsactl »
make[1]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/alsactl »
Making all in utils
make[1]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/utils »
make[1]: Rien à faire pour « all ».
make[1]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/utils »
Making all in m4
make[1]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/m4 »
make[1]: Rien à faire pour « all ».
make[1]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/m4 »
Making all in po
make[1]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/po »
make[1]: Rien à faire pour « all ».
make[1]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/po »
Making all in alsamixer
make[1]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/alsamixer »
make[1]: Rien à faire pour « all ».
make[1]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/alsamixer »
Making all in amixer
make[1]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/amixer »
make[1]: Rien à faire pour « all ».
make[1]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/amixer »
Making all in amidi
make[1]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/amidi »
make[1]: Rien à faire pour « all ».
make[1]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/amidi »
Making all in alsaconf
make[1]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/alsaconf »
Making all in po
make[2]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/alsaconf/po »
make[2]: Rien à faire pour « all ».
make[2]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/alsaconf/po »
make[2]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/alsaconf »
make[2]: Rien à faire pour « all-am ».
make[2]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/alsaconf »
make[1]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/alsaconf »
Making all in aplay
make[1]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/aplay »
make[1]: Rien à faire pour « all ».
make[1]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/aplay »
Making all in iecset
make[1]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/iecset »
make[1]: Rien à faire pour « all ».
make[1]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/iecset »
Making all in speaker-test
make[1]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/speaker-test »
Making all in samples
make[2]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/speaker-test/samples »
make[2]: Rien à faire pour « all ».
make[2]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/speaker-test/samples »
make[2]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/speaker-test »
make[2]: Rien à faire pour « all-am ».
make[2]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/speaker-test »
make[1]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/speaker-test »
Making all in seq
make[1]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/seq »
Making all in aconnect
make[2]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/seq/aconnect »
make[2]: Rien à faire pour « all ».
make[2]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/seq/aconnect »
Making all in aplaymidi
make[2]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/seq/aplaymidi »
make[2]: Rien à faire pour « all ».
make[2]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/seq/aplaymidi »
Making all in aseqdump
make[2]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/seq/aseqdump »
make[2]: Rien à faire pour « all ».
make[2]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/seq/aseqdump »
Making all in aseqnet
make[2]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/seq/aseqnet »
make[2]: Rien à faire pour « all ».
make[2]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/seq/aseqnet »
make[2]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/seq »
make[2]: Rien à faire pour « all-am ».
make[2]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/seq »
make[1]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/seq »
make[1]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20 »
make[1]: Rien à faire pour « all-am ».
make[1]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20 »
rabgye@ubuntumaya:~/alsa-utils-1.0.20$ sudo make install
Making install in include
make[1]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/include »
make[2]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/include »
make[2]: Rien à faire pour « install-exec-am ».
make[2]: Rien à faire pour « install-data-am ».
make[2]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/include »
make[1]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/include »
Making install in alsactl
make[1]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/alsactl »
Making install in init
make[2]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/alsactl/init »
make[3]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/alsactl/init »
make[3]: Rien à faire pour « install-exec-am ».
test -z "/usr/share/alsa/init" || mkdir -p -- "/usr/share/alsa/init"
 /usr/bin/install -c -m 644 '00main' '/usr/share/alsa/init/00main'
 /usr/bin/install -c -m 644 'default' '/usr/share/alsa/init/default'
 /usr/bin/install -c -m 644 'help' '/usr/share/alsa/init/help'
 /usr/bin/install -c -m 644 'info' '/usr/share/alsa/init/info'
 /usr/bin/install -c -m 644 'test' '/usr/share/alsa/init/test'
 /usr/bin/install -c -m 644 'hda' '/usr/share/alsa/init/hda'
make[3]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/alsactl/init »
make[2]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/alsactl/init »
make[2]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/alsactl »
make[3]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/alsactl »
test -z "/usr/sbin" || mkdir -p -- "/usr/sbin"
  /usr/bin/install -c 'alsactl' '/usr/sbin/alsactl'
test -z "/usr/share/man/man1" || mkdir -p -- "/usr/share/man/man1"
 /usr/bin/install -c -m 644 './alsactl.1' '/usr/share/man/man1/alsactl.1'
test -z "/usr/share/man/man7" || mkdir -p -- "/usr/share/man/man7"
 /usr/bin/install -c -m 644 './alsactl_init.7' '/usr/share/man/man7/alsactl_init.7'
make[3]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/alsactl »
make[2]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/alsactl »
make[1]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/alsactl »
Making install in utils
make[1]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/utils »
make[2]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/utils »
make[2]: Rien à faire pour « install-exec-am ».
make[2]: Rien à faire pour « install-data-am ».
make[2]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/utils »
make[1]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/utils »
Making install in m4
make[1]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/m4 »
make[2]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/m4 »
make[2]: Rien à faire pour « install-exec-am ».
make[2]: Rien à faire pour « install-data-am ».
make[2]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/m4 »
make[1]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/m4 »
Making install in po
make[1]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/po »
mkdir -p -- /usr/share
installing ja.gmo as /usr/share/locale/ja/LC_MESSAGES/alsa-utils.mo
if test "alsa-utils" = "gettext-tools"; then \
      mkdir -p -- /usr/share/gettext/po; \
      for file in Makefile.in.in remove-potcdate.sin quot.sed boldquot.sed [email]en@quot.header[/email] [email]en@boldquot.header[/email] insert-header.sin Rules-quot   Makevars.template; do \
        /usr/bin/install -c -m 644 ./$file \
                /usr/share/gettext/po/$file; \
      done; \
      for file in Makevars; do \
        rm -f /usr/share/gettext/po/$file; \
      done; \
    else \
      : ; \
    fi
make[1]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/po »
Making install in alsamixer
make[1]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/alsamixer »
make[2]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/alsamixer »
test -z "/usr/bin" || mkdir -p -- "/usr/bin"
  /usr/bin/install -c 'alsamixer' '/usr/bin/alsamixer'
test -z "/usr/share/man/man1" || mkdir -p -- "/usr/share/man/man1"
 /usr/bin/install -c -m 644 './alsamixer.1' '/usr/share/man/man1/alsamixer.1'
make[2]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/alsamixer »
make[1]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/alsamixer »
Making install in amixer
make[1]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/amixer »
make[2]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/amixer »
test -z "/usr/bin" || mkdir -p -- "/usr/bin"
  /usr/bin/install -c 'amixer' '/usr/bin/amixer'
test -z "/usr/share/man/man1" || mkdir -p -- "/usr/share/man/man1"
 /usr/bin/install -c -m 644 './amixer.1' '/usr/share/man/man1/amixer.1'
make[2]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/amixer »
make[1]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/amixer »
Making install in amidi
make[1]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/amidi »
make[2]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/amidi »
test -z "/usr/bin" || mkdir -p -- "/usr/bin"
  /usr/bin/install -c 'amidi' '/usr/bin/amidi'
test -z "/usr/share/man/man1" || mkdir -p -- "/usr/share/man/man1"
 /usr/bin/install -c -m 644 './amidi.1' '/usr/share/man/man1/amidi.1'
make[2]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/amidi »
make[1]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/amidi »
Making install in alsaconf
make[1]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/alsaconf »
Making install in po
make[2]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/alsaconf/po »
mkdir -p -- /usr/share
make[2]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/alsaconf/po »
make[2]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/alsaconf »
make[3]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/alsaconf »
test -z "/usr/sbin" || mkdir -p -- "/usr/sbin"
 /usr/bin/install -c 'alsaconf' '/usr/sbin/alsaconf'
 /usr/bin/install -c -m 644 alsaconf.8 /usr/share/man/man8/alsaconf.8
 /usr/bin/install -c -m 644 alsaconf.fr.8 /usr/share/man/fr/man8/alsaconf.8
make[3]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/alsaconf »
make[2]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/alsaconf »
make[1]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/alsaconf »
Making install in aplay
make[1]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/aplay »
make[2]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/aplay »
test -z "/usr/bin" || mkdir -p -- "/usr/bin"
  /usr/bin/install -c 'aplay' '/usr/bin/aplay'
make  install-exec-hook
make[3]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/aplay »
rm -f arecord
ln -s aplay arecord
rm -f /usr/bin/arecord
(cd /usr/bin && ln -s aplay arecord)
make[3]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/aplay »
test -z "/usr/share/man/man1" || mkdir -p -- "/usr/share/man/man1"
 /usr/bin/install -c -m 644 './aplay.1' '/usr/share/man/man1/aplay.1'
 /usr/bin/install -c -m 644 './arecord.1' '/usr/share/man/man1/arecord.1'
make  install-data-hook
make[3]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/aplay »
rm -f /usr/share/man/man1/arecord.1
(cd /usr/share/man/man1 && ln -s aplay.1 arecord.1)
make[3]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/aplay »
make[2]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/aplay »
make[1]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/aplay »
Making install in iecset
make[1]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/iecset »
make[2]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/iecset »
test -z "/usr/bin" || mkdir -p -- "/usr/bin"
  /usr/bin/install -c 'iecset' '/usr/bin/iecset'
test -z "/usr/share/man/man1" || mkdir -p -- "/usr/share/man/man1"
 /usr/bin/install -c -m 644 './iecset.1' '/usr/share/man/man1/iecset.1'
make[2]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/iecset »
make[1]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/iecset »
Making install in speaker-test
make[1]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/speaker-test »
Making install in samples
make[2]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/speaker-test/samples »
make[3]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/speaker-test/samples »
make[3]: Rien à faire pour « install-exec-am ».
test -z "/usr/share/alsa/speaker-test" || mkdir -p -- "/usr/share/alsa/speaker-test"
 /usr/bin/install -c -m 644 'sample_map.csv' '/usr/share/alsa/speaker-test/sample_map.csv'
test -z "/usr/share/sounds/alsa" || mkdir -p -- "/usr/share/sounds/alsa"
 /usr/bin/install -c -m 644 'Front_Left.wav' '/usr/share/sounds/alsa/Front_Left.wav'
 /usr/bin/install -c -m 644 'Rear_Center.wav' '/usr/share/sounds/alsa/Rear_Center.wav'
 /usr/bin/install -c -m 644 'Rear_Right.wav' '/usr/share/sounds/alsa/Rear_Right.wav'
 /usr/bin/install -c -m 644 'Side_Right.wav' '/usr/share/sounds/alsa/Side_Right.wav'
 /usr/bin/install -c -m 644 'Front_Center.wav' '/usr/share/sounds/alsa/Front_Center.wav'
 /usr/bin/install -c -m 644 'Front_Right.wav' '/usr/share/sounds/alsa/Front_Right.wav'
 /usr/bin/install -c -m 644 'Noise.wav' '/usr/share/sounds/alsa/Noise.wav'
 /usr/bin/install -c -m 644 'Rear_Left.wav' '/usr/share/sounds/alsa/Rear_Left.wav'
 /usr/bin/install -c -m 644 'Side_Left.wav' '/usr/share/sounds/alsa/Side_Left.wav'
make[3]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/speaker-test/samples »
make[2]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/speaker-test/samples »
make[2]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/speaker-test »
make[3]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/speaker-test »
test -z "/usr/bin" || mkdir -p -- "/usr/bin"
  /usr/bin/install -c 'speaker-test' '/usr/bin/speaker-test'
test -z "/usr/share/man/man1" || mkdir -p -- "/usr/share/man/man1"
 /usr/bin/install -c -m 644 './speaker-test.1' '/usr/share/man/man1/speaker-test.1'
make[3]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/speaker-test »
make[2]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/speaker-test »
make[1]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/speaker-test »
Making install in seq
make[1]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/seq »
Making install in aconnect
make[2]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/seq/aconnect »
make[3]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/seq/aconnect »
test -z "/usr/bin" || mkdir -p -- "/usr/bin"
  /usr/bin/install -c 'aconnect' '/usr/bin/aconnect'
test -z "/usr/share/man/man1" || mkdir -p -- "/usr/share/man/man1"
 /usr/bin/install -c -m 644 './aconnect.1' '/usr/share/man/man1/aconnect.1'
make[3]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/seq/aconnect »
make[2]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/seq/aconnect »
Making install in aplaymidi
make[2]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/seq/aplaymidi »
make[3]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/seq/aplaymidi »
test -z "/usr/bin" || mkdir -p -- "/usr/bin"
  /usr/bin/install -c 'aplaymidi' '/usr/bin/aplaymidi'
  /usr/bin/install -c 'arecordmidi' '/usr/bin/arecordmidi'
test -z "/usr/share/man/man1" || mkdir -p -- "/usr/share/man/man1"
 /usr/bin/install -c -m 644 './aplaymidi.1' '/usr/share/man/man1/aplaymidi.1'
 /usr/bin/install -c -m 644 './arecordmidi.1' '/usr/share/man/man1/arecordmidi.1'
make[3]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/seq/aplaymidi »
make[2]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/seq/aplaymidi »
Making install in aseqdump
make[2]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/seq/aseqdump »
make[3]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/seq/aseqdump »
test -z "/usr/bin" || mkdir -p -- "/usr/bin"
  /usr/bin/install -c 'aseqdump' '/usr/bin/aseqdump'
test -z "/usr/share/man/man1" || mkdir -p -- "/usr/share/man/man1"
 /usr/bin/install -c -m 644 './aseqdump.1' '/usr/share/man/man1/aseqdump.1'
make[3]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/seq/aseqdump »
make[2]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/seq/aseqdump »
Making install in aseqnet
make[2]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/seq/aseqnet »
make[3]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/seq/aseqnet »
test -z "/usr/bin" || mkdir -p -- "/usr/bin"
  /usr/bin/install -c 'aseqnet' '/usr/bin/aseqnet'
test -z "/usr/share/man/man1" || mkdir -p -- "/usr/share/man/man1"
 /usr/bin/install -c -m 644 './aseqnet.1' '/usr/share/man/man1/aseqnet.1'
make[3]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/seq/aseqnet »
make[2]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/seq/aseqnet »
make[2]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/seq »
make[3]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/seq »
make[3]: Rien à faire pour « install-exec-am ».
make[3]: Rien à faire pour « install-data-am ».
make[3]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/seq »
make[2]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/seq »
make[1]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/seq »
make[1]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20 »
make[2]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20 »
make[2]: Rien à faire pour « install-exec-am ».
make[2]: Rien à faire pour « install-data-am ».
make[2]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20 »
make[1]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20 »
rabgye@ubuntumaya:~/alsa-utils-1.0.20$ rm -f ~/alsa-driver*
rm: ne peut enlever `/home/rabgye/alsa-driver-1.0.20': est un dossier
rabgye@ubuntumaya:~/alsa-utils-1.0.20$ rm -f ~/alsa-lib*
rm: ne peut enlever `/home/rabgye/alsa-lib-1.0.20': est un dossier
rabgye@ubuntumaya:~/alsa-utils-1.0.20$ rm -f ~/alsa-utils*
rm: ne peut enlever `/home/rabgye/alsa-utils-1.0.20': est un dossier
rabgye@ubuntumaya:~/alsa-utils-1.0.20$ 


































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































make[1]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/amixer »
if gcc -DHAVE_CONFIG_H -I. -I. -I../include -I../include    -g -O2 -MT amixer.o -MD -MP -MF ".deps/amixer.Tpo" -c -o amixer.o amixer.c; \
    then mv -f ".deps/amixer.Tpo" ".deps/amixer.Po"; else rm -f ".deps/amixer.Tpo"; exit 1; fi
amixer.c: In function ‘get_integer’:
amixer.c:244: attention : ignoring return value of ‘strtol’, declared with attribute warn_unused_result
amixer.c: In function ‘get_integer64’:
amixer.c:272: attention : ignoring return value of ‘strtol’, declared with attribute warn_unused_result
amixer.c: In function ‘set_volume_simple’:
amixer.c:358: attention : ignoring return value of ‘strtol’, declared with attribute warn_unused_result
gcc  -g -O2   -o amixer  amixer.o -lm -lasound -lm -ldl -lpthread
make[1]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/amixer »
Making all in amidi
make[1]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/amidi »
if gcc -DHAVE_CONFIG_H -I. -I. -I../include -I../include    -g -O2 -MT amidi.o -MD -MP -MF ".deps/amidi.Tpo" -c -o amidi.o amidi.c; \
    then mv -f ".deps/amidi.Tpo" ".deps/amidi.Po"; else rm -f ".deps/amidi.Tpo"; exit 1; fi
amidi.c: In function ‘main’:
amidi.c:658: attention : ignoring return value of ‘write’, declared with attribute warn_unused_result
gcc  -g -O2   -o amidi  amidi.o  -lasound -lm -ldl -lpthread
make[1]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/amidi »
Making all in alsaconf
make[1]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/alsaconf »
Making all in po
make[2]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/alsaconf/po »
35 messages traduits, 1 message non traduit.
34 messages traduits, 1 traduction approximative, 1 message non traduit.
make[2]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/alsaconf/po »
make[2]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/alsaconf »
make[2]: Rien à faire pour « all-am ».
make[2]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/alsaconf »
make[1]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/alsaconf »
Making all in aplay
make[1]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/aplay »
if gcc -DHAVE_CONFIG_H -I. -I. -I../include -I../include    -g -O2 -MT aplay.o -MD -MP -MF ".deps/aplay.Tpo" -c -o aplay.o aplay.c; \
    then mv -f ".deps/aplay.Tpo" ".deps/aplay.Po"; else rm -f ".deps/aplay.Tpo"; exit 1; fi
aplay.c: In function ‘end_voc’:
aplay.c:2158: attention : ignoring return value of ‘write’, declared with attribute warn_unused_result
aplay.c: In function ‘end_wave’:
aplay.c:2178: attention : ignoring return value of ‘write’, declared with attribute warn_unused_result
aplay.c:2180: attention : ignoring return value of ‘write’, declared with attribute warn_unused_result
aplay.c: In function ‘end_au’:
aplay.c:2193: attention : ignoring return value of ‘write’, declared with attribute warn_unused_result
gcc  -g -O2   -o aplay  aplay.o  -lrt -lasound -lm -ldl -lpthread
make[1]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/aplay »
Making all in iecset
make[1]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/iecset »
if gcc -DHAVE_CONFIG_H -I. -I. -I../include -I../include    -g -O2 -MT iecset.o -MD -MP -MF ".deps/iecset.Tpo" -c -o iecset.o iecset.c; \
    then mv -f ".deps/iecset.Tpo" ".deps/iecset.Po"; else rm -f ".deps/iecset.Tpo"; exit 1; fi
if gcc -DHAVE_CONFIG_H -I. -I. -I../include -I../include    -g -O2 -MT iecbits.o -MD -MP -MF ".deps/iecbits.Tpo" -c -o iecbits.o iecbits.c; \
    then mv -f ".deps/iecbits.Tpo" ".deps/iecbits.Po"; else rm -f ".deps/iecbits.Tpo"; exit 1; fi
gcc  -g -O2   -o iecset  iecset.o iecbits.o -lm -lasound -lm -ldl -lpthread
make[1]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/iecset »
Making all in speaker-test
make[1]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/speaker-test »
Making all in samples
make[2]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/speaker-test/samples »
make[2]: Rien à faire pour « all ».
make[2]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/speaker-test/samples »
make[2]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/speaker-test »
if gcc -DHAVE_CONFIG_H -I. -I. -I../include -I../include    -g -O2 -MT speaker-test.o -MD -MP -MF ".deps/speaker-test.Tpo" -c -o speaker-test.o speaker-test.c; \
    then mv -f ".deps/speaker-test.Tpo" ".deps/speaker-test.Po"; else rm -f ".deps/speaker-test.Tpo"; exit 1; fi
if gcc -DHAVE_CONFIG_H -I. -I. -I../include -I../include    -g -O2 -MT pink.o -MD -MP -MF ".deps/pink.Tpo" -c -o pink.o pink.c; \
    then mv -f ".deps/pink.Tpo" ".deps/pink.Po"; else rm -f ".deps/pink.Tpo"; exit 1; fi
gcc  -g -O2   -o speaker-test  speaker-test.o pink.o  -lm -lasound -lm -ldl -lpthread
make[2]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/speaker-test »
make[1]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/speaker-test »
Making all in seq
make[1]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/seq »
Making all in aconnect
make[2]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/seq/aconnect »
if gcc -DHAVE_CONFIG_H -I. -I. -I../../include -I../../include    -g -O2 -MT aconnect.o -MD -MP -MF ".deps/aconnect.Tpo" -c -o aconnect.o aconnect.c; \
    then mv -f ".deps/aconnect.Tpo" ".deps/aconnect.Po"; else rm -f ".deps/aconnect.Tpo"; exit 1; fi
gcc  -g -O2   -o aconnect  aconnect.o  -lasound -lm -ldl -lpthread
make[2]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/seq/aconnect »
Making all in aplaymidi
make[2]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/seq/aplaymidi »
if gcc -DHAVE_CONFIG_H -I. -I. -I../../include -I../../include    -g -O2 -MT aplaymidi.o -MD -MP -MF ".deps/aplaymidi.Tpo" -c -o aplaymidi.o aplaymidi.c; \
    then mv -f ".deps/aplaymidi.Tpo" ".deps/aplaymidi.Po"; else rm -f ".deps/aplaymidi.Tpo"; exit 1; fi
gcc  -g -O2   -o aplaymidi  aplaymidi.o  -lasound -lm -ldl -lpthread
if gcc -DHAVE_CONFIG_H -I. -I. -I../../include -I../../include    -g -O2 -MT arecordmidi.o -MD -MP -MF ".deps/arecordmidi.Tpo" -c -o arecordmidi.o arecordmidi.c; \
    then mv -f ".deps/arecordmidi.Tpo" ".deps/arecordmidi.Po"; else rm -f ".deps/arecordmidi.Tpo"; exit 1; fi
gcc  -g -O2   -o arecordmidi  arecordmidi.o  -lasound -lm -ldl -lpthread
make[2]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/seq/aplaymidi »
Making all in aseqdump
make[2]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/seq/aseqdump »
if gcc -DHAVE_CONFIG_H -I. -I. -I../../include -I../../include    -g -O2 -MT aseqdump.o -MD -MP -MF ".deps/aseqdump.Tpo" -c -o aseqdump.o aseqdump.c; \
    then mv -f ".deps/aseqdump.Tpo" ".deps/aseqdump.Po"; else rm -f ".deps/aseqdump.Tpo"; exit 1; fi
gcc  -g -O2   -o aseqdump  aseqdump.o  -lasound -lm -ldl -lpthread
make[2]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/seq/aseqdump »
Making all in aseqnet
make[2]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/seq/aseqnet »
if gcc -DHAVE_CONFIG_H -I. -I. -I../../include -I../../include    -g -O2 -MT aseqnet.o -MD -MP -MF ".deps/aseqnet.Tpo" -c -o aseqnet.o aseqnet.c; \
    then mv -f ".deps/aseqnet.Tpo" ".deps/aseqnet.Po"; else rm -f ".deps/aseqnet.Tpo"; exit 1; fi
aseqnet.c: In function ‘flush_writebuf’:
aseqnet.c:495: attention : ignoring return value of ‘write’, declared with attribute warn_unused_result
gcc  -g -O2   -o aseqnet  aseqnet.o  -lasound -lm -ldl -lpthread
make[2]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/seq/aseqnet »
make[2]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/seq »
make[2]: Rien à faire pour « all-am ».
make[2]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/seq »
make[1]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/seq »
make[1]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20 »
make[1]: Rien à faire pour « all-am ».
make[1]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20 »
rabgye@ubuntumaya:~/alsa-utils-1.0.20$ sudo make
Making all in include
make[1]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/include »
make  all-am
make[2]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/include »
make[2]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/include »
make[1]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/include »
Making all in alsactl
make[1]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/alsactl »
Making all in init
make[2]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/alsactl/init »
make[2]: Rien à faire pour « all ».
make[2]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/alsactl/init »
make[2]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/alsactl »
make[2]: Rien à faire pour « all-am ».
make[2]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/alsactl »
make[1]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/alsactl »
Making all in utils
make[1]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/utils »
make[1]: Rien à faire pour « all ».
make[1]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/utils »
Making all in m4
make[1]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/m4 »
make[1]: Rien à faire pour « all ».
make[1]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/m4 »
Making all in po
make[1]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/po »
make[1]: Rien à faire pour « all ».
make[1]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/po »
Making all in alsamixer
make[1]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/alsamixer »
make[1]: Rien à faire pour « all ».
make[1]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/alsamixer »
Making all in amixer
make[1]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/amixer »
make[1]: Rien à faire pour « all ».
make[1]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/amixer »
Making all in amidi
make[1]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/amidi »
make[1]: Rien à faire pour « all ».
make[1]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/amidi »
Making all in alsaconf
make[1]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/alsaconf »
Making all in po
make[2]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/alsaconf/po »
make[2]: Rien à faire pour « all ».
make[2]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/alsaconf/po »
make[2]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/alsaconf »
make[2]: Rien à faire pour « all-am ».
make[2]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/alsaconf »
make[1]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/alsaconf »
Making all in aplay
make[1]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/aplay »
make[1]: Rien à faire pour « all ».
make[1]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/aplay »
Making all in iecset
make[1]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/iecset »
make[1]: Rien à faire pour « all ».
make[1]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/iecset »
Making all in speaker-test
make[1]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/speaker-test »
Making all in samples
make[2]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/speaker-test/samples »
make[2]: Rien à faire pour « all ».
make[2]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/speaker-test/samples »
make[2]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/speaker-test »
make[2]: Rien à faire pour « all-am ».
make[2]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/speaker-test »
make[1]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/speaker-test »
Making all in seq
make[1]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/seq »
Making all in aconnect
make[2]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/seq/aconnect »
make[2]: Rien à faire pour « all ».
make[2]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/seq/aconnect »
Making all in aplaymidi
make[2]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/seq/aplaymidi »
make[2]: Rien à faire pour « all ».
make[2]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/seq/aplaymidi »
Making all in aseqdump
make[2]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/seq/aseqdump »
make[2]: Rien à faire pour « all ».
make[2]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/seq/aseqdump »
Making all in aseqnet
make[2]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/seq/aseqnet »
make[2]: Rien à faire pour « all ».
make[2]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/seq/aseqnet »
make[2]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/seq »
make[2]: Rien à faire pour « all-am ».
make[2]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/seq »
make[1]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/seq »
make[1]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20 »
make[1]: Rien à faire pour « all-am ».
make[1]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20 »
rabgye@ubuntumaya:~/alsa-utils-1.0.20$ sudo make install
Making install in include
make[1]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/include »
make[2]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/include »
make[2]: Rien à faire pour « install-exec-am ».
make[2]: Rien à faire pour « install-data-am ».
make[2]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/include »
make[1]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/include »
Making install in alsactl
make[1]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/alsactl »
Making install in init
make[2]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/alsactl/init »
make[3]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/alsactl/init »
make[3]: Rien à faire pour « install-exec-am ».
test -z "/usr/share/alsa/init" || mkdir -p -- "/usr/share/alsa/init"
 /usr/bin/install -c -m 644 '00main' '/usr/share/alsa/init/00main'
 /usr/bin/install -c -m 644 'default' '/usr/share/alsa/init/default'
 /usr/bin/install -c -m 644 'help' '/usr/share/alsa/init/help'
 /usr/bin/install -c -m 644 'info' '/usr/share/alsa/init/info'
 /usr/bin/install -c -m 644 'test' '/usr/share/alsa/init/test'
 /usr/bin/install -c -m 644 'hda' '/usr/share/alsa/init/hda'
make[3]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/alsactl/init »
make[2]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/alsactl/init »
make[2]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/alsactl »
make[3]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/alsactl »
test -z "/usr/sbin" || mkdir -p -- "/usr/sbin"
  /usr/bin/install -c 'alsactl' '/usr/sbin/alsactl'
test -z "/usr/share/man/man1" || mkdir -p -- "/usr/share/man/man1"
 /usr/bin/install -c -m 644 './alsactl.1' '/usr/share/man/man1/alsactl.1'
test -z "/usr/share/man/man7" || mkdir -p -- "/usr/share/man/man7"
 /usr/bin/install -c -m 644 './alsactl_init.7' '/usr/share/man/man7/alsactl_init.7'
make[3]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/alsactl »
make[2]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/alsactl »
make[1]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/alsactl »
Making install in utils
make[1]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/utils »
make[2]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/utils »
make[2]: Rien à faire pour « install-exec-am ».
make[2]: Rien à faire pour « install-data-am ».
make[2]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/utils »
make[1]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/utils »
Making install in m4
make[1]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/m4 »
make[2]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/m4 »
make[2]: Rien à faire pour « install-exec-am ».
make[2]: Rien à faire pour « install-data-am ».
make[2]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/m4 »
make[1]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/m4 »
Making install in po
make[1]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/po »
mkdir -p -- /usr/share
installing ja.gmo as /usr/share/locale/ja/LC_MESSAGES/alsa-utils.mo
if test "alsa-utils" = "gettext-tools"; then \
      mkdir -p -- /usr/share/gettext/po; \
      for file in Makefile.in.in remove-potcdate.sin quot.sed boldquot.sed [email]en@quot.header[/email] [email]en@boldquot.header[/email] insert-header.sin Rules-quot   Makevars.template; do \
        /usr/bin/install -c -m 644 ./$file \
                /usr/share/gettext/po/$file; \
      done; \
      for file in Makevars; do \
        rm -f /usr/share/gettext/po/$file; \
      done; \
    else \
      : ; \
    fi
make[1]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/po »
Making install in alsamixer
make[1]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/alsamixer »
make[2]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/alsamixer »
test -z "/usr/bin" || mkdir -p -- "/usr/bin"
  /usr/bin/install -c 'alsamixer' '/usr/bin/alsamixer'
test -z "/usr/share/man/man1" || mkdir -p -- "/usr/share/man/man1"
 /usr/bin/install -c -m 644 './alsamixer.1' '/usr/share/man/man1/alsamixer.1'
make[2]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/alsamixer »
make[1]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/alsamixer »
Making install in amixer
make[1]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/amixer »
make[2]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/amixer »
test -z "/usr/bin" || mkdir -p -- "/usr/bin"
  /usr/bin/install -c 'amixer' '/usr/bin/amixer'
test -z "/usr/share/man/man1" || mkdir -p -- "/usr/share/man/man1"
 /usr/bin/install -c -m 644 './amixer.1' '/usr/share/man/man1/amixer.1'
make[2]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/amixer »
make[1]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/amixer »
Making install in amidi
make[1]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/amidi »
make[2]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/amidi »
test -z "/usr/bin" || mkdir -p -- "/usr/bin"
  /usr/bin/install -c 'amidi' '/usr/bin/amidi'
test -z "/usr/share/man/man1" || mkdir -p -- "/usr/share/man/man1"
 /usr/bin/install -c -m 644 './amidi.1' '/usr/share/man/man1/amidi.1'
make[2]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/amidi »
make[1]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/amidi »
Making install in alsaconf
make[1]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/alsaconf »
Making install in po
make[2]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/alsaconf/po »
mkdir -p -- /usr/share
make[2]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/alsaconf/po »
make[2]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/alsaconf »
make[3]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/alsaconf »
test -z "/usr/sbin" || mkdir -p -- "/usr/sbin"
 /usr/bin/install -c 'alsaconf' '/usr/sbin/alsaconf'
 /usr/bin/install -c -m 644 alsaconf.8 /usr/share/man/man8/alsaconf.8
 /usr/bin/install -c -m 644 alsaconf.fr.8 /usr/share/man/fr/man8/alsaconf.8
make[3]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/alsaconf »
make[2]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/alsaconf »
make[1]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/alsaconf »
Making install in aplay
make[1]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/aplay »
make[2]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/aplay »
test -z "/usr/bin" || mkdir -p -- "/usr/bin"
  /usr/bin/install -c 'aplay' '/usr/bin/aplay'
make  install-exec-hook
make[3]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/aplay »
rm -f arecord
ln -s aplay arecord
rm -f /usr/bin/arecord
(cd /usr/bin && ln -s aplay arecord)
make[3]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/aplay »
test -z "/usr/share/man/man1" || mkdir -p -- "/usr/share/man/man1"
 /usr/bin/install -c -m 644 './aplay.1' '/usr/share/man/man1/aplay.1'
 /usr/bin/install -c -m 644 './arecord.1' '/usr/share/man/man1/arecord.1'
make  install-data-hook
make[3]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/aplay »
rm -f /usr/share/man/man1/arecord.1
(cd /usr/share/man/man1 && ln -s aplay.1 arecord.1)
make[3]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/aplay »
make[2]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/aplay »
make[1]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/aplay »
Making install in iecset
make[1]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/iecset »
make[2]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/iecset »
test -z "/usr/bin" || mkdir -p -- "/usr/bin"
  /usr/bin/install -c 'iecset' '/usr/bin/iecset'
test -z "/usr/share/man/man1" || mkdir -p -- "/usr/share/man/man1"
 /usr/bin/install -c -m 644 './iecset.1' '/usr/share/man/man1/iecset.1'
make[2]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/iecset »
make[1]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/iecset »
Making install in speaker-test
make[1]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/speaker-test »
Making install in samples
make[2]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/speaker-test/samples »
make[3]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/speaker-test/samples »
make[3]: Rien à faire pour « install-exec-am ».
test -z "/usr/share/alsa/speaker-test" || mkdir -p -- "/usr/share/alsa/speaker-test"
 /usr/bin/install -c -m 644 'sample_map.csv' '/usr/share/alsa/speaker-test/sample_map.csv'
test -z "/usr/share/sounds/alsa" || mkdir -p -- "/usr/share/sounds/alsa"
 /usr/bin/install -c -m 644 'Front_Left.wav' '/usr/share/sounds/alsa/Front_Left.wav'
 /usr/bin/install -c -m 644 'Rear_Center.wav' '/usr/share/sounds/alsa/Rear_Center.wav'
 /usr/bin/install -c -m 644 'Rear_Right.wav' '/usr/share/sounds/alsa/Rear_Right.wav'
 /usr/bin/install -c -m 644 'Side_Right.wav' '/usr/share/sounds/alsa/Side_Right.wav'
 /usr/bin/install -c -m 644 'Front_Center.wav' '/usr/share/sounds/alsa/Front_Center.wav'
 /usr/bin/install -c -m 644 'Front_Right.wav' '/usr/share/sounds/alsa/Front_Right.wav'
 /usr/bin/install -c -m 644 'Noise.wav' '/usr/share/sounds/alsa/Noise.wav'
 /usr/bin/install -c -m 644 'Rear_Left.wav' '/usr/share/sounds/alsa/Rear_Left.wav'
 /usr/bin/install -c -m 644 'Side_Left.wav' '/usr/share/sounds/alsa/Side_Left.wav'
make[3]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/speaker-test/samples »
make[2]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/speaker-test/samples »
make[2]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/speaker-test »
make[3]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/speaker-test »
test -z "/usr/bin" || mkdir -p -- "/usr/bin"
  /usr/bin/install -c 'speaker-test' '/usr/bin/speaker-test'
test -z "/usr/share/man/man1" || mkdir -p -- "/usr/share/man/man1"
 /usr/bin/install -c -m 644 './speaker-test.1' '/usr/share/man/man1/speaker-test.1'
make[3]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/speaker-test »
make[2]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/speaker-test »
make[1]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/speaker-test »
Making install in seq
make[1]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/seq »
Making install in aconnect
make[2]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/seq/aconnect »
make[3]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/seq/aconnect »
test -z "/usr/bin" || mkdir -p -- "/usr/bin"
  /usr/bin/install -c 'aconnect' '/usr/bin/aconnect'
test -z "/usr/share/man/man1" || mkdir -p -- "/usr/share/man/man1"
 /usr/bin/install -c -m 644 './aconnect.1' '/usr/share/man/man1/aconnect.1'
make[3]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/seq/aconnect »
make[2]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/seq/aconnect »
Making install in aplaymidi
make[2]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/seq/aplaymidi »
make[3]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/seq/aplaymidi »
test -z "/usr/bin" || mkdir -p -- "/usr/bin"
  /usr/bin/install -c 'aplaymidi' '/usr/bin/aplaymidi'
  /usr/bin/install -c 'arecordmidi' '/usr/bin/arecordmidi'
test -z "/usr/share/man/man1" || mkdir -p -- "/usr/share/man/man1"
 /usr/bin/install -c -m 644 './aplaymidi.1' '/usr/share/man/man1/aplaymidi.1'
 /usr/bin/install -c -m 644 './arecordmidi.1' '/usr/share/man/man1/arecordmidi.1'
make[3]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/seq/aplaymidi »
make[2]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/seq/aplaymidi »
Making install in aseqdump
make[2]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/seq/aseqdump »
make[3]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/seq/aseqdump »
test -z "/usr/bin" || mkdir -p -- "/usr/bin"
  /usr/bin/install -c 'aseqdump' '/usr/bin/aseqdump'
test -z "/usr/share/man/man1" || mkdir -p -- "/usr/share/man/man1"
 /usr/bin/install -c -m 644 './aseqdump.1' '/usr/share/man/man1/aseqdump.1'
make[3]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/seq/aseqdump »
make[2]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/seq/aseqdump »
Making install in aseqnet
make[2]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/seq/aseqnet »
make[3]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/seq/aseqnet »
test -z "/usr/bin" || mkdir -p -- "/usr/bin"
  /usr/bin/install -c 'aseqnet' '/usr/bin/aseqnet'
test -z "/usr/share/man/man1" || mkdir -p -- "/usr/share/man/man1"
 /usr/bin/install -c -m 644 './aseqnet.1' '/usr/share/man/man1/aseqnet.1'
make[3]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/seq/aseqnet »
make[2]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/seq/aseqnet »
make[2]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/seq »
make[3]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/seq »
make[3]: Rien à faire pour « install-exec-am ».
make[3]: Rien à faire pour « install-data-am ».
make[3]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/seq »
make[2]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/seq »
make[1]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/seq »
make[1]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20 »
make[2]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20 »
make[2]: Rien à faire pour « install-exec-am ».
make[2]: Rien à faire pour « install-data-am ».
make[2]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20 »
make[1]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20 »
rabgye@ubuntumaya:~/alsa-utils-1.0.20$ rm -f ~/alsa-driver*
rm: ne peut enlever `/home/rabgye/alsa-driver-1.0.20': est un dossier
rabgye@ubuntumaya:~/alsa-utils-1.0.20$ rm -f ~/alsa-lib*
rm: ne peut enlever `/home/rabgye/alsa-lib-1.0.20': est un dossier
rabgye@ubuntumaya:~/alsa-utils-1.0.20$ rm -f ~/alsa-utils*
rm: ne peut enlever `/home/rabgye/alsa-utils-1.0.20': est un dossier
rabgye@ubuntumaya:~/alsa-utils-1.0.20$ 


































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































make[1]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/amixer »
if gcc -DHAVE_CONFIG_H -I. -I. -I../include -I../include    -g -O2 -MT amixer.o -MD -MP -MF ".deps/amixer.Tpo" -c -o amixer.o amixer.c; \
    then mv -f ".deps/amixer.Tpo" ".deps/amixer.Po"; else rm -f ".deps/amixer.Tpo"; exit 1; fi
amixer.c: In function ‘get_integer’:
amixer.c:244: attention : ignoring return value of ‘strtol’, declared with attribute warn_unused_result
amixer.c: In function ‘get_integer64’:
amixer.c:272: attention : ignoring return value of ‘strtol’, declared with attribute warn_unused_result
amixer.c: In function ‘set_volume_simple’:
amixer.c:358: attention : ignoring return value of ‘strtol’, declared with attribute warn_unused_result
gcc  -g -O2   -o amixer  amixer.o -lm -lasound -lm -ldl -lpthread
make[1]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/amixer »
Making all in amidi
make[1]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/amidi »
if gcc -DHAVE_CONFIG_H -I. -I. -I../include -I../include    -g -O2 -MT amidi.o -MD -MP -MF ".deps/amidi.Tpo" -c -o amidi.o amidi.c; \
    then mv -f ".deps/amidi.Tpo" ".deps/amidi.Po"; else rm -f ".deps/amidi.Tpo"; exit 1; fi
amidi.c: In function ‘main’:
amidi.c:658: attention : ignoring return value of ‘write’, declared with attribute warn_unused_result
gcc  -g -O2   -o amidi  amidi.o  -lasound -lm -ldl -lpthread
make[1]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/amidi »
Making all in alsaconf
make[1]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/alsaconf »
Making all in po
make[2]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/alsaconf/po »
35 messages traduits, 1 message non traduit.
34 messages traduits, 1 traduction approximative, 1 message non traduit.
make[2]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/alsaconf/po »
make[2]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/alsaconf »
make[2]: Rien à faire pour « all-am ».
make[2]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/alsaconf »
make[1]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/alsaconf »
Making all in aplay
make[1]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/aplay »
if gcc -DHAVE_CONFIG_H -I. -I. -I../include -I../include    -g -O2 -MT aplay.o -MD -MP -MF ".deps/aplay.Tpo" -c -o aplay.o aplay.c; \
    then mv -f ".deps/aplay.Tpo" ".deps/aplay.Po"; else rm -f ".deps/aplay.Tpo"; exit 1; fi
aplay.c: In function ‘end_voc’:
aplay.c:2158: attention : ignoring return value of ‘write’, declared with attribute warn_unused_result
aplay.c: In function ‘end_wave’:
aplay.c:2178: attention : ignoring return value of ‘write’, declared with attribute warn_unused_result
aplay.c:2180: attention : ignoring return value of ‘write’, declared with attribute warn_unused_result
aplay.c: In function ‘end_au’:
aplay.c:2193: attention : ignoring return value of ‘write’, declared with attribute warn_unused_result
gcc  -g -O2   -o aplay  aplay.o  -lrt -lasound -lm -ldl -lpthread
make[1]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/aplay »
Making all in iecset
make[1]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/iecset »
if gcc -DHAVE_CONFIG_H -I. -I. -I../include -I../include    -g -O2 -MT iecset.o -MD -MP -MF ".deps/iecset.Tpo" -c -o iecset.o iecset.c; \
    then mv -f ".deps/iecset.Tpo" ".deps/iecset.Po"; else rm -f ".deps/iecset.Tpo"; exit 1; fi
if gcc -DHAVE_CONFIG_H -I. -I. -I../include -I../include    -g -O2 -MT iecbits.o -MD -MP -MF ".deps/iecbits.Tpo" -c -o iecbits.o iecbits.c; \
    then mv -f ".deps/iecbits.Tpo" ".deps/iecbits.Po"; else rm -f ".deps/iecbits.Tpo"; exit 1; fi
gcc  -g -O2   -o iecset  iecset.o iecbits.o -lm -lasound -lm -ldl -lpthread
make[1]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/iecset »
Making all in speaker-test
make[1]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/speaker-test »
Making all in samples
make[2]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/speaker-test/samples »
make[2]: Rien à faire pour « all ».
make[2]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/speaker-test/samples »
make[2]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/speaker-test »
if gcc -DHAVE_CONFIG_H -I. -I. -I../include -I../include    -g -O2 -MT speaker-test.o -MD -MP -MF ".deps/speaker-test.Tpo" -c -o speaker-test.o speaker-test.c; \
    then mv -f ".deps/speaker-test.Tpo" ".deps/speaker-test.Po"; else rm -f ".deps/speaker-test.Tpo"; exit 1; fi
if gcc -DHAVE_CONFIG_H -I. -I. -I../include -I../include    -g -O2 -MT pink.o -MD -MP -MF ".deps/pink.Tpo" -c -o pink.o pink.c; \
    then mv -f ".deps/pink.Tpo" ".deps/pink.Po"; else rm -f ".deps/pink.Tpo"; exit 1; fi
gcc  -g -O2   -o speaker-test  speaker-test.o pink.o  -lm -lasound -lm -ldl -lpthread
make[2]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/speaker-test »
make[1]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/speaker-test »
Making all in seq
make[1]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/seq »
Making all in aconnect
make[2]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/seq/aconnect »
if gcc -DHAVE_CONFIG_H -I. -I. -I../../include -I../../include    -g -O2 -MT aconnect.o -MD -MP -MF ".deps/aconnect.Tpo" -c -o aconnect.o aconnect.c; \
    then mv -f ".deps/aconnect.Tpo" ".deps/aconnect.Po"; else rm -f ".deps/aconnect.Tpo"; exit 1; fi
gcc  -g -O2   -o aconnect  aconnect.o  -lasound -lm -ldl -lpthread
make[2]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/seq/aconnect »
Making all in aplaymidi
make[2]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/seq/aplaymidi »
if gcc -DHAVE_CONFIG_H -I. -I. -I../../include -I../../include    -g -O2 -MT aplaymidi.o -MD -MP -MF ".deps/aplaymidi.Tpo" -c -o aplaymidi.o aplaymidi.c; \
    then mv -f ".deps/aplaymidi.Tpo" ".deps/aplaymidi.Po"; else rm -f ".deps/aplaymidi.Tpo"; exit 1; fi
gcc  -g -O2   -o aplaymidi  aplaymidi.o  -lasound -lm -ldl -lpthread
if gcc -DHAVE_CONFIG_H -I. -I. -I../../include -I../../include    -g -O2 -MT arecordmidi.o -MD -MP -MF ".deps/arecordmidi.Tpo" -c -o arecordmidi.o arecordmidi.c; \
    then mv -f ".deps/arecordmidi.Tpo" ".deps/arecordmidi.Po"; else rm -f ".deps/arecordmidi.Tpo"; exit 1; fi
gcc  -g -O2   -o arecordmidi  arecordmidi.o  -lasound -lm -ldl -lpthread
make[2]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/seq/aplaymidi »
Making all in aseqdump
make[2]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/seq/aseqdump »
if gcc -DHAVE_CONFIG_H -I. -I. -I../../include -I../../include    -g -O2 -MT aseqdump.o -MD -MP -MF ".deps/aseqdump.Tpo" -c -o aseqdump.o aseqdump.c; \
    then mv -f ".deps/aseqdump.Tpo" ".deps/aseqdump.Po"; else rm -f ".deps/aseqdump.Tpo"; exit 1; fi
gcc  -g -O2   -o aseqdump  aseqdump.o  -lasound -lm -ldl -lpthread
make[2]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/seq/aseqdump »
Making all in aseqnet
make[2]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/seq/aseqnet »
if gcc -DHAVE_CONFIG_H -I. -I. -I../../include -I../../include    -g -O2 -MT aseqnet.o -MD -MP -MF ".deps/aseqnet.Tpo" -c -o aseqnet.o aseqnet.c; \
    then mv -f ".deps/aseqnet.Tpo" ".deps/aseqnet.Po"; else rm -f ".deps/aseqnet.Tpo"; exit 1; fi
aseqnet.c: In function ‘flush_writebuf’:
aseqnet.c:495: attention : ignoring return value of ‘write’, declared with attribute warn_unused_result
gcc  -g -O2   -o aseqnet  aseqnet.o  -lasound -lm -ldl -lpthread
make[2]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/seq/aseqnet »
make[2]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/seq »
make[2]: Rien à faire pour « all-am ».
make[2]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/seq »
make[1]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/seq »
make[1]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20 »
make[1]: Rien à faire pour « all-am ».
make[1]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20 »
rabgye@ubuntumaya:~/alsa-utils-1.0.20$ sudo make
Making all in include
make[1]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/include »
make  all-am
make[2]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/include »
make[2]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/include »
make[1]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/include »
Making all in alsactl
make[1]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/alsactl »
Making all in init
make[2]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/alsactl/init »
make[2]: Rien à faire pour « all ».
make[2]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/alsactl/init »
make[2]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/alsactl »
make[2]: Rien à faire pour « all-am ».
make[2]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/alsactl »
make[1]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/alsactl »
Making all in utils
make[1]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/utils »
make[1]: Rien à faire pour « all ».
make[1]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/utils »
Making all in m4
make[1]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/m4 »
make[1]: Rien à faire pour « all ».
make[1]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/m4 »
Making all in po
make[1]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/po »
make[1]: Rien à faire pour « all ».
make[1]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/po »
Making all in alsamixer
make[1]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/alsamixer »
make[1]: Rien à faire pour « all ».
make[1]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/alsamixer »
Making all in amixer
make[1]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/amixer »
make[1]: Rien à faire pour « all ».
make[1]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/amixer »
Making all in amidi
make[1]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/amidi »
make[1]: Rien à faire pour « all ».
make[1]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/amidi »
Making all in alsaconf
make[1]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/alsaconf »
Making all in po
make[2]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/alsaconf/po »
make[2]: Rien à faire pour « all ».
make[2]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/alsaconf/po »
make[2]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/alsaconf »
make[2]: Rien à faire pour « all-am ».
make[2]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/alsaconf »
make[1]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/alsaconf »
Making all in aplay
make[1]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/aplay »
make[1]: Rien à faire pour « all ».
make[1]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/aplay »
Making all in iecset
make[1]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/iecset »
make[1]: Rien à faire pour « all ».
make[1]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/iecset »
Making all in speaker-test
make[1]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/speaker-test »
Making all in samples
make[2]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/speaker-test/samples »
make[2]: Rien à faire pour « all ».
make[2]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/speaker-test/samples »
make[2]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/speaker-test »
make[2]: Rien à faire pour « all-am ».
make[2]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/speaker-test »
make[1]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/speaker-test »
Making all in seq
make[1]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/seq »
Making all in aconnect
make[2]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/seq/aconnect »
make[2]: Rien à faire pour « all ».
make[2]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/seq/aconnect »
Making all in aplaymidi
make[2]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/seq/aplaymidi »
make[2]: Rien à faire pour « all ».
make[2]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/seq/aplaymidi »
Making all in aseqdump
make[2]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/seq/aseqdump »
make[2]: Rien à faire pour « all ».
make[2]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/seq/aseqdump »
Making all in aseqnet
make[2]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/seq/aseqnet »
make[2]: Rien à faire pour « all ».
make[2]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/seq/aseqnet »
make[2]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/seq »
make[2]: Rien à faire pour « all-am ».
make[2]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/seq »
make[1]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/seq »
make[1]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20 »
make[1]: Rien à faire pour « all-am ».
make[1]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20 »
rabgye@ubuntumaya:~/alsa-utils-1.0.20$ sudo make install
Making install in include
make[1]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/include »
make[2]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/include »
make[2]: Rien à faire pour « install-exec-am ».
make[2]: Rien à faire pour « install-data-am ».
make[2]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/include »
make[1]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/include »
Making install in alsactl
make[1]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/alsactl »
Making install in init
make[2]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/alsactl/init »
make[3]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/alsactl/init »
make[3]: Rien à faire pour « install-exec-am ».
test -z "/usr/share/alsa/init" || mkdir -p -- "/usr/share/alsa/init"
 /usr/bin/install -c -m 644 '00main' '/usr/share/alsa/init/00main'
 /usr/bin/install -c -m 644 'default' '/usr/share/alsa/init/default'
 /usr/bin/install -c -m 644 'help' '/usr/share/alsa/init/help'
 /usr/bin/install -c -m 644 'info' '/usr/share/alsa/init/info'
 /usr/bin/install -c -m 644 'test' '/usr/share/alsa/init/test'
 /usr/bin/install -c -m 644 'hda' '/usr/share/alsa/init/hda'
make[3]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/alsactl/init »
make[2]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/alsactl/init »
make[2]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/alsactl »
make[3]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/alsactl »
test -z "/usr/sbin" || mkdir -p -- "/usr/sbin"
  /usr/bin/install -c 'alsactl' '/usr/sbin/alsactl'
test -z "/usr/share/man/man1" || mkdir -p -- "/usr/share/man/man1"
 /usr/bin/install -c -m 644 './alsactl.1' '/usr/share/man/man1/alsactl.1'
test -z "/usr/share/man/man7" || mkdir -p -- "/usr/share/man/man7"
 /usr/bin/install -c -m 644 './alsactl_init.7' '/usr/share/man/man7/alsactl_init.7'
make[3]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/alsactl »
make[2]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/alsactl »
make[1]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/alsactl »
Making install in utils
make[1]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/utils »
make[2]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/utils »
make[2]: Rien à faire pour « install-exec-am ».
make[2]: Rien à faire pour « install-data-am ».
make[2]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/utils »
make[1]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/utils »
Making install in m4
make[1]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/m4 »
make[2]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/m4 »
make[2]: Rien à faire pour « install-exec-am ».
make[2]: Rien à faire pour « install-data-am ».
make[2]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/m4 »
make[1]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/m4 »
Making install in po
make[1]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/po »
mkdir -p -- /usr/share
installing ja.gmo as /usr/share/locale/ja/LC_MESSAGES/alsa-utils.mo
if test "alsa-utils" = "gettext-tools"; then \
      mkdir -p -- /usr/share/gettext/po; \
      for file in Makefile.in.in remove-potcdate.sin quot.sed boldquot.sed [email]en@quot.header[/email] [email]en@boldquot.header[/email] insert-header.sin Rules-quot   Makevars.template; do \
        /usr/bin/install -c -m 644 ./$file \
                /usr/share/gettext/po/$file; \
      done; \
      for file in Makevars; do \
        rm -f /usr/share/gettext/po/$file; \
      done; \
    else \
      : ; \
    fi
make[1]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/po »
Making install in alsamixer
make[1]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/alsamixer »
make[2]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/alsamixer »
test -z "/usr/bin" || mkdir -p -- "/usr/bin"
  /usr/bin/install -c 'alsamixer' '/usr/bin/alsamixer'
test -z "/usr/share/man/man1" || mkdir -p -- "/usr/share/man/man1"
 /usr/bin/install -c -m 644 './alsamixer.1' '/usr/share/man/man1/alsamixer.1'
make[2]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/alsamixer »
make[1]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/alsamixer »
Making install in amixer
make[1]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/amixer »
make[2]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/amixer »
test -z "/usr/bin" || mkdir -p -- "/usr/bin"
  /usr/bin/install -c 'amixer' '/usr/bin/amixer'
test -z "/usr/share/man/man1" || mkdir -p -- "/usr/share/man/man1"
 /usr/bin/install -c -m 644 './amixer.1' '/usr/share/man/man1/amixer.1'
make[2]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/amixer »
make[1]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/amixer »
Making install in amidi
make[1]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/amidi »
make[2]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/amidi »
test -z "/usr/bin" || mkdir -p -- "/usr/bin"
  /usr/bin/install -c 'amidi' '/usr/bin/amidi'
test -z "/usr/share/man/man1" || mkdir -p -- "/usr/share/man/man1"
 /usr/bin/install -c -m 644 './amidi.1' '/usr/share/man/man1/amidi.1'
make[2]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/amidi »
make[1]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/amidi »
Making install in alsaconf
make[1]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/alsaconf »
Making install in po
make[2]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/alsaconf/po »
mkdir -p -- /usr/share
make[2]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/alsaconf/po »
make[2]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/alsaconf »
make[3]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/alsaconf »
test -z "/usr/sbin" || mkdir -p -- "/usr/sbin"
 /usr/bin/install -c 'alsaconf' '/usr/sbin/alsaconf'
 /usr/bin/install -c -m 644 alsaconf.8 /usr/share/man/man8/alsaconf.8
 /usr/bin/install -c -m 644 alsaconf.fr.8 /usr/share/man/fr/man8/alsaconf.8
make[3]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/alsaconf »
make[2]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/alsaconf »
make[1]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/alsaconf »
Making install in aplay
make[1]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/aplay »
make[2]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/aplay »
test -z "/usr/bin" || mkdir -p -- "/usr/bin"
  /usr/bin/install -c 'aplay' '/usr/bin/aplay'
make  install-exec-hook
make[3]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/aplay »
rm -f arecord
ln -s aplay arecord
rm -f /usr/bin/arecord
(cd /usr/bin && ln -s aplay arecord)
make[3]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/aplay »
test -z "/usr/share/man/man1" || mkdir -p -- "/usr/share/man/man1"
 /usr/bin/install -c -m 644 './aplay.1' '/usr/share/man/man1/aplay.1'
 /usr/bin/install -c -m 644 './arecord.1' '/usr/share/man/man1/arecord.1'
make  install-data-hook
make[3]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/aplay »
rm -f /usr/share/man/man1/arecord.1
(cd /usr/share/man/man1 && ln -s aplay.1 arecord.1)
make[3]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/aplay »
make[2]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/aplay »
make[1]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/aplay »
Making install in iecset
make[1]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/iecset »
make[2]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/iecset »
test -z "/usr/bin" || mkdir -p -- "/usr/bin"
  /usr/bin/install -c 'iecset' '/usr/bin/iecset'
test -z "/usr/share/man/man1" || mkdir -p -- "/usr/share/man/man1"
 /usr/bin/install -c -m 644 './iecset.1' '/usr/share/man/man1/iecset.1'
make[2]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/iecset »
make[1]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/iecset »
Making install in speaker-test
make[1]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/speaker-test »
Making install in samples
make[2]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/speaker-test/samples »
make[3]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/speaker-test/samples »
make[3]: Rien à faire pour « install-exec-am ».
test -z "/usr/share/alsa/speaker-test" || mkdir -p -- "/usr/share/alsa/speaker-test"
 /usr/bin/install -c -m 644 'sample_map.csv' '/usr/share/alsa/speaker-test/sample_map.csv'
test -z "/usr/share/sounds/alsa" || mkdir -p -- "/usr/share/sounds/alsa"
 /usr/bin/install -c -m 644 'Front_Left.wav' '/usr/share/sounds/alsa/Front_Left.wav'
 /usr/bin/install -c -m 644 'Rear_Center.wav' '/usr/share/sounds/alsa/Rear_Center.wav'
 /usr/bin/install -c -m 644 'Rear_Right.wav' '/usr/share/sounds/alsa/Rear_Right.wav'
 /usr/bin/install -c -m 644 'Side_Right.wav' '/usr/share/sounds/alsa/Side_Right.wav'
 /usr/bin/install -c -m 644 'Front_Center.wav' '/usr/share/sounds/alsa/Front_Center.wav'
 /usr/bin/install -c -m 644 'Front_Right.wav' '/usr/share/sounds/alsa/Front_Right.wav'
 /usr/bin/install -c -m 644 'Noise.wav' '/usr/share/sounds/alsa/Noise.wav'
 /usr/bin/install -c -m 644 'Rear_Left.wav' '/usr/share/sounds/alsa/Rear_Left.wav'
 /usr/bin/install -c -m 644 'Side_Left.wav' '/usr/share/sounds/alsa/Side_Left.wav'
make[3]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/speaker-test/samples »
make[2]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/speaker-test/samples »
make[2]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/speaker-test »
make[3]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/speaker-test »
test -z "/usr/bin" || mkdir -p -- "/usr/bin"
  /usr/bin/install -c 'speaker-test' '/usr/bin/speaker-test'
test -z "/usr/share/man/man1" || mkdir -p -- "/usr/share/man/man1"
 /usr/bin/install -c -m 644 './speaker-test.1' '/usr/share/man/man1/speaker-test.1'
make[3]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/speaker-test »
make[2]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/speaker-test »
make[1]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/speaker-test »
Making install in seq
make[1]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/seq »
Making install in aconnect
make[2]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/seq/aconnect »
make[3]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/seq/aconnect »
test -z "/usr/bin" || mkdir -p -- "/usr/bin"
  /usr/bin/install -c 'aconnect' '/usr/bin/aconnect'
test -z "/usr/share/man/man1" || mkdir -p -- "/usr/share/man/man1"
 /usr/bin/install -c -m 644 './aconnect.1' '/usr/share/man/man1/aconnect.1'
make[3]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/seq/aconnect »
make[2]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/seq/aconnect »
Making install in aplaymidi
make[2]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/seq/aplaymidi »
make[3]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/seq/aplaymidi »
test -z "/usr/bin" || mkdir -p -- "/usr/bin"
  /usr/bin/install -c 'aplaymidi' '/usr/bin/aplaymidi'
  /usr/bin/install -c 'arecordmidi' '/usr/bin/arecordmidi'
test -z "/usr/share/man/man1" || mkdir -p -- "/usr/share/man/man1"
 /usr/bin/install -c -m 644 './aplaymidi.1' '/usr/share/man/man1/aplaymidi.1'
 /usr/bin/install -c -m 644 './arecordmidi.1' '/usr/share/man/man1/arecordmidi.1'
make[3]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/seq/aplaymidi »
make[2]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/seq/aplaymidi »
Making install in aseqdump
make[2]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/seq/aseqdump »
make[3]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/seq/aseqdump »
test -z "/usr/bin" || mkdir -p -- "/usr/bin"
  /usr/bin/install -c 'aseqdump' '/usr/bin/aseqdump'
test -z "/usr/share/man/man1" || mkdir -p -- "/usr/share/man/man1"
 /usr/bin/install -c -m 644 './aseqdump.1' '/usr/share/man/man1/aseqdump.1'
make[3]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/seq/aseqdump »
make[2]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/seq/aseqdump »
Making install in aseqnet
make[2]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/seq/aseqnet »
make[3]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/seq/aseqnet »
test -z "/usr/bin" || mkdir -p -- "/usr/bin"
  /usr/bin/install -c 'aseqnet' '/usr/bin/aseqnet'
test -z "/usr/share/man/man1" || mkdir -p -- "/usr/share/man/man1"
 /usr/bin/install -c -m 644 './aseqnet.1' '/usr/share/man/man1/aseqnet.1'
make[3]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/seq/aseqnet »
make[2]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/seq/aseqnet »
make[2]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/seq »
make[3]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/seq »
make[3]: Rien à faire pour « install-exec-am ».
make[3]: Rien à faire pour « install-data-am ».
make[3]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/seq »
make[2]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/seq »
make[1]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/seq »
make[1]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20 »
make[2]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20 »
make[2]: Rien à faire pour « install-exec-am ».
make[2]: Rien à faire pour « install-data-am ».
make[2]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20 »
make[1]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20 »
rabgye@ubuntumaya:~/alsa-utils-1.0.20$ rm -f ~/alsa-driver*
rm: ne peut enlever `/home/rabgye/alsa-driver-1.0.20': est un dossier
rabgye@ubuntumaya:~/alsa-utils-1.0.20$ rm -f ~/alsa-lib*
rm: ne peut enlever `/home/rabgye/alsa-lib-1.0.20': est un dossier
rabgye@ubuntumaya:~/alsa-utils-1.0.20$ rm -f ~/alsa-utils*
rm: ne peut enlever `/home/rabgye/alsa-utils-1.0.20': est un dossier
rabgye@ubuntumaya:~/alsa-utils-1.0.20$ 


































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































make[1]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/amixer »
if gcc -DHAVE_CONFIG_H -I. -I. -I../include -I../include    -g -O2 -MT amixer.o -MD -MP -MF ".deps/amixer.Tpo" -c -o amixer.o amixer.c; \
    then mv -f ".deps/amixer.Tpo" ".deps/amixer.Po"; else rm -f ".deps/amixer.Tpo"; exit 1; fi
amixer.c: In function ‘get_integer’:
amixer.c:244: attention : ignoring return value of ‘strtol’, declared with attribute warn_unused_result
amixer.c: In function ‘get_integer64’:
amixer.c:272: attention : ignoring return value of ‘strtol’, declared with attribute warn_unused_result
amixer.c: In function ‘set_volume_simple’:
amixer.c:358: attention : ignoring return value of ‘strtol’, declared with attribute warn_unused_result
gcc  -g -O2   -o amixer  amixer.o -lm -lasound -lm -ldl -lpthread
make[1]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/amixer »
Making all in amidi
make[1]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/amidi »
if gcc -DHAVE_CONFIG_H -I. -I. -I../include -I../include    -g -O2 -MT amidi.o -MD -MP -MF ".deps/amidi.Tpo" -c -o amidi.o amidi.c; \
    then mv -f ".deps/amidi.Tpo" ".deps/amidi.Po"; else rm -f ".deps/amidi.Tpo"; exit 1; fi
amidi.c: In function ‘main’:
amidi.c:658: attention : ignoring return value of ‘write’, declared with attribute warn_unused_result
gcc  -g -O2   -o amidi  amidi.o  -lasound -lm -ldl -lpthread
make[1]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/amidi »
Making all in alsaconf
make[1]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/alsaconf »
Making all in po
make[2]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/alsaconf/po »
35 messages traduits, 1 message non traduit.
34 messages traduits, 1 traduction approximative, 1 message non traduit.
make[2]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/alsaconf/po »
make[2]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/alsaconf »
make[2]: Rien à faire pour « all-am ».
make[2]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/alsaconf »
make[1]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/alsaconf »
Making all in aplay
make[1]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/aplay »
if gcc -DHAVE_CONFIG_H -I. -I. -I../include -I../include    -g -O2 -MT aplay.o -MD -MP -MF ".deps/aplay.Tpo" -c -o aplay.o aplay.c; \
    then mv -f ".deps/aplay.Tpo" ".deps/aplay.Po"; else rm -f ".deps/aplay.Tpo"; exit 1; fi
aplay.c: In function ‘end_voc’:
aplay.c:2158: attention : ignoring return value of ‘write’, declared with attribute warn_unused_result
aplay.c: In function ‘end_wave’:
aplay.c:2178: attention : ignoring return value of ‘write’, declared with attribute warn_unused_result
aplay.c:2180: attention : ignoring return value of ‘write’, declared with attribute warn_unused_result
aplay.c: In function ‘end_au’:
aplay.c:2193: attention : ignoring return value of ‘write’, declared with attribute warn_unused_result
gcc  -g -O2   -o aplay  aplay.o  -lrt -lasound -lm -ldl -lpthread
make[1]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/aplay »
Making all in iecset
make[1]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/iecset »
if gcc -DHAVE_CONFIG_H -I. -I. -I../include -I../include    -g -O2 -MT iecset.o -MD -MP -MF ".deps/iecset.Tpo" -c -o iecset.o iecset.c; \
    then mv -f ".deps/iecset.Tpo" ".deps/iecset.Po"; else rm -f ".deps/iecset.Tpo"; exit 1; fi
if gcc -DHAVE_CONFIG_H -I. -I. -I../include -I../include    -g -O2 -MT iecbits.o -MD -MP -MF ".deps/iecbits.Tpo" -c -o iecbits.o iecbits.c; \
    then mv -f ".deps/iecbits.Tpo" ".deps/iecbits.Po"; else rm -f ".deps/iecbits.Tpo"; exit 1; fi
gcc  -g -O2   -o iecset  iecset.o iecbits.o -lm -lasound -lm -ldl -lpthread
make[1]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/iecset »
Making all in speaker-test
make[1]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/speaker-test »
Making all in samples
make[2]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/speaker-test/samples »
make[2]: Rien à faire pour « all ».
make[2]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/speaker-test/samples »
make[2]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/speaker-test »
if gcc -DHAVE_CONFIG_H -I. -I. -I../include -I../include    -g -O2 -MT speaker-test.o -MD -MP -MF ".deps/speaker-test.Tpo" -c -o speaker-test.o speaker-test.c; \
    then mv -f ".deps/speaker-test.Tpo" ".deps/speaker-test.Po"; else rm -f ".deps/speaker-test.Tpo"; exit 1; fi
if gcc -DHAVE_CONFIG_H -I. -I. -I../include -I../include    -g -O2 -MT pink.o -MD -MP -MF ".deps/pink.Tpo" -c -o pink.o pink.c; \
    then mv -f ".deps/pink.Tpo" ".deps/pink.Po"; else rm -f ".deps/pink.Tpo"; exit 1; fi
gcc  -g -O2   -o speaker-test  speaker-test.o pink.o  -lm -lasound -lm -ldl -lpthread
make[2]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/speaker-test »
make[1]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/speaker-test »
Making all in seq
make[1]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/seq »
Making all in aconnect
make[2]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/seq/aconnect »
if gcc -DHAVE_CONFIG_H -I. -I. -I../../include -I../../include    -g -O2 -MT aconnect.o -MD -MP -MF ".deps/aconnect.Tpo" -c -o aconnect.o aconnect.c; \
    then mv -f ".deps/aconnect.Tpo" ".deps/aconnect.Po"; else rm -f ".deps/aconnect.Tpo"; exit 1; fi
gcc  -g -O2   -o aconnect  aconnect.o  -lasound -lm -ldl -lpthread
make[2]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/seq/aconnect »
Making all in aplaymidi
make[2]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/seq/aplaymidi »
if gcc -DHAVE_CONFIG_H -I. -I. -I../../include -I../../include    -g -O2 -MT aplaymidi.o -MD -MP -MF ".deps/aplaymidi.Tpo" -c -o aplaymidi.o aplaymidi.c; \
    then mv -f ".deps/aplaymidi.Tpo" ".deps/aplaymidi.Po"; else rm -f ".deps/aplaymidi.Tpo"; exit 1; fi
gcc  -g -O2   -o aplaymidi  aplaymidi.o  -lasound -lm -ldl -lpthread
if gcc -DHAVE_CONFIG_H -I. -I. -I../../include -I../../include    -g -O2 -MT arecordmidi.o -MD -MP -MF ".deps/arecordmidi.Tpo" -c -o arecordmidi.o arecordmidi.c; \
    then mv -f ".deps/arecordmidi.Tpo" ".deps/arecordmidi.Po"; else rm -f ".deps/arecordmidi.Tpo"; exit 1; fi
gcc  -g -O2   -o arecordmidi  arecordmidi.o  -lasound -lm -ldl -lpthread
make[2]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/seq/aplaymidi »
Making all in aseqdump
make[2]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/seq/aseqdump »
if gcc -DHAVE_CONFIG_H -I. -I. -I../../include -I../../include    -g -O2 -MT aseqdump.o -MD -MP -MF ".deps/aseqdump.Tpo" -c -o aseqdump.o aseqdump.c; \
    then mv -f ".deps/aseqdump.Tpo" ".deps/aseqdump.Po"; else rm -f ".deps/aseqdump.Tpo"; exit 1; fi
gcc  -g -O2   -o aseqdump  aseqdump.o  -lasound -lm -ldl -lpthread
make[2]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/seq/aseqdump »
Making all in aseqnet
make[2]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/seq/aseqnet »
if gcc -DHAVE_CONFIG_H -I. -I. -I../../include -I../../include    -g -O2 -MT aseqnet.o -MD -MP -MF ".deps/aseqnet.Tpo" -c -o aseqnet.o aseqnet.c; \
    then mv -f ".deps/aseqnet.Tpo" ".deps/aseqnet.Po"; else rm -f ".deps/aseqnet.Tpo"; exit 1; fi
aseqnet.c: In function ‘flush_writebuf’:
aseqnet.c:495: attention : ignoring return value of ‘write’, declared with attribute warn_unused_result
gcc  -g -O2   -o aseqnet  aseqnet.o  -lasound -lm -ldl -lpthread
make[2]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/seq/aseqnet »
make[2]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/seq »
make[2]: Rien à faire pour « all-am ».
make[2]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/seq »
make[1]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/seq »
make[1]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20 »
make[1]: Rien à faire pour « all-am ».
make[1]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20 »
rabgye@ubuntumaya:~/alsa-utils-1.0.20$ sudo make
Making all in include
make[1]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/include »
make  all-am
make[2]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/include »
make[2]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/include »
make[1]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/include »
Making all in alsactl
make[1]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/alsactl »
Making all in init
make[2]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/alsactl/init »
make[2]: Rien à faire pour « all ».
make[2]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/alsactl/init »
make[2]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/alsactl »
make[2]: Rien à faire pour « all-am ».
make[2]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/alsactl »
make[1]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/alsactl »
Making all in utils
make[1]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/utils »
make[1]: Rien à faire pour « all ».
make[1]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/utils »
Making all in m4
make[1]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/m4 »
make[1]: Rien à faire pour « all ».
make[1]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/m4 »
Making all in po
make[1]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/po »
make[1]: Rien à faire pour « all ».
make[1]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/po »
Making all in alsamixer
make[1]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/alsamixer »
make[1]: Rien à faire pour « all ».
make[1]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/alsamixer »
Making all in amixer
make[1]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/amixer »
make[1]: Rien à faire pour « all ».
make[1]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/amixer »
Making all in amidi
make[1]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/amidi »
make[1]: Rien à faire pour « all ».
make[1]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/amidi »
Making all in alsaconf
make[1]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/alsaconf »
Making all in po
make[2]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/alsaconf/po »
make[2]: Rien à faire pour « all ».
make[2]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/alsaconf/po »
make[2]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/alsaconf »
make[2]: Rien à faire pour « all-am ».
make[2]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/alsaconf »
make[1]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/alsaconf »
Making all in aplay
make[1]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/aplay »
make[1]: Rien à faire pour « all ».
make[1]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/aplay »
Making all in iecset
make[1]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/iecset »
make[1]: Rien à faire pour « all ».
make[1]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/iecset »
Making all in speaker-test
make[1]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/speaker-test »
Making all in samples
make[2]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/speaker-test/samples »
make[2]: Rien à faire pour « all ».
make[2]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/speaker-test/samples »
make[2]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/speaker-test »
make[2]: Rien à faire pour « all-am ».
make[2]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/speaker-test »
make[1]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/speaker-test »
Making all in seq
make[1]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/seq »
Making all in aconnect
make[2]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/seq/aconnect »
make[2]: Rien à faire pour « all ».
make[2]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/seq/aconnect »
Making all in aplaymidi
make[2]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/seq/aplaymidi »
make[2]: Rien à faire pour « all ».
make[2]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/seq/aplaymidi »
Making all in aseqdump
make[2]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/seq/aseqdump »
make[2]: Rien à faire pour « all ».
make[2]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/seq/aseqdump »
Making all in aseqnet
make[2]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/seq/aseqnet »
make[2]: Rien à faire pour « all ».
make[2]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/seq/aseqnet »
make[2]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/seq »
make[2]: Rien à faire pour « all-am ».
make[2]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/seq »
make[1]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/seq »
make[1]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20 »
make[1]: Rien à faire pour « all-am ».
make[1]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20 »
rabgye@ubuntumaya:~/alsa-utils-1.0.20$ sudo make install
Making install in include
make[1]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/include »
make[2]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/include »
make[2]: Rien à faire pour « install-exec-am ».
make[2]: Rien à faire pour « install-data-am ».
make[2]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/include »
make[1]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/include »
Making install in alsactl
make[1]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/alsactl »
Making install in init
make[2]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/alsactl/init »
make[3]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/alsactl/init »
make[3]: Rien à faire pour « install-exec-am ».
test -z "/usr/share/alsa/init" || mkdir -p -- "/usr/share/alsa/init"
 /usr/bin/install -c -m 644 '00main' '/usr/share/alsa/init/00main'
 /usr/bin/install -c -m 644 'default' '/usr/share/alsa/init/default'
 /usr/bin/install -c -m 644 'help' '/usr/share/alsa/init/help'
 /usr/bin/install -c -m 644 'info' '/usr/share/alsa/init/info'
 /usr/bin/install -c -m 644 'test' '/usr/share/alsa/init/test'
 /usr/bin/install -c -m 644 'hda' '/usr/share/alsa/init/hda'
make[3]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/alsactl/init »
make[2]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/alsactl/init »
make[2]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/alsactl »
make[3]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/alsactl »
test -z "/usr/sbin" || mkdir -p -- "/usr/sbin"
  /usr/bin/install -c 'alsactl' '/usr/sbin/alsactl'
test -z "/usr/share/man/man1" || mkdir -p -- "/usr/share/man/man1"
 /usr/bin/install -c -m 644 './alsactl.1' '/usr/share/man/man1/alsactl.1'
test -z "/usr/share/man/man7" || mkdir -p -- "/usr/share/man/man7"
 /usr/bin/install -c -m 644 './alsactl_init.7' '/usr/share/man/man7/alsactl_init.7'
make[3]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/alsactl »
make[2]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/alsactl »
make[1]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/alsactl »
Making install in utils
make[1]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/utils »
make[2]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/utils »
make[2]: Rien à faire pour « install-exec-am ».
make[2]: Rien à faire pour « install-data-am ».
make[2]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/utils »
make[1]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/utils »
Making install in m4
make[1]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/m4 »
make[2]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/m4 »
make[2]: Rien à faire pour « install-exec-am ».
make[2]: Rien à faire pour « install-data-am ».
make[2]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/m4 »
make[1]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/m4 »
Making install in po
make[1]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/po »
mkdir -p -- /usr/share
installing ja.gmo as /usr/share/locale/ja/LC_MESSAGES/alsa-utils.mo
if test "alsa-utils" = "gettext-tools"; then \
      mkdir -p -- /usr/share/gettext/po; \
      for file in Makefile.in.in remove-potcdate.sin quot.sed boldquot.sed [email]en@quot.header[/email] [email]en@boldquot.header[/email] insert-header.sin Rules-quot   Makevars.template; do \
        /usr/bin/install -c -m 644 ./$file \
                /usr/share/gettext/po/$file; \
      done; \
      for file in Makevars; do \
        rm -f /usr/share/gettext/po/$file; \
      done; \
    else \
      : ; \
    fi
make[1]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/po »
Making install in alsamixer
make[1]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/alsamixer »
make[2]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/alsamixer »
test -z "/usr/bin" || mkdir -p -- "/usr/bin"
  /usr/bin/install -c 'alsamixer' '/usr/bin/alsamixer'
test -z "/usr/share/man/man1" || mkdir -p -- "/usr/share/man/man1"
 /usr/bin/install -c -m 644 './alsamixer.1' '/usr/share/man/man1/alsamixer.1'
make[2]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/alsamixer »
make[1]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/alsamixer »
Making install in amixer
make[1]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/amixer »
make[2]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/amixer »
test -z "/usr/bin" || mkdir -p -- "/usr/bin"
  /usr/bin/install -c 'amixer' '/usr/bin/amixer'
test -z "/usr/share/man/man1" || mkdir -p -- "/usr/share/man/man1"
 /usr/bin/install -c -m 644 './amixer.1' '/usr/share/man/man1/amixer.1'
make[2]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/amixer »
make[1]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/amixer »
Making install in amidi
make[1]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/amidi »
make[2]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/amidi »
test -z "/usr/bin" || mkdir -p -- "/usr/bin"
  /usr/bin/install -c 'amidi' '/usr/bin/amidi'
test -z "/usr/share/man/man1" || mkdir -p -- "/usr/share/man/man1"
 /usr/bin/install -c -m 644 './amidi.1' '/usr/share/man/man1/amidi.1'
make[2]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/amidi »
make[1]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/amidi »
Making install in alsaconf
make[1]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/alsaconf »
Making install in po
make[2]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/alsaconf/po »
mkdir -p -- /usr/share
make[2]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/alsaconf/po »
make[2]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/alsaconf »
make[3]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/alsaconf »
test -z "/usr/sbin" || mkdir -p -- "/usr/sbin"
 /usr/bin/install -c 'alsaconf' '/usr/sbin/alsaconf'
 /usr/bin/install -c -m 644 alsaconf.8 /usr/share/man/man8/alsaconf.8
 /usr/bin/install -c -m 644 alsaconf.fr.8 /usr/share/man/fr/man8/alsaconf.8
make[3]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/alsaconf »
make[2]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/alsaconf »
make[1]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/alsaconf »
Making install in aplay
make[1]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/aplay »
make[2]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/aplay »
test -z "/usr/bin" || mkdir -p -- "/usr/bin"
  /usr/bin/install -c 'aplay' '/usr/bin/aplay'
make  install-exec-hook
make[3]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/aplay »
rm -f arecord
ln -s aplay arecord
rm -f /usr/bin/arecord
(cd /usr/bin && ln -s aplay arecord)
make[3]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/aplay »
test -z "/usr/share/man/man1" || mkdir -p -- "/usr/share/man/man1"
 /usr/bin/install -c -m 644 './aplay.1' '/usr/share/man/man1/aplay.1'
 /usr/bin/install -c -m 644 './arecord.1' '/usr/share/man/man1/arecord.1'
make  install-data-hook
make[3]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/aplay »
rm -f /usr/share/man/man1/arecord.1
(cd /usr/share/man/man1 && ln -s aplay.1 arecord.1)
make[3]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/aplay »
make[2]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/aplay »
make[1]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/aplay »
Making install in iecset
make[1]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/iecset »
make[2]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/iecset »
test -z "/usr/bin" || mkdir -p -- "/usr/bin"
  /usr/bin/install -c 'iecset' '/usr/bin/iecset'
test -z "/usr/share/man/man1" || mkdir -p -- "/usr/share/man/man1"
 /usr/bin/install -c -m 644 './iecset.1' '/usr/share/man/man1/iecset.1'
make[2]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/iecset »
make[1]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/iecset »
Making install in speaker-test
make[1]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/speaker-test »
Making install in samples
make[2]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/speaker-test/samples »
make[3]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/speaker-test/samples »
make[3]: Rien à faire pour « install-exec-am ».
test -z "/usr/share/alsa/speaker-test" || mkdir -p -- "/usr/share/alsa/speaker-test"
 /usr/bin/install -c -m 644 'sample_map.csv' '/usr/share/alsa/speaker-test/sample_map.csv'
test -z "/usr/share/sounds/alsa" || mkdir -p -- "/usr/share/sounds/alsa"
 /usr/bin/install -c -m 644 'Front_Left.wav' '/usr/share/sounds/alsa/Front_Left.wav'
 /usr/bin/install -c -m 644 'Rear_Center.wav' '/usr/share/sounds/alsa/Rear_Center.wav'
 /usr/bin/install -c -m 644 'Rear_Right.wav' '/usr/share/sounds/alsa/Rear_Right.wav'
 /usr/bin/install -c -m 644 'Side_Right.wav' '/usr/share/sounds/alsa/Side_Right.wav'
 /usr/bin/install -c -m 644 'Front_Center.wav' '/usr/share/sounds/alsa/Front_Center.wav'
 /usr/bin/install -c -m 644 'Front_Right.wav' '/usr/share/sounds/alsa/Front_Right.wav'
 /usr/bin/install -c -m 644 'Noise.wav' '/usr/share/sounds/alsa/Noise.wav'
 /usr/bin/install -c -m 644 'Rear_Left.wav' '/usr/share/sounds/alsa/Rear_Left.wav'
 /usr/bin/install -c -m 644 'Side_Left.wav' '/usr/share/sounds/alsa/Side_Left.wav'
make[3]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/speaker-test/samples »
make[2]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/speaker-test/samples »
make[2]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/speaker-test »
make[3]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/speaker-test »
test -z "/usr/bin" || mkdir -p -- "/usr/bin"
  /usr/bin/install -c 'speaker-test' '/usr/bin/speaker-test'
test -z "/usr/share/man/man1" || mkdir -p -- "/usr/share/man/man1"
 /usr/bin/install -c -m 644 './speaker-test.1' '/usr/share/man/man1/speaker-test.1'
make[3]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/speaker-test »
make[2]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/speaker-test »
make[1]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/speaker-test »
Making install in seq
make[1]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/seq »
Making install in aconnect
make[2]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/seq/aconnect »
make[3]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/seq/aconnect »
test -z "/usr/bin" || mkdir -p -- "/usr/bin"
  /usr/bin/install -c 'aconnect' '/usr/bin/aconnect'
test -z "/usr/share/man/man1" || mkdir -p -- "/usr/share/man/man1"
 /usr/bin/install -c -m 644 './aconnect.1' '/usr/share/man/man1/aconnect.1'
make[3]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/seq/aconnect »
make[2]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/seq/aconnect »
Making install in aplaymidi
make[2]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/seq/aplaymidi »
make[3]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/seq/aplaymidi »
test -z "/usr/bin" || mkdir -p -- "/usr/bin"
  /usr/bin/install -c 'aplaymidi' '/usr/bin/aplaymidi'
  /usr/bin/install -c 'arecordmidi' '/usr/bin/arecordmidi'
test -z "/usr/share/man/man1" || mkdir -p -- "/usr/share/man/man1"
 /usr/bin/install -c -m 644 './aplaymidi.1' '/usr/share/man/man1/aplaymidi.1'
 /usr/bin/install -c -m 644 './arecordmidi.1' '/usr/share/man/man1/arecordmidi.1'
make[3]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/seq/aplaymidi »
make[2]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/seq/aplaymidi »
Making install in aseqdump
make[2]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/seq/aseqdump »
make[3]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/seq/aseqdump »
test -z "/usr/bin" || mkdir -p -- "/usr/bin"
  /usr/bin/install -c 'aseqdump' '/usr/bin/aseqdump'
test -z "/usr/share/man/man1" || mkdir -p -- "/usr/share/man/man1"
 /usr/bin/install -c -m 644 './aseqdump.1' '/usr/share/man/man1/aseqdump.1'
make[3]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/seq/aseqdump »
make[2]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/seq/aseqdump »
Making install in aseqnet
make[2]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/seq/aseqnet »
make[3]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/seq/aseqnet »
test -z "/usr/bin" || mkdir -p -- "/usr/bin"
  /usr/bin/install -c 'aseqnet' '/usr/bin/aseqnet'
test -z "/usr/share/man/man1" || mkdir -p -- "/usr/share/man/man1"
 /usr/bin/install -c -m 644 './aseqnet.1' '/usr/share/man/man1/aseqnet.1'
make[3]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/seq/aseqnet »
make[2]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/seq/aseqnet »
make[2]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/seq »
make[3]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/seq »
make[3]: Rien à faire pour « install-exec-am ».
make[3]: Rien à faire pour « install-data-am ».
make[3]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/seq »
make[2]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/seq »
make[1]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/seq »
make[1]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20 »
make[2]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20 »
make[2]: Rien à faire pour « install-exec-am ».
make[2]: Rien à faire pour « install-data-am ».
make[2]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20 »
make[1]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20 »
rabgye@ubuntumaya:~/alsa-utils-1.0.20$ rm -f ~/alsa-driver*
rm: ne peut enlever `/home/rabgye/alsa-driver-1.0.20': est un dossier
rabgye@ubuntumaya:~/alsa-utils-1.0.20$ rm -f ~/alsa-lib*
rm: ne peut enlever `/home/rabgye/alsa-lib-1.0.20': est un dossier
rabgye@ubuntumaya:~/alsa-utils-1.0.20$ rm -f ~/alsa-utils*
rm: ne peut enlever `/home/rabgye/alsa-utils-1.0.20': est un dossier
rabgye@ubuntumaya:~/alsa-utils-1.0.20$ 


































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































make[1]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/amixer »
if gcc -DHAVE_CONFIG_H -I. -I. -I../include -I../include    -g -O2 -MT amixer.o -MD -MP -MF ".deps/amixer.Tpo" -c -o amixer.o amixer.c; \
    then mv -f ".deps/amixer.Tpo" ".deps/amixer.Po"; else rm -f ".deps/amixer.Tpo"; exit 1; fi
amixer.c: In function ‘get_integer’:
amixer.c:244: attention : ignoring return value of ‘strtol’, declared with attribute warn_unused_result
amixer.c: In function ‘get_integer64’:
amixer.c:272: attention : ignoring return value of ‘strtol’, declared with attribute warn_unused_result
amixer.c: In function ‘set_volume_simple’:
amixer.c:358: attention : ignoring return value of ‘strtol’, declared with attribute warn_unused_result
gcc  -g -O2   -o amixer  amixer.o -lm -lasound -lm -ldl -lpthread
make[1]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/amixer »
Making all in amidi
make[1]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/amidi »
if gcc -DHAVE_CONFIG_H -I. -I. -I../include -I../include    -g -O2 -MT amidi.o -MD -MP -MF ".deps/amidi.Tpo" -c -o amidi.o amidi.c; \
    then mv -f ".deps/amidi.Tpo" ".deps/amidi.Po"; else rm -f ".deps/amidi.Tpo"; exit 1; fi
amidi.c: In function ‘main’:
amidi.c:658: attention : ignoring return value of ‘write’, declared with attribute warn_unused_result
gcc  -g -O2   -o amidi  amidi.o  -lasound -lm -ldl -lpthread
make[1]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/amidi »
Making all in alsaconf
make[1]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/alsaconf »
Making all in po
make[2]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/alsaconf/po »
35 messages traduits, 1 message non traduit.
34 messages traduits, 1 traduction approximative, 1 message non traduit.
make[2]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/alsaconf/po »
make[2]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/alsaconf »
make[2]: Rien à faire pour « all-am ».
make[2]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/alsaconf »
make[1]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/alsaconf »
Making all in aplay
make[1]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/aplay »
if gcc -DHAVE_CONFIG_H -I. -I. -I../include -I../include    -g -O2 -MT aplay.o -MD -MP -MF ".deps/aplay.Tpo" -c -o aplay.o aplay.c; \
    then mv -f ".deps/aplay.Tpo" ".deps/aplay.Po"; else rm -f ".deps/aplay.Tpo"; exit 1; fi
aplay.c: In function ‘end_voc’:
aplay.c:2158: attention : ignoring return value of ‘write’, declared with attribute warn_unused_result
aplay.c: In function ‘end_wave’:
aplay.c:2178: attention : ignoring return value of ‘write’, declared with attribute warn_unused_result
aplay.c:2180: attention : ignoring return value of ‘write’, declared with attribute warn_unused_result
aplay.c: In function ‘end_au’:
aplay.c:2193: attention : ignoring return value of ‘write’, declared with attribute warn_unused_result
gcc  -g -O2   -o aplay  aplay.o  -lrt -lasound -lm -ldl -lpthread
make[1]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/aplay »
Making all in iecset
make[1]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/iecset »
if gcc -DHAVE_CONFIG_H -I. -I. -I../include -I../include    -g -O2 -MT iecset.o -MD -MP -MF ".deps/iecset.Tpo" -c -o iecset.o iecset.c; \
    then mv -f ".deps/iecset.Tpo" ".deps/iecset.Po"; else rm -f ".deps/iecset.Tpo"; exit 1; fi
if gcc -DHAVE_CONFIG_H -I. -I. -I../include -I../include    -g -O2 -MT iecbits.o -MD -MP -MF ".deps/iecbits.Tpo" -c -o iecbits.o iecbits.c; \
    then mv -f ".deps/iecbits.Tpo" ".deps/iecbits.Po"; else rm -f ".deps/iecbits.Tpo"; exit 1; fi
gcc  -g -O2   -o iecset  iecset.o iecbits.o -lm -lasound -lm -ldl -lpthread
make[1]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/iecset »
Making all in speaker-test
make[1]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/speaker-test »
Making all in samples
make[2]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/speaker-test/samples »
make[2]: Rien à faire pour « all ».
make[2]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/speaker-test/samples »
make[2]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/speaker-test »
if gcc -DHAVE_CONFIG_H -I. -I. -I../include -I../include    -g -O2 -MT speaker-test.o -MD -MP -MF ".deps/speaker-test.Tpo" -c -o speaker-test.o speaker-test.c; \
    then mv -f ".deps/speaker-test.Tpo" ".deps/speaker-test.Po"; else rm -f ".deps/speaker-test.Tpo"; exit 1; fi
if gcc -DHAVE_CONFIG_H -I. -I. -I../include -I../include    -g -O2 -MT pink.o -MD -MP -MF ".deps/pink.Tpo" -c -o pink.o pink.c; \
    then mv -f ".deps/pink.Tpo" ".deps/pink.Po"; else rm -f ".deps/pink.Tpo"; exit 1; fi
gcc  -g -O2   -o speaker-test  speaker-test.o pink.o  -lm -lasound -lm -ldl -lpthread
make[2]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/speaker-test »
make[1]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/speaker-test »
Making all in seq
make[1]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/seq »
Making all in aconnect
make[2]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/seq/aconnect »
if gcc -DHAVE_CONFIG_H -I. -I. -I../../include -I../../include    -g -O2 -MT aconnect.o -MD -MP -MF ".deps/aconnect.Tpo" -c -o aconnect.o aconnect.c; \
    then mv -f ".deps/aconnect.Tpo" ".deps/aconnect.Po"; else rm -f ".deps/aconnect.Tpo"; exit 1; fi
gcc  -g -O2   -o aconnect  aconnect.o  -lasound -lm -ldl -lpthread
make[2]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/seq/aconnect »
Making all in aplaymidi
make[2]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/seq/aplaymidi »
if gcc -DHAVE_CONFIG_H -I. -I. -I../../include -I../../include    -g -O2 -MT aplaymidi.o -MD -MP -MF ".deps/aplaymidi.Tpo" -c -o aplaymidi.o aplaymidi.c; \
    then mv -f ".deps/aplaymidi.Tpo" ".deps/aplaymidi.Po"; else rm -f ".deps/aplaymidi.Tpo"; exit 1; fi
gcc  -g -O2   -o aplaymidi  aplaymidi.o  -lasound -lm -ldl -lpthread
if gcc -DHAVE_CONFIG_H -I. -I. -I../../include -I../../include    -g -O2 -MT arecordmidi.o -MD -MP -MF ".deps/arecordmidi.Tpo" -c -o arecordmidi.o arecordmidi.c; \
    then mv -f ".deps/arecordmidi.Tpo" ".deps/arecordmidi.Po"; else rm -f ".deps/arecordmidi.Tpo"; exit 1; fi
gcc  -g -O2   -o arecordmidi  arecordmidi.o  -lasound -lm -ldl -lpthread
make[2]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/seq/aplaymidi »
Making all in aseqdump
make[2]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/seq/aseqdump »
if gcc -DHAVE_CONFIG_H -I. -I. -I../../include -I../../include    -g -O2 -MT aseqdump.o -MD -MP -MF ".deps/aseqdump.Tpo" -c -o aseqdump.o aseqdump.c; \
    then mv -f ".deps/aseqdump.Tpo" ".deps/aseqdump.Po"; else rm -f ".deps/aseqdump.Tpo"; exit 1; fi
gcc  -g -O2   -o aseqdump  aseqdump.o  -lasound -lm -ldl -lpthread
make[2]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/seq/aseqdump »
Making all in aseqnet
make[2]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/seq/aseqnet »
if gcc -DHAVE_CONFIG_H -I. -I. -I../../include -I../../include    -g -O2 -MT aseqnet.o -MD -MP -MF ".deps/aseqnet.Tpo" -c -o aseqnet.o aseqnet.c; \
    then mv -f ".deps/aseqnet.Tpo" ".deps/aseqnet.Po"; else rm -f ".deps/aseqnet.Tpo"; exit 1; fi
aseqnet.c: In function ‘flush_writebuf’:
aseqnet.c:495: attention : ignoring return value of ‘write’, declared with attribute warn_unused_result
gcc  -g -O2   -o aseqnet  aseqnet.o  -lasound -lm -ldl -lpthread
make[2]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/seq/aseqnet »
make[2]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/seq »
make[2]: Rien à faire pour « all-am ».
make[2]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/seq »
make[1]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/seq »
make[1]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20 »
make[1]: Rien à faire pour « all-am ».
make[1]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20 »
rabgye@ubuntumaya:~/alsa-utils-1.0.20$ sudo make
Making all in include
make[1]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/include »
make  all-am
make[2]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/include »
make[2]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/include »
make[1]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/include »
Making all in alsactl
make[1]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/alsactl »
Making all in init
make[2]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/alsactl/init »
make[2]: Rien à faire pour « all ».
make[2]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/alsactl/init »
make[2]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/alsactl »
make[2]: Rien à faire pour « all-am ».
make[2]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/alsactl »
make[1]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/alsactl »
Making all in utils
make[1]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/utils »
make[1]: Rien à faire pour « all ».
make[1]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/utils »
Making all in m4
make[1]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/m4 »
make[1]: Rien à faire pour « all ».
make[1]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/m4 »
Making all in po
make[1]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/po »
make[1]: Rien à faire pour « all ».
make[1]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/po »
Making all in alsamixer
make[1]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/alsamixer »
make[1]: Rien à faire pour « all ».
make[1]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/alsamixer »
Making all in amixer
make[1]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/amixer »
make[1]: Rien à faire pour « all ».
make[1]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/amixer »
Making all in amidi
make[1]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/amidi »
make[1]: Rien à faire pour « all ».
make[1]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/amidi »
Making all in alsaconf
make[1]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/alsaconf »
Making all in po
make[2]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/alsaconf/po »
make[2]: Rien à faire pour « all ».
make[2]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/alsaconf/po »
make[2]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/alsaconf »
make[2]: Rien à faire pour « all-am ».
make[2]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/alsaconf »
make[1]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/alsaconf »
Making all in aplay
make[1]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/aplay »
make[1]: Rien à faire pour « all ».
make[1]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/aplay »
Making all in iecset
make[1]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/iecset »
make[1]: Rien à faire pour « all ».
make[1]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/iecset »
Making all in speaker-test
make[1]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/speaker-test »
Making all in samples
make[2]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/speaker-test/samples »
make[2]: Rien à faire pour « all ».
make[2]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/speaker-test/samples »
make[2]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/speaker-test »
make[2]: Rien à faire pour « all-am ».
make[2]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/speaker-test »
make[1]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/speaker-test »
Making all in seq
make[1]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/seq »
Making all in aconnect
make[2]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/seq/aconnect »
make[2]: Rien à faire pour « all ».
make[2]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/seq/aconnect »
Making all in aplaymidi
make[2]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/seq/aplaymidi »
make[2]: Rien à faire pour « all ».
make[2]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/seq/aplaymidi »
Making all in aseqdump
make[2]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/seq/aseqdump »
make[2]: Rien à faire pour « all ».
make[2]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/seq/aseqdump »
Making all in aseqnet
make[2]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/seq/aseqnet »
make[2]: Rien à faire pour « all ».
make[2]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/seq/aseqnet »
make[2]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/seq »
make[2]: Rien à faire pour « all-am ».
make[2]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/seq »
make[1]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/seq »
make[1]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20 »
make[1]: Rien à faire pour « all-am ».
make[1]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20 »
rabgye@ubuntumaya:~/alsa-utils-1.0.20$ sudo make install
Making install in include
make[1]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/include »
make[2]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/include »
make[2]: Rien à faire pour « install-exec-am ».
make[2]: Rien à faire pour « install-data-am ».
make[2]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/include »
make[1]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/include »
Making install in alsactl
make[1]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/alsactl »
Making install in init
make[2]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/alsactl/init »
make[3]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/alsactl/init »
make[3]: Rien à faire pour « install-exec-am ».
test -z "/usr/share/alsa/init" || mkdir -p -- "/usr/share/alsa/init"
 /usr/bin/install -c -m 644 '00main' '/usr/share/alsa/init/00main'
 /usr/bin/install -c -m 644 'default' '/usr/share/alsa/init/default'
 /usr/bin/install -c -m 644 'help' '/usr/share/alsa/init/help'
 /usr/bin/install -c -m 644 'info' '/usr/share/alsa/init/info'
 /usr/bin/install -c -m 644 'test' '/usr/share/alsa/init/test'
 /usr/bin/install -c -m 644 'hda' '/usr/share/alsa/init/hda'
make[3]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/alsactl/init »
make[2]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/alsactl/init »
make[2]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/alsactl »
make[3]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/alsactl »
test -z "/usr/sbin" || mkdir -p -- "/usr/sbin"
  /usr/bin/install -c 'alsactl' '/usr/sbin/alsactl'
test -z "/usr/share/man/man1" || mkdir -p -- "/usr/share/man/man1"
 /usr/bin/install -c -m 644 './alsactl.1' '/usr/share/man/man1/alsactl.1'
test -z "/usr/share/man/man7" || mkdir -p -- "/usr/share/man/man7"
 /usr/bin/install -c -m 644 './alsactl_init.7' '/usr/share/man/man7/alsactl_init.7'
make[3]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/alsactl »
make[2]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/alsactl »
make[1]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/alsactl »
Making install in utils
make[1]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/utils »
make[2]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/utils »
make[2]: Rien à faire pour « install-exec-am ».
make[2]: Rien à faire pour « install-data-am ».
make[2]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/utils »
make[1]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/utils »
Making install in m4
make[1]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/m4 »
make[2]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/m4 »
make[2]: Rien à faire pour « install-exec-am ».
make[2]: Rien à faire pour « install-data-am ».
make[2]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/m4 »
make[1]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/m4 »
Making install in po
make[1]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/po »
mkdir -p -- /usr/share
installing ja.gmo as /usr/share/locale/ja/LC_MESSAGES/alsa-utils.mo
if test "alsa-utils" = "gettext-tools"; then \
      mkdir -p -- /usr/share/gettext/po; \
      for file in Makefile.in.in remove-potcdate.sin quot.sed boldquot.sed [email]en@quot.header[/email] [email]en@boldquot.header[/email] insert-header.sin Rules-quot   Makevars.template; do \
        /usr/bin/install -c -m 644 ./$file \
                /usr/share/gettext/po/$file; \
      done; \
      for file in Makevars; do \
        rm -f /usr/share/gettext/po/$file; \
      done; \
    else \
      : ; \
    fi
make[1]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/po »
Making install in alsamixer
make[1]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/alsamixer »
make[2]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/alsamixer »
test -z "/usr/bin" || mkdir -p -- "/usr/bin"
  /usr/bin/install -c 'alsamixer' '/usr/bin/alsamixer'
test -z "/usr/share/man/man1" || mkdir -p -- "/usr/share/man/man1"
 /usr/bin/install -c -m 644 './alsamixer.1' '/usr/share/man/man1/alsamixer.1'
make[2]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/alsamixer »
make[1]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/alsamixer »
Making install in amixer
make[1]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/amixer »
make[2]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/amixer »
test -z "/usr/bin" || mkdir -p -- "/usr/bin"
  /usr/bin/install -c 'amixer' '/usr/bin/amixer'
test -z "/usr/share/man/man1" || mkdir -p -- "/usr/share/man/man1"
 /usr/bin/install -c -m 644 './amixer.1' '/usr/share/man/man1/amixer.1'
make[2]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/amixer »
make[1]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/amixer »
Making install in amidi
make[1]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/amidi »
make[2]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/amidi »
test -z "/usr/bin" || mkdir -p -- "/usr/bin"
  /usr/bin/install -c 'amidi' '/usr/bin/amidi'
test -z "/usr/share/man/man1" || mkdir -p -- "/usr/share/man/man1"
 /usr/bin/install -c -m 644 './amidi.1' '/usr/share/man/man1/amidi.1'
make[2]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/amidi »
make[1]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/amidi »
Making install in alsaconf
make[1]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/alsaconf »
Making install in po
make[2]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/alsaconf/po »
mkdir -p -- /usr/share
make[2]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/alsaconf/po »
make[2]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/alsaconf »
make[3]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/alsaconf »
test -z "/usr/sbin" || mkdir -p -- "/usr/sbin"
 /usr/bin/install -c 'alsaconf' '/usr/sbin/alsaconf'
 /usr/bin/install -c -m 644 alsaconf.8 /usr/share/man/man8/alsaconf.8
 /usr/bin/install -c -m 644 alsaconf.fr.8 /usr/share/man/fr/man8/alsaconf.8
make[3]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/alsaconf »
make[2]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/alsaconf »
make[1]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/alsaconf »
Making install in aplay
make[1]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/aplay »
make[2]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/aplay »
test -z "/usr/bin" || mkdir -p -- "/usr/bin"
  /usr/bin/install -c 'aplay' '/usr/bin/aplay'
make  install-exec-hook
make[3]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/aplay »
rm -f arecord
ln -s aplay arecord
rm -f /usr/bin/arecord
(cd /usr/bin && ln -s aplay arecord)
make[3]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/aplay »
test -z "/usr/share/man/man1" || mkdir -p -- "/usr/share/man/man1"
 /usr/bin/install -c -m 644 './aplay.1' '/usr/share/man/man1/aplay.1'
 /usr/bin/install -c -m 644 './arecord.1' '/usr/share/man/man1/arecord.1'
make  install-data-hook
make[3]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/aplay »
rm -f /usr/share/man/man1/arecord.1
(cd /usr/share/man/man1 && ln -s aplay.1 arecord.1)
make[3]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/aplay »
make[2]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/aplay »
make[1]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/aplay »
Making install in iecset
make[1]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/iecset »
make[2]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/iecset »
test -z "/usr/bin" || mkdir -p -- "/usr/bin"
  /usr/bin/install -c 'iecset' '/usr/bin/iecset'
test -z "/usr/share/man/man1" || mkdir -p -- "/usr/share/man/man1"
 /usr/bin/install -c -m 644 './iecset.1' '/usr/share/man/man1/iecset.1'
make[2]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/iecset »
make[1]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/iecset »
Making install in speaker-test
make[1]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/speaker-test »
Making install in samples
make[2]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/speaker-test/samples »
make[3]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/speaker-test/samples »
make[3]: Rien à faire pour « install-exec-am ».
test -z "/usr/share/alsa/speaker-test" || mkdir -p -- "/usr/share/alsa/speaker-test"
 /usr/bin/install -c -m 644 'sample_map.csv' '/usr/share/alsa/speaker-test/sample_map.csv'
test -z "/usr/share/sounds/alsa" || mkdir -p -- "/usr/share/sounds/alsa"
 /usr/bin/install -c -m 644 'Front_Left.wav' '/usr/share/sounds/alsa/Front_Left.wav'
 /usr/bin/install -c -m 644 'Rear_Center.wav' '/usr/share/sounds/alsa/Rear_Center.wav'
 /usr/bin/install -c -m 644 'Rear_Right.wav' '/usr/share/sounds/alsa/Rear_Right.wav'
 /usr/bin/install -c -m 644 'Side_Right.wav' '/usr/share/sounds/alsa/Side_Right.wav'
 /usr/bin/install -c -m 644 'Front_Center.wav' '/usr/share/sounds/alsa/Front_Center.wav'
 /usr/bin/install -c -m 644 'Front_Right.wav' '/usr/share/sounds/alsa/Front_Right.wav'
 /usr/bin/install -c -m 644 'Noise.wav' '/usr/share/sounds/alsa/Noise.wav'
 /usr/bin/install -c -m 644 'Rear_Left.wav' '/usr/share/sounds/alsa/Rear_Left.wav'
 /usr/bin/install -c -m 644 'Side_Left.wav' '/usr/share/sounds/alsa/Side_Left.wav'
make[3]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/speaker-test/samples »
make[2]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/speaker-test/samples »
make[2]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/speaker-test »
make[3]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/speaker-test »
test -z "/usr/bin" || mkdir -p -- "/usr/bin"
  /usr/bin/install -c 'speaker-test' '/usr/bin/speaker-test'
test -z "/usr/share/man/man1" || mkdir -p -- "/usr/share/man/man1"
 /usr/bin/install -c -m 644 './speaker-test.1' '/usr/share/man/man1/speaker-test.1'
make[3]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/speaker-test »
make[2]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/speaker-test »
make[1]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/speaker-test »
Making install in seq
make[1]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/seq »
Making install in aconnect
make[2]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/seq/aconnect »
make[3]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/seq/aconnect »
test -z "/usr/bin" || mkdir -p -- "/usr/bin"
  /usr/bin/install -c 'aconnect' '/usr/bin/aconnect'
test -z "/usr/share/man/man1" || mkdir -p -- "/usr/share/man/man1"
 /usr/bin/install -c -m 644 './aconnect.1' '/usr/share/man/man1/aconnect.1'
make[3]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/seq/aconnect »
make[2]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/seq/aconnect »
Making install in aplaymidi
make[2]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/seq/aplaymidi »
make[3]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/seq/aplaymidi »
test -z "/usr/bin" || mkdir -p -- "/usr/bin"
  /usr/bin/install -c 'aplaymidi' '/usr/bin/aplaymidi'
  /usr/bin/install -c 'arecordmidi' '/usr/bin/arecordmidi'
test -z "/usr/share/man/man1" || mkdir -p -- "/usr/share/man/man1"
 /usr/bin/install -c -m 644 './aplaymidi.1' '/usr/share/man/man1/aplaymidi.1'
 /usr/bin/install -c -m 644 './arecordmidi.1' '/usr/share/man/man1/arecordmidi.1'
make[3]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/seq/aplaymidi »
make[2]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/seq/aplaymidi »
Making install in aseqdump
make[2]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/seq/aseqdump »
make[3]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/seq/aseqdump »
test -z "/usr/bin" || mkdir -p -- "/usr/bin"
  /usr/bin/install -c 'aseqdump' '/usr/bin/aseqdump'
test -z "/usr/share/man/man1" || mkdir -p -- "/usr/share/man/man1"
 /usr/bin/install -c -m 644 './aseqdump.1' '/usr/share/man/man1/aseqdump.1'
make[3]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/seq/aseqdump »
make[2]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/seq/aseqdump »
Making install in aseqnet
make[2]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/seq/aseqnet »
make[3]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/seq/aseqnet »
test -z "/usr/bin" || mkdir -p -- "/usr/bin"
  /usr/bin/install -c 'aseqnet' '/usr/bin/aseqnet'
test -z "/usr/share/man/man1" || mkdir -p -- "/usr/share/man/man1"
 /usr/bin/install -c -m 644 './aseqnet.1' '/usr/share/man/man1/aseqnet.1'
make[3]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/seq/aseqnet »
make[2]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/seq/aseqnet »
make[2]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/seq »
make[3]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/seq »
make[3]: Rien à faire pour « install-exec-am ».
make[3]: Rien à faire pour « install-data-am ».
make[3]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/seq »
make[2]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/seq »
make[1]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/seq »
make[1]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20 »
make[2]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20 »
make[2]: Rien à faire pour « install-exec-am ».
make[2]: Rien à faire pour « install-data-am ».
make[2]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20 »
make[1]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20 »
rabgye@ubuntumaya:~/alsa-utils-1.0.20$ rm -f ~/alsa-driver*
rm: ne peut enlever `/home/rabgye/alsa-driver-1.0.20': est un dossier
rabgye@ubuntumaya:~/alsa-utils-1.0.20$ rm -f ~/alsa-lib*
rm: ne peut enlever `/home/rabgye/alsa-lib-1.0.20': est un dossier
rabgye@ubuntumaya:~/alsa-utils-1.0.20$ rm -f ~/alsa-utils*
rm: ne peut enlever `/home/rabgye/alsa-utils-1.0.20': est un dossier
rabgye@ubuntumaya:~/alsa-utils-1.0.20$

---

### Post by manjusri on 2009-06-25
> **manjusri said:**
> tout semble avoir marche avec quelques modifications sauf les trois dernieres lignes.voici les outputs:

































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































make[1]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/amixer »
if gcc -DHAVE_CONFIG_H -I. -I. -I../include -I../include    -g -O2 -MT amixer.o -MD -MP -MF ".deps/amixer.Tpo" -c -o amixer.o amixer.c; \
    then mv -f ".deps/amixer.Tpo" ".deps/amixer.Po"; else rm -f ".deps/amixer.Tpo"; exit 1; fi
amixer.c: In function ‘get_integer’:
amixer.c:244: attention : ignoring return value of ‘strtol’, declared with attribute warn_unused_result
amixer.c: In function ‘get_integer64’:
amixer.c:272: attention : ignoring return value of ‘strtol’, declared with attribute warn_unused_result
amixer.c: In function ‘set_volume_simple’:
amixer.c:358: attention : ignoring return value of ‘strtol’, declared with attribute warn_unused_result
gcc  -g -O2   -o amixer  amixer.o -lm -lasound -lm -ldl -lpthread
make[1]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/amixer »
Making all in amidi
make[1]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/amidi »
if gcc -DHAVE_CONFIG_H -I. -I. -I../include -I../include    -g -O2 -MT amidi.o -MD -MP -MF ".deps/amidi.Tpo" -c -o amidi.o amidi.c; \
    then mv -f ".deps/amidi.Tpo" ".deps/amidi.Po"; else rm -f ".deps/amidi.Tpo"; exit 1; fi
amidi.c: In function ‘main’:
amidi.c:658: attention : ignoring return value of ‘write’, declared with attribute warn_unused_result
gcc  -g -O2   -o amidi  amidi.o  -lasound -lm -ldl -lpthread
make[1]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/amidi »
Making all in alsaconf
make[1]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/alsaconf »
Making all in po
make[2]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/alsaconf/po »
35 messages traduits, 1 message non traduit.
34 messages traduits, 1 traduction approximative, 1 message non traduit.
make[2]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/alsaconf/po »
make[2]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/alsaconf »
make[2]: Rien à faire pour « all-am ».
make[2]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/alsaconf »
make[1]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/alsaconf »
Making all in aplay
make[1]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/aplay »
if gcc -DHAVE_CONFIG_H -I. -I. -I../include -I../include    -g -O2 -MT aplay.o -MD -MP -MF ".deps/aplay.Tpo" -c -o aplay.o aplay.c; \
    then mv -f ".deps/aplay.Tpo" ".deps/aplay.Po"; else rm -f ".deps/aplay.Tpo"; exit 1; fi
aplay.c: In function ‘end_voc’:
aplay.c:2158: attention : ignoring return value of ‘write’, declared with attribute warn_unused_result
aplay.c: In function ‘end_wave’:
aplay.c:2178: attention : ignoring return value of ‘write’, declared with attribute warn_unused_result
aplay.c:2180: attention : ignoring return value of ‘write’, declared with attribute warn_unused_result
aplay.c: In function ‘end_au’:
aplay.c:2193: attention : ignoring return value of ‘write’, declared with attribute warn_unused_result
gcc  -g -O2   -o aplay  aplay.o  -lrt -lasound -lm -ldl -lpthread
make[1]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/aplay »
Making all in iecset
make[1]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/iecset »
if gcc -DHAVE_CONFIG_H -I. -I. -I../include -I../include    -g -O2 -MT iecset.o -MD -MP -MF ".deps/iecset.Tpo" -c -o iecset.o iecset.c; \
    then mv -f ".deps/iecset.Tpo" ".deps/iecset.Po"; else rm -f ".deps/iecset.Tpo"; exit 1; fi
if gcc -DHAVE_CONFIG_H -I. -I. -I../include -I../include    -g -O2 -MT iecbits.o -MD -MP -MF ".deps/iecbits.Tpo" -c -o iecbits.o iecbits.c; \
    then mv -f ".deps/iecbits.Tpo" ".deps/iecbits.Po"; else rm -f ".deps/iecbits.Tpo"; exit 1; fi
gcc  -g -O2   -o iecset  iecset.o iecbits.o -lm -lasound -lm -ldl -lpthread
make[1]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/iecset »
Making all in speaker-test
make[1]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/speaker-test »
Making all in samples
make[2]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/speaker-test/samples »
make[2]: Rien à faire pour « all ».
make[2]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/speaker-test/samples »
make[2]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/speaker-test »
if gcc -DHAVE_CONFIG_H -I. -I. -I../include -I../include    -g -O2 -MT speaker-test.o -MD -MP -MF ".deps/speaker-test.Tpo" -c -o speaker-test.o speaker-test.c; \
    then mv -f ".deps/speaker-test.Tpo" ".deps/speaker-test.Po"; else rm -f ".deps/speaker-test.Tpo"; exit 1; fi
if gcc -DHAVE_CONFIG_H -I. -I. -I../include -I../include    -g -O2 -MT pink.o -MD -MP -MF ".deps/pink.Tpo" -c -o pink.o pink.c; \
    then mv -f ".deps/pink.Tpo" ".deps/pink.Po"; else rm -f ".deps/pink.Tpo"; exit 1; fi
gcc  -g -O2   -o speaker-test  speaker-test.o pink.o  -lm -lasound -lm -ldl -lpthread
make[2]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/speaker-test »
make[1]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/speaker-test »
Making all in seq
make[1]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/seq »
Making all in aconnect
make[2]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/seq/aconnect »
if gcc -DHAVE_CONFIG_H -I. -I. -I../../include -I../../include    -g -O2 -MT aconnect.o -MD -MP -MF ".deps/aconnect.Tpo" -c -o aconnect.o aconnect.c; \
    then mv -f ".deps/aconnect.Tpo" ".deps/aconnect.Po"; else rm -f ".deps/aconnect.Tpo"; exit 1; fi
gcc  -g -O2   -o aconnect  aconnect.o  -lasound -lm -ldl -lpthread
make[2]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/seq/aconnect »
Making all in aplaymidi
make[2]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/seq/aplaymidi »
if gcc -DHAVE_CONFIG_H -I. -I. -I../../include -I../../include    -g -O2 -MT aplaymidi.o -MD -MP -MF ".deps/aplaymidi.Tpo" -c -o aplaymidi.o aplaymidi.c; \
    then mv -f ".deps/aplaymidi.Tpo" ".deps/aplaymidi.Po"; else rm -f ".deps/aplaymidi.Tpo"; exit 1; fi
gcc  -g -O2   -o aplaymidi  aplaymidi.o  -lasound -lm -ldl -lpthread
if gcc -DHAVE_CONFIG_H -I. -I. -I../../include -I../../include    -g -O2 -MT arecordmidi.o -MD -MP -MF ".deps/arecordmidi.Tpo" -c -o arecordmidi.o arecordmidi.c; \
    then mv -f ".deps/arecordmidi.Tpo" ".deps/arecordmidi.Po"; else rm -f ".deps/arecordmidi.Tpo"; exit 1; fi
gcc  -g -O2   -o arecordmidi  arecordmidi.o  -lasound -lm -ldl -lpthread
make[2]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/seq/aplaymidi »
Making all in aseqdump
make[2]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/seq/aseqdump »
if gcc -DHAVE_CONFIG_H -I. -I. -I../../include -I../../include    -g -O2 -MT aseqdump.o -MD -MP -MF ".deps/aseqdump.Tpo" -c -o aseqdump.o aseqdump.c; \
    then mv -f ".deps/aseqdump.Tpo" ".deps/aseqdump.Po"; else rm -f ".deps/aseqdump.Tpo"; exit 1; fi
gcc  -g -O2   -o aseqdump  aseqdump.o  -lasound -lm -ldl -lpthread
make[2]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/seq/aseqdump »
Making all in aseqnet
make[2]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/seq/aseqnet »
if gcc -DHAVE_CONFIG_H -I. -I. -I../../include -I../../include    -g -O2 -MT aseqnet.o -MD -MP -MF ".deps/aseqnet.Tpo" -c -o aseqnet.o aseqnet.c; \
    then mv -f ".deps/aseqnet.Tpo" ".deps/aseqnet.Po"; else rm -f ".deps/aseqnet.Tpo"; exit 1; fi
aseqnet.c: In function ‘flush_writebuf’:
aseqnet.c:495: attention : ignoring return value of ‘write’, declared with attribute warn_unused_result
gcc  -g -O2   -o aseqnet  aseqnet.o  -lasound -lm -ldl -lpthread
make[2]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/seq/aseqnet »
make[2]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/seq »
make[2]: Rien à faire pour « all-am ».
make[2]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/seq »
make[1]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/seq »
make[1]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20 »
make[1]: Rien à faire pour « all-am ».
make[1]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20 »
rabgye@ubuntumaya:~/alsa-utils-1.0.20$ sudo make
Making all in include
make[1]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/include »
make  all-am
make[2]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/include »
make[2]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/include »
make[1]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/include »
Making all in alsactl
make[1]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/alsactl »
Making all in init
make[2]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/alsactl/init »
make[2]: Rien à faire pour « all ».
make[2]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/alsactl/init »
make[2]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/alsactl »
make[2]: Rien à faire pour « all-am ».
make[2]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/alsactl »
make[1]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/alsactl »
Making all in utils
make[1]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/utils »
make[1]: Rien à faire pour « all ».
make[1]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/utils »
Making all in m4
make[1]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/m4 »
make[1]: Rien à faire pour « all ».
make[1]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/m4 »
Making all in po
make[1]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/po »
make[1]: Rien à faire pour « all ».
make[1]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/po »
Making all in alsamixer
make[1]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/alsamixer »
make[1]: Rien à faire pour « all ».
make[1]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/alsamixer »
Making all in amixer
make[1]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/amixer »
make[1]: Rien à faire pour « all ».
make[1]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/amixer »
Making all in amidi
make[1]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/amidi »
make[1]: Rien à faire pour « all ».
make[1]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/amidi »
Making all in alsaconf
make[1]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/alsaconf »
Making all in po
make[2]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/alsaconf/po »
make[2]: Rien à faire pour « all ».
make[2]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/alsaconf/po »
make[2]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/alsaconf »
make[2]: Rien à faire pour « all-am ».
make[2]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/alsaconf »
make[1]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/alsaconf »
Making all in aplay
make[1]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/aplay »
make[1]: Rien à faire pour « all ».
make[1]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/aplay »
Making all in iecset
make[1]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/iecset »
make[1]: Rien à faire pour « all ».
make[1]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/iecset »
Making all in speaker-test
make[1]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/speaker-test »
Making all in samples
make[2]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/speaker-test/samples »
make[2]: Rien à faire pour « all ».
make[2]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/speaker-test/samples »
make[2]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/speaker-test »
make[2]: Rien à faire pour « all-am ».
make[2]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/speaker-test »
make[1]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/speaker-test »
Making all in seq
make[1]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/seq »
Making all in aconnect
make[2]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/seq/aconnect »
make[2]: Rien à faire pour « all ».
make[2]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/seq/aconnect »
Making all in aplaymidi
make[2]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/seq/aplaymidi »
make[2]: Rien à faire pour « all ».
make[2]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/seq/aplaymidi »
Making all in aseqdump
make[2]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/seq/aseqdump »
make[2]: Rien à faire pour « all ».
make[2]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/seq/aseqdump »
Making all in aseqnet
make[2]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/seq/aseqnet »
make[2]: Rien à faire pour « all ».
make[2]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/seq/aseqnet »
make[2]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/seq »
make[2]: Rien à faire pour « all-am ».
make[2]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/seq »
make[1]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/seq »
make[1]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20 »
make[1]: Rien à faire pour « all-am ».
make[1]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20 »
rabgye@ubuntumaya:~/alsa-utils-1.0.20$ sudo make install
Making install in include
make[1]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/include »
make[2]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/include »
make[2]: Rien à faire pour « install-exec-am ».
make[2]: Rien à faire pour « install-data-am ».
make[2]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/include »
make[1]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/include »
Making install in alsactl
make[1]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/alsactl »
Making install in init
make[2]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/alsactl/init »
make[3]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/alsactl/init »
make[3]: Rien à faire pour « install-exec-am ».
test -z "/usr/share/alsa/init" || mkdir -p -- "/usr/share/alsa/init"
 /usr/bin/install -c -m 644 '00main' '/usr/share/alsa/init/00main'
 /usr/bin/install -c -m 644 'default' '/usr/share/alsa/init/default'
 /usr/bin/install -c -m 644 'help' '/usr/share/alsa/init/help'
 /usr/bin/install -c -m 644 'info' '/usr/share/alsa/init/info'
 /usr/bin/install -c -m 644 'test' '/usr/share/alsa/init/test'
 /usr/bin/install -c -m 644 'hda' '/usr/share/alsa/init/hda'
make[3]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/alsactl/init »
make[2]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/alsactl/init »
make[2]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/alsactl »
make[3]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/alsactl »
test -z "/usr/sbin" || mkdir -p -- "/usr/sbin"
  /usr/bin/install -c 'alsactl' '/usr/sbin/alsactl'
test -z "/usr/share/man/man1" || mkdir -p -- "/usr/share/man/man1"
 /usr/bin/install -c -m 644 './alsactl.1' '/usr/share/man/man1/alsactl.1'
test -z "/usr/share/man/man7" || mkdir -p -- "/usr/share/man/man7"
 /usr/bin/install -c -m 644 './alsactl_init.7' '/usr/share/man/man7/alsactl_init.7'
make[3]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/alsactl »
make[2]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/alsactl »
make[1]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/alsactl »
Making install in utils
make[1]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/utils »
make[2]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/utils »
make[2]: Rien à faire pour « install-exec-am ».
make[2]: Rien à faire pour « install-data-am ».
make[2]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/utils »
make[1]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/utils »
Making install in m4
make[1]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/m4 »
make[2]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/m4 »
make[2]: Rien à faire pour « install-exec-am ».
make[2]: Rien à faire pour « install-data-am ».
make[2]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/m4 »
make[1]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/m4 »
Making install in po
make[1]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/po »
mkdir -p -- /usr/share
installing ja.gmo as /usr/share/locale/ja/LC_MESSAGES/alsa-utils.mo
if test "alsa-utils" = "gettext-tools"; then \
      mkdir -p -- /usr/share/gettext/po; \
      for file in Makefile.in.in remove-potcdate.sin quot.sed boldquot.sed [EMAIL="en@quot.header"]en@quot.header[/EMAIL] [EMAIL="en@boldquot.header"]en@boldquot.header[/EMAIL] insert-header.sin Rules-quot   Makevars.template; do \
        /usr/bin/install -c -m 644 ./$file \
                /usr/share/gettext/po/$file; \
      done; \
      for file in Makevars; do \
        rm -f /usr/share/gettext/po/$file; \
      done; \
    else \
      : ; \
    fi
make[1]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/po »
Making install in alsamixer
make[1]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/alsamixer »
make[2]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/alsamixer »
test -z "/usr/bin" || mkdir -p -- "/usr/bin"
  /usr/bin/install -c 'alsamixer' '/usr/bin/alsamixer'
test -z "/usr/share/man/man1" || mkdir -p -- "/usr/share/man/man1"
 /usr/bin/install -c -m 644 './alsamixer.1' '/usr/share/man/man1/alsamixer.1'
make[2]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/alsamixer »
make[1]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/alsamixer »
Making install in amixer
make[1]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/amixer »
make[2]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/amixer »
test -z "/usr/bin" || mkdir -p -- "/usr/bin"
  /usr/bin/install -c 'amixer' '/usr/bin/amixer'
test -z "/usr/share/man/man1" || mkdir -p -- "/usr/share/man/man1"
 /usr/bin/install -c -m 644 './amixer.1' '/usr/share/man/man1/amixer.1'
make[2]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/amixer »
make[1]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/amixer »
Making install in amidi
make[1]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/amidi »
make[2]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/amidi »
test -z "/usr/bin" || mkdir -p -- "/usr/bin"
  /usr/bin/install -c 'amidi' '/usr/bin/amidi'
test -z "/usr/share/man/man1" || mkdir -p -- "/usr/share/man/man1"
 /usr/bin/install -c -m 644 './amidi.1' '/usr/share/man/man1/amidi.1'
make[2]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/amidi »
make[1]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/amidi »
Making install in alsaconf
make[1]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/alsaconf »
Making install in po
make[2]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/alsaconf/po »
mkdir -p -- /usr/share
make[2]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/alsaconf/po »
make[2]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/alsaconf »
make[3]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/alsaconf »
test -z "/usr/sbin" || mkdir -p -- "/usr/sbin"
 /usr/bin/install -c 'alsaconf' '/usr/sbin/alsaconf'
 /usr/bin/install -c -m 644 alsaconf.8 /usr/share/man/man8/alsaconf.8
 /usr/bin/install -c -m 644 alsaconf.fr.8 /usr/share/man/fr/man8/alsaconf.8
make[3]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/alsaconf »
make[2]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/alsaconf »
make[1]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/alsaconf »
Making install in aplay
make[1]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/aplay »
make[2]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/aplay »
test -z "/usr/bin" || mkdir -p -- "/usr/bin"
  /usr/bin/install -c 'aplay' '/usr/bin/aplay'
make  install-exec-hook
make[3]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/aplay »
rm -f arecord
ln -s aplay arecord
rm -f /usr/bin/arecord
(cd /usr/bin && ln -s aplay arecord)
make[3]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/aplay »
test -z "/usr/share/man/man1" || mkdir -p -- "/usr/share/man/man1"
 /usr/bin/install -c -m 644 './aplay.1' '/usr/share/man/man1/aplay.1'
 /usr/bin/install -c -m 644 './arecord.1' '/usr/share/man/man1/arecord.1'
make  install-data-hook
make[3]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/aplay »
rm -f /usr/share/man/man1/arecord.1
(cd /usr/share/man/man1 && ln -s aplay.1 arecord.1)
make[3]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/aplay »
make[2]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/aplay »
make[1]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/aplay »
Making install in iecset
make[1]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/iecset »
make[2]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/iecset »
test -z "/usr/bin" || mkdir -p -- "/usr/bin"
  /usr/bin/install -c 'iecset' '/usr/bin/iecset'
test -z "/usr/share/man/man1" || mkdir -p -- "/usr/share/man/man1"
 /usr/bin/install -c -m 644 './iecset.1' '/usr/share/man/man1/iecset.1'
make[2]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/iecset »
make[1]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/iecset »
Making install in speaker-test
make[1]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/speaker-test »
Making install in samples
make[2]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/speaker-test/samples »
make[3]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/speaker-test/samples »
make[3]: Rien à faire pour « install-exec-am ».
test -z "/usr/share/alsa/speaker-test" || mkdir -p -- "/usr/share/alsa/speaker-test"
 /usr/bin/install -c -m 644 'sample_map.csv' '/usr/share/alsa/speaker-test/sample_map.csv'
test -z "/usr/share/sounds/alsa" || mkdir -p -- "/usr/share/sounds/alsa"
 /usr/bin/install -c -m 644 'Front_Left.wav' '/usr/share/sounds/alsa/Front_Left.wav'
 /usr/bin/install -c -m 644 'Rear_Center.wav' '/usr/share/sounds/alsa/Rear_Center.wav'
 /usr/bin/install -c -m 644 'Rear_Right.wav' '/usr/share/sounds/alsa/Rear_Right.wav'
 /usr/bin/install -c -m 644 'Side_Right.wav' '/usr/share/sounds/alsa/Side_Right.wav'
 /usr/bin/install -c -m 644 'Front_Center.wav' '/usr/share/sounds/alsa/Front_Center.wav'
 /usr/bin/install -c -m 644 'Front_Right.wav' '/usr/share/sounds/alsa/Front_Right.wav'
 /usr/bin/install -c -m 644 'Noise.wav' '/usr/share/sounds/alsa/Noise.wav'
 /usr/bin/install -c -m 644 'Rear_Left.wav' '/usr/share/sounds/alsa/Rear_Left.wav'
 /usr/bin/install -c -m 644 'Side_Left.wav' '/usr/share/sounds/alsa/Side_Left.wav'
make[3]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/speaker-test/samples »
make[2]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/speaker-test/samples »
make[2]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/speaker-test »
make[3]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/speaker-test »
test -z "/usr/bin" || mkdir -p -- "/usr/bin"
  /usr/bin/install -c 'speaker-test' '/usr/bin/speaker-test'
test -z "/usr/share/man/man1" || mkdir -p -- "/usr/share/man/man1"
 /usr/bin/install -c -m 644 './speaker-test.1' '/usr/share/man/man1/speaker-test.1'
make[3]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/speaker-test »
make[2]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/speaker-test »
make[1]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/speaker-test »
Making install in seq
make[1]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/seq »
Making install in aconnect
make[2]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/seq/aconnect »
make[3]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/seq/aconnect »
test -z "/usr/bin" || mkdir -p -- "/usr/bin"
  /usr/bin/install -c 'aconnect' '/usr/bin/aconnect'
test -z "/usr/share/man/man1" || mkdir -p -- "/usr/share/man/man1"
 /usr/bin/install -c -m 644 './aconnect.1' '/usr/share/man/man1/aconnect.1'
make[3]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/seq/aconnect »
make[2]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/seq/aconnect »
Making install in aplaymidi
make[2]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/seq/aplaymidi »
make[3]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/seq/aplaymidi »
test -z "/usr/bin" || mkdir -p -- "/usr/bin"
  /usr/bin/install -c 'aplaymidi' '/usr/bin/aplaymidi'
  /usr/bin/install -c 'arecordmidi' '/usr/bin/arecordmidi'
test -z "/usr/share/man/man1" || mkdir -p -- "/usr/share/man/man1"
 /usr/bin/install -c -m 644 './aplaymidi.1' '/usr/share/man/man1/aplaymidi.1'
 /usr/bin/install -c -m 644 './arecordmidi.1' '/usr/share/man/man1/arecordmidi.1'
make[3]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/seq/aplaymidi »
make[2]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/seq/aplaymidi »
Making install in aseqdump
make[2]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/seq/aseqdump »
make[3]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/seq/aseqdump »
test -z "/usr/bin" || mkdir -p -- "/usr/bin"
  /usr/bin/install -c 'aseqdump' '/usr/bin/aseqdump'
test -z "/usr/share/man/man1" || mkdir -p -- "/usr/share/man/man1"
 /usr/bin/install -c -m 644 './aseqdump.1' '/usr/share/man/man1/aseqdump.1'
make[3]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/seq/aseqdump »
make[2]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/seq/aseqdump »
Making install in aseqnet
make[2]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/seq/aseqnet »
make[3]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/seq/aseqnet »
test -z "/usr/bin" || mkdir -p -- "/usr/bin"
  /usr/bin/install -c 'aseqnet' '/usr/bin/aseqnet'
test -z "/usr/share/man/man1" || mkdir -p -- "/usr/share/man/man1"
 /usr/bin/install -c -m 644 './aseqnet.1' '/usr/share/man/man1/aseqnet.1'
make[3]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/seq/aseqnet »
make[2]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/seq/aseqnet »
make[2]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/seq »
make[3]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/seq »
make[3]: Rien à faire pour « install-exec-am ».
make[3]: Rien à faire pour « install-data-am ».
make[3]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/seq »
make[2]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/seq »
make[1]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/seq »
make[1]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20 »
make[2]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20 »
make[2]: Rien à faire pour « install-exec-am ».
make[2]: Rien à faire pour « install-data-am ».
make[2]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20 »
make[1]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20 »
rabgye@ubuntumaya:~/alsa-utils-1.0.20$ rm -f ~/alsa-driver*
rm: ne peut enlever `/home/rabgye/alsa-driver-1.0.20': est un dossier
rabgye@ubuntumaya:~/alsa-utils-1.0.20$ rm -f ~/alsa-lib*
rm: ne peut enlever `/home/rabgye/alsa-lib-1.0.20': est un dossier
rabgye@ubuntumaya:~/alsa-utils-1.0.20$ rm -f ~/alsa-utils*
rm: ne peut enlever `/home/rabgye/alsa-utils-1.0.20': est un dossier
rabgye@ubuntumaya:~/alsa-utils-1.0.20$ 

je n'ai pas teste ne sachant pas quoi faire pour les trois dernieres lignes.merci.j'espere que les vacances ont ete bonnes































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































make[1]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/amixer »
if gcc -DHAVE_CONFIG_H -I. -I. -I../include -I../include    -g -O2 -MT amixer.o -MD -MP -MF ".deps/amixer.Tpo" -c -o amixer.o amixer.c; \
    then mv -f ".deps/amixer.Tpo" ".deps/amixer.Po"; else rm -f ".deps/amixer.Tpo"; exit 1; fi
amixer.c: In function ‘get_integer’:
amixer.c:244: attention : ignoring return value of ‘strtol’, declared with attribute warn_unused_result
amixer.c: In function ‘get_integer64’:
amixer.c:272: attention : ignoring return value of ‘strtol’, declared with attribute warn_unused_result
amixer.c: In function ‘set_volume_simple’:
amixer.c:358: attention : ignoring return value of ‘strtol’, declared with attribute warn_unused_result
gcc  -g -O2   -o amixer  amixer.o -lm -lasound -lm -ldl -lpthread
make[1]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/amixer »
Making all in amidi
make[1]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/amidi »
if gcc -DHAVE_CONFIG_H -I. -I. -I../include -I../include    -g -O2 -MT amidi.o -MD -MP -MF ".deps/amidi.Tpo" -c -o amidi.o amidi.c; \
    then mv -f ".deps/amidi.Tpo" ".deps/amidi.Po"; else rm -f ".deps/amidi.Tpo"; exit 1; fi
amidi.c: In function ‘main’:
amidi.c:658: attention : ignoring return value of ‘write’, declared with attribute warn_unused_result
gcc  -g -O2   -o amidi  amidi.o  -lasound -lm -ldl -lpthread
make[1]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/amidi »
Making all in alsaconf
make[1]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/alsaconf »
Making all in po
make[2]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/alsaconf/po »
35 messages traduits, 1 message non traduit.
34 messages traduits, 1 traduction approximative, 1 message non traduit.
make[2]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/alsaconf/po »
make[2]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/alsaconf »
make[2]: Rien à faire pour « all-am ».
make[2]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/alsaconf »
make[1]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/alsaconf »
Making all in aplay
make[1]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/aplay »
if gcc -DHAVE_CONFIG_H -I. -I. -I../include -I../include    -g -O2 -MT aplay.o -MD -MP -MF ".deps/aplay.Tpo" -c -o aplay.o aplay.c; \
    then mv -f ".deps/aplay.Tpo" ".deps/aplay.Po"; else rm -f ".deps/aplay.Tpo"; exit 1; fi
aplay.c: In function ‘end_voc’:
aplay.c:2158: attention : ignoring return value of ‘write’, declared with attribute warn_unused_result
aplay.c: In function ‘end_wave’:
aplay.c:2178: attention : ignoring return value of ‘write’, declared with attribute warn_unused_result
aplay.c:2180: attention : ignoring return value of ‘write’, declared with attribute warn_unused_result
aplay.c: In function ‘end_au’:
aplay.c:2193: attention : ignoring return value of ‘write’, declared with attribute warn_unused_result
gcc  -g -O2   -o aplay  aplay.o  -lrt -lasound -lm -ldl -lpthread
make[1]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/aplay »
Making all in iecset
make[1]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/iecset »
if gcc -DHAVE_CONFIG_H -I. -I. -I../include -I../include    -g -O2 -MT iecset.o -MD -MP -MF ".deps/iecset.Tpo" -c -o iecset.o iecset.c; \
    then mv -f ".deps/iecset.Tpo" ".deps/iecset.Po"; else rm -f ".deps/iecset.Tpo"; exit 1; fi
if gcc -DHAVE_CONFIG_H -I. -I. -I../include -I../include    -g -O2 -MT iecbits.o -MD -MP -MF ".deps/iecbits.Tpo" -c -o iecbits.o iecbits.c; \
    then mv -f ".deps/iecbits.Tpo" ".deps/iecbits.Po"; else rm -f ".deps/iecbits.Tpo"; exit 1; fi
gcc  -g -O2   -o iecset  iecset.o iecbits.o -lm -lasound -lm -ldl -lpthread
make[1]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/iecset »
Making all in speaker-test
make[1]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/speaker-test »
Making all in samples
make[2]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/speaker-test/samples »
make[2]: Rien à faire pour « all ».
make[2]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/speaker-test/samples »
make[2]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/speaker-test »
if gcc -DHAVE_CONFIG_H -I. -I. -I../include -I../include    -g -O2 -MT speaker-test.o -MD -MP -MF ".deps/speaker-test.Tpo" -c -o speaker-test.o speaker-test.c; \
    then mv -f ".deps/speaker-test.Tpo" ".deps/speaker-test.Po"; else rm -f ".deps/speaker-test.Tpo"; exit 1; fi
if gcc -DHAVE_CONFIG_H -I. -I. -I../include -I../include    -g -O2 -MT pink.o -MD -MP -MF ".deps/pink.Tpo" -c -o pink.o pink.c; \
    then mv -f ".deps/pink.Tpo" ".deps/pink.Po"; else rm -f ".deps/pink.Tpo"; exit 1; fi
gcc  -g -O2   -o speaker-test  speaker-test.o pink.o  -lm -lasound -lm -ldl -lpthread
make[2]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/speaker-test »
make[1]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/speaker-test »
Making all in seq
make[1]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/seq »
Making all in aconnect
make[2]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/seq/aconnect »
if gcc -DHAVE_CONFIG_H -I. -I. -I../../include -I../../include    -g -O2 -MT aconnect.o -MD -MP -MF ".deps/aconnect.Tpo" -c -o aconnect.o aconnect.c; \
    then mv -f ".deps/aconnect.Tpo" ".deps/aconnect.Po"; else rm -f ".deps/aconnect.Tpo"; exit 1; fi
gcc  -g -O2   -o aconnect  aconnect.o  -lasound -lm -ldl -lpthread
make[2]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/seq/aconnect »
Making all in aplaymidi
make[2]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/seq/aplaymidi »
if gcc -DHAVE_CONFIG_H -I. -I. -I../../include -I../../include    -g -O2 -MT aplaymidi.o -MD -MP -MF ".deps/aplaymidi.Tpo" -c -o aplaymidi.o aplaymidi.c; \
    then mv -f ".deps/aplaymidi.Tpo" ".deps/aplaymidi.Po"; else rm -f ".deps/aplaymidi.Tpo"; exit 1; fi
gcc  -g -O2   -o aplaymidi  aplaymidi.o  -lasound -lm -ldl -lpthread
if gcc -DHAVE_CONFIG_H -I. -I. -I../../include -I../../include    -g -O2 -MT arecordmidi.o -MD -MP -MF ".deps/arecordmidi.Tpo" -c -o arecordmidi.o arecordmidi.c; \
    then mv -f ".deps/arecordmidi.Tpo" ".deps/arecordmidi.Po"; else rm -f ".deps/arecordmidi.Tpo"; exit 1; fi
gcc  -g -O2   -o arecordmidi  arecordmidi.o  -lasound -lm -ldl -lpthread
make[2]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/seq/aplaymidi »
Making all in aseqdump
make[2]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/seq/aseqdump »
if gcc -DHAVE_CONFIG_H -I. -I. -I../../include -I../../include    -g -O2 -MT aseqdump.o -MD -MP -MF ".deps/aseqdump.Tpo" -c -o aseqdump.o aseqdump.c; \
    then mv -f ".deps/aseqdump.Tpo" ".deps/aseqdump.Po"; else rm -f ".deps/aseqdump.Tpo"; exit 1; fi
gcc  -g -O2   -o aseqdump  aseqdump.o  -lasound -lm -ldl -lpthread
make[2]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/seq/aseqdump »
Making all in aseqnet
make[2]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/seq/aseqnet »
if gcc -DHAVE_CONFIG_H -I. -I. -I../../include -I../../include    -g -O2 -MT aseqnet.o -MD -MP -MF ".deps/aseqnet.Tpo" -c -o aseqnet.o aseqnet.c; \
    then mv -f ".deps/aseqnet.Tpo" ".deps/aseqnet.Po"; else rm -f ".deps/aseqnet.Tpo"; exit 1; fi
aseqnet.c: In function ‘flush_writebuf’:
aseqnet.c:495: attention : ignoring return value of ‘write’, declared with attribute warn_unused_result
gcc  -g -O2   -o aseqnet  aseqnet.o  -lasound -lm -ldl -lpthread
make[2]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/seq/aseqnet »
make[2]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/seq »
make[2]: Rien à faire pour « all-am ».
make[2]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/seq »
make[1]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/seq »
make[1]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20 »
make[1]: Rien à faire pour « all-am ».
make[1]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20 »
rabgye@ubuntumaya:~/alsa-utils-1.0.20$ sudo make
Making all in include
make[1]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/include »
make  all-am
make[2]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/include »
make[2]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/include »
make[1]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/include »
Making all in alsactl
make[1]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/alsactl »
Making all in init
make[2]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/alsactl/init »
make[2]: Rien à faire pour « all ».
make[2]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/alsactl/init »
make[2]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/alsactl »
make[2]: Rien à faire pour « all-am ».
make[2]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/alsactl »
make[1]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/alsactl »
Making all in utils
make[1]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/utils »
make[1]: Rien à faire pour « all ».
make[1]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/utils »
Making all in m4
make[1]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/m4 »
make[1]: Rien à faire pour « all ».
make[1]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/m4 »
Making all in po
make[1]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/po »
make[1]: Rien à faire pour « all ».
make[1]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/po »
Making all in alsamixer
make[1]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/alsamixer »
make[1]: Rien à faire pour « all ».
make[1]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/alsamixer »
Making all in amixer
make[1]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/amixer »
make[1]: Rien à faire pour « all ».
make[1]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/amixer »
Making all in amidi
make[1]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/amidi »
make[1]: Rien à faire pour « all ».
make[1]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/amidi »
Making all in alsaconf
make[1]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/alsaconf »
Making all in po
make[2]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/alsaconf/po »
make[2]: Rien à faire pour « all ».
make[2]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/alsaconf/po »
make[2]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/alsaconf »
make[2]: Rien à faire pour « all-am ».
make[2]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/alsaconf »
make[1]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/alsaconf »
Making all in aplay
make[1]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/aplay »
make[1]: Rien à faire pour « all ».
make[1]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/aplay »
Making all in iecset
make[1]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/iecset »
make[1]: Rien à faire pour « all ».
make[1]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/iecset »
Making all in speaker-test
make[1]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/speaker-test »
Making all in samples
make[2]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/speaker-test/samples »
make[2]: Rien à faire pour « all ».
make[2]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/speaker-test/samples »
make[2]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/speaker-test »
make[2]: Rien à faire pour « all-am ».
make[2]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/speaker-test »
make[1]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/speaker-test »
Making all in seq
make[1]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/seq »
Making all in aconnect
make[2]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/seq/aconnect »
make[2]: Rien à faire pour « all ».
make[2]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/seq/aconnect »
Making all in aplaymidi
make[2]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/seq/aplaymidi »
make[2]: Rien à faire pour « all ».
make[2]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/seq/aplaymidi »
Making all in aseqdump
make[2]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/seq/aseqdump »
make[2]: Rien à faire pour « all ».
make[2]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/seq/aseqdump »
Making all in aseqnet
make[2]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/seq/aseqnet »
make[2]: Rien à faire pour « all ».
make[2]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/seq/aseqnet »
make[2]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/seq »
make[2]: Rien à faire pour « all-am ».
make[2]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/seq »
make[1]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/seq »
make[1]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20 »
make[1]: Rien à faire pour « all-am ».
make[1]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20 »
rabgye@ubuntumaya:~/alsa-utils-1.0.20$ sudo make install
Making install in include
make[1]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/include »
make[2]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/include »
make[2]: Rien à faire pour « install-exec-am ».
make[2]: Rien à faire pour « install-data-am ».
make[2]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/include »
make[1]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/include »
Making install in alsactl
make[1]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/alsactl »
Making install in init
make[2]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/alsactl/init »
make[3]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/alsactl/init »
make[3]: Rien à faire pour « install-exec-am ».
test -z "/usr/share/alsa/init" || mkdir -p -- "/usr/share/alsa/init"
 /usr/bin/install -c -m 644 '00main' '/usr/share/alsa/init/00main'
 /usr/bin/install -c -m 644 'default' '/usr/share/alsa/init/default'
 /usr/bin/install -c -m 644 'help' '/usr/share/alsa/init/help'
 /usr/bin/install -c -m 644 'info' '/usr/share/alsa/init/info'
 /usr/bin/install -c -m 644 'test' '/usr/share/alsa/init/test'
 /usr/bin/install -c -m 644 'hda' '/usr/share/alsa/init/hda'
make[3]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/alsactl/init »
make[2]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/alsactl/init »
make[2]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/alsactl »
make[3]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/alsactl »
test -z "/usr/sbin" || mkdir -p -- "/usr/sbin"
  /usr/bin/install -c 'alsactl' '/usr/sbin/alsactl'
test -z "/usr/share/man/man1" || mkdir -p -- "/usr/share/man/man1"
 /usr/bin/install -c -m 644 './alsactl.1' '/usr/share/man/man1/alsactl.1'
test -z "/usr/share/man/man7" || mkdir -p -- "/usr/share/man/man7"
 /usr/bin/install -c -m 644 './alsactl_init.7' '/usr/share/man/man7/alsactl_init.7'
make[3]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/alsactl »
make[2]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/alsactl »
make[1]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/alsactl »
Making install in utils
make[1]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/utils »
make[2]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/utils »
make[2]: Rien à faire pour « install-exec-am ».
make[2]: Rien à faire pour « install-data-am ».
make[2]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/utils »
make[1]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/utils »
Making install in m4
make[1]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/m4 »
make[2]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/m4 »
make[2]: Rien à faire pour « install-exec-am ».
make[2]: Rien à faire pour « install-data-am ».
make[2]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/m4 »
make[1]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/m4 »
Making install in po
make[1]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/po »
mkdir -p -- /usr/share
installing ja.gmo as /usr/share/locale/ja/LC_MESSAGES/alsa-utils.mo
if test "alsa-utils" = "gettext-tools"; then \
      mkdir -p -- /usr/share/gettext/po; \
      for file in Makefile.in.in remove-potcdate.sin quot.sed boldquot.sed [EMAIL="en@quot.header"]en@quot.header[/EMAIL] [EMAIL="en@boldquot.header"]en@boldquot.header[/EMAIL] insert-header.sin Rules-quot   Makevars.template; do \
        /usr/bin/install -c -m 644 ./$file \
                /usr/share/gettext/po/$file; \
      done; \
      for file in Makevars; do \
        rm -f /usr/share/gettext/po/$file; \
      done; \
    else \
      : ; \
    fi
make[1]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/po »
Making install in alsamixer
make[1]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/alsamixer »
make[2]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/alsamixer »
test -z "/usr/bin" || mkdir -p -- "/usr/bin"
  /usr/bin/install -c 'alsamixer' '/usr/bin/alsamixer'
test -z "/usr/share/man/man1" || mkdir -p -- "/usr/share/man/man1"
 /usr/bin/install -c -m 644 './alsamixer.1' '/usr/share/man/man1/alsamixer.1'
make[2]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/alsamixer »
make[1]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/alsamixer »
Making install in amixer
make[1]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/amixer »
make[2]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/amixer »
test -z "/usr/bin" || mkdir -p -- "/usr/bin"
  /usr/bin/install -c 'amixer' '/usr/bin/amixer'
test -z "/usr/share/man/man1" || mkdir -p -- "/usr/share/man/man1"
 /usr/bin/install -c -m 644 './amixer.1' '/usr/share/man/man1/amixer.1'
make[2]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/amixer »
make[1]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/amixer »
Making install in amidi
make[1]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/amidi »
make[2]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/amidi »
test -z "/usr/bin" || mkdir -p -- "/usr/bin"
  /usr/bin/install -c 'amidi' '/usr/bin/amidi'
test -z "/usr/share/man/man1" || mkdir -p -- "/usr/share/man/man1"
 /usr/bin/install -c -m 644 './amidi.1' '/usr/share/man/man1/amidi.1'
make[2]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/amidi »
make[1]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/amidi »
Making install in alsaconf
make[1]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/alsaconf »
Making install in po
make[2]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/alsaconf/po »
mkdir -p -- /usr/share
make[2]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/alsaconf/po »
make[2]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/alsaconf »
make[3]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/alsaconf »
test -z "/usr/sbin" || mkdir -p -- "/usr/sbin"
 /usr/bin/install -c 'alsaconf' '/usr/sbin/alsaconf'
 /usr/bin/install -c -m 644 alsaconf.8 /usr/share/man/man8/alsaconf.8
 /usr/bin/install -c -m 644 alsaconf.fr.8 /usr/share/man/fr/man8/alsaconf.8
make[3]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/alsaconf »
make[2]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/alsaconf »
make[1]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/alsaconf »
Making install in aplay
make[1]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/aplay »
make[2]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/aplay »
test -z "/usr/bin" || mkdir -p -- "/usr/bin"
  /usr/bin/install -c 'aplay' '/usr/bin/aplay'
make  install-exec-hook
make[3]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/aplay »
rm -f arecord
ln -s aplay arecord
rm -f /usr/bin/arecord
(cd /usr/bin && ln -s aplay arecord)
make[3]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/aplay »
test -z "/usr/share/man/man1" || mkdir -p -- "/usr/share/man/man1"
 /usr/bin/install -c -m 644 './aplay.1' '/usr/share/man/man1/aplay.1'
 /usr/bin/install -c -m 644 './arecord.1' '/usr/share/man/man1/arecord.1'
make  install-data-hook
make[3]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/aplay »
rm -f /usr/share/man/man1/arecord.1
(cd /usr/share/man/man1 && ln -s aplay.1 arecord.1)
make[3]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/aplay »
make[2]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/aplay »
make[1]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/aplay »
Making install in iecset
make[1]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/iecset »
make[2]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/iecset »
test -z "/usr/bin" || mkdir -p -- "/usr/bin"
  /usr/bin/install -c 'iecset' '/usr/bin/iecset'
test -z "/usr/share/man/man1" || mkdir -p -- "/usr/share/man/man1"
 /usr/bin/install -c -m 644 './iecset.1' '/usr/share/man/man1/iecset.1'
make[2]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/iecset »
make[1]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/iecset »
Making install in speaker-test
make[1]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/speaker-test »
Making install in samples
make[2]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/speaker-test/samples »
make[3]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/speaker-test/samples »
make[3]: Rien à faire pour « install-exec-am ».
test -z "/usr/share/alsa/speaker-test" || mkdir -p -- "/usr/share/alsa/speaker-test"
 /usr/bin/install -c -m 644 'sample_map.csv' '/usr/share/alsa/speaker-test/sample_map.csv'
test -z "/usr/share/sounds/alsa" || mkdir -p -- "/usr/share/sounds/alsa"
 /usr/bin/install -c -m 644 'Front_Left.wav' '/usr/share/sounds/alsa/Front_Left.wav'
 /usr/bin/install -c -m 644 'Rear_Center.wav' '/usr/share/sounds/alsa/Rear_Center.wav'
 /usr/bin/install -c -m 644 'Rear_Right.wav' '/usr/share/sounds/alsa/Rear_Right.wav'
 /usr/bin/install -c -m 644 'Side_Right.wav' '/usr/share/sounds/alsa/Side_Right.wav'
 /usr/bin/install -c -m 644 'Front_Center.wav' '/usr/share/sounds/alsa/Front_Center.wav'
 /usr/bin/install -c -m 644 'Front_Right.wav' '/usr/share/sounds/alsa/Front_Right.wav'
 /usr/bin/install -c -m 644 'Noise.wav' '/usr/share/sounds/alsa/Noise.wav'
 /usr/bin/install -c -m 644 'Rear_Left.wav' '/usr/share/sounds/alsa/Rear_Left.wav'
 /usr/bin/install -c -m 644 'Side_Left.wav' '/usr/share/sounds/alsa/Side_Left.wav'
make[3]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/speaker-test/samples »
make[2]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/speaker-test/samples »
make[2]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/speaker-test »
make[3]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/speaker-test »
test -z "/usr/bin" || mkdir -p -- "/usr/bin"
  /usr/bin/install -c 'speaker-test' '/usr/bin/speaker-test'
test -z "/usr/share/man/man1" || mkdir -p -- "/usr/share/man/man1"
 /usr/bin/install -c -m 644 './speaker-test.1' '/usr/share/man/man1/speaker-test.1'
make[3]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/speaker-test »
make[2]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/speaker-test »
make[1]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/speaker-test »
Making install in seq
make[1]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/seq »
Making install in aconnect
make[2]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/seq/aconnect »
make[3]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/seq/aconnect »
test -z "/usr/bin" || mkdir -p -- "/usr/bin"
  /usr/bin/install -c 'aconnect' '/usr/bin/aconnect'
test -z "/usr/share/man/man1" || mkdir -p -- "/usr/share/man/man1"
 /usr/bin/install -c -m 644 './aconnect.1' '/usr/share/man/man1/aconnect.1'
make[3]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/seq/aconnect »
make[2]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/seq/aconnect »
Making install in aplaymidi
make[2]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/seq/aplaymidi »
make[3]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/seq/aplaymidi »
test -z "/usr/bin" || mkdir -p -- "/usr/bin"
  /usr/bin/install -c 'aplaymidi' '/usr/bin/aplaymidi'
  /usr/bin/install -c 'arecordmidi' '/usr/bin/arecordmidi'
test -z "/usr/share/man/man1" || mkdir -p -- "/usr/share/man/man1"
 /usr/bin/install -c -m 644 './aplaymidi.1' '/usr/share/man/man1/aplaymidi.1'
 /usr/bin/install -c -m 644 './arecordmidi.1' '/usr/share/man/man1/arecordmidi.1'
make[3]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/seq/aplaymidi »
make[2]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/seq/aplaymidi »
Making install in aseqdump
make[2]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/seq/aseqdump »
make[3]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/seq/aseqdump »
test -z "/usr/bin" || mkdir -p -- "/usr/bin"
  /usr/bin/install -c 'aseqdump' '/usr/bin/aseqdump'
test -z "/usr/share/man/man1" || mkdir -p -- "/usr/share/man/man1"
 /usr/bin/install -c -m 644 './aseqdump.1' '/usr/share/man/man1/aseqdump.1'
make[3]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/seq/aseqdump »
make[2]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/seq/aseqdump »
Making install in aseqnet
make[2]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/seq/aseqnet »
make[3]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/seq/aseqnet »
test -z "/usr/bin" || mkdir -p -- "/usr/bin"
  /usr/bin/install -c 'aseqnet' '/usr/bin/aseqnet'
test -z "/usr/share/man/man1" || mkdir -p -- "/usr/share/man/man1"
 /usr/bin/install -c -m 644 './aseqnet.1' '/usr/share/man/man1/aseqnet.1'
make[3]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/seq/aseqnet »
make[2]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/seq/aseqnet »
make[2]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/seq »
make[3]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/seq »
make[3]: Rien à faire pour « install-exec-am ».
make[3]: Rien à faire pour « install-data-am ».
make[3]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/seq »
make[2]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/seq »
make[1]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/seq »
make[1]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20 »
make[2]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20 »
make[2]: Rien à faire pour « install-exec-am ».
make[2]: Rien à faire pour « install-data-am ».
make[2]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20 »
make[1]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20 »
rabgye@ubuntumaya:~/alsa-utils-1.0.20$ rm -f ~/alsa-driver*
rm: ne peut enlever `/home/rabgye/alsa-driver-1.0.20': est un dossier
rabgye@ubuntumaya:~/alsa-utils-1.0.20$ rm -f ~/alsa-lib*
rm: ne peut enlever `/home/rabgye/alsa-lib-1.0.20': est un dossier
rabgye@ubuntumaya:~/alsa-utils-1.0.20$ rm -f ~/alsa-utils*
rm: ne peut enlever `/home/rabgye/alsa-utils-1.0.20': est un dossier
rabgye@ubuntumaya:~/alsa-utils-1.0.20$ 


































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































make[1]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/amixer »
if gcc -DHAVE_CONFIG_H -I. -I. -I../include -I../include    -g -O2 -MT amixer.o -MD -MP -MF ".deps/amixer.Tpo" -c -o amixer.o amixer.c; \
    then mv -f ".deps/amixer.Tpo" ".deps/amixer.Po"; else rm -f ".deps/amixer.Tpo"; exit 1; fi
amixer.c: In function ‘get_integer’:
amixer.c:244: attention : ignoring return value of ‘strtol’, declared with attribute warn_unused_result
amixer.c: In function ‘get_integer64’:
amixer.c:272: attention : ignoring return value of ‘strtol’, declared with attribute warn_unused_result
amixer.c: In function ‘set_volume_simple’:
amixer.c:358: attention : ignoring return value of ‘strtol’, declared with attribute warn_unused_result
gcc  -g -O2   -o amixer  amixer.o -lm -lasound -lm -ldl -lpthread
make[1]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/amixer »
Making all in amidi
make[1]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/amidi »
if gcc -DHAVE_CONFIG_H -I. -I. -I../include -I../include    -g -O2 -MT amidi.o -MD -MP -MF ".deps/amidi.Tpo" -c -o amidi.o amidi.c; \
    then mv -f ".deps/amidi.Tpo" ".deps/amidi.Po"; else rm -f ".deps/amidi.Tpo"; exit 1; fi
amidi.c: In function ‘main’:
amidi.c:658: attention : ignoring return value of ‘write’, declared with attribute warn_unused_result
gcc  -g -O2   -o amidi  amidi.o  -lasound -lm -ldl -lpthread
make[1]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/amidi »
Making all in alsaconf
make[1]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/alsaconf »
Making all in po
make[2]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/alsaconf/po »
35 messages traduits, 1 message non traduit.
34 messages traduits, 1 traduction approximative, 1 message non traduit.
make[2]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/alsaconf/po »
make[2]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/alsaconf »
make[2]: Rien à faire pour « all-am ».
make[2]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/alsaconf »
make[1]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/alsaconf »
Making all in aplay
make[1]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/aplay »
if gcc -DHAVE_CONFIG_H -I. -I. -I../include -I../include    -g -O2 -MT aplay.o -MD -MP -MF ".deps/aplay.Tpo" -c -o aplay.o aplay.c; \
    then mv -f ".deps/aplay.Tpo" ".deps/aplay.Po"; else rm -f ".deps/aplay.Tpo"; exit 1; fi
aplay.c: In function ‘end_voc’:
aplay.c:2158: attention : ignoring return value of ‘write’, declared with attribute warn_unused_result
aplay.c: In function ‘end_wave’:
aplay.c:2178: attention : ignoring return value of ‘write’, declared with attribute warn_unused_result
aplay.c:2180: attention : ignoring return value of ‘write’, declared with attribute warn_unused_result
aplay.c: In function ‘end_au’:
aplay.c:2193: attention : ignoring return value of ‘write’, declared with attribute warn_unused_result
gcc  -g -O2   -o aplay  aplay.o  -lrt -lasound -lm -ldl -lpthread
make[1]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/aplay »
Making all in iecset
make[1]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/iecset »
if gcc -DHAVE_CONFIG_H -I. -I. -I../include -I../include    -g -O2 -MT iecset.o -MD -MP -MF ".deps/iecset.Tpo" -c -o iecset.o iecset.c; \
    then mv -f ".deps/iecset.Tpo" ".deps/iecset.Po"; else rm -f ".deps/iecset.Tpo"; exit 1; fi
if gcc -DHAVE_CONFIG_H -I. -I. -I../include -I../include    -g -O2 -MT iecbits.o -MD -MP -MF ".deps/iecbits.Tpo" -c -o iecbits.o iecbits.c; \
    then mv -f ".deps/iecbits.Tpo" ".deps/iecbits.Po"; else rm -f ".deps/iecbits.Tpo"; exit 1; fi
gcc  -g -O2   -o iecset  iecset.o iecbits.o -lm -lasound -lm -ldl -lpthread
make[1]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/iecset »
Making all in speaker-test
make[1]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/speaker-test »
Making all in samples
make[2]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/speaker-test/samples »
make[2]: Rien à faire pour « all ».
make[2]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/speaker-test/samples »
make[2]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/speaker-test »
if gcc -DHAVE_CONFIG_H -I. -I. -I../include -I../include    -g -O2 -MT speaker-test.o -MD -MP -MF ".deps/speaker-test.Tpo" -c -o speaker-test.o speaker-test.c; \
    then mv -f ".deps/speaker-test.Tpo" ".deps/speaker-test.Po"; else rm -f ".deps/speaker-test.Tpo"; exit 1; fi
if gcc -DHAVE_CONFIG_H -I. -I. -I../include -I../include    -g -O2 -MT pink.o -MD -MP -MF ".deps/pink.Tpo" -c -o pink.o pink.c; \
    then mv -f ".deps/pink.Tpo" ".deps/pink.Po"; else rm -f ".deps/pink.Tpo"; exit 1; fi
gcc  -g -O2   -o speaker-test  speaker-test.o pink.o  -lm -lasound -lm -ldl -lpthread
make[2]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/speaker-test »
make[1]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/speaker-test »
Making all in seq
make[1]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/seq »
Making all in aconnect
make[2]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/seq/aconnect »
if gcc -DHAVE_CONFIG_H -I. -I. -I../../include -I../../include    -g -O2 -MT aconnect.o -MD -MP -MF ".deps/aconnect.Tpo" -c -o aconnect.o aconnect.c; \
    then mv -f ".deps/aconnect.Tpo" ".deps/aconnect.Po"; else rm -f ".deps/aconnect.Tpo"; exit 1; fi
gcc  -g -O2   -o aconnect  aconnect.o  -lasound -lm -ldl -lpthread
make[2]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/seq/aconnect »
Making all in aplaymidi
make[2]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/seq/aplaymidi »
if gcc -DHAVE_CONFIG_H -I. -I. -I../../include -I../../include    -g -O2 -MT aplaymidi.o -MD -MP -MF ".deps/aplaymidi.Tpo" -c -o aplaymidi.o aplaymidi.c; \
    then mv -f ".deps/aplaymidi.Tpo" ".deps/aplaymidi.Po"; else rm -f ".deps/aplaymidi.Tpo"; exit 1; fi
gcc  -g -O2   -o aplaymidi  aplaymidi.o  -lasound -lm -ldl -lpthread
if gcc -DHAVE_CONFIG_H -I. -I. -I../../include -I../../include    -g -O2 -MT arecordmidi.o -MD -MP -MF ".deps/arecordmidi.Tpo" -c -o arecordmidi.o arecordmidi.c; \
    then mv -f ".deps/arecordmidi.Tpo" ".deps/arecordmidi.Po"; else rm -f ".deps/arecordmidi.Tpo"; exit 1; fi
gcc  -g -O2   -o arecordmidi  arecordmidi.o  -lasound -lm -ldl -lpthread
make[2]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/seq/aplaymidi »
Making all in aseqdump
make[2]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/seq/aseqdump »
if gcc -DHAVE_CONFIG_H -I. -I. -I../../include -I../../include    -g -O2 -MT aseqdump.o -MD -MP -MF ".deps/aseqdump.Tpo" -c -o aseqdump.o aseqdump.c; \
    then mv -f ".deps/aseqdump.Tpo" ".deps/aseqdump.Po"; else rm -f ".deps/aseqdump.Tpo"; exit 1; fi
gcc  -g -O2   -o aseqdump  aseqdump.o  -lasound -lm -ldl -lpthread
make[2]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/seq/aseqdump »
Making all in aseqnet
make[2]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/seq/aseqnet »
if gcc -DHAVE_CONFIG_H -I. -I. -I../../include -I../../include    -g -O2 -MT aseqnet.o -MD -MP -MF ".deps/aseqnet.Tpo" -c -o aseqnet.o aseqnet.c; \
    then mv -f ".deps/aseqnet.Tpo" ".deps/aseqnet.Po"; else rm -f ".deps/aseqnet.Tpo"; exit 1; fi
aseqnet.c: In function ‘flush_writebuf’:
aseqnet.c:495: attention : ignoring return value of ‘write’, declared with attribute warn_unused_result
gcc  -g -O2   -o aseqnet  aseqnet.o  -lasound -lm -ldl -lpthread
make[2]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/seq/aseqnet »
make[2]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/seq »
make[2]: Rien à faire pour « all-am ».
make[2]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/seq »
make[1]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/seq »
make[1]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20 »
make[1]: Rien à faire pour « all-am ».
make[1]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20 »
rabgye@ubuntumaya:~/alsa-utils-1.0.20$ sudo make
Making all in include
make[1]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/include »
make  all-am
make[2]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/include »
make[2]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/include »
make[1]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/include »
Making all in alsactl
make[1]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/alsactl »
Making all in init
make[2]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/alsactl/init »
make[2]: Rien à faire pour « all ».
make[2]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/alsactl/init »
make[2]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/alsactl »
make[2]: Rien à faire pour « all-am ».
make[2]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/alsactl »
make[1]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/alsactl »
Making all in utils
make[1]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/utils »
make[1]: Rien à faire pour « all ».
make[1]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/utils »
Making all in m4
make[1]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/m4 »
make[1]: Rien à faire pour « all ».
make[1]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/m4 »
Making all in po
make[1]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/po »
make[1]: Rien à faire pour « all ».
make[1]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/po »
Making all in alsamixer
make[1]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/alsamixer »
make[1]: Rien à faire pour « all ».
make[1]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/alsamixer »
Making all in amixer
make[1]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/amixer »
make[1]: Rien à faire pour « all ».
make[1]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/amixer »
Making all in amidi
make[1]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/amidi »
make[1]: Rien à faire pour « all ».
make[1]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/amidi »
Making all in alsaconf
make[1]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/alsaconf »
Making all in po
make[2]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/alsaconf/po »
make[2]: Rien à faire pour « all ».
make[2]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/alsaconf/po »
make[2]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/alsaconf »
make[2]: Rien à faire pour « all-am ».
make[2]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/alsaconf »
make[1]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/alsaconf »
Making all in aplay
make[1]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/aplay »
make[1]: Rien à faire pour « all ».
make[1]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/aplay »
Making all in iecset
make[1]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/iecset »
make[1]: Rien à faire pour « all ».
make[1]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/iecset »
Making all in speaker-test
make[1]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/speaker-test »
Making all in samples
make[2]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/speaker-test/samples »
make[2]: Rien à faire pour « all ».
make[2]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/speaker-test/samples »
make[2]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/speaker-test »
make[2]: Rien à faire pour « all-am ».
make[2]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/speaker-test »
make[1]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/speaker-test »
Making all in seq
make[1]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/seq »
Making all in aconnect
make[2]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/seq/aconnect »
make[2]: Rien à faire pour « all ».
make[2]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/seq/aconnect »
Making all in aplaymidi
make[2]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/seq/aplaymidi »
make[2]: Rien à faire pour « all ».
make[2]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/seq/aplaymidi »
Making all in aseqdump
make[2]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/seq/aseqdump »
make[2]: Rien à faire pour « all ».
make[2]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/seq/aseqdump »
Making all in aseqnet
make[2]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/seq/aseqnet »
make[2]: Rien à faire pour « all ».
make[2]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/seq/aseqnet »
make[2]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/seq »
make[2]: Rien à faire pour « all-am ».
make[2]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/seq »
make[1]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/seq »
make[1]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20 »
make[1]: Rien à faire pour « all-am ».
make[1]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20 »
rabgye@ubuntumaya:~/alsa-utils-1.0.20$ sudo make install
Making install in include
make[1]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/include »
make[2]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/include »
make[2]: Rien à faire pour « install-exec-am ».
make[2]: Rien à faire pour « install-data-am ».
make[2]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/include »
make[1]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/include »
Making install in alsactl
make[1]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/alsactl »
Making install in init
make[2]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/alsactl/init »
make[3]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/alsactl/init »
make[3]: Rien à faire pour « install-exec-am ».
test -z "/usr/share/alsa/init" || mkdir -p -- "/usr/share/alsa/init"
 /usr/bin/install -c -m 644 '00main' '/usr/share/alsa/init/00main'
 /usr/bin/install -c -m 644 'default' '/usr/share/alsa/init/default'
 /usr/bin/install -c -m 644 'help' '/usr/share/alsa/init/help'
 /usr/bin/install -c -m 644 'info' '/usr/share/alsa/init/info'
 /usr/bin/install -c -m 644 'test' '/usr/share/alsa/init/test'
 /usr/bin/install -c -m 644 'hda' '/usr/share/alsa/init/hda'
make[3]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/alsactl/init »
make[2]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/alsactl/init »
make[2]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/alsactl »
make[3]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/alsactl »
test -z "/usr/sbin" || mkdir -p -- "/usr/sbin"
  /usr/bin/install -c 'alsactl' '/usr/sbin/alsactl'
test -z "/usr/share/man/man1" || mkdir -p -- "/usr/share/man/man1"
 /usr/bin/install -c -m 644 './alsactl.1' '/usr/share/man/man1/alsactl.1'
test -z "/usr/share/man/man7" || mkdir -p -- "/usr/share/man/man7"
 /usr/bin/install -c -m 644 './alsactl_init.7' '/usr/share/man/man7/alsactl_init.7'
make[3]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/alsactl »
make[2]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/alsactl »
make[1]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/alsactl »
Making install in utils
make[1]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/utils »
make[2]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/utils »
make[2]: Rien à faire pour « install-exec-am ».
make[2]: Rien à faire pour « install-data-am ».
make[2]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/utils »
make[1]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/utils »
Making install in m4
make[1]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/m4 »
make[2]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/m4 »
make[2]: Rien à faire pour « install-exec-am ».
make[2]: Rien à faire pour « install-data-am ».
make[2]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/m4 »
make[1]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/m4 »
Making install in po
make[1]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/po »
mkdir -p -- /usr/share
installing ja.gmo as /usr/share/locale/ja/LC_MESSAGES/alsa-utils.mo
if test "alsa-utils" = "gettext-tools"; then \
      mkdir -p -- /usr/share/gettext/po; \
      for file in Makefile.in.in remove-potcdate.sin quot.sed boldquot.sed [EMAIL="en@quot.header"]en@quot.header[/EMAIL] [EMAIL="en@boldquot.header"]en@boldquot.header[/EMAIL] insert-header.sin Rules-quot   Makevars.template; do \
        /usr/bin/install -c -m 644 ./$file \
                /usr/share/gettext/po/$file; \
      done; \
      for file in Makevars; do \
        rm -f /usr/share/gettext/po/$file; \
      done; \
    else \
      : ; \
    fi
make[1]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/po »
Making install in alsamixer
make[1]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/alsamixer »
make[2]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/alsamixer »
test -z "/usr/bin" || mkdir -p -- "/usr/bin"
  /usr/bin/install -c 'alsamixer' '/usr/bin/alsamixer'
test -z "/usr/share/man/man1" || mkdir -p -- "/usr/share/man/man1"
 /usr/bin/install -c -m 644 './alsamixer.1' '/usr/share/man/man1/alsamixer.1'
make[2]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/alsamixer »
make[1]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/alsamixer »
Making install in amixer
make[1]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/amixer »
make[2]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/amixer »
test -z "/usr/bin" || mkdir -p -- "/usr/bin"
  /usr/bin/install -c 'amixer' '/usr/bin/amixer'
test -z "/usr/share/man/man1" || mkdir -p -- "/usr/share/man/man1"
 /usr/bin/install -c -m 644 './amixer.1' '/usr/share/man/man1/amixer.1'
make[2]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/amixer »
make[1]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/amixer »
Making install in amidi
make[1]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/amidi »
make[2]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/amidi »
test -z "/usr/bin" || mkdir -p -- "/usr/bin"
  /usr/bin/install -c 'amidi' '/usr/bin/amidi'
test -z "/usr/share/man/man1" || mkdir -p -- "/usr/share/man/man1"
 /usr/bin/install -c -m 644 './amidi.1' '/usr/share/man/man1/amidi.1'
make[2]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/amidi »
make[1]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/amidi »
Making install in alsaconf
make[1]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/alsaconf »
Making install in po
make[2]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/alsaconf/po »
mkdir -p -- /usr/share
make[2]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/alsaconf/po »
make[2]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/alsaconf »
make[3]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/alsaconf »
test -z "/usr/sbin" || mkdir -p -- "/usr/sbin"
 /usr/bin/install -c 'alsaconf' '/usr/sbin/alsaconf'
 /usr/bin/install -c -m 644 alsaconf.8 /usr/share/man/man8/alsaconf.8
 /usr/bin/install -c -m 644 alsaconf.fr.8 /usr/share/man/fr/man8/alsaconf.8
make[3]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/alsaconf »
make[2]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/alsaconf »
make[1]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/alsaconf »
Making install in aplay
make[1]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/aplay »
make[2]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/aplay »
test -z "/usr/bin" || mkdir -p -- "/usr/bin"
  /usr/bin/install -c 'aplay' '/usr/bin/aplay'
make  install-exec-hook
make[3]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/aplay »
rm -f arecord
ln -s aplay arecord
rm -f /usr/bin/arecord
(cd /usr/bin && ln -s aplay arecord)
make[3]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/aplay »
test -z "/usr/share/man/man1" || mkdir -p -- "/usr/share/man/man1"
 /usr/bin/install -c -m 644 './aplay.1' '/usr/share/man/man1/aplay.1'
 /usr/bin/install -c -m 644 './arecord.1' '/usr/share/man/man1/arecord.1'
make  install-data-hook
make[3]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/aplay »
rm -f /usr/share/man/man1/arecord.1
(cd /usr/share/man/man1 && ln -s aplay.1 arecord.1)
make[3]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/aplay »
make[2]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/aplay »
make[1]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/aplay »
Making install in iecset
make[1]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/iecset »
make[2]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/iecset »
test -z "/usr/bin" || mkdir -p -- "/usr/bin"
  /usr/bin/install -c 'iecset' '/usr/bin/iecset'
test -z "/usr/share/man/man1" || mkdir -p -- "/usr/share/man/man1"
 /usr/bin/install -c -m 644 './iecset.1' '/usr/share/man/man1/iecset.1'
make[2]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/iecset »
make[1]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/iecset »
Making install in speaker-test
make[1]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/speaker-test »
Making install in samples
make[2]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/speaker-test/samples »
make[3]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/speaker-test/samples »
make[3]: Rien à faire pour « install-exec-am ».
test -z "/usr/share/alsa/speaker-test" || mkdir -p -- "/usr/share/alsa/speaker-test"
 /usr/bin/install -c -m 644 'sample_map.csv' '/usr/share/alsa/speaker-test/sample_map.csv'
test -z "/usr/share/sounds/alsa" || mkdir -p -- "/usr/share/sounds/alsa"
 /usr/bin/install -c -m 644 'Front_Left.wav' '/usr/share/sounds/alsa/Front_Left.wav'
 /usr/bin/install -c -m 644 'Rear_Center.wav' '/usr/share/sounds/alsa/Rear_Center.wav'
 /usr/bin/install -c -m 644 'Rear_Right.wav' '/usr/share/sounds/alsa/Rear_Right.wav'
 /usr/bin/install -c -m 644 'Side_Right.wav' '/usr/share/sounds/alsa/Side_Right.wav'
 /usr/bin/install -c -m 644 'Front_Center.wav' '/usr/share/sounds/alsa/Front_Center.wav'
 /usr/bin/install -c -m 644 'Front_Right.wav' '/usr/share/sounds/alsa/Front_Right.wav'
 /usr/bin/install -c -m 644 'Noise.wav' '/usr/share/sounds/alsa/Noise.wav'
 /usr/bin/install -c -m 644 'Rear_Left.wav' '/usr/share/sounds/alsa/Rear_Left.wav'
 /usr/bin/install -c -m 644 'Side_Left.wav' '/usr/share/sounds/alsa/Side_Left.wav'
make[3]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/speaker-test/samples »
make[2]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/speaker-test/samples »
make[2]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/speaker-test »
make[3]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/speaker-test »
test -z "/usr/bin" || mkdir -p -- "/usr/bin"
  /usr/bin/install -c 'speaker-test' '/usr/bin/speaker-test'
test -z "/usr/share/man/man1" || mkdir -p -- "/usr/share/man/man1"
 /usr/bin/install -c -m 644 './speaker-test.1' '/usr/share/man/man1/speaker-test.1'
make[3]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/speaker-test »
make[2]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/speaker-test »
make[1]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/speaker-test »
Making install in seq
make[1]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/seq »
Making install in aconnect
make[2]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/seq/aconnect »
make[3]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/seq/aconnect »
test -z "/usr/bin" || mkdir -p -- "/usr/bin"
  /usr/bin/install -c 'aconnect' '/usr/bin/aconnect'
test -z "/usr/share/man/man1" || mkdir -p -- "/usr/share/man/man1"
 /usr/bin/install -c -m 644 './aconnect.1' '/usr/share/man/man1/aconnect.1'
make[3]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/seq/aconnect »
make[2]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/seq/aconnect »
Making install in aplaymidi
make[2]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/seq/aplaymidi »
make[3]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/seq/aplaymidi »
test -z "/usr/bin" || mkdir -p -- "/usr/bin"
  /usr/bin/install -c 'aplaymidi' '/usr/bin/aplaymidi'
  /usr/bin/install -c 'arecordmidi' '/usr/bin/arecordmidi'
test -z "/usr/share/man/man1" || mkdir -p -- "/usr/share/man/man1"
 /usr/bin/install -c -m 644 './aplaymidi.1' '/usr/share/man/man1/aplaymidi.1'
 /usr/bin/install -c -m 644 './arecordmidi.1' '/usr/share/man/man1/arecordmidi.1'
make[3]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/seq/aplaymidi »
make[2]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/seq/aplaymidi »
Making install in aseqdump
make[2]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/seq/aseqdump »
make[3]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/seq/aseqdump »
test -z "/usr/bin" || mkdir -p -- "/usr/bin"
  /usr/bin/install -c 'aseqdump' '/usr/bin/aseqdump'
test -z "/usr/share/man/man1" || mkdir -p -- "/usr/share/man/man1"
 /usr/bin/install -c -m 644 './aseqdump.1' '/usr/share/man/man1/aseqdump.1'
make[3]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/seq/aseqdump »
make[2]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/seq/aseqdump »
Making install in aseqnet
make[2]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/seq/aseqnet »
make[3]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/seq/aseqnet »
test -z "/usr/bin" || mkdir -p -- "/usr/bin"
  /usr/bin/install -c 'aseqnet' '/usr/bin/aseqnet'
test -z "/usr/share/man/man1" || mkdir -p -- "/usr/share/man/man1"
 /usr/bin/install -c -m 644 './aseqnet.1' '/usr/share/man/man1/aseqnet.1'
make[3]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/seq/aseqnet »
make[2]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/seq/aseqnet »
make[2]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/seq »
make[3]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/seq »
make[3]: Rien à faire pour « install-exec-am ».
make[3]: Rien à faire pour « install-data-am ».
make[3]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/seq »
make[2]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/seq »
make[1]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/seq »
make[1]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20 »
make[2]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20 »
make[2]: Rien à faire pour « install-exec-am ».
make[2]: Rien à faire pour « install-data-am ».
make[2]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20 »
make[1]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20 »
rabgye@ubuntumaya:~/alsa-utils-1.0.20$ rm -f ~/alsa-driver*
rm: ne peut enlever `/home/rabgye/alsa-driver-1.0.20': est un dossier
rabgye@ubuntumaya:~/alsa-utils-1.0.20$ rm -f ~/alsa-lib*
rm: ne peut enlever `/home/rabgye/alsa-lib-1.0.20': est un dossier
rabgye@ubuntumaya:~/alsa-utils-1.0.20$ rm -f ~/alsa-utils*
rm: ne peut enlever `/home/rabgye/alsa-utils-1.0.20': est un dossier
rabgye@ubuntumaya:~/alsa-utils-1.0.20$ 


































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































make[1]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/amixer »
if gcc -DHAVE_CONFIG_H -I. -I. -I../include -I../include    -g -O2 -MT amixer.o -MD -MP -MF ".deps/amixer.Tpo" -c -o amixer.o amixer.c; \
    then mv -f ".deps/amixer.Tpo" ".deps/amixer.Po"; else rm -f ".deps/amixer.Tpo"; exit 1; fi
amixer.c: In function ‘get_integer’:
amixer.c:244: attention : ignoring return value of ‘strtol’, declared with attribute warn_unused_result
amixer.c: In function ‘get_integer64’:
amixer.c:272: attention : ignoring return value of ‘strtol’, declared with attribute warn_unused_result
amixer.c: In function ‘set_volume_simple’:
amixer.c:358: attention : ignoring return value of ‘strtol’, declared with attribute warn_unused_result
gcc  -g -O2   -o amixer  amixer.o -lm -lasound -lm -ldl -lpthread
make[1]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/amixer »
Making all in amidi
make[1]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/amidi »
if gcc -DHAVE_CONFIG_H -I. -I. -I../include -I../include    -g -O2 -MT amidi.o -MD -MP -MF ".deps/amidi.Tpo" -c -o amidi.o amidi.c; \
    then mv -f ".deps/amidi.Tpo" ".deps/amidi.Po"; else rm -f ".deps/amidi.Tpo"; exit 1; fi
amidi.c: In function ‘main’:
amidi.c:658: attention : ignoring return value of ‘write’, declared with attribute warn_unused_result
gcc  -g -O2   -o amidi  amidi.o  -lasound -lm -ldl -lpthread
make[1]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/amidi »
Making all in alsaconf
make[1]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/alsaconf »
Making all in po
make[2]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/alsaconf/po »
35 messages traduits, 1 message non traduit.
34 messages traduits, 1 traduction approximative, 1 message non traduit.
make[2]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/alsaconf/po »
make[2]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/alsaconf »
make[2]: Rien à faire pour « all-am ».
make[2]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/alsaconf »
make[1]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/alsaconf »
Making all in aplay
make[1]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/aplay »
if gcc -DHAVE_CONFIG_H -I. -I. -I../include -I../include    -g -O2 -MT aplay.o -MD -MP -MF ".deps/aplay.Tpo" -c -o aplay.o aplay.c; \
    then mv -f ".deps/aplay.Tpo" ".deps/aplay.Po"; else rm -f ".deps/aplay.Tpo"; exit 1; fi
aplay.c: In function ‘end_voc’:
aplay.c:2158: attention : ignoring return value of ‘write’, declared with attribute warn_unused_result
aplay.c: In function ‘end_wave’:
aplay.c:2178: attention : ignoring return value of ‘write’, declared with attribute warn_unused_result
aplay.c:2180: attention : ignoring return value of ‘write’, declared with attribute warn_unused_result
aplay.c: In function ‘end_au’:
aplay.c:2193: attention : ignoring return value of ‘write’, declared with attribute warn_unused_result
gcc  -g -O2   -o aplay  aplay.o  -lrt -lasound -lm -ldl -lpthread
make[1]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/aplay »
Making all in iecset
make[1]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/iecset »
if gcc -DHAVE_CONFIG_H -I. -I. -I../include -I../include    -g -O2 -MT iecset.o -MD -MP -MF ".deps/iecset.Tpo" -c -o iecset.o iecset.c; \
    then mv -f ".deps/iecset.Tpo" ".deps/iecset.Po"; else rm -f ".deps/iecset.Tpo"; exit 1; fi
if gcc -DHAVE_CONFIG_H -I. -I. -I../include -I../include    -g -O2 -MT iecbits.o -MD -MP -MF ".deps/iecbits.Tpo" -c -o iecbits.o iecbits.c; \
    then mv -f ".deps/iecbits.Tpo" ".deps/iecbits.Po"; else rm -f ".deps/iecbits.Tpo"; exit 1; fi
gcc  -g -O2   -o iecset  iecset.o iecbits.o -lm -lasound -lm -ldl -lpthread
make[1]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/iecset »
Making all in speaker-test
make[1]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/speaker-test »
Making all in samples
make[2]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/speaker-test/samples »
make[2]: Rien à faire pour « all ».
make[2]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/speaker-test/samples »
make[2]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/speaker-test »
if gcc -DHAVE_CONFIG_H -I. -I. -I../include -I../include    -g -O2 -MT speaker-test.o -MD -MP -MF ".deps/speaker-test.Tpo" -c -o speaker-test.o speaker-test.c; \
    then mv -f ".deps/speaker-test.Tpo" ".deps/speaker-test.Po"; else rm -f ".deps/speaker-test.Tpo"; exit 1; fi
if gcc -DHAVE_CONFIG_H -I. -I. -I../include -I../include    -g -O2 -MT pink.o -MD -MP -MF ".deps/pink.Tpo" -c -o pink.o pink.c; \
    then mv -f ".deps/pink.Tpo" ".deps/pink.Po"; else rm -f ".deps/pink.Tpo"; exit 1; fi
gcc  -g -O2   -o speaker-test  speaker-test.o pink.o  -lm -lasound -lm -ldl -lpthread
make[2]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/speaker-test »
make[1]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/speaker-test »
Making all in seq
make[1]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/seq »
Making all in aconnect
make[2]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/seq/aconnect »
if gcc -DHAVE_CONFIG_H -I. -I. -I../../include -I../../include    -g -O2 -MT aconnect.o -MD -MP -MF ".deps/aconnect.Tpo" -c -o aconnect.o aconnect.c; \
    then mv -f ".deps/aconnect.Tpo" ".deps/aconnect.Po"; else rm -f ".deps/aconnect.Tpo"; exit 1; fi
gcc  -g -O2   -o aconnect  aconnect.o  -lasound -lm -ldl -lpthread
make[2]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/seq/aconnect »
Making all in aplaymidi
make[2]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/seq/aplaymidi »
if gcc -DHAVE_CONFIG_H -I. -I. -I../../include -I../../include    -g -O2 -MT aplaymidi.o -MD -MP -MF ".deps/aplaymidi.Tpo" -c -o aplaymidi.o aplaymidi.c; \
    then mv -f ".deps/aplaymidi.Tpo" ".deps/aplaymidi.Po"; else rm -f ".deps/aplaymidi.Tpo"; exit 1; fi
gcc  -g -O2   -o aplaymidi  aplaymidi.o  -lasound -lm -ldl -lpthread
if gcc -DHAVE_CONFIG_H -I. -I. -I../../include -I../../include    -g -O2 -MT arecordmidi.o -MD -MP -MF ".deps/arecordmidi.Tpo" -c -o arecordmidi.o arecordmidi.c; \
    then mv -f ".deps/arecordmidi.Tpo" ".deps/arecordmidi.Po"; else rm -f ".deps/arecordmidi.Tpo"; exit 1; fi
gcc  -g -O2   -o arecordmidi  arecordmidi.o  -lasound -lm -ldl -lpthread
make[2]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/seq/aplaymidi »
Making all in aseqdump
make[2]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/seq/aseqdump »
if gcc -DHAVE_CONFIG_H -I. -I. -I../../include -I../../include    -g -O2 -MT aseqdump.o -MD -MP -MF ".deps/aseqdump.Tpo" -c -o aseqdump.o aseqdump.c; \
    then mv -f ".deps/aseqdump.Tpo" ".deps/aseqdump.Po"; else rm -f ".deps/aseqdump.Tpo"; exit 1; fi
gcc  -g -O2   -o aseqdump  aseqdump.o  -lasound -lm -ldl -lpthread
make[2]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/seq/aseqdump »
Making all in aseqnet
make[2]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/seq/aseqnet »
if gcc -DHAVE_CONFIG_H -I. -I. -I../../include -I../../include    -g -O2 -MT aseqnet.o -MD -MP -MF ".deps/aseqnet.Tpo" -c -o aseqnet.o aseqnet.c; \
    then mv -f ".deps/aseqnet.Tpo" ".deps/aseqnet.Po"; else rm -f ".deps/aseqnet.Tpo"; exit 1; fi
aseqnet.c: In function ‘flush_writebuf’:
aseqnet.c:495: attention : ignoring return value of ‘write’, declared with attribute warn_unused_result
gcc  -g -O2   -o aseqnet  aseqnet.o  -lasound -lm -ldl -lpthread
make[2]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/seq/aseqnet »
make[2]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/seq »
make[2]: Rien à faire pour « all-am ».
make[2]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/seq »
make[1]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/seq »
make[1]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20 »
make[1]: Rien à faire pour « all-am ».
make[1]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20 »
rabgye@ubuntumaya:~/alsa-utils-1.0.20$ sudo make
Making all in include
make[1]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/include »
make  all-am
make[2]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/include »
make[2]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/include »
make[1]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/include »
Making all in alsactl
make[1]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/alsactl »
Making all in init
make[2]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/alsactl/init »
make[2]: Rien à faire pour « all ».
make[2]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/alsactl/init »
make[2]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/alsactl »
make[2]: Rien à faire pour « all-am ».
make[2]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/alsactl »
make[1]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/alsactl »
Making all in utils
make[1]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/utils »
make[1]: Rien à faire pour « all ».
make[1]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/utils »
Making all in m4
make[1]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/m4 »
make[1]: Rien à faire pour « all ».
make[1]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/m4 »
Making all in po
make[1]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/po »
make[1]: Rien à faire pour « all ».
make[1]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/po »
Making all in alsamixer
make[1]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/alsamixer »
make[1]: Rien à faire pour « all ».
make[1]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/alsamixer »
Making all in amixer
make[1]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/amixer »
make[1]: Rien à faire pour « all ».
make[1]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/amixer »
Making all in amidi
make[1]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/amidi »
make[1]: Rien à faire pour « all ».
make[1]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/amidi »
Making all in alsaconf
make[1]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/alsaconf »
Making all in po
make[2]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/alsaconf/po »
make[2]: Rien à faire pour « all ».
make[2]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/alsaconf/po »
make[2]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/alsaconf »
make[2]: Rien à faire pour « all-am ».
make[2]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/alsaconf »
make[1]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/alsaconf »
Making all in aplay
make[1]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/aplay »
make[1]: Rien à faire pour « all ».
make[1]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/aplay »
Making all in iecset
make[1]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/iecset »
make[1]: Rien à faire pour « all ».
make[1]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/iecset »
Making all in speaker-test
make[1]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/speaker-test »
Making all in samples
make[2]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/speaker-test/samples »
make[2]: Rien à faire pour « all ».
make[2]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/speaker-test/samples »
make[2]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/speaker-test »
make[2]: Rien à faire pour « all-am ».
make[2]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/speaker-test »
make[1]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/speaker-test »
Making all in seq
make[1]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/seq »
Making all in aconnect
make[2]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/seq/aconnect »
make[2]: Rien à faire pour « all ».
make[2]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/seq/aconnect »
Making all in aplaymidi
make[2]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/seq/aplaymidi »
make[2]: Rien à faire pour « all ».
make[2]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/seq/aplaymidi »
Making all in aseqdump
make[2]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/seq/aseqdump »
make[2]: Rien à faire pour « all ».
make[2]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/seq/aseqdump »
Making all in aseqnet
make[2]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/seq/aseqnet »
make[2]: Rien à faire pour « all ».
make[2]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/seq/aseqnet »
make[2]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/seq »
make[2]: Rien à faire pour « all-am ».
make[2]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/seq »
make[1]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/seq »
make[1]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20 »
make[1]: Rien à faire pour « all-am ».
make[1]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20 »
rabgye@ubuntumaya:~/alsa-utils-1.0.20$ sudo make install
Making install in include
make[1]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/include »
make[2]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/include »
make[2]: Rien à faire pour « install-exec-am ».
make[2]: Rien à faire pour « install-data-am ».
make[2]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/include »
make[1]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/include »
Making install in alsactl
make[1]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/alsactl »
Making install in init
make[2]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/alsactl/init »
make[3]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/alsactl/init »
make[3]: Rien à faire pour « install-exec-am ».
test -z "/usr/share/alsa/init" || mkdir -p -- "/usr/share/alsa/init"
 /usr/bin/install -c -m 644 '00main' '/usr/share/alsa/init/00main'
 /usr/bin/install -c -m 644 'default' '/usr/share/alsa/init/default'
 /usr/bin/install -c -m 644 'help' '/usr/share/alsa/init/help'
 /usr/bin/install -c -m 644 'info' '/usr/share/alsa/init/info'
 /usr/bin/install -c -m 644 'test' '/usr/share/alsa/init/test'
 /usr/bin/install -c -m 644 'hda' '/usr/share/alsa/init/hda'
make[3]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/alsactl/init »
make[2]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/alsactl/init »
make[2]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/alsactl »
make[3]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/alsactl »
test -z "/usr/sbin" || mkdir -p -- "/usr/sbin"
  /usr/bin/install -c 'alsactl' '/usr/sbin/alsactl'
test -z "/usr/share/man/man1" || mkdir -p -- "/usr/share/man/man1"
 /usr/bin/install -c -m 644 './alsactl.1' '/usr/share/man/man1/alsactl.1'
test -z "/usr/share/man/man7" || mkdir -p -- "/usr/share/man/man7"
 /usr/bin/install -c -m 644 './alsactl_init.7' '/usr/share/man/man7/alsactl_init.7'
make[3]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/alsactl »
make[2]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/alsactl »
make[1]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/alsactl »
Making install in utils
make[1]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/utils »
make[2]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/utils »
make[2]: Rien à faire pour « install-exec-am ».
make[2]: Rien à faire pour « install-data-am ».
make[2]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/utils »
make[1]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/utils »
Making install in m4
make[1]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/m4 »
make[2]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/m4 »
make[2]: Rien à faire pour « install-exec-am ».
make[2]: Rien à faire pour « install-data-am ».
make[2]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/m4 »
make[1]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/m4 »
Making install in po
make[1]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/po »
mkdir -p -- /usr/share
installing ja.gmo as /usr/share/locale/ja/LC_MESSAGES/alsa-utils.mo
if test "alsa-utils" = "gettext-tools"; then \
      mkdir -p -- /usr/share/gettext/po; \
      for file in Makefile.in.in remove-potcdate.sin quot.sed boldquot.sed [EMAIL="en@quot.header"]en@quot.header[/EMAIL] [EMAIL="en@boldquot.header"]en@boldquot.header[/EMAIL] insert-header.sin Rules-quot   Makevars.template; do \
        /usr/bin/install -c -m 644 ./$file \
                /usr/share/gettext/po/$file; \
      done; \
      for file in Makevars; do \
        rm -f /usr/share/gettext/po/$file; \
      done; \
    else \
      : ; \
    fi
make[1]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/po »
Making install in alsamixer
make[1]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/alsamixer »
make[2]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/alsamixer »
test -z "/usr/bin" || mkdir -p -- "/usr/bin"
  /usr/bin/install -c 'alsamixer' '/usr/bin/alsamixer'
test -z "/usr/share/man/man1" || mkdir -p -- "/usr/share/man/man1"
 /usr/bin/install -c -m 644 './alsamixer.1' '/usr/share/man/man1/alsamixer.1'
make[2]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/alsamixer »
make[1]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/alsamixer »
Making install in amixer
make[1]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/amixer »
make[2]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/amixer »
test -z "/usr/bin" || mkdir -p -- "/usr/bin"
  /usr/bin/install -c 'amixer' '/usr/bin/amixer'
test -z "/usr/share/man/man1" || mkdir -p -- "/usr/share/man/man1"
 /usr/bin/install -c -m 644 './amixer.1' '/usr/share/man/man1/amixer.1'
make[2]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/amixer »
make[1]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/amixer »
Making install in amidi
make[1]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/amidi »
make[2]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/amidi »
test -z "/usr/bin" || mkdir -p -- "/usr/bin"
  /usr/bin/install -c 'amidi' '/usr/bin/amidi'
test -z "/usr/share/man/man1" || mkdir -p -- "/usr/share/man/man1"
 /usr/bin/install -c -m 644 './amidi.1' '/usr/share/man/man1/amidi.1'
make[2]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/amidi »
make[1]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/amidi »
Making install in alsaconf
make[1]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/alsaconf »
Making install in po
make[2]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/alsaconf/po »
mkdir -p -- /usr/share
make[2]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/alsaconf/po »
make[2]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/alsaconf »
make[3]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/alsaconf »
test -z "/usr/sbin" || mkdir -p -- "/usr/sbin"
 /usr/bin/install -c 'alsaconf' '/usr/sbin/alsaconf'
 /usr/bin/install -c -m 644 alsaconf.8 /usr/share/man/man8/alsaconf.8
 /usr/bin/install -c -m 644 alsaconf.fr.8 /usr/share/man/fr/man8/alsaconf.8
make[3]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/alsaconf »
make[2]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/alsaconf »
make[1]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/alsaconf »
Making install in aplay
make[1]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/aplay »
make[2]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/aplay »
test -z "/usr/bin" || mkdir -p -- "/usr/bin"
  /usr/bin/install -c 'aplay' '/usr/bin/aplay'
make  install-exec-hook
make[3]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/aplay »
rm -f arecord
ln -s aplay arecord
rm -f /usr/bin/arecord
(cd /usr/bin && ln -s aplay arecord)
make[3]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/aplay »
test -z "/usr/share/man/man1" || mkdir -p -- "/usr/share/man/man1"
 /usr/bin/install -c -m 644 './aplay.1' '/usr/share/man/man1/aplay.1'
 /usr/bin/install -c -m 644 './arecord.1' '/usr/share/man/man1/arecord.1'
make  install-data-hook
make[3]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/aplay »
rm -f /usr/share/man/man1/arecord.1
(cd /usr/share/man/man1 && ln -s aplay.1 arecord.1)
make[3]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/aplay »
make[2]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/aplay »
make[1]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/aplay »
Making install in iecset
make[1]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/iecset »
make[2]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/iecset »
test -z "/usr/bin" || mkdir -p -- "/usr/bin"
  /usr/bin/install -c 'iecset' '/usr/bin/iecset'
test -z "/usr/share/man/man1" || mkdir -p -- "/usr/share/man/man1"
 /usr/bin/install -c -m 644 './iecset.1' '/usr/share/man/man1/iecset.1'
make[2]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/iecset »
make[1]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/iecset »
Making install in speaker-test
make[1]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/speaker-test »
Making install in samples
make[2]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/speaker-test/samples »
make[3]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/speaker-test/samples »
make[3]: Rien à faire pour « install-exec-am ».
test -z "/usr/share/alsa/speaker-test" || mkdir -p -- "/usr/share/alsa/speaker-test"
 /usr/bin/install -c -m 644 'sample_map.csv' '/usr/share/alsa/speaker-test/sample_map.csv'
test -z "/usr/share/sounds/alsa" || mkdir -p -- "/usr/share/sounds/alsa"
 /usr/bin/install -c -m 644 'Front_Left.wav' '/usr/share/sounds/alsa/Front_Left.wav'
 /usr/bin/install -c -m 644 'Rear_Center.wav' '/usr/share/sounds/alsa/Rear_Center.wav'
 /usr/bin/install -c -m 644 'Rear_Right.wav' '/usr/share/sounds/alsa/Rear_Right.wav'
 /usr/bin/install -c -m 644 'Side_Right.wav' '/usr/share/sounds/alsa/Side_Right.wav'
 /usr/bin/install -c -m 644 'Front_Center.wav' '/usr/share/sounds/alsa/Front_Center.wav'
 /usr/bin/install -c -m 644 'Front_Right.wav' '/usr/share/sounds/alsa/Front_Right.wav'
 /usr/bin/install -c -m 644 'Noise.wav' '/usr/share/sounds/alsa/Noise.wav'
 /usr/bin/install -c -m 644 'Rear_Left.wav' '/usr/share/sounds/alsa/Rear_Left.wav'
 /usr/bin/install -c -m 644 'Side_Left.wav' '/usr/share/sounds/alsa/Side_Left.wav'
make[3]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/speaker-test/samples »
make[2]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/speaker-test/samples »
make[2]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/speaker-test »
make[3]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/speaker-test »
test -z "/usr/bin" || mkdir -p -- "/usr/bin"
  /usr/bin/install -c 'speaker-test' '/usr/bin/speaker-test'
test -z "/usr/share/man/man1" || mkdir -p -- "/usr/share/man/man1"
 /usr/bin/install -c -m 644 './speaker-test.1' '/usr/share/man/man1/speaker-test.1'
make[3]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/speaker-test »
make[2]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/speaker-test »
make[1]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/speaker-test »
Making install in seq
make[1]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/seq »
Making install in aconnect
make[2]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/seq/aconnect »
make[3]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/seq/aconnect »
test -z "/usr/bin" || mkdir -p -- "/usr/bin"
  /usr/bin/install -c 'aconnect' '/usr/bin/aconnect'
test -z "/usr/share/man/man1" || mkdir -p -- "/usr/share/man/man1"
 /usr/bin/install -c -m 644 './aconnect.1' '/usr/share/man/man1/aconnect.1'
make[3]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/seq/aconnect »
make[2]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/seq/aconnect »
Making install in aplaymidi
make[2]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/seq/aplaymidi »
make[3]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/seq/aplaymidi »
test -z "/usr/bin" || mkdir -p -- "/usr/bin"
  /usr/bin/install -c 'aplaymidi' '/usr/bin/aplaymidi'
  /usr/bin/install -c 'arecordmidi' '/usr/bin/arecordmidi'
test -z "/usr/share/man/man1" || mkdir -p -- "/usr/share/man/man1"
 /usr/bin/install -c -m 644 './aplaymidi.1' '/usr/share/man/man1/aplaymidi.1'
 /usr/bin/install -c -m 644 './arecordmidi.1' '/usr/share/man/man1/arecordmidi.1'
make[3]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/seq/aplaymidi »
make[2]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/seq/aplaymidi »
Making install in aseqdump
make[2]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/seq/aseqdump »
make[3]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/seq/aseqdump »
test -z "/usr/bin" || mkdir -p -- "/usr/bin"
  /usr/bin/install -c 'aseqdump' '/usr/bin/aseqdump'
test -z "/usr/share/man/man1" || mkdir -p -- "/usr/share/man/man1"
 /usr/bin/install -c -m 644 './aseqdump.1' '/usr/share/man/man1/aseqdump.1'
make[3]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/seq/aseqdump »
make[2]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/seq/aseqdump »
Making install in aseqnet
make[2]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/seq/aseqnet »
make[3]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/seq/aseqnet »
test -z "/usr/bin" || mkdir -p -- "/usr/bin"
  /usr/bin/install -c 'aseqnet' '/usr/bin/aseqnet'
test -z "/usr/share/man/man1" || mkdir -p -- "/usr/share/man/man1"
 /usr/bin/install -c -m 644 './aseqnet.1' '/usr/share/man/man1/aseqnet.1'
make[3]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/seq/aseqnet »
make[2]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/seq/aseqnet »
make[2]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/seq »
make[3]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/seq »
make[3]: Rien à faire pour « install-exec-am ».
make[3]: Rien à faire pour « install-data-am ».
make[3]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/seq »
make[2]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/seq »
make[1]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/seq »
make[1]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20 »
make[2]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20 »
make[2]: Rien à faire pour « install-exec-am ».
make[2]: Rien à faire pour « install-data-am ».
make[2]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20 »
make[1]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20 »
rabgye@ubuntumaya:~/alsa-utils-1.0.20$ rm -f ~/alsa-driver*
rm: ne peut enlever `/home/rabgye/alsa-driver-1.0.20': est un dossier
rabgye@ubuntumaya:~/alsa-utils-1.0.20$ rm -f ~/alsa-lib*
rm: ne peut enlever `/home/rabgye/alsa-lib-1.0.20': est un dossier
rabgye@ubuntumaya:~/alsa-utils-1.0.20$ rm -f ~/alsa-utils*
rm: ne peut enlever `/home/rabgye/alsa-utils-1.0.20': est un dossier
rabgye@ubuntumaya:~/alsa-utils-1.0.20$ 


































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































make[1]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/amixer »
if gcc -DHAVE_CONFIG_H -I. -I. -I../include -I../include    -g -O2 -MT amixer.o -MD -MP -MF ".deps/amixer.Tpo" -c -o amixer.o amixer.c; \
    then mv -f ".deps/amixer.Tpo" ".deps/amixer.Po"; else rm -f ".deps/amixer.Tpo"; exit 1; fi
amixer.c: In function ‘get_integer’:
amixer.c:244: attention : ignoring return value of ‘strtol’, declared with attribute warn_unused_result
amixer.c: In function ‘get_integer64’:
amixer.c:272: attention : ignoring return value of ‘strtol’, declared with attribute warn_unused_result
amixer.c: In function ‘set_volume_simple’:
amixer.c:358: attention : ignoring return value of ‘strtol’, declared with attribute warn_unused_result
gcc  -g -O2   -o amixer  amixer.o -lm -lasound -lm -ldl -lpthread
make[1]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/amixer »
Making all in amidi
make[1]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/amidi »
if gcc -DHAVE_CONFIG_H -I. -I. -I../include -I../include    -g -O2 -MT amidi.o -MD -MP -MF ".deps/amidi.Tpo" -c -o amidi.o amidi.c; \
    then mv -f ".deps/amidi.Tpo" ".deps/amidi.Po"; else rm -f ".deps/amidi.Tpo"; exit 1; fi
amidi.c: In function ‘main’:
amidi.c:658: attention : ignoring return value of ‘write’, declared with attribute warn_unused_result
gcc  -g -O2   -o amidi  amidi.o  -lasound -lm -ldl -lpthread
make[1]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/amidi »
Making all in alsaconf
make[1]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/alsaconf »
Making all in po
make[2]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/alsaconf/po »
35 messages traduits, 1 message non traduit.
34 messages traduits, 1 traduction approximative, 1 message non traduit.
make[2]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/alsaconf/po »
make[2]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/alsaconf »
make[2]: Rien à faire pour « all-am ».
make[2]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/alsaconf »
make[1]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/alsaconf »
Making all in aplay
make[1]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/aplay »
if gcc -DHAVE_CONFIG_H -I. -I. -I../include -I../include    -g -O2 -MT aplay.o -MD -MP -MF ".deps/aplay.Tpo" -c -o aplay.o aplay.c; \
    then mv -f ".deps/aplay.Tpo" ".deps/aplay.Po"; else rm -f ".deps/aplay.Tpo"; exit 1; fi
aplay.c: In function ‘end_voc’:
aplay.c:2158: attention : ignoring return value of ‘write’, declared with attribute warn_unused_result
aplay.c: In function ‘end_wave’:
aplay.c:2178: attention : ignoring return value of ‘write’, declared with attribute warn_unused_result
aplay.c:2180: attention : ignoring return value of ‘write’, declared with attribute warn_unused_result
aplay.c: In function ‘end_au’:
aplay.c:2193: attention : ignoring return value of ‘write’, declared with attribute warn_unused_result
gcc  -g -O2   -o aplay  aplay.o  -lrt -lasound -lm -ldl -lpthread
make[1]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/aplay »
Making all in iecset
make[1]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/iecset »
if gcc -DHAVE_CONFIG_H -I. -I. -I../include -I../include    -g -O2 -MT iecset.o -MD -MP -MF ".deps/iecset.Tpo" -c -o iecset.o iecset.c; \
    then mv -f ".deps/iecset.Tpo" ".deps/iecset.Po"; else rm -f ".deps/iecset.Tpo"; exit 1; fi
if gcc -DHAVE_CONFIG_H -I. -I. -I../include -I../include    -g -O2 -MT iecbits.o -MD -MP -MF ".deps/iecbits.Tpo" -c -o iecbits.o iecbits.c; \
    then mv -f ".deps/iecbits.Tpo" ".deps/iecbits.Po"; else rm -f ".deps/iecbits.Tpo"; exit 1; fi
gcc  -g -O2   -o iecset  iecset.o iecbits.o -lm -lasound -lm -ldl -lpthread
make[1]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/iecset »
Making all in speaker-test
make[1]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/speaker-test »
Making all in samples
make[2]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/speaker-test/samples »
make[2]: Rien à faire pour « all ».
make[2]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/speaker-test/samples »
make[2]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/speaker-test »
if gcc -DHAVE_CONFIG_H -I. -I. -I../include -I../include    -g -O2 -MT speaker-test.o -MD -MP -MF ".deps/speaker-test.Tpo" -c -o speaker-test.o speaker-test.c; \
    then mv -f ".deps/speaker-test.Tpo" ".deps/speaker-test.Po"; else rm -f ".deps/speaker-test.Tpo"; exit 1; fi
if gcc -DHAVE_CONFIG_H -I. -I. -I../include -I../include    -g -O2 -MT pink.o -MD -MP -MF ".deps/pink.Tpo" -c -o pink.o pink.c; \
    then mv -f ".deps/pink.Tpo" ".deps/pink.Po"; else rm -f ".deps/pink.Tpo"; exit 1; fi
gcc  -g -O2   -o speaker-test  speaker-test.o pink.o  -lm -lasound -lm -ldl -lpthread
make[2]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/speaker-test »
make[1]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/speaker-test »
Making all in seq
make[1]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/seq »
Making all in aconnect
make[2]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/seq/aconnect »
if gcc -DHAVE_CONFIG_H -I. -I. -I../../include -I../../include    -g -O2 -MT aconnect.o -MD -MP -MF ".deps/aconnect.Tpo" -c -o aconnect.o aconnect.c; \
    then mv -f ".deps/aconnect.Tpo" ".deps/aconnect.Po"; else rm -f ".deps/aconnect.Tpo"; exit 1; fi
gcc  -g -O2   -o aconnect  aconnect.o  -lasound -lm -ldl -lpthread
make[2]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/seq/aconnect »
Making all in aplaymidi
make[2]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/seq/aplaymidi »
if gcc -DHAVE_CONFIG_H -I. -I. -I../../include -I../../include    -g -O2 -MT aplaymidi.o -MD -MP -MF ".deps/aplaymidi.Tpo" -c -o aplaymidi.o aplaymidi.c; \
    then mv -f ".deps/aplaymidi.Tpo" ".deps/aplaymidi.Po"; else rm -f ".deps/aplaymidi.Tpo"; exit 1; fi
gcc  -g -O2   -o aplaymidi  aplaymidi.o  -lasound -lm -ldl -lpthread
if gcc -DHAVE_CONFIG_H -I. -I. -I../../include -I../../include    -g -O2 -MT arecordmidi.o -MD -MP -MF ".deps/arecordmidi.Tpo" -c -o arecordmidi.o arecordmidi.c; \
    then mv -f ".deps/arecordmidi.Tpo" ".deps/arecordmidi.Po"; else rm -f ".deps/arecordmidi.Tpo"; exit 1; fi
gcc  -g -O2   -o arecordmidi  arecordmidi.o  -lasound -lm -ldl -lpthread
make[2]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/seq/aplaymidi »
Making all in aseqdump
make[2]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/seq/aseqdump »
if gcc -DHAVE_CONFIG_H -I. -I. -I../../include -I../../include    -g -O2 -MT aseqdump.o -MD -MP -MF ".deps/aseqdump.Tpo" -c -o aseqdump.o aseqdump.c; \
    then mv -f ".deps/aseqdump.Tpo" ".deps/aseqdump.Po"; else rm -f ".deps/aseqdump.Tpo"; exit 1; fi
gcc  -g -O2   -o aseqdump  aseqdump.o  -lasound -lm -ldl -lpthread
make[2]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/seq/aseqdump »
Making all in aseqnet
make[2]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/seq/aseqnet »
if gcc -DHAVE_CONFIG_H -I. -I. -I../../include -I../../include    -g -O2 -MT aseqnet.o -MD -MP -MF ".deps/aseqnet.Tpo" -c -o aseqnet.o aseqnet.c; \
    then mv -f ".deps/aseqnet.Tpo" ".deps/aseqnet.Po"; else rm -f ".deps/aseqnet.Tpo"; exit 1; fi
aseqnet.c: In function ‘flush_writebuf’:
aseqnet.c:495: attention : ignoring return value of ‘write’, declared with attribute warn_unused_result
gcc  -g -O2   -o aseqnet  aseqnet.o  -lasound -lm -ldl -lpthread
make[2]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/seq/aseqnet »
make[2]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/seq »
make[2]: Rien à faire pour « all-am ».
make[2]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/seq »
make[1]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/seq »
make[1]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20 »
make[1]: Rien à faire pour « all-am ».
make[1]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20 »
rabgye@ubuntumaya:~/alsa-utils-1.0.20$ sudo make
Making all in include
make[1]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/include »
make  all-am
make[2]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/include »
make[2]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/include »
make[1]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/include »
Making all in alsactl
make[1]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/alsactl »
Making all in init
make[2]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/alsactl/init »
make[2]: Rien à faire pour « all ».
make[2]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/alsactl/init »
make[2]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/alsactl »
make[2]: Rien à faire pour « all-am ».
make[2]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/alsactl »
make[1]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/alsactl »
Making all in utils
make[1]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/utils »
make[1]: Rien à faire pour « all ».
make[1]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/utils »
Making all in m4
make[1]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/m4 »
make[1]: Rien à faire pour « all ».
make[1]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/m4 »
Making all in po
make[1]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/po »
make[1]: Rien à faire pour « all ».
make[1]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/po »
Making all in alsamixer
make[1]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/alsamixer »
make[1]: Rien à faire pour « all ».
make[1]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/alsamixer »
Making all in amixer
make[1]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/amixer »
make[1]: Rien à faire pour « all ».
make[1]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/amixer »
Making all in amidi
make[1]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/amidi »
make[1]: Rien à faire pour « all ».
make[1]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/amidi »
Making all in alsaconf
make[1]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/alsaconf »
Making all in po
make[2]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/alsaconf/po »
make[2]: Rien à faire pour « all ».
make[2]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/alsaconf/po »
make[2]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/alsaconf »
make[2]: Rien à faire pour « all-am ».
make[2]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/alsaconf »
make[1]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/alsaconf »
Making all in aplay
make[1]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/aplay »
make[1]: Rien à faire pour « all ».
make[1]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/aplay »
Making all in iecset
make[1]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/iecset »
make[1]: Rien à faire pour « all ».
make[1]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/iecset »
Making all in speaker-test
make[1]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/speaker-test »
Making all in samples
make[2]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/speaker-test/samples »
make[2]: Rien à faire pour « all ».
make[2]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/speaker-test/samples »
make[2]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/speaker-test »
make[2]: Rien à faire pour « all-am ».
make[2]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/speaker-test »
make[1]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/speaker-test »
Making all in seq
make[1]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/seq »
Making all in aconnect
make[2]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/seq/aconnect »
make[2]: Rien à faire pour « all ».
make[2]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/seq/aconnect »
Making all in aplaymidi
make[2]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/seq/aplaymidi »
make[2]: Rien à faire pour « all ».
make[2]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/seq/aplaymidi »
Making all in aseqdump
make[2]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/seq/aseqdump »
make[2]: Rien à faire pour « all ».
make[2]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/seq/aseqdump »
Making all in aseqnet
make[2]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/seq/aseqnet »
make[2]: Rien à faire pour « all ».
make[2]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/seq/aseqnet »
make[2]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/seq »
make[2]: Rien à faire pour « all-am ».
make[2]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/seq »
make[1]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/seq »
make[1]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20 »
make[1]: Rien à faire pour « all-am ».
make[1]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20 »
rabgye@ubuntumaya:~/alsa-utils-1.0.20$ sudo make install
Making install in include
make[1]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/include »
make[2]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/include »
make[2]: Rien à faire pour « install-exec-am ».
make[2]: Rien à faire pour « install-data-am ».
make[2]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/include »
make[1]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/include »
Making install in alsactl
make[1]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/alsactl »
Making install in init
make[2]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/alsactl/init »
make[3]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/alsactl/init »
make[3]: Rien à faire pour « install-exec-am ».
test -z "/usr/share/alsa/init" || mkdir -p -- "/usr/share/alsa/init"
 /usr/bin/install -c -m 644 '00main' '/usr/share/alsa/init/00main'
 /usr/bin/install -c -m 644 'default' '/usr/share/alsa/init/default'
 /usr/bin/install -c -m 644 'help' '/usr/share/alsa/init/help'
 /usr/bin/install -c -m 644 'info' '/usr/share/alsa/init/info'
 /usr/bin/install -c -m 644 'test' '/usr/share/alsa/init/test'
 /usr/bin/install -c -m 644 'hda' '/usr/share/alsa/init/hda'
make[3]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/alsactl/init »
make[2]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/alsactl/init »
make[2]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/alsactl »
make[3]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/alsactl »
test -z "/usr/sbin" || mkdir -p -- "/usr/sbin"
  /usr/bin/install -c 'alsactl' '/usr/sbin/alsactl'
test -z "/usr/share/man/man1" || mkdir -p -- "/usr/share/man/man1"
 /usr/bin/install -c -m 644 './alsactl.1' '/usr/share/man/man1/alsactl.1'
test -z "/usr/share/man/man7" || mkdir -p -- "/usr/share/man/man7"
 /usr/bin/install -c -m 644 './alsactl_init.7' '/usr/share/man/man7/alsactl_init.7'
make[3]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/alsactl »
make[2]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/alsactl »
make[1]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/alsactl »
Making install in utils
make[1]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/utils »
make[2]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/utils »
make[2]: Rien à faire pour « install-exec-am ».
make[2]: Rien à faire pour « install-data-am ».
make[2]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/utils »
make[1]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/utils »
Making install in m4
make[1]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/m4 »
make[2]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/m4 »
make[2]: Rien à faire pour « install-exec-am ».
make[2]: Rien à faire pour « install-data-am ».
make[2]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/m4 »
make[1]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/m4 »
Making install in po
make[1]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/po »
mkdir -p -- /usr/share
installing ja.gmo as /usr/share/locale/ja/LC_MESSAGES/alsa-utils.mo
if test "alsa-utils" = "gettext-tools"; then \
      mkdir -p -- /usr/share/gettext/po; \
      for file in Makefile.in.in remove-potcdate.sin quot.sed boldquot.sed [EMAIL="en@quot.header"]en@quot.header[/EMAIL] [EMAIL="en@boldquot.header"]en@boldquot.header[/EMAIL] insert-header.sin Rules-quot   Makevars.template; do \
        /usr/bin/install -c -m 644 ./$file \
                /usr/share/gettext/po/$file; \
      done; \
      for file in Makevars; do \
        rm -f /usr/share/gettext/po/$file; \
      done; \
    else \
      : ; \
    fi
make[1]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/po »
Making install in alsamixer
make[1]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/alsamixer »
make[2]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/alsamixer »
test -z "/usr/bin" || mkdir -p -- "/usr/bin"
  /usr/bin/install -c 'alsamixer' '/usr/bin/alsamixer'
test -z "/usr/share/man/man1" || mkdir -p -- "/usr/share/man/man1"
 /usr/bin/install -c -m 644 './alsamixer.1' '/usr/share/man/man1/alsamixer.1'
make[2]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/alsamixer »
make[1]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/alsamixer »
Making install in amixer
make[1]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/amixer »
make[2]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/amixer »
test -z "/usr/bin" || mkdir -p -- "/usr/bin"
  /usr/bin/install -c 'amixer' '/usr/bin/amixer'
test -z "/usr/share/man/man1" || mkdir -p -- "/usr/share/man/man1"
 /usr/bin/install -c -m 644 './amixer.1' '/usr/share/man/man1/amixer.1'
make[2]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/amixer »
make[1]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/amixer »
Making install in amidi
make[1]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/amidi »
make[2]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/amidi »
test -z "/usr/bin" || mkdir -p -- "/usr/bin"
  /usr/bin/install -c 'amidi' '/usr/bin/amidi'
test -z "/usr/share/man/man1" || mkdir -p -- "/usr/share/man/man1"
 /usr/bin/install -c -m 644 './amidi.1' '/usr/share/man/man1/amidi.1'
make[2]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/amidi »
make[1]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/amidi »
Making install in alsaconf
make[1]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/alsaconf »
Making install in po
make[2]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/alsaconf/po »
mkdir -p -- /usr/share
make[2]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/alsaconf/po »
make[2]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/alsaconf »
make[3]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/alsaconf »
test -z "/usr/sbin" || mkdir -p -- "/usr/sbin"
 /usr/bin/install -c 'alsaconf' '/usr/sbin/alsaconf'
 /usr/bin/install -c -m 644 alsaconf.8 /usr/share/man/man8/alsaconf.8
 /usr/bin/install -c -m 644 alsaconf.fr.8 /usr/share/man/fr/man8/alsaconf.8
make[3]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/alsaconf »
make[2]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/alsaconf »
make[1]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/alsaconf »
Making install in aplay
make[1]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/aplay »
make[2]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/aplay »
test -z "/usr/bin" || mkdir -p -- "/usr/bin"
  /usr/bin/install -c 'aplay' '/usr/bin/aplay'
make  install-exec-hook
make[3]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/aplay »
rm -f arecord
ln -s aplay arecord
rm -f /usr/bin/arecord
(cd /usr/bin && ln -s aplay arecord)
make[3]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/aplay »
test -z "/usr/share/man/man1" || mkdir -p -- "/usr/share/man/man1"
 /usr/bin/install -c -m 644 './aplay.1' '/usr/share/man/man1/aplay.1'
 /usr/bin/install -c -m 644 './arecord.1' '/usr/share/man/man1/arecord.1'
make  install-data-hook
make[3]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/aplay »
rm -f /usr/share/man/man1/arecord.1
(cd /usr/share/man/man1 && ln -s aplay.1 arecord.1)
make[3]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/aplay »
make[2]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/aplay »
make[1]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/aplay »
Making install in iecset
make[1]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/iecset »
make[2]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/iecset »
test -z "/usr/bin" || mkdir -p -- "/usr/bin"
  /usr/bin/install -c 'iecset' '/usr/bin/iecset'
test -z "/usr/share/man/man1" || mkdir -p -- "/usr/share/man/man1"
 /usr/bin/install -c -m 644 './iecset.1' '/usr/share/man/man1/iecset.1'
make[2]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/iecset »
make[1]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/iecset »
Making install in speaker-test
make[1]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/speaker-test »
Making install in samples
make[2]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/speaker-test/samples »
make[3]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/speaker-test/samples »
make[3]: Rien à faire pour « install-exec-am ».
test -z "/usr/share/alsa/speaker-test" || mkdir -p -- "/usr/share/alsa/speaker-test"
 /usr/bin/install -c -m 644 'sample_map.csv' '/usr/share/alsa/speaker-test/sample_map.csv'
test -z "/usr/share/sounds/alsa" || mkdir -p -- "/usr/share/sounds/alsa"
 /usr/bin/install -c -m 644 'Front_Left.wav' '/usr/share/sounds/alsa/Front_Left.wav'
 /usr/bin/install -c -m 644 'Rear_Center.wav' '/usr/share/sounds/alsa/Rear_Center.wav'
 /usr/bin/install -c -m 644 'Rear_Right.wav' '/usr/share/sounds/alsa/Rear_Right.wav'
 /usr/bin/install -c -m 644 'Side_Right.wav' '/usr/share/sounds/alsa/Side_Right.wav'
 /usr/bin/install -c -m 644 'Front_Center.wav' '/usr/share/sounds/alsa/Front_Center.wav'
 /usr/bin/install -c -m 644 'Front_Right.wav' '/usr/share/sounds/alsa/Front_Right.wav'
 /usr/bin/install -c -m 644 'Noise.wav' '/usr/share/sounds/alsa/Noise.wav'
 /usr/bin/install -c -m 644 'Rear_Left.wav' '/usr/share/sounds/alsa/Rear_Left.wav'
 /usr/bin/install -c -m 644 'Side_Left.wav' '/usr/share/sounds/alsa/Side_Left.wav'
make[3]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/speaker-test/samples »
make[2]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/speaker-test/samples »
make[2]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/speaker-test »
make[3]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/speaker-test »
test -z "/usr/bin" || mkdir -p -- "/usr/bin"
  /usr/bin/install -c 'speaker-test' '/usr/bin/speaker-test'
test -z "/usr/share/man/man1" || mkdir -p -- "/usr/share/man/man1"
 /usr/bin/install -c -m 644 './speaker-test.1' '/usr/share/man/man1/speaker-test.1'
make[3]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/speaker-test »
make[2]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/speaker-test »
make[1]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/speaker-test »
Making install in seq
make[1]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/seq »
Making install in aconnect
make[2]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/seq/aconnect »
make[3]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/seq/aconnect »
test -z "/usr/bin" || mkdir -p -- "/usr/bin"
  /usr/bin/install -c 'aconnect' '/usr/bin/aconnect'
test -z "/usr/share/man/man1" || mkdir -p -- "/usr/share/man/man1"
 /usr/bin/install -c -m 644 './aconnect.1' '/usr/share/man/man1/aconnect.1'
make[3]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/seq/aconnect »
make[2]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/seq/aconnect »
Making install in aplaymidi
make[2]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/seq/aplaymidi »
make[3]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/seq/aplaymidi »
test -z "/usr/bin" || mkdir -p -- "/usr/bin"
  /usr/bin/install -c 'aplaymidi' '/usr/bin/aplaymidi'
  /usr/bin/install -c 'arecordmidi' '/usr/bin/arecordmidi'
test -z "/usr/share/man/man1" || mkdir -p -- "/usr/share/man/man1"
 /usr/bin/install -c -m 644 './aplaymidi.1' '/usr/share/man/man1/aplaymidi.1'
 /usr/bin/install -c -m 644 './arecordmidi.1' '/usr/share/man/man1/arecordmidi.1'
make[3]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/seq/aplaymidi »
make[2]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/seq/aplaymidi »
Making install in aseqdump
make[2]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/seq/aseqdump »
make[3]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/seq/aseqdump »
test -z "/usr/bin" || mkdir -p -- "/usr/bin"
  /usr/bin/install -c 'aseqdump' '/usr/bin/aseqdump'
test -z "/usr/share/man/man1" || mkdir -p -- "/usr/share/man/man1"
 /usr/bin/install -c -m 644 './aseqdump.1' '/usr/share/man/man1/aseqdump.1'
make[3]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/seq/aseqdump »
make[2]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/seq/aseqdump »
Making install in aseqnet
make[2]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/seq/aseqnet »
make[3]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/seq/aseqnet »
test -z "/usr/bin" || mkdir -p -- "/usr/bin"
  /usr/bin/install -c 'aseqnet' '/usr/bin/aseqnet'
test -z "/usr/share/man/man1" || mkdir -p -- "/usr/share/man/man1"
 /usr/bin/install -c -m 644 './aseqnet.1' '/usr/share/man/man1/aseqnet.1'
make[3]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/seq/aseqnet »
make[2]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/seq/aseqnet »
make[2]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/seq »
make[3]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/seq »
make[3]: Rien à faire pour « install-exec-am ».
make[3]: Rien à faire pour « install-data-am ».
make[3]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/seq »
make[2]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/seq »
make[1]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/seq »
make[1]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20 »
make[2]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20 »
make[2]: Rien à faire pour « install-exec-am ».
make[2]: Rien à faire pour « install-data-am ».
make[2]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20 »
make[1]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20 »
rabgye@ubuntumaya:~/alsa-utils-1.0.20$ rm -f ~/alsa-driver*
rm: ne peut enlever `/home/rabgye/alsa-driver-1.0.20': est un dossier
rabgye@ubuntumaya:~/alsa-utils-1.0.20$ rm -f ~/alsa-lib*
rm: ne peut enlever `/home/rabgye/alsa-lib-1.0.20': est un dossier
rabgye@ubuntumaya:~/alsa-utils-1.0.20$ rm -f ~/alsa-utils*
rm: ne peut enlever `/home/rabgye/alsa-utils-1.0.20': est un dossier
rabgye@ubuntumaya:~/alsa-utils-1.0.20$ 


































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































make[1]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/amixer »
if gcc -DHAVE_CONFIG_H -I. -I. -I../include -I../include    -g -O2 -MT amixer.o -MD -MP -MF ".deps/amixer.Tpo" -c -o amixer.o amixer.c; \
    then mv -f ".deps/amixer.Tpo" ".deps/amixer.Po"; else rm -f ".deps/amixer.Tpo"; exit 1; fi
amixer.c: In function ‘get_integer’:
amixer.c:244: attention : ignoring return value of ‘strtol’, declared with attribute warn_unused_result
amixer.c: In function ‘get_integer64’:
amixer.c:272: attention : ignoring return value of ‘strtol’, declared with attribute warn_unused_result
amixer.c: In function ‘set_volume_simple’:
amixer.c:358: attention : ignoring return value of ‘strtol’, declared with attribute warn_unused_result
gcc  -g -O2   -o amixer  amixer.o -lm -lasound -lm -ldl -lpthread
make[1]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/amixer »
Making all in amidi
make[1]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/amidi »
if gcc -DHAVE_CONFIG_H -I. -I. -I../include -I../include    -g -O2 -MT amidi.o -MD -MP -MF ".deps/amidi.Tpo" -c -o amidi.o amidi.c; \
    then mv -f ".deps/amidi.Tpo" ".deps/amidi.Po"; else rm -f ".deps/amidi.Tpo"; exit 1; fi
amidi.c: In function ‘main’:
amidi.c:658: attention : ignoring return value of ‘write’, declared with attribute warn_unused_result
gcc  -g -O2   -o amidi  amidi.o  -lasound -lm -ldl -lpthread
make[1]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/amidi »
Making all in alsaconf
make[1]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/alsaconf »
Making all in po
make[2]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/alsaconf/po »
35 messages traduits, 1 message non traduit.
34 messages traduits, 1 traduction approximative, 1 message non traduit.
make[2]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/alsaconf/po »
make[2]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/alsaconf »
make[2]: Rien à faire pour « all-am ».
make[2]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/alsaconf »
make[1]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/alsaconf »
Making all in aplay
make[1]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/aplay »
if gcc -DHAVE_CONFIG_H -I. -I. -I../include -I../include    -g -O2 -MT aplay.o -MD -MP -MF ".deps/aplay.Tpo" -c -o aplay.o aplay.c; \
    then mv -f ".deps/aplay.Tpo" ".deps/aplay.Po"; else rm -f ".deps/aplay.Tpo"; exit 1; fi
aplay.c: In function ‘end_voc’:
aplay.c:2158: attention : ignoring return value of ‘write’, declared with attribute warn_unused_result
aplay.c: In function ‘end_wave’:
aplay.c:2178: attention : ignoring return value of ‘write’, declared with attribute warn_unused_result
aplay.c:2180: attention : ignoring return value of ‘write’, declared with attribute warn_unused_result
aplay.c: In function ‘end_au’:
aplay.c:2193: attention : ignoring return value of ‘write’, declared with attribute warn_unused_result
gcc  -g -O2   -o aplay  aplay.o  -lrt -lasound -lm -ldl -lpthread
make[1]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/aplay »
Making all in iecset
make[1]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/iecset »
if gcc -DHAVE_CONFIG_H -I. -I. -I../include -I../include    -g -O2 -MT iecset.o -MD -MP -MF ".deps/iecset.Tpo" -c -o iecset.o iecset.c; \
    then mv -f ".deps/iecset.Tpo" ".deps/iecset.Po"; else rm -f ".deps/iecset.Tpo"; exit 1; fi
if gcc -DHAVE_CONFIG_H -I. -I. -I../include -I../include    -g -O2 -MT iecbits.o -MD -MP -MF ".deps/iecbits.Tpo" -c -o iecbits.o iecbits.c; \
    then mv -f ".deps/iecbits.Tpo" ".deps/iecbits.Po"; else rm -f ".deps/iecbits.Tpo"; exit 1; fi
gcc  -g -O2   -o iecset  iecset.o iecbits.o -lm -lasound -lm -ldl -lpthread
make[1]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/iecset »
Making all in speaker-test
make[1]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/speaker-test »
Making all in samples
make[2]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/speaker-test/samples »
make[2]: Rien à faire pour « all ».
make[2]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/speaker-test/samples »
make[2]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/speaker-test »
if gcc -DHAVE_CONFIG_H -I. -I. -I../include -I../include    -g -O2 -MT speaker-test.o -MD -MP -MF ".deps/speaker-test.Tpo" -c -o speaker-test.o speaker-test.c; \
    then mv -f ".deps/speaker-test.Tpo" ".deps/speaker-test.Po"; else rm -f ".deps/speaker-test.Tpo"; exit 1; fi
if gcc -DHAVE_CONFIG_H -I. -I. -I../include -I../include    -g -O2 -MT pink.o -MD -MP -MF ".deps/pink.Tpo" -c -o pink.o pink.c; \
    then mv -f ".deps/pink.Tpo" ".deps/pink.Po"; else rm -f ".deps/pink.Tpo"; exit 1; fi
gcc  -g -O2   -o speaker-test  speaker-test.o pink.o  -lm -lasound -lm -ldl -lpthread
make[2]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/speaker-test »
make[1]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/speaker-test »
Making all in seq
make[1]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/seq »
Making all in aconnect
make[2]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/seq/aconnect »
if gcc -DHAVE_CONFIG_H -I. -I. -I../../include -I../../include    -g -O2 -MT aconnect.o -MD -MP -MF ".deps/aconnect.Tpo" -c -o aconnect.o aconnect.c; \
    then mv -f ".deps/aconnect.Tpo" ".deps/aconnect.Po"; else rm -f ".deps/aconnect.Tpo"; exit 1; fi
gcc  -g -O2   -o aconnect  aconnect.o  -lasound -lm -ldl -lpthread
make[2]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/seq/aconnect »
Making all in aplaymidi
make[2]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/seq/aplaymidi »
if gcc -DHAVE_CONFIG_H -I. -I. -I../../include -I../../include    -g -O2 -MT aplaymidi.o -MD -MP -MF ".deps/aplaymidi.Tpo" -c -o aplaymidi.o aplaymidi.c; \
    then mv -f ".deps/aplaymidi.Tpo" ".deps/aplaymidi.Po"; else rm -f ".deps/aplaymidi.Tpo"; exit 1; fi
gcc  -g -O2   -o aplaymidi  aplaymidi.o  -lasound -lm -ldl -lpthread
if gcc -DHAVE_CONFIG_H -I. -I. -I../../include -I../../include    -g -O2 -MT arecordmidi.o -MD -MP -MF ".deps/arecordmidi.Tpo" -c -o arecordmidi.o arecordmidi.c; \
    then mv -f ".deps/arecordmidi.Tpo" ".deps/arecordmidi.Po"; else rm -f ".deps/arecordmidi.Tpo"; exit 1; fi
gcc  -g -O2   -o arecordmidi  arecordmidi.o  -lasound -lm -ldl -lpthread
make[2]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/seq/aplaymidi »
Making all in aseqdump
make[2]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/seq/aseqdump »
if gcc -DHAVE_CONFIG_H -I. -I. -I../../include -I../../include    -g -O2 -MT aseqdump.o -MD -MP -MF ".deps/aseqdump.Tpo" -c -o aseqdump.o aseqdump.c; \
    then mv -f ".deps/aseqdump.Tpo" ".deps/aseqdump.Po"; else rm -f ".deps/aseqdump.Tpo"; exit 1; fi
gcc  -g -O2   -o aseqdump  aseqdump.o  -lasound -lm -ldl -lpthread
make[2]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/seq/aseqdump »
Making all in aseqnet
make[2]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/seq/aseqnet »
if gcc -DHAVE_CONFIG_H -I. -I. -I../../include -I../../include    -g -O2 -MT aseqnet.o -MD -MP -MF ".deps/aseqnet.Tpo" -c -o aseqnet.o aseqnet.c; \
    then mv -f ".deps/aseqnet.Tpo" ".deps/aseqnet.Po"; else rm -f ".deps/aseqnet.Tpo"; exit 1; fi
aseqnet.c: In function ‘flush_writebuf’:
aseqnet.c:495: attention : ignoring return value of ‘write’, declared with attribute warn_unused_result
gcc  -g -O2   -o aseqnet  aseqnet.o  -lasound -lm -ldl -lpthread
make[2]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/seq/aseqnet »
make[2]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/seq »
make[2]: Rien à faire pour « all-am ».
make[2]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/seq »
make[1]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/seq »
make[1]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20 »
make[1]: Rien à faire pour « all-am ».
make[1]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20 »
rabgye@ubuntumaya:~/alsa-utils-1.0.20$ sudo make
Making all in include
make[1]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/include »
make  all-am
make[2]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/include »
make[2]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/include »
make[1]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/include »
Making all in alsactl
make[1]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/alsactl »
Making all in init
make[2]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/alsactl/init »
make[2]: Rien à faire pour « all ».
make[2]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/alsactl/init »
make[2]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/alsactl »
make[2]: Rien à faire pour « all-am ».
make[2]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/alsactl »
make[1]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/alsactl »
Making all in utils
make[1]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/utils »
make[1]: Rien à faire pour « all ».
make[1]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/utils »
Making all in m4
make[1]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/m4 »
make[1]: Rien à faire pour « all ».
make[1]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/m4 »
Making all in po
make[1]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/po »
make[1]: Rien à faire pour « all ».
make[1]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/po »
Making all in alsamixer
make[1]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/alsamixer »
make[1]: Rien à faire pour « all ».
make[1]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/alsamixer »
Making all in amixer
make[1]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/amixer »
make[1]: Rien à faire pour « all ».
make[1]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/amixer »
Making all in amidi
make[1]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/amidi »
make[1]: Rien à faire pour « all ».
make[1]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/amidi »
Making all in alsaconf
make[1]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/alsaconf »
Making all in po
make[2]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/alsaconf/po »
make[2]: Rien à faire pour « all ».
make[2]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/alsaconf/po »
make[2]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/alsaconf »
make[2]: Rien à faire pour « all-am ».
make[2]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/alsaconf »
make[1]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/alsaconf »
Making all in aplay
make[1]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/aplay »
make[1]: Rien à faire pour « all ».
make[1]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/aplay »
Making all in iecset
make[1]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/iecset »
make[1]: Rien à faire pour « all ».
make[1]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/iecset »
Making all in speaker-test
make[1]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/speaker-test »
Making all in samples
make[2]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/speaker-test/samples »
make[2]: Rien à faire pour « all ».
make[2]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/speaker-test/samples »
make[2]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/speaker-test »
make[2]: Rien à faire pour « all-am ».
make[2]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/speaker-test »
make[1]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/speaker-test »
Making all in seq
make[1]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/seq »
Making all in aconnect
make[2]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/seq/aconnect »
make[2]: Rien à faire pour « all ».
make[2]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/seq/aconnect »
Making all in aplaymidi
make[2]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/seq/aplaymidi »
make[2]: Rien à faire pour « all ».
make[2]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/seq/aplaymidi »
Making all in aseqdump
make[2]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/seq/aseqdump »
make[2]: Rien à faire pour « all ».
make[2]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/seq/aseqdump »
Making all in aseqnet
make[2]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/seq/aseqnet »
make[2]: Rien à faire pour « all ».
make[2]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/seq/aseqnet »
make[2]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/seq »
make[2]: Rien à faire pour « all-am ».
make[2]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/seq »
make[1]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/seq »
make[1]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20 »
make[1]: Rien à faire pour « all-am ».
make[1]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20 »
rabgye@ubuntumaya:~/alsa-utils-1.0.20$ sudo make install
Making install in include
make[1]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/include »
make[2]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/include »
make[2]: Rien à faire pour « install-exec-am ».
make[2]: Rien à faire pour « install-data-am ».
make[2]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/include »
make[1]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/include »
Making install in alsactl
make[1]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/alsactl »
Making install in init
make[2]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/alsactl/init »
make[3]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/alsactl/init »
make[3]: Rien à faire pour « install-exec-am ».
test -z "/usr/share/alsa/init" || mkdir -p -- "/usr/share/alsa/init"
 /usr/bin/install -c -m 644 '00main' '/usr/share/alsa/init/00main'
 /usr/bin/install -c -m 644 'default' '/usr/share/alsa/init/default'
 /usr/bin/install -c -m 644 'help' '/usr/share/alsa/init/help'
 /usr/bin/install -c -m 644 'info' '/usr/share/alsa/init/info'
 /usr/bin/install -c -m 644 'test' '/usr/share/alsa/init/test'
 /usr/bin/install -c -m 644 'hda' '/usr/share/alsa/init/hda'
make[3]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/alsactl/init »
make[2]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/alsactl/init »
make[2]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/alsactl »
make[3]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/alsactl »
test -z "/usr/sbin" || mkdir -p -- "/usr/sbin"
  /usr/bin/install -c 'alsactl' '/usr/sbin/alsactl'
test -z "/usr/share/man/man1" || mkdir -p -- "/usr/share/man/man1"
 /usr/bin/install -c -m 644 './alsactl.1' '/usr/share/man/man1/alsactl.1'
test -z "/usr/share/man/man7" || mkdir -p -- "/usr/share/man/man7"
 /usr/bin/install -c -m 644 './alsactl_init.7' '/usr/share/man/man7/alsactl_init.7'
make[3]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/alsactl »
make[2]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/alsactl »
make[1]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/alsactl »
Making install in utils
make[1]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/utils »
make[2]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/utils »
make[2]: Rien à faire pour « install-exec-am ».
make[2]: Rien à faire pour « install-data-am ».
make[2]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/utils »
make[1]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/utils »
Making install in m4
make[1]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/m4 »
make[2]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/m4 »
make[2]: Rien à faire pour « install-exec-am ».
make[2]: Rien à faire pour « install-data-am ».
make[2]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/m4 »
make[1]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/m4 »
Making install in po
make[1]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/po »
mkdir -p -- /usr/share
installing ja.gmo as /usr/share/locale/ja/LC_MESSAGES/alsa-utils.mo
if test "alsa-utils" = "gettext-tools"; then \
      mkdir -p -- /usr/share/gettext/po; \
      for file in Makefile.in.in remove-potcdate.sin quot.sed boldquot.sed [EMAIL="en@quot.header"]en@quot.header[/EMAIL] [EMAIL="en@boldquot.header"]en@boldquot.header[/EMAIL] insert-header.sin Rules-quot   Makevars.template; do \
        /usr/bin/install -c -m 644 ./$file \
                /usr/share/gettext/po/$file; \
      done; \
      for file in Makevars; do \
        rm -f /usr/share/gettext/po/$file; \
      done; \
    else \
      : ; \
    fi
make[1]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/po »
Making install in alsamixer
make[1]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/alsamixer »
make[2]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/alsamixer »
test -z "/usr/bin" || mkdir -p -- "/usr/bin"
  /usr/bin/install -c 'alsamixer' '/usr/bin/alsamixer'
test -z "/usr/share/man/man1" || mkdir -p -- "/usr/share/man/man1"
 /usr/bin/install -c -m 644 './alsamixer.1' '/usr/share/man/man1/alsamixer.1'
make[2]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/alsamixer »
make[1]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/alsamixer »
Making install in amixer
make[1]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/amixer »
make[2]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/amixer »
test -z "/usr/bin" || mkdir -p -- "/usr/bin"
  /usr/bin/install -c 'amixer' '/usr/bin/amixer'
test -z "/usr/share/man/man1" || mkdir -p -- "/usr/share/man/man1"
 /usr/bin/install -c -m 644 './amixer.1' '/usr/share/man/man1/amixer.1'
make[2]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/amixer »
make[1]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/amixer »
Making install in amidi
make[1]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/amidi »
make[2]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/amidi »
test -z "/usr/bin" || mkdir -p -- "/usr/bin"
  /usr/bin/install -c 'amidi' '/usr/bin/amidi'
test -z "/usr/share/man/man1" || mkdir -p -- "/usr/share/man/man1"
 /usr/bin/install -c -m 644 './amidi.1' '/usr/share/man/man1/amidi.1'
make[2]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/amidi »
make[1]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/amidi »
Making install in alsaconf
make[1]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/alsaconf »
Making install in po
make[2]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/alsaconf/po »
mkdir -p -- /usr/share
make[2]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/alsaconf/po »
make[2]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/alsaconf »
make[3]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/alsaconf »
test -z "/usr/sbin" || mkdir -p -- "/usr/sbin"
 /usr/bin/install -c 'alsaconf' '/usr/sbin/alsaconf'
 /usr/bin/install -c -m 644 alsaconf.8 /usr/share/man/man8/alsaconf.8
 /usr/bin/install -c -m 644 alsaconf.fr.8 /usr/share/man/fr/man8/alsaconf.8
make[3]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/alsaconf »
make[2]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/alsaconf »
make[1]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/alsaconf »
Making install in aplay
make[1]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/aplay »
make[2]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/aplay »
test -z "/usr/bin" || mkdir -p -- "/usr/bin"
  /usr/bin/install -c 'aplay' '/usr/bin/aplay'
make  install-exec-hook
make[3]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/aplay »
rm -f arecord
ln -s aplay arecord
rm -f /usr/bin/arecord
(cd /usr/bin && ln -s aplay arecord)
make[3]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/aplay »
test -z "/usr/share/man/man1" || mkdir -p -- "/usr/share/man/man1"
 /usr/bin/install -c -m 644 './aplay.1' '/usr/share/man/man1/aplay.1'
 /usr/bin/install -c -m 644 './arecord.1' '/usr/share/man/man1/arecord.1'
make  install-data-hook
make[3]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/aplay »
rm -f /usr/share/man/man1/arecord.1
(cd /usr/share/man/man1 && ln -s aplay.1 arecord.1)
make[3]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/aplay »
make[2]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/aplay »
make[1]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/aplay »
Making install in iecset
make[1]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/iecset »
make[2]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/iecset »
test -z "/usr/bin" || mkdir -p -- "/usr/bin"
  /usr/bin/install -c 'iecset' '/usr/bin/iecset'
test -z "/usr/share/man/man1" || mkdir -p -- "/usr/share/man/man1"
 /usr/bin/install -c -m 644 './iecset.1' '/usr/share/man/man1/iecset.1'
make[2]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/iecset »
make[1]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/iecset »
Making install in speaker-test
make[1]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/speaker-test »
Making install in samples
make[2]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/speaker-test/samples »
make[3]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/speaker-test/samples »
make[3]: Rien à faire pour « install-exec-am ».
test -z "/usr/share/alsa/speaker-test" || mkdir -p -- "/usr/share/alsa/speaker-test"
 /usr/bin/install -c -m 644 'sample_map.csv' '/usr/share/alsa/speaker-test/sample_map.csv'
test -z "/usr/share/sounds/alsa" || mkdir -p -- "/usr/share/sounds/alsa"
 /usr/bin/install -c -m 644 'Front_Left.wav' '/usr/share/sounds/alsa/Front_Left.wav'
 /usr/bin/install -c -m 644 'Rear_Center.wav' '/usr/share/sounds/alsa/Rear_Center.wav'
 /usr/bin/install -c -m 644 'Rear_Right.wav' '/usr/share/sounds/alsa/Rear_Right.wav'
 /usr/bin/install -c -m 644 'Side_Right.wav' '/usr/share/sounds/alsa/Side_Right.wav'
 /usr/bin/install -c -m 644 'Front_Center.wav' '/usr/share/sounds/alsa/Front_Center.wav'
 /usr/bin/install -c -m 644 'Front_Right.wav' '/usr/share/sounds/alsa/Front_Right.wav'
 /usr/bin/install -c -m 644 'Noise.wav' '/usr/share/sounds/alsa/Noise.wav'
 /usr/bin/install -c -m 644 'Rear_Left.wav' '/usr/share/sounds/alsa/Rear_Left.wav'
 /usr/bin/install -c -m 644 'Side_Left.wav' '/usr/share/sounds/alsa/Side_Left.wav'
make[3]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/speaker-test/samples »
make[2]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/speaker-test/samples »
make[2]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/speaker-test »
make[3]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/speaker-test »
test -z "/usr/bin" || mkdir -p -- "/usr/bin"
  /usr/bin/install -c 'speaker-test' '/usr/bin/speaker-test'
test -z "/usr/share/man/man1" || mkdir -p -- "/usr/share/man/man1"
 /usr/bin/install -c -m 644 './speaker-test.1' '/usr/share/man/man1/speaker-test.1'
make[3]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/speaker-test »
make[2]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/speaker-test »
make[1]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/speaker-test »
Making install in seq
make[1]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/seq »
Making install in aconnect
make[2]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/seq/aconnect »
make[3]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/seq/aconnect »
test -z "/usr/bin" || mkdir -p -- "/usr/bin"
  /usr/bin/install -c 'aconnect' '/usr/bin/aconnect'
test -z "/usr/share/man/man1" || mkdir -p -- "/usr/share/man/man1"
 /usr/bin/install -c -m 644 './aconnect.1' '/usr/share/man/man1/aconnect.1'
make[3]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/seq/aconnect »
make[2]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/seq/aconnect »
Making install in aplaymidi
make[2]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/seq/aplaymidi »
make[3]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/seq/aplaymidi »
test -z "/usr/bin" || mkdir -p -- "/usr/bin"
  /usr/bin/install -c 'aplaymidi' '/usr/bin/aplaymidi'
  /usr/bin/install -c 'arecordmidi' '/usr/bin/arecordmidi'
test -z "/usr/share/man/man1" || mkdir -p -- "/usr/share/man/man1"
 /usr/bin/install -c -m 644 './aplaymidi.1' '/usr/share/man/man1/aplaymidi.1'
 /usr/bin/install -c -m 644 './arecordmidi.1' '/usr/share/man/man1/arecordmidi.1'
make[3]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/seq/aplaymidi »
make[2]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/seq/aplaymidi »
Making install in aseqdump
make[2]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/seq/aseqdump »
make[3]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/seq/aseqdump »
test -z "/usr/bin" || mkdir -p -- "/usr/bin"
  /usr/bin/install -c 'aseqdump' '/usr/bin/aseqdump'
test -z "/usr/share/man/man1" || mkdir -p -- "/usr/share/man/man1"
 /usr/bin/install -c -m 644 './aseqdump.1' '/usr/share/man/man1/aseqdump.1'
make[3]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/seq/aseqdump »
make[2]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/seq/aseqdump »
Making install in aseqnet
make[2]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/seq/aseqnet »
make[3]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/seq/aseqnet »
test -z "/usr/bin" || mkdir -p -- "/usr/bin"
  /usr/bin/install -c 'aseqnet' '/usr/bin/aseqnet'
test -z "/usr/share/man/man1" || mkdir -p -- "/usr/share/man/man1"
 /usr/bin/install -c -m 644 './aseqnet.1' '/usr/share/man/man1/aseqnet.1'
make[3]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/seq/aseqnet »
make[2]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/seq/aseqnet »
make[2]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/seq »
make[3]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/seq »
make[3]: Rien à faire pour « install-exec-am ».
make[3]: Rien à faire pour « install-data-am ».
make[3]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/seq »
make[2]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/seq »
make[1]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/seq »
make[1]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20 »
make[2]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20 »
make[2]: Rien à faire pour « install-exec-am ».
make[2]: Rien à faire pour « install-data-am ».
make[2]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20 »
make[1]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20 »
rabgye@ubuntumaya:~/alsa-utils-1.0.20$ rm -f ~/alsa-driver*
rm: ne peut enlever `/home/rabgye/alsa-driver-1.0.20': est un dossier
rabgye@ubuntumaya:~/alsa-utils-1.0.20$ rm -f ~/alsa-lib*
rm: ne peut enlever `/home/rabgye/alsa-lib-1.0.20': est un dossier
rabgye@ubuntumaya:~/alsa-utils-1.0.20$ rm -f ~/alsa-utils*
rm: ne peut enlever `/home/rabgye/alsa-utils-1.0.20': est un dossier
rabgye@ubuntumaya:~/alsa-utils-1.0.20$ 


































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































make[1]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/amixer »
if gcc -DHAVE_CONFIG_H -I. -I. -I../include -I../include    -g -O2 -MT amixer.o -MD -MP -MF ".deps/amixer.Tpo" -c -o amixer.o amixer.c; \
    then mv -f ".deps/amixer.Tpo" ".deps/amixer.Po"; else rm -f ".deps/amixer.Tpo"; exit 1; fi
amixer.c: In function ‘get_integer’:
amixer.c:244: attention : ignoring return value of ‘strtol’, declared with attribute warn_unused_result
amixer.c: In function ‘get_integer64’:
amixer.c:272: attention : ignoring return value of ‘strtol’, declared with attribute warn_unused_result
amixer.c: In function ‘set_volume_simple’:
amixer.c:358: attention : ignoring return value of ‘strtol’, declared with attribute warn_unused_result
gcc  -g -O2   -o amixer  amixer.o -lm -lasound -lm -ldl -lpthread
make[1]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/amixer »
Making all in amidi
make[1]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/amidi »
if gcc -DHAVE_CONFIG_H -I. -I. -I../include -I../include    -g -O2 -MT amidi.o -MD -MP -MF ".deps/amidi.Tpo" -c -o amidi.o amidi.c; \
    then mv -f ".deps/amidi.Tpo" ".deps/amidi.Po"; else rm -f ".deps/amidi.Tpo"; exit 1; fi
amidi.c: In function ‘main’:
amidi.c:658: attention : ignoring return value of ‘write’, declared with attribute warn_unused_result
gcc  -g -O2   -o amidi  amidi.o  -lasound -lm -ldl -lpthread
make[1]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/amidi »
Making all in alsaconf
make[1]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/alsaconf »
Making all in po
make[2]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/alsaconf/po »
35 messages traduits, 1 message non traduit.
34 messages traduits, 1 traduction approximative, 1 message non traduit.
make[2]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/alsaconf/po »
make[2]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/alsaconf »
make[2]: Rien à faire pour « all-am ».
make[2]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/alsaconf »
make[1]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/alsaconf »
Making all in aplay
make[1]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/aplay »
if gcc -DHAVE_CONFIG_H -I. -I. -I../include -I../include    -g -O2 -MT aplay.o -MD -MP -MF ".deps/aplay.Tpo" -c -o aplay.o aplay.c; \
    then mv -f ".deps/aplay.Tpo" ".deps/aplay.Po"; else rm -f ".deps/aplay.Tpo"; exit 1; fi
aplay.c: In function ‘end_voc’:
aplay.c:2158: attention : ignoring return value of ‘write’, declared with attribute warn_unused_result
aplay.c: In function ‘end_wave’:
aplay.c:2178: attention : ignoring return value of ‘write’, declared with attribute warn_unused_result
aplay.c:2180: attention : ignoring return value of ‘write’, declared with attribute warn_unused_result
aplay.c: In function ‘end_au’:
aplay.c:2193: attention : ignoring return value of ‘write’, declared with attribute warn_unused_result
gcc  -g -O2   -o aplay  aplay.o  -lrt -lasound -lm -ldl -lpthread
make[1]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/aplay »
Making all in iecset
make[1]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/iecset »
if gcc -DHAVE_CONFIG_H -I. -I. -I../include -I../include    -g -O2 -MT iecset.o -MD -MP -MF ".deps/iecset.Tpo" -c -o iecset.o iecset.c; \
    then mv -f ".deps/iecset.Tpo" ".deps/iecset.Po"; else rm -f ".deps/iecset.Tpo"; exit 1; fi
if gcc -DHAVE_CONFIG_H -I. -I. -I../include -I../include    -g -O2 -MT iecbits.o -MD -MP -MF ".deps/iecbits.Tpo" -c -o iecbits.o iecbits.c; \
    then mv -f ".deps/iecbits.Tpo" ".deps/iecbits.Po"; else rm -f ".deps/iecbits.Tpo"; exit 1; fi
gcc  -g -O2   -o iecset  iecset.o iecbits.o -lm -lasound -lm -ldl -lpthread
make[1]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/iecset »
Making all in speaker-test
make[1]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/speaker-test »
Making all in samples
make[2]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/speaker-test/samples »
make[2]: Rien à faire pour « all ».
make[2]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/speaker-test/samples »
make[2]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/speaker-test »
if gcc -DHAVE_CONFIG_H -I. -I. -I../include -I../include    -g -O2 -MT speaker-test.o -MD -MP -MF ".deps/speaker-test.Tpo" -c -o speaker-test.o speaker-test.c; \
    then mv -f ".deps/speaker-test.Tpo" ".deps/speaker-test.Po"; else rm -f ".deps/speaker-test.Tpo"; exit 1; fi
if gcc -DHAVE_CONFIG_H -I. -I. -I../include -I../include    -g -O2 -MT pink.o -MD -MP -MF ".deps/pink.Tpo" -c -o pink.o pink.c; \
    then mv -f ".deps/pink.Tpo" ".deps/pink.Po"; else rm -f ".deps/pink.Tpo"; exit 1; fi
gcc  -g -O2   -o speaker-test  speaker-test.o pink.o  -lm -lasound -lm -ldl -lpthread
make[2]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/speaker-test »
make[1]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/speaker-test »
Making all in seq
make[1]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/seq »
Making all in aconnect
make[2]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/seq/aconnect »
if gcc -DHAVE_CONFIG_H -I. -I. -I../../include -I../../include    -g -O2 -MT aconnect.o -MD -MP -MF ".deps/aconnect.Tpo" -c -o aconnect.o aconnect.c; \
    then mv -f ".deps/aconnect.Tpo" ".deps/aconnect.Po"; else rm -f ".deps/aconnect.Tpo"; exit 1; fi
gcc  -g -O2   -o aconnect  aconnect.o  -lasound -lm -ldl -lpthread
make[2]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/seq/aconnect »
Making all in aplaymidi
make[2]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/seq/aplaymidi »
if gcc -DHAVE_CONFIG_H -I. -I. -I../../include -I../../include    -g -O2 -MT aplaymidi.o -MD -MP -MF ".deps/aplaymidi.Tpo" -c -o aplaymidi.o aplaymidi.c; \
    then mv -f ".deps/aplaymidi.Tpo" ".deps/aplaymidi.Po"; else rm -f ".deps/aplaymidi.Tpo"; exit 1; fi
gcc  -g -O2   -o aplaymidi  aplaymidi.o  -lasound -lm -ldl -lpthread
if gcc -DHAVE_CONFIG_H -I. -I. -I../../include -I../../include    -g -O2 -MT arecordmidi.o -MD -MP -MF ".deps/arecordmidi.Tpo" -c -o arecordmidi.o arecordmidi.c; \
    then mv -f ".deps/arecordmidi.Tpo" ".deps/arecordmidi.Po"; else rm -f ".deps/arecordmidi.Tpo"; exit 1; fi
gcc  -g -O2   -o arecordmidi  arecordmidi.o  -lasound -lm -ldl -lpthread
make[2]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/seq/aplaymidi »
Making all in aseqdump
make[2]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/seq/aseqdump »
if gcc -DHAVE_CONFIG_H -I. -I. -I../../include -I../../include    -g -O2 -MT aseqdump.o -MD -MP -MF ".deps/aseqdump.Tpo" -c -o aseqdump.o aseqdump.c; \
    then mv -f ".deps/aseqdump.Tpo" ".deps/aseqdump.Po"; else rm -f ".deps/aseqdump.Tpo"; exit 1; fi
gcc  -g -O2   -o aseqdump  aseqdump.o  -lasound -lm -ldl -lpthread
make[2]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/seq/aseqdump »
Making all in aseqnet
make[2]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/seq/aseqnet »
if gcc -DHAVE_CONFIG_H -I. -I. -I../../include -I../../include    -g -O2 -MT aseqnet.o -MD -MP -MF ".deps/aseqnet.Tpo" -c -o aseqnet.o aseqnet.c; \
    then mv -f ".deps/aseqnet.Tpo" ".deps/aseqnet.Po"; else rm -f ".deps/aseqnet.Tpo"; exit 1; fi
aseqnet.c: In function ‘flush_writebuf’:
aseqnet.c:495: attention : ignoring return value of ‘write’, declared with attribute warn_unused_result
gcc  -g -O2   -o aseqnet  aseqnet.o  -lasound -lm -ldl -lpthread
make[2]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/seq/aseqnet »
make[2]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/seq »
make[2]: Rien à faire pour « all-am ».
make[2]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/seq »
make[1]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/seq »
make[1]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20 »
make[1]: Rien à faire pour « all-am ».
make[1]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20 »
rabgye@ubuntumaya:~/alsa-utils-1.0.20$ sudo make
Making all in include
make[1]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/include »
make  all-am
make[2]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/include »
make[2]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/include »
make[1]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/include »
Making all in alsactl
make[1]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/alsactl »
Making all in init
make[2]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/alsactl/init »
make[2]: Rien à faire pour « all ».
make[2]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/alsactl/init »
make[2]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/alsactl »
make[2]: Rien à faire pour « all-am ».
make[2]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/alsactl »
make[1]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/alsactl »
Making all in utils
make[1]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/utils »
make[1]: Rien à faire pour « all ».
make[1]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/utils »
Making all in m4
make[1]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/m4 »
make[1]: Rien à faire pour « all ».
make[1]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/m4 »
Making all in po
make[1]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/po »
make[1]: Rien à faire pour « all ».
make[1]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/po »
Making all in alsamixer
make[1]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/alsamixer »
make[1]: Rien à faire pour « all ».
make[1]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/alsamixer »
Making all in amixer
make[1]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/amixer »
make[1]: Rien à faire pour « all ».
make[1]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/amixer »
Making all in amidi
make[1]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/amidi »
make[1]: Rien à faire pour « all ».
make[1]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/amidi »
Making all in alsaconf
make[1]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/alsaconf »
Making all in po
make[2]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/alsaconf/po »
make[2]: Rien à faire pour « all ».
make[2]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/alsaconf/po »
make[2]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/alsaconf »
make[2]: Rien à faire pour « all-am ».
make[2]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/alsaconf »
make[1]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/alsaconf »
Making all in aplay
make[1]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/aplay »
make[1]: Rien à faire pour « all ».
make[1]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/aplay »
Making all in iecset
make[1]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/iecset »
make[1]: Rien à faire pour « all ».
make[1]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/iecset »
Making all in speaker-test
make[1]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/speaker-test »
Making all in samples
make[2]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/speaker-test/samples »
make[2]: Rien à faire pour « all ».
make[2]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/speaker-test/samples »
make[2]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/speaker-test »
make[2]: Rien à faire pour « all-am ».
make[2]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/speaker-test »
make[1]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/speaker-test »
Making all in seq
make[1]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/seq »
Making all in aconnect
make[2]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/seq/aconnect »
make[2]: Rien à faire pour « all ».
make[2]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/seq/aconnect »
Making all in aplaymidi
make[2]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/seq/aplaymidi »
make[2]: Rien à faire pour « all ».
make[2]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/seq/aplaymidi »
Making all in aseqdump
make[2]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/seq/aseqdump »
make[2]: Rien à faire pour « all ».
make[2]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/seq/aseqdump »
Making all in aseqnet
make[2]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/seq/aseqnet »
make[2]: Rien à faire pour « all ».
make[2]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/seq/aseqnet »
make[2]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/seq »
make[2]: Rien à faire pour « all-am ».
make[2]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/seq »
make[1]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/seq »
make[1]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20 »
make[1]: Rien à faire pour « all-am ».
make[1]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20 »
rabgye@ubuntumaya:~/alsa-utils-1.0.20$ sudo make install
Making install in include
make[1]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/include »
make[2]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/include »
make[2]: Rien à faire pour « install-exec-am ».
make[2]: Rien à faire pour « install-data-am ».
make[2]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/include »
make[1]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/include »
Making install in alsactl
make[1]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/alsactl »
Making install in init
make[2]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/alsactl/init »
make[3]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/alsactl/init »
make[3]: Rien à faire pour « install-exec-am ».
test -z "/usr/share/alsa/init" || mkdir -p -- "/usr/share/alsa/init"
 /usr/bin/install -c -m 644 '00main' '/usr/share/alsa/init/00main'
 /usr/bin/install -c -m 644 'default' '/usr/share/alsa/init/default'
 /usr/bin/install -c -m 644 'help' '/usr/share/alsa/init/help'
 /usr/bin/install -c -m 644 'info' '/usr/share/alsa/init/info'
 /usr/bin/install -c -m 644 'test' '/usr/share/alsa/init/test'
 /usr/bin/install -c -m 644 'hda' '/usr/share/alsa/init/hda'
make[3]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/alsactl/init »
make[2]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/alsactl/init »
make[2]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/alsactl »
make[3]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/alsactl »
test -z "/usr/sbin" || mkdir -p -- "/usr/sbin"
  /usr/bin/install -c 'alsactl' '/usr/sbin/alsactl'
test -z "/usr/share/man/man1" || mkdir -p -- "/usr/share/man/man1"
 /usr/bin/install -c -m 644 './alsactl.1' '/usr/share/man/man1/alsactl.1'
test -z "/usr/share/man/man7" || mkdir -p -- "/usr/share/man/man7"
 /usr/bin/install -c -m 644 './alsactl_init.7' '/usr/share/man/man7/alsactl_init.7'
make[3]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/alsactl »
make[2]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/alsactl »
make[1]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/alsactl »
Making install in utils
make[1]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/utils »
make[2]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/utils »
make[2]: Rien à faire pour « install-exec-am ».
make[2]: Rien à faire pour « install-data-am ».
make[2]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/utils »
make[1]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/utils »
Making install in m4
make[1]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/m4 »
make[2]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/m4 »
make[2]: Rien à faire pour « install-exec-am ».
make[2]: Rien à faire pour « install-data-am ».
make[2]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/m4 »
make[1]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/m4 »
Making install in po
make[1]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/po »
mkdir -p -- /usr/share
installing ja.gmo as /usr/share/locale/ja/LC_MESSAGES/alsa-utils.mo
if test "alsa-utils" = "gettext-tools"; then \
      mkdir -p -- /usr/share/gettext/po; \
      for file in Makefile.in.in remove-potcdate.sin quot.sed boldquot.sed [EMAIL="en@quot.header"]en@quot.header[/EMAIL] [EMAIL="en@boldquot.header"]en@boldquot.header[/EMAIL] insert-header.sin Rules-quot   Makevars.template; do \
        /usr/bin/install -c -m 644 ./$file \
                /usr/share/gettext/po/$file; \
      done; \
      for file in Makevars; do \
        rm -f /usr/share/gettext/po/$file; \
      done; \
    else \
      : ; \
    fi
make[1]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/po »
Making install in alsamixer
make[1]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/alsamixer »
make[2]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/alsamixer »
test -z "/usr/bin" || mkdir -p -- "/usr/bin"
  /usr/bin/install -c 'alsamixer' '/usr/bin/alsamixer'
test -z "/usr/share/man/man1" || mkdir -p -- "/usr/share/man/man1"
 /usr/bin/install -c -m 644 './alsamixer.1' '/usr/share/man/man1/alsamixer.1'
make[2]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/alsamixer »
make[1]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/alsamixer »
Making install in amixer
make[1]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/amixer »
make[2]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/amixer »
test -z "/usr/bin" || mkdir -p -- "/usr/bin"
  /usr/bin/install -c 'amixer' '/usr/bin/amixer'
test -z "/usr/share/man/man1" || mkdir -p -- "/usr/share/man/man1"
 /usr/bin/install -c -m 644 './amixer.1' '/usr/share/man/man1/amixer.1'
make[2]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/amixer »
make[1]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/amixer »
Making install in amidi
make[1]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/amidi »
make[2]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/amidi »
test -z "/usr/bin" || mkdir -p -- "/usr/bin"
  /usr/bin/install -c 'amidi' '/usr/bin/amidi'
test -z "/usr/share/man/man1" || mkdir -p -- "/usr/share/man/man1"
 /usr/bin/install -c -m 644 './amidi.1' '/usr/share/man/man1/amidi.1'
make[2]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/amidi »
make[1]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/amidi »
Making install in alsaconf
make[1]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/alsaconf »
Making install in po
make[2]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/alsaconf/po »
mkdir -p -- /usr/share
make[2]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/alsaconf/po »
make[2]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/alsaconf »
make[3]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/alsaconf »
test -z "/usr/sbin" || mkdir -p -- "/usr/sbin"
 /usr/bin/install -c 'alsaconf' '/usr/sbin/alsaconf'
 /usr/bin/install -c -m 644 alsaconf.8 /usr/share/man/man8/alsaconf.8
 /usr/bin/install -c -m 644 alsaconf.fr.8 /usr/share/man/fr/man8/alsaconf.8
make[3]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/alsaconf »
make[2]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/alsaconf »
make[1]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/alsaconf »
Making install in aplay
make[1]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/aplay »
make[2]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/aplay »
test -z "/usr/bin" || mkdir -p -- "/usr/bin"
  /usr/bin/install -c 'aplay' '/usr/bin/aplay'
make  install-exec-hook
make[3]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/aplay »
rm -f arecord
ln -s aplay arecord
rm -f /usr/bin/arecord
(cd /usr/bin && ln -s aplay arecord)
make[3]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/aplay »
test -z "/usr/share/man/man1" || mkdir -p -- "/usr/share/man/man1"
 /usr/bin/install -c -m 644 './aplay.1' '/usr/share/man/man1/aplay.1'
 /usr/bin/install -c -m 644 './arecord.1' '/usr/share/man/man1/arecord.1'
make  install-data-hook
make[3]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/aplay »
rm -f /usr/share/man/man1/arecord.1
(cd /usr/share/man/man1 && ln -s aplay.1 arecord.1)
make[3]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/aplay »
make[2]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/aplay »
make[1]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/aplay »
Making install in iecset
make[1]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/iecset »
make[2]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/iecset »
test -z "/usr/bin" || mkdir -p -- "/usr/bin"
  /usr/bin/install -c 'iecset' '/usr/bin/iecset'
test -z "/usr/share/man/man1" || mkdir -p -- "/usr/share/man/man1"
 /usr/bin/install -c -m 644 './iecset.1' '/usr/share/man/man1/iecset.1'
make[2]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/iecset »
make[1]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/iecset »
Making install in speaker-test
make[1]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/speaker-test »
Making install in samples
make[2]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/speaker-test/samples »
make[3]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/speaker-test/samples »
make[3]: Rien à faire pour « install-exec-am ».
test -z "/usr/share/alsa/speaker-test" || mkdir -p -- "/usr/share/alsa/speaker-test"
 /usr/bin/install -c -m 644 'sample_map.csv' '/usr/share/alsa/speaker-test/sample_map.csv'
test -z "/usr/share/sounds/alsa" || mkdir -p -- "/usr/share/sounds/alsa"
 /usr/bin/install -c -m 644 'Front_Left.wav' '/usr/share/sounds/alsa/Front_Left.wav'
 /usr/bin/install -c -m 644 'Rear_Center.wav' '/usr/share/sounds/alsa/Rear_Center.wav'
 /usr/bin/install -c -m 644 'Rear_Right.wav' '/usr/share/sounds/alsa/Rear_Right.wav'
 /usr/bin/install -c -m 644 'Side_Right.wav' '/usr/share/sounds/alsa/Side_Right.wav'
 /usr/bin/install -c -m 644 'Front_Center.wav' '/usr/share/sounds/alsa/Front_Center.wav'
 /usr/bin/install -c -m 644 'Front_Right.wav' '/usr/share/sounds/alsa/Front_Right.wav'
 /usr/bin/install -c -m 644 'Noise.wav' '/usr/share/sounds/alsa/Noise.wav'
 /usr/bin/install -c -m 644 'Rear_Left.wav' '/usr/share/sounds/alsa/Rear_Left.wav'
 /usr/bin/install -c -m 644 'Side_Left.wav' '/usr/share/sounds/alsa/Side_Left.wav'
make[3]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/speaker-test/samples »
make[2]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/speaker-test/samples »
make[2]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/speaker-test »
make[3]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/speaker-test »
test -z "/usr/bin" || mkdir -p -- "/usr/bin"
  /usr/bin/install -c 'speaker-test' '/usr/bin/speaker-test'
test -z "/usr/share/man/man1" || mkdir -p -- "/usr/share/man/man1"
 /usr/bin/install -c -m 644 './speaker-test.1' '/usr/share/man/man1/speaker-test.1'
make[3]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/speaker-test »
make[2]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/speaker-test »
make[1]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/speaker-test »
Making install in seq
make[1]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/seq »
Making install in aconnect
make[2]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/seq/aconnect »
make[3]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/seq/aconnect »
test -z "/usr/bin" || mkdir -p -- "/usr/bin"
  /usr/bin/install -c 'aconnect' '/usr/bin/aconnect'
test -z "/usr/share/man/man1" || mkdir -p -- "/usr/share/man/man1"
 /usr/bin/install -c -m 644 './aconnect.1' '/usr/share/man/man1/aconnect.1'
make[3]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/seq/aconnect »
make[2]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/seq/aconnect »
Making install in aplaymidi
make[2]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/seq/aplaymidi »
make[3]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/seq/aplaymidi »
test -z "/usr/bin" || mkdir -p -- "/usr/bin"
  /usr/bin/install -c 'aplaymidi' '/usr/bin/aplaymidi'
  /usr/bin/install -c 'arecordmidi' '/usr/bin/arecordmidi'
test -z "/usr/share/man/man1" || mkdir -p -- "/usr/share/man/man1"
 /usr/bin/install -c -m 644 './aplaymidi.1' '/usr/share/man/man1/aplaymidi.1'
 /usr/bin/install -c -m 644 './arecordmidi.1' '/usr/share/man/man1/arecordmidi.1'
make[3]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/seq/aplaymidi »
make[2]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/seq/aplaymidi »
Making install in aseqdump
make[2]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/seq/aseqdump »
make[3]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/seq/aseqdump »
test -z "/usr/bin" || mkdir -p -- "/usr/bin"
  /usr/bin/install -c 'aseqdump' '/usr/bin/aseqdump'
test -z "/usr/share/man/man1" || mkdir -p -- "/usr/share/man/man1"
 /usr/bin/install -c -m 644 './aseqdump.1' '/usr/share/man/man1/aseqdump.1'
make[3]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/seq/aseqdump »
make[2]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/seq/aseqdump »
Making install in aseqnet
make[2]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/seq/aseqnet »
make[3]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/seq/aseqnet »
test -z "/usr/bin" || mkdir -p -- "/usr/bin"
  /usr/bin/install -c 'aseqnet' '/usr/bin/aseqnet'
test -z "/usr/share/man/man1" || mkdir -p -- "/usr/share/man/man1"
 /usr/bin/install -c -m 644 './aseqnet.1' '/usr/share/man/man1/aseqnet.1'
make[3]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/seq/aseqnet »
make[2]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/seq/aseqnet »
make[2]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/seq »
make[3]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/seq »
make[3]: Rien à faire pour « install-exec-am ».
make[3]: Rien à faire pour « install-data-am ».
make[3]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/seq »
make[2]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/seq »
make[1]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/seq »
make[1]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20 »
make[2]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20 »
make[2]: Rien à faire pour « install-exec-am ».
make[2]: Rien à faire pour « install-data-am ».
make[2]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20 »
make[1]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20 »
rabgye@ubuntumaya:~/alsa-utils-1.0.20$ rm -f ~/alsa-driver*
rm: ne peut enlever `/home/rabgye/alsa-driver-1.0.20': est un dossier
rabgye@ubuntumaya:~/alsa-utils-1.0.20$ rm -f ~/alsa-lib*
rm: ne peut enlever `/home/rabgye/alsa-lib-1.0.20': est un dossier
rabgye@ubuntumaya:~/alsa-utils-1.0.20$ rm -f ~/alsa-utils*
rm: ne peut enlever `/home/rabgye/alsa-utils-1.0.20': est un dossier
rabgye@ubuntumaya:~/alsa-utils-1.0.20$tout semble avoir marche sauf les trois derniers lignes.j'espere que les vacances ont ete bonnes merci

---

### Post by manjusri on 2009-06-25
> **manjusri said:**
> tout semble avoir marche avec quelques modifications sauf les trois dernieres lignes.voici les outputs:

































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































make[1]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/amixer »
if gcc -DHAVE_CONFIG_H -I. -I. -I../include -I../include    -g -O2 -MT amixer.o -MD -MP -MF ".deps/amixer.Tpo" -c -o amixer.o amixer.c; \
    then mv -f ".deps/amixer.Tpo" ".deps/amixer.Po"; else rm -f ".deps/amixer.Tpo"; exit 1; fi
amixer.c: In function ‘get_integer’:
amixer.c:244: attention : ignoring return value of ‘strtol’, declared with attribute warn_unused_result
amixer.c: In function ‘get_integer64’:
amixer.c:272: attention : ignoring return value of ‘strtol’, declared with attribute warn_unused_result
amixer.c: In function ‘set_volume_simple’:
amixer.c:358: attention : ignoring return value of ‘strtol’, declared with attribute warn_unused_result
gcc  -g -O2   -o amixer  amixer.o -lm -lasound -lm -ldl -lpthread
make[1]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/amixer »
Making all in amidi
make[1]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/amidi »
if gcc -DHAVE_CONFIG_H -I. -I. -I../include -I../include    -g -O2 -MT amidi.o -MD -MP -MF ".deps/amidi.Tpo" -c -o amidi.o amidi.c; \
    then mv -f ".deps/amidi.Tpo" ".deps/amidi.Po"; else rm -f ".deps/amidi.Tpo"; exit 1; fi
amidi.c: In function ‘main’:
amidi.c:658: attention : ignoring return value of ‘write’, declared with attribute warn_unused_result
gcc  -g -O2   -o amidi  amidi.o  -lasound -lm -ldl -lpthread
make[1]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/amidi »
Making all in alsaconf
make[1]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/alsaconf »
Making all in po
make[2]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/alsaconf/po »
35 messages traduits, 1 message non traduit.
34 messages traduits, 1 traduction approximative, 1 message non traduit.
make[2]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/alsaconf/po »
make[2]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/alsaconf »
make[2]: Rien à faire pour « all-am ».
make[2]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/alsaconf »
make[1]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/alsaconf »
Making all in aplay
make[1]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/aplay »
if gcc -DHAVE_CONFIG_H -I. -I. -I../include -I../include    -g -O2 -MT aplay.o -MD -MP -MF ".deps/aplay.Tpo" -c -o aplay.o aplay.c; \
    then mv -f ".deps/aplay.Tpo" ".deps/aplay.Po"; else rm -f ".deps/aplay.Tpo"; exit 1; fi
aplay.c: In function ‘end_voc’:
aplay.c:2158: attention : ignoring return value of ‘write’, declared with attribute warn_unused_result
aplay.c: In function ‘end_wave’:
aplay.c:2178: attention : ignoring return value of ‘write’, declared with attribute warn_unused_result
aplay.c:2180: attention : ignoring return value of ‘write’, declared with attribute warn_unused_result
aplay.c: In function ‘end_au’:
aplay.c:2193: attention : ignoring return value of ‘write’, declared with attribute warn_unused_result
gcc  -g -O2   -o aplay  aplay.o  -lrt -lasound -lm -ldl -lpthread
make[1]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/aplay »
Making all in iecset
make[1]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/iecset »
if gcc -DHAVE_CONFIG_H -I. -I. -I../include -I../include    -g -O2 -MT iecset.o -MD -MP -MF ".deps/iecset.Tpo" -c -o iecset.o iecset.c; \
    then mv -f ".deps/iecset.Tpo" ".deps/iecset.Po"; else rm -f ".deps/iecset.Tpo"; exit 1; fi
if gcc -DHAVE_CONFIG_H -I. -I. -I../include -I../include    -g -O2 -MT iecbits.o -MD -MP -MF ".deps/iecbits.Tpo" -c -o iecbits.o iecbits.c; \
    then mv -f ".deps/iecbits.Tpo" ".deps/iecbits.Po"; else rm -f ".deps/iecbits.Tpo"; exit 1; fi
gcc  -g -O2   -o iecset  iecset.o iecbits.o -lm -lasound -lm -ldl -lpthread
make[1]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/iecset »
Making all in speaker-test
make[1]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/speaker-test »
Making all in samples
make[2]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/speaker-test/samples »
make[2]: Rien à faire pour « all ».
make[2]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/speaker-test/samples »
make[2]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/speaker-test »
if gcc -DHAVE_CONFIG_H -I. -I. -I../include -I../include    -g -O2 -MT speaker-test.o -MD -MP -MF ".deps/speaker-test.Tpo" -c -o speaker-test.o speaker-test.c; \
    then mv -f ".deps/speaker-test.Tpo" ".deps/speaker-test.Po"; else rm -f ".deps/speaker-test.Tpo"; exit 1; fi
if gcc -DHAVE_CONFIG_H -I. -I. -I../include -I../include    -g -O2 -MT pink.o -MD -MP -MF ".deps/pink.Tpo" -c -o pink.o pink.c; \
    then mv -f ".deps/pink.Tpo" ".deps/pink.Po"; else rm -f ".deps/pink.Tpo"; exit 1; fi
gcc  -g -O2   -o speaker-test  speaker-test.o pink.o  -lm -lasound -lm -ldl -lpthread
make[2]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/speaker-test »
make[1]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/speaker-test »
Making all in seq
make[1]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/seq »
Making all in aconnect
make[2]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/seq/aconnect »
if gcc -DHAVE_CONFIG_H -I. -I. -I../../include -I../../include    -g -O2 -MT aconnect.o -MD -MP -MF ".deps/aconnect.Tpo" -c -o aconnect.o aconnect.c; \
    then mv -f ".deps/aconnect.Tpo" ".deps/aconnect.Po"; else rm -f ".deps/aconnect.Tpo"; exit 1; fi
gcc  -g -O2   -o aconnect  aconnect.o  -lasound -lm -ldl -lpthread
make[2]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/seq/aconnect »
Making all in aplaymidi
make[2]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/seq/aplaymidi »
if gcc -DHAVE_CONFIG_H -I. -I. -I../../include -I../../include    -g -O2 -MT aplaymidi.o -MD -MP -MF ".deps/aplaymidi.Tpo" -c -o aplaymidi.o aplaymidi.c; \
    then mv -f ".deps/aplaymidi.Tpo" ".deps/aplaymidi.Po"; else rm -f ".deps/aplaymidi.Tpo"; exit 1; fi
gcc  -g -O2   -o aplaymidi  aplaymidi.o  -lasound -lm -ldl -lpthread
if gcc -DHAVE_CONFIG_H -I. -I. -I../../include -I../../include    -g -O2 -MT arecordmidi.o -MD -MP -MF ".deps/arecordmidi.Tpo" -c -o arecordmidi.o arecordmidi.c; \
    then mv -f ".deps/arecordmidi.Tpo" ".deps/arecordmidi.Po"; else rm -f ".deps/arecordmidi.Tpo"; exit 1; fi
gcc  -g -O2   -o arecordmidi  arecordmidi.o  -lasound -lm -ldl -lpthread
make[2]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/seq/aplaymidi »
Making all in aseqdump
make[2]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/seq/aseqdump »
if gcc -DHAVE_CONFIG_H -I. -I. -I../../include -I../../include    -g -O2 -MT aseqdump.o -MD -MP -MF ".deps/aseqdump.Tpo" -c -o aseqdump.o aseqdump.c; \
    then mv -f ".deps/aseqdump.Tpo" ".deps/aseqdump.Po"; else rm -f ".deps/aseqdump.Tpo"; exit 1; fi
gcc  -g -O2   -o aseqdump  aseqdump.o  -lasound -lm -ldl -lpthread
make[2]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/seq/aseqdump »
Making all in aseqnet
make[2]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/seq/aseqnet »
if gcc -DHAVE_CONFIG_H -I. -I. -I../../include -I../../include    -g -O2 -MT aseqnet.o -MD -MP -MF ".deps/aseqnet.Tpo" -c -o aseqnet.o aseqnet.c; \
    then mv -f ".deps/aseqnet.Tpo" ".deps/aseqnet.Po"; else rm -f ".deps/aseqnet.Tpo"; exit 1; fi
aseqnet.c: In function ‘flush_writebuf’:
aseqnet.c:495: attention : ignoring return value of ‘write’, declared with attribute warn_unused_result
gcc  -g -O2   -o aseqnet  aseqnet.o  -lasound -lm -ldl -lpthread
make[2]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/seq/aseqnet »
make[2]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/seq »
make[2]: Rien à faire pour « all-am ».
make[2]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/seq »
make[1]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/seq »
make[1]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20 »
make[1]: Rien à faire pour « all-am ».
make[1]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20 »
rabgye@ubuntumaya:~/alsa-utils-1.0.20$ sudo make
Making all in include
make[1]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/include »
make  all-am
make[2]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/include »
make[2]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/include »
make[1]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/include »
Making all in alsactl
make[1]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/alsactl »
Making all in init
make[2]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/alsactl/init »
make[2]: Rien à faire pour « all ».
make[2]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/alsactl/init »
make[2]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/alsactl »
make[2]: Rien à faire pour « all-am ».
make[2]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/alsactl »
make[1]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/alsactl »
Making all in utils
make[1]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/utils »
make[1]: Rien à faire pour « all ».
make[1]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/utils »
Making all in m4
make[1]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/m4 »
make[1]: Rien à faire pour « all ».
make[1]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/m4 »
Making all in po
make[1]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/po »
make[1]: Rien à faire pour « all ».
make[1]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/po »
Making all in alsamixer
make[1]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/alsamixer »
make[1]: Rien à faire pour « all ».
make[1]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/alsamixer »
Making all in amixer
make[1]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/amixer »
make[1]: Rien à faire pour « all ».
make[1]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/amixer »
Making all in amidi
make[1]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/amidi »
make[1]: Rien à faire pour « all ».
make[1]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/amidi »
Making all in alsaconf
make[1]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/alsaconf »
Making all in po
make[2]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/alsaconf/po »
make[2]: Rien à faire pour « all ».
make[2]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/alsaconf/po »
make[2]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/alsaconf »
make[2]: Rien à faire pour « all-am ».
make[2]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/alsaconf »
make[1]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/alsaconf »
Making all in aplay
make[1]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/aplay »
make[1]: Rien à faire pour « all ».
make[1]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/aplay »
Making all in iecset
make[1]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/iecset »
make[1]: Rien à faire pour « all ».
make[1]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/iecset »
Making all in speaker-test
make[1]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/speaker-test »
Making all in samples
make[2]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/speaker-test/samples »
make[2]: Rien à faire pour « all ».
make[2]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/speaker-test/samples »
make[2]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/speaker-test »
make[2]: Rien à faire pour « all-am ».
make[2]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/speaker-test »
make[1]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/speaker-test »
Making all in seq
make[1]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/seq »
Making all in aconnect
make[2]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/seq/aconnect »
make[2]: Rien à faire pour « all ».
make[2]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/seq/aconnect »
Making all in aplaymidi
make[2]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/seq/aplaymidi »
make[2]: Rien à faire pour « all ».
make[2]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/seq/aplaymidi »
Making all in aseqdump
make[2]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/seq/aseqdump »
make[2]: Rien à faire pour « all ».
make[2]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/seq/aseqdump »
Making all in aseqnet
make[2]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/seq/aseqnet »
make[2]: Rien à faire pour « all ».
make[2]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/seq/aseqnet »
make[2]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/seq »
make[2]: Rien à faire pour « all-am ».
make[2]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/seq »
make[1]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/seq »
make[1]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20 »
make[1]: Rien à faire pour « all-am ».
make[1]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20 »
rabgye@ubuntumaya:~/alsa-utils-1.0.20$ sudo make install
Making install in include
make[1]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/include »
make[2]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/include »
make[2]: Rien à faire pour « install-exec-am ».
make[2]: Rien à faire pour « install-data-am ».
make[2]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/include »
make[1]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/include »
Making install in alsactl
make[1]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/alsactl »
Making install in init
make[2]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/alsactl/init »
make[3]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/alsactl/init »
make[3]: Rien à faire pour « install-exec-am ».
test -z "/usr/share/alsa/init" || mkdir -p -- "/usr/share/alsa/init"
 /usr/bin/install -c -m 644 '00main' '/usr/share/alsa/init/00main'
 /usr/bin/install -c -m 644 'default' '/usr/share/alsa/init/default'
 /usr/bin/install -c -m 644 'help' '/usr/share/alsa/init/help'
 /usr/bin/install -c -m 644 'info' '/usr/share/alsa/init/info'
 /usr/bin/install -c -m 644 'test' '/usr/share/alsa/init/test'
 /usr/bin/install -c -m 644 'hda' '/usr/share/alsa/init/hda'
make[3]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/alsactl/init »
make[2]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/alsactl/init »
make[2]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/alsactl »
make[3]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/alsactl »
test -z "/usr/sbin" || mkdir -p -- "/usr/sbin"
  /usr/bin/install -c 'alsactl' '/usr/sbin/alsactl'
test -z "/usr/share/man/man1" || mkdir -p -- "/usr/share/man/man1"
 /usr/bin/install -c -m 644 './alsactl.1' '/usr/share/man/man1/alsactl.1'
test -z "/usr/share/man/man7" || mkdir -p -- "/usr/share/man/man7"
 /usr/bin/install -c -m 644 './alsactl_init.7' '/usr/share/man/man7/alsactl_init.7'
make[3]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/alsactl »
make[2]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/alsactl »
make[1]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/alsactl »
Making install in utils
make[1]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/utils »
make[2]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/utils »
make[2]: Rien à faire pour « install-exec-am ».
make[2]: Rien à faire pour « install-data-am ».
make[2]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/utils »
make[1]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/utils »
Making install in m4
make[1]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/m4 »
make[2]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/m4 »
make[2]: Rien à faire pour « install-exec-am ».
make[2]: Rien à faire pour « install-data-am ».
make[2]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/m4 »
make[1]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/m4 »
Making install in po
make[1]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/po »
mkdir -p -- /usr/share
installing ja.gmo as /usr/share/locale/ja/LC_MESSAGES/alsa-utils.mo
if test "alsa-utils" = "gettext-tools"; then \
      mkdir -p -- /usr/share/gettext/po; \
      for file in Makefile.in.in remove-potcdate.sin quot.sed boldquot.sed [email]en@quot.header[/email] [email]en@boldquot.header[/email] insert-header.sin Rules-quot   Makevars.template; do \
        /usr/bin/install -c -m 644 ./$file \
                /usr/share/gettext/po/$file; \
      done; \
      for file in Makevars; do \
        rm -f /usr/share/gettext/po/$file; \
      done; \
    else \
      : ; \
    fi
make[1]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/po »
Making install in alsamixer
make[1]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/alsamixer »
make[2]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/alsamixer »
test -z "/usr/bin" || mkdir -p -- "/usr/bin"
  /usr/bin/install -c 'alsamixer' '/usr/bin/alsamixer'
test -z "/usr/share/man/man1" || mkdir -p -- "/usr/share/man/man1"
 /usr/bin/install -c -m 644 './alsamixer.1' '/usr/share/man/man1/alsamixer.1'
make[2]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/alsamixer »
make[1]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/alsamixer »
Making install in amixer
make[1]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/amixer »
make[2]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/amixer »
test -z "/usr/bin" || mkdir -p -- "/usr/bin"
  /usr/bin/install -c 'amixer' '/usr/bin/amixer'
test -z "/usr/share/man/man1" || mkdir -p -- "/usr/share/man/man1"
 /usr/bin/install -c -m 644 './amixer.1' '/usr/share/man/man1/amixer.1'
make[2]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/amixer »
make[1]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/amixer »
Making install in amidi
make[1]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/amidi »
make[2]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/amidi »
test -z "/usr/bin" || mkdir -p -- "/usr/bin"
  /usr/bin/install -c 'amidi' '/usr/bin/amidi'
test -z "/usr/share/man/man1" || mkdir -p -- "/usr/share/man/man1"
 /usr/bin/install -c -m 644 './amidi.1' '/usr/share/man/man1/amidi.1'
make[2]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/amidi »
make[1]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/amidi »
Making install in alsaconf
make[1]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/alsaconf »
Making install in po
make[2]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/alsaconf/po »
mkdir -p -- /usr/share
make[2]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/alsaconf/po »
make[2]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/alsaconf »
make[3]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/alsaconf »
test -z "/usr/sbin" || mkdir -p -- "/usr/sbin"
 /usr/bin/install -c 'alsaconf' '/usr/sbin/alsaconf'
 /usr/bin/install -c -m 644 alsaconf.8 /usr/share/man/man8/alsaconf.8
 /usr/bin/install -c -m 644 alsaconf.fr.8 /usr/share/man/fr/man8/alsaconf.8
make[3]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/alsaconf »
make[2]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/alsaconf »
make[1]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/alsaconf »
Making install in aplay
make[1]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/aplay »
make[2]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/aplay »
test -z "/usr/bin" || mkdir -p -- "/usr/bin"
  /usr/bin/install -c 'aplay' '/usr/bin/aplay'
make  install-exec-hook
make[3]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/aplay »
rm -f arecord
ln -s aplay arecord
rm -f /usr/bin/arecord
(cd /usr/bin && ln -s aplay arecord)
make[3]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/aplay »
test -z "/usr/share/man/man1" || mkdir -p -- "/usr/share/man/man1"
 /usr/bin/install -c -m 644 './aplay.1' '/usr/share/man/man1/aplay.1'
 /usr/bin/install -c -m 644 './arecord.1' '/usr/share/man/man1/arecord.1'
make  install-data-hook
make[3]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/aplay »
rm -f /usr/share/man/man1/arecord.1
(cd /usr/share/man/man1 && ln -s aplay.1 arecord.1)
make[3]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/aplay »
make[2]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/aplay »
make[1]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/aplay »
Making install in iecset
make[1]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/iecset »
make[2]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/iecset »
test -z "/usr/bin" || mkdir -p -- "/usr/bin"
  /usr/bin/install -c 'iecset' '/usr/bin/iecset'
test -z "/usr/share/man/man1" || mkdir -p -- "/usr/share/man/man1"
 /usr/bin/install -c -m 644 './iecset.1' '/usr/share/man/man1/iecset.1'
make[2]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/iecset »
make[1]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/iecset »
Making install in speaker-test
make[1]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/speaker-test »
Making install in samples
make[2]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/speaker-test/samples »
make[3]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/speaker-test/samples »
make[3]: Rien à faire pour « install-exec-am ».
test -z "/usr/share/alsa/speaker-test" || mkdir -p -- "/usr/share/alsa/speaker-test"
 /usr/bin/install -c -m 644 'sample_map.csv' '/usr/share/alsa/speaker-test/sample_map.csv'
test -z "/usr/share/sounds/alsa" || mkdir -p -- "/usr/share/sounds/alsa"
 /usr/bin/install -c -m 644 'Front_Left.wav' '/usr/share/sounds/alsa/Front_Left.wav'
 /usr/bin/install -c -m 644 'Rear_Center.wav' '/usr/share/sounds/alsa/Rear_Center.wav'
 /usr/bin/install -c -m 644 'Rear_Right.wav' '/usr/share/sounds/alsa/Rear_Right.wav'
 /usr/bin/install -c -m 644 'Side_Right.wav' '/usr/share/sounds/alsa/Side_Right.wav'
 /usr/bin/install -c -m 644 'Front_Center.wav' '/usr/share/sounds/alsa/Front_Center.wav'
 /usr/bin/install -c -m 644 'Front_Right.wav' '/usr/share/sounds/alsa/Front_Right.wav'
 /usr/bin/install -c -m 644 'Noise.wav' '/usr/share/sounds/alsa/Noise.wav'
 /usr/bin/install -c -m 644 'Rear_Left.wav' '/usr/share/sounds/alsa/Rear_Left.wav'
 /usr/bin/install -c -m 644 'Side_Left.wav' '/usr/share/sounds/alsa/Side_Left.wav'
make[3]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/speaker-test/samples »
make[2]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/speaker-test/samples »
make[2]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/speaker-test »
make[3]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/speaker-test »
test -z "/usr/bin" || mkdir -p -- "/usr/bin"
  /usr/bin/install -c 'speaker-test' '/usr/bin/speaker-test'
test -z "/usr/share/man/man1" || mkdir -p -- "/usr/share/man/man1"
 /usr/bin/install -c -m 644 './speaker-test.1' '/usr/share/man/man1/speaker-test.1'
make[3]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/speaker-test »
make[2]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/speaker-test »
make[1]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/speaker-test »
Making install in seq
make[1]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/seq »
Making install in aconnect
make[2]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/seq/aconnect »
make[3]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/seq/aconnect »
test -z "/usr/bin" || mkdir -p -- "/usr/bin"
  /usr/bin/install -c 'aconnect' '/usr/bin/aconnect'
test -z "/usr/share/man/man1" || mkdir -p -- "/usr/share/man/man1"
 /usr/bin/install -c -m 644 './aconnect.1' '/usr/share/man/man1/aconnect.1'
make[3]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/seq/aconnect »
make[2]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/seq/aconnect »
Making install in aplaymidi
make[2]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/seq/aplaymidi »
make[3]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/seq/aplaymidi »
test -z "/usr/bin" || mkdir -p -- "/usr/bin"
  /usr/bin/install -c 'aplaymidi' '/usr/bin/aplaymidi'
  /usr/bin/install -c 'arecordmidi' '/usr/bin/arecordmidi'
test -z "/usr/share/man/man1" || mkdir -p -- "/usr/share/man/man1"
 /usr/bin/install -c -m 644 './aplaymidi.1' '/usr/share/man/man1/aplaymidi.1'
 /usr/bin/install -c -m 644 './arecordmidi.1' '/usr/share/man/man1/arecordmidi.1'
make[3]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/seq/aplaymidi »
make[2]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/seq/aplaymidi »
Making install in aseqdump
make[2]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/seq/aseqdump »
make[3]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/seq/aseqdump »
test -z "/usr/bin" || mkdir -p -- "/usr/bin"
  /usr/bin/install -c 'aseqdump' '/usr/bin/aseqdump'
test -z "/usr/share/man/man1" || mkdir -p -- "/usr/share/man/man1"
 /usr/bin/install -c -m 644 './aseqdump.1' '/usr/share/man/man1/aseqdump.1'
make[3]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/seq/aseqdump »
make[2]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/seq/aseqdump »
Making install in aseqnet
make[2]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/seq/aseqnet »
make[3]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/seq/aseqnet »
test -z "/usr/bin" || mkdir -p -- "/usr/bin"
  /usr/bin/install -c 'aseqnet' '/usr/bin/aseqnet'
test -z "/usr/share/man/man1" || mkdir -p -- "/usr/share/man/man1"
 /usr/bin/install -c -m 644 './aseqnet.1' '/usr/share/man/man1/aseqnet.1'
make[3]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/seq/aseqnet »
make[2]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/seq/aseqnet »
make[2]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/seq »
make[3]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/seq »
make[3]: Rien à faire pour « install-exec-am ».
make[3]: Rien à faire pour « install-data-am ».
make[3]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/seq »
make[2]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/seq »
make[1]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/seq »
make[1]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20 »
make[2]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20 »
make[2]: Rien à faire pour « install-exec-am ».
make[2]: Rien à faire pour « install-data-am ».
make[2]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20 »
make[1]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20 »
rabgye@ubuntumaya:~/alsa-utils-1.0.20$ rm -f ~/alsa-driver*
rm: ne peut enlever `/home/rabgye/alsa-driver-1.0.20': est un dossier
rabgye@ubuntumaya:~/alsa-utils-1.0.20$ rm -f ~/alsa-lib*
rm: ne peut enlever `/home/rabgye/alsa-lib-1.0.20': est un dossier
rabgye@ubuntumaya:~/alsa-utils-1.0.20$ rm -f ~/alsa-utils*
rm: ne peut enlever `/home/rabgye/alsa-utils-1.0.20': est un dossier
rabgye@ubuntumaya:~/alsa-utils-1.0.20$ 

je n'ai pas teste ne sachant pas quoi faire pour les trois dernieres lignes.merci.j'espere que les vacances ont ete bonnes































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































make[1]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/amixer »
if gcc -DHAVE_CONFIG_H -I. -I. -I../include -I../include    -g -O2 -MT amixer.o -MD -MP -MF ".deps/amixer.Tpo" -c -o amixer.o amixer.c; \
    then mv -f ".deps/amixer.Tpo" ".deps/amixer.Po"; else rm -f ".deps/amixer.Tpo"; exit 1; fi
amixer.c: In function ‘get_integer’:
amixer.c:244: attention : ignoring return value of ‘strtol’, declared with attribute warn_unused_result
amixer.c: In function ‘get_integer64’:
amixer.c:272: attention : ignoring return value of ‘strtol’, declared with attribute warn_unused_result
amixer.c: In function ‘set_volume_simple’:
amixer.c:358: attention : ignoring return value of ‘strtol’, declared with attribute warn_unused_result
gcc  -g -O2   -o amixer  amixer.o -lm -lasound -lm -ldl -lpthread
make[1]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/amixer »
Making all in amidi
make[1]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/amidi »
if gcc -DHAVE_CONFIG_H -I. -I. -I../include -I../include    -g -O2 -MT amidi.o -MD -MP -MF ".deps/amidi.Tpo" -c -o amidi.o amidi.c; \
    then mv -f ".deps/amidi.Tpo" ".deps/amidi.Po"; else rm -f ".deps/amidi.Tpo"; exit 1; fi
amidi.c: In function ‘main’:
amidi.c:658: attention : ignoring return value of ‘write’, declared with attribute warn_unused_result
gcc  -g -O2   -o amidi  amidi.o  -lasound -lm -ldl -lpthread
make[1]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/amidi »
Making all in alsaconf
make[1]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/alsaconf »
Making all in po
make[2]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/alsaconf/po »
35 messages traduits, 1 message non traduit.
34 messages traduits, 1 traduction approximative, 1 message non traduit.
make[2]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/alsaconf/po »
make[2]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/alsaconf »
make[2]: Rien à faire pour « all-am ».
make[2]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/alsaconf »
make[1]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/alsaconf »
Making all in aplay
make[1]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/aplay »
if gcc -DHAVE_CONFIG_H -I. -I. -I../include -I../include    -g -O2 -MT aplay.o -MD -MP -MF ".deps/aplay.Tpo" -c -o aplay.o aplay.c; \
    then mv -f ".deps/aplay.Tpo" ".deps/aplay.Po"; else rm -f ".deps/aplay.Tpo"; exit 1; fi
aplay.c: In function ‘end_voc’:
aplay.c:2158: attention : ignoring return value of ‘write’, declared with attribute warn_unused_result
aplay.c: In function ‘end_wave’:
aplay.c:2178: attention : ignoring return value of ‘write’, declared with attribute warn_unused_result
aplay.c:2180: attention : ignoring return value of ‘write’, declared with attribute warn_unused_result
aplay.c: In function ‘end_au’:
aplay.c:2193: attention : ignoring return value of ‘write’, declared with attribute warn_unused_result
gcc  -g -O2   -o aplay  aplay.o  -lrt -lasound -lm -ldl -lpthread
make[1]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/aplay »
Making all in iecset
make[1]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/iecset »
if gcc -DHAVE_CONFIG_H -I. -I. -I../include -I../include    -g -O2 -MT iecset.o -MD -MP -MF ".deps/iecset.Tpo" -c -o iecset.o iecset.c; \
    then mv -f ".deps/iecset.Tpo" ".deps/iecset.Po"; else rm -f ".deps/iecset.Tpo"; exit 1; fi
if gcc -DHAVE_CONFIG_H -I. -I. -I../include -I../include    -g -O2 -MT iecbits.o -MD -MP -MF ".deps/iecbits.Tpo" -c -o iecbits.o iecbits.c; \
    then mv -f ".deps/iecbits.Tpo" ".deps/iecbits.Po"; else rm -f ".deps/iecbits.Tpo"; exit 1; fi
gcc  -g -O2   -o iecset  iecset.o iecbits.o -lm -lasound -lm -ldl -lpthread
make[1]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/iecset »
Making all in speaker-test
make[1]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/speaker-test »
Making all in samples
make[2]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/speaker-test/samples »
make[2]: Rien à faire pour « all ».
make[2]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/speaker-test/samples »
make[2]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/speaker-test »
if gcc -DHAVE_CONFIG_H -I. -I. -I../include -I../include    -g -O2 -MT speaker-test.o -MD -MP -MF ".deps/speaker-test.Tpo" -c -o speaker-test.o speaker-test.c; \
    then mv -f ".deps/speaker-test.Tpo" ".deps/speaker-test.Po"; else rm -f ".deps/speaker-test.Tpo"; exit 1; fi
if gcc -DHAVE_CONFIG_H -I. -I. -I../include -I../include    -g -O2 -MT pink.o -MD -MP -MF ".deps/pink.Tpo" -c -o pink.o pink.c; \
    then mv -f ".deps/pink.Tpo" ".deps/pink.Po"; else rm -f ".deps/pink.Tpo"; exit 1; fi
gcc  -g -O2   -o speaker-test  speaker-test.o pink.o  -lm -lasound -lm -ldl -lpthread
make[2]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/speaker-test »
make[1]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/speaker-test »
Making all in seq
make[1]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/seq »
Making all in aconnect
make[2]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/seq/aconnect »
if gcc -DHAVE_CONFIG_H -I. -I. -I../../include -I../../include    -g -O2 -MT aconnect.o -MD -MP -MF ".deps/aconnect.Tpo" -c -o aconnect.o aconnect.c; \
    then mv -f ".deps/aconnect.Tpo" ".deps/aconnect.Po"; else rm -f ".deps/aconnect.Tpo"; exit 1; fi
gcc  -g -O2   -o aconnect  aconnect.o  -lasound -lm -ldl -lpthread
make[2]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/seq/aconnect »
Making all in aplaymidi
make[2]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/seq/aplaymidi »
if gcc -DHAVE_CONFIG_H -I. -I. -I../../include -I../../include    -g -O2 -MT aplaymidi.o -MD -MP -MF ".deps/aplaymidi.Tpo" -c -o aplaymidi.o aplaymidi.c; \
    then mv -f ".deps/aplaymidi.Tpo" ".deps/aplaymidi.Po"; else rm -f ".deps/aplaymidi.Tpo"; exit 1; fi
gcc  -g -O2   -o aplaymidi  aplaymidi.o  -lasound -lm -ldl -lpthread
if gcc -DHAVE_CONFIG_H -I. -I. -I../../include -I../../include    -g -O2 -MT arecordmidi.o -MD -MP -MF ".deps/arecordmidi.Tpo" -c -o arecordmidi.o arecordmidi.c; \
    then mv -f ".deps/arecordmidi.Tpo" ".deps/arecordmidi.Po"; else rm -f ".deps/arecordmidi.Tpo"; exit 1; fi
gcc  -g -O2   -o arecordmidi  arecordmidi.o  -lasound -lm -ldl -lpthread
make[2]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/seq/aplaymidi »
Making all in aseqdump
make[2]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/seq/aseqdump »
if gcc -DHAVE_CONFIG_H -I. -I. -I../../include -I../../include    -g -O2 -MT aseqdump.o -MD -MP -MF ".deps/aseqdump.Tpo" -c -o aseqdump.o aseqdump.c; \
    then mv -f ".deps/aseqdump.Tpo" ".deps/aseqdump.Po"; else rm -f ".deps/aseqdump.Tpo"; exit 1; fi
gcc  -g -O2   -o aseqdump  aseqdump.o  -lasound -lm -ldl -lpthread
make[2]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/seq/aseqdump »
Making all in aseqnet
make[2]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/seq/aseqnet »
if gcc -DHAVE_CONFIG_H -I. -I. -I../../include -I../../include    -g -O2 -MT aseqnet.o -MD -MP -MF ".deps/aseqnet.Tpo" -c -o aseqnet.o aseqnet.c; \
    then mv -f ".deps/aseqnet.Tpo" ".deps/aseqnet.Po"; else rm -f ".deps/aseqnet.Tpo"; exit 1; fi
aseqnet.c: In function ‘flush_writebuf’:
aseqnet.c:495: attention : ignoring return value of ‘write’, declared with attribute warn_unused_result
gcc  -g -O2   -o aseqnet  aseqnet.o  -lasound -lm -ldl -lpthread
make[2]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/seq/aseqnet »
make[2]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/seq »
make[2]: Rien à faire pour « all-am ».
make[2]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/seq »
make[1]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/seq »
make[1]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20 »
make[1]: Rien à faire pour « all-am ».
make[1]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20 »
rabgye@ubuntumaya:~/alsa-utils-1.0.20$ sudo make
Making all in include
make[1]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/include »
make  all-am
make[2]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/include »
make[2]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/include »
make[1]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/include »
Making all in alsactl
make[1]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/alsactl »
Making all in init
make[2]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/alsactl/init »
make[2]: Rien à faire pour « all ».
make[2]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/alsactl/init »
make[2]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/alsactl »
make[2]: Rien à faire pour « all-am ».
make[2]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/alsactl »
make[1]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/alsactl »
Making all in utils
make[1]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/utils »
make[1]: Rien à faire pour « all ».
make[1]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/utils »
Making all in m4
make[1]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/m4 »
make[1]: Rien à faire pour « all ».
make[1]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/m4 »
Making all in po
make[1]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/po »
make[1]: Rien à faire pour « all ».
make[1]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/po »
Making all in alsamixer
make[1]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/alsamixer »
make[1]: Rien à faire pour « all ».
make[1]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/alsamixer »
Making all in amixer
make[1]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/amixer »
make[1]: Rien à faire pour « all ».
make[1]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/amixer »
Making all in amidi
make[1]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/amidi »
make[1]: Rien à faire pour « all ».
make[1]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/amidi »
Making all in alsaconf
make[1]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/alsaconf »
Making all in po
make[2]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/alsaconf/po »
make[2]: Rien à faire pour « all ».
make[2]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/alsaconf/po »
make[2]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/alsaconf »
make[2]: Rien à faire pour « all-am ».
make[2]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/alsaconf »
make[1]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/alsaconf »
Making all in aplay
make[1]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/aplay »
make[1]: Rien à faire pour « all ».
make[1]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/aplay »
Making all in iecset
make[1]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/iecset »
make[1]: Rien à faire pour « all ».
make[1]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/iecset »
Making all in speaker-test
make[1]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/speaker-test »
Making all in samples
make[2]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/speaker-test/samples »
make[2]: Rien à faire pour « all ».
make[2]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/speaker-test/samples »
make[2]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/speaker-test »
make[2]: Rien à faire pour « all-am ».
make[2]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/speaker-test »
make[1]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/speaker-test »
Making all in seq
make[1]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/seq »
Making all in aconnect
make[2]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/seq/aconnect »
make[2]: Rien à faire pour « all ».
make[2]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/seq/aconnect »
Making all in aplaymidi
make[2]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/seq/aplaymidi »
make[2]: Rien à faire pour « all ».
make[2]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/seq/aplaymidi »
Making all in aseqdump
make[2]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/seq/aseqdump »
make[2]: Rien à faire pour « all ».
make[2]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/seq/aseqdump »
Making all in aseqnet
make[2]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/seq/aseqnet »
make[2]: Rien à faire pour « all ».
make[2]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/seq/aseqnet »
make[2]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/seq »
make[2]: Rien à faire pour « all-am ».
make[2]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/seq »
make[1]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/seq »
make[1]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20 »
make[1]: Rien à faire pour « all-am ».
make[1]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20 »
rabgye@ubuntumaya:~/alsa-utils-1.0.20$ sudo make install
Making install in include
make[1]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/include »
make[2]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/include »
make[2]: Rien à faire pour « install-exec-am ».
make[2]: Rien à faire pour « install-data-am ».
make[2]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/include »
make[1]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/include »
Making install in alsactl
make[1]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/alsactl »
Making install in init
make[2]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/alsactl/init »
make[3]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/alsactl/init »
make[3]: Rien à faire pour « install-exec-am ».
test -z "/usr/share/alsa/init" || mkdir -p -- "/usr/share/alsa/init"
 /usr/bin/install -c -m 644 '00main' '/usr/share/alsa/init/00main'
 /usr/bin/install -c -m 644 'default' '/usr/share/alsa/init/default'
 /usr/bin/install -c -m 644 'help' '/usr/share/alsa/init/help'
 /usr/bin/install -c -m 644 'info' '/usr/share/alsa/init/info'
 /usr/bin/install -c -m 644 'test' '/usr/share/alsa/init/test'
 /usr/bin/install -c -m 644 'hda' '/usr/share/alsa/init/hda'
make[3]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/alsactl/init »
make[2]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/alsactl/init »
make[2]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/alsactl »
make[3]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/alsactl »
test -z "/usr/sbin" || mkdir -p -- "/usr/sbin"
  /usr/bin/install -c 'alsactl' '/usr/sbin/alsactl'
test -z "/usr/share/man/man1" || mkdir -p -- "/usr/share/man/man1"
 /usr/bin/install -c -m 644 './alsactl.1' '/usr/share/man/man1/alsactl.1'
test -z "/usr/share/man/man7" || mkdir -p -- "/usr/share/man/man7"
 /usr/bin/install -c -m 644 './alsactl_init.7' '/usr/share/man/man7/alsactl_init.7'
make[3]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/alsactl »
make[2]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/alsactl »
make[1]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/alsactl »
Making install in utils
make[1]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/utils »
make[2]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/utils »
make[2]: Rien à faire pour « install-exec-am ».
make[2]: Rien à faire pour « install-data-am ».
make[2]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/utils »
make[1]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/utils »
Making install in m4
make[1]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/m4 »
make[2]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/m4 »
make[2]: Rien à faire pour « install-exec-am ».
make[2]: Rien à faire pour « install-data-am ».
make[2]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/m4 »
make[1]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/m4 »
Making install in po
make[1]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/po »
mkdir -p -- /usr/share
installing ja.gmo as /usr/share/locale/ja/LC_MESSAGES/alsa-utils.mo
if test "alsa-utils" = "gettext-tools"; then \
      mkdir -p -- /usr/share/gettext/po; \
      for file in Makefile.in.in remove-potcdate.sin quot.sed boldquot.sed [email]en@quot.header[/email] [email]en@boldquot.header[/email] insert-header.sin Rules-quot   Makevars.template; do \
        /usr/bin/install -c -m 644 ./$file \
                /usr/share/gettext/po/$file; \
      done; \
      for file in Makevars; do \
        rm -f /usr/share/gettext/po/$file; \
      done; \
    else \
      : ; \
    fi
make[1]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/po »
Making install in alsamixer
make[1]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/alsamixer »
make[2]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/alsamixer »
test -z "/usr/bin" || mkdir -p -- "/usr/bin"
  /usr/bin/install -c 'alsamixer' '/usr/bin/alsamixer'
test -z "/usr/share/man/man1" || mkdir -p -- "/usr/share/man/man1"
 /usr/bin/install -c -m 644 './alsamixer.1' '/usr/share/man/man1/alsamixer.1'
make[2]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/alsamixer »
make[1]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/alsamixer »
Making install in amixer
make[1]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/amixer »
make[2]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/amixer »
test -z "/usr/bin" || mkdir -p -- "/usr/bin"
  /usr/bin/install -c 'amixer' '/usr/bin/amixer'
test -z "/usr/share/man/man1" || mkdir -p -- "/usr/share/man/man1"
 /usr/bin/install -c -m 644 './amixer.1' '/usr/share/man/man1/amixer.1'
make[2]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/amixer »
make[1]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/amixer »
Making install in amidi
make[1]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/amidi »
make[2]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/amidi »
test -z "/usr/bin" || mkdir -p -- "/usr/bin"
  /usr/bin/install -c 'amidi' '/usr/bin/amidi'
test -z "/usr/share/man/man1" || mkdir -p -- "/usr/share/man/man1"
 /usr/bin/install -c -m 644 './amidi.1' '/usr/share/man/man1/amidi.1'
make[2]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/amidi »
make[1]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/amidi »
Making install in alsaconf
make[1]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/alsaconf »
Making install in po
make[2]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/alsaconf/po »
mkdir -p -- /usr/share
make[2]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/alsaconf/po »
make[2]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/alsaconf »
make[3]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/alsaconf »
test -z "/usr/sbin" || mkdir -p -- "/usr/sbin"
 /usr/bin/install -c 'alsaconf' '/usr/sbin/alsaconf'
 /usr/bin/install -c -m 644 alsaconf.8 /usr/share/man/man8/alsaconf.8
 /usr/bin/install -c -m 644 alsaconf.fr.8 /usr/share/man/fr/man8/alsaconf.8
make[3]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/alsaconf »
make[2]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/alsaconf »
make[1]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/alsaconf »
Making install in aplay
make[1]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/aplay »
make[2]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/aplay »
test -z "/usr/bin" || mkdir -p -- "/usr/bin"
  /usr/bin/install -c 'aplay' '/usr/bin/aplay'
make  install-exec-hook
make[3]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/aplay »
rm -f arecord
ln -s aplay arecord
rm -f /usr/bin/arecord
(cd /usr/bin && ln -s aplay arecord)
make[3]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/aplay »
test -z "/usr/share/man/man1" || mkdir -p -- "/usr/share/man/man1"
 /usr/bin/install -c -m 644 './aplay.1' '/usr/share/man/man1/aplay.1'
 /usr/bin/install -c -m 644 './arecord.1' '/usr/share/man/man1/arecord.1'
make  install-data-hook
make[3]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/aplay »
rm -f /usr/share/man/man1/arecord.1
(cd /usr/share/man/man1 && ln -s aplay.1 arecord.1)
make[3]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/aplay »
make[2]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/aplay »
make[1]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/aplay »
Making install in iecset
make[1]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/iecset »
make[2]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/iecset »
test -z "/usr/bin" || mkdir -p -- "/usr/bin"
  /usr/bin/install -c 'iecset' '/usr/bin/iecset'
test -z "/usr/share/man/man1" || mkdir -p -- "/usr/share/man/man1"
 /usr/bin/install -c -m 644 './iecset.1' '/usr/share/man/man1/iecset.1'
make[2]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/iecset »
make[1]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/iecset »
Making install in speaker-test
make[1]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/speaker-test »
Making install in samples
make[2]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/speaker-test/samples »
make[3]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/speaker-test/samples »
make[3]: Rien à faire pour « install-exec-am ».
test -z "/usr/share/alsa/speaker-test" || mkdir -p -- "/usr/share/alsa/speaker-test"
 /usr/bin/install -c -m 644 'sample_map.csv' '/usr/share/alsa/speaker-test/sample_map.csv'
test -z "/usr/share/sounds/alsa" || mkdir -p -- "/usr/share/sounds/alsa"
 /usr/bin/install -c -m 644 'Front_Left.wav' '/usr/share/sounds/alsa/Front_Left.wav'
 /usr/bin/install -c -m 644 'Rear_Center.wav' '/usr/share/sounds/alsa/Rear_Center.wav'
 /usr/bin/install -c -m 644 'Rear_Right.wav' '/usr/share/sounds/alsa/Rear_Right.wav'
 /usr/bin/install -c -m 644 'Side_Right.wav' '/usr/share/sounds/alsa/Side_Right.wav'
 /usr/bin/install -c -m 644 'Front_Center.wav' '/usr/share/sounds/alsa/Front_Center.wav'
 /usr/bin/install -c -m 644 'Front_Right.wav' '/usr/share/sounds/alsa/Front_Right.wav'
 /usr/bin/install -c -m 644 'Noise.wav' '/usr/share/sounds/alsa/Noise.wav'
 /usr/bin/install -c -m 644 'Rear_Left.wav' '/usr/share/sounds/alsa/Rear_Left.wav'
 /usr/bin/install -c -m 644 'Side_Left.wav' '/usr/share/sounds/alsa/Side_Left.wav'
make[3]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/speaker-test/samples »
make[2]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/speaker-test/samples »
make[2]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/speaker-test »
make[3]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/speaker-test »
test -z "/usr/bin" || mkdir -p -- "/usr/bin"
  /usr/bin/install -c 'speaker-test' '/usr/bin/speaker-test'
test -z "/usr/share/man/man1" || mkdir -p -- "/usr/share/man/man1"
 /usr/bin/install -c -m 644 './speaker-test.1' '/usr/share/man/man1/speaker-test.1'
make[3]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/speaker-test »
make[2]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/speaker-test »
make[1]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/speaker-test »
Making install in seq
make[1]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/seq »
Making install in aconnect
make[2]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/seq/aconnect »
make[3]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/seq/aconnect »
test -z "/usr/bin" || mkdir -p -- "/usr/bin"
  /usr/bin/install -c 'aconnect' '/usr/bin/aconnect'
test -z "/usr/share/man/man1" || mkdir -p -- "/usr/share/man/man1"
 /usr/bin/install -c -m 644 './aconnect.1' '/usr/share/man/man1/aconnect.1'
make[3]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/seq/aconnect »
make[2]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/seq/aconnect »
Making install in aplaymidi
make[2]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/seq/aplaymidi »
make[3]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/seq/aplaymidi »
test -z "/usr/bin" || mkdir -p -- "/usr/bin"
  /usr/bin/install -c 'aplaymidi' '/usr/bin/aplaymidi'
  /usr/bin/install -c 'arecordmidi' '/usr/bin/arecordmidi'
test -z "/usr/share/man/man1" || mkdir -p -- "/usr/share/man/man1"
 /usr/bin/install -c -m 644 './aplaymidi.1' '/usr/share/man/man1/aplaymidi.1'
 /usr/bin/install -c -m 644 './arecordmidi.1' '/usr/share/man/man1/arecordmidi.1'
make[3]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/seq/aplaymidi »
make[2]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/seq/aplaymidi »
Making install in aseqdump
make[2]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/seq/aseqdump »
make[3]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/seq/aseqdump »
test -z "/usr/bin" || mkdir -p -- "/usr/bin"
  /usr/bin/install -c 'aseqdump' '/usr/bin/aseqdump'
test -z "/usr/share/man/man1" || mkdir -p -- "/usr/share/man/man1"
 /usr/bin/install -c -m 644 './aseqdump.1' '/usr/share/man/man1/aseqdump.1'
make[3]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/seq/aseqdump »
make[2]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/seq/aseqdump »
Making install in aseqnet
make[2]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/seq/aseqnet »
make[3]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/seq/aseqnet »
test -z "/usr/bin" || mkdir -p -- "/usr/bin"
  /usr/bin/install -c 'aseqnet' '/usr/bin/aseqnet'
test -z "/usr/share/man/man1" || mkdir -p -- "/usr/share/man/man1"
 /usr/bin/install -c -m 644 './aseqnet.1' '/usr/share/man/man1/aseqnet.1'
make[3]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/seq/aseqnet »
make[2]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/seq/aseqnet »
make[2]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/seq »
make[3]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/seq »
make[3]: Rien à faire pour « install-exec-am ».
make[3]: Rien à faire pour « install-data-am ».
make[3]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/seq »
make[2]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/seq »
make[1]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/seq »
make[1]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20 »
make[2]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20 »
make[2]: Rien à faire pour « install-exec-am ».
make[2]: Rien à faire pour « install-data-am ».
make[2]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20 »
make[1]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20 »
rabgye@ubuntumaya:~/alsa-utils-1.0.20$ rm -f ~/alsa-driver*
rm: ne peut enlever `/home/rabgye/alsa-driver-1.0.20': est un dossier
rabgye@ubuntumaya:~/alsa-utils-1.0.20$ rm -f ~/alsa-lib*
rm: ne peut enlever `/home/rabgye/alsa-lib-1.0.20': est un dossier
rabgye@ubuntumaya:~/alsa-utils-1.0.20$ rm -f ~/alsa-utils*
rm: ne peut enlever `/home/rabgye/alsa-utils-1.0.20': est un dossier
rabgye@ubuntumaya:~/alsa-utils-1.0.20$ 


































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































make[1]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/amixer »
if gcc -DHAVE_CONFIG_H -I. -I. -I../include -I../include    -g -O2 -MT amixer.o -MD -MP -MF ".deps/amixer.Tpo" -c -o amixer.o amixer.c; \
    then mv -f ".deps/amixer.Tpo" ".deps/amixer.Po"; else rm -f ".deps/amixer.Tpo"; exit 1; fi
amixer.c: In function ‘get_integer’:
amixer.c:244: attention : ignoring return value of ‘strtol’, declared with attribute warn_unused_result
amixer.c: In function ‘get_integer64’:
amixer.c:272: attention : ignoring return value of ‘strtol’, declared with attribute warn_unused_result
amixer.c: In function ‘set_volume_simple’:
amixer.c:358: attention : ignoring return value of ‘strtol’, declared with attribute warn_unused_result
gcc  -g -O2   -o amixer  amixer.o -lm -lasound -lm -ldl -lpthread
make[1]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/amixer »
Making all in amidi
make[1]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/amidi »
if gcc -DHAVE_CONFIG_H -I. -I. -I../include -I../include    -g -O2 -MT amidi.o -MD -MP -MF ".deps/amidi.Tpo" -c -o amidi.o amidi.c; \
    then mv -f ".deps/amidi.Tpo" ".deps/amidi.Po"; else rm -f ".deps/amidi.Tpo"; exit 1; fi
amidi.c: In function ‘main’:
amidi.c:658: attention : ignoring return value of ‘write’, declared with attribute warn_unused_result
gcc  -g -O2   -o amidi  amidi.o  -lasound -lm -ldl -lpthread
make[1]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/amidi »
Making all in alsaconf
make[1]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/alsaconf »
Making all in po
make[2]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/alsaconf/po »
35 messages traduits, 1 message non traduit.
34 messages traduits, 1 traduction approximative, 1 message non traduit.
make[2]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/alsaconf/po »
make[2]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/alsaconf »
make[2]: Rien à faire pour « all-am ».
make[2]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/alsaconf »
make[1]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/alsaconf »
Making all in aplay
make[1]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/aplay »
if gcc -DHAVE_CONFIG_H -I. -I. -I../include -I../include    -g -O2 -MT aplay.o -MD -MP -MF ".deps/aplay.Tpo" -c -o aplay.o aplay.c; \
    then mv -f ".deps/aplay.Tpo" ".deps/aplay.Po"; else rm -f ".deps/aplay.Tpo"; exit 1; fi
aplay.c: In function ‘end_voc’:
aplay.c:2158: attention : ignoring return value of ‘write’, declared with attribute warn_unused_result
aplay.c: In function ‘end_wave’:
aplay.c:2178: attention : ignoring return value of ‘write’, declared with attribute warn_unused_result
aplay.c:2180: attention : ignoring return value of ‘write’, declared with attribute warn_unused_result
aplay.c: In function ‘end_au’:
aplay.c:2193: attention : ignoring return value of ‘write’, declared with attribute warn_unused_result
gcc  -g -O2   -o aplay  aplay.o  -lrt -lasound -lm -ldl -lpthread
make[1]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/aplay »
Making all in iecset
make[1]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/iecset »
if gcc -DHAVE_CONFIG_H -I. -I. -I../include -I../include    -g -O2 -MT iecset.o -MD -MP -MF ".deps/iecset.Tpo" -c -o iecset.o iecset.c; \
    then mv -f ".deps/iecset.Tpo" ".deps/iecset.Po"; else rm -f ".deps/iecset.Tpo"; exit 1; fi
if gcc -DHAVE_CONFIG_H -I. -I. -I../include -I../include    -g -O2 -MT iecbits.o -MD -MP -MF ".deps/iecbits.Tpo" -c -o iecbits.o iecbits.c; \
    then mv -f ".deps/iecbits.Tpo" ".deps/iecbits.Po"; else rm -f ".deps/iecbits.Tpo"; exit 1; fi
gcc  -g -O2   -o iecset  iecset.o iecbits.o -lm -lasound -lm -ldl -lpthread
make[1]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/iecset »
Making all in speaker-test
make[1]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/speaker-test »
Making all in samples
make[2]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/speaker-test/samples »
make[2]: Rien à faire pour « all ».
make[2]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/speaker-test/samples »
make[2]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/speaker-test »
if gcc -DHAVE_CONFIG_H -I. -I. -I../include -I../include    -g -O2 -MT speaker-test.o -MD -MP -MF ".deps/speaker-test.Tpo" -c -o speaker-test.o speaker-test.c; \
    then mv -f ".deps/speaker-test.Tpo" ".deps/speaker-test.Po"; else rm -f ".deps/speaker-test.Tpo"; exit 1; fi
if gcc -DHAVE_CONFIG_H -I. -I. -I../include -I../include    -g -O2 -MT pink.o -MD -MP -MF ".deps/pink.Tpo" -c -o pink.o pink.c; \
    then mv -f ".deps/pink.Tpo" ".deps/pink.Po"; else rm -f ".deps/pink.Tpo"; exit 1; fi
gcc  -g -O2   -o speaker-test  speaker-test.o pink.o  -lm -lasound -lm -ldl -lpthread
make[2]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/speaker-test »
make[1]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/speaker-test »
Making all in seq
make[1]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/seq »
Making all in aconnect
make[2]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/seq/aconnect »
if gcc -DHAVE_CONFIG_H -I. -I. -I../../include -I../../include    -g -O2 -MT aconnect.o -MD -MP -MF ".deps/aconnect.Tpo" -c -o aconnect.o aconnect.c; \
    then mv -f ".deps/aconnect.Tpo" ".deps/aconnect.Po"; else rm -f ".deps/aconnect.Tpo"; exit 1; fi
gcc  -g -O2   -o aconnect  aconnect.o  -lasound -lm -ldl -lpthread
make[2]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/seq/aconnect »
Making all in aplaymidi
make[2]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/seq/aplaymidi »
if gcc -DHAVE_CONFIG_H -I. -I. -I../../include -I../../include    -g -O2 -MT aplaymidi.o -MD -MP -MF ".deps/aplaymidi.Tpo" -c -o aplaymidi.o aplaymidi.c; \
    then mv -f ".deps/aplaymidi.Tpo" ".deps/aplaymidi.Po"; else rm -f ".deps/aplaymidi.Tpo"; exit 1; fi
gcc  -g -O2   -o aplaymidi  aplaymidi.o  -lasound -lm -ldl -lpthread
if gcc -DHAVE_CONFIG_H -I. -I. -I../../include -I../../include    -g -O2 -MT arecordmidi.o -MD -MP -MF ".deps/arecordmidi.Tpo" -c -o arecordmidi.o arecordmidi.c; \
    then mv -f ".deps/arecordmidi.Tpo" ".deps/arecordmidi.Po"; else rm -f ".deps/arecordmidi.Tpo"; exit 1; fi
gcc  -g -O2   -o arecordmidi  arecordmidi.o  -lasound -lm -ldl -lpthread
make[2]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/seq/aplaymidi »
Making all in aseqdump
make[2]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/seq/aseqdump »
if gcc -DHAVE_CONFIG_H -I. -I. -I../../include -I../../include    -g -O2 -MT aseqdump.o -MD -MP -MF ".deps/aseqdump.Tpo" -c -o aseqdump.o aseqdump.c; \
    then mv -f ".deps/aseqdump.Tpo" ".deps/aseqdump.Po"; else rm -f ".deps/aseqdump.Tpo"; exit 1; fi
gcc  -g -O2   -o aseqdump  aseqdump.o  -lasound -lm -ldl -lpthread
make[2]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/seq/aseqdump »
Making all in aseqnet
make[2]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/seq/aseqnet »
if gcc -DHAVE_CONFIG_H -I. -I. -I../../include -I../../include    -g -O2 -MT aseqnet.o -MD -MP -MF ".deps/aseqnet.Tpo" -c -o aseqnet.o aseqnet.c; \
    then mv -f ".deps/aseqnet.Tpo" ".deps/aseqnet.Po"; else rm -f ".deps/aseqnet.Tpo"; exit 1; fi
aseqnet.c: In function ‘flush_writebuf’:
aseqnet.c:495: attention : ignoring return value of ‘write’, declared with attribute warn_unused_result
gcc  -g -O2   -o aseqnet  aseqnet.o  -lasound -lm -ldl -lpthread
make[2]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/seq/aseqnet »
make[2]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/seq »
make[2]: Rien à faire pour « all-am ».
make[2]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/seq »
make[1]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/seq »
make[1]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20 »
make[1]: Rien à faire pour « all-am ».
make[1]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20 »
rabgye@ubuntumaya:~/alsa-utils-1.0.20$ sudo make
Making all in include
make[1]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/include »
make  all-am
make[2]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/include »
make[2]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/include »
make[1]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/include »
Making all in alsactl
make[1]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/alsactl »
Making all in init
make[2]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/alsactl/init »
make[2]: Rien à faire pour « all ».
make[2]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/alsactl/init »
make[2]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/alsactl »
make[2]: Rien à faire pour « all-am ».
make[2]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/alsactl »
make[1]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/alsactl »
Making all in utils
make[1]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/utils »
make[1]: Rien à faire pour « all ».
make[1]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/utils »
Making all in m4
make[1]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/m4 »
make[1]: Rien à faire pour « all ».
make[1]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/m4 »
Making all in po
make[1]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/po »
make[1]: Rien à faire pour « all ».
make[1]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/po »
Making all in alsamixer
make[1]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/alsamixer »
make[1]: Rien à faire pour « all ».
make[1]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/alsamixer »
Making all in amixer
make[1]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/amixer »
make[1]: Rien à faire pour « all ».
make[1]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/amixer »
Making all in amidi
make[1]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/amidi »
make[1]: Rien à faire pour « all ».
make[1]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/amidi »
Making all in alsaconf
make[1]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/alsaconf »
Making all in po
make[2]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/alsaconf/po »
make[2]: Rien à faire pour « all ».
make[2]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/alsaconf/po »
make[2]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/alsaconf »
make[2]: Rien à faire pour « all-am ».
make[2]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/alsaconf »
make[1]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/alsaconf »
Making all in aplay
make[1]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/aplay »
make[1]: Rien à faire pour « all ».
make[1]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/aplay »
Making all in iecset
make[1]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/iecset »
make[1]: Rien à faire pour « all ».
make[1]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/iecset »
Making all in speaker-test
make[1]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/speaker-test »
Making all in samples
make[2]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/speaker-test/samples »
make[2]: Rien à faire pour « all ».
make[2]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/speaker-test/samples »
make[2]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/speaker-test »
make[2]: Rien à faire pour « all-am ».
make[2]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/speaker-test »
make[1]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/speaker-test »
Making all in seq
make[1]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/seq »
Making all in aconnect
make[2]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/seq/aconnect »
make[2]: Rien à faire pour « all ».
make[2]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/seq/aconnect »
Making all in aplaymidi
make[2]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/seq/aplaymidi »
make[2]: Rien à faire pour « all ».
make[2]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/seq/aplaymidi »
Making all in aseqdump
make[2]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/seq/aseqdump »
make[2]: Rien à faire pour « all ».
make[2]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/seq/aseqdump »
Making all in aseqnet
make[2]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/seq/aseqnet »
make[2]: Rien à faire pour « all ».
make[2]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/seq/aseqnet »
make[2]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/seq »
make[2]: Rien à faire pour « all-am ».
make[2]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/seq »
make[1]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/seq »
make[1]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20 »
make[1]: Rien à faire pour « all-am ».
make[1]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20 »
rabgye@ubuntumaya:~/alsa-utils-1.0.20$ sudo make install
Making install in include
make[1]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/include »
make[2]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/include »
make[2]: Rien à faire pour « install-exec-am ».
make[2]: Rien à faire pour « install-data-am ».
make[2]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/include »
make[1]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/include »
Making install in alsactl
make[1]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/alsactl »
Making install in init
make[2]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/alsactl/init »
make[3]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/alsactl/init »
make[3]: Rien à faire pour « install-exec-am ».
test -z "/usr/share/alsa/init" || mkdir -p -- "/usr/share/alsa/init"
 /usr/bin/install -c -m 644 '00main' '/usr/share/alsa/init/00main'
 /usr/bin/install -c -m 644 'default' '/usr/share/alsa/init/default'
 /usr/bin/install -c -m 644 'help' '/usr/share/alsa/init/help'
 /usr/bin/install -c -m 644 'info' '/usr/share/alsa/init/info'
 /usr/bin/install -c -m 644 'test' '/usr/share/alsa/init/test'
 /usr/bin/install -c -m 644 'hda' '/usr/share/alsa/init/hda'
make[3]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/alsactl/init »
make[2]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/alsactl/init »
make[2]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/alsactl »
make[3]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/alsactl »
test -z "/usr/sbin" || mkdir -p -- "/usr/sbin"
  /usr/bin/install -c 'alsactl' '/usr/sbin/alsactl'
test -z "/usr/share/man/man1" || mkdir -p -- "/usr/share/man/man1"
 /usr/bin/install -c -m 644 './alsactl.1' '/usr/share/man/man1/alsactl.1'
test -z "/usr/share/man/man7" || mkdir -p -- "/usr/share/man/man7"
 /usr/bin/install -c -m 644 './alsactl_init.7' '/usr/share/man/man7/alsactl_init.7'
make[3]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/alsactl »
make[2]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/alsactl »
make[1]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/alsactl »
Making install in utils
make[1]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/utils »
make[2]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/utils »
make[2]: Rien à faire pour « install-exec-am ».
make[2]: Rien à faire pour « install-data-am ».
make[2]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/utils »
make[1]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/utils »
Making install in m4
make[1]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/m4 »
make[2]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/m4 »
make[2]: Rien à faire pour « install-exec-am ».
make[2]: Rien à faire pour « install-data-am ».
make[2]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/m4 »
make[1]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/m4 »
Making install in po
make[1]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/po »
mkdir -p -- /usr/share
installing ja.gmo as /usr/share/locale/ja/LC_MESSAGES/alsa-utils.mo
if test "alsa-utils" = "gettext-tools"; then \
      mkdir -p -- /usr/share/gettext/po; \
      for file in Makefile.in.in remove-potcdate.sin quot.sed boldquot.sed [email]en@quot.header[/email] [email]en@boldquot.header[/email] insert-header.sin Rules-quot   Makevars.template; do \
        /usr/bin/install -c -m 644 ./$file \
                /usr/share/gettext/po/$file; \
      done; \
      for file in Makevars; do \
        rm -f /usr/share/gettext/po/$file; \
      done; \
    else \
      : ; \
    fi
make[1]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/po »
Making install in alsamixer
make[1]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/alsamixer »
make[2]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/alsamixer »
test -z "/usr/bin" || mkdir -p -- "/usr/bin"
  /usr/bin/install -c 'alsamixer' '/usr/bin/alsamixer'
test -z "/usr/share/man/man1" || mkdir -p -- "/usr/share/man/man1"
 /usr/bin/install -c -m 644 './alsamixer.1' '/usr/share/man/man1/alsamixer.1'
make[2]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/alsamixer »
make[1]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/alsamixer »
Making install in amixer
make[1]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/amixer »
make[2]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/amixer »
test -z "/usr/bin" || mkdir -p -- "/usr/bin"
  /usr/bin/install -c 'amixer' '/usr/bin/amixer'
test -z "/usr/share/man/man1" || mkdir -p -- "/usr/share/man/man1"
 /usr/bin/install -c -m 644 './amixer.1' '/usr/share/man/man1/amixer.1'
make[2]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/amixer »
make[1]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/amixer »
Making install in amidi
make[1]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/amidi »
make[2]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/amidi »
test -z "/usr/bin" || mkdir -p -- "/usr/bin"
  /usr/bin/install -c 'amidi' '/usr/bin/amidi'
test -z "/usr/share/man/man1" || mkdir -p -- "/usr/share/man/man1"
 /usr/bin/install -c -m 644 './amidi.1' '/usr/share/man/man1/amidi.1'
make[2]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/amidi »
make[1]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/amidi »
Making install in alsaconf
make[1]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/alsaconf »
Making install in po
make[2]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/alsaconf/po »
mkdir -p -- /usr/share
make[2]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/alsaconf/po »
make[2]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/alsaconf »
make[3]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/alsaconf »
test -z "/usr/sbin" || mkdir -p -- "/usr/sbin"
 /usr/bin/install -c 'alsaconf' '/usr/sbin/alsaconf'
 /usr/bin/install -c -m 644 alsaconf.8 /usr/share/man/man8/alsaconf.8
 /usr/bin/install -c -m 644 alsaconf.fr.8 /usr/share/man/fr/man8/alsaconf.8
make[3]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/alsaconf »
make[2]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/alsaconf »
make[1]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/alsaconf »
Making install in aplay
make[1]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/aplay »
make[2]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/aplay »
test -z "/usr/bin" || mkdir -p -- "/usr/bin"
  /usr/bin/install -c 'aplay' '/usr/bin/aplay'
make  install-exec-hook
make[3]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/aplay »
rm -f arecord
ln -s aplay arecord
rm -f /usr/bin/arecord
(cd /usr/bin && ln -s aplay arecord)
make[3]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/aplay »
test -z "/usr/share/man/man1" || mkdir -p -- "/usr/share/man/man1"
 /usr/bin/install -c -m 644 './aplay.1' '/usr/share/man/man1/aplay.1'
 /usr/bin/install -c -m 644 './arecord.1' '/usr/share/man/man1/arecord.1'
make  install-data-hook
make[3]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/aplay »
rm -f /usr/share/man/man1/arecord.1
(cd /usr/share/man/man1 && ln -s aplay.1 arecord.1)
make[3]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/aplay »
make[2]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/aplay »
make[1]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/aplay »
Making install in iecset
make[1]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/iecset »
make[2]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/iecset »
test -z "/usr/bin" || mkdir -p -- "/usr/bin"
  /usr/bin/install -c 'iecset' '/usr/bin/iecset'
test -z "/usr/share/man/man1" || mkdir -p -- "/usr/share/man/man1"
 /usr/bin/install -c -m 644 './iecset.1' '/usr/share/man/man1/iecset.1'
make[2]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/iecset »
make[1]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/iecset »
Making install in speaker-test
make[1]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/speaker-test »
Making install in samples
make[2]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/speaker-test/samples »
make[3]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/speaker-test/samples »
make[3]: Rien à faire pour « install-exec-am ».
test -z "/usr/share/alsa/speaker-test" || mkdir -p -- "/usr/share/alsa/speaker-test"
 /usr/bin/install -c -m 644 'sample_map.csv' '/usr/share/alsa/speaker-test/sample_map.csv'
test -z "/usr/share/sounds/alsa" || mkdir -p -- "/usr/share/sounds/alsa"
 /usr/bin/install -c -m 644 'Front_Left.wav' '/usr/share/sounds/alsa/Front_Left.wav'
 /usr/bin/install -c -m 644 'Rear_Center.wav' '/usr/share/sounds/alsa/Rear_Center.wav'
 /usr/bin/install -c -m 644 'Rear_Right.wav' '/usr/share/sounds/alsa/Rear_Right.wav'
 /usr/bin/install -c -m 644 'Side_Right.wav' '/usr/share/sounds/alsa/Side_Right.wav'
 /usr/bin/install -c -m 644 'Front_Center.wav' '/usr/share/sounds/alsa/Front_Center.wav'
 /usr/bin/install -c -m 644 'Front_Right.wav' '/usr/share/sounds/alsa/Front_Right.wav'
 /usr/bin/install -c -m 644 'Noise.wav' '/usr/share/sounds/alsa/Noise.wav'
 /usr/bin/install -c -m 644 'Rear_Left.wav' '/usr/share/sounds/alsa/Rear_Left.wav'
 /usr/bin/install -c -m 644 'Side_Left.wav' '/usr/share/sounds/alsa/Side_Left.wav'
make[3]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/speaker-test/samples »
make[2]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/speaker-test/samples »
make[2]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/speaker-test »
make[3]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/speaker-test »
test -z "/usr/bin" || mkdir -p -- "/usr/bin"
  /usr/bin/install -c 'speaker-test' '/usr/bin/speaker-test'
test -z "/usr/share/man/man1" || mkdir -p -- "/usr/share/man/man1"
 /usr/bin/install -c -m 644 './speaker-test.1' '/usr/share/man/man1/speaker-test.1'
make[3]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/speaker-test »
make[2]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/speaker-test »
make[1]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/speaker-test »
Making install in seq
make[1]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/seq »
Making install in aconnect
make[2]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/seq/aconnect »
make[3]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/seq/aconnect »
test -z "/usr/bin" || mkdir -p -- "/usr/bin"
  /usr/bin/install -c 'aconnect' '/usr/bin/aconnect'
test -z "/usr/share/man/man1" || mkdir -p -- "/usr/share/man/man1"
 /usr/bin/install -c -m 644 './aconnect.1' '/usr/share/man/man1/aconnect.1'
make[3]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/seq/aconnect »
make[2]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/seq/aconnect »
Making install in aplaymidi
make[2]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/seq/aplaymidi »
make[3]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/seq/aplaymidi »
test -z "/usr/bin" || mkdir -p -- "/usr/bin"
  /usr/bin/install -c 'aplaymidi' '/usr/bin/aplaymidi'
  /usr/bin/install -c 'arecordmidi' '/usr/bin/arecordmidi'
test -z "/usr/share/man/man1" || mkdir -p -- "/usr/share/man/man1"
 /usr/bin/install -c -m 644 './aplaymidi.1' '/usr/share/man/man1/aplaymidi.1'
 /usr/bin/install -c -m 644 './arecordmidi.1' '/usr/share/man/man1/arecordmidi.1'
make[3]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/seq/aplaymidi »
make[2]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/seq/aplaymidi »
Making install in aseqdump
make[2]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/seq/aseqdump »
make[3]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/seq/aseqdump »
test -z "/usr/bin" || mkdir -p -- "/usr/bin"
  /usr/bin/install -c 'aseqdump' '/usr/bin/aseqdump'
test -z "/usr/share/man/man1" || mkdir -p -- "/usr/share/man/man1"
 /usr/bin/install -c -m 644 './aseqdump.1' '/usr/share/man/man1/aseqdump.1'
make[3]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/seq/aseqdump »
make[2]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/seq/aseqdump »
Making install in aseqnet
make[2]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/seq/aseqnet »
make[3]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/seq/aseqnet »
test -z "/usr/bin" || mkdir -p -- "/usr/bin"
  /usr/bin/install -c 'aseqnet' '/usr/bin/aseqnet'
test -z "/usr/share/man/man1" || mkdir -p -- "/usr/share/man/man1"
 /usr/bin/install -c -m 644 './aseqnet.1' '/usr/share/man/man1/aseqnet.1'
make[3]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/seq/aseqnet »
make[2]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/seq/aseqnet »
make[2]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/seq »
make[3]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/seq »
make[3]: Rien à faire pour « install-exec-am ».
make[3]: Rien à faire pour « install-data-am ».
make[3]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/seq »
make[2]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/seq »
make[1]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/seq »
make[1]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20 »
make[2]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20 »
make[2]: Rien à faire pour « install-exec-am ».
make[2]: Rien à faire pour « install-data-am ».
make[2]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20 »
make[1]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20 »
rabgye@ubuntumaya:~/alsa-utils-1.0.20$ rm -f ~/alsa-driver*
rm: ne peut enlever `/home/rabgye/alsa-driver-1.0.20': est un dossier
rabgye@ubuntumaya:~/alsa-utils-1.0.20$ rm -f ~/alsa-lib*
rm: ne peut enlever `/home/rabgye/alsa-lib-1.0.20': est un dossier
rabgye@ubuntumaya:~/alsa-utils-1.0.20$ rm -f ~/alsa-utils*
rm: ne peut enlever `/home/rabgye/alsa-utils-1.0.20': est un dossier
rabgye@ubuntumaya:~/alsa-utils-1.0.20$ 


































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































make[1]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/amixer »
if gcc -DHAVE_CONFIG_H -I. -I. -I../include -I../include    -g -O2 -MT amixer.o -MD -MP -MF ".deps/amixer.Tpo" -c -o amixer.o amixer.c; \
    then mv -f ".deps/amixer.Tpo" ".deps/amixer.Po"; else rm -f ".deps/amixer.Tpo"; exit 1; fi
amixer.c: In function ‘get_integer’:
amixer.c:244: attention : ignoring return value of ‘strtol’, declared with attribute warn_unused_result
amixer.c: In function ‘get_integer64’:
amixer.c:272: attention : ignoring return value of ‘strtol’, declared with attribute warn_unused_result
amixer.c: In function ‘set_volume_simple’:
amixer.c:358: attention : ignoring return value of ‘strtol’, declared with attribute warn_unused_result
gcc  -g -O2   -o amixer  amixer.o -lm -lasound -lm -ldl -lpthread
make[1]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/amixer »
Making all in amidi
make[1]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/amidi »
if gcc -DHAVE_CONFIG_H -I. -I. -I../include -I../include    -g -O2 -MT amidi.o -MD -MP -MF ".deps/amidi.Tpo" -c -o amidi.o amidi.c; \
    then mv -f ".deps/amidi.Tpo" ".deps/amidi.Po"; else rm -f ".deps/amidi.Tpo"; exit 1; fi
amidi.c: In function ‘main’:
amidi.c:658: attention : ignoring return value of ‘write’, declared with attribute warn_unused_result
gcc  -g -O2   -o amidi  amidi.o  -lasound -lm -ldl -lpthread
make[1]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/amidi »
Making all in alsaconf
make[1]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/alsaconf »
Making all in po
make[2]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/alsaconf/po »
35 messages traduits, 1 message non traduit.
34 messages traduits, 1 traduction approximative, 1 message non traduit.
make[2]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/alsaconf/po »
make[2]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/alsaconf »
make[2]: Rien à faire pour « all-am ».
make[2]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/alsaconf »
make[1]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/alsaconf »
Making all in aplay
make[1]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/aplay »
if gcc -DHAVE_CONFIG_H -I. -I. -I../include -I../include    -g -O2 -MT aplay.o -MD -MP -MF ".deps/aplay.Tpo" -c -o aplay.o aplay.c; \
    then mv -f ".deps/aplay.Tpo" ".deps/aplay.Po"; else rm -f ".deps/aplay.Tpo"; exit 1; fi
aplay.c: In function ‘end_voc’:
aplay.c:2158: attention : ignoring return value of ‘write’, declared with attribute warn_unused_result
aplay.c: In function ‘end_wave’:
aplay.c:2178: attention : ignoring return value of ‘write’, declared with attribute warn_unused_result
aplay.c:2180: attention : ignoring return value of ‘write’, declared with attribute warn_unused_result
aplay.c: In function ‘end_au’:
aplay.c:2193: attention : ignoring return value of ‘write’, declared with attribute warn_unused_result
gcc  -g -O2   -o aplay  aplay.o  -lrt -lasound -lm -ldl -lpthread
make[1]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/aplay »
Making all in iecset
make[1]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/iecset »
if gcc -DHAVE_CONFIG_H -I. -I. -I../include -I../include    -g -O2 -MT iecset.o -MD -MP -MF ".deps/iecset.Tpo" -c -o iecset.o iecset.c; \
    then mv -f ".deps/iecset.Tpo" ".deps/iecset.Po"; else rm -f ".deps/iecset.Tpo"; exit 1; fi
if gcc -DHAVE_CONFIG_H -I. -I. -I../include -I../include    -g -O2 -MT iecbits.o -MD -MP -MF ".deps/iecbits.Tpo" -c -o iecbits.o iecbits.c; \
    then mv -f ".deps/iecbits.Tpo" ".deps/iecbits.Po"; else rm -f ".deps/iecbits.Tpo"; exit 1; fi
gcc  -g -O2   -o iecset  iecset.o iecbits.o -lm -lasound -lm -ldl -lpthread
make[1]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/iecset »
Making all in speaker-test
make[1]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/speaker-test »
Making all in samples
make[2]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/speaker-test/samples »
make[2]: Rien à faire pour « all ».
make[2]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/speaker-test/samples »
make[2]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/speaker-test »
if gcc -DHAVE_CONFIG_H -I. -I. -I../include -I../include    -g -O2 -MT speaker-test.o -MD -MP -MF ".deps/speaker-test.Tpo" -c -o speaker-test.o speaker-test.c; \
    then mv -f ".deps/speaker-test.Tpo" ".deps/speaker-test.Po"; else rm -f ".deps/speaker-test.Tpo"; exit 1; fi
if gcc -DHAVE_CONFIG_H -I. -I. -I../include -I../include    -g -O2 -MT pink.o -MD -MP -MF ".deps/pink.Tpo" -c -o pink.o pink.c; \
    then mv -f ".deps/pink.Tpo" ".deps/pink.Po"; else rm -f ".deps/pink.Tpo"; exit 1; fi
gcc  -g -O2   -o speaker-test  speaker-test.o pink.o  -lm -lasound -lm -ldl -lpthread
make[2]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/speaker-test »
make[1]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/speaker-test »
Making all in seq
make[1]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/seq »
Making all in aconnect
make[2]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/seq/aconnect »
if gcc -DHAVE_CONFIG_H -I. -I. -I../../include -I../../include    -g -O2 -MT aconnect.o -MD -MP -MF ".deps/aconnect.Tpo" -c -o aconnect.o aconnect.c; \
    then mv -f ".deps/aconnect.Tpo" ".deps/aconnect.Po"; else rm -f ".deps/aconnect.Tpo"; exit 1; fi
gcc  -g -O2   -o aconnect  aconnect.o  -lasound -lm -ldl -lpthread
make[2]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/seq/aconnect »
Making all in aplaymidi
make[2]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/seq/aplaymidi »
if gcc -DHAVE_CONFIG_H -I. -I. -I../../include -I../../include    -g -O2 -MT aplaymidi.o -MD -MP -MF ".deps/aplaymidi.Tpo" -c -o aplaymidi.o aplaymidi.c; \
    then mv -f ".deps/aplaymidi.Tpo" ".deps/aplaymidi.Po"; else rm -f ".deps/aplaymidi.Tpo"; exit 1; fi
gcc  -g -O2   -o aplaymidi  aplaymidi.o  -lasound -lm -ldl -lpthread
if gcc -DHAVE_CONFIG_H -I. -I. -I../../include -I../../include    -g -O2 -MT arecordmidi.o -MD -MP -MF ".deps/arecordmidi.Tpo" -c -o arecordmidi.o arecordmidi.c; \
    then mv -f ".deps/arecordmidi.Tpo" ".deps/arecordmidi.Po"; else rm -f ".deps/arecordmidi.Tpo"; exit 1; fi
gcc  -g -O2   -o arecordmidi  arecordmidi.o  -lasound -lm -ldl -lpthread
make[2]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/seq/aplaymidi »
Making all in aseqdump
make[2]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/seq/aseqdump »
if gcc -DHAVE_CONFIG_H -I. -I. -I../../include -I../../include    -g -O2 -MT aseqdump.o -MD -MP -MF ".deps/aseqdump.Tpo" -c -o aseqdump.o aseqdump.c; \
    then mv -f ".deps/aseqdump.Tpo" ".deps/aseqdump.Po"; else rm -f ".deps/aseqdump.Tpo"; exit 1; fi
gcc  -g -O2   -o aseqdump  aseqdump.o  -lasound -lm -ldl -lpthread
make[2]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/seq/aseqdump »
Making all in aseqnet
make[2]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/seq/aseqnet »
if gcc -DHAVE_CONFIG_H -I. -I. -I../../include -I../../include    -g -O2 -MT aseqnet.o -MD -MP -MF ".deps/aseqnet.Tpo" -c -o aseqnet.o aseqnet.c; \
    then mv -f ".deps/aseqnet.Tpo" ".deps/aseqnet.Po"; else rm -f ".deps/aseqnet.Tpo"; exit 1; fi
aseqnet.c: In function ‘flush_writebuf’:
aseqnet.c:495: attention : ignoring return value of ‘write’, declared with attribute warn_unused_result
gcc  -g -O2   -o aseqnet  aseqnet.o  -lasound -lm -ldl -lpthread
make[2]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/seq/aseqnet »
make[2]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/seq »
make[2]: Rien à faire pour « all-am ».
make[2]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/seq »
make[1]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/seq »
make[1]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20 »
make[1]: Rien à faire pour « all-am ».
make[1]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20 »
rabgye@ubuntumaya:~/alsa-utils-1.0.20$ sudo make
Making all in include
make[1]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/include »
make  all-am
make[2]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/include »
make[2]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/include »
make[1]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/include »
Making all in alsactl
make[1]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/alsactl »
Making all in init
make[2]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/alsactl/init »
make[2]: Rien à faire pour « all ».
make[2]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/alsactl/init »
make[2]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/alsactl »
make[2]: Rien à faire pour « all-am ».
make[2]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/alsactl »
make[1]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/alsactl »
Making all in utils
make[1]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/utils »
make[1]: Rien à faire pour « all ».
make[1]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/utils »
Making all in m4
make[1]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/m4 »
make[1]: Rien à faire pour « all ».
make[1]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/m4 »
Making all in po
make[1]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/po »
make[1]: Rien à faire pour « all ».
make[1]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/po »
Making all in alsamixer
make[1]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/alsamixer »
make[1]: Rien à faire pour « all ».
make[1]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/alsamixer »
Making all in amixer
make[1]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/amixer »
make[1]: Rien à faire pour « all ».
make[1]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/amixer »
Making all in amidi
make[1]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/amidi »
make[1]: Rien à faire pour « all ».
make[1]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/amidi »
Making all in alsaconf
make[1]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/alsaconf »
Making all in po
make[2]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/alsaconf/po »
make[2]: Rien à faire pour « all ».
make[2]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/alsaconf/po »
make[2]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/alsaconf »
make[2]: Rien à faire pour « all-am ».
make[2]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/alsaconf »
make[1]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/alsaconf »
Making all in aplay
make[1]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/aplay »
make[1]: Rien à faire pour « all ».
make[1]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/aplay »
Making all in iecset
make[1]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/iecset »
make[1]: Rien à faire pour « all ».
make[1]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/iecset »
Making all in speaker-test
make[1]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/speaker-test »
Making all in samples
make[2]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/speaker-test/samples »
make[2]: Rien à faire pour « all ».
make[2]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/speaker-test/samples »
make[2]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/speaker-test »
make[2]: Rien à faire pour « all-am ».
make[2]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/speaker-test »
make[1]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/speaker-test »
Making all in seq
make[1]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/seq »
Making all in aconnect
make[2]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/seq/aconnect »
make[2]: Rien à faire pour « all ».
make[2]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/seq/aconnect »
Making all in aplaymidi
make[2]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/seq/aplaymidi »
make[2]: Rien à faire pour « all ».
make[2]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/seq/aplaymidi »
Making all in aseqdump
make[2]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/seq/aseqdump »
make[2]: Rien à faire pour « all ».
make[2]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/seq/aseqdump »
Making all in aseqnet
make[2]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/seq/aseqnet »
make[2]: Rien à faire pour « all ».
make[2]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/seq/aseqnet »
make[2]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/seq »
make[2]: Rien à faire pour « all-am ».
make[2]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/seq »
make[1]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/seq »
make[1]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20 »
make[1]: Rien à faire pour « all-am ».
make[1]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20 »
rabgye@ubuntumaya:~/alsa-utils-1.0.20$ sudo make install
Making install in include
make[1]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/include »
make[2]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/include »
make[2]: Rien à faire pour « install-exec-am ».
make[2]: Rien à faire pour « install-data-am ».
make[2]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/include »
make[1]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/include »
Making install in alsactl
make[1]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/alsactl »
Making install in init
make[2]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/alsactl/init »
make[3]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/alsactl/init »
make[3]: Rien à faire pour « install-exec-am ».
test -z "/usr/share/alsa/init" || mkdir -p -- "/usr/share/alsa/init"
 /usr/bin/install -c -m 644 '00main' '/usr/share/alsa/init/00main'
 /usr/bin/install -c -m 644 'default' '/usr/share/alsa/init/default'
 /usr/bin/install -c -m 644 'help' '/usr/share/alsa/init/help'
 /usr/bin/install -c -m 644 'info' '/usr/share/alsa/init/info'
 /usr/bin/install -c -m 644 'test' '/usr/share/alsa/init/test'
 /usr/bin/install -c -m 644 'hda' '/usr/share/alsa/init/hda'
make[3]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/alsactl/init »
make[2]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/alsactl/init »
make[2]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/alsactl »
make[3]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/alsactl »
test -z "/usr/sbin" || mkdir -p -- "/usr/sbin"
  /usr/bin/install -c 'alsactl' '/usr/sbin/alsactl'
test -z "/usr/share/man/man1" || mkdir -p -- "/usr/share/man/man1"
 /usr/bin/install -c -m 644 './alsactl.1' '/usr/share/man/man1/alsactl.1'
test -z "/usr/share/man/man7" || mkdir -p -- "/usr/share/man/man7"
 /usr/bin/install -c -m 644 './alsactl_init.7' '/usr/share/man/man7/alsactl_init.7'
make[3]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/alsactl »
make[2]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/alsactl »
make[1]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/alsactl »
Making install in utils
make[1]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/utils »
make[2]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/utils »
make[2]: Rien à faire pour « install-exec-am ».
make[2]: Rien à faire pour « install-data-am ».
make[2]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/utils »
make[1]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/utils »
Making install in m4
make[1]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/m4 »
make[2]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/m4 »
make[2]: Rien à faire pour « install-exec-am ».
make[2]: Rien à faire pour « install-data-am ».
make[2]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/m4 »
make[1]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/m4 »
Making install in po
make[1]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/po »
mkdir -p -- /usr/share
installing ja.gmo as /usr/share/locale/ja/LC_MESSAGES/alsa-utils.mo
if test "alsa-utils" = "gettext-tools"; then \
      mkdir -p -- /usr/share/gettext/po; \
      for file in Makefile.in.in remove-potcdate.sin quot.sed boldquot.sed [email]en@quot.header[/email] [email]en@boldquot.header[/email] insert-header.sin Rules-quot   Makevars.template; do \
        /usr/bin/install -c -m 644 ./$file \
                /usr/share/gettext/po/$file; \
      done; \
      for file in Makevars; do \
        rm -f /usr/share/gettext/po/$file; \
      done; \
    else \
      : ; \
    fi
make[1]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/po »
Making install in alsamixer
make[1]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/alsamixer »
make[2]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/alsamixer »
test -z "/usr/bin" || mkdir -p -- "/usr/bin"
  /usr/bin/install -c 'alsamixer' '/usr/bin/alsamixer'
test -z "/usr/share/man/man1" || mkdir -p -- "/usr/share/man/man1"
 /usr/bin/install -c -m 644 './alsamixer.1' '/usr/share/man/man1/alsamixer.1'
make[2]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/alsamixer »
make[1]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/alsamixer »
Making install in amixer
make[1]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/amixer »
make[2]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/amixer »
test -z "/usr/bin" || mkdir -p -- "/usr/bin"
  /usr/bin/install -c 'amixer' '/usr/bin/amixer'
test -z "/usr/share/man/man1" || mkdir -p -- "/usr/share/man/man1"
 /usr/bin/install -c -m 644 './amixer.1' '/usr/share/man/man1/amixer.1'
make[2]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/amixer »
make[1]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/amixer »
Making install in amidi
make[1]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/amidi »
make[2]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/amidi »
test -z "/usr/bin" || mkdir -p -- "/usr/bin"
  /usr/bin/install -c 'amidi' '/usr/bin/amidi'
test -z "/usr/share/man/man1" || mkdir -p -- "/usr/share/man/man1"
 /usr/bin/install -c -m 644 './amidi.1' '/usr/share/man/man1/amidi.1'
make[2]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/amidi »
make[1]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/amidi »
Making install in alsaconf
make[1]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/alsaconf »
Making install in po
make[2]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/alsaconf/po »
mkdir -p -- /usr/share
make[2]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/alsaconf/po »
make[2]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/alsaconf »
make[3]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/alsaconf »
test -z "/usr/sbin" || mkdir -p -- "/usr/sbin"
 /usr/bin/install -c 'alsaconf' '/usr/sbin/alsaconf'
 /usr/bin/install -c -m 644 alsaconf.8 /usr/share/man/man8/alsaconf.8
 /usr/bin/install -c -m 644 alsaconf.fr.8 /usr/share/man/fr/man8/alsaconf.8
make[3]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/alsaconf »
make[2]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/alsaconf »
make[1]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/alsaconf »
Making install in aplay
make[1]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/aplay »
make[2]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/aplay »
test -z "/usr/bin" || mkdir -p -- "/usr/bin"
  /usr/bin/install -c 'aplay' '/usr/bin/aplay'
make  install-exec-hook
make[3]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/aplay »
rm -f arecord
ln -s aplay arecord
rm -f /usr/bin/arecord
(cd /usr/bin && ln -s aplay arecord)
make[3]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/aplay »
test -z "/usr/share/man/man1" || mkdir -p -- "/usr/share/man/man1"
 /usr/bin/install -c -m 644 './aplay.1' '/usr/share/man/man1/aplay.1'
 /usr/bin/install -c -m 644 './arecord.1' '/usr/share/man/man1/arecord.1'
make  install-data-hook
make[3]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/aplay »
rm -f /usr/share/man/man1/arecord.1
(cd /usr/share/man/man1 && ln -s aplay.1 arecord.1)
make[3]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/aplay »
make[2]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/aplay »
make[1]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/aplay »
Making install in iecset
make[1]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/iecset »
make[2]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/iecset »
test -z "/usr/bin" || mkdir -p -- "/usr/bin"
  /usr/bin/install -c 'iecset' '/usr/bin/iecset'
test -z "/usr/share/man/man1" || mkdir -p -- "/usr/share/man/man1"
 /usr/bin/install -c -m 644 './iecset.1' '/usr/share/man/man1/iecset.1'
make[2]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/iecset »
make[1]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/iecset »
Making install in speaker-test
make[1]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/speaker-test »
Making install in samples
make[2]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/speaker-test/samples »
make[3]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/speaker-test/samples »
make[3]: Rien à faire pour « install-exec-am ».
test -z "/usr/share/alsa/speaker-test" || mkdir -p -- "/usr/share/alsa/speaker-test"
 /usr/bin/install -c -m 644 'sample_map.csv' '/usr/share/alsa/speaker-test/sample_map.csv'
test -z "/usr/share/sounds/alsa" || mkdir -p -- "/usr/share/sounds/alsa"
 /usr/bin/install -c -m 644 'Front_Left.wav' '/usr/share/sounds/alsa/Front_Left.wav'
 /usr/bin/install -c -m 644 'Rear_Center.wav' '/usr/share/sounds/alsa/Rear_Center.wav'
 /usr/bin/install -c -m 644 'Rear_Right.wav' '/usr/share/sounds/alsa/Rear_Right.wav'
 /usr/bin/install -c -m 644 'Side_Right.wav' '/usr/share/sounds/alsa/Side_Right.wav'
 /usr/bin/install -c -m 644 'Front_Center.wav' '/usr/share/sounds/alsa/Front_Center.wav'
 /usr/bin/install -c -m 644 'Front_Right.wav' '/usr/share/sounds/alsa/Front_Right.wav'
 /usr/bin/install -c -m 644 'Noise.wav' '/usr/share/sounds/alsa/Noise.wav'
 /usr/bin/install -c -m 644 'Rear_Left.wav' '/usr/share/sounds/alsa/Rear_Left.wav'
 /usr/bin/install -c -m 644 'Side_Left.wav' '/usr/share/sounds/alsa/Side_Left.wav'
make[3]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/speaker-test/samples »
make[2]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/speaker-test/samples »
make[2]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/speaker-test »
make[3]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/speaker-test »
test -z "/usr/bin" || mkdir -p -- "/usr/bin"
  /usr/bin/install -c 'speaker-test' '/usr/bin/speaker-test'
test -z "/usr/share/man/man1" || mkdir -p -- "/usr/share/man/man1"
 /usr/bin/install -c -m 644 './speaker-test.1' '/usr/share/man/man1/speaker-test.1'
make[3]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/speaker-test »
make[2]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/speaker-test »
make[1]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/speaker-test »
Making install in seq
make[1]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/seq »
Making install in aconnect
make[2]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/seq/aconnect »
make[3]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/seq/aconnect »
test -z "/usr/bin" || mkdir -p -- "/usr/bin"
  /usr/bin/install -c 'aconnect' '/usr/bin/aconnect'
test -z "/usr/share/man/man1" || mkdir -p -- "/usr/share/man/man1"
 /usr/bin/install -c -m 644 './aconnect.1' '/usr/share/man/man1/aconnect.1'
make[3]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/seq/aconnect »
make[2]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/seq/aconnect »
Making install in aplaymidi
make[2]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/seq/aplaymidi »
make[3]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/seq/aplaymidi »
test -z "/usr/bin" || mkdir -p -- "/usr/bin"
  /usr/bin/install -c 'aplaymidi' '/usr/bin/aplaymidi'
  /usr/bin/install -c 'arecordmidi' '/usr/bin/arecordmidi'
test -z "/usr/share/man/man1" || mkdir -p -- "/usr/share/man/man1"
 /usr/bin/install -c -m 644 './aplaymidi.1' '/usr/share/man/man1/aplaymidi.1'
 /usr/bin/install -c -m 644 './arecordmidi.1' '/usr/share/man/man1/arecordmidi.1'
make[3]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/seq/aplaymidi »
make[2]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/seq/aplaymidi »
Making install in aseqdump
make[2]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/seq/aseqdump »
make[3]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/seq/aseqdump »
test -z "/usr/bin" || mkdir -p -- "/usr/bin"
  /usr/bin/install -c 'aseqdump' '/usr/bin/aseqdump'
test -z "/usr/share/man/man1" || mkdir -p -- "/usr/share/man/man1"
 /usr/bin/install -c -m 644 './aseqdump.1' '/usr/share/man/man1/aseqdump.1'
make[3]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/seq/aseqdump »
make[2]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/seq/aseqdump »
Making install in aseqnet
make[2]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/seq/aseqnet »
make[3]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/seq/aseqnet »
test -z "/usr/bin" || mkdir -p -- "/usr/bin"
  /usr/bin/install -c 'aseqnet' '/usr/bin/aseqnet'
test -z "/usr/share/man/man1" || mkdir -p -- "/usr/share/man/man1"
 /usr/bin/install -c -m 644 './aseqnet.1' '/usr/share/man/man1/aseqnet.1'
make[3]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/seq/aseqnet »
make[2]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/seq/aseqnet »
make[2]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/seq »
make[3]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/seq »
make[3]: Rien à faire pour « install-exec-am ».
make[3]: Rien à faire pour « install-data-am ».
make[3]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/seq »
make[2]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/seq »
make[1]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/seq »
make[1]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20 »
make[2]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20 »
make[2]: Rien à faire pour « install-exec-am ».
make[2]: Rien à faire pour « install-data-am ».
make[2]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20 »
make[1]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20 »
rabgye@ubuntumaya:~/alsa-utils-1.0.20$ rm -f ~/alsa-driver*
rm: ne peut enlever `/home/rabgye/alsa-driver-1.0.20': est un dossier
rabgye@ubuntumaya:~/alsa-utils-1.0.20$ rm -f ~/alsa-lib*
rm: ne peut enlever `/home/rabgye/alsa-lib-1.0.20': est un dossier
rabgye@ubuntumaya:~/alsa-utils-1.0.20$ rm -f ~/alsa-utils*
rm: ne peut enlever `/home/rabgye/alsa-utils-1.0.20': est un dossier
rabgye@ubuntumaya:~/alsa-utils-1.0.20$ 


































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































make[1]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/amixer »
if gcc -DHAVE_CONFIG_H -I. -I. -I../include -I../include    -g -O2 -MT amixer.o -MD -MP -MF ".deps/amixer.Tpo" -c -o amixer.o amixer.c; \
    then mv -f ".deps/amixer.Tpo" ".deps/amixer.Po"; else rm -f ".deps/amixer.Tpo"; exit 1; fi
amixer.c: In function ‘get_integer’:
amixer.c:244: attention : ignoring return value of ‘strtol’, declared with attribute warn_unused_result
amixer.c: In function ‘get_integer64’:
amixer.c:272: attention : ignoring return value of ‘strtol’, declared with attribute warn_unused_result
amixer.c: In function ‘set_volume_simple’:
amixer.c:358: attention : ignoring return value of ‘strtol’, declared with attribute warn_unused_result
gcc  -g -O2   -o amixer  amixer.o -lm -lasound -lm -ldl -lpthread
make[1]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/amixer »
Making all in amidi
make[1]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/amidi »
if gcc -DHAVE_CONFIG_H -I. -I. -I../include -I../include    -g -O2 -MT amidi.o -MD -MP -MF ".deps/amidi.Tpo" -c -o amidi.o amidi.c; \
    then mv -f ".deps/amidi.Tpo" ".deps/amidi.Po"; else rm -f ".deps/amidi.Tpo"; exit 1; fi
amidi.c: In function ‘main’:
amidi.c:658: attention : ignoring return value of ‘write’, declared with attribute warn_unused_result
gcc  -g -O2   -o amidi  amidi.o  -lasound -lm -ldl -lpthread
make[1]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/amidi »
Making all in alsaconf
make[1]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/alsaconf »
Making all in po
make[2]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/alsaconf/po »
35 messages traduits, 1 message non traduit.
34 messages traduits, 1 traduction approximative, 1 message non traduit.
make[2]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/alsaconf/po »
make[2]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/alsaconf »
make[2]: Rien à faire pour « all-am ».
make[2]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/alsaconf »
make[1]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/alsaconf »
Making all in aplay
make[1]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/aplay »
if gcc -DHAVE_CONFIG_H -I. -I. -I../include -I../include    -g -O2 -MT aplay.o -MD -MP -MF ".deps/aplay.Tpo" -c -o aplay.o aplay.c; \
    then mv -f ".deps/aplay.Tpo" ".deps/aplay.Po"; else rm -f ".deps/aplay.Tpo"; exit 1; fi
aplay.c: In function ‘end_voc’:
aplay.c:2158: attention : ignoring return value of ‘write’, declared with attribute warn_unused_result
aplay.c: In function ‘end_wave’:
aplay.c:2178: attention : ignoring return value of ‘write’, declared with attribute warn_unused_result
aplay.c:2180: attention : ignoring return value of ‘write’, declared with attribute warn_unused_result
aplay.c: In function ‘end_au’:
aplay.c:2193: attention : ignoring return value of ‘write’, declared with attribute warn_unused_result
gcc  -g -O2   -o aplay  aplay.o  -lrt -lasound -lm -ldl -lpthread
make[1]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/aplay »
Making all in iecset
make[1]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/iecset »
if gcc -DHAVE_CONFIG_H -I. -I. -I../include -I../include    -g -O2 -MT iecset.o -MD -MP -MF ".deps/iecset.Tpo" -c -o iecset.o iecset.c; \
    then mv -f ".deps/iecset.Tpo" ".deps/iecset.Po"; else rm -f ".deps/iecset.Tpo"; exit 1; fi
if gcc -DHAVE_CONFIG_H -I. -I. -I../include -I../include    -g -O2 -MT iecbits.o -MD -MP -MF ".deps/iecbits.Tpo" -c -o iecbits.o iecbits.c; \
    then mv -f ".deps/iecbits.Tpo" ".deps/iecbits.Po"; else rm -f ".deps/iecbits.Tpo"; exit 1; fi
gcc  -g -O2   -o iecset  iecset.o iecbits.o -lm -lasound -lm -ldl -lpthread
make[1]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/iecset »
Making all in speaker-test
make[1]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/speaker-test »
Making all in samples
make[2]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/speaker-test/samples »
make[2]: Rien à faire pour « all ».
make[2]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/speaker-test/samples »
make[2]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/speaker-test »
if gcc -DHAVE_CONFIG_H -I. -I. -I../include -I../include    -g -O2 -MT speaker-test.o -MD -MP -MF ".deps/speaker-test.Tpo" -c -o speaker-test.o speaker-test.c; \
    then mv -f ".deps/speaker-test.Tpo" ".deps/speaker-test.Po"; else rm -f ".deps/speaker-test.Tpo"; exit 1; fi
if gcc -DHAVE_CONFIG_H -I. -I. -I../include -I../include    -g -O2 -MT pink.o -MD -MP -MF ".deps/pink.Tpo" -c -o pink.o pink.c; \
    then mv -f ".deps/pink.Tpo" ".deps/pink.Po"; else rm -f ".deps/pink.Tpo"; exit 1; fi
gcc  -g -O2   -o speaker-test  speaker-test.o pink.o  -lm -lasound -lm -ldl -lpthread
make[2]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/speaker-test »
make[1]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/speaker-test »
Making all in seq
make[1]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/seq »
Making all in aconnect
make[2]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/seq/aconnect »
if gcc -DHAVE_CONFIG_H -I. -I. -I../../include -I../../include    -g -O2 -MT aconnect.o -MD -MP -MF ".deps/aconnect.Tpo" -c -o aconnect.o aconnect.c; \
    then mv -f ".deps/aconnect.Tpo" ".deps/aconnect.Po"; else rm -f ".deps/aconnect.Tpo"; exit 1; fi
gcc  -g -O2   -o aconnect  aconnect.o  -lasound -lm -ldl -lpthread
make[2]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/seq/aconnect »
Making all in aplaymidi
make[2]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/seq/aplaymidi »
if gcc -DHAVE_CONFIG_H -I. -I. -I../../include -I../../include    -g -O2 -MT aplaymidi.o -MD -MP -MF ".deps/aplaymidi.Tpo" -c -o aplaymidi.o aplaymidi.c; \
    then mv -f ".deps/aplaymidi.Tpo" ".deps/aplaymidi.Po"; else rm -f ".deps/aplaymidi.Tpo"; exit 1; fi
gcc  -g -O2   -o aplaymidi  aplaymidi.o  -lasound -lm -ldl -lpthread
if gcc -DHAVE_CONFIG_H -I. -I. -I../../include -I../../include    -g -O2 -MT arecordmidi.o -MD -MP -MF ".deps/arecordmidi.Tpo" -c -o arecordmidi.o arecordmidi.c; \
    then mv -f ".deps/arecordmidi.Tpo" ".deps/arecordmidi.Po"; else rm -f ".deps/arecordmidi.Tpo"; exit 1; fi
gcc  -g -O2   -o arecordmidi  arecordmidi.o  -lasound -lm -ldl -lpthread
make[2]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/seq/aplaymidi »
Making all in aseqdump
make[2]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/seq/aseqdump »
if gcc -DHAVE_CONFIG_H -I. -I. -I../../include -I../../include    -g -O2 -MT aseqdump.o -MD -MP -MF ".deps/aseqdump.Tpo" -c -o aseqdump.o aseqdump.c; \
    then mv -f ".deps/aseqdump.Tpo" ".deps/aseqdump.Po"; else rm -f ".deps/aseqdump.Tpo"; exit 1; fi
gcc  -g -O2   -o aseqdump  aseqdump.o  -lasound -lm -ldl -lpthread
make[2]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/seq/aseqdump »
Making all in aseqnet
make[2]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/seq/aseqnet »
if gcc -DHAVE_CONFIG_H -I. -I. -I../../include -I../../include    -g -O2 -MT aseqnet.o -MD -MP -MF ".deps/aseqnet.Tpo" -c -o aseqnet.o aseqnet.c; \
    then mv -f ".deps/aseqnet.Tpo" ".deps/aseqnet.Po"; else rm -f ".deps/aseqnet.Tpo"; exit 1; fi
aseqnet.c: In function ‘flush_writebuf’:
aseqnet.c:495: attention : ignoring return value of ‘write’, declared with attribute warn_unused_result
gcc  -g -O2   -o aseqnet  aseqnet.o  -lasound -lm -ldl -lpthread
make[2]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/seq/aseqnet »
make[2]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/seq »
make[2]: Rien à faire pour « all-am ».
make[2]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/seq »
make[1]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/seq »
make[1]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20 »
make[1]: Rien à faire pour « all-am ».
make[1]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20 »
rabgye@ubuntumaya:~/alsa-utils-1.0.20$ sudo make
Making all in include
make[1]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/include »
make  all-am
make[2]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/include »
make[2]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/include »
make[1]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/include »
Making all in alsactl
make[1]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/alsactl »
Making all in init
make[2]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/alsactl/init »
make[2]: Rien à faire pour « all ».
make[2]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/alsactl/init »
make[2]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/alsactl »
make[2]: Rien à faire pour « all-am ».
make[2]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/alsactl »
make[1]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/alsactl »
Making all in utils
make[1]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/utils »
make[1]: Rien à faire pour « all ».
make[1]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/utils »
Making all in m4
make[1]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/m4 »
make[1]: Rien à faire pour « all ».
make[1]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/m4 »
Making all in po
make[1]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/po »
make[1]: Rien à faire pour « all ».
make[1]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/po »
Making all in alsamixer
make[1]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/alsamixer »
make[1]: Rien à faire pour « all ».
make[1]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/alsamixer »
Making all in amixer
make[1]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/amixer »
make[1]: Rien à faire pour « all ».
make[1]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/amixer »
Making all in amidi
make[1]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/amidi »
make[1]: Rien à faire pour « all ».
make[1]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/amidi »
Making all in alsaconf
make[1]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/alsaconf »
Making all in po
make[2]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/alsaconf/po »
make[2]: Rien à faire pour « all ».
make[2]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/alsaconf/po »
make[2]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/alsaconf »
make[2]: Rien à faire pour « all-am ».
make[2]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/alsaconf »
make[1]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/alsaconf »
Making all in aplay
make[1]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/aplay »
make[1]: Rien à faire pour « all ».
make[1]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/aplay »
Making all in iecset
make[1]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/iecset »
make[1]: Rien à faire pour « all ».
make[1]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/iecset »
Making all in speaker-test
make[1]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/speaker-test »
Making all in samples
make[2]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/speaker-test/samples »
make[2]: Rien à faire pour « all ».
make[2]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/speaker-test/samples »
make[2]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/speaker-test »
make[2]: Rien à faire pour « all-am ».
make[2]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/speaker-test »
make[1]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/speaker-test »
Making all in seq
make[1]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/seq »
Making all in aconnect
make[2]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/seq/aconnect »
make[2]: Rien à faire pour « all ».
make[2]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/seq/aconnect »
Making all in aplaymidi
make[2]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/seq/aplaymidi »
make[2]: Rien à faire pour « all ».
make[2]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/seq/aplaymidi »
Making all in aseqdump
make[2]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/seq/aseqdump »
make[2]: Rien à faire pour « all ».
make[2]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/seq/aseqdump »
Making all in aseqnet
make[2]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/seq/aseqnet »
make[2]: Rien à faire pour « all ».
make[2]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/seq/aseqnet »
make[2]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/seq »
make[2]: Rien à faire pour « all-am ».
make[2]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/seq »
make[1]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/seq »
make[1]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20 »
make[1]: Rien à faire pour « all-am ».
make[1]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20 »
rabgye@ubuntumaya:~/alsa-utils-1.0.20$ sudo make install
Making install in include
make[1]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/include »
make[2]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/include »
make[2]: Rien à faire pour « install-exec-am ».
make[2]: Rien à faire pour « install-data-am ».
make[2]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/include »
make[1]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/include »
Making install in alsactl
make[1]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/alsactl »
Making install in init
make[2]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/alsactl/init »
make[3]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/alsactl/init »
make[3]: Rien à faire pour « install-exec-am ».
test -z "/usr/share/alsa/init" || mkdir -p -- "/usr/share/alsa/init"
 /usr/bin/install -c -m 644 '00main' '/usr/share/alsa/init/00main'
 /usr/bin/install -c -m 644 'default' '/usr/share/alsa/init/default'
 /usr/bin/install -c -m 644 'help' '/usr/share/alsa/init/help'
 /usr/bin/install -c -m 644 'info' '/usr/share/alsa/init/info'
 /usr/bin/install -c -m 644 'test' '/usr/share/alsa/init/test'
 /usr/bin/install -c -m 644 'hda' '/usr/share/alsa/init/hda'
make[3]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/alsactl/init »
make[2]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/alsactl/init »
make[2]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/alsactl »
make[3]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/alsactl »
test -z "/usr/sbin" || mkdir -p -- "/usr/sbin"
  /usr/bin/install -c 'alsactl' '/usr/sbin/alsactl'
test -z "/usr/share/man/man1" || mkdir -p -- "/usr/share/man/man1"
 /usr/bin/install -c -m 644 './alsactl.1' '/usr/share/man/man1/alsactl.1'
test -z "/usr/share/man/man7" || mkdir -p -- "/usr/share/man/man7"
 /usr/bin/install -c -m 644 './alsactl_init.7' '/usr/share/man/man7/alsactl_init.7'
make[3]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/alsactl »
make[2]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/alsactl »
make[1]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/alsactl »
Making install in utils
make[1]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/utils »
make[2]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/utils »
make[2]: Rien à faire pour « install-exec-am ».
make[2]: Rien à faire pour « install-data-am ».
make[2]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/utils »
make[1]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/utils »
Making install in m4
make[1]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/m4 »
make[2]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/m4 »
make[2]: Rien à faire pour « install-exec-am ».
make[2]: Rien à faire pour « install-data-am ».
make[2]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/m4 »
make[1]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/m4 »
Making install in po
make[1]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/po »
mkdir -p -- /usr/share
installing ja.gmo as /usr/share/locale/ja/LC_MESSAGES/alsa-utils.mo
if test "alsa-utils" = "gettext-tools"; then \
      mkdir -p -- /usr/share/gettext/po; \
      for file in Makefile.in.in remove-potcdate.sin quot.sed boldquot.sed [email]en@quot.header[/email] [email]en@boldquot.header[/email] insert-header.sin Rules-quot   Makevars.template; do \
        /usr/bin/install -c -m 644 ./$file \
                /usr/share/gettext/po/$file; \
      done; \
      for file in Makevars; do \
        rm -f /usr/share/gettext/po/$file; \
      done; \
    else \
      : ; \
    fi
make[1]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/po »
Making install in alsamixer
make[1]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/alsamixer »
make[2]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/alsamixer »
test -z "/usr/bin" || mkdir -p -- "/usr/bin"
  /usr/bin/install -c 'alsamixer' '/usr/bin/alsamixer'
test -z "/usr/share/man/man1" || mkdir -p -- "/usr/share/man/man1"
 /usr/bin/install -c -m 644 './alsamixer.1' '/usr/share/man/man1/alsamixer.1'
make[2]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/alsamixer »
make[1]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/alsamixer »
Making install in amixer
make[1]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/amixer »
make[2]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/amixer »
test -z "/usr/bin" || mkdir -p -- "/usr/bin"
  /usr/bin/install -c 'amixer' '/usr/bin/amixer'
test -z "/usr/share/man/man1" || mkdir -p -- "/usr/share/man/man1"
 /usr/bin/install -c -m 644 './amixer.1' '/usr/share/man/man1/amixer.1'
make[2]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/amixer »
make[1]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/amixer »
Making install in amidi
make[1]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/amidi »
make[2]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/amidi »
test -z "/usr/bin" || mkdir -p -- "/usr/bin"
  /usr/bin/install -c 'amidi' '/usr/bin/amidi'
test -z "/usr/share/man/man1" || mkdir -p -- "/usr/share/man/man1"
 /usr/bin/install -c -m 644 './amidi.1' '/usr/share/man/man1/amidi.1'
make[2]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/amidi »
make[1]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/amidi »
Making install in alsaconf
make[1]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/alsaconf »
Making install in po
make[2]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/alsaconf/po »
mkdir -p -- /usr/share
make[2]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/alsaconf/po »
make[2]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/alsaconf »
make[3]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/alsaconf »
test -z "/usr/sbin" || mkdir -p -- "/usr/sbin"
 /usr/bin/install -c 'alsaconf' '/usr/sbin/alsaconf'
 /usr/bin/install -c -m 644 alsaconf.8 /usr/share/man/man8/alsaconf.8
 /usr/bin/install -c -m 644 alsaconf.fr.8 /usr/share/man/fr/man8/alsaconf.8
make[3]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/alsaconf »
make[2]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/alsaconf »
make[1]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/alsaconf »
Making install in aplay
make[1]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/aplay »
make[2]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/aplay »
test -z "/usr/bin" || mkdir -p -- "/usr/bin"
  /usr/bin/install -c 'aplay' '/usr/bin/aplay'
make  install-exec-hook
make[3]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/aplay »
rm -f arecord
ln -s aplay arecord
rm -f /usr/bin/arecord
(cd /usr/bin && ln -s aplay arecord)
make[3]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/aplay »
test -z "/usr/share/man/man1" || mkdir -p -- "/usr/share/man/man1"
 /usr/bin/install -c -m 644 './aplay.1' '/usr/share/man/man1/aplay.1'
 /usr/bin/install -c -m 644 './arecord.1' '/usr/share/man/man1/arecord.1'
make  install-data-hook
make[3]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/aplay »
rm -f /usr/share/man/man1/arecord.1
(cd /usr/share/man/man1 && ln -s aplay.1 arecord.1)
make[3]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/aplay »
make[2]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/aplay »
make[1]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/aplay »
Making install in iecset
make[1]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/iecset »
make[2]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/iecset »
test -z "/usr/bin" || mkdir -p -- "/usr/bin"
  /usr/bin/install -c 'iecset' '/usr/bin/iecset'
test -z "/usr/share/man/man1" || mkdir -p -- "/usr/share/man/man1"
 /usr/bin/install -c -m 644 './iecset.1' '/usr/share/man/man1/iecset.1'
make[2]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/iecset »
make[1]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/iecset »
Making install in speaker-test
make[1]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/speaker-test »
Making install in samples
make[2]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/speaker-test/samples »
make[3]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/speaker-test/samples »
make[3]: Rien à faire pour « install-exec-am ».
test -z "/usr/share/alsa/speaker-test" || mkdir -p -- "/usr/share/alsa/speaker-test"
 /usr/bin/install -c -m 644 'sample_map.csv' '/usr/share/alsa/speaker-test/sample_map.csv'
test -z "/usr/share/sounds/alsa" || mkdir -p -- "/usr/share/sounds/alsa"
 /usr/bin/install -c -m 644 'Front_Left.wav' '/usr/share/sounds/alsa/Front_Left.wav'
 /usr/bin/install -c -m 644 'Rear_Center.wav' '/usr/share/sounds/alsa/Rear_Center.wav'
 /usr/bin/install -c -m 644 'Rear_Right.wav' '/usr/share/sounds/alsa/Rear_Right.wav'
 /usr/bin/install -c -m 644 'Side_Right.wav' '/usr/share/sounds/alsa/Side_Right.wav'
 /usr/bin/install -c -m 644 'Front_Center.wav' '/usr/share/sounds/alsa/Front_Center.wav'
 /usr/bin/install -c -m 644 'Front_Right.wav' '/usr/share/sounds/alsa/Front_Right.wav'
 /usr/bin/install -c -m 644 'Noise.wav' '/usr/share/sounds/alsa/Noise.wav'
 /usr/bin/install -c -m 644 'Rear_Left.wav' '/usr/share/sounds/alsa/Rear_Left.wav'
 /usr/bin/install -c -m 644 'Side_Left.wav' '/usr/share/sounds/alsa/Side_Left.wav'
make[3]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/speaker-test/samples »
make[2]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/speaker-test/samples »
make[2]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/speaker-test »
make[3]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/speaker-test »
test -z "/usr/bin" || mkdir -p -- "/usr/bin"
  /usr/bin/install -c 'speaker-test' '/usr/bin/speaker-test'
test -z "/usr/share/man/man1" || mkdir -p -- "/usr/share/man/man1"
 /usr/bin/install -c -m 644 './speaker-test.1' '/usr/share/man/man1/speaker-test.1'
make[3]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/speaker-test »
make[2]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/speaker-test »
make[1]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/speaker-test »
Making install in seq
make[1]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/seq »
Making install in aconnect
make[2]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/seq/aconnect »
make[3]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/seq/aconnect »
test -z "/usr/bin" || mkdir -p -- "/usr/bin"
  /usr/bin/install -c 'aconnect' '/usr/bin/aconnect'
test -z "/usr/share/man/man1" || mkdir -p -- "/usr/share/man/man1"
 /usr/bin/install -c -m 644 './aconnect.1' '/usr/share/man/man1/aconnect.1'
make[3]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/seq/aconnect »
make[2]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/seq/aconnect »
Making install in aplaymidi
make[2]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/seq/aplaymidi »
make[3]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/seq/aplaymidi »
test -z "/usr/bin" || mkdir -p -- "/usr/bin"
  /usr/bin/install -c 'aplaymidi' '/usr/bin/aplaymidi'
  /usr/bin/install -c 'arecordmidi' '/usr/bin/arecordmidi'
test -z "/usr/share/man/man1" || mkdir -p -- "/usr/share/man/man1"
 /usr/bin/install -c -m 644 './aplaymidi.1' '/usr/share/man/man1/aplaymidi.1'
 /usr/bin/install -c -m 644 './arecordmidi.1' '/usr/share/man/man1/arecordmidi.1'
make[3]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/seq/aplaymidi »
make[2]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/seq/aplaymidi »
Making install in aseqdump
make[2]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/seq/aseqdump »
make[3]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/seq/aseqdump »
test -z "/usr/bin" || mkdir -p -- "/usr/bin"
  /usr/bin/install -c 'aseqdump' '/usr/bin/aseqdump'
test -z "/usr/share/man/man1" || mkdir -p -- "/usr/share/man/man1"
 /usr/bin/install -c -m 644 './aseqdump.1' '/usr/share/man/man1/aseqdump.1'
make[3]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/seq/aseqdump »
make[2]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/seq/aseqdump »
Making install in aseqnet
make[2]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/seq/aseqnet »
make[3]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/seq/aseqnet »
test -z "/usr/bin" || mkdir -p -- "/usr/bin"
  /usr/bin/install -c 'aseqnet' '/usr/bin/aseqnet'
test -z "/usr/share/man/man1" || mkdir -p -- "/usr/share/man/man1"
 /usr/bin/install -c -m 644 './aseqnet.1' '/usr/share/man/man1/aseqnet.1'
make[3]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/seq/aseqnet »
make[2]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/seq/aseqnet »
make[2]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/seq »
make[3]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/seq »
make[3]: Rien à faire pour « install-exec-am ».
make[3]: Rien à faire pour « install-data-am ».
make[3]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/seq »
make[2]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/seq »
make[1]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/seq »
make[1]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20 »
make[2]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20 »
make[2]: Rien à faire pour « install-exec-am ».
make[2]: Rien à faire pour « install-data-am ».
make[2]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20 »
make[1]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20 »
rabgye@ubuntumaya:~/alsa-utils-1.0.20$ rm -f ~/alsa-driver*
rm: ne peut enlever `/home/rabgye/alsa-driver-1.0.20': est un dossier
rabgye@ubuntumaya:~/alsa-utils-1.0.20$ rm -f ~/alsa-lib*
rm: ne peut enlever `/home/rabgye/alsa-lib-1.0.20': est un dossier
rabgye@ubuntumaya:~/alsa-utils-1.0.20$ rm -f ~/alsa-utils*
rm: ne peut enlever `/home/rabgye/alsa-utils-1.0.20': est un dossier
rabgye@ubuntumaya:~/alsa-utils-1.0.20$ 


































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































make[1]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/amixer »
if gcc -DHAVE_CONFIG_H -I. -I. -I../include -I../include    -g -O2 -MT amixer.o -MD -MP -MF ".deps/amixer.Tpo" -c -o amixer.o amixer.c; \
    then mv -f ".deps/amixer.Tpo" ".deps/amixer.Po"; else rm -f ".deps/amixer.Tpo"; exit 1; fi
amixer.c: In function ‘get_integer’:
amixer.c:244: attention : ignoring return value of ‘strtol’, declared with attribute warn_unused_result
amixer.c: In function ‘get_integer64’:
amixer.c:272: attention : ignoring return value of ‘strtol’, declared with attribute warn_unused_result
amixer.c: In function ‘set_volume_simple’:
amixer.c:358: attention : ignoring return value of ‘strtol’, declared with attribute warn_unused_result
gcc  -g -O2   -o amixer  amixer.o -lm -lasound -lm -ldl -lpthread
make[1]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/amixer »
Making all in amidi
make[1]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/amidi »
if gcc -DHAVE_CONFIG_H -I. -I. -I../include -I../include    -g -O2 -MT amidi.o -MD -MP -MF ".deps/amidi.Tpo" -c -o amidi.o amidi.c; \
    then mv -f ".deps/amidi.Tpo" ".deps/amidi.Po"; else rm -f ".deps/amidi.Tpo"; exit 1; fi
amidi.c: In function ‘main’:
amidi.c:658: attention : ignoring return value of ‘write’, declared with attribute warn_unused_result
gcc  -g -O2   -o amidi  amidi.o  -lasound -lm -ldl -lpthread
make[1]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/amidi »
Making all in alsaconf
make[1]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/alsaconf »
Making all in po
make[2]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/alsaconf/po »
35 messages traduits, 1 message non traduit.
34 messages traduits, 1 traduction approximative, 1 message non traduit.
make[2]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/alsaconf/po »
make[2]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/alsaconf »
make[2]: Rien à faire pour « all-am ».
make[2]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/alsaconf »
make[1]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/alsaconf »
Making all in aplay
make[1]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/aplay »
if gcc -DHAVE_CONFIG_H -I. -I. -I../include -I../include    -g -O2 -MT aplay.o -MD -MP -MF ".deps/aplay.Tpo" -c -o aplay.o aplay.c; \
    then mv -f ".deps/aplay.Tpo" ".deps/aplay.Po"; else rm -f ".deps/aplay.Tpo"; exit 1; fi
aplay.c: In function ‘end_voc’:
aplay.c:2158: attention : ignoring return value of ‘write’, declared with attribute warn_unused_result
aplay.c: In function ‘end_wave’:
aplay.c:2178: attention : ignoring return value of ‘write’, declared with attribute warn_unused_result
aplay.c:2180: attention : ignoring return value of ‘write’, declared with attribute warn_unused_result
aplay.c: In function ‘end_au’:
aplay.c:2193: attention : ignoring return value of ‘write’, declared with attribute warn_unused_result
gcc  -g -O2   -o aplay  aplay.o  -lrt -lasound -lm -ldl -lpthread
make[1]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/aplay »
Making all in iecset
make[1]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/iecset »
if gcc -DHAVE_CONFIG_H -I. -I. -I../include -I../include    -g -O2 -MT iecset.o -MD -MP -MF ".deps/iecset.Tpo" -c -o iecset.o iecset.c; \
    then mv -f ".deps/iecset.Tpo" ".deps/iecset.Po"; else rm -f ".deps/iecset.Tpo"; exit 1; fi
if gcc -DHAVE_CONFIG_H -I. -I. -I../include -I../include    -g -O2 -MT iecbits.o -MD -MP -MF ".deps/iecbits.Tpo" -c -o iecbits.o iecbits.c; \
    then mv -f ".deps/iecbits.Tpo" ".deps/iecbits.Po"; else rm -f ".deps/iecbits.Tpo"; exit 1; fi
gcc  -g -O2   -o iecset  iecset.o iecbits.o -lm -lasound -lm -ldl -lpthread
make[1]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/iecset »
Making all in speaker-test
make[1]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/speaker-test »
Making all in samples
make[2]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/speaker-test/samples »
make[2]: Rien à faire pour « all ».
make[2]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/speaker-test/samples »
make[2]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/speaker-test »
if gcc -DHAVE_CONFIG_H -I. -I. -I../include -I../include    -g -O2 -MT speaker-test.o -MD -MP -MF ".deps/speaker-test.Tpo" -c -o speaker-test.o speaker-test.c; \
    then mv -f ".deps/speaker-test.Tpo" ".deps/speaker-test.Po"; else rm -f ".deps/speaker-test.Tpo"; exit 1; fi
if gcc -DHAVE_CONFIG_H -I. -I. -I../include -I../include    -g -O2 -MT pink.o -MD -MP -MF ".deps/pink.Tpo" -c -o pink.o pink.c; \
    then mv -f ".deps/pink.Tpo" ".deps/pink.Po"; else rm -f ".deps/pink.Tpo"; exit 1; fi
gcc  -g -O2   -o speaker-test  speaker-test.o pink.o  -lm -lasound -lm -ldl -lpthread
make[2]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/speaker-test »
make[1]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/speaker-test »
Making all in seq
make[1]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/seq »
Making all in aconnect
make[2]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/seq/aconnect »
if gcc -DHAVE_CONFIG_H -I. -I. -I../../include -I../../include    -g -O2 -MT aconnect.o -MD -MP -MF ".deps/aconnect.Tpo" -c -o aconnect.o aconnect.c; \
    then mv -f ".deps/aconnect.Tpo" ".deps/aconnect.Po"; else rm -f ".deps/aconnect.Tpo"; exit 1; fi
gcc  -g -O2   -o aconnect  aconnect.o  -lasound -lm -ldl -lpthread
make[2]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/seq/aconnect »
Making all in aplaymidi
make[2]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/seq/aplaymidi »
if gcc -DHAVE_CONFIG_H -I. -I. -I../../include -I../../include    -g -O2 -MT aplaymidi.o -MD -MP -MF ".deps/aplaymidi.Tpo" -c -o aplaymidi.o aplaymidi.c; \
    then mv -f ".deps/aplaymidi.Tpo" ".deps/aplaymidi.Po"; else rm -f ".deps/aplaymidi.Tpo"; exit 1; fi
gcc  -g -O2   -o aplaymidi  aplaymidi.o  -lasound -lm -ldl -lpthread
if gcc -DHAVE_CONFIG_H -I. -I. -I../../include -I../../include    -g -O2 -MT arecordmidi.o -MD -MP -MF ".deps/arecordmidi.Tpo" -c -o arecordmidi.o arecordmidi.c; \
    then mv -f ".deps/arecordmidi.Tpo" ".deps/arecordmidi.Po"; else rm -f ".deps/arecordmidi.Tpo"; exit 1; fi
gcc  -g -O2   -o arecordmidi  arecordmidi.o  -lasound -lm -ldl -lpthread
make[2]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/seq/aplaymidi »
Making all in aseqdump
make[2]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/seq/aseqdump »
if gcc -DHAVE_CONFIG_H -I. -I. -I../../include -I../../include    -g -O2 -MT aseqdump.o -MD -MP -MF ".deps/aseqdump.Tpo" -c -o aseqdump.o aseqdump.c; \
    then mv -f ".deps/aseqdump.Tpo" ".deps/aseqdump.Po"; else rm -f ".deps/aseqdump.Tpo"; exit 1; fi
gcc  -g -O2   -o aseqdump  aseqdump.o  -lasound -lm -ldl -lpthread
make[2]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/seq/aseqdump »
Making all in aseqnet
make[2]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/seq/aseqnet »
if gcc -DHAVE_CONFIG_H -I. -I. -I../../include -I../../include    -g -O2 -MT aseqnet.o -MD -MP -MF ".deps/aseqnet.Tpo" -c -o aseqnet.o aseqnet.c; \
    then mv -f ".deps/aseqnet.Tpo" ".deps/aseqnet.Po"; else rm -f ".deps/aseqnet.Tpo"; exit 1; fi
aseqnet.c: In function ‘flush_writebuf’:
aseqnet.c:495: attention : ignoring return value of ‘write’, declared with attribute warn_unused_result
gcc  -g -O2   -o aseqnet  aseqnet.o  -lasound -lm -ldl -lpthread
make[2]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/seq/aseqnet »
make[2]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/seq »
make[2]: Rien à faire pour « all-am ».
make[2]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/seq »
make[1]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/seq »
make[1]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20 »
make[1]: Rien à faire pour « all-am ».
make[1]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20 »
rabgye@ubuntumaya:~/alsa-utils-1.0.20$ sudo make
Making all in include
make[1]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/include »
make  all-am
make[2]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/include »
make[2]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/include »
make[1]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/include »
Making all in alsactl
make[1]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/alsactl »
Making all in init
make[2]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/alsactl/init »
make[2]: Rien à faire pour « all ».
make[2]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/alsactl/init »
make[2]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/alsactl »
make[2]: Rien à faire pour « all-am ».
make[2]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/alsactl »
make[1]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/alsactl »
Making all in utils
make[1]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/utils »
make[1]: Rien à faire pour « all ».
make[1]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/utils »
Making all in m4
make[1]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/m4 »
make[1]: Rien à faire pour « all ».
make[1]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/m4 »
Making all in po
make[1]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/po »
make[1]: Rien à faire pour « all ».
make[1]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/po »
Making all in alsamixer
make[1]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/alsamixer »
make[1]: Rien à faire pour « all ».
make[1]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/alsamixer »
Making all in amixer
make[1]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/amixer »
make[1]: Rien à faire pour « all ».
make[1]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/amixer »
Making all in amidi
make[1]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/amidi »
make[1]: Rien à faire pour « all ».
make[1]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/amidi »
Making all in alsaconf
make[1]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/alsaconf »
Making all in po
make[2]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/alsaconf/po »
make[2]: Rien à faire pour « all ».
make[2]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/alsaconf/po »
make[2]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/alsaconf »
make[2]: Rien à faire pour « all-am ».
make[2]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/alsaconf »
make[1]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/alsaconf »
Making all in aplay
make[1]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/aplay »
make[1]: Rien à faire pour « all ».
make[1]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/aplay »
Making all in iecset
make[1]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/iecset »
make[1]: Rien à faire pour « all ».
make[1]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/iecset »
Making all in speaker-test
make[1]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/speaker-test »
Making all in samples
make[2]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/speaker-test/samples »
make[2]: Rien à faire pour « all ».
make[2]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/speaker-test/samples »
make[2]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/speaker-test »
make[2]: Rien à faire pour « all-am ».
make[2]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/speaker-test »
make[1]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/speaker-test »
Making all in seq
make[1]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/seq »
Making all in aconnect
make[2]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/seq/aconnect »
make[2]: Rien à faire pour « all ».
make[2]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/seq/aconnect »
Making all in aplaymidi
make[2]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/seq/aplaymidi »
make[2]: Rien à faire pour « all ».
make[2]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/seq/aplaymidi »
Making all in aseqdump
make[2]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/seq/aseqdump »
make[2]: Rien à faire pour « all ».
make[2]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/seq/aseqdump »
Making all in aseqnet
make[2]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/seq/aseqnet »
make[2]: Rien à faire pour « all ».
make[2]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/seq/aseqnet »
make[2]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/seq »
make[2]: Rien à faire pour « all-am ».
make[2]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/seq »
make[1]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/seq »
make[1]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20 »
make[1]: Rien à faire pour « all-am ».
make[1]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20 »
rabgye@ubuntumaya:~/alsa-utils-1.0.20$ sudo make install
Making install in include
make[1]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/include »
make[2]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/include »
make[2]: Rien à faire pour « install-exec-am ».
make[2]: Rien à faire pour « install-data-am ».
make[2]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/include »
make[1]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/include »
Making install in alsactl
make[1]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/alsactl »
Making install in init
make[2]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/alsactl/init »
make[3]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/alsactl/init »
make[3]: Rien à faire pour « install-exec-am ».
test -z "/usr/share/alsa/init" || mkdir -p -- "/usr/share/alsa/init"
 /usr/bin/install -c -m 644 '00main' '/usr/share/alsa/init/00main'
 /usr/bin/install -c -m 644 'default' '/usr/share/alsa/init/default'
 /usr/bin/install -c -m 644 'help' '/usr/share/alsa/init/help'
 /usr/bin/install -c -m 644 'info' '/usr/share/alsa/init/info'
 /usr/bin/install -c -m 644 'test' '/usr/share/alsa/init/test'
 /usr/bin/install -c -m 644 'hda' '/usr/share/alsa/init/hda'
make[3]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/alsactl/init »
make[2]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/alsactl/init »
make[2]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/alsactl »
make[3]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/alsactl »
test -z "/usr/sbin" || mkdir -p -- "/usr/sbin"
  /usr/bin/install -c 'alsactl' '/usr/sbin/alsactl'
test -z "/usr/share/man/man1" || mkdir -p -- "/usr/share/man/man1"
 /usr/bin/install -c -m 644 './alsactl.1' '/usr/share/man/man1/alsactl.1'
test -z "/usr/share/man/man7" || mkdir -p -- "/usr/share/man/man7"
 /usr/bin/install -c -m 644 './alsactl_init.7' '/usr/share/man/man7/alsactl_init.7'
make[3]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/alsactl »
make[2]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/alsactl »
make[1]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/alsactl »
Making install in utils
make[1]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/utils »
make[2]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/utils »
make[2]: Rien à faire pour « install-exec-am ».
make[2]: Rien à faire pour « install-data-am ».
make[2]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/utils »
make[1]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/utils »
Making install in m4
make[1]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/m4 »
make[2]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/m4 »
make[2]: Rien à faire pour « install-exec-am ».
make[2]: Rien à faire pour « install-data-am ».
make[2]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/m4 »
make[1]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/m4 »
Making install in po
make[1]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/po »
mkdir -p -- /usr/share
installing ja.gmo as /usr/share/locale/ja/LC_MESSAGES/alsa-utils.mo
if test "alsa-utils" = "gettext-tools"; then \
      mkdir -p -- /usr/share/gettext/po; \
      for file in Makefile.in.in remove-potcdate.sin quot.sed boldquot.sed [email]en@quot.header[/email] [email]en@boldquot.header[/email] insert-header.sin Rules-quot   Makevars.template; do \
        /usr/bin/install -c -m 644 ./$file \
                /usr/share/gettext/po/$file; \
      done; \
      for file in Makevars; do \
        rm -f /usr/share/gettext/po/$file; \
      done; \
    else \
      : ; \
    fi
make[1]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/po »
Making install in alsamixer
make[1]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/alsamixer »
make[2]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/alsamixer »
test -z "/usr/bin" || mkdir -p -- "/usr/bin"
  /usr/bin/install -c 'alsamixer' '/usr/bin/alsamixer'
test -z "/usr/share/man/man1" || mkdir -p -- "/usr/share/man/man1"
 /usr/bin/install -c -m 644 './alsamixer.1' '/usr/share/man/man1/alsamixer.1'
make[2]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/alsamixer »
make[1]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/alsamixer »
Making install in amixer
make[1]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/amixer »
make[2]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/amixer »
test -z "/usr/bin" || mkdir -p -- "/usr/bin"
  /usr/bin/install -c 'amixer' '/usr/bin/amixer'
test -z "/usr/share/man/man1" || mkdir -p -- "/usr/share/man/man1"
 /usr/bin/install -c -m 644 './amixer.1' '/usr/share/man/man1/amixer.1'
make[2]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/amixer »
make[1]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/amixer »
Making install in amidi
make[1]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/amidi »
make[2]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/amidi »
test -z "/usr/bin" || mkdir -p -- "/usr/bin"
  /usr/bin/install -c 'amidi' '/usr/bin/amidi'
test -z "/usr/share/man/man1" || mkdir -p -- "/usr/share/man/man1"
 /usr/bin/install -c -m 644 './amidi.1' '/usr/share/man/man1/amidi.1'
make[2]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/amidi »
make[1]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/amidi »
Making install in alsaconf
make[1]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/alsaconf »
Making install in po
make[2]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/alsaconf/po »
mkdir -p -- /usr/share
make[2]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/alsaconf/po »
make[2]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/alsaconf »
make[3]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/alsaconf »
test -z "/usr/sbin" || mkdir -p -- "/usr/sbin"
 /usr/bin/install -c 'alsaconf' '/usr/sbin/alsaconf'
 /usr/bin/install -c -m 644 alsaconf.8 /usr/share/man/man8/alsaconf.8
 /usr/bin/install -c -m 644 alsaconf.fr.8 /usr/share/man/fr/man8/alsaconf.8
make[3]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/alsaconf »
make[2]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/alsaconf »
make[1]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/alsaconf »
Making install in aplay
make[1]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/aplay »
make[2]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/aplay »
test -z "/usr/bin" || mkdir -p -- "/usr/bin"
  /usr/bin/install -c 'aplay' '/usr/bin/aplay'
make  install-exec-hook
make[3]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/aplay »
rm -f arecord
ln -s aplay arecord
rm -f /usr/bin/arecord
(cd /usr/bin && ln -s aplay arecord)
make[3]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/aplay »
test -z "/usr/share/man/man1" || mkdir -p -- "/usr/share/man/man1"
 /usr/bin/install -c -m 644 './aplay.1' '/usr/share/man/man1/aplay.1'
 /usr/bin/install -c -m 644 './arecord.1' '/usr/share/man/man1/arecord.1'
make  install-data-hook
make[3]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/aplay »
rm -f /usr/share/man/man1/arecord.1
(cd /usr/share/man/man1 && ln -s aplay.1 arecord.1)
make[3]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/aplay »
make[2]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/aplay »
make[1]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/aplay »
Making install in iecset
make[1]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/iecset »
make[2]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/iecset »
test -z "/usr/bin" || mkdir -p -- "/usr/bin"
  /usr/bin/install -c 'iecset' '/usr/bin/iecset'
test -z "/usr/share/man/man1" || mkdir -p -- "/usr/share/man/man1"
 /usr/bin/install -c -m 644 './iecset.1' '/usr/share/man/man1/iecset.1'
make[2]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/iecset »
make[1]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/iecset »
Making install in speaker-test
make[1]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/speaker-test »
Making install in samples
make[2]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/speaker-test/samples »
make[3]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/speaker-test/samples »
make[3]: Rien à faire pour « install-exec-am ».
test -z "/usr/share/alsa/speaker-test" || mkdir -p -- "/usr/share/alsa/speaker-test"
 /usr/bin/install -c -m 644 'sample_map.csv' '/usr/share/alsa/speaker-test/sample_map.csv'
test -z "/usr/share/sounds/alsa" || mkdir -p -- "/usr/share/sounds/alsa"
 /usr/bin/install -c -m 644 'Front_Left.wav' '/usr/share/sounds/alsa/Front_Left.wav'
 /usr/bin/install -c -m 644 'Rear_Center.wav' '/usr/share/sounds/alsa/Rear_Center.wav'
 /usr/bin/install -c -m 644 'Rear_Right.wav' '/usr/share/sounds/alsa/Rear_Right.wav'
 /usr/bin/install -c -m 644 'Side_Right.wav' '/usr/share/sounds/alsa/Side_Right.wav'
 /usr/bin/install -c -m 644 'Front_Center.wav' '/usr/share/sounds/alsa/Front_Center.wav'
 /usr/bin/install -c -m 644 'Front_Right.wav' '/usr/share/sounds/alsa/Front_Right.wav'
 /usr/bin/install -c -m 644 'Noise.wav' '/usr/share/sounds/alsa/Noise.wav'
 /usr/bin/install -c -m 644 'Rear_Left.wav' '/usr/share/sounds/alsa/Rear_Left.wav'
 /usr/bin/install -c -m 644 'Side_Left.wav' '/usr/share/sounds/alsa/Side_Left.wav'
make[3]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/speaker-test/samples »
make[2]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/speaker-test/samples »
make[2]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/speaker-test »
make[3]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/speaker-test »
test -z "/usr/bin" || mkdir -p -- "/usr/bin"
  /usr/bin/install -c 'speaker-test' '/usr/bin/speaker-test'
test -z "/usr/share/man/man1" || mkdir -p -- "/usr/share/man/man1"
 /usr/bin/install -c -m 644 './speaker-test.1' '/usr/share/man/man1/speaker-test.1'
make[3]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/speaker-test »
make[2]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/speaker-test »
make[1]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/speaker-test »
Making install in seq
make[1]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/seq »
Making install in aconnect
make[2]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/seq/aconnect »
make[3]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/seq/aconnect »
test -z "/usr/bin" || mkdir -p -- "/usr/bin"
  /usr/bin/install -c 'aconnect' '/usr/bin/aconnect'
test -z "/usr/share/man/man1" || mkdir -p -- "/usr/share/man/man1"
 /usr/bin/install -c -m 644 './aconnect.1' '/usr/share/man/man1/aconnect.1'
make[3]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/seq/aconnect »
make[2]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/seq/aconnect »
Making install in aplaymidi
make[2]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/seq/aplaymidi »
make[3]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/seq/aplaymidi »
test -z "/usr/bin" || mkdir -p -- "/usr/bin"
  /usr/bin/install -c 'aplaymidi' '/usr/bin/aplaymidi'
  /usr/bin/install -c 'arecordmidi' '/usr/bin/arecordmidi'
test -z "/usr/share/man/man1" || mkdir -p -- "/usr/share/man/man1"
 /usr/bin/install -c -m 644 './aplaymidi.1' '/usr/share/man/man1/aplaymidi.1'
 /usr/bin/install -c -m 644 './arecordmidi.1' '/usr/share/man/man1/arecordmidi.1'
make[3]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/seq/aplaymidi »
make[2]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/seq/aplaymidi »
Making install in aseqdump
make[2]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/seq/aseqdump »
make[3]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/seq/aseqdump »
test -z "/usr/bin" || mkdir -p -- "/usr/bin"
  /usr/bin/install -c 'aseqdump' '/usr/bin/aseqdump'
test -z "/usr/share/man/man1" || mkdir -p -- "/usr/share/man/man1"
 /usr/bin/install -c -m 644 './aseqdump.1' '/usr/share/man/man1/aseqdump.1'
make[3]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/seq/aseqdump »
make[2]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/seq/aseqdump »
Making install in aseqnet
make[2]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/seq/aseqnet »
make[3]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/seq/aseqnet »
test -z "/usr/bin" || mkdir -p -- "/usr/bin"
  /usr/bin/install -c 'aseqnet' '/usr/bin/aseqnet'
test -z "/usr/share/man/man1" || mkdir -p -- "/usr/share/man/man1"
 /usr/bin/install -c -m 644 './aseqnet.1' '/usr/share/man/man1/aseqnet.1'
make[3]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/seq/aseqnet »
make[2]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/seq/aseqnet »
make[2]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/seq »
make[3]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/seq »
make[3]: Rien à faire pour « install-exec-am ».
make[3]: Rien à faire pour « install-data-am ».
make[3]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/seq »
make[2]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/seq »
make[1]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/seq »
make[1]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20 »
make[2]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20 »
make[2]: Rien à faire pour « install-exec-am ».
make[2]: Rien à faire pour « install-data-am ».
make[2]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20 »
make[1]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20 »
rabgye@ubuntumaya:~/alsa-utils-1.0.20$ rm -f ~/alsa-driver*
rm: ne peut enlever `/home/rabgye/alsa-driver-1.0.20': est un dossier
rabgye@ubuntumaya:~/alsa-utils-1.0.20$ rm -f ~/alsa-lib*
rm: ne peut enlever `/home/rabgye/alsa-lib-1.0.20': est un dossier
rabgye@ubuntumaya:~/alsa-utils-1.0.20$ rm -f ~/alsa-utils*
rm: ne peut enlever `/home/rabgye/alsa-utils-1.0.20': est un dossier
rabgye@ubuntumaya:~/alsa-utils-1.0.20$ 


































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































make[1]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/amixer »
if gcc -DHAVE_CONFIG_H -I. -I. -I../include -I../include    -g -O2 -MT amixer.o -MD -MP -MF ".deps/amixer.Tpo" -c -o amixer.o amixer.c; \
    then mv -f ".deps/amixer.Tpo" ".deps/amixer.Po"; else rm -f ".deps/amixer.Tpo"; exit 1; fi
amixer.c: In function ‘get_integer’:
amixer.c:244: attention : ignoring return value of ‘strtol’, declared with attribute warn_unused_result
amixer.c: In function ‘get_integer64’:
amixer.c:272: attention : ignoring return value of ‘strtol’, declared with attribute warn_unused_result
amixer.c: In function ‘set_volume_simple’:
amixer.c:358: attention : ignoring return value of ‘strtol’, declared with attribute warn_unused_result
gcc  -g -O2   -o amixer  amixer.o -lm -lasound -lm -ldl -lpthread
make[1]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/amixer »
Making all in amidi
make[1]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/amidi »
if gcc -DHAVE_CONFIG_H -I. -I. -I../include -I../include    -g -O2 -MT amidi.o -MD -MP -MF ".deps/amidi.Tpo" -c -o amidi.o amidi.c; \
    then mv -f ".deps/amidi.Tpo" ".deps/amidi.Po"; else rm -f ".deps/amidi.Tpo"; exit 1; fi
amidi.c: In function ‘main’:
amidi.c:658: attention : ignoring return value of ‘write’, declared with attribute warn_unused_result
gcc  -g -O2   -o amidi  amidi.o  -lasound -lm -ldl -lpthread
make[1]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/amidi »
Making all in alsaconf
make[1]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/alsaconf »
Making all in po
make[2]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/alsaconf/po »
35 messages traduits, 1 message non traduit.
34 messages traduits, 1 traduction approximative, 1 message non traduit.
make[2]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/alsaconf/po »
make[2]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/alsaconf »
make[2]: Rien à faire pour « all-am ».
make[2]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/alsaconf »
make[1]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/alsaconf »
Making all in aplay
make[1]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/aplay »
if gcc -DHAVE_CONFIG_H -I. -I. -I../include -I../include    -g -O2 -MT aplay.o -MD -MP -MF ".deps/aplay.Tpo" -c -o aplay.o aplay.c; \
    then mv -f ".deps/aplay.Tpo" ".deps/aplay.Po"; else rm -f ".deps/aplay.Tpo"; exit 1; fi
aplay.c: In function ‘end_voc’:
aplay.c:2158: attention : ignoring return value of ‘write’, declared with attribute warn_unused_result
aplay.c: In function ‘end_wave’:
aplay.c:2178: attention : ignoring return value of ‘write’, declared with attribute warn_unused_result
aplay.c:2180: attention : ignoring return value of ‘write’, declared with attribute warn_unused_result
aplay.c: In function ‘end_au’:
aplay.c:2193: attention : ignoring return value of ‘write’, declared with attribute warn_unused_result
gcc  -g -O2   -o aplay  aplay.o  -lrt -lasound -lm -ldl -lpthread
make[1]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/aplay »
Making all in iecset
make[1]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/iecset »
if gcc -DHAVE_CONFIG_H -I. -I. -I../include -I../include    -g -O2 -MT iecset.o -MD -MP -MF ".deps/iecset.Tpo" -c -o iecset.o iecset.c; \
    then mv -f ".deps/iecset.Tpo" ".deps/iecset.Po"; else rm -f ".deps/iecset.Tpo"; exit 1; fi
if gcc -DHAVE_CONFIG_H -I. -I. -I../include -I../include    -g -O2 -MT iecbits.o -MD -MP -MF ".deps/iecbits.Tpo" -c -o iecbits.o iecbits.c; \
    then mv -f ".deps/iecbits.Tpo" ".deps/iecbits.Po"; else rm -f ".deps/iecbits.Tpo"; exit 1; fi
gcc  -g -O2   -o iecset  iecset.o iecbits.o -lm -lasound -lm -ldl -lpthread
make[1]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/iecset »
Making all in speaker-test
make[1]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/speaker-test »
Making all in samples
make[2]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/speaker-test/samples »
make[2]: Rien à faire pour « all ».
make[2]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/speaker-test/samples »
make[2]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/speaker-test »
if gcc -DHAVE_CONFIG_H -I. -I. -I../include -I../include    -g -O2 -MT speaker-test.o -MD -MP -MF ".deps/speaker-test.Tpo" -c -o speaker-test.o speaker-test.c; \
    then mv -f ".deps/speaker-test.Tpo" ".deps/speaker-test.Po"; else rm -f ".deps/speaker-test.Tpo"; exit 1; fi
if gcc -DHAVE_CONFIG_H -I. -I. -I../include -I../include    -g -O2 -MT pink.o -MD -MP -MF ".deps/pink.Tpo" -c -o pink.o pink.c; \
    then mv -f ".deps/pink.Tpo" ".deps/pink.Po"; else rm -f ".deps/pink.Tpo"; exit 1; fi
gcc  -g -O2   -o speaker-test  speaker-test.o pink.o  -lm -lasound -lm -ldl -lpthread
make[2]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/speaker-test »
make[1]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/speaker-test »
Making all in seq
make[1]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/seq »
Making all in aconnect
make[2]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/seq/aconnect »
if gcc -DHAVE_CONFIG_H -I. -I. -I../../include -I../../include    -g -O2 -MT aconnect.o -MD -MP -MF ".deps/aconnect.Tpo" -c -o aconnect.o aconnect.c; \
    then mv -f ".deps/aconnect.Tpo" ".deps/aconnect.Po"; else rm -f ".deps/aconnect.Tpo"; exit 1; fi
gcc  -g -O2   -o aconnect  aconnect.o  -lasound -lm -ldl -lpthread
make[2]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/seq/aconnect »
Making all in aplaymidi
make[2]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/seq/aplaymidi »
if gcc -DHAVE_CONFIG_H -I. -I. -I../../include -I../../include    -g -O2 -MT aplaymidi.o -MD -MP -MF ".deps/aplaymidi.Tpo" -c -o aplaymidi.o aplaymidi.c; \
    then mv -f ".deps/aplaymidi.Tpo" ".deps/aplaymidi.Po"; else rm -f ".deps/aplaymidi.Tpo"; exit 1; fi
gcc  -g -O2   -o aplaymidi  aplaymidi.o  -lasound -lm -ldl -lpthread
if gcc -DHAVE_CONFIG_H -I. -I. -I../../include -I../../include    -g -O2 -MT arecordmidi.o -MD -MP -MF ".deps/arecordmidi.Tpo" -c -o arecordmidi.o arecordmidi.c; \
    then mv -f ".deps/arecordmidi.Tpo" ".deps/arecordmidi.Po"; else rm -f ".deps/arecordmidi.Tpo"; exit 1; fi
gcc  -g -O2   -o arecordmidi  arecordmidi.o  -lasound -lm -ldl -lpthread
make[2]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/seq/aplaymidi »
Making all in aseqdump
make[2]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/seq/aseqdump »
if gcc -DHAVE_CONFIG_H -I. -I. -I../../include -I../../include    -g -O2 -MT aseqdump.o -MD -MP -MF ".deps/aseqdump.Tpo" -c -o aseqdump.o aseqdump.c; \
    then mv -f ".deps/aseqdump.Tpo" ".deps/aseqdump.Po"; else rm -f ".deps/aseqdump.Tpo"; exit 1; fi
gcc  -g -O2   -o aseqdump  aseqdump.o  -lasound -lm -ldl -lpthread
make[2]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/seq/aseqdump »
Making all in aseqnet
make[2]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/seq/aseqnet »
if gcc -DHAVE_CONFIG_H -I. -I. -I../../include -I../../include    -g -O2 -MT aseqnet.o -MD -MP -MF ".deps/aseqnet.Tpo" -c -o aseqnet.o aseqnet.c; \
    then mv -f ".deps/aseqnet.Tpo" ".deps/aseqnet.Po"; else rm -f ".deps/aseqnet.Tpo"; exit 1; fi
aseqnet.c: In function ‘flush_writebuf’:
aseqnet.c:495: attention : ignoring return value of ‘write’, declared with attribute warn_unused_result
gcc  -g -O2   -o aseqnet  aseqnet.o  -lasound -lm -ldl -lpthread
make[2]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/seq/aseqnet »
make[2]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/seq »
make[2]: Rien à faire pour « all-am ».
make[2]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/seq »
make[1]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/seq »
make[1]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20 »
make[1]: Rien à faire pour « all-am ».
make[1]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20 »
rabgye@ubuntumaya:~/alsa-utils-1.0.20$ sudo make
Making all in include
make[1]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/include »
make  all-am
make[2]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/include »
make[2]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/include »
make[1]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/include »
Making all in alsactl
make[1]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/alsactl »
Making all in init
make[2]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/alsactl/init »
make[2]: Rien à faire pour « all ».
make[2]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/alsactl/init »
make[2]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/alsactl »
make[2]: Rien à faire pour « all-am ».
make[2]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/alsactl »
make[1]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/alsactl »
Making all in utils
make[1]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/utils »
make[1]: Rien à faire pour « all ».
make[1]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/utils »
Making all in m4
make[1]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/m4 »
make[1]: Rien à faire pour « all ».
make[1]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/m4 »
Making all in po
make[1]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/po »
make[1]: Rien à faire pour « all ».
make[1]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/po »
Making all in alsamixer
make[1]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/alsamixer »
make[1]: Rien à faire pour « all ».
make[1]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/alsamixer »
Making all in amixer
make[1]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/amixer »
make[1]: Rien à faire pour « all ».
make[1]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/amixer »
Making all in amidi
make[1]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/amidi »
make[1]: Rien à faire pour « all ».
make[1]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/amidi »
Making all in alsaconf
make[1]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/alsaconf »
Making all in po
make[2]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/alsaconf/po »
make[2]: Rien à faire pour « all ».
make[2]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/alsaconf/po »
make[2]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/alsaconf »
make[2]: Rien à faire pour « all-am ».
make[2]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/alsaconf »
make[1]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/alsaconf »
Making all in aplay
make[1]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/aplay »
make[1]: Rien à faire pour « all ».
make[1]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/aplay »
Making all in iecset
make[1]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/iecset »
make[1]: Rien à faire pour « all ».
make[1]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/iecset »
Making all in speaker-test
make[1]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/speaker-test »
Making all in samples
make[2]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/speaker-test/samples »
make[2]: Rien à faire pour « all ».
make[2]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/speaker-test/samples »
make[2]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/speaker-test »
make[2]: Rien à faire pour « all-am ».
make[2]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/speaker-test »
make[1]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/speaker-test »
Making all in seq
make[1]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/seq »
Making all in aconnect
make[2]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/seq/aconnect »
make[2]: Rien à faire pour « all ».
make[2]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/seq/aconnect »
Making all in aplaymidi
make[2]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/seq/aplaymidi »
make[2]: Rien à faire pour « all ».
make[2]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/seq/aplaymidi »
Making all in aseqdump
make[2]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/seq/aseqdump »
make[2]: Rien à faire pour « all ».
make[2]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/seq/aseqdump »
Making all in aseqnet
make[2]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/seq/aseqnet »
make[2]: Rien à faire pour « all ».
make[2]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/seq/aseqnet »
make[2]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/seq »
make[2]: Rien à faire pour « all-am ».
make[2]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/seq »
make[1]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/seq »
make[1]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20 »
make[1]: Rien à faire pour « all-am ».
make[1]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20 »
rabgye@ubuntumaya:~/alsa-utils-1.0.20$ sudo make install
Making install in include
make[1]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/include »
make[2]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/include »
make[2]: Rien à faire pour « install-exec-am ».
make[2]: Rien à faire pour « install-data-am ».
make[2]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/include »
make[1]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/include »
Making install in alsactl
make[1]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/alsactl »
Making install in init
make[2]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/alsactl/init »
make[3]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/alsactl/init »
make[3]: Rien à faire pour « install-exec-am ».
test -z "/usr/share/alsa/init" || mkdir -p -- "/usr/share/alsa/init"
 /usr/bin/install -c -m 644 '00main' '/usr/share/alsa/init/00main'
 /usr/bin/install -c -m 644 'default' '/usr/share/alsa/init/default'
 /usr/bin/install -c -m 644 'help' '/usr/share/alsa/init/help'
 /usr/bin/install -c -m 644 'info' '/usr/share/alsa/init/info'
 /usr/bin/install -c -m 644 'test' '/usr/share/alsa/init/test'
 /usr/bin/install -c -m 644 'hda' '/usr/share/alsa/init/hda'
make[3]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/alsactl/init »
make[2]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/alsactl/init »
make[2]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/alsactl »
make[3]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/alsactl »
test -z "/usr/sbin" || mkdir -p -- "/usr/sbin"
  /usr/bin/install -c 'alsactl' '/usr/sbin/alsactl'
test -z "/usr/share/man/man1" || mkdir -p -- "/usr/share/man/man1"
 /usr/bin/install -c -m 644 './alsactl.1' '/usr/share/man/man1/alsactl.1'
test -z "/usr/share/man/man7" || mkdir -p -- "/usr/share/man/man7"
 /usr/bin/install -c -m 644 './alsactl_init.7' '/usr/share/man/man7/alsactl_init.7'
make[3]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/alsactl »
make[2]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/alsactl »
make[1]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/alsactl »
Making install in utils
make[1]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/utils »
make[2]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/utils »
make[2]: Rien à faire pour « install-exec-am ».
make[2]: Rien à faire pour « install-data-am ».
make[2]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/utils »
make[1]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/utils »
Making install in m4
make[1]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/m4 »
make[2]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/m4 »
make[2]: Rien à faire pour « install-exec-am ».
make[2]: Rien à faire pour « install-data-am ».
make[2]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/m4 »
make[1]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/m4 »
Making install in po
make[1]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/po »
mkdir -p -- /usr/share
installing ja.gmo as /usr/share/locale/ja/LC_MESSAGES/alsa-utils.mo
if test "alsa-utils" = "gettext-tools"; then \
      mkdir -p -- /usr/share/gettext/po; \
      for file in Makefile.in.in remove-potcdate.sin quot.sed boldquot.sed [email]en@quot.header[/email] [email]en@boldquot.header[/email] insert-header.sin Rules-quot   Makevars.template; do \
        /usr/bin/install -c -m 644 ./$file \
                /usr/share/gettext/po/$file; \
      done; \
      for file in Makevars; do \
        rm -f /usr/share/gettext/po/$file; \
      done; \
    else \
      : ; \
    fi
make[1]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/po »
Making install in alsamixer
make[1]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/alsamixer »
make[2]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/alsamixer »
test -z "/usr/bin" || mkdir -p -- "/usr/bin"
  /usr/bin/install -c 'alsamixer' '/usr/bin/alsamixer'
test -z "/usr/share/man/man1" || mkdir -p -- "/usr/share/man/man1"
 /usr/bin/install -c -m 644 './alsamixer.1' '/usr/share/man/man1/alsamixer.1'
make[2]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/alsamixer »
make[1]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/alsamixer »
Making install in amixer
make[1]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/amixer »
make[2]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/amixer »
test -z "/usr/bin" || mkdir -p -- "/usr/bin"
  /usr/bin/install -c 'amixer' '/usr/bin/amixer'
test -z "/usr/share/man/man1" || mkdir -p -- "/usr/share/man/man1"
 /usr/bin/install -c -m 644 './amixer.1' '/usr/share/man/man1/amixer.1'
make[2]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/amixer »
make[1]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/amixer »
Making install in amidi
make[1]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/amidi »
make[2]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/amidi »
test -z "/usr/bin" || mkdir -p -- "/usr/bin"
  /usr/bin/install -c 'amidi' '/usr/bin/amidi'
test -z "/usr/share/man/man1" || mkdir -p -- "/usr/share/man/man1"
 /usr/bin/install -c -m 644 './amidi.1' '/usr/share/man/man1/amidi.1'
make[2]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/amidi »
make[1]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/amidi »
Making install in alsaconf
make[1]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/alsaconf »
Making install in po
make[2]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/alsaconf/po »
mkdir -p -- /usr/share
make[2]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/alsaconf/po »
make[2]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/alsaconf »
make[3]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/alsaconf »
test -z "/usr/sbin" || mkdir -p -- "/usr/sbin"
 /usr/bin/install -c 'alsaconf' '/usr/sbin/alsaconf'
 /usr/bin/install -c -m 644 alsaconf.8 /usr/share/man/man8/alsaconf.8
 /usr/bin/install -c -m 644 alsaconf.fr.8 /usr/share/man/fr/man8/alsaconf.8
make[3]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/alsaconf »
make[2]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/alsaconf »
make[1]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/alsaconf »
Making install in aplay
make[1]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/aplay »
make[2]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/aplay »
test -z "/usr/bin" || mkdir -p -- "/usr/bin"
  /usr/bin/install -c 'aplay' '/usr/bin/aplay'
make  install-exec-hook
make[3]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/aplay »
rm -f arecord
ln -s aplay arecord
rm -f /usr/bin/arecord
(cd /usr/bin && ln -s aplay arecord)
make[3]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/aplay »
test -z "/usr/share/man/man1" || mkdir -p -- "/usr/share/man/man1"
 /usr/bin/install -c -m 644 './aplay.1' '/usr/share/man/man1/aplay.1'
 /usr/bin/install -c -m 644 './arecord.1' '/usr/share/man/man1/arecord.1'
make  install-data-hook
make[3]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/aplay »
rm -f /usr/share/man/man1/arecord.1
(cd /usr/share/man/man1 && ln -s aplay.1 arecord.1)
make[3]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/aplay »
make[2]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/aplay »
make[1]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/aplay »
Making install in iecset
make[1]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/iecset »
make[2]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/iecset »
test -z "/usr/bin" || mkdir -p -- "/usr/bin"
  /usr/bin/install -c 'iecset' '/usr/bin/iecset'
test -z "/usr/share/man/man1" || mkdir -p -- "/usr/share/man/man1"
 /usr/bin/install -c -m 644 './iecset.1' '/usr/share/man/man1/iecset.1'
make[2]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/iecset »
make[1]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/iecset »
Making install in speaker-test
make[1]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/speaker-test »
Making install in samples
make[2]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/speaker-test/samples »
make[3]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/speaker-test/samples »
make[3]: Rien à faire pour « install-exec-am ».
test -z "/usr/share/alsa/speaker-test" || mkdir -p -- "/usr/share/alsa/speaker-test"
 /usr/bin/install -c -m 644 'sample_map.csv' '/usr/share/alsa/speaker-test/sample_map.csv'
test -z "/usr/share/sounds/alsa" || mkdir -p -- "/usr/share/sounds/alsa"
 /usr/bin/install -c -m 644 'Front_Left.wav' '/usr/share/sounds/alsa/Front_Left.wav'
 /usr/bin/install -c -m 644 'Rear_Center.wav' '/usr/share/sounds/alsa/Rear_Center.wav'
 /usr/bin/install -c -m 644 'Rear_Right.wav' '/usr/share/sounds/alsa/Rear_Right.wav'
 /usr/bin/install -c -m 644 'Side_Right.wav' '/usr/share/sounds/alsa/Side_Right.wav'
 /usr/bin/install -c -m 644 'Front_Center.wav' '/usr/share/sounds/alsa/Front_Center.wav'
 /usr/bin/install -c -m 644 'Front_Right.wav' '/usr/share/sounds/alsa/Front_Right.wav'
 /usr/bin/install -c -m 644 'Noise.wav' '/usr/share/sounds/alsa/Noise.wav'
 /usr/bin/install -c -m 644 'Rear_Left.wav' '/usr/share/sounds/alsa/Rear_Left.wav'
 /usr/bin/install -c -m 644 'Side_Left.wav' '/usr/share/sounds/alsa/Side_Left.wav'
make[3]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/speaker-test/samples »
make[2]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/speaker-test/samples »
make[2]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/speaker-test »
make[3]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/speaker-test »
test -z "/usr/bin" || mkdir -p -- "/usr/bin"
  /usr/bin/install -c 'speaker-test' '/usr/bin/speaker-test'
test -z "/usr/share/man/man1" || mkdir -p -- "/usr/share/man/man1"
 /usr/bin/install -c -m 644 './speaker-test.1' '/usr/share/man/man1/speaker-test.1'
make[3]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/speaker-test »
make[2]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/speaker-test »
make[1]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/speaker-test »
Making install in seq
make[1]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/seq »
Making install in aconnect
make[2]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/seq/aconnect »
make[3]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/seq/aconnect »
test -z "/usr/bin" || mkdir -p -- "/usr/bin"
  /usr/bin/install -c 'aconnect' '/usr/bin/aconnect'
test -z "/usr/share/man/man1" || mkdir -p -- "/usr/share/man/man1"
 /usr/bin/install -c -m 644 './aconnect.1' '/usr/share/man/man1/aconnect.1'
make[3]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/seq/aconnect »
make[2]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/seq/aconnect »
Making install in aplaymidi
make[2]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/seq/aplaymidi »
make[3]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/seq/aplaymidi »
test -z "/usr/bin" || mkdir -p -- "/usr/bin"
  /usr/bin/install -c 'aplaymidi' '/usr/bin/aplaymidi'
  /usr/bin/install -c 'arecordmidi' '/usr/bin/arecordmidi'
test -z "/usr/share/man/man1" || mkdir -p -- "/usr/share/man/man1"
 /usr/bin/install -c -m 644 './aplaymidi.1' '/usr/share/man/man1/aplaymidi.1'
 /usr/bin/install -c -m 644 './arecordmidi.1' '/usr/share/man/man1/arecordmidi.1'
make[3]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/seq/aplaymidi »
make[2]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/seq/aplaymidi »
Making install in aseqdump
make[2]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/seq/aseqdump »
make[3]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/seq/aseqdump »
test -z "/usr/bin" || mkdir -p -- "/usr/bin"
  /usr/bin/install -c 'aseqdump' '/usr/bin/aseqdump'
test -z "/usr/share/man/man1" || mkdir -p -- "/usr/share/man/man1"
 /usr/bin/install -c -m 644 './aseqdump.1' '/usr/share/man/man1/aseqdump.1'
make[3]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/seq/aseqdump »
make[2]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/seq/aseqdump »
Making install in aseqnet
make[2]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/seq/aseqnet »
make[3]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/seq/aseqnet »
test -z "/usr/bin" || mkdir -p -- "/usr/bin"
  /usr/bin/install -c 'aseqnet' '/usr/bin/aseqnet'
test -z "/usr/share/man/man1" || mkdir -p -- "/usr/share/man/man1"
 /usr/bin/install -c -m 644 './aseqnet.1' '/usr/share/man/man1/aseqnet.1'
make[3]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/seq/aseqnet »
make[2]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/seq/aseqnet »
make[2]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/seq »
make[3]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20/seq »
make[3]: Rien à faire pour « install-exec-am ».
make[3]: Rien à faire pour « install-data-am ».
make[3]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/seq »
make[2]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/seq »
make[1]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20/seq »
make[1]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20 »
make[2]: entrant dans le répertoire « /home/rabgye/alsa-utils-1.0.20 »
make[2]: Rien à faire pour « install-exec-am ».
make[2]: Rien à faire pour « install-data-am ».
make[2]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20 »
make[1]: quittant le répertoire « /home/rabgye/alsa-utils-1.0.20 »
rabgye@ubuntumaya:~/alsa-utils-1.0.20$ rm -f ~/alsa-driver*
rm: ne peut enlever `/home/rabgye/alsa-driver-1.0.20': est un dossier
rabgye@ubuntumaya:~/alsa-utils-1.0.20$ rm -f ~/alsa-lib*
rm: ne peut enlever `/home/rabgye/alsa-lib-1.0.20': est un dossier
rabgye@ubuntumaya:~/alsa-utils-1.0.20$ rm -f ~/alsa-utils*
rm: ne peut enlever `/home/rabgye/alsa-utils-1.0.20': est un dossier
rabgye@ubuntumaya:~/alsa-utils-1.0.20$
tout semble avoir marche sauf les trois derniers lignes.j'espere que les vacances ont ete bonnes merci

---

### Post by manjusri on 2009-06-25
toujours pas de son de generique;toujours pas de son au test de capture du son.la commande `cat /proc/asound/versionco,firme la bonne installation de alsa-1.0.20.il faudra sans doute installer le driver de la carte realtek alc662

---

### Post by pytheas22 on 2009-06-25
En faite les trois dernières commandes ne sont pas essentielles--elles sont juste pour "nettoyer" les fichiers non-essentiels du procès d'installation qui restent sur votre ordinateur.  Vous pouvez les ressayer avec:
```

rm -rf ~/alsa-driver*
rm -rf ~/alsa-lib*
rm -rf ~/alsa-utils*
```

et ça devrait marcher, mais ce n'est pas obligatoire pour le bon functionnement de ALSA.

Alors merci de redémarrer votre ordinateur quand vous avez le temps, et me faire savoir si le son marche mieux.

---

### Post by manjusri on 2009-06-26
le son ne marche pas mieux;toujours pas de generique de start-up et resultats toujours negatifs aux tests de capture du son;le copier-coller a fonctionne d'une drole de maliere lors de ma derniere reponse.il me semble avoir lu que alsa-driver etait installe "mute" par default;je n'ai rien fait pour corriger ce probleme mais tous les autres tests de son marchentet aucun probleme a ecouter un cd audio ou video.reste-t-il yne autre solution que d'installer le driver de la carte realtek alc662?merci de ta reponse qui a ete rapide.

---

### Post by manjusri on 2009-06-26
bonjour pytheas;as tu reussi a determiner quel type de controleur utilise ma carte son?il me semble qu'apres l'installation du driver de la carte-son ne semble pas(plus)trop compliquee.merci amicalement manjusri

---

### Post by pytheas22 on 2009-06-27
Désolé que le son ne marche toujours pas comme désiré...

Il semble que votre carte est du type "Azalia," selon l'output de la commande 'lspci -nn'.  J'ai fait quelques cherches sur Internet pour cette carte et Ubuntu, et j'ai trouvé [cette page]("http://ubuntuforums.org/showthread.php?t=181186").  On dit là que la solution a été de faire les commandes suivantes:
```

echo snd-hda-intel | sudo tee -a /etc/modprobe.d/blacklist.conf
wget ftp://ftp.alsa-project.org/pub/driver/alsa-driver-1.0.20.tar.bz2
tar -xvf alsa-driver-1.0.14.tar.bz2
cd alsa-driver-1.0.14
./configure --with-cards=all --with-card-options=all
sudo make
sudo make install
```

Ce sont un peu les mêmes commandes que vous avez déjà essayées, mais avec quelques précisions qui pourraient être importantes.

Comme toujours, merci de d'afficher dans le forum les outputs des commandes.

---

### Post by manjusri on 2009-06-28
ce n'est toujours pas la bonne solution
;j'ai essaye desuivre pas a pas la procedure d'installation;ça confirme que la carte son est de type azalia;je n'arrive pas a ouvrir ou executer alsamixer pour rendre le son "unmute".je ne t'envoie pas les outputs car il y a eu un bug lors de l'enregistrementmais tout semble avoir fonctionne normalement.la seule chose qui reste afaire dans l'installation pas apas est d'executer alsamixer;peux tu m'indiquer comment faire? merci

---

### Post by manjusri on 2009-06-28
voici ce que j'obtiens en tapant "alsamixer" dans le terminal:
























&#9484;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;[AlsaMixer v1.0.20 (Press Escape to quit)]&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9488;
&#9474; Card: HDA SIS966                                                             &#9474;
&#9474; Chip: Realtek ALC662 rev1                                                    &#9474;
&#9474; View: [Playback] Capture  All                                                &#9474;
&#9474; Item: Master [dB gain=-11.00]                                                &#9474;
&#9474;                                                                              &#9474;
&#9474;    &#9484;&#9472;&#9472;&#9488;               &#9484;&#9472;&#9472;&#9488;     &#9484;&#9472;&#9472;&#9488;     &#9484;&#9472;&#9472;&#9488;      &#9484;&#9472;&#9472;&#9488;     &#9484;&#9472;&#9472;&#9488;     &#9484;&#9472;&#9472;&#9488;     &#9474;
&#9474;    &#9474;  &#9474;               &#9474;&#9618;&#9618;&#9474;     &#9474;  &#9474;     &#9474;  &#9474;      &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;
&#9474;    &#9474;&#9618;&#9618;&#9474;               &#9474;&#9618;&#9618;&#9474;     &#9474;  &#9474;     &#9474;  &#9474;      &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;
&#9474;    &#9474;&#9618;&#9618;&#9474;               &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;  &#9474;      &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;     >
&#9474;    &#9474;&#9618;&#9618;&#9474;               &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;  &#9474;      &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;     >
&#9474;    &#9474;&#9618;&#9618;&#9474;               &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;  &#9474;      &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;     >
&#9474;    &#9474;&#9618;&#9618;&#9474;               &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;  &#9474;      &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;     >
&#9474;    &#9474;&#9618;&#9618;&#9474;               &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;  &#9474;      &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;     >
&#9474;    &#9474;&#9618;&#9618;&#9474;               &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;  &#9474;      &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;     >
&#9474;    &#9474;&#9618;&#9618;&#9474;               &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;  &#9474;      &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;
&#9474;    &#9474;&#9618;&#9618;&#9474;               &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;  &#9474;      &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;
&#9474;    &#9474;&#9618;&#9618;&#9474;               &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;  &#9474;      &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;
&#9474;    &#9500;&#9472;&#9472;&#9508;     &#9484;&#9472;&#9472;&#9488;      &#9492;&#9472;&#9472;&#9496;     &#9500;&#9472;&#9472;&#9508;     &#9500;&#9472;&#9472;&#9508;      &#9500;&#9472;&#9472;&#9508;     &#9500;&#9472;&#9472;&#9508;     &#9500;&#9472;&#9472;&#9508;     &#9474;
&#9474;    &#9474;OO&#9474;     &#9474;OO&#9474;               &#9474;OO&#9474;     &#9474;MM&#9474;      &#9474;OO&#9474;     &#9474;OO&#9474;     &#9474;OO&#9474;     &#9474;
&#9474;    &#9492;&#9472;&#9472;&#9496;     &#9492;&#9472;&#9472;&#9496;               &#9492;&#9472;&#9472;&#9496;     &#9492;&#9472;&#9472;&#9496;      &#9492;&#9472;&#9472;&#9496;     &#9492;&#9472;&#9472;&#9496;     &#9492;&#9472;&#9472;&#9496;     &#9474;
&#9474;     83              100<>100  81<>81    0<>0    100<>100    100      100     &#9474;
&#9474; < Master >Headphon    PCM     Front   Front Mi  Surround  Center    LFE      &#9474;
&#9492;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9496;

mais je vois pas quoi en faire!

---

### Post by manjusri on 2009-06-28
ton dernier message contenait un quiproquo;j'ai essaye la preliere fois avec alsa-driver-1.0.20;l'installation areussie mais sans changements en ce qui concerne la capture du son .en essayant de compiler alsa-driver-1.0.14 j'obtiens une errreur;voici l'output:











































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































checking for kernel media/v4l2-dev.h... yes
checking for kernel linux/devfs_fs_kernel.h... no
Creating a dummy <linux/devfs_fs_kernel.h>...
checking for kernel linux/highmem.h... yes
checking for kernel linux/workqueue.h... yes
checking for kernel linux/dma-mapping.h... yes
checking for kernel asm/hw_irq.h... no
Creating a dummy <asm/hw_irq.h>...
checking for kernel linux/device.h... yes
checking for kernel linux/platform_device.h... yes
checking for kernel linux/isa.h... yes
checking for kernel linux/jiffies.h... yes
checking for kernel linux/compat.h... yes
checking for kernel linux/log2.h... yes
checking for kernel linux/adb.h... yes
checking for kernel linux/cuda.h... yes
checking for kernel linux/pmu.h... yes
checking for kernel linux/moduleparam.h... yes
checking for kernel linux/syscalls.h... yes
checking for kernel linux/firmware.h... yes
checking for kernel linux/err.h... yes
checking for kernel linux/bitmap.h... yes
checking for kernel linux/mutex.h... yes
checking for kernel linux/latency.h... no
Creating <linux/latency.h>...
checking for kernel asm/irq_regs.h... no
Creating a dummy <asm/irq_regs.h>...
checking for kernel module symbol versions... yes
checking for PCI support in kernel... yes
checking for I2C driver in kernel... yes
checking for I2C_POWERMAC in kernel... unknown
checking for firmware loader... yes
checking for input subsystem in kernel... yes
checking for directory to store kernel modules... /lib/modules/2.6.28-3-rt/kernel/sound
checking for verbose procfs... on
checking for verbose printk... on
checking for debug level... none
checking for ISA support in kernel... no
checking for processor type... x86_64
checking for ISA DMA API... yes
checking for 32bit compat support... yes
checking for SMP... yes
checking for Video device support in kernel... yes
checking for ISA PnP driver in kernel... yes
checking for PnP driver in kernel... yes
checking for Kernel ISA-PnP support... no
checking for Kernel ISA-PnP module support... no
checking for strlcpy... no
checking for snprintf... no
checking for vsnprintf... no
checking for scnprintf... no
checking for sscanf... no
checking for vmalloc_to_page... no
checking for old kmod... yes
checking for PDE... no
checking for pci_set_consistent_dma_mask... no
checking for pci_dev_present... no
checking for msleep... no
checking for msecs_to_jiffies... no
checking for tty->count is the atomic type... no
checking for video_get_drvdata... no
checking for V4L1 layer... yes
checking for io_remap_pfn_range... no
checking for new io_remap_page_range... no
checking for kcalloc... no
checking for kstrdup... no
checking for kzalloc... no
checking for create_workqueue with flags... no
checking for saved_config_space in pci_dev... no
checking for register_sound_special_device... no
checking for driver version... 1.0.14
checking for sequencer support... yes
checking for OSS/Free emulation... yes
checking for OSS PCM plugin system inclusion... yes
checking for RTC callback support in kernel... no
checking for HPET support... yes
checking for dynamic minor numbers... no
checking for support of old API... yes
checking for Procfs support... yes
checking for USB support... yes
checking for class_simple... no
checking for old driver suspend/resume callbacks... no
checking for removal of page-reservation for nopage/mmap... no
checking for nested class_device... no
checking for new IRQ handler... no
checking for gfp_t... no
checking for PnP suspend/resume... no
checking for new unlocked/compat_ioctl... no
checking for PC-Speaker hook... no
checking for kernel PCMCIA
checking for PCMCIA support... yes
checking for PC9800 support in kernel... no
checking for parallel port support... yes
checking for power management... yes
checking for which soundcards to compile driver for... all
configure: creating ./config.status
config.status: creating version
config.status: creating Makefile.conf
config.status: WARNING:  Makefile.conf.in seems to ignore the --datarootdir setting
config.status: creating snddevices
config.status: creating utils/alsa-driver.spec
config.status: creating utils/buildrpm
config.status: creating toplevel.config
config.status: creating utils/alsasound
config.status: creating utils/alsasound.posix
config.status: creating include/pci_ids_compat.h
config.status: creating include/i2c-id_compat.h
config.status: creating include/config.h
config.status: include/config.h is unchanged
config.status: creating include/config1.h
config.status: include/config1.h is unchanged
config.status: creating include/version.h
config.status: include/version.h is unchanged
config.status: creating include/autoconf-extra.h
config.status: include/autoconf-extra.h is unchanged
Hacking autoconf.h...
rabgye@ubuntumaya:~/alsa-driver-1.0.14$ sudo make
if [ ! -d include/sound -a ! -L include/sound ]; then \
      ln -sf ../alsa-kernel/include include/sound ; \
    fi
cp -puvf include/version.h include/sound/version.h
`include/version.h' -> `include/sound/version.h'
make dep
make[1]: entrant dans le répertoire « /home/rabgye/alsa-driver-1.0.14 »
make[2]: entrant dans le répertoire « /home/rabgye/alsa-driver-1.0.14/acore »
copying file alsa-kernel/core/info.c
patching file info.c
Hunk #8 succeeded at 535 with fuzz 2.
copying file alsa-kernel/core/pcm.c
patching file pcm.c
copying file alsa-kernel/core/pcm_native.c
patching file pcm_native.c
copying file alsa-kernel/core/control.c
patching file control.c
copying file alsa-kernel/core/hwdep.c
patching file hwdep.c
copying file alsa-kernel/core/init.c
patching file init.c
Hunk #2 succeeded at 228 (offset 5 lines).
Hunk #3 succeeded at 254 with fuzz 2 (offset 5 lines).
copying file alsa-kernel/core/rawmidi.c
patching file rawmidi.c
copying file alsa-kernel/core/sound.c
patching file sound.c
copying file alsa-kernel/core/timer.c
patching file timer.c
copying file alsa-kernel/core/memalloc.c
patching file memalloc.c
Hunk #2 succeeded at 83 (offset -1 lines).
Hunk #3 succeeded at 143 (offset -1 lines).
Hunk #4 succeeded at 174 (offset -1 lines).
Hunk #5 succeeded at 207 (offset -1 lines).
Hunk #6 succeeded at 228 (offset -1 lines).
Hunk #7 succeeded at 264 (offset -1 lines).
Hunk #8 succeeded at 286 (offset -1 lines).
Hunk #9 succeeded at 311 (offset -1 lines).
Hunk #10 succeeded at 329 (offset -1 lines).
Hunk #11 succeeded at 604 (offset -5 lines).
Hunk #12 succeeded at 693 (offset -5 lines).
Hunk #13 succeeded at 708 (offset -5 lines).
Hunk #14 succeeded at 742 (offset -5 lines).
copying file alsa-kernel/core/misc.c
patching file misc.c
Hunk #2 succeeded at 30 (offset -1 lines).
Hunk #3 succeeded at 96 (offset -1 lines).
make[3]: entrant dans le répertoire « /home/rabgye/alsa-driver-1.0.14/acore/ioctl32 »
make[3]: quittant le répertoire « /home/rabgye/alsa-driver-1.0.14/acore/ioctl32 »
make[3]: entrant dans le répertoire « /home/rabgye/alsa-driver-1.0.14/acore/oss »
copying file alsa-kernel/core/oss/mixer_oss.c
patching file mixer_oss.c
copying file alsa-kernel/core/oss/pcm_oss.c
patching file pcm_oss.c
make[3]: quittant le répertoire « /home/rabgye/alsa-driver-1.0.14/acore/oss »
make[3]: entrant dans le répertoire « /home/rabgye/alsa-driver-1.0.14/acore/seq »
copying file alsa-kernel/core/seq/seq.c
patching file seq.c
Hunk #1 succeeded at 57 (offset 6 lines).
copying file alsa-kernel/core/seq/seq_clientmgr.c
patching file seq_clientmgr.c
copying file alsa-kernel/core/seq/seq_memory.c
patching file seq_memory.c
Hunk #3 succeeded at 248 (offset 3 lines).
make[4]: entrant dans le répertoire « /home/rabgye/alsa-driver-1.0.14/acore/seq/instr »
make[4]: quittant le répertoire « /home/rabgye/alsa-driver-1.0.14/acore/seq/instr »
make[4]: entrant dans le répertoire « /home/rabgye/alsa-driver-1.0.14/acore/seq/oss »
copying file alsa-kernel/core/seq/oss/seq_oss.c
patching file seq_oss.c
make[4]: quittant le répertoire « /home/rabgye/alsa-driver-1.0.14/acore/seq/oss »
make[3]: quittant le répertoire « /home/rabgye/alsa-driver-1.0.14/acore/seq »
make[2]: quittant le répertoire « /home/rabgye/alsa-driver-1.0.14/acore »
make[2]: entrant dans le répertoire « /home/rabgye/alsa-driver-1.0.14/i2c »
make[3]: entrant dans le répertoire « /home/rabgye/alsa-driver-1.0.14/i2c/other »
copying file alsa-kernel/i2c/other/tea575x-tuner.c
patching file tea575x-tuner.c
make[3]: quittant le répertoire « /home/rabgye/alsa-driver-1.0.14/i2c/other »
make[2]: quittant le répertoire « /home/rabgye/alsa-driver-1.0.14/i2c »
make[2]: entrant dans le répertoire « /home/rabgye/alsa-driver-1.0.14/drivers »
copying file alsa-kernel/drivers/mts64.c
patching file mts64.c
copying file alsa-kernel/drivers/portman2x4.c
patching file portman2x4.c
make[3]: entrant dans le répertoire « /home/rabgye/alsa-driver-1.0.14/drivers/mpu401 »
copying file alsa-kernel/drivers/mpu401/mpu401.c
patching file mpu401.c
make[3]: quittant le répertoire « /home/rabgye/alsa-driver-1.0.14/drivers/mpu401 »
make[3]: entrant dans le répertoire « /home/rabgye/alsa-driver-1.0.14/drivers/opl3 »
copying file alsa-kernel/drivers/opl3/opl3_lib.c
patching file opl3_lib.c
Hunk #1 succeeded at 435 (offset 2 lines).
make[3]: quittant le répertoire « /home/rabgye/alsa-driver-1.0.14/drivers/opl3 »
make[3]: entrant dans le répertoire « /home/rabgye/alsa-driver-1.0.14/drivers/opl4 »
make[3]: quittant le répertoire « /home/rabgye/alsa-driver-1.0.14/drivers/opl4 »
make[3]: entrant dans le répertoire « /home/rabgye/alsa-driver-1.0.14/drivers/pcsp »
make[3]: quittant le répertoire « /home/rabgye/alsa-driver-1.0.14/drivers/pcsp »
make[3]: entrant dans le répertoire « /home/rabgye/alsa-driver-1.0.14/drivers/vx »
make[3]: quittant le répertoire « /home/rabgye/alsa-driver-1.0.14/drivers/vx »
make[2]: quittant le répertoire « /home/rabgye/alsa-driver-1.0.14/drivers »
make[2]: entrant dans le répertoire « /home/rabgye/alsa-driver-1.0.14/isa »
make[3]: entrant dans le répertoire « /home/rabgye/alsa-driver-1.0.14/isa/ad1816a »
make[3]: quittant le répertoire « /home/rabgye/alsa-driver-1.0.14/isa/ad1816a »
make[3]: entrant dans le répertoire « /home/rabgye/alsa-driver-1.0.14/isa/ad1848 »
make[3]: quittant le répertoire « /home/rabgye/alsa-driver-1.0.14/isa/ad1848 »
make[3]: entrant dans le répertoire « /home/rabgye/alsa-driver-1.0.14/isa/cs423x »
make[3]: quittant le répertoire « /home/rabgye/alsa-driver-1.0.14/isa/cs423x »
make[3]: entrant dans le répertoire « /home/rabgye/alsa-driver-1.0.14/isa/es1688 »
make[3]: quittant le répertoire « /home/rabgye/alsa-driver-1.0.14/isa/es1688 »
make[3]: entrant dans le répertoire « /home/rabgye/alsa-driver-1.0.14/isa/gus »
make[3]: quittant le répertoire « /home/rabgye/alsa-driver-1.0.14/isa/gus »
make[3]: entrant dans le répertoire « /home/rabgye/alsa-driver-1.0.14/isa/msnd »
make[3]: quittant le répertoire « /home/rabgye/alsa-driver-1.0.14/isa/msnd »
make[3]: entrant dans le répertoire « /home/rabgye/alsa-driver-1.0.14/isa/opti9xx »
make[3]: quittant le répertoire « /home/rabgye/alsa-driver-1.0.14/isa/opti9xx »
make[3]: entrant dans le répertoire « /home/rabgye/alsa-driver-1.0.14/isa/sb »
copying file alsa-kernel/isa/sb/sb16_csp.c
patching file sb16_csp.c
Hunk #1 succeeded at 730 (offset 7 lines).
make[3]: quittant le répertoire « /home/rabgye/alsa-driver-1.0.14/isa/sb »
make[3]: entrant dans le répertoire « /home/rabgye/alsa-driver-1.0.14/isa/wavefront »
copying file alsa-kernel/isa/wavefront/wavefront_fx.c
patching file wavefront_fx.c
make[3]: quittant le répertoire « /home/rabgye/alsa-driver-1.0.14/isa/wavefront »
make[2]: quittant le répertoire « /home/rabgye/alsa-driver-1.0.14/isa »
make[2]: entrant dans le répertoire « /home/rabgye/alsa-driver-1.0.14/synth »
make[3]: entrant dans le répertoire « /home/rabgye/alsa-driver-1.0.14/synth/emux »
make[3]: quittant le répertoire « /home/rabgye/alsa-driver-1.0.14/synth/emux »
make[2]: quittant le répertoire « /home/rabgye/alsa-driver-1.0.14/synth »
make[2]: entrant dans le répertoire « /home/rabgye/alsa-driver-1.0.14/pci »
copying file alsa-kernel/pci/ad1889.c
patching file ad1889.c
Hunk #1 succeeded at 53 with fuzz 2 (offset 1 line).
copying file alsa-kernel/pci/bt87x.c
patching file bt87x.c
Hunk #1 succeeded at 818 (offset 8 lines).
Hunk #2 succeeded at 957 (offset 9 lines).
copying file alsa-kernel/pci/intel8x0.c
patching file intel8x0.c
Hunk #2 succeeded at 704 (offset 3 lines).
Hunk #3 succeeded at 715 (offset 3 lines).
Hunk #4 succeeded at 3094 (offset 83 lines).
copying file alsa-kernel/pci/maestro3.c
patching file maestro3.c
Hunk #1 succeeded at 2750 (offset 4 lines).
Hunk #2 succeeded at 2936 (offset 4 lines).
make[3]: entrant dans le répertoire « /home/rabgye/alsa-driver-1.0.14/pci/ac97 »
copying file alsa-kernel/pci/ac97/ac97_codec.c
patching file ac97_codec.c
make[3]: quittant le répertoire « /home/rabgye/alsa-driver-1.0.14/pci/ac97 »
make[3]: entrant dans le répertoire « /home/rabgye/alsa-driver-1.0.14/pci/ali5451 »
make[3]: quittant le répertoire « /home/rabgye/alsa-driver-1.0.14/pci/ali5451 »
make[3]: entrant dans le répertoire « /home/rabgye/alsa-driver-1.0.14/pci/asihpi »
make[3]: quittant le répertoire « /home/rabgye/alsa-driver-1.0.14/pci/asihpi »
make[3]: entrant dans le répertoire « /home/rabgye/alsa-driver-1.0.14/pci/au88x0 »
make[3]: quittant le répertoire « /home/rabgye/alsa-driver-1.0.14/pci/au88x0 »
make[3]: entrant dans le répertoire « /home/rabgye/alsa-driver-1.0.14/pci/ca0106 »
make[3]: quittant le répertoire « /home/rabgye/alsa-driver-1.0.14/pci/ca0106 »
make[3]: entrant dans le répertoire « /home/rabgye/alsa-driver-1.0.14/pci/cs46xx »
make[3]: quittant le répertoire « /home/rabgye/alsa-driver-1.0.14/pci/cs46xx »
make[3]: entrant dans le répertoire « /home/rabgye/alsa-driver-1.0.14/pci/cs5535audio »
make[3]: quittant le répertoire « /home/rabgye/alsa-driver-1.0.14/pci/cs5535audio »
make[3]: entrant dans le répertoire « /home/rabgye/alsa-driver-1.0.14/pci/echoaudio »
copying file alsa-kernel/pci/echoaudio/echoaudio.c
patching file echoaudio.c
Hunk #1 succeeded at 1924 (offset -2 lines).
Hunk #2 succeeded at 1987 (offset -2 lines).
copying file alsa-kernel/pci/echoaudio/darla20.c
patching file darla20.c
Hunk #2 succeeded at 107 (offset 2 lines).
copying file alsa-kernel/pci/echoaudio/darla24.c
patching file darla24.c
Hunk #2 succeeded at 114 (offset 2 lines).
copying file alsa-kernel/pci/echoaudio/echo3g.c
patching file echo3g.c
Hunk #2 succeeded at 128 (offset 4 lines).
copying file alsa-kernel/pci/echoaudio/gina20.c
patching file gina20.c
Hunk #2 succeeded at 111 (offset 2 lines).
copying file alsa-kernel/pci/echoaudio/gina24.c
patching file gina24.c
Hunk #2 succeeded at 135 (offset 6 lines).
copying file alsa-kernel/pci/echoaudio/indigo.c
patching file indigo.c
Hunk #2 succeeded at 113 (offset 3 lines).
copying file alsa-kernel/pci/echoaudio/indigodj.c
patching file indigodj.c
Hunk #2 succeeded at 113 (offset 3 lines).
copying file alsa-kernel/pci/echoaudio/indigoio.c
patching file indigoio.c
Hunk #2 succeeded at 114 (offset 3 lines).
copying file alsa-kernel/pci/echoaudio/layla20.c
patching file layla20.c
Hunk #2 succeeded at 121 (offset 3 lines).
copying file alsa-kernel/pci/echoaudio/layla24.c
patching file layla24.c
Hunk #2 succeeded at 133 (offset 6 lines).
copying file alsa-kernel/pci/echoaudio/mia.c
patching file mia.c
Hunk #2 succeeded at 126 (offset 3 lines).
copying file alsa-kernel/pci/echoaudio/mona.c
patching file mona.c
Hunk #2 succeeded at 144 (offset 9 lines).
make[3]: quittant le répertoire « /home/rabgye/alsa-driver-1.0.14/pci/echoaudio »
make[3]: entrant dans le répertoire « /home/rabgye/alsa-driver-1.0.14/pci/emu10k1 »
copying file alsa-kernel/pci/emu10k1/emu10k1_main.c
patching file emu10k1_main.c
Hunk #2 succeeded at 656 (offset 44 lines).
make[3]: quittant le répertoire « /home/rabgye/alsa-driver-1.0.14/pci/emu10k1 »
make[3]: entrant dans le répertoire « /home/rabgye/alsa-driver-1.0.14/pci/hda »
copying file alsa-kernel/pci/hda/hda_codec.c
patching file hda_codec.c
make[3]: quittant le répertoire « /home/rabgye/alsa-driver-1.0.14/pci/hda »
make[3]: entrant dans le répertoire « /home/rabgye/alsa-driver-1.0.14/pci/ice1712 »
make[3]: quittant le répertoire « /home/rabgye/alsa-driver-1.0.14/pci/ice1712 »
make[3]: entrant dans le répertoire « /home/rabgye/alsa-driver-1.0.14/pci/korg1212 »
copying file alsa-kernel/pci/korg1212/korg1212.c
patching file korg1212.c
Hunk #1 succeeded at 2346 (offset 3 lines).
Hunk #2 succeeded at 2507 (offset 3 lines).
make[3]: quittant le répertoire « /home/rabgye/alsa-driver-1.0.14/pci/korg1212 »
make[3]: entrant dans le répertoire « /home/rabgye/alsa-driver-1.0.14/pci/mixart »
make[3]: quittant le répertoire « /home/rabgye/alsa-driver-1.0.14/pci/mixart »
make[3]: entrant dans le répertoire « /home/rabgye/alsa-driver-1.0.14/pci/nm256 »
make[3]: quittant le répertoire « /home/rabgye/alsa-driver-1.0.14/pci/nm256 »
make[3]: entrant dans le répertoire « /home/rabgye/alsa-driver-1.0.14/pci/pcxhr »
make[3]: quittant le répertoire « /home/rabgye/alsa-driver-1.0.14/pci/pcxhr »
make[3]: entrant dans le répertoire « /home/rabgye/alsa-driver-1.0.14/pci/pdplus »
make[3]: quittant le répertoire « /home/rabgye/alsa-driver-1.0.14/pci/pdplus »
make[3]: entrant dans le répertoire « /home/rabgye/alsa-driver-1.0.14/pci/riptide »
copying file alsa-kernel/pci/riptide/riptide.c
patching file riptide.c
Hunk #1 succeeded at 1279 (offset 10 lines).
Hunk #2 succeeded at 2236 (offset 10 lines).
make[3]: quittant le répertoire « /home/rabgye/alsa-driver-1.0.14/pci/riptide »
make[3]: entrant dans le répertoire « /home/rabgye/alsa-driver-1.0.14/pci/rme9652 »
make[3]: quittant le répertoire « /home/rabgye/alsa-driver-1.0.14/pci/rme9652 »
make[3]: entrant dans le répertoire « /home/rabgye/alsa-driver-1.0.14/pci/trident »
make[3]: quittant le répertoire « /home/rabgye/alsa-driver-1.0.14/pci/trident »
make[3]: entrant dans le répertoire « /home/rabgye/alsa-driver-1.0.14/pci/vx222 »
make[3]: quittant le répertoire « /home/rabgye/alsa-driver-1.0.14/pci/vx222 »
make[3]: entrant dans le répertoire « /home/rabgye/alsa-driver-1.0.14/pci/ymfpci »
copying file alsa-kernel/pci/ymfpci/ymfpci_main.c
patching file ymfpci_main.c
make[3]: quittant le répertoire « /home/rabgye/alsa-driver-1.0.14/pci/ymfpci »
make[2]: quittant le répertoire « /home/rabgye/alsa-driver-1.0.14/pci »
make[2]: entrant dans le répertoire « /home/rabgye/alsa-driver-1.0.14/aoa »
make[3]: entrant dans le répertoire « /home/rabgye/alsa-driver-1.0.14/aoa/codecs »
make[3]: quittant le répertoire « /home/rabgye/alsa-driver-1.0.14/aoa/codecs »
make[3]: entrant dans le répertoire « /home/rabgye/alsa-driver-1.0.14/aoa/core »
make[3]: quittant le répertoire « /home/rabgye/alsa-driver-1.0.14/aoa/core »
make[3]: entrant dans le répertoire « /home/rabgye/alsa-driver-1.0.14/aoa/fabrics »
make[3]: quittant le répertoire « /home/rabgye/alsa-driver-1.0.14/aoa/fabrics »
make[3]: entrant dans le répertoire « /home/rabgye/alsa-driver-1.0.14/aoa/soundbus »
make[4]: entrant dans le répertoire « /home/rabgye/alsa-driver-1.0.14/aoa/soundbus/i2sbus »
make[4]: quittant le répertoire « /home/rabgye/alsa-driver-1.0.14/aoa/soundbus/i2sbus »
make[3]: quittant le répertoire « /home/rabgye/alsa-driver-1.0.14/aoa/soundbus »
make[2]: quittant le répertoire « /home/rabgye/alsa-driver-1.0.14/aoa »
make[2]: entrant dans le répertoire « /home/rabgye/alsa-driver-1.0.14/soc »
make[3]: entrant dans le répertoire « /home/rabgye/alsa-driver-1.0.14/soc/at91 »
make[3]: quittant le répertoire « /home/rabgye/alsa-driver-1.0.14/soc/at91 »
make[3]: entrant dans le répertoire « /home/rabgye/alsa-driver-1.0.14/soc/codecs »
make[3]: quittant le répertoire « /home/rabgye/alsa-driver-1.0.14/soc/codecs »
make[3]: entrant dans le répertoire « /home/rabgye/alsa-driver-1.0.14/soc/pxa »
make[3]: quittant le répertoire « /home/rabgye/alsa-driver-1.0.14/soc/pxa »
make[3]: entrant dans le répertoire « /home/rabgye/alsa-driver-1.0.14/soc/s3c24xx »
make[3]: quittant le répertoire « /home/rabgye/alsa-driver-1.0.14/soc/s3c24xx »
make[3]: entrant dans le répertoire « /home/rabgye/alsa-driver-1.0.14/soc/sh »
make[3]: quittant le répertoire « /home/rabgye/alsa-driver-1.0.14/soc/sh »
make[2]: quittant le répertoire « /home/rabgye/alsa-driver-1.0.14/soc »
make[2]: entrant dans le répertoire « /home/rabgye/alsa-driver-1.0.14/usb »
copying file alsa-kernel/usb/usbaudio.c
patching file usbaudio.c
Hunk #3 succeeded at 660 with fuzz 2 (offset -9 lines).
Hunk #4 succeeded at 687 with fuzz 2 (offset -9 lines).
Hunk #5 succeeded at 768 (offset -9 lines).
Hunk #6 succeeded at 783 (offset -9 lines).
Hunk #7 succeeded at 1161 (offset -9 lines).
Hunk #11 succeeded at 2675 (offset 13 lines).
Hunk #12 succeeded at 2747 (offset 13 lines).
Hunk #13 succeeded at 3031 (offset 13 lines).
Hunk #14 succeeded at 3102 (offset 13 lines).
Hunk #15 succeeded at 3223 (offset 65 lines).
Hunk #16 succeeded at 3241 (offset 65 lines).
Hunk #17 succeeded at 3255 (offset 65 lines).
Hunk #18 succeeded at 3268 (offset 65 lines).
Hunk #19 succeeded at 3466 (offset 67 lines).
Hunk #20 succeeded at 3557 (offset 67 lines).
Hunk #21 succeeded at 3694 (offset 66 lines).
Hunk #22 succeeded at 3715 (offset 66 lines).
Hunk #23 succeeded at 3736 (offset 66 lines).
copying file alsa-kernel/usb/usbmidi.c
patching file usbmidi.c
Hunk #2 succeeded at 226 (offset 1 line).
Hunk #3 succeeded at 250 (offset 1 line).
Hunk #4 succeeded at 343 (offset 1 line).
Hunk #5 succeeded at 1413 (offset 51 lines).
Hunk #6 succeeded at 1760 (offset 54 lines).
copying file alsa-kernel/usb/usbmixer.c
patching file usbmixer.c
Hunk #3 succeeded at 1725 (offset -1 lines).
Hunk #4 succeeded at 1774 (offset -1 lines).
Hunk #5 succeeded at 1795 (offset -1 lines).
make[3]: entrant dans le répertoire « /home/rabgye/alsa-driver-1.0.14/usb/caiaq »
make[3]: quittant le répertoire « /home/rabgye/alsa-driver-1.0.14/usb/caiaq »
make[3]: entrant dans le répertoire « /home/rabgye/alsa-driver-1.0.14/usb/usx2y »
copying file alsa-kernel/usb/usx2y/usX2Yhwdep.c
patching file usX2Yhwdep.c
Hunk #3 succeeded at 63 with fuzz 2.
copying file alsa-kernel/usb/usx2y/usbusx2y.c
patching file usbusx2y.c
copying file alsa-kernel/usb/usx2y/usbusx2yaudio.c
patching file usbusx2yaudio.c
Hunk #10 succeeded at 1057 (offset -1 lines).
copying file alsa-kernel/usb/usx2y/usx2yhwdeppcm.c
patching file usx2yhwdeppcm.c
make[3]: quittant le répertoire « /home/rabgye/alsa-driver-1.0.14/usb/usx2y »
make[2]: quittant le répertoire « /home/rabgye/alsa-driver-1.0.14/usb »
make[2]: entrant dans le répertoire « /home/rabgye/alsa-driver-1.0.14/pcmcia »
make[3]: entrant dans le répertoire « /home/rabgye/alsa-driver-1.0.14/pcmcia/pdaudiocf »
make[3]: quittant le répertoire « /home/rabgye/alsa-driver-1.0.14/pcmcia/pdaudiocf »
make[3]: entrant dans le répertoire « /home/rabgye/alsa-driver-1.0.14/pcmcia/vx »
make[3]: quittant le répertoire « /home/rabgye/alsa-driver-1.0.14/pcmcia/vx »
make[2]: quittant le répertoire « /home/rabgye/alsa-driver-1.0.14/pcmcia »
make[2]: entrant dans le répertoire « /home/rabgye/alsa-driver-1.0.14/misc »
make[2]: quittant le répertoire « /home/rabgye/alsa-driver-1.0.14/misc »
make[1]: quittant le répertoire « /home/rabgye/alsa-driver-1.0.14 »
make -C /lib/modules/2.6.28-3-rt/build SUBDIRS=/home/rabgye/alsa-driver-1.0.14  CPP="gcc -E" CC="gcc" modules
make[1]: entrant dans le répertoire « /usr/src/linux-headers-2.6.28-3-rt »
scripts/Makefile.build:46: *** CFLAGS was changed in "/home/rabgye/alsa-driver-1.0.14/acore/Makefile". Fix it to use EXTRA_CFLAGS. Arrêt.
make[2]: *** [/home/rabgye/alsa-driver-1.0.14/acore] Erreur 2
make[1]: *** [_module_/home/rabgye/alsa-driver-1.0.14] Erreur 2
make[1]: quittant le répertoire « /usr/src/linux-headers-2.6.28-3-rt »
make: *** [compile] Erreur 2
rabgye@ubuntumaya:~/alsa-driver-1.0.14$

---

### Post by pytheas22 on 2009-06-28
> ton dernier message contenait un quiproquo;j'ai essaye la preliere fois avec alsa-driver-1.0.20;l'installation areussie mais sans changements en ce qui concerne la capture du son .en essayant de compiler alsa-driver-1.0.14 j'obtiens une errreur;voici l'output:

Oui, tu as déjà compilé alsa-driver-1.0.20, mais la page que j'ai citée dans mon dernier message a suggéré quelques précisions que tu n'as pas faites la première fois, à savoir celles en caractères gras:
```

[B]echo snd-hda-intel | sudo tee -a /etc/modprobe.d/blacklist.conf
[/B]wget ftp://ftp.alsa-project.org/pub/driver/alsa-driver-1.0.20.tar.bz2
tar -xvf alsa-driver-1.0.20.tar.bz2
cd alsa-driver-1.0.20
./configure **--with-cards=all --with-card-options=all**
sudo make
sudo make install
```

Je ne sais pas si cela produirait des resultats différents pour vous, mais je pense qu'il vaut la peine d'essayer, vu qu'on n'a pas d'autre idée...


En ce qui concerne alsamixer, je pense que cela ne marche pas à cause des problèmes avec le pilote son...donc il faut les résoluer afin qu'alsamixer marche.

---

### Post by manjusri on 2009-06-29
bonjour pytheas;j'avais deja essaye ce que tu m'as dit;comme je ne t'avais pas envoye les outputs j'ai recommence et donc les outputs:













































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































  LD [M]  /home/rabgye/alsa-driver-1.0.20/soc/snd-soc-core.o
  CC [M]  /home/rabgye/alsa-driver-1.0.20/synth/util_mem.o
  LD [M]  /home/rabgye/alsa-driver-1.0.20/synth/snd-util-mem.o
  CC [M]  /home/rabgye/alsa-driver-1.0.20/synth/emux/emux.o
  CC [M]  /home/rabgye/alsa-driver-1.0.20/synth/emux/emux_synth.o
  CC [M]  /home/rabgye/alsa-driver-1.0.20/synth/emux/emux_seq.o
  CC [M]  /home/rabgye/alsa-driver-1.0.20/synth/emux/emux_nrpn.o
  CC [M]  /home/rabgye/alsa-driver-1.0.20/synth/emux/emux_effect.o
  CC [M]  /home/rabgye/alsa-driver-1.0.20/synth/emux/emux_proc.o
  CC [M]  /home/rabgye/alsa-driver-1.0.20/synth/emux/emux_hwdep.o
  CC [M]  /home/rabgye/alsa-driver-1.0.20/synth/emux/soundfont.o
  CC [M]  /home/rabgye/alsa-driver-1.0.20/synth/emux/emux_oss.o
  LD [M]  /home/rabgye/alsa-driver-1.0.20/synth/emux/snd-emux-synth.o
  CC [M]  /home/rabgye/alsa-driver-1.0.20/usb/usbaudio.o
  CC [M]  /home/rabgye/alsa-driver-1.0.20/usb/usbmixer.o
  CC [M]  /home/rabgye/alsa-driver-1.0.20/usb/usbmidi.o
  LD [M]  /home/rabgye/alsa-driver-1.0.20/usb/snd-usb-audio.o
  LD [M]  /home/rabgye/alsa-driver-1.0.20/usb/snd-usb-lib.o
  CC [M]  /home/rabgye/alsa-driver-1.0.20/usb/caiaq/device.o
  CC [M]  /home/rabgye/alsa-driver-1.0.20/usb/caiaq/audio.o
  CC [M]  /home/rabgye/alsa-driver-1.0.20/usb/caiaq/midi.o
  CC [M]  /home/rabgye/alsa-driver-1.0.20/usb/caiaq/control.o
  CC [M]  /home/rabgye/alsa-driver-1.0.20/usb/caiaq/input.o
  LD [M]  /home/rabgye/alsa-driver-1.0.20/usb/caiaq/snd-usb-caiaq.o
  CC [M]  /home/rabgye/alsa-driver-1.0.20/usb/usx2y/us122l.o
  CC [M]  /home/rabgye/alsa-driver-1.0.20/usb/usx2y/usbusx2y.o
  CC [M]  /home/rabgye/alsa-driver-1.0.20/usb/usx2y/usX2Yhwdep.o
  CC [M]  /home/rabgye/alsa-driver-1.0.20/usb/usx2y/usx2yhwdeppcm.o
  LD [M]  /home/rabgye/alsa-driver-1.0.20/usb/usx2y/snd-usb-usx2y.o
  LD [M]  /home/rabgye/alsa-driver-1.0.20/usb/usx2y/snd-usb-us122l.o
  Building modules, stage 2.
  MODPOST 130 modules
  LD [M]  /home/rabgye/alsa-driver-1.0.20/acore/oss/snd-mixer-oss.ko
  LD [M]  /home/rabgye/alsa-driver-1.0.20/acore/oss/snd-pcm-oss.ko
  LD [M]  /home/rabgye/alsa-driver-1.0.20/acore/seq/oss/snd-seq-oss.ko
  LD [M]  /home/rabgye/alsa-driver-1.0.20/acore/seq/snd-seq-device.ko
  LD [M]  /home/rabgye/alsa-driver-1.0.20/acore/seq/snd-seq-dummy.ko
  LD [M]  /home/rabgye/alsa-driver-1.0.20/acore/seq/snd-seq-midi-emul.ko
  LD [M]  /home/rabgye/alsa-driver-1.0.20/acore/seq/snd-seq-midi-event.ko
  LD [M]  /home/rabgye/alsa-driver-1.0.20/acore/seq/snd-seq-midi.ko
  LD [M]  /home/rabgye/alsa-driver-1.0.20/acore/seq/snd-seq-virmidi.ko
  LD [M]  /home/rabgye/alsa-driver-1.0.20/acore/seq/snd-seq.ko
  LD [M]  /home/rabgye/alsa-driver-1.0.20/acore/snd-hrtimer.ko
  LD [M]  /home/rabgye/alsa-driver-1.0.20/acore/snd-hwdep.ko
  LD [M]  /home/rabgye/alsa-driver-1.0.20/acore/snd-page-alloc.ko
  LD [M]  /home/rabgye/alsa-driver-1.0.20/acore/snd-pcm.ko
  LD [M]  /home/rabgye/alsa-driver-1.0.20/acore/snd-rawmidi.ko
  LD [M]  /home/rabgye/alsa-driver-1.0.20/acore/snd-timer.ko
  LD [M]  /home/rabgye/alsa-driver-1.0.20/acore/snd.ko
  LD [M]  /home/rabgye/alsa-driver-1.0.20/drivers/mpu401/snd-mpu401-uart.ko
  LD [M]  /home/rabgye/alsa-driver-1.0.20/drivers/mpu401/snd-mpu401.ko
  LD [M]  /home/rabgye/alsa-driver-1.0.20/drivers/opl3/snd-opl3-lib.ko
  LD [M]  /home/rabgye/alsa-driver-1.0.20/drivers/opl3/snd-opl3-synth.ko
  LD [M]  /home/rabgye/alsa-driver-1.0.20/drivers/pcsp/snd-pcsp.ko
  LD [M]  /home/rabgye/alsa-driver-1.0.20/drivers/snd-aloop.ko
  LD [M]  /home/rabgye/alsa-driver-1.0.20/drivers/snd-dummy.ko
  LD [M]  /home/rabgye/alsa-driver-1.0.20/drivers/snd-mtpav.ko
  LD [M]  /home/rabgye/alsa-driver-1.0.20/drivers/snd-mts64.ko
  LD [M]  /home/rabgye/alsa-driver-1.0.20/drivers/snd-portman2x4.ko
  LD [M]  /home/rabgye/alsa-driver-1.0.20/drivers/snd-serial-u16550.ko
  LD [M]  /home/rabgye/alsa-driver-1.0.20/drivers/snd-virmidi.ko
  LD [M]  /home/rabgye/alsa-driver-1.0.20/drivers/vx/snd-vx-lib.ko
  LD [M]  /home/rabgye/alsa-driver-1.0.20/i2c/other/snd-ak4114.ko
  LD [M]  /home/rabgye/alsa-driver-1.0.20/i2c/other/snd-ak4117.ko
  LD [M]  /home/rabgye/alsa-driver-1.0.20/i2c/other/snd-ak4xxx-adda.ko
  LD [M]  /home/rabgye/alsa-driver-1.0.20/i2c/other/snd-pt2258.ko
  LD [M]  /home/rabgye/alsa-driver-1.0.20/i2c/other/snd-tea575x-tuner.ko
  LD [M]  /home/rabgye/alsa-driver-1.0.20/i2c/snd-cs8427.ko
  LD [M]  /home/rabgye/alsa-driver-1.0.20/i2c/snd-i2c.ko
  LD [M]  /home/rabgye/alsa-driver-1.0.20/isa/sb/snd-sb-common.ko
  LD [M]  /home/rabgye/alsa-driver-1.0.20/isa/sb/snd-sb16-dsp.ko
  LD [M]  /home/rabgye/alsa-driver-1.0.20/misc/ac97_bus.ko
  LD [M]  /home/rabgye/alsa-driver-1.0.20/pci/ac97/snd-ac97-codec.ko
  LD [M]  /home/rabgye/alsa-driver-1.0.20/pci/ali5451/snd-ali5451.ko
  LD [M]  /home/rabgye/alsa-driver-1.0.20/pci/asihpi/snd-asihpi.ko
  LD [M]  /home/rabgye/alsa-driver-1.0.20/pci/au88x0/snd-au8810.ko
  LD [M]  /home/rabgye/alsa-driver-1.0.20/pci/au88x0/snd-au8820.ko
  LD [M]  /home/rabgye/alsa-driver-1.0.20/pci/au88x0/snd-au8830.ko
  LD [M]  /home/rabgye/alsa-driver-1.0.20/pci/aw2/snd-aw2.ko
  LD [M]  /home/rabgye/alsa-driver-1.0.20/pci/ca0106/snd-ca0106.ko
  LD [M]  /home/rabgye/alsa-driver-1.0.20/pci/cs46xx/snd-cs46xx.ko
  LD [M]  /home/rabgye/alsa-driver-1.0.20/pci/echoaudio/snd-darla20.ko
  LD [M]  /home/rabgye/alsa-driver-1.0.20/pci/echoaudio/snd-darla24.ko
  LD [M]  /home/rabgye/alsa-driver-1.0.20/pci/echoaudio/snd-echo3g.ko
  LD [M]  /home/rabgye/alsa-driver-1.0.20/pci/echoaudio/snd-gina20.ko
  LD [M]  /home/rabgye/alsa-driver-1.0.20/pci/echoaudio/snd-gina24.ko
  LD [M]  /home/rabgye/alsa-driver-1.0.20/pci/echoaudio/snd-indigo.ko
  LD [M]  /home/rabgye/alsa-driver-1.0.20/pci/echoaudio/snd-indigodj.ko
  LD [M]  /home/rabgye/alsa-driver-1.0.20/pci/echoaudio/snd-indigodjx.ko
  LD [M]  /home/rabgye/alsa-driver-1.0.20/pci/echoaudio/snd-indigoio.ko
  LD [M]  /home/rabgye/alsa-driver-1.0.20/pci/echoaudio/snd-indigoiox.ko
  LD [M]  /home/rabgye/alsa-driver-1.0.20/pci/echoaudio/snd-layla20.ko
  LD [M]  /home/rabgye/alsa-driver-1.0.20/pci/echoaudio/snd-layla24.ko
  LD [M]  /home/rabgye/alsa-driver-1.0.20/pci/echoaudio/snd-mia.ko
  LD [M]  /home/rabgye/alsa-driver-1.0.20/pci/echoaudio/snd-mona.ko
  LD [M]  /home/rabgye/alsa-driver-1.0.20/pci/emu10k1/snd-emu10k1-synth.ko
  LD [M]  /home/rabgye/alsa-driver-1.0.20/pci/emu10k1/snd-emu10k1.ko
  LD [M]  /home/rabgye/alsa-driver-1.0.20/pci/emu10k1/snd-emu10k1x.ko
  LD [M]  /home/rabgye/alsa-driver-1.0.20/pci/hda/snd-hda-codec-analog.ko
  LD [M]  /home/rabgye/alsa-driver-1.0.20/pci/hda/snd-hda-codec-atihdmi.ko
  LD [M]  /home/rabgye/alsa-driver-1.0.20/pci/hda/snd-hda-codec-cmedia.ko
  LD [M]  /home/rabgye/alsa-driver-1.0.20/pci/hda/snd-hda-codec-conexant.ko
  LD [M]  /home/rabgye/alsa-driver-1.0.20/pci/hda/snd-hda-codec-idt.ko
  LD [M]  /home/rabgye/alsa-driver-1.0.20/pci/hda/snd-hda-codec-intelhdmi.ko
  LD [M]  /home/rabgye/alsa-driver-1.0.20/pci/hda/snd-hda-codec-nvhdmi.ko
  LD [M]  /home/rabgye/alsa-driver-1.0.20/pci/hda/snd-hda-codec-realtek.ko
  LD [M]  /home/rabgye/alsa-driver-1.0.20/pci/hda/snd-hda-codec-si3054.ko
  LD [M]  /home/rabgye/alsa-driver-1.0.20/pci/hda/snd-hda-codec-via.ko
  LD [M]  /home/rabgye/alsa-driver-1.0.20/pci/hda/snd-hda-codec.ko
  LD [M]  /home/rabgye/alsa-driver-1.0.20/pci/hda/snd-hda-intel.ko
  LD [M]  /home/rabgye/alsa-driver-1.0.20/pci/ice1712/snd-ice1712.ko
  LD [M]  /home/rabgye/alsa-driver-1.0.20/pci/ice1712/snd-ice1724.ko
  LD [M]  /home/rabgye/alsa-driver-1.0.20/pci/ice1712/snd-ice17xx-ak4xxx.ko
  LD [M]  /home/rabgye/alsa-driver-1.0.20/pci/korg1212/snd-korg1212.ko
  LD [M]  /home/rabgye/alsa-driver-1.0.20/pci/mixart/snd-mixart.ko
  LD [M]  /home/rabgye/alsa-driver-1.0.20/pci/nm256/snd-nm256.ko
  LD [M]  /home/rabgye/alsa-driver-1.0.20/pci/oxygen/snd-hifier.ko
  LD [M]  /home/rabgye/alsa-driver-1.0.20/pci/oxygen/snd-oxygen-lib.ko
  LD [M]  /home/rabgye/alsa-driver-1.0.20/pci/oxygen/snd-oxygen.ko
  LD [M]  /home/rabgye/alsa-driver-1.0.20/pci/oxygen/snd-virtuoso.ko
  LD [M]  /home/rabgye/alsa-driver-1.0.20/pci/pcxhr/snd-pcxhr.ko
  LD [M]  /home/rabgye/alsa-driver-1.0.20/pci/pdplus/snd-pdplus.ko
  LD [M]  /home/rabgye/alsa-driver-1.0.20/pci/riptide/snd-riptide.ko
  LD [M]  /home/rabgye/alsa-driver-1.0.20/pci/rme9652/snd-hdsp.ko
  LD [M]  /home/rabgye/alsa-driver-1.0.20/pci/rme9652/snd-hdspm.ko
  LD [M]  /home/rabgye/alsa-driver-1.0.20/pci/rme9652/snd-rme9652.ko
  LD [M]  /home/rabgye/alsa-driver-1.0.20/pci/snd-ad1889.ko
  LD [M]  /home/rabgye/alsa-driver-1.0.20/pci/snd-als300.ko
  LD [M]  /home/rabgye/alsa-driver-1.0.20/pci/snd-als4000.ko
  LD [M]  /home/rabgye/alsa-driver-1.0.20/pci/snd-atiixp-modem.ko
  LD [M]  /home/rabgye/alsa-driver-1.0.20/pci/snd-atiixp.ko
  LD [M]  /home/rabgye/alsa-driver-1.0.20/pci/snd-azt3328.ko
  LD [M]  /home/rabgye/alsa-driver-1.0.20/pci/snd-bt87x.ko
  LD [M]  /home/rabgye/alsa-driver-1.0.20/pci/snd-cmipci.ko
  LD [M]  /home/rabgye/alsa-driver-1.0.20/pci/snd-cs4281.ko
  LD [M]  /home/rabgye/alsa-driver-1.0.20/pci/snd-cs5530.ko
  LD [M]  /home/rabgye/alsa-driver-1.0.20/pci/snd-ens1370.ko
  LD [M]  /home/rabgye/alsa-driver-1.0.20/pci/snd-ens1371.ko
  LD [M]  /home/rabgye/alsa-driver-1.0.20/pci/snd-es1938.ko
  LD [M]  /home/rabgye/alsa-driver-1.0.20/pci/snd-es1968.ko
  LD [M]  /home/rabgye/alsa-driver-1.0.20/pci/snd-fm801.ko
  LD [M]  /home/rabgye/alsa-driver-1.0.20/pci/snd-intel8x0.ko
  LD [M]  /home/rabgye/alsa-driver-1.0.20/pci/snd-intel8x0m.ko
  LD [M]  /home/rabgye/alsa-driver-1.0.20/pci/snd-maestro3.ko
  LD [M]  /home/rabgye/alsa-driver-1.0.20/pci/snd-rme32.ko
  LD [M]  /home/rabgye/alsa-driver-1.0.20/pci/snd-rme96.ko
  LD [M]  /home/rabgye/alsa-driver-1.0.20/pci/snd-sonicvibes.ko
  LD [M]  /home/rabgye/alsa-driver-1.0.20/pci/snd-via82xx-modem.ko
  LD [M]  /home/rabgye/alsa-driver-1.0.20/pci/snd-via82xx.ko
  LD [M]  /home/rabgye/alsa-driver-1.0.20/pci/trident/snd-trident.ko
  LD [M]  /home/rabgye/alsa-driver-1.0.20/pci/vx222/snd-vx222.ko
  LD [M]  /home/rabgye/alsa-driver-1.0.20/pci/ymfpci/snd-ymfpci.ko
  LD [M]  /home/rabgye/alsa-driver-1.0.20/pcmcia/pdaudiocf/snd-pdaudiocf.ko
  LD [M]  /home/rabgye/alsa-driver-1.0.20/pcmcia/vx/snd-vxpocket.ko
  LD [M]  /home/rabgye/alsa-driver-1.0.20/soc/snd-soc-core.ko
  LD [M]  /home/rabgye/alsa-driver-1.0.20/synth/emux/snd-emux-synth.ko
  LD [M]  /home/rabgye/alsa-driver-1.0.20/synth/snd-util-mem.ko
  LD [M]  /home/rabgye/alsa-driver-1.0.20/usb/caiaq/snd-usb-caiaq.ko
  LD [M]  /home/rabgye/alsa-driver-1.0.20/usb/snd-usb-audio.ko
  LD [M]  /home/rabgye/alsa-driver-1.0.20/usb/snd-usb-lib.ko
  LD [M]  /home/rabgye/alsa-driver-1.0.20/usb/usx2y/snd-usb-us122l.ko
  LD [M]  /home/rabgye/alsa-driver-1.0.20/usb/usx2y/snd-usb-usx2y.ko
make[1]: quittant le répertoire « /usr/src/linux-headers-2.6.28-3-rt »
utils/link-modules /home/rabgye/alsa-driver-1.0.20

ALSA modules were successfully compiled.

rabgye@ubuntumaya:~/alsa-driver-1.0.20$ sudo make install
if [ -L /usr/include/sound ]; then \
        rm -f /usr/include/sound; \
        ln -sf /home/rabgye/alsa-driver-1.0.20/include/sound /usr/include/sound; \
    else \
        rm -rf /usr/include/sound; \
        install -d -m 755 -g root -o root /usr/include/sound; \
        for f in include/sound/*.h; do \
            install -m 644 -g root -o root $f /usr/include/sound; \
        done \
    fi
find /lib/modules/2.6.28-3-rt/kernel/sound -name 'snd*.*o' | xargs rm -f
find /lib/modules/2.6.28-3-rt/kernel/sound -name 'snd*.*o.gz' | xargs rm -f
find /lib/modules/2.6.28-3-rt/kernel/sound -name 'ac97_bus.*o' | xargs rm -f
find /lib/modules/2.6.28-3-rt/kernel/sound -name 'ac97_bus.*o.gz' | xargs rm -f
make[1]: entrant dans le répertoire « /home/rabgye/alsa-driver-1.0.20/acore »
mkdir -p /lib/modules/2.6.28-3-rt/kernel/sound/acore
cp snd-hrtimer.ko snd-hwdep.ko snd-page-alloc.ko snd-pcm.ko snd-rawmidi.ko snd-timer.ko snd.ko /lib/modules/2.6.28-3-rt/kernel/sound/acore
make[2]: entrant dans le répertoire « /home/rabgye/alsa-driver-1.0.20/acore/ioctl32 »
make[2]: quittant le répertoire « /home/rabgye/alsa-driver-1.0.20/acore/ioctl32 »
make[2]: entrant dans le répertoire « /home/rabgye/alsa-driver-1.0.20/acore/oss »
mkdir -p /lib/modules/2.6.28-3-rt/kernel/sound/acore/oss
cp snd-mixer-oss.ko snd-pcm-oss.ko /lib/modules/2.6.28-3-rt/kernel/sound/acore/oss
make[2]: quittant le répertoire « /home/rabgye/alsa-driver-1.0.20/acore/oss »
make[2]: entrant dans le répertoire « /home/rabgye/alsa-driver-1.0.20/acore/seq »
mkdir -p /lib/modules/2.6.28-3-rt/kernel/sound/acore/seq
cp snd-seq-device.ko snd-seq-dummy.ko snd-seq-midi-emul.ko snd-seq-midi-event.ko snd-seq-midi.ko snd-seq-virmidi.ko snd-seq.ko /lib/modules/2.6.28-3-rt/kernel/sound/acore/seq
make[3]: entrant dans le répertoire « /home/rabgye/alsa-driver-1.0.20/acore/seq/oss »
mkdir -p /lib/modules/2.6.28-3-rt/kernel/sound/acore/seq/oss
cp snd-seq-oss.ko /lib/modules/2.6.28-3-rt/kernel/sound/acore/seq/oss
make[3]: quittant le répertoire « /home/rabgye/alsa-driver-1.0.20/acore/seq/oss »
make[2]: quittant le répertoire « /home/rabgye/alsa-driver-1.0.20/acore/seq »
make[1]: quittant le répertoire « /home/rabgye/alsa-driver-1.0.20/acore »
make[1]: entrant dans le répertoire « /home/rabgye/alsa-driver-1.0.20/i2c »
mkdir -p /lib/modules/2.6.28-3-rt/kernel/sound/i2c
cp snd-cs8427.ko snd-i2c.ko /lib/modules/2.6.28-3-rt/kernel/sound/i2c
make[2]: entrant dans le répertoire « /home/rabgye/alsa-driver-1.0.20/i2c/l3 »
make[2]: quittant le répertoire « /home/rabgye/alsa-driver-1.0.20/i2c/l3 »
make[2]: entrant dans le répertoire « /home/rabgye/alsa-driver-1.0.20/i2c/other »
mkdir -p /lib/modules/2.6.28-3-rt/kernel/sound/i2c/other
cp snd-ak4114.ko snd-ak4117.ko snd-ak4xxx-adda.ko snd-pt2258.ko snd-tea575x-tuner.ko /lib/modules/2.6.28-3-rt/kernel/sound/i2c/other
make[2]: quittant le répertoire « /home/rabgye/alsa-driver-1.0.20/i2c/other »
make[1]: quittant le répertoire « /home/rabgye/alsa-driver-1.0.20/i2c »
make[1]: entrant dans le répertoire « /home/rabgye/alsa-driver-1.0.20/drivers »
mkdir -p /lib/modules/2.6.28-3-rt/kernel/sound/drivers
cp snd-aloop.ko snd-dummy.ko snd-mtpav.ko snd-mts64.ko snd-portman2x4.ko snd-serial-u16550.ko snd-virmidi.ko /lib/modules/2.6.28-3-rt/kernel/sound/drivers
make[2]: entrant dans le répertoire « /home/rabgye/alsa-driver-1.0.20/drivers/mpu401 »
mkdir -p /lib/modules/2.6.28-3-rt/kernel/sound/drivers/mpu401
cp snd-mpu401-uart.ko snd-mpu401.ko /lib/modules/2.6.28-3-rt/kernel/sound/drivers/mpu401
make[2]: quittant le répertoire « /home/rabgye/alsa-driver-1.0.20/drivers/mpu401 »
make[2]: entrant dans le répertoire « /home/rabgye/alsa-driver-1.0.20/drivers/opl3 »
mkdir -p /lib/modules/2.6.28-3-rt/kernel/sound/drivers/opl3
cp snd-opl3-lib.ko snd-opl3-synth.ko /lib/modules/2.6.28-3-rt/kernel/sound/drivers/opl3
make[2]: quittant le répertoire « /home/rabgye/alsa-driver-1.0.20/drivers/opl3 »
make[2]: entrant dans le répertoire « /home/rabgye/alsa-driver-1.0.20/drivers/opl4 »
make[2]: quittant le répertoire « /home/rabgye/alsa-driver-1.0.20/drivers/opl4 »
make[2]: entrant dans le répertoire « /home/rabgye/alsa-driver-1.0.20/drivers/pcsp »
mkdir -p /lib/modules/2.6.28-3-rt/kernel/sound/drivers/pcsp
cp snd-pcsp.ko /lib/modules/2.6.28-3-rt/kernel/sound/drivers/pcsp
make[2]: quittant le répertoire « /home/rabgye/alsa-driver-1.0.20/drivers/pcsp »
make[2]: entrant dans le répertoire « /home/rabgye/alsa-driver-1.0.20/drivers/vx »
mkdir -p /lib/modules/2.6.28-3-rt/kernel/sound/drivers/vx
cp snd-vx-lib.ko /lib/modules/2.6.28-3-rt/kernel/sound/drivers/vx
make[2]: quittant le répertoire « /home/rabgye/alsa-driver-1.0.20/drivers/vx »
make[1]: quittant le répertoire « /home/rabgye/alsa-driver-1.0.20/drivers »
make[1]: entrant dans le répertoire « /home/rabgye/alsa-driver-1.0.20/isa »
make[2]: entrant dans le répertoire « /home/rabgye/alsa-driver-1.0.20/isa/ad1816a »
make[2]: quittant le répertoire « /home/rabgye/alsa-driver-1.0.20/isa/ad1816a »
make[2]: entrant dans le répertoire « /home/rabgye/alsa-driver-1.0.20/isa/ad1848 »
make[2]: quittant le répertoire « /home/rabgye/alsa-driver-1.0.20/isa/ad1848 »
make[2]: entrant dans le répertoire « /home/rabgye/alsa-driver-1.0.20/isa/cs423x »
make[2]: quittant le répertoire « /home/rabgye/alsa-driver-1.0.20/isa/cs423x »
make[2]: entrant dans le répertoire « /home/rabgye/alsa-driver-1.0.20/isa/es1688 »
make[2]: quittant le répertoire « /home/rabgye/alsa-driver-1.0.20/isa/es1688 »
make[2]: entrant dans le répertoire « /home/rabgye/alsa-driver-1.0.20/isa/gus »
make[2]: quittant le répertoire « /home/rabgye/alsa-driver-1.0.20/isa/gus »
make[2]: entrant dans le répertoire « /home/rabgye/alsa-driver-1.0.20/isa/msnd »
make[2]: quittant le répertoire « /home/rabgye/alsa-driver-1.0.20/isa/msnd »
make[2]: entrant dans le répertoire « /home/rabgye/alsa-driver-1.0.20/isa/opti9xx »
make[2]: quittant le répertoire « /home/rabgye/alsa-driver-1.0.20/isa/opti9xx »
make[2]: entrant dans le répertoire « /home/rabgye/alsa-driver-1.0.20/isa/sb »
mkdir -p /lib/modules/2.6.28-3-rt/kernel/sound/isa/sb
cp snd-sb-common.ko snd-sb16-dsp.ko /lib/modules/2.6.28-3-rt/kernel/sound/isa/sb
make[2]: quittant le répertoire « /home/rabgye/alsa-driver-1.0.20/isa/sb »
make[2]: entrant dans le répertoire « /home/rabgye/alsa-driver-1.0.20/isa/wavefront »
make[2]: quittant le répertoire « /home/rabgye/alsa-driver-1.0.20/isa/wavefront »
make[2]: entrant dans le répertoire « /home/rabgye/alsa-driver-1.0.20/isa/wss »
make[2]: quittant le répertoire « /home/rabgye/alsa-driver-1.0.20/isa/wss »
make[1]: quittant le répertoire « /home/rabgye/alsa-driver-1.0.20/isa »
make[1]: entrant dans le répertoire « /home/rabgye/alsa-driver-1.0.20/synth »
mkdir -p /lib/modules/2.6.28-3-rt/kernel/sound/synth
cp snd-util-mem.ko /lib/modules/2.6.28-3-rt/kernel/sound/synth
make[2]: entrant dans le répertoire « /home/rabgye/alsa-driver-1.0.20/synth/emux »
mkdir -p /lib/modules/2.6.28-3-rt/kernel/sound/synth/emux
cp snd-emux-synth.ko /lib/modules/2.6.28-3-rt/kernel/sound/synth/emux
make[2]: quittant le répertoire « /home/rabgye/alsa-driver-1.0.20/synth/emux »
make[1]: quittant le répertoire « /home/rabgye/alsa-driver-1.0.20/synth »
make[1]: entrant dans le répertoire « /home/rabgye/alsa-driver-1.0.20/pci »
mkdir -p /lib/modules/2.6.28-3-rt/kernel/sound/pci
cp snd-ad1889.ko snd-als300.ko snd-als4000.ko snd-atiixp-modem.ko snd-atiixp.ko snd-azt3328.ko snd-bt87x.ko snd-cmipci.ko snd-cs4281.ko snd-cs5530.ko snd-ens1370.ko snd-ens1371.ko snd-es1938.ko snd-es1968.ko snd-fm801.ko snd-intel8x0.ko snd-intel8x0m.ko snd-maestro3.ko snd-rme32.ko snd-rme96.ko snd-sonicvibes.ko snd-via82xx-modem.ko snd-via82xx.ko /lib/modules/2.6.28-3-rt/kernel/sound/pci
make[2]: entrant dans le répertoire « /home/rabgye/alsa-driver-1.0.20/pci/ac97 »
mkdir -p /lib/modules/2.6.28-3-rt/kernel/sound/pci/ac97
cp snd-ac97-codec.ko /lib/modules/2.6.28-3-rt/kernel/sound/pci/ac97
make[2]: quittant le répertoire « /home/rabgye/alsa-driver-1.0.20/pci/ac97 »
make[2]: entrant dans le répertoire « /home/rabgye/alsa-driver-1.0.20/pci/ali5451 »
mkdir -p /lib/modules/2.6.28-3-rt/kernel/sound/pci/ali5451
cp snd-ali5451.ko /lib/modules/2.6.28-3-rt/kernel/sound/pci/ali5451
make[2]: quittant le répertoire « /home/rabgye/alsa-driver-1.0.20/pci/ali5451 »
make[2]: entrant dans le répertoire « /home/rabgye/alsa-driver-1.0.20/pci/asihpi »
mkdir -p /lib/modules/2.6.28-3-rt/kernel/sound/pci/asihpi
cp snd-asihpi.ko /lib/modules/2.6.28-3-rt/kernel/sound/pci/asihpi
make[2]: quittant le répertoire « /home/rabgye/alsa-driver-1.0.20/pci/asihpi »
make[2]: entrant dans le répertoire « /home/rabgye/alsa-driver-1.0.20/pci/au88x0 »
mkdir -p /lib/modules/2.6.28-3-rt/kernel/sound/pci/au88x0
cp snd-au8810.ko snd-au8820.ko snd-au8830.ko /lib/modules/2.6.28-3-rt/kernel/sound/pci/au88x0
make[2]: quittant le répertoire « /home/rabgye/alsa-driver-1.0.20/pci/au88x0 »
make[2]: entrant dans le répertoire « /home/rabgye/alsa-driver-1.0.20/pci/aw2 »
mkdir -p /lib/modules/2.6.28-3-rt/kernel/sound/pci/aw2
cp snd-aw2.ko /lib/modules/2.6.28-3-rt/kernel/sound/pci/aw2
make[2]: quittant le répertoire « /home/rabgye/alsa-driver-1.0.20/pci/aw2 »
make[2]: entrant dans le répertoire « /home/rabgye/alsa-driver-1.0.20/pci/ca0106 »
mkdir -p /lib/modules/2.6.28-3-rt/kernel/sound/pci/ca0106
cp snd-ca0106.ko /lib/modules/2.6.28-3-rt/kernel/sound/pci/ca0106
make[2]: quittant le répertoire « /home/rabgye/alsa-driver-1.0.20/pci/ca0106 »
make[2]: entrant dans le répertoire « /home/rabgye/alsa-driver-1.0.20/pci/cs46xx »
mkdir -p /lib/modules/2.6.28-3-rt/kernel/sound/pci/cs46xx
cp snd-cs46xx.ko /lib/modules/2.6.28-3-rt/kernel/sound/pci/cs46xx
make[2]: quittant le répertoire « /home/rabgye/alsa-driver-1.0.20/pci/cs46xx »
make[2]: entrant dans le répertoire « /home/rabgye/alsa-driver-1.0.20/pci/cs5535audio »
make[2]: quittant le répertoire « /home/rabgye/alsa-driver-1.0.20/pci/cs5535audio »
make[2]: entrant dans le répertoire « /home/rabgye/alsa-driver-1.0.20/pci/echoaudio »
mkdir -p /lib/modules/2.6.28-3-rt/kernel/sound/pci/echoaudio
cp snd-darla20.ko snd-darla24.ko snd-echo3g.ko snd-gina20.ko snd-gina24.ko snd-indigo.ko snd-indigodj.ko snd-indigodjx.ko snd-indigoio.ko snd-indigoiox.ko snd-layla20.ko snd-layla24.ko snd-mia.ko snd-mona.ko /lib/modules/2.6.28-3-rt/kernel/sound/pci/echoaudio
make[2]: quittant le répertoire « /home/rabgye/alsa-driver-1.0.20/pci/echoaudio »
make[2]: entrant dans le répertoire « /home/rabgye/alsa-driver-1.0.20/pci/emu10k1 »
mkdir -p /lib/modules/2.6.28-3-rt/kernel/sound/pci/emu10k1
cp snd-emu10k1-synth.ko snd-emu10k1.ko snd-emu10k1x.ko /lib/modules/2.6.28-3-rt/kernel/sound/pci/emu10k1
make[2]: quittant le répertoire « /home/rabgye/alsa-driver-1.0.20/pci/emu10k1 »
make[2]: entrant dans le répertoire « /home/rabgye/alsa-driver-1.0.20/pci/hda »
mkdir -p /lib/modules/2.6.28-3-rt/kernel/sound/pci/hda
cp snd-hda-codec-analog.ko snd-hda-codec-atihdmi.ko snd-hda-codec-cmedia.ko snd-hda-codec-conexant.ko snd-hda-codec-idt.ko snd-hda-codec-intelhdmi.ko snd-hda-codec-nvhdmi.ko snd-hda-codec-realtek.ko snd-hda-codec-si3054.ko snd-hda-codec-via.ko snd-hda-codec.ko snd-hda-intel.ko /lib/modules/2.6.28-3-rt/kernel/sound/pci/hda
make[2]: quittant le répertoire « /home/rabgye/alsa-driver-1.0.20/pci/hda »
make[2]: entrant dans le répertoire « /home/rabgye/alsa-driver-1.0.20/pci/ice1712 »
mkdir -p /lib/modules/2.6.28-3-rt/kernel/sound/pci/ice1712
cp snd-ice1712.ko snd-ice1724.ko snd-ice17xx-ak4xxx.ko /lib/modules/2.6.28-3-rt/kernel/sound/pci/ice1712
make[2]: quittant le répertoire « /home/rabgye/alsa-driver-1.0.20/pci/ice1712 »
make[2]: entrant dans le répertoire « /home/rabgye/alsa-driver-1.0.20/pci/korg1212 »
mkdir -p /lib/modules/2.6.28-3-rt/kernel/sound/pci/korg1212
cp snd-korg1212.ko /lib/modules/2.6.28-3-rt/kernel/sound/pci/korg1212
make[2]: quittant le répertoire « /home/rabgye/alsa-driver-1.0.20/pci/korg1212 »
make[2]: entrant dans le répertoire « /home/rabgye/alsa-driver-1.0.20/pci/mixart »
mkdir -p /lib/modules/2.6.28-3-rt/kernel/sound/pci/mixart
cp snd-mixart.ko /lib/modules/2.6.28-3-rt/kernel/sound/pci/mixart
make[2]: quittant le répertoire « /home/rabgye/alsa-driver-1.0.20/pci/mixart »
make[2]: entrant dans le répertoire « /home/rabgye/alsa-driver-1.0.20/pci/nm256 »
mkdir -p /lib/modules/2.6.28-3-rt/kernel/sound/pci/nm256
cp snd-nm256.ko /lib/modules/2.6.28-3-rt/kernel/sound/pci/nm256
make[2]: quittant le répertoire « /home/rabgye/alsa-driver-1.0.20/pci/nm256 »
make[2]: entrant dans le répertoire « /home/rabgye/alsa-driver-1.0.20/pci/oxygen »
mkdir -p /lib/modules/2.6.28-3-rt/kernel/sound/pci/oxygen
cp snd-hifier.ko snd-oxygen-lib.ko snd-oxygen.ko snd-virtuoso.ko /lib/modules/2.6.28-3-rt/kernel/sound/pci/oxygen
make[2]: quittant le répertoire « /home/rabgye/alsa-driver-1.0.20/pci/oxygen »
make[2]: entrant dans le répertoire « /home/rabgye/alsa-driver-1.0.20/pci/pcxhr »
mkdir -p /lib/modules/2.6.28-3-rt/kernel/sound/pci/pcxhr
cp snd-pcxhr.ko /lib/modules/2.6.28-3-rt/kernel/sound/pci/pcxhr
make[2]: quittant le répertoire « /home/rabgye/alsa-driver-1.0.20/pci/pcxhr »
make[2]: entrant dans le répertoire « /home/rabgye/alsa-driver-1.0.20/pci/pdplus »
mkdir -p /lib/modules/2.6.28-3-rt/kernel/sound/pci/pdplus
cp snd-pdplus.ko /lib/modules/2.6.28-3-rt/kernel/sound/pci/pdplus
make[2]: quittant le répertoire « /home/rabgye/alsa-driver-1.0.20/pci/pdplus »
make[2]: entrant dans le répertoire « /home/rabgye/alsa-driver-1.0.20/pci/riptide »
mkdir -p /lib/modules/2.6.28-3-rt/kernel/sound/pci/riptide
cp snd-riptide.ko /lib/modules/2.6.28-3-rt/kernel/sound/pci/riptide
make[2]: quittant le répertoire « /home/rabgye/alsa-driver-1.0.20/pci/riptide »
make[2]: entrant dans le répertoire « /home/rabgye/alsa-driver-1.0.20/pci/rme9652 »
mkdir -p /lib/modules/2.6.28-3-rt/kernel/sound/pci/rme9652
cp snd-hdsp.ko snd-hdspm.ko snd-rme9652.ko /lib/modules/2.6.28-3-rt/kernel/sound/pci/rme9652
make[2]: quittant le répertoire « /home/rabgye/alsa-driver-1.0.20/pci/rme9652 »
make[2]: entrant dans le répertoire « /home/rabgye/alsa-driver-1.0.20/pci/trident »
mkdir -p /lib/modules/2.6.28-3-rt/kernel/sound/pci/trident
cp snd-trident.ko /lib/modules/2.6.28-3-rt/kernel/sound/pci/trident
make[2]: quittant le répertoire « /home/rabgye/alsa-driver-1.0.20/pci/trident »
make[2]: entrant dans le répertoire « /home/rabgye/alsa-driver-1.0.20/pci/vx222 »
mkdir -p /lib/modules/2.6.28-3-rt/kernel/sound/pci/vx222
cp snd-vx222.ko /lib/modules/2.6.28-3-rt/kernel/sound/pci/vx222
make[2]: quittant le répertoire « /home/rabgye/alsa-driver-1.0.20/pci/vx222 »
make[2]: entrant dans le répertoire « /home/rabgye/alsa-driver-1.0.20/pci/ymfpci »
mkdir -p /lib/modules/2.6.28-3-rt/kernel/sound/pci/ymfpci
cp snd-ymfpci.ko /lib/modules/2.6.28-3-rt/kernel/sound/pci/ymfpci
make[2]: quittant le répertoire « /home/rabgye/alsa-driver-1.0.20/pci/ymfpci »
make[1]: quittant le répertoire « /home/rabgye/alsa-driver-1.0.20/pci »
make[1]: entrant dans le répertoire « /home/rabgye/alsa-driver-1.0.20/aoa »
make[2]: entrant dans le répertoire « /home/rabgye/alsa-driver-1.0.20/aoa/codecs »
make[2]: quittant le répertoire « /home/rabgye/alsa-driver-1.0.20/aoa/codecs »
make[2]: entrant dans le répertoire « /home/rabgye/alsa-driver-1.0.20/aoa/core »
make[2]: quittant le répertoire « /home/rabgye/alsa-driver-1.0.20/aoa/core »
make[2]: entrant dans le répertoire « /home/rabgye/alsa-driver-1.0.20/aoa/fabrics »
make[2]: quittant le répertoire « /home/rabgye/alsa-driver-1.0.20/aoa/fabrics »
make[2]: entrant dans le répertoire « /home/rabgye/alsa-driver-1.0.20/aoa/soundbus »
make[3]: entrant dans le répertoire « /home/rabgye/alsa-driver-1.0.20/aoa/soundbus/i2sbus »
make[3]: quittant le répertoire « /home/rabgye/alsa-driver-1.0.20/aoa/soundbus/i2sbus »
make[2]: quittant le répertoire « /home/rabgye/alsa-driver-1.0.20/aoa/soundbus »
make[1]: quittant le répertoire « /home/rabgye/alsa-driver-1.0.20/aoa »
make[1]: entrant dans le répertoire « /home/rabgye/alsa-driver-1.0.20/soc »
mkdir -p /lib/modules/2.6.28-3-rt/kernel/sound/soc
cp snd-soc-core.ko /lib/modules/2.6.28-3-rt/kernel/sound/soc
make[2]: entrant dans le répertoire « /home/rabgye/alsa-driver-1.0.20/soc/atmel »
make[2]: quittant le répertoire « /home/rabgye/alsa-driver-1.0.20/soc/atmel »
make[2]: entrant dans le répertoire « /home/rabgye/alsa-driver-1.0.20/soc/au1x »
make[2]: quittant le répertoire « /home/rabgye/alsa-driver-1.0.20/soc/au1x »
make[2]: entrant dans le répertoire « /home/rabgye/alsa-driver-1.0.20/soc/blackfin »
make[2]: quittant le répertoire « /home/rabgye/alsa-driver-1.0.20/soc/blackfin »
make[2]: entrant dans le répertoire « /home/rabgye/alsa-driver-1.0.20/soc/codecs »
make[2]: quittant le répertoire « /home/rabgye/alsa-driver-1.0.20/soc/codecs »
make[2]: entrant dans le répertoire « /home/rabgye/alsa-driver-1.0.20/soc/davinci »
make[2]: quittant le répertoire « /home/rabgye/alsa-driver-1.0.20/soc/davinci »
make[2]: entrant dans le répertoire « /home/rabgye/alsa-driver-1.0.20/soc/fsl »
make[2]: quittant le répertoire « /home/rabgye/alsa-driver-1.0.20/soc/fsl »
make[2]: entrant dans le répertoire « /home/rabgye/alsa-driver-1.0.20/soc/omap »
make[2]: quittant le répertoire « /home/rabgye/alsa-driver-1.0.20/soc/omap »
make[2]: entrant dans le répertoire « /home/rabgye/alsa-driver-1.0.20/soc/pxa »
make[2]: quittant le répertoire « /home/rabgye/alsa-driver-1.0.20/soc/pxa »
make[2]: entrant dans le répertoire « /home/rabgye/alsa-driver-1.0.20/soc/s3c24xx »
make[2]: quittant le répertoire « /home/rabgye/alsa-driver-1.0.20/soc/s3c24xx »
make[2]: entrant dans le répertoire « /home/rabgye/alsa-driver-1.0.20/soc/sh »
make[2]: quittant le répertoire « /home/rabgye/alsa-driver-1.0.20/soc/sh »
make[1]: quittant le répertoire « /home/rabgye/alsa-driver-1.0.20/soc »
make[1]: entrant dans le répertoire « /home/rabgye/alsa-driver-1.0.20/usb »
mkdir -p /lib/modules/2.6.28-3-rt/kernel/sound/usb
cp snd-usb-audio.ko snd-usb-lib.ko /lib/modules/2.6.28-3-rt/kernel/sound/usb
make[2]: entrant dans le répertoire « /home/rabgye/alsa-driver-1.0.20/usb/caiaq »
mkdir -p /lib/modules/2.6.28-3-rt/kernel/sound/usb/caiaq
cp snd-usb-caiaq.ko /lib/modules/2.6.28-3-rt/kernel/sound/usb/caiaq
make[2]: quittant le répertoire « /home/rabgye/alsa-driver-1.0.20/usb/caiaq »
make[2]: entrant dans le répertoire « /home/rabgye/alsa-driver-1.0.20/usb/usx2y »
mkdir -p /lib/modules/2.6.28-3-rt/kernel/sound/usb/usx2y
cp snd-usb-us122l.ko snd-usb-usx2y.ko /lib/modules/2.6.28-3-rt/kernel/sound/usb/usx2y
make[2]: quittant le répertoire « /home/rabgye/alsa-driver-1.0.20/usb/usx2y »
make[1]: quittant le répertoire « /home/rabgye/alsa-driver-1.0.20/usb »
make[1]: entrant dans le répertoire « /home/rabgye/alsa-driver-1.0.20/pcmcia »
make[2]: entrant dans le répertoire « /home/rabgye/alsa-driver-1.0.20/pcmcia/pdaudiocf »
mkdir -p /lib/modules/2.6.28-3-rt/kernel/sound/pcmcia/pdaudiocf
cp snd-pdaudiocf.ko /lib/modules/2.6.28-3-rt/kernel/sound/pcmcia/pdaudiocf
make[2]: quittant le répertoire « /home/rabgye/alsa-driver-1.0.20/pcmcia/pdaudiocf »
make[2]: entrant dans le répertoire « /home/rabgye/alsa-driver-1.0.20/pcmcia/vx »
mkdir -p /lib/modules/2.6.28-3-rt/kernel/sound/pcmcia/vx
cp snd-vxpocket.ko /lib/modules/2.6.28-3-rt/kernel/sound/pcmcia/vx
make[2]: quittant le répertoire « /home/rabgye/alsa-driver-1.0.20/pcmcia/vx »
make[1]: quittant le répertoire « /home/rabgye/alsa-driver-1.0.20/pcmcia »
make[1]: entrant dans le répertoire « /home/rabgye/alsa-driver-1.0.20/misc »
mkdir -p /lib/modules/2.6.28-3-rt/kernel/sound/misc
cp ac97_bus.ko /lib/modules/2.6.28-3-rt/kernel/sound/misc
make[1]: quittant le répertoire « /home/rabgye/alsa-driver-1.0.20/misc »
/sbin/depmod -a 2.6.28-3-rt 
cat WARNING

WARNING!!! The mixer channels for the ALSA driver are muted by default!!!
**************************************************************************
You would use some ALSA or OSS mixer to set the appropriate volume.

rabgye@ubuntumaya:~/alsa-driver-1.0.20$ 

depuis j'etais alle faire des reherches sur internet et je n'aiplus la capture posible par la carte realtekalc662suite a une commande qu'on disait etre la solution et que j'ai oubliee.plus aucun son ne marche.en pistes de mixer par defaut je n'ai plus que:
capture:monitor of simultaneous output(pulse audio mixer)
playback:simultaneous output(pulse audio mixer)
la capture par la carte realtek alc662 rev1et deux autres possibilites ont disparues.je vais essayer de retrouver la commande que j'ai tapeeet peut -etre me rendre sur alsa.org.

---

### Post by manjusri on 2009-06-29
la commande que j'avais tapee etait:
options snd-hda-intel model=auto
si tu peux m'indiquer un moyen de l'annuler.merci

---

### Post by pytheas22 on 2009-06-30
Pour annuler la commande, je pense qu'il suffira d'ouvrir le fichier /etc/modprobe.d/alsa-base et supprimer la ligne qui dit "options snd-hda-intel model=auto".  Puis il faudra probablement redémarrer l'ordinateur.

En ce qui concerne votre problème plus large, il me semble que je n'ai malheuresement plus d'idées...je ne peux rien de plus trouver sur Internet qui pourrait constituer une solution, et je n'ai plus d'idées moi-même (mais il faut préciser qu'il y a d'autres gens qui savent beaucoup plus que moi en ce qui concerne le son sur Ubuntu).  Donc je suis très désolé mais je pense qu'il faut dire que je ne peux rien de plus...

---

### Post by manjusri on 2009-07-08
bonjour pytheas;desole de te repondre si tard;j'ai reussi a annnuler la commande qui se trouvait dans /etc/modprobe.d/options;merci de m'avoir aide;je me suis inscrit sur alsa-project.org et je vais faire un rapport de bug sur le launchpad bonne continuation.manjusri

---

