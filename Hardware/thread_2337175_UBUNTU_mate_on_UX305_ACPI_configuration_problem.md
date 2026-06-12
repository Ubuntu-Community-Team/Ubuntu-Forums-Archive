---
title: "UBUNTU mate on UX305 ACPI configuration problem"
date: 2016-09-15
forum: Hardware
---

### Post by 0wafi0 on 2016-09-15
[COLOR=#111111][FONT=Ubuntu]Hello everyone, I am Wafi. This will be my first post here after I tried doing a bit of digging around and could not find a proper solution to go by. I am new to ubuntu and am planning on switching to Ubuntu Mate completely and at the moment I am running a dual boot with windows.

I am trying to figuring this out. So on my laptop which is a asus ux305ua with an intal core i7-6500U quadcore processor and intel graphics with 8 gb of ram, I just installed ubuntu and managed to get the function keys working (even the brightness keys which needed to be linked).[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]However the issue I am having now is that there is no event in the acpi events folder for the fn+f7 keypress (turn of display) so I was planning on creating my own even. so if I run acpi_listen and press fn+f7 this is the output:[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]video/displayoff DOFF 00000089 00000000 K PNP0C14:00 000000ff 00000000[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]Hence here is the code I have written for the event:[/FONT][/COLOR]
event=video/displayoff DOFF 00000089
action=xset dpms force off
[COLOR=#111111][FONT=Ubuntu]So I've just added this code to a new file in etc/acpi/events[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]However as you can guess this is not working after I restart the acpi service or reboot.[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]I am very new to ubuntu and couldn't find proper resources for this. Kind regards[/FONT][/COLOR]

---

