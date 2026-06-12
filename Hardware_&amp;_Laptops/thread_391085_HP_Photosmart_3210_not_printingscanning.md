---
title: "HP Photosmart 3210 not printing/scanning"
date: 2007-03-22
forum: Hardware &amp; Laptops
---

### Post by volksolwagen57 on 2007-03-22
hey everybody, i'm new to ubuntu. so far i love it, maybe because i'm patient. i have this hp photosmart 3210 all in one printer that was given to me as a gift when i fixed/cleaned up my friend's windows computer:) . initially, i installed it successfully using the **hpijs** driver in the printer installation wizard (cups?). i was able to print a test page (kind of, i needed to push the paper in the tray for the drive rollers to pick up paper, and when they did they picked up like twelve pages). when i tried to use the scanner the LCD display says "No Scan Options" and then is says "Refer to device documentation to troubleshoot." 
so, if figured the printing function was being recognized and i moved on to try troubleshoot the scanner. I looked up HPAllInOne Community help to work it out. the help page is cryptic and not stupid-proof. i installed the **hpoj** driver for the scanner and this did nothing.
i installed this driver and the driver to allow the QT function on the LCD panel of the printer to work and i just jacked everything up.
now i can't print anymore, even when reinstalling the **hpijs** driver:( 
i can't scan either:( 
and even if i could print, i need to reconfigure the paper type. I think my paper is too light.
can anyone help me please!?!?

---

### Post by 11hjpphty76lkjj on 2007-03-23
Please do NOT use hpoj.  hpoj is very old (and I do mean VERY old) and outdated and if it's installed will not work with hpijs.  Using synaptic remove hpoj and hplip/hpijs and install the latest version from;

[http://hplip.sf.net](http://hplip.sf.net)

The automated installer is fully tested with ubuntu, and your printer is fully supported.

Hope this helps.

---

### Post by volksolwagen57 on 2007-03-24
hey kalo! thanks for the input. this is what i did: i took your advice and uninstalled hpoj from the synaptic package manager and all of its supplementary software. instead of downloading the hplip driver, i reinstalled hpijs, the one that is recommended by the cups printer installation wizard. i now have the ability to print! thanks :)!
now, i'm hardheaded and i didn't follow all of your professional advice. i wanted to go the easy way and use the wizard because of my separation anxiety with windows.
i still can't scan. i did go to the link and downloaded the driver but it was a *.run* type executable and i wasn't sure how to use it. i deleted it and reinstalled hpijs and now the printer funcion is working. here are my questions:
should i be able to scan with hpijs?
if i should be able to and i'm not, what did I miss?
does hplip allow for scan support? support for all the All-in-One funtions?
if so, how do i install the driver? how do i execute/install a *.run* driver?
please help?
thanks for your time and patience and help and so on...

---

### Post by 11hjpphty76lkjj on 2007-03-27
If you please--remove hpijs (it's an older version in synaptic anyway.)

And follow the directions here:

[http://hplip.sourceforge.net/install/install/index.html](http://hplip.sourceforge.net/install/install/index.html)

:)

In addition I'd be interested in any feedback you have about the instructions.  I just updated them with the last release.

Thanks!

---

### Post by suspicion4u on 2007-07-04
hey kalo im kinda new to gnome and when i go to try and install 2.7.6 its telling me that it doesnt or cant read the character coding. so i tried to download tar.gz using the instructions on that page that you made reference to and it didn't work either. help me please!!!!!!!

---

### Post by 11hjpphty76lkjj on 2007-07-05
Can you paste the exact error message?

Thanks!

A

---

### Post by suspicion4u on 2007-07-05
doing so from console terminal it says... sh hplip-2.7.6.run
sh: Can't open hplip-2.7.6.run

and doing so from the icon it says... Could not open the file... hplip-2.7.6.run gedit has not been able to detect the character coding.
Please check that you are not trying to open a binary file.
Select a character coding from the menu and try again

---

### Post by 11hjpphty76lkjj on 2007-07-05
Sounds like the download was corrupted.  Perhaps delete it and re-download it.  Then run the sh hplip-2.7.6.run .

A

---

### Post by suspicion4u on 2007-07-05
i think i did that a couple times but i'll try it again though. should i do it from the same site?

---

### Post by 11hjpphty76lkjj on 2007-07-05
Run in a terminal shell:

```

wget http://superb-west.dl.sourceforge.net/sourceforge/hplip/hplip-2.7.6.run
```

This worked for me..seems to be good.

A

---

### Post by suspicion4u on 2007-07-05
im kinda scared to delete the ones in the repositories if this doesn't work so should i do that or not cuz i don't wanna not be able to do nothing at all? i will try what you said though from the terminal.

---

### Post by 11hjpphty76lkjj on 2007-07-05
Not sure what you mean?  You should uninstall the pre-installed hplip.

sudo apt-get remove hplip

then download the new hplip and install it per the instructions.

A

---

### Post by suspicion4u on 2007-07-06
ok now the printer works with no problem but the scanner will not scan properly and sometimes wont scan at all.  i tried going the xsane and it will start and access the scanner but its like it'll heat up the lamp but not actually scan the things im trying to scan. any suggestions?

---

