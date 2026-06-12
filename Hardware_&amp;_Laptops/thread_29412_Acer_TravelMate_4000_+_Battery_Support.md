---
title: "Acer TravelMate 4000 + Battery Support"
date: 2005-04-24
forum: Hardware &amp; Laptops
---

### Post by daschl on 2005-04-24
Hi!

I installed ubuntu and it works perfect, but theres one thing that doesnt work.

the battery-status.

the system always says it at 0% but i dont know how to install the support?

i read a thread about battery-problems and looked in

/proc/acpi/battery/

but there i didnt find a file !?

i hope someone can help me
thanks in advance, 
daschl

---

### Post by fernando on 2005-04-24
The problem here is that this laptop uses a "Smart Battery", and that kind of battery ain't supported by acpi yet. Got to wait til a version that supports our laptop comes out!!  :-| 

If you need any further advice, just send me a pm ok! 

Att,

Fernando

---

### Post by snop on 2005-04-24
Hi,

There's a project trying to address this issue at [http://sourceforge.net/projects/sbs-linux/](http://sourceforge.net/projects/sbs-linux/)  (there are already patches available).

It would be great if ubuntu merges this patches into the kernel (they aren't declared stable, though).

There are 2 aprox. to this problem: apply this patch to the kernel or load a new DSDT at boot time (Ubuntu has the right patches to load a new DSDT just appending a file to initrd).

I own a Travelmate 4001 wlmi and tried to load a patched DSDT I found at ACPI mailing list ([http://sourceforge.net/mailarchive/message.php?msg_id=10561609](http://sourceforge.net/mailarchive/message.php?msg_id=10561609)) but battery values were no correctly reported :(

SnOp

PD: I don't remember where exactly I found the patched DSDT.

---

### Post by snop on 2005-04-26
[QUOTE=snop]Hi,

There's a project trying to address this issue at [http://sourceforge.net/projects/sbs-linux/](http://sourceforge.net/projects/sbs-linux/)  (there are already patches available).

It would be great if ubuntu merges this patches into the kernel (they aren't declared stable, though).
[/QUOTE]

I'm quoting myself here to say that I was wrong: there is, in fact, a patch at sbs-linux project page but it not for what I thought. The guy at [http://sourceforge.net/projects/sbs-linux/](http://sourceforge.net/projects/sbs-linux/) provides patches for buggy dsdt's.


> 
There are 2 aprox. to this problem: apply this patch to the kernel or load a new DSDT at boot time (Ubuntu has the right patches to load a new DSDT just appending a file to initrd).

I own a Travelmate 4001 wlmi and tried to load a patched DSDT I found at ACPI mailing list ([http://sourceforge.net/mailarchive/message.php?msg_id=10561609](http://sourceforge.net/mailarchive/message.php?msg_id=10561609)) but battery values were no correctly reported :(


Just tried again to patch my dsdt with the latest release and... it seems to work fine this time! There's just a minor lag when refreshing battery status (i.e. it doesn't show up immediately when I switch from AC power to battery).

Worth to give it a try. You may follow the instructions found at [http://www.ubuntu-es.org/node/3028](http://www.ubuntu-es.org/node/3028) (spanish).

Hint: in order to compile iasl compiler from intel you need the package flex-old (instead of flex) as the web mentioned above points.

SnOp

PD: If you encounter problems using this process drop me a line and I'll translate that how-to to English.

---

### Post by adrislayer on 2005-05-01
I have downloaded the patch and I wanted to install it but...

the link is broken. It is not that I doesn't understand spanish, but it's quit difficult with it. And I'm too beginer to try install it without any help.

If you could just copy the tutorial here, I would be pleased.

thanks

---

### Post by ssck on 2005-05-28
I am using Acer Travelmate 2308 with the same problems of battery wrongly reporting the status.Has anybody tried any of the patches and that it works ?

---

### Post by Confuse on 2005-06-19
Would you be able to provide translated instructions still? I'm having trouble understanding some stuff.

[QUOTE=snop]I'm quoting myself here to say that I was wrong: there is, in fact, a patch at sbs-linux project page but it not for what I thought. The guy at [http://sourceforge.net/projects/sbs-linux/](http://sourceforge.net/projects/sbs-linux/) provides patches for buggy dsdt's.




Just tried again to patch my dsdt with the latest release and... it seems to work fine this time! There's just a minor lag when refreshing battery status (i.e. it doesn't show up immediately when I switch from AC power to battery).

Worth to give it a try. You may follow the instructions found at [http://www.ubuntu-es.org/node/3028](http://www.ubuntu-es.org/node/3028) (spanish).

Hint: in order to compile iasl compiler from intel you need the package flex-old (instead of flex) as the web mentioned above points.

SnOp

PD: If you encounter problems using this process drop me a line and I'll translate that how-to to English.[/QUOTE]

---

### Post by snop on 2005-06-19
> Would you be able to provide translated instructions still? I'm having trouble understanding some stuff.

Just download the file found at [https://sourceforge.net/projects/sbs-linux/](https://sourceforge.net/projects/sbs-linux/) and read the README where explains how to use the dsdt patches. Post your specific problems here and I'll try to solve them.

SnOp

---

### Post by daschl on 2006-05-01
Big Ad: With the ubuntu 6.06 beta2 it works out of the box

HOORAY!

*dance*

---

