---
title: "disabling hotplug usb device"
date: 2005-04-22
forum: Hardware &amp; Laptops
---

### Post by brickbat on 2005-04-22
Hi, I'm running vmware so I can run my multifunction printer/scanner off the vm.  My problem is that when I connect it as per the instructions, vmware tells me that I have to disable it for the guest system to take ownership.

Could someone please tell me how to do this?

Thanks
bb

---

### Post by diebels on 2005-04-22
Blacklist the printer module, or rename it. Search on the forums, sure it's been explained some times.

---

### Post by brickbat on 2005-04-22
thanks for the advice.  It seems i am half way there.  Now i need to know what the device name is so i can put it in the blacklist.

can someone please tell me how to figure it out.  i have searched in the forum but could not find it.

thanks
bb

---

### Post by diebels on 2005-04-22
Device name and module name are two different things. You need to find the module name. Run "lsmod" and see if something familiar shows up

---

