---
title: "Ubuntu 18.04. GPU seems detected, but unable to select driver?"
date: 2022-02-03
forum: Hardware
---

### Post by stilson on 2022-02-03
G'day folks,

Sorry to be the needy guy, but I've got a little issue:

[U][B]Background:
[/B][/U]
My rig died, and I got a hold of a free 'puter: 4th gen intel with a GT610 Nvid GPU. I chucked my SSD into it and she fired up all good running 18.04.

I had a GTX1080ti in my old rig running a 4xx.x version of the propriety driver.

[U][B]Issue:
[/B]
[/U]The system won't boot when mon is plugged into GPU. (via either HDMI or VGA).

With the mon plugged into the mobo, the system is running on the intergrated graphics, not the GPU, as expected. Oddly though, under 'additional drivers' the GPU is listed, but I can't select a driver for it. When I run 'lshw' it shows the intergrated graphics being used.


[IMG]https://ubuntuforums.org/attachment.php?attachmentid=289954&stc=1[/IMG]


The grey options are un-selectable.

[U][B]Observations:
[/B][/U]

[LIST]
[*]Maybe it's possible the card won't run on the new driver, but why are the greyed options an old driver, not the one I have on disc? 
[*]I've never seen the Continue....... option before. 
[/LIST]


Any help appreciated.

---

### Post by Autodave on 2022-02-03
You need the 390 driver....that is the newest one that you can use on that GT610 card.  Remove the current driver, reboot, and then go back to what you have above and select the 390 driver which will be visible then.

---

