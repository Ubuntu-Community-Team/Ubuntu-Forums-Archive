---
title: "Ubuntu 12.04 lts Hp touchpad right click problem"
date: 2012-04-26
forum: Hardware
---

### Post by emirwashere on 2012-04-26
Hi all,

I've just downloaded ubuntu 12.04 lts and It was pretty good experience until i realize to my touchpad problem.

It was same nightmare just like ubuntu 11.10, i can not use my right click function.

I tried this: [http://askubuntu.com/questions/83590/how-do-i-disable-the-touchpad-using-the-upper-left-corner-on-an-hp-pavilion-dv6](http://askubuntu.com/questions/83590/how-do-i-disable-the-touchpad-using-the-upper-left-corner-on-an-hp-pavilion-dv6) but it didn't work, I'm waiting for your help.

ps: I've Hp Probook

SOLVED: [http://ubuntuforums.org/showpost.php?p=11918367&postcount=18](http://ubuntuforums.org/showpost.php?p=11918367&postcount=18)
Thank you Tomkear2006

---

### Post by irishshagua on 2012-04-26
I believe I'm having the same issue. Right click is not working (it is being treated as a left click). I'm using a HP Pavillion dv7

---

### Post by VideoRoy on 2012-04-26
This is a very old, old problem that was supposed to be fixed in 12.04.  I just blew away my working 11.10 config on my HP Mini 2102 because this was supposed to be working now.  I have struggling with this since 10.10 and only help from the community to create hacks has helped.

My only reason to upgrade was that this was supposed to be working.  Time to load the backup and get back to 11.10 or finally move to SUSE which has this simple problem fixed.

Very disappointed again.  Ubuntu just seems to be a bag of hurt on netbooks.

---

### Post by VideoRoy on 2012-04-27
After searching I found one useful tip to reenable the right click but even with that 12.04 is a major step backward from where I was with the patched driver.

Here is what I did:

1. Create _**51-clickpad.conf**_ in _**/etc/X11/xorg.conf.d**_ directory.  Note that xorg.conf.d directory did not exist for me on 12.04 as it did in previous versions so I had to make the directory.
2. Put the following lines in_** 51-clickpad.conf**_
> Section "InputClass"
        Identifier "Default clickpad buttons"
        MatchDriver "synaptics"
        Option "SoftButtonAreas" "50% 0 82% 0 0 0 0 0"

 #Next 3 items added just for the HP Mini to better control the clickpad
    Option "LockedDrags" "1"
    Option "BottomEdge" "4000"
    Option "AreaBottomEdge" "4445"

EndSection

3. Logout / Login for changes to take effect.

The SoftButtonAreas fixes the right click.  The BottomEdge items mask off the bottom of the clickpad so the button will not act like the rest of the clickpad when dragging your finger on it.

I had to add LockedDrags which I hate, because I can no longer left click with my thumb and drag with pointer finger.  The sensitivity is all messed up so locked drags is my only solution if I stay with Ubuntu.  I keep threating to change to SUSE but I like all the rest of Ubuntu better.  The hardware support for Netbooks and laptops with clickpads has been bad for years now.

---

### Post by barrieluv on 2012-04-27
I've had this problem for ages with my Pavilion DV6, but I can get the right click action on 12.04 (running live as I type) by tapping the lower right corner of the touchpad. And by that I mean the lower right corner of the space where you would tap to click in the lower right space (if that makes sense).

---

### Post by VideoRoy on 2012-04-27
> **barrieluv said:**
> I've had this problem for ages with my Pavilion DV6, but I can get the right click action on 12.04 (running live as I type) by tapping the lower right corner of the touchpad. And by that I mean the lower right corner of the space where you would tap to click in the lower right space (if that makes sense).

Yes that works because by default RTCornerButton = 2.  Which means when you tap the lower right corner treat it as a Right Click.  1=Left, 2 =Right, 3=Middle if HW supports.

For those that are interested in your runtime settings, go to Terminal and type [SIZE=2]**synclient -l**[/SIZE] That is a lower case "L".  You can change runtime parameters by typing [SIZE=2]**syclient RTCornerButton=1**[/SIZE] for example.  This will make the right corner a Left click instead for a test.  All changes revert back after logout / login or restart X server.

To remain persistent you have to put them in any file with a .conf extension in the xorg.conf.d directory.

Manpages for this are here [http://manpages.ubuntu.com/manpages/precise/man4/synaptics.4.html](http://manpages.ubuntu.com/manpages/precise/man4/synaptics.4.html)

I have spent way too many hours messing with this since Maverick.

Good luck.

---

### Post by lim1t on 2012-04-27
Hi,

Got same problem on HP Mini 210 2001sa.

Looks like right button on clickpad is not being detected:

```
xinput list-props "SynPS/2 Synaptics TouchPad" | grep Capabilities
```

gives

```
Synaptics Capabilities (297):   1, 0, 0, 1, 1, 1, 1
```

Still got jumpy 'left click + drag', but its soooo close to being fixed! Multitouch etc. all seems to work well.

(update) - As VideoRoy and ufuntoo pointed out that single button detection is probably correct. Instead, when button a is pressed, the driver uses the position of the finger to determine if a left/(middle)/right click took place.

---

### Post by VideoRoy on 2012-04-27
> **lim1t said:**
> Hi,

Got same problem on HP Mini 210 2001sa.

Looks like right button on clickpad is not being detected:

```
xinput list-props "SynPS/2 Synaptics TouchPad" | grep Capabilities
```

gives

```
Synaptics Capabilities (297):   1, 0, 0, 1, 1, 1, 1
```

Still got jumpy 'left click + drag', but its soooo close to being fixed! Multitouch etc. all seems to work well.

I am on the Mini 2102 basically the business model of the 210.  If you use the settings I have above **_Option "SoftButtonAreas" "50% 0 82% 0 0 0 0 0"_** it will give you back the right click.

This was a work around until they fix it in 12.10.

---

### Post by lim1t on 2012-04-27
> **VideoRoy said:**
> I am on the Mini 2102 basically the business model of the 210.  If you use the settings I have above **_Option "SoftButtonAreas" "50% 0 82% 0 0 0 0 0"_** it will give you back the right click.

This was a work around until they fix it in 12.10.

It Works!

Thanks VR, that really is a good workable setup.

---

### Post by ufuntoo on 2012-04-27
So, I have an HP clickpad as well (same SynPS/2 as above).  By accident I determined that the clickpad seems to not distinguish between mechanical buttons.  Instead it uses a 1 finger click as a left click and a 2 finger click as a right click.  Its not intuitive at the start but I personally think it may grow on me.

---

### Post by HPA on 2012-04-28
I've recently upgraded from Ubuntu 11.10 64 bit to Ubuntu 12.04 LTS 64 bit and the problem with the right click on my HP Probook 4520s touchpad reappeared (like it happened in [the upgrade to Ubuntu 11.04]("http://ubuntuforums.org/showthread.php?t=1726450") in last April and the next upgrade to Ubuntu 11.10 in last October).
> **VideoRoy said:**
> Here is what I did:

1. Create _**51-clickpad.conf**_ in _**/etc/X11/xorg.conf.d**_ directory.  Note that xorg.conf.d directory did not exist for me on 12.04 as it did in previous versions so I had to make the directory.
2. Put the following lines in_** 51-clickpad.conf**_

[I]Section "InputClass"
        Identifier "Default clickpad buttons"
        MatchDriver "synaptics"
        Option "SoftButtonAreas" "50% 0 82% 0 0 0 0 0"

 #Next 3 items added just for the HP Mini to better control the clickpad[/I] [I]
    Option "LockedDrags" "1"
    Option "BottomEdge" "4000"
    Option "AreaBottomEdge" "4445"

EndSection                      [/I] 

3. Logout / Login for changes to take effect.The above-mentioned instructions worked.
Thanks VideoRoy.

---

### Post by VideoRoy on 2012-04-28
> **lim1t said:**
> It Works!

Thanks VR, that really is a good workable setup.

I am glad it works.  My only real problem now is the left click / drag as you mentioned.  The Jumpy setting is gone in Precise so for now I am using the Locked Drags parameter I listed above.  It helps mostly even with highlighting text for a copy / paste operation.

Resizing a window is still extremely difficult though.

---

### Post by VideoRoy on 2012-04-28
> **VideoRoy said:**
> Yes that works because by default RTCornerButton = 2.  Which means when you tap the lower right corner treat it as a Right Click.  1=Left, 2 =Right, 3=Middle if HW supports.

For those that are interested in your runtime settings, go to Terminal and type [SIZE=2]**synclient -l**[/SIZE] That is a lower case "L".  You can change runtime parameters by typing [SIZE=2]**syclient RTCornerButton=1**[/SIZE] for example.  This will make the right corner a Left click instead for a test.  All changes revert back after logout / login or restart X server.

To remain persistent you have to put them in any file with a .conf extension in the xorg.conf.d directory.

Manpages for this are here [http://manpages.ubuntu.com/manpages/precise/man4/synaptics.4.html](http://manpages.ubuntu.com/manpages/precise/man4/synaptics.4.html)

I have spent way too many hours messing with this since Maverick.

Good luck.

Just correcting myself here any place I said RTCornerButton should be RBCornerButton.  The difference is the Top versus the Bottom part of the button.

Sorry for any confusion.

---

### Post by HPA on 2012-04-29
I've noticed a new problem with the touchpad after using the VideoRoy's fix.
Before the appearance of the problem, when I pressed the line between the left and the right click on a link of Mozilla Firefox or in Nautilus, this link opened automatically in a new tab.
Now this function is not active.
How can we adjust this?
Thank you.

---

### Post by monkiki on 2012-04-30
Thanks a lot, works pretty well.

---

### Post by AnotherMuggle on 2012-05-07
I posted a patched mouse driver for the last two Ubuntu releases and I'm currently working on porting the patch to the Precise kernel. I can get left middle and right click working beautifully on my HP Mini 210 but I'm struggling with dragging. I will have another look when I get a chance to see if I can figure it our.  If I get a decent patch together then I will post it here along with installation instructions.

EDIT: I have now patched the 12.04 psmouse driver and can confirm the following work:

- Left Click
- Middle Click
- Right Click
- Click and Drag (not 100% but pretty good)
- Tap to Click
- Horizontal and Vertical scrolling

I will get it uploaded with instructions tonight.

---

### Post by Truefire on 2012-05-08
Thanks, I look forward to that!

:popcorn:

---

### Post by AnotherMuggle on 2012-05-08
As promised I have attached my mouse driver patch for kernel 3.2.0-24-generic-pae.  I am using this patch myself but I only just finished tinkering with it so I can't promise anything regarding reliability or whether the patch will work for other people. Hopefully it will help some people out!

1. Download the attached file to your computers desktop
2. sudo apt-get install dkms build-essential
3. cd ~/Desktop
4. tar jxvf psmouse-3.2.0-24-generic-pae.tar.bz2
5. sudo mv psmouse-3.2.0-24-generic-pae /usr/src
6. cd /usr/src
7. sudo chmod -R a+rx psmouse-3.2.0-24-generic-pae
8. sudo dkms add -m psmouse -v 3.2.0-24-generic-pae
9. sudo dkms build -m psmouse -v 3.2.0-24-generic-pae
10. sudo dkms install -m psmouse -v 3.2.0-24-generic-pae
11. sudo modprobe -r psmouse
12. sudo modprobe psmouse
13. sudo dkms status

The output of the last command should look similar to this (with no errors):
"psmouse, 3.2.0-24-generic-pae, 3.2.0-24-generic-pae, i686: installed"

No need to restart the computer as the driver is now loaded and the mouse should be working, including the hardware right button.

---

### Post by argylerabbit on 2012-05-08
The patch worked for me, so far, so good. Thank you!

---

### Post by xbartolo on 2012-05-08
What a great patch. It worked very well. Thank you for the work and for sharing!!

---

### Post by rileynowokowski on 2012-05-08
Tomkear2006's patch worked great. Thanks a ton! This trackpad has always been a source of problems for me and this worked extremely well. Thanks again!

[U]
[/U]

---

### Post by the pwner224 on 2012-05-09
tomkear2006's patch (#16) works perfectly.

---

### Post by randomist33 on 2012-05-09
This works perfectly!!! Thanks!

---

### Post by rbwerst on 2012-05-11
Much appreciated...I put a Solid state hard drive in my HP mini 210; did a fresh Ubuntu 12.04 lts install, and the right click is now working like a charm...on to the file transfer portion of the procedure, and finding out how much the SSD improves this little note-taker's performance.

---

### Post by julianopallaoro on 2012-05-12
It worked properly on my HP dm1-3251br.

Thanks for your help @VideoRoy

Regards,

Juliano


> **VideoRoy said:**
> After searching I found one useful tip to reenable the right click but even with that 12.04 is a major step backward from where I was with the patched driver.

Here is what I did:

1. Create _**51-clickpad.conf**_ in _**/etc/X11/xorg.conf.d**_ directory.  Note that xorg.conf.d directory did not exist for me on 12.04 as it did in previous versions so I had to make the directory.
2. Put the following lines in_** 51-clickpad.conf**_

3. Logout / Login for changes to take effect.

The SoftButtonAreas fixes the right click.  The BottomEdge items mask off the bottom of the clickpad so the button will not act like the rest of the clickpad when dragging your finger on it.

I had to add LockedDrags which I hate, because I can no longer left click with my thumb and drag with pointer finger.  The sensitivity is all messed up so locked drags is my only solution if I stay with Ubuntu.  I keep threating to change to SUSE but I like all the rest of Ubuntu better.  The hardware support for Netbooks and laptops with clickpads has been bad for years now.

---

### Post by ombradelsole on 2012-05-13
Very good for my HP Envy!
It's ok and now I can work using right click.
Thanks a lot to tomkear2006 for this guide and for the psmouse-3.2.0-24-generic-pae.tar.bz2 file.

---

### Post by jwp1 on 2012-05-13
The patch worked for me also

---

### Post by Frank2600 on 2012-05-13
Thank you, it has worked also for me !

---

### Post by ceac13 on 2012-05-13
Work to me! Thanks from Brazil!

---

### Post by nerina on 2012-05-15
Very very tanks tomkear2006 from Italy

---

### Post by emirwashere on 2012-05-16
Works with Hp-Probook 4525s.
Thank you #18

---

### Post by progre55_icky on 2012-05-16
Worked like a charm! Appreciate, tomkear2006

---

### Post by DerHerrMigo on 2012-05-17
Works on HP Mini 210, 32-bit Lubuntu.  Thanks!
Any chance this could go into the build?  While the patch is most appreciated, it would be less frustrating if we didn't have to look for it here...

---

### Post by AnotherMuggle on 2012-05-18
> **DerHerrMigo said:**
> Works on HP Mini 210, 32-bit Lubuntu.  Thanks!
Any chance this could go into the build?  While the patch is most appreciated, it would be less frustrating if we didn't have to look for it here...

I'd be very pleased if it made it into the main Linux Kernel, but I'm not sure of a few things:

1) If it breaks mouse functionality on any other hardware.
2) How to go about submitting the patch for review/acceptance.

Cheers,
TK

---

### Post by varunp87 on 2012-05-18
It's working w/o any issues. Thanks Tk!!

---

### Post by theresaanna on 2012-05-19
Works perfectly on my HP Folio 13. Thanks so much!

---

### Post by earthwormgym on 2012-05-20
Hi,

This patch works on my HP DM-1 touchpad in making right click available but it seems as if my touchpad is devided into 3 areas horizontally so that when I click the pad in the first third I get a left button response, 2nd third middle button and last third right button. This makes it difficult to use as I frequently get a middle button response when I want left. For example it closes tabs in firefox rather than selecting it (annoying as this is the exact opposite of what I want! ;-). I have tried vaious settings for:
TapButton1
TapButton2
TapButton3
ClickFinger1
ClickFinger2
ClickFinger3
SoftButtonAreas 

But nothing seems to change the way this is layed out. What I want is to have the button areas at the bottom of the pad clearly the left and right click areas and then when I click anywhere else I get a left click response.

Has any one else seen this? Any tips?
Thanks

---

### Post by AnotherMuggle on 2012-05-21
> **earthwormgym said:**
> Hi,

This patch works on my HP DM-1 touchpad in making right click available but it seems as if my touchpad is devided into 3 areas horizontally so that when I click the pad in the first third I get a left button response, 2nd third middle button and last third right button. This makes it difficult to use as I frequently get a middle button response when I want left. For example it closes tabs in firefox rather than selecting it (annoying as this is the exact opposite of what I want! ;-). I have tried vaious settings for:
TapButton1
TapButton2
TapButton3
ClickFinger1
ClickFinger2
ClickFinger3
SoftButtonAreas 

But nothing seems to change the way this is layed out. What I want is to have the button areas at the bottom of the pad clearly the left and right click areas and then when I click anywhere else I get a left click response.

Has any one else seen this? Any tips?
Thanks

Hi earthwormgym,

That is exactly how the patch is working, its taking the width of the pad from the firmware, taking the left section as the left button, right section as the right button and anything in the middle as the middle button.  However it should be divided vertically, not horizontally so I'm not sure what's happening there!?

---

### Post by vibemanslim on 2012-05-22
> **tomkear2006 said:**
> As promised I have attached my mouse driver patch for kernel 3.2.0-24-generic-pae.  I am using this patch myself but I only just finished tinkering with it so I can't promise anything regarding reliability or whether the patch will work for other people. Hopefully it will help some people out!

1. Download the attached file to your computers desktop
2. sudo apt-get install dkms build-essential
3. cd ~/Desktop
4. tar jxvf psmouse-3.2.0-24-generic-pae.tar.bz2
5. sudo mv psmouse-3.2.0-24-generic-pae /usr/src
6. cd /usr/src
7. sudo chmod -R a+rx psmouse-3.2.0-24-generic-pae
8. sudo dkms add -m psmouse -v 3.2.0-24-generic-pae
9. sudo dkms build -m psmouse -v 3.2.0-24-generic-pae
10. sudo dkms install -m psmouse -v 3.2.0-24-generic-pae
11. sudo modprobe -r psmouse
12. sudo modprobe psmouse
13. sudo dkms status

The output of the last command should look similar to this (with no errors):
"psmouse, 3.2.0-24-generic-pae, 3.2.0-24-generic-pae, i686: installed"

No need to restart the computer as the driver is now loaded and the mouse should be working, including the hardware right button.

Thanks for the share. This worked for me!

---

### Post by earthwormgym on 2012-05-22
> **tomkear2006 said:**
> Hi earthwormgym,

That is exactly how the patch is working, its taking the width of the pad from the firmware, taking the left section as the left button, right section as the right button and anything in the middle as the middle button.  However it should be divided vertically, not horizontally so I'm not sure what's happening there!?

Thanks for getting back to me. It's devided up vertically not horizontally as I first said.

What I'd like ideally is to only have the buttons section devided into left and right buttons (no middle button) and have the rest of the pad as a left button. Failing that just being able to get rid of the middle button would be good. Is there any way to configure how it is devided?

---

### Post by AnotherMuggle on 2012-05-23
> **earthwormgym said:**
> Thanks for getting back to me. It's devided up vertically not horizontally as I first said.

What I'd like ideally is to only have the buttons section devided into left and right buttons (no middle button) and have the rest of the pad as a left button. Failing that just being able to get rid of the middle button would be good. Is there any way to configure how it is devided?

Are you familiar with c programming? If so then modifying the source code in the patch is straightforward, you can diff it against the original kernel source and you will be able to see where my changes are.  If not then let me know and I will do a version with no middle button, just left and right buttons.

---

### Post by amithbn on 2012-05-28
Thanks for the driver! Works like a charm

---

### Post by sportsdude81 on 2012-05-30
how do uninstall this if I wanted to?  It did fix the right click issue but the click and drag is much worse for me.  I'm on an HP folio 13

---

### Post by AnotherMuggle on 2012-05-31
> **sportsdude81 said:**
> how do uninstall this if I wanted to?  It did fix the right click issue but the click and drag is much worse for me.  I'm on an HP folio 13

Hi sportsdude81,

There are a few fixes in this thread, which one did you use?

Cheers,
TK

---

### Post by Davidgo on 2012-05-31
[QUOTE=AnotherMuggle]

1. Download the attached file to your computers desktop
2. sudo apt-get install dkms build-essential
3. cd ~/Desktop
4. tar jxvf psmouse-3.2.0-24-generic-pae.tar.bz2
5. sudo mv psmouse-3.2.0-24-generic-pae /usr/src
6. cd /usr/src
7. sudo chmod -R a+rx psmouse-3.2.0-24-generic-pae
8. sudo dkms add -m psmouse -v 3.2.0-24-generic-pae
9. sudo dkms build -m psmouse -v 3.2.0-24-generic-pae
10. sudo dkms install -m psmouse -v 3.2.0-24-generic-pae
11. sudo modprobe -r psmouse
12. sudo modprobe psmouse
13. sudo dkms status
[/quote]

Thank you for this.  It works great on my HP Folio 13 with the slightest of modifications -

For anyone using X86 , it seems you can download this package, rename it to the appropriate version instead of "3.2.0-24-generic-pae"  (which you can find by typing uname -a), editing the "PACKAGE_VERSION" in dkms.conf and modifying the above instructions to suit.

---

### Post by Mr0zz on 2012-06-01
The patch works perfectly!! Thank you so much sir! :D

---

### Post by lexya000 on 2012-06-04
> **AnotherMuggle said:**
> As promised I have attached my mouse driver patch for kernel 3.2.0-24-generic-pae.  I am using this patch myself but I only just finished tinkering with it so I can't promise anything regarding reliability or whether the patch will work for other people. Hopefully it will help some people out!

1. Download the attached file to your computers desktop
2. sudo apt-get install dkms build-essential
3. cd ~/Desktop
4. tar jxvf psmouse-3.2.0-24-generic-pae.tar.bz2
5. sudo mv psmouse-3.2.0-24-generic-pae /usr/src
6. cd /usr/src
7. sudo chmod -R a+rx psmouse-3.2.0-24-generic-pae
8. sudo dkms add -m psmouse -v 3.2.0-24-generic-pae
9. sudo dkms build -m psmouse -v 3.2.0-24-generic-pae
10. sudo dkms install -m psmouse -v 3.2.0-24-generic-pae
11. sudo modprobe -r psmouse
12. sudo modprobe psmouse
13. sudo dkms status

The output of the last command should look similar to this (with no errors):
"psmouse, 3.2.0-24-generic-pae, 3.2.0-24-generic-pae, i686: installed"

No need to restart the computer as the driver is now loaded and the mouse should be working, including the hardware right button.


hy, i have an mini hp 210 too...with ubuntu 12.04..and i've made all the things you said....but still doesn't work.... i sais the il correctly install..but nothing...the scrollbar doens't exist! please help me!

---

### Post by AnotherMuggle on 2012-06-05
> **lexya000 said:**
> hy, i have an mini hp 210 too...with ubuntu 12.04..and i've made all the things you said....but still doesn't work.... i sais the il correctly install..but nothing...the scrollbar doens't exist! please help me!

Please post the output of this command:
```
sudo dkms status
```

and this command:
```
uname -a
```

---

### Post by josephaland on 2012-06-09
> **AnotherMuggle said:**
> As promised I have attached my mouse driver patch for kernel 3.2.0-24-generic-pae.

Perfect. Thank you so much. Works great on my HP Pavilion dv6.

---

### Post by russov on 2012-06-10
it works perfectly.
tanks from italy

---

### Post by spyvie on 2012-06-11
The steps in post #18 don't work for me, I can't get past line 7. I don't claim to be an expert and I didn't realize until just now that I would need to be one to set this up. Seems to me it ought to be a little more straight forward to achieve basic functionality from Ubuntu on these VERY MAINSTREAM HP Pavilion DM4 laptops. 

Not much chance I'm going to pursue this further, I don't need the headaches and I have Windows licenses for all of these machines. I's just a shame is all, and I wanted to vent a little. 

Thanks.

---

### Post by AnotherMuggle on 2012-06-11
> **spyvie said:**
> The steps in post #18 don't work for me, I can't get past line 7. I don't claim to be an expert and I didn't realize until just now that I would need to be one to set this up. Seems to me it ought to be a little more straight forward to achieve basic functionality from Ubuntu on these VERY MAINSTREAM HP Pavilion DM4 laptops. 

Not much chance I'm going to pursue this further, I don't need the headaches and I have Windows licenses for all of these machines. I's just a shame is all, and I wanted to vent a little. 

Thanks.

Hi spyvie,

Sorry to hear you're having difficulties. What exactly happens when you get to step 7?

Cheers,
TK

---

### Post by metodiew on 2012-06-12
> **AnotherMuggle said:**
> As promised I have attached my mouse driver patch for kernel 3.2.0-24-generic-pae....  

Thank you for sharing this solution. It works great here at HP Probook 4525s under Ubuntu 12.04 :)

---

### Post by earthwormgym on 2012-06-13
> **AnotherMuggle said:**
> Are you familiar with c programming? If so then modifying the source code in the patch is straightforward, you can diff it against the original kernel source and you will be able to see where my changes are.  If not then let me know and I will do a version with no middle button, just left and right buttons.

Hi, I'm not familiar with c programming but it wasn't too tricky to work out. I have attached a patch file of the changes I have made in case they are useful to any one else. This has the top 80% of the pad being left click with the bottom 20% being split in half for left and right click (no middle button)

---

### Post by AnotherMuggle on 2012-06-13
> **earthwormgym said:**
> Hi, I'm not familiar with c programming but it wasn't too tricky to work out. I have attached a patch file of the changes I have made in case they are useful to any one else. This has the top 80% of the pad being left click with the bottom 20% being split in half for left and right click (no middle button)

Excellent work! Hopefully this satisfy other people who also aren't interested in the middle button.

---

### Post by incindre on 2012-06-15
Hi AnotherMuggle,
I've been struggling with TouchPad issues on my HP-DM1Z; Same as most people I have no hardware right click (its acts as another left click) or pinch to zoom (but most other things work fine).

Your patch seemed like a godsend, but I'm a complete linux novice and running Linux Mint 13 64-bit; thinking that, one being built on the other, it would work fine, I followed all your instructions to the letter (I know, dumb) and it all seemed to work until "11. sudo modprobe -r psmouse" upon which my netbook froze completely.

On force reboot the TouchPad does not work at all.

Is this a salvagable situation? I'd dearly love your input (the Mint community is pretty poor for helping people). Just let me know if I've boned it to death and I'll install Ubuntu!

I've appended the Terminal log for 'uname -a' and 'sudo dkms status'

   **uname -a:**
Linux Vespa 3.2.0-23-generic #36-Ubuntu SMP Tue Apr 10 20:39:51 UTC 2012 x86_64 x86_64 x86_64 GNU/Linux
[B]
sudo dkms status:[/B]
fglrx, 8.960, 3.2.0-23-generic, amd64: installed
psmouse, 3.2.0-24-generic-pae, 3.2.0-23-generic, x86_64: installed (original_module exists)
virtualbox-guest,  4.1.12, 3.2.0-23-generic, x86_64: installed (WARNING! Diff between  built and installed module!) (WARNING! Diff between built and installed  module!) (WARNING! Diff between built and installed module!)

Thanks in advance and sorry for crashing your forums!

---

### Post by AnotherMuggle on 2012-06-15
> **incindre said:**
> Hi AnotherMuggle,
I've been struggling with TouchPad issues on my HP-DM1Z; Same as most people I have no hardware right click (its acts as another left click) or pinch to zoom (but most other things work fine).

Your patch seemed like a godsend, but I'm a complete linux novice and running Linux Mint 13 64-bit; thinking that, one being built on the other, it would work fine, I followed all your instructions to the letter (I know, dumb) and it all seemed to work until "11. sudo modprobe -r psmouse" upon which my netbook froze completely.

On force reboot the TouchPad does not work at all.

Is this a salvagable situation? I'd dearly love your input (the Mint community is pretty poor for helping people). Just let me know if I've boned it to death and I'll install Ubuntu!

I've appended the Terminal log for 'uname -a' and 'sudo dkms status'

   **uname -a:**
Linux Vespa 3.2.0-23-generic #36-Ubuntu SMP Tue Apr 10 20:39:51 UTC 2012 x86_64 x86_64 x86_64 GNU/Linux
[B]
sudo dkms status:[/B]
fglrx, 8.960, 3.2.0-23-generic, amd64: installed
psmouse, 3.2.0-24-generic-pae, 3.2.0-23-generic, x86_64: installed (original_module exists)
virtualbox-guest,  4.1.12, 3.2.0-23-generic, x86_64: installed (WARNING! Diff between  built and installed module!) (WARNING! Diff between built and installed  module!) (WARNING! Diff between built and installed module!)

Thanks in advance and sorry for crashing your forums!

Hi incindre,

I think the first step you need to take is to completely remove the dkms module from your system as it is not compatible with your kernel.  You are using a different kernel version and it is also 64 bit, either of these things, or both, could be causing the problem. 

To remove the module, log in, open a terminal and run the following commands.  Reboot the system and you should be back to square one... a working mouse but left click only.

```

1. sudo dkms uninstall -m psmouse -v 3.2.0-24-generic-pae
2. sudo dkms remove -m psmouse -v 3.2.0-24-generic-pae --all

```

Let me know how you get on with that.

Regards,
Tom

---

### Post by incindre on 2012-06-15
Alright, I have done that, and now the Touchpad works as it did prior, thanks a bunch!
I eagerly await further instruction.

---

### Post by AnotherMuggle on 2012-06-16
> **incindre said:**
> Alright, I have done that, and now the Touchpad works as it did prior, thanks a bunch!
I eagerly await further instruction.

I'm afraid you will need to find someone to port this patch into the default Mint kernel. Unfortunately I don't have a Mint install so I don't think I can help.  Sorry.

TK

---

### Post by incindre on 2012-06-16
Cheers, that's all I needed to hear; I'm going to jump ship to Ubuntu immediately!

---

### Post by ozonito on 2012-06-17
> **AnotherMuggle said:**
> As promised I have attached my mouse driver patch for kernel 3.2.0-24-generic-pae.  I am using this patch myself but I only just finished tinkering with it so I can't promise anything regarding reliability or whether the patch will work for other people. Hopefully it will help some people out!

1. Download the attached file to your computers desktop
2. sudo apt-get install dkms build-essential
3. cd ~/Desktop
4. tar jxvf psmouse-3.2.0-24-generic-pae.tar.bz2
5. sudo mv psmouse-3.2.0-24-generic-pae /usr/src
6. cd /usr/src
7. sudo chmod -R a+rx psmouse-3.2.0-24-generic-pae
8. sudo dkms add -m psmouse -v 3.2.0-24-generic-pae
9. sudo dkms build -m psmouse -v 3.2.0-24-generic-pae
10. sudo dkms install -m psmouse -v 3.2.0-24-generic-pae
11. sudo modprobe -r psmouse
12. sudo modprobe psmouse
13. sudo dkms status

The output of the last command should look similar to this (with no errors):
"psmouse, 3.2.0-24-generic-pae, 3.2.0-24-generic-pae, i686: installed"

No need to restart the computer as the driver is now loaded and the mouse should be working, including the hardware right button.

Fantastic!!!=D> Folio 13 user

---

### Post by sportsdude81 on 2012-06-17
> **AnotherMuggle said:**
> Hi incindre,

I think the first step you need to take is to completely remove the dkms module from your system as it is not compatible with your kernel.  You are using a different kernel version and it is also 64 bit, either of these things, or both, could be causing the problem. 

To remove the module, log in, open a terminal and run the following commands.  Reboot the system and you should be back to square one... a working mouse but left click only.

```

1. sudo dkms uninstall -m psmouse -v 3.2.0-24-generic-pae
2. sudo dkms remove -m psmouse -v 3.2.0-24-generic-pae --all

```

Let me know how you get on with that.

Regards,
Tom

That is what I was looking for.  Thanks AnotherMuggle

---

### Post by sportsdude81 on 2012-06-17
> **earthwormgym said:**
> Hi, I'm not familiar with c programming but it wasn't too tricky to work out. I have attached a patch file of the changes I have made in case they are useful to any one else. This has the top 80% of the pad being left click with the bottom 20% being split in half for left and right click (no middle button)

Perfect!!! This is exactly the change I was planning on making.  Thanks

---

### Post by azevedo on 2012-06-17
Hi, I'm a Folio 13 user, and after the patch everything works fine, left and right click, double-finger scrolling, but when i  click with the left button and try to drag a selection with other finger it doesnt work. Does anybody using a Folio 13 had a similar problem? If yes, do you know how to fix it?

Cheers!

---

### Post by AnotherMuggle on 2012-06-17
> **azevedo said:**
> Hi, I'm a Folio 13 user, and after the patch everything works fine, left and right click, double-finger scrolling, but when i  click with the left button and try to drag a selection with other finger it doesnt work. Does anybody using a Folio 13 had a similar problem? If yes, do you know how to fix it?

Cheers!

When you click the left button, try placing the touch right on the bottom edge of the touch area.  Does that help?

It might be because some of the coordinates are slightly different in the touchpad on that device and need tweaking in the source code.

---

### Post by mrbuhi on 2012-06-18
> **AnotherMuggle said:**
> As promised I have attached my mouse driver patch for kernel 3.2.0-24-generic-pae.  I am using this patch myself but I only just finished tinkering with it so I can't promise anything regarding reliability or whether the patch will work for other people. Hopefully it will help some people out!

1. Download the attached file to your computers desktop
2. sudo apt-get install dkms build-essential
3. cd ~/Desktop
4. tar jxvf psmouse-3.2.0-24-generic-pae.tar.bz2
5. sudo mv psmouse-3.2.0-24-generic-pae /usr/src
6. cd /usr/src
7. sudo chmod -R a+rx psmouse-3.2.0-24-generic-pae
8. sudo dkms add -m psmouse -v 3.2.0-24-generic-pae
9. sudo dkms build -m psmouse -v 3.2.0-24-generic-pae
10. sudo dkms install -m psmouse -v 3.2.0-24-generic-pae
11. sudo modprobe -r psmouse
12. sudo modprobe psmouse
13. sudo dkms status

The output of the last command should look similar to this (with no errors):
"psmouse, 3.2.0-24-generic-pae, 3.2.0-24-generic-pae, i686: installed"

No need to restart the computer as the driver is now loaded and the mouse should be working, including the hardware right button.

Thank You so much. That perfectly works. I just changed the kernel version with mine.

---

### Post by azevedo on 2012-06-18
> **AnotherMuggle said:**
> When you click the left button, try placing the touch right on the bottom edge of the touch area.  Does that help?

It might be because some of the coordinates are slightly different in the touchpad on that device and need tweaking in the source code.

Hi, it's weird, but after restarting the computer, now it's actually working, not very properly though. depending on how i click on the left button, im able to drag or not. I still havent figured out exactly what is the best way to do it. But as im usually use an usb mouse I wont take it too seriously. Thanks for the attention, by the way.

---

### Post by Dynaflow on 2012-06-19
> **AnotherMuggle said:**
> As promised I have attached my mouse driver patch for kernel 3.2.0-24-generic-pae.  I am using this patch myself but I only just finished tinkering with it so I can't promise anything regarding reliability or whether the patch will work for other people. Hopefully it will help some people out!

1. Download the attached file to your computers desktop
2. sudo apt-get install dkms build-essential
3. cd ~/Desktop
4. tar jxvf psmouse-3.2.0-24-generic-pae.tar.bz2
5. sudo mv psmouse-3.2.0-24-generic-pae /usr/src
6. cd /usr/src
7. sudo chmod -R a+rx psmouse-3.2.0-24-generic-pae
8. sudo dkms add -m psmouse -v 3.2.0-24-generic-pae
9. sudo dkms build -m psmouse -v 3.2.0-24-generic-pae
10. sudo dkms install -m psmouse -v 3.2.0-24-generic-pae
11. sudo modprobe -r psmouse
12. sudo modprobe psmouse
13. sudo dkms status

The output of the last command should look similar to this (with no errors):
"psmouse, 3.2.0-24-generic-pae, 3.2.0-24-generic-pae, i686: installed"

No need to restart the computer as the driver is now loaded and the mouse should be working, including the hardware right button.

At step 11, X is crashing and I'm being returned to the initial login window without any use of the touchpad at all.  

This problem has been re-occurring for so long, if I can't fix this soon, I'm probably going to move this machine to the new iteration of Fedora Core, which does not seem to have any issues with my Mini 210's hardware in my live-distro tests.  I'm quite happy with how 12.04  is working on my full-size laptop (which has been running Ubuntu since 6.10), but on this netbook, Ubuntu has been somewhat of a pig for the last few upgrade cycles because of this and several other hardware issues.  Has anyone else had this level of frustration with their HP Mini's, or is mine just special?

---

### Post by AnotherMuggle on 2012-06-20
> **Dynaflow said:**
> At step 11, X is crashing and I'm being returned to the initial login window without any use of the touchpad at all.  

This problem has been re-occurring for so long, if I can't fix this soon, I'm probably going to move this machine to the new iteration of Fedora Core, which does not seem to have any issues with my Mini 210's hardware in my live-distro tests.  I'm quite happy with how 12.04  is working on my full-size laptop (which has been running Ubuntu since 6.10), but on this netbook, Ubuntu has been somewhat of a pig for the last few upgrade cycles because of this and several other hardware issues.  Has anyone else had this level of frustration with their HP Mini's, or is mine just special?

The touchpad has been my main cause of problems with Ubuntu on my Mini 210.  I have tried other distro's and been faced with the same problems.  It's interesting that you say Fedora doesn't have the same issue, they must be applying a patch themselves or using a different driver for touchpad support.

---

### Post by slayaplaya16 on 2012-06-28
> **AnotherMuggle said:**
> As promised I have attached my mouse driver patch for kernel 3.2.0-24-generic-pae.  I am using this patch myself but I only just finished tinkering with it so I can't promise anything regarding reliability or whether the patch will work for other people. Hopefully it will help some people out!

1. Download the attached file to your computers desktop
2. sudo apt-get install dkms build-essential
3. cd ~/Desktop
4. tar jxvf psmouse-3.2.0-24-generic-pae.tar.bz2
5. sudo mv psmouse-3.2.0-24-generic-pae /usr/src
6. cd /usr/src
7. sudo chmod -R a+rx psmouse-3.2.0-24-generic-pae
8. sudo dkms add -m psmouse -v 3.2.0-24-generic-pae
9. sudo dkms build -m psmouse -v 3.2.0-24-generic-pae
10. sudo dkms install -m psmouse -v 3.2.0-24-generic-pae
11. sudo modprobe -r psmouse
12. sudo modprobe psmouse
13. sudo dkms status

The output of the last command should look similar to this (with no errors):
"psmouse, 3.2.0-24-generic-pae, 3.2.0-24-generic-pae, i686: installed"

No need to restart the computer as the driver is now loaded and the mouse should be working, including the hardware right button.

Will this work with kernel version 3.2.0-26? If not I have coded a bit in c++ and could try to patch the patch for this version, but just wanted to see if it would work before I break my kernel. Thanks!

---

### Post by AnotherMuggle on 2012-06-28
> **slayaplaya16 said:**
> Will this work with kernel version 3.2.0-26? If not I have coded a bit in c++ and could try to patch the patch for this version, but just wanted to see if it would work before I break my kernel. Thanks!

I just downloaded the source for 3.2.0-26 and a diff shows the mouse driver hasn't changed at all.  You may need to change the kernel version in the dkms.conf file, but I don't know for sure.

---

### Post by aia832003 on 2012-06-30
> **AnotherMuggle said:**
> I just downloaded the source for 3.2.0-26 and a diff shows the mouse driver hasn't changed at all.  You may need to change the kernel version in the dkms.conf file, but I don't know for sure.

I had the same problems. Re-run steps 9-13 and it will rebuild the driver for the proper kernel.

---

### Post by mioxnam on 2012-07-01
I just installed ubuntu 12.04 in my Inspiron dell n5010. When i tried to touch my touch pad the right click button stop functioning. Just gone crazy. I tried this one from the post i saw with no errors still not helping.

1. Download the attached file to your computers desktop
2. sudo apt-get install dkms build-essential
3. cd ~/Desktop
4. tar jxvf psmouse-3.2.0-24-generic-pae.tar.bz2
5. sudo mv psmouse-3.2.0-24-generic-pae /usr/src
6. cd /usr/src
7. sudo chmod -R a+rx psmouse-3.2.0-24-generic-pae
8. sudo dkms add -m psmouse -v 3.2.0-24-generic-pae
9. sudo dkms build -m psmouse -v 3.2.0-24-generic-pae
10. sudo dkms install -m psmouse -v 3.2.0-24-generic-pae
11. sudo modprobe -r psmouse
12. sudo modprobe psmouse
13. sudo dkms status

The output of the last command should look similar to this (with no errors):
"psmouse, 3.2.0-24-generic-pae, 3.2.0-24-generic-pae, i686: installed"

So could someone got another way to help me please. For now i disabled my touch pad using this synclient TouchpadOff=1. Till someone could make a working instruction for dell.

---

### Post by AnotherMuggle on 2012-07-01
> **mioxnam said:**
> I just installed ubuntu 12.04 in my Inspiron dell n5010. When i tried to touch my touch pad the right click button stop functioning. Just gone crazy. I tried this one from the post i saw with no errors still not helping.

1. Download the attached file to your computers desktop
2. sudo apt-get install dkms build-essential
3. cd ~/Desktop
4. tar jxvf psmouse-3.2.0-24-generic-pae.tar.bz2
5. sudo mv psmouse-3.2.0-24-generic-pae /usr/src
6. cd /usr/src
7. sudo chmod -R a+rx psmouse-3.2.0-24-generic-pae
8. sudo dkms add -m psmouse -v 3.2.0-24-generic-pae
9. sudo dkms build -m psmouse -v 3.2.0-24-generic-pae
10. sudo dkms install -m psmouse -v 3.2.0-24-generic-pae
11. sudo modprobe -r psmouse
12. sudo modprobe psmouse
13. sudo dkms status

The output of the last command should look similar to this (with no errors):
"psmouse, 3.2.0-24-generic-pae, 3.2.0-24-generic-pae, i686: installed"

So could someone got another way to help me please. For now i disabled my touch pad using this synclient TouchpadOff=1. Till someone could make a working instruction for dell.

Sorry I can't help with fixing your problem but you should start by removing this patch because it could confuse any other fixes you try to put in place.

This patch was written specifically for HP Mini netbooks which have a single hardware button underneath the touch area of the touchpad.

Run these commands to remove the patch:
```
1. sudo dkms uninstall -m psmouse -v 3.2.0-24-generic-pae
2. sudo dkms remove -m psmouse -v 3.2.0-24-generic-pae --all
```

---

### Post by Richimax on 2012-07-01
Thanks you! My first time that i use Ubuntu, i have a lot problems with graphic card, touchpad, etc. but you help me a lot with it. Now is ok my touchpad.;)

> **AnotherMuggle said:**
> As promised I have attached my mouse driver patch for kernel 3.2.0-24-generic-pae.  I am using this patch myself but I only just finished tinkering with it so I can't promise anything regarding reliability or whether the patch will work for other people. Hopefully it will help some people out!

1. Download the attached file to your computers desktop
2. sudo apt-get install dkms build-essential
3. cd ~/Desktop
4. tar jxvf psmouse-3.2.0-24-generic-pae.tar.bz2
5. sudo mv psmouse-3.2.0-24-generic-pae /usr/src
6. cd /usr/src
7. sudo chmod -R a+rx psmouse-3.2.0-24-generic-pae
8. sudo dkms add -m psmouse -v 3.2.0-24-generic-pae
9. sudo dkms build -m psmouse -v 3.2.0-24-generic-pae
10. sudo dkms install -m psmouse -v 3.2.0-24-generic-pae
11. sudo modprobe -r psmouse
12. sudo modprobe psmouse
13. sudo dkms status

The output of the last command should look similar to this (with no errors):
"psmouse, 3.2.0-24-generic-pae, 3.2.0-24-generic-pae, i686: installed"

No need to restart the computer as the driver is now loaded and the mouse should be working, including the hardware right button.

---

### Post by udaraseneviratne on 2012-07-02
> **AnotherMuggle said:**
> As promised I have attached my mouse driver patch for kernel 3.2.0-24-generic-pae.  I am using this patch myself but I only just finished tinkering with it so I can't promise anything regarding reliability or whether the patch will work for other people. Hopefully it will help some people out!

1. Download the attached file to your computers desktop
2. sudo apt-get install dkms build-essential
3. cd ~/Desktop
4. tar jxvf psmouse-3.2.0-24-generic-pae.tar.bz2
5. sudo mv psmouse-3.2.0-24-generic-pae /usr/src
6. cd /usr/src
7. sudo chmod -R a+rx psmouse-3.2.0-24-generic-pae
8. sudo dkms add -m psmouse -v 3.2.0-24-generic-pae
9. sudo dkms build -m psmouse -v 3.2.0-24-generic-pae
10. sudo dkms install -m psmouse -v 3.2.0-24-generic-pae
11. sudo modprobe -r psmouse
12. sudo modprobe psmouse
13. sudo dkms status

The output of the last command should look similar to this (with no errors):
"psmouse, 3.2.0-24-generic-pae, 3.2.0-24-generic-pae, i686: installed"

No need to restart the computer as the driver is now loaded and the mouse should be working, including the hardware right button.

It works very well on my PC thank you very much...................

---

### Post by wilson99 on 2012-07-05
It worked with HP DV6 3020EP...
Thank you!!!:p

I had some trouble with cd ~/Desktop (I had to rename it... in portuguese is Área de Trabalho)

THANK YOU, and greetings from Portugal!

---

### Post by gunashekar on 2012-07-05
Thank you for these. I am looking for all such fixes for my daughters new(proposed) HP mini on which I plan to install Ubuntu 12.04 . Where can I find more fixes for issues with ubuntu on HP mini? 
Or would anyone advice a better netbook brand/model than HP mini?
Regards
guna

---

### Post by bdeviitb on 2012-07-06
Thanks buddy

---

### Post by mohsaba on 2012-07-07
> **AnotherMuggle said:**
> As promised I have attached my mouse driver patch for kernel 3.2.0-24-generic-pae.  I am using this patch myself but I only just finished tinkering with it so I can't promise anything regarding reliability or whether the patch will work for other people. Hopefully it will help some people out!

1. Download the attached file to your computers desktop
2. sudo apt-get install dkms build-essential
3. cd ~/Desktop
4. tar jxvf psmouse-3.2.0-24-generic-pae.tar.bz2
5. sudo mv psmouse-3.2.0-24-generic-pae /usr/src
6. cd /usr/src
7. sudo chmod -R a+rx psmouse-3.2.0-24-generic-pae
8. sudo dkms add -m psmouse -v 3.2.0-24-generic-pae
9. sudo dkms build -m psmouse -v 3.2.0-24-generic-pae
10. sudo dkms install -m psmouse -v 3.2.0-24-generic-pae
11. sudo modprobe -r psmouse
12. sudo modprobe psmouse
13. sudo dkms status

The output of the last command should look similar to this (with no errors):
"psmouse, 3.2.0-24-generic-pae, 3.2.0-24-generic-pae, i686: installed"

No need to restart the computer as the driver is now loaded and the mouse should be working, including the hardware right button.

It works fine, thank you.

---

### Post by aeirado on 2012-07-08
> **AnotherMuggle said:**
> As promised I have attached my mouse driver patch for kernel 3.2.0-24-generic-pae.  I am using this patch myself but I only just finished tinkering with it so I can't promise anything regarding reliability or whether the patch will work for other people. Hopefully it will help some people out!

1. Download the attached file to your computers desktop
2. sudo apt-get install dkms build-essential
3. cd ~/Desktop
4. tar jxvf psmouse-3.2.0-24-generic-pae.tar.bz2
5. sudo mv psmouse-3.2.0-24-generic-pae /usr/src
6. cd /usr/src
7. sudo chmod -R a+rx psmouse-3.2.0-24-generic-pae
8. sudo dkms add -m psmouse -v 3.2.0-24-generic-pae
9. sudo dkms build -m psmouse -v 3.2.0-24-generic-pae
10. sudo dkms install -m psmouse -v 3.2.0-24-generic-pae
11. sudo modprobe -r psmouse
12. sudo modprobe psmouse
13. sudo dkms status

The output of the last command should look similar to this (with no errors):
"psmouse, 3.2.0-24-generic-pae, 3.2.0-24-generic-pae, i686: installed"

No need to restart the computer as the driver is now loaded and the mouse should be working, including the hardware right button.

Hi, 
Thanks a lot AnotherMuggles!
It works on HP Pavilion DV6, kernel 3.2.0-26 (dkms.conf edited)

---

### Post by ksenofor on 2012-07-12
> **AnotherMuggle said:**
> As promised I have attached my mouse driver patch for kernel 3.2.0-24-generic-pae.  I am using this patch myself but I only just finished tinkering with it so I can't promise anything regarding reliability or whether the patch will work for other people. Hopefully it will help some people out!

1. Download the attached file to your computers desktop
2. sudo apt-get install dkms build-essential
3. cd ~/Desktop
4. tar jxvf psmouse-3.2.0-24-generic-pae.tar.bz2
5. sudo mv psmouse-3.2.0-24-generic-pae /usr/src
6. cd /usr/src
7. sudo chmod -R a+rx psmouse-3.2.0-24-generic-pae
8. sudo dkms add -m psmouse -v 3.2.0-24-generic-pae
9. sudo dkms build -m psmouse -v 3.2.0-24-generic-pae
10. sudo dkms install -m psmouse -v 3.2.0-24-generic-pae
11. sudo modprobe -r psmouse
12. sudo modprobe psmouse
13. sudo dkms status

The output of the last command should look similar to this (with no errors):
"psmouse, 3.2.0-24-generic-pae, 3.2.0-24-generic-pae, i686: installed"

No need to restart the computer as the driver is now loaded and the mouse should be working, including the hardware right button.

You are really superman - a lot... no.. A LOT OF THANKS!!!
It was my dream to use right mouse on my thouchpad with HP 4525s

---

### Post by ralynx on 2012-07-15
Thanks from Puerto Rico!!

---

### Post by aman451 on 2012-07-17
Thanks a lot man... :D

---

### Post by tompeach on 2012-07-17
> **AnotherMuggle said:**
> As promised I have attached my mouse driver patch for kernel 3.2.0-24-generic-pae.  I am using this patch myself but I only just finished tinkering with it so I can't promise anything regarding reliability or whether the patch will work for other people. Hopefully it will help some people out!

1. Download the attached file to your computers desktop
2. sudo apt-get install dkms build-essential
3. cd ~/Desktop
4. tar jxvf psmouse-3.2.0-24-generic-pae.tar.bz2
5. sudo mv psmouse-3.2.0-24-generic-pae /usr/src
6. cd /usr/src
7. sudo chmod -R a+rx psmouse-3.2.0-24-generic-pae
8. sudo dkms add -m psmouse -v 3.2.0-24-generic-pae
9. sudo dkms build -m psmouse -v 3.2.0-24-generic-pae
10. sudo dkms install -m psmouse -v 3.2.0-24-generic-pae
11. sudo modprobe -r psmouse
12. sudo modprobe psmouse
13. sudo dkms status

The output of the last command should look similar to this (with no errors):
"psmouse, 3.2.0-24-generic-pae, 3.2.0-24-generic-pae, i686: installed"

No need to restart the computer as the driver is now loaded and the mouse should be working, including the hardware right button.

I followed these steps on my HP mini210 and got an error at step 9 (I think)

below is the contents of the make.log file



DKMS make.log for psmouse-3.2.0-24-generic-pae for kernel 3.0.0-22-generic (i686)
Tue Jul 17 21:43:16 BST 2012
make: Entering directory `/usr/src/linux-headers-3.0.0-22-generic'
  CC [M]  /var/lib/dkms/psmouse/3.2.0-24-generic-pae/build/src/psmouse-base.o
  CC [M]  /var/lib/dkms/psmouse/3.2.0-24-generic-pae/build/src/synaptics.o
/var/lib/dkms/psmouse/3.2.0-24-generic-pae/build/src/synaptics.c: In function ‘set_input_params’:
/var/lib/dkms/psmouse/3.2.0-24-generic-pae/build/src/synaptics.c:1217:13: error: ‘BTN_TOOL_QUINTTAP’ undeclared (first use in this function)
/var/lib/dkms/psmouse/3.2.0-24-generic-pae/build/src/synaptics.c:1217:13: note: each undeclared identifier is reported only once for each function it appears in
make[1]: *** [/var/lib/dkms/psmouse/3.2.0-24-generic-pae/build/src/synaptics.o] Error 1
make: *** [psmouse.ko] Error 2
make: Leaving directory `/usr/src/linux-headers-3.0.0-22-generic'

PLEASE - anyone HELP!!

---

### Post by tompeach on 2012-07-19
Come on Ubuntu Community, has anybody got a clue how to fix my problem above?

I don't want to go back to winbloze but if I can't make this work, I have no choice.

I was told that the community here was active and friendly.

Please someone help...

---

### Post by helgatheviking on 2012-07-24
> **AnotherMuggle said:**
> As promised I have attached my mouse driver patch for kernel 3.2.0-24-generic-pae.  I am using this patch myself but I only just finished tinkering with it so I can't promise anything regarding reliability or whether the patch will work for other people. Hopefully it will help some people out!

1. Download the attached file to your computers desktop
2. sudo apt-get install dkms build-essential
3. cd ~/Desktop
4. tar jxvf psmouse-3.2.0-24-generic-pae.tar.bz2
5. sudo mv psmouse-3.2.0-24-generic-pae /usr/src
6. cd /usr/src
7. sudo chmod -R a+rx psmouse-3.2.0-24-generic-pae
8. sudo dkms add -m psmouse -v 3.2.0-24-generic-pae
9. sudo dkms build -m psmouse -v 3.2.0-24-generic-pae
10. sudo dkms install -m psmouse -v 3.2.0-24-generic-pae
11. sudo modprobe -r psmouse
12. sudo modprobe psmouse
13. sudo dkms status

The output of the last command should look similar to this (with no errors):
"psmouse, 3.2.0-24-generic-pae, 3.2.0-24-generic-pae, i686: installed"

No need to restart the computer as the driver is now loaded and the mouse should be working, including the hardware right button.

AnotherMuggle,

Is this an HP specific patch?  I probably should've asked that before trying it, but I'm not seeing any difference on my Samsung 7, which is experiencing the same trouble of no right click.

---

### Post by AnotherMuggle on 2012-07-24
> **helgatheviking said:**
> AnotherMuggle,

Is this an HP specific patch?  I probably should've asked that before trying it, but I'm not seeing any difference on my Samsung 7, which is experiencing the same trouble of no right click.

The patch was put together specifically for the HP Mini 210 with little regard for any other devices.

If it didn't help with your Samsung 7 then follow the removal instructions in post #74 to ensure it doesn't cause confusion with any other potential fixes.

---

### Post by AnotherMuggle on 2012-07-26
> **tompeach said:**
> I followed these steps on my HP mini210 and got an error at step 9 (I think)

below is the contents of the make.log file



DKMS make.log for psmouse-3.2.0-24-generic-pae for kernel 3.0.0-22-generic (i686)
Tue Jul 17 21:43:16 BST 2012
make: Entering directory `/usr/src/linux-headers-3.0.0-22-generic'
  CC [M]  /var/lib/dkms/psmouse/3.2.0-24-generic-pae/build/src/psmouse-base.o
  CC [M]  /var/lib/dkms/psmouse/3.2.0-24-generic-pae/build/src/synaptics.o
/var/lib/dkms/psmouse/3.2.0-24-generic-pae/build/src/synaptics.c: In function ‘set_input_params’:
/var/lib/dkms/psmouse/3.2.0-24-generic-pae/build/src/synaptics.c:1217:13: error: ‘BTN_TOOL_QUINTTAP’ undeclared (first use in this function)
/var/lib/dkms/psmouse/3.2.0-24-generic-pae/build/src/synaptics.c:1217:13: note: each undeclared identifier is reported only once for each function it appears in
make[1]: *** [/var/lib/dkms/psmouse/3.2.0-24-generic-pae/build/src/synaptics.o] Error 1
make: *** [psmouse.ko] Error 2
make: Leaving directory `/usr/src/linux-headers-3.0.0-22-generic'

PLEASE - anyone HELP!!

Hi Tom,

Just got your PM. I somehow missed this message on the forums.

By the look of the log messages there is a kernel version conflict. You appear to have the kernel 3.0.0-22-generic... I am guessing this is Ubuntu 11.10 (Oneiric)?

If that is the case then this isn't the patch for you. I did do one for 11.10 which you can find here: [http://ubuntuforums.org/showthread.php?t=1388164&page=27]("http://ubuntuforums.org/showthread.php?t=1388164&page=27") post #265.  I can't promise anything but that one should do the trick!  The instructions remain the same just use the different version number where applicable.

Hope that helps,
TK

---

### Post by jigsaw! on 2012-07-27
> **AnotherMuggle said:**
> As promised I have attached my mouse driver patch for kernel 3.2.0-24-generic-pae.  I am using this patch myself but I only just finished tinkering with it so I can't promise anything regarding reliability or whether the patch will work for other people. Hopefully it will help some people out!

1. Download the attached file to your computers desktop
2. sudo apt-get install dkms build-essential
3. cd ~/Desktop
4. tar jxvf psmouse-3.2.0-24-generic-pae.tar.bz2
5. sudo mv psmouse-3.2.0-24-generic-pae /usr/src
6. cd /usr/src
7. sudo chmod -R a+rx psmouse-3.2.0-24-generic-pae
8. sudo dkms add -m psmouse -v 3.2.0-24-generic-pae
9. sudo dkms build -m psmouse -v 3.2.0-24-generic-pae
10. sudo dkms install -m psmouse -v 3.2.0-24-generic-pae
11. sudo modprobe -r psmouse
12. sudo modprobe psmouse
13. sudo dkms status

The output of the last command should look similar to this (with no errors):
"psmouse, 3.2.0-24-generic-pae, 3.2.0-24-generic-pae, i686: installed"

No need to restart the computer as the driver is now loaded and the mouse should be working, including the hardware right button.

Dude, thank you a lot!!!

You are my hero!!! )))

---

### Post by kuroquick on 2012-07-28
> **AnotherMuggle said:**
> As promised I have attached my mouse driver patch for kernel 3.2.0-24-generic-pae.  I am using this patch myself but I only just finished tinkering with it so I can't promise anything regarding reliability or whether the patch will work for other people. Hopefully it will help some people out!

1. Download the attached file to your computers desktop
2. sudo apt-get install dkms build-essential
3. cd ~/Desktop
4. tar jxvf psmouse-3.2.0-24-generic-pae.tar.bz2
5. sudo mv psmouse-3.2.0-24-generic-pae /usr/src
6. cd /usr/src
7. sudo chmod -R a+rx psmouse-3.2.0-24-generic-pae
8. sudo dkms add -m psmouse -v 3.2.0-24-generic-pae
9. sudo dkms build -m psmouse -v 3.2.0-24-generic-pae
10. sudo dkms install -m psmouse -v 3.2.0-24-generic-pae
11. sudo modprobe -r psmouse
12. sudo modprobe psmouse
13. sudo dkms status

The output of the last command should look similar to this (with no errors):
"psmouse, 3.2.0-24-generic-pae, 3.2.0-24-generic-pae, i686: installed"

No need to restart the computer as the driver is now loaded and the mouse should be working, including the hardware right button.

thanks you
perfect solution for me

---

### Post by tricolorpoa on 2012-07-28
> **AnotherMuggle said:**
> As promised I have attached my mouse driver patch for kernel 3.2.0-24-generic-pae.  I am using this patch myself but I only just finished tinkering with it so I can't promise anything regarding reliability or whether the patch will work for other people. Hopefully it will help some people out!

1. Download the attached file to your computers desktop
2. sudo apt-get install dkms build-essential
3. cd ~/Desktop
4. tar jxvf psmouse-3.2.0-24-generic-pae.tar.bz2
5. sudo mv psmouse-3.2.0-24-generic-pae /usr/src
6. cd /usr/src
7. sudo chmod -R a+rx psmouse-3.2.0-24-generic-pae
8. sudo dkms add -m psmouse -v 3.2.0-24-generic-pae
9. sudo dkms build -m psmouse -v 3.2.0-24-generic-pae
10. sudo dkms install -m psmouse -v 3.2.0-24-generic-pae
11. sudo modprobe -r psmouse
12. sudo modprobe psmouse
13. sudo dkms status

The output of the last command should look similar to this (with no errors):
"psmouse, 3.2.0-24-generic-pae, 3.2.0-24-generic-pae, i686: installed"

No need to restart the computer as the driver is now loaded and the mouse should be working, including the hardware right button.


Thanks!!!! :P

---

### Post by tompeach on 2012-07-29
> **AnotherMuggle said:**
> Hi Tom,

Just got your PM. I somehow missed this message on the forums.

By the look of the log messages there is a kernel version conflict. You appear to have the kernel 3.0.0-22-generic... I am guessing this is Ubuntu 11.10 (Oneiric)?

If that is the case then this isn't the patch for you. I did do one for 11.10 which you can find here: [http://ubuntuforums.org/showthread.php?t=1388164&page=27](http://ubuntuforums.org/showthread.php?t=1388164&page=27) post #265.  I can't promise anything but that one should do the trick!  The instructions remain the same just use the different version number where applicable.

Hope that helps,
TK


It certainly did, worked a treat. I now have a working laptop - Thanks

You are truly a Linux Genius!!!

Much Appreciated.

---

### Post by kriengten on 2012-08-03
it work on acer aspire one v5-171
thanks

---

### Post by HPA on 2012-08-14
I have a different problem:
The middle click in my HP Probook 4520s Touchpad doesn't work after upgrade to Ubuntu 12.04 (64 bit).
How can I fix this problem?
Thank you.

---

### Post by AnotherMuggle on 2012-08-20
> **HPA said:**
> I have a different problem:
The middle click in my HP Probook 4520s Touchpad doesn't work after upgrade to Ubuntu 12.04 (64 bit).
How can I fix this problem?
Thank you.

Does this help?:
[http://askubuntu.com/questions/130393/how-to-configure-the-touchpad-middle-click]("http://askubuntu.com/questions/130393/how-to-configure-the-touchpad-middle-click")

---

### Post by HPA on 2012-08-20
Thanks for your help.
I followed all suggestions presented here [http://askubuntu.com/questions/130393/how-to-configure-the-touchpad-middle-click](http://askubuntu.com/questions/130393/how-to-configure-the-touchpad-middle-click) but the problem remains.
The only think I want is to open links in a new tab whenever I press the borderline between left and right click on the touchpad of my HP Probook 4520s.
That worked before the upgrade to Ubuntu 12.04.
I never used three finger click.
Actually, I don't know exactly how it works and I never cared about it.

---

### Post by malegria on 2012-08-20
> **AnotherMuggle said:**
> As promised I have attached my mouse driver patch for kernel 3.2.0-24-generic-pae.  I am using this patch myself but I only just finished tinkering with it so I can't promise anything regarding reliability or whether the patch will work for other people. Hopefully it will help some people out!

1. Download the attached file to your computers desktop
2. sudo apt-get install dkms build-essential
3. cd ~/Desktop
4. tar jxvf psmouse-3.2.0-24-generic-pae.tar.bz2
5. sudo mv psmouse-3.2.0-24-generic-pae /usr/src
6. cd /usr/src
7. sudo chmod -R a+rx psmouse-3.2.0-24-generic-pae
8. sudo dkms add -m psmouse -v 3.2.0-24-generic-pae
9. sudo dkms build -m psmouse -v 3.2.0-24-generic-pae
10. sudo dkms install -m psmouse -v 3.2.0-24-generic-pae
11. sudo modprobe -r psmouse
12. sudo modprobe psmouse
13. sudo dkms status

The output of the last command should look similar to this (with no errors):
"psmouse, 3.2.0-24-generic-pae, 3.2.0-24-generic-pae, i686: installed"

No need to restart the computer as the driver is now loaded and the mouse should be working, including the hardware right button.

Would this also work if I am using kernel 3.2.0-29-generic-pae?

---

### Post by retracenz on 2012-08-21
> **AnotherMuggle said:**
> As promised I have attached my mouse driver patch for kernel 3.2.0-24-generic-pae.  I am using this patch myself but I only just finished tinkering with it so I can't promise anything regarding reliability or whether the patch will work for other people. Hopefully it will help some people out!

1. Download the attached file to your computers desktop
2. sudo apt-get install dkms build-essential
3. cd ~/Desktop
4. tar jxvf psmouse-3.2.0-24-generic-pae.tar.bz2
5. sudo mv psmouse-3.2.0-24-generic-pae /usr/src
6. cd /usr/src
7. sudo chmod -R a+rx psmouse-3.2.0-24-generic-pae
8. sudo dkms add -m psmouse -v 3.2.0-24-generic-pae
9. sudo dkms build -m psmouse -v 3.2.0-24-generic-pae
10. sudo dkms install -m psmouse -v 3.2.0-24-generic-pae
11. sudo modprobe -r psmouse
12. sudo modprobe psmouse
13. sudo dkms status

The output of the last command should look similar to this (with no errors):
"psmouse, 3.2.0-24-generic-pae, 3.2.0-24-generic-pae, i686: installed"

No need to restart the computer as the driver is now loaded and the mouse should be working, including the hardware right button.
Excellent!

---

### Post by HPA on 2012-08-21
> **malegria said:**
> Would this also work if I am using kernel 3.2.0-29-generic-pae?I don't think so. In previous cases (for Ubuntu 10.10, 11.04 and 11.10) the patch was kernel-dependent.
However, the most appropriate person to answer to your question is AnotherMuggle.

---

### Post by dhizzy13 on 2012-08-29
> Originally Posted by AnotherMuggle  
As promised I have attached my mouse driver patch for kernel 3.2.0-24-generic-pae. I am using this patch myself but I only just finished tinkering with it so I can't promise anything regarding reliability or whether the patch will work for other people. Hopefully it will help some people out!

1. Download the attached file to your computers desktop
2. sudo apt-get install dkms build-essential
3. cd ~/Desktop
4. tar jxvf psmouse-3.2.0-24-generic-pae.tar.bz2
5. sudo mv psmouse-3.2.0-24-generic-pae /usr/src
6. cd /usr/src
7. sudo chmod -R a+rx psmouse-3.2.0-24-generic-pae
8. sudo dkms add -m psmouse -v 3.2.0-24-generic-pae
9. sudo dkms build -m psmouse -v 3.2.0-24-generic-pae
10. sudo dkms install -m psmouse -v 3.2.0-24-generic-pae
11. sudo modprobe -r psmouse
12. sudo modprobe psmouse
13. sudo dkms status

The output of the last command should look similar to this (with no errors):
"psmouse, 3.2.0-24-generic-pae, 3.2.0-24-generic-pae, i686: installed"

No need to restart the computer as the driver is now loaded and the mouse should be working, including the hardware right button.

This worked for me right after I installed it but after a reeboot, my touchpad no longer worked at all. Using an HP dm4-1060us Ubuntu 12.04.1
Please help

---

### Post by AnotherMuggle on 2012-08-29
> **malegria said:**
> Would this also work if I am using kernel 3.2.0-29-generic-pae?

It should work...give it a go.  If it doesn't work as expected and you're landed with no mouse, or whatever, then you can just remove the module as per the instructions in post #74.

---

### Post by AnotherMuggle on 2012-08-29
> **dhizzy13 said:**
> This worked for me right after I installed it but after a reeboot, my touchpad no longer worked at all. Using an HP dm4-1060us Ubuntu 12.04.1
Please help

What is the output of this command?:
```
sudo dkms status
```

---

### Post by dhizzy13 on 2012-08-29
This is what comes up
bcmwl, 5.100.82.38+bdcom, 3.2.0-29-generic-pae, i686: installedError! Could not locate dkms.conf file.
File:  does not exist.

---

### Post by dhizzy13 on 2012-08-29
and if i try to remove it:
daniel@ubuntu:~$ sudo dkms uninstall -m psmouse -v 3.2.0-24-generic-pae
daniel@ubuntu:~$ sudo dkms remove -m psmouse -v 3.2.0-24-generic-pae --all
Error! Could not locate dkms.conf file.
File:  does not exist.

---

### Post by dhizzy13 on 2012-08-29
Is there a way to get this to work on 3.2.0-29?

---

### Post by AnotherMuggle on 2012-08-29
> **dhizzy13 said:**
> Is there a way to get this to work on 3.2.0-29?

I can't promise anything, but try repeating the entire process using this attached file and the version number 3.2.0-29 in place of the older 3.2.0-24.  All I have done is update the version numbers in the dkms.conf file.  It may help.

---

### Post by dhizzy13 on 2012-08-29
> **AnotherMuggle said:**
> I can't promise anything, but try repeating the entire process using this attached file and the version number 3.2.0-29 in place of the older 3.2.0-24.  All I have done is update the version numbers in the dkms.conf file.  It may help.

lets see if it works

what would the remove code for this be in case anything goes wrong?

---

### Post by AnotherMuggle on 2012-08-29
> **dhizzy13 said:**
> lets see if it works

what would the remove code for this be in case anything goes wrong?

Just the same as with the previous version but use 29 in place of the 24 in the previous version.

---

### Post by dhizzy13 on 2012-08-29
YES! It works so far. I will reboot again to see if it works after that. Thanks for your help.

---

### Post by dhizzy13 on 2012-08-29
Thank you very much for helping me. It works now after the reboot too. Thanks. -dhizzy13

---

### Post by HPA on 2012-08-30
@AnotherMuggle:
I tried your solution ( [http://ubuntuforums.org/showpost.php?p=11918367&postcount=18](http://ubuntuforums.org/showpost.php?p=11918367&postcount=18) ) on a Dell Inspiron Q15R N5110, which had a problem with the edge scrolling of its touchpad.
The result of the following command ```
sudo dkms status
```is (last lines) ```
psmouse, 3.2.0-24-generic-pae, 3.2.0-27-generic, x86_64: installed
psmouse, 3.2.0-24-generic-pae, 3.2.0-29-generic, x86_64: built
psmouse, 3.2.0-29-generic-pae, 3.2.0-29-generic, x86_64: installed (WARNING! Diff between built and installed module!)
psmouse-alps, 0.10, 2.6.38-11-generic, x86_64: built
```The problem with the edge scrolling was not solved, and not only this:
The middle click on the touchpad stopped working since then.
What can I do now?
Thank you in advance.

---

### Post by AnotherMuggle on 2012-08-30
> **HPA said:**
> @AnotherMuggle:
I tried your solution ( [http://ubuntuforums.org/showpost.php?p=11918367&postcount=18](http://ubuntuforums.org/showpost.php?p=11918367&postcount=18) ) on a Dell Inspiron Q15R N5110, which had a problem with the edge scrolling of its touchpad.
The result of the following command ```
sudo dkms status
```is (last lines) ```
psmouse, 3.2.0-24-generic-pae, 3.2.0-27-generic, x86_64: installed
psmouse, 3.2.0-24-generic-pae, 3.2.0-29-generic, x86_64: built
psmouse, 3.2.0-29-generic-pae, 3.2.0-29-generic, x86_64: installed (WARNING! Diff between built and installed module!)
psmouse-alps, 0.10, 2.6.38-11-generic, x86_64: built
```The problem with the edge scrolling was not solved, and not only this:
The middle click on the touchpad stopped working since then.
What can I do now?
Thank you in advance.

Your problem is almost definitely because this is a patch built from the 32bit PAE kernel source and you machine is running a 64bit kernel.

Only suggestion I have is to remove the patch by following the instructions in post #74.

EDIT: On second thought it looks like you have an alps touchpad rather than the synaptics this patch is for.

---

### Post by HPA on 2012-08-30
> **AnotherMuggle said:**
> EDIT: On second thought it looks like you have an alps touchpad rather than the synaptics this patch is for.Yes, you 're right, thank you.
I' ll remove the patch from Dell and I'll try to find (or start) a different topic concerning the problem with the edge scrolling on Dell touchpad.

A few minutes ago I tested the same solution ( [http://ubuntuforums.org/showpost.php?p=11918367&postcount=18](http://ubuntuforums.org/showpost.php?p=11918367&postcount=18) ) on my HP Probook 4520s (though it has the 64bit version of Ubuntu 12.04 installed in it).
In this HP laptop the edge scrolling, as well as the middle click don't work.
The solution didn't work here again, for some other reason.
The output on my terminal (starting from step 4, the previous steps have messages in Greek, so you won't understand them) is:```
..@..-HP:~$ tar jxvf psmouse-3.2.0-29-generic-pae.tar.bz2
psmouse-3.2.0-29-generic-pae/
psmouse-3.2.0-29-generic-pae/dk...conf
psmouse-3.2.0-29-generic-pae/src/
psmouse-3.2.0-29-generic-pae/src/alps.c
psmouse-3.2.0-29-generic-pae/src/alps.h
psmouse-3.2.0-29-generic-pae/src/amimouse.c
psmouse-3.2.0-29-generic-pae/src/appletouch.c
psmouse-3.2.0-29-generic-pae/src/atarimouse.c
psmouse-3.2.0-29-generic-pae/src/bcm5974.c
psmouse-3.2.0-29-generic-pae/src/elantech.c
psmouse-3.2.0-29-generic-pae/src/elantech.h
psmouse-3.2.0-29-generic-pae/src/gpio_mouse.c
psmouse-3.2.0-29-generic-pae/src/hgpk.c
psmouse-3.2.0-29-generic-pae/src/hgpk.h
psmouse-3.2.0-29-generic-pae/src/inport.c
psmouse-3.2.0-29-generic-pae/src/Kconfig
psmouse-3.2.0-29-generic-pae/src/lifebook.c
psmouse-3.2.0-29-generic-pae/src/lifebook.h
psmouse-3.2.0-29-generic-pae/src/logibm.c
psmouse-3.2.0-29-generic-pae/src/logips2pp.c
psmouse-3.2.0-29-generic-pae/src/logips2pp.h
psmouse-3.2.0-29-generic-pae/src/Makefile
psmouse-3.2.0-29-generic-pae/src/maplemouse.c
psmouse-3.2.0-29-generic-pae/src/pc110pad.c
psmouse-3.2.0-29-generic-pae/src/psmouse-base.c
psmouse-3.2.0-29-generic-pae/src/psmouse.h
psmouse-3.2.0-29-generic-pae/src/pxa930_trkball.c
psmouse-3.2.0-29-generic-pae/src/rpcmouse.c
psmouse-3.2.0-29-generic-pae/src/sentelic.c
psmouse-3.2.0-29-generic-pae/src/sentelic.h
psmouse-3.2.0-29-generic-pae/src/sermouse.c
psmouse-3.2.0-29-generic-pae/src/synaptics.c
psmouse-3.2.0-29-generic-pae/src/synaptics.h
psmouse-3.2.0-29-generic-pae/src/synaptics_i2c.c
psmouse-3.2.0-29-generic-pae/src/touchkit_ps2.c
psmouse-3.2.0-29-generic-pae/src/touchkit_ps2.h
psmouse-3.2.0-29-generic-pae/src/trackpoint.c
psmouse-3.2.0-29-generic-pae/src/trackpoint.h
psmouse-3.2.0-29-generic-pae/src/vsxxxaa.c
..@..-HP:~$ sudo mv psmouse-3.2.0-29-generic-pae /usr/src
..@..-HP:~$ cd /usr/src
..@..-HP:/usr/src$ sudo chmod -R a+rx psmouse-3.2.0-29-generic-pae
..@..-HP:/usr/src$ sudo dk.. add -m psmouse -v 3.2.0-29-generic-pae

Creating symlink /var/lib/dk../psmouse/3.2.0-29-generic-pae/source ->
                 /usr/src/psmouse-3.2.0-29-generic-pae

DK..: add completed.
..@..-HP:/usr/src$ sudo dk.. build -m psmouse -v 3.2.0-29-generic-pae

Kernel preparation unnecessary for this kernel.  Skipping...

Building module:
cleaning build area....
make KERNELRELEASE=3.2.0-29-generic -C /lib/modules/3.2.0-29-generic/build M=/var/lib/dk../psmouse/3.2.0-29-generic-pae/build/src psmouse.ko......
cleaning build area....

DK..: build completed.
..@..-HP:/usr/src$ sudo dk.. install -m psmouse -v 3.2.0-29-generic-pae

psmouse:
Running module version sanity check.
 - Original module
 - Installation
   - Installing to /lib/modules/3.2.0-29-generic/updates/dk../

depmod.........

DK..: install completed.
..@..-HP:/usr/src$ sudo modprobe -r psmouse
WARNING: All config files need .conf: /etc/modprobe.d/psmouse.modprobe, it will be ignored in a future release.
..@..-HP:/usr/src$ sudo modprobe psmouse
WARNING: All config files need .conf: /etc/modprobe.d/psmouse.modprobe, it will be ignored in a future release.
..@..-HP:/usr/src$ sudo dk.. status
fglrx, 8.960, 3.2.0-29-generic, x86_64: installed
psmouse, 3.2.0-29-generic-pae, 3.2.0-29-generic, x86_64: installed
..@..-HP:/usr/src$ 
```I think the problem doesn't have to do with 64 bit.
You can see here that: ```
..@..-HP:/usr/src$ sudo dk.. status
fglrx, 8.960, 3.2.0-29-generic, x86_64: installed
psmouse, 3.2.0-29-generic-pae, 3.2.0-29-generic, x86_64: installed
```, which shows that it was successfully installed.
What do you think?

---

### Post by AnotherMuggle on 2012-08-31
> **HPA said:**
> Yes, you 're right, thank you.
I' ll remove the patch from Dell and I'll try to find (or start) a different topic concerning the problem with the edge scrolling on Dell touchpad.

A few minutes ago I tested the same solution ( [http://ubuntuforums.org/showpost.php?p=11918367&postcount=18](http://ubuntuforums.org/showpost.php?p=11918367&postcount=18) ) on my HP Probook 4520s (though it has the 64bit version of Ubuntu 12.04 installed in it).
In this HP laptop the edge scrolling, as well as the middle click don't work.
The solution didn't work here again, for some other reason.
The output on my terminal (starting from step 4, the previous steps have messages in Greek, so you won't understand them) is:```
..@..-HP:~$ tar jxvf psmouse-3.2.0-29-generic-pae.tar.bz2
psmouse-3.2.0-29-generic-pae/
psmouse-3.2.0-29-generic-pae/dk...conf
psmouse-3.2.0-29-generic-pae/src/
psmouse-3.2.0-29-generic-pae/src/alps.c
psmouse-3.2.0-29-generic-pae/src/alps.h
psmouse-3.2.0-29-generic-pae/src/amimouse.c
psmouse-3.2.0-29-generic-pae/src/appletouch.c
psmouse-3.2.0-29-generic-pae/src/atarimouse.c
psmouse-3.2.0-29-generic-pae/src/bcm5974.c
psmouse-3.2.0-29-generic-pae/src/elantech.c
psmouse-3.2.0-29-generic-pae/src/elantech.h
psmouse-3.2.0-29-generic-pae/src/gpio_mouse.c
psmouse-3.2.0-29-generic-pae/src/hgpk.c
psmouse-3.2.0-29-generic-pae/src/hgpk.h
psmouse-3.2.0-29-generic-pae/src/inport.c
psmouse-3.2.0-29-generic-pae/src/Kconfig
psmouse-3.2.0-29-generic-pae/src/lifebook.c
psmouse-3.2.0-29-generic-pae/src/lifebook.h
psmouse-3.2.0-29-generic-pae/src/logibm.c
psmouse-3.2.0-29-generic-pae/src/logips2pp.c
psmouse-3.2.0-29-generic-pae/src/logips2pp.h
psmouse-3.2.0-29-generic-pae/src/Makefile
psmouse-3.2.0-29-generic-pae/src/maplemouse.c
psmouse-3.2.0-29-generic-pae/src/pc110pad.c
psmouse-3.2.0-29-generic-pae/src/psmouse-base.c
psmouse-3.2.0-29-generic-pae/src/psmouse.h
psmouse-3.2.0-29-generic-pae/src/pxa930_trkball.c
psmouse-3.2.0-29-generic-pae/src/rpcmouse.c
psmouse-3.2.0-29-generic-pae/src/sentelic.c
psmouse-3.2.0-29-generic-pae/src/sentelic.h
psmouse-3.2.0-29-generic-pae/src/sermouse.c
psmouse-3.2.0-29-generic-pae/src/synaptics.c
psmouse-3.2.0-29-generic-pae/src/synaptics.h
psmouse-3.2.0-29-generic-pae/src/synaptics_i2c.c
psmouse-3.2.0-29-generic-pae/src/touchkit_ps2.c
psmouse-3.2.0-29-generic-pae/src/touchkit_ps2.h
psmouse-3.2.0-29-generic-pae/src/trackpoint.c
psmouse-3.2.0-29-generic-pae/src/trackpoint.h
psmouse-3.2.0-29-generic-pae/src/vsxxxaa.c
..@..-HP:~$ sudo mv psmouse-3.2.0-29-generic-pae /usr/src
..@..-HP:~$ cd /usr/src
..@..-HP:/usr/src$ sudo chmod -R a+rx psmouse-3.2.0-29-generic-pae
..@..-HP:/usr/src$ sudo dk.. add -m psmouse -v 3.2.0-29-generic-pae

Creating symlink /var/lib/dk../psmouse/3.2.0-29-generic-pae/source ->
                 /usr/src/psmouse-3.2.0-29-generic-pae

DK..: add completed.
..@..-HP:/usr/src$ sudo dk.. build -m psmouse -v 3.2.0-29-generic-pae

Kernel preparation unnecessary for this kernel.  Skipping...

Building module:
cleaning build area....
make KERNELRELEASE=3.2.0-29-generic -C /lib/modules/3.2.0-29-generic/build M=/var/lib/dk../psmouse/3.2.0-29-generic-pae/build/src psmouse.ko......
cleaning build area....

DK..: build completed.
..@..-HP:/usr/src$ sudo dk.. install -m psmouse -v 3.2.0-29-generic-pae

psmouse:
Running module version sanity check.
 - Original module
 - Installation
   - Installing to /lib/modules/3.2.0-29-generic/updates/dk../

depmod.........

DK..: install completed.
..@..-HP:/usr/src$ sudo modprobe -r psmouse
WARNING: All config files need .conf: /etc/modprobe.d/psmouse.modprobe, it will be ignored in a future release.
..@..-HP:/usr/src$ sudo modprobe psmouse
WARNING: All config files need .conf: /etc/modprobe.d/psmouse.modprobe, it will be ignored in a future release.
..@..-HP:/usr/src$ sudo dk.. status
fglrx, 8.960, 3.2.0-29-generic, x86_64: installed
psmouse, 3.2.0-29-generic-pae, 3.2.0-29-generic, x86_64: installed
..@..-HP:/usr/src$ 
```I think the problem doesn't have to do with 64 bit.
You can see here that: ```
..@..-HP:/usr/src$ sudo dk.. status
fglrx, 8.960, 3.2.0-29-generic, x86_64: installed
psmouse, 3.2.0-29-generic-pae, 3.2.0-29-generic, x86_64: installed
```, which shows that it was successfully installed.
What do you think?

I don't know any facts related to the different architectures as I've never tried it myself, never compared the source and never tested how DKMS reacts in situations like that.

Personally I would only recommend this patch for the 32bit PAE kernel.

---

### Post by HPA on 2012-08-31
&#927;&#922;.
For the edge scrolling problem on my Dell laptop (Alps touchpad), the appropriate topic is this: [http://ubuntuforums.org/showthread.php?t=1904605](http://ubuntuforums.org/showthread.php?t=1904605).
I' ve posted a message there.

---

### Post by surfinnerd on 2012-09-01
Hello

Thanks !

Works fine for my HP Mini 210 1020SA

.....soooo happy to have my right click back

One thing i did experience was my netbook shutdown at the modprobe -r stage but after it rebooted I just cd'd back to /usr/src and continued to end

status came back as 'installed' so all good

Awesome-thanks again.:D

---

### Post by SimonBugs on 2012-09-01
Using the patch on a 64 bits Sony Vaio 1311, it works!

2 problems: 

- when you rest your thumb on a button (not clicking), the mousepad is not usable. In Windows this does work.
- When you click left and have your finger on the right side of the pad, it clicks right. Perhaps make a patch which only detects the button position if area is within the AreaBottomEdge ?

---

### Post by mattylee on 2012-09-07
> **AnotherMuggle said:**
> As promised I have attached my mouse driver patch for kernel 3.2.0-24-generic-pae.  I am using this patch myself but I only just finished tinkering with it so I can't promise anything regarding reliability or whether the patch will work for other people. Hopefully it will help some people out!

1. Download the attached file to your computers desktop
2. sudo apt-get install dkms build-essential
3. cd ~/Desktop
4. tar jxvf psmouse-3.2.0-24-generic-pae.tar.bz2
5. sudo mv psmouse-3.2.0-24-generic-pae /usr/src
6. cd /usr/src
7. sudo chmod -R a+rx psmouse-3.2.0-24-generic-pae
8. sudo dkms add -m psmouse -v 3.2.0-24-generic-pae
9. sudo dkms build -m psmouse -v 3.2.0-24-generic-pae
10. sudo dkms install -m psmouse -v 3.2.0-24-generic-pae
11. sudo modprobe -r psmouse
12. sudo modprobe psmouse
13. sudo dkms status

The output of the last command should look similar to this (with no errors):
"psmouse, 3.2.0-24-generic-pae, 3.2.0-24-generic-pae, i686: installed"

No need to restart the computer as the driver is now loaded and the mouse should be working, including the hardware right button.

Perfect on HP Envy14 12.04LTS! Right, Left, Middle, Drag & Drop.
Thanks!

---

### Post by eliasmohor on 2012-09-09
Thank you very much! Your patch worked great!

---

### Post by MooMinIL on 2012-09-10
> **SimonBugs said:**
> Using the patch on a 64 bits Sony Vaio 1311, it works!

2 problems: 

- when you rest your thumb on a button (not clicking), the mousepad is not usable. In Windows this does work.
- When you click left and have your finger on the right side of the pad, it clicks right. Perhaps make a patch which only detects the button position if area is within the AreaBottomEdge ? 
I second those problems.
It seems to me that the driver is programmed to rightclick whenever it detects a click and a finger on the whole of the right side of the touchpad.
I'm currently using a lenovo z380 with a synaptics touchpad that has no physical buttons except for the whole of the touchpad itself(similer to the macbook but poorer quality)
Basically what i feel that this driver needs is to seperate not only on the X Axis but also on the Y. Meaning that any click above a certain line(the virtual button line) will count as a left click.
Also while writing this comment now I noticed that there's a very fine line of a middle button click that is for some reason assigned to pasting.
I would try to work on the source myself but I've only just started the dabble in linux and have absolutely no idea how as of this moment =]
I'd love to help in any other way I can though.

---

### Post by MooMinIL on 2012-09-10
> **manumann said:**
> [http://sehajmann.com/hd-dvd-and-blu-ray/](http://sehajmann.com/hd-dvd-and-blu-ray/)
lts Hp touchpad right click problem
Ehm, what?

---

### Post by AnotherMuggle on 2012-09-14
> **MooMinIL said:**
> I second those problems.
It seems to me that the driver is programmed to rightclick whenever it detects a click and a finger on the whole of the right side of the touchpad.
I'm currently using a lenovo z380 with a synaptics touchpad that has no physical buttons except for the whole of the touchpad itself(similer to the macbook but poorer quality)
Basically what i feel that this driver needs is to seperate not only on the X Axis but also on the Y. Meaning that any click above a certain line(the virtual button line) will count as a left click.
Also while writing this comment now I noticed that there's a very fine line of a middle button click that is for some reason assigned to pasting.
I would try to work on the source myself but I've only just started the dabble in linux and have absolutely no idea how as of this moment =]
I'd love to help in any other way I can though.

There are loads of possibilities for tweaks and changes but for me the right click is usable now.  Anyone who is interested in modifying the source is free to do so as all relevant files are included in the .tar.bz2 file.

It might be worth noting that the right click works for me without needing a patch on a bang up-to-date Debian Sid system.  Hopefully there will be no need to make any changes with upcoming kernel releases.

---

### Post by AnotherMuggle on 2012-09-18
This post is to draw everything into once place.  Partly to help people looking for this patch and partly so I can keep better track myself lol.

I have attached all the patch files that I have done for Ubuntu 12.04 to this post and will remove from elsewhere a link here (I think I can do that).  All these patches are the same, the only difference is the version number, so that it doesn't cause any problems when installing against a different kernel version.

Once the patch is installed it can be left alone, no need to do anything when you get a kernel installed as it is updated automatically.

I have been using this patch myself and have had no issues with it.  Many people have contacted me or posted on this thread confirming it works on other laptops but it was put together specifically for the HP Mini 210...you may find success on other laptops too :D

When using the commands below replace <VERSION> with the relevant version number you are trying to installed, for example for version 3.2.0-24, use psmouse-3.2.0-24-generic-pae

```
To install the patch:

1. Download the attached file to your computers desktop
2. sudo apt-get install dkms build-essential
3. cd ~/Desktop
4. tar jxvf psmouse-<VERSION>-generic-pae.tar.bz2
5. sudo mv psmouse-<VERSION>-generic-pae /usr/src
6. cd /usr/src
7. sudo chmod -R a+rx psmouse-<VERSION>-generic-pae
8. sudo dkms add -m psmouse -v <VERSION>-generic-pae
9. sudo dkms build -m psmouse -v <VERSION>-generic-pae
10. sudo dkms install -m psmouse -v <VERSION>-generic-pae
11. sudo modprobe -r psmouse
12. sudo modprobe psmouse
13. sudo dkms status
```

The output of the last command should look similar to this (with no errors):
```
"psmouse, 3.2.0-24-generic-pae, 3.2.0-24-generic-pae, i686: installed"
```

No need to restart the computer as the driver is now loaded and the mouse should be working, including the hardware right button.

```
To uninstall the patch:

1. sudo dkms uninstall -m psmouse -v <VERSION>-generic-pae
2. sudo dkms remove -m psmouse -v <VERSION>-generic-pae --all
```

---

### Post by Solzhenitsyn1 on 2012-09-24
HP mini, running xubuntu - 3.2.0-31-generic (i686)

works perfectly, thanks very much.

---

### Post by tru23 on 2012-09-29
HP Envy 14, Linux Mint 13 - kernel version 3.2.0-23

Works like a charm, thank you very much.8)

---

### Post by l4c on 2012-10-03
Anything for kernel 3.2.0-31?

Thank you

---

### Post by AnotherMuggle on 2012-10-03
> **l4c said:**
> Anything for kernel 3.2.0-31?

Thank you

Here :D

Follow the instructions in post #124 of this thread.

---

### Post by l4c on 2012-10-06
Thank you for your reply, unfortunately it didn't work for my ASUS K55VM-SX083VF laptop.

Thanks anyway :)

---

### Post by pheonone on 2012-10-11
HP Probook 4520s, Ubuntu  12.04.1 with kernel 3.2.0-31
Works perfectly, thank you very much ;)

UPDATE: after kernel update to 3.2.0-32 still works perfectly

---

### Post by asifejaz on 2012-10-16
> **AnotherMuggle said:**
> This post is to draw everything into once place.  Partly to help people looking for this patch and partly so I can keep better track myself lol.

I have attached all the patch files that I have done for Ubuntu 12.04 to this post and will remove from elsewhere a link here (I think I can do that).  All these patches are the same, the only difference is the version number, so that it doesn't cause any problems when installing against a different kernel version.

Once the patch is installed it can be left alone, no need to do anything when you get a kernel installed as it is updated automatically.

I have been using this patch myself and have had no issues with it.  Many people have contacted me or posted on this thread confirming it works on other laptops but it was put together specifically for the HP Mini 210...you may find success on other laptops too :D

When using the commands below replace <VERSION> with the relevant version number you are trying to installed, for example for version 3.2.0-24, use psmouse-3.2.0-24-generic-pae

```
To install the patch:

1. Download the attached file to your computers desktop
2. sudo apt-get install dkms build-essential
3. cd ~/Desktop
4. tar jxvf psmouse-<VERSION>-generic-pae.tar.bz2
5. sudo mv psmouse-<VERSION>-generic-pae /usr/src
6. cd /usr/src
7. sudo chmod -R a+rx psmouse-<VERSION>-generic-pae
8. sudo dkms add -m psmouse -v <VERSION>-generic-pae
9. sudo dkms build -m psmouse -v <VERSION>-generic-pae
10. sudo dkms install -m psmouse -v <VERSION>-generic-pae
11. sudo modprobe -r psmouse
12. sudo modprobe psmouse
13. sudo dkms status
```The output of the last command should look similar to this (with no errors):
```
"psmouse, 3.2.0-24-generic-pae, 3.2.0-24-generic-pae, i686: installed"
```No need to restart the computer as the driver is now loaded and the mouse should be working, including the hardware right button.

```
To uninstall the patch:

1. sudo dkms uninstall -m psmouse -v <VERSION>-generic-pae
2. sudo dkms remove -m psmouse -v <VERSION>-generic-pae --all
```


this method works like a charm.. thumbs up

---

### Post by avermaa on 2012-10-18
Hi,

I am new to this forum and Ubuntu as well. Having the same right cick problem, but I cant see the 'attached file' to downlaod???

---

### Post by AnotherMuggle on 2012-10-18
> **avermaa said:**
> Hi,

I am new to this forum and Ubuntu as well. Having the same right cick problem, but I cant see the 'attached file' to downlaod???

Everything you need is in post #124 of this thread.

Good luck :D

---

### Post by avermaa on 2012-10-18
> **AnotherMuggle said:**
> Everything you need is in post #124 of this thread.

Good luck :D

Thanks a ton - I was looking at an older post. It works fine...

---

### Post by fgiava on 2012-10-27
Thank you very much, after two years my HP ProBook 4320 touchpad works with gesture and right click both!
 

 I applied the patch version  psmouse-3.2.0-30-generic-pae to the kernel 3.2.0-32-generic-pae (Ubuntu12.04) . All seems to be ok.
 

 I have noticed that on Ubuntu 12.10 this touchpad problem it is already solved.

---

### Post by fgiava on 2012-10-27
Thank you very much, after two years my HP ProBook 4320 touchpad works with gesture and right click both.
 

 I applied the patch version  psmouse-3.2.0-30-generic-pae to the kernel 3.2.0-32-generic-pae (Ubuntu12.04).  All seems to be ok.
 

 I have noticed that on Ubuntu 12.10 this touchpad problem it is already solved.

---

### Post by AnotherMuggle on 2012-10-27
> **fgiava said:**
> I have noticed that on Ubuntu 12.10 this touchpad problem it is already solved.

I was pleased to discover this too.  12.10 works very nicely on my Mini :)

---

### Post by aliuntu on 2012-10-28
trouble with "right clicking" on new asus i5 core, 6Gb ram 720 Gb HD, doesnt respond to right clicking, btw, got rid of the dell latitude e6420 wasnt worth the headaches.. will try a few more thing in the settings just to make sure that im doin everything correctly, i hvae upgraded to 12.04 LTS... yeah baby!! now we're going places..

---

### Post by AnotherMuggle on 2012-11-12
[QUOTE=ntzrmtthihu777]
HP dv5 click pad patch.
I don't suppose a 64-bit version of this patch is available, or you could tell me how to make it compatible?
[/QUOTE]

I've never looked at the source for the 64bit kernel.  It may be just the same, it may be very different, I've honestly no idea, sorry.

Also the patch is for a HP Mini, not a DV5, but it may work on that model.

You may be interested to know the clickpad works perfectly with Ubuntu 12.10 with no need for a patch.

---

### Post by irvingvladimir on 2012-12-12
I have the same problem but touching anywhere with two fingers opened the right click menu on my acer aspire v5-171 with ubuntu 12.04.

---

### Post by chrismack88 on 2012-12-13
Works excellently HP Probook 4525s :)

---

### Post by lipu123 on 2012-12-18
> **AnotherMuggle said:**
> Here :D

Follow the instructions in post #124 of this thread.

What about 3.2.0-35-generic-pae????

I tried with the psmouse-3.2.0-30 but after giving this "sudo modprobe -r psmouse"
my touchpad don't work any more.

My laptop is Lenovo S400

---

### Post by Lazorne on 2012-12-18
Thank you the psmouse-3.2.0-30 worked like a charm on my HP DV6-3163! 

One of my two major gripes are gone, thanks for that:KS:KS:KS

...Now if only my Radeon HD 5xxx Series/Intel hybrid would work as well.. Some day maybe.

---

### Post by synace on 2012-12-22
Does this prevent the cursor from moving if touching the 'button' areas of the click pad?

I'd like left/middle/right click to work in the designated bottom area of my clickpad, but I don't want cursor movement to work.

Normally, if I use  AreaButtonEdge, it disables touch sensitivity altogether (good because they cursor won't move), but it also kills it's ability to detect 'where' my finger is, thereby killing the right-click area (as such, it registers as left click).

I think a small patch to modify 'AreaBottomEdge' so that it only applies to cursor movement would be the goal. Is that what this patch does?

Have not tried patch yet Sony Vaio Z1311 3.6.9 kernel.

Thanks in advance!

---

### Post by Shaddan on 2012-12-24
Hi,
I was using this patch and it worked very well for me, but after formatting and trying to reinstall everything I can't find the patch anymore for download.
Would anyone have a link for it.
Thanks.

---

### Post by AnotherMuggle on 2012-12-30
> **Shaddan said:**
> Hi,
I was using this patch and it worked very well for me, but after formatting and trying to reinstall everything I can't find the patch anymore for download.
Would anyone have a link for it.
Thanks.

Post #124 of this thread mate.

---

### Post by AnotherMuggle on 2012-12-30
> **synace said:**
> Does this prevent the cursor from moving if touching the 'button' areas of the click pad?

I'd like left/middle/right click to work in the designated bottom area of my clickpad, but I don't want cursor movement to work.

Normally, if I use  AreaButtonEdge, it disables touch sensitivity altogether (good because they cursor won't move), but it also kills it's ability to detect 'where' my finger is, thereby killing the right-click area (as such, it registers as left click).

I think a small patch to modify 'AreaBottomEdge' so that it only applies to cursor movement would be the goal. Is that what this patch does?

Have not tried patch yet Sony Vaio Z1311 3.6.9 kernel.

Thanks in advance!

Kind of, but no. Follow the steps in post #124 of this thread to test and remove if it doesn't work as you hoped.

---

### Post by AnotherMuggle on 2012-12-30
> **lipu123 said:**
> What about 3.2.0-35-generic-pae????

I tried with the psmouse-3.2.0-30 but after giving this "sudo modprobe -r psmouse"
my touchpad don't work any more.

My laptop is Lenovo S400

That's fine. That command removes the old driver, so the touchpad will stop working. You need to finish all the steps to reload the new patched driver.

---

### Post by rclai89 on 2013-01-08
I used:

[psmouse-3.2.0-30-generic-pae.tar.bz2]("http://ubuntuforums.org/attachment.php?attachmentid=224326&d=1347990559")

Worked on my HP DV7-T CTO-4000 with my 12.04 LTS 3.2.0-35-generic installation. Thanks a lot AnotherMuggle for the instructions for installation AND uninstallation.

=D>

---

### Post by tux-world on 2013-01-12
hi all which link i can download ubuntu-12.04 for HP TP?

---

### Post by Javi80 on 2013-01-20
HP Spectre XT on 12.04

Works, thanks!

---

### Post by hVolo17 on 2013-02-02
> **VideoRoy said:**
> After searching I found one useful tip to reenable the right click but even with that 12.04 is a major step backward from where I was with the patched driver.

Here is what I did:

1. Create _**51-clickpad.conf**_ in _**/etc/X11/xorg.conf.d**_ directory.  Note that xorg.conf.d directory did not exist for me on 12.04 as it did in previous versions so I had to make the directory.
2. Put the following lines in_** 51-clickpad.conf**_

3. Logout / Login for changes to take effect.

The SoftButtonAreas fixes the right click.  The BottomEdge items mask off the bottom of the clickpad so the button will not act like the rest of the clickpad when dragging your finger on it.

I had to add LockedDrags which I hate, because I can no longer left click with my thumb and drag with pointer finger.  The sensitivity is all messed up so locked drags is my only solution if I stay with Ubuntu.  I keep threating to change to SUSE but I like all the rest of Ubuntu better.  The hardware support for Netbooks and laptops with clickpads has been bad for years now.

You are awesome! I've been struggling to get my right click to work and this solves the problem for a HP dm1-3020us. If imaginary internet money exists you can have all of mine.

---

### Post by TuxCrafter on 2013-02-04
System: HP ProBook 4520s WD842EA

I used to have the /etc/X11/xorg.conf.d/51.clickpad.conf with the Option "SoftButtonAreas" "50% 0 82% 0 0 0 0 0" lines, this gave the right button functionality but you still cant use two hands at the same time on the touchpad and sometimes the cursor just jumps to an other part of the screen.

Followed the steps at post #124
Linux arie-laptop 3.2.0-37-generic #58-Ubuntu SMP Thu Jan 24 15:28:57 UTC 2013 i686 i686 i386 GNU/Linux
psmouse, 3.2.0-30-generic-pae, 3.2.0-37-generic, i686: installed

I still got the same problem, the cursor can jump to an other part of the screen. Also the touch-pad still responses in areas of the mouse buttons you cant use your left hand to press the left button and use your right hand to make an selection and drag the items around.

I hopped the 3.5.0 kernel would fix this but there the right mouse button didn't even work.... I met somebody with a Asus Zenbook that has an similar touch-pad (from the outside) and with the 3.5.0 kernel it worked fine, with two hands and buttons.

So the behaviour of the touch-pad is really unstable (jumping) during production work.

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1095169](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1095169)

---

### Post by babadonz on 2013-03-01
> **AnotherMuggle said:**
> As promised I have attached my mouse driver patch for kernel 3.2.0-24-generic-pae.  I am using this patch myself but I only just finished tinkering with it so I can't promise anything regarding reliability or whether the patch will work for other people. Hopefully it will help some people out!

1. Download the attached file to your computers desktop
2. sudo apt-get install dkms build-essential
3. cd ~/Desktop
4. tar jxvf psmouse-3.2.0-24-generic-pae.tar.bz2
5. sudo mv psmouse-3.2.0-24-generic-pae /usr/src
6. cd /usr/src
7. sudo chmod -R a+rx psmouse-3.2.0-24-generic-pae
8. sudo dkms add -m psmouse -v 3.2.0-24-generic-pae
9. sudo dkms build -m psmouse -v 3.2.0-24-generic-pae
10. sudo dkms install -m psmouse -v 3.2.0-24-generic-pae
11. sudo modprobe -r psmouse
12. sudo modprobe psmouse
13. sudo dkms status

The output of the last command should look similar to this (with no errors):
"psmouse, 3.2.0-24-generic-pae, 3.2.0-24-generic-pae, i686: installed"

No need to restart the computer as the driver is now loaded and the mouse should be working, including the hardware right button.

Dear Friends,

How can I obtain the attached files here?
Nothing shown here.

Thanks.

---

### Post by AnotherMuggle on 2013-03-02
> **babadonz said:**
> Dear Friends,

How can I obtain the attached files here?
Nothing shown here.

Thanks.

Post #124 of this thread.

Also the touchpad is perfect out of the box with 12.10. I recently switched to Xubuntu Because the performance is so much better on the low powered HP Mini.

---

### Post by sepulphuric on 2013-03-03
Haha wow I had no idea there was even a problem with my touchpad until I came across this post, and that's that I've been running ubuntu for about a month now! O.O
Install was super easy, I copied and pasted the whole way through!

You truly are a superstar AnotherMuggle! 
Thank you so much. :)

---

### Post by aj.pai.r on 2013-03-04
Post #131 worked for me. Using HP Envy Spectre 14 3210NR.

Thanks a ton!

---

### Post by IamNotANerd on 2013-03-06
I'm on HP Envy Spectre 14 and followed #124 and it worked. Thank you!!

---

### Post by dheuma on 2013-03-11
HP ProBook 4520s
Ubuntu 12.04 x64
Kernel 3.2.0-38-generic

Post #124
clear and very simple "howto"
works perfectly, thanks very much mate :)

---

### Post by cheguiva on 2013-04-27
Hello, 
I have a big problem with my touchpad with my HP laptop. 
I would like to test your patch but I did not find it. 
COuld you help me. 
Thanks. 
K H.

---

### Post by amitsaxena on 2013-05-24
Post #124 works for HP ProBook 4420s.

Thanks!!!

---

### Post by amisiek on 2013-06-30
Is there such a patch for 3.5.0-34-generic #55~precise1-Ubuntu SMP on x86_64?

---

### Post by astra-i on 2013-10-05
would you please tell me how to view the attached file?

---

### Post by astra-i on 2013-10-05
> **AnotherMuggle said:**
> As promised I have attached my mouse driver patch for kernel 3.2.0-24-generic-pae.  I am using this patch myself but I only just finished tinkering with it so I can't promise anything regarding reliability or whether the patch will work for other people. Hopefully it will help some people out!

1. Download the attached file to your computers desktop
2. sudo apt-get install dkms build-essential
3. cd ~/Desktop
4. tar jxvf psmouse-3.2.0-24-generic-pae.tar.bz2
5. sudo mv psmouse-3.2.0-24-generic-pae /usr/src
6. cd /usr/src
7. sudo chmod -R a+rx psmouse-3.2.0-24-generic-pae
8. sudo dkms add -m psmouse -v 3.2.0-24-generic-pae
9. sudo dkms build -m psmouse -v 3.2.0-24-generic-pae
10. sudo dkms install -m psmouse -v 3.2.0-24-generic-pae
11. sudo modprobe -r psmouse
12. sudo modprobe psmouse
13. sudo dkms status

The output of the last command should look similar to this (with no errors):
"psmouse, 3.2.0-24-generic-pae, 3.2.0-24-generic-pae, i686: installed"

No need to restart the computer as the driver is now loaded and the mouse should be working, including the hardware right button.
I mean this attached file!

---

### Post by kantor-d on 2013-12-29
Would it be possible to create a patch for kernel: 3.8.0-34 THANK YOU!

---

### Post by thomasmcdowal on 2014-03-06
See post #124 - I just followed the instructions not five minutes ago and it worked a charm!

Many thanks for this

---

### Post by mosu90 on 2014-03-17
Does patch from #124 enable Left Top led ?

I am on a HP ProBook 4540s, i want to be able to disable the touchpad using left top button.

Thanks and if anybody tried please let me know how it's working.

---

### Post by egsenah2 on 2014-07-09
what file should I use for elementary OS Luna?

EDIT:
I made it with -29-generic-pae, worked like a charm. THANKS!

---

