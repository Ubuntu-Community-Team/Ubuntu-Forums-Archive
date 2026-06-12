---
title: "Urgent help needed after NVIDIA driver update on 14.04"
date: 2014-07-25
forum: Hardware
---

### Post by WB0HYQ on 2014-07-25
I did an update on my newly upgraded 12.04 to 14.04 Ubuntu system, installing the proper driver for my NVIDIA GeForce 8400GS card.

what I did -->  downloaded NVIDIA-Lunux-x86_64-340.24.run (and made it executable)
------------> then I went into a fullscreen Terminal and entered "sudo service lightdm stop"
------------> then I ran the command "sudo sh NVIDIA-Linuxx86_64-340.24.run"
--
-- I got the Dos-like screen that installed the new driver with no apparent errors at all.  When it was done, I rebooted using the 'shutdown -r' command.

When the computer came back up, it got a VERY brief message that I think said something about X-whatever and then it was replaced by a login prompt.  The font used was very tiny which supported the idea that the driver installed correctly as the former terminal used a much larger font.

I entered Ctrl-Alt-F7 to return to the GUI, but nothing happened.  There was a brief bit of disk activity and then that stopped.  No GUI, no nothing.

I can go back and forth from the blank screen to Terminal mode again so at least that part works.  What I need to do now is get some help on getting back my GUI.  How do I do that?

Bill

---

### Post by WB0HYQ on 2014-07-25
More information:

I ran the command "sudo sh NVIDIA-Lunux-x86_64-340.24.run --uninstall" and it apparently uninstalled.  Just before it did that, I was asked if I wanted to try and recover my last set of drivers.  I said yes and let it uninstall.

When that was done, a reboot gave me the same thing as before.  I can get into Terminal using Ctrl-Alt-F2, but when I try Ctrl-Alt-F7 I get the blank screen.

Does this mean that something ina config file needs to be tweaked?  If so, which file?  I suspect is had to to with starting my X-server, but I don't know how to do that.

Bill

---

### Post by grahammechanical on 2014-07-25
You could try recovery mode. In 14.04 we find recovery under the Advanced Options for Ubuntu sub-menu. Select Resume. That may get you to a desktop using a fall back open source video driver.

At the desktop you can experiment with video drivers in System Settings>Software and Updates>Additional Drivers tab. You might find that Nouveau does all you need or that the Nvidia drivers being offered officially are also suitable. You need to be connected to the internet and to allow the utility a little time to find the available drivers.

Edit: Just a point about your method for installing a proprietary video driver downloaded from the manufacturers website. This command is correct and used in the right place (I think)

```
sudo service lightdm stop
```

but you do not mention running this command

```
sudo service lightdm start
```

That command, I understand, also needs to be run after the driver has been installed.

Regards.

---

### Post by WB0HYQ on 2014-07-25
Okay.  Last bit of info before I give up and sleep on it overnight.

I have tried the recovery mode (in the boot menu) and tried the option to run with a 'standard' video driver.  That give me a loop back to the initial screen asking which method of boot do I want.  No help there.  I tried several of the older kernels and none of them worked either (same bootup sequence and then - nothing - black screen.  I did notice that during the very rapid loop after choosing 'use a standard video driver' that there was some text that appeared at the speed of light and got immediately replaced by the "what boot type do you want to do" screen.

It took me many, many loops to get it all down (even using the Scroll Lock key) and here it is:

Quote:  
zenity: error while loading shared libraries: libGL.so.1: cannot open shared object file: no such file or directory ((this repeats twice) 
EndQuote

and then I get:

Quote: xinit: connections to X server lost
waiting for X server to shutdown error setting MTRR (base-0xcf000000 size=0x00e00000, type=1) invalid argument (22)
(EE) server terminated successfully (0). closing log file.
EndQuote

I am still able to get a Terminal so there is SOMETHING running there, but I haven't a clue what it is other than the system minus a graphical interface.

So, how do I get the graphical interface kickstarted and back into operation.  I have a feeling that my uninstall command actually did uninstall the NVIDIA driver so how do I get back the video driver I had before my driver upgrade effort failed?  I feel certain that there are commands I can issue that will do that but I do NOT know what they are so how about just a little help here'?

Bill

---

### Post by WB0HYQ on 2014-07-25
Thanks for the reply -LM-.  My efforts with the advanced options are what I just posted.  I was never able to get to any type of desktop at all.  I did try issuing the 'lightdm' service start command, but nothing happened afterwards.

EDIT:  tried the start command again and got "lightdm is already running"

Bill

---

### Post by WB0HYQ on 2014-07-25
Oh, man.  Now I do feel really red-faced.  I got to thinking and just for the heck of it I gave the command:

sudo apt-get install ubuntu-desktop && sudo apt-get install -f

When that was finished, I rebooted.

I now have my desktop back, at my default resolution of 1600x900, and all is well now.

All of this goes to show that if it isn't really broken, don't mess with it.  I wanted a little sharper picture and also do some programming with OpenGL so I went on my quest for a new driver.  A couple of NVIDIA drivers (of lesser version numbers than 340.24) are in the Additional Drivers application, but, for now I'm not trying a single one of them.  I'm using the 'standard' driver and the resolution is fine.

I always seem to be fixing my own stuff, but airing laundry here.  I wonder why that is.  :-)

Now, if I can just fix the "stackframe / loadparm / leaking memory" error when I start a terminal I will be happy.

Bill

---

