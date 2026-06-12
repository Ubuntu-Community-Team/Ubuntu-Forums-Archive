---
title: "Patch kernel for hardware fix"
date: 2009-03-23
forum: Hardware
---

### Post by Fredvs79 on 2009-03-23
Hi,
 I have a dell 600m that experiences [THIS]("https://bugs.launchpad.net/ubuntu/+source/acpid/+bug/285323") bug related to changing screen brightness and function keys not properly mapping when pushed with certain other keybaord keys. This was determined to be a kernel bug.

There was an upstream kernel patch made by Matthew Garrett in August of 2008. It was commit 61579ba83934d397a4fa2bb7372de9ae112587d5, and info can be found [here]("https://bugs.launchpad.net/ubuntu/+source/gnome-power-manager/+bug/285323/comments/68").

However, as it was found out, this patch code did not fix all computer issues. The problem was laid out [here]("http://linux.derkeiler.com/Mailing-Lists/Kernel/2008-11/msg03803.html"). Apparently there is a different vendor string on different Dell machines, either "Dell Inc." or "Dell Computer Corporation", and the patch only works for those computers with "Dell Inc" in the vendor string. My computer has the other vendor string, "Dell Computer Corporation".

Because of this, a thread was started [here]("http://ubuntuforums.org/showthread.php?t=978973") on ubuntuforums asking for the vendor string from dmidecode to collect ALL the vendor strings possible for Dell hardware. This thread was marked SOLVED in January because enough information was gathered.

I looked at the bug report status page [here]("https://bugs.launchpad.net/ubuntu/+source/gnome-power-manager/+bug/285323/+activity") and there hasn't been any activity since January. The last significant piece of info states that the patch was originally applied to kernel 2.6.27-11.22, but only works on the one vendor string.


What's going on, why isn't this fixed? It isn't committed to anything, I don't see any progress in 2 months. Should I email someone to ask what is going on?  

======== Here's the question ===========

Can I patch my kernel by just changing the code - specifically, the vendor string and product strings - from "Dell inc" to "Dell Computer Corporation" and "Latitude" to "Inspiron 600m" on [this]("https://bugs.launchpad.net/ubuntu/+source/gnome-power-manager/+bug/285323/comments/68") page? How can I just apply code to patch a kernel source?? It looks like I need to do a diff on file atkbd.c

My output of **sudo dmidecode | grep -i -a1 -b1 vendor; sudo dmidecode | grep -i -a1 -b1 "Product Name"**
[I]
523-BIOS Information
540:	Vendor: Dell Computer Corporation
575-	Version: A17
1429-	Manufacturer: Dell Computer Corporation
1470:	Product Name: Inspiron 600m                   
1518-	Version: Not Specified
--
1697-	Manufacturer: Dell Computer Corporation
1738:	Product Name:       
1760-	Version:    
[/I]


Relevant code I need to change
[I]
+ .ident = "Dell Laptop",
                .matches = {
                        DMI_MATCH(DMI_SYS_VENDOR, "Dell Inc."),
- DMI_MATCH(DMI_PRODUCT_NAME, "Latitude"),
+ DMI_MATCH(DMI_CHASSIS_TYPE, "8"), /* Portable */
                },
[/I]

"Dell Inc." becomes "Dell Computer Corporation"
"Latitude" becomes "Inspiron 600m"

Can anyone tell me if I change this in the file atkbd.c and compile a new kernel if I can solve this issue?

---

### Post by Bachstelze on 2009-03-23
Patches are applied using the [font="monospace"]patch[/font] utility and feeding it the pach file on stdin. For example:

```
patch -p0 < foo.patch
```

It should be fairly trivial to modify the patch so it matches your laptop's vendor string, but keep in mind that after you patched your kernel sources, you have to compile thme. That, on the other hand, is not trivial.

---

### Post by Fredvs79 on 2009-03-23
Nevermind. It seems that this is 1) possible, and 2) already implemented in the newest kernel (2.6.27-20)

Thanks for the help. Now I'm onto compiling a new kernel (from source).

---

