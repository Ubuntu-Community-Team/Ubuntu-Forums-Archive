---
title: "System fatally freezes just after Boot but will NOT [Shift] to grub... Only GUI"
date: 2017-09-26
forum: Hardware
---

### Post by tregrrr on 2017-09-26
I believe the LTS the system is running is 16.04 but It may be 17.04. I don't think the fix will be all that different...

The  miscreant system has demanded a manual fsck -y intervention several  times, and now reboots ALWAYS include a schwack of orphaned inode lists. It then boots straight to through the grey screen (where the mouse cursor is born) and up comes the desktop... for up to 10 seconds if you don't touch anything. The screen then fractures all up and you can see the cubanist impression of the desktop and everything freezes like deer  in headlights. After a few moments it most often digresses further ending up as a pure mustard, purple, blue white or some other seemingly random solid colour screen. 

For kicks and giggles I transplanted  the drive into an identical twin box. Everything is identical, except  serial numbers and monitor, and it did almost exactly the same thing.  The shape of the artwork rendered was slightly different but I attribute  that to the nicer monitor. That in my mind rules out a hardware issue.

The  impasse I have is the machine boots directly into GUI and does not  respond to holding nor tapping  [shift] or [Ctrl]+[Alt]+[F1] in an  attempt to access grub for a terminal approach to addressing the  problem.


I found [URL="https://ubuntuforums.org/showthread.php?t=1904347"]https://ubuntuforums.org/showthread.php?t=1904347 
[/URL]

I have the exact same need as that OP: I need to modify a config file on the real system so that it HAS to boot into a CLI. I have 

opened/boot/grub/grub.cfg

as suggested by Paddy (the Jedi Master in the other, old thread) except that in the past 7 years I think things changed.


Can someone help me out with a more modern hack that will do what I need it to do and force a CLI bootup? After that we can talk about how to fix the drivers if Google and forum searching fail me.

Thanks guys 
T

---

### Post by westie457 on 2017-09-26
Welcome tregrrr

Things have changed, the left shift key was used for Grub versions 0.99 and earlier. When Grub2 (1.97 and later) began to be utilised the Grub menu access key was changed to the Esc key.

---

### Post by Autodave on 2017-09-26
How about some specs on the machine and video card in it. Have you installed any video drivers yet? Which one(s)?

---

### Post by deadflowr on 2017-09-26
> **tregrrr said:**
> I believe the LTS the system is running is 16.04 but It may be 17.04. I don't think the fix will be all that different...

The  miscreant system has demanded a manual fsck -y intervention several  times, and now reboots ALWAYS include a schwack of orphaned inode lists. It then boots straight to through the grey screen (where the mouse cursor is born) and up comes the desktop... for up to 10 seconds if you don't touch anything. The screen then fractures all up and you can see the cubanist impression of the desktop and everything freezes like deer  in headlights. After a few moments it most often digresses further ending up as a pure mustard, purple, blue white or some other seemingly random solid colour screen. 

For kicks and giggles I transplanted  the drive into an identical twin box. Everything is identical, except  serial numbers and monitor, and it did almost exactly the same thing.  The shape of the artwork rendered was slightly different but I attribute  that to the nicer monitor. That in my mind rules out a hardware issue.

The  impasse I have is the machine boots directly into GUI and does not  respond to holding nor tapping  [shift] or [Ctrl]+[Alt]+[F1] in an  attempt to access grub for a terminal approach to addressing the  problem.


I found [URL="https://ubuntuforums.org/showthread.php?t=1904347"]https://ubuntuforums.org/showthread.php?t=1904347 
[/URL]

I have the exact same need as that OP: I need to modify a config file on the real system so that it HAS to boot into a CLI. I have 

opened/boot/grub/grub.cfg

as suggested by Paddy (the Jedi Master in the other, old thread) except that in the past 7 years I think things changed.


Can someone help me out with a more modern hack that will do what I need it to do and force a CLI bootup? After that we can talk about how to fix the drivers if Google and forum searching fail me.

Thanks guys 
T
Your issue and the issue of that thread are not the same, based on what you've posted as the problem.
But you can easily circumvent loading grub by booting into a livedvd/usb of Ubuntu then mounting the hard drive and editing the grub.cfg file there.
See drs305's post:[https://ubuntuforums.org/showthread.php?t=1904347&p=11586952#post11586952]("https://ubuntuforums.org/showthread.php?t=1904347&p=11586952#post11586952") 
(Actually re=-reading notice the post doesn't open a text editor; and gksudo is no longer installed by default, so use
```
sudo -H gedit /mnt/boot/grub/grub.cfg
```
As stated editing this file is normally not advised, but in some instances it's okay. But only as a one time edit.
> **westie457 said:**
> Welcome tregrrr

Things have changed, the left shift key was used for Grub versions 0.99 and earlier. When Grub2 (1.97 and later) began to be utilised the Grub menu access key was changed to the Esc key.
Shift still works, but only for legacy BIOS-mode, the newer UEFI-mode uses ESC.
> **Autodave said:**
> How about some specs on the machine and video card in it. Have you installed any video drivers yet? Which one(s)?
+1

---

### Post by tregrrr on 2017-09-26
No, I understand that the root cause of the two cases are different, but the symptom is the same (no access to anything once the system goes graphical, cannot cancel the graphical) so while the final treatment plan will be different, the first aid will be the same :-D


I apologize for not including specs originally, I thought I had. I guess I cut it without actually pasting it back in...

Acer Aspire AX3400-e4202
AMD Athalon II X@ 255
3GB shared RAM
nVIDIA GeForce 9200
500GB HDD
1000/100/10 T network adapter on board
sound on board

It is an older all in Wonder box that is being resurrected for word processing and surfing duties


one thing that raises an eyebrow...
> 02:00.0 VGA compatible controller: NVIDIA Corporation C77 [COLOR=#ff0000]**[GeForce 8200] (rev a2)**[/COLOR] (prog-if 00 [VGA controller])
    DeviceName: Onboard Nvidia Graphics
    Subsystem: Acer Incorporated [ALI] C77 [GeForce 8200]
    Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B- DisINTx-
    Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 0
    Interrupt: pin A routed to IRQ 22
    Region 0: Memory at fd000000 (32-bit, non-prefetchable) [size=16M]
    Region 1: Memory at f0000000 (64-bit, prefetchable) [size=128M]
    Region 3: Memory at fa000000 (64-bit, prefetchable) [size=32M]
    Region 5: I/O ports at ec00 [size=128]
    Expansion ROM at 000c0000 [disabled] [size=128K]
    Capabilities: <access denied>
    Kernel driver in use: nouveau
    Kernel modules: nvidiafb, nouveau



I am not sure how the real installation of Ubuntu identified the video card but the case says 9200 not 8200
might that be part of the concern?

---

