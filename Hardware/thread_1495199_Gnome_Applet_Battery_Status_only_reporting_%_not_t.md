---
title: "Gnome Applet Battery Status only reporting % not time left"
date: 2010-05-27
forum: Hardware
---

### Post by artshark on 2010-05-27
hey guys. I am using the non-stock battery status gnome applet to monitor my battery. instead of displaying the time remaining, it simply says [discharging]. likewise, the stock battery applet does not show timeleft. what's up?
HP Mini 1000, recognizes manufacturer, battery health and everything else is fine, including battery life. 
Thanks,
Art

---

### Post by artshark on 2010-06-03
please!

---

### Post by red_Marvin on 2010-06-05
I am just guessing wildly here, but if you run 
[COLOR="DarkSlateBlue"][FONT="Courier New"]acpi -bi[/FONT][/COLOR]
 in the terminal, do you get a time estimate then?
Perhaps it is unable to get a time estimate if it relies on the acpi stuff directly and it is not listed there...

---

### Post by artshark on 2010-06-06
> **red_Marvin said:**
> I am just guessing wildly here, but if you run 
[COLOR=DarkSlateBlue][FONT=Courier New]acpi -bi[/FONT][/COLOR]
 in the terminal, do you get a time estimate then?
Perhaps it is unable to get a time estimate if it relies on the acpi stuff directly and it is not listed there...
indeed, there is no acpi data. is there any remedy to this? in 9.04, this data was available.

---

### Post by nishant.singh28 on 2010-06-06
try booting in NOAPIC mode.

---

### Post by artshark on 2010-06-06
> **nishant.singh28 said:**
> try booting in NOAPIC mode.
this seems to be a low graphics mode. why would i want to do this?

---

### Post by calumay_oo on 2010-06-13
:confused: i have the same problem with my hp mini 210...
isnt there any solutions yet?

---

### Post by artshark on 2010-06-14
damn you hp!

---

