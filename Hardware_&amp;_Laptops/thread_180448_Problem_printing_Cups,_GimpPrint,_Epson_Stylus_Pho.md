---
title: "Problem printing: Cups, GimpPrint, Epson Stylus Photo 890"
date: 2006-05-22
forum: Hardware &amp; Laptops
---

### Post by Keith_Beef on 2006-05-22
I just can't get this to work properly.

I've had this printer for a few years, it should be well known and documented, and should work fine.

Indeed, it worked just fine with Mandrake 8.2 through to 10.2; then I had a few problems when I installed Mandriva (switch from GimpPrint to Gutenprint), but got that sorted.

Then, I started to run out of disc space, and spent a long time fumbling around when I saw error messages like "client-server-error-message-too-long". ](*,) 

Well, after understanding, despite the cryptic error message, where the problem was, I cleared enough space and everything worked again.

All this may sound like it is irrelevent to today's problem, but it proves that my printer was working perfectly well, with a fresh ink cartridge in it, up until I installed Ubuntu 5.10.

Today, I tried for the first time to print a photo on 6" x 4" (15cm x 10cm) Canon paper, from Gimp.

The printed image had a horrible yellowish greenish cast to it. I tried several settings (paper quality, resolution) and made sure that the settings in "Image/Output Settings" -> "Print Color Adjust" are all set to 1.0, but still I get nasty casts; red, green or yellow, and often large expanses of colour.

The test page printed by the gnome-cups-manager tool should print various shades of red, green, blue, cyan, magenta, yellow and black, for the five colours in the colour cartridge, plus black for the black cartridge.

The green and blue bars go from solid black at 0% to solid ink colour (green or blue) at 100%.

However, the red bar goes from solid black at 0% to solid **yellow** at 100%.

The cyan, magenta, yellow and black bars go from white at 0% to solid ink at 100%.

Is it normal for there to be this difference?

I also have a few gripes with the gnome-cups-manager tool.

[LIST]
[*]I can't set the print queue name. I get stuck with names assigned by the tool, like "Stylus-Photo-890", "Stylus Photo 890-1" and "Stylus Photo 890-2".

[*]If I set try to set one of these new queues to be the default, the big tick on the icon disappears from the previous default, but does not appear on the new default.

[*]I cannot set the default paper size or resolution on a new queue that I have added.
[/LIST]

I would have liked to add queues with meaningful names, so I tried pointing my browser at localhost:631 only to find that admin functions have been disabled :( so now I have to dig around in /etc/cups/cupsd.conf to get that sorted out.


Beef.

---

### Post by Keith_Beef on 2006-05-25
[QUOTE=Keith_Beef]
Today, I tried for the first time to print a photo on 6" x 4" (15cm x 10cm) Canon paper, from Gimp.

The printed image had a horrible yellowish greenish cast to it. I tried several settings (paper quality, resolution) and made sure that the settings in "Image/Output Settings" -> "Print Color Adjust" are all set to 1.0, but still I get nasty casts; red, green or yellow, and often large expanses of colour.

The test page printed by the gnome-cups-manager tool should print various shades of red, green, blue, cyan, magenta, yellow and black, for the five colours in the colour cartridge, plus black for the black cartridge.

The green and blue bars go from solid black at 0% to solid ink colour (green or blue) at 100%.

However, the red bar goes from solid black at 0% to solid **yellow** at 100%.

The cyan, magenta, yellow and black bars go from white at 0% to solid ink at 100%.

Is it normal for there to be this difference?
[/QUOTE]

Well, after banging away at this and getting nowhere, I thought that it might be the ink that was running out.

I tried using escputil to check the ink levels, and sure enough there was no reply. Then, printing stopped altogether. Whatever I printed, nothing came out, and the web page queue monitor (localhost:631/printers/Stylus-Photo-890) would tell me "Parallel port busy; will retry in 30 seconds"...

I remember that this is a bug with the Epson printer: when the ink level gets really low, the printer plays silly tricks. 

I replaced the black cartridge, and now printing works.

But when ink levels get low, you can only know this from the way the printer refuses to work. You can't find out from escputil.

That set me wondering if it would be useful to have a sort of "daemon mode"; so escputil could write the ink levels every 30 seconds or so into a log file. That way, a warning of low ink would be visible even after the printer stops communicating with the computer.

I image the log file would look something like this:

```

Thu May 25 12:33:15 EDT 2006
Black : 25 percent
Cyan : 86 percent
Magenta : 85 percent
Yellow : 83 percent
Light Cyan : 84 percent
Light Magenta : 85 percent

Thu May 25 12:33:45 EDT 2006
Black : 12 percent
Cyan : 86 percent
Magenta : 85 percent
Yellow : 83 percent
Light Cyan : 84 percent
Light Magenta : 85 percent

Thu May 25 12:34:15 EDT 2006
Black : 10 percent ** WARNING: INK LEVEL LOW**
Cyan : 86 percent
Magenta : 85 percent
Yellow : 83 percent
Light Cyan : 84 percent
Light Magenta : 85 percent

Thu May 25 12:34:45 EDT 2006
**WARNING: NO RESPONSE FROM PRINTER**


```


Any opinions on this?




Beef.

---

### Post by coolclassic on 2006-05-25
Have you tried turboprint its available @
[http://www.turboprint.de/english.html](http://www.turboprint.de/english.html)

As well as giving you excellent drivers for your printer it gives you a gui to check ink levels, test heads ect

---

### Post by Keith_Beef on 2006-05-25
[QUOTE=coolclassic]Have you tried turboprint its available @
[http://www.turboprint.de/english.html](http://www.turboprint.de/english.html)

As well as giving you excellent drivers for your printer it gives you a gui to check ink levels, test heads ect[/QUOTE]

Sounds nice, and I'll take a look at it, but it's not quite what I was getting at.

Cups and GimpPrint have been good enough (except for when they didn't work, for one reason or another) for the past few years.

I doubt that TurboPrint would solve the problem of the Epson printer not wanting to talk when the ink levels get low...

Beef.

---

### Post by coolclassic on 2006-05-25
Turboprint allows you to check ink with a couple of clicks of the mouse at any time.

---

