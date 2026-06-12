---
title: "an intrepid synaptics touchpad how-to"
date: 2008-12-31
forum: Hardware
---

### Post by maclenin on 2008-12-31
With reference and due deference to **[ubuntu-freak]("http://ubuntuforums.org/showthread.php?t=766683")**, **[wgrant]("http://ubuntuforums.org/showpost.php?p=5996727&postcount=4")** and a large handful of others, I've decided to distill a summary of their suggestions and my own searching and experimenting into a short "how-to resolve the Intrepid synaptics touchpad **renegade tap and scroll issue**".

**NB1:** This guide describes the **SHMConfig method** I used successfully on my **Intrepid**-run HP 6910p to configure its **SynPS/2 Synaptics TouchPad**.

**NB1a:** Though the methods described herein might be used to modify any number of synaptic touchpad attributes (see step 7a.), this guide focuses most specifically on addressing the "renegade tap and scroll issue".

**NB2:** For an earlier **xorg.conf method** used to successfully re-configure the same touchpad in **Feisty**, please click [_here_]("http://ubuntuforums.org/showthread.php?t=351058").

**[COLOR="Red"]WORDS OF WARNING:[/COLOR]**>  This method is not secure if you are in an untrusted multiuser environment. All local users can change the parameters at any time (i.e. root privileges will not be required to make the touchpad changes described herein, once SHMConfig has been enabled).

- adapted from "man synclient"



Assuming you're still game - having processed the warning - let's get started...

**A. DO YOU HAVE A SYNAPTICS TOUCHPAD?**

1. Open the terminal to confirm that you do, indeed, have a synaptics touchpad, by entering...

```
xinput list
```

2. If, among the xinput devices listed you find something similar to...

```
"SynPS/2 Synaptics TouchPad"	id=4	[XExtensionPointer]
	Num_buttons is 12
	Num_axes is 2
	Mode is Relative
	Motion_buffer is 256
	Axis 0 :
		Min_value is 0
		Max_value is -1
		Resolution is 1
	Axis 1 :
		Min_value is 0
		Max_value is -1
		Resolution is 1
```

...read on!

**B. ENABLE SHMConfig TO "UNLOCK" THE TOUCHPAD UTILITIES**

3. Create a **shmconfig.fdi** file by entering the following into the terminal...

```
sudo nano /etc/hal/fdi/policy/shmconfig.fdi
```

4. Copy and paste this code into the empty, newly-created **shmconfig.fdi** file...

```
<?xml version="1.0" encoding="ISO-8859-1"?>
<deviceinfo version="0.2">
<device>
<match key="input.x11_driver" string="synaptics">
<merge key="input.x11_options.SHMConfig" type="string">True</merge>
</match>
</device>
</deviceinfo>
```

5. Save and exit **shmconfig.fdi**...

6. Restart your computer.

**C. USE THE synclient UTILITY TO CONFIGURE YOUR SYNAPTICS TOUCHPAD**

7. Open the terminal.

7a. Enter...

```
man synaptics
```

...to peruse the myriad touchpad configuration options available.

8. Use **synclient** to disable touchpad tapping and scrolling via the TouchpadOff option...

```
synclient TouchpadOff=2
```

9. Exit the terminal.

**D. TEST YOUR NEW SETTINGS**

10. Test your current configuration to make certain the revised touchpad settings took effect.

11. If your changes were successful, read on to cause them to take effect at each restart or log-in.

**E. CAUSE YOUR NEW TOUCHPAD SETTINGS TO "AUTOSTART"**

12. Navigate to **Autostarted apps** (in xubuntu: **Applications - Settings - Settings Mananger - Autostarted apps**).

13. Click on **+Add** to add your touchpad configuration command.

14. **Name** it anything you like, "touchpad toggle", for instance.

15. The **Description** can be similar - "turn off tap and scroll".

16. The **Command** would be the same as that you entered at step 8. For example...

```
synclient TouchpadOff=2
```

17. Click **Ok**, and restart your computer to enjoy the result!

Any and all comments, suggestions and criticisms are always welcomed!

HNY!

---

### Post by concertedrxn on 2009-01-08
Thanks for your how-to, but I believe I stumbled across a better solution.  While looking for a solution to an apparently unrelated issue, the mute button not working on a Del XPS M1210 laptop, I came across this thread: [http://ubuntuforums.org/showthread.php?t=966519&page=2]("http://ubuntuforums.org/showthread.php?t=966519&page=2").  In post number 13, linfidel deleted ~/.gconf/desktop/gnome/peripherals/mouse/%gconf.xml and restarted his X session to fix the mute button.  I did much the same by moving the file to another location, and it worked, but as a side effect the "Touchpad" tab in System -> Preferences -> Mouse became visible.  Even without the Synaptics option "SHMConfig" being set to "true", clearing the checkbox "Enable mouse clicks with touchpad" in the "Touchpad" tab disabled the touchpad tap feature.  When done this way, the setting survives suspend/resume cycles and reboots without additional configuration.

---

### Post by agim on 2009-01-08
I actually use this page, and made the .fdi file. It worked brilliantly.
Then I made gsynaptics-init one of my startup applications, after setting the preferences in gsynaptics itself, of course.

[https://help.ubuntu.com/community/SynapticsTouchpad](https://help.ubuntu.com/community/SynapticsTouchpad)

---

### Post by jalexstark on 2009-01-19
The original post helped me, albeit with
```
#!/bin/sh
synclient TouchpadOff=2
``` in a touchpadfix file.

The definitive fact is that there is a bug.  I notice that gsynaptics-init is run in the startup tab of "sessions" Preferences.  man gsynaptics reveals that a gconf settings file should be read, but something goes wrong with the process.  A guess is that the gsynaptics version does not work with the settings available in the synclient on which it depends.  The difficulty people have with this issue indicates that there is a real bug.

The other pages referenced in follow-ups, eg, HAL configuration, were somewhat opaque and not helpful.  For example, I get the touchpad tab in the mouse preference-settings, but these settings do not persist on my system.

---

### Post by roadracer on 2009-03-11
> 8. Use synclient to disable touchpad tapping and scrolling via the TouchpadOff option...

Code:

synclient TouchpadOff 2



Is this for both Gnome and KDE?  I would like to disable the touchpad tapping in Kubuntu 8.10.

---

### Post by maclenin on 2009-03-12
**roadracer:**

I cannot vouch for KDE (or GNOME) as I am working in the XFCE (xubuntu 8.10) environment. Give it a try (with KDE) and report back on your results!

---

### Post by roadracer on 2009-03-13
> **maclenin said:**
> **roadracer:**

I cannot vouch for KDE (or GNOME) as I am working in the XFCE (xubuntu 8.10) environment. Give it a try (with KDE) and report back on your results!

Gnome has a settings gui for the touchpad, but KDE does not.  Does anyone know how to disable the touchpad taps only in Kubuntu 8.10?

---

### Post by declipse on 2009-06-20
This fix worked for me in Kubuntu 9.04.  

Thanks a lot for taking the time to write that out.  After implementing this, my experience with Kubuntu on a laptop has improved greatly.  The whole accidentally dragging icons, clicking on things, etc was driving me nuts.  I don't know why anyone would want that enabled.

Would be nice if they had an option for it in system preferences!  But this works for me - and thanks again for your time in documenting a fix and sharing it with us.

-Bill

---

