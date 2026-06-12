---
title: "Adjust Synaptics Touchpad Drag Speed"
date: 2009-06-02
forum: Hardware
---

### Post by SoftwareExplorer on 2009-06-02
Is there a way to adjust how fast the cursor moves when you get to the edge of your touchpad when you are dragging by double tapping?

I have 9.04 64 bit
I'm not sure how to find the exact model of the touchpad, but I have a Compaq Presario F500

---

### Post by SoftwareExplorer on 2009-06-26
If you don't understand my question, I'll be happy to clarify.

---

### Post by RabidWeezle on 2009-06-27
I would be interested to know the answer to this question aswell as I believe the sensitivity is way to low for dragging files from one window to another. I usally just end up holding down the actual button and dragging my finger across the pad a few times to get the selected file to the destination. Also I would prefer more sensitivity for the games I use the mouse on like card games and stuff. The only thing I could think of is maybe there's a setting for it in xorg.conf under the mouse device settings.

---

### Post by Ayuthia on 2009-06-27
You will have to enable SHMConfig in the fdi.  There is a guide that tells you how:
[https://help.ubuntu.com/community/SynapticsTouchpad](https://help.ubuntu.com/community/SynapticsTouchpad)

From there, you can either use synclient or gsynaptics to adjust things.

Hope that helps.

The other option is to add the options into the .fdi file.  The [Arch wiki]("http://wiki.archlinux.org/index.php/Touchpad_Synaptics") has some examples on how to convert the the xorg.conf version over to the .fdi format.

---

### Post by SoftwareExplorer on 2009-07-04
> **RabidWeezle said:**
> I would be interested to know the answer to this question aswell as I believe the sensitivity is way to low for dragging files from one window to another. I usally just end up holding down the actual button and dragging my finger across the pad a few times to get the selected file to the destination. Also I would prefer more sensitivity for the games I use the mouse on like card games and stuff. The only thing I could think of is maybe there's a setting for it in xorg.conf under the mouse device settings.

What I did from the wiki:
```
Alt + F2
```
```
gksudo gedit /etc/hal/fdi/policy/shmconfig.fdi
```
then put this into the file:
```
<?xml version="1.0" encoding="UTF-8"?>
<deviceinfo version="0.2">
  <device>
    <match key="input.x11_driver" string="synaptics">
      <merge key="input.x11_options.SHMConfig" type="string">True</merge>
    </match>
  </device>
</deviceinfo>
```
save and close the file, then restart.

Then go to Applications->Accessories->Terminal, then put in
```
synclient EdgeMotionMinSpeed=400 EdgeMotionMaxSpeed=401
``` to change the settings. You can tweak the numbers to your liking by running it with different numbers until you get what you want. To see a list of things you can change, in a terminal do ```
synclient -l
``` When you have it how you like it, go to System->Preferences->Startup Applications, then do Add. In the command box put the command you ran to get the settings the way you want. Give it whatever name and description you want, then hit Add. 
Tada! 
Oh, and you can close all the windows we opened.

---

