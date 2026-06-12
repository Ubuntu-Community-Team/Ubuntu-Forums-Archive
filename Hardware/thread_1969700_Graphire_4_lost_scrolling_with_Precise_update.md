---
title: "Graphire 4 lost scrolling with Precise update"
date: 2012-04-30
forum: Hardware
---

### Post by intruderukr on 2012-04-30
I have a Dell Inspiron e1405, my wacom tablet worked well with Onieric, but now on Precise I've lost scrolling
```
~$ xsetwacom -v --list dev --verbose
... Display is '(null)'.
... 'list' requested.
... Found device 'Virtual core XTEST pointer' (4).
... Found device 'Virtual core XTEST keyboard' (5).
... Found device 'Video Bus' (6).
... Found device 'Power Button' (7).
... Found device 'Sleep Button' (8).
... Found device 'Wacom Graphire4 4x5 stylus' (9).
Wacom Graphire4 4x5 stylus      	id: 9	type: STYLUS    
... Found device 'AT Translated Set 2 keyboard' (10).
... Found device 'SynPS/2 Synaptics TouchPad' (11).
... Found device 'Dell WMI hotkeys' (12).
... Found device 'Wacom Graphire4 4x5 eraser' (13).
Wacom Graphire4 4x5 eraser      	id: 13	type: ERASER    
... Found device 'Wacom Graphire4 4x5 cursor' (14).
Wacom Graphire4 4x5 cursor      	id: 14	type: CURSOR    
... Found device 'Wacom Graphire4 4x5 pad' (15).
Wacom Graphire4 4x5 pad         	id: 15	type: PAD  
[CODE]:~$ sudo add-apt-repository https://launchpad.net/~doctormo/+archive/wacom-plus
```
[/CODE]
```
:~$ git clone git://linuxwacom.git.sourceforge.net/gitroot/linuxwacom/xf86-input-wacom
Cloning into 'xf86-input-wacom'...
remote: Counting objects: 11225, done.
remote: Compressing objects: 100% (5657/5657), done.
remote: Total 11225 (delta 8702), reused 7009 (delta 5553)
Receiving objects: 100% (11225/11225), 2.83 MiB | 640 KiB/s, done.
Resolving deltas: 100% (8702/8702), done.

```
```
~/xf86-input-wacom$ ./autogen.sh --prefix=/usr --libdir=/usr/lib
autoreconf: Entering directory `.'
autoreconf: configure.ac: not using Gettext
autoreconf: running: aclocal 
configure.ac:43: error: must install xorg-macros 1.8 or later before running autoconf/autogen
configure.ac:43: the top level
autom4te: /usr/bin/m4 failed with exit status: 1
aclocal: /usr/bin/autom4te failed with exit status: 1
autoreconf: aclocal failed with exit status: 1

```
What am I doing wrong please?
Thanks, alleykat

---

### Post by Favux on 2012-04-30
Hi alleykat,

First you do not want to install DoctorMO's PPA.  It is outdated and the wacom.ko (usb kernel driver/module) that comes with Precise's 3.2 kernel is about 1 year newer.  I checked the PPA and Precise isn't in it so I don't think you managed to install anything.  If you did, maybe using another PPA, let me know.

No reason to update the xf86-input-wacom driver either.  The Precise default is 0.14.0 which should work fine with your Graphire.  I'm not clear why you are seeing the error:
```
configure.ac:43: error: must install xorg-macros 1.8 or later before running autoconf/autogen
```
anyway.  Precise does have xorg-macros 1.8 or later.  That error is something you would see with Lucid (10.04) not 12.04.

So with just the default Wacom drivers please post the outputs of:
```
xinput list
```
and
```
xsetwacom list
```

---

### Post by intruderukr on 2012-05-01
Thank you, Favux, for the reply.
You said to go back to default Wacom drivers.  Could you please guide me in how I should restore the defaults?  Sorry I don't know how to undo what I did when I installed the doctormo drivers.
Thanks, alleykat

---

### Post by Favux on 2012-05-01
I think it should show up in the Synaptic Package Manager since it was a PPA.  Uninstall it through that.  Or also the Software Center I guess.  For either search 'wacom'.  Doesn't the PPA have wacom in the name?  In Software Center you'd have to tell it to show you the technical stuff I suppose.  I don't remember for sure if the PPA had uninstall instructions, I don't thinks so.

---

### Post by intruderukr on 2012-05-01
Hi Favux, thanks for the quick response - here is a screenshot of my wacom query in synaptic: [IMG]http://dl.dropbox.com/u/21860535/Screenshot%20from%202012-05-01%2009%3A10%3A45.png[/IMG]
It seems as if the x.org drivers are installed.
here is the output of the command you gave me, ( I have not removed any drivers)
code:
:~$ xinput list
&#9121; Virtual core pointer                    	id=2	[master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer              	id=4	[slave  pointer  (2)]
&#9116;   &#8627; Wacom Graphire4 4x5 stylus              	id=9	[slave  pointer  (2)]
&#9116;   &#8627; SynPS/2 Synaptics TouchPad              	id=11	[slave  pointer  (2)]
&#9116;   &#8627; Wacom Graphire4 4x5 eraser              	id=13	[slave  pointer  (2)]
&#9116;   &#8627; Wacom Graphire4 4x5 cursor              	id=14	[slave  pointer  (2)]
&#9116;   &#8627; Wacom Graphire4 4x5 pad                 	id=15	[slave  pointer  (2)]
&#9123; Virtual core keyboard                   	id=3	[master keyboard (2)]
    &#8627; Virtual core XTEST keyboard             	id=5	[slave  keyboard (3)]
    &#8627; Video Bus                               	id=6	[slave  keyboard (3)]
    &#8627; Power Button                            	id=7	[slave  keyboard (3)]
    &#8627; Sleep Button                            	id=8	[slave  keyboard (3)]
    &#8627; AT Translated Set 2 keyboard            	id=10	[slave  keyboard (3)]
    &#8627; Dell WMI hotkeys                        	id=12	[slave  keyboard (3)]

and 
code:
trude@trude-MXC061:~$ xsetwacom list
Wacom Graphire4 4x5 stylus      	id: 9	type: STYLUS    
Wacom Graphire4 4x5 eraser      	id: 13	type: ERASER    
Wacom Graphire4 4x5 cursor      	id: 14	type: CURSOR    
Wacom Graphire4 4x5 pad         	id: 15	type: PAD

---

### Post by intruderukr on 2012-05-01
the PPA:
[IMG]http://dl.dropbox.com/u/21860535/Screenshot%20from%202012-05-01%2009%3A23%3A09.png[/IMG]

---

### Post by Favux on 2012-05-01
Hi alleykat,

I admit to being a little confused.  Your Software Sources sure seems to show the PPA.  But if you go directly to the site:  [https://launchpad.net/~doctormo/+archive/wacom-plus](https://launchpad.net/~doctormo/+archive/wacom-plus)  and look at the dates you'll see they are more than a year old.  And click on "View package details" you'll see Natty was the last release any package was built for.  So it shouldn't have installed anything.  I wouldn't think Software Sources would let you set it up in Precise, but hey.

But let's check anyway because what you are describing sounds like an old bug and the PPA may have installed an outdated xf86-input-wacom.  That's the Wacom X driver.  The default for Precise is 0.14.0 and the PPA has 0.10.11.  So in a terminal run this command:
```
xsetwacom -V
```
and the output will tell you what version of xf86-input-wacom you have.

The Ubuntu package that contains xf86-input-wacom is xserver-xorg-input-wacom.  You show that in your first screen shot.  If you do have the old xf86-input-wacom just tell Software Center you want to reinstall xserver-xorg-input-wacom.  Then restart.

Your *xinput list* and *xsetwacom list* show the tablet is on the Wacom drivers so that isn't the problem.

---

### Post by intruderukr on 2012-05-01
Thanks for sticking with me, Favux.
Here's the result of the querie:
```
~$ xsetwacom -V
0.14.0

```
So this is the current driver?
Does that mean my scrolling days are over? (weeps)
Any other suggestions? Should I uninstall and reinstall xserver-xorg-input-wacom?
Thanks again! :)
Alleykat

---

### Post by intruderukr on 2012-05-01
I have the latest version of xserver-xorg-input-wacom installed: 1:0 14.0-0ubuntu2...

---

### Post by Favux on 2012-05-01
Looks like the PPA did nothing as that is the default.  You could reinstall it if you wanted.  Sometimes the install gets corrupted.

Are you implementing any xsetwacom scripts?

Let's see what querying the pad tells us:
```
xinput list-props "Wacom Graphire4 4x5 pad"
```
And let's check what the scroll wheel is set to:
```
xsetwacom get "Wacom Intuos4 4x5 pad" AbsWheelDown

xsetwacom get "Wacom Intuos4 4x5 pad" AbsWheelUp
```

---

### Post by intruderukr on 2012-05-01
ok, here's the results of those tests...
```
:~$ xinput list "Wacom Graphire4 4x5 pad"
Wacom Graphire4 4x5 pad                 	id=15	[slave  pointer  (2)]
	Reporting 8 classes:
		Class originated from: 15. Type: XIButtonClass
		Buttons supported: 7
		Button labels: None None None None None None None
		Button state:
		Class originated from: 15. Type: XIKeyClass
		Keycodes supported: 248
		Class originated from: 15. Type: XIValuatorClass
		Detail for Valuator 0:
		  Label: Abs X
		  Range: 0.000000 - 0.000000
		  Resolution: 0 units/m
		  Mode: absolute
		  Current value: 0.000000
		Class originated from: 15. Type: XIValuatorClass
		Detail for Valuator 1:
		  Label: Abs Y
		  Range: 0.000000 - 0.000000
		  Resolution: 0 units/m
		  Mode: absolute
		  Current value: 0.000000
		Class originated from: 15. Type: XIValuatorClass
		Detail for Valuator 2:
		  Label: None
		  Range: 0.000000 - 1.000000
		  Resolution: 1 units/m
		  Mode: absolute
		  Current value: 0.000000
		Class originated from: 15. Type: XIValuatorClass
		Detail for Valuator 3:
		  Label: None
		  Range: 0.000000 - 1.000000
		  Resolution: 1 units/m
		  Mode: absolute
		  Current value: 0.000000
		Class originated from: 15. Type: XIValuatorClass
		Detail for Valuator 4:
		  Label: None
		  Range: 0.000000 - 1.000000
		  Resolution: 1 units/m
		  Mode: absolute
		  Current value: 0.000000
		Class originated from: 15. Type: XIValuatorClass
		Detail for Valuator 5:
		  Label: None
		  Range: 0.000000 - 1.000000
		  Resolution: 1 units/m
		  Mode: absolute
		  Current value: 0.000000

```
```
~$ xsetwacom get "Wacom Intuos4 4x5 pad" AbsWheelUp
Cannot find device 'Wacom Intuos4 4x5 pad'.
MXC061:~$ xsetwacom get "Wacom Intuos4 4x5 pad" AbsWheelDown
Cannot find device 'Wacom Intuos4 4x5 pad'.

```
of course my pad is Graphire4...lets see...

```
$ xsetwacom get "Wacom Graphire4 4x5 pad" AbsWheelUp
button +90 -90 
MXC061:~$ xsetwacom get "Wacom Graphire4 4x5 pad" AbsWheelDown
button +91 -91 

```
maybe something will work here?

---

### Post by Favux on 2012-05-01
What happens with the scroll wheel if you enter into a terminal?
```
xsetwacom set "Wacom Graphire4 4x5 pad" AbsWheelDown "key shift plus"

xsetwacom set "Wacom Graphire4 4x5 pad" AbsWheelUp" key minus"

```

---

### Post by intruderukr on 2012-05-02
Good morning, here's what happens:
```
:~$ xsetwacom set "Wacom Graphire4 4x5 pad" AbsWheelDown "key shift plus"

```
```
~$ xsetwacom set "Wacom Graphire4 4x5 pad" AbsWheelUp" key minus"
Unknown parameter name 'AbsWheelUp key minus'.

```

There is no still no scroll.

---

### Post by Favux on 2012-05-02
Oh, sorry that is for zoom.  Did you test in an app. that has zoom?  I was testing the scroll wheel in response to your:
> maybe something will work here?

Also sorry for the typo:
```
xsetwacom set "Wacom Graphire4 4x5 pad" AbsWheelUp "key minus"
```
Also if you have a European keyboard it is "key plus".

For scroll try "key Prior" and "key Next".

---

### Post by intruderukr on 2012-05-02
```
MXC061:~$ xsetwacom set "Wacom Graphire4 4x5 pad" AbsWheelUp "key plus"
-MXC061:~$ xsetwacom set "Wacom Graphire4 4x5 pad" AbsWheelUp "key prior"
Invalid key 'prior'.
Cannot parse keyword 'prior' at position 2
-MXC061:~$ xsetwacom set "Wacom Graphire4 4x5 pad" AbsWheelUp "key next"
Invalid key 'next'.
Cannot parse keyword 'next' at position 2
MXC061:~$ xsetwacom set "Wacom Graphire4 4x5 pad" AbsWheelUp "key minus"

```
with Gimp I can zoom only using the keyboard, with plus or minus.
I used to be able to use scroll in any application, like firefox, I'd scroll down the page as I'd read, but now it simply doesn't respond in any app I've tried it with.

---

### Post by intruderukr on 2012-05-02
just out of interest I tried this:
```
-MXC061:~$ xsetwacom set "Wacom Graphire4 4x5 pad" AbsWheelUp "key up"
-MXC061:~$ xsetwacom set "Wacom Graphire4 4x5 pad" AbsWheelDown "key down"

```
but no reaction from the scroll wheel.

---

### Post by Favux on 2012-05-02
Is it broken?

Do you have another OS you can boot into, say Windows, or a previous Ubuntu release or live CD?  You want to test if the scroll wheel is working and doing this should rule out a hardware issue.

---

### Post by intruderukr on 2012-05-02
I was wondering if it were broken too, and at your suggestion (smart!) I tried it on windows7; scrolls fine in a PDF I was reading, scrolls also in Chrome.

---

### Post by Favux on 2012-05-02
Well shoot, did they break the Graphire again?

You have two pad buttons (Express Keys) right?  Can you assign them?

---

### Post by intruderukr on 2012-05-02
> **Favux said:**
> Well shoot, did they break the Graphire again?

You have two pad buttons (Express Keys) right?  Can you assign them?
Yes, there are 2 buttons, and the scroll bar is inbetween them, but I can't get them to do anything.
I wouldn't really know where to start, but I'm learning a lot with your help.
Thanks for your time.

---

### Post by Favux on 2012-05-02
Let's rule out two xsetwacom binaries.  There should be just one in /usr/bin/xsetwacom,  See if there is another in say /usr/local/bin.  Sometimes when there are two of them from different versions of xf86-input-wacom they can make xetwacom flakey or non-working.  You could also try, after changing directory to root:
```
locate xsetwacom
```

---

### Post by intruderukr on 2012-05-03
Hi Favux, this is what I got:
```
~$ sudo locate xsetwacom

/home/xxx/xf86-input-wacom/man/xsetwacom.man
/home/xxx/xf86-input-wacom/tools/xsetwacom.c
/usr/bin/xsetwacom
/usr/share/man/man1/xsetwacom.1.gz

```

---

### Post by Favux on 2012-05-03
Alright, unless I am missing something obvious (always possible) this is looking like a driver bug.  Either in the kernels wacom.ko or in xf86-input-wacom.

Your bug tracker report on the LWP will get looked at, but you would likely get a much faster response if you posted on [linuxwacom-discuss]("https://lists.sourceforge.net/lists/listinfo/linuxwacom-discuss") mailing list.

The other option is to assume the bug is in xf86-input-wacom and do a bisection of it and see if we can't locate the offending commit.

Right now my memory is hazy on when they fixed the kernel(?) driver for the graphire.  I also seemed to recall a little later Chris(?) wanting to make another change and Jason(?) was worried about how that would affect the Graphire I think.  Don't remember what happened for sure but I think it got left alone.  I'll see if the details will come back to me.

---

### Post by intruderukr on 2012-05-11
Thanks, I'm not sure I know how to submit a bug... I just did one for the printer, like this:
ubuntu-bug cups
how do I do it for wacom?
or how do I do a bisection of xf86-input-wacom?
Thanks

---

### Post by Favux on 2012-05-11
Post on linuxwacom-discuss using the link I gave you.

Details you could post might include the output of the following commands:
lsusb - the line with Wacom in it, that will show your Product ID

Distro and release

kernel and X Server versions - can get those from 'Xorg -version'
xsetwacom -V

xinput list
xsetwacom list

(most of this you already have on this thread)


Then describe your problem with the scroll wheel.  Be sure to mention the scroll wheel works in Win7.

---

### Post by neverama on 2012-08-23
**SUCCESS!!**

This was very helpful. Favux: Thank you a million times for your work. I spent a LOT of time trying to get my Graphire4 scroll to work properly on Precise, if it were not for this forums and human readable info it provide to users, wacom would be an Ubuntu stopper for me. But it was quite a reading...

I know its the due to policy changes, but (dumb me) i didn't **notice the  update on post 1034 in your first link about the patch**, before already  crashing my xserver with a console login, scaring myself a bit,  and  only then wondering if just had to give up...  this is [the relevant page (http://ubuntuforums.org/showthread.php?t=1515562&page=104)]("http://ubuntuforums.org/showthread.php?t=1515562&page=104")... 

It could be worth stressing it out here for future readers: **PATCH THE .TAR  to fix the crashing of your  Xsession on reboot/logout**. If like me, you screwed it, CLI your way in to uninstall the driver to get your X back to norm[COLOR=Black]al by running "[/COLOR][COLOR=Black]sudo make uninstall" in a command-line at the folder where you installed it from[/COLOR]. You will probably want to reinstall your distribution original xserver-xorg-input-wacom package too.

My small grain of sand is this reply with the script to get my Graphire4 up and running properly in Ubuntu Precise 12.04 (64bits but i dont think it will matter in this case) just if anyone finds it helpful... it has the patch in the TAR itself to make life easier but you can grab it from here too... right-click to give execute permissions and run in IN TERMINAL, but it's commented out enough to be worth reading it first... it installs everything in ~/bin [COLOR=SlateGray]*[/COLOR] or at least will give you a hint on where to get the explanations). Credits of course due to the proper authors and no guarantees for it to work. 

[COLOR=SlateGray]..i hate desktop clutter and its easy to CLI your way back in case of error: cd ~/bin/, then cd x+TAB autocompletion, and finally sudo make uninstall and then reboot.[/COLOR]


Hope it helps someone...it fixed mine while we wait for Canonical updates. Thanks again. GO LINUX!

---

### Post by Favux on 2012-08-23
Hi neverama,

Welcome to Ubuntu forums!


Thank you for sharing your solutions and script.  Nice work!  Sorry it was such a pain.  :)

---

### Post by intruderukr on 2012-08-31
Hi, how do I patch the tar? I'd really like to get my wacom scrolling again before teaching starts...
thanks

---

### Post by parazythum on 2012-11-08
First of all big thanks to neverama for sharing the files, there were little typos at the beginning of the .sh file but nothing I couldn't correct.

I have a Graphire4 and could compile the new driver.
But... even if I could get my wheel working, the 2 buttons next to it don't give any answer :(

List of controls for the pad device (just after plugging in the tablet) :
```
xinput list-props "Wacom Graphire4 6x8 pad"
Device 'Wacom Graphire4 6x8 pad':
	Device Enabled (142):	1
	Coordinate Transformation Matrix (144):	1.000000, 0.000000, 0.000000, 0.000000, 1.000000, 0.000000, 0.000000, 0.000000, 1.000000
	Device Accel Profile (267):	0
	Device Accel Constant Deceleration (268):	1.000000
	Device Accel Adaptive Deceleration (269):	1.000000
	Device Accel Velocity Scaling (270):	10.000000
	Device Node (262):	"/dev/input/event13"
	Wacom Rotation (636):	0
	Wacom Serial IDs (638):	22, 0, 15, 0, 0
	Wacom Serial ID binding (639):	0
	Wacom Pressure Threshold (640):	27
	Wacom Sample and Suppress (641):	2, 4
	Wacom Enable Touch (642):	1
	Wacom Enable Touch Gesture (644):	0
	Wacom Touch Gesture Parameters (645):	0, 0, 250
	Wacom Tool Type (372):	"PAD" (370)
	Wacom Button Actions (646):	"None" (0), "None" (0), "None" (0), "None" (0), "None" (0), "None" (0), "None" (0), "None" (0), "None" (0)
        Wacom Strip Buttons (652):	"Button StripLeftUp action" (659), "Button StripLeftDown action" (660), "Button StripRightUp action" (661), "Button StripRightDown action" (662)
	Wacom Wheel Buttons (651):	"Button AbsWheelUp action" (653), "Button AbsWheelDown action" (654), "Button RelWheelUp action" (655), "Button RelWheelDown action" (656), "Button AbsWheel2Up action" (657), "Button AbsWheel2Down action" (658)
	Device Product ID (261):	1386, 22
	Wacom Debug Levels (647):	0, 0
	Button AbsWheelUp action (653):	1572954, 20
	Button AbsWheelDown action (654):	1572955, 20
	Button RelWheelUp action (655):	1572954, 20
	Button RelWheelDown action (656):	1572955, 20
	Button AbsWheel2Up action (657):	1572956, 20
	Button AbsWheel2Down action (658):	1572957, 20
	Button StripLeftUp action (659):	1572958, 20
	Button StripLeftDown action (660):	1572959, 20
	Button StripRightUp action (661):	1572960, 20
	Button StripRightDown action (662):	1572961, 20

```
There aren't any actions associated with the button 1 and button 2. I don't know what are the "strip" buttons.

Even with :
```
#Right button
xsetwacom set "$PAD" Button 2 "key a"
#Left button
xsetwacom set "$PAD" Button 1 "key b"

```
I couldn't associate any keystroke to them. I've tried several combinations but no joy.

Is this another bug in the code (I know how to compile but I'm not fluent in C), or something else missing ?

---

### Post by Favux on 2012-11-08
I think Jason fixed the buttons in 0.16.0 too.

What release of Ubuntu do you have?  What version of xf86-input-wacom?
```
xsetwacom -V
```

---

### Post by parazythum on 2012-11-09
> **Favux said:**
> I think Jason fixed the buttons in 0.16.0 too.

What release of Ubuntu do you have?  What version of xf86-input-wacom?
```
xsetwacom -V
```

Here we go :
```
xsetwacom -V
0.16.0
```

Ubuntu 12.04

---

