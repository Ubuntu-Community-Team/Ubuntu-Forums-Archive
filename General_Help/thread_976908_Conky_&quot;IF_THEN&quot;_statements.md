---
title: "Conky &quot;IF THEN&quot; statements"
date: 2008-11-09
forum: General Help
---

### Post by Digitm on 2008-11-09
Does anyone know if/howto do "IF THEN" type statements in Conky. An example of what I am looking for is changing the font color based off variables like:

IF CpuTemp > X degrees Then
The font color is Blue
Else 
The font color is White

Any ideas???

---

### Post by easybake on 2008-11-09
Don't believe that is possible. I would suggest you use a script.

---

### Post by th89 on 2008-11-09
Yes, it is possible. Try modifying the following examples to your needs.

```
${if_mounted /hda2}${color1} /        hda7  ${color1}${fs_bar 5,35 /}$alignr${color3}${fs_free /}$else${color1} /        hda2  ${color1}${fs_bar 5,35 /} $alignr${color3}${fs_free /}$endif

${if_existing  /sys/class/power_supply/BAT1/charge_now} $alignc${color8}${execi 10 /scripts/linux/conky/check-battery.pl} $else $alignc${color7}ACPI NOT WORKING$endif

${color2}${if_existing  /var/run/firewall } ${color3} $else $alignc${color7}FW NOT WORKING$endif
```

Original source [http://bbs.archlinux.org/viewtopic.php?id=52818](http://bbs.archlinux.org/viewtopic.php?id=52818)

---

### Post by cl0ckwork on 2008-11-09
heres a link for you

[Conditionally color your CPU Temp]("http://ubuntuforums.org/showthread.php?p=5936189#post5936189")

a script called colorize.sh written by **Crinos512** that has been buried in the conky screenshots thread, if you just need to use it for number/temperature values.

it can be modified for use with other things, there is also a command called **sed** that can be used for so many different things.
currently i am using one to color a few parts of my conky

[http://sed.sourceforge.net/sed1line.txt]("http://sed.sourceforge.net/sed1line.txt")

hope you get it all worked out

---

### Post by Digitm on 2008-11-12
Oh sweet thanks, I will have to try this out when I get back in town. Jeez how did I miss that part in that post, I thought I looked everywhere... Ohhh it was on page 387 of 437...haha. thanks again.

---

