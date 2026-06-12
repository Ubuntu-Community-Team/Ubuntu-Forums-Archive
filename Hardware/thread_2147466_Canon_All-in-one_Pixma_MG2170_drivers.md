---
title: "Canon All-in-one Pixma MG2170 drivers?"
date: 2013-05-22
forum: Hardware
---

### Post by DragonFart on 2013-05-22
i've downloaded the driver from here( [http://support-sg.canon-asia.com/contents/SG/EN/0100392902.html](http://support-sg.canon-asia.com/contents/SG/EN/0100392902.html) ) installed it, rebooted computer, launched xsane scanner, still it gives me cant detect any scanner device thing. The printer works great but scanner..meh :(

Thanks in advance.

I'm running ElementaryOS (based on Ubuntu 12.04) 64bit
Printer: Canon All-in-one Pixma MG2170.

---

### Post by Resistent on 2013-05-22
I have also Canon Pixma.  (MG2250).

Try to run  scangearmp on terminal.
This is the scanner software you installed

You have to switch on your Pixma, otherwise scangearmp says "no scanner found"

Yup, looks like XSANE cannot find your scanner, also if switched on. --> Use the "scangearmp" in terminal.

---

### Post by pdc on 2013-05-22
resistent is absolutely right

you can get the guide to ScanGear from here

[http://support-asia.canon-asia.com/contents/ASIA/EN/0300578001.html](http://support-asia.canon-asia.com/contents/ASIA/EN/0300578001.html)

it comes down as [COLOR="#008000"]guidemg2100series-sd-1.80-1_en.tar.gz[/COLOR] so if you open with archive manager; and extract files to Desktop and look for the icon guide_index.htm and click or double-click on that; it opens a tab in Firefox and you may find some helpful stuff there;

Enjoy

> [COLOR="#FF0000"]scangearmp[/COLOR]

........most folks make a launcher to ........launch [COLOR="#0000FF"]ScanGearMP[/COLOR] in future ......

the thumbnail shows what the guide looks like when you open it

___________________________________________________________________

and you can also run it from within GIMP  [COLOR="#EE82EE"]File....................Create..........ScanGearMP[/COLOR]...........

---

### Post by DragonFart on 2013-05-22
wow thanks guys that worked great! i went to ubuntu irc channel no one was able to figure out how to make it work. i guess u guys are the better ones huh :)
but is there a way to run scangearmp off terminal? its my sister who wnated to use the scanner and shes like computer dumb(even on windows machine) getting her to type something on terminal is like waiting for a disaster to happen :D

---

### Post by pdc on 2013-05-23
if you create a launcher

[http://www.howopensource.com/2012/10/create-application-launcher-add-icon-to-unity-ubuntu-12-10/](http://www.howopensource.com/2012/10/create-application-launcher-add-icon-to-unity-ubuntu-12-10/)

that creates an icon for someone to click on.....to launch ScanGearMP

so the commands are

> [COLOR="#FF0000"]sudo apt-get install --no-install-recommends gnome-panel[/COLOR]

then 

> [COLOR="#FF0000"]sudo gnome-desktop-item-edit /usr/share/applications/ --create-new[/COLOR]

the [COLOR="#EE82EE"]create new[/COLOR] command opens a dialogue box, as in the thumbnail I enclose

the [COLOR="#0000FF"]**command**[/COLOR] in the dialogue box that opens must be

> [COLOR="#FF0000"]scangearmp[/COLOR]

but the name can be whatever you so want .........

let us know how it goes

____________________________________________________________

to edit LibreOffice settings you can create a launcher for that...........using the above ......

its command in the dialogue box is 

> [COLOR="#FF0000"]/usr/lib/libreoffice/program/spadmin[/COLOR]

with the launchers you can change the icon picture as you so wish......endless tinkering!!

---

### Post by Resistent on 2013-05-23
Also, in ScanGearMP I had better results in "Advanted Mode"  (I wanted smaller file size, with acceptable scanning quality)

---

### Post by DragonFart on 2013-05-23
> **pdc said:**
> 
let us know how it goes

it went super well! dude you're a legend! thanks :)

---

