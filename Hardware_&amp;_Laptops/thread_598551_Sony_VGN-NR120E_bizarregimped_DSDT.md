---
title: "Sony VGN-NR120E bizarre/gimped DSDT"
date: 2007-10-31
forum: Hardware &amp; Laptops
---

### Post by tscook on 2007-10-31
Crossposted at [http://bbs.archlinux.org/viewtopic.php?pid=294716#p294716](http://bbs.archlinux.org/viewtopic.php?pid=294716#p294716) since this is less distro dependent rather than bios bizarreness. 

Following the instructions in [http://www.linux.it/~malattia/wiki/index.php/Sony-laptop](http://www.linux.it/~malattia/wiki/index.php/Sony-laptop) yielded nothing, so I went through [http://tjworld.net/snc/](http://tjworld.net/snc/)'s directions  to submit my DSDT. Looking over it myself, it seemed suspect so I tried the analysis scripts here [http://tjworld.net/snc/sourcecode.html](http://tjworld.net/snc/sourcecode.html) and none of the methods sony_acpi/sony-laptop work with were detected (!?). The full results along with the DSDT.aml and DSDT.dsl are available at [http://skrrgh.googlepages.com/vgn-nr120e-analysed.tar.gz](http://skrrgh.googlepages.com/vgn-nr120e-analysed.tar.gz). Any insight would be appreciated.

As far as I can tell this is what's going on:

SNC is nonfunctional if you're not running Vista
```
                Device (SNC)
                {
                    Name (_HID, EisaId ("SNY5001"))
                    Method (_INI, 0, NotSerialized)
                    {
                        If (_OSI ("Windows 2006"))
                        {
                            And (ENMK, 0xFFBF, ENMK)
                            And (SNIA, 0xFFFD, SNIA)
                            Or (SNIA, 0x40, SNIA)
                            If (And (SYID, 0x80)) {}
                            Else
                            {
                                Store (0x394A0000, SNI4)
                            }
```

Sound plays both through headphones and onboard speakers? This looks suspect.
```
    Scope (_SB)
    {
        Method (_INI, 0, NotSerialized)
        {
            Store (0x07D0, OSYS)
            If (CondRefOf (_OSI, Local0))
            {
                If (_OSI ("Linux"))
                {
                    Store (One, LINX)
                }
```

Is this just not going to work with sony-laptop? WTF

---

