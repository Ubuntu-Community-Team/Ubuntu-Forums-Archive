---
title: "Razer Copperhead issues - 7.04 - the Feisty Fawn"
date: 2007-03-29
forum: Hardware &amp; Laptops
---

### Post by soniclava on 2007-03-29
Hey

I have been having issues with my Razer Copperhead mouse w/ 7.04.  Every time I restart I have to unplug/plug my mouse to make it work again.

I have loaded 
[http://razertool.sourceforge.net/](http://razertool.sourceforge.net/)

When I run the Razer configure utility (razertool-gtk) I am able to see my mouse connected.  It seems to just be a post loading issue, but not sure how to check post errors.

Anyone have any ideas???

---

### Post by soniclava on 2007-03-29
I reinstalled the mouse software, restarted, and worked.  Guess I posted too soon!

---

### Post by derrekito on 2007-04-21
If you have any other issues, let us know; I am currently tracking specific hardware (Razer Copperhead being one of them) for Linux support.  Thank you.

---

### Post by Instance42 on 2007-05-04
> **soniclava said:**
> I reinstalled the mouse software, restarted, and worked.  Guess I posted too soon!

Hi soniclava,

Could you please detail what you mean by "reinstalling the mouse software"? Do you refer to the razortool software?
I'm experiencing the same trouble with my copperhead (need to replug it at feisty's startup else the pointer remains stuck in the bottom left corner of the screen).

Thanks!

---

### Post by thread on 2007-05-10
Yeah, what Instance42 said! What needs to be done, exactly? There are no drivers to reinstall afaik....

---

### Post by sih_phos on 2007-05-10
I'm still really new to Ubuntu so I'm not sure how/if this will help or apply to anybody.  

I used to have the same problem (no mouse on restart) when running WinXP.  If you can, go to razerzone.com and download the new driver/firmware.  Of course, I did this in Windows  This also solved the problem for a friend of mine.  Neither of us have run it directly in Ubuntu so I can't guarantee anything.  I also have to make sure it's plugged into the same usb port for WinXP to recognize it, but that could be my motherboard or something else.

Eric

---

### Post by _simon_ on 2007-05-19
I've got the same problem, anyone fixed this yet?

I just tried the Live CD and the mouse works without needing to be unplugged and plugged back in, does this mean a fresh install would get it working?

---

### Post by Bokonon on 2007-05-19
Hmm, I had trouble with dual boot and my copperhead.  My laptop would beep like mad on rebooting and loading BIOS.

My solution was to go back to my G5, but I might give this a try.  

I really liked the Copperhead, but never totally got used to it....i right-clicked a lot by accident.  

Thanks for the info, I wish I had found this earlier!

---

### Post by _simon_ on 2007-05-19
Just tried a fresh install but still no joy.

Why does it work on the Live session via the CD but not the install?

---

### Post by _simon_ on 2007-05-19
*RESOLVED*

This worked for me, hopefully it will for others as well.

What I did:

1) Fresh Ubuntu 7.04 Install (probably not needed)

2) Edited Mouse section in Xorg with this:

```

Section "InputDevice"
    Identifier  "Configured Mouse"
    Driver      "mouse"
    Option      "Name"          "Razer Copperhead"
    Option      "Vendor"        "Razer"
    Option      "CorePointer"
    Option      "Protocol"      "ExplorerPS/2"
    Option      "ZAxisMapping"  "4 5"
    Option      "Device"        "/dev/input/mice"
    Option      "Buttons"       "7"
    Option      "ZAxisMapping"  "6 7"
    Option      "ButtonMapping" "1 2 3 6 7"
    Option      "Resolution"    "2000" 
    Option      "SampleRate"    "1000Hz" 
EndSection

```

3) Installed razertool-gtk from here: [http://downloads.sourceforge.net/razertool/razertool-gtk_0.0.7-1_i386.deb?modtime=1171502538&big_mirror=0](http://downloads.sourceforge.net/razertool/razertool-gtk_0.0.7-1_i386.deb?modtime=1171502538&big_mirror=0)

4) From terminal 

```

sudo razertool-gtk

```

I did not change anything, just closed it.

5) Restarted the machine.

I've restarted twice now just to make sure, but can confirm that it now works without having to be unplugged and plugged back in again.

---

### Post by _simon_ on 2007-05-20
**UPDATE**

From a cold boot this morning it's not working again! :(

Is there anyway to "reinitiate" all USB ports after login?

---

### Post by _simon_ on 2007-05-25
It worked this morning without having to unplug it and plug it back in!

The only thing I have changed is that I'm currently not using a wallpaper, but I can't see how this would affect anything?

---

### Post by _simon_ on 2007-06-05
Another update- the above was very short lived.

I've had 3 power cuts today which has meant that Ubuntu has not shut down properly.

Each time I have booted again, the mouse has worked without needing to be unplugged and plugged back in,

Aside from the shutdown option, is there an alternative shutdown method that might not run through the shutdown sequence that is normally used? I don't know how things work but I am guessing that the mouse does not normally work on boot because something is being written or set at shutdown,bypassing normal shutdown means that this does not happen. - or so it seems?

---

### Post by _simon_ on 2007-06-06
Right guys, I may have found the solution.

Instead of going to System -> Quit, I used this command to shutdown from terminal:

```

sudo shutdown -h now

```

On booting this morning, the mouse is working without needing to be unplugged and plugged back in.

Would be great if someone else could try this to see if it does really work...

---

### Post by _simon_ on 2007-06-07
Day 2 of shutting down the above way and the mouse has again worked on boot!

---

