---
title: "Video Driver Major issue"
date: 2009-01-21
forum: Hardware
---

### Post by makaymurray on 2009-01-21
Hey Guise:

  I have a Toshiba Satellite 1400 (its an old one.) and i recently installed Ubuntu 8.10 and ran into a large problem. the screen resolution maxes out at 800x600 and there is no option bigger than that in the "screen Resolution" settings. I've read around and heard about something called the xorg.conf file. (don't quote me but I think thats it) and for the life of me I cant figure out what I'm to do with the file. (there is no "800x600" item that I can just retype and it just seems to be gobble-de-goop)  

I know that the screen resolution is 1024x768 because when it had windows installed that was the resolution. 

here is all the technical info on the bottom of the machine: 
C133 14X 256M 30 RW/DV M/L
Toshiba Satellite 1400 system unit; model number: PS140C-03D07P

(also external monitors don't even get recognized when plugged into the VGA port)

plz help!

---

### Post by utnubuuser on 2009-01-21
Terminal >>  sudo dpkg --reconfigure xserver-xorg

--This is dependent on your video card.  Nvidea, Radeon etc each have slightly different procedures.

Google: "800x600 resolution ubuntu", and you'll find plenty of forum posts addressing the same issue.

---

### Post by JKyleOKC on 2009-01-21
For weeks I've been trying to get better than 800x600 resolution on one of my systems. It was working just fine with Fiesty, but when I upgraded to Hardy the best I could get was 800x600. Changing drivers from "ati" to "vesa" had no effect, adding modelines didn't do much of anything, and nothing I saw suggested here or in the video section changed things either.

But a few minutes ago I had a brainstorm, and tried typing "startx -- -depth 8" instead of just "startx" to launch my X session. Lo and behold, it came up as 1024x768! With a depth of only 8, it had only 256-color response, so I then tried with a depth of 15 instead of 8, and it still worked. Apparently my video card's 2-MB video RAM simply could not support 24-bit depth at any higher resolution.

My final change was to go into xorg.conf manually, and change the default depth from 24 to 15. This removes the need to add the "depth" argument to the startx command, and lets me enable the gdm graphic login if I desire to have automatic login.

Hopefully this may help others who have been frustrated by the inability to get better than 800x600 resolution...

---

### Post by RJARRRPCGP on 2009-01-21
Looks like your laptop is from 1997 or around there. LOL. 

Thus, that would be typical, you're lucky to have 2 MB of VRAM.

And you would be real lucky to have 1024x768 at all! And NO 3D!

You would be better with DSL or Puppy. No offense.

---

### Post by JKyleOKC on 2009-01-21
Actually it's not a laptop; it's a desktop system but the video card is an ancient ATI Rage 128. It can do 24-bit video at 1024x768 in Win98, but for some reason cannot do so in Hardy even though it did in Fiesty! I suspect the change in xorg between the Xubuntu versions is the reason...

edit: Sorry for posting in the wrong area. I simply searched for the "resolution" tag and this thread seemed like an appropriate place to post my discovery. Never noticed that it was in the Laptops section.

---

### Post by RJARRRPCGP on 2009-01-21
> **JKyleOKC said:**
> Actually it's not a laptop; it's a desktop system but the video card is an ancient ATI Rage 128. It can do 24-bit video at 1024x768 in Win98, but for some reason cannot do so in Hardy even though it did in Fiesty! I suspect the change in xorg between the Xubuntu versions is the reason...

edit: Sorry for posting in the wrong area. I simply searched for the "resolution" tag and this thread seemed like an appropriate place to post my discovery. Never noticed that it was in the Laptops section.

Now, that sounds a lot better. :D 

An ATI Rage 128 can also do 3D acceleration, but likely only in Windows. :( 

I dunno if it even supports OpenGL at all. It does support DirectX 6 and 7.

---

### Post by makaymurray on 2009-01-26
> **JKyleOKC said:**
> \
But a few minutes ago I had a brainstorm, and tried typing "startx -- -depth 8" instead of just "startx" to launch my X session. Lo and behold, it came up as 1024x768! With a depth of only 8, it had only 256-color response, so I then tried with a depth of 15 instead of 8, and it still worked. Apparently my video card's 2-MB video RAM simply could not support 24-bit depth at any higher resolution.


sorry but I'm a little nieve in the world of linux i know a little about the ctrl+alt+funcion keys and how that is differend users in different services enabled modes. but aside from that and some simple unix commands (rm -R, mv, cp, pwd, cd .. etc) im rather a noob. is there any totorial site i could go to, so i can leanr what you did there with the xstart command? or if your so inclined could you do a quick walkthough of exactly what you did?

---

### Post by igknighted on 2009-01-26
> **makaymurray said:**
> sorry but I'm a little nieve in the world of linux i know a little about the ctrl+alt+funcion keys and how that is differend users in different services enabled modes. but aside from that and some simple unix commands (rm -R, mv, cp, pwd, cd .. etc) im rather a noob. is there any totorial site i could go to, so i can leanr what you did there with the xstart command? or if your so inclined could you do a quick walkthough of exactly what you did?

He/She had a completely different issue than you, so ignore that solution.  You probably have a driver issue.  First things first, we won't know where to begin unless we know what type of video card you have.  Open a terminal and try running the command 'lspci | grep VGA' and posting the output.  The command 'lspci' lists (like ls) the devices on the PCI bus (where a video card would be).  The | is a pipe, it redirects the output of that command to another command, in this case grep which is acting as a filter, printing only the lines that contain the text VGA (note: case is important here).

---

### Post by makaymurray on 2009-01-26
> **igknighted said:**
> He/She had a completely different issue than you, so ignore that solution.  You probably have a driver issue.  First things first, we won't know where to begin unless we know what type of video card you have.  Open a terminal and try running the command 'lspci | grep VGA' and posting the output.  The command 'lspci' lists (like ls) the devices on the PCI bus (where a video card would be).  The | is a pipe, it redirects the output of that command to another command, in this case grep which is acting as a filter, printing only the lines that contain the text VGA (note: case is important here).

alright i did as you asked and i was given this:

01:00.0 VGA compatible controller: Trident Microsystems CyberBlade XPAil (rev 82)

where do i get a driver for this?

---

### Post by bigbird on 2009-01-26
I tried Dpkg --reconfigure xserver thing now I have blank white screen

I changed from on-board video to a Sapphire HD3850 card and was stuck with 600x400
No what sorry I'm stupid But try my best.
Thank you in advance Chauvin.

---

### Post by makaymurray on 2009-01-27
i would just like to say that i finaly figured out the xorg.conf file and edited all the fields correctly, however ican only successfully edit the color bit. the resolution change never takes effect..

---

### Post by auriza on 2009-06-14
I also have **Trident Cyberblade XPAi1** on my Toshiba Satellite 1800 laptop.
To fix the video resolution to 1024*768, you have to edit **xorg.conf** file manually.

Open the Terminal (Application --> Accessories --> Terminal), and type:
```
sudo gedit /etc/X11/xorg.conf
```This will open up xorg.conf file in text editor. 

Replace the content of the file with the following text:
I got it from: [http://ubuntuforums.org/showpost.php?p=5039883&postcount=12](http://ubuntuforums.org/showpost.php?p=5039883&postcount=12)
```

Section "Device"
  Identifier "Trident Microsystems CyberBlade XPAi1"
  Driver "trident"
  BusID "PCI:1:0:0"
EndSection

Section "Monitor"
  Identifier "Generic Monitor"
  Option "DPMS"
  HorizSync 28-51
  VertRefresh 43-60
EndSection

Section "Screen"
    Identifier    "Default Screen"
    Monitor        "Generic Monitor"
    Device        "Trident Microsystems CyberBlade XPAi1"
    SubSection "Display"
           Depth 8
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
    SubSection "Display"
           Depth 32
           Modes "1024x768"
    EndSubSection
EndSection
```Don't forget to add newline (press ENTER) at the end of the file before saving.

I have tested it in Ubuntu 9.04 and it works! Hope this will help.

---

### Post by SlidingHorn on 2010-05-03
@auriza

Just wanted to say thank you...I have the same card & your xorg fix worked perfectly!

---

