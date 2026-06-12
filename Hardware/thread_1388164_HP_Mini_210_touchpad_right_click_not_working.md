---
title: "HP Mini 210 touchpad right click not working"
date: 2010-01-22
forum: Hardware
---

### Post by MsKK on 2010-01-22
Hello everyone. I'm a newbie in this forum so please excuse me if i mislabeled something. I just bought an HP Mini 210 and installed UNR on it. I solved a problem with the wireless connection but now I can't figure out how to fix the touchpad. The pointer works (moves) and the left click works like a charm. However I cannot do right clicking (when I touch the button it only does left click instead). Since the buttons are IN the touchpad itself, I think this is the source of the problem.

Also, if someone knows why I get a black screen of death after closing and re-opening the lid, I would welcome any advice.

Thanks again.

---

### Post by sdledesma on 2010-01-27
I've got a similar problem with the touchpad.  I can left click only by tapping the pad (clicking on the bottom left cornet will not work)  No right click and no click and drag. 


Any ideas?

Santi

---

### Post by The Deacon on 2010-02-01
I've got the same issue.  Any help would be greatly appreciated.

The "trigger secondary click by holding down primary button" (under System> Mouse) isn't a disaster if you really need a right click, at least.

---

### Post by cbrman on 2010-02-11
Try this:

It's in german but the terminal commands are the same

[http://greendevnet.blogspot.com/2009/10/ubuntu-910-karmic-koala-no-touchpad.html](http://greendevnet.blogspot.com/2009/10/ubuntu-910-karmic-koala-no-touchpad.html)

---

### Post by JohnFr on 2010-02-12
I can't help with the touchpad, but perhaps with the
black screen.  I have a Mini 110.  Closing the top
puts it in sleep mode (this is customizable).  Opening
reawakens it, but the screen is blanked.  When I come
back from sleep I wait a couple of seconds then press
"fn f4" which is the hardware keystroke to brighten the screen and then it comes back.

---

### Post by Sabot on 2010-02-12
To get the trackpad working correctly you need to use the terminal and enter in the below commands. Make sure you press enter after each command:

    ```
sudo su
```

    ```
echo options psmouse proto=exps > /etc/modprobe.d/psmouse.modprobe
```

    ```
reboot
```


Once the computer reboots your trackpad will be able to do left click and drag and right clicking.

---

### Post by JCasper on 2010-02-12
This is great. Thank you so much. Worked perfect. Now if we can get two finger scrolling working, I'll be set.

---

### Post by MsKK on 2010-02-13
Thanks, it worked for me too. As JCasper said, now I only need the double scrolling. Is it possible to set the touchpad "clickable" area? because the right and left buttons are embedded in the touchpad and the cursor moves everytime i click.

I also solved my screen issue thank you guys :)

---

### Post by sevenX on 2010-03-13
> **Sabot said:**
> To get the trackpad working correctly you need to use the terminal and enter in the below commands. Make sure you press enter after each command:

    ```
sudo su
```

    ```
echo options psmouse proto=exps > /etc/modprobe.d/psmouse.modprobe
```

    ```
reboot
```


Once the computer reboots your trackpad will be able to do left click and drag and right clicking.



AWSOME!!!! :popcorn: WORKED PERFECTLY! THANK YOU VERY MUCH, I have hp mini 210 also and have been wondering about this for awhile now. Just curious though... what is two finger scrolling?

---

### Post by sevenX on 2010-03-13
Should mark this thread as solved "MsKK" under thread tools at the top! :D

---

### Post by jnetman1 on 2010-03-18
You're much better off actually fixing the problem with the driver, as telling the system that the touchpad is a PS/2 mouse leaves you with zero control of the pad on the Mini 210. To do this, download the attachment at the bottom of this post and save it in your home folder:

Open the terminal on your Mini 210 and

```
sudo apt-get install build-essential patch linux-source
```

The kernel source will be a tarball that is installed in /usr/src. Extract it to your home directory like so:

```
tar -xjvf /usr/src/linux-source <tab>
``` 

Note that pressing tab will autocomplete to the version you downloaded. Once extracted, change to the source directory and untar the patch attachment you downloaded at the beginning:

```
cd linux-source <tab>
tar -xzvf ../clickpad.tar.gz
```

Now we'll patch the driver files, copy the Makefile to the right place, and compile and install the new driver:

```
patch -p1 <clickpad_patch
cp Makefile drivers/input/mouse/
cd drivers/input/mouse
make
sudo make install
```

Reboot your machine, and you'll find the touchpad works like it should. Note that this patch is based on Takashi Iwai's fine work here: [http://patchwork.kernel.org/patch/67335/](http://patchwork.kernel.org/patch/67335/)

---

### Post by theng168 on 2010-03-19
thx bro, ur clickpad patch works like a charm :D

---

### Post by MsKK on 2010-03-19
well, it didnt change much from the previous fix. I still cannot scroll.

---

### Post by theng168 on 2010-03-19
MsKK, make sure you remove the psmouse.modprobe and do a reboot.
Mine fully working now. Just cannot 2-fingers scroll and pinch to zoom.

Theng

---

### Post by MsKK on 2010-03-19
What I meant was that the psmouse.modprobe change left my mouse just like it is now: right and left click working but no 2-finger scrolling, so I don't see any difference between the psmouse fix vs. the clickpad.tar.gz patch fix.

---

### Post by theng168 on 2010-03-20
i see.
because mine previously if using the psmouse.modprobe, the vertical scrolling not working. So i left no choice but to use the clickpad.tar.gz

---

### Post by RosyHP210 on 2010-03-20
clickpad.tar.gz works great, buttons and vertical scroll!  Thanks!:D

---

### Post by MsKK on 2010-03-23
I removed the psmouse change, rebooted, and used the clickpad patch, but i still cannot scroll. 

To the person who said it fixed the scroll... did u do any additional steps? do u also have a hp mini 210?

---

### Post by RosyHP210 on 2010-03-23
Yes, HP Mini 210, followed the instructions religiously ;)
Buttons work, as does the vertical scroll on the right hand edge.

---

### Post by pemaincadangan on 2010-03-27
I've tried the clickpad.tar.gz, the result is; as in it's name, it activates the two clickpad at the bottom, shut down the touch function at the clickpad area (so the cursor won't go crazy when being clicked), and the good news is the edge scrolling function still working.

But this patch didn't enable the multi touch function, when we press with one finger, and then add a pressure with another finger, the cursor still going crazy to the corner :(

*still waiting for another tricks to enable the multi touch.

Anyway, the clickpad patch is very useful, this is so much better than default, thanks for the trick :)

---

### Post by penguinrepair on 2010-03-30
AWWSSOOMMEE... my hp mini 210-1010NR, now windoze free, touchpad patch wifi netbook-remix 16G sd card, swapfiled, quick and clean....:popcorn:

---

### Post by Black Sunshine on 2010-04-01
Well done! Worked fine for me.

---

### Post by danben on 2010-04-03
I installed the patch and my mouse stopped working altogether.  I have an Envy 15, not a Mini 210, but it uses the Synaptics Clickpad so I'd think it wouldn't make a difference.  Anyone have similar results or know why this wouldn't work for me?

---

### Post by strad on 2010-04-05
Hi All,

I am having some problems with the mouse patch installation. I loaded Ubuntu onto my HP 210 yesterday and have resolved most issues. I tried setting up the patch as described but think I have done something wrong.

I downloaded the patch and put it into my home folder (I found that I was only able to place things in the named user folder under the home folder. I then opened the terminal and entered the first line of the code. The terminal asked if I wanted to download patches so I said "yes". After the download the second line of code gave an error message <bash: syntax error near unexpected token `newline'>.

I have not been able to proceed any further with this remedy. I would appreciate some help on this one. Please explain any instructions at a very detailed level. 

I also noted someone said that they removed the PS2 code that they had previously entered. How is this done?

Thanks

---

### Post by Marktech on 2010-04-05
Hurrah, the patch worked for me -- many thanks!

---

### Post by Noirdraco on 2010-04-05
> **jnetman1 said:**
> You're much better off actually fixing the problem with the driver, as telling the system that the touchpad is a PS/2 mouse leaves you with zero control of the pad on the Mini 210. To do this, download the attachment at the bottom of this post and save it in your home folder:

Open the terminal on your Mini 210 and

```
sudo apt-get install build-essential patch linux-source
```The kernel source will be a tarball that is installed in /usr/src. Extract it to your home directory like so:

```
tar -xjvf /usr/src/linux-source <tab>
```Note that pressing tab will autocomplete to the version you downloaded. Once extracted, change to the source directory and untar the patch attachment you downloaded at the beginning:

```
cd linux-source <tab>
tar -xzvf ../clickpad.tar.gz
```Now we'll patch the driver files, copy the Makefile to the right place, and compile and install the new driver:

```
patch -p1 <clickpad_patch
cp Makefile drivers/input/mouse/
cd drivers/input/mouse
make
sudo make install
```Reboot your machine, and you'll find the touchpad works like it should. Note that this patch is based on Takashi Iwai's fine work here: [http://patchwork.kernel.org/patch/67335/](http://patchwork.kernel.org/patch/67335/)

not working with ubuntu 10.04

---

### Post by danben on 2010-04-05
> **Noirdraco said:**
> not working with ubuntu 10.04

Maybe that was what was wrong with mine.

---

### Post by gurashi on 2010-04-07
> **danben said:**
> Maybe that was what was wrong with mine.
Same here how do i reverse this?

---

### Post by ephevos on 2010-04-08
Probably there is a better way, but what I did is reinstalling the kernel.

sudo apt-get remove linux-image-2.6.32-19-generic
sudo apt-get install linux-image-2.6.32-19-generic

---

### Post by pauljwells on 2010-04-22
Lucid uses the udev architecture for input device control, apparently :-S

I found this on the Debian Wiki:

[http://wiki.debian.org/SynapticsTouchpad]("http://wiki.debian.org/SynapticsTouchpad")

> This goes in /etc/udev/rules.d/99-synaptics.rules


ACTION!="add|change", GOTO="my_synaptics_end"
KERNEL!="event*", GOTO="my_synaptics_end"
ENV{ID_INPUT_TOUCHPAD}!="1", GOTO="my_synaptics_end"

ENV{x11_driver}="synaptics"

ATTR{device/name}=="*SynPS/2*", \
  ENV{x11_options.SHMConfig}="On", \
  ENV{x11_options.EmulateTwoFingerMinZ}="40", \
  ENV{x11_options.VertTwoFingerScroll}="1", \
  ENV{x11_options.HorizTwoFingerScroll}="1", \
  ENV{x11_options.TapButton1}="1", \
  ENV{x11_options.TapButton2}="2", \
  ENV{x11_options.TapButton3}="3"

LABEL="my_synaptics_end"

You have to delete the psmouse.modprobe file from /etc/modprobe.d/ if you used the psmouse kludge before, then create the 99-synaptics.rules file and fill in the above text and reboot. For me it got left and right mouse clicks working and also right hand edge scrolling, nice!

There is a whole section in the Ubuntu docs about setting this up here:

[http://manpages.ubuntu.com/manpages/karmic/man4/synaptics.4.html]("http://manpages.ubuntu.com/manpages/karmic/man4/synaptics.4.html")

Maybe we can have a play around and improve on the Debian file?

---

### Post by tgm4883 on 2010-04-22
> **pauljwells said:**
> Lucid uses the udev architecture for input device control, apparently :-S

I found this on the Debian Wiki:

[http://wiki.debian.org/SynapticsTouchpad]("http://wiki.debian.org/SynapticsTouchpad")



You have to delete the psmouse.modprobe file from /etc/modprobe.d/ if you used the psmouse kludge before, then create the 99-synaptics.rules file and fill in the above text and reboot. For me it got left and right mouse clicks working and also right hand edge scrolling, nice!

There is a whole section in the Ubuntu docs about setting this up here:

[http://manpages.ubuntu.com/manpages/karmic/man4/synaptics.4.html]("http://manpages.ubuntu.com/manpages/karmic/man4/synaptics.4.html")

Maybe we can have a play around and improve on the Debian file?

I didn't make either change. I used to have the issue (no right/left click, only tapping), but recent updates seem to have fixed that. Is it possible that is what fixed your issue and not that file?


Anyone know what that little hole at the top left of the touchpad is? I think it's a light saying the touchpad is on or off, but thats just a guess.

---

### Post by MsKK on 2010-04-22
I want to know how can I make the 2 finger scroll work properly

---

### Post by pauljwells on 2010-04-22
@tgm4883 is right. And I thought I'd been really clever! :-/

Looks like our Minis are supported ootb on Lucid

---

### Post by tempted on 2010-04-23
OMG - I'm not afraid to type anymore on my 210... this is a dream come true. THANK YOU! 

to delete the modprobe ..

sudo nautilus <in terminal> then delete the file in the above mentioned location. 

also sudo gedit the Rules file.
-- 

I was able to type that whole thing without the mouse moving everywhere :P . YOU ARE A GOD. I read that they had implemented the new synaptic drivers, but didn't know how to use them.

---

### Post by ElectroDruid on 2010-05-01
> **pauljwells said:**
> Lucid uses the udev architecture for input device control, apparently :-S

I found this on the Debian Wiki:

[http://wiki.debian.org/SynapticsTouchpad](http://wiki.debian.org/SynapticsTouchpad)



Thank you very much!  It's great to finally have that scroll bar working.

---

### Post by rudeybear on 2010-05-02
Thanks a million, works perfectly on my Mini 210.

If anyone's having issues with this, make sure you delete the psmouse.modprobe file as discussed in this thread. Once I did that everything worked perfectly;

( Cheers to "Tempted" for the below line on how to do this, also in this thread ):

"sudo nautilus <in terminal> then delete the file in the above mentioned location."

---

### Post by MsKK on 2010-05-02
> **rudeybear said:**
> Thanks a million, works perfectly on my Mini 210.

If anyone's having issues with this, make sure you delete the psmouse.modprobe file as discussed in this thread. Once I did that everything worked perfectly;

( Cheers to "Tempted" for the below line on how to do this, also in this thread ):

"sudo nautilus <in terminal> then delete the file in the above mentioned location."

But do you have 2-finger scrolling?

---

### Post by onionman911 on 2010-05-03
Does not work :-(

I get this when I patch


patching file drivers/input/mouse/synaptics.c
Hunk #1 succeeded at 365 with fuzz 2 (offset 38 lines).
Hunk #2 succeeded at 487 with fuzz 2 (offset 41 lines).
Hunk #3 succeeded at 784 with fuzz 2 (offset 41 lines).
patching file drivers/input/mouse/synaptics.h
Reversed (or previously applied) patch detected!  Assume -R? [n] 


saying yes or no will lead to errors during ''make''


make -C /lib/modules/2.6.32-21-generic/build SUBDIRS=/home/dany/linux-source-2.6.32/drivers/input/mouse modules
make: *** /lib/modules/2.6.32-21-generic/build: Aucun fichier ou dossier de ce type. Arrêt.
make: *** [default] Erreur 2


sorry for the french :-O

---

### Post by onionman911 on 2010-05-05
Help anyone?

thx!

---

### Post by tgm4883 on 2010-05-05
Are you doing this on 10.04? cause you shouldn't need to. the touchpad works OOTB in 10.04

---

### Post by MsKK on 2010-05-05
upgraded to 10.04, but still no multitouch... anyone?

---

### Post by onionman911 on 2010-05-05
> **tgm4883 said:**
> Are you doing this on 10.04? cause you shouldn't need to. the touchpad works OOTB in 10.04

Yes on 10.04. But I have the exact same problem as described.

:(
What can i do?

---

### Post by John Baptist on 2010-05-06
I found that on the Ubuntu 10.04, the following command will work very well:

```

synclient TapButton2=3 HorizTwoFingerScroll=1 VertTwoFingerScroll=1 EmulateTwoFingerMinZ=29 EmulateTwoFingerMinW=5 JumpyCursorThreshold=200
```On my HP Mini 210, the above command will enable two finger scroll (horizontal and vertical), disable random mouse jumping, and will let me tap with two fingers for a right click. The only problem is that the settings are "forgotten" when you reboot, hibernate, or suspend.

I believe this is just another way of accomplishing the same thing as the above solution (with synaptic-rules), but can be done on the command line. I hope this will be helpful.

---

### Post by MsKK on 2010-05-07
> **John Baptist said:**
> I found that on the Ubuntu 10.04, the following command will work very well:

```

synclient TapButton2=3 HorizTwoFingerScroll=1 VertTwoFingerScroll=1 EmulateTwoFingerMinZ=29 EmulateTwoFingerMinW=5 JumpyCursorThreshold=200
```On my HP Mini 210, the above command will enable two finger scroll (horizontal and vertical), disable random mouse jumping, and will let me tap with two fingers for a right click. The only problem is that the settings are "forgotten" when you reboot, hibernate, or suspend.

I believe this is just another way of accomplishing the same thing as the above solution (with synaptic-rules), but can be done on the command line. I hope this will be helpful.

THANK YOU!!!! This was just what I was looking for. It worked!! If someone figures out how to make this permanent (without having to execute everytime one reboots) I will change the status of the thread as solved.

---

### Post by tgm4883 on 2010-05-07
> **MsKK said:**
> THANK YOU!!!! This was just what I was looking for. It worked!! If someone figures out how to make this permanent (without having to execute everytime one reboots) I will change the status of the thread as solved.

I'm working on it. I think you will need to make changes to a udev rule for it, but I'm not that knowledgable on udev.

---

### Post by Sisophon2001 on 2010-05-07
> **onionman911 said:**
> Help anyone?

thx!

A version of this patch has made it into 10.04 so there is no longer any need to install it. However two finger scrolling is still not supported. There is one difference between 10.04 code and the patch, the size of the non-touch sensitive buttons is smaller in 10.04, about half the thickness, and with my fingers this makes the mouse buttons difficult to use.

Garvan

---

### Post by darkmoon on 2010-05-08
> **Sisophon2001 said:**
> There is one difference between 10.04 code and the patch, the size of the non-touch sensitive buttons is smaller in 10.04, about half the thickness, and with my fingers this makes the mouse buttons difficult to use.
Garvan

I did notice that.  It's annoying since when I checked, the patch itself actually lined up with the lines on the synaptics clickpad.   The one that was placed in the kernel basically made it almost impossible to use.  Well, you have to slide your finger along the edge of the clickpad if you have larger fingers.

I was actually hoping to just be able to apply the patch and be done with it.   Guess we'll now have to wait for the kernel to get updated with better patches, or re-patch the module again.

---

### Post by drivindisco on 2010-05-08
Having same issue on 10.04... fix did seem to help a little. I can side scroll and tap to click. However, click hold highlighting and lassoing don't work. Any ideas?

---

### Post by Sisophon2001 on 2010-05-11
> **drivindisco said:**
> Having same issue on 10.04... fix did seem to help a little. I can side scroll and tap to click. However, click hold highlighting and lassoing don't work. Any ideas?

You can get this to work but you need to re-train your fingers. If you click first (fingers off the main touch sensitive pad area) and then drag it should work. Not ideal - but good to know when you need it.

Garvan

---

### Post by zythar on 2010-05-21
> **jnetman1 said:**
> You're much better off actually fixing the problem with the driver, as telling the system that the touchpad is a PS/2 mouse leaves you with zero control of the pad on the Mini 210. To do this, download the attachment at the bottom of this post and save it in your home folder:

Open the terminal on your Mini 210 and

```
sudo apt-get install build-essential patch linux-source
```

The kernel source will be a tarball that is installed in /usr/src. Extract it to your home directory like so:

```
tar -xjvf /usr/src/linux-source <tab>
``` 

Note that pressing tab will autocomplete to the version you downloaded. Once extracted, change to the source directory and untar the patch attachment you downloaded at the beginning:

```
cd linux-source <tab>
tar -xzvf ../clickpad.tar.gz
```

Now we'll patch the driver files, copy the Makefile to the right place, and compile and install the new driver:

```
patch -p1 <clickpad_patch
cp Makefile drivers/input/mouse/
cd drivers/input/mouse
make
sudo make install
```

Reboot your machine, and you'll find the touchpad works like it should. Note that this patch is based on Takashi Iwai's fine work here: [http://patchwork.kernel.org/patch/67335/](http://patchwork.kernel.org/patch/67335/)


hi all.
i'm owner of lenovo s10-3t, and after upgrading kernel to 2.6.34 from 2.6.33.3 i have same problem with my synaptics touchpad.
because Synaptics touchpad is Synaptics touchpad, even in Africa, i downloaded patch for kernel and tried to apply it.
there was a problem, it couldn't applay patch to synaptics.h (2nd hunk).
when i have opened the file, i saw that the line, that should be inserted is already there.

it's okay, so i typed make. i've got error about unknown symbol fsp_{init, detect}, so i had to add to Makefile line:
**psmouse-$(CONFIG_MOUSE_PS2_SENTELIC)	+= sentelic.o**
because these functions were defined in sentelic.h.

when i compiled module, i inserted it and... nothing new happened to me. touchpad buttons are not working.

ps i looked at 99-synaptics.rule for udev, tried it, but there was no effect. no effect at all.
only psmouse.modprobe worked for me, but, as it was said here, it is turning off right-hand vertical scrolling.

---

### Post by nykon on 2010-05-23
This thread attracted me to this forum. Can safely say the patch is effective on my HP Mini-210 running Backtrack 4 Final, and unlike other methods I have previously tried it retains its settings after reboot. An easy fix was to use a USB mouse, but can't always have that on me!
 
Many thanks to those involved in its production.

---

### Post by mpapamanz on 2010-05-24
In Lucid should be enough to APPEND to the file /usr/lib/X11/xorg.conf.d/10-synaptics.conf
the following code
```
Section "InputClass"
        Identifier "HP Mini 2010"
        MatchProduct "SynPS/2 Synaptics TouchPad"
        MatchDevicePath "/dev/input/event*"
        Driver "synaptics"
        Option "TapButton2" "3"
        Option "EmulateTwoFingerMinZ" "15"
        Option "EmulateTwoFingerMinW" "5"
        Option "JumpyCursorThreshold" "200"
        Option "VertTwoFingerScroll" "1"
        Option "HorizTwoFingerScroll" "1"
EndSection
```Please, leave untouched the previous lines of the file.
In my case it partially works: all the settings are applied except the {Vert,Horiz}TwoFingerScroll :(. It is strange since in the Xorg.0.log file it is written that the value is updated. According to me there is a gnome configuration that overwrites the value... but I haven't find it yet.
Maybe it is usefull to someone

---

### Post by Sisophon2001 on 2010-05-29
I created a script to set my touch pad settings, placed the script in my home directory (~/username/bin/myscripts/)and and then added the script to my start-up applications (System->Preferences->start up applications). I only set the JumpyCursorThreshold but you could add whatever preferences you like.

The script looks like this:

```
#!/bin/sh
synclient JumpyCursorThreshold=200
```

Settings are lost when you sleep and resume, so I added an icon to my favourites folder to run the script by hand if necessary.

I looked into calling the script automatically after resume, but the notification of resume comes too early, before user settings load, and I could not get it to work.

Garvan

---

### Post by John Baptist on 2010-06-27
Hi. I believe I've finally solved this problem. I've enclosed the solution in the attachment. Basically, it goes like this:

1. Copy the enclosed file as 11-touchpad.conf into this directory: /usr/lib/X11/xorg.conf.d/
2. In addition, it's also necessary to execute the following command:

gconftool-2 --set /desktop/gnome/peripherals/touchpad/scroll_method 2 --type int

You only need to run this command once; unless you play around with gnome-mouse-properties, the setting will be remembered until you change it. You need root privileges to copy the config file, but the gconftool-2 command should be run as your regular login user.

If you follow these steps, two-fingered scrolling and double-tap for right click will be enabled on your touchpad, even on non-multitouch hardware. It will work even after restart, hibernate, or suspend. If the responsiveness isn't exactly your liking, you can change the EmulateTwoFingerMinZ, EmulateTwoFingerMinW, and JumpyCursorThreshold settings in the file; the best value for these settings also depends on your hardware. The EmulateTwoFingerMinW is the most interesting; this is the minimum width of the touch that should be considered two-finger, and should thus activate scrolling. 

I've tested this on my HP Mini 210 running Lucid. I'd love to hear if this works for you, too.

---

### Post by Sisophon2001 on 2010-06-27
Hi,

Yes it works, and it solves the problem of settings being lost after suspend and resume. Thanks for sharing.

Garvan

---

### Post by Veector on 2010-06-27
I also was searching and found this site, i'm not sure what all of this mean but i think that it can help

---

### Post by MsKK on 2010-06-28
It didn't work for me. I copied the file to the folder and ran the command but the 2-figer scrolling wasnot available. 

I ran 

> 
gconftool -R /desktop/gnome/peripherals/touchpad


and it says "scroll_method = 2" but nothing changed.

---

### Post by Sisophon2001 on 2010-06-28
> **MsKK said:**
> It didn't work for me. I copied the file to the folder and ran the command but the 2-figer scrolling wasnot available. 

I ran 



and it says "scroll_method = 2" but nothing changed.

Some other things to check.

1. Make sure you remove the .txt extension from the download, and that it is in the correct directory.
2. Make sure tap_to_click = true

Garvan

---

### Post by MsKK on 2010-06-28
I just logged out and logged in again and now it is working... I'll see if it's still working when I restart but so far so good... Thanks!

---

### Post by John Baptist on 2010-06-28
Sorry, I forgot to mention that it's necessary to log out or restart for the changes to take effect.

---

### Post by trampgeek on 2010-07-03
Many thanks, John Baptist! Those instructions worked fine for me (HP Mini 210 + Ubuntu Lucid 10.04). I still prefer a mouse to a touchpad, but now at least I have a Netbook that's usable by itself whereas before I couldn't be bothered with it unless I had a mouse plugged in.

For the benefit of any other users as ignorant as I was of how a Synaptics-style touch pad should behave, I'll confess that I initially thought the fix hadn't worked, because the touchpad buttons didn't function as I expected and I couldn't figure out how to click-and-drag. I found this link very helpful: [http://manpages.ubuntu.com/manpages/intrepid/man4/synaptics.4.html](http://manpages.ubuntu.com/manpages/intrepid/man4/synaptics.4.html)

Thanks again for an invaluable posting.

---

### Post by MsKK on 2010-07-04
Well, it now works even after restarting. Thanks everyone, I'm going to mark this thread as solved. ;)

---

### Post by daathi on 2010-07-25
Hi!

Unfortunately I have not been able to get two finger scrolling, or any other special functions to work on my HP mini 210-1023 by following the instructions here. Could you please help me? I'm desperate to get at least two finger scrolling to work. I'm running Ubuntu 10.04.

I have done like John Babtist instructed:

[I]1. Copy the enclosed file as 11-touchpad.conf into this directory: /usr/lib/X11/xorg.conf.d/
2. In addition, it's also necessary to execute the following command:

gconftool-2 --set /desktop/gnome/peripherals/touchpad/scroll_method 2 --type int[/I] 
 
Rebooted, but it did not help, then I added this to 10-synaptics.conf:

Section "InputClass"
        Identifier "HP Mini 2010"
        MatchProduct "SynPS/2 Synaptics TouchPad"
        MatchDevicePath "/dev/input/event*"
        Driver "synaptics"
        Option "TapButton2" "3"
        Option "EmulateTwoFingerMinZ" "15"
        Option "EmulateTwoFingerMinW" "5"
        Option "JumpyCursorThreshold" "200"
        Option "VertTwoFingerScroll" "1"
        Option "HorizTwoFingerScroll" "1"


EndSection


Rebooted, nothing changed. Then I saw Sisophon2001 said:

[I]Some other things to check.

1. Make sure you remove the .txt extension from the download, and that it is in the correct directory.
2. Make sure tap_to_click = true[/I] 

But I can't find option 2 in any conf file.

Please help.


EDIT: *Couldn't find synaptics properties. No synaptics driver loaded?*  <- does this really mean the driver is not properly loaded? It should be installed...how can I get it loaded?

EDIT2: psmouse loaded first and overtook synaptics, I blacklisted psmouse and set rc.local to load psmouse, so now the loading order is reversed and I have synaptics in use. Can't get two finger scrolling to work yet, but perhaps it's easier to accomplish now that I have the driver working. I'll try it later.

---

### Post by IceDoE on 2010-08-05
Hey, John Baptists solution worked pretty well to make the touchpad more reliable and enable scrolling and such, but I have another problem with right clicking that some indicated earlier I think: I can't right click with my thumb. I believe this is a "to wide/large of pressure" feature or something, and people were mentioning this being an issue before. So while I can right click just fine using my index finger, if I try to tap it with my thumb nothing will happen. Is there a known way to fix this? Is it a setting somewhere that I can alter so that it will accept a large finger click?

---

### Post by fakbill on 2010-08-07
Ok it's a bit better with 
Section "InputClass"
        Identifier "HP Mini 2010"
        MatchProduct "SynPS/2 Synaptics TouchPad"
        MatchDevicePath "/dev/input/event*"
        Driver "synaptics"
        #Option "TapButton2" "3"
        #Option "EmulateTwoFingerMinZ" "15"
        #Option "EmulateTwoFingerMinW" "5"
        Option "JumpyCursorThreshold" "200"
        #Option "VertTwoFingerScroll" "1"
        #Option "HorizTwoFingerScroll" "1"
    Option "EmulateMidButtonTime" "100"
EndSection

but there is something very annoying : The mid button emulation does not work.
On linux I always use the mid clik to paste.
With a touchpad, I always use the two buttons at the same time to emulate the mid button.

When I try to emulate a mid click I only get a right clik.

I have no xorg.conf.

BTW,the bug is still there in 10.10 alpha3.

---

### Post by 12barz on 2010-08-13
Worked for me too on my HP dm4 with the new weird built-in-buttons clickpad.  But now I've lost edge-scrolling and my mouse settings in control panel don't have a touchpad tab for changing any settings.  Any ideas?  Running Lucid 64 bit.  Thanks.

---

### Post by badgoiko on 2010-08-15
> **John Baptist said:**
> Hi. I believe I've finally solved this problem. I've enclosed the solution in the attachment. Basically, it goes like this:

1. Copy the enclosed file as 11-touchpad.conf into this directory: /usr/lib/X11/xorg.conf.d/
2. In addition, it's also necessary to execute the following command:

gconftool-2 --set /desktop/gnome/peripherals/touchpad/scroll_method 2 --type int

You only need to run this command once; unless you play around with gnome-mouse-properties, the setting will be remembered until you change it. You need root privileges to copy the config file, but the gconftool-2 command should be run as your regular login user.

If you follow these steps, two-fingered scrolling and double-tap for right click will be enabled on your touchpad, even on non-multitouch hardware. It will work even after restart, hibernate, or suspend. If the responsiveness isn't exactly your liking, you can change the EmulateTwoFingerMinZ, EmulateTwoFingerMinW, and JumpyCursorThreshold settings in the file; the best value for these settings also depends on your hardware. The EmulateTwoFingerMinW is the most interesting; this is the minimum width of the touch that should be considered two-finger, and should thus activate scrolling. 

I've tested this on my HP Mini 210 running Lucid. I'd love to hear if this works for you, too.

Work. 10x

---

### Post by camorri on 2010-08-16
I'm glad I read this entire thread before proceeding. The fix worked on my HP 210 with Lucid. Could this be put into a HowTo? Or the Wiki ?

---

### Post by ljrmorgan on 2010-08-16
Sorry to be a pain, but could someone clarify what does and what doesn't work after doing this?

I've been running Lucid on my 210 exclusively for ages now, and have somehow managed to get used to the almost unusable touch pad, bit wary of mucking it up!

I figure multitouch doesn't work, how about two finger scrolling, the scrollbar at the side of the touch pad, the clickpad buttons etc?

Thanks for your help.

---

### Post by Sisophon2001 on 2010-08-17
Hi,

Many different configuration variables can come into play, but I believe that if you have an Ubuntu 10.4 version then the click buttons should already be working. Perhaps this may depend on the software settings you have selected for your mouse, but it works here. Keep in mind that many of the posts on this thread can be in the context of specific mouse settings, and thus might take some fiddling for you to get the same results as the poster.

However the click area defined in software does not match the markings on the click pad. The software defines the click area as half the height of the markings, and it divides it into three areas, each of equal width, left click, middle click and right click. I find I have to slide my finders along the bottom of the touch pad to activate the clicks, the area is really too small. I know how to change it in the kernel source code, but updating the kernel every time it changes is a pain.

Secondly the touch pad causes jumps when you accidentally touch it with a second finger, or part of your hand. This is easily fixed, and I strongly recomend you at least apply the

Option "JumpyCursorThreshold" "200"

option as described in 
[http://ubuntuforums.org/showpost.php?p=9516270&postcount=54]("http://ubuntuforums.org/showpost.php?p=9516270&postcount=54")
John Baptist's post, but selecting only this option and not any of the others.

If you want to try out the other options of two finger scrolling, or side scrolling, they all work, but in my opinion there are compromises that you must live with, and if you are used to the default, then I recomend only the JumpyCursorThreshold option.

You need to experiment carefully, and decide which settings work best for you.

Have fun,

Garvan

---

### Post by popk1d on 2010-08-22
Sisophon:
Thanks to this thread my (otherwise rather great) HP Mini210 is now useable in Linux, but the 'thinness' of the button area that you mention (ie. not matching up to the markings) is driving me crazy.

How would I make the changes to the kernel that you suggest? Can you point me to some resource that shows a step-by-step on how to do this? Or give me any clues?;)

Thanks for the support...

---

### Post by Sisophon2001 on 2010-08-22
> **popk1d said:**
> Sisophon:
Thanks to this thread my (otherwise rather great) HP Mini210 is now useable in Linux, but the 'thinness' of the button area that you mention (ie. not matching up to the markings) is driving me crazy.

How would I make the changes to the kernel that you suggest? Can you point me to some resource that shows a step-by-step on how to do this? Or give me any clues?;)

Thanks for the support...

Okay, I will try. I will modify jnetman1 post here: [http://ubuntuforums.org/showpost.php?p=8989185&postcount=11]("http://ubuntuforums.org/showpost.php?p=8989185&postcount=11")

Open the terminal on your Mini 210 and:
```
sudo apt-get install build-essential linux-source
```
The kernel source will be a tarball that is installed in /usr/src. Extract it to your home directory like so:

```
tar -xjvf /usr/src/linux-source <tab>
```
Note that pressing tab will auto-complete to the version you downloaded.

Open the file > ~/linux-source<tab>/drivers/input/mouse/synaptics.c in gedit or your favourite text editor

and search for the line

```
if (hw->y < YMIN_NOMINAL) {
```

and change it to

```
if (hw->y < YMIN_NOMINAL +800) {
```

Now you need to create a file called "Makefile" in the same folder as synaptics.c with this contents:

```
obj-m := psmouse.o

psmouse-objs := psmouse-base.o synaptics.o

psmouse-$(CONFIG_MOUSE_PS2_ALPS)        += alps.o
psmouse-$(CONFIG_MOUSE_PS2_ELANTECH)    += elantech.o
psmouse-$(CONFIG_MOUSE_PS2_OLPC)        += hgpk.o
psmouse-$(CONFIG_MOUSE_PS2_LOGIPS2PP)   += logips2pp.o
psmouse-$(CONFIG_MOUSE_PS2_LIFEBOOK)    += lifebook.o
psmouse-$(CONFIG_MOUSE_PS2_TRACKPOINT)  += trackpoint.o
psmouse-$(CONFIG_MOUSE_PS2_TOUCHKIT)    += touchkit_ps2.o
psmouse-$(CONFIG_MOUSE_PS2_SENTELIC)    += sentelic.o




KDIR := /lib/modules/$(shell uname -r)/build
PWD := $(shell pwd)
default:
	$(MAKE) -C $(KDIR) SUBDIRS=$(PWD) modules

install: 
	@cp psmouse.ko /lib/modules/$(shell uname -r)/kernel/drivers/input/mouse/

```


Then type 
```

cd linux-source <tab>
cd drivers/input/mouse
make
sudo make install
```

To build and install the new driver. 

Reboot your machine.

I realize editing source files is not ideal, so I hope somebody who knows how to automate these changes will help to create a patch file or a script to do this automatically. As I said before, I don't do this myself because it is too cumbersome to keep repeating it after every kernel update. If fact, the first time I ever did it was just before writing this post.

Garvan

---

### Post by John Baptist on 2010-08-22
@popk1d:

Yes, you could rebuild the driver as above or you could just set the parameter:

synclient AreaBottomEdge=x

where x is a number.

---

### Post by Sisophon2001 on 2010-08-23
> **John Baptist said:**
> @popk1d:

Yes, you could rebuild the driver as above or you could just set the parameter:

synclient AreaBottomEdge=x

where x is a number.

This does nothing in my tests. What value for x did you use?

I think the driver is buggy, but from internet search I know people are working on it, so I hope we will have a proper solutions soon.

Garvan

---

### Post by ryandavis33 on 2010-08-25
> **John Baptist said:**
> Hi. I believe I've finally solved this problem. I've enclosed the solution in the attachment. Basically, it goes like this:

1. Copy the enclosed file as 11-touchpad.conf into this directory: /usr/lib/X11/xorg.conf.d/
2. In addition, it's also necessary to execute the following command:

gconftool-2 --set /desktop/gnome/peripherals/touchpad/scroll_method 2 --type int

You only need to run this command once; unless you play around with gnome-mouse-properties, the setting will be remembered until you change it. You need root privileges to copy the config file, but the gconftool-2 command should be run as your regular login user.

If you follow these steps, two-fingered scrolling and double-tap for right click will be enabled on your touchpad, even on non-multitouch hardware. It will work even after restart, hibernate, or suspend. If the responsiveness isn't exactly your liking, you can change the EmulateTwoFingerMinZ, EmulateTwoFingerMinW, and JumpyCursorThreshold settings in the file; the best value for these settings also depends on your hardware. The EmulateTwoFingerMinW is the most interesting; this is the minimum width of the touch that should be considered two-finger, and should thus activate scrolling. 

I've tested this on my HP Mini 210 running Lucid. I'd love to hear if this works for you, too.
run that command in what? terminal?

---

### Post by Sisophon2001 on 2010-08-26
> **ryandavis33 said:**
> run that command in what? terminal?
Yes. 

The command
```
gconftool-2 --set /desktop/gnome/peripherals/touchpad/scroll_method 2 --type int
```

Is run in a terminal.

Garvan

---

### Post by daigorobr on 2010-08-30
Reading back the comments I couldn't get to a point of understanding how are things with Clickpad. I'm in Maverick and the proposed kernel patch doesn't "fit" in .35 kernel. Tried using some kernel found in the tubes but it didn't work wither (the cursor wouldn't move no matter how hard I cursed it).
I thought that, by this time, Clickpad and the new MultiTouch arch would work together as a charm. I was wrong.
bugs.launchpad.net has no comments after April or so, and then I am lost.
Can someone clarify what is going on?

---

### Post by ljrmorgan on 2010-08-30
> **daigorobr said:**
> Reading back the comments I couldn't get to a point of understanding how are things with Clickpad. I'm in Maverick and the proposed kernel patch doesn't "fit" in .35 kernel. Tried using some kernel found in the tubes but it didn't work wither (the cursor wouldn't move no matter how hard I cursed it).
I thought that, by this time, Clickpad and the new MultiTouch arch would work together as a charm. I was wrong.
bugs.launchpad.net has no comments after April or so, and then I am lost.
Can someone clarify what is going on?

Have you tried [this]("http://ubuntutesting.wordpress.com/2010/08/30/testing-your-multitouch-device/")?

I don't think the multitouch is supposed to work out the box in maverick (yet), you have to install a package first. I've just handed in my dissertation (yay!), so I thought I might try it out this week.

---

### Post by Tenzy on 2010-09-01
> **John Baptist said:**
> Hi. I believe I've finally solved this problem. I've enclosed the solution in the attachment. Basically, it goes like this:

1. Copy the enclosed file as 11-touchpad.conf into this directory: /usr/lib/X11/xorg.conf.d/
2. In addition, it's also necessary to execute the following command:

gconftool-2 --set /desktop/gnome/peripherals/touchpad/scroll_method 2 --type int

You only need to run this command once; unless you play around with gnome-mouse-properties, the setting will be remembered until you change it. You need root privileges to copy the config file, but the gconftool-2 command should be run as your regular login user.

If you follow these steps, two-fingered scrolling and double-tap for right click will be enabled on your touchpad, even on non-multitouch hardware. It will work even after restart, hibernate, or suspend. If the responsiveness isn't exactly your liking, you can change the EmulateTwoFingerMinZ, EmulateTwoFingerMinW, and JumpyCursorThreshold settings in the file; the best value for these settings also depends on your hardware. The EmulateTwoFingerMinW is the most interesting; this is the minimum width of the touch that should be considered two-finger, and should thus activate scrolling. 

I've tested this on my HP Mini 210 running Lucid. I'd love to hear if this works for you, too.


I have a HP mini 210 on order with the intention to install either Ubuntu Netbook, or linux Mint on it. When I get it I can still send it back as long as I leave the box unopened. 
I'm trying it figure out if I should or not because I don't plan on using an external mouse. 

You mention in your post that the setting will be remembered unless you play around with gnome-mouse-properties. I'm left handed. Does this still work if you put your mouse properties to left handed? Assuming that you change it to left handed  before you do the fix?

---

### Post by samfraser on 2010-09-06
This solution did not work for my new hp210-100, any suggestions,the mouse pad not working is making me have to use mswindows!  This is the output from make

oh gee the select text copy and paste from the terminal doesn't past all of the text, great! What else doesn't work !?!
:cry::cry:

---

### Post by kelchm on 2010-09-06
Justa note, 

/usr/lib/X11/xorg.conf.d/ seems to have moved to /usr/share/X11/xorg.conf.d/ in 10.10.

Also, has anyone found a way to have both tap to click as well as the physical left and right click working properly?

---

### Post by Sisophon2001 on 2010-09-07
> **samfraser said:**
> This solution did not work for my new hp210-100, any suggestions,the mouse pad not working is making me have to use mswindows!  This is the output from make

oh gee the select text copy and paste from the terminal doesn't past all of the text, great! What else doesn't work !?!
:cry::cry:

This thread is old, and many people have suggested different solutions, all of which worked to different extents, so when you say "this Solution" you should refer back to the instructions you followed, and you also need to state which version of UNR or Ununtu you are running.

And no crying! :)

Garvan

---

### Post by Sisophon2001 on 2010-09-07
> **kelchm said:**
> Justa note, 

/usr/lib/X11/xorg.conf.d/ seems to have moved to /usr/share/X11/xorg.conf.d/ in 10.10.

Also, has anyone found a way to have both tap to click as well as the physical left and right click working properly?

I was not able to get both tap and buttons working together to my satisfaction, but for me the action of the "fist-generation" mouse-pad is buried in my muscle memory so I am happy enough to work without taps or special features, and I did not spend a long time trying to get them working.

Garvan

---

### Post by Sisophon2001 on 2010-09-07
> **Tenzy said:**
> I have a HP mini 210 on order with the intention to install either Ubuntu Netbook, or linux Mint on it. When I get it I can still send it back as long as I leave the box unopened. 
I'm trying it figure out if I should or not because I don't plan on using an external mouse. 

You mention in your post that the setting will be remembered unless you play around with gnome-mouse-properties. I'm left handed. Does this still work if you put your mouse properties to left handed? Assuming that you change it to left handed  before you do the fix?

The mouse works perfectly for my needs, and it works left or right handed, but it does take a lot of work to set it up correctly, even to the point of recompiling the driver in my case.

Garvan

---

### Post by bigbrovar on 2010-09-07
> **jnetman1 said:**
> You're much better off actually fixing the problem with the driver, as telling the system that the touchpad is a PS/2 mouse leaves you with zero control of the pad on the Mini 210. To do this, download the attachment at the bottom of this post and save it in your home folder:

Open the terminal on your Mini 210 and

```
sudo apt-get install build-essential patch linux-source
```

The kernel source will be a tarball that is installed in /usr/src. Extract it to your home directory like so:

```
tar -xjvf /usr/src/linux-source <tab>
``` 

Note that pressing tab will autocomplete to the version you downloaded. Once extracted, change to the source directory and untar the patch attachment you downloaded at the beginning:

```
cd linux-source <tab>
tar -xzvf ../clickpad.tar.gz
```

Now we'll patch the driver files, copy the Makefile to the right place, and compile and install the new driver:

```
patch -p1 <clickpad_patch
cp Makefile drivers/input/mouse/
cd drivers/input/mouse
make
sudo make install
```

Reboot your machine, and you'll find the touchpad works like it should. Note that this patch is based on Takashi Iwai's fine work here: [http://patchwork.kernel.org/patch/67335/](http://patchwork.kernel.org/patch/67335/)
Anyone tried this patch on Ubuntu 10.10? does it work?

---

### Post by daigorobr on 2010-09-07
No, it doesn't work with 10.10, unfortunately.

---

### Post by daigorobr on 2010-09-07
> **ljrmorgan said:**
> Have you tried [this]("http://ubuntutesting.wordpress.com/2010/08/30/testing-your-multitouch-device/")?

I don't think the multitouch is supposed to work out the box in maverick (yet), you have to install a package first. I've just handed in my dissertation (yay!), so I thought I might try it out this week.

I didn't really expect it to work OOTB... What I am saying is that it is a shame that we have this multitouch device apparently supported in kernel that can't be tested (through the link you sent) because of recognition issues.
It's so close and so far at the same point and it's frustrating...

---

### Post by Tenzy on 2010-09-07
> **Sisophon2001 said:**
> The mouse works perfectly for my needs, and it works left or right handed, but it does take a lot of work to set it up correctly, even to the point of recompiling the driver in my case.

Garvan
Thanks for your answer. I'm new to Ubuntu so I think I'll look for a netbook that has no troubles or ones that even a newbie can fix. Otherwise I'm stuck with windows and that's no way to learn linux. ;)

---

### Post by bigbrovar on 2010-09-08
> **daigorobr said:**
> No, it doesn't work with 10.10, unfortunately.

Thanks, at times like this I really miss the thanks button. any idea if it works on 10.04?

---

### Post by Sisophon2001 on 2010-09-08
> **bigbrovar said:**
> Anyone tried this patch on Ubuntu 10.10? does it work?

This was written for 9.10, and most of the code was included in the official 10.04 release, so the instructions no longer work with 10.04. Unfortunately for us HP Mini 210 users they did not include a "Hack" to adjust the height of the click buttons to match the marking on the HP Mini 210.

In my post here [http://ubuntuforums.org/showpost.php?p=9750332&postcount=72](http://ubuntuforums.org/showpost.php?p=9750332&postcount=72)

I show how to apply this "Hack" to 10.04. 

I know work is still being done on improving this driver, so I expect future versions will not require this hack. But we have to wait for the next release of Ubuntu to see if the new code is approved.

I think my modification/hack is essential for users who prefer separate click buttons.

Users (of 10.04) who prefer the more modern tapping and scrolling action of a mouse pad should follow the instructions in this post [http://ubuntuforums.org/showpost.php?p=9516270&postcount=54](http://ubuntuforums.org/showpost.php?p=9516270&postcount=54)

I use a combination of both to get the mouse to work exactly as I want.

Have fun,

Garvan

---

### Post by daigorobr on 2010-09-08
> **bigbrovar said:**
> Thanks, at times like this I really miss the thanks button. any idea if it works on 10.04?

Every time I used a 10.04-based system (Mint, Ubuntu, UNR) in my 210, it worked OOTB. The only catch is that the height of the button area is smaller than it should, but our frend up there has the hack for it.

---

### Post by samfraser on 2010-09-12
None of those worked for me either.  I've got a hp 210-1000, this is the output from the terminal when i tried the source code edit option, i'm using ubuntu 10.04 64bit:-

samfraser@samfraser-laptop:~$ sudo apt-get install build-essential linux-source

Reading package lists... Done
Building dependency tree       
Reading state information... Done
build-essential is already the newest version.
linux-source is already the newest version.
The following packages were automatically installed and are no longer required:
  linux-headers-2.6.32-21-generic linux-headers-2.6.32-21
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 10 not upgraded.

samfraser@samfraser-laptop:~$ gedit linux-source-2.6.32/drivers/input/mouse/synaptics.c

samfraser@samfraser-laptop:~$ gedit linux-source-2.6.32/drivers/input/mouse/makefile

samfraser@samfraser-laptop:~$ mv linux-source-2.6.32/drivers/input/mouse/makefile linux-source-2.6.32/drivers/input/mouse/Makefile
samfraser@samfraser-laptop:~$ 

samfraser@samfraser-laptop:~$ cat linux-source-2.6.32/drivers/input/mouse/Makefile


obj-m := psmouse.o

psmouse-objs := psmouse-base.o synaptics.o

psmouse-$(CONFIG_MOUSE_PS2_ALPS)        += alps.o
psmouse-$(CONFIG_MOUSE_PS2_ELANTECH)    += elantech.o
psmouse-$(CONFIG_MOUSE_PS2_OLPC)        += hgpk.o
psmouse-$(CONFIG_MOUSE_PS2_LOGIPS2PP)   += logips2pp.o
psmouse-$(CONFIG_MOUSE_PS2_LIFEBOOK)    += lifebook.o
psmouse-$(CONFIG_MOUSE_PS2_TRACKPOINT)  += trackpoint.o
psmouse-$(CONFIG_MOUSE_PS2_TOUCHKIT)    += touchkit_ps2.o
psmouse-$(CONFIG_MOUSE_PS2_SENTELIC)    += sentelic.o




KDIR := /lib/modules/$(shell uname -r)/build
PWD := $(shell pwd)
default:
	$(MAKE) -C $(KDIR) SUBDIRS=$(PWD) modules

install: 
	@cp psmouse.ko /lib/modules/$(shell uname -r)/kernel/drivers/input/mouse


samfraser@samfraser-laptop:~$ cd linux-source-2.6.32/

samfraser@samfraser-laptop:~/linux-source-2.6.32$ cd drivers/input/mouse
samfraser@samfraser-laptop:~/linux-source-2.6.32

samfraser@samfraser-laptop:~/linux-source-2.6.32/drivers/input/mouse$ make

make -C /lib/modules/2.6.32-24-generic/build SUBDIRS=/home/samfraser/linux-source-2.6.32/drivers/input/mouse modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.32-24-generic'
  CC [M]  /home/samfraser/linux-source-2.6.32/drivers/input/mouse/synaptics.o
/home/samfraser/linux-source-2.6.32/drivers/input/mouse/synaptics.c: In function &#8216;clickpad_process_packet&#8217;:
/home/samfraser/linux-source-2.6.32/drivers/input/mouse/synaptics.c:344: warning: statement with no effect
/home/samfraser/linux-source-2.6.32/drivers/input/mouse/synaptics.c:344: error: expected &#8216;;&#8217; before &#8216;{&#8217; token
/home/samfraser/linux-source-2.6.32/drivers/input/mouse/synaptics.c: At top level:
/home/samfraser/linux-source-2.6.32/drivers/input/mouse/synaptics.c:377: error: redefinition of &#8216;clickpad_process_packet&#8217;
/home/samfraser/linux-source-2.6.32/drivers/input/mouse/synaptics.c:338: note: previous definition of &#8216;clickpad_process_packet&#8217; was here
/home/samfraser/linux-source-2.6.32/drivers/input/mouse/synaptics.c: In function &#8216;clickpad_process_packet&#8217;:
/home/samfraser/linux-source-2.6.32/drivers/input/mouse/synaptics.c:400: error: &#8216;struct synaptics_data&#8217; has no member named &#8216;prev_hw&#8217;
/home/samfraser/linux-source-2.6.32/drivers/input/mouse/synaptics.c:401: error: &#8216;struct synaptics_data&#8217; has no member named &#8216;prev_hw&#8217;
/home/samfraser/linux-source-2.6.32/drivers/input/mouse/synaptics.c:402: error: &#8216;struct synaptics_data&#8217; has no member named &#8216;prev_hw&#8217;
/home/samfraser/linux-source-2.6.32/drivers/input/mouse/synaptics.c:404: error: &#8216;struct synaptics_data&#8217; has no member named &#8216;prev_hw&#8217;
/home/samfraser/linux-source-2.6.32/drivers/input/mouse/synaptics.c: At top level:
/home/samfraser/linux-source-2.6.32/drivers/input/mouse/synaptics.c:416: error: redefinition of &#8216;clickpad_process_packet&#8217;
/home/samfraser/linux-source-2.6.32/drivers/input/mouse/synaptics.c:377: note: previous definition of &#8216;clickpad_process_packet&#8217; was here
/home/samfraser/linux-source-2.6.32/drivers/input/mouse/synaptics.c: In function &#8216;clickpad_process_packet&#8217;:
/home/samfraser/linux-source-2.6.32/drivers/input/mouse/synaptics.c:439: error: &#8216;struct synaptics_data&#8217; has no member named &#8216;prev_hw&#8217;
/home/samfraser/linux-source-2.6.32/drivers/input/mouse/synaptics.c:440: error: &#8216;struct synaptics_data&#8217; has no member named &#8216;prev_hw&#8217;
/home/samfraser/linux-source-2.6.32/drivers/input/mouse/synaptics.c:441: error: &#8216;struct synaptics_data&#8217; has no member named &#8216;prev_hw&#8217;
/home/samfraser/linux-source-2.6.32/drivers/input/mouse/synaptics.c:443: error: &#8216;struct synaptics_data&#8217; has no member named &#8216;prev_hw&#8217;
/home/samfraser/linux-source-2.6.32/drivers/input/mouse/synaptics.c: At top level:
/home/samfraser/linux-source-2.6.32/drivers/input/mouse/synaptics.c:455: error: redefinition of &#8216;clickpad_process_packet&#8217;
/home/samfraser/linux-source-2.6.32/drivers/input/mouse/synaptics.c:416: note: previous definition of &#8216;clickpad_process_packet&#8217; was here
/home/samfraser/linux-source-2.6.32/drivers/input/mouse/synaptics.c: In function &#8216;clickpad_process_packet&#8217;:
/home/samfraser/linux-source-2.6.32/drivers/input/mouse/synaptics.c:478: error: &#8216;struct synaptics_data&#8217; has no member named &#8216;prev_hw&#8217;
/home/samfraser/linux-source-2.6.32/drivers/input/mouse/synaptics.c:479: error: &#8216;struct synaptics_data&#8217; has no member named &#8216;prev_hw&#8217;
/home/samfraser/linux-source-2.6.32/drivers/input/mouse/synaptics.c:480: error: &#8216;struct synaptics_data&#8217; has no member named &#8216;prev_hw&#8217;
/home/samfraser/linux-source-2.6.32/drivers/input/mouse/synaptics.c:482: error: &#8216;struct synaptics_data&#8217; has no member named &#8216;prev_hw&#8217;
/home/samfraser/linux-source-2.6.32/drivers/input/mouse/synaptics.c: In function &#8216;synaptics_process_packet&#8217;:
/home/samfraser/linux-source-2.6.32/drivers/input/mouse/synaptics.c:565: error: implicit declaration of function &#8216;SYN_CAP_CLICKPAD&#8217;
make[2]: *** [/home/samfraser/linux-source-2.6.32/drivers/input/mouse/synaptics.o] Error 1
make[1]: *** [_module_/home/samfraser/linux-source-2.6.32/drivers/input/mouse] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.32-24-generic'
make: *** [default] Error 2

---

### Post by Sisophon2001 on 2010-09-15
Hi samfraser,

You said you are using 64bit, but you have a hp 210-1000? Is this correct? If you have the exact same version as me (32bit) then I could just send you the compiled module to test.


Even though our kernel versions are the same, the line numbers in your error messages do not appear to correspond to the line numbers in my source files. I suspect you have a typing error in your source code, but in addition to this there may be other errors.

I suggest you send me your entire > /home/samfraser/linux-source-2.6.32/drivers/input/mouse directory as a zip file so I can see exactly what the source code looks like.

In the meantime, I suggest you try following John Baptist's post again [http://ubuntuforums.org/showpost.php?p=9516270&postcount=54]("http://ubuntuforums.org/showpost.php?p=9516270&postcount=54")
If you can get this to work, it may be all you need.

Garvan

---

### Post by Oleksa Stasevych on 2010-09-18
Guys, can sombeody overcome this issue on Maverick?...

---

### Post by ljrmorgan on 2010-09-18
I haven't had any luck with it. I don't know where the problem lies - is the relevant patch in the kernel? If so, is it just that the device isn't recognised properly? Has the relevant patch to X been applied?

I haven't mucked around with kernels before, so I don't know where to start.

---

### Post by masterblah777 on 2010-09-18
> **pauljwells said:**
> Lucid uses the udev architecture for input device control, apparently :-S

I found this on the Debian Wiki:

[http://wiki.debian.org/SynapticsTouchpad]("http://wiki.debian.org/SynapticsTouchpad")



You have to delete the psmouse.modprobe file from /etc/modprobe.d/ if you used the psmouse kludge before, then create the 99-synaptics.rules file and fill in the above text and reboot. For me it got left and right mouse clicks working and also right hand edge scrolling, nice!

There is a whole section in the Ubuntu docs about setting this up here:

[http://manpages.ubuntu.com/manpages/karmic/man4/synaptics.4.html]("http://manpages.ubuntu.com/manpages/karmic/man4/synaptics.4.html")

Maybe we can have a play around and improve on the Debian file?

After following these instructions I was able to get the vertical scrolling working on my HP mini 311 with alps touch pad. I am unable to use 2-finger-scrolling however.

---

### Post by slycooper on 2010-09-30
> **MsKK said:**
> THANK YOU!!!! This was just what I was looking for. It worked!! If someone figures out how to make this permanent (without having to execute everytime one reboots) I will change the status of the thread as solved.
Not working for ubuntu 10.04.
:~$ synclient TapButton2=3 HorizTwoFingerScroll=1 VertTwoFingerScroll=1 EmulateTwoFingerMinZ=29 EmulateTwoFingerMinW=5 JumpyCursorThreshold=200
Couldn't find synaptics properties. No synaptics driver loaded? 
Instructions on Page 1 fixed normal working of my touchpad. Scrolling/Multitouch is not working.

---

### Post by ACol on 2010-10-04
__[http://ubuntuforums.org/showpost.php...0&postcount=54]("http://ubuntuforums.org/showpost.php?p=9516270&postcount=54")
John Baptist's instructions as per that post do not work for me on my pavilion dm3, which uses a similar trackpad and encounters similar problems.

I am running 10.10 and out of the box the touchpad exhibits the same erratic behavior described by users running 9.10 and under.

The psmouse hack from the first page or so of this thread will make right click work again but not everything else.

If anyone else is running 10.10 and has a solution to get the touchpad working as it does under windows it would be much appreciated.

---

### Post by ACol on 2010-10-04
note: I moved the file minus the .txt to /usr/share/X11/xorg.conf.d as this is where the relevant directory is in 10.10.

---

### Post by mapkar on 2010-10-04
> **Sabot said:**
> To get the trackpad working correctly you need to use the terminal and enter in the below commands. Make sure you press enter after each command:

    ```
sudo su
```    ```
echo options psmouse proto=exps > /etc/modprobe.d/psmouse.modprobe
```    ```
reboot
```
Once the computer reboots your trackpad will be able to do left click and drag and right clicking.

how can this be undone?

---

### Post by tgm4883 on 2010-10-04
> **mapkar said:**
> how can this be undone?

I stress that you should figure out what commands do before blindly copying and pasting them onto your system. You can do real damage that way. Reverting that command is really easy if you know what that command you ran did.

---

### Post by mapkar on 2010-10-04
to #101

That's why I asked, I'm aware that it can damage important stuff. The click_patch posted on page two fails to work at the final step where the "make" and "make" install commands are listed, it fails like this:

```

chris@Free-Cookies-Net:~/linux-source-2.6.32$ make
make -C /lib/modules/2.6.32-21-generic/build SUBDIRS=/home/chris/linux-source-2.6.32 modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.32-21-generic'
  CC      kernel/bounds.s
/home/chris/linux-source-2.6.32/kernel/bounds.c:1: fatal error: can’t open kernel/bounds.s for writing: Permission denied
compilation terminated.
make[2]: *** [kernel/bounds.s] Error 1
make[1]: *** [_module_/home/chris/linux-source-2.6.32] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.32-21-generic'
make: *** [default] Error 2
chris@Free-Cookies-Net:~/linux-source-2.6.32$ 

```I don't really understand the problem, I followed the other directions to the letter...

---

### Post by ericbarch on 2010-10-10
To anyone stuck trying to get right click working in 10.10, here is what I did. The xorg.conf.d folder changed locations in 10.10 so I created the file:

/usr/share/X11/xorg.conf.d/11-touchpad.conf

I then copied this into the file, saved, and restarted:

```
Section "InputClass"
	Identifier "touchpad catchall"
	MatchProduct "SynPS/2 Synaptics TouchPad"
	MatchIsTouchpad "on"
	Driver "synaptics"
	Option "JumpyCursorThreshold"  "200"
	Option "EmulateTwoFingerMinZ"  "20"
	Option "EmulateTwoFingerMinW"  "5"
	Option "TapButton2" "3"
	Option "PalmDetect" "on"
EndSection
```

I'm not a huge fan of two finger scrolling and the multi-touch never seems to work quite how I like it, so I used the file above to enable two finger tapping to right click. I then went into the Mouse menu item under System >> Preferences >> Touchpad and selected edge scrolling. Smooth sailing under 10.10 now with right click and edge scrolling! :P

---

### Post by monkeysinacan on 2010-10-11
Sigh... I was really hoping this would be sorted out in 10.10 since this is such a popular netbook.

---

### Post by Jakiejake on 2010-10-11
> **monkeysinacan said:**
> Sigh... I was really hoping this would be sorted out in 10.10 since this is such a popular netbook.

Same, well kind of
I just installed Ubuntu 10.10 Netbook on my HP Mini 210 (I'm typing this on it) and am trying to get it to work!
I'm using a mouse since the trackpad is horrible in Ubuntu 10.10

---

### Post by toejam316 on 2010-10-11
I'm not going to dive into this all and mess around, because I'm still adjusting to Ubuntu after running XP and Vista and 7 for a long time on my desktop, so anyone got a simple way to re-enable Multi-touch scrolling and right clicking (preferably within the boundaries of the respective markings for right and left clicking on the trackpad) on the Mini 210?

I'm getting a bit sick of having to press a physical keyboard button to open the right click menu :P

---

### Post by monkeysinacan on 2010-10-11
Whew! I got two finger scrolling and two-finger tap for right-click working in 10.10!

Put the "11-touchpad.conf" file found on page 6 of this thread in to **/usr/share/X11/xorg.conf.d/** (while running as root) 

Then while running under your normal account execute
```
gconftool-2 --set /desktop/gnome/peripherals/touchpad/scroll_method 2 --type int
```
in the terminal as mentioned by John Baptist on page 6

I now have "mostly" everything working the way it used to under 10.04
ie: The physical right click button is no longer working. Which isn't the end of the world, but I have found instances where the physical button was useful.

I hope this helps :)

---

### Post by monkeysinacan on 2010-10-15
And now the physical right click is magically working. Go figure.

---

### Post by tgm4883 on 2010-10-15
> **monkeysinacan said:**
> And now the physical right click is magically working. Go figure.

Do you have any extra repositories/PPAs?

---

### Post by zachin2036 on 2010-10-16
Right click worked for my netbook in 10.04...but no dice in 10.10.  Will try the "page 6 solution"....I'm nervous :(

---

### Post by zachin2036 on 2010-10-16
[post deleted by author]

---

### Post by zachin2036 on 2010-10-17
> **ericbarch said:**
> To anyone stuck trying to get right click working in 10.10, here is what I did. The xorg.conf.d folder changed locations in 10.10 so I created the file:

/usr/share/X11/xorg.conf.d/11-touchpad.conf

I then copied this into the file, saved, and restarted:

```
Section "InputClass"
    Identifier "touchpad catchall"
    MatchProduct "SynPS/2 Synaptics TouchPad"
    MatchIsTouchpad "on"
    Driver "synaptics"
    Option "JumpyCursorThreshold"  "200"
    Option "EmulateTwoFingerMinZ"  "20"
    Option "EmulateTwoFingerMinW"  "5"
    Option "TapButton2" "3"
    Option "PalmDetect" "on"
EndSection
```I'm not a huge fan of two finger scrolling and the multi-touch never seems to work quite how I like it, so I used the file above to enable two finger tapping to right click. I then went into the Mouse menu item under System >> Preferences >> Touchpad and selected edge scrolling. Smooth sailing under 10.10 now with right click and edge scrolling! :P

Thanks for this solution - and for those having problems copying the file, you'll have to make this file in your Documents folder (for example), then open a terminal, "cd Documents" and do a 
```
sudo cp 11-touchpad.conf /usr/share/X11/xorg.conf.d/
```

So...that being said - I don't have right-click still.  But I do have a double-finger-tap that works as right-click, so it's not 100% bad.  Does anyone know if we can mess around with those above variables to get right click back?  I would think that "TapButton2" would be the right click - so I changed it from 3 to 2....no change as far as I can tell.  Any ideas?

---

### Post by Vincentbernard on 2010-10-18
Hi !

I'm new to Ubuntu community and I really love the Ubuntu OS for netbooks. I've install it on my HP mini 100 and it works like a charm. My best friend wanted to have it, so I did install it on his HP mini 210. But then, no right click.

I'm a newbie to Linux systems and i'm not very good in english... Is this problem solved ? I mean, I saw the solution at page 6 but will it make my right click work ? I don't really care about multi-finger stuff... and i really don't want to go back to Windows 7 scrappy netbook version.

---

### Post by JacobAppleGeek on 2010-10-21
Hi,

I just installed 10.10 and the path you specified doesn't exist and I can't create a folder. Any thoughts? 

Thanks!

---

### Post by Blue DaNoob on 2010-10-23
Thanks John Baptist! Worked great on my HP Mini 210. The trackpad was always troublesome and sporadic for me... two finger scroll, two finger tap, and the hard left/right clicks all work. It's no longer a pain when I forget my wireless mouse.

---

### Post by cyberkilla on 2010-10-27
Will there be an update to Maverick that resolves this issue? :)

I hope so, because, as a few people have mentioned, the HP Mini computers very popular; and clickpads have been out for over a year now, that I know of.

I bought one a couple of months ago. I really don't expect Ubuntu to be flawless out-of-the-box, but until the touchpad is fixed, I don't think it's worth the hassle to install.

The moment its fixed, I'll be on board. :P

---

### Post by davbren on 2010-10-28
Anybody had this working with Envy 13?

---

### Post by VideoRoy on 2010-10-28
I just wanted to say a big THANKS for this thread.  I have the HP Mini 2102 which is the business version of the 210 and the touchpad was causing me headaches with MM 10.10.

Still no right click but the config file in post #54 works great.  I can now click and drag and while 2 finger click is not natural for me it works.

Awesome support folks.:cool:

---

### Post by andyeyre on 2010-10-30
Hey All

Just to clarify, there are two issues with the HP 210 Synaptics clickpad here:

1. the driver fails to recognize that it's a multitouch pad, and only ever reports 1 finger;
2. the driver fails to accommodate the "virtual" right-click that one  expects when clicking the pad with a finger over the right button  region.

I don't have time to do anything about (1) now, but I've created a .deb  for a modified version of the synaptics driver that fixes (2).  Unfortunately, since I did this in a rush this afternoon in order to get  my new laptop working how I like it, it's not a very neat solution -  I've hard-coded a right click if the pad is clicked with the finger in  the right-half and bottom-5th of the pad.

I did this because I personally don't like tap-to-click and I didn't find the previous workarounds as acceptable.

Problems with my patch:
1. the behaviour is hard-coded --- not good --- however, I have very  little time and probably won't be able to get it to read from the config  variables as it should.
2. understand that my modifications will produce strange results if you  attempt to tap-to-click with finger(s) in the right-click region, or if  you attempt to left-click-drag and you happen to stray into the  right-click region.

You can download my .deb from:
[http://sites.google.com/site/andyeyr...edirects=0&d=1]("http://sites.google.com/site/andyeyre/files/xserver-xorg-input-synaptics_1.2.2-2ubuntu5eyre1_i386.deb?attredirects=0&d=1")

Checksum: 8c01c181a5ac95dbfca347a01581f6d1  xserver-xorg-input-synaptics_1.2.2-2ubuntu5eyre1_i386.deb

thanks,
andy

---

### Post by VideoRoy on 2010-10-30
> **andyeyre said:**
> Hey All

Just to clarify, there are two issues with the HP 210 Synaptics clickpad here:

1. the driver fails to recognize that it's a multitouch pad, and only ever reports 1 finger;
2. the driver fails to accommodate the "virtual" right-click that one  expects when clicking the pad with a finger over the right button  region.

I don't have time to do anything about (1) now, but I've created a .deb  for a modified version of the synaptics driver that fixes (2).  Unfortunately, since I did this in a rush this afternoon in order to get  my new laptop working how I like it, it's not a very neat solution -  I've hard-coded a right click if the pad is clicked with the finger in  the right-half and bottom-5th of the pad.

I did this because I personally don't like tap-to-click and I didn't find the previous workarounds as acceptable.

Problems with my patch:
1. the behaviour is hard-coded --- not good --- however, I have very  little time and probably won't be able to get it to read from the config  variables as it should.
2. understand that my modifications will produce strange results if you  attempt to tap-to-click with finger(s) in the right-click region, or if  you attempt to left-click-drag and you happen to stray into the  right-click region.

You can download my .deb from:
[http://sites.google.com/site/andyeyr...edirects=0&d=1]("http://sites.google.com/site/andyeyre/files/xserver-xorg-input-synaptics_1.2.2-2ubuntu5eyre1_i386.deb?attredirects=0&d=1")

Checksum: 8c01c181a5ac95dbfca347a01581f6d1  xserver-xorg-input-synaptics_1.2.2-2ubuntu5eyre1_i386.deb

thanks,
andy
Andy,
Thanks I will give this a try for my 2102 which is the same hardware.  This has continued to bother me as well and I keep screwing up with the 2 finger tap.

I have a different work around that I will offer up but I am still going to try your fix.  Below is my take at the 11-touchpad.conf that was originally posted in #54 of this thread:

> Section "InputClass"
    Identifier "touchpad catchall"
    MatchProduct "SynPS/2 Synaptics TouchPad"
    MatchIsTouchpad "on"
    Driver "synaptics"
    Option "JumpyCursorThreshold"  "200"
    Option "EmulateTwoFingerMinZ"  "20"
    Option "EmulateTwoFingerMinW"  "5"
    Option "TapButton2" "3"
    Option "PalmDetect" "1"
    Option "PalmMinWidth" "20"
    Option "LockedDrags" "1"
    Option "AccelFactor" ".01"
    Option "MaxSpeed" "1.0"
    Option "RBCornerButton" "3" 
EndSection

The things I added where some fixes to the pointer speed from the default so it behaves more like when I dual boot into Win 7 but the interesting option is the last one "RBCornerButton".  With this option if you single tap the very lower right part of the pad / button it will emulate a right click.

Note: You have to tap the extreme lower right corner.

Maybe this will help someone.

---

### Post by VideoRoy on 2010-10-30
Andy,
So far this is awesome!  Combined with my pointer speed changes the touchpad is down right useable now :P.  This is about my last hardware problem I needed to get fixed.

I am assuming if there is a update from Ubuntu repsoitories then this fix will be overwritten?

Very much appreciated!!!

---

### Post by tgm4883 on 2010-10-30
> **VideoRoy said:**
> Andy,
So far this is awesome!  Combined with my pointer speed changes the touchpad is down right useable now :P.  This is about my last hardware problem I needed to get fixed.

I am assuming if there is a update from Ubuntu repsoitories then this fix will be overwritten?

Very much appreciated!!!

That would depend on the version numbering. I would hope that Andy would post the source code of his changes, that way someone else might A) Fix it so the values aren't hardcoded, and/or B) get the fixes into the official repos.

---

### Post by andyeyre on 2010-10-31
> **tgm4883 said:**
> That would depend on the version numbering. I would hope that Andy would post the source code of his changes, that way someone else might A) Fix it so the values aren't hardcoded, and/or B) get the fixes into the official repos.

Hi. I've posted the source on [http://sites.google.com/site/andyeyre/files](http://sites.google.com/site/andyeyre/files). The patch is only a couple of lines, (if a click & if in the right-click zone, right-click instead of left). The big problem would be automatically IDing clickpads, but I suppose it could be left to the user to set an option in these circumstances.

I might get around to it & if so I will submit a patch to the maintainer, but I also want to fix the battery meter which isn't working properly for my laptop either.

In answer to a prev. question, I've given my .deb a derivative version number (1.2.2-2ubuntu5eyre1) instead of (1.2.2-2ubuntu5). The package manager will consider it newer than 2ubuntu5, but older than 2ubuntu6 or 1.2.3-anything. So it *will* get overwritten when an update comes out, unless you lock the version of the package to 2ubuntu5eyre1. You can do that by going to Synaptic Package Manager, search for "synaptics" in the search box, select the xserver-xorg-input-synaptics package, and click on Package Menu -> Lock Version.

andy

---

### Post by andyeyre on 2010-10-31
> **VideoRoy said:**
> Andy,
Thanks I will give this a try for my 2102 which is the same hardware.  This has continued to bother me as well and I keep screwing up with the 2 finger tap.

I have a different work around that I will offer up but I am still going to try your fix.  Below is my take at the 11-touchpad.conf that was originally posted in #54 of this thread:



The things I added where some fixes to the pointer speed from the default so it behaves more like when I dual boot into Win 7 but the interesting option is the last one "RBCornerButton".  With this option if you single tap the very lower right part of the pad / button it will emulate a right click.

Note: You have to tap the extreme lower right corner.

Maybe this will help someone.

I should point out that Roy's "Option" "JumpyCursorThreshold" "200" is pretty much necessary to make the clickpad usable (it will do strange things if you so much as think about putting a second finger anywhere near it, without this option set or something similar). It should have been included in the .deb but it wasn't, so you'll each have to make this change by hand, until I build another version.

---

### Post by VideoRoy on 2010-10-31
> **andyeyre said:**
> I should point out that Roy's "Option" "JumpyCursorThreshold" "200" is pretty much necessary to make the clickpad usable (it will do strange things if you so much as think about putting a second finger anywhere near it, without this option set or something similar). It should have been included in the .deb but it wasn't, so you'll each have to make this change by hand, until I build another version.
Yeah, someone else mentioned this and it was the only way to get it somewhat stable.  I tried a bunch of values but keep going back to 200.

 The only problems I have left with touchpad after Andy's fix is Left click and drag or highlight text.  Still unuseable since it looks like the driver is confused over 2 fingers.  I know it is possible because it works on the Windows side.  Also I have not found the magic on the palm detect since it keeps taking that as a click but to be fair I have that problem in Windows and have never been able to fine tune it.

Off topic:
Same problem here on the battery of course but my work around there is right click battery icon ---> click "Laptop Battery (estimating)" ---> Details tab and scroll down.  Percentage is near the bottom.  Not great, but it works for now.  The battery graphic is pretty accurate for my 6 cell battery though.

---

### Post by VideoRoy on 2010-10-31
Sorry to keep updating but I think I fixed the click drag / highlight problem.

After applying Andy's patch I commented out these 2 lines from the original fix:

    #Option "EmulateTwoFingerMinZ"  "20"
    #Option "EmulateTwoFingerMinW"  "5"

then checking synclient after a reboot the values went back to their defaults of:

    EmulateTwoFingerMinZ"  = 280
    EmulateTwoFingerMinW"  = 7

Now I am able to Left click, drag or highlight as you would expect.  I can do it with one or 2 hands which is great for me since I have some mobility problems in my fingers.

Also to give a little more detail on why I put in these options:
    Option "AccelFactor" ".01"
    Option "MaxSpeed" "1.0"

With these values through trial / error, pointer movement is much smoother for me and I can pan horizontally across the whole width without having to lift my finger and start again (does not run out of track pad space).  The Accel solved some of it but I needed the Max Speed to be faster because it was taking me 3 touches to even move the pointer slowly vertically.

Good luck.

---

### Post by andyeyre on 2010-10-31
> **VideoRoy said:**
> 
Off topic:
Same problem here on the battery of course but my work around there is right click battery icon ---> click "Laptop Battery (estimating)" ---> Details tab and scroll down.  Percentage is near the bottom.  Not great, but it works for now.  The battery graphic is pretty accurate for my 6 cell battery though.

Hey VideoRoy, I coded up a fix for the battery "estimating" problem. Turns out there was a bug in the upower package that provides information on battery runtime, amongst other things.

You can download a patched .deb of upower here:
[https://sites.google.com/site/andyeyre/files/upower_0.9.5-4eyre1_i386.deb?attredirects=0&d=1](https://sites.google.com/site/andyeyre/files/upower_0.9.5-4eyre1_i386.deb?attredirects=0&d=1)

(source there also) - with the patched upower, the battery runtime and charge times are reported to within ballpark accurate times, which I guess is as good as any battery gauge gets.

---

### Post by VideoRoy on 2010-10-31
> **andyeyre said:**
> Hey VideoRoy, I coded up a fix for the battery "estimating" problem. Turns out there was a bug in the upower package that provides information on battery runtime, amongst other things.

You can download a patched .deb of upower here:
[https://sites.google.com/site/andyeyre/files/upower_0.9.5-4eyre1_i386.deb?attredirects=0&d=1](https://sites.google.com/site/andyeyre/files/upower_0.9.5-4eyre1_i386.deb?attredirects=0&d=1)

(source there also) - with the patched upower, the battery runtime and charge times are reported to within ballpark accurate times, which I guess is as good as any battery gauge gets.

It works! :cool:  I will keep an eye on it tonight to see how it tracks.

Thanks very much!

---

### Post by spopa2 on 2010-11-01
I have followed the instructions in post 6 to get my left and right buttons to work:
 	Code:
 	sudo su 
     	Code:
 	echo options psmouse proto=exps > /etc/modprobe.d/psmouse.modprobe 
     	Code:
 	reboot 
Next I put the "11-touchpad.conf" file found on page 6 of this thread in to **/usr/share/X11/xorg.conf.d/** (while running as root) and ran the command:

gconftool-2 --set /desktop/gnome/peripherals/touchpad/scroll_method 2 --type int

I am running ubuntu 10.10 and I still cannot use the two finger scrolling on my HP mini 210. 

Does anyone know what can be done to fix this? Is it necessary to undo the first set of commands I followed? If so how can this be done?

Thanks!

---

### Post by VideoRoy on 2010-11-01
> **spopa2 said:**
> I have followed the instructions in post 6 to get my left and right buttons to work:
     Code:
     sudo su 
         Code:
     echo options psmouse proto=exps > /etc/modprobe.d/psmouse.modprobe 
         Code:
     reboot 
Next I put the "11-touchpad.conf" file found on page 6 of this thread in to **/usr/share/X11/xorg.conf.d/** (while running as root) and ran the command:

gconftool-2 --set /desktop/gnome/peripherals/touchpad/scroll_method 2 --type int

I am running ubuntu 10.10 and I still cannot use the two finger scrolling on my HP mini 210. 

Does anyone know what can be done to fix this? Is it necessary to undo the first set of commands I followed? If so how can this be done?

Thanks!
Sorry I did not do those steps.  I just edited the 11-touchpad.conf and loaded Andy's patch and rebooted.  Did not run anything else.

I would say undo if you can and just load Andy's patch.  You might want to check out my last post as well with a few tweaks to the 11-touchpad.conf.  I have to say my setup is working perfectly except for my big fat palms hitting the touchpad.

---

### Post by spopa2 on 2010-11-02
hey videoroy,

so i reinstalled ubuntu to get rid of my previous settings, and then i followed exactly what you did. while following post 54 i also ran the line:
gconftool-2 --set /desktop/gnome/peripherals/touchpad/scroll_method 2 --type int

i then installed andy's patch, made you changes to the .conf file and rebooted.

my mouse pad now has right click, but it is erratic if i try to use two fingers and it does not scroll at all (two fingers or edge).

Did you not run the line i mentioned previously?

do you have any ideas what im doing wrong?

thanks

---

### Post by taofd on 2010-11-03
Hey guys, I've been reading through the suggestions on the thread, but I'm really confused where to begin and what step to follow next (everyone seems to have a different suggestion for 11-touchpad.conf.

Can someone who knows what they're doing quickly summarise the steps and order necessary to get a working touchpad.

1) Which 11-touchpad.conf to use
2) Which order do I do this? touchpad.conf first or Andy's deb first?

I would like to have:

1) touchpad LEFT and RIGHT click working (cursor doesn't tweak when I have two fingers on separate areas of the touchpad)
2) two finger scroll working


An added bonus would be able to enable edge scrolling / and or horizontal scroll in conjunction with two finger scroll.

Thanks!

**EDIT: I've gotten it to work... kind of. The cursor will still slightly move when attempting to commit a click and this prevents precision clicks which is super annoying. Does anyone know of a way to make it so that if two points of contact are present on the touchpad and one of the points is located within a "click zone", that the cursor is prevented from moving, or sensitivity is turned WAY down during this duration?**

---

### Post by oxfrombws on 2010-11-05
This is what I did to get
1. Left and Right click.
2. Vertical Scroll

Created /etc/udev/rules.d/66-xorg-synaptics.rules 
This tag the device as hpmini_210

```
ACTION!="add|change", GOTO="xorg_synaptics_end"
KERNEL!="event*", GOTO="xorg_synaptics_end"

ENV{ID_INPUT_TOUCHPAD}!="1", GOTO="xorg_synaptics_end"

# Placeholder for platform specific quirks needing
# ID_INPUT.tags to be set.
ATTR{[dmi/id]product_name}=="HP Mini 210-1100", ENV{ID_INPUT.tags}="hpmini_210"

LABEL="xorg_synaptics_end"

```Created /usr/share/X11/xorg.conf.d/52-synaptics-quirks.conf 
This sets the click zone and jump threshold, you can add more setting to suite your needs, and it only applies to HP mini 210 click pad with the MatchTag setting.

```
Section "InputClass"
    Identifier "HP 210 embedded buttons quirks"
    MatchTag "hpmini_210"
    MatchDevicePath "/dev/input/event*"
    Driver "synaptics"
    Option "JumpyCursorThreshold" "200"
    Option "AreaBottomEdge" "3900"
EndSection

```


And install the patched [andyeyre]("http://newyork.ubuntuforums.org/member.php?u=1178283")'s xorg-synaptic package on post #119 to get right click.

---

### Post by taofd on 2010-11-05
Out of curiosity, how do you guys know what to put in these conf files? Is there documentation available for the synaptics driver, or for what will work for the hp 210?

I still don't have two-finger scroll working -___-;

---

### Post by oxfrombws on 2010-11-05
> **taofd said:**
> Out of curiosity, how do you guys know what to put in these conf files? Is there documentation available for the synaptics driver, or for what will work for the hp 210?

I still don't have two-finger scroll working -___-;

It's in the man page.
[http://manpages.ubuntu.com/manpages/lucid/man4/synaptics.4.html](http://manpages.ubuntu.com/manpages/lucid/man4/synaptics.4.html)

---

### Post by skipperx on 2010-11-05
I think it will be helpful if people who got it working can post the output of 
```
synclient -l
```

---

### Post by VideoRoy on 2010-11-05
> **skipperx said:**
> I think it will be helpful if people who got it working can post the output of 
```
synclient -l
```
Sorry folks I have been traveling without my computer.

My setup is working very well for me.  All I did was make the changes I posted in the 11-touchpad.conf and installed Andy's patch and rebooted.  To be clear I do not use the 2 finger scroll because I cannot use that method for my fingers.  Also I am using the HP mini 2102 but all the hardware is identical to the 210 (I have inside info on that one)

Attached is the output of synclient and my 11-touchpad.conf file if it helps anyone.  Note I added .txt to the 11-touchpad.conf so it would upload here.

---

### Post by VideoRoy on 2010-11-07
I should probably start another thread but this one seems to have some momentum.

I still have one weird problem that comes and goes and after reading some of the other posts here I think others may have it but describing it differently.

The problem is when I left click and try to highlight text or move an object with the second finger, the pointer goes crazy and moves all over.  This is how I highlight text most of the time.  I think others are experiencing the same problem here.

The strange thing is that sometimes it will work as expected even without me making any change that I know of.  Maybe some application sets it working or some other activity.

Any way I have saved output of synclient -l in my non-working config and if I ever get it working again I will capture it again and hopefully the change is in there.  If anyone has this working I would appreciate knowing what you did or just capture synclient -l output to a file an post it.

BTW: Thanks to oxfrombws for the AreaBottomEdge "3900" setting.  This has helped make the workaround a little smoother for me since it keeps the button area from reacting like a normal touchpad if you graze it.

Great help here in the forums!

---

### Post by VideoRoy on 2010-11-07
Ok, I booted up this morning and left click drag / highlight is working fine again.  Ran synclient and the only difference is the LockedDrags=0 now where as I had it enabled before when it was not working for me.

I am a little suspicious that this is actually the problem because during troubleshooting I changed this value from on to off a couple of times and rebooted and it did not make a difference.  The only difference this time was a cold boot but Ubuntu should not know the difference unless a setting is kept in a different location.

I will continue to monitor this one.

---

### Post by cyberkilla on 2010-11-08
Hello, will there be a fix for this problem available in Maverick within the next few of months?

I've read through the entire thread, and, forgive me if I'm mistaken, but there doesn't appear to be fully fledged solution available at the moment.

---

### Post by VideoRoy on 2010-11-12
> **cyberkilla said:**
> Hello, will there be a fix for this problem available in Maverick within the next few of months?

I've read through the entire thread, and, forgive me if I'm mistaken, but there doesn't appear to be fully fledged solution available at the moment.
You might not get a reply unless one of the developers chimes in.

I can tell you that I have been using the setup in this thread daily now and it does work perfectly for me even though this is not an official Ubuntu fix.  I do not use 2 finger scrolling and never have so that is the only part I cannot comment on but the button clicks all work as expected.

---

### Post by lemming1 on 2010-11-16
The developers may not realise that there is a problem as this thread title begins with the word  "[SOLVED]".

Is a repost necessary?

---

### Post by zachin2036 on 2010-11-17
> **lemming1 said:**
> The developers may not realise that there is a problem as this thread title begins with the word  "[SOLVED]".

Is a repost necessary?

+1 for this idea.  Sure, the whole "two-finger tap for right-click" works, technically.  But it's not a perfect solution.  It's one of the only things that bums me out about having Linux on my wife's netbook - because she doesn't know why I wiped out Windows if what I replaced it with is "not working".  It's the bad apple spoiling the bunch for her, unfortunately.

Anyway, all that said, I think someone should either re-post or re-open this topic...thanks!

---

### Post by pmbuc on 2010-11-22
> **John Baptist said:**
> Hi. I believe I've finally solved this problem. I've enclosed the solution in the attachment. Basically, it goes like this:

1. Copy the enclosed file as 11-touchpad.conf into this directory: /usr/lib/X11/xorg.conf.d/
2. In addition, it's also necessary to execute the following command:

gconftool-2 --set /desktop/gnome/peripherals/touchpad/scroll_method 2 --type int

You only need to run this command once; unless you play around with gnome-mouse-properties, the setting will be remembered until you change it. You need root privileges to copy the config file, but the gconftool-2 command should be run as your regular login user.

If you follow these steps, two-fingered scrolling and double-tap for right click will be enabled on your touchpad, even on non-multitouch hardware. It will work even after restart, hibernate, or suspend. If the responsiveness isn't exactly your liking, you can change the EmulateTwoFingerMinZ, EmulateTwoFingerMinW, and JumpyCursorThreshold settings in the file; the best value for these settings also depends on your hardware. The EmulateTwoFingerMinW is the most interesting; this is the minimum width of the touch that should be considered two-finger, and should thus activate scrolling. 

I've tested this on my HP Mini 210 running Lucid. I'd love to hear if this works for you, too.

My thanks for your outstanding solution! You and others may be interested to know that this solution also works in Jolicloud 1.1 Preview, which is based on Ubuntu 10.04 LTS, which I am currently testing out on my HP Mini 210, with two-finger scolling and right-click working just fine. 

Thanks again ~ Paul :P

---

### Post by taofd on 2010-11-23
> **zachin2036 said:**
> +1 for this idea.  Sure, the whole "two-finger tap for right-click" works, technically.  But it's not a perfect solution.  It's one of the only things that bums me out about having Linux on my wife's netbook - because she doesn't know why I wiped out Windows if what I replaced it with is "not working".  It's the bad apple spoiling the bunch for her, unfortunately.

Anyway, all that said, I think someone should either re-post or re-open this topic...thanks!


Agreed, while it "works", I occasionally get periods where my touchpad still tweaks out and is extremely jumpy again. I used VideoRoy and Andy's fixes.

There are still problems with precision clicking and two finger scroll not working.

---

### Post by d-block on 2010-11-30
I'm unable to right click, basically the two buttons at the bottom of the touch pad don't work.  I tried the solution on page two, but I must have done something wrong.  Is there a simple update, or something that is smart enough to install without a degree in linux?  I'm not trying to write a freaking program here.

---

### Post by billsdesk on 2010-12-01
The kernel patch mentioned early on in this thread did not work for kernel version 2.6.35. The header hunks failed.

I downloaded the X11 changes mentioned above, but the new version of X does not have the same directory structure.

Besides Ubuntu 10.10 and Linux Mint 10, the same problems appears in Fedora 14. However, I do not have the problem in MeeGo 1.1.

The problem is that there is no right mouse button, the entire button area acts as a huge left mouse button.

---

### Post by ElSlunko on 2010-12-02
Just posting a quick "me too" in this thread. I just bought a dm4 and am having the same trackpad issues.

---

### Post by N o i r on 2010-12-02
Hi, I just got a HP Mini 1005sa - the suggestions in this thread helped me and now I can successfully select text with the pad; the right click doesn't work yet, but no big deal.

Thanks to the people that intervened!

---

### Post by sshatery on 2010-12-03
> **theng168 said:**
> MsKK, make sure you remove the psmouse.modprobe and do a reboot.
Mine fully working now. Just cannot 2-fingers scroll and pinch to zoom.

Theng

how to remove psmouse.modprobe ???

---

### Post by yud1hu1 on 2010-12-04
Hi there!

thanks a lot to all who worked out, how to get it working. But could someone write a new instruction based on 10.10, because it seems that not only the directory changed, but also the files in it. I've got three files starting with "50-..." one with "51-..."  one with "60-..."and another with "10-..." and do neither know where to fill in the code mentioned in #52 nor do I know where to put the file in #54 to make it working.
thanks a lot for your work on this issue.

Greets

yud1hu1

---

### Post by Mindr on 2010-12-04
andyeyre,
can you please build your package for amd64 or upload the patch (didn't find it on [http://sites.google.com/site/andyeyre/files/)?](http://sites.google.com/site/andyeyre/files/)?)

---

### Post by gOLdenHaWK3D on 2010-12-04
Thanks all, especially JohnBaptist, for making this "clickpad"-thing work on my HP ProBook 4420s too.

Nice job :D Love u all. :guitar:

---

### Post by sshatery on 2010-12-05
finally i could enable the multi finger scrolling but right click still not working. im using 10.10 .
is there any solution to fix right click on 10.10??

---

### Post by yud1hu1 on 2010-12-05
could someone write a summarized instruction on how to get my touchpad working as it should on 10.10?
because double tapping as right-click is not what it could be like and not a really satisfying solution... would be wonderful! and sorry for asking: i was just not able to fix it on my own or by using the posts in this thread...

---

### Post by josecuervo on 2010-12-06
A brand new HP Mini 210-2072Cl is working after I run this command. Thanks a lot!

---

### Post by DMacos on 2010-12-12
> **mpapamanz said:**
> In Lucid should be enough to APPEND to the file /usr/lib/X11/xorg.conf.d/10-synaptics.conf
the following code
```
Section "InputClass"
        Identifier "HP Mini 2010"
        MatchProduct "SynPS/2 Synaptics TouchPad"
        MatchDevicePath "/dev/input/event*"
        Driver "synaptics"
        Option "TapButton2" "3"
        Option "EmulateTwoFingerMinZ" "15"
        Option "EmulateTwoFingerMinW" "5"
        Option "JumpyCursorThreshold" "200"
        Option "VertTwoFingerScroll" "1"
        Option "HorizTwoFingerScroll" "1"
EndSection
```Please, leave untouched the previous lines of the file.
In my case it partially works: all the settings are applied except the {Vert,Horiz}TwoFingerScroll :(. It is strange since in the Xorg.0.log file it is written that the value is updated. According to me there is a gnome configuration that overwrites the value... but I haven't find it yet.
Maybe it is usefull to someone
On my HP mini doesn't work. I copied  the 
> 11-touchpad.conf 
 file into 

> /usr/lib/X11/xorg.conf.d/
directory and rebooted the machine, but the synaptics settings are not set:
>  
...
TapAndDragGesture       = 1
    AreaLeftEdge            = 0
    AreaRightEdge           = 0
    AreaTopEdge             = 0
    AreaBottomEdge          = 0
    JumpyCursorThreshold    = 0
...


any Idea?

My bests 

DM

---

### Post by DMacos on 2010-12-12
It works, 
at maverick, the *.con files are in /usr/share/X11/xorg.conf.d
but not in /usr/lib/X11/xorg.conf.d
:)  

Best Regards 
DM

---

### Post by lyschoolsocool on 2010-12-12
> **mapkar said:**
> how can this be undone?

I was wondering that too. The command makes right clicks possible, but it also slows down the pointer to unbearable levels and deletes the touchpad options from the mouse menu.

I disabled it by running nautilus as root then locating

/etc/modprobe.d/psmouse.modprobe

Open the file then just cancel its function (put # in front of the line).

I appreciate everyone's work so far, but none of the solutions feel just right. It would be nice to have both two-finger scroll and the physical right-click functioning. Hopefully there will be an encompassing solution! :)

---

### Post by lyschoolsocool on 2010-12-12
EUREKA! :D

There is a sensible workaround that allows for both left and right click.

[http://bigbrovar.aoizora.org/index.php/2010/10/10/how-to-enable-right-middle-click-on-clickpads-ubuntu-10-10/](http://bigbrovar.aoizora.org/index.php/2010/10/10/how-to-enable-right-middle-click-on-clickpads-ubuntu-10-10/)

Just follow the instructions detailed and your computer will have physical right and left click. Then, just follow the directions by John Baptist to enable two-finger scrolling.

This is so far the only way I've been able to have both two-finger scroll and physical clicks, and it mimics the functions in windows 7 close enough. The only downer is that for physical clicks, you have to press close to the bottom edge.

I'm using an HP dv5-2135dx, but it has the same clickpad as the HP Mini 210 and the HP Envy. Good luck to those with the same problems!

---

### Post by jswalker2 on 2010-12-17
> **lyschoolsocool said:**
> EUREKA! :D

There is a sensible workaround that allows for both left and right click.

[http://bigbrovar.aoizora.org/index.php/2010/10/10/how-to-enable-right-middle-click-on-clickpads-ubuntu-10-10/](http://bigbrovar.aoizora.org/index.php/2010/10/10/how-to-enable-right-middle-click-on-clickpads-ubuntu-10-10/)

Just follow the instructions detailed and your computer will have physical right and left click. Then, just follow the directions by John Baptist to enable two-finger scrolling.

This is so far the only way I've been able to have both two-finger scroll and physical clicks, and it mimics the functions in windows 7 close enough. The only downer is that for physical clicks, you have to press close to the bottom edge.

I'm using an HP dv5-2135dx, but it has the same clickpad as the HP Mini 210 and the HP Envy. Good luck to those with the same problems!

Finally, thank you so much! :)

This work on both Ubuntu netbook 10.10 and jolicloud 1.1 on my HP mini 210. Fantastic stuff

---

### Post by scooby359 on 2010-12-19
Indeed, tried this on my HP Mini 210 and I've got right click!! And without the slowing of the cursor I've suffered with other fixes in the past.

Very impressed, thank you!

---

### Post by jrodimusprime on 2010-12-20
worked for me. hopefully more mouse scrolly goodness to come.

---

### Post by ElSlunko on 2010-12-20
Wait so do you guys have to actually click down on the pad for the right click or do you have to tap quickly? What about dragging windows.

---

### Post by uppertoe on 2010-12-25
Not sure it's been mentioned in this thread, but [https://help.ubuntu.com/community/SynapticsTouchpad](https://help.ubuntu.com/community/SynapticsTouchpad) has a nice bit of advice that worked for my hp 210.

Installing the package at 

[https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-input-synaptics/+bug/308191/comments/167](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-input-synaptics/+bug/308191/comments/167)

worked like a dream - no two finger scroll, but click and drag is working nicely; something I think is a little more important.

---

### Post by ElSlunko on 2010-12-26
After doing two finger scrolling in windows and edge scrolling (or whatever it's called) I much prefer the edge scrolling. Though it would be nice to be able to pinch and zoom.


Edit : Thanks for that link uppertoe! Now I just have to get my physical right click working and we're in business!

---

### Post by gregalynch on 2010-12-30
> **pauljwells said:**
> Lucid uses the udev architecture for input device control, apparently :-S

I found this on the Debian Wiki:

[http://wiki.debian.org/SynapticsTouchpad]("http://wiki.debian.org/SynapticsTouchpad")



You have to delete the psmouse.modprobe file from /etc/modprobe.d/ if you used the psmouse kludge before, then create the 99-synaptics.rules file and fill in the above text and reboot. For me it got left and right mouse clicks working and also right hand edge scrolling, nice!

There is a whole section in the Ubuntu docs about setting this up here:

[http://manpages.ubuntu.com/manpages/karmic/man4/synaptics.4.html]("http://manpages.ubuntu.com/manpages/karmic/man4/synaptics.4.html")

Maybe we can have a play around and improve on the Debian file?

I used this fix and it enabled me to do everything - albeit not in exactly the way I would want to do everything.  The only real annoyance now is that after restart the cursor is frozen for 30 seconds or so for some reason - any ideas on what's causing this?

---

### Post by betoqp on 2011-01-02
I have an HP Mini 210 and recently installed Ubuntu Unity 10.10 on it as the only OS.
I tried a solution ([http://caseytinsley.wordpress.com/2010/11/07/ubuntu-10-10-touchpad-fix/](http://caseytinsley.wordpress.com/2010/11/07/ubuntu-10-10-touchpad-fix/)) and it worked, but no scrolling at all and the pointer speed got terribly slow. Also the Touchpad tab in System>Mouse disappeared. Maxing out the sensitivity and acceleration doesn't seem to do much to fix this. I've been reading this thread but I got confused after a few pages about what to do what not to do. All I want is to undo what I did with the link up there and have a touchpad with left/right clicks and ANY type of scrolling (two finger or edge, same thing). I tried this:

> **jnetman1 said:**
> You're much better off actually fixing the problem with the driver, as telling the system that the touchpad is a PS/2 mouse leaves you with zero control of the pad on the Mini 210. To do this, download the attachment at the bottom of this post and save it in your home folder:

Open the terminal on your Mini 210 and

```
sudo apt-get install build-essential patch linux-source
```

The kernel source will be a tarball that is installed in /usr/src. Extract it to your home directory like so:

```
tar -xjvf /usr/src/linux-source <tab>
``` 

Note that pressing tab will autocomplete to the version you downloaded. Once extracted, change to the source directory and untar the patch attachment you downloaded at the beginning:

```
cd linux-source <tab>
tar -xzvf ../clickpad.tar.gz
```

Now we'll patch the driver files, copy the Makefile to the right place, and compile and install the new driver:

```
patch -p1 <clickpad_patch
cp Makefile drivers/input/mouse/
cd drivers/input/mouse
make
sudo make install
```

Reboot your machine, and you'll find the touchpad works like it should. Note that this patch is based on Takashi Iwai's fine work here: [http://patchwork.kernel.org/patch/67335/](http://patchwork.kernel.org/patch/67335/)
But I got an error message around
> The kernel source will be a tarball that is installed in /usr/src. Extract it to your home directory like so:

```
tar -xjvf /usr/src/linux-source <tab>
``` 
saying something about the files being corrupted. Any help please??:confused:

---

### Post by ElSlunko on 2011-01-02
Did you try uppertoe's suggestion?

---

### Post by betoqp on 2011-01-02
yeah, both. Still nothing.

---

### Post by Sisophon2001 on 2011-01-05
> **betoqp said:**
> I have an HP Mini 210 and recently installed Ubuntu Unity 10.10 on it as the only OS.
I tried a solution ([http://caseytinsley.wordpress.com/2010/11/07/ubuntu-10-10-touchpad-fix/](http://caseytinsley.wordpress.com/2010/11/07/ubuntu-10-10-touchpad-fix/)) 

To undo this change delete the file /etc/modprobe.d/psmouse.modprobe

The second solution you tried from jnetman1 is for an old version of Ubuntu, so it had no hope of working with 10.10. However I doubt you did any harm. They to find a solution later on, matching your Ubuntu version.

Garvan

---

### Post by betoqp on 2011-01-05
What I did was reinstalling my system. I went ahead and installed the pack synaptics-dkms_1.1.1_all.deb. It gave me:
·Two finger scrolling
·Two finger right click (though no physical right click)
·Sensitivity/speed were not affected
·No click and drag (I can do small drags by holding one physical click and dragging while pressing)
·As for the 30 second wait at the start, it happens to me, but pressing the <esc> key two or three times seems to somehow 'activate' the touchpad.

I highly recommend this solution to HP Mini 210 owners (I think right click has a higher priority than click and drag). Kudos to the contributers (Y) :)

---

### Post by Mindr on 2011-01-10
So I did install a patched version of xserver-xorg-input-synaptics 1.3.0 ([found in AUR]("http://aur.archlinux.org/packages.php?ID=38120")) in Ubuntu.

Here's how (just paste the following to the terminal):
```
cd /tmp
wget http://xorg.freedesktop.org/releases/individual/driver/xf86-input-synaptics-1.3.0.tar.bz2
tar xfv xf86-input-synaptics-1.3.0.tar.bz2 
cd xf86-input-synaptics-1.3.0/
wget http://aur.archlinux.org/packages/xf86-input-synaptics-clickpad/xf86-input-synaptics-clickpad/synaptics-clickpad-support.patch
patch -p1 < synaptics-clickpad-support.patch
./configure --prefix=/usr
make
sudo make install
```
and reboot your computer.

Disclaimer: I'm not really a power Linux user, so there's probably will be some additional steps I done before.

This patch enables the right click, but two-finger scroll (which I'm not using, edge scrolling FTW) is unavailable. Tested on my HP ProBook 4520s.

---

### Post by cyberkilla on 2011-02-01
Have you tried the clickpad with a fully updated Ubuntu? A kernel update appeared a few days ago, and it mentioned clickpads several times in the changelog. I haven't downloaded a Live CD to test it on my HP Mini yet. I definitely mentioned clickpads a few times though.

Might be worth a look :)

---

### Post by pauljwells on 2011-02-02
> **cyberkilla said:**
> Have you tried the clickpad with a fully updated Ubuntu? A kernel update appeared a few days ago, and it mentioned clickpads several times in the changelog. I haven't downloaded a Live CD to test it on my HP Mini yet. I definitely mentioned clickpads a few times though.

Might be worth a look :)

Nope, doesn't seem to fixed. I uninstalled the synaptics-dkms_1.1.1_all.deb package and rebooted, back to no right click and only edge scrolling. Reinstalled the deb and it's all good again...

---

### Post by Sisophon2001 on 2011-02-02
> **cyberkilla said:**
> Have you tried the clickpad with a fully updated Ubuntu? A kernel update appeared a few days ago, and it mentioned clickpads several times in the changelog. I haven't downloaded a Live CD to test it on my HP Mini yet. I definitely mentioned clickpads a few times though.

Might be worth a look :)

Downloading the source of the latest Ubuntu kernel version 2.6.35 I find this is a comment in the source code of 

/home/garvan/linux-source-2.6.35/drivers/input/mouse/synaptics.c

```
/*
 * Clickpad's button is transmitted as middle button,
 * however, since it is primary button, we will report
 * it as BTN_LEFT.
 */
hw->left = ((buf[0] ^ buf[3]) & 0x01) ? 1 : 0;

```

With this code it will never be possible for the code below designed to transmit clicks by position on the click-pad to work.

```
/* left and right clickpad button ranges;
 * the gap between them is interpreted as a middle-button click
 */
#define CLICKPAD_LEFT_BTN_X \
((XMAX_NOMINAL - XMIN_NOMINAL) * 2 / 5 + XMIN_NOMINAL)
#define CLICKPAD_RIGHT_BTN_X \
((XMAX_NOMINAL - XMIN_NOMINAL) * 3 / 5 + XMIN_NOMINAL)

/* handle clickpad events */
static void clickpad_process_packet(struct synaptics_data *priv,
    struct synaptics_hw_state *hw)
{
/* clickpad mode reports Y range from 0 to YMAX_NOMINAL,
 * where the area Y < YMIN_NOMINAL is used as click buttons
 */
if (hw->y < YMIN_NOMINAL) {
/* button area */
hw->z = 0; /* don't move pointer */
/* clickpad reports only the middle button, and we need
 * to fake left/right buttons depending on the touch position
 */
if **(hw->middle)** { /* clicked? */

```

I recall there is another issue with the reported capabilities of the click-pad, also easily fixed. What i don't understand is why it has not been fixed long ago.

Garvan

---

### Post by cyberkilla on 2011-02-03
> **pauljwells said:**
> Nope, doesn't seem to fixed. I uninstalled the synaptics-dkms_1.1.1_all.deb package and rebooted, back to no right click and only edge scrolling. Reinstalled the deb and it's all good again...

Damn, I apologise for giving you false hope. Just for the record, the lines in the change log that tricked me were:

```
Version 2.6.35-25.43: 

  [ Robert Hooker ]

  * Revert "(pre-stable): input: Support Clickpad devices in ClickZone
    mode"
    - LP: #669399

 ...

 [ Takashi Iwai ]

  * SAUCE: input: Support Clickpad devices in ClickZone mode
    - LP: #516329
```

Looks like something was done, then reverted?

---

### Post by Lokesh123 on 2011-02-06
> **pauljwells said:**
> Nope, doesn't seem to fixed. I uninstalled the synaptics-dkms_1.1.1_all.deb package and rebooted, back to no right click and only edge scrolling. Reinstalled the deb and it's all good again...

Hello,
following this thread I installed the cited synaptics-dkms 1.1.1, and oh wonderful, it gave me the functionality I needed. BUT

A recent system upgrade, which included kernel 2.6.35-25 (before I had 2.6.35-24), destroyed the whole benefit. Instead, tipping with two fingers, which was the right-click, now results in an uncontrolled random jump of the mouse pointer. Removing and re-installing of the synaptics-dkms file did not help, neither booting back into the previous kernel version.

I have not the slightest idea what to do. Any suggestions what I could look up?

BTW, I have the Envy13, same touchpad as the one for the mini.

Lokesh

---

### Post by prwells on 2011-02-06
> **The Deacon said:**
> I've got the same issue.  Any help would be greatly appreciated.

The "trigger secondary click by holding down primary button" (under System> Mouse) isn't a disaster if you really need a right click, at least.

Ok! Very good indeed! Thanks.

---

### Post by jevus on 2011-02-16
I used the 11-touchpad.conf file and everything seems to work fine except for the click area. I set the threshold to 3900 which disabled tapping/moving below the line on the touchpad but when I want to click (left or right) I need to press the bottom millimeter of the button. 

Is there an option I'm not seeing in the manpage? I just want to be able to click anywhere within the button confines instead of the bottom millimeter of the buttons.

---

### Post by TianaCo on 2011-02-28
> **Sabot said:**
> To get the trackpad working correctly you need to use the terminal and enter in the below commands. Make sure you press enter after each command:

    ```
sudo su
```    ```
echo options psmouse proto=exps > /etc/modprobe.d/psmouse.modprobe
```    ```
reboot
```
Once the computer reboots your trackpad will be able to do left click and drag and right clicking.

thank you, Sabot - this worked perfectly:D

---

### Post by DormantBrood on 2011-03-08
> **jnetman1 said:**
> You're much better off actually fixing the problem with the driver, as telling the system that the touchpad is a PS/2 mouse leaves you with zero control of the pad on the Mini 210. To do this, download the attachment at the bottom of this post and save it in your home folder:

Open the terminal on your Mini 210 and

```
sudo apt-get install build-essential patch linux-source
```The kernel source will be a tarball that is installed in /usr/src. Extract it to your home directory like so:

```
tar -xjvf /usr/src/linux-source <tab>
```Note that pressing tab will autocomplete to the version you downloaded. Once extracted, change to the source directory and untar the patch attachment you downloaded at the beginning:

```
cd linux-source <tab>
tar -xzvf ../clickpad.tar.gz
```Now we'll patch the driver files, copy the Makefile to the right place, and compile and install the new driver:

```
patch -p1 <clickpad_patch
cp Makefile drivers/input/mouse/
cd drivers/input/mouse
make
sudo make install
```Reboot your machine, and you'll find the touchpad works like it should. Note that this patch is based on Takashi Iwai's fine work here: [http://patchwork.kernel.org/patch/67335/](http://patchwork.kernel.org/patch/67335/)

Hi,

The above patch does not seem to work for me, and fails upon executing the second command. And a new ubuntu user I am not sure what to make of the terminal output stating the error.

I enter ```
tar -xjvf /usr/src/linux-source <tab>
``` and tab to get the correct version number and the terminal outputs:

```
tar (child): /usr/src/linux-source-2.6.35: Cannot read: Is a directory
tar (child): At beginning of tape, quitting now
tar (child): Error is not recoverable: exiting now

bzip2: Compressed file ends unexpectedly;
    perhaps it is corrupted?  *Possible* reason follows.
bzip2: Invalid argument
    Input file = (stdin), output file = (stdout)

It is possible that the compressed file(s) have become corrupted.
You can use the -tvv option to test integrity of such files.

You can use the `bzip2recover' program to attempt to recover
data from undamaged sections of corrupted files.

tar: Child returned status 2
tar: Error is not recoverable: exiting now

```

Can anyone make any sense of this, and perhaps suggest a fix?

---

### Post by VideoRoy on 2011-03-09
I just noticed in the new kernel update, 2.6.35-27-generic that one of the fixes is for the click pad and it mentions the HP Mini 210.

I am still using Andy's patch for months and it has worked flawlessly so I was wondering if anyone have tried this new kernel yet to see if it actually fixes the problem.  

I have updated my desktop but not my Mini yet.

---

### Post by tyoungblood on 2011-03-10
> **VideoRoy said:**
> I just noticed in the new kernel update, 2.6.35-27-generic that one of the fixes is for the click pad and it mentions the HP Mini 210.

I am still using Andy's patch for months and it has worked flawlessly so I was wondering if anyone have tried this new kernel yet to see if it actually fixes the problem.  

I have updated my desktop but not my Mini yet.

Just did a fresh install on my Mini 210-1170NR and I updated it about 4 hrs ago. The track pad and scrolling work but no right click. When was the the kernel updated and how do I  know if that's the current one installed? TIA

---

### Post by tgm4883 on 2011-03-10
"uname -a" will show you the full kernel version.

I updated my kernel on my 10.04 machine, although I think i'm on 2.6.38 now (from natty). I did notice that the touchpad works better now, although no right click (multitouch clicking works for right click though)

---

### Post by jakslev on 2011-03-11
> **John Baptist said:**
> Hi. I believe I've finally solved this problem. I've enclosed the solution in the attachment. Basically, it goes like this:

1. Copy the enclosed file as 11-touchpad.conf into this directory: /usr/lib/X11/xorg.conf.d/
2. In addition, it's also necessary to execute the following command:

gconftool-2 --set /desktop/gnome/peripherals/touchpad/scroll_method 2 --type int

You only need to run this command once; unless you play around with gnome-mouse-properties, the setting will be remembered until you change it. You need root privileges to copy the config file, but the gconftool-2 command should be run as your regular login user.

If you follow these steps, two-fingered scrolling and double-tap for right click will be enabled on your touchpad, even on non-multitouch hardware. It will work even after restart, hibernate, or suspend. If the responsiveness isn't exactly your liking, you can change the EmulateTwoFingerMinZ, EmulateTwoFingerMinW, and JumpyCursorThreshold settings in the file; the best value for these settings also depends on your hardware. The EmulateTwoFingerMinW is the most interesting; this is the minimum width of the touch that should be considered two-finger, and should thus activate scrolling. 

I've tested this on my HP Mini 210 running Lucid. I'd love to hear if this works for you, too.

I don't have the directory /usr/lib/X11/xorg.conf.d/ - am I supposed to make it myself?

---

### Post by VideoRoy on 2011-03-12
> **tgm4883 said:**
> "uname -a" will show you the full kernel version.

I updated my kernel on my 10.04 machine, although I think i'm on 2.6.38 now (from natty). I did notice that the touchpad works better now, although no right click (multitouch clicking works for right click though)

Thanks for the confirmation.  I will update but just continue to use Andy's patch then.

At least with his patch and the few others my Mini 2102 works exactly like a laptop with discreet buttons, etc.  Too bad that level of patch has not made it back into the kernel.

---

### Post by sshatery on 2011-03-16
> **Sabot said:**
> To get the trackpad working correctly you need to use the terminal and enter in the below commands. Make sure you press enter after each command:

    ```
sudo su
```

    ```
echo options psmouse proto=exps > /etc/modprobe.d/psmouse.modprobe
```

    ```
reboot
```


Once the computer reboots your trackpad will be able to do left click and drag and right clicking.

i did it but now i want to remove it and bring it back to the 1st condition i mean the time before what i did.
how can i remove this:
```
echo options psmouse proto=exps > /etc/modprobe.d/psmouse.modprobe
```

---

### Post by jrishel on 2011-03-21
edit the file and remove the text that we echoed into the last line of the file.
```

vi /etc/modprobe.d/psmouse.modprobe
```

---

### Post by mark.0 on 2011-03-23
Please help, I applied this new patch ontop of the old "psmouse" fix. Then I used the vi command to remove the old fix. Now my mouse doesn't work at all! I looked at my modprobe file and it is completely empty. Not sure how that happened. How do I restore my modprobe file to normal? Is that even what the problem is? Please help, thanks.

I tried renaming the psmouse.modprobe to psmouse.modprobeOLD but I still have no mouse. I'm starting to think that the patch that was applied messed something up, but i'm not knowledgable enough to say. I can say however, that the steps were followed to the T.

---

### Post by howgodskill on 2011-04-28
things are getting complicated again. as i just installed 11.04 on my mini 210, i noticed the scrolling was fixed, even the two finger swipe. nevertheless, the jumping cursor problem was back. applying the fix got the jumpiness fixed, but this removed both swiping and the touchpad-side scrolling! damned!

nevertheless, i have good hope. the swiping/scrolling is possible with 11.04, and so is getting the second button click and drag/drop. now just having these combined again would be amazing.

---

### Post by tgm4883 on 2011-04-28
> **howgodskill said:**
> things are getting complicated again. as i just installed 11.04 on my mini 210, i noticed the scrolling was fixed, even the two finger swipe. nevertheless, the jumping cursor problem was back. applying the fix got the jumpiness fixed, but this removed both swiping and the touchpad-side scrolling! damned!

nevertheless, i have good hope. the swiping/scrolling is possible with 11.04, and so is getting the second button click and drag/drop. now just having these combined again would be amazing.

Which fix?

---

### Post by howgodskill on 2011-04-28
> **tgm4883 said:**
> Which fix?
/etc/modprobe.d/psmouse.modprobe
fixes the drag/drop but disables the swiping functionality added in 11.04.

---

### Post by tgm4883 on 2011-04-28
> **howgodskill said:**
> /etc/modprobe.d/psmouse.modprobe
fixes the drag/drop but disables the swiping functionality added in 11.04.

That is correct. Do you know what a ps mouse is?

[http://en.wikipedia.org/wiki/PS/2_connector](http://en.wikipedia.org/wiki/PS/2_connector)

There is no swiping ability with a ps mouse. With that fix you are basically saying that the touchpad is a mouse from the 90's

---

### Post by arscariosus on 2011-04-29
Ubuntu 11.04 has good mouse support for HP MIni 210's crappy clickpad, only the right click is not working. Any fix on this? Thanks.

---

### Post by scooby359 on 2011-04-29
I'm finding that if I tap the bottom right of the pad very lightly, that brings up the right click menu, or alternatively, click and hold anywhere on the pad, then press with a second finger and as long as the first finger is still held, then menu can be navigated.

Not ideal but it's an option

---

### Post by VideoRoy on 2011-04-29
> **arscariosus said:**
> Ubuntu 11.04 has good mouse support for HP MIni 210's crappy clickpad, only the right click is not working. Any fix on this? Thanks.

I actually had just the opposite experience.  The click pad was unusable again just like a 10.10 install.  I had to go back and modify some of the config files or else the click pad buttons acted just like the touchpad.

After doing that I have everything working again except of course for the right click.  I am going to reload AndyEyre's patched driver again and see if that fixes it like it did for 10.10.

For the record I am running the HP 2102 which is the business version of the 210 but is all the same hardward.

---

### Post by VideoRoy on 2011-04-29
Looks like the old patch does not work any more due to new dependencies.  I hope Andy is still around to maybe fix this up again ;)

The 2 finger works about 10% of the time.  I does not work on little status icons, etc.  I was really hoping 11.04 would be better.

---

### Post by VideoRoy on 2011-04-29
Ok, this is solved for me by following the build instructions in post #144 in the link below.

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/582809]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/582809")

Note: I had to uninstall Synaptics driver in Synaptic manager before install my new .deb or else it just reinstalls the original.

Here are the features I use that are fixed:
1. Left Click Button Drag
2. Right Click Button
3. Right side of pad scroll

I can also confirm 2 finger tap emulates a Right Click but I think that worked in 11.04 already.

I do not use any of the other multi-finger or advanced features due to a slight disability in my fingers so I cannot confirm if anything else works.

---

### Post by lennyp on 2011-04-30
can you please repost your solution here?
the page is huge so I don't know which part you read :(

---

### Post by stathis21 on 2011-04-30
install the .deb file that user Alexander S. Gryanko posted at post #155 here 
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/582809](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/582809)
this file fixes the right clic and multitouch still works...
but drag n drop doesn't work at all:(....:confused:

---

### Post by VideoRoy on 2011-04-30
> **lennyp said:**
> can you please repost your solution here?
the page is huge so I don't know which part you read :(

Sure, it is the one from David in post #144 only.  But here are the steps from him below.


A tarball of the patches is here (they are as similar to the SuSE patches as possible, 212-fixups.patch contains the additions to make the result compile cleanly):
[http://david.hardeman.nu/synaptics-suse-patches.tar.bz2](http://david.hardeman.nu/synaptics-suse-patches.tar.bz2)

> To build your own xserver-xorg-input-synaptics package, do:

mkdir tmpbuild
cd tmpbuild
wget [http://david.hardeman.nu/synaptics-suse-patches.tar.bz2](http://david.hardeman.nu/synaptics-suse-patches.tar.bz2)
apt-get source xserver-xorg-input-synaptics
cd xserver-xorg-input-synaptics-<version>
cd debian
cd patches
tar xfvj ../../../synaptics-suse-patches.tar.bz2
ls -1 2*.patch >> series
cd ..
cd ..
sudo apt-get build-dep xserver-xorg-input-synaptics
dpkg-buildpackage -us -uc -rfakeroot
sudo dpkg -i ../xserver-xorg-input-synaptics_<version>_<arch>.deb

And then restart your X server


I actually skipped the last step since I built is on a second computer but I just copied my i386 .DEB on a memory stick to my Netbook, uninstalled current Synaptics Xorg driver from Synatic Package Manager.

Next I installed my new .DEB by just clicking on it and letting Get Software install it.  Just ignore the warning.

If all goes wrong just reinstall original Xorg driver from Synaptic again.

This was a perfect step by step for me.  I am running 11.04 Desktop 32 bit on an HP 2102 (same as 210).  I cannot vouch for others.  I would post my .DEB but I do not have a way to do that.

Edit: One other comment, I had put some fixes in the /usr/share/X11/xord.d directory like I did for 10.10.  I had to remove all these because they conflicted with the new driver.

---

### Post by VideoRoy on 2011-04-30
> **stathis21 said:**
> install the .deb file that user Alexander S. Gryanko posted at post #155 here 
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/582809](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/582809)
this file fixes the right clic and multitouch still works...
but drag n drop doesn't work at all:(....:confused:

That was a x64 version so I could not use it so cannot vouch whether it works for the Mini.

Have you tried just building your own?  Took me only about 15 minutes to go through the steps.

---

### Post by stathis21 on 2011-04-30
> **VideoRoy said:**
> That was a x64 version so I could not use it so cannot vouch whether it works for the Mini.

Have you tried just building your own?  Took me only about 15 minutes to go through the steps.

I tried both solutions,(i'm using ubuntu 64bit),but still no drag n drop... (my laptop is a hp pavilion dv6,not hp mini)
thank for the reply!

---

### Post by tgm4883 on 2011-04-30
> **lennyp said:**
> can you please repost your solution here?
the page is huge so I don't know which part you read :(

As he noted, post [#144]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/582809/comments/144")

---

### Post by tgm4883 on 2011-04-30
> **VideoRoy said:**
> Sure, it is the one from David in post #144 only.  But here are the steps from him below.


A tarball of the patches is here (they are as similar to the SuSE patches as possible, 212-fixups.patch contains the additions to make the result compile cleanly):
[http://david.hardeman.nu/synaptics-suse-patches.tar.bz2](http://david.hardeman.nu/synaptics-suse-patches.tar.bz2)



I actually skipped the last step since I built is on a second computer but I just copied my i386 .DEB on a memory stick to my Netbook, uninstalled current Synaptics Xorg driver from Synatic Package Manager.

Next I installed my new .DEB by just clicking on it and letting Get Software install it.  Just ignore the warning.

If all goes wrong just reinstall original Xorg driver from Synaptic again.

This was a perfect step by step for me.  I am running 11.04 Desktop 32 bit on an HP 2102 (same as 210).  I cannot vouch for others.  I would post my .DEB but I do not have a way to do that.

Edit: One other comment, I had put some fixes in the /usr/share/X11/xord.d directory like I did for 10.10.  I had to remove all these because they conflicted with the new driver.

Do you have a launchpad account? You could post it to your PPA

---

### Post by VideoRoy on 2011-04-30
> **tgm4883 said:**
> Do you have a launchpad account? You could post it to your PPA

I just registered there so I could reply but I do not know much about it.  I will check it out and see if I can figure out how to post it.

---

### Post by VideoRoy on 2011-05-01
I messed around with Launchpad too long.  Some day when I have a bunch of extra time I will try it again.

Not sure what rules I am violating but I just gziped the deb and attached it here.

Just use gzip -d <file name>

Note if you save the .gz to directory of its own you can type "gzip -d x" then hit the tab key and it will fill in the rest.

I make not warranties express or implied.  I compiled this from the post I listed above and it works on an HP Mini 2102 should work fine on a 210 as well.  Not sure about any other model or make.

Good luck.

Note: Please read my previous post but this is only tested on 11.04.

---

### Post by howgodskill on 2011-05-01
scrolling fix might be

sudo apt-get install gpointing-device-settings

---

### Post by howgodskill on 2011-05-01
> **VideoRoy said:**
> I messed around with Launchpad too long.  Some day when I have a bunch of extra time I will try it again.

Not sure what rules I am violating but I just gziped the deb and attached it here.

Just use gzip -d <file name>

Note if you save the .gz to directory of its own you can type "gzip -d x" then hit the tab key and it will fill in the rest.

I make not warranties express or implied.  I compiled this from the post I listed above and it works on an HP Mini 2102 should work fine on a 210 as well.  Not sure about any other model or make.

Good luck.

Note: Please read my previous post but this is only tested on 11.04.

this is amazing, thanks!!! only thing that still misfires is that selecting / dragging doesn't work when two-finger-scroll is enabled, because when one finger pushes left button and other finger moves, it's regarded as scrolling. nevertheless, this fix was just what i needed!


edit: this two-finger-scrolling / selecting problem could be fixed if the button-part of the touchpad would no longer be regarded as part of the touchpad but just as buttons, right? would that be a possibility, to just disable the bottom centimeter for all input except clicking of the buttons? just letting the mind run wild here, it's a longshot...

---

### Post by CTR_Cody on 2011-05-01
VideoRoy,

I just wanted to say thank you so much for making that .deb patch for my touchpad!
I'm here to report that the patch works PERFECTLY for my HP mini 210 1170NR netbook, and that you are totally awesome. You saved my right click!

---

### Post by VideoRoy on 2011-05-01
> **howgodskill said:**
> this is amazing, thanks!!! only thing that still misfires is that selecting / dragging doesn't work when two-finger-scroll is enabled, because when one finger pushes left button and other finger moves, it's regarded as scrolling. nevertheless, this fix was just what i needed!


edit: this two-finger-scrolling / selecting problem could be fixed if the button-part of the touchpad would no longer be regarded as part of the touchpad but just as buttons, right? would that be a possibility, to just disable the bottom centimeter for all input except clicking of the buttons? just letting the mind run wild here, it's a longshot...

Nice to see a second confirmation here.

I actually played around with AreaBottomEdge which will do what you described.  I did this will synclient and with some config files like I did in 10.10.  While I can mask off the buttom quite easily, it also disables the right click again.

This worked with Andy Eyre's patch for 10.10 but it does not work here for some reason.  If I get a chance I was going to look back through the 2xx source files and see if there is anything there.

I will give you one hint that if you go look in the /usr/share/X11/xorg.d directory and check out some of those config files you will see similar patches for other makes of computers.  However every time I implement something similar if fixes one part but breaks the right click again.  Maybe someone can figure that one out.

For now I am starting to get used to the behavior.

---

### Post by VideoRoy on 2011-05-01
> **CTR_Cody said:**
> VideoRoy,

I just wanted to say thank you so much for making that .deb patch for my touchpad!
I'm here to report that the patch works PERFECTLY for my HP mini 210 1170NR netbook, and that you are totally awesome. You saved my right click!

I am very glad it worked out.  That is really the only quirk I have had with my mini with 10.10 or 11.04.  Ubuntu is awesome on these little guys.

---

### Post by gfgodoy on 2011-05-02
(edit)
Nervermind. Got it working by uninstalling synaptics and installing the x64 .deb posted above.
Drag and drop only works if I shut down two finger scroll.
(/edit) 

Does the steps by videoroy enable you guys the right click?
I mean it still only works by double tapping to me.

Same as it was when I first ran 11.04

Thanks in advance

---

### Post by VideoRoy on 2011-05-02
> **gfgodoy said:**
> (edit)
Nervermind. Got it working by uninstalling synaptics and installing the x64 .deb posted above.
Drag and drop only works if I shut down two finger scroll.
(/edit) 

Does the steps by videoroy enable you guys the right click?
I mean it still only works by double tapping to me.

Same as it was when I first ran 11.04

Thanks in advance

There must be some other difference here.  Right now I am only running the i386 patch on my HP 2102 and it all seems to work.  To really test it out I played 3 games of solitaire (lots of dragging and dropping).

I found it is best to click the left button first then drag your other finger on the pad.  I have a little problem with my hands so sometimes I will use 2 hands for a critical drag and drop.  Click the button with my left hand then use my right index finger to do the dragging.

---

### Post by jonhen on 2011-05-14
I've given up with this problem of not being able to right click. I don't fully understand the steps required and I'm not keen anyway in case some future update causes further issues (is that possible(?), I don't know). :confused:

Using a bt mouse for now till this patch is added to the updates. Can't understand why it's not been implemented yet.

---

### Post by tgm4883 on 2011-05-14
> **jonhen said:**
> I've given up with this problem of not being able to right click. I don't fully understand the steps required and I'm not keen anyway in case some future update causes further issues (is that possible(?), I don't know). :confused:

Using a bt mouse for now till this patch is added to the updates. Can't understand why it's not been implemented yet.

I don't know what you are talking about. This works OOTB for me in 11.04

---

### Post by AnotherMuggle on 2011-05-17
In case anyone is interested I have applied a patch to the Natty kernel (2.6.38-8-generic) and as far as I can tell all mouse features are working perfectly.  

The features I know work are:
- Left, Middle, Right Hardware Clicks
- Top to Left Button
- Two finger Tap to Right Button
- Vertical, Horizontal Scroll Regions
- Drag And Drop (both hardware and tap clicks)

I examined and ported the changes in the source provided here:
[http://bigbrovar.aoizora.org/index.php/2010/10/10/how-to-enable-right-middle-click-on-clickpads-ubuntu-10-10/]("http://bigbrovar.aoizora.org/index.php/2010/10/10/how-to-enable-right-middle-click-on-clickpads-ubuntu-10-10/")

This patch has made Natty usable on my HP Mini and it might help someone else too?  I am happy to supply the relevant files...I just need somewhere to upload them?

Tom

---

### Post by tgm4883 on 2011-05-17
> **tomkear2006 said:**
> In case anyone is interested I have applied a patch to the Natty kernel (2.6.38-8-generic) and as far as I can tell all mouse features are working perfectly.  

The features I know work are:
- Left, Middle, Right Hardware Clicks
- Top to Left Button
- Two finger Tap to Right Button
- Vertical, Horizontal Scroll Regions
- Drag And Drop (both hardware and tap clicks)

I examined and ported the changes in the source provided here:
[http://bigbrovar.aoizora.org/index.php/2010/10/10/how-to-enable-right-middle-click-on-clickpads-ubuntu-10-10/]("http://bigbrovar.aoizora.org/index.php/2010/10/10/how-to-enable-right-middle-click-on-clickpads-ubuntu-10-10/")

This patch has made Natty usable on my HP Mini and it might help someone else too?  I am happy to supply the relevant files...I just need somewhere to upload them?

Tom

How is this different from a default natty install?

As for hosting the files, you could upload them here or create a ppa

---

### Post by AnotherMuggle on 2011-05-17
> **tgm4883 said:**
> How is this different from a default natty install?

As for hosting the files, you could upload them here or create a ppa

For me, and I've seen posts by some other users, I get left click only from the clickpad on an unpatched kernel.  This patch basically adds, middle and right hardware clicks, without breaking any other functionality at the same time.

---

### Post by TimHeckman on 2011-05-22
> **tomkear2006 said:**
> For me, and I've seen posts by some other users, I get left click only from the clickpad on an unpatched kernel.  This patch basically adds, middle and right hardware clicks, without breaking any other functionality at the same time.

Fresh install of Natty running a HP Mini 210-1040NR.  I can get right click with two-finger tap.  I cannot, however, use the right mouse or a middle mouse button.  Clicking and dragging is hard to accomplish with the clickpad.  It's almost like this following kernel change was not replicated in Natty?:

- [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/516329](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/516329)

I would be in your debt if you would be able to upload the files and provide the instructions to patch the kernel.  This is driving me mad. :(

---

### Post by AnotherMuggle on 2011-05-23
> **TimHeckman said:**
> Fresh install of Natty running a HP Mini 210-1040NR.  I can get right click with two-finger tap.  I cannot, however, use the right mouse or a middle mouse button.  Clicking and dragging is hard to accomplish with the clickpad.  It's almost like this following kernel change was not replicated in Natty?:

- [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/516329](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/516329)

I would be in your debt if you would be able to upload the files and provide the instructions to patch the kernel.  This is driving me mad. :(

I will upload the files tonight along with instructions on how to apply the patch. It's very quick and easy to apply and is still working perfectly for me.

---

### Post by TimHeckman on 2011-05-23
> **tomkear2006 said:**
> I will upload the files tonight along with instructions on how to apply the patch. It's very quick and easy to apply and is still working perfectly for me.

Awesome.  I'm sorry for his newbie-like question, but it's something I've never run in to before.  I've been lucky enough that the kernel has had everything I needed.

When applying this patch what will need to be done when a new kernel version is provided from the repositories.  Do I need to put it together manually?

Thanks for throwing the instructions together.  I use my netbook as the mouse and keyboard for my system, so gimping along like this has been a bit unpleasant.

-Tim

---

### Post by AnotherMuggle on 2011-05-23
> **TimHeckman said:**
> Awesome.  I'm sorry for his newbie-like question, but it's something I've never run in to before.  I've been lucky enough that the kernel has had everything I needed.

When applying this patch what will need to be done when a new kernel version is provided from the repositories.  Do I need to put it together manually?

Thanks for throwing the instructions together.  I use my netbook as the mouse and keyboard for my system, so gimping along like this has been a bit unpleasant.

-Tim


I have attached the relevant files to this post. The patch is installed using dkms so once the patch is applied, it will remain applied even when your computer is updated with newer kernel versions.

This is what I did and I hope it works for you too (obviously I can't guarantee anything):

1. Download the attached file to your computers desktop
2. sudo apt-get install dkms build-essential
3. cd ~/Desktop
4. tar jxvf psmouse-2.6.38-8-generic.tar.bz2
5. sudo mv psmouse-2.6.38-8-generic /usr/src
6. cd /usr/src
7. sudo chmod -R a+rx psmouse-2.6.38-8-generic
8. sudo dkms add -m psmouse -v 2.6.38-8-generic
9. sudo dkms build -m psmouse -v 2.6.38-8-generic
10. sudo dkms install -m psmouse -v 2.6.38-8-generic
11. sudo shutdown -r now
12. dkms status

The output of the last command should look similar to this (with no errors):
"psmouse, 2.6.38-8-generic, 2.6.38-8-generic, i686: installed"

You can go ahead and delete the files on your desktop. If everything went well you can even right click to select "Move To Wastebasket".

Good luck!

---

### Post by TimHeckman on 2011-05-23
> **tomkear2006 said:**
> I have attached the relevant files to this post. The patch is installed using dkms so once the patch is applied, it will remain applied even when your computer is updated with newer kernel versions.

This is what I did and I hope it works for you too (obviously I can't guarantee anything):

1. Download the attached file to your computers desktop
2. sudo apt-get install dkms build-essential
3. cd ~/Desktop
4. tar jxvf psmouse-2.6.38-8-generic.tar.bz2
5. sudo mv psmouse-2.6.38-8-generic /usr/src
6. cd /usr/src
7. sudo chmod -R a+rx psmouse-2.6.38-8-generic
8. sudo dkms add -m psmouse -v 2.6.38-8-generic
9. sudo dkms build -m psmouse -v 2.6.38-8-generic
10. sudo dkms install -m psmouse -v 2.6.38-8-generic
11. sudo shutdown -r now
12. dkms status

The output of the last command should look similar to this (with no errors):
"psmouse, 2.6.38-8-generic, 2.6.38-8-generic, i686: installed"

You can go ahead and delete the files on your desktop. If everything went well you can even right click to select "Move To Wastebasket".

Good luck!

Thank you for the information.  It installed without a hitch.  I assume if I need to remove it that this will do the trick: ```
sudo dkms remove -m psmouse -v 2.6.38-8-generic
```

The only thing that does not appear to be working fully is the hardware drag and drop.  Works most of the time, but overall a flaky experience.  

Regardless, thank you for this patch. Most of the functionality of my mousepad exists now.  Using my netbook+synergy with my desktop will be enjoyable again!

---

### Post by AnotherMuggle on 2011-05-23
> **TimHeckman said:**
> Thank you for the information.  It installed without a hitch.  I assume if I need to remove it that this will do the trick: ```
sudo dkms remove -m psmouse -v 2.6.38-8-generic
```

The only thing that does not appear to be working fully is the hardware drag and drop.  Works most of the time, but overall a flaky experience.  

Regardless, thank you for this patch. Most of the functionality of my mousepad exists now.  Using my netbook+synergy with my desktop will be enjoyable again!

Good, I'm glad it's working for you :D

To completely remove the patch you can use the following commands:
1. sudo dkms uninstall -m psmouse -v 2.6.38-8-generic
2. sudo dkms remove -m psmouse -v 2.6.38-8-generic --all

I normally double tap the touchpad to drag and drop so I just tested using the hardware button.  For me, it seems fine, but you do need to press the hardware button before placing another finger on the touchpad to perform the drag.

---

### Post by TimHeckman on 2011-05-23
> **tomkear2006 said:**
> Good, I'm glad it's working for you :D

To completely remove the patch you can use the following commands:
1. sudo dkms uninstall -m psmouse -v 2.6.38-8-generic
2. sudo dkms remove -m psmouse -v 2.6.38-8-generic --all

I normally double tap the touchpad to drag and drop so I just tested using the hardware button.  For me, it seems fine, but **you do need to press the hardware button before placing another finger on the touchpad to perform the drag.**

That explains it!  After doing that it works fine.  Normally I do the double tap and drag, but it really depends on what I am doing whether that'll work or not.

Thanks again for the patch!

---

### Post by astowe32 on 2011-05-28
Works for me on my HP Mini 2105.

Thanks for the info!

  Allen...

---

### Post by fexolop on 2011-05-28
thanks great work, drag and drop needs some work but the rest is ok.

Oscar
Santiago, Chile.

---

### Post by ogranadino on 2011-05-29
Not sure why but if I use both fingers from the same hand the drag and drop movement is more difficult but fluent. This is weird.

Oscar



> **fexolop said:**
> thanks great work, drag and drop needs some work but the rest is ok.

Oscar
Santiago, Chile.

---

### Post by charliewhizbeez on 2011-05-30
> **VideoRoy said:**
> Sure, it is the one from David in post #144 only.  But here are the steps from him below.


A tarball of the patches is here (they are as similar to the SuSE patches as possible, 212-fixups.patch contains the additions to make the result compile cleanly):
[http://david.hardeman.nu/synaptics-suse-patches.tar.bz2](http://david.hardeman.nu/synaptics-suse-patches.tar.bz2)



I actually skipped the last step since I built is on a second computer but I just copied my i386 .DEB on a memory stick to my Netbook, uninstalled current Synaptics Xorg driver from Synatic Package Manager.

Next I installed my new .DEB by just clicking on it and letting Get Software install it.  Just ignore the warning.

If all goes wrong just reinstall original Xorg driver from Synaptic again.

This was a perfect step by step for me.  I am running 11.04 Desktop 32 bit on an HP 2102 (same as 210).  I cannot vouch for others.  I would post my .DEB but I do not have a way to do that.

Edit: One other comment, I had put some fixes in the /usr/share/X11/xord.d directory like I did for 10.10.  I had to remove all these because they conflicted with the new driver.



Thanks so much.  The deb a couple posts down from there is perfect.  My trackpad works perfectly :D.  Drag and drop is a little difficult, but i always just use the pad itself for that anyway.

Btw, I have a Pavilion dm4-1265dx and I'm running Ubuntu 11.04 32 bit.

THANK YOU SOOO MUCH.

---

### Post by makro on 2011-06-02
Worked for me too! Thanks

But apt-get update & apt-get upgrade try to reinstall original xserver-xorg-input-synaptics... I can't lock the package since it is the same version..

Any ideas?

---

### Post by jonhen on 2011-06-04
> **tgm4883 said:**
> I don't know what you are talking about. This works OOTB for me in 11.04

Sorry for replying to an old post but I visit this board infrequently. Let me see if I can help you here. ;)

I am running a version of 10.10 and the clickpad does not work properly OOTB, the same, it appears, as many others on here. :(

When this thread was started in January 2010 Natty wasn't around and I naively believed that this thread was still relevant to me since there were others still experiencing this problem at the time and still are. ](*,)

If it has worked OOTB for you in 11.04 that is great news and maybe I need to upgrade to 11.04, something I'd rather not have to keep doing just to get a mouse pad to work. :rolleyes:

Have a nice day. :)

---

### Post by tgm4883 on 2011-06-04
> **jonhen said:**
> Sorry for replying to an old post but I visit this board infrequently. Let me see if I can help you here. ;)

I am running a version of 10.10 and the clickpad does not work properly OOTB, the same, it appears, as many others on here. :(

When this thread was started in January 2010 Natty wasn't around and I naively believed that this thread was still relevant to me since there were others still experiencing this problem at the time and still are. ](*,)

If it has worked OOTB for you in 11.04 that is great news and maybe I need to upgrade to 11.04, something I'd rather not have to keep doing just to get a mouse pad to work. :rolleyes:

Have a nice day. :)

I've asked for this thread to be closed for that very reason (Minimally it needs retitled to be more specific). Maybe it's time others started reporting it too.

My response was aimed at you saying

> Using a bt mouse for now till this patch is added to the updates. Can't understand why it's not been implemented yet.

Basically I said that it had been implemented. 

New hardware doesn't always work on old OS's, and may require tweaking some files or adding a patch. Deal with it.

---

### Post by jonhen on 2011-06-04
> **tgm4883 said:**
> I've asked for this thread to be closed for that very reason (Minimally it needs retitled to be more specific). Maybe it's time others started reporting it too.

My response was aimed at you saying



Basically I said that it had been implemented. 

New hardware doesn't always work on old OS's, and may require tweaking some files or adding a patch. Deal with it.

I wasn't aware that it had in 11.04? If it has been implemented in 11.04 how come there are people still having issues with it? 

This isn't new hardware and 10.10 is still supported. They are of a similar era yet the Clickpad is still an issue. 

I've had to patch/tweak this OS for a number of hardware issues on a number of different computers, nothing new there then. :rolleyes: No idea what you mean by 'Deal with it.' :confused:

---

### Post by tgm4883 on 2011-06-04
> **jonhen said:**
> I wasn't aware that it had in 11.04? If it has been implemented in 11.04 how come there are people still having issues with it? 

This isn't new hardware and 10.10 is still supported. They are of a similar era yet the Clickpad is still an issue. 

I've had to patch/tweak this OS for a number of hardware issues on a number of different computers, nothing new there then. :rolleyes: No idea what you mean by 'Deal with it.' :confused:

I already said it works OOTB in 11.04. What people using 11.04 are still having an issue with it?

Correct. 10.10 is still supported. That's why you are still getting security patches. But this isn't a security patch, so it's not going to be available as an update through the official repositories. It might be, if someone decided to do a backport for it, but I honestly don't know if it even meets the criteria (then you have to find someone that cares enough to do it)

---

### Post by jonhen on 2011-06-05
As it is working OOTB for 11.04 I think I understand your frustration. 

I take your point regarding updates for 10.10. 

For now I have downloaded a patch that is easy to install and remove if necessary and that has got the multi-touch mode working for now. Here is the link to the information I used if any one is interested:

[http://bigbrovar.aoizora.org/index.php/2011/01/12/enable-multitouch-support-for-clickpad-on-ubuntu-10-10/](http://bigbrovar.aoizora.org/index.php/2011/01/12/enable-multitouch-support-for-clickpad-on-ubuntu-10-10/)

And thanks for your patience :)

---

### Post by shadowninty on 2011-06-06
Anyway to undo this?

---

### Post by gusdefrog on 2011-06-17
I'm on a hp mini 210 and no, the touchpad still didn't work "out of the box" with 11.04, it was working with the alteration of the 50-synaptics.conf adding 

Option "RBCornerButton" "2"

to it, but since the latest synaptics driver update that no longer works. >.> neither does synclient RBCornerButton=2 from the command line.

So the right button function is still an ongoing problem.

---

### Post by tgm4883 on 2011-06-17
> **gusdefrog said:**
> I'm on a hp mini 210 and no, the touchpad still didn't work "out of the box" with 11.04, it was working with the alteration of the 50-synaptics.conf adding 

Option "RBCornerButton" "2"

to it, but since the latest synaptics driver update that no longer works. >.> neither does synclient RBCornerButton=2 from the command line.

So the right button function is still an ongoing problem.

Odd, it works for me. 

Are you clicking or tapping the button?

Did you do an upgrade to 11.04 or a clean install?

---

### Post by Datura-bomb on 2011-06-19
Thanks for the fix, it worked great. Really liking Ubuntu 11.04 on my new HP Mini 210 netbook.

---

### Post by VideoRoy on 2011-06-22
> **gusdefrog said:**
> I'm on a hp mini 210 and no, the touchpad still didn't work "out of the box" with 11.04, it was working with the alteration of the 50-synaptics.conf adding 

Option "RBCornerButton" "2"

to it, but since the latest synaptics driver update that no longer works. >.> neither does synclient RBCornerButton=2 from the command line.

So the right button function is still an ongoing problem.

Correct on the HP mini 210 and 2102 it is still not working OOTB with Natty 11.04 32bit at least.

The new Xserver driver that was just provided in the last update broke my functionality again so I had to rebuild the patch with the newer sources so it would not be overwritten.  Not hard to do but still a hassle. Hopefully this will make it into the base driver.

Also one of the other users posted a setting that finally worked for my to stabilize the drag and drop even more for the Mini 210 and 2102.  BottomEdge 4000 and AreaBottomEdge 4445 added to the /usr/share/X11/xorg.confg.d/50-synaptics.conf.

The correct syntax for this is:

Option "BottomEdge" "4000"
Option "AreaBottomEdge" "4445"

This masked off part of the button so if you click a the very bottom of the button the cursor will not move while click n dragging.  As close to perfect as I have gotten now.  If you are not on the Mini versions I noted you may have to play with the area since it could be different.

Note that you can test these settings real time using synclient from terminal.  I did this first to see the functionality and verify the settings.

Word or warning!!!!  Make sure you make a copy of 50-synaptics.conf first and double check the syntax.  I made one typo which caused me to not be able to do a normal boot.  I had to go to recovery mode root console and fix my typo.

---

### Post by Jessyell on 2011-07-05
Hi,

I am new to Ubuntu (and Linux), having just installed Ubuntu 11.04 on my HP Mini 210 netbook. I entered the following command to fix the touchpad problem:

# echo options psmouse proto=exps > /etc/modprobe.d/psmouse.modprobe

This worked fine with the only problem being that an automatic click takes place when my cursor remains still for a certain amount of time - meaning that the cursor will relocate mid way through typing to wherever the cursor happens to be at the time. 

This is very annoying so I have decided to remove the psmouse.modprobe and just use the HP settings to adjust how the mouse operates.

I would very much appreciate if someone could tell me how to undo the psmouse.modprobe change in order to return the computer to its original functionality. Can anybody help me with this?

Many thanks!

---

### Post by Hubcube on 2011-07-06
Go to the directory /etc/modprobe.d/psmouse.modprobe and in the Terminal:

```
sudo rm _***drag&drop your psmouse file***_
```

It will delete the file. You have to reboot after that! :)

I let my trackpad functions as they were out of the box, so I use no physical button and I scroll and right-click with two fingers. ;)

---

### Post by Jessyell on 2011-07-06
> **Hubcube said:**
> Go to the directory /etc/modprobe.d/psmouse.modprobe and in the Terminal:

```
sudo rm _***drag&drop your psmouse file***_
```It will delete the file. You have to reboot after that! :)

I let my trackpad functions as they were out of the box, so I use no physical button and I scroll and right-click with two fingers. ;)

Too easy, thanks Hubcube! Problem solved.

---

### Post by stonr on 2011-07-15
> **tomkear2006 said:**
> I have attached the relevant files to this post. The patch is installed using dkms so once the patch is applied, it will remain applied even when your computer is updated with newer kernel versions.

This is what I did and I hope it works for you too (obviously I can't guarantee anything):

1. Download the attached file to your computers desktop
2. sudo apt-get install dkms build-essential
3. cd ~/Desktop
4. tar jxvf psmouse-2.6.38-8-generic.tar.bz2
5. sudo mv psmouse-2.6.38-8-generic /usr/src
6. cd /usr/src
7. sudo chmod -R a+rx psmouse-2.6.38-8-generic
8. sudo dkms add -m psmouse -v 2.6.38-8-generic
9. sudo dkms build -m psmouse -v 2.6.38-8-generic
10. sudo dkms install -m psmouse -v 2.6.38-8-generic
11. sudo shutdown -r now
12. dkms status

The output of the last command should look similar to this (with no errors):
"psmouse, 2.6.38-8-generic, 2.6.38-8-generic, i686: installed"

You can go ahead and delete the files on your desktop. If everything went well you can even right click to select "Move To Wastebasket".

Good luck!

installed in less than 2 minutes, including restart. thanks! now my Mini 210 w/SSD is reasonable to use without a mouse.

---

### Post by Abu Nadifa on 2011-07-15
Dear All,

Solution from tomkear2006, post #224 work for me.
Now my HP Mini 210 right click is working perfectly. :P :P :P

---

### Post by kolicha on 2011-07-22
> **tomkear2006 said:**
> I have attached the relevant files to this post. The patch is installed using dkms so once the patch is applied, it will remain applied even when your computer is updated with newer kernel versions.

This is what I did and I hope it works for you too (obviously I can't guarantee anything):

1. Download the attached file to your computers desktop
2. sudo apt-get install dkms build-essential
3. cd ~/Desktop
4. tar jxvf psmouse-2.6.38-8-generic.tar.bz2
5. sudo mv psmouse-2.6.38-8-generic /usr/src
6. cd /usr/src
7. sudo chmod -R a+rx psmouse-2.6.38-8-generic
8. sudo dkms add -m psmouse -v 2.6.38-8-generic
9. sudo dkms build -m psmouse -v 2.6.38-8-generic
10. sudo dkms install -m psmouse -v 2.6.38-8-generic
11. sudo shutdown -r now
12. dkms status

The output of the last command should look similar to this (with no errors):
"psmouse, 2.6.38-8-generic, 2.6.38-8-generic, i686: installed"

You can go ahead and delete the files on your desktop. If everything went well you can even right click to select "Move To Wastebasket".

Good luck!

Hi, I used this thread about 10 months ago to fix the right click with one finger vertical scroll on my HP mini 210. However, a recent update has reverted the solution I used to change it. I tried the above but I get the following when using dkms build:

```
:/usr/src$ sudo dkms build -m psmouse -v 2.6.38-8-generic

Kernel preparation unnecessary for this kernel.  Skipping...

Building module:
cleaning build area....
make KERNELRELEASE=2.6.32-33-generic -C /lib/modules/2.6.32-33-generic/build M=/var/lib/dkms/psmouse/2.6.38-8-generic/build/src psmouse.ko....(bad exit status: 2)

Error! Bad return status for module build on kernel: 2.6.32-33-generic (i686)
Consult the make.log in the build directory
/var/lib/dkms/psmouse/2.6.38-8-generic/build/ for more information.
0
0
ERROR: binary package for psmouse: 2.6.38-8-generic not found

```

The make.log contains:
```
DKMS make.log for psmouse-2.6.38-8-generic for kernel 2.6.32-33-generic (i686)
Fri Jul 22 19:07:06 BST 2011
make: Entering directory `/usr/src/linux-headers-2.6.32-33-generic'
  CC [M]  /var/lib/dkms/psmouse/2.6.38-8-generic/build/src/psmouse-base.o
/var/lib/dkms/psmouse/2.6.38-8-generic/build/src/psmouse-base.c:44: error: variable ‘param_ops_proto_abbrev’ has initializer /var/lib/dkms/psmouse/2.6.38-8-generic/build/src/psmouse-base.c:45: error: unknown field ‘set’ specified in initializer
/var/lib/dkms/psmouse/2.6.38-8-generic/build/src/psmouse-base.c:45: warning: excess elements in struct initializer
/var/lib/dkms/psmouse/2.6.38-8-generic/build/src/psmouse-base.c:45: warning: (near initialization for ‘param_ops_proto_abbrev
/var/lib/dkms/psmouse/2.6.38-8-generic/build/src/psmouse-base.c:46: error: unknown field ‘get’ specified in initializer
/var/lib/dkms/psmouse/2.6.38-8-generic/build/src/psmouse-base.c:46: warning: excess elements in struct initializer
/var/lib/dkms/psmouse/2.6.38-8-generic/build/src/psmouse-base.c:46: warning: (near initialization for ‘param_ops_proto_abbrev
/var/lib/dkms/psmouse/2.6.38-8-generic/build/src/psmouse-base.c:49: error: ‘param_set_proto_abbrev’ undeclared here (not in a
/var/lib/dkms/psmouse/2.6.38-8-generic/build/src/psmouse-base.c:49: error: ‘param_get_proto_abbrev’ undeclared here (not in a/var/lib/dkms/psmouse/2.6.38-8-generic/build/src/psmouse-base.c: In function ‘psmouse_attr_set_protocol’:
/var/lib/dkms/psmouse/2.6.38-8-generic/build/src/psmouse-base.c:1587: error: ‘struct serio’ has no member named ‘children’
make[1]: *** [/var/lib/dkms/psmouse/2.6.38-8-generic/build/src/psmouse-base.o] Error 1
make: *** [psmouse.ko] Error 2
make: Leaving directory `/usr/src/linux-headers-2.6.32-33-generic'

```

I'm running Ubuntu 10.04 with kernel 2.6.32-33-generic

Does anyone know how to fix this? I'll also make my way through the previous solutions to see if I can find the one I originally used. 

Many thanks

---

### Post by kolicha on 2011-07-22
> **kolicha said:**
> Hi, I used this thread about 10 months ago to fix the right click with one finger vertical scroll on my HP mini 210. However, a recent update has reverted the solution I used to change it. I tried the above but I get the following when using dkms build:

```
:/usr/src$ sudo dkms build -m psmouse -v 2.6.38-8-generic

Kernel preparation unnecessary for this kernel.  Skipping...

Building module:
cleaning build area....
make KERNELRELEASE=2.6.32-33-generic -C /lib/modules/2.6.32-33-generic/build M=/var/lib/dkms/psmouse/2.6.38-8-generic/build/src psmouse.ko....(bad exit status: 2)

Error! Bad return status for module build on kernel: 2.6.32-33-generic (i686)
Consult the make.log in the build directory
/var/lib/dkms/psmouse/2.6.38-8-generic/build/ for more information.
0
0
ERROR: binary package for psmouse: 2.6.38-8-generic not found

```

The make.log contains:
```
DKMS make.log for psmouse-2.6.38-8-generic for kernel 2.6.32-33-generic (i686)
Fri Jul 22 19:07:06 BST 2011
make: Entering directory `/usr/src/linux-headers-2.6.32-33-generic'
  CC [M]  /var/lib/dkms/psmouse/2.6.38-8-generic/build/src/psmouse-base.o
/var/lib/dkms/psmouse/2.6.38-8-generic/build/src/psmouse-base.c:44: error: variable ‘param_ops_proto_abbrev’ has initializer /var/lib/dkms/psmouse/2.6.38-8-generic/build/src/psmouse-base.c:45: error: unknown field ‘set’ specified in initializer
/var/lib/dkms/psmouse/2.6.38-8-generic/build/src/psmouse-base.c:45: warning: excess elements in struct initializer
/var/lib/dkms/psmouse/2.6.38-8-generic/build/src/psmouse-base.c:45: warning: (near initialization for ‘param_ops_proto_abbrev
/var/lib/dkms/psmouse/2.6.38-8-generic/build/src/psmouse-base.c:46: error: unknown field ‘get’ specified in initializer
/var/lib/dkms/psmouse/2.6.38-8-generic/build/src/psmouse-base.c:46: warning: excess elements in struct initializer
/var/lib/dkms/psmouse/2.6.38-8-generic/build/src/psmouse-base.c:46: warning: (near initialization for ‘param_ops_proto_abbrev
/var/lib/dkms/psmouse/2.6.38-8-generic/build/src/psmouse-base.c:49: error: ‘param_set_proto_abbrev’ undeclared here (not in a
/var/lib/dkms/psmouse/2.6.38-8-generic/build/src/psmouse-base.c:49: error: ‘param_get_proto_abbrev’ undeclared here (not in a/var/lib/dkms/psmouse/2.6.38-8-generic/build/src/psmouse-base.c: In function ‘psmouse_attr_set_protocol’:
/var/lib/dkms/psmouse/2.6.38-8-generic/build/src/psmouse-base.c:1587: error: ‘struct serio’ has no member named ‘children’
make[1]: *** [/var/lib/dkms/psmouse/2.6.38-8-generic/build/src/psmouse-base.o] Error 1
make: *** [psmouse.ko] Error 2
make: Leaving directory `/usr/src/linux-headers-2.6.32-33-generic'

```

I'm running Ubuntu 10.04 with kernel 2.6.32-33-generic

Does anyone know how to fix this? I'll also make my way through the previous solutions to see if I can find the one I originally used. 

Many thanks
OK sorted. The solution on page 6 that I used last time no longer works. However, following:

[http://bigbrovar.aoizora.org/index.php/2010/10/10/how-to-enable-right-middle-click-on-clickpads-ubuntu-10-10/](http://bigbrovar.aoizora.org/index.php/2010/10/10/how-to-enable-right-middle-click-on-clickpads-ubuntu-10-10/)

worked for me. I.E. removing psmouse-2.6.38-8-generic (with the remove parameter) and using the earlier psmouse-2.6.35-22-generic instead.

Note: I haven't seen a change log so I'm not sure what changes are missing from the earlier version.

Hope this helps anyone with a similar problem to me.

---

### Post by mdl4 on 2011-07-22
I had a really bad time hunting down the fix for this issue following the update to 11.04, but I found VideoRoy's suggestion helpful ([#202]("http://ubuntuforums.org/showpost.php?p=10744640&postcount=202")). When I also modified my psmouse.modprobe file with the following command, everything worked perfectly on my HP Mini.

```
sudo echo options psmouse proto=exps > /etc/modprobe.d/psmouse.modprobe
```

I put together a .deb file that combines everything into a complete fix for anyone who's interested:

_[Fix your HP Mini&#8217;s Touchpad in Ubuntu 11.04]("http://www.mdl4.com/2011/07/fix-your-hp-mini-mouse-in-ubuntu-11-04/")_

Hope it's helpful/timesaving for someone.

---

### Post by karla0nlinux on 2011-07-25
Hi, I have the same problem as Kolicha - I am also running 10.4 and a recent update messed up my touchpad settings.  I used the bigbrovar fix suggested, but my vertical scrolling is still dead.  Help, please!

---

### Post by Gremlyn1 on 2011-07-26
> **mdl4 said:**
> I had a really bad time hunting down the fix for this issue following the update to 11.04, but I found VideoRoy's suggestion helpful ([#202]("http://ubuntuforums.org/showpost.php?p=10744640&postcount=202")). When I also modified my psmouse.modprobe file with the following command, everything worked perfectly on my HP Mini.

```
sudo echo options psmouse proto=exps > /etc/modprobe.d/psmouse.modprobe
```

I put together a .deb file that combines everything into a complete fix for anyone who's interested:

_[Fix your HP Mini&#8217;s Touchpad in Ubuntu 11.04]("http://www.mdl4.com/2011/07/fix-your-hp-mini-mouse-in-ubuntu-11-04/")_

Hope it's helpful/timesaving for someone.

Asked on your site as well, but should this only be used for the HP Mini, or can any HP laptop, or even any device with the clickpad work?

EDIT: NM, this won't work for 10.04 :(

---

### Post by tuchedsf on 2011-07-26
thank you... Resolvido o meu problema no Touchpad..... Very Nice...Excelent....

---

### Post by predikt on 2011-07-28
> **Sabot said:**
> To get the trackpad working correctly you need to use the terminal and enter in the below commands. Make sure you press enter after each command:

    ```
sudo su
```

    ```
echo options psmouse proto=exps > /etc/modprobe.d/psmouse.modprobe
```

    ```
reboot
```


Once the computer reboots your trackpad will be able to do left click and drag and right clicking.


Thanks so much. This worked perfect on my HP Pavilion dv7.

What's proto=exps?

---

### Post by Neo Napster on 2011-08-15
> **tomkear2006 said:**
> I have attached the relevant files to this post. The patch is installed using dkms so once the patch is applied, it will remain applied even when your computer is updated with newer kernel versions.

This is what I did and I hope it works for you too (obviously I can't guarantee anything):

1. Download the attached file to your computers desktop
2. sudo apt-get install dkms build-essential
3. cd ~/Desktop
4. tar jxvf psmouse-2.6.38-8-generic.tar.bz2
5. sudo mv psmouse-2.6.38-8-generic /usr/src
6. cd /usr/src
7. sudo chmod -R a+rx psmouse-2.6.38-8-generic
8. sudo dkms add -m psmouse -v 2.6.38-8-generic
9. sudo dkms build -m psmouse -v 2.6.38-8-generic
10. sudo dkms install -m psmouse -v 2.6.38-8-generic
11. sudo shutdown -r now
12. dkms status

The output of the last command should look similar to this (with no errors):
"psmouse, 2.6.38-8-generic, 2.6.38-8-generic, i686: installed"

You can go ahead and delete the files on your desktop. If everything went well you can even right click to select "Move To Wastebasket".

Good luck!

This worked like a charm on my HP Pavilion dm-4 installed with Ubuntu 11.04 64-bit. Thanks!:D

---

### Post by AnotherMuggle on 2011-08-16
> **Neo Napster said:**
> This worked like a charm on my HP Pavilion dm-4 installed with Ubuntu 11.04 64-bit. Thanks!:D

Glad to hear it.  Mine is still working perfectly too.  I actually find my touchpad more comfortable in Ubuntu than in Windows now.

---

### Post by jagan185 on 2011-09-01
This fixed the issue with right click, now edge scrolling is not functioning on my hp mini 210 with Ubuntu 10.04

---

### Post by tgm4883 on 2011-09-01
> **jagan185 said:**
> This fixed the issue with right click, now edge scrolling is not functioning on my hp mini 210 with Ubuntu 10.04

Yep, did you read the entire thread?

---

### Post by cdufour on 2011-09-15
Hello,

On Debian/Squeeze 64-bit, applying patch from [http://ubuntuforums.org/showpost.php?p=8989185&postcount=11](http://ubuntuforums.org/showpost.php?p=8989185&postcount=11) - with NO other modifications (niether to /etc/modprobe.d nor /etc/udev.d) - allowed me to successfully fix my HP Mini 210's touchpad (iow. working right button, right-edge scroll and no more erratic behavior when selecting+dragging)

I compiled a DKMS package - based on the (Debian) 2.6.32 mouse driver source - that should take the hassle off of installing the updated driver (psmouse.ko) and keeping it up-to-date as the kernel gets updated. See attached tarball.
PS: For those who wonder what DKMS is: DKMS stand for Dynamic Kernel Module Support and is an elegant way of installing/maintaining an additional or modified driver for the installed kernel(s). As new kernels get installed, DKMS will automatically kick in and recompile/install the driver for it.

Installation:
```
tar -xjf psmouse-*.deb.tar.bz2
sudo dpkg -i psmouse-*.deb

```Cheers

---

### Post by Megastar12 on 2011-09-15
[COLOR=#333333][FONT=arial]Everything else works fine. The left mouse click, the scrolling function and the zoom-in, zoom-out.

Whenever I touch the right mouse click area it does a left mouse click. Very frustrating.

This netbook is only a few days old, it hasn't worked since I got it. Still has the original Windows OS.

[LIST]
[*]1 year ago 
[*](Tiebreaker)
[/LIST]
:p:p:p:p




[Watch TV Online]("http://www.goonlinetv.com")
[watch online tv ]("http://www.goonlinetv.com")

[/FONT][/COLOR]

---

### Post by dannyauble on 2011-09-27
I got good functionality with 11.10 by following the instructions in the Background section of [http://www.mdl4.com/2011/07/fix-your-hp-mini-mouse-in-ubuntu-11-04/](http://www.mdl4.com/2011/07/fix-your-hp-mini-mouse-in-ubuntu-11-04/)

Attached is an altered patch file that will work on the new synaptics.  If you are running 11.04 the one on the link above will probably work, but I didn't test.

This made the right click work and the slide scroll.  No dragging, but that wasn't as big of a deal for me.

---

### Post by Frysboxen on 2011-10-14
After reading the bug-report I found a PPA with a patched xserver-xorg-input-synaptics package.
The PPA is located over at [https://launchpad.net/~sergio91pt/+archive/synaptics+clickpads](https://launchpad.net/~sergio91pt/+archive/synaptics+clickpads) .

To install:
```

sudo add-apt-repository ppa:sergio91pt/synaptics+clickpads [CODE]
```
sudo apt-get update
sudo apt-get upgrade
[/CODE]

in case of any problems, try removing the orld xserver-xorg-input-synaptics with apt-get remove, and try the procedure above again.

What's working in this version:
*edge-scrolling
*click-and-drag

What's not working:
*two-finger-scroll
*touchpad on/off in top-left corner (only on some HP models)

Hope this was helpful.

---

### Post by jwp1 on 2011-10-17
I am pretty upset.
I do not often get upset in Linux as its free and if it does not work I just find a distro that did work.

I had heard ubuntu 11.10 had some new features with ubuntu one.
I had been running 11.04 Xubuntu and got the track pad to work fine using this page [http://www.mdl4.com/2011/07/fix-your-hp-mini-mouse-in-ubuntu-11-04/#more-929](http://www.mdl4.com/2011/07/fix-your-hp-mini-mouse-in-ubuntu-11-04/#more-929)

With some fear I upgraded hoping the mouse issue would be easy to fix as in the past.

But when I use the software center it will not allow for the deb file to be installed like wise I had to install a package manager and it would not install it either.  They say that the file is newer.

I tired to do it via the console with the commands listed it says this

sudo echo options psmouse proto=exps > /etc/modprobe.d/psmouse.modprobe
bash: /etc/modprobe.d/psmouse.modprobe: Permission denied

Why I have no idea.  Why can ubuntu as a company not just sell driver for the HP Mini 210 there are about a million of them out there? They have the software center and I would be willing to pay something just not to have to go through this.

---

### Post by tgm4883 on 2011-10-17
> **jwp1 said:**
> I am pretty upset.
I do not often get upset in Linux as its free and if it does not work I just find a distro that did work.

I had heard ubuntu 11.10 had some new features with ubuntu one.
I had been running 11.04 Xubuntu and got the track pad to work fine using this page [http://www.mdl4.com/2011/07/fix-your-hp-mini-mouse-in-ubuntu-11-04/#more-929](http://www.mdl4.com/2011/07/fix-your-hp-mini-mouse-in-ubuntu-11-04/#more-929)

With some fear I upgraded hoping the mouse issue would be easy to fix as in the past.

But when I use the software center it will not allow for the deb file to be installed like wise I had to install a package manager and it would not install it either.  They say that the file is newer.

I tired to do it via the console with the commands listed it says this

sudo echo options psmouse proto=exps > /etc/modprobe.d/psmouse.modprobe
bash: /etc/modprobe.d/psmouse.modprobe: Permission denied

Why I have no idea.  Why can ubuntu as a company not just sell driver for the HP Mini 210 there are about a million of them out there? They have the software center and I would be willing to pay something just not to have to go through this.

So I really urge you to not run commands if you don't understand whats going on, even at a basic level. 

```

sudo nano /etc/modprobe.d/psmouse.modprobe

```

Then add

```
options psmouse proto=exps
```

Then save it

---

### Post by AnotherMuggle on 2011-10-17
In case anyone is interested (I know some people had success) I have applied the same patch as I posted in #224 of this thread, to the default kernel in 11.10 (Oneiric Ocelot).  This is working perfectly for me on the 64bit version.  Follow the instructions as in post #224 swapping out the new kernel version for each command.

---

### Post by alexuk86 on 2011-10-29
> **tomkear2006 said:**
> In case anyone is interested (I know some people had success) I have applied the same patch as I posted in #224 of this thread, to the default kernel in 11.10 (Oneiric Ocelot).  This is working perfectly for me on the 64bit version.  Follow the instructions as in post #224 swapping out the new kernel version for each command.


Confirmed. This works for me too on a HP DM1-3020us in ubuntu 11.10 64bit :D

---

### Post by Rgibbons on 2011-10-30
Fantastic. Works like a charm.

---

### Post by marcellux on 2011-11-07
awesome!! I was having exactly the same problem, but with HP dv6!! Thanks a lot for the big help!!!

---

### Post by marcellux on 2011-11-10
hi,
so, the touchpad is working fine. does anyone know how to get rid off the message on system startup "no touchpad found"?
thanks in advance

---

### Post by the pwner224 on 2011-11-25
Hi,
I just joined this forum about 2 minutes ago. I have an HP Mini 201-1041nr. I had 11.04 and now have Oneiric Ocelot. On both versions, the mouse worked but the left click button didnt work. I could scroll with two fingers, click by tapping, and right click by tapping with two fingers. However, if I use the left click button, the mouse still moves around on the screen, and the right click button does a left click. I have only read the first few pages of the thread because I do not have much time right now, so can someone please post the best solution to this problem?
The dot in the top left that disables/enables the touchpad when double clicked is also not working anymore.

Also, is the Pavilion dv7 compatible with Ubuntu? I have tried installing many times, but the installer does not work and Wubi is also not working. I have just shipped it to HP for repair (it fell down the stairs, but i had the 4 year warranty that includes accidental damage), and will try reinstalling when it gets back.

---

### Post by insession on 2011-12-09
I had a similar problem and fixed it with this:

"```
sudo add-apt-repository ppa:sergio91pt/synaptics+clickpads
sudo apt-get update
sudo apt-get install xserver-xorg-input-synaptics
```

Then reboot your computer so it can be loaded into the Kernel"

Source: [http://pessetto.com/question2answer/index.php?qa=52&qa_1=ubuntu-11-10-clickpad-not-working-right-click-not-working](http://pessetto.com/question2answer/index.php?qa=52&qa_1=ubuntu-11-10-clickpad-not-working-right-click-not-working)

Now I have:
1) Right click
2) click and drag
3) two-finger scrolling
4) edge scrolling

I can't disable the touchpad on the top left (I have an hp pavilion dv5).

I'm not sure if I can attribute these results to just this patch since I tried a few different fixes before I found this, but it did fix the right click and click and drag problem for me.

Let us know your results.

---

### Post by the pwner224 on 2011-12-09
Thanks. I was pulling my charger out of the laptop and it got bent and then broke. I ordered a new one that should come on Monday or Tuesday. I will try this when the new charger comes.

---

### Post by ptoche on 2011-12-09
I have an HP-DV6 and I was hoping these patches would work for me. I have tried this:[FONT=monospace]

[/FONT]```

sudo add-apt-repository ppa:sergio91pt/synaptics+clickpads sudo apt-get update
sudo apt-get upgrade

```didn't do anything here ... still no right-click ...

will try some of the other patches now, fingers crossed.

Edit:

This worked!

```

1. Download psmouse-3.0.0-12-generic.tar.bz2
2. sudo apt-get install dkms build-essential
3. cd /home/downloads
4. tar jxvf psmouse-3.0.0-12-generic.tar.bz2
5. sudo mv psmouse-3.0.0-12-generic /usr/src
6. cd /usr/src
7. sudo chmod -R a+rx psmouse-3.0.0-12-generic
8. sudo dkms add -m psmouse -v 3.0.0-12-generic
9. sudo dkms build -m psmouse -v 3.0.0-12-generic
10. sudo dkms install -m psmouse -v 3.0.0-12-generic
11. sudo shutdown -r now
12. dkms status

```

Thank you very much for a great contribution. This patch works very well, on an HP-DV6 and Kubuntu 11.10. I'd been looking for a fix for a few days, this is my fifth attempt to patch, so fifth time lucky.

---

### Post by JohnnyB98604 on 2011-12-10
> **insession said:**
> I had a similar problem and fixed it with this:

"```
sudo add-apt-repository ppa:sergio91pt/synaptics+clickpads
sudo apt-get update
sudo apt-get install xserver-xorg-input-synaptics
```

Then reboot your computer so it can be loaded into the Kernel"

Source: [http://pessetto.com/question2answer/index.php?qa=52&qa_1=ubuntu-11-10-clickpad-not-working-right-click-not-working](http://pessetto.com/question2answer/index.php?qa=52&qa_1=ubuntu-11-10-clickpad-not-working-right-click-not-working)

Now I have:
1) Right click
2) click and drag
3) two-finger scrolling
4) edge scrolling

I can't disable the touchpad on the top left (I have an hp pavilion dv5).

I'm not sure if I can attribute these results to just this patch since I tried a few different fixes before I found this, but it did fix the right click and click and drag problem for me.

Let us know your results.

I've just installed this per your instructions and now have a nearly fully functional touchpad on my HP Pavilion dm4.  I still don't have the support for disabling the toucpad by tapping the upper left corner (as you've already stated) but everything else I use is supported now.

Thank you very much for your post.  I know there's a very simple utility for disabling the touchpad...I read about it in another thread.  I may just use that for now.

---

### Post by sap2011 on 2011-12-11
I have a HP mini laptop and I was facing the same problem. To fix this, I ran this command on the command prompt.

$ sudo echo options psmouse proto=exps > /etc/modprobe.d/psmouse.modprobe

After this, my touchpad itself stopped working. Now I can't move the pointer and can't use either of the clicks.

What can I do to revert my PC to the earlier state? Please note that I am a complete noob when it comes to Linux, so it will be great if your instructions are in details.

Cheers,
Saurabh.

edit : I tried to run this command from post 271
sudo add-apt-repository ppa:sergio91pt/synaptics+clickpads sudo apt-get update sudo apt-get install xserver-xorg-input-synaptics
but this didn't help me. I am getting this error after running second line. 

E: Could not get lock /var/lib/apt/lists/lock - open (11: Resource temporarily unavailable)
E: Unable to lock directory /var/lib/apt/lists/

---

### Post by tgm4883 on 2011-12-11
> **sap2011 said:**
> I have a HP mini laptop and I was facing the same problem. To fix this, I ran this command on the command prompt.

$ sudo echo options psmouse proto=exps > /etc/modprobe.d/psmouse.modprobe

After this, my touchpad itself stopped working. Now I can't move the pointer and can't use either of the clicks.

What can I do to revert my PC to the earlier state? Please note that I am a complete noob when it comes to Linux, so it will be great if your instructions are in details.


_**Don't run commands you find on the internet unless you know what they do.**_

I've already explained this once in this thread, I don't give instructions again. You can revert it rather easily if you figure out what 'echo' and '>' does in the command you ran.

---

### Post by JohnnyB98604 on 2011-12-11
> **JohnnyB98604 said:**
> I've just installed this per your instructions and now have a nearly fully functional touchpad on my HP Pavilion dm4.  I still don't have the support for disabling the toucpad by tapping the upper left corner (as you've already stated) but everything else I use is supported now.

Thank you very much for your post.  I know there's a very simple utility for disabling the touchpad...I read about it in another thread.  I may just use that for now.

I tried the other utility, and it didn't work. I'm not savvy enough with Ubuntu to sort out the error message... (I don't want to risk the ridicule either, someone may have already answered the question!)

---

### Post by sap2011 on 2011-12-12
> **tgm4883 said:**
> _**Don't run commands you find on the internet unless you know what they do.**_

I've already explained this once in this thread, I don't give instructions again. You can revert it rather easily if you figure out what 'echo' and '>' does in the command you ran.

Thanks for your reply. Its true that running any code that is available  online is not advisable and one must not do that, But when you don't  know anything about linux and there are so many different solutions given, I had to try something.
About that reverting to earlier state, I don't know how this can be done. And while I was busy checking solution for this problem, it seems I didn't realise that there is no sound as well. :-(


Saurabh.

---

### Post by tgm4883 on 2011-12-12
> **sap2011 said:**
> Thanks for your reply. Its true that running any code that is available  online is not advisable and one must not do that, But when you don't  know anything about linux and there are so many different solutions given, I had to try something.
About that reverting to earlier state, I don't know how this can be done. And while I was busy checking solution for this problem, it seems I didn't realise that there is no sound as well. :-(


Saurabh.

I told you exactly what to research. You need to know what '[echo]("http://unixhelp.ed.ac.uk/CGI/man-cgi?echo")' and '[>]("http://tldp.org/LDP/abs/html/io-redirection.html")' (an i/o redirector) do. I can't help more than that unless you have a specific question about either of those commands (or the command you ran). By specific, I don't mean "what does echo do".


As for the sound issue. What you did would have zero impact on sound.

---

### Post by sap2011 on 2011-12-13
> **tgm4883 said:**
> I told you exactly what to research. You need to know what '[echo]("http://unixhelp.ed.ac.uk/CGI/man-cgi?echo")' and '[>]("http://tldp.org/LDP/abs/html/io-redirection.html")' (an i/o redirector) do. I can't help more than that unless you have a specific question about either of those commands (or the command you ran). By specific, I don't mean "what does echo do".


As for the sound issue. What you did would have zero impact on sound.


Thanks for your help my dear friend. My English has failed me. I tried my best to tell you that I don't understand anything, echo and > and < and all that. English Literature is my subject and if you have any queries ( for example, who were graveyard poets and who were university wits, then may be I can help you) please feel free to ask me.

As for my problem, I have tried so many solutions, I think reinstall would be a better choice. Or may be I will have to go back to that window through which I came here. :-(

Saurabh

---

### Post by tgm4883 on 2011-12-13
> **sap2011 said:**
> Thanks for your help my dear friend. My English has failed me. I tried my best to tell you that I don't understand anything, echo and > and < and all that. English Literature is my subject and if you have any queries ( for example, who were graveyard poets and who were university wits, then may be I can help you) please feel free to ask me.

As for my problem, I have tried so many solutions, I think reinstall would be a better choice. Or may be I will have to go back to that window through which I came here. :-(

Saurabh

:roll: Don't give me the "my English has failed me" story, I told you exactly what to search for and what it is called. I even linked to relevant web pages that had the information you are looking for. Just stop this passive aggressive BS. Please do at least the slightest bit of research on the commands you find on the internet _**BEFORE**_ you run it on your machine. Otherwise the next command you run might destroy your machine. It's not like the command you ran was super complicated, there are basically 3 things you need to research, but let me spoon feed you.

sudo 
From [http://linux.die.net/man/8/sudo](http://linux.die.net/man/8/sudo)
> sudo, sudoedit - execute a command as another user

echo
From [http://unixhelp.ed.ac.uk/CGI/man-cgi?echo](http://unixhelp.ed.ac.uk/CGI/man-cgi?echo)
> echo - display a line of text

>
[http://tldp.org/LDP/abs/html/io-redirection.html](http://tldp.org/LDP/abs/html/io-redirection.html)
> 1>filename
      # Redirect stdout to file "filename."

So using that knowledge, and looking at the command you ran

```
sudo echo options psmouse proto=exps > /etc/modprobe.d/psmouse.modprobe
```

you see that while running as another user (in this case, root) you used echo to redirect "options psmouse proto=exps" to the file /etc/modprobe.d/psmouse.modprobe

To reverse that you will need to edit that file (/etc/modprobe.d/psmouse.modprobe) and remove the line (the last line, honestly probably the only line) that says "options psmouse proto=exps". Then reboot the machine.

Any other issues you are having (eg. your no sound issue) was likely caused by a different command that you got from the internet and failed to research properly.

---

### Post by sap2011 on 2011-12-14
:-)

Looks like I had been taking things for granted. Apology. But even after spending more than two hours, using provided information, if you can't find a single easy way to revert, things do seem frustrating. 

Anyways, I had shared my problem with my friend and he [FONT=courier new]advised me to delete that [/FONT][FONT=courier new]psmouse.modprobe[/FONT] file and run the code which I had tried earlier but with some changes.

[FONT=courier new]sudo echo options psmouse proto=exps > /etc/modprobe.d/psmouse.modprobe[/FONT]
[FONT=courier new]
Changed code :

[/FONT][FONT=courier new]sudo [/FONT][FONT=courier new]echo options psmouse proto=imps[/FONT][FONT=courier new] > /etc/modprobe.d/psmouse.modprobe[/FONT]

And that was it. Now my touchpad is working but seems a bit hyperactive. thats all.

And after doing this, even sound is working now. Don't know what happened. 

Thank you for taking time to help me. [FONT=courier new]

Saurabh
[/FONT]

---

### Post by barakatax on 2011-12-19
```

1. Download psmouse-3.0.0-12-generic.tar.bz2
2. sudo apt-get install dkms build-essential
3. cd /home/downloads
4. tar jxvf psmouse-3.0.0-12-generic.tar.bz2
5. sudo mv psmouse-3.0.0-12-generic /usr/src
6. cd /usr/src
7. sudo chmod -R a+rx psmouse-3.0.0-12-generic
8. sudo dkms add -m psmouse -v 3.0.0-12-generic
9. sudo dkms build -m psmouse -v 3.0.0-12-generic
10. sudo dkms install -m psmouse -v 3.0.0-12-generic
11. sudo shutdown -r now
12. dkms status

```
Confirmed work on HP Mini 210 - 1002TU.
Thank you for the patch. ;)

---

### Post by tricolorpoa on 2011-12-22
> **insession said:**
> I had a similar problem and fixed it with this:

"```
sudo add-apt-repository ppa:sergio91pt/synaptics+clickpads
sudo apt-get update
sudo apt-get install xserver-xorg-input-synaptics
```Then reboot your computer so it can be loaded into the Kernel"

Source: [http://pessetto.com/question2answer/index.php?qa=52&qa_1=ubuntu-11-10-clickpad-not-working-right-click-not-working](http://pessetto.com/question2answer/index.php?qa=52&qa_1=ubuntu-11-10-clickpad-not-working-right-click-not-working)

Now I have:
1) Right click
2) click and drag
3) two-finger scrolling
4) edge scrolling

I can't disable the touchpad on the top left (I have an hp pavilion dv5).

I'm not sure if I can attribute these results to just this patch since I tried a few different fixes before I found this, but it did fix the right click and click and drag problem for me.

Let us know your results.




This works!!
Thanks!
Ubuntu 11.10 x86_64 kernel 3.0.0-14-generic

---

### Post by Riehlthing on 2012-01-22
> **tomkear2006 said:**
> I have attached the relevant files to this post. The patch is installed using dkms so once the patch is applied, it will remain applied even when your computer is updated with newer kernel versions.

This is what I did and I hope it works for you too (obviously I can't guarantee anything):

1. Download the attached file to your computers desktop
2. sudo apt-get install dkms build-essential
3. cd ~/Desktop
4. tar jxvf psmouse-2.6.38-8-generic.tar.bz2
5. sudo mv psmouse-2.6.38-8-generic /usr/src
6. cd /usr/src
7. sudo chmod -R a+rx psmouse-2.6.38-8-generic
8. sudo dkms add -m psmouse -v 2.6.38-8-generic
9. sudo dkms build -m psmouse -v 2.6.38-8-generic
10. sudo dkms install -m psmouse -v 2.6.38-8-generic
11. sudo shutdown -r now
12. dkms status

The output of the last command should look similar to this (with no errors):
"psmouse, 2.6.38-8-generic, 2.6.38-8-generic, i686: installed"

You can go ahead and delete the files on your desktop. If everything went well you can even right click to select "Move To Wastebasket".

Good luck!

I've been reading over this thread, to get right click functionality on my HP Laptop, and so far only have gotten partially to normal use.  I tried this, and at step 9, I get an error stating "bad return status on module...".  I was hoping to just get right click, and no tap to click on the touchpad part itself.

---

### Post by Martin Cronje on 2012-02-03
> **Sabot said:**
> To get the trackpad working correctly you need to use the terminal and enter in the below commands. Make sure you press enter after each command:

    ```
sudo su
```

    ```
echo options psmouse proto=exps > /etc/modprobe.d/psmouse.modprobe
```

    ```
reboot
```


Once the computer reboots your trackpad will be able to do left click and drag and right clicking.

How do you undo this? This leaves my mousepad without any multi-touching options

---

### Post by tgm4883 on 2012-02-04
> **Martin Cronje said:**
> How do you undo this? This leaves my mousepad without any multi-touching options

Read the thread backwards, you will find the answer.

---

### Post by vovajedi on 2012-02-29
> **Riehlthing said:**
> I've been reading over this thread, to get right click functionality on my HP Laptop, and so far only have gotten partially to normal use.  I tried this, and at step 9, I get an error stating "bad return status on module...".  I was hoping to just get right click, and no tap to click on the touchpad part itself.
#283 worked perfectly for me.
U should upgrade kernel to >3 and download the last patched psmouse-3.0.0-12-generic (not 2.6) than follow the instruction. 

Thanx to this thread now it works!

---

### Post by AlexAv on 2012-03-09
> **tricolorpoa said:**
> This works!!
Thanks!
Ubuntu 11.10 x86_64 kernel 3.0.0-14-generic

This works too with a HP Mini 210-1180NR 

With Linux Mint 12 Gnome 3.2 Kernel 3.0.0.12

Thanx...

---

### Post by ivoacioly on 2012-03-17
> **tomkear2006 said:**
> i have attached the relevant files to this post. The patch is installed using dkms so once the patch is applied, it will remain applied even when your computer is updated with newer kernel versions.

This is what i did and i hope it works for you too (obviously i can't guarantee anything):

1. Download the attached file to your computers desktop
2. Sudo apt-get install dkms build-essential
3. Cd ~/desktop
4. Tar jxvf psmouse-2.6.38-8-generic.tar.bz2
5. Sudo mv psmouse-2.6.38-8-generic /usr/src
6. Cd /usr/src
7. Sudo chmod -r a+rx psmouse-2.6.38-8-generic
8. Sudo dkms add -m psmouse -v 2.6.38-8-generic
9. Sudo dkms build -m psmouse -v 2.6.38-8-generic
10. Sudo dkms install -m psmouse -v 2.6.38-8-generic
11. Sudo shutdown -r now
12. Dkms status

the output of the last command should look similar to this (with no errors):
"psmouse, 2.6.38-8-generic, 2.6.38-8-generic, i686: Installed"

you can go ahead and delete the files on your desktop. If everything went well you can even right click to select "move to wastebasket".

Good luck!

muito obrigado!!!!!!!!! (thank you!!!!!!!!!!!)

---

### Post by atrich0608 on 2012-04-26
> **tomkear2006 said:**
> In case anyone is interested (I know some people had success) I have applied the same patch as I posted in #224 of this thread, to the default kernel in 11.10 (Oneiric Ocelot).  This is working perfectly for me on the 64bit version.  Follow the instructions as in post #224 swapping out the new kernel version for each command.

I would like to confirm that this works for me HP DM1-3020-US on 12.04 LTS :-)

---

### Post by bichoninf on 2012-04-27
> **atrich0608 said:**
> I would like to confirm that this works for me HP DM1-3020-US on 12.04 LTS :-)
Can you please paste the lines you did after:
$ tar jxvf psmouse-3.0.0-12-generic.tar.bz2
Please ? 
:)

---

### Post by the pwner224 on 2012-04-27
Post #224 (page 23) works on Oneiric Ocelot with kernel 3.0.0-17 on the HP Mini 210-1041nr.

---

### Post by AnotherMuggle on 2012-05-08
I have now patched the psmouse driver for the Ubuntu 12.04 kernel and will upload it here tonight: [http://ubuntuforums.org/showthread.php?t=1966016](http://ubuntuforums.org/showthread.php?t=1966016)

It's very similar to the patch I posted in #224 (for 11.04 Natty) and #265 (for 11.10 Oneiric) but this one is specifically for 12.04 (Precise).

---

### Post by onebutters on 2012-05-20
Re Post #224 worked great for me on 12.04 LTS. Got right-click and 2 finger scrolling. Using HP Mini 210-1036VU

---

### Post by AnotherMuggle on 2012-05-21
> **onebutters said:**
> Re Post #224 worked great for me on 12.04 LTS. Got right-click and 2 finger scrolling. Using HP Mini 210-1036VU

If it is working OK for you then probably no need to change but you would have been better off using the patch in post #18 of this thread for 12.04: [http://ubuntuforums.org/showthread.php?t=1966016&page=2]("http://ubuntuforums.org/showthread.php?t=1966016&page=2")

---

### Post by jonhen on 2012-05-28
Thank you to [[COLOR=#339900]**tgm4883**[/COLOR]]("http://ubuntuforums.org/member.php?u=191664") post 264 that does all I need after upgrade to 12.04. Nice and simple. Cheers. :)

---

### Post by Guicho99 on 2012-07-31
Is not working for me... terminal showed to me this error


colo@colo-HP-Mini-210-1000 ~/linux-source-3.2.0 $ patch -p1 <clickpad_patch
patching file drivers/input/mouse/synaptics.c
Hunk #1 FAILED at 327.
Hunk #2 succeeded at 987 with fuzz 2 (offset 580 lines).
Hunk #3 succeeded at 1413 with fuzz 2 (offset 709 lines).
1 out of 3 hunks FAILED -- saving rejects to file drivers/input/mouse/synaptics.c.rej
patching file drivers/input/mouse/synaptics.h
Hunk #1 FAILED at 48.
Hunk #2 FAILED at 103.
2 out of 2 hunks FAILED -- saving rejects to file drivers/input/mouse/synaptics.h.rej

after that i cant continue.. help please.. im trying to use it in linux mint 13 maya

---

### Post by AnotherMuggle on 2012-07-31
> **Guicho99 said:**
> Is not working for me... terminal showed to me this error


colo@colo-HP-Mini-210-1000 ~/linux-source-3.2.0 $ patch -p1 <clickpad_patch
patching file drivers/input/mouse/synaptics.c
Hunk #1 FAILED at 327.
Hunk #2 succeeded at 987 with fuzz 2 (offset 580 lines).
Hunk #3 succeeded at 1413 with fuzz 2 (offset 709 lines).
1 out of 3 hunks FAILED -- saving rejects to file drivers/input/mouse/synaptics.c.rej
patching file drivers/input/mouse/synaptics.h
Hunk #1 FAILED at 48.
Hunk #2 FAILED at 103.
2 out of 2 hunks FAILED -- saving rejects to file drivers/input/mouse/synaptics.h.rej

after that i cant continue.. help please.. im trying to use it in linux mint 13 maya

I am not sure which instructions you are following but if you want to attempt an Ubuntu patch on Linux Mint 13 (I don't know if the kernels are exactly the same) then try my patch in post #18 here: [http://ubuntuforums.org/showthread.php?t=1966016&page=2]("http://ubuntuforums.org/showthread.php?t=1966016&page=2")  Linux Mint 13 is based on Ubuntu 12.04 so it's "more likely" to work for you.

---

### Post by dreamer0 on 2012-08-23
Hi all,

I'm using Xubuntu (Ubuntu + Xfce) 12.04, and about the 'right click issue', well, the touchpad right button does not work here but I have discovered I dont need to do anything, it works in another way ;). Follow me.  

This solution:

$ sudo echo options psmouse proto=exps > /etc/modprobe.d/psmouse.modprobe

turns off the vertical and horizontal scrollings. It's not good.

First of all we need to determ the type of Touchpad:

$ egrep -i 'synap|alps|etps' /proc/bus/input/devices

(Synaptics, ALPS or Elantech touchpad)  mine  Hpmini 210-1000  is synaptics. 

(For Elantech touchpad see:
[http://wiki.debian.org/DebianEeePC/HowTo/ElantechTouchpad](http://wiki.debian.org/DebianEeePC/HowTo/ElantechTouchpad) )

Run:

$ grep "TouchPad: buttons:" /var/log/Xorg.0.log

as a result here:

(II) SynPS/2 Synaptics TouchPad: buttons: left double triple

'double' and 'triple' means  two and three-finger multipad function (as on Mac's) and 'left' is a left mouse button. Where is the right mouse button?

I've discovered using the command:

$ synclient -l 

this part:

RTCornerButton = 2
RBCornerButton = 3
LTCornerButton = 0
LBCornerButton = 0
...
ClickFinger1 = 1
ClickFinger2 = 3
ClickFinger3 = 0

(RT = right top , LT= left top, RB= right bottom, and so on). The numbers mean:  1 - left mouse button emulation, 2 - middle button, and 3 - right. 

RTCornerButton = 2  > tap on right top corner and it works as the middle mouse button.

So,  'RBCornerButton = 3'    means: hey man, tap the right bottom corner of your touchpad and you have a right click mouse (3). And it works here!  

Another way: 
 'ClickFinger2 = 3'   means: click with two fingers on the 'right button area' and it also works as a right click mouse action! It works here, it was here and I didnt know! I have the right button, using these ways! So, no patch, no configuration needed. 

Also, we can set two-fingers vertical and horiz scrolling using this command:

$ synclient VertTwoFingerScroll=1 HorizTwoFingerScroll=1 

and voila!  
(1 - turn on,   0 turn off). It also works here. (it does not work if you have used that command $ sudo echo options psmouse proto=exps > /etc/modprobe.d/psmouse.modprobe   , so delete the psmouse.modprobe file and reboot. Then use synclient command.)

We can set  LTCornerButton and LBCornerButton   with values  6 and 7,  (L = tap the left corners of the touchpad, Top and Bottom). The 6 and 7 values function as the Back and Forward buttons in your browser, respectively. Very nice! :guitar:

(remember that iPod circular scrolling? we can try it:
$ synclient CircularScrolling=1 CircularPad=1 CircScrollTrigger=8  
to see more:
[http://manpages.ubuntu.com/manpages/karmic/man4/synaptics.4.html](http://manpages.ubuntu.com/manpages/karmic/man4/synaptics.4.html))
):P

---

### Post by bkarlan on 2012-09-09
> **AnotherMuggle said:**
> I have attached the relevant files to this post. The patch is installed using dkms so once the patch is applied, it will remain applied even when your computer is updated with newer kernel versions.

This is what I did and I hope it works for you too (obviously I can't guarantee anything):

1. Download the attached file to your computers desktop
2. sudo apt-get install dkms build-essential
3. cd ~/Desktop
4. tar jxvf psmouse-2.6.38-8-generic.tar.bz2
5. sudo mv psmouse-2.6.38-8-generic /usr/src
6. cd /usr/src
7. sudo chmod -R a+rx psmouse-2.6.38-8-generic
8. sudo dkms add -m psmouse -v 2.6.38-8-generic
9. sudo dkms build -m psmouse -v 2.6.38-8-generic
10. sudo dkms install -m psmouse -v 2.6.38-8-generic
11. sudo shutdown -r now
12. dkms status

The output of the last command should look similar to this (with no errors):
"psmouse, 2.6.38-8-generic, 2.6.38-8-generic, i686: installed"

You can go ahead and delete the files on your desktop. If everything went well you can even right click to select "Move To Wastebasket".

Good luck!

I've done both the commands at the beginning of this thread which enabled my right click but disabled the computer from recognizing my touchpad, so I have lost all configuration abilities, such as setting it up for scroll.  So I ran this patch successfully and I still have right click, but synaptics touch pad configuration tells me that it can't find the touchpad.

So to summarize.  This all has fixed the right click, but disabled scroll and my ability to configure mouse speed, etc...

FYI, I don't have an HP Mini.  I have an HP Pavilion dm3t.

---

### Post by AnotherMuggle on 2012-09-14
> **bkarlan said:**
> I've done both the commands at the beginning of this thread which enabled my right click but disabled the computer from recognizing my touchpad, so I have lost all configuration abilities, such as setting it up for scroll.  So I ran this patch successfully and I still have right click, but synaptics touch pad configuration tells me that it can't find the touchpad.

So to summarize.  This all has fixed the right click, but disabled scroll and my ability to configure mouse speed, etc...

FYI, I don't have an HP Mini.  I have an HP Pavilion dm3t.

I can't say with confidence whether this patch will work on your system.  The patch has only been tested on a HP Mini 210 so it may or may not work for your "HP Pavilion dm3t".

Which commands did you run on your system?

You should revert all other changes you made to your system regarding the touchpad/mouse and then install the patched driver.  Any other changes you made may interfere with the patch.

---

### Post by bmorris36 on 2012-09-16
> **Sabot said:**
> To get the trackpad working correctly you need to use the terminal and enter in the below commands. Make sure you press enter after each command:

    ```
sudo su
```

    ```
echo options psmouse proto=exps > /etc/modprobe.d/psmouse.modprobe
```

    ```
reboot
```



Terminal says
bash: /etc/modprobe.d/psmouse.modprobe: No Such file or directory 

Help Please???

---

### Post by AnotherMuggle on 2012-09-17
> **bmorris36 said:**
> Terminal says
bash: /etc/modprobe.d/psmouse.modprobe: No Such file or directory 

Help Please???

If you are using a HP Mini 210 then ignore those commands.

Please post the output of this command:
```
uname -a
```

---

### Post by bmorris36 on 2012-09-17
> **AnotherMuggle said:**
> If you are using a HP Mini 210 then ignore those commands.

Please post the output of this command:
```
uname -a
```

Yes I have the Hp Mini 210

It says 

Linux britt 3.2.0-30-generic-pae #48-ubuntu SMP fri Aug 24 
17:14:09 2012 i686 i686 i386 GNU/Linux

---

### Post by AnotherMuggle on 2012-09-18
> **bmorris36 said:**
> Yes I have the Hp Mini 210

It says 

Linux britt 3.2.0-30-generic-pae #48-ubuntu SMP fri Aug 24 
17:14:09 2012 i686 i686 i386 GNU/Linux

It looks like you are using Ubuntu 12.04 with the latest kernel installed.
Please follow my instructions [HERE]("http://ubuntuforums.org/showpost.php?p=12246443&postcount=124") and post in that thread if you have any issues.

---

### Post by bmorris36 on 2012-09-22
Sorry but i had immediate problems thanks for trying but ill just stick with using a wireless mouse but thanks anyway and do you know how i could get xp onto a flash drive while still in Ubuntu i want to put it on my Hp Mini 210 and i have the xp but i need to put it on the flash drive and i don't know how to on Ubuntu.

---

### Post by AnotherMuggle on 2012-09-22
> **bmorris36 said:**
> Sorry but i had immediate problems thanks for trying but ill just stick with using a wireless mouse but thanks anyway and do you know how i could get xp onto a flash drive while still in Ubuntu i want to put it on my Hp Mini 210 and i have the xp but i need to put it on the flash drive and i don't know how to on Ubuntu.

What were the immediate problems? I (or someone else) may be able to help.

As for the other question, please start a new thread with an appropriate title.

---

### Post by geee on 2012-11-09
thanks, all! This works great on my HP mini 210 1090nr running a clean install of 12.04 LTS

---

### Post by zahidindia on 2013-02-14
> **jnetman1 said:**
> You're much better off actually fixing the problem with the driver, as telling the system that the touchpad is a PS/2 mouse leaves you with zero control of the pad on the Mini 210. To do this, download the attachment at the bottom of this post and save it in your home folder:

Open the terminal on your Mini 210 and

```
sudo apt-get install build-essential patch linux-source
```

The kernel source will be a tarball that is installed in /usr/src. Extract it to your home directory like so:

```
tar -xjvf /usr/src/linux-source <tab>
``` 

Note that pressing tab will autocomplete to the version you downloaded. Once extracted, change to the source directory and untar the patch attachment you downloaded at the beginning:

```
cd linux-source <tab>
tar -xzvf ../clickpad.tar.gz
```

Now we'll patch the driver files, copy the Makefile to the right place, and compile and install the new driver:

```
patch -p1 <clickpad_patch
cp Makefile drivers/input/mouse/
cd drivers/input/mouse
make
sudo make install
```

Reboot your machine, and you'll find the touchpad works like it should. Note that this patch is based on Takashi Iwai's fine work here: [http://patchwork.kernel.org/patch/67335/](http://patchwork.kernel.org/patch/67335/)

Hi,

After running this command tar -xzvf ../clickpad.tar.gz, the terminal gets stucks and blinks only does nothing. Please help.

---

### Post by alex8wendt on 2013-04-04
> **Sabot said:**
> To get the trackpad working correctly you need to use the terminal and enter in the below commands. Make sure you press enter after each command:

    ```
sudo su
```

    ```
echo options psmouse proto=exps > /etc/modprobe.d/psmouse.modprobe
```

    ```
reboot
```


Once the computer reboots your trackpad will be able to do left click and drag and right clicking.


Works in my HP Pavilion dv6 3030us... i using Linux Mint 14

---

### Post by thewisdomhacker on 2013-06-06
You know I filled a form and made an account specially to tell you something

which is.....

"YOU ROCK"...

Thanks a lot! 
Cheers:D

---

