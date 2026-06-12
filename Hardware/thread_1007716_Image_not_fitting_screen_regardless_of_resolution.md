---
title: "Image not fitting screen regardless of resolution"
date: 2008-12-10
forum: Hardware
---

### Post by thor-on-kveven on 2008-12-10
Ubuntu 8.10
Geeforce 8400 GS 256MB with proprietary drivers NVIDIA 177 enabled
_DVI to HDMI cable _
Hitachi 32"LCD TV 32LD8800TA

Hi!
Thanks for looking at my post. Relatively new to Linux, and would be back to windows a long time ago if it was not for the incredibly comprehensive forum help!

I have a new box with the set-up above that I am intending to run as a media centre in the living room. Initially I used a VGA cable to connect box to TV at 1024x768, which worked OK but not quite up to what the card and TV is sipposed to do. I've been told DVI or HDMI input would improve resolution and picture quality, so I bought a DVI-HDMI (GE 8400 does not have HDMI-out)cable and plugged into the HDMI port on my LCD TV. With this set-up the image is slightly too big for the screen _regardless of resolution_: I can see just the top/bottom of the lower/upper menu bars.

I have searched the forum and found related image vs screen problems, but they mostly concern resolution problems. I can go all the way up to 1920x1080 with about the same amount of screen missing as on 800x600. (The only way I can see the whole screen is by choosing "centered" in the NVIDIA x server settings "GPU scaling method". The other two scaling methods look similar, with screen missing on all four sides). Also, the Hitachi TV has zoom and format settings built in, but with HDMI input these functions are not supported, so I can't "zoom" in and out to fit the picture. 

Can someone give me a pointer in therms of what to try?? At this stage I don't really know whether the issue is the 
- graphics card and drivers, 
- the cable or the 
- TV???
- or does it have something to do with advanced set-up such as x/ y axis etc??  


It is not a complete crisis in that I can always swap back to my VGA cable, but the picture looks better in qualitative terms with HDMI, just shame about the quantity :-)

Cheers

---

### Post by thor-on-kveven on 2008-12-10
Sorry, I should of course specify that when I choose the "centred" option as described above I can see the whole image but as a tiny image in the middle of the screen with 40% black frame around it.

---

### Post by lamboram on 2008-12-10
> **thor-on-kveven said:**
> Ubuntu 8.10
Geeforce 8400 GS 256MB with proprietary drivers NVIDIA 177 enabled
_DVI to HDMI cable _
Hitachi 32"LCD TV 32LD8800TA

Hi!
Thanks for looking at my post. Relatively new to Linux, and would be back to windows a long time ago if it was not for the incredibly comprehensive forum help!

I have a new box with the set-up above that I am intending to run as a media centre in the living room. Initially I used a VGA cable to connect box to TV at 1024x768, which worked OK but not quite up to what the card and TV is sipposed to do. I've been told DVI or HDMI input would improve resolution and picture quality, so I bought a DVI-HDMI (GE 8400 does not have HDMI-out)cable and plugged into the HDMI port on my LCD TV. With this set-up the image is slightly too big for the screen _regardless of resolution_: I can see just the top/bottom of the lower/upper menu bars.

I have searched the forum and found related image vs screen problems, but they mostly concern resolution problems. I can go all the way up to 1920x1080 with about the same amount of screen missing as on 800x600. (The only way I can see the whole screen is by choosing "centered" in the NVIDIA x server settings "GPU scaling method". The other two scaling methods look similar, with screen missing on all four sides). Also, the Hitachi TV has zoom and format settings built in, but with HDMI input these functions are not supported, so I can't "zoom" in and out to fit the picture. 

Can someone give me a pointer in therms of what to try?? At this stage I don't really know whether the issue is the 
- graphics card and drivers, 
- the cable or the 
- TV???
- or does it have something to do with advanced set-up such as x/ y axis etc??  


It is not a complete crisis in that I can always swap back to my VGA cable, but the picture looks better in qualitative terms with HDMI, just shame about the quantity :-)

Cheers
hi mate..i had the same prob ..the prob is mostly with ur tv output.if u r using dish u ll get high resolution output..but if u r using std coaxial cable u  would face such problem..theres no solution for this i guess...try some other tv tuner card..but not sure..

---

### Post by thor-on-kveven on 2008-12-12
I've found through searching the nvidia forums that my trouble may have something to do with "overscanning", and that some ?graphics cards? from nvidia have a way of adjusting this. Anyone know about "overscanning"?

Cheers

---

