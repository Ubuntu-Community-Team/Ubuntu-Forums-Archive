---
title: "Trouble installing"
date: 2009-06-11
forum: Installation &amp; Upgrades
---

### Post by thewang767 on 2009-06-11
Hi,

I am installing Ubuntu from the Alternate CD because my system has 256MB of RAM. It also has a Nvidia graphics card.

After I installed, the first time the login screen would not display, and instead I would get a black screen. The next time I entered the command line and input:
```
sudo apt-get install nvidia-glx-96
```
I continued to boot normally, and this time I got a login screen, however my keyboard and mouse would not work. I also tried:
```
sudo dpkg-reconfigure xserver-xorg
```
Then I got a message saying "Ubuntu is running in low graphics mode," and my keyboard and mouse still would not work.

Is there a fix for this? Everywhere I've looked to install Nvidia drivers already assume you can log in, which I can't.

---

### Post by LepeKaname on 2009-06-12
maybe try other nvidia driver. Can you post your xorg.conf? what model of card and computer you have? 
Use driver "vesa" for now... until you can fix this problem.

---

### Post by thewang767 on 2009-06-12
What do you mean by "post your xorg.conf?" I can't log in to Ubuntu or see the GUI (actually, I think it may display now, but my keyboard/mouse do not work).
I'm using an old system from around 2002. I can find the card model when I get home.
> Use driver "vesa" for nowDo you mean to use```
sudo apt-get install vesa
```

---

### Post by dstew on 2009-06-12
What version of Ubuntu did you install? If it is 9.04, you can try the **xfix** command from the command line. Hopefully you can get a user interface that will let you use the mouse and keyboard.

If you get an interface, you can go to the System --> Administration --> Hardware drivers menu to see if there is a restricted driver available for the care. You might need to activate the Multiverse repository (System --> Administration --> Software Sources).

---

### Post by thewang767 on 2009-06-13
The graphics card I am running is a Nvidia GeForce2 MX/MX400. I'm assuming I will have to download the Nvidia drivers manually after I install Ubuntu? What would be the correct commands to do that?

Whenever the GUI loads up, the Num Lock light on my keyboard goes off.

---

### Post by LepeKaname on 2009-06-13
Install these packages:  

"sudo aptitude install nvidia-glx-96" 
"sudo aptitude install nvidia-96-modaliases" (recommended)

Try first: "sudo nvidia-xconfig"

If doesn't work, try using this xorg.conf:

```

Section "ServerLayout"
    Identifier     "Layout0"
    Screen      0  "Screen0"
EndSection

Section "Module"
    Load           "dbe"
    Load           "extmod"
    Load           "type1"
    Load           "freetype"
    Load           "glx"
EndSection

Section "Monitor"
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "Unknown"
    HorizSync       30.0 - 110.0
    VertRefresh     50.0 - 150.0
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
    SubSection     "Display"
        Depth       24
        Modes      "1024x768" "800x600" "640x480"
    EndSubSection
    Option "AllowGLXWithComposite" "True"
    Option "AddARGBGLXVisuals" "True"
EndSection

Section "Extensions"
    Option "Composite" "Enabled"
EndSection

```

Just adjust the HorizSync and VertRefresh of your monitor.

Should work.

---

### Post by thewang767 on 2009-06-15
Hi, sorry again. I tried the two nvidia commands, however "sudo nvidia-xconfig" does not work. How do I edit the xorg.conf? There is no graphical display, and how would I get to xorg.conf? Thanks.

---

### Post by LinuxGuy1234 on 2009-06-15
You can get to the xorg.conf file using:
```
sudo nano /etc/X11/xorg.conf
```
Remember, when a command in nano has a ^, you need to push Ctrl (or Control) and then the letter it says. For example, to quit nano, use Ctrl-Q.

---

