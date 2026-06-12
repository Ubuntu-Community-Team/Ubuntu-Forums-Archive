---
title: "HOWTO: Setup a wizardpen-based tablet!"
date: 2006-08-03
forum: Hardware &amp; Laptops
---

### Post by daller on 2006-08-03
This HOWTO should help you setting up your tablet!

Known vendors: 

* Genius Wizardpen 
* Genius Mousepen 
* Genius 
* iBall 
* QWare 
* UC-LOGIC

Known tablets: (that works with this howto)

* Tablet W4030U
* Tablet WP5540U (lsusb: UC-Logic Technology Corp. Genius MousePen 5x4 Tablet)
* Tablet WP8060U (Genius MousePen 8x6 Tablet) - Genius MousePen 8x6 Tablet
* Tablet PF1209 (lsusb: UC-Logic Technology Corp.) - Genius PenSketch 9x12"

See this howto:

[https://wiki.ubuntu.com/TabletSetupWizardpen](https://wiki.ubuntu.com/TabletSetupWizardpen)

...and if your tablet is not using the wizardpen-driver:

[https://wiki.ubuntu.com/TabletSetup](https://wiki.ubuntu.com/TabletSetup)

---

### Post by stepheny on 2006-08-22
After typing xmkmf I get the following errors.

-desktop:~/Downloads/wizardpen-driver-0.5.0$ xmkmf
imake -DUseInstalled -I/etc/X11/config/cf
<stdin>:1:19: error: stdio.h: No such file or directory
<stdin>:2:19: error: ctype.h: No such file or directory
<stdin>: In function ‘main’:
<stdin>:18: error: ‘NULL’ undeclared (first use in this function)
<stdin>:18: error: (Each undeclared identifier is reported only once
<stdin>:18: error: for each function it appears in.)
<stdin>:45: warning: incompatible implicit declaration of built-in function ‘sscanf’
<stdin>:49: warning: incompatible implicit declaration of built-in function ‘printf’
/usr/bin/xmkmf: line 57: 10980 Aborted                 imake $imake_defines $args

Do you have any idea what is wrong?

---

### Post by daller on 2006-08-22
Your problem is probably that you don't have **libc6-dev** and **gcc** installed.

The howto is NEW - Please reply with ANY problems whatsoever!

BTW: What model is the tablet? (run **lsusb** from console)

---

### Post by stepheny on 2006-08-24
I found out what was wrong with xmkmf. The packet "build-essential" needed to be installed.

---

### Post by daller on 2006-08-24
If it's not a secret, I'm still interested in the tablet's make and model!

Did it all work as it should?

BTW: Build-essential is not a real package! - I simply depends on some other packages!

If you have one of the tablets that is already on the list, I'm also interested in how much you paid for it!

---

### Post by ashyanbhog on 2006-10-06
Hi, I followed [https://wiki.ubuntu.com/TabletSetupWizardpen](https://wiki.ubuntu.com/TabletSetupWizardpen) guide to configure my new iBall tablet that identifies itself as WP8060, 

The guide worked and the pen is detected and works to an extent, 

However, the default setup considers the pen-tip contact with the board as left click and hence tries to window-pick objects on desktop. This is easily rectified in Windows with the vendor provided software that allows button action cutomization.

Is it possible to change the button-actions setup in Linux someplace. In the present state the tablet is pretty much unusable as it draws continuosly in Gimp when the pen is moved across the tablet

---

### Post by ashyanbhog on 2006-10-08
ok, I think I found the way to confiure buttons, 

$ sudo apt-get xinput
(if its not installed already)

$ xinput set-button-map "WizardPen Tablet" 0 1 2 3 4

my tablet is supposed to have 5 buttons, hence the five numbers, can also include no 5 and be in any order ur comfortable with.

---

### Post by daller on 2006-10-08
> **ashyanbhog said:**
> 
$ xinput set-button-map "WizardPen Tablet" 0 1 2 3 4
.

The command seems to have an effect on my pen.

(Now I CAN'T use it properly :D)

How do you manage the buttons after running this command?

---

### Post by ashyanbhog on 2006-10-11
$ xinput list

will give some details of your input devices, including the number of buttons on your pen

you can change the order of buttons and that'll rotate the function between buttons, 

for example in my tablet, the pen tip contact with tablet is configured as  left click by default, and this make the pen almost unusable, at least for me. I need to explicitly set it to 0 (no action)

on my pen, the number vs fuction is something like

0 : No action (only movement)
1 : Left button click  
2 : Middle Button Click
3 : Right Button click
4 : Scroll up (one click equals one step of scroll wheel in my logitech mouse)
5 : Scroll down

I am yet to find time to see what other numbers do, but if you want help documenting them, I can check them out. 

you need to assign some function for all the buttons one ur device, else xinput exits with some error,

The s/w provided on the driver CD for Windows allows one to see the function assigned to each button and choose a diff function from a drop down menu. Unfortunately, there does not seem to be a similar software available for Linux.

If u have been comfortable with the ur setup so far, ur device comes with a saner set of defaults than my cheeeeeep (but good) tablet.

maybe u can update the tutorial to indicate this option to users who may want to change their default button functions.

I have included the xinput command to my rc.local,

[i]XORG_CONF=/etc/X11/xorg.conf
if [ -e /dev/tablet-event ]; then
  sed -ie 's/^\(\s*\)\#\(\s*InputDevice\s\s*\"WizardPen\ Tablet\"\s\s*\"AlwaysCore\"\)\s*$/\1\2/' "$XORG_CONF"
  echo "Udev created /dev/tablet-event, which means that the tablet is present! - Tablet-driver enabled"
  xinput set-button-map "WizardPen Tablet" 0 1 3 4 5
else
  sed -ie 's/\(^\s*InputDevice\s\s*\"WizardPen\ Tablet\"\s\s*\"AlwaysCore\"\)\s*$/\#&/' "$XORG_CONF"
  echo "Udev did NOT create /dev/tablet-event, which means that the tablet is NOT present! - Tablet-driver disabled"
fi

exit 0[/i]

---

### Post by daller on 2006-10-12
Hmm...

Afaict, the setup is only temporary?

I think i'll add a section to the guide about this issue.

Wouldn't it be correct to place the xinput command in the rc.local file? (along with detecting the tablet) - So that the command is run on every startup

[B]EDIT: I just finished reading your post! - It seems that we are thinking the same about the rc.local file... NICE!

It'll pe a part of the guide very soon![/B]

---

### Post by daller on 2006-10-12
> **ashyanbhog said:**
> $ xinput list

will give some details of your input devices, including the number of buttons on your pen

you can change the order of buttons and that'll rotate the function between buttons, 

for example in my tablet, the pen tip contact with tablet is configured as  left click by default, and this make the pen almost unusable, at least for me. I need to explicitly set it to 0 (no action)

on my pen, the number vs fuction is something like

0 : No action (only movement)
1 : Left button click  
2 : Middle Button Click
3 : Right Button click
4 : Scroll up (one click equals one step of scroll wheel in my logitech mouse)
5 : Scroll down

I am yet to find time to see what other numbers do, but if you want help documenting them, I can check them out. 

you need to assign some function for all the buttons one ur device, else xinput exits with some error,



I can see that it has 5 buttons (whatever that is? - I can only identify 3 of them) - Is it maybe pressure combined with buttons?

But how do I know where to put in "1" "2" and "3" etc...?

Is it a matter of guessing, or what?

---

### Post by daller on 2006-10-12
> **ashyanbhog said:**
> Hi, I followed [https://wiki.ubuntu.com/TabletSetupWizardpen](https://wiki.ubuntu.com/TabletSetupWizardpen) guide to configure my new iBall tablet that identifies itself as WP8060, 

You mentioned "iBall" - Is it the **make** or **model**?

The reason I'm asking, is that I'm listing all vendors and models in my guide...

And what is the output from lsusb? (please post the whole line regarding the tablet!)

**WP8060** or **WP8060U** ?

---

### Post by daller on 2006-10-21
Just a "bump" - In case you missed the last mail!

I've been fidling with the xinput stuff, but I haven't managed to figure out how to assign which number (1-5) to which button!

Please respond! - So that I can test it, and add it to the guide.

---

### Post by beefcurry on 2006-12-07
Does this guide work with ALL wizardpen based tablets? because my UC-Logic PF1209-PRO (to be exact a p-active XP-pen 12" tablet) does not work after following all the steps, as always only the MOUSE works and the stylus does not. After looking around for hours i came to see this on a board somewhere

```
Section "InputDevice"
Identifier "stylus"
Driver "mouse"
Option "Protocol" "IMPS/2"
Option "Device" "/dev/input/mouse0"
# Option "Type" "stylus"
Option "Mode" "relative"
# Option "USB" "on"
# Option "Tilt" "on"
# Option "Threshold" "1"
EndSection
```

Apparently they configured the stylus to work as a mouse. Its not perfect as it dosnt have pressure sensitivity but its one way, has anyone confirmed that it works?

---

### Post by daller on 2007-01-03
> **beefcurry said:**
> Does this guide work with ALL wizardpen based tablets? because my UC-Logic PF1209-PRO (to be exact a p-active XP-pen 12" tablet) does not work after following all the steps, as always only the MOUSE works and the stylus does not. After looking around for hours i came to see this on a board somewhere

Apparently they configured the stylus to work as a mouse. Its not perfect as it dosnt have pressure sensitivity but its one way, has anyone confirmed that it works?

I just got a confirmation from a fellow ubuntu user yesterday - about a PF1209 working flawlessly! - Have you got it working yet?

---

### Post by gespertino on 2007-01-03
I'm the lucky guy! :D 

I've used the daller's guide and this xorg.conf section:

Section "InputDevice"
        Identifier          "PenSketch Tablet"
        Driver              "wizardpen"
        Option              "Device"     "/dev/input/event2"
        Option              "SendCoreEvents" "true"
        Option              "TopX"    "0"
        Option              "TopY"    "1553"
        Option              "BottomX"    "32541"
        Option              "BottomY"    "32762"
        Option              "MaxX"    "32541"
        Option              "MaxY"    "32762"
        Option              "Mode"    "Absolute"
EndSection

It worked very well! (pressure sensitivity included)

---

### Post by Arrrgh4life on 2007-05-20
Hi,

I tried this wizardpen method, and am still having problems.  I have a UC Logic WP8060(U).  I think the issue is that I am running a dual monitor set-up, and I can move the cursor between the 2 screens, but it wont reach to all corners.  That seems to be the only issue though.

Anyone know of a fix?

I tried calibrating the work area to match that of the screen ratio, but still no luck.

The InputDevice section from my xorg.conf

```
Section "InputDevice"
        Identifier      "WizardPen Tablet"
        Option          "SendCoreEvents"        "true"
        Driver          "wizardpen"
        Option          "Device"        "/dev/tablet-event"
        Option          "TopX"          "2593"
        Option          "TopY"          "8338"
        Option          "BottomX"       "31528"
        Option          "BottomY"       "24055"
        Option          "MaxX"          "31528"
        Option          "MaxY"          "24055"
EndSection
```

---

### Post by fugative on 2007-05-21
hey here's one for you,

I've got a wintime wp504 tablet but it's an older non-USB type (one plug goes in the ps2 with a piggy back for a mouse the other goes in the little serial plug). still works fine in 'doze. Would it be possible to get it going in edgy (and soon feisty).

cheers

---

### Post by laser310 on 2007-06-02
Hello Daller,

First of all, thank you very much for providing this so detailed instruction! It is really great!

I have just bought a Genius MousePen 8x6 (WP8060U) and tried your HOWTO on Kubuntu 7.04.
The pressure works in GIMP. *However* there is a big trouble:
Once I start to use the pen, GIMP always thinks that the pen is in the canvas area, even it is moved out of the GIMP window, which means I cannot do anything except drawing, until I use the keyboard (Alt-F->quit) to quit GIMP.

I also noticed that the cursor position (X,Y) showing at the bottom of GIMP window are gray digits when the pen moves out of the window area, sometimes even negative. While if I do not use tablet, the position (X,Y) will disappear when moving the cursor out of the window (i.e. the normal behavior).

I have tried on 3 Kubuntu machines, 2 laptops & 1 desktop and got exactly the same results.
InkScape is the same.

I will email you the debug info later.

Thanks again for providing this very nice HOWTO!

- Laser310

---

### Post by deadcabbit on 2007-07-16
Forget Gimp, it does not work for me either, this is not a problem with the tablet or it can't be fixed right now afaik. Try Krita, it works; I had an olda Painter (version four or something) which I tried in wine and pressure detection also worked there...

---

### Post by chewearn on 2007-09-07
I will just like to say thank you to all those who has contributed to this HowTo.

A colleague bought a MousePen 8x6 recently, and I borrowed it to test see if the device will work in Ubuntu.  Needless to say I'm very impressed, and immediately rush out (in the middle of office hour!) to get one as well.

Too bad about the sensitivity problem with GIMP though; well at least it's good enough to draw some funny cartoons.
:lolflag:

---

### Post by yorik on 2007-09-22
Just a small info for who had the same problem as me:

Even after installing/enabling the wizardpen driver, ubuntu still thinks it's a mouse. This is because X uses a device called /dev/input/mice which is a link to ALL mouse-like devices found on your system. The solution there is to replace /dev/input/mice by /dev/input/mouse0 (or mouse1, mouse2, the one your system uses) in xorg.conf. The problem is that from time to time, ubuntu maps your mouse to a different mouse number. So each time you must edit your xorg.conf.

The solution is to create a new udev rule, in the same /etc/udev/rules.d/010_local.rules, which will map your mouse to a new, unique name. So you will use that name instead of mouse0, mouse1, etc.

First you must detect what your mouse product name is:

```
udevinfo -a -p `udevinfo -q path -n /dev/input/mouse1`
```

where mouse1 is your mouse (try to cat all /dev/input/mouse devices until you find yours). This command will give you a list of attributes of your mouse. Find the "{product}" one.

Then, edit your /etc/udev/rules.d/010_local.rules, and, below the wizardpen rule, add this one:

```
BUS=="usb", KERNEL=="mouse*", SYSFS{product}=="PS/2+USB Mouse", NAME="input/%k", SYMLINK+="input/usb-mouse", MODE="0666"
```

where PS/2+USB Mouse is what the udevinfo command gave you as {product}. Now you should have a new name for your mouse. (do /etc/init.dudev restart, and check that the new link has been created). If all is ok, you can change your mouse device in xorg.conf to this new name, and you are done!

---

### Post by Misosaki on 2007-10-04
Hi,

Before going to the problem, I'd just like to say thanks to daller for a great, comprehensive how-to, and to others here who have posted settings that worked for them. 

Got a UC-Logic WP5540U tablet here and the install went well, but it currently acts as a mouse without pressure sensitivity in GIMP (it does not recognise the tablet in Preferences > Extended Input Devices) or Inkscape. I've also tried varying the device path in xorg.conf - /dev/tablet-event, /dev/input/(tablet-event/mouse2/event5) - and restarting X each time with no luck.

```
cat /var/log/Xorg.0.log | grep "wizardpen"
``` gave the following error:

```

(II) LoadModule: "wizardpen"
(II) Loading /usr/lib/xorg/modules/input//wizardpen_drv.so
dlopen: /usr/lib/xorg/modules/input//wizardpen_drv.so: wrong ELF class: ELFCLASS32
(EE) Failed to load /usr/lib/xorg/modules/input//wizardpen_drv.so
(II) UnloadModule: "wizardpen"
(EE) Failed to load module "wizardpen" (loader failed, 7)
(EE) No Input driver matching `wizardpen'

```

Already checked to make sure the .so file is in /usr/lib/xorg/modules/input. Would anyone happen to know what the "wrong ELF class" error means and how one might correct it?

I'm glad the tablet actually works, but pressure sensitivity would be a real plus. Attached is the debug log (includes the xorg.conf settings). 

Thanks!

Edit: Forgot to mention I'm on amd64 Feisty.

[ATTACH]45341[/ATTACH]

---

### Post by daller on 2007-10-04
> **Misosaki said:**
> 
Got a UC-Logic WP5540U tablet here and the install went well, but it currently acts as a mouse without pressure sensitivity in GIMP (it does not recognise the tablet in Preferences > Extended Input Devices) or Inkscape. I've also tried varying the device path in xorg.conf - /dev/tablet-event, /dev/input/(tablet-event/mouse2/event5) - and restarting X each time with no luck.


I've had replies from 50+ people with this issue, or similar... I've tried to debug it, but I'm stuck...
All the mysteries seems to have vanished with the latest beta of Gutsy, though!
I've recommended a couple of folks to upgrade to Gutsy, and that seems to have fixed their issues!

---

### Post by Misosaki on 2007-10-04
> **daller said:**
> I've had replies from 50+ people with this issue, or similar... I've tried to debug it, but I'm stuck...
All the mysteries seems to have vanished with the latest beta of Gutsy, though!
I've recommended a couple of folks to upgrade to Gutsy, and that seems to have fixed their issues!

I'll definitely consider the upgrade. Will post again once I get around to it. Thanks very much! :)

---

### Post by Ninivekha on 2007-10-23
Hi, 

I'm a newbie into linux, and reading your tutorial I think there is something wrong in my Ubuntu 7.10 because I get:
> TABLET DEVICE
OHCI Host Controller
OHCI Host Controller
EHCI Host Controller


Do I need to install something else before following the tutorial?

Thanks!

---

### Post by daller on 2007-10-24
> **Ninivekha said:**
> Hi, 

I'm a newbie into linux, and reading your tutorial I think there is something wrong in my Ubuntu 7.10 because I get:


Do I need to install something else before following the tutorial?

Thanks!

You should just use TABLET DEVICE where I use WP5540U...

TABLET DEVICE is indead the name of you tablet (according to your computer!)

---

### Post by EseNoy on 2007-10-24
Mi tablet its almost working in a Ubuntu Gutsy; the problem is (I'm not really sure) the button mapping.

When I do a click in my desktop, my Compiz cube starts to turn :confused:!!

I have tried some different configurations for the buttons, having the same results. The good part is that tablet works perfectly (only) in GIMP, pressure included... 

Any idea?

---

### Post by Ninivekha on 2007-10-24
Thank you Daller!

The tablet is kind of working... I can get the pressure in GIMP and Inkscape, but they are not working as I had thought they would...

---

### Post by p.herewini on 2007-11-06
Thanks for the tutorial! Got everything working for my "Genius MousePen 8x6" EXCEPT the buttons:

 - Tapping the pen on the tablet does a left-click AND and middle-click at the same time, meaning I cannot open any icons on the desktop as the middle-click must happen slightly earlier and starts the compiz cube-rotate.

 - Pressing either button on the side of the pen does a right-click, opening context menu

I have tried different combinations of:

$ xinput set-button-map "WizardPen Tablet" 0 1 2 3 4

but i don't think it has any affect and I don't know whether you need to restart the computer for this change to take affect? Does anybody know how to successfully configure the buttons (including tapping the pen on the tablet)?

---

### Post by felixleong on 2007-11-09
I'm currently using a Genius MousePen 5x4 Tablet (WP8060U) and I'm also having problems with the button mappings as well. It seemed that the pen tip acts like a left mouse down when pressed and a middle mouse press when released which causes it work in a haphazard manner.

From what I'm able to understand from reading the `xev` execution log, it's confirmed that the pentip press will send both button 1 (left-mouse button pressed) and button 2 (middle button pressed) events. (See attached "tablet_pentip_presses.txt.bz2", which I basically just use the pen tip like normal mouse clicks, i.e. without drag and drop)

Just wondering is there a solution to this problem? Have attached the error log for your reference.

**_[COLOR="Red"][UPDATE][/COLOR]_**
Found a solution for the problem, which is to add a new udev rule for the other mouse to prevent any mouse message conflicts (/dev/input/mice seemed to be a catch-all mouse device). which should look something like this in /etc/udev/rules.d/010_local.rules:
***[COLOR="Red"](***NOTE: Settings may vary, please refer [this forum thread]("http://www.stud.fit.vutbr.cz/~xhorak28/unb/forum.php?req=thread&id=11&nocount=1&page=1") for the full instructions on how to configure udev!!!)[/COLOR]***
```
BUS=="usb", KERNEL=="event*", SYSFS{product}=="Tablet WP*", NAME="input/%k", SYMLINK+="tablet-event", MODE="0666"
KERNEL=="mouse*", SYSFS{dev}=="13:34", NAME="input/%k", SYMLINK="psmouse"
```

Once done, configure /etc/X11/xorg.conf and replace "/dev/input/mice" to "/dev/psmouse". Restart the X server by pressing Ctrl-Alt-Backspace. And once restarted, that should do the trick.

Hope this helps.

*P/S: As for the rocker buttons, the lower one corresponds to button 3 (right-mouse button press) while the top one corresponds to button 2. Despite xinput report it having 5 mouse buttons, I can't seem to trigger the button 4 and 5 events. Guess they didn't really exist?

---

### Post by Alekiel on 2007-11-09
I have a problem: xinput now tells me that WizardPen Tablet device cannot be found, which is weird because it could before. It is in my xorg.conf and stuff, so what am I missing here?

EDIT: DISREGARD THAT. I fixeded it :3. I didn't change the /dev/imput/mice to /dev/psmouse in xorg.conf and now its working fine. Button map, now I must test pressure and such...

Thanks a lot felixleong.

---

### Post by p.herewini on 2007-11-11
Thanks for the reply felixleong. This didn't work for me but as you said I will now have to look into udev and how to configure this. After doing the steps you suggested my touchpad, mouse and tablet all stopped working except for the tablet keys, I just couldn't move the mouse pointer with any device.

Then after making some changes suggested in the forum thread (that you linked to) I got the tablet to move the mouse pointer again although all the tablet buttons (including pen tip) still did middle clicks as well as their intended buttons. Then after a restart with the tablet unplugged, X won't start at all. Un oh.

I think I will just start again from scratch with the tablet tutorial then read up on configuring udev. Now hopefully my texteditor backed-up /etc/udev/rules.d/010_local.rules.... Lucky I have two computers ;-).

---

### Post by Lometari on 2007-11-11
Same thing used to happen to me in Feisty. If you made a backup of xorg.conf then start in safe mode and restore it. But make sure not to lose the modified file. I had 3 files: xorg.conf, xorg.conf.backup and xorg.conf.withTablet. Whenever I wanted to use the tablet I replaced xorg.conf with the tablet file, and before turning off my laptop I would replace it with the backup. It's a bit tiresome but works. BTW what laptop do you have?

I don't know if I'll have to do the same in Gutsy (will find out next time I turn on my laptop)

I've been trying all afternoon and still my WP8060U is not working... I'm having the crazy messed up buttons behaviour. I have to try felixleong's solution.

---

### Post by p.herewini on 2007-11-11
Acer TravelMate 2400

---

### Post by felixleong on 2007-11-12
p.herewini, if the solution that I found was still valid in a three pointer devices setup (i.e. mouse, touchpad and tablet), I would suggest to tinker with the udev rules get the touchpad and tablet to work together first, just to keep things simple. My guess is that probably you'd need 3 udev rules, which one is your touchpad, the other for the tablet and another one as a catch-all for USB or PS/2 mouse. (I didn't have a laptop to test it out so it'd be nice if you're able to get it work and let us know how you did it ;) )

I do have to admit that writing udev rules was quite a tricky task on its own, though. ^-^|||

Does made me wonder whether the driver for Wacom tablet have these kinds of problems or not...

---

### Post by Lometari on 2007-11-12
Heh, I bought a MousePen because I read it had better Linux compatibility... XD

I'll try the udev rules. I had no time for it today. My laptop is a HP nx6325. As soon as I have something working I'll let you know :)

---

### Post by davixu on 2007-11-30
Hello,
I have a  Tablet WP4030U, it should work out
but It doesnt.

I configured the buttons
trying different combinations
but when I assign left click to pressure
IT doesnt click..it pastes anything I've recently wrote using the keyboard....weird 
..someone plz help me..thanks

---

### Post by mifth on 2007-12-03
Thank you UBUNTU people for your help in wizardpen setting! Thaks a lot! 
My tablet is WP5540U. When I activate a tablet input device in gimp or inkscape preferences, I can draw with my tablet, but can't draw with my mouse. Mouse just does not draw. The same thing was under Mandriva linux. Is it possible to fix? My settings are:

I have downloaded a wizardpen driver from an ubuntu wizardpen tutorial, as my system compiles incorrectly the source.
There is my xorg.log:
(II) LoadModule: "mouse"
(II) Loading /usr/lib/xorg/modules/input//mouse_drv.so
(II) Module mouse: vendor="X.Org Foundation"
	compiled for 1.3.0, module version = 1.2.1
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 0.7
(II) LoadModule: "wizardpen"
(II) Loading /usr/lib/xorg/modules/input//wizardpen_drv.so
(II) Module wizardpen: vendor="The XFree86 Project"
	compiled for 6.8.2, module version = 0.4.1
	Module class: XFree86 XInput Driver
	ABI class: XFree86 XInput driver, version 0.4


There is my xorg.conf:
Section "InputDevice"
        Identifier	"tablet"
        Driver          "wizardpen"
        Option          "Device"        "/dev/tablet-event"
        Option          "TopX"          "0"
        Option          "TopY"          "212"
        Option          "TopZ"          "10"
        Option          "MaxZ"          "1024"
        Option          "BottomX"       "32489"
        Option          "BottomY"       "32745"
        Option          "MaxX"          "32489"
        Option          "MaxY"          "32745"
EndSection


I was trying many types of such things like below, but it didn't help:
xinput set-button-map "tablet" 1 2 3
xinput set-button-map "tablet" 0 1 2 3 4
xinput set-button-map "tablet" 2 3 1
...


There is my "xinput list":
"tablet"        id=2    [XExtensionDevice]
        Num_buttons is 5
        Num_axes is 3
        Mode is Absolute
        Motion_buffer is 0
        Axis 0 :
                Min_value is 0
                Max_value is 32489
                Resolution is 1000
        Axis 1 :
                Min_value is 0
                Max_value is 32533
                Resolution is 1000
        Axis 2 :
                Min_value is 0
                Max_value is 1014
                Resolution is 1000


My "cat /proc/bus/input/devices":
I: Bus=0003 Vendor=5543 Product=0004 Version=0100
N: Name="UC-LOGIC Tablet WP5540U"
P: Phys=usb-0000:00:1d.1-2/input0
S: Sysfs=/class/input/input2
U: Uniq=
H: Handlers=mouse1 event2
B: EV=f
B: KEY=c01 0 3f0001 0 0 0 0 0 0 0 0
B: REL=303
B: ABS=100000f

---

### Post by chewearn on 2007-12-09
hi
I just changed my installation to 64-bit gutsy, but I saw this message on the wiki:
"AMD64 use may cause problems! - Currently the following link doesn't work!"

Any suggestion?  Can I ignore the broken link and still following the installation procedure?

---

### Post by yorik on 2007-12-09
mifth: I have the same problem with tablet & mouse not being able to draw together in gimp, inkscape and any other GTK application. The same thing occurs on windows too, with the same programs. As far as I searched on the net, this is a gtk problem, and it seems that there is no solution at this time...

Astalavista: I installed the whole thing on an AMD64 gusty, and it works fine... If you want, I still have here the driver comiled (and packaged in a .deb :D ) here:
[http://yorik.orgfree.com/archive/wizardpen-driver_0.5.0-1_amd64.deb](http://yorik.orgfree.com/archive/wizardpen-driver_0.5.0-1_amd64.deb)

But this package contains only the compiled .so driver file (it will be installed in the correct dir if you install the deb file), but all the rest (udev rule, calibrating, etc...) you'll still need to do yourself... My knowledge in debian packaging is a bit small to do all that automatically...

---

### Post by chewearn on 2007-12-09
hi yorik
Thanks for the input.  I went ahead and follow the installation, compiled the driver in my machine, and it worked! :)

Problem now is the buttons assignment, which I see a few people in this thread was also facing.  Previously in my 32-bit feisty installation (same PC), this was not a problem.  The buttons behave like a mouse, which is what I wanted.

But now, the pen tip seemed to be both left and middle button clicks at once, etc.  I followed the link to the forum, try to understand what need to be done.
But I soon realized this is not something I could fix in a couple of minutes.
 
At the moment, the pen works in gimp (after configuring the input devices), despite the problem with the buttons, so I'm going to leave it alone.

Thanks again.

---

### Post by chep on 2008-01-06
Hi!, I got a laptop as well and get the messy button problem.

The only way I found to use the tablet as a mouse, with buton working fine is to rename the /input/mice to mouse0 

the touchpad and the tablet works BUT the usb mouses doesnt work anymore

So as I dont need my tablet all time, only when I draw, sometimes Im playing video games rpg like ,) I need a real mouse the touchpad is crap ^^ I found a way like Lometari do but easely

I use a sed command in the rc.local wich automaticaly change mice to mouse0 when the tablet is detected and otherside when not.

Of course it's not a hotplug way....

rc.local

XORG_CONF=/etc/X11/xorg.conf
if [ -e /dev/tablet-event ]; then
  sed -e 's/mice/mouse0/' "$XORG_CONF"
  sed -ie 's/^\(\s*\)\#\(\s*InputDevice\s\s*\"WizardPen\ Tablet\"\s\s*\"AlwaysCore\"\)\s*$/\1\2/' "$XORG_CONF"
  echo "tablet ON, usb mouses disabled"
else
  sed -e 's/mouse0/mice/' "$XORG_CONF"
  sed -ie 's/\(^\s*InputDevice\s\s*\"WizardPen\ Tablet\"\s\s*\"AlwaysCore\"\)\s*$/\#&/' "$XORG_CONF"
  echo "tablet off, usb mouses enabled"
fi
exit 0

So I hope it will work for U

---

### Post by Wehaha on 2008-04-08
Hi!
I've done all i've could to make my Genius Mousepen 8x6 tablet work. And everything went fine during the install of the driver, but i cannot use my pen with tablet only the mouse. When i check if my tablet is connected it says that everything is ok.
I"m running ubuntu 8.04.
Plz help if you can!
Thank in return!

---

### Post by yorik on 2008-04-08
It's hard to tell (and I didn't try 8.04 yet, so I'm not sure it works the same way), but you should check the following things:
1. check that your tablet is appearing as a usb device with the lsusb command
2. if you made that udev rule like explained in this howto, check that the device file was created correctly in /dev directory
3. check that the appropriate stuff is placed in your xorg.conf
4. check that the X driver was loaded correctly (check if it appears somewhere in /var/log/xorg.0.log, and that it didn't issue errors

If all that is ok, then i don't know, but chances are high that some of those 4 points ddn't go right... Read the howto again and make sure you did everything that is explained there...

---

### Post by Wehaha on 2008-04-09
Thanks for the reply
I've failed on the first test:(
everything else seems to be fine. Don't know what information should is post?
Or should i just wait till the new tutorial comes out for hardy?

---

### Post by yorik on 2008-04-09
just type lsusb from the terminal. For example, here is the output of mine:

yorik@aragorn:~$ lsusb
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 003: ID 1267:0201 Logic3 / SpectraVideo plc A4Tech SWOP-3 Mouse
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 003: ID 5543:0004 UC-Logic Technology Corp. Genius MousePen 5x4 Tablet
Bus 001 Device 001: ID 0000:0000

You can see the Genius tablet listed... But if your tablet is not there, then logically step 2 also should fail...

---

### Post by zeronet on 2008-04-09
Xorg 7.3 changes a lot of things on xinput beacuse it has better support for hotpluging, so the Wizardpen Driver 0.5.0.1 won't work anymore, you should use a new one that has been released in the wizardpen driver forums...

[http://iitdchub.com/Wizardpen/wizardpen-0.6.0.2.tar.gz](http://iitdchub.com/Wizardpen/wizardpen-0.6.0.2.tar.gz)

Just uncompress and compile with:

> ./configure --with-xorg-module-dir=/usr/lib/xorg/modules && make && make install

After that, it should be detected automatically, so you should comment the line about the Device in your /etc/X11/xorg.conf :

> Section "InputDevice"
    Identifier     "Wizardpen Tablet"
    Option         "Name"  "UC-LOGIC Tablet WP5540U"
    Driver         "wizardpen"
    Option         "SendCoreEvents" "true"
[COLOR="Red"]  #  Option	   "Device"	"/dev/tablet-event"[/COLOR]
    Option         "TopX" "0"
    Option         "TopY" "0"
    Option         "BottomX" "32739"
    Option         "BottomY" "32745"
    Option         "MaxX" "32739"
    Option         "MaxY" "32745"
EndSection

And this is the discussion about the driver:

[http://www.stud.fit.vutbr.cz/~xhorak28/unb/forum.php?req=thread&id=71&nocount=1&page=7](http://www.stud.fit.vutbr.cz/~xhorak28/unb/forum.php?req=thread&id=71&nocount=1&page=7)

Tested on Ubuntu 8.04 and Slackware 12.1, with Xorg 7.3 and Xserver 1.4, here there is a screenshot:
[http://img206.imageshack.us/img206/2599/slackware132zb4.jpg](http://img206.imageshack.us/img206/2599/slackware132zb4.jpg)


PS: Thanks to Miriad for all the hard work writting the new driver!

---

### Post by buried on 2008-04-09
Wrong area for a how-to but nice how to anyways :)

---

### Post by felixleong on 2008-04-12
For installation in Hardy, I have whipped up a quick HOWTO as I go through getting my Wizardpen to work today:
[http://digitalbluewave.blogspot.com/2008/04/genius-wizardpen-with-hardy-heron-and.html](http://digitalbluewave.blogspot.com/2008/04/genius-wizardpen-with-hardy-heron-and.html)

Do let me know if there's any mistakes.

---

### Post by yorik on 2008-04-18
If I read well on the wizardpen forum, hotplugging is now working with the new driver? Is it true?

---

### Post by PsYhLo on 2008-04-25
can some one attach wizardpen-0.6.0.2.tar.gz because the site doesn't work :( today i bought Genius MousePen 8x6 and i'm with 8.04 pls i want it to work :)

---

### Post by PsYhLo on 2008-04-26
a little bit spaming but please guys help i need that driver to work my mousepen tablet it is new from yesterday attached upload it :)

---

### Post by Orfvz on 2008-04-26
Hi,

like PsYhLo said, the link doesn't work anymore. :(

I installed Hardy, and I really need my tablet for drawing.

Could someone upload the driver ?

---

### Post by PsYhLo on 2008-04-26
look here 
[http://www.stud.fit.vutbr.cz/~xhorak28/unb/forum.php?req=thread&postid=606](http://www.stud.fit.vutbr.cz/~xhorak28/unb/forum.php?req=thread&postid=606)
and i attached to my post :)

---

### Post by dennus on 2008-05-01
I'm kinda new to Ubuntu. I have this WP8060 tablet as well, and after the update to Hardy Heron it doesn't work anymore. So, I downloaded the new 0.6.2 driver. Now, I don't know how to set it up. Can anyone help?

I should add that I did try to install the previous driver just last week, but with no luck. I did it all, calibrated en setting up the conf. So, should I remove the old driver first?

---

### Post by BCtom on 2008-05-03
I'm a little taken back about loosing my tablet after the upgrade to 8.04 because I really use my table a lot. For the day or so I have been working on getting it up and running, but seem to be hitting a roadblock.  The tablet worked wonderfully in the past, and currently, the table is recognized and the mouse that came with the tablet works great, just not the pen. 

Here are my particulars:

sudo vim /etc/X11/xorg.conf

Section "InputDevice"
        Identifier      "WizardPen Tablet"
        Option          "Name"          "UC-LOGIC Tablet WP5540U"
        Option          "SendCoreEvents"        "true"
        Driver          "wizardpen"
        Option          "Device"        "/dev/tablet-event"
        Option          "TopX"          "0"
        Option          "TopY"          "1553"
        Option          "BottomX"       "32541"
        Option          "BottomY"       "32762"
        Option          "MaxX"          "32541"
        Option          "MaxY"          "32762"
EndSection

----and------


Section "ServerLayout"
        Identifier      "Default Layout"
        Screen          "Default Screen"
        InputDevice     "Generic Keyboard"
        InputDevice     "Configured Mouse"  "CorePointer"
        InputDevice     "stylus"        "SendCoreEvents"
        InputDevice     "cursor"        "SendCoreEvents"
        InputDevice     "eraser"        "SendCoreEvents"
        InputDevice     "WizardPen Tablet"  "SendCoreEvents"
EndSection

----and-----

sudo vim /etc/rc.local

XORG_CONF=/etc/X11/xorg.conf
if [ -e /dev/tablet-event ]; then
  sed -ie 's/^\(\s*\)\#\(\s*InputDevice\s\s*\"WizardPen\ Tablet\"\s\s*\"AlwaysCore\"\)\s*$/\1\2/' "$XORG_CONF"
  echo "Udev created /dev/tablet-event = Tablet present! - Tablet-driver enabled"
else
  sed -ie 's/\(^\s*InputDevice\s\s*\"WizardPen\ Tablet\"\s\s*\"AlwaysCore\"\)\s*$/\#&/' "$XORG_CONF"
@                                                                               
"/etc/rc.local" 23L, 766C


I think it matches what it list both here from the [Ditigital Blue Wave]("http://digitalbluewave.blogspot.com/2008/04/genius-wizardpen-with-hardy-heron-and.html") web site that has the upgrade fix for my WP8060U Graphics Tablet, but here is the problem. I can't compile the wizard pen file. I have tried copying the  wizardpen_drv.so, that did not work. 

Then I noticed that in option 2, there is a second file that sits in the  [FONT=monospace]/usr/lib/xorg/modules/input/  called: [/FONT]wizardpen.la along with the wizardpen.so file.

So I tried to install the wizardpen-0.6.0.2.tar.gz file from source to get the two file, but everytime, and this was after installing the required files, I get this error:

sudo ./configure --with-xorg-module-dir=/usr/lib/xorg/modules && make && make install

.......
test -z "/usr/lib/xorg/modules/input" || /bin/mkdir -p "/usr/lib/xorg/modules/input"
 /bin/bash ../libtool --mode=install /usr/bin/install -c  'wizardpen_drv.la' '/usr/lib/xorg/modules/input/wizardpen_drv.la'
/usr/bin/install -c .libs/wizardpen_drv.so /usr/lib/xorg/modules/input/wizardpen_drv.so
/usr/bin/install: cannot remove `/usr/lib/xorg/modules/input/wizardpen_drv.so': Permission denied
make[2]: *** [install-wizardpen_drv_laLTLIBRARIES] Error 1
make[2]: Leaving directory `/home/tom/Desktop/wizardpen-0.6.0.2/src'
make[1]: *** [install-am] Error 2
make[1]: Leaving directory `/home/tom/Desktop/wizardpen-0.6.0.2/src'
make: *** [install-recursive] Error 1


Why is my permission denied? Does one need to be in root to do the actull install? Any thoughts would be welcomed.

Thanks.

---

### Post by yorik on 2008-05-03
I'm not sure about your particular case, but sometimes sudo is not the same as being root.. try to become root first (sudo su), then issue the configure & make commands.

Also, it seems that only the last step of the build process failed (the install part, = copying the .so file to its final location). So, if you search into your wizardpen-0.6.0.2/src dir, you'll find the .so file, and you can manually copy it to /usr/lib/xorg/modules/input/

Actually it looks like the installer couldn't remove an old wizardpen_drv.so... Maybe you can simply remove it manually, and then with a bit of luck everything would work normally...

---

### Post by BCtom on 2008-05-03
> **yorik said:**
> I'm not sure about your particular case, but sometimes sudo is not the same as being root.. try to become root first (sudo su), then issue the configure & make commands.

Also, it seems that only the last step of the build process failed (the install part, = copying the .so file to its final location). So, if you search into your wizardpen-0.6.0.2/src dir, you'll find the .so file, and you can manually copy it to /usr/lib/xorg/modules/input/

Actually it looks like the installer couldn't remove an old wizardpen_drv.so... Maybe you can simply remove it manually, and then with a bit of luck everything would work normally...

Thanks for the quick reply!

I just did a bunch of clean-up. There were some bad text in my xorg.config file, but I think I got everything figured out there.  But in the end this is the error report I finally have after compiling in root, which by way your sugestion worked like a charm.

Calling up:

cat /var/log/Xorg.0.log | grep "wizardpen"

(II) LoadModule: "wizardpen"
(II) Loading /usr/lib/xorg/modules//wizardpen_drv.so
dlopen: /usr/lib/xorg/modules//wizardpen_drv.so: undefined symbol: xf86IsCorePointer
(EE) Failed to load /usr/lib/xorg/modules//wizardpen_drv.so
(II) UnloadModule: "wizardpen"
(EE) Failed to load module "wizardpen" (loader failed, 7)
(EE) No Input driver matching `wizardpen'


Now, I have done both compiled and replaced the wizardpen_drv.os file, and I am still getting this error?

I must be missing somthing....?

---

### Post by yorik on 2008-05-03
Hmm really I don't know... I'm still on gutsy, I have a project to finish before upgrading, so I couldn't test the new driver on hardy yet...

Most certainly, some library is missing... by searching google for xf86IsCorePointer it looks like it is part of xinput... you sure xinput is installed?

---

### Post by BCtom on 2008-05-04
> **yorik said:**
> Most certainly, some library is missing... by searching google for xf86IsCorePointer it looks like it is part of xinput... you sure xinput is installed?

Yes, there is an issue with me compiling the wizard-pen driver on my desk-top. I reinstalled all of the files listed below, and ran the configure/make/install of the wizard-pen upgrade file again without any luck. Same results as before. There must be something missing? This list I got from the [Digital Blue Wave]("http://digitalbluewave.blogspot.com/2008/04/genius-wizardpen-with-hardy-heron-and.html") web site. It seems everyone there has compiled it successfully.

[FONT=monospace]xutils
libx11-dev
libxext-dev
x-dev 
build-essential 
xautomation
xinput
xserver-xorg-dev[/FONT]

Thanks yorik. If you think there is something missing from this list, I'll try anything at this point?

---

### Post by niikaza on 2008-05-07
I have done every thing and my tablet ehich is the WP8060U tablet and every thing works except the cusor moving and and movment.can any one help me out?

---

### Post by aizhiguo on 2008-05-11
I've been wading through this thread but it still isn't clear to me- have we figured out why pressure sensitivity doesn't work in Gimp?

I've had the same problem in both Hardy and Debian Lenny- the tablet (Mousepen 8x6) works fabulously in Inkscape and Krita. But in Gimp, when I configure it the same way I have it configured in Inkscape (mode: screen), I get weird behavior. Pressing down causes the pointer to freeze and no actual drawing occurs. If I just use the tablet as a mouse (mode: disabled), no troubles. Is their input controller configuration that needs to be done? Is it Gimp's problem? What's going on here?

---

### Post by swilwerth on 2008-05-22
Hi,

I have the same problem with pressure sensitivity on Gimp and Hardy Heron.
I'm a linux user since 1999 (not debian or ubuntu, I'd installed ubuntu recently) and I had weird problems with linux, but ... very few like this.

The mouse also (not the mouse on the table, the other mouse), doesn't work on gimp, but if you restart the program, maybe work, maybe not, it's the craziest thing ever.

The pen, if you press the pen tip over the Gimp's toolbar, sometimes acts like third mouse button, sometimes NOT.

I tried to erase the .gimp-xxx directory from my home, to restart with a fresh Gimp configuration, then reconfigure and restart gimp, and doesn't work.

Inkscape works well with no problems on pressure sensitivity.

I think that is a problem with Gimp and the new Xorg or something similar because on Gutsy Gibbon and the wizardpen driver 0.5 the Gimp works well.

Also, my /etc/X11/xorg.conf, changes between bootings, and undoes my modifications.

Any suggestions?
Thanks.
Sebastian.
[B]
UPDATE:[/B]
The wizardpen 0.6.0.2 driver and gimp shipped with hardy heron works well, the only factor that scrambles the things up is the mouse configuration.
If you comment the line on your /etc/X11/xorg.conf 

#       Inputdevice     "Configured Mouse"

Everything works fine, also the mouse.
I think that's a problem with the mouse driver, on some posts that other users writes, I found that the mouse doesn't be pointed to /dev/input/mice.

Greetings
Sebastian.

---

### Post by toppknott on 2008-06-13
Hi all,

I'm using my Genius Mousepen 8x6 successfully in 8.04 thanks to a post I found on this forum: [http://www.stud.fit.vutbr.cz/~xhorak28/unb/forum.php?req=thread&postid=773](http://www.stud.fit.vutbr.cz/~xhorak28/unb/forum.php?req=thread&postid=773)

It says something about udev rules no longer being used, which I don't understand, but the suggested updates to my xorg.conf did the trick. Whoever is maintaining the HOW-TO ought to add that.

I was seriously high after restarting my computer and found my tablet actually working. The incorrectly configured tablet was one of the major reasons I kept going back to using Windows XP. :KS

---

### Post by aizhiguo on 2008-06-13
Awesome- following up on swilwerth's post, I have gotten my tablet working with gimp in Hardy.

The trick is removing or commenting out the "configured mouse." No corepointer needs to be specified; the logs indicate that when no corepointer is specified, X creates one out of thin air, and it does a much better job.

Here are the relevant pieces of my xorg.conf, for a setup with a Logitech MX400 and a Genius Mousepen 8x6. If I were to leave out the MX400-specific stuff I would still have a basic mouse but no extra buttons.

```
#Section "InputDevice"
#	Identifier	"Configured Mouse"
#	Driver		"vmmouse"
#	Option		"CorePointer"
#EndSection

Section "InputDevice"
	Identifier	"WizardPen Tablet"
	Driver		"wizardpen"
	Option		"Name"		"UC-LOGIC Tablet WP8060U"
	Option		"Device"	"/dev/tablet-event"
	Option		"TopX"		"826"
	Option		"TopY"		"2626"
	Option		"BottomX"	"32747"
	Option		"BottomY"	"32762"
	Option		"MaxX"		"32747"
	Option		"MaxY"		"32762"
	Option		"SendCoreEvents"	"true"
EndSection

Section "InputDevice"
	Identifier	"MX400"
	Driver		"evdev"
	Option		"Name"	"Logitech USB-PS/2 Optical Mouse"
	Option		"Device"	  "/dev/mouse-event"
	Option		"HWHEELRelativeAxisButtons" "6 7"
	Option		"Resolution"		    "800"
	Option		"SendCoreEvents"	    "true"
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
  	screen "Default Screen"
#	InputDevice	"Configured Mouse"	"CorePointer"
	InputDevice	"MX400"			"SendCoreEvents"
	InputDevice	"WizardPen Tablet"	"SendCoreEvents"
EndSection

```

I hope this helps somebody. Thanks to everybody who works on this.

---

### Post by maxim_86ualb2 on 2008-06-20
> **BCtom said:**
> Yes, there is an issue with me compiling the wizard-pen driver on my desk-top. I reinstalled all of the files listed below, and ran the configure/make/install of the wizard-pen upgrade file again without any luck. Same results as before. There must be something missing? This list I got from the [Digital Blue Wave]("http://digitalbluewave.blogspot.com/2008/04/genius-wizardpen-with-hardy-heron-and.html") web site. It seems everyone there has compiled it successfully.

[FONT=monospace]xutils
libx11-dev
libxext-dev
x-dev 
build-essential 
xautomation
xinput
xserver-xorg-dev[/FONT]

Thanks yorik. If you think there is something missing from this list, I'll try anything at this point?

I used the precompiled driver from the link you gave.

Just make sure that you delete any other ones in the /usr/lib/xorg/modules/ folder, and follow the advice on the other posts above and it should work.

---

### Post by BCtom on 2008-06-20
> **maxim_86ualb2 said:**
> I used the precompiled driver from the link you gave. Just make sure that you delete any other ones in the /usr/lib/xorg/modules/ folder, and followed the advice on the other posts above and it worked.

OMG---THAT DID IT! I thank you "Hugely" maxim_86ualb2;522897. I never thought of looking for other wizardpen_drv.so files elsewhere, like in /usr/lib/xorg/modules/. Thank you very much for that bit of information. It worked right after I rebooted X.  Yes!

---

### Post by maxim_86ualb2 on 2008-06-21
I am glad that I was able to help. I was filding with it for some time too.

---

### Post by dennus on 2008-06-26
A couple of days later. My PEN is now working, movement is fine... but, the buttons are not. Tipping the pen on the tablet makes it jump a page forward in my web browser. It acts kinda' jumpy, and I really have tried several things to make it work. Can anyone help me out?

---

