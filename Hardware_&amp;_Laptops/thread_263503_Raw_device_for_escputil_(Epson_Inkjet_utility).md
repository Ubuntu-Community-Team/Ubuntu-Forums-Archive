---
title: "Raw device for escputil (Epson Inkjet utility)"
date: 2006-09-23
forum: Hardware &amp; Laptops
---

### Post by szf on 2006-09-23
I'm trying to discover the current ink levels in my local printer, an Epson Stylus Photo 890.

To do this, you can run the utility against the raw device. Suggested as:
[FONT="Courier New"]$ escputil --ink-level --raw-device /dev/usb/lp0[/FONT]

Ubuntu doesn't have a /dev/usb/ - but it does have a /dev/usblp0... so I substituted that as the raw device. No dice - the utility only echoes the accepted arguments back to me.

Any ideas?

---

### Post by szf on 2006-09-25
I'll reply to self.

This [thread]("http://ubuntuforums.org/showthread.php?t=245843&highlight=escputil") covers the mtink (graphical ink level tool) and leads the escputil with a search.

**_For escputil_**
Despite the CLI args presented - the clean heads switch won't respond unless:
1. You use the "new" printer switch
2. You do not use the long command name [i.e. not --new, but -u; not --raw-device but -r]

i.e. 
$ sudo escputil -c -u -r /dev/usblp0

See [here]("http://ubuntuforums.org/showthread.php?t=122084&highlight=escputil") for more details.

**_For mtink_**
You may need to edit ~/.mtinkrc to point to port /dev/usblp0 on Ubuntu.

**_Other_**
Btw, once the Epson "maintenence" led starts flashing - apparently no tool will read the ink level successfully.

---

