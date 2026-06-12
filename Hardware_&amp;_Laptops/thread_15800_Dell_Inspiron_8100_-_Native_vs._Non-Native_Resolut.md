---
title: "Dell Inspiron 8100 - Native vs. Non-Native Resolution"
date: 2005-02-16
forum: Hardware &amp; Laptops
---

### Post by TheAngryPenguin on 2005-02-16
I've just discovered Ubuntu (thanks to [ShellCity](http://shellcity.net/)) and scholpped it unto my 8100.  Whenever I switch to a non-native resolution (eg. anything *other* than 1600X1200), there's a black border around the entire viewable area.  IOW, the lower resolutions don't seem to stretch out to fill up the entire display.  I've installed the nVidia driver (with help from the fine [Unofficial Ubuntu 4.10 Starter Guide](http://ubuntuguide.org/index.html#installnvidiadriver)), and it doesn't seem to help.  Changing from 'nv' to 'nvidia' causes X to fail upon startup, so I have a feeling that this particular driver doesn't support the GeForce2Go integrated into this laptop.  So, is there any possible way to stretch non-native resolutions to full screen.  Mine eyes have much difficulty with such small text (although it *does* look pretty damn awesome -- wish I had better eyes)...

---

### Post by CyrilleMortreux on 2005-02-17
[QUOTE=TheAngryPenguin]I've just discovered Ubuntu (thanks to [ShellCity](http://shellcity.net/)) and scholpped it unto my 8100.  Whenever I switch to a non-native resolution (eg. anything *other* than 1600X1200), there's a black border around the entire viewable area.  IOW, the lower resolutions don't seem to stretch out to fill up the entire display.  I've installed the nVidia driver (with help from the fine [Unofficial Ubuntu 4.10 Starter Guide](http://ubuntuguide.org/index.html#installnvidiadriver)), and it doesn't seem to help.  Changing from 'nv' to 'nvidia' causes X to fail upon startup, so I have a feeling that this particular driver doesn't support the GeForce2Go integrated into this laptop.  So, is there any possible way to stretch non-native resolutions to full screen.  Mine eyes have much difficulty with such small text (although it *does* look pretty damn awesome -- wish I had better eyes)...[/QUOTE]


I also have a Dell Latitude with the same screen resolution : 
I have tried with Ubuntu, Debian, Slackware, but none can give me something nice to use if it's not in 1600x1200, and I don't think the Nvidia driver may help you. (I use it too).

To install the nvidia driver, you should try that : 

apt-get install nvidia-glx linux-restricted-modules-your_kernel

That's a Dell "technology", whatever your distro is, you ll have to use this settings.

---

### Post by TheAngryPenguin on 2005-02-17
[QUOTE=CyrilleMortreux]To install the nvidia driver, you should try that : 

apt-get install nvidia-glx linux-restricted-modules-your_kernel[/quote]
Thanks for the reply.  Will the above method of installing the nVidia driver actually load anything different than the method described at ubuntuguide.org?

[QUOTE=CyrilleMortreux]That's a Dell "technology", whatever your distro is, you ll have to use this settings.[/QUOTE]
Not sure what you mean here.  Even when using the official nVidia driver (vs. Dell's) on Win32, I can still have a full screen at other resolutions than 1600x1200.  IIRC, there has been at least one Live CD-based distro that I've tried in the past that did full screen at 1024x768 (eg. without the black borders) -- which distro it was escapes me.

---

### Post by CyrilleMortreux on 2005-02-18
[QUOTE=TheAngryPenguin]Thanks for the reply.  Will the above method of installing the nVidia driver actually load anything different than the method described at ubuntuguide.org?[/QUOTE]

Not at all, these are two ways to obtain the same thing. I have not read before this part of the ubuntu guide...

> 
Not sure what you mean here.  Even when using the official nVidia driver (vs. Dell's) on Win32, I can still have a full screen at other resolutions than 1600x1200.  IIRC, there has been at least one Live CD-based distro that I've tried in the past that did full screen at 1024x768 (eg. without the black borders) -- which distro it was escapes me.

Well, you are right, and I used to have full screen to at other resolutions too, but it was not perfect and my screen was too much bright.
I mean the 1600x1200 is a not "logical" but technical and hardware limitation and, even if it was working with Knoppix, screen was not as clean as I wanted it to be. 

My laptop runs Slackware by now, (xorg, nvidia drivers and 1600x1200...)  but I going to install Ubuntu on a second hard drive to have a look at that.

---

### Post by TheAngryPenguin on 2005-02-18
[QUOTE=CyrilleMortreux]Not at all, these are two ways to obtain the same thing. I have not read before this part of the ubuntu guide...[/QUOTE]
This is good to know.  As I mentioned in my OP, after I installed the nVidia driver, I realized that it probably wasn't the *correct* driver, for when I configured X to used 'nvndia' (as opposed to its deafult selection of 'nv'), X refused to start.  So, I am not 100% sure, but I don't think that the driver I installed was written for the Geforce2Go.

[QUOTE=CyrilleMortreux]Well, you are right, and I used to have full screen to at other resolutions too, but it was not perfect and my screen was too much bright.
I mean the 1600x1200 is a not "logical" but technical and hardware limitation and, even if it was working with Knoppix, screen was not as clean as I wanted it to be.[/QUOTE]
Ah!  I understand what you mean now.  I realize that running an LCD in something other than its 'native' resolution will distort the image in one way or an other.  It's just that 1600X1200 on a 15" screen is a little too high for my eye's taste, even though it look awesomely good.

[QUOTE=CyrilleMortreux]My laptop runs Slackware by now, (xorg, nvidia drivers and 1600x1200...)  but I going to install Ubuntu on a second hard drive to have a look at that.[/QUOTE]
I'm in the same boat in that I have an extra HD that I am looking for a non-Windows home for.  I am utterly impressed with Ubuntu thus far, but I am open to other recommendations.  Maybe I should give Slackware a shot.  Or I could try bringing my current Ubuntu install up to the current beta.  Sorry -- just thinking aloud...

---

### Post by CyrilleMortreux on 2005-02-18
[QUOTE=TheAngryPenguin]
I'm in the same boat in that I have an extra HD that I am looking for a non-Windows home for.  I am utterly impressed with Ubuntu thus far, but I am open to other recommendations.  Maybe I should give Slackware a shot.  Or I could try bringing my current Ubuntu install up to the current beta.  Sorry -- just thinking aloud...[/QUOTE]

1- I am running Slackware for years now, I my laptop is the only computer still with that distro. I am wainting for a stable Hoary maybe to change. 

2- I am also running Hoary for monthes now, with my main computer. You may be carefull because it's a development base, and I have been blocked some times to times by bugs. 
I am french, and since one week, due to a Gnome update, I improve my english ;) No way to get him in my native language !!!

Once, I have lost all the mime types for one week, It was garbage  :-D 

So far, it works fine in the end .

---

### Post by ollietc on 2005-02-18
Howdy, Inspiron 8100 with Ubuntu Warty user. Had the same issues as you and can provide some light in the matter.

1. For your error when trying to start X with the 'nvidia' driver. The problem is that the module is not getting loaded on boot. To resolve this, edit /etc/modules and put nvidia at the end of the file. Reboot and try to start X with the nvidia driver. You can also use 'modprobe nvidia' if you don't want to reboot but remember to still edit the /etc/modules file for future boots.

2. For your black border around the screen. I was stumped by this for a long time until dumb luck solved it. To resolve it, do a FN+F7(Font) option on your keyboard. You may have to do it twice to toggle it on and off. This will stretch your screen.

Hope this helps...

---

### Post by CyrilleMortreux on 2005-02-18
[QUOTE=ollietc]Howdy, Inspiron 8100 with Ubuntu Warty user. Had the same issues as you and can provide some light in the matter.

1. For your error when trying to start X with the 'nvidia' driver. The problem is that the module is not getting loaded on boot. To resolve this, edit /etc/modules and put nvidia at the end of the file. Reboot and try to start X with the nvidia driver. You can also use 'modprobe nvidia' if you don't want to reboot but remember to still edit the /etc/modules file for future boots.[/QUOTE]

Yeh, I remember I used to have the same thing. I forgot this one.

---

### Post by TheAngryPenguin on 2005-02-27
Jeez -- Thanks so much.  I am fully aware of FN+F7, but since there were no borders at boot, I didn't even think to give it a try.

Now, on to the nvidia driver -- and I am sure that the only way to really find this out is to give it a try, but would using the 'nvidia' driver vs. the default 'nv' one provide any absolute advantage?

Thanks again for the reminder.  I can now use Ubuntu more often, and actually not strain mine eyes whist doing so!

*Edit:*

Okay -- I got the nvidia driver up and running.  Seems to make a difference -- the weird pixel noise, for lack of a better term, has disappeared from the left side of the display.  However, it seems that 1024x768 and 1600x1200 are the only resolutions that offer true color -- anything else looks as if only 256 colors are being displayed.  And 10x7 on Ubuntu looks so much larger than 10x7 on XP.  How can I increase the color depth for the resolutions in between 10x7 and 16x12?

---

### Post by leo2 on 2006-03-21
I have ubuntu 5.10 on my dell inspiron 8100.
nv is working, but the caracters are too small and it doesn't work with a videoprojector. So I tried to install a nvidia driver, but I failed.

I have read many messages on ubuntu forums, and tested many methods (howto Nvidia drivers)
- NVIIDIA-Linux...(many versions: 4363, 7174, 7667, 8178)
- nvidia-glx
- nvidia-glx-legacy
- gcc3.4, 
/etc/X11/xorg.conf  #load "dri" #load "GLcore#     load "glx"   driver "nvidia"
- apt-get install nvidia-glx'-legacy) .... nvidia-sett.., restrict-mod-nvidia-leg..
...
for each method, installations and compilations are OK 
but when i reboot or restart xwin, nvidia doesn't work
 I got at the last moment a black screen)
I have to comeback with nv to get xwindow....

Have you any clue?
If somebody have succeded with nvidia - ubuntu 5.10 on a dell inspiron 8100,
may i have the sequence of the instructions?

thanks a lot   Leo   
---------------------------------------------------------
DELL INSPIRON 8100
Linux dell 2.6.12-10-386 #1 Sat Mar 11 16:13:17 UTC 2006 i686 GNU/Linux
processor: Intel(R) Pentium(R) III Mobile CPU       866MHz
0000:01:00.0 VGA compatible controller: nVidia Corporation NV11 [GeForce2 Go] (rev b2)
---------------------------------------------------------

---

### Post by ledonnell on 2006-04-11
I get this same issue with my 8100.
I also get this with my desktop with ANY nvidia card once I follow a how-to install 3D drivers.
It would be great to get this beat!](*,) 


[QUOTE=leo2]I have ubuntu 5.10 on my dell inspiron 8100.
nv is working, but the caracters are too small and it doesn't work with a videoprojector. So I tried to install a nvidia driver, but I failed.

I have read many messages on ubuntu forums, and tested many methods (howto Nvidia drivers)
- NVIIDIA-Linux...(many versions: 4363, 7174, 7667, 8178)
- nvidia-glx
- nvidia-glx-legacy
- gcc3.4, 
/etc/X11/xorg.conf  #load "dri" #load "GLcore#     load "glx"   driver "nvidia"
- apt-get install nvidia-glx'-legacy) .... nvidia-sett.., restrict-mod-nvidia-leg..
...
for each method, installations and compilations are OK 
but when i reboot or restart xwin, nvidia doesn't work
 I got at the last moment a black screen)
I have to comeback with nv to get xwindow....

Have you any clue?
If somebody have succeded with nvidia - ubuntu 5.10 on a dell inspiron 8100,
may i have the sequence of the instructions?

thanks a lot   Leo   
---------------------------------------------------------
DELL INSPIRON 8100
Linux dell 2.6.12-10-386 #1 Sat Mar 11 16:13:17 UTC 2006 i686 GNU/Linux
processor: Intel(R) Pentium(R) III Mobile CPU       866MHz
0000:01:00.0 VGA compatible controller: nVidia Corporation NV11 [GeForce2 Go] (rev b2)
---------------------------------------------------------[/QUOTE]

---

### Post by g00n on 2006-06-18
as i type this on my inspiron 8100.. and have run into the thick black border.

It's not really  driver issue.. it's a "feature".. 

once you have the black border.. usually a couple inches wide.. 
fn-f7 once or twice.. it might not register the first time.. 

but it'll make that little 1024x768 (or whatever you want) window in the middle and stretch it to the whole screen.. with an actual 1024x768 resolution.

give it a shot.

---

