---
title: "[SOLVED] Graphial Boot Problem (x will not load)"
date: 2009-01-05
forum: Installation &amp; Upgrades
---

### Post by sc_dan2002 on 2009-01-05
Hello,

Having trouble booting into ubuntu 7.10.  When I attempt an graphical boot (with gnome) I get a solid black screen, with which the only interaction I have with is ctrl+alt+del to reboot.

I am assuming that this is a video card problem, and have been looking on google for quite awhile now attempting to fix.  I am using Dual NVIDIA® GeForce® Go 9800M GTX 1GB GDDR3 video cards, and here is what I have tried thus far (all in recovery mode):

1) edit nvidia driver in xorg.conf to 'nv' 'nvidia' and 'vessa' respectively (none of the three corrected problem)

2) ran dpkg-reconfigure xserver-xorg and configured to 'nv' and then 'vessa' (I know it is redundant but I figured i'd try) neither of which worked.

Now am at a loss, does anyone know of a driver that I can load, to at least get gnome up and running?

Thanks!
|}

---

### Post by Bucky Ball on 2009-01-05
'vesa' with one 's'.

If you can't boot, you could always try dropping to a shell by holding down ctl/alt/f1, then:

```
startx
```

---

### Post by sc_dan2002 on 2009-01-05
No go, startx simply gives me the solid black screen again.

---

### Post by rjmoerland on 2009-01-05
I had a similar problem on my laptop, though there it was a completely garbled screen instead of a black screen while booting. Turned out that if I switched off the splash screen while booting, everything would be allright and I could see the login screen.

To try this, press the escape button when you have the chance (GRUB will tell you just after powering up the machine to press ESC to go to the menu). After pressing escape, you'll see a list of options. Select the topmost one. Press 'e'. You'll see a new screen something like

```

title		Ubuntu 8.10, kernel 2.6.27-9-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.27-9-generic root=UUID=0be270a0-14a2-49d0-ad75-8db20bca2efa ro splash 
initrd		/boot/initrd.img-2.6.27-9-generic

```

Go to the line that says 'kernel ...' and press 'e' again. You can now edit the this line of text. Go to the end of the line and there will be something like 'quiet splash'. Remove 'splash'. Press enter, then 'b'. You will now boot into your Linux installation, without a splash screen. To see what is going on you can also remove 'quiet'. See if you can see a login screen now.

HTH
Robert

---

### Post by rjmoerland on 2009-01-05
Additionally, you might check that your monitor is capable of the resolution that X selects for you?

---

### Post by sc_dan2002 on 2009-01-05
Tried removing splash, computer is rebooting will try removing quiet.  Still getting black screen.

I have resolution set to 1920 x 1200 which is exactly what my monitor on that laptop is rated at.

---

### Post by rjmoerland on 2009-01-05
> **sc_dan2002 said:**
> Tried removing splash, computer is rebooting will try removing quiet.  Still getting black screen.

I have resolution set to 1920 x 1200 which is exactly what my monitor on that laptop is rated at.

Including the set refresh rate? I'm also a bit in the dark here (no pun intended). 

You might give the 'vga' and 'fbdev' drivers a go?

---

### Post by sc_dan2002 on 2009-01-05
Well I'm not completly in the dark, the back light stays on (har har)

Anyway... I'll try those drivers.

---

### Post by aikiwolfie on 2009-01-05
The problem is X doesn't assign a default display adapter. So you get a blank screen. Here's how to fix it.

> **damien_vancouver said:**
> [CENTER][U]HOW TO GET THE NVIDIA DRIVER WORKING FOR NVIDIA SLI DUAL VIDEO CARDS UBUNTU INTREPID 8.10
HOW TO FIX BROKEN X WINDOWS TEXT ONLY NO GRAPHICAL DESKTOP AFTER INSTALLING THE NVIDIA DRIVER
[/U][/CENTER]

This problem should affect anyone with a SLI setup with 2 or 3 nvidia video cards, the first time you reboot after installing the nvidia restricted driver (which will happen if you turn on desktop effects on a newly installed Ubuntu / SLI system).  X Windows will fail to start saying "No Screen Found" and you will be stuck at a text login prompt!  Doh!!!!


**_Fast fix instructions for the experienced:_** 

[LIST=1]
[*]The BusId fix described in this thread has to go into the "Device" section in /etc/X11/xorg.conf, not into the "Screens" section.

[*]Use **lspci | grep -i vga** to find your cards BusIDs.  They will be something like 01:00.0 or 02:00.0.  These would translate to BusId "01:00:00" or BusId "02:00:0" in the xorg.conf.

[*]Edit /etc/X11/xorg.conf with sudo, find *Section "Device"* and try one or the other BusId line.

[*]Test X windows with **startx**.  Use **ctrl-alt-backspace** to get out of X windows.  Try the other BusID line if the first one doesn't work.

[*]Once you have it working, Restart gdm with **sudo /etc/init.d/gdm restart.  Rejoice.**
[/LIST]


**_Very Gentle instructions for beginners:_**

You will be starting from a broken system that only boots into text mode, and it will be prompting you for a username.  Type the commands shown in boldface.  Everything else is just a copy of what happened on my system so you know what else you will be seeing.

1. Login with your username/password you usually login with.  If you don't have a password set, just hit enter.

```
Ubuntu 8.10 yourmachine tty1

yourmachine login: **yourusername**
Password: **mypassword**

```

2. Remove any old possibly broken install of v173 or v177 nvidia drivers...

```
$ **sudo apt-get purge nvidia-glx-173 nvidia-glx-177**
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package nvidia-glx-173 is not installed, so not removed
The following packages will be REMOVED:
  nvidia-glx-177*
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
After this operation, 25.8MB disk space will be freed.
Do you want to continue [Y/n]? **[Enter]**
(Reading database ... 111389 files and directories currently installed.)
Removing nvidia-glx-177 ...
Purging configuration files for nvidia-glx-177 ...
dpkg - warning: while removing nvidia-glx-177, directory `/usr/lib/tls' not empty so not removed.
Processing triggers for man-db ...
Processing triggers for libc6 ...
ldconfig deferred processing now taking place
```

3. Reinstall the v177 nvidia driver

```
$ **sudo apt-get install nvidia-glx-177**
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following NEW packages will be installed:
  nvidia-glx-177
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B/8931kB of archives.
After this operation, 25.8MB of additional disk space will be used.
Selecting previously deselected package nvidia-glx-177.
(Reading database ... 111345 files and directories currently installed.)
Unpacking nvidia-glx-177 (from .../nvidia-glx-177_177.80-0ubuntu2_i386.deb) ...
Processing triggers for man-db ...
Setting up nvidia-glx-177 (177.80-0ubuntu2) ...

Processing triggers for libc6 ...
ldconfig deferred processing now taking place
```


4. Let nvidia-xconfig make you a new /etc/X11/xorg.conf file:
```
$ **sudo nvidia-xconfig**

Using X configuration file: "/etc/X11/xorg.conf".
Backed up file '/etc/X11/xorg.conf' as '/etc/X11/xorg.conf.backup'
New X configuration file written to '/etc/X11/xorg.conf'

```

5. List the video card busID's with lspci:
```
$ **lspci | grep -i vga**
***03:00.0*** VGA compatible controller: nVidia Corporation G80 [GeForce 8800 GTS] (rev a2)
***04:00.0 ***VGA compatible controller: nVidia Corporation G80 [GeForce 8800 GTS] (rev a2)

```

On my system, the cards are *03:00.0* and *04:00.0*.  These would go into xorg.conf as **BusId "03:00:00"** and **BusId "04:00:00"** respectively.  Your setup will probably show different numbers in the first field, and you might even have 3 video cards if you're using 3-way SLI.


Next you have to take a guess which card is which.  You have a 50/50 chance of getting it right... :)

Write down the two bus ID's on a piece of paper so you have them for the next step.

6. Edit /etc/X11/xorg.conf and add the BusId line to the Device section.  (use your favourite text editor instead of pico if you want)
```
$ ** sudo pico /etc/X11/xorg.conf **
```

Hit Ctrl-W and type:  **Section "Device"** to search for the right section.

Pico will find the Device section.  Mine looked like this:

```
Section "Device"
    Identifier     "Configured Video Device" 
    Driver         "nvidia"
EndSection
```


Add in the your first guess for the BusId line, so it looks like this:
```
Section "Device"
    Identifier     "Configured Video Device" 
    Driver         "nvidia"
    **BusId "04:00:00"**
EndSection
```


Now save the file with Ctrl-O and then exit pico with Ctrl-X.  You will be back at a $ command prompt.

7. See if X Windows starts using startx!
```
$ ** startx **
```

With any luck you see X-Windows startup!

If you see just a black screen or nothing happens, you go back to step 6 and edit xorg.conf, putting in the other possible BusId line..  Then re-try **startx** and it should work.  You can stop X windows now with **ctrl-alt-backspace** to get back to the prompt so you can repeat step 6.

The debugging output you see go by can be found in /var/log/Xorg.0.log, which you can look at with **less /var/log/Xorg.0.log**  (use space bar for next page, b for previous page, g for start of file, G for end of file, and q to quit).


Now it's time to stop the X windows we started with "startx" and try and start the gdm login manager:

8. Stop X-Windows if it's running.  Press: **Ctrl-Alt-Backspace** and X will die, leaving you back at the $ command prompt
 
9. repeat steps 6 and 7 again until you get the right BusId. 
Once you have a working configuration, restart gdm (the graphical login screen):
```

$ **sudo /etc/init.d/gdm start**

```

the usual Ubuntu login screen should start!

10. Graphical Linux is now back, rejoice!  

11. You should now be able to go into System -> preferences -> Appearance in Ubuntu and turn on the enhanced effects in the Visual Effects tab.   Try dragging windows around and shaking them.  Also try breaking them out to the left or right to switch them to a different desktop.  Try Windows-Tab instead of Alt-Tab to do fancy 3D window switching.  Cool!

Here's the original thread.
[http://ubuntuforums.org/showthread.php?t=966315&page=2](http://ubuntuforums.org/showthread.php?t=966315&page=2)

---

### Post by sc_dan2002 on 2009-01-05
Ok, neither of those drivers work either.  I still get solid black screen =(

More info:
If the command gdm or startx is given from recouvery mode, the sreen blinks black 3 times, and then goes solid black.  If the command gdm stop is given during the blinking screen phase, there is no change to the sequence.

laptop specs:  intel 9650, dual nvidia 9800m gtx, 8gb ram, 17" 1920 x 1200 WUXGA LCD Active Matrix Display, 64gb ssd foor booting.

Don't know if any of that will help.  Any suggestions would be appreciated!

---

### Post by sc_dan2002 on 2009-01-05
Thanks aikiwolfie, off and attempting now!

---

### Post by sc_dan2002 on 2009-01-05
Ok, now I feel like a complete moron.  All I needed to do was change the PCI id, sheesh

thanks a lot aikiwolfie!!!

^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
still having issues with GDM, but X is working via startx in recovery mode

---

### Post by rjmoerland on 2009-01-05
Congrats!

---

### Post by sc_dan2002 on 2009-01-05
Ok, this sucks.

startx works  
I can get into and work on the graphical system that way.

When I attempt to start gdm, the screen flashes, (it appears to be attempting to start gnome) and then goes back to prompt, with gdm in the background.

Normal boot simply hangs.

---

### Post by sc_dan2002 on 2009-01-05
OK, getting a little bit further now.

I have got GDM running (by configuring the horizontal and vertical sync rates via dpkg-reconfigure)

now, when GDM comes up (I get the login screen and everything) I log in, and an error comes up.
"Your session only lasted less than 10 seconds.  If you have not logged out yourself, this could mean that there is some installation problem or that you may be out of diskspace.  Try loggins in with on of the failsafe sessions to see if you can fix this problem."

In the "View Details (~/.xsession-errors file)" the following is displayed
process:5620): Gtk-WARNING **:  THis process is currently rnning setuid or setgid.
This is not a supported use of GTK+ Your must create a helper program instead.  For further details, see:  [http://www.gtk.org/setuid.html](http://www.gtk.org/setuid.html)
refusing to initialize GTK+

And this is reapeated a few times.


The above happens when conducting a normal boot, and when going into recovery mode and launching GDM.

Can anyone give any advice?

---

### Post by sc_dan2002 on 2009-01-06
Anyone?

---

### Post by sc_dan2002 on 2009-01-06
OK, got it now (at least its working right now).

Seems that there were multiple problems, listed below in order they were corrected:

The wrong driver was selected for my nvidia card from the begining, instead of the "nv" driver the "vesa" driver should have been used.

The video card busid was wrong, this laptop had dual video cards, and for some reason ubuntu would not recognize the first, and xorg.conf had to be modified to the second card.

The horizontal and vertical sync rates were set wrong for the monitor, had to be set with dpkg-reconfigure  (or it could be set by modifying xorg.conf if you are used to adding stuff to it, I'm not).

Ubuntu corrupted the user account upon install (or the multiple reboots while attempting to fix the first couple of problems) causing gdm to fail upon logon (but x was able to be run from recovery mode as root).

With all of that said, I simply created a new user, and now GDM works, whoopie!!!  (Now I can proceed to break this computer by playing with it har har)

thanks everyone for your help!

---

