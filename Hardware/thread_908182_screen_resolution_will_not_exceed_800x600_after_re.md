---
title: "screen resolution will not exceed 800x600 after reboot"
date: 2008-09-02
forum: Hardware
---

### Post by bobdobbs on 2008-09-02
Hi all.

I'm using Hardy. I've been using an nvidia card, but I don't know a lot about it.

I've always had trouble understanding X and linux video, but this couldn't have come at a worse time. 

I was having trouble with my network, so I rebooted to see if that would help. When Heron restarted the screen was stuck at 800x600.
Nightmare! I have design work due in the morning, and I've been using gimp.

When I log in to gnome I can't actually go to screen resolution setting. Gnome was so unusable that I couldn't target anything to click with the mouse. 

I logged in to KDE4 to get to a settings menu where I can set the resolution.
I found a settings panel for nvidia settings. But, the resolution options don't go past 800x640.

I've left this computer on for a very long time, over which I've run the software update program. I suspect that changes were made that didn't take effect until a reboot.

I would be grateful in the extreme if someone could help me out on this one.

---

### Post by overdrank on 2008-09-02
> **bobdobbs said:**
> Hi all.

I'm using Hardy. I've been using an nvidia card, but I don't know a lot about it.

I've always had trouble understanding X and linux video, but this couldn't have come at a worse time. 

I was having trouble with my network, so I rebooted to see if that would help. When Heron restarted the screen was stuck at 800x600.
Nightmare! I have design work due in the morning, and I've been using gimp.

When I log in to gnome I can't actually go to screen resolution setting. Gnome was so unusable that I couldn't target anything to click with the mouse. 

I logged in to KDE4 to get to a settings menu where I can set the resolution.
I found a settings panel for nvidia settings. But, the resolution options don't go past 800x640.

I've left this computer on for a very long time, over which I've run the software update program. I suspect that changes were made that didn't take effect until a reboot.

I would be grateful in the extreme if someone could help me out on this one.

Hi and you can try and boot into recovery mode and use the xfix option. Recovery mode is usually the second choice from the grub.

---

### Post by bobdobbs on 2008-09-02
Hm.

I can't seem to get video in text mode.
When I should be seeing text scrolling before X starts on boot, or as the OS shuts down, I get an error from my monitor instead.
"out of range"

I just plugged in another monitor and something similair happened:
I get a similair message:
"out of range error"

Something is seriously screwy here.

---

### Post by Onyxblack on 2008-09-02
Pressing Ctr+alt+f2 after bootup? does that switch you to text or do you still give you a out of range error?

---

### Post by bobdobbs on 2008-09-02
> **Onyxblack said:**
> Pressing Ctr+alt+f2 after bootup? does that switch you to text or do you still give you a out of range error?

Hi Onyx.
Strange...

When I first noticed this problem I used ctrl+alt+F1 to drop to a shell in order to kill and restart the X server.
I was able to do so.

But, trying that now fails. 
The "out of range" error persists.
Xorg seems to have completely melted down on me.

I've plugged my main monitor back in, so I haven't tested this on my back-up monitor.

Any idea what could be going on ?

It looks to me like the problem is somehow getting worse.
I now have no way of accessing my desktop computer.
I cant access it via ssh because I could never figure out how to make the wireless network start automatically on boot.

This is particularly frustrating for me because I was doing design work on my desktop. Fortunately, I have most of that my current project backed up onto my laptop. 

I'm a bit worried that I might have to completely re-install an OS in order to get use of that desktop computer.


update - I did a hard reboot by turning the desktop pc's power off.
I now have X back. But, it is still in low resolution.
I can no longer drop to a shell with ctrl-alt-F1.

---

### Post by Onyxblack on 2008-09-03
No clue man sorry - other then getting a vid card that might be compatible - what are you trying to connect with now ATI? heh... yeah their driver support sucks... - If your worried about your file, are you able to start with a boot CD? its possible to connect to a network with a start cd - and transfer your files to a network - then at least your files are backed up.

---

### Post by tuxxy on 2008-09-03
Search in synaptic for nvidia-glx and remove any nvidia drivers you have installed.

Now try and enable the driver, if still no luck and you out of options you could reconfigure the xorg

```
dpkg-reconfigure xserver-xorg
```

---

### Post by bobdobbs on 2008-09-04
Most fortunatly, and most scarily, this problem went away.

I pulled apart my rigs to do testing on the monitor and cables.
I tested the monitor, a 22" chimei with a plug matching this image:

[http://www.interfacebus.com/PC_Plug_and_Display_Video_Bus_Pinout.html](http://www.interfacebus.com/PC_Plug_and_Display_Video_Bus_Pinout.html)

It worked fine with another computer. I also tested it's other cable input - the one that looks like a more typical monitor cable plug.

I tested the problem machine with another monitor. No problems.

I plugged the problem monitor back in.

It was working again. It continues to work.

This is a temporary relief.
But it is creates a fear in the back of my mind.
I don't know what happened, or when it will happen again.
I don't know the conditions under which this problem will resurface.

I'm going to have to reboot some time soon, and I don't know if the problem will resurface upon this reboot or future reboots.

My work at the moment and no doubt upon future occaisons will require design. This requires a dependable video subsystem.

I might have to put some research time and money into finding the best-supported, most reliable combination of video card and monitor in order to avoid this kind of thing happening.

Thanks for the input guys.

Any further thoughts appreciated.

---

