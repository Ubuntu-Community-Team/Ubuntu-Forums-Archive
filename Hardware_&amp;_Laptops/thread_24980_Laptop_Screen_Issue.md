---
title: "Laptop Screen Issue"
date: 2005-04-08
forum: Hardware &amp; Laptops
---

### Post by marxamuel on 2005-04-08
I have an ancient satellite 4020.  It has a 13.3 screen and a C&T65555 controller chipset.   When I installed Ubuntu on my laptop, I orginally had the 640x480 screen size. Then I followed the 855 instructions and now I improved my screen size to  800x600 screen.  I would like to have all the screen.  How do I get all my realestate ? Please mind that I am a newbie and not very fluent in command line interface.  Thank you for any suggestions that you might have.

---

### Post by nad on 2005-04-09
According to Toshiba, the native resolution of your display is 1024x768 @ 60Hz. Try lowering your refresh rate to 60Hz in Computer -> System Configuration -> Screen Resolution. If you can't improve your resolution, you may be able to increase the area of your display by playing with the video timings through the program xvidtune. To tell you the truth, I have never tried this with an LCD display, and, as the xvidtune program writes directly to your monitor, you can fry it with the wrong settings. It does allow you to increase the timings slowly. Click on Applications -> Run Application and type in xvidtune. Read the warning. Then, maybe do some more research first. The Toshiba site has a fine pdf of your computers' detailed specifications.

Dan M

---

### Post by marxamuel on 2005-04-11
Hello,

Thank you for your response.  I did exactly as you said and opened up xvidtune but it didn't effect the screen at all.  I went to the manual page for xvidtune and read that it was a utility for manipulating X86 and as far as I can tell X86 has been superceded on Hoary.  I have had some success (following the 855 post) by editing xorg.conf, but I havent been able to get all the way there.  Again, any help would be appreciated.

---

### Post by lucus on 2005-05-01
i have a toshiba tecra, and i have the same problem...
i tried a lot of stuff a dude named mendicant helped me a lot, but i could never get it to work... so i've just been using computers at the university

---

### Post by marxamuel on 2005-05-01
re: toshiba 4020cdt resolution issue


Just found a solution for the issue. I am really pleased.  After reading posts I went into a post from a similar post and copied a post and pasted into xorg.conf under the monitor section and modified as 

Section "Monitor"
 Identifier "Generic Monitor"
 ModelName "Dell 1024x768 Laptop Display Panel"
 HorizSync 31.5 - 48.5
 VertRefresh 59.0 - 75.0
 Option "DPMS"
This gave me 800x600 resolution.  
Then I read somewhere in the forum that the older toshibas should be set th default depth at 16 rather than 24 and bingo I got all my real estate.  

Section "Screen"
 Identifier "Default Screen"
 Device  "Chips and Technologies F65555 HiQVPro"
 Monitor  "Generic Monitor"
 DefaultDepth 16
 SubSection "Display"
  Depth  1
  Modes  "1280x1024" "1024x768" "800x600"
 EndSubSection
 SubSection "Display"
  Depth  4
  Modes  "1280x1024" "1024x768" "800x600"
 EndSubSection
 SubSection "Display"
  Depth  8
  Modes  "1280x1024" "1024x768" "800x600"
 EndSubSection
 SubSection "Display"
  Depth  15
  Modes  "1280x1024" "1024x768" "800x600"
 EndSubSection
 SubSection "Display"
  Depth  16
  Modes  "1280x1024" "1024x768" "800x600"
 EndSubSection
 SubSection "Display"
  Depth  24
  Modes  "1280x1024" "1024x768" "800x600"
 EndSubSection
EndSection

I hope that this is helpful to some one. Now on to get my sound working. \\:D/

---

### Post by trash on 2005-09-07
Here's my 4020cdt xorg... gives me very sweet 1024x768 @60

Section "Monitor"
Identifier "Generic Monitor"
HorizSync 28 - 49
VertRefresh 43 - 72
Option "DPMS"

DefaultDepth 16 #24
SubSection "Display"
Depth 1
Modes "1024x768"
EndSubSection
SubSection "Display"
Depth 4
Modes  "1024x768"
EndSubSection
SubSection "Display"
Depth 8
Modes "1024x768"
EndSubSection
SubSection "Display"
Depth 15
Modes "1024x768"
EndSubSection
SubSection "Display"
Depth 16
Modes "1024x768"
EndSubSection
SubSection "Display"
Depth 24
Modes "1024x768"
EndSubSection
EndSection

Ever get the sound working marxamuel?

---

### Post by epedersen on 2006-02-13
Howdy,

After much re-futzing around with a new install on my HP Ominbook XE2, I found this post.

Setting the "DefaultDepth 16" works perfectly.

---

### Post by mi_were on 2007-03-07
> **marxamuel said:**
> re: toshiba 4020cdt resolution issue


Just found a solution for the issue. I am really pleased.  After reading posts I went into a post from a similar post and copied a post and pasted into xorg.conf under the monitor section and modified as 

Section "Monitor"
 Identifier "Generic Monitor"
 ModelName "Dell 1024x768 Laptop Display Panel"
 HorizSync 31.5 - 48.5
 VertRefresh 59.0 - 75.0
 Option "DPMS"
This gave me 800x600 resolution.  
Then I read somewhere in the forum that the older toshibas should be set th default depth at 16 rather than 24 and bingo I got all my real estate.  

Section "Screen"
 Identifier "Default Screen"
 Device  "Chips and Technologies F65555 HiQVPro"
 Monitor  "Generic Monitor"
 DefaultDepth 16
 SubSection "Display"
  Depth  1
  Modes  "1280x1024" "1024x768" "800x600"
 EndSubSection
 SubSection "Display"
  Depth  4
  Modes  "1280x1024" "1024x768" "800x600"
 EndSubSection
 SubSection "Display"
  Depth  8
  Modes  "1280x1024" "1024x768" "800x600"
 EndSubSection
 SubSection "Display"
  Depth  15
  Modes  "1280x1024" "1024x768" "800x600"
 EndSubSection
 SubSection "Display"
  Depth  16
  Modes  "1280x1024" "1024x768" "800x600"
 EndSubSection
 SubSection "Display"
  Depth  24
  Modes  "1280x1024" "1024x768" "800x600"
 EndSubSection
EndSection

I hope that this is helpful to some one. Now on to get my sound working. \\:D/

I have been looking for this for a while so as to sort out the display on my little Toshiba Satellite 335CDT xubuntu project. Hope it goes well.

Cheers

---

### Post by mi_were on 2007-03-07
> **mi_were said:**
> I have been looking for this for a while so as to sort out the display on my little Toshiba Satellite 335CDT xubuntu project. Hope it goes well.

Cheers

I have 800x600 right now. works like a charm.

---

### Post by superatrain on 2007-03-25
The key to getting these screens to work is just make sure the default-depth is 16, and the 16 mode has 1024x768. You dont need to post the entire section.

Too bad ubuntu cant control the depth directly. And with xubuntu, I dont see 1024x768 in the CP, even though its running it.  Not much demand for these old machines I guess...

---

