---
title: "Gnome-panel start hidden? (Hide buttons, not auto-hide)"
date: 2008-08-06
forum: General Help
---

### Post by the real omni on 2008-08-06
Hi,

I have my gnome panel set to display the hide buttons. In general I like to have just the one button visible to show the panel if needed, but I keep it hidden for the most part except for the one 'show' button (doesn't say 'show', it just has a little arrow that slides the gnome-panel into view)

My problem is that even if the panel is hidden when I log out, it starts in full view when I log back in.

I've tried saving my session before logging out... same results.

Is there a way to set the panel to hide automatically upon login?

---

### Post by the real omni on 2008-08-09
(bump) Any weekend warriors able to help on this one?

---

### Post by shakma on 2008-10-09
I want this same thing!  I want to start Cairo-dock on boot, and I don't need that extra gnome panel.  I, too, have it hiding with the little arrows, but I want it to start hidden when I login.

I can't solve the problem, but I can bump the thread!

Peace.
shakma

---

### Post by Het Irv on 2008-10-09
It sounds like you should be able to find the file that handle the show/hide function of the Gnome panel and change a "true" to a "false" or something like that.

As to where is file is I don't know, but maybe someone else does?

---

### Post by fooman on 2008-10-09
well.  i dunno about starting the panel in "hide" mode...but when i use AWN,  i just delete the panel(s) entirely.  the bottom panel can be removed by right clicking an empty spot on it and choosing "delete this panel" from the drop down list.  the top panel is a bit tricky...

to do that,  go to system > preferences > sessions

in the sessions window,  click the "current session" tab.  find "gnome-panel" in the list and click once on it to highlight it...then click on the "remove" button.  next, click on the "session options" tab and choose "remember currently running programs".  now if you logout/login or restart...the desktop should come up with no panels.

to get the panels back again....press alt-f2 to bring up a run dialog box.  in the space, type or copy paste:

```
gnome-panel &
```

click the "run" button and your top panel should be back.  to get the bottom one back,  right click an empty spot on the top panel and choose "new panel".

---

### Post by CJay554 on 2008-12-19
This would be a nice feature as i hide my multiple deskspace diagram in its biggest form for better viewing.. but every time i restart or log in i must constantly wait for it to load and then hide it, i also have my media control hidden as well and a few apps/system monitor for quick viewing... Anyone have any idea on this?

bump*

---

### Post by indosupremacy on 2009-09-13
the same thing i want to have too in my desktop....bump...

---

### Post by nrundy on 2010-12-19
I want the Top Panel to stay hidden too (when it was hidden on logout).  Anybody have a solution for this?

---

### Post by halabb on 2011-01-07
bump

Clicking the left hide button at startup isn't a horrible task but this is linux, I shouldn't have to be confined to a mouse click.

---

### Post by nrundy on 2011-01-10
> **halabb said:**
> bump

Clicking the left hide button at startup isn't a horrible task but this is linux, I shouldn't have to be confined to a mouse click.

 What does "bump" mean?

---

### Post by alladnsane on 2011-01-18
I would really like this to work as well. again it's not too difficult to click the hide button but would really like it too work by default

---

### Post by flomar on 2011-03-02
I am using Docky exclusively as my panel, however I think there is no way to totally delete all panels, therefore and because I need it every once in a while, I keep a panel hidden on the right bottom.

I really dont like having to klick away that ugly dock on the right side every time I boot!

---

### Post by 741Baus on 2011-03-04
If you wish to remove both top and bottom panels open a terminal and run this code,
```
sudo chmod -x /usr/bin/gnome-panel
sudo reboot
```

However this creates problems if you have more than one user on your machine as they have no panels , to revert back to having top and bottom panels again rerun the above code changing - to + ,

```
sudo chmod +x /usr/bin/gnome-panel
sudo reboot
```

and your panels will reappear.

---

### Post by Chriske on 2011-06-03
I'd like this too! :)

Time for a bit of Googling methinks...

---

### Post by tomasijeaux on 2011-06-21
Hope someone will solve this, I just spent lot of time googling with no result :-|

---

### Post by JepUbu on 2011-07-22
Hi!

I had the same problem and finally I have found this tool "xdotool" ([http://www.semicomplete.com/projects/xdotool/](http://www.semicomplete.com/projects/xdotool/)) that emulates the mouse movement. The command to minimize the panel is:
xdotool mousemovement 1 798 click 1
with that command I am putting the mouse on the button and pressing it. After checking that the command works, all I have to do is writing in the startup application with a few seconds of delay.

Yours sincerely,
Josep Bonet.

---

### Post by jasir on 2011-09-07
Here's the best way to hide the gnome panel: 

1. install compiz and ccsm 
2. open ccsm and enable the "widget layer" feature 
3. in the widget layer options, go to "behaviour" tab 
4. add the line "name=gnome-panel" (without quotes) in the field "widget windows" 
5. close ccsm

Once this is done you will see the gnome panels only when you display the widget layer. the default key for this is "F9"

---

