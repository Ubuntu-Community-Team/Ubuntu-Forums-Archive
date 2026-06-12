---
title: "Battery Problem with HP Dv4 series"
date: 2009-02-13
forum: Hardware
---

### Post by Logistics64 on 2009-02-13
I'm having a bit of trouble with the battery on my HP Pavilion DV4t-1000 notebook. When take the battery off of AC power, the icon reads "Battery state could not be read at this time" and "Battery charge time is current unknown". Any help would be greatly appreciated. Thanks in advance.

---

### Post by Logistics64 on 2009-02-14
Ok guys, I did some research and found out that the battery monitor stops working after the computer sleeps. When I wake it back up, the battery icon displays the message above. Hope someone can help me now, thanks.

---

### Post by Logistics64 on 2009-02-14
Bump bump bump it up

---

### Post by manincagejackwilson on 2009-02-23
I am having this problem as well. DV4-1120US. Any suggestions?

Not sure if a module may need to be forced to reload within /etc/default/acpi-support, as I had to add "snd_hda_intel" in order for sound to work upon resume.

---

### Post by BilliShere on 2009-03-03
hey guys i have a HP pavilion dv4 1014nr and it works with ubuntu flawlessly
just make sure you update to the latest everything! that battery problem was fixed for me in updates a few weeks ago actually and everytime i resume from sleep, it doesnt show it cannot be read thing anymore.

im not so sure about the snd_hda_intel thingy... i had to do that at the very beginning when my sound on my laptop made wierd stuttering sounds... i just added a options snd-hda-intel msi_enable summin summin option... and my sound was working perfect..

so that is probably not related to the power manager problem

and sometimes it helps to know what chipset you are using, what processor, etc... because not all dv4 series have a similar chipset build or summin if ya kno what i mean. the problem can be narrowed down further if you could mention your chipset and all that. i have a true intel centrino laptop so if you do too then you should not be seeing this problem of gnome-manager.

btw... how is your battery life consumption compared to windows? did anyone get anywhere the same number of hours as windows? my battery life gets cut down to half in ubuntu despite many optimizations.

---

