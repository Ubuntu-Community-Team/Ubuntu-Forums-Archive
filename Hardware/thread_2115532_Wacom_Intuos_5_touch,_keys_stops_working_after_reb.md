---
title: "Wacom Intuos 5 touch, keys stops working after reboot"
date: 2013-02-13
forum: Hardware
---

### Post by bent95kr on 2013-02-13
Hi Ubuntu forums, I have the following problem with my Wacom Intuos 5 touch medium tablet: Whenever I reboot my computer the tablet express keys, the touch ring and the button inside the touch ring no longer work as I configured them to, instead they have different functions, or no functions at all. For example the button inside the touch ring starts acting like the left mouse button, and the touch ring scrolls up and down in programs. Trying to configure the keys and the touch ring from the system settings doesn't have any effect on the tablet.This makes me wonder if “whatever detects devices on Ubuntu boot” believes this part of the tablet is a mouse. Configuring the pen works as it should by the way. 

I have found that disconnecting and then reconnecting the tablet solves the issue, but it is of course pretty annoying having to do that every time I turn on my computer, so if anyone have any idea on how to solve this problem, I would be very thankful.    

My computer is an Acer Aspire X3990 with the 64-bit version of Ubuntu 12.10 installed.

---

### Post by Favux on 2013-02-13
Hi bent95kr,

It sounds like you are configuring the ExpressKeys using the Gnome Wacom tablet app. in System Settings.  Correct?

To rule out a hardware problem does the tablet work correctly in Windows, or another Distro or release?

Check the usb cable connections and make sure they're good on both ends.  If the tablet is plugged into a hub change it to a usb port on the computer.

A quick way to check if the tablet is on the Wacom X driver is to run in a terminal the following command:
```
xinput list
```
If you see stylus, eraser, pad, and touch appended to the device names it is on the Wacom X driver.  If not it is probably on the evdev driver and that's why things aren't working.  So run that command when things work and when they don't and see if the output is different.

---

### Post by bent95kr on 2013-02-13
Hi, yes it is correct that I'm using the Gnome Wacom tablet app. in System Settings.  The tablet works as it should in windows 7. The tablet is connected directly into the computer, and the cable is good on both ends. 

When running the ximput list when having the issue this shows:
&#9121; Virtual core pointer                        id=2    [master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer                  id=4    [slave  pointer  (2)]
&#9116;   &#8627; Wacom Intuos5 touch M Pen stylus            id=8    [slave  pointer  (2)]
&#9116;   &#8627; Wacom Intuos5 touch M Finger touch          id=9    [slave  pointer  (2)]
&#9116;   &#8627; Microsoft SideWinder™ Mouse               id=10    [slave  pointer  (2)]
&#9116;   &#8627; Wacom Intuos5 touch M Pen eraser            id=12    [slave  pointer  (2)]
&#9116;   &#8627; Wacom Intuos5 touch M Pen cursor            id=13    [slave  pointer  (2)]
&#9116;   &#8627; Wacom Intuos5 touch M Pen pad               id=14    [slave  pointer  (2)]
&#9123; Virtual core keyboard                       id=3    [master keyboard (2)]
    &#8627; Virtual core XTEST keyboard                 id=5    [slave  keyboard (3)]
    &#8627; Power Button                                id=6    [slave  keyboard (3)]
    &#8627; Power Button                                id=7    [slave  keyboard (3)]
    &#8627; AT Translated Set 2 keyboard                id=11    [slave  keyboard (3)]

When I reconnect, and type in the command again it shows this:
&#9121; Virtual core pointer                        id=2    [master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer                  id=4    [slave  pointer  (2)]
&#9116;   &#8627; Microsoft SideWinder™ Mouse               id=10    [slave  pointer  (2)]
&#9116;   &#8627; Wacom Intuos5 touch M Finger touch          id=8    [slave  pointer  (2)]
&#9116;   &#8627; Wacom Intuos5 touch M Pen stylus            id=9    [slave  pointer  (2)]
&#9116;   &#8627; Wacom Intuos5 touch M Pen eraser            id=12    [slave  pointer  (2)]
&#9116;   &#8627; Wacom Intuos5 touch M Pen cursor            id=13    [slave  pointer  (2)]
&#9116;   &#8627; Wacom Intuos5 touch M Pen pad               id=14    [slave  pointer  (2)]
&#9123; Virtual core keyboard                       id=3    [master keyboard (2)]
    &#8627; Virtual core XTEST keyboard                 id=5    [slave  keyboard (3)]
    &#8627; Power Button                                id=6    [slave  keyboard (3)]
    &#8627; Power Button                                id=7    [slave  keyboard (3)]
    &#8627; AT Translated Set 2 keyboard                id=11    [slave  keyboard (3)]

So the only difference I can see between the two lists is the placement of my mouse.

---

### Post by Favux on 2013-02-13
Good.  I think that's solid progress diagnosing the issue.

Hardware is OK.  The tablet is on the Wacom X driver and stays on it.

Since this occurs during a boot and not a hot plug then it is a problem with the boot.

The components, as far as I know, are the gnome-settings-daemon and the Wacom plug-in for it.  And the Wacom tablet applet.  Not sure which has the settings.  But since you use the Tablet app. to set them maybe that's where to bet.

I know the Wacom tablet applet has a start up file we can edit.  Not sure about the gnome-settings-daemon and not sure we'd want to mess with it anyway.

So the theory would be what?  On your system the Wacom tablet app. is making the settings available too early before the gnome-settings-daemon/Wacom plug-in are ready to read them?  Throw a delay into the Wacom tablet app. startup file and that will fix things?  Worth a shot I suppose.

Let me figure out how to do that for the app.

---

### Post by Favux on 2013-02-13
Found the location for the .desktop or autostart file, I think.  OK, to edit use:
```
gksudo gedit /usr/share/applications/gnome-wacom-panel.desktop
```
Then at the bottom of the file add the line:
```
X-GNOME-Autostart-Delay=1
```

---

### Post by bent95kr on 2013-02-13
Nope, unfortunately it didn't do anything... 

Another issue with the tablet I noticed now is that when I'm reconnecting the tablet I can't configure the touch ring, and dragging my finger around it clockwise changes the touch ring mode. This doesn't happen in windows 7 either. I have no idea if those two issues could have anything to do with each other or not...

---

### Post by Favux on 2013-02-13
Well I left the Gnome control center (System Settings) out of the chain.  That also has a startup file:  /usr/share/applications/gnome-control-center.desktop.

Try moving the delay there and see what happens.

Otherwise I'm not sure what to do.  The gnome-settings-daemon doesn't have an autostart file and I think the dconf settings for the Wacom plug-in just consist of it being active or not.  Ah just checked.  Hmm, there is a priority setting:
> Priority to use for this plugin in gnome-settings-daemon startup queue
Hmm, do we want to mess with that?

---

### Post by bent95kr on 2013-02-13
This didn't work either... As for the other thing you suggested, I guess I could try that, if you tell me how. Even though I have no idea what that might affect. But anyway I won't blame you if my system breaks ;).

---

### Post by Favux on 2013-02-13
> But anyway I won't blame you if my system breaks.
Good, I appreciate that!  :)

A thought occurs.  First how about trying something simpler or more basic anyway?  Use Synaptic Package Manager and search gnome-control-center and then right click on it and Mark for Reinstallation.  Then reinstall it.  Let's see if the problem is some corruption of the original install.

To use dconf editor you enter in a terminal:
```
dconf-editor
```
It probably isn't installed so you'll have to do an apt-get install.

Then navigate to org.gnome.settings-daemon.plugins.gsdwacom where you should see the two keys:  active and priority.  Click on priority and adjust the key value.  I have no idea which way to go so you'll have to try different values.  Hopefully it does what I think it says it does so we aren't just wasting time.

---

### Post by bent95kr on 2013-02-13
For some reason I don't have the option to mark gnome-control-center for reinstallation in Synaptic Package Mananger, the option is just grayed out, unlike other installed packages. But I tried to mess with that priority in the Dconf editor, trying both 1 and 20, and when I changed the priority to 100, it actually worked! Awesome! Thank you very much! 



  
 Now it's just the issue with configuring the touch ring, but since that issue seams to have nothing to do with this issue, I'll post a new tread about it.

---

### Post by Favux on 2013-02-13
> I tried to mess with that priority in the Dconf editor, trying both 1 and 20, and when I changed the priority to 100, it actually worked!
Cool!  :)

---

