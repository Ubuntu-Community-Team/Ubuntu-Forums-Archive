---
title: "Problem with Hibernation !"
date: 2007-02-22
forum: Hardware &amp; Laptops
---

### Post by akshaysrinivasan on 2007-02-22
Hibernation used to work out of the box and beautifully from Breezy ,but from dapper onwards only suspend works ,If i Hibernate ,i just get a blinking white cursor on the Terminal and it returns back to the Locked Screen after a while.My Hardware consists of....
AMD Athlon 2400+
VIA KM400 and VIA 8235 Chipsets on ASUS A7V8X Motherboard.
Anybody know what i must do ?

---

### Post by akshaysrinivasan on 2007-02-22
I just discovered that whenever Edgy ,apparently fails to Hibernate ,it ruins the filesystem on the Swap Partition.Isn't this a Bug?

---

### Post by akshaysrinivasan on 2007-02-22
Update:
I also found that during the process of Hibernation ,it gives out an error...

pnp: Failed to activete device 00:0b
pnp: Failed to activate device 00:0a

Does this make any sense to anyone ?

---

### Post by fulanodetal316 on 2007-02-22
I also have edgy, mine successfully hibernates - at least I think it does - before it hibernates it shows an error message, then powers down.

[17380160.364000] pnp: failed to activate device. 00:06
Power Down.

Does anyone know what this means? Also, is there any way to tell it to wake back up into Ubuntu w/o asking which version I want to wake up too?

---

### Post by robertpolson on 2007-02-22
Hibernation and Suspend do not work for me. Whenever I recover from them all I get is a black screen with the mouse cursor. This seems to be a common Linux problem.

---

### Post by MystaMax on 2007-02-22
I'm having the same problem on a Dell D620 laptop. I'm not sure I used on Dapper, so I can't answer for that.

---

### Post by Rui Pais on 2007-02-22
> **akshaysrinivasan said:**
> I just discovered that whenever Edgy ,apparently fails to Hibernate ,it ruins the filesystem on the Swap Partition.Isn't this a Bug?

Hi, have you add a:
```
resume=/dev/<your_swap_partition_device>
```
to the kernel line of your grub menu.lst?

---

### Post by akshaysrinivasan on 2007-02-22
It seems that pnp stands for Plug and play.When i use the command lspnp it gives out an error..
/proc/bus/pnp not found.

Then i tried removing all USB devices and turning PNP off in the BIOS ,but that didn't at all help.

---

### Post by akshaysrinivasan on 2007-02-22
Eureka! Adding resume=/dev/hda3 ,made the computer return to its previous state.Thanks a lot Ruis.Although ,i have to Hibernate using a program called Hibernate.Clicking on hibernate  does not help i.e Gnome Power Manager does not Hibernate.Any idea why?I still miss Breezy ,everything was great in there

---

### Post by akshaysrinivasan on 2007-02-23
Anybody know how to get the HIbernation support of Breezy back?I know this might sound strange ,it might even be impossible ,since Dapper afterwards we have Gnome power manager managing all the shutdown .....

---

