---
title: "touchpad erratic hp pavilion dm4"
date: 2010-10-10
forum: Hardware
---

### Post by agvs on 2010-10-10
Hello,

I'm brand new to linux, a long-time mac user and hoping to get away from Apple. I have an HP pavilion dm4 and have installed 64-bit ubuntu 10.10.

The touchpad works fine in Win7 but is totally erratic in Ubuntu. If I put more than one finger on the touchpad, the cursor jumps all over the place erratically and randomly submits clicks. The right-click function of the touchpad also doesn't work.

In the mouse settings, the option for multi-touch is greyed out, but the touchpad is obviously still registering multi-touch info.

I've tried installing gsynaptics, but that doesn't help. I've also tried a few scripts provided by other people for enabling multi-touch when the option is greyed out, but that doesn't help. I've also tried uninstalling and reinstalling the synaptics xorg touchpad driver with no luck.

Any suggestions? Thanks.

---

### Post by cjav on 2010-10-10
Well I found your post looking for a solution to my own problems with Ubuntu 10.10(Maverick).

In my case right-double click was my main problem, and also some randoms left click by just putting my fingers in the touchpad, and I was able to fixed by going to System/Preferences/Mouse/Touchpad and de-selecting "Enable mouse clicks with the touchpad". I think the problem is that for some reason after a clean install, the touchpad got way more sensitive, I'm using third party drivers for my GMA500(Poulsbo) chipset, so I don't know is I should report this as a bug.

My laptop is a Dell Mini 10, with left and right clicks that you need to push down in the touchpad. It gonna take me some time to adapt to do the push down, but in the end will be better as this method is way less error prone.

Hope it helps.
Carlos

---

### Post by agvs on 2010-10-11
Thanks for the reply. I did try disabling mouse clicks to no avail; the cursor would still jump around erratically. It must have something to do with the multitouch control information being sent by the touchpad.

---

### Post by rayman7718 on 2010-10-12
I upgraded to ubuntu 10.10, with the distribution upgrade and it was fine yesterday, but i did the kernel updates today, as scheduled by the update manager, and i'm back to square one :|

---

### Post by zappadragon on 2010-10-13
I am having the same kind of problems. My HP DV7 the touchpad is all one section that inlucdes the buttons. If I try to click right or left the mouse will jump to that section. I am not able to drag and drop either. This bug is really driving me nuts.

---

### Post by TheSe7enthSin on 2010-10-13
So I've had this issue since 10.04. Last night I ran 10.10 via the LiveCD and the touchpad worked perfectly. I was so happy to see it working, so i erased my windows OS & installed 10.10. Now this issue is back. I hope someone can point us to a solution.

I am not running the same laptop though. I have a Lenovo Y550.

I just want to disable multitouch. This erratic behavior is ridiculous.

---

### Post by inphilly on 2010-10-18
I solved (not completely) the erratic pointer of the hp pavilion dm4-1160us. I work a simple script to reconfigure the synaptics driver. You can find the code (post in English) [here]("http://sansmicrosoft.blogspot.com/2010/10/pavilion-dm4-1160-erratic-touchpad.html") and (post in French, with code in zip file) [there]("http://sansmicrosoft.canalblog.com/archives/2010/10/18/index.html") .

It's not perfect, the right click is missing but the left click is emulated with a short tap, the vertical scroll is on the right edge of the pad, and the pointer doesn't jump erratically.

---

### Post by austinjh on 2010-10-22
I have a Pavillion dm4-1060 ea running 10.10 with the same issues. Thanks to inphilly's script, the touchpad is much more useable.

---

### Post by CPMariner on 2010-12-11
This may not address the more complicated problems reported here, but the "case of the wild cursor" is easily solved in Windows 7. On my new HP Pavillion (DV7), it's just a case of touchpad sensitivity. If the sensitivity is set too low, all you have to is *breathe* on the pad for the cursor to go off into the wild blue yonder, all over the page. Here's the fix:
 
Start
Control Panel
Hardware and Sound
Mouse
Device Settings
Settings
Pointing (double-click)
Sensitivity (double-click)
Touch Sensitivity
Move slider more to the right toward "Heavy"
Apply
OK
 
You probably knew this... just covering all the bases :-)

---

### Post by alonamaloh on 2011-01-08
I just bought a dm4t-1100, I installed ubuntu 10.10 64 bits on it and got the same crappy trackpad experience that others have described. inphilly's script helped somewhat, but it's still not very usable. I am using a separate mouse for now, but I guess I'll reinstall Windows (horror!) on it if I can't get this fixed, and then install ubuntu inside VirtualBox.

---

### Post by magtrask on 2011-02-08
Hi, I'm having the same problems with an HP Pavillion  dv3.  I would love to be able to use my the multi-touch capabilities (zoom, scroll, even select).  Anyone found any solutions? I'm on 10.10. Thanks.

---

### Post by mhutton on 2011-02-12
I am also having the same problems described on a HP Pavilion DV7. I have tried every setting I can find under mouse and with no success. Annoying for sure.

---

### Post by chasem1991 on 2011-02-12
For all of those who have Synaptics touch pads, you can try this. [Tutorial I made in another thread.]("http://ubuntuforums.org/showpost.php?p=10403066&postcount=8")

---

### Post by magtrask on 2011-05-12
Hi again, I have the Pavilion dm3. 
I tried your suggestion, but the second command to 
[PHP]sudo apt-get update && sudo apt-get install synaptics-dkms [/PHP]returns:  Unable to locate package synaptics-dkms

I really love Linux and want to stay with Ubuntu. I have been trying to solve this touchpad problem for months by following all community suggestions. Please, I just want to be able to select, drag and drop with a left-click function like I can on this laptop in Win7 with its touchpad, or on this laptop in linux with a USB mouse.

If I can't solve this asap I need to leave Ubuntu. Please help.

---

### Post by CronoDekar on 2011-05-12
I suspect I might be having these problems -- I have a Pavilion g6 myself, and cannot change the touchpad settings.  

chasem1991: When doing the update, I get:

```
W: Failed to fetch http://ppa.launchpad.net/utouch-team/utouch/ubuntu/dists/lucid/main/binary-i386/Packages.gz  404  Not Found

```

---

### Post by savage25rcracer on 2011-06-17
i enabled 2 finger scroling and is works great.

---

### Post by amorriso on 2011-07-02
Hey all 

Successful two finger mouse functionality on a HP Pavilion dv6 using lucid ubuntu 10.04

I tried for weeks messing around with different settings in xinput. This is very time consuming due to a lack of good documentation. 

Finally got something acceptable working using the instructions here:

[https://help.ubuntu.com/community/T101MT](https://help.ubuntu.com/community/T101MT)

Note: for full functionality/control you also need to do some final (easy) settings manipulation using gpointing. 

Good luck!

---

### Post by coachsd on 2012-01-09
I just installed Ubuntu 11.10 on my HP Pavilion dm4 and had the same eratic track pad behavoir and I had to use a USB mouse to control the curser. I was able to solve the problem easily. I clicked on System Settings/Mouse and Touchpad/Touchpad (tab) and changed the pointer speed. Both acceleration and sensitivity were set all the way to the left (zero). I just changed them to about 10% and presto-magico touchpad worked.

---

