---
title: "dd from 1 flashdrive to another"
date: 2010-06-14
forum: Hardware
---

### Post by TomAbada on 2010-06-14
hi all
can someone remind me
how can i copy 1 USB flash drive to another by using dd ???
p.s i dont remember how can i know which USB is sda / sdb ? ...etc
so if i can reminded to that 
that would be great

thanks in advance

---

### Post by anglican on 2010-06-14
> **TomAbada said:**
> hi all
can someone remind me
how can i copy 1 USB flash drive to another by using dd ???
p.s i dont remember how can i know which USB is sda / sdb ? ...etc
so if i can reminded to that 
that would be great

thanks in advance
Plug one in and type "dmesg" in a terminal, then plug the other in and do the same. That will also tell you the associated device files which you will need for the dd command.

H

---

### Post by C.S.Cameron on 2010-06-14
dd if=/dev/sda of=/dev/sdb


[http://www.linuxquestions.org/questions/linux-newbie-8/learn-the-dd-command-362506/](http://www.linuxquestions.org/questions/linux-newbie-8/learn-the-dd-command-362506/)

---

