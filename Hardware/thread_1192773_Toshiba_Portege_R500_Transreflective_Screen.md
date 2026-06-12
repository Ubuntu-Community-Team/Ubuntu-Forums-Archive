---
title: "Toshiba Portege R500 Transreflective Screen"
date: 2009-06-20
forum: Hardware
---

### Post by hamidaddin on 2009-06-20
I have just installed Ubuntu 9.04 (Jaunty Jackalope) on a Toshiba Portege R500 that comes with the ability to switch off the screen back light (called transreflective mode) to preserve battery power.

By default ubuntu installed a utility called toshset. Below is the package description in Synaptic:

> This is a collection of utilities to control a Toshiba laptop. It includes programs to turn the fan on and off, to view the power mode, and to set the supervisor password.

The toshset utility can toggle the transreflective mode on and off but ubuntu does not recognize the transreflective hotkey and therefore I created a simple script to toggle the transreflective mode on and off.

I am not an expert, so there might be better ways of doing this. But anyways, this does the job.

I will put here a step by step guide to activate the transreflective toggle hotkey:

1- Open your text editor and paste the following code:
```
#!/bin/bash
trmode_status=$(gksudo "toshset -q *transreflective*")
echo $trmode_status | grep "on"
if [[ $? -eq 0 ]] ; then
	gksudo "toshset -trmode off"
else
	gksudo "toshset -trmode on"
fi 

```

2- Save the file as trmode-toggle.sh

3- Go to the folder you saved your file in using your file browser and right click on the file. Choose "Properties" then go to the "Permissions" tab and make sure that the "Execute" check box is marked.

4- In the main menu, go to System => Preferences => Keyboard Shortcuts

5- Press "Add" then write "Toggle Transreflective Mode" as the Name and "./location/of/the/script/trmode-toggle.sh" (dot then the path to the script then the script name)

6- A new shortcut will be created under "Custom Shortcuts" named "Toggle Transreflective Mode". Press "Disabled" and when you see "New shortcut.." press the Transreflective hotkey at the top right corner of your keyboard. Then press "Close"

That should be all. Please note that the Transreflective hotkey and the Toshiba Help hotkey next to it are not being distinguished by ubuntu (yet). Therefore, if you press any of the two buttons, you will get the same resule. Both buttons are recognized by ubuntu as "XF86HomePage". If you prefer, you can choose another key combination to toggle the Transreflective mode (e.g. Alt+Shif+T) and use the hotkeys to launch the browser.

On another subject, if anyone gets the built-in 3G working please let me know. I think the new version of [toshset (1.75)]("http://schwieters.org/toshset/") solves it but I did not test it yet .

Hope you find this useful...

Yahya Hamidaddin

---

### Post by llelkes on 2009-07-23
Hi, I just installed toshset 1.75 and 3g is working :D

toshset -3g on

now only need a nice gui or some nice trick to call it before establishing the connection (toshset-gui till now did not support it)

Bye...
Laci

---

### Post by hamidaddin on 2009-07-23
Thanks llelkes,

I've written a step by step guide on how to fix this here:

[http://ubuntuforums.org/showthread.php?t=1221077](http://ubuntuforums.org/showthread.php?t=1221077)

The guide should be obselete for users of ubuntu karmic 9.10 since that version will have the new version of toshset. Hopeful it will also have the hardware added to the option kernel module.

Thanks..

---

