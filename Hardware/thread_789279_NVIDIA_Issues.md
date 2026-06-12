---
title: "NVIDIA Issues"
date: 2008-05-10
forum: Hardware
---

### Post by jsegars on 2008-05-10
I'm trying to get the NVIDIA proprietary drivers up and running on my system and I have something odd going on. After running the installer (it builds the kernel module and everything) I bring up gdm with $sudo /etc/init.d/gdm start. Tada, everything comes up nice and pretty and resolution is just right. I can even do a gdm restart in the same session and it comes up just fine. glxgears runs smoothly as well. The problems seem to happen when I restart. Visually I get a message saying that it couldn't detect my display or something to that effect and it starts up with the failsafe driver. Looking through the Xorg.0.log there's the following error: (EE) Failed to initialize GLX extension (Compatible NVIDIA X driver not found). Now what's interesting about this is that this occurs on line 1576 but further up at line 261 it states that it recognizes and loads the glx module???? I've attached my xorg.conf and Xorg.0.log files if anyone wants to give it a shot. Thanks in advance for the help.

---

### Post by Tomatz on 2008-05-10
Have you tried using envyng to install them?

Envyng:

[http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)

---

### Post by jsegars on 2008-05-10
no I haven't, I'll give it a shot now and let you know how it works out. Thanks

---

### Post by that_IT_guy on 2008-05-10
I just got my Nvidia Geforce 7600gs up and working.  Envyng did not do it for me.  I used synaptic package installer and removed all related nvidia drivers and components including nvidia xorg driver and nv glx, or glx new in either case.  I then installed the Nvidia 169.12 pkg manually from a shell, after installing my resolution works great, and my openGL is smokin now too:guitar:.  When I first tried to install the drivers my res wouldnt work, and neither would my openGL.  Now my problem is getting nvtvout to recognize my tv, the default drivers loaded when installing ubuntu could see my tv (no nvtvout) but now with the nvidia xconfig working nvtvout doesnt see my tv.

I hope this helps you with your driver problem.  Keep us posted

BTW if you are using Ubuntu Server Edition you are out of luck, as Server uses a Xen kernel which is not supported by Nvidia at the moment I actually had to reinstall my OS from Server to Desktop so I could utilize my card.

---

### Post by pointym5 on 2008-05-10
I just finished installing the NVidia driver from the NVidia site after getting fed up with the terrible performance from the Hardy nvidia-glx package.  Now, my xterms refresh more-or-less instantaneously after I switch desktops, just like they used to with Dapper.

My suspicions that something was badly wrong with the driver really solidified when I installed Hardy on a Dell box with lowly Intel graphics. It was *much* faster than my home machine (well, the UI was faster).

Has anybody logged appropriate bugs? It's quite clear to me that something's very wrong.

---

### Post by PmDematagoda on 2008-05-10
For the people with the OP's problem, it is most likely to be something with the incorrect modules being loaded at start-up. To fix this, do:-
1) Open a modules file for editing with:-
```
sudo nano /etc/default/linux-restricted-modules-common
```

2) Edit the DISABLED_MODULES line to make it look like this:-
```
DISABLED_MODULES="nv nvidia_new"
```
and save the file.

Then reconfigure the X-Server or reinstall the driver again and reboot the PC, the X-Server should work properly now.

---

### Post by that_IT_guy on 2008-05-10
> **pointym5 said:**
> I just finished installing the NVidia driver from the NVidia site after getting fed up with the terrible performance from the Hardy nvidia-glx package.  Now, my xterms refresh more-or-less instantaneously after I switch desktops, just like they used to with Dapper.

My suspicions that something was badly wrong with the driver really solidified when I installed Hardy on a Dell box with lowly Intel graphics. It was *much* faster than my home machine (well, the UI was faster).

Has anybody logged appropriate bugs? It's quite clear to me that something's very wrong.


As far as I can tell it,s a conflict with the -nvidia-glx driver still being installed in the system when installing the proprietary drivers from nvidias website.  Look up and maybe try my solution, it worked for me.  But I am a linux noob, so I may be wrong.  Let me know what happens.

---

### Post by pointym5 on 2008-05-10
> **that_IT_guy said:**
> As far as I can tell it,s a conflict with the -nvidia-glx driver still being installed in the system when installing the proprietary drivers from nvidias website.  Look up and maybe try my solution, it worked for me.  But I am a linux noob, so I may be wrong.  Let me know what happens.

No, I removed the packaged and unloaded the driver before running the NVidia installer. The NVidia installer had no problems at all, and X started up the first time I tried it.

The difference between performance with the Ubuntu-packaged driver and the NVidia-packaged driver is not subtle - it's **huge**. Previously, a large xterm window filled with text would take almost a second to redraw - it was like using an RS-232 terminal at 19.2KBaud. Now, the xterm windows redraw instantaneously. That's the way my machine was when running Dapper, and it's back to that now.

[edit]
Upon re-reading the OP I suspect you're right. My problems were different. The Ubuntu-packaged driver *worked*, but it was terribly slow. The NVidia-packaged driver works and works properly.

---

### Post by jsegars on 2008-05-10
Interesting issues...I grabbed envyng, brought it up and told it to uninstall my current drivers. Essentially what it appeared to do was download the latest generic nvidia libglx drivers and installed those. After a restart everything appeared to be fine, The resolution on the login screen was set correctly and looked sharp. During the login process it looked like everything was happening right but after the background appeared, the bottom toolbar came up but looked jagged and completely messed up. The top toolbar never came up and mouse clicks did nothing. I couldn't even ctrl+alt+f1 or ctrl+alt+backspace the thing. After a restart I went straight to the command prompt and ran envyng in textual mode. I selected the option to automatically detect my card and install the latest drivers. It did just that and it did it right. After a restart everything is in order. GLX is up and running beautifully :). Thanks for the help and the quick replies.

---

### Post by Tomatz on 2008-05-10
> **jsegars said:**
> Interesting issues...I grabbed envyng, brought it up and told it to uninstall my current drivers. Essentially what it appeared to do was download the latest generic nvidia libglx drivers and installed those. After a restart everything appeared to be fine, The resolution on the login screen was set correctly and looked sharp. During the login process it looked like everything was happening right but after the background appeared, the bottom toolbar came up but looked jagged and completely messed up. The top toolbar never came up and mouse clicks did nothing. I couldn't even ctrl+alt+f1 or ctrl+alt+backspace the thing. After a restart I went straight to the command prompt and ran envyng in textual mode. I selected the option to automatically detect my card and install the latest drivers. It did just that and it did it right. After a restart everything is in order. GLX is up and running beautifully :). Thanks for the help and the quick replies.


Strange.

There must have been some residual configuration from the old drivers conflicting with the new ones. Linux can do some strange things when gpu drivers are misconfigured. Once i had a problem with my drivers, the text rendered in mozilla was about 10 times the size of my screen and sideways lol. 

The text was perfectly antialiased though.

:lolflag:

---

