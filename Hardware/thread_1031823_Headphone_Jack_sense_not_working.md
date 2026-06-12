---
title: "Headphone Jack sense not working"
date: 2009-01-05
forum: Hardware
---

### Post by PurpleSkyz on 2009-01-05
Hello there,

I am new to Linux and Ubuntu, and would like to migrate from Vista to ubuntu, however, I encountered a problem that is likely to drive me off.

Whenever I insert my headphones in my laptop, sound does go to them, but the speakers are not muted. I see all over internet I am not alone, yet I cannot find a solution to that.

Any Ideas?

Thanks.

---

### Post by IQRules on 2009-01-05
what is the laptop model? Is it snd-hda-intel driver?
Go to xterm window, run '$ lspci -v ', look for multimedia section.
Post '$ aplay -l' and '$ aplay -L'

---

### Post by oojanen on 2009-01-07
I had exactly same problem with HP Pavilion 1035EA, which got fixed by upgrading from my Intrepid 2.6.27.9 to 2.6.27.11. Read reports that it worked for some Dell laptops as well (actually 2.6.27.10 is enough)

It's an intrepid-proposed release as of now so so be careful. You need to 

1. go to System->Administartion->Software Sources->Updates and enable "Pre-released updates" 
2. run in terminal: sudo apt-get dist-upgrade

---

