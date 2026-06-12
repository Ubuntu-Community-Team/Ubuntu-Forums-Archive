---
title: "GRUB noprobe parameter seems not working"
date: 2006-01-31
forum: Hardware &amp; Laptops
---

### Post by giacomolg on 2006-01-31
Hi everyone!
As my second cd drive (**/dev/hdb**) give me a *lost interrupt* error (it was doing that even on other distros) I usually disable it from the GRUB *menu.lst* file:

> title		Ubuntu, kernel 2.6.12-9-386 
root		(hd0,5)
kernel		/vmlinuz-2.6.12-9-386 root=/dev/sda7 ro quiet splash hdb=noprobe
initrd		/initrd.img-2.6.12-9-386
savedefault
boot

Despite this, dmesg keeps informing that 
[COLOR="Red"][4302168.498000] ide-cd: cmd 0x3 timed out
[4302168.498000] hdb: lost interrupt
[4302228.498000] ide-cd: cmd 0x3 timed out
[4302228.498000] hdb: lost interrupt[/COLOR]
and this gives me problems. For example the computer doesn't shut down completely.
Have I to type some different options to GRUB (with Mandriva works fine...)?
:confused: 
Thank you very much.

---

### Post by giacomolg on 2006-02-01
Is maybe due to the particolar version/flavour of the Kernel, **changing** or **downgrading** the kernel (2.6.12-9-386) could help??

Thanks

---

### Post by giacomolg on 2006-02-04
**up**

---

