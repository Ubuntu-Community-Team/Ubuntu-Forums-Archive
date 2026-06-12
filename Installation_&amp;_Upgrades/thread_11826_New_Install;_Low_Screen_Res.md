---
title: "New Install; Low Screen Res"
date: 2005-01-19
forum: Installation &amp; Upgrades
---

### Post by DeathByDisco on 2005-01-19
Hello All...

Being relatively new to Linux, I must first say that Ubuntu has been awesome...
The forums and Ubuntuguide have been indispensable resources and there seems to be an authentic (and positive) support community for this OS...  but I digress...

**Problem**
I have just reinstalled Ubuntu, but...  
-login screen and desktop seem to extend beyond the monitor which scrolls to reach the top and bottom panel
-misc. horizontal pixel trash throughout interface 
-screen resolution only shows options for 720x480 or 640x480 at 85Hz 

**Hardware**
PII 400
192Mb RAM
Trident Providia 9685
Soundblaster 16

My previous install on this system did not have this issue and was able to hold a screen res of 1024x768...
Is there any reason that Ubuntu would not have loaded the correct driver for this particular install???
I was using a different monitor during this install... would that matter???
Is this explanation clear???

Thanks in Advance,
DBD

---

### Post by shmonkey on 2005-01-19
Try running

```
# /usr/X11R6/bin/XF86Config
```

to reconfigre X

or manually edit /etc/X11/XF86Config-4 to include the modes you want.

---

### Post by Compwiz on 2005-01-21
[QUOTE=shmonkey]Try running

```
# /usr/X11R6/bin/XF86Config
```

to reconfigre X

or manually edit /etc/X11/XF86Config-4 to include the modes you want.[/QUOTE]

does this work with AMD64 version ... im newto Ubuntu...the resolution that was set at install is not allowing the GUI to run ... will this solution help me too? it seems to not help at all.  will tryasking for help in AMD 64 section

---

### Post by Lachlan on 2005-01-23
Open up a root terminal and try running xf86cfg.Select configure monitor,change the horizontal and vertical frequencies to your monitors specs.
Quit and save,log out or reboot,select screen resolution and hopefully you will have more options to play with.

Lachlan

---

### Post by DeathByDisco on 2005-01-26
Max props to shmonkey...

Apologies for the delay in my reply...

DBD

---

### Post by Fugee on 2005-06-07
I have the same vid card, but I couldn't find XF86Config anywhere on my system. My problems are:

-misc. horizontal pixel trash throughout interface
-screen resolution only shows options for 640x480 at 85Hz 

I tried editing my xorg file to add the proper HorizSync and VertRefresh for my monitor, but to no avail.

 ](*,) 

I'm using Hoary 5.04

*edit - I just realized that I post on the wrong forums... my bad...

---

### Post by duffmckagan on 2005-06-07
I had the resolution problem.

Whenever I change the resolution (I did it only once) the same scrolling thing happened to me.

I haven't changed anything on my Desktop.

The default Ubuntu wallpaper is quite annoying when it looks like the one in the file that I have attached.

Why is it so?
Personally, I think it is because of a low-bit color depth.
The maximum supported by my Video Card is 32bit, and I never got this problem in KDE. It always seems to be a problem in GNOME.
What may be wrong?

---

### Post by mingus on 2005-06-07
This can happen if the video card is not being read properly.  The monitor resolution will not be permitted to be set higher than the value read (or it could fry).

When you first boot, is the framebuffer driver displaying the proper resolution?  I noticed that there is a trident framebuffer on the system.  I'm rusty with this, but I seem to recall that the kernel passes what this driver reads on to the server. You might try adding the kernel argument at boot:
video=tridentfb vga=0x317
which is 1024x768x24

---

### Post by mingus on 2005-06-07
here is some poop on that driver . . . may tell you if it applies to your particular card/chipset

[http://sourceforge.net/projects/tridentfb](http://sourceforge.net/projects/tridentfb)

---

### Post by duffmckagan on 2005-06-07
[QUOTE=mingus] You might try adding the kernel argument at boot:
video=tridentfb vga=0x317
which is 1024x768x24[/QUOTE]

Howz that done?



Moreover, in windows, I can see fairly fine images, with 32 bit 
My monitor doesn't support more than 60Hz.
But I have made it to work at 85Hz. At this rate comes the screen scrolling problem.

Moreover, with KDE, this is not a problem.
Only GNOME is troublesome.

---

### Post by mingus on 2005-06-07
First, let's be sure we don't confuse resolution with refresh rate.  There is of course a relationship, which is why too high a color depth will (should) force down the refresh rate, otherwise the display can fry.  So the resolution setting can dictate the refresh setting on the display.  However, the resolution is strictly a function of the video card.

So . . .

At the boot menu, highlight the default boot entry, then press the 'e' key.  You will be taken to a second screen highlighting each line of that boot section.  Highlight the one that says "kernel", press 'e' and you can then add to that line (these are called "arguments").  Add "video=tridentfb vga=0x317" and see what happens.

Re your other comments:
Running the monitor at 85hz when your monitor doesn't support it is a recipe for fried eggs.  Probably why you got the flickering.  If this was a tft laptop, it'd be toast.

Re 32 bit:
That's the same as 24.  The extra 8 bits are a reserved space, blah blah you don't wanna know this programming stuff, do ya?  Same as 24.

Windows is in general better at hardware detection than linux, although of course all that matters to the user is what is in his own box, so that's kinda academic.  Windows "hal" (hardware abstraction layer) is fed by all the hardware vendors with drivers written for the OS.  MS doesn't have to do anything but plug them in.  Linux has come a real long way with this of recent, but there are still devices with drivers that have to be added after the fact, just for that matter as there still are with Windows (ATI anyone?).  You're doing that kinda of tweaking here.

Hope this helps.  Welcome.

---

### Post by duffmckagan on 2005-06-08
Thanks for the reply.

> That's the same as 24. The extra 8 bits are a reserved space, blah blah you don't wanna know this programming stuff, do ya? Same as 24.
Why not, I would like to understand everything that comes in my way.
I am learning Unix Shell Programming.



> At the boot menu, highlight the default boot entry, then press the 'e' key. You will be taken to a second screen highlighting each line of that boot section. Highlight the one that says "kernel", press 'e' and you can then add to that line (these are called "arguments"). Add "video=tridentfb vga=0x317" and see what happens.
Do I have to edit grub?



> Running the monitor at 85hz when your monitor doesn't support it is a recipe for fried eggs. Probably why you got the flickering. If this was a tft laptop, it'd be toast.
No. It is not a Laptop, so not a LCD TFT. It is just a CRT. And yes, I got no frying etc.

---

### Post by duffmckagan on 2005-06-08
> here is some poop on that driver . . . may tell you if it applies to your particular card/chipset

[http://sourceforge.net/projects/tridentfb](http://sourceforge.net/projects/tridentfb) 

What should I download here?

I downloaded "tridentfb" and "tridentfb patch".

---

### Post by mingus on 2005-06-08
Tridentfb is already on your system.  The one at sourceforge is a kernel source - use the binary you already have.  Old programming rule:  Never patch unless you know  what it is and that you need it.

Editing grub:  Only if this works.  There are other tweaks sometimes needed in the argument (e.g., on a system I have with an ATI card, I have to add :nomtrr because to make memory addressing work properly).  So use the command interactively at the grub boot menu first.  Note also that menu.lst is built on this system the Debian way; there is a section to add arguments (# kopt=), and then you do $sudo update-grub to regen the file.

If you really wanna know about those 8 bits, google it.  There is an in-depth X technology guide out there that explains it.

---

### Post by duffmckagan on 2005-06-08
What do I have to do with that downloaded file?

I did not get the reason for downloading that.

My video card is a S3 Graphics PRO Savage DDR with 32 MB of shared Video Memory.

Moreover, the Monitor is a LG Electronics CRT E700S Flatron

---

### Post by mingus on 2005-06-08
duggmckagan -

damn!  sorry, but I was responding to the original problem in this thread, which was with a Trident card.   Looking down in the thread to your post, not the same issue and not sure what your problem is.

it might be better to start a new thread and elaborate on the problem.

---

### Post by duffmckagan on 2005-06-08
[QUOTE=mingus]duggmckagan -

damn!  sorry, but I was responding to the original problem in this thread, which was with a Trident card.   Looking down in the thread to your post, not the same issue and not sure what your problem is.

it might be better to start a new thread and elaborate on the problem.[/QUOTE]

Oh.... :???: 

Ok, Here I go.

---

### Post by Fugee on 2005-06-08
I was finally able to get my resolutions to show correctly when I changed my DefaultDepth to 16 instead of 24.

---

### Post by duffmckagan on 2005-06-08
[QUOTE=Fugee]I was finally able to get my resolutions to show correctly when I changed my DefaultDepth to 16 instead of 24.[/QUOTE]
 How was that done?

---

### Post by andlinux21 on 2005-06-08
[FONT=Comic Sans MS][SIZE=3][COLOR=Blue]you can change it in the X11 config file just change it from 24 to 16 it worked for me also. :) [/COLOR][/SIZE][/FONT]

---

### Post by Fugee on 2005-06-08
[QUOTE=duffmckagan]How was that done?[/QUOTE]
sudo gedit /etc/X11/xorg.conf

Under Section "Screen" change the DefaultDepth to 16.

---

