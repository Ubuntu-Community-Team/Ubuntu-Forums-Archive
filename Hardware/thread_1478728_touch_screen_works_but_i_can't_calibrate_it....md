---
title: "touch screen works but i can't calibrate it..."
date: 2010-05-10
forum: Hardware
---

### Post by ~dr,j on 2010-05-10
hey everyone~
ok so i posted about one of the few quarks i have now that i've upgraded to lucid from karmic. here's my other main one...

i have an hp pavillion tx2510us. it has a wacom tablet screen and well in karmic the stylus worked but wasn't able to be calibrated.

now that i've upgraded it works with my finger and with my stylus but still i can not calibrate it.

i have installed anything in the repos that sounded like it may help me calibrate it....but no luck. wacomcpl isn't in the repos (and i know many say use that but i tried that in the last 2 editions of ubuntu and never had it recognize my touchscreen)

so does anyone have any ideas on how i can calibrate it? i am fairly comforatable editing files in an editor....so it doesn't have to be a gui way although that would be preferable.

thanks in advanced!
~j

p.s. im running the 64 bit version

---

### Post by Shehab66 on 2010-05-10
I have the same problem and I cant rotation the screen
I have HP HP TouchSmart tx2 1035ee and running the 32 bit version

---

### Post by Shehab66 on 2010-05-10
I have the same problem and I cant rotation the screen
I have HP HP TouchSmart tx2 1035ee and running the 32 bit version

---

### Post by Favux on 2010-05-10
Hi ~drj and Shehab66,

The calibration for a TX2500's stylus is:
```
	Option		"TopX"		"225"
	Option		"TopY"		"225"
	Option		"BottomX"	"26300"
	Option		"BottomY"	"16375"
```
The calibration for a TX2500's touch is:
```
	Option		"TopX"		"200"
	Option		"TopY"		"225"
	Option		"BottomX"	"4000"
	Option		"BottomY"	"3875"
```
The calibration for a TX2z's stylus and touch is:
```
	Option		"TopX"		"0"
	Option		"TopY"		"0"
	Option		"BottomX"	"9600"
	Option		"BottomY"	"7200"
```
You can add that to the 10-wacom.conf, or if that fails to a section in xorg.conf.  I think the wacom driver is suppose to auto-calibrate your device.  Often Xorg.0.log in /var/log has the coordinates when the driver initiates the device.

The [Rotation HOW TO]("http://ubuntuforums.org/showpost.php?p=6274392&postcount=1") has scripts.  Just remember there has been a change in the device name conventions.  Enter 'xinput --list' in a terminal to get the new device name and substitute it in the scripts (with the quotes) where it says stylus or touch, etc.  You can also use the device ID numbers.

---

### Post by ~dr,j on 2010-05-11
favux~
i'll give that a shot and let ya know....sounds promising :-) [i'd try right now but i have a hard learned rule....NO programing after 11pm....i get too tired and make stupid/rookie mistakes and usually wind up haveing to reinstall everything lol]

i appreciate the help man....
~j

---

### Post by ~dr,j on 2010-05-12
favux~
hey there, so i can't find a 10-wacom.conf file. i looked in the log you mentioned and the cordinates are off...so adding the values you said to the xorg file leaves me with one question

would i add them as a new section or under an exsisting section? i would guess i should add them as a new section i just want to make sure before hand :P

thanks
~j

---

### Post by Favux on 2010-05-12
Hi ~drj,

The .conf files are in /usr/lib/X11/xorg.conf.d/.  You'll need to add Wacom sections, because they shouldn't be in xorg.conf right now.  A sample TX2000 xorg.conf is attached to the bottom of the [linuxwacom HOW TO]("http://ubuntuforums.org/showpost.php?p=6546012&postcount=1").  And Section 3 talks a little bit about the 10-wacom.conf.

You probably should have me review your xorg.conf before you try it.  And back up your current working xorg.conf and be prepared to re-install it from the command line.

---

### Post by mitchells00 on 2010-05-12
Favux: Have you got the calibration points for a HP Touchsmart T**_M_**2?

Thanks
Mitchells00

---

### Post by Favux on 2010-05-12
Hi mitchells00,

I think so.  Often Xorg.0.log (in /var/log) will show the coordinates when the driver is initalized.  In the [HP TM2 convertible notebook on Lucid]("http://ohioloco.ubuntuforums.org/showthread.php?p=8867004") thread at [post #35]("http://ohioloco.ubuntuforums.org/showpost.php?p=8948960&postcount=35") I found a Xorg.0.log.  And it showed:
```
(II) XINPUT: Adding extended input device ""Wacom ISDv4 E3"" (type: STYLUS)
(--) "Wacom ISDv4 E3": top X=0 top Y=0 bottom X=26112 bottom Y=16320 resol X=2540 resol Y=2540
```
So with luck those are your values.  You can check your own Xorg.0.log also.

Edit:  Since the thread is in Lucid testing forum it is frozen now.  So no more posts.  Skimming through the thread I saw the Magic Rotation script using hp-wmi.  I didn't realize the TM2 has a switch in the swivel hinge.  I thought I read somewhere it didn't.  If it does you might want to try the Magick Rotation applet.  Just brought out a beta1 for Lucid and it looks like it works fine.  See Section 4 in the [Rotation HOW TO]("http://ubuntuforums.org/showpost.php?p=6274392&postcount=1").

---

### Post by ~dr,j on 2010-05-14
favux~
first off, man your awesome! thank you SO much....you're one of the most helpful guru's i've meet here. i hope as i learn even more i can model your willingness to help. (i've posetd help answers only a few times...i should use the forum more lol)

ok if i did this right, my 10-wacom file should be attached as well as my xorg.conf file.....i have NOT added anything to them yet. 

so when you can look over them and give me advice? i'd assume the 10-wacom file is the better way to do this project (since you mentioned it first lol) and i would also assume i just add to the middle section of the file?

anyhow i hope i attached them right...and thanks again, youre sooo helpful :-)
~j

---

### Post by Favux on 2010-05-14
Hi ~drj,

Thank you for the kind words.  The ".conf" files are the new way to do things, replacing the .fdi files.  Let's see if we can get the stylus calibrated first.

To get touch we probably need at least another match line or another snippet/section.  If that fails we'll just go to the xorg.conf.

---

### Post by ~dr,j on 2010-05-15
favux~
thanks....that worked like a charm for the stylus! so for the touch would i now add the other section in that same heading?
~j

---

### Post by dglnz on 2010-05-16
favux~

I have posted a call for help regarding a effinet Model 1503x touch screen (posting # 1483778).

Under winXP it is an intellitouch 2500S.

had it working under Kubuntu 6.10LTS (but calibration was required) after adding in the code in etc/X11/xorg.conf.

Decided to try it under Lucid-Lynx but with no joy.
have tried following instructions [https://help.ubuntu.com/community/EloTouchScreen](https://help.ubuntu.com/community/EloTouchScreen) and getting nothing.

Like the original poster I don't see any reference to the touch screen in any logs or messages (ie demsg, lshap or lspci).

I thought xorg.conf was depreciated in favour of the files in .../xorg.d directory.

where does the xorg you speak of below reside and how is it made?

I think i could get the touch working like i had in 6.10 if i used a xorg.conf file to store the settings.

advise would be appreciated.

dave. :)

** snipped **
You can add that to the 10-wacom.conf, or if that fails to a section in xorg.conf.  I think the wacom driver is suppose to auto-calibrate your device.  Often Xorg.0.log in /var/log has the coordinates when the driver initiates the device.

The [Rotation HOW TO]("http://ubuntuforums.org/showpost.php?p=6274392&postcount=1") has scripts.  Just remember there has been a change in the device name conventions.  Enter 'xinput --list' in a terminal to get the new device name and substitute it in the scripts (with the quotes) where it says stylus or touch, etc.  You can also use the device ID numbers.[/QUOTE]

---

### Post by Favux on 2010-05-16
Hi ~drj,

Good.  Now the adventure.  We could guess or look at udevadm info for touch.  Let's see if we can use a shortcut and look at the output of:
```
xinput --list
```
in a terminal.

---

### Post by ~dr,j on 2010-05-16
favuv~
ok my friend.....here's what the output from that command says:

[B]jason@jason-ubuntu-laptop:~$ xinput --list
&#9121; Virtual core pointer                    	id=2	[master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer              	id=4	[slave  pointer  (2)]
&#9116;   &#8627; Microsoft Microsoft Notebook Receiver v2.0	id=10	[slave  pointer  (2)]
&#9116;   &#8627; Wacom ISDv4 93 eraser                   	id=12	[slave  pointer  (2)]
&#9116;   &#8627; Wacom ISDv4 93                          	id=13	[slave  pointer  (2)]
&#9116;   &#8627; Wacom ISDv4 93                          	id=14	[slave  pointer  (2)]
&#9116;   &#8627; SynPS/2 Synaptics TouchPad              	id=16	[slave  pointer  (2)]
&#9116;   &#8627; Macintosh mouse button emulation        	id=17	[slave  pointer  (2)]
&#9123; Virtual core keyboard                   	id=3	[master keyboard (2)]
    &#8627; Virtual core XTEST keyboard             	id=5	[slave  keyboard (3)]
    &#8627; Power Button                            	id=6	[slave  keyboard (3)]
    &#8627; Video Bus                               	id=7	[slave  keyboard (3)]
    &#8627; Power Button                            	id=8	[slave  keyboard (3)]
    &#8627; Sleep Button                            	id=9	[slave  keyboard (3)]
    &#8627; HP Webcam                               	id=11	[slave  keyboard (3)]
    &#8627; AT Translated Set 2 keyboard            	id=15	[slave  keyboard (3)]
jason@jason-ubuntu-laptop:~$ [/B]

thanks again for all your help :-) i really appreciate it a lot!
~j

---

### Post by Favux on 2010-05-16
Hi ~drj,

No joy with xinput.  Ok, we could guess that a valid match is touch and come up with something like:
```
	MatchProduct "Wacom|WACOM|touch|TOUCH"
```
or probably better find the event # associated with touch.  We can probably get that from:
```
dmesg | grep [Ww]acom
```
or from the Xorg.0.log in /var/log/.

---

### Post by ~dr,j on 2010-05-17
favux~
ok here's what the command output was:

[B]jason@jason-ubuntu-laptop:~$ dmesg | grep [Ww]acom
[    7.462198] input: Wacom ISDv4 93 as /devices/pci0000:00/0000:00:14.5/usb7/7-2/7-2:1.0/input/input7
[    7.465037] input: Wacom ISDv4 93 as /devices/pci0000:00/0000:00:14.5/usb7/7-2/7-2:1.1/input/input8
[    7.465335] usbcore: registered new interface driver wacom
[    7.465427] wacom: v1.52:USB Wacom tablet driver
jason@jason-ubuntu-laptop:~$ [/B]

hope that helps :P
~j

---

### Post by Favux on 2010-05-18
Hi ~drj,

OK, let's guess that input7 and input8 match up with event7 and event8.  Let's also guess stylus is event7 and touch event8.  It may be the other way around.  But if those guesses are correct then maybe something like?  If not 8 try 7.

---

### Post by ~dr,j on 2010-05-18
favux~
uhm yeah that didn't work. it toasted my x i think as now when i boot it just sits on the 'ubuntu' logo screen....im in windows now and later today or tomorrow i will go into 'recovery mode' and overwrite the new 10wacom file with the last one that u made up for the stylus...after i do that ill let ya know :-)
~j

---

### Post by Favux on 2010-05-18
That is a serious bummer.  I'm going to guess the event number is reversed.  If you used 8 try 7.  I'm a little surprised that was enough to break X.  Maybe we need to specify event number in both snippets?

---

### Post by ~dr,j on 2010-05-21
favux~
hey there man....sorry it took a few days to get back to u. i wound up having to reinstall ubuntu :s i restored the 10-wacom file...but still couldnt boot, so i restored the original xorg.conf file and tried every trick i could think to get X to work again with no luck....

don't worry i still like idolize u bro. lol but get this....well wait i don't htink it was ur file that screwed my system up. i think i maybe have opened and edited the wrong file for something different....

now the wierd thing...so i reinstalled right....got my programs back etc. and i noticed, now it seems to have auto-calibrated [or atleast pretty darn close]

so that means my biggest frustration in this new version seems to be solved....

if for somereason it wierds out...ill come back and grab the file u made [and switch the numbers and stuff]

than k u for all your help! i really really appreciate it :-)
~j

---

