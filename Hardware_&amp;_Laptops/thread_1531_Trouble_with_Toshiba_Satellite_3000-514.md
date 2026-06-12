---
title: "Trouble with Toshiba Satellite 3000-514"
date: 2004-10-21
forum: Hardware &amp; Laptops
---

### Post by harvie_krumpet on 2004-10-21
Hello there!
First of all, I want to thank the people that put UBUNTU together - you did a great job! Especially my notebook turned out to be really troublesome under any distribution that I had tried out so far. But with UBUNTU the Netgear WLAN card and the AC'97 worked out of the box, and installling the NVIDIA driver was a piece of cake thanks to the howto!
But I'm still left with a few problems - and I'd greatly appreciate any help on these issues!

ad 1.)
The built-in WinModem is an Askey 1456VQL4(INT) (Lucent SCORPIO). It has been reported to work with the slmdm softmodem driver, which are not yet including from what I understood...
How can I get it to work?   'lspci -V'  reports:
```
0000&#58;00&#58;1f.6 Modem&#58; Intel Corp. 82801CA/CAM AC'97 Modem Controller &#40;rev 01&#41; &#40;prog-if 00 &#91;Generic&#93;&#41;
        Subsystem&#58; Toshiba America Info Systems Toshiba Satellite 1110 Z15 internal Modem
        Flags&#58; bus master, medium devsel, latency 0, IRQ 10
        I/O ports at 2400
        I/O ports at 2000 &#91;size=128&#93;
```
ad 2.) 
The notebook has a built-in smartmedia-cardreader (Toshiba TC6371AF) which I use quite frequently... Any idea how I can get this to work? It would be sad to have to leave M$ XP on a partition just to be able to read the pictures from the digicam (I lost the USB cable a long time ago)!
Here's more from  'lspci -V':
```
0000&#58;02&#58;06.0 System peripheral&#58; Toshiba America Info Systems TC6371AF SmartMedia Controller &#40;rev 02&#41;
        Subsystem&#58; Toshiba America Info Systems&#58; Unknown device ff00
        Flags&#58; slow devsel, IRQ 9
        Memory at d2004c00 &#40;32-bit, non-prefetchable&#41;
        Capabilities&#58; &lt;available only to root&gt;
```
ad 3.)
And this one is kind of stupid, because Toshiba could and should have fixed this forever... The notebook's bios is buggy, respectively it's DSDT table. Unfortunately, this prevents ACPI from working properly. I don't mind not being able to suspend to disk, but I could really use the PIII-M's speedstep. But worst of all: the battery status cannot be determined correctly!
FWIU the only way to fix this might be compiling a kernel with the proper patch, right? If so, is there a howto somewhere that I haven't seen yet where I can see what patches have to be applied to which kernel? And maybe even a kernel config?

Thanks a lot in advance!

---

