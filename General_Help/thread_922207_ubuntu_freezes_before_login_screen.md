---
title: "ubuntu freezes before login screen"
date: 2008-09-17
forum: General Help
---

### Post by o0brae0o on 2008-09-17
ok so here's the deal, all was well with gutsy, then i decided to install the updates available... they were downloading from the hardy repos and am apparently running hardy :|, this is where the problem starts, i rebooted and just as gdm starts, the screen goes black, mouse cursor appears and freezes.. no movement and the animation is also frozen, it is one of those crappy mighty mouses and the LED in the mouse turns off, there is also no response from the keyboard either (LOCK keys don't do anything) the screen appears to refresh once as well.

If i run recovery mode, then type gdm, it runs all well.
I had similar problems when trying to install from the hardy livecd, but that seems to freeze at random points during boot.
i am running a ga pcv2 mini itx mobo (via chipset) with openchrome video drivers installed, from what i could find so far it appears to be xorg or the kernel.

dunno if this helps but...
> lspci
00:00.0 Host bridge: VIA Technologies, Inc. VT8623 [Apollo CLE266]
00:01.0 PCI bridge: VIA Technologies, Inc. VT8633 [Apollo Pro266 AGP]
00:05.0 Communication controller: Rockwell International HSF 56k Data/Fax/Voice Modem (rev 01)
00:09.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
00:10.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 80)
00:10.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 80)
00:10.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 80)
00:10.3 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 82)
00:11.0 ISA bridge: VIA Technologies, Inc. VT8235 ISA Bridge
00:11.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 06)
00:11.5 Multimedia audio controller: VIA Technologies, Inc. VT8233/A/8235/8237 AC97 Audio Controller (rev 50)
01:00.0 VGA compatible controller: VIA Technologies, Inc. VT8623 [Apollo CLE266] integrated CastleRock graphics (rev 03)


if anyone can help that would be greatly appreciated.
cheers in advance.

---

### Post by tb52726 on 2008-10-16
not much help, but i too have this problem.

Am using the latest ubuntu version 8.041 i386. 

Tried both LiveCD and installation both fail. LiveCd option boots to desktop with a error message, but no details (system had a error, no error report was reported" or something like that)

Does Ubuntu have support for Via c3 eden cpus? Or is there no support for this Motherboard?

---

### Post by o0brae0o on 2008-10-17
cheers for that reply.. i was half way through downloading 8.04.1... on dial-up, but since i know that is not gona work i think i'll just try intrepid beta and see how my luck goes there.

as for support.. i have c3 nemehiah.. or however it's spelt.. and it does not appear so, i have been trying to find a solution for a VERY long time, i would hate to add together the hours in total so i kinda just gave up. All i can say is 7.10 works fine, but i want 8.04 dammit! :P

well if i end up sussing something out i will post back but till then, good luck.
PEACE.

---

### Post by tb52726 on 2008-10-18
hey, yeah i just installed 7.10 and its working great, needed to use the alt cd but it was fast and painless.

Also tried xbuntu but it too crashs. I reckon all 8.04.1 will fail, 8.10 is meant to be out soon might try that, but right now as my first go at linux 7.10 will do fine.

Cheers
TB

---

### Post by o0brae0o on 2008-10-21
hmm, well this certainly sucks, i tried 8.10 beta livecd and it hung as it did in 8.04.

do you also get this retarded thing where there is no audio in 7.10?

well looks like i will be going back to fedora.. ugh i hate packagekit.. soo slowww.. but at least i know fedora 9 works, wine doesnt make my system hang and i also get audio.
 Sad really, i just want to use ubuntu and not have to wait a friggin' hour for packagekit to play with itself whenever i install something from the repositories!

might try the 8.10 text based installer though when the final version is released.

damn i hope it works!
Cheers.
PEACE

---

### Post by tb52726 on 2008-11-03
Just tried audio and it plays fine. was via a xvid avi file, had to install some codecs (which it did automatically)

---

### Post by gabkdlly on 2008-11-12
I too have had problems since Hardy, and as we have similar hardware, I would like to make you aware of the bug I filed about this issue:

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/278141](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/278141)

---

