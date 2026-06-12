---
title: "Hibernation Question"
date: 2005-11-11
forum: General Help
---

### Post by justintime32 on 2005-11-11
Hi all,
I just installed Ubuntu 5.10, and so far I really like it. But, I have a question related to hibernation.

I tried hibernating this, and it worked well. Although, I tried a "sudo hibernate" at the command line, and the SWSP hibernate script wasn't installed. I did a "sudo apt-get install hibernate" and got this message when trying to hibernate:```
Your kernel does not have any recent Software Suspend 2 support compiled in.
Please follow the HOWTO linked from http://softwaresuspend.berlios.de/ for
instructions on how to compile Software Suspend into your kernel.
hibernate: Aborting.
```Before trying Ubuntu, I tried Kubuntu. It worked OK, but I couldn't find out how to hibernate it. I read somewhere that you could go to System Settings > Laptop and Power > Laptop Battery > ACPI and enable hibernation, but I didn't have the ACPI option. I got a message saying something to the extent that my kernel only had partial ACPI support ( :confused: ).

Because I really want KDE and hibernation seems to work in Gnome, I wanted to try installing Kubuntu from apt-get, but I'm concerned that hibernation won't work (which is one of the reasons I tried Ubuntu). Can someone please inform me what command Ubuntu executes when it hibernates? Thanks!

---

### Post by ranf on 2005-11-11
[QUOTE=justintime32]Can someone please inform me what command Ubuntu executes when it hibernates?[/QUOTE]
```
sudo /etc/acpi/hibernate.sh
```
should at least work "by hand" in Kubuntu too.

---

### Post by justintime32 on 2005-11-12
That works, thanks!

---

