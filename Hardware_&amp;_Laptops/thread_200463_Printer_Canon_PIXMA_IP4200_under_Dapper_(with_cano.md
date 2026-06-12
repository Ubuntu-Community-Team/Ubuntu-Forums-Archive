---
title: "Printer: Canon PIXMA IP4200 under Dapper (with canon drivers)"
date: 2006-06-20
forum: Hardware &amp; Laptops
---

### Post by penguintutor on 2006-06-20
Has anyone been able to get the Canon IP4200 to work under Ubuntu with the Canon Drivers? The packages are supplied as rpms, with instructions for Fedora and SuSe, I installed it with no problems under Mandriva, but have been unsuccessful using Ubuntu. I much prefer Ubuntu to the other distros so would like to get this working.

The driver is available to download from the European site at:
[http://software.canon-europe.com/software/canon_print_filter_for_linuxs24302.asp?model=](http://software.canon-europe.com/software/canon_print_filter_for_linuxs24302.asp?model=)

I installed the packages using 
```

alien -i *.rpm

```

and restarted cups. Then using the Gnome "Add Printer" it appeared to go fine, the new driver was there and everything. When I came to print it just kept pausing the printer, and the printer didn't do anything.

I did get errors (in the log - and sometimes displayed in the printer properties):
> 
No %%BoundingBox: comment in header!

but I can't find what this really means or how to fix it (perhaps some problem with udev, but I'm not sure?)

I've also tried compiling these from source, although it didn't make any differences (I'm not 100% sure that it completely replaced the binary drivers).

The printer does work using TurboPrint, but that's £20, which I'd rather donate towards some open source project rather than funding proprietary drivers.

I'd be grateful if anyone can give some help with this.

PenguinTutor

[Info on getting the printer to work with Mandriva - on my blog](http://www.penguintutor.com/blog/viewblog.php?blog=214)

---

### Post by frogotronic on 2006-06-21
[QUOTE=penguintutor]Has anyone been able to get the Canon IP4200 to work under Ubuntu with the Canon Drivers? The packages are supplied as rpms, with instructions for Fedora and SuSe, I installed it with no problems under Mandriva, but have been unsuccessful using Ubuntu. I much prefer Ubuntu to the other distros so would like to get this working.

The driver is available to download from the European site at:
[http://software.canon-europe.com/software/canon_print_filter_for_linuxs24302.asp?model=](http://software.canon-europe.com/software/canon_print_filter_for_linuxs24302.asp?model=)

I installed the packages using 
```

alien -i *.rpm

```

and restarted cups. Then using the Gnome "Add Printer" it appeared to go fine, the new driver was there and everything. When I came to print it just kept pausing the printer, and the printer didn't do anything.

I did get errors (in the log - and sometimes displayed in the printer properties):

but I can't find what this really means or how to fix it (perhaps some problem with udev, but I'm not sure?)

I've also tried compiling these from source, although it didn't make any differences (I'm not 100% sure that it completely replaced the binary drivers).

The printer does work using TurboPrint, but that's £20, which I'd rather donate towards some open source project rather than funding proprietary drivers.

I'd be grateful if anyone can give some help with this.

PenguinTutor

[Info on getting the printer to work with Mandriva - on my blog](http://www.penguintutor.com/blog/viewblog.php?blog=214)[/QUOTE]


Check the following:

1) That the paper type is "plain" and not NONE

2) The paper size is "Letter"

3) The paper tray is correct.


- CH:wink:

---

### Post by penguintutor on 2006-06-22
Yes checked all those - Although paper is A4 as I'm in the UK.

---

### Post by Steven_B on 2006-06-26
I appear to have the same problem.
```
E [26/Jun/2006:17:29:46 -0400] [Job 221] No %%BoundingBox: comment in header!
E [26/Jun/2006:17:29:46 -0400] PID 15737 (/usr/lib/cups/filter/pstocanonij) crashed on signal 11!
```
The "status" it shows me is: Ready: /usr/lib/cups/filter/pstocanonij failed
Some quick googling around seems to show that the "boundingbox" has something to do with the PostScript input file.
I can actually get the printer to print using the ip4000 and bjc4300 drivers, but there are other problems.

---

### Post by Bobbyw8 on 2007-12-08
I am new to this community.  Where can iIget drivers for my canon BJC4300 Printer.  It only prints in feint and large font from the drivers with my copy of Fedora.

Bobby

---

