---
title: "Multitouch Trackpad support"
date: 2010-05-10
forum: Hardware
---

### Post by dbhatt on 2010-05-10
[FONT=Verdana]I just upgraded my Ubuntu install to the latest release. I have a Synaptics trackpad that supports multitouch in Linux and I was trying to activate it. This is what I found: 

[http://ubuntu-snippets.blogspot.com/2009/03/multi-touch-for-anyall-synaptics.html](http://ubuntu-snippets.blogspot.com/2009/03/multi-touch-for-anyall-synaptics.html)

I tried what the site suggested, but I got the following error: [/FONT]
sudo: /etc/init.d/hal: command not found

[FONT=Verdana]Could someone tell me what's wrong/how to enable multitouch on my machine? I've made 
it work in Windows 7, so I'm pretty sure it is supported. 

Thanks!
[/FONT]

---

### Post by giova.86 on 2010-05-14
hal doesn't exist any more in ubuntu 10.04. Try with these command:

xinput set-int-prop "SynPS/2 Synaptics TouchPad" "Two-Finger Scrolling" 8 1
xinput set-int-prop "SynPS/2 Synaptics TouchPad" "Synaptics Two-Finger Scrolling" 8 1 1
xinput set-int-prop "SynPS/2 Synaptics TouchPad" "Synaptics Two-Finger Pressure" 32 10
xinput set-int-prop "SynPS/2 Synaptics TouchPad" "Synaptics Two-Finger Width" 32 8

I have an acer 4820tg and it works.

---

### Post by dbhatt on 2010-05-14
It worked. Thanks!

---

### Post by dbhatt on 2010-05-14
I just noticed that everytime I restart my machine, the multitouch features go away and I have to run those commands again. Is there a way to permanently enable them?

---

### Post by kio_http on 2010-05-15
> **dbhatt said:**
> I just noticed that everytime I restart my machine, the multitouch features go away and I have to run those commands again. Is there a way to permanently enable them?

Open your textediting program e/g gedit. kate, kwrie, mousepad etc

Paste this in it
```
#!/bin/bash
xinput set-int-prop "SynPS/2 Synaptics TouchPad" "Two-Finger Scrolling" 8
 1
xinput set-int-prop "SynPS/2 Synaptics TouchPad" "Synaptics Two-Finger 
Scrolling" 8 1 1
xinput set-int-prop "SynPS/2 Synaptics TouchPad" "Synaptics Two-Finger 
Pressure" 32 10
xinput set-int-prop "SynPS/2 Synaptics TouchPad" "Synaptics Two-Finger 
Width" 32 8
```

(Each command on a separate line. )
Save the file somewhere as .run extension

Now go here.
System > Preferences > Sessions and click on Startup Programs.   Click 'Add' and enter the name of the script.  It should do the work  from there!

---

### Post by VeeDubb on 2010-05-15
Wow.  I've been looking for a solution for this for more than a week.  I had no idea it was so easy.

Any idea how to enable zoom features or 3-finger clicking for middle click?

---

### Post by giova.86 on 2010-05-15
If someone has a problem with the script, he must add the following command at the beginning of the script: sleep 10, to obtain:

```

#!/bin/bash
sleep 10
xinput set-int-prop "SynPS/2 Synaptics TouchPad" "Two-Finger Scrolling" 8 1
xinput set-int-prop "SynPS/2 Synaptics TouchPad" "Synaptics Two-Finger Scrolling" 8 1 1
xinput set-int-prop "SynPS/2 Synaptics TouchPad" "Synaptics Two-Finger Pressure" 32 10
xinput set-int-prop "SynPS/2 Synaptics TouchPad" "Synaptics Two-Finger Width" 32 8

```

---

### Post by IcarusR on 2010-05-15
For other options available with synaptics see the man page.

```
man synaptics
```

---

### Post by VeeDubb on 2010-05-15
Thank you for the reference to the synaptics man page, but I still have a problem.

It appears to be primarily concerned with setting up your xorg.conf, which really doesn't help me.

I also tried looking through the xinput man pages, but I'm really having a hard time seeing how to take the information from those two man pages, and come up with a command that does what I want it to do.

There are only two other features I want to enable, both of which at referenced in the synaptics man page.

1. 3-finger clicking to enter a "middle click"
2. The "guest mouse" function, which if I understand correctly, will automatically disable the touchpad if an external mouse is plugged in.

Neither of these functions is a 'deal breaker' but I would love to get them working.  If you can explain how to use the information from the synaptics man page to figure out an xinput command, I would appreciate it greatly.

Thank you.

---

### Post by bitinerant on 2010-05-18
This works on the Asus Eee 1005HA as well.  :-)

---

### Post by moteprime on 2010-05-19
And it works on my Asus 1005P also.

If the driver exists, recognize the hardware and are working fine, why does it not work in gnome mouse settings and two finger scrolling out of the box?

The two finger touch that should (to my experience), work as middle mouse button appears to works as right mouse button. I have been struggling with the commando to change this but with little luck.
The "man synaptics" descriptions does not provide much information, are there a better description somewhere? 
I tried with:
xinput set-int-prop "SynPS/2 Synaptics TouchPad" "TapButton2" 3
and:
xinput set-int-prop "SynPS/2 Synaptics TouchPad" "TapButton2" "3"

But I get the error: "Invalid format 3"
Is it the right command at all, and what are the syntax.

---

### Post by KlavKalashj on 2010-05-19
huh? you don't have the taps and scroll by default? O.o

---

### Post by VeeDubb on 2010-05-19
> **KlavKalashj said:**
> huh? you don't have the taps and scroll by default? O.o

One finger tap for click, yes.

Edge scrolling, yes.

Two finger tap for middle or right click, no.

Three finger tap for middle or right click, no.

Circular scrolling, no.

Advanced gestures like pinch/spread to zoom, no.

---

### Post by crisco552 on 2010-05-22
I have a Dell Inspiron 1545, and it supports 2 finger scoll if you make it an OS X machine, but I can't seem to get any of those scripts to work, it always says the device is not found. Is there a way to fix this?

---

### Post by dbhatt on 2010-05-23
> **giova.86 said:**
> If someone has a problem with the script, he must add the following command at the beginning of the script: sleep 10, to obtain:

```

#!/bin/bash
sleep 10
xinput set-int-prop "SynPS/2 Synaptics TouchPad" "Two-Finger Scrolling" 8 1
xinput set-int-prop "SynPS/2 Synaptics TouchPad" "Synaptics Two-Finger Scrolling" 8 1 1
xinput set-int-prop "SynPS/2 Synaptics TouchPad" "Synaptics Two-Finger Pressure" 32 10
xinput set-int-prop "SynPS/2 Synaptics TouchPad" "Synaptics Two-Finger Width" 32 8

```

Sorry to be replying so late, but I did what you suggested and it still does not seem to work. I tried to make the .run file executable and ran it in my current session, but that did not activate the features even for that one session let alone all of them. 

I think i should mention that I did not find a "sessions" section in System>Preferences, but there was the option of Startup programs and I put the file in that. Could someone tell me what's wrong?

---

### Post by moteprime on 2010-05-24
I made the script with the .run file and made it executeable.
I put it in the list of startup applications in system-> preferences-> startup applications.

The script work when I run it, but it does not execute during startup? so I have to run it manually every time I log in. 

I Still haven't figured out how to make the two finger tap work?

---

### Post by ShiroKitsune on 2010-05-25
Hello! Okay I have been wacking at this all day and after checking some other posts I was able to come up with a combination that works witch was this.

[[IMG]http://img52.imageshack.us/img52/7925/bored3.th.png[/IMG]](http://img52.imageshack.us/i/bored3.png/)

Uploaded with [ImageShack.us](http://imageshack.us)

And added that to my pre-start programs in my settings

I'm sure you can do the same with ubuntu 

Also make sure you make it's executable and thats how I got mine to work, let me know if it also works for anyone else if you want I could upload the file it self to a site, just ask =]

---

### Post by moteprime on 2010-05-26
Thanks ShiroKitsune.

It now runs the script and two-finger scrolling works. -Was it a matter of delaying the script so that it does not run before gnome is fully loaded?

I still have not figured out how to make two-finger tap work as the middle mouse button.

---

### Post by joseamirandavelez on 2010-06-03
Hi guys,

I have tried multiple solutions to this but none of them have worked.

I have a Gateway NV7915U, with a Synaptics touchpad. Multitouch works OK on Windows 7 but it does not work in Ubuntu 10.04 LTS using the solutions found here or anywhere on the internet.

When I put two fingers on the touchpad, the pointer just goes crazy! It starts to move all around the screen.

Any ideas?

-Jose

---

### Post by briteflite on 2010-06-09
The command works great on an Asus eee 1005HA, but I'm having trouble with the .run. I've tried both versions (with and without the Sleep 10), saved it as a .run in gedit, and have it selected as one of my startup items, but I still have to manually re-enter the code in Terminal every time I restart.

Any ideas?

P.S. Thanks SO MUCH for the original code, it really saved my *** during my XP-to-Ubuntu transition.

---

### Post by ethan1701 on 2010-06-10
> **joseamirandavelez said:**
> Hi guys,

I have tried multiple solutions to this but none of them have worked.

I have a Gateway NV7915U, with a Synaptics touchpad. Multitouch works OK on Windows 7 but it does not work in Ubuntu 10.04 LTS using the solutions found here or anywhere on the internet.

When I put two fingers on the touchpad, the pointer just goes crazy! It starts to move all around the screen.

Any ideas?

-Jose
I also have an NV7915u, and this script actually did work. I'm quite pleased with it (it's not perfect, but I can tweak it!)
I wonder if it's working for me but not for you because you have not updated the system. I'm presently running on kernel 2.6.32.22 (it's an update relative to the one that installs from the CD).
See if that fixes the issue for you?

---

### Post by i.siddharth.iitd on 2010-06-19
> **giova.86 said:**
> hal doesn't exist any more in ubuntu 10.04. Try with these command:

xinput set-int-prop "SynPS/2 Synaptics TouchPad" "Two-Finger Scrolling" 8 1
xinput set-int-prop "SynPS/2 Synaptics TouchPad" "Synaptics Two-Finger Scrolling" 8 1 1
xinput set-int-prop "SynPS/2 Synaptics TouchPad" "Synaptics Two-Finger Pressure" 32 10
xinput set-int-prop "SynPS/2 Synaptics TouchPad" "Synaptics Two-Finger Width" 32 8

I have an acer 4820tg and it works.
@ giova.86
Hi, I am very new to Ubuntu and I have just installed Lucid Lynx on my Acer Aspire 5740G in dual boot with Win 7.
I used the commands that you first mentioned in the terminal and two finger scroll and two finger tap got activated.
I read on in this thread to find out that it won't automatically start the next time I boot. So I created the .run file as you instructed and added it to the Startup Applications. That did not work the next time I booted.
Moreover, the terminal commands no longer activated multi touch when I tried again and my mouse goes mad when i put more than one finger on the trackpad. I've tried removing the .run script from the startup to make sure that it doesn't interfere with the terminal commands, but that doesn't work either.
Can you suggest a solution?

---

### Post by joseamirandavelez on 2010-06-19
OK. It worked for me but now Ubuntu is freezing from time to time if I use multitouching... I think Im gonna remove multitouch...

---

### Post by ethan1701 on 2010-06-25
I found that even after adding the script to the bootup, it wasn't working. I presumed it was because it was run before all the modules it relied on had loaded.
I modified the script to the following:
```
#!/bin/bash
#enable multitouch
sleep 10
xinput set-int-prop "SynPS/2 Synaptics TouchPad" "Two-Finger Scrolling" 8 1
xinput set-int-prop "SynPS/2 Synaptics TouchPad" "Synaptics Two-Finger Scrolling" 8 1 1
xinput set-int-prop "SynPS/2 Synaptics TouchPad" "Synaptics Two-Finger Pressure" 32 10
xinput set-int-prop "SynPS/2 Synaptics TouchPad" "Synaptics Two-Finger Width" 32 8

```
This file is saved as startup.run in my home directory.
I then ran the command
```
chmod +x startup.run
``` to make the file executable.
Finally, under System-> Preferences-> Startup Applications, I added the file.
Multitouch now works upon startup.
As for @joseamirandavelez 's freezes - I've been encountering this problem as well, but have been suffering from it even before making these changes. Especially when using Firefox (Had to switch to Chrome, I'm sad to say). I don't think that the multitouoch is what's making the difference here...

-Ethan

---

### Post by RavensKrag on 2010-06-26
I'm so happy to finally find a current solution that actually works! Most of the solution's I've seen to get multitouch working were old ways that I believe are depreciated now.  

Still, just one question.  Is there a way to make the scrolling less sensitive? My scrolling goes crazy when I try to simply move the page a little bit.

---

### Post by octavius on 2010-07-03
Hello.

Has anyone noticed any change on the behavior of the touchpath with kernel 2.6.32-23-generic?

The steps and values of xinput described here where working excellent con kernel 2.6.32-22 but since I updated the touchpath goes crazy if I use more than one finger, leaving multitouch useless and can't revert back...

Any ideas on this?

---

### Post by moore.bryan on 2010-07-03
Now that Synaptics has release the Gesture Suite for Ubuntu OEM, how long do you all think it'll take before we see a possible software release?

---

### Post by Anilix on 2010-07-04
> **octavius said:**
> Hello.

Has anyone noticed any change on the behavior of the touchpath with kernel 2.6.32-23-generic?

The steps and values of xinput described here where working excellent con kernel 2.6.32-22 but since I updated the touchpath goes crazy if I use more than one finger, leaving multitouch useless and can't revert back...

Any ideas on this?


Worked at first but after a couple of reboots now everytime I try to start the script even manually it just opens up gedit

Touchpad goes crazy again

Kernel 2.6.32.23-generic

---

### Post by moore.bryan on 2010-07-04
> **Anilix said:**
> Worked at first but after a couple of reboots now everytime I try to start the script even manually it just opens up gedit

Touchpad goes crazy again

Kernel 2.6.32.23-generic

Sorry, folks... I don't have this problem and I'm running the 2.6.32.23-generic kernel.

---

### Post by nerdy_kid on 2010-07-04
> **kio_http said:**
> Open your textediting program e/g gedit. kate, kwrie, mousepad etc

Paste this in it
```
#!/bin/bash
xinput set-int-prop "SynPS/2 Synaptics TouchPad" "Two-Finger Scrolling" 8
 1
xinput set-int-prop "SynPS/2 Synaptics TouchPad" "Synaptics Two-Finger 
Scrolling" 8 1 1
xinput set-int-prop "SynPS/2 Synaptics TouchPad" "Synaptics Two-Finger 
Pressure" 32 10
xinput set-int-prop "SynPS/2 Synaptics TouchPad" "Synaptics Two-Finger 
Width" 32 8
```

(Each command on a separate line. )
Save the file somewhere as .run extension

Now go here.
System > Preferences > Sessions and click on Startup Programs.   Click 'Add' and enter the name of the script.  It should do the work  from there!
then add executible permissions: either right  click the file and in properties check all executing or open a terminal and do chmod +x FILENAME

---

### Post by nerdy_kid on 2010-07-04
as a side thought, why not just install gsynaptics?

---

### Post by VeeDubb on 2010-07-04
> **nerdy_kid said:**
> as a side thought, why not just install gsynaptics?

Because there are a lot of options not covered by gsynaptics.

---

### Post by nerdy_kid on 2010-07-04
> **VeeDubb said:**
> Because there are a lot of options not covered by gsynaptics.

well for the extent of this topic gsynaptics would be fine...

---

### Post by VeeDubb on 2010-07-05
Well, unless it's been updated in the last few weeks, no it won't.  gsynaptics won't even enable 2-finger scrolling.  The best it can do is edge scrolling.

---

### Post by VeeDubb on 2010-07-05
I just checked, gsynaptics doesn't even have an option to enable 2-finger scroll.

gpointing-device-settings which claims to be the successor to gsynaptics has the option, and quite a few others, but it doesn't work on my touchpad even though it is a synaptics touchpad.

---

### Post by seandgibbonsy on 2010-08-10
> **moore.bryan said:**
> Now that Synaptics has release the [Gesture Suite]("http://www.synaptics.com/solutions/technology/gestures/touchpad-linux") for Ubuntu OEM, how long do you all think it'll take before we see a possible software release?

It would be great if we could get this released to the Ubuntu community.  I'd like to be able to use pinch, 3-finger tapping, rotating, and the other gestures they have available with the suite.

---

### Post by brenosabino on 2010-08-10
I finally got it working on my asus 1005ha-p

This is the script im using (multitouch.run):

> #!/bin/bash

sleep 10
xinput set-int-prop "SynPS/2 Synaptics TouchPad" "Two-Finger Scrolling" 8 1

xinput set-int-prop "SynPS/2 Synaptics TouchPad" "Synaptics Two-Finger Scrolling" 8 1 1

xinput set-int-prop "SynPS/2 Synaptics TouchPad" "Synaptics Two-Finger Pressure" 32 10

xinput set-int-prop "SynPS/2 Synaptics TouchPad" "Synaptics Two-Finger Width" 32 8

xinput set-int-prop "SynPS/2 Synaptics TouchPad" "Synaptics Edge Scrolling" 8 0 0 0 

xinput set-int-prop "SynPS/2 Synaptics TouchPad" "Synaptics Jumpy Cursor Threshold" 32 110

synclient TapButton2=2

exit

I placed it on the home folder, set it as executable (chmod +x multitouch.run) and added it to the session startup list.

The last two xinput commands are to disable edge scrolling and to avoid jumpy cursor after two finger scroll. And the synclient command is to enable middle mouse click with two finger tap.

---

### Post by moteprime on 2010-08-12
Thanks, it is an improvement. And i really love to have the two finger middle mouse click working.

It still puzzles me, why we have to do all this, if the touchpad driver are there, and are working. Why can't it be made to work with Ubuntu out of the box?

---

### Post by ottofit on 2010-08-30
In Preferences/Mouse a "Touchpad" Tab appears, where you can select "Two-finger scrolling"
Did you check out that already? It just worked for my old M6NE centrino asus laptop.
My 2 euroc.

---

### Post by ottofit on 2010-08-30
sorry, double post, can't delete it

---

### Post by moore.bryan on 2010-08-30
Where's our "pinch" zoom, dammit!
:-)

---

### Post by moteprime on 2010-08-31
> In Preferences/Mouse a "Touchpad" Tab appears, where you can select "Two-finger scrolling"
Did you check out that already? It just worked for my old M6NE centrino asus laptop.
My 2 euroc

I have never been able to select it, it's greyed out on my Asus eee 1005P.

---

### Post by higashi on 2010-09-03
> **giova.86 said:**
> hal doesn't exist any more in ubuntu 10.04. Try with these command:

xinput set-int-prop "SynPS/2 Synaptics TouchPad" "Two-Finger Scrolling" 8 1
xinput set-int-prop "SynPS/2 Synaptics TouchPad" "Synaptics Two-Finger Scrolling" 8 1 1
xinput set-int-prop "SynPS/2 Synaptics TouchPad" "Synaptics Two-Finger Pressure" 32 10
xinput set-int-prop "SynPS/2 Synaptics TouchPad" "Synaptics Two-Finger Width" 32 8

I have an acer 4820tg and it works.

Thanks so much!

---

### Post by marcobbi on 2010-09-24
> **brenosabino said:**
> I finally got it working on my asus 1005ha-p

This is the script im using (multitouch.run):



I placed it on the home folder, set it as executable (chmod +x multitouch.run) and added it to the session startup list.

The last two xinput commands are to disable edge scrolling and to avoid jumpy cursor after two finger scroll. And the synclient command is to enable middle mouse click with two finger tap.

how can i automatically resume this script after suspend? thank you

---

### Post by banstew on 2010-10-26
> **marcobbi said:**
> how can i automatically resume this script after suspend? thank you

I would like to know this as well. Also the script quit working for me when I try to run it.

What I have is

```

#!/bin/bash
#enable multitouch

sleep 10
xinput set-int-prop "SynPS/2 Synaptics TouchPad" "Two-Finger Scrolling" 8 1

xinput set-int-prop "SynPS/2 Synaptics TouchPad" "Synaptics Two-Finger Scrolling" 8 1 1

xinput set-int-prop "SynPS/2 Synaptics TouchPad" "Synaptics Two-Finger     Pressure" 32 10

xinput set-int-prop "SynPS/2 Synaptics TouchPad" "Synaptics Two-Finger     Width" 32 8

xinput set-int-prop "SynPS/2 Synaptics TouchPad" "Synaptics Edge Scrolling" 8 0 0 0

xinput set-int-prop "SynPS/2 Synaptics TouchPad" "Synaptics Jumpy Cursor Threshold" 32 110

synclient TapButton2=2

exit

```I can still enter the commands in terminal and they work, but having a working script would be nice. Also I am on an Acer Aspire 5742

Edit: I am running ubuntu 10.10

---

### Post by dubrict on 2010-11-19
Mine only works when I set "Synaptics Two-Finger Width" to 5, and orient my fingers vertical to each other, rather than horizontal.  I'm on a HP G61-511wm.

---

### Post by Jrgifford on 2010-11-19
Hello, I have a Asus Eee PC 1001P, and I had the two-finger scrolling working perfectly when I was on 10.04 Netbook, but now that I upgraded to 10.10 I can't get it to work. I've tried everything I could find on the forums, but to no avail. I'm about ready to downgrade to 10.04.

---

### Post by Paulmoore on 2010-12-08
This works for me although I have a couple of problems.

The two finger double-tap as right click is incredibly annoying. How can I disable it?

Also from time-to time when typing the cursor jumps as an accidental palm rest is considered two finger scrolling. Is there a way to get the driver to recognize two discrete touches instead of one wide one?

---

### Post by rg4w on 2010-12-08
> **crisco552 said:**
> I have a Dell Inspiron 1545, and it supports 2 finger scoll if you make it an OS X machine...

How did you do that?

Man, I sure wish I could get two-finger scrolling to work on my Dell Vostro 1400, but it seems the hardware is too limited to support it, so I'm stuck with edge-scrolling.

---

### Post by kane0 on 2011-03-31
Hi All,

This is my first post so sorry if its a little stupid, 

im not exactly sure why this is, but my trackpad is crazy if i put more than one finger on it the mouse zooms everywhere and i cant control it ... i tried the scripts on page 1 to get the 2 finger scroll happening with no success. 

I have an acer 4820tg machine with kubuntu 10.10... if anyone knows why this is the case it would be brilliant ...

thanks :)

Kaneo

---

### Post by moteprime on 2011-04-01
Hi. Kane0
I cant really help you with your problem, but you should check out Ubuntu 11.04 Natty Narwhale, the multi touch works out of the box with no scripts now.

---

### Post by kane0 on 2011-04-01
> **moteprime said:**
> Hi. Kane0
I cant really help you with your problem, but you should check out Ubuntu 11.04 Natty Narwhale, the multi touch works out of the box with no scripts now.

I just have to mention real quick, the upgrade process with kubuntu/ubuntu is awesome!...

upgrading now and will give it a try :)

---

### Post by Sim-I-Am :} on 2011-05-10
This helped me out a whole lot. Doesn't do anything about three- or four-finger gestures, but the the two-finger scrolling works great, both vertically, and horizontally. It also seems to have enabled a right-click emulation when tapping with two fingers....

I might try to mess around with adding synclient commands to this script, now that I've found one that actually works....

Oh, I'm running Natty 64-bit by the way.

[http://mixeduperic.com/linux/ubuntu-1004-how-to-setup-two-finger-scroll-on-laptop-touch-pad.html](http://mixeduperic.com/linux/ubuntu-1004-how-to-setup-two-finger-scroll-on-laptop-touch-pad.html)

---

### Post by libssd on 2011-11-29
Thanks so much for this. Yesterday, I experimented with a variant openSUSE distribution, and discovered that the trackpad on my Acer D150 netbook supported two-finger scrolling as a mouse preference (this choice is grayed out on Ubuntu 10.04. It's my understanding that this has been solved in Ubuntu 11.10, but I don't want to go there. 

Looking for a solution took me to:

[http://ubuntu-snippets.blogspot.com/2009/03/multi-touch-for-anyall-synaptics.html](http://ubuntu-snippets.blogspot.com/2009/03/multi-touch-for-anyall-synaptics.html) [didn't work]
[http://ubuntuforums.org/showthread.php?t=1426782](http://ubuntuforums.org/showthread.php?t=1426782) [didn't work]

While I would have preferred a solution that activated the two-finger scrolling radio button in the mouse preference, your solution works, and is far simpler than the other approaches. The only thing missing (which is addressed later in this thread, #37) is to make the new script executable using chmod +x.

I also have a Cr-48 Chromebook, which supports both two-finger scrolling and two-finger tap = right click, and now the trackpad on my Acer netbook supports both these features, so I don't have to re-learn when switching from one to the other.

> **kio_http said:**
> Open your textediting program e/g gedit. kate, kwrie, mousepad etc

Paste this in it
```
#!/bin/bash
xinput set-int-prop "SynPS/2 Synaptics TouchPad" "Two-Finger Scrolling" 8
 1
xinput set-int-prop "SynPS/2 Synaptics TouchPad" "Synaptics Two-Finger 
Scrolling" 8 1 1
xinput set-int-prop "SynPS/2 Synaptics TouchPad" "Synaptics Two-Finger 
Pressure" 32 10
xinput set-int-prop "SynPS/2 Synaptics TouchPad" "Synaptics Two-Finger 
Width" 32 8
```
(Each command on a separate line. )
Save the file somewhere as .run extension

Now go here.
System > Preferences > Sessions and click on Startup Programs.   Click 'Add' and enter the name of the script.  It should do the work  from there!

---

### Post by libssd on 2011-11-29
**One more observation:** I assume that because two-finger scrolling isn't supported by the Mouse/Trackpad preference in Ubuntu 10.04 (at least not on my hardware), changes to this preference will override the startup script. One reason I was so interested in two-finger scrolling is that edge scrolling was driving me crazy. When I disabled off edge scrolling, two-finger scrolling *also* stopped working until I rebooted. This is not meant as a criticism; merely a "heads up" — don't make changes to the Mouse/Trackpad preference.

---

