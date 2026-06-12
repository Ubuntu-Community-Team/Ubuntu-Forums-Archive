---
title: "getting scanner hp5300c to work"
date: 2005-05-19
forum: Hardware &amp; Laptops
---

### Post by wimva on 2005-05-19
Hi there,

I have been busy trying to use my HP5300C scanner with Hoary and XSane because it didn't work quite out of the box. Browsing the internet learned me that the trouble seems to be the loaded hpusbscsi module. 

So what's the status now : if - after a clean boot - I manually remove the hpusbscsi module (modprobe -r) then XSane recognizes my scanner and I can use it. So that's good news. 

However I don't seem to be able to prevent the loading of the hpusbscsi module at boot time. I have read some faq's and "module" documentation but obviously I am missing something. 

At the moment I have tried the following : 

* in /etc/hotplug/blacklist I have added "hpusbscsi"
* in /etc/modprobe.d I created a file with the following content :
install hpusbscsi echo "hpusbscsi - nothing done"

but this doesn't make any difference in case of a reboot. The module was there again. Eventually I even (re)moved the hpusbscsi.ko file under /lib/modules/.... to some other place but ... after a reboot ... the module is there again when executing lsmod. 

So, I really would like to know where and what I should adjust in order to make sure a module isn't loaded anymore at the next reboot. Anyone any hints? Much appreciated.

Regard,
Wim Van Acker

---

### Post by daller on 2005-12-30
If any help, this issue should have been fixed in Breezy!

---

