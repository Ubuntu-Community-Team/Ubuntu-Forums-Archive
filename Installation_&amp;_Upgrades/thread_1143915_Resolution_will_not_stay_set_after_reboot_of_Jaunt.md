---
title: "Resolution will not stay set after reboot of Jaunty install"
date: 2009-04-30
forum: Installation &amp; Upgrades
---

### Post by danebramaged on 2009-04-30
I just went from 8.10 to 9.04.  I have an Nvidia 7600 GS 8x AGP card.  AMD Semperon 3100+, Gigabyte mobo.  Jaunty wants my res to be 1600 but I like 1280 x 1024 on my Nokia 445xi.  Everytime I reboot it goes back to 1600 resolution.

How do I force Ubuntu to except the fact that I am farsighted and need the 1280 x 1024 at 85mhz setting?

(  This was never a problem under Hardy OR Intrepid.  )

please help the danebramaged.

---

### Post by Mark Phelps on 2009-04-30
Try going into the Display applet and setting the resolution there.  Maybe that will "stick" beyond reboot.

---

### Post by guitar_man on 2009-04-30
on the terminal type


> sudo nvidia-settings

clisk on X server configuration

then choose your desire resolution then save it...
please do reply when it work...I had the same problem and got it working....

---

### Post by danebramaged on 2009-04-30
> **Mark Phelps said:**
> Try going into the Display applet and setting the resolution there.  Maybe that will "stick" beyond reboot.

When I do that this is what I get:

"It appears that your graphics driver does not support the necessary extensions to use this tool.  Do you want to use your graphics driver vendor's tool instead?"

Clicking "Yes" brings up NVIDIA X Server Settings.

I am able to change what ever I want for the current session however, the X server will still be set to "auto" the next time I start my computer.

"auto" is the default setting for resolution and refresh rate. What it defaults to is 1600 x 1200.  1280 x 1024 @ 85 mhz is sooo much more "swedish standard" on my eyes.

Amazingly, other settings available through NVIDIA X Server settings like unchecking the "Do You Really Want to Quit" Option, are held over after the reboot as they should be.

The monitor is a Nokia 445Xi and is recognized properly by the system.

:confused:

---

### Post by danebramaged on 2009-04-30
> **guitar_man said:**
>                                   **Re: Resolution will not stay set after reboot of Jaunty install**             
                                                                on the terminal type


     Quote:
                                                 sudo nvidia-settings   

                              
clisk on X server configuration

then choose your desire resolution then save it...
please do reply when it work...I had the same problem and got it working....
                                                                                               __________________
                **Coffee drinkers don't get dehydrated...**             



This is what I get when I run sudo nvidia-settings:


isaac@Monolith:~$ sudo nvidia-settings

ERROR: Cannot open display 'Monolith:0.0'.


ERROR: Unable to assign attribute CursorShadow specified on line 21 of
       configuration file '/home/isaac/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute CursorShadowAlpha specified on line 22 of
       configuration file '/home/isaac/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute CursorShadowRed specified on line 23 of
       configuration file '/home/isaac/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute CursorShadowGreen specified on line 24 of
       configuration file '/home/isaac/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute CursorShadowBlue specified on line 25 of
       configuration file '/home/isaac/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute CursorShadowXOffset specified on line 26 of
       configuration file '/home/isaac/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute CursorShadowYOffset specified on line 27 of
       configuration file '/home/isaac/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute SyncToVBlank specified on line 28 of
       configuration file '/home/isaac/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute LogAniso specified on line 29 of
       configuration file '/home/isaac/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute FSAA specified on line 30 of configuration
       file '/home/isaac/.nvidia-settings-rc' (no Display connection).


ERROR: Unable to assign attribute TextureSharpen specified on line 31 of
       configuration file '/home/isaac/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute AllowFlipping specified on line 32 of
       configuration file '/home/isaac/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute FSAAAppControlled specified on line 33 of
       configuration file '/home/isaac/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute LogAnisoAppControlled specified on line 34 of
       configuration file '/home/isaac/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute OpenGLImageSettings specified on line 35 of
       configuration file '/home/isaac/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute RedBrightness specified on line 36 of
       configuration file '/home/isaac/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute GreenBrightness specified on line 37 of
       configuration file '/home/isaac/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute BlueBrightness specified on line 38 of
       configuration file '/home/isaac/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute RedContrast specified on line 39 of
       configuration file '/home/isaac/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute GreenContrast specified on line 40 of
       configuration file '/home/isaac/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute BlueContrast specified on line 41 of
       configuration file '/home/isaac/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute RedGamma specified on line 42 of
       configuration file '/home/isaac/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute GreenGamma specified on line 43 of
       configuration file '/home/isaac/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute BlueGamma specified on line 44 of
       configuration file '/home/isaac/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute DigitalVibrance specified on line 45 of
       configuration file '/home/isaac/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute ImageSharpening specified on line 46 of
       configuration file '/home/isaac/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute XVideoTextureSyncToVBlank specified on line
       47 of configuration file '/home/isaac/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute XVideoBlitterSyncToVBlank specified on line
       48 of configuration file '/home/isaac/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute XVideoSyncToDisplay specified on line 49 of
       configuration file '/home/isaac/.nvidia-settings-rc' (no Display
       connection).



The NVIDIA X Server then loads and works as it should.  The only exception being that next time I start my computer the resolution and refresh rate will once again be set to "auto".

How do I turn off or disable "auto" in the NVIDIA X Server?

:confused:

---

### Post by User20202 on 2009-05-03
I had exactly the same problem using an NVIDIA 8400GS after upgrading to Jaunty in that I could change the resolution using the NVIDA settings but it wouldn't stay when I rebooted. I tried guitar man's solution and it didn't work at first. Then I realized that when he had the right idea but left out a step. First, go into a terminal and "sudo nividia-settings" exactly like he says. This is necessary so that the "Save to X Configuration File" will work properly. If you don't sudo, it can't create the backup file and won't update the master file. Then change to the resolution and Hz settings that you want. The step Guitar Man left out is that you must then Apply the new settings first and then accept the new settings. Once your system is running at the settings you want, you can then "Save to X Configuration File". If you get no errors in this step, then you are good to go and when you reboot you should come up in the resolution that you set.

---

### Post by danebramaged on 2009-05-04
> **User20202 said:**
> I had exactly the same problem using an NVIDIA 8400GS after upgrading to Jaunty in that I could change the resolution using the NVIDA settings but it wouldn't stay when I rebooted. I tried guitar man's solution and it didn't work at first. Then I realized that when he had the right idea but left out a step. First, go into a terminal and "sudo nividia-settings" exactly like he says. This is necessary so that the "Save to X Configuration File" will work properly. If you don't sudo, it can't create the backup file and won't update the master file. Then change to the resolution and Hz settings that you want. The step Guitar Man left out is that you must then Apply the new settings first and then accept the new settings. Once your system is running at the settings you want, you can then "Save to X Configuration File". If you get no errors in this step, then you are good to go and when you reboot you should come up in the resolution that you set.

[SIZE=7]**SOLVED**[/SIZE]



Thank you for helping the danebramaged.

---

### Post by zim2dive on 2009-05-29
> **danebramaged said:**
> I just went from 8.10 to 9.04.  I have an Nvidia 7600 GS 8x AGP card.  AMD Semperon 3100+, Gigabyte mobo.  Jaunty wants my res to be 1600 but I like 1280 x 1024 on my Nokia 445xi.  Everytime I reboot it goes back to 1600 resolution.

How do I force Ubuntu to except the fact that I am farsighted and need the 1280 x 1024 at 85mhz setting?

(  This was never a problem under Hardy OR Intrepid.  )

please help the danebramaged.

I have the same problem (just so no one thinks the OP is a one-off situation).. I will try the solution below when I get back from out of town (running w/sudo from cmd line)

---

