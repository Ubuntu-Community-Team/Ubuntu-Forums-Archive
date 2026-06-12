---
title: "Using external monitor on my laptop"
date: 2007-08-10
forum: Hardware &amp; Laptops
---

### Post by RezDuane on 2007-08-10
I have an HP Pavilion zv6000 which I finally got my wireless and other little items working. Now I want to plug in my Samsung monitor. So far, no luck. Well I did get it to work a couple of times but mostly if I boot up with the monitor connected, the screen goes blank at the login screen.  I found I can actually log in but I still get nothing on the laptop screen or monitor. I boot up and then plug in the monitor and once a blue moon it will work. Any suggestions?

BTW, I'm running Feisty

---

### Post by KyleBrandt on 2007-08-10
Graphics Card? The output of "lspci" in terminal can help you find this information.  There are a couple options for dual head on linux, see: [http://ubuntuforums.org/showthread.php?t=221174](http://ubuntuforums.org/showthread.php?t=221174)
I don't find any of them to have worked all that smoothly for myself.  If you boot up with the monitor plugged in, and there is output on the monitor but not the laptop--you can unplug the monitor and restart the x server to switch back to the laptop screen (Maybe): ctrl-alt-backspace. This will kill the applications currently running however.

---

### Post by RezDuane on 2007-08-10
This is what I get from lspci concerning my VGA controler:

01:05.0 VGA compatible controller: ATI Technologies Inc ATI Radeon XPRESS 200M 5955 (PCIE)

I'll check out the other you sent also.

Thanks!

---

### Post by Beuntje on 2007-08-10
I was having the same issues with an external monitor.
At last I got it to work.

Before you Begin
If you've just installed Ubuntu, you will have noticed that it's working on your laptop's monitor, but not on the external monitor. (If you press the appropriate buttons on the laptop, you might be able to switch between the two, but it will always be one or the other.) The first thing you should do is take a backup of your existing xorg.conf file, and name it xorg.justlaptop.prod1. This will become the configuration file you'll be using when you boot up with just the laptop's screen. You shouldn't have to make any further changes to it; X did all the work for you.

From this point on, the rest of this article will be describing the changes you need to make to xorg.conf to get it working with both of your monitors, so make sure that you have your external monitor plugged into the laptop.

Editing the File
If you haven't already, you should read the X Window Configuration article, on how to edit the xorg.conf file — especially the sections on making a backup copy!

There are various pieces of xorg.conf having to do with display. Here are the pieces you will need to edit in yours — each of which will be described in more detail below:

One Device for every video card — or virtual video card — that the system has 
One Monitor for every physical monitor the system has 
One Screen for every Monitor 
A ServerLayout section 
There are also some ServerFlags you need. 
Video Card
The first thing you'll have to do is set up a Device section for your video card(s). This was the tricky part, for a laptop, because you actually have to create two device sections, one for each head on the video card.

Generically, a Device section for a video card should look like this:

> Section "Device"
    Identifier    "NAME YOU'RE GIVING THE CARD"
    Driver        "DRIVER"
    BusID        "BUS LOCATION"
    Option        "OPTION" "OPTION VALUE"
    Screen        NUMBER OF THE MONITOR, STARTING AT 0
EndSection

If you install Ubuntu on a laptop, you will probably just have one Device created for your video card, even though it has two “heads.” Also, it won't have all of the options you need, for running multiple monitors. So you'll have to fill it out, and create a second section.

Here's what it looks like on my laptop, which is a Dell Latitude D610:

> Section "Device"
    Identifier    "Intel Graphics Controller"
    Driver        "i810"
    BusID        "PCI:0:2:0"
    Option        "VBERestore" "true"
    Option        "DRI" "true"
    Option        "SWCursor" "true"
    Option        "MonitorLayout" "CRT,LFP"
    Option        "CloneRefresh" "85"
    Screen        0
EndSection

Section "Device"
    Identifier    "Intel Graphics Controller 2"
    Driver        "i810"
    BusID        "PCI:0:2:0"
    Option        "Display" "CRT"
    Option        "MonitorLayout" "CRT,LFP"
    Screen        1
EndSection

The first one is the head for the video card which will run the laptop's LCD screen, and the second is for the external monitor. The key points for this section are:

The Identifier must be unique for each “head” 
You'll need to make sure you have the right driver for your card; whichever one was filled in for you was probably the right one, so use it when you create your second Device section. 
You'll notice, in my example, that the BusID is actually the same for both entries 
Most of the other entries I got from examples on the internet; I don't understand it all.

Monitor
Now that you have your two Device sections, you need two Monitor sections. Again, the xorg.conf file that was created for you probably only has one of these sections, so you'll have to create the second one from scratch. Luckily, the Monitor section is normally pretty easy to fill in. It looks like this:

> Section "Monitor"
    Identifier    "UNIQUE NAME"
    Option        "OPTION" "VALUE"
EndSection

On my computer, it looks like this:

> Section "Monitor"
    Identifier    "Generic Monitor"
    Option        "DPMS"
EndSection

Section "Monitor"
    Identifier    "External Monitor"
    Option        "DPMS"
EndSection

Again, the first section is for the laptop's LCD screen, and the second for the external CRT.

Some notes on this section:

There are actually a lot of options you can specify for a monitor, for things like refresh rate and size and a billion other things. I don't normally specify any of them, because X can figure most of that out on its own. (For example, if you get the refresh rate wrong, your monitor can flicker badly, which hurts your eyes; but if you don't specify anything for the refresh rate, X seems to be able to figure out the best refresh rate to use, for your monitor.) 
I don't know what the DPMS option is, but it works, and the examples all have it, so I included it… 
Screen
For each “Monitor” you've defined, you also need to define a “Screen,” using the Screen section. The Monitor section describes the hardware, the Screen section outlines how you want the display to work.

The section looks like this:

> Section "Screen"
    Identifier    "UNIQUE NAME"
    Device        "NAME OF VIDEO CARD DEVICE"
    Monitor        "NAME OF MONITOR"
    DefaultDepth    DEFAULT DEPTH NUMBER
    SubSection "Display"
        Depth        DEPTH NUMBER
        Modes        "SCREEN RESOLUTION", "LOWER SCREEN RESOLUTION", "ETC."
    EndSubSection
EndSection

Just as with the previous two sections, your initial xorg.conf will only have one of these sections, so you'll have to create the second one from scratch. On my machine, it looks like this:

> Section "Screen"
    Identifier    "Default Screen"
    Device        "Intel Graphics Controller"
    Monitor        "Generic Monitor"
    DefaultDepth    24
    SubSection "Display"
        Depth        1
        Modes        "1024x768"
    EndSubSection
    SubSection "Display"
        Depth        4
        Modes        "1024x768"
    EndSubSection
    SubSection "Display"
        Depth        8
        Modes        "1024x768"
    EndSubSection
    SubSection "Display"
        Depth        15
        Modes        "1024x768"
    EndSubSection
    SubSection "Display"
        Depth        16
        Modes        "1024x768"
    EndSubSection
    SubSection "Display"
        Depth        24
        Modes        "1024x768"
    EndSubSection
EndSection

Section "Screen"
    Identifier    "External Screen"
    Device        "Intel Graphics Controller 2"
    Monitor        "External Monitor"
    DefaultDepth    24
    SubSection "Display"
        Depth        1
        Modes        "1280x1024" "1024x768"
    EndSubSection
    SubSection "Display"
        Depth        4
        Modes        "1280x1024" "1024x768"
    EndSubSection
    SubSection "Display"
        Depth        8
        Modes        "1280x1024" "1024x768"
    EndSubSection
    SubSection "Display"
        Depth        15
        Modes        "1280x1024" "1024x768"
    EndSubSection
    SubSection "Display"
        Depth        16
        Modes        "1280x1024" "1024x768"
    EndSubSection
    SubSection "Display"
        Depth        24
        Modes        "1280x1024" "1024x768"
    EndSubSection
EndSection

As with the two previous sections, I've put the laptop screen first, and the external one second.

Some notes on this section:

Note that the Device and Monitor settings are referring back to the names you defined earlier. 
You can include as many Display subsections as you want. For the files generated automatically by tools, I always get 6 entries, as above, that are all identical. A lot of examples I've seen on the net simply have one, with the number 24. 
On a related note, the DefaultDepth setting must be the same as one of the Depth identifiers. Every example I've ever seen has been set to 24. 
Server Layout
The Server Layout ties it all together. The xorg.conf man page says that you can have multiple ServerLayout sections, and gives some rules as to which one will be used. However, we'll just have one in each xorg.conf file that we use.

This section looks like this:

> Section "ServerLayout"
    Identifier    "UNIQUE IDENTIFIER"
    Screen        "SCREEN NAME"
    Option        "OPTION" "VALUE"
    InputDevice    "INPUT DEVICE IDENTIFIER"
EndSection

For example, on my laptop, for my two-screen configuration, it looks like this:

> Section "ServerLayout"
    Identifier    "Two Screen Layout"
    Screen        0 "Default Screen" 0 0
    Screen        1 "External Screen" RightOf "Default Screen"
    Option        "Xinerama" "On"
    InputDevice    "Generic Keyboard"
    InputDevice    "Configured Mouse"
    InputDevice    "stylus" "SendCoreEvents"
    InputDevice    "cursor" "SendCoreEvents"
    InputDevice    "eraser" "SendCoreEvents"
    InputDevice    "Synaptics Touchpad"
EndSection

There are two key pieces to note about this section:

I have turned on the Xinerama option. This is one of the ways X has of working with multiple monitors, and probably the easiest. 
For each Screen, I had to prefix it with a number, starting with 0, to identify it. 
Also, for the first screen, I included a location, where to put the screen; in this case, at the coordinates "0 and 0". 
For the second screen, I indicated that it is to be to the right of the first screen. 
Server Flags
Finally, I had to set a “server flag,” to enable the Xinerama functionality:

> Section "ServerFlags"
    Option    "Xinerama" "true"
EndSection

Testing the Changes
Once you've finished editing the file, simply hit Ctrl+Alt+Backspace to restart X. (Make sure you shut everything down, first.) If it doesn't work, simply restore your xorg.conf file back to a version that you know works — for example, the xorg.justlaptop.prod file that you created earlier — and then start again. (See the X Window Configuration article for more help on doing that.)

Feel free to make as many backup copies as you need, while you're doing your editing. You can always delete them later, when you're up and running.

Finishing Your Editing
You now have at least two copies of your configuration file: xorg.justlaptop.prod, which works with just the laptop's display, and a working xorg.conf that powers both of your monitors. Your final step is to make another copy of your configuration file — the current one, that works with both of your monitors — and call it xorg.twomonitors.prod.

The Startup Script
Your final step is to create a script which will figure out whether or not the monitor is plugged in; depending on that answer, it will decide which configuration file should be used, and copy that file to /etc/X11/xorg.conf. The file should be put in the /etc/init.d directory; I named mine xorg.conf_switcher.sh. Here is what it contains:

> # determine whether an external display is attached
if /usr/sbin/ddcprobe | grep "monitorname"; then
echo "External Display attached."
# set external display as exclusive primary
cp /etc/X11/xorg.twoscreens.prod /etc/X11/xorg.conf
else
echo "Using built-in LCD."
# set build-in LCD as exclusive primary display
cp /etc/X11/xorg.justlaptop.prod /etc/X11/xorg.conf
fi

Once this is done, you need to change the permissions on the file, to make it “executable:”

> $sudo chmod a+x /etc/init.d/xorg.conf_switcher.sh

Now lets configure the startup so the script will run before xorg starts. Other wise an CTRL+ALT+BACKSPACE is required.
With solution it will boot up before xorg has.

> sudo ln -s /etc/init.d/xorg.conf_switcher.sh S08startupscript

[B][SIZE="2"]all credits goes to the maker of [http://sernaonubuntu.wikidot.com/multiple-monitors](http://sernaonubuntu.wikidot.com/multiple-monitors) for the script and the howto
the last line was found in an patch for 915resolution.[/SIZE][/B]

cheers and good luck!

---

### Post by RezDuane on 2007-08-10
OK, thanks!  Looks like I'll need to 'bring my lunch.'  Ubuntu is relatively new to me and finding and editing files is something I've only done a little of.  Like for my wireless.  Your directions are pretty clear so guess I'll jump into it in the next couple of days.

Thanks!
rd

---

