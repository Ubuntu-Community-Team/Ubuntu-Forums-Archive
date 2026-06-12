---
title: "Battery life"
date: 2012-08-11
forum: Hardware
---

### Post by rvdli on 2012-08-11
Hi all,

I recently bought a Dell Inspiron 5420. It came with Windows 7, but I use in  dual-boot with Ubuntu, as I prefer... I use Windows only for specific  stuff of college.

But I noticed that on Windows, my battery lasts about 5 hours, while on Ubuntu 12.04 it lasts about 1:40, 2 hours maximum.

I tried booting with pcie_aspm=force and i915.i915_enable_rc6 on Grub  (it used to work on my previous chinese-branded Sandy Bridge laptop),  but I don't know if is effective on Ivy Bridge processors. Battery life  hasn't improved a single minute.

General specs:

CPU: Ivy Bridge Core i5 3210M
6GB DDR3 RAM
Hybrid Graphics (Intel HD 4000 + GeForce 630M)

Did anybody here experience something like this and has any info that can help?

Thanks,
R.

---

### Post by andriansah on 2012-09-26
Anyone have solution with this? I have the same problem, on ubuntu 12.04 it only last about less than 2 hours

---

### Post by shaktiman1234 on 2012-09-26
Please check that you have proper driver installed for your graphics card, if you have one.

---

### Post by andriansah on 2012-09-26
> **shaktiman1234 said:**
> Please check that you have proper driver installed for your graphics card, if you have one.

Ther driver of graphoc card is doing fine, the problem is in networking, but it fix.

---

### Post by kc1di on 2012-09-26
you may want to try this package:
[http://packages.ubuntu.com/lucid/laptop-mode-tools]("http://packages.ubuntu.com/lucid/laptop-mode-tools")

---

### Post by andriansah on 2012-09-26
> **kc1di said:**
> you may want to try this package:
[http://packages.ubuntu.com/lucid/laptop-mode-tools]("http://packages.ubuntu.com/lucid/laptop-mode-tools")



still not good, I have install this package but the problem still continue
I leave my laptop only for download, from 67% to 26% in about 40 minutes

---

### Post by andriansah on 2012-09-27
Hi all

there's must be something with hybrid graphic since this laptop use 2 VGA cards. 

I'm still searching on how to only using 1 VGA at all times or something that easy to configure.
I already search about hybrid graphics but still don't give me enough solution
If there someone has solution about hybrid graphics let me know

Thanks

---

### Post by andriansah on 2012-09-28
Last night I Install this
[http://bumblebee-project.org/](http://bumblebee-project.org/) follow the instruction on how to install it.

From this morning I running with battery and shutdown at noon, so its about 3 hours and 15 minutes.

not bad



Still searching other this to make battery more efficient

---

### Post by andriansah on 2012-09-29
update!

I think what make the battery last longer is by applying this method
[http://hybrid-graphics-linux.tuxfamily.org/index.php?title=Acpi_call](http://hybrid-graphics-linux.tuxfamily.org/index.php?title=Acpi_call)

This what make my battery last longer

---

### Post by marcoDallas on 2013-09-07
Hi, if you just want long battery life you can use acpi_call.

If you want to use it via graphic interface try acpi_call_GUI:

Here's the wiki guide: [https://help.ubuntu.com/community/HybridGraphics#acpi_call](https://help.ubuntu.com/community/HybridGraphics#acpi_call)

And Here's the website: [http://marcodallas.github.io/acpi_call_GUI/](http://marcodallas.github.io/acpi_call_GUI/)

---

