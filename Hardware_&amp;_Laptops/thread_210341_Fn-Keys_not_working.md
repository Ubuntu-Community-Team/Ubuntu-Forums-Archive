---
title: "Fn-Keys not working"
date: 2006-07-06
forum: Hardware &amp; Laptops
---

### Post by kryptosaint on 2006-07-06
Trying to get the Fn-Keys to work on my new Toshiba laptop. Have tried installing fnfx but unfortunately this program doesn't support my Phoenix Bios. 

Does anyone know of an alternative solution. Thankyou in advance... 

Spec:
Toshiba Satellite Pro A100
Linux version 2.6.15-23-386

---

### Post by tonyr on 2006-07-06
You may need a different keyboard layout: **System->Preferences->Keyboard**, Layout
tab.  You can also run **xev** in a terminal to see what keycodes the Fn keys are 
producing (a small window  opens; put the mouse in that window and hit any key).

There is a package, **xkeycaps**, that provides a utility for more extensive keyboard
management (read about it [here]("http://www.jwz.org/xkeycaps/")).

---

### Post by kryptosaint on 2006-07-06
> **tonyr]You may need a different keyboard layout: **System->Preferences->Keyboard**, Layout
tab.  You can also run **xev** in a terminal to see what keycodes the Fn keys are 
producing (a small window  opens said:**
> here[/URL]).

Have tried the above suggestions. Cannot find a similar keyboard layout, even in xkeycaps. Is it possible to create your own keyboard layout file?

Also when operating xev the 'Fn' does not display a code?

---

### Post by tonyr on 2006-07-06
[QUOTE=kryptosaint]Have tried the above suggestions. Cannot find a similar keyboard layout, even in xkeycaps. Is it possible to create your own keyboard layout file?

Also when operating xev the 'Fn' does not display a code?[/QUOTE]

Yes, it is possible, but it depends on the Fn keys producing keycodes when pressed.
If the Fn keys are not doing that,  I would suspect that the keyboard is broken.
If you are dual booting with windows, do the Fn keys work there? 

You might be able to use an external keyboard (USB for example) and test Fn key
functionality in the OS that way.

---

### Post by kryptosaint on 2006-07-06
[QUOTE=tonyr]Yes, it is possible, but it depends on the Fn keys producing keycodes when pressed.
If the Fn keys are not doing that,  I would suspect that the keyboard is broken.
If you are dual booting with windows, do the Fn keys work there? 

You might be able to use an external keyboard (USB for example) and test Fn key
functionality in the OS that way.[/QUOTE]

Just rebooted my system into Windows XP and found the Fn Keys functioning correctly, so I know the 'Fn' key is not broken, although it's a mystery why no code is displayed. 

It's also interesting to note how a code is displayed for every other key except 'Fn', even the windows (Super_L) key works!

---

### Post by tonyr on 2006-07-06
When you run **xkeycaps** you have the option of writing an output file, with a name
of the form .xmodmap-<your-machine-name>.  The output button will ask if you want
to write all keys or only changed keys.  Choose all keys.  A message box will pop up
showing the file name and a suggestion to add a line to your shell startup file.

I don't know if this will work, but it's worth a shot.

---

### Post by cracker on 2006-07-07
I'd also try pressing fn+[key] and comparing it to that key's normal output, to see if its a manual, non-software toggle.

---

### Post by kryptosaint on 2006-07-07
> **tonyr said:**
> When you run **xkeycaps** you have the option of writing an output file, with a name
of the form .xmodmap-<your-machine-name>.  The output button will ask if you want
to write all keys or only changed keys.  Choose all keys.  A message box will pop up
showing the file name and a suggestion to add a line to your shell startup file.

I don't know if this will work, but it's worth a shot.

Tried the above which works very nicely for every other key but sadly the Fn key still does not function.

Further investigation reveals that Toshiba wrote a special Fn key driver for Windows only. I think the only way around this problem is to perform some reverse engineering and produce a Linux driver similar to this guy below.

[http://tz.exit0.net/tecras1.html](http://tz.exit0.net/tecras1.html)

Thanks for your help.

---

### Post by tonyr on 2006-07-07
[This]("http://tuxmobil.org/toshiba.html") link, which you probably already visited, 
says something about the Fn keys and ACPI on some Toshiba
laptops.  Have you tried turning acpi off in the grub boot menu file?

---

### Post by EpicCrusadr on 2006-07-10
Which model Laptop are you using? On my Satellite M55 most all of the Fn keys work except: Powersave, Screen Lock, and stand by.

---

