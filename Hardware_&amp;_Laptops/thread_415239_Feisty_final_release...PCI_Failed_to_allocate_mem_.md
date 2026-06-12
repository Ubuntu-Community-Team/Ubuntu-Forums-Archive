---
title: "Feisty final release...PCI: Failed to allocate mem resource #6...message on boot up"
date: 2007-04-20
forum: Hardware &amp; Laptops
---

### Post by oobuntoo on 2007-04-20
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+source/xorg/+bug/54294](https://bugs.launchpad.net/ubuntu/+source/xorg/+bug/54294) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				"...PCI: Failed to allocate mem resource #6..." shows up right after selecting kernel to boot.

Is anyone else still getting this message when booting their core 2 dual laptop? It has been there since alpha and beta releases, and still there after the final release. It doesn't seem to have any ill-effect, but very annoying. It's not something you want to show your Windows-friends. Is there any way to hide  this message during boot process?

---

### Post by vobrik29 on 2007-04-22
Have the same problem with Feisty on a Toshiba laptop with a Core Duo proc

---

### Post by brazzmonkey on 2007-04-22
i do get this message as well on a core2duo laptop

---

### Post by medz on 2007-04-23
same error as well on mine...i got a core2duo lappy..and always get this error message popping up

is there a fix ?

---

### Post by UMDGaara on 2007-04-24
I get a similar error as well: Lenovo 3000 n100 core duo 1.8, 7300 go

Everything seems to be working alright though, so I guess it's fine.

---

### Post by oobuntoo on 2007-04-25
This bug is not considered urgent by developer(s), but at least someone knows about it, I think. May be if we add more comments to the bug page to let them know that a lot of laptop users get this bug, they might up the priority on this bug. This bug has been around for a long time, would someone please look into it. Pretty please !!!!:lolflag:

---

### Post by **Jas** on 2007-04-25
I get it to.  Toshiba P100 dual-core.

---

### Post by Tyriel on 2007-04-26
I also get this message on my Toshiba P105 laptop.  As other posters have said it does not seem to cause any issues but is still very annoying to get every single time you boot.

---

### Post by silkstone on 2007-04-29
+1

Get it on Acer laptop with T2300 dual core running Feisty. I've seen numerous posts about this problem on several forums, but I haven't found a fix or even an explanation.

---

### Post by manro on 2007-04-29
Same here!

Core 2 Duo Desktop, Intel motherboard, hope someone find a fix for this, I doesn't seem to affect the system, but surely is annoying! :mad:

---

### Post by robinwilson2 on 2007-04-30
I get the problem too, HP laptop with Core Duo. It doesn't seem to be hurting anything, but it still is a little strange.

---

### Post by drobvice on 2007-05-03
I get this with my toshiba satellite with a pentium m processor.

---

### Post by Patrick He on 2007-05-03
I get the same problem too.
[INDENT]PCI: Failed to allocate mem resource #6:20000@c0000000 for 0000:01:00.0[/INDENT]
My laptop is Toshiba Portege S100. 

There are two others problems:
1. I tried to reboot during installation progress, and the laptop halted during POST.
2. It cannot boot into Ubuntu 7.04 after installation, but it still can boot into Windows XP.

It's all right when I am using Ubuntu 6.10.

---

### Post by hendrakieran on 2007-05-04
I have Lenovo Y400 (Core 2 Duo T5500) + nvidia, and it happens to me too

---

### Post by larry wales on 2007-05-04
I also have this problem, however it's not consistent.  I just installed Fiesty a week ago, on a Toshiba Satellite Pro M 30 laptop.

-larry

---

### Post by neilius on 2007-05-08
Also getting this with my Acer Aspire 1350 laptop. Everything else seems to work properly.

Rgds,

Neil.

---

### Post by qtrey on 2007-05-09
I also have this problem. I have a Zepto Znote 6314W.

---

### Post by arbulus on 2007-05-10
I have this problem also.
HP Netserver E60 Pentium 3 processor with dual processor enabled mobo, only one processor installed.

---

### Post by MikeDK on 2007-05-15
if im not mistaken, this might turn out to be a kernel-bug, hows that for a change.

having a similar problem on a HP pavilion dv9232eu AMD Turion64 X2 TL-52,
theres also another thread, in this subject. search for "failed allocate" and it should be on top

Kind Regards MikeDK

---

### Post by becosses on 2007-05-18
Hi everyone , 
                     I have also the same problem  "Failed to allocate mem resource"  But Here is the solution i have found  to solve  this problem. 

I have a dual core  INTEL SE7500  with 2 x Xeon  2.0 Ghz processor  server .  I found the problem was my raid controler  adaptec Raid 2100S who  crash my system .  

To find it  i replace every periferal  with another HCL OR   who was working before on another computer who run Ubuntu .

If you have a built-in controler(video ,SCSI,etc..) , just desactivate it and try another one. 

Take care also to put a right card on a proper slot .  (You will get error if you put a 32 bit pci cars on a 64 bit pci slot = Failed to allocate mem resource )

For me i put a regular ide hard drive . Now all i need to do it's to find  a proper raid controler to do the job...

Wish to be helpfull for you !!

---

### Post by brazzmonkey on 2007-05-18
becosses,
i don't know if this is related in any way, because most (if not all) users who report this error - including me - own a laptop, not a server/desktop computer. therefore i suppose they don't usually have a raid controler nor additional pci slots...

---

### Post by el3arto on 2007-06-14
> **brazzmonkey said:**
> becosses,
i don't know if this is related in any way, because most (if not all) users who report this error - including me - own a laptop, not a server/desktop computer. therefore i suppose they don't usually have a raid controler nor additional pci slots...

Yes, I have the same message and I've got a Toshiba p100 (that is the european analogue of p105, I think) and Toshiba users are the most part of people that have this problem...
Toshiba is not really Linux friendly!!!

--
el3arto

---

### Post by benhelfman@hotmail.com on 2007-06-17
I get same error message but my system never gets past it to boot

---

### Post by IntuitiveNipple on 2007-06-17
If you check the PCI ID reported in the message you'll be able to identify the device. From my own observations it seems mainly to be Nvidia display adapters on laptop PCs.
```
[    0.192641] PCI: Failed to allocate mem resource #6:20000@c0000000 for 0000:01:00.0

```
This is an Nvidia GeForce Go 7600 in a Sony Vaio VGN-FE41Z.
```
$ lspci -v -s 01:00.0
01:00.0 VGA compatible controller: nVidia Corporation G70 [GeForce Go 7600] (rev a1) (prog-if 00 [VGA])
        Subsystem: Sony Corporation Unknown device 81ef
        Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
        Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Latency: 0
        Interrupt: pin A routed to IRQ 16
        Region 0: Memory at d1000000 (32-bit, non-prefetchable) [size=16M]
        Region 1: Memory at b0000000 (64-bit, prefetchable) [size=256M]
        Region 3: Memory at d0000000 (64-bit, non-prefetchable) [size=16M]
        Region 5: I/O ports at 2000 [size=128]
```

It may be possible to fix via a custom DSDT (Differentiated System Description Table) if the cause is faulty data in the BIOS DSDT.

If there is a widespread problem I'd expect the fix to come via Nvidia notifying the BIOS makers (Phoenix, Award, AMI, etc.) who would/should release BIOS upgrades to the PC manufacturers.

---

### Post by brazzmonkey on 2007-06-18
similar hardware here :
```
01:00.0 VGA compatible controller: nVidia Corporation G70 [GeForce Go 7600] (rev a1) (prog-if 00 [VGA])
        Subsystem: Acer Incorporated [ALI] Unknown device 006c
        Flags: bus master, fast devsel, latency 0, IRQ 16
        Memory at d1000000 (32-bit, non-prefetchable) [size=16M]
        Memory at b0000000 (64-bit, prefetchable) [size=256M]
        Memory at d0000000 (64-bit, non-prefetchable) [size=16M]
        I/O ports at 2000 [size=128]
        Capabilities: <access denied>
```

---

### Post by manro on 2007-06-18
Here too, but mine is a Desktop system with a nVidia GeForce 7950GT!

```
$ lspci -v -s 01:00.0
01:00.0 VGA compatible controller: nVidia Corporation Unknown device 0295 (rev a1) (prog-if 00 [VGA])
        Subsystem: eVga.com. Corp. Unknown device c635
        Flags: bus master, fast devsel, latency 0, IRQ 16
        Memory at 51000000 (32-bit, non-prefetchable) [size=16M]
        Memory at 40000000 (64-bit, prefetchable) [size=256M]
        Memory at 50000000 (64-bit, non-prefetchable) [size=16M]
        I/O ports at 2000 [size=128]
        Capabilities: <access denied>

```

---

### Post by penvzila on 2007-06-18
> **oobuntoo said:**
> This bug is not considered urgent by developer(s), but at least someone knows about it, I think. May be if we add more comments to the bug page to let them know that a lot of laptop users get this bug, they might up the priority on this bug. This bug has been around for a long time, would someone please look into it. Pretty please !!!!:lolflag:

Funny that it's not considered urgent.  Anyone with a relatively new laptop simply cannot install Ubuntu!

---

### Post by penvzila on 2007-06-20
I am getting this bug on the edgy, fiesty, and gutsy livecds and alternate cds.  Having to use windows is frustrating after 2 years of (mostly) having Ubuntu work perfectly.

---

### Post by Grungydan on 2007-06-20
Another one here.  HP dv9000t running Core 2 Duo.

---

### Post by penvzila on 2007-06-20
Here is what I did to fix it:

- installed with the amd64 alternate cd (Fiesty):
          - replace 'quite splash' with noapic nolapic vga=771
- boot failed, so I used the recovery mode.

- from here, I downloaded and installed the NVIDIA drivers (it's the graphics card that was causing this mess for me).  I had to do telinit 3 to get out of runlevel 1.

- restarted gdm.  installed all the updates, booted the new kernel using noapic again.

- had to re-install the nvidia drivers

it now works.  Although, I don't notice any CPU scaling.  Does noapic disable acpi?  I don't really consider this a fix if I can't have my advanced power management controls.

---

### Post by mikewhatever on 2007-06-21
> Funny that it's not considered urgent. Anyone with a relatively new laptop simply cannot install Ubuntu!
penvzila, what are you talking about. The bug has no effect neither on installation, nor on performance. The only harm done is seeing is a stupid line at boot.

---

### Post by brazzmonkey on 2007-06-21
mikewhatever's right, it's nothing but an error message at boot time. Mostly harmless.

---

### Post by Yoeri on 2007-06-21
Error confirmed on
Asus A4K AMD3200+ ATI Radeon 9700 Mobility

---

### Post by penvzila on 2007-06-21
> **mikewhatever said:**
> penvzila, what are you talking about. The bug has no effect neither on installation, nor on performance. The only harm done is seeing is a stupid line at boot.

It has a big effect on installation.  It prevented installation for me.  At least, until I used an alternate install cd, and then used recovery mode to install the latest drivers for my card. 

I realize that in it's previous incarnation, it was quite harmless.  It was a pain in the *** on my new laptop, though.

---

### Post by penvzila on 2007-06-21
> **brazzmonkey said:**
> mikewhatever's right, it's nothing but an error message at boot time. Mostly harmless.


It must have been something else then, and I attributed it to the message because that was the last thing I saw.

---

### Post by brazzmonkey on 2007-06-22
if you do think it prevents you from installing ubuntu, then maybe you should report it
[https://bugs.launchpad.net/ubuntu/+source/xorg/+bug/54294](https://bugs.launchpad.net/ubuntu/+source/xorg/+bug/54294)

---

### Post by applegrew on 2007-06-22
I have HP DV5200TX laptop with Duo Core and NVidia Geforce Go 7400 and a Phoenix Bios and I too get this message everytime I boot.

---

### Post by nickytl on 2007-06-26
I get the message too on a desktop with nvidia 7800gt. The issue is i triple boot with osx86 and windows. After booting into ubuntu i have to power down (not restart or reboot) to get osx to boot. otherwise i get a kernel panic in osx. I guess ubuntu is leaving my video card set in some way osx doesnt like.

---

### Post by lamegaptop on 2007-07-01
I experience this same error at boot:(

I have been under the impression, since 6.10,  that this was related to the "quickplay"  buttons on my HP DV8408us. The DVD and "funny round arrow thing" buttons to the left of my volume buttons. They don't work and I never use them. I got this impression from some forgotten forum a while back.

Now I am wondering if it may be the Nvidia thing mentioned above. Could it be the Turbo cache capability of the Geforce GO 76xx? In other OSs my video card shows 256M main memory and 256M shared. 

Everything works great otherwise. It is annoying to see the error at boot. If I could only just hide the error I would be happier.

---

### Post by drobvice on 2007-07-01
I really don't even care about the error, as it doesn't affect anything.  It would be fine if it were suppressed so you couldn't see it.  It's just a 'fit and finish' kind of thing.

---

### Post by turezky on 2007-07-01
HP Pavilion dv6172ea, GeForce Go 7400...
Same problem...
Is there any way to remove this message?

---

### Post by bangsters on 2007-07-04
I have the same error.  Ubuntu Studio 7.04 (Had feisty to start but i just loved the layout of studio) on a sony vaio sz280p.  i thought at first it was my hardware failing, but i guess i'm not the only one.  anyway, it doesn't seem to have any effects on my notebook.

btw, this is my first post here....a convert from windows lol.... been using windowz from v 3.0 to vista, then just had the last straw as my dual core notebook with 2gb ram runs sluggish under xp and vista which shouldn't have been the case lol....loving every bit of ubuntu!!!! :)  just need to get used to since i've been using centos more on servers rather than debian, but wow just wow! :)

btw anyone got the webcam and fingerprint and hdd shock protector to work?

---

### Post by delbene on 2007-08-27
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/54294](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/54294) [br].[/br] ---------------------------- [br].[/br] [br].[/br]                 [FONT=monospace]Same problem here on an ACER Aspire 5685WLMi with Ubuntu 7.04 64bit (kernel 2.6.20-16-generic):
[   18.172172] PCI: Failed to allocate mem resource #6:20000@d0000000 for 0000:01:00.0
 

- dmesg output posted to bug #54294 in launchpad -

[/FONT]

---

### Post by Some_ux on 2007-08-30
Same story here, (Lenovo core 2 duo).

I agree, definitely not something you want to show to any windows folks. I did and got smirks and giggles :(

If not for 7.04, please address this issue in the next version so i can show my face outside again :popcorn:

---

### Post by Flupoid on 2007-11-13
I've tried to install ubuntu 7.04 and 7.10, first try for me to use ubuntu :(
I also get the "Failed to allocate mem resource #6......." error message, and then my laptop freezes.
Fujitsu Siemens Amilo, AMD turon 64 tl-56, Geforce 8600M GS.

There's no way this is not an urgent flaw!

---

### Post by shiptar76 on 2007-11-14
sony vaio vgn-z2m

shqiptare@shqiptare-laptop:~$ dmesg | grep ailed
[   19.742773] PCI: Failed to allocate mem resource #6:20000@d0000000 for 0000:01:00.0
[    7.000000] PM: Resume from disk failed.
[   15.936000] iTCO_wdt: failed to reset NO_REBOOT flag, reboot disabled by hardware

shqiptare@shqiptare-laptop:~$ lshw -C display
  *-display               
       description: VGA compatible controller
       product: G72M [GeForce Go 7400]
       vendor: nVidia Corporation
       physical id: 0
       bus info: pci@0000:01:00.0
       version: a1
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress vga bus_master cap_list
       configuration: driver=nvidia latency=0 module=nvidia

---

### Post by pwn on 2007-11-14
I get the same error message. Had it in Fiesty, and hoped it'd go away after installing Gutsy, but it didn't.

Core2Duo 2GHz
2GB RAM
GeForce 8600M GT

---

### Post by Daelyn on 2007-11-14
This is very strange.

I have a Hybrid Graphics system in my lappie and when I use the chipset integrated IntelGMA950 GFX at boot, I seem not to get this "could not allocate memory" error.

But, as soon as I switch to the nVidia 7400Go GFX it gives me this error at every startup.

Haven't read through the whole thread, so, I don't know if the issue is reported for people with GMA950 too or not. Well, it haven't caused me any issues yet, just a bit annoying as everyone sez! :P

---

### Post by oobuntoo on 2007-11-17
I think this is kernel-related bug. It's still there in Gutsy. Someone had mentioned in a Heron development thread that the new kernel 2.6.23 fixes this problem. I'm using Fedora 8 with this new kernel on my HP dv6000t laptop and this problem is gone.

---

### Post by oobuntoo on 2007-11-30
The stupid message is gone!!!!!

I was about to compile kernel 2.6.23 but decided to play around with usplash theme first. I installed startupmanager and install new from here: [http://www.gnome-look.org/content/show.php/Usplash+BlackChrome?content=60249](http://www.gnome-look.org/content/show.php/Usplash+BlackChrome?content=60249)

When I reboot my laptop, that message couldn't be seen anymore. It's probably still there, but as long as I can't see it, I can live with that.

---

### Post by jsamarasinghe on 2007-12-12
Get same error.

I'm using an Compaq 8510w Core Duo. I do see in the logs an error regarding irq 22 keeps popping up.

---

### Post by Donskov on 2007-12-12
I have an AMD 64bit desktop that tells me the same thing.

---

### Post by mut80r on 2008-02-04
Problem confirmed on an Alienware m5500 w/ 2.5GB RAM, 2.00GHz Core2Duo CPU and nVIDIA Geforce 7600 Go. Very annoying. Ubuntu 7.10

---

### Post by cryptout on 2008-02-04
Same message Zepto Znote 6224w

---

### Post by Elle Stone on 2008-02-08
same problem here, but with gutsy on a 64-bit tyan server board opteron processor.

---

