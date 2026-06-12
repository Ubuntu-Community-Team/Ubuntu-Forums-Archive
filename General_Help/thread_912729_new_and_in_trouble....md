---
title: "new and in trouble..."
date: 2008-09-07
forum: General Help
---

### Post by davh11 on 2008-09-07
a few weeks ago i decided to use ubuntu. ik ordered a cd, which came quite fast. yesterday i installed it. i also installed all the updates which i had to install. but now i can't shut down my computer!

when i go to system -> shutdown, i see only these options: log out, lock screen, switch user and a pause function. but no shut down or something. when i log off and go to the menu, there is no way i can shut down.

can someone help me?

---

### Post by mb_webguy on 2008-09-07
I don't know why you aren't seeing the other shut down options...  You should have Restart and Shut Down, if not also Suspend and Hibernate.  However, if you really need to shut down your computer, open the terminal and type "shutdown now".  (I'm not entirely sure since I haven't needed to use it in a while, but you *may* have to append "sudo" to the beginning of that.  I'd try it and see, but I don't want to shut down my computer right now. :) )

You can also use the "reboot" command from the terminal to reboot your computer.

---

### Post by banewman on 2008-09-07
When you logout click on options at bottom left and there should be shutdown in the menu. :)

---

### Post by Neo_The_User on 2008-09-07
Another thing you can do is right click on the panel (where it says System, Places etc etc) and select Add to Panel. Scroll down the list to where you see "Quit" and you can add that to your tool bar / panel and see if that works.

To shut down ubuntu via Terminal it is

sudo shutdown -h now

---

### Post by 3rdalbum on 2008-09-07
You can shut down straight from the desktop by going to a terminal and typing:

```
sudo halt
```

Rebooting is this:

```
sudo reboot
```

It's very strange that you've lost Shutdown and Reboot as options.

---

### Post by MaxIBoy on 2008-09-07
Another way would be to log out, then go to the "options" button and click shut down.

---

