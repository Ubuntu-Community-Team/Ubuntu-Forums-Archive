---
title: "trying to use plasma tv as monitor"
date: 2008-09-25
forum: Hardware
---

### Post by ubunt2guy on 2008-09-25
Laptop has:
3 usb 
1 vga

Philips 50" plasma has:
2 HDMI ports
1 s-video
1 component (red,yellow,white)

Anyone think, with these combinations, that it is possible to connect my ubuntu box up to my TV and use it as a monitor. I'm thinking I may need a converter somewhere down the road.

thanks

cheers

---

### Post by at0mic on 2008-09-25
> **ubunt2guy said:**
> Laptop has:
3 usb 
1 vga

Philips 50" plasma has:
2 HDMI ports
1 s-video
1 component (red,yellow,white)

Anyone think, with these combinations, that it is possible to connect my ubuntu box up to my TV and use it as a monitor. I'm thinking I may need a converter somewhere down the road.

thanks

cheers



Hi,

I have a ton of experience in this department and yes its doable. Your basic cheap solution is to buy a really really good vga to HDMI cable. do not skimp on the price or the quality will suffer. In my experience with a medium grade cable, it was too grainy. straight VGA to VGA on my tv was much clearer. You may not have a vga. FOr your sound, you may have to just use speakers on your laptop or external speakers connected to your laptop. Your tv/laptop may also have SPDIF/digital audio out/ins to use [check closely + read manual].  My plasma had VGA and therefore thought about a PC audio input as well.

My setup now is way beyond the above. [damn humans and their one step futher drive] I have a 42'' plasma, a sub $500 denon audio/video reciever, a windows box connected to the reciever via spdif optical audio and vga direct to the tv, a ubuntu box connected to the reciever via HDMI [had HDMI out on the motherboard] and optical audio, a PS3 connected to the reciever via HDMI and optical out and my cable tv connected to the reciever via HDMI and optical out. I also have a logitec harmony one remote so i can press one button that sends any number of commands to any number of devices. [eg = switch tv to hdmi, switch reciever to hdmi1 and optical to opt1]
With a reciever you  can also get into high end audio and home built setups. I have some Energy floor speakers for surround sound. I also have a logitec mx32000 wireless mouse / keyboard solution that works with ubuntu.Trickiest thing about setting up the big plasma on ubuntu is if your resolution isnt detected correctly and you have to adjust it in administration options, you may have to use the tab and arrow keys as the screen jumped around on me when using mouse.

---

### Post by CranKey on 2008-09-30
I presently am using an AMD box that is connected to a 42" Toshiba plasma screen for general PC use as well as a HTPC.  The HDMI output on the motherboard runs to one of the HDMI inputs on the plasma screen but it carries video only.

One of the more difficult issues that I faced was getting things to display at a reasonable size so that I could read text while sitting back on the sofa with the wireless keyboard.  Eventually I came up with the solution in my xorg.conf file (I've pasted the relevant bits below).  Note that this is an Nvidia specific solution (I'm using the on-board graphics), though I'm not sure if other graphics vendors have something similar.  Essentially what I'm now doing is generating a 720 image and then telling the graphics chipset to upscale it to 1080.  I tried to use a 720 image without the upscaling (I'd prefer that), but that left me with overscan that I couldn't seem to get rid of.  This solution seems to give me a nice size for my icons and text and whatnot, but the drawback is that images can be blocky from the upscaling.

On the audio side of things, I have the optical out on the motherboard running to a lower-end Sony amp.

The motherboard is a abit AN-M2HD.

xorg.conf excerpt:
====
Section "Monitor"
    Identifier     "Panasonic-HDTV"
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "nVidia Corporation NVIDIA Default Card"
    Driver         "nvidia"
    Option "FlatPanelProperties" "Scaling = aspect-scaled"
EndSection

Section "Screen"
    Identifier     "Default Screen"
    Device         "nVidia Corporation NVIDIA Default Card"
    Monitor        "Panasonic-HDTV"
    DefaultDepth    24
    SubSection     "Display"
        Depth       24
        Modes      "1280x720"
    EndSubSection
====

I hope this helps.

---

### Post by ubunt2guy on 2008-10-20
> **at0mic said:**
> Hi,

I have a ton of experience in this department and yes its doable. Your basic cheap solution is to buy a really really good vga to HDMI cable. do not skimp on the price or the quality will suffer. In my experience with a medium grade cable, it was too grainy. straight VGA to VGA on my tv was much clearer. You may not have a vga. FOr your sound, you may have to just use speakers on your laptop or external speakers connected to your laptop. Your tv/laptop may also have SPDIF/digital audio out/ins to use [check closely + read manual].  My plasma had VGA and therefore thought about a PC audio input as well.

My setup now is way beyond the above. [damn humans and their one step futher drive] I have a 42'' plasma, a sub $500 denon audio/video reciever, a windows box connected to the reciever via spdif optical audio and vga direct to the tv, a ubuntu box connected to the reciever via HDMI [had HDMI out on the motherboard] and optical audio, a PS3 connected to the reciever via HDMI and optical out and my cable tv connected to the reciever via HDMI and optical out. I also have a[COLOR="Yellow"] logitec harmony [/COLOR]one remote so i can press one button that sends any number of commands to any number of devices. [eg = switch tv to hdmi, switch reciever to hdmi1 and optical to opt1]
With a reciever you  can also get into high end audio and home built setups. I have some Energy floor speakers for surround sound. I also have a logitec mx32000 wireless mouse / keyboard solution that works with ubuntu.Trickiest thing about setting up the big plasma on ubuntu is if your resolution isnt detected correctly and you have to adjust it in administration options, you may have to use the tab and arrow keys as the screen jumped around on me when using mouse.

that is a pretty sick setup.  Hopefully on day I'll catch up to you.  

do you like that logitech remote? i'm thinking of getting one myself.  

cheers

---

