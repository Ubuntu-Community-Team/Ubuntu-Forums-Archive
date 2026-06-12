---
title: "Help with martian modem package on maverick"
date: 2011-02-26
forum: Hardware
---

### Post by bartman2589 on 2011-02-26
I'm hoping someone will be able to help me with getting my Agere modem working using the martian modem package from the Ubuntu Multiverse repository.  I have tried to follow some of the guides I found when I searched, but to be honest I got confused by a lot of what was said in them, and most of them applied to older versions of linux so a lot of the information wasn't relevant anyway.  I'm hoping someone can help 'dumb it down' for me so I can get this modem working (mainly I want it for sending and receiving faxes).  I'm running Kubuntu 10.10 (Maverick) on an old AMD Athlon XP 2400+ with 1.5Gb DDR RAM and an old nVidia MX4000 128mb pci video card on an old DFI KT-600AL motherboard.  I installed the martian modem package but when I run:
```
sudo lshw -c communication
```I get:
```
  *-communication UNCLAIMED
       description: Communication controller
       product: LT WinModem
       vendor: Agere Systems
       physical id: a
       bus info: pci@0000:00:0a.0
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list
       configuration: latency=32 maxlatency=14 mingnt=252
       resources: memory:e2105000-e21050ff ioport:9000(size=8) ioport:9400(size=256)
```Unless I'm mistaken the 'UNCLAIMED' means that no driver is installed for the device, is that right?

And if I run:
```
sudo lsmod
```I get:
```
Module                  Size  Used by
nls_iso8859_1           3261  1 
nls_cp437               4931  1 
vfat                    9201  1 
fat                    48240  1 vfat
usb_storage            40172  1 
binfmt_misc             6599  1 
lirc_serial            10618  3 
lirc_dev                9393  1 lirc_serial
ipt_REJECT              2004  1 
ipt_LOG                 4490  4 
xt_limit                1394  6 
xt_tcpudp               1927  7 
ipt_addrtype            1611  4 
xt_state                1014  9 
dm_crypt               11385  0 
ip6table_filter         1275  1 
ip6_tables             11764  1 ip6table_filter
snd_cs46xx             77321  2 
nf_nat_irc              1168  0 
gameport                9327  2 snd_cs46xx
snd_ac97_codec         99227  1 snd_cs46xx
nf_conntrack_irc        3348  1 nf_nat_irc
ac97_bus                1014  1 snd_ac97_codec
nf_nat_ftp              1398  0 
nf_nat                 16289  2 nf_nat_irc,nf_nat_ftp
nouveau               517274  2 
nf_conntrack_ipv4      10783  11 nf_nat
nf_defrag_ipv4          1117  1 nf_conntrack_ipv4
snd_pcm                71475  2 snd_cs46xx,snd_ac97_codec
nf_conntrack_ftp        5361  1 nf_nat_ftp
snd_seq_midi            4588  0 
nf_conntrack           63258  7 xt_state,nf_nat_irc,nf_conntrack_irc,nf_nat_ftp,nf_nat,nf_conntrack_ipv4,nf_conntrack_ftp
snd_rawmidi            17783  2 snd_cs46xx,snd_seq_midi
iptable_filter          1302  1 
ttm                    56633  1 nouveau
ip_tables              10460  1 iptable_filter
snd_seq_midi_event      6047  1 snd_seq_midi
x_tables               15921  10 ipt_REJECT,ipt_LOG,xt_limit,xt_tcpudp,ipt_addrtype,xt_state,ip6table_filter,ip6_tables,iptable_filter,ip_tables
drm_kms_helper         30200  1 nouveau
snd_seq                47174  3 snd_seq_midi,snd_seq_midi_event
ppdev                   5556  0 
snd_timer              19067  2 snd_pcm,snd_seq
snd_seq_device          5744  3 snd_seq_midi,snd_rawmidi,snd_seq
psmouse                59033  0 
drm                   168092  4 nouveau,ttm,drm_kms_helper
serio_raw               4022  0 
parport_pc             26058  1 
via_agp                 5322  1 
snd                    49038  12 snd_cs46xx,snd_ac97_codec,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
i2c_viapro              5777  0 
soundcore                880  1 snd
shpchp                 29886  0 
i2c_algo_bit            5168  1 nouveau
agpgart                32011  3 ttm,drm,via_agp
snd_page_alloc          7120  2 snd_cs46xx,snd_pcm
lp                      7342  0 
parport                31492  3 ppdev,parport_pc,lp
raid10                 22394  0 
raid456                53514  0 
async_raid6_recov       4883  1 raid456
async_pq                3038  2 raid456,async_raid6_recov
raid6_pq               80029  2 async_raid6_recov,async_pq
async_xor               2298  3 raid456,async_raid6_recov,async_pq
xor                    15136  1 async_xor
async_memcpy            1045  2 raid456,async_raid6_recov
async_tx                2135  5 raid456,async_raid6_recov,async_pq,async_xor,async_memcpy
raid1                  20969  0 
via_rhine              19038  0 
floppy                 54311  0 
raid0                   8547  0 
mii                     4425  1 via_rhine
pata_via                7332  3 
pata_pdc2027x           5677  2 
multipath               5955  0 
linear                  3822  0 

```And if I run:
```
sudo modprobe martian_dev
```To try to get the module to load manually (as several of the articles I googled say to do), I get:
```
FATAL: Module martian_dev not found.
```And if I run:
```
sudo modprobe martian-modem
```because I see a file named martian-modem present in '/etc/default' and in '/etc/init.d' that I think is the module that's supposed to load with this version of the drivers, I get:
```
FATAL: Module martian_modem not found.
```I have located the file 'martian_modem' in '/usr/sbin' but for whatever reason it's not being found by the module 'martian-modem'.  I have also verified that as both root (using sudo and su) and regular user '/usr/sbin' is in my path (used 'echo $PATH') as well, thinking that might have been part of the problem, but apparently it's not.

I'd really like to avoid having to build a new kernel to support this device since I really have no idea how to do that and don't want to have to do it each and every time a new kernel is released.

Additionally I have to wonder why the martian modem package is being included in Maverick if it doesn't work properly 'out of the box'.  I mean isn't the whole idea of packages to make installation of software & drivers straightforward and simple requiring almost no user intervention?

So anyway at this point I'm totally confused as to what's going on, any help would be greatly appreciated.

Thanks,
bartman2589

---

### Post by bartman2589 on 2011-02-26
I should also point out that I have tried several other modems that I have laying around and have had no luck in getting any of them working (I know that not all of them use the martian modem drivers of course).

Modems I have tried (just by physically installing them in the computer):
[INDENT]2 HP/Compaq MW560CI Conexant/Rockwell chipset (have one with Conexant and one with Rockwell chipset)

2 PCTel 789T based modems (one has PCT1789 Rev 2.2 marked on it as well as having "HSP 56 MicroModem V.90/K56Flex marked on it and was made by a company called 'ONSpeed', the other is marked with 'P/N:MM9050R3.0' and has an FCC Reg code of 'M4TUSA-33142-M5-E'

1 Zoom Modem Model 2925L (Lucent HV90P-T chipset)

1 HP/Compaq Cheetah Modem (Agere 1648C-TV3 chipset)
[/INDENT]
All are PCI bus cards, and all were reported as being "UNCLAIMED" by 'lshw -c communication'.  AFIK all use fairly common chipsets (at least as far as modems are concerned) so I'm pretty disappointed that none of them were supported 'out of the box' by Maverick.

I would prefer to have either the Agere based modem or the Lucent based one working, but I would also be happy with getting either of the MW560CI modems working if I can't get either of the other 2 working.  I would rather stay away from the PCTel modems if possible because I've had extremely bad results with them in my Windows machine.

I would also prefer not having to use any of the crippled drivers from the Linmodem site because I'd like to have full 56K access just in case I ever need to use the modem for web access, not very likely to need to but still just in case.

---

### Post by bartman2589 on 2011-02-27
Anyone?

---

### Post by bartman2589 on 2011-02-28
Ok, I'm updating this with what I've managed to do so far in case someone finally decides to offer some help with this.

I think I've got the martian modem drivers partly working now after building from source using the file named 'martian-full-20100123.tar.gz' from [http://linmodems.technion.ac.il/packages/ltmodem/kernel-2.6/martian/](http://linmodems.technion.ac.il/packages/ltmodem/kernel-2.6/martian/).  The package appeared to build ok even though I received several warnings during a few of the build/install stages.  At least now when I use:
```
sudo lshw -c communication
```after a fresh boot, I get:
```
  *-communication         
       description: Communication controller
       product: LT WinModem
       vendor: Agere Systems
       physical id: a
       bus info: pci@0000:00:0a.0
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list
       configuration: driver=martian latency=32 maxlatency=14 mingnt=252
       resources: irq:17 memory:e2105000-e21050ff ioport:9000(size=8) ioport:9400(size=256)
```I'm no longer getting the 'UNCLAIMED' message so I'm guessing that means that a driver or at least a kernel module successfully loaded for it now.  However the problem I have now is that when I run:
```
sudo martian_modem
``` to start the helper that assigns a port address to the modem I get:```
martian: info: Your port is /dev/ttySM0
``` which is ok I guess, but when I try to access that port using any programs I can't do anything, it's like the port is locked, I've made sure my user account is added to the tty, fax, dip and dialout groups, but it doesn't seem to make a difference, also I need to find a way to load the martian_modem helper program during bootup without having to enter my root password every time.  As well as to figure out how to allow user access to the port that the helper app assigns to my modem.

So once again any help would be much appreciated.

---

### Post by bartman2589 on 2011-02-28
Ok, so much for that thought, I tried using the --user switch to change ownership of the tty port to my user account when I loaded the martian_modem helper app by using su in a console, only to have it crash saying "Segmentation fault" when I tried to access it with cutecom (for testing purposes).  Not sure if this is related to the warnings I received when I built the modules or not, I don't really have anymore ideas what I can do to get this working now.

Once again some help would be greatly appreciated!!  After all this is a support forum isn't it??

---

### Post by bartman2589 on 2011-02-28
In the hopes that someone might be able to help me figure out what's going wrong with my attempts to build the modules from source here's the results of running 'make':```
make -C kmodule/ modules
make[1]: Entering directory `/home/user/Downloads/Martian/kmodule'
make -C /lib/modules/2.6.35-25-generic/build M="/home/user/Downloads/Martian/kmodule"  modules
make[2]: Entering directory `/usr/src/linux-headers-2.6.35-25-generic'
  CC [M]  /home/user/Downloads/Martian/kmodule/martian.o
/home/user/Downloads/Martian/kmodule/martian.c: In function ‘martian_isr’:
/home/user/Downloads/Martian/kmodule/martian.c:135: warning: value computed is not used
  CC [M]  /home/user/Downloads/Martian/kmodule/marsio.o
/home/user/Downloads/Martian/kmodule/marsio.c:358: warning: ‘mars_read_register_rem’ defined but not used
/home/user/Downloads/Martian/kmodule/marsio.c:371: warning: ‘mars_write_register_rem’ defined but not used
In file included from /usr/src/linux-headers-2.6.35-25-generic/arch/x86/include/asm/uaccess.h:571,
                 from /home/user/Downloads/Martian/kmodule/marsio.c:2:
In function ‘copy_from_user’,
    inlined from ‘mars_download_dsp_user’ at /home/user/Downloads/Martian/kmodule/marsio.c:767:
/usr/src/linux-headers-2.6.35-25-generic/arch/x86/include/asm/uaccess_32.h:212: warning: call to ‘copy_from_user_overflow’ declared with attribute warning: copy_from_user() buffer size is not provably correct
  CC [M]  /home/user/Downloads/Martian/kmodule/mfifo.o
  LD [M]  /home/user/Downloads/Martian/kmodule/martian_dev.o
  Building modules, stage 2.
  MODPOST 1 modules
  CC      /home/user/Downloads/Martian/kmodule/martian_dev.mod.o
  LD [M]  /home/user/Downloads/Martian/kmodule/martian_dev.ko
make[2]: Leaving directory `/usr/src/linux-headers-2.6.35-25-generic'
make[1]: Leaving directory `/home/user/Downloads/Martian/kmodule'
make -C modem/ all
make[1]: Entering directory `/home/user/Downloads/Martian/modem'
    CC    main.o
    CC    dumpers.o
    CC    log.o
    CC    session.o
    CC    mport.o
    CC    pty.o
    CC    sysdep.o
    CC    isr.o
    CC    smp.o
    CC    core_if.o
    CC    coresubst.o
    CC    link.o
    CC    tweakrelocsdynamic.o
    CC    coreadd.o
    CC    elf386tweakrelocs
    LD    marscore.o
    TWEAK    marscore.o
    LD    martian_modem
make[1]: Leaving directory `/home/user/Downloads/Martian/modem'
```and here is the results of running 'sudo make install' (as near as I can tell this part looks ok):```
make -C kmodule/ install
make[1]: Entering directory `/home/user/Downloads/Martian/kmodule'
make -C /lib/modules/2.6.35-25-generic/build M="/home/user/Downloads/Martian/kmodule" modules_install
make[2]: Entering directory `/usr/src/linux-headers-2.6.35-25-generic'
  INSTALL /home/user/Downloads/Martian/kmodule/martian_dev.ko
  DEPMOD  2.6.35-25-generic
make[2]: Leaving directory `/usr/src/linux-headers-2.6.35-25-generic'
if ! /sbin/modprobe -nq martian_dev ; then /sbin/depmod -a; fi
make[1]: Leaving directory `/home/user/Downloads/Martian/kmodule'
make -C modem/ install
make[1]: Entering directory `/home/user/Downloads/Martian/modem'
    LD    martian_modem.debug
    STRIP    martian_modem.debug
    STRIP    martian_modem.stripped
    INSTALL    /usr/sbin/martian_modem
    INSTALL    /usr/lib/debug/usr/sbin/martian_modem.debug
make[1]: Leaving directory `/home/user/Downloads/Martian/modem'
```I didn't put the output from running 'make clean' because as far as I know that's used to cleanup previous build attempts in order to avoid contaminating the current build attempt, I may be mistaken of course since I really have no idea of how to compile programs from a command line on my own, I generally use the instructions included in the INSTALL or README file if present, so for all I know I might be doing something seriously wrong here.

Anyway again, any help is appreciated.

---

### Post by bartman2589 on 2011-03-01
bump

Can't anyone help?

---

### Post by bartman2589 on 2011-03-08
Anyone?

---

### Post by mastablasta on 2011-03-08
uf, modems.... the reason i gave up on redhat all those years back.
are they actually winmodems that they need martian modem package?  perhaps you could try one that attaches via serial cable.
 
there seem to be two packages for this: 
[http://packages.debian.org/stable/net/martian-modem-source](http://packages.debian.org/stable/net/martian-modem-source)
 
i bet you already read this one:
[http://ubuntuforums.org/showthread.php?t=328050](http://ubuntuforums.org/showthread.php?t=328050)

---

### Post by bartman2589 on 2011-03-08
An External modem is not really an option since I don't have one.  All of the modems I do have are considered 'Winmodems' though are not actually the 'Winmodem' brand of controllerless modem.  The martian modem packages supplied with Ubuntu/Kubuntu Maverick are broken, they do not take into account the new folder structure introduced with one of the previous versions.  That's why I've been trying to get the newest 2010 modules from the martian modem page at linmodems.org to work building them from source.  Also the thread you linked to is too old, it also does not take into account the new folder structure introduced within the last couple years.  Thanks anyway.

---

### Post by peyre on 2011-03-11
Sorry about the delay, bartman.  I've just finally gotten my own Agere winmodem working (permanently, I hope) on my Tecra 8100.  Unfortunately I'm not savvy enough to dumb this down for you though; I just did some reading online, then tinkered with it until I got it to work.  (Then I had to tinker with it some more to get it to work again, but it seems to be working reliably now.)  I'm not sure exactly what I did and exactly what was necessary and what wasn't.  But here's what I wrote down when I had it done.

(This was in Lubuntu 10.04.)

I installed **KPPP**, **martian-modem**, and **martian-modem-source**. 
I also installed **gnome-ppp**, but it was useless: it kept hanging when I tried to detect the modem.  I eventually removed it altogether.

I ran **sudo martian_modem**, which I think started martian running.
At one point I ran **sudo m-a a-i martian-modem** (which built martian) and **sudo m-a -f get martian-modem**.  At some point in here, something told me what device the modem was assigned to: **/dev/ttySM0**.  (Apparently, ttyS**_M_**x is how martian assigns ports.)

At another point I ran **sudo apt-get update** and **sudo apt-get -s install linux-kernel-devel**.  At yet another point I ran **sudo apt-get install module-assistant**.

At the end, I installed hwinfo, which I think installs the Hardware Drivers utility (installed on Ubuntu and Xubuntu by default) that controls third-party and proprietary drivers.  When I ran that utility, I saw my modem in there and active, as the Agere 164x dsp driver.

KPPP doesn't have an option for /dev/ttySM0, so I linked it to /dev/modem:
  sudo ln -s /dev/ttySM0 /dev/modem

I was now able to select /dev/modem and get KPPP to recognize it.  Woohoo!

---------------------------

After that initial success, I was never able to get the modem working, so I brought did some more messing with it.  In the end, I found that in order to use the modem, I needed a script on the Desktop which reads as follows:
```

gksudo martian_modem
gksudo ln -s /dev/ttySM0 /dev/modem
/usr/bin/kppp
```

The last line, of course, brings up KPPP--both to save me a step and to keep me from opening KPPP prematurely.  If I want to dial out, I just double-click on the icon, and it gets the modem ready and opens the dial utility for me to use--slick.

---

### Post by SoConfused on 2011-03-12
You are not alone out there.  Our stories are very similar.  I tried a Modem with a Conexant chip and another with PcTel but no luck. So now I am also trying to get my Agere PCI modem to work in Ubuntu 10.10 - I also want to use the modem for faxes and once I can then I want to control it with Hylafax and Avantfax to get the fax to/from email from any web browser.  I stumbled in the darkness and also tripped over the 2010 martian-full download which did build for me too whereas the 2008 version did not.  I followed the instructions to edit the wv.conf file and I used the one in the scripts directory - but no luck.  When I start wvdial, it says it doesn't see the ttySM0 device and immediately reports a segmentation fault.  So - if I stumble on success I will report here with details and I would be grateful if you would do the same.  Thanks and Good Luck

---

