---
title: "internal speakes on HP NC6220 - are alway on"
date: 2009-11-11
forum: Hardware
---

### Post by MartinFrog on 2009-11-11
Hello out there.
I am new to ubunto, and just installed 9.10 on a spare HP NC6220. After a little tricky installation because of the lack of a floppy drive (thanks to 4listair for providing usefull help) I am now up and running.
But: I have a problem with my internal speakers. When i put my NC6220 in the docking station - or when i plug in headphones in the headphone jack - the internal speakes stay on - and they are ofcource supposed to mute - so sound is only in external speakes/headphones.
I should note, that I can turn volume up and down, and mute the hole thing. My problem is only, that the internal speakes do not turn off when they should.

I have really tried to google and search the community for fix - so I hope some here have heard of the problem, og have any suggestions.
Otherwise it might has to be reported as a bug.

best regards
MartinFrog

---

### Post by MartinFrog on 2009-11-12
I found the solutions in other treads in this great forum - I put it here, just to end my own thread.
 
The solution was to go to "terminal" and then type: alsamixer
 
 
then move to the right with your cursor-keys to **[COLOR=#ff0000]Headphone[/COLOR]**, and press 'M' if it says '[COLOR=blue]MM[COLOR=black]'

Press 'Esc' and try again with your **[COLOR=#ff0000]headphone[/COLOR]**.

It worked for me right away.[/COLOR][/COLOR]
 
I must say, that if it was not for my family whom expect Windows XP, Office2003, and iTunes programs and interface, I'd move ubunto to more that my on laptops testdrive.
 
 
 
regards
Martin
 
[COLOR=blue][COLOR=black][/COLOR][/COLOR]

---

### Post by afreytes on 2011-01-07
I just followed your instructions exactly as stated and it worked like a charm. I just installed Ubuntu 9.10 on a used HP Compaq nc6220 which presented the same problem. You saved the day !!! ,,, Thanks

---

### Post by Bucky Ball on 2011-01-07
If you're not too far into the experience, I would advise 10.04 LTS. 9.10 out of support this coming October, 10.04 LTS (long term support) until April 2013. Also, when the next LTS release comes out it's a one click process to upgrade from Update Manager rather than a full reinstall or a terminal frenzy. ;)

You also have options by right clicking the speaker icon and selecting 'Sound Preferences', go to 'Output' and select 'Analogue Headphones' in the drop down list at the bottom. Your setup may be a little different to this.

Welcome to Ubuntu and the forums!

Martinfrog, they'll come around when they see your machine has been on for a year with no issues and they've been blue screening and getting other inevitable Windows issues! Show them Open Office! That installs on Windows machines, too, so you might want to inconspicuously install it while they're out and show them. Once they've played around with it, who knows??? It's a start. You need to download the ISO and burn to disk. Then just put the disk in and install.

[http://distribution.openoffice.org/cdrom/iso_download.html](http://distribution.openoffice.org/cdrom/iso_download.html)

Install instructions for Windows:

[http://download.openoffice.org/common/instructions.html](http://download.openoffice.org/common/instructions.html)

---

