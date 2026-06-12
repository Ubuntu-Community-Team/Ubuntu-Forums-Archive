---
title: "Ati drivers weird Big Desktop issues"
date: 2008-04-27
forum: Hardware
---

### Post by mxc on 2008-04-27
Hi all,

I am using the restricted ati drivers and just install the 8.3 version using envyNG on Hardy Heron. In Gutsy I had the big desktop feature working ok but I am battling like crazy in Hardy Heron. I have a Asus F3J series notebook. 

lspci reports my card as 


01:00.0 VGA compatible controller: ATI Technologies Inc Mobility Radeon X2300

Apparently this is really a X1300 chip that was just rebranded by the marketing department. It is almost impossible to find a reference to this model (2300) in any ati documentation and I think this explains it.

Anyway I did the "aticonfig --initial --dtop=horizontal" --overlay-on=1 --overlay-type=Xv"

Doing this resulted in the crt remaining dark on boot up. For some reason the driver now takes the external monitor as the primary instead of the latop screen. I don't mind but the last driver took the laptop as primary. I battled for a while with the blank crt as I couldnt see the login prompt. On a whim I just typed in my username and password and voila the desktop cam up with both screen on. But they were in clomed mode!

I managed to sort out the crt being dark on boot up by adding the line "Option "Mode2" "1024x768" to the devices section of xorg.conf.

I still had the clone instead of big desktop problem. Using the amdccccle didn't seem to do the trick either with changes being ignored. I then tried running it manually as root. This seemed to work in that I can now get the desired big desktop. The only problem is that on reboot it looses the changes!  Anyone know how to persits these changes. I did try using amdcccle but it seems not to work :(

---

### Post by jjacobs2 on 2008-05-13
I'm having the same types of issues with an ATI card and two monitors on a desktop.  I can get big desktop to work with the amdccc program but when rebooted it reverts to clone mode.

---

### Post by Tleilax on 2008-06-07
I'm having this problem too,

Tried following Ziox's guide to enable big desktop but ran into problems. 
The CCC allows me to get the desired result but upon reboot I have a cloned desktop.

I'm really new to Ubuntu (and Linux in general) so any help would be appreciated, let me know if I need to post additional information.

Thanks

---

### Post by Tleilax on 2008-06-09
Well after a good afternoon going through the Dual Monitors thread I finally found the issue:

Once you've got Big Desktop going you have to go to
System > Preferences > Screen Resolution

And then adjust it accordingly, the resolution you want will be the combined width of both your monitors plus the height of your first monitor.

I haven't tested this with the control center, I went back and edited xorg.conf directly but I think as long as you alter your resolution it should work fine.

---

