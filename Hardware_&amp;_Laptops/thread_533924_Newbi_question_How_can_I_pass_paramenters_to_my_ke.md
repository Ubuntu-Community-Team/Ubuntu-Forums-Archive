---
title: "Newbi question: How can I pass paramenters to my kernel?"
date: 2007-08-24
forum: Hardware &amp; Laptops
---

### Post by Hxsrmeng on 2007-08-24
My usbcore is not a module, it's built in.
I'd like to pass parameter
                   usbcore.blinkenlights=1
to the kernel

where can I do it?
I try this in the console command line. but it said "usbcore: command not found"

Below is what I have:
"
/usr/src/linux-2.6.22.1/drivers/usb/core/.usbcore.o.cmd
/usr/src/linux-2.6.22.1/drivers/usb/core/usbcore.o
"
Thanks in advance.

---

### Post by anubhavrocks on 2007-08-24
why dont you recompile the kernel with that parameter set to 1 in the code itself.

---

### Post by Hxsrmeng on 2007-08-24
> **anubhavrocks said:**
> why dont you recompile the kernel with that parameter set to 1 in the code itself.

I just want a practice.:)

---

### Post by anubhavrocks on 2007-08-24
```
usbcore.blinkenlights=1
```  has to be given in the ```
/boot/grub/menu.lst
```  file and not on the console.Alternatively you can pass parameter while booting up.

---

### Post by Hxsrmeng on 2007-08-24
> **anubhavrocks said:**
> ```
usbcore.blinkenlights=1
```  has to be given in the ```
/boot/grub/menu.lst
```  file and not on the console.Alternatively you can pass parameter while booting up.

Thanks.

if I add it to menu.lst, I have to restart my computer, correct?

But if usbcore is a module, how can I pass the paramenter to it?
on console to do 
               $ modprobe usbcore blinkenlights=1
or add a line to /etc/modprobe.conf
               option usbcore blinkenlights=1
If the second is the correct way, can it work without restart the computer?

Thank you so much.

---

### Post by anubhavrocks on 2007-08-24
Right.With modules; restart  is not required.also check
/sys/module/usbcore/parameters

---

### Post by Hxsrmeng on 2007-08-24
> **anubhavrocks said:**
> Right.With modules; restart  is not required.also check
/sys/module/usbcore/parameters

Thanks.:)

---

