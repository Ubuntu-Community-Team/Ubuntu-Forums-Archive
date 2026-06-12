---
title: "(emerald vs compiz) vs x11mouse"
date: 2008-10-07
forum: General Help
---

### Post by fib1807 on 2008-10-07
Well,all I knw is that emerald is a window decorator and compiz is a much bigger thing and manages the windows as well as the desktop effects.

So I've been using the following CL to switch b/n the two

<?> --replace

(?=emerald/compiz This I use coz I'm only able to initialize emerald this way,can't directly change by using the emerald-theme-manager)

Well my problem is that when I shift between emerald and compiz by using the abv,I'm unable to change X11 mouse at all.For ex: If I had a theme xyz when using compiz I can't change this x11 theme (I cannot shift to any other theme when using emerald again).I need to come back to compiz to achieve the x11 change.Well,however I thought compiz manages mouse themes  also and began usin' a satisfactory Gtk in replacement with emerald (with some transparent effects through gconf-editor).
But most times I've observed that when I shift b/n these two compiz fails to replace the window title bar I've tried fixin' x server etc. but still not happy coz it ruined the desktop further.So any ideas for solvin' the abv problems ?

Thanks geeks.

---

### Post by 16777216 on 2008-10-07
Compiz needs to be restarted before changes to the mouse cursor theme show up.
I recommend you install Fusion. Icon ```
sudo apt-get install fusion-icon
```Fusion lets you Choose a window manager such as Compiz, Metacity, KWM, XFWM, OpenBox, etc., as well choose between Emerald and Metacity style window decroatiors, restart your chosen WM and more all from a nice tray icon.

You may want to install Compiz-Config Settings Manager as well. ```
sudo apt-get install ccsm
```

---

### Post by fib1807 on 2008-10-07
Thanks budd.I thought that did help..but when I'm usin' compiz the window title bar vanishes.When I changed to metacity it was back again  (it's basically a metacity theme).But again I tried using an emerald theme so I switched to emerald via Fusion icon but..then it didn't reload the window manager properly i guess...I tried a several emerald themes which worked well otherwise.So any help ? Can u emphasize on "restart emerald/compiz/metacity"

Can u please temme if I'm not using the right driver (I'm running ubuntu on NVDIA FX 5200) also can someone enlighten me with what's an xserver and xorg
also what's xserver-xgl I've tried gathering some info but wanted a much more killer and straight explanation of dat.If someone's interested please do enlighten me otherwise atleast solve my damn! problem.Thanks all

---

### Post by fib1807 on 2008-10-08
everything's gone now.gnome-appearance-properties says "Desktop effects cannot be enabled"
tried dloadin' nvdia-glx-envy
but no finally
tried nvdia-glx-new
even this doesn't work (it worked earlier)
Finally to my horror it said "X server failed" or something when I rebooted.

---

### Post by loomsen on 2008-10-08
No need for horror trips. X failed is a little too less output tho.

Try and do this:
```

wget http://blogage.de/files/4359/download -O compiz-check && chmod +x compiz-check

```
and then
```

./compiz-check

```

And copy&paste its output along with your xorg.conf (/etc/X11/xorg.conf).

I'm sure you'll find someone to help you fixing everything.

---

### Post by loomsen on 2008-10-10
Oh, I must have missed your question about X anyhow.

Well, I'll try and explain it as comprehensive as I can.

As you might know, there are different runlevels during boot in Linux.
Each runlevel provides a certain step, such as initializing your basic hardware, initializing modules für your kernel, initializing harddrives, network-interfaces and so on.

Now, as linux is modular, there are runlevel you cannot directly interact with. For example, my computer doesn't ask me if I wanna build or omit anything after I chose the kernel to boot from grub.

Bootchart will show you the different runlevel, and what actually happens in each. 
Just a short example, you'll have to have your hard drives alive and prepared before you are able to properly use you network connections. So you hdds get mounted in an earlier runlevel.

Alright, so, when all modules are initiated, the last runlevel, the display manager such as gnome is initiated by activating the graphics driver.

The shell without a display manager is one runlevel below, which makes it possible to fix things from shell and simply start gdm without having to reboot the whole system, cause files in lower runlevel aren't affected by any hacks anyway. So the higher the runlevel, the higher the accessibility of your hardware for you as a user. 

Alright, hope you were able to follow me so far.
Now, lets assume our hardware has been made accesible as far as possible.

Now, there are different types of hardware. Input(mice, keyboards), output(video/graphics cards, fonts and such) and so on.

Now, what the X-SERVER as it is called actually does, is taking your computer as a basis and linkin a mouse and a keyboard to it, so that we are able to produce INPUT. 
Just for better comprehension: BIOS stands for Basic Input Output System.
So, this means Computer are based on 
INPUT(by us)--> 
computing our input command(like calculating or sth)
--> and returning an answer, OUTPUT, which is called STDOUT(STD=standard) 
(Actually there's a third component too, which is STDERR. STDERR are errors we aren't interested in, or just sth the PC prints while working on our Input -- most likely we are not interested in how the computing works, but just in STDOUT, so that STDERR gets omitted by redirecting this output to /dev/null)


OK, thats basically the whole story.

The X-SERVER! combines different ways, so that different parts of hardware are tied together so that we can use it. 
A Mouse without a screen to follow the pointer is actually completely useless. But if we get OUTPUT from our INPUT(=moving the mouse), we can use it for our purpose.

Thats it, thats what the X-Server does. It provides a way to combine different types of hardware to a 
Basic Input Output System
xorg = organization of the different components(such as which screen is connected which mouse, and how.)

This is all very basic, and if you have one mouse, one keyboard, one screen and one processing unit, there are not too many possibilities to organize them. But, as you may know, UNIX is a multiuser OS. 
This means, that multiple Outputs(screens), or multiple Inputs(Keyboards) can be assigned to only one Central Processing Unit. 

Well, thats what happens in X.
Lets assume we have 4 screens, 4 keyboards and one CPU.
Without 4 graphics cards, or at least ways to connect each screen, it will hardly be possible to use all 4. But that, in this case, is STDERR :)
So, imagine we actually have the capabilities to connect all peripherals(printer,screens(output)<<-soundcards(which can be both)->> (inputs)scanner,webcams...)

Now we gotta tell X how the designated users should be granted accesibility, and which hardware should be accesible from which user and so on. This is all trivial for single user CPUs, but UNIX wasn't written for single users, but for Enterprises in times when one CPU was bigger than a house. 

So the X-Architecture provides a way for system admins to allocate ressources, which have to be shared. 
User1 might just cut a Video, while User2 has to write emails whole day long. 
So User1 needs a lot more Power for his purpose than User2 does. 

And X allocates exactly that, the more powerfull graphics card to User1, the less powerfull is directed to User2 and so on...

--> So, all in all, X provides an environment to use CPUs by organizing the different components and allocating them --- in other words: it organizes them. Thats where the first part of the X-ORG stands for.
Well, I guess I explained the .CONF part enough as well.

Without it I wouldnt be able to connect my LCD-TV to my Laptop, get two independent Outputs, different resolutions, basically two computers, but still be able to acces both outputs with just one mouse and one keyboard. 
Thats what X does. Possibilities are endless as you can imagine.

I hope you've been able to follow me, it's pretty early in the morning in germany and I've been awake whole night long, however I tried to explain it as good as I can.

(Wow, I hope anybody reads this) 

OK, just my 2ct 

---oh well--- 

my 20ct more likely ^^

---

### Post by fib1807 on 2008-10-10
Cheers! Loomsen,..err..Can u tell me which book do u read to understand unix ? :P
You've given me the best explanation that I wouldn't find on the entire internet.I'm really thankful u could enlighten me with that simple language.Thanks I never thought someone could be so helpful.

and..hey this is what I got  when I did ./compiz-check

```
fib@azad:~$ ./compiz-check

Gathering information about your system...

 Distribution:          Ubuntu 8.04
 Desktop environment:   GNOME
 Graphics chip:         nVidia Corporation NV34 [GeForce FX 5200] (rev a1)
 Driver in use:         nv
 Rendering method:      None

Checking if it's possible to run Compiz on your system...  [SKIP]

 Checking for hardware/setup problems...           [SKIP]

At least one check had to be skipped:
 Error: No rendering method in use (AIGLX, Xgl or Nvidia) 

Would you like to know more? (Y/n) Y

 The nv driver is not capable of running Compiz, you need to install the
 proper driver for your graphics card. 

Check if there's an alternate (proprietary) driver available? (Y/n) Y
fib@azad:~$ /home/fib/.themes/choconome/gtk-2.0/gtkrc:556: error: unexpected end of file, expected character `='



```

Here's the attachment of my xorg.conf :)

---

### Post by fib1807 on 2008-10-10
This is my xorg.conf

---

### Post by loomsen on 2008-10-10
You're welcome bud.

Your xorg as well as compiz-check show you're using the free nv driver. Tho I don't know if it will actually work with your card, you should try and get a restricted driver directly from nvidia instead of using nv, which actually is the OpenSource driver. 
 
In doubt, I'd probably get 
nvidia-ng-toolkit and envyng-core
through synaptic, and let one of this tools chose and install the apropriate driver for me.
I got them both installed and didnt have any problems with kernel upgrades. I think this is the most chilled out solution, I can tell you, I had some pretty hard times running debian and trying to upgrade kernels to the bleeding edges. Actually thats the only thing I prefer on Ubuntu.

But I think your card is somewhat older, so you won't have to many problems anyway I guess :)



@X-org: Thanks for reading it I have to say I guess ^^
Actually, tbh, I have never read any book on Linux. Using it for like max 6 months or so, well, installed it earlier here n there, but since max 6 months it advanced to my main OS. 

Actually I don't even know where I know all that stuff from.

But, tbh, I always hoped that destroying countless numbers of DOS PCs way back when I was a Kid would have some positive aspects too :D

---

### Post by fib1807 on 2008-10-11
Oh! well thanks anyway bud.

---

### Post by fib1807 on 2008-10-11
So are u tryin' to say that I shouldn't be using an envy nvdia driver ?
what I did was I dloaded envy and let it check fetch some drivers automatically but guess it was unsuccessful.Well,I've used nvdia-glx-new (think it's restricted) and I seem to have no problem with it on my new ubuntu(new=newly installed) but..I've used it earlier too on the other ubuntu I didn't have any problem with restricted drivers then one day when I was tryin' fo' some really kewl compiz effects (cylindrical and spherical desktop) dunno what occured to my machine.I then thought of nv and may be I've overwritten the xorg.conf via (try xfix a several times) which might have actually ruined the case acc to my diagnosis.

Now how can I remove the entire nvdia drivers I tried 
sudo apt-get autoremove nvdia* and 
sudo apt-get remove nvdia --purge
but it wasn't able to recognize the driver perhaps

---

### Post by loomsen on 2008-10-11
Nope, I'm trying to say that you should be using nvidia instead of nv.

If you got the drivers installed, get a tool to have it autoconfigured if you like:
```
sudo apt-get install nvidia-xconfig

```

Then I'd recommend rebooting your system and choosing single user mode (might be called recovery mode for your OS, depending)

Then, drop to a root shell, and run 
```

nvidia-xconfig
```

It will set up your xorg for you.

To try if it actually set it up correctly, run(still in recovery/single user mode)
```

gdm
```

If gnome starts up fine, log out again and reboot your computer just as usual.

Then, if it's all set up correctly, and you're logged in as regular user again, backup your xorg.conf
Use a location you can easily remember, like your home dir, cause, if you need your backup you probably are in a shell having to fix things from there.

From now on, if sth goes wrong, or you reconfigure your X with default values somehow, just boot into single user mode, copy your backed up xorg to /etc/X11 replacing the one which wouldn't work, and X-errors should be history for you :)

---

### Post by fib1807 on 2008-10-12
Lovely I didn't have to upgrade the kernel directly dloaded those drivers from nvidia.com Thank god and Thank you...you've been really helpful through and through.Thanks a loooooooooooooooooooot.

---

