---
title: "Problem with xset dpms force off"
date: 2009-11-07
forum: Hardware
---

### Post by El Raspa on 2009-11-07
Hello everyone

I have intel chipset and ubuntu 9.10 (fresh install)

when I run 'xset dpms force off' the backlight turns off but after a few seconds (30 to 120) it turns on again and is driving me crazy

I have disabled the screensaver but it keeps doing it

When I had 9.04 this problem doesn't happened

Can anyone help me please?

Regards!

---

### Post by El Raspa on 2009-11-07
bumb

---

### Post by ciphercast on 2009-11-08
so much for trying to sleep.  I am on arch linux, and am experiencing the same problem after doing an upgrade.

only happened with the last release of something within the last few days, will know more tomorrow.

---

### Post by rzrgenesys187 on 2009-11-09
Same here on gentoo

---

### Post by dpward on 2009-11-10
I'm seeing the same problem on Ubuntu 9.10.  This didn't happen with Ubuntu 9.04.

I have a Dell Latitude E6500 with nvidia Quadro NVS 160m graphics (using the nvidia driver version 185.18.36, from the Hardware Drivers wizard).

---

### Post by raltar1 on 2009-11-10
I confirm the problem, this time with 9.10 on an HP HDX16 laptop with Nvidia 9600M graphics card.

---

### Post by ekorn on 2009-11-14
Same for me on a Thinkpad [X41]("http://www.thinkwiki.org/wiki/Category:X41") with a [Intel Graphics Media Accelerator 900.]("http://www.thinkwiki.org/wiki/Intel_Graphics_Media_Accelerator_900")
I have the feeling that it works when the Screensaver triggers it.

---

### Post by DGMcCloud on 2009-11-17
Same problem on a Dell D820. Has this bug been reported?

---

### Post by lokkiikkol on 2009-11-21
hey there,

i have (had) the exact same problem on 9.10

are you all on wireless connections? i realized that every time, the wireless strength meter in the network-manager changed, the display went back on... so what i did was disabling the wireless before i turned the screen black. it works now. not really a fix, but rather a workaround.

hope this helps!

---

### Post by lokkiikkol on 2009-11-21
ok, strange

it seems kind of random now. i turned wireless back on, and it still works!

so, i have no clue.

---

### Post by DGMcCloud on 2009-11-22
This bug has been reported here: [https://bugs.launchpad.net/ubuntu/+source/gnome-power-manager/+bug/447728](https://bugs.launchpad.net/ubuntu/+source/gnome-power-manager/+bug/447728)

See my post in that bug-report for more info on this issue.

---

### Post by alexcabal on 2009-12-18
I have this problem too, and it doesn't look like there's an easy solution.  I have, however, whipped up a quick script to maybe solve this problem for some of you.  It's not an ideal solution (you run the script once to turn the screen off, then again to turn it back on), but it'll have to do until the bug gets fixed.  Here's a link:
[http://alexcabal.com/turn-your-laptop-screen-off-with-a-keyboard-shortcut-in-ubuntu-karmic/](http://alexcabal.com/turn-your-laptop-screen-off-with-a-keyboard-shortcut-in-ubuntu-karmic/)

---

### Post by mondalaci on 2010-01-12
Here's my workaround: [http://monda.hu/blog/2010/01/12/lock-your-laptop-and-turn-off-display-with-the-touch-of-a-keystroke-in-ubuntu-karmic/](http://monda.hu/blog/2010/01/12/lock-your-laptop-and-turn-off-display-with-the-touch-of-a-keystroke-in-ubuntu-karmic/)

---

### Post by Andaril on 2010-01-18
It work if I have volume 0% for pulse audio!


------
Sorry false alarm I turn pulse volume on and it steel working... but it does not before...

---

### Post by jurusu on 2010-02-20
Works perfectly fine! Thanks!!!

---

### Post by vamapaull on 2010-05-17
I have this same problem with Ubuntu Netbook Edition 10.04 on a Toshiba NB100

---

### Post by muadnu on 2010-05-24
> **mondalaci said:**
> Here's my workaround: [http://monda.hu/blog/2010/01/12/lock-your-laptop-and-turn-off-display-with-the-touch-of-a-keystroke-in-ubuntu-karmic/](http://monda.hu/blog/2010/01/12/lock-your-laptop-and-turn-off-display-with-the-touch-of-a-keystroke-in-ubuntu-karmic/)

This doesn't work for me... Somehow the backlight stays off for longer than if I just did xset dpms force off, but it still eventually does after 30 or so seconds...

---

### Post by muadnu on 2010-05-24
I think I know what the problem is: gnome-screensaver. If I run
```
sleep 3 && xset -display :0.0 dpms force off && gnome-screensaver-command -i
```
on a terminal (the last bit inhibits the screensaver) then the backlight stays off (at least for a couple of minutes, which is what I've tried). This has the problem that now gnome-screensaver is inhibited even if I turn the screen back on (since it will stay inhibited until I cancel the command, e.g. by closing the terminal or hitting ctrl+c). But maybe someone has a good idea of how to go from here.

---

### Post by dino99 on 2010-05-24
might help to install the latest driver:

[https://launchpad.net/~xorg-edgers/+archive/ppa](https://launchpad.net/~xorg-edgers/+archive/ppa)

---

### Post by nxmehta on 2010-05-25
> **muadnu said:**
> I think I know what the problem is: gnome-screensaver. If I run
```
sleep 3 && xset -display :0.0 dpms force off && gnome-screensaver-command -i
```
on a terminal (the last bit inhibits the screensaver) then the backlight stays off (at least for a couple of minutes, which is what I've tried). This has the problem that now gnome-screensaver is inhibited even if I turn the screen back on (since it will stay inhibited until I cancel the command, e.g. by closing the terminal or hitting ctrl+c). But maybe someone has a good idea of how to go from here.

Bingo: it's gnome-screensaver. Here's one way to fix this:

```
sudo apt-get remove gnome-screensaver
```

Honestly who needs a stupid "screen saver" anyways, I'm not using a plasma display over here on my laptop, nothing is getting burned in.  I just want something to turn off my display, which gnome-power-manager does already.  Hopefully this is a better solution than the utterly insane option of running 'xset dpms force off' in an infinite loop.

Seriously though, people are piddling about with this bug on three different bugtrackers over the course of months and this is the first time someone's pointed out what the actual problem is.  Sheesh.

---

### Post by inameiname on 2010-05-25
Alex Cabal's workaround is what I've used since the problem first occurred with me in Karmic:

[http://alexcabal.com/turn-your-laptop-screen-off-with-a-keyboard-shortcut-in-ubuntu-karmic/](http://alexcabal.com/turn-your-laptop-screen-off-with-a-keyboard-shortcut-in-ubuntu-karmic/)

László Monda's Blog's post also sounds intriguing. I'll definitely check his out as I hadn't run across it in my many nights of Googling a solution to this very problem. :P

---

### Post by muadnu on 2010-05-25
I thought about removing gnome-screensaver but didn't go with since I've had issues in the past doing that (maybe related with gnome-power-manager turning the screen off), but I guess there's no harm in trying.

EDIT: Ok, I tried it and now I figured out what the issue is: the screen cannot be locked without gnome-screensaver. Since I need to be able to lock it, my workaround is to simply add "gnome-screensaver-command -i" to the startup applications. As nxmehta points out, I don't really need it working...

EDIT 2: This doesn't work either :(. By inhibiting gnome-screensaver the locking facility is also disabled.

---

### Post by inameiname on 2010-05-26
Okay so trying Monda's script, what it does for me is that it pops up my screensaver for a half a second, before proceeding to a black screen. However, after a few minutes (no more than 3 or so) the screensaver suddenly pops up. And if I then push something, I notice my screen is locked and I must log in. Oh, and fyi, my screensaver is set to turn on in 5 minutes, and to not display a log in box, meaning it's not locked, if that makes any difference. 

However, trying Muadnu's way of writing out Monda's script, it is delayed a few seconds, and then goes black and seems to stay that way:

[B]#!/bin/bash
sleep 3 && xset -display :0.0 dpms force off && gnome-screensaver-command -i[/B]

It seems to work, minus the locked screen and log in requirement when a button is touched. Thus, I'm guessing the placement of that 'gnome-screensaver-command -i' changes things from Monda's original script.

So it seems if I just use that as my script, bind it to say a launcher on my desktop or panel, or even to a hardware button, the screen will forever stay off until I push something for it to resume. Anybody else get that? However, due to that 'gnome-screensaver-command -i' part, my screensaver won't work again. Am I right, or does 'inhibited' mean something else? And also, if I want a locked screen desire, I'm also out of luck too? Not to say I need the latter really.

As I mentioned earlier, Alex Cabal's workaround is what I've used for months, but if this one as it stands now does what his does but more efficiently, I'm ready to try it.

---

### Post by nxmehta on 2010-06-09
Well, for some reason removing gnome-screensaver didn't seem to work for me after thorough testing.  The whole 'gnome-screensaver-command -i' thing DID seem to work, which is weird.

I got sufficiently pissed off about this problem today that I wrote a python script that is much more elegant than the whole run 'xset dpms force off' in an infinite loop thing, then somehow try to break the loop.  For this script to work you need python and the python-xlib package installed.  Paste the following into a file, chmod +x it, and then run it to finally turn off the screen once and for all.

```
#!/usr/bin/python

import time
import subprocess
from Xlib import X
from Xlib.display import Display

display = Display(':0')
root = display.screen().root
root.grab_pointer(True, 
        X.ButtonPressMask | X.ButtonReleaseMask | X.PointerMotionMask, 
        X.GrabModeAsync, X.GrabModeAsync, 0, 0, X.CurrentTime)
root.grab_keyboard(True, 
        X.GrabModeAsync, X.GrabModeAsync, X.CurrentTime)

subprocess.call('xset dpms force off'.split())
p = subprocess.Popen('gnome-screensaver-command -i'.split())
time.sleep(1)

while True:
    print display.next_event()
    p.terminate()
    break
```

This is just my first shot at this, so it might not work perfectly.  Basically what it does is it calls 'xset dpms force off', forks a process to inhibit gnome-screensaver, waits one second, then sits waiting for any user input to the X server.  If the user moves the mouse, hits a mouse button, or presses a key, the script terminates the gnome-screensaver inhibit command and exits.

Hopefully this will work.  I'll post back if I ever notice the backlight turning back on.  Then we'll have to go back to the drawing board...

If you wanted this to lock the screensaver as well you could probably put in a "subprocess.Popen('gnome-screensaver-command -l'.split())" call after the "p.termintate()" call (but I suspect the timing might be a little off).

---

### Post by muadnu on 2010-06-09
Thanks! It works great for me, at least for a minute (haven't tried it longer).

---

### Post by inameiname on 2010-06-09
Very cool, [nxmehta]("http://ubuntuforums.org/member.php?u=641055"). I will have to try it and get back to you on it.

UPDATE:

Works just fine for me! Wow, after 8.5 months since Karmic was released and this problem started (at least from what I've gotten online), a real solution seems to have been found! Thanks. Credit to all those that contributed to the final product, of course.

Oh, and while it's not a huge issue for me, the 'lock screen' command that you suggested to add seems to also work, despite the timing, as you said might be an issue. Basically, when I hit a button, or move the cursor, it pops up my screen for a second, only to suddenly go to a black screen, sometimes my screensaver, and then if I hit a button again and/or continue to move the cursor for a sec, it goes to the login box.

---

### Post by caprilo on 2010-06-18
Have you tried

```
sleep 1 && gnome-screensaver-command -a && xset dpms force off
```

?

---

### Post by inameiname on 2010-06-22
Unfortunately Caprilo, what:

sleep 1 && gnome-screensaver-command -a && xset dpms force off

does for me is that it turns off the display for a second or two, and then either goes to screensaver, or keeps the screen backlight on.

Regardless, the fix previously that I mentioned working continues to work flawlessly.

---

### Post by SirPecanGum on 2010-07-05
Sorry, commented to soon...

---

### Post by adamlogan on 2010-07-06
Thank you very much for your script nxmehta. I am only recently using Ubuntu as my full time OS at home. Fortunately I had started getting into CLI on my personal mac which is currently being used at work but I am still very green to the *NIX like OS's.

I'm executing this script via an alias. How can I make the script run silently with nothing appearing on std output? The output to std out is somewhat undesirable. I tried using 

alias sd='nohup path/to/script &' 

and once more without the nohup. Didn't get the effect I wanted. In the script itself I see the text "print display.next_event()" Is that writing to std out?

Other than that I'm very pleased with the script.

---

### Post by lunatico on 2010-07-26
> **nxmehta said:**
> 
Hopefully this will work.  I'll post back if I ever notice the backlight turning back on.  Then we'll have to go back to the drawing board...


Nice script! Unfortunately it's still not working for me... it does stay off for longer I have to say... but if I run your script from the terminal, after a few seconds the screen comes one again and the script is still there waiting from input.

Any idea how I can troubleshoot this to try to determine what's turning my screen on?

Thanks!

---

### Post by lunatico on 2010-07-26
> **lunatico said:**
> 
Any idea how I can troubleshoot this to try to determine what's turning my screen on?


Sorry! My bad!
I use blueproximity and it had a proximity command set to 'gnome-screensaver-command -p' to run every 60 seconds. Removed that command and now my screen stays off forever! Yei!

The weird thing is that a simple command like:
```
#!/bin/bash
sleep 2
xset dpms force off
```
does the trick...

---

### Post by lunatico on 2010-07-26
> **lunatico said:**
> 
The weird thing is that a simple command like:
```
#!/bin/bash
sleep 2
xset dpms force off
```
does the trick...

Nope... me getting ahead of myself again. I had to use your script, which is perfect! Thanks!

---

### Post by digbysellers on 2010-07-29
Thanks for the script!
I use this running from irexec with lirc so I can turn the monitor off by remote. 
 
I was wondering perhaps if there was a way to edit the script so that it running it would effectively toggle the display on and off? 
Or any way I could turn the display back on by way of remote?

---

### Post by axyelp on 2010-09-01
> **adamlogan said:**
> Thank you very much for your script nxmehta. I am only recently using Ubuntu as my full time OS at home. Fortunately I had started getting into CLI on my personal mac which is currently being used at work but I am still very green to the *NIX like OS's.

I'm executing this script via an alias. How can I make the script run silently with nothing appearing on std output? The output to std out is somewhat undesirable. I tried using 

alias sd='nohup path/to/script &' 

and once more without the nohup. Didn't get the effect I wanted. In the script itself I see the text "print display.next_event()" Is that writing to std out?

Other than that I'm very pleased with the script.

i've done
alias so="script>/dev/null"
/dev/null discards all data that you redirect to it!
just learnt it! :D


p.s the script is just perfect! i've stopped the screen saver services, but i guess its the power managers' preference to dim the backlight when not in use which is causing the screen to lit back!

---

### Post by glorfindel_i510 on 2010-12-14
I think I've found a simple workaround for this problem.

Create a script which first calls sleep and then xset.

The key here is the amount of secs to sleep. If this doesn't work in your case, simply try increasing the amount of secs to sleep.

You can see how to achieve this here: [http://usemoslinux.blogspot.com/2010/12/como-apagar-el-monitor-desde-un.html](http://usemoslinux.blogspot.com/2010/12/como-apagar-el-monitor-desde-un.html)

Greetings from Argentina! Pablo.

---

### Post by inameiname on 2010-12-15
As shown in previous posts, this script, by **nxmehta, **solves this problem for most of us. Lunatico is the only person I've found who is still having issues. Not sure what to offer as advice for him, though:

> 

#!/usr/bin/python

import time
import subprocess
from Xlib import X
from Xlib.display import Display

display = Display(':0')
root = display.screen().root
root.grab_pointer(True, 
        X.ButtonPressMask | X.ButtonReleaseMask | X.PointerMotionMask, 
        X.GrabModeAsync, X.GrabModeAsync, 0, 0, X.CurrentTime)
root.grab_keyboard(True, 
        X.GrabModeAsync, X.GrabModeAsync, X.CurrentTime)

subprocess.call('xset dpms force off'.split())
p = subprocess.Popen('gnome-screensaver-command -i'.split())
time.sleep(1)

while True:
    print display.next_event()
    p.terminate()
    break


---

### Post by dstein on 2011-02-28
Using nxmehta's script, my monitor turns off, but the computer no longer goes into sleep mode after 2 hours, which I have it set to do. Has anyone had any success with powering off the monitor with a program, and also having the computer being able to go into sleep mode after whatever the configured time is has elapsed.

---

### Post by sehyoun on 2011-03-03
> **dstein said:**
> Using nxmehta's script, my monitor turns off, but the computer no longer goes into sleep mode after 2 hours, which I have it set to do. Has anyone had any success with powering off the monitor with a program, and also having the computer being able to go into sleep mode after whatever the configured time is has elapsed.

 I believe you can run
```
xdg-screensaver activate && xset dpms force off
```In this case, you are turning the screen saver on and then forcing the backlight off. You might have to type in your password when you return to your computer depending on your screen saver setting. If you want to lock your computer(independent of your screen saver setting), then just replace "activate" with "lock."

---

### Post by dstein on 2011-03-03
> **sehyoun said:**
> I believe you can run
```
xdg-screensaver activate && xset dpms force off
```In this case, you are turning the screen saver on and then forcing the backlight off. You might have to type in your password when you return to your computer depending on your screen saver setting. If you want to lock your computer(independent of your screen saver setting), then just replace "activate" with "lock."

This will have the problem that the monitor turns on after a few seconds, as described in El Raspa's original post.

---

### Post by sehyoun on 2011-03-03
> **dstein said:**
> This will have the problem that the monitor turns on after a few seconds, as described in El Raspa's original post.

Oh, I see... It actually just lengthened the time before the monitor turning back on (2sec -> 1 min). Sorry about that. I guess I should have waited longer than 30 secs to be sure.

---

### Post by sehyoun on 2011-03-04
Ok. Apparently how you call on the screensaver might matter. Could you test

```
gnome-screensaver-command -a && xset dpms force off
```I tested it twice up to 5 minutes and once up to 20 minutes this time. I hope it didn't just lengthen the wait time again since 20 mins is about at the edge of my patience =P

---

### Post by McCleod on 2011-03-07
> **lunatico said:**
> 

The weird thing is that a simple command like:
```
#!/bin/bash
sleep 2
xset dpms force off
```
does the trick...

I am trying to make a gnome-screensaver module based on that script. I just needs some good documentation on how to make .desktop modules. Anyone?

Using Google get's me nowhere :-(

---

### Post by Rebelli0us on 2011-03-13
Same problem here. Something is defeating the screen auto-shut off... like sending mouse or keyboard events to the system. This is a worldwide energy disaster with millions of screens lit up when they should be off! How may megawatts of wasted energy is that?!

Never mind scripts and workarounds... this thread is old, so why haven't the devs fixed this????

---

### Post by kwevej on 2011-05-05
My solution lcdonoff script - simple and elegant :popcorn:
```
#/bin/sh
OID='LVDS1'
STATE=`xrandr | grep $OID | grep -c "ted ("`
case $STATE in
'1')
xrandr --output $OID --auto
;;
'0')
xrandr --output $OID --off
;;
esac
```

replace OID by your device

posted also at
[http://paste2.org/p/1400104](http://paste2.org/p/1400104)

...and the best is - you can still control your music player, while your LCD is turned off

---

### Post by inameiname on 2011-05-05
That works, but only if you have that script set on a button, not an icon. Though, I have only tested it on a laptop, so I do not know if it works on a desktop. I'm sure it can be adapted, though. Of course, you can usually turn those monitors off.

Nxmehta's script still is my choice, and hasn't failed me for several Ubuntu versions, including Natty.

---

### Post by GSF1200S on 2011-06-12
A little bit of a thread revival (1 month ~), but I wanted to thank nxmehta for his script and also pass a little info on for those who might want screenlock at the same time. 

I KNOW there is a more elegant way, so when one of you guys read this and think of that better way, be sure to post and make me feel stupid ;)

I created one script (simply called 'lock') that contained:
```
#!/bin/bash
xflock4 &
sleep 3
python /home/user/scripts/screenlock
```
and then pasted nxmehta's python script into another script at that location. I then bound a key combination to execute 'lock', which enables screen lock and follows by executing nxmehta's script to turn off (and keep off!) the monitor. 

I did it this way in hopes I can use his script to figure out how to get the screensaver itself to shut off the monitor ( ](*,) )

Thanks again..

---

### Post by nxmehta on 2011-07-04
Wow, it's been almost exactly 1 year since I posted that python script... and the bug still isn't fixed in Ubuntu.  Glad that some people are getting use out of it though I guess.

I'll check in around June 2012... here's hoping that people don't have to keep using a python script to turn their screen off!

---

### Post by inameiname on 2011-07-04
> **nxmehta said:**
> Wow, it's been almost exactly 1 year since I posted that python script... and the bug still isn't fixed in Ubuntu.  Glad that some people are getting use out of it though I guess.

I'll check in around June 2012... here's hoping that people don't have to keep using a python script to turn their screen off!


Haha, I hope so too. Regardless, I'm sure I speak for all of us on here: thanks for the script. :)

---

### Post by snoxu on 2011-07-05
Running Gnome 3 on Arch with the same issue but I can't get the script to work, I get this error:

```
File "./monitoroff.sh", line 21
    print display.next_event()
                ^
SyntaxError: invalid syntax
```

I've switched to xfce4-power-manager which doesn't integrate in the Gnome 3 top bar, but I'll make do for the meantime.

It's a shame gnome-power-manager as yet to fix this conflict with xset dpms force off.

---

### Post by adgmonk on 2011-07-30
How about this:

```
 xset s blank ; xset s 1 ; sleep 3 ; xset s 0 
```.

(Ubuntu 10.10 / Intel GMA graphics / i915 driver.)

---

### Post by snoxu on 2011-08-13
> **adgmonk said:**
> How about this:

```
 xset s blank ; xset s 1 ; sleep 3 ; xset s 0 
```.

(Ubuntu 10.10 / Intel GMA graphics / i915 driver.)
This seems to work. What does it actully do?

And how can I put this in Gnome's keyboard shortcut command option?

---

### Post by GSF1200S on 2011-08-14
> **snoxu said:**
> This seems to work. What does it actully do?

And how can I put this in Gnome's keyboard shortcut command option?

Im not familiar with Gnome, but can you point its keyboard shortcuts to your own script? If so, just create a script:
```
#!/bin/sh
xset s blank ; xset s 1 ; sleep 3 ; xset s 0
```
then point Gnome at it in the keyboard shortcuts. Make sure to make the script executable..

---

### Post by adgmonk on 2011-09-05
> **snoxu said:**
> This seems to work. What does it actully do?


It uses the built-in X11 screen saver to blank the screen. This method appears to be immune to the gnome-screensaver bug causing problems with the dpms method for screen blanking discussed in this thread.

Here is a slight improvement to my original command line to blank the screen:

```
xset s blank ; sleep 1 ; xset s activate
```Of course, as shown by GSF1200S, you can put this command line in a shell script and bind it to a key via gnome's window manager.

Or you can do it even without any script file, by binding a key directly to the command:

```
/bin/sh -c 'xset s blank ; sleep 1 ; xset s activate'
```Note:  The key-binding can be done directly (to avoid gnome key binding bugs) using the passive grab mechanism available in Xlib, which will make it independent of gnome or ubuntu.  I can post code if any one is interested.  Full active grab of the entire keyboard and pointer (as done in nxmehta's script) may work, but is not secure, and should be avoided.

---

### Post by inameiname on 2011-09-18
Just to add a bit to this again, I recently ran across another interesting little display off script that I felt like sharing on here. Firstly, I still use **nxmehta**'s script to turn the display off:

```

#!/usr/bin/python

import time
import subprocess
from Xlib import X
from Xlib.display import Display

display = Display(':0')
root = display.screen().root
root.grab_pointer(True,
        X.ButtonPressMask | X.ButtonReleaseMask | X.PointerMotionMask,
        X.GrabModeAsync, X.GrabModeAsync, 0, 0, X.CurrentTime)
root.grab_keyboard(True,
        X.GrabModeAsync, X.GrabModeAsync, X.CurrentTime)

subprocess.call('xset dpms force off'.split())
p = subprocess.Popen('gnome-screensaver-command -i'.split())
time.sleep(1)

while True:
    print display.next_event()
    p.terminate()
    break

```


...it never fails me as a means to turn off the display just once. Once you hit something or press a button it will come back on.

Now, for a little different one, this one will turn the display off, and it will continue to stay off, or rather, will resume to turning the screen back off, it you happen to press a button or touch the touchpad. So far, it seems to work too, and is another good means to turn off the screen, particularly if you give a hardware shortcut to it, such as like this:

```

gconftool-2 --set /apps/metacity/global_keybindings/run_command_5 --type string "<Control><Alt>Z"
gconftool-2 --set /apps/metacity/keybinding_commands/command_5 --type string "/home/me/.gnome2/nautilus-scripts/My_Scripts/Display-Off/Display-Offed.sh"

```

Anyway, here is the script:

```

#!/bin/bash

# Display-Offed.sh
# turns off screen and it will stay off until this script is closed/finished
# works well attached to a hardware button shortcut

LF=/tmp/screen-lock;
if [ -f $LF ]; then
    /bin/rm $LF;
else
    touch $LF;
    sleep .5;
    while [ -f $LF ]; do
        xset dpms force off;
        sleep 2;
    done;
fi

```

---

### Post by ScumCoder on 2011-09-28
Hi guys, I just use
```
xset dpms force suspend
```and it works! :popcorn: It actually does exactly the same (i.e. blanks the screen and turns off the backlight), but it doesn't get dropped. I'm using lucid lynx 10.04.3 x64 on my Acer z5710 monoblock.

UPDATE: that stopped working after some random update :-(  But ```
sleep 1 && xset dpms force off
``` still works fine :-)

---

### Post by 5oak on 2011-12-11
> **adgmonk said:**
> It uses the built-in X11 screen saver to blank the screen. This method appears to be immune to the gnome-screensaver bug causing problems with the dpms method for screen blanking discussed in this thread.

Here is a slight improvement to my original command line to blank the screen:

```
xset s blank ; sleep 1 ; xset s activate
```Of course, as shown by GSF1200S, you can put this command line in a shell script and bind it to a key via gnome's window manager.

Or you can do it even without any script file, by binding a key directly to the command:

```
/bin/sh -c 'xset s blank ; sleep 1 ; xset s activate'
```Note:  The key-binding can be done directly (to avoid gnome key binding bugs) using the passive grab mechanism available in Xlib, which will make it independent of gnome or ubuntu.  I can post code if any one is interested.  Full active grab of the entire keyboard and pointer (as done in nxmehta's script) may work, but is not secure, and should be avoided.

Thnx! I've been looking for a workaround for years (literally)!:D

---

### Post by buddhaflow on 2012-04-12
I wanted to throw my two cents in.

I ran the following in a script:

#!/bin/sh
perl -e 'select(undef,undef,undef,.1)' && xset dpms force off

It fixed the problem right away. No idea what that perl is doing, but it works.

AMD, lucid 32, etc.

Cheers :)

---

### Post by RedgeOnline on 2012-05-09
> **kwevej said:**
> My solution lcdonoff script - simple and elegant :popcorn:
```
#/bin/sh
OID='LVDS1'
STATE=`xrandr | grep $OID | grep -c "ted ("`
case $STATE in
'1')
xrandr --output $OID --auto
;;
'0')
xrandr --output $OID --off
;;
esac
```

replace OID by your device

posted also at
[http://paste2.org/p/1400104](http://paste2.org/p/1400104)

...and the best is - you can still control your music player, while your LCD is turned off

Well this works, but it does mess with my Compiz. On the other hand, compiz has been sensitive as hell since I upgraded tot 12.04 so it might not be caused by the script.

---

### Post by mondalaci on 2012-10-02
Please somebody explain to me how `gnome-screensaver-command -i` is supposed to "inhibit" the screen saver.  "-i" seems to be an invalid argument.

```
$ gnome-screensaver-command -i

** (gnome-screensaver-command:25672): WARNING **: Unknown option -i

```

---

### Post by mondalaci on 2012-10-03
Hey guys,

You're encouraged to take a look at [my workaround]("https://github.com/mondalaci/dpms-force-off-until-activity") and let me know how it works.

Cheers,
Laci

---

### Post by nascapaul on 2012-11-08
Screen blanking at random times

I have a Fujitsu laptop Lifebook and I am using Ubuntu 12.10. Since I upgraded to this version of Ubuntu I experienced random screen blanking each few minutes, like a "blank" screensaver. I solved this issue for myself, but I want to describe it here for others. 

The unsuccesful way I tried to solve this issues:

I disabled dpms and screensaver but something re-enabled it and blanked the screen.
The methods how I tried to disable the dpms and screensaver are:
1) Launched this script:
    xset dpms force on
    xset s noblank
    xset s off
    xset -dpms
2) I put in /etc/rc.local these commands:
setterm -blank 0 -powerdown 0
echo -ne "\033[9;0]" >> /etc/issue
3) Added a new file in /usr/share/X11/xorg.conf.d/99-paul-dpms.conf

Section "Monitor"
    Identifier "monitor"
    Option "DPMS" "false"
EndSection


Section "ServerLayout"
    Identifier "monitor"
    Option "BlankTime" "0"
    Option "StandbyTime" "0"
    Option "SuspendTime" "0"
    Option "OffTime" "0"
EndSection

4) All of the above with minor changes

The problem still persisted.

The successfull workaround:

Today (after many days of random screen blanking) I noticed that it is somehow related with the WiFi Internet connection. Indeed, after I turned off and on the router, the screen blanked imediately after wifi reconnection (usually after few seconds). 
So, decided to monitor the dbus system messages with the command: dbus-monitor --system

I noticed that always just before screen blanking there is a "lock" message where Interface=org.freesmartphone.Device.IdleNotifier:

--------dbus system monitor log----------------------
signal sender=:1.20 -> dest=(null destination) serial=3397 path=/org/freesmartphone/Device/IdleNotifier/0; interface=org.freesmartphone.Device.IdleNotifier; member=State
   string "idle_dim"
signal sender=:1.4 -> dest=(null destination) serial=2978 path=/org/freedesktop/NetworkManager/Devices/0; interface=org.freedesktop.NetworkManager.Device.Wireless; member=PropertiesChanged
   array [
      dict entry(
         string "Bitrate"
         variant             uint32 1000
      )
   ]
signal sender=:1.20 -> dest=(null destination) serial=3399 path=/org/freesmartphone/Device/IdleNotifier/0; interface=org.freesmartphone.Device.IdleNotifier; member=State
   string "idle_prelock"
signal sender=:1.20 -> dest=(null destination) serial=3401 path=/org/freesmartphone/Device/IdleNotifier/0; interface=org.freesmartphone.Device.IdleNotifier; member=State
   string "lock"
signal sender=:1.4 -> dest=(null destination) serial=2979 path=/org/freedesktop/NetworkManager/AccessPoint/0; interface=org.freedesktop.NetworkManager.AccessPoint; member=PropertiesChanged
[screen shuts down here]

[I move the mouse and after less than one minute...]
signal sender=:1.4 -> dest=(null destination) serial=3000 path=/org/freedesktop/NetworkManager/Devices/0; interface=org.freedesktop.NetworkManager.Device.Wireless; member=AccessPointRemoved
   object path "/org/freedesktop/NetworkManager/AccessPoint/15"
signal sender=:1.4 -> dest=(null destination) serial=3001 path=/org/freedesktop/NetworkManager/AccessPoint/0; interface=org.freedesktop.NetworkManager.AccessPoint; member=PropertiesChanged
   array [
      dict entry(
         string "Strength"
         variant             byte 81
      )
   ]
signal sender=:1.20 -> dest=(null destination) serial=3424 path=/org/freesmartphone/Device/IdleNotifier/0; interface=org.freesmartphone.Device.IdleNotifier; member=State
   string "idle_prelock"
signal sender=:1.20 -> dest=(null destination) serial=3426 path=/org/freesmartphone/Device/IdleNotifier/0; interface=org.freesmartphone.Device.IdleNotifier; member=State
   string "lock"

[screen shuts down here again]
----------------------------------

**So, the process which sent the message is "fsodeviced" (from "fso-deviced" package, the freesmartphone.org). I uninstalled the "fso-deviced" package and the problem went away.**

So, for anyone looking a solution to this annoying problem, this is the workaround. If you need more help on debugging this issue, I will reinstall this package in order to provide more useful data. 

Paul

---

