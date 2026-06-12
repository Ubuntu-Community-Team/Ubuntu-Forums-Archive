---
title: "Random freezes getting rediculous"
date: 2009-01-29
forum: Hardware
---

### Post by Just-trevor on 2009-01-29
Pretty often my computer will completely freeze up.

It usually seems pretty unprovoked; I don't usually have tons of programs running at once, and my average RAM usage is like 20% or less.

These random freezes have only started recently; this is a pretty fresh installation of Ubuntu Hardy, I think less than a month old.

I put this under Hardware and Laptops because I think it is a hardware problem, because these random freezes happened back when I had Windows, then again on a new hard drive with Ubuntu, but only towards when it crashed totally..., and with another new hard drive now.

Pretty often it will freeze when it goes into the screensaver, this happened a lot on my hard drive before this one, too, when I had a sucky graphics card - it would freeze even when I looked for a screensaver in the screensaver chooser.

This newer graphics card runs Compiz now, but I don't think that Compiz is the cause, even though sometimes it will freeze doing Compiz things like spinning the cube, which just happened a little bit ago.

I have the screensaver set to the flying windows, but if I lock the screen it goes to the not-compiz one I had set, which I set to no screensaver, and it still freezes on a black blank screensaver.

Here is my hardware:

```
root@trevor3:/home/trevor# lspci -v
00:00.0 Host bridge: nVidia Corporation nForce2 IGP2 (rev c1)
	Flags: bus master, 66MHz, fast devsel, latency 0
	Memory at e0000000 (32-bit, prefetchable) [size=64M]
	Capabilities: [40] AGP version 3.0
	Capabilities: [60] HyperTransport: Host or Secondary Interface

00:00.1 RAM memory: nVidia Corporation nForce2 Memory Controller 0 (rev c1)
	Subsystem: Biostar Microtech Int'l Corp Unknown device 1400
	Flags: 66MHz, fast devsel

00:00.2 RAM memory: nVidia Corporation nForce2 Memory Controller 4 (rev c1)
	Subsystem: Biostar Microtech Int'l Corp Unknown device 1400
	Flags: 66MHz, fast devsel

00:00.3 RAM memory: nVidia Corporation nForce2 Memory Controller 3 (rev c1)
	Subsystem: Biostar Microtech Int'l Corp Unknown device 1400
	Flags: 66MHz, fast devsel

00:00.4 RAM memory: nVidia Corporation nForce2 Memory Controller 2 (rev c1)
	Subsystem: Biostar Microtech Int'l Corp Unknown device 1400
	Flags: 66MHz, fast devsel

00:00.5 RAM memory: nVidia Corporation nForce2 Memory Controller 5 (rev c1)
	Subsystem: Biostar Microtech Int'l Corp Unknown device 1400
	Flags: 66MHz, fast devsel

00:01.0 ISA bridge: nVidia Corporation nForce2 ISA Bridge (rev a4)
	Subsystem: Biostar Microtech Int'l Corp Unknown device 3400
	Flags: bus master, 66MHz, fast devsel, latency 0
	Capabilities: [48] HyperTransport: Slave or Primary Interface

00:01.1 SMBus: nVidia Corporation nForce2 SMBus (MCP) (rev a2)
	Subsystem: Biostar Microtech Int'l Corp Unknown device 3400
	Flags: 66MHz, fast devsel, IRQ 11
	I/O ports at e400 [size=32]
	Capabilities: [44] Power Management version 2

00:02.0 USB Controller: nVidia Corporation nForce2 USB Controller (rev a4) (prog-if 10 [OHCI])
	Subsystem: Biostar Microtech Int'l Corp Unknown device 3400
	Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 17
	Memory at e8003000 (32-bit, non-prefetchable) [size=4K]
	Capabilities: [44] Power Management version 2

00:02.1 USB Controller: nVidia Corporation nForce2 USB Controller (rev a4) (prog-if 10 [OHCI])
	Subsystem: Biostar Microtech Int'l Corp Unknown device 3400
	Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 18
	Memory at e8004000 (32-bit, non-prefetchable) [size=4K]
	Capabilities: [44] Power Management version 2

00:02.2 USB Controller: nVidia Corporation nForce2 USB Controller (rev a4) (prog-if 20 [EHCI])
	Subsystem: Biostar Microtech Int'l Corp Unknown device 3400
	Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 16
	Memory at e8005000 (32-bit, non-prefetchable) [size=256]
	Capabilities: [44] Debug port
	Capabilities: [80] Power Management version 2

00:04.0 Ethernet controller: nVidia Corporation nForce2 Ethernet Controller (rev a1)
	Subsystem: Biostar Microtech Int'l Corp Unknown device 2301
	Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 16
	Memory at e8000000 (32-bit, non-prefetchable) [size=4K]
	I/O ports at d000 [size=8]
	Capabilities: [44] Power Management version 2

00:06.0 Multimedia audio controller: nVidia Corporation nForce2 AC97 Audio Controler (MCP) (rev a1)
	Subsystem: Biostar Microtech Int'l Corp Unknown device 8201
	Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 17
	I/O ports at d400 [size=256]
	I/O ports at d800 [size=128]
	Memory at e8001000 (32-bit, non-prefetchable) [size=4K]
	Capabilities: [44] Power Management version 2

00:08.0 PCI bridge: nVidia Corporation nForce2 External PCI Bridge (rev a3) (prog-if 00 [Normal decode])
	Flags: bus master, 66MHz, fast devsel, latency 0
	Bus: primary=00, secondary=01, subordinate=01, sec-latency=32
	I/O behind bridge: 0000c000-0000cfff
	Memory behind bridge: e7000000-e7ffffff

00:09.0 IDE interface: nVidia Corporation nForce2 IDE (rev a2) (prog-if 8a [Master SecP PriP])
	Subsystem: Unknown device f565:3400
	Flags: bus master, 66MHz, fast devsel, latency 0
	[virtual] Memory at 000001f0 (32-bit, non-prefetchable) [disabled] [size=8]
	[virtual] Memory at 000003f0 (type 3, non-prefetchable) [disabled] [size=1]
	[virtual] Memory at 00000170 (32-bit, non-prefetchable) [disabled] [size=8]
	[virtual] Memory at 00000370 (type 3, non-prefetchable) [disabled] [size=1]
	I/O ports at f000 [size=16]
	Capabilities: [44] Power Management version 2

00:1e.0 PCI bridge: nVidia Corporation nForce2 AGP (rev c1) (prog-if 00 [Normal decode])
	Flags: bus master, 66MHz, medium devsel, latency 32
	Bus: primary=00, secondary=02, subordinate=02, sec-latency=32
	Memory behind bridge: e4000000-e6ffffff
	Prefetchable memory behind bridge: d0000000-dfffffff

01:06.0 Multimedia audio controller: C-Media Electronics Inc CM8738 (rev 10)
	Subsystem: C-Media Electronics Inc CMI8738/C3DX PCI Audio Device
	Flags: bus master, medium devsel, latency 32, IRQ 20
	I/O ports at c000 [size=256]
	Capabilities: [c0] Power Management version 2

01:07.0 Network controller: RaLink RT2561/RT61 802.11g PCI
	Subsystem: RaLink EW-7108PCg
	Flags: bus master, slow devsel, latency 32, IRQ 19
	Memory at e7000000 (32-bit, non-prefetchable) [size=32K]
	Capabilities: [40] Power Management version 2

02:00.0 VGA compatible controller: nVidia Corporation NV44A [GeForce 6200] (rev a1) (prog-if 00 [VGA controller])
	Subsystem: XFX Pine Group Inc. Unknown device 213f
	Flags: bus master, 66MHz, medium devsel, latency 248, IRQ 21
	Memory at e4000000 (32-bit, non-prefetchable) [size=16M]
	Memory at d0000000 (32-bit, prefetchable) [size=256M]
	Memory at e5000000 (32-bit, non-prefetchable) [size=16M]
	[virtual] Expansion ROM at e6000000 [disabled] [size=128K]
	Capabilities: [60] Power Management version 2
	Capabilities: [44] AGP version 3.0


```

OK, so thats all I can think to tell you all for now, but I'm trying to do this quickly before the computer freezes again...

Thanks in advance! :guitar:

---

### Post by Yashiro on 2009-01-29
Test your ram with memtest.

---

### Post by Just-trevor on 2009-01-30
I ran memtest for 17 hours and it passed 14 times with no errors...
I have also gotten new ram (two one gigs) since my other hard drives and the problem has persisted with the new ram, so I don't think that's the problem

---

### Post by dabl on 2009-01-30
Use top or htop to list the running processes in a console window.  Place that window on the screen where you can watch it.  When your computer "freezes", what process is sucking up all the resources?  That's your bad boy.  Then you can focus on why.  :)

---

### Post by Just-trevor on 2009-01-30
K, I stuck a line on conky showing the program that's using the most rescources, but I don't think it will help much because it usually freezes because of something to do with the screensaver, although there are some exceptions...

Yeah, and it froze three times before I could add the line on conky and post this... that's how obnoxious this is getting.

---

### Post by electrogeist on 2009-01-30
Do you have the latest BIOS revision for your motherboard?  IIRC some of the earlier nforce2 boards had some issues that this might fix

This is potentially risky if you have frequent freezes tho...a freeze during flash may require buying a replacement chip, unless there is an emergency flash jumper on the motherboard.  Being able to run memtest for 17 hours leads me to believe you'll probably be ok flashing in DOS.  Probably.

You could also try disabling/pulling the audio and network, via BIOS settings if they're integrated.

Aside from that I would be pointing a finger at the motherboard or power supply.

---

### Post by Just-trevor on 2009-01-30
for some reason the computer is better now

I have no idea why...

I think I replaced the power supply a little while ago, so it should be working still, but the mother board is pretty old...

I can't think of what the problem possibly could have been, but it is better now.

It fixed itself, I guess...

I might need to reopen this thread in a bit, if the freezes come back, but oh well.

Thanks :)

---

### Post by superjavi on 2009-01-30
Most probably you have a problem with your chipset, the nVidia one.

In my experience, those chipsets are not very much stable, and tend to overheat.

---

### Post by Just-trevor on 2009-03-29
I'm gonna go ahead and re-open this thread.

Freezes still rediculous

All of the different annoying things that keep happening every two minutes are:
- Complete freezes with caps lock and scroll lock flashing on the keyboard
- Complete freezes without any flashing lights
- Sudden black screen with the first few logging out lines it shows when logging out showing, but nothing happens
- Starts to shut down and shows the first few shutting down lines but it never shuts down all the way
- Complete Firefox freezes but I can close the window and start over with the same session
- Firefox quits out but I can open a new one and start from the same session
- Compiz gets disabled and I have to enable all of the non-default plugins again after I enable it again
- Bar on all the windows with maximize and exit on it (I forget what it's called) disappears when I maximize windows sometimes

When booting up instead of loading the grub it shows some stuff about my mobo or something and says system boot failure and I have to shut it down and start again sometimes

On brand new installations on Ubuntu these problems don't really start until I install the nvidia driver and gstreamer

Usually freezes when using flash on Firefox but not always - freezes with limewire and when logging in too.  Also freezes with screensaver still.

I got a new graphics card since last post

Any ideas at all anybody has on what is causing these problems or what I can do to fix them will be really great

---

### Post by Just-trevor on 2009-04-04
uh... bump...

The freezing problem comes pretty consistently after about two minutes of running any flash at all, and frequently when loading gnome, and not really ever other than that, usually.

sometimes when there are lots of windows up it happens again, or when i'm playing with compiz things like wobbly windows or paint fire.
when I disable compiz all the other problems persist

It is basically impossible to do anything fun on this computer...

Any ideas at all that anybody has would be really appreciated, I'm really going crazy.

---

### Post by Just-trevor on 2009-04-09
I feel kind of guilty, but bump again

Everything runs perfectly and then out of the blue it freezes, after maybe an average of 3 minutes, including the less than a minute it takes to boot up and log in

I found a few people with very similar problems, but from a few years ago, and I couldn't really find anything to help

Any suggestions at all please - any new parts that might help, or whatever - I want to know if there possibly any way to fix it

---

### Post by Just-trevor on 2009-04-23
Bump again
I upgraded to Jaunty but the problems are only a little less severe

What hardware could I buy that would maybe help?

I think I'll try upgrading my processor, but I don't want to spend the money on a new one if it probably won't help

---

### Post by Just-trevor on 2009-04-26
It froze during the start-up and the message was

[1.240933] Kernel Panic: Not Syncing - Tried to delete init!

Or something very similar.

Any ideas at all?

It freezes more and more often the longer I go without a fresh install.

---

### Post by vincent orange on 2009-05-24
I've been experiencing the exact same issues. I have an Abit AN7 mobo (Nvidia 430 chipset..i think). I thought it was RAM issue...memtest told me otherwise. I then thought it was a PCI USB Card issue that I had installed a few weeks ago...problem persisted even with this piece of kit out of the machine.

I've seen this issue with Hardy and Jaunty...other releases are fine IMHO.

Sorry, I can't be of help, but letting you know that i've got the same issues too.

I'm thinking it might be a hardware issue as my pc is 5 years old now...but i can't see how age is responsible for this when the hardware is kept in good condition most of the time.

edit: I had a good look at the mobo during operation, the fan for the chipset isn't working and not cooling it down....freeze *might* be down to this. will see if i can replace and then investigate.


edit: cleaned the whole system..got the Northbridge fan working again...lock up continued. I have tried running a Live CD to source a similar error. Nothing so far. Seems like a software issue on the installed version of ubuntu.

Have you looked through your system messages? System > Adminsitrator > Logs. then scroll down to Messages.

---

### Post by Just-trevor on 2009-06-15
Yah, thanks for the reply, orange. I googled the problems one time and got a few results from a while ago that were exactly the same as mine - it seems like it's a somewhat common thing.

Sorry I didn't reply for a while... Nobody said anything for like 4 months so I gave up checking.

I also gave up on my computer. I bought a new one and it's working great. I went a little crazy and made it way better than necessary so it never ever ever ever ever ever freezes ever. I'm gonna sell the old one on craigslist or whatever.

Try running Debian Lenny and see if the problems persist. I never tried it, but I should have.

---

