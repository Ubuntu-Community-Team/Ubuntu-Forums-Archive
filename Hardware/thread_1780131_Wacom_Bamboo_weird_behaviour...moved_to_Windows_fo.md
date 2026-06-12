---
title: "Wacom Bamboo weird behaviour...moved to Windows for now"
date: 2011-06-11
forum: Hardware
---

### Post by FrostBlue on 2011-06-11
My old bamboo started to behave weirdly suddenly. It registers a click even if my pen is hovering over the tablet and not actually touching. This causes some serious problems for me. The pointer clicks randomly on things , deletes files once in a while ,makes new folder...y'know.
I have moved to windows for now as I don't have any problems over there with the latest Wacom driver. I am working on projects and need to keep moving. 
I love linux , so many things are great , but right now its plain useless to me cuz of this as I only use a tablet , no mouse or touchpad.

I tried on Maverick and Natty with the latest kernel ending in  .38 and also reinstalled Maverick with an old kernel ending in  .22. I also tried installing the latest wacom drivers and utilities from a ppa.

All help appreciated.

---

### Post by Favux on 2011-06-11
Hi FrostBlue,

What release of Ubuntu did you first notice the problem on?  What release are you using now?

What model Bamboo is it?  Should be on the back of the tablet.  Also enter in a terminal *lsusb* for Product ID.  So post the Wacom line.

What is the output of the commands *xinput list* and *xsetwacom list* in a terminal?

---

### Post by FrostBlue on 2011-06-11
Hey Favux , thanks for the reply,
I had the problems showing up on Maverick , I dont think I had updated recently ,but am not sure. I did have backports on.
Then I tried Natty which had the latest kernel and drivers. And now I am running original Maverick , fresh install.

At first I thought it was hardware related , as the eraser at the back seems to work fine. So I tried it on Windows and have seen no problems at all. So it shouldnt be a hardware thing , I think. 

Heres what you asked for,

The model is **MTE-450/K(A)**

lsusb Output :

[COLOR="Indigo"]Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 002: ID 056a:0065 Wacom Co., Ltd Bamboo
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 0a5c:2101 Broadcom Corp. Bluetooth Controller
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub [/COLOR]

xinput list Output :

[COLOR="Indigo"]&#9121; Virtual core pointer                          id=2    [master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer                id=4    [slave  pointer  (2)]
&#9116;   &#8627; Wacom Bamboo eraser                       id=10   [slave  pointer  (2)]
&#9116;   &#8627; Wacom Bamboo cursor                       id=11   [slave  pointer  (2)]
&#9116;   &#8627; Wacom Bamboo pad                          id=12   [slave  pointer  (2)]
&#9116;   &#8627; Wacom Bamboo stylus                       id=13   [slave  pointer  (2)]
&#9116;   &#8627; SynPS/2 Synaptics TouchPad                id=15   [slave  pointer  (2)]
&#9123; Virtual core keyboard                         id=3    [master keyboard (2)]
    &#8627; Virtual core XTEST keyboard               id=5    [slave  keyboard (3)]
    &#8627; Power Button                              id=6    [slave  keyboard (3)]
    &#8627; Video Bus                                 id=7    [slave  keyboard (3)]
    &#8627; Power Button                              id=8    [slave  keyboard (3)]
    &#8627; Sleep Button                              id=9    [slave  keyboard (3)]
    &#8627; AT Translated Set 2 keyboard[/COLOR]  

xsetwacom list Output :

[COLOR="Indigo"]Wacom Bamboo eraser ERASER    
Wacom Bamboo cursor CURSOR    
Wacom Bamboo pad PAD       
Wacom Bamboo stylus STYLUS [/COLOR]

thanks again for looking into this.

---

### Post by FrostBlue on 2011-06-12
Sorry, I was vague about the kernel numbers. They are 2.6.35-22 and 2.3.38-28.

---

### Post by Favux on 2011-06-12
That all looks good, you appear to be on the Wacom X driver.  So the behavior is weird.  What's the output of?:
```
xinput list-props "Wacom Bamboo stylus"
```

Are you doing any configuration beyond the defaults in the wacom.conf in xorg.conf.d or through an xsetwacom script?

---

### Post by FrostBlue on 2011-06-12
No , I havent done any conifguration. I am running a clean , fresh Maverick install and am downloading updates right now.

Heres the Output :


[COLOR="Indigo"]Device 'Wacom Bamboo stylus':
        Device Enabled (121):   1
        Coordinate Transformation Matrix (123): 1.000000, 0.000000, 0.000000, 0.000000, 1.000000, 0.000000, 0.000000, 0.000000, 1.000000
        Device Accel Profile (242):     0
        Device Accel Constant Deceleration (243):       1.000000
        Device Accel Adaptive Deceleration (244):       1.000000
        Device Accel Velocity Scaling (245):    10.000000
        Wacom Tablet Area (251):        0, 0, 14760, 9225
        Wacom Rotation (252):   0
        Wacom Pressurecurve (253):      0, 0, 100, 100
        Wacom Serial IDs (254): 101, 0, 2, 0
        Wacom TwinView Resolution (255):        0, 0, 0, 0
        Wacom Display Options (256):    -1, 0, 1
        Wacom Screen Area (257):        0, 0, 1440, 900
        Wacom Proximity Threshold (258):        42
        Wacom Capacity (259):   -1
        Wacom Pressure Threshold (260): 27
        Wacom Sample and Suppress (261):        2, 4
        Wacom Enable Touch (262):       0
        Wacom Hover Click (263):        1
        Wacom Enable Touch Gesture (264):       0
        Wacom Touch Gesture Parameters (265):   50, 20, 250
        Wacom Tool Type (266):  "STYLUS" (273)
        Wacom Button Actions (267):     "None" (0), "None" (0), "None" (0), "None" (0), "None" (0), "None" (0), "None" (0), "None" (0), "None" (0), "None" (0), "None" (0), "None" (0), "None" (0), "None" (0), "None" (0), "None" (0)


[/COLOR]

---

### Post by FrostBlue on 2011-06-12
That smiley up there is 258 in brackets.


Which driver should I be using. How do I remove this driver and get the new one?

thanks for the quick reply Favux.

---

### Post by Favux on 2011-06-12
You appear to have the correct driver.  It's the xf86-input-wacom driver, which is the Wacom X driver.  With Maverick the default version is 0.10.8.  In Ubuntu it is in the package xserver-xorg-input-wacom which also has xsetwacom.  You should also have xserver-xorg-input-all installed.  Given everything is showing up the Wacom usb kernel driver wacom.ko is also there and working.

You currently have the TPCButton parameter off which is hover mode and the default for a tablet.  Are you used to it on?
```
xsetwacom set "Wacom Bamboo stylus" TPCButton "on"
```
We could also try adjusting the ClickForce up from 27.

We could also get you a newer xf86-input-wacom in case there is some bug with 0.10.8 and the Bamboo MTE-450 I'm not aware of.

---

### Post by FrostBlue on 2011-06-12
EDIT : Have updated the link with the proper one which was at the bottom of the earlier link. Sorry,had too many tabs open and copied the wrong one.

I really dont know whats going on , it was working fine for a long time.
I have tried upgrading the drivers from this guide
[http://www.techytalk.info/2011/03/ubuntu-latest-wacom-tablet-driver-ppa/]("http://www.techytalk.info/2011/03/ubuntu-latest-wacom-tablet-driver-ppa/")

And also tried the command above,
It gave me this

[COLOR="Indigo"]Parameter 'TPCButton' is no longer in use. It was replaced with 'TabletPCButton'.[/COLOR]
 
So I made the changes and rebooted , still no improvement.

How do I change the click force. Also is there a way to disable hover click completely. I will try it to see if it helps.

If nothing works I am afraid I am gonna have to goto the world where every third window says 'not responding' while on the same machine , Kubuntu blazes...he he he...

---

### Post by Favux on 2011-06-12
Hi FrostBlue,

You are confusing me:
> And now I am running original Maverick , fresh install.
That isn't correct because you have the new parameter names for xf86-input-wacom-0.10.11.  They changed from Maverick's default 0.10.8.  So I'm assuming you actually updated the drivers using Irie's PPA.  Is that correct?

Table of parameter name changes:  [http://sourceforge.net/apps/mediawiki/linuxwacom/index.php?title=Xsetwacom#Table_of_New_Parameter_Names](http://sourceforge.net/apps/mediawiki/linuxwacom/index.php?title=Xsetwacom#Table_of_New_Parameter_Names)

So I need to know where you are at.  Maverick with Irie's PPA?  Did you make any changes to the wacom.conf?  If so what?  Are you running any xsetwacom scripts?

---

### Post by FrostBlue on 2011-06-12
Right sorry , I was on a fresh Maverick install when I said so , then I ran a google search and found the link above which directed me to Irie's PPA. So I tried upgrading the driver to see if it helped. 
So far I have tried the following
* fresh Natty install
* fresh Maverick install
And currently am running Maverick with Irie's PPA driver.

All of them had problems. Which led me to think it could be the hardware , but it isn't as it works fine on Windows.

The only change I have made is passing this command :
[COLOR="Indigo"]xsetwacom set "Wacom Bamboo stylus" TabletPCButton "on"[/COLOR]

I am not used to having this ON as I just install my Kubuntu and start working.No altering configs or anything. Although I had a similar problem for a while during kernel update 2.6.35-25 I think sometime back. But it went away after a few updates which were released quickly.

I am sorry if my posts are confusing , I am juggling a few things right now.Have to get in working shape asap.

I can run all the above query commands again , if you want and I will answer any questions that you have. I appreciate you taking time to look into this.

---

### Post by FrostBlue on 2011-06-12
Also I have not made any changes to the wacom.conf and am not running any xsetwacom scripts. Just tried the one command above about TabletPC button.

---

### Post by Favux on 2011-06-12
Sure, I'm working on a project too so I'm also distracted.

If you could quick run the diagnostic commands and make sure everything still looks good.

xsetwacom commands are run-time.  They only apply during a current session.  So when you do:
```
xsetwacom set "Wacom Bamboo stylus" TabletPCButton "on"
```
don't restart.  It should apply right away.

To try ClickForce, its name has changed to.  So let's try a "big" jump, say 3x default:
```
xsetwacom set "Wacom Bamboo stylus" Threshold 81
```
You can keep going up because the limit is 2047.

By the way entering *man xsetwacom* and *man wacom* in a terminal will bring the manuals up for you.

---

### Post by FrostBlue on 2011-06-14
Thanks a lot Favux, that seems to work fine so far. I have moved to Windows,turns out some software I use works better over there.Only for a while tho,KDE and Ubuntu rock...
You have been very prompt in you replies,thanks again buddy :)

---

### Post by FrostBlue on 2011-06-21
Hey man, I have made an edit to one my earlier posts which had a wrong link. 
Heres the link which I used to install the latest drivers
[http://www.techytalk.info/2011/03/ubuntu-latest-wacom-tablet-driver-ppa/]("http://www.techytalk.info/2011/03/ubuntu-latest-wacom-tablet-driver-ppa/")
Peace boss.

---

