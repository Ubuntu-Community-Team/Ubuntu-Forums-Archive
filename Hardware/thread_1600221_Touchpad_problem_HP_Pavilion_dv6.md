---
title: "Touchpad problem HP Pavilion dv6"
date: 2010-10-18
forum: Hardware
---

### Post by linuxrockz on 2010-10-18
Hi everyone :)
I am using ubuntu 10.04 on a HP Pavilion dv6 laptop.
I am facing an issue with my touchpad.
It is a synaptics touchpad with multitouch support. 

The touchpad buttons are integrated into the touchpad (i.e the buttons are themselves touchsensitive)
When I use two fingers the mouse pointer jumps on the screen erratically. 
This prevents me from using drag and drop, selecting and copying etc.

Please help me either to enable multitouch support or atleast disable the bottom 1/4 th of the touch pad.

Thanks :)

---

### Post by linuxrockz on 2010-10-19
Anyone please :(

---

### Post by linuxrockz on 2010-10-20
bump

---

### Post by linuxrockz on 2010-10-21
So i have resigned myself to lug a mouse with me all along.

any way gud day :(

---

### Post by cecilx22 on 2010-10-23
HPs are kind of notorious for having hardware that only fully works in Windows, so I've heard.  Let us know if you figure it out!

---

### Post by mario_k8 on 2010-11-05
Hi!

I had the same problem on a new HP dv6-3120 laptop and Ubuntu 10.10.

I followed these very simple instructions I found on this thread :

[http://ubuntuforums.org/showpost.php?p=8816327&postcount=6](http://ubuntuforums.org/showpost.php?p=8816327&postcount=6)

They refer to a different HP model (a netbook actually) but they worked in my case as well. :)

The pointer no longer jumps around when i put two fingers on the touchpad, and left and right button clicks work just fine (including dragging etc). 

Scrolling does not work yet, but I'm looking into it. I'll let you know if I find out something...

---

### Post by estima on 2010-11-29
Same problem with my DV6 3030.

So, two options for now:

Out-of-the-box:
- Only LEFT clicks (by tapping), 
- Scroll working
- Disbale of the mouse pad working 

With the solution above:
- Both clicks (left and right)
- Drags, etc 

BUT:
- no scroll 
- no way to disable the mouse pad in the preferences

Anyone luck with this issue?

---

### Post by linuxrockz on 2010-12-15
Thanks for the solution mario_k8 :-), i will try it. And i do hope that HP stops making such pathetic touchpads, i really hate mine :-(

@ estima it seems thats the way it has to be at present :-(

---

### Post by gregalynch on 2010-12-26
for the touchpad issue - this fixed mine:

[http://ubuntuforums.org/showpost.php?p=8816327&postcount=6](http://ubuntuforums.org/showpost.php?p=8816327&postcount=6)

---

### Post by ElSlunko on 2010-12-26
This worked for me:

> **uppertoe said:**
> Not sure it's been mentioned in this thread, but [https://help.ubuntu.com/community/SynapticsTouchpad](https://help.ubuntu.com/community/SynapticsTouchpad) has a nice bit of advice that worked for my hp 210.

Installing the package at 

[https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-input-synaptics/+bug/308191/comments/167](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-input-synaptics/+bug/308191/comments/167)

worked like a dream - no two finger scroll, but click and drag is working nicely; something I think is a little more important.

---

### Post by revmarkp on 2010-12-27
> **gregalynch said:**
> for the touchpad issue - this fixed mine:

[http://ubuntuforums.org/showpost.php?p=8816327&postcount=6](http://ubuntuforums.org/showpost.php?p=8816327&postcount=6)

THANKS

Worked for my dv6, although I've no touch scrolling now, but can live with that...

---

### Post by gregalynch on 2010-12-30
> **gregalynch said:**
> for the touchpad issue - this fixed mine:

[http://ubuntuforums.org/showpost.php?p=8816327&postcount=6](http://ubuntuforums.org/showpost.php?p=8816327&postcount=6)

Actually, I changed my mind.  the only problem here is that now you can't turn the trackpad off, which, given the awkward placement of the track pad on this model, means you basically can't type, because your palm always hit the track pad.  This is a real bummer

---

### Post by Stratosmacker on 2010-12-30
Actually if you mess with the synclient options you can make this trackpad work alright. I have a pavillion dv6 and It has a similar trackpad. by passing these commands to the terminal

synclient AreaBottomEdge=3950
synclient JumpyCursorThreshold=100

I was able to make the mouse work most of the time the way I wanted it to. That being said Im still refining this for my trackpad but this should get you on the right track.

p.s. I put it in a sh script to run at startup so it doesnt revert to the default config in the xorg.conf file. You could also edit that file to make it permanent but as this is a work in progress constantly re-editing system files can be a hassle.

---

### Post by revmarkp on 2010-12-31
THX Stratosmacker. Can I clarify what you're saying please?

Did you [COLOR="Black"]just[/COLOR] do those synclient commands without running the commands as in post # 6 (as at: [http://ubuntuforums.org/showpost.php...27&postcount=6](http://ubuntuforums.org/showpost.php...27&postcount=6) )?

or do you mean you did those additionally. If so:
do you still have touch scrolling?

My main problem was 1. the button area was seen as touch area, turning off horizontal scrolling in mouse preferences sorted that, but then, 2. when I tried to drag the mouse (with left button depressed) the pointer would jump to bottom left of screen as soon as the dragging finger came off the pad, making (eg) dragging a window impossible.

post #6 cured that, I'm just checking that was your issue too? 

gregalynch - estima, mario_k8 and myself did note that the post #6 way does mean no scrolling and no way to turn off the touchpad, but if stratosmacker's solution simply tweaks default settings we could all be in business.

I pressume this problem is caused by the fact that this touchpad is designed for fancy two finger touching in windoze, ala iphone...

---

### Post by Stratosmacker on 2010-12-31
> **revmarkp said:**
> THX Stratosmacker. Can I clarify what you're saying please?

Did you [COLOR="Black"]just[/COLOR] do those synclient commands without running the commands as in post # 6 (as at: [http://ubuntuforums.org/showpost.php...27&postcount=6](http://ubuntuforums.org/showpost.php...27&postcount=6) )?

or do you mean you did those additionally. If so:
do you still have touch scrolling?

My main problem was 1. the button area was seen as touch area, turning off horizontal scrolling in mouse preferences sorted that, but then, 2. when I tried to drag the mouse (with left button depressed) the pointer would jump to bottom left of screen as soon as the dragging finger came off the pad, making (eg) dragging a window impossible.

post #6 cured that, I'm just checking that was your issue too? 

gregalynch - estima, mario_k8 and myself did note that the post #6 way does mean no scrolling and no way to turn off the touchpad, but if stratosmacker's solution simply tweaks default settings we could all be in business.

I pressume this problem is caused by the fact that this touchpad is designed for fancy two finger touching in windoze, ala iphone...


The problem with post 6 is that it stop using the synaptics driver and configuration meaning that the touchpad doesn't have any touchpad unique features (scrolling on the sides) and that it doesnt turn off when you are typing causing allot of problems due to the trackpad placement on these models. These commands are not to be done hand in hand with post 6 as they require the synaptics driver. But they edit the xorg configuration for the touchpad so that it behaves the way it should. In order to revert from any changes made due to post 6 simply delete the only line in /etc/modprobe.d/psmouse.modprobe and restart. THEN run the commands I posted. It should work, but it might need slight tweaking. 

btw this is the thread that helped me [http://ubuntuforums.org/showthread.php?t=1401645](http://ubuntuforums.org/showthread.php?t=1401645)
its just somewhat generic.

---

### Post by lfmiller on 2011-01-13
> **mario_k8 said:**
> Hi!

I had the same problem on a new HP dv6-3120 laptop and Ubuntu 10.10.

I followed these very simple instructions I found on this thread :

[http://ubuntuforums.org/showpost.php?p=8816327&postcount=6](http://ubuntuforums.org/showpost.php?p=8816327&postcount=6)

They refer to a different HP model (a netbook actually) but they worked in my case as well. :)

The pointer no longer jumps around when i put two fingers on the touchpad, and left and right button clicks work just fine (including dragging etc). 

Scrolling does not work yet, but I'm looking into it. I'll let you know if I find out something...

This method worked like a charm on my Pavilion DV6000, touchpad stopped working after upgrading to Ubuntu 10.10, Thanks.

---

### Post by janthonywj on 2011-01-13
I've seen way too many hardware issues with the touch-pads in both HP and Toshiba. I see the eractic jumping around independent of the OS. You may have driver issues in this case with a multi-touch pad, but it might just be a hardware issue as well.

---

### Post by danielhep on 2011-02-15
> **mario_k8 said:**
> Hi!

I had the same problem on a new HP dv6-3120 laptop and Ubuntu 10.10.

I followed these very simple instructions I found on this thread :

[http://ubuntuforums.org/showpost.php?p=8816327&postcount=6](http://ubuntuforums.org/showpost.php?p=8816327&postcount=6)

They refer to a different HP model (a netbook actually) but they worked in my case as well. :)

The pointer no longer jumps around when i put two fingers on the touchpad, and left and right button clicks work just fine (including dragging etc). 

Scrolling does not work yet, but I'm looking into it. I'll let you know if I find out something...

Is there any way to undo this? I've done it, and now I think It's conflicting with the drivers found on the Ubuntu bug tracking page thing. I.e. it's taking control so I don't have multitouch.

---

### Post by Stratosmacker on 2011-02-15
> **Stratosmacker said:**
> The problem with post 6 is that it stop using the synaptics driver and configuration meaning that the touchpad doesn't have any touchpad unique features (scrolling on the sides) and that it doesnt turn off when you are typing causing allot of problems due to the trackpad placement on these models. These commands are not to be done hand in hand with post 6 as they require the synaptics driver. But they edit the xorg configuration for the touchpad so that it behaves the way it should. In order to revert from any changes made due to post 6 simply delete the only line in /etc/modprobe.d/psmouse.modprobe and restart. THEN run the commands I posted. It should work, but it might need slight tweaking. 

btw this is the thread that helped me [http://ubuntuforums.org/showthread.php?t=1401645](http://ubuntuforums.org/showthread.php?t=1401645)
its just somewhat generic.

Look at that

---

### Post by thed0ctor on 2012-01-21
Post6 worked on my HP touchsmart tm2. However, as mentioned above, it disables two finger scrolling. 

The post given by Stratosmacker worked as well:

synclient AreaBottomEdge=3950
synclient JumpyCursorThreshold=100

Just go into the terminal and type these two. The second one returned with "Unknown parameter JumpyCursorThreshold."

However I can now drag and drop while using two finger scroll with only the first line being used. I noticed that right clicking wasn't working. But then I clicked both left and right at the same time and it right clicks. I'd say I can live with this haha. 

If anyone was right clicking before in this manner (using both left and right simultaneously to right click, as noted [here]("https://wiki.ubuntu.com/HP%20TouchSmart%20tm2")) and now it seems to not be working. Try pressing both along the white line on the trackpad,this works for me.

Hope this helps others! I'm on Ubuntu 11.10 x64

---

