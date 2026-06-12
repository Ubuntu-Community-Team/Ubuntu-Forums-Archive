---
title: "HP Compaq 615 laptop problems"
date: 2009-11-15
forum: Hardware
---

### Post by force317 on 2009-11-15
HP Notebook 615 AthlonQL-64 1GB 160GB DVD+/-RW 15.6"
Sound : HP Premier Sound - High Definition Audio 24 Bit Audio DAC
Graphics card : ATI Radeon HD 3200

I received this Compaq 615 laptop I ordered last saturday. I bought it with just FREEDOS installed. I intended to install Ubuntu 9.10 on it. Tried the 32 bit Desktop/Live CD and the 32 bit Alernate CD, even the 64 bit Desktop CD, but installation just doesn't start, when I click on 'installation' or even on 'try Ubuntu without installing' the cd stop running after a few seconds and that's it. No installation possible.

I tried openSUSE 11.2, same problem.

The only install that worked was Linux Mint 7 in 'Compatibility Mode', but then I have no sound !

I read about the sound problems with the Compaq 615, but still, normally I should be able to install it !

It seems this laptop is still too new and so lacking support in Linux ?
Could this be the reason ? I don't understand why it just doesn't start installing ... .

---

### Post by nixscripter on 2009-11-18
The problem might be that the live CDs don't have a driver for the bus the CD-ROM drive is on. If there is a BIOS mode on the bus, for example, try changing it from AHCI to ATA.

Also, have you tried the Knoppix Live CD?

[http://www.knoppix.org/](http://www.knoppix.org/)

It's got a lot more drivers.

---

### Post by force317 on 2009-11-21
I will try Knoppix. There is a new distro just out.

Already tried the new openSUSE en Sidux, Xubuntu 9.10 and the latest simplyMEPIS.

SimplyMEPIS might work too - tried it in Sun VirtualBox - but they use
an older kernel version. I thought that was the problem :the recent kernel version.

But Knoppix is certainly a good idea.I will try it.

---

### Post by force317 on 2009-11-21
Just chequed the BIOS.

The SATA configuration can ony be changed from AHCI to IDE.

I did this.

---

### Post by nixscripter on 2009-11-21
That sounds like the right BIOS flag. Hopefully, it will work.

Good luck.

---

### Post by force317 on 2009-11-21
While Knoppix is downloading, I tried again with the Ubuntu 9.10 Live CD, no luck however. Same as before.

But isn't the SATA configuration rather about the hard disk than about the CD ROM, or does the BIOS setting I changed work for the entre system ?

---

### Post by force317 on 2009-11-21
Unfortunately ... same resut with Knoppix 6.2.

No install possible ... .

---

### Post by nixscripter on 2009-11-21
It depends on how your computer is set up. I was assuming that, since it's a laptop, the CD and the hard drive are both on the same SATA bus. Changing it to IDE compatibility mode would affect both.

Try Knoppix, but add "failsafe" and "debug" to the boot options.

[http://www.knoppix.net/wiki/Cheat_Codes](http://www.knoppix.net/wiki/Cheat_Codes)

---

### Post by sengst on 2009-11-22
Try the nolapic option of the boot cd, worked for me (see [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/454268](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/454268))

---

### Post by mastablasta on 2009-11-25
I too am interested in this notebook due to it's price. I tried Ubuntu Live 9.10 on my desktop and liked it, so i intend to install it on a new notebook i plan to buy.

I am specificall interested in 
**HP Compaq 615 RM74 NX568** and **HP Compaq 615 RM76 VC289**

It appears the difference is only the watter resistant keyboard on the expencive version.

As i read on the internet there is practicaly no issues (appart from a bit of tinkering to get the sound working) when installing (k)Ubuntu 9.04. However i see there are issues with the latest Ubuntu, which i intended to use on the computer. 

What i am interested is if these commands noapic and nolapic solve a problem specified above on any of these two particular models? And also is this a problem in running the linux on them or just when installing it? Is the probelm also showing when trying to install the 32 bit version?

-----

Another notebook that caught my attention is the following one:
Asus PRO5DAB-SX092L
with ATI Mobility Radeon X4570HD 512 MB VRAM

I can not find any information on the internet on wheather linux is working on it out of the box. 

Another option i found is an intel/nvidia notebook:
Asus K50IN-SX003L
nVIDIA GeForce G102M, 512 MB
But again i found some information on compatibility with K50IN but i am unsure if it would be working out of the box with this particular model. Any opinions or experience with these two notebooks?

---

### Post by force317 on 2009-11-28
Editing / modifiing the boot options is something I've never done before.

How do you do that in Knoppix and/or Ubuntu ?

How do I add "failsafe" and "debug" to the boot options in Knoppix ? Must I still 
change the BIOS setting for the SATA configuration from AHCI to IDE ?

And the nolapic option of the boot cd ? How do I enter that ?

Sorry, but making changes to the boot options is new to me !

---

### Post by force317 on 2009-11-28
Tried several boot options (F6) this afternoon with Ubuntu 9.10 :
nothing works ...

With Knoppix : he doesn't even finisch the startup process, then the CD stops ... .

So ... again ... the only remaining choice that works for this Laptop
is Linux Mint 7 and Linux Mint 8 RC1. So that's the one I will be using on
this laptop. Not a bad choice anyway, far from it !

The one installed until Linux Mint 8 is released is Linux Mint 7. After
installing and compiling the latest alsa sound driver ( is necessary, otherwise no sound ) and the commercial graphics card driver ( in the second highest setting, that one works best ) it's an excellent cost effective laptop.

---

### Post by nixscripter on 2009-11-28
Glad to hear you found something that worked. If you got the Linux Mint CD working, I actually think you could install Ubuntu from it if you really were attached to it. If you save the image as an ISO file, you could mount it on a loopback device, and run the installer from there.

If you are satisfied, don't forget to mark this thread as solved (under the Thread Tools menu).

---

### Post by force317 on 2009-11-29
Can't say I am satisfied, certainly for the future.

Just tried to install Linux Mint 8 that was released yesterday : it doesn`t work ! The same problem as all the other recent distros. 

Not an immediate problem but one day support for Ubuntu 9.04 / Mint 7 will stop, and if there is no alternative by then. Moreover I must confess I like to test the most recent Linux distros. I first try them out on my 3 1/2 years old MSI notebook, to install it then on this recently bought Compaq 615 for daily use. But if this Compaq 615 isn't even capable of starting to install anything recent ... there is no point !

Are there other recent laptop models with installation problems? If that is the case, it's a question of finding out what they have in common.

---

### Post by mastablasta on 2009-11-29
hey force317, not trying to steal the thread or anything, bu ti am also interested in buying this laptop due to it's price and because i read that linux ver. 9.04 works on it.

Could you tell specifically which version your computer is (full model description). I checked on HP site and it appears there are a lot of Compaq 615 versions.

---

### Post by force317 on 2009-11-30
Mastablasta, here are the specifications of my Compaq 615 :


HP Notebook 615 AthlonQL-64 1GB 160GB DVD+/-RW 15.6"

Prozessor AMD Athlon 64 X2 QL-64 2x 2,10 GHz
Cache 	1 MB
Arbeitsspeicher
Größe 	1 GB
Technologie 	DDR2 SDRAM
max. Erweiterung auf 	4096 MB
Verbaut 	2 von 2 Modulen
Formfaktor 	SODIMM 200-Polig
Grafik
Grafikkarte 	ATI Radeon HD 3200
Speicher 	max. 512 MB TurboCache
VGA-Ausgang 	ja
Festplatte
Anzahl 	1
Kapazität 	160 GB
Laufwerk
  	DVD Super Multi Brenner (Double Layer) DVD DL±RW/CDRW
Display
  	15,6 1366 x 768 Pixel (WXGA TFT)
Besonderheit 	High Definition BrightView Widescreen
Webcam 	1.3 Megapixel
Schnittstellen
Card Reader 	3in1 (MMC/SD/Memory Stick)
ExpressCard-Slot 	ja
USB 2.0 	3x
56K Modem 	ja
Bluetooth 	ja
Webcam 	ja
Kommunikation
Ethernet LAN 	100 MBit/s
Wireless Lan 	WLAN 802.11g, WLAN 802.11b, WLAN 802.11a
Sound
Chipsatz 	HP Premier Sound - High Definition Audio 24 Bit Audio DAC
Mikrofon-in 	ja
Kopfhörer-out 	ja
Ausstattung
Kensington- Schloss Buchse 	ja
Office 2007 Ready 	ja
  	 
Garantie
Collect & Return Service vom Hersteller 	24 Monate
Betriebssystem/Software
Betriebssystem 	Freedos
Notebookeigenschaften
Abmessungen 	BxHxT 37,18 x 25,43 x 3,20 cm (vorne) (mm)
Akkulaufzeit 	bis zu 4 Stunden
Gewicht 	2.49 kg

By the way, I have been following up on some of thelinks posted about the Compaq 615 problems with Ubuntu 9.10. It seems to be a kernel version problem. Some have actually found a solution to the problem.

If I can make mine work with the latest version of Ubuntu, I will post it here. The laptop is certainly worth the effort ! For the moment I am running Linux Mint 7, but I'm certain that anything with a older kernel version than 2.6.3X will work !

Look at the link below : [http://bbs.archlinux.org/viewtopic.php?id=82052]("http://bbs.archlinux.org/viewtopic.php?id=82052")

---

### Post by mastablasta on 2009-11-30
Oh this is a very different model than we had here. well at least in some components that is.


Rats! it seems they don't sell the cheaper version of this model anymore here. :-( only the more expencive one with some protection on keyboard. now tzhey only have a 470 EUR version. But they seem to have a better components in Asus PRO5DAB-SX092L for 499 EUR with 4GB ram, 320 GB disk and 512 MB ATI Mobility Radeon X4570HD


Still i am very interested in the solution, because amybe i will still go for the HP one if Linux can be installed on it with no problems (or with that workarround).

---

### Post by force317 on 2009-11-30
There seems to be a way to solve the problem with installing Ubuntu 9.10 (or any other linux distro using kernel 2.6.3X or later) on the Compaq 615 (and other laptops)

[COLOR="Red"]It is explained here[/COLOR] : [http://bbs.archlinux.org/viewtopic.php?id=82052]("http://bbs.archlinux.org/viewtopic.php?id=82052")

The explanation about the Compaq 615 is on the latest entry.

It is also mentioned here : [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/454268]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/454268")

I understand how to activate the 'acpi=off' option : on the main Ubuntu menu you choose **F6**, put an X before 'acpi=off' with **enter** button, then click on **ESC**. But the rest of the explanation ... . Could somebody please post here a more detailed explanation of what you have to do to make you installation CD actually start up please ? :D

I think quite a few people with installation problems (with AMD chipset ?) will be helped with this. :p

Hopefully in a later kernel version this problem will be solved without need for all this manual editing, but for now it would be helpfull to have a detailed explanation how to fix this bug.

---

### Post by damirje on 2009-12-11
I have also Compaq 615 - Turion X2 and ATI VGA (with FreeDOS).
I tried to install Ubuntu 9.10 UNR i386 (amd64 version can't find) from CD with wubi.exe.
After partitioning, during copying files, installation stopped on 53 %. I done it again with another CD installation.
After that, I tried same installation from USB flash (created bootable with Unetbootin), and during copying files installation stopped also on 53 %.

On that notebook I left 50 GB free space for Ubuntu installation. I create swap and ext4 partition during installation.
Win 7 x64 works fine on same PC.

Any idea and help, please???
Maybe, boot loader (grub) can't install on first (system partition), where is FreeDOS.

Thanx

---

### Post by damirje on 2009-12-15
SOLVED!
Installed ubuntu9.10-karmic-amd64 and solved.

---

### Post by force317 on 2009-12-16
I installed Linux Mint 8 x64 64bit on it today in compatibility mode.
Everything works fine !

The wireless needs the commercial drivers and the commercial graphics driver also works in 3D and the highest setting ! Even the sound works immediately !

So ; solved !

---

### Post by kristian.kroflin on 2009-12-18
Did you try to install from a USB-stick ([http://www.pendrivelinux.com/create-a-xubuntu-9-10-flash-drive-using-windows/)?](http://www.pendrivelinux.com/create-a-xubuntu-9-10-flash-drive-using-windows/)?) I have the same Laptop as you and it works fine. 
I hope you have some access to a computer using Windows, or to some Linux using Wine.

---

### Post by colourful-leaves on 2010-01-20
Hallo @ all

Ich hatte die gleichen Probleme !!!

Nach dem mich das Notebook 1 Woche genervt hatte, ist mir eingefallen das ich die gleichen Probleme vor Jahren mit einem Fujtsu-Siemens auch schon hatte.
Bei dem Amilo M mit einer verbauten Fujitsu-Siemens lies sich auch kein Linux installieren.
Erst als ich die von Siemens verbaute Festplatte, durch eine Hitachi ersetzt habe, ging die Installation problemlos.

Als erstes müßt ihr euch von der Webseite von HP das Bios-update holen. "sp46875.exe"
ROM-Image für HP Notebook-System-BIOS (68GVV) Remote-ROM-Flash – für den Einsatz mit SSM

[http://h20000.www2.hp.com/bizsupport/Tec…EnvOID=1093#120](http://h20000.www2.hp.com/bizsupport/Tec…EnvOID=1093#120)

Bootfähigen USB-Stick mit dem Bios-update sp46875.exe starten und das Bios Updaten.

Nach dem mich die Kiste immer noch angezick hat, habe ich die 160GB Seagate Festplatte ausgebaut und durch meine 500GB Externe-Festplatte ersetzt.

Danach habe ich Ubuntu 9.10, amd 64 Installiert.
Und was soll ich sage, es hat geklappt.

Nach der Installation, habe ich erst ein Update durchgeführt und einen "reboot" gemacht.
Nächter schritt war, ich habe nur für den Kernel ein "dist-upgrade" durgeführt.
Wieder "reboot"
Danach habe ich die "sources.list" durch meine ersetzt:

#deb cdrom:[Ubuntu 9.10 _Karmic Koala_ - Release amd64 (20091027)]/ karmic main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.


## kermic
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) karmic main restricted universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) karmic main restricted universe multiverse

## karmic-backports
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) karmic-backports main restricted universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) karmic-backports main restricted universe multiverse

## karmic-proposed
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) karmic-proposed main restricted universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) karmic-proposed main restricted universe multiverse

## karmic-updates
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) karmic-updates main restricted universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) karmic-updates main restricted universe multiverse

## karmic-security
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) karmic-security main restricted universe multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) karmic-security main restricted universe multiverse

## partner
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) karmic partner
deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) karmic partner

## medibuntu
deb [http://packages.medibuntu.org/](http://packages.medibuntu.org/) karmic free non-free

Hoffen und Beten:

Vorletzter schritt war:

apt-get -y update && apt-get -y dist-upgrade

und

reboot

Und zu letzt habe ich den Grafik und W-Lan Treiber installiert.
ATI/AMD FGLRX-Grafiktreiber und Broadcom-STA-Funk-Lan-Treiber

Als Software für die Cam habe ich " cheese" und "guvcview" installiert.

Die Kiste läuft seither ohne Probleme.

Ich hoffe ich konnte helfen.

mfg
Richy-Wishbone

---

