---
title: "Problem with battery applet on Edgy with HP NX6125"
date: 2006-10-30
forum: Hardware &amp; Laptops
---

### Post by eugenwinter on 2006-10-30
Hi there
 I have a problem with the battery applet on my newly installed edgy on a HP NX6125 (AMD Turion notebook). The state of the battery applet is not changing when I plug or unplug the AC adapter. In fact, the battery applet is not changing in any case also the charging state of the battery remains at 91% during usual operation. It seems that the entire ACPI system is somehow ignoring the battery. Has anyone an idea whats going on? I had not such problems on dapper.

thanks 
  Eugen

---

### Post by eugenwinter on 2006-10-30
Hm. It seems that I was a bit too fast with my posting. 
After some investigation I found out that the problem is somwhere in the ACPI subsystem. It seems that no ACPI events are handled belonging to battery and ac adapter. The funny thing is that Suspend and Hibernate works fine. 
Any ideas?

eugen

---

### Post by mrthst on 2006-10-30
Exactly the same on my HP nc2400 with a freshly installed Edgy.

Funny thing is that it works perfectly fine when I boot from the live CD.

For example u can open a Terminal and type "acpi_listen". It will print all sorts of acpi events. Like when u unplug/plug-in the power-cord.

After installation those events are gone, the only events I still get are when I open and close the lid.

---

### Post by eugenwinter on 2006-11-02
I found the problem!!!! :D 
It seems that one does not need the **[COLOR="Red"]noapic[/COLOR]** and **[COLOR="Red"]nolapic[/COLOR]** kernel option for installation. However, if one wants to have ACPI working properly you really should use them.

So, simply add **[COLOR="Red"]noapic[/COLOR]** and **[COLOR="Red"]nolapic[/COLOR]** to the kernel options in the menu.lst file of grub.
After a reboot everything works fine :)

---

### Post by mrthst on 2006-11-20
didn't work for me.
But I was able to fix it by removing the psmouse kernel-module.

---

