---
title: "compaq evo n610c: suspend and hibernate"
date: 2004-11-13
forum: Hardware &amp; Laptops
---

### Post by ubusaj on 2004-11-13
I'm a linux newbie.  Can anyone offer me some simple advice on getting suspend [preferably] and/or hibernate to work on my Evo n610c?

---

### Post by ubusaj on 2004-11-14
Here are couple of links regarding Linux on the n610c.  Based on this information, how can I get Ubuntu to suspend/hibernate?   

[http://jeff.blogdns.com/n610c/n610c_howto.html](http://jeff.blogdns.com/n610c/n610c_howto.html)
[http://www.psychosis.net/evo-linux/](http://www.psychosis.net/evo-linux/)

I'm looking for someone to help me take the information above and make it Ubuntu specific.

Thanks.

---

### Post by DiCiCat on 2004-12-14
Hello,

I want the same as above. 
I tried to follow the wiki howto about the suspend/hibernate on laptop and just want to active the suspend to ram mode.
[https://www.ubuntulinux.org/wiki/SuspendHowto](https://www.ubuntulinux.org/wiki/SuspendHowto)

When i close the lip or presse stand by button, my computer (evo N610c) perfectly respond to request, but when i open my computer, power restart, fan restart, but nothing else, screen stay black. 
I tried to enter a "echo 3 > /proc/acpi/sleep" command on a shell and in a text session whith same result.

Someone can help me to find what is go wrong?
I'm running an Ubuntu warty with a standard 686 kernel.

---

### Post by malmjako on 2004-12-17
I had to add acpi_sleep=s3_bios to my kernel options to get waking up to work on my HP Omnibook 6000. You could try that!
(Add it to /boot/grub/menu.lst, #kopts = ... acpi_sleep=s3_bios. Then run update-grub, and reboot!)

---

### Post by nehalem on 2004-12-18
Same thing here.

hp nx7010.

It suspends but won't come out.  That grub option didn't seem to help either.  Anyone got any ideas?  We need a kernel guru or something :)

---

### Post by monte.lin on 2004-12-24
[QUOTE=DiCiCat]

I want the same as above. 
I tried to follow the wiki howto about the suspend/hibernate on laptop and just want to active the suspend to ram mode.
[https://www.ubuntulinux.org/wiki/SuspendHowto](https://www.ubuntulinux.org/wiki/SuspendHowto)

[/QUOTE]


The suspend script in the tar ball is a joke. It is too simple to be  of pratical use for most ACPI notebook. I had a good working script/add-on modules working with stock Debian kernel, but failed with Ubuntu's patched kernel. I'm still inspecting on this.

---

