---
title: "PC shuts off when booting any linux distro"
date: 2016-06-24
forum: Hardware
---

### Post by mmsmc on 2016-06-24
[COLOR=#070F14][FONT=Verdana]My pc is a dedicated windows pc for school. I have had this issue before with windows but determined it was mainly an overheating issue when gaming or running simulations. However I recently decided to get back into linux with my free time over the summer and am having an interesting time. Every time I attempt to fully boot into any linux distro my pc restarts, I never get into the distro as it shuts off when it loads the iso. I can however boot into the installation gui for the distros. I would imagine this is either a graphics card or power issue. I do not know how to trouble shoot it though as I cannot replicate the issue in windows, any hardware diagnostic tools I use tell me nothing is wrong.[/FONT][/COLOR]

[COLOR=#070F14][FONT=Verdana]Any ideas on this?[/FONT][/COLOR]
[COLOR=#070F14][FONT=Verdana]Thanks[/FONT][/COLOR]

[COLOR=#070F14][FONT=Verdana]PC Specs:[/FONT][/COLOR]
[COLOR=#070F14][FONT=Verdana]PSU: Corsair 750W[/FONT][/COLOR]
[COLOR=#070F14][FONT=Verdana]CPU: AMD 8350[/FONT][/COLOR]
[COLOR=#070F14][FONT=Verdana]CPU Fan: Cooler Master Hyper 101i[/FONT][/COLOR]
[COLOR=#070F14][FONT=Verdana]MotherBoard: ASUS Sabertooth 990FX[/FONT][/COLOR]
[COLOR=#070F14][FONT=Verdana]GPU: GTX 780[/FONT][/COLOR]

---

### Post by Bucky Ball on 2016-06-24
So you're saying when you click 'Install Ubuntu' it heads of to the install GUI, when you hit 'Try Ubuntu' the machine restarts?

Try hitting any key when you get to the purple screen with the icon at the bottom. From the next screen, hit F6. That should bring up some options. Choose 'nomodeset' and proceed to 'Try Ubuntu'. Any luck?

(PS: The above may not be how you get to the options now, haven't done it in awhile, but you are looking for 'nomodeset' as the option to try. You will find it somewhere in one of the menus at boot by hitting F6 somewhere. This may get you through any vid issues for the time being, if it is that.)

---

### Post by mmsmc on 2016-06-24
Nope, no luck. cant even get to the purple screen in time before it shuts off. Ill click on try ubuntu, itll load two files then bam it restarts. Works perfectly on windows though.

---

### Post by yancek on 2016-06-24
Which version of Ubuntu are you trying, is it the latest 16.04?
Did you download from the Ubuntu site?  Did you do an md5sum to verify the download was good?  Are you able to test the DVD/flash drive in another computer to verify that it boots? How are you booting Ubuntu or your other Linux systems?  Burning a DVD "as an image"?  Are you using a usb/flash drive?  If so, what software did you use to put it on the flash drive?   Also, which windows version are you using?  Makes a big difference as recent versions have made major changes in the basic process.

---

### Post by RobGoss on 2016-06-25
You stated this also happens while you was using Windows correct? so this tells me it's this has nothing to do with any Linux distribution but may have something to do with your machines hardware or maybe your CPU over heating issue. Try it with the Live USB and see if you're able to boot in to the desktop with out your machine shutting down or restarting

---

### Post by gordintoronto on 2016-06-26
How old is the computer? You might need to clean the heat sink and fan, and replace the thermal paste.

---

