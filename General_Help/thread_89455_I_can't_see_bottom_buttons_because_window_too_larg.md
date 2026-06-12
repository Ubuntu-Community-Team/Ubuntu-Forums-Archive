---
title: "I can't see bottom buttons because window too large"
date: 2005-11-12
forum: General Help
---

### Post by frankabel on 2005-11-12
Hi!
When I execute some application I can't see the bottom buttons(Help, Defaults, Reset, Apply, etc.) because the windows is too large, more than the screen. My resolution es 800x600.
How can fix the windows size to my screen.

Thanks

---

### Post by teaker1s on 2005-11-12
have you tried resizing the window? not a permanant fix but useable

---

### Post by frankabel on 2005-11-12
Yes, I try, but I just can adjust the windows witdth. When I try to adjust the windows height I can't. 
Thank for your answer.

---

### Post by salva on 2005-11-12
Have you tried to adjust you monitor controls. Sometimes the monitor is a bit offset, and needs to be reset.
Else, if your monitor is set up correct, try dragging the window with Alt depressed. This may allow you to get hold of the resize controls in bottom left corner and adjust the window.

Other than that... hmmmm... what application is giving you this trouble?

---

### Post by beldon on 2005-11-12
[QUOTE=salva]Have you tried to adjust you monitor controls. Sometimes the monitor is a bit offset, and needs to be reset.
Else, if your monitor is set up correct, try dragging the window with Alt depressed. This may allow you to get hold of the resize controls in bottom left corner and adjust the window.

Other than that... hmmmm... what application is giving you this trouble?[/QUOTE]

I'm having the same issue with Kubuntu.  It's most (if not all) of the System Control sub-panels.  They are not re-sizable and are too large to see the buttons for "Administrator Mode" and several others-- depending on the window.

Unfortunately, I don't have the option of increasing my flat-screens to a higher resolution than 1024x768, so I can't use Ubuntu on two of my three machines.

---

### Post by frankabel on 2005-11-12
For example the System Setting --> Network Settings, I can resize this windows and I can see the bottom buttons. I repeat that my resolution is 800x600, I change the file /etc/X11/xorg.conf and remove "1024x768" in the subsection "Display" whose depth macth match my DefaultDepth (24)
Thanks again for your answer

---

### Post by piquadrat on 2005-11-13
[QUOTE=frankabel]For example the System Setting --> Network Settings, I can resize this windows and I can see the bottom buttons.[/QUOTE]

You can or you can't? Because I have the same problem you described in the first post with this window. It's on an 1024x768 LCD, so I can't adjust the resolution.

---

### Post by frankabel on 2005-11-13
So sorry, was a mistake, I meant I can't.
Thanks and excuses me.

---

### Post by metoo on 2005-11-13
This seems to be a known problem but AFAIK there is no workaround. I once worked around it blindly via the TAB key, counting the tabs and shooting into the dark (hit enter when you think it might be on the OK-button).

Try kcontrol, the original KDE system settings manager, from a console:
sudo kcontrol

If this does not work, I fear you are lost.

---

### Post by frankabel on 2005-11-13
'sudo kcontrol" work for me, Thanks

---

### Post by BRODEL on 2005-11-13
I had this problem earlier while trying to configure my network devices after installing. Someone on IRC suggested I hit Alt and click on the window to move  the window to see the button you need to hit. 

It worked for what I needed to do, but it does kind of suck that you have to do this as a workaround.

---

### Post by kwalker on 2005-12-20
Thanks, I had the same problem, the alt key is the secret to being able to drag it beyond the top of the screen.  :-)

---

### Post by pickapepper on 2005-12-20
Hey I am a new user on Kubuntu and Linux.  I am having the same problem.  When I go into Kconsole what or where do I go from there?  Thanks for the help

---

### Post by ace2005 on 2005-12-21
To move a window press  and hold down the Alt key and then click on an empty area of an application where there is nothing, like the status bar to drag it

To change system settings use "Alt + F2"  to open the run dialogue and then type kcontrol, kcontrol can be maximized and the buttons will show

---

### Post by orbital on 2006-01-12
sudo kcontrol works for me too.

---

### Post by feathers on 2006-01-12
You can always move the windo upwards if you press the ALT key and then klick and hold the mouse on any part of the window. Then you can at least press the buttons.

---

### Post by jason.b.c on 2006-02-20
i have a question , in breezy how can you resize your desktop _without_changing the screen resolution. what i mean is this, say you change your res to 1280-1024 wich is what i use _but_there is this black border around the actual desktop ( about an inch i would say )so how can you _zoom_this in without changing the screen resolution or any or all settings on the monitor ( if i change the settings in the monitor it will affect the way that my windows desktop looks );)

---

### Post by caish5 on 2007-10-24
A new solution for this problem that i've found is...

If you have Desktop Effects running you can use <super> + <v>
and the window will scale to the sceen.

---

