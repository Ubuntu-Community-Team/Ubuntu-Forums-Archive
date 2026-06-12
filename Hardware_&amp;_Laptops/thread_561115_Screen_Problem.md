---
title: "Screen Problem"
date: 2007-09-27
forum: Hardware &amp; Laptops
---

### Post by tasomaniac on 2007-09-27
I have Gateway CX210X tablet PC. When I try to install UBUNTU, I get a problem that says there is a problem with X.org server. Screen not found etc. Please help me. I wanna use UBUNTU. But when such problems occurs, I become estranged.:(

---

### Post by w4ett on 2007-09-27
I'd start by reconfiguring your xorg.conf.....boot into recovery mode.

From the command line type:
```
Login
```
you will be prompted to enter your user name and password

```
sudo dpkg-reconfigure -phigh xserver-xorg
```

This will give you the interface to modify the driver and resolutions. Controls are UP and DOWN cursor keys move the cursor and scrolls through available options, the space selects options, and <enter> confirms selections.

Select [COLOR="Red"]"vesa"[/COLOR] as the driver and press <enter>, then at the next screen you can enable any addttional resolutions that you want to use.....then use the cursor keys to highlight {OK} and <spacebar> to select the resolutions and press <enter> to save the selections as prompted, then type:


```
startx
```

This should  get you to a GUI desktop.

---

### Post by PizzaHog on 2007-09-27
I have a similar problem - but when I follow the above instructions, I'm not able to change to "vesa" just to specific resolutions.  One of the resolutions available, that is also the native resolution of my Dell Vostro 1500 screen, is 1680x1050.  However, selecting any resolution doesn't seem to "stick", and it seems to default to the lowest 3 resolutions.  

But I still can't get past the command prompt.  I'm obviously not entering the correct command(s) to be able to edit the /etc/x11/xorg.conf file - I know it's there, I just can't get to it... 

Additional info:
[LIST]
[*]I am running 7.04, freshly installed (several times) last night
[*]I'm getting " Fatal server error  no screens found" and "cannot open display" 
[*]Also getting: "(EE) N(0): No display devices found" and "(EE) Screen(s) found, but none have a usable configuration.
[*]I can't figure out how to edit the xorg.conf file from a prompt
[/LIST]

Sounds like Ubuntu can't see the vidcard...?

Help!  Frustration levels approaching critical!:(

---

### Post by w4ett on 2007-09-27
to edit your xorg.conf from cli:

```
sudo nano /etc/X11/xorg.conf
```

---

### Post by PizzaHog on 2007-09-27
My xorg.conf file is blank?!

At least, that's what shows when I open it per the above post.  (Thanks by the way!)

So, now that I'm in the silly thing, what is it supposed to say?  

When I threw a random line in (linux vga=771) it wouldn't let me save the file: "No such file or directory".

????

(edit: the laptop has an nVidia 8400 series vidcard)

---

### Post by w4ett on 2007-09-27
Sorry...I made a typo.... :(

```
sudo nano /etc/X11/xorg.conf
```

It's a capital X......

---

### Post by PizzaHog on 2007-09-28
Heh.  I'm such a n00b, I didn't realize that it mattered...

So, now that I'm into the file (thanks again!), I think I understand what I'm looking at, but I want to make sure before I really screw things up.

Now it's a screen resolution issue.  I'll get it right, somehow...bloody drivers.

---

### Post by tasomaniac on 2007-09-28
I did this but it still says screen not found. In addition I write " sudo nano /etc/X11/xorg.conf" and I didn't understand anything. Help!

---

### Post by PizzaHog on 2007-09-28
OK - this is what I have so far:
[LIST=1]
[*]sudo nano /etc/X11/xorg.conf
[*]scroll down until you start seeing things that look like they describe your video card
[*]Something will say " Device" and "Identifier".  Change whatever is there to "default card"
[*]Change driver to "vesa" (edit: this used to say vga)
[*]Change the "Depth" to "8"
[/LIST]

If the vidcard errors pop up (they keep doing so in mine), scroll the cursor up or down, then back where you want to work on the file - the errors aren't really being displayed in the file.

There are a couple of other instances (lower in the file) in which Ubuntu tries to identify the vidcard - change them to "default card" too.

Save the file, get back to the prompt.  

When I did "startx" I went in on a low-permission account, and updates were prohibited.  "sudo startx" seemed to be the key here.

When the GUI fires up, it's at 300x200 @140 Hz refresh.  Very tough to do anything.  I haven't figured out how to change this - there were no Dell Ubuntu vidcard drivers available on their website to install.

BUT! -when you click on the upper right-hand corner of the screen (where the Update Manager displays it's little orange "star" under normal circumstances) you indeed get the Update Manager.  But the tool bar across the bottom edge gets in the way, keeping you from doing anything useful.

Blindly hit the Enter key.  This should start the update process.

When the "Downloading package files" window opens, right click on the upper-left of the window - on the Window Menu icon.  Select "Always on Top."  This will give you enough screen space to see how the downloads are progressing.

I got a message saying that some packages couldn't be downloaded.  I blindly hit Enter again, and the actual installation began.

***This didn't actually accomplish anything.  The display is still hosed, but I'm updated...:p

Trying out how to install nVidia's Linux drivers...

---

### Post by w4ett on 2007-09-28
System>Administration>Restricted Driver Manager is the 7.04 Feisty Fawn method...but:

There are three ways to install the restricted drivers for your card:

1. Use the restricted drivers manager in Ubuntu, System.>Administration>Restricted Driver Manager.[COLOR="Blue"] (try this option first)[/COLOR]

2. Use an installation script called Envy: [http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html) ( this is MY preferred method because it uses the most up to date driver)

3. Compile your own driver modules from Nvidia: [http://www.nvidia.com/object/unix.html](http://www.nvidia.com/object/unix.html)

To use Envy,  navigate to:

[http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)

Install envy and then from the terminal type:


```
sudo envy -t
```

This will run the installation script from the terminal....follow the instructions to  install the correct Nvidia proprietary driver.

Good Luck

---

### Post by PizzaHog on 2007-09-28
The problem is the screen resolution - I can't get it higher than 300x200, so the windows are unreadable.

I can open a terminal.  But I'm not that experienced at doing command-line stuff.

:confused:

---

### Post by PizzaHog on 2007-09-28
It turns out that the Dell laptop has a proprietary version of the nVidia 8400m - the nVidia driver won't install - it has to be Dell's flavor of the driver.  Nuts.

The restricted drivers manager can't find any hardware that needs restricted drivers.  So, that option doesn't work.

I downloaded Envy, but it can't get all the files it needs to install - though the laptop is connected to the 'Net.  I have the Ubuntu install CD (actually, the Alternate disk, as the regular won't install on a WinXP laptop) in the drive.

I can't get the nVidia Linux driver to install.  Again, I can't see the windows.

Essentially, without some inspiration on how to increase screen resolution, this install is dead in the water.  At 300x200, everything is simply too big to display on the screen - heck, the File Browser is even unusable.

> **w4ett said:**
> System>Administration>Restricted Driver Manager is the 7.04 Feisty Fawn method...but:

There are three ways to install the restricted drivers for your card:

1. Use the restricted drivers manager in Ubuntu, System.>Administration>Restricted Driver Manager.[COLOR="Blue"] (try this option first)[/COLOR]

2. Use an installation script called Envy: [http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html) ( this is MY preferred method because it uses the most up to date driver)

3. Compile your own driver modules from Nvidia: [http://www.nvidia.com/object/unix.html](http://www.nvidia.com/object/unix.html)

To use Envy,  navigate to:

[http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)

Install envy and then from the terminal type:


```
sudo envy -t
```

This will run the installation script from the terminal....follow the instructions to  install the correct Nvidia proprietary driver.

Good Luck

---

### Post by PizzaHog on 2007-09-29
[http://ubuntuforums.org/showthread.php?t=521753](http://ubuntuforums.org/showthread.php?t=521753)

...has some promising info and suggestions.

---

### Post by PizzaHog on 2007-09-29
The above link had the answers to all of my issues, and I'm up and running.  Thanks for all of your help!

PH

---

### Post by tasomaniac on 2007-09-30
I haven't get my answer yet unfortunately. Please help. My graphic card is ATI Mobility Radeon X1400. I select "vesa" it doesnt work. I select "ati" it also doesnt work. When I write "startx", it says screen not found.

---

