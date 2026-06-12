---
title: "How to get monitor refresh rate past 60Hz"
date: 2005-11-17
forum: Hardware &amp; Laptops
---

### Post by HackSawtooth on 2005-11-17
I think my eyes are really sensitive to refresh rates lower than 70 or 75Hz.  60Hz really seems "flickery" to me.  Anyway I havent figured out how to change the refresh rate from 60Hz to the 75Hz that my monitor supports.  Someone please tell me how.

Thanks

Chris P

---

### Post by audax321 on 2005-11-17
We need the manufacturer and model of your monitor in order to help. :)

---

### Post by HackSawtooth on 2005-11-17
Its an Apple MultipleScan 15AV monitor.  Its max resolution is 1024x768@75Hz.  That is my default resolution under Mac OS X.  I have a 128MB Radeon 9200 driving it.

Thanks

Chris P

---

### Post by audax321 on 2005-11-17
After a Google search these are the values I found for that monitor:
[INDENT]horizontal refresh rate: 30.0-56.5[/INDENT]
[INDENT]vertical refresh rate: 56.0-75.0[/INDENT]

Here are the steps to enter this information in xorg.conf:

In a terminal,

1. sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf_bak

2. sudo gedit /etc/X11/xorg.conf

3. In the gedit window that pops up find the section in the file that looks like this: 

Section "Monitor"
        ... (some monitor stuff) ...
EndSection

4. You need to either enter the following lines in this section or edit the existing ones:
[INDENT]HorizSync	30-56.5[/INDENT]
[INDENT]VertRefresh	56-75[/INDENT]

5. Restart to enable the changes.

----------------------------------------------------------------------
If the X server fails to load or you get a garbled screen, push CNTRL+ALT+F1 to get to a console and to get your old xorg.conf back:

1. sudo mv /etc/X11/xorg.conf_bak /etc/X11/xorg.conf

2. sudo shutdown -r now


Good luck :)

---

### Post by HackSawtooth on 2005-11-17
Thanks a lot.  I did everything you said, and now I have a 70Hz option.  Im not sure if I have to be using MacOS in order for 1024x768@75Hz, or if maybe the settings you gave me were slightly off.  Or if I just need to do some sort of fine tuning.  But youve helped out greatly, and I'll do more research to see why exactly I only have a 70Hz option and not 75Hz.  Ubuntu is MUCH easier for me to use now.

Chris P

---

### Post by audax321 on 2005-11-17
Take a look at this website as well:
[http://www.everymac.com/monitors/apple/multiple_scan/specs/multiple_scan_15av.html](http://www.everymac.com/monitors/apple/multiple_scan/specs/multiple_scan_15av.html)

It lists the following:
640x480 (31.77-35 kHz Hor. Scan, 60-66.7 Hz Ver. Scan, 58 DPI)
800x600 (37.9-48.1 kHz Hor. Scan, 60-72 Hz. Ver. Scan, 73 DPI)
832x624 (49.7 kHz Hor. Scan, 75 Hz. Ver. Scan, 76 DPI)
1024x768 (48.4-60.5 kHz Hor. Scan, 60-75 Hz. Ver. Scan, 93 DPI)

If you are just going to be using 1024x768, you could try using these values:
HorizSync 48.4-60.5
VertRefresh 60-75

The only thing that worries me there is that the high end of the HorizSync is out of the 30-56.5 range. But that might give you 75 Hz.

Also, other websites indicate that the values might be:
HorizSync 31-57
VertRefresh 60-75

---

### Post by SickTwist on 2005-11-17
[QUOTE=HackSawtooth]Thanks a lot.  I did everything you said, and now I have a 70Hz option.  Im not sure if I have to be using MacOS in order for 1024x768@75Hz, or if maybe the settings you gave me were slightly off.  Or if I just need to do some sort of fine tuning.  But youve helped out greatly, and I'll do more research to see why exactly I only have a 70Hz option and not 75Hz.  Ubuntu is MUCH easier for me to use now.

Chris P[/QUOTE]

If you have any documentation that came with your monitor (in print form or perhaps in digital form on a CD) it will usually list your monitor's specifications. Use this to determine the *exact* horizontal sync and vertical refresh rates that your monitor can support. *If you use the incorrect values, you risk damaging your monitor.* If you do not have the documentation on hand,  you may need to go to the website of your monitor's manufacturer to see if it is available for download.

Open xorg.conf (sudo gedit /etc/X11/xorg.conf) and enter these information like was posted above. Scroll down to the part that starts with 'Section "Screen"'. Determine what number follows "DefaultDepth" (probably 24) and look further down to the Depth subsection that matches this number. So if you see "DefaultDepth 24" scroll down to the SubSection that has "Depth 24" contained in it. After the Depth line there is a line that starts with "Modes" which is followed by a list of one or more resolutions. The first one in the list is the default. Change that line to look like this:

Modes     "1024x768"

Save the file and restart X (ALT+CTRL+Backspace). This will make X display in 1024x768 at the greatest refresh rate that your monitor will support (at that resolution). If you want to increase the refresh rate more, you will need to lower the resolution (e.g. "800x600") on the Modes line in xorg.conf (if your monitor can support a lower resolution).

---

### Post by HackSawtooth on 2005-11-17
Alright Ill give that method a try.  Apples specs for the monitor are:

Freq. range  43-63Hz

Mode / res / vert rate / horiz rate
VGA / 640x480 / 60Hz / 31.77kHz
Mac / 640x480 / 66.7Hz / 35kHz
SVGA / 800x600 / 60Hz / 37.8kHz
SVGA / 800x600 / 72Hz / 48.1kHz
Mac / 832x624 / 75Hz / 49.7kHz
VESA / 1024x768 / 60Hz / 48.4kHz
1024x768 / 1024x768 / 70Hz / 56.5kHz
Mac / 1024x768 / 75Hz / 60.5kHz

Im a bit confused why 1024x768 is listed as a mode.  Anyway, that is leading me to believe I can only get 1024x768@75Hz under "Mac" mode whatever that means.  If you can make much sense out of this please let me know.  Other than that I'll try your method for getting max refresh rate at a given resolution and post back the results.

Thanks

Chris P

---

### Post by SickTwist on 2005-11-17
I found [this]("http://www.farrer.net/~rbf/files/docs/Apple/Monitor's%20TV%20Radio%20&%20Video%20%3F/Multiple%20Scan/multiple_scan_15av_display.pdf") PDF document (Google HTML view [here]("http://64.233.161.104/search?q=cache:BnGt9Fu7xEEJ:www.farrer.net/~rbf/files/docs/Apple/Monitor%27s%2520TV%2520Radio%2520%26%2520Video%2520%253F/Multiple%2520Scan/multiple_scan_15av_display.pdf+Apple+Multiple+Scan+15AV+Display+specifications+horizontal&hl=en")) that indicates that these are the valid input frequency ranges for your monitor:

HorizSync        30-60.2
VertRefresh      56-75

Try updating your xorg.conf file with that to see if it helps.

If that does the trick, here is a tip: Tape those numbers to the back/side of your monitor for future reference. :)

---

### Post by HackSawtooth on 2005-11-20
Sorry for the delay.  But I just now tried to get 75Hz working, and I did.  Using the info I posted above from Apples website, I figured the correct HorizSync is actually 31.77-60.5.  I put that in and it works great.  You all helped me a lot though by showing me how to enter that information.

---

