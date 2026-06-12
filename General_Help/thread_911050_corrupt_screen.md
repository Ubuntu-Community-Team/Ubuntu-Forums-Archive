---
title: "corrupt screen"
date: 2008-09-05
forum: General Help
---

### Post by mukiduk on 2008-09-05
I have just again installed 8.04 and it was running ok until I changed the screen resolution to 800x600. Now, when I boot, it seems to run ok until it tries to open the desktop. It shows hundreds of horizontal lines close together and I cannot read anything on the screen. 
I assume it is because of the resolution and ubuntu does not like it. I am using a crt monitor and the resolution was set very high and everything was very small. That is why I wanted to change it.
The problem now is how do I change the resolution back even though I cannot see anything on the screen. 

I am a rank newby and cannot understand anything about the terminal commands.

---

### Post by Crafty Kisses on 2008-09-05
Post the results of this command: ```
glxinfo
```

---

### Post by Threbus5 on 2008-09-05
Hi,
I just posted a similar response.
Try this,
turn the computer off,
restart it,
as soon as you see grub start to load, press escape.
That will bring up a series of restore or test options.
select the one that indicates to restart or enable or repair the x-server. If the process asks questions, keep saying yes.
After the x-server repairs itself, restart the computer again.

If that works you should have the Ubuntu auto selected resolution and should see the screen.

Then, although you may want to select 800X600 resolution, try working with the default for a while before experimenting again. (I observe that screen resolution issues seem fairly common with Ubuntu 8.04)

Best of fortune.

---

