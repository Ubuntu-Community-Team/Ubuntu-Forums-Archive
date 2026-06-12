---
title: "Incorrect laptop battery low message"
date: 2010-07-15
forum: Hardware
---

### Post by Laen on 2010-07-15
I recently got an Acer netbook and put Ubuntu 10.04 on it.

However, I'm having an issue with the power management.

If the netbook has been closed for a while and has not been plugged in, shortly after I open the lid, I get a "Laptop battery critically low" message telling me that the system is going to hibernate.
I know there's nothing wrong with the battery because it hardly drains when the netbook is closed.
I run "acpi" when I get this message and it tells me the battery is at over 60% and has almost 2 hours left.

If I plug in the adapter and reopen the laptop - voila! No problem. And I still have over 60% of battery left.

Any suggestions?

Thanks!

---

### Post by mjk183 on 2010-07-15
I  have a similar problem on a Sony Vaio VPC EB1Z0E.  

Once the laptop battery has fully charged I disconnect the power supply, and straight away I get a box telling me my battery is critically low and that I should recharge.  I also get a notification telling me I have 3 minutes of battery left, however if I then click on the battery on the panel it tells me there is 2 hours of life.  

not a major problem but a little annoying.

---

### Post by moore.bryan on 2010-07-15
Is the nettie set to hibernate or suspend when you close the lid? There are some "known issues" with acpi related events and one or both of those options.

---

### Post by Laen on 2010-07-15
> **moore.bryan said:**
> Is the nettie set to hibernate or suspend when you close the lid? There are some "known issues" with acpi related events and one or both of those options.

It's set to suspend.

---

### Post by Laen on 2010-07-15
Just an update.

Even if I press "Cancel" on the battery low dialog, about a minute later the screen goes dark and I'm asked to enter my password (as if reactivating the netbook after it's turned the screen off).
Trying to re-login, however, doesn't work because everything freezes.

I end up having to press the power button which seems to suspend the netbook (or maybe hibernate?) and then press it again to reload it.

This whole process takes a bit of time and ironically probably drains some of the battery because of all the swapping that must be going on.

---

### Post by technix32 on 2010-07-16
I've been having exactly the same problem with my MSI Wind netbook. As soon as i disconnect AC it says critical.

Occasionally it will report the battery has 2 mins remaining, but most of the time it reports correctly, around 2.5hrs.  Yet still begins to hibernate.

Any ideas?

---

### Post by pavel__ on 2011-10-15
same problem with 11.10 on a lenovo 3000 n100 :(

---

### Post by Joplggr on 2013-04-04
Oddly enough, I've been having the same problem with an iMac. For some reason, the system recognizes the Bluetooth mouse and keyboard as laptop batteries and will suspend after a few seconds of being connected. The suspending isn't much of a problem compared to the fact that the mouse and keyboard are not responsive.

---

