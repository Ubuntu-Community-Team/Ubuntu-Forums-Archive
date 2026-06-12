---
title: "No sound"
date: 2010-05-26
forum: Hardware
---

### Post by Brendog on 2010-05-26
it appears that i'm not getting any sound when i open ubuntu. do i need any drivers or coding? keeping in mind that i'm a linux noob
nvidia drivers installed
computer-macbook pro
using reelfit as a duel boot

[appologies for posting something simullar to this in the apple section, since i though i use a mac i though it would be acceptable.]

---

### Post by lidex on 2010-05-26
Can you post the output of these terminal commands for me please:
```
uname -a
aplay -l
cat /proc/asound/version
head -n 1 /proc/asound/card*/codec#* 
```
Terminal="Applications->Accessories->Terminal"
**Please also include the make/model of your PC/Laptop.**
Please post text output using code tags (the # in toolbar)

---

### Post by upmendoza on 2010-05-27
Hi... I've the same problem, so I decide catch this oportunity, hope you can help me.
Computer: Compaq Presario 2100
OS: Xubuntu 9.10
Sound Card: it seems M5451 AC-Link Ali Controller

The results to those commands was:


zarya@zarya-laptop:~/Documentos$ uname -a
Linux zarya-laptop 2.6.31-21-generic #59-Ubuntu SMP Wed Mar 24 07:28:56 UTC 2010 i686 GNU/Linux
zarya@zarya-laptop:~/Documentos$ aplay -l
**** Lista de PLAYBACK Dispositivos Hardware ****
tarjeta 0: A5451 [ALI 5451], dispositivo 0: ALI 5451 [ALI 5451]
  Subdispositivos: 32/32
  Subdispositivo #0: subdevice #0
  Subdispositivo #1: subdevice #1
  Subdispositivo #2: subdevice #2
  Subdispositivo #3: subdevice #3
  Subdispositivo #4: subdevice #4
  Subdispositivo #5: subdevice #5
  Subdispositivo #6: subdevice #6
  Subdispositivo #7: subdevice #7
  Subdispositivo #8: subdevice #8
  Subdispositivo #9: subdevice #9
  Subdispositivo #10: subdevice #10
  Subdispositivo #11: subdevice #11
  Subdispositivo #12: subdevice #12
  Subdispositivo #13: subdevice #13
  Subdispositivo #14: subdevice #14
  Subdispositivo #15: subdevice #15
  Subdispositivo #16: subdevice #16
  Subdispositivo #17: subdevice #17
  Subdispositivo #18: subdevice #18
  Subdispositivo #19: subdevice #19
  Subdispositivo #20: subdevice #20
  Subdispositivo #21: subdevice #21
  Subdispositivo #22: subdevice #22
  Subdispositivo #23: subdevice #23
  Subdispositivo #24: subdevice #24
  Subdispositivo #25: subdevice #25
  Subdispositivo #26: subdevice #26
  Subdispositivo #27: subdevice #27
  Subdispositivo #28: subdevice #28
  Subdispositivo #29: subdevice #29
  Subdispositivo #30: subdevice #30
  Subdispositivo #31: subdevice #31
zarya@zarya-laptop:~/Documentos$ cat /proc/asound/version
Advanced Linux Sound Architecture Driver Version 1.0.20.
zarya@zarya-laptop:~/Documentos$ head -n 1 /proc/asound/card*/codec#*
head: no se puede abrir «/proc/asound/card*/codec#*» para lectura: No existe el fichero ó directorio

So many tnks in advance

---

