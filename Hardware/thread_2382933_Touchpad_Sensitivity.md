---
title: "Touchpad Sensitivity"
date: 2018-01-19
forum: Hardware
---

### Post by cue-ball on 2018-01-19
I am very new to Ubuntu and I am hoping there is a fix for the touchpad  sensitivity on my laptop. It is too sensitive and there is no option to  adjust it via the GUI. I am running Ubuntu 16.04 on a HP laptop with a  Synaptics touchpad.

Thank you.

---

### Post by DuckHook on 2018-01-19
Though it's a CLI solution, this may help: [https://help.ubuntu.com/community/SynapticsTouchpad](https://help.ubuntu.com/community/SynapticsTouchpad)

---

### Post by DuckHook on 2018-01-19
As a follow-up, I just checked my laptop, running 16.04.3 which has a synaptics touchpad (though likely a different model). I can control pointer speed through System Settings &#8594; Mouse & Touchpad. There is a subsection headed "Touchpad" with a ruler control for "Pointer speed". Does yours have this?

---

### Post by cue-ball on 2018-01-19
Thank you for your help.

I followed the instructions in the link you posted and this produced an interesting result. Using the following command in the Terminal gives me a perfectly working touchpad: 

**xinput --set-prop 11 "Synaptics Finger" 50 80 257**

However, after a reboot the mouse resets to default. It's almost as though the command isn't saving. Now if I want my touchpad to work correctly, I must enter the above command each time I use Ubuntu.

Much much better, but not ideal.

---

### Post by DuckHook on 2018-01-19
> **cue-ball said:**
> …It's almost as though the command isn't saving…
Good instincts. That's exactly the reason. *xinput* is an interactive command. It doesn't change system files so it doesn't persist after logout.

To make it load with every login, you can use the following workaround:

[LIST=1]
[*]Create a *bin* directory in your */home*:```
mkdir ~/bin
```
[*]Using *nano*, create a shell script to run your command:```
nano ~/bin/touchpad.sh
```
[*]Copy/paste the following lines into your script. It's better to copy/paste than type. Linux is case and syntax sensitive:```
#!/bin/bash

# This script is used to slow down and desensitize synaptics touchpad

sleep 5     # delays script for 5 seconds to give X a chance to load
xinput --set-prop 11 "Synaptics Finger" 50 80 257
```Write the file out to disk with <Ctrl>+<o>, exit *nano* with <Ctrl>+<x)
[*]Make the script executable:```
chmod 755 ~/bin/touchpad.sh
```
[*]Add the script to your Startup Applications. The Startup Applications applet can be found in the Launcher (type "startup" and it will show). Click on *Add*. Fill in the fields as follows:
```
Name:		Desensitize Touchpad
Command:	/home/<replace_with_your_home_directory>/bin/touchpad.sh
Comment:	Slows down synaptic touchpad

```
[*]Then click *Save*
[*]Logout &#8594; Login. If that doesn't work, reboot.
[/LIST]
Your touchpad should now automatically behave well 5 seconds after login.

---

### Post by cue-ball on 2018-01-19
Thank you! I followed your instructions when I got home from work. The numbers do not reset after reboot :) Blimey, that was clever. Thanks again.

---

### Post by DuckHook on 2018-01-19
*Please mark thread **solved** using *Thread Tools* in the top toolbar for the benefit of others searching for solutions*.

---

### Post by rigel4 on 2018-08-21
Thank you .. worked for me on an HP Pro 450 G2

---

### Post by Farbror on 2018-11-15
Such a beautyful solution. Txs. I have used Ubuntu and derivates since version 9 and have wondered ever since  why this is not included in touchpad-adjustments from beginning.

---

