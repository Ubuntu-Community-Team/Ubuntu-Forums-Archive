---
title: "[Howto] Asus T91MT and Ubuntu 10.10 (Maverick)"
date: 2010-10-13
forum: Hardware
---

### Post by yatt on 2010-10-13
Hi, ya'll. So with the release of Maverick, I've been working to get my T91MT working as well as it did with Lucid. I figured it would be nice if I have posted my progress as a guide, and perhaps other people will be able to share the missing parts they have working.

So here is my guide to using Ubuntu 10.10 on your ASUS T91MT.

**Installation:**

Install Ubuntu as per normal (or possibly update from Lucid). This will work from a fresh install, and it shouldn't matter which flavor of Ubuntu you choose.

**Graphics:**

The ASUS T91MT uses a Intel GMA500 for graphics. To make that work, we have to install the poulsbo driver from a ppa. With a graphical tool, you can copy and paste **ppa:gma500/ppa** in the add source dialog. Then install **poulsbo-driver-2d, poulsbo-driver-3d,** and ** poulsbo-config**. Or from the command line:
```

sudo add-apt-repository ppa:gma500/ppa && sudo aptitude update && sudo aptitude install poulsbo-driver-2d poulsbo-driver-3d poulsbo-config

```

For three packages, it takes a fair amount of time. When it finishes, reboot and notice your screen works a a much nicer resolution. Unfortunately, the graphics driver does not support compositing. This means Compiz, Unity, and KWin's effects cannot be used.

[Source]("https://wiki.ubuntu.com/HardwareSupportComponentsVideoCardsPoulsbo/")

**Touchscreen**

No longer do we need to compile a kernel! [H3g3m0n](http://ubuntuforums.org/showthread.php?t=1507489) provides an updated multitouch-kernel-source to work with Maverick. Download it, extract it, install it, reboot.

That was easy.

**Two Finger Scrolling**

Here is a nice script to make two finger scrolling work on the touchpad.

```

#!/bin/bash

sleep 10
xinput set-int-prop "SynPS/2 Synaptics TouchPad" "Two-Finger Scrolling" 8 1

xinput set-int-prop "SynPS/2 Synaptics TouchPad" "Synaptics Two-Finger Scrolling" 8 1 1

xinput set-int-prop "SynPS/2 Synaptics TouchPad" "Synaptics Two-Finger Pressure" 32 10

xinput set-int-prop "SynPS/2 Synaptics TouchPad" "Synaptics Two-Finger Width" 32 8

xinput set-int-prop "SynPS/2 Synaptics TouchPad" "Synaptics Edge Scrolling" 8 0 0 0 

xinput set-int-prop "SynPS/2 Synaptics TouchPad" "Synaptics Jumpy Cursor Threshold" 32 110

synclient TapButton2=2

exit
```

Save the file to .multitouch.sh (the dot at the beginning makes it a hidden file). Make  it executable through either Right Click -> Properties or:

```
chmod +x .multitouch.sh
```

Then make it run on startup from System->Preferences->Session (can someone who uses Gnome verify this?) or System Settings->Startup and Shutdown.

[Source](http://ubuntuforums.org/showpost.php?p=9968910&postcount=3)

**Rotate Button**

Warning: I tried this, and my wireless stopped working (It did make the rotate button work). However it seems to work for the folks at [=t101]eeeuser.com](http://wiki.eeeuser.com/ubuntu_9.10_on_the_t91_t91mt?s[), so I will post this in hope it works for those daring enough to try.

Create the file **/etc/acpi/events/asus-rotate-t91** and add to it:
```
event=hotkey (ATKD|HOTK) 0000007b
action=/etc/acpi/rotatescreen.sh
```

Then edit **/etc/defaults/grub** and add **acpi_osi=Linux** to the line starting with GRUB_CMDLINE_LINUX_DEFAULT (make sure you paste it inside the quotes). This is the part that caused my wireless to stop working. If you are affected in the same way, simply undo this line.

Finally edit the file **/etc/acpi/rotatescreen.sh** and add to the end:
```
INPUTDEV="9"
ROTATION=`cat /var/lib/acpi-support/screen-rotation`
case $ROTATION in
    normal) xinput set-int-prop $INPUTDEV "Evdev Axes Swap" 8 0
       xinput set-int-prop $INPUTDEV "Evdev Axis Inversion" 8 0 0;;
    left) xinput set-int-prop $INPUTDEV "Evdev Axes Swap" 8 1
       xinput set-int-prop $INPUTDEV "Evdev Axis Inversion" 8 1 0;;
    right) xinput set-int-prop $INPUTDEV "Evdev Axes Swap" 8 1
       xinput set-int-prop $INPUTDEV "Evdev Axis Inversion" 8 0 1;;
    inverted) xinput set-int-prop $INPUTDEV "Evdev Axes Swap" 8 0
       xinput set-int-prop $INPUTDEV "Evdev Axis Inversion" 8 1 1;;
esac
```

**Other Hardware**

AFAIK, the webcam only works in Skype. I have no idea if the microphone works at all. If anyone has an leads, please post in this thread and let me know!

**Apps**

The following is a list of apps that a generally useful with a tablet PC.

Xournal - Allows you to take notes using the stylus. It imitates writing notes in a standard notebook. However, it also allows you to import pdf files, and right your notes directly on the pdf. (Package Name: xournal)

Keyboard Plasmoid - Included with a default Kubuntu install, it is a onscreen keyboard app. Very handy for entering a short bit of text when in tablet mode (Package Name: plasma-widgets-workspace)

---

### Post by kathleenhenri on 2010-10-13
I can't wait to try this. 
Because of the time required to compile the kernel - I'll probably have to wait till the weekend to give it a go.
I'll report my experiences after that.

---

### Post by rentabuddha on 2010-10-13
Thank you so much for this! 

I've completed it now and everything seems to be working perfectly!

To get the touchpad working check out this script:
[http://ubuntuforums.org/showthread.php?t=1479361&highlight=gestures+touchpad&page=4](http://ubuntuforums.org/showthread.php?t=1479361&highlight=gestures+touchpad&page=4)
post #37

I've finally got my Asus T91MT up and running to full potential with 10.10 desktop edition. The netbook session using Unity still doesn't work... has anyone found a solution to this? I've got the drivers, it logs in, but then just displays the wallpaper and randomly flashes warped desktop environment icons.  Can the T91MT not handle these 3D graphics?

In any case, I'm happy with 10.10 so far. Thank you again for this great guide to setting it up on the T91MT! Win7 is molasses compared to this.

---

### Post by yatt on 2010-10-14
> **rentabuddha said:**
> Thank you so much for this! 

I've completed it now and everything seems to be working perfectly!

To get the touchpad working check out this script:
[http://ubuntuforums.org/showthread.php?t=1479361&highlight=gestures+touchpad&page=4](http://ubuntuforums.org/showthread.php?t=1479361&highlight=gestures+touchpad&page=4)
post #37
Sweet! If it works for me, I will include it into the original post.
> I've finally got my Asus T91MT up and running to full potential with 10.10 desktop edition. The netbook session using Unity still doesn't work... has anyone found a solution to this? I've got the drivers, it logs in, but then just displays the wallpaper and randomly flashes warped desktop environment icons.  Can the T91MT not handle these 3D graphics?
No. The drivers don't support full 3D. So no Compiz, no KWin effects and no Unity. I'll update the OP to mention this.
> In any case, I'm happy with 10.10 so far. Thank you again for this great guide to setting it up on the T91MT! Win7 is molasses compared to this.
You are very welcome. I couldn't believe how much faster Linux was than Windows 7.

---

### Post by rentabuddha on 2010-10-15
Hey so just a curious question... why do we comment out and blacklist the T91MT specific drivers? What exactly does this do?  Or, if that isn't the case, what are we even doing when we do the comment out & blacklist step?

---

### Post by jaz2099 on 2010-10-15
This is gonna be my first Linux experience, and I recieve the t91mt tomorrow but have been reading up the past couple of weeks in preparation and anticipation.
 
So a few questions:
 
1) Will this enable multitouch on the screen or just touch? Is it as robust as the win7 options? Is there a way to customize specific actions to perform certain tasks, like a 2 finger circular swipe to rotate the screen or something?
 
2) Will it have the same pressure sensitivity options?
 
3) Would it be advisable to [_[COLOR=darkorange]follow the eeeuser wiki[/COLOR]_ ]("http://wiki.eeeuser.com/ubuntu_9.10_on_the_t91_t91mt?s%5B%5D=t101")guide for 10.04 to install and tweak then upgrade to this for all the video and touch drivers, or just do a basic install from scratch starting at 10.10, disregard that wiki and follow from here?
 
4) Does this include functionality for the rotation button on the screen?
 
5) Will using a Dvorak layout affect functionality before, during, or after install?
 
Anyway, thanks a bunch. Really looking forward to checking out Ubuntu, but man it looks like I jumped into the deep end getting a t91mt. It was just too good to pass up tho. So from a newbie, know that all of you guys' hard work is insanely appreciated.
 
 
Edit: Wow, just saw the update at the eeeuser wiki lol. Very cool. Some clarification is still appreciated tho, with the touchscreen vs touchpad and touch vs multitouch stuff. Thanks again.

---

### Post by H3g3m0n on 2010-10-16
I modified the package from the chasedouglas PPA to work with T91MT, maverick and the new kernel.

Since it uses DKMS this should allow for a much simpler install without needing any source code changes or kernel recompiles.

Grab it from here:
[http://ubuntuforums.org/showthread.php?t=1507489](http://ubuntuforums.org/showthread.php?t=1507489)

---

### Post by yatt on 2010-10-16
> **rentabuddha said:**
> Hey so just a curious question... why do we comment out and blacklist the T91MT specific drivers? What exactly does this do?  Or, if that isn't the case, what are we even doing when we do the comment out & blacklist step?
When you comment out the T91MT driver, you are removing it from a blacklist which prevents it from being compiled/used. When you add it to the blacklist, you are blacklisting the multitouch feature (ie reducing it to single touch). This is done because with multitouch enabled all clicks move the mouse to the very top left (which is probably why Linus has it blacklisted).

NB - The OP has been updated so this question doesn't make as much sense. It does provide some insight on why touch doesn't work out of the box.

---

### Post by yatt on 2010-10-17
> **jaz2099 said:**
> This is gonna be my first Linux experience, and I recieve the t91mt tomorrow but have been reading up the past couple of weeks in preparation and anticipation.
 
So a few questions:
 
1) Will this enable multitouch on the screen or just touch? Is it as robust as the win7 options? Is there a way to customize specific actions to perform certain tasks, like a 2 finger circular swipe to rotate the screen or something?
Just singular touch. Multitouch is currently broken. 
 
> 2) Will it have the same pressure sensitivity options? I didn't even know that it had pressure sensitivity under Windows, or what it would be used for. My guess, would be no.
 
> 3) Would it be advisable to [_[COLOR=darkorange]follow the eeeuser wiki[/COLOR]_ ]("http://wiki.eeeuser.com/ubuntu_9.10_on_the_t91_t91mt?s%5B%5D=t101")guide for 10.04 to install and tweak then upgrade to this for all the video and touch drivers, or just do a basic install from scratch starting at 10.10, disregard that wiki and follow from here?
Either option works. However, it does mention that you have to tweak Grub to get the rotate button to work and this made my wireless stop working. Specifically adding "apci_osi=Linux" part.

> 4) Does this include functionality for the rotation button on the screen?
I will add it to my guide, with a warning.
 
> 5) Will using a Dvorak layout affect functionality before, during, or after install?
Nope. When you first boot from the live-usb you can select dvorak by pressing F3. After that, everything will be dvorak for you.

---

### Post by rentabuddha on 2010-10-17
I attempted to get the rotation button working, but nothing really happened. My wireless still works, which is a bonus I suppose.

When I try to run the script (or when the button tries to run it), it gives me an error saying that /var/lib/acpi-support/screen-rotation does not exist.  That would definitely explain why its not rotating, but why is this missing is the next question.

Regular T91MT using this guide to install... any ideas or suggestions on how to make my computer create and keep this file updated?

---

### Post by jtjs on 2010-10-17
> **yatt said:**
>  I didn't even know that it had pressure sensitivity under Windows, or what it would be used for. My guess, would be no.


The mosart kernel driver doesn't support pressure sensitivity.. It's unfortunate, becuase it would be really useful for painting programs. Hopefully someone will complete the driver.

---

### Post by Foone on 2010-10-17
I was able to get screen rotation working by doing "xhost :local". (This wouldn't be secure if I had other users on my system, but I'm not sure how else to correct the permissions issues)

(I put it in my startup applications so it would persist across sessions)

I also adjusted the rotation behavior:

```

case "$ROTATION" in
    right)
    NEW_ROTATION="inverted"
    ;;
    normal)
    NEW_ROTATION="right"
    ;;
    *)
    NEW_ROTATION="normal"
    ;;
esac

```

This will make it switch through normal->rotated 90->rotated 180->normal instead of just normal->rotated 90->normal.

---

### Post by rentabuddha on 2010-10-17
Foone, can you elaborate on how you got this working, and the difference between this method and the method proposed by the original post?

---

### Post by Foone on 2010-10-17
My method was in addition to the method listed in the first post, as it didn't work for me. After some debugging, I found that making the change I listed (xhost local:) made it work. 

The other change is just a behaviour change I made which I thought others might find useful. 

If you've followed the first post's guide on rotation and you still can't rotate, try typing "xhost local:" in a terminal and pushing the rotate button, see if that fixes it like it did for me.

---

### Post by H3g3m0n on 2010-10-18
> **rentabuddha said:**
> I attempted to get the rotation button working, but nothing really happened. My wireless still works, which is a bonus I suppose.

When I try to run the script (or when the button tries to run it), it gives me an error saying that /var/lib/acpi-support/screen-rotation does not exist.  That would definitely explain why its not rotating, but why is this missing is the next question.

Regular T91MT using this guide to install... any ideas or suggestions on how to make my computer create and keep this file updated?

I've also run into problems getting the screen rotation to work. 

It's not the missing /var/lib/acpi-support/screen-rotation as it isn't supposed to exist first run. It's a file that keeps the last rotation setting and is created after a successful rotate so next time the rotate runs it will rotate to a different orientation. If it doesn't exist it will just use the default 'right' rotation and then create the file.

The actual problem (at least for me) is a bug in the getXConsole function (It's pulled in from: /usr/share/acpi-support/power-funcs), there is some awk error thrown. 

I suspect that the true problem lies with the fgconsole command that getXConsole calls. It always results in "Couldn't get a file descriptor referring to the console". Although the error I was getting was in awk (which is in getXUser called from getXConsole).

I believe the simplest solution would be to remove getXConsole and manually set the DISPLAY=":0" and XAUTHORITY="/home/yourusername/.Xauthority". That would break it if you have other userlogins or if you have more than 1 Xorg running at once though.

---

### Post by rentabuddha on 2010-10-18
So... I've gotten the screen to rotate. You are right, that file just wasn't there the first time so I created it manually but now the script updates it and works fine. HOWEVER...

My button still doesn't work. Basically, I know something (kernel?) is capturing or recognizing the key press, because in dmesg and the system log I get this error message:

eeepc_wmi: Unknown key e4 pressed
eeepc_wmi: Unknown key e5 pressed

I assume this is the press and release of that silver little rotate button.  It seems that X does not capture or realize that a button was pushed at all...

I'm an linux noob if you haven't guessed it already haha but I'm trying. I'm not sure I want to try removing getXConsole just yet because its not the same error... but, someone should know better than me lol, any ideas?

---

### Post by H3g3m0n on 2010-10-19
> **rentabuddha said:**
> So... I've gotten the screen to rotate. You are right, that file just wasn't there the first time so I created it manually but now the script updates it and works fine. HOWEVER...

My button still doesn't work. Basically, I know something (kernel?) is capturing or recognizing the key press, because in dmesg and the system log I get this error message:

eeepc_wmi: Unknown key e4 pressed
eeepc_wmi: Unknown key e5 pressed

I assume this is the press and release of that silver little rotate button.  It seems that X does not capture or realize that a button was pushed at all...

I'm an linux noob if you haven't guessed it already haha but I'm trying. I'm not sure I want to try removing getXConsole just yet because its not the same error... but, someone should know better than me lol, any ideas?

I get that "Unknown key" error message too, but the script is still firing. Just stick a 'date >> /tmp/rotate.log' at the end or something and it will show you it's firing. I did try the XAUTHORITY and DISPLAY hacks without success, at that stage the script wasn't working even when I tried to manually run it as root.

I get some "can't open display :0" and "No protocol specified" errors (even when I try to specify a xrandr protocol.

One problem might be that "XAUTHORITY=/var/run/gdm/auth-for-hegemon-hU9EIr/database" according to `env`, not /home/hegemon/.Xauthority Having a random directory means no hard coding hacks since it will just be different next login.

When I have time later I'll dump debug statements into everything and see where exactly getXConsole is failing.

In anycase the xhost command in a login script as mention above sounds like a good idea provided your not too worried about local security.

---

### Post by Foone on 2010-10-19
> **rentabuddha said:**
> Basically, I know something (kernel?) is capturing or recognizing the key press, because in dmesg and the system log I get this error message:

eeepc_wmi: Unknown key e4 pressed
eeepc_wmi: Unknown key e5 pressed


I'm getting the same errors, but it still rotates fine. Does it rotate if you run 
/etc/acpi/rotatescreen.sh manually? if not, you need to fix the script before worrying about the buttons.

---

### Post by milanp on 2010-10-20
Can you play divx videos on 10.10 without any problems?

---

### Post by rentabuddha on 2010-10-20
> **Foone said:**
> I'm getting the same errors, but it still rotates fine. Does it rotate if you run 
/etc/acpi/rotatescreen.sh manually? if not, you need to fix the script before worrying about the buttons.

Yes, running the script manually works just fine... so far nothing doing on the button press actually being caught by X.
I tired the xhost local: idea with no effect. Haven't tried removing getXConsole, as I'm a frightful noob haha.

---

### Post by DothBrood on 2010-10-21
> **rentabuddha said:**
> So... I've gotten the screen to rotate. You are right, that file just wasn't there the first time so I created it manually but now the script updates it and works fine. HOWEVER...

My button still doesn't work. Basically, I know something (kernel?) is capturing or recognizing the key press, because in dmesg and the system log I get this error message:

eeepc_wmi: Unknown key e4 pressed
eeepc_wmi: Unknown key e5 pressed

I assume this is the press and release of that silver little rotate button.  It seems that X does not capture or realize that a button was pushed at all...

I'm an linux noob if you haven't guessed it already haha but I'm trying. I'm not sure I want to try removing getXConsole just yet because its not the same error... but, someone should know better than me lol, any ideas?

Did you run update-grub and reboot after you added acpi_osi=Linux to GRUB_CMDLINE_LINUX_DEFAULT in /etc/defaul/grub? Again, this may cause your wireless to stop working (it did for me too), and you can undo it by removing the acpi_osi=Linux and running update-grub again.

---

### Post by ian57 on 2010-10-22
Hello all, 

the errors in the /usr/share/acpi-support/power-funcs is on line 9 character 41, the ')' should not be here.  Erase it and save the file.

Reload the power-funcs with .  /usr/share/acpi-support/power-funcs and test getXconsole and getXuser, it should work.

After that, the script worked for me with the xhost local: tips.

but it work to by replacing all the loop 

for x in /tmp/.X11-unix/*; do
    displaynum=`echo $x | sed s#/tmp/.X11-unix/X##`
    getXconsole;
    if [ x"$XAUTHORITY" != x"" ]; then
        export DISPLAY=":$displaynum"           
        /usr/bin/xrandr -o $NEW_ROTATION && echo $NEW_ROTATION > /var/lib/ac
pi-support/screen-rotation
    fi

by 
/usr/bin/xrandr -o $NEW_ROTATION
echo $NEW_ROTATION > /var/lib/acpi-support/screen-rotation

without the xhost tips.

dmesg gives me the eeepc_wmi: Unknown key e4 pressed
eeepc_wmi: Unknown key e5 pressed messages but works well

hope this helps

Yann

---

### Post by ian57 on 2010-10-24
> **milanp said:**
> Can you play divx videos on 10.10 without any problems?
Yes without any configuration, divx can't play. It is due to poulsbo drivers see [https://wiki.ubuntu.com/HardwareSupportComponentsVideoCardsPoulsbo/](https://wiki.ubuntu.com/HardwareSupportComponentsVideoCardsPoulsbo/).

But a workaround for 9.10 exists and still works  : from [http://wiki.eeeuser.com/ubuntu_9.10_on_the_t91_t91mt#the_ubuntu_wiki_way_9.10](http://wiki.eeeuser.com/ubuntu_9.10_on_the_t91_t91mt#the_ubuntu_wiki_way_9.10)

    If you do want to use the vaapi driver with mplayer:  
  sudo apt-get install mplayer gnome-mplayer   Edit /etc/mplayer/mplayer.conf (or ~/.mplayer/config) and add:  
  vo=vaapi   Compiz works ok for normal usage however runs into problems in rotation  mode, massive lag on things like rotate cube and the right side of the  screen glitches. 
   Edit /etc/X11/xorg.conf and add the following line to the device section:  
      Option         "AccelMethod" "EXA"

Yann

---

### Post by rentabuddha on 2010-11-05
Hey again,

So I re-installed because messing with the rotate button I screwed some other things up. Everything's working golden now except the rotate button; still can't get that to work.

HOWEVER, without adding or changing anything (no editing grub) my wireless stopped working.  I found out that for some reason, my wireless is getting blocked at boot! What????!!!!

So I run:
rfkill unblock 0 && rfkill unblock 3
 to unblock the loopback and wlan, which fixes the problem. So, I wrote a start up script to run these commands, which works except it never auto-connects. So my question then is, is there some way in the script I can make WICD (I'm not using network-manager) check for auto-connect? Or, better yet, what could possibly be wrong with my computer that's making it block the wireless (both hard and soft blocks) at boot?

Any suggestions would be appreciated. Its not high priority but its very annoying having to manually connect to the internet haha

---

### Post by lgrubu on 2010-11-07
Hi all,

on my t91mt there are no files in /var/lib/acpi-support. Therefor my screen rotation won't work.

Am I missing any packages?

Thabks in advance if anyone has a suggestion.

Cheers
Lutz

---

### Post by rentabuddha on 2010-11-08
@Lutz

I think I had the same problem while I was playing around with the rotation stuff. If its not there you have to create it. It should work with just some initial variables. Once you've run it once successfully though it'll be good to go. Sorry I can't be more specific but I was never able to get it to work haha

---

### Post by jordanbtucker on 2010-11-09
> **rentabuddha said:**
> Hey again,

So I re-installed because messing with the rotate button I screwed some other things up. Everything's working golden now except the rotate button; still can't get that to work.

HOWEVER, without adding or changing anything (no editing grub) my wireless stopped working.  I found out that for some reason, my wireless is getting blocked at boot! What????!!!!

So I run:
rfkill unblock 0 && rfkill unblock 3
 to unblock the loopback and wlan, which fixes the problem. So, I wrote a start up script to run these commands, which works except it never auto-connects. So my question then is, is there some way in the script I can make WICD (I'm not using network-manager) check for auto-connect? Or, better yet, what could possibly be wrong with my computer that's making it block the wireless (both hard and soft blocks) at boot?

Any suggestions would be appreciated. Its not high priority but its very annoying having to manually connect to the internet haha

Same here, except that I never messed with rotate or grub settings. However, I'm trying it out with wubi for now. Maybe it will be fixed when I perform a real install.

---

### Post by nopacman on 2010-11-09
Hello, nice guide, got video and flash working like a charm, and getting now onto the touch thing. But somehow I keep getting a very noticeable buzzing sound in the background when using any ubuntu (fresh install) on the T91MT that can only be shut down if i shut down the volume. Also, playing with alsamixer did not help (except muting). I've searched around but could not find anyone with the same problem. So, any tip, please, anyone?


Tried ubuntu desktop: 9.04,9.10,10.04,10.10 (current)
Appears on fresh install / live usb
The noise has always the same intensity, and can only be turned off by muting the sound. (Tried all the sound options in Sound Preferences and all the intensity bars in alsamixer)
Dual booting with win7 this time. Sound still works perfect in win. Tried to fiddle with sound options/devices in win7. No differences.
After touching something in Sound preferences I seem to have lost sound on speakers, but I still have it in the jack plug.

Seriously, am I the only one with this problem? It seems unfair >.< .

---

### Post by Alexandr_OFF on 2010-11-10
> **rentabuddha said:**
> HOWEVER, without adding or changing anything  (no editing grub) my wireless stopped working.  I found out that for  some reason, my wireless is getting blocked at boot!  What????!!!!
 Have the same problem after installation of graphic driver.

---

### Post by megahjt on 2010-11-11
I got some problems on my ubuntu 10.04 netbook edition with T91MT:
 
1. The screen brightless (Fn + F3/F4) is not work
 
2. The touch screen is only single touch supported after I install the multitouch pack.
 
3. When I play mp3 or wan file. The player crash and give an error message: failed to create output image buffer of 409x240 pixels.
 
4. Is there a screen keyboard in ubuntu?
 
Could someone help me out?

---

### Post by megahjt on 2010-11-11
To #29:
 
I have exactly the same problem in Ubuntu 10.10. But I try 10.04 netbook edition and it work fine. The GMA500 and wifi both work correctly.

---

### Post by kathleenhenri on 2010-11-12
> **megahjt said:**
> I got some problems on my ubuntu 10.04 netbook edition with T91MT:
 
1. The screen brightless (Fn + F3/F4) is not work
 
2. The touch screen is only single touch supported after I install the multitouch pack.
 
3. When I play mp3 or wan file. The player crash and give an error message: failed to create output image buffer of 409x240 pixels.
 
4. Is there a screen keyboard in ubuntu?
 
Could someone help me out?


A very good on screen keyboard is cellwriter. And a good note taking journal is xournal. Cellwriter has a handwriting recognition component as well. Both are in the default repositories.

---

### Post by H3g3m0n on 2010-11-12
> **megahjt said:**
> I got some problems on my ubuntu 10.04 netbook edition with T91MT:
 
1. The screen brightless (Fn + F3/F4) is not work
 
2. The touch screen is only single touch supported after I install the multitouch pack.
 
3. When I play mp3 or wan file. The player crash and give an error message: failed to create output image buffer of 409x240 pixels.
 
4. Is there a screen keyboard in ubuntu?
 
Could someone help me out?

1. Make sure you add the options "acpi_backlight=vendor acpi_osi=Linux" options to /etc/default/grub in the  GRUB_CMDLINE_LINUX_DEFAULT variable and do a 'update-grub'
2. No multitouch support yet.
3. No idea, works fine for me. Maybe try a different player. Or reinstall.
4. Try the following: onboard (my favourite), xvkbd, cellwriter (mainly does handwriting recognition, but also had a keyboard option), matchbox-keyboard, (also some kde ones, kvkbd, klavier and plasma-widget-plasmaboard).

Also give easystroke a go, it does gesture recognition. Very useful to bind one for things like, alt+f4, close-tab in browsers, open a terminal, new browser window and so on. I started to use it on my desktop now too.

---

### Post by kathleenhenri on 2010-11-14
> **H3g3m0n said:**
> Also give easystroke a go, it does gesture recognition. Very useful to bind one for things like, alt+f4, close-tab in browsers, open a terminal, new browser window and so on. I started to use it on my desktop now too.


Yes, easystroke is great for getting around the missing right mouse click/long press when using the touchscreen.

---

### Post by _integer_ on 2010-11-14
When I update the package list after adding the chasedouglas repository, apt fails to fetch a number of the packages (with appropriate error messages). Then I get the following message when I try to install multitouch-kernel-source:

E: Unable to locate package multitouch-kernel-source

Any idea why apt can't find it?

---

### Post by jtjs on 2010-12-04
I don't know if anyone else here read this on the kernel mailing list, it's from october, but it seems that there is a patch for the mosart kernel driver, which should mean that we'll be able to use it rather than hid quirks mode..

[http://www.mail-archive.com/multi-touch-dev@lists.launchpad.net/msg00544.html](http://www.mail-archive.com/multi-touch-dev@lists.launchpad.net/msg00544.html)

Point #2 explains the odd behaviour when the mosart driver was enabled(rather than relying on hiddev's built in touchscreen handling)... So this is great news for t91mt owners once multitouch is sorted out on the userspace end.

---

### Post by jtjs on 2010-12-05
alright, good news, I've applied the patches from Benjamin tissories, disabled the multitouch quirk, and lsmod confirms that I'm now using the mosart driver for the touch screen.

I've attached the patched files if you want to give it a try.. but you will need to do a dpkg-reconfigure on the package..

the files go in /usr/src/multitouch-1.555/drivers/hid

---

### Post by jtjs on 2010-12-05
more good news..

twofing works.. almost, it crashes after a few gestures, but it does briefly work, kinetic scrolling and all..

One thing about twofing though, the udev rule needs to be modified to attach to the t91mt's touchscreen, which is device id 0185.

update: I've been investigating twofing a bit, maybe I can get it functioning properly, of note, the id's for the fingers on the t91mt's screen are 1 and 2, as opposed to egalax's 0 and 1..

update 2: modifying twofing to use id's 1 and 2 makes gestures function properly, still segfaults though.

update 3: twofing's segmentation fault seems to be due to a corrupt char.. the blacklist somehow gets corrupted.. needs to be re-built each time the "isWindowBlacklistedForGestures" function is called, otherwise  we get a segmentation fault.. Anyone got any ideas? I have uploaded the modified source

---

### Post by jtjs on 2010-12-07
T91MT owners: you should add the utouch PPA and install the hid-mosart-dkms package, it contains the patched mosart kernel module, which has functional multitouch.

sudo add-apt-repository ppa:utouch-team/utouch
sudo apt-get update
sudo apt-get install hid-mosart-dkms

After that, you will be able to take advantage of any multitouch apps that are released, this ppa is maintained by ubuntu devs who are working on multitouch, so, hopefully there will be some nice things showing up there.

---

### Post by H3g3m0n on 2010-12-08
> **_integer_ said:**
> When I update the package list after adding the chasedouglas repository, apt fails to fetch a number of the packages (with appropriate error messages). Then I get the following message when I try to install multitouch-kernel-source:

E: Unable to locate package multitouch-kernel-source

Any idea why apt can't find it?

The chasedouglas ppa was for Lucid. Maverick uses a .deb file from the other thread linked in the first post or better yet the PPA above.

That PPA seems to be working well for me, although it took 2 installs to work for some reason.

I haven't had any problems with twofing crashing yet, but I havn't been using it long and I don't really know how to use it yet.

I also made a new multitouch-kernel-source 1.556 using the above patches, not much use now there is a PPA but might be some use to someone.

---

### Post by jtjs on 2010-12-08
the copy of twofing that I attached has a hackish workaround for the seg fault I had been experiencing, so, hopefully you won't get that crashing problem at all..

if you drag two fingers along the screen it scrolls, if you start dragging with two fingers, lift one up, keep dragging and then lift the second finger up, it gives a kinetic scroll. Pinch zooming works pretty well and if you hold two fingers down for a couple seconds, when you lift them up you get the right click menu.

---

### Post by jtjs on 2010-12-09
Plippo has released a new version of twofing, it's available for download from here: [https://help.ubuntu.com/community/T101MT#EXPERIMENTAL%20TWO-FINGER%20TOUCH%20DAEMON](https://help.ubuntu.com/community/T101MT#EXPERIMENTAL%20TWO-FINGER%20TOUCH%20DAEMON)

Just one change that T91MT users need to make, edit 70-touchscreen-egalax.rules and change 480d to 0185 before "sudo make install"

---

### Post by razor180 on 2010-12-10
alright, I'm having a problem with the poulsbo driver installation. Mostly with the fact that it's not working. I installed it, then restarted, and now, I have no graphics what-so-ever. the login screen is just text (I don't know the term, but I think it's bash)

when I restarted and chose ubuntu in grub, it brought up text stating 

[I]Ubuntu 10.10 Jack-T91MT tty1

Jack-T91MT login:[/I]

when I login it just displays the last login, the linux type and some minor system information and a welcome message then an update message then the normal command prefix (User@computername:~$)

I was able to see graphics without the driver, when I installed, it just seemed to make things worse

---

### Post by razzac11 on 2010-12-14
Please help, whenever i install the graphics driver my Wireless is automatically disabled, as if the hardware wasnt even there. and it pressing Fn F2 doesnt turn it back on like it should. ??

---

### Post by razor180 on 2010-12-15
have you tried going into ubuntu's wireless internet options and fixing it without the hotkey?
have you also tried getting rid of and then reinstalling the wireless drivers?

---

### Post by razor180 on 2010-12-15
disregard my message posted on here, I reloaded the OS, retried installing the video drivers and it worked perfectly (looks like I just had a bad install, no worries)

thank you for posting this information here

although on the graphics installation, I had to do apt-get instead of just aptitude because it didn't accept the command otherwise

---

### Post by Ozone77 on 2010-12-16
> **razzac11 said:**
> Please help, whenever i install the graphics driver my Wireless is automatically disabled, as if the hardware wasnt even there. and it pressing Fn F2 doesnt turn it back on like it should. ??

My wireless worked at first but after something (kernel update?) it only works if I run 

sudo rfkill unblock all

If this works for you, edit /etc/rc.local and add "rfkill unblock all" for a permanent workaround.

---

### Post by yigal.weinstein on 2010-12-19
Really, really awesome.  It's _great_ to finally have some multitouch functionality in Ubuntu - forget some really this is exactly what I wanted when I first purchased this laptop.  Awesome!!

> **jtjs said:**
> Plippo has released a new version of twofing, it's available for download from here: [https://help.ubuntu.com/community/T101MT#EXPERIMENTAL%20TWO-FINGER%20TOUCH%20DAEMON](https://help.ubuntu.com/community/T101MT#EXPERIMENTAL%20TWO-FINGER%20TOUCH%20DAEMON)

Just one change that T91MT users need to make, edit 70-touchscreen-egalax.rules and change 480d to 0185 before "sudo make install"

---

### Post by yigal.weinstein on 2010-12-20
Grub problems:  in /etc/default/grub when I change GRUB_CMDLINE_LINUX_DEFAULT="acpi_backlight=vendor acpi_osi=Linux" or anything more complicated I cannot get wifi to start.

lspci shows the wireless
dmesg has plenty of ath0 throughout the booting sequence

but Fn-F2 fails to wake the wireless nor can I control it via the command line via iwlist/iwconfig etc.  Network-manager shows no wireless connections found and so I'm stuck between having wireless and being able to control the back lights.

I believe this may have to do with the kernel Maverick is using as I remember having similar troubles using the same kernel in 10.4 but I really don't know how to go about rectifying the issue - other than trying different kernels which I would prefer not to have to do.  

I see that yatt in post #4 has this similar issue with grub but there appears to be no work around at present.  I would like to know if anyone other than myself is having similar issues.  Any feedback or help would be very much appreciated.
 
Edit: Ozone your work around didn't work for some reason when I first tried, "rfkill ...".  However, after I reinstalled the psb driver - as I installed 2.6.36 but of course psb didn't build on that kernel.  So upon reinstalling psb driver on 2.35 I tried
```
#rfkill unblock all
```
and I've got wireless.  Hopefully it isn't just on this boot :D

Edit2: After three boots - I had to add "acpi_backlight=vendor" to GRUB_CMDLINE_LINUX_DEFAULT - wifi is working with Ozone's fix.  Now the only issue for me is getting two finger scrolling working, and I guess eventually three finger page turning on the touchpad.  Happy holidays!

---

### Post by kathleenhenri on 2011-01-09
> **jtjs said:**
> Plippo has released a new version of twofing, it's available for download from here: [https://help.ubuntu.com/community/T101MT#EXPERIMENTAL%20TWO-FINGER%20TOUCH%20DAEMON](https://help.ubuntu.com/community/T101MT#EXPERIMENTAL%20TWO-FINGER%20TOUCH%20DAEMON)

Just one change that T91MT users need to make, edit 70-touchscreen-egalax.rules and change 480d to 0185 before "sudo make install"


I just installed the two-finger touch daemon and I have to say, YAY! :D

Now my T91MT does all I could ask for. A long wait for sure, all the while experimenting with various Linux distros and putting up with with a lot of Windows 7 in between, but in the end, worth it!

---

### Post by razor180 on 2011-01-23
I can't get the screen rotate button to work at all, I don't even think it's acknowledging that I'm hitting it. I'm almost to the point where I'm going to learn how to make a python GUI script to make a button that will rotate my screen orientation 90 degrees every time it's clicked (or possibly making an applet, but the button seems easier) just by activating scripts that are already there

I've edited and added the files like instructed, but nothing happened, my wireless didn't even go out, I did reset grub and I did the xhost thing, but it didn't work

---

### Post by Favux on 2011-01-23
Hi razor180,

> I'm almost to the point where I'm going to learn how to make a python GUI script to make a button that will rotate my screen orientation 90 degrees every time it's clicked
The rotation engine for Magick Rotation, xrotate.py, already does that.  Counter clockwise steps, see README for instructions.  Magick Rotation:  [https://launchpad.net/magick-rotation](https://launchpad.net/magick-rotation)

Out of curiosity does the Asus T91MT auto-rotate in Windows?  In other words is there a switch somewhere that signals it is in tablet mode?

---

### Post by razor180 on 2011-01-23
thanks favux, I did find a way to do it through the terminal and I was going to write a script to do that, but this is much easier, thanks

what tells windows it's in tablet mode (and forces the CPU down to 800mhz no matter what you're doing) is changing the orientation by pressing and holding the screen rotate button to rotate the screen

---

### Post by Favux on 2011-01-23
Glad it's working for you.  Saved you some time anyway.
> what tells windows it's in tablet mode (and forces the CPU down to 800mhz no matter what you're doing) is changing the orientation by pressing and holding the screen rotate button to rotate the screen 
Sounds like they didn't include a tablet mode switch so auto-rotation won't be available.  Too bad, it would have been fun to see if we could have added it to Magick.

---

### Post by H3g3m0n on 2011-01-23
I posted [instructions on the eeeuser wiki]("http://wiki.eeeuser.com/ubuntu_9.10_on_the_t91_t91mt#screen_rotate_button_10.10_10.04_9.10") on fixing the rotate button scripts under Maverik ([original fix from ian57]("http://ubuntuforums.org/showpost.php?p=10010690&postcount=22")).

---

### Post by razor180 on 2011-01-24
well, I have a problem (and I think most t91mt ubuntu users have just haven't noticed it)

if you listen real closely you can hear a quiet hissing noise coming from your speakers, now I don't hear this in windows at all, so I think it's probably ubuntu's audio drivers. I don't know how to fix this and I'm not sure if most other t91mt ubuntu users have it, but if you want to see, take a pair of headphones and plug them into the jack and you'll easily be able to hear it

I've only seen one other person post about this problem on this topic, with no response

EDIT: going back to the rotate screen button problem (and I've been having problems getting magick to initialize) I tried the fixes in the updated wiki with no success, I ran dmesg and it's telling me unknown key e4 pressed or unknown key e5 pressed. I'm also getting errors for unknown keys 57 and 58 (but not as frequent as e4 or e5). Another thing, I waited for the screen to start dimming for its process of making the screen sleep after 5 minutes idle, and I pressed the screen rotate key and the screen kept on dimming (normally any interactive action on the computer would stop this, but pressing the screen rotate button did not stop this process)

EDIT 2: looks like I misunderstood the instructions partially, but I went back and fixed rotatescreen.sh and made sure it was right this time, restarted the computer, ran xhost local and pressed the button and I'm still getting the same error for buttons e4 and e5

---

### Post by H3g3m0n on 2011-01-24
The e4/e5 error messages are to be expected, I get them and it works fine.

Try adding ```
date >> /tmp/rotate.log
``` to the top of /etc/acpi/rotatescreen.sh (just under the comment block).

Then press the button. If you get a /tmp/rotate.log file with the timestamp in it, then you know that the script is running, button is working and it's just the rotation portion that is broken. If you don't then you need to fix the button.

the xhost :local command didn't actually work for me (although I have noticed that the wiki entry I made had :local not local: so I might have been doing it wrong). I had to apply the extra block of code to the bottom of /etc/acpi/rotatescreen.sh from the wiki.

Did you create the /etc/acpi/events/asus-rotate-t91 file with the correct lines?

I can hear that slight hissing sound with headphones plugged in, I normally use bluetooth ones so it's not really an issue for me. I've also come to expect some minor hissing from speakers anyway since I often have things like VGA cards emitting enough radiation to cause dragging windows around to be slightly audible. Wish they would start producing digital headphones.

Try googling around for alsa hiss, or snd-hda-intel hiss or whatever.

If you wanted it fixed, first you would have to figure out if it was pulseaudio or alsa, so you would probably have to uninstall pulse. Then you would have to submit a bug to the alsa people (assuming its them).

---

### Post by mrov on 2011-01-25
Hi Everyone,

First, thank you to everyone that has put all of this information together - its been incredibly helpful.  My T91MT is working well except for the fact that I cannot play back any video.  I've tried a couple of different video players (including MPlayer and VLC) and several different video formats.  In every case, it appears as if it will play the video but the screen of the player is blank and there is no sound.  

I'm a complete newbie when it comes to Ubuntu, so I don't even know where to begin to start debugging.  Any help would be greatly appreciated.  I've installed Meerkat Netbook remix, gma500 PPA ([https://launchpad.net/~gma500/+archive/ppa]("https://launchpad.net/%7Egma500/+archive/ppa")), Utouch PPA ([https://launchpad.net/~utouch-team/+archive/utouch]("https://launchpad.net/%7Eutouch-team/+archive/utouch")).  

Thanks in advance.

---

### Post by mrov on 2011-01-28
> **mrov said:**
> Hi Everyone,

First, thank you to everyone that has put all of this information together - its been incredibly helpful.  My T91MT is working well except for the fact that I cannot play back any video.  I've tried a couple of different video players (including MPlayer and VLC) and several different video formats.  In every case, it appears as if it will play the video but the screen of the player is blank and there is no sound.  

I'm a complete newbie when it comes to Ubuntu, so I don't even know where to begin to start debugging.  Any help would be greatly appreciated.  I've installed Meerkat Netbook remix, gma500 PPA ([https://launchpad.net/~gma500/+archive/ppa]("https://launchpad.net/%7Egma500/+archive/ppa")), Utouch PPA ([https://launchpad.net/~utouch-team/+archive/utouch]("https://launchpad.net/%7Eutouch-team/+archive/utouch")).  

Thanks in advance.

Hi Everyone,

I found a fix to my problems:
VLC-->Settings-->Preferences  Video-->Output modules-->Advanced: X11

---

### Post by mmanu on 2011-03-19
> **H3g3m0n said:**
> I posted [instructions on the eeeuser wiki]("http://wiki.eeeuser.com/ubuntu_9.10_on_the_t91_t91mt#screen_rotate_button_10.10_10.04_9.10") on fixing the rotate button scripts under Maverik ([original fix from ian57]("http://ubuntuforums.org/showpost.php?p=10010690&postcount=22")).

i'm a bit puzzled... all seems ok but it doesn't happen!

grub seems ok:

GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX="acpi_osi=Linux acpi_backlight=vendor acpi_skip_timer nomodeset video=uvesafb:mode_option=1024x600-24,mtrr=3,scroll=ywrap pci=nocrs mem=896mb"

/etc/acpi/events/asus-rorate-t91 is created with 0000007b. a /etc/acpi/events/asus-rorate is already present with 0000009b.

the silver butter is firing the rotatescreen.sh : the date >> /tmp/rotate.org test works wherever i put it, i've also checked the /var/lib/acpi-support/screen-rotation file after pressing the button and it works well too, but the screen doesn't move any pixel!

also, from a terminal, the script /etc/acpi/rotatescreen.sh rotates screen as expected.

all seems ok but the /usr/bin/xrandr -o $NEW_ROTATION seems doing nothing when i press that button !!

some additionnal remarks:
when i put both events files (asus-rotate & asus-rotate-t91) to 0000007b or to 0000009b the results are the same (the rotate file fires).
dmsg has a hidden error message when the button is held pushed: unknown key ea (windows use this action to rotate). yeah! i'm glad to contribute :P

---

### Post by H3g3m0n on 2011-03-20
> **mmanu said:**
> i'm a bit puzzled... all seems ok but it doesn't happen!

grub seems ok:

GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX="acpi_osi=Linux acpi_backlight=vendor acpi_skip_timer nomodeset video=uvesafb:mode_option=1024x600-24,mtrr=3,scroll=ywrap pci=nocrs mem=896mb"

/etc/acpi/events/asus-rorate-t91 is created with 0000007b. a /etc/acpi/events/asus-rorate is already present with 0000009b.

the silver butter is firing the rotatescreen.sh : the date >> /tmp/rotate.org test works wherever i put it, i've also checked the /var/lib/acpi-support/screen-rotation file after pressing the button and it works well too, but the screen doesn't move any pixel!

also, from a terminal, the script /etc/acpi/rotatescreen.sh rotates screen as expected.

all seems ok but the /usr/bin/xrandr -o $NEW_ROTATION seems doing nothing when i press that button !!

some additionnal remarks:
when i put both events files (asus-rotate & asus-rotate-t91) to 0000007b or to 0000009b the results are the same (the rotate file fires).
dmsg has a hidden error message when the button is held pushed: unknown key ea (windows use this action to rotate). yeah! i'm glad to contribute :P
After posting that stuff before I discovered that you do need 'xhost local:' in a startup script in addition to the other hacks. Didn't remember to update the wiki.

---

### Post by mmanu on 2011-03-21
ok, it appears that my real problem is to properly add scripts at startup in xubuntu...

i put "  xhost local:" in a +x file (~/.xhost_local) and add it to startup with "xfce settings manager > session and startup > application autostart > add > ~/.xhost_local" reboot and nothing appends. within a term it gives: "non-network local connections being added to access control list" which seems all right to me. i tried some other commands as "sh ~/.xhost_local" or "~/.xhost_local --wait", i add a shebang in the .xhost_local but nothing seems to work. i tried also to put it in some .xinitrc coming from esoteric forums and /etc/gdm/xfce4 but it wasn't really much convincing.

actually, i've the same problem with the multitouchpad script, which works like a charm manually, but doesn't want to autostart.

on the other hand, twofing launches perfectly at startup, which makes me guess an improper method with scripts...

---

### Post by chone on 2011-03-26
> **razor180 said:**
> well, I have a problem (and I think most t91mt ubuntu users have just haven't noticed it)

if you listen real closely you can hear a quiet hissing noise coming from your speakers, now I don't hear this in windows at all, so I think it's probably ubuntu's audio drivers. I don't know how to fix this and I'm not sure if most other t91mt ubuntu users have it, but if you want to see, take a pair of headphones and plug them into the jack and you'll easily be able to hear it

I've only seen one other person post about this problem on this topic, with no response


Hey, just wanted to touch base and say I have this problem too. I've tried a million different things to try to fix it, to no avail. I wonder if there's some way to just filter that noise out if it's some abstruse hardware problem...it's not too bad I guess, but it's not very pleasant. The weird part is that the sound output is otherwise very good.

Another thing, too: has anyone used xournal on their t91mt? I can't get it to smoothly recognize touch input. If I doodle a bunch without picking up the stylus, it works fine, but writing something like text results in a bunch of choppy lines. I honestly think that this is a utouch problem, because my cpu won't go above 40% or so. Xournal has the problem and so does cellwriter. The touchscreen works fine for non-inking tasks, but inking tasks seem to have a ~.25s lag whenever the pen touches the tablet.

Any ideas to fix this would be awesome. It really makes taking notes and drawing diagrams undoable at my natural speed.

---

### Post by kgingeri on 2011-04-03
Hey, I realize this isn't in the flow of the thread at the moment, but I want to share that I've had success with full screen video finally (was white screening previously)! 
I'm using the emgd drivers. (Are there other fixes maybe?)

Thanks to Lucazade's post in ["Guide to Get the Best Performace from the GMA 500" here]("http://ubuntuforums.org/showpost.php?p=10420769&postcount=2976"). The wget and install worked well for me.

NOTE! You will need to customize your xorg.conf.  My current one is below (still fiddling with it and grub settings)

X has quit on me a few times, and lost sync settings - not exactly sure why yet. It's better since I commented DRI in my xorg.conf. Still no 3D that I can tell - not enabled in System->Preferences->Appearance->Visual Effects panel yet, but full screen and smooth video is nice!! :D

3 items: no DRI, the name GMA500 and resolution 1024x600...

```
#Section "DRI"
#        Mode         0666
#EndSection

Section "ServerLayout"
    Identifier     "Default Layout"
    Screen 0       "Screen0"		0 0 
EndSection

Section "Device"
    Identifier "Intel_GMA500"
    Driver     "emgd"
    VendorName "Intel(R) DEG"
    BoardName  "Embedded Graphics"
    BusID      "0:2:0"
    Screen      0
    Option     "PcfVersion"				"1792"
    Option     "ConfigId"				"1"
    Option     "PortDrivers"				"lvds"
    Option     "ALL/1/name"				"lvds-display"
    Option     "ALL/1/General/PortOrder"		"40000"
    Option     "ALL/1/General/DisplayConfig"		"1"
    Option     "ALL/1/General/DisplayDetect"		"1"
    Option     "ALL/1/General/VideoRAM"                 "131072"
    Option     "ALL/1/Port/4/General/name"		"LVDS"
#    Option     "ALL/1/Port/4/General/Rotation"		"0"
    Option     "ALL/1/Port/4/General/Edid"		"1"
    Option     "ALL/1/Port/4/Attr/70"			"0"
    Option     "ALL/1/General/Accel" 			"0"
EndSection

Section "Screen"
    Identifier    "Screen0"
    Device        "Intel_GMA500"
    Monitor       "LVDS"
    SubSection "Display"
	Depth     24
	Modes    "1024x600"
    EndSubSection
EndSection

Section "Monitor"
	Identifier   "LVDS"
	ModelName    "LCD Panel 1024x600"
EndSection

Section "Extensions"
	Option "composite" "enable"
EndSection

```

EDIT: My current grub is as follows:
```
# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.

GRUB_DEFAULT=0
GRUB_HIDDEN_TIMEOUT=1
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=2
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`

GRUB_CMDLINE_LINUX_DEFAULT="quiet splash mem=786mb pciehp.pciehp_force=1 pciehp.pciehp_poll_mode=1"
# ...original...GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
# ...karmic mods...GRUB_CMDLINE_LINUX_DEFAULT="quiet nosplash mem=786mb pciehp.pciehp_force=1 pciehp.pciehp_poll_mode=1"

GRUB_CMDLINE_LINUX="acpi_osi=Linux acpi_backlight=vendor acpi_skip_timer nomodeset video=uvesafb:mode_option=1024x600-24,mtrr=3,scroll=ywrap pci=nocrs mem=896mb"

# Uncomment to enable BadRAM filtering, modify to suit your needs
...
```

---

### Post by Goldstorm on 2011-05-02
EDIT 2: Ok, went and reinstalled a clean version. Everything still works I just need help with 2 minor things:

1. In order for my Wifi to work and the screen rotate button to work On Boot I need to type in terminal:
```
xhost local:
``` for the Rotate Button AND
```
sudo rfkill unblock all
``` for the wifi.

I need to make these 2 things run at startup but I don't know how (nub :c)

2. Whenever I go into suspend mode and wake it up my Wifi stops working...I'll just leave it at that.


I did notice that in tablet mode (Vertical Mode) The screen refreshes from right to left. Was wondering if anyone else noticed this?

EDIT 3: Got it working...but the screen refreshes from right to left. Was wondering if anyone else noticed this?

---

### Post by onebir on 2011-07-09
The saga continue. I just installed Ubuntu **11.04** on a T91 (no MT). Most things work out of the box (including webcam), apart from:
a screen resolution rather low (it said 800x600 in System->Monitors)
b) choppy video playback 
c) touchscreen poorly calibrated
d) no screen rotation & 
e) inability to get bezel button recognised in Easystroke (which as far as I can tell is currently unusable without a keyboard key held down, making it pretty much incompatible with the T91's twisty screen).

Installing EMGD drivers fixed a & b ([https://wiki.ubuntu.com/HardwareSupportComponentsVideoCardsPoulsbo](https://wiki.ubuntu.com/HardwareSupportComponentsVideoCardsPoulsbo))

#330 included this suggestion for screen calibration:```

xinput set-int-prop "IDEACOM  IDC 6680" "Evdev Axis Calibration" 32 300 7900 400 7800
```It doesn't work. But (unusually!) it produces a pretty helpful error message & I was able to work out it should be
```
xinput set-int-prop 9 "Evdev Axis Calibration" 32 300 7900 400 7800
```The 9 comes from running "xinput list" (ie the number by the first "IDEACOM  IDC 6680" entry.

As #330 recommends, in /etc/X11/Xsession.d/98x11-common_touchscreen I added this script:

```
#!/bin/sh

xinput set-int-prop 9 "Evdev Axis Calibration" 32 300 7900 400 7800
```(It took me a while to figure this out :rolleyes:)

So I can now use the T91 like an ebook reader (unlike *all* the other document readers I've tried, evince has a fullscreen mode with an onscreen forward AND back button) and watching videos. Which is why I bought it... :D

It would be great to get screen rotation working, and to get the bezel button recognised by Easystroke for activating gestures. That ought to make it possible to customise things for keyboard free operation - which ironically requiring a gesture button rules out (on a resistive touchscreen).

Has anyone managed?

---

### Post by christophermluna on 2011-07-21
> The 9 comes from running "xinput list" (ie the number by the first "IDEACOM IDC 6680" entry.

As #330 recommends, in /etc/X11/Xsession.d/98x11-common_touchscreen I added this script:

Sorry, I am a bit of newbie to this sort of thing myself. Do you mean that we should create this file */etc/X11/Xsession.d/98x11-common_touchscreen* and paste the code you mentioned into the file? Is that all?

---

### Post by onebir on 2011-07-21
> Sorry, I am a bit of newbie to this sort of thing myself. Do you mean that we should create this file */etc/X11/Xsession.d/98x11-common_touchscreen* and paste the code you mentioned into the file? Is that all? 	

Yes - exactly. Every time the an X session starts, that command should run, calibrating your screen (more or less - it's still not perfect on mine).

---

### Post by christophermluna on 2011-07-30
It worked perfectly. Thanks so much for this! You have no idea how awesome it is to have a correctly calibrated touch screen for the first time in months!

---

### Post by ArchiMark on 2011-08-01
> **onebir said:**
> The saga continue. I just installed Ubuntu **11.04** on a T91 (no MT). Most things work out of the box (including webcam), apart from:
a screen resolution rather low (it said 800x600 in System->Monitors)
b) choppy video playback 
c) touchscreen poorly calibrated
d) no screen rotation & 
e) inability to get bezel button recognised in Easystroke (which as far as I can tell is currently unusable without a keyboard key held down, making it pretty much incompatible with the T91's twisty screen).

Installing EMGD drivers fixed a & b ([https://wiki.ubuntu.com/HardwareSupportComponentsVideoCardsPoulsbo](https://wiki.ubuntu.com/HardwareSupportComponentsVideoCardsPoulsbo))

#330 included this suggestion for screen calibration:```

xinput set-int-prop "IDEACOM  IDC 6680" "Evdev Axis Calibration" 32 300 7900 400 7800
```It doesn't work. But (unusually!) it produces a pretty helpful error message & I was able to work out it should be
```
xinput set-int-prop 9 "Evdev Axis Calibration" 32 300 7900 400 7800
```The 9 comes from running "xinput list" (ie the number by the first "IDEACOM  IDC 6680" entry.

As #330 recommends, in /etc/X11/Xsession.d/98x11-common_touchscreen I added this script:

```
#!/bin/sh

xinput set-int-prop 9 "Evdev Axis Calibration" 32 300 7900 400 7800
```(It took me a while to figure this out :rolleyes:)

So I can now use the T91 like an ebook reader (unlike *all* the other document readers I've tried, evince has a fullscreen mode with an onscreen forward AND back button) and watching videos. Which is why I bought it... :D

It would be great to get screen rotation working, and to get the bezel button recognised by Easystroke for activating gestures. That ought to make it possible to customise things for keyboard free operation - which ironically requiring a gesture button rules out (on a resistive touchscreen).

Has anyone managed?

Tried to install EMGD drivers on my T91MT running 11.04 per the info on Ubunti wiki link you provide...however, when I try to add the gma500/emgd repository here's what I get:

```

$ sudo add-apt-repository ppa:gma500/emgd 
........ (text....) .....
........ (text....) .....
........ (text....) .....
.......  (text....) .....
gpg: requesting key 34xxxxxx from hkp server keyserver.ubuntu.com
gpg: key 34xxxxxx: "Launchpad GMA500 PPA" not changed
gpg: Total number processed: 1
gpg:              unchanged: 1
$

```

Have several times to add this repository at various times today, but always get same message....

Any suggestions?

Thanks!

Mark

---

