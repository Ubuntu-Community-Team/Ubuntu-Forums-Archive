---
title: "[SOLVED] Dual boot with Vista Linux distro recommendations"
date: 2008-08-19
forum: General Help
---

### Post by Yezinki on 2008-08-19
Hi there,

Let me make things simple........I want to dual boot Vista 32 bit with some version of Linux / Unix OS.

Please recommend........Open SuSE 11, Fedora 9, Ubuntu etc etc 32 bit or 64 bit??

My desktop is Sony Vaio VGC-LS1.

Lap top Dell XPS 1710.

Hoping to hear your recommendations,

Thanks in advance!

---

### Post by mb_webguy on 2008-08-19
I'm not exactly sure what your topic has to do with your post, but ok...

I'd suggest Ubuntu, if only because it has the largest user base and support structure.  It also focuses on usability, which has always been a weakness of Linux.  The current release is 8.04.1 (Hardy Heron), which is a Long Term Support release, meaning it will be supported until April 2011.  However, the next version, 8.10 (Intrepid Ibex), will be released at the end of next month, and will have a number of improvements over 8.04, including a greater focus on mobile computing and connectivity (which means good things for your laptop.  You can, of course, upgrade from Hardy to Intrepid if you choose to install 8.04.1 now.

As for 32-bit versus 64-bit, it really depends on how you use your computer.  Not many consumer applications take full advantage of 64-bit computing at this point, and some software is not currently available for 64-bit systems, particularly some web browser plugins.  If you're going to use the computer for general computing (i.e. web browsing, word processing and other office uses, etc.), you might therefore consider installing the 32-bit version, since more software will be compatible with your system.  On the other hand, a 64-bit system will provide better performance for tasks like compiling programs or encoding audio and video, so if you're a programmer or work with multimedia, you definitely want to go with a 64-bit system.

---

### Post by thestig_992 on 2008-08-19
lol to asking about what linux to use in an ubuntu forum....
I think that you should explain what you want your computer for first, because most linux OSs are quite different...maybe do a google search to find what each OS is good at...

ubuntu is deffinitly good for useability though, and is good if your a begginer or an advanced user

---

### Post by prshah on 2008-08-19
> **Yezinki said:**
> 
Let me make things simple.. I want to dual boot Vista 32 bit with some version of Linux / Unix OS.
My desktop is Sony Vaio VGC-LS1.
Lap top Dell XPS 1710.


I'd stick to 32 bit. 

Considering that this is a media-center oriented desktop; you should get your hands on either MythBuntu, LMCE or similar HTPC oriented linuxes. I highly suggest MythBuntu 8.04.

For your laptop, you can use Kubuntu (KDE4) if you like the Vista interface, or switch over to Ubuntu if you'd like something different.

OpenSUSE 11 is also very good; the live CD runs far better and smoother on my desktop than the Ubuntu Hardy Heron CD; ntfs partitions, bluetooth, etc all work better.

---

### Post by thumper13 on 2008-08-19
Here's my 2 cents.

I have tried each of the distros you mentioned, and my suggestion is to get Ubuntu if you're a beginner in linux.

I had some problems in the other distro's as far as hardware compatibility goes, and I find that for some reason, Ubuntu runs on just about anything. (Ubuntu on a toaster? that would be neat.)

Don't get me wrong, OpenSUSE and Fedora are great, I just find myself always coming back to Ubuntu in the end.

As far as Kubuntu vs. Ubuntu vs. Xubuntu and etc. are concerned, I'd check to see what GUI they use. For example, Kubuntu = KDE, Ubuntu = Gnome and Xubuntu = Xfce. Most of the commands in terminal are the same (there are subtle differences) but its like comparing different types of apples, not apples to oranges. It doesnt matter if you like green or red apples, they're still apples.

There are topics on Wikipedia as far as Xfce, Gnome and KDE go, complete with screenshots, so you can look and see what you like.. I personally prefer Gnome, others prefer different ones, but in the end, it's what YOU like. Aside from that, if you install say, Ubuntu and decide in a week you want to give KDE, Xfce, etc. a try, you can always install it (even if you have no idea how to operate linux) using the Package Manager.

Another thing I'd like to point out is that software specific to one gui isn't limited to JUST that gui. for example, I run gnome, but I prefer amaroK to listen to music (amaroK is a program that comes with KDE, similar to media player). I look it up, and next thing you know, I have amarok.

Just remember, Rome wasn't built in a day, and you won't learn Linux in a day, so don't get discouraged, if you have a problem post it in the forums, the people in these forums will be all over it very quickly.

Thumper.

---

### Post by Yezinki on 2008-08-19
Thanks prshahv!

I highly appreciate your recommendations about MythBuntu.

A few queries:

1. How can I exactly know the specs/ make, type of the built in TV tuner board in my Sony....using which software?

2. Can I install MythBuntu on both?

3. How different is it from Ubuntu hardy or Kbuntu?

4. Can I use my Cam online with MythBuntu?

5. Does it have yahoo messanger or pidgin?

6. I am not impressed at all using cheese or camorama.

7. Using Ubuntu/Kbuntu/MythBuntu what command can I use to perform a low level format of my drive?

8. Would MythBuntu allow me to take snap shots of windows & itself for burning it later on to an optical media for a back up......like Acronis True Image?

9. Would it have all the driers needed?

10. Does it get auto updates?

11. Lastly why do you prefer Kbuntu & Open SuSe over Ubuntu hardy ?

Thanks again,

Hoping to hear from a genius!!

---

### Post by Yezinki on 2008-08-19
Thanks thumper13,

One question:

Can Ubuntu, Kbuntu & MythBuntus's different features like KDE, GENOME, MCE be integrated & make one customized Ubuntu??

Hoping to hear your views!

---

### Post by Sycron on 2008-08-19
AFAIK , yes, you can. :)

---

### Post by Yezinki on 2008-08-19
Just to add:

1. I have a External USB Logitech laser comfort KB + mouse on my Dell lap top & external webcam (not integrated one) Quick cam Pro 9000 & built in BT 3.55 module.

2. On My Sony the KB & mouse are infra red & Ubuntu is running fine with them.

---

### Post by Yezinki on 2008-08-19
> **Yezinki said:**
> Thanks thumper13,

One question:

Can Ubuntu, Kbuntu & MythBuntus's different features like KDE, GENOME, MCE be integrated & make one customized Ubuntu??

Hoping to hear your views!


Hi Sycron,

How can one do that, kindly elaborate?

Thanks!

---

### Post by Sycron on 2008-08-19
If you want to have for example GNOME and KDE on ubuntu at the same time you can do that by installing them.

If you have gnome and you wish to install KDE try with this.
```
$ sudo aptitude update && sudo aptitude install kubuntu-desktop
```

Or if you have KDE and want gnome try this:
```
$ sudo aptitude update && sudo aptitude install ubuntu-desktop
```

---

### Post by Yezinki on 2008-08-19
```
ubuntu@ubuntu-desktop:~$ sudo aptitude update && sudo aptitude install kubuntu-desktop
[sudo] password for ubuntu: 
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy Release.gpg                              
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/main Translation-en_US                   
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security Release.gpg
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/main Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/universe Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/multiverse Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/restricted Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/universe Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/multiverse Translation-en_US
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security Release
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/main Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/restricted Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/main Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/restricted Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/universe Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/universe Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/multiverse Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/multiverse Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates Release.gpg
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/main Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/universe Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/multiverse Translation-en_US
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy Release
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates Release
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/universe Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/universe Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/multiverse Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/multiverse Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/universe Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/universe Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/multiverse Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/multiverse Sources
Reading package lists... Done
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Initializing package states... Done
Writing extended state information... Done
Building tag database... Done             
The following packages are unused and will be REMOVED:
  2vcard 3270-common 
The following NEW packages will be automatically installed:
  adept adept-batch adept-common adept-installer adept-manager 
  adept-notifier adept-updater akregator amarok-xine cryptsetup debtags 
  dmsetup enscript exiv2 gnupg-agent gpgsm gtk2-engines-qtcurve 
  ijsgutenprint imagemagick k3b kaddressbook kamera kdebase-bin 
  kdebase-bin-kde3 kdebase-data kdelibs-data kdelibs4c2a 
  kdemultimedia-kio-plugins kdepim-kio-plugins kdepim-kresources kdesktop 
  kdesudo kfind kicker kipi-plugins kmail kmplayer-base knode konqueror 
  konqueror-nsplugins konsole kooka korganizer kpersonalizer kregexpeditor 
  kscreensaver-xsavers ksysguardd libakode2 libarts1-akode libarts1c2a 
  libartsc0 libaudio2 libavahi-qt3-1 libavcodec1d libavutil1d libc6-dev 
  libclucene0ldbl libdbus-qt-1-1c2 libept0 libexiv2-2 libfftw3-3 libflac++6 
  libgmp3c2 libgsm1 libifp4 libijs-0.35 libiso9660-5 libjpeg-progs libk3b2 
  libkbluetooth0 libkcal2b libkcddb1 libkdcraw3 libkdepim1a libkexiv2-3 
  libkipi0 libkleopatra1 libkmime2 libkonq4 libkpimexchange1 
  libkpimidentities1 libksba8 libkscan1 libksieve0 libktnef1 liblua50 
  liblualib50 libmad0 libmimelib1c2a libmodplug0c2 libmpcdec3 
  libmysqlclient15off libnjb5 libofa0 libpoppler-qt2 libpostproc1d libpq5 
  libpythonize0 libqt-perl libqt3-mt libqt4-core libqt4-gui 
  libqt4-qt3support libqt4-sql librsync1 libruby1.8 libsearchclient0 
  libskim0 libsmokeqt1 libstreamanalyzer0 libstreams0 libstrigihtmlgui0 
  libtunepimp5 libvcdinfo0 libxapian15 libxcb-shape0 libxcb-shm0 libxcb-xv0 
  libxine1 libxine1-bin libxine1-console libxine1-ffmpeg 
  libxine1-misc-plugins libxine1-plugins libxine1-x libxvmc1 linux-libc-dev 
  mpg123 mysql-common ncompress network-manager-openvpn 
  network-manager-pptp network-manager-vpnc networkstatus ocrad 
  openoffice.org-style-crystal openvpn openvpn-blacklist oss-compat 
  p7zip-full perl-suid pinentry-curses pinentry-qt pmount poster postfix 
  pptp-linux procmail pykdeextensions python-dev python-kde3 
  python-pylibacl python-pyxattr python-qt3 python-qt4 python-qt4-common 
  python-qt4-dbus python-reportlab python-sip4 python2.5-dev qt4-qtconfig 
  rdiff-backup resolvconf ruby ruby1.8 sane-utils ttf-dustin vcdimager vpnc 
  zoo 
The following NEW packages will be installed:
  adept adept-batch adept-common adept-installer adept-manager 
  adept-notifier adept-updater akregator amarok amarok-xine apport-qt ark 
  arts cryptsetup debtags desktop-effects-kde digikam dmsetup dolphin 
  enscript exiv2 foomatic-db-gutenprint gdebi-kde gnupg-agent gpgsm 
  gtk-qt-engine gtk2-engines-qtcurve gwenview hpijs-ppds hplip-gui 
  ijsgutenprint imagemagick jockey-kde k3b kaddressbook kaffeine kamera 
  karm katapult kate kbstate kcontrol kcron kde-guidance 
  kde-guidance-powermanager kde-icons-mono kde-style-qtcurve 
  kde-systemsettings kdeadmin-kfile-plugins kdebase-bin kdebase-bin-kde3 
  kdebase-data kdebase-kio-plugins kdebluetooth kdegraphics-kfile-plugins 
  kdelibs-data kdelibs4c2a kdemultimedia-kfile-plugins 
  kdemultimedia-kio-plugins kdenetwork-filesharing kdenetwork-kfile-plugins 
  kdepasswd kdepim-kio-plugins kdepim-kresources kdepim-wizards kdeprint 
  kdesktop kdesudo kdm kdnssd keep kfind kghostview khelpcenter kicker 
  kio-apt kio-locate kio-umountwrapper kipi-plugins klipper kmag kmail 
  kmailcvt kmenuedit kmilo kmix kmousetool kmplayer-base 
  kmplayer-konq-plugins knetworkconf knode knotes konq-plugins konqueror 
  konqueror-nsplugins konsole kontact konversation kooka kopete korganizer 
  kpdf kpersonalizer kpf kppp krdc kregexpeditor krfb kscreensaver 
  kscreensaver-xsavers ksmserver ksnapshot ksvg ksysguard ksysguardd 
  ksystemlog ktorrent kubuntu-artwork-usplash kubuntu-default-settings 
  kubuntu-desktop kubuntu-docs kubuntu-konqueror-shortcuts kvkbd 
  kwalletmanager kwin kwin-style-crystal language-selector-qt libakode2 
  libarts1-akode libarts1c2a libartsc0 libaudio2 libavahi-qt3-1 
  libavcodec1d libavutil1d libc6-dev libclucene0ldbl libdbus-qt-1-1c2 
  libept0 libexiv2-2 libfftw3-3 libflac++6 libgmp3c2 libgsm1 libifp4 
  libijs-0.35 libiso9660-5 libjpeg-progs libk3b2 libkbluetooth0 libkcal2b 
  libkcddb1 libkdcraw3 libkdepim1a libkexiv2-3 libkipi0 libkleopatra1 
  libkmime2 libkonq4 libkpimexchange1 libkpimidentities1 libksba8 libkscan1 
  libksieve0 libktnef1 liblua50 liblualib50 libmad0 libmimelib1c2a 
  libmodplug0c2 libmpcdec3 libmysqlclient15off libnjb5 libofa0 
  libpoppler-qt2 libpostproc1d libpq5 libpythonize0 libqt-perl libqt3-mt 
  libqt4-core libqt4-gui libqt4-qt3support libqt4-sql librsync1 libruby1.8 
  libsearchclient0 libskim0 libsmokeqt1 libstreamanalyzer0 libstreams0 
  libstrigihtmlgui0 libtunepimp5 libvcdinfo0 libxapian15 libxcb-shape0 
  libxcb-shm0 libxcb-xv0 libxine1 libxine1-bin libxine1-console 
  libxine1-ffmpeg libxine1-misc-plugins libxine1-plugins libxine1-x 
  libxvmc1 linux-libc-dev mpg123 mysql-common ncompress network-manager-kde 
  network-manager-openvpn network-manager-pptp network-manager-vpnc 
  networkstatus ocrad openoffice.org-kde openoffice.org-style-crystal 
  openvpn openvpn-blacklist oss-compat p7zip-full perl-suid pinentry-curses 
  pinentry-qt pmount poster postfix pptp-linux procmail pykdeextensions 
  python-dev python-kde3 python-pylibacl python-pyxattr python-qt3 
  python-qt4 python-qt4-common python-qt4-dbus python-reportlab python-sip4 
  python2.5-dev qca-tls qt4-qtconfig rdiff-backup resolvconf ruby ruby1.8 
  sane-utils scim-bridge-client-qt scim-qtimm skim software-properties-kde 
  speedcrunch strigi-applet strigi-daemon system-config-printer-kde 
  ttf-arphic-ukai ttf-dustin vcdimager vpnc zoo 
0 packages upgraded, 262 newly installed, 2 to remove and 0 not upgraded.
Need to get 225MB of archives. After unpacking 785MB will be used.
Do you want to continue? [Y/n/?] y
Writing extended state information... Done
Get:1 [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/main libxine1-bin 1.1.11.1-1ubuntu3.1 [1328kB]
Get:2 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/main kdelibs-data 4:3.5.9-0ubuntu7.1 [7308kB]
0% [2 kdelibs-data 15610/7308kB 0%] [1 libxine1-bin 61949/1328kB 4%]                                                                                                                                           
ubuntu@ubuntu-desktop:~$
```

---

### Post by Yezinki on 2008-08-19
Stopped at 4%?

---

### Post by prshah on 2008-08-19
> **Yezinki said:**
> 
1. How can I exactly know the specs/ make, type of the built in TV tuner board in my Sony....using which software?

Boot off a (K, Myth)Ubuntu live CD, then open a terminal (Applications-Accessories-Terminal) and give the command ```
lspci
```; if you want more details, you can add -v or -vv or -vvv to the above command, Eg```
lspci -v
``` Or for total hardware list, you can use ```
sudo lshw
```
> **Yezinki said:**
> 
2. Can I install MythBuntu on both?
3. How different is it from Ubuntu hardy or Kbuntu?

Yeah, sure; but MythUbuntu is based on Xfce (Xubuntu), which is a little less capable than (K)Ubuntu. Any 8.04 version of (Myth,X,K)Ubuntu is called Hardy (Heron).
> **Yezinki said:**
> 
4. Can I use my Cam online with MythBuntu? Should be able to, if it is recognized; using the live CD will give you a clue.
> **Yezinki said:**
> 
5. Does it have yahoo messanger or pidgin? Yes.
> **Yezinki said:**
> 
7. Using Ubuntu/Kbuntu/MythBuntu what command can I use to perform a low level format of my drive? A low-level format has nothing to do with the operating system (hence the "low level"). This should not be done in any case.
> **Yezinki said:**
> 
8. Would MythBuntu allow me to take snap shots of windows & itself for burning it later on to an optical media for a back up.. Yes. Look at remastersys; this works for all (Myth,X,K)Ubuntus

> **Yezinki said:**
> 
9. Would it have all the driers needed? Probably not; check using the live CD.

> **Yezinki said:**
> 10. Does it get auto updates?Yes.

> **Yezinki said:**
> 11. Lastly why do you prefer Kbuntu & Open SuSe over Ubuntu hardy ?

I like Ubuntu Hardy just fine. I suggest Kubuntu because KDE4 is more Windowsy/Vistaish, and both Kubuntu and OpenSUSE 11 use KDE4. Plus OpenSUSE v11 ran very well on my desktop as a live CD, but I've not installed it, so I don't know anything else about it.

---

### Post by Yezinki on 2008-08-19
```
Quote:
Originally Posted by Yezinki View Post
2. Can I install MythBuntu on both?
3. How different is it from Ubuntu hardy or Kbuntu?
Yeah, sure; but MythUbuntu is based on Xfce (Xubuntu), which is a little less capable than (K)Ubuntu. Any 8.04 version of (Myth,X,K)Ubuntu is called Hardy (Heron).
```

Hi thanks prshah again for being so elaborate.

What I meant is that whats the real difference between MythBuntu vs Kbuntu & Ubuntu?

I asked earlier too.......can the difeering features of 3 be integrated since they have the same basic platform Ubuntu???

Q```
uote:
Originally Posted by Yezinki View Post
5. Does it have yahoo messanger or pidgin?


Does MythUbuntu have a seperate yahoo messanger or just pidgin?

```
Can it use a web cam on line not like cheese or camorama?

Firstly I think you would recommend to download Ubunntu,Kbuntu & MythBuntu & than integrate features of Kbuntu  & MythBuntu in it??

waiting to hear your personal views!

---

### Post by prshah on 2008-08-19
> **Yezinki said:**
> 
3. How different is it from Ubuntu hardy or Kbuntu?
What I meant is that whats the real difference between MythBuntu vs Kbuntu & Ubuntu?
I asked earlier too.. can the differing features of 3 be integrated since they have the same basic platform Ubuntu???


Ubuntu 8.04 (Also called Hardy Heron) is Ubuntu with a desktop manager called Gnome. Gnome is a good desktop manager, but the interface is slightly different from Windows.

Kubuntu 8.04 (Also called Hardy Heron) is Ubuntu with a desktop manager called KDE, version 4. The interface is similar to Vista.

Xubuntu 8.04 (Also called Hardy Heron) is Ubuntu with a desktop manager called XFCE, which is a lightweight desktop manager that is designed for use on systems that have limited resources.

MythBuntu 8.04 (Also called Hardy Heron) is Ubuntu with a the XFCE desktop manager (Which makes is similar to Xubuntu), but with a program called MythTV pre-installed and setup into it; MythTV is a special interface that is similar to Windows Media Center.

Yes, you can use the programs from any one type in any other type. There are no limitations. You can also separately install, at any time, any one distribution into the other (Eg., Kubuntu into Ubuntu) with a simple command (and a massive download). You can switch between them to your hearts content.

Any more information will only confuse you further; I suggest you pick up MythBuntu and give it a go; Once you are comfortable with it, you can easily integrate other distros into it.

I don't know if you can use your webcam to stream video to messengers; I assume you can, but I have not tried this.

---

### Post by Yezinki on 2008-08-19
Thanks so much prshah! :smile:

You have been a REAL help in answering almost all my queries.

One last question you suggested to start from MythBuntu & than rum commands for the rest....I have Ubuntu Hardy Heron downloaded ......Can I start from there OR as you wrote from MythBuntu??

I hope you didn't mind my silly questions.

& hope  that in future shall be of guidance/assistance. O:)

being a med doc don't know much about OSs specially Linux based.....they are a whole new world.

Regards!

---

### Post by Yezinki on 2008-08-19
I have Ubuntu Hardy Heron 8.04 & Open SuS 10.3 installed on the same machine.....how can I unintsall Open SUS?

---

### Post by Yezinki on 2008-08-19
Capabilities: <access denied>

00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 02)
	Subsystem: Sony Corporation Unknown device 8205
	Flags: medium devsel, IRQ 10
	I/O ports at 18e0 [size=32]

02:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8036 PCI-E Fast Ethernet Controller (rev 10)
	Subsystem: Sony Corporation Unknown device 8205
	Flags: bus master, fast devsel, latency 0, IRQ 220
	Memory at d8000000 (64-bit, non-prefetchable) [size=16K]
	I/O ports at 2000 [size=256]
	Capabilities: <access denied>

06:00.0 Network controller: Broadcom Corporation BCM4311 802.11b/g WLAN (rev 01)
	Subsystem: AMBIT Microsystem Corp. Unknown device 0315
	Flags: bus master, fast devsel, latency 0, IRQ 18
	Memory at da000000 (32-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>

08:03.0 CardBus bridge: Texas Instruments PCIxx12 Cardbus Controller
	Subsystem: Sony Corporation Unknown device 8205
	Flags: bus master, medium devsel, latency 168, IRQ 17
	Memory at dc216000 (32-bit, non-prefetchable) [size=4K]
	Bus: primary=08, secondary=09, subordinate=0c, sec-latency=176
	Memory window 0: 88000000-8bfff000 (prefetchable)
	Memory window 1: 8c000000-8ffff000
	I/O window 0: 00005400-000054ff
	I/O window 1: 00005800-000058ff
	16-bit legacy interface ports at 0001

08:03.1 FireWire (IEEE 1394): Texas Instruments PCIxx12 OHCI Compliant IEEE 1394 Host Controller (prog-if 10 [OHCI])
	Subsystem: Sony Corporation Unknown device 8205
	Flags: bus master, medium devsel, latency 64, IRQ 17
	Memory at dc215000 (32-bit, non-prefetchable) [size=2K]
	Memory at dc210000 (32-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>

08:03.2 Mass storage controller: Texas Instruments 5-in-1 Multimedia Card Reader (SD/MMC/MS/MS PRO/xD)
	Subsystem: Sony Corporation Unknown device 8205
	Flags: bus master, medium devsel, latency 64, IRQ 18
	Memory at dc214000 (32-bit, non-prefetchable) [size=4K]
	Capabilities: <access denied>

08:05.0 Multimedia controller: Fujitsu Limited. Unknown device 202a
	Subsystem: Sony Corporation Unknown device 81fa
	Flags: medium devsel, IRQ 11
	I/O ports at 5000 [disabled] [size=256]
	Memory at dc000000 (32-bit, non-prefetchable) [disabled] [size=2M]
	Memory at dc200000 (32-bit, non-prefetchable) [disabled] [size=64K]
	Capabilities: <access denied>

ubuntu@ubuntu-desktop:~$ sudo lshw
ubuntu-desktop            
    description: Notebook
    product: VGC-LS1
    vendor: Sony Corporation
    version: C3LMKZHR
    serial: 28243230-3001856
    width: 32 bits
    capabilities: smbios-2.40 dmi-2.40 smp-1.4 smp
    configuration: boot=normal chassis=notebook cpus=2 uuid=C97E3540-29C3-11DB-8104-0013A94B18F6
  *-core
       description: Motherboard
       product: VAIO
       vendor: Sony Corporation
       physical id: 0
       version: N/A
       serial: N/A
       slot: Bank 0
     *-firmware
          description: BIOS
          vendor: Phoenix Technologies LTD
          physical id: 0
          version: R0062W2 (09/13/2006)
          size: 101KiB
          capacity: 960KiB
          capabilities: pci pcmcia pnp upgrade shadowing escd cdboot bootselect edd int9keyboard int10video acpi usb agp smartbattery biosbootspecification netboot
     *-cpu:0
          description: CPU
          product: Genuine Intel(R) CPU           T2400  @ 1.83GHz
          vendor: Intel Corp.
          physical id: 4
          bus info: cpu@0
          version: 6.14.8
          serial: 0000-06E8-0000-0000-0000-0000
          slot: N/A
          size: 1833MHz
          capacity: 1833MHz
          width: 32 bits
          clock: 167MHz
          capabilities: boot fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx constant_tsc arch_perfmon bts pni monitor vmx est tm2 xtpr cpufreq
          configuration: id=0
        *-cache:0
             description: L1 cache
             physical id: 5
             slot: L1 Cache
             size: 64KiB
             capacity: 64KiB
             capabilities: pipeline-burst internal write-back data
        *-cache:1
             description: L2 cache
             physical id: 6
             slot: L2 Cache
             size: 2MiB
             capacity: 2MiB
             capabilities: pipeline-burst internal write-back unified
        *-cache:2 DISABLED
             description: L3 cache
             physical id: 7
             slot: L3 Cache
        *-logicalcpu:0
             description: Logical CPU
             physical id: 0.1
             width: 32 bits
             capabilities: logical
        *-logicalcpu:1
             description: Logical CPU
             physical id: 0.2
             width: 32 bits
             capabilities: logical
     *-memory
          description: System Memory
          physical id: a
          slot: System board or motherboard
          size: 2GiB
        *-bank:0
             description: SODIMM Synchronous
             physical id: 0
             slot: SODIMM1
             size: 1GiB
             width: 64 bits
        *-bank:1
             description: SODIMM Synchronous
             physical id: 1
             slot: SODIMM2
             size: 1GiB
             width: 64 bits
     *-cpu:1
          physical id: 1
          bus info: cpu@1
          version: 6.14.8
          serial: 0000-06E8-0000-0000-0000-0000
          size: 1833MHz
          capacity: 1833MHz
          capabilities: vmx ht cpufreq
          configuration: id=0
        *-logicalcpu:0
             description: Logical CPU
             physical id: 0.1
             capabilities: logical
        *-logicalcpu:1
             description: Logical CPU
             physical id: 0.2
             capabilities: logical
     *-pci
          description: Host bridge
          product: Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub
          vendor: Intel Corporation
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 03
          width: 32 bits
          clock: 33MHz
          configuration: driver=agpgart-intel module=intel_agp
        *-display UNCLAIMED
             description: VGA compatible controller
             product: Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller
             vendor: Intel Corporation
             physical id: 2
             bus info: pci@0000:00:02.0
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: msi pm vga_controller bus_master cap_list
             configuration: latency=0
        *-multimedia
             description: Audio device
             product: 82801G (ICH7 Family) High Definition Audio Controller
             vendor: Intel Corporation
             physical id: 1b
             bus info: pci@0000:00:1b.0
             version: 02
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi pciexpress bus_master cap_list
             configuration: driver=HDA Intel latency=0 module=snd_hda_intel
        *-pci:0
             description: PCI bridge
             product: 82801G (ICH7 Family) PCI Express Port 1
             vendor: Intel Corporation
             physical id: 1c
             bus info: pci@0000:00:1c.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport-driver
           *-network
                description: Ethernet interface
                product: 88E8036 PCI-E Fast Ethernet Controller
                vendor: Marvell Technology Group Ltd.
                physical id: 0
                bus info: pci@0000:02:00.0
                logical name: eth0
                version: 10
                serial: 00:13:a9:4b:18:f6
                size: 100MB/s
                capacity: 100MB/s
                width: 64 bits
                clock: 33MHz
                capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation
                configuration: autonegotiation=on broadcast=yes driver=sky2 driverversion=1.20 duplex=full firmware=N/A ip=10.0.0.6 latency=0 link=yes module=sky2 multicast=yes port=twisted pair speed=100MB/s
        *-pci:1
             description: PCI bridge
             product: 82801G (ICH7 Family) PCI Express Port 2
             vendor: Intel Corporation
             physical id: 1c.1
             bus info: pci@0000:00:1c.1
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport-driver
        *-pci:2
             description: PCI bridge
             product: 82801G (ICH7 Family) PCI Express Port 3
             vendor: Intel Corporation
             physical id: 1c.2
             bus info: pci@0000:00:1c.2
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport-driver
           *-network
                description: Network controller
                product: BCM4311 802.11b/g WLAN
                vendor: Broadcom Corporation
                physical id: 0
                bus info: pci@0000:06:00.0
                version: 01
                width: 32 bits
                clock: 33MHz
                capabilities: pm msi pciexpress bus_master cap_list
                configuration: driver=b43-pci-bridge latency=0 module=ssb
        *-usb:0
             description: USB Controller
             product: 82801G (ICH7 Family) USB UHCI Controller #1
             vendor: Intel Corporation
             physical id: 1d
             bus info: pci@0000:00:1d.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0 module=uhci_hcd
        *-usb:1
             description: USB Controller
             product: 82801G (ICH7 Family) USB UHCI Controller #2
             vendor: Intel Corporation
             physical id: 1d.1
             bus info: pci@0000:00:1d.1
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0 module=uhci_hcd
        *-usb:2
             description: USB Controller
             product: 82801G (ICH7 Family) USB UHCI Controller #3
             vendor: Intel Corporation
             physical id: 1d.2
             bus info: pci@0000:00:1d.2
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0 module=uhci_hcd
        *-usb:3
             description: USB Controller
             product: 82801G (ICH7 Family) USB UHCI Controller #4
             vendor: Intel Corporation
             physical id: 1d.3
             bus info: pci@0000:00:1d.3
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0 module=uhci_hcd
        *-usb:4
             description: USB Controller
             product: 82801G (ICH7 Family) USB2 EHCI Controller
             vendor: Intel Corporation
             physical id: 1d.7
             bus info: pci@0000:00:1d.7
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: pm debug ehci bus_master cap_list
             configuration: driver=ehci_hcd latency=0 module=ehci_hcd
        *-pci:3
             description: PCI bridge
             product: 82801 Mobile PCI Bridge
             vendor: Intel Corporation
             physical id: 1e
             bus info: pci@0000:00:1e.0
             version: e2
             width: 32 bits
             clock: 33MHz
             capabilities: pci subtractive_decode bus_master cap_list
           *-pcmcia
                description: CardBus bridge
                product: PCIxx12 Cardbus Controller
                vendor: Texas Instruments
                physical id: 3
                bus info: pci@0000:08:03.0
                version: 00
                width: 32 bits
                clock: 33MHz
                capabilities: pcmcia bus_master cap_list
                configuration: driver=yenta_cardbus latency=176 maxlatency=5 mingnt=192 module=yenta_socket
           *-firewire
                description: FireWire (IEEE 1394)
                product: PCIxx12 OHCI Compliant IEEE 1394 Host Controller
                vendor: Texas Instruments
                physical id: 3.1
                bus info: pci@0000:08:03.1
                version: 00
                width: 32 bits
                clock: 33MHz
                capabilities: pm ohci bus_master cap_list
                configuration: driver=ohci1394 latency=64 maxlatency=4 mingnt=3 module=ohci1394
           *-storage
                description: Mass storage controller
                product: 5-in-1 Multimedia Card Reader (SD/MMC/MS/MS PRO/xD)
                vendor: Texas Instruments
                physical id: 3.2
                bus info: pci@0000:08:03.2
                version: 00
                width: 32 bits
                clock: 33MHz
                capabilities: storage pm bus_master cap_list
                configuration: driver=tifm_7xx1 latency=64 maxlatency=4 mingnt=7 module=tifm_7xx1
           *-multimedia UNCLAIMED
                description: Multimedia controller
                product: Fujitsu Limited.
                vendor: Fujitsu Limited.
                physical id: 5
                bus info: pci@0000:08:05.0
                version: 00
                width: 32 bits
                clock: 33MHz
                capabilities: pm cap_list
                configuration: latency=64 maxlatency=64 mingnt=16
        *-isa
             description: ISA bridge
             product: 82801GBM (ICH7-M) LPC Interface Bridge
             vendor: Intel Corporation
             physical id: 1f
             bus info: pci@0000:00:1f.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master cap_list
             configuration: latency=0
        *-ide:0
             description: IDE interface
             product: 82801G (ICH7 Family) IDE Controller
             vendor: Intel Corporation
             physical id: 1f.1
             bus info: pci@0000:00:1f.1
             logical name: scsi0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: ide bus_master emulated
             configuration: driver=ata_piix latency=0 module=ata_piix
           *-cdrom
                description: DVD-RAM writer
                product: DVD-RAM UJ-846S
                vendor: MATSHITA
                physical id: 0.0.0
                bus info: scsi@0:0.0.0
                logical name: /dev/cdrom
                logical name: /dev/dvd
                logical name: /dev/scd0
                logical name: /dev/sr0
                version: F200
                capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
                configuration: ansiversion=5 status=open
        *-ide:1
             description: IDE interface
             product: 82801GBM/GHM (ICH7 Family) SATA IDE Controller
             vendor: Intel Corporation
             physical id: 1f.2
             bus info: pci@0000:00:1f.2
             logical name: scsi2
             version: 02
             width: 32 bits
             clock: 66MHz
             capabilities: ide pm bus_master cap_list emulated
             configuration: driver=ata_piix latency=0 module=ata_piix
           *-disk
                description: ATA Disk
                product: WDC WD2500JS-98N
                vendor: Western Digital
                physical id: 0.0.0
                bus info: scsi@2:0.0.0
                logical name: /dev/sda
                version: 10.0
                serial: WD-WCANK4928404
                size: 232GiB (250GB)
                capabilities: partitioned partitioned:dos
                configuration: ansiversion=5 signature=000bf9ee
              *-volume:0
                   description: Linux filesystem partition
                   physical id: 1
                   bus info: scsi@2:0.0.0,1
                   logical name: /dev/sda1
                   version: 3.6
                   serial: a8021a13-fb08-4098-96e9-38c141099ca9
                   size: 10GiB
                   capacity: 10GiB
                   capabilities: primary journaled reiserfs initialized
                   configuration: filesystem=reiserfs hash=r5 state=clean
              *-volume:1
                   description: Extended partition
                   physical id: 2
                   bus info: scsi@2:0.0.0,2
                   logical name: /dev/sda2
                   size: 20GiB
                   capacity: 20GiB
                   capabilities: primary extended partitioned partitioned:extended
                 *-logicalvolume:0
                      description: Linux filesystem partition
                      physical id: 5
                      logical name: /dev/sda5
                      logical name: /
                      logical name: /dev/.static/dev
                      capacity: 10001MiB
                      configuration: mount.fstype=reiserfs mount.options=rw,relatime state=mounted
                 *-logicalvolume:1
                      description: Linux filesystem partition
                      physical id: 6
                      logical name: /dev/sda6
                      logical name: /home
                      capacity: 10001MiB
                      configuration: mount.fstype=reiserfs mount.options=rw,relatime state=mounted
                 *-logicalvolume:2
                      description: Linux swap / Solaris partition
                      physical id: 7
                      logical name: /dev/sda7
                      capacity: 996MiB
                      capabilities: nofs
              *-volume:2
                   description: EXT3 volume
                   vendor: Linux
                   physical id: 3
                   bus info: scsi@2:0.0.0,3
                   logical name: /dev/sda3
                   version: 1.0
                   serial: da94606c-f5c9-4a51-9a31-93e15b85e5d6
                   size: 20GiB
                   capacity: 20GiB
                   capabilities: primary bootable journaled extended_attributes large_files huge_files recover ext3 ext2 initialized
                   configuration: created=2008-08-17 09:37:29 filesystem=ext3 modified=2008-08-18 08:55:16 mounted=2008-08-18 08:54:58 state=clean
              *-volume:3
                   description: EXT3 volume
                   vendor: Linux
                   physical id: 4
                   bus info: scsi@2:0.0.0,4
                   logical name: /dev/sda4
                   version: 1.0
                   serial: b3a9dad1-9875-41e2-902e-c58ef3814f0d
                   size: 182GiB
                   capacity: 182GiB
                   capabilities: primary journaled extended_attributes large_files huge_files recover ext3 ext2 initialized
                   configuration: created=2008-08-17 09:37:40 filesystem=ext3 modified=2008-08-18 08:55:16 mounted=2008-08-18 08:55:03 state=clean
        *-serial UNCLAIMED
             description: SMBus
             product: 82801G (ICH7 Family) SMBus Controller
             vendor: Intel Corporation
             physical id: 1f.3
             bus info: pci@0000:00:1f.3
             version: 02
             width: 32 bits
             clock: 33MHz
             configuration: latency=0
  *-network DISABLED
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:16:cf:12:c4:02
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11g
ubuntu@ubuntu-desktop:~$ 
ubuntu@ubuntu-desktop:~$

---

### Post by Yezinki on 2008-08-19
Hi Sycron,

Did a clean install of Ubuntu Hardy Heron 8.04 & than tried to install Kbuntu package.......this is what I got.




ubuntu@ubuntu-laptop:~$ sudo aptitude update && aptitude install kbuntu-desktop
[sudo] password for ubuntu: 
Get:1 [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security Release.gpg [189B]              
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/main Translation-en_US            
Get:2 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy Release.gpg [191B]
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/main Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/restricted Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/universe Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/multiverse Translation-en_US
Get:3 [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security Release [58.5kB]
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/universe Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/multiverse Translation-en_US
Get:4 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates Release.gpg [189B]
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/main Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/universe Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/multiverse Translation-en_US
Get:5 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy Release [65.9kB]
Get:6 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates Release [58.5kB]
Get:7 [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/main Packages [53.8kB]          
Get:8 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/main Packages [1178kB]
Get:9 [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/restricted Packages [6636B]
Get:10 [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/main Sources [12.3kB]       
Get:11 [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/restricted Sources [908B]         
Get:12 [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/universe Packages [28.0kB]  
Get:13 [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/universe Sources [4530B]                                                                                                                                      
Get:14 [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/multiverse Packages [8222B]                                                                                                                                   
Get:15 [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/multiverse Sources [14B]                                                                                                                                      
Get:16 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/restricted Packages [6986B]                                                                                                                                          
Get:17 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/main Sources [338kB]                                                                                                                                                 
Get:18 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/restricted Sources [1488B]                                                                                                                                           
Get:19 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/universe Packages [4297kB]                                                                                                                                           
Get:20 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/universe Sources [1323kB]                                                                                                                                            
Get:21 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/multiverse Packages [179kB]                                                                                                                                          
Get:22 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/multiverse Sources [60.9kB]                                                                                                                                          
Get:23 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/main Packages [298kB]                                                                                                                                        
Get:24 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/restricted Packages [6636B]                                                                                                                                  
Get:25 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/main Sources [86.4kB]                                                                                                                                        
Get:26 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/restricted Sources [908B]                                                                                                                                    
Get:27 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/universe Packages [88.1kB]                                                                                                                                   
Get:28 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/universe Sources [21.6kB]                                                                                                                                    
Get:29 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/multiverse Packages [16.4kB]                                                                                                                                 
Get:30 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/multiverse Sources [2795B]                                                                                                                                   
Fetched 8203kB in 2min40s (51.1kB/s)                                                                                                                                                                           
Reading package lists... Done
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Initializing package states... Done
Building tag database... Done      
E: Could not open lock file /var/lib/dpkg/lock - open (13 Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?
ubuntu@ubuntu-laptop:~$ 
ubuntu@ubuntu-laptop:~$

---

### Post by Yezinki on 2008-08-19
Formatted the drive so removed Open SUSE........first it used to hang at 48%........now complete but wont install?

---

### Post by Yezinki on 2008-08-19
> **Sycron said:**
> If you want to have for example GNOME and KDE on ubuntu at the same time you can do that by installing them.

If you have gnome and you wish to install KDE try with this.
```
$ sudo aptitude update && sudo aptitude install kubuntu-desktop
```

Or if you have KDE and want gnome try this:
```
$ sudo aptitude update && sudo aptitude install ubuntu-desktop
```

Hi,

The Kubuntu command does not install it.....downloads 100% after I reinstalled Ubuntu....any ideas?

---

### Post by Yezinki on 2008-08-19
What are the commands for Xubuntu install??

---

### Post by Yezinki on 2008-08-19
Hi,

Whats wrong with the drive partitions that KDE wont install??

Thanks!

---

### Post by LowSky on 2008-08-19
> **Yezinki said:**
> 
```
sudo aptitude update && aptitude install kbuntu-desktop
```

should be

```
sudo aptitude update && aptitude install kubuntu-desktop
```

---

### Post by LowSky on 2008-08-19
> **Yezinki said:**
> What are the commands for Xubuntu install??

```
sudo aptitude install xubuntu-desktop
```

---

### Post by LowSky on 2008-08-19
> **Yezinki said:**
> Hi,

Whats wrong with the drive partitions that KDE wont install??

Thanks!

Your / and /home... are both the same size. which is impossible I would fix that. By the way / only need to be about 15GB, you can give the rest to /home

---

### Post by Yezinki on 2008-08-19
> **LowSky said:**
> should be

```
sudo aptitude update && aptitude install kubuntu-desktop
```

Ain't both the same??

---

### Post by Yezinki on 2008-08-19
> **LowSky said:**
> Your / and /home... are both the same size. which is impossible I would fix that. By the way / only need to be about 15GB, you can give the rest to /home

Hi there,

How do I correct em??

Thanks for your assistance!

---

### Post by Yezinki on 2008-08-19
Re: Dont discourage me from off Open Source!!
Quote:
Originally Posted by Yezinki View Post
Code:

sudo aptitude update && aptitude install kbuntu-desktop

should be

Code:

sudo aptitude update && aptitude install kubuntu-desktop



The Kubuntu does not install coz of the drive /partitions configurations??

---

### Post by Yezinki on 2008-08-19
> **LowSky said:**
> should be

```
sudo aptitude update && aptitude install kubuntu-desktop
```

Still says action denied.........


ubuntu@ubuntu-laptop:~$ sudo aptitude update && aptitude install kubuntu-desktop
[sudo] password for ubuntu: 
Ign cdrom://Ubuntu 8.04.1 _Hardy Heron_ - Release i386 (20080702.1) hardy Release.gpg
Ign cdrom://Ubuntu 8.04.1 _Hardy Heron_ - Release i386 (20080702.1) hardy/main Translation-en_US
Ign cdrom://Ubuntu 8.04.1 _Hardy Heron_ - Release i386 (20080702.1) hardy/restricted Translation-en_US
Ign cdrom://Ubuntu 8.04.1 _Hardy Heron_ - Release i386 (20080702.1) hardy Release
Ign cdrom://Ubuntu 8.04.1 _Hardy Heron_ - Release i386 (20080702.1) hardy/main Packages
Ign cdrom://Ubuntu 8.04.1 _Hardy Heron_ - Release i386 (20080702.1) hardy/restricted Packages
Err cdrom://Ubuntu 8.04.1 _Hardy Heron_ - Release i386 (20080702.1) hardy/main Packages
  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
Err cdrom://Ubuntu 8.04.1 _Hardy Heron_ - Release i386 (20080702.1) hardy/restricted Packages
  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
Hit [http://archive.canonical.com](http://archive.canonical.com) hardy Release.gpg                              
Ign [http://archive.canonical.com](http://archive.canonical.com) hardy/partner Translation-en_US                
Hit [http://archive.canonical.com](http://archive.canonical.com) hardy Release 
Get:1 [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security Release.gpg [189B] 
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/main Translation-en_US         
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy Release.gpg                   
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/main Translation-en_US        
Hit [http://archive.canonical.com](http://archive.canonical.com) hardy/partner Packages              
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/restricted Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/universe Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/multiverse Translation-en_US
Get:2 [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security Release [58.5kB]     
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/restricted Translation-en_US      
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/universe Translation-en_US        
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/multiverse Translation-en_US      
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates Release.gpg               
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/main Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/universe Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/multiverse Translation-en_US
Hit [http://archive.canonical.com](http://archive.canonical.com) hardy/partner Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy Release     
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates Release                  
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/main Packages                      
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/universe Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/universe Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/multiverse Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/multiverse Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/universe Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/universe Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/multiverse Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/multiverse Sources
Get:3 [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/main Packages [55.2kB]
Get:4 [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/restricted Packages [6636B]
Get:5 [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/main Sources [12.5kB]
Get:6 [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/restricted Sources [908B]
Get:7 [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/universe Packages [28.0kB]
Get:8 [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/universe Sources [4530B]
Get:9 [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/multiverse Packages [8222B]
Get:10 [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/multiverse Sources [14B]
Fetched 175kB in 4s (39.9kB/s) 
Reading package lists... Done
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Building tag database... Done      
E: Could not open lock file /var/lib/dpkg/lock - open (13 Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?
ubuntu@ubuntu-laptop:~$ 
ubuntu@ubuntu-laptop:~$

---

### Post by mb_webguy on 2008-08-19
You have to use sudo for both the update and the installation.  I use apt-get instead of aptitude, but the commands are otherwise identical:```
sudo apt-get update && sudo apt-get install kubuntu-desktop
```

---

### Post by Yezinki on 2008-08-19
Hi there,

You mean to type the same command again once the downloading is done....for installation?


Thanks.

---

### Post by mb_webguy on 2008-08-19
You're actually entering two different commands, one to update your package list, and anther to install the package.  Both commands must be run with root permissions, which means you have to precede each command with sudo.
```
sudo apt-get update && sudo apt-get install kubuntu-desktop
```...is the same as typing...```
sudo apt-get update
sudo apt-get install kubuntu-desktop
```
If you just type...```
sudo apt-get update && apt-get install kubuntu-desktop
```...then you're running only the first command with root permissions.

And as I said, you can substitute "aptitude" where I have typed "apt-get" in the above lines if you want.  However, if you use the Synaptic package manager, you should use apt-get rather than aptitude, since otherwise you could run into some problems, such as Synaptic not recognizing packages installed with aptitude.

---

### Post by Yezinki on 2008-08-19
Thanks i'll try & let ya know!

---

