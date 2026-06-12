---
title: "Monitor Troubles"
date: 2005-04-21
forum: Hardware &amp; Laptops
---

### Post by Jade Robbins on 2005-04-21
I installed ubuntu and it's great, but the only problem arises when my monitor isn't detected. T's a Dell E770p and i know it can go up to 1152x864 @ 72mhz. So i went into my xorg config and added that resoulution, but when i go to switch to that resolution the only refresh rate that is there is 75, which is just slightly too high. I added the Horizontal and Vertical refresh ranges in the config file, but still nothing. Any suggestions? Thanks in Advance.

Edit: Sorry i cross posted, but i really need help here :(

---

### Post by dataw0lf on 2005-04-21
Although we all understand that this is a 'major' problem, and you need help, cross posting is highly discouraged.  Please delete the clone post(s).  Thanks!

Did you restart X after you added the new refresh rates to the config?  If so, did the conf file retain them after the restart?

---

### Post by themelvin on 2005-04-21
Start the console and write this:
```

gtf 1152 864 72

```

Press enter.

Thene enter the line that says:
```

Modeline "1152x768_72.00"  88.58  1152 1224 1344 1536  768 769 772 801  -HSync +Vsync

```

In your /etc/X11/xorg.conf file under Monitor section:

It helped me.
[http://www.ubuntuforums.org/showthread.php?t=28654](http://www.ubuntuforums.org/showthread.php?t=28654)

But still didn't find a way to slightly change the position of the screen to the left :(

---

### Post by Jade Robbins on 2005-04-21
[QUOTE=dataw0lf]Although we all understand that this is a 'major' problem, and you need help, cross posting is highly discouraged.  Please delete the clone post(s).  Thanks!

Did you restart X after you added the new refresh rates to the config?  If so, did the conf file retain them after the restart?[/QUOTE]
I tried to delete the post, but i don't know how. I did ask a moderator to delete it, i guess i'm just used to more strict forums where you don't have the ability to delete your own posts. I'll try to find the way to delete it though, once again sorry about that.

A quick solution was i manually set my refresh rate in my xorg.conf and then manually set the resulution as the only option being the res i wanted. The resolution options shows it as 800x600 at 75 hz but it's really not. Works though, i'm happy.

---

### Post by Jade Robbins on 2005-04-21
[QUOTE=themelvin]Start the console and write this:
```

gtf 1152 864 72

```

Press enter.

Thene enter the line that says:
```

Modeline "1152x768_72.00"  88.58  1152 1224 1344 1536  768 769 772 801  -HSync +Vsync

```

In your /etc/X11/xorg.conf file under Monitor section:

It helped me.
[http://www.ubuntuforums.org/showthread.php?t=28654](http://www.ubuntuforums.org/showthread.php?t=28654)

But still didn't find a way to slightly change the position of the screen to the left :([/QUOTE]

wow i put everything back the way it should, put that line in my xorg.conf and it works BEAUTIFULLY. Thank you so much sir!

---

