---
title: "Enabling onboard graphics in dual monitor scenario"
date: 2013-09-09
forum: Hardware
---

### Post by ktz84 on 2013-09-09
I currently have an MSI Radeon 6850 OC graphics card which I'm using with my main monitor. I also have onboard graphics on my Gigabyte 880GA-UD3H mobo which uses ATI Rdeon HD 4250 graphics. I had this disabled in the bios however I've renabled it however when I boot in the newly connected monitor doesn't do anything - just gives a message to check cable. I've gone into displays however I see no way to enable the extended monitors or even mirror for that matter as the mirror displays option is greyed out.

I'm not even sure if my onboard graphics are even recognised so how do I go about enabling it in Ubuntu 13.04 x64?

---

### Post by ktz84 on 2013-09-09
If I choose OnChip option as the priority graphics it will boot with other monitor however it goes into low resolution mode and the mouse and keyboard can't control the options so I couldn't get any further with that. All other options for priority boot to the main monitor and the secondary one never comes on. So at least I know the vga port on the mobo works.

---

### Post by Mark Phelps on 2013-09-10
Unfortunately, the AMD HD4250 does not have any working restricted drivers that will operate in any Ubuntu version newer than 12.04.1.

IF you have restricted drivers installed for the 6850, those will not work when you enable the 4250.

---

### Post by ktz84 on 2013-09-10
Thanks Mark. I've had a bit of luck. Whilst looking through my box of parts that I've accumulated I found a VGA to DVI converter which is a bit of luck as my graphics card has 4 connectors 2 of which are DVI though there is a difference in the two DVI ports. If I plug the vga monitor into the lower DVI it will show no signal however if I move into the top it will show the signal so long as I don't plug the main TV (HDMI to DVI cable) in. If I plug both in then I do get both appearing (one correctly identified as my Samsung TV and the other showing as unknown). It's resolution is supposed to 1400x900 however no matter what resolution I chose for that screen it errors out saying:

> The selected configuration for displays could not be applied

required virtual size does not fit available size: requested=(2720, 1080), minimum=(320, 200), maximum=(1920, 1920)

So a bit of success. Where do I go from here to get both working together.

I've enabled the proprietary drivers-updated as not using the updated one gives me a message with an ATI logo on the lower right of the screen saying unsupported hardware which disappears when I enable the updated version.

---

### Post by ktz84 on 2013-09-10
Ok I've now managed to configure both displays using the AMD Catalyst Manager to run side by side however the VGA display is set as the default display I can't figure out how to get my Main Monitor set as my default. It's a bit of annoyance as my desktop icons are not appearing on the screen I'd chose to put them on and that's the same for my conky theme but at least I can now use both displays.

---

