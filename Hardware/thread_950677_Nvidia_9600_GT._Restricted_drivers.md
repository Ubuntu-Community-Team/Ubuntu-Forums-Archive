---
title: "Nvidia 9600 GT. Restricted drivers?"
date: 2008-10-17
forum: Hardware
---

### Post by Roasted on 2008-10-17
I have a 9600 GT, brand new computer. Ubuntu Hardy Heron 64 bit. I ended up installing the latest Nvidia driver via EnvyGTK. It seems to work, but I can't run Compiz right. Compiz just won't take custom settings... it reverts back to normal settings. So, I figured it may be the driver. But there's no restricted drivers available. Hmm...

So I went on Nvidia's site and I saw a driver available for it, requiring me to download their tarball and unpack it and use a command they had listed on their web site. Even in command line mode when I boot up, it yields me with an error, saying I'm already in an x-server, or something.

In short, I'm bored of this. It's a graphics card, a very popular one. Where's the driver for it? Why are the instructions I'm following not working?

---

### Post by ajgreeny on 2008-10-17
Make a note of the command then start in recovery mode, go to the console and use the command again.  You will not be able tyo use the command when running in graphical mode.  You could also use Ctrl+Alt+F1 to get a terminal screen, then run ```
sudo /etc/init.d/gdm stop
``` to stop the graphical session, then run the command again, probably with sudo at the front.  Then you can either just go back to a graphical session with ```
sudo /etc/init.d/gdm start
``` or ```
startx
``` or ```
reboot
```

---

### Post by Roasted on 2008-10-17
Hmm... makes sense. I wonder why it isn't on the Nvidia site... or maybe I missed it. That little part of information may help a lottt of people.

Also - I mentioned my compiz settings won't stick. Do you folks think this is related to my graphics card driver with Envy? I have the latest driver via manual install with Envy, but nonetheless, it's there. I'm not sure if the driver on Nvidia's web site would make a difference or not, but I'm hoping it would. 

Thoughts?

---

### Post by Roasted on 2008-10-18
I installed this driver.

My compiz settings won't stay on custom, still.

I'm going to reinstall Envy-GTK, since it seems easier and does the same job.

Meanwhile, somebody PLEASE help me figure out what the **** is wrong.

EDIT - Okay, I put Envyng-gtk back in, and now I can select custom, but when I hit apply it says desktop effects could not be enabled. I manually installed the latest driver, 173 something, available with Envy.

Ideas?

---

### Post by Roasted on 2008-10-19
:confused:

---

