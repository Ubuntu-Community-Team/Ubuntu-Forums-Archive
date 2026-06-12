---
title: "HP PSC printing in grayscale with black cartridge"
date: 2006-12-20
forum: Hardware &amp; Laptops
---

### Post by inunguak on 2006-12-20
I have a HP PSC 1210, and I want to be able to print in grayscale using only the black cartridge. 

In Windows, I can remove the color cartridge, set it to print in grayscale, and it would work.  If I don't remove the color cartridge, then it would print in grayscale by combining the colors from the color cartridge, thereby wasting colored ink.

In Ubuntu, I can print only using the color cartridge, color or grayscale.  If I remove the color cartridge and try to print in grayscale, it prints out a blank page.

How can I set up my printer to be able to print with the black cartridge?  Thanks.

---

### Post by inunguak on 2006-12-20
Anybody?

---

### Post by inunguak on 2006-12-22
If nobody can help me here, where can I go for help?

---

### Post by steven8 on 2006-12-22
I have the same printer, but have never tried to do what you are trying.  HP obviously cares for the Linux side of things, so maybe they can help?

I will give it a try over the next day or so and let you know what I find out as well.

Keep us up to date if you contact HP.

---

### Post by inunguak on 2006-12-22
Thank you!

---

### Post by steven8 on 2006-12-23
Oh wow.  What program are you trying to print from?  I just drew a little thing in Krita, took out the color cartridge, told my printer to use greyscale, black cartridge, and it worked just fine.  Now, it had two settings.  One for just Greyscale, and one for Greyscale - Black Cartridge.  I used Greyscale - Black Cartridge.

---

### Post by inunguak on 2006-12-26
Wow, it's working now. I was originally trying to print a webpage in Firefox, Google Maps. I'm not sure why it didn't work that time. Sorry for wasting your time.  Thanks, though.

---

### Post by steven8 on 2006-12-28
Time not wasted at all.  I learned some stuff from this.  Glad it's working!!

---

### Post by GeryonD on 2007-03-04
I am having this exact same problem.  I currently have the color cartridge removed and configured it for 'grayscale (black cartridge)' in cups and the printer configuration and it still is printing black pages.  I have restarted cupsys as well to no avail.  If I run 'hp-level' it indeed tells me that my color cartridge is not installed.  

```

Using device: hp:/usb/psc_1200_series?serial=MY31G1202Y5H
 
 Black cartridge
 Part No.: 56 (C6656AN)
 Health: OK
 ----------------------------------------------------------------------------------------------------
 |/////////////////////////////////////////////////////                                             | (approx. 53%)
 ----------------------------------------------------------------------------------------------------
 
 Tri-color cartridge
 Part No.: 57 (C6657AN)/28 (C8728AN)
 Health: Not installed

```

However, if I run 'hp-toolbox' I get an error telling me that I don't have a printer installed and that it must be listed in by cups, which it is.  Other commands provided by HP won't work either, such as 'hp-clean' gives me this:

```

 Using device: hp:/usb/psc_1200_series?serial=MY31G1202Y5H
 Performing type 2, level 1 cleaning...
lp: The printer or class was not found.

```

Any ideas on these issues?  'steven8' mentioned he 'told my printer to use grayscale', was this via the cups interface?  Thanks.

---

### Post by ramjet_1953 on 2007-03-05
Have you got HPLIP installed?

If not, use Synaptic to install it.

In HPLIP go to Tools & Settings and click on the configure button

It will then take you into CUPS

Click on the Set Printer Options button.

You will now have two drop down menus, with a plethora of settable options, including the selection of colour and black cartridges.

ps if you encounter difficulty in saving your chosen settings from within CUPS post again, and I can show you a work-around.

Regards,
Roger :cool:

---

### Post by GeryonD on 2007-03-05
ramjet, thanks for the info.  This is exactly what I did.  I indeed have the newer HP driver installed and chose these items from the CUPS menus to no avail.  :(

---

### Post by GeryonD on 2007-03-06
Okay, so I feel like an idiot.

While the printer was reporting that my black ink cartdrige still have half it's life, it was clogged.  I put a new color cartridge in because I really just needed to be print some things out.  Nothing printed at all.  So I figured at that point something was wrong with the black.  Put in a new black cartridge and it's printing great now.  Now if I can only clean the heads on that older black cartridge to use it again... :)

---

### Post by inunguak on 2007-05-22
Note to self:  Reboot the computer to make it work.  (I reinstalled recently.)

---

