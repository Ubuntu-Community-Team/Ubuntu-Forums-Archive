---
title: "Problems installing drivers"
date: 2014-09-14
forum: Hardware
---

### Post by creator3 on 2014-09-14
I recently read through a fix for my Asus PCE-N15 wireless card and came up short from fixing my problem. Specifically, I downloaded new realtek drivers, followed the command inputs that were listed on the post, and sucessfully deleted my old drivers. The problem is, the last command "sudo modprobe -v rtl819ce" showed me the following message

"modprobe: FATAL: Module rtl819ce not found." 

I am painfully new when it comes to using my terminal. I know this much: I need new drivers. For now, I would be fine simply reinstalling the drivers from the disk I recieved with my hardware, but I am at a loss as to how to do that as well. The readme on the disk is a dead end, probably because I am inputting the wrong commands. 

I needs me some serious help. Any takers?

---

### Post by weatherman2 on 2014-09-14
One guess: you probably mis-typed the name of the module: I think it's "rtl8192ce" not "rtl819ce" .

The message you received means that modprobe could not find the module you were trying to install.

Otherwise, you're going to have to show us a link to the instructions you were following to be able to offer you help.

---

