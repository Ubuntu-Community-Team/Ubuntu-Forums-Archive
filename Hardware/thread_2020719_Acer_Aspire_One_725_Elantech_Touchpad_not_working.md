---
title: "Acer Aspire One 725 Elantech Touchpad not working"
date: 2012-07-08
forum: Hardware
---

### Post by NihilisticNabarlek on 2012-07-08
Hello,

I just installed 12.04 on an Acer Aspire One 725, and after updating the kernel to 3.4, everything seems to work except the Elantech touchpad, which doesn't work at all.

"xinput list" in terminal shows the following:


Virtual core pointer                        id=2    [master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer                  id=4    [slave  pointer  (2)]
&#9116;   &#8627; USB Optical Mouse                           id=10    [slave  pointer  (2)]
&#9116;   &#8627; ETPS/2 Elantech Touchpad                    id=13    [slave  pointer  (2)]
&#9123; Virtual core keyboard                       id=3    [master keyboard (2)]
    &#8627; Virtual core XTEST keyboard                 id=5    [slave  keyboard (3)]
    &#8627; Power Button                                id=6    [slave  keyboard (3)]
    &#8627; Video Bus                                   id=7    [slave  keyboard (3)]
    &#8627; Power Button                                id=8    [slave  keyboard (3)]
    &#8627; Sleep Button                                id=9    [slave  keyboard (3)]
    &#8627; HD WebCam                                   id=11    [slave  keyboard (3)]
    &#8627; AT Translated Set 2 keyboard                id=12    [slave  keyboard (3)]
    &#8627; Acer WMI hotkeys                            id=14    [slave  keyboard (3)]

still can't get the touchpad running.  Any thoughts? ideas?

Thank-you

---

### Post by eneskuray on 2012-07-09
did you look additional drivers on dock ?

---

### Post by anirbanghosh on 2012-07-09
Same here. I have Acer Aspire One 722.
Elantech Touchpad is not working.

---

### Post by cortman on 2012-07-09
Hi, try [this]("http://ubuntuforums.org/showpost.php?p=11552780&postcount=6") or check out some solutions [here]("http://askubuntu.com/questions/74964/touchpad-stopped-working-on-an-acer-aspireone-d255e").

---

### Post by felo242 on 2012-07-11
Hi,
 
 I have the same problem. Just bought an Aspire One 725 and tried Ubuntu  12.04 LTS and Mint Cinnamon 13, both sadly do not support the touchpad.

> **cortman said:**
> Hi, try [this]("http://ubuntuforums.org/showpost.php?p=11552780&postcount=6") or check out some solutions [here]("http://askubuntu.com/questions/74964/touchpad-stopped-working-on-an-acer-aspireone-d255e").

this did not work for me :(

[EDIT]
Now it works :) Had to press Fn-F7 afterwards. However scrolling does not work yet...

---

### Post by NihilisticNabarlek on 2012-07-12
> **cortman said:**
> Hi, try [this]("http://ubuntuforums.org/showpost.php?p=11552780&postcount=6") or check out some solutions [here]("http://askubuntu.com/questions/74964/touchpad-stopped-working-on-an-acer-aspireone-d255e").


Nope, this definitely doesn't work, as soon as I enter: sudo vi /etc/modprobe.d/psmouse.conf it just hangs at the terminal forever, after about an hour I just killed the process.

---

### Post by cortman on 2012-07-12
Sure you don't just need to re-enable it with Fn+F7? That seems to be a common problem.

---

### Post by NihilisticNabarlek on 2012-07-14
Ok, turns out this solution from the link above works, though no scrolling:

This is a way to create a file that fixed my Aspire One, so I'm sharing it:
  
[LIST=1]
[*]Open the Terminal
[*]cd /etc/modprobe.d/
[*]gksudo gedit options.conf
[*]In the text editor, type: options psmouse proto=imps
[*]Save the file and close it.
[*]sudo modprobe -r psmouse
[*]sudo modprobe psmouse
[/LIST]

---

### Post by cortman on 2012-07-14
> **NihilisticNabarlek said:**
> Ok, turns out this solution from the link above works, though no scrolling:

This is a way to create a file that fixed my Aspire One, so I'm sharing it:
  
[LIST=1]
[*]Open the Terminal
[*]cd /etc/modprobe.d/
[*]gksudo gedit options.conf
[*]In the text editor, type: options psmouse proto=imps
[*]Save the file and close it.
[*]sudo modprobe -r psmouse
[*]sudo modprobe psmouse
[/LIST]


Great, thanks for sharing! Please mark the thread [SOLVED] so others know they can find a solution in it. 
Good luck!

---

### Post by OlsMo on 2012-07-22
Can someone explain this a little more detailed?. I dont understand what you do to make it work please tell me :(

---

### Post by green0eggs on 2012-08-11
Hello All.

I had the same problem. I found Nabarlek's solution worked, but I can't scroll. Furthermore, the 'Mouse and Touchpad' settings: there is no longer a touchpad tab (see attached). Am I missing something?


> **NihilisticNabarlek said:**
> 
[LIST=1]
[*]Open the Terminal
[*]cd /etc/modprobe.d/
[*]gksudo gedit options.conf
[*]In the text editor, type: options psmouse proto=imps
[*]Save the file and close it.
[*]sudo modprobe -r psmouse
[*]sudo modprobe psmouse
[/LIST]

Any further help'd be appreciated! Cheers.

---

### Post by sasukeskapa on 2012-08-13
I also used this

(Originally Posted by NihilisticNabarlek  
Open the Terminal
cd /etc/modprobe.d/
gksudo gedit options.conf
In the text editor, type: options psmouse proto=imps
Save the file and close it.
sudo modprobe -r psmouse
sudo modprobe psmouse)

method, but it says this:

sasukeskapa@sasukeskapa-AO725:/etc/modprobe.d$ sudo modprobe -r psmouse
WARNING: All config files need .conf: /etc/modprobe.d/options.comf, it will be ignored in a future release.
sasukeskapa@sasukeskapa-AO725:/etc/modprobe.d$ sudo modprobe psmouse
WARNING: All config files need .conf: /etc/modprobe.d/options.comf, it will be ignored in a future release.
sasukeskapa@sasukeskapa-AO725:/etc/modprobe.d$

And after reboot it forgets everything and I have to do it again.
Isn't there a permanent solution??? Also what could be the problem here???
(I'm using a Kubuntu 12.04)
(Also the scrolling doesn't working.)

After a next reboot now it works :)
Only the scrolling left to repair :)

---

### Post by Chuck Glenn on 2012-08-27
> **NihilisticNabarlek said:**
> Ok, turns out this solution from the link above works, though no scrolling:

This is a way to create a file that fixed my Aspire One, so I'm sharing it:
  
[LIST=1]
[*]Open the Terminal
[*]cd /etc/modprobe.d/
[*]gksudo gedit options.conf
[*]In the text editor, type: options psmouse proto=imps
[*]Save the file and close it.
[*]sudo modprobe -r psmouse
[*]sudo modprobe psmouse
[/LIST]


This worked, but the notification are is goofy. You can fn-F7 to togle off and on, but the notification icon always shows the "off" graphic. So for those of you who tried the above and think it doesn't work after rebooting, try fn-F7 even if it keeps showing you the "turned off" graphic.

---

### Post by NihilisticNabarlek on 2012-09-01
FIXED WITH NO HACKS YEAH!!!!!


Finally got Elantech touchpad working perfectly.  Follow the following instructions, reboot and you're golden

ELANTECH TOUCHPAD

In TERMINAL type the following: 
```

sudo gedit /etc/X11/xorg.conf

```

Then COPY and PASE the following in the file.  Save it, reboot and voila it works, multitouch and all!
```

Section "InputClass"
	Identifier "ETPS/2 Elantech Touchpad"
	MatchProduct "ETPS/2 Elantech Touchpad"
	MatchDevicePath "/dev/input/event*"
	Driver "synaptics"
	Option "TapButton1" "1"
	Option "TapButton2" "3"
	Option "TapButton3" "2"
	Option "VertTwoFingerScroll" "1"
	Option "HorizTwoFingerScroll" "1"
	Option "CoastingSpeed" "10"
	Option "EdgeMotionMinZ" "30"
	Option "EdgeMotionMaxZ" "40"
	Option "EdgeMotionMinSpeed" "100"
	Option "EdgeMotionMaxSpeed" "400"
	Option "FingerLow" "9"
	Option "FingerHigh" "12"
	Option "EmulateMidButtonTime" "0"
	Option "ClickPad" "True"
	Option "SoftButtonAreas" "50% 0 82% 0 0 0 0 0"
EndSection

```

---

### Post by sandyd on 2012-09-01
You are amazing.

Totally.

Touchpad fully works on my gathering-dust acer.

Thanks!

---

### Post by md2406 on 2012-09-14
I have Acer Aspire 725 netbook and I have edit xorg.conf and added the section but still touchpad is not working. Am I missing something?

---

### Post by MADinMelbourne on 2012-09-14
NEC E6300 running ubuntu 12.04.. touchpad was working fine until the last update, I have run dconfig-editor, there's nothing in the box to click under 'org'. Followed instruction from Narbalek and nothing changed. No tab is showing for touchpad in systems.

Not a coder, will follow instructions and keen to learn if anyone is willing to step me thru. Thanks.

---

### Post by jofa87 on 2012-09-14
hi,

i followed the instructions from chuck glenn, same problem. it works - no scrolling.No tab is showing for touchpad in systems.

at nihilistic nabarlek:  I use linux mint 13: there is no xorg.conf, but xorg.conf.failsafe. to change this file isn´t successful.

can you help me? thanks

---

### Post by norbs on 2012-09-28
I have reported this one: [https://bugs.launchpad.net/ubuntu/+source/linux-ac100/+bug/1058346](https://bugs.launchpad.net/ubuntu/+source/linux-ac100/+bug/1058346)

Please add more details to the report.

---

### Post by peteremmm on 2012-09-28
I have an Acer 725 - updated my ubuntu 12.04 to 12.10 and it works even with multitouch.

---

### Post by omiazad on 2012-09-29
> **NihilisticNabarlek said:**
> FIXED WITH NO HACKS YEAH!!!!!


Finally got Elantech touchpad working perfectly.  Follow the following instructions, reboot and you're golden

ELANTECH TOUCHPAD

In TERMINAL type the following: 
```

sudo gedit /etc/X11/xorg.conf

```Then COPY and PASE the following in the file.  Save it, reboot and voila it works, multitouch and all!
```

Section "InputClass"
    Identifier "ETPS/2 Elantech Touchpad"
    MatchProduct "ETPS/2 Elantech Touchpad"
    MatchDevicePath "/dev/input/event*"
    Driver "synaptics"
    Option "TapButton1" "1"
    Option "TapButton2" "3"
    Option "TapButton3" "2"
    Option "VertTwoFingerScroll" "1"
    Option "HorizTwoFingerScroll" "1"
    Option "CoastingSpeed" "10"
    Option "EdgeMotionMinZ" "30"
    Option "EdgeMotionMaxZ" "40"
    Option "EdgeMotionMinSpeed" "100"
    Option "EdgeMotionMaxSpeed" "400"
    Option "FingerLow" "9"
    Option "FingerHigh" "12"
    Option "EmulateMidButtonTime" "0"
    Option "ClickPad" "True"
    Option "SoftButtonAreas" "50% 0 82% 0 0 0 0 0"
EndSection

```

I did not have any ```
/etc/X11/xorg.conf
``` file so created one and pasted the above text. Did not help. :(

---

### Post by norbs on 2012-09-29
Installing Ubuntu 12.10 did not solve the problem for me.

---

### Post by omiazad on 2012-09-29
But Kubuntu works fine.

---

### Post by simontaylor on 2012-10-03
another Elantech Touchpad, on an Asus JC43u - running Mint 13 64-bit, suddenly my cursor went wild, making it difficult to write ... anything! since jumping from one line to the next...

tried the fix outlined here... seemed fine first runthrough... on reboot no dice.

don't get it. Any help welcome.

Best,

Simon

---

### Post by ozora on 2012-10-05
> **NihilisticNabarlek said:**
> FIXED WITH NO HACKS YEAH!!!!!


Finally got Elantech touchpad working perfectly.  Follow the following instructions, reboot and you're golden

ELANTECH TOUCHPAD

In TERMINAL type the following: 
```

sudo gedit /etc/X11/xorg.conf

```Then COPY and PASE the following in the file.  Save it, reboot and voila it works, multitouch and all!
```

Section "InputClass"
    Identifier "ETPS/2 Elantech Touchpad"
    MatchProduct "ETPS/2 Elantech Touchpad"
    MatchDevicePath "/dev/input/event*"
    Driver "synaptics"
    Option "TapButton1" "1"
    Option "TapButton2" "3"
    Option "TapButton3" "2"
    Option "VertTwoFingerScroll" "1"
    Option "HorizTwoFingerScroll" "1"
    Option "CoastingSpeed" "10"
    Option "EdgeMotionMinZ" "30"
    Option "EdgeMotionMaxZ" "40"
    Option "EdgeMotionMinSpeed" "100"
    Option "EdgeMotionMaxSpeed" "400"
    Option "FingerLow" "9"
    Option "FingerHigh" "12"
    Option "EmulateMidButtonTime" "0"
    Option "ClickPad" "True"
    Option "SoftButtonAreas" "50% 0 82% 0 0 0 0 0"
EndSection

```


i <3 youuuu!!!!!!!!!!!!!:guitar:

is there any possibility so i could use the side finger scroll to page  forward / back in firefox?

Thanks again!

---

### Post by simontaylor on 2012-10-05
no luck so far with this fix... any help welcome. Very.

---

### Post by omiazad on 2012-10-06
Before logging in to your desktop, press Fn+F7 that will enable the touch pad. 

:popcorn:

---

### Post by casbahdk on 2012-10-06
> **omiazad said:**
> Before logging in to your desktop, press Fn+F7 that will enable the touch pad.

In my experience, it doesn't matter if Fn + F7 is pressed before or after logging in, the trackpad will still enable. I find it extremely irritating however, to have to do that everytime I startup my 725 for the first time. Is that a bug or a feature?

---

### Post by omiazad on 2012-10-06
> **casbahdk said:**
> In my experience, it doesn't matter if Fn + F7 is pressed before or after logging in, the trackpad will still enable. I find it extremely irritating however, to have to do that everytime I startup my 725 for the first time. Is that a bug or a feature?


It's obviously a bug.

It working fine with Kubuntu.

---

### Post by frank75riz on 2012-10-25
Originally Posted by NihilisticNabarlek

this works..just did this and ghadzooks...it works

1.  Open the Terminal
2.  cd /etc/modprobe.d/
3.  gksudo gedit options.conf
4.  In the text editor (which will pop up) type without the quotes
    "options psmouse proto=imps"
5.  Save the file and close the terminal
6.  sudo modprobe -r psmouse
7.  sudo modprobe psmouse

THANK YOU NihilisticNabarlek

---

### Post by frank75riz on 2012-10-25
ALSO...DO NOT BOTHER CALLING ACER

You get someone from Asia, and they know nothing of Linux

---

### Post by omiazad on 2012-10-25
> **frank75riz said:**
> ALSO...DO NOT BOTHER CALLING ACER

You get someone from Asia, and they know nothing of Linux


I wonder why Ubuntu is not fixing it as it works fine in Kubuntu.

---

### Post by simontaylor on 2012-10-25
have tried this before without success - i.e. adding options psmouse proto=imps etc. -
and get this warning when I repeat the steps:

> WARNING: All config files need .conf: /etc/modprobe.d/options, it will be ignored in a future release.

advice welcome,

best,
Simon

---

### Post by WhiteDryas on 2012-10-29
@Simontaylor

It seems you have forgotten the .conf extension. The file should be saved as options.conf

---

### Post by smalss on 2012-11-27
You guys figure out these touchpad issues? I just bought myself an Acer Aspire One 725 and I was curious. Also, would it make a difference it you were running the 32 bit OS vs the 64 bit OS?

---

### Post by frank75riz on 2012-11-30
try hitting Fn+F7 before you sign in, it worked for me

---

### Post by smalss on 2012-12-19
FN + F7 does work. Just kinda annoying. Tried the other fixes with no luck. :( 

Anyone have any luck with this?

---

### Post by empollondefisica on 2012-12-21
What I found was that blacklisting the **acer-wmi** driver was all I had to do. The process is simple:
```

cd /etc/modprobe.d
gksudo gedit blacklist.conf

```

There is a long list of "blacklist .." items.  Add **blacklist acer-wmi** to the bottom of the list, save, reboot.

You may have to turn the touchpad on initially.  Mine was off by default; but, after turning it on, it has been on at each boot-up.

The only problem I have seen with this solution so far is that it does not display a message when you toggle the touchpad on/off.

---

### Post by sylvainhalle on 2013-01-12
Tried all solutions mentioned in this thread with no success. 

- Editing /etc/modprobe.d and reloading psmouse works intermittently. Sometimes is makes the touchpad work, but it stops responding after an unpredictable interval varying between one minute and one day. The funny thing is that I can tell when the mouse is about to quit on me, as the cursor first responds intermittently for a couple of seconds before dying completely.

- Changing /etc/X11/xorg.conf to add "Elantech Touchpad" settings and rebooting has no effect at all.

- Ditto for blacklisting acer-wmi.

- Pressed Fn+F7 about a zillion times throughout.

Actually "Elantech Touchpad" does not even appear when I type xinput list (no matter what).

Any more inspiration?

---

### Post by sylvainhalle on 2013-01-12
Breaking news: I rebooted in Windows, updated the BIOS to the latest version and now everything works perfectly. I even have a fully working Touchpad tab in the System settings.

---

### Post by sylvainhalle on 2013-01-13
Follow-up on my previous post: the touchpad worked only for a single boot. I suspended the computer, and when it resumed, the Touchpad tab was gone from the system settings (as was the touchpad itself). None of the solutions mentioned in this thread have worked since then (rebooted many times).

BTW, when booting in Windows, the touchpad works flawlessly, ruling out some hardware failure.

---

### Post by zxcvbnmelvin on 2013-04-04
thanks with this one. :) it works on mine.

---

### Post by JoeD906 on 2013-05-05
Observations:
When you press the Fn+F7 in Ubuntu (13.04), it show an icon that the track pad has been enable or disable but nothing happen.
Its work well in windows however.
Now in Windows press the Fn+F7 to disable the track pad and reboot to Ubuntu, then again press the Fn+F7 to enable the track pad again and now it work.
It will work after stand by but shut down mean to do the whole process again.

It may not be the best solution but it works for my and I hope that the Ubuntu Developers them self can see this and fix it properly in their next update or upgrade

---

### Post by flournnoi on 2013-05-08
> **NihilisticNabarlek said:**
> FIXED WITH NO HACKS YEAH!!!!!


Finally got Elantech touchpad working perfectly.  Follow the following instructions, reboot and you're golden

ELANTECH TOUCHPAD

In TERMINAL type the following: 
```

sudo gedit /etc/X11/xorg.conf

```

Then COPY and PASE the following in the file.  Save it, reboot and voila it works, multitouch and all!
```

Section "InputClass"
    Identifier "ETPS/2 Elantech Touchpad"
    MatchProduct "ETPS/2 Elantech Touchpad"
    MatchDevicePath "/dev/input/event*"
    Driver "synaptics"
    Option "TapButton1" "1"
    Option "TapButton2" "3"
    Option "TapButton3" "2"
    Option "VertTwoFingerScroll" "1"
    Option "HorizTwoFingerScroll" "1"
    Option "CoastingSpeed" "10"
    Option "EdgeMotionMinZ" "30"
    Option "EdgeMotionMaxZ" "40"
    Option "EdgeMotionMinSpeed" "100"
    Option "EdgeMotionMaxSpeed" "400"
    Option "FingerLow" "9"
    Option "FingerHigh" "12"
    Option "EmulateMidButtonTime" "0"
    Option "ClickPad" "True"
    Option "SoftButtonAreas" "50% 0 82% 0 0 0 0 0"
EndSection

```

WOW..KUDOS to this!

I have had two Acer Netbooks, starting from 2008.  My oldest one was a ZG5.  The one I currently have is the A0725. I have NEVER had a fully functioning touchpad in Linux with these netbooks until now!  I have had limited functionality in the past using the modprobe.d/ psmouse fix listed here, but I have always had to enable the mouse at startup with the Fn+F7 key.  I recently installed Linux Mint 13 (64 bit) on my A0725 and found that the mouse did not work at all at initial installation.  I again got mixed results with the modprobe.d/ psmouse change so I tried the above solution out and it worked.  This XORG solution did not enable the touchpad automatically at startup, but I also followed the advice to add "blacklist acer-wmi" to the blacklist options (also listed above). So now the touchpad loads at startup AND has full functionality.

This worked for me, but as described at the beginning of this thread, my elantech touchpad was listed in "xinput list" at the terminal.

---

### Post by JoeD906 on 2013-06-10
Update:

I didn't do any of the configuration they say jet it work for me.
OK, my new finding is that after a shutdown is that I don't need to start windows any more but I must press Fn + F7 before log in and the track-pad will star to work again.
If you do log in then the Fn + F7 will not work!

People just tested out and post to let the rest of us to know, thx

---

### Post by ronewolf on 2014-02-04
> **frank75riz said:**
> Originally Posted by NihilisticNabarlek

this works..just did this and ghadzooks...it works

1.  Open the Terminal
2.  cd /etc/modprobe.d/
3.  gksudo gedit options.conf
4.  In the text editor (which will pop up) type without the quotes
    "options psmouse proto=imps"
5.  Save the file and close the terminal
6.  sudo modprobe -r psmouse
7.  sudo modprobe psmouse

THANK YOU NihilisticNabarlek

This didn't seem to fix the problem for me (Aspire One 722, problem just started a fe ow days ago....). How do I back this hack out? That is how do I revert to the Elantech stuff?

BTW, touchpad works fine when the netbook is not plugged into power. I think its actually some sort of grounding problem as described here: [http://askubuntu.com/questions/309971/touchpad-doesnt-respond-when-power-is-pluggged](http://askubuntu.com/questions/309971/touchpad-doesnt-respond-when-power-is-pluggged)

---

### Post by jauntyjackalope2 on 2014-02-04
To everybody who **couldnt get it with the xorg.conf edit solution**, here may be **the trick** :
coming from this [http://ubuntuforums.org/showthread.php?t=2198715](http://ubuntuforums.org/showthread.php?t=2198715) i am pretty close to say i would bet that all ur problems are gone either :

* Installing the **Daily Build of 12.04.4** now,
 * or wait till the sixth (2 days) till the **12.04.4 officialy** arrivies (-:

u may test this with a simple live usb stick 
[http://cdimage.ubuntu.com/precise/daily-live/current/](http://cdimage.ubuntu.com/precise/daily-live/current/)
13.10 should also handle elantech nice.

**Have Fun (-:**

---

### Post by n4rps2 on 2014-02-18
Hello!

The problem is still present with the Samsung RV515-A03US in 12.04.4 (3.8.0-34 kernel). Adding that options.conf file to directory /etc/modprobe.d was the fix here.

73 DE N4RPS
Rob

Linux Lite 1.0.8
[http://www.linuxliteos.com](http://www.linuxliteos.com)

---

