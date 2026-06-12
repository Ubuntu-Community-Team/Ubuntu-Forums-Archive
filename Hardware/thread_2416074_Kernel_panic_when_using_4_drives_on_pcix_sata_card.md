---
title: "Kernel panic when using 4 drives on pcix sata card"
date: 2019-04-04
forum: Hardware
---

### Post by w1ll1am2 on 2019-04-04
So I am in the process of building a new server. I have 7 drives including a M2 boot drive. 2 drives on my motherboards main SATA ports and 4 drives on an add on PCI x SATA controller. When using the controller 95% of boots result in a kernel panic. If I remove one of the drives from the controller and connect it to another sata port on the motherboard or to another pcix controller everything works fine. Ordered another 4 port card with a different chip and it does the same thing. 

I am running ubuntu 18.04 server. Not sure what I can do from here to diagnose. Currently the only solution I have is to use 3 of the 4 ports on the card and move the other drive to another card or internal sata. I plan to get more drives so I will need the port eventually. 

Also not using RAID if that matters. 

Anyone have any ideas?

---

### Post by w1ll1am2 on 2019-04-04
Update: I am now having the issue when using 3 drives on the card so I guess it's not related to having 4 on the same card. It also happens when having 2 on one card and 2 on another both using the same chip but different models.

---

### Post by QIII on 2019-04-04
Hello!

Are these devices in your fstab?  If so, what happens if you comment them out?

Does the machine boot?  Can you mount the devices manually after booting?

---

### Post by w1ll1am2 on 2019-04-04
They are in my fstab. If I comment them out it will boot, and even if I don't it will boot sometimes but then after being up for awhile and interacting with the drives I'll end up with the same kernel panic. I can't remember if I tried commenting them out booting up uncommenting and mounting to see if things work better, but based on the panic I get when I do get a successful boot that makes me think it won't help much.

---

### Post by QIII on 2019-04-04
A bit of a ramble there.  :)

So if you comment them out in fstab, you boot consistently?

---

### Post by w1ll1am2 on 2019-04-04
I am trying to do some more testing now. I was just able to recreat the panic without using the controller card at all (complete removed it from the system) which I wasn't able to do last week when I first had the problem which made me think it was the pci card. I'll report back with more findings after I test some more.

---

### Post by w1ll1am2 on 2019-04-05
Memtest86+ reported errors so I am thinking this is most likely a memory issue. Trying to track down which module and/or slot on the board is bad.

---

### Post by crjackson on 2019-04-07
Did you check your log file to see what caused the panic?

If you had memory errors, then I suspect you&#8217;re on the right track.

---

