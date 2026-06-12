---
title: "Asus M6000n"
date: 2005-03-17
forum: Hardware &amp; Laptops
---

### Post by Viggy on 2005-03-17
Hi!

I have this laptop and everything goes fine. everything but ACPI. 

Then i found help in [here](http://www.ubuntulinux.org/wiki/HardwareSupportMachinesLaptops).

But (this is because i'm a newbie) i don't know how to do this: 
kernel parser can be fixed with a patch in order to make ACPI work:  [http://m6n.ath.cx/aml_method_exec_hack.patch](http://m6n.ath.cx/aml_method_exec_hack.patch)

Anyone can help me?

Thanks in advance,
Tiago

---

### Post by alastair on 2005-03-17
That's a kernel patch for 2.6.5 - so - what kernel are you running?

uname -r

Options include :

- upgrading the kernel
- upgrading to hoary (if you use warty)
- building a kernel and patching (*)

(*) if you do this, first just build a "normal" kernel and check it works OK. Then see if the patch is still applicable by looking at the relevant file :

drivers/acpi/parser/psparse.c

and seeing if the changes make sense (jn a newer kernel say). ACPI in the kernel has changed a lot since 2.6.5 I think. I would try a standard Ubuntu kernel upgrade.

---

### Post by Jae686 on 2005-03-17
So if i Upgrade to Hoary i get the battery detection working?

---

### Post by alastair on 2005-03-18
Maybe. Things are improving all the time.

---

### Post by NuSYS on 2005-03-19
[QUOTE=Jae686]So if i Upgrade to Hoary i get the battery detection working?[/QUOTE]
I've ASUSM6742 and Hoary. The battery status doesn't work.

---

