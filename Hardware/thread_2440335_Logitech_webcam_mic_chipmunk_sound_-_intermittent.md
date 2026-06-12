---
title: "Logitech webcam mic chipmunk sound - intermittent"
date: 2020-04-09
forum: Hardware
---

### Post by thatguymark on 2020-04-09
I'm running 18.04 LTS, found this solution about disabling USB autosuspend at Ask Ubuntu but it still does this every so often. I've switched USB ports and was wondering if that might make a difference and mostly want to get some insight about this. Aside from the GRUB kernel parameter could there be any other settings that relates to autosuspend? I was not able to comment at Ask Ubuntu because you need 50 reputation points.

[https://askubuntu.com/questions/1039058/18-04-recording-problems-with-my-usb-microphone/1071436#1071436](https://askubuntu.com/questions/1039058/18-04-recording-problems-with-my-usb-microphone/1071436#1071436)

---

### Post by mastablasta on 2020-04-09
ah it's a bug. have you seen one of the answers below?
> 
[COLOR=#242729][FONT=Arial]Dennis The problem is caused by absence of driver_info for the popular Logitech webcams in latest Ubuntu 18.04 kernel drivers/usb/core/quirks.c, take a look: [https://pastebin.ubuntu.com/p/CQBhn2w97j/](https://pastebin.ubuntu.com/p/CQBhn2w97j/) - the file should be patched like this: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/843431/comments/37](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/843431/comments/37) Regarding MikeRSpencer's replug it's difficult to say something without additional information. The replug doesn't work in my case.[/FONT][/COLOR][COLOR=#242729][FONT=Arial] &#8211; [/FONT][/COLOR][Bob]("https://askubuntu.com/users/847087/bob")[COLOR=#242729][FONT=Arial] [/FONT][/COLOR][COLOR=var(--black-350)][FONT=Arial][[FONT=inherit]Sep 3 '18 at 4:10[/FONT]]("https://askubuntu.com/questions/1039058/18-04-recording-problems-with-my-usb-microphone/1071436#comment1757907_1071436")[/FONT][/COLOR][COLOR=#242729][FONT=Arial] [/FONT][/COLOR]

i didn't know this is caused by suspend. i noticed it in CS:GO and Skype. i "solved it" by using a headset and moving the mic input over to headset.

i though logitech provides the drivers.

btw if you find a bug you can always report it in launchpad. during report similar to bugs will be foudn and oyu can comment on those or sometimes find a patch or solutions in there.

---

### Post by thatguymark on 2020-04-12
Yeah I actually bought an analog headset for that purpose - but of course it turns out I'll need a splitter cable.

A simple thing that seems to work is open Cheese first. I haven't tested this with Zoom which is one of two applications where I have this issue, but this seems to work with Audacity - otherwise it seems like 2/3 of the time it goes to chipmunk mode..

---

