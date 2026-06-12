---
title: "Hard lock with ubuntu 5.04 on hp 4055"
date: 2005-08-18
forum: Hardware &amp; Laptops
---

### Post by patrikj on 2005-08-18
Installing Ubuntu 5.04 on a HP d4055.se

Text-based install went smoothly, with nicely automagic subsequent
  boot and downloading/installing/updating of packages. GDM starts,
  but not at the optimum 1600x1200 resolution (at 1280x960 or
  something like that instead). Worse than the resolution problem is
  that the mouse clicks are undetected (moving the mouse pointer works
  fine and so does the keyboard (both wireless HID devices)). I didn't
  manage to do much in GNOME after login without a clicking mouse, but
  after some testing and managed to find out how to use the keyboard
  only to start synaptics and install kernel 2.6.11 with smp support
  (was kernel 2.6.10 without). After reboot with the new kernel the
  mouse clicks work, but GNOME hard locks the computer very soon after
  login (only upper and lower bar background color and half an icon in
  the bottom left + mouse pointer appear on screen). Only way out is
  the dreaded 5s press on the power-off button (keyboard, mouse are
  dead).

(Console login works fine, but startx also results in hard-lock.)

Next I borrowed a regular keyboard + mouse (with wires;-) known to
  work with another computer and also switched from using digital DVI
  to analog D-SUB cable to the monitor. The result is that 1600x1200
  works in GDM but the same hard-lock happens immediately after login
  as before. Thus the keyboard-mouse combo (with corresponding HID
  driver) seems innocent.

Next I installed IceWM and restarted choosing it in the GDM session
  menu. This login works with the window manager without the
  hard-lock. I hack around fairly happily for two hours (downloading
  and installing heaps of useful packages I will need for my work and
  play later + copying files from an older computer) before the
  hard-lock appears again - this time without an easily reproducible
  trigger action. First thought: hardware error.

Next I let GRUB run memtest for an hour, but nothing showed up.

Any ideas how I could pinpoint the problem better? Is there some nice
  debug logging option available for some part of this GNU/Linux/GNOME
  complex which could provide sufficient data to help avoiding the
  hard-locks?

Specification:
  HP Pavilion 4055.se (bought July 2005)
  Screen HP 2035 20" TFT with DVI input
  wireless keyboard and mouse
  1Gb RAM

Details below (in Swedish)

HP Pavilion d4055.se stationär dator (PW749AA)- Specifikationer
	
	
Processor, operativsystem och minne
  Installerat operativsystem
          Microsoft® Windows® XP Home Edition
  Processor
          Intel® Pentium® 4-processor 550
             90nm LDA775, 1Mb L2 cache, 3.4 GHz, 800MHz front side
  bus, 
  processorteknik
          med Hyperthreading-teknik
  Processorfrekvens
          3,4 GHz
  Systembuss
          800 MHz
  Cache
          1 MB cacheminne (L2)
  Kretsar
          Intel® 915P-express kretsar
  Minne som standard
          1 GB
  Minnestyp
          DDR2 SDRAM
  Minneskortplatser
          4 DIMM-platser
Interna drivrutiner
  Intern hårddisk
          500 GB (2 x 250 GB)
  Hårddiskstyrenhet
          Seriell ATA-hårddisk
  Hårddiskhastighet
          (7200 rpm)
  typ av optisk enhet
          DVD-enhet
  optiska enhetens hastighet
          16x max.
  enhetstyp, andra optisk enhet
          DVD-brännare
  hastighet hos andra optisk enhet
          ±R/ ±RW med dubbla lager och upp till 16x med stöd för LightScribe-teknik
Systemegenskaper
  Minneskortsläsare
          9-i-1 minneskortsläsare
  Nätverksgränssnitt
          10/100 Mbit/s nätverksstöd
  gränssnitt för videofångst
          IEEE 1394 FireWire®-gränssnitt
  Internt ljud
          Creative Sound Blaster® Audigy® 2 ZS 7.1
  Tangentbord
          Trådlöst tangentbord och trådlös mus
  Externa enhetsfack
          4 externa platser för optiska enheter, 3 interna hårddiskplatser
  Bildskärmsadapter, buss
          1 PCI-Express 16x
  Expansionsfack
          3 PCI
  Externa I/O-portar
          7 USB 2.0-portar (3 på framsidan); 2 FireWire / IEEE-1394-portar (1 på framsidan); 1 parallellport
Programvara
  Program -- Produktivitet och finans
          Microsoft® Word 2002; Microsoft® Works 8.0; Adobe® Photoshop Elements (engelsk version)
  Förinstallerad programvara
          Microsoft® Internet Explorer 6.0; Microsoft® Outlook® Express; Adobe® Reader 6.0
  drivrutin för optiska läsare
          Microsoft® MovieMaker 2; Microsoft® Windows® Media Player; Apple iTunes; InterVideo WinDVD med Dolby Digital-uppspelning
  nedladdningsbar programvara
          Gratis programvaruerbjudande med Pavilion Club
  Programvara - internet och online
          Easy Internet Signup med ledande Internetleverantörer
  Medföljande program
          Återställningspartitionering för HP Pavilion (med möjlighet att återställa system, tillämpningar och drivrutiner separat); Valfri omallokering av återställningspartitionering; Symantec™ Norton Internet Security™ 2005 (3 års realtidsuppdateringar)
  Mått/vikt/garanti
  Vikt
          18,2 kg
  Emballagevikt
          21 kg
  Yttermått (b x d x h)
          200 x 480 x 430 mm
  Emballagets yttermått (B x D x H)
          600 x 500 x 540 mm
  Garantideklaration
          Modeller i HP Pavilion-familjen som säljs i Hem-PC omfattas av tre års utökad garanti.

---

### Post by patrikj on 2005-08-28
Hardlock roblem fixed: the 2.6.11 kernel needs the noinotify parameter added. (Edit with grub.) After doing that gnome works without hardlock. Seems to be this (solved) bug:  [http://bugzilla.ubuntu.com/show_bug.cgi?id=7346](http://bugzilla.ubuntu.com/show_bug.cgi?id=7346)

The "No 1600x1200 resoultion with DVI cable" problem is not fixed however.

---

