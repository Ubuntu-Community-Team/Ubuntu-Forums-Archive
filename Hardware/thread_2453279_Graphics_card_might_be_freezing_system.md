---
title: "Graphics card might be freezing system"
date: 2020-11-06
forum: Hardware
---

### Post by ciphin78 on 2020-11-06
Hi All, First time posting.  I'll try to be as detailed as I can....

I just built a new desktop PC (first new PC I've had in 10 years).  It was a kit from newegg.  Here are the components:
[SIZE=2][/SIZE]
[LIST]
[*][h=1][FONT=arial][SIZE=2]EVGA 500 BA 100-BA-0500-K1 500W ATX12V / EPS12V SLI CrossFire 80 PLUS BRONZE Certified Non-Modular Active PFC Power Supply[/SIZE][/FONT][/h]
[*][h=1][FONT=arial][SIZE=2]ASUS TUF B450-PLUS GAMING AM4 AMD B450 SATA 6Gb/s ATX AMD Motherboard[/SIZE][/FONT][/h]
[*][h=1][FONT=arial][SIZE=2]ASRock Phantom Gaming D Radeon RX 570 DirectX 12 RX570 4G 4GB 256-Bit GDDR5 PCI Express 3.0 x16 HDCP Ready Video Card[/SIZE][/FONT][/h]
[*][h=1][FONT=arial][SIZE=2]AMD RYZEN 5 2600X 6-Core 3.6 GHz (4.2 GHz Max Boost) Socket AM4 95W YD260XBCAFBOX Desktop Processor[/SIZE][/FONT][/h]
[/LIST]
[SIZE=2]Currently running Ubuntu 18.04.5 LTS, but I've also tried 20.04 & 20.10.
What is happening:

After a fresh OS install things appear to be up and running great for about 1 day.  After that amount of time, the system will freeze.  I will reboot and things work good for about an hour and then freeze.  This can repeat forever.  

I removed the RX570 card and put in an old MSI graphics card just to see if that helped and to my surprise the system is not suffering the freezing (this is what i'm running at the moment to post this).

I attempted to install the amdgpu drivers from the amd site for the 570 ([/SIZE]https://www.amd.com/en/support/graphics/radeon-500-series/radeon-rx-500-series/radeon-rx-570) for 18.04.5.  I thought that worked at first but then after a day the freezing started again.

I'm somewhat new to Linux.  I've been looking at the logs but I don't really know what I'm looking for and nothing is jumping out at me....so, i'm hear asking for help.

I'm happy to perform any kind of diagnostics and/or log reporting, I just don't know what else to do at the moment - any direction would be great.  

Let me know if more information about my system is needed, thanks!

---

### Post by ciphin78 on 2020-11-07
Well, It would seem that the GPU may only be part of the problem.  The system froze up again today.  I'm running a Memtest and there are failures...not sure what to do about that at the moment.

---

### Post by MartyBuntu on 2020-11-07
If you have more than one stick of RAM installed, try testing them one at a time.

---

### Post by MartyBuntu on 2020-11-07
Also, your graphics card is bumping up against the very limit of what your power supply can serve. That may or may not be adding to your concerns.

---

### Post by ciphin78 on 2020-11-07
Please expand about the graphics card and PS.  The recommend PSU for the graphics card is 500Watt.  

I removed the first stick of ram (I have 4) and reran memtest and it came back clean.  So i put the rx570 back in and left out the first ram stick and i'm running the system now.  We'll see if it locks up again.  

Are there more hardware tests I should do?

Thanks!

---

### Post by kurt18947 on 2020-11-08
I had something similar happen when I had an Asrock AB350M motherboard and VGA compatible controller: Advanced Micro Devices, Inc. [AMD/ATI] Caicos PRO [Radeon HD 7450] GPU running 18.04. Installing HWE helped some but it still wasn't stable. I then installed 20.04 which was an improvement but still had occasional hard lockups. I tried a different AMD video card but no change in stability. Nothing out of the ordinary showed up in dmesg and I'm not really savvy with reading logs. I swapped out the motherboard to an MSI B450 based board and reinstalled Ubuntu 20.04.1. So far this seems to behave as it should. The video card is using the Radeon driver.

---

### Post by Autodave on 2020-11-08
If that runs clean right now, then I would strongly suspect that your bad RAM chip is the one not in the machine.

---

### Post by mastablasta on 2020-11-08
ryzen - 95 W
Radeon RX 570 150W
--
240 W
+ motherboard + disks+ram should bring you up to 300W-350 W on max

500W bronze should provide at least around 400 W so you should be on the safe side regarding power supply. just a quick calculation.

dmesg shows the errors from boot onwards. there should be xorg or wayland logs you can search for and logviewer will provide you with other logs and errors. you can see if something is wrong if it says ERROR next to the message.

psensor can be used to check for any overheating. lockups can also happen because of that. if PCu is overheating , then paste wasnt' applied correctly, or the cooler isn't sitting on CPU well. 

RAM stick can also cause issues. memtest will show you that.

or it may just be that motherbroard is crappy.

---

### Post by ciphin78 on 2020-11-08
Thanks.  It seems like things are better, however Chrome seems to be locking up and crashing.  I've turned on crash reporting so I can see what it says the reason is.  There is a *.crash file in /var/crash for Chrome, but i don't have a good way to read it... If you know of a good way, please tell me.  So, i think things are getting better but not tweaked to stable just yet.

---

### Post by ciphin78 on 2020-11-08
Can you provide me with some more information about xorg / wayland logs?

I've switched back to the old video card for now.  I'm using psensor and the CPU temp seems to be hovering between 26C - 40C which i think is okay?  I've run memtest several times without the one ram stick and it keeps showing clear of errors.

Here's some info from LOGS:
-Applications: Cannot access vdagent virtio channel /dev/virtio-ports/com.redhat.spice.0
-Applications: [pulseaudio] bluez5-util.c: GetManageObjects() failed: org.freedesktop.DBus.Error.AcessDenied: Rejected sent message
-Applications: CRITICAL: We failed, but the fail whale is dead. Sorry....
-Applciations: [pulseaudio] client-conf-x11.c: xcb_connection_has_error() returned true
-Other [1307]: error: Failed to create /var/spool/cups/tmp/.hplip
-Other Unrecoverable failure in required component org.gnome.shell.desktop

---

### Post by mastablasta on 2020-11-09
> **ciphin78 said:**
> Thanks.  It seems like things are better, however Chrome seems to be locking up and crashing.  I've turned on crash reporting so I can see what it says the reason is.  There is a *.crash file in /var/crash for Chrome, but i don't have a good way to read it... If you know of a good way, please tell me.  So, i think things are getting better but not tweaked to stable just yet.

any major websites where you see this? how did you install it? is it snap?

i use firefox and noscript plugin to turn off scripts i don't need to run (mostly about advertising).

> **ciphin78 said:**
> Can you provide me with some more information about xorg / wayland logs?

I've switched back to the old video card for now.  I'm using psensor and the CPU temp seems to be hovering between 26C - 40C which i think is okay?  I've run memtest several times without the one ram stick and it keeps showing clear of errors.

here is current status: 
[LIST]
[*]you ruled out CPU overheating (that temp is good)
[*]one ram stick seems to be faulty, others are fine
[*]PSU is likely strong enough
[/LIST]

things that still need to be checked:
[LIST]
[*]Radeon RX 570 - does it overheat?
[*]Radeon RX 570 - does it create any error messages in logs?
[/LIST]

the easiest way to see these is when you see desktop acting strange, you switch to terminal using ctrl+alt+F2, then you login and then type dmesg. you will get last errors logged in the end of report.
you can switch back using combination ctrl+alt+F1 or you can reboot or shutdown the PC from here
```
sudo reboot
sudo shutdown -h now

```

> 
Here's some info from LOGS:
-Applications: Cannot access vdagent virtio channel /dev/virtio-ports/com.redhat.spice.0
-Applications: [pulseaudio] bluez5-util.c: GetManageObjects() failed: org.freedesktop.DBus.Error.AcessDenied: Rejected sent message
-Applications: CRITICAL: We failed, but the fail whale is dead. Sorry....
-Applciations: [pulseaudio] client-conf-x11.c: xcb_connection_has_error() returned true
-Other [1307]: error: Failed to create /var/spool/cups/tmp/.hplip
-Other Unrecoverable failure in required component org.gnome.shell.desktop
[/QUOTE]

* Pulse audio errors are sound related. depends what were you doing when these were made. they don't look too critical to me. *[edit: i have same errors]*
* cups is printer driver. do you have trouble printing? *[edit: i seem to have have same errors]*
* last one is desktop error. it can happen in any desktop. sometimes it shows up if application crashes and brings down part of desktop with it. if chrome crashed such message could pop up and desktop could have other errors. i use Kubuntu with KDE and there i can easily solve these kind of errors by having each session start from fresh. so all i would need to do is perform a logout and login and error would be gone. i normally get kwin crash and errors when game running under Wine crashes. 

*edit: xorg log provides information on/from GPU. i don't seem any errors in mine. it just states what was loaded. i don't know if wayland uses same log or journald. i need to still use xorg because nvidia*

---

### Post by P-I H on 2020-11-09
I had problem with my Radeon RX5700 GPU on kernel 5.4. It was related to  the "[COLOR=#202124][FONT=Roboto]Use hardware acceleration when available" setting in Chrome. When I turn off that setting I didn't get any freezes. Now on Ubuntu 20.10 with kernel 5.8 , gnome 3.38 and Chrome v[/FONT][/COLOR][COLOR=#5F6368][FONT=Roboto]ersion 86.0.4240.183[/FONT][/COLOR][COLOR=#202124][FONT=Roboto]  I have no freezes.[/FONT][/COLOR]

---

### Post by ciphin78 on 2020-11-10
Thanks guys.  Another update - I'm at 24 hours of continuous running with no issues.  Temps are normal, errors seems to be gone, and the RX570 is running smoothly.  I even did a few 4k videos just to test with and temps stayed under 55C.  I don't know if it will last, but I'm hopeful.  

I made one change, and this was really stupid on my part.  I went back to the motherboard to ensure everything was connected properly and discovered that there were two issues with the case connectors for the power button LED and the HD LED indicator that were not correctly set on the system panel connector pins on the motherboard.  I corrected those connections and things seem to be working as expected now.  I'm not sure why that alone would reek such havoc but maybe ground wasn't set correctly and causing power issues...  My take-away is to be more careful when counting pins.  If I can run all day today without issue I'll consider this closed.  Thanks for the info on the logs and the memory tests, i've learned a bunch.

---

