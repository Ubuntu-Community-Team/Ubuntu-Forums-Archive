---
title: "[hint] Ati cards powerstates"
date: 2007-05-15
forum: Hardware &amp; Laptops
---

### Post by willywongi on 2007-05-15
Hi to all. I know this is all well-known, but maybe a post could help newbies like me.:popcorn: 

Note: I have a core duo laptop with a ATI X1600.

While investigating on the possible options available from the ati-config utility shipped with the Feisty packaged fglrx (AMD/ATI closed source drivers) I discovered that I can easily switch the powerstates, that is I can underclock the video chipset to lower consumption, heat and fan noise. Altought I can't prove this enhanchments, here are the commands you can issue:
```
pongi@pongi-laptop:~$ aticonfig --list-powerstates
    core/mem      [flags]
-----------------
* 1: 128/135 MHz  [low voltage]
  2: 392/243 MHz  [low voltage]
  3: 419/378 MHz  [default state]
```

```
pongi@pongi-laptop:~$ aticonfig --set-powerstate=3
```

This last one let you choose the powerstate.
I also wrote a little bash script to cycle through those powersates:
```
#!/bin/bash
# Cycles through Ati card Powerstates

POWERSTATE=`aticonfig --list-powerstates | grep \* | cut -d " " -f2 | sed 's/://g'`

case $POWERSTATE in
        "3")    aticonfig --set-powerstate=1; echo Set Powerstate to lowest. ;;
        "2")    aticonfig --set-powerstate=3; echo Set Powerstate to highest. ;;
        "1")    aticonfig --set-powerstate=2; echo Set Powerstate to medium. ;;
esac
```

I think this is my very first batch script.. so let me know of any mistakes or improvements.. Thanks!!

---

