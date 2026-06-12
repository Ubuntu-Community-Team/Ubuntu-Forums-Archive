---
title: "Possible regression in Wizardpen driver."
date: 2010-12-14
forum: Hardware
---

### Post by VeeDubb on 2010-12-14
I have a tablet that was purchased from Monoprice, which uses the Wizardpen driver.  I only use it intermittently, so I cannot pin down the failure to any time narrower than the last one to two weeks.

In short, I received the table as a gift on the 5th of November to replace a woefully inadequate graphire tablet.  I tried plug'n'play, and all it would do was cause the cursor to instantly jump to the top left corner of the screen.

After doing some research, I installed the latest driver from the doctormo PPA, and followed configuration directions I found here on the forum, which lead me to generating the following configuration file:

```
#Save this file to /usr/share/X11/xorg.conf.d/70-wizardpen.conf 

Section "InputClass"
   Identifier "wizardpen"
   MatchIsTablet "on"

# Here I hardcoded the event6, please check wich event is yours.
   MatchDevicePath "/dev/input/event5"

# This line is the original one. Removed because my tablet was not matched.
#   MatchVendor "*WALTOP*|*Tablet*"

#[CALIBRATION] This data was taken from wizard-calibrate tool.
	Option		"TopX"		"93"
	Option		"TopY"		"701"
	Option		"BottomX"	"19936"
	Option		"BottomY"	"13165"
#[END CALIBRATION]

   Driver "wizardpen"

EndSection

Section "InputClass"
   Identifier      "wizardpen ignore mouse dev"
   MatchDevicePath "/dev/input/by-id/usb-UC-LOGIC_TWA60-mouse"
   MatchTag        "wizardpen"
   Driver          "mouse"
   Option          "MouseSpeed" "16"
   Option          "ignore"     "true"
	Option		"TopX"		"47"
	Option		"TopY"		"166"
	Option		"BottomX"	"19986"
	Option		"BottomY"	"13165"
EndSection
```

With that config file, it was working absolutely perfectly.  About a week ago (give or take) I installed the MyPaint program (awesome) and played with the tablet and that program for a day or two.  I then tried to demonstrate the program to my fiance after running some updates, and found that it had reverted to it's original behavior.

I have tried all of the following with no results of any kind (positive or negative)

[LIST]
[*]Various restarts of X, the entire VT, and the machine.
[*]Connecting to a different USB port.
[*]purging the driver and reinstalling
[*]copying my config file to every location that I could find any reference to it being stored, including going old school and putting it in xorg.conf.
[*]purging it again, along with the wacom driver and the mypaint program in case of a conflict.
[*]ppapurge-ing my Xorg edgers PPA and repeating all of the above.
[*]Resinstalling edgers and repeating all of the above again.
[/LIST]

No matter what I have done, it continues to behave as though it is not configured at all.  I do know that the table is functioning and not defective because wizardpen-calibrate still returns the normal/sane results I would expect.

I'm wide open to suggestion (Other than go spend $900 on a comparably sized wacom of course)

---

### Post by VeeDubb on 2010-12-15
Just a bump.  I know that wizardpen tablets aren't as popular, but I'm having a hard time imagining nobody else has had this problem.

---

### Post by Favux on 2010-12-15
Hi VeeDubb,

What release of Ubuntu are you in?  Marverick, Lucid, Karmic, etc.

Let's look at your ouput of:
```
xinput --list
```
in a terminal.

Do you remember what the updates were about?  Is there a reason you are using coordinates in the ignore mouse section?  Do you have a tablet mouse?

---

### Post by VeeDubb on 2010-12-15
```
steve@binky-dekstop:~$ xinput --list
&#9121; Virtual core pointer                    	id=2	[master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer              	id=4	[slave  pointer  (2)]
&#9116;   &#8627; Microsoft Microsoft® 2.4GHz Transceiver v6.0	id=9	[slave  pointer  (2)]
&#9116;   &#8627; Microsoft Microsoft® 2.4GHz Transceiver v6.0	id=10	[slave  pointer  (2)]
&#9116;   &#8627; **UC-LOGIC TWA60**                          	id=11	[slave  pointer  (2)]
&#9123; Virtual core keyboard                   	id=3	[master keyboard (2)]
    &#8627; Virtual core XTEST keyboard             	id=5	[slave  keyboard (3)]
    &#8627; Power Button                            	id=6	[slave  keyboard (3)]
    &#8627; Power Button                            	id=7	[slave  keyboard (3)]
    &#8627; Microsoft Microsoft® 2.4GHz Transceiver v6.0	id=8	[slave  keyboard (3)]

```

The bold listing is my tablet.

To be honest, the reason I have the other section set to "ignore" is because somebody posted a working config and I ripped it off.  I kept it set to ignore because I was guessing it was for a mouse, and I only have a stylus.  I use a regular old mouse for mouseing.

The only thing I changed was the resolution, which was the resolution provided by the output of wizardpen-calibrate.  

It's worth pointing out again that this calibration worked perfectly up until a week ago give or take.  I really wish I could pinpoint the updates, but I have a nasty habit of running ```
sudo aptitude update && sudo aptitude -y safe-upgrade
``` and walking away.

Oh, and I'm running Maverick.  Fully up to date of course.

---

### Post by Favux on 2010-12-15
Did you check and make sure there wasn't a WizardPen update?  It may have installed another wizardpen.conf perhaps with another number.  So you could look in /usr/share/X11/xorg.conf.d and make sure.  Do you have the original wizardpen.conf before you modified it.  I'm interested in the match lines.

---

### Post by Favux on 2010-12-15
Anyway I'd like to start with:
```
Section "InputClass"
    Identifier "WizardPen class"
    MatchIsTablet "on"
    MatchVendor "UC-LOGIC|KYE Systems|Ace Cad"
    MatchDevicePath "/dev/input/event*"
    Driver "wizardpen"
EndSection

Section "InputClass"
    Identifier "WizardPen ignore mouse dev class"
    MatchIsTablet "on"
    MatchVendor "UC-LOGIC|KYE Systems|Ace Cad"
    MatchDevicePath "/dev/input/mouse*"
    Option "Ignore" "yes"
EndSection
```
and see if that works for you.  We'll worry about the coordinates later.  So make a back up copy of your current wizardpen.conf and then substitute this one in its place.

---

### Post by VeeDubb on 2010-12-15
> **Favux said:**
> Did you check and make sure there wasn't a WizardPen update?  It may have installed another wizardpen.conf perhaps with another number.  So you could look in /usr/share/X11/xorg.conf.d and make sure.  Do you have the original wizardpen.conf before you modified it.  I'm interested in the match lines.

I'm afraid I don't have the unmodified file anymore.  Once I had verified that mine was working I got rid of it. I did go in and look, and they have not changed the name of the config file.  Mine is still the only one in there.

> **Favux said:**
> Anyway I'd like to start with:
```
Section "InputClass"
    Identifier "WizardPen class"
    MatchIsTablet "on"
    MatchVendor "UC-LOGIC|KYE Systems|Ace Cad"
    MatchDevicePath "/dev/input/event*"
    Driver "wizardpen"
EndSection

Section "InputClass"
    Identifier "WizardPen ignore mouse dev class"
    MatchIsTablet "on"
    MatchVendor "UC-LOGIC|KYE Systems|Ace Cad"
    MatchDevicePath "/dev/input/mouse*"
    Option "Ignore" "yes"
EndSection
```
and see if that works for you.  We'll worry about the coordinates later.  So make a back up copy of your current wizardpen.conf and then substitute this one in its place.

This one works great.  The calibration is a little off, and MyPaint is buggy, but it sounds like you know where to put the calibration in (I hope) and the bugginess with mypaint is a topic for another thread.

When/if you are able to clear up the calibration for me, I'd appreciate it if you could explain where my config went wrong.  I've been using linux as my main OS for most of the last decade, but I think I've gotten soft using Ubuntu where 99% of the hardware I plug in 'just works" and half the windows software does too.

---

### Post by VeeDubb on 2010-12-15
I went ahead and purge the wizardpen package and reinstalled it so I could post up the original config file.  Here it is.

```
Section "InputClass"
   Identifier      "wizardpen"
   MatchIsTablet   "on"
   MatchDevicePath "/dev/input/event*"
   MatchTag        "wizardpen"
   Driver          "wizardpen"
EndSection

Section "InputClass"
   Identifier      "wizardpen ignore mouse dev"
   MatchDevicePath "/dev/input/mouse*"
   MatchTag        "wizardpen"
   Driver          "mouse"
   Option          "MouseSpeed" "16"
   Option          "ignore"     "true"
EndSection
```

---

### Post by Favux on 2010-12-15
OK, good.  I have that somewhere but couldn't find it.  We probably don't need the match tag lines.  Stick with the one I gave you.  Then in the first snippet of the .conf add the coordinates like so:
```
Section "InputClass"
    Identifier "WizardPen class"
    MatchIsTablet "on"
    MatchVendor "UC-LOGIC|KYE Systems|Ace Cad"
    MatchDevicePath "/dev/input/event*"
    Driver "wizardpen"
    Option    "TopX"       "93"
    Option    "TopY"       "701"
    Option    "BottomX"    "19936"
    Option    "BottomY"    "13165"
EndSection
```
My guess is your event specific match line changed.:
```
   MatchDevicePath "/dev/input/event5"
```
That's why you want to use the general match lines and then for dev (device) node use * so it just picks the one the tablet is on since the previous match lines have specified it.

---

### Post by VeeDubb on 2010-12-15
That's really excellent.  It looks like the tablet is properly sorted out now.  Thank you.  Next project is going to be figuring out why MyPaint freaks out every time I touch my mouse instead of the tablet, but that's another thread.

*Edit - Well-documented MyPaint bug, and already fixed in version 0.9 which can be installed from source or an alternate repo.

---

### Post by bingotailspin on 2011-02-06
I just bought a monoprice tablet and want to hook it up to Maverick amd64 workstation.  So from the thread, the answer is this?

[LIST=1]
[*]Uninstall Wizardpen packages
[*]Add PPA (what is the PPA again?) :confused:
[*]Install Wizardpen package from PPA
[*]Use  /usr/share/X11/xorg.conf.d/wizardsomething.conf in #6 + #8?
[/LIST]

Any help would be appreciated as the normal setup in the documents just gives me the *cursor to instantly jump to the top left corner of the screen* behavior.  Alternately, I will downgrade to Lucid.

---

### Post by Favux on 2011-02-06
Hi bingotailspin,

PPA means Personal Package Archive.  Looks like you have it about right.  The pointer going to the upper left corner like that means X isn't getting any input from a driver.

---

### Post by bingotailspin on 2011-02-21
Okay, that worked!  Finally got around to testing it.  :D

Found wizardpen in software center and removed.

Ran this on command line:
```
sudo add-apt-repository ppa:doctormo/xorg-wizardpen
sudo apt-get update
```

Installed wizardpen from software center and ppa.  BTW, the version is the same as the dist version?

Changed the /usr/share/X11/xorg.conf.d/70-wizardpen.conf file:
```
sudo cp -p /usr/share/X11/xorg.conf.d/70-wizardpen.conf /usr/share/X11/xorg.conf.d/70-wizardpen.conf.dist
sudo vi /usr/share/X11/xorg.conf.d/70-wizardpen.conf
```

```
Section "InputClass"
Identifier "WizardPen class"
MatchIsTablet "on"
MatchVendor "UC-LOGIC|KYE Systems|Ace Cad"
MatchDevicePath "/dev/input/event*"
Driver "wizardpen"
Option "TopX" "93"
Option "TopY" "701"
Option "BottomX" "19936"
Option "BottomY" "13165"
EndSection

Section "InputClass"
Identifier "WizardPen ignore mouse dev class"
MatchIsTablet "on"
MatchVendor "UC-LOGIC|KYE Systems|Ace Cad"
MatchDevicePath "/dev/input/mouse*"
Option "Ignore" "yes"
EndSection

```

---

### Post by VeeDubb on 2011-04-29
Thought I'd try here rather than a new thread.


Anyway, I'm now running natty, and it won't work.  I've verified that the .conf file is still being installed to the same place, installed from the PPA by changing adding the ppa as usual, and then changing natty to maverick because there is no natty PPA, but it won't work.

When I try xinput --list I get the following:
```
xinput --list
&#9121; Virtual core pointer                    	id=2	[master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer              	id=4	[slave  pointer  (2)]
&#9116;   &#8627; HID 0a5c:4503                           	id=10	[slave  pointer  (2)]
&#9116;   &#8627; Microsoft Microsoft® 2.4GHz Transceiver v6.0	id=12	[slave  pointer  (2)]
&#9116;   &#8627; Microsoft Microsoft® 2.4GHz Transceiver v6.0	id=13	[slave  pointer  (2)]
&#9123; Virtual core keyboard                   	id=3	[master keyboard (2)]
    &#8627; Virtual core XTEST keyboard             	id=5	[slave  keyboard (3)]
    &#8627; Power Button                            	id=6	[slave  keyboard (3)]
    &#8627; Power Button                            	id=7	[slave  keyboard (3)]
    &#8627; HID 0a5c:4502                           	id=9	[slave  keyboard (3)]
    &#8627; Microsoft Microsoft® 2.4GHz Transceiver v6.0	id=11	[slave  keyboard (3)]

```

As you can see, my tablet doesn't show up at all.  Likewise, when I try to run wizardpen-calibrate, it's unable to find my tablet.  Obviously, that's pretty much a show stopper.

Any clues?

---

