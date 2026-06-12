---
title: "thinkpad x31: video remains blank after resume from suspend (Feisty)"
date: 2007-05-04
forum: Hardware &amp; Laptops
---

### Post by matthewn on 2007-05-04
I have a Thinkpad X31 that suspended (and hibernated) just fine with Edgy and Dapper. Since upgrading to Feisty, resume from suspend fails: The screen never comes back on.

I've been crawling all through /etc/acpi looking for something different/new and am coming up short. Can someone out there help me troubleshoot this annoying regression?

---

### Post by benanzo on 2007-05-04
what graphics chip does your machine have?  Some people have been reporting problems with some of the Intel chips not returning from suspend.  have a look here:[http://ubuntuforums.org/showthread.php?t=398381](http://ubuntuforums.org/showthread.php?t=398381)

this is referring to the MacBooks but if they have the same graphics chip as you it is probably related.

---

### Post by matthewn on 2007-05-04
Thanks, but I don't think that's it. My X31 is several years old and has ATI Radeon Mobility M6 LY graphics according to lspci.

---

### Post by twoblackeyes on 2007-06-16
Has anyone found a solution to this? I just upgraded my own X31 to Feisty and am encountering the same problem. Any help would be awesome. Thanks.

---

### Post by szymon_g on 2007-06-16
[http://en.opensuse.org/S2ram#ATI_Graphics_Chipsets](http://en.opensuse.org/S2ram#ATI_Graphics_Chipsets)

is it what you are/was looking for?

---

### Post by matthewn on 2007-06-16
twoblackeyes: I never arrived at a solution; I ended up downgrading my X31 to Edgy. If you can get Feisty to play nice on your machine, please share the recipe. :)

---

### Post by twoblackeyes on 2007-06-17
> I have seen many machines lately that needed the APIC disabled on the kernel command line with "noapic", otherwise they would not resume or behave strange after resume (timer interrupts no longer working etc.), so this is something to try out. It should be no longer necessary with recent kernels, openSUSE 10.2 already should not need it anymore.
[edit]


-From the website linked by szymon--I'll give it a try but I'm not sure how to do what it's asking. Can someone clue me in on how to "disable APIC on the kernel command line" ?

---

### Post by spet on 2007-06-22
Certainly

[LIST=1]
[*]Open the file [FONT="Courier New"]/boot/grub/menu.lst[/FONT]
[*]Near the bottom find the section applicable to your kernel (it starts with [FONT="Courier New"]title[/FONT] and the title you see in the boot menu)
[*]Append [FONT="Courier New"]noapic[/FONT] to the line that starts with kernel
[/LIST]

Here's an example, but beware: I use a custom menu.lst so don't expect yours to look exactly the same.
[LIST]
[*]Before:
[INDENT][FONT="Courier New"]
title           Ubuntu (2.6.22-6-generic)
root            (hd0,1)
kernel          /vmlinuz-2.6.22-6-generic root=/dev/sda7 ro quiet splash vga=0x356
initrd          /initrd.img-2.6.22-6-generic
quiet
savedefault
[/FONT][/INDENT]
[*]After:
[INDENT][FONT="Courier New"]
title           Ubuntu (2.6.22-6-generic)
root            (hd0,1)
kernel          /vmlinuz-2.6.22-6-generic root=/dev/sda7 ro quiet splash vga=0x356 **noapic**
initrd          /initrd.img-2.6.22-6-generic
quiet
savedefault
[/FONT][/INDENT]
[/LIST]
Do to the way Ubuntu manages kernel upgrades you might have to do this every time you update your kernel.

---

