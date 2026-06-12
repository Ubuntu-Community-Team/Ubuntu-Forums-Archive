---
title: "Nvidia card problems"
date: 2007-02-03
forum: Hardware &amp; Laptops
---

### Post by conradcliff on 2007-02-03
Alright, well, here's the story... I installed ubuntu while using an integrated graphics card, I now want to use an old nvidia gforce4 mx440 pci card but once ubuntu gets past it's loading screen everything goes blank. Any help would be great.
[edit] I've also just switched over to xfce but of course I'm still having the same problem...

---

### Post by Titus A Duxass on 2007-02-03
Have you disabled your on-board card in BIOS?
Then you need to run "sudo dpkg-reconfigure xorg-server that should get you up and running.  Do this from the command line if you can see the login prompt.
If you can't see the prompt do a "shift-alt-f1" and do it from there.

---

### Post by conradcliff on 2007-02-03
once I disable the on-board vid it only uses the card but it doesn't make it to the login promt...any ideas?

---

### Post by Titus A Duxass on 2007-02-03
As I said before do a "ctrl + Alt+f1" (correcting my error from the first post - sorry) that will get you to a command prompt.
Then do the reconfigure of the xserver.

---

### Post by conradcliff on 2007-02-03
Thank a ton, I'm going to try that now.

---

### Post by conradcliff on 2007-02-03
Well, cntrl-alt-f1 still left me with a blank screen so I logged in using the integrated vid to try and follow the steps neccessary in order to go through the process blind. Unfortunately while I'm logged in with the onboard and I try and use cntrl-alt-f1 I just get a ton of crazy video artifacts so I can't tell what's going on there either in order to see what steps I need to take. I tried running the "sudo dpkg-reconfigure xorg-server" and it gives me this:

tower@Employee-Computer:~$ sudo dpkg-reconfigure xorg-server
Password:
Package `xorg-server' is not installed and no info is available.
Use dpkg --info (= dpkg-deb --info) to examine archive files,
and dpkg --contents (= dpkg-deb --contents) to list their contents.
/usr/sbin/dpkg-reconfigure: xorg-server is not installed
tower@Employee-Computer:~$ 

I tried to install the 'xorg-server' from synaptic but it doesn't come up in the search. The only thing that comes up under xorg is the 'ATI binary X.Org driver' which of course is only for the ati chipsets. So at this point I'm kinda back to square one. Anymore help would be very appreciated...thanks.

---

### Post by conradcliff on 2007-02-03
Anybody else got any ideas?

---

### Post by RandomJoe on 2007-02-03
Actually, I'm working on this very problem right now.  Onboard Intel graphics, adding in an nVidia card, on a Dell GX150.

The problem is that apparently even if the BIOS is set to use the add-in card, X picks up the onboard chipset and as it has a lower PCI ID it is set default.  And, as you mention, if I switch the monitor to the onboard card the video is badly corrupted.

I am still in the process of installing Edgy (without the add-in card) but what I plan on doing - I think it'll work - is to set the BIOS to use the onboard video by default, boot with the add-in card installed but using the onboard video, then see what the PCI ID is for the add-in card.  Once I have that, I'll edit the xorg.conf file to properly use the add-in card, reboot, disable the onboard card and (if all goes well) everything works since X has been told to use a specific PCI ID...

I'll post what happens here...  But I'm still waiting for the inital raft of updates to finish... ;)

---

### Post by conradcliff on 2007-02-03
Sweet, I'll be waiting for your results...

---

### Post by RandomJoe on 2007-02-03
Yep, that worked!

Before installing the nVidia card I went into the BIOS and set "Primary Video ONBOARD".  Shut down, installed the card, rebooted.  Edgy used the onboard video card just as before.

Ran 'lspci' to get the PCI ID for the new card - you'll get a line like:
```
01:07.0 VGA compatible controller: nVidia Corporation NV18 [GeForce4 MX 440 AGP 8x] (rev c1)
```
The PCI BusID is therefore PCI:1:7:0.

Edit /etc/X11/xorg.conf. I use vim, which is tough to use if you aren't used to it, but it appears you can use gedit by running 'sudo gedit /etc/X11/xorg.conf'.  You need to replace the Device section, then edit the Screen section, as shown below:
```
#Section "Device"
#       Identifier      "Intel Corporation 82815 CGC [Chipset Graphics Controller]"
#       Driver          "i810"
#       BusID           "PCI:0:2:0"
#EndSection

Section "Device"
        Identifier      "nVidia"
        Driver          "nv"
        BusID           "PCI:1:7:0"
EndSection

Section "Monitor"
        Identifier      "DELL 1704FPV"
        Option          "DPMS"
EndSection

Section "Screen"
        Identifier      "Default Screen"
#       Device          "Intel Corporation 82815 CGC [Chipset Graphics Controller]"
        Device          "nVidia"
        Monitor         "DELL 1704FPV"
        DefaultDepth    24

```
I just commented out the original Device section for the Intel card since I now plan to set up dual-head.  It's also an easy way of having fallback in case something doesn't work...!

Add in the Device section for the nVidia card (the Identifier is just a name for elsewhere in the xorg.conf file, it can be anything).  The 'nv' driver is the default Xorg one, you can later replace it with the binary nvidia driver for hardware accel (once it has been installed).  And put the BusID from before in.

Finally, in the Screen section change the Device line to whatever you named your card.

I then rebooted, went into the BIOS and set the Primary Display to AUTO (no way to actually disable the onboard video here), switch the monitor to the new card, and it came up just fine.

---

### Post by RandomJoe on 2007-02-03
Spiffy - I just reenabled the onboard Intel, added the nVidia binary driver, and now have dual-head with hardware accel on the nVidia display.  First time I've successfully done that!  Tried it a while back with a different Dell system (GX200) that when nuts every time I tried to use the nVidia binary driver with both video outputs enabled...

If you do this, I found I had to re-set the BIOS so that Primary Display was ONBOARD again - otherwise, the Intel card put out garbage.  Fortunately, if you want the nVidia display to be "primary" in X, just list it that way in xorg.conf.  Even though the BIOS and bootup stuff happens on the Intel card, X will switch its login screen to the nVidia display once running.

Here's the final xorg.conf (relevant section) for my system, with the nVidia card as primary (Screen0):
```
Section "Device"
        Identifier      "Intel"
        Driver          "i810"
        BusID           "PCI:0:2:0"
EndSection

Section "Device"
        Identifier      "nVidia"
        Driver          "nvidia"
        BusID           "PCI:1:7:0"
EndSection

Section "Monitor"
        Identifier      "Dell"
        Option          "DPMS"
EndSection

Section "Monitor"
        Identifier      "ViewSonic"
        Option          "DPMS"
EndSection

Section "Screen"
        Identifier      "Screen0"
        Device          "nVidia"
        Monitor         "Dell"
        DefaultDepth    24
        SubSection "Display"
                Depth           24
                Modes           "1280x1024" "1024x768" "800x600" "720x400" "640x480"
        EndSubSection
EndSection

Section "Screen"
        Identifier      "Screen1"
        Device          "Intel"
        Monitor         "ViewSonic"
        DefaultDepth    24
        SubSection      "Display"
                Depth           24
                Modes           "1024x768" "800x600" "720x400" "640x480"
        EndSubSection
EndSection

Section "ServerLayout"
        Identifier      "Dual Head"
        Screen          0 "Screen0" 0 0
        Screen          1 "Screen1" rightof "Screen0"
        Option          "Xinerama" "true"
        InputDevice     "Generic Keyboard"
        InputDevice     "Configured Mouse"
        InputDevice     "stylus" "SendCoreEvents"
        InputDevice     "cursor" "SendCoreEvents"
        InputDevice     "eraser" "SendCoreEvents"
EndSection
```
I edited all the identifiers for easier reading - again, they are simply for referencing between xorg.conf sections and can be anything.

FWIW, I am hoping to get this thing working well on my "media PC" - to replace the 3GHz P4 that's currently there.  Less power, and I have better things for a P4 to do! ;)  The nVidia output will run the projector while I'll have a small monitor on the Intel output to use when playing music or other tasks I don't need the projector for.  Movies run a lot smoother on a hardware-accelerated display, thus the need for the binary nVidia driver.

---

### Post by conradcliff on 2007-02-04
Wow, excellent! Thanks so much for the info. I'm going to try it right now. I don't think I need to do the dualhead as this system only has one monitor, I would like to use the nvidia driver though. I've already installed it from synaptic so do I just need to change the 'nv' to 'nvidia'?

---

### Post by RandomJoe on 2007-02-04
Yes, that's it.

---

### Post by conradcliff on 2007-02-04
Well, it worked. Unfortunately the card has a strange sort of static it causes where it kind of blurs everything, I've seen the same thing once before on a win2k system. I was hoping that the nvidia driver would clear it up but once I set xorg to use it the video was chalk full of artifacts and it started crashing the system. I'm thinking that the card is the culprit so I'm gonna switch back to the integrated vid. Thanks for all the help, at least I learned something. :)

---

