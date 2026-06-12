---
title: "[SOLVED] Gnome panel and notification area questions"
date: 2008-10-16
forum: General Help
---

### Post by Brandon81 on 2008-10-16
Somehow on my laptop I put the trash icon into the notification area and I have no idea how I did that. I would really like to do the same for my desktop. I'd also if possible like to place the viewport switcher in there too, as anytime the notification area changes size due to new icons anything on the panel all the way to the right doesn't automatically put itself back up against the notification area. 

I've searched for ubuntu notification area, and system tray, and I can't seem to find anything other then people who have accidentally lose their notification area. 

Thanks!

---

### Post by zvacet on 2008-10-16
I don´t know if I understand you correctly but it looks like you want to lock notification area.if that is the case 

```
gconf-editor
```

and then** apps>panel>applets>click on notification area>**unchecked locked and you can add more icons.After that you can lock it again.

---

### Post by Brandon81 on 2008-10-16
Yeah, the "system tray" in the upper right on ubuntu. 

That sounds like that would do the trick if it would allow me to move panel icons to it. 

Thanks!

---

### Post by Brandon81 on 2008-10-16
Okay, I was able to drag the trash and the viewport switcher into the notification area. 

I have the check now on lock and on panel_right_stick and it doesn't seem to be hugging the right. I have the viewport switcher all the way to the right, and to the left of that, the trash, and then to the left of that the notification icons. 

I opened an qpp that creates a notification icon, then closed the icon and the whole notification area moved left to make room for the icon and didn't collapse back, or hug the right so now there's a blank area between the notification icons and the trash. 

Any way to make the notifications hug the other icons on the bar that are to its right?

---

### Post by ryanhaigh on 2008-10-16
You aren't actually adding the trash icon and viewport switcher to the notification area. The notification area is its own applet as are trash and viewport switcher. Probably the easiest thing to do would be moving the trash and viewport switcher to the right of the notification area applet. You will probably have to unlock the applets to do this.

---

### Post by Brandon81 on 2008-10-16
Nevermind... I got it working how I want. Thanks :D

---

