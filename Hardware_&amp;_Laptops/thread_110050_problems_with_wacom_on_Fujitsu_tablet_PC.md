---
title: "problems with wacom on Fujitsu tablet PC"
date: 2005-12-29
forum: Hardware &amp; Laptops
---

### Post by nathanielrb on 2005-12-29
To save other clueless beginners from the hours of forum browsing that I had to do, here are some step-by-step instructions for making the stylus work on the Fujitsu T4020.  It's only slightly different from other Tablet PCs, but that slight difference confused me for a while. 

Please make suggestions for how to improve this...

thanks

nathaniel

* * *


>In the Synaptic Package Manager, install the following packages:

wacom-kernel-source
wacom-tools
xserver-xorg-input-wacom
setserial

>in the terminal type:

[B]$sudo setserial /dev/ttyS0 port 0x0220 irq 4 autoconfigure
$wacdump -f c100 /dev/ttyS0[/B]

You should be able to influence the numbers on the screen with your stylus.  If not, start browsing the forums...

>then type 

**$gksudo 'gedit /etc/X11/xorg.conf'**

to edit the xorg.conf file.  Add the following lines to the file:

Section "InputDevice"
  Driver        "wacom"
  Identifier    "stylus"
  Option        "Type"          "stylus"
 Option  "SendCoreEvents"        "true"
  Option	"Device"	"/dev/ttyS0"
  Option        "ForceDevice"   "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "eraser"
  Option        "Type"          "eraser"
  Option	"Device"	"/dev/ttyS0"
  Option        "ForceDevice"   "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "cursor"
  Option        "Type"          "cursor"
  Option	"Device"	"/dev/ttyS0"
  Option        "ForceDevice"   "ISDV4"               # Tablet PC ONLY
EndSection

and then add these lines to the Section "ServerLayout":

        InputDevice     "cursor"    "SendCoreEvents"
        InputDevice     "stylus"   "SendCoreEvents"
        InputDevice     "eraser"    "SendCoreEvents"

>finally, to make the changes permanent, type in the terminal:

**$sudo dpkg-reconfigure setserial**

and choose the option 'autosave once'

Restart the X server by pressing [ctl]-[alt]-[backspace]

and once you're logged back into Ubuntu type:

**$sudo xsetpointer stylus**

That should work. If not...

---

### Post by nathanielrb on 2005-12-30
now it works (so I'm an overeager poster).

the missing step was: $sudo xsetpointer stylus

---

### Post by technosophos on 2006-01-20
Okay... I've installed the source files for a new kernel (wacom-kernel-source)... do I need to BUILD the new kernel? Or is the step of installing the source simply a shorthand way of getting all of the dependencies satisfied?

---

### Post by technosophos on 2006-01-20
Using a variation of the above instructions, I got the tablet for my Toshiba Satellite R-15 working under Ubuntu 5.10.

Step 1: I installed the packages Nathanial specified. I'm not sure which of these are actually important... since I didn't compile a new kernel, I'm not sure that the wacom-kernel-sources package was necessary (though I could be wrong about that).

Step 2: I took a peek in /dev/ to see what devices I had to choose from... and lo and behold, there was a device named wacom0. I guess the R15's tablet gets recognized by default.

So there was no need to mess with setserial on this tablet. Yay.

Hint: If you do not know which tty your tablet is listening on, you can use the wacdump command to test various /dev/ttyS* devices.

Step 3: Using 'wacdump /dev/wacom0', I tested the device. Here's how it works: with your stylus ready, type the command and hit enter. Then immediately start drawing on the screen. You should see coordinate data written to the screen. Moments after you stop writing, the 'wacdump' command will exit.

NOTE: /dev/wacom0 is a symbolic link to /dev/ttyS14. What does that mean? It means that the Toshiba Satellite Wacom tablet listens on a different serial device than the Fujitsu tablet does. (And if you are using yet a different model, it may listen on yet a different tty).

Step 4: Edit /etc/X11/xorg.conf as Nathanial suggested, **EXCEPT** replace the all occurances of '/dev/ttyS0' with '/dev/wacom0'.

Step 5: Log out of the desktop and restart the X server (CTRL-ALT-Backspace). At this point (even at the login screen), you should be able to use the stylus instead of the mouse.

There is no need, under this setup, to do the dpkg-reconfigure or xpointer steps on an R-15.

Thanks, Nathanial. Your tutorial saved me hours (maybe days) of research (and associated anguish!).

----
More on my [installing Ubuntu on a Toshiba Satellite R-15]("http://aleph-null.tv/go.php?doc=20050625-0102-56.xml").

---

### Post by mauriceling on 2006-03-22
I've tried nathanielrb's instructions but I still cannot get it to work. When I restarted X server, the stylus is not working (as in the cursor is not moving). All seems to work prior to that, including "wacdump -f c100 /dev/ttyS0".
"sudo xsetpointer stylus" did not show any errors and doesn't seems to have an effect either.

Any suggestions?

---

### Post by mauriceling on 2006-03-23
I've tried to run wacdump on the various /dev/ttyS* using "wacdump -f c100 /dev/ttyS*" where * is 0 to 53. In my system, there is ttyS0-53.

After running the following command:
sudo setserial /dev/ttyS2 port 0x0220 irq 4 autoconfigure
wacdump -f c100 /dev/ttyS2 
shows some readings
However, wacdump -f c100 /dev/ttyS3 showed the same screen but no response. The rest 0,1,4-53, gave WacomOpenTablet: Invalid argument.

Any suggestions?

---

### Post by mauriceling on 2006-03-24
Ok, this is what I've found out:

1. The instructions by nathanielrb will work for Linux Kernel 2.6.12-9-386, it is the kernel installed by Breezy Badger (Ubuntu 5.10).

2. If a system upgrade is done by Synaptics Package Manager, a newer kernel (2.6.10-386) may be installed and will not work.

3. Nathanielrb's instructions did not survive a reboot on my system, that is, when I reboot, I cannot control the cursor with stylus until I do a "sudo setserial /dev/ttyS0 port 0x0220 irq 4 autoconfigure", followed by restarting X server with [ctrl][alt][backspace].

4. I solve (3) by adding a file /etc/serial.conf, which was not present in my system, and putting the line "/dev/ttyS0 port 0x0220 irq 4 autoconfigure" in it. This somehow allows ttySo to be configure before X server is initiated following a reboot.

5. There are some cases where [ctrl][alt][backspace] doesn't restart X but end up with a text-based login screen. In that case, I have to login, followed by "sudo killall gdm" to kill the Gnome Display Manager, followed by "sudo gdm" to run Gnome Display Manager.

Hope this can help anyone.

---

### Post by RAV TUX on 2006-05-08
this may help also:

[https://wiki.ubuntu.com/LaptopTestingTeam/FujitsuT4010D?highlight=%28fujitsu%29](https://wiki.ubuntu.com/LaptopTestingTeam/FujitsuT4010D?highlight=%28fujitsu%29)

[http://calkinsc.home.comcast.net/fujitsu_st_4000.html](http://calkinsc.home.comcast.net/fujitsu_st_4000.html)

---

### Post by moclippa on 2006-05-29
Thanks for the support, I was able to get everything working on my Toshiba Tecra.... For anyone still confused and/or too noob for even this forum to suffice (me included) I've taken most of the relevant info from the various posts, and [tried to put it all down in one place]("http://clipperisms.blogspot.com/2006/05/getting-toshiba-tablet-input-to-work.html") (its a blog, so sorry if that offends anyone.. not trying to get hits, but figured since all the info was up here anyways I didnt want to repeat...)

I was able to get it working perfectly through various peoples suggestions.

I had to sort through the info a bit... but the link will help you if you are running a Toshiba laptop on Ubuntu Breezy 5.10 

Hope that helps people a bit more... And thanks for everyone that posted up here, you were all a tremendous help!

---

### Post by moclippa on 2006-05-30
Just upgraded to Dapper... the same process does not work because the /dev/wacom0 has been changed....

anyone having that problem can fix it easily by replacing all instances of 'wacom0' with 'wacom'

Seems like the file names changed and nothing else

You can find the [new fixes for dapper here]("http://ubuntuforums.org/showthread.php?t=184542&highlight=tablet+pc")

---

### Post by wylie348 on 2006-10-14
Yes!  Finally got my Fujitsu T4210 tablet working - Using the instructions posted above.  Time to drop windows...!
:p

---

### Post by smitty5533 on 2007-01-23
Thanks guys, we got my toshiba r15 recognizing the stylus, the only thing that i'm concerned about is that when in drag the stylus across the screen it drags open the same square that there would be from clicking and dragging the mouse...
anything to worry about? i feel like it isn't a biggie

---

### Post by azim.manjee on 2007-05-20
I am having a lot of trouble with this. i have a t4020 with fiesty fawn and i cant seem to get the wacom device recongnized, its not showing up in the /dev/input area, and i have tried every device listed- attatched is the screen shot of the hardware info and the /dev/input folder-

---

### Post by thoice on 2007-05-20
looks like there is a new version of wacdump? is it wacom tools? so 
> **nathanielrb said:**
> 
**$wacdump -f c100 /dev/ttyS0**

doesn't work.... the found workaround is to change c100 to tpc
so it will look like 
$wacdump -f tpc /dev/ttyS0

maybe it's just for my situation

---

### Post by azim.manjee on 2007-05-20
thanks for your help, i figured it out around 4am this morning though- i am a total noob, does anyone know about the biometric device ?

---

### Post by azim.manjee on 2007-05-21
OK so it was UP and runing for about 24 hours. then i was tinkering with the setserial autosave, and NOW whenever i put the pen to the screen, the mouse shoots to the lower left hand corner, what the hell do i do now?

---

### Post by thndrbck on 2007-05-22
I just used this info to get the touchscreen working on my Toshiba M400. After insuring that the necessary packages were installed under Fiesty, I declined to change the entries in the xorg.conf file. What I discovered was that there is a hard link in /dev/input called wacom. That link points to /dev/ttyS0. I created a soft link, /dev/wacom that points to /dev/input/wacom.

restarted X with ctrl-alt-bksp and bam! it is working nicely.

---

### Post by emoore625 on 2007-08-03
In Feisty on my T4020, I needed to use ttyS0 instead of wacom and tpc instead of c100.  When I edited Xorg.conf, I replaced /dev/input/wacom with /dev/ttyS0 although I probably could have just created a soft link. 

Interesting that we all have basically the same product and there are about 20 different setups.

---

### Post by azim.manjee on 2007-08-03
im still having issues getting ACPI working, any ideas? no brightness control, hibernation sometimes has issues...:-| (im still in love though)

---

### Post by emoore625 on 2007-08-03
Yeah no luck on those feats at all.  I'd like to get the function keys working to adjust brightness.  Seems like F3, F8 and F9 work for sound.  F4 for the mouse and F10 for display seem to be working as well.  It's just the brightness.

---

### Post by emoore625 on 2007-08-03
It seems as if my settings are being reset each time I shutdown and restart.  Any way I can get the stylus to work on boot?  

Thanks a bunch.  We're only as good as all of us.

---

### Post by sburhan on 2007-08-23
> **wylie348 said:**
> Yes!  Finally got my Fujitsu T4210 tablet working - Using the instructions posted above.  Time to drop windows...!
:p

Hi Whylie,

I used Fujitsu T4215v. I'm still new with Ubuntu feisty and try to set the Tablet.

Pls confirm me that ,which step by step guides to follow.

THanks...xie xie..

stephen_burhanATyahooDOTcom

---

### Post by sangamc on 2008-01-20
i was able to succesfully get the pen working on my t4020 by using tpc instead of c100 and using ttyS0 instead of wacom when modifying xorg.conf. even after rebooting the pen works correctly.

i would like to know if its possible to configure the buttons that flip the orientation of the display? if anyone has had any success with this please let me know

---

### Post by jklehm on 2008-04-29
Slightly simplified for 8.04 on a Fujitsu T4020D:

>In the Synaptic Package Manager, install the following packages:

wacom-tools
xserver-xorg-input-wacom
setserial

>in the terminal type:

$sudo setserial /dev/ttyS0 port 0x0220 irq 4 autoconfigure
$wacdump -f tpc /dev/ttyS0

You should be able to influence the numbers on the screen with your stylus. If not, start browsing the forums...

>then type

$gksudo 'gedit /etc/X11/xorg.conf'

>Change all instances of Option "Device" "/dev/input/wacom"
>to Option "Device" "/dev/ttyS0"

>Uncomment these InputDevice lines in the Section "ServerLayout":

# Uncomment if you have a wacom tablet
#     InputDevice "cursor" "SendCoreEvents"
#     InputDevice "stylus" "SendCoreEvents"
#     InputDevice "eraser" "SendCoreEvents"

>finally, to make the changes permanent, type in the terminal:

$sudo dpkg-reconfigure setserial

>and choose the option 'autosave once'

Then **Reboot ubuntu**

From there on all should be well =)

---

### Post by priegog on 2008-04-29
@jklehm
The package wacom-kernel-sources is not available... and in the repos GUI options when I click on sources only a "-" is shown. Is this package necessary for it to work? and of yes, how do I get a hold of it? Thanks

---

### Post by MosMusy on 2008-04-29
This is what mine gives me:

movses@movses-laptop:~$ $sudo setserial /dev/ttyS0 port 0x0220 irq 4 autoconfigure
Cannot autoconfigure port: Operation not permitted

---

### Post by priegog on 2008-04-30
Ok here's a question for all of you knowledgable people out there:
in this line:
```
$sudo setserial /dev/ttyS0 port 0x0220 irq 4 autoconfigure
```
what does the 0x0220 stand for? I know it must be some kind of physical address, so my question is, how do I find this value for my particular tablet? (different model)
Thanks

---

### Post by marian99us on 2008-05-04
> **technosophos said:**
> Using a variation of the above instructions, I got the tablet for my Toshiba Satellite R-15 working under Ubuntu 5.10.

Step 1: I installed the packages Nathanial specified. I'm not sure which of these are actually important... since I didn't compile a new kernel, I'm not sure that the wacom-kernel-sources package was necessary (though I could be wrong about that).

Step 2: I took a peek in /dev/ to see what devices I had to choose from... and lo and behold, there was a device named wacom0. I guess the R15's tablet gets recognized by default.

So there was no need to mess with setserial on this tablet. Yay.

Hint: If you do not know which tty your tablet is listening on, you can use the wacdump command to test various /dev/ttyS* devices.

Step 3: Using 'wacdump /dev/wacom0', I tested the device. Here's how it works: with your stylus ready, type the command and hit enter. Then immediately start drawing on the screen. You should see coordinate data written to the screen. Moments after you stop writing, the 'wacdump' command will exit.

NOTE: /dev/wacom0 is a symbolic link to /dev/ttyS14. What does that mean? It means that the Toshiba Satellite Wacom tablet listens on a different serial device than the Fujitsu tablet does. (And if you are using yet a different model, it may listen on yet a different tty).

Step 4: Edit /etc/X11/xorg.conf as Nathanial suggested, **EXCEPT** replace the all occurances of '/dev/ttyS0' with '/dev/wacom0'.

Step 5: Log out of the desktop and restart the X server (CTRL-ALT-Backspace). At this point (even at the login screen), you should be able to use the stylus instead of the mouse.

There is no need, under this setup, to do the dpkg-reconfigure or xpointer steps on an R-15.

Thanks, Nathanial. Your tutorial saved me hours (maybe days) of research (and associated anguish!).

----
More on my [installing Ubuntu on a Toshiba Satellite R-15]("http://aleph-null.tv/go.php?doc=20050625-0102-56.xml").

could you help me with my Satellite R25 ? my stylus doesn't do anything! 
please please please i need help!

---

### Post by jklehm on 2008-05-06
@ priegog

Good catch about the wacom kernel sources.  They are no longer required as they have been accepted into mainline kernel. I have updated my earlier post and removed it.

As far as the physical address goes,  I do not know at this time.  I will post back if I should find out. 


@marian99us

Its easier to help someone when they have posted which parts of the how to worked and which didn't.  Stylus doesn't work isnt' descriptive enough.  

Post back with which step of the howto fails and the output of the following commands from a terminal:

$xidump -l

$xsetpointer -l

---

### Post by priegog on 2008-05-06
> **jklehm said:**
> @ priegog
As far as the physical address goes,  I do not know at this time.  I will post back if I should find out. 


Thanks, that'd help me a lot.

---

### Post by jklehm on 2008-05-06
List of io ports:
[http://www.pcguide.com/ref/mbsys/res/ioSummary-c.html](http://www.pcguide.com/ref/mbsys/res/ioSummary-c.html)

However the easiest way would probably to boot windows and look in device manager at what port io address it is using there.

---

### Post by priegog on 2008-05-06
> **jklehm said:**
> List of io ports:
[http://www.pcguide.com/ref/mbsys/res/ioSummary-c.html](http://www.pcguide.com/ref/mbsys/res/ioSummary-c.html)

However the easiest way would probably to boot windows and look in device manager at what port io address it is using there.

Thanks a bunch. It just so happens that I dual boot now, I hadn't tought of that. Linux should really have an easy way to check that tho. Thanks again :)

---

### Post by jklehm on 2008-05-06
Well its a driver thing. Wacom is actually pretty good with their linux drivers. I'm not sure if it is wacoms issue or manufacturers(fujitsu, dell, etc}.

---

### Post by HoloArgue on 2008-05-09
> **jklehm said:**
> Slightly simplified for 8.04 on a Fujitsu T4020D:

>In the Synaptic Package Manager, install the following packages:

wacom-tools
xserver-xorg-input-wacom
setserial

>in the terminal type:

$sudo setserial /dev/ttyS0 port 0x0220 irq 4 autoconfigure
$wacdump -f tpc /dev/ttyS0

You should be able to influence the numbers on the screen with your stylus. If not, start browsing the forums...

>then type

$gksudo 'gedit /etc/X11/xorg.conf'

>Change all instances of Option "Device" "/dev/input/wacom"
>to Option "Device" "/dev/ttyS0"

>Uncomment these InputDevice lines in the Section "ServerLayout":

# Uncomment if you have a wacom tablet
#     InputDevice "cursor" "SendCoreEvents"
#     InputDevice "stylus" "SendCoreEvents"
#     InputDevice "eraser" "SendCoreEvents"

>finally, to make the changes permanent, type in the terminal:

$sudo dpkg-reconfigure setserial

>and choose the option 'autosave once'

Then **Reboot ubuntu**

From there on all should be well =)

This worked for me on my T4210 - thanks :) Only thing was that I had to add the relevant wacom tablet lines to xorg.conf (see original post).

---

### Post by priegog on 2008-05-16
So... I got it working WOOHOO! but it only works as a mouse, and a bad one at that. The eraser acts as a normal click and if I press the button it doesn't act as a right click. How do I make it recognize them as such? I don't know if it has anything to do with that, but when i did the last step (sudo xsetpointer stylus) it returned an error, something about not finding any stylus device.
Also, I'd like to know if anyone knows how to make either cellwriter or an on-screen keyboard appear at gnome login so I don't need to hookup a keyboard.
Thanks

---

### Post by phixx2000 on 2008-07-23
> **marian99us said:**
> could you help me with my Satellite R25 ? my stylus doesn't do anything! 
please please please i need help!

i have a R25-3513. I can help you. Let me know what you have installed

---

