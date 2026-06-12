---
title: "Installing on Laptop with Broken LCD"
date: 2009-08-23
forum: Hardware
---

### Post by ben.clark on 2009-08-23
Hi there, I'm new to Linux so I'm experimenting with an older broken HP laptop I have. The machine itself is ok although it won't boot into windows, it will run the LiveCD. The problem here is that the LCD screen is totally screwed, only a tiny portion works, enough to know where I am in the menus to start the LiveCD but nothing more.

What I want to do is use the S-Video output on my laptop to connect to my TV as an external monitor so I can use the machine again. I've tried looking this up online and found the display preferences but the computer/ubuntu isn't recognizing my tv as a screen.

I'm sure there must be a way to do this but without a screen working in the first place it's kinda hard to do anything.

Hopefully someone out there can help.

Thanks Ben

---

### Post by theozzlives on 2009-08-23
Do you have an external monitor you can plug into the laptop?

---

### Post by ben.clark on 2009-08-23
Sadly no, although I will be keeping my eye's on Freecycle for one as obviously that should be auto-recognised. Any idea for the TV? I heard about modifying some file although obviously I can't do that without a working screen in the first place.

---

### Post by theozzlives on 2009-08-23
> **ben.clark said:**
> Sadly no, although I will be keeping my eye's on Freecycle for one as obviously that should be auto-recognised. Any idea for the TV? I heard about modifying some file although obviously I can't do that without a working screen in the first place.

Without seeing what your doing it's hard, almost impossible.

---

### Post by ben.clark on 2009-08-23
Using my working laptop I put the LiveCD in for the 9.04 build of Ubuntu, go through the few menu's to get it working (writing down the key presses needed for later on the non-working laptop). Since my 2 laptops are the same model I then connected it up to the TV and entered the "Display Prefences" dialog, and the S-Video output to the TV is not recognised.

Reading online I believe there is a file that can be modified to activate the S-Video output however obviously this can only be done on the broken machine itself so either I need to as you suggest get an actual monitor to connect to the standard display output or pray that someone here knows of some way to get the S-Video output working with a default install straight from the LiveCD.

---

### Post by kruzztee on 2009-08-23
I want to share my experience installing Ubuntu on my broken Toshiba M200. It have severe graphic issue, that always display scanlines on the LCD and VGA output.

Basically I use other laptop (HP TC4200) to install Ubuntu 8.10 inside my Toshiba M200 hardrive. I didn't make any changes on the fresh installed Ubuntu 8.10. I just add a VNC server for a remote access. I used XDMCP for remote login, I forgot the steps but I found it on Ubuntuforums.org (I did a search and if I'm not mistaken I use this steps [http://ubuntuforums.org/showthread.php?t=795036&highlight=vnc+xdmcp](http://ubuntuforums.org/showthread.php?t=795036&highlight=vnc+xdmcp)).

Test out the installation fresh access... SUCCESS.

I move the hardrive to my broken laptop, hook up the LAN to my router. Fire it up.
Then I Access it using RealVNC or Ubuntu Remote Desktop Access.

---

### Post by ben.clark on 2009-08-25
I had thought about swapping the hard drives round and although I've done it once in the past I don't want to take the risk again as doing what I want to do with Linux right now isn't essential. Since these seem to be the few ways of doing what I want I'm just gonna have to wait till I can get access or get a proper monitor to hook up to it.

Wierd thing is one of my other computers has a broken monitor too, but will boot to windows and uses the S-Video output without any problems, tried the LiveCD of Ubuntu on it and the S-Video output worked perfectly. I wonder if the "Fn+F4" button combination I have to hit to turn on the outputs only works in windows but activates something hardward based that remains set afterwards?

Hopefully it's not a windows only thing and I can get this working, if not I've got a nice hunk of junk to take apart and have fun with lol

---

### Post by ben.clark on 2009-08-26
Hi there, well I got a monitor and sadly it seems that the outputs are shot, I can't do anything without seeing the screen in the first place and windows won't boot at all which leads to me to wonder if the hdd is faulty in some way. While I have no money this laptop's going back in the attic but on the bright side my other laptop no longer uses the S-Video with the TV so we're back to colour and higher resolution! :-)

---

### Post by sideaway on 2009-08-26
have you tried setting up an ssh server on it (simple command of sudo apt-get install openssh-server then installing VNC and setting it up that way? That was you can get a monitor on it with only a working network connection, this will allow you to setup a more permanent solution.

---

