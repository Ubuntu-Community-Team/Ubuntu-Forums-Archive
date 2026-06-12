---
title: "Power consumption higher?"
date: 2011-09-18
forum: Hardware
---

### Post by Langney on 2011-09-18
Hi everyone, sorry to bug you guys but I was just wondering If my version of Ubuntu Is what you might call a power hog. Up until about 2 weeks ago I was using Mint and my electric would last a week on a tenner but since up until the 2 weeks ago I started to use Ubuntu 10.04 lucid. For some reason it feels like It's consuming more electric as I have had to top up twice this week already. Is It just me or Is Ubuntu 10.04 a power hog? BTW Loving It all apart from this small problem If there Is any.

---

### Post by ajgreeny on 2011-09-18
Is this a laptop you are talking about?  Which version of Linux Mint were you using, as Mint 9 is the same base as Ubuntu10.04?

I have read about 11.04 having a power leak but I don't know how true that is, but I've not heard about 10.04 with the same problem.

---

### Post by Langney on 2011-09-18
Was using Mint 11 Katya. Not sure If this helps. No also on Desktop. Probably posted on the wrong part of the forum havent I?

---

### Post by ajgreeny on 2011-09-18
> **Langney said:**
> Was using Mint 11 Katya. Not sure If this helps. No also on Desktop. Probably posted on the wrong part of the forum havent I?
No, not on the wrong section, so don't worry about that.

Unfortunately I can not help you other than suggestion you try adding the following simple edit to your grub with ```
gksudo gedit /etc/default/grub 
``` and change the line
```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
```to ```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash pcie_aspm=force"
``` then run ```
sudo update-grub
``` It may or may not help, but I don't think it can do any harm, so is safe to try.

---

### Post by Langney on 2011-09-18
Thanks for that ajgreeny. Did everything you suggested. All I can do now Is wait and see :) I will keep this updated till I know whats what. Hopefully I won't have to get another Distro lol. Have everything set up on here. Took me the best part of 4 hours to get everything the way I wanted lol.

---

