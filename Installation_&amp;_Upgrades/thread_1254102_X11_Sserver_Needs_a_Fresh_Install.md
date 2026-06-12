---
title: "X11 Sserver Needs a Fresh Install"
date: 2009-08-30
forum: Installation &amp; Upgrades
---

### Post by rruarkjr on 2009-08-30
While trying to coerce my installation of Hardy to accept my Westinghouse LCD HD TV as a display monitor, I followed some advice concerning adding some ppa.* repository to my sources-list and then running an update.

The process of updating with this new repository caused some portions of my existing X11 installation to be removed. I am interested in learning how to properly re-install xserver. Any help will be greatly appreciated.

---

### Post by wojox on 2009-08-30
Are you sure it didn't just misconfigure your xorg.conf file?


```
sudo apt-get --reinstall install xserver-xorg xserver-xorg-core
```

---

### Post by inobe on 2009-08-31
> **rruarkjr said:**
> While trying to coerce my installation of Hardy to accept my Westinghouse LCD HD TV as a display monitor, I followed some advice concerning adding some ppa.* repository to my sources-list and then running an update.

The process of updating with this new repository caused some portions of my existing X11 installation to be removed. I am interested in learning how to properly re-install xserver. Any help will be greatly appreciated.

please include what version of ubuntu is installed and most important the repo you added ?


i will assume you added the avenard repo for nvidia drivers ?

if yes' you must add the correct repo that matches your distribution !

if the repo does not match the distro you are using' it will uninstall ubuntu desktop and xserver/ xorg

if this is the case' mistakes happen and can be easily fixed.

first do

```
sudo apt-get --reinstall install xserver-xorg xserver-xorg-core
```

then

```
sudo apt-get install ubuntu-desktop
```

to use the correct repo for avenard' be sure it matches your version of ubuntu.

for example

9.04 will appear like this **"notice it says jaunty"**

```
 echo "deb http://www.avenard.org/files/ubuntu-repos jaunty release" | sudo tee /etc/apt/sources.list.d/avenard.list

```

for 8.10 **"notice it says intrepid"**

```
echo "deb http://www.avenard.org/files/ubuntu-repos intrepid release" | sudo tee /etc/apt/sources.list.d/avenard.list
```

for 8.04 **"notice it says hardy"**

```
echo "deb http://www.avenard.org/files/ubuntu-repos hardy release" | sudo tee /etc/apt/sources.list.d/avenard.list
```

this is the place

[http://www.avenard.org/media/Ubuntu_Repository/Ubuntu_Repository.html](http://www.avenard.org/media/Ubuntu_Repository/Ubuntu_Repository.html)

---

### Post by rruarkjr on 2009-08-31
wojox: I had been playing with the xorg.conf file earlier, but I was at least able to get the server to display X windows at 600X800 resolution. It was only after adding the new repository and running update manager that I am now no longer able to get to even a login screen. The system displays an error message about me being stuck in "low resolution mode" and then locks up with no repsonse from either the keyboard or the mouse. Only recourse is to use the power button and reboot.

I will try your suggestion and let you know how it turns out. Please don't feel bad if i am a bit slow in responding, I only have access to these forums from home. My work does not allow us to visit blogs, forums, or external email addresses.

inobe: No. I don't have a dedicated graphics card. I have an HP Pavillion using the integrated graphics chipset on the motherboard. I don't recall the exact repository name, but it starts with ppa.* and I found the site from another forum that said this was the repository to use for X11 support for Ubuntu 7.04 thru 9.04 in addtion to the main supported repository. Once I can get back to the GUI, I can look the repository name up, unless you can give me the command to display this in dash?

In any event, thank you for your suggestions. I appreciate all the help I can get.


Russ

---

### Post by rruarkjr on 2009-08-31
wojox: I tried the reinstall and it seemed to go well, but the lock-up still exists. I am unable to get to a shell prompt with a network connection, so I can't grab things from my installed repositories, just from the packages on my PC. Or is this not correct?

inobe: Will your install command for ubuntu-desktop work without a network connection?

And to answer your original request, I am using Ubuntu 8.04 which I believe has a working name of Hardy Heron.

Russ

---

### Post by rruarkjr on 2009-08-31
wojox & inobe: I was able to activate my network connection and can now see all of the repositories in my sources-list. I issued the commands you both gave me. Both of those apt-get commands ran successfully and the appropriate packages were either installed or reinstalled. However, the problem must be deeper than this. I am still stuck at the warning screen where Hardy tells me that it could not find my graphics card and I will be using "low graphics mode". Unfortunately, once this message is displayed, the keyboard becomes unresponsive and the mouse cursor is frozen in the center of the screen.

Any guesses as to what I should try next?

---

### Post by rruarkjr on 2009-09-05
wojox, inobe, and anyone else reading this thread: I finally resorted to a full re-install of Ubuntu and can now at least get up and running at 600x800. I will continue to research ways to get the system beyond this resolution.

wojox & inobe: Thanks for all your help. I really appreciate how quickly you both jumped in to offer solutions to my problem. I will try to let you know what the ultimate resolution was for this issue.

---

### Post by rruarkjr on 2009-09-20
To All:
I am still searching for a solution for displaying Ubuntu 8.04 in a resolution greater that 600x800 on my HD TV.

Today I found a thread where the poster was having trouble with their display only showing half of the desktop. A part of the solution to this issue involved adding the following to the xorg.conf file:

SubSection "Display"
   Virtual 1024 768
EndSubSection

This was added to the "Screen" section of xorg.conf. When I applied this entry, the system would indeed boot with the keyboard and mouse active. However, the display was hopelessly garbled and pixelated.

After restoring my working xorg.conf file, my search continues. Is it possible that the chipset on my machine is incapable of displaying any higher resolution on the HDTV?

---

### Post by rruarkjr on 2009-09-20
Further documentation: I have now tried what I believe to be all of the available drivers for the chipset I have on the PC. When I view the Xorg.0.log file, I find that I have the Intel 915G chipset.

I have tried both the i810 and the intel drivers. The i810 driver will display an 640X480 screen, but says that all of the other resolutions (800x600 thru 1990x"something") either have a vertical refresh or horizontal sync value that is out of range. The intel driver can't even produce a working video display. The log shows that it tries to produce a 1024x768 screen, but all I get is a black screen that displays nothing. The keyboard is still active because I can CTRL+ALT+PF2 out to a terminal and issue commands there.

I have tried adding the allowable HorizSync and VertRefresh values to the xorg.conf file and I can get a login screen displayed in 1024x768, but once I enter my credentials, the screen goes black. I have also tried adding these values and adding a Modes entry for 1024x768 with similar results.

Is there something simple that I am missing, or is there just no way to get any driver except the vesa one to work with my Westinghouse SK-26H240S HD TV?

---

### Post by rruarkjr on 2009-09-29
Final Update:

I finally have a successfull conclusion to my problem of being stuck at 800x600 with the HD TV as a monitor.

It did boil down to an improperly configured xorg.conf file. After reading (and re-reading) the HOWTO's and a few threads on the forums, I ran cvt from terminal and got the proper modelines to plug into the Monitor section of my xorg.conf. I then used the Hsync and VertRefresh ranges given in the user manual for the HD TV to tell X what the allowable ranges were. I then added a Display subsection to the Screen section and defined my virtual display to be 1024 768 and told X to use either 800x600 or 1024x768 as modes.

I was still not getting a workable X display. I tried adjusting my xorg.conf to be sure that the mode names were the same in both the Monitor sections and the Display subsections, but nothing woearked when using the i810 driver. I was initially hesitant to use the intel driver, because my earlier experience (the one that led me to believe that I needed a re-install of X) was that the intel driver only produced a blank screen with allowing even a graphical logon. My final and working change to xorg.conf was to try the intel driver. Viola! It somehow now produced a working 1024x768 screen. Both the logon and the desktop now display at this resolution. It appears that I must have been missing one or more steps in my earlier attempts. Thanks and much appreciation must go to both wojox and inobe who were instrumental in getting me started down the right path and for their prompt response to my initial posting.

---

