---
title: "proplem in SAVING Nnvidia server setting"
date: 2009-12-25
forum: Hardware
---

### Post by dr.sehs on 2009-12-25
hello

i installed ubuntu 9.10 and i have nvidia fx5200 card and the driver is nvidea accelerated graphic driver 173 ... it's work perfect ..

first time i installed ubuntu ican't save the setting because the proplem of

Failed to parse existing X config file '/etc/X11/xorg.conf'!

and i follow these steps :
>  Open a terminal from Accessories>Terminal

Paste the following into the Terminal:

-----------------------------------------------------------------------
     sudo mv -i /etc/X11/xorg.conf /etc/X11/xorg.conf.backup
sudo touch /etc/X11/xorg.conf 

-----------------------------------------------------------------------
Hit Enter

-----------------------------------------------------------------------
Now paste:

     gksudo gedit /etc/X11/xorg.conf 
Hit Enter

-----------------------------------------------------------------------
Now paste the following into the file that opened:

     Section "Device"
    Identifier     "Configured Video Device"
    Driver         "nvidia"
EndSection 
press save at the top of that window
-----------------------------------------------------------------------
Now paste      
      sudo nvidia-settings 
---------------------------------------------------------------------
Hit Enter and highlight X Server Display Configuration
Press Save to X Configuration File

This time you should have a preview button you can view and save at the bottom.and every thing was alright and it work

now i change my monitor and i want to change resolution into 16080*1050 and when i follow the above setting an error appear in the terminal
> WARNING:  No Screen specified, constructing implicit screen section.



WARNING:  No Layout specified, constructing implicit layout section using screen "Default Screen".



WARNING:  Unable to find CorePointer in X configuration; attempting to add new CorePointer section.


WARNING:  The CorePointer device was not specified explicitly in the layout; using the first mouse device.



WARNING:  Unable to find CoreKeyboard in X configuration; attempting to add new CoreKeyboard section.


WARNING:  The CoreKeyboard device was not specified explicitly in the layout; using the first keyboard device.

and when i logout or restart the computer it return into the past resolution 1280*720

how i can make it save the new setting ?


thank's

---

### Post by MarkX on 2009-12-25
I'm trying to unsuccessfully fix the eternal wrong resolution problem on mine (a-bloody-gain...!) but stumbled on this thread which might help you:

[http://ubuntuforums.org/showthread.php?t=1101445&highlight=fx5200&page=1](http://ubuntuforums.org/showthread.php?t=1101445&highlight=fx5200&page=1)


It seems developers can't get their little heads around this repetitive bug and what happens when a monitor isn't properly recognised (like supplying a GUI where you can set ANY and ALL resolutions manually, DUH...). Instead of fixing it they just break it differently on various releases so noobs have to find NEW ways of repairing it after trying all the old ones that don't work any more. The "developers" of xorg should just go back to playing with their ZX81s and let people who can actually think do the coding.

---

### Post by dr.sehs on 2009-12-27
i can't believe that there is no solution for this problem

now each time i log into Ubuntu the first thing i do is changing the screen resolution ...


is there any solution that i can save my screen resolution ?

---

### Post by gradinaruvasile on 2009-12-27
> **dr.sehs said:**
> hello

i installed ubuntu 9.10 and i have nvidia fx5200 card and the driver is nvidea accelerated graphic driver 173 ... it's work perfect ..

first time i installed ubuntu ican't save the setting because the proplem of

Failed to parse existing X config file '/etc/X11/xorg.conf'!

and i follow these steps :
and every thing was alright and it work

now i change my monitor and i want to change resolution into 16080*1050 and when i follow the above setting an error appear in the terminal
and when i logout or restart the computer it return into the past resolution 1280*720

how i can make it save the new setting ?


thank's

There is a configuration utility called nvidia-xconfig. That will setup your xorg.conf, no need to copy-paste stuff that will work or not.
Open a terminal and launch it with sudo:

sudo nvidia-xconfig

It will setup your xorg.conf as needed.

As for the resolution problem, you have to launch nvidias screen configuration utility - nvidia-settings WITH SUDO:

sudo /usr/bin/nvidia-settings

Set you resolution, click "save to x configuration file". Check "merge with existing file".

---

### Post by bill olsen on 2009-12-27
Hi, I'm a newbie with a very similar problem, or maybe a host of problems

I'm running a brand new installation of karmic, 9.10 x64 with a GeForce 7600 GS, clean installed on a brand new hard drive (just a couple of days old).  
I have 2 ACER LCD screens.  One of the screens is new, but the rest of my hardware is a few years old.

I installed the NVIDIA accelerated graphics driver (version 185 as recommended).
I clumsily sorted out the issue that I forgot to plug power into the card, and I may have messed up something along that way.

After reboot, I soon encountered the problem that the NVIDIA X Server Settings 
utility could not write the xorg.conf file.  It gave the error message:

     Failed to parse existing X config file '/etc/x11/xorg.conf

I determined that I had a very incomplete /etc/xorg.conf, and I finally repaired it with 
your helpful advice to run:

     /etc/X11$ sudo nvidia-xconfig
then
     /etc/X11$ sudo nvidia-settings

Then I was able to click "save to x configuration file". Check "merge with existing file",
without error.

However, when I reboot, I still get  
    Only one screen 
    That screen is at the wrong resolution.

I've tried so many permutations, that I'm losing track of what might have worked
earlier.  In case it may be relevant, I should mention that I also want to get *one* of the screens to rotate, and haven't made progress, and that I don't seem to have Xinerama?  But I will put those problems off to another thread after I solve this one.

Thanks for any ideas.
Bill

---

### Post by bpalone on 2009-12-27
I had a similar issue just yesterday.  I ended up having the GUI NVIDIA X server settings app save the file to my home directory and using the command line to "sudo cp filename_I_saved_it_as /etc/X11/xorg.conf".  This cured the problem of not being able to save it.

Hope that helps.

---

### Post by bill olsen on 2009-12-27
Amazingly, this last time worked: I re-started and got both screens at the correct resolution.  The only change that I made was (following the earlier post by [gradinaruvasile]("http://ubuntuforums.org/member.php?u=589640") (thanks again!)  I lauched the NVIDIA utility with

/etc/X11$ sudo /usr/bin/nvidia-settings

instead of this earlier try that didn't seem to work:

/etc/X11$ sudo nvidia-settings

Everything seems to behave identically either way, so I assumed that therewas no difference in the result.  But it seems that there was a difference.:confused:

---

