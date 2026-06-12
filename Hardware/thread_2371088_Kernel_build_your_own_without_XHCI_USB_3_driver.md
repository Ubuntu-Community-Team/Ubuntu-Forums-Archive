---
title: "Kernel build your own without XHCI USB 3 driver"
date: 2017-09-10
forum: Hardware
---

### Post by tt007-real on 2017-09-10
Hello,
I'm trying to build my own kernel according to this tutorial:
[https://wiki.ubuntu.com/Kernel/BuildYourOwnKernel](https://wiki.ubuntu.com/Kernel/BuildYourOwnKernel)

I remove the XHCI (USB3) driver via the```
[COLOR=#333333]akeroot debian/rules editconfigs[/COLOR]
``` and leave the EHCI (USB2) driver buildin (*) in the kernel.
When I try to build it, I get an error:
```
install -d /home/user/ubuntu-xenial/debian.master/abi/4.4.0-93.116/amd64find /home/user/ubuntu-xenial/debian/build/build-generic/ -name \*.ko | \
    sed -e 's/.*\/\([^\/]*\)\.ko/\1/' | sort > /home/user/ubuntu-xenial/debian.master/abi/4.4.0-93.116/amd64/generic.modules
II: Checking modules for generic...
   reading modules to ignore...read 1 modules.
   reading new modules...read 4616 modules.
   reading old modules...
      MISS: xhci-plat-hcd
      read 4617 modules : new(0)  missing(1)
EE: Missing modules (start begging for mercy)
debian/rules.d/4-checks.mk:12: recipe for target 'module-check-generic' failed
make: *** [module-check-generic] Error 1



```
What I need to remove in order to compile it without the XHCI successfully?
I tried to compile it with the XHCI as a module (M), blacklist it and force the EHCI to loaded at boot time, but the XHCI continue to be uploaded and can't be remove (FATAL error).

B.T.W How can I change the subject to **Kernel build your own without XHCI USB 3 driver**

---

### Post by jeremy31 on 2017-09-10
I think you can edit your first post in the thread to change the topic

Is there no option in BIOS to disable XHCI support?

---

### Post by tt007-real on 2017-09-10
I did disable the XHCI via the BIOS, but somehow it still loaded at boot time.

In edit I can edit my message but not my subject.

---

### Post by jeremy31 on 2017-09-10
Press the edit post then "Go Advanced" below the editing window and it should allow you to change

What problems are you having that you want to stop XHCI?

---

### Post by tt007-real on 2017-09-10
That the XHCI has only 32bit devices that he can created by the driver. I need more devices.

---

### Post by wpiyong70 on 2018-06-11
I tried to build the kernel without XHCI usb 3 driver but could not make it. Is there anyone build the kernel successfully without usb 3 driver?

---

### Post by him610 on 2018-06-12
You might want to read intel's specification for xHCI
[https://www.intel.com/content/www/us/en/io/universal-serial-bus/extensible-host-controler-interface-usb-xhci.html]("https://www.intel.com/content/www/us/en/io/universal-serial-bus/extensible-host-controler-interface-usb-xhci.html")

---

