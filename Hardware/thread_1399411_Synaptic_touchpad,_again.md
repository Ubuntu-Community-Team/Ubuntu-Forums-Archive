---
title: "Synaptic touchpad, again"
date: 2010-02-05
forum: Hardware
---

### Post by edpatterson on 2010-02-05
Same problem: Touchpad not being disabled while typing, different approach to making my laptop usable

Change the sensitivity of it so the inadvertant bumps of it while typing do not register. I swear this thing is so sensitive that I can move the pointer by blowing on the touchpad!

I tried the steps here: [http://www.yeap.de/blog2.0/archives/84-Configuring-the-Synaptics-Touchpad.html](http://www.yeap.de/blog2.0/archives/84-Configuring-the-Synaptics-Touchpad.html) I installed gsynaptics and a touchpad icon appeared in the System->Preferences menu. Changing the sensitivity had no effect at all, still too sensitive. Then I removed gsynaptics and installed gpointing-device-settings as it claimed to be the GSynaptics successor. I lost the touchpad icon and can not locate anything to change the setting with.

I would like to set the sensitivity so low that there is no way my palm could possibly inadvertently activate the mouse.

PLEASE could someone tell me how to change the settings

I am using an HP Pavilion dv6000

Ed

---

### Post by pi/roman on 2010-02-06
By same problem, do you mean it was fixed before but quit working? The page you linked to makes suggestions for editing the xorg.conf file, did you try that? If you are looking for information on synaptics settings you can use "man synaptics." In order to get advice on changing settings it must first be known what settings currently exist so you would need to post your hal configuration like this:
sudo find /usr/share/hal /etc/hal -name 11-x11* -print0 | xargs -0 -t cat

and also post the input device section of your xorg.conf file:
cat /etc/X11/xorg.conf

---

### Post by edpatterson on 2010-02-06
By same problem I mean I have tried numbers approaches to either disable the touch pad while typing and now I am trying to change it's sensitivity. Nothing seems to work.

First, I am a fairly new Ubuntu/Linux user so things that some take for granted are totally alien to me. I found numerous posts related to editing the xorg.conf file. I spent literally hours trying to find it and failed. Turns out by default it does not exist on 9.10 and has been replaced by a hal or hai (I see it referenced both ways and the hai is the one that exists on my laptop). 

Installing the gsynapics gave me a touchpad icon that showed sensitivity settings WAHO! I set it as low as possible, no change. I went back into the it and the setting was still dead center. I removed it (gsynaptics) and installed gpointing-device-settings but could not locate any interface to/for it.

All I want to do is have my touchpad revert back to it's behavior under 8.04.

Ed (pondering if I should simply downgrade this weekend and deem 9.10 Ubuntu's version of Vista)

---

### Post by pi/roman on 2010-02-06
do
```
sudo find /usr/share/hal /etc/hal -name 11-x11* -print0 | xargs -0 -t  cat
```and
```
cat /etc/X11/xorg.conf
```give any output?

---

### Post by IcarusR on 2010-02-06
Syndaemon can do this checkout 'man syndaemon' & this page

[http://embraceubuntu.com/2006/09/20/disable-touchpad-temporarily-when-typing/]("http://embraceubuntu.com/2006/09/20/disable-touchpad-temporarily-when-typing/")

---

### Post by pi/roman on 2010-02-06
Adding syndaemon to the startups is a good idea.  You could also add synclient commands to the startup list such as "synclient fingerhigh=100" that should make the necessary finger pressure fairly high.

---

### Post by edpatterson on 2010-02-06
> **pi/roman said:**
> 
give any output?
The first
```

<?xml version="1.0" encoding="ISO-8859-1"?>
<deviceinfo version="0.2">
  <device>
    <match key="info.capabilities" contains="input.touchpad">
        <merge key="input.x11_driver" type="string">synaptics</merge>
        <!-- Arbitrary options can be passed to the driver using
             the input.x11_options property since xorg-server-1.5. -->
        <!-- EXAMPLES:
        Switch on shared memory, enables the driver to be configured at runtime
	<merge key="input.x11_options.SHMConfig" type="string">true</merge>

	Maximum movement of the finger for detecting a tap
	<merge key="input.x11_options.MaxTapMove" type="string">2000</merge>

	Enable vertical scrolling when dragging along the right edge
	<merge key="input.x11_options.VertEdgeScroll" type="string">true</merge>

	Enable vertical scrolling when dragging with two fingers anywhere on the touchpad
	<merge key="input.x11_options.VertTwoFingerScroll" type="string">true</merge>

	Enable horizontal scrolling when dragging with two fingers anywhere on the touchpad
	<merge key="input.x11_options.HorizTwoFingerScroll" type="string">true</merge>

	If on, circular scrolling is used
	<merge key="input.x11_options.CircularScrolling" type="string">true</merge>

	For other possible options, check CONFIGURATION DETAILS in synaptics man page
        -->
        <match key="/org/freedesktop/Hal/devices/computer:system.hardware.product" string="Inspiron 1011">
            <merge key="input.x11_options.JumpyCursorThreshold" type="string">90</merge>
            <merge key="input.x11_options.AreaBottomEdge" type="string">4100</merge>
        </match>
        <match key="/org/freedesktop/Hal/devices/computer:system.hardware.product" string="Inspiron 1012">
            <merge key="input.x11_options.JumpyCursorThreshold" type="string">90</merge>
            <merge key="input.x11_options.AreaBottomEdge" type="string">4100</merge>
        </match>
        <match key="/org/freedesktop/Hal/devices/computer:system.hardware.product" string="HP MiniNote 1000">
            <merge key="input.x11_options.JumpyCursorThreshold" type="string">200</merge>
        </match>
    </match>
  </device>
</deviceinfo>
<?xml version="1.0" encoding="ISO-8859-1"?>
<deviceinfo version="0.2">
  <device>
    <match key="info.capabilities" contains="input.mouse">
      <match key="input.originating_device" contains="i8042_AUX_port">
        <append key="info.callouts.add" type="strlist">hal-probe-vmmouse</append>
      </match>
    </match>
  </device>
</deviceinfo>

```
The second
```

cat: /etc/x11/xorg.conf: No such file or directory

```

All of which mighrt as me step by step directions for heart surgery.

You have no idea how much I appreciate the assistance.

---

### Post by edpatterson on 2010-02-06
> **pi/roman said:**
> Adding syndaemon to the startups is a good idea.  You could also add synclient commands to the startup list such as "synclient fingerhigh=100" that should make the necessary finger pressure fairly high.

And were exactly would I do this?

---

### Post by pi/roman on 2010-02-06
> **edpatterson said:**
> And were exactly would I do this?
As IcarusR stated type "man daemon" in a terminal to see instructions for it.  Syndaemon can be used to disable the touchpad while using the keyboard.  Try it out and if it works you can place the syndaemon command with the proper options in the startup applications: go to system|preferences|startup applications in the desktop menu, click the "add" button and enter any name and the command that you have found to work underneath.

You can do the same thing with the synclient command and now I see you have a HAL configuration you could also adjust the synaptics settings with that. To see your list of synclient options just type "synclient -l" in a terminal. You can see what all of these settings do by opening another terminal and typing "man synaptics". 
The fingerhigh setting should increase the required pressure on your touchpad if it is too sensitive. Type "synclient fingerhigh=50" or more if that isn't high enough. This is only a temporary setting.

To make it permanent, enter it in your HAL configuration with the following line:
<merge key="input.x11_options.fingerhigh" type="string">50</merge>

also this line has to be moved out of the example section:
<merge key="input.x11_options.SHMConfig" type="string">true</merge>
so copy and paste it either above where it says "<!--Arbitrary options." or below where it says "For other possible options...-->"

---

### Post by pi/roman on 2010-02-06
You should double check the second command and make sure to use a capital "X" on X11 so it would be:
cat /etc/X11/xorg.conf

---

### Post by IcarusR on 2010-02-07
READ the page I linked !! ([http://embraceubuntu.com/2006/09/20/disable-touchpad-temporarily-when-typing/]("http://embraceubuntu.com/2006/09/20/disable-touchpad-temporarily-when-typing/")) It answers your problem. 
Try to do it, (that's how to learn) if you have problems THEN post back.

DO NOT expect other people to do it all for you. That is not what Linux is about. 
If you want an OS where it is all done for you & easy, then go back to Windows.

If xorg.conf does not exist then create it & add your synaptics options to it.
Again 'man xorg.conf' will help with the format.

Most, if not all, linux commands have a manual page accessed by typing in a terminal..

```
man syndaemon
```

---

### Post by edpatterson on 2010-02-07
> **pi/roman said:**
> You should double check the second command and make sure to use a capital "X" on X11 so it would be:
cat /etc/X11/xorg.conf
Thanks, the case was correct.

I am getting closer!
I issued 'sysclient fingerhigh=73' and that appears to be the magic setting. No more 'thumb tying'!
I added```

        <merge key="input.x11.options.SHMConfig" type="string">true</merge>
        <merge key="input.x11.options.fingerhigh" type="string">73</merge>
        <!-- Arbitrary options can be passed to the driver using

```
to
/usr/share/hal/fdi/policy/20thirdparty/11-x11-synaptics.fdi
Then rebooted. The change was not permanent. 

Was I supposed to put the lines in a different file? Not that I am complaining, if I have to execute the command each time I reboot it is no big deal.

Again, you have no idea how much I appreciate the help, and yes, I am reading all of the suggested man pages and blogs. However, reading and comprehending are sometimes very different things.

Ed

---

### Post by pi/roman on 2010-02-07
I'm happy to help so maybe even sometimes my help doesn't fix the problem but it might give someone a boost to find information they need to do it then hopefully you should have enough understanding of the matter that you may be able to help someone else with it.
So if the change is not permanent after rebooting, the file could be moved to a higher level folder to give it more persuasion by using this command:
```
sudo mv /usr/share/hal/fdi/policy/20thirdparty/11-x11-synaptics.fdi /etc/hal/fdi/policy/
```, which will move it to /etc/hal/fdi/policy/
If it is still not having an effect then you can do as was mentioned before, going to system, preferences, startup applications and adding your synclient command there.

---

### Post by edpatterson on 2010-02-07
> **pi/roman said:**
> 
So if the change is not permanent after rebooting, the file could be moved to a higher level folder to give it more persuasion by using this command:
```
sudo mv /usr/share/hal/fdi/policy/20thirdparty/11-x11-synaptics.fdi /etc/hal/fdi/policy/
```, which will move it to /etc/hal/fdi/policy/
If it is still not having an effect then you can do as was mentioned before, going to system, preferences, startup applications and adding your synclient command there.
OK, I tried the move command first, no go. Then I tried the startup applicatons idea, still no go.

Perhaps I have bigger problems the 'thumb typing' :-)

I am making a 'launcher' on my desktop for my setting.

Thanks!

---

### Post by pi/roman on 2010-02-07
I am at a bit of a loss now because I really did expect that since synclient fingerhigh=73 fixed the problem temporarily, then placing it in startup applications should be the end all to it.
You said you had installed gsynaptics but it didn't work so is that still installed, and if so maybe try removing it in package manager.
Also try placing 11-x11-synaptics.fdi in both folders if it is still in the /etc/hal/fdi/policy folder:
sudo cp  /etc/hal/fdi/policy/11-x11-synaptics.fdi /usr/share/hal/fdi/policy/20thirdparty/

---

### Post by edpatterson on 2010-02-07
> **pi/roman said:**
> You said you had installed gsynaptics but it didn't work so is that still installed, and if so maybe try removing it in package manager.
Also try placing 11-x11-synaptics.fdi in both folders if it is still in the /etc/hal/fdi/policy folder:
sudo cp  /etc/hal/fdi/policy/11-x11-synaptics.fdi /usr/share/hal/fdi/policy/20thirdparty/
That did it! Now I can get back to learning Java. Perhaps my first app will be a graphical interface for synclient (that actually works).

Thanks a million!

Ed

---

### Post by pi/roman on 2010-02-07
> **edpatterson said:**
> That did it!
Cool. Could you mark it as solved by using "thread tools" at the top of the thread and was it necessary to remove gsynaptics or did you just copy 11-x11-synaptics.fdi into both locations?

---

### Post by edpatterson on 2010-02-07
> **pi/roman said:**
> Cool. Could you mark it as solved by using "thread tools" at the top of the thread and was it necessary to remove gsynaptics or did you just copy 11-x11-synaptics.fdi into both locations?
Don't know which it was. I broke the cardinal rule of troubleshooting and changed 2 things at the same time. 

You also solved another question I have had for quite a while, how to mark a thread as solved.

---

