---
title: "Upgraded from 9.04 to 9.10 - Won't play media"
date: 2009-10-31
forum: Installation &amp; Upgrades
---

### Post by Nicoon on 2009-10-31
Hi guys, 

I upgraded from Jaunty to Karmic yesterday. One thing I noticed after the upgrade was that none of my videos worked anymore. It claimed I no longer had the correct codecs to run it - same in all players, including VLC. 

I reinstalled the ubuntu-extras, searched for codecs, did manual installs through synaptic, ... anything I could think of and nothing worked. 

Anyone care to point me in the right direction?

---

### Post by SoundGuy.Jon on 2009-11-01
I'm having the same problem. None of my videos will play in any media player, not even VLC, with which I have never had a problem playing a video unless it was corrupted. This is very very annoying. Hopefully the developers will see the problem and fix it soon

---

### Post by legalguy on 2009-11-01
Me three...I noticed the restricted extras were gone, instaling those didn't help.

---

### Post by chenxiaolong on 2009-11-01
I did a clean install and this also happens to me. I guess it's a bug in the new OS.

---

### Post by 11010110 on 2009-11-01
Yeah it is the same thing with me... I've had my own thread going on it too. More exposure couldn't hurt I guess. Ill link ya to it. Maybe someone will get back to one of us lol. 


heres my thread:
[http://ubuntuforums.org/showthread.php?t=1308235](http://ubuntuforums.org/showthread.php?t=1308235)

Good luck everyone!

---

### Post by Pépou on 2009-11-02
Same problem for me since I upgraded my ubuntu to karmic. All videos freeze all the time !!

---

### Post by jet-san on 2009-11-02
My movies woks, I mean I can watch it, but without sound.
After upgrade to 9.10 I have NO sound on Ubuntu (music, videos, etc.).

Does anyone have problem ONLY with sounds like me?
[http://ubuntuforums.org/showthread.php?p=8221955#post8221955](http://ubuntuforums.org/showthread.php?p=8221955#post8221955)

---

### Post by chenxiaolong on 2009-11-02
I got the problem fixed. Make sure you have the Medibuntu repository disabled if you have it. Here's how I did it:

I removed the packages that were installed by the metapackage "ubuntu-restricted-extras". (If you use synaptic, choose the completely remove option or run the command below the list)

ffmpeg
gstreamer0.10-ffmpeg
gstreamer0.10-fluendo-mp3
gstreamer0.10-plugins-ugly
liba52-0.7.4
libavcodec52
libavformat52
libavutil49
libdvdnav4
libdvdread4
libgsm1
libid3tag0
libmad0
libmpeg2-4
libpostproc51
libschroedinger-1.0-0
libsidplay1
libswscale0
libtwolame0
ubuntu-restricted-extras
libavcodec52
libavformat52
libswscale0
libvlc2
libvlccore2
vlc
vlc-data
vlc-nox
vlc-plugin-pulse

```
sudo apt-get remove --purge ffmpeg gstreamer0.10-ffmpeg gstreamer0.10-fluendo-mp3 gstreamer0.10-plugins-ugly liba52-0.7.4 libavcodec52 libavformat52 libavutil49 libdvdnav4 libdvdread4 libgsm1 libid3tag0 libmad0 libmpeg2-4 libpostproc51 libschroedinger-1.0-0 libsidplay1 libswscale0 libtwolame0 ubuntu-restricted-extras libavcodec52 libavformat52 libswscale0 libvlc2 libvlccore2 vlc vlc-data vlc-nox vlc-plugin-pulse
```

This will remove any codecs installed and any programs that use the codecs. Ex. mplayer, Audacity, xmms, etc. Don't worry, you can install them afterwards. 

Then install the ubuntu-desktop package (I have no idea how it got removed):

```
sudo apt-get install ubuntu-desktop
```

OR if you use Kubuntu, run:

```
sudo apt-get install kubuntu-desktop
```

Then clear the package cache, so it doesn't install the same screwed up package again:

```
sudo apt-get clean
```

Restart your computer.

Afterwards, install the ubuntu-restricted-extras package again:

```
sudo apt-get install ubuntu-restricted-extras
```

And install any other player/software that was removed again and hope that it works :)

---

### Post by Pépou on 2009-11-03
Works for me !!!

Thank you so much !!

:KS

---

### Post by garvinrick4 on 2009-11-03
Try Movie Player with Ubuntu-restricted-extras in add-remove applications is simplest.

Movie player with all the codecs in ubuntu-restricted-extras
plays just about everything you can throw at it. 


If you think problem with restricted extras remove them.

Use your GUI or the terminal which ever you choose.



Sudo apt-get clean

sudo apt-get install ubuntu-restricted-extras

If package is broken you have to apt-get clean to remove from cache or you are just adding same package back again.
I know simple but just in case you need the help.

---

### Post by jet-san on 2009-11-03
I did everything [chenxiaolong]("http://ubuntuforums.org/member.php?u=724117") says, but it didn't fix my problem with sound. My Ubuntu is still muted:(

PC
Processor:  	Intel Core 2 Duo E8600
Memory:  	4GB (2 X 2GB) Kingston PC6400 800Mhz DDR2
PCI-E Graphics:  	512MB ATI HD4850
Sound Card:  	Creative PCI Audigy SE 7.1

---

### Post by style23 on 2009-11-03
I Did the workarounds and ever time I try to play a movie in Movie Player, Movie Player just closes. Now if I don't have ubuntu-restricted-extras installed, when I try to play the movies it will ask for a plugin and i'll click the search for the plugin, then it will install the plugin and it will be successful. I'll try to play the movie again and i'll get errors that it it doesn't have this or that plug-in. Is there anything else that I can do?

---

### Post by style23 on 2009-11-03
Also this is the error I receive in Totem:

The program 'totem' received an X Window System error.
This probably reflects a bug in the program.
The error was 'BadAlloc (insufficient resources for operation)'.
  (Details: serial 94 error_code 11 request_code 132 minor_code 19)
  (Note to programmers: normally, X errors are reported asynchronously;
   that is, you will receive the error a while after causing it.
   To debug your program, run it with the --sync command line
   option to change this behavior. You can then get a meaningful
   backtrace from your debugger if you break on the gdk_x_error() function.)

---

### Post by chenxiaolong on 2009-11-03
Jet-san, does your sound not work only when you're playing videos? Does it work if you watch videos online, like from Youtube? If no sounds work, then it's probably a problem with alsa. By the way, is your computer a Dell?

---

### Post by jet-san on 2009-11-04
No, no. I have NO sound in general. I can't hear musics, videos, YouTube - nothing. Whole Ubuntu is muted since upgrade, despite my sound preferences are on and set for 100% :/
No my computer is NOT Dell.

Regards
Jet

---

### Post by jet-san on 2009-11-04
I have just noticed YouTube videos doesn't work properly. I can't press "play-button" or stop it when it runs. I am not sure, but I think it was fine before this clearing. What should I do? Maybe install something?

Of course my Ubuntu is still muted:(

---

### Post by chenxiaolong on 2009-11-04
Actually the YouTube problem is another bug in the new Ubuntu release. You'll have to download the flash player from adobe. 

If you run Ubuntu 64 bit, download this: [http://download.macromedia.com/pub/labs/flashplayer10/libflashplayer-10.0.32.18.linux-x86_64.so.tar.gz](http://download.macromedia.com/pub/labs/flashplayer10/libflashplayer-10.0.32.18.linux-x86_64.so.tar.gz)

If you run Ubuntu 32 bit, download this: [http://fpdownload.macromedia.com/get/flashplayer/current/install_flash_player_10_linux.tar.gz](http://fpdownload.macromedia.com/get/flashplayer/current/install_flash_player_10_linux.tar.gz)

Then extract the package. (right click and click Extract Here)

Copy the "libflashplayer.so" to ~/.mozilla/plugins/. You will have to create the plugins folder.

Then uninstall the original broken flash player. 

```
sudo apt-get remove --purge flashplugin-nonfree flashplugin-installer
```

And open Firefox again.

-----------------------------------------

As for your sound card issue, could you try installing the "alsa-firmware" package? Some Creative audio cards need it to work. If it still doesn't work (after restart), could run "lspci -vv" in Terminal and post the entire section about your card. It will make it easier for me to find a solution.

---

### Post by style23 on 2009-11-04
Problem solved for Totem - give thanks to Koston for the totem help.
This is the thread.

[http://ubuntuforums.org/showthread.php?t=855418](http://ubuntuforums.org/showthread.php?t=855418)

Solution:

Pressed Alt + F2

Typed in the box: gstreamer-properties
Click run.

Select the video tab and changed the output to (X Window System no Xv)

It plays, so thats cool. I had to change the Video output plugin on the other media players in order for them to work correctly as well.

---

### Post by adalal on 2009-11-04
Make sure the restricted repositories are re-enabled, because they get disabled during upgrades.

---

### Post by jet-san on 2009-11-05
YouTube fixed - thanks [chenxiaolong]("http://ubuntuforums.org/member.php?u=724117")!

About my sound - what is "alsa-firmware" package and how to install it?
I went to this site [http://www.alsa-project.org/main/index.php/Main_Page](http://www.alsa-project.org/main/index.php/Main_Page)
is it the right one?
I have downloaded "[alsa-driver-1.0.21]("ftp://ftp.alsa-project.org/pub/driver/alsa-driver-1.0.21.tar.bz2")" what's nest?
I'm still a beginner user with Ubuntu=]

P.S.
Is it any keyboard shortcut to open Terminal?

---

### Post by jet-san on 2009-11-05
```
_@_:~$ lspci -vv
00:00.0 Host bridge: Intel Corporation 82G33/G31/P35/P31 Express DRAM Controller (rev 10)
    Subsystem: ASRock Incorporation Device 29c0
    Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort+ >SERR- <PERR- INTx-
    Latency: 0
    Capabilities: <access denied>
    Kernel modules: intel-agp

00:01.0 PCI bridge: Intel Corporation 82G33/G31/P35/P31 Express PCI Express Root Port (rev 10)
    Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B- DisINTx+
    Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 0, Cache Line Size: 32 bytes
    Bus: primary=00, secondary=04, subordinate=04, sec-latency=0
    I/O behind bridge: 0000e000-0000efff
    Memory behind bridge: feb00000-febfffff
    Prefetchable memory behind bridge: 00000000d0000000-00000000dfffffff
    Secondary status: 66MHz- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort+ <SERR- <PERR-
    BridgeCtl: Parity- SERR+ NoISA- VGA+ MAbort- >Reset- FastB2B-
        PriDiscTmr- SecDiscTmr- DiscTmrStat- DiscTmrSERREn-
    Capabilities: <access denied>
    Kernel driver in use: pcieport-driver
    Kernel modules: shpchp

00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 01)
    Subsystem: ASRock Incorporation Device 3662
    Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 0, Cache Line Size: 32 bytes
    Interrupt: pin A routed to IRQ 16
    Region 0: Memory at fe9fc000 (64-bit, non-prefetchable) [size=16K]
    Capabilities: <access denied>
    Kernel driver in use: HDA Intel
    Kernel modules: snd-hda-intel

00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 01)
    Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B- DisINTx+
    Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 0, Cache Line Size: 32 bytes
    Bus: primary=00, secondary=02, subordinate=02, sec-latency=0
    Prefetchable memory behind bridge: 00000000cff00000-00000000cfffffff
    Secondary status: 66MHz- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort+ <SERR- <PERR-
    BridgeCtl: Parity- SERR+ NoISA- VGA- MAbort- >Reset- FastB2B-
        PriDiscTmr- SecDiscTmr- DiscTmrStat- DiscTmrSERREn-
    Capabilities: <access denied>
    Kernel driver in use: pcieport-driver
    Kernel modules: shpchp

00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 01)
    Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B- DisINTx+
    Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 0, Cache Line Size: 32 bytes
    Bus: primary=00, secondary=01, subordinate=01, sec-latency=0
    I/O behind bridge: 0000c000-0000cfff
    Memory behind bridge: fea00000-feafffff
    Prefetchable memory behind bridge: 00000000cfe00000-00000000cfefffff
    Secondary status: 66MHz- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- <SERR- <PERR-
    BridgeCtl: Parity- SERR+ NoISA- VGA- MAbort- >Reset- FastB2B-
        PriDiscTmr- SecDiscTmr- DiscTmrStat- DiscTmrSERREn-
    Capabilities: <access denied>
    Kernel driver in use: pcieport-driver
    Kernel modules: shpchp

00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 01)
    Subsystem: ASRock Incorporation Device 27c8
    Control: I/O+ Mem- BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Status: Cap- 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 0
    Interrupt: pin A routed to IRQ 23
    Region 4: I/O ports at b480 [size=32]
    Kernel driver in use: uhci_hcd

00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 01)
    Subsystem: ASRock Incorporation Device 27c9
    Control: I/O+ Mem- BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Status: Cap- 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 0
    Interrupt: pin B routed to IRQ 19
    Region 4: I/O ports at b800 [size=32]
    Kernel driver in use: uhci_hcd

00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 01)
    Subsystem: ASRock Incorporation Device 27ca
    Control: I/O+ Mem- BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Status: Cap- 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 0
    Interrupt: pin C routed to IRQ 18
    Region 4: I/O ports at b880 [size=32]
    Kernel driver in use: uhci_hcd

00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 01)
    Subsystem: ASRock Incorporation Device 27cb
    Control: I/O+ Mem- BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Status: Cap- 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 0
    Interrupt: pin D routed to IRQ 16
    Region 4: I/O ports at bc00 [size=32]
    Kernel driver in use: uhci_hcd

00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 01) (prog-if 20)
    Subsystem: ASRock Incorporation Device 27cc
    Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 0
    Interrupt: pin A routed to IRQ 23
    Region 0: Memory at fe9fbc00 (32-bit, non-prefetchable) [size=1K]
    Capabilities: <access denied>
    Kernel driver in use: ehci_hcd

00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev e1) (prog-if 01)
    Control: I/O+ Mem- BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B- DisINTx-
    Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 0
    Bus: primary=00, secondary=03, subordinate=03, sec-latency=32
    I/O behind bridge: 0000d000-0000dfff
    Secondary status: 66MHz- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort+ <SERR- <PERR-
    BridgeCtl: Parity- SERR+ NoISA- VGA- MAbort- >Reset- FastB2B-
        PriDiscTmr- SecDiscTmr- DiscTmrStat- DiscTmrSERREn-
    Capabilities: <access denied>

00:1f.0 ISA bridge: Intel Corporation 82801GB/GR (ICH7 Family) LPC Interface Bridge (rev 01)
    Subsystem: ASRock Incorporation Device 27b8
    Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 0
    Capabilities: <access denied>
    Kernel modules: iTCO_wdt, intel-rng

00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 01) (prog-if 8a [Master SecP PriP])
    Subsystem: ASRock Incorporation Device 27df
    Control: I/O+ Mem- BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Status: Cap- 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 0
    Interrupt: pin A routed to IRQ 18
    Region 0: I/O ports at 01f0 [size=8]
    Region 1: I/O ports at 03f4 [size=1]
    Region 2: I/O ports at 0170 [size=8]
    Region 3: I/O ports at 0374 [size=1]
    Region 4: I/O ports at ffa0 [size=16]
    Kernel driver in use: ata_piix

00:1f.2 IDE interface: Intel Corporation 82801GB/GR/GH (ICH7 Family) SATA IDE Controller (rev 01) (prog-if 8f [Master SecP SecO PriP PriO])
    Subsystem: ASRock Incorporation Device 27c0
    Control: I/O+ Mem- BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Status: Cap+ 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 0
    Interrupt: pin B routed to IRQ 19
    Region 0: I/O ports at b400 [size=8]
    Region 1: I/O ports at b080 [size=4]
    Region 2: I/O ports at b000 [size=8]
    Region 3: I/O ports at ac00 [size=4]
    Region 4: I/O ports at a880 [size=16]
    Capabilities: <access denied>
    Kernel driver in use: ata_piix

00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 01)
    Subsystem: ASRock Incorporation Device 27da
    Control: I/O+ Mem- BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Status: Cap- 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Interrupt: pin B routed to IRQ 5
    Region 4: I/O ports at 0400 [size=32]
    Kernel modules: i2c-i801

01:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 02)
    Subsystem: ASRock Incorporation Device 8136
    Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx+
    Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 0, Cache Line Size: 32 bytes
    Interrupt: pin A routed to IRQ 2300
    Region 0: I/O ports at c800 [size=256]
    Region 2: Memory at cfeff000 (64-bit, prefetchable) [size=4K]
    Region 4: Memory at cfee0000 (64-bit, prefetchable) [size=64K]
    Expansion ROM at feae0000 [disabled] [size=128K]
    Capabilities: <access denied>
    Kernel driver in use: r8169
    Kernel modules: r8169

03:01.0 Multimedia audio controller: Creative Labs CA0106 Soundblaster
    Subsystem: Creative Labs Device 100a
    Control: I/O+ Mem- BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 32 (500ns min, 5000ns max)
    Interrupt: pin A routed to IRQ 22
    Region 0: I/O ports at dc00 [size=32]
    Capabilities: <access denied>
    Kernel driver in use: CA0106
    Kernel modules: snd-ca0106

04:00.0 VGA compatible controller: ATI Technologies Inc RV770 [Radeon HD 4850]
    Subsystem: Giga-byte Technology Device 21c0
    Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx+
    Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 0, Cache Line Size: 32 bytes
    Interrupt: pin A routed to IRQ 2299
    Region 0: Memory at d0000000 (64-bit, prefetchable) [size=256M]
    Region 2: Memory at febe0000 (64-bit, non-prefetchable) [size=64K]
    Region 4: I/O ports at e000 [size=256]
    Expansion ROM at febc0000 [disabled] [size=128K]
    Capabilities: <access denied>
    Kernel driver in use: fglrx_pci
    Kernel modules: fglrx

04:00.1 Audio device: ATI Technologies Inc HD48x0 audio
    Subsystem: Giga-byte Technology Device aa30
    Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 0, Cache Line Size: 32 bytes
    Interrupt: pin B routed to IRQ 17
    Region 0: Memory at febfc000 (64-bit, non-prefetchable) [size=16K]
    Capabilities: <access denied>
    Kernel driver in use: HDA Intel
    Kernel modules: snd-hda-intel

```

---

