---
title: "instaling gtkpod and webcam driver"
date: 2008-11-18
forum: General Help
---

### Post by fusionxtc on 2008-11-18
hey, currently a noob at linux
wondering if anyone could help me out with an install with gtkpod for syncing music from linux to ipod. TUTORIAL IF POSSIBLE, also to update driver for a hp dv6000 internal webcam.

---

### Post by Twitch6000 on 2008-11-18
For your webcam just go to terminal and type sudo apt-get install cheese

Or go to applications>add/remove then choose all programs then type in cheese

Then check for install and install from there.

After that you can use cheese to setup your webcam.(it works with most built in webcams)

As for gtkpod same thing except type in gtkpod instead of cheese :).

However I know Amarok is better for syncing and working with an ipod.

---

### Post by fusionxtc on 2008-11-18
Reading package lists... Done
Building dependency tree       
Reading state information... Done
cheese is already the newest version.
The following packages were automatically installed and are no longer required:
  vorbis-tools id3v2 libid3-3.8.3c2a
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.



what would i do next after i put that into the terminal. 
i tried going through the add/remove apps and typed in cheese but nothing showed up.

---

### Post by Twitch6000 on 2008-11-18
> **fusionxtc said:**
> Reading package lists... Done
Building dependency tree       
Reading state information... Done
cheese is already the newest version.
The following packages were automatically installed and are no longer required:
  vorbis-tools id3v2 libid3-3.8.3c2a
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.



what would i do next after i put that into the terminal. 
i tried going through the add/remove apps and typed in cheese but nothing showed up.

It seems cheese is installed so there are two ways to start it.

The CLI way(command line) and the GUI way(grahpical user interface).

If I am right cheese will be under somewhere under apps not sure where.

For the CLI way just go under terminal and type cheese and the program will start up.

---

### Post by fusionxtc on 2008-11-18
yes the application was installed thank you for that. 
but when running the application i get a No Camera Found Error :\

what should i do with that?

---

### Post by Twitch6000 on 2008-11-18
> **fusionxtc said:**
> yes the application was installed thank you for that. 
but when running the application i get a No Camera Found Error :\

what should i do with that?

Humm stumped there might have to wait for someone else to help you with that.

---

### Post by easoukenka on 2008-11-19
I would install skype it works with more webcams and I think better for troubleshooting.  I still have not gotten cheese to work with mine.  

sudo apt-get install skype

Now type in skype(or click on your menu)  goto options and video devices.  There should be a drop down box make sure your webcam is selected and click test.  My linux always likes to default to my TV card as my webcam every boot and I need to change this.

If this does not work please in terminal type lsusb and paste that information here.  

Then unplug your webcam and type dmesg and paste the end of that anything having to do with your webcam here.  

Now plug it in run dmesg again and paste any of that information here.

---

### Post by fusionxtc on 2008-11-19
the skype install didnt work

the webcam doesnt work all together. it doesnt work on websites such as stickam.com either. the webcam is a built in webcam for my laptop.

maybe i just need to find a driver for it?

mike@mike-laptop:~$ lsusb
Bus 002 Device 007: ID 05ac:1260 Apple, Inc. iPod Nano 2.Gen
Bus 002 Device 002: ID 0c45:62c0 Microdia Pavilion Webcam
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 003: ID 046d:c521 Logitech, Inc. MX620 Laser Cordless Mouse
Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
mike@mike-laptop:~$

---

### Post by Twitch6000 on 2008-11-19
> **fusionxtc said:**
> the skype install didnt work

the webcam doesnt work all together. it doesnt work on websites such as stickam.com either. the webcam is a built in webcam for my laptop.

maybe i just need to find a driver for it?

mike@mike-laptop:~$ lsusb
Bus 002 Device 007: ID 05ac:1260 Apple, Inc. iPod Nano 2.Gen
Bus 002 Device 002: ID 0c45:62c0 Microdia Pavilion Webcam
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 003: ID 046d:c521 Logitech, Inc. MX620 Laser Cordless Mouse
Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
mike@mike-laptop:~$

Mind also giving the skype error message?

As for your webcam driver there is one,but i do not know where to get it. I know someone else can probably get it for you pretty easy.

---

### Post by fusionxtc on 2008-11-19
thanks you for all your help

i got the gtkpod working and transfering the files to the ipod. the only thing im having trouble with is transfering playlists. any good ways to do so?

---

### Post by Twitch6000 on 2008-11-19
> **fusionxtc said:**
> thanks you for all your help

i got the gtkpod working and transfering the files to the ipod. the only thing im having trouble with is transfering playlists. any good ways to do so?

Well since you are using gtkpod I would not know maybe look on the gtkpod site or wait for a response from someone who has used it :).

Edit: Well I have found the gtkpod's irc channel maybe you can get help with that there.

the irc channel is - #gtkpod on irc.freenode.net

just get xchat to go on there >.>.

its in the repos so it should be easy to find.

Or you can go to the terminal and type sudo apt-get install xchat

---

