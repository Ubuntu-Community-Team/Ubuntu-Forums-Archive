---
title: "cant achieve 2560 resolution"
date: 2016-03-23
forum: Hardware
---

### Post by cee2 on 2016-03-23
i have a visiontek radeon 6870 with 2 monitors hooked up  dvi vga and hdmi for  my lg 34" acer 23" and panasonic tv 60 " respectively resolutions look proper on acer and panasonic but on the lg 34 it looks stretched at 1920 resolution. the monitor itself recomends 2560 resolution but if i click on that option it goes black.  so is this dependant on the type of hookup or the software ubuntu uses for the card, the card itself,  or what?

---

### Post by cee2 on 2016-03-23
noone has a clue or am i asking the wrong questions?

---

### Post by Drone4four on 2016-03-24
What have you tried so far?  Were there any guides, blog posts or forum posts you found off Google written by users with similar problem with similar hardware with similar drivers? 

Do you know what driver you're running on Ubuntu? AMD's proprietary Catalyst drivers are very problematic for *nix users across the board and have been for years.  You might have better luck with running the open source Gallium drivers.  Although I'm really not the expert when it comes to AMD hardware because I am loyal to nVidia precisely for the driver support.  Sorry.  I wish I could have been more helpful.

You're on the right sub forum for sure tho.  Someone else here more familiar with AMD hardware should be able to better answer your question than I can.

---

### Post by cee2 on 2016-03-25
thanks anyway
Ive always been an underdog supporter in the intel/amd fight as i dont like globalist monopolistic type companies.
So im stuck with amd drivers  and i was only an intermediate software/hardware guy in the windows world.
Now that i use ubuntu almost exclusively im back to being a noob

So ive no idea how to change my drivers on a linux system.

Im not even sure i have any optopns to change connections and still have all monitors running.

I have 2 dvi port, 1 hdmi port and 2 DISPLAY PORTS on my visiontek graphics card
acer 23" only has 1 vga 1 dvi hookup
60'tv only has hdmi
34 lg has dvi and hdmi

the 2 display ports and the 2 dvi all support 2560 max resolution

so tv has to get hdmi port
acer is hooked up to dvi/vga adapter
so lg34 that wont allow 2560 resolution is hooked up via dvi and adapter to those Display ports.

---

### Post by QDR06VV9 on 2016-03-25
Turns out that the AMD drivers only support a pixel clock of up to a certain rate. Monitors that run at this resolution at 60 fps need a higher pixel clock rate.

 But have a look here [https://wiki.ubuntu.com/X/Config/Resolution/#Adding_undetected_resolutions](https://wiki.ubuntu.com/X/Config/Resolution/#Adding_undetected_resolutions)
 Bear in mind I have only an onboard ATI card so your mileage may vary..
 Kind Regards

---

### Post by cee2 on 2016-03-25
i dont know what all that means but i forgot to mention that my monitor appears to offer 2560 resolution as a window pops up saying so at bootup but if you actually click on 2560 it goes black until the timer runs out for you to agree to these new settings or i manually reset it on another screen.

---

### Post by QDR06VV9 on 2016-03-25
Ok just to make things a little easier to understand.
If you already have that option(2560) after you select it and it goes black just hit the Enter Key(Before it times out to the lower resolution), that should just use the accept this configuration.

---

