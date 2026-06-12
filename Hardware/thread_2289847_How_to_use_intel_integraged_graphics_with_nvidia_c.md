---
title: "How to use intel integraged graphics with nvidia card on a desktop."
date: 2015-08-07
forum: Hardware
---

### Post by Chase_Preuninger on 2015-08-07
I am working on cuda development and the prolbem is that I sometimes freeze my display when I run cuda programs.  I want to use my nvidia gtx 960 just for cuda and my intel integrated graphics for display.  To do this I booted into my BIOS and changed to CPU graphics.  However when I booted into ubuntu it appeared that it tired to load the nvidia driver and would not get past some error messages on boot.  How can I use intel graphics while still having my nvidia card for cuda?

---

### Post by Bashing-om on 2015-08-07
Chase_Preuninger; Hello.

My experience with 'cuda' is limited. Hoever, with the Nvidia proprietary driver the function to select the chip set is in the nvidia-settings tool.

Do you have the proprietary Nvidia driver installed ?
```

lspci -vnn | grep -i VGA
sudo lshw -C display
dpkg -l | grep -i nvidia

```
We can expect to what the hardware is, and I expect to see that the 346 version of the Nvidia driver is installed.
If not we do so .

[INDENT][INDENT][INDENT]good results take
[INDENT][INDENT][INDENT]good tools
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by NoWayWin8 on 2015-08-09
>  I booted into my BIOS and changed to CPU graphics
AFAIK the BIOS settings control the on-board (integrated) gpu, not the discrete one.

---

