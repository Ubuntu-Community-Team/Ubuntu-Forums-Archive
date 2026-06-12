---
title: "Umax Astra 1220p - tried everything, what to do now?"
date: 2004-12-09
forum: Hardware &amp; Laptops
---

### Post by broseman on 2004-12-09
Hello folks!

I tried to get my UMAX Scanner working and failed. I did the job before under Fedora Core 2, so I basically know what to do, especially editing /etc/sane.d/dll.conf

But even after editing /etc/sane.d/umax_pp.conf xsane is not able to find the scanner.

Does anyone have some suggestions?

Thanks in advance,

 broseman

My /etc/sane.d/umax_pp.conf reads:
```
option buffer 2097152
port safe-auto
```

I tried: 
```
port /dev/parport0
option astra 1220
```

My /etc/sane.d/dll.conf lists among others
```
umax
umax_pp
umax1220u
```

---

### Post by broseman on 2004-12-10
Hi!

My scanner is still not running. :-(

But I have some more infos: The problem is the incorrect detecting of the mode of the parallel port! It is set to EPP or ECP+EPP (via BIOS) but neither EPP nor ECP is recognized.

dmesg lists only PCSPP or PCSPP,TRISTATE

```
parport: PnPBIOS parport detected.
parport0: PC-style at 0x378, irq 7 [PCSPP,TRISTATE]
```

It should be

```
parport: PnPBIOS parport detected.
parport0: PC-style at 0x378, irq 7 [PCSPP,TRISTATE,**EPP**]
```

or something like that.

Could anyone please help me?

Regards,

 broseman

---

### Post by polemicz on 2004-12-10
Have you tried scanimage -L from console? What does it say? If it's a usb scanner you may have to do a chmod 777 for the scanner in /proc/bus/usb directory (sorry not on Ubuntu right now so I'm unsure of the rest of the path). There have been some postings on this.

---

### Post by broseman on 2004-12-10
No, it's not an usb scanner (since I'm talking about the parallel port... =) )

Therefore scanimage -L won't find anything - and doesn't do it:

```
scanimage -L
No scanners were identified.
```

I'm pretty sure, that this is a problem of ubuntu. I still have the Fedora Core 2 on the same system and the scanner is working there... The only difference I could find so far is the modes thing.

/proc/sys/dev/parport/parport0/modes reads

under **Ubuntu**
```
PCSPP
```


and under **Fedora**
```
PCSPP,EPP
```

Greetings,

 broseman

---

### Post by LostBear on 2005-12-27
is this any use to you...

[http://umax1220p.sourceforge.net/](http://umax1220p.sourceforge.net/)

---

