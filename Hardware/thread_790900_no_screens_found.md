---
title: "no screens found?"
date: 2008-05-11
forum: Hardware
---

### Post by stolle on 2008-05-11
i am attempting to install ubuntu dapper drake on a dell smartstep100n, im getting a video error "no screens found" i have tryed various things none of which has made any progress. any suggestions i really dont even know where to start...i have searched nothing i have found has helped though...

following errors are displayed:
(EE) I810(0): No Video BIOS modes for chosen depth.
(EE) Screen(s) found, but none have a usable configuration.

  Fatal server error:
no screens found

---

### Post by stolle on 2008-05-11
a couple more hours searching and i have found this:
[http://roland-lopez.blogspot.com/2007/03/auto915resolution-ubuntu-resolution-fix.html]("http://roland-lopez.blogspot.com/2007/03/auto915resolution-ubuntu-resolution-fix.html")

and this:
[https://help.ubuntu.com/community/i915Driver]("https://help.ubuntu.com/community/i915Driver")

my question would be, how do i implement this on a system during a fresh install?

---

### Post by Yellow Pasque on 2008-05-12
If you can download/burn the "alternate install" CD, that will do the trick for you.
Or you could press Ctrl+Alt+F1 and install the 915resolution package through the terminal assuming your internet connection works.

---

### Post by stolle on 2008-05-12
> **Temüjin said:**
> If you can download/burn the "alternate install" CD, that will do the trick for you.
Or you could press Ctrl+Alt+F1 and install the 915resolution package through the terminal assuming your internet connection works.


thanks ill try that... :)

---

### Post by stolle on 2008-05-12
no internet connection, im trying to do it from a cd, i dont know what to do really should be fun...starting to get a little aggravated though...

---

### Post by stolle on 2008-05-13
alright i have installed hardy using the alternate cd, all i get is a blank screen, sound can be heard, i can actually type in username and password and hear the ubuntu theme music or whatever, but again the screen is blank.

similar to this thread:
[http://ubuntuforums.org/showthread.php?t=749256](http://ubuntuforums.org/showthread.php?t=749256)

i have tryed to reconfigure x by running 
> sudo dpkg-reconfigure xserver-xorg
it doesnt let me configure video, it starts off in a window about a frame buffer...please help i dont want to go back to windows my laptop is the only pc i have left thats not running ubuntu...

edit: how would i go about installing 915resolution from the command line with no internet connection?

---

### Post by stolle on 2008-05-13
no one has any ideas?

---

### Post by stolle on 2008-05-17
ok, i installed 7.10 now i dont have anymore errors, but i still have a blank screen. i can plug in an external monitor and see it fine, but not on the laptops lcd screen i have tryed changing the video driver to vesa, vga, i810 and edited the xorg.conf numerous times, tried different resolutions, different color depths. i am now in the process of upgrading the laptop to 8.04 to see if that will help my situation, sadly i dont believe it will; have i left anything out? oh yeah, i updated the bios also, im at a loss i have no idea what i should try next can someone please give me some guidance...or tell me to stop trying, cause its not possible...

thanks

---

### Post by Yellow Pasque on 2008-05-17
Hey stolle, sorry to hear of your install troubles. Hopefully, hardy will sort everything out. If not, build from source: [http://intellinuxgraphics.org/download.html](http://intellinuxgraphics.org/download.html)

---

### Post by stolle on 2008-05-17
> **Temüjin said:**
> Hey stolle, sorry to hear of your install troubles. Hopefully, hardy will sort everything out. If not, build from source: [http://intellinuxgraphics.org/download.html](http://intellinuxgraphics.org/download.html)


thanks for your reply, to my understanding the "correct" drivers are already included. which it makes this even more frustrating i can pick the correct driver from a list set the resolution for my screen restart and nothing. i have come to the realization that i am unable to get this working, maybe it will be fixed in a future update maybe, i will learn enough to correct the problem myself, as of right now, i guess i have to go searching for my windows cd's :(

---

### Post by stolle on 2009-06-15
im happy to say i finally have linux installed on my dell smartstep 100n. i got debian lenny installed with xfce it still has a few quirks, the sound isnt right and the screen looks corrupted at times, but its usable. now i have all my pc's either running ubuntu or debian...

here a link to the information i used to get x working:
[http://www.geocities.com/kymacpherson/linux/debian_i2600.html]("http://www.geocities.com/kymacpherson/linux/debian_i2600.html") 

its for an inspiron 2600, it works, as both the smartstep 100n and 2600 shared the same chipset. all i did was edit xorg.conf with the video settings in the link above, i set my videoram to 8000...

as i understand it ubuntu and debian are very similar. if i install ubuntu and edit xorg.conf with the same settings that work for debian i get nothing but errors?

below is my xorg.conf file, im wondering if i would have to install anything extra to get this to work with ubuntu...


> Section "InputDevice"
        Identifier      "Generic Keyboard"
        Driver          "kbd"
        Option          "XkbRules"      "xorg"
        Option          "XkbModel"      "pc104"
        Option          "XkbLayout"     "us"
EndSection

Section "InputDevice"
        Identifier      "Configured Mouse"
        Driver          "mouse"
EndSection

Section "Device"
 Identifier      "Intel i830"
        Driver          "i810"
        VideoRam        8000
#       Option          "UseFBDev"              "true"
EndSection

Section "Device"
        Identifier      "Linux Frame Buffer"
        Driver          "fbdev"
EndSection

Section "Monitor"
        Identifier      "Configured Monitor"
        HorizSync       28-49
        VertRefresh     43-72
        Option          "DPMS"
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Device          "Intel i830"
        Monitor         "Configured Monitor"
        DefaultDepth    16
        SubSection "Display"
                Depth           16
                Modes           "1024x768"
        EndSubSection
EndSection

Section "DRI"
     Mode    0666
EndSection


thanks...

---

### Post by stolle on 2009-06-15
der, should have searched before i posted that, i found more info on the forums. we will see how it goes...

---

### Post by stolle on 2009-06-15
just reinstalled xubuntu 8.04, edited xorg.conf per this [thread]("http://ubuntuforums.org/showthread.php?t=1011213") post #5. it works!!! im posting from my laptop right now :)

---

