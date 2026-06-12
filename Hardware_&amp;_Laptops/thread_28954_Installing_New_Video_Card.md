---
title: "Installing New Video Card"
date: 2005-04-22
forum: Hardware &amp; Laptops
---

### Post by clarke.rainey on 2005-04-22
Well I looked around a bit for a "How-to" or a previous post on this subject and could not find one... so I am making one now...

I just upgraded to Hoary and am using X11 now... I just got a new nVidia 6600GT AGP card in the mail today and I really want to install it for WoW... I was wondering what I would need to do in order to install it with the least amount of trouble... 

I read that Hoary has better new hardware detection and such but I do now know if that is only at install or if you can find new hardware on an existing install... I was also wondering what kind of stuff I would need to change in the X11 config for the new card...

If anyone could please educate me on this matter it would be much appreciated as I really want to try and get this card in as soon as possible... also some sort of detailed write-up would be the best so that the next person installing a new video card will have some good ubuntu reference material on the subject...

Thanks alot peoples!..

---

### Post by andvaranaut on 2005-04-22
[QUOTE=clarke.rainey]I just upgraded to Hoary and am using X11 now... I just got a new nVidia 6600GT AGP card in the mail today and I really want to install it for WoW... I was wondering what I would need to do in order to install it with the least amount of trouble... 

[/QUOTE]
 See [http://www.ubuntuguide.org/#installnvidiadriver](http://www.ubuntuguide.org/#installnvidiadriver). The process is rather painless and straightforward. You don't need to install the nVidia settings shortcut if you don't want to; do what the guide says up to the **sudo nvidia-glx-config enable** command and that will do it. (You will probably want to restart X, or reboot).

In fact, the nVidia drivers are common to all nVidia models. If you are updating from another nVidia card and already have the nVidia drivers installed, they will pick up your new card automatically.

You shouldn't have many problems installing the video card. If you have X configured to use a generic 'vesa' videocard, it will boot up perfectly once you have installed the card and you will be able to open a terminal to issue the commands in the guide. If not, you will be presented with a terminal for you to login, then you can copy the commands there. A good thing to do would be to print the commands, so that you are still able to write them even if you can't access X. (Writing **sudo reboot** or pressing Ctrl-Alt-Del will reboot the computer in a safe way)

If you want more info about the internals of the process you should read the driver's isntallation notes. I'm on Fedora Core at the moment (I have Ubuntu only at home) so I don't know where they are exactly. Look for NVIDIA in  /usr/share/doc/. The docs are rather well written. The installation part will be taken care of by the Ubuntu package management system, but you might want to play with the options you can enable by tinkering a little bit with xorg.conf.

Hope this helps. Cheers

---

### Post by baylisscg on 2005-04-22
Hi,

  One point about the 6600GT. The open source "nv" driver doesn't support it or any of the 6 series so you will require nVidia's binary driver, "nvidia". Provided you are using the nvidia driver you should be able to swap out your old card. I have done the same thing changing between a MX460, FX5200, 6600GT and 6800GT with no apparent ill effects. 

You can locate which driver you are using in your X config. Either "XF86CONFIG-4" for XFree86 or "xorg.conf" for X.org. There should be a 'Section "Device"' line and below it a 'Driver          "<driver name>"' line. Of course if your current card is not an nVidia one you will have something else here. I havn't tried Hoary's ability to detect the 6600 so it may automagically but be prepared for it to boot to a terminal and have to change the driver in an editor.

The good news is that Hoary has the latest versions of the vNidia driver that seem to work rather well on the 6 series.

---

### Post by clarke.rainey on 2005-04-22
Well thanks sooo much guys... I had figured that the nvidia drivers would work since they are all about the unified driver stuff... I was just worried about the X11 stuff since I have never really messed with that... I am about to go walk to the campus mail center to get the card now... I will tell you how it goes!..

Have a great day!

---

