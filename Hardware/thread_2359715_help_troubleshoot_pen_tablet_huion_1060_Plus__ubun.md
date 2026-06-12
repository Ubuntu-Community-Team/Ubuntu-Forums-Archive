---
title: "help troubleshoot pen tablet huion 1060 Plus / ubuntu studio 16.04 and 17.4"
date: 2017-04-27
forum: Hardware
---

### Post by caramel-pegasus on 2017-04-27
// edit
  Update: 
  Scroll down a few post. 
  This is mostly solved by switching to 17.4 ubuntu and adding PTXconf
  Digimend was not needed after that. 
// end edit 


Desktop environment: XFCE 
Ubuntu studio 16.04 
Huion pen tablet 1060 plus

Problem: Partially working, but not quite there.
As of now, the pen and tablet are working (except tablet buttons.) However, when i draw a circle, i get an oval. I have multiple screens (3) 
I'm ok with confining the tablet to just one as long as it works. But i don't know how. 


Following these instructions: [https://github.com/DIGImend/digimend-kernel-drivers/issues/26](https://github.com/DIGImend/digimend-kernel-drivers/issues/26)
(I was following these instructions because I was told the 1060 is pretty much identical to the 610 
 except the 1060 plus has larger surface and more buttons. )

I am currently stuck at the last part of:  
"(1.3) Setting up an 52-tablet.conf entry for the H610" 
Which states: 

```

d) upon restarting, when you open Terminal and input:
xsetwacom --list

(you should see:)    
HUION PenTablet Pad pad id: 11 type: PAD
HUION PenTablet Pen stylus id: 12 type: STYLUS
(the id will vary from machine to machine)

``` 

Problem is, I don't see that output. I get nothing at all. 
What can i do to troubleshoot this? 


Some additional info:

xinput --list
```
 caramel@pegasus-device /etc/X11/xorg.conf.d $ xinput list&#9121; Virtual core pointer                        id=2    [master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer                  id=4    [slave  pointer  (2)]
&#9116;   &#8627; Logitech M705                               id=8    [slave  pointer  (2)]
&#9116;   &#8627; Logitech M705                               id=9    [slave  pointer  (2)]
&#9116;   &#8627; PenTablet  Pen                              id=10    [slave  pointer  (2)]
&#9116;   &#8627; PenTablet  Pad                              id=11    [slave  pointer  (2)]
&#9116;   &#8627; PenTablet  Mouse                            id=12    [slave  pointer  (2)]
&#9116;   &#8627; PenTablet  Consumer Control                 id=14    [slave  pointer  (2)]
&#9116;   &#8627; Dell Dell Wired Multimedia Keyboard         id=17    [slave  pointer  (2)]
&#9123; Virtual core keyboard                       id=3    [master keyboard (2)]
    &#8627; Virtual core XTEST keyboard                 id=5    [slave  keyboard (3)]
    &#8627; Power Button                                id=6    [slave  keyboard (3)]
    &#8627; Power Button                                id=7    [slave  keyboard (3)]
    &#8627; PenTablet  Keyboard                         id=13    [slave  keyboard (3)]
    &#8627; PenTablet  System Control                   id=15    [slave  keyboard (3)]
    &#8627; Dell Dell Wired Multimedia Keyboard         id=16    [slave  keyboard (3)]
caramel@pegasus-device /etc/X11/xorg.conf.d $ 

```



LSUSB
```
 
caramel@pegasus-device ~ $ lsusb
Bus 002 Device 003: ID 413c:2110 Dell Computer Corp. 
Bus 002 Device 002: ID 413c:1010 Dell Computer Corp. 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 006: ID 058f:6366 Alcor Micro Corp. Multi Flash Reader
Bus 001 Device 004: ID 256c:006e  
Bus 001 Device 002: ID 058f:6254 Alcor Micro Corp. USB Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 002: ID 046d:c52b Logitech, Inc. Unifying Receiver
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 0a12:0001 Cambridge Silicon Radio, Ltd Bluetooth Dongle (HCI mode)
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
caramel@pegasus-device ~ $ 

```


Xorg at ubuntu paste: 
[http://paste.ubuntu.com/24485714/](http://paste.ubuntu.com/24485714/)

---

### Post by mörgæs on 2017-04-27
Hi, welcome to the fora.

As always with new hardware: Have you tried how it works in a live boot of 17.04?

---

### Post by caramel-pegasus on 2017-04-27
> **mörgæs said:**
> Hi, welcome to the fora.

As always with new hardware: Have you tried how it works in a live boot of 17.04?

Great news: Huion 1060 Plus is showing signs that it might be working out the box in 17.04 
booted a live ubuntu studio and then i plugged the pen tab in. The buttons on the tablet seem to have nothing assigned. But the pen works as expected. I launched krita and did a quick sketch, pressure sensitivity is there, pen buttons work, but i have not tested the tablet buttons further. 

I disabled all the extra monitors and my circles are true circles, not ovals. I'm hoping there is a solution for that i can explore. 
Tried loading blender 3d, and it seems to somewhat work, im getting some serious lag when attempting sculpting but that could be just the live setup with no nvidia drivers...? maybe? 

I'll be installing 17.04 studio when i get home tonight and post an update to my experience. 
Thank you for the suggestion!

---

### Post by pdc on 2017-04-27
one wonders if this could be a good effect of the 4.10 kernel; that I understand 17.04 comes with; whereas likely 16.04 is running on 4.4; so one could install a newer kernel on 16.04 without perhaps needing a 17.04 install; 17.04 is only going to last till Jan 2018; 16.10 expires in 3 months;

There were issues with the x-pen; and reading bug reports on that; I felt that work on that too was to go into newer kernels as well; 

I think 4.11 has been delayed by a further week; for further testing; [http://news.softpedia.com/news/linux-kernel-4-11-to-launch-on-april-30-as-linus-torvalds-released-eighth-rc-515113.shtml](http://news.softpedia.com/news/linux-kernel-4-11-to-launch-on-april-30-as-linus-torvalds-released-eighth-rc-515113.shtml)

this link talks about various tablet improvements for the 4.11 kernel [http://lkml.iu.edu/hypermail/linux/kernel/1702.2/02470.html](http://lkml.iu.edu/hypermail/linux/kernel/1702.2/02470.html)

and from discussions like this [https://www.reddit.com/r/linux/comments/5vbld0/wacoms_intuos_pro_to_be_supported_by_the_linux/](https://www.reddit.com/r/linux/comments/5vbld0/wacoms_intuos_pro_to_be_supported_by_the_linux/) it is clear many are buying many different brands of tablets; that are in many cases enthusiastically used and acclaimed

---

### Post by caramel-pegasus on 2017-04-30
> **pdc said:**
> one wonders if this could be a good effect of the 4.10 kernel; that I understand 17.04 comes with; whereas likely 16.04 is running on 4.4; so one could install a newer kernel on 16.04 without perhaps needing a 17.04 install; 17.04 is only going to last till Jan 2018; 16.10 expires in 3 months;

There were issues with the x-pen; and reading bug reports on that; I felt that work on that too was to go into newer kernels as well; 

I think 4.11 has been delayed by a further week; for further testing; [http://news.softpedia.com/news/linux-kernel-4-11-to-launch-on-april-30-as-linus-torvalds-released-eighth-rc-515113.shtml](http://news.softpedia.com/news/linux-kernel-4-11-to-launch-on-april-30-as-linus-torvalds-released-eighth-rc-515113.shtml)

this link talks about various tablet improvements for the 4.11 kernel [http://lkml.iu.edu/hypermail/linux/kernel/1702.2/02470.html](http://lkml.iu.edu/hypermail/linux/kernel/1702.2/02470.html)

and from discussions like this [https://www.reddit.com/r/linux/comments/5vbld0/wacoms_intuos_pro_to_be_supported_by_the_linux/](https://www.reddit.com/r/linux/comments/5vbld0/wacoms_intuos_pro_to_be_supported_by_the_linux/) it is clear many are buying many different brands of tablets; that are in many cases enthusiastically used and acclaimed

I would have to try that in a VM unless you know a way to reboot a live pen drive while keeping modified settings.

---

### Post by caramel-pegasus on 2017-04-30
> **caramel-pegasus said:**
> Great news: Huion 1060 Plus is showing signs that it might be working out the box in 17.04 
booted a live ubuntu studio and then i plugged the pen tab in. The buttons on the tablet seem to have nothing assigned. But the pen works as expected. I launched krita and did a quick sketch, pressure sensitivity is there, pen buttons work, but i have not tested the tablet buttons further. 

I disabled all the extra monitors and my circles are true circles, not ovals. I'm hoping there is a solution for that i can explore. 
Tried loading blender 3d, and it seems to somewhat work, im getting some serious lag when attempting sculpting but that could be just the live setup with no nvidia drivers...? maybe? 

I'll be installing 17.04 studio when i get home tonight and post an update to my experience. 
Thank you for the suggestion!


UPDATE: 
It's working fine in 17.4 ubuntu Studio. Pressure sensitivity works great in Krita. (I still have not tested mapping buttons) 
I found a solution to a problem I was having when using multiple monitors. If i had multiple monitors, the tablet would scale in size to all monitors combined. 
This was a problem because circles drawn on the tablet became ovals. 
 See this image:
[IMG]http://orig14.deviantart.net/a176/f/2017/120/1/9/18216717_1784094595251466_8268619512112421433_o_by_caramel_pegasus-db7m7h4.jpg[/IMG]

There is a program called PTXconfig that rests in the system tray which address this problem. 
See this website for details: [http://wenhsinjen.github.io/ptxconf/](http://wenhsinjen.github.io/ptxconf/) 

Basically, you select the input device, and bind the pen to a display, and you also bind the tablet to the same display. 
You have to do both, pen and tablet. 
[IMG]http://orig08.deviantart.net/c944/f/2017/120/1/6/config_menu_by_caramel_pegasus-db7m724.jpg[/IMG]


The down side is that you can only use the pen and tablet in that monitor BUT you can always configure which monitor you want to use without having to signout/signin. 
A nice feature would be to implement a way to bind the scale to the application window similar to how OBS-studio can bind recording to just specified program. This way, you can always move the window to another screen and still have the pen/tablet draw in it. 
Not sure what difficulties that entails but i'd love to run that by the developer and also thank him/her/them for their work. 

Anyway, Go check out their website if you are having this issue: 
[http://wenhsinjen.github.io/ptxconf/](http://wenhsinjen.github.io/ptxconf/)

---

### Post by mörgæs on 2017-04-30
Good, if you are satisfied then please mark the thread 'solved'. Thanks for the thorough explanation, it might help others.

Also it would be great if you could encourage other people using old software on new hardware to move on and see what 17.04 has to offer.

---

