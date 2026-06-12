---
title: "i810 vs i915 for Intel GMA950 - No DRI"
date: 2007-04-18
forum: Hardware &amp; Laptops
---

### Post by benanzo on 2007-04-18
Hi!

I've been running Feisty since Herd 5 n my MacBook Core Duo, doing all the upgrades along the way.  By default I was getting the i810 driver loaded for the GMA950 graphics chip and was getting DRI and decent framerates.  Now, since the last upgrade, I notice that the i915 driver is loading instead of the i810 driver, and I'm not getting any DRI and beryl just turns white and forces me to kill X.

lsmod | grep i915

```
i915                   24448  0 
drm                    81044  1 i915

```

there is no i810

xorg.conf - relevant sections

```
Section "Module"
        Load    "bitmap"
        Load    "dbe"
        Load    "ddc"
        Load    "dri"
        Load    "extmod"
        Load    "freetype"
        Load    "glx"
        Load    "int10"
        Load    "record"
        Load    "v4l"
        Load    "vbe"
        Load    "i2c"
EndSection
```

```
Section "Device"
        Identifier      "Intel GMA950"
        Driver          "i810"
        BusID           "PCI:0:2:0"
        Option          "UseFBDev" "true"
        Option          "XAANoOffscreenPixmaps"
EndSection

```

```
Section "DRI"
        Mode    0666
EndSection

```


cat /var/log/Xorg.0.log | grep EE

```
(EE) I810(0): Failed to allocate texture space.
(EE) AIGLX: Screen 0 is not DRI capable
```

cat /var/log/Xorg.0.log | grep i915

```
(II) I810(0): [drm] loaded kernel module for "i915" driver
(II) I810(0): [drm] created "i915" driver at busid "pci:0000:00:02.0"
```

dmesg | grep drm

```
[  286.168000] [drm] Initialized drm 1.1.0 20060810
[  286.312000] [drm] Initialized i915 1.6.0 20060119 on minor 0
[  286.316000] [drm:drm_unlock] *ERROR* Process 6226 using kernel context 0

```

glxinfo | grep direct

```
direct rendering: No
OpenGL renderer string: Mesa GLX Indirect
```

I don't understand what changed.  I have since removed and reinstalled the i810 module and all the mesa/glx stuff with synaptic but it still wont work.  I have done dpkg-reconfigure xserver-xorg and set everything right but it still gives that error and goes to the i915 module.

any help would be great.

---

### Post by lorenzo on 2007-04-19
I have exactly the same problem. Anyone has a clue?

---

### Post by gjohn2 on 2007-04-20
I have the same problem, error messages and card.  Someone save us! LOL.

---

### Post by damian.arroyuelo on 2007-04-20
Do you try using the intel driver?

[COLOR="Green"]1. Start the system in "recovery mod" to boot in console.[/COLOR]

[COLOR="Green"]2. Install the INTEL driver: sudo apt-get install xserver-xorg-video-intel[/COLOR]

[COLOR="Green"]3. Edit the xorg configuration file and set the new video driver: sudo nano /etc/X11/xorg.conf
    Remplace the word "i810" from the Section "Device" to "intel":[/COLOR]

**Before:**
---------------------------------------------------
Section "Device"
[COLOR="White"]------------[/COLOR]Identifier       "Intel Corporation 82945G/GZ Integrated Graphics Controller"
[COLOR="White"]------------[/COLOR]Driver            **[COLOR="Red"]"i810"[/COLOR]**
[COLOR="White"]------------[/COLOR]BusID            "PCI:0:2:0"
End Section
---------------------------------------------------

**After:**
---------------------------------------------------
Section "Device"
[COLOR="White"]------------[/COLOR]Identifier       "Intel Corporation 82945G/GZ Integrated Graphics Controller"
[COLOR="White"]------------[/COLOR]Driver            **[COLOR="Red"]"intel"[/COLOR]**
[COLOR="White"]------------[/COLOR]BusID            "PCI:0:2:0"
End Section
---------------------------------------------------

[COLOR="Green"]4. Restart the Computer.[/COLOR]


Sorry for my bad English.
Hope this help you.

---

### Post by gjohn2 on 2007-04-20
Hey this worked great and your English is wonderful, take it from a Linguist.

However. I didn't have to do all of that.
I opened synaptic
searched for i810
the 'intel' driver also came up. 
so i selected it. the i810 was selected for 
uninstall.

i did
sudo gedit /etc/X11/xorg.conf
and changed the driver like you said. 

then i did 

ctrl+alt+Backspace to restart x and

now everything works.

thanks again for the idea!
greg

---

### Post by ]Nbx*cmD[ on 2007-04-26
> **damian.arroyuelo said:**
> Do you try using the intel driver?

[COLOR="Green"]1. Start the system in "recovery mod" to boot in console.[/COLOR]

[COLOR="Green"]2. Install the INTEL driver: sudo apt-get install xserver-xorg-video-intel[/COLOR]

[COLOR="Green"]3. Edit the xorg configuration file and set the new video driver: sudo nano /etc/X11/xorg.conf
    Remplace the word "i810" from the Section "Device" to "intel":[/COLOR]

**Before:**
---------------------------------------------------
Section "Device"
[COLOR="White"]------------[/COLOR]Identifier       "Intel Corporation 82945G/GZ Integrated Graphics Controller"
[COLOR="White"]------------[/COLOR]Driver            **[COLOR="Red"]"i810"[/COLOR]**
[COLOR="White"]------------[/COLOR]BusID            "PCI:0:2:0"
End Section
---------------------------------------------------

**After:**
---------------------------------------------------
Section "Device"
[COLOR="White"]------------[/COLOR]Identifier       "Intel Corporation 82945G/GZ Integrated Graphics Controller"
[COLOR="White"]------------[/COLOR]Driver            **[COLOR="Red"]"intel"[/COLOR]**
[COLOR="White"]------------[/COLOR]BusID            "PCI:0:2:0"
End Section
---------------------------------------------------

[COLOR="Green"]4. Restart the Computer.[/COLOR]


Sorry for my bad English.
Hope this help you.

Hi!

Tried this solution, gdm starts but when i enter my username and password the screen will just go blank and restart gdm... i've got no clue about what's happening... did somebody have the same problem? thanks!

---

### Post by Michl on 2007-04-27
I had the same thing happen to me with Control Alt Backspace.  I just
rebooted and it worked.

---

### Post by damian.arroyuelo on 2007-04-28
> **']Nbx*cmD[ said:**
> Hi!

Tried this solution, gdm starts but when i enter my username and password the screen will just go blank and restart gdm... i've got no clue about what's happening... did somebody have the same problem? thanks!

Try the vesa driver and reducing the monitor resolution and the color depth.
Match this values in your "/etc/X11/xorg.conf":

Driver		"vesa"

DefaultDepth	16

Modes		"800x600" "640x480" 

I want to give you more details, but its very dificulty to me write long descriptions in English... sorry...
Good luck!

---

### Post by orestisp on 2007-05-08
hi I did the changes mentioned...

1) via synaptic installed intel drivers (i810 default uninstalled)
2) changed X11 option
3) restarted

but..

the screen went black, xserver failed and as it seemed form X diagnostics the "new" driver was not working...

I fixed it by rolling back to the default driver
(also had to use X11 in gui.conf for Mplayer)

I have the 950 GMA Intel graphics card...

Now I have no acceleration and desktop effects are not working...

I 'm using 7.04 version and I desperately search for drivers...

I found xfree86 drivers from intel official site but it was packaged for suse and no good readme was inside or in the intel site (tar archive)

can someone help me plz?

maybe installing the drivers will enable acceleration but I have no clue how to install the source on ubuntu...

thnx in advance :)

---

### Post by nonlinear on 2007-05-26
hey, i know this is an old thread, sorry for bringing it back up...

did you guys solve your problem with the i915?  I whad the same exact problem you're all describing, and i get really frustrated when i can't make things work, so i stayed up like all weekend and finally fixed it.  so if you look you'll see that xorg has installed 435987345987 extra graphics drivers onto your computer.  the filenames are like xserver-xorg-video-POS_graphx_card.

you'll see that there's like 30 or 40 if them, and that you don't need them. It turns out that when you install i915, it references a library file that is updated but it ends up trying to use the old one that another (ati, i think) driver uses).  Sorry guys!  I don't remember any of the filenames, but uninistall those 43985734987 pointless xorg drivers, you might have to reconfig (can't remmebr), but then you'll get cri with i915.  I j ust did a clean install and about to redo this whole process, so i'll update you guys in a bit with filenames etc.

---

### Post by nonlinear on 2007-05-26
so i just uninstalled all of the xorg drivers except for the vga, vesa, and another generic one.  There is also one called xserver-xorg-video-all, last time i did this I thgouhgt that package included all the drivers, but I just read the description (quick) and it said it didn't contain any drivers and that you could uninstall it if you only wanted c`ertain drivers... anyhow, i didn't read it really cause I uninstalled it last time and so i just did it again.

ANyhow, ima boot into safe and reconfig, i'll be right back to report on my success.

OH, and looking at the file names, I think the file is lib2 whatever... not sure, im gonna hook up my firefox profile after boot, hopefully i can dig up some old stuff i was reading about it.

---

### Post by nonlinear on 2007-05-26
sorry for my third post in a row, but anyhow, I got my dri working on i915 in like 2 minutes after a clean install....  like i said, all you you have to do is uninstall all of the unnecessary xserver-xorg-video drivers (well, i left the super basic ones there), boot into safe, dpkg-reconfigure xserver-org, reboot and it will work.  I've attached a screenshot for the skeptics :P  A few weeks ago I had this all figured out, i.e. exactly what driver and lib file, I prolly have it documented somewhere will look....

this casued me major stress and frustratoin for a long lon gtime, and it's a serious problem..... strangely, no one seems to kjnow how to solve the problem, it took me like 3 days of searching to find the solution, and it was just posted nonchauntly on some forum somewhere.... but no more info anywhere!!!  so when you see peeps with this problem, make sure you tell them how to remedy it

**BTW, when i use i915 i xorg reports 256mb shared RAM, however card specs are 128mb.... does this happen to anyone else?**

cheers

---

### Post by stevetxt on 2007-08-30
Thanks, Damian.

Changing to the intel driver worked for me too.  I have the intel gma 950 graphics and an acer AL2216W monitor with 1680 by 1050 resolution.  With the i810 driver I was not getting the option for that resolution.

Also, your English is great.

Steve

---

