---
title: "Ubuntu 9.10 muted after upgrade"
date: 2009-11-08
forum: Installation &amp; Upgrades
---

### Post by Cashmir on 2009-11-08
Hello, 

I have just installed new ubuntu 9.10 and I don't have any sound... 
Command **lspci | grep -i audio** lists:

```
01:0a.0 Multimedia audio controller: Creative Labs CA0106 Soundblaster
```

Command **sudo cat /proc/asound/cards** lists:

```
0 [CA0106 ]: CA0106 - CA0106
AudigyLS [SB0310] at 0xb880 irq 21

```

Unfortunately when I check System>Preferences>Sound in the sections Hardware, Input I cannot see any device listed - I expect that is the reason of no sound in the system... 

Do you have any idea what do with it ? Thank in advance !

---

