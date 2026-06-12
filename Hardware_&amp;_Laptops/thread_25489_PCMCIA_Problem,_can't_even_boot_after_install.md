---
title: "PCMCIA Problem, can't even boot after install"
date: 2005-04-10
forum: Hardware &amp; Laptops
---

### Post by nborde on 2005-04-10
Hi,

I'm new to this forum. I tried to install Ubuntu on my laptop MANY times. First I tried Warty, then Hoary... And still have a problem.

It seems that my Card reader isn't compatible with this distribution. The last thing I can read at boot is :

```

* Starting PCMCIA services
cs: IO Port probe 0x0100-0x04FF: excluding 0x4d0-0x4d7
cs: IO Port probe 0x0800-0x08FF

```

of course this prints only when I'm on debug mode. Otherwise I only read ** Starting PCMCIA services* :(

I can't solve that problem and didn't find anything on the Internet. I installed my ubuntu with these parameters :

```

expert vga=771 hw-detect/stat_pcmcia=false

```

So no problem for the installation itself (I also need to disable the Card reader starting)
But I haven't found ANYTHING to prevent that PCMCIA something from starting after the installation reboot :/

Do you have any idea ?

My laptop : Toshiba M30X-42 (Centrino Pentium M 725)

---

### Post by az on 2005-04-10
File a bug report.

[https://bugzilla.ubuntu.com/](https://bugzilla.ubuntu.com/)

---

### Post by nborde on 2005-04-12
submited...

[http://bugzilla.ubuntu.com/show_bug.cgi?id=9101](http://bugzilla.ubuntu.com/show_bug.cgi?id=9101)

---

### Post by az on 2005-04-12
You rock.

---

### Post by moa on 2005-04-13
Have same problem with my Sony viao PCG-795P laptop. 

Using linux vga=771  hw-detect/stat_pcmcia=false does not work: it freezes in the same place. 

chris

QUOTE=nborde]Hi,

I'm new to this forum. I tried to install Ubuntu on my laptop MANY times. First I tried Warty, then Hoary... And still have a problem.

It seems that my Card reader isn't compatible with this distribution. The last thing I can read at boot is :

```

* Starting PCMCIA services
cs: IO Port probe 0x0100-0x04FF: excluding 0x4d0-0x4d7
cs: IO Port probe 0x0800-0x08FF

```

of course this prints only when I'm on debug mode. Otherwise I only read ** Starting PCMCIA services* :(

I can't solve that problem and didn't find anything on the Internet. I installed my ubuntu with these parameters :

```

expert vga=771 hw-detect/stat_pcmcia=false

```

So no problem for the installation itself (I also need to disable the Card reader starting)
But I haven't found ANYTHING to prevent that PCMCIA something from starting after the installation reboot :/

Do you have any idea ?

My laptop : Toshiba M30X-42 (Centrino Pentium M 725)[/QUOTE]

---

