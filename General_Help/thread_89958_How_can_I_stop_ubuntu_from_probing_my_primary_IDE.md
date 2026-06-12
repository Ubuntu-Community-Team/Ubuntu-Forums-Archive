---
title: "How can I stop ubuntu from probing my primary IDE?"
date: 2005-11-13
forum: General Help
---

### Post by obscenic on 2005-11-13
I have no drives on my primary IDE, and linux takes 3 or 4 minutes to do the IRQ probe.  Bootup is incredibly slow, unbearably so.  I would like it to skip this step - how can I do this?

---

### Post by ranf on 2005-11-14
[QUOTE=obscenic]I have no drives on my primary IDE, and linux takes 3 or 4 minutes to do the IRQ probe.  Bootup is incredibly slow, unbearably so.  I would like it to skip this step - how can I do this?[/QUOTE]
From /usr/src/linux/Documentation/ide.txt:
```
Summary of ide driver parameters for kernel command line
--------------------------------------------------------

 "hdx="  is recognized for all "x" from "a" to "h", such as "hdc".

 "idex=" is recognized for all "x" from "0" to "3", such as "ide1".

 "hdx=noprobe"          : drive may be present, but do not probe for it

 "hdx=none"             : drive is NOT present, ignore cmos and do not probe

```
I'd try none or noprobe.

---

### Post by obscenic on 2005-11-15
Am I going to be rebuilding the kernel?  I found that doc page online (but there's nothing in /usr/scr on my machine at all).  Where is the IDE driver now?

Found  
"idex=noprobe"         : do not attempt to access/use this interface
in that doc, so that's great!  Just don't know where to plop it.

---

### Post by ranf on 2005-11-15
[QUOTE=obscenic]Am I going to be rebuilding the kernel?[/QUOTE]
No no.
[QUOTE=obscenic]I found that doc page online (but there's nothing in /usr/scr on my machine at all).[/QUOTE]
It were on your disk if you had the linux-source installed. That's not required though.

[QUOTE=obscenic]
Found  
"idex=noprobe"         : do not attempt to access/use this interface
in that doc, so that's great!  Just don't know where to plop it.[/QUOTE]
For a test if this has the effect you want do this:
- on bootup you should get the GRUB boot menu.
- hit e to edit the top Linux entry (top of the list by default)
- go to the kernel parameter line hit e again (this is from memory. The line that has something like root=/dev/... in it)
- at the end of the line put in "ide0=noprobe" without the quotes
- hit Enter
- hit b to boot this entry

---

### Post by obscenic on 2005-11-15
I added ide0=noprobe and ide1=noprobe to the end of the kernel param line in both my primary kernel (it probed it anyway) and the "recovery mode" of my primary kernel. (which is 9, k7) It probed again.

I will try again with hda=none and hdb=none...

---

### Post by obscenic on 2005-11-15
Okay, cut out quiet and splash so I could see what was going on. The only other text after the kernel and the root=/dev/hdf/ was "ro" (minus quotes)

I went all out after a few boots and added ide0=none ide0=noprobe ide1=none ide1=noprobe hda=none hda=noprobe hdb=none hdb=noprobe 

AND the bios clearly states that their are no drives there...

And it STILL probes those drives. I can see the line when it starts and it's taking all the extra params I added.... just ignoring them or something...

---

### Post by ranf on 2005-11-15
[QUOTE=obscenic]Okay, cut out quiet and splash so I could see what was going on. The only other text after the kernel and the root=/dev/hdf/ was "ro" (minus quotes)
[/QUOTE]
I'm sorry. I'm running out of ideas.

---

### Post by obscenic on 2005-11-15
located...
> 
The "ide<x>=noprobe" option was found not to work as expected in the in the 2.4.20 code.

The basic problem is that the data structures that describe possible IDE interfaces are initialized to indicate "noprobe" when the option is set at the kernel command line. However, later some drivers reset the value of "noprobe" in the data structures when certain interfaces are detected.

The end result is that (at least in Linux version 2.4.20) the kernel command line processing for "ide<x>=noprobe" has no practical effect.

The desired behavior is that the "noprobe" option will be observed, even if subsequent driver initialization finds out that an interface is actually present. 


and > 
drivers/ide/ide.c: ide_setup() is called early in start_kernel sequence (via parse_options -> checksetup -> __setup() macro mechanism). It calls init_hwif_data to init each interface to "noprobe=1". Then parses cmd line params such as "ide1=noprobe", setting noprobe back to 1.

Later, drivers such as the PCI-IDE bridge driver, at drivers/ide/ide-pci.c: ide_setup_pci_device, resets the value of noprobe according to whether there's a valid interface there:

       hwif->noprobe = !hwif->io_ports[IDE_DATA_OFFSET]; 

This undoes the effect of any "noprobe" cmd line option. 


I suspect ubuntu may be doing something like this.. anyone have any thoughts about fixing this?

---

### Post by obscenic on 2005-11-27
Bump!

This is a serious problem folks, and I swear it can't be totally unsolvable! Where the dev's at?

---

### Post by The Belgain on 2006-02-01
Second that bump.

I need to be able to specify a noprobe parameter in order to be able to use my Highpoint 1540 SATA card on Ubuntu.

Another question: the drives I need to disable probing for are ide2 - ide5 (hde - hdl), but the noprobe options are apparently only recognised upto ide3 (hdh) - is this correct?

---

### Post by obscenic on 2007-06-26
I ended up solving this (I think....) by discovering setting all of my primary IDE that weren't used to "none" rather than auto.  A linux solution never appeared...

---

