---
title: "[HOWTO] Fix for Stuck Volume/Multimedia Keys"
date: 2008-11-07
forum: Hardware
---

### Post by ktemkin on 2008-11-07
(ADDED NOTE: This is for users using the 'evdev' driver only. This includes most of the users who have recently upgraded to Intrepid.)

First off, this isn't a permanent fix for the volume/media key issues started in Intrepid. It's just a port of a small fix found in the 'kbd' driver present in Hardy to the 'evdev' driver present in Intrepid. Something similar, may eventually may work its way into future evdev releases, but for now, several developers are having deciding where the 'bug' should be handled.

The issue is that on certain systems' PS/2 keyboards, the volume control keys (and certain media keys) report a KEY_DOWN when they're pressed, but not a KEY_UP when they're released. The result of this is that the system acts like they're stuck- and repeats them indefinitely, often preventing use of the keyboard and/or mouse.

If your system seems to be affected by this bug, this is a detailed workaround. It requires for you to use the terminal, perform some file copy operations, and perform some compilations yourself. It also may require you to think a little, instead of following step by step instructions. If you're not comfortable with any of this, you can simply remap your volume controls to other keys using System->Preferences->Keyboard Shortcuts.

A warning: you are modifying the primary keyboard input drivers for your graphical user interface. There is always the possibility that something can go wrong. You can take steps to recover from these, using one of the Virtual Terminals (CTRL+ALT+F2, for example), or a recovery mode prompt, but *in the end all responsibility for your system's state is yours.*

That said, there are two basic methods:

1) Download a pre-modified version of evdev-2.0.99, compile it, and install it. This method gives you the least customization, restricts you to evdev-2.0.99 in the event that a later stable version has been released, and only fixes the volume keys, but is easiest and doesn't require any mucking about with C code.

2) Download the current version of the evdev source from the [Ubuntu Package Repository]("http://packages.ubuntu.com/source/jaunty/xserver-xorg-input-evdev"). Customize it according to this How-To, then compile and install.

```
Text enclosed in these boxes are intended to be typed into the terminal.
```

You will probably have to re-apply this patch using 'Method 2' below each time there's an evdev update, if you want to install the evdev update. Otherwise, simply choose not to install updates to evdev (not reccomended).

**Method 1**

1) Back up your current evdev driver, just in case. This line will back up to your home directory (~/), you can modify it if you want; just remember where you put it for later.

```
 cp /usr/lib/xorg/modules/input/evdev_drv.so ~/
```

2) Download my modified evdev-2.0.99 driver, if you're using intrepid:

```

wget http://labs.ktemkin.com/ubuntu/evdev_fix_2.0.99.tar.gz

```

or my modified evdev-2.1.1 driver, if you're using jaunty;

```
 wget http://www.ktemkin.com/content/ubuntu/evdev_fix_2.1.1.tar.gz 
```

or, if you're using jaunty and have a Toshiba model with a volume wheel:

```
 wget http://www.ktemkin.com/content/ubuntu/evdev_fix_2.1.1-toshiba.tar.gz 
```

3) 'Unzip' it to the evdev_fix folder (you'll need to change this to 2.0.99 if you're using intrepid, or to 2.1.1-toshiba if you're using the Toshiba version.):

```
 tar -zxvf evdev_fix_2.1.1.tar.gz 
```

4) Change the working directory to the evdev_fix folder:

```
 cd evdev_fix
```

5) You're ready to compile! Skip to the 'both methods' section.

**Method 2**

This method assumes a bit more technical knoweldge, so simple things like downloading and decompressing won't be explained.

If you're more comfortable with the GUI:

1) Download the newest version of the evdev driver from the [Ubuntu Package Repository]("http://packages.ubuntu.com/source/intrepid/xserver-xorg-input-evdev") (Intrepid) or [Ubuntu Package Repository]("http://packages.ubuntu.com/source/jaunty/xserver-xorg-input-evdev") (Jaunty). 

2) Untar it to a folder inside of your home directory.

Or, if you're more comfortable with the terminal:

1/2) This will download the current evdev source for you:

```
apt-get source xserver-xorg-input-evdev
```

3) Inside the folder for the evdev version you just downloaded, you'll find a 'src' folder. Look for the block that contains:

[php]
    /* filter repeat events for chording keys */
    if (value == 2 &&
        (ev->code == KEY_LEFTCTRL || ev->code == KEY_RIGHTCTRL ||
         ev->code == KEY_LEFTSHIFT || ev->code == KEY_RIGHTSHIFT ||
         ev->code == KEY_LEFTALT || ev->code == KEY_RIGHTALT ||
         ev->code == KEY_LEFTMETA || ev->code == KEY_RIGHTMETA ||
         ev->code == KEY_CAPSLOCK || ev->code == KEY_NUMLOCK ||
         ev->code == KEY_SCROLLLOCK)) /* XXX windows keys? */
        return;
[/php]

After it, on a new line, copy and paste the following code:

[php]
    /* fix events for volume keys */
    if(ev->code == KEY_VOLUMEDOWN || ev->code == KEY_VOLUMEUP) //MODIFY THIS LINE
    { 
	//post a keydown and then a keyup, as media keys have no automatic key-up
	xf86PostKeyboardEvent(pInfo->dev, code, 1);
	xf86PostKeyboardEvent(pInfo->dev, code, 0);
	return;
    }
[/php]

4) Customize. At this point, you'll be customizing the line that preceeds the "Modify this line" comment. You can add additional keycodes by adding "ev->code == YOUR_KEYCODE", seperating each instance with a pair of double bars. "||". You can find additional keycodes using either the 'evtest' utility in the console, or in [<linux/input.h>]("http://www.gelato.unsw.edu.au/lxr/source/include/linux/input.h").

For example, if you needed to fix the mute key on your keyboard as well, your block would look like:

[php]
    /* fix events for volume keys */
    if(ev->code == KEY_VOLUMEDOWN || ev->code == KEY_VOLUMEUP ||  ev->code == KEY_MUTE) //MODIFY THIS LINE
    { 
	//post a keydown and then a keyup, as media keys have no automatic key-up
	xf86PostKeyboardEvent(pInfo->dev, code, 1);
	xf86PostKeyboardEvent(pInfo->dev, code, 0);
	return;
    }
[/php]

5) Continue on to 'Both Methods' below.

**Both Methods**

1) Compile. Firstly, we'll need to make sure you have everything set up to compile. Install anything this step requires, or just continue if it tells you you're 'already newest version'. You'll need to type in your password to give yourself installation rights.

```
 sudo apt-get install build-essential libtool automake gcc xorg-dev xutils-dev
```

This *should* be the same as:

```
 sudo apt-get build-dep xserver-xorg-input-evdev 
```

but for safety, especially if you're using method 1, I recommend executing both.

Next, we have to generate our 'Makefile'. This tells the computer how to compile. It will probably generate a lot of text output. 

```
./autogen.sh
```

Once it generates succesfully, it's time to perform the compilation itself.

```
make
```

2) Install. First, tell make to install the file:

```
sudo make install
```

Now, copy it to the correct location. *There's a strong possibility this will restart your x-server (GUI)*, so make sure you've saved everything you want to save, as if you were restarting your computer. When it restarts, your volume keys should work!

```
sudo cp /usr/local/lib/xorg/modules/input/evdev_drv.so /usr/lib/xorg/modules/input/
```

If your x-server didn't restart you can restart it by pressing CTRL+ALT+BACKSPACE, or by restarting your computer.


**Recovery**

If your keyboard/mouse stopped working, don't panic! Instead, switch to one of your virtual terminals by pressing CTRL+ALT+F2. Then, execute the following command:

```
sudo cp ~/evdev_drv.so /usr/lib/xorg/modules/input/
```

That will restore your original driver. Then, restart the computer with the following commands.

```
sudo shutdown -r 0
```

---

### Post by rekado on 2008-11-09
Thanks for this workaround. While trying the easy method 1 autogen.sh stops with the following error:

```

./configure: line 11656: syntax error near unexpected token `RANDR,'
./configure: line 11656: `XORG_DRIVER_CHECK_EXT(RANDR, randrproto)'

```

I will try method 2 now...


EDIT:
okay, that's the same with method 2. I'm probably just missing some development libraries.

EDIT 2:
configuration works with the xorg-dev metapackage installed. How could I miss that... hehe!

---

### Post by ktemkin on 2008-11-09
Oops. I missed a dependency. I'll add that above. Thank you.

---

### Post by rekado on 2008-11-09
It didn't work for me. After typing in the line to replace the driver the X server crashed (of course) and I was asked to re-login. However, input from the keyboard was not recognized any more. I could switch to tty1 but there was just some purple pattern. So I decided to just press the power button to restart. I go to the login screen again but still no input was accepted. This time switching to tty1 worked, I logged in and tried the recovery procedure.
For me it only worked when changing the recovery line to:

```

sudo cp ~/evdev_drv.so /usr/lib/xorg/modules/input/

```

i.e. copying to the same pathe where we took the backup from. I think this needs to be changed as the original line (with the "local" in between) didn't work.

Sad to say it didn't work. Did I do something obvious wrong?

---

### Post by ktemkin on 2008-11-09
Yes, the backup line was a typo. It has been corrected. Did you use Method 2 the time that it didn't work? If so, please try Method 1 and tell me if your results differ. Any additional information you can give me about your procedure would help immensely.

If you did use Method 2, please post your modified code.

---

### Post by rekado on 2008-11-10
I used method 2 but I just entered wrong key codes. So just now I performed method 1 again and it worked like a charm! Now I can adjust my volume without locking up the X-session.

Thanks a lot! More people should read this.

---

### Post by jrf2027 on 2008-11-10
Worked like a charm - fixed my volume control issues described in [http://ubuntuforums.org/showthread.php?t=964870]("http://ubuntuforums.org/showthread.php?t=964870").  Thanks for your work!

---

### Post by ztrange on 2008-11-14
Also method 1 worked like a charm, thank you very much. Just one question, wont it prevent me from getting it fixed whenever the official patch arives?

---

### Post by hirev on 2008-11-14
Thank you for the fix.

---

### Post by lolo67 on 2008-11-16
:lolflag: Thanks ktemkin, I used method 1 and it worked great:):KS

I got a email from the bug on LaunchPad [https://bugs.launchpad.net/ubuntu/+bug/278781](https://bugs.launchpad.net/ubuntu/+bug/278781) , I will thank you over there too.

thank you.

---

### Post by dldeskins on 2008-11-16
This did not work for me, I have a Toshiba Satellite U305-S7448.  I used Method 1.  Now, the volume control knob does not control volume, but it now does not "lock" the system (i do not have to use CTRL-ALT-F1 to get out of it).  While this is much better, I still have to use the desktop applet or such to control the volume.

Thanks

---

### Post by ktemkin on 2008-11-16
> **ztrange said:**
> Also method 1 worked like a charm, thank you very much. Just one question, wont it prevent me from getting it fixed whenever the official patch arives?

It shouldn't. The APT package manager doesn't know we're replacing the files- so when you download an evdev update, it'll simply replace your hand-patched driver.

[quote="dldeskins"]This did not work for me, I have a Toshiba Satellite U305-S7448. I used Method 1. Now, the volume control knob does not control volume, but it now does not "lock" the system. [/quote]

That's... weird. It doesn't seem to be autorepeating anymore, which indicates to me that the code is affecting the right keys... but the evdev driver no longer seems to be registering their key-down in the first place. And since this code just says 'KEY-DOWN', 'KEY-UP', it might be possible that something on your system is causing them to happen too quickly for the system to even count it as a keypress.

Even odder, as I'm using a Satellite U305 myself; so I can say with reasonable certainty that it's probably not your hardware. 

If you wouldn't mind answering a few questions for me...

1) Can you make sure that your keyboard shortcuts are still mapped to XF86VolumeDown and XF86VolumeUp in System->Preferences->Keyboard Shortcuts? I know it's basic, but I have to ask. 

2) Did you ever use Hardy Heron? Did the volume knob work with that? Did it work with any past versions? Those used a different driver (kbd.so), which had a similar patch. 

3) Can you run the following for me, spin the volume wheel a little while it's running and post the results? 

```
sudo evtest /dev/input/event1
``` 

'event1' should be the event number of your keyboard.
You can press CTRL+C once you spin the volume wheel to exit. 

I'd appreciate it if you included just a few lines of the information it prints when it first runs, too. They should look like this:

```

Input driver version is 1.0.0
Input device ID: bus 0x11 vendor 0x1 product 0x1 version 0xab41
Input device name: "AT Translated Set 2 keyboard"
<snip>
    Event code 113 (Mute)
    Event code 114 (VolumeDown)
    Event code 115 (VolumeUp)
<snip>

```

(Spinning the volume wheel might not do anything to the terminal. That's good.)

---

### Post by dldeskins on 2008-11-16
> **ktemkin said:**
> 
1) Can you make sure that your keyboard shortcuts are still mapped to XF86VolumeDown and XF86VolumeUp in System->Preferences->Keyboard Shortcuts? I know it's basic, but I have to ask. 

They are still mapped that way.

> **ktemkin said:**
> 
2) Did you ever use Hardy Heron? Did the volume knob work with that? Did it work with any past versions? Those used a different driver (kbd.so), which had a similar patch. 

Yes, this was an upgrade.  I have been using Ubuntu since 7.04. No patches, everything worked.

> **ktemkin said:**
> 
3) Can you run the following for me, spin the volume wheel a little while it's running and post the results? 

```
sudo evtest /dev/input/event1
``` 

'event1' should be the event number of your keyboard.
You can press CTRL+C once you spin the volume wheel to exit. 

I'd appreciate it if you included just a few lines of the information it prints when it first runs, too. They should look like this:

```

Input driver version is 1.0.0
Input device ID: bus 0x11 vendor 0x1 product 0x1 version 0xab41
Input device name: "AT Translated Set 2 keyboard"
<snip>
    Event code 113 (Mute)
    Event code 114 (VolumeDown)
    Event code 115 (VolumeUp)
<snip>

```

(Spinning the volume wheel might not do anything to the terminal. That's good.)

```

Input driver version is 1.0.0
Input device ID: bus 0x11 vendor 0x1 product 0x1 version 0xab41
Input device name: "AT Translated Set 2 keyboard"
Supported events:
  Event type 0 (Reset)
    Event code 0 (Reset)
    Event code 1 (Key)
    Event code 4 (?)
    Event code 17 (LED)
    Event code 20 (Repeat)
  Event type 1 (Key)
<snip>
    Event code 113 (Mute)
    Event code 114 (VolumeDown)
    Event code 115 (VolumeUp)
<snip>

```
It did nothing.


Thanks very much for your time.  That's what makes Ubuntu and this community fun... you can actually find out info and get help.

---

### Post by dldeskins on 2008-11-16
It is working now!

When I was trying to fix this earlier, I found a thread that said to install pulse Audio.  After i had posted the last reply, I purged all of the pulse audio stuff and force reloaded alsa, and it worked. I rebooted to make sure.

Thanks again. :)

(Now if i can only get the wifi stuff fixed)
[http://ubuntuforums.org/showthread.php?t=983365](http://ubuntuforums.org/showthread.php?t=983365)

---

### Post by ktemkin on 2008-11-16
Good! Glad to hear so many of you have gotten this working. I must say- I've only been using Linux exclusively for a short while now, and it's absolutely a breath of fresh air to have open source drivers.

It's a great feeling to be able to see something that bothers you- or doesn't work- and change it programatically with relative ease. Open source really is wonderful.

---

### Post by Jon Bradbury on 2008-11-30
I can't get it to compile (in Ibex)...

[PHP]libtool: compile:  gcc -DHAVE_CONFIG_H -I. -I.. -g -O2 -I/usr/include/xorg -I/usr/include/pixman-1 -I../src -MT evdev.lo -MD -MP -MF .deps/evdev.Tpo -c evdev.c  -fPIC -DPIC -o .libs/evdev.o
evdev.c: In function ‘EvdevKbdCtrl’:
evdev.c:707: warning: ignoring return value of ‘write’, declared with attribute warn_unused_result
evdev.c: At top level:
evdev.c:1445: error: ‘PACKAGE_VERSION_MAJOR’ undeclared here (not in a function)
evdev.c:1445: error: ‘PACKAGE_VERSION_MINOR’ undeclared here (not in a function)
evdev.c:1445: error: ‘PACKAGE_VERSION_PATCHLEVEL’ undeclared here (not in a function)
make[2]: *** [evdev.lo] Error 1
make[2]: Leaving directory `/home/jon/evdev/evdev_fix/src'
[/PHP]

Hacking in these values (2, 0, 99 respectively) leads to other problems, but these are in the man directory, so I gues we can skip 'em.

Let's see if it works... :)

---

### Post by Jon Bradbury on 2008-11-30
...nope  :(

See this question for more details : [http://ubuntuforums.org/showthread.php?t=980848](http://ubuntuforums.org/showthread.php?t=980848)

I suspect the keycode I have put in evdev.c is being picked up and processed by another part of the system...

---

### Post by ktemkin on 2008-12-02
Yes, your issue definitely seems like the same one. Can I ask if the compile errors happens if you compile evdev without any of your changes?

---

### Post by Citizen_Kane01 on 2008-12-10
Used your pre- 1 or 2 suggestion as a workaround! (remapping keys) Brand new to Linux and it is very exciting, but complex fixes are a bit scary still. Thanks for a good solution.

---

### Post by ThinkDave on 2008-12-11
```
evdev.c: In function ‘EvdevKbdCtrl’:
evdev.c:705: warning: ignoring return value of ‘write’, declared with attribute warn_unused_result
evdev.c: At top level:
evdev.c:1443: error: ‘PACKAGE_VERSION_MAJOR’ undeclared here (not in a function)
evdev.c:1443: error: ‘PACKAGE_VERSION_MINOR’ undeclared here (not in a function)
evdev.c:1443: error: ‘PACKAGE_VERSION_PATCHLEVEL’ undeclared here (not in a function)

```

Awww :( i was really hoping id fix the problem but im struggling here any help?

---

### Post by ztrange on 2008-12-11
That's odd, just yesterday I used the fix 1 to correct the problem in my laptop. I had just formated and reinstalled everything, I did it with the latest updates for everything...

What exactly did you do?

---

### Post by ThinkDave on 2008-12-11
Tried both methods it configures but when it comes to making the package it halts on those errors like the other poster i hard coded the version information in but that only created other errors later on. I'm assuming I'm missing a dependency or something. Whilst its not a brand new install it was a fresh install of Ibex a few months back and I really don't want to have to wipe it and start again.
I think I'm using the proposed updates could that be causing a conflict?

---

### Post by kyle.p on 2008-12-12
I was having errors like this as well:
```
evdev.c:1443: error: ‘PACKAGE_VERSION_MAJOR’ undeclared here (not in a function)
evdev.c:1443: error: ‘PACKAGE_VERSION_MINOR’ undeclared here (not in a function)
evdev.c:1443: error: ‘PACKAGE_VERSION_PATCHLEVEL’ undeclared here (not in a function)
```

This is on a fresh install of 8.10, minutes after fully updating everything (160 updates.. wow that took a long time!).  I was previously having the same issues in Fedora on my other partition, was pretty frustrated that it was happening in Ubuntu (although expected, considering the nature of the problem).

I got "METHOD 1" to work by just defining PACKAGE_VERSION_MAJOR, PACKAGE_VERSION_MINOR and PACKAGE_VERSION_PATCHLEVEL in evdev_fix/src/evdev.c as below:

```
/*******************************/
/*change this if does not work */
#define PACKAGE_VERSION_MAJOR 1
#define PACKAGE_VERSION_MINOR 2
#define PACKAGE_VERSION_PATCHLEVEL 0
/*******************************/ 
```

I placed it in the section "evdev flags" underneath the line:
```

#define COMPOSEFLAG	16
```


That should be about line 93...

There was another error afterwards (I think it had to do with man files?) but I ignored that and continued.  

Honestly, I don't know enough to say if this will cause any issues later. I got frustrated and took the risk myself. 

Hope this helps and thanks for the post! I can finally use my computer without accidentally cranking up the volume to max, and having my xorg mess up as well! 

-Kyle

---

### Post by ktemkin on 2008-12-12
I think it's yet again another dependency problem. I believe you're missing the set of macros that define these parameters.

I know on several other distributions it's called 'xorg-macros' or 'util-macros', but I thought it was obsoleted in newer releases of X.

---

### Post by kyle.p on 2008-12-12
Thanks for the info ktemkin.  I will look into this a little further.

I would rather I fix this properly rather than just slapping lipstick on it as I had done. 

In the meantime, do you know if there would be any harm in not having xorg-macros?  I can't really seem to find too much information on it.

-k

---

### Post by ThinkDave on 2008-12-13
Thanks ktemkin it was missing **xutils-dev** (which contains the macros) so probably good idea to add that to the original post.

Edit: Fixxxxxxed! ahhh thanks for that accidentally hitting the volume control was a nightmare.

---

### Post by sopak on 2008-12-30
Thousand thanks, it worked wonderfully on my Toshiba U300-11Z. I used the Method 1.

---

### Post by jachavezd on 2009-01-03
Thanks a lot, method one worked like a charm.

---

### Post by falconstd71 on 2009-01-12
By Method 1 works Perfeclty. Thanks a lot.

---

### Post by polyplay26 on 2009-02-18
I tried method 1 with the following error:
make
...
evdev.c:1000: error: too few arguments to function ‘XIRegisterPropertyHandler’
make[2]: *** [evderev.lo] Error 1
make[2]: Leaving directory `/home/paul/evdev_fix/src'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/paul/evdev_fix'
make: *** [all] Error 2

Please help!

FSC Amilo PI 3525, Jaunty Jackalope Alpha 4

---

### Post by simon_wrafter on 2009-03-02
> **polyplay26 said:**
> ... Jaunty Jackalope Alpha 4

On jaunty you should use method 2, since xserver-xorg-input-evdev is (currently) on version 1:2.1.1-1ubuntu3.

Also I say use ```
sudo apt-get build-dep xserver-xorg-input-evdev
``` to satisfy dependencies, makes it that much easier. :) That goes for everyone!

---

### Post by Mkve on 2009-03-21
Method 1 worked for me. Thanks very much for this! :)

---

### Post by mwacky on 2009-04-06
Method 1 worked perfectly for me, thank you!

---

### Post by ztrange on 2009-04-13
> **simon_wrafter said:**
> On jaunty you should use method 2, since xserver-xorg-input-evdev is (currently) on version 1:2.1.1-1ubuntu3.


True, method 1 failed on jaunty, used method 2 successfully.

---

### Post by pekka.fi on 2009-04-15
I had also keyboard jam problem with my fujitsu-siemens amilo 1510. Ubuntu did jam when fn+vol keys were pressed.

I used this thread instructions and it fixed it for me:


-Peter

---

### Post by jrf2027 on 2009-04-21
Method 2 works great in Jaunty.  I used the evdev source file found [here]("http://packages.ubuntu.com/source/jaunty/xserver-xorg-input-evdev").

---

### Post by ktemkin on 2009-04-23
> sudo apt-get build-dep xserver-xorg-input-evdev

I can't believe, after all this time, I didn't know about that. You learn something new every day, 

I guess, with jaunty, I'd better create a new Method #1 file. Possibly a patch/install script. I'll look at it when I'm less busy with work- maybe this weekend.

---

### Post by heyho on 2009-04-24
I have been looking for this fix since I upgraded from gutsy - using a fujitsu siemens 1505, and it's been driving me mad.

I will do a clean jaunty install at the weekend, and have a go with method 2.

Can't believe I've only just found this thread!

---

### Post by mwacky on 2009-05-03
> **heyho said:**
> I have been looking for this fix since I upgraded from gutsy - using a fujitsu siemens 1505, and it's been driving me mad.

I will do a clean jaunty install at the weekend, and have a go with method 2.

Can't believe I've only just found this thread!

Yeah, there are plenty of posts with people asking howto fix this.

Method 1 worked for me in Intrepid and Method 2 for Jaunty....

---

### Post by Altay_H on 2009-05-08
I have a few questions...

1) After the fix, does pressing and holding down the volume up/down button only change the volume by one increment, or does it continue to increase/decrease the volume until the button is released?

2) Will the fix affect the behavior of the buttons in the Virtual Terminals? Without the fix they currently behave perfectly in the Virtual Terminals.

3) If I use Method 2 in Jaunty and the bug is fixed, will the eventual evdev driver update permanently solve the problem, or will it require some hacking?

4) What exactly does the previously mentioned "sudo apt-get build-dep xserver-xorg-input-evdev" do?

---

### Post by meditatingfrog on 2009-05-08
i tried method 2, and when I typed make, I got these warnings and errors:  

evdev.c:696: warning: ignoring return value of &#8216;write&#8217;, declared with attribute warn_unused_result
evdev.c: In function &#8216;EvdevInit&#8217;:
evdev.c:989: warning: passing argument 2 of &#8216;XIRegisterPropertyHandler&#8217; from incompatible pointer type
evdev.c:989: error: too few arguments to function &#8216;XIRegisterPropertyHandler&#8217;
make[2]: *** [evdev.lo] Error 1
make[2]: Leaving directory `/home/buddha/Desktop/xserver-xorg-input-evdev-2.0.99+git20080912/src'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/buddha/Desktop/xserver-xorg-input-evdev-2.0.99+git20080912'
make: *** [all] Error 2

I have no idea what I could be.  I tried the sudo apt-get build-dep xserver-xorg-input-evdev but I still got the same warnings and errors.  ./autogen.sh worked fine.  

I even tried running make without the pasted code, still got the same errors.

EDIT:  I'm running Jaunty

---

### Post by noOneSpecial on 2009-06-01
I got the same error as you meditatingfrog.

If you follow the steps in the fix, the link to the evdev source is to the intrepid version. If you use the jaunty source all is well !

[http://packages.ubuntu.com/source/jaunty/xserver-xorg-input-evdev](http://packages.ubuntu.com/source/jaunty/xserver-xorg-input-evdev)

jrf2027 mentions using the jaunty source earlier in the thread, thanks !

---

### Post by heyho on 2009-06-01
Can't thank you enough - method 2 worked in the end!!! Woot!!!

I can finally use my favorite laptop again :)

---

### Post by meditatingfrog on 2009-06-01
Thanks for the heads up noOneSpecial.  I downloaded a copy and was going to go through the work again, but decided instead to remap my keys and wait for the next version of Ubuntu to come out.  I'm sure in time it will get fixed, and I think it might be better to work on something else, like my website, blog and writing.  

Glad you got it working.

---

### Post by ktemkin on 2009-06-08
Updated with Jaunty fixes and a new version for people with certain Toshiba models with a touchy volume wheel. Toshiba version is going to be obsoleted shortly by a newer fix anyways.

---

### Post by meditatingfrog on 2009-08-04
> **ktemkin said:**
> Updated with Jaunty fixes and a new version for people with certain Toshiba models with a touchy volume wheel. Toshiba version is going to be obsoleted shortly by a newer fix anyways.

Ktemkin:

Just revisited this "project", and this time compiling worked.  

Thank you.

Kevin

---

### Post by ouq77 on 2009-10-05
@ktemkin You have no idea how long I've been looking for a fix for this VERY annoying problem.  Thank you!  Method 2 worked on my Fujitsu Amilo Xi3650.

:guitar:

---

### Post by Liakopaido on 2009-10-21
That's a really good fix from ktemkin. Thanks a lot dude, now I can use the fn+volume keys on my Fujitsu Siemens Pi 2550 Laptop!!!!
But, since Karmic Koala is getting released soon, I need to know: how can this solution be applied to Karmic Koala?

Edit: I used the evdev 2.1.1 driver for Jaunty on Karmic and it worked just fine!!!
       Also, I tried to use the 2.2.5 which is Karmic's evdev driver but I couldn't find autogen.sh in the downloaded tar.gz.
       Strange... Shouldn't the package contain autogen.sh?
       Would the autogen.sh from 2.1.1 work for 2.2.5?

---

### Post by drvista on 2009-10-29
please i just installed karmic and i did try your fix before on jaunty and it worked will but not working in karmic

---

### Post by drvista on 2009-10-30
plz help me fix it i did all and changed the premissions of autogen and it worked but after reboot same issue present

---

### Post by drvista on 2009-10-30
could you do that fix on karmic ??
i tried to do that but the fix compile suusccfully but not working

---

### Post by allaf on 2009-11-01
I can confirm that it doesn't work for karmic. Very annoying because my keyboard worked fine with jaunty!
I also tcompile d the jaunty versio  and tried it but the result is not good : the key doesn't repeat itself anymore but it looks like it doesn't do anything

---

### Post by mrvanes on 2009-11-07
I also had problems fixing this bug under Karmic, but fixed the fix ;)

I did some testing and it turns out my volume/mute keys (now?) generate a value = 2 for all keypresses except the first one. That is why it works the first keypress. In the Karmic evdev.c now is a conditional statement after the 'if (value = 2)' code, which takes all kinds of dead keys into account (?), but only #if GET_ABI_MAJOR(ABI_XINPUT_VERSION) <= 2. It turns out the the dead-key code isn't compiled in (GET_ABI_MAJOR(ABI_XINPUT_VERSION > 2?) so that for every volume key press except the first, the routine immediately returns, without generating any keypress nor release.

The simplest fix for this is to insert the fix-code ABOVE the 'if (value = 2)' condition.
I'm not sure WHY the conditional statement is there and what I'm going to break by putting the code above, but my volume keys work again ;)

Hope this helps.

---

### Post by drvista on 2009-11-07
[COLOR="Red"][CENTER]**[SIZE="4"]This is  a rewrite of the fix [/SIZE]**[/CENTER][/COLOR]

1) Back up your current evdev driver, just in case. This line will back up to your home directory (~/), you can modify it if you want; just remember where you put it for later.


 > cp /usr/lib/xorg/modules/input/evdev_drv.so ~/






2) This will download the current evdev source for you:



> 
apt-get source xserver-xorg-input-evdev




3) Inside the folder for the evdev version you just downloaded, you'll find a 'src' folder. Look for the block that contains:

 

>    /* Filter all repeated events from device.
       We'll do softrepeat in the server, but only since 1.6 */
    if (value == 2
#if GET_ABI_MAJOR(ABI_XINPUT_VERSION) <= 2
        && (ev->code == KEY_LEFTCTRL || ev->code == KEY_RIGHTCTRL ||
            ev->code == KEY_LEFTSHIFT || ev->code == KEY_RIGHTSHIFT ||
            ev->code == KEY_LEFTALT || ev->code == KEY_RIGHTALT ||
            ev->code == KEY_LEFTMETA || ev->code == KEY_RIGHTMETA ||
            ev->code == KEY_CAPSLOCK || ev->code == KEY_NUMLOCK ||
            ev->code == KEY_SCROLLLOCK) /* XXX windows keys? */
#endif
            )
	return;





[COLOR="Red"]**Above  it**[/COLOR], on a new line, copy and paste the following code:


   >  /* fix events for volume keys */
    if(ev->code == KEY_VOLUMEDOWN || ev->code == KEY_VOLUMEUP) //MODIFY THIS LINE
    { 
    //post a keydown and then a keyup, as media keys have no automatic key-up
    xf86PostKeyboardEvent(pInfo->dev, code, 1);
    xf86PostKeyboardEvent(pInfo->dev, code, 0);
    return;
    }  



Then install the needed packages for compiling

>  sudo apt-get install build-essential libtool automake gcc xorg-dev xutils-dev




Compile. Firstly, we'll need to make sure you have everything set up to compile. Install anything this step requires, or just continue if it tells you you're 'already newest version'. You'll need to type in your password to give yourself installation rights.

> cd xserver-xorg-input-evdev-2.2.5
chmod +x autogen.sh
./autogen.sh
make
sudo make install
sudo cp /usr/local/lib/xorg/modules/input/evdev_drv.so /usr/lib/xorg/modules/input/


Recovery

If your keyboard/mouse stopped working, don't panic! Instead, switch to one of your virtual terminals by pressing CTRL+ALT+F2. Then, execute the following command:

Code:

> sudo cp ~/evdev_drv.so /usr/lib/xorg/modules/input/

That will restore your original driver. Then, restart the computer with the following commands.

Code:

> sudo shutdown -r 0

---

### Post by mrvanes on 2009-11-09
Just a tiny nitpicky detail: you write about looking for code in the 'src' directory. It would be very helpful to hint that this code actually exists in evdev.c.

And another thing: How am I going to press CTRL-ALT-F2 if my keyboard stopped responding? ;)

---

### Post by jrf2027 on 2009-11-13
I haven't had a chance to upgrade to Karmic yet...I'm planning on trying 64-bit this time around, does anybody know if this fix is necessary on 64-bit, and if it is, is it the same as what is posted above?

---

### Post by allaf on 2009-11-13
just to let you know my keyboard is working again, i didn't do anything except applying updates on karmic (64bit version).

---

### Post by ihateregistering1 on 2009-11-18
how can it be, this _still_ has to be fixed by hand?!

---

### Post by noureddineam on 2009-11-30
thank you [drvista]("http://ubuntuforums.org/member.php?u=227498") !! your fix for karmic worked great on my HP zv6000 laptop

---

### Post by aharown07 on 2010-03-03
Im using Karmic now... (actually Mint 8) and trying to implement this for my Dell 1558.
When I do step 2 I get
> E: You must put some 'source' URIs in your sources.list

Not sure what I need to add to my sources. Advice?

Edit: added sources in the "software sources" tool, but now I get this...
> E: Unable to find a source package for xserver-xorg-input-evdev

So I still don't have the right item there I guess?
(This is probably because I'm in Mint and the Ubuntu "source code" repos. is not enabled by default. If someone can tell me what it is, I can add manually)

Edit: I think I've got it. Do tell me if I'm wrong:
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic main restricted

Seems to be working

---

### Post by aharown07 on 2010-03-05
OK... post 54 seems to make some assumptions about the user's knowledge of Linux. I'm a noob I guess.

I got through step 2.

Now step 3 refers to "the folder for the evdev version you just downloaded." Where is that?
I have two archive files in my home directory now: xserver-xorg-input-evdev_2.2.5.orig.tar.gz and xserver-xorg-input-evdev_2.2.5-1ubuntu6.diff.gz

Step 3 then says "you'll find a 'src' folder, look for the block that contains..."

Well, the xserver-xorg-input-evdev_2.2.5.orig.tar.gz file does contain a src folder, but, being a folder, it has multiple files in it. Which one should I be searching for "the block that contains..."?

I've got a feeling I already did something wrong in step 2.8-[

Edit: OK, I see the block in evdev.c... but am I really supposed to be doing this in a .gz arhive?

---

### Post by aharown07 on 2010-03-08
For what it's worth, found a workaround... at least in the case of the Dell 1558.
Using the keyboard shortcuts tool, I assigned Mod4+up to volume up and Mod4+down to volume down. Works fine. Not quite as nice as using the one-touch multimedia keys though... so I'd still love to figure out how to use the fix posted above.
Wd need help with that though.

---

### Post by osterchrisi on 2010-03-15
Hi!

I did the whole procedure, but it didn't show any effect... So one question: Do I have to insert the few new lines into the evdev.c before the few lines that are posted here or before the _whole block_ where these lines appear?

Thanks  for that!

//edit
Ah, or am I too stupid to realize that the "Recovery" section where you restore your old driver is just for when it's not working at all? And now that I've recovered my old driver of course there's no change?
//edit2
Ok, it works now - WITHOUT restoring the old drivers... :P

---

### Post by zhaoyuncom on 2010-04-07
:P:KSI have try 2rd method on my laptop,in order to compile the evdev_drv.so ,you must apt-get install build-essential libtool automake gcc xorg-dev xutils-dev,and download the latest xserver-xorg-input-evdev.
[COLOR=Red]apt-get source xserver-xorg-input-evdev

sudo apt-get build-dep xserver-xorg-input-evdev[/COLOR]

I found when I press the volum [fn+key],the new compiled evdev_drv.so can avoid the Dead cycle&#65292;But it works responds too slowly.I don't know why

---

### Post by orcjuggernaut on 2010-05-01
u r the best!!! thanks

---

### Post by macrules on 2010-05-04
Well, a subject being posted after 3 years, that really indicates this is a problem!
The solution does not work for me.
First of all, I have no autobuild script, so used ./configure .
then make && make install.

I have trouble with my sound and cam keys and adjusted the source of evdev.c accordingly.
The only thing changing is that it does not hang on the first combo for cam, but the second time I use it.
Then switching ctrl+alt+f2 and back to ctrl+alt+f7 , i have no more trouble with it.

Does anyone have a FINAL solution for this annoyance?
Who had already filed bug reports?
I am cosidering posting a new one, but do not want to pollute launchpad.

to the devs: how do we fix this?
If any help is needed i am willing to.

I have a Mivvy G310 netbook (Viooo Corporation PT17 or something) and I have hanging media keys for sound up, down and mute and webcam.
Other keys seem to work.

---

### Post by Tshann on 2010-08-18
Here it is August 2010, and I had to use this work-around. I used Dr. Vista's workaround, and it appears to have worked. Though I did have to reboot to enable the fix. Hopefully this will continue to work, until someone figures out how to get the multimedia keys to unstick. Who knows, maybe in the next few years?

Peace

---

### Post by heyho on 2010-10-20
Once again this issue is putting me off of a fresh LTS install, as using a Live USB has confirmed that it is still a problem on my Fujitsu Siemens Amilo.

Is there any reason that this fix (original fix, post #1)would not work on Lucid?

---

### Post by codyduncan on 2011-02-27
It looks like this server is either down or no longer any use?  Trying method 1 leads to a dead end.

I am having problems with an HP zv6000, with the typical "hit it once, and it acts as though I am holding it" problem.  [Actually, at the moment, the volume buttons seem to be doing nothing at all, other than the mute button.]

---

### Post by solarisdreams on 2011-04-13
> **drvista said:**
> [COLOR="Red"][CENTER]**[SIZE="4"]This is  a rewrite of the fix [/SIZE]**[/CENTER][/COLOR]


I'd like to say, "I love you drvista."  You made my day - excellent work.

Can I ask how you figured this out?

---

### Post by drvista on 2011-04-15
some guy told me so on irc

---

### Post by allaf on 2011-04-24
I can't believe this bug RE-happened to me just today after the weekly updates.

---

### Post by codyduncan on 2011-09-04
Still fighting this fight.  I'm using 11.04, and get the same old bugs.  I hit hangups on each fix.  This time I'm getting this on sudo make install:

> Making install in src
make[1]: Entering directory `/home/cody/xserver-xorg-input-evdev-2.6.0/src'
  CC     evdev.lo
libtool: Version mismatch error.  This is libtool 2.2.10, but the
libtool: definition of this LT_INIT comes from libtool 2.2.6b.
libtool: You should recreate aclocal.m4 with macros from libtool 2.2.10
libtool: and run autoconf again.
make[1]: *** [evdev.lo] Error 63
make[1]: Leaving directory `/home/cody/xserver-xorg-input-evdev-2.6.0/src'
make: *** [install-recursive] Error 1


Where to go from here?

---

### Post by drvista on 2011-11-09
I have created deb package for oneiric /percise
ppa:dr3mro/xserver-xorg-input-evdev

---

### Post by drvista on 2011-11-19
the fixed evdev is for oneiric at
ppa:dr3mro/xserver-xorg-input-evdev

---

