---
title: "Can't change resolution or refresh rate on my laptop"
date: 2010-01-08
forum: Hardware
---

### Post by Ehknaton on 2010-01-08
The laptop I'm using in a Fujitsu Siemens Amilo L 6825, it's quite old but works fine with ubuntu. 
The problem is that when i go to Display under Preferences I can't change the Display, Refresh rate or Rotation.
I'll attach several screenshots to get a better idea, with a lspci command and the Display window.
Any help will be appreciated.

---

### Post by Ehknaton on 2010-01-09
No one knows how to fix this ? 
No opinions what so ever?

---

### Post by Capitolman on 2010-01-09
Try finding this deb file: xorg-driver-sismedia_0.9-1_i386.deb
i dont know if this will work but it works on my Fujitsu Siemens Esprimo v5535.

you then have the choice of: 1280 x 800, 1024 x 768, 800 x 600, 640 x 480.

Please let me know if it works.

---

### Post by Ehknaton on 2010-01-10
Thanks for the reply,
I tried searching the file but i couldn't find it; nor others like it, only some py xorg_driver files.
Since it's an older laptop i was thinking to switch to Xubuntu, you think that's a good idea?

---

### Post by cova on 2010-01-11
Ok. I had similar problems with my L7320GW but its sorted now. Just created a new xorg.conf. The easist way is to create a new text document with the config on the desktop and rename it xorg.conf, then open a terminal, navigate to the desktop folder and type
> sudo cp xorg.conf /etc/X11/
This will copy the xorg on your desktop to the correct folder. Here is my xorg.conf (had used another but didnt have the highest resolution on it so just used a basic one and worked fine)
> Section "Device"
Identifier "Configured Video Device"
EndSection

Section "Monitor"
Identifier "Configured Monitor"
EndSection

Section "Screen"
Identifier "Default Screen"
Monitor "Configured Monitor"
Device "Configured Video Device"
DefaultDepth 16
Subsection "Display"
Viewport 0 0
Depth 16
Modes "1280x800" "1024x768" "800x600"
EndSubSection
EndSection
PLEASE NOTE:
You may want to back up your original xorg.conf file before trying this just in case.

---

### Post by Ehknaton on 2010-01-12
I tried searching for the file xorg.conf, and the only result was: xorg.conf.5.gz which is in /usr/share/man/man5. So no file to back-up. I created a file as you said and copied it in X11 folder. I don't know if i did it properly, but I'll se if anything changes.

---

### Post by cova on 2010-01-12
Could you load up a terminal and type the following:
> gksudo gedit /etc/X11/xorg.conf
This should load up your text editor (gedit) with your xorg.conf file.
If you did it as I was saying above, you should have exactly what is in the xorg.conf I posted above. If not, then copy the text above and paste it into your version or else just make sure that the bit in bold here is entered before the EndSection part for the Screen section.
> Section "Screen"
Identifier "Default Screen"
Monitor "Configured Monitor"
Device "Configured Video Device"
DefaultDepth 16[B]
Subsection "Display"
Viewport 0 0
Depth 16
Modes "1280x800" "1024x768" "800x600"
EndSubSection[/B]
EndSection 
Then once you've done that, if you restart then you should notice that you see those options available in your display settings.

---

### Post by Capitolman on 2010-01-13
This worked for me and was very easy to do. Go to this site ( SIS ON LINUX) download and save the first file in the list. open your download file and click on the file you have saved and it should self install. If you find this  works please let me know, as i am a complete beginner and would love to know i have been of help.

---

### Post by Ehknaton on 2010-01-14
I just did what you said, copied the exact things in that file, restarted my laptop, but it's still the same.
I'll try capitolman's solution later on when i have time.

---

### Post by simonc50 on 2010-01-17
Hi Guys i have had the problem on a few systems...xorg.conf needed HorizSync settings etc..
you may need too google for your particular settings or check owners manual etc.

this xorg.took me from 600x800 too 1024x768 after a reboot..

Section "Device"
Identifier "Configured Video Device"
EndSection

Section "Monitor"
Identifier "Configured Monitor"
HorizSync   28-51
VertRefresh 43-60
EndSection

Section "Screen"
Identifier "Default Screen"
Monitor "Configured Monitor"
Device "Configured Video Device"
DefaultDepth 16
Subsection "Display"
Viewport 0 0
Depth 16
Modes "1280x800" "1024x768" "800x600"
EndSubSection
EndSection




Hope this helps!
this is 9.10 on an old gateway FlexATX 700c

---

### Post by Ehknaton on 2010-01-18
Hi, I edited my xorg.conf file in my /etc/X11 folder to match what you posted, restarted but the problem is still not solved.
I don't have the owners manual, and I don't know what graphic's card is installed on this computer. I only know the make and the model of the laptop. If anyone could help me I'll greatly appreciate it.

---

