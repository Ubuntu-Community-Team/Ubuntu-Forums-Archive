---
title: "DCP-130C Scanner Protocol"
date: 2008-06-24
forum: Hardware
---

### Post by Amit Yaron on 2008-06-24
Does anybody know where I can get the protocol of the DCP-130C printer? Unfortunately the kernel has been upgraded to 2.6.22-15-generic, and now the scanner is not recognized. I think that if I don't have a driver that works I should be able to develop one.

---

### Post by ukripper on 2008-06-24
> **Amit Yaron said:**
> Does anybody know where I can get the protocol of the DCP-130C printer? Unfortunately the kernel has been upgraded to 2.6.22-15-generic, and now the scanner is not recognized. I think that if I don't have a driver that works I should be able to develop one.

Use driver **brscan2** here for scanner and it works perfectly with xsane
[http://solutions.brother.com/linux/sol/printer/linux/sane_drivers.html](http://solutions.brother.com/linux/sol/printer/linux/sane_drivers.html)

i use same printer scanner 130c on gutsy

---

### Post by Amit Yaron on 2008-06-24
What version of SANE do you have? Mine is 1.0.14, and I get the error 'No devices available' though I have installed brscan2.

---

### Post by ukripper on 2008-06-24
> **Amit Yaron said:**
> What version of SANE do you have? Mine is 1.0.14, and I get the error 'No devices available' though I have installed brscan2.

i am using gutsy 7.10 and my xsane version is 0.991.
it should work with hardy too.

in terminal type:
> xsane

---

### Post by Amit Yaron on 2008-06-25
Well, that's exactly what I do.

---

### Post by ukripper on 2008-06-25
> **Amit Yaron said:**
> Well, that's exactly what I do.

For 7.10 it was different. 

For 8.04 you need to follwo this:
[http://solutions.brother.com/linux/sol/printer/linux/linux_faq.html#9](http://solutions.brother.com/linux/sol/printer/linux/linux_faq.html#9)

---

### Post by Amit Yaron on 2008-06-25
I'm still working on Gutsy; can it be that upgrading the kernel only was a mistake?

---

### Post by ukripper on 2008-06-25
> **Amit Yaron said:**
> I'm still working on Gutsy; can it be that upgrading the kernel only was a mistake?

you can still use your previous kernel selecting at grub boot menu when you reboot.

---

### Post by Amit Yaron on 2008-06-25
WORKAROUND:

In the terminal
> 
export LD_PRELOAD=/usr/lib/sane/libsane-brother2.so
xsane


---

### Post by growingneeds on 2008-09-08
> **Amit Yaron said:**
> WORKAROUND:

In the terminal

This does not work. I still have to fire up xsane as root:
```
gksudo xsane
```

---

### Post by ukripper on 2008-09-08
> **growingneeds said:**
> This does not work. I still have to fire up xsane as root:
```
gksudo xsane
```

include xsane in /etc/sudoers to allow your username and group to have access without sudo (root)

---

### Post by ronjan41 on 2009-07-24
Acquires and scans once and then I have to reboot before it will do it again. Using 9.04. Worked perfectly on 8.10 I have several hundred pics to scan and cannot reboot for each one. Must be a way around this. Any help appreciated.

---

