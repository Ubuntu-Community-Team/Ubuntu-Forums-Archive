---
title: "[SOLVED] Can't change monitor resolution -- help!!"
date: 2008-10-29
forum: General Help
---

### Post by alberto ferreira on 2008-10-29
I have Ubuntu 8.04 installed and when I try to change resolutions the only ones available are 640x480 and 800x600. But I know that I can change it to at least 1024x768 because in Gutsy that was my resolution.


 [http://www.conita.com/Computers/Hewlett-Packard-Computers/196.html](http://www.conita.com/Computers/Hewlett-Packard-Computers/196.html):
> [SIZE=1][I]The display of the HP Compaq Presario 1200 also has an HPA passive matrix integrated display type with a max resolution of 800 x 600 SVGA.  Although it does not offer a widescreen display, it does have 16-bit, 64k colours colour support.  It also includes the Trident graphics processor and CyberBlade i7 AGP 2x.  In addition it has Shared Video Memory (UMA) and supports a number of display graphics. These graphics include 
VGA (640 x 480), SVGA (800 x 600), XGA (1024 x 768 ), and SXGA (1280 x 1024).[/I][/SIZE]**I have tried with no avail:**
*xrandr
*adding Modeline "1024x768" ..... to xorg.conf's Monitor section

sudo lshw -C display:
>   *-display UNCLAIMED
       description: VGA compatible controller
       product: CyberBlade i1
       vendor: Trident Microsystems
       physical id: 0
       bus info: pci@0000:01:00.0
       version: 6a
       width: 32 bits
       clock: 66MHz
       capabilities: agp agp-1.0 pm vga_controller bus_master cap_list
       configuration: latency=64[COLOR=Blue]*How can I change resolution to XGA (1024 x 768 ) or SXGA (1280 x 1024)?
*Currently it's using VESA driver. Does it have to be replaced with trident-driver or whatever it's name is?[/COLOR]

---

### Post by SuperSonic4 on 2008-10-29
I think you need the propriatory drivers, what kind of card do you have?

---

### Post by alberto ferreira on 2008-10-29
Integrated card from Intel, > Trident graphics processor and CyberBlade i7 AGP 2x. 

---

### Post by alberto ferreira on 2008-10-29
help!! bump

---

### Post by aeronotix on 2008-10-29
Have you tried plugging in a different monitor? I have Hardy 8.04 and I use two monitors for different things when I plug in my Samsung 40" the display settings go upto 1360x768 (Something like that anyway) and the other one can only use smaller resolutions.

---

### Post by alberto ferreira on 2008-10-29
Thanks guys I used "gksu displayconfig-gtk" to manually edit my monitor so now I'm at 1024x768!

---

### Post by SirScott13 on 2009-04-03
> **alberto ferreira said:**
> Thanks guys I used "gksu displayconfig-gtk" to manually edit my monitor so now I'm at 1024x768!

Ok, that doesn't seem to do anything for me.  I am having the same problem.  I have tried several of the solutions.  In addition to the smalller screen, when I try to open up my xorg.conf file, it is completely blank.  Not just headers, nothing at all.

---

### Post by boof1988 on 2009-04-03
> **SirScott13 said:**
> <snip> when I try to open up my xorg.conf file, it is completely blank.  Not just headers, nothing at all.

If you are using nano (or maybe other editors as well), you may be creating the file rather than opening it if the path and name are not correct.

One way to look for the file before opening (editing) it is to use *ls*.

This will show all the files in root [/]...
```
ls -al /
```

This will show the files in /etc...
```
ls -al /etc/
```

This will show the files in /etc/X11 (Where my xorg.conf file is located)...
```
ls -al /etc/X11/
```

I'm not sure if this is where all xorg.conf's are located or not.

Hope this helps.

---

