---
title: "Kubuntu Intrepid Graphics Issues"
date: 2009-12-18
forum: Hardware
---

### Post by TrevT93 on 2009-12-18
EDIT: this post has been completely rewritten:

Having issues with the ATI graphics (Radeon 9500 PRO) on a computer running Kubuntu Intrepid.  FGLRX does not work, I've tried a thousand different methods of getting it to work with the card, but none seem to work.

Moreover, the ATI and Radeon xserver-xorg drivers aren't working the way they should.  If I install them and edit the "Driver" line in xorg.conf to say ATI or Radeon, I get a blank screen (the monitor isn't picking up a signal, the card probably isn't putting one out).  Only the vesa driver seems to do anything.

Using KRandR with a res. of anything but 1280x1024 (under the vesa driver) gives me a garbled screen.

Since I have no clue about how graphics drivers in general interact with Xorg, _any_ help would be appreciated.

Thanks.

EDIT AGAIN: just a note, trying to use this computer for LinuxMCE, which in its current stage (beta 2) only works with Intrepid.  Hence the issue to start with...

---

### Post by TrevT93 on 2009-12-22
EDIT: I decided to completely rewrite my first post, and included all of the information that used to be in this post in that first post.  Feel free to ignore this.

EDIT AGAIN: I did think of something I could occupy this space with: a little more information.  I don't know how much this helps, but when I first installed 8.10 on the computer, I had to use the Safe Graphics option on the disk's Mode menu.  Setting the Mode to "Normal" made it so that no screen would show up.

---

### Post by TrevT93 on 2009-12-23
Bumping this thread.  Again, any help appreciated.  Thanks.

---

### Post by TrevT93 on 2009-12-24
Daily bump.  I'd really like to get this server into use with this graphics adapter, but I need some help if I want to do that...

---

### Post by RedSingularity on 2009-12-24
Do you currently have fglrx installed?

---

### Post by TrevT93 on 2009-12-24
Thanks for replying, first off.

No, fglrx is not installed.  I used (... --purge fglrx*) last time to fully remove it from the machine.  I'm more or less done with fglrx, seeing that it had a problem with Intrepid to start with.  But if I could get the open-source drivers to work, I would be really appreciative.

---

### Post by RedSingularity on 2009-12-24
Good, dont use the FGLRX because i see that they are not compatible with your card. 

Post the output of 

lspci | grep VGA

---

### Post by TrevT93 on 2009-12-24
Huh?  Adept lists fglrx as supporting the 9500...

Anyway, the output:

```

01:00.0 VGA compatible controller: ATI Technologies Inc Radeon R300 NE [Radeon 9500 Pro]
```

---

### Post by RedSingularity on 2009-12-24
Just run this to make sure it is all uninstalled..........
[FONT=monospace]
[/FONT]sudo apt-get remove --purge xorg-driver-fglrx

Then do the following..........

sudo apt-get install xserver-xorg-video-radeon

---

### Post by TrevT93 on 2009-12-24
As I had expected, fglrx had been purged from the system, and xserver-xorg-video-radeon is already installed and at its latest version.

---

### Post by RedSingularity on 2009-12-24
Ok now can you boot to a graphical interface?

---

### Post by TrevT93 on 2009-12-24
Yeah.  "xserver-xorg-video-vesa" is installed, and that's the driver xorg.conf is using to make my system work.  Simply changing it to "radeon" makes the system not give me anything.  The screen just goes black, like the monitor's not picking up a signal (whenever the radeon driver is used, that is).

---

### Post by RedSingularity on 2009-12-24
Ok lets just see if this is installed.....

sudo apt-get install xserver-xorg-video-ati

---

### Post by TrevT93 on 2009-12-24
It wasn't.  But I've used this thing in the past, changing the xorg.conf driver line to "ati" and the same thing happens.

---

### Post by RedSingularity on 2009-12-24
Make your xorg file look like this.................


```
Section "Device"
        Identifier      "Radeon 9600"
        Driver          "ati"
        BusID           "PCI:1:0:0"
        Option          "XAANoOffscreenPixmaps"
EndSection
```

---

### Post by TrevT93 on 2009-12-24
Making the assumption that you want the "Screen" section's "Configured Video Device" to also change to the "Device" section's "Identifier" (in your case, you want both to say "Radeon 9600"...

Aaannnddd...screen goes black.  Not that I'm surprised.  Oh, and I forgot to mention, when this happens the keyboard also stops responding (Caps Lock/Num Lock lights don't light up when touched), so maybe there's something wrong with X?

---

### Post by RedSingularity on 2009-12-24
Ok, what happens if you add this to the xorg file?

```
Section "Screen"
        Identifier      "Default Screen"
        Device          "Radeon 9500"
        Monitor         "Generic Monitor"
        DefaultDepth    24
        SubSection "Display"
                Depth           24
                Modes           "1440x900" "1024x768"
        EndSubSection
EndSection
```

---

### Post by TrevT93 on 2009-12-24
Okay.  I'm going to change 1440x900 to 1280x1024 (that's my monitor's optimum resolution).

Aaannnddd...still black screen, keyboard still not working.

---

### Post by RedSingularity on 2009-12-24
And you experience these problems only when you use the "ati" driver?

---

### Post by TrevT93 on 2009-12-24
Well, that or radeon.  Yeah.  fglrx does even worse with the screens...and vesa actually works, but it's unaccelerated so it's not much use as a media server.

---

### Post by RedSingularity on 2009-12-24
Ok lets make a new xorg file.  Run this command to create a new file and if you can without too much trouble post the output of you xorg.conf file.

sudo xorgconfig

---

### Post by TrevT93 on 2009-12-24
Command not found.

(As a reminder, the machine is running Intrepid.  I don't know whether or not that makes a difference, but I thought it might.)

---

### Post by RedSingularity on 2009-12-24
Have you tried a newer version of Ubuntu on that machine yet?  Can you post the contents of your xorg file or are you typing on another computer?

---

### Post by TrevT93 on 2009-12-24
My laptop (Xubuntu Karmic) is what I'm using to post on the forums, and my media server is what I'm posting about.  But I'll give it a shot, hold on...

I can't seem to get Kubuntu Karmic to load the screen either.  What the heck is up with these graphics issues?  Is it possible this is another hardware issue?

The weird thing is that I KNOW that I was able to get a live copy of Karmic running on that computer earlier...

---

### Post by RedSingularity on 2009-12-24
It could be a hardware issue.......here try this command to reconfigure the xorg file.

sudo dpkg-reconfigure xserver-xorg

THen post an output of the file here if you can.

---

### Post by TrevT93 on 2009-12-24
Command not found, again.

---

### Post by RedSingularity on 2009-12-24
You are missing some major files then!  I suggest you reinstall the OS if you have the time.  The commands i gave you are basic ones and if the system cant find them then something is definitely wrong. :(

---

### Post by TrevT93 on 2009-12-24
Okay, well I'm reinstalling now.  After that's done I'll tell you what happens with the "dpkg-reconfigure" command

---

