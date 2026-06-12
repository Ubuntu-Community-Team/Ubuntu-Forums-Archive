---
title: "Logitech mx 1000"
date: 2005-06-27
forum: Hardware &amp; Laptops
---

### Post by POET250 on 2005-06-27
alright i'm still getting the hang of linux so i'm not too knowlegable.  but i had searched and all the guides here to get a mouse working correct had no mention of the mx 1000 and well i tried them ne ways and my mouse still isn't working.  i've installed imwheel but have no clue how to open it since its been hidden after the synaptic install.  i appreciate your help

---

### Post by FLeiXiuS on 2005-06-27
[QUOTE=POET250]alright i'm still getting the hang of linux so i'm not too knowlegable.  but i had searched and all the guides here to get a mouse working correct had no mention of the mx 1000 and well i tried them ne ways and my mouse still isn't working.  i've installed imwheel but have no clue how to open it since its been hidden after the synaptic install.  i appreciate your help[/QUOTE]

Are you reffering to the mouse buttons?  Because I'm pretty sure the MX1000 works by default :-P but the buttons do not of course.  What I'd do is the following...

```
sudo gedit /etc/X11/xorg.conf
```

Browse down to the mouse section and add the code below:

```

Option     "Protocol"     "**ExplorerPS/2**"
Option "Buttons"      "10" 
Option "ZAxisMapping" "9 10"        # adding this maps wheel scrolling events to mouse buttons 9 & 10

```
*Note: Remove overwrite the default protocol.  The object is bolded ahead.*

Save and with one last step, you'll be set.

```
sudo xmodmap -e "pointer = 1 2 3 6 7 8 9 10 4 5"
```

That should enable the buttons, let me know how it goes.

---

### Post by POET250 on 2005-06-27
*FleiXius well I did try and the results are as follows.  editing the config file went fine but the bit of code didn't work

poet@ubuntu:~$ sudo xmodmap -e "pointer = 1 2 3 6 7 8 9 10 4 5"
xmodmap:  commandline:0:  bad number of buttons, must have 5 instead of 10
xmodmap:  1 error encountered, aborting.
poet@ubuntu:~$

I'm not really sure what it all means. and thanks for your help

---

### Post by Coldsnap on 2005-06-28
I'm pretty new to Linux, as well, and I've also got the MX1000 Laser.

I tried to follow FLeiXiuS's advice, but I couldn't even get as far as POET250.  When I typed "sudo -n /etc/X11/xorg.conf" into the terminal, this is what I got:

sudo: illegal option `-n'
usage: sudo -K | -L | -V | -h | -k | -l | -v
usage: sudo [-HPSb] [-p prompt] [-u username|#uid]
            { -e file [...] | -i | -s | <command> }

Anybody have any suggestions?

---

### Post by POET250 on 2005-06-28
coldsnap the command is "sudo gedit /etc/X11/xorg.conf"  and it will bring up the xorg.conf file in a text editor so you can doctor that to make it what it should be

---

### Post by Coldsnap on 2005-06-28
Yeah, I figured that out, eventually.  Heh.  Pardon the noobness.

However, then I get the same error you do.

I found this on the net, but I'm not sure how to follow it, myself: [http://floam.sh.nu/index.xhtml?page=guides&section=mx1000](http://floam.sh.nu/index.xhtml?page=guides&section=mx1000)

---

### Post by POET250 on 2005-06-28
coldsnap good find but i too don't have the knowledge to do any thing with that help since i cannot even install a .deb or gtx file and haven't even tried to compile and files yet

---

### Post by FLeiXiuS on 2005-06-28
Blah sorry, I mis-typed the line to open /etc/X11/xorg.conf.  

sudo gedit /etc/X11/xorg.conf

---

### Post by FLeiXiuS on 2005-06-28
[QUOTE=POET250]*FleiXius well I did try and the results are as follows.  editing the config file went fine but the bit of code didn't work

poet@ubuntu:~$ sudo xmodmap -e "pointer = 1 2 3 6 7 8 9 10 4 5"
xmodmap:  commandline:0:  bad number of buttons, must have 5 instead of 10
xmodmap:  1 error encountered, aborting.
poet@ubuntu:~$

I'm not really sure what it all means. and thanks for your help[/QUOTE]

Read the instructions again, I fixed a typo that I had.  Sorry!

---

### Post by POET250 on 2005-06-29
FleiXius the last step in you instructions does not work results as follows

poet@ubuntu:~$ sudo xmodmap -e "pointer = 1 2 3 6 7 8 9 10 4 5"
xmodmap:  commandline:0:  bad number of buttons, must have 5 instead of 10
xmodmap:  1 error encountered, aborting.
poet@ubuntu:~$

and second the mx1000 has 12 buttons as listed on [http://floam.sh.nu/index.xhtml?page=guides&section=mx1000](http://floam.sh.nu/index.xhtml?page=guides&section=mx1000)

---

### Post by FLeiXiuS on 2005-06-29
For some ODD reasons I don't know why, but I was thinking of the MX510.  

The directions on [http://floam.sh.nu/?page=guides&section=mx1000](http://floam.sh.nu/?page=guides&section=mx1000) worked fine for my friend who has the **MX1000**.

Now I feel dumb, shoot me if you must.

---

