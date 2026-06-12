---
title: "All kinds of problems"
date: 2008-10-19
forum: General Help
---

### Post by TheHybrid520 on 2008-10-19
I've been using ubuntu for 2 days now and I keep coming aross the same problems and it's getting annoying.

One of them is I would just loses all audio and I need to fully shut down and turn on my machine to hear it again for like 2 hours before it goes down again. When I use a music player it won't even play the song when I click it plus youtube (or any video site) won't go passed 2 seconds when I try to play it until I fully restart the system. This goes with problem one.

Problem two is sometimes nothing will work correctly when I try to open up active manager it would just turn black and I have to force quit it, and nothing will open, im, music, firefox. Unless I shut down my computer.

Lastly sometimes I just looks the title bar on applications and I can't move them.

Can anyone help? :KS

---

### Post by shawnrgr on 2008-10-19
Flash+Firefox like to steal the audio from your whole system from time to time.
```
killall firefox && firefox
```

as for all your problems in a whole, try intepid, they fixed a lot of issues.

---

### Post by TheHybrid520 on 2008-10-19
Thank you but it happened again and now I can't access the terminal since it goes black and just forces me to shut down. Now I can't click anything on the top or bottom bar, and a few of my applications just shut down on me.

---

### Post by oldos2er on 2008-10-19
Which version of Ubuntu are you running?

---

### Post by Uchiha_madara on 2008-10-19
> **oldos2er said:**
> Which version of Ubuntu are you running?


Yeah .. that's Right you must to tell us Which version firstly

Second : tell us the Specs of your PC / Laptop and
 Print This Command : and Post as Reply :

code
> lspci -v

and then we study the three things you gave and post the answer...

---

### Post by StooJ on 2008-10-19
Just as a quick note about the title bar, if you hold down the ALT key and click-drag anywhere on the window you can move it about.

So if you lose the title bar off the top of the screen you can drag it back down again.

---

### Post by TheHybrid520 on 2008-10-19
> **Uchiha_madara said:**
> Yeah .. that's Right you must to tell us Which version firstly

Second : tell us the Specs of your PC / Laptop and
 Print This Command : and Post as Reply :

code


and then we study the three things you gave and post the answer...

I'm running off 8.04 (hardy)

I'm running Compaq Persario(sp?)
1 Gb of Ram
8500gt
AMD 64 processor 3500+

Not to sure what you mean by the code, if you mean type in the terminal and c&p the results then I can do that.

Edit:

> 00:00.0 RAM memory: nVidia Corporation C51 Host Bridge (rev a2)
	Subsystem: Hewlett-Packard Company Unknown device 2a3e
	Flags: bus master, 66MHz, fast devsel, latency 0
	Capabilities: <access denied>

00:00.1 RAM memory: nVidia Corporation C51 Memory Controller 0 (rev a2)
	Subsystem: Hewlett-Packard Company Unknown device 2a3e
	Flags: 66MHz, fast devsel

00:00.2 RAM memory: nVidia Corporation C51 Memory Controller 1 (rev a2)
	Subsystem: Hewlett-Packard Company Unknown device 2a3e
	Flags: 66MHz, fast devsel

00:00.3 RAM memory: nVidia Corporation C51 Memory Controller 5 (rev a2)
	Subsystem: Hewlett-Packard Company Unknown device 2a3e
	Flags: 66MHz, fast devsel

00:00.4 RAM memory: nVidia Corporation C51 Memory Controller 4 (rev a2)
	Subsystem: Hewlett-Packard Company Unknown device 2a3e
	Flags: bus master, 66MHz, fast devsel, latency 0

00:00.5 RAM memory: nVidia Corporation C51 Host Bridge (rev a2)
	Subsystem: Hewlett-Packard Company Unknown device 2a3e
	Flags: bus master, 66MHz, fast devsel, latency 0
	Capabilities: <access denied>

00:00.6 RAM memory: nVidia Corporation C51 Memory Controller 3 (rev a2)
	Subsystem: Hewlett-Packard Company Unknown device 2a3e
	Flags: 66MHz, fast devsel

00:00.7 RAM memory: nVidia Corporation C51 Memory Controller 2 (rev a2)
	Subsystem: Hewlett-Packard Company Unknown device 2a3e
	Flags: 66MHz, fast devsel

00:02.0 PCI bridge: nVidia Corporation C51 PCI Express Bridge (rev a1) (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=01, subordinate=01, sec-latency=0
	I/O behind bridge: 0000e000-0000efff
	Memory behind bridge: fdb00000-fdbfffff
	Prefetchable memory behind bridge: 00000000fdc00000-00000000fdcfffff
	Capabilities: <access denied>

00:04.0 PCI bridge: nVidia Corporation C51 PCI Express Bridge (rev a1) (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=02, subordinate=02, sec-latency=0
	I/O behind bridge: 0000c000-0000cfff
	Memory behind bridge: f8000000-fbffffff
	Prefetchable memory behind bridge: 00000000e0000000-00000000efffffff
	Capabilities: <access denied>

00:09.0 RAM memory: nVidia Corporation MCP51 Host Bridge (rev a2)
	Subsystem: Hewlett-Packard Company Unknown device 2a3e
	Flags: bus master, 66MHz, fast devsel, latency 0
	Capabilities: <access denied>

00:0a.0 ISA bridge: nVidia Corporation MCP51 LPC Bridge (rev a3)
	Subsystem: Hewlett-Packard Company Unknown device 2a3e
	Flags: bus master, 66MHz, fast devsel, latency 0

00:0a.1 SMBus: nVidia Corporation MCP51 SMBus (rev a3)
	Subsystem: Hewlett-Packard Company Unknown device 2a3e
	Flags: 66MHz, fast devsel, IRQ 255
	I/O ports at 4c00 [size=64]
	I/O ports at 4c40 [size=64]
	Capabilities: <access denied>

00:0a.2 RAM memory: nVidia Corporation MCP51 Memory Controller 0 (rev a3)
	Subsystem: Hewlett-Packard Company Unknown device 2a3e
	Flags: 66MHz, fast devsel

00:0b.0 USB Controller: nVidia Corporation MCP51 USB Controller (rev a3) (prog-if 10 [OHCI])
	Subsystem: Hewlett-Packard Company Unknown device 2a3e
	Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 16
	Memory at fe02f000 (32-bit, non-prefetchable) [size=4K]
	Capabilities: <access denied>

00:0b.1 USB Controller: nVidia Corporation MCP51 USB Controller (rev a3) (prog-if 20 [EHCI])
	Subsystem: Hewlett-Packard Company Unknown device 2a3e
	Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 17
	Memory at fe02e000 (32-bit, non-prefetchable) [size=256]
	Capabilities: <access denied>

00:0d.0 IDE interface: nVidia Corporation MCP51 IDE (rev a1) (prog-if 8a [Master SecP PriP])
	Subsystem: Unknown device f03c:2a3e
	Flags: bus master, 66MHz, fast devsel, latency 0
	[virtual] Memory at 000001f0 (32-bit, non-prefetchable) [disabled] [size=8]
	[virtual] Memory at 000003f0 (type 3, non-prefetchable) [disabled] [size=1]
	[virtual] Memory at 00000170 (32-bit, non-prefetchable) [disabled] [size=8]
	[virtual] Memory at 00000370 (type 3, non-prefetchable) [disabled] [size=1]
	I/O ports at fd00 [size=16]
	Capabilities: <access denied>

00:0e.0 IDE interface: nVidia Corporation MCP51 Serial ATA Controller (rev a1) (prog-if 85 [Master SecO PriO])
	Subsystem: Hewlett-Packard Company Unknown device 2a3e
	Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 19
	I/O ports at 09f0 [size=8]
	I/O ports at 0bf0 [size=4]
	I/O ports at 0970 [size=8]
	I/O ports at 0b70 [size=4]
	I/O ports at f800 [size=16]
	Memory at fe02d000 (32-bit, non-prefetchable) [size=4K]
	Capabilities: <access denied>

00:0f.0 IDE interface: nVidia Corporation MCP51 Serial ATA Controller (rev a1) (prog-if 85 [Master SecO PriO])
	Subsystem: Hewlett-Packard Company Unknown device 2a3e
	Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 16
	I/O ports at 09e0 [size=8]
	I/O ports at 0be0 [size=4]
	I/O ports at 0960 [size=8]
	I/O ports at 0b60 [size=4]
	I/O ports at f300 [size=16]
	Memory at fe02c000 (32-bit, non-prefetchable) [size=4K]
	Capabilities: <access denied>

00:10.0 PCI bridge: nVidia Corporation MCP51 PCI Bridge (rev a2) (prog-if 01 [Subtractive decode])
	Flags: bus master, 66MHz, fast devsel, latency 0
	Bus: primary=00, secondary=03, subordinate=03, sec-latency=128
	I/O behind bridge: 0000d000-0000dfff
	Memory behind bridge: fde00000-fdefffff
	Prefetchable memory behind bridge: fdd00000-fddfffff
	Capabilities: <access denied>

00:10.1 Audio device: nVidia Corporation MCP51 High Definition Audio (rev a2)
	Subsystem: Hewlett-Packard Company Unknown device 2a3e
	Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 17
	Memory at fe024000 (32-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>

00:14.0 Bridge: nVidia Corporation MCP51 Ethernet Controller (rev a3)
	Subsystem: Hewlett-Packard Company Unknown device 2a3e
	Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 18
	Memory at fe02b000 (32-bit, non-prefetchable) [size=4K]
	I/O ports at f200 [size=8]
	Capabilities: <access denied>

00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
	Flags: fast devsel
	Capabilities: <access denied>

00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
	Flags: fast devsel

00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
	Flags: fast devsel

00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
	Flags: fast devsel

02:00.0 VGA compatible controller: nVidia Corporation GeForce 8500 GT (rev a1) (prog-if 00 [VGA controller])
	Subsystem: eVga.com. Corp. Unknown device c747
	Flags: bus master, fast devsel, latency 0, IRQ 20
	Memory at fa000000 (32-bit, non-prefetchable) [size=16M]
	Memory at e0000000 (64-bit, prefetchable) [size=256M]
	Memory at f8000000 (64-bit, non-prefetchable) [size=32M]
	I/O ports at cf00 [size=128]
	[virtual] Expansion ROM at fbfe0000 [disabled] [size=128K]
	Capabilities: <access denied>

03:0a.0 Communication controller: Agere Systems Unknown device 0620
	Subsystem: Agere Systems Unknown device 0620
	Flags: bus master, medium devsel, latency 32, IRQ 255
	I/O ports at de00 [size=256]
	Capabilities: <access denied>


---

### Post by Sam on 2008-10-19
> **TheHybrid520 said:**
> Not to sure what you mean by the code, if you mean type in the terminal and c&p the results then I can do that.

That's it.

---

### Post by TheHybrid520 on 2008-10-19
Oh okay. Well I edited my previous post with the information.

---

### Post by oldos2er on 2008-10-19
If you're using Pulse Audio, try switching to Alsa.

---

### Post by TheHybrid520 on 2008-10-19
I think I'm on alsa, how can I check?

The audio is being the biggest problem, I can take a screen shot of how even if I press play nothing will play if you want.

---

### Post by oldos2er on 2008-10-19
> **TheHybrid520 said:**
> I think I'm on alsa, how can I check?
  

 Look under the System menu, not sure if it's under Preferences or Administration, but look for "Sound," and whichever you're running, Pulse or Alsa, try switching to the other one.

---

### Post by TheHybrid520 on 2008-10-20
Well okay I'm trying pulse I'll see if I still get that problem, also I've notice some times the terminal won't work and I have to force shut everything, I can't even open firefox or some other browser for it to work.

---

### Post by Retaliation on 2008-10-20
You could try just reinstalling Ubuntu. I had a bunch of little problems that were just bugging the crap outta me, and some that werent so little like the terminal and firefox acting wierd, and I eventually just said screw it and I reinstalled and voila, all problems gone. Been much happier ever since then :)

---

### Post by TheHybrid520 on 2008-10-20
I finally got Ubuntu set with all my software, the only way I'm reinstalling it is if it's guaranteed it will fix all the problems :0

---

