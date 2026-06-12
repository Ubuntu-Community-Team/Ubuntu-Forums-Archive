---
title: "ACER ASPIRE 4736z display problems"
date: 2011-06-23
forum: Hardware
---

### Post by proudchild on 2011-06-23
Hello guys, i tried like 3 times installing ubuntu on my notebook and i get a wierd problem with my default notebook monitor, it get really dark, and i cant see squad, i thout it would be a problem with the ubuntu 11.04 live, but no, i tried fedora 15, centos 5.6 debian, all of those make the display goes off as soon as the X11 start, and i use xrandr and i dont get a display list, but when i plug a vga monitor i get a "mirror" image of my desktop fine, i really need help getting rid of micro$oft window$...


thanks for the help in advance. :(

UPDATE: PROBLEM SOLVED

---

### Post by Toz on 2011-06-23
Try appending the kernel parameter **acpi_osi=Linux** to the kernel line after the words "quiet splash" but within the quotes. Something like **"quiet splash acpi_osi=Linux"** 

To test, see:[https://help.ubuntu.com/community/Grub2#Editing%20the%20GRUB%202%20Menu%20During%20Boot]("https://help.ubuntu.com/community/Grub2#Editing%20the%20GRUB%202%20Menu%20During%20Boot")

---

### Post by Blasphemist on 2011-06-23
The parameter mentioned needs this syntax.
```
acpi_osi=\"Linux\"
```
This allows the parser to correctly interpret the parameter and what you'll then see on the line in Grub2 is
```
acpi_osi=Linux
```
The back slashes are escape characters.

---

### Post by Toz on 2011-06-23
So then quotes in quotes?
```
"quiet splash acpi_osi=\"Linux\""
```

Seems awkward.

---

### Post by Blasphemist on 2011-06-23
Yes, here is the line you edit in /etc/default/grub
```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash acpi_osi=\"Linux\""
```

---

### Post by Toz on 2011-06-24
Oh. It parses it out to **acpi_osi="Linux"**
Interesting.

---

### Post by proudchild on 2011-06-26
oh! ill try those ones, i am currently using a vmware machine under windows to play ubuntu 11.04, but it sucks pretty hard, thanks guys!

---

### Post by proudchild on 2011-06-27
Good news everyone [by professor putricide]

i finally managed to get through the problem
hint for those with similar issues
together with the acpi_osi=Linux 
also put acpi_backlight=vendor

then use the default keyboard keys to change the brightness, it might get ackward at first, but you get through it...

---

### Post by Toz on 2011-06-27
Glad to hear. Please mark this thread as solved.

---

### Post by gabak on 2012-05-19
hi
i saw this forum i got the same problem but i know how to edit /boot/grub/grub.cfg but i dont know where to put that line you said about adding the thing for the kernel.

---

### Post by gabak on 2012-05-19
plz can you tell me where should i put that?
plz step by step


> **Blasphemist said:**
> The parameter mentioned needs this syntax.
```
acpi_osi=\"Linux\"
```
This allows the parser to correctly interpret the parameter and what you'll then see on the line in Grub2 is
```
acpi_osi=Linux
```
The back slashes are escape characters.

---

### Post by gabak on 2012-05-19
wich one should i use? the first one or the second one?
i got ubuntu 12.04

i have done this but it does nt work

the line i edit in /etc/default/grub
Code:
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash acpi_osi=\"Linux\""



> **Blasphemist said:**
> The parameter mentioned needs this syntax.
```
acpi_osi=\"Linux\"
```
This allows the parser to correctly interpret the parameter and what you'll then see on the line in Grub2 is
```
acpi_osi=Linux
```
The back slashes are escape characters.

---

