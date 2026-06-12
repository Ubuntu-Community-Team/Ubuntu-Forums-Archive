---
title: "Dell claims Ubuntu don't support Mini Card drives for M3800 :-("
date: 2015-02-19
forum: Hardware
---

### Post by mark-alan-richards on 2015-02-19
[SIZE=2][FONT=arial]I have been scoping out a laptop for work and found the Dell Precision M3800 was probably an alright option.

It seems (from the configurator) that you can install an extra long battery by not using the typical SATA SSDs but instead choose something like their:
"1TB mSATA Solid State Drive designed for installation in Mini-Card Slot"

However when I select this, I see the message:
[/FONT][/SIZE][TABLE]
[TR]
[TD="class: val_errors_header, colspan: 2"]Errors:
[/TD]
[/TR]
[TR]
[TD="class: val_bullet_cl"][IMG]http://i.dell.com/images/global/config/bullet-s-blk.gif[/IMG][/TD]
[TD="class: val_msg"]Ubuntu is not compatible with Mini Card Drives. Please use the highlighted links to amend your selections.
[/TD]
[/TR]
[/TABLE]
[SIZE=2][FONT=arial]
Has anyone tried this or know more? Is this a firmware issue?


[/FONT][/SIZE]

---

### Post by pkolloch2 on 2015-03-12
Actually, that's the only thing preventing me from buying the m3800 still.

Unfortunately, I ask the support and got a confirmation.

If the mSATA drive is the minicard drive, the nit looks like at least one is supported as reported by Ubuntu, though:

[http://www.ubuntu.com/certification/catalog/component/scsi/4932/scsi%3ASAMSUNGSSDPM851mSATA1TB/](http://www.ubuntu.com/certification/catalog/component/scsi/4932/scsi%3ASAMSUNGSSDPM851mSATA1TB/)

---

### Post by astrobob.tk on 2015-04-06
I believe they fixed it or you may not have selected "None" for the 2nd drive.
The thing is that the 2nd drive takes room which the larger battery needs.

This video displays the space the 2nd HDD takes. [https://youtu.be/_0uKhLfmxA4?t=9m6s](https://youtu.be/_0uKhLfmxA4?t=9m6s)
Here he's installing an msata (covered by the orange band) and leaves out the 2nd HDD (though he got a new one!). You can remove the metal bracket and install the larger battery.

P.S.: The 1TB msata costs ~ $1050. I found the samsung one on Amazon for ~$500.

---

