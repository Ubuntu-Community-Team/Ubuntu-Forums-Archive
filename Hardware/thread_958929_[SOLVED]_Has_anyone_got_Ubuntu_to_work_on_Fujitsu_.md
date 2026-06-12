---
title: "[SOLVED] Has anyone got Ubuntu to work on Fujitsu T5010?"
date: 2008-10-25
forum: Hardware
---

### Post by Fc1032 on 2008-10-25
Hello all,

I am likely to buy the Fujitsu T5010 in a few weeks time. I just started using Ubuntu at home on the desktops, and everything has worked fine.

However, I do not know if ubuntu is the same on laptops, let alone tablets. So my main question is : '**has anyone got Ubuntu to work on the Fujitsu T5010 tablet, so it is fully functional like it would be on windows? (including working digitizer, screen rotation, sound, wireless etc etc)**


I really do prefer Ubuntu over windows but I don't know how I would configure things... Any help, links or tutorials would be greatly appreciated!



Many Thanks!
P.S I am really nooby at configuring files and stuff. So very simple terms need to be used :)

P.S.S 4 Days to Ubuntu 8.10!!!

---

### Post by werries on 2008-10-25
Maybe give us a link with specs? :)

---

### Post by Fc1032 on 2008-10-26
Hello!

Here is a link to the Australian website>>>
[http://www.fujitsu.com/au/services/technology/pc/notebooks/tseries/t5010/]("http://www.fujitsu.com/au/services/technology/pc/notebooks/tseries/t5010/")

Thanks!

---

### Post by Fc1032 on 2008-10-27
Bump :-\"

---

### Post by werries on 2008-10-28
Everything looks fine.
I looked into sound, wireless, graphics, and bluetooth.
Sound should work fine. Bluetooth should work fine.
Wireless is going to take some work but there appears to be a fix. Check out [http://ubuntuforums.org/showthread.php?t=903240](http://ubuntuforums.org/showthread.php?t=903240), and read it. (i didnt read through to see what you actually have to do though.)
Graphics work perfectly fine in hardy but there appears to be a slowdown bug in Intrepid.

As for digitizer and screen rotation, I have no idea. But I know the graphics card has problems outputting to an external screen with linux.

In conclusion, its not going to be perfect, but you can get most if not all functionality for it, and I'm sure the graphics in Intrepid will be fixed soon enough.

edit: it appears that ibex fixes the wireless! :)

---

### Post by Fc1032 on 2008-10-28
Thanks werries,

Well if the basic all work fine, its enough, I'll just have to look into the digitizer and screen later on. How did you find this out though??

It doesn't mean I've given up ppl, I am still open to any links or tutorials about the screen and digitizer!:)


Again, thanks in advance!

---

### Post by werries on 2008-11-12
I just searched your hardware, with linux at the end of it, and looked through stuff to see if had any chance of working. and it has good stuff.
and i really dont know what you mean by digitizer.

---

### Post by rarara77 on 2009-05-19
I am typing this on my T5010 running 64 bit Ubuntu right now!!

Wacom pen digitizer, wireless, screen resolution, power management, suspend, hibernate, bluetooth, keyboard, webcam, mouse, sound - work right away, I was so happy!


Things that do not work:
+buttons on the screen (there is a driver for, but it did not successfully compile for me)

+get the screen to rotate correctly AND the pen input to rotate with it.
What happens: I rotate the screen 90 degrees and the pen input remains in landscape laptop mode :(

+scroll sensor on the screen, which was somewhat annoying because it was easy to bump accidentally anyways.

If I could fix the rotation pen problems and buttons I would be in Linux tablet heaven! :)

---

### Post by bhishan on 2009-05-19
Check this out:

[http://www.linlap.com/wiki/fujitsu+lifebook+t5010](http://www.linlap.com/wiki/fujitsu+lifebook+t5010)

---

### Post by rarara77 on 2009-05-19
Yeah I've seen that page. Thanks

I tired installing the fjbtndrv drivers for the buttons from ([http://sourceforge.net/projects/fjbtndrv/](http://sourceforge.net/projects/fjbtndrv/)) ./configure is fine but then it reports "makefile not found" and I don't know what to do then... :(

---

### Post by Favux on 2009-05-20
Hi rarara77,

We should be able to get rotation to work.  The problem may be with the names HAL is returning.  Check:
```
xsetwacom
```
it should not be blank.  It should show your wacom devices like stylus and eraser, etc.  To see the names HAL is returning in a terminal type:
```
xinput --list
```
It should be stylus, eraser etc. again.  If not then wacomcpl and xsetwacom commands (rotation) won't work.  See Jaunty Users near the top here:  [http://ubuntuforums.org/showthread.php?t=996830](http://ubuntuforums.org/showthread.php?t=996830)
And for some rotation scripts see:  [http://ubuntuforums.org/showthread.php?t=996830](http://ubuntuforums.org/showthread.php?t=996830)

I hope this is helpful.

---

### Post by rarara77 on 2009-05-20
YES!! :D
xinput --list did display a list:  pen,ereaser,touchpad,etc.
I then installed wacomrotate from: [http://ppa.launchpad.net/thjaeger/ubuntu/pool/main/w/wacomrotate/](http://ppa.launchpad.net/thjaeger/ubuntu/pool/main/w/wacomrotate/)
and the pen input rotates when I rotate the screen!!   Thank you SO much Favux this is awesome!!!!!!!!!!!!!!!!!!!!!! :D

Uhh any idea on the buttons?
Right now I just created a drawer with custom application launchers in it for Normal, reverse, and left and right tablet modes.

Can I do unlocking while in tablet mode??
Possibly with finger print reader?
Because right now when I want to login or unlock my computer I have to flip it and when it's in the case that's very annoying.

---

### Post by Favux on 2009-05-20
Hi rarara77,

Great!

I've seen several people have problems installing the fjbtndrv drivers.  Not sure what's going wrong.  Did you:
```
sudo apt-get install build-essential
```
when you compiled?

I've seen people who seem to have that working.  Someone posted using Onboard in the last few weeks.  The HP TC1100 folks use CellWriter.  Search this thread:  [http://ubuntuforums.org/showthread.php?t=563736](http://ubuntuforums.org/showthread.php?t=563736)

---

### Post by rarara77 on 2009-05-20
"build-essential is already the newest version."

however when i run ./configure the end of it gives the following error:

```
checking for XRANDR... configure: error: Package requirements (x11 xrandr) were not met:

No package 'x11' found
No package 'xrandr' found

Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

Alternatively, you may set the environment variables XRANDR_CFLAGS
and XRANDR_LIBS to avoid the need to call pkg-config.
See the pkg-config man page for more details.

```

whaa? :confused:

For the onscreen keyboard, I ment to login and unlock my computer from screensaver with. I have CellWriter and it's AMAZING but only works once I am logged in.

---

### Post by Favux on 2009-05-20
Hi rarara77,

At a guess it's saying won't build against Xserver 1.6?  Which is the new version with Jaunty.

Sorry, I'm not going to be able to help with that.  Don't they have CellWriter set up to log into their tablets on boot?  Doesn't work for screensaver?  I think the Onboard poster was using a Motion tablet.  So maybe he has it figured out.

---

### Post by rarara77 on 2009-05-20
Got the fjbtndrv drivers working myself!! :D

Here is what I did:
I downloaded and installed the fjbtndrv drivers from this page: [https://launchpad.net/~khnz/+archive/ppa/+sourcepub/529485/+listing-archive-extra](https://launchpad.net/~khnz/+archive/ppa/+sourcepub/529485/+listing-archive-extra)
I used the 64 bit drivers because I am running 64 bit.

Installed fine but still not working.  I then added the following lines to my xorg configuration file (always make sure you backup your xorg configuration file to another directory before editing it, for anyone attempting this!!)

```
Section "InputDevice" 
Identifier "FSC Tablet Buttons" 
Driver "evdev" 
Option "Phys" "fsc/input0" 
Option "SendCoreEvents" "true" 
EndSection 
```

reboot and my buttons now work!!

---

### Post by Favux on 2009-05-20
Hi rarara77,

Outstanding!  Nice work.  I'll send other folks to your solution.

I found the Motion post, it's here:  [http://ubuntuforums.org/showthread.php?t=1154085&highlight=motion+computing](http://ubuntuforums.org/showthread.php?t=1154085&highlight=motion+computing)

---

### Post by rarara77 on 2009-05-22
Why is it that every time I log-off or shut down my pen buttons are reset to defaults? I like to have the main pointer set to left mouse button, next one to right click, then the 3rd button to F9 for window switcher, and eraser as eraser.

How can I get it to keep my button preferences even when I logout?

Still any ideas on getting an on screen keyboard on the unlock dialogue after suspend & hibernate?  Right now I try to keep it out of suspend and hibernate because to unlock it I have to take it out of case somewhat and flip it around.

---

### Post by Favux on 2009-05-22
Hi rarara77,

Usually the stylus buttons are set by wacomcpl and to keep them through a boot you have to enable the file it generates .xinitrc in Startup Applications.  Please see section 3 here:  [http://ubuntuforums.org/showthread.php?t=1038949](http://ubuntuforums.org/showthread.php?t=1038949)

---

### Post by victorhooi on 2009-06-10
heya,

rarara77: Glad to hear you got your rotation working.

I've got a Fujitsu tablet-pc as well, the T4215, and I'm struggling to get the pen-input and rotation to work...lol. Favux and some others tried to help with the pen, to little avail (yet), but I'm going to at least try to get the rotation working.

I'm also trying to install the fjbtndrv package, but in my case, I added the repository mentioned at [https://launchpad.net/~khnz/+archive/ppa](https://launchpad.net/~khnz/+archive/ppa) to my sources.list

However, upon trying to apt-get install "fjbtndrv" (which automatically pulls in "fsc " as a dependency, I get an error when it tries to install fsc-btns-kernel-source.

At the command line, I get:
```
Unpacking fjbtndrv (from .../fjbtndrv_2.0-4_amd64.deb) ...                                 
Processing triggers for hal ...                                                            
Regenerating hal fdi cache ...                                                             
 * Restarting Hardware abstraction layer hald                                             [ OK ] 
Setting up fsc-btns-kernel-source (2.0-4) ...                                                    

Creating symlink /var/lib/dkms/fsc_btns/2.0/source ->
                 /usr/src/fsc_btns-2.0               

DKMS: add Completed.

Kernel preparation unnecessary for this kernel.  Skipping...

Building module:
cleaning build area....
make KERNELRELEASE=2.6.30-8-generic....(bad exit status: 2)

Error! Bad return status for module build on kernel: 2.6.30-8-generic (x86_64)
Consult the make.log in the build directory
/var/lib/dkms/fsc_btns/2.0/build/ for more information.
0
0
dpkg: error processing fsc-btns-kernel-source (--configure):
 subprocess post-installation script returned error exit status 10
dpkg: dependency problems prevent configuration of fjbtndrv:
 fjbtndrv depends on fsc-btns-kernel-source; however:
  Package fsc-btns-kernel-source is not configured yet.
dpkg: error processing fjbtndrv (--configure):
 dependency problems - leaving unconfigured
No apport report written because the error message indicates its a followup error from a previous failure.
         Errors were encountered while processing:
 fsc-btns-kernel-source
 fjbtndrv
E: Sub-process /usr/bin/dpkg returned an error code (1)
victorhooi@ubuntu:~/Desktop/fjbtndrv-2.0.1$
```

And in the make.log file, I get:
```
Unpacking fjbtndrv (from .../fjbtndrv_2.0-4_amd64.deb) ...                                 
Processing triggers for hal ...                                                            
Regenerating hal fdi cache ...                                                             
 * Restarting Hardware abstraction layer hald                                             [ OK ] 
Setting up fsc-btns-kernel-source (2.0-4) ...                                                    

Creating symlink /var/lib/dkms/fsc_btns/2.0/source ->
                 /usr/src/fsc_btns-2.0               

DKMS: add Completed.

Kernel preparation unnecessary for this kernel.  Skipping...

Building module:
cleaning build area....
make KERNELRELEASE=2.6.30-8-generic....(bad exit status: 2)

Error! Bad return status for module build on kernel: 2.6.30-8-generic (x86_64)
Consult the make.log in the build directory
/var/lib/dkms/fsc_btns/2.0/build/ for more information.
0
0
dpkg: error processing fsc-btns-kernel-source (--configure):
 subprocess post-installation script returned error exit status 10
dpkg: dependency problems prevent configuration of fjbtndrv:
 fjbtndrv depends on fsc-btns-kernel-source; however:
  Package fsc-btns-kernel-source is not configured yet.
dpkg: error processing fjbtndrv (--configure):
 dependency problems - leaving unconfigured
No apport report written because the error message indicates its a followup error from a previous failure.
         Errors were encountered while processing:
 fsc-btns-kernel-source
 fjbtndrv
E: Sub-process /usr/bin/dpkg returned an error code (1)
victorhooi@ubuntu:~/Desktop/fjbtndrv-2.0.1$
```

I do notice that in the changelog for 2.0.1, it says:

```
Changes: fix for Linux 2.6.29, thanks to baerschen 
```

not sure if that's related to this?

Trying to compile it from the source tar.gz gives me the same XRANDR/pkgconfig error mentioned above.
```
checking for XRANDR... configure: error: in `/home/victorhooi/Desktop/fjbtndrv-2.0.1':
configure: error: The pkg-config script could not be found or is too old.  Make sure it
is in your PATH or set the PKG_CONFIG environment variable to the full
path to pkg-config.

Alternatively, you may set the environment variables XRANDR_CFLAGS
and XRANDR_LIBS to avoid the need to call pkg-config.
See the pkg-config man page for more details.

To get pkg-config, see <http://pkg-config.freedesktop.org/>.
See `config.log' for more details.
```

Cheers,
Victor

---

### Post by rarara77 on 2009-06-10
hey victorhooi, sorry to hear your having trouble.

compiling from source did not work for me ether, I would suggest trying to install fjbtndrv from the deb package for your architecture from this page: [https://launchpad.net/~khnz/+archive/ppa/+sourcepub/529485/+listing-archive-extra](https://launchpad.net/~khnz/+archive/ppa/+sourcepub/529485/+listing-archive-extra).
The 64 bit edition installed suscessfully for me on Ubuntu 9.04. 

Also, about the pen, what verison of Ubuntu are you using? 9.04 supports most Wacom tablets out of the box.
Hope that helps!

---

### Post by victorhooi on 2009-06-10
heya,

Yeah, I am basically installing from there (I added Robert's PPA to my sources.list)

However, when you try to install the fjbtndrv package, it will pull in and try to install the fsc-buttons-kernel-source package, which is where I encountered the problems before (see output in post #20 on page 2 of here).

I'm currently running Karmic 9.10. I did hope it worked out of the box, but no such luck...lol...the eraser end intermittenly works, but never the pen end, and currently eraser end not working. I put some details up here:

[http://ubuntuforums.org/showthread.php?t=1136848&page=5&highlight=t4215](http://ubuntuforums.org/showthread.php?t=1136848&page=5&highlight=t4215)

perhaps you might have comments, based on having a Fujitsu tablet?

Cheers,
Victor

---

### Post by marc1uk on 2009-11-14
Did anyone here ever get the scrollbar on the screen edge working? I've got a T1010, and that's one of the last things remaining to get working. Personally I find it really helpful, so i'd be sorry to see it stay useless.

---

### Post by draco31.fr on 2010-01-10
I've got a T1010 too, and the scroll bar at the bottom of the screen did not work at all.
I can't find the input device associated with the scoll sensor, so I think it is an udev problem.

---

### Post by ozkhalsa on 2010-05-26
has anybody got lucid lynx now working on t5010. i have yet not upgraded from karmic as removal of hal and earlier packages may couse pen inout to not work in lucid? need advise from more experianced user.

---

### Post by Favux on 2010-05-26
Hi ozkhalsa,

I think at this point you can maybe get it working.  You may need to compile some things.

I'd sure keep Karmic and install Lucid in a separate partition if at all possible.  That way you have at least one working linux partition.

---

### Post by ProgressionMurph on 2010-07-15
I am using 64 bit 10.04 installation and everything works except for the scroll sensor, fingerprint read and currently my cursor doesn't rotate when I rotate my screen.

---

### Post by Favux on 2010-07-15
Hi ProgressionMurph,

I think there is a Lucid/Xserver 1.7 aware fjbtndrv (which supplies rotation for Fujitsu) v. 2.1.2 dated 2-17-10.  You can download and compile the source at:  [https://sourceforge.net/projects/fjbtndrv/](https://sourceforge.net/projects/fjbtndrv/)

You may be able to use a ppa which has a deb of it, which might be easier.  It worked for Karmic anyway.  At a guess I think you'd do something like the following.  Add to Software Sources:
```
deb http://ppa.launchpad.net/khnz/ppa/ubuntu lucid main

deb-src http://ppa.launchpad.net/khnz/ppa/ubuntu lucid main
```
Enter in a terminal the key:
```
sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys E88D7B6F

```
Then:
```
sudo apt-get update

sudo apt-get install fjbtndrv
```
There should be a description of how to get the PPA working on the sourceforge site but I don't see it, I just saw:  [https://sourceforge.net/apps/mediawiki/fjbtndrv/index.php?title=Main_Page](https://sourceforge.net/apps/mediawiki/fjbtndrv/index.php?title=Main_Page)

---

