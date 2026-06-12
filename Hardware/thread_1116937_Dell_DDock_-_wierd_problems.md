---
title: "Dell D/Dock - wierd problems"
date: 2009-04-05
forum: Hardware
---

### Post by recluce on 2009-04-05
I am a newbie to Ubuntu (after 11 years of Windows and before that, 10 years of Amiga OS and back in the dark ages, 10 years on Commodore and Atari 8-bit systems) and recently installed Ubuntu 8.10 (64-bit edition) on my Dell Latitude D830.

I figured that I would not want to move to Vista or Windows 7, so I should start to get used to a different OS, since I will not be able to run XP forever.

I am quite impressed with Ubuntu - and undocked, everything works without a flaw (Audio has to go through the OSS driver, ALSA does not give me as much as a squeak).

If the machine is docked to a Dell D/Dock (the large one, with PCI slot), two incompatibilities appear.

1.) Video Issue

My laptop is equipped with a Nvidia Quadro NVS140 graphics module. An external Acer 23" screen connects via DVI to the docking station. Both internal and external screens have 1680*1050 resolution.

If I use the open source driver (the one the Live CD defaults to), both the internal laptop screen and the external display are handled correctly. That is, if the laptop is docked, the system defaults to the external screen. However, graphics are rather slow and limited with that driver.

If I use the Nvidia drivers (either 173 or 177, makes no difference) and the system is docked, Ubuntu starts out on the external screen (Boot messages, progress bar) up to the point at which the graphics driver is initialized. As soon as the Nvidia driver takes control, it switches back to the internal screen and the external screen goes blank. I can open up the lid of my laptop about half way when docked (Dell monitor stand). This is sufficient to see that I am at the Ubuntu log-in screen and to fondle for the "Fn + F8" key combination on the internal keyboard to switch to the external screen.

At that point, I get a black screen with a white text-box on the external display. After entering my user credentials, Gnome desktop will start perfectly fine on the external display. Everything will be normal until log-out, at which point the system switches to the internal laptop display again.

This problem does not exist with Windows XP and current Nvidia Win32 drivers.

Anybody with a solution or any ideas?


2.) Audio problem

Audio is only routed to the Audio connector on the laptop, not to the connector on the docking station (which works fine under Windows XP). It baffles me that anything can actually tell the two connectors apart, since the docking station has no Audio hardware except for the connector. 

Ubuntu offer a bunch of different Audio drivers for my hardware, only the OSS driver actually produces sound.

Again, anybody with an idea or solution?

Any response is greatly appreciated!

---

### Post by recluce on 2009-04-11
*** bump ***

Nobody with any ideas?

---

### Post by pillbug22 on 2009-04-30
Mine is doing roughly the same thing (Latitude D820 w/ standard Dell D-series dock).
 
Everything is perfect undocked, but booting up with it docked brings up a blank screen on the external/dock display.
 
What I found out (by slightly opening the lid on the laptop as it is docked), is that the laptop was booting up and getting to the login screen without any issues. Even though there was no picture on the external display, my external keyboard still worked, so I could put in my username and password.
 
Once it logged in, Unbuntu detected my external display and resolution. Appears the piece that detects external displays only runs after login.
 
 
 

I did also make sure:
[LIST]
[*]Newest NVIDIA driver/console installed
[*]Newest Dell BIOS installed
[*]I set the power management setting to "do nothing" when the screen is closed and it is running on AC power.
[/LIST]

---

### Post by pillbug22 on 2009-05-01
Ok, so that works as a partial fix. It does allow me to view the desktop on my external screen while I'm docked, as long as I dock the laptop while shutdown, then do a fresh boot while already docked. A few issues I'm still having that I'd love to solve (and I'm sure others would too): 
[LIST]
[*]How to display the login screen on the external display when docked? You can see the BIOS, bootup commands, then it works after login, but the login screen does not display on the external.
[*]How to detect the external screen upon docking, when the laptop is already running? Docking the laptop does not seem to kick off any commands/detection within Ubuntu to look for changes (screen changes, NIC/connection changes, etc)
[*]When I do boot up froma docked position and login, I can see the desktop, but the only application that I can run and see on the external display is Firefox. All other apps or managers I start always show up on the laptop display only. I have the newest NVIDIA drivers, and have tried setting the mode to both "Seperate X Screen" and "TwinView", but get the same results either way.
[/LIST]

---

### Post by pcls on 2009-05-08
I have a Dell Latitude E6400 with a Dell E-port docking station, a Dell monitor and sound bar.  I've had/am having similar problems too.  While I've had no luck with my audio problem (see my post [http://ubuntuforums.org/showthread.php?t=1151820](http://ubuntuforums.org/showthread.php?t=1151820)) I have sorted out the graphics problem.

When I got to the login prompt (now only on the laptop screen) I used the <fn>+F8 twice to direct the output to the external monitor but not the laptop screen.  The resolution is still that of the laptop screen (different from my monitor's resolution) but this will be fixed below.

After logging in, run:
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.old
(just in case!).

From a terminal I ran:
sudo nvidia-settings
to start the Nvidia configuration GUI.  The "sudo" is necessary to give root permissions when saving the Xorg.conf file at the end.
In the menu down the left-hand side, click on X Server Display Configuration.  In the resulting Layout view, click on the rectangle corresponding to your external monitor, it is now possible to configure this display using the boxes below the Layout view.  I simply set the appropriate resolution for my monitor, selected "Separate X Screen" via Configure and clicked Apply.  As I recall, a window appears asking if you can see it (i.e. that things haven't been messed up)---click Yes/OK.  

I then selected the monitor screen in the Layout view (in my case, labelled Seiko) and then I Disabled it (I'll mostly have my laptop docked, but keep it as a Separate X Screen if you wish) via Configure (if it wasn't already from the <fn>+F8 above).  Again I clicked Apply if changes had been made.

If all is now as you'd like it, click "Save to X Configuration File" (and I think I then clicked the Merge with existing xorg.conf file when prompted).

The external monitor should now be used by Nvidia driver when logging in etc.

I hope this gives you a few clues.

Regards,
Philip.

---

### Post by pillbug22 on 2009-05-12
Did you have to load anything extra for the Fn+F8 to work? When I'm at the login screen and hit it, the screen flashes for a fraction of a seconds, but always comes back to the laptop screen. Never goes to external mode only.

---

### Post by pcls on 2009-05-12
> **pillbug22 said:**
> Did you have to load anything extra for the Fn+F8 to work? When I'm at the login screen and hit it, the screen flashes for a fraction of a seconds, but always comes back to the laptop screen. Never goes to external mode only.

No extra software required.  But perhaps there are some settings in the BIOS that need to changed; however, I can't recall seeing any.  The Fn+F8 combination (it's F8 on my notebook, check for the LCD/CRT symbols on your notebook keyboard) toggles through the sequence: notebook screen only | both notebook screen and external monitor | external monitor only.  

I'm afraid I can't think why this is not working in your case.  Do you have multiple output display ports you could try?

---

### Post by recluce on 2009-06-17
> **recluce said:**
> 
If the machine is docked to a Dell D/Dock (the large one, with PCI slot), two incompatibilities appear.

1.) Video Issue

If I use the Nvidia drivers (either 173 or 177, makes no difference) and the system is docked, Ubuntu starts out on the external screen (Boot messages, progress bar) up to the point at which the graphics driver is initialized. As soon as the Nvidia driver takes control, it switches back to the internal screen and the external screen goes blank. I can open up the lid of my laptop about half way when docked (Dell monitor stand). This is sufficient to see that I am at the Ubuntu log-in screen and to fondle for the "Fn + F8" key combination on the internal keyboard to switch to the external screen.


This problem continues to exist in Jaunty and in the 180 Nvidia driver, but there is a workaround that makes live much easier:

Press "Scroll-Lock" and "F8" on the **external** keyboard. This is equivalent on most Dell notebooks to pressing "Fn + F8" on the internal keyboard. So no more need to open the lid and fumble for keys blindly! :)


> 
At that point, I get a black screen with a white text-box on the external display. After entering my user credentials, Gnome desktop will start perfectly fine on the external display. Everything will be normal until log-out, at which point the system switches to the internal laptop display again.


The display errors on the login-screen after switching from internal to external display no longer exist with Jaunty. :D


> 
2.) Audio problem

Audio is only routed to the Audio connector on the laptop, not to the connector on the docking station (which works fine under Windows XP). It baffles me that anything can actually tell the two connectors apart, since the docking station has no Audio hardware except for the connector. 

Ubuntu offer a bunch of different Audio drivers for my hardware, only the OSS driver actually produces sound.


Upgrading to Jaunty initially brought a partial solution, as "Autodetect" of the Audio system (HDA Intel STAC92xx) now works. 

The docking station audio connector was suddenly recognized a while later, when I had that connector in use after using Windows XP and forgot to switch back. I assume that some update after the initial release of Jaunty resolved this issue for good.

Bottomline: The D/Dock now works almost perfectly, just press "Scroll-Lock" + "F8" before Login to bring up the external screen.

---

### Post by recluce on 2009-08-23
I believe that one should always share solutions to problems, not only ask questions. For that reason, I dug up this old thread, hoping that the solutions I found will help other people.

These solutions address two problems that exist on (at least some) Dell D-Series laptops (Latitude Dxxx and derived Precision models) when docked to the Dell D/Dock and maybe also when docked to the D/Port


> **recluce said:**
> 
1.) Video Issue

My laptop is equipped with a Nvidia Quadro NVS140 graphics module. An external Acer 23" screen connects via DVI to the docking station. Both internal and external screens have 1680*1050 resolution.

If I use the open source driver (the one the Live CD defaults to), both the internal laptop screen and the external display are handled correctly. That is, if the laptop is docked, the system defaults to the external screen. However, graphics are rather slow and limited with that driver.

If I use the Nvidia drivers (either 173 or 177, makes no difference) and the system is docked, Ubuntu starts out on the external screen (Boot messages, progress bar) up to the point at which the graphics driver is initialized. As soon as the Nvidia driver takes control, it switches back to the internal screen and the external screen goes blank. I can open up the lid of my laptop about half way when docked (Dell monitor stand). This is sufficient to see that I am at the Ubuntu log-in screen and to fondle for the "Fn + F8" key combination on the internal keyboard to switch to the external screen.


Workaround: when you hear Ubuntu's "login drums", press "Scroll Lock" + "F8" on the **external** keyboard, in Jaunty the system will switch to the external screen and you will see Ubuntu's login screen without display errors. This is identical to pressing "Fn" + "F8" on the internal keyboard and eliminates the fumbling under the lid.

While not a complete solution, this takes 99% of the hassle away.


> **recluce said:**
> 

2.) Audio problem

Audio is only routed to the Audio connector on the laptop, not to the connector on the docking station (which works fine under Windows XP). It baffles me that anything can actually tell the two connectors apart, since the docking station has no Audio hardware except for the connector. 

Ubuntu offer a bunch of different Audio drivers for my hardware, only the OSS driver actually produces sound.



This problem and its solution may or may not be limited to systems using Intel's HDA audio system (identified as "Sigmatel HDA" under Windows).

First of all, under Jaunty, you can simply let the System "Autodect" your Audio hardware and it will work (at least for the laptop audio connector). It should default to "HDA Intel (ALSA Mixer)".

To get everything working:

1.) Select the speaker icon on the top right of the screen and click on "Volume Control".

2.) Device should be "HDA Intel (ALSA Mixer)". If not, change the setting accordingly.

3.) Click "Preferences"

4.) In the Volume Control Preferences windows, select the following options: "Master" "PCM" "Front" **"IEC958"**. Close the window

5.) You will now see three tabs in the Volume Control window: "Playback" "Switches" and "Sound Theme". Click on "Switches" and enable "IEC958" to enable the audio connector on the docking station!

6.) Note that both the "Front" and "Master" sliders control the laptop audio connector only! The docking station audio connector can be controlled by the "PCM" slider.

I hope this can help some of you.

---

