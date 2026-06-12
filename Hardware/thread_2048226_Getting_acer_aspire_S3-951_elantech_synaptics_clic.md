---
title: "Getting acer aspire S3-951 elantech synaptics clickpad right click working"
date: 2012-08-26
forum: Hardware
---

### Post by InuY4sha on 2012-08-26
For those having troubles with rightclick on synaptics clickpads on *ubuntu 12.04 you can edit the clickpad config with synclient tools:
Use this command
```
synclient -l
```
to list you clickpad properties;Among them find the following:

```

    LeftEdge                = 106
    RightEdge               = 2558
    TopEdge                 = 103
    BottomEdge              = 1821
```

These numbers determine the XY coordinates of your topleft to bottomright corner of your clickpad [for some reason in my case the top-left doesn't start from (0,0) coordinates, but no panic].

Now tell your kernel/drivers that you have a clickpad:

```
synclient clickpad=1
```

Enable the right click if it was not:

```
synclient RBCornerButton=2
```

This tells that the Right-Bottom corner button is assigned to mouse button "2" (that should be the right click event).

Finally specify an area in which the right click is accepted. This area  corresponds to a rectangle in the bottom right corner of your clickpad (in my case I configured it to take the whole right half of the lower board of the clickpad:

```
synclient RightButtonAreaLeft=1300 RightButtonAreaRight=2558 RightButtonAreaTop=1600 RightButtonAreaBottom=1821
```

Now if you CLICK (not TAP) on the lower right corner of the clickpad you should be able to see the right click action.

---

### Post by Seborreia on 2013-03-11
Thank you for the post InuY4sha!
It works for me, though when I restart my computer, right click stops working again. Is there any workaround for that?

Thanks!

---

### Post by Toz on 2013-03-11
Try the following procedure to get those commands to execute when you log on (all commands to be issued from a terminal window):

1. Create a file for those commands:
```
leafpad $HOME/touchpad
```
...and copy/paste these commands into the window:
```
#!/bin/bash
synclient clickpad=1
synclient RBCornerButton=2
synclient RightButtonAreaLeft=1300 RightButtonAreaRight=2558 RightButtonAreaTop=1600 RightButtonAreaBottom=1821
```
...then save and close the file.

2. Make the file executable:
```
chmod +x $HOME/touchpad
```

3. Add the file to your startup programs via Settings Manager -> Session Startup -> Application Autostart.

---

