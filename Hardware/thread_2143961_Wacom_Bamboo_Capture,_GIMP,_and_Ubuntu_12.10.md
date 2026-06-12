---
title: "Wacom Bamboo Capture, GIMP, and Ubuntu 12.10"
date: 2013-05-10
forum: Hardware
---

### Post by Shansie on 2013-05-10
Okay, I have a few things I'm struggling with here. Keep in mind when you answer these, I've only been running Ubuntu for a few weeks. I understand little of the terminology so far (as I've had little time to look it up yet - finals are coming up). Please be as specific and simple in your explanations as you can. I'm not especially great at technology in general yet, either, as pretty much everything I've learned has been from Windows Vista (couldn't afford to upgrade to a different version of Windows on my laptop) using trial and error or Googling things. I don't understand a lot of the terminology yet, but I'm trying. If you use a term that's above very very basic levels, I would appreciate if you'd define or explain it for me so I can save it for future reference. Honestly, I'm hesitant to leave the "Absolute Beginner Section," even though this thread fits better here.

In case anyone needs to know, I'm running Ubuntu 12.10 on a Dell Inspiron 1545. I bought it when I was only in 8th grade and haven't been able to afford an upgrade, especially since it hasn't given out yet (though Vista has).

**#1: Setting up Wacom Bamboo Capture**
I have this tablet I bought a few months ago (can't remember exactly when) to use. It comes with two CDs. One is the installation CD and the other is the Software Bundle. The Installation CD says the following on it: "Bamboo tablet driver v5.2.5 WIN / 5.2.5 MAC." I'm assuming it would be pointless to use this CD to set up the tablet on Ubuntu as I did when I had Vista. I've looked around on Google, the ubuntuforums, and the Wacom website and haven't found anything useful yet. There were a few threads here that talked about it, but being the low level beginner I am, I was really confused when I tried to read through them.

**#2: GIMP tablet set up; 2.8 doesn't support pressure sensitivity**
Or at least, that's what I've read. The GIMP website says to downgrade to 2.6 to have pressure sensitivity for tablets until 3.0 is released. Thing is, I can't find it on their website or in the software center. I'm hesitant to download from any other source that hasn't been tested/trusted by other users. Does anyone know where to find it and/or how to set up the pressure sensitivity once I do get it?

**#3: Software Bundle**
As I mentioned in #1, this tablet comes with a software bundle -- one of the perks of this particular tablet. I'm not sure which, if any, of the software on the CD will work on Ubuntu without additional things like WINE or emulators. I don't want to try to download things that aren't compatible, as much as I love the software that came with the tablet. I'll list the things that come with it below:
[LIST]
[*]Adobe Photoshop Elements 8.0 Win/Mac -* I assume this one doesn't, since it specified?*
[*]Autodesk SketchBook Express
[*]Nik Color Efex Pro 3.0 WE3
[/LIST]
Since I know at least most of the software that comes with things like this is specific to Windows/Mac, I'm tempted to doubt any of the programs would be compatible with Linux. Still, I prefer to ask.

Any and all help is greatly appreciated.

---

### Post by Favux on 2013-05-11
The Bamboo Capture should work out of the box in Quantal (12.10).  The Wacom drivers are installed by default.  And you are correct the Windows version of the drivers does not work.  Let's check a couple of things.  In a terminal (with the Bamboo plugged in) enter the following commands and post the outputs:
```
lsmod | grep [Ww]acom

xinput list
```

You might be able to run some of the grapics app.s with Wine but you could try the linux app.s first.  Gtk versions are Gimp, Inkscape, MyPaint etc.  There are KDE versions too like Krita and so on.  And for 3-D Blender which doesn't use either of the two toolkits.

---

### Post by Shansie on 2013-05-11
```
lsmod | grep [Ww]acom
wacom                  51337  0

xinput list
&#9121; Virtual core pointer                        id=2    [master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer                  id=4    [slave  pointer  (2)]
&#9116;   &#8627; Logitech USB Optical Mouse                  id=9    [slave  pointer  (2)]
&#9116;   &#8627; AlpsPS/2 ALPS GlidePoint                    id=11    [slave  pointer  (2)]
&#9116;   &#8627; PS/2 Mouse                                  id=12    [slave  pointer  (2)]
&#9116;   &#8627; Wacom Bamboo 16FG 4x5 Pen stylus            id=14    [slave  pointer  (2)]
&#9116;   &#8627; Wacom Bamboo 16FG 4x5 Pen eraser            id=15    [slave  pointer  (2)]
&#9116;   &#8627; Wacom Bamboo 16FG 4x5 Finger touch          id=16    [slave  pointer  (2)]
&#9116;   &#8627; Wacom Bamboo 16FG 4x5 Finger pad            id=17    [slave  pointer  (2)]
&#9123; Virtual core keyboard                       id=3    [master keyboard (2)]
    &#8627; Virtual core XTEST keyboard                 id=5    [slave  keyboard (3)]
    &#8627; Video Bus                                   id=6    [slave  keyboard (3)]
    &#8627; Power Button                                id=7    [slave  keyboard (3)]
    &#8627; Sleep Button                                id=8    [slave  keyboard (3)]
    &#8627; AT Translated Set 2 keyboard                id=10    [slave  keyboard (3)]
    &#8627; Dell WMI hotkeys                            id=13    [slave  keyboard (3)]
```

Just for future reference to help me learn as I go, could you explain what exactly those mean or what they are asking the computer? I can sort of guess from the output, but I'm not sure.

---

### Post by Shansie on 2013-05-11
Also, I figured it'd be useful to note that it does "work" out of the box, in that I can draw in GIMP, move the cursor, and click, but there is no pressure sensitivity. I've been told this is because of GIMP 2.8. Before I moved to Linux, the pressure worked fine, but I don't know which version of GIMP I had. I also don't know if I need anything extra installed for the tablet to work the way it is supposed to behind-the-scenes. I figure it's safer (for my computer's sake) not to assume.

---

### Post by Favux on 2013-05-11
OK, that explains why the output from the two commands look normal.

Are you aware that in Gimp you need to configure the extended input devices to get pressure?  As in:  Edit > Preferences > Input Devices > Configure Extended Input Devices > set device drop down to Wacom stylus and then set Mode drop down to Screen.  Do the same for eraser.

---

### Post by Shansie on 2013-05-11
Wacom Stylus doesn't appear in the input devices in GIMP. I remember it showing up fine on the older version (probably a version or two ago, if I had to guess) I had on Vista, but I can't find it here.

The options are "Core Pointer", "AlpsPS/2 ALPS GlidePoint" (this one sounds more promising than the others), "Logitech USB Optical Mouse", "PS/2 Mouse", and "Virtual core XTEST pointer."

---

### Post by Favux on 2013-05-13
Well as long as the tablet is plugged in and showing up in xinput list it should show up in Gimp.

If it doesn't then the Wacom driver crashed and it would have stopped showing in xinput list or there is a bug in your version of Gimp.

---

### Post by Shansie on 2013-05-14
I think it's probably the version of GIMP. It still shows in xinput list. [http://www.gimp.org/release-notes/gimp-2.8.html](http://www.gimp.org/release-notes/gimp-2.8.html)
> GIMP 2.8 relies on a newer version of GTK+2 that unfortunately haspartially broken support for graphics tablets such as Wacom. If yourgraphic tablet doesn't work in GIMP 2.8 as it should, we recommenddowngrading to 2.6 until we release GIMP 3.0 that relies on GTK+3which has fully functional support for advanced input devices.To address the needs to migrate from the old tools presets systemto the new one we provide a [script]("http://wiki.gimp.org/index.php/Mindstorm:Preset_converter") inPython. However, the old tools presets are not 100% convertible tothe new tool presets. For instance, brush scale from 2.6 can't beconverted to brush size in 2.8.
It's quite frustrating to lack pressure sensitivity. I've heard that getting 2.6 allows tablets to work properly (and the GIMP website even says to download it if you have a tablet), but there is no official download for GIMP 2.6 that I can find on the website. I'm hesitant to download from anywhere else.

---

### Post by landstander on 2013-09-30
> **Shansie said:**
> ...no official download for GIMP 2.6 that I can find on the website. I'm hesitant to download from anywhere else.

Official websites are mostly ok to trust but you should note that official releases from the source websites are sometimes not as throughly vetted by the community which is why those packages haven't been added to the official package repositories yet and which is why you should consider a website as being a place to test new software. If its older stuff your looking for, then maybe try this safer method first: (I can't speak for Ubuntu 12.10 but this should be similar as in 12.04 (which is what I'm using)).

If you look in synaptic package manager under your installed version of gimp (type "gimp" into the search bar). Check its properties by right clicking on the "gimp" package then --> properties --> versions. This will list all available versions of gimp for you're system.

From here exit the properties menu for gimp and go to the main menu bar and select --> package --> force version --> then simply select the version of gimp you wish to install and follow the instructions from there. 
You might be required to uninstall or downgrade some other packages when downgrading gimp so make note of any messages you get while performing this downgrade (you will be asked if its ok before synaptic does anything) to make sure its something you're ok with.

---

