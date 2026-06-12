---
title: "Drivers for Canon M 5220 All-in-on printer (and scanner)"
date: 2013-03-26
forum: Hardware
---

### Post by Phantom010 on 2013-03-26
Hello everybody,

I'm new to the forum, and although I'm an advanced Windows user, I'm only a beginner when it comes to Linux. I've just recently installed Ubuntu 12.04 LTS on my Windows XP Pro computer with Wubi.

I've had a little trouble finding a working driver for my Canon printer, but finally managed to install one and the printer is recognized alright. However, even if I've followed the instructions from **[[COLOR=#0000ff]HERE[/COLOR]]("http://linuxtidbits.wordpress.com/2011/07/14/canon-pixma-mg5220-ubuntu-setup/")**[COLOR=#000000] (installed both drivers), [/COLOR]Ubuntu will just not recognize the scanner, even if ScanGear is showing inside Gimp. Tried it many times.

Any ideas why it's not recognized and how can I make it work?

Thanks in advance.

---

### Post by pdc on 2013-03-26
I don't know Sooty, as Harry Corbett might have said.............

if I type 

> [COLOR="#FF0000"]scangearmp[/COLOR]

in a terminal, I get what is shown in the thumbnail

........what do you get ?

also, can you [COLOR="#0000FF"]copy and paste[/COLOR] these queries into a terminal and copy and paste the results back: 

> [COLOR="#FF0000"]dpkg -l | grep cnijfilter[/COLOR]

> [COLOR="#FF0000"]dpkg -l | grep scangear[/COLOR]

can you also tell us if you are using 32bit or 64bit..

...on my MG3100 I need to ensure the device is live by pressing the [COLOR="#0000FF"]**ON**[/COLOR] button.....otherwise it sleeps through my attempts to awaken it..................

---

### Post by Phantom010 on 2013-03-27
> **pdc said:**
> I don't know Sooty, as Harry Corbett might have said.............

if I type 



in a terminal, I get what is shown in the thumbnail

........what do you get ?

also, can you [COLOR=#0000FF]copy and paste[/COLOR] these queries into a terminal and copy and paste the results back: 





can you also tell us if you are using 32bit or 64bit..

...on my MG3100 I need to ensure the device is live by pressing the [COLOR=#0000FF]**ON**[/COLOR] button.....otherwise it sleeps through my attempts to awaken it..................
Thank you for your reply.

I'm using 32-bit.

```
steve@ubuntu:~$ dpkg -l | grep cnijfilter
ii  cnijfilter-common                            3.40-1                                           IJ Printer Driver for Linux.
ii  cnijfilter-mg5200series                      3.40-1                                           IJ Printer Driver for Linux.
steve@ubuntu:~$ dpkg -l | grep scangear
ii  scangearmp-common                            1.60-1                                           ScanGear MP for Linux.
ii  scangearmp-mg5200series                      1.60-1                                           ScanGear MP for Linux.
```

---

### Post by Phantom010 on 2013-03-27
Forgot to mention that my Canon printer/scanner is indeed "live" when trying to make Ubuntu recognize the scanner. I had no choice either for the printer part only. Otherwise, nothing would show.

---

### Post by pdc on 2013-03-27
does it work as a scanner by pressing the scan button.......

other than that, I can only think of deleting the scangear and re-installing........... you seem to have the correct packages......common first and then 5200............ I have a 3100 and it was just fine....

I now note this

> on my Windows XP Pro computer with Wubi.

so I wonder if this is somehow an issue................ I could only suggest being bold and installing a small new partition for ubuntu.............I have understood XP and ubuntu play well together............... because anyone I have helped with scangear finds it installs and works well

---

### Post by Phantom010 on 2013-03-27
Oh, and that's not the only problem. I cannot find any settings, anywhere, to print in color. In XP, I get a complete printer control panel with all the settings: color, ink levels and much much more. How can Canon provide a Linux driver that is so incomplete!?! [IMG]http://i1206.photobucket.com/albums/bb460/Phantom010/Question2.gif[/IMG]

---

### Post by pdc on 2013-03-27
if you copy and paste

> [COLOR="#FF0000"]cngpij P MG5200[/COLOR]

into a terminal, and hit enter

.............what do you get?

....if successful, one needs to create a launcher........

as shown in the attached thumbnail........

various companies supply CLI things for linux...... they can't tweak GUI applications for each distro.................so one tends to get a little oil on one's hands with linux.......changing spark plugs and cleaning the oil filter!

and another utility is MENU......Administration...........Printing .........right-click on MG5200 and edit properties there........as in attached thumbnail

---

### Post by MyR on 2013-03-27
There's another guide posted here: [http://linuxdeal.com/Printer-PIXMA-MG5220#reviews](http://linuxdeal.com/Printer-PIXMA-MG5220#reviews)
Not sure if it might help... You could add a review either way ;]

Peace.

---

### Post by Phantom010 on 2013-03-27
> **MyR said:**
> There's another guide posted here: [http://linuxdeal.com/Printer-PIXMA-MG5220#reviews](http://linuxdeal.com/Printer-PIXMA-MG5220#reviews)
Not sure if it might help... You could add a review either way ;]

Peace.

Thank you. I'll read it.

---

### Post by Phantom010 on 2013-03-27
> **pdc said:**
> if you copy and paste



into a terminal, and hit enter

.............what do you get?

....if successful, one needs to create a launcher........

as shown in the attached thumbnail........

various companies supply CLI things for linux...... they can't tweak GUI applications for each distro.................so one tends to get a little oil on one's hands with linux.......changing spark plugs and cleaning the oil filter!

and another utility is MENU......Administration...........Printing .........right-click on MG5200 and edit properties there........as in attached thumbnail

[COLOR=#FF0000]cngpij P MG5200 [/COLOR]gave me a lot more settings! Thanks![COLOR=#FF0000]

[/COLOR][COLOR=#000000]How can I access that from the GUI? Where is it located? I'd like to make a shortcut to it.[/COLOR][COLOR=#FF0000]


[/COLOR][COLOR=#000000]Any idea for the scanner?
[/COLOR]

---

### Post by pdc on 2013-03-27
> How can I access that from the GUI? Where is it located? I'd like to make a shortcut to it.

looks like mine is in /usr/bin (meaning binary........) however as you found out, from the terminal the system loads it......

you need to make what is called a launcher........ to launch it each time ..........

I think this guide

[http://www.codemarvels.com/2012/05/create-shortcut-launcher-on-desktop-on-ubuntu-12-04/](http://www.codemarvels.com/2012/05/create-shortcut-launcher-on-desktop-on-ubuntu-12-04/)

is good

> [COLOR="#FF0000"]sudo apt-get install gnome-panel[/COLOR] installs the ability

> [COLOR="#FF0000"]gnome-desktop-item-edit ~/Desktop/ --create-new[/COLOR] loads the device.....

command must be

> [COLOR="#0000FF"]cngpij P MG5200[/COLOR] but names etc are up to you, as is the icon you choose!

I do suspect the Wubi is what is preventing your system loading the scanner: again, I can only suggest a small ubuntu partition and that should allow you to use the scanner component

---

### Post by Phantom010 on 2013-03-28
Thanks. That works. However, I've changed the icon and made it a "printer" icon, but when I drag it to the launcher, it reverts to some kind of generic icon [IMG]http://img138.imageshack.us/img138/8657/slection001p.png[/IMG] . It just won't stay as I want it: [IMG]http://img266.imageshack.us/img266/8764/slection002.png[/IMG] .

---

### Post by Phantom010 on 2013-03-28
Standby. I think I may know why. Will post back soon. :)

---

### Post by Phantom010 on 2013-03-28
Nope. The icon always changes when I drag it to the launcher.

---

### Post by Phantom010 on 2013-03-28
I'm supposed to send the desktop shortcut I've created to /usr/share/applications, but I'm always denied [COLOR=#ff0000]permission[/COLOR]! Man, this is beginning to remind me of why I didn't want to go from XP to Windows 7... :roll:

---

### Post by Phantom010 on 2013-03-28
Finally did it! :)

Now, if I can only figure out why the scanner will not be detected by Ubuntu. :(

---

### Post by Phantom010 on 2013-03-28
Found the solution [**[COLOR=#0000ff]HERE[/COLOR]**]("http://askubuntu.com/questions/182604/canon-mp280-all-in-one-prints-but-scanner-not-recognized").  :) 

Problem Solved!

Thank you very much for your help, guys!

[I]
By the way, if there is any way to mark this thread as "solved", I just don't see it, sorry.[/I]

---

### Post by Phantom010 on 2013-03-28
When trying to edit printer settings through that custom shortcut - Gnome print ([COLOR=#0000FF]cngpij P MG5200[/COLOR][COLOR=#000000]), they just [/COLOR]won't stick, and don't apply to anything I print. When I open the panel again, settings haven't been changed at all! Why? :confused:

---

### Post by Phantom010 on 2013-03-28
The reason I need those printer settings is that LibreOffice and Thunderbird do not include all settings, especially duplex printing, nor can I choose to print Standard or Fast.

Can it be a system-wide permission thing?

---

### Post by Phantom010 on 2013-03-28
OK, got it. Thank God there's CUPS! :)

Still haven't found Standard or Fast print (it's print quality), but at least I can use Duplex.

If you can think of anything else, please let me know.

---

### Post by pdc on 2013-03-28
> [COLOR="#EE82EE"]Found the solution HERE.

Problem Solved![/COLOR]

..........my reading of the thread that you said solved your problem....................was that it was yet another source of the deb files you needed............

...........so was it this component

> [COLOR="#008000"]The OS then prompted me to install 4 new packages which I did and everything seems to be working now![/COLOR]

ie help me understand what worked; 

and what actually does work for you now

________________________________________________________________________________

standard or fast print.................. I just print pages so I haven't attempted to resolve such things...

I suspect one tweaks the settings in the ppd file...........if you google on that?

I enclose a screenshot and I suspect one adds things to the ppd

you can see where it is from the top of the page...........there is a very useful SEARCH function that one can set up on a launcher to find .........things.....................at home I have my wife.............on the computer, I resort to SEARCH................

eg 

[http://www.cups.org/documentation.php/spec-ppd.html](http://www.cups.org/documentation.php/spec-ppd.html)

and particularly this

[http://ubuntuforums.org/showthread.php?t=1602839](http://ubuntuforums.org/showthread.php?t=1602839)

this guy said to expand what I showed you in the [COLOR="#0000FF"]thumbnail[/COLOR] to 

> [COLOR="#008000"]*OpenUI *Resolution/Output Resolution: PickOne
*DefaultResolution: 4800dpi[/COLOR]
[COLOR="#EE82EE"]*Resolution 600dpi/600 DPI: "<</HWResolution[600 600]>>setpagedevice"
*Resolution 1200dpi/1200 DPI: "<</HWResolution[1200 1200]>>setpagedevice"
*Resolution 2400dpi/2400 DPI: "<</HWResolution[2400 2400]>>setpagedevice"
*Resolution 2400dpi/4800 DPI: "<</HWResolution[2400 4800]>>setpagedevice"
*Resolution 2400dpi/9600 DPI: "<</HWResolution[2400 9600]>>setpagedevice"[/COLOR]
[COLOR="#008000"]*CloseUI: *Resolution[/COLOR]


let us know how it goes

---

### Post by Phantom010 on 2013-03-28
[FONT=verdana]The following commands were used:[/FONT]


sudo add-apt-repository ppa:michael-gruz/canon-trunk

sudo apt-get update

[FONT=verdana]
Then, I ran the updates that were shown. 

ScanGear finally worked and the scanner was recognized.
[/FONT]

---

### Post by Phantom010 on 2013-03-28
Resolution is stuck at 600 dpi and is the only resolution I can see, althought the following is what I see in my ppd file:

```
*OpenUI *Resolution/Output Resolution: PickOne
*DefaultResolution: 600dpi
*Resolution 600dpi/600 dpi: "<</HWResolution[600 600]>>setpagedevice"
*Resolution 1200dpi/1200 dpi: "<</HWResolution[1200 1200]>>setpagedevice"
*Resolution 2400dpi/2400 dpi: "<</HWResolution[2400 2400]>>setpagedevice"
*CloseUI: *Resolution
```

CUPS doesn't even show any resolution settings whatsover.

---

### Post by Phantom010 on 2013-03-28
This is what CUPS shows:

[IMG]http://img29.imageshack.us/img29/6541/slection003r.png[/IMG]

---

### Post by pdc on 2013-03-28
.........interesting...............

I think after installing any ubuntu OS, the advice is [COLOR="#FF0000"]sudo apt-get update[/COLOR] so I wonder if this was what was needed............as you already had the drivers installed...........michael gruz carefully collects all the canon drivers..............

to alter resolution settings in LibreOffice ,

> [COLOR="#FF0000"]usr/lib/libreoffice/program/spadmin[/COLOR]

.........as before, make a launcher

launch it.......click on your printer..........click on properties..............I see resolution there..................can you tweak from there?

......thumbnail enclosed..................

---

### Post by Phantom010 on 2013-03-28
No, the resolution cannot be changed. 600 dpi is the only one showing.

---

### Post by Phantom010 on 2013-03-28
Just noticed that the resolution shows different when I try to print a photo with Shotwell. It goes up to 1200. I wonder why I cannot reach the maximum my printer is supposed to give me.

I'm really confused when trying to understand printer and scanner resolution. What's [COLOR=#ff0000]Up to[/COLOR] [COLOR=#ff0000]9600 x 2400 dpi[SUP]3[/SUP][/COLOR] ? What's the 1200 dpi I see?

Here are the Canon PIXMA MG5220 specs:

[http://www.usa.canon.com/cusa/support/consumer/printers_multifunction/pixma_mg_series/pixma_mg5220#Specifications](http://www.usa.canon.com/cusa/support/consumer/printers_multifunction/pixma_mg_series/pixma_mg5220#Specifications)

---

### Post by Phantom010 on 2013-03-28
By the way, do you know a good free photo printing software? (like EasyPhotoPrint)

---

### Post by pdc on 2013-03-28
google suggests this to me

[http://linuxprinting.sourceforge.net/](http://linuxprinting.sourceforge.net/)

...........in linux, folks take "free" to mean.........................free as in beer................the purists see "free" as meaning .............................as in .................................."free speech".......................

the good folks at turboprint have been supporting firstly the Amiga.......and more recently linux

[http://www.zedonet.com/en_p_turboprint_driver.phtml?printer=Canon_PIXMA_MG5200series](http://www.zedonet.com/en_p_turboprint_driver.phtml?printer=Canon_PIXMA_MG5200series)

they make printer drivers ............they allow much tweaking..................... it costs a few bob but like most things in this world, you get what you pay for .....it's about $US37 .......and is good for many years.......

---

### Post by Phantom010 on 2013-03-29
That photo printing program seems a little old, but I may give it a try.

As for TurboPrint, the trial version, like most trial versions, is not the full version. How can we really test a product before buying it when it doesn't include all features? :rolleyes:

Thank you very much for helping. I've learned quite a few things in the process.

---

### Post by Phantom010 on 2013-03-29
Just tried TurboPrint. Although it increases the price of today's cheap printers considerably, it's excellent! A lot more features, including print quality settings I was looking for. If this isn't the full version yet, can't wait to see it! I guess it's better, and cheaper, than bying Windows 7 or 8 in April 2014 (end of XP support)...

I'll go through the trial period and we'll see...

Thanks again.

By the way, now that I'm using TurboPrint, I can do exactly what I want with Shotwell.

Found how to mark my thread as solved. A nice button, like the one I see on other forums would have been nice... ;) :)

---

