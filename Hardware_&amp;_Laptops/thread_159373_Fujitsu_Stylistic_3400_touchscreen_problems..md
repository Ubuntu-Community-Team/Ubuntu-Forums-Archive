---
title: "Fujitsu Stylistic 3400 touchscreen problems."
date: 2006-04-12
forum: Hardware &amp; Laptops
---

### Post by odubtaig on 2006-04-12
Now, on the one hand I'm substantially impressed with Ubuntu (believe me, I didn't expect to be) seeing as it's the only distro worth looking at that actually found my PCMCIA CD-Rom drive.

On the other hand, after much poking around in config files and having got portrait mode working properly I still have one problem: when I press the stylus down and lift it up once Ubuntu sees it as just a press down. After this if I press down and release again it registers as a double click.

Now, this is a fairly old pre-Tablet PenPC with a passive stylus so I'm using the fpit driver for the stylus and I've set it all up properly so far as I can tell.

Now, the stylus has been tested with the original supplied edition of Win98 and works without issue so this is definitely a software problem.

Ah yes, also Option "Rotate" "CW" for the fpit driver didn't work properly, ended up much like a basic SwapXY.

In my xorg.conf file:
[indent][font=courier]Section "InputDevice"
[INDENT]Identifier "Touchscreen"
[INDENT]Driver "fpit"
Option "Device" "/dev/ttyS3"
Option "BaudRate" "9600"
Option "SwapXY"
Option "SwapX"
Option "MaximumXPosition" "4096"
Option "MaximumYPosition" "4096"
Option "MinimumXPosition" "0"
Option "MinimumYPosition" "0" [/INDENT][/INDENT]EndSection[/font][/indent]
...and in a script symlinked in /etc/init.d/rcS.d numbered before xorg-common:
[indent][font=courier]#!/bin/sh
/bin/setserial /dev/ttyS3 autoconfig
/bin/setserial /dev/ttyS3 uart 8250 irq 5 port 0xfd68 low_latency[/font][/indent]

I would give a bit more detail but I've just tried restarting with xubuntu Flight 6 and... erm... experimentation has its price. Needless to say I'll be more than happy to try again once I've restored Windows and linld.com :oops: 

So, if anyone's got any ideas I'd love to know... although I've just considered it might be an IRQ conflict issue. That takes me back I can tell ya.

---

### Post by dan_kent on 2006-04-29
i've been stugling to get my Stylistic 3400 touchscreen to work at all.
Is there any chance you can post a walkthorugh of how to do it?

Dan

---

### Post by bcw on 2006-08-26
I'm working through the set up steps for this computer, and I'll put them in the wiki when I've got it all lined up.

In the meantime, the 'fpit' driver used does not install by default - you have to add it.  It's 'xserver-xorg-input-fpit'.

---

### Post by bcw on 2006-08-27
> **odubtaig said:**
> 
On the other hand, after much poking around in config files and having got portrait mode working properly I still have one problem: when I press the stylus down and lift it up once Ubuntu sees it as just a press down. After this if I press down and release again it registers as a double click.

Now, this is a fairly old pre-Tablet PenPC with a passive stylus so I'm using the fpit driver for the stylus and I've set it all up properly so far as I can tell.

Now, the stylus has been tested with the original supplied edition of Win98 and works without issue so this is definitely a software problem.

Ah yes, also Option "Rotate" "CW" for the fpit driver didn't work properly, ended up much like a basic SwapXY.

In my xorg.conf file:
[indent][font=courier]Section "InputDevice"
[INDENT]Identifier "Touchscreen"
[INDENT]Driver "fpit"
Option "Device" "/dev/ttyS3"
Option "BaudRate" "9600"
Option "SwapXY"
Option "SwapX"
Option "MaximumXPosition" "4096"
Option "MaximumYPosition" "4096"
Option "MinimumXPosition" "0"
Option "MinimumYPosition" "0" [/INDENT][/INDENT]EndSection[/font][/indent]
...and in a script symlinked in /etc/init.d/rcS.d numbered before xorg-common:
[indent][font=courier]#!/bin/sh
/bin/setserial /dev/ttyS3 autoconfig
/bin/setserial /dev/ttyS3 uart 8250 irq 5 port 0xfd68 low_latency[/font][/indent]


I don't know if this is the problem, but the Fujitsu 3400/3500 needs:
```
Option     "Passive"
```

in the InputDevice Section.

Pardon me if you already know this, the standard way to get documentation in Unix/Linux is "man fpit" (in this case).  A newer, not-completely-implemented-but-worth-trying alternative is "info fpit".

The man page for fpit mentions the Stylistic 3400 specifically needing the "Passive" entry.  I'm writing this for the benefit of anyone else that reads this in the future, so they know they have a place to read all (or lots) about it.

HTH,
Bret

---

### Post by one_stinky_bum on 2006-09-01
Did you get this to work? I'm just interested in anyone who can get a FinePoint digitizer to work on Dapper. I have a Gateway M280 tablet with a finepoint MP-800 digitizer and it's been a month since I tried to get this thing to work.

---

### Post by one_stinky_bum on 2006-09-20
bump :confused:

---

### Post by kelvinelk on 2006-09-25
I have successfully managed to get the touch-screen working on the 3400. When i get a chance I will post a full run-through.

---

### Post by one_stinky_bum on 2006-09-25
could you give a hint or two, so that I can start working on it? This is exciting - which drivers did you use - the ones from [www.conan.de](www.conan.de) or from linuxslate? I'm hoping the finepoint digitizer in the 3400 is the MP-800 that I have here in my gateway M280.

---

### Post by kelvinelk on 2006-09-25
the driver is the fpit driver. I have not tried the other drivers as i'm not sure they will work with my 3400. after much fiddling around i managed to get it working.

the man page for fpit was not correct for my fujitsu stylistic 3400.

a quick look at "dmesg" indicated that ttyS3 was already in use by another serial device. So for starters i needed to choose a different serial port - i chose ttyS2. i then created a script in /etc/init.d/fujitsuserial.sh (like on the man page but with the alternative serial port) did a "chmod +x fujitsuserial.sh" 

and then ran "update-rc.d fujitsuserial.sh defaults"
There must be a cleaner way but I haven't worked it out yet.

This created the (almost) correct symlinks in the /etc/rc$.d directories. I had to manually change the K90fujitsuserial entries to a number less than the entries for gdm K19 i think. Hope this helps as a start. Oh and /etc/X11/xorg.conf needs to match the serial entry in the script.

This got the pen working but was slightly misaligned.
Had to do a bit of fiddling with the xorg.conf fpit entry 
Option "MaximumXPosition" and Option "MaximumYPosition" to get it right.

Please note this only works with the 3400 OUT of the cradle.

Hope this gets you started

---

### Post by one_stinky_bum on 2006-09-26
Cool. I'm on a gateway M280, with the Finepoint MP-800 digitizer. I'll let you know if it works.

---

### Post by mindglow on 2006-11-10
Hi there,

I own a fujitsu stylistic 3500, and I can't get the pen to work. I know it did work in the past, but I redid my setup and I can't get it to work anymore. I used /dev/ttyS2, ttyS3 being used (by the wifi network card, I think) I used exactly the same setup you did, but I get the following message in Xorg.0.log : ProcXCloseDevice to close or not ?. Any idea ?

Thx !

> **kelvinelk said:**
> the driver is the fpit driver. I have not tried the other drivers as i'm not sure they will work with my 3400. after much fiddling around i managed to get it working.

the man page for fpit was not correct for my fujitsu stylistic 3400.

a quick look at "dmesg" indicated that ttyS3 was already in use by another serial device. So for starters i needed to choose a different serial port - i chose ttyS2. i then created a script in /etc/init.d/fujitsuserial.sh (like on the man page but with the alternative serial port) did a "chmod +x fujitsuserial.sh" 

and then ran "update-rc.d fujitsuserial.sh defaults"
There must be a cleaner way but I haven't worked it out yet.

This created the (almost) correct symlinks in the /etc/rc$.d directories. I had to manually change the K90fujitsuserial entries to a number less than the entries for gdm K19 i think. Hope this helps as a start. Oh and /etc/X11/xorg.conf needs to match the serial entry in the script.

This got the pen working but was slightly misaligned.
Had to do a bit of fiddling with the xorg.conf fpit entry 
Option "MaximumXPosition" and Option "MaximumYPosition" to get it right.

Please note this only works with the 3400 OUT of the cradle.

Hope this gets you started

---

### Post by rusty0101 on 2006-11-27
I did a install of ubunto 6.06, with xubuntu-desktop and am still having problems with getting fpit to function.

Specifically I have followed the instructions given above, though I had to change the rc$.d simlinks to 12, as gdm was at 13. At the moment Xorg.log is showing me a message "(EE) No Input driver matching 'fpit'"

Is there something that I need to apt-get to enable this feature? I had been under the impression that fpit was compiled into the xorg servers, or included with the core modules. It looks like either ubuntu compiled without it, or it is not in the xorg libraries that are available for 6.06 at this time.

When I do a 'apt-cache search fpit' nothing comes back, so it looks like it is not listed in the descriptions of any of the debs that are in the standard distribution files.

I have not added universe, multiverse or plf at this time, so if it is in one of those collections, that my be where I need to go.

Thanks for any help.

-Rusty

---

### Post by one_stinky_bum on 2006-11-27
The package is titled xserver-xorg-input-fpit and it is in Edgy's universe repository:

[http://packages.ubuntu.com/edgy/x11/xserver-xorg-input-fpit](http://packages.ubuntu.com/edgy/x11/xserver-xorg-input-fpit)

Hope this helps.

---

### Post by Dubstar_04 on 2006-12-11
Please help before I go insane!!

I've been trying to get the pen in for my Fujitsu stylistic 3400 on and off for over 6 weeks with no result!!

I've tried everything to get it to work Ive copied and pasted all the settings from this thread into the corresponding files and nothing.

So far:

I initially installed the fpit driver using the synaptic package manager and  stupidly assumed that it would work out the tin!! WRONG!

I followed all the instructions from the Fpit man site, nothing.

I have copied and pasted info from this post and still nothing. 

I have even tried to get the screen to rotate to get any result from the changes at all and still nothing!!

Its really wearing me down now and If I can't get it sorted Im gonna have to revert back to dare I say it windows!!

I am a noob and I am really struggling with this. I really want it to work as Ubuntu dapper is a faster than the tablet edition I was running.

Any help would be appriciate as Im at the end of my knowledge!!

Please be kind. as I am almost in tears as it is!!!

---

### Post by Dubstar_04 on 2006-12-11
Update,

I have now installed Xubuntu on my tablet thinking that there may be more suport of fpit in edgy!! Nope still not a sausage!!

Please could anyone who has had success with a fujitsu stylistic 3400 and the pen please help me??

I am new to linux and I must be doing something wrong as the best result I have had so far is a failed load with the screen saying 

/bin/setserial /dev/ttyS3 autoconfig
/bin/setserial /dev/ttyS3 uart 8250 irq 5 port 0xfd68 low_latency

Files cannot be found!!

Thats the only result i have had so its the best as yet. 

I'm not one for giving up but no one seems to understand these passive pen tablets and with them being old fewer people are interested in learning about them!!

If you think you could offer any relavant advise other than stick to windows please help!!

Thanks Dan

---

### Post by one_stinky_bum on 2006-12-11
Try the following:

[http://ubuntuforums.org/showpost.php?p=1704070&postcount=26](http://ubuntuforums.org/showpost.php?p=1704070&postcount=26)

---

### Post by Dubstar_04 on 2006-12-12
Thank you for replying. Once I get this pen working I can move on and experiment with Onscreen keyboards, and handwriting recognition, but until then all I have is a pain in the behind as I have to use the attached keyboard and mouse!!!

Has Anyone had good results with the Fujitsu stylistic 3400 and pen?? If so could you let me know, as all i have ever read is that it kind of works but 'still needs configuring'!

---

### Post by rusty0101 on 2006-12-12
Oh, getting better, but still some problems.

fpit is working with caveats to follow. I followed the instructions from above. Unless you launch a superuser shell, (sudo -s) to enter the commands above, remember to prepend those commands with sudo.

Once you have gotten edgy or dapper installed on your system from CD or DVD, confirm your network is working by doing a refresh and update in synaptic package manager.

Add the Universe respository.

Install the packages setserial and the package with fpit in it's name. (it's an xorg input package, which is in the universe repository. I also installed the xubuntu-desktop, as a result of the low memory abilities. Since I am building a system for my son, I would like a virtual keyboard to be available so I also installed the GOK package, though I may use one of the other virtual keyboards along the way, 

xvkbd has been suggested elsewhere. Getting it to run under gdm is pretty much the final step I expect to have before I hand the tablet over to my son. Once I have it set up so that he can login with the pen, I think it will be ready for him.

Before I get there though, I need to get the display sized properly. At the moment it seems to be stuck with a maximum resolution of 800x600, which leaves a really big black border around the screen. It's better than 640x480 perhaps, but pen alignment isn't right, etc.

I suspect that adding a modeline would solve the problem, though I am not having much luck in a search for one. Alternatively if someone has a recomendation, I would be happy to take a look. Possibly there is a tool that will set things up for me, but I am not seeing anything useful at the moment. (though that may just be my frustration at the moment.)

---

### Post by Dubstar_04 on 2006-12-12
Thank you for the advise I will try all these when I get in.

With reference to the black boarder I managed to get a fullscreen by using the 

Sudo dpkg-reconfigure xserver-xorg

and selecting the 'trident' as the screen driver this worked for me as 'vesa' was selected by default and gave the results that you described.

I hope this can help with your problem.

Is there any sort of wiki anywhere that I could read and maybe add to?

It seems that everyone with a tablet has the same configure problems!

Thanks again.

P.S. Let me know if the screen driver helps.

---

### Post by lfjewett on 2006-12-12
The original poster in this thread said his problem was when he pushed down and lifted up, the lift up was never recorded.  This is EXACTLY the same problem I have with my 3500.  It makes drawing, and typing on the On Screen Keyboard almost impossible.   Has anybody gotten their 3400/3500 touchscreen not only to work, but work "well"?  What are we missing that is preventing mouse "off" events from being recorded? 

PS: I'm using the Driver "ati" in my xorg.conf and it works good. I'm also at 800x600 but that is all my display can do.  There are 3 versions of the 3500, only one of them had a 1024x768 screen.  As for calibration, in the XandY variables for your fpit driver. try these numbers
4096, 4096, 50, 0  ( Xmax, Ymax, Xmin, Ymin ) Then adjust as necessary to calibrate. 

Thanks
Louis

---

### Post by Dubstar_04 on 2006-12-12
I've had enought now. Sudo won't work so I can't edit any files to configure anything and Xubuntu won't shut down.

Thanks for everyones help. I'm off back to windows where every thing works 'straight out the tin'!!

Maybe I will try ubuntu again where its a bit more mature.

Take care and farwell.

---

### Post by rusty0101 on 2006-12-12
Sorry, didn't specify. I did do a dpkg reconfigure and actually ended up worse than I started. I suspect that it is the refressh rate (horizontal or vertical) that is giving me problems at this time. Unfortunately I don't know what they 'should' be, and the generic settings are not helping.

---

### Post by rusty0101 on 2006-12-14
Found a solution that gives me full display usage, but perhaps not as much color depth as desireable. For some reason I can't get anything larger than 800x600 in 24 bit color. Dropping down to 16 bit color gives a full display for me. I don't think that the Trident video interface in the 3400 does shared memory, though I will check on that later on. If I am correct, then there just isn't enough video memory on the system I have to support 24bit 1024x786 resolution. 

Now tidying things up a bit (getting rid of the Gnome Desktop stuff using xubuntu-desktop, and working out how to get the keyboard on the signin screen. I seem to recall a thread somewhere about that using onboard which I see is installed, rather than gok. So have removed gok as well. (give my son more space to install apps as needed.)

I'll be happy to do a better writeup on how I got where I am if someone thinks that will help. I don't have long with this laptop, as I will be turning it over to my son as soon as I get the keyboard thing worked out. (well, see if I can toss some books off of the Baen Free Library for him as well...)

Thanks for the help that has been provided so far.

-Rusty

---

### Post by lfjewett on 2006-12-14
Did you resolve the issue of the touchscreen not recording mouse off events.  On mine ( and others it seems ) clicking a button on the on screen keyboard will 50% of the time yeild the key being stuck down and repeating forever?   This also crops up as an issue when painting on the screen?  If you've solved this issue, I love you!

---

### Post by rusty0101 on 2006-12-15
Honestly that was not an issue with my son's 3400 when I got fpit up and running. I am not perfectly happy witht he alignment yet, so I will be tweeking that, but one of the issues I actually have appears to be a hardware problem, as the upper right quarter of the display has intermitent response to any pointing activity. I.e. if I use the Gimp to draw, I will get occasionall recognition of pen presses in that quadrant, while the rest ofthe screen seems to wrok very wel. I think I will be replacing the chassi, and perhaps using this one as a display for a heads up system or something along the way. Who knows. 

-Rusty

---

### Post by goodbyegti on 2006-12-24
I'm also having a huge amount of trouble with the fpit driver.

After installing Breezy Badger on my LT P-600 (the newer distros wouldn't install using grub) and setting up the fpit driver everything was working great. I had right click and the calibration was good.

Now I install all available updates and whilst the cursor is still taking input from the screen it's gone crazy! The calibration is way off!!

So now i need to figure out which update did it and somehow get rid of it?!

---

### Post by larsw on 2007-01-06
[edit] Updated my post today (2007-Mai-07) to include some comments from bwiewiora (thanks for finding my faults when writing this down!) so that future "followers" do not need to read the replies to get it working. [/edit]

Good day everyone.

Followed instructions here and elsewhere and eventually got my fpit screen working on my Stylistic 3400. Thought the one or other line of my own quick and dirty howto below might help someone stumbling over this post. So, here's how mine worked in the end.
Hope that helps, if not post your questions and I'll try my best to help further.
Best regards
Lars

-------8<------ -------8<------ -------8<------ -------8<------ 

Stylistic 3400 fpit touchscreen driver mini howto

[B]Note: commands below require root rights. To enable sudo / su / root login, a root password needs to be set on a freshly installed ubuntu box. 
To do this, log on to X with the user account created during setup. 
Then open a shell (Alt+F2, type "xterm" and press enter) 
and type in 
```
sudo passwd
```

Note that this first asks for your normal user account password, and thereafter asks you to enter the new root password twice. 
(go this hint from a german page: [http://wiki.ubuntuusers.de/sudo]("http://wiki.ubuntuusers.de/sudo"))
[/B]
Now, on to the fpit installation:

[edit]
(0) start a root shell, i.e. open a shell and then type "su", press enter, give the root password you set above, and from here on be careful as you are root now. (I don't like using sudo all the time, so I rather stick to the "old" infamous way of becoming root for a while - knowing what I do ... most of the time ;-) )
[/edit]

(a) install the package "xserver-xorg-input-fpit" 
Normally, all you need is
```
apt-get install xserver-xorg-input-fpit
```
However, as the box I'm playing with is not yet on a network (ubuntu installed from a DVD which does not have the fpit driver package included), I had to download it from 
[http://debian.charite.de/ubuntu/pool/universe/x/xserver-xorg-input-fpit/xserver-xorg-input-fpit_1.1.0-0ubuntu1_i386.deb]("http://debian.charite.de/ubuntu/pool/universe/x/xserver-xorg-input-fpit/xserver-xorg-input-fpit_1.1.0-0ubuntu1_i386.deb")
then copy it to a floppy, then (as root, see note above) 
```

mount /dev/fd0 /media/floppy
cd /floppy
dpkg -i xserver-xorg-input-fpit

```

(b) edit /etc/X11/xorg.conf
(b.1) remove all unnecessary "InputDevice" sections that are there by default.
(b.2) create an "InputDevice" section:
```

Section "InputDevice"
    Identifier "Touchscreen"
        Driver "fpit"
        Option "Device" "/dev/ttyS1"
        Option "BaudRate" "9600"
#        Option "SwapXY"  #depending on your screen layout (landscape/portrait)
#        Option "SwapX"   #depending on your screen layout (landscape/portrait)
	Option "Passive" #very important for the 3400!
	Option "SendCoreEvents"
	Option "CorePointer"
        Option "MaximumXPosition" "4096"
        Option "MaximumYPosition" "4096"
        Option "MinimumXPosition" "0"
        Option "MinimumYPosition" "0" 
EndSection

```

The "ServerLayout" Section can be reduced to
```

Section "ServerLayout"
	Identifier "Default Layout"
	Screen	"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Touchscreen" "SendCoreEvents"
	InputDevice	"Configured Mouse"
EndSection

```


(c) create a script to activate the serial port representing the touch screen
(c.1) create /etc/init.d/finepointscreen.sh
```

#!/bin/sh
/bin/setserial /dev/ttyS1 autoconfig
/bin/setserial /dev/ttyS1 uart 16450 port 0xfd68 irq 5

```
[edit] Note(1): The file ends here! All "code" snipplets below are commands that need to be executed from the shell, they are NOT part of the above file. The file has only the above three lines. Wasn't clear to someone... [/edit]
Note(2): The ttyS1 might be 0 through 3. Run "dmesg | grep ttyS" which will initially list two devices only, one is the physical serial port of the device, the other is the FIR port. 
Compare the values shown by dmesg with your bios settings for these two ports. 
Next, run "setserial -g /dev/ttyS*" which will show all available serial ports. One of the "Unknown" types is your panel. 
Never mind what addresses are reported for the panel initially, use the above "port 0xfd68 irq 5" in your script, overwriting the settings detected. 
At least that is what I had to do, with the standard values the pointer never moved, with the above it worked immediately.
[edit]
Only to prevent confusion if you get other results than above: I have done this procedure again today on an Xubuntu 7.04 installation, and dmesg gave me four serial ports immediately, listing ttyS1 with 0xfd68 and irq5 straight away. Maybe the drivers in kernel 2.6.20-15-generic are better now? Anyhow, setserial also shows the port, and sees it as an 16550, not 16450 now....
[/edit]

(c.2) No, run this command: 
```
chmod +x /etc/init.d/finepointscreen.sh
```

(c.3) insert the created script into the runlevels:
[edit]
```
update-rc.d finepointscreen.sh defaults
```
[/edit]
This will create symlinks in /etc/rcX.d/S20finepointscreen.sh
However, gdm is started in S13gdm, and we need the finepoint screen serial port before GDM.
Hence, in each rcX.d directory:
```
mv S20finepointscreen.sh S12finepointscreen.sh
```

[edit] Note: bwiewiora suggests that the K20 scripts (kill scripts) also need to be touched to become K12. I think this is not a requirement, as it does not matter at what stage we KILL the fpit thing when shutting the box down. It was only important to initialize the thing **before** starting X. Hence, I do not include bwiewiora's advise to change the K20 things here. [/edit]

(d) restart gdm or the entire system.

(e) from now on, whenever gdm comes up, the pointer will be usable. 

Another hint: Beware the "hovering mode" hotpad icon (arrow with four lines next to it) in the lower right of the screen. This hardware screen button disables click recognition, leaving the pointer follow the pen but preventing clicks. Might be confusing :confused:  if clicked accidentally - maybe even related to the no-pen-up-recognition problem others mentioned above? (Have those checked the hotpad settings in BIOS? Just an idea.... :-k )

---

### Post by Dubstar_04 on 2007-01-18
Is this proven to work?  I am feeling in the mood for another go at mine. Has anyone had success with this method before I have a go??

---

### Post by lfjewett on 2007-01-18
Yes, I used the exact same method for my 3500.  However the hotpad buttons do not work on mine wither enabled or disabled in the BOIS, and MouseOFF events are not always recorded, leading to some annoying issues.  Like moveing a window that gets stuck to your arrow and being unable to "drop it".   The touchscreen does however work.  Best of luck to you.  ](*,)

---

### Post by Dubstar_04 on 2007-01-18
Excellent. I will have a go at this tonight. whats best for the 3400 6.06 or 6.10??

Will dapper be less demanding than edgy?

---

### Post by bwiewiora on 2007-02-03
This is a total noob question, but I can't find any answers that work anywhere else.  I have a fujitsu stylistic 3500, and I'm trying to get the pen to work.  When I try to edit xorg.conf, however, I get "Error: no write permission for file "/etc/x11/xorg.conf""

I've tried using sudo, setting the root password, using nano instead of edit, everything I can think of.  Any ideas??

---

### Post by Dubstar_04 on 2007-02-04
Depends which *buntu your using:

Press 'Alt + F2' then type in the box

ubuntu

```
gksudo nautilus
```

Kubuntu 

```
kdesu konqueror
```

Xubuntu

```
gksudo thunar
```

This will then open up a file manager that you can use to browse and edit files. People say that this is the wrong way to go about it, and you should use

```
sudo nano /blah/blah/blah.sh 
```

but as far as im concerned it works and its straight forward!!

I hope this helps. Let me know if you have any luck with the pen as i've still not got mine working!!!

What I would really like is some one to host an image of their working config that i can put on my machine, A stylistic 3400  Hint, hint!!!

---

### Post by bwiewiora on 2007-02-05
Thanks, I'll give that a shot tonight.  And if it works out, I'll post my conf file.

---

### Post by bwiewiora on 2007-02-05
Still no dice.  Thanks for the gksudo Thunar trick, though--very nice.

I configured my xorg.conf just like larsw's how-to.  One thing I was confused about, though, is what exactly goes into the finepointscreen.sh--does all the code in the 'c' subsections go into the same file?  As it is now, my finepointscreen.sh file contains:

[INDENT]#!/bin/sh
/bin/setserial /dev/ttyS1 autoconfig
/bin/setserial /dev/ttyS1 uart 16450 port 0xfd68 irq 5

chmod +x /etc/init.d/finepointscreen.sh
update-rc.d fujitsuserial.sh defaults
mv S20finepointscreen.sh S12finepointscreen.sh
[/INDENT]

I can boot without problems, but touchscreen doesn't work at all.

---

### Post by Dubstar_04 on 2007-02-06
I cant help you with this I am afraid. This is the same problem that i experienced!!

---

### Post by bwiewiora on 2007-02-17
Okay Dubstar, I think I figured it out.

finepointscreen.sh should contain:

[INDENT]#!/bin/sh
/bin/setserial /dev/ttyS1 autoconfig
/bin/setserial /dev/ttyS1 uart 16450 port 0xfd68 irq 5[/INDENT]

after that, go into a terminal and enter:

[INDENT]sudo chmod +x /etc/init.d/finepointscreen.sh[/INDENT]

Then, I found there's a typo in the how-to.  Still in the terminal, enter:

[INDENT]sudo update-rc.d finepointscreen.sh defaults[/INDENT]

in the original how-to, the file is called fujitsuserial.sh, which doesn't exist.  The above, however, works.

Still in the terminal, navigate to each rcX.d directory, and type the command in the how-to:

[INDENT]mv S20finepointscreen.sh S12finepointscreen.sh[/INDENT]

HOWEVER--when I did the previous update command, the output in the terminal showed that not all of the symlinks it created started with S20.  Some started with K20 (specifically, they were the ones in rc0.d, rc1.d, and rc6.d).  So for those I modified the command to:

[INDENT]mv K20finepointscreen.sh S12finepointscreen.sh[/INDENT]

After that, I rebooted and magically could use the pen.  I still have to experiment with a lot of things, like good writing recognition and other stuff, but at least for now, I'm psyched out of my mind.

Good Luck!

---

### Post by Dubstar_04 on 2007-02-27
Just checking how you are getting on with the pen?? I've not tried my tablet for months. might collect it from my folks house and give it a try at the weekend!!

You had any joy with hand writing recognition? or a good on screen keyboard?

I'm quite excited!!

---

### Post by bwiewiora on 2007-03-03
The software has actually left a lot to be desired.  I downloaded a program call Gournal for taking handwritten notes, and that works pretty well.  Its saving mechanism is really awkward, though (there's no "Save as", so files automatically are named by the date and time they were written), and it doesn't have any handwriting recognition.  

I actually haven't been able to locate any free handwriting recognition stuff, so that's been disappointing.  Because of the small screen, the on-screen keyboards I've found are VERY awkward to use--basically you can't look at the keyboard and enough of what you're typing at the same time.  My Fujitsu stylistic 3500 only has 800x 600 res, though, so a tablet with higher res would be a lot better in that respect.

If anyone out there has some good programs to recommend, I'd be very appreciative!

---

### Post by bcw on 2007-05-25
[QUOTE=bwiewiora]
If anyone out there has some good programs to recommend, I'd be very appreciative![/QUOTE]

Search in the forums for the xstroke deb.  That works well for me.

I've had my ST3400 working well with Xubuntu.  I mostly am using my ST5032D, but I'll do an install onto my ST3400 again this weekend.


Regards,
Bret

---

### Post by bcw on 2007-05-27
Hi,

My HowTo is [_here_]("http://ubuntuforums.org/showthread.php?p=2729857#post2729857")

---

### Post by bcw on 2007-05-27
Hi,

My HowTo is [_here_]("http://ubuntuforums.org/showthread.php?p=2729857#post2729857")

---

### Post by themischiev on 2008-06-26
Stylistic 3400 Harddrive Image For Download?

Please Someone Have An Image Of The Fujitsu Stylistic 3400 Hard Drive With Ubuntu Installed That I Could Download And Copy To My Stylistic 3400 Hard Drive?

---

