---
title: "Samsung QX410 issues (touchpad, nvidia, brightness/volume)"
date: 2010-11-22
forum: Hardware
---

### Post by devTristan on 2010-11-22
I've just put ubuntu on my new qx410. There are a few issues I've encountered, which I've found to happen to everyone with ubuntu on a qx410.

The main issue, at least for me, is the touchpad. It's recognized as a "PS/2 Logitech Wheel Mouse". There is no touchpad tab under system>preferences>mouse, and so I can't configure side scrolling, disabling it while I type, or anything useful like that. I think this is because there's no driver for it yet...? Very very annoying.

Second issue is the graphics. Jockey offers me the nvidia driver, which installs just fine but prevents the computer from booting properly (I just end up with tty1, where I disable the driver and reboot). This issue doesn't bother me at all, but it's still an issue.

Third, most minor issue is that of the volume and brightness keys. If you do fn-up or fn-down it'll change the brightness, fn-left and fn-right for volume. It works, I guess, but it fails to recognize when you stop pressing the key, and glitches out your keyboard, pretty much preventing you from doing anything until you reboot. I just solved this by setting some volume and brightness hotkeys and avoiding that particular key combo. No problem.

I understand that the QX line has only been available for a month or so, so it'll probably take a while for support to be out there. However, if anybody's got any sort of solution, particularly for the touchpad issue, I'm open.

---

### Post by zerosixx on 2010-11-24
Hey devT,


So, what does the solution exactly do? does it disable the video card and then restart the computer? or does it disable the drivers and then restart? Should people not update the drivers to begin with in linux? It keeps prompting to update- whats your advicve? should people just hassle with this command when it drops us down to (tty?)

Also, would you like me to repost your solution for others to see?

Any other issues with the Samsung QX410 laptop that you know of or have solved?

Thanks so much in advance,


zero

---

### Post by devTristan on 2010-11-24
My solution just disables the driver and reboots. I read somewhere that the graphics card switching isn't yet supported on ubuntu, so I didn't push it much. I did find a script somewhere that was able to power off the dedicated graphics card, but that's it. It actually increased the battery life a lot.

The update renders the system unable to boot into a graphical interface, so there's no point in installing it.

If you find yourself unable to boot into a graphical interface because you installed the nvidia driver, here's what you can do:

```
sudo jockey-text -d xorg:nvidia_current
sudo shutdown -r now
```
That'll disable the driver and reboot.

I'm afraid I haven't found any kind of solution yet. I'll keep looking.

---

### Post by zerosixx on 2010-11-25
Yeah, that should work for now...

This is the time where I wish I knew coding and knew how to write drivers, as in this is something I'd spend quite some time figuring out. I'm wondering why nVidia wont support this? I found online that they've said they wont support Optimus technology in linux? I'll keep digging for other solutions..

I'll keep this thread alive for other people as well. I love that laptop, but I'm sad that it can't trigger the 3d capabilities in Linux, since I installed it to learn and fully test.

---

### Post by 2min4roughing on 2010-12-21
I just purchased the QX410 last week, even after reading this thread. Liked the machine and the feel of the keyboard (IOW, I'm like shiny new things). I agree, the touchpad is very annoying. The issue has been reported on lauchpad at [https://bugs.launchpad.net/ubuntu/+bug/681904](https://bugs.launchpad.net/ubuntu/+bug/681904). 

In the meantime, I've decided to bind xinput commands to key combinations to turn on/off the touchpad manually. Not a perfect solution, but in the meantime I can type without issue while waiting for a fix to get the Elantech touchpad recongized. I'm running Linux Mint 10 and using CompizConfig Settings Manager to bind a key combinations to shell scripts. Here's what I did (for other Linux n00bs like me):

1. Create a shell script that will turn on the mouse using xinput (e.g. ~/scripts/mouseon)
```
xinput set-int-prop "PS/2 Logitech Wheel Mouse" "Device Enabled" 8 1
```

2. Create a shell script that will turn off the mouse using xinput (e.g. ~/scripts/mouseoff)
```
xinput set-int-prop "PS/2 Logitech Wheel Mouse" "Device Enabled" 8 0
```

3. Make sure both scripts are executable
```

chmod u+x ~/scripts/mouseon
chmod u+X ~/scripts/mouseoff

```

4. Open up CompizConfig (System > Control Center > CompizConfig Settings Manager)

5. Click the "Commands" option under "General"

6. In the "Commands" tab, type the absolute path to mouseon in one free command line

7. Type the absolute path to mouseoff in another free command line

8. Click the "Key Bindings" tab and enable the command lines you chose in the previous steps and assign key combinations for them (I'm using Shift+Control+UpArrow to turn mouse on and Shift+Control+DownArrow to turn mouse off).

HTH

Reference
[https://wiki.ubuntu.com/X/Config/Input](https://wiki.ubuntu.com/X/Config/Input)

---

### Post by Roadmaster on 2010-12-21
Ubuntu already has the infrastructure in place to handle most of the QX410's keys. 

The udev subsystem handles mapping actual keypresses to keycodes which can then be interpreted by the operating system and programs to perform actual functions. A set of rules tell udev which keycode to generate for every key. The rules for Samsung computers are already there, and can handle most of the quirks of the QX410, but they don't get loaded because, since the model is so new, it's not in the list of  Samsung computers that Ubuntu has. It can be added manually and things work much better that way.

How to do it:

1- Open /lib/udev/rules.d/95-keyboard-force-release.rules with your favorite text editor.
2- Go to line 22, which begins:
```
ENV{DMI_VENDOR}=="[sS][aA][mM][sS][uU][nN][gG]*"

```3- The line contains a list of Samsung models. Near the end of the line, after *X460*, add the QX410, so the list ends like this:
```
|*X460*|*QX410*"

```DO NOT delete the stuff that's still at the end of the line (,RUN+=... and so on)
4- Reboot

After doing this:
1- The volume and brightness up/down keys now work correctly, they don't stick all the way up or down.
2- The Fn-F2 (display battery status) and Fn-F10 (disable touchpad) keys now work correctly. The Fn-F10 is particularly useful because it allows us to disable the touchpad manually when typing.
3- The Fn-F5 (disable backlight), F7 (help center), F8 (silent mode) and F9 (disable wireless) keys are available in the keyboard shortcuts dialog, and can thus be assigned commands to mimic their functions under Windows.

There's still the question of the touchpad, which will have to wait until support for the Elan trackpad is added to the kernel's mouse driver.

---

### Post by 2min4roughing on 2010-12-22
Thanks for the tip Roadmaster. Works like a charm.

---

### Post by Shisoik on 2010-12-27
This also worked for Samsung SF310. Apparently it should work for the whole product line: Samsung QX310/QX410/QX510/SF310/SF410/SF510. Thanks Roadmaster! :D

---

### Post by Quadunit404 on 2010-12-28
What about the Samsung NP-RF510? Should that work with that too? I own one and, with the exception of the NVIDIA driver issue, I'm experiencing the same symptoms as the OP.

I bookmarked both the touchpad and keyboard solutions to try them out. I think I'll reboot into Ubuntu right now since I don't feel like playing games on my PC right now...

EDIT: Yes, it does work! Just put RF510 in /lib/udev/rules.d/95-keyboard-force-release.rules as suggested and it'll work! Brightness won't change, though...

---

### Post by nascirek on 2010-12-30
There is another way to quickly disable/enable the touchpad (tested on QX510):

For disable the touchpad type in terminal:

```
xinput --set-prop "PS/2 Logitech Wheel Mouse" "Device Enabled" 1
```For enable the touchpad type in terminal:

```
xinput --set-prop "PS/2 Logitech Wheel Mouse" "Device Enabled" 0
```I set shortcuts this way for turn on / turn off but now the Roadmaster's way is easier.

However adding the command line *xinput --set-prop "PS/2 Logitech Wheel Mouse" "Device Enabled" 0* as a new Startup Program is great solution when you use commonly a mouse instead of touchpad. You can always turn on the touchpad by Ctrl+F10 after apply the Roadmaster's fix.

---

### Post by armanatz on 2011-02-03
Don't know if anyone still visits this thread but just in case someone stumbles in here through Google, I have solved most of the issues found on recent Samsung laptops.

Check out my thread (I am not promoting, just want to provide a solution):
[http://ubuntuforums.org/showthread.php?t=1680872](http://ubuntuforums.org/showthread.php?t=1680872)

If the solutions posted by me actually work then do post on the thread so others can see. It is very critical that people solve these issues as Samsung makes some great laptops

---

### Post by barricane on 2011-03-25
Thanks for the very very useful tip RoadMaster. 

Your function key solution works perfectly for volume, brightness and backlight keys on my Samsung RV511 (just add *rv511* instead of *qx410*)
I reached this thread via armanatz's post (thanks). Having already loaded samsung-tools and samsung-backlight, I found RoadMaster's solution got the above function keys working.

---

### Post by tuho3 on 2011-03-26
Anyone else having problems with VGA output port? 
[http://ubuntuforums.org/showthread.php?t=1714484](http://ubuntuforums.org/showthread.php?t=1714484)

---

### Post by jolus on 2011-05-04
> **tuho3 said:**
> Anyone else having problems with VGA output port? 
[http://ubuntuforums.org/showthread.php?t=1714484](http://ubuntuforums.org/showthread.php?t=1714484)

BUMP, I also want to know more about this

---

### Post by edjski on 2011-05-18
> **devTristan said:**
> I've just put ubuntu on my new qx410. There are a few issues I've encountered, which I've found to happen to everyone with ubuntu on a qx410.

The main issue, at least for me, is the touchpad. It's recognized as a "PS/2 Logitech Wheel Mouse". There is no touchpad tab under system>preferences>mouse, and so I can't configure side scrolling, disabling it while I type, or anything useful like that. I think this is because there's no driver for it yet...? Very very annoying.



I understand that the QX line has only been available for a month or so, so it'll probably take a while for support to be out there. However, if anybody's got any sort of solution, particularly for the touchpad issue, I'm open.

5/18/2011 
Does anyone know if there are any updates on getting the elan smartpad recognized as something other than a logitech mouse?

---

### Post by mkquist on 2011-06-09
devTristan,
I see that you said you found script that disables the Nvidia card and extends battery life.  Not sure if anyone reads this, but if you do would you be willing to share the script?

---

### Post by Roadmaster on 2011-06-16
FYI, Ubuntu 11.04 recognizes the QX410 (and presumably others of the same family) so the patch to udev rules is no longer necessary.

Also, to get the touchpad to be recognized as such, see this bug:

[https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/681904]("https://code.launchpad.net/%7Ecr3/ubuntu/lucid/checkbox/0.9.2")

comment #64 ([https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/681904/comments/64](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/681904/comments/64)) has instructions on installing a patched psmouse/elantech driver via dkms. Do so at your own risk, this code is not bulletproof, nor has it been integrated into the mainline Linux kernel. I do have it on my QX410 and it works like a charm.

---

### Post by hazielquake on 2011-09-14
> **Roadmaster said:**
> FYI, Ubuntu 11.04 recognizes the QX410 (and presumably others of the same family) so the patch to udev rules is no longer necessary.

Also, to get the touchpad to be recognized as such, see this bug:

[https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/681904]("https://code.launchpad.net/%7Ecr3/ubuntu/lucid/checkbox/0.9.2")

comment #64 ([https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/681904/comments/64](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/681904/comments/64)) has instructions on installing a patched psmouse/elantech driver via dkms. Do so at your own risk, this code is not bulletproof, nor has it been integrated into the mainline Linux kernel. I do have it on my QX410 and it works like a charm.

By any chance, did you any of you who applied this patch lost the right click feature? I installed it, and the scrolling works perfect, but I can't right click with the mouse pad now... only the key between Alt and Ctrl!
Oh! How do you uninstall it by the way? thanks.

---

### Post by seanmonstar on 2011-09-14
> **hazielquake said:**
> By any chance, did you any of you who applied this patch lost the right click feature? I installed it, and the scrolling works perfect, but I can't right click with the mouse pad now... only the key between Alt and Ctrl!
Oh! How do you uninstall it by the way? thanks.

Yea, I lost right click as well. However, you can right click by tapping with 2 fingers, and middle click by tapping with 3.

---

### Post by bakis2011 on 2011-10-15
Hey i checked out that bug and the comment and followed the instructions but it didn't work... can anyone help? i've got a samsung qx410 on ubuntu 11.04... still can't get my touchpad recognized.

---

