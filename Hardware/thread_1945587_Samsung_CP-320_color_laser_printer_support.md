---
title: "Samsung CP-320 color laser printer support"
date: 2012-03-23
forum: Hardware
---

### Post by frankvw on 2012-03-23
Hi, everyone,

I have searched for this but not found anything, so let me ask the question. :-) I have bought a shiny, brand-spanking-new Samsung CP-320 color laser printer. And as expected, getting it to work under Ubuntu (Natty) on my laptop was actually easier than on XP. The printer was recognized, the foomatic driver was missing but got downloaded automagically, and all I had left to do was to select my printer from the list.

Of course that's where the fun started: the CP-320 is not listed. However I chose the closest option (CP-315) and at least my test pages come out perfectly (although there is some bad moiré in the gray scale bar on the color test page).

My questions at this point:
[LIST]
[*]Is there a foomatic driver for the CP-320 and if so, where, and how do I painlessly integrate it with my Natty distro?
[*]Is there any major difference between the CP-320 and CP-315 that might cause problems when I try to use my 320 with the 315 driver?
[*]Eventually I need to connect this printer to my Linux server, which runs (if memory serves) Karmic server. I've fought Great Battles with CUPS on that thing in the past, so if there is an easy way to do this, any suggestion on where to look for it would really make my day.
[/LIST]

Thanks!

// FvW

---

### Post by Bucky Ball on 2012-03-23
Tried this???

[http://www.samsung.com/hk_en/support/model/CLP-320/XSS-downloads?isManualDownload=true](http://www.samsung.com/hk_en/support/model/CLP-320/XSS-downloads?isManualDownload=true)

---

### Post by frankvw on 2012-03-26
> **Bucky Ball said:**
> Tried this???

[http://www.samsung.com/hk_en/support/model/CLP-320/XSS-downloads?isManualDownload=true](http://www.samsung.com/hk_en/support/model/CLP-320/XSS-downloads?isManualDownload=true)

Yep. I now have. :-) But so far it hasn't been an unqualified success. 

First off, the Samsung Unified Driver Package for Linux comes with documentation in HTML format, with a Javascript pop-up stating that "This manual is optimized for IE6 and later versions". Nice. The autorun file in the cdroot directory of the driver package doesn't work, the installer script is mostly broken (half the files aren't copied, and some of the rest is copied to the wrong location) and the file permissions are mostly wrong, too, causing CUPS to refuse running filters because the permissions are insecure. (Which makes sense from CUPS's standpoint: if a filter is flagged world writeable, anyone could substitute the filter with any program at all which will then be run with root privileges, and bang, your system security has been irreversibly compromised - so I approve of that.)

After much manual file copying and changing file permissions I've finally managed to get to a point where CUPS will crank a job out to the printer. However, the test page is printed in two duplicate, identical, narrow columns, each a half-size version of the page, separated by a series of white bands every 3 mm or so. Not good. According to Google, I'm not the only one with that problem, and the solution seems to be related to file permissions (but I'm not sure yet which ones) and the procedure to fix it involves replacing something with something else, and then changing something. Or something like that.

Strangely, though, via a Samba share the printer works fine from Windows clients. So it's definitely a problem with the unified driver package. Because when I hang the printer off the USB port on my Ubuntu Workstation laptop (so that it uses the foomatic drivers from the repositories) it works fine without me having to fiddle with anything at all - it's literally plug-and-play and it's actually easier to get the printer working correctly under the Ubuntu Desktop distro.

So. Kudos to the Ubuntu developers, a so-so for CUPS (which remains shakey and has its known problems) but a fat zero to Samsung's Unified Driver rubbish. :-(

Onward...

// FvW

---

