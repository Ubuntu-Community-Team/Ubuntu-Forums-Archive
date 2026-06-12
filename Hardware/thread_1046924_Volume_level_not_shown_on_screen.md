---
title: "Volume level not shown on screen"
date: 2009-01-21
forum: Hardware
---

### Post by again617 on 2009-01-21
My laptop is an IBM Thinkpad T41.  When I use the volume up and down buttons the volume does go up and down.  However, there is no display showing what the volume is at.

Yesterday, I plugged my Apple keyboard into my laptop and to my surprise when I used the volume buttons, I did in fact get visual feedback as to what the volume was at.

If I right click the volume applet on my menu bar and open Volume Control and watch the levels while changing volume something which I find odd happens.  When changing the level of the volume with my IBM volume buttons, the levels do not change.  When I change the volume with my Apple keyboard then I can see the Master level move up and down.

So where are my laptop volume buttons changing the volume?  In my Preferences -> Sound everything is set to ALSA.

---

### Post by pnutzh4x0r on 2009-01-22
You may want to check out: [http://www.thinkwiki.org/wiki/How_to_get_special_keys_to_work]("http://www.thinkwiki.org/wiki/How_to_get_special_keys_to_work").  It appears that you have do something like:

```
echo enable,0xffffffff >/proc/acpi/ibm/hotkey
```

To get the keys sent to the appropriate the acpi daemon, which will hopefully relay the key press to the on-screen display.  I'm not sure if this will work, but you can find more resources in the link above. 

You may also want to see if you can bind the keys in the Keyboard Shortcuts options dialog under System | Preferences | Keyboard Shortcuts.  Good luck.

---

### Post by again617 on 2009-01-22
Thanks, I'll try it out tonight when I get home.

---

### Post by again617 on 2009-01-22
> **pnutzh4x0r said:**
> 
```
echo enable,0xffffffff >/proc/acpi/ibm/hotkey
```


I get a permission denied when I try that.  Putting sudo in front of that didn't work so I searched and found this:
```
echo enable,0xffffffff | sudo tee /proc/acpi/ibm/hotkey
```
Which gives the output
```
enable,0xffffffff
```
Which seems correct but doesn't make any difference.  Putting the word disable instead of enable doesn't actually disable the buttons either.

> **pnutzh4x0r said:**
> 
You may also want to see if you can bind the keys in the Keyboard Shortcuts options dialog under System | Preferences | Keyboard Shortcuts.  Good luck.

That doesn't seem to work for me.  I select the Volume Up, I get the *New Accelerator* message but pressing the volume buttons don't get any values put in there.  But the volume does go up and down.

Thanks for replying to my post.  If you have any more ideas as to what is going on I would appreciate the help but this isn't a big problem for me -- more of a curiosity.

---

### Post by AnythingBut on 2009-04-14
Hey,

Are your volume keys generating acpi events?  Check by running acpi_listen and watch for things like
```
ibm/hotkey HKEY 00000080 00001015
ibm/hotkey HKEY 00000080 00001016

```

---

