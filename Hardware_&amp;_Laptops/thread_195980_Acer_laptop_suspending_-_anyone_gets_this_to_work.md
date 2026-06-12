---
title: "Acer laptop suspending - anyone gets this to work?"
date: 2006-06-13
forum: Hardware &amp; Laptops
---

### Post by boom2k1 on 2006-06-13
Hello all,

I am using an Acer 3502. I think this might apply to many acer laptop users as well.

The problem is that the laptop screen does not wake up after suspending it! (In particular, the screen stays black.)

Does any users get it fixed?
And how exactly?

Thanks!

---

### Post by patrickfromspain on 2006-06-13
I don't if this will work for you, but you could try this:

sudo gedit /etc/default/acpi-support

look for this line:

MODULES_WHITELIST=""

and put your video driver modulo into it. In my laptop (uses the i810 driver) this would be:

MODULES_WHITELIST="i810"

save the file and do sudo /etc/init.d/acpid restart

now you can try if it works.. If not, you can try with other settings in that file.

Hope it helps.

---

### Post by boom2k1 on 2006-06-14
How do you check which modulo you use? thanks!

---

### Post by patrickfromspain on 2006-06-14
try looking into /etc/X11/xorg.conf

there look for Section "Device" and check which driver you  are using, that would be the module.

---

