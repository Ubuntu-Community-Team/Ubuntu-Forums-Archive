---
title: "Screen Resolution"
date: 2007-12-22
forum: Hardware &amp; Laptops
---

### Post by slice16 on 2007-12-22
Hi All,

I have a strange issue here. When I ran the live CD on my Dell D620, I has a larger selection of resolutions. However, now that I have installed ubuntu, I am only able to select 1024x768. There are no other options in Restricted Drivers. 

Am I missing a setting somewhere?

Thanks in advance

---

### Post by ijason on 2007-12-22
yep. in your xorg.conf, look for where it says :

> Section "Screen"
        Identifier      "Default Screen"
        Device          "ATI Technologies Inc M22 [Mobility Radeon X300]"
        Monitor         "Generic Monitor"
        Defaultdepth    24
        SubSection "Display"
                Modes           "1920x1200" "800x600"
        EndSubSection
EndSection

you will need to add whichever resolutions you want to have as an option. i had to add 1920x1200 to get my laptop to look right. :) restart the windows manager with the cntrl+alt+backspace and you should now have more options for resolutions in your settings.

---

### Post by ijason on 2007-12-22
of course, your "device" will be different than mine. but the section "screen" and "display" are universal.

to edit your xorg.conf do this:
> 
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.backup
sudo pico /etc/X11/xorg.conf

the first part makes a backup, and the second part will open an editor. you'll need to know your sudo password.

---

### Post by slice16 on 2007-12-22
Hi Both, 

Thanks for the prompt reply. I have checked my xorg.conf and the only resolution in the conf  is 1280x800 (The one I want). However, I am only able to see 1024x768.

Thanks

---

### Post by ijason on 2007-12-22
hmm. that is strange :confused:

in your settings, do you have a few options for the refresh rate? maybe it is at some weird refresh rate that is limiting the resolutions. 

try adding the 1440x900 resolution, maybe your computer has the WXGA+ display? i've never heard about the live-cd properly supporting hardware on a machine and then the install not. but i'm still a bit new :)

---

### Post by slice16 on 2007-12-22
I don't have any other options in the refresh rate either. 

I have tried different resolutions in xorg.conf, including 800x600, and for some reason, it appears to be ignoring xorg.conf. 1025x768 is no where to be seen.

---

### Post by ijason on 2007-12-22
dang. other than the xorg.conf option, i'm out of solutions. :confused:

hope you can find someone else whose more helpful!

---

