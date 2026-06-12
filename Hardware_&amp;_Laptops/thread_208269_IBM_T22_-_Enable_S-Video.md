---
title: "IBM T22 - Enable S-Video?"
date: 2006-07-03
forum: Hardware &amp; Laptops
---

### Post by Charlatat on 2006-07-03
I recently bought a S-Video to RCA cable so I can connect my laptop to my entertainment system.  However, having difficulties with the video (audio works fine).  Have both Windows XP and Dapper on it (dual boot), and neither will send video correctly.  I kinda thought once you connect the cable, it should "just work".  Is there something I'm forgetting to enable? Or what?  Any advice would be appreciated.  Thanks

---

### Post by isharra on 2006-08-05
Unfortunately the savage driver does not auto detect and configure the svideo port. I believe there is a package called s3switch available in the universe repository that will do what you need (as long as the tv format is ntsc and not pal) if it's pal format you need to worry about advanced xorg.conf settings.

---

### Post by bodymind on 2007-07-05
i've PAL, and i can't get it to work.. :( i only get my tv on black & white... when i do:

```
s3switch tv pal 
```
the output is this:
```
$~/devel/tv$ sudo s3switch tv pal
vm86() failed
return = 0x1
eax = 0x00005fbd
ebx = 0xffff0808
ecx = 0x00000000
edx = 0x0000000c
esi = 0x00000000
edi = 0x00000000
ebp = 0x00000fd4
eip = 0x0000c25b
cs  = 0xf000
esp = 0x00000fbc
ss  = 0x1000
ds  = 0x0000
es  = 0x0000
fs  = 0x0000
gs  = 0x0000
eflags  = 0x000b3246
cs:ip = [ e6 70 e6 ed e4 71 c3 53 b7 00 eb 08 53 b7 01 eb ]
Could not set TV state (vm86 failure)
Devices attached:  CRT LCD TV
Devices active:    CRT LCD TV
Current TV format is NTSC

```

---> Current TV format is NTSC WHAAAAAY? :'(

do i need to change anything in xorg.conf cause i've put:
            Option "TVStandard" "PAL"
and on Xorg.log:
             (WW) SAVAGE(0): Option "TVStandard" is not used
i've changed my bios from NTSC to PAL.. but it's the same... :\


plz.. help.. :(:(

---

