---
title: "How do I install a printer?"
date: 2006-06-28
forum: Hardware &amp; Laptops
---

### Post by OtubrabNad on 2006-06-28
I'm going crazy trying to accomplish a seemingly simple task.

I just got an Epson Stylus C62 printer. I connected it to the computer and went to System--> Administration--> Printing, chose New Printer and selected Add Printer. The utility detected the make and model of my printer, so I chose forward. This brings me to the Install Driver step, but I don't know what to do next. 

According to linuxprinting.org, the correct driver for my printer is gimp-print, also known as gutenprint. I searched Synaptic and I already have the driver package installed on my computer. I just have no idea where it is. When I click Install Driver it wants me to manually find the location of the correct ppd file. But I don't know where the driver is located. Does this make any sense and can someone help me? Thanks.

---

### Post by johnc4510 on 2006-06-28
The install driver bar is for choosing the driver. If the correct driver is showing in the bar, the app will use that one to drive the printer. You don't have to manually search your computer for it.

---

### Post by johnc4510 on 2006-06-28
I just ran the printer setup to see which driver it had in the driver bar, and it wasn't the one you named. However it should be noted that it is the suggested driver. If I were you, I would go ahead and set that one up and finish the printer install and see if it works.

---

### Post by OtubrabNad on 2006-06-28
[QUOTE=johnc4510]The install driver bar is for choosing the driver. If the correct driver is showing in the bar, the app will use that one to drive the printer. You don't have to manually search your computer for it.[/QUOTE]

There's no driver showing in the bar. The manufacturer, model, and driver fields are all blank.

Perhaps this link may help someone more knowledgeable than I: [http://www.linuxprinting.org/show_printer.cgi?recnum=Epson-Stylus_C62](http://www.linuxprinting.org/show_printer.cgi?recnum=Epson-Stylus_C62)

---

### Post by OtubrabNad on 2006-06-28
I found the solution in the following thread:
[http://ubuntuforums.org/showthread.php?t=204870](http://ubuntuforums.org/showthread.php?t=204870)

I suppose it's best to search for the solution before posting a new thread!

---

### Post by drtvasudevan on 2006-06-29
actually it seems a genuine problem
i tried and though it shows a suggestion and you click forward you end up with a window to point to the ppd

in my case i had to find a ppd and so turned out ok.
but what is supposed to be the procedure?

of course for the present you can go to linuxprinting .org and get a ppd made
just a few kb like 24kb

but i would like to know the proper way.

tv

---

