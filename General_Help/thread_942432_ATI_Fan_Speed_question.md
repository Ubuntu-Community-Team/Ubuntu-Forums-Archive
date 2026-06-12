---
title: "ATI Fan Speed question"
date: 2008-10-09
forum: General Help
---

### Post by gen0 on 2008-10-09
I've noticed others in this forum have managed to get the fan speed controller on their ATI graphics cards using aticonfig in the latest drivers from ATI.  I have installed the latest 8.9 (8.53.4) drivers, Catalyst Control Centre works and reports 8.53.4 as my driver version, but when I try to set the fan speed, I get the following error:

```
~$ aticonfig --pplib-cmd "set fanspeed 0 65"
PPLIB command execution has failed!
ati_pplib_cmd: execute "set" failed!
```

My card is a Sapphire Radeon X1950 and I'm running Ubuntu 7.04 64-bit.

Can anyone tell me if upgrading to the latest version of Ubuntu make any difference to this?  Or does the driver just not support this feature in my card?

---

### Post by gen0 on 2008-10-27
Well I just installed Ubuntu 8.04.1 from CD and installed the latest drivers from ati.com per the instructions here: [https://help.ubuntu.com/community/BinaryDriverHowto/ATI](https://help.ubuntu.com/community/BinaryDriverHowto/ATI)

Still no good:

```
$ aticonfig --adapter=0 --od-gettemperature
ERROR - Get temperature failed for Adapter 0 - Radeon X1950 Series
$ aticonfig --pplib-cmd "get fanspeed 0"
PPLIB command execution has failed!
ati_pplib_cmd: execute "get" failed!
$ aticonfig --pplib-cmd "set fanspeed 0 40"
PPLIB command execution has failed!
ati_pplib_cmd: execute "set" failed!

```

Maybe the linux drivers only support this for newer ATI cards.

---

