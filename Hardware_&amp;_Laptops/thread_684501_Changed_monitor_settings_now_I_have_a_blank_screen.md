---
title: "Changed monitor settings now I have a blank screen."
date: 2008-02-01
forum: Hardware &amp; Laptops
---

### Post by Sk1nnyMan on 2008-02-01
Hey 

First of all here is my hardware configuration.

Intel Core Processor
ASUS SLI motherboard
2x XFX 8800GTX
4GB RAM

Yesterday I had a perfectly working 32 bit Ubuntu 7.10 installation running from my hard disk with the above hardware, the only problem was that the highest resolution I could go to was 1024x768 and I wanted to take it up to 1280x1024. 

First of all I went into the Administration > Screen Resolution and saw that highest value I could go to for my monitor was 1024x768 (my monitor is built to go higher) and I noticed that the monitor it had selected in that menu was "Custom Monitor", I changed the "Custom Monitor" with the drop down menu to "1280 Monitor" and hit OK, I then restarted the computer.

When I restarted I tried loading Ubuntu as I normally would, the progress bar completed and the screen became blank then a console output showed up saying “running local boot scripts” before the screen then went blank again for a moment then the same console output appeared again, this repeated twice more (a total of three times) before the screen became blank permanently, forcing a restart.

In an attempt to fix it I logged on and pressed Ctrl-Alt-F1 and tried the “sudo dpgk-reconfiqure xserver-xorg” command, allowing it to automatically detect all my settings (I selected the “nv” driver), rebooted, and tried booting again with similar results.

I was also able to recreate the problem by attempting to load gdm when I was in the command line.

Right now I cannot get into the “main” command line using the “Ctrl-Alt-F1” command I can however get into the Recovery mode command line.

Attached should be a copy of my xorg.conf file that I grabbed from my Vista install (I dual boot), I had to convert it to xorg.conf.txt to get in to attach.

Any help would be appreciated, I don't want to have to scrap the whole install over this stuff.

Thanks

Sk1nnyman

---

### Post by oldsoundguy on 2008-02-01
what is the video card?

---

### Post by Sk1nnyMan on 2008-02-01
I have 2 8800GTXs in SLI.

---

### Post by smurphy_it on 2008-02-01
There is only one entry for a video card in your xorg file, and it lists the BusID as 10.0.0, which is quite high in my opinion, but may work.... You could try commenting out that line to see if it will load properly.

Could always try reconfiguring again with dpkg (if you have see with ctrl-alt-F1), or try changing the video driver from "nv" to "vesa".

---

### Post by Yellow Pasque on 2008-02-01
> There is only one entry for a video card in your xorg file, and it lists the BusID as 10.0.0, which is quite high in my opinion, but may work.... You could try commenting out that line to see if it will load properly.
Instead of guessing at the BusID, run this command to make sure:
```
sudo update-pciids; lspci | grep VGA
```

You'll also need to install the nvidia proprietary drivers (nvidia-glx-new in Synaptic) if you have not already. To use the proprietary drivers, you need to make sure the 'driver' line in the Device section says "nvidia", not "nv"
Also, what model of monitor do you have?

---

### Post by makilgore06 on 2008-02-01
I am experiencing this same problem except I am running a
Dell Insprion 1720
nVidia GeForce Go 8400M (maybe 8600M but they use the same driver)
17" generic LCD monitor.
2.5GB RAM
2.0GHZ Intel Core Duo Processor

Here is a rough and incomplete account of what I did:
I tried to install the propietary drivers when Ubuntu boots the first time and they didn't work so I had to uncheck that box.  Then I tried to install the nividia-glx-new and it did not work either, even when I selected the nVidia (not vesa or nv) driver.  I did not know about ctrl+alt+f1 as I'm a noob, but at least this will allow me back in to my filesystem.  

The bottom line is that the default install version of Gutsy from the live-cd (which I'm running right now with no hiccups) works, and I need to make my install like it previously was without losing any data that I have stored on the box (all or most major packages and personal files).  Any tips?
(note I can either get everything off the hd and reinstall, or get the files i need to correct this back to default)


mike

---

### Post by Sk1nnyMan on 2008-02-01
> **Temüjin said:**
> 
Also, what model of monitor do you have?

My monitor is a 19" LG Flatron L1952S

---

### Post by Sk1nnyMan on 2008-02-01
FIXED IT:guitar::guitar::popcorn::popcorn:

Here is what I did:

First of all I did the "sudo dpkg-reconfigure xserver-xorg" command from Ubuntu recovery mode setting the driver to nvidia and letting the program automatically select all the other values.

This allowed me to reboot and hit "Ctrl-Alt-F1" which gave me access the full command line where I used syn-apt to download the  lspci app that gave me the PCI address of my video cards, I then ran the "sudo dpkg-reconfigure xserver-xorg" again and specified the PCI address of the first video card it found and rebooted to the full GUI.

As an interesting side effect I can now set Ubuntu to run at 1280x1024 for the duration of a session, the changes are lost when I reboot though, but I would rather have a lower resolution GUI than a command line only one (that being said the Command line of Unix like system rules).

A HUGE thanks to everyone who helped, I was not looking forward to doing a full reinstall, (although it would have let me have a look at 64 bit Ubuntu:)).

---

### Post by Yellow Pasque on 2008-02-01
Glad to hear it's fixed. Could you mark the thread solved to let people know? Thanks

---

