---
title: "Ubuntu fails to see cdrom!"
date: 2007-07-29
forum: Hardware &amp; Laptops
---

### Post by Psyence88 on 2007-07-29
Hi all, I just recently installed Ubuntu on my laptop and everything worked out fine, so I did the same for my uncle and he is having issues with his cdrom drive(using a Acer Travelmate 6292) when I'm in the file browser I click on CD-ROM 1 and it gives me this error:

Unable to mount the selected volume.

mount: special device /dev/hda does not exist


I've looked around for advice but to no avail! Any help would be greatly appreciated thanks!

---

### Post by Psyence88 on 2007-07-29
Help, no? :(

---

### Post by fjgaude on 2007-07-29
Sounds like the installer didn't recognize this particular drive. What to do about it? Hmmm... using the file browser go into File System and click on /media and see what it says there. Do you see any cdrom listings?

Also when you click on Computer at the home menu, do you see any CDROMs listed?

frank

---

### Post by Psyence88 on 2007-07-29
Yep, in fact I do; I see cdrom and cdrom0 though when I go into the computer portion it says CD-ROM 1. Could there be some mis-information going on?

---

### Post by Syke on 2007-07-30
Sounds like he has a Santa Rosa-based system. Sometimes you need to add "piix" to /etc/modules.

```
sudo gedit /etc/modules
```

and add

```
piix
```

to the end of the file. Save, exit, and reboot. Hopefully that will re-enable the drive.[/QUOTE]

---

