---
title: "completely lost in power management + HD load cycle issue"
date: 2010-12-12
forum: Hardware
---

### Post by Megatron3000 on 2010-12-12
I've been quite happy with Lucid so far, since it all ran directly and decently. But upon researching something about my hard disk, I found out mine is doing easily 100 load cycles an hour when on AC - which should not be good.

I looked into what is written about solving this, and it just got me completely confused on how power management works in Lucid. Currently, it's apparently divided between pm-utils, acpi-support and laptop-mode-tools, and in no way is it transparent to me how it actually works. I've been trying to solve the load cycle issue with laptop-mode-tools, but it turns out that I can't even turn laptop-mode-tools on. 
On a side note, when switching to Ubuntu my battery life shortened to half of it's previous length in a day, and when switching to 10.04, I ended up with just a minute of battery life. There's no slow decay involved, it just became impossible to do anything on battery. And also, my fan is always on, no matter what happens to my computer. I remember once trying to do something about that with an old package that helped with a Phoenix bios, but obviously to no avail.

Could someone explain me what -amongst all the solutions spread around the net - is the current one for the load cycle issue? I would also be extremely pleased if someone could give me a link to where power management in its entirety is explained. 
If it all sounds like my power management configuration is a mess, is there a way i can just do a clean reinstall of the necessary components? I didn't change any parameters in acpi-support or pm-utils before today, but you never know.
I am very much in love with Ubuntu and want to keep on using it - but i'd rather not kill my hard disk while doing that. Probably I am going to update my laptop at some point, but I'd rather wait a little longer - and I want to know how to avoid these issues in the future.

I'm using a 3 year old Toshiba Satellite with a Phoenix Bios (vs 1.50) and run a 64 bit version of Lucid on it.

---

### Post by Megatron3000 on 2010-12-13
le bump

---

### Post by dabl on 2010-12-13
I don't know what you've already read, but AFAIK this is still the authoritative reference:  [https://ata.wiki.kernel.org/index.php/Known_issues#Drives_which_perform_frequent_head_unloads_under_Linux](https://ata.wiki.kernel.org/index.php/Known_issues#Drives_which_perform_frequent_head_unloads_under_Linux)

---

### Post by Megatron3000 on 2010-12-19
Thanks! I didn't read that one yet. My hard disk is not listed, but since it steadily adds a hundred load cycles per hour, i guess i should take a look at fixing it. Where would one set the apm?
And if I want to do a full overhaul of all the different parts that manage power, and a hard disk issue like this, what would be the best way to do it? I don't quite get how acpi-support and pm-utils and laptop-mode-tools interact.

---

