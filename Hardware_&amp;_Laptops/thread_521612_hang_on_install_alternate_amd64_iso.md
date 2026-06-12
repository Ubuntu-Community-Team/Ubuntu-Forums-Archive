---
title: "hang on install: alternate amd64 iso"
date: 2007-08-09
forum: Hardware &amp; Laptops
---

### Post by stabu on 2007-08-09
Hi,

I have a Clevo laptop MJ55 running a turion(x1) 64 proc, nvidia mobo, and I can't install the amd64 feisty on it because each time the screen seems to hang along with the whole pc.

To be honest, pretty much nothing installs on this computer (except slackware and an old version of knoppix) because each time the installation prog wants to do something fancy with the screen, it all clogs up. I'm pretty definite it's got something to do with the graphics driver which is (as lspci reports it):
```

00:05.0 VGA compatible controller: nVidia Corporation C51 PCI Express Bridge (rev a2) (prog-if 00 [VGA])
	Subsystem: CLEVO/KAPOK Computer Unknown device 5403
	Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 10
	Memory at c2000000 (32-bit, non-prefetchable) [size=16M]
	Memory at d0000000 (64-bit, prefetchable) [size=256M]
	Memory at c1000000 (64-bit, non-prefetchable) [size=16M]
	[virtual] Expansion ROM at 52000000 [disabled] [size=128K]
	Capabilities: [48] Power Management version 2
	Capabilities: [50] Message Signalled Interrupts: 64bit+ Queue=0/0 Enable-

```
I was trying the normal Fesity amd64 before and it never worked either. It would hang more horribly. SO I thought with the text based alternate amd64 iso I'd be OK.

Well, the installation procedure with the text based interface gets farther than the graphics installer, but it does hang after it finishes installing language stuff and some 500M worth of uncompressed files. It gets past the proxy question too. When it hangs, I get the faint idea that  the text installer maybe  trying out some vga modes on it.

You see, I thought the text installer would expect the user to set up X manually. Would I be right in saying it doesn't?

---

### Post by hamburglar6 on 2007-08-10
The text based installer also configures X automatically.  In my experience the only difference in installation with the alternate cd is that it goes faster.  

are you able to change your video device in your bios?  if you can try disabling your video card and using what the motherboard has to offer while installing, and then switching back afterwards.  if that doesn't work you could also try installing the server version of ubuntu and then doing a sudo apt-get install ubuntu-desktop.  that being said, i have absolutely no experience with server installs- if anybody else has something more intelligent to say about that by all means speak up.

---

### Post by stabu on 2007-08-10
Hi hamburglar6,

Ref. BIOS that sounds like good advice, though I have my doubts, I will try.

Thanks for confiming text based installer. Confirms my feeling that Ubuntu is a bit anti-command line. Not much, but a little.

Cheers!

---

