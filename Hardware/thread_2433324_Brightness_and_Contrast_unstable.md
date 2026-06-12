---
title: "Brightness and Contrast unstable"
date: 2019-12-17
forum: Hardware
---

### Post by WB0HYQ on 2019-12-17
When I upgraded to 18.04LTS I found that my video display was rather unstable. I'd set the brightness/contrast/gamma once and suddenly it would jump to very bright and a loss of contrast with colors washing out. When I reset it, the same thing would happen again periodically during the day. I use the NVIDIA XServer video interface to set sliders where I want them.

My system: NVIDIA GT710 running NVIDIA driver set 340.107. My desktop is XFCE

The display will sometimes reset itself if I simply open the XServer interface, suddenly jumping back to the settings I want without me touching a single slider. Other times, I have to move them to reset things the way I want them.

ANy ideas?

Bill

---

### Post by Autodave on 2019-12-18
From what did you upgrade to 18.04?  Upgrades can often cause problems like this.  Can you make a bootable thumb drive with 18.04 on it and boot from that and see if you have the problem?  You may need to do a clean install of 18.04.

---

### Post by WB0HYQ on 2019-12-18
This was a clean install. I dumped Windows 7. The install was from an ISO file on DVD and I reformatted the drive before installing 18.04. I booted up using the installation DVD and the problem still exists. It is probably important to note that under Windows 7, the video card worked just fine with no problems at all.

I booted up a DVD of 16.10 and used it for over an hour with no variation in brightness/contrast. It seems to be something in the way the driver is applied/runs just under 18.04.

Bill

---

### Post by Autodave on 2019-12-18
That card should be using the newest driver and not that old one.  Can you go into settings -> additional drivers and see what that suggests?  Anything newer than the one you are using would be great.  Go for the newest (highest number) one that is suggested.  You may have to reboot for it to work properly.

---

### Post by WB0HYQ on 2019-12-20
I am SO sorry, Autodave. I never got notified your post was here. I went to the Additional Drivers, but was told no drivers were found. I suspect it may be because the card is a fairly old one. In fact, it was the main reason I bought a new computer so I could play graphics-intense games and simulations. This poor, old GT710 couldn't handle it.

I opened the NVIDIA X-Server panel, made the adjustments (for the thousandth time) and saved it to an X Configuration file, yet rebooting has no effect - I still get variations in brightness, sometimes nearly blinding me with bright whites and overexposed web pages. I took the video card out and cleaned the fan blades even though they looked fine. A fan speed monitor says everything is fine in the heat department as well. I feel there is just one small thing keeping this from working and I haven't yet found it.

Bill

---

### Post by Autodave on 2019-12-21
Download a fresh copy of 18.04 and boot to that and see what happens.  You could have gotten a bad download or a bad install.

You definitely need a newer driver for that card, and since your OS can't find one, I believe that you have a bad d-l or install.

---

### Post by WB0HYQ on 2019-12-21
Did that this morning. Latest version of 18.04 still says there aren't any drivers available. Very odd.

Bill

---

### Post by WB0HYQ on 2019-12-21
Well. I tried once more,  this time I booted into a pure version of Unity and tried the software sources once more. I got a little farther, but still of no help. I've attached a screenshot of the results this time. Before, there was nothing in the panel except it could NOT find any driver for me. This time it at least told me there WAS a driver, but I can't get to use because the radio buttons aren't enabled. I'm still stuck with the "manually installed driver" whatever that is.

Bill


[ATTACH=CONFIG]284653[/ATTACH]

---

### Post by ajgreeny on 2019-12-21
But what happens if you select any of the 390, 430 or 435 drivers, all of which are offered in that window?  Are they really all disabled?

Try them one by one to see if they are any better.

---

### Post by WB0HYQ on 2019-12-21
As I said, the radio buttons are NOT enabled. They are "grayed out" and cannot be "pressed".

Bill

---

### Post by Autodave on 2019-12-21
Can you try going into Synaptic and see if you can install the 435 driver from there?

---

### Post by WB0HYQ on 2019-12-21
Synaptic give me a list of perhaps 50 different NVIDIA drivers (three of which, the 331, 331-uvm, and the 340) are installed (green box). The rest are apparently selectable, but with such a variety of versions to choose from I'm totally out of my depth.

I went to the NVIDIA site itself and downloaded the Linux .RUN file for NVIDIA-Linux-x86_64-440.44 and tried to run it with SUDO. It told me I "seemed to be running an X-Server" and "to get out of it before trying it again". I took this to mean booting back up into Unity and trying it again. Is this a safer/easier way to go than trying to use Synaptic to change drivers? I am running XFCE and apparently that's what the driver installation script was trying to tell me.

Bill

---

### Post by Autodave on 2019-12-21
Do NOT install the drivers from the nVidia site: you are just asking for way more work than you bargained for.  If it were me, I would go back to Synaptic, chose the "nvidia-driver-430" driver and let it install.

---

### Post by WB0HYQ on 2019-12-21
I thought the official driver from their site might become a problem, so I did exactly that: used Synaptic to install nvidia-driver-430. Wow, what a mess! Following reboot, the screen had reverted to 800x600 and everything was HUGE! I managed to get Synaptic running and could just barely see the panel with the checkboxes for drivers and such. I reverted back to the ones I mentioned in the previous post and booted yet again. My resolution came back to 1920x1080 and all was well.

I seems as if I simply cannot have a better driver than the one I have now (340.107, according to the NVIDIA X-Server settings panel). It is a very old driver set, yet trying to get a newer one results in disaster. I'll have to live with the abrupt changes in brightness and contrast.

Bill

---

### Post by WB0HYQ on 2019-12-21
I've been doing more thinking about this whole thing. Windows had a setting somewhere (don't remember exactly where) that had two radio buttons. The top one was "Let Windows decide what driver settings to use" and the bottom one was "Let applications decide what settings to use" (or words to that effect).

Does Linux have that type of setting, and if so, where is it.

Bill

---

### Post by WB0HYQ on 2019-12-23
I made the mountain come to me. Next time the NVIDIA card decided to blind me, I used the monitor brightness controls to set it where I wanted it. Now, NVIDIA can undermine my video settings and it will simply return them to where I wanted them in the first place. of course, this will probably get broken in the next update.

Bill

---

