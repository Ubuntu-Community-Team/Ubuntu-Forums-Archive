---
title: "Acer 5920(G) - Karmic tweaks"
date: 2009-11-04
forum: Hardware
---

### Post by FokkerCharlie on 2009-11-04
Okey, Dokey, fellow 5920(G) owners!

Here's some tips that may help to make your Karmic experience a little better.  Most of the methods described are as per those that worked for Jaunty (see thread [here]("http://ubuntuforums.org/showthread.php?t=997860"), but there are a few new issues that we need to take a look at.  Conversely, on my system, the brightness control now works correctly, so I have omitted the steps for fixing this.  If it's an issue for anyone else, please let us know.

All the guidance below is what works for me.  I am not an expert, and all advice comes with the usual disclaimers!


[FONT="Arial Black"]Part 1:  Media Keys[/FONT]

OK, we'll start off with the most complicated bit.  We need to patch xserver-xorg-input-synaptics to cope with the media keys.

- Get the sourcecode of syndaemon and build dependencies

```
apt-get source xserver-xorg-input-synaptics
sudo apt-get build-dep xserver-xorg-input-synaptics
```

- Patch syndaemon

```
cd xserver-xorg-input-synaptics-1.1.2
wget "http://bugs.gentoo.org/attachment.cgi?id=202431&action=view" -O tools/syndaemon.patch
patch tools/syndaemon.c tools/syndaemon.patch
```

- Configure and make

```
./autogen.sh
make
```

Now, we'll make 2 fdi files- one for the media keys, and one for the touchpad proper.

```
gksu gedit /etc/hal/fdi/policy/touchpad.fdi
```

Put this in the file, then save:

```
<?xml version="1.0" encoding="UTF-8"?>
<deviceinfo version="0.2">

  <device>
    <match key="info.udi" string="/org/freedesktop/Hal/devices/platform_i8042_i8042_AUX3_port_logicaldev_input">
        <merge key="info.product" type="string">Touchpad</merge>
        <merge key="input.x11_options.AlwaysCore" type="string">true</merge>
        <merge key="input.x11_options.RTCornerButton" type="string">2</merge>
        <merge key="input.x11_options.RBCornerButton" type="string">3</merge>
        <merge key="input.x11_options.LTCornerButton" type="string">4</merge>
        <merge key="input.x11_options.LBCornerButton" type="string">5</merge>
        <merge key="input.x11_options.TapButton1" type="string">1</merge>
        <merge key="input.x11_options.TapButton2" type="string">1</merge>
        <merge key="input.x11_options.TapButton3" type="string">1</merge>
        <merge key="input.x11_options.PalmDetect" type="string">0</merge>
        <merge key="input.x11_options.PalmMinWidth" type="string">0</merge>
        <merge key="input.x11_options.PalmMinZ" type="string">0</merge>
    </match>
  </device>

</deviceinfo>
```

Now for the mediakeys:

```
gksu gedit /etc/hal/fdi/policy/mediakeys.fdi
```

```
<?xml version="1.0" encoding="UTF-8"?>
<deviceinfo version="0.2">

  <device>
    <match key="info.udi" string="/org/freedesktop/Hal/devices/platform_i8042_i8042_AUX2_port_logicaldev_input">
        <merge key="info.product" type="string">Mediakeys</merge>
        <merge key="input.x11_options.AlwaysCore" type="string">true</merge>
    </match>
  </device>

</deviceinfo>
```

And save again.

Now, we need to make sure that we're using our newly patched version of Syndaemon, not the old one.  So go to System > Prefs > Startup Apps, and find the Syndaemon entry.  If you don't have one, you can create a new one.

Replace the command with:

```
/home/<username>/xserver-xorg-input-synaptics-1.1.2/tools/syndaemon -t -n Touchpad
```

Note the '-n Touchpad' bit.  The other switches are up to you.

Now we need to remap the media key 'buttons', so add another command to your startup apps (or replace the previous equivalent):

```
xinput set-button-map "Mediakeys" 1 2 3 17 18 19 20 8 9 10 11 12 13 14 15 16
```
You can call it what you like.

If you have not yet done so, install xbindkeys and xvkbd, and open the configuration file for editing:

```
sudo apt-get install xbindkeys
sudo apt-get install xvkbd
gedit .xbindkeysrc
```

Copy this text into the file:

#Mutlimedia control keys:
```

"xvkbd  -text "\[XF86AudioPlay]""
    b:17

"xvkbd  -text "\[XF86AudioStop]""
   b:18:

"xvkbd  -text "\[XF86AudioPrev]""
    b:19

"xvkbd  -text "\[XF86AudioNext]""
    b:20
```

This works perfectly with all the Gnome music players that I have tried.  While you're here, you can map your blue 'e' key to run Exaile, or whatever else you want:

```
#Map 'e' key to launch exaile
"exaile %f"
    c:219
```

It turns out that Karmic has integrated syndaemon, so to prevent two instances of the process starting, go to System > Prefs > Mouse > Touchpad, untick 'Disable touchpad when typing'.

And you're done.  Restart for the changes to take effect.  **NOTE:  THE BLUE E-KEY WILL ONLY WORK AFTER YOU HAVE COMPLETED PART 3 BELOW**

[FONT="Arial Black"]Part 2: The Hotkeys[/FONT]

If your hotkeys (the fn keys for suspend, etc) aren't working right, you can follow this section.  With thanks to Alkis and Percy for the work on [this]("https://bugs.launchpad.net/ubuntu/+source/hal-info/+bug/281951") bug.

Download a new fdi file from [here]("http://launchpadlibrarian.net/23227355/30-keymap-acer.fdi").  Now you need to replace your old /usr/share/hal/fdi/information/10freedesktop/30-keymap-acer.fdi file with the one you just downloaded.  The steps below assume that you have downloaded the file to your home folder.

**THIS IS RISKY.  PLEASE ONLY FOLLOW THESE STEPS IF YOU UNDERSTAND THEM, AND ARE ABLE TO UNDO THEM.  DO THIS AT YOUR OWN RISK!**

```
sudo mv /usr/share/hal/fdi/information/10freedesktop/30-keymap-acer.fdi /home/<yourusername>/30-keymap-acer-old.fdi
sudo cp 30-keymap-acer.fdi /usr/share/hal/fdi/information/10freedesktop/
```

Note that the first command may generate a 'file not found' error.  If so, don't worry, just carry on.  That should fix any issues with your fn keys.  It also sets us up for part 3.

[FONT="Arial Black"]Part 3:  Enable the &#8364; and $ keys[/FONT]

We need to make a script that will run every time you log in.  In this example, I will make a hidden folder in your home folder and put it in there.

Open a terminal, and type:
```
cd .startscripts
gedit eurodollar.sh
```

And paste this code:
```
#!/bin/sh
echo 'keycode 186 = dollar dollar dollar dollar dollar' | xmodmap -
echo 'keycode 185 = EuroSign EuroSign EuroSign EuroSign EuroSign' | xmodmap -
```

Now, to set this script to run on every login, go to System > Prefs > Sessions, and under Startup Programs, add again:
Name:  EuroDollar
Command: sh /home/<username>/.startscripts/eurodollar.sh
Description: Enables &#8364; and $ keys.

And close.  You should see this come into effect when you next restart X, or log out/in.

Please note that if you have multiple users on your system, you will need to follow parts 1 and 3 for each user.

[FONT="Arial Black"]Part 4:  Fix the glitchy sound.[/FONT]

You may have noticed some pops from the speakers from time to time.  It seems that this is an issue with power-saving.  To fix:

open a terminal and type:
```
/etc/modprobe.d/alsa-base.conf
```

At the start of the last line, insert: #   
You will probably have to re-start for this change to take effect.

-------------------

OK, that's it.  Let us know by posting on the thread how you have got on with the fixes above.  If there's anything missing or incorrect, please do post so that your corrections can help others.

Thanks to everyone who has contributed to the solutions posted above, including on the Intrepid / Jaunty thread, and a special shout to Mohr Tutchy who keeps coming up with the goods regarding xinput.

Cheerio!
Charlie

---

### Post by errenay on 2009-11-04
It looks really strange, but some keys are working (play and stop). There is the output from xev:
```

KeyRelease event, serial 30, synthetic NO, window 0x3600001,
    root 0x13c, subw 0x0, time 806024, (-448,385), root:(537,410),
    state 0x0, keycode 36 (keysym 0xff0d, Return), same_screen YES,
"   XLookupString gives 1 bytes: (0d) "
    XFilterEvent returns: False

PropertyNotify event, serial 33, synthetic NO, window 0x3600001,
    atom 0x210 (_NET_WM_ICON_GEOMETRY), time 806422, state PropertyNewValue

```
There is no output for rev / fwd buttons. If I try to start script manually I have
```
device has no buttons

```
Something was changed with the device?

---

### Post by errenay on 2009-11-05
One more thing - I have also some problems with sound. Sometimes there are loud cracks from speakers. I think that they are connected with initialization of sound card. First crack is just before first sound during starting of KDE, next cracks may be heard after long break between sounds (reinitialization of the sound card?).
In System properties / Multimedia / Music my sound card is mentioned as "HD Intel ALC1200 Analog". As far as I remember, in 9.04 it was "ALC 888" or something like this.
Does anyone have similar problems?

---

### Post by FokkerCharlie on 2009-11-05
Hi Errenay.

That's strange.  A report from the Intrepid/Jaunty thread reports all OK with the media keys.  Can you post the output from xev | grep button without xbindkeys running (as above).  And also, without the button remapping script running (disable it in the startup apps menu, log out and in again)?

For sound problems, have you tried this:

[http://swiss.ubuntuforums.org/showpost.php?p=8099760&postcount=12]("http://swiss.ubuntuforums.org/showpost.php?p=8099760&postcount=12")

Charlie

---

### Post by errenay on 2009-11-06
Output after xev | grep button: "play" button:
```
^[[A^[[A^[[
```
"stop":
```
^[[B^[[B^[[B

```
rev / fwd: nothing.
With script disabled output is the same
About sound - it looks that after commenting out the line, there are no cracks. Thank you!

---

### Post by FokkerCharlie on 2009-11-09
Errenay- was this output from xev when you have xbindkeys running, or without?

Charlie

---

### Post by mohr tutchy on 2009-11-10
With karmic the target of syndaemon and synclient are the media keys instead of the touchpad.

I can't solve this problem with these methods
[http://ubuntuforums.org/showpost.php?p=7535907&postcount=4](http://ubuntuforums.org/showpost.php?p=7535907&postcount=4)
[http://ubuntuforums.org/showthread.php?t=517156](http://ubuntuforums.org/showthread.php?t=517156)

That is probably because syndaemon and synclient don't need SHMConfig=true anymore.

---

### Post by FokkerCharlie on 2009-11-10
Hi Mohr

I installed Karmic yesterday, and have been grappling with this issue.  It's a pain...

And is it just me, or is the fn+f4 suspend key not working?

Working on it...

---

### Post by errenay on 2009-11-10
> **FokkerCharlie said:**
> Errenay- was this output from xev when you have xbindkeys running, or without?

Charlie

The output was checked after using
```
killall xbindkeys
```

---

### Post by FokkerCharlie on 2009-11-10
That's strange.  Can you disable the button-remapping script, log out/in again and try again?

Suspend hotkey works now.  Should have followed my own instructions.  :rolleyes:

Charlie

---

### Post by mohr tutchy on 2009-11-11
I found a patch for syndaemon that allow us to specify the target device.
[http://bugs.gentoo.org/show_bug.cgi?id=282949#c1](http://bugs.gentoo.org/show_bug.cgi?id=282949#c1)
[http://bugs.gentoo.org/attachment.cgi?id=202431&action=view](http://bugs.gentoo.org/attachment.cgi?id=202431&action=view)
Great thanks Per Öberg :)

How to make it work:

- Get the sourcecode of syndaemon and build dependencies
```
apt-get source xserver-xorg-input-synaptics
sudo apt-get build-dep xserver-xorg-input-synaptics
```

- Patch syndaemon
```
cd xserver-xorg-input-synaptics-1.1.2
wget "http://bugs.gentoo.org/attachment.cgi?id=202431" -O tools/syndaemon.patch
patch tools/syndaemon.c tools/syndaemon.patch

```

- Configure and make
```
./autogen.sh
make
```

- Create /etc/hal/fdi/policy/touchpad.fdi file
The way to find the right parameters is the same described here
[http://ubuntuforums.org/showpost.php?p=7535907&postcount=4](http://ubuntuforums.org/showpost.php?p=7535907&postcount=4)

SHMConfig parameter is not needed. The most important things are info.udi and info.product. The second parameter will be the one passed to syndaemon. Here is an example.
```

<?xml version="1.0" encoding="UTF-8"?>
<deviceinfo version="0.2">
  <device>
      <match key="info.udi" string="/org/freedesktop/Hal/devices/platform_i8042_i8042_AUX3_port_logicaldev_input"> 
        <merge key="info.product" type="string">Touchpad</merge>
        <merge key="input.x11_options.AlwaysCore" type="string">true</merge>
        <merge key="input.x11_options.VertTwoFingerScroll" type="string">true</merge>
        <merge key="input.x11_options.RTCornerButton" type="string">0</merge>
        <merge key="input.x11_options.RBCornerButton" type="string">0</merge>
        <merge key="input.x11_options.LTCornerButton" type="string">0</merge>
        <merge key="input.x11_options.LBCornerButton" type="string">0</merge>
        <merge key="input.x11_options.TapButton1" type="string">1</merge>
        <merge key="input.x11_options.TapButton2" type="string">0</merge>
        <merge key="input.x11_options.TapButton3" type="string">0</merge>
        <merge key="input.x11_options.PalmDetect" type="string">1</merge>
        <merge key="input.x11_options.PalmMinWidth" type="string">10</merge>
        <merge key="input.x11_options.PalmMinZ" type="string">200</merge>
    </match>
  </device>
</deviceinfo>

```

- Test
Restart hal 
```
sudo service hal restart
```
logout from the X session and log in again.
Run your brand new syndaemon with these parameters
```
xserver-xorg-input-synaptics-1.1-2/tools/syndaemon -i 2 -n Touchpad
```

I hope i was clear, sorry for bad english.

---

### Post by errenay on 2009-11-11
> **FokkerCharlie said:**
>  Can you disable the button-remapping script, log out/in again and try again?


With the script disabled, output is the same.
Yes, it is strange - I'm also using the same method and script for browser / e-mail keys (left side of keyboard). And they work...

---

### Post by FokkerCharlie on 2009-11-11
Mohr Tuchy:

Good job!  I'll try that out on my setup, and then put together some instructions for the top post shortly.

errenay:

What about if you just run xev without the '| grep button' ?

Charlie

---

### Post by FokkerCharlie on 2009-11-12
Top post updated with the methods that seem to work OK for me.

The patched syndaemon works fine; it's a shame that gsynaptics can't be made to target the correct device... but not to worry.

Cheerio!
Charlie

---

### Post by mohr tutchy on 2009-11-12
> **FokkerCharlie said:**
> 
it's a shame that gsynaptics can't be made to target the correct device... but not to worry.


Right FokkerCharlie! Don't worry :)
Once you set a name for the touchpad in the touchpad.fdi file you can configure the right device using gpointing-device-settings instead of gsynaptics.

PS: Don't care about the VertTwoFingerScroll parameter in my touchpad.fdi file. Our  hardware doesn't support multitouch.
PPS: Opened new bug in launchpad for xserver-xorg-input-synaptics: [https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-input-synaptics/+bug/480717](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-input-synaptics/+bug/480717)
[SIZE="1"]PPPS: My nickname is mohr tuTchy... ;)[/SIZE]

---

### Post by FokkerCharlie on 2009-11-13
Yes, I had forgotten about gpointing-device-settings.  The only disappointing thing about that is that it doesn't seem to be possible to adjust pointer speed and acceleration... but the default settings are fine for me.

I'll make some adjustments to the top post to reflect this; naming the devices can make the button-mapping command a bit more elegant, too.

Charlie

PS:  You're correct, our hardwarde doesn't support multi-touch... however, it's possible to emulate it.  See [this]("http://ubuntuforums.org/showthread.php?t=969993") thread.  I don't use it, as I couldn't get the settings to work for me consistently.

PPS:  Sorry for spelling your name wrong.  I am a bad person.

---

### Post by Pott on 2009-11-14
Doesn't work for me... :(

Some of the instructions didn't work, or I didn't get them right. In order:
1)
sudo service hal restart and hal-device To find out the right string for line 4 of the touchpad.fdi file
I got about 150 entries and only about 15 displayed on the terminal. I have no idea if I have the right 4th line on the file, and no way to check as they're not all displayed... I'm guessing this could be the key, I must have the device wrong. 

2)
I got the syndaemon thing right I think, in the startup aps. There was nothing before so I created it. I just did as it said, so ~/filefolder/folder/name etc... with -t -n Touchpad at the end, but apparently the -t is left to our preference..? I have no idea what should go there at all... Do I also need to make the file executable as a program for the startup apps to pick it up and start it?

3) (sorry :P)

sudo mv /usr/share/hal/fdi/information/10freedesktop/30-keymap-acer.fdi /home/<yourusername>/30-keymap-acer-old.fdi
This line here didn't work (don't worry I filled in the <yourusername> part!). Somehow though the hotkeys DO WORK now... :s so I just hope I've not messed anything else up.
Anyway, I couldn't create that file in this folder basically. I'm not 100% sure that I understand the codes so I didn't want to do this but can I simply do a sudo gedit <filefilder/name>  and copy the content of the downloaded file?
EDIT:
I figured out what was wrong. There is no 30-keymap-acer.fdi file in this folder. So the move function of course didn't work. I just created it with the new file content and saved. Nothing so far...

Aaand that's about it... the keys don't work right now with movieplayer on a DVD, don't know if the software recognizes these anyway. I'll get Exaile to see if it works with them anyway...

Thanks, I hope this is solvable...

EDIT: I got Exaile, installed the plugins but nothing works. I still have no media keys. The hot keys do work, including with movie player, so the media keys should work too but they still function as mouse keys for now... :(
Also, the Euro/Dollar keys aren't working, which is weird as it's the easy script out of all :s
EDIT2: I found out something weird... the 'sh' in front of the EuroDollar script disappears when I log out/in. So it doesn't get the command right I'm guessing. Making it executable didn't solve anything either.
EDIT3: xev | grep button gives me buttons 17, 18, 19 and 20 on the media keys. So I guess the script command works. But it lacks the command to make these stop being mousebuttons and making it media buttons.

---

### Post by mohr tutchy on 2009-11-15
> **Pott said:**
> 
1)
sudo service hal restart and hal-device To find out the right string for line 4 of the touchpad.fdi file
I got about 150 entries and only about 15 displayed on the terminal. I have no idea if I have the right 4th line on the file, and no way to check as they're not all displayed... I'm guessing this could be the key, I must have the device wrong. 


To find the touchpad udi use this command:
```
hal-device |grep Synaptics -B 9|grep udi
```
the output should be like this:
```
35: udi = '/org/freedesktop/Hal/devices/platform_i8042_i8042_AUX3_port_logicaldev_input'
36: udi = '/org/freedesktop/Hal/devices/platform_i8042_i8042_AUX2_port_logicaldev_input'
```
in my case the first is the touchpad and the second the media keys.
[SIZE="1"]
PS:When a command returns a long output like dmesg, an easy thing to do is to use less:
```
dmesg|less
```[/SIZE]

---

### Post by FokkerCharlie on 2009-11-15
Hi Pott, Mohr

Sorry the instructions weren't that clear.

1) Mohr is quite correct with his method above.  However, it's quite likely that the udi string that you require is the same as mine; so, as a starter for 10, you can just copy and paste from the top post, and it will most likely work.

You can also type:

lshal > lshal.txt 
That outputs the info to the text file lshal.txt, which you can look at with gedit.

2)  Yes, syndaemon needs to be executable.  I think that is already is when it's unpacked, but if it isn't, let me know, and I will amend the instructions.  To check your startup apps command, best thing to do is to copy, then paste into a terminal.  As for the switches, -t is what I prefer.  It's personal choice- see man syndaemon for options.

3) The error message here is quite normal.  Should have mentioned that, I just left that 'mv' line in for anyone who had an old version of the file in there.  Could you confirm- are your hotkeys now working?

Let us know how the media keys go with Ea nice, gnome music player.

Charlie

---

### Post by Pott on 2009-11-15
Ok thanks guys... turns out my info strings were indeed correct, so that wasn't the issue. 

The EuroDollar script isn't working, even after I run it into the terminal. The sh function disappears from the Command once I log out/back in.

Syndaemon is indeed executable... I can't find the man syndaemon file anywhere. I just left the file as it was then... I think I meant the actual script for the remapping of the mouse keys, but this one seems to work as my output seems to be 17, 18, 19 etc...

Hotkeys are working as far as I know, but for instance I still have the weird brightness controls, which I'm guessing this should have corrected (as in Jaunty) so I figured it didn't work. I'll try again by creating a new file, rebooting etc...


EDIT: just restarted x and reviewed the entire process:
After you guys' help from today, I'm 100% sure I did exactly as I should. Everything is correct file wise, folder wise etc...

I still have glitchy hotkey brightness control (which I'm guessing means the hotkeys aren't working as they should but I never use sleep or suspend or any others)
I still have no Euro Dollar signs, again which is very weird, it worked very well and very quick on Jaunty. Here, nothing. I checked the script, the only difference is the sh sign which disappears. 
The media keys still don't work. I double checked the .fdi files and their locations, all is ok. The media keys ARE mapped 17, 18, 19, 20, but still register as mouse clicks. My xbindkeysrc file is also correct... Weird :s

Thanks for all the help with this guys... Not sure what's off...

EDIT2:
AH! Getting there with the mediakeys
I'd forgotten to make xbindkeys executable at startup. I created an application for this but it didn't work...I think I may need to make it a launcher. 
Anyway... I typed in xbindkeys on the termial and then the keys worked with Exaile :) So we're 90% done there!
As for the hotkeys, still not sure about that. 
Still no eurodollar script working :(

EDIT3: 
Yep, Mediakeys are working!! Thanks so much guys, that's the big deal for me!
Also, the sh in front of the eurodollar script sticks now, but the script still doesn't work... Mhmm... :s

About the hotkeys, I realised that the brightness fix was done by backlisting video, which is something I've not done on Karmic. So for all I know they actually all work now.

---

### Post by FokkerCharlie on 2009-11-15
Glad you seem to have got there.

I'll take a look at the euro / dollar script later.  I don't bother with those keys myself, really.

Interestingly, the brightness controls work fine out of the box for me.  Strange.

Charlie

---

### Post by Pott on 2009-11-15
It works here too, but it works the same was as it did before the backlisting fix on Jaunty.

Ok I did a rounding of all the hotkeys:

Hot media keys work (fn + home, pg up etc...)
Brightness works, it's a bit glitchy
Sleep just brings me a black screen with blinking white cursor, nothing else. I had to manually restart the PC...
Touchpad enable/disable works
Num lock works
Scroll lock does NOT work
Screen off works
Switch screens, no clue, can't try this
Mute works
The one on F3 gives me power information
The one on F2 does nothing
The one on F1 does nothing

---

### Post by p3y on 2009-11-15
I still prefer a PageUp and PageDown on the €- and $-keys. This can be done by editing the file /lib/udev/keymaps/acer and editing the entries 0xB3 and 0xB4 to look like this:

```
0xB3 pageup
0xB4 pagedown

```

Percy

---

### Post by Dao984 on 2009-11-16
Help, eurodollar fix never worked on my laptop. Why?

Thanks all for all fixes and thank Fokker for your thread, my laptop is very cool whit them :)

---

### Post by FokkerCharlie on 2009-11-24
Hello!

Is anyone else finding Karmic a bit glitchy on this machine?  I have been using it now for a couple of weeks since the fresh install, and have the following issues:

- Suspend key isn't working.  I can suspend fine from the panl applet, or by closing the lid, but I'd prefer the key.  I have it set in keyboard shortcuts (where the key is detected fine), and also the power management app, but no joy.  I've also tried fiddling with the settings of each, without luck.  Oddly, it was working last week but has now stopped!

- Speaking of power management, I don't seem to be able to stop my display from going to sleep (dimming to darkness) when on AC or battery power.  That's very annoying when watching a movie or whatever.  I've got all the settings in power-management for the whole machine to stay awake.  Maybe I'm missing something?

- I have lost compiz quite a few times (although not in the last few days).  Suddenly, the window decoration and gnome-do will disappear, and I've ended up having to reboot.

- I can't mount / unmount my windows partition as a normal (non-root) user.  If anyone is able to do this, please could you post your fstab?

- VPN via pptp will only intermittently work.  I think that's not necessarily a problem with Karmic, mind.

Grrrr.

If you can shed any light on any of the above, please let me know!

Charlie

---

### Post by Dao984 on 2010-01-30
Hello
Can someone help us ? Mediakeys are ok with Totem and Rhythmbox but they dont work with Vlc. How can i use they on vlc? Thank you

[Help]("http://ubuntuforums.org/showthread.php?p=8749125#post8749125")

---

### Post by Dao984 on 2010-02-11
hi again,
im sry but i have some problems whit xubuntu karmic, can these multimadiakeys' fix work on xubuntu? I dont know xubuntu very well can someone help me? thx

---

### Post by SXW on 2010-04-13
I have a different solution for getting syndaemon to pick up the correct touchpad in Karmic. Maybe it helps you. I had to do two things, which I put into one file: /etc/hal/fdi/policy/touchpad.fdi

```

<?xml version="1.0" encoding="UTF-8"?>
<deviceinfo version="0.2">
  <device>
    <match key="input.x11_driver" string="synaptics">
      <merge key="input.x11_options.SHMConfig" type="string">on</merge>
    </match>
  </device>

  <device>
    <match key="info.udi" string="/org/freedesktop/Hal/devices/platform_i8042_i8042_AUX2_port_logicaldev_input">
      <merge key="input.x11_driver" type="string">none</merge>
    </match>
  </device>

</deviceinfo>

```The first part enables SHMConfig for all devices that a synaptics driver is loaded for by X11. Needed to get syndaemon to work at all.... The second part tells X11 to load driver "none" for the media keys on the right side of the keyboard. This driver does not exist, so in the X11 log file you will see a warning, but that does not matter: The effect is that the media keys are disabled. Since syndaemon now only sees one touchpad instead of two, it will always attach itself to the correct one, all problems fixed. Also works with the setting under System -> Preferences -> Mouse -> Touchpad

---

### Post by chemicalrulez on 2010-04-21
Hi,
i tried to follow this guide, but i have a problem during one step of the process.
When i execute

```
patch tools/syndaemon.c tools/syndaemon.patch
```I have

```

patching file tools/syndaemon.c
Hunk #2 FAILED at 477.
Hunk #4 FAILED at 563.
2 out of 5 hunks FAILED -- saving rejects to file tools/syndaemon.c.rej

```And at the end of all the process the media keys still don't work.
What do you think about it?
Bye!

---

### Post by FokkerCharlie on 2010-05-04
Hello!

Recently installed Lucid on my machine, and have been enjoying the biannual struggle with the media keys!

I see that the current (unpatched) release of synaptics still does not allow the -n switch.  I am seeing:

```
$ tools/syndaemon -n Touchpad
Unable to find a synaptics device.
```

I can't remap the media key buttons, either:

```
$ xinput set-button-map "Mediakeys" 1 2 3 17 18 19 20 8 9 10 11 12 13 14 15 16
unable to find device Mediakeys

```

Hmmm.

Anyone had any success with this on Lucid?

Cheers
Charlie

---

### Post by oleg89 on 2010-05-05
First of let me say I don't use the patched syndaemon. Instead I'm using the little script in the startup apps from [here]("http://swiss.ubuntuforums.org/showthread.php?t=997860") which I had to change a bit (replace tail with head) for lucid:
```

#!/bin/sh

#Remaps the second Synaptics touchpad entry.

xinput set-button-map "`xinput list | grep Synaptics | head -1 | grep -o id=.. | tr -d id=`" 1 2 3 17 18 19 20 8 9 10 11 12 13 14 15 16

```Furthermore (as in karmic) my bluetooth gets enabled at every start. In karmic I added the following to rc.local:
```
echo "0" > /sys/devices/platform/acer-wmi/rfkill/rfkill1/state
```But in lucid the rfkill1 is not always mapped to bluetooth, giving the result that sometimes my wlan was disabled but bluetooth was still enabled. So I had to put this in rc.local:
```

if [ `cat /sys/devices/platform/acer-wmi/rfkill/rfkill1/type` = "bluetooth" ]
then
echo "0" > /sys/devices/platform/acer-wmi/rfkill/rfkill1/state
fi
if [ `cat /sys/devices/platform/acer-wmi/rfkill/rfkill2/type` = "bluetooth" ]
then
echo "0" > /sys/devices/platform/acer-wmi/rfkill/rfkill2/state
fi

```I guess there is a more sophisticated approach with a for-loop, but I'm not quite sure how to do this in a script.

oleg

---

### Post by FokkerCharlie on 2010-05-06
Oleg...

Nice one.  I really didn't think about trying the solution that was working a year ago, but not since Karmic.

Still left with the syndaemon not working properly, mind.

Cheers
Charlie

---

### Post by oleg89 on 2010-05-06
Hey Charlie,

glad to be of help! Actually the script did also work for me in karmic. The problem was that the id had two digits (and still has in lucid, at least on my machine), so I replaced "id=." with "id=..".
So why do you still need the syndaemon, if that script works for you? Are there any advantages?
One last thing: Is the brightness control working for you properly in lucid? I had to blacklist the video module and add "acpi_backlight=vendor".

Anyways thanks so far for your guide!

oleg

---

### Post by Dao984 on 2010-05-14
hi all
im sry im not uderstund, can i use this fix for mediakeys in lucid? 
What can i do for mediakeys in lucid?
 Thx all for your works, unfortunally im a bit noob and i cant help.

---

### Post by p3y on 2010-05-16
> **FokkerCharlie said:**
> I can't remap the media key buttons, either:

```
$ xinput set-button-map "Mediakeys" 1 2 3 17 18 19 20 8 9 10 11 12 13 14 15 16
unable to find device Mediakeys

```


I am still using 

```
xinput set-button-map "`xinput list | grep Synaptics | head -1 | grep -o id=.. | tr -d id=`" 1 2 3 17 18 19 20 8 9 10 11 12 13 14 15 16
```

without any patches. Works flawlessly.

---

### Post by Jeff Hill on 2010-08-11
Hello, Charlie.
I'm a newbie to Ubuntu, running  Lucid on an Aspire 5920 (Ubuntu is my only op system). My touchpad has stopped working after being OK initially. I have some experience of DOS in the old days, so tried your patch. Inputing the line "./autogen.sh" then <Enter> I get 'bash: ./autogen.sh: Permission denied'. How do I get around this to continue, please? I tried prefacing the line with "Sudu" but this doesn't work either. Also how do I get out of terminal at this stage without wrecking my machine? is it OK to just close Terminal or will this leave behind changes that I have now done? Many Thanks, Jeff Hill.

---

### Post by Jeff Hill on 2010-08-11
> **FokkerCharlie said:**
> Okey, Dokey, fellow 5920(G) owners!

Here's some tips that may help to make your Karmic experience a little better.  Most of the methods described are as per those that worked for Jaunty (see thread [here]("http://ubuntuforums.org/showthread.php?t=997860"), but there are a few new issues that we need to take a look at.  Conversely, on my system, the brightness control now works correctly, so I have omitted the steps for fixing this.  If it's an issue for anyone else, please let us know.

All the guidance below is what works for me.  I am not an expert, and all advice comes with the usual disclaimers!


[FONT="Arial Black"]Part 1:  Media Keys[/FONT]

OK, we'll start off with the most complicated bit.  We need to patch xserver-xorg-input-synaptics to cope with the media keys.

- Get the sourcecode of syndaemon and build dependencies

```
apt-get source xserver-xorg-input-synaptics
sudo apt-get build-dep xserver-xorg-input-synaptics
```

- Patch syndaemon

```
cd xserver-xorg-input-synaptics-1.1.2
wget "http://bugs.gentoo.org/attachment.cgi?id=202431&action=view" -O tools/syndaemon.patch
patch tools/syndaemon.c tools/syndaemon.patch
```

- Configure and make

```
./autogen.sh
make
```

Now, we'll make 2 fdi files- one for the media keys, and one for the touchpad proper.

```
gksu gedit /etc/hal/fdi/policy/touchpad.fdi
```

Put this in the file, then save:

```
<?xml version="1.0" encoding="UTF-8"?>
<deviceinfo version="0.2">

  <device>
    <match key="info.udi" string="/org/freedesktop/Hal/devices/platform_i8042_i8042_AUX3_port_logicaldev_input">
        <merge key="info.product" type="string">Touchpad</merge>
        <merge key="input.x11_options.AlwaysCore" type="string">true</merge>
        <merge key="input.x11_options.RTCornerButton" type="string">2</merge>
        <merge key="input.x11_options.RBCornerButton" type="string">3</merge>
        <merge key="input.x11_options.LTCornerButton" type="string">4</merge>
        <merge key="input.x11_options.LBCornerButton" type="string">5</merge>
        <merge key="input.x11_options.TapButton1" type="string">1</merge>
        <merge key="input.x11_options.TapButton2" type="string">1</merge>
        <merge key="input.x11_options.TapButton3" type="string">1</merge>
        <merge key="input.x11_options.PalmDetect" type="string">0</merge>
        <merge key="input.x11_options.PalmMinWidth" type="string">0</merge>
        <merge key="input.x11_options.PalmMinZ" type="string">0</merge>
    </match>
  </device>

</deviceinfo>
```

Now for the mediakeys:

```
gksu gedit /etc/hal/fdi/policy/mediakeys.fdi
```

```
<?xml version="1.0" encoding="UTF-8"?>
<deviceinfo version="0.2">

  <device>
    <match key="info.udi" string="/org/freedesktop/Hal/devices/platform_i8042_i8042_AUX2_port_logicaldev_input">
        <merge key="info.product" type="string">Mediakeys</merge>
        <merge key="input.x11_options.AlwaysCore" type="string">true</merge>
    </match>
  </device>

</deviceinfo>
```

And save again.

Now, we need to make sure that we're using our newly patched version of Syndaemon, not the old one.  So go to System > Prefs > Startup Apps, and find the Syndaemon entry.  If you don't have one, you can create a new one.

Replace the command with:

```
/home/<username>/xserver-xorg-input-synaptics-1.1.2/tools/syndaemon -t -n Touchpad
```

Note the '-n Touchpad' bit.  The other switches are up to you.

Now we need to remap the media key 'buttons', so add another command to your startup apps (or replace the previous equivalent):

```
xinput set-button-map "Mediakeys" 1 2 3 17 18 19 20 8 9 10 11 12 13 14 15 16
```
You can call it what you like.

If you have not yet done so, install xbindkeys and xvkbd, and open the configuration file for editing:

```
sudo apt-get install xbindkeys
sudo apt-get install xvkbd
gedit .xbindkeysrc
```

Copy this text into the file:

#Mutlimedia control keys:
```

"xvkbd  -text "\[XF86AudioPlay]""
    b:17

"xvkbd  -text "\[XF86AudioStop]""
   b:18:

"xvkbd  -text "\[XF86AudioPrev]""
    b:19

"xvkbd  -text "\[XF86AudioNext]""
    b:20
```

This works perfectly with all the Gnome music players that I have tried.  While you're here, you can map your blue 'e' key to run Exaile, or whatever else you want:

```
#Map 'e' key to launch exaile
"exaile %f"
    c:219
```

It turns out that Karmic has integrated syndaemon, so to prevent two instances of the process starting, go to System > Prefs > Mouse > Touchpad, untick 'Disable touchpad when typing'.

And you're done.  Restart for the changes to take effect.  **NOTE:  THE BLUE E-KEY WILL ONLY WORK AFTER YOU HAVE COMPLETED PART 3 BELOW**

[FONT="Arial Black"]Part 2: The Hotkeys[/FONT]

If your hotkeys (the fn keys for suspend, etc) aren't working right, you can follow this section.  With thanks to Alkis and Percy for the work on [this]("https://bugs.launchpad.net/ubuntu/+source/hal-info/+bug/281951") bug.

Download a new fdi file from [here]("http://launchpadlibrarian.net/23227355/30-keymap-acer.fdi").  Now you need to replace your old /usr/share/hal/fdi/information/10freedesktop/30-keymap-acer.fdi file with the one you just downloaded.  The steps below assume that you have downloaded the file to your home folder.

**THIS IS RISKY.  PLEASE ONLY FOLLOW THESE STEPS IF YOU UNDERSTAND THEM, AND ARE ABLE TO UNDO THEM.  DO THIS AT YOUR OWN RISK!**

```
sudo mv /usr/share/hal/fdi/information/10freedesktop/30-keymap-acer.fdi /home/<yourusername>/30-keymap-acer-old.fdi
sudo cp 30-keymap-acer.fdi /usr/share/hal/fdi/information/10freedesktop/
```

Note that the first command may generate a 'file not found' error.  If so, don't worry, just carry on.  That should fix any issues with your fn keys.  It also sets us up for part 3.

[FONT="Arial Black"]Part 3:  Enable the &#8364; and $ keys[/FONT]

We need to make a script that will run every time you log in.  In this example, I will make a hidden folder in your home folder and put it in there.

Open a terminal, and type:
```
cd .startscripts
gedit eurodollar.sh
```

And paste this code:
```
#!/bin/sh
echo 'keycode 186 = dollar dollar dollar dollar dollar' | xmodmap -
echo 'keycode 185 = EuroSign EuroSign EuroSign EuroSign EuroSign' | xmodmap -
```

Now, to set this script to run on every login, go to System > Prefs > Sessions, and under Startup Programs, add again:
Name:  EuroDollar
Command: sh /home/<username>/.startscripts/eurodollar.sh
Description: Enables &#8364; and $ keys.

And close.  You should see this come into effect when you next restart X, or log out/in.

Please note that if you have multiple users on your system, you will need to follow parts 1 and 3 for each user.

[FONT="Arial Black"]Part 4:  Fix the glitchy sound.[/FONT]

You may have noticed some pops from the speakers from time to time.  It seems that this is an issue with power-saving.  To fix:

open a terminal and type:
```
/etc/modprobe.d/alsa-base.conf
```

At the start of the last line, insert: #   
You will probably have to re-start for this change to take effect.

-------------------

OK, that's it.  Let us know by posting on the thread how you have got on with the fixes above.  If there's anything missing or incorrect, please do post so that your corrections can help others.

Thanks to everyone who has contributed to the solutions posted above, including on the Intrepid / Jaunty thread, and a special shout to Mohr Tutchy who keeps coming up with the goods regarding xinput.

Cheerio!
Charlie
Hi. I'm a newbie running Lucid on Aspire 5920 (No windows, just Ubuntu). Touchpad not working after being OK initially. I tried to input your patch but after typing " ./autogen.sh I get "bash: ./autogen.sh: Permission denied. What do I do nest (I've tried prefacing the line with 'Sudo ' but then I get "Command not found". Also how can I get out of terminal at this stage without wrecking the system - is it OK to just close the Terminal, or will I be left with changes thet I might have done with the earlier lines? Thanks, Jeff Hill.

---

### Post by FokkerCharlie on 2010-08-11
Hi Jeff

I have somewhat moved on from my 5920G, so it's a little tricky to recreate the problems you are having.  However- did you start having issues with the touchpad BEFORE trying the tweaks?

Just to double-check (I was caught out by this) there's a fn-key on either one of the numbers or an f-key, it has a little finger-on-a-touchpad symbol on it... holding the 'fn' key and pressing it enables / re-enables the touchpad.  Have you tried that?

Charlie

---

### Post by Jeff Hill on 2010-08-11
Hi, Charlie.
Thanks for replying so quickly. I lost the trackpad after updating/installing more softwhere (I'm not sure exactly when, as I had it disabled for a while, and only found the problem when I tried to enable it with 'Fn,F7', - I think that is the key you referred to. I looked in System>Mouse and found it was showing as enabled, so installed "gsynaptics Touchpad Preferences" and tried that. That didn't work either (showed touchpad enabled). All this before I tried to input your tweak. I realize your code was intended for Karmic, but I couldn't find anything for Lucid, so had to try it anyway. Bear in mind, I am new at this, so am easily stumped!  Regards,.Jeff.:)

---

### Post by FokkerCharlie on 2010-08-11
Hi Jeff

I'm sorry, but I don't think that I'll be too much help at this, as my 5920g is 1000 miles away... but I suggest that you try booting an ubuntu live CD (or USB stick, or whatever you used to install) and see if your issue is with the installed OS or a deeper-level problem.

And yes, fn+f7 was the combo I was referring to.

Let us know how you get on.

Charlie

---

### Post by oleg89 on 2010-09-08
Hey Jeff,

do you have a multi-boot environment with windows? Because if I disable my touchpad in windows, I can't re-enable it in ubuntu. I have to boot windows, enable it and then i can en/disable it again in ubuntu.
Moreover [this thread]("http://ubuntuforums.org/showthread.php?t=1476344") may help you.
 
oleg

---

### Post by Dao984 on 2010-12-01
Ok guys, i installed kubuntu 10.10 in ours laptop, some problems whit nvidia drivers current and i fix it, now i have problems whit sleep mode.
Fn+F4 keys dont work. Sleep work fine but keys for sleep dont work.
I think its a know bug, look [here]("https://bugs.launchpad.net/kdebase/+bug/543022"), but i dont understund how i can fix it, only i know, maybe, its a authorizations problem. Can someone help me?
Fn+F1,F2 and F3 dont works too, but F4 is most important for me, thx u so much :) and sry my bad english.

Ok no problem, xev see Fn+F4 and others F, i solved whith xbindkeys :) 

oleg89 solution for mediakeys (scripts) work fine in maverick too, thx oleg :)

Only problem now are &#8364; and $ keys near the up-arrow key, but i never solved it :D

---

### Post by Blackkitten on 2011-10-15
Guys, thank you all, especially FokkerCharlie and Oleg89.
Media keys are working now. I've almost archieved harmony with my acer ! :-)

Btw, I'm on 11.10 and instructions are working as you can guess.

---

### Post by Blackkitten on 2012-04-29
12.04 is out and this method works perfectly.

---

