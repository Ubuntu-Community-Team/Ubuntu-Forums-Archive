---
title: "[SOLVED] screen flickering"
date: 2008-11-13
forum: Hardware
---

### Post by JunCTionS on 2008-11-13
Hi, I seem to have an issue with the way my screen was automatically configured with a clean install of Kubuntu 8.10.
The computer is a Toshiba Satellite M55-S135, it's specified to have an "Intel Graphics Media Accelerator 900"
By sugestion of aquaman420 I looked at the X.org log, and although there are no warnings I saw that each time the screen flickers it adds these four lines:

```
(II) intel(0): EDID vendor "SEC", prod id 22082
(II) intel(0): EDID vendor "SEC", prod id 22082
(II) intel(0): Printing DDC gathered Modelines:
(II) intel(0): Modeline "1280x768"x0.0   68.93  1280 1296 1344 1408  768 771 777 816 -hsync -vsync (49.0 kHz)

```

I imagine it might have something to do with a badly configured refresh rate (it used to have a lower resolution, but this has been fixed, 1280x768 is the native resolution of this computer). I don't know how to fix this, the Xorg.conf now carries a lot less information (it only points to "Configured monitor").

Any suggestions? maybe a tutorial on how to tinker with the xorg without having to reboot for each try?. Maybe something like if I was just changing the resolution with the "System Settings" programs (which by the way gives me a very small set of choices).

I come from [this thread]("http://ubuntuforums.org/showthread.php?t=971486") but I'm not sure the first poster there has the same issue.

---

### Post by Niscrome on 2008-11-13
Dude I am having the same problem too. I have wubi 8.10 installed. I believe I have the same graphics card as you. 

Right now I search the forum for a solution. If I find one, I'll relay it here. Hopefully someone can help.

---

### Post by Niscrome on 2008-11-21
Hey I finally found a solution. 
1) Click on the K menu
2) Go to the Applications tab
3) Click on the System menu followed by System Settings
4) In the System Settings window, click on the Advanced tab
5) Click on the Service Manager
6) In the Startup Services list, select the service named, "[COLOR="Red"]Detecting RANDR (monitor) changes[/COLOR]" so that it's highlighted
7) Click the [COLOR="Red"]Stop[/COLOR] button to stop the service, then _click the checkbox to clear it_ (so it doesn't start up anymore)
8) Click the [COLOR="Red"]Apply[/COLOR] button

Source:
[HTML]http://blog.turbulentsky.com/2008/11/kubuntu-810-video-flashing-flickering.html[/HTML]

It solved the problem for me.

---

### Post by JunCTionS on 2008-11-21
Oh thanks, I didn't have much time to find a solution so I tried switching to an older version of Kubuntu and by mistake ended up switching to Ubuntu :P.
Anyways, I was just demonstrating the liveCD on the same computer, and it works! :)
Thanks!

---

### Post by Niscrome on 2008-11-24
No problem! I honestly switched back to my first love; Gnome!

---

### Post by mariosx on 2008-12-02
> **Niscrome said:**
> Hey I finally found a solution. 
1) Click on the K menu
2) Go to the Applications tab
3) Click on the System menu followed by System Settings
4) In the System Settings window, click on the Advanced tab
5) Click on the Service Manager
6) In the Startup Services list, select the service named, "[COLOR="Red"]Detecting RANDR (monitor) changes[/COLOR]" so that it's highlighted
7) Click the [COLOR="Red"]Stop[/COLOR] button to stop the service, then _click the checkbox to clear it_ (so it doesn't start up anymore)
8) Click the [COLOR="Red"]Apply[/COLOR] button

Source:
[HTML]http://blog.turbulentsky.com/2008/11/kubuntu-810-video-flashing-flickering.html[/HTML]

It solved the problem for me.

a big thank you from Greece :)

---

### Post by INsaneJuly on 2008-12-18
Thank you very much!  It solved my problem too, and I am on a Dell Inspirion 6000.

---

### Post by Philo1 on 2009-01-04
Thanks from here as well, I was having the same issue. This is my first round with KDE.

---

### Post by gaiaap on 2009-04-03
Solved the same problem on Kubuntu 8.10 with an ATI X800 XT and Samsung SM 957p monitor as well. Cheers!

---

### Post by emoXodus on 2009-04-07
ty soooooooooooooooo much

---

### Post by dgray_from_dc on 2009-04-10
This solution worked for me as well on a Dell Latitude D620 With a D/Dock.  However, I've now lost the ability to hot-dock my laptop.  Even when I turn the service back on, it sometimes freezes the computer.  I'm thinking that I'll probably have to wait for KDE to fix the RANDR service.  Anyone have any ideas?

---

### Post by andy17 on 2009-05-14
I got the same problem, but on Jaunty I can't find the menu you described... How can I do???

---

### Post by awthomp on 2009-06-13
This solution does not work for KDE 4.2, unfortunately.

---

### Post by chb on 2009-06-22
Don't know if this is useful to you but disabling RandR fixed my problems with fglrx 9.4 (8.6.4) on Jaunty. 

just add 

"Option" "EnableRandR12" "false" under "Section Device" in /etc/X11/xorg.conf

PS: Sorry if this is the wrong thread, just wanted to share my solution.

---

### Post by kardian on 2009-12-24
Many thanks for this!

---

