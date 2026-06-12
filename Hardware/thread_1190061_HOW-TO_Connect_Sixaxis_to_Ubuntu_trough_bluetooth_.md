---
title: "HOW-TO: Connect Sixaxis to Ubuntu trough bluetooth mode"
date: 2009-06-17
forum: Hardware
---

### Post by falkTX on 2009-06-17
**Intro:**
After the BlueZ stack was updated to 4.xx, Sixaxis joysticks (from Sony PS3 console) stop working. There's some people on the bluez team working to make it work, but it seems that it could take a while.
So I decided to create a simple GUI that would use some patched 'hidd' that allows to connect Sixaxis to a Linux PC "out-of-the-box".

The app is called 'QtSixA' (It will be in 'Apps' -> 'Utils' -> 'QtSixA'). The GUI is now complete and has been tested to work in 32, 64bit and PowerPC/PS3 computers.



**Installation:**
If you're not running from a PS3 (or any PowerPC machine), add the repo by running this command:
For Ubuntu 9.10 or upwards:
```
sudo add-apt-repository ppa:falk-t-j/qtsixa
```

For Ubuntu Jaunty or Intrepid, add QtSixA PPA to the Software Sources: *(replace UBUNTU_VERSION by "jaunty" or "intrepid")*
```
deb http://ppa.launchpad.net/falk-t-j/qtsixa/ubuntu UBUNTU_VERSION main
```

Then can you install it by opening a terminal and type:
```
sudo apt-get update && sudo apt-get install qtsixa
```
For PS3 users, DEBs can be downloaded here: [https://sourceforge.net/projects/qtsixa/files/](https://sourceforge.net/projects/qtsixa/files/)

If you are _**using Natty (11.04)**_, please check this first:
[http://ubuntuforums.org/showpost.php?p=10953616&postcount=885](http://ubuntuforums.org/showpost.php?p=10953616&postcount=885)


**Screenshot:** (Old)
[http://kde-apps.org/CONTENT/content-pre1/107197-1.jpeg](http://kde-apps.org/CONTENT/content-pre1/107197-1.jpeg)


**Bugs or feature requests:**
Use the links in the QtSixA GUI (menu "Help" -> "Web Links")


**About the Code:**
The GUI is written in PyQt (python-qt4) and uses 'sixad' (written in C++) to connect through bluetooth or a hidraw device. They're both released under the GPL v2 license and you can get the source code here:
[https://sourceforge.net/projects/qtsixa/files/](https://sourceforge.net/projects/qtsixa/files/)



You can check recent posts at page 89

---

### Post by falkTX on 2009-06-18
**Update:**
The main tab on the GUI now displays the connected Sixaxis and curretly set profile.

I've been attempting to set the repo as trusted and I'm close to it. If you note something when updating sources, it's normal;
I think the repo should be trusted before the end of the month

---

### Post by Psyphre on 2009-06-18
Hi, first I want to thank you for your dedicated and hard work.

Ive installed the sixa from your repo and started it. Unfortunately it cannot detect my ps3 controller. 

Its plugged in via usb and all its lights are flashing, yet no detection.
Also tried it unplugged (therefore using bluetooth), still nothing.

---

### Post by falkTX on 2009-06-19
> **Psyphre said:**
> Hi, first I want to thank you for your dedicated and hard work.

Ive installed the sixa from your repo and started it. Unfortunately it cannot detect my ps3 controller. 

Its plugged in via usb and all its lights are flashing, yet no detection.
Also tried it unplugged (therefore using bluetooth), still nothing.

Go to the advanced tab and check "I know what I'm doing" ;)
Try the sixpair setup
(Note: in this setup you'll pair your Sixaxis to the bluetooth stick in USB mode, so please plug the bluetooth stick/device/pen into a USB port as well as the Sixaxis.)
Run that setup and post the sixaxis report at the end

---

### Post by falkTX on 2009-06-19
**Update:**
New version brings control (disconnect only, yet) to the list of connected sixaxis.
Also some minor adjustments to the GUI and setups

---

### Post by falkTX on 2009-06-19
SixA in the KDE-App.org:
[http://www.kde-apps.org/content/show.php/SixA?content=107197](http://www.kde-apps.org/content/show.php/SixA?content=107197)

---

### Post by Psyphre on 2009-06-19
> **falkTX said:**
> Go to the advanced tab and check "I know what I'm doing" ;)
Try the sixpair setup
(Note: in this setup you'll pair your Sixaxis to the bluetooth stick in USB mode, so please plug the bluetooth stick/device/pen into a USB port as well as the Sixaxis.)
Run that setup and post the sixaxis report at the end

Gave that a try but no luck. The report is this:

Current Bluetooth master: 00:09:dd:50:5a:a4
Setting master bd_addr to 00:09:dd:50:5a:a4

Still no sixa controller in the list. :(
The bluetooth usb dongle is in and the ps3 controller is plugged in via usb aswell. I pressed the PS button before pairing.


EDIT!
No wait it works. I didnt realise I had to the advanced mode _then_ do the normal Sixa pairing (without USB) AFTER doing a USB pair. Works brilliant. Great job!

---

### Post by sl1pkn07 on 2009-06-21
not working for me

sl1pkn07@SpinFlo:~/Downloads$ sixa-gui       
Traceback (most recent call last):           
  File "/usr/share/sixa/gui/main.pyw", line 620, in <module>
    SixA = Main_SixA_Window()                               
  File "/usr/share/sixa/gui/main.pyw", line 18, in __init__ 
    uic.loadUi("/usr/share/sixa/gui/main.ui", self)         
  File "/usr/lib/python2.6/dist-packages/PyQt4/uic/__init__.py", line 106, in loadUi
    return loader.DynamicUILoader().loadUi(uifile, baseinstance)                    
  File "/usr/lib/python2.6/dist-packages/PyQt4/uic/Loader/loader.py", line 22, in loadUi
    return self.parse(filename)
  File "/usr/lib/python2.6/dist-packages/PyQt4/uic/uiparser.py", line 690, in parse
    actor(elem)
  File "/usr/lib/python2.6/dist-packages/PyQt4/uic/uiparser.py", line 538, in createUserInterface
    self.traverseWidgetTree(elem)
  File "/usr/lib/python2.6/dist-packages/PyQt4/uic/uiparser.py", line 516, in traverseWidgetTree
    handler(self, child)
  File "/usr/lib/python2.6/dist-packages/PyQt4/uic/uiparser.py", line 163, in createWidget
    self.traverseWidgetTree(elem)
  File "/usr/lib/python2.6/dist-packages/PyQt4/uic/uiparser.py", line 516, in traverseWidgetTree
    handler(self, child)
  File "/usr/lib/python2.6/dist-packages/PyQt4/uic/uiparser.py", line 320, in createLayout
    self.traverseWidgetTree(elem)
  File "/usr/lib/python2.6/dist-packages/PyQt4/uic/uiparser.py", line 516, in traverseWidgetTree
    handler(self, child)
  File "/usr/lib/python2.6/dist-packages/PyQt4/uic/uiparser.py", line 340, in handleItem
    self.traverseWidgetTree(elem)
  File "/usr/lib/python2.6/dist-packages/PyQt4/uic/uiparser.py", line 516, in traverseWidgetTree
    handler(self, child)
  File "/usr/lib/python2.6/dist-packages/PyQt4/uic/uiparser.py", line 320, in createLayout
    self.traverseWidgetTree(elem)
  File "/usr/lib/python2.6/dist-packages/PyQt4/uic/uiparser.py", line 516, in traverseWidgetTree
    handler(self, child)
  File "/usr/lib/python2.6/dist-packages/PyQt4/uic/uiparser.py", line 340, in handleItem
    self.traverseWidgetTree(elem)
  File "/usr/lib/python2.6/dist-packages/PyQt4/uic/uiparser.py", line 516, in traverseWidgetTree
    handler(self, child)
  File "/usr/lib/python2.6/dist-packages/PyQt4/uic/uiparser.py", line 163, in createWidget
    self.traverseWidgetTree(elem)
  File "/usr/lib/python2.6/dist-packages/PyQt4/uic/uiparser.py", line 516, in traverseWidgetTree
    handler(self, child)
  File "/usr/lib/python2.6/dist-packages/PyQt4/uic/uiparser.py", line 167, in createWidget
    widget.setSortingEnabled(self.sorting_enabled)
AttributeError: setSortingEnabled
sl1pkn07@SpinFlo:~/Downloads$

python-qt4 v4.4.4 installed

---

### Post by falkTX on 2009-06-22
> **sl1pkn07 said:**
> not working for me

sl1pkn07@SpinFlo:~/Downloads$ sixa-gui       
Traceback (most recent call last):           
  File "/usr/share/sixa/gui/main.pyw", line 620, in <module>
    SixA = Main_SixA_Window()                               
  ....
  File "/usr/lib/python2.6/dist-packages/PyQt4/uic/uiparser.py", line 167, in createWidget
    widget.setSortingEnabled(self.sorting_enabled)
AttributeError: setSortingEnabled
sl1pkn07@SpinFlo:~/Downloads$

python-qt4 v4.4.4 installed


Seems to be missing the 'UIC' python modules.
Thanks for the report, I'll see what I can do

---

### Post by falkTX on 2009-06-22
**Update:** *(copied from changelog)*
  * On 'list of Sixaxis' the "Info" buttons is now available (when a Sixaxis is connected)
  * New progress bar near the 'list of Sixaxis' shows currently selected Sixaxis' signal quality
  * Auto-uncheck "Use Sixaxis as Mouse/Keyboard" when no profile is set in the system
  * Removed XBMC profile
    [New versions of XBMC have a built-in Sixaxis profile. Using a custom profile just messes around with XBMC]
  * More "Small fixes for small things"

---

### Post by falkTX on 2009-06-22
> **falkTX said:**
> Seems to be missing the 'UIC' python modules.
Thanks for the report, I'll see what I can do

I checked it out. It seems a python-QT4 bug.
The debian guys already fixed, but I'm not sure it will be fixed on Ubuntu soon.

Here's the report from the debian guys:
[http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=523059](http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=523059)


I'll fill out a bug report

---

### Post by dcs3apj on 2009-06-22
> **falkTX said:**
> I checked it out. It seems a python-QT4 bug.
The debian guys already fixed, but I'm not sure it will be fixed on Ubuntu soon.

Here's the report from the debian guys:
[http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=523059](http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=523059)


I'll fill out a bug report

Is there a workaround in the meantime? e.g. Can the source be built against more recent python QT4 bindings in another directory?

cheers,
Alex

---

### Post by falkTX on 2009-06-23
> **dcs3apj said:**
> Is there a workaround in the meantime? e.g. Can the source be built against more recent python QT4 bindings in another directory?

cheers,
Alex

Try installing the packages 'python2.5', 'python2.6' and 'python3.0' to see if that makes any difference

---

### Post by falkTX on 2009-06-23
**Update:**
Is now possible to create your own profiles.

The main program doesn't auto-add custom profile yet; This will be done for v0.3.1.
Right now I will try to make a good icon and fix all the bugs I can find. This will complete the 0.3.0 version, so after that I'll be waiting for suggestions on how to improve SixA.

---

### Post by dcs3apj on 2009-06-23
> **falkTX said:**
> Try installing the packages 'python2.5', 'python2.6' and 'python3.0' to see if that makes any difference

No need. The new version has fixed it. :D

cheers!

---

### Post by kennethadammiller on 2009-06-24
hey, which works better, following the sixaxis gui that you have made or these directions - "https://help.ubuntu.com/community/Sixaxis"?

thanks.

---

### Post by falkTX on 2009-06-24
> **kennethadammiller said:**
> hey, which works better, following the sixaxis gui that you have made or these directions - "https://help.ubuntu.com/community/Sixaxis"?

thanks.

Those directions are for old Ubuntu Hardy (released more than one year ago). And they actually don't work on new Ubuntu versions.
So I recommend using my app.
It works... - isn't that the most important?

---

### Post by Psyphre on 2009-06-24
Ive been using it for about a week and loving it. Good job.

But there is a bug I wanted to mention.

The profiles arent swapable. In order for me to change controller profiles I have to disconnect and restart the pc before the new settings take effect. Would be awesome if I could change profiles on the fly.

---

### Post by falkTX on 2009-06-24
> **Psyphre said:**
> Ive been using it for about a week and loving it. Good job.

But there is a bug I wanted to mention.

The profiles arent swapable. In order for me to change controller profiles I have to disconnect and restart the pc before the new settings take effect. Would be awesome if I could change profiles on the fly.

I don't think that would be possible right now.
The profiles are 'fdi' (xml) files that HAL loads when a device is connected and matches the fdi info file (in the xml tag "match"). Maybe it's possible to unset a specific HAL device and force it's reload, I don't know.
I'll look into it.

EDIT: I haven't noticed the *_restart_*...
I don't know if you wrote it on purpose or not, but I can say restart it's not needed; just disconnect and connect again.

---

### Post by falkTX on 2009-06-26
**Update:** *(Copied from changelog)*
  * Sixaxis connected through USB now appears on the 'list of sixaxis'  [Disconnect button, as not needed, is disabled when a USB Sixaxis is selected]
  * New SixA icon  [Original icon from tango/gnome devs]
  * Updated sixa.desktop file
  * Marked as RC1


Time for bug fixing, so please report any bugs you find

---

### Post by Psyphre on 2009-06-26
> **falkTX said:**
> I don't think that would be possible right now.
The profiles are 'fdi' (xml) files that HAL loads when a device is connected and matches the fdi info file (in the xml tag "match"). Maybe it's possible to unset a specific HAL device and force it's reload, I don't know.
I'll look into it.

EDIT: I haven't noticed the *_restart_*...
I don't know if you wrote it on purpose or not, but I can say restart it's not needed; just disconnect and connect again.

I'll double check that. But im pretty sure I tried disconnecting then reconnecting. It's not a huge issue so no need to make it a priority as I just use 1 profile anyway.

Keep up the great work!

---

### Post by Polk1986 on 2009-06-27
It's working great for me. I was wondering, is there any way to get it to scan for controllers periodically? I am hoping to be able to ditch my keyboard and mouse for my HTPC, but don't want to leave my controller on all the time. Thanks so much for this program; it's awesome!

---

### Post by falkTX on 2009-06-29
> **Polk1986 said:**
> It's working great for me. I was wondering, is there any way to get it to scan for controllers periodically?

I still don't know how to do this in python, I'm still learning.
But one simple thing I could do is a small script that displays an pop-up/notification (like in systray) when something changes about a controller.

*Edit: Only Sixaxis, of course*

---

### Post by falkTX on 2009-06-29
News... (not that much, LOL)

Well, the repo will not be trusted this month; This happens because of some problems with the FTP server (I'm using a free web-hosting service...)

And I'll NOT ask you to donate a thing; I'll just keep this free/poor-but-working service until it sill works.
In the future, when I'll want to add some other packages, I'll move into a paid/good hosting server. Until then, SixA repo will be untrusted

---

### Post by Gliitch on 2009-06-29
Hey Guys, nice work on the  PS3 Bluetooth application, I've been looking for a solution like this for ages, well ever since i upgraded to 9.04.I know this is still in its early stages of development, ive found it to be quite sensitive, with gens,or it may just be my buttons

oh, i did have trouble pairing my pad with bluetooth but using the advanced option works, i found i had to reboot to get it to work again.


But still a great improvement on the old sixaxsis solution. 
I'm using the ps3 pad atm for the mouse, as the program currently kills my mouse(although i read that it would in the other posts) - which is bluetooth. I shall use the pad with other apps ie: PSX and see how that works out...

After having a little play, i think it may well be just gens, but i have to say its a nice touch being able to pick your games out with the pad, absolutely fantastic job :D Keep up the good work ; )* found out why gens was oversensitive, its due to having the mouse and keyboard profile on ^^

EDIT: Solved the mouse killing issue, just have to restore bluetooth, then disconnect- next to refresh, which for some odd reason, still lets me use the pad as well as my mouse. :D But im not complaining SixA works well with PSX and the DS3 which i just got through the mail. ^_^

---

### Post by falkTX on 2009-06-30
**Update:** *(Copied from changelog)*
  * Properly show SixA version (0.3.0-11 or 0.3.0_RC1-11)
  * Updated GUIs to Qt 4.5.2
  * Small changes to 'sixa' [terminal] script

Can someone that has a PowerPC or PlayStation3 report if this is working or not?

---

### Post by scotthew1 on 2009-07-01
hey all, i'm new to this whole linux thing and i've recently just been trying to install ubuntu on my ps3. i'm currently running ubuntu 9.04 under xubuntu. so i would love to be able to use my sixaxis! i tried running your program and the controller does not seem to connect. the "SizA modules started" but it won't recognize my controller under the "list of connected sixaxis." i tried running "sixpair setup" under advanced. again i'm new to this whole os so i may very well be doing something rather stupid. but my efforts so far have not been able to get the controller to work. =[

---

### Post by falkTX on 2009-07-01
> **scotthew1 said:**
> hey all, i'm new to this whole linux thing and i've recently just been trying to install ubuntu on my ps3. i'm currently running ubuntu 9.04 under xubuntu. so i would love to be able to use my sixaxis! i tried running your program and the controller does not seem to connect. the "SizA modules started" but it won't recognize my controller under the "list of connected sixaxis." i tried running "sixpair setup" under advanced. again i'm new to this whole os so i may very well be doing something rather stupid. but my efforts so far have not been able to get the controller to work. =[
First of all, please run 'sixa-gui' on a terminal (apps -> utils -> terminal/console) and post here all it's output (the messages it prints when the program is running).

You'll also need to unpair your Sixaxis from the PS3 to get this to work (not sure how to do this, but somewhere in PS3 main settings/options).

The 'sixpair' thing is not needed when running from a PS3

---

### Post by falkTX on 2009-07-01
I've been working in trying to get the sixaxis to change profiles on the fly (without need to disconnect and connect again); and it doesn't seem to be possible. I could explain piece by piece why it doesn't work, but I just though of a smart solution for this.
When you "Start SixA Modules" it will (in near future) display a check-box that will allow you to use a custom [selected at the moment, but not system-wide] profile for the Sixaxis you'll connect at that point. For the USBs, just change the profile normally before connecting it.

And also... gyro support is coming...

---

### Post by ps3mhome on 2009-07-01
Hi. Thanks for all efforts!

I have a PS3, Dualshock3-Sixaxis (DS3) and Ubuntu 9.04. I am new to Linux and Ubuntu. In addition to the DS3, I have Sony wireless keypad, which I also would like to be able to use in Ubuntu.

Not sure I did the right things, but I proceeded as follows:

1. Executed six-gui from Terminal. 
2. Clicked the "Start SixA" button (maybe the word PC should be removed from the textbox underneath the button, given that PS3 users should go through this step).
3. Pressed the PS button followed by Refresh. An adress appeared 00:21:4F:E4:5E:76. Pressed Finish.
4. The same adress appeared on List of connected Sixaxis".
5. Pressed Input Profiles tab. I want to use the DS3 as a mouse in Ubuntu. Ticked "Use Sixaxis as Mouse/Keyboard". Not sure what profile to select. Tried several, including Fake Joystick, Gnome, KDE, and a few others. Then pressed Apply. Got the respective Layout. Tried to use DS3 on basis of the layouts, but to no avail. Nothing happened to the (mouse) pointer.

6. Pressed the Info button:
"Name: Sony Computer Entertainment Wireless Controller
Adress: 00:21:4F:E4:5E:76
ID: 054C:0268
Signal quality: 251
Status: Connected (through bluetooth (wireless))
 
 
Adresses of the bluetooth devices/sticks/pens used until now:
00:0B:E4:40:E6:A9".

7. Exited Sixa.

8. Copied the following from Terminal:
"ubuntu:~$ six-gui
bash: six-gui: command not found
ro@ubuntu:~$ sixa-gui
 * Stopping bluetooth                                                    [ OK ] 
 * Starting bluetooth                                                    [ OK ] 
SixA modules alreay running
 * Stopping bluetooth                                                    [ OK ] 
hidd[3015]: Bluetooth HID daemonhidd[3015]: New HID device 00:21:4F:E4:5E:76 (Sony Computer Entertainment Wireless Controller)
hidd: no process killedhidd[3015]: Exit
 * Starting bluetooth                                                    [ OK ] 
 * Stopping bluetooth                                                    [ OK ] 
 * Starting bluetooth                                                    [ OK ] 
SixA modules alreay running
 * Stopping bluetooth                                                    [ OK ] 
hidd[4094]: Bluetooth HID daemonhidd[4094]: New HID device 00:21:4F:E4:5E:76 (Sony Computer Entertainment Wireless Controller)
hidd: no process killedhidd[4094]: Exit
 * Starting bluetooth                                                    [ OK ] 
 * Stopping bluetooth                                                    [ OK ] 
 * Starting bluetooth                                                    [ OK ] 
SixA modules alreay running
 * Stopping bluetooth                                                    [ OK ] 
hidd[4716]: Bluetooth HID daemonhidd[4716]: New HID device 00:21:4F:E4:5E:76 (Sony Computer Entertainment Wireless Controller)
hidd: no process killedhidd[4716]: Exit
 * Starting bluetooth                                                    [ OK ] ".

---

### Post by ps3mhome on 2009-07-01
Sorry, in step above 8, I copied info from Terminal corresponding to other actions than described in post above, including that I disconnected and reconnected DS3 for instance. Quite sure you understand this anyway, but the "correct" step 8 should be:

8. "ro@ubuntu:~$ sixa-gui
 * Stopping bluetooth                                                    [ OK ] 
 * Starting bluetooth                                                    [ OK ] 
SixA modules alreay running
 * Stopping bluetooth                                                    [ OK ] 
hidd[3018]: Bluetooth HID daemonhidd[3018]: New HID device 00:21:4F:E4:5E:76 (Sony Computer Entertainment Wireless Controller)
hidd: no process killedhidd[3018]: Exit
 * Starting bluetooth                                                    [ OK ] "

---

### Post by andrewwg94 on 2009-07-02
> **falkTX said:**
> 
Can someone that has a PowerPC or PlayStation3 report if this is working or not?

It does *NOT* work on the ps3. I am running the latest version from your repos on a clean install ubuntu 9.04. there appears to be a problem with the "Connect to PC" wizard. When normal bluetooth is running, I always get the bluetooth icon in the system tray. When the sixaxis bluetooth is running, it always goes away. Well, when i run the wizard, it goes away like normal, but, when i click 'finish' at the end of the wizard, the icon comes back, indicating that normal bluetooth has been restored. I know this because I've used to use sixaxis-gui and it's the same thing on there. It doesn't seem to work with usb either, if that makes a difference. All I did was run the connect to pc wizard and activate the firefox thing on the other tab. Although nice works, the app it self is VERY nice :) i love how you added the visuals to the tab. but again, doesn't work on ps3. Also, may I ask what are you doing with a Sixaxis without a PS3? ;)

---

### Post by falkTX on 2009-07-02
> **ps3mhome said:**
> Not sure I did the right things, but I proceeded as follows:

1. Executed six-gui from Terminal. 
2. Clicked the "Start SixA" button (maybe the word PC should be removed from the textbox underneath the button, given that PS3 users should go through this step).
3. Pressed the PS button followed by Refresh. An adress appeared 00:21:4F:E4:5E:76. Pressed Finish.
4. The same adress appeared on List of connected Sixaxis".
5. Pressed Input Profiles tab. I want to use the DS3 as a mouse in Ubuntu. Ticked "Use Sixaxis as Mouse/Keyboard". Not sure what profile to select. Tried several, including Fake Joystick, Gnome, KDE, and a few others. Then pressed Apply. Got the respective Layout. Tried to use DS3 on basis of the layouts, but to no avail. Nothing happened to the (mouse) pointer.

You did everything right, but just forgot one thing (which is partly my fault).
Please try the new version (0.3.0-RC1-2 or 0.3.0-12); then, after connecting Sixaxis and closed SixA, run on terminal:
**jstest /dev/input/js0**
This will tell you if the Sixaxis is fully working or not.

Thanks for the report

---

### Post by falkTX on 2009-07-02
**Update:** *(0.3.0-falktx12)*
As promised, you can now select a different profile from the one set system-wide, before connecting any Sixaxis in "Start SixA Modules"
(previous selected profile is restored when setup is finished)
Other small fixes as well

---

### Post by falkTX on 2009-07-02
> **andrewwg94 said:**
> It does *NOT* work on the ps3. I am running the latest version from your repos on a clean install ubuntu 9.04. there appears to be a problem with the "Connect to PC" wizard.I don't have a PS3 to test if this fully works or not. That's why I need you guys to reply here. Thank you ;)

> **andrewwg94 said:**
> When normal bluetooth is running, I always get the bluetooth icon in the system tray. When the sixaxis bluetooth is running, it always goes away. Well, when i run the wizard, it goes away like normal, but, when i click 'finish' at the end of the wizard, the icon comes back, indicating that normal bluetooth has been restored. I know this because I've used to use sixaxis-gui and it's the same thing on there.That is normal, cause in order to connect the Sixaxis, the bluetooth needs to be turned off; This causes the gnome-bluetooth icon to disappear (If it wouldn't, that would be the problem)

> **andrewwg94 said:**
> It doesn't seem to work with usb either, if that makes a difference.That's weird... Are you sure you unpaired the joystick from the PS3? (ie, if all lights just blinks instead of only 1 LED on?)

> **andrewwg94 said:**
> All I did was run the connect to pc wizard and activate the firefox thing on the other tab. Although nice works, the app it self is VERY nice :) i love how you added the visuals to the tab. but again, doesn't work on ps3.Profile before connecting... but it's fixed now

> **andrewwg94 said:**
> Also, may I ask what are you doing with a Sixaxis without a PS3? ;)The Sixaxis is my favourite joystick (of all that exists in the world!)
Playing PS1 games with a PS3 wireless gamepad is the best!

---

### Post by falkTX on 2009-07-02
**Update:** *(0.3.0-falktx13)*
I noticed a small bug when starting SixA modules.
So, quick-fix

---

### Post by falkTX on 2009-07-02
**Update:**
Added support for 'lpia' architecture

Not sure who uses it, but since bluez+hidd-patch compiled on it, it doesn't hurt to add support for it

---

### Post by falkTX on 2009-07-03
Good News:

SixA will work on PS3 soon!
But I NEED your help on this...

_If you have a PS3:_
**1.** Load Ubuntu *IN* the PS3
**2.** Open a browser in [http://falktx.xtreemhost.com/](http://falktx.xtreemhost.com/), go inside *outro* folder and download the file *bluez_4.41-special.tar.gz*
**3.** Extract it somewhere
**4.** Open a terminal and change ("cd") to that directory
**5.** Be sure to have the sources repositories enabled in Synaptic (or other package manager)
**6.** Execute this in the terminal (which is "cd" to bluez package):
```
sudo apt-get build-dep bluez
./configure --prefix=/opt/bluez --enable-hidd
make
sudo make install
cp /opt/bluez/bin/hidd $HOME/new-hidd
sudo rm -r /opt/bluez
```
**7.** In your home folder there will be a new file "new-hidd".
Compress it to gz, tar or whatever
**8.** Upload it here in the Ubuntu forums.

Done!
I will then make the necessary arrangements to make SixA fully working on PS3.

See ya soon!

---

### Post by falkTX on 2009-07-03
**Update:** *(copied from changelog)*
  * Clicking on the systray icon now shows/hides main window
  * Display "You are not using an input profile" instead of "... profile is set to 'None'" in main tab


I've been searching in the web for new Sixaxis stuff to apply to my program. Some guy released a patch for the 2.6.28 Linux kernel that would (supposedly) make Sixaxis' gyro to work. I applied the patch and compiled it, but it doesn't work (dammit...).
Also other attempts at Sixaxis special functions (LEDs, battery, etc) don't seem to exist yet (or yet not released);
So, no cool things for now..

---

### Post by sl1pkn07 on 2009-07-04
hi. the program recognized the controller, but no send signal when pulse/move pads/buttons

jstest and jscalibrator not works (recognized controller, but no received signal)

what is the problem? though USB still works  

greetings

---

### Post by Melhisedek on 2009-07-04
Hello there, 
I have a Sixaxis and a DualShock3, and would like to use Sixaxis with emulators. think is I don't have any bluetooth stick or such on my PC. Can I use Sixaxis through USB mode only? I've connected it to PC and followed this guide:

[https://help.ubuntu.com/community/Joystick_lshal_outputs_done](https://help.ubuntu.com/community/Joystick_lshal_outputs_done)
and installed the file at the bottom Dualshock3.fdi

When i connect joystick to the PC I get all lights flashing and ZSNES won't recognize button presses. Is there anything else I need to do? (I rebooted as well) Just want to use it through USB nothing else :)

Thank you for your time!

---

### Post by ps3mhome on 2009-07-04
> **falkTX said:**
> You did everything right, but just forgot one thing (which is partly my fault).
Please try the new version (0.3.0-RC1-2 or 0.3.0-12); then, after connecting Sixaxis and closed SixA, run on terminal:
**jstest /dev/input/js0**
This will tell you if the Sixaxis is fully working or not.

Thanks for the report

When I press different buttons on the DS3, jstest responds; for example, when SELECT is pressed, jstest reports that button 0 is on. There is also a lot of other output relating to Axes. Is this "fully working"?

Given that this is "fully working", how do I actually go about to use the DS3 as mouse in Ubuntu?

---

### Post by ps3mhome on 2009-07-04
> **falkTX said:**
> Good News:

SixA will work on PS3 soon!
But I NEED your help on this...

_If you have a PS3:_
**1.** Load Ubuntu *IN* the PS3
**2.** Open a browser in [http://falktx.xtreemhost.com/](http://falktx.xtreemhost.com/), go inside *outro* folder and download the file *bluez_4.41-special.tar.gz*
**3.** Extract it somewhere
**4.** Open a terminal and change ("cd") to that directory
**5.** Be sure to have the sources repositories enabled in Synaptic (or other package manager)
**6.** Execute this in the terminal (which is "cd" to bluez package):
```
sudo apt-get build-dep bluez
./configure --prefix=/opt/bluez --enable-hidd
make
sudo make install
cp /opt/bluez/bin/hidd $HOME/new-hidd
sudo rm -r /opt/bluez
```**7.** In your home folder there will be a new file "new-hidd".
Compress it to gz, tar or whatever
**8.** Upload it here in the Ubuntu forums.

Done!
I will then make the necessary arrangements to make SixA fully working on PS3.

See ya soon!

tried this. pls find new-hidd.tar.gz attached

---

### Post by falkTX on 2009-07-04
> **Melhisedek said:**
> When i connect joystick to the PC I get all lights flashing and ZSNES won't recognize button presses. Is there anything else I need to do? (I rebooted as well) Just want to use it through USB nothing else :)
You can use the "Fake Joystick" profile that assign normal keyboard keys to the Sixaxis (like up, left keys; see the pic in 'Input Profiles' for a detailed version).
Then on ZSNES, when you press, let's say, Sixaxis' X button, it will act like 'X' on keyboard.
You can use the 'Fake Joystick' for all applications that doesn't seem to work well with Sixaxis.

Just don't forget that you must set the profile _before_ connecting the Sixaxis

---

### Post by falkTX on 2009-07-04
> **sl1pkn07 said:**
> hi. the program recognized the controller, but no send signal when pulse/move pads/buttons

jstest and jscalibrator not works (recognized controller, but no received signal)

what is the problem? though USB still works  

greetings

[I]Please, when reporting stuff, specify the Ubuntu version (or if using other distro) and architecture (32 or 64bit, lpia or PPC).
[/I]

If your Sixaxis works on USB but not bluetooth that can only be for three reasons:
**1.** Running on PPC/PS3 (cause that don't work yet, but it will VERY SOON)
**2.** The Sixaxis is still paired with a PS3 (if you don't have one, skip this)
**3.** You haven't runned "Sixpair" yet (on the 'Advanced' tab)

---

### Post by falkTX on 2009-07-04
> **ps3mhome said:**
> When I press different buttons on the DS3, jstest responds; for example, when SELECT is pressed, jstest reports that button 0 is on. There is also a lot of other output relating to Axes. Is this "fully working"?

Given that this is "fully working", how do I actually go about to use the DS3 as mouse in Ubuntu?

If jstest shows axis moving then that's fully working.

You can use your Sixaxis as mouse/keyboard by activating an input profile in the "Input profile" tab.
Then, the *next time* a Sixaxis is connected, it will work as set in the profile

---

### Post by falkTX on 2009-07-04
**Update:**
I just updated the "bluez-sixa" package for PowerPC. *(bluez-sixa_1.1-falktx2)*

Sixaxis should now works on the PlayStation3!!

Please test and report!

---

### Post by falkTX on 2009-07-05
Another update:

I found a way to check a Sixaxis battery. Once you're Sixaxis is connected through bluetooth, Run this on a terminal:
```
sudo hcidump -R -O ADDR | head -n 5 | tail -n 1 | awk '{printf "Sixaxis battery: "$1"/05\n"}'
```
(ADDR is the address displayed in the 'list of Sixaxis' on SixA)

It will report like this:
```
Sixaxis battery: **NN**/05
```
(NN can be 01-05 depending on battery level, or 'EE' for charging)


The bad thing is, you need admin/root access to run this; and since we don't want to be asked for password to start SixA, this will not be implemented right now. But it's better than nothing

---

### Post by ps3mhome on 2009-07-05
> **falkTX said:**
> **Update:**
I just updated the "bluez-sixa" package for PowerPC. *(bluez-sixa_1.1-falktx2)*

Sixaxis should now works on the PlayStation3!!

Please test and report!

Did this (PS3, Ubtuntu 9.04):

1. Selected Fake Joystick in Input Profiles
2. Connected DS3 successfully
3. Exited SixA

At this stage I expect DS3 to work as a mouse, but nothing happens (to the mouse pointer) when I press the DS3 buttons. 

Then ran jstest successfully. Also redid steps 1-3 but selected Firefox in Input Profiles, and started Firefox to see whether DS3 would work with Firefox - but no.

Sorry if I have missed something obvious (like not having set some option that mouse should be replaced by jostick or so). I'm new to Ubuntu and Linux.

---

### Post by sl1pkn07 on 2009-07-05
Kubuntu 64 bits jaunty + kde4 4.3rc1

is strange, but need make clear bluethoot data and sixpair with usb  ever disconnect/change profile pad. is normal? if not run this steps (clear bluez data -> sixpair) , the software recognize/connect the pad with bluetooth, but not respond move joy/pulse buttons

another question, the analog buttons (triangle, square,cross,circle,L1/2 and R1/2) no works with bluez, but working fine with USB (jscalibrator view sensibility of this buttons with axis)and gyroscope (sixasis)neither works

thanks and sorry my english

---

### Post by falkTX on 2009-07-06
> **ps3mhome said:**
> Did this (PS3, Ubtuntu 9.04):

1. Selected Fake Joystick in Input Profiles
**2. Connected DS3 successfully**
3. Exited SixA

At this stage I expect DS3 to work as a mouse, but nothing happens (to the mouse pointer) when I press the DS3 buttons. 

Then ran jstest successfully. Also redid steps 1-3 but selected Firefox in Input Profiles, and started Firefox to see whether DS3 would work with Firefox - but no.

Sorry if I have missed something obvious (like not having set some option that mouse should be replaced by jostick or so). I'm new to Ubuntu and Linux.

Do this means that Sixaxis now works in PS3? That would be awesome.

I think I know what the profile problem is - It's the DualShock3. I'll explain:
The input profile are fdi/xml files that contains "tags"; Some tags define buttons, some others define the 'driver' to add these new assigned buttons. In the input profile that's a tag 'driver=XXXX' where XXX could be "PlayStation3 Controller", etc. Since the DualShock3 (DS3 and Sixaxis are different!) has a different driver name, this name must also be specified in the input profile fdi file.

The solution is should very simple. *(and is going to be implemented soon)*

*EDIT: a user already mail-me about this*

---

### Post by falkTX on 2009-07-07
**Update:**
I have bad news... and awesome news!!

First, the bad news - we're not going to have an update soon (1-2 weeks)

The awesome news is why - because of new features.


1st feature - Battery report (as you might have seen, there's command for that);
2nd feature - LED support (Yes, this is really possible). I already coded that part, but implemented it in the GUI is the hardest part.
3rd feature - Gyro/Sensors (not sure if this will be possible yet, but I'll do my best).

---

### Post by falkTX on 2009-07-07
**Update:** *(copied from changelog)*
  * Is now possible to know a Sixaxis battery status (but not yet implemented on the GUI)
    [usage:  'sixa battery <sixaxis-adrr>']
  * You can now choose a LED when connecting a Sixaxis (only in terminal, not yet in the GUI)
    [usage:  'sixa --start --led #'] (where # can be 0-10)
  * Modified the fdi input profiles to make sure they are loaded by HAL (NEED TESTING)

Well...
I was thinking of waiting for GUI implementation of battery status and LEDs before releasing an update, but it may be better to let users test it first. So, if you're confortable using the command-line, this update brings 2 new cool stuff for you:
```
sixa battery <sixaxis-adrr>
```Use this to check the battery status of ADRR Sixaxis
```
sixa --start --led #
```This will let you choose a LED (0-10) for the incoming connections. The LED #5 is LED1 + LED4; #6 is LED2 +LED4, etc; #10 is LED1+2+3+4; 0 is all off.

---

### Post by falkTX on 2009-07-09
**Update:** *(Copied from changelog)*
 * Marked as RC2
  * In the 'list of sixaxis':
    - bugfix: different Sixaxis appeared, but in the same line (thanks Pierluigi Vicinanza);
    - improvement: auto-refresh (3sec).
  * Very cool LED animation when connecting a Sixaxis
  [LED changes 1,2,3,4,3,2,1,2... 8 times, before lighting up the selected one]
  * Display a really useful text file when clicking 'View Available Keys' in new profile window
  * New 'SixA Modules Setup' interface (with auto-refresh!)
  * Replaced "Restore Bluetooth" button for "Start Daemon" in main tab, although the daemon is not written yet
  * Official support to LPIA and PowerPC
  * Limit LEDs to 1-7, since Sixaxis doesn't seem to support more than this
  * Added bluez-hcidump as debian dependeds (used for battery check)
  * Completed the Firefox profile
  * Inform user that it's needed to disconnect Sixaxis after apply a profile


This update brings lot of new stuff; so don't forget to report any problems that you make experience.


For the PS3/PowerPC users:
The input profiles not working is under investigation; they will work, I just don't know when.
The PPC version doesn't support LED animation yet. This is because launchpad doesn't build/compile PPC stuff for regular users; I always need to ask a user to compile stuff, so that PPC build is done. Many thanks to Pierluigi Vicinanza for this!


Also another thing...
DualShock3 rumble and various Sixaxis/Dualshock3 connected at the same time can't be officially supported. That's because I just have 1 Sixaxis joystick.
So, if you are a very rich person, maybe you could buy me a DualShock3 (?). I'll then work to make sure rumble/many-sixaxis-at-once work nicely.

See ya soon!

---

### Post by falkTX on 2009-07-13
**Update:**
I'll be completely honest about this:
Holmen started v0.4 of SixA, while the 0.3 is not fully complete yet. This way we'll never come to a common sense.

So, I've come up with a solution - separate Qt-SixA and Gtk-SixA

If you like my little app, you'll be happy to know that I'll create a simple blog for it, and I'll change the repo for something trusted and faster, soon.

Anyone who hates Qt stuff is welcome to try the Holmen's Gtk-SixA that, in my opinion, never worked as needed.


[I]Note: The blog is not yet finished but you can access it right now:
[http://www.falktx.blogspot.com/](http://www.falktx.blogspot.com/)[/I]

---

### Post by falkTX on 2009-07-13
**Update:** *(Copied from Changelog)*
  * Final release
  * Revert old "View available keys" text file (new file is doesn't work)
  * Small fix of the SMPlayer profile
  * Changed name from SixA to Qt-SixA
  * Change Holmen status as former developer
  * Updated links to the new Qt-SixA blog

---

### Post by falkTX on 2009-07-13
**Update:**
PowerPC/PS3 guys does now have the LED animation when connecting a Sixaxis

---

### Post by falkTX on 2009-07-14
**Update:**
The QtSixA blog is up and running. It may not be totally finished yet, but works for now (it should be completed in about 2 weeks).

[http://falktx.blogspot.com/](http://falktx.blogspot.com/)


Updates, bug reports and feature requests should go there;
But, of course, you can still reply here (I am subscribed to this thread)

---

### Post by falkTX on 2009-07-16
**Update:** *(copied from changelog)*
  * Fixed "Report bug" menu action
  * Run QtSixA as root
  [some actions are disabled by now because of this]
  * Half LED animation time
  * All temporary files are now in dir "/tmp/sixa/" instead of just "/tmp/"
  * Battery status check support (only for wireless/bluetooth Sixaxis)
  * Added option to change Qt Theme
  * Don't allow to select "No Sixaxis found" on 'list of Sixaxis'
  * Some other small fixes

Users using Karmic may notice that bluetooth cannot be turned off, so this means my app will NOT work in Karmic at the time. But, as this is an important Ubuntu bug, they should fixed it soon

---

### Post by mikerz343 on 2009-07-16
This looks wonderful. I'm sure I'll use this a lot when I get my new machine :) thanks!

---

### Post by falkTX on 2009-07-17
**Update:** *(Copied from changelog)*
  * New upstream release:
    - Fixed GUI hanging when checking battery
    - Stop "bluetoothd-service-input" before starting modules (it uses the HIDD channel, needed for the connection)
    - 'List of Sixaxis' no longer flashes when auto-updating the list
    - QtSixA Daemon now implemented
    - Added Debian recommends (gksu or kdesudo)

---

### Post by falkTX on 2009-07-18
**Update:** *(Copied from changelog)*
* Fixes for the QtSixA Modules:
    - Load QtSixA modules faster
    - Fixed Sixaxis sometimes been disconnected when starting modules
    - Fixed modules not starting correctly in terminal mode
    - Don't print information in terminal unless some error ocur
  * Removed old bluetooth related conf/script files (no longer necessary)
  * Added "QtSixA Daemon" to applications menu
  * Added desktop menu files (just for compatibility, will not be needed in karmic)


Also, the LEDs now don't stay on the same # for different Sixaxis. When the 1st is set to 1, the next will go to LED 2, then 3, etc.

---

### Post by Gliitch on 2009-07-19
I have tested a Sixaxis and Dual Shock 3, at the same time,they do indeed work.I've noticed that when pressing Ctrl+R, normal bluetooth does not always resume.

---

### Post by falkTX on 2009-07-20
> **Gliitch said:**
> I've noticed that when pressing Ctrl+R, normal bluetooth does not always resume.
Can you be a little more specific? Usually bluetooth should be restored after running the modules.
Or is it just the Ctrl+R combination?

---

### Post by DEagleson on 2009-07-20
Awesome stuff here. :)
Maybe its possible to use my second Dual Shock 3 controller in XBMC on my Asrock Ion 330 box.

---

### Post by falkTX on 2009-07-20
> **DEagleson said:**
> Awesome stuff here. :)
Maybe its possible to use my second Dual Shock 3 controller in XBMC on my Asrock Ion 330 box.

Here:
[https://launchpad.net/~team-xbmc/+archive/ppa](https://launchpad.net/~team-xbmc/+archive/ppa)

Add these packages to the software sources list and install xbmc and xbmc-eventclients-ps3.
That will make XBMC recognize the controller (if connected) and use it has input (like an IR remote).
I'm have no idea what any of the buttons do, but it shouldn't be too hard to find out

Edit: Just remember to DO NOT set any input profile when using XBMC

---

### Post by DEagleson on 2009-07-20
> **falkTX said:**
> Here:
[https://launchpad.net/~team-xbmc/+archive/ppa](https://launchpad.net/~team-xbmc/+archive/ppa)

Add these packages to the software sources list and install xbmc and xbmc-eventclients-ps3.
That will make XBMC recognize the controller (if connected) and use it has input (like an IR remote).
I'm have no idea what any of the buttons do, but it shouldn't be too hard to find out

Edit: Just remember to DO NOT set any input profile when using XBMC

Thanks for the info. :)
Will try it when i get the time.

---

### Post by falkTX on 2009-07-20
**Update:**
  * Faster GUI responsiveness
    - Do not write to files and then read them unless stricly necessary
    - Starting the QtSixA modules/daemon is even faster now
  * Fixed some small issues related to QtSixA modules


The QtSixA modules may not start at first setup (changes to the code to make it faster may had caused this). If this happens to you, when running QtSixA modules, click back/next some times.
I'll fix this soon

---

### Post by falkTX on 2009-07-20
**Accelerometer/Gyro driver**
I've been trying to make the accelerometer/gyro stuff to work...

There are some code out there that makes Sixaxis been detected in bluetooth mode without using hidd (although some of the code is based on it). It creates a /dev/input/jsX device using uinput.

I got access to that code and I started modifying it. I implemented the LED animation, fixed some little bugs and started working on the acc/gyro support. But since I'm not a real "C" code guy (I usually code in python), it's not that easy for me to understand the code.

Anyway, I need you guys to test it out, just to see if it works OK and doesn't crash your desktop or something.

Download it:
[http://falktx.xtreemhost.com/outro/sixaxisd-0.2a.tar.gz](http://falktx.xtreemhost.com/outro/sixaxisd-0.2a.tar.gz)

It's a typical source code package; but this one only requires "make" to get it to work (of course it will also need some dependencies, but since I always install all *-dev packages, I don't know which are needed for this source to compile).

Once 'make' is done, just do - "sudo ./sixaxisd"
That will run the application and wait for Sixaxis joysticks.
(Don't forget to turn off bluetooth first - "sudo /etc/init.d/bluetooth stop")

To close the app, hit Ctrl+C


I'll be waiting for reports!

---

### Post by stingerid4 on 2009-07-20
Greetings, 

Just trying out (X)ubuntu for the first time on my ps3 and it's .. well it's quite slow and crappy but it gets my geek mode on and that's all quite fun.

So I tried your program and I gotta say it's bloody awesome. Sixaxis works perfectly on my ps3. 

Now I also have a ps3 keypad thingie ([linky]("http://www.us.playstation.com/PS3/Accessories/SCPH-98048?ILC-lps&FTTR=PS3_keypad_bottomleft_wirelesskeypaddetailpage")). It connects and the mouse feature of it works perfectly. But the keyboard doesn't do anything. I assume I need some sort of profile or so to bind all the keys on the keyboard to actual keys? .. Just I have no idea how to do that. Any help would be greatly appreciated.

hmm small edit: it does work in the console (ctrl+alt+f1) just not in the graphical interface

---

### Post by falkTX on 2009-07-21
> **stingerid4 said:**
> Greetings, 

Just trying out (X)ubuntu for the first time on my ps3 and it's .. well it's quite slow and crappy but it gets my geek mode on and that's all quite fun.

So I tried your program and I gotta say it's bloody awesome. Sixaxis works perfectly on my ps3. 

Now I also have a ps3 keypad thingie ([linky]("http://www.us.playstation.com/PS3/Accessories/SCPH-98048?ILC-lps&FTTR=PS3_keypad_bottomleft_wirelesskeypaddetailpage")). It connects and the mouse feature of it works perfectly. But the keyboard doesn't do anything. I assume I need some sort of profile or so to bind all the keys on the keyboard to actual keys? .. Just I have no idea how to do that. Any help would be greatly appreciated.

hmm small edit: it does work in the console (ctrl+alt+f1) just not in the graphical interface

I don't have one to try it out, but I think it only needs some input profile (NOT the same as the ones in QtSixA) that will map buttons from the pad to "fake" real buttons.
To be honest, I didn't even knew it has mouse input...


But you can help by doing this:
1. connect it to the USB (without Sixaxis, just the pad) and run "lsusb" from a terminal. Then post the output
2. connect it through bluetooth (how did you do this?) and run "dmesg | tail". Send me the output as well.

That will help

---

### Post by falkTX on 2009-07-21
**Update:** *(Copied from changelog)*
* Really fix problem that made QtSixA modules won't start at first setup time
  * Fixed a small visual bug when disconnecting a Sixaxis

---

### Post by falkTX on 2009-07-21
[SIZE="5"]Accelerometer/Gyro driver is ready! PLEASE TEST![/SIZE]
The driver is now ready!

**To install:**
Just open a package manager (like synaptic) and install the package "sixa-extra-modules" from my repo.

**To Run:**
Well, I'll create a script and then implement it in the GUI, but, for now, you'll have to:
1. Connect normally using QtSixA modules
2. Disconnect it
3. Open a terminal and type:
```
sudo /etc/init.d/bluetooth stop
sudo modprobe uinput
sudo sixad-bin
```

Then press the PS button. It will connect and register a new joystick, with the Accelerometers/Gyro in Axis 4-7. The Axis 20-27 were disabled, cause they are not needed and don't do anything at all.


Please report anything you get

---

### Post by DEagleson on 2009-07-21
> **stingerid4 said:**
> Greetings, 

Just trying out (X)ubuntu for the first time on my ps3 and it's .. well it's quite slow and crappy but it gets my geek mode on and that's all quite fun.

So I tried your program and I gotta say it's bloody awesome. Sixaxis works perfectly on my ps3. 

Now I also have a ps3 keypad thingie ([linky]("http://www.us.playstation.com/PS3/Accessories/SCPH-98048?ILC-lps&FTTR=PS3_keypad_bottomleft_wirelesskeypaddetailpage")). It connects and the mouse feature of it works perfectly. But the keyboard doesn't do anything. I assume I need some sort of profile or so to bind all the keys on the keyboard to actual keys? .. Just I have no idea how to do that. Any help would be greatly appreciated.

hmm small edit: it does work in the console (ctrl+alt+f1) just not in the graphical interface

Have you tried activating thee Vram as Swap?
I dont remember exacly how to do it but a quick google search should point you in the right direction.

---

### Post by asetapen on 2009-07-21
I'm having trouble connecting with SixA via bluetooth. The controller works when connected via usb, but I'm having problems when starting the module.

The main QtSixA tab lists a connected controller when connected through USB. I've run the Sixpair setup under the advanced tab, and the controller's MAC address is found just fine. However, when I attempt to start the module, and am prompted to press the PS button, the list of connected Sixaxis controllers remains unpopulated.

Any ideas? I've tried resetting the bluetooth data, as well as restoring the original profiles. Oh, and I'm running 9.04 on a mac mini.

Thanks in advance

---

### Post by falkTX on 2009-07-21
> **asetapen said:**
> I'm having trouble connecting with SixA via bluetooth. The controller works when connected via usb, but I'm having problems when starting the module.

The main QtSixA tab lists a connected controller when connected through USB. I've run the Sixpair setup under the advanced tab, and the controller's MAC address is found just fine. However, when I attempt to start the module, and am prompted to press the PS button, the list of connected Sixaxis controllers remains unpopulated.

Any ideas? I've tried resetting the bluetooth data, as well as restoring the original profiles. Oh, and I'm running 9.04 on a mac mini.

Thanks in advance

please run "qt-sixa" from a terminal (apps -> utils -> terminal/console).
then post here it's output

---

### Post by asetapen on 2009-07-21
Yeah, I already tried that - sorry I forgot to post the output (it wasn't very helpful for me)

$> qt-sixa
32652 ?        00:00:00 hidd-six
 * Stopping bluetooth                                                    [ OK ] 
Using LED #1
hidd[14173]: Bluetooth HID daemon

And this is when it hangs.

When I try to clear the bluetooth data I get:
rm: cannot remove `/var/lib/bluetooth': No such file or directory

---

### Post by falkTX on 2009-07-21
> **asetapen said:**
> Yeah, I already tried that - sorry I forgot to post the output (it wasn't very helpful for me)

$> qt-sixa
32652 ?        00:00:00 hidd-six
 * Stopping bluetooth                                                    [ OK ] 
Using LED #1


And this is when it hangs.

When I try to clear the bluetooth data I get:
rm: cannot remove `/var/lib/bluetooth': No such file or directory

Hmmm... Mac mini you said.. I suppose it's powerpc?

Try running the modules, and then clicking next/back some times
(still with the terminal output)

---

### Post by asetapen on 2009-07-21
Nope, it's an intel x86 mac mini running 64 bit jaunty.

I get the same thing over and over when I go back and forward:

14173 ?        00:00:00 hidd-six
 * Stopping bluetooth                                                    [ OK ] 
Using LED #1
hidd[15730]: Bluetooth HID daemon
15730 ?        00:00:00 hidd-six
hidd[15730]: Exit
 * Stopping bluetooth                                                    [ OK ] 
Using LED #1
hidd[15796]: Bluetooth HID daemon
15796 ?        00:00:00 hidd-six
hidd[15796]: Exit
 * Stopping bluetooth                                                    [ OK ] 
Using LED #1
hidd[15858]: Bluetooth HID daemon
15858 ?        00:00:00 hidd-six
hidd[15858]: Exit

Also, I should mention that all 4 leds on the PS3 controller continuously blink.

---

### Post by falkTX on 2009-07-21
> **asetapen said:**
> Nope, it's an intel x86 mac mini running 64 bit jaunty.

I get the same thing over and over when I go back and forward:

14173 ?        00:00:00 hidd-six
 * Stopping bluetooth                                                    [ OK ] 
Using LED #1
hidd[15730]: Bluetooth HID daemon
15730 ?        00:00:00 hidd-six
hidd[15730]: Exit
 * Stopping bluetooth                                                    [ OK ] 
Using LED #1
hidd[15796]: Bluetooth HID daemon
15796 ?        00:00:00 hidd-six
hidd[15796]: Exit
 * Stopping bluetooth                                                    [ OK ] 
Using LED #1
hidd[15858]: Bluetooth HID daemon
15858 ?        00:00:00 hidd-six
hidd[15858]: Exit

Also, I should mention that all 4 leds on the PS3 controller continuously blink.

This is weird. Usually it works on 64bit.

You can try this: (after trying to connect, please don't reboot)
open a terminal and type:
```
sudo /etc/init.d/bluetooth stop
sudo apt-get update && sudo apt-get install sixa-extra-modules
sudo modprobe uinput
sudo sixad-bin
```
Then press the PS button.
If it works, the LEDs will start to change and then a message it's printed.
Press Ctrl+C on the terminal to close the Sixaxis connection.


Also, are you sure that your bluetooth stick/pen works fine in ubuntu? (connecting to cellphone, etc?)

---

### Post by asetapen on 2009-07-21
Bingo - after some searching I found that the onboard bluetooth adaptor for the new mac mini is broken. Thanks for your help debugging this problem. I'll probably just go grab a dongle and try again.

Thanks!

---

### Post by Gliitch on 2009-07-21
@FalkTX

Sorry, I'll try and explain it better .... I think it may of just been my mistake, pressing Ctrl+R usually brings up the "bluetooth should now be started" box.The problem I was having was that i pressed Ctrl+R  it wasn't restarting because my cursor wasn't on the program, but on the desktop so it was refreshing the desktop instead.

---

### Post by stingerid4 on 2009-07-21
> **falkTX said:**
> I don't have one to try it out, but I think it only needs some input profile (NOT the same as the ones in QtSixA) that will map buttons from the pad to "fake" real buttons.
To be honest, I didn't even knew it has mouse input...


But you can help by doing this:
1. connect it to the USB (without Sixaxis, just the pad) and run "lsusb" from a terminal. Then post the output
2. connect it through bluetooth (how did you do this?) and run "dmesg | tail". Send me the output as well.

That will help

Connecting it via your sixaxis program is quite easy:
```
stinger@psubuntu:~$ sixa s
[sudo] password for stinger:
 * Stopping bluetooth                                                                                                                                                                                                                 [ OK ]
Please press the PS button on your Sixaxis joysticks
Once you see them reported here, click 'Enter' or 'Return' on the PC keyboard
Using LED #1
hidd[4312]: Bluetooth HID daemon
hidd[4312]: New HID device 00:23:06:68:66:3A (Sony Computer Entertainment Wireless Keypad)

hidd[4312]: Exit
 * Starting bluetooth    
```

So I think this thing is actually a keyboard, as it works right out of the box on the console after pairing it via the sixa program.

I think it's just this HAL thing I've been reading about, cause this is what my Xorg.0.log says right after it's connected via your sixa program:

```
(II) config/hal: Adding input device Sony Computer Entertainment Wireless Keypad
(II) Synaptics touchpad driver version 0.99.3
(**) Option "Device" "/dev/input/event2"
(--) Sony Computer Entertainment Wireless Keypad: no supported touchpad found
(**) Sony Computer Entertainment Wireless Keypad: always reports core events
(II) XINPUT: Adding extended input device "Sony Computer Entertainment Wireless Keypad" (type: TOUCHPAD)
(**) Sony Computer Entertainment Wireless Keypad: (accel) keeping acceleration scheme 1
(**) Sony Computer Entertainment Wireless Keypad: (accel) filter chain progression: 2.00
(**) Sony Computer Entertainment Wireless Keypad: (accel) filter stage 0: 20.00 ms
(**) Sony Computer Entertainment Wireless Keypad: (accel) set acceleration profile 0

```

it only recognizes the touch pad .. any idea how I can tell Hal .. hey uhm .. it has 2 devices you should look at *smacks*?

I know this probably has nothing to do anymore with your program, but any help in the right direction would be greatly appreciated. 

> **DEagleson said:**
> Have you tried activating thee Vram as Swap?
I dont remember exacly how to do it but a quick google search should point you in the right direction.

Yeah I did, it helped a bit. It's just too bad it's all stuck in the hypervisor, could have done so much more fun stuff with it.

---

### Post by stingerid4 on 2009-07-21
> 2. connect it through bluetooth (how did you do this?) and run "dmesg | tail". Send me the output as well.

this gives:
```
[ 2596.385931] input: Sony Computer Entertainment Wireless Keypad as /devices/ps3_system/sb_07/usb2/2-2/2-2:1.0/bluetooth/hci0/hci0:44/input7
[ 2596.426420] generic-bluetooth 0005:054C:03A0.0007: input,hidraw4: BLUETOOTH HID v0.01 Mouse [Sony Computer Entertainment Wireless Keypad] on 00:1B:FB:9C:21:29

```

edit: a little ps. on this  .. should I maybe set up these input devices in my xorg.conf or so? .. it's totally empty right now <.< .. first time I see that, so I guess it detects all settings himself? .. just brainstorming on my own here :)

---

### Post by stingerid4 on 2009-07-21
> **falkTX said:**
> 
```
sudo /etc/init.d/bluetooth stop
sudo modprobe uinput
sudo sixad-bin
```

Then press the PS button. It will connect and register a new joystick, with the Accelerometers/Gyro in Axis 4-7. The Axis 20-27 were disabled, cause they are not needed and don't do anything at all.


Please report anything you get

my report:
```
stinger@psubuntu:~$ sudo /etc/init.d/bluetooth stop
 * Stopping bluetooth                                                                                                                                                                                                                 [ OK ]
stinger@psubuntu:~$ sudo modprobe uinput
WARNING: All config files need .conf: /etc/modprobe.d/oss-compat, it will be ignored in a future release.
stinger@psubuntu:~$ sudo sixad-bin
Will Use LED #1
Press the PS button now
error on uinput ioctl (UI_SET_ABSBIT)
sixad-bin: uinput_open(): : Invalid argument

```

so close ;)

---

### Post by falkTX on 2009-07-22
> **stingerid4 said:**
> ```
stinger@psubuntu:~$ sudo sixad-bin
Will Use LED #1
Press the PS button now
error on uinput ioctl (UI_SET_ABSBIT)
sixad-bin: uinput_open(): : Invalid argument

```

so close ;)

I think I solved this problem last night. Please try this again, but run now 'sixad' instead of 'sixad-bin'.
That should give you the accelerometer driver (although it's a little experimental right now)

Edit: Don't forget to update first...

---

### Post by falkTX on 2009-07-22
**Update:**
* Experimental Accelerometer/Gyro driver in a new tab
* Info button now displays more information

I need to say, please test out the new driver  (there's a new tab, "experimental", in the GUI).
If this is reported to work good enough, I'll implemented as a main feature

---

### Post by falkTX on 2009-07-22
> **stingerid4 said:**
> this gives:
```
[ 2596.385931] input: Sony Computer Entertainment Wireless Keypad as /devices/ps3_system/sb_07/usb2/2-2/2-2:1.0/bluetooth/hci0/hci0:44/input7
[ 2596.426420] generic-bluetooth 0005:054C:03A0.0007: input,hidraw4: BLUETOOTH HID v0.01 Mouse [Sony Computer Entertainment Wireless Keypad] on 00:1B:FB:9C:21:29

```

edit: a little ps. on this  .. should I maybe set up these input devices in my xorg.conf or so? .. it's totally empty right now <.< .. first time I see that, so I guess it detects all settings himself? .. just brainstorming on my own here :)

This should be fixed with a simple text file in the right location.

Please try downloading the attached file, unzip it, and copy it to:
/usr/share/hal/fdi/policy/20thirdparty

Then check if anything changed when connecting the pad again

---

### Post by stingerid4 on 2009-07-22
> **falkTX said:**
> This should be fixed with a simple text file in the right location.

Please try downloading the attached file, unzip it, and copy it to:
/usr/share/hal/fdi/policy/20thirdparty

Then check if anything changed when connecting the pad again

tried this and I'm afriad the same thing happens:
dmesg:
```
[  594.650085] Bluetooth: HIDP (Human Interface Emulation) ver 1.2
[  601.679416] input: Sony Computer Entertainment Wireless Keypad as /devices/ps3_system/sb_07/usb2/2-2/2-2:1.0/bluetooth/hci0/hci0:43/input2
[  601.736572] generic-bluetooth 0005:054C:03A0.0002: input,hidraw1: BLUETOOTH HID v0.01 Mouse [Sony Computer Entertainment Wireless Keypad] on 00:1B:FB:9C:21:29

```

Xorg log:
```
(II) config/hal: Adding input device Sony Computer Entertainment Wireless Keypad
(II) LoadModule: "synaptics"
(II) Loading /usr/lib/xorg/modules/input//synaptics_drv.so
(II) Module synaptics: vendor="X.Org Foundation"
        compiled for 1.6.0, module version = 0.99.3
        Module class: X.Org XInput Driver
        ABI class: X.Org XInput driver, version 4.0
(II) Synaptics touchpad driver version 0.99.3
(**) Option "Device" "/dev/input/event2"
(--) Sony Computer Entertainment Wireless Keypad: no supported touchpad found
(**) Sony Computer Entertainment Wireless Keypad: always reports core events
(II) XINPUT: Adding extended input device "Sony Computer Entertainment Wireless Keypad" (type: TOUCHPAD)
(**) Sony Computer Entertainment Wireless Keypad: (accel) keeping acceleration scheme 1
(**) Sony Computer Entertainment Wireless Keypad: (accel) filter chain progression: 2.00
(**) Sony Computer Entertainment Wireless Keypad: (accel) filter stage 0: 20.00 ms
(**) Sony Computer Entertainment Wireless Keypad: (accel) set acceleration profile 0
(--) Sony Computer Entertainment Wireless Keypad: no supported touchpad found
```

I put it here:
```
stinger@psubuntu:/usr/share/hal/fdi/policy/20thirdparty$ ls -l
total 16
-rw-r--r-- 1 root root 3046 2009-04-07 23:37 10-wacom.fdi
-rw-r--r-- 1 root root 1568 2009-03-19 08:49 10-x11-joystick.fdi
-rwxr-xr-x 1 root root  402 2009-07-22 11:05 10-x11-sony_pad.fdi
-rw-r--r-- 1 root root  497 2009-04-03 21:07 11-x11-synaptics.fdi

```

Even rebooted after putting it there, was probably not needed, but to no avail.

> **falkTX said:**
> I think I solved this problem last night. Please try this again, but run now 'sixad' instead of 'sixad-bin'.
That should give you the accelerometer driver (although it's a little experimental right now)

Edit: Don't forget to update first...

This is what happened when I updated: (I just did apt-get update/apt-get upgrade)
```
Get:1 http://falktx.xtreemhost.com jaunty/main sixa-extra-modules 0.2a-falktx5 [8804B]
Get:2 http://falktx.xtreemhost.com jaunty/main qt-sixa 0.3.1-falktx5 [1839kB]
Fetched 1848kB in 2s (651kB/s)
(Reading database ... 113190 files and directories currently installed.)
Preparing to replace sixa-extra-modules 0.2a-falktx3 (using .../sixa-extra-modules_0.2a-falktx5_all.deb) ...
Unpacking replacement sixa-extra-modules ...
Preparing to replace qt-sixa 0.3.1-falktx4 (using .../qt-sixa_0.3.1-falktx5_all.deb) ...
Unpacking replacement qt-sixa ...
Setting up sixa-extra-modules (0.2a-falktx5) ...
-m64 build flag was set
sixad-bin: no process killed
gcc -m64 -Wall -O2 -D_GNU_SOURCE     -c -o uinputdev.o uinputdev.c
In file included from /usr/include/features.h:354,
                 from /usr/include/stdio.h:28,
                 from uinputdev.c:20:
/usr/include/gnu/stubs.h:9:27: error: gnu/stubs-64.h: No such file or directory
make: *** [uinputdev.o] Error 1
cp: cannot stat `/tmp/sixa_extra/sixad-bin': No such file or directory
rm -f uinputdev.o sixsrv.o sixad-bin

Setting up qt-sixa (0.3.1-falktx5) ...

```

guessing it's trying to compile something 64 bit?

After this the sixad still gives the same error as before.

> **falkTX said:**
> **Update:**
* Experimental Accelerometer/Gyro driver in a new tab
* Info button now displays more information

I need to say, please test out the new driver  (there's a new tab, "experimental", in the GUI).
If this is reported to work good enough, I'll implemented as a main feature

This does nothing when I activate the experimental driver and then press the PS button on my controller, it doesn't connect, but I assume that's because of the update error?

---

### Post by falkTX on 2009-07-22
Thanks for the report.
I have found a solution for this already (missing file)

I'll upload an update to the repo soon

---

### Post by falkTX on 2009-07-22
Done. That should be fixed now.

But please run ```
sudo apt-get dist-upgrade
``` cause it will require installation of new packages (the ones that were missing)

---

### Post by falkTX on 2009-07-23
With the accelerometers working in the new driver, it's possible to use it in a variety of games. One of the best ones for this is "NeverBall"
Neverball don't has an option to configure joysticks, but you can open it's configuration file and edit the joystick axis stuff. For that run:
```
xdg-open $HOME/.neverball/neverballrc
```
At line 30, it says:
```
joystick_axis_x           0
joystick_axis_y           1
```
Change it to:
```
joystick_axis_x           4
joystick_axis_y           5
```

The next time you'll start Neverball (and if 'sixad', the new driver, is running), moving the Sixaxis (no need for buttons) will move the table, controlling the ball!
I can tell you from my personal experience - it's awesome stuff!

---

### Post by falkTX on 2009-07-23
@stingerid4:
can you please connect the sixaxis pad and run:
```
hcitool name 00:23:06:68:66:3A
```

I'll start using hcitool to get the 'list of connected Sixaxis', which will report any that has the name "PLAYSTATION(3) Controller". (to be able to show Sixaxis connect by different methods other than QtSixA)

Maybe the pad has a different name, which would make it not appear on the list. We don't want that to happen, so I need to know what name it reports.

Thanks in advance

---

### Post by stingerid4 on 2009-07-23
```
stinger@psubuntu:~$ hcitool name 00:23:06:68:66:3A
Wireless Keypad

```

no playstation 3 in the name


tried to play NetherBall .. but uhm .. doesn't really work on the PS3 .. :P guess it needs a little hardware rendering hehe. 

Not sure how else to test the gyro function.

---

### Post by falkTX on 2009-07-23
> **stingerid4 said:**
> ```
stinger@psubuntu:~$ hcitool name 00:23:06:68:66:3A
Wireless Keypad

```

no playstation 3 in the name


tried to play NetherBall .. but uhm .. doesn't really work on the PS3 .. :P guess it needs a little hardware rendering hehe. 

Not sure how else to test the gyro function.

Just tell me it works on PPC OSes...

does:
```
jstest /dev/input/js0
```
Moves the 4-7 axis?

---

### Post by stingerid4 on 2009-07-23
oooh js0, yeah it works beautifully! Though axis 4-5-6 move, not 7

---

### Post by falkTX on 2009-07-23
> **stingerid4 said:**
> oooh js0, yeah it works beautifully! Though axis 4-5-6 move, not 7

Nice! Now all I need to know now is if it works on 64bit PCs too (not just PowerPC and i386)

I'm also preparing an init script, to launched at boot, so Sixaxis can actually be connected while booting (not sure if it will work or not)

---

### Post by Polk1986 on 2009-07-23
I have been using the program for the last month or two, and I must say it is improving rapidly! It's really great that I can use my DS3 for games and videos. I'm excited about the new init script as I am trying to completely avoid using a keyboard and mouse on my living room HTPC.

I was wondering if there was any chance of implementing a way to make our own key configurations on our machine? The new button is all greyed out on mine, where we used to be able to make a new file to send you, so I was wondering what is up with that? 

Also, I just wanted to see how much interest there was on the forums for setting up a paypal donation box or something so that falkTX can get some more hardware to test to help speed up testing. Perhaps this is a silly idea, but if everyone chips in $5-$10 then he could do more testing on multiple controllers, the keyboard, and perhaps other alternative controllers as well.

---

### Post by falkTX on 2009-07-24
> **Polk1986 said:**
> I have been using the program for the last month or two, and I must say it is improving rapidly! It's really great that I can use my DS3 for games and videos. I'm excited about the new init script as I am trying to completely avoid using a keyboard and mouse on my living room HTPC.

I was wondering if there was any chance of implementing a way to make our own key configurations on our machine? The new button is all greyed out on mine, where we used to be able to make a new file to send you, so I was wondering what is up with that? 

Also, I just wanted to see how much interest there was on the forums for setting up a paypal donation box or something so that falkTX can get some more hardware to test to help speed up testing. Perhaps this is a silly idea, but if everyone chips in $5-$10 then he could do more testing on multiple controllers, the keyboard, and perhaps other alternative controllers as well.

Thanks!

The reason the "new profile" buttons is greyed out is because QtSixA now has to run as root (need for battery function, also you won't have to type password several times...). The created file is automatically putted in the user Docs folder, but since the app run as root, that will go to the root folder (that should never happen).
I'll try to implement a 'select-location-to-save-file' thing when the profile is complete.

This is why the webpage buttons are also grey-out, cause clicking on them would launch a browser as root...

---

### Post by falkTX on 2009-07-24
**Update:**
* Changed the way Sixaxis are detected, now through 'hcitool', making appear Sixaxis connected using methods other than QtSixA
  * Display Sixaxis keypads when connected through USB
  * GUI refresh interval is now 5 seconds instead of 3

On the 'extra-sixa-modules', the new driver, there's now 2 more buttons (at the end). Those buttons are triggered when the horizontal/vertical accelerometer is moved quickly (something like the Wii controller does). The code for buttons are not yet finished, but are usable now.

I haven't found a good game to try this yet, if you did - tell me!


*To test the driver, run in a terminal - 'sixad'*

---

### Post by falkTX on 2009-07-24
forget this post, New driver now supports input profiles!

---

### Post by halfsoul on 2009-07-26
> **falkTX said:**
> QUESTION:
Should the init script (the one that allows connect sixaxis from boot) use:
1. Support for input profiles but no accelerometers
2. No support for input profiles but accelerometers do work


(maybe an option to configure it inside QtSixA?)
I suspect most people will be using it for vintage emulation, and I think support for non-console accelerometer applications is still very limited.  I would vote for profiles (1).  Of course, an option would be the best.

---

### Post by falkTX on 2009-07-27
**Update:** *(copied from changelog)*
  * New upstream release:
    - New SixA driver is now compatible with input profiles!
    - Fixed input profiles "none" keys (may had cause X crashes)
    - "New" button on input profile tab is available again
    [You're now able to choose the filename/path to save to]
    - 'List of Sixaxis' now also displays controller's name (at right of address)
    - "QtSixA Modules" now has option to start the new driver
    - Removed the experimental driver tab
    - Added a "Game Profiles" tab ('Neverball' and 'ePSXe' profiles are available now)
    - Added a simple label text that informs if QtSixA modules are running or not
    - In the about dialog, 'devs' has changed to 'thanks to'
    - Support for new hardware:
      + PS3 remote appears in 'list of Sixaxis' when connected through USB (bluetooth not yet)
      + PS3 remote support using the new driver (NOT TESTED!, and will not appear on 'list of Sixaxis' or setup)
      + Keypad support using the new driver (only mouse "works" yet [NOT TESTED!])
    - New 'List of Features' menu action in "Help"
    - Allow the 'non-use' of LED in QtSixA modules (new driver only, all LEDs will be off)
    - Auto-start new driver when starting QtSixA
    - Added a splash screen [can someone do a better one, please?]
    - 'List of Sixaxis' is now 'list of devices', since QtSixA supports more than just Sixaxis
    - QtSixA Daemon removed (QtSixA auto-loads modules now; still available in applications)
    - Other small fixes

---

### Post by falkTX on 2009-07-27
There's a lot of new things...
The most notable one (besides the splash screen), is that QtSixA modules now automatically loads when starting the app.

The next thing I'll focus on is the keypad, but I need help to get it working. If you have one and you're not a linux newbie, please reply

---

### Post by falkTX on 2009-07-27
Donations are now accepted:
[http://falktx.blogspot.com/](http://falktx.blogspot.com/)

The first thing I'll get is a Keypad, then a DS3. Maybe, if enough money, a PS3 remote as well

---

### Post by stingerid4 on 2009-07-27
I got a new harddisk for my ps3 so I reinstalled xubuntu from scratch. Had to start over with all the things

When I installed sixa (added the repository and then did apt-get install sixa) I got this error:
```
Setting up sixa-extra-modules (0.2a-falktx8) ...
-m64 build flag was set
sixad-bin: no process killed
gcc -m64 -Wall -O2 -D_GNU_SOURCE    -c -o uinputdev.o uinputdev.c
gcc -m64 -Wall -O2 -D_GNU_SOURCE    -c -o sixsrv.o sixsrv.c
gcc uinputdev.o sixsrv.o -m64 -Wall -O2 -D_GNU_SOURCE  -o sixad-bin  -lbluetooth
/usr/bin/ld: skipping incompatible /usr/lib/gcc/powerpc-linux-gnu/4.3.3/../../../libbluetooth.so when searching for -lbluetooth
/usr/bin/ld: skipping incompatible /usr/lib/libbluetooth.so when searching for -lbluetooth
/usr/bin/ld: cannot find -lbluetooth
collect2: ld returned 1 exit status
make: *** [sixad-bin] Error 1
cp: cannot stat `/tmp/sixa_extra/sixad-bin': No such file or directory
rm -f uinputdev.o sixsrv.o sixad-bin

```


but .. good news! I got my keypad to work :D

> **falkTX said:**
> This should be fixed with a simple text file in the right location.

Please try downloading the attached file, unzip it, and copy it to:
/usr/share/hal/fdi/policy/20thirdparty

Then check if anything changed when connecting the pad again

This was your fdi file:
```
<?xml version="1.0" encoding="UTF-8"?>
<deviceinfo version="0.2">
  <device>
      <!-- Experimental Keypad driver for Sixaxis -->      
      <match key="input.product" string_outof="Sony Computer Entertainment Wireless Keypad">
        <merge key="input.x11_driver" type="string">joystick</merge>
	<merge key="input.x11_driver" type="string">keyboard</merge>
      </match>
  </device>
</deviceinfo>

```

I moved the file to /etc/hal/fdi/policy (where you put one of your fdi's as well?)
and changed the file to:
```
<?xml version="1.0" encoding="UTF-8"?>
<deviceinfo version="0.2">
  <device>
      <!-- Experimental Keypad driver for Sixaxis -->
      <match key="input.product" string_outof="Sony Computer Entertainment Wireless Keypad">
        <merge key="input.x11_driver" type="string">synaptic</merge>
        <merge key="input.x11_driver" type="string">evdev</merge>
      </match>
  </device>
</deviceinfo>

```

And then it worked :)

happily mousing and typing away on my ps3 via the keypad.

Just one question .. not sure if it's possible. this keypad isn't a true keyboard, misses some buttons like .. ctrl, alt, all the f keys. 
It does have 2 buttons that is just for the ps3, a link to the message menu in the XMB and the friendlist. Would it maybe be possible somehow to bind these 2 keys to make them work as ctrl and alt?

---

### Post by stingerid4 on 2009-07-27
hmmm

that's weird .. I just saw I made a typing error in "synaptic" .. it should be "synaptics"

It still works though

with only evdev I get this in the log:
```
(II) config/hal: Adding input device Sony Computer Entertainment Wireless Keypad
(**) Sony Computer Entertainment Wireless Keypad: always reports core events
(**) Sony Computer Entertainment Wireless Keypad: Device: "/dev/input/event2"
(II) Sony Computer Entertainment Wireless Keypad: Found 2 mouse buttons
(II) Sony Computer Entertainment Wireless Keypad: Found x and y relative axes
(II) Sony Computer Entertainment Wireless Keypad: Found keys
(II) Sony Computer Entertainment Wireless Keypad: Configuring as mouse
(II) Sony Computer Entertainment Wireless Keypad: Configuring as keyboard
(**) Sony Computer Entertainment Wireless Keypad: YAxisMapping: buttons 4 and 5
(**) Sony Computer Entertainment Wireless Keypad: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
(II) XINPUT: Adding extended input device "Sony Computer Entertainment Wireless Keypad" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Sony Computer Entertainment Wireless Keypad: xkb_rules: "evdev"
(**) Option "xkb_model" "pc105"
(**) Sony Computer Entertainment Wireless Keypad: xkb_model: "pc105"
(**) Option "xkb_layout" "us"
(**) Sony Computer Entertainment Wireless Keypad: xkb_layout: "us"
(**) Sony Computer Entertainment Wireless Keypad: (accel) keeping acceleration scheme 1
(**) Sony Computer Entertainment Wireless Keypad: (accel) filter chain progression: 2.00
(**) Sony Computer Entertainment Wireless Keypad: (accel) filter stage 0: 20.00 ms
(**) Sony Computer Entertainment Wireless Keypad: (accel) set acceleration profile 0

```

guess I don't have to define it as a touchpad .. evdev does that itself or so?

---

### Post by Polk1986 on 2009-07-27
> **falkTX said:**
> **Update:** *(copied from changelog)*
  * New upstream release:
    - New SixA driver is now compatible with input profiles!
    - Fixed input profiles "none" keys (may had cause X crashes)
    - "New" button on input profile tab is available again
    [You're now able to choose the filename/path to save to]
    - 'List of Sixaxis' now also displays controller's name (at right of address)


I am unable to open the available keys file to make a new profile. :(

---

### Post by falkTX on 2009-07-28
> **Polk1986 said:**
> I am unable to open the available keys file to make a new profile. :(

just do in a terminal:
```
xmodmap -pke
```

I'll fix that soon (it was supposed to open your default text editor; I guess you don't have one set..?)

---

### Post by falkTX on 2009-07-28
> **stingerid4 said:**
> I got a new harddisk for my ps3 so I reinstalled xubuntu from scratch. Had to start over with all the things

When I installed sixa (added the repository and then did apt-get install sixa) I got this error:
```
Setting up sixa-extra-modules (0.2a-falktx8) ...
-m64 build flag was set
sixad-bin: no process killed
gcc -m64 -Wall -O2 -D_GNU_SOURCE    -c -o uinputdev.o uinputdev.c
gcc -m64 -Wall -O2 -D_GNU_SOURCE    -c -o sixsrv.o sixsrv.c
gcc uinputdev.o sixsrv.o -m64 -Wall -O2 -D_GNU_SOURCE  -o sixad-bin  -lbluetooth
/usr/bin/ld: skipping incompatible /usr/lib/gcc/powerpc-linux-gnu/4.3.3/../../../libbluetooth.so when searching for -lbluetooth
/usr/bin/ld: skipping incompatible /usr/lib/libbluetooth.so when searching for -lbluetooth
/usr/bin/ld: cannot find -lbluetooth
collect2: ld returned 1 exit status
make: *** [sixad-bin] Error 1
cp: cannot stat `/tmp/sixa_extra/sixad-bin': No such file or directory
rm -f uinputdev.o sixsrv.o sixad-bin

```

This should be fixed now

---

### Post by falkTX on 2009-07-28
For the keypad, I plan to make a joystick driver for it. Then, just like the input profiles for Sixaxis, the joystick buttons will be mapped to real buttons (and special ones if needed)
This will also allow different type of configurations for the keypad (like US or other country layouts; other ideas could be implemented too)

---

### Post by falkTX on 2009-07-28
**Update:**
The UInput driver - the 2 new buttons were removed (they didn't work as I expected).
But there are now 4 new buttons! These are the accelerometers, but digital. Just like any button in the Sixaxis has sensitive axis, the accelerometers should trigger buttons as well (for games that don't support axis)

The modules can now be started at boot. To test out this run:
```
sudo sixad --boot-yes
```
Please note that this will turn off regular bluetooth. You can still restore it in the QtSixA, or by
```
sudo /etc/init.d/bluetoooth start
```*(after connecting your Sixaxis)*



I'll try to get the modules running before regular bluetooth (so both can work in harmony); But since bluetooth is somehow broken in Karmic, I can't really test this.

If you want to disable the modules during boot, run
```
sudo sixad --boot-no
```

---

### Post by falkTX on 2009-07-29
**Update:**
The keypad should have some basic functionality right now (normal key buttons only; thanks stingerid4)

And basically, that's it for this update...

Sorry I've been a little busy (my brother is about to get married and needs my help...)

But, I'll have 3 weeks totally free! I still don't have the money to get new hardware to test&code, but fixing the bugs and adding new game profiles should keep me busy.


See ya soon!

---

### Post by MadrofieL on 2009-08-01
Hey,
 
I'm new to linux and just got Linux on my PS3 (after wasting 10 cd's)
but ok i'm happy i have Kubuntu 9.04 on the PS3 and it works fine. Now i'm trying to install Sixa and did what the Tutorial said,
 
sudo apt-get update && sudo apt-get install qt-sixa
 
it all went good and no error till i start Sixa. "Command not found"
and then i tried in Terminal and get this error,
 
sudo: sixad-bin: command not found
 
what does this mean? or what do i need to do to get it working?
 
Thx in advance.

---

### Post by falkTX on 2009-08-02
> **MadrofieL said:**
> Hey,
 
I'm new to linux and just got Linux on my PS3 (after wasting 10 cd's)
but ok i'm happy i have Kubuntu 9.04 on the PS3 and it works fine. Now i'm trying to install Sixa and did what the Tutorial said,
 
sudo apt-get update && sudo apt-get install qt-sixa
 
it all went good and no error till i start Sixa. "Command not found"
and then i tried in Terminal and get this error,
 
sudo: sixad-bin: command not found
 
what does this mean? or what do i need to do to get it working?
 
Thx in advance.

do in a terminal:
```
sudo apt-get install sixa-extra-modules
```

It seems that your system is not installing recommended packages...? Or have downloaded and installed them by "hand"?
Maybe because of KDE's Adept or something...

Thanks for reporting this. Please report if installing "sixa-extra-modules" goes well,and if this makes the QtSixA work for you or not

---

### Post by Enjeru on 2009-08-05
I get the following error when I try to run qt-sixa:

```
Traceback (most recent call last):  File "/usr/share/qt-sixa/gui/main.pyw", line 1216, in <module>
    QtSixA = Main_QtSixA_Window()
  File "/usr/share/qt-sixa/gui/main.pyw", line 195, in __init__
    self.func_Refresh()
  File "/usr/share/qt-sixa/gui/main.pyw", line 597, in func_Refresh
    self.listWidget.setSelectionMode(1)
TypeError: argument 1 of QAbstractItemView.setSelectionMode() has an invalid type
```

I have qt-sixa installed through the repo on Ubuntu 8.10.  Did I miss something?

---

### Post by falkTX on 2009-08-06
> **Enjeru said:**
> I get the following error when I try to run qt-sixa:

```
Traceback (most recent call last):  File "/usr/share/qt-sixa/gui/main.pyw", line 1216, in <module>
    QtSixA = Main_QtSixA_Window()
  File "/usr/share/qt-sixa/gui/main.pyw", line 195, in __init__
    self.func_Refresh()
  File "/usr/share/qt-sixa/gui/main.pyw", line 597, in func_Refresh
    self.listWidget.setSelectionMode(1)
TypeError: argument 1 of QAbstractItemView.setSelectionMode() has an invalid type
```

I have qt-sixa installed through the repo on Ubuntu 8.10.  Did I miss something?

Are you sure you have the latest updates?

This seems to be PyQT problem.
Please open Synaptic, search for "python-qt4" and report the version you have installed

---

### Post by ArwinST on 2009-08-07
Congrats, after many attempts to get the sixaxis to work properly on anything but my PS3, this worked immediately and flawlessly. I'll definitely consider donating. 

In the meantime I was wondering if anyone here has experience with writing software that reads this information? What I would like to do / experiment with is basically using opengl to render a cube and then use the various inputs including the motion sensors to manipulate the cube. Does anyone know of any sample projects in C/C++ or Java that I could consult? 

If I get to that point (rotate cube using sixaxis) I'll be so happy I'll donate $20! No, make that euros ;)

---

### Post by marcoshayeb on 2009-08-07
When I try to install sixa-extra-modules on my PS3, I get the following:

Unpacking replacement sixa-extra-modules ...
Setting up sixa-extra-modules (0.2a-falktx9) ...
-m64 build flag was set
sixad-bin: no process killed
gcc -m64 -Wall -O2 -D_GNU_SOURCE    -c -o uinputdev.o uinputdev.c
gcc -m64 -Wall -O2 -D_GNU_SOURCE    -c -o sixsrv.o sixsrv.c
gcc uinputdev.o sixsrv.o -m64 -Wall -O2 -D_GNU_SOURCE  -o sixad-bin  -lbluetooth
/usr/bin/ld: skipping incompatible /usr/lib/gcc/powerpc-linux-gnu/4.3.3/../../../libbluetooth.so when searching for -lbluetooth
/usr/bin/ld: skipping incompatible /usr/lib/libbluetooth.so when searching for -lbluetooth
/usr/bin/ld: cannot find -lbluetooth
collect2: ld returned 1 exit status
make: *** [sixad-bin] Error 1
cp: cannot stat `/tmp/sixa_extra/sixad-bin': No such file or directory
rm -f uinputdev.o sixsrv.o sixad-bin

Any idea on how to avoid this?

---

### Post by Enjeru on 2009-08-08
> **falkTX said:**
> Are you sure you have the latest updates?

This seems to be PyQT problem.
Please open Synaptic, search for "python-qt4" and report the version you have installed

python-qt4 version: 4.4.3-1ubuntu1

EDIT: Looked around launchpad and saw version 4.4.4-2ubuntu1~intrepid1 was available as a backport; everything works (except using accelerometer, but I can only test this in USB mode since I don't have bluetooth on this machine) after enabling backports in software sources and upgrading.

---

### Post by falkTX on 2009-08-10
> **marcoshayeb said:**
> When I try to install sixa-extra-modules on my PS3, I get the following:

Unpacking replacement sixa-extra-modules ...
Setting up sixa-extra-modules (0.2a-falktx9) ...
-m64 build flag was set
sixad-bin: no process killed
gcc -m64 -Wall -O2 -D_GNU_SOURCE    -c -o uinputdev.o uinputdev.c
gcc -m64 -Wall -O2 -D_GNU_SOURCE    -c -o sixsrv.o sixsrv.c
gcc uinputdev.o sixsrv.o -m64 -Wall -O2 -D_GNU_SOURCE  -o sixad-bin  -lbluetooth
/usr/bin/ld: skipping incompatible /usr/lib/gcc/powerpc-linux-gnu/4.3.3/../../../libbluetooth.so when searching for -lbluetooth
/usr/bin/ld: skipping incompatible /usr/lib/libbluetooth.so when searching for -lbluetooth
/usr/bin/ld: cannot find -lbluetooth
collect2: ld returned 1 exit status
make: *** [sixad-bin] Error 1
cp: cannot stat `/tmp/sixa_extra/sixad-bin': No such file or directory
rm -f uinputdev.o sixsrv.o sixad-bin

Any idea on how to avoid this?

I don't have a PS3 so I don't really know how to solve this. Try checking if there's a "PPC" related package in synaptic - try out any packages (in Synaptic) like "make-ppc" or "gcc-multilib-pcc".
This error occurs because of some missing files. So basically, if those file are present, it will compile fine.
I'll also search for this on the web, to see if I can find something

---

### Post by falkTX on 2009-08-10
> **Enjeru said:**
> python-qt4 version: 4.4.3-1ubuntu1

EDIT: Looked around launchpad and saw version 4.4.4-2ubuntu1~intrepid1 was available as a backport; everything works (except using accelerometer, but I can only test this in USB mode since I don't have bluetooth on this machine) after enabling backports in software sources and upgrading.

Nice to know this.
So, if anyone uses Intrepid, it will require backports...

And you're right; the gyro doesn't work on USB mode. I could make it work, but it will require lots of work (maybe kernel re-compilation...), and I basically only use it on bluetooth mode (which I think is much more important).
Of course you'll need to connect to USB to charge the battery, but usually 2-4 hours charges it completely, while it takes several days to use all the battery

---

### Post by falkTX on 2009-08-10
**Update:**
While I was helping my brother on his wedding, I didn't had time for working on QtSixA. Now that is over, it's time to work again.

I'm preparing the v0.4, that will allow to add custom input profiles. It will also have a preferences window that will remember if you want systray or some other misc options.

The donations are going fine, now having $42.34 USD. (paypal usually takes a small fee...)
This means I should be able to get a keypad soon. It also means the GUI need a new tab - just for the keypad (?) - so users from different countries can perfectly use it (the buttons on the keypad may change layout depending on the country)

---

### Post by falkTX on 2009-08-11
**Update:**
I've updated the accelerometer drivers. And because they have different names like "QtSixA modules", "new drivers", etc... we'll just call them _'sixad'_

The new update has now (partial) udev support, meaning it will auto-stop bluetooth and start 'sixad', wait 15 seconds, then restore bluetooth again.
This works fine in Karmic, but I'm not sure how it will work on previous versions (Jaunty and Intrepid).
Also, the PPC/PS3 compiling problem may be fixed now (please test!)

Since this introduces some new stuff (udev auto-detection), please do the following testing:
**1.** Update your Ubuntu:
```
sudo apt-get update && sudo apt-get dist-upgrade
```
**2.** Reboot (required!) *- Please restart with the bluetooth stick/pen connected*
**3.** After restarting, please wait until the desktop is fully loaded
**4.** Press the PS button on _one_ Sixaxis only.

At this point, bluetooth should be stopped (the gnome/KDE-bluetooth icon on systray should go away);
3-5 seconds later the LED animation should start, meaning it was connected;
Then after around 5 seconds, the BT icon should be restored (bluetooth was restored).
At least this is what happens to me.

Please report what happens in your Ubuntu

---

### Post by Polk1986 on 2009-08-12
OK, here's an idea that may not be possible to implement but could be cool: since each Sixaxis/DS3 has an individual ID, would it be possible to assign a particular key layout to a specific controller everytime you auto-connect? Like if I have two controllers, one is always player 1 and one is always player 2, and the computer remembers which is which?

BTW, the last update (have not updated yet this week) allows me to see the list of keys, but it seems to extend below my screen in the popup. I may just need to adjust my font size though, as I have it set to enormous since it is on my TV. Thanks for all the work so far!

---

### Post by falkTX on 2009-08-14
> **Polk1986 said:**
> OK, here's an idea that may not be possible to implement but could be cool: since each Sixaxis/DS3 has an individual ID, would it be possible to assign a particular key layout to a specific controller everytime you auto-connect? Like if I have two controllers, one is always player 1 and one is always player 2, and the computer remembers which is which?

BTW, the last update (have not updated yet this week) allows me to see the list of keys, but it seems to extend below my screen in the popup. I may just need to adjust my font size though, as I have it set to enormous since it is on my TV. Thanks for all the work so far!

This could be a little more difficult...
Usually we only get a Sixaxis MAC/ID when we connect it, so this way we probably need you to press the PS twice (1 - identification; 2- connection).
But I'll try this as soon as I get the 0.4 ready (maybe for 0.4.1)

And that list-of-keys-bug... I know about it; I was trying to make it with a scrollbar on the right... I'll fix that soon

---

### Post by falkTX on 2009-08-14
*I posted this on my blog and I'll post it here too:*

Maybe you notice that the QtSixA icon says "SixA" instead of QtSixA...
Or maybe you don't like much of the icon...

Well, I don't like it much as well. But, every application needs an icon.

What do you say about creating an icon for QtSixA?
And what about a splash screen too?


I'll be waiting for comments!

---

### Post by falkTX on 2009-08-16
I just wanted to make you guys aware that QtSixA 0.4.0 will be available soon.

I've been working on the udev rule (auto-load sixad), so that no more "starting modules" is needed (and also QtSixA...)
It _will_ be possible too assign a profile for a controller or keypad. Maybe only for 0.4.1, but* it will happen*
The "input profiles" Sixaxis pictures will be replace by an SVG ones, making QtSixA real GPL


If I manage to get it ready/stable soon, I'll try to make it appear in the universe Ubuntu repositories, for Karmic

---

### Post by falkTX on 2009-08-18
**Update:**
[SIZE="4"]QtSixA 0.4.0 (Beta) as been released![/SIZE]

Because it's beta, some of the GUI option and buttons don't work yet.
But the "Link Quality" related actions are now available - You can use this to, for example, shutdown your PC when your Sixaxis or Keypad link/signal reaches 30% quality.


Here's the full changelog:
-----------------------------
    - You can now add your own custom input profiles
    - Disconnect menu now also displays device's name
    - Added "Change Input Profile" to menu (disabled for now)
    - Added "Preferences" to Options menu (moved systray options there)
    - sixad now displays all devices detected (even if non-Sony)
    - Add debian dependency "qt4-qtconfig" (needed for changing Qt theme)
    - Only try to check battery if the selected device is a Sixaxis
    - New tab "Outro" (with some widgets from the old "Advanced" tab)
    - New "Advanced" tab (disabled for now)
    - Replaced "Stop QtSixA Modules" for "Sixpair Setup" in 'Quick Tasks'
    - Added "Stop Bluetooth" action to Tasks menu
    - (Maybe) PS3 remotes will appear on the 'list of devices' when connected through bluetooth
    - "Start QtSixA Modules" renamed to 'old'; Only starts Old hidd connection
    [sixad is now auto-started when needed]
    - Removed the splash screen
    - Added an update information when starting QtSixA
    - Added "Donate" menu action (in Help)
    - Added names of people that donated QtSixA, in the About-Thanks tab
    - Lots of other small fixes and improvements
    - Mark this release as Beta



Happy vacations, if that's the case!

---

### Post by falkTX on 2009-08-19
**Update:** *(0.4.0 Beta 2)*

Changelog:
  * Re-Added bluez-sixa as debian dependency [Why was it removed??]
  * Do not refresh "Advanced" tab automatically (causes visual bugs)
  * All web links are now in "Help" -> "Web Links" (Also added "Ubuntu Forums" and "Submit Idea")
  * Added "Sixaxis Reference" to Help menu
  * Added python2.5 or python2.6 as debian dependency
  * Notifications are now implemented [through libnotify-bin]
  * Override system-wide set profiles through MAC/ID-Check is now implemented (only for bluetooth, using sixad)
    [This will not be possible for USB cause it would require modifying the kernel...]
  * All widgets in "Outro" and "Advanced" tabs are now not checkable
  * Added missing status tips where convenient (still need some more)
  * Removed support for PS3 remotes in sixad (BlueZ officially supports them, not need for an extra driver)
  * Marked as Beta 2

Only some minor stuff doesn't work now. I'll try to make all GUI features enabled for the final 0.4.0, but I can't promise that all stuff will be implemented.

You may also notice that is now possible to notify when a Sixaxis/Remote/Keypad is connected; it uses 'libnotify-bin', so it looks very nice in Gnome or KDE 4.3. You should try it out!

---

### Post by Polk1986 on 2009-08-22
I updated my QT-SixA through the repositories yesterday and have been unable to connect since then. I will try to get terminal output up soon, but I am leaving town at the moment and was wondering if anyone else was experiencing issues with Jaunty? Thanks.


EDIT: Added terminal code. I also seem to be unable to access the GUI as I told it to minimize to system tray on startup, but nothing shows in the system tray. Thanks.


```

File "/usr/share/qt-sixa/gui/main.pyw", line 955, in <module>
    QtSixA = Main_QtSixA_Window()
  File "/usr/share/qt-sixa/gui/main.pyw", line 117, in __init__
    if config_enable_systray == "1":  self.createTrayIcon()
  File "/usr/share/qt-sixa/gui/main.pyw", line 383, in createTrayIcon
    self.trayIcon.activated.connect(self.func_Systray_Clicked)
AttributeError: activated
```

---

### Post by nxmehta on 2009-08-22
Thank you so much for this great program!  It was very easy to setup my DS3 and get it working.  I'm definitely going to donate to this project :)

I just have a few issues that I wanted to ask you about:

1. Can you add an option to disable axes 4-7?  They make it basically impossible to setup joystick controls on some emulators.  For example, on mupen64plus, when you setup the joystick you click the N64 controller button you want to setup, and then mupen waits for input.  It then immediate receives input from one of the accelerometer/gyro axes before I can press a button on the controller.  Axes 7 in particular is trouble- it always seems to get input from that.  When I run jscalibrator axis 7 doesn't appear to do anything (its axis value doesn't change with any motion) and it seems to be set to the maximum value for its range (32767).  So I don't know what axis 7 is supposed to correspond to.  Anyways, if you could add this feature or tell me how to work around it I'd really be greatful.

I know that I can setup a keyboard mapping, but I'd much prefer using a joystick because the analog sticks are pressure sensitive (unlike a keyboard).  Plus many emulators have different, hardcoded shortcut keys that do things like pause the game, exit the emulator, etc, so it's hard to come up with one keyboard profile that would work for all of them.  Using a joystick is a much easier solution.

2. There seems to be a sixa-notify file that keeps getting created in my homedir.  If you need this for libnotify or something, could you name it .sixa-notify so it gets hidden?

3. I'm encountering an occasional bug where after I pair my joystick and connect it via bluetooth, if I then connect the same joystick via a usb cable I get logged out of my gnome session!?  I wonder if it's causing compiz to crash.  It's not a bug I run into regularly, but it does seem pretty weird.  I'll see if I can come up with a sequence of operations to help you replicate it.

4. I'm see an error after installing qt-sixa from the repository.  It doesn't seem to affect anything but everytime I install any package via apt-get I see the same message:

/usr/share/menu/qt-sixa: 1: Syntax error: word unexpected (expecting ")")
Execution of /usr/share/menu/qt-sixa generated no output or returned an error.

5. There seems to be a problem with your GPG key for the repository?

W: GPG error: [http://falktx.xtreemhost.com](http://falktx.xtreemhost.com) jaunty Release: The following signatures were invalid: BADSIG 474A97AA5834371E Filipe Coelho (falkTX) <falktx@gmail.com>
W: You may want to run apt-get update to correct these problems

Thanks again for you hard work!

---

### Post by refried on 2009-08-23
> **stingerid4 said:**
> I got a new harddisk for my ps3 so I reinstalled xubuntu from scratch. Had to start over with all the things

When I installed sixa (added the repository and then did apt-get install sixa) I got this error:
```
Setting up sixa-extra-modules (0.2a-falktx8) ...
-m64 build flag was set
sixad-bin: no process killed
gcc -m64 -Wall -O2 -D_GNU_SOURCE    -c -o uinputdev.o uinputdev.c
gcc -m64 -Wall -O2 -D_GNU_SOURCE    -c -o sixsrv.o sixsrv.c
gcc uinputdev.o sixsrv.o -m64 -Wall -O2 -D_GNU_SOURCE  -o sixad-bin  -lbluetooth
/usr/bin/ld: skipping incompatible /usr/lib/gcc/powerpc-linux-gnu/4.3.3/../../../libbluetooth.so when searching for -lbluetooth
/usr/bin/ld: skipping incompatible /usr/lib/libbluetooth.so when searching for -lbluetooth
/usr/bin/ld: cannot find -lbluetooth
collect2: ld returned 1 exit status
make: *** [sixad-bin] Error 1
cp: cannot stat `/tmp/sixa_extra/sixad-bin': No such file or directory
rm -f uinputdev.o sixsrv.o sixad-bin

```


I just installed jaunty-ps3 last night, and tried installing sixad from the repository this morning, and am having the same build problem. 

Any suggestions?

Thanks

---

### Post by falkTX on 2009-08-23
> **Polk1986 said:**
> I updated my QT-SixA through the repositories yesterday and have been unable to connect since then. I will try to get terminal output up soon, but I am leaving town at the moment and was wondering if anyone else was experiencing issues with Jaunty? Thanks.


EDIT: Added terminal code. I also seem to be unable to access the GUI as I told it to minimize to system tray on startup, but nothing shows in the system tray. Thanks.


```

File "/usr/share/qt-sixa/gui/main.pyw", line 955, in <module>
    QtSixA = Main_QtSixA_Window()
  File "/usr/share/qt-sixa/gui/main.pyw", line 117, in __init__
    if config_enable_systray == "1":  self.createTrayIcon()
  File "/usr/share/qt-sixa/gui/main.pyw", line 383, in createTrayIcon
    self.trayIcon.activated.connect(self.func_Systray_Clicked)
AttributeError: activated
```

That really seems to be an error of mine. It shouldn't have self.trayIcon.**activated**.connect.
Thanks for the report. I'll fix that on the next update (beta 3)

To pass to problem now you can do:
```
sudo cp /usr/share/qt-sixa/qtsixa.conf.bak /usr/share/qt-sixa/qtsixa.conf
```
That will restore the default settings

---

### Post by falkTX on 2009-08-23
> **nxmehta said:**
> Thank you so much for this great program!  It was very easy to setup my DS3 and get it working.  I'm definitely going to donate to this project :)
Thanks!

> **nxmehta said:**
> I just have a few issues that I wanted to ask you about:

1. Can you add an option to disable axes 4-7?  They make it basically impossible to setup joystick controls on some emulators.  For example, on mupen64plus, when you setup the joystick you click the N64 controller button you want to setup, and then mupen waits for input.  It then immediate receives input from one of the accelerometer/gyro axes before I can press a button on the controller.  Axes 7 in particular is trouble- it always seems to get input from that.  When I run jscalibrator axis 7 doesn't appear to do anything (its axis value doesn't change with any motion) and it seems to be set to the maximum value for its range (32767).  So I don't know what axis 7 is supposed to correspond to.  Anyways, if you could add this feature or tell me how to work around it I'd really be greatful.
This came to my mind when I first started with the Accel support. Also, the Acceleration/Speed is almost done and will be implemented soon - which will make this even more difficult...

But one simple way to pass this is to use the Sixaxis in USB during the game joystick setup process (the Accel/Gyro/LED only works via bluetooth).


> **nxmehta said:**
> 2. There seems to be a sixa-notify file that keeps getting created in my homedir.  If you need this for libnotify or something, could you name it .sixa-notify so it gets hidden?
That's something that shouldn't be happening - the sixa-notify file needs to be written to "/tmp/sixa-notify"... But I'll hide it anyway, it doesn't hurt

> **nxmehta said:**
> 3. I'm encountering an occasional bug where after I pair my joystick and connect it via bluetooth, if I then connect the same joystick via a usb cable I get logged out of my gnome session!?  I wonder if it's causing compiz to crash.  It's not a bug I run into regularly, but it does seem pretty weird.  I'll see if I can come up with a sequence of operations to help you replicate it.
So you're having this bug too... I though it was just in Karmic... (and I'm using KDE, so it's a X/Xorg bug)
I think, but not sure, that this error occurs because, in the input profiles, there are some "key=none", where 'none' it's not a real key. The problem is that removing this part will get the Sixaxis act like a mouse button.
The solution is to find a "key" that is null (maybe 'NoSymbol'?). Since this is not just a Karmic bug, I'll look deep into this and fix it as soon as possible

> **nxmehta said:**
> 4. I'm see an error after installing qt-sixa from the repository.  It doesn't seem to affect anything but everytime I install any package via apt-get I see the same message:

/usr/share/menu/qt-sixa: 1: Syntax error: word unexpected (expecting ")")
Execution of /usr/share/menu/qt-sixa generated no output or returned an error.
Hmm... looks like I have one more bug to fix...

> **nxmehta said:**
> 5. There seems to be a problem with your GPG key for the repository?

W: GPG error: [http://falktx.xtreemhost.com](http://falktx.xtreemhost.com) jaunty Release: The following signatures were invalid: BADSIG 474A97AA5834371E Filipe Coelho (falkTX) <falktx@gmail.com>
W: You may want to run apt-get update to correct these problems
I spend hells of time looking for a solution for this. But I gave up searching/working for a solution. It's not that easy to get a repository trusted, you know?
You may ask why I don't use Launchpad... the answer is simple - it doesn't build for PowerPC (used in PS3). This is a very important thing

> **nxmehta said:**
> Thanks again for you hard work!
Thank you, for using my software!

---

### Post by falkTX on 2009-08-23
> **refried said:**
> I just installed jaunty-ps3 last night, and tried installing sixad from the repository this morning, and am having the same build problem. 

Any suggestions?

Thanks

can you try:
```
sudo apt-get install libc6-dev libc6-dev-i386 libc6-dev-amd64 libc6-dev-ppc64 lib64gcc1 lib64objc2 gcc-multilib ppu-ppc
```
Then, when update the repositories stuff (I've launched an update), please check if that still happens

*Note: I've found lots of building failures like this on the web, seems like it's a common thing to PPC64 users.*

---

### Post by falkTX on 2009-08-23
**Update:**
The sixad driver will now compile using ppu-gcc instead of gcc in PowerPC64 machines (including PS3). This may fix the builds errors - please report

The Acceleration and Speed works now (axis 20-26). For those who don't know what that is, just leave it - I haven't found a single game that uses this feature like it should.

This can make configuring games joystick really hard. A smart thing to do is to don't move the Sixaxis while doing it (or it may trigger the accelerometers...)
Another work-around is to configure games while connect in USB, cause there's no special stuff in USB (yet)

---

### Post by falkTX on 2009-08-24
**Update:** *(Beta 3, Changelog: )*
  * Replaced "Refresh" button for "Test" button
  * Neverball game profile was (not always) applied successfully - fixed
  * Extreme Tux Racer game profile is now available
  * SuperTuxKart game profile is now available [all 4 players!]
  * ePSXe game profile now supports 2 players
  * The sixad driver now supports acceleration and speed
  * Added all the missing status tips
  * Added keypad option to sixpair setup
  * Added 2 new tools to sixad package:
    -> sixad-raw (prints all buttons/axis information from a Sixaxis hidraw (sudo su root -c "sixad-raw < /dev/hidrawX")
    -> hidraw-dump (dumps all info from a hidraw device, just like hcidump (sudo su root -c "hidraw-dump < /dev/hidrawX")
  * Mouse hover systray icon now shows the list of connected devices
  * The Info button works again (reworked)
  * Hide sixa-notify file (user request)
  * Removed qt-sixa.menu file
  * (Maybe) fixed a random/weird X/Xorg crash (profiles now use 'NoSymbol' for "none" keys)
  * Warning when cannot write to file, in game profiles "Apply"
  * When creating a new profile: Mouse buttons and no axis are now supported, 'list of keys' is now clear and visible
  * Pop-up dialogs are now displayed correctly [finally!]
  * "Sixaxis reference" now fits on the screen
  * Marked as Beta 3


The hidraw enabler stuff will not be ready for 0.4.0 (I think).
As soon as I finish fixing some bugs, I'll focus on getting the Keypad to work. Some guys already mail-me about this (you can see that there's now sixpair support for keypads), so it shouldn't take long to get them working.


Can someone with a PS3 report if the sixad package builds now?

---

### Post by FJRMaverick on 2009-08-25
It does still not build on a PS3. While compiling it states that libbluetooth.so has the wrong version and cannot find -lbluetooth ....

---

### Post by falkTX on 2009-08-26
> **FJRMaverick said:**
> It does still not build on a PS3. While compiling it states that libbluetooth.so has the wrong version and cannot find -lbluetooth ....
This means the ppu-gcc didn't do anything...

What the heck is wrong?

---

### Post by falkTX on 2009-08-26
**Update:** *(changelog)*
  * Fixed final dialog when creating a new profile
  * If there are various names in "list of users" and they are the same, only show one
  * Is now possible to open the web links (only when 1 user is logged in)
  * Only add Sixaxis to the list of Sixaxis profiles overrides
  * Auto-restart QtSixA when clicked restore/clear buttons
  * Support for Keypad layouts (but not yet completed in sixad)
  * Install english layout for keypad as default (when no layout is found)
  * Updated the terminal 'sixa' to match updates
  * sixad:
  -> Keypads now registers as joysticks
  -> Experimental 5 key/button support (for testing)
  * Removed Sixaxis profiles option when starting old modules (no longer compatible)
  * Marked as RC1


The keypad will be working soon!

---

### Post by sparkix on 2009-08-27
Your application window is too big to fit completely on my display resolution (1024 x 600).  Since netbooks might be a significant portion of the users, it would be nice if they didn't have to pan the window around using alt+drag.  Just a thought.

---

### Post by Polk1986 on 2009-08-27
I have been unable to pair my DS3 since the first update to 0.4 and the subsequent updates have only allowed me to connect via USB. All the LEDs go out on the DS3 until I reboot the computer. I am unsure as to how to get terminal output to help debug, that would be great. Thanks.

---

### Post by falkTX on 2009-08-28
> **sparkix said:**
> Your application window is too big to fit completely on my display resolution (1024 x 600).  Since netbooks might be a significant portion of the users, it would be nice if they didn't have to pan the window around using alt+drag.  Just a thought.

The minimum I've tested my app was *x768, as I thought it was the minimum possible. Seems like it's not.

I'll work on this in 0.4.1

Thanks for the report

---

### Post by falkTX on 2009-08-28
> **Polk1986 said:**
> I have been unable to pair my DS3 since the first update to 0.4 and the subsequent updates have only allowed me to connect via USB. All the LEDs go out on the DS3 until I reboot the computer. I am unsure as to how to get terminal output to help debug, that would be great. Thanks.

What's your Linux/Ubuntu version? (usually should be Jaunty 32bit)

You can see the logging by doing:
```
sixad --stop
sixad
```

I know sixad (the driver that makes the connection) is unable to build on PS3, but I'm guessing you're just using a normal Ubuntu version, which should connect fine.

Please run that 2 commands and check if any connection is made (it may take a little longer to connect than usual)

---

### Post by Polk1986 on 2009-08-29
I am running Jaunty 32 bit (unfortunately some of the drivers for my computer are not available in the 64 bit variety).

When run from the terminal, everything seems to go well, and I was able to get it to connect once after a reboot immediately after the terminal start. However, I am unable to reconnect the DS3 after disconnecting via the GUI and attempting to reconnect. I have tried with and without the systray enabled and it didn't make a noticeable difference to me. 

Thanks for the terminal code, so I can now use my controller again. The terminal just says it has connected, so I didn't bother pasting it. The GUI shows the DS3 intermittently. It will show up and the "test" button says the device is working, and then it promptly disappears again, all the while flashing all 4 of the LEDs. I am not really sure how else to explain it.

I'd just like to say that I really love the program and am really excited about all the new features in 0.4 . Thanks for all the work!

---

### Post by falkTX on 2009-08-29
> **Polk1986 said:**
> I am running Jaunty 32 bit (unfortunately some of the drivers for my computer are not available in the 64 bit variety).

When run from the terminal, everything seems to go well, and I was able to get it to connect once after a reboot immediately after the terminal start. However, I am unable to reconnect the DS3 after disconnecting via the GUI and attempting to reconnect. I have tried with and without the systray enabled and it didn't make a noticeable difference to me. 

Thanks for the terminal code, so I can now use my controller again. The terminal just says it has connected, so I didn't bother pasting it. The GUI shows the DS3 intermittently. It will show up and the "test" button says the device is working, and then it promptly disappears again, all the while flashing all 4 of the LEDs. I am not really sure how else to explain it.

I'd just like to say that I really love the program and am really excited about all the new features in 0.4 . Thanks for all the work!

This must be something with the udev rule.
I think I'll add an option to QtSixA to force the connection, just for people that can't seem to connect it automatically

---

### Post by falkTX on 2009-08-29
**Update:**
[SIZE="3"]The final 0.4.0 is here![/SIZE]

Sorry but right now I don't have the time to write much.

But I can say that the new sixad update now brings pre-compiled binaries (for users with build problems).

Since I'm using a 64bit installation, please test out if the new update works for you - run:
```
sixad
```
If it says it's already running, good.

I need testing from 32bit, PowerPC (Macs?) and PowerPC64 (PS3).


Thanks, see you guys soon.

---

### Post by falkTX on 2009-09-02
**Update:** v0.4.1 is already here! - changelog:
    - Show proper info when asking for password (kdesudo and gksu)
    - Fixed an issue that caused sixad not to auto-start on some systems
    - Re-read configuration file when showing preferences
    - sixad can now be configured (file is - /etc/default/sixad)
    - Notify group has been moved to "Preferences"
    - It's now possible to configure sixad in the GUI ("Preferences" -> "sixad")
    - Associate "pitch/roll/yaw/gravity" names to the accelerometer and gyro
    - "Change Input Profiles" menu is now available (also on systray)
    - Clicking on the systray icon shows/hides main window (only if Qt >= 4.4.0)
    - Misc improvements to systray icon
    - Some other very small fixes


The major feature is that you can now configure sixad (options->prefs->sixad)

I still need to hear from you guys, if sixad is working for you (32bit and PPC users!)

After the upgrade, just do:
```
sixad
```
If it doesn't show errors or doesn't crash when a device is connected, then it means it compiled fine. I don't expect that to happen for 32 and 64bit, but I'm not so sure about PowerPC/PS3 users - so please test out this.

---

### Post by aatu_kanifani on 2009-09-03
Hmm, on my computer/installation it allows to go to Options/Preferences only once. If I try to click it again, it does nothing. I removed "sixad" and "qt-sixa" through synaptic, then installed it again through terminal, after which the GUI allows me to go to the preferences again (but still only once).

Furthermore, if I tried connecting through GUI on the version 0.4.0, it constantly dropped the connection for me (gave only 0% or 100%) and kept graying out/freezing. But if I ran "sixad" from terminal, it kept the connection on and gave anything from 27% to 40%. There were some problems getting for example zsnes working with it, but I think it was because the motion sensing kept giving different input values all the time. But after changing profile to "Fake Joystick", it was OK.

In the 0.4.1 version it seems to give only 0% or 100% and dropping connection constantly, with or without terminal command. And judging by the lack of others' comments, I'm probably alone with my problems. Maybe something went wrong?


Ps. Using Ubuntu 9.04 32bit and Dualshock3 (but I assume it doesn't matter). And you're doing a great job!

---

### Post by falkTX on 2009-09-03
> **aatu_kanifani said:**
> Hmm, on my computer/installation it allows to go to Options/Preferences only once. If I try to click it again, it does nothing. I removed "sixad" and "qt-sixa" through synaptic, then installed it again through terminal, after which the GUI allows me to go to the preferences again (but still only once).
I released an update, but still, can you run:
```
qt-sixa
```
and check if that still happens to you?

> **aatu_kanifani said:**
> Furthermore, if I tried connecting through GUI on the version 0.4.0, it constantly dropped the connection for me (gave only 0% or 100%) and kept graying out/freezing. But if I ran "sixad" from terminal, it kept the connection on and gave anything from 27% to 40%.
That must be some problem with the auto-detection rules. I've added an option to force the connection, you should try it

> **aatu_kanifani said:**
> There were some problems getting for example zsnes working with it, but I think it was because the motion sensing kept giving different input values all the time. But after changing profile to "Fake Joystick", it was OK.
If the preferences don't crash on you anymore, use it to disable axis/accelerometers if you want. I know it will be "usefull to disable features"

> **aatu_kanifani said:**
> In the 0.4.1 version it seems to give only 0% or 100% and dropping connection constantly, with or without terminal command. And judging by the lack of others' comments, I'm probably alone with my problems. Maybe something went wrong?
I think that maybe there's a little problem with DualShock3...
can you run:
```
hcitool name XX:XX:XX:XX:XX
```
*(where XX... is your DS3 adress [use 'hcitool con' to find it])*
Then post here the complete output (exactly as it prints)


> **aatu_kanifani said:**
> Ps. Using Ubuntu 9.04 32bit and Dualshock3 (but I assume it doesn't matter). And you're doing a great job!
Maybe it matters if 'hcitool name ....' gives a different output from a Sixaxis.

---

### Post by falkTX on 2009-09-03
**Update:** *(copied from changelog: )*
  * Added "Force Connect" action to tasks and systray menu
  * Re-worked the systray tooltip
  * Auto-stop sixad when shutting down



I won't have too much time to work on this after next week (vacations are over...), but I'll still update QtSixA/sixad as much as I can.
I started negotiating for a keypad, so I should get a one soon - which means full support for it.

I also started a thread on the blog for making a list of all PS3-hardware stuff that we can find. Visit it ([falktx.blogspot.com]("http://falktx.blogspot.com")) if you want to participate

---

### Post by janlugt on 2009-09-04
Great work, falkTX! I'm currently using your program together with VTK (Visualization ToolKit) to create interactive 3d-visualizations for a course I'm currently following. It works great!
Today I installed Ubuntu on a separate USB drive so I can run it from there instead of in a virtual machine due to OpenGL performance. Of course I wanted to install qt-sixa on this installation too (which is 64-bit instead of the 32-bit VM), but it gave me an error while downloading the package.
The package sixad_0.3-falktx1_amd64.deb has a size mismatch. Can you check the files are correctly uploaded to your host?

Regards,
Jan

---

### Post by nxmehta on 2009-09-04
I'm having big problems with the latest package.  Running Jaunty 32-bit.  Here's the error when trying to apt-get upgrade:

```

Preparing to replace sixad 0.3-falktx1 (using .../sixad_0.3-falktx1_i386.deb) ...
/var/lib/dpkg/tmp.ci/preinst: line 4: /etc/init.d/sixad: No such file or directory
dpkg: error processing /var/cache/apt/archives/sixad_0.3-falktx1_i386.deb (--unpack):
 subprocess pre-installation script returned error exit status 127
/var/lib/dpkg/tmp.ci/postrm: line 4: sixad: command not found
dpkg: error while cleaning up:
 subprocess post-removal script returned error exit status 127

```

And when I try to remove sixad:

```

The following packages will be REMOVED:
  sixad*
0 upgraded, 0 newly installed, 1 to remove and 2 not upgraded.
1 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
dpkg: error processing sixad (--purge):
 Package is in a very bad inconsistent state - you should
 reinstall it before attempting a removal.
Errors were encountered while processing:
 sixad
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

Not good... :(

---

### Post by LazarusHC on 2009-09-04
I'm having the same problem.:(

---

### Post by aatu_kanifani on 2009-09-05
@falkTX:

Sorry it took this long. I tried another sixaxis connection method, which basically messed up my computer, because I chose to "hold" bluez-compat package, as per instructed by them as optional. But I finally got it out of my system. (And bluez-compat is not in "hold" anymore.)

When now re-installing, I got the same errors as nxmehta. And now it doesn't let me go to Preferences at all.

When I run qt-sixa, it opens the GUI normally (terminal output remains clear). When I try to go to Preferences, it gives this:

```
File "/usr/share/qt-sixa/gui/main.pyw", line 1765, in func_Prefs
    QtSixA_Prefs_Window().exec_()
  File "/usr/share/qt-sixa/gui/main.pyw", line 176, in __init__
    sixad_config_axis = sixad_file[5]
IndexError: list index out of range
```

When I select Force Connection:
```
sh: sixad: not found
```


When I try to connect, it gives this five times:
```
Traceback (most recent call last):
  File "/usr/share/qt-sixa/gui/main.pyw", line 1381, in func_Refresh
    self.func_UpdateSixaxisStats()
  File "/usr/share/qt-sixa/gui/main.pyw", line 1470, in func_UpdateSixaxisStats
    self.SixaxisBatQ = commands.getoutput("hcidump "+"-R "+"-O '"+self.selected_hidd_number+"' "+"| "+"head "+"-n "+"5 "+"| "+"tail "+"-n "+"1 "+"| "+"awk "+"'{printf$1}' "+"& "+"sleep "+"0.001 "+"&& "+"killall "+"hcidump "+"> "+"/dev/null")
  File "/usr/lib/python2.6/commands.py", line 46, in getoutput
    return getstatusoutput(cmd)[1]
  File "/usr/lib/python2.6/commands.py", line 56, in getstatusoutput
    text = pipe.read()
IOError: [Errno 4] Interrupted system call
```


hcitool con (while "trying" to connect, otherwise gives nothing):
```
Connections:
	> ACL 00:23:06:8E:9A:DB handle 11 state 1 lm SLAVE
```

hcitool name 00:23:06:8E:9A:DB (while "trying" to connect):
```
PLAYSTATION(R)3 Controller
```

PS. The controller works with btsix on Windows, and I have gotten it to work with your methods also at some point, so it should be compatible. Additionally, it should be genuine Dualshock3 (black, European). Though not "original", meaning it didn't come with a PS3, and was thus bought separately.

PPS. It seems the "sixad" isn't installed properly anymore. It shows up in synaptic as pending for upgrade, but isn't able to do so. Maybe that's behind all these new problems...?

---

### Post by falkTX on 2009-09-05
**Update:** *(0.4.2)*
  * sixad now supports hidraw devices (usage: sixad --raw <hidraw device>)
  * Support sixad preferences (except LEDs) in sixad-raw
  * sixad-raw is now implemented in the GUI
  * Fixed some debian rules for sixad

Sorry for the bad last update - that should be fixed now.
Meanwhile, I've installed Jaunty on VirtualBox, so I can test both Jaunty (I use Karmic already), and 32bit (I use x64).

Please report if sixad updates fines for you

---

### Post by refried on 2009-09-05
```

Unpacking sixad (from .../sixad_0.3-falktx2_powerpc.deb) ...
dpkg: error processing /var/cache/apt/archives/sixad_0.3-falktx2_powerpc.deb (--unpack):
 subprocess new pre-installation script returned error exit status 1
Errors were encountered while processing:
 /var/cache/apt/archives/sixad_0.3-falktx2_powerpc.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

Any suggestions?  I dont see anything actually wrong with the preinst script, I  run the individual commands without any error output...

---

### Post by nxmehta on 2009-09-05
> **refried said:**
> ```

Unpacking sixad (from .../sixad_0.3-falktx2_powerpc.deb) ...
dpkg: error processing /var/cache/apt/archives/sixad_0.3-falktx2_powerpc.deb (--unpack):
 subprocess new pre-installation script returned error exit status 1
Errors were encountered while processing:
 /var/cache/apt/archives/sixad_0.3-falktx2_powerpc.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

Any suggestions?  I dont see anything actually wrong with the preinst script, I  run the individual commands without any error output...

I get the same error too.  Jaunty 32-bit.

---

### Post by refried on 2009-09-06
Also:

```
arya@lrrr:/etc/init.d$ sudo /etc/init.d/sixad start
 * Starting sixad
   ...done.
arya@lrrr:/etc/init.d$ /usr/bin/sixad-bin: 1: Syntax error: word unexpected (expecting ")")
less `which sixad-bin`
"/usr/bin/sixad-bin" may be a binary file.  See it anyway? 
arya@lrrr:/etc/init.d$ sixad-bin --help
-bash: /usr/bin/sixad-bin: cannot execute binary file

```This is Karmic/ps3.

Perhaps this explains why the devices don't associate for me at all unless i load the "old modules"?

---

### Post by aatu_kanifani on 2009-09-06
Same unpacking error output here too with i386. I even tried it on a freshly installed Ubuntu on my laptop. It seems the sixad-package (currently: sixad_0.3-falktx2_i386.deb) won't install properly. At all, really. The /etc/init.d/sixad doesn't even exist on my computer. If I run sixad on terminal, it gives this:

```
bash: sixad: command not found
```

But yes, the "Start Old Modules"-method seems to work. But I also noticed some sort of performance/incompatibility issues with the qt-sixa and sound. If I have the GUI running (not even controller connected), and then play some music, the sound skips every now and then (every 5 seconds or so). Even though CPU usage is only few percents. Using ALSA.

PS. Is anybody else having problems going to the preferences? Neither my laptop nor desktop computer would let me do that... And the laptop was a fresh install. What about the sound issues?

---

### Post by falkTX on 2009-09-07
**Update:** *(changelog)*
  * Really fix sixad debian rules
  * Fix QtSixA 'out-of-range' configuration file issues
  * Temporarily disabled 'Advanced'/'Signal Quality Actions' (needs some work)


Sorry guys for the recent errors. I feel like you need an explanation, so here it is:
When updating, sixad needs to be stopped (so the binary file can be replaced). The usuall "killall sixad" will not work, so I started using "pkill -KILL sixad" to terminate the process. The thing is, 'pkill' never prints any information, even when the process is not running. Usually that is good, but in this case it returns, silently, and exit code '-1', which make the package un-installable. To solve this I just override the output to be always "1" (or "true") - 'pkill -KILL sixad || true'. This solves the problem for sixad installation.
However, it still doesn't compile on PowerPC because of a incompatible 'libbluetooth.so' binary file (needs to be linked to that when compiling). I think we need to re-compile bluez just to get the right file... Anyone with a PowerPC machine or PS3 is welcome to contribute

For the QtSixA preferences, it just the configuration that is missing one last option. I actually did that about 1 month ago, but since no one reported a bug... This release fixes the configuration/preferences stuff.

---

### Post by falkTX on 2009-09-07
**Update:**

I found a pre-compiled libbluetooth.so.3 for PPC64 in the openSUSE repos.
Guess what? sixad compiles now for PowerPC/PS3.

I've updated my repo and sixad should now run on PPC/PS3 machines

---

### Post by aatu_kanifani on 2009-09-07
The terminal installation gave these warnings:
```
The following packages have unmet dependencies:
  qt-sixa: Depends: sixad (>= 0.3) but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).
```

I don't know what it's called, but it added a "red circle with white horizontal line"-icon to the tray. I checked that, and it said there's one broken package that needs to be updated. It updated the sixad and qt-sixa without problems (Yay!).

Well, the GUI started OK. I tried connecting with PS-button. No connection. I decided to check the preferences (before trying through terminal). It let me go to preferences (Yay!). Fiddled with options. Applied changes. Stopped sixad through the Tasks-menu as instructed. Exit and restart the program. It gives the "QtSixA has been updated to 0.4.2"-popup, but won't show the GUI anymore. If I run qt-sixa from the terminal, it gives this:

```
File "/usr/share/qt-sixa/gui/main.pyw", line 1899, in <module>
    QtSixA = Main_QtSixA_Window()
  File "/usr/share/qt-sixa/gui/main.pyw", line 863, in __init__
    self.createTrayIcon()
  File "/usr/share/qt-sixa/gui/main.pyw", line 1239, in createTrayIcon
    if (QtCore.qVersion() >= "4.4.0"): self.trayIcon.activated.connect(self.func_Systray_Clicked) #Not available on older versions
AttributeError: activated
```

Running sixad from terminal works, though. Luckily I disabled accelerometers etc. from the preferences when I were still able to get there, so now it recognizes the right inputs. (Or maybe it's because it seems to have enabled Gnome-profile by default or something. At least the sticks seem to emulate mouse, and buttons output keyboard presses.) Through terminal there aren't even any sound issues. (Or at least I haven't run into them yet.)

---

### Post by falkTX on 2009-09-07
Thanks for the report.
This issue:
```
File "/usr/share/qt-sixa/gui/main.pyw", line 1899, in <module>
    QtSixA = Main_QtSixA_Window()
  File "/usr/share/qt-sixa/gui/main.pyw", line 863, in __init__
    self.createTrayIcon()
  File "/usr/share/qt-sixa/gui/main.pyw", line 1239, in createTrayIcon
    if (QtCore.qVersion() >= "4.4.0"): self.trayIcon.activated.connect(self.func_Systray_Clicked) #Not available on older versions
AttributeError: activated
```is not actually an issue. You seem to be using an old PyQt version that doesn't support "activated" commands. I'm at work right now, but I'll look for a solution. Check again for the next hour and it should be fixed

---

### Post by falkTX on 2009-09-07
**Update:**
The bug has been fixed (I think).
Users of PyQt >=4.4 will get the double click on systray icon to show/hide main GUI. Users below 4.4 won't get this feature

---

### Post by aatu_kanifani on 2009-09-07
Hmm, still won't show the GUI. And I don't have a tray icon at all (I think I never had, really)...

Here's the terminal output of qt-sixa:
```
Using PyQt version 4.5.0
Traceback (most recent call last):
  File "/usr/share/qt-sixa/gui/main.pyw", line 1901, in <module>
    QtSixA = Main_QtSixA_Window()
  File "/usr/share/qt-sixa/gui/main.pyw", line 865, in __init__
    self.createTrayIcon()
  File "/usr/share/qt-sixa/gui/main.pyw", line 1241, in createTrayIcon
    if (QtCore.qVersion() >= "4.4.0") and QtCore.QT_VERSION > 0x040400: self.trayIcon.activated.connect(self.func_Systray_Clicked) #Not available on older versions
AttributeError: activated
```

My system should be updated to the latest. "python-qt4" shows its version as 4.4.4 on synaptic. Is that the package I should check?

---

### Post by refried on 2009-09-07
qt-sixa 0.4.2-falktx3

Karmic, PS3 -- willing to do whatever to troubleshoot.

```
arya@lrrr:~$ sixad-bin 
sixad-bin: error while loading shared libraries: libbluetooth.so.3: cannot open shared object file: No such file or directory
arya@lrrr:~$ sudo apt-get install libbluetooth3
Reading package lists... Done
Building dependency tree       
Reading state information... Done
libbluetooth3 is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 105 not upgraded.
arya@lrrr:~$ locate libbluetooth.so.3
/usr/lib/libbluetooth.so.3
/usr/lib/libbluetooth.so.3.4.0
arya@lrrr:~$ 

```*shrug*

Edit:
```
arya@lrrr:~$ LD_LIBRARY_PATH=/usr/lib/ sixad-bin
sixad-bin: error while loading shared libraries: libbluetooth.so.3: wrong ELF class: ELFCLASS32

```

---

### Post by falkTX on 2009-09-08
> **aatu_kanifani said:**
> Hmm, still won't show the GUI. And I don't have a tray icon at all (I think I never had, really)...

Here's the terminal output of qt-sixa:
```
Using PyQt version 4.5.0
Traceback (most recent call last):
  File "/usr/share/qt-sixa/gui/main.pyw", line 1901, in <module>
    QtSixA = Main_QtSixA_Window()
  File "/usr/share/qt-sixa/gui/main.pyw", line 865, in __init__
    self.createTrayIcon()
  File "/usr/share/qt-sixa/gui/main.pyw", line 1241, in createTrayIcon
    if (QtCore.qVersion() >= "4.4.0") and QtCore.QT_VERSION > 0x040400: self.trayIcon.activated.connect(self.func_Systray_Clicked) #Not available on older versions
AttributeError: activated
```

My system should be updated to the latest. "python-qt4" shows its version as 4.4.4 on synaptic. Is that the package I should check?
That is indeed the version I needed to know. Now the problem is that, when I was using the exactly same version (fresh Jaunty install), this error doesn't occur. This is strange...

I'm already looking for a solution, will post update soon

---

### Post by falkTX on 2009-09-08
> **refried said:**
> qt-sixa 0.4.2-falktx3

Karmic, PS3 -- willing to do whatever to troubleshoot.

```
arya@lrrr:~$ sixad-bin 
sixad-bin: error while loading shared libraries: libbluetooth.so.3: cannot open shared object file: No such file or directory
arya@lrrr:~$ sudo apt-get install libbluetooth3
Reading package lists... Done
Building dependency tree       
Reading state information... Done
libbluetooth3 is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 105 not upgraded.
arya@lrrr:~$ locate libbluetooth.so.3
/usr/lib/libbluetooth.so.3
/usr/lib/libbluetooth.so.3.4.0
arya@lrrr:~$ 

```*shrug*

Edit:
```
arya@lrrr:~$ LD_LIBRARY_PATH=/usr/lib/ sixad-bin
sixad-bin: error while loading shared libraries: libbluetooth.so.3: wrong ELF class: ELFCLASS32

```

I'll just include the libbluetooth I used to compile sixad, wait for update

---

### Post by falkTX on 2009-09-08
**Update:** *(changelog: )*

  * Fixed random hcidump error (killing it too soon)
  * Fixed PyQt check (was checking for global Qt version instead)
  * Show main Qt and PyQt versions on startup (on terminal, even with gksu/kdesudo)
  * "Signal Quality Actions" is back
  * Updated the "About" dialog
  * sixad builds on PowerPC now (needs testing)
  * (Maybe) Fixed systray "activated" error (disabling it for some systems)


Not sure if the 2 bugs reported ('activated' and sixad libbluetooth) are really fixed or not (but it works for me). Please re-report if those have been fixed already or not

---

### Post by refried on 2009-09-08
> **falkTX said:**
> **Update:** *(changelog: )*
* sixad builds on PowerPC now (needs testing)
  

```
Setting up sixad (0.3-falktx5) ...
/usr/bin/sixad: line 7: /usr/lib/: is a directory

Setting up qt-sixa (0.4.2-falktx4) ...

```(should be colon-separated, not semicolon)
but even with that fix, I get```
sixad-bin: error while loading shared libraries: libbluetooth.so.3: cannot open shared object file: No such file or directory

```Do you want me to compile something for you?

Edit:
```
arya@lrrr:~$ LD_LIBRARY_PATH=/usr/lib/qt-sixa sixad
sixad-bin: error while loading shared libraries: libbluetooth.so.3: cannot open shared object file: No such file or directory
arya@lrrr:~$ find /usr/lib/qt-sixa/
/usr/lib/qt-sixa/
/usr/lib/qt-sixa/libbluetooth.so.3
arya@lrrr:~$ LD_LIBRARY_PATH=/usr/lib/qt-sixa/ sixad
sixad-bin: error while loading shared libraries: libbluetooth.so.3: cannot open shared object file: No such file or directory
arya@lrrr:~$ LD_LIBRARY_PATH=/usr/lib/qt-sixa/ sixad-bin
sixad-bin: can't bind to psm 17: Permission denied
Will Use LED #1, arya@lrrr:~$ LD_LIBRARY_PATH=/usr/lib/qt-sixa/:/usr/lib sixad-bin
sixad-bin: can't bind to psm 17: Permission denied
Will Use LED #1, arya@lrrr:~$ sudo LD_LIBRARY_PATH=/usr/lib/qt-sixa/:/usr/lib sixad-bin
Will Use LED #1, Press the PS button now

```

---

### Post by falkTX on 2009-09-08
> **refried said:**
> (should be colon-separated, not semicolon)
Really useful, thanks for pointing that out. Fixed now

> **refried said:**
> Edit: *(...)*
```
arya@lrrr:~$ sudo LD_LIBRARY_PATH=/usr/lib/qt-sixa/:/usr/lib sixad-bin
Will Use LED #1, Press the PS button now

```

The last part means sixad is now running on PowerPC machines.
I've updated sixad already.

Can you connect a Sixaxis and see if there are events in:
```
jstest /dev/input/js0
```

---

### Post by refried on 2009-09-08
> **falkTX said:**
> 
Can you connect a Sixaxis and see if there are events in:
```
jstest /dev/input/js0
```

```

arya@lrrr:~$ jstest /dev/input/js3
Driver version is 2.1.0.
Joystick (PLAYSTATION(R)3 Controller (00:19:C1:6A:73:B3)) has 26 axes (X, Y, Z, Rx, Ry, Rz, Throttle, Rudder, Wheel, Gas, Brake, ?, ?, ?, ?, ?, Hat0X, Hat0Y, Hat1X, Hat1Y, Hat2X, Hat2Y, Hat3X, Hat3Y, ?, ?)
Segmentation fault (core dumped)

```  It does work in snes9x though.

On a separate note, when I connect a 2nd controller, sixad starts spewing garbage to the console:

[http://pastebin.com/f6ee773eb](http://pastebin.com/f6ee773eb)

---

### Post by falkTX on 2009-09-08
> **refried said:**
> ```

arya@lrrr:~$ jstest /dev/input/js3
Driver version is 2.1.0.
Joystick (PLAYSTATION(R)3 Controller (00:19:C1:6A:73:B3)) has 26 axes (X, Y, Z, Rx, Ry, Rz, Throttle, Rudder, Wheel, Gas, Brake, ?, ?, ?, ?, ?, Hat0X, Hat0Y, Hat1X, Hat1Y, Hat2X, Hat2Y, Hat3X, Hat3Y, ?, ?)
Segmentation fault (core dumped)

```  It does work in snes9x though.

On a separate note, when I connect a 2nd controller, sixad starts spewing garbage to the console:

[http://pastebin.com/f6ee773eb](http://pastebin.com/f6ee773eb)

Nice to know it's working.

I'll see what I can do with that garbage little bug, but I can't promise anything, since I only have 1 controller.
Does it increase CPU usage when printing that?

--------------
Edit: did you used all stuff from sixad (like accel/speed) or you disabled anything?
Knowing that will help me fix it.
*(If you don't mind, can you check various sixad settings and check in which ones sixad prints that garbage?)*

---

### Post by refried on 2009-09-08
> **falkTX said:**
> 
Does it increase CPU usage when printing that?

CPU usage goes from 1% to 3%.

[quote=falkTX]
Edit: did you used all stuff from sixad (like accel/speed) or you disabled anything?
Knowing that will help me fix it.
[/quote][I]
I didn't change any of the arguments in sixad

[quote=falkTX]
(If you don't mind, can you check various sixad settings and check in which ones sixad prints that garbage?)[/quote][/I]

It looks like maybe garbage prints for any input on the second controller -- i.e. i have set
```
LED_n=1
LED_plus=1
LED_anim=0
Enable_buttons=1
Enable_sbuttons=0
Enable_axis=0
Enable_accel=0
Enable_accon=0
Enable_speed=0
Enable_gyro=0
```and I get output from sixad when i press or release any button.  perhaps the stream of garbage before was analog inputs?

Side note:
```

LD_LIBRARY_PATH=foo sudo command
```doesn't seem to work -- the environment isn't passed through to the sudo environment
```
arya@lrrr:~$ FOO=test sudo bash
root@lrrr:~# echo $FOO

root@lrrr:~#
``````
arya@lrrr:/etc/init.d$ LD_LIBRARY_PATH=/usr/lib/qt-sixa/:/usr/lib sudo sixad-bin
sixad-bin: error while loading shared libraries: libbluetooth.so.3: cannot open shared object file: No such file or directory

arya@lrrr:/etc/init.d$ sudo LD_LIBRARY_PATH=/usr/lib/qt-sixa/:/usr/lib sixad-bin
Will Use LED #1, Press the PS button now
^C
```Try "sudo LD_LIBRARY_PATH=foo command" instead
or...  find a way to link against the right library, and get rid of the /usr/lib/qt-sixa dependency...

Thanks,
Arya

---

### Post by falkTX on 2009-09-09
> **refried said:**
> CPU usage goes from 1% to 3%.

[I]
I didn't change any of the arguments in sixad

[/I]

It looks like maybe garbage prints for any input on the second controller -- i.e. i have set
```
LED_n=1
LED_plus=1
LED_anim=0
Enable_buttons=1
Enable_sbuttons=0
Enable_axis=0
Enable_accel=0
Enable_accon=0
Enable_speed=0
Enable_gyro=0
```and I get output from sixad when i press or release any button.  perhaps the stream of garbage before was analog inputs?

Side note:
```

LD_LIBRARY_PATH=foo sudo command
```doesn't seem to work -- the environment isn't passed through to the sudo environment
```
arya@lrrr:~$ FOO=test sudo bash
root@lrrr:~# echo $FOO

root@lrrr:~#
``````
arya@lrrr:/etc/init.d$ LD_LIBRARY_PATH=/usr/lib/qt-sixa/:/usr/lib sudo sixad-bin
sixad-bin: error while loading shared libraries: libbluetooth.so.3: cannot open shared object file: No such file or directory

arya@lrrr:/etc/init.d$ sudo LD_LIBRARY_PATH=/usr/lib/qt-sixa/:/usr/lib sixad-bin
Will Use LED #1, Press the PS button now
^C
```Try "sudo LD_LIBRARY_PATH=foo command" instead
or...  find a way to link against the right library, and get rid of the /usr/lib/qt-sixa dependency...

Thanks,
Arya

The LD_... stuff has already been set inside sixad, so running
```
sixad
```*(and this is the most important command)*
should just work.

I've already updated sixad, so maybe that garbage stuff won't appear (not sure)

---

### Post by falkTX on 2009-09-09
**Update:** *(changelog: )*
  * Fixed bug when saving a file using old PyQt version
  [Actually a PyQt bug, now fixed using "echo 'CONF&VARS' > /to/path"]
  * Restore default configuration files if broken (due to last bug)
  * Fixed a notification bug when "$HOME/.config/autostart/" didn't existed

The keypad is coming. I set a deadline for full keypad support - 21 September. So, before day 21, the keypad will already be supported in bluetooth mode. Not sure about USB, but shouldn't take much longer than bluetooth

---

### Post by aatu_kanifani on 2009-09-09
I thought I wrote this already, but seems I didn't send it or something. Well, this was the case yesterday:

> The GUI works again. First it seemed to drop the connection, but then picked it up again, and kept it connected. Now it also shows signal quality correctly. Tray icon is also showing. The GUI still seems to cause some audio problems (even if using Old Modules), and it seems sluggish sometimes. And the preferences won't work, either.

Terminal output for qt-sixa:
```
Main Qt version: 4.5.0
Python-Qt version: 4.4.4
Your system doesn't supoort double-click on systray
```

This is the output when trying preferences:
```
Traceback (most recent call last):
  File "/usr/share/qt-sixa/gui/main.pyw", line 1775, in func_Prefs
    QtSixA_Prefs_Window().exec_()
  File "/usr/share/qt-sixa/gui/main.pyw", line 188, in __init__
    if (int(sixad_config_led_n) == -1):
ValueError: invalid literal for int() with base 10: '/etc/default/sixad:'
```

If I run sixad from terminal, the audio problems don't exist. Maybe there's something broken with my Qt?

Changes in the newest version:
It doesn't say anything about double-click and the lines changed to 1774 and 187. And the tray icon disappeared.

It also seems that now even if I exit the GUI and run sixad from terminal, it tells sixad is still running. And if I press the PS-button to connect (without GUI, because GUI still gives audio problems to me) it automatically uses LED #2. And because sixad isn't "actively running" on terminal, I have to use the GUI to disconnect. Is there a manual command for sixad to disconnect?

I'm gonna go try this with my brother to see how it plays out with two controllers.

---

### Post by falkTX on 2009-09-09
> **aatu_kanifani said:**
> Changes in the newest version:
It doesn't say anything about double-click and the lines changed to 1774 and 187. And the tray icon disappeared.

It also seems that now even if I exit the GUI and run sixad from terminal, it tells sixad is still running. And if I press the PS-button to connect (without GUI, because GUI still gives audio problems to me) it automatically uses LED #2. And because sixad isn't "actively running" on terminal, I have to use the GUI to disconnect. Is there a manual command for sixad to disconnect?

I'm gonna go try this with my brother to see how it plays out with two controllers.

The configuration files were broken and were replaced automatically on update.
sixad is intencionally running on background. To get sixad output to terminal you'll have to stop it and start it manually:
```
sixad --stop
sixad
```

As soon as I get a keypad, I'll be able to test 2 devices too


For everyone experiencing errors when starting 'qt-sixa', this can be fixed with:
*(be sure to have the latest sixad/qtsixa packages)*
```
cp /usr/share/qt-sixa/qtsixa.conf.bak /usr/share/qt-sixa/qtsixa.conf
cp /usr/share/qt-sixa/sixad.default.bak /etc/default/sixad
```

---

### Post by refried on 2009-09-09
> **falkTX said:**
> The LD_... stuff has already been set inside sixad, so running
```
sixad
```*(and this is the most important command)*
should just work.

I've already updated sixad, so maybe that garbage stuff won't appear (not sure)

That's not the right fix, you have to give the environment variables before each command;  sudo LD_...  by itself (line 126) won't do anything.

```
Setting up sixad (0.3-falktx7) ...
arya@lrrr:~$ sixad
usage: sudo [-n] -h | -K | -k | -L | -V | -v
usage: sudo -l[l] [-AnS] [-g groupname|#gid] [-U username] [-u username|#uid] [-g groupname|#gid] [command]
usage: sudo [-AbEHnPS] [-C fd] [-g groupname|#gid] [-p prompt] [-u username|#uid] [-g groupname|#gid] [VAR=value] [-i|-s] [<command>]
usage: sudo -e [-AnS] [-C fd] [-g groupname|#gid] [-p prompt] [-u username|#uid] file ...
sixad-bin: error while loading shared libraries: libbluetooth.so.3: cannot open shared object file: No such file or directory
arya@lrrr:~$ 
```

Try "sudo LD_LIBRARY_PATH=foo sixad" like I said in my previous post, or even better: let's link against the standard libbluetooth.so.3

---

### Post by falkTX on 2009-09-09
> **refried said:**
> Try "sudo LD_LIBRARY_PATH=foo sixad" like I said in my previous post, or even better: let's link against the standard libbluetooth.so.3

Dammit...

Such mistakes for a programmer :lolflag:

But it's *really* fixed now (updated)

---

### Post by refried on 2009-09-09
> **falkTX said:**
> Dammit...

Such mistakes for a programmer :lolflag:

But it's *really* fixed now (updated)

Thanks.

Now to tackle two controllers  (lots of output is still generated when connecting the 2nd)
Why don't you let me debug it, since I have two controllers?

---

### Post by falkTX on 2009-09-09
> **refried said:**
> Thanks.

Now to tackle two controllers  (lots of output is still generated when connecting the 2nd)
Why don't you let me debug it, since I have two controllers?

You can access the full code in my repo, but I save you some time and uploaded it here.

Feel free to do any modifications you want, just post the patch/diff file when done.

Don't use the 'make' stuff, it's specifically for my PC building process.
To compile sixad-bin you can use:
```
gcc -mpowerpc -Wall -O2 sixad.c -o sixad-bin -lbluetooth -L./ppu-gcc/lib
```
Change '-mpowerpc' to '-m64' if you got a uinput error;
You may need to change -L/path/to/libbluetooth.so.3 (folder)

---

### Post by refried on 2009-09-09
> **falkTX said:**
> You can access the full code in my repo, but I save you some time and uploaded it here.

Feel free to do any modifications you want, just post the patch/diff file when done.

Don't use the 'make' stuff, it's specifically for my PC building process.
To compile sixad-bin you can use:
```
gcc -mpowerpc -Wall -O2 sixad.c -o sixad-bin -lbluetooth -L./ppu-gcc/lib
```Change '-mpowerpc' to '-m64' if you got a uinput error;
You may need to change -L/path/to/libbluetooth.so.3 (folder)

Thanks!  Btw, using
```
        ppu-gcc -m32 -Wall -O2 sixad.c -o bins/sixad-bin_powerpc -lbluetooth

```allowed me to link against my Karmic+ps3's libbluetooth (attached), which is evidently 32-bit.

---

### Post by Polk1986 on 2009-09-09
Hey,

I am still only able to connect in terminal. I was wondering if  the "force connection" was available and I'm just missing it, or what the deal is, as I am still unable to autoconnect my controllers. Thanks!

---

### Post by falkTX on 2009-09-10
> **Polk1986 said:**
> Hey,

I am still only able to connect in terminal. I was wondering if  the "force connection" was available and I'm just missing it, or what the deal is, as I am still unable to autoconnect my controllers. Thanks!

The force connection option is in the "Tasks" menu.
Just press it then PS button, and it will connect

---

### Post by aatu_kanifani on 2009-09-10
Everything seems to work now (GUI, preferences, tray icon). The sound issue is still there with the GUI on, but I noticed it doesn't affect all the apps. Opera is OK at least (youtube sounds perfect).

Regarding the two controllers at the same time: I didn't get them to work together either. Every time I connected the second controller, the terminal showed constant activity, even though accelerometers were disabled in the preferences.

But I just now noticed that at least the profiles seem to work better with Force Connection. So next time I go to visit my brother, I'll try it with that also.

Few questions I was wondering:
Does the second tab of the GUI apply to both/all controllers? What about the sixad preferences? Is there a conf file which defines the overrides?

---

### Post by falkTX on 2009-09-10
> **aatu_kanifani said:**
> Few questions I was wondering:
Does the second tab of the GUI apply to both/all controllers? What about the sixad preferences? Is there a conf file which defines the overrides?

It does apply to all controllers (except in "old modules", support dropped).
To override a profile to a specific Sixaxis, use the "Advanced" tab

---

### Post by Polk1986 on 2009-09-10
> **falkTX said:**
> The force connection option is in the "Tasks" menu.
Just press it then PS button, and it will connect

Cool. That fixed it for one controller at least. The second acts connected, lights up the leds, but then doesn't do anything. I presume this is what you and aatu_kanifani have been talking about? Thanks everyone working on the code!

---

### Post by falkTX on 2009-09-11
> **Polk1986 said:**
> Cool. That fixed it for one controller at least. The second acts connected, lights up the leds, but then doesn't do anything. I presume this is what you and aatu_kanifani have been talking about? Thanks everyone working on the code!

Probably there's something wrong with the code when connecting a 2nd controller (I will try to fix this soon, as my keypad is coming...)

But, meanwhile, you can do this trick for 2 controllers:
1 - Stop sixad
2 - Start old modules and connect 1 controller (profiles don't work in this mode)
3 - Force sixad and connect the 2nd Sixaxis

Note that only the 2nd sixaxis can have accelerometers (not mandatory)

---

### Post by falkTX on 2009-09-11
**Update:**
As QtSixA 0.4.2 is now stable, and I still don't have a keypad (will come soon), I began to work on the next QtSixA version.
One thing I was thinking of was to write the GUI in C++ instead of python (python is well-known for being slow). That will make the GUI a lot faster, but it will take me more time to write it.
Anyway, you guys still have 0.4.2 and, of course, I'll try to fix any bugs found on it

Want a preview?
Just download the attachments (you can open the ui file with kuiviewer or QtDesigner)

---

### Post by falkTX on 2009-09-12
**Update:**
I have a Keypad!! - Thanks to everyone that donate for this cause! :D:P::D

I already have the keys working in sixad but the mouse/trackpad looks crazy/jerky (why would we need that if the Sixaxis can be a mouse too?)
Anyway, I the implementation is almost ready and I'll release an update soon.

For the bug recently found (cannot connect 2 controllers), I was able to reproduce it, so that should be fixed soon too.


Thanks for everyone that donated to this project! 
The keypad is really awesome :guitar:

---

### Post by Vantskruv on 2009-09-13
Very nice and thanks for outstanding drivers!

Though I have a question about the acceleration sensors. I'm connecting my PS3 DualShock 3 Sixaxis controller via the USB (not bluetooth), and the acceleration axes doesn't work. Are these axes only supported via bluetooth connection? I've tried testing these axes in Neverball (version 1.5.3), using the "Accelerometers moves table" settings for Neverball in "Game Profiles Tab". Also I've tried setting up the neverballrc config file manually (changing joystick_x and jostick_y to 4 and 5). I've also tried checking the axes with the jstest tool and there are no input from the acceleration axes.

Another public question, is there any graphical GUI for easily test and analyse axes and buttons for joysticks in Ubuntu (in contrast with windows joystick calibration utility)?

---

### Post by Polk1986 on 2009-09-13
> **Vantskruv said:**
> Very nice and thanks for outstanding drivers!

Though I have a question about the acceleration sensors. I'm connecting my PS3 DualShock 3 Sixaxis controller via the USB (not bluetooth), and the acceleration axes doesn't work. Are these axes only supported via bluetooth connection?

Unless something has changed in the last couple updates, the accelerometers only work in BT mode.

---

### Post by Vantskruv on 2009-09-13
Thanks for replying! Anyway, I just want to add I've found a calibration program called *jscalibrator*, not so fancy GUI, but it works monitoring the axes and buttons! :)

Acceleration axis doesn't work, but everything else, so I guess this is not implemented in the drivers for USB-connection.

---

### Post by falkTX on 2009-09-14
> **Vantskruv said:**
> Thanks for replying! Anyway, I just want to add I've found a calibration program called *jscalibrator*, not so fancy GUI, but it works monitoring the axes and buttons! :)

Acceleration axis doesn't work, but everything else, so I guess this is not implemented in the drivers for USB-connection.

The USB accelerometers are supported. They work based on a Sixaxis hidraw.
You can use the GUI, in advanced, 3rd option.
Or you can use:
```
sixad --raw /dev/hidrawX
```
where "X" should be replaced by the Sixaxis hidraw # (use 'dmesg' to find it)

---

### Post by falkTX on 2009-09-14
> **Vantskruv said:**
> I've tried testing these axes in Neverball (version 1.5.3), using the "Accelerometers moves table" settings for Neverball in "Game Profiles Tab". Also I've tried setting up the neverballrc config file manually (changing joystick_x and jostick_y to 4 and 5). I've also tried checking the axes with the jstest tool and there are no input from the acceleration axes.

I assume that you're using the GetDeb version. The 1.5.3-getdeb don't work with joysticks (probably a bug).
You can use karmic/jaunty-backports 1.5.2, which works pretty well with Sixaxis accelerometers.

---

### Post by Xenphor on 2009-09-15
Hi,  First of all I would like to thank you very much for providing an excellent tool that's easy to use. I have been able to connect my dualshock3 via bluetooth using the old module on my ps3. Unfortunately, I have not been able to get any of the input profiles to function which is apparently a problem on the ps3.     

Is there some way I could use another program to make an input file that would work with QtSixA? I am extremely new to all of this so forgive me if this is a dumb question. I would just really like to be able to use my dualshock as a mouse on my ps3. If anyone else knows how I could do this I would really appreciate it. In the past I tried to use xorg.conf to set the inputs but I was unable to get it working.      

Of course if you think you may be close to getting the input profiles to work in qtsixa on ps3 that would also be great :)

---

### Post by falkTX on 2009-09-16
**Update:** *Changelog:*
_qt-sixa (0.4.3-falktx1)_
  * New upstream release:
    - Disabled the "Info" button (causing problems, will be removed/replaced in next version)
    - Enabled Keypad 'signal quality'
    - Fixed typo that made Keypad and Remotes not appear in the list when connected thorugh USB
    - Fixed little bug when trying to check 'signal quality' for a disconnected device
    [When auto-refreshing and user clicks "Disconnect"]
    - Removed Keypad profile option (will not be needed)
    - Moved restore stuff to "Help" menu
    - Removed "Outro" tab
    - Other small fixes to the GUI
    - Test button is now disabled since it's checks are incompatible with the new driver
    - Maybe - Sixaxis profiles *may* work on PS3 now (needs testing)

_sixad (0.4-falktx0)_
  * Major sixad update:
    - Code rewrite now based on "hidd" (from bluez-compat) instead of a custom user code
    - Support for lots of hardware (incluing keypads and imitations of the Sixaxis controller [will use same driver as USB])
    - Ported Sixaxis/DualShock3 special functions to the new code (leds, acceleration, etc)
    - You can connect as many devices as you want!
    - You can now check the 'sixad' activity without using the terminal
    [Open a System Log Viewer and filter the output to "sixad"]


I've pushed myself too much into this, and I haven't slept too much in the past few days. Now I'm sick... :frown:
I hope my work was useful in some way

See you guys soon

*Edit: I just noticed after update that Sixaxis will not raise LED # after a new connection is made. Just something I forgot in the process, will fix it soon*

---

### Post by falkTX on 2009-09-16
Neverball as been updated to 1.5.3 and has fixed the joystick problem.
It should be in GetDeb/PlayDeb soon

EDIT: Even with 1.5.3 it doesn't work...:(
But 1.5.1 works just fine, grab it:
[http://packages.ubuntu.com/search?keywords=neverball&searchon=names&suite=all&section=all](http://packages.ubuntu.com/search?keywords=neverball&searchon=names&suite=all&section=all)
*(you'll also need neverball-data and neverball-common packages)*

---

### Post by Xenphor on 2009-09-16
Well I got the new version and I still can't seem to get the profiles working on ps3. I'm still having to use the old module in case that would make a difference. Of course since I'm new there is a possibility that I'm doing something wrong so if anyone else can get them working on ps3 (9.04) I would be interested to hear about it. Thanks for all the hard work.

---

### Post by falkTX on 2009-09-17
> **Xenphor said:**
> Well I got the new version and I still can't seem to get the profiles working on ps3. I'm still having to use the old module in case that would make a difference. Of course since I'm new there is a possibility that I'm doing something wrong so if anyone else can get them working on ps3 (9.04) I would be interested to hear about it. Thanks for all the hard work.

Sad to hear it's not working :( . I can't really fix this, as I don't have a PS3 to test any small workarounds.

And you don't need the old modules anymore. I've re-written sixad and it's now based on hidd (same code as the old modules)

---

### Post by Xenphor on 2009-09-18
Well as I said before it's probably my fault as I'm still new to all of this; which is why I would greatly appreciate any help from other PS3 owners to get the profiles working.

---

### Post by falkTX on 2009-09-19
**Update:**
I've been working on 0.5.0 already. The most significant changes will be the new GUI layout and the fact that it will be much faster than 0.4.x releases. As soon as it gets usable I'll probably release it on a separate package in my repo (qtsixa-0.5?).

---

### Post by aatu_kanifani on 2009-09-20
Nobody else has said anything about it yet, so:

The two controllers work now. Even the profiles work. Though I have problems when trying to CREATE them (with both desktop and laptop). When trying to save, the GUI simply crashes, and the tray icon disappears. It nevertheless makes the fdi file, but it's not readable (and the size is anything from 176 to 568kB, instead of 2.6kB). The only way I could make it work was to copy one of the original fdi's, rename and gedit them manually, then add that file in the program.

BTW, the "Disconnect All" doesn't work either (I think it worked at some point). Well, this is at least the case when using Force Connection. Terminal only states that bluetooth is started again. The single Disconnect works normally, though.

Using 9.04, 32bit.

---

### Post by falkTX on 2009-09-21
> **aatu_kanifani said:**
> Nobody else has said anything about it yet, so:

The two controllers work now. Even the profiles work. Though I have problems when trying to CREATE them (with both desktop and laptop). When trying to save, the GUI simply crashes, and the tray icon disappears. It nevertheless makes the fdi file, but it's not readable (and the size is anything from 176 to 568kB, instead of 2.6kB). The only way I could make it work was to copy one of the original fdi's, rename and gedit them manually, then add that file in the program.

BTW, the "Disconnect All" doesn't work either (I think it worked at some point). Well, this is at least the case when using Force Connection. Terminal only states that bluetooth is started again. The single Disconnect works normally, though.

Using 9.04, 32bit.

Because I re-wrote the whole sixad driver, some things may not work as before.
I started working on a new version already, most because the GUI, at the moment, fills the entire screen, when I honestly think my app should only be an utility...

The v0.5 will be a serious thing, as I'm planning a sourceforge page and hosting the code at launchpad.
Until then, keep using the "old" GUI and report the bugs you find (many thanks to those who do that!)

Can you upload the profile you created? (may be useful for other users)

---

### Post by aatu_kanifani on 2009-09-22
Here you go, Fake_Joystick_2 (fdi and corresponding picture). Just take the .txt away from the end of the file (forum won't allow me to upload .fdi directly).

I made it so that it can be used simultaneously with the original Fake_Joystick without overlapping. (except the mouse movement, I left that intentionally)

If somebody wants to disable mouse, put the "mode=none" to the MapAxis1...Axis4 lines also.

And thanks again for the great app!

Here's the contents of the fdi-file for those without a forum login:

```
<?xml version="1.0" encoding="UTF-8"?>
<deviceinfo version="0.2">
  <device>
      <!-- Sixaxis configuration for Fake-Joystick Use (Keyboard) -->
      <match key="input.product" contains="PLAYSTATION(R)3 Controller">

        <merge key="input.x11_driver" type="string">joystick</merge>

	<!-- Main Axis. Left=Mouse; Right=Scroll
        -->
        <merge key="input.x11_options.MapAxis1" type="string">mode=relative axis=+2x deadzone=5000</merge>
        <merge key="input.x11_options.MapAxis2" type="string">mode=relative axis=+2y deadzone=5000</merge>
        <merge key="input.x11_options.MapAxis3" type="string">mode=relative axis=+1zx deadzone=7500</merge>
        <merge key="input.x11_options.MapAxis4" type="string">mode=relative axis=+1zy deadzone=7500</merge>
	<merge key="input.x11_options.MapAxis5" type="string">mode=none</merge>
	<merge key="input.x11_options.MapAxis6" type="string">mode=none</merge>
	<merge key="input.x11_options.MapAxis7" type="string">mode=none</merge>
	<merge key="input.x11_options.MapAxis8" type="string">mode=none</merge>
 
	<!-- Select=K; Start=L; PS=I
        -->
        <merge key="input.x11_options.MapButton1" type="string">key=K</merge>
        <merge key="input.x11_options.MapButton2" type="string">key=NoSymbol</merge>
        <merge key="input.x11_options.MapButton3" type="string">key=NoSymbol</merge>p
        <merge key="input.x11_options.MapButton4" type="string">key=L</merge>
        <merge key="input.x11_options.MapButton17" type="string">key=I</merge>

	<!-- Directional keys (Up=G, Down=V, Left=F & Right=B)
        -->
        <merge key="input.x11_options.MapButton5" type="string">key=G</merge>
        <merge key="input.x11_options.MapButton8" type="string">key=F</merge>
        <merge key="input.x11_options.MapButton6" type="string">key=B</merge>
        <merge key="input.x11_options.MapButton7" type="string">key=V</merge>

	<!-- R2=P; L2=Y; R1=O; L1=U
        -->
        <merge key="input.x11_options.MapButton10" type="string">key=P</merge>
        <merge key="input.x11_options.MapButton9" type="string">key=Y</merge>
        <merge key="input.x11_options.MapButton12" type="string">key=O</merge>
        <merge key="input.x11_options.MapButton11" type="string">key=U</merge>

	<!-- Cross=N; Circle=M; Square=H; Triangle=J
        -->

        <merge key="input.x11_options.MapButton15" type="string">key=N</merge>
        <merge key="input.x11_options.MapButton14" type="string">key=M</merge>
        <merge key="input.x11_options.MapButton16" type="string">key=H</merge>
        <merge key="input.x11_options.MapButton13" type="string">key=J</merge>

      </match>
  </device>
</deviceinfo>
```

---

### Post by falkTX on 2009-09-25
**Update:** (changelog) :
```
qtsixa (0.5.0-dev_falktx1) unstable

  * New package name (qtsixa instead of qt-sixa)
  * New GUI layout (not finished yet)

sixad (0.5-falktx0) unstable

  * Merged sixpair into sixad package
  * Stop launching hcid before sixad (was needed for SDP, but SDP is now included in sixad)
  * Drop bluez-sixa package (no longer needed)
  * Preparations for RPM Linuxes (Fedora, OpenSUSE, etc)
  * Fixed LED # increase issue
```

The new (development/unstable) package is now on the repo (called "qtsixa" instead of "qt-sixa". It will appear in the menu as "*QtSixA (DEV)*"
I WARN YOU - see it but don't touch it... It's just to give you guys an idea of what I've been working on recently

And, due to the rewrite, we don't need the old bluez-sixa (hcid/hidd-six/libluetooth2) anymore. This will cause "Start old modules" to fail, which is on purpose.
The new GUI will not have an option to start old modules. If Sixaxis doesn't automatically connects, use the force menu option

Thanks aatu_kanifani for the profile. I'll add it on the next update
And the bug when creating a profile - it's caused by using a old PyQt version (which makes unreadable files). Maybe there's a PyQt repo for jaunty, I'll look for it

---

### Post by falkTX on 2009-09-25
I found a repo update - it's the KDE backports
It contains updates to the KDE apps **and also PyQt 4.5.4**

That will fix the creating profile bug and activate the double-click on the systray icon

The line for the repo is:
```
deb http://ppa.launchpad.net/kubuntu-ppa/backports/ubuntu jaunty main
```

---

### Post by falkTX on 2009-09-25
**Update:**
The launchpad and sourceforge pages have been created. There's not too much there to see yet...

[https://launchpad.net/qtsixa](https://launchpad.net/qtsixa)
[https://sourceforge.net/projects/qtsixa/](https://sourceforge.net/projects/qtsixa/)

---

### Post by falkTX on 2009-09-28
**Update:** QtSixA 0.5.0 is released!
Changelog:
```
qtsixa (0.5.0-falktx1) unstable;

  * Added "Fake Joystick 2" profile by aatu_kanifani
  * Added "xdg-utils" as debian dependency (needed for opening web pages)
  * Disconnect a device now uses DBus, which doesn't need root
  * Added python-dbus as debian dependency
  * The GUI is ready for real usage!
  * Release 0.5.0

sixad (0.5-falktx1) unstable;

  * Forgotten check for "LED_plus=X" (was always "yes", now fixed)
  * Removed bluez-sixa as debian dependency
  * Drop LPIA architecture support (LPIA users can safely use i386 binaries)
  * Set bluetooth restore timeout to 10 seconds (was 15)
```


This is the result of my weekend work, I hope you enjoy it.
As always, feel free to ask something, report a bug or post an idea


See ya soon
*falkTX*

---

### Post by aatu_kanifani on 2009-10-01
Hmm, seems like sixad doesn't always (re)start properly or something. Anyway, I have to start sixad manually in terminal to (re)connect successfully. I haven't yet tried with two controllers.

And it seems that disconnect (any of them) doesn't work, but maybe that's because of manually starting sixad. It disconnects when I terminate the sixad, though.

The update process gave some problems, but "Fix broken packages" in synaptic sorted that out. And the new GUI is great, very snappy. I think the sound problems are also gone. I think there were few, but either I can't get them to reappear anymore or they're so minor errors that I can't properly notice them anymore.

Didn't try creating profiles or using overrides. I'll probably try the overrides on Saturday when I go meet my brother and try 2 controllers.

---

### Post by falkTX on 2009-10-01
Thanks for testing that out. I'm about to buy a new "Sixaxis" controller (a crappy imitation, but it's new device that will be compatible with sixad).

The reason you're not able to disconnect devices it's because it now depends on dbus ("org.bluez"), which only starts some time *after* a controller has been connected (needs to be turned off for the connection to be made). I'll make the disconnect error display this info soon

There's also a bug when starting KDEsu (only happens once per session). I'll fix that soon too.


@aatu_kanifani: wouldn't you mind to make a few tests so I can know for sure why sixad is not auto-start in your system?

---

### Post by aatu_kanifani on 2009-10-01
I think initially sixad DID autostart on my laptop (at least it connected OK and the profiles worked without manually starting anything). But only on the first time, not anymore... On desktop, never.

Still using 9.04 32bit. qtsixa reports QT's as:
Main Qt version: 4.5.0
Python-Qt version: 4.4.4

Regarding tests: sure, I can try.

---

### Post by falkTX on 2009-10-02
> **aatu_kanifani said:**
> I think initially sixad DID autostart on my laptop (at least it connected OK and the profiles worked without manually starting anything). But only on the first time, not anymore... On desktop, never.

Still using 9.04 32bit. qtsixa reports QT's as:
Main Qt version: 4.5.0
Python-Qt version: 4.4.4

Regarding tests: sure, I can try.

First test (just to make sure if the problem is with Jaunty).
Can you get a Karmic (beta) Live CD, install QtSixA and see if Sixaxis auto-connects?
```
http://cdimage.ubuntu.com/daily-live/current/karmic-desktop-i386.iso
```

I'm not sure if the problem are old versions of UDev/BlueZ/HAL, but would be nice to know whatever it will be fully functional on Karmic or not
I use Karmic already, and sixad always auto-starts correctly

---

### Post by falkTX on 2009-10-02
**Update:**
I bought a new Sixaxis (an imitation one, to add support for it in sixad), and that joystick is... weird...
It uses a USB radio-signal? (like an IR device) that connects to the joystick in wireless mode.

Linux recognizes it and creates a basic controller, but this one is even worst than the Linux Sixaxis driver (30 axis... 13 buttons - 3 are missing!)
But the good thing is that it generates a hidraw device. I used 'hidraw-dump' (included in the sixad package) to get all possible data from it. It reports data just like a normal Sixaxis, but the accelerometer values doesn't change (I guess it's there just for PS3 compatibility). It also reports 2 more data packets than the original Sixaxis.

Since the default Linux driver only makes it with 13 buttons, the last 3 (X, [], and PS) don't work... So I tried to apply the sixad-raw to the hidraw device...
I needed to do some small modifications to the code and ...voilá! It fully works now.

The joystick is a NPlay PS3-88602

---

### Post by aatu_kanifani on 2009-10-02
Okay, so I tried the beta Koala. It worked ok. Also tried with 9.04 livecd, but that required manual sixad to connect. 

A side note: sometimes terminal says sixad is already running, even though System Monitor doesn't see it. If I don't manually stop and restart it, it won't let me connect. (this is in Jaunty)

Regarding two controllers:
Got the controllers working with 9.04 (with both HD-installed and livecd). With overrides also. Didn't remember to try in Koala, but I'd guess it wouldn't have caused problems...


Hmm, but now that I got home and tried it again on my desktop machine, I can't get it to connect at all on Jaunty. I even tried removing the current versions and reinstalling from the deb-files. On laptop it still works through manual sixad.

---

### Post by falkTX on 2009-10-03
> **aatu_kanifani said:**
> Okay, so I tried the beta Koala. It worked ok. Also tried with 9.04 livecd, but that required manual sixad to connect.  Are you saying that, on the same PC, Karmic auto-connects Sixaxis while, in Jaunty, you always have to start it manually?

> **aatu_kanifani said:**
> A side note: sometimes terminal says sixad is already running, even though System Monitor doesn't see it. If I don't manually stop and restart it, it won't let me connect. (this is in Jaunty) Not sure about this, but maybe because sixad is runned top-privileged, regular users can't see it. If that happens again, please try "ps -e | grep sixad": if it prints anything, then sixad is running 

> **aatu_kanifani said:**
> Regarding two controllers:
Got the controllers working with 9.04 (with both HD-installed and livecd). With overrides also. Didn't remember to try in Koala, but I'd guess it wouldn't have caused problems... They work fine in Karmic (I've tested that myself)

> **aatu_kanifani said:**
> Hmm, but now that I got home and tried it again on my desktop machine, I can't get it to connect at all on Jaunty. I even tried removing the current versions and reinstalling from the deb-files. On laptop it still works through manual sixad.
Something really strange is going on... Have you tried to pair yours Sixaxis again?

---

### Post by falkTX on 2009-10-03
Here's my little "test quiz" just to find out why the heck sixad doesn't, sometimes, work properly on Jaunty. (seems to be working fine on Karmic).


_Part 1 - Quick answers_

**1** - What's you GNU/Linux version and architecture?
```
uname -a
```

**2** - What's your UDev version?
```
dpkg -l | grep udev
```

**3** - What's you BlueZ version?
```
dpkg -l | grep bluez
```

**4** - When you first start a clean desktop session, what does this commmand reports?
```
ps -e | grep sixa
```

**5** - Do you have a bluetooth pen/device plugged-in?
```
hcitool dev
```

**6** - At startup, do you use any bluetooth hardware (mice, keyboards, etc) besides Sixaxis?
```
hcitool con
```

**7** - Have you paired your(s) Sixaxis?
> Yes or no?

------------------------------------------------------------------------

_Part 2 - Reporting data_

**1**  - At session startup, before doing anything else, please run:
```
/etc/init.d/bluetooth status; /etc/init.d/sixad status
```
At startup, bluetooth should be running and sixad should not.


**2** - Press the PS button on 1 Sixaxis and keep running that command every 2 seconds.
```
/etc/init.d/bluetooth status; /etc/init.d/sixad status
```
Once you press the PS button, bluetooth should stop and sixad run. Then, 10 seconds later bluetooth will start again while sixad is still running


**3** - Disconnect that Sixaxis and press the button again. Keep running every 2 seconds:
```
/etc/init.d/bluetooth status; /etc/init.d/sixad status
```
The bluetooth should stop while sixad is always running. As before, bluetooth should restore/start 10 seconds after pressing PS.


Please, Ubuntu users - report what happens to you!

---

### Post by falkTX on 2009-10-03
Here's my own report:


Part 1:
1 - Linux falkTX-Laptop 2.6.31-11-generic #38-Ubuntu SMP Fri Oct 2 11:06:40 UTC 2009 x86_64 GNU/Linux
2 - ii  udev                                  147~-5                                     rule-based device node and kernel event manager
3 - ii  bluez                                 4.51-0ubuntu2                              Bluetooth tools and daemons
4 - (nothing)
5 - Devices:	hci0    00:80:5A:65:BC:BA
6 - Connections:
7 - Yes

Part 2:
1 - 
* bluetooth is running
* sixad is not running

2 - Happens just like posted

3 - Happens just like posted

---

### Post by Okiura on 2009-10-05
Hi,

Excellent work here I'm loving this new version it makes my life so much easier. :)

I need a little help though I have very small problem with the input... all the buttons, sticks & g-sensors work fine and jstest confirms every button is working fine including the pressure sensitive axis's on each button.

my issue is this: axis's 0,1,2 & 3 seems to randomly receive a input even though no sticks are being moved this only lasts for a fraction of a second and then stops jstest shows each effected axis registering a movement of -32767 briefly before returning to 0. there is a pattern to the order the axis's are registering this input and it is as follows (X = -32767 & 0 = 0, e.g 0:0 is axis 0 reading no input and 1:X is axis 1 reading -32767)

0:0 1:0 2:0 3:0 <-- all off 
0:X 1:0 2:0 3:0
0:X 1:X 2:0 3:0
0:X 1:X 2:X 3:0
0:X 1:X 2:X 3:X
0:0 1:X 2:X 3:X
0:0 1:0 2:X 3:X
0:0 1:0 2:0 3:X
0:0 1:0 2:0 3:0 <-- all off

This sequence takes less than a second to do and it happens at random intervals but more frequent if the sixaxis is left idle, then it seems to happen about every 30 seconds or so.

I have use the configuration section to test each axis 1 by 1 (disabling all functions and enabling them 1 at a time) and the only axis's it is affecting is 0,1,2 & 3, i have tested with more then 1 sixaxis controller too.

Basic system info:

Kernel: 2.6.28-15-generic #52-Ubuntu SMP Wed Sep 9 10:49:34 UTC 2009 i686 GNU/Linux

Ubuntu version: Jaunty

Sixad Version: 0:5:0 and all the latest packages form the apt respiratory

I don't know how much info you need here but i can supply more if needed.

P.S. I'm sorry if this question has been asked before i did look through all the old posts but only found buttons not working.

---

### Post by falkTX on 2009-10-06
Thanks Okiura, that was actually the first time someone reported this.
I'll see if I can reproduce the error.

Can you check if, connecting Sixaxis through USB, then using:
```
sixad --raw /dev/hidrawX
```
Where "X" is the hidraw device 'dmesg' reports. Does the axis error still occurs in the hidraw mode?

---

### Post by falkTX on 2009-10-06
**Update:** - v0.5.1:
> qtsixa (0.5.1-falktx1) stable

  * Do not display icons on "Cancel"/"Finish" buttons, Sixpair Setup (looks bad on GTK)
  * Fixed Configure Sixaxis widget layout on 1st tab
  * Fixed root actions needed to be run twice in KDE (kdesudo)
  * Use 'kdesu' when 'kdesudo' is not available (needed for some RPM distros)
  * QtSixA/sixad are now also available as RPM packages [check 'qtsixa.sourceforge.net' for downloads]
  * Force option is available again
  * Some other small fixes

sixad (0.6-falktx1) unstable

  * Fixed bluetooth not stopped properly when starting sixad (needed for auto-connect devices)
  * Re-Added 'hcid' (still needed for SDP)
  * Force option is available again
  * Output much more information from sixad

I haven't too much time for test on Jaunty, but it should auto-connect now.
This release also starts support for RPM Linux distros, check [https://sourceforge.net/projects/qtsixa/files/](https://sourceforge.net/projects/qtsixa/files/) and download the RPM pack to test it

Happy gaming!

---

### Post by falkTX on 2009-10-06
For people with problems updating, run this commands:
```
sudo apt-get update
sudo dpkg -r qtsixa qt-sixa sixad bluez-sixa sixad
sudo apt-get -f install
sudo apt-get install qtsixa sixad
```
That would fix the update problems (sorry about that)

---

### Post by Okiura on 2009-10-06
Hi FalkTX

I connected the Sixaxis via USB and activated hidraw mode this created a new js device in: 

```
/dev/input/
``` 

and a dmesg output of:

```
 input: PLAYSTATION(R)3 Controller (hidraw) as /devices/virtual/input/input44 
```

This has now been connected for while and the only input i'm seeing in jstest is the input from movements i'm making so this apperes to only be a bluetooth issue.

Okiura

---

### Post by falkTX on 2009-10-06
Thanks for reporting this issue.
I'm currently at work, but once I get home I will check this.

---

### Post by digge on 2009-10-06
I seem to have trouble getting sixa to work for me, im new to this program so not sure how its supposed to work. I cant seem to be able to pair the controller for any long period of time. From the looks of it when i start the controller on the PS button it shows up in sixa and the bluetooth icon goes away, then it disappear again in sixa and comes back a few times. After that disappear permanently in sixa and bluetooth icon is back.

Looking at what processes spawn during this i see 1-8 sixad spawning and then dieing again until there is none of them left. Any ideas what im doing wrong?

My controller is Dualshock 3 original ones.
Im running karmic updated today.
Trying to get it to work on my PS3

Tell me if there is any more info i can supply you with that might help.

---

### Post by falkTX on 2009-10-07
@digge - can you make the test on the previous page?
There's an option in QtSixA to force the connnection (in the menu, "Tasks" -> "Force Connection")

@Okiura - I can confirm that little bug. I've already clean'up the code, but it still happens.
In or to not fill the forum thread with this discussion, I've filled a bug report - [https://bugs.launchpad.net/qtsixa/+bug/445259](https://bugs.launchpad.net/qtsixa/+bug/445259)
Conversation about this little bug should happen there

---

### Post by aatu_kanifani on 2009-10-07
Sorry it took this long, I had a preliminary report to make.

Well anyway, long story short... The situation got so bad I couldn't even re-install it anymore (I tried a lot of stuff). So I figured something simply must have broken along the way (software-wise). So now I re-installed Jaunty and the new 0.5.1 version of qtsixa with the deb files. And now it works with Force Connection.

I have the old 0.5.0 version still on my laptop with Jaunty, so I'll post the "test" for that in a while.
And yes, with that same laptop Koala livecd auto-connects, but Jaunty hd-installed requires manual sixad.

Today was the first time I got to try the 0.5.1 version with "Force Connection". The earlier version had that disabled. I tried the "Stop bluetooth" like instructed, though. And yes, I always re-pair after trying with different PCs (or PS3). And one thing I haven't yet mentioned: Laptop has integrated BT, desktop has a dongle. But I don't think that should matter.

It seems on the new version (at least after Force Connection) sixad won't stop at all. Not even with "sixad --stop". "ps -e | grep sixad" still shows this on the terminal:
```
21874 ?        00:00:00 sixad
21887 ?        00:00:00 sixad-bin
```

That doesn't matter to me though. But here's the tests I made for Koala livecd on desktop with 0.5.0 (I'll try the new version at some point too):

```

Part 1.

1. Linux machine 2.6.28-15-generic #52-Ubuntu SMP Wed Sep 9 10:49:34 UTC 2009 i686 GNU/Linux
2. ii  udev  141-1.2  rule-based device node and kernel event mana
3. ii  bluez  4.32-0ubuntu4.1  Bluetooth tools and daemons
4. (nothing)
5. Devices: hci0  00:19:86:00:01:21
6. Connections:
7. Yes (only one Dualshock3 tried on desktop machine)

Part 2.

1.
* bluetooth is running
* sixad is not running
 
2. (I assume "status1" should be "status", meaning the same commands as in the first step)
* bluetooth is running
* sixad is not running
(and won't change)

3. (well, can't disconnect without connection)
```

On part1:2&3 there were others, but are those the ones you need?

---

### Post by falkTX on 2009-10-07
Many thanks for reporting that aatu_kanifani!!

It seems that sixad is not even started...

But I noticed you're using an old Karmic alpha release.
The daily build has udev147 & bluez4.51 while yours has udev141 & bluez4.32
Please try with Karmic beta next time

The major problem here is that sixad is not started by udev...
I need to ask you to do this:
```
sixad &
#(wait a few seconds)
sudo pkill -KILL hcid
sudo /etc/init.d/bluetooth start

```
Does pressing the PS button now, connects the Sixaxis?

*(note that sixad cannot be stopped until you disconnected all devices)*

---

### Post by digge on 2009-10-07
**1** - What's you GNU/Linux version and architecture?
Linux ubuntu 2.6.31-11-powerpc64-smp #38-Ubuntu SMP Fri Oct 2 14:15:47 UTC 2009 ppc64 GNU/Linux

**2** - What's your UDev version?
147~-5 

**3** - What's you BlueZ version?
4.51-0ubuntu2

**4** - When you first start a clean desktop session, what does this commmand reports?
nothing

**5** - Do you have a bluetooth pen/device plugged-in?
Using built in BT of the PS3 (hci0	00:23:06:XX:XX:XX)

**6** - At startup, do you use any bluetooth hardware (mice, keyboards, etc) besides Sixaxis?
Nope

**7** - Have you paired your(s) Sixaxis?
Tried but since i cant see it for long periods impossible.

------------------------------------------------------------------------

_Part 2 - Reporting data_

**1**  - At session startup, before doing anything else, please run:
At startup, bluetooth should be running and sixad should not.
 * bluetooth is running
 * sixad is not running

**2** - Press the PS button on 1 Sixaxis and keep running that command every 2 seconds.
```
/etc/init.d/bluetooth status; /etc/init.d/sixad status
```
Once you press the PS button, bluetooth should stop and sixad run. Then, 10 seconds later bluetooth will start again while sixad is still running
Bluetooth stops for 10 secs and starts again but sixad never starts.


**3** - Disconnect that Sixaxis and press the button again. Keep running every 2 seconds:
```
/etc/init.d/bluetooth status; /etc/init.d/sixad status
```
The bluetooth should stop while sixad is always running. As before, bluetooth should restore/start 10 seconds after pressing PS.
Cant since i never get a stable connection.

Please, Ubuntu users - report what happens to you![/QUOTE]

Noticed a weird thing though that might be related. ```
/etc/init.d/sixad start
 * Starting sixad
/etc/init.d/sixad: 59: /usr/sbin/sixad: not found

```

however if i look in that folder the sixad file isnt there, there is a sixad file in /usr/bin though.

Tried force but seems sixad doesnt start at all. It tries but fails.

Edit: Noticed you updated sixad, will update to latest.
Edit 2: No change.

---

### Post by falkTX on 2009-10-07
> **digge said:**
> Noticed a weird thing though that might be related. ```
/etc/init.d/sixad start
 * Starting sixad
/etc/init.d/sixad: 59: /usr/sbin/sixad: not found

```

however if i look in that folder the sixad file isnt there, there is a sixad file in /usr/bin though.

Tried force but seems sixad doesnt start at all. It tries but fails.

Edit: Noticed you updated sixad, will update to latest.
Edit 2: No change.

Thanks for reporting too.
the /etc/init... doesn't change anything at all (but thanks anyway for finding it)

It seems like you didn't understood how the Sixaxis is paired:
You have to connect the Sixaxis through USB, then on QtSixA, click "Pair Sixaxis/Keypad to PC"

You can force the connection through the terminal too, by doing:
```
sudo sixad --force
```
That will stop regular bluetooth, start sixad, and start hcid (which prevents regular bluetooth to turn on again)

---

### Post by digge on 2009-10-07
Tried pairing with it connected through usb. The report afterwards is blank, no text whatsoever, pushed finish anyways. 

Tried the commandline you gave me,

```
sudo sixad --force
sixad has been forced to start.
bluetooth will not be operational in this mode
/usr/bin/sixad: line 43: /usr/sbin/sixad-bin: No such file or directory
```

Weird part is that the file is there.

---

### Post by ESPNSTI on 2009-10-07
I seem to have almost identical issues as digge except I'm on jaunty (and 0.5.1).

I've seen that "/usr/sbin/sixad-bin: No such file or directory" error before and if I recall correctly, the sixad-bin was in that directory. (But I should re-test that to confirm that).

I'll see if I have some time later this week to do that test.

Pairing through usb will be a bit of an adventure for me since I have my PS3 in an equipment rack in the basement downstairs and my TV upstairs. (I could probably use the exercise that I will get from running up and down the stairs. :) )

---

### Post by aatu_kanifani on 2009-10-07
@reply #231:
Ah, that explains it. I made a bootable USB with UNetbootin, and I assumed selecting "Daily_Live" would download the latest there is, but apparently not. ( <-- I don't have a cd-drive on my desktop machine...)

And like I earlier stated, the Koala (with the image from the link you gave) on laptop auto-connected.

Anyway, at the moment it works OK on my desktop Jaunty with the 0.5.1 version. I also noticed I don't have to use "Force Connection" after all; "Stop Bluetooth" is enough. But if using those commands in the reply #231, it won't let me connect. But if I stop bluetooth after those, everything is OK again.

And using those commands on the Jaunty laptop with 0.5.0 won't let it connect either. And stopping the bluetooth won't help this time. But as a side note, it now once connected without any tricks, meaning "Fresh session -> Start GUI -> Press PS-button  ---->  Connected". But only once...

Should I still keep the 0.5.0 on the laptop for more tests or should I try the new version and see how that works?

About disconnecting and sixad (on desktop Jaunty with 0.5.1): it seems the Disconnect-button doesn't work. But I can still disconnect with PS-button. That way the sixad won't stop automatically, but I can stop it manually from the menu.

---

### Post by falkTX on 2009-10-08
Answer to many questions: (I'll probably create a FAQ soon)

**What is required to connect Sixaxis over bluetooth?**
1 - 'qtsixa' and 'sixad' packages installed
2 - 32/64bit or PowerPC/PS3
3 - Paired your Sixaxis through USB (option available in QtSixA)
4 - Ubuntu Jaunty/9.04 or Karmic/9.10 (Intrepid may not work)
*[NOTE: I've tested a fresh Jaunty 32bit LiveUSB, and it worked fine]*
5 - A bluetooth 2.0/2.1 adapter/stick/pen/whatever (a bluetooth 2.0/2.1 receiver)

Pressing the PS button on these conditions should automatically connect the Sixaxis.
If not, you can try:
```
sixad --stop
sixad
```

Usually, what prevents the 'sixad' driver to connect to a Sixaxis is the regular bluetooth (starts automatically when a new bluetooth device is found). Running sixad from terminal launches also 'hcid' that should prevent the regular bluetooth from starting (but doesn't always work).

I really want to help you guys (and that way making my application better).
So, before saying that is not working for you, please make this tests first:
1 - Check if your bluetooth adapter can connect to any other devices (like a cellphone)
2 - Make sure you're using the last updates (specially sixad/qtsixa)
3 - Pair your Sixaxis/Keypads first
4 - Reboot frequently just to make sure


I'll ignore all non-working reports done so far, so please re-report if the Sixaxis still doesn't work.

---

### Post by falkTX on 2009-10-08
**Update:**
A very small sixad update, just to fix some "PATH" issues. Is in the repos now

---

### Post by ESPNSTI on 2009-10-08
> **falkTX said:**
>  5 - A bluetooth 2.0/2.1 adapter/stick/pen/whatever (a bluetooth 2.0/2.1 receiver)
Just for clarification, the PS3's internal bluetooth receiver fulfills this requirement correct?

---

### Post by falkTX on 2009-10-08
> **ESPNSTI said:**
> Just for clarification, the PS3's internal bluetooth receiver fulfills this requirement correct?

I think so, users have been reported to work
And it does connect Sixaxis in the normal PlayStation OS/Gaming, so YES, it works

But, anyway, you should try connected it to any other device (like a cell phone), just to make sure bluetooth is working fine in Ubuntu

---

### Post by digge on 2009-10-09
Hi agian, sorry for not replying sooner. My install of karmic got blown up during an update so i went back to jaunty for now. Clean install and it still doesnt work. Did some digging around, hope you can use this info somehow.

When installing from the repo i get this, might be nothing but wasnt there before ```
Setting up qtsixa (0.5.1-falktx1) ...
cp: cannot stat `/usr/share/qtsixa/profiles/sixa_none.fdi': No such file or directory
```

Issuing sixad from a terminal still gives a file not found error. ```
sixad
sudo: unable to execute /usr/sbin/sixad-bin: No such file or directory
```

So i did a bit of digging in your code and saw that you log some events to syslog and this is what syslog says when the file not found appears.  ```
ubuntu hcid[15344]: Bluetooth HCI daemon
ubuntu hcid[15344]: Can't open config file /etc/bluetooth/hcid.conf
ubuntu hcid[15344]: Config load failed
ubuntu hcid[15344]: Could not become the primary owner of org.bluez
ubuntu hcid[15344]: Unable to get on D-Bus

```

after installing bluez-compat libusb-dev i got this instead.

```
ubuntu hcid[3229]: Bluetooth HCI daemon
ubuntu hcid[3229]: Can't open config file /etc/bluetooth/hcid.conf
ubuntu hcid[3229]: Config load failed
ubuntu hcid[3229]: HCI dev 0 registered
ubuntu hcid[3229]: HCI dev 0 already up
ubuntu hcid[3229]: Device hci0 has been added
ubuntu hcid[3229]: Starting security manager 0
ubuntu hcid[3229]: Device hci0 has been activated
ubuntu hcid[3229]: Created local server at unix:abstract=/var/run/dbus-4Vpjv7Olq9,guid=15132de6b0a848c77d82bb924acfab04

```

The file not found is still there though. Sorry for not putting all version numbers of everything here atm, ill try to add those tomorrow when im not as tired, hitting the bed now.

---

### Post by ESPNSTI on 2009-10-09
I removed sixa and cleaned up as much as I could:
```
sudo apt-get update
sudo apt-get purge qtsixa qt-sixa sixad bluez-sixa
sudo apt-get -f install
sudo apt-get autoremove
I did a search using "sudo find -name '*sixa*'" and removed all those files.
```I then started over.
This is what I got during install:

```
espnsti@PS3:~$ sudo apt-get install qtsixa sixad
[sudo] password for espnsti: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  bluez-hcidump libnotify-bin libphonon4 libqt4-assistant libqt4-help
  libqt4-opengl libqt4-svg libqt4-test libqt4-webkit libqt4-xmlpatterns phonon
  phonon-backend-gstreamer python-qt4 python-qt4-common python-sip4
Suggested packages:
  phonon-backend-xine phonon-backend-vlc phonon-backend-mplayer python-qt4-dbg
The following NEW packages will be installed:
  bluez-hcidump libnotify-bin libphonon4 libqt4-assistant libqt4-help
  libqt4-opengl libqt4-svg libqt4-test libqt4-webkit libqt4-xmlpatterns phonon
  phonon-backend-gstreamer python-qt4 python-qt4-common python-sip4 qtsixa
  sixad
0 upgraded, 17 newly installed, 0 to remove and 0 not upgraded.
Need to get 977kB/10.5MB of archives.
After this operation, 53.0MB of additional disk space will be used.
Do you want to continue [Y/n]? y
WARNING: The following packages cannot be authenticated!
  sixad qtsixa
Install these packages without verification [y/N]? y
Get:1 [http://falktx.xtreemhost.com](http://falktx.xtreemhost.com) jaunty/main sixad 0.6-falktx3 [248kB]
Get:2 [http://falktx.xtreemhost.com](http://falktx.xtreemhost.com) jaunty/main qtsixa 0.5.1-falktx1 [729kB]
Fetched 977kB in 24s (39.7kB/s)                                                
Selecting previously deselected package libqt4-assistant.
(Reading database ... 107957 files and directories currently installed.)
Unpacking libqt4-assistant (from .../libqt4-assistant_4.5.0-0ubuntu4.2_powerpc.deb) ...
Selecting previously deselected package libqt4-help.
Unpacking libqt4-help (from .../libqt4-help_4.5.0-0ubuntu4.2_powerpc.deb) ...
Selecting previously deselected package libqt4-opengl.
Unpacking libqt4-opengl (from .../libqt4-opengl_4.5.0-0ubuntu4.2_powerpc.deb) ...
Selecting previously deselected package libqt4-svg.
Unpacking libqt4-svg (from .../libqt4-svg_4.5.0-0ubuntu4.2_powerpc.deb) ...
Selecting previously deselected package libqt4-test.
Unpacking libqt4-test (from .../libqt4-test_4.5.0-0ubuntu4.2_powerpc.deb) ...
Selecting previously deselected package libphonon4.
Unpacking libphonon4 (from .../libphonon4_4%3a4.3.1-0ubuntu3_powerpc.deb) ...
Selecting previously deselected package phonon-backend-gstreamer.
Unpacking phonon-backend-gstreamer (from .../phonon-backend-gstreamer_4%3a4.3.1-0ubuntu3_powerpc.deb) ...
Selecting previously deselected package phonon.
Unpacking phonon (from .../phonon_4%3a4.3.1-0ubuntu3_all.deb) ...
Selecting previously deselected package libqt4-webkit.
Unpacking libqt4-webkit (from .../libqt4-webkit_4.5.0-0ubuntu4.2_powerpc.deb) ...
Selecting previously deselected package libqt4-xmlpatterns.
Unpacking libqt4-xmlpatterns (from .../libqt4-xmlpatterns_4.5.0-0ubuntu4.2_powerpc.deb) ...
Selecting previously deselected package libnotify-bin.
Unpacking libnotify-bin (from .../libnotify-bin_0.4.5-0ubuntu1_powerpc.deb) ...
Selecting previously deselected package python-sip4.
Unpacking python-sip4 (from .../python-sip4_4.7.9-1ubuntu1_powerpc.deb) ...
Selecting previously deselected package python-qt4-common.
Unpacking python-qt4-common (from .../python-qt4-common_4.4.4-2ubuntu6_all.deb) ...
Selecting previously deselected package python-qt4.
Unpacking python-qt4 (from .../python-qt4_4.4.4-2ubuntu6_powerpc.deb) ...
Selecting previously deselected package bluez-hcidump.
Unpacking bluez-hcidump (from .../bluez-hcidump_1.42-1build1_powerpc.deb) ...
Selecting previously deselected package sixad.
Unpacking sixad (from .../sixad_0.6-falktx3_powerpc.deb) ...
Selecting previously deselected package qtsixa.
Unpacking qtsixa (from .../qtsixa_0.5.1-falktx1_all.deb) ...
Processing triggers for man-db ...
Setting up libqt4-assistant (4.5.0-0ubuntu4.2) ...

Setting up libqt4-help (4.5.0-0ubuntu4.2) ...

Setting up libqt4-opengl (4.5.0-0ubuntu4.2) ...

Setting up libqt4-svg (4.5.0-0ubuntu4.2) ...

Setting up libqt4-test (4.5.0-0ubuntu4.2) ...

Setting up libphonon4 (4:4.3.1-0ubuntu3) ...

Setting up phonon-backend-gstreamer (4:4.3.1-0ubuntu3) ...
Setting up phonon (4:4.3.1-0ubuntu3) ...
Setting up libqt4-webkit (4.5.0-0ubuntu4.2) ...

Setting up libqt4-xmlpatterns (4.5.0-0ubuntu4.2) ...

Setting up libnotify-bin (0.4.5-0ubuntu1) ...
Setting up python-sip4 (4.7.9-1ubuntu1) ...
Setting up python-qt4-common (4.4.4-2ubuntu6) ...

Setting up python-qt4 (4.4.4-2ubuntu6) ...

Setting up bluez-hcidump (1.42-1build1) ...
Setting up sixad (0.6-falktx3) ...

Setting up qtsixa (0.5.1-falktx1) ...
cp: cannot stat `/usr/share/qtsixa/profiles/sixa_none.fdi': No such file or directory

Processing triggers for libc6 ...
ldconfig deferred processing now taking place
```I then started qtsixa and attempted to pair it (with the ds3 connected using usb).
It showed blank in the sixpair report.
I also tried the force connection menu item.
```
espnsti@PS3:~$ qtsixa
Main Qt version: 4.5.0
Python-Qt version: 4.4.4
Will use 'gksu' for root actions
Your system doesn't suport double-click on systray
sixad has been forced to start.
bluetooth will not be operational in this mode
WARNING: All config files need .conf: /etc/modprobe.d/oss-compat, it will be ignored in a future release./usr/bin/sixad: line 43: /usr/sbin/sixad-bin: No such file or directory
l be ignored in a future release.espnsti@PS3:~$
```I attempted the sixad command from the terminal:
```
espnsti@PS3:~$ sudo sixad --stop
 * Starting bluetooth                                                    [ OK ] 
espnsti@PS3:~$ sudo sixad
WARNING: All config files need .conf: /etc/modprobe.d/oss-compat, it will be ignored in a future release.
sudo: unable to execute /usr/sbin/sixad-bin: No such file or directory
espnsti@PS3:~$ ssixad --stop
bash: ssixad: command not found
espnsti@PS3:~$ sixad --stop
 * Starting bluetooth                                                    [ OK ] 
espnsti@PS3:~$ sixad
WARNING: All config files need .conf: /etc/modprobe.d/oss-compat, it will be ignored in a future release.
sudo: unable to execute /usr/sbin/sixad-bin: No such file or directory
espnsti@PS3:~$ 
```sixad-bin is present, but I'm assuming sixad-bin is complaining about a file it can't find instead of the OS complaining that sixad-bin isn't there.
```

espnsti@PS3:/usr/sbin$ ls sixad-bin
sixad-bin
espnsti@PS3:/usr/sbin$ sudo sixad-bin
sudo: unable to execute /usr/sbin/sixad-bin: No such file or directory
espnsti@PS3:/usr/sbin$ sixad-bin
bash: /usr/sbin/sixad-bin: No such file or directory
espnsti@PS3:/usr/sbin$
```I'm also seeing the same in syslog:
```
Oct  9 19:51:37 PS3 hcid[7629]: Bluetooth HCI daemon
Oct  9 19:51:37 PS3 hcid[7629]: Can't open config file /etc/bluetooth/hcid.conf
Oct  9 19:51:37 PS3 hcid[7629]: Config load failed
Oct  9 19:51:37 PS3 hcid[7629]: Could not become the primary owner of org.bluez
Oct  9 19:51:37 PS3 hcid[7629]: Unable to get on D-Bus
```

```
espnsti@PS3:/etc/bluetooth$ ls -la
total 36
drwxr-xr-x   2 root root  4096 2009-10-05 02:27 .
drwxr-xr-x 132 root root 12288 2009-10-09 19:17 ..
-rw-r--r--   1 root root   910 2009-04-01 03:53 audio.conf
-rw-r--r--   1 root root   262 2009-04-01 03:53 input.conf
-rw-r--r--   1 root root  1744 2009-04-01 03:53 main.conf
-rw-r--r--   1 root root   751 2009-04-01 03:53 network.conf
-rw-r--r--   1 root root   297 2009-04-01 03:53 rfcomm.conf
espnsti@PS3:/etc/bluetooth$ sudo echo . > hcid.conf
bash: hcid.conf: Permission denied
espnsti@PS3:/etc/bluetooth$ 
```

---

### Post by falkTX on 2009-10-10
Thanks guys for re-reporting this. I just wanted to make sure I didn't had to look around for fixes I already made in the past.

About the issues reported
1 - file /etc/bluetooth/hcid.conf missing
this is nothing really, just hcid trying to read the conf file. It uses the back-up/default configuration when the file is not present. But I'll add the file anyway...

2 - cp: cannot stat `/usr/share/qtsixa/profiles/sixa_none.fdi'
Just something I forgot in the process. It should be ...qtsixa/sixaxis-profiles/si...

For the rest, I'll provide an update soon

---

### Post by falkTX on 2009-10-10
**Update:** QtSixA 0.5.2 released!
Changelog:
> qtsixa (0.5.2-falktx1) stable
  * Fixed debian postinst script (wrong path to "sixa_none.fdi" file)
  * Display "You're not using a Sixaxis profile" in systray when main GUI says that too
  * Fixed layout in the "Game Profiles" tab
  * Sixpair setup now displays an error when no root privileges are available
  * Debian conflits with old qt-sixa version (for happy update)
  * Report to terminal when QtSixA cannot disconnect devices (old PyQt version)
  [On Jaunty, use the KDE updates repo to update your PyQt version]
  * Updated features.html file (used in "Help" -> "List of Features")
  * Other very small fixes

sixad (0.6-falktx{2,3,4}) stable
  * Fixed some PATH issues
  * Debian conflicts with "libbluetooth2", "bluez-sixa", "bluez-sixaxis" and "bluez-sixaxis-bin"
  * Make sure sixad binaries are executable (no more "/usr/sbin/sixad-bin: command not found" when the file is really there!)
  * Axis 4-7 (accelerometers) are now centered at 0 when disabled (was always max, 32767)

As always, keep posting any bugs you find. Thanks to all that are already doing this!

---

### Post by falkTX on 2009-10-10
Does anyone has an account in the PSUbuntu forums?

Check this:
[http://psubuntu.com/forums/viewtopic.php?f=4&t=764&start=30](http://psubuntu.com/forums/viewtopic.php?f=4&t=764&start=30)

Those guys are using my 2-year-old-and-sucking-gui...

I don't want to create an account there just for a single post...
Thanks in advance

---

### Post by ESPNSTI on 2009-10-10
Still no dice for me with 0.5.2:
```
espnsti@PS3:/usr/sbin$ ls -la sixad-bin
-rwxr-xr-x 1 espnsti espnsti 42328 2009-10-10 06:21 sixad-bin
espnsti@PS3:/usr/sbin$ sudo sixad --stop
espnsti@PS3:/usr/sbin$ sudo sixad
WARNING: All config files need .conf: /etc/modprobe.d/oss-compat, it will be ignored in a future release.
sudo: unable to execute /usr/sbin/sixad-bin: No such file or directory
espnsti@PS3:/usr/sbin$ sudo sixad-raw
sudo: unable to execute /usr/sbin/sixad-raw: No such file or directory
espnsti@PS3:/usr/sbin$ sudo sixad-uinput-sixaxis 
sudo: unable to execute /usr/sbin/sixad-uinput-sixaxis: No such file or directory
espnsti@PS3:/usr/sbin$ sudo sixpair
sudo: unable to execute /usr/sbin/sixpair: No such file or directory
espnsti@PS3:/usr/sbin$ sudo sixpair-kbd
sudo: unable to execute /usr/sbin/sixpair-kbd: No such file or directory
espnsti@PS3:/usr/sbin$ 
```

---

### Post by falkTX on 2009-10-10
> **ESPNSTI said:**
> Still no dice for me with 0.5.2:
```
espnsti@PS3:/usr/sbin$ ls -la sixad-bin
-rwxr-xr-x 1 espnsti espnsti 42328 2009-10-10 06:21 sixad-bin
espnsti@PS3:/usr/sbin$ sudo sixad --stop
espnsti@PS3:/usr/sbin$ sudo sixad
WARNING: All config files need .conf: /etc/modprobe.d/oss-compat, it will be ignored in a future release.
sudo: unable to execute /usr/sbin/sixad-bin: No such file or directory
espnsti@PS3:/usr/sbin$ sudo sixad-raw
sudo: unable to execute /usr/sbin/sixad-raw: No such file or directory
espnsti@PS3:/usr/sbin$ sudo sixad-uinput-sixaxis 
sudo: unable to execute /usr/sbin/sixad-uinput-sixaxis: No such file or directory
espnsti@PS3:/usr/sbin$ sudo sixpair
sudo: unable to execute /usr/sbin/sixpair: No such file or directory
espnsti@PS3:/usr/sbin$ sudo sixpair-kbd
sudo: unable to execute /usr/sbin/sixpair-kbd: No such file or directory
espnsti@PS3:/usr/sbin$ 
```

try this:
```
cd /usr/sbin
sudo chmod +x sixad-bin
./sixad-bin
```

It's really weird how you can't execute that file...
Is this the first time you see this problem? (It is for me)

---

### Post by digge on 2009-10-10
Still the same for me, updated it to latest. Also tried the chmod but still ```
sixad
sudo: unable to execute /usr/sbin/sixad-bin: No such file or directory
```

I think the problem lies in some unmet dependency. Like at first i was missing the bluez-compat package wich meant i was missing the hcid command, that would make your program spit out file not found? Think there is more of them missing for some reason, what other command line commands do you use?

I think it executes fine, just that when your program tries to run some command line command it cant find it, hence the file not found error.

Maybe you could make a debug version where you echo each line you send to command line before execute, that would catch it if the case is as i described above.

---

### Post by falkTX on 2009-10-10
sixad-bin is a C compiled code binary.
It first checks for user arguments [--opts], which are automatically sent when running sixad.
If the number of arguments is lower than 11 (there are many sixad options...) it just prints:
> falktx@falkTX-Laptop:~$ sixad-bin
Running sixad-bin requires 'sixad'. Please run sixad insteadAnd that's the expected result.

*The file doesn't not depend on any other file*, except "sixad-uinput-sixaxis" that is launched when a Sixaxis is detected and connected.
Since the Sixaxis doesn't connect right away, the problem it something else.

maybe some other application suffers from the same problem..?
I'll look around


Edit:
try "strace sixad-bin", which outputs LOTS of information

---

### Post by digge on 2009-10-10
Here is the output of that.

```
strace sixad-bin
execve("/usr/sbin/sixad-bin", ["sixad-bin"], [/* 38 vars */]) = -1 ENOENT (No such file or directory)
dup(2)                                  = 3
fcntl64(3, F_GETFL)                     = 0x2 (flags O_RDWR)
fstat64(3, {st_mode=S_IFCHR|0620, st_rdev=makedev(136, 0), ...}) = 0
mmap(NULL, 4096, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0xf7ffb000
_llseek(3, 0, 0xffe71018, SEEK_CUR)     = -1 ESPIPE (Illegal seek)
write(3, "strace: exec: No such file or dir"..., 40strace: exec: No such file or directory
) = 40
close(3)                                = 0
munmap(0xf7ffb000, 4096)                = 0
exit_group(1)                           = ?
```

---

### Post by falkTX on 2009-10-10
Thanks for that, but it outputs the error right in the 1st line...
*execve(...= -1 ENOENT (No such file or directory)*

To get the list of needed libraries: (you should not need this)
```
ldd /usr/sbin/sixad-bin
```


Can you download the last QtSixA code:
[https://sourceforge.net/projects/qtsixa/files/QtSixA%200.5.2/QtSixA_20091010.tar.gz/download](https://sourceforge.net/projects/qtsixa/files/QtSixA%200.5.2/QtSixA_20091010.tar.gz/download)
and try to compile sixad?
```
cd DIR_OF_SIXAD
make
sudo make install
```


Thanks for your help so far

---

### Post by digge on 2009-10-10
This is what that command gives.

```
ldd /usr/sbin/sixad-bin
	not a dynamic executable
```

Havnt tried to compile it myself no, started on it but since it doesnt have a configure script makes it hard on me as a compiler noob to know what error message is due to what missing dev package. Ill give it a shot though and see if that helps.

Assuming i need some bluetooth dev packages at least, ill try at least.

EDIT: Compiled sixad and started without any issues, had a small hickup though, it said hcid, command not found. So then i installed from the repos and the overwrote the files with the ones i compiled and now no errors.

Edit2: Stays connected and on now, pairing worked fine via usb, however the leds keep flashing (is that part implemented yet?) and no /dev/input/js0 shows up. (not sure that it is supposed to happen either). Batterystatus wont show anything but 0. Maybe i need to recompile qtsixa as well?

---

### Post by falkTX on 2009-10-10
Thanks again.

This is fixed for you, but not sure if others will have similar errors or not
It bothers me how I never had problems with sixad, even in Jaunty, and people are always complaining that it doesn't work...

Anyway, you should know that pairing is a one-time job and there's no LED support when using Sixaxis over USB.
Sometimes checking battery sets the progress-bar to 0, you just need to keep trying.
And there's no need to compile QtSixA, as it is written on python (python processes code "on-the-fly")


EDIT: wait... are you running PowerPC/PS3? - If yes, then I've got a fix for you

---

### Post by digge on 2009-10-10
Im using it over bluetooth now, and leds still flash. 
And is a js0 device supposed to be created? if so it doesnt work as intended, no such device gets created.

Really grateful for your help, looks like an awesome software. Hope i dont sound like i complain, just want to help out as much as i can.

Edit: yes im on ps3/ppc

---

### Post by falkTX on 2009-10-10
> **digge said:**
> Im using it over bluetooth now, and leds still flash. 
And is a js0 device supposed to be created? if so it doesnt work as intended, no such device gets created.

Really grateful for your help, looks like an awesome software. Hope i dont sound like i complain, just want to help out as much as i can.

Edit: yes im on ps3/ppc

try the option "Force connection" in QtSixA.

I already fixed the executable not found problem and I'll release an update soon

---

### Post by falkTX on 2009-10-10
**Update:**
sixad is now compiled with the option "-m32" for PowerPC.
This will match the Ubuntu PowerPC[32] architecture (previously was PowerPC64) and, hopefully, solve the issue about not being able to run the binaries on the PS3.

Many thanks to digge for helping me on this!

---

### Post by digge on 2009-10-10
Force didnt seem to have any effect. Exactly the same happens as well as  sixad --force apears running as well as sixad-bin 1 1 1 1 ... and an instance of gksu for qtsixa --force

Not sure if this is to any help at all but here is what errors ive found so far.
```
sixad
Will use LED # 1
sixad[13596]: sixad started, press the PS button now
Server mode now active, will start search now
One event received
Will initiate Sixaxis now
One event proccessed
Changing LED # to 2
sixad[13618]: Connected PLAYSTATION(R)3 Controller (00:23:06:XX:XX:XX)
error on uinput ioctl (UI_SET_ABSBIT)

```

Syslog says this

```
Oct 11 03:12:56 ubuntu bluetoothd[13625]: Bluetooth daemon
Oct 11 03:12:56 ubuntu bluetoothd[13625]: Starting SDP server
Oct 11 03:12:56 ubuntu bluetoothd[13625]: Starting experimental netlink support
Oct 11 03:12:56 ubuntu bluetoothd[13625]: Failed to find Bluetooth netlink family
Oct 11 03:12:56 ubuntu bluetoothd[13625]: Can't create GN bridge
Oct 11 03:12:56 ubuntu bluetoothd[13625]: Registered interface org.bluez.Service on path /org/bluez/13625/any
Oct 11 03:12:56 ubuntu bluetoothd[13625]: HCI dev 0 registered
Oct 11 03:12:56 ubuntu bluetoothd[13625]: HCI dev 0 already up
Oct 11 03:12:56 ubuntu bluetoothd[13625]: Starting security manager 0
Oct 11 03:12:56 ubuntu bluetoothd[13625]: Registered interface org.bluez.NetworkPeer on path /org/bluez/13625/hci0
Oct 11 03:12:56 ubuntu bluetoothd[13625]: Registered interface org.bluez.NetworkHub on path /org/bluez/13625/hci0
Oct 11 03:12:56 ubuntu bluetoothd[13625]: Registered interface org.bluez.NetworkRouter on path /org/bluez/13625/hci0
Oct 11 03:12:56 ubuntu bluetoothd[13625]: Registered interface org.bluez.SerialProxyManager on path /org/bluez/13625/hci0
Oct 11 03:12:56 ubuntu bluetoothd[13625]: Registered interface org.bluez.Service on path /org/bluez/13625/hci0
Oct 11 03:12:56 ubuntu bluetoothd[13625]: Adapter /org/bluez/13625/hci0 has been enabled
Oct 11 03:14:09 ubuntu kernel: [ 2246.817299] ioctl32(gnome-terminal:13632): Unknown cmd fd(22) cmd(0000530b){t:'S';sz:0} arg(0ffd8d38) on /dev/pts/1
Oct 11 03:14:09 ubuntu kernel: [ 2246.817322] ioctl32(gnome-terminal:13632): Unknown cmd fd(22) cmd(0000530b){t:'S';sz:0} arg(0ffd8d40) on /dev/pts/1
Oct 11 03:14:09 ubuntu kernel: [ 2246.817341] ioctl32(gnome-terminal:13632): Unknown cmd fd(22) cmd(0000530b){t:'S';sz:0} arg(0ffd8d48) on /dev/pts/1
```

Im of to bed now though, getting late. Funny how easy it is to get hooked on troubleshooting ;)

---

### Post by falkTX on 2009-10-11
> **digge said:**
> Force didnt seem to have any effect. Exactly the same happens as well as  sixad --force apears running as well as sixad-bin 1 1 1 1 ... and an instance of gksu for qtsixa --force

Not sure if this is to any help at all but here is what errors ive found so far.
```
sixad
Will use LED # 1
sixad[13596]: sixad started, press the PS button now
Server mode now active, will start search now
One event received
Will initiate Sixaxis now
One event proccessed
Changing LED # to 2
sixad[13618]: Connected PLAYSTATION(R)3 Controller (00:23:06:XX:XX:XX)
error on uinput ioctl (UI_SET_ABSBIT)

```

(...)

Im of to bed now though, getting late. Funny how easy it is to get hooked on troubleshooting ;)

We should talk over IRC next time (I only started sleeping at 3 AM...)

I've faced with this error before. It seems that compiling UInput stuff requires "-m64" flag for PowerPC, but PowerPC64 binaries may not be compatible with the Ubuntu's PowerPC architecture...

I've updated sixad anyway, so please update your system and tell me if it works now

---

### Post by digge on 2009-10-11
ok, updated to latest from the repo and the "No such file or directory" is back. 

uname -r gives me 2.6.28-6-powerpc64-smp

so it seems im using a 64 bit kernel, ill have a look if there is a 32 bit one for testing if that is in fact the difference between working and not working.

Im up for IRC, would make it a lot easier to try things faster.

EDIT: 32 bit was a no go, just a few beeps and then black screen ;) Might be due to the configuration of the kernel, am not sure, but didnt boot up at least.

EDIT: also redowloaded the source and the file not found goes away but ioctl thing still there. Maybe im to fast here, maybe it was the file not found thing you were working on?

---

### Post by falkTX on 2009-10-12
> **digge said:**
> ok, updated to latest from the repo and the "No such file or directory" is back. 

uname -r gives me 2.6.28-6-powerpc64-smp

so it seems im using a 64 bit kernel, ill have a look if there is a 32 bit one for testing if that is in fact the difference between working and not working.

Im up for IRC, would make it a lot easier to try things faster.

EDIT: 32 bit was a no go, just a few beeps and then black screen ;) Might be due to the configuration of the kernel, am not sure, but didnt boot up at least.

EDIT: also redowloaded the source and the file not found goes away but ioctl thing still there. Maybe im to fast here, maybe it was the file not found thing you were working on?

Please try downloading the attached file, rename it to "Makefile" (Case sensitive!) and place on the sixad source folder. Then try compiling and report once again how it goes

---

### Post by digge on 2009-10-12
Tried it, got errors.
```

# make
gcc -Wall -m64 -O2 sdp.c textfile.c sixad.c -o bins/sixad-bin -lbluetooth
In file included from /usr/include/features.h:354,
                 from /usr/include/stdio.h:28,
                 from sdp.c:28:
/usr/include/gnu/stubs.h:9:27: error: gnu/stubs-64.h: No such file or directory
In file included from /usr/include/features.h:354,
                 from /usr/include/stdio.h:28,
                 from textfile.c:29:
/usr/include/gnu/stubs.h:9:27: error: gnu/stubs-64.h: No such file or directory
In file included from /usr/include/features.h:354,
                 from /usr/include/errno.h:29,
                 from sixad.c:9:
/usr/include/gnu/stubs.h:9:27: error: gnu/stubs-64.h: No such file or directory
make: *** [sixad-bin] Error 1
```

EDIT: made some googling and installed libc6-dev-ppc64 and now i get 

```
# make
gcc -Wall -m64 -O2 sdp.c textfile.c sixad.c -o bins/sixad-bin -lbluetooth
/usr/bin/ld: skipping incompatible /usr/lib/gcc/powerpc-linux-gnu/4.3.3/../../../libbluetooth.so when searching for -lbluetooth
/usr/bin/ld: skipping incompatible /usr/lib/libbluetooth.so when searching for -lbluetooth
/usr/bin/ld: cannot find -lbluetooth
collect2: ld returned 1 exit status
make: *** [sixad-bin] Error 1
```

---

### Post by falkTX on 2009-10-12
you should use my libbluetooth.so.3_powerpc that is in the 'compat' folder.
```
sudo cp ...PATH.../sixad/compat/libbluetooth.so.3_powerpc /usr/lib/libbluetooth.so.3
```

Then the compilation will be fine.

To restore the original file, reinstall the DEB package "libbluetooth3" in synaptic

---

### Post by digge on 2009-10-12
Now i get a new error.
```

make
gcc -Wall -m64 -O2 sdp.c textfile.c sixad.c -o bins/sixad-bin -lbluetooth
gcc -Wall -m64 -O2 sdp.c textfile.c sixad-uinput-sixaxis.c -o bins/sixad-uinput-sixaxis -lbluetooth
gcc -Wall -m64 -O2 sixpair.c -o bins/sixpair -lusb
/usr/bin/ld: skipping incompatible /usr/lib/gcc/powerpc-linux-gnu/4.3.3/../../../libusb.so when searching for -lusb
/usr/bin/ld: skipping incompatible /usr/lib/gcc/powerpc-linux-gnu/4.3.3/../../../libusb.a when searching for -lusb
/usr/bin/ld: skipping incompatible /usr/lib/libusb.so when searching for -lusb
/usr/bin/ld: skipping incompatible /usr/lib/libusb.a when searching for -lusb
/usr/bin/ld: cannot find -lusb
collect2: ld returned 1 exit status
make: *** [tools] Error 1

```

---

### Post by falkTX on 2009-10-12
This is not really needed now, just try if the new compiled binary has worked or not.
(if it did, then we take care of usb stuff)

---

### Post by falkTX on 2009-10-13
**Update:** - QtSixA 0.5.3 is here!
Changelog:
> qtsixa (0.5.3-falktx1)
  * Fixed "kdesu" usage in RPM distros [They don't echo to terminal, but open a separate session for sudo]
  * Added "PS3 UInput Fix" option (in "Configure Sixaxis")
  * Fixed checking battery of Sixaxis (will take a little longer, but it will [probably] work)

sixad (0.7-falktx1)
  * Final fixes for openSUSE compatibility (and maybe other RPM distros)
  * Warn to install 'libbluetooth.so.2' and 'hcid' manually, in Makefile [only needed when compiling from source]
  * Build all binaries on PowerPC with "-32" flag, except for UInput stuff (sixad-uniput-sixaxis and sixad-raw)
  [Otherwise UInput will fail to initialize]
  * Added sixad option "PS3 Fix for UInput" [When connecting a Sixaxis, initiates regular driver instead of the sixad one]
  * Auto-enable PS3 Fix if installing PowerPC sixad
  * Axis 0-3 (left & right axis) are now also centered at 0 when disabled

This release fix the issues on the PS3, but it costs disabling the sixad UInput driver (acceleremeters and enable/disable stuff).
I've tested it on a openSUSE LiveCD, and it worked fine

---

### Post by digge on 2009-10-13
Sorry for taking long to reply. Noticed you did some work on the uinput stuff without me, will try it out. For reference here is the output i get now, same as before with the uinput error.

```
sixad
Will use LED # 1
sixad[2875]: sixad started, press the PS button now
Server mode now active, will start search now
One event received
Will initiate Sixaxis now
sixad[2901]: Connected PLAYSTATION(R)3 Controller (00:23:06:D9:B5:D6)
One event proccessed
Changing LED # to 2
error on uinput ioctl (UI_SET_ABSBIT)

```

Will update to latest and give it a try. Thanks you for trying so hard! btw, tried your software on my laptop and i loved it ;)

EDIT: Tried the new build and works like a sharm, THANK YOU!

---

### Post by elfraser on 2009-10-13
First off, sorry if I sound like a moron, I'm new to Ubuntu/Linux.
I've got a ps3 with Jaunty installed.  Works great.
I've installed QtSixA 0.53 and it can recognize my two DS3 controllers.

Two problems, though:
1) When I try to create a profile, then add it, SixA tells me to restart the program and it will appear.  I restart and it's not there.
2) Giving up on my own profile, I've attempted to use the pre-configured ones.  The home screen on SixA says "Current Sixaxis profile is __" whatever I've chosen.  However, when I go and press the buttons on the DS3, nothing happens.  The buttons assigned to keys to not enter keys at the cursor spot, the mouse doesn't work, basically nothing happens.

Not sure if it's relevant, but under "Device Properties" on the home screen, it says the type is joystick and the status is unknown (??).


Thanks for your help!

---

### Post by falkTX on 2009-10-14
> **elfraser said:**
> First off, sorry if I sound like a moron, I'm new to Ubuntu/Linux.
I've got a ps3 with Jaunty installed.  Works great.
I've installed QtSixA 0.53 and it can recognize my two DS3 controllers.

Two problems, though:
1) When I try to create a profile, then add it, SixA tells me to restart the program and it will appear.  I restart and it's not there.
2) Giving up on my own profile, I've attempted to use the pre-configured ones.  The home screen on SixA says "Current Sixaxis profile is __" whatever I've chosen.  However, when I go and press the buttons on the DS3, nothing happens.  The buttons assigned to keys to not enter keys at the cursor spot, the mouse doesn't work, basically nothing happens.

Not sure if it's relevant, but under "Device Properties" on the home screen, it says the type is joystick and the status is unknown (??).


Thanks for your help!

1) Probably you're using an old PyQt package. Open "Software Sources" and add this repository:
```
deb http://ppa.launchpad.net/kubuntu-ppa/backports/ubuntu jaunty main
```Then update your system and all will be OK.
(The new Ubuntu version, Karmic, will not need this)

2) Sixaxis profiles are not working on the PS3 (a bug in some Ubuntu package somewhere...)
[https://bugs.launchpad.net/qtsixa/+bug/436720](https://bugs.launchpad.net/qtsixa/+bug/436720)
Any help is appreciated (I don't have a PS3)

And I still haven't found a way to know whatever a Sixaxis is fully working or not, so I just place there "Unknown".
Maybe I'll remove the "Status" thing, it's misleading

---

### Post by elfraser on 2009-10-14
> **falkTX said:**
> 1) Probably you're using an old PyQt package. Open "Software Sources" and add this repository:
```
deb http://ppa.launchpad.net/kubuntu-ppa/backports/ubuntu jaunty main
```Then update your system and all will be OK.
(The new Ubuntu version, Karmic, will not need this)

2) Sixaxis profiles are not working on the PS3 (a bug in some Ubuntu package somewhere...)
[https://bugs.launchpad.net/qtsixa/+bug/436720](https://bugs.launchpad.net/qtsixa/+bug/436720)
Any help is appreciated (I don't have a PS3)

And I still haven't found a way to know whatever a Sixaxis is fully working or not, so I just place there "Unknown".
Maybe I'll remove the "Status" thing, it's misleading

Tried adding the deb code but got the no key error.
Updated in the terminal anyways and got this:

W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 2836CB0A8AC93F7A
W: You may want to run apt-get update to correct these problems

Still no dice.  :(

UPDATE: Used this to get a key. Still not working though.
[http://kubuntuforums.net/forums/index.php?action=printpage%3Btopic=3103855.0](http://kubuntuforums.net/forums/index.php?action=printpage%3Btopic=3103855.0)

---

### Post by falkTX on 2009-10-15
You'll also need to enable jaunty-backports in "Software Sources" too
(sorry I forgot to mention that).

You can ignore the update error about a missing key and proceed with the update

---

### Post by falkTX on 2009-10-15
**Update:** - QtSixA 0.5.4

Changelog:
> qtsixa (0.5.4-falktx1)
  * In the "Configure Sixaxis" dialog:
    - New tab "Advanced"
    - Moved PS3 Fix option  to "Advanced"
    - Added experimental option 'Enable DualShock3 Rumble'
    - Other minor changes
  * Updated features.html to reflect recent changes to sixad code (rumble)
  * Warn if using an old PyQt version (< 4.5.0)
  * Disable, in "Configure Sixaxis", 'Add New Profile' button if PyQt < 4.5.0

sixad (0.8-falktx1)
  * Proper build for PowerPC:
    - Create separate 32bit and 64bit PowerPC packages
    - Build with "-m32" and "-m64" for 32 and 64 bit (respectively)
    - Only enable PS3 Fix/Workaround for PowerPC32
  * Experimental rumble support
  * Added TODO and CHANGELOG to sixad source
  * Small code cleanup

If you have a DS3, please test out the rumble feature. (The warning is just to scare the noob guys)
Don't ask me which games have Rumble/Force-Feedback, I don't know any (yet)

---

### Post by elfraser on 2009-10-15
> **falkTX said:**
> You'll also need to enable jaunty-backports in "Software Sources" too
(sorry I forgot to mention that).

You can ignore the update error about a missing key and proceed with the update


Tried that and then updated. Nope.
Then I tried to completely remove the package with Synaptic.  Did that, restarted, then used the sudo command to install again.  Still the same trouble.  It shows up in the gui but does not actually do anything.  I even tried different profiles.

When I do sudo apt-get update, this is what I get:

```
Get:1 http://falktx.xtreemhost.com jaunty Release.gpg [197B]
Hit http://ppa.launchpad.net jaunty Release.gpg                                                   
Ign http://ppa.launchpad.net jaunty/main Translation-en_US                 
Hit http://ppa.launchpad.net jaunty Release.gpg                            
Hit http://ports.ubuntu.com jaunty Release.gpg                             
Ign http://ports.ubuntu.com jaunty/main Translation-en_US                                   
Ign http://ports.ubuntu.com jaunty/restricted Translation-en_US                             
Ign http://ppa.launchpad.net jaunty/main Translation-en_US                                  
Hit http://ppa.launchpad.net jaunty Release                                                 
Get:2 http://falktx.xtreemhost.com jaunty/main Translation-en_US [11.5kB]                   
Ign http://ports.ubuntu.com jaunty/universe Translation-en_US                                        
Ign http://ports.ubuntu.com jaunty/multiverse Translation-en_US                      
Hit http://ports.ubuntu.com jaunty-updates Release.gpg                               
Ign http://ports.ubuntu.com jaunty-updates/main Translation-en_US                    
Ign http://ports.ubuntu.com jaunty-updates/restricted Translation-en_US              
Ign http://ports.ubuntu.com jaunty-updates/universe Translation-en_US                
Ign http://ports.ubuntu.com jaunty-updates/multiverse Translation-en_US              
Hit http://ports.ubuntu.com jaunty-security Release.gpg        
Hit http://ppa.launchpad.net jaunty Release                                          
Ign http://ports.ubuntu.com jaunty-security/restricted Translation-en_US                                  
Ign http://ports.ubuntu.com jaunty-security/main Translation-en_US                                        
Ign http://ports.ubuntu.com jaunty-security/universe Translation-en_US                                    
Ign http://ports.ubuntu.com jaunty-security/multiverse Translation-en_US                                  
Hit http://ports.ubuntu.com jaunty-backports Release.gpg                                     
Ign http://ports.ubuntu.com jaunty-backports/restricted Translation-en_US                    
Hit http://ppa.launchpad.net jaunty/main Packages                                            
Hit http://ppa.launchpad.net jaunty/main Sources                                             
99% [2 Translation-en_US bzip2 0] [Waiting for headers] [Connecting to falktx.xtreemhost.com]bzip2: (stdin) is not a bzip2 file.
Ign http://falktx.xtreemhost.com jaunty/main Translation-en_US                               
Ign http://ports.ubuntu.com jaunty-backports/main Translation-en_US                          
Ign http://ports.ubuntu.com jaunty-backports/multiverse Translation-en_US           
Ign http://ports.ubuntu.com jaunty-backports/universe Translation-en_US
Hit http://ports.ubuntu.com jaunty Release                    
Hit http://ports.ubuntu.com jaunty-updates Release            
Hit http://ppa.launchpad.net jaunty/main Packages                                                         
Hit http://ports.ubuntu.com jaunty-security Release                 
Hit http://ports.ubuntu.com jaunty-backports Release
Hit http://ports.ubuntu.com jaunty/main Packages                   
Hit http://ports.ubuntu.com jaunty/restricted Packages
Hit http://ports.ubuntu.com jaunty/universe Packages
Hit http://ports.ubuntu.com jaunty/multiverse Packages
Hit http://ports.ubuntu.com jaunty-updates/main Packages
Hit http://ports.ubuntu.com jaunty-updates/restricted Packages
Hit http://ports.ubuntu.com jaunty-updates/universe Packages
Hit http://ports.ubuntu.com jaunty-updates/multiverse Packages
Hit http://ports.ubuntu.com jaunty-security/restricted Packages
Hit http://ports.ubuntu.com jaunty-security/main Packages
Hit http://ports.ubuntu.com jaunty-security/universe Packages
Hit http://ports.ubuntu.com jaunty-security/multiverse Packages
Hit http://ports.ubuntu.com jaunty-backports/restricted Packages
Hit http://ports.ubuntu.com jaunty-backports/main Packages
Hit http://ports.ubuntu.com jaunty-backports/multiverse Packages
Hit http://ports.ubuntu.com jaunty-backports/universe Packages
Get:3 http://falktx.xtreemhost.com jaunty Release [4958B]
Ign http://falktx.xtreemhost.com jaunty Release
Hit http://falktx.xtreemhost.com jaunty/main Packages
Fetched 16.6kB in 2s (5645B/s)
Reading package lists... Done
W: GPG error: http://falktx.xtreemhost.com jaunty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 1E08B5104443AAA5
W: You may want to run apt-get update to correct these problems
```


Going back to what you suggested earlier about an outdated PyQt package, when I added backports, it updated something to do with sound nothing with PyQt.  Synaptic shows me as having qt 4.5 (libqtcore4), in addition to a bunch of other qt related things, including python-qt4 v4.4.4-2ubuntu6.  Is that what I should have?

---

### Post by falkTX on 2009-10-16
The command:
```
sudo apt-get update
```
Only update the list of software for download.

To REALLY update your system run this after it:
```
sudo apt-get dist-upgrade
```

---

### Post by elfraser on 2009-10-19
> **falkTX said:**
> The command:
```
sudo apt-get update
```Only update the list of software for download.

To REALLY update your system run this after it:
```
sudo apt-get dist-upgrade
```

I wasn't clear from your post, do I need to use the upgrade to get all the proper versions of stuff?  This may be a dumb question but does dist-upgrade upgrade the OS or is it really just a thorough update?

I tried to upgrade from Intrepid to Jaunty using Synaptic and it totally f'd up the PS3.  So I'm not keen on doing so again.

---

### Post by falkTX on 2009-10-19
> **elfraser said:**
> I wasn't clear from your post, do I need to use the upgrade to get all the proper versions of stuff?  This may be a dumb question but does dist-upgrade upgrade the OS or is it really just a thorough update?

I tried to upgrade from Intrepid to Jaunty using Synaptic and it totally f'd up the PS3.  So I'm not keen on doing so again.

*dist-upgrade* only installs additional packages require to update.
It will not update to a new OS version (like Intrepid to Jaunty)

---

### Post by falkTX on 2009-10-20
**Update:** - QtSixA 0.6.0!
Changelog:
> qtsixa (0.6.0-falktx1)
  * Fixed bluetooth Keypad always appearing as USB Keypad, in notifications
  * Fixed some game profiles not applied properly
  * Updated "Configure Sixaxis" and "Sixaxis Reference" dialogs to match sixad updates
  * Added "Final Fantasy VIII PC" profile
  * Other small fixes as usual

sixad (0.9-falktx1)
  * Preparations for v1.0 stable release: (remove unnecessary stuff, clean the rest)
    - Removed accelerometer buttons (not really needed and a little confusing)
    - Moved "gyro" to "accelerometers" section (but disabled for now)
    - Moved rumble (experimental) to "Input events"
    - Changed all "PS3 Fix" text to "Legacy driver"
    - Added "Position" axis (25-28 )
    - Increased timeout for Acceleration/Speed/Position values
    - Cleaned up the accelerometers code (cause they can be disabled at any time)
  * Start 0,1,2,3 axis at 0
  * New option - set LED # according to joystick # (default now; js0 will be LED 1)
  * New option - start sixad at boot (disables normal bluetooth; can be stopped anytime)
  * Show sixad configuration when starting from terminal
  * Applied same updates for sixad-raw
  * Temporarily enable some debug output for 'sixad-uniput-sixaxis'
  * Fixed weird random input to axis 0-3
  * Disable Acceleration/Speed/Position by default (but keep Accelerometers)

The most notable update is that the Sixaxis sets its LED # depending on which joystick it is, instead of going +1 for each new connection

I'm preparing QtSixA/sixad to be really stable and useful, so feel free to post any comments.
Although QtSixA will not make it into Karmic, I believe it will be available for 10.04/Lucid, in universe.

Right now I need:
 - Someone who has a DualShock3 to test and report Rumble
 - Someone with a PS3 (and some free time), to test new fixes to the PowerPC32 UInput issue

---

### Post by elfraser on 2009-10-20
> **falkTX said:**
> *dist-upgrade* only installs additional packages require to update.
It will not update to a new OS version (like Intrepid to Jaunty)

Did this.  Not sure if it's a .60 bug or what but now the sixaxis controllers won't even connect to the system.  They'll blink for a while (and show up in connected devices) but then go away.  They cannot move the cursor (or presumably do anything) during this time.

Pressing the PS button on the controller makes the bluetooth adapter disappear as well. 

:(

---

### Post by falkTX on 2009-10-21
> **elfraser said:**
> Did this.  Not sure if it's a .60 bug or what but now the sixaxis controllers won't even connect to the system.  They'll blink for a while (and show up in connected devices) but then go away.  They cannot move the cursor (or presumably do anything) during this time.

Pressing the PS button on the controller makes the bluetooth adapter disappear as well. 

:(

The bluetooth icon disapearing is normal.
Have you paired yours Sixaxis yet? (in menu Tasks -> Pair Sixaxis to PC)

Then IT WILL connect (but needs pairing first).
If not, use the "Force Connection" menu

---

### Post by Slumz187 on 2009-10-21
alright I did everything, got system and packages updated, loaded up your program..

now im having trouble using it...

first i opened your app, paired it with the usb cable attached, started bluetooth and unattached controller, no go!

then i did the same thing all over again and even clicked on use this device as mouse and keypad, with cable attached no go!

dude i am going insane here please help,

ive  been trying to pair this controller and use a decent emulator since yesterday, i am having crazy issues!

---

### Post by Okiura on 2009-10-21
> **falkTX said:**
> **Update:**
Right now I need:
 - Someone who has a DualShock3 to test and report Rumble
 - Someone with a PS3 (and some free time), to test new fixes to the PowerPC32 UInput issue

I have all of the above :)

---

### Post by Slumz187 on 2009-10-21
i solved it, thanx for the program man, i can only use it via usb thought.. im too wore out to even try and figure it out...

also if anyone can help by posting a tutorial on getting the sixaxis controller to work as mouse id gladly appreciate it!

---

### Post by elfraser on 2009-10-21
How did you get it to work with USB?  What steps did you follow? I can't get mine to work even with the USB.
I get the device to show up but it doesn't do anything . . .

---

### Post by Okiura on 2009-10-21
Hi,

I just updated to the new version 0.6.0 and it seem I've lost the ability to conned via Bluetooth :)

I have tried a few things to get this working:

I tested the driver via USB using the HID-raw driver and all works ok.

I've removed all paired device and reset all configs back to default, then I re-paired the devices (pairing was successful) but still un-able to connect.

I tried using the Force connection option from the Tasks menu, this disabled my Bluetooth for all other connections but it didn't allow me to connect 

Lastly I tried running from terminal (This is the same as force connection?):

```

xeon@xeon-laptop:~$ sixad --stop

xeon@xeon-laptop:~$ sixad
sixad settings:
Enable LEDs:	3
js# as LED #:	0
Start LED #:	3
LED # increase:	1
LED animation:	1
Buttons:	1
Sens. buttons:	1
Axis:		1
Accelerometers:	0
Acceleration:	0
Speed:		0
Position:	0
Rumble:		1
sixad[12412]: sixad started, press the PS button now
Server mode now active, will start search now


```

What I'm seeing at the moment when I press the PS button (non forced connection) my DS3's BT-MAC address shows in QtSixA > list of connected devices at the same time my system Bluetooth disabled and the four leds on my DS3 blink on/off twice a second (connecting?), then the device disappears from QtSixA > list of connected devices and my Bluetooh is re-enabled. This happens about 3-4 times before the DS3 gives up and turns off. 

If I use the Force connection option (or run from terminal) the same thing happens with the exception of my system Bluetooth be permanently disabled.

One more thing I noticed is no Bluetooh HID/input device is added when the PS button is pressed, in-fact neither dmesg or /var/logs/messages register anything going on at all, not to sure about /var/logs/messages (as I don't often check it) but dmesg always showed a Bluetooth HID/input device being connected almost as soon as the PS button was pressed in previous versions.


This looks like the same issue Slumz187 & Elfraser have reported above

if you need any further info/test let me know,

Okiura,

---

### Post by Okiura on 2009-10-22
> **elfraser said:**
> How did you get it to work with USB?  What steps did you follow? I can't get mine to work even with the USB.
I get the device to show up but it doesn't do anything . . .

When you connect the device via used does the system recognise it it correctly? two ways to check is dmesg output and jstest.

dmesg output (all the useless stuff edited out)

```


xeon@xeon-laptop:~$ dmesg

*lots of useless removed from here* 

[ 7622.700174] input: Sony PLAYSTATION(R)3 Controller as /devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1:1.0/input/input14
[ 7622.700346] sony 0003:054C:0268.0004: input,hiddev96,hidraw0: USB HID v1.11 Joystick [Sony PLAYSTATION(R)3 Controller] on usb-0000:00:1d.0-1/input0
xeon@xeon-laptop:~$ 


```

and jstest output

```


xeon@xeon-laptop:~$ jstest /dev/input/js0 

*once again useless info remove form here*

Axes:  0:-32767  1:-32767  2:-32767  3:-32767  4:-32767  5:-32767  6:-32767  7:-32767  8:-32767
9:-32767 10:-32767 11:-32767 12:-32767 13:-32767 14:-32767 15:-32767 16:-32767 17:-32767 18:-32767 19:-32767 20:-32767 21:-32767 22:-32767 23:-32767 24:-32767 25:-32767 26:-32767 27:
0 Buttons:  0:off  1:off  2:off  3:off  4:off  5:off  6:off  7:off  8:off  9:off 10:off 11:off
12:off 13:off 14:off



```

Notice how all the axis's read "-32767" if you see this then your controller is connected but will not work, simply press the PS button and axis's 0-3 will return to 0 and the controller is ready to use with the legacy driver (moving the joystick should increase and decrease the value of axis's 0-3 the rest are button axis's these will remain at "-32767" till a button is pressed).

To use the non-legacy driver HID-raw open QtsixA and go to the advanced tab here you'll see two refresh buttons click the bottom one, the dropdown box above should then fill with a device in most cases there will be only 1 device in the list if there is more than 1 then use the dmesg output to determine the correct one, from my dmesg output (input,hiddev96,hidraw0) I can see the correct one is "/dev/hidraw0". Once selected click apply (next to refresh) when prompted enter your system password and you should then see a conformation box confirming the connection, if at this point QtSixA fades out and appears to have crash press the PS button that should bring it back to life.

if all goes well you are now connected using the HID-raw driver, one final note here is that the original legacy driver is not unloaded this remains on "/dev/input/js0" the HID-raw driver will be loaded as a new js device "/dev/input/js1" 

hope this helps you

Okiura,

---

### Post by Slumz187 on 2009-10-22
yeah it seems as if something disabled all bluetooth compatibility with the sixaxis controller.
I tried almost everything and the results were negative But all i did to get the joystick to work was simply follow the initial installation instructions, run the program, pair the device with usb connected, then disabled bluetooth, by pressing stop, forcing a coonection, and then i think(im not at home now) in the advanced tab enabled 1:1 playstation controller option!  the way i tested it was simple to, i just installed snes9gtx and in the button configuration toggled sixaxis until the buttons started changing and thats how i finally figured it out! alot of noob trial and error lol

---

### Post by falkTX on 2009-10-22
> **Slumz187 said:**
> alright I did everything, got system and packages updated, loaded up your program..

now im having trouble using it...

first i opened your app, paired it with the usb cable attached, started bluetooth and unattached controller, no go!

then i did the same thing all over again and even clicked on use this device as mouse and keypad, with cable attached no go!

dude i am going insane here please help,

ive  been trying to pair this controller and use a decent emulator since yesterday, i am having crazy issues!


update your system once again - I've released an update.
This one now has a quick manual in "Help" -> "Manual"
Everyone with problems should read it

---

### Post by falkTX on 2009-10-22
> **Okiura said:**
> I have all of the above :)

Nice!

Please PM me with your mail, so we can start on business

---

### Post by falkTX on 2009-10-22
> **Okiura said:**
> What I'm seeing at the moment when I press the PS button (non forced connection) my DS3's BT-MAC address shows in QtSixA > list of connected devices at the same time my system Bluetooth disabled and the four leds on my DS3 blink on/off twice a second (connecting?), then the device disappears from QtSixA > list of connected devices and my Bluetooh is re-enabled. This happens about 3-4 times before the DS3 gives up and turns off. 

If I use the Force connection option (or run from terminal) the same thing happens with the exception of my system Bluetooth be permanently disabled.

One more thing I noticed is no Bluetooh HID/input device is added when the PS button is pressed, in-fact neither dmesg or /var/logs/messages register anything going on at all, not to sure about /var/logs/messages (as I don't often check it) but dmesg always showed a Bluetooth HID/input device being connected almost as soon as the PS button was pressed in previous versions.


This looks like the same issue Slumz187 & Elfraser have reported above

if you need any further info/test let me know,

Okiura,

Maybe your using 2 bluetooth sticks ? (internal and external usb)
I know that it will not work with 2 at same time (pairing only sets for the first stick/dongle/pen)

I think I need to go one user at a time.
Let's start with U Okiura, mail me so we can fix these problems

---

### Post by falkTX on 2009-10-22
**Update:** v1.0 Beta - final version is coming!
Changelog:
>   * QtSixA:
    - Changed homepage to 'http://qtsixa.sourceforge.net'
    - Fixed crash when creating a new profile using old PyQt (create button is now available)
    - Do not display warning about old PyQt anymore (bug fixed)
    - Fixed script to add new profile (it works now)
    - Allow any filetype to be selected as fdi profile to add
    - Finally wrote the manual!
    - A last check to the code, fixing all the possible bugs still around
  * sixad:
    - Small cleanup of code
    - Read sixad configuration file when connecting a new Sixaxis
    [You don't have to stop sixad to applied configuration changes]
    - Lots of debug stuff

I'm preparing the final version, so please update your Linux and check if QtSixA works for you.
I know that it's not working for everyone and *I want* to help.
One user at a time, I hope I can fix most problems.

Also check the manual (Help->Manual) if you're having problems with QtSxiA

---

### Post by Slumz187 on 2009-10-22
ok..im trying to upgrade but i guess its not posted on the server yet or something! because its telling me i have the newest version installed already which is the one im having trouble with!

---

### Post by falkTX on 2009-10-22
> **Slumz187 said:**
> ok..im trying to upgrade but i guess its not posted on the server yet or something! because its telling me i have the newest version installed already which is the one im having trouble with!

hmm... try again in 5 minutes

---

### Post by Slumz187 on 2009-10-22
aight upgrade went just fine..had to use 

sudo apt-get upgrade dist-upgrade option! now im off to test this baby out! lol

---

### Post by falkTX on 2009-10-22
I've created an IRC channel:

server: irc.freenode.net
channel: #qtsixa


Or use Windows MSN:

falk.t.j / _at_ / hotmail.com



Please let's talk about bugs there

---

### Post by Slumz187 on 2009-10-22
falk is there any suggestions on connecting besides the ones in the tutorial? 

a tleast to just connect via usb , and blue tooth seems pretty difficult to configure even with manual !

also after pairing device and configuring its settings, does it take a reboot for changes to take effect or is it okay after you exit and open the application back up?

---

### Post by falkTX on 2009-10-22
> **Slumz187 said:**
> falk is there any suggestions on connecting besides the ones in the tutorial? 

a tleast to just connect via usb , and blue tooth seems pretty difficult to configure even with manual !

also after pairing device and configuring its settings, does it take a reboot for changes to take effect or is it okay after you exit and open the application back up?

The update says that you don't need to stop sixad for apply the new settings. However, you still have to re-connect the Sixaxis.

Can't you just connect with a USB cable and press the PS button? (the one in the middle)
It _*always*_ works in USB that way

---

### Post by falkTX on 2009-10-22
**Update:**
After some time chatting with Okiura, I've found the problem that was making sixad not detecting any devices.
It was just 3 lines of code removed that, although seemed useless, it is necessary to a proper server mode.

Update your Linux and enjoy!

---

### Post by Slumz187 on 2009-10-22
thx for the update falk..
ive followed instructions according to the manual still a no go..
it recognizes the device fine, but the leds keeping blinking

i forced it to stop, amd then forced connection..that doesnt work...
also in my dmesg files when i usually do this while sixaxis is connected to the usb, i get hidraw2 and the results are normal..but when i do this while connected to bluetooth i get errors



gelic_eurus_sync_cmd_worker: cmd issue failed and
in gnome terminal ) unknown command

should i update again?

---

### Post by falkTX on 2009-10-23
> **Slumz187 said:**
> thx for the update falk..
ive followed instructions according to the manual still a no go..
it recognizes the device fine, but the leds keeping blinking

i forced it to stop, amd then forced connection..that doesnt work...
also in my dmesg files when i usually do this while sixaxis is connected to the usb, i get hidraw2 and the results are normal..but when i do this while connected to bluetooth i get errors



gelic_eurus_sync_cmd_worker: cmd issue failed and
in gnome terminal ) unknown command

should i update again?

try purging the packages and reinstall
```
sudo apt-get --purge qtsixa sixad
sudo apt-get install -f
sudo apt-get update
sudo apt-get install qtsixa sixad
```

Meet me at IRC for a faster solving of issues:

irc.freenode.net
#qtsixa


edit: your error is related to a wireless network issue, nothing about QtSixA
edit2: I don't have net access at home, so no chatting on the weekends...

---

### Post by falkTX on 2009-10-23
**Update:** 1.0 RC
Changelog:
> qtsixa (1.0-falktx{1,2})
  * Removed "Status" from main device properties
  * Fixed "list of devices" unselectable when only USB devices were connected
  * Auto-add *.fdi extension to new created profiles
  * Revert "Allow any filetype to be selected as fdi profile to add"
  * Fixed not showing fdi/png files in browser when adding a new profile (only happened on Gnome)
  * Marked update as RC

sixad (1.0-falktx{1,2})
  * Fixed sixad search for devices
  * Trying to fix random input bug (disabling axis deadzones)

Can you guys report if the Sixaxis connects over bluetooth now?

---

### Post by nxmehta on 2009-10-23
Minor issue, but something I asked about before... I'm running Ubuntu 9.04, and I still see a ~/sixa-notify file being created on session startup.  I was hoping that could be made to be a hidden file like ~/.sixa-notify or something like that.  Could you fix that?

---

### Post by elfraser on 2009-10-23
> **Okiura said:**
> When you connect the device via used does the system recognise it it correctly? two ways to check is dmesg output and jstest.

```


xeon@xeon-laptop:~$ jstest /dev/input/js0 

*once again useless info remove form here*

Axes:  0:-32767  1:-32767  2:-32767  3:-32767  4:-32767  5:-32767  6:-32767  7:-32767  8:-32767
9:-32767 10:-32767 11:-32767 12:-32767 13:-32767 14:-32767 15:-32767 16:-32767 17:-32767 18:-32767 19:-32767 20:-32767 21:-32767 22:-32767 23:-32767 24:-32767 25:-32767 26:-32767 27:
0 Buttons:  0:off  1:off  2:off  3:off  4:off  5:off  6:off  7:off  8:off  9:off 10:off 11:off
12:off 13:off 14:off



```Okiura,

How's this for weird: when I did the jstest command it said
bash: jstest: command not found.

Maybe the xbuntu distribution that comes prepackaged (by Ubuntu) for the PS3 doesn't include it?

How would I go about adding it?

---

### Post by Okiura on 2009-10-24
> **elfraser said:**
> How's this for weird: when I did the jstest command it said
bash: jstest: command not found.

Maybe the xbuntu distribution that comes prepackaged (by Ubuntu) for the PS3 doesn't include it?

How would I go about adding it?

My bad there ^^ you need to install it, it doesn't come installed on any Ubuntu distros as far as i'm aware but it is in the Ubuntu repo so,

```
 sudo apt-get install joystick 
```

should do the trick and get the app installed, I should point out though this is not a required application it's just purely for testing the joystick.

Okiura,

---

### Post by Slumz187 on 2009-10-24
thats the same thing i was looking at as well Elfraser, but its a bummer to know that its no necessity with getting the application and/or bluetooth working!


btw, falk can you explain this error-


sixad-debug[5776]:debug mode started
error on uinput ioctl (UI_SET_ABSBIT)

---

### Post by elfraser on 2009-10-24
> **Okiura said:**
> My bad there ^^ you need to install it, it doesn't come installed on any Ubuntu distros as far as i'm aware but it is in the Ubuntu repo so,

```
 sudo apt-get install joystick 
```should do the trick and get the app installed, I should point out though this is not a required application it's just purely for testing the joystick.

Okiura,

Thanks, figured it out before I saw this.  Well, the good news is that with joystick installed it works with USB.  I actually didn't have to use the program to use the sixaxis.  I just used your command lines (dmesg, etc.) and it usually worked.

Occasionally I was getting some weird stuff when I entered dmesg, but I just restarted and it usually found the controller.

Couldn't get two controllers to show up on the PS3, though... not sure why not.

And the bluetooth connection is still a no-go.  Thanks for your help with getting it via USB, though!

---

### Post by Okiura on 2009-10-24
> **elfraser said:**
> 

Occasionally I was getting some weird stuff when I entered dmesg, but I just restarted and it usually found the controller.



The weird stuff you saw was most likely the output from the kernel, all the dmesg command really does is show you the output from the kernel so you see what the kernel is up to. You normally only use it if you want to see what the kernel is doing, in this case we wanted to see if the kernel was seeing the controller when we connected it. Nether of the two commands i stated in my previous post (dmesg,jstest) are needed to get this working via USB both are just used to lets us see what is going on when you connect the device.

Strange it started working via USB though once you installed the joystick app, as the legacy module is compiled into the kernel it should just work when you connect the device. the joystick app is purely for testing and calibration. maybe FalkTx knows why this is.

I'm just finishing off a fresh install of Karmic on my ps3 (after 2 days of nothing but problems) i will test some more.

Okiura,

---

### Post by Okiura on 2009-10-25
Ok i have now managed to get Ubuntu Karmic installed on my ps3 :)

Before installing any new programs I did a little test:

Connect a DS3 via USB then 'cat' the device, the raw input is displayed. this confirms that the joystick app is not required to get this to work via USB. 

So next I installed Qtsixa and paired the DS3 unplugged and pressed the PS button... connected!!! 'cat' the device again and i got even more jibberish on the screen so the g-sensors are working too.

One issue I've spotted so far is profiles do not work, I can set them ok and the xorg logs shows that keys are being mapped to axis's, the same build (but x86) works fine on my laptop.

FalkTX we can discuss this further on IRC to keep the forum clean if you like.

Also you guys having connection issues can log on to the IRC room too I may be able to help get you connected.

To connect to the IRC room open pidgin (under apps > internet) and add a new IRC account with the following info:

Username: just enter something unique,
Server: irc.freenode.net
Password: you can just leave it blank,
Local Alias: use your forum name

don't change any other settings and click add. once a window pops up type:

```
 /join #qtsixa 
```

and hit enter, this will be enough to get you connected. if you have any issue getting connected PM me or search google ^^

Okiura,

---

### Post by falkTX on 2009-10-25
> **nxmehta said:**
> Minor issue, but something I asked about before... I'm running Ubuntu 9.04, and I still see a ~/sixa-notify file being created on session startup.  I was hoping that could be made to be a hidden file like ~/.sixa-notify or something like that.  Could you fix that?

I noticed that it happens on Gnome but not on KDE.
It's a weird thing, cause I always make the file hidden and in "/tmp".

Maybe you can help:
1. I suspect that the file is only created when "start notifications at session startup" is checked. Is that true?

2. Is sixa-notify also created in /tmp?
```
ls -a /tmp | grep sixa-notify
```

---

### Post by falkTX on 2009-10-25
> **Okiura said:**
> Ok i have now managed to get Ubuntu Karmic installed on my ps3 :)

Before installing any new programs I did a little test:

Connect a DS3 via USB then 'cat' the device, the raw input is displayed. this confirms that the joystick app is not required to get this to work via USB. 

So next I installed Qtsixa and paired the DS3 unplugged and pressed the PS button... connected!!! 'cat' the device again and i got even more jibberish on the screen so the g-sensors are working too.

One issue I've spotted so far is profiles do not work, I can set them ok and the xorg logs shows that keys are being mapped to axis's, the same build (but x86) works fine on my laptop.

FalkTX we can discuss this further on IRC to keep the forum clean if you like.

Also you guys having connection issues can log on to the IRC room too I may be able to help get you connected.

To connect to the IRC room open pidgin (under apps > internet) and add a new IRC account with the following info:

Username: just enter something unique,
Server: irc.freenode.net
Password: you can just leave it blank,
Local Alias: use your forum name

don't change any other settings and click add. once a window pops up type:

```
 /join #qtsixa 
```

and hit enter, this will be enough to get you connected. if you have any issue getting connected PM me or search google ^^

Okiura,

Thanks Okiura for helping out.

I'm not sure why the profiles don't work, but I think it may be related to xserver-xorg-input-joystick package.
I think that package it's broken in PowerPC.
[https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-input-joystick/+bug/358211](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-input-joystick/+bug/358211)

---

### Post by falkTX on 2009-10-25
**Update:** *qtsixa/sixad (1.0-falktx3)*

Changelog:
> 
  * QtSixA:
    - All bluetooth devices appear in the list, so updated features to match that
  * sixad:
    - Re-enabled axis deadzones
    - Deadzones also for Accelerometers and Accel/Speed/Position
    - The accelerometers are now properly centered
    - Small rumble effect along with LEDs animation
    - Fixed rumble activating all LEDs
    - Removed most rumble code for now (looking for the best way to implement it)
    - Only process packets if received from a Sixaxis (may fix random uinput bug)

---

### Post by falkTX on 2009-10-25
**Update:** *(1.0-falktx4)*

Changelog:
>   * QtSixA:
    - Changed rumble feature to "Incomplete"
    - Added debug on/off option in "Configure Sixaxis"/"Advanced"
  * sixad:
    - *REALLY* Only process packets if received from a Sixaxis (Random uinput bug now fixed!)
    [print "got non-Sixaxis packet and ignored" for debug purposes]
    - Added debug on/off option

We're almost 1.0 final.

Known bugs:
1 - Sixaxis profiles don't work on PS3
2 - sixad-notify created in home folder
3 - sixad not auto-connecting in some cases.


I really want to make this work stable, so please test out this:
run in a terminal:
```
sixad --stop
sixad
```
and press the PS button on the Sixaxis.

If the Sixaxis desn't get connected - PLEASE SAY IT!


I really don't know how to fix bug 1;
I'll look around bug 2;
I NEED your help for bug 3.


Once these 3 bugs are fixed, I'll release 1.0 final

---

### Post by nxmehta on 2009-10-25
> **falkTX said:**
> I noticed that it happens on Gnome but not on KDE.
It's a weird thing, cause I always make the file hidden and in "/tmp".

Maybe you can help:
1. I suspect that the file is only created when "start notifications at session startup" is checked. Is that true?

2. Is sixa-notify also created in /tmp?
```
ls -a /tmp | grep sixa-notify
```

1. I'll test this out later today- in the middle of some important stuff so don't want to restart my session yet...

2. I see a file called "/tmp/sixa-notify;" in addition to my ~/sixa-notify file.  That *includes* the semicolon.  Which is obviously weird ;)

---

### Post by falkTX on 2009-10-26
> **nxmehta said:**
> 1. I'll test this out later today- in the middle of some important stuff so don't want to restart my session yet...

2. I see a file called "/tmp/sixa-notify;" in addition to my ~/sixa-notify file.  That *includes* the semicolon.  Which is obviously weird ;)

I'll just install Gnome...
Karmic is almost here - I'll be formatting my PC soon - so it's not a big deal.
I hope this gets fixed for once.

See ya soon

---

### Post by Okiura on 2009-10-26
> **falkTX said:**
> **Update:** *(1.0-falktx4)*

Known bugs:
1 - Sixaxis profiles don't work on PS3



I got it working with the standard xserver-input-joystick, I don't know enough about HAL to fix it using the fdi's but i do know X so i've been making custom Xorg.conf's. at this point I have a really messy Xorg.conf but it does work, So tomorrow i'll back track and find out which option got this working and post it here for you.

EDIT >> It seems the enable-mouse & enable-keys option is set to 0 by default, So i mapped a button to to these options in the gnome.fdi copied it in to the profiles directory and selected. I hit the button button for disable-mouse and  hit the button for disable-keys then the whole lot came alive and it now works!! so i guess the  the trick is to either try and enable to by default or maybe map it to the PS button and have the option to enable and disable the joystick. 

Okiura,

---

### Post by elfraser on 2009-10-26
Still a no-go on the bluetooth connection on my PS3 (using 1.0-RC).
This is what I get from my dmesg, hope it helps someone will the skillz to figure out what's wrong.
```
[    0.000000] Using PS3 machine description
[    0.000000] Page orders: linear mapping = 24, virtual = 12, io = 12, vmemmap = 12
[    0.000000] Found initrd at 0xc000000000d9c000:0xc0000000016a6000
[    0.000000] CPU maps initialized for 2 threads per core
[    0.000000]  (thread shift is 1)
[    0.000000] Starting Linux PPC64 #20-Ubuntu SMP Fri Apr 17 09:59:41 UTC 2009
[    0.000000] -----------------------------------------------------
[    0.000000] ppc64_pft_size                = 0x14
[    0.000000] physicalMemorySize            = 0x8000000
[    0.000000] htab_hash_mask                = 0x1fff
[    0.000000] -----------------------------------------------------
[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Linux version 2.6.28-6-powerpc64-smp (buildd@adare) (gcc version 4.3.3 (Ubuntu 4.3.3-5ubuntu4) ) #20-Ubuntu SMP Fri Apr 17 09:59:41 UTC 2009 (Ubuntu 2.6.28-6.20-powerpc64-smp)
[    0.000000] *** 0000 : CF000012
[    0.000000] 
[    0.000000] *** 0000 : Setup Arch
[    0.000000] [boot]0012 Setup Arch
[    0.000000] Top of RAM: 0x8000000, Total RAM: 0x8000000
[    0.000000] Memory hole size: 0MB
[    0.000000] PS3 firmware version 3.0.1
[    0.000000] ps3fb videomemory: 9437184 bytes at c000000002100000
[    0.000000] ps3flash bounce buffer: 262144 bytes at c000000002a00000
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA      0x00000000 -> 0x00008000
[    0.000000]   Normal   0x00008000 -> 0x00008000
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[1] active PFN ranges
[    0.000000]     0: 0x00000000 -> 0x00008000
[    0.000000] On node 0 totalpages: 32768
[    0.000000]   DMA zone: 448 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 32320 pages, LIFO batch:7
[    0.000000]   Normal zone: 0 pages used for memmap
[    0.000000]   Movable zone: 0 pages used for memmap
[    0.000000] *** 0000 : CF000015
[    0.000000] 
[    0.000000] *** 0000 : Setup Done
[    0.000000] [boot]0015 Setup Done
[    0.000000] Built 1 zonelists in Node order, mobility grouping on.  Total pages: 32320
[    0.000000] Policy zone: DMA
[    0.000000] Kernel command line: root=UUID=89637ea1-f52c-4ff4-9704-0066ef7af592 quiet 
[    0.000000] PID hash table entries: 512 (order: 9, 4096 bytes)
[    0.000000] time_init: decrementer frequency = 79.800000 MHz
[    0.000000] time_init: processor frequency   = 3192.000000 MHz
[    0.000000] clocksource: timebase mult[3220149] shift[22] registered
[    0.000000] clockevent: decrementer mult[146d] shift[16] cpu[0]
[    0.000048] Console: colour dummy device 80x25
[    0.000054] console [tty0] enabled
[    0.000119] Dentry cache hash table entries: 16384 (order: 5, 131072 bytes)
[    0.000276] Inode-cache hash table entries: 8192 (order: 4, 65536 bytes)
[    0.000354] freeing bootmem node 0
[    0.008206] Memory: 101548k/131072k available (6988k kernel code, 29524k reserved, 832k data, 597k bss, 316k init)
[    0.008280] SLUB: Genslabs=13, HWalign=128, Order=0-3, MinObjects=0, CPUs=2, Nodes=16
[    0.008319] Calibrating delay loop... 159.23 BogoMIPS (lpj=318464)
[    0.088169] Security Framework initialized
[    0.088182] SELinux:  Disabled at boot.
[    0.088232] AppArmor: AppArmor initialized
[    0.088252] Mount-cache hash table entries: 256
[    0.088600] Initializing cgroup subsys ns
[    0.088607] Initializing cgroup subsys devices
[    0.088613] Initializing cgroup subsys freezer
[    0.089168] clockevent: decrementer mult[146d] shift[16] cpu[1]
[    0.089176] Processor 1 found.
[    0.089204] Brought up 2 CPUs
[    0.089303] CPU0 attaching sched-domain:
[    0.089308]  domain 0: span 0-1 level SIBLING
[    0.089315]   groups: 0 1
[    0.089324]   domain 1: span 0-1 level NODE
[    0.089329]    groups: 0-1
[    0.089340] CPU1 attaching sched-domain:
[    0.089344]  domain 0: span 0-1 level SIBLING
[    0.089349]   groups: 1 0
[    0.089358]   domain 1: span 0-1 level NODE
[    0.089363]    groups: 0-1
[    0.097304] net_namespace: 1368 bytes
[    0.130810] regulator: core version 0.5
[    0.130883] NET: Registered protocol family 16
[    0.130924] IBM eBus Device Driver
[    0.131272] *** 0000 : Linux ppc64
[    0.131274] 
[    0.131278] *** 0000 : #20-Ubuntu SMP Fri Apr 17 09:59:41 UTC 2009
[    0.131286] CPU Hotplug not supported by firmware - disabling.
[    0.131428] PCI: Probing PCI hardware
[    0.131435] PCI: Probing PCI hardware done
[    0.133152] usbcore: registered new interface driver usbfs
[    0.133192] usbcore: registered new interface driver hub
[    0.133307] usbcore: registered new device driver usb
[    0.144298] NET: Registered protocol family 8
[    0.144303] NET: Registered protocol family 20
[    0.144429] AppArmor: AppArmor Filesystem Enabled
[    0.144811] NET: Registered protocol family 2
[    0.148297] Switched to high resolution mode on CPU 0
[    0.149350] Switched to high resolution mode on CPU 1
[    0.180354] IP route cache hash table entries: 1024 (order: 1, 8192 bytes)
[    0.180473] TCP established hash table entries: 4096 (order: 4, 65536 bytes)
[    0.180506] TCP bind hash table entries: 4096 (order: 4, 65536 bytes)
[    0.180578] TCP: Hash tables configured (established 4096 bind 4096)
[    0.180584] TCP reno registered
[    0.192402] NET: Registered protocol family 1
[    0.192707] checking if image is initramfs... it is
[    1.787338] Freeing initrd memory: 9256k freed
[    1.790774] ps3_system_bus_match:360: dev=4.0(vuart_01), drv=4.0(ps3_av): match
[    1.948896] audit: initializing netlink socket (disabled)
[    1.948921] type=2000 audit(1256587197.948:1): initialized
[    1.976039] HugeTLB registered 16 MB page size, pre-allocated 0 pages
[    1.979480] VFS: Disk quotas dquot_6.5.1
[    1.979590] Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
[    1.979812] fuse init (API version 7.10)
[    1.980027] msgmni has been set to 440
[    1.980480] alg: No test for stdrng (krng)
[    1.980528] io scheduler noop registered
[    1.980534] io scheduler anticipatory registered
[    1.980539] io scheduler deadline registered
[    1.980718] io scheduler cfq registered (default)
[    1.981018] ps3_system_bus_match:360: dev=10.1(ioc0_01), drv=10.1(ps3fb): match
[    1.981026] ps3_system_bus_match:360: dev=10.1(ioc0_01), drv=10.1(ps3fb): match
[    2.394852] Console: switching to colour frame buffer device 140x40
[    2.406410] ps3fb ioc0_01: graphics fb0, using 9152 KiB of video memory
[    2.409041] vio_register_driver: driver hvc_console registering
[    2.409071] HVSI: registered 0 devices
[    2.410800] brd: module loaded
[    2.410898] Fixed MDIO Bus: probed
[    2.411029] input: Macintosh mouse button emulation as /devices/virtual/input/input0
[    2.411067] Uniform Multi-Platform E-IDE driver
[    2.411214] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    2.411265] ps3_system_bus_match:360: dev=1.0(sb_05), drv=1.0(ps3-ehci-driver): match
[    2.411272] ps3_system_bus_match:360: dev=1.0(sb_05), drv=1.0(ps3-ehci-driver): match
[    2.411299] dma_sb_region_create_linear:984: forcing 16M pages for linear map
[    2.411304]  -> dma_sb_region_create:652:
[    2.411430] ps3-ehci-driver sb_05: PS3 EHCI Host Controller
[    2.411595] ps3-ehci-driver sb_05: new USB bus registered, assigned bus number 1
[    2.411680] ps3-ehci-driver sb_05: irq 45, io mem 0x400000270000
[    2.420313] ps3-ehci-driver sb_05: USB 0.0 started, EHCI 1.00
[    2.420482] usb usb1: configuration #1 chosen from 1 choice
[    2.420548] hub 1-0:1.0: USB hub found
[    2.420568] hub 1-0:1.0: 2 ports detected
[    2.420812] ps3_system_bus_match:360: dev=1.0(sb_07), drv=1.0(ps3-ehci-driver): match
[    2.420819] ps3_system_bus_match:360: dev=1.0(sb_07), drv=1.0(ps3-ehci-driver): match
[    2.420843] dma_sb_region_create_linear:984: forcing 16M pages for linear map
[    2.420849]  -> dma_sb_region_create:652:
[    2.420952] ps3-ehci-driver sb_07: PS3 EHCI Host Controller
[    2.421076] ps3-ehci-driver sb_07: new USB bus registered, assigned bus number 2
[    2.421155] ps3-ehci-driver sb_07: irq 46, io mem 0x400000280000
[    2.432313] ps3-ehci-driver sb_07: USB 0.0 started, EHCI 1.00
[    2.432460] usb usb2: configuration #1 chosen from 1 choice
[    2.432537] hub 2-0:1.0: USB hub found
[    2.432553] hub 2-0:1.0: 2 ports detected
[    2.432794] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    2.432813] ps3_system_bus_match:360: dev=2.0(sb_06), drv=2.0(ps3-ohci-driver): match
[    2.432820] ps3_system_bus_match:360: dev=2.0(sb_06), drv=2.0(ps3-ohci-driver): match
[    2.432834] dma_sb_region_create_linear:984: forcing 16M pages for linear map
[    2.432839]  -> dma_sb_region_create:652:
[    2.432943] ps3-ohci-driver sb_06: PS3 OHCI Host Controller
[    2.433076] ps3-ohci-driver sb_06: new USB bus registered, assigned bus number 3
[    2.433136] ps3-ohci-driver sb_06: irq 47, io mem 0x400000290000
[    2.739974] usb usb3: configuration #1 chosen from 1 choice
[    2.740042] hub 3-0:1.0: USB hub found
[    2.740062] hub 3-0:1.0: 2 ports detected
[    2.740279] ps3_system_bus_match:360: dev=2.0(sb_08), drv=2.0(ps3-ohci-driver): match
[    2.740303] ps3_system_bus_match:360: dev=2.0(sb_08), drv=2.0(ps3-ohci-driver): match
[    2.740318] dma_sb_region_create_linear:984: forcing 16M pages for linear map
[    2.740323]  -> dma_sb_region_create:652:
[    2.740437] ps3-ohci-driver sb_08: PS3 OHCI Host Controller
[    2.740561] ps3-ohci-driver sb_08: new USB bus registered, assigned bus number 4
[    2.740632] ps3-ohci-driver sb_08: irq 48, io mem 0x4000002a0000
[    3.048009] usb usb4: configuration #1 chosen from 1 choice
[    3.048076] hub 4-0:1.0: USB hub found
[    3.048096] hub 4-0:1.0: 2 ports detected
[    3.048375] uhci_hcd: USB Universal Host Controller Interface driver
[    3.048526] usbcore: registered new interface driver libusual
[    3.060398] mice: PS/2 mouse device common for all mice
[    3.060564] platform ppc-rtc.0: rtc core: registered ppc_md as rtc0
[    3.060605] ps3_system_bus_match:360: dev=5.0(vuart_02), drv=5.0(ps3_sys_manager): match
[    3.060611] ps3_system_bus_match:360: dev=5.0(vuart_02), drv=5.0(ps3_sys_manager): match
[    3.060840] TCP cubic registered
[    3.061069] registered taskstats version 1
[    3.061127] /build/buildd/linux-ports-2.6.28/drivers/rtc/hctosys.c: unable to open rtc device (y)
[    3.160328] usb 1-2: new high speed USB device using ps3-ehci-driver and address 2
[    3.213173] Freeing unused kernel memory: 316k freed
[    3.298149] usb 1-2: configuration #1 chosen from 1 choice
[    3.298564] hub 1-2:1.0: USB hub found
[    3.298840] hub 1-2:1.0: 4 ports detected
[    3.416388] usb 2-2: new high speed USB device using ps3-ehci-driver and address 2
[    3.574501] usb 2-2: configuration #1 chosen from 1 choice
[    3.648571] usb 1-2.2: new full speed USB device using ps3-ehci-driver and address 3
[    3.741313] usb 1-2.2: configuration #1 chosen from 1 choice
[    3.741560] hub 1-2.2:1.0: USB hub found
[    3.741727] hub 1-2.2:1.0: 4 ports detected
[    3.833771] SCSI subsystem initialized
[    3.837822] ps3vram: registered block device major 254
[    3.837858] ps3_system_bus_match:360: dev=10.2(ioc0_03), drv=10.2(ps3vram): match
[    3.837869] ps3_system_bus_match:360: dev=10.2(ioc0_03), drv=10.2(ps3vram): match
[    3.852872] ps3disk_init:585: registered block device major 253
[    3.852940] ps3_system_bus_match:360: dev=6.0(sb_02), drv=6.0(ps3disk): match
[    3.857672] ps3_system_bus_match:360: dev=7.0(sb_01), drv=7.0(ps3rom): match
[    3.858027] ps3vram ioc0_03: Created ram cache: 7 entries, 256 KiB each
[    3.858082] ps3vram ioc0_03: ps3vram: Using 245 MiB of GPU memory
[    3.858353] ps3_system_bus_match:360: dev=6.0(sb_02), drv=6.0(ps3disk): match
[    3.858463]  -> dma_sb_region_create:652:
[    3.899336] ps3disk sb_02: First accessible region has index 3 start 135329976 size 20971512
[    3.900385] ps3disk sb_02: ps3da is a TOSHIBA MK8052GSX (76319 MiB total, 10239 MiB for OtherOS)
[    3.900545]  ps3da: ps3da1 ps3da2 < ps3da5 >
[    3.927068] ps3_system_bus_match:360: dev=7.0(sb_01), drv=7.0(ps3rom): match
[    3.927187]  -> dma_sb_region_create:652:
[    3.942559] scsi0 : ps3rom
[    3.949072] scsi 0:0:0:0: CD-ROM            SONY     PS-SYSTEM   302R 4112 PQ: 0 ANSI: 0
[    4.037186] usb 1-2.2.1: new low speed USB device using ps3-ehci-driver and address 4
[    4.139724] usb 1-2.2.1: configuration #1 chosen from 1 choice
[    4.220635] usb 1-2.2.2: new low speed USB device using ps3-ehci-driver and address 5
[    4.326630] usb 1-2.2.2: configuration #1 chosen from 1 choice
[    4.520598] Driver 'sr' needs updating - please use bus_type methods
[    4.525661] sr0: scsi3-mmc drive: 0x/0x cd/rw xa/form2 cdda tray
[    4.525707] Uniform CD-ROM driver Revision: 3.20
[    4.526028] sr 0:0:0:0: Attached scsi CD-ROM sr0
[    4.543364] usbcore: registered new interface driver hiddev
[    4.560340] sr 0:0:0:0: Attached scsi generic sg0 type 5
[    4.565957] input: Alps Electric M2452 as /devices/ps3_system/sb_05/usb1/1-2/1-2.2/1-2.2.1/1-2.2.1:1.0/input/input1
[    4.586506] generic-usb 0003:05AC:0201.0001: input,hidraw0: USB HID v1.00 Keyboard [Alps Electric M2452] on usb-sb_05-2.2.1/input0
[    4.590565] input: USB Mouse               as /devices/ps3_system/sb_05/usb1/1-2/1-2.2/1-2.2.2/1-2.2.2:1.0/input/input2
[    4.609552] generic-usb 0003:05E3:1205.0002: input,hidraw1: USB HID v1.10 Mouse [USB Mouse              ] on usb-sb_05-2.2.2/input0
[    4.609613] usbcore: registered new interface driver usbhid
[    4.609624] usbhid: v2.6:USB HID core driver
[    4.800778] PM: Starting manual resume from disk
[    4.885534] kjournald starting.  Commit interval 5 seconds
[    4.885585] EXT3-fs: mounted filesystem with ordered data mode.
[   10.772188] udev: starting version 141
[   11.203627] ps3_system_bus_match:360: dev=3.0(sb_04), drv=3.0(ps3_gelic_driver): match
[   11.203641] ps3_system_bus_match:360: dev=3.0(sb_04), drv=3.0(ps3_gelic_driver): match
[   11.203696] dma_sb_region_create_linear:984: forcing 16M pages for linear map
[   11.203705]  -> dma_sb_region_create:652:
[   11.203841] ps3_gelic_driver sb_04: internal vlan enabled
[   11.204646] ps3_gelic_driver sb_04: eth0: MAC addr 00:1f:a7:24:9d:bd
[   11.215123] ps3_gelic_driver sb_04: wlan0: MAC addr 00:1f:a7:24:9d:bd
[   11.303172] ps3_system_bus_match:360: dev=8.0(sb_03), drv=8.0(ps3flash): match
[   11.303186] ps3_system_bus_match:360: dev=8.0(sb_03), drv=8.0(ps3flash): match
[   11.303280]  -> dma_sb_region_create:652:
[   11.324777] ps3flash sb_03: First accessible region has index 5 start 473600 size 8192
[   11.325123] ps3flash sb_03: ps3flash_probe:388: registered misc device 60
[   11.508043] Bluetooth: Core ver 2.13
[   11.542692] NET: Registered protocol family 31
[   11.542701] Bluetooth: HCI device and connection manager initialized
[   11.542739] Bluetooth: HCI socket layer initialized
[   11.548662] Bluetooth: Generic Bluetooth USB driver ver 0.3
[   11.549238] usbcore: registered new interface driver btusb
[   12.010374] ps3_system_bus_match:360: dev=9.0(ioc0_02), drv=9.0(snd_ps3): match
[   12.010387] ps3_system_bus_match:360: dev=9.0(ioc0_02), drv=9.0(snd_ps3): match
[   12.458105] PS3 sound started. start_delay=2000ms
[   12.975250] loop: module loaded
[   13.632040] Adding 489940k swap on /dev/ps3da5.  Priority:-1 extents:1 across:489940k
[   14.029347] EXT3 FS on ps3da1, internal journal
[   15.659705] type=1505 audit(1256587211.656:2): operation="profile_load" name="/sbin/dhclient-script" name2="default" pid=1601
[   15.660041] type=1505 audit(1256587211.656:3): operation="profile_load" name="/sbin/dhclient3" name2="default" pid=1601
[   15.660188] type=1505 audit(1256587211.656:4): operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" name2="default" pid=1601
[   15.660364] type=1505 audit(1256587211.660:5): operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" name2="default" pid=1601
[   16.191959] type=1505 audit(1256587212.188:6): operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" name2="default" pid=1606
[   16.192488] type=1505 audit(1256587212.192:7): operation="profile_load" name="/usr/sbin/cupsd" name2="default" pid=1606
[   16.307261] type=1505 audit(1256587212.304:8): operation="profile_load" name="/usr/sbin/tcpdump" name2="default" pid=1610
[   19.977644] NET: Registered protocol family 15
[   20.042620] alg: No test for cipher_null (cipher_null-generic)
[   20.045751] alg: No test for digest_null (digest_null-generic)
[   20.045934] alg: No test for compress_null (compress_null-generic)
[   22.001869] Bluetooth: L2CAP ver 2.11
[   22.001877] Bluetooth: L2CAP socket layer initialized
[   22.110029] Bluetooth: SCO (Voice Link) ver 0.6
[   22.110037] Bluetooth: SCO socket layer initialized
[   22.141795] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   22.141803] Bluetooth: BNEP filters: protocol multicast
[   22.206154] Bridge firewalling registered
[   22.234723] Bluetooth: RFCOMM socket layer initialized
[   22.234764] Bluetooth: RFCOMM TTY layer initialized
[   22.234773] Bluetooth: RFCOMM ver 1.10
[   24.688610] lp: driver loaded but no devices found
[   24.731905] ppdev: user-space parallel port driver
[   25.733008] NET: Registered protocol family 10
[   25.733700] lo: Disabled Privacy Extensions
[   28.013660] gelic_wl_assoc_worker: no bss matched. association failed
[   28.067508] NET: Registered protocol family 17
[   38.288378] wlan0: no IPv6 routers present
[   38.580300] eth0: no IPv6 routers present
[  792.941241] ioctl32(xfce4-terminal:3154): Unknown cmd fd(9) cmd(0000530b){t:'S';sz:0} arg(0fd36d38) on /dev/pts/0
[  792.941263] ioctl32(xfce4-terminal:3154): Unknown cmd fd(9) cmd(0000530b){t:'S';sz:0} arg(0fd36d40) on /dev/pts/0
[  792.941284] ioctl32(xfce4-terminal:3154): Unknown cmd fd(9) cmd(0000530b){t:'S';sz:0} arg(0fd36d48) on /dev/pts/0
[ 1139.333799] ioctl32(synaptic:3284): Unknown cmd fd(34) cmd(0000530b){t:'S';sz:0} arg(0f234d38) on /dev/pts/0
[ 1139.333823] ioctl32(synaptic:3284): Unknown cmd fd(34) cmd(0000530b){t:'S';sz:0} arg(0f234d40) on /dev/pts/0
[ 1139.333845] ioctl32(synaptic:3284): Unknown cmd fd(34) cmd(0000530b){t:'S';sz:0} arg(0f234d48) on /dev/pts/0
[ 1208.703865] Bluetooth: HIDP (Human Interface Emulation) ver 1.2
[ 1256.132153] ioctl32(sixad-uinput-si:3913): Unknown cmd fd(5) cmd(80045564){t:'U';sz:4} arg(00000000) on /dev/input/uinput
[ 1256.132179] ioctl32(sixad-uinput-si:3913): Unknown cmd fd(5) cmd(80045564){t:'U';sz:4} arg(00000003) on /dev/input/uinput
[ 1256.132201] ioctl32(sixad-uinput-si:3913): Unknown cmd fd(5) cmd(80045564){t:'U';sz:4} arg(00000001) on /dev/input/uinput
[ 1256.132223] ioctl32(sixad-uinput-si:3913): Unknown cmd fd(5) cmd(80045567){t:'U';sz:4} arg(00000000) on /dev/input/uinput
[ 1459.513440] ioctl32(sixad-uinput-si:5447): Unknown cmd fd(5) cmd(80045564){t:'U';sz:4} arg(00000000) on /dev/input/uinput
[ 1459.513456] ioctl32(sixad-uinput-si:5447): Unknown cmd fd(5) cmd(80045564){t:'U';sz:4} arg(00000003) on /dev/input/uinput
[ 1459.513468] ioctl32(sixad-uinput-si:5447): Unknown cmd fd(5) cmd(80045564){t:'U';sz:4} arg(00000001) on /dev/input/uinput
[ 1459.513482] ioctl32(sixad-uinput-si:5447): Unknown cmd fd(5) cmd(80045567){t:'U';sz:4} arg(00000000) on /dev/input/uinput
[ 1492.254420] ioctl32(xfce4-terminal:5759): Unknown cmd fd(9) cmd(0000530b){t:'S';sz:0} arg(0fd36d38) on /dev/pts/0
[ 1492.254444] ioctl32(xfce4-terminal:5759): Unknown cmd fd(9) cmd(0000530b){t:'S';sz:0} arg(0fd36d40) on /dev/pts/0
[ 1492.254465] ioctl32(xfce4-terminal:5759): Unknown cmd fd(9) cmd(0000530b){t:'S';sz:0} arg(0fd36d48) on /dev/pts/0

```

---

### Post by elfraser on 2009-10-26
> **falkTX said:**
> **Update:** *(1.0-falktx4)*

I really want to make this work stable, so please test out this:
run in a terminal:
```
sixad --stop
sixad
```and press the PS button on the Sixaxis.


```
~$ sixad
WARNING: All config files need .conf: /etc/modprobe.d/oss-compat, it will be ignored in a future release.
sixad settings:
Enable LEDs:    1
js# as LED #:    1
Start LED #:    1
LED # increase:    1
LED animation:    1
Buttons:    1
Sens. buttons:    1
Axis:        1
Accelerometers:    1
Acceleration:    0
Speed:        0
Position:    0
Rumble:        0
Debug:        1
sixad[14197]: sixad started, press the PS button now
sixad[14224]: Connected PLAYSTATION(R)3 Controller (00:23:06:11:73:F1)
sixad-debug[14224]: debug mode started
error on uinput ioctl (UI_SET_ABSBIT)

```

---

### Post by Okiura on 2009-10-26
Your having the same issue as Slumz187 i'm having a look at his issue to see if i can see the problem but i think it may be kernel related, what kernel are you using?

```
 uname -r 
```


Edit >>> never mind i seen it in your dmesg and it's the same version.

Okiura,

---

### Post by falkTX on 2009-10-27
These bugs happen because UInput doesn't compile correctly on PowerPC[32].
Please go to "Configure Sixaxis"->"Advanced" and check the option the use the legacy driver.

I'll put a warning about that soon.

---

### Post by falkTX on 2009-10-27
**Update:** *1.0.0-falktx5*

Changelog:
>   * QtSixA:
    - Fixed sixa-notify file appearing on home folder
    - Fixed notifications not auto-started on Gnome sessions
    - Notifications can now be started anytime by running "sixa-notify"
    - Disabled Rumble feature (for v1.0 stability, can be enabled manually)
    - Display warning when "Legacy Driver" is not enabled on PowerPC

If you're not running PS3 and still have problems connecting -tell me.
Are you using a PS3, elfraser?

PS3 users **must** enable the legacy driver option.
I'll look for a solution now.

---

### Post by elfraser on 2009-10-27
> **falkTX said:**
> **Update:** *1.0.0-falktx5*

Changelog:


If you're not running PS3 and still have problems connecting -tell me.
Are you using a PS3, elfraser?

PS3 users **must** enable the legacy driver option.
I'll look for a solution now.

I am on a PS3.  I thought I had the legacy driver enabled but I must have forgot to enable it after I removed the package and reinstalled it.

I'll try it out and let you know what happens!

UPDATE: With legacy, I get the following: 
```
 ~$ sixad
WARNING: All config files need .conf: /etc/modprobe.d/oss-compat, it will be ignored in a future release.
Legacy driver workaround enabled (no neat stuff...)
sixad[6856]: sixad started, press the PS button now
sixad[6856]: Connected Sony Computer Entertainment Wireless Controller (00:23:06:11:73:F1)

```

And it will recognize multiple controllers (and count LEDs) using the GUI.  Only problem now is that it doesn't work.  I booted up my emulator to try it out and ... no dice.

When I run jstest, no response from either controller.   Jstest says it's talking to a Sony controller but nothing.
```
~$ jstest /dev/input/js1
Driver version is 2.1.0.
Joystick (Sony Computer Entertainment Wireless Controller) has 28 axes and 19 buttons.
Testing ... (interrupt to exit)
Axes:  0:     0  1:     0  2:     0  3:     0  4:     0  5:     0  6:     0  7:     0  8:     0  9:     0 10:     0 11:     0 12:     0 13:     0 14:     0 15:     0 16:     0 17:     0 18:     0 19:     0 20:     0 21:     0 22:     0 23:     0 24:     0 25:     0 26:     0 27:     0 Buttons:  0:off  1:off  2:off
... a bunch of repeats ...
Axes:  0:-32767  1:-32767  2:-32767  3:-32767  4:-32767  5:-32767  6:-32767  7:-32767  8:-32767  9:-32767 10:-32767 11:-32767 12:-32767 13:-32767 14:-32767 15:-32767 16:-32767 17:-32767 18:-32767 19:-32767 20:-32767 21:-32767 22:-32767 23:-32767 24:-32767 25:-32767 26:-32767 27:-32767 Buttons:  0:off  1:off  2:off  3:off  4:off  5:off  6:off  7:off  8:off  9:off 10:off 11:off 12:off 13:off 14:off 15:off 16:off 17:off 18:off

 
```

---

### Post by Slumz187 on 2009-10-27
elfraser, i get the same errors, the same connections, and everything..we both must be running ubuntu 9.04 on the ps3, from what I understand now is that its a issue with our kernel and uinput...the uinput is created but is not communicating with the qtsixa program... my device is actually recognized as a touchpad...test it out for me after connecting with the legacy driver..just click on something with your mouse and press the ps button a couple of times and see if selects or highlights any text!

there is no solution yet man unfortunately!

---

### Post by elfraser on 2009-10-27
> **Slumz187 said:**
> elfraser, i get the same errors, the same connections, and everything..we both must be running ubuntu 9.04 on the ps3, from what I understand now is that its a issue with our kernel and uinput...the uinput is created but is not communicating with the qtsixa program... my device is actually recognized as a touchpad...test it out for me after connecting with the legacy driver..just click on something with your mouse and press the ps button a couple of times and see if selects or highlights any text!

there is no solution yet man unfortunately!

Yup, I just discovered that too (about the PS button acting as a mouse click).
Sorry for over-sharing, I just figured I would provide as much info as possible.

---

### Post by falkTX on 2009-10-28
I need to ask you, PS3 guys, to update to Karmic as soon as it is released.
I've tested my program mainly on Karmic, and from my conversations with Okiura, karmic will work even without the legacy driver.

Just be sure to install using the correct ISO. Once karmic is released it will be here:
[http://cdimage.ubuntu.com/ports/releases/karmic/](http://cdimage.ubuntu.com/ports/releases/karmic/)
*(be sure to select the PS3 Alternate CD)*

---

### Post by falkTX on 2009-10-28
**Update:**
I noticed the notifications were not starting... fixed now (update, disable and enable notifications again to apply it).

I also made a presentation video for QtSixA:
[http://www.youtube.com/watch?v=KLhvQ3PtV2Q](http://www.youtube.com/watch?v=KLhvQ3PtV2Q)

My plans now are:
1 - search for possible bugs in QtSixA/sixad and fix them
2 - Release 1.0 (upload for KDE-Apps and sourceforge too)
3 - Finish QtSixA webpage (qtsixa.sourceforge.net)
4 - Make QtSixA package go to Lucid (Ubuntu 10.04)
x - Maybe a PPA repo?

v1.0 should be finished next week

---

### Post by digge on 2009-10-28
For thoose that use the legacy on PS3 and it still doesnt work i might have a workaround. Previously i ran into a similar issue with my keyboard/trackball combo, trackball was detected as synaptic touchpad. Turns out there is a bug with hal/ppc that makes synaptic detect on all sorts of devices. The bug is here.

[https://bugs.launchpad.net/ubuntu/+source/hal/+bug/351059](https://bugs.launchpad.net/ubuntu/+source/hal/+bug/351059)

So one workaround is simply to remove the package [COLOR="Red"]xserver-xorg-input-synaptics[/COLOR]

Or do as sugested in the comments and quote away a line in the fdi for synaptic so it doesnt gets used. [https://bugs.launchpad.net/ubuntu/+source/hal/+bug/351059/comments/11](https://bugs.launchpad.net/ubuntu/+source/hal/+bug/351059/comments/11)

Im currently on karmic on my ps3 and after doing the second woraround to get my mouse working and then enabling legacy, reboot and then conected via bluetooth and jstest spits out numbers at me. But i recall having the same issue before on jaunty as well so worth a try for thoose that have problems.

---

### Post by falkTX on 2009-10-28
thanks digge.
Maybe I should make sixad conflict with the synaptics package on PowerPC?
Does removing that package hurts anything on the PS3?

---

### Post by digge on 2009-10-28
The problem with removing the package is that its a dependency of other meta packages, like for instance if you want to install lxde desktop, lubuntu-desktop the synaptics package is a dependency and you would probably get into a bad spiral there where you cant have both. Have no idea why they made it requirement btw, should rather be a recommended download. 

Thats why i opted for the second approach cause then i can have the dependency installed and dont get issues with dependencies all over the place.

EDIT: Not sure how viable this solution would be but maybe you could do the editing of the fdi file from your installer if PS3 is detected?

EDIT2: The problem will probably be fixed sometime, and there might even be someone with a touchpad attached through usb or something who knows that its not so good to disable synaptic for.

---

### Post by falkTX on 2009-10-28
> **digge said:**
> The problem with removing the package is that its a dependency of other meta packages, like for instance if you want to install lxde desktop, lubuntu-desktop the synaptics package is a dependency and you would probably get into a bad spiral there where you cant have both. Have no idea why they made it requirement btw, should rather be a recommended download. 

Thats why i opted for the second approach cause then i can have the dependency installed and dont get issues with dependencies all over the place.

Ok, thanks for letting me know.
What do you think about a post-installation script that check for those lines and delete them automatically?

---

### Post by digge on 2009-10-28
> **falkTX said:**
> Ok, thanks for letting me know.
What do you think about a post-installation script that check for those lines and delete them automatically?

Well, i dont know if this is only ubuntu that have these problems, or if any ppc linux have it. Maybe you could make the program detect if its detected as synaptic and if it is comment out that line in that file and suggest a reboot? Hopefully you could remove that code after a while once the bug gets fixed. 

Tell me if you need a sample output from dmesg or syslog or something when it gets detected wrong. Dont remember what log i found it in, maybe it was the xorg log file.

EDIT: problem being it gets a bit hard to navigate without the mouse ;)

---

### Post by digge on 2009-10-28
Here are the interesting lines from Xorg.0.log
```
(II) config/hal: Adding input device Sony Computer Entertainment Wireless Controller
(II) Synaptics touchpad driver version 1.1.2
(**) Option "Device" "/dev/input/event3"
(--) Sony Computer Entertainment Wireless Controller: no supported touchpad found
(EE) Sony Computer Entertainment Wireless Controller Unable to query/initialize Synaptics hardware.
(EE) PreInit failed for input device "Sony Computer Entertainment Wireless Controller"
(II) UnloadModule: "synaptics"
(EE) config/hal: NewInputDeviceRequest failed (8)
```

And here is how it looks after commenting that line.
```
(II) config/hal: Adding input device Sony Computer Entertainment Wireless Controller
(**) Sony Computer Entertainment Wireless Controller: always reports core events
(**) Sony Computer Entertainment Wireless Controller: Device: "/dev/input/event3"
(II) Sony Computer Entertainment Wireless Controller: Found x and y absolute axes
(WW) Sony Computer Entertainment Wireless Controller: Don't know how to use device
(II) UnloadModule: "evdev"
(EE) PreInit returned NULL for "Sony Computer Entertainment Wireless Controller"
(EE) config/hal: NewInputDeviceRequest failed (8)
```

Odd thing is that joystick worked for me on both occasions i think, so maybe its not related, but sounds related since some here claim it registers mouseclicks.

---

### Post by elfraser on 2009-10-28
> **digge said:**
> For thoose that use the legacy on PS3 and it still doesnt work i might have a workaround. Previously i ran into a similar issue with my keyboard/trackball combo, trackball was detected as synaptic touchpad. Turns out there is a bug with hal/ppc that makes synaptic detect on all sorts of devices. The bug is here.


Or do as sugested in the comments and quote away a line in the fdi for synaptic so it doesnt gets used. [https://bugs.launchpad.net/ubuntu/+source/hal/+bug/351059/comments/11](https://bugs.launchpad.net/ubuntu/+source/hal/+bug/351059/comments/11)


I did this (second) work around, commenting out part of the fdi.
It did the trick . . . sort of.  THANKS! 

I can now use both controllers.  However, both are mapping to the same output.  Not sure if this is a SixA problem or the conflict with the PPC.   

I had unchecked the box for "Use Sixaxis as a mouse" but instead had assigned each controller it's own profile (Fake JS 1 and Fake JS 2).

I will play around with some other configurations to see if I can get them to map to different things.

UPDATE:  Both controllers work great, each with it's own independent location.  The problem I was experiencing was due to the inputs I'd assigned in the program I was using.  Thanks, for all your help, everyone!   :D

---

### Post by Okiura on 2009-10-29
I been looking around for a better solution to the profile issue on PS3, I know what needs to be done but I can't find the option to do it, and this appearers to be a limitation of the xserver-input-joystick driver.
This does present a bit of a issue... At the moment this issue is only seen on Karmic which uses a newer version of Xorg than any other Ubuntu Distro, it seems that they have decided to disable key and mouse inputs by default and they need to be manually enabled by mapping a button to "disable-keys" and "disable-mouse" (as far as I can see form alot of Googling this is due to a issue with joystick's messing with the mouse). As the source for Xorg is the same for all Arch's I have a feeling this my become a issue on all Arch's as they upgrade to this new version (I may be wrong). I have had a look at the source for the joystick driver and I can see no way of passing any enable mouse/kbd options without changing it in the source...

Suggestions anyone? :)

Also for the issue with the uinput module, as FalkTX said you should upgrade to Karmic asap, :) I'm also going get the source for the problematic kernel and apply a patch then recompile the module, I'll try and do that this week and post it up.

Okiura,

---

### Post by falkTX on 2009-10-29
> **digge said:**
> Well, i dont know if this is only ubuntu that have these problems, or if any ppc linux have it. Maybe you could make the program detect if its detected as synaptic and if it is comment out that line in that file and suggest a reboot? Hopefully you could remove that code after a while once the bug gets fixed.

Quoting a specific part is not that easy. All I can now do is to remove lines. (Unless someone writes a very good script).
I also have no idea if any other distros have the same issue or not.

But I guess the most important thing here is:
- Does removing/comment that line hurts anything on the PS3?
- I suspect that the mouse stops working, is that true?
- Do the Sixaxis profiles work "out-of-the-box" once we do this (on the PS3)?

Sorry to keep you asking stuff, but I don't have a PS3, so wherever QtSixA works or not in the PS3 - it's up to you guys.
Of course, I'm here to help too

---

### Post by falkTX on 2009-10-29
> **Okiura said:**
> I been looking around for a better solution to the profile issue on PS3, I know what needs to be done but I can't find the option to do it, and this appearers to be a limitation of the xserver-input-joystick driver.
This does present a bit of a issue... At the moment this issue is only seen on Karmic which uses a newer version of Xorg than any other Ubuntu Distro, it seems that they have decided to disable key and mouse inputs by default and they need to be manually enabled by mapping a button to "disable-keys" and "disable-mouse" (as far as I can see form alot of Googling this is due to a issue with joystick's messing with the mouse). As the source for Xorg is the same for all Arch's I have a feeling this my become a issue on all Arch's as they upgrade to this new version (I may be wrong). I have had a look at the source for the joystick driver and I can see no way of passing any enable mouse/kbd options without changing it in the source... This is not correct. I'm using Karmic (with no Xorg PPAs, just the official drivers), and the Sixaxis profiles work just fine. It's only a PowerPC issue (or maybe only PS3)

> **Okiura said:**
> Suggestions anyone? :)
I may have a solution - send a hal command that will activate mouse for a specific device. Something like: "hald --set-property --device=/blah/blah --enable-mouse". I'll look for this.

> **Okiura said:**
> Also for the issue with the uinput module, as FalkTX said you should upgrade to Karmic asap, :) I'm also going get the source for the problematic kernel and apply a patch then recompile the module, I'll try and do that this week and post it up.Only powerpc (32bit) needs the uinput re-compilation. PowerPC64 doesn't have this issue.
I'm not sure, but I think Karmic now comes with PowerPC64 kernel in the PS3 iso. If this is the case, no recompilation is needed.
You can get your kernel architecture by running:
```
uname -m
```
If it prints "ppc64" or "powerpc64" - everything will work (axis, accelerometers, etc)
It it prints "ppc" or "powerpc" - you'll need to enable the legacy driver

Karmic is just a few hours away...
Please wait for the final announcement...

---

### Post by Okiura on 2009-10-29
> **falkTX said:**
> This is not correct. I'm using Karmic (with no Xorg PPAs, just the official drivers), and the Sixaxis profiles work just fine. It's only a PowerPC issue (or maybe only PS3)


the code I was looking at was for the ppc version of Xorg (well the version from the ppc repo anyway) so it could be case that it will only affect ppc platforms. I don't know for sure as source files should be the same across all arch's.

> **falkTX said:**
> Only powerpc (32bit) needs the uinput re-compilation. PowerPC64 doesn't have this issue.
I'm not sure, but I think Karmic now comes with PowerPC64 kernel in the PS3 iso. If this is the case, no recompilation is needed.
You can get your kernel architecture by running:
```
uname -m
```
If it prints "ppc64" or "powerpc64" - everything will work (axis, accelerometers, etc)
It it prints "ppc" or "powerpc" - you'll need to enable the legacy driver

Karmic is just a few hours away...
Please wait for the final announcement...

The kernel I have on Kermic is ppc64 and it works fine. both elfraser and slumz187 are running "2.6.28-6-powerpc64-smp" (ppc64?) and they seem to be having this issue maybe its a bug in the 2.6.28 tree?

---

### Post by falkTX on 2009-10-29
> **Okiura said:**
> The kernel I have on Kermic is ppc64 and it works fine. both elfraser and slumz187 are running "2.6.28-6-powerpc64-smp" (ppc64?) and they seem to be having this issue maybe its a bug in the 2.6.28 tree?

Probably. I'll guess we'll know tomorrow for sure (giving the time for the final release, download and install)

---

### Post by digge on 2009-10-29
> **falkTX said:**
> Quoting a specific part is not that easy. All I can now do is to remove lines. (Unless someone writes a very good script).
I also have no idea if any other distros have the same issue or not.

But I guess the most important thing here is:
- Does removing/comment that line hurts anything on the PS3?
- I suspect that the mouse stops working, is that true?
- Do the Sixaxis profiles work "out-of-the-box" once we do this (on the PS3)?

Sorry to keep you asking stuff, but I don't have a PS3, so wherever QtSixA works or not in the PS3 - it's up to you guys.
Of course, I'm here to help too

It wont hurt anything other then that no synaptic touchpads will work on PS3. Not sure how often if ever its used on a PS3 though. There are some media keyboards with a touchpad on them, not sure if they use the synaptic driver or what they use. For instance some ppl use the dinovo mini keyboard, anyone know what driver it use for its touchpad?

Im by no means a programmer in the languages you use but cant you do a replace line just as easy as delete line? I have mostly used scripting languages and most of them have some kind of replace function. Either way if you choose to go with the delete line option could you inject the line back when you uninstall qtsixa as well, just to make sure it doesnt create problems for ppl less tech savvy down the line.

Or maybe better yet, just save a backup copy of the file someplace and copy it back on uninstall, much simpler solution ;)

---

### Post by falkTX on 2009-10-29
> **digge said:**
> Or maybe better yet, just save a backup copy of the file someplace and copy it back on uninstall, much simpler solution ;)

That's the solution!
I'll update soon.

---

### Post by falkTX on 2009-10-29
**Update:** This is pre-final - report any bugs found

Changelog:
>   * Pre-Final release (just for users to test)
  * QtSixA:
    - Do not apply a game profile if the it's configuration file doesn't exist
  * sixad:
    - Disable debug by default
    - Workaround for a PowerPC synaptics bug (#351059)

---

### Post by falkTX on 2009-10-29
And karmic is here!

Download link for PS3 ISO:
[http://cdimage.ubuntu.com/ports/releases/9.10/release/ubuntu-9.10-alternate-powerpc+ps3.iso](http://cdimage.ubuntu.com/ports/releases/9.10/release/ubuntu-9.10-alternate-powerpc+ps3.iso)


Enjoy!

---

### Post by Slumz187 on 2009-10-29
damn if i could jut get into the server and download..lol..

---

### Post by falkTX on 2009-10-29
> **Slumz187 said:**
> damn if i could jut get into the server and download..lol..

I'll see if I can get the torrent to upload here


Edit: the ISO is not available yet...

---

### Post by Slumz187 on 2009-10-29
alright torrent would be perfect anyway because i could never get the downloads from there to work anyway..

---

### Post by falkTX on 2009-10-29
Alright, Karmic PS3 ISOs are here!!


Alternate ISO
[http://torrent.ubuntu.com/ports/releases/karmic/release/alternate/ubuntu-9.10-alternate-powerpc+ps3.iso.torrent](http://torrent.ubuntu.com/ports/releases/karmic/release/alternate/ubuntu-9.10-alternate-powerpc+ps3.iso.torrent)



Desktop ISO
[http://torrent.ubuntu.com/ports/releases/karmic/release/desktop/ubuntu-9.10-desktop-powerpc+ps3.iso.torrent](http://torrent.ubuntu.com/ports/releases/karmic/release/desktop/ubuntu-9.10-desktop-powerpc+ps3.iso.torrent)


Enjoy!

---

### Post by Slumz187 on 2009-10-29
Im going to wait until alot more people download or seed because my torrent's not even moving..lol

i dont even have 1%

---

### Post by ps3mhome on 2009-10-29
> **Slumz187 said:**
> Im going to wait until alot more people download or seed because my torrent's not even moving..lol

i dont even have 1%
Should be quicker:
[http://www.mininova.org/tor/3098476](http://www.mininova.org/tor/3098476)
karmic-desktop-powerpc+ps3.iso

---

### Post by falkTX on 2009-10-30
> **ps3mhome said:**
> Should be quicker:
[http://www.mininova.org/tor/3098476](http://www.mininova.org/tor/3098476)
karmic-desktop-powerpc+ps3.iso

That might not be the final stable version...
I belive that is "Current" download of some days ago...


for even faster - direct download:
Desktop - [http://cdimage.ubuntu.com/ports/releases/karmic/release/ubuntu-9.10-desktop-powerpc+ps3.iso](http://cdimage.ubuntu.com/ports/releases/karmic/release/ubuntu-9.10-desktop-powerpc+ps3.iso)

Alternate - [http://cdimage.ubuntu.com/ports/releases/karmic/release/ubuntu-9.10-alternate-powerpc+ps3.iso](http://cdimage.ubuntu.com/ports/releases/karmic/release/ubuntu-9.10-alternate-powerpc+ps3.iso)


These links might take some time to load, but once the file is found and the download is started, expect to get in 20mins (with a good internet connection)

---

### Post by ps3mhome on 2009-10-30
Sorry and thanks FalkTX for pointing that out. 

Btw, just finished Upgrade through Update Manager. Worked very smooth. Now 9.10 is running on my PS3.

---

### Post by falkTX on 2009-10-30
> **ps3mhome said:**
> Sorry and thanks FalkTX for pointing that out. 

Btw, just finished Upgrade through Update Manager. Worked very smooth. Now 9.10 is running on my PS3.

Glad to know that.

Are you available to do some tests?

---

### Post by ps3mhome on 2009-10-30
Yes, glad to help, but it may take some time for me to complete any tests, as I'm working. 

What would you like me to do?

---

### Post by falkTX on 2009-10-30
> **ps3mhome said:**
> Yes, glad to help, but it may take some time for me to complete any tests, as I'm working. 

What would you like me to do?

I'll just release the final version soon.

I need the following tests to be done - PS3 only:
1 - Running "sixad" in terminal
2 - Connects 2 or more Sixaxis
3 - Apply a Sixaxis profile - does it work?
4 - Do the Sixaxis work without the legacy driver option enabled?

---

### Post by falkTX on 2009-10-30
**Update:** Final Version is here!

Changelog:
>   * Final release! (v1.0.1 for happy update)
  * QtSixA:
    - Final fix for the notifications
    - Fixed sixad-raw PATH (needed for RPM Linuxes)
    - Write to sixad config file as root (needed for RPM Linuxes)
    - Other very small fixes where needed
  * sixad:
    - hidraw-dump and sixad-raw do now read file instead of stdin
    [No more 'sudo su root -c "hid...', just 'hidraw-dump /dev/hidrawX']


Enjoy!

---

### Post by Slumz187 on 2009-10-30
alright..it finally works for me.. woo hooo

and im updated to karmic, which has a bug in its kboot or something because it trys to install on ext4 which isnt supported by kboot so when you install you either manually partition the drive to ext3 or use kboot from older ubuntu..if any one else is experiencing this issue..it worked for me!

but thank you very much falk and also thx to okiura for even helping me....

---

### Post by falkTX on 2009-10-30
> **Slumz187 said:**
> alright..it finally works for me.. woo hooo

and im updated to karmic, which has a bug in its kboot or something because it trys to install on ext4 which isnt supported by kboot so when you install you either manually partition the drive to ext3 or use kboot from older ubuntu..if any one else is experiencing this issue..it worked for me!

but thank you very much falk and also thx to okiura for even helping me....
Cool! I was not totally sure if it would work on the PS3.


But, as I said:
[QUOTE=falkTX]I need the following tests to be done - PS3 only:
1 - Running "sixad" in terminal
2 - Connects 2 or more Sixaxis
3 - Apply a Sixaxis profile - does it work?
4 - Do the Sixaxis work without the legacy driver option enabled? [/QUOTE]

---

### Post by ps3mhome on 2009-10-30
> **falkTX said:**
> I'll just release the final version soon.

I need the following tests to be done - PS3 only:
1 - Running "sixad" in terminal
2 - Connects 2 or more Sixaxis
3 - Apply a Sixaxis profile - does it work?
4 - Do the Sixaxis work without the legacy driver option enabled?

I need the following tests to be done - PS3 only:
1 - Running "sixad" in terminal
2 - Connects 2 or more Sixaxis
3 - Apply a Sixaxis profile - does it work?
4 - Do the Sixaxis work without the legacy driver option enabled?[/QUOTE]

Tests (sorry I'm noob, not sure exactly what to do, need more instructions):
1. sixad
$ sixad
sixad settings:
Enable LEDs:	1
js# as LED #:	0
Start LED #:	1
LED # increase:	1
LED animation:	1
Buttons:	1
Sens. buttons:	1
Axis:		1
Accelerometers:	1
Acceleration:	0
Speed:		0
Position:	0
Rumble:		0
Debug:		0
sixad[2532]: sixad started, press the PS button now
sixad[2555]: Connected PLAYSTATION(R)3 Controller (00:21:4F:E4:XX:XX)

3. Run QtSixA (not legacy driver), first w Fake_Joystick profile. jstest /dev/input/js0 reacts. Switched Profile to gnome. jstest reacts. disconnect. psbutton. grant access=yes. jstest /dev/input/js0 no reaction, 4 red dots blink in sync.

Disconnect. Blinking dots go out. Ticked Legacy driver. PS button. Grant access. Dot 2 light up. jstest reacts. Disconnect. PS button. Dot 3 light up. jstest reacts. Seems to disconnet after inactivity.

2. Only have 1 DS3, and Sony keypad which works with and without QtSixA running.

Comment: Expect and would like DS3 to work as mouse, but nothing happens.

---

### Post by Slumz187 on 2009-10-30
lol unfortunately ps3mhome..i had mines running as a mouse in karmic earlier, the analog sticks were moving the arrow but there was no input and also the mouse that i have connected was disabled..it was weird to me but i cant figure out how it happened!

---

### Post by falkTX on 2009-10-30
So everything now works in the PS3 except for the profiles...
Once you apply a profile then re-connect, there's no mouse/keyboard events wherever legacy option is on or off - is this correct?

If yes, all we need is a shell command to activate mouse/keyboard feature of a specific device. I'm looking for it now

---

### Post by falkTX on 2009-10-30
> **Slumz187 said:**
> lol unfortunately ps3mhome..i had mines running as a mouse in karmic earlier, the analog sticks were moving the arrow but there was no input and also the mouse that i have connected was disabled..it was weird to me but i cant figure out how it happened!

that's because Sixaxis was being detected as a synaptic device - which is wrong.
That has been fixed already, but the profiles problem is still there

---

### Post by falkTX on 2009-10-30
Some progress: *(Replace "XX:XX:XX:XX:XX:XX" with the Sixaxis ID)*
```
sudo hal-set-property --udi `hal-find-by-property --key "info.product" --string "PLAYSTATION(R)3 Controller (XX:XX:XX:XX:XX:XX)"` --key input.x11_options.MapButton1 --string "A"
```

Just an example... now I need to find the right option... :-k

---

### Post by falkTX on 2009-10-30
I think I found a solution!
Please test!!

Steps:
1 - Apply any profile of your choice.
2 - Run:
```
sudo gedit /etc/hal/fdi/policy/sixa*fdi
```
3 - Replace the line:
>         <merge key="input.x11_driver" type="string">joystick</merge>
with this:
>         <merge key="input.x11_driver" type="string">joystick</merge>
	<merge key="input.x11_options.StartKeysEnabled" type="bool">true</merge>
	<merge key="input.x11_options.StartMouseEnabled" type="bool">true</merge>
4 - disconnect the Sixaxis and connect again

Does it work??

---

### Post by Slumz187 on 2009-10-30
Let me test this for you falk ! give me a min



im not getting any reaction from the controller!

---

### Post by falkTX on 2009-10-30
> **Slumz187 said:**
> Let me test this for you falk ! give me a min



im not getting any reaction from the controller!

damn...

I don't know what else to do, sorry

---

### Post by ps3mhome on 2009-10-31
Thanks, but it doesn't seem to work, the mouse thing.

---

### Post by falkTX on 2009-11-02
**Update:** 1.0.2

Changelog:
>   * On the Sixaxis profiles, use "none" for no key instead of "key=NoSymbol"
  * Renamed *.bak files to *.bu (debian complains)
  * New Option - "Toggle profiles on/off" (useful for PS3 guys!)
  * First PPA release!


This means great news!
The profiles not working on the PS3 do now have a workaround:
1 - Update to the new 1.0.2
2 - Go to "Configure Sixaxis" -> "Advanced" -> and check "Use L3/R3 to enable/disable mouse and keyboard"
3 - Click apply
4 - Apply a new profile and re-connect the Sixaxis.
5 - Now you can press L3 to enable/disable mouse and R3 for keyboard
Isn't that great?


and I was able to create a full debian source package for QtSixA, meaning it will be on my PPA soon...

---

### Post by falkTX on 2009-11-02
**Update:**

QtSixA does now have a launchpad PPA!

If you're using Karmic (and not running from a PS3), add the repo by running this command:
```
sudo add-apt-repository ppa:falk-t-j/qtsixa
```

---

### Post by falkTX on 2009-11-02
More good news!

I've submitted QtSixA to the official Ubuntu repos for reviewing...
I'll do my best to make it to Lucid (and maybe Karmic too)

Follow the reviewing updates here:
[http://revu.ubuntuwire.com/p/qtsixa](http://revu.ubuntuwire.com/p/qtsixa)

---

### Post by nxmehta on 2009-11-02
> **falkTX said:**
> **Update:**

QtSixA does now have a launchpad PPA!

If you're using Karmic (and not running from a PS3), add the repo by running this command:
```
sudo add-apt-repository ppa:falk-t-j/qtsixa
```

Cool news.  Can you also add builds for jaunty?  All you have to do is change the debian/changelog file with something like sed and rerun debuild :)

---

### Post by falkTX on 2009-11-02
> **nxmehta said:**
> Cool news.  Can you also add builds for jaunty?  All you have to do is change the debian/changelog file with something like sed and rerun debuild :)

Done, but the build will only start in 10 hours.

You might want to wait for tomorrow.
I'll also get my first MOTU review tonight. If all goes well, QtSixA will be available for Lucid & Karmic soon

---

### Post by jrumpsa on 2009-11-02
Whenever I try to install the qtsixa package from synaptic, I get the following error

E: qtsixa: subprocess installed post-installation script returned error exit status 1

any ideas?

---

### Post by falkTX on 2009-11-02
> **jrumpsa said:**
> Whenever I try to install the qtsixa package from synaptic, I get the following error

E: qtsixa: subprocess installed post-installation script returned error exit status 1

any ideas?

Ubuntu version?
32-64 bit or PS3?

Are you using old Repo or the new PPA?



[I]Why don't people say that in the first place... 
I'm not a wizard to guess things...[/I]

---

### Post by jrumpsa on 2009-11-02
lol, So sorry, Ubuntu 9.10 x86.
I couldn't use the new ppa, it said the keyserver was taking too long to respond, I'll try it again.
version 1.0.2-ubuntu~ppa5

---

### Post by falkTX on 2009-11-02
Thanks for pointint that out.

I just forgot to rename *.bak -> *.bu in the postinst.
This is fixed now, although it may take some time for the update to appear on the PPA.


And the keyserver thing it's an error in Ubuntu (happens all the time for recent PPAs)

---

### Post by jrumpsa on 2009-11-02
Awesome, Thank you so much for taking the time to build a simpler 6A/ds3 software package!:p Is this going to be made available to non debian distros?

---

### Post by falkTX on 2009-11-02
> **jrumpsa said:**
> Awesome, Thank you so much for taking the time to build a simpler 6A/ds3 software package!:p Is this going to be made available to non debian distros?

I've made available 1.0.1 RPMs, check the sourceforge page for that.
If you're experienced on making RPMs, I really need some help on that

The source is also available there, feel free to do whatever you want with it

---

### Post by falkTX on 2009-11-03
**Update:**
After some troubles building Jaunty PPA packages, I decided NOT to use the PPA for Jaunty.
The normal, but untrusted, repository will still be available.

---

### Post by Chonnawonga on 2009-11-03
Hi, I'm running Karmic and trying to install. Adding the PPA and updating was fine, but on trying to install, I get "E: Couldn't find package qtsixa".

Hrmm.

---

### Post by Slumz187 on 2009-11-03
did you try updating and installing at the same time? 

or u might want to try
 
sudo apt-get dist-upgrade

---

### Post by Chonnawonga on 2009-11-03
Tried updating and installing together first, but got the "Couldn't find package" error. Dist-upgrade tells me there's nothing to upgrade or install.

---

### Post by futuresnake on 2009-11-03
im on a ps3 running 9.10 and the program picks up the controller but i cant move the mouse or anything....

---

### Post by falkTX on 2009-11-04
> **futuresnake said:**
> im on a ps3 running 9.10 and the program picks up the controller but i cant move the mouse or anything....

Go to "Configure Sixaxis" -> "Advanced" and check the Toggle L3/R3 thing.
Then, the next time you apply apply a profile, L3 will enable/disable mouse and R3 will go for keyboard

---

### Post by falkTX on 2009-11-04
> **Chonnawonga said:**
> Tried updating and installing together first, but got the "Couldn't find package" error. Dist-upgrade tells me there's nothing to upgrade or install.

Try go to "Software Sources" and remove the repo (should have "falk-t-j" or "qtsixa"). Then add this new one:
```
deb http://ppa.launchpad.net/falk-t-j/qtsixa/ubuntu karmic main
```

Maybe you're using my other, personal PPA repo; I don't have qtsixa packages there

---

### Post by futuresnake on 2009-11-04
okay i probably did somthing wrong before hand but i enabled L3/R3 thing but still not working i have it under gnome profile but i feel lost i guess

---

### Post by falkTX on 2009-11-04
> **futuresnake said:**
> okay i probably did somthing wrong before hand but i enabled L3/R3 thing but still not working i have it under gnome profile but i feel lost i guess

Well... I can't really help here - I don't have a PS3.

I know Okiura was able to get the profiles working on the PS3, I'll ask him

---

### Post by Chonnawonga on 2009-11-04
Hi falkTX,

Thanks for the help. Was about to muck around with my source file and double-check, but decided to try again as-is before changing anything. Now it's installed and working.

I'm not sure what happened before. It seemed like the files just weren't in the repo. Go figure!

---

### Post by falkTX on 2009-11-04
> **Chonnawonga said:**
> Hi falkTX,

Thanks for the help. Was about to muck around with my source file and double-check, but decided to try again as-is before changing anything. Now it's installed and working.

I'm not sure what happened before. It seemed like the files just weren't in the repo. Go figure!

Maintaining 4 different repos is no easy task
I have my old QtSixA repo; QtSixA PPA; Personal PPA; and "falkuntu" PPA (a new project I'm working on)

Maybe it was my fault, not sure. Sorry if that's the case

---

### Post by Chonnawonga on 2009-11-04
No worries, and thanks for all the work you've put into this! It's very cool.

---

### Post by Okiura on 2009-11-04
> **futuresnake said:**
> okay i probably did somthing wrong before hand but i enabled L3/R3 thing but still not working i have it under gnome profile but i feel lost i guess


Once you've enabled the L3/R3 option you need to goto profiles and change to a differant one click apply then change back to the original one (this only need to be done once after enabling the L3/R3 option) then click apply, if this is not done the original fdi remains and the L3/R3 option are not added, Once you have done this disconnect and reconnect the Sixaxis. the Kbd and Mouse inputs are disabled by default so you will need to press both L3 and R3 once to enable them.

if this doesn't work for you let me know, i'll see what i can do :)


I have been looking for a way to enable these by default for a while now but not had much luck, FalkTX had the right idea of adding the option on the SixA config. I have tested this option on both my systems and it works well :)

Okiura,

---

### Post by falkTX on 2009-11-05
> **Okiura said:**
> Once you've enabled the L3/R3 option you need to goto profiles and change to a differant one click apply then change back to the original one (this only need to be done once after enabling the L3/R3 option) then click apply, if this is not done the original fdi remains and the L3/R3 option are not added, Once you have done this disconnect and reconnect the Sixaxis. the Kbd and Mouse inputs are disabled by default so you will need to press both L3 and R3 once to enable them.

if this doesn't work for you let me know, i'll see what i can do :)


I have been looking for a way to enable these by default for a while now but not had much luck, FalkTX had the right idea of adding the option on the SixA config. I have tested this option on both my systems and it works well :)

Okiura,

Many thanks again Okiura, you're the best.
I was in doubt if this was working or not... thanks for all the testing you've made so far.

Have you tried "man joystick" - there's a list of the available options there, but I don't have a PS3 to test all little changes.
Let me know if you find anything useful

---

### Post by Okiura on 2009-11-05
I found the options :)

```

Option StartMouseEnabled "True"
Option StartKeysEnabled "True"


```

can't get them to work in the fdi's though, gonna try in a xorg.conf instead also will try both fdi's and xorg.conf on my x86 just incase it's a broke ppc input-joystick build... didn't see the options in the source for ppc i'll do this today at some point and post update.

---

### Post by futuresnake on 2009-11-05
sigh :( not working for me i did what u said Okiura **** and still no luck if theres anything i can do to help im sort of noob but i can give some info i guess if it may help

---

### Post by Slumz187 on 2009-11-06
welcome to the linux world futuresnake lol and prepare to spend long hours on troubleshooting like i did! i feel your pain!

---

### Post by Okiura on 2009-11-06
> **Slumz187 said:**
> welcome to the linux world futuresnake lol and prepare to spend long hours on troubleshooting like i did! i feel your pain!

But it's worth it in the end :)

@ futuresnake, Yes I will need more info lets start at the beginning disconnect everything then open a terminal window (Applications > Accessories > Terminal). Next connect the controller, then run and paste the outputs for the following commands please.

```
dmesg
```

```
cat /var/log/Xorg.0.log
```

```
dpkg -l xserver-xorg-input*
```

*plz remember to put the CODE tag around each output

Okiura,

---

### Post by falkTX on 2009-11-06
I have good news!

QtSixA WILL be available in the official repositories.
I'm sure for Lucid and maybe for Karmic. Not sure about Jaunty though.

I just wanna fix some stuff first, complete the manuals and then release 1.0.3 for everyone.

---

### Post by falkTX on 2009-11-06
**Update:** *1.0.3 is here!*

Changelog:
>   * Fixed "Force connection" dialog
  * Use 'hcitool' to disconnect devices when python-dbus is not available
  * Use update-rc.d to register sixad service (PPA only, for happy RPMs)
  * Created man pages

The PPA repository may take a little more time to show the update, but it will come.

This release doesn't have the PS3 synaptics bug fixed anymore.
This because overriding a file that is in a different package is a debian policy violation. Ask the Ubuntu developers to fix the bug, or use the workaround.


Also, this is the version that will go to the Ubuntu repositories.
You can follow the integration here - [http://revu.ubuntuwire.com/p/qtsixa](http://revu.ubuntuwire.com/p/qtsixa)


See ya soon

---

### Post by ps3mhome on 2009-11-06
> **futuresnake said:**
> sigh :( not working for me i did what u said Okiura **** and still no luck if theres anything i can do to help im sort of noob but i can give some info i guess if it may help

I had some problems getting it to work at first, but now it works!! on PS3, DS3, 9.10 and QtSixa 1.0.2. Thanks falkTX and Okiura.

These were the steps I went through on QtSixa 1.0.2:

1  Went to "Configure Sixaxis" -> "Advanced" -> and checked "Use L3/R3 to enable/disable mouse and keyboard"
2. Connected DS3 with Gnome profile (the desired profile)
3. Selected different profile, Firefox. Clicked Apply.
4. Selected Gnome (the desired profile). Clicked Apply.
5. Disconnected.
6. Connected.
7. Pressed L3/R3 to enable/disable mouse/keys
It worked!

Thanks again FalkTX and congratulations on the place in the official repositories.

---

### Post by futuresnake on 2009-11-06
okay so reinstalled my ubuntu today( i kno im wierd like that) but when i went to try to download qtsixa i received an error... dont kno if ya aware of it

: sudo apt-get install qtsixa
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  qtsixa: Depends: sixad (>= 1.0.3) but it is not installable
E: Broken packages

---

### Post by falkTX on 2009-11-07
> **futuresnake said:**
> okay so reinstalled my ubuntu today( i kno im wierd like that) but when i went to try to download qtsixa i received an error... dont kno if ya aware of it

: sudo apt-get install qtsixa
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  qtsixa: Depends: sixad (>= 1.0.3) but it is not installable
E: Broken packages

Can you try again now?

---

### Post by futuresnake on 2009-11-07
same thing as above :(

---

### Post by kurupted on 2009-11-08
> **futuresnake said:**
> okay so reinstalled my ubuntu today( i kno im wierd like that) but when i went to try to download qtsixa i received an error... dont kno if ya aware of it

: sudo apt-get install qtsixa
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  qtsixa: Depends: sixad (>= 1.0.3) but it is not installable
E: Broken packagesI get exactly the same thing, Ironically its not a problem wit this version as I attempted to install every previous version after I installed 9.10 and I keep getting the exact same error with the "Depends: sixad (>= x.x.x)" always changing depending on the version.

For the record I'm trying to install it on my PS3.

---

### Post by Slumz187 on 2009-11-08
> **Okiura said:**
> But it's worth it in the end :)

Okiura,


lmao...ur right man..but umm falk im getting the exact same update error everyone else is getting when trying to upgrade qtsixa

---

### Post by falkTX on 2009-11-08
... :lolflag:

---

### Post by falkTX on 2009-11-08
as I said before, PPA is ONLY available to 32/64bit PCs.
Launchpad doesn't compile PowerPC binaries anymore, so no PS3 support in PPAs.

Please, PS3 users, MUST use the old, untrusted, repo.
```
deb http://falktx.xtreemhost.com/repo/ubuntu ubuntu main
```

*EDIT: Sorry I didn't noticed this sooner*

---

### Post by Slumz187 on 2009-11-08
> **falkTX said:**
> .... don't you guys read...?

as I said before, PPA is ONLY available to 32/64bit PCs.
Launchpad doesn't compile PowerPC binaries anymore, so no PS3 support in PPAs.

Please, PS3 users, MUST use the old, untrusted, repo.
```
deb http://falktx.xtreemhost.com/repo/ubuntu ubuntu main
```.... ](*,)

ive always used the old untrusted repo..today as soon as i turned my ps3 on to upgrade the qtsixa program, i got :

```
 The following packages have unmet dependencies:
  qtsixa: Depends: sixad (>= 1.0.3) but 1.0.1-falktx1 is to be installed
E: Broken packages
```

I then tried to add the ppa anyway just to mess around with it, and still a no go!

---

### Post by kurupted on 2009-11-08
> **Slumz187 said:**
> ive always used the old untrusted repo..today as soon as i turned my ps3 on to upgrade the qtsixa program, i got :

```
 The following packages have unmet dependencies:
  qtsixa: Depends: sixad (>= 1.0.3) but 1.0.1-falktx1 is to be installed
E: Broken packages
```I then tried to add the ppa anyway just to mess around with it, and still a no go!Ditto

---

### Post by falkTX on 2009-11-08
Oops... my bad! :roll:

Fixed now. Please try again, it should work now

---

### Post by oifish on 2009-11-08
I just tried to install and I get the same error.

```
The following packages have unmet dependencies:
  qtsixa: Depends: sixad (>= 1.0.3) but 0.9-falktx1 is to be installed
E: Broken packages
```

---

### Post by kurupted on 2009-11-08
```
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  qtsixa: Depends: sixad (>= 1.0.3) but it is not installable
E: Broken packages

```Thats what I still get.

---

### Post by futuresnake on 2009-11-09
yup yup  i just tried now and got same error as one above me

---

### Post by falkTX on 2009-11-09
EDiT: this post was useless.
The problem was been solved now (only affected PS3 users)

---

### Post by falkTX on 2009-11-09
Ha! I finally found the problem.

Just a typo error: "powerpc32" instead of "powerpc".
This was introduced when I started reformatting the source code, so it could easily be updated old repo & PPA at the same time.

Sorry for the little problem

---

### Post by falkTX on 2009-11-09
**Update:** *v1.0.3a or 1.0.3-falktx2*

Just an update to fix the PS3 typo in the packages and also PATH to man pages.


The QtSixA webpage is almost complete:
[http://qtsixa.sourceforge.net/](http://qtsixa.sourceforge.net/)

---

### Post by Slumz187 on 2009-11-09
okay ill be the first to confirm that it works now..

thanx falk ur the man!

---

### Post by futuresnake on 2009-11-09
:) i got it to work thz guys for teh help now if only ya could get rid of r3/l3 things for i can use that for right clicks and left clicks that would be awesome
_Okiura_ if u still want the info u ask before, ill give it to u i dont kno if its still relevant since its working already

---

### Post by ps3mhome on 2009-11-10
Just updated to 1.0.3 and it works on PS3, DS3 and 9.10. Many thanks falkTX. 

A question though: with gnome profile, for instance, left axis, right axis, x and o behave as expected, as mouse, scroller, left and right click, respectively. I'm not quite sure what to expect, but no other buttons seem to work. Shouldn't they work according to the profile? For example, R2=End. 

And in keyboard mode, excepting x and o, the buttons return numbers.

Sorry if I'm missing something obviuos.

One more question (indirecly related to QtSixA): This Authorization request dialog, I keep getting it despite having ticked Always grant access.

---

### Post by falkTX on 2009-11-11
> **ps3mhome said:**
> Just updated to 1.0.3 and it works on PS3, DS3 and 9.10. Many thanks falkTX. 

A question though: with gnome profile, for instance, left axis, right axis, x and o behave as expected, as mouse, scroller, left and right click, respectively. I'm not quite sure what to expect, but no other buttons seem to work. Shouldn't they work according to the profile? For example, R2=End. 

And in keyboard mode, excepting x and o, the buttons return numbers.

Sorry if I'm missing something obviuos.

One more question (indirecly related to QtSixA): This Authorization request dialog, I keep getting it despite having ticked Always grant access.

The 1.0.3 doesn't have the synaptics PS3 bug fixed anymore (debian policy violation). Maybe it's because of that..? I don't really know.
You should enable the "Toggle On/Off" option if running in the PS3. Does it still return numbers even with the L3/R3 thing?
I can't really support any PS3 stuff since I don't have one. You have to wait for others to comment about it.

What's about the authorization dialog? Not sure I get your point.. :-k

---

### Post by ps3mhome on 2009-11-11
> **falkTX said:**
> The 1.0.3 doesn't have the synaptics PS3 bug fixed anymore (debian policy violation). Maybe it's because of that..? I don't really know.
You should enable the "Toggle On/Off" option if running in the PS3. Does it still return numbers even with the L3/R3 thing?
I can't really support any PS3 stuff since I don't have one. You have to wait for others to comment about it.

What's about the authorization dialog? Not sure I get your point.. :-k

(The "Toggle On/Off" is enabled). I press R3 for keyboard mode, then all buttons except x and o (which work properly) return numbers. It was the same with 1.0.2. 

Sorry about the unclear writing; even failed to come up with the question. With the DS3 disconnected, pressing the PS button to connect results in an "Authorization request" dialog asking whether the PLAYSTATION(R)3 Controller (00:21:4F:XX:XX:XX) should be granted access to "00001124-0000-..." (the computer I guess). There is also a checkbox "Always grant access". I tick the checkbox and click Yes to grant access. The DS3 connects and works. If I later Disconnect and then press the PS button, I have to go through the "Authorization request" dialog again, despite having ticked "Always grant access". Why? (I cannot respond to "Authorization request" dialog using the DS3, since the DS3 is disconnected.)

---

### Post by falkTX on 2009-11-11
> **ps3mhome said:**
> (The "Toggle On/Off" is enabled). I press R3 for keyboard mode, then all buttons except x and o (which work properly) return numbers. It was the same with 1.0.2. 

Sorry about the unclear writing; even failed to come up with the question. With the DS3 disconnected, pressing the PS button to connect results in an "Authorization request" dialog asking whether the PLAYSTATION(R)3 Controller (00:21:4F:XX:XX:XX) should be granted access to "00001124-0000-..." (the computer I guess). There is also a checkbox "Always grant access". I tick the checkbox and click Yes to grant access. The DS3 connects and works. If I later Disconnect and then press the PS button, I have to go through the "Authorization request" dialog again, despite having ticked "Always grant access". Why? (I cannot respond to "Authorization request" dialog using the DS3, since the DS3 is disconnected.)

Ooh...
That happens on Gnome, not KDE.
It is the bluetooth manager detecting an "untrusted device" (the Sixaxis), and just shows that dialog everytime...
I know that if you grant full access (I even tried setting it manually), it ignores yours settings and ask for authorization again.

If you don't use bluetooth for anything else you could remove the Gnome bluetooth manager:
```
sudo apt-get remove bluez-gnome gnome-bluetooth
```

This is a bug somewhere in BlueZ or the applet itself.
If you don't mind, maybe you could report a bug about it..?

Not sure about the buttons and numbers thing though. Anyone else has this issue?

---

### Post by ps3mhome on 2009-11-11
> **falkTX said:**
> Ooh...
That happens on Gnome, not KDE.
It is the bluetooth manager detecting an "untrusted device" (the Sixaxis), and just shows that dialog everytime...
I know that if you grant full access (I even tried setting it manually), it ignores yours settings and ask for authorization again.

If you don't use bluetooth for anything else you could remove the Gnome bluetooth manager:
```
sudo apt-get remove bluez-gnome gnome-bluetooth
```

This is a bug somewhere in BlueZ or the applet itself.
If you don't mind, maybe you could report a bug about it..?

Not sure about the buttons and numbers thing though. Anyone else has this issue?

Thanks falkTX. I would like to do it, but how do I report a bug?

About the numbers, it is not random numbers or so, a given button return the same digit consistently. So maybe it would be possible to find the mapping. And, as I said, R2=End, L2=Home, L1=Menus, and so on, don't work at all, when in mouse mode.

---

### Post by DanielBC on 2009-11-16
Hi falkTX!
I'm also having the same problem that ps3mhome has. The button mapping is not the one as the one that is stated in the fdi file. I even tried to setup my own profile but, instead of actually returning the keys that I configured, it just returned the numbers from 0 to 9 (e.g., if I pressed circle it would return me 9)

---

### Post by ps3mhome on 2009-11-16
> **DanielBC said:**
> Hi falkTX!
I'm also having the same problem that ps3mhome has. The button mapping is not the one as the one that is stated in the fdi file. I even tried to setup my own profile but, instead of actually returning the keys that I configured, it just returned the numbers from 0 to 9 (e.g., if I pressed circle it would return me 9)

Hi DanielBC. We seem to have the same problem just getting the digits 0-9 in keyboard mode. In the Gnome profile, in mouse mode, R2=End, L2=Home, L1=Menus and so on, do not work for me, nothing seems to happen. Do they work for you?

---

### Post by falkTX on 2009-11-17
This is probably related to the PS3 synaptics bug.

Try this:
```
sudo apt-get remove xserver-xorg-input-synaptics
```
Then restart.
Does it still return numbers instead of the real keys?

---

### Post by ps3mhome on 2009-11-17
Did sudo apt-get remove xserver-xorg-input-synaptics.
Then restarted.

Result: Still digits being returned, and also = and -. Probably same as before (not sure if I got = and - then though).

---

### Post by falkTX on 2009-11-17
> **ps3mhome said:**
> Did sudo apt-get remove xserver-xorg-input-synaptics.
Then restarted.

Result: Still digits being returned, and also = and -. Probably same as before (not sure if I got = and - then though).

Did this happened all the time, or is it recent?
If it's recent, can you give me an approximate version number?

---

### Post by ps3mhome on 2009-11-18
> **falkTX said:**
> Did this happened all the time, or is it recent?
If it's recent, can you give me an approximate version number?

QtSixA 1.0.2 (and 9.10) was the first version when the DS3 worked as a mouse at all for me on the PS3. As far as I remember, inGnome profile the buttons returned the same digits then also (and probably - and =, I did not investigate it systematically really). Now in QtSixA 1.0.3 and 9.10 the following is returned in Gnome profile (in keyboard mode):
start=1; arrows: up=2, r=3, dn=4, l=5; select=nothing; ps= = ; triangle=0; square=-; L2=6; L1=8; R2=7; R1=9.

---

### Post by falkTX on 2009-11-18
> **ps3mhome said:**
> QtSixA 1.0.2 (and 9.10) was the first version when the DS3 worked as a mouse at all for me on the PS3. As far as I remember, inGnome profile the buttons returned the same digits then also (and probably - and =, I did not investigate it systematically really). Now in QtSixA 1.0.3 and 9.10 the following is returned in Gnome profile (in keyboard mode):
start=1; arrows: up=2, r=3, dn=4, l=5; select=nothing; ps= = ; triangle=0; square=-; L2=6; L1=8; R2=7; R1=9.

The only thing I think that could have caused this is still the synaptics bug.
On v1.0.2 the bug was automatically fixed (by overriding another's package file).
But since that is a debian violation I had to remove it.

Can you try:
```
sudo gedit /usr/share/hal/fdi/policy/20thirdparty/11-x11-synaptics.fdi
```
And comment this line by adding <!-- before and --> after
```
<!--
**<merge key="input.x11_driver" type="string">synaptics</merge>**
-->
```

---

### Post by falkTX on 2009-11-18
**Update** v1.0.4

Changelog:
>   * Use "ppc64" for 64-bit PowerPC (used in some RPM distros)
  * Fixed sixad-raw (looking for 2nd argument instead of 1st)
  * Use "/var/lib/sixad/" for STORAGEDIR instead of "/" (root)


PS: Did no one noticed a weird folder name in the root folder... LOL

---

### Post by falkTX on 2009-11-18
Good news for PC people! (but not PS3)

I started my own gaming PPA:
[https://launchpad.net/~falk-t-j/+archive/games](https://launchpad.net/~falk-t-j/+archive/games)

At this moment it has:
- PCSX Reloaded (Latest)
- Super Maryo Chronicles v1.9.1
- UltraStar Deluxe (Stable SVN, I tested that myself)


Enjoy!

---

### Post by ps3mhome on 2009-11-18
The file /usr/share/hal/fdi/policy/20thirdparty/11-x11-synaptics.fdi does not exist.

---

### Post by digge on 2009-11-18
May i make a suggestion falkTX, i fully understand that they don't want one program to poke around in the files of another. However you could make some detection code and pop up a window or something and maybe a link to some info about the problem? Would save you some support time for the occasions when it actually is the problem.

---

### Post by falkTX on 2009-11-18
> **digge said:**
> May i make a suggestion falkTX, i fully understand that they don't want one program to poke around in the files of another. However you could make some detection code and pop up a window or something and maybe a link to some info about the problem? Would save you some support time for the occasions when it actually is the problem.

I'll probably do that soon. Not sure how yet, but I'll look into it.

Sorry guys but I don't really know what is causing this issue.
I do not have a PS3 to test out stuff, so you're on your own.
If someone finds a solution though, I'll implemented it right away.

---

### Post by ps3mhome on 2009-11-19
Thanks for your efforts falkTX. If I remember correctly the problem with buttons returning digits etc was present also in QtSixA v1.0.2 (and 9.04), but that was the first version in which the DS3 worked as a mouse.

---

### Post by DanielBC on 2009-11-19
Hi FalkTX!

I tried what you said: I first commented the line where <merge key="input.x11_driver" type="string">synaptics</merge> was written
in the /usr/share/hal/fdi/policy/20thirdparty/11-x11-synaptics.fdi file. But when I tried to see if with that my issue was resolved, it still gave me the same problem...
Then I issued the command sudo apt-get remove xserver-xorg-input-synaptics, and once again tried to see if the issue was resoved, but nothing...
I'm am using Karmic 9.10 and QtSixA 1.0.4... And I'm using a laptop... not a ps3...

---

### Post by falkTX on 2009-11-20
> **DanielBC said:**
> I'm am using Karmic 9.10 and QtSixA 1.0.4... And I'm using a laptop... not a ps3...

That's weird.
I do run Karmic 9.10, QtSixA 1.0.5 (not released yet), 64bit.
Are you running 32bit?

Anyway, this is weird. This never happened before...
I'll install a Karmic 32bit in VirtualBox and try to see if I can get this issue

---

### Post by falkTX on 2009-11-21
**Update:** v1.1.0 Beta (PPA Only)

Changelog:
>   * Fixed some issues related to creating a new profile
  * You can view a FULL list of possible keys now
  * Removed update info at startup
  * Added "Show warnings" option, which will show:
    - No bluetooth dongle detected -> no bluetooth support
    - Running PowerPC[32] without Legacy enabled
  * Configuration file:
    - Now in ~/.qtsixa instead of ~/.qtsixa/qtsixa.conf
    - Uses yes/no instead of 0/1
  * Sixaxis Profiles can now use spaces
  * Added new devices to notifications:
    - Bluetooth dongles (*all*)
    - Generic USB Joystick (0079:0006)
  * Supported new device: Generic USB Joystick (0079:0006)
  * Fixed display bug when 2+ USB joysticks where connected
  * Fixed sixad-raw crashing X
  * Some other small fixes
  * Marked release as Beta (PPA only)

Released as beta because I always forgot something...

I've tested QtSixA under a 32-bit VirtualBox and the Sixaxis Profiles worked just fine (except for mouse, due a VBox bug).
So the "returning numbers" bug should only be caused by 3 things:
1 - Broken profiles (The new PPA update will come with a try-out for this prob, please test it out)
2 - "Toogle L3/R3..." thing option is messing with something (please test this option on/off)
3 - A recent Ubuntu update broke the whole thing (try booting a clean LiveCD/USB and just install QtSixA without any other updates)

I was also thinking of supporting more than just Sixaxis... But, nah, not right now.
I added the "Generic" joystick one because some Sixaxis imitations use that device ID when used on a PC.

Final 1.1 will come soon

---

### Post by ps3mhome on 2009-11-25
Tested 1.0.4 on ps3, ds3, 9.10, Gnome and Firefox profiles. L3 works as mouse with x and o as left and right click, but other buttons do not seem to respond. In Gnome keyboard mode: R3 scrolls, other buttons return 1-9, ', +, and select returns nada; this is slightly different from 1.0.3. In Firefox keyboard mode: R3 scrolls, other buttons return 1-7, "89", ', w, "delete" and +; in Firefox app, R3 can't be toggled off, always on as a scroller; in gedit, R3 can be toggled off, when on scrolls up and down, but returns tab and q instead of left and right scroll.

---

### Post by Davidhal on 2009-11-25
Everytime I apply the sixad driver on hidraw device I get "error on send_event" all over terminal. It was working fine just earlier today. I'm actually using a third party PS3 controller, so qtsixa just sees it as USB since it requires a separate dongle. 

I tried it on my other PC, I would get the same error, then the x session would crash and some message about maximum joydev.

---

### Post by falkTX on 2009-11-26
> **Davidhal said:**
> Everytime I apply the sixad driver on hidraw device I get "error on send_event" all over terminal. It was working fine just earlier today. I'm actually using a third party PS3 controller, so qtsixa just sees it as USB since it requires a separate dongle. 

I tried it on my other PC, I would get the same error, then the x session would crash and some message about maximum joydev.

I noticed that bug too.
I've fixed it already and an update is coming soon

---

### Post by falkTX on 2009-11-26
> **ps3mhome said:**
> Tested 1.0.4 on ps3, ds3, 9.10, Gnome and Firefox profiles. L3 works as mouse with x and o as left and right click, but other buttons do not seem to respond. In Gnome keyboard mode: R3 scrolls, other buttons return 1-9, ', +, and select returns nada; this is slightly different from 1.0.3. In Firefox keyboard mode: R3 scrolls, other buttons return 1-7, "89", ', w, "delete" and +; in Firefox app, R3 can't be toggled off, always on as a scroller; in gedit, R3 can be toggled off, when on scrolls up and down, but returns tab and q instead of left and right scroll.

So it's just the keyboard that is not working right.
Let me prepare the update and then we'll see about this

---

### Post by Davidhal on 2009-11-26
> **falkTX said:**
> I noticed that bug too.
I've fixed it already and an update is coming soon

Great! Keep up the good work, can't wait to be able to play emulators with my gamepad in Linux :D

---

### Post by falkTX on 2009-11-26
**Update:** v1.1.0 is here!

The changelog is pretty much is same as the beta, just fixed notifications and some other small stuff.


The webpage is now "complete" (could be better, but it could be worse too...)
[http://qtsixa.sourceforge.net/](http://qtsixa.sourceforge.net/)

---

### Post by falkTX on 2009-11-26
> **ps3mhome said:**
> Tested 1.0.4 on ps3, ds3, 9.10, Gnome and Firefox profiles. L3 works as mouse with x and o as left and right click, but other buttons do not seem to respond. In Gnome keyboard mode: R3 scrolls, other buttons return 1-9, ', +, and select returns nada; this is slightly different from 1.0.3. In Firefox keyboard mode: R3 scrolls, other buttons return 1-7, "89", ', w, "delete" and +; in Firefox app, R3 can't be toggled off, always on as a scroller; in gedit, R3 can be toggled off, when on scrolls up and down, but returns tab and q instead of left and right scroll.

Let's take care of this problem now.
Can you update to QtSixA 1.1.0 and check if this is still present?

---

### Post by Davidhal on 2009-11-26
Still getting the error on send_event error with 1.1.0

Ubuntu 9.10 32-bit and Ubuntu 9.04 64-bit, same results.

---

### Post by falkTX on 2009-11-26
> **Davidhal said:**
> Still getting the error on send_event error with 1.1.0

Ubuntu 9.10 32-bit and Ubuntu 9.04 64-bit, same results.

You're talking about sixad crashing, isn't it?
Are you sure you're using v1.1.0?

---

### Post by falkTX on 2009-11-26
Aaa!

please run:
```
sudo modprobe uinput
```
Before runing sixad.


The uinput module doesn't load automatically.
This is done in sixad (bluetooth mode) BTW, but sixad-raw needs manual loading of uinput.
You only need to run the command once per boot.

Then start sixad-raw by running:
```
sudo sixad-raw /dev/hidrawX
```
Where X is the # of the joystick hidraw (check "dmesg"), or use the last tab on the GUI, under "advanced".

---

### Post by Davidhal on 2009-11-26
> **falkTX said:**
> Aaa!

please run:
```
sudo modprobe uinput
```
Before runing sixad.


The uinput module doesn't load automatically.
This is done in sixad (bluetooth mode) BTW, but sixad-raw needs manual loading of uinput.
You only need to run the command once per boot.
Ah, this fixed it, thanks :D

I'll just add uinput to /etc/modules

---

### Post by falkTX on 2009-11-26
> **Davidhal said:**
> Ah, this fixed it, thanks :D

For the next update, I'll make sure to load uniput at boot.
Any clues on how to do that?

---

### Post by Davidhal on 2009-11-26
> **falkTX said:**
> For the next update, I'll make sure to load uniput at boot.
Any clues on how to do that?
Make it run this command on install
```

sudo echo -e "uinput" | sudo tee -a /etc/modules

```
This will append it to /etc/modules, and therefore it will be modprobed on startup.

---

### Post by Davidhal on 2009-11-26
Hmm, I'm trying to play extremetuxracer with the accelerometer, I enabled the accelerometer direction under profile and applied, but nothing happens in-game. I know the accelerometer is working, because when I'm mapping buttons in GFCEUX the mapping goes bananas when I move the controller about.

---

### Post by ps3mhome on 2009-11-26
> **falkTX said:**
> Let's take care of this problem now.
Can you update to QtSixA 1.1.0 and check if this is still present?

Just tested 1.1.0. In keyboard mode, digits etc still being returned; in mouse mode, non-working R2=End, L2=Home, L1=Menus and so on.

---

### Post by scotthew1 on 2009-11-27
hey i'm probably missing something obvious or just really don't understand something, but i'm confused. I'm trying to create a custom profile with left and right mouse buttons but i really don't understand how to do that. the "tips and tricks" say to use "mouse_BUTTON (where BUTTON is a number)" but i don't know what the number would be or how i should be doing this? and advice would be great help as i haven't been able to find any answer for this. also, know that i've accumulated a good number of test profiles under my settings, i was wondering how i would go about deleting profiles.

thanks!

---

### Post by falkTX on 2009-11-27
> **scotthew1 said:**
> hey i'm probably missing something obvious or just really don't understand something, but i'm confused. I'm trying to create a custom profile with left and right mouse buttons but i really don't understand how to do that. the "tips and tricks" say to use "mouse_BUTTON (where BUTTON is a number)" but i don't know what the number would be or how i should be doing this? and advice would be great help as i haven't been able to find any answer for this. also, know that i've accumulated a good number of test profiles under my settings, i was wondering how i would go about deleting profiles.

thanks!

I only know 3 mouse buttons:
#1 - left click
#2 - middle click (the scroll click)
#3 - right click
The other ones are rarely used

You can remove your custom profiles, but you'll have to remove all.
Somewhere in the menu there's an option to restore the default profiles (not in my PC now, so not sure where it is)

---

### Post by falkTX on 2009-11-27
> **Davidhal said:**
> Hmm, I'm trying to play extremetuxracer with the accelerometer, I enabled the accelerometer direction under profile and applied, but nothing happens in-game. I know the accelerometer is working, because when I'm mapping buttons in GFCEUX the mapping goes bananas when I move the controller about.

hmm... you're using Karmic I suppose...
Try this:
1 - Delete the ".etracer" in home folder (it's hidden)
2 - Launch the game, go to settings and quit (check if the folder was created)
3 - In QtSixA, go to "Configure Sixaxis" and make sure Accelerometers are checked (if not, check it and stop "sixad" using the menu option for it)
4 - Apply the game profile in QtSixA

I'll try this soon too, but try checking if the folder contents gets modified when you apply the profile in QtSixA.
You can also get QtSixA output by running it in a terminal:
```
qtsixa
```
If there is any error, it will be reported

---

### Post by falkTX on 2009-11-27
> **ps3mhome said:**
> Just tested 1.1.0. In keyboard mode, digits etc still being returned; in mouse mode, non-working R2=End, L2=Home, L1=Menus and so on.

Let me check if I understood right. (tell me what #s are correct)

1 - Connecting the Sixaxis to PC works just fine (including LEDs)
2 - The Sixaxis works as joystick (buttons, axis, etc)
3 - You have not set any Sixaxis profile override
[Go to "Configure Sixaxis" and click on the bottom, "Show Sixaxis Overrides"]
4 - You have not set the Legacy driver option


When you apply a profile (let's take "Gnome" as example):
5 - Mouse works fine (Left & Right Axis; X and O as mouse clicks)
6 - Any other button ([], Tri, L~R~1~2, Up/Down/Right/Left) return numbers or incorrect stuff
7 - Using the "Toggle L3/R3" thing doesn't change anything


What's your output for:
```
uname -a
```

---

### Post by Davidhal on 2009-11-27
> **falkTX said:**
> hmm... you're using Karmic I suppose...
Try this:
1 - Delete the ".etracer" in home folder (it's hidden)
2 - Launch the game, go to settings and quit (check if the folder was created)
3 - In QtSixA, go to "Configure Sixaxis" and make sure Accelerometers are checked (if not, check it and stop "sixad" using the menu option for it)
4 - Apply the game profile in QtSixA

I'll try this soon too, but try checking if the folder contents gets modified when you apply the profile in QtSixA.
You can also get QtSixA output by running it in a terminal:
```
qtsixa
```
If there is any error, it will be reported
I'm actually using Mint 7 (Jaunty) on the PC I'm trying to run this on, but I suppose I could boot it into Karmic and see if it works there.

---

### Post by ps3mhome on 2009-11-27
> **falkTX said:**
> Let me check if I understood right. (tell me what #s are correct)

1 - Connecting the Sixaxis to PC works just fine (including LEDs)
2 - The Sixaxis works as joystick (buttons, axis, etc)
3 - You have not set any Sixaxis profile override
[Go to "Configure Sixaxis" and click on the bottom, "Show Sixaxis Overrides"]
4 - You have not set the Legacy driver option


When you apply a profile (let's take "Gnome" as example):
5 - Mouse works fine (Left & Right Axis; X and O as mouse clicks)
6 - Any other button ([], Tri, L~R~1~2, Up/Down/Right/Left) return numbers or incorrect stuff
7 - Using the "Toggle L3/R3" thing doesn't change anything


What's your output for:
```
uname -a
```

1. Yes, I do not know what to expect about the leds, but 1st connection lights 1st led, disconnect-reconnect lights 2nd led, and so on. Have not paid much attention to the leds.
2. This is with no profile set (None), I presume. Before R3/L3 are pressed, nothing happens when DS3 is used. After L3 is pressed to invoke mouse mode, L3, left and right click works as mouse. R3 scrolls. Toggle R3/L3 works. After R3 has been pressed to invoke keyboard mode, digits etc are returned; R3 scrolls correctly. 
3. No. Only non-default setting is R3/L3 toggle on/off.
4. No.

5. In Gnome profile: After L3 is pressed to invoke mouse mode, Yes, Left & Right Axis; X and O as mouse clicks, works. Other buttons do not respond (in mouse mode).
6. Yes, but only after R3 has toggled keyboard mode on.
7. No, R3/L3 toggles mouse/keyboard on/off. Before L3 or R3 pressed, nothing at all happens when buttons are pressed and axes are manipulated.

uname -a:
Linux ubuntu 2.6.31-14-powerpc64-smp #48-Ubuntu SMP Fri Oct 16 15:56:40 UTC 2009 ppc64 GNU/Linux

Just an observation, it seems that Gnome and Firefox profiles (the ones I tested) works similar, but not exactly, as no profile (None).

---

### Post by falkTX on 2009-11-27
> **ps3mhome said:**
> 1. Yes, I do not know what to expect about the leds, but 1st connection lights 1st led, disconnect-reconnect lights 2nd led, and so on. Have not paid much attention to the leds.
2. This is with no profile set (None), I presume. Before R3/L3 are pressed, nothing happens when DS3 is used. After L3 is pressed to invoke mouse mode, L3, left and right click works as mouse. R3 scrolls. Toggle R3/L3 works. After R3 has been pressed to invoke keyboard mode, digits etc are returned; R3 scrolls correctly. 
3. No. Only non-default setting is R3/L3 toggle on/off.
4. No.

5. In Gnome profile: After L3 is pressed to invoke mouse mode, Yes, Left & Right Axis; X and O as mouse clicks, works. Other buttons do not respond (in mouse mode).
6. Yes, but only after R3 has toggled keyboard mode on.
7. No, R3/L3 toggles mouse/keyboard on/off. Before L3 or R3 pressed, nothing at all happens when buttons are pressed and axes are manipulated.

uname -a:
Linux ubuntu 2.6.31-14-powerpc64-smp #48-Ubuntu SMP Fri Oct 16 15:56:40 UTC 2009 ppc64 GNU/Linux

Just an observation, it seems that Gnome and Firefox profiles (the ones I tested) works similar, but exactly, as no profile (None).

Do you have that synaptics PS3 bug fixed?

---

### Post by ps3mhome on 2009-11-27
> **falkTX said:**
> Do you have that synaptics PS3 bug fixed?


Probably not. I tried to follow your instructions earlier and commenting out stuff in the file /usr/share/hal/fdi/policy/20thirdparty/11-x11-synaptics.fdi, but that file did not exist. Now there is a file "11-x11-synaptics.fdi~". I did the recommended commenting out on that file and restarted, but nothing seems to have changed, the DS3 works but with the digits etc problem still present.

Moreover, If I remember correctly the problem with buttons returning digits etc was present also in QtSixA v1.0.2, which allegedly had a fix for the synaptics bug. 1.02 was btw the first version in which the DS3 worked as a mouse for me.

---

### Post by falkTX on 2009-11-30
> **ps3mhome said:**
> Probably not. I tried to follow your instructions earlier and commenting out stuff in the file /usr/share/hal/fdi/policy/20thirdparty/11-x11-synaptics.fdi, but that file did not exist. Now there is a file "11-x11-synaptics.fdi~". I did the recommended commenting out on that file and restarted, but nothing seems to have changed, the DS3 works but with the digits etc problem still present.

Moreover, If I remember correctly the problem with buttons returning digits etc was present also in QtSixA v1.0.2, which allegedly had a fix for the synaptics bug. 1.02 was btw the first version in which the DS3 worked as a mouse for me.

So this was always like this, I guess.
Just that in previous versions the profiles didn't worked at all, right?

By the way (you're using powerpc64...), are you using a Mac? (that would be cool)

---

### Post by ps3mhome on 2009-11-30
> **falkTX said:**
> So this was always like this, I guess.
Just that in previous versions the profiles didn't worked at all, right?

By the way (you're using powerpc64...), are you using a Mac? (that would be cool)

Yes, since v1.0.2, ds3 works as a mouse (profile none). It's possible that the profiles have never worked.

No, I'm using a ps3, not a Mac. Isn't there some confusion about whether the ps3 CPU is 32, 64 or even 128-bit?

---

### Post by narmoture on 2009-12-01
Just wanted to say that I like that you've developed this program and I would love to use it!

Unfortunately, it doesn't seem to want to install on my laptop, I always get the error "dependency not satisfiable libbluetooth3" when I click on the deb file. I use Intrepid 64-bit, if that helps. I'm also new to this, but if you want any further info, just ask. Be sure to explain, though...

EDIT: I should point out that I plan to use it wired...

---

### Post by Davidhal on 2009-12-01
> **narmoture said:**
> Just wanted to say that I like that you've developed this program and I would love to use it!

Unfortunately, it doesn't seem to want to install on my laptop, I always get the error "dependency not satisfiable libbluetooth3" when I click on the deb file. I use Intrepid 64-bit, if that helps. I'm also new to this, but if you want any further info, just ask. Be sure to explain, though...

EDIT: I should point out that I plan to use it wired...
I had the same problem on Jaunty, you need to install the Karmic version of libbluetooth3, just find the .debs online.

---

### Post by AAUBUNTU on 2009-12-02
Has anyone tried this application in Xubuntu 9.10 running on PS3?  I can get my sixaxis to show up as a connected device via bluetooth, but can't get it to work as keyboard/mouse.

---

### Post by falkTX on 2009-12-02
> **AAUBUNTU said:**
> Has anyone tried this application in Xubuntu 9.10 running on PS3?  I can get my sixaxis to show up as a connected device via bluetooth, but can't get it to work as keyboard/mouse.

Enable the option "Toggle profiles on/off" and re-connect the Sixaxis.
You can then use L3 to activate mouse and R3 for keyboard.

That is only a problem in PS3, regular PCs don't need this option (profiles work right away)

---

### Post by falkTX on 2009-12-02
> **Davidhal said:**
> I had the same problem on Jaunty, you need to install the Karmic version of libbluetooth3, just find the .debs online.

Maybe you're using the PPA? (It is only for Karmic...)
Try using the other repo, ...xtreemhost.com/... something

Anyway, go to packages.ubuntu.com to find Ubuntu packages

---

### Post by falkTX on 2009-12-02
> **ps3mhome said:**
> Yes, since v1.0.2, ds3 works as a mouse (profile none). It's possible that the profiles have never worked.

No, I'm using a ps3, not a Mac. Isn't there some confusion about whether the ps3 CPU is 32, 64 or even 128-bit?

I believe the PS3 CPU is 64bit.
The problem is that, in Ubuntu, there's only 1 powerpc arch type. (there should at least powerpc[32] and ppc64, like some other distros do).

But since PowerPC is not an official supported platform, it is pretty cool that there are still people caring about it

---

### Post by falkTX on 2009-12-02
**Update:** v1.1.1

Changelog:
>   * modprobe uinput before running sixad-raw (GUI only)
  * Added new option: "uinput at boot"
  * Fixed systray showing a previously connected device

Just fixing some small stuff

---

### Post by AAUBUNTU on 2009-12-02
> **falkTX said:**
> Enable the option "Toggle profiles on/off" and re-connect the Sixaxis.
You can then use L3 to activate mouse and R3 for keyboard.

That is only a problem in PS3, regular PCs don't need this option (profiles work right away)

Thanks, that worked.

---

### Post by falkTX on 2009-12-03
> **AAUBUNTU said:**
> Thanks, that worked.

Does the keyboard works as well?
Some users report that the keyboard stuff doesn't work in PS3.

Can you confirm this?

---

### Post by skuzzel on 2009-12-05
Getting this error message in the terminal?

Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  qtsixa: Depends: sixad (>= 1.0.3) but it is not going to be installed
E: Broken packages

---

### Post by Davidhal on 2009-12-05
> **skuzzel said:**
> Getting this error message in the terminal?

Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  qtsixa: Depends: sixad (>= 1.0.3) but it is not going to be installed
E: Broken packages
This happens if you are trying to install it on a distro older than 9.10, you need to manually download some files that are too old in the 9.04 repos.

---

### Post by falkTX on 2009-12-05
> **Davidhal said:**
> This happens if you are trying to install it on a distro older than 9.10, you need to manually download some files that are too old in the 9.04 repos.

The PPA should be used only for Karmic... that way it wouldn't be any problems.

But... I'm a nice guy; I'll upload the missing packages to the PPA

---

### Post by robertneville777 on 2009-12-16
Hey Falk, NICE program you've come up with here! I just have one slight problem. I cannot custom map the controls anymore, i.e. setting "R1" to "left click" or "X" to "spacebar." At first, I could open up -->"Settings"-->"Configure Sixaxis" tab, but now nothing happens when I try to open up that tab. Here's what it says in terminal:

Main Qt version: 4.5.2
Python-Qt version: 4.6
Will use 'gksu' for root actions
Traceback (most recent call last):
  File "/usr/share/qtsixa/gui/qtsixa.pyw", line 1214, in func_ConfSixaxis
    QtSixA_ConfSixaxis_Window().exec_()
  File "/usr/share/qtsixa/gui/qtsixa.pyw", line 443, in __init__
    self.inputComboBox.addItem(listOfSixaxisProfiles[i+1])
IndexError: list index out of range

Any ideas on what's going wrong? I really like this program; I just need to customize my settings. Anyway, let me know how I can fix that.

Thanks! And keep up the good work!

robertneville777

---

### Post by falkTX on 2009-12-17
> **robertneville777 said:**
> Hey Falk, NICE program you've come up with here! I just have one slight problem. I cannot custom map the controls anymore, i.e. setting "R1" to "left click" or "X" to "spacebar." At first, I could open up -->"Settings"-->"Configure Sixaxis" tab, but now nothing happens when I try to open up that tab. Here's what it says in terminal:

Main Qt version: 4.5.2
Python-Qt version: 4.6
Will use 'gksu' for root actions
Traceback (most recent call last):
  File "/usr/share/qtsixa/gui/qtsixa.pyw", line 1214, in func_ConfSixaxis
    QtSixA_ConfSixaxis_Window().exec_()
  File "/usr/share/qtsixa/gui/qtsixa.pyw", line 443, in __init__
    self.inputComboBox.addItem(listOfSixaxisProfiles[i+1])
IndexError: list index out of range

Any ideas on what's going wrong? I really like this program; I just need to customize my settings. Anyway, let me know how I can fix that.

Thanks! And keep up the good work!

robertneville777

Probably an error ocurred when adding a new profile.

Open QtSixA, in the menu "Settings" -> "Advanced" -> "Restore Sixaxis Profiles".
That will fix it

---

### Post by n3IVI0 on 2009-12-19
I am using qtsixa on a PS3 running xubuntu 9.10. The Sixaxis controllers sync and function perfectly. One question however. Is it possible to pair and control multiple controllers, like to play games in MAME (arcade emulator)? I was mapping the controllers to specific keyboard inputs, and matching that up with MAME, which was working, but only for one controller. I had also tried creating a Profile for each controller, and binding this to each controllers bluetooth mac, but again, it will only map one profile. How can I have at least 2 controllers, functioning with sdlmame/gmameui as joysticks?

---

### Post by n3IVI0 on 2009-12-19
My bad. Figured it out.

---

### Post by robertneville777 on 2009-12-21
> **falkTX said:**
> Probably an error ocurred when adding a new profile.

Open QtSixA, in the menu "Settings" -> "Advanced" -> "Restore Sixaxis Profiles".
That will fix it

Hey thanks man, its working again! You da man!

---

### Post by falkTX on 2009-12-21
**Update:**
Translations are coming soon!

I will translate QtSixA to portuguese, if you want to help translations, reply!

---

### Post by mkbrown69 on 2009-12-21
Hi Folks!
 
I'm having some problems with getting Sixad running with my existing 9.04 HTPC system. I can't presently upgrade due to a MythTV dependency on 0.21 for now, but I'm hoping to get two DualShock3 controllers working for SuperTuxKart and etracer for my kids
 
I start up sixad and connect a DS3 controller, and I get a never-ending stream of 
sixad-debug[]: non-Sixaxis packet received and ignored
 
Here's the output from the start:
 
root@freevo:/home/freevo# sixad
WARNING: All config files need .conf: /etc/modprobe.d/oss-compat, it will be ign
ored in a future release.
sixad settings:
Enable LEDs: 1
js# as LED #: 1
Start LED #: 1
LED # increase: 1
LED animation: 1
Buttons: 1
Sens. buttons: 1
Axis: 1
Accelerometers: 1
Acceleration: 0
Speed: 0
Position: 0
Rumble: 0
Debug: 1
sixad[32716]: sixad started, press the PS button now
sixad[378]: Connected PLAYSTATION(R)3 Controller (00:24:33:3D:9B:40)
sixad-debug[378]: debug mode started
sixad-debug[378]: No previous js# found, setting LED # to 1
sixad-debug[378]: non-Sixaxis packet received and ignored
sixad-debug[378]: non-Sixaxis packet received and ignored
sixad-debug[378]: non-Sixaxis packet received and ignored
sixad-debug[378]: non-Sixaxis packet received and ignored
sixad-debug[378]: non-Sixaxis packet received and ignored
 
root@freevo:/home/freevo# uname -a
Linux freevo 2.6.28-15-generic #52-Ubuntu SMP Wed Sep 9 10:48:52 UTC 2009 x86_64 GNU/Linux
 
root@freevo:/home/freevo# dpkg -l sixad
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Inst/Cfg-files/Unpacked/Failed-cfg/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Hold/Reinst-required/X=both-problems (Status,Err: uppercase=bad)
||/ Name Version Description
+++-==============-==============-============================================
ii sixad 1.1.1-falktx2 [Qt]SixA Daemon
 
root@freevo:/usr/src# dpkg -l libbluetooth3
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Inst/Cfg-files/Unpacked/Failed-cfg/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Hold/Reinst-required/X=both-problems (Status,Err: uppercase=bad)
||/ Name Version Description
+++-==============-==============-============================================
ii libbluetooth3 4.32-0ubuntu4. Library to use the BlueZ Linux Bluetooth sta
 
lsusb -v
Bus 002 Device 010: ID 1131:1001 Integrated System Solution Corp. KY-BT100 Bluetooth Adapter (the one with the MAC address of all 1's)
 
root@freevo:/usr/src# hcitool dev
Devices:
hci0 11:11:11:11:11:11
 
Controllers originally paired using sixpair via usb.
 
Would a newer kernel/uniput help? Other dependencies need to be upgraded?
 
Thanks in advance for any help!
 
/Mike
 
EDIT: Of course, the day after having asked for help is when I figured it out.  For the record and for anyone else experiencing similar problems, it was the bluetooth adapter.  I bought a new one and swapped them, and it worked fine.  The old one would pair and bring up the connection, but was obviously mangling the data from the DS3 controller.
 
Hope that helps!
 
/Mike

---

### Post by pkkid on 2009-12-23
Hello,

This is is great and hooks up the SixAxis without any hassle.  However, I am curious to learn more about the force connection feature.  I can only get this to work when I force a connection.

The problem is that I want to use my PC as a middle man to have my SixAxis send commands to my NXT (Lego Mindstorm).  This means I need both the NXT and the SixAxis to be connected through Bluetooth.  I believe when you force a connection, all other bluetooth devices cannot be connected.

Is there anything I can do to get both to be connected?

---

### Post by falkTX on 2009-12-28
> **mkbrown69 said:**
> Hi Folks!
*(...)*
EDIT: Of course, the day after having asked for help is when I figured it out.  For the record and for anyone else experiencing similar problems, it was the bluetooth adapter.  I bought a new one and swapped them, and it worked fine.  The old one would pair and bring up the connection, but was obviously mangling the data from the DS3 controller.
 
Hope that helps!
 
/Mike

I guess that was because the bluetooth dongle was too old (Sixaxis needs one that support v2.0 or higher).

I'm glad you figured it out

---

### Post by falkTX on 2009-12-28
> **pkkid said:**
> Hello,

This is is great and hooks up the SixAxis without any hassle.  However, I am curious to learn more about the force connection feature.  I can only get this to work when I force a connection.

The problem is that I want to use my PC as a middle man to have my SixAxis send commands to my NXT (Lego Mindstorm).  This means I need both the NXT and the SixAxis to be connected through Bluetooth.  I believe when you force a connection, all other bluetooth devices cannot be connected.

Is there anything I can do to get both to be connected?

The "Force connection" option will stop the normal bluetooth and start **/sbin/hcid**, which makes the normal bluetooth unusable (can't load).
This is needed because having 2 bluetooth apps running at the same time is not possible.

However, you can force the the connection, connect the sixaxis, and then restore bluetooth. Use QtSixA menus for that, if they don't work try (after forcing connection and Sixaxis connected):
```
sudo pkill -KILL hcid
sudo killall hcid
sudo /etc/init.d/bluetooth start

```
That should do it

---

### Post by sopha33 on 2009-12-31
So I finally got this installed and it tells me that no Bluetooth dongles are detected. I am using ubuntu 9.10 on my ps3. Is that the reason why it wont work? I thought it would use the bluetooth that is built into the ps3. Am I wrong? Please help.

Edit: Turns out I tried everything but restarting the system. Works perfectly now. Sorry I ever doubted you :)

---

### Post by falkTX on 2010-01-01
> **sopha33 said:**
> So I finally got this installed and it tells me that no Bluetooth dongles are detected. I am using ubuntu 9.10 on my ps3. Is that the reason why it wont work? I thought it would use the bluetooth that is built into the ps3. Am I wrong? Please help.

Edit: Turns out I tried everything but restarting the system. Works perfectly now. Sorry I ever doubted you :)

No prob.

But I'm still looking for translators for QtSixA...

---

### Post by falkTX on 2010-01-07
**Update:** v1.2.0 Beta is released!

*Changelog:*
* Started working on translations (contact me if you want to help)
* Fixed wrong Accelerometer #4 value in sixad-raw
* Pre-compiled stuff are no longer needed [hcid and libbluetooth2]
(hcid is compiled along with sixad)
* Running "sixad" in a terminal with no arguments shows some info instead of just starting server
* Added new stuff to Makefile, which can make sixad installed manually
* Other small changes and code clean-up
* QtSixA is now also available for Ubuntu Lucid (ppa:falk-t-j/qtsixa)


Because this release is Beta, it will not hit the repos.
Instead, download deb packages at this link:
[http://sourceforge.net/projects/qtsixa/files/QtSixA%201.2.0%20Beta%201/QtSixA_1.2.0%7Ebeta1_DEB.zip/download](http://sourceforge.net/projects/qtsixa/files/QtSixA%201.2.0%20Beta%201/QtSixA_1.2.0%7Ebeta1_DEB.zip/download)

Please test out if it all works for you.

QtSixA is now able to use translations. Currently only "portuguese" language is translated (by me).
If you want to help translate, please contact me.

---

### Post by MatthewJohn on 2010-01-12
I am trying to use my ps3 controller to navigate xbmc, I have it working with qtsixa but i am getting some weird behavior, for example when pressing left or right it goes over two times as if I pressed it twice. And sometimes it will just go crazy, buttons and menus will be opened in a loop making it so I have to kill the process.

I am using:
ubuntu 9.10
xbmc 9.11
I tried the version of qtsixa that you posted in the guide and also 1.20 beta both have the same behavior.

If you know how to fix this or have any tips on how to get this to work with xbmc please let me know

thank you.

---

### Post by falkTX on 2010-01-13
> **MatthewJohn said:**
> I am trying to use my ps3 controller to navigate xbmc, I have it working with qtsixa but i am getting some weird behavior, for example when pressing left or right it goes over two times as if I pressed it twice. And sometimes it will just go crazy, buttons and menus will be opened in a loop making it so I have to kill the process.

I am using:
ubuntu 9.10
xbmc 9.11
I tried the version of qtsixa that you posted in the guide and also 1.20 beta both have the same behavior.

If you know how to fix this or have any tips on how to get this to work with xbmc please let me know

thank you.

From what I remember, XBMC has built-in support for the Sixaxis, so if you have 1 connected, it will work right away.

Make sure _you're not using Sixaxis profiles_. That might do the job

---

### Post by falkTX on 2010-01-13
**Update:** v1.2.0 RC1 is released!

Changelog:
> * Finished strings for translators
* Finished pt_PT translation
* Make sure translations don't make QtSixA crash
* Started GUI code port to C++ (only for v2.0)
* Updated manual, and added translation section 


A small how-to translate QtSixA is now in the manual.
I'll wait until 30 January for translations, then I'll release the final version

---

### Post by Xeijin on 2010-01-13
This looks fantastic, my only problem is I'm running a minimal install as this is my dedicated XBMC box, but I'd like to use the PS3 controller for navigation. Is there any way to Make QtSixa run on the commandline or otherwise any other way to make this work without a window manager? Thanks in Advance.

---

### Post by falkTX on 2010-01-14
> **Xeijin said:**
> This looks fantastic, my only problem is I'm running a minimal install as this is my dedicated XBMC box, but I'd like to use the PS3 controller for navigation. Is there any way to Make QtSixa run on the commandline or otherwise any other way to make this work without a window manager? Thanks in Advance.

Hmm... QtSixA is not needed for connecting a Sixaxis. And to change settings you can edit the file "/etc/default/sixad".
But you won't be able to change profiles without using the GUI.
However, QtSixA creates a systray icon per default. Just left-click on it to hide the main interface. You can still disconnect devices and launch the settings anytime.

---

### Post by Xeijin on 2010-01-14
> **falkTX said:**
> Hmm... QtSixA is not needed for connecting a Sixaxis. And to change settings you can edit the file "/etc/default/sixad".
But you won't be able to change profiles without using the GUI.
However, QtSixA creates a systray icon per default. Just left-click on it to hide the main interface. You can still disconnect devices and launch the settings anytime.

Thanks for your reply. I won't be needing to switch profiles as it'll be used just for XBMC, which has its own button mapping for the Sixaxis. How do I get the Sixaxis to connect? I tried running sixad from terminal, it asks me to press the PS button but it doesn't seem to connect. Will I need to run sixpair first?

---

### Post by falkTX on 2010-01-14
> **Xeijin said:**
> Thanks for your reply. I won't be needing to switch profiles as it'll be used just for XBMC, which has its own button mapping for the Sixaxis. How do I get the Sixaxis to connect? I tried running sixad from terminal, it asks me to press the PS button but it doesn't seem to connect. Will I need to run sixpair first?

Yes, you'll need to pair it first.
Just connect both the bluetooth dongle and the Sixaxis over USB, and launch the menu in QtSixA for that.

Then you can remove the Sixaxis from USB and press the PS button to connect.
If it still refuses to connect you have a force option in the menu.

QtSixA also has a small manual, you should read it too (menu Help -> Manual)

---

### Post by Xeijin on 2010-01-14
> **falkTX said:**
> Yes, you'll need to pair it first.
Just connect both the bluetooth dongle and the Sixaxis over USB, and launch the menu in QtSixA for that.

Then you can remove the Sixaxis from USB and press the PS button to connect.
If it still refuses to connect you have a force option in the menu.

QtSixA also has a small manual, you should read it too (menu Help -> Manual)

Thanks, turns out I just needed a reboot controller is now connecting :)

I would love to read the manual but I have *no* window manager installed so I cannot use any GUI applications at all. I kept it this way because the box is essentially just meant to boot straight into XBMC and I prefer to do things over the command line.

One quick question, is there any way to keep the controller connected even after a reboot? If not, would you be able to tell me how to get sixad to startup automatically on boot so I can just hit the PS button to connect?

Thanks for all your help.

---

### Post by falkTX on 2010-01-14
> **Xeijin said:**
> Thanks, turns out I just needed a reboot controller is now connecting :)

I would love to read the manual but I have *no* window manager installed so I cannot use any GUI applications at all. I kept it this way because the box is essentially just meant to boot straight into XBMC and I prefer to do things over the command line.

One quick question, is there any way to keep the controller connected even after a reboot? If not, would you be able to tell me how to get sixad to startup automatically on boot so I can just hit the PS button to connect?

Thanks for all your help.

The Sixaxis should connect without any user interaction (it uses udev rules, so sixad is auto-started when needed).

But sometimes this doesn't happen. So there's an option in the menu "Configure Sixaxis" -> Advanced -> sixad at boot.
But notice that usual bluetooth stuff (mouse/keyboards/etc) will not connect in this mode

---

### Post by Xeijin on 2010-01-14
> **falkTX said:**
> The Sixaxis should connect without any user interaction (it uses udev rules, so sixad is auto-started when needed).

But sometimes this doesn't happen. So there's an option in the menu "Configure Sixaxis" -> Advanced -> sixad at boot.
But notice that usual bluetooth stuff (mouse/keyboards/etc) will not connect in this mode

I'm guessing the udev rules don't apply to me since I'm not running it with QtSixa? Unfortunately I can't do the "Configure Sixaxis -> Advanced -> sixad at boot" as I'm not running a window manager. Would I be able to manually do this with the CLI?

---

### Post by falkTX on 2010-01-14
> **Xeijin said:**
> I'm guessing the udev rules don't apply to me since I'm not running it with QtSixa? Unfortunately I can't do the "Configure Sixaxis -> Advanced -> sixad at boot" as I'm not running a window manager. Would I be able to manually do this with the CLI?

This specific option yes.
Run:
```
sudo sixad --boot-yes

```

To revert:
```
sudo sixad --boot-no
```


For help (only with 1.2.0) run:
```
sixad --help
```

---

### Post by Xeijin on 2010-01-14
> **falkTX said:**
> This specific option yes.
Run:
```
sudo sixad --boot-yes

```To revert:
```
sudo sixad --boot-no
```
For help (only with 1.2.0) run:
```
sixad --help
```

Fantastic. Works flawlessly now, thank you so much! Only thing I've got to figure out now is how to get it working with XBMC! :P

---

### Post by fummo on 2010-01-19
Great work FalkTX, this is great. Thank you very much :D:D:D:D.

---

### Post by falkTX on 2010-01-20
Good news!

QtSixA does now build on older Ubuntu PPAs (Jaunty & Intrepid), so users will be able to pass the error on my other repo.
It also ensures that it works correctly, since the binaries are compiled with the same GCC/libc/etc as the Ubuntu version installed.

QtSixA v1.2.0 will be available soon (before the end of the month)

---

### Post by Gazaaa on 2010-01-24
Thanks for the fantistic app FalkTX.  From reading this forum, I've managed to get it downloaded, installed, paired and working!  However, I do have one question that I hope you can help me with.  I'm running Ubuntu 9.10 through a PS3 on a SDTV.  Because of this the windows often expand off the bottom of the screen and i can't select the 'apply', 'cancel' etc buttons, so i rely on the Alt + grab method.  Now i'm wanting to use my sixaxis without needing to have the keyboard or mouse attached.  I see that in the Gnome profile there is a Alt option, but when i try using the mapped 'alt' + 'left mouse' + direction on the sixaxis I can't move the window.   Would there be a way to map the 'grab' function to one of the buttons?  Any suggestions? 

Thanks

---

### Post by falkTX on 2010-01-24
> **Gazaaa said:**
> I see that in the Gnome profile there is a Alt option, but when i try using the mapped 'alt' + 'left mouse' + direction on the sixaxis I can't move the window.   Would there be a way to map the 'grab' function to one of the buttons?  Any suggestions?

I did look for it, but it doesn't seems to be possible. The 'Alt', 'Ctrl' and 'Meta' keys don't seem to work very well when combined with other keys.

But you can try making your own profile, change to whatever you need and check if it works.
If it works, please tell me.
I never got a Compiz effect profile done because 'Alt' + 'Ctrl' + left/right never worked too

---

### Post by falkTX on 2010-01-27
**Update:** QtSixA v1.2.0 is released!

Most important changes since v1.1.1:
> - Fixed sixad-raw accelerometer #4 always at 32767
- Re-arranged "Configure Sixaxis" dialog
- Translations are now possible
- Don't crash if list of profiles is not present
- Warn user when using < 2.0 bluetooth dongle (Sixaxis incompatible)
- Pre-compiled stuff are no longer needed
- Running "sixad" in a terminal with no arguments shows some info instead of just starting server
- Added useful docs to the source tree
- Added Makefiles to easier install

QtSixA is now also available for Lucid, Karmic, Jaunty and Intrepid.
Check [https://launchpad.net/~falk-t-j/+archive/qtsixa/](https://launchpad.net/~falk-t-j/+archive/qtsixa/) for details on how to install

PS3 users still need the untrusted repo. Also v1.2.0 packages for PowerPC/PS3 are not yet available. They will come soon


Enjoy and report any bugs you found

---

### Post by ashokgm on 2010-01-27
[http://linux-solution-for-us.blogspot.com/](http://linux-solution-for-us.blogspot.com/)

---

### Post by falkTX on 2010-01-27
> **ashokgm said:**
> [http://linux-solution-for-us.blogspot.com/](http://linux-solution-for-us.blogspot.com/)

?

---

### Post by Jonyjack on 2010-02-08
It has been two days since I fight with bluez between the versions 3.xx and 4.xx and I finally find your comment. QtSixA works very well, I was able to calibrate my joystick.

However, the axes 4, 5 and 6 seem to be axes for the detection of movements. Here is what jstest gives me: 

[IMG]http://jonyjack38.free.fr/jstest.png[/IMG]

The three axes being never equal to 0, I cannot use the Sixaxis in games, because when I try to configure keys, axes are assigned. If somebody knows how to deactivate them it would be nice.

---

### Post by falkTX on 2010-02-09
> **Jonyjack said:**
> It has been two days since I fight with bluez between the versions 3.xx and 4.xx and I finally find your comment. QtSixA works very well, I was able to calibrate my joystick.

However, the axes 4, 5 and 6 seem to be axes for the detection of movements. Here is what jstest gives me: 

[IMG]http://jonyjack38.free.fr/jstest.png[/IMG]

The three axes being never equal to 0, I cannot use the Sixaxis in games, because when I try to configure keys, axes are assigned. If somebody knows how to deactivate them it would be nice.

This was my first concern when I coded the accelerometers (axis 4-7).
You can choose what events to enable in QtSixA -> "Configure Sixaxis".
Just disable the accelerometers, click apply and re-connect.

Enjoy!

---

### Post by Jonyjack on 2010-02-09
Woaw I didn't see the Settings menu.
Well, now it's definitely wonderful. :D

Also, it's great to use L3/R3 to enable the mouse mode.

I just want to know if it's normal that the Signal Quality is always about 5%? Anyway, it's working well.
And last one: Can I change the joystick sensitive for the mouse mode? Because it's too fast.


And again, thanks a lot. ;)

---

### Post by falkTX on 2010-02-09
> **Jonyjack said:**
> Woaw I didn't see the Settings menu.
Well, now it's definitely wonderful. :D

Also, it's great to use L3/R3 to enable the mouse mode.

I just want to know if it's normal that the Signal Quality is always about 5%? Anyway, it's working well.
And last one: Can I change the joystick sensitive for the mouse mode? Because it's too fast.


And again, thanks a lot. ;)

I usually gets 90-100% signal quality, but what matters is that it works.
You can change the sensitivity of the mouse, if you create a new profile.

Check those in "/usr/share/qtsixa/sixaxis-profiles" and edit them as you need.

---

### Post by Monzerelli on 2010-02-09
I'm new so I don't understand....I'm not sure how the application is installed. Quipeace says to double click on "-bin" file....but doesn't explain how to install...please help me, thank you.

---

### Post by Jonyjack on 2010-02-10
> **falkTX said:**
> I usually gets 90-100% signal quality, but what matters is that it works.
You can change the sensitivity of the mouse, if you create a new profile.

Check those in "/usr/share/qtsixa/sixaxis-profiles" and edit them as you need.
Because I want to use the option which disconnect the pad if the signal quality is low. Anyway, I can do without it.
How can I create a new profile? (Do I have to modify an existing one like sixa-gnome.fdi? If yes, do I have to change the value between '+' and 'x'? "mode=relative axis=+2x")

> **Monzerelli said:**
> I'm new so I don't understand....I'm not sure how the application is installed. Quipeace says to double click on "-bin" file....but doesn't explain how to install...please help me, thank you.
If you double click on -bin file, you will see a window with a button at the top right corner: "Install". Click on it and it will install itself automatically. Do the same with the other .deb file.

---

### Post by falkTX on 2010-02-10
> **Jonyjack said:**
> Because I want to use the option which disconnect the pad if the signal quality is low. Anyway, I can do without it.
How can I create a new profile? (Do I have to modify an existing one like sixa-gnome.fdi? If yes, do I have to change the value between '+' and 'x'? "mode=relative axis=+2x")

You're right changing that value "+2x" and "+2y" will do the trick.
You can copy the profile, modify it, then on the Sixaxis profiles you can add it (so you can have both the original and the modified).

Of course you can just modify the original file, that works too (but the file will be replaced when QtSixA is updated)

---

### Post by Jonyjack on 2010-02-10
Wonderful :o

Thank you very much for your support :)

I've finished with my questions x)


PS: Did you make a mistake in the topic title? Connect Sixaxis to Ubuntu **trough** (through) bluetooth mode
Ubuntu trough oO :mrgreen:

---

### Post by Chrigi on 2010-02-11
Hello

I just installed Ubuntu 9.10 on my PS3 and the next step would have been to enable Sixaxis support through QtSixA. So I added the two corresponding repositories mentioned in the first post but I can't install version 1.2 of QtSixA as it depends on sixad which is only available in version 1.1.1 and not the required minimum of 1.2.
Did I add the wrong repos? Do I have to get sixad elsewhere or do I just have to wait a bit until the new sixad will be released or do I have to do something completely different?

Thank you

---

### Post by falkTX on 2010-02-11
> **Chrigi said:**
> Hello

I just installed Ubuntu 9.10 on my PS3 and the next step would have been to enable Sixaxis support through QtSixA. So I added the two corresponding repositories mentioned in the first post but I can't install version 1.2 of QtSixA as it depends on sixad which is only available in version 1.1.1 and not the required minimum of 1.2.
Did I add the wrong repos? Do I have to get sixad elsewhere or do I just have to wait a bit until the new sixad will be released or do I have to do something completely different?

Thank you

There are 2 repositories.
1 - untrusted repo with builds for 32bit, 64bit and PPC (PS3)
2 - Ubuntu PPA, builds only for 32bit and 64bit.

I wasn't able to compile v1.2.0 for PPC (Lucid errors), but someone did it on Karmic. Here's the link:
[http://launchpadlibrarian.net/38873633/qtsixa_1.2.0-0build.tar.gz](http://launchpadlibrarian.net/38873633/qtsixa_1.2.0-0build.tar.gz)
Install sixad first then qtsixa.

---

### Post by KC2LBF on 2010-02-16
Okay I am new to this and have read bits and pieces of this thread.  I was able to get my PS3 up and running with Ubuntu 9.10 karmic.  I have also done so with my IBM T40p laptop.  I have Qtsixa 1.2 on both.  I was able to get sixaxis controller recognized on both and working on the PS3 but not the T40p(thinking that it is because the internal dongle is not a 2.0).  I was able to get my bluetooth keyboard recognized on both and working on the T40p but not the PS3.  So my question is why would the keyboard not work with the PS3?  Could it be that the PS3 dongle is 2.0? If so does anyone have a 2.0 working on their PC?  The other thought is this is PPC versus PC 32bit.  Trying to get all my thoughts out there and any help or ideas to try would be appreciated.  I have browsed other threads that have used HIDD and/or disabled xserver-xorg-input-synaptic.  Any thoughts on this?  Thanks for any support.

---

### Post by falkTX on 2010-02-22
> **KC2LBF said:**
> Okay I am new to this and have read bits and pieces of this thread.  I was able to get my PS3 up and running with Ubuntu 9.10 karmic.  I have also done so with my IBM T40p laptop.  I have Qtsixa 1.2 on both.  I was able to get sixaxis controller recognized on both and working on the PS3 but not the T40p(thinking that it is because the internal dongle is not a 2.0).  I was able to get my bluetooth keyboard recognized on both and working on the T40p but not the PS3.  So my question is why would the keyboard not work with the PS3?  Could it be that the PS3 dongle is 2.0? If so does anyone have a 2.0 working on their PC?  The other thought is this is PPC versus PC 32bit.  Trying to get all my thoughts out there and any help or ideas to try would be appreciated.  I have browsed other threads that have used HIDD and/or disabled xserver-xorg-input-synaptic.  Any thoughts on this?  Thanks for any support.

You should get rid of 'xserver-xorg-input-synaptic' when using a PS3 (known ubuntu bug).
That keeps you from using Sixaxis profiles in the PS3 (and maybe the keypad too).
I don't have a PS3 so I can't test this myself.

---

### Post by falkTX on 2010-02-22
QtSixA v1.2.1 released!

Changelog:
>   * Allow only single instance of QtSixA to run (LP: #518350)
  * Fix Sixaxis settings window too small
  * Start fixing 'Adding new profile works once out of a hundred times'
    (LP: #518105)


NOTE TO ALL PS3 USERS:
I no longer keep the PS3 repo (only PPA now).
If you're using a PS3, delete the QtSixA repo from your Software Sources.
Download the updated DEBs here: [https://sourceforge.net/projects/qtsixa/files/QtSixA%201.2.1/QtSixA-1.2.1-DEBs.zip/download](https://sourceforge.net/projects/qtsixa/files/QtSixA%201.2.1/QtSixA-1.2.1-DEBs.zip/download)

---

### Post by KC2LBF on 2010-02-22
Well from what I have tried it did not seem to fix the issue.  There could be something I am doing wrong or different that could be causing this.  But if I get it figured out, I will def make a note of it and pass the information accordingly through here.

> **falkTX said:**
> You should get rid of 'xserver-xorg-input-synaptic' when using a PS3 (known ubuntu bug).
That keeps you from using Sixaxis profiles in the PS3 (and maybe the keypad too).
I don't have a PS3 so I can't test this myself.

---

### Post by LilDeamon on 2010-03-15
I am running PS3 Ubuntu 9.10 and when installing the sixad 1.2.1 package i get the following error:

[[IMG]http://img704.imageshack.us/img704/7840/screenshotnu.th.png[/IMG]](http://img704.imageshack.us/i/screenshotnu.png/)

Because of this i then cant install QtSixA.

Thanks, Jamie

---

### Post by linuxcreeper on 2010-03-20
> **falkTX said:**
> QtSixA v1.2.1 released!

Changelog:



NOTE TO ALL PS3 USERS:
I no longer keep the PS3 repo (only PPA now).
If you're using a PS3, delete the QtSixA repo from your Software Sources.
Download the updated DEBs here: [https://sourceforge.net/projects/qtsixa/files/QtSixA%201.2.1/QtSixA-1.2.1-DEBs.zip/download](https://sourceforge.net/projects/qtsixa/files/QtSixA%201.2.1/QtSixA-1.2.1-DEBs.zip/download)


Hello, sorry if this has been answered, but a quick search didn't turn up any results. When I try to install the the DEBs on Ubuntu 9.04 for PS3, I get this:

"Error: Dependency is not satisfiable: libbluetooth3 (>= 4.40)"

I'm probably doing something wrong here, since I don't have a lot of experience in using Linux on a PS3, so any help would be much appreciated.

---

### Post by falkTX on 2010-03-20
> **LilDeamon said:**
> I am running PS3 Ubuntu 9.10 and when installing the sixad 1.2.1 package i get the following error:

[[IMG]http://img704.imageshack.us/img704/7840/screenshotnu.th.png[/IMG]](http://img704.imageshack.us/i/screenshotnu.png/)

Because of this i then cant install QtSixA.

Thanks, Jamie

You're using my older files! (from sixaxis-gui... 2 years ago)

Use Synaptic to remove bluez-sixaxis-bin, and any other package with "sixaxis" in the name.
Then QtSixA will install fine.

---

### Post by falkTX on 2010-03-20
> **linuxcreeper said:**
> Hello, sorry if this has been answered, but a quick search didn't turn up any results. When I try to install the the DEBs on Ubuntu 9.04 for PS3, I get this:

"Error: Dependency is not satisfiable: libbluetooth3 (>= 4.40)"

I'm probably doing something wrong here, since I don't have a lot of experience in using Linux on a PS3, so any help would be much appreciated.

First of all, you should install Karmic (ubuntu 9.10) (or you won't get accelerometer support and rumble, when it's supported).
There are also some other issues with 9.04, so it's really recommended that you upgrade.

For Jaunty (9.04), you need to install this first:
[http://launchpadlibrarian.net/32410029/libbluetooth3_4.51-0ubuntu2_powerpc.deb](http://launchpadlibrarian.net/32410029/libbluetooth3_4.51-0ubuntu2_powerpc.deb)

---

### Post by linuxcreeper on 2010-03-20
> **falkTX said:**
> First of all, you should install Karmic (ubuntu 9.10) (or you won't get accelerometer support and rumble, when it's supported).
There are also some other issues with 9.04, so it's really recommended that you upgrade.

For Jaunty (9.04), you need to install this first:
[http://launchpadlibrarian.net/32410029/libbluetooth3_4.51-0ubuntu2_powerpc.deb](http://launchpadlibrarian.net/32410029/libbluetooth3_4.51-0ubuntu2_powerpc.deb)


Thanks, that worked great! I'll try to convinced my friend to upgrade to 9.10, as it's his system. He hasn't wanted to though since we finally got a bunch of stuff working for it, and he doesn't want to start over again. As long as this works for now though, he should be happy with it.

---

### Post by linuxcreeper on 2010-03-22
Alright, now I've upgraded to Karmic for the PS3, and the controller works, but when I try to set it up in mednafen, the tilt sensors in the controller automatically sets all the controls to itself. I want to set the controller up to work like a NES controller, with keypad on the keypad, and A and B set to O and X, but the tilt sensor wont let me. Any way to turn that off?

---

### Post by falkTX on 2010-03-23
> **linuxcreeper said:**
> Alright, now I've upgraded to Karmic for the PS3, and the controller works, but when I try to set it up in mednafen, the tilt sensors in the controller automatically sets all the controls to itself. I want to set the controller up to work like a NES controller, with keypad on the keypad, and A and B set to O and X, but the tilt sensor wont let me. Any way to turn that off?

Yes, open QtSixA, then in the menu "Settings" -> "Configure Sixaxis". In the "input events" section, disable what you don't want.
Disconnect and Connect the Sixaxis again to apply those settings.

---

### Post by KhaaL on 2010-03-24
Just a quick question, is it possible to use two sixaxis at the same time on the PC with this?

---

### Post by falkTX on 2010-03-24
> **KhaaL said:**
> Just a quick question, is it possible to use two sixaxis at the same time on the PC with this?

Yes.
I tested with 4, all working Ok.

---

### Post by originalg on 2010-03-28
First I'd like to thank everyone who has helped create this software. I've got 2 sixaxis controllers successfully connected and working through bluetooth, and this has me very excited! However, I'm using the profiles option to have my controllers emulate keyboard presses and when I try to apply an override for the second controller I get the following error message:

"The selected profile is not on the list of profiles! QtSixA will quit now!"

Concerned that the profiles I had created and added might very well have been the problem, I went to settings-->advanced and clicked "Restore Sixaxis Profiles". I then chose to use the supplied "Fake Joystick" profile and attempted to override my second controller with the "Fake Joystick 2" profile. Unfortunately, I received the same error message as before.

I'm new here, and to Linux/Ubuntu, and did my best to search the form before posting, but did not see any posts relating to this issue. I have overcome a number of hurdles while setting up my new HTPC, but this time I'm truly stuck and could use some help.

---

### Post by keenanv on 2010-03-28
I installed the deb today (on my PS3) from your SF project but when I installed (PowerPC version) there's no GUI. Am I missing something?

using sixad in terminal works to start/stop the service but where is the GUI lol?

---

### Post by keenanv on 2010-03-29
Upon further investigation I made the mistake of installing "sixad", and not "qtSixA" lol :X

---

### Post by falkTX on 2010-03-29
> **keenanv said:**
> Upon further investigation I made the mistake of installing "sixad", and not "qtSixA" lol :X

You need to install sixad first, then QtSixA.
That was on the readme file...

---

### Post by gopher38 on 2010-03-30
Hi,

Looking for help on this.  I'm trying to get this running on a PS3 with Jaunty.  Just trying to use the SixAxis as a mouse and for MAME.  I know the first question will be, "Why Jaunty?".  Well, I'm familiar with Jaunty, so I tried that first.  Couldn't get it to work, so I went to Karmic, but I had more serious issues with the screen, sound, and other flaky behaviour, so I'm back to Jaunty.   Also, I know that this works at least on a laptop using Jaunty, because I got it to work on my HP Pavilion. Besides, I only want to use the SixAxis as a mouse, so I don't care about some of the new features.  So, I'm back to trying Jaunty on the PS3.  I believe that this combination will work, but if someone knows that it definitely will not work (like this falkTX, who seems to know everything), please give me a heads up.

Anyway, I'm on jaunty and I'm pretty sure that I read that you first have to install this:

libbluetooth3_4.51-0ubuntu2_powerpc.deb

So I downloaded and installed it with no problems.  I then downloaded this:

QtSixA-1.2.1-DEBs.zip

And installed this file:

sixad_1.2.1-0ubuntu0+karmic1_powerpc.deb

And then this:

qtsixa_1.2.1-0ubuntu0+karmic1_all.deb

I know that they both say "karmic" on them, but I believe that they are the right files.  They worked on my Pavilion with Jaunty anyway, and seemed to install correctly on the PS3.

So I thought I'd be OK, but I can't get the thing to work.  QtSixA sees the SixAxis (address listed in connected devices), both on bluetooth and through USB.  I can select the hidraw device, but when I hit apply, one of two things happens: a) it seems to work but I still don't see any reaction when I move the joysticks, or b) it gives me an error message that it can't start the sixad driver.  There aren't any lights on the sixaxis either.

So couple of questions to start.  Can anyone:

a) confirm that the sixaxis will work as a mouse on the PS3 with jaunty?

b) tell me if I'm using the correct packages?
       libbluetooth3_4.51-0ubuntu2_powerpc.deb
       sixad_1.2.1-0ubuntu0+karmic1_powerpc.deb
       qtsixa_1.2.1-0ubuntu0+karmic1_all.deb

c) give me any hints on what I might try next?

Muchos gracias.

---

### Post by gloarb on 2010-03-31
Hello,

I'm on karmic on PC :

Linux ubuntu 2.6.31-20-generic #58-Ubuntu SMP Fri Mar 12 05:23:09 UTC 2010 i686 GNU/Linux

QtSixa detect my ps3 controller, i can associate on bluetooth (blinking and after a while a single light on number 1), but controler do not works.

Signal quality is always 0% and Battery status 0/5.

I can see it on dmesg : 

[10979.083490] input: PLAYSTATION(R)3 Controller (00:24:34:66:18:99) as /devices/virtual/input/input19

I tried a jstest /dev/input/js0 but nothing. (this command works on usb mode).

Any idea?

Thanks.;)

---

### Post by falkTX on 2010-03-31
> **gopher38 said:**
> Hi,

Looking for help on this.  I'm trying to get this running on a PS3 with Jaunty.  Just trying to use the SixAxis as a mouse and for MAME.  I know the first question will be, "Why Jaunty?".  Well, I'm familiar with Jaunty, so I tried that first.  Couldn't get it to work, so I went to Karmic, but I had more serious issues with the screen, sound, and other flaky behaviour, so I'm back to Jaunty.   Also, I know that this works at least on a laptop using Jaunty, because I got it to work on my HP Pavilion. Besides, I only want to use the SixAxis as a mouse, so I don't care about some of the new features.  So, I'm back to trying Jaunty on the PS3.  I believe that this combination will work, but if someone knows that it definitely will not work (like this falkTX, who seems to know everything), please give me a heads up.

Anyway, I'm on jaunty and I'm pretty sure that I read that you first have to install this:

libbluetooth3_4.51-0ubuntu2_powerpc.deb

So I downloaded and installed it with no problems.  I then downloaded this:

QtSixA-1.2.1-DEBs.zip

And installed this file:

sixad_1.2.1-0ubuntu0+karmic1_powerpc.deb

And then this:

qtsixa_1.2.1-0ubuntu0+karmic1_all.deb

I know that they both say "karmic" on them, but I believe that they are the right files.  They worked on my Pavilion with Jaunty anyway, and seemed to install correctly on the PS3.

So I thought I'd be OK, but I can't get the thing to work.  QtSixA sees the SixAxis (address listed in connected devices), both on bluetooth and through USB.  I can select the hidraw device, but when I hit apply, one of two things happens: a) it seems to work but I still don't see any reaction when I move the joysticks, or b) it gives me an error message that it can't start the sixad driver.  There aren't any lights on the sixaxis either.

So couple of questions to start.  Can anyone:

a) confirm that the sixaxis will work as a mouse on the PS3 with jaunty?

b) tell me if I'm using the correct packages?
       libbluetooth3_4.51-0ubuntu2_powerpc.deb
       sixad_1.2.1-0ubuntu0+karmic1_powerpc.deb
       qtsixa_1.2.1-0ubuntu0+karmic1_all.deb

c) give me any hints on what I might try next?

Muchos gracias.


Hi!
First of all, "like this falkTX, who seems to know everything"... well, I developed QtSixA, so I think it's normal that I know how it works... ;)

Here's the answers
a)Yes, they will work.
b)Everything seems fine
c) Try this:
1-Disconnect all Sixaxis and use "Force Connection" in the menu.
2-run "sixad --start" from a terminal

Note that, when connecting trough bluetooth, you know it's working when 1 LED lights up (instead of all just flashing)

---

### Post by falkTX on 2010-03-31
> **gloarb said:**
> Hello,

I'm on karmic on PC :

Linux ubuntu 2.6.31-20-generic #58-Ubuntu SMP Fri Mar 12 05:23:09 UTC 2010 i686 GNU/Linux

QtSixa detect my ps3 controller, i can associate on bluetooth (blinking and after a while a single light on number 1), but controler do not works.

Signal quality is always 0% and Battery status 0/5.

I can see it on dmesg : 

[10979.083490] input: PLAYSTATION(R)3 Controller (00:24:34:66:18:99) as /devices/virtual/input/input19

I tried a jstest /dev/input/js0 but nothing. (this command works on usb mode).

Any idea?

Thanks.;)

Can you try to re-compile QtSixA ?

1 - get source code
2 - install packages "libbluetooth-dev libusb-dev libdbus-glib-1-dev libdbus-1-dev"
3 - open a terminal with "cd <where-you-extracted-(folder)>" and run: "debuild -rfakeroot"

It will then build 2 deb files (don't worry about the signature error).
Install these 2 deb files, reboot and please report if anything changes.


*Sorry that I don't have a PS3 to test these things...*

---

### Post by gopher38 on 2010-03-31
> **falkTX said:**
> Hi!
First of all, "like this falkTX, who seems to know everything"... well, I developed QtSixA, so I think it's normal that I know how it works... ;)

Here's the answers
a)Yes, they will work.
b)Everything seems fine
c) Try this:
1-Disconnect all Sixaxis and use "Force Connection" in the menu.
2-run "sixad --start" from a terminal

Note that, when connecting trough bluetooth, you know it's working when 1 LED lights up (instead of all just flashing)

Hi falkTX.  Very impressive work. I can't get much beyond "main() {"

Are you really in Portugal?  I was in Lisbon last year and loved it.  Beautiful city and I topped off every evening with some of that Ginjinha (sp?) liquor at a stand in the city center.  If you're there, you're a lucky guy.

Regarding qtsixa, first, thanks for confirming that people have made it work on the PS3 with Jaunty.  That is helpful.  This is what I've learned so far.  I think the order that you do things the first time is very important, and if you don't do it correctly, you can break it and not get it back.  For instance, when you confirmed that this would work on the PS3, I went to my Pavilion to try to repeat what I'd done there.  The SixAxis had been working perfectly on the Pavilion for several days.  I cleared the profiles, reset everything and then tried to connect again.  This time, I must have done a different order to things, because I was never able to get it to reconnect.  Furthermore, I started getting the same error about sixad not being able to start the driver.  I then removed both the qtsixa and sixad packets and re-installed them, but I then couldn't even start qtsixa (!!!).  When I started from the command line, I found out that the problem was that qtsixa was dying when it tried to create the .qtsixa directory which still existed from the first install.  I deleted it, and then qtsixa could start, but there were still profiles remaining from first install (still using Gnome as a profile).  Still couldn't get it to connect either.  Specifically, the step where you select hidraw2 and hit "apply" hangs, until you unplug the sixaxis, when it then gives you a "couldn't start driver" message.  I did a cntl-c one time from the command line and I think it might hang while trying to write something in /usr/share/qtsixa/qui/qtsixa.pyw. Not sure about that though.

Anyway, I've got to get back to work, but I'll keep experimenting.  Great work on this. I had it going and working great on one of my machines.  Like I said though, I think you have to do things in a precise order the first time you set it up, and if you break it, it's tough to get it back. I'm going to keep trying though.

---

### Post by gopher38 on 2010-03-31
Little more experimentation. 

On both my systems, when I try to apply the sixad driver to hidraw2, it hangs.  "ps -e | grep six" shows qtsixa and sixad-raw running.  If I kill the sixad-raw process, then I get the "The sixad driver could not start" message.  Same thing if I physically unplug the SixAxis; I get the message.  So this sixad-raw process is hanging on me for some reason.


Incidentally, I thought that maybe sixad should be running beforehand, so I manually started them before running qtsixa.  No difference. Same behavior.

falkTX, if I wanted to completely clean the slate and try again from the beginning (remembering that I DID have this working at one time), are there things I should delete in addition to .qtsixa and uninstalling qtsixa and sixad?  /usr/share/qtsixa  ??  Anything else?  Thanks.

---

### Post by gloarb on 2010-03-31
> **falkTX said:**
> Can you try to re-compile QtSixA ?

1 - get source code
2 - install packages "libbluetooth-dev libusb-dev libdbus-glib-1-dev libdbus-1-dev"
3 - open a terminal with "cd <where-you-extracted-(folder)>" and run: "debuild -rfakeroot"

It will then build 2 deb files (don't worry about the signature error).
Install these 2 deb files, reboot and please report if anything changes.


*Sorry that I don't have a PS3 to test these things...*

Read ps and ps2 first! :)

I successfull created and installed the 2 deb files, rebooted, and same thing.

Signal quality 0%, Battery 0/5 and controler do not control anything.

I still see it on "List of connected devices".

I am on a pc, not on a PS3.

Thanks!

ps: I tried on another PC (x64)(same bluetooth dongle)(ubuntu karmic x64)... Same thing. :(
ps2: I tried on another PC with another bluetooth (minipci), it works!!

So my bluetooth dongle isn't compatible. Weird, because it works with my wiimote.

here is macs address of my 2 incompatible dongles:
00:15:83:15:a2:36
00:15:83:15:a3:74

---

### Post by gopher38 on 2010-04-01
More experimentation.  Got it working again on my Pavilion.  Know what I had to do?  Reset the SixAxis using the pinhole on the back.  Did that and it connected right away.  I'll try on the PS3 tomorrow.  Ciao.

EDIT: yeah, got it working on PS3 too, using the legacy drivers.  Reseting the sixaxis was key for me whenever I ran into problems.

---

### Post by falkTX on 2010-04-01
Thanks guys for not giving up easily. I know my code it's not perfect, but I'm learning everyday how to be a better programmer.

For those who need sixad-raw, simply running:
```
sudo sixad-raw /dev/hidrawX
```*(Change "X" to the dev #)*
This will activate the sixad-raw driver without need to go trough the GUI.

Sorry that I forgot to say this, but on PS3/Jaunty you need to activate "Legacy USB driver" in QtSixA -> Sixaxis Settings. Karmic users don't need this.
You should also try to enable "UInput at boot" and reboot the system if it still doesn't work.


I'm now a little busy with another project ([http://kxstudio.sourceforge.net/](http://kxstudio.sourceforge.net/)), but I'll make some time to code QtSixA again.
My idea is to rewrite the code (maybe PyKDE?), and start working on Rumble too.


And thanks for all the people that has been donating!
I'll get a DualShock3 soon thanks to you guys!

---

### Post by The Thunder Chimp on 2010-04-05
> **falkTX said:**
> 
Sorry that I forgot to say this, but on PS3/Jaunty you need to activate "Legacy USB driver" in QtSixA -> Sixaxis Settings. Karmic users don't need this.

This is not related to QtSixa, but, speaking of Linux PS3, if you want to keep Other_OS and get online access, follow this link, it should aid you.

[http://ubuntuforums.org/showthread.php?t=1447304](http://ubuntuforums.org/showthread.php?t=1447304)

Hope it helps! (Will only work if you haven't updated to version 3.21)

---

### Post by e2b on 2010-04-17
Does someone know if it's possible to use a third-party wireless controller with a special usb dongle? Seems to be this one: [http://www.tinydeal.com/wireless-dual-shock-sixaxis-controller-for-ps3-gps3ct01-p-1650.html](http://www.tinydeal.com/wireless-dual-shock-sixaxis-controller-for-ps3-gps3ct01-p-1650.html)

---

### Post by aatu_kanifani on 2010-04-18
@e2b:

Hmm, it doesn't even state its manufacturer. But it seems it would be for PC usage also. I wonder if they have their own driver and software for Windows, then... Or maybe it's a generic controller, and thus doesn't work with same input/output calls as genuine Sixaxis or DS3. I think PS3 recognizes most of the generic PC pads, but Windows for one won't play well with Sixaxis without additional software.

Thus it may be it won't be compatible with QtSixA out-of-the-box. But if it's generic, it could work without it.

But all in all, the whole site seems a little shady. Have you already ordered and received the pad? Or do you have prior experience with them?
For example, the 7" netbook they have for sale for 98$ shows a picture of a netbook with what would appear to be Windows XP with classic interface, but in reality is WinCE 5.0 and with VERY low system specifications. Be careful...

---

### Post by falkTX on 2010-04-18
@e2b:

I have a similar joystick and it works.
It has a special usb device (uses some weird radio waves to connect to the joystick). Once you insert the usb thing, it will register a new joystick, just like with any other one. Then you turn on the joystick (a switch in the back) and it connects.
I need sixad-raw to make it work properly though (only 13 buttons are available when it should have 16, so sixad-raw fixes it).

Also consider what aatu_kanifani said.

But, from my experience, there's no joystick better than the original Sixaxis|DualShock3. It's not cheap, but it works fine (even after falling to the floor several times... :P)

---

### Post by e2b on 2010-04-20
Well, it's already here. I know it's not a store you buy good hardware but it was cheap and sometimes I do some risky purchases and use the PayPal protection later ... I'm going to do in this case, no Bluetooth like described.

I already recognized it's some proprietary thing: Neither using Bluetooth (some special USB dongle used) nor cable connection (only to recharge). The USB dongle acts like a wired connected Dualshock that does wireless on its own. Although the dongle will detect the wireless gamepad if it's switched on. The problem is the gamepad continues blinking and jstest shows no update (it should, shouldn't it?). Interestingly there are to blink modes.

```
dmesg
[ 1603.464057] usb 4-2: new full speed USB device using uhci_hcd and address 2
[ 1603.691258] usb 4-2: configuration #1 chosen from 1 choice
[ 1613.737298] /build/buildd/linux-2.6.31/drivers/hid/usbhid/hid-core.c: usb_submit_urb(ctrl) failed
[ 1613.737329] sony 0003:054C:0268.0002: timeout initializing reports
[ 1613.737516] input: Gasia Co.,Ltd PS(R) Gamepad as /devices/pci0000:00/0000:00:1d.2/usb4/4-2/4-2:1.0/input/input11
[ 1613.737809] sony 0003:054C:0268.0002: input,hiddev96,hidraw1: USB HID v1.11 Joystick [Gasia Co.,Ltd PS(R) Gamepad] on usb-0000:00:1d.2-2/input0
```

```
jstest /dev/input/js0 
Driver version is 2.1.0.
Joystick (Gasia Co.,Ltd PS(R) Gamepad) has 28 axes (X, Y, Z, Rz, (null), (null), (null), (null), (null), (null), (null), (null), (null), (null), (null), (null), (null), (null), (null), (null), (null), (null), (null), (null), (null), (null), (null), (null))
and 19 buttons (Trigger, ThumbBtn, ThumbBtn2, TopBtn, TopBtn2, PinkieBtn, BaseBtn, BaseBtn2, BaseBtn3, BaseBtn4, BaseBtn5, BaseBtn6, BtnDead, BtnA, BtnB, BtnC, BtnX, BtnY, BtnZ).
Testing ... (interrupt to exit)
Axes:  0:     0  1:     0  2:     0  3:     0  4:     0  5:     0  6:     0  7:     0  8:     0  9:     0 10:     0 11:     0 12:     0 13:     0 14:     0 15:     0 16:     0 17:     0 18:     0 19:     0 20:     0 21:     0 22:     0 23:     0 24:     0 25:     0 26:     0 27:     0 Buttons:  0:off  1:off  2:off  3:off  4:off  5:off  6:off  7:off  8:off  9:off 10:off 11:off 12:off 13:off 14:off
```

---

### Post by aatu_kanifani on 2010-04-20
Do you have a possibility to test it with a PS3 or Windows? Or both, with and without the dongle?

And do you mean the dongle recognizes itself as Dualshock (3?) in Ubuntu, even if the controller is off?

Not that any of those matter regarding the QtSixA. I'm just curious.

---

### Post by e2b on 2010-04-21
> **aatu_kanifani said:**
> Do you have a possibility to test it with a PS3 or Windows? Or both, with and without the dongle?
I have no PS3 but I've just tested with a Windows computer and got the same result: No direct wired connection, dongle is detected as HID game controller but pressed buttons aren't detected.

> **aatu_kanifani said:**
> And do you mean the dongle recognizes itself as Dualshock (3?) in Ubuntu, even if the controller is off?
Yes, this is dmesg after I've plugged in the USB dongle:
```
Apr 21 13:34:04: [ 4350.088055] usb 4-2: new full speed USB device using uhci_hcd and address 4
Apr 21 13:34:05: [ 4350.317270] usb 4-2: configuration #1 chosen from 1 choice
Apr 21 13:34:15: [ 4360.333320] sony 0003:054C:0268.0004: timeout initializing reports
Apr 21 13:34:15: [ 4360.333507] input: Gasia Co.,Ltd PS(R) Gamepad as /devices/pci0000:00/0000:00:1d.2/usb4/4-2/4-2:1.0/input/input13
Apr 21 13:34:15: [ 4360.333806] sony 0003:054C:0268.0004: input,hiddev96,hidraw1: USB HID v1.11 Joystick [Gasia Co.,Ltd PS(R) Gamepad] on usb-0000:00:1d.2-2/input0
```
Controller was switched off and switching it on didn't change anything.

---

### Post by aatu_kanifani on 2010-04-21
Hmm, that sounds odd indeed.

If Windows doesn't play well with it (and the package didn't include any drivers, I assume), then I'd say they didn't intend it to work with PC.

The wired third-party controllers for PS3 probably use some kind of proprietary detection/calls, otherwise they'd advertise them for both PS3 and PC. Your controller could be the same, they just artificially made it wireless.

But they are a no-name manufacturer, I just don't see why they didn't make it a generic gamepad. Well, I don't see why the more recognized brands don't use generic gamepads, either. And I know for a fact there are gamepads that work with both systems.

Well, just one thing to make sure: have you tried it with first turning on the controller and then plugging in the dongle? It's a far stretch it would change anything, but you could try anyway.

Other than that, I'd say return it. There's possibly even a two weeks' satisfaction guarantee of some sort. Hopefully.

PS. The best thing would be if you could try it out with a friend's PS3. To see if it works at all. There could simply be something wrong with the transmitter and/or receiver chips, etc. Well, that would also lead to returning it, though...

---

### Post by help_plz on 2010-04-21
hey guys I need some help.
I'm pretty much a noob to ubuntu and linux.(I've had experience with Windows XP mostly.)

When I try to run the installer files, I get an error saying it's either corrupt or I don't have permission.

I ran "sudo apt-get update && sudo apt-get install qtsixa" command and it said I don't have bluez sixaxis and that it couldn't find it.


I'm on 9.10 on my PS3.
I'm using a really old ball mouse and it's getting quite annoying.

---

### Post by e2b on 2010-04-22
> **aatu_kanifani said:**
> Well, just one thing to make sure: have you tried it with first turning on the controller and then plugging in the dongle? Of course.

> **help_plz said:**
> When I try to run the installer files, I get an error saying it's either corrupt or I don't have permission.
Simply download "QtSixA-1.2.1-DEBs.zip" from the [project page]("http://sourceforge.net/projects/qtsixa/files/"). Unzip and double-click on "sixad_1.2.1-0ubuntu0+karmic1_powerpc.deb". Then start the package installation. That's all, no terminal is needed.

---

### Post by help_plz on 2010-04-22
> **e2b said:**
> Simply download "QtSixA-1.2.1-DEBs.zip" from the [project page]("http://sourceforge.net/projects/qtsixa/files/"). Unzip and double-click on "sixad_1.2.1-0ubuntu0+karmic1_powerpc.deb". Then start the package installation. That's all, no terminal is needed.

I've just tried this just now and it didn't work. 
after I open the "sixad_1.2.1-0ubuntu0+karmic1_powerpc.deb" I get an error message that says 
"Could not opensixad_1.2.1-0ubuntu0+karmic1_powerpc.deb"
"The package might be corrupt or you are not allowed to open the file. Check the permissions of the file."

sorry if I wasn't clear before.

---

### Post by e2b on 2010-04-23
> **help_plz said:**
> "The package might be corrupt or you are not allowed to open the file. Check the permissions of the file."

If you know how to use a terminal you should try to navigate to the unzipped folder and run "sudo dpkg -i sixad_*_powerpc.deb". If this fails you will be able to read some error messages. An other question is: Are you allowed to install anything? Try installing something from the package repository. Maybe you are not in the necessary usergroup.

---

### Post by help_plz on 2010-04-26
> **e2b said:**
> If you know how to use a terminal you should try to navigate to the unzipped folder and run "sudo dpkg -i sixad_*_powerpc.deb". If this fails you will be able to read some error messages. An other question is: Are you allowed to install anything? Try installing something from the package repository. Maybe you are not in the necessary usergroup.

oh yes I can't seem to install other programs aswell.
what can I do to fix this?

---

### Post by falkTX on 2010-04-26
First you should try a disk check, not sure how to do it in the PS3, though.

Are you in the group admin and sudo?
```
groups
```

---

### Post by help_plz on 2010-04-28
uh yeah when I enter "groups" in the Terminal, after my username it has "adm dialout cdrom plugdev lpadmin admin sambashare".

is there some sort of System Restore feature maybe?

---

### Post by e2b on 2010-04-29
> **help_plz said:**
> "adm dialout cdrom plugdev lpadmin admin sambashare".

That should be ok. :confused:

---

### Post by falkTX on 2010-04-29
Then I don't know what your errors are all about...
I would recommend to reformat the system...
A new Ubuntu version is just coming out (10.04, Lucid Lynx), so...

---

### Post by help_plz on 2010-05-01
i reinstalled/reformatted, got the installer to work but had some trouble getting it function, then I had my internet connection keep cutting off, even after rebooting.

I'm just gonna update my PS3. :/ (remove Other OS feature so I can go on psn.)

thanks for the help anyway guys.

---

### Post by Occasionally Correct on 2010-05-06
Hello!

I've recently upgraded to Lucid (by way of clean installation) and I can't use my DualShock 3 anymore. It's apparently detected when I plug it into my computer (it's listed in qtsixa), but the device file /dev/input/js0 is never created. If it helps, here's the dmesg output:

```
[ 2998.024026] usb 7-1: new full speed USB device using uhci_hcd and address 7
[ 2998.247145] usb 7-1: configuration #1 chosen from 1 choice
[ 3013.261250] /build/buildd/linux-2.6.32/drivers/hid/usbhid/hid-core.c: usb_submit_urb(ctrl) failed
[ 3013.261265] sony 0003:054C:0268.0009: timeout initializing reports
[ 3013.261401] input: Sony PLAYSTATION(R)3 Controller as /devices/pci0000:00/0000:00:1d.1/usb7/7-1/7-1:1.0/input/input14
[ 3013.261670] sony 0003:054C:0268.0009: input,hiddev96,hidraw3: USB HID v1.11 Joystick [Sony PLAYSTATION(R)3 Controller] on usb-0000:00:1d.1-1/input0
[ 3018.261682] sony 0003:054C:0268.0009: can't set operational mode
[ 3018.284357] sony: probe of 0003:054C:0268.0009 failed with error -110
```When I try to pair it from the menu, it freezes for a few seconds and reports:

```
USB_REQ_GET_CONFIGURATION: Connection timed out
USB_REQ_SET_CONFIGURATION: Connection timed out
Current Bluetooth master: Setting master bd_addr to 00:1b:dc:00:44:3c
```...and when I pull the plug and turn the controller on again, it starts acting as a new mouse (even though that option isn't selected).

Any help would be very much appreciated.

---

### Post by falkTX on 2010-05-06
> **Occasionally Correct said:**
> Hello!

I've recently upgraded to Lucid (by way of clean installation) and I can't use my DualShock 3 anymore. It's apparently detected when I plug it into my computer (it's listed in qtsixa), but the device file /dev/input/js0 is never created. If it helps, here's the dmesg output:

```
[ 2998.024026] usb 7-1: new full speed USB device using uhci_hcd and address 7
[ 2998.247145] usb 7-1: configuration #1 chosen from 1 choice
[ 3013.261250] /build/buildd/linux-2.6.32/drivers/hid/usbhid/hid-core.c: usb_submit_urb(ctrl) failed
[ 3013.261265] sony 0003:054C:0268.0009: timeout initializing reports
[ 3013.261401] input: Sony PLAYSTATION(R)3 Controller as /devices/pci0000:00/0000:00:1d.1/usb7/7-1/7-1:1.0/input/input14
[ 3013.261670] sony 0003:054C:0268.0009: input,hiddev96,hidraw3: USB HID v1.11 Joystick [Sony PLAYSTATION(R)3 Controller] on usb-0000:00:1d.1-1/input0
[ 3018.261682] sony 0003:054C:0268.0009: can't set operational mode
[ 3018.284357] sony: probe of 0003:054C:0268.0009 failed with error -110
```When I try to pair it from the menu, it freezes for a few seconds and reports:

```
USB_REQ_GET_CONFIGURATION: Connection timed out
USB_REQ_SET_CONFIGURATION: Connection timed out
Current Bluetooth master: Setting master bd_addr to 00:1b:dc:00:44:3c
```...and when I pull the plug and turn the controller on again, it starts acting as a new mouse (even though that option isn't selected).

Any help would be very much appreciated.


Things are a little weird on Lucid... You should, first of all, select "None" as profile and apply it. Lucid ships a Xorg conf that enables joystick mouse without user intervention. This way *any* joystick won't work as mouse or keyboard.

Which kernel are use using?

The hidraw device seems to be created when you connect over USB. You can use "sudo sixad-raw /dev/hidrawX" to get it to work. It's not the perfect solution, but it should work.


I'll look into these Lucid issues soon, just be a little patient.

---

### Post by Efaustus9 on 2010-05-07
Thanks for creating this works quite well.

---

### Post by Occasionally Correct on 2010-05-07
> **falkTX said:**
> Which kernel are use using?
2.6.32-22-generic.

> The hidraw device seems to be created when you connect over USB. You can use "sudo sixad-raw /dev/hidrawX" to get it to work.
Well, I checked with and without the controller connected and it doesn't look like it's actually creating one... I tried *sixad-raw* anyway with the last hidraw device and it told me it wasn't a controller.

---

### Post by mmichielin on 2010-05-07
> **falkTX said:**
> Ooh...
That happens on Gnome, not KDE.
It is the bluetooth manager detecting an "untrusted device" (the Sixaxis), and just shows that dialog everytime...
I know that if you grant full access (I even tried setting it manually), it ignores yours settings and ask for authorization again.
...

Hi, I'm using my wonderful sixaxis with ubuntu (Lucid AMD64) via usb but unfortunately I'm not able to make it work via bluetooth using qtsixa because I'm having this "grant access" issue.

Can someone please tell me if this issue has somehow been solved?

I cannot uninstall bluetooth manager because I nedd it to connect my cell phones to the PC.

PS: falkTX, I think your work is very useful and your helpfulness is incomparable

Thanks in advance

---

### Post by falkTX on 2010-05-08
> **mmichielin said:**
> Hi, I'm using my wonderful sixaxis with ubuntu (Lucid AMD64) via usb but unfortunately I'm not able to make it work via bluetooth using qtsixa because I'm having this "grant access" issue.

Can someone please tell me if this issue has somehow been solved?

I cannot uninstall bluetooth manager because I nedd it to connect my cell phones to the PC.

PS: falkTX, I think your work is very useful and your helpfulness is incomparable

Thanks in advance

Firstly, use QtSixA to pair your sixaxis. Then later run:
```
sixad --stop
sixad --start

```
That should do it

---

### Post by falkTX on 2010-05-08
> **Occasionally Correct said:**
> 2.6.32-22-generic.


Well, I checked with and without the controller connected and it doesn't look like it's actually creating one... I tried *sixad-raw* anyway with the last hidraw device and it told me it wasn't a controller.

This seems a problem at the kernel level (broken drivers?).
Are you using Ubuntu? (it's ok if not, but I just need to know)

If not asking too much, can you try a different kernel?

---

### Post by Occasionally Correct on 2010-05-08
Yep, I'm using Ubuntu 10.04. I just tried kernel 2.6.34 rc6 and it's still behaving the same way. I wonder if this could be in part related to the removal of hal. I'll see if I can test with hal later today.

Edit: No difference.

---

### Post by falkTX on 2010-05-09
> **Occasionally Correct said:**
> Yep, I'm using Ubuntu 10.04. I just tried kernel 2.6.34 rc6 and it's still behaving the same way. I wonder if this could be in part related to the removal of hal. I'll see if I can test with hal later today.

Edit: No difference.

Have you consider the possibility... that your Sixaxis is broken... ?

---

### Post by Occasionally Correct on 2010-05-09
> **falkTX said:**
> Have you consider the possibility... that your Sixaxis is broken... ?
Now that you mention it, no! Used it about a week ago on my PS3, so I assumed it was in working condition... but I just plugged in another controller and it seems to work fine. I guess that settles things!

Thanks for all the help. Sorry I missed a step as obvious as making sure it still works. :P

---

### Post by falkTX on 2010-05-09
> **Occasionally Correct said:**
> Now that you mention it, no! Used it about a week ago on my PS3, so I assumed it was in working condition... but I just plugged in another controller and it seems to work fine. I guess that settles things!

Thanks for all the help. Sorry I missed a step as obvious as making sure it still works. :P

Try resetting the Sixaxis (a tiny hole in the back). It probably won't change anything though.

---

### Post by KLineD on 2010-05-10
Hi,

Sorry if this is a silly question but, is it possible to use the sixaxis/dualshock3 without bluetooth?

I ask this because I can't figure out how to pair my dualshock3 with my PC. I don't have bluetooth, but I figured out that using the USB cable would be enough. I installed QtSixA and it appears on the list of connected devices, then I press the PS button but the leds keep blinking (I'm assuming they will stop blinking and indicate the control number as if paired to the PS3)

Another thing I tried is to run sixad manually, I get a prompt to press the PS button but when I do, nothing happens.

In dmesg I get the following information:

> [ 2813.784752] input: Sony PLAYSTATION(R)3 Controller as /devices/pci0000:00/0000:00:1d.0/usb5/5-1/5-1:1.0/input/input15
[ 2813.785204] sony 0003:054C:0268.0003: input,hiddev96,hidraw0: USB HID v1.11 Joystick [Sony PLAYSTATION(R)3 Controller] on usb-0000:00:1d.0-1/input0
e

And when I unplug/plug the controller via USB, QtSixA even displays a notification that a new controller has been plugged in, but the leds keep blinking and never settle.

Any help is appreciated. Thanks in advance!

**Update:** ups, spoke too early. I restarted the controller by clicking the small button on the back, and it started to work perfectly. The leds are still blinking, but maybe that's normal?

---

### Post by mmichielin on 2010-05-10
> **falkTX said:**
> Firstly, use QtSixA to pair your sixaxis. Then later run:
```
sixad --stop
sixad --start

```
That should do it

Thanks again, now it works and I'm very happy!

A question: is it possibile to configure qtsixa to use dualshock3 just as a joystick for gaming and not as a substitute for the mouse in X?

I'm having some difficulty using dualshock as a mouse (sensing the accelerators...)

Thanks in advance

---

### Post by falkTX on 2010-05-10
> **mmichielin said:**
> Thanks again, now it works and I'm very happy!

A question: is it possibile to configure qtsixa to use dualshock3 just as a joystick for gaming and not as a substitute for the mouse in X?

I'm having some difficulty using dualshock as a mouse (sensing the accelerators...)

Thanks in advance

Use the option in QtSixA:
QtSixA -> Settings (menu) -> Configure Sixaxis -> Input profiles (tab).
Make sure you check "use sixaxis as joystick" but select "none" as profile.

---

### Post by fatski on 2010-05-12
Man, thank you for this. Works perfectly for me. I have to Force Connect but who cares?

I think this should be in the standard Ubuntu repositories.

---

### Post by falkTX on 2010-05-13
> **fatski said:**
> Man, thank you for this. Works perfectly for me. I have to Force Connect but who cares?

I think this should be in the standard Ubuntu repositories.

I tried, check this:
[http://revu.ubuntuwire.com/p/qtsixa](http://revu.ubuntuwire.com/p/qtsixa)

Probably on 10.10

---

### Post by Xenphor on 2010-05-20
Hello,

I was able to get everything working on 10.04 on my x86 laptop but I'm having troubles with the profiles. First of all, I don't see any option to make my own profile. I can select one from a list and get it working but am not able to customize. I found that the mouse is extremely sensitive on the firefox profile and would like to adjust it. I would also like to switch some of the buttom mappings around. Is this possible in the latest version or am I doing something wrong?

Edit: I've noticed that even after I select a profile and restart x, qtsixa still reports that I'm not using a profile even though I can use the mouse with a joystick, etc.

---

### Post by Efaustus9 on 2010-05-21
> **falkTX said:**
> Use the option in QtSixA:
QtSixA -> Settings (menu) -> Configure Sixaxis -> Input profiles (tab).
Make sure you check "use sixaxis as joystick" but select "none" as profile.

Following that path I see no option of "use sixaxis as joystick" just "use sixaxis as mouse/keyboard". Assuming a typo I select none as the profile and the sixaxis still acts like a mouse. Currently the only way I can get the sixaxis to not act like a mouse is to go to "input events" and disable every thing but "enable buttons". Im wondering if this has something to do with ubuntu and not specifically your application as even my usb joysticks do the same thing. Is there a way to tell ubuntu not to treat every joystick I plug into my computer as a mouse.

---

### Post by falkTX on 2010-05-21
> **Efaustus9 said:**
> Following that path I see no option of "use sixaxis as joystick" just "use sixaxis as mouse/keyboard". Assuming a typo I select none as the profile and the sixaxis still acts like a mouse. Currently the only way I can get the sixaxis to not act like a mouse is to go to "input events" and disable every thing but "enable buttons". Im wondering if this has something to do with ubuntu and not specifically your application as even my usb joysticks do the same thing. Is there a way to tell ubuntu not to treat every joystick I plug into my computer as a mouse.

That is indeed a problem with Ubuntu, see my next post.

---

### Post by falkTX on 2010-05-21
For all those of you using **Ubuntu Lucid**:

Profiles will not work as expected, or may not work at all.
Ubuntu has pushed too many changes in this release (again), so there are a lot of things that have changed. One of them is dropping HAL (what QtSixA uses for the profiles).
On Ubuntu Lucid, you'll get QtSixA v1.2.1b, which is just the same as 1.2.1 with quick adjustments for Lucid. I took the time to convert the HAL profiles to the new Ubuntu specification (xorg snippets), but they don't work well...

And because this could happen again (Ubuntu changes making QtSixA unusable), I started re-writing QtSixA, but focusing at getting profiles to work without the need of Xorg/HAL/etc.
Rumble is coming too, although I didn't see any game/testing tool that worked with rumble (fftest, the official tool, crashes).

The core driver (sixad) is 90% complete and I'll soon re-create the GUI.
Sorry if QtSixA doesn't work well on Lucid right now, I'm working on it.

In the meantime, please be patient.


[I]PS: If Ubuntu still acts as a mouse when you really don't want to, make sure you delete the file "/usr/lib/X11/xorg.conf.d/10-joystick*".
You'll have to restart Xorg...[/I]

---

### Post by Xenphor on 2010-05-21
Thanks for the reply and support. I will look forward to the next release.

---

### Post by Xenphor on 2010-05-21
I also thought of a feature that would be really nice for profiles. If this was already included before then I apologize but I think it would be cool to allow for multiple button presses. I'm thinking about things like Ctrl+Left Arrow or Right Arrow to go forwards or backwards in Firefox or Alt+Left Arrow or Right Arrow to scroll through tabs. I've tried other programs like qjoypad and they only seem to allow a single key to be mapped. 

If this was already a feature then I look forward to being able to use it, if not, then maybe it'll give you something to think about, thanks.

---

### Post by falkTX on 2010-05-21
> **Xenphor said:**
> I also thought of a feature that would be really nice for profiles. If this was already included before then I apologize but I think it would be cool to allow for multiple button presses. I'm thinking about things like Ctrl+Left Arrow or Right Arrow to go forwards or backwards in Firefox or Alt+Left Arrow or Right Arrow to scroll through tabs. I've tried other programs like qjoypad and they only seem to allow a single key to be mapped. 

If this was already a feature then I look forward to being able to use it, if not, then maybe it'll give you something to think about, thanks.

This feature IS present at the moment. For example, SMPlayer uses Ctrl+O to open a file (L1 button I think).

But this probably won't be available in the rewrite. I'm not sure yet, but I don't think it will be possible.

---

### Post by Efaustus9 on 2010-05-21
> **falkTX said:**
> For all those of you using **Ubuntu Lucid**:

Profiles will not work as expected, or may not work at all.
Ubuntu has pushed too many changes in this release (again), so there are a lot of things that have changed. One of them is dropping HAL (what QtSixA uses for the profiles).
On Ubuntu Lucid, you'll get QtSixA v1.2.1b, which is just the same as 1.2.1 with quick adjustments for Lucid. I took the time to convert the HAL profiles to the new Ubuntu specification (xorg snippets), but they don't work well...

And because this could happen again (Ubuntu changes making QtSixA unusable), I started re-writing QtSixA, but focusing at getting profiles to work without the need of Xorg/HAL/etc.
Rumble is coming too, although I didn't see any game/testing tool that worked with rumble (fftest, the official tool, crashes).

The core driver (sixad) is 90% complete and I'll soon re-create the GUI.
Sorry if QtSixA doesn't work well on Lucid right now, I'm working on it.

In the meantime, please be patient.


[I]PS: If Ubuntu still acts as a mouse when you really don't want to, make sure you delete the file "/usr/lib/X11/xorg.conf.d/10-joystick*".
You'll have to restart Xorg...[/I]

Thanks it worked like a charm. you rock :guitar:

---

### Post by Xenphor on 2010-05-21
I had another question. Since it seems your program is creating xorg config files, I was wondering if I could just modify them directly to change the different key mappings. Would this be possible or is there something that would prevent the changes from actually working? If that doesn't work, could I just manually create my own config file in that directory and have the dualshock 3 act as a mouse/kb or is your program doing something in addition? 

I'm sorry; I still do not really understand how xorg works so I'm not sure if what I'm asking is possible. Sorry to bother you but I figured you would be a good person to ask. Thanks.

edit: this would all be done through usb.

---

### Post by plextor on 2010-05-22
Hello, I'm testing sixad for a project based on it (with no QtSixa) . After the pairing, start successfully sixad  but the mouse in desktop works with the PS3 controller. Is there any way to disable this option without using QtSixA?

Regards,

---

### Post by falkTX on 2010-05-24
> **plextor said:**
> Hello, I'm testing sixad for a project based on it (with no QtSixa) . After the pairing, start successfully sixad  but the mouse in desktop works with the PS3 controller. Is there any way to disable this option without using QtSixA?

Regards,

If you check the previous posts...

> PS: If Ubuntu still acts as a mouse when you really don't want to, make sure you delete the file "/usr/lib/X11/xorg.conf.d/10-joystick*".
You'll have to restart Xorg...

---

### Post by falkTX on 2010-05-24
> **Xenphor said:**
> I had another question. Since it seems your program is creating xorg config files, I was wondering if I could just modify them directly to change the different key mappings. Would this be possible or is there something that would prevent the changes from actually working? If that doesn't work, could I just manually create my own config file in that directory and have the dualshock 3 act as a mouse/kb or is your program doing something in addition? 

I'm sorry; I still do not really understand how xorg works so I'm not sure if what I'm asking is possible. Sorry to bother you but I figured you would be a good person to ask. Thanks.

edit: this would all be done through usb.

A new QtSixA version is coming soon, and the way devices are managed will be different (no more xorg/hal stuff).

Just wait a few more days and I'll release a beta.

---

### Post by frs89 on 2010-05-26
@falkTX

Hello, 

         I'm interesting in knowing how sixaxis pairs with bluetooth devices, I only know that it involves the exchange of two passkeys in order to agree the connection. 

Questions:
1-What does QtSixa change in both sixaxis gamepad and the system to do the pairing? 
2-I realized that the sixaxis will only connect to the last paired system, there's any way to connect with different systems without re-pairing?

         I need also technical information regarding the sixaxis, like some kind of datasheet, I've goggled some but I can't find anything. If you could give me some references I'll be very thankful.

---

### Post by falkTX on 2010-05-26
> **frs89 said:**
> @falkTX

Hello, 

         I'm interesting in knowing how sixaxis pairs with bluetooth devices, I only know that it involves the exchange of two passkeys in order to agree the connection. 

Questions:
1-What does QtSixa change in both sixaxis gamepad and the system to do the pairing? 
2-I realized that the sixaxis will only connect to the last paired system, there's any way to connect with different systems without re-pairing?

         I need also technical information regarding the sixaxis, like some kind of datasheet, I've goggled some but I can't find anything. If you could give me some references I'll be very thankful.

1 - the utility "sixpair" is used to pair the sixaxis to the pc
2 - no, the sixaxis doesn't allow this (it can only have 1 master)

I'll be glad to help you after i release the next version.
PM me next week, ok?

---

### Post by Rich43 on 2010-06-06
Sorry if this question been done to death but I cant find a answer in this huge thread.

Is there any force feedback (viabration) support for dual shock 3?

---

### Post by falkTX on 2010-06-07
> **Rich43 said:**
> Sorry if this question been done to death but I cant find a answer in this huge thread.

Is there any force feedback (viabration) support for dual shock 3?

Not in the current version.

The once I'm still developing yes, but the GUI is not finished yet.

You can get the latest/latest QtSixA, alpha code in my testing PPA:
[https://launchpad.net/~falk-t-j/+archive/ppa/](https://launchpad.net/~falk-t-j/+archive/ppa/)

Rumble is there, although not many games support it.

---

### Post by benmoran on 2010-06-08
First of all, I think I speak for everyone who uses a Dualshock/sixaxis and Linux when I say  Thanks for creating such an awesome program!

I have a suggestion that I think makes sense. The way it is now, by default the left stick is set as the joystick. That part is OK. The problem is that the Select, Start, and the two Stick Clicks are set to the first joystick buttons.  A lot of games don't have any button configuration, so it's impossible to play them. Is it possible to set the first four joystick buttons to the Square-Triangle-Circle-X buttons? It would make a lot of games playable as-is.

---

### Post by falkTX on 2010-06-08
> **benmoran said:**
> First of all, I think I speak for everyone who uses a Dualshock/sixaxis and Linux when I say  Thanks for creating such an awesome program!

I have a suggestion that I think makes sense. The way it is now, by default the left stick is set as the joystick. That part is OK. The problem is that the Select, Start, and the two Stick Clicks are set to the first joystick buttons.  A lot of games don't have any button configuration, so it's impossible to play them. Is it possible to set the first four joystick buttons to the Square-Triangle-Circle-X buttons? It would make a lot of games playable as-is.

But then it will be not compatible using USB and bluetooth modes...

I can make it as you want though, later on the new v1.5.0 version.

And thanks!

---

### Post by benmoran on 2010-06-09
Thank you FalkTX! 

I've started using your testing PPA. Everything works OK, except for the unfinished GUI of course. Is there anything you need tested?

---

### Post by falkTX on 2010-06-09
> **benmoran said:**
> Thank you FalkTX! 

I've started using your testing PPA. Everything works OK, except for the unfinished GUI of course. Is there anything you need tested?

hmm... you shouldn't use that PPA, all my testing stuff go there.
but anyway, use it with care, and be suspicious about any update in that PPA...

if you have a dualshock3, the rumble support really needs testing.
I haven't found a single game that supports rumble/force-feeback...

And thanks for the interest on QtSixA!

---

### Post by benmoran on 2010-06-12
I wonder if windows games that support rumble will work through wine? My PC isn't fast enough to test any of them, but hopefully somebody else can.

---

### Post by BLuFeNiX on 2010-06-13
@FalkTX

I'm also using your testing PPA, and everything is great, but I was wondering if there was a way to revert the mouse control back to being relative? In the older version of QtSixA when I moved the left axis the cursor would move across the screen and stay there. Now I have to hold the axis in that position, so if I let go of the joystick it moves the cursor back over to where it was. This *would* be okay, but the learning system isn't working well for me (I have to move the joystick back and forth to reset the deadzone and can't move it too slowly, otherwise I can't go to the edge of the screen).

I found that **/usr/lib/X11/xorg.conf.d/11-sixaxis_gnome.conf** contains these lines:
```
        Option "MapAxis1"       "**mode=relative** axis=+2x deadzone=5000"
        Option "MapAxis2"       "**mode=relative** axis=+2y deadzone=5000"
        Option "MapAxis3"       "**mode=relative** axis=+1zx deadzone=7500"
        Option "MapAxis4"       "**mode=relative** axis=+1zy deadzone=7500"
```

and the new config files in **~/.qtsixa2/profiles/** contain this: ```
axis_left_type 3
axis_left_up 1
axis_left_right 0
axis_left_down 0
axis_left_left 0
axis_right_type 3
axis_right_up 8
axis_right_right 6
axis_right_down 0
axis_right_left 0
```

In the second block of code there is no "mode" parameter. Is there a way to make this new config file "relative" or am I looking in the wrong direction?

Thanks :)

---

### Post by falkTX on 2010-06-14
> **BLuFeNiX said:**
> @FalkTX

I'm also using your testing PPA, and everything is great, but I was wondering if there was a way to revert the mouse control back to being relative? In the older version of QtSixA when I moved the left axis the cursor would move across the screen and stay there. Now I have to hold the axis in that position, so if I let go of the joystick it moves the cursor back over to where it was. This *would* be okay, but the learning system isn't working well for me (I have to move the joystick back and forth to reset the deadzone and can't move it too slowly, otherwise I can't go to the edge of the screen).

I found that **/usr/lib/X11/xorg.conf.d/11-sixaxis_gnome.conf** contains these lines:
```
        Option "MapAxis1"       "**mode=relative** axis=+2x deadzone=5000"
        Option "MapAxis2"       "**mode=relative** axis=+2y deadzone=5000"
        Option "MapAxis3"       "**mode=relative** axis=+1zx deadzone=7500"
        Option "MapAxis4"       "**mode=relative** axis=+1zy deadzone=7500"
```

and the new config files in **~/.qtsixa2/profiles/** contain this: ```
axis_left_type 3
axis_left_up 1
axis_left_right 0
axis_left_down 0
axis_left_left 0
axis_right_type 3
axis_right_up 8
axis_right_right 6
axis_right_down 0
axis_right_left 0
```

In the second block of code there is no "mode" parameter. Is there a way to make this new config file "relative" or am I looking in the wrong direction?

Thanks :)

Consider that a bug, as I don't like how it works too. (I also can't see anyone wanting that)
I should fix it soon enough though, don't worry.

---

### Post by BLuFeNiX on 2010-06-14
> **falkTX said:**
> Consider that a bug, as I don't like how it works too. (I also can't see anyone wanting that)
I should fix it soon enough though, don't worry.

I can see it being useful for some things, were it not so sensitive, and maybe had a manual calibration option, rather than the learning system. But it's good to know that it will be fixed soon! Thank you for this wonderful program!

---

### Post by Matt- on 2010-06-23
@FalkTX

I'm trying to use my PS3 controller with Blender, which is interfacing with a microcontroller to control a RC car. How would I go about reading the values from the controller in a Python script?

So far the PS3 controller works great with Ubuntu, thanks to QtSixA. Thanks.

---

### Post by falkTX on 2010-06-23
> **Matt- said:**
> @FalkTX

I'm trying to use my PS3 controller with Blender, which is interfacing with a microcontroller to control a RC car. How would I go about reading the values from the controller in a Python script?

So far the PS3 controller works great with Ubuntu, thanks to QtSixA. Thanks.

Reading joysticks values from python... I don't know anything about that, sorry.

But I know that blender has an internal game engine, where you can map joystick buttons/axis (and accelerometers too) to a specific action, like button "Up" moves the cube pos-x +1 value, etc

---

### Post by Mudbutt on 2010-06-23
Hey

I couldn't get QtSixA working, but I got the Sixaxis working with only using sixad -s in ps3 ubuntu 10.04. 
I have a problem where the sixaxis automatically replaces the mouse so that I have to use the sixaxis to move the mouse cursor. The mouse is basicly docked in the middle of the screen and i control it with the left sixaxis analog stick, and have to use the left mouse button as one usually does.
 That causes some problems. Any way to disable that, and enable the actual mouse to control the mouse cursor?

PS: It didn't work removing the xorg file..

---

### Post by falkTX on 2010-06-23
> **Mudbutt said:**
> Hey

I couldn't get QtSixA working, but I got the Sixaxis working with only using sixad -s in ps3 ubuntu 10.04. 
I have a problem where the sixaxis automatically replaces the mouse so that I have to use the sixaxis to move the mouse cursor. The mouse is basicly docked in the middle of the screen and i control it with the left sixaxis analog stick, and have to use the left mouse button as one usually does.
 That causes some problems. Any way to disable that, and enable the actual mouse to control the mouse cursor?

PS: It didn't work removing the xorg file..

are you by any chance using the new/beta version from the testing ppa?
that would explain it...

---

### Post by Mudbutt on 2010-06-24
I installed sixad from the 1.2.1b download with make install-system, but I was unable to install qtsixa. 
At least I think I'm using the 1.2.1b version, however, the version displayed in sixad -v says it's 1.2.0. Did you update that?

It's not the PPA version, I haven't figured out how to install that one. Should qtsixa be available in Synaptic Software Center if I added the PPA repo correctly?

sorry for the slow reply btw..

---

### Post by falkTX on 2010-06-24
> **Mudbutt said:**
> I installed sixad from the 1.2.1b download with make install-system, but I was unable to install qtsixa. 
At least I think I'm using the 1.2.1b version, however, the version displayed in sixad -v says it's 1.2.0. Did you update that?

It's not the PPA version, I haven't figured out how to install that one. Should qtsixa be available in Synaptic Software Center if I added the PPA repo correctly?

sorry for the slow reply btw..

hm, the "sixad -v", probably i just forgot... it happens sometimes

the PPA version is TESTING, and I'm glad u don't use that one, cause it still needs some work there...

About your mouse error, I think it's something related to a PS3-Ubuntu bug... (I don't have a PS3, sorry)

Can you check for older posts?
There was a problem similar to yours...

---

### Post by Matt- on 2010-06-24
I've got another question sorry. 

I'm currently making a profile, which is a fairly simple task. What I want though is to use only the vertical motion of the left joystick mapped to the mouse, and the horizontal motion of the right joystick mapped to the mouse. That way I can use the analog motion of both joysticks to control a car model in Blender.

I thought about using the scroll option, although it doesn't seem to be analog.

Any ideas?

---

### Post by falkTX on 2010-06-25
> **Matt- said:**
> I've got another question sorry. 

I'm currently making a profile, which is a fairly simple task. What I want though is to use only the vertical motion of the left joystick mapped to the mouse, and the horizontal motion of the right joystick mapped to the mouse. That way I can use the analog motion of both joysticks to control a car model in Blender.

I thought about using the scroll option, although it doesn't seem to be analog.

Any ideas?

What linux/ubuntu version do you use?

Supposing that is not Lucid, this can be possible and should be simple.

First you should create a basic profile to start.
Then edit it manually through a text editor, and make the axes part like this:

```
        <merge key="input.x11_options.MapAxis1" type="string">mode=none</merge>
        <merge key="input.x11_options.MapAxis2" type="string">mode=relative axis=+2y deadzone=5000</merge>
        <merge key="input.x11_options.MapAxis3" type="string">mode=none</merge>
        <merge key="input.x11_options.MapAxis4" type="string">mode=relative axis=+2x deadzone=5000</merge>

```

Not sure if that is exactly what you want, but it should give you an idea of how it works.
Tell me if you need any more help

---

### Post by Matt- on 2010-06-25
Unfortunately I'm running Lucid. I've tried to install 1.2.1b but it fails when I try to make. Part of the error is displayed below:

sdp.c:37:33: error: bluetooth/bluetooth.h: No such file or directory
sdp.c:38:29: error: bluetooth/l2cap.h: No such file or directory
sdp.c:39:27: error: bluetooth/sdp.h: No such file or directory
sdp.c:40:31: error: bluetooth/sdp_lib.h: No such file or directory
sdp.c:41:28: error: bluetooth/hidp.h: No such file or directory
sdp.c:42:28: error: bluetooth/bnep.h: No such file or directory

I'll just wait till you've completed the next version before using profiles. Thanks for your help anyway.

---

### Post by falkTX on 2010-06-25
> **Matt- said:**
> Unfortunately I'm running Lucid. I've tried to install 1.2.1b but it fails when I try to make. Part of the error is displayed below:

sdp.c:37:33: error: bluetooth/bluetooth.h: No such file or directory
sdp.c:38:29: error: bluetooth/l2cap.h: No such file or directory
sdp.c:39:27: error: bluetooth/sdp.h: No such file or directory
sdp.c:40:31: error: bluetooth/sdp_lib.h: No such file or directory
sdp.c:41:28: error: bluetooth/hidp.h: No such file or directory
sdp.c:42:28: error: bluetooth/bnep.h: No such file or directory

I'll just wait till you've completed the next version before using profiles. Thanks for your help anyway.

hm.. there are debs for QtSixA...

that errors are because of missing libraries (libusb-de, libbluetooth-dev, etc)

---

### Post by databreaker on 2010-07-06
ok so i'm having issues getting the bluetooth to work. everything works fine when connected with USB. i used the sixpair program to change the master BT addr on the controller, and both qtsixa and hcitool list my controller as connected. the four LEDs on the controller continue to flash.

> kevin@cerberus:~$ hcitool con
Connections:
    > ACL 00:1E:3D:B9:1B:9D handle 11 state 1 lm MASTER 
> qtsixa:
List of connected devices:  00:1E:3D:B9:1B:9D
PLAYSTATION(R)3 Controller, Joystick, 054c:0268, Bluetooth
but I have no joystick (js0) in folder /dev/input/ like I do when I connect via USB. After connecting via USB and seeing everything works fine, I unplug the cable expecting it to switch to bluetooth mode. Looking at /var/log/syslog, I see this:

> Jul  6 00:54:21 cerberus NetworkManager: bluez_manager_bdaddr_removed_cb: BT  device 00:1E:3D:B9:1B:9D removed
Jul  6 00:54:29 cerberus bluetoothd[2856]: Refusing connection: setup in progress
but hcitool and qtsixa both say 'connected'. any idea? i'm using karmic.

SOLVED: if I run sixad in force mode, bluetooth works fine.

---

### Post by falkTX on 2010-07-12
Good news!

The development version has become kinda stable and it's now on QtSixA Lucid PPA.
Intrepid/Jaunty/Karmic users will have v1.2.1 for now, as the bugs get fixed on the new version (1.5.0)

This new version brings many changes, including:
 - Rumble is now supported
 - Every device has it's own configuration now, but will use the default if it's not set-up yet
 - Only bluetooth sixaxis have input profile support (for now)
 - new utility "sixad-jack" which will make your Sixaxis act like a midi-keyboard

Some stuff is not implemented yet though, like auto-disconnect after some time, only 1 QtSixA instance and some other small stuff.

For bugs and requests, please do it in this page:
[https://bugs.launchpad.net/qtsixa](https://bugs.launchpad.net/qtsixa)
Make sure you say what QtSixA version you're using.


Feel free to ask any questions, I should probably make a FAQ soon...



And enjoy this release!

---

### Post by asorron on 2010-07-13
for some reason pairing over usb works but through bluetooth its like... dead, it wont even find the sixaxis... any idea whats wrong (adapter is on btw.)?
running lucid if it helps
P.s;

Running it with my laptop bluetooth card is possible?

---

### Post by falkTX on 2010-07-13
> **asorron said:**
> for some reason pairing over usb works but through bluetooth its like... dead, it wont even find the sixaxis... any idea whats wrong (adapter is on btw.)?

hm, have you tried the force option?

you can run this in the terminal to get some output:
```
sixad --stop
sixad --start
#press the PS button now

```

---

### Post by asorron on 2010-07-13
The irony is the line that you wrote is the only output I get... its like it refuses to connect to it.

---

### Post by falkTX on 2010-07-13
> **asorron said:**
> The irony is the line that you wrote is the only output I get... its like it refuses to connect to it.

hm, how so?

which QtSixA version do you have?

---

### Post by asorron on 2010-07-13
funny, yesterday it was 1.2.0.0 beta (i think) but now its 1.5.0.0 but still wont work... (didnt work out yesterday too.)

ask my for any input/output and ill give it out, i've been running after this such of pairing program since windows 7 came out but it didnt work out too.

the thing i think of the most is ; if its possible to do so with the onboard bluetooth device of my lappy.

---

### Post by falkTX on 2010-07-13
> **asorron said:**
> funny, yesterday it was 1.2.0.0 beta (i think) but now its 1.5.0.0 but still wont work... (didnt work out yesterday too.)

ask my for any input/output and ill give it out, i've been running after this such of pairing program since windows 7 came out but it didnt work out too.

if you connect the sixaxis over usb, with the bluetooth dongle on too,
what is the output of:
```
sudo sixpair
```
?

---

### Post by asorron on 2010-07-13
I get this out: 
```
Current Bluetooth master: 00:1b:fb:45:f0:dd
Setting master bd_addr to 00:0d:f0:7a:35:82
USB_REQ_SET_CONFIGURATION: Broken pipe

```

putting it back up again; does it have to be with some kind of a bluetooth stick (usb connected one) or it can be done with the laptop one?

---

### Post by falkTX on 2010-07-13
> **asorron said:**
> I get this out: 
```
Current Bluetooth master: 00:1b:fb:45:f0:dd
Setting master bd_addr to 00:0d:f0:7a:35:82
USB_REQ_SET_CONFIGURATION: Broken pipe

```

putting it back up again; does it have to be with some kind of a bluetooth stick (usb connected one) or it can be done with the laptop one?

well, anyway, the pairing didn't work:
"USB_REQ_SET_CONFIGURATION: Broken pipe" means errors

without pairing first, bluetooth will certainly not work...

I'll have to check this once I get home later today

---

### Post by asorron on 2010-07-13
I think iv'e found out something...

```
Orginally from https://help.ubuntu.com/community/Sixaxis

"..
**Requirements**

 Must be using kernel version 2.6.21  or later..."


```and from running:
```
 file /usr/bin/file

/usr/bin/file: ELF 32-bit LSB executable, Intel 80386, version 1 (SYSV), dynamically linked (uses shared libs), for GNU/Linux 2.6.15, stripped

```It means something isnt it?8-[

My bad, didnt figure out Lucid comes out with 2.6.3x kernels, haha.

---

### Post by falkTX on 2010-07-13
> **asorron said:**
> I think iv'e found out something...

```
Orginally from https://help.ubuntu.com/community/Sixaxis

"..
**Requirements**

 Must be using kernel version 2.6.21  or later..."


```

and from running:
```
 file /usr/bin/file

/usr/bin/file: ELF 32-bit LSB executable, Intel 80386, version 1 (SYSV), dynamically linked (uses shared libs), for GNU/Linux 2.6.15, stripped

```
It means something isnt it?8-[


no, nothing at all...

there seems to be a bug in the pairing utility i need to fix first...
should be fixed tomorrow

heh, I said v1.5.0 was beta...

---

### Post by asorron on 2010-07-13
Generally, it feels like im missing something, doesnt a joystick or some sort of device manager for joystick needed to be installed in order to set something to it? like x11 joystick input or something.

or the program itself is mounting the joystick out as a standalone?

---

### Post by tipdrinker on 2010-07-13
Hi, 

I hope this issue wasnt already brought up but i dont have the patience to trudge through the whole 62 pages on this post. Anyway here goes :-)

I have no blue-tooth on my pc and was just hoping to connect my six-axis via USB so i can play some emulator games. I tried going through this tutorial 

[https://help.ubuntu.com/community/Sixaxis#USB%20Pairing](https://help.ubuntu.com/community/Sixaxis#USB%20Pairing)

but got lost about half way through. I then installed the program on this post. The program recognises my controller but I don't seem to be able to get it to work. Also it recognises it on gens/gs but it wont let me set up the buttons.

am i missing something or doing something wrong?

hope someone can help

I just realised i installed version 1.5 instead of 1.2.1 ( I'm using mint which is built on lucid) would this be a factor?

---

### Post by falkTX on 2010-07-13
> **tipdrinker said:**
> Hi, 

I hope this issue wasnt already brought up but i dont have the patience to trudge through the whole 62 pages on this post. Anyway here goes :-)

I have no blue-tooth on my pc and was just hoping to connect my six-axis via USB so i can play some emulator games. I tried going through this tutorial 

[https://help.ubuntu.com/community/Sixaxis#USB%20Pairing](https://help.ubuntu.com/community/Sixaxis#USB%20Pairing)

but got lost about half way through. I then installed the program on this post. The program recognises my controller but I don't seem to be able to get it to work. Also it recognises it on gens/gs but it wont let me set up the buttons.

am i missing something or doing something wrong?

hope someone can help

I just realised i installed version 1.5 instead of 1.2.1 ( I'm using mint which is built on lucid) would this be a factor?

Sixaxis should just work when used in USB mode.
All you need is to press the PS button once (after connecting through USB) to activate it.


The QtSixA Lucid version is now 1.5.0 Beta, as the old 1.2.1 didn't work very well...

---

### Post by asorron on 2010-07-13
Okay, I got forward, thanks for putting that page up, I thought of using it from the start but for some reason I thought it will have collisions with QtSixa. but still, im stuck on hidd stop,
```
service hidd stop
hidd: unrecognized service
```
and for trying to run hidd
```
sudo hidd --server --nocheck -n
Can't listen on HID control channel: Address already in use
```
if i kill bluetooth it wont let me use it again untill logoff (i think, unless im missing something out.)

---

### Post by falkTX on 2010-07-13
> **asorron said:**
> Okay, I got forward, thanks for putting that page up, I thought of using it from the start but for some reason I thought it will have collisions with QtSixa. but still, im stuck on hidd stop,
```
service hidd stop
hidd: unrecognized service
```
and for trying to run hidd
```
sudo hidd --server --nocheck -n
Can't listen on HID control channel: Address already in use
```
if i kill bluetooth it wont let me use it again untill logoff (i think, unless im missing something out.)

What the heck...?

The QtSixA actually uses code from hidd...
hidd is deprecated now...

Can't you guys just read the manual:
[http://qtsixa.sourceforge.net/](http://qtsixa.sourceforge.net/)
click on the left, "manual"

---

### Post by asorron on 2010-07-13
bingo. shoul've run the whole thing through QtSixa.
It got the id of it and for now i just missed the accept connection buttion so im trying to restore it.

P.S

running couple of remotes at once is possible?

---

### Post by falkTX on 2010-07-13
> **asorron said:**
> bingo. shoul've run the whole thing through QtSixa.
It got the id of it and for now i just missed the accept connection buttion so im trying to restore it.

P.S

running couple of remotes at once is possible?

Yes, I was able to connect (and play) with 4 sixaxis at the same time.
The QtSixA video on Youtube (2nd part, shows a demo...)

---

### Post by asorron on 2010-07-13
Awsome! it finally works!

I think the main cause was pointing to that bluez update which obviously made the difference...

tip: how about a "minimize to try" in task button? since pressing over the X closes it :/


MUSTT SAYY
Awsome work dude. I totally worship you now, finally my lappy can be used as remoteable ps3 XD pes2010 here i come :D

though the game behaving wierd as im attempting to set it up at thsi moment

---

### Post by falkTX on 2010-07-13
> **asorron said:**
> Awsome! it finally works!

I think the main cause was pointing to that bluez update which obviously made the difference...

tip: how about a "minimize to try" in task button? since pressing over the X closes it :/


MUSTT SAYY
Awsome work dude. I totally worship you now, finally my lappy can be used as remoteable ps3 XD pes2010 here i come :D

thanks.

double click on the systray icon to hide the main window
make sure you enable it first on the settings...

---

### Post by asorron on 2010-07-14
got one for you, while playing PES2010 , the screen fades, goes black and screensaver part kicks in, though i dont want to increase the screensaver time, as I just want to make the joystick "wake on key" settings just like using the computer count as busy and not idle. any way to do that? or you can add it to your next update? :]

---

### Post by falkTX on 2010-07-14
> **asorron said:**
> got one for you, while playing PES2010 , the screen fades, goes black and screensaver part kicks in, though i dont want to increase the screensaver time, as I just want to make the joystick "wake on key" settings just like using the computer count as busy and not idle. any way to do that? or you can add it to your next update? :]

Just enable joystick and input profiles, and set like "left" and "x" buttons to some random keyboard keys.
That would do the trick

---

### Post by asorron on 2010-07-15
Okay, I've found out another issue,
Playing PES2010 on the bluetooth works flawlessly.
But I just found out some sort of bug that issues playing on it as the controller as #2 and the laptop keyboard is set as player 1, the buttons dont behave well, and the controller overlaps the keyboard and sending some commands from the controller to the player 1 while playing. as in, for some reason while i use R1 on the controller, it selects one of my player and sustainly moving right.

I dont really know whats causing it, I'm gonna try two controllers at once later on today (idk if its possible, but oh well..)

blah... seems like i need to manually run Sixad from its folder to make it work.

Edit; got it to work using the above method.

---

### Post by falkTX on 2010-07-16
> **asorron said:**
> Okay, I've found out another issue,
Playing PES2010 on the bluetooth works flawlessly.
But I just found out some sort of bug that issues playing on it as the controller as #2 and the laptop keyboard is set as player 1, the buttons dont behave well, and the controller overlaps the keyboard and sending some commands from the controller to the player 1 while playing. as in, for some reason while i use R1 on the controller, it selects one of my player and sustainly moving right.

I dont really know whats causing it, I'm gonna try two controllers at once later on today (idk if its possible, but oh well..)

Probably you set some keyboard key to R1, that is already in use in PES.
Try setting weird keys (accents, special chars, etc) and it should be fine

---

### Post by asorron on 2010-07-16
well the joypad is causing both keyboard and player 2 to move, and I saw I cant really configure it at that menu... Plus, when confinguring keys at PES 2010 settings it acts like you configure a joypad and not a keyboard, so I think it uses the raw keys inputted from it, while setting the keys works as a keyboard and configuring it out will act for both players, I dont think you can play with 2 players at the keyboard, the game wont let you, it'll ask for another player to connect.

---

### Post by asorron on 2010-07-16
trying to pair another remote it gives me broken pipe error message again... whats wrong with it :/

---

### Post by falkTX on 2010-07-16
> **asorron said:**
> trying to pair another remote it gives me broken pipe error message again... whats wrong with it :/

That is my error...
I was trying to join sixpair and sixpair-kbd in the same file, it didn't work...

I'll fix this in an update soon.

---

### Post by Pipmeister. on 2010-07-17
I get a broken pipe error whenever I try to pair a controller (1.5 beta on Lucid). Is this related?

---

### Post by falkTX on 2010-07-17
> **Pipmeister. said:**
> I get a broken pipe error whenever I try to pair a controller (1.5 beta on Lucid). Is this related?

Yes, I should fix this soon

---

### Post by quequotion on 2010-07-17
I had an issue with the sixaxis and all other joysticks on my pc working as mice which I resolved by removing xserver-xorg-input-joystick.

I am not sure if it was related to QTSixA or not however, as there was one suspicious bit where the QTSixA input profile, specified the joystick as "/dev/input/js*" meaning any and all devices js(something)... however, modifying this file, deleting this file, disabling QTSixA, and various other attempts to solve the problem on that end failed to change anything.  

Unfortunately, xserver-xorg-input-joystick took QTSixA with it as it's dependent...

Two questions about this: Is there a way to configure sixad by command line? (ie disable/enable accelerometers) OR Has this issue been resolved?

Also, any news on how other bluetooth devices are handled while sixad is running? Does using this driver still disable support for standard bluetooth connections?

---

### Post by falkTX on 2010-07-17
> **quequotion said:**
> I had an issue with the sixaxis and all other joysticks on my pc working as mice which I resolved by removing xserver-xorg-input-joystick.

I am not sure if it was related to QTSixA or not however, as there was one suspicious bit where the QTSixA input profile, specified the joystick as "/dev/input/js*" meaning any and all devices js(something)... however, modifying this file, deleting this file, disabling QTSixA, and various other attempts to solve the problem on that end failed to change anything.  

Unfortunately, xserver-xorg-input-joystick took QTSixA with it as it's dependent...

Two questions about this: Is there a way to configure sixad by command line? (ie disable/enable accelerometers) OR Has this issue been resolved?

Also, any news on how other bluetooth devices are handled while sixad is running? Does using this driver still disable support for standard bluetooth connections?

On Lucid, "xserver-xorg-input-joystick" is set as 'conflict' with QtSixA...
It's only needed on previous versions.

To configure sixad/joysticks, use the QtSixA GUI

And udev takes care of new devices, disabling the regular bluetooth when a Sixaxis or Keypad is found, waiting for the connection (10 seconds), then restores normal bluetooth again

---

### Post by asorron on 2010-07-17
Okay, Ive got another thing for you, while connecting the controllers via either bluetooth or usb. It seems it configures it as Joystick / Joystick - 2 at the PES settings, and I suspect that theres some /dev/xxx that is being replaced by the order you connect the controllers, can you define by the leds, that when you connect either controllers, that they will have some reserved device for them at QtSixa? so when the settings wont be changed while you either connect either of the controllers

I still dont know if its a good idea because it wont happen the same way on the ps3, but I also found out that when you set the settings of the leds to "Auto" it wont give them different lights for some reason...

I dont know if its a good idea, but feel free to inspect these things and tell me what you think :D

---

### Post by falkTX on 2010-07-17
> **asorron said:**
> Okay, Ive got another thing for you, while connecting the controllers via either bluetooth or usb. It seems it configures it as Joystick / Joystick - 2 at the PES settings, and I suspect that theres some /dev/xxx that is being replaced by the order you connect the controllers, can you define by the leds, that when you connect either controllers, that they will have some reserved device for them at QtSixa? so when the settings wont be changed while you either connect either of the controllers

I still dont know if its a good idea because it wont happen the same way on the ps3, but I also found out that when you set the settings of the leds to "Auto" it wont give them different lights for some reason...

I dont know if its a good idea, but feel free to inspect these things and tell me what you think :D

On Lucid, you can set a custom led # to a specific joystick.

The Auto-LED thing doesn't work because it's not implemented yet..
For now, it will always use LED #1

---

### Post by asorron on 2010-07-17
Well, actually I did set it by manual led display, but, when you connect a joypad, it mounts it as a device, which I would like to keep its settings (like i have dualshock 3 and just sixaxis gamepad which i disabled rumble and have specific settings to it through the game manager, ill add a pic so youll see what im talking about.
[[IMG]http://img441.imageshack.us/img441/9248/79152619.th.jpg[/IMG]]("http://img441.imageshack.us/i/79152619.jpg/")

Uploaded with [ImageShack.us]("http://imageshack.us")

Sorry that my remotes weren't available atm (bro took em to play with his friends). but imagine that the listing there is as I detailed. for any remote youll get " Joystick & another selection of the Sony Playstation remote..... +(the ID of it listed)." once you select the joystick listing  you will be able to set the keys, and once you set the Sony... listing the keys you will press will come out wrong. So, the joystick listing will come out by the order of the controllers you connect if you connect the controller you assigned to "led 2" it will take the settings of "joystick 1" and if you connected the controller that assigned to "led 1" first, he will take those settings. so I'd like to reserve mounting spots for the devices you connect, I.E , you connected JoyLed 1, and it will save it as a saved device in the system untill you remove these settings, so the next time you connect it, it will mount it under the device it was saved as and not as the other one...

I know that its quite complicated to understand but I cant find any other way to put it out.

It might have better use in the future with some other games which people like to play with totally other settings...

---

### Post by falkTX on 2010-07-17
> **asorron said:**
> Well, actually I did set it by manual led display, but, when you connect a joypad, it mounts it as a device, which I would like to keep its settings (like i have dualshock 3 and just sixaxis gamepad which i disabled rumble and have specific settings to it through the game manager, ill add a pic so youll see what im talking about.
[[IMG]http://img441.imageshack.us/img441/9248/79152619.th.jpg[/IMG]]("http://img441.imageshack.us/i/79152619.jpg/")

Uploaded with [ImageShack.us]("http://imageshack.us")

Sorry that my remotes weren't available atm (bro took em to play with his friends). but imagine that the listing there is as I detailed. for any remote youll get " Joystick & another selection of the Sony Playstation remote..... +(the ID of it listed)." once you select the joystick listing  you will be able to set the keys, and once you set the Sony... listing the keys you will press will come out wrong. So, the joystick listing will come out by the order of the controllers you connect if you connect the controller you assigned to "led 2" it will take the settings of "joystick 1" and if you connected the controller that assigned to "led 1" first, he will take those settings. so I'd like to reserve mounting spots for the devices you connect, I.E , you connected JoyLed 1, and it will save it as a saved device in the system untill you remove these settings, so the next time you connect it, it will mount it under the device it was saved as and not as the other one...

I know that its quite complicated to understand but I cant find any other way to put it out.

It might have better use in the future with some other games which people like to play with totally other settings...

I'm not sure if I understand...
in QtSixA, different sixaxis have different names and configs...

Maybe you need to make sure which sixaxis needs to be connected first ?

I guess you should keep trying until you find a proper solution...

---

### Post by asorron on 2010-07-17
If you connect some sixaxis first, it'll take the settings of the "Joystick 1" that will show up in the game's configuration settings (i.e picture.) and you'll need to disconnect it and connect the other controller in order to get the other controller the settings you wanted. so I just wanted the ability to switch settings between the controllers without turning both of them off and setting them on by order.

---

### Post by falkTX on 2010-07-17
> **asorron said:**
> If you connect some sixaxis first, it'll take the settings of the "Joystick 1" that will show up in the game's configuration settings (i.e picture.) and you'll need to disconnect it and connect the other controller in order to get the other controller the settings you wanted. so I just wanted the ability to switch settings between the controllers without turning both of them off and setting them on by order.

ah, ok, i get the point now.

This should be possible, yes, but I won't be able to get it done/implemented so soon...
Same thing goes for the rumble test button.

maybe you could mark the first joystick somehow, and make sure you connect it first... ?

---

### Post by frs89 on 2010-07-17
I'm using sixad in the shell to connect the sixaxis. It creates /dev/input/js0, but all the times, the LED that brights is the second. Any way to fix this?

---

### Post by falkTX on 2010-07-17
> **frs89 said:**
> I'm using sixad in the shell to connect the sixaxis. It creates /dev/input/js0, but all the times, the LED that brights is the second. Any way to fix this?

Just manually set the LED # to any you want (1 to 7) in the options

---

### Post by frs89 on 2010-07-17
> Quote:
                                                                      Originally Posted by **frs89**                     [[IMG]http://ubuntuforums.org/images/buttons/viewpost.gif[/IMG]]("http://ubuntuforums.org/showthread.php?p=9601703#post9601703")                 
                 *I'm using sixad in the shell to  connect the sixaxis. It creates /dev/input/js0, but all the times, the  LED that brights is the second. Any way to fix this?*
                                 
Just manually set the LED # to any you want (1 to 7) in the  optionsWhere are the options?

---

### Post by falkTX on 2010-07-17
> **frs89 said:**
> Where are the options?

In QtSixA...

---

### Post by asorron on 2010-07-17
@frs89: in QtSixa ; settings >Manage devices/profiles ; add the device that you want and set the led to manual and the leds you want to apply to it.

well generally the Dualshock has rumble and the sixaxis doesnt (Dualshock is just a sixaxis with rumble on it.) so its not that hard to figure what is what, but lets say people who wanna play any game with both controllers support are gonna play it with X360 remote and PS3 remote the same time, the options of it are obviously gonna change, probably its a different input to the config and once it connects under js0 it will have different settings to it. the idea is to be able to switch the input device while the controllers connected, the question is how, maybe disconnecting a remote by remote with short delay (it might send it a kill sign and then it will re-try to connect) so killing the 2nd one first and then the 1st one, and then the 2nd one tries to catch it faster than the 1st one and then it switches hardware-side. maybe theres a way to do it client side too (linux, that is.)

This thing is as same as ps3 "PS hold to change remotes" method, you hold the PS button, prompt with settings menu to turn off ps3/remote/quit game/switch remotes things. so I thought the most useful thing will be the switch remote idea.

hope this idea might come into future use.

Edit:

Its annoying me now... my brother got the remotes back after he paired them back with the ps3 now I cant get them paired back to the pc because of that broken pipe error... its too randomly connecting, I wish i knew what was it that iv'e done to get it paired back :(

---

### Post by asorron on 2010-07-17
OKAY I've found out the reason i got the broken pipes msgs. i told Sixpair to run by typing 
```
$sudo sixpair
```But after seeking a little bit at websites, iv'e found that i shoudl've run
```
$sudo ./sixpair/sixpair
```Its all working now, maybe thats the same reason the broken pipe msg appear on qtsixa too?

Also i noted that when letting it connect by accepting it without the force connection, it wont let it and just refresh it (looks like the windows program that iv'e got, it shows almost the same thing)

only using force will let the remote to connect :|

---

### Post by frs89 on 2010-07-17
I want to read accelerometer data from USB connection.

tried:
```
modprobe uinput & sudo sixad-raw /dev/hidraw0
```

But without sucess. I'm using Lucid btw. Sugestions?

---

### Post by emoguitarist06 on 2010-07-18
**Awesome! I am so excited about this thread and all the hard work you've done falkTX!**
I personally do not own a ps3 either but I love the controller as well and I have successfully installed and able to run ePSXe
and of course ZNES and plan on buying a DS3 to and follow this forum to get it to work.

[COLOR="Red"]1.[/COLOR] I just wanted to know do you still not own a ps3 falkTX?
[COLOR="red"]2.[/COLOR] What applications do you personally use your sixaxis for?
[COLOR="red"]3.[/COLOR] Which version are you running of Ubuntu?

Thanks Again and I'll report how well I do when I purchase the controller this friday.

I run Karmic BTW.
-Phillip

P.S. If I just borrowed a friends ps3 controller will it work?
(asking because idk if they actually pair and must unpair from the ps3)

---

### Post by asorron on 2010-07-18
Generally in order to pair a ps3 device (i got both dualshock 3 and sixaxis) youll need to connect the remote to your pc, pair them via usb (a little bit problematic for me for some reason but i managed to get over it) and then it will work flawlessly with the bluetooh. if you dont pair it with the usb it will still think its "master" device is the ps3 and when you try to press the ps button on it, it'll try to connect to the ps3 rather than the computer (it doesnt search, its really, as the word; paired. with the ps3)
so once you plugged it in and pair it, it wont connect to your ps3 again unless you connect it via usb to it (it'll pair it automaticly if im not wrong.)

---

### Post by emoguitarist06 on 2010-07-18
I bought the DS3 and I got it to work in ZNES by 
Settings>Configure Sixaxis>Profiles
Check use sixaxis as mouse/keyboard and using the Fake Joystick

However I cannot get it to work under ePSXe
I have not clue what to do.

Please help.

---

### Post by falkTX on 2010-07-19
> **asorron said:**
> OKAY I've found out the reason i got the broken pipes msgs. i told Sixpair to run by typing 
```
$sudo sixpair
```But after seeking a little bit at websites, iv'e found that i shoudl've run
```
$sudo ./sixpair/sixpair
```Its all working now, maybe thats the same reason the broken pipe msg appear on qtsixa too?

Also i noted that when letting it connect by accepting it without the force connection, it wont let it and just refresh it (looks like the windows program that iv'e got, it shows almost the same thing)

only using force will let the remote to connect :|

Lol, the real reason for the sixpair fix was that i fixed the code...
Didn't you noticed the update..?

For some computers the Sixaxis will only work in force mode.
That's the main reason it exists

---

### Post by falkTX on 2010-07-19
> **frs89 said:**
> I want to read accelerometer data from USB connection.

tried:
```
modprobe uinput & sudo sixad-raw /dev/hidraw0
```

But without sucess. I'm using Lucid btw. Sugestions?

hm, what is the output?

btw, the command should be:
```
sudo modprobe uinput && sudo sixad-raw /dev/hidraw0
```

---

### Post by falkTX on 2010-07-19
> **emoguitarist06 said:**
> **Awesome! I am so excited about this thread and all the hard work you've done falkTX!**
I personally do not own a ps3 either but I love the controller as well and I have successfully installed and able to run ePSXe
and of course ZNES and plan on buying a DS3 to and follow this forum to get it to work.

[COLOR="Red"]1.[/COLOR] I just wanted to know do you still not own a ps3 falkTX?
[COLOR="red"]2.[/COLOR] What applications do you personally use your sixaxis for?
[COLOR="red"]3.[/COLOR] Which version are you running of Ubuntu?

Thanks Again and I'll report how well I do when I purchase the controller this friday.

I run Karmic BTW.
-Phillip

P.S. If I just borrowed a friends ps3 controller will it work?
(asking because idk if they actually pair and must unpair from the ps3)

Thanks for the interest,

Answers:

1 - I don't have a PS3 yet...

2 - Many uses:
-> Controlling the desktop while I'm far from the pc ;)
-> Karaoke (UltraStar Deluxe)
-> PS1 Games
-> Making music (look at the new 'sixad-jack' utility)

3 - I run my own OS, "KXStudio" - [http://kxstudio.sourceforge.net/](http://kxstudio.sourceforge.net/)

---

### Post by falkTX on 2010-07-19
> **emoguitarist06 said:**
> I bought the DS3 and I got it to work in ZNES by 
Settings>Configure Sixaxis>Profiles
Check use sixaxis as mouse/keyboard and using the Fake Joystick

However I cannot get it to work under ePSXe
I have not clue what to do.

Please help.

You shouldn't use the ePSXe version for linux... too old and buggy...

Use the Windows version through Wine, rumble may work there, not sure

For [the windows] ePSXe you shouldn't use input profiles (like 'Fake Joystick'), just enable the Joystick and disable the accelerometers and sensitive buttons (useless for PS1 games).
Then on QtSixA, use the 'game profiles' tab, select ePSXe and apply.
ePSXe will be auto-configured!


If you really need a linux emulation app, go for PCSXR - [http://pcsxr.codeplex.com/](http://pcsxr.codeplex.com/)

---

### Post by Xenphor on 2010-07-19
Hello,

I tried the 1.5 beta in Lucid and was not able to get the profiles to work at all. I understand that this is not the latest stable version but just thought I would let you know. If this is already known then please disregard my post. Thanks.

---

### Post by emoguitarist06 on 2010-07-19
> **falkTX said:**
> You shouldn't use the ePSXe version for linux... too old and buggy...

Use the Windows version through Wine, rumble may work there, not sure

For [the windows] ePSXe you shouldn't use input profiles (like 'Fake Joystick'), just enable the Joystick and disable the accelerometers and sensitive buttons (useless for PS1 games).
Then on QtSixA, use the 'game profiles' tab, select ePSXe and apply.
ePSXe will be auto-configured!


If you really need a linux emulation app, go for PCSXR - [http://pcsxr.codeplex.com/](http://pcsxr.codeplex.com/)

**I got PCSXR and it works perfectly!** (couldn't get epsxe to install via wine... oh well)

You know... I am so happy right now. Playstation on my computer and bluetooth on sixaxxis.... this is the life!

One minor problem with sixad & pcsxr. On the Dpad when I press down it's really down-right and same for left it equals left up however the left joystick works great! Is it possible to disable the mouse movement for the left joystick and still allow it to work in pcsxr?

Edit: Ok I found that still the best way for me to use sixaxxis for pcsxr is still with fake joystick. I figured out that not only is the Left Dpad and Down Dpad problems but also the buttons. Like X is square, start is L2. I suppose I can live with it, some games are bearable like Castlevania but others like FF7 are note. I'll keep playing around with it but **does anyone know a solution?** (I think for now I'll play my ps1 games with my keyboard and use sixaxxis for znes)

---

### Post by Pipmeister. on 2010-07-20
I got my Sixasis connected after the update, thank you for writing such a great utility!

However, my keypad will not connect, when i try to pair it up the sixpair report simply states "No controller found on USB busses" despite the fact that the keyboard's address shows up on the list of devices.

Is this a bug in the new version or am I just doing it wrong?

---

### Post by falkTX on 2010-07-20
> **Pipmeister. said:**
> I got my Sixasis connected after the update, thank you for writing such a great utility!

However, my keypad will not connect, when i try to pair it up the sixpair report simply states "No controller found on USB busses" despite the fact that the keyboard's address shows up on the list of devices.

Is this a bug in the new version or am I just doing it wrong?

I tried to merge the sixpair for sixaxis and keypads (didn't work...)

For pairing keypads, please run:
```
sudo sixpair-kbd
```

This will be fixed soon

---

### Post by falkTX on 2010-07-20
> **emoguitarist06 said:**
> **I got PCSXR and it works perfectly!** (couldn't get epsxe to install via wine... oh well)

You know... I am so happy right now. Playstation on my computer and bluetooth on sixaxxis.... this is the life!

One minor problem with sixad & pcsxr. On the Dpad when I press down it's really down-right and same for left it equals left up however the left joystick works great! Is it possible to disable the mouse movement for the left joystick and still allow it to work in pcsxr?

Edit: Ok I found that still the best way for me to use sixaxxis for pcsxr is still with fake joystick. I figured out that not only is the Left Dpad and Down Dpad problems but also the buttons. Like X is square, start is L2. I suppose I can live with it lol. I'll keep playing around with it but **does anyone know a solution?** (I think for now I'll play my ps1 games with my keyboard and use sixaxxis for znes)

Heh? you can configure the buttons in PCSX-R...
Assign "right" to "right", "X" to "X", etc...

No need for input profiles there...

---

### Post by falkTX on 2010-07-20
> **Xenphor said:**
> Hello,

I tried the 1.5 beta in Lucid and was not able to get the profiles to work at all. I understand that this is not the latest stable version but just thought I would let you know. If this is already known then please disregard my post. Thanks.

Hm, profiles are working fine in Lucid, if you manage them in QtSixA.
(check other people posts...)

They are not available for USB though (yet)

---

### Post by Xenphor on 2010-07-22
Okay I was able to get the profiles to work with bluetooth. I now seem to be having an issue someone else was having with the mouse emulation. Instead of directly imitating the mouse movement, the cursors maintains a fixed position on the screen and the cursor moves relative to that position.

---

### Post by falkTX on 2010-07-22
> **Xenphor said:**
> Okay I was able to get the profiles to work with bluetooth. I now seem to be having an issue someone else was having with the mouse emulation. Instead of directly imitating the mouse movement, the cursors maintains a fixed position on the screen and the cursor moves relative to that position.

That is a known issue.
It happens when you use both joystick and input options for a sixaxis.

As a workaround, disable joystick and it will work as it should.

---

### Post by Xenphor on 2010-07-22
Ok now I got everything working pretty well. The only thing I would say is that the mouse emulation even at 1x is a bit too sensitve. For making large jumps arcross the monitor it's fine but for making little adjustments it is somewhat difficult. However what is there is much improved from the original. I don't know if this is possible, but if you could add a setting that is somewhere below 1x, it would be even better. Perhaps decreasing the deadzone would also help for making little adjustments with the joystick. Other than that though it is working very well. Thank you very much.


 edit: The scrolling is a bit too sensitive as well. Sorry for being such a pain but just want to see this program get better and better.

---

### Post by falkTX on 2010-07-23
> **Xenphor said:**
> Ok now I got everything working pretty well. The only thing I would say is that the mouse emulation even at 1x is a bit too sensitve. For making large jumps arcross the monitor it's fine but for making little adjustments it is somewhat difficult. However what is there is much improved from the original. I don't know if this is possible, but if you could add a setting that is somewhere below 1x, it would be even better. Perhaps decreasing the deadzone would also help for making little adjustments with the joystick. Other than that though it is working very well. Thank you very much.


 edit: The scrolling is a bit too sensitive as well. Sorry for being such a pain but just want to see this program get better and better.

I know about this,
the thing is that making them less sensitive can cause it not to work at all...

But I'll see what I can do

---

### Post by Xenphor on 2010-07-23
Well I don't know if you know about it, but the windows program Joy2key has the best mouse emulation I've ever used. You can go check it out here [http://electracode.com/4/joy2key/JoyToKey%20English%20Version.htm]("http://electracode.com/4/joy2key/JoyToKey%20English%20Version.htm") (assuming you have a windows installation of course). You'll have to check "Use other axes than X and Y" in the "Others" tab to the right. Then editing AxisX and AxisY to use cursor movements should give you mouse emulation. I set them around 50, -50 for X, Y and -X, -Y respectively. You can also edit them to give you a mouse scroll. 

Just thought it might help you to figure out what you might change for Qtsixa.

---

### Post by falkTX on 2010-07-23
> **Xenphor said:**
> Well I don't know if you know about it, but the windows program Joy2key has the best mouse emulation I've ever used. You can go check it out here [http://electracode.com/4/joy2key/JoyToKey%20English%20Version.htm](http://electracode.com/4/joy2key/JoyToKey%20English%20Version.htm) (assuming you have a windows installation of course). You'll have to check "Use other axes than X and Y" in the "Others" tab to the right. Then editing AxisX and AxisY to use cursor movements should give you mouse emulation. I set them around 50, -50 for X, Y and -X, -Y respectively. You can also edit them to give you a mouse scroll. 

Just thought it might give you something to think about.

Thanks.

I don't have windows, but I can test it in VirtualBox.

---

### Post by emoguitarist06 on 2010-07-23
> **falkTX said:**
> Heh? you can configure the buttons in PCSX-R...
Assign "right" to "right", "X" to "X", etc...

No need for input profiles there...

**Thank You!**

I don't know why but it took me Forever! to key map but I finally got it done :)
Everything is perfect now!
I guess I'll be back if I ever get a second controller or a keyboard :)

---

### Post by falkTX on 2010-07-23
> **emoguitarist06 said:**
> **Thank You!**

I don't know why but it took me Forever! to key map but I finally got it done :)
Everything is perfect now!
I guess I'll be back if I ever get a second controller or a keyboard :)

Beat my record and try to connect more than 4 sixaxis ;)

In theory only 7 sixaxis will work... but that may be false.
I would love to test this someday...

---

### Post by Chickenpope on 2010-07-25
Hey quick question, I have lucid and 1.2.1. I dont have bluetooth and was just going to hook up via usb. I can't seem to get any of the profiles working, its always default, also when making a profile what should i put for left click?

---

### Post by asorron on 2010-07-25
well another desperate move of me is attempting to get gh3 work in ubuntu which doesnt go lately, and it got me wondering.

Is there any ability to set 2 keys to 1 button on the controller? because i was used to the ps2/3 remote handling on that game (holding a color provides fretting it too, as in "Z+Space")

i might find it handy on some other games (since gh isnt showing ways of breathing any soon...)

Thanks again.

---

### Post by falkTX on 2010-07-26
> **Chickenpope said:**
> Hey quick question, I have lucid and 1.2.1. I dont have bluetooth and was just going to hook up via usb. I can't seem to get any of the profiles working, its always default, also when making a profile what should i put for left click?

on lucid, profiles are only working in bluetooth mode.
for usb-sixaxis, try using another tool - joy2key and qjoypad are 2 examples

---

### Post by falkTX on 2010-07-26
> **asorron said:**
> well another desperate move of me is attempting to get gh3 work in ubuntu which doesnt go lately, and it got me wondering.

Is there any ability to set 2 keys to 1 button on the controller? because i was used to the ps2/3 remote handling on that game (holding a color provides fretting it too, as in "Z+Space")

i might find it handy on some other games (since gh isnt showing ways of breathing any soon...)

Thanks again.

2 keys in 1 button is not supported anymore, sorry :(

Maybe some time later...

---

### Post by benmoran on 2010-07-30
This is my most watched project right now! The DualShock has such awesome potential, and you're making it happen! If you ever come to Tokyo, i'll buy you a beer.

---

### Post by falkTX on 2010-07-30
> **benmoran said:**
> This is my most watched project right now! The DualShock has such awesome potential, and you're making it happen! If you ever come to Tokyo, i'll buy you a beer.

hehe, thanks!

but I don't think I'll go to Tokyo any time soon...

---

### Post by Xenphor on 2010-08-09
I actually noticed one more thing regarding mouse sensitivity. I had always been using the right stick for the mouse because I am right handed. However, I recently used a configuration that had the mouse on the left stick and noticed that it was much easier to control even though the axis speed multiplier was at 6x. It seems that the left stick is operating with different parameters when adjusting sensitivity. I think all you would have to do is allow the right stick to operate the same way, because even if I dropped the multiplier down to 1x, the right stick was still harder to control than the left one at 6x. I hope this makes sense.

---

### Post by falkTX on 2010-08-09
> **Xenphor said:**
> I actually noticed one more thing regarding mouse sensitivity. I had always been using the right stick for the mouse because I am right handed. However, I recently used a configuration that had the mouse on the left stick and noticed that it was much easier to control even though the axis speed multiplier was at 6x. It seems that the left stick is operating with different parameters when adjusting sensitivity. I think all you would have to do is allow the right stick to operate the same way, because even if I dropped the multiplier down to 1x, the right stick was still harder to control than the left one at 6x. I hope this makes sense.

Thanks for the info,

I'll look into the axis code soon,
hopefully to make it work more consistent

---

### Post by csbvs on 2010-08-11
Hello,
I have been trying to connect my ps3 sixaxis via the usb port (bluetooth seems a bit more complicated and I figured I'd start slow). I am using qtsixa, when I plug in the controller the four LEDs begin flashing and qtsixa rocognizes that a controller is plugged in. However, when I press the PS button nothing changes, my computer does not recognize the controller inputs. The profile properties of the qtsixa reads "ED: Yes | Joystick: Yes | Input: No. I was just wondering what else can I do/try to make the controller connect. I have spent many hours doing google searches of this topic but everything I can find relates to connecting the controller via bluetooth. I'm running ubuntu 10.04. Any help would be much appreciated.
-csbvs

---

### Post by madrang on 2010-08-11
Hi,

I have the same problem as csbvs. Pairing did work but no input at all... when i unplug the usb wire the controller connect to Bluetooth do the little led anim and rumble, after P1 led stay on but no input at all in Joy or Input mode.

Also i have a keypad and no problem with it at all, except the track-pad thing is a little too fast but didn't buy it for that.

Keypad : CECHZK1UC
Controller : CECHZC2U
QtSixA : 1.5.0 (from launchpad repo)
Ubuntu : 10.4 Lucid + Pre-released update

---

### Post by falkTX on 2010-08-11
Hm, for USB mode, the Sixaxis should work out-of-the-box.
QtSixA is not needed to use the Sixaxis on USB.

For bluetooth, you have to pair it first (as you already did).
When the joystick connects, it will by default rumble, animate the LEDs and stay on #1.
The default setup is to use the Sixaxis as a Joystick, with no mouse/keyboard emulation.

you can test if this is working by running:
```
sixad --stop #stops the sixaxis driver
sixad --start #starts the driver again, all debug messages are shown

``` At this point you press the PS button on the Sixaxis and it will connect.
You'll see some output on the terminal, saying that the sixaxis is activated, and what config it's using (or if using default).

On the config output, make sure you got (at least) joystick mode enabled:
> (...)
--- Features ---
enable_leds 1
**enable_joystick 1**
enable_input 0
(...)
--- Joystick ---
enable_buttons 1
enable_sbuttons 1
enable_axis 1
(...)


In another terminal run this to test if the sixaxis is working:
```
jstest /dev/input/js0
```
If you see any values moving when you press some keys, then it's working!


As for the keypad, yes, the trackpad is weird...
Using in keyboard mode works fine though, and you can already use the sixaxis as mouse, so...

---

### Post by madrang on 2010-08-11
```
sixad[1274]: Connected PLAYSTATION(R)3 Controller (00:23:06:C8:8D:7F)
sixad[1274]: Debug mode active
This is your configuration:

--- Features ---
enable_leds 1
enable_joystick 1
enable_input 0

--- LED ---
led_n_auto 1
led_n_number 1
led_anim 1

--- Joystick ---
enable_buttons 1
enable_sbuttons 1
enable_axis 1
enable_accel 1
enable_accon 0
enable_speed 0
enable_pos 0
enable_rumble 1

--- Misc ---
enable_timeout 0
timeout_mins 30
use_lr3 0
```

---I didn't post the Input section.

i installed jstest and it dosent work as it seams that the controller dont send update or somthing like that

```
Axes:  0:     0  1:     0  2:     0  3:     0  4:     0  5:     0  6:     0  7:     0  8:     0  9:     0 10:     0 11:     0 12:     0 13:     0 14:     0 15:     0 16:     0 17:     0 18:     0 19:     0 20:     0 21:     0 22:     0 23:     0 24:     0 25:     0 26:     0 27:     0 28:     0 Buttons:  0:off  1:off  2:off  3:off  4:off  5:off  6:off  7:off  8:off  9:off 10:off 11:off 12:off 13:off 14:off 15:off 16:offAxes:  0:     0  1:     0  2:     0  3:     0  4:-32767  5:     0  6:     0  7:     0  8:     0  9:     0 10:     0 11:     0 12:     0 13:     0 14:     0 15:     0 16:     0 17:     0 18:     0 19:     0 20:     0 21:     0 22:     0 23:     0 24:     0 25:     0 26:     0 27:     0 28:     0 Buttons:  0:off  1:off  2:off  3:off  4:off  5:off  6:off  7:off  8:off  9:off 10:off 11:off 12:off 13:off 14:off 15:off 16:offAxes:  0:     0  1:     0  2:     0  3:     0  4:-32767  5: 32767  6:     0  7:     0  8:     0  9:     0 10:     0 11:     0 12:     0 13:     0 14:     0 15:     0 16:     0 17:     0 18:     0 19:     0 20:     0 21:     0 22:     0 23:     0 24:     0 25:     0 26:     0 27:     0 28:     0 Buttons:  0:off  1:off  2:off  3:off  4:off  5:off  6:off  7:off  8:off  9:off 10:off 11:off 12:off 13:off 14:off 15:off 16:offAxes:  0:     0  1:     0  2:     0  3:     0  4:-32767  5: 32767  6: 32767  7:
```

the first are all zero then the value change like shown and after that they are all the same BUT all of them write as soon as i hit enter to send the cmd after no more line are added and nothing move...

then i used wireshark to listen to my Bus 003 Device 002: ID 0a12:0001 Cambridge Silicon Radio, Ltd Bluetooth Dongle (HCI mode) and the computer dont recive URB_INTERRUPT when i press a key(like when i listen to my mouse.), but at random interval there is 2 URB_CONTROL and 2 URB_INTERRUPT 1 sent and 1 received for each.

```
No.     Time        Source                Destination           Protocol Info
  35851 514.021507  2.1                   host                  USB      URB_INTERRUPT

Frame 35851 (15 bytes on wire, 15 bytes captured)
USB URB

No.     Time        Source                Destination           Protocol Info
  35852 514.021513  host                  2.1                   USB      URB_INTERRUPT[Packet size limited during capture]

Frame 35852 (24 bytes on wire, 8 bytes captured)
USB URB
[Packet size limited during capture: USB truncated]

No.     Time        Source                Destination           Protocol Info
  35853 514.027270  host                  2.0                   USB      URB_CONTROL

Frame 35853 (18 bytes on wire, 18 bytes captured)
USB URB

No.     Time        Source                Destination           Protocol Info
  35854 514.028508  2.0                   host                  USB      URB_CONTROL[Packet size limited during capture]

Frame 35854 (18 bytes on wire, 8 bytes captured)
USB URB
[Packet size limited during capture: USB truncated]

No.     Time        Source                Destination           Protocol Info
  35855 514.029505  2.1                   host                  USB      URB_INTERRUPT

Frame 35855 (18 bytes on wire, 18 bytes captured)
USB URB

No.     Time        Source                Destination           Protocol Info
  35856 514.029509  host                  2.1                   USB      URB_INTERRUPT[Packet size limited during capture]

Frame 35856 (24 bytes on wire, 8 bytes captured)
USB URB
[Packet size limited during capture: USB truncated]

No.     Time        Source                Destination           Protocol Info
  35857 514.029521  host                  2.0                   USB      URB_CONTROL

Frame 35857 (11 bytes on wire, 11 bytes captured)
USB URB

No.     Time        Source                Destination           Protocol Info
  35858 514.031504  2.0                   host                  USB      URB_CONTROL[Packet size limited during capture]

Frame 35858 (11 bytes on wire, 8 bytes captured)
USB URB
[Packet size limited during capture: USB truncated]

No.     Time        Source                Destination           Protocol Info
  35859 514.032504  2.1                   host                  USB      URB_INTERRUPT

Frame 35859 (22 bytes on wire, 22 bytes captured)
USB URB

No.     Time        Source                Destination           Protocol Info
  35860 514.032507  host                  2.1                   USB      URB_INTERRUPT[Packet size limited during capture]

Frame 35860 (24 bytes on wire, 8 bytes captured)
USB URB
[Packet size limited during capture: USB truncated]

No.     Time        Source                Destination           Protocol Info
  35861 514.032533  host                  2.0                   USB      URB_CONTROL

Frame 35861 (11 bytes on wire, 11 bytes captured)
USB URB

No.     Time        Source                Destination           Protocol Info
  35862 514.034505  2.0                   host                  USB      URB_CONTROL[Packet size limited during capture]

Frame 35862 (11 bytes on wire, 8 bytes captured)
USB URB
[Packet size limited during capture: USB truncated]
```

---

### Post by falkTX on 2010-08-11
> **madrang said:**
> 
then i used wireshark to listen to my Bus 003 Device 002: ID 0a12:0001 Cambridge Silicon Radio, Ltd Bluetooth Dongle (HCI mode) and the computer dont recive URB_INTERRUPT when i press a key(like when i listen to my mouse.), but at random interval there is 2 URB_CONTROL and 2 URB_INTERRUPT 1 sent and 1 received for each.


You seem to have done everything correctly,
hm...

Can you test with a different bluetooth stick?
thanks

---

### Post by madrang on 2010-08-11
at the moment i don't have an other Bluetooth key but i think the right thing to do at the moment would be to make it work in usb and try wireless after. in lsusb it show as Bus 003 Device 006: ID 054c:0268 Sony Corp. Batoh Device
again no luck with jstest BUT with wireshark i can see a lot of  URB_INTERRUPT and the data change as i press some keys and move the pad.
this pad do work with my ps3 and my Bluetooth key work with all the cellphone i ever tried on it.

Linux UberBox 2.6.32-24-generic #39-Ubuntu SMP Wed Jul 28 05:14:15 UTC 2010 x86_64 GNU/Linux

can it all be related to the driver included with the kernel ??

---

### Post by falkTX on 2010-08-12
> **madrang said:**
> at the moment i don't have an other Bluetooth key but i think the right thing to do at the moment would be to make it work in usb and try wireless after. in lsusb it show as Bus 003 Device 006: ID 054c:0268 Sony Corp. Batoh Device
again no luck with jstest BUT with wireshark i can see a lot of  URB_INTERRUPT and the data change as i press some keys and move the pad.
this pad do work with my ps3 and my Bluetooth key work with all the cellphone i ever tried on it.

Linux UberBox 2.6.32-24-generic #39-Ubuntu SMP Wed Jul 28 05:14:15 UTC 2010 x86_64 GNU/Linux

can it all be related to the driver included with the kernel ??

hm, are you saying that the Sixaxis doesn't actually work on USB mode?
That would really weird...

If the Sixaxis can't work properly on USB, it will probably not work on bluetooth mode too.

And the kernel you're using is fine, I used it for some time before (now testing 2.6.35, which works too)

---

### Post by ratty on 2010-08-18
I'm having the same issue as above. Works perfectly under USB. But over bluetooth everything appears to work. Lights animate then stop on #1, rumbles but jstest shows no activity when I press the buttons.

Also the signal quality and battery status are both 0 in QtSixa, not sure if this is normal.

I've tried 2 different bluetooth dongles. Controller is just a few months old, dualshock 3 model number CHECHZC2A.

Perhaps an issue with this specific model?

And tips on debugging this would be helpful. Can I see raw bluetooth activity somehow?

Cheers,
Ryan

---

### Post by falkTX on 2010-08-18
> **ratty said:**
> I'm having the same issue as above. Works perfectly under USB. But over bluetooth everything appears to work. Lights animate then stop on #1, rumbles but jstest shows no activity when I press the buttons.

Also the signal quality and battery status are both 0 in QtSixa, not sure if this is normal.

I've tried 2 different bluetooth dongles. Controller is just a few months old, dualshock 3 model number CHECHZC2A.

Perhaps an issue with this specific model?

And tips on debugging this would be helpful. Can I see raw bluetooth activity somehow?

Cheers,
Ryan

This seems to be happening a lot recently... :(

hm... you can use 'hcidump' to dump data from *all* bluetooth activity.
(can't remember the best arguments used to see more useful data....)

If 'hcidump' does not print anything, then the pc it's not getting anything from the sixaxis, which is really bad...

---

### Post by ratty on 2010-08-18
I tried hcidump -x to dump values as hex. It's sending data as I can see the values changing as I press buttons/move sticks.

If it's any use here's the activity when making the initial connection:

[http://pastebin.com/raw.php?i=rJfMd81j](http://pastebin.com/raw.php?i=rJfMd81j)

And a random chunk of data I get while pressing buttons and stuff:

[http://pastebin.com/raw.php?i=Jic7q84d](http://pastebin.com/raw.php?i=Jic7q84d)

---

### Post by falkTX on 2010-08-18
> **ratty said:**
> I tried hcidump -x to dump values as hex. It's sending data as I can see the values changing as I press buttons/move sticks.

If it's any use here's the activity when making the initial connection:

[http://pastebin.com/raw.php?i=rJfMd81j](http://pastebin.com/raw.php?i=rJfMd81j)

And a random chunk of data I get while pressing buttons and stuff:

[http://pastebin.com/raw.php?i=Jic7q84d](http://pastebin.com/raw.php?i=Jic7q84d)

Can you try using the old QtSixA version?
(just to check if it's a problem with the new code)

[https://sourceforge.net/projects/qtsixa/files/](https://sourceforge.net/projects/qtsixa/files/)
(1.2.1b for lucid)


Please restart the pc, just to be sure

---

### Post by ratty on 2010-08-18
I used 1.2.1b previous to the 1.5beta and it only worked on USB then too. Same problem as I have now. So I guess it's not caused by new code.

---

### Post by falkTX on 2010-08-18
> **ratty said:**
> I used 1.2.1b previous to the 1.5beta and it only worked on USB then too. Same problem as I have now. So I guess it's not caused by new code.

Yep, this is really weird...
'hcidump' reports data, so it should be working... :mad:

Maybe it's a new/different model ??

I have 1 Sixaxis and 1 DualShock3, they both work fine.
I'll check the specific model when I get home

---

### Post by ratty on 2010-08-18
Well if there's any data I can dump to help then let me know.

---

### Post by asorron on 2010-08-18
just wondering...
how about adding a device such as steering wheel / guitar hero controllers (mic / guitar / drums) support to the program? never tried it though but i wonder if it'll work with the ps3 set.

---

### Post by falkTX on 2010-08-18
> **asorron said:**
> just wondering...
how about adding a device such as steering wheel / guitar hero controllers (mic / guitar / drums) support to the program? never tried it though but i wonder if it'll work with the ps3 set.

Yep, I'll do that as soon as I get my hand on one. ;)

There's a Wii-like controller coming out soon...

---

### Post by megamanexent on 2010-08-18
Hey, got to say thank you for such an awesome application!
But I'm getting an error when I run sixad
```
/usr/bin/sixad: line 59:  9356 Segmentation fault      sudo /usr/sbin/sixad-bin $DEBUG

```

I'm running:

BlueZ 4.69
QtSixa 1.4.90
sixad reports it version 1.5.0
kernel 2.6.33-020633-generic
Ubuntu 10.04 Lucid Lynx

The GUI work flawlessly though!

---

### Post by falkTX on 2010-08-19
> **megamanexent said:**
> Hey, got to say thank you for such an awesome application!
But I'm getting an error when I run sixad
```
/usr/bin/sixad: line 59:  9356 Segmentation fault      sudo /usr/sbin/sixad-bin $DEBUG

```

I'm running:

BlueZ 4.69
QtSixa 1.4.90
sixad reports it version 1.5.0
kernel 2.6.33-020633-generic
Ubuntu 10.04 Lucid Lynx

The GUI work flawlessly though!

Nice found...

Just delete the old ~/.qtsixa folder and it then should be working again.
I'll fix this soon.

---

### Post by megamanexent on 2010-08-19
> **falkTX said:**
> Nice found...

Just delete the old ~/.qtsixa folder and it then should be working again.
I'll fix this soon.
Wow, I can't believe it was that simple. Thank you!!

If you ever need some help testing, I can help. I have a DS3 so Rumble testing I can defiantly help with.

---

### Post by falkTX on 2010-08-19
> **megamanexent said:**
> Wow, I can't believe it was that simple. Thank you!!

If you ever need some help testing, I can help. I have a DS3 so Rumble testing I can defiantly help with.

Hehe, sometimes I forgot the about some old small stuff...


Just tell me how it works.
I would except "normal" :lolflag:


Does anyone knows a Linux game with rumble support?
Maybe Wine supports it... ?

---

### Post by megamanexent on 2010-08-20
Oh it is working "normally"! :)

I wish I knew any games that support rumble for linux or windows, but I do not

---

### Post by dbzkid on 2010-08-20
hello,
I've been wondering I have gotten this to work with usb, but with blue-tooth it connects and I get the led's to function properly but it doesn't want to do anything with the buttons, nothing seems to function. has anyone had this problem, I am using a cheap blue-tooth dongle though I don't know if this could be the problem.
--Thanks
--Kevin

---

### Post by falkTX on 2010-08-20
> **dbzkid said:**
> hello,
I've been wondering I have gotten this to work with usb, but with blue-tooth it connects and I get the led's to function properly but it doesn't want to do anything with the buttons, nothing seems to function. has anyone had this problem, I am using a cheap blue-tooth dongle though I don't know if this could be the problem.
--Thanks
--Kevin

Hi, some other people have been complaining about the same thing...

I'm not sure why some Sixaxis are working and some are not,
but I'll look deeply into it this weekend.

I'll let you guys know how it goes

---

### Post by dbzkid on 2010-08-20
Thank you very much, and thank you for the quick reply. Great application, It works perfect when you use it through usb, so I will use it that way. Again Thank you! and I was using the 1.5 beta on Ubuntu 10.04

--Kevin

**Edit**
found out that with the new 1.5 beta, usb isnt working more precicely hidraw, when i go to the advanced tab, and choose to activate the hidraw on device hidraw0 (should be the sixaxis) it tells me this 
> The sixad driver could not start.
Are you sure you selected a Sixaxis?. I run it in terminal and i get this every time i try that feature
```
WARNING: All config files need .conf: /etc/modprobe.d/blacklist, it will be ignored in a future release.

```
what strangeness, and i used version 1.2 and it worked fine connected to usb

---

### Post by dbrenha on 2010-08-22
awesome application! i have just managed to connect the keypad to my pc (not sure how i did it but it happened the 3rd time i tried). i only have one question, is it possible to assign the buttons to the left and right "mouse" button to "ctrl" an "alt"?

---

### Post by Xenphor on 2010-08-22
I was wondering if you would ever consider releasing a version for other distributions of Linux such as Fedora or something similar? If not, is it possible to compile the program on other distros and how difficult would that be? Do you have instructions for compiling (I did not see anything on the website or in the source)?

---

### Post by falkTX on 2010-08-23
> **dbzkid said:**
> Thank you very much, and thank you for the quick reply. Great application, It works perfect when you use it through usb, so I will use it that way. Again Thank you! and I was using the 1.5 beta on Ubuntu 10.04

--Kevin

**Edit**
found out that with the new 1.5 beta, usb isnt working more precicely hidraw, when i go to the advanced tab, and choose to activate the hidraw on device hidraw0 (should be the sixaxis) it tells me this 
. I run it in terminal and i get this every time i try that feature
```
WARNING: All config files need .conf: /etc/modprobe.d/blacklist, it will be ignored in a future release.

```
what strangeness, and i used version 1.2 and it worked fine connected to usb

There are still missing pieces on the new 1.5.0 (beta) version.

In this case, you probably need to activate the uinput module first, like this:
```
sudo modprobe uinput
sudo sixad-raw /dev/hidrawX

```
;)

---

### Post by falkTX on 2010-08-23
> **dbrenha said:**
> awesome application! i have just managed to connect the keypad to my pc (not sure how i did it but it happened the 3rd time i tried). i only have one question, is it possible to assign the buttons to the left and right "mouse" button to "ctrl" an "alt"?

Re-assign buttons on the keypad is not possible,
it just goes with the default driver (it works, so...)

---

### Post by falkTX on 2010-08-23
> **Xenphor said:**
> I was wondering if you would ever consider releasing a version for other distributions of Linux such as Fedora or something similar? If not, is it possible to compile the program on other distros and how difficult would that be? Do you have instructions for compiling (I did not see anything on the website or in the source)?

Of course it's possible, but I will not be the one to do it, I'll need help.
Someone already package it for ArchLinux (1.2.1 version) and there's a maemo package around the web

Compiling the application for other distros is not hard, as long as you have the required build dependencies.
Just install them (bluez, python, pyqt, libusb) and run "make" on the source tree.

EDIT: and, of course, 'make install' to install it.
*(I once tested 1.2.1 on OpenSUSE, it worked fine)*

---

### Post by ratty on 2010-08-26
Did you get anywhere on finding out why some controllers don't work?

---

### Post by falkTX on 2010-08-26
> **ratty said:**
> Did you get anywhere on finding out why some controllers don't work?

Sorry I have been busy with some of my other projects (they have a deadline for next week...)

But I can already tell you my 1st plan:
make a new binary/script that will simply connect a sixaxis and report back info from it (testing rumble, axes, leds, etc).
That will me us figuring out why it's not working

---

### Post by Xenphor on 2010-08-28
I've been running the 1.5 beta for awhile and then recently tried the 1.2 debs that you have supplied. It seems that the 1.2 version actually has some more features like starting the sixad at boot which I would really like to have in 1.5 beta. I would use 1.2 but for some reason it won't work. If I load sixad, the controller will connect but I can't do anything with it. For this reason I was wondering if you had any plans to include starting sixad at boot in future versions?

If that's not possible then I would like to be able to enable sixad without having to input my password every time. Would this be possible by changing permissions on some of the files? I tried adding myself as a group owner of the qtsixa folder and the sixad files in sbin but it still asked me for a password.

---

### Post by falkTX on 2010-08-30
> **Xenphor said:**
> I've been running the 1.5 beta for awhile and then recently tried the 1.2 debs that you have supplied. It seems that the 1.2 version actually has some more features like starting the sixad at boot which I would really like to have in 1.5 beta. I would use 1.2 but for some reason it won't work. If I load sixad, the controller will connect but I can't do anything with it. For this reason I was wondering if you had any plans to include starting sixad at boot in future versions?

If that's not possible then I would like to be able to enable sixad without having to input my password every time. Would this be possible by changing permissions on some of the files? I tried adding myself as a group owner of the qtsixa folder and the sixad files in sbin but it still asked me for a password.

The option to start sixad at boot is there (just not in the GUI yet), just run:
```
sudo sixad --boot-yes
```to enable it.

and sixad needs access to raw bluetooth data, so it will always need root/password...

---

### Post by Xenphor on 2010-08-30
> **falkTX said:**
> The option to start sixad at boot is there (just not in the GUI yet), just run:
```
sudo sixad --boot-yes
```to enable it.

and sixad needs access to raw bluetooth data, so it will always need root/password...

 Would that also work coming off a suspend? Because that would be really nice to have as well. (I don't have access to my ubuntu computer at the moment to test).

---

### Post by falkTX on 2010-08-31
> **Xenphor said:**
> Would that also work coming off a suspend? Because that would be really nice to have as well. (I don't have access to my ubuntu computer at the moment to test).

hm... I haven't tested suspend/resume (sometimes my laptop can't wake up, so I just don't do it)

But,
if 'sixad' gets stuck - 50% usage and doing nothing -, just stop it and start it again manually:
```
sudo sixad --sotp
sudo sixad --start

```

---

### Post by trumee on 2010-09-02
Hi falkTX,

I have been using sixaxis controller paired with Nokia N900 and it has been working quite well. However if two controllers are paired at the same time then the touchscreen of the N900 stops taking input. It behaves as if somebody is pressing down a button all the time.

The sixaxis code for N900 sits at [http://repository.maemo.org/extras/pool/fremantle/free/source/q/qtsixa/qtsixa_1.3.0-0maemo2.tar.gz](http://repository.maemo.org/extras/pool/fremantle/free/source/q/qtsixa/qtsixa_1.3.0-0maemo2.tar.gz)

Would you be able to investigate this?

---

### Post by falkTX on 2010-09-02
> **trumee said:**
> Hi falkTX,

I have been using sixaxis controller paired with Nokia N900 and it has been working quite well. However if two controllers are paired at the same time then the touchscreen of the N900 stops taking input. It behaves as if somebody is pressing down a button all the time.

The sixaxis code for N900 sits at [http://repository.maemo.org/extras/pool/fremantle/free/source/q/qtsixa/qtsixa_1.3.0-0maemo2.tar.gz](http://repository.maemo.org/extras/pool/fremantle/free/source/q/qtsixa/qtsixa_1.3.0-0maemo2.tar.gz)

Would you be able to investigate this?

hm... I dont have that phone to test it...

AFAIK, that version (1.3.0) is based on my QtSixA 1.2.1 with a few small changes (to make it work properly on N900).

can you try to disable all kind of input (buttons, axis, etc), in the file '20-x11-sony-sixaxis' ? (reboot might be required)

---

### Post by trumee on 2010-09-03
Ok, i commented out all the input lines in the fdi file and paired both the controllers. Ofcourse, now the phone doesnt register any of the controllers key but the touchscreen is now fully usable. So is some input key the cause of the problem?

The commented fdi file looks like this
```

<?xml version="1.0" encoding="UTF-8"?>
<deviceinfo version="0.2">
  <device>
    <!-- Sixaxis configuration for Fake-Joystick Use (Keyboard) -->
    <match key="input.product" contains="PLAYSTATION(R)3 Controller">

     <merge key="input.x11_driver" type="string">joystick</merge>

     <match key="info.udi" contains="input_1">
<!--
      <!-- Main Axis. Left=Mouse; Right=Scroll -->
      <merge key="input.x11_options.MapAxis1" type="string">mode=relative axis=+2x deadzone=5000</merge>
      <merge key="input.x11_options.MapAxis2" type="string">mode=relative axis=+2y deadzone=5000</merge>
      <merge key="input.x11_options.MapAxis3" type="string">mode=relative axis=+1zx deadzone=7500</merge>
      <merge key="input.x11_options.MapAxis4" type="string">mode=relative axis=+1zy deadzone=7500</merge>
      <merge key="input.x11_options.MapAxis5" type="string">mode=none</merge>
      <merge key="input.x11_options.MapAxis6" type="string">mode=none</merge>
      <merge key="input.x11_options.MapAxis7" type="string">mode=none</merge>
      <merge key="input.x11_options.MapAxis8" type="string">mode=none</merge>

      <!-- Select=SPACE; Start=ENTER; PS=D. -->
      <merge key="input.x11_options.MapButton1" type="string">key=65</merge>
      <merge key="input.x11_options.MapButton2" type="string">none</merge>
      <merge key="input.x11_options.MapButton3" type="string">none</merge>
      <merge key="input.x11_options.MapButton4" type="string">key=36</merge>
      <merge key="input.x11_options.MapButton17" type="string">key=40</merge>

      <!-- Direcctional keys (Up, Down, Left & Right) -->
      <merge key="input.x11_options.MapButton5" type="string">key=111</merge>
      <merge key="input.x11_options.MapButton8" type="string">key=113</merge>
      <merge key="input.x11_options.MapButton6" type="string">key=114</merge>
      <merge key="input.x11_options.MapButton7" type="string">key=116</merge>

      <!-- R2=R; L2=Q; R1=E; L1=W -->
      <merge key="input.x11_options.MapButton10" type="string">key=27</merge>
      <merge key="input.x11_options.MapButton9" type="string">key=24</merge>
      <merge key="input.x11_options.MapButton12" type="string">key=26</merge>
      <merge key="input.x11_options.MapButton11" type="string">key=25</merge>

      <!-- X=Z; O=X; []=A; &#916;=S -->
      <merge key="input.x11_options.MapButton15" type="string">key=52</merge>
      <merge key="input.x11_options.MapButton14" type="string">key=53</merge>
      <merge key="input.x11_options.MapButton16" type="string">key=38</merge>
      <merge key="input.x11_options.MapButton13" type="string">key=39</merge>
-->
     </match>

     <match key="info.udi" contains="input_2">
<!--
      <!-- Select=P; Start=,; PS=I -->
      <merge key="input.x11_options.MapButton1" type="string">key=33</merge>
      <merge key="input.x11_options.MapButton2" type="string">none</merge>
      <merge key="input.x11_options.MapButton3" type="string">none</merge>
      <merge key="input.x11_options.MapButton4" type="string">key=59</merge>
      <merge key="input.x11_options.MapButton17" type="string">key=31</merge>

      <!-- Direcctional keys (^=O, v=L, <=K, >=.) -->
      <merge key="input.x11_options.MapButton5" type="string">key=32</merge>
      <merge key="input.x11_options.MapButton6" type="string">key=60</merge>
      <merge key="input.x11_options.MapButton7" type="string">key=46</merge>
      <merge key="input.x11_options.MapButton8" type="string">key=45</merge>

      <!-- R2=U; L2=G; R1=Y; L1=T -->
      <merge key="input.x11_options.MapButton10" type="string">key=30</merge>
      <merge key="input.x11_options.MapButton9" type="string">key=42</merge>
      <merge key="input.x11_options.MapButton12" type="string">key=29</merge>
      <merge key="input.x11_options.MapButton11" type="string">key=28</merge>

      <!-- X=N; O=M; []=H; &#916;=J -->
      <merge key="input.x11_options.MapButton15" type="string">key=57</merge>
      <merge key="input.x11_options.MapButton14" type="string">key=58</merge>
      <merge key="input.x11_options.MapButton16" type="string">key=43</merge>
      <merge key="input.x11_options.MapButton13" type="string">key=44</merge>
-->
     </match>

    </match>
  </device>
</deviceinfo>




```

---

### Post by nominal on 2010-09-03
so what does this mean?

> sudo sixad -start
***** NOTICE *****
You're using a very old bluetooth dongle,
the Sixaxis will not work properly!

/usr/bin/sixad: line 59: 22128 Segmentation fault      sudo /usr/sbin/sixad-bin $DEBUG


---from my other post:

"You're using a very old bluetooth dongle,
the Sixaxis will not work properly!"

I get that message every time i start the daemon. And it's right, my ps3 controller won't work properly. It'll connect via bluetooth, and then...the '1' spot on the ps3 controller lights up, but then my laptop doesn't seem to receiving any input from the controller.

So...what can I do?

lsusb: > Bus 002 Device 002: ID 0a12:0001 Cambridge Silicon Radio, Ltd Bluetooth Dongle (HCI mode)

dmesg: > [   18.037711] Bluetooth: L2CAP ver 2.14
[   18.037715] Bluetooth: L2CAP socket layer initialized
[   18.121282] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   18.121285] Bluetooth: BNEP filters: protocol multicast
[   18.243020] Bridge firewalling registered
[   18.249519] ppdev: user-space parallel port driver
[   18.260709] Bluetooth: SCO (Voice Link) ver 0.6
[   18.260713] Bluetooth: SCO socket layer initialized
[   19.273008] Bluetooth: RFCOMM TTY layer initialized
[   19.273014] Bluetooth: RFCOMM socket layer initialized
[   19.273017] Bluetooth: RFCOMM ver 1.11

---

### Post by frs89 on 2010-09-04
@falkTx

Sixad-raw is working in 1.5.0b?

I get this from QtSixa:
 > 
The sixad driver could not start.
 Are you sure you selected a Sixaxis?
I've tried via terminal and sixad-raw freezes until I unplug the sixaxis or kill the application. I ensured that uinput was activated.

---

### Post by falkTX on 2010-09-05
> **trumee said:**
> Ok, i commented out all the input lines in the fdi file and paired both the controllers. Ofcourse, now the phone doesnt register any of the controllers key but the touchscreen is now fully usable. So is some input key the cause of the problem?

The commented fdi file looks like this
[CODE]
<?xml version="1.0" encoding="UTF-8"?>
<deviceinfo version="0.2">
...

I believe so,

please try to enable one by one (I know it's a lot of work...) and check which specific button/axis causes the freeze.

Thanks!

---

### Post by falkTX on 2010-09-05
> **nominal said:**
> so what does this mean?



---from my other post:

"You're using a very old bluetooth dongle,
the Sixaxis will not work properly!"

I get that message every time i start the daemon. And it's right, my ps3 controller won't work properly. It'll connect via bluetooth, and then...the '1' spot on the ps3 controller lights up, but then my laptop doesn't seem to receiving any input from the controller.

So...what can I do?

lsusb: 

dmesg:

Hehe, someone failed the first test...
Basically that message means the Sixaxis won't work :(

You'll have to use another bluetooth dongle/pen/stick
(some that supports, at least, the bluetooth v2.0 standard)

---

### Post by nominal on 2010-09-05
> **falkTX said:**
> Hehe, someone failed the first test...
Basically that message means the Sixaxis won't work :(

You'll have to use another bluetooth dongle/pen/stick
(some that supports, at least, the bluetooth v2.0 standard)

hahaha nooooo. am I the first person to fail the first test?

I thought it had bluetooth 2.0...oh well. Another is on the way!

---

### Post by trumee on 2010-09-12
> **falkTX said:**
> I believe so,

please try to enable one by one (I know it's a lot of work...) and check which specific button/axis causes the freeze.

Thanks!

Hi falkTX,

I took me a while to test the keys out. But i have spotted the key which is the cause of this issue. It is the Select key of the second controller.
```


     <match key="info.udi" contains="input_2">

      <!-- Select=P; Start=,; PS=I -->
      **<merge key="input.x11_options.MapButton1" type="string">key=33</merge>**
      <merge key="input.x11_options.MapButton2" type="string">none</merge>      


```The key is currently mapped to 'p' which has a scan code of 33. I modified it to 55 which is the scancode for 'v' but it did not help. When i disable this key, the N900 behaves properly. The scan codes are listed at [http://talk.maemo.org/showpost.php?p=517534&postcount=220](http://talk.maemo.org/showpost.php?p=517534&postcount=220)

Any suggestions?

---

### Post by Xenphor on 2010-09-12
I was wondering, is there a way to "Disconnect all Sixaxis" or "Disconnect all Devices" through the terminal? Thanks.

---

### Post by falkTX on 2010-09-13
> **trumee said:**
> Hi falkTX,

I took me a while to test the keys out. But i have spotted the key which is the cause of this issue. It is the Select key of the second controller.
```


     <match key="info.udi" contains="input_2">

      <!-- Select=P; Start=,; PS=I -->
      **<merge key="input.x11_options.MapButton1" type="string">key=33</merge>**
      <merge key="input.x11_options.MapButton2" type="string">none</merge>      


```The key is currently mapped to 'p' which has a scan code of 33. I modified it to 55 which is the scancode for 'v' but it did not help. When i disable this key, the N900 behaves properly. The scan codes are listed at [http://talk.maemo.org/showpost.php?p=517534&postcount=220](http://talk.maemo.org/showpost.php?p=517534&postcount=220)

Any suggestions?


Can you check if that key works properly in other scenarios (PS3, PC, etc) ?

If you know coding (sixad is written in C), check if there's any difference between the Start and Select buttons code.



I'll finish some of my other projects next week, so then I'll have some time to focus on QtSixA.

---

### Post by falkTX on 2010-09-13
> **Xenphor said:**
> I was wondering, is there a way to "Disconnect all Sixaxis" or "Disconnect all Devices" through the terminal? Thanks.

hm... I got so focused on the GUI that I forgot about this.

but you can make a script for it, using 'hcitool' as base:

to show all connected devices, run:
*hcitool con*

to disconnect a device:
*sudo hcitool dc <addr>*

so if you know all of your sixaxis MAC addresses, just run something like this:
```
sudo hcitool dc 00:XX:00:XX:00
sudo hcitool dc 00:XX:00:XX:01
..etc
```

---

### Post by Xenphor on 2010-09-15
I noticed something strange with the keypad just now. When I try to wake the pad up after it automatically goes to sleep, it does not reconnect properly.  It will just keep flashing and then nothing happens. If I turn the power on and off and then try to reconnect, it will eventually start working again. For the record, I have also tried this in windows and it is able to reconnect properly so I do not think it is a problem with the keypad. I am not sure if this has been posted before as I just tried the keypad yesterday.

---

### Post by falkTX on 2010-09-18
> **Xenphor said:**
> I noticed something strange with the keypad just now. When I try to wake the pad up after it automatically goes to sleep, it does not reconnect properly.  It will just keep flashing and then nothing happens. If I turn the power on and off and then try to reconnect, it will eventually start working again. For the record, I have also tried this in windows and it is able to reconnect properly so I do not think it is a problem with the keypad. I am not sure if this has been posted before as I just tried the keypad yesterday.

I always have seen the keypad working like this (self-disconnecting after ~5mins of no usage).

For me, pressing a key when it's off connects it right away (~3 sec).

If you only use your bluetooth adapter for sixaxis/keypads, run this:
```
sudo sixad --boot-yes
```which will make sure sixad (the backend driver) is always available and running.

---

### Post by kennethadammiller on 2010-09-19
So yea, I'm having some trouble getting the ps3 controller buttons to correspond to actions on the computer. I can get it connected, but there seems to be some additional problems...

whenever I start qtsixa up, it asks me this: 

In order to use QtSixA you moust be in the sixad group.

Do you want do do this now?

And I don't know what that means, but from what I understand, everyone else is able to download this and use it as freeware without much trouble at all. 

I'll mention the fact that I'm running 10.04, which means that there were some changes about hal, which I read about being a part of qtsixa's internals... now that they changed it, custom configurations with how it works can't be done-which is why you changed the profiles to something like those that fit games that are already out. I want to be able to use it with snes9x and Muopen64. But I think that It would be better to be able to dynamically assign usage; like... up arrow corresponds to action x or whatever.

I will also say that after I open qtsixa, and then I go to settings>advanced> the configure sixa option can't be selected.

Can you help me get set up?

I can connect, but after I do, I don't see any responsiveness on the screen with what I'm doing with the controller...

---

### Post by kennethadammiller on 2010-09-21
Please don't just block me off as an idiot. I actually had this running a while back. The GUI looks different from when I had it running last time, and I even posted some comments a long way back on this very same thread.

---

### Post by kurmudgeon79 on 2010-09-21
I made new icons that work better with the Ubuntu Ambience (Dark) theme.  They can be found here: [http://gnome-look.org/content/show.php?content=132894](http://gnome-look.org/content/show.php?content=132894)

Screenshot:
[IMG]http://gnome-look.org/CONTENT/content-pre1/132894-1.png[/IMG]

Enjoy!

---

### Post by falkTX on 2010-09-24
> **kennethadammiller said:**
> Please don't just block me off as an idiot. I actually had this running a while back. The GUI looks different from when I had it running last time, and I even posted some comments a long way back on this very same thread.

Hi,

Just to be safe, the first thing you should do is to delete the old qtsixa folder (look into the hidden files in your home folder and delete the ones related to 'qtsixa' or 'sixad').

And you're right, QtSixA doesn't use HAL (through fdi files) anymore, now everything is done in pure code.
Because of this, the mouse/keyboard features will only work on bluetooth mode (for now).

If something is not working properly, just start the app in a terminal ('qtsixa') and post here the output

---

### Post by kennethadammiller on 2010-09-25
Oh wait... I went to a profile, and it allowed me to pick epsx 1:1 playstation controller... this suits my needs. I just wanted to be able to use it to play on SNES9x and muopen64!

Anyway, Nice job, badass.

---

### Post by emoguitarist06 on 2010-09-28
Just giving an update on my experience... It's pretty much Awesome!
I was running 32 Bit Karmic and now I'm running 64 Bit Lucid and everything is amazing :) just fyi you're the Sh**

---

### Post by WienerWuerstel on 2010-10-11
Sorry if i bother you. But when will Qtsixa be available for Maverick?

---

### Post by Xenphor on 2010-10-12
I would also be interested in a version for maverick if it isnt too much trouble.

---

### Post by falkTX on 2010-10-12
> **Xenphor said:**
> I would also be interested in a version for maverick if it isnt too much trouble.

Done, just use the PPA.

I'm still on Lucid, so I actually forgot about this... :lolflag:

---

### Post by Xenphor on 2010-10-23
I've noticed that the battery life under qtsixa via bluetooth seems to be quite a bit shorter than the driver I'm using with windows. I was wondering if there is anyway you could optimize the program somehow so it doesn't drain the battery as fast? I turn off all the rumble, LED lights, and sixaxis stuff and mainly just use the controller as a mouse and keyboard. 

The driver I have for windows doesn't turn off the controller ever and I've been able to use it for multiple days without having to charge it. With qtsixa I can't seem to be able to get through a day without having to charge it again. I'm sorry I can't give anymore specifics than that -- just that for some reason it lasts a lot longer in windows. It doesn't seem like it should use more or less power regardless of what os or driver it's using so I don't know. 

Here is the link to the drivers I'm using in windows. The site is actually in Japanese so I had to use google translate to make it somewhat readable: [http://translate.google.com/translate?hl=en&ie=UTF8&langpair=ja|en&u=http://tamamyikesu.web.fc2.com/sd_devicedriver.html]("http://translate.google.com/translate?hl=en&ie=UTF8&langpair=ja%7Cen&u=http://tamamyikesu.web.fc2.com/sd_devicedriver.html")

You'll have to install the usb driver first and then the bluetooth one I believe. Unfortunately for bluetooth you will need a dedicated bluetooth radio for it to install the driver on. Also be sure to download the SDDrivertools at the bottom of the page. Then download this program here [http://tamamyikesu.web.fc2.com/files/sddriversetting_1.4.0.11e.zip](http://tamamyikesu.web.fc2.com/files/sddriversetting_1.4.0.11e.zip) to pair the DS3 through usb. After you do that you can use SDDrivertools to initiate a connection via bluetooth.

---

### Post by link141 on 2010-10-29
First off, excellent job with qtsixa!!=D>  It is an excellent driver/frontend for the DS3 that I have used many a-time to play emulators and games on my laptop.  I also used it back in April for a presentation of an air hockey game I made for a high-school graduation project; my audience was very impressed with the wireless controllers.

I'm running 64-bit Kubuntu Lucid and I've noticed a bug with the rumble feature.  (First, the permissions on the rumble event file must be changed) Upon opening a force-feedback enabled program using qtsixa with a DS3 and rumble enabled, the program will hang indefinitely.  This can be seen Mupen64Plus and pSX.  When the controller is disconnected, Mupen64 will resume and start up successfully, wheras pSX will crash.  I do not have enough experience with C or programming in general to know exactly why this happens, but I'm willing to help you fix this in any way I can.  Let me know what I can do.

Once again, thank you for your awesome driver and frontend!

link141

---

### Post by cable_guy on 2010-11-01
Hi all, I am new here, and wondered if it was 100% essential to use the GUI to set up my PS3 remote for use over Bluetooth?

I am using a window-manager-less version of Ubuntu (XBMC Live) and hence can't fire up the GUI but I have a "keymap" which is an XML file which I believe contains certain instructions for my XBMC application to understand what button presses do what.

---

### Post by emoguitarist06 on 2010-11-04
**[COLOR="Red"]WHOA I GOT A WEIRD ONE FOR YOU FALKTX![/COLOR]**

I am running Ubuntu 10.10 64bit and I installed Mupen64Plus v1.5 from USC
whenever my sixad is connected MUPEN freezes without loading a game **BUT** the moment I disconnect my PS3 controller it loads the game and continues normally. Weird?

Here is the terminal output **W/O sixad connected**
```
phillipguy@phillipguy-laptop:~$ mupen64plus /home/phillipguy/Games/n64/Legend\ of\ Zelda\,\ The\ -\ Ocarina\ of\ Time\ \(E\)\ \(V1.0\)\ \[\!\].zip 
 __  __                         __   _  _   ____  _             
|  \/  |_   _ _ __   ___ _ __  / /_ | || | |  _ \| |_   _ ___ 
| |\/| | | | | '_ \ / _ \ '_ \| '_ \| || |_| |_) | | | | / __|  
| |  | | |_| | |_) |  __/ | | | (_) |__   _|  __/| | |_| \__ \  
|_|  |_|\__,_| .__/ \___|_| |_|\___/   |_| |_|   |_|\__,_|___/  
             |_|         http://code.google.com/p/mupen64plus/  
Version 1.5

Config Dir:  /home/phillipguy/.config/mupen64plus/
Data Dir:  /home/phillipguy/.local/share/mupen64plus/
Cache Dir:  /home/phillipguy/.cache/mupen64plus/
Install Dir: /usr/share/mupen64plus/
Plugin Dir:  /usr/lib/mupen64plus/

Rescanning rom cache.
Rom cache up to date. 0 ROMs.
Compression: Zip
Imagetype: .z64 (native)
Rom size: 33554432 bytes (or 32 Mb or 256 Megabits)
MD5: E040DE91A74B61E3201DB0E2323F768A
80 37 12 40
ClockRate = f
Version: 1449
CRC: b044b569 373c1985
Name: THE LEGEND OF ZELDA
Manufacturer: Nintendo
Cartridge_ID: 4c5a
Country: Europe (0x50)
PC = 80000400
EEPROM type: 0
init timer!
[RiceVideo] SSE processing enabled.
[blight's SDL input plugin]: version 0.0.10 initialized.
memory initialized
[RiceVideo] SSE processing enabled.
[RiceVideo] Found ROM 'THE LEGEND OF ZELDA', CRC 69b544b085193c37-50
[RiceVideo] Enabled hacks for game: 'THE LEGEND OF ZELDA'
InitExternalTextures
Initializing OpenGL Device Context
(II) Initializing SDL video subsystem...
(II) Getting video info...
(II) Setting video mode 640x480...
NVIDIA Corporation - ION/PCI/SSE2 : 3.3.0 NVIDIA 260.19.06
[RiceVideo] OpenGL Combiner: Fragment Program
[JttL's SDL Audio plugin] version 1.5 initalizing.
[JttL's SDL Audio plugin] Initializing SDL audio subsystem...
[JttL's SDL Audio plugin] Allocating memory for audio buffer: 65536 bytes.
/dev/mixer: : No such file or directory
[blight's SDL input plugin]: Couldn't open joystick for controller #0: There are 0 joysticks available
Starting r4300 emulator
R4300 Core mode: Dynamic Recompiler
R4300 core: starting 64-bit dynamic recompiler at: 0x3279200.
/dev/mixer: : No such file or directory
/dev/mixer: : No such file or directory
R4300 core finished.
[JttL's SDL Audio plugin] Cleaning up SDL sound plugin...
[RiceVideo] Found ROM 'THE LEGEND OF ZELDA', CRC 69b544b085193c37-50
[blight's SDL input plugin]: Closing...
```
That output shows Mupen64Plus starting and I see Link riding on his horse and than I closed it.

Here is the terminal output of Mupen64Plus **WITH sixad connected**
```
phillipguy@phillipguy-laptop:~$ mupen64plus /home/phillipguy/Games/n64/Legend\ of\ Zelda\,\ The\ -\ Ocarina\ of\ Time\ \(E\)\ \(V1.0\)\ \[\!\].zip 
 __  __                         __   _  _   ____  _             
|  \/  |_   _ _ __   ___ _ __  / /_ | || | |  _ \| |_   _ ___ 
| |\/| | | | | '_ \ / _ \ '_ \| '_ \| || |_| |_) | | | | / __|  
| |  | | |_| | |_) |  __/ | | | (_) |__   _|  __/| | |_| \__ \  
|_|  |_|\__,_| .__/ \___|_| |_|\___/   |_| |_|   |_|\__,_|___/  
             |_|         http://code.google.com/p/mupen64plus/  
Version 1.5

Config Dir:  /home/phillipguy/.config/mupen64plus/
Data Dir:  /home/phillipguy/.local/share/mupen64plus/
Cache Dir:  /home/phillipguy/.cache/mupen64plus/
Install Dir: /usr/share/mupen64plus/
Plugin Dir:  /usr/lib/mupen64plus/

Rescanning rom cache.
Rom cache up to date. 0 ROMs.
Compression: Zip
Imagetype: .z64 (native)
Rom size: 33554432 bytes (or 32 Mb or 256 Megabits)
MD5: E040DE91A74B61E3201DB0E2323F768A
80 37 12 40
ClockRate = f
Version: 1449
CRC: b044b569 373c1985
Name: THE LEGEND OF ZELDA
Manufacturer: Nintendo
Cartridge_ID: 4c5a
Country: Europe (0x50)
PC = 80000400
EEPROM type: 0
init timer!
[RiceVideo] SSE processing enabled.
```
[B][COLOR="Blue"]And it stays right there indefinitely without fully starting Mupen
but the VERY MOMENT I disconect six ad it continues with[/COLOR][/B]
```
[JttL's SDL Audio plugin] version 1.5 initalizing.
[JttL's SDL Audio plugin] Initializing SDL audio subsystem...
[JttL's SDL Audio plugin] Allocating memory for audio buffer: 65536 bytes.
/dev/mixer: : No such file or directory
[blight's SDL input plugin]: Couldn't open joystick for controller #0: There are 0 joysticks available
Starting r4300 emulator
R4300 Core mode: Dynamic Recompiler
R4300 core: starting 64-bit dynamic recompiler at: 0x479c200.
/dev/mixer: : No such file or directory
/dev/mixer: : No such file or directory
```

---

### Post by emoguitarist06 on 2010-11-04
**UPDATE!**

It works via USB perfectly
To work via Bluetooth you must disable the Rumble feature in QtSixA

Odd but hey it works :)

---

### Post by link141 on 2010-11-04
> **emoguitarist06 said:**
> **[COLOR="Red"]WHOA I GOT A WEIRD ONE FOR YOU FALKTX![/COLOR]**

I am running Ubuntu 10.10 64bit and I installed Mupen64Plus v1.5 from USC
whenever my sixad is connected MUPEN freezes without loading a game **BUT** the moment I disconnect my PS3 controller it loads the game and continues normally. Weird?

[...]

And it stays right there indefinitely without fully starting Mupen
but the VERY MOMENT I disconect six ad it continues [...]

This is exactly the problem/bug I was running into (see my last post).  I believe the problem is because the driver is not using the rumble event interface properly or is not sending certain feedback to the calling program when rumble is opened. (However, this is merely speculation)  We know that rumble actually works in the driver though, because of the rumble effect that falkTX implemented upon connecting a DS3.

Using a program that supports rumble with rumble enabled in the driver has caused the calling program to hang with all of the programs I've tried (mupen64plus and pSX).

Perhaps I'll look into this more when I have a chance.  It should be relatively easy to fix for someone who knows what they're doing (I certainly do not;)).

The rest of the driver is perfect though.

---

### Post by falkTX on 2010-11-06
> **link141 said:**
> This is exactly the problem/bug I was running into (see my last post).  I believe the problem is because the driver is not using the rumble event interface properly or is not sending certain feedback to the calling program when rumble is opened. (However, this is merely speculation)  We know that rumble actually works in the driver though, because of the rumble effect that falkTX implemented upon connecting a DS3.

Using a program that supports rumble with rumble enabled in the driver has caused the calling program to hang with all of the programs I've tried (mupen64plus and pSX).

Perhaps I'll look into this more when I have a chance.  It should be relatively easy to fix for someone who knows what they're doing (I certainly do not;)).

The rest of the driver is perfect though.


I won't call the driver perfect, but it work for most cases.
the rumble feature is really experimental cause I never had found a game that supported it.

but now i'll try pSX to see how it works

---

### Post by falkTX on 2010-11-06
> **cable_guy said:**
> Hi all, I am new here, and wondered if it was 100% essential to use the GUI to set up my PS3 remote for use over Bluetooth?

I am using a window-manager-less version of Ubuntu (XBMC Live) and hence can't fire up the GUI but I have a "keymap" which is an XML file which I believe contains certain instructions for my XBMC application to understand what button presses do what.

it's complicated to explain how the configuration for qtsixa works...

but you can use 1 computer, set it up nicely, then copy the folders to the XBMC PC.
the configuration folders are:
~/.qtsixa2/ *(User specific settings and input profiles)*
/var/lib/sixad *(System-wide sixaxis configuration)*

and make sure you run "sixpair" and "sixpair-kbd" to pair the sixaxis on the XBMC machine

---

### Post by falkTX on 2010-11-06
> **Xenphor said:**
> I've noticed that the battery life under qtsixa via bluetooth seems to be quite a bit shorter than the driver I'm using with windows. I was wondering if there is anyway you could optimize the program somehow so it doesn't drain the battery as fast? I turn off all the rumble, LED lights, and sixaxis stuff and mainly just use the controller as a mouse and keyboard. 

The driver I have for windows doesn't turn off the controller ever and I've been able to use it for multiple days without having to charge it. With qtsixa I can't seem to be able to get through a day without having to charge it again. I'm sorry I can't give anymore specifics than that -- just that for some reason it lasts a lot longer in windows. It doesn't seem like it should use more or less power regardless of what os or driver it's using so I don't know. 

Here is the link to the drivers I'm using in windows. The site is actually in Japanese so I had to use google translate to make it somewhat readable: [http://translate.google.com/translate?hl=en&ie=UTF8&langpair=ja|en&u=http://tamamyikesu.web.fc2.com/sd_devicedriver.html]("http://translate.google.com/translate?hl=en&ie=UTF8&langpair=ja%7Cen&u=http://tamamyikesu.web.fc2.com/sd_devicedriver.html")

You'll have to install the usb driver first and then the bluetooth one I believe. Unfortunately for bluetooth you will need a dedicated bluetooth radio for it to install the driver on. Also be sure to download the SDDrivertools at the bottom of the page. Then download this program here [http://tamamyikesu.web.fc2.com/files/sddriversetting_1.4.0.11e.zip](http://tamamyikesu.web.fc2.com/files/sddriversetting_1.4.0.11e.zip) to pair the DS3 through usb. After you do that you can use SDDrivertools to initiate a connection via bluetooth.


I'm no coder expert, but I do my best and I learn more everyday.

I'm thinking about re-writing the whole thing again, now to allow using the sixaxis without turning off normal bluetooth (I need to check how the Wii guys do this...)

There is some conversation about getting official sixaxis support in BlueZ and a patch was made to make the LEDs work on USB mode (should be in kernel 2.6.36 now).

Anyway, I'll keep you guys posted about what happens

---

### Post by benmoran on 2010-11-06
FalkTX,  The userspace xbox 360 controller driver, XBOXDRV, also has rumble support. I've tested it in Tomb Raider Anniversary through wine, and it works OK. I don't have my Dualshock with me at the moment so I can't test it myself, but perhaps someone else here can?

---

### Post by link141 on 2010-11-06
[QUOTE=falkTX][...] the rumble feature is really experimental cause I never had found a game that supported it.[...][/QUOTE]

You should also be able to use the program fftest in the joystick package in the Ubuntu repos.  I'd imagine it would be much easier to test the driver with this.  I can also give you a larger list of Linux games that support rumble if you'd like.

Thanks for looking into this.  Once again, your driver is excellent!

---

### Post by falkTX on 2010-11-15
**Good News!**

[SIZE="5"]Rumble is now working![/SIZE]

Just update via PPA and enjoy!
*(make sure you have a "DualShock3")*


I tested it with pSX, and worked fine there.
The 'fftest' utility doesn't seem to work as expected though.

Every-time there's a rumble request, some messages will be printed in the terminal (if you started 'sixad' manually).

Please report any issues.

---

### Post by link141 on 2010-11-15
Excellent work!!  I can confirm that rumble now works in pSX on my machine.  It was only a week ago that I reported this issue, and you already have it fixed.  Thank you!!

Unfortunately, it still does not wok correctly in Mupen64Plus.  Upon starting emulation with rumble enabled, the controller will give a quick rumble once (this request will show up in the console qtsixa was started in).  However, no more rumble requests are caught by the driver after this.

Anyway, thanks again for getting rumble in its current state.  Because of your efforts, I can now play Crash Bandicoot and other PS games with rumble.

EDIT: I tried Mupen64Plus with wired Xbox 360 controller (my sister's boyfriend happened to bring his 360 over...) and rumble wasn't working on that either.  The rumble DID work with pSX though.

---

### Post by falkTX on 2010-11-17
> **link141 said:**
> Excellent work!!  I can confirm that rumble now works in pSX on my machine.  It was only a week ago that I reported this issue, and you already have it fixed.  Thank you!!

Unfortunately, it still does not wok correctly in Mupen64Plus.  Upon starting emulation with rumble enabled, the controller will give a quick rumble once (this request will show up in the console qtsixa was started in).  However, no more rumble requests are caught by the driver after this.

Anyway, thanks again for getting rumble in its current state.  Because of your efforts, I can now play Crash Bandicoot and other PS games with rumble.

EDIT: I tried Mupen64Plus with wired Xbox 360 controller (my sister's boyfriend happened to bring his 360 over...) and rumble wasn't working on that either.  The rumble DID work with pSX though.


Hi there,

I only tested it on pSX, so I'm not sure about other games.
I'll get some n64 roms to test this thing. Any recommendations?

Can someone help here and list some of the linux games that support rumble?

---

### Post by link141 on 2010-11-17
Some good N64 games to test rumble with:
[LIST]
[*]Star Fox 64 (Lylat Wars in Europe) - This was the first game ever to use controller rumble AFAIK
[*]Super Smash Bros. (This one is particularly heavy on the rumble)
[*]F-Zero x
[*]The Legend of Zelda Ocarina of Time
[*][Here is a full list of N64 games that support Rumble]("http://en.wikipedia.org/wiki/Rumble_Pak#List_of_compatible_games")
[/LIST]

Here are all of the Linux games that I know of that support rumble (warning: some of these may have to be built from source):
[LIST]
[*]BZFlag (apparently...)
[*]Dolphin-Emu
[*]PCSX2
[*]Be the Wumpus
[*]ePSXe (I *think* the Linux version has FF support...)
[*]VDrift
[*]Mupen64plus
[*]pSX
[/LIST]

---

### Post by falkTX on 2010-11-18
> **link141 said:**
> Some good N64 games to test rumble with:
[LIST]
[*]Star Fox 64 (Lylat Wars in Europe) - This was the first game ever to use controller rumble AFAIK
[*]Super Smash Bros. (This one is particularly heavy on the rumble)
[*]F-Zero x
[*]The Legend of Zelda Ocarina of Time
[*][Here is a full list of N64 games that support Rumble]("http://en.wikipedia.org/wiki/Rumble_Pak#List_of_compatible_games")
[/LIST]

Here are all of the Linux games that I know of that support rumble (warning: some of these may have to be built from source):
[LIST]
[*]BZFlag (apparently...)
[*]Dolphin-Emu
[*]PCSX2
[*]Be the Wumpus
[*]ePSXe (I *think* the Linux version has FF support...)
[*]VDrift
[*]Mupen64plus
[*]pSX
[/LIST]


Many thanks!


I've found why some games are not working, but the solution makes the games freeze when the rumble occurs...

I'll keep working on this and let you guys know how it goes


NOTES: ePSXe for Linux does not even have joystick support (only keyboard)
the Windows version has a weird rumble implementation. I think I'll patch Wine myself to force rumble for it... ;)

---

### Post by Rapture2k4 on 2010-12-02
I'm having trouble with QtSixA on my Asus EeePC 1005HA. I have 10.10 32-bit installed and went through the guide on page 1 to install the app. When I launch it, I get a nasty error and a hard-crash that looks similar to this:

```

CPU 1: Machine Check Exception:                        4 Bank 2: ...
SC 185e668534 ADDR 0ef29800
PROCESSOR 0:106c2 TIME 1291281349 SOCKET APIC 1
No human readable MCE decoding support on this CPU type.
Run the message through 'mcelog --ascii' to decode
CPU 0: Machine Check Exception:                        4 Bank 2: ...
TSC 185e66855c ADDR 6ef29800
PROCESSOR 0:106c2 TIME 1291281349 SOCKET 0 APIC 0
No human readable MCI decoding support on this CPU type.
Run the message through 'mcelog --ascii' to decode
This is not a software problem!
Machine check: Processor context corrupt
Kernel panic - not syncing: Fatal machine check
Pid: 0, comm: swapper Tained: G   M 2.6.35-23-generic #41-Ubuntu
Call Trace:
? printk+0x2d/0x35
panic+0x5a/0xd2
mce_panic+0x1aa/01d0
...
panic occurred, switching back to text console
Rebooting in 30 seconds.._

```

Obviously, it states this isn't a software issue. It looks like my CPU doesn't support something. My CPU is an Atom N280 (1.66Ghz). I've seen other posts where people got it working with similar processors. Is there something I can do to figure this out?

---

### Post by starscalling on 2010-12-02
OK this is redonkulous.

Can anyone actually show step by step how to make this program not !@#$%^?

The latest takes out the xorg joystick package, and is made of fail from what i can tell in 10.10

Shoot, i'll even put up a bounty - just $5 - make a guide that works and i'll send it. 

Needed: usb connection, bluetooth is not present.

Issue: pushing the ps button activates, but ONLY the default NEVER a profile, ALWAYS the left joy is mouse, right is scroll, and those two click. select is mouse left button, and nothing else does anything. FAIL.

Tried 1.2x and 1.5 versions.

uname -a:
Linux nocubu-q66 2.6.35-23-generic-pae #41-Ubuntu SMP Wed Nov 24 10:35:46 UTC 2010 i686 GNU/Linux

cat /etc/*release /etc/*version
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=10.10
DISTRIB_CODENAME=maverick
DISTRIB_DESCRIPTION="Ubuntu 10.10"
squeeze/sid

dmesg|tail
[ 3108.620020] usb 7-1: new full speed USB device using uhci_hcd and address 4
[ 3108.981153] input: Sony PLAYSTATION(R)3 Controller as /devices/pci0000:00/0000:00:1d.1/usb7/7-1/7-1:1.0/input/input6
[ 3108.981357] sony 0003:054C:0268.0005: input,hiddev96,hidraw2: USB HID v1.11 Joystick [Sony PLAYSTATION(R)3 Controller] on usb-0000:00:1d.1-1/input0

---

### Post by falkTX on 2010-12-02
> **Rapture2k4 said:**
> I'm having trouble with QtSixA on my Asus EeePC 1005HA. I have 10.10 32-bit installed and went through the guide on page 1 to install the app. When I launch it, I get a nasty error and a hard-crash that looks similar to this:

```

CPU 1: Machine Check Exception:                        4 Bank 2: ...
SC 185e668534 ADDR 0ef29800
PROCESSOR 0:106c2 TIME 1291281349 SOCKET APIC 1
No human readable MCE decoding support on this CPU type.
Run the message through 'mcelog --ascii' to decode
CPU 0: Machine Check Exception:                        4 Bank 2: ...
TSC 185e66855c ADDR 6ef29800
PROCESSOR 0:106c2 TIME 1291281349 SOCKET 0 APIC 0
No human readable MCI decoding support on this CPU type.
Run the message through 'mcelog --ascii' to decode
This is not a software problem!
Machine check: Processor context corrupt
Kernel panic - not syncing: Fatal machine check
Pid: 0, comm: swapper Tained: G   M 2.6.35-23-generic #41-Ubuntu
Call Trace:
? printk+0x2d/0x35
panic+0x5a/0xd2
mce_panic+0x1aa/01d0
...
panic occurred, switching back to text console
Rebooting in 30 seconds.._

```

Obviously, it states this isn't a software issue. It looks like my CPU doesn't support something. My CPU is an Atom N280 (1.66Ghz). I've seen other posts where people got it working with similar processors. Is there something I can do to figure this out?

You can try to compile qtsixa by yourself.

follow these steps:


1 - make sure you have the qtsixa repo installed:
```
sudo add-apt-repository ppa:falk-t-j/qtsixa
```

2 - edit the repo file and enable sources:
```
sudo nano /etc/apt/sources.list.d/falk-t-j-qtsixa-lucid.list
```
paste this in the file:
```
deb http://ppa.launchpad.net/falk-t-j/qtsixa/ubuntu lucid main
deb-src http://ppa.launchpad.net/falk-t-j/qtsixa/ubuntu lucid main
```

3 - update sources, install dependencies and download qtsixa
```
sudo apt-get update
sudo apt-get install devscripts fakeroot build-essential
sudo apt-get build-dep qtsixa
apt-get source qtsixa
```

4 - compile qtsixa
```
cd qtsixa*
debuild -rfakeroot
```
It should print an error at the end, saying it could not sign the package. Ignore it.
You should then have 2 deb files, qtsixa and sixad.
Install them and reboot


Tell me if this works

---

### Post by falkTX on 2010-12-02
> **starscalling said:**
> OK this is redonkulous.

Can anyone actually show step by step how to make this program not !@#$%^?

The latest takes out the xorg joystick package, and is made of fail from what i can tell in 10.10

Shoot, i'll even put up a bounty - just $5 - make a guide that works and i'll send it. 

Needed: usb connection, bluetooth is not present.

Issue: pushing the ps button activates, but ONLY the default NEVER a profile, ALWAYS the left joy is mouse, right is scroll, and those two click. select is mouse left button, and nothing else does anything. FAIL.

Tried 1.2x and 1.5 versions.

uname -a:
Linux nocubu-q66 2.6.35-23-generic-pae #41-Ubuntu SMP Wed Nov 24 10:35:46 UTC 2010 i686 GNU/Linux

cat /etc/*release /etc/*version
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=10.10
DISTRIB_CODENAME=maverick
DISTRIB_DESCRIPTION="Ubuntu 10.10"
squeeze/sid

dmesg|tail
[ 3108.620020] usb 7-1: new full speed USB device using uhci_hcd and address 4
[ 3108.981153] input: Sony PLAYSTATION(R)3 Controller as /devices/pci0000:00/0000:00:1d.1/usb7/7-1/7-1:1.0/input/input6
[ 3108.981357] sony 0003:054C:0268.0005: input,hiddev96,hidraw2: USB HID v1.11 Joystick [Sony PLAYSTATION(R)3 Controller] on usb-0000:00:1d.1-1/input0


I've just made some recent changes for 1.5.0 beta (for lucid and maverick)
Please install it and update.

It should fix the issue of the sixaxis always working as a mouse/keyboard even when it's not enabled.


Please note that in the 1.5.0 version, profiles will only work in bluetooth mode.
A work-around is to configure the hidraw device in qtsixa (enable input only and select an input profile), and then run:
```
sudo modprobe uinput
sudo sixad-raw /dev/hidrawX
```
where 'X' is the hidraw dev number of the sixaxis (check 'dmesg' to know which number to use)

---

### Post by Rapture2k4 on 2010-12-02
> **falkTX said:**
> You can try to compile qtsixa by yourself.

follow these steps:


1 - make sure you have the qtsixa repo installed:
```
sudo add-apt-repository ppa:falk-t-j/qtsixa
```

2 - edit the repo file and enable sources:
```
sudo nano /etc/apt/sources.list.d/falk-t-j-qtsixa-lucid.list
```
paste this in the file:
```
deb http://ppa.launchpad.net/falk-t-j/qtsixa/ubuntu lucid main
deb-src http://ppa.launchpad.net/falk-t-j/qtsixa/ubuntu lucid main
```

3 - update sources, install dependencies and download qtsixa
```
sudo apt-get update
sudo apt-get install devscripts fakeroot build-essential
sudo apt-get build-dep qtsixa
apt-get source qtsixa
```

4 - compile qtsixa
```
cd qtsixa*
debuild -rfakeroot
```
It should print an error at the end, saying it could not sign the package. Ignore it.
You should then have 2 deb files, qtsixa and sixad.
Install them and reboot


Tell me if this works

New error:
```
gpg:  skipped "falkRX <falktx@gmail.com>": secret key not available
gpg: /tmp/debsign.KN20lfRP/qtsixa_1.4.95-0~maverick3.dsc: clearsign failed: secret key not available
debsign: gpg error occurred! Aborting...
debuild: fatal error a line 1258:
running debsign failed
```


Correction, I was trying to build the wrong version. Here is what 1.5 spits out:
```
g++ -Wall -O2 sixad-bin.cpp bluetooth.cpp shared.cpp textfile.cpp -o bins/sixad-bin -lbluetooth
sixad-bin.cpp: In function &#8216;int main(int, char**)&#8217;:
sixad-bin.cpp:36: warning: taking address of temporary
textfile.cpp: In function &#8216;char* read_key(const char*, const char*, int)&#8217;:
textfile.cpp:82: error: &#8216;fstat&#8217; was not declared in this scope
make[2]: *** [sixad_bins] Error 1
make[2]: Leaving directory `/home/****/qtsixa-1.5.0/sixad'
make[1]: *** [build] Error 2
make[1]: Leaving directory `/home/****/qtsixa-1.5.0'
make: *** [build] Error 2
dpkg-buildpackage: error: debian/rules build gave error exit status 2
debuild: fatal error at line 1337:
dpkg-buildpackage -rfakeroot -D -us -uc failed
```

---

### Post by starscalling on 2010-12-03
> **starscalling said:**
> OK this is redonkulous.

Can anyone actually show step by step how to make this program not !@#$%^?

The latest takes out the xorg joystick package, and is made of fail from what i can tell in 10.10

Shoot, i'll even put up a bounty - just $5 - make a guide that works and i'll send it. 

Needed: usb connection, bluetooth is not present.

Issue: pushing the ps button activates, but ONLY the default NEVER a profile, ALWAYS the left joy is mouse, right is scroll, and those two click. select is mouse left button, and nothing else does anything. FAIL.

Tried 1.2x and 1.5 versions.

uname -a:
Linux nocubu-q66 2.6.35-23-generic-pae #41-Ubuntu SMP Wed Nov 24 10:35:46 UTC 2010 i686 GNU/Linux

cat /etc/*release /etc/*version
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=10.10
DISTRIB_CODENAME=maverick
DISTRIB_DESCRIPTION="Ubuntu 10.10"
squeeze/sid

dmesg|tail
[ 3108.620020] usb 7-1: new full speed USB device using uhci_hcd and address 4
[ 3108.981153] input: Sony PLAYSTATION(R)3 Controller as /devices/pci0000:00/0000:00:1d.1/usb7/7-1/7-1:1.0/input/input6
[ 3108.981357] sony 0003:054C:0268.0005: input,hiddev96,hidraw2: USB HID v1.11 Joystick [Sony PLAYSTATION(R)3 Controller] on usb-0000:00:1d.1-1/input0


[I][COLOR="DarkGreen"]
Well, here's one for ya - guess i get my own 5 bucks. The thread *[COLOR="Green"]i found this in ( [http://ubuntuforums.org/showthread.php?t=1600876&highlight=Sixaxis](http://ubuntuforums.org/showthread.php?t=1600876&highlight=Sixaxis) )[/COLOR]* has another part that goes in the xorg server section and that breaks my xorg in 10.10 - however if i just define the device, im good to go. Ive got the xorg joystick bit back in -- FYI[/COLOR][/I]

> **starscalling said:**
> [QUOTE=tipp98;9997834]ok, it's whipped. According to my log it seem that js0 had one more axis, probably accounting for the different behavior in xinput :/   I added another match clause to ignore /dev/inpu/js* devices. Seems to be functioning as configured now. Here it is. This goes in /etc/X11/xorg.conf.d/10-dualshock3.conf
```

Section "InputClass"
    Identifier    "DualShock3"
    MatchProduct    "Sony PLAYSTATION(R)3 Controller"
    MatchDevicePath "/dev/input/event*" 
    Driver        "joystick"
    Option "MapAxis1" "mode=relative axis=+1.25zx" # deadzone=500"
    Option "MapAxis2" "mode=relative axis=+1.25zy" # deadzone=500"
    Option "MapAxis3" "mode=relative axis=+1.75x" # deadzone=500"
    Option "MapAxis4" "mode=relative axis=+1.75y" # deadzone=500"
    Option "MapAxis5" "none"
    Option "MapAxis6" "none"

    Option "MapButton1" "key=119"    #Select=delete
    Option "MapButton2" "key=50"    #L3=shift
    Option "MapButton3" "key=133"    #R3=super
    Option "MapButton4" "key=36"    #start=enter
    Option "MapButton5" "key=111"    #up
    Option "MapButton6" "key=114"    #right
    Option "MapButton7" "key=116"    #down
    Option "MapButton8" "key=113"    #left
    Option "MapButton9" "key=64"    #L2=alt
    Option "MapButton10" "button=3    #R2=right click
    Option "MapButton11" "key=37"    #L1=ctrl
    Option "MapButton12" "button=1"    #R1=left click
    Option "MapButton13" "button=2"    #tri=middle click
    Option "MapButton14" "key=9"    #circle=ESC
    Option "MapButton15" "key=65"    #cross=space
    Option "MapButton16" "key=23"    #square=tab
    Option "MapButton17" "none"    #PS=osk/dasher?
EndSection

```

There's just one small thing that bugs me and that is the performance. It doesn't seem responsive to direction changes. For instance, if I move the stick in a smooth circle, it kinda makes the cursor do a square. It just doesn't seem right.
breaks xorg for me


mmmm

ok without the xorg server bit the above works great.

[http://www.x.org/archive/X11R7.5/doc/man/man4/joystick.4.html](http://www.x.org/archive/X11R7.5/doc/man/man4/joystick.4.html)

has further details on modding the above.[/QUOTE]
[I][COLOR="DarkGreen"]
for further customization see link 
[http://www.x.org/archive/X11R7.5/doc/man/man4/joystick.4.html](http://www.x.org/archive/X11R7.5/doc/man/man4/joystick.4.html)

EXPLICITLY - YES THE ABOVE WAS ALL I HAD TO DO TO MAKE IT WORK WITH USB; I changed the following:
```
    Option "MapAxis1"      "mode=accelerated keylow=113  keyhigh=114"
    Option "MapAxis2"      "mode=accelerated keylow=111  keyhigh=116"
    Option "MapAxis3" "mode=relative axis=+5x" # deadzone=500"
    Option "MapAxis4" "mode=relative axis=+5y" # deadzone=500"

```and there you go.
[/COLOR][/I]

---

### Post by howtieatie on 2010-12-03
well i have the cdma phone

---

### Post by falkTX on 2010-12-03
> **Rapture2k4 said:**
> New error:
```
gpg:  skipped "falkRX <falktx@gmail.com>": secret key not available
gpg: /tmp/debsign.KN20lfRP/qtsixa_1.4.95-0~maverick3.dsc: clearsign failed: secret key not available
debsign: gpg error occurred! Aborting...
debuild: fatal error a line 1258:
running debsign failed
```

This error is expected (it's the one I write about earlier).
It happens just because you're not me... ;)

> **Rapture2k4 said:**
> 
Correction, I was trying to build the wrong version. Here is what 1.5 spits out:
```
g++ -Wall -O2 sixad-bin.cpp bluetooth.cpp shared.cpp textfile.cpp -o bins/sixad-bin -lbluetooth
sixad-bin.cpp: In function ‘int main(int, char**)’:
sixad-bin.cpp:36: warning: taking address of temporary
textfile.cpp: In function ‘char* read_key(const char*, const char*, int)’:
textfile.cpp:82: error: ‘fstat’ was not declared in this scope
make[2]: *** [sixad_bins] Error 1
make[2]: Leaving directory `/home/****/qtsixa-1.5.0/sixad'
make[1]: *** [build] Error 2
make[1]: Leaving directory `/home/****/qtsixa-1.5.0'
make: *** [build] Error 2
dpkg-buildpackage: error: debian/rules build gave error exit status 2
debuild: fatal error at line 1337:
dpkg-buildpackage -rfakeroot -D -us -uc failed
```

Please run the commands again. I fixed this in the last upload.

---

### Post by Rapture2k4 on 2010-12-04
Finally got it to compile, but still get the Kernel Panic. The odd thing is, it only happens with the GUI frontend. All the sixad stuff works fine. Is there a manual for all the sixad commands/switches so I can write a perl script?

---

### Post by falkTX on 2010-12-04
> **Rapture2k4 said:**
> Finally got it to compile, but still get the Kernel Panic. The odd thing is, it only happens with the GUI frontend. All the sixad stuff works fine. Is there a manual for all the sixad commands/switches so I can write a perl script?

Are you saying that running the GUI causes a kernel panic?
That seems unlikely (a problem in Qt libs..?)

I did not yet documented the sixad configuration files cause the driver itself it's not finished and I want to add more stuff soon (DBus controller and ALSA MIDI driver)

but checking into /var/lib/sixad/profiles/ should get you an idea of how it works.
You can check the source (sixad/shared.cpp file) to know more about how sixad handles the conf files

---

### Post by Rapture2k4 on 2010-12-04
Hopefully I will have time to look into it, but I won't be able to dedicate alot of time to it. Between military life, family life, and other projects, I don't have a lot of time to spare.

I find it odd that only when I start the GUI I get the Kernel Panic. Maybe there is an underlying issue with qt4-python and atom processors. I will look into your source code and start debugging from there. Throw some catches to see exactly where it is deciding to fade to black.

Have you had any reports from other Netbook/Nettop users?

---

### Post by falkTX on 2010-12-05
> **Rapture2k4 said:**
> Hopefully I will have time to look into it, but I won't be able to dedicate alot of time to it. Between military life, family life, and other projects, I don't have a lot of time to spare.

I find it odd that only when I start the GUI I get the Kernel Panic. Maybe there is an underlying issue with qt4-python and atom processors. I will look into your source code and start debugging from there. Throw some catches to see exactly where it is deciding to fade to black.

Have you had any reports from other Netbook/Nettop users?

You should probably try other PyQt4 apps and see if they cause a panic too (the python-qt4-doc package has many app demos/examples).

The QtSixA code for the GUI is not the best (one of my first projects) and I've been focusing on the driver part recently (rumble!).

I'll probably re-write the GUI soon...

---

### Post by Aaron.A on 2010-12-14
i'm using 10.10 and 1.5.0 

here's the issue. when i open the app, and then click something, the app stops responding. everytime. 

to be more specific, i can pair the sixaxis both usb and bluetooth.  when i start up bluetooth it does the whole lights flashing, vibrating thing. 

but, when i click to edit profiles, or even try to select the the bluetooth connection on the main screen, app stops responding. 

thus i can't configure the keys, and can't use the controller. help please! i'm sort of a newb to linux, but if you need more information i can definitely find and copy/paste =)

---

### Post by Aaron.A on 2010-12-14
well never mind.. i installed qt (probably the important part) 
then used qtsixa to pair, jscal to calibrate, and qjoypad to assign keyboard/mouse functions. alls well =)

---

### Post by Aaron.A on 2010-12-16
@falktx
after working out some of the initial kinks i really like this app and i appreciate the work you put into it. fkn awesome =D 

but there is one issue that should be solved to make this thing epic. the app provides the option to assign keys/mouse function to the joystick. 

i edited 'fake joystick 2' and applied it with joystick off. then tested the stick in a text box. when you push the joystick in any direction it gets stuck repeating the key its supposed to execute until you push a button. so, bummer.. no fps =( i'm infinitely walking left xD  

i was thinking it might be a deadzone issue, or maybe the stick isn't calibrated properly, but i really don't know. the mouse actions work flawlessly when using the fake joystick setup, so i was really surprised when the keys didn't work

please fix this?

---

### Post by falkTX on 2010-12-22
> **Aaron.A said:**
> @falktx
after working out some of the initial kinks i really like this app and i appreciate the work you put into it. fkn awesome =D 

but there is one issue that should be solved to make this thing epic. the app provides the option to assign keys/mouse function to the joystick. 

i edited 'fake joystick 2' and applied it with joystick off. then tested the stick in a text box. when you push the joystick in any direction it gets stuck repeating the key its supposed to execute until you push a button. so, bummer.. no fps =( i'm infinitely walking left xD  

i was thinking it might be a deadzone issue, or maybe the stick isn't calibrated properly, but i really don't know. the mouse actions work flawlessly when using the fake joystick setup, so i was really surprised when the keys didn't work

please fix this?

Hi, thanks for the report

I'll look into this later today and see what I can do.


Are you using version 1.5.0 ?

---

### Post by falkTX on 2010-12-27
Good News!

@Aaron.A - I fixed your issue. Many thanks for the report!

I also took the time to fix the mouse scroll speed.
The new code uses a little more CPU, but system monitor still shows sixad[-sixaxis] with 0%, so I guess it's fine.

Update the PPA as usual to get the fixes.


I'll release a final v1.5.0 tarball soon, so that users on other distros can get the new functionality too.

---

### Post by lyleunderwood on 2010-12-28
Hey, I'm on an EEE PC 900. It does not have bluetooth. So I'm just trying to get it working via USB. Qtsixa sees the controller (the notification comes up and it shows in the list), but all four LEDs flash forever and nothing else really happens. I push the PS button, and nothing happens. When I try to restart sixa it just says it can't find any bluetooth devices and exits. Same thing if I try the force option. I've tried both 1.5 and currently 1.2.1, same result. There's like a 75% chance that I'm just missing something, because the documentation is terribly sparse. In the manual for USB it just says plug it in and hit the PS button. I assume that only works if sixad is running, which in my case it does not appear to be?

Any help would be appreciated.

---

### Post by falkTX on 2010-12-28
> **lyleunderwood said:**
> Hey, I'm on an EEE PC 900. It does not have bluetooth. So I'm just trying to get it working via USB. Qtsixa sees the controller (the notification comes up and it shows in the list), but all four LEDs flash forever and nothing else really happens. I push the PS button, and nothing happens. When I try to restart sixa it just says it can't find any bluetooth devices and exits. Same thing if I try the force option. I've tried both 1.5 and currently 1.2.1, same result. There's like a 75% chance that I'm just missing something, because the documentation is terribly sparse. In the manual for USB it just says plug it in and hit the PS button. I assume that only works if sixad is running, which in my case it does not appear to be?

Any help would be appreciated.

Well... let me clarify this:
**QtSixA/sixad only works for bluetooth mode. The Sixaxis works out-of-the-box in USB, in any distro.**

sixad has nothing to do with USB stuff (except sixad-raw).

Just plug your sixaxis on a USB port and press the PS button.
You can then test the joystick with:
```
jstest /dev/input/js0
```

The leds will keep blinking, yes. The default linux driver for the Sixaxis doesn't have LEDs, accelerometers or rumble support.

---

### Post by AngelDE98 on 2010-12-29
This program ... is not working ... :confused: 
I want to connect it with the HIDRAW function ( USB ) or with sixad-raw but : 

QtSixA 1.2.1 : Freeze
QtSixA 1.5b : Could not connect ... But I selected the right one ! 
sixad-raw ( both ) : Just " hangs " ( No output and can do nothing until pkill used ... ) 

After pressing the PS button : 

```
sixad-raw::read(fd) - not a sixaxis
```

It is an Sixaxis and no Dualshock 3 ... And it came with my 40gb PS3 . Please help me ! I had some problems on Windows , too until I found MotioninJoy and the FAQ linked me to here ... 

Thanks for any help !

Edit : It works somehow ... Still want some help because it is confusing ...

Edit 2 : Accelerators not working ...

---

### Post by falkTX on 2010-12-29
> **AngelDE98 said:**
> This program ... is not working ... :confused: 
I want to connect it with the HIDRAW function ( USB ) or with sixad-raw but : 

QtSixA 1.2.1 : Freeze
QtSixA 1.5b : Could not connect ... But I selected the right one ! 
sixad-raw ( both ) : Just " hangs " ( No output and can do nothing until pkill used ... ) 

After pressing the PS button : 

```
sixad-raw::read(fd) - not a sixaxis
```

It is an Sixaxis and no Dualshock 3 ... And it came with my 40gb PS3 . Please help me ! I had some problems on Windows , too until I found MotioninJoy and the FAQ linked me to here ... 

Thanks for any help !

Edit : It works somehow ... Still want some help because it is confusing ...

Edit 2 : Accelerators not working ...


Make sure you enable accelerometers in QtSixA -> profiles -> sixad-raw.

Remember that it creates a new joystick, but does not delete the old one (I think I found a way to do this, but I need to do some testing first).


I'll look into this myself too and report back soon

---

### Post by AngelDE98 on 2010-12-29
Umm ... Accelerometers are being activated automaticly . I said the sixad-raw Driver has problems loading ( No output / Hang ) . And I only see the normal PS3 Controller in my emulator ( dolphin-emu ) . I think because of it it uses the Ubuntu Driver , not yours ...

---

### Post by falkTX on 2010-12-29
> **AngelDE98 said:**
> Umm ... Accelerometers are being activated automaticly . I said the sixad-raw Driver has problems loading ( No output / Hang ) . And I only see the normal PS3 Controller in my emulator ( dolphin-emu ) . I think because of it it uses the Ubuntu Driver , not yours ...

You should press the PS button before running sixad-raw, just to make sure the joystick events are activated.

Then, in the game, you should select the new sixad joystick, not the default/first one.

---

### Post by AngelDE98 on 2010-12-29
I did what you told me but I got this little error ( in Terminal ) : 
```
sixad-raw::read(fd) - not a sixaxis
``` 

I had hidraw0 to hidraw2 BEFORE connecting used and DMESG has shown me hidraw3 for the sixaxis . And I pressed the Button BEFORE using the command . I tried it with killed processes but still same . Is my legit Sixaxis an legit Sixaxis or an FAKE ? I have an second , 3rd Party Controller but I am not going to try that one because it has no accelerators . 

And just an question : Are the accelerators in QtSixA the same as in MotionInJoy : The Tilting ?

---

### Post by AngelDE98 on 2010-12-30
NVM ... It is just confusing me why sixad-raw is not working ( Without it I get no tilting / accelerators ) ... 

But I get my Emulator working with my sixaxis :D 

Still I wonder how you make it and you just rock :guitar: 

Please just fix this error . 

Some technical data :

Model number : CECHZC1E
Barcode ( lol ? :p ) : 1628216400944 
Made by : Sony Computer Entertainment Inc.
MADE IN CHINA ( :lol: )

---

### Post by falkTX on 2010-12-30
> **AngelDE98 said:**
> NVM ... It is just confusing me why sixad-raw is not working ( Without it I get no tilting / accelerators ) ... 

But I get my Emulator working with my sixaxis :D 

Still I wonder how you make it and you just rock :guitar: 

Please just fix this error . 

Some technical data :

Model number : CECHZC1E
Barcode ( lol ? :p ) : 1628216400944 
Made by : Sony Computer Entertainment Inc.
MADE IN CHINA ( :lol: )


Please update, I've just fixed it :p


The issue was caused by a change in the kernel (happens from time to time).
Basically the Sixaxis has a buffer size of 50, but sometimes we get 49...
using this code:
```
          for (i=50; i>0; i--) {
            buf[i] = buf[i-1];
          }
```
fixes the issue, although it looks a bit hacky...

Anyway, it's working again

---

### Post by AngelDE98 on 2010-12-30
OH MY GAWD ! IT WORKS ... only in terminal mode ... The GUI gives me the same error :lolflag: 

But in terminal it even says that it has an non-standart buffer size ```
sixad-raw[31647]: Connected 'PLAYSTATION(R)3 Controller (hidraw)' [Battery EF]sixad-raw[31647]: Notice: non-standard Sixaxis buffer size (49)
' [Battery EF]

```

Just fix the gui that it is not sending another FAILURE message to me because it is not telling what it says at buffer size 50 ... 

But big thanx ! The Tilting is working ! You rock :guitar:

---

### Post by falkTX on 2010-12-30
> **AngelDE98 said:**
> OH MY GAWD ! IT WORKS ... only in terminal mode ... The GUI gives me the same error :lolflag: 

But in terminal it even says that it has an non-standart buffer size ```
sixad-raw[31647]: Connected 'PLAYSTATION(R)3 Controller (hidraw)' [Battery EF]sixad-raw[31647]: Notice: non-standard Sixaxis buffer size (49)
' [Battery EF]

```

Just fix the gui that it is not sending another FAILURE message to me because it is not telling what it says at buffer size 50 ... 

But big thanx ! The Tilting is working ! You rock :guitar:

hehe, I forgot about it...

But sixad-raw changes cannot be just adjusted in the GUI.
I need to temporarily disable it for now...

---

### Post by blierp on 2010-12-31
can anyone give me some pointers on how to automate this as much as possible? A bit of information about my system:

[LIST]
[*]ubuntu 10.10 on a mac mini (built-in bluetooth)
[*]using a bluetooth keyboard to control this machine, i've got a feeling this will hinder the process of automating qtsixa the most.
[/LIST]

couldn't get this thing running via the gui but in the console with sixad stop and start it worked. My user is in the sixad group.

while i really like that i can use my ps3 controller to play emulated games i don't like to have to manually start and stop sixad everytime i play ;)

---

### Post by falkTX on 2011-01-03
> **blierp said:**
> can anyone give me some pointers on how to automate this as much as possible? A bit of information about my system:

[LIST]
[*]ubuntu 10.10 on a mac mini (built-in bluetooth)
[*]using a bluetooth keyboard to control this machine, i've got a feeling this will hinder the process of automating qtsixa the most.
[/LIST]

couldn't get this thing running via the gui but in the console with sixad stop and start it worked. My user is in the sixad group.

while i really like that i can use my ps3 controller to play emulated games i don't like to have to manually start and stop sixad everytime i play ;)

Hi,

Starting the GUI will *not* start the backend driver (I have no idea why people think that...)

Usually pressing the PS button is enough to start sixad,
but something may happen if you have other BT stuff connected, yes.
The only bluetooth capable devices I have are the sixaxis, so I was never able to test this...

Anyway, it should work fine if you connect the sixaxis first, then the keyboard

---

### Post by blierp on 2011-01-04
thanks for your reply. I encountered another problem: my keyboard disconnects itself after 10 minutes of inactivity. If sixad is not running i can easily press a button and it reconnects. However, with sixad running this doesn't work. It just won't connect untill i kill sixad again. Any idea why this happens?

---

### Post by iDVB on 2011-01-04
First off, looks like great work you've done here. Unfortunately, nothing yet works for me.
I'm having trouble getting this running on Ubuntu 10.10 with either of my SixAxis controllers.

Specs:
Ubuntu 10.10
Asus USB-BT211 Dongle ( [http://goo.gl/Gigwk](http://goo.gl/Gigwk) ) (v2.1)


I've followed the steps on the QTSixa site ( [http://qtsixa.sourceforge.net/](http://qtsixa.sourceforge.net/) ) 
I've followed a tutuial I found ( [http://goo.gl/6MtPk](http://goo.gl/6MtPk) ) on YouTube.
I also read around and only got more confused when I saw this ( [http://goo.gl/6MtPk](http://goo.gl/6MtPk) ) in the ubuntu docs.
I've tried pairing with USB cable attached as well as NOT attached.
I also had to "apt-get install joystick" in order to even get USB working. I never saw anyone mention that install step?

Here are a few questions I've come up with:
1) Am I supposed to be able to pair the SixAxis with ubuntu and my adapter "out of the box" without the help of QTSixA? That is what your docs seem to hint at. My SixAxis does not appear in the found list of my adapter when searching. (SixAxis in pair mode)

2) Based on the Ubuntu Docs I also tried:
```
$ sudo apt-get install libusb-dev libusb-0.1-4
```

But I get the same results in QTSixa and my adaptor.

This is what I see in QTSixa with USB attached and while "trying" to pair w BT.
[[IMG]http://img5.imagebanana.com/img/f0ixqu49/thumb/QtSixA_006.png[/IMG]](http://www.imagebanana.com/view/f0ixqu49/QtSixA_006.png)

Does anyone have any ideas?

---

### Post by artik1024 on 2011-01-15
Many falkTX for your work. What I don't understand is why when I use a PS3 controller with USB, XBMC works. when I pair my sixaxis with Qtsix, it works, but not under XBMC.

In USB mode, I need to enter :

```
python /home/xbmc/EventClients/Clients/PS3\ BD\ Remote/ps3_remote.py localhost &> /etc/init.d/start_remote.log
```

To get ot working, what to type to get BT working ? What did I do wrong ?

---

### Post by falkTX on 2011-01-15
> **artik1024 said:**
> Many falkTX for your work. What I don't understand is why when I use a PS3 controller with USB, XBMC works. when I pair my sixaxis with Qtsix, it works, but not under XBMC.

In USB mode, I need to enter :

```
python /home/xbmc/EventClients/Clients/PS3\ BD\ Remote/ps3_remote.py localhost &> /etc/init.d/start_remote.log
```

To get ot working, what to type to get BT working ? What did I do wrong ?

I dont know exactly what that command does, but you should check if the Sixaxis configuration is the default (ie, joystick mode only).

You can always create an input profile if everything else fails...

---

### Post by falkTX on 2011-01-15
> **iDVB said:**
> First off, looks like great work you've done here. Unfortunately, nothing yet works for me.
I'm having trouble getting this running on Ubuntu 10.10 with either of my SixAxis controllers.

Specs:
Ubuntu 10.10
Asus USB-BT211 Dongle ( [http://goo.gl/Gigwk](http://goo.gl/Gigwk) ) (v2.1)


I've followed the steps on the QTSixa site ( [http://qtsixa.sourceforge.net/](http://qtsixa.sourceforge.net/) ) 
I've followed a tutuial I found ( [http://goo.gl/6MtPk](http://goo.gl/6MtPk) ) on YouTube.
I also read around and only got more confused when I saw this ( [http://goo.gl/6MtPk](http://goo.gl/6MtPk) ) in the ubuntu docs.
I've tried pairing with USB cable attached as well as NOT attached.
I also had to "apt-get install joystick" in order to even get USB working. I never saw anyone mention that install step?

Here are a few questions I've come up with:
1) Am I supposed to be able to pair the SixAxis with ubuntu and my adapter "out of the box" without the help of QTSixA? That is what your docs seem to hint at. My SixAxis does not appear in the found list of my adapter when searching. (SixAxis in pair mode)

2) Based on the Ubuntu Docs I also tried:
```
$ sudo apt-get install libusb-dev libusb-0.1-4
```

But I get the same results in QTSixa and my adaptor.

This is what I see in QTSixa with USB attached and while "trying" to pair w BT.
[[IMG]http://img5.imagebanana.com/img/f0ixqu49/thumb/QtSixA_006.png[/IMG]](http://www.imagebanana.com/view/f0ixqu49/QtSixA_006.png)

Does anyone have any ideas?

Hi, sorry for the late reply

Don't care about the ubuntu documentation, it's very old (could be a fossil by now...)
Installing 'joystick' is *not* required.

Basically, here are the steps required to use Sixaxis, in bluetooth mode:

1 - Pair the Sixaxis to your bluetooth dongle
This is made by connecting the sixaxis over USB, with the bluetooth dongle on USB too (unless it's internal, of course).
You can check if the sixaxis is properly connected with 'lsusb', and the bluetooth dongle with 'hcitool dev'.
If all is ok, run:
```
sudo sixpair
```
And the sixaxis will be paired, first step completed. You can now remove the sixaxis from USB.

2 - Connect over bluetooth
Usually, if the sixaxis is paired, pressing the PS button should auto-connect the sixaxis (it has a udev rule).
If that doesnt happen, wait until it stops blinking (you can force it by using 'hcitool dc <mac>' [get <mac> using 'hcitool con']).
Then run:
```
sixad --stop
sixad --start
```
And press the PS button again. It *must* connect now. If not, consider it a bug and please report back to me.

One thing worth trying is edit '/etc/default/sixad' and change debug mode to 1 (DEBUG=1), so you can get more messages out of the sixad.

You can do all this without even starting the GUI. (QtSixA).
Use the GUI if you need to change profiles, or maybe to disconnect stuff.


btw, you may ask 'how do I know when the sixaxis is connected?'.
If you ran 'sixad --start' from the terminal, a message will printed everytime a device connects (sixaxis or keypad).
Unless you changed the default profile, the sixaxis should animate the leds (and rumble if supported).


I hope this clears up something ;)

---

### Post by falkTX on 2011-01-15
> **blierp said:**
> thanks for your reply. I encountered another problem: my keyboard disconnects itself after 10 minutes of inactivity. If sixad is not running i can easily press a button and it reconnects. However, with sixad running this doesn't work. It just won't connect untill i kill sixad again. Any idea why this happens?

This happens because the sixad driver kinda conflicts with the normal bluetooth (the sixaxis is a very weird device).
I've been trying to hack into bluez to make the sixaxis work out-of-the-box (no more sixad), but it's not easy at all...

and I dont have any other bluetooth devices except 2 sixaxis and a keypad, so I can't test/work this, sorry

but if you find a workaround, let me know

---

### Post by quids on 2011-01-18
My PS3 controller stopped connecting after a recent update on the console, I just assumed that Sony had removed yet another feature.
But following your instructions in post #789 worked a treat. Thanks falkTX, and thanks for doing this great app.


I did the video on Youtube [http://goo.gl/6MtPk](http://goo.gl/6MtPk) hope you don't mind?
Thought that qtsixa could do with a bit more publicity. I only came across it by accident and started with an outdated Karmic version.

---

### Post by falkTX on 2011-01-18
> **quids said:**
> My PS3 controller stopped connecting after a recent update on the console, I just assumed that Sony had removed yet another feature.
But following your instructions in post #789 worked a treat. Thanks falkTX, and thanks for doing this great app.


I did the video on Youtube [http://goo.gl/6MtPk](http://goo.gl/6MtPk) hope you don't mind?
Thought that qtsixa could do with a bit more publicity. I only came across it by accident and started with an outdated Karmic version.

nice, many thanks!

You're free to make any videos you want about it.
I did one too, some time ago; it's outdated now though...

---

### Post by falkTX on 2011-01-18
Hey guys,

I have good news for those having troubles with the sixad driver - the Legacy mode is back!
*(if you dont know what it is, ignore this)*

The GUI has no option for this yet, but you can enable by editing '/etc/default/sixad' and set LEGACY to 1:
```
LEGACY=1
```

Then the next sixaxis to be connected will use the default driver, not the sixad one.
This allows:
- kill sixad anytime, and the sixaxis will be kept connected (useful if you have other bluetooth devices, like user "blierp")
- sixad is somewhat not working for you

But the default driver is missing some features:
- no LED support
- no accelerometers
- no rumble

the legacy mode will create the joystick only (no mouse/keyboard emulation).
but you can easily work-around this. check 'dmesg' and you'll notice that this method creates a hidraw device, which then can be used with 'sixad-raw' to allow mouse/keyboard emulation.

enjoy!

---

### Post by falkTX on 2011-01-18
sorry buggy internet, ignore this please...

---

### Post by falkTX on 2011-01-21
@quids

I noticed in the video, you said neverball profile was not working.
I checked it and you're right, should be fixed now.

---

### Post by quids on 2011-01-22
Thats great, it worked a treat. So much easier and better playing Neverball with a PS3 controller

Thanks falkTX

---

### Post by Jungleboss on 2011-01-23
I've tried it out on my Ubuntu client and it works! :)

If I do some changes to profiles or change any options where's the config files saved? It seems that no files are updated in my ~/.qtsixa2 directory when I do changes.
I'm thinking of doing the parameter changes on my client, and then transfer them to my Xbmc Ubuntu machine (that doesn't have Gnome installed).

One more question:
Sometimes (quite often) when I press the PS button the controller never connects to the BT adapter. If I wait and try again after the leds on the controller stops blinking it usually works. And even if it connects the first time it can take up to 10-15 seconds.

What can be the cause of this? Are some usb BT adapter better than others? 
Or can it be optimised by some parameter in Ubuntu, so I don't have to press the PS button two times or manually use sixad --stop, --start, if it don't work automatically the first time.


Thanks for your work!

---

### Post by falkTX on 2011-01-24
> **Jungleboss said:**
> I've tried it out on my Ubuntu client and it works! :)

If I do some changes to profiles or change any options where's the config files saved? It seems that no files are updated in my ~/.qtsixa2 directory when I do changes.
I'm thinking of doing the parameter changes on my client, and then transfer them to my Xbmc Ubuntu machine (that doesn't have Gnome installed).

One more question:
Sometimes (quite often) when I press the PS button the controller never connects to the BT adapter. If I wait and try again after the leds on the controller stops blinking it usually works. And even if it connects the first time it can take up to 10-15 seconds.

What can be the cause of this? Are some usb BT adapter better than others? 
Or can it be optimised by some parameter in Ubuntu, so I don't have to press the PS button two times or manually use sixad --stop, --start, if it don't work automatically the first time.


Thanks for your work!

The auto-connect feature depends on udev and bluez, but it doesnt work all the time. I dont have a proper solution for this yet, unless you enable sixad at boot ('sixad --boot-yes')

your input profiles are saved in ~/.qtsixa/profiles (just the mouse/key mapping), and the system/global profiles are saved as:
/var/lib/sixad/profiles/<mac> (being '<mac>' your sixaxis mac address, or 'hidraw' or 'default'.

please note that, when you update your input profiles, you'll need to re-apply that profiles system-wide (to copy the new data to /var/...)

---

### Post by Jungleboss on 2011-01-24
> **falkTX said:**
> The auto-connect feature depends on udev and bluez, but it doesnt work all the time. I down have a proper solution for this yet, unless you enable sixad at boot ('sixad --boot-yes')

your input profiles are saved in ~/.qtsixa/profiles (just the mouse/key mapping), where the system/global profiles are saved as:
/var/lib/sixad/profiles/<mac> (being '<mac>' your sixaxis mac address, or 'hidraw' or 'default'.

please note that, when you update your input profiles, you'll need to re-apply that profiles system-wide (to copy the new data to /var/...)

I've enabled sixad at boot. But connecting the contoller doesn't always work the first time. If it doesn't work the first time it usually works when I try a second time (after the leds have stopped blinking).

Thanks, will have that in mind when I transfer the settings to my XBMC machine.

---

### Post by disturbedite on 2011-02-21
using a ps3 pad with bluetooth (wirelessly) i was having the problem of the accelerometers (axes 5 & 6) constantly overwriting any other input when trying to map controls in gambatte, yet mapping controls worked fine with bsnes and mame. so before i found that disabling the accelerometers could be done with QtSixA i found that i needed to create a new 'joystick.conf' file for xorg as well as references to it in my 'evdev.conf' file to disable the accelerometers (using Option "MapAxisX" "mode=none" for axes 5 & 6). doing this successfully disabled accelerometers.
however, this another problem: the pad was now controlling the cursor/mouse. (again, before i realized this feature could be disabled with QtSixA) i had to use Option "StartMouseEnabled" "False" to disable this feature.
however, this DID NOT disable the pad controlling the cursor/mouse. i then found that i could disable these features (accelerometers and pad as mouse) with QtSixA.
***however***, there is yet another problem: i have noticed that QtSixA utilizes hal for some stuff. hal was deprecated by xorg with version 7.6 in favor other alternatives. a number of recent versions of distros have removed hal entirely (including the distro i use, opensuse).
i believe evdev is what should be used now. do you have any plans to rewrite QtSixA to support evdev instead of hal? or implement evdev support since hal is now dead?
hal being non-existent on a system (as in my case) causes certain features (saving the settings of turning off the pad as mouse/keyboard for example) from being saved.
i did notice that you said using the legacy driver is a workaround for this sort of thing though and have decided to use the legacy driver. i will report back if there is any problems with it.

---

### Post by falkTX on 2011-02-23
> **disturbedite said:**
> using a ps3 pad with bluetooth (wirelessly) i was having the problem of the accelerometers (axes 5 & 6) constantly overwriting any other input when trying to map controls in gambatte, yet mapping controls worked fine with bsnes and mame. so before i found that disabling the accelerometers could be done with QtSixA i found that i needed to create a new 'joystick.conf' file for xorg as well as references to it in my 'evdev.conf' file to disable the accelerometers (using Option "MapAxisX" "mode=none" for axes 5 & 6). doing this successfully disabled accelerometers.
however, this another problem: the pad was now controlling the cursor/mouse. (again, before i realized this feature could be disabled with QtSixA) i had to use Option "StartMouseEnabled" "False" to disable this feature.
however, this DID NOT disable the pad controlling the cursor/mouse. i then found that i could disable these features (accelerometers and pad as mouse) with QtSixA.
***however***, there is yet another problem: i have noticed that QtSixA utilizes hal for some stuff. hal was deprecated by xorg with version 7.6 in favor other alternatives. a number of recent versions of distros have removed hal entirely (including the distro i use, opensuse).
i believe evdev is what should be used now. do you have any plans to rewrite QtSixA to support evdev instead of hal? or implement evdev support since hal is now dead?
hal being non-existent on a system (as in my case) causes certain features (saving the settings of turning off the pad as mouse/keyboard for example from being saved).
i did notice that you said using the legacy driver is a workaround for this sort of thing though and have decided to use the legacy driver. i will report back if there is any problems with it.

hey there,

you are using the old version of QtSixA, where HAL was used for profiles (now the code is built-in, using UInput kernel driver).

I haven't officially released the new version (tagged 1.5.0), but it's on the PPAs for Lucid, Maverick and Natty.
So, i have to guess you're not using Ubuntu...

I've uploaded the latest code (still in beta) of the upcoming 1.5.0 release:
[http://sourceforge.net/projects/qtsixa/files/QtSixA%201.5.0%20Beta/qtsixa-1.4.96.tar.gz/download](http://sourceforge.net/projects/qtsixa/files/QtSixA%201.5.0%20Beta/qtsixa-1.4.96.tar.gz/download)

Things are a lot different in this version, to name a few:

1) Using UInput for mouse/keyboard profiles
(this method only allows only 1 key per button, using joystick axis and mouse simultaneously is broken at the moment)

2) Rumble is working

3) Every time you connect a Sixaxis, you'll know it's battery charge status (value 02 to 05, or 'EE' when charging)

4) Updated GUI
(all devices are managed separately now)

5) Added 'sixad-jack' utility
(Allows to use a Sixaxis as a MIDI keyboard)

and some other small stuff (code was re-written in C++...)


Let me know if you got any issues

---

### Post by disturbedite on 2011-02-23
thank you for your response falkTX.
i use opensuse. i'm sure i have all the dependencies installed after having read the INSTALL file, but compilation is failing with this:
> make
make -C qtsixa
make[1]: Entering directory `/home/echoes/compile/qtsixa-1.4.96/qtsixa'
pyuic4 -o ./gui/ui_qtsixa_mainw.py ./gui/ui/qtsixa_mainw.ui
pyuic4 -o ./gui/ui_qtsixa_aboutw.py ./gui/ui/qtsixa_aboutw.ui
pyuic4 -o ./gui/ui_qtsixa_managew.py ./gui/ui/qtsixa_managew.ui
pyuic4 -o ./gui/ui_qtsixa_newdevw.py ./gui/ui/qtsixa_newdevw.ui
pyuic4 -o ./gui/ui_qtsixa_newprofilew.py ./gui/ui/qtsixa_newprofilew.ui
pyuic4 -o ./gui/ui_qtsixa_preferencesw.py ./gui/ui/qtsixa_preferencesw.ui
pyuic4 -o ./gui/ui_qtsixa_referencew.py ./gui/ui/qtsixa_referencew.ui
pyuic4 -o ./gui/ui_qtsixa_sixpairw.py ./gui/ui/qtsixa_sixpairw.ui
pyrcc4 -o ./gui/qtsixa_rc.py ./icons/qtsixa.qrc
make[1]: Leaving directory `/home/echoes/compile/qtsixa-1.4.96/qtsixa'
make -C utils
make[1]: Entering directory `/home/echoes/compile/qtsixa-1.4.96/utils'
gcc -Wall -O2 hidraw-dump.c -o bins/hidraw-dump
gcc -Wall -O2 sixad-jack.c -o bins/sixad-jack -ljack -lm
gcc -Wall -O2 sixpair.c -o bins/sixpair -lusb
sixpair.c:9:17: fatal error: usb.h: No such file or directory
compilation terminated.
make[1]: *** [tools] Error 1
make[1]: Leaving directory `/home/echoes/compile/qtsixa-1.4.96/utils'
make: *** [build] Error 2

by the way, i found that my conclusion of needing to create a 'joystick.conf' file and a reference to it in my evdev.conf file was wrong. it was actually causing the joystick to act as cursor/mouse, even with the option to disable it.

---

### Post by falkTX on 2011-02-25
> **disturbedite said:**
> thank you for your response falkTX.
i use opensuse. i'm sure i have all the dependencies installed after having read the INSTALL file, but compilation is failing with this:


by the way, i found that my conclusion of needing to create a 'joystick.conf' file and a reference to it in my evdev.conf file was wrong. it was actually causing the joystick to act as cursor/mouse, even with the option to disable it.

you're missing some header files.
Make sure you got the devel packages of:
dbus
libusb
libbluetooth (bluez)
jack [for the sixad-jack utility]

Maybe others, not sure right now

---

### Post by disturbedite on 2011-02-25
> **falkTX said:**
> you're missing some header files.
Make sure you got the devel packages of:
dbus
libusb
libbluetooth (bluez)
jack [for the sixad-jack utility]

Maybe others, not sure right now
i was missing the bluez development package but that apparently wasn't the problem. i've got all of the development packages for those installed but it seems to be failing on (lib)usb. on opensuse the only libusb development pacakge is: libusb-1_0-devel and it ***IS*** installed but it is still generating the same error as before.
also, i noticed version 1.4.97 in the changelog. could you upload the source for this version to the sourceforge page so i (and others) can download it?

---

### Post by falkTX on 2011-02-26
> **disturbedite said:**
> i was missing the bluez development package but that apparently wasn't the problem. i've got all of the development packages for those installed but it seems to be failing on (lib)usb. on opensuse the only libusb development pacakge is: libusb-1_0-devel and it ***IS*** installed but it is still generating the same error as before.
also, i noticed version 1.4.97 in the changelog. could you upload the source for this version to the sourceforge page so i (and others) can download it?

hm, i'm not sure about the usb error. it's only needed for the 'sixpair' utility.
If you already have it, you can just comment out the line in the makefile to stop compiling it. (then also remove from the install process too).

the version I uploaded is the latest. it's all 1.5.0-beta, I just bumped the version in the PPA

---

### Post by disturbedite on 2011-02-27
> **falkTX said:**
> hm, i'm not sure about the usb error. it's only needed for the 'sixpair' utility.
If you already have it, you can just comment out the line in the makefile to stop compiling it. (then also remove from the install process too).
i don't have it already and i need sixpair.
i think perhaps something is wrong in the detecting of the libusb development library because i have it installed. here is a list of the files it includes:

libusb-1_0-devel-1.0.8-16.1.x86_64

/usr/include/libusb-1.0
**/usr/include/libusb-1.0/libusb.h**
/usr/lib64/libusb-1.0.so
/usr/lib64/pkgconfig/libusb-1.0.pc
/usr/share/doc/packages/libusb-1_0-devel
/usr/share/doc/packages/libusb-1_0-devel/PORTING

---

### Post by disturbedite on 2011-03-01
could you please look into the above problem falkTX?

---

### Post by falkTX on 2011-03-04
> **disturbedite said:**
> could you please look into the above problem falkTX?

Please try opening utils/Makefile and change:
```
gcc -Wall -O2 sixpair.c -o bins/sixpair -lusb
```
to:
```
gcc -Wall -O2 sixpair.c -o bins/sixpair -lusb -I/usr/include/libusb-1.0/
```

That should do it

---

### Post by Teraspes on 2011-03-07
Hi!
I have installed QtSixA through the PPA, so I suppose I have the most recent version. I have connected my Dual Shock 3 controller to the computer with an USB-cable and it shows up in the software. But I can't get the profile stuff to work, so that the controller controls the mouse arrow head. I don't even know if it even works as an joystick. :neutral: So, I need a piece of advice to get the controller to work as a mouse, please.

EDIT: I downloaded both Extreme Tux Racer and Supertuxkart, and the controller worked in neither of the games...

---

### Post by falkTX on 2011-03-08
> **Teraspes said:**
> Hi!
I have installed QtSixA through the PPA, so I suppose I have the most recent version. I have connected my Dual Shock 3 controller to the computer with an USB-cable and it shows up in the software. But I can't get the profile stuff to work, so that the controller controls the mouse arrow head. I don't even know if it even works as an joystick. :neutral: So, I need a piece of advice to get the controller to work as a mouse, please.

EDIT: I downloaded both Extreme Tux Racer and Supertuxkart, and the controller worked in neither of the games...

hm... the sixaxis should work just fine in USB...

BUT, the profiles are not available for USB, only for bluetooth connections.
There are tools to map joystick tools to mouse/keyboard if you can only use USB

---

### Post by Teraspes on 2011-03-08
Aha, I didn't know that. Can you recommend a tool like that? :)

---

### Post by falkTX on 2011-03-08
> **Teraspes said:**
> Aha, I didn't know that. Can you recommend a tool like that? :)

hmm... I actually never used them, cause I use bluetooth (I make my own software when I need... ;))

guys, can you comment on this?
[tools to map joystick keys to mouse/keyboard]

---

### Post by disturbedite on 2011-03-13
> **falkTX said:**
> Please try opening utils/Makefile and change:
```
gcc -Wall -O2 sixpair.c -o bins/sixpair -lusb
```
to:
```
gcc -Wall -O2 sixpair.c -o bins/sixpair -lusb -I/usr/include/libusb-1.0/
```

That should do it

sorry it took me so long to respond, but here is the result:
```
make -j3
gcc -Wall -O2 hidraw-dump.c -o bins/hidraw-dump
make -C hcid
make[1]: Entering directory `/home/echoes/compile/qtsixa-1.4.96/utils/hcid'
make[1]: warning: jobserver unavailable: using -j1.  Add `+' to parent make rule.
cc -DHAVE_CONFIG_H -I. -I./mod   -I/usr/include/dbus-1.0 -I/usr/lib/dbus-1.0/include   -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include   -g -O2 -g -Wall -O2 -D_FORTIFY_SOURCE=2 -c common/oui.c
cc -DHAVE_CONFIG_H -I. -I./mod   -I/usr/include/dbus-1.0 -I/usr/lib/dbus-1.0/include   -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include   -g -O2 -g -Wall -O2 -D_FORTIFY_SOURCE=2 -c common/dbus.c
gcc -Wall -O2 sixad-jack.c -o bins/sixad-jack -ljack -lm
In file included from /usr/include/glib-2.0/glib/galloca.h:34:0,
                 from /usr/include/glib-2.0/glib.h:32,
                 from common/dbus.c:36:
/usr/include/glib-2.0/glib/gtypes.h:34:24: fatal error: glibconfig.h: No such file or directory
compilation terminated.
make[1]: *** [common_so] Error 1
make[1]: Leaving directory `/home/echoes/compile/qtsixa-1.4.96/utils/hcid'
make: *** [hcid_bin] Error 2
make: *** Waiting for unfinished jobs....
gcc -Wall -O2 sixpair.c -o bins/sixpair -lusb -I/usr/include/libusb-1.0/
sixpair.c:9:17: fatal error: usb.h: No such file or directory
compilation terminated.
make: *** [tools] Error 1
```

so same problem. strange thing is about the missing glibconfig.h error too is that i have glibconfig.h installed via glib2-devel...

---

### Post by falkTX on 2011-03-13
> **disturbedite said:**
> sorry it took me so long to respond, but here is the result:
```
make -j3
gcc -Wall -O2 hidraw-dump.c -o bins/hidraw-dump
make -C hcid
make[1]: Entering directory `/home/echoes/compile/qtsixa-1.4.96/utils/hcid'
make[1]: warning: jobserver unavailable: using -j1.  Add `+' to parent make rule.
cc -DHAVE_CONFIG_H -I. -I./mod   -I/usr/include/dbus-1.0 -I/usr/lib/dbus-1.0/include   -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include   -g -O2 -g -Wall -O2 -D_FORTIFY_SOURCE=2 -c common/oui.c
cc -DHAVE_CONFIG_H -I. -I./mod   -I/usr/include/dbus-1.0 -I/usr/lib/dbus-1.0/include   -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include   -g -O2 -g -Wall -O2 -D_FORTIFY_SOURCE=2 -c common/dbus.c
gcc -Wall -O2 sixad-jack.c -o bins/sixad-jack -ljack -lm
In file included from /usr/include/glib-2.0/glib/galloca.h:34:0,
                 from /usr/include/glib-2.0/glib.h:32,
                 from common/dbus.c:36:
/usr/include/glib-2.0/glib/gtypes.h:34:24: fatal error: glibconfig.h: No such file or directory
compilation terminated.
make[1]: *** [common_so] Error 1
make[1]: Leaving directory `/home/echoes/compile/qtsixa-1.4.96/utils/hcid'
make: *** [hcid_bin] Error 2
make: *** Waiting for unfinished jobs....
gcc -Wall -O2 sixpair.c -o bins/sixpair -lusb -I/usr/include/libusb-1.0/
sixpair.c:9:17: fatal error: usb.h: No such file or directory
compilation terminated.
make: *** [tools] Error 1
```

so same problem. strange thing is about the missing glibconfig.h error too is that i have glibconfig.h installed via glib2-devel...

This will require another '-I<some-path>'.
Find which directory has the "glibconfig.h" and append the '-I/that/path' as done last time

---

### Post by disturbedite on 2011-03-13
> **falkTX said:**
> This will require another '-I<some-path>'.
Find which directory has the "glibconfig.h" and append the '-I/that/path' as done last time
i think you missed the last part of my last post, specifically, the part about making that change to the usb.h path not working.
i changed the sixad-jack line to read the way you told me (gcc -Wall -O2 sixad-jack.c -o bins/sixad-jack -ljack -lm -I/usr/lib64/glib-2.0/include/) but the exact same error was produced.
it is like your source is failing to see files that exist in the places it expects to find them.

---

### Post by falkTX on 2011-03-15
> **disturbedite said:**
> i think you missed the last part of my last post, specifically, the part about making that change to the usb.h path not working.
i changed the sixad-jack line to read the way you told me (gcc -Wall -O2 sixad-jack.c -o bins/sixad-jack -ljack -lm -I/usr/lib64/glib-2.0/include/) but the exact same error was produced.
it is like your source is failing to see files that exist in the places it expects to find them.

it's very weird...

remind me again, which exact linux distro (and version) are you using?
also, 32bit or 64bit?

---

### Post by sjvega on 2011-03-17
Hello: I'm trying to use QTsixa with a wired controller but I'm not having any success. I've read somewhere to use the sixad-raw but im having this error:

```
sudo sixad-raw /dev/hidraw1
sixad-raw[25675]: uinput_open()::open(uinput_filename[i], O_RDWR) - failed to open uinput
```


At this point I'm pretty clueless about what to do...
I'm ignoring some configuration I should do?

Thanks in advance, and sorry for the bad english.

---

### Post by falkTX on 2011-03-18
> **sjvega said:**
> Hello: I'm trying to use QTsixa with a wired controller but I'm not having any success. I've read somewhere to use the sixad-raw but im having this error:

```
sudo sixad-raw /dev/hidraw1
sixad-raw[25675]: uinput_open()::open(uinput_filename[i], O_RDWR) - failed to open uinput
```


At this point I'm pretty clueless about what to do...
I'm ignoring some configuration I should do?

Thanks in advance, and sorry for the bad english.

The UInput module probably is not loaded yet.
Try this:
```
sudo modprobe uinput
sudo sixad-raw /dev/hidrawX

```

It should work. If not, report back please.

---

### Post by sjvega on 2011-03-18
Thanks! Now it's working, even though i have to load the module every time I boot...

I have another issue now: the PS3 controller is now recognized as two inputs js0 and js1. js0 is the default with every sensible button activated, and I set the controller in QTsixa to disable them, which now is the controller in js1 (as I tested them using jstest). The problem is that many emulators detect both controllers (such as mednafen), and I cant seem to configure which to use in this instance, so the button mapping goes all over the place due to the sensible buttons. I there a way to inhibit js0 from being detected?
Thanks in advance!

---

### Post by falkTX on 2011-03-18
> **sjvega said:**
> Thanks! Now it's working, even though i have to load the module every time I boot...

I have another issue now: the PS3 controller is now recognized as two inputs js0 and js1. js0 is the default with every sensible button activated, and I set the controller in QTsixa to disable them, which now is the controller in js1 (as I tested them using jstest). The problem is that many emulators detect both controllers (such as mednafen), and I cant seem to configure which to use in this instance, so the button mapping goes all over the place due to the sensible buttons. I there a way to inhibit js0 from being detected?
Thanks in advance!

Hey again, nice to see it working.
you can add 'uinput' to '/etc/modules' to make it load at boot.

Note that in QtSixA you can define the profile for 'hidraw' which will change the settings used in sixad-raw.

And for games reading jsX events, you can do:
```
sudo rm /dev/input/jsX
```
To delete the old js device, although I really don't recommend this at all...

---

### Post by sjvega on 2011-03-18
Thanks for the quick response! 
I've tried removing the js0 but it's still being recognized, apparently it doesn't load the input from there. :(
I've already found a workaround for this particular problem, so thanks anyway. 
For anyone wondering I've used this config [here]("http://forum.fobby.net/index.php?t=msg&goto=1140&") for mednafen.
And [this]("http://ubuntuforums.org/showthread.php?p=8826233") one for Zsnes
And the rest of the programs I use, seem to recognize it just fine.
Cheers!

---

### Post by kruykaze on 2011-03-25
> **falkTX said:**
> hmm... I actually never used them, cause I use bluetooth (I make my own software when I need... ;))

guys, can you comment on this?
[tools to map joystick keys to mouse/keyboard]

qjoypad

---

### Post by quequotion on 2011-03-26
Is there a way to enable input *without* the joysticks taking over the mouse? (i want to emulate the keyboard and mouse buttons only)

I tried making my own input profile, but I can't even test if it's working since joystick->mouse function seriously interferes with gameplay.

here's the full MAC profile:```
# ##########################
# sixad configuration file #
########################## #

# Features
enable_leds 1
enable_joystick 1
enable_input 1
enable_rumble 0
enable_timeout 0

# LED
led_n_auto 0
led_n_number 1
led_anim 1

# Joystick
enable_buttons 1
enable_sbuttons 0
enable_axis 1
enable_accel 0
enable_accon 0
enable_speed 0
enable_pos 0

# Input - "GTA", by "quequotion"
key_select 47
key_l3 42
key_r3 58
key_start 1
key_up 17
key_right 32
key_down 31
key_left 30
key_l2 83
key_r2 28
key_l1 15
key_r1 273
key_tri 33
key_cir 272
key_squ 44
key_cro 45
key_ps 0
axis_left_type 0
axis_left_up 17
axis_left_right 32
axis_left_down 31
axis_left_left 30
axis_right_type 0
axis_right_up 77
axis_right_right 76
axis_right_down 73
axis_right_left 75
axis_speed 6
use_lr3 0

# Rumble
old_rumble_mode 0

# Timeout
timeout_mins 30
```

The layout is for GTA Vice City for wine, which has no built-in joystick support. It's a compromise between the PS2 layout and the messy PC defaults (there is no ideal solution, some keys will have to be remaped if possible).

Unfortunately, in this particular game, the mouse is used to control the camera.

The left analog stick takes control of the mouse, resulting in an ever spinning, twirling point of view. I can't figure out what the right analog stick is doing, but it is not using the buttons I configured in the profile, which are all num-pad keys.

What does ***_axis_type** do?

---

### Post by quequotion on 2011-03-26
> **falkTX said:**
> 
NOTES: ePSXe for Linux does not even have joystick support

I use your driver and two sixaxis with ePSXe (1.6.0) for linux.

You need a third-party joystick plugin.

Like most of the other psx emulators, ePSXe suffers from configuration hell.

I also use the same controllers with ePSXe (1.7.0) for wine, but the configuration is an even bigger mess because wine seems to think a single sixaxis represents several controllers.

In either case, the most difficult part is configuring the analog sticks and not letting them get in the way of configuring other buttons. The slightest vibration seems to put them off center one way or another, which gets picked up as the button setting for whatever. The trick is to hold the button you want to set down until you click on the next button to configure, but I know of no trick for configuring the actual joysticks, just luck and time.

---

### Post by bumder on 2011-04-10
> **emoguitarist06 said:**
> I bought the DS3 and I got it to work in ZNES by 
Settings>Configure Sixaxis>Profiles
Check use sixaxis as mouse/keyboard and using the Fake Joystick

However I cannot get it to work under ePSXe
I have not clue what to do.

Please help.

Trying to use my DS3 with zsnes at the moment :s

When connected over usb, it seems to detect it, no luck with bluetooth though.

I selected joystick=no, input-mouse/keyboard=yes and fake joystick profile, but does nothing when running zsnes. I leave Qtsixa running in the background.

What could i be doing wrong? Do you have to do something in zsnes first maybe?

---

### Post by bumder on 2011-04-16
UPDATE: got the DS3 controller to 'sync' with my system now, qtsixa shows it connected via bluetooth, giving signal/battery info.

(I followed [http://ubuntuforums.org/showpost.php?p=10360389&postcount=789](http://ubuntuforums.org/showpost.php?p=10360389&postcount=789) to get it to work though...)

Also got zsnes to finally take input from the dualshock3 by changing the profile in qtsixa to mouse/keyboard input, as well as joystick.

---

### Post by falkTX on 2011-04-22
> **quequotion said:**
> Is there a way to enable input *without* the joysticks taking over the mouse? (i want to emulate the keyboard and mouse buttons only)

I tried making my own input profile, but I can't even test if it's working since joystick->mouse function seriously interferes with gameplay.

here's the full MAC profile:```
# ##########################
# sixad configuration file #
########################## #

# Features
enable_leds 1
enable_joystick 1
enable_input 1
enable_rumble 0
enable_timeout 0

# LED
led_n_auto 0
led_n_number 1
led_anim 1

# Joystick
enable_buttons 1
enable_sbuttons 0
enable_axis 1
enable_accel 0
enable_accon 0
enable_speed 0
enable_pos 0

# Input - "GTA", by "quequotion"
key_select 47
key_l3 42
key_r3 58
key_start 1
key_up 17
key_right 32
key_down 31
key_left 30
key_l2 83
key_r2 28
key_l1 15
key_r1 273
key_tri 33
key_cir 272
key_squ 44
key_cro 45
key_ps 0
axis_left_type 0
axis_left_up 17
axis_left_right 32
axis_left_down 31
axis_left_left 30
axis_right_type 0
axis_right_up 77
axis_right_right 76
axis_right_down 73
axis_right_left 75
axis_speed 6
use_lr3 0

# Rumble
old_rumble_mode 0

# Timeout
timeout_mins 30
```

The layout is for GTA Vice City for wine, which has no built-in joystick support. It's a compromise between the PS2 layout and the messy PC defaults (there is no ideal solution, some keys will have to be remaped if possible).

Unfortunately, in this particular game, the mouse is used to control the camera.

The left analog stick takes control of the mouse, resulting in an ever spinning, twirling point of view. I can't figure out what the right analog stick is doing, but it is not using the buttons I configured in the profile, which are all num-pad keys.

What does ***_axis_type** do?

hey there,

I'm finishing up the sixad driver, so hopefully I'll soon release a spec of the configuration (to allow creation of other GUIs, or manual hacking too).

but basically *_axis_type changes what the axis do.
valid values are:
0 - do nothing (useful for joystick only mode)
2 - key mode (up, down, left, right will act as keyboard keys)
3 - mouse mode
^ (this is more tricky. when set, only up and right values become valid.
then up/right values can be REL_X, REL_Y, REL_WHEEL and REL_HWHEEL.
up controls Y axis, right controls X axis)

Use '/usr/include/linux/input.h' to do the value->int conversion.


I will release the final spec sometime soon anyway...

---

### Post by kruykaze on 2011-05-01
Can't connect my sixaxis once i upgraded to natty :(

---

### Post by falkTX on 2011-05-02
> **kruykaze said:**
> Can't connect my sixaxis once i upgraded to natty :(

Yes, I've experienced the same issue here.

I investigated it a bit, and it seems that bluetooth in kinda broken in kernel 2.6.38, which Natty uses.

I found a way around this, but it's too much hard work and a very ugly hack.
This leave us with 2 options:
1 - Use an older kernel (2.6.35 is fine, didn't test 2.6.36 or 2.6.37 yet).
2 - Don't use Natty at all and stay on Maverick or Lucid.

I'll see which latest kernel has working bluetooth, and upload it to the QtSixA PPA for Natty.

---

### Post by kruykaze on 2011-05-04
> **falkTX said:**
> Yes, I've experienced the same issue here.

I investigated it a bit, and it seems that bluetooth in kinda broken in kernel 2.6.38, which Natty uses.

I found a way around this, but it's too much hard work and a very ugly hack.
This leave us with 2 options:
1 - Use an older kernel (2.6.35 is fine, didn't test 2.6.36 or 2.6.37 yet).
2 - Don't use Natty at all and stay on Maverick or Lucid.

I'll see which latest kernel has working bluetooth, and upload it to the QtSixA PPA for Natty.

It has been fixed :)

---

### Post by highnz on 2011-05-09
Hi

first sorry for my worse English :oops:

I try to connect my new dualshock3 pad about usb

here my steps for this

1.fresh install from Kubuntu 11.04 natty 64bit with all updates (kernel 2.6.38-8 )
2. sudo apt-get install supertuxkart
3.sudo add-apt-repository ppa:falk-t-j/qtsixa
4.sudo apt-get update && sudo apt-get install qtsixa
5 start qtsixa
6. add my user to sixad
7. reboot
8. connect dualshock3 LED blink
9.start qtsixa and press ps buttons
10.Leds on controller going off
11.supertuxkart and try to config  controls nothing happens
12. i try to config dualshock about "joystick kde-controlmodul" this show me a gamepad
"Gasia Co.,Ltd PS(R) Gamepad (/dev/input/js0)" but is not configure able
[IMG]http://img825.imageshack.us/img825/2719/kdejoy.png[/IMG]

The curious things are:

1. all action button are grey in qtsixa
[IMG]http://img804.imageshack.us/img804/5453/qtsixa.png[/IMG]

2.the console output
-------------------------------------------------
highnz@privatlxn1:~$ qtsixa 
Qt version: 4.7.2
PyQt version: 4.8.3
QtSixA version: 1.5.0
Will use 'kdesudo' for root actions
QInotifyFileSystemWatcherEngine::addPaths: inotify_add_watch failed: Datei oder Verzeichnis nicht gefunden
QFileSystemWatcher: failed to add paths: /home/highnz/.config/ibus/bus
---------------------------------------------------
3.and i have the same picture in "joystick kde-controlmodul" on Natty live without qtsixa installed
but is not configure able too

4. I try step 9 again but the LED going not off

I tested the gamepad on windows7 and it works except for sixaxis

I hope thats is enogh at me to help
greets Highnz

---

### Post by falkTX on 2011-05-09
> **highnz said:**
> Hi

first sorry for my worse English :oops:

I try to connect my new dualshock3 pad about usb

here my steps for this

1.fresh install from Kubuntu 11.04 natty with all updates kernel 2.6.38-8
2. sudo apt-get install supertuxkart
3.sudo add-apt-repository ppa:falk-t-j/qtsixa
4.sudo apt-get update && sudo apt-get install qtsixa
5 start qtsixa
6. add my user to sixad
7. reboot
8. connect dualshock3 LED blink
9.start qtsixa and press ps buttons
10.Leds on controller going off
11.supertuxkart and try to config  controls nothing happens
12. i try to config dualshock about "joystick kde-controlmodul" this show me a gamepad
"Gasia Co.,Ltd PS(R) Gamepad (/dev/input/js0)" but is not configure able
[IMG]http://img825.imageshack.us/img825/2719/kdejoy.png[/IMG]

The curious things are:

1. all action button are grey in qtsixa
[IMG]http://img804.imageshack.us/img804/5453/qtsixa.png[/IMG]

2.the console output
-------------------------------------------------
highnz@privatlxn1:~$ qtsixa 
Qt version: 4.7.2
PyQt version: 4.8.3
QtSixA version: 1.5.0
Will use 'kdesudo' for root actions
QInotifyFileSystemWatcherEngine::addPaths: inotify_add_watch failed: Datei oder Verzeichnis nicht gefunden
QFileSystemWatcher: failed to add paths: /home/highnz/.config/ibus/bus
---------------------------------------------------
3.and i have the same picture in "joystick kde-controlmodul" on Natty live without qtsixa installed
but is not configure able too

4. I try step 9 again but the LED going not off

I tested the gamepad on windows7 and it works except for sixaxis

I hope thats is enogh at me to help
greets Highnz

I have the same issue too.
It's about this special device - 'Gasia Co.,Ltd PS(R) Gamepad', that is not a real Sixaxis.
it behaves differently than a normal Sixaxis, and I was not able to make it work so far... (even in USB)

But you're saying that it works in Windows?
Do you use some custom driver or does it just work?

---

### Post by highnz on 2011-05-09
Hi
Thanks for the fast response
Means this " It's about this special device - 'Gasia Co.,Ltd PS(R) Gamepad'"
That my device is not a original sony dualshock3 pad?

my dualschock3 works on windowsXP and Seven with this driver [http://www.motioninjoy.com/home-index-1.html](http://www.motioninjoy.com/home-index-1.html) the install it was tricky but its works

greetz highnz

---

### Post by falkTX on 2011-05-09
> **highnz said:**
> Hi
Thanks for the fast response
Means this " It's about this special device - 'Gasia Co.,Ltd PS(R) Gamepad'"
That my device is not a original sony dualshock3 pad?
Yes, it means you don't have an original Sixiaxis, but an imitation of it
(actually a very good imitation I would say, looks just like the real thing)
If you bought it from someone saying it was the real deal, I would trade it back...

> **highnz said:**
> 
my dualschock3 works on windowsXP and Seven with this driver [http://www.motioninjoy.com/home-index-1.html](http://www.motioninjoy.com/home-index-1.html) the install it was tricky but its works

Thanks, I'll install this in a virtual machine and try to find out more about this weird device.

---

### Post by DeathFire on 2011-05-20
[FONT=Arial][SIZE=2]Hi!

I am looking for some help with QTSixA 1.50. I am pretty excited to use this with my media centre and I feel it will be the perfect pairing once I get it working!

I am trying to connect my Dualshock 3 to Ubuntu 11.04 and am not having any luck.  I have tested bluetooth on it's own and it is working.

I have tried a few different things, and I am sure I must be missing a step somewhere:

What I did is this:

A fresh install of 11.04

Install QTSixA through the PPA:

[/SIZE][/FONT]sudo add-apt-repository ppa:falk-t-j/qtsixa
sudo apt-get update
sudo apt-get install qtsixa
[FONT=Arial][SIZE=2]
I also tried it with and without doing upgrades to the system after the fresh install as well as after installing QTSixA

I ran QTSixA, let the user get added to the sixad group

Rebooted (yes, I know I can just log off and on, but I wanted to make sure that everything was coming up right.

Plugged in via USB, the controller shows up, I then tried to pair.  The report window that comes up is blank.

So I tried to force a connection, and then paired, normally I still get nothing, however I have gotten this error a couple of times:

```
(gksu:2854): Gdk-CRITICAL **: IA__gdk_window_get_events: assertion `GDK_IS_WINDOW (window)' failed

(gksu:2854): GLib-GObject-CRITICAL **: g_object_ref: assertion `G_IS_OBJECT (object)' failed

(gksu:2854): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed
```I have also tried running sixad manually, the error here tips me off that something might not be right on the 11.04 install:

```
tv@tv-Veriton-N282G:~$ qtsixa
Qt version: 4.7.2
PyQt version: 4.8.3
QtSixA version: 1.5.0
Will use 'gksu' for root actions
error here, 3
```[/SIZE][/FONT]

I did see in some earlier posts that there have been issues with bluetooth and the kernel with 11.04 so I have tried with fresh and not so fresh installs of Ubuntu 10.10 and have had similar issues, I haven't had any luck, which tells me that there is a good chance that I may be doing something wrong.

Thank you in advance for any help that you can give me!

---

### Post by DeathFire on 2011-05-21
An update on my previous post.  I found a controller labeled Sixaxis and am having the same problems trying to connect it.

---

### Post by falkTX on 2011-05-23
> **DeathFire said:**
> An update on my previous post.  I found a controller labeled Sixaxis and am having the same problems trying to connect it.

The devices labeled "Gasia Gamepad" are tricky and they don't work right now.

As I said before, the GUI needs some tune-up, some stuff stopped working... :(

I'll publish a complete tutorial for QtSixA very very soon, but for now, try this:

1 - connect your sixaxis via USB (so as the bluetooth adapter, if not internal), and run:
```
sudo sixpair
```
then disconnect the sixaxis (usb cable)

2 - run sixad, and press the PS button on the sixaxis:
```
sudo sixad -s
```


There are a lot of issues with Natty's kernel (because 'hcid' simply doesn't work).
I'll need to investigate this more.

[FONT="Arial Black"]**MAJOR NOTE:**[/FONT]
If you're not using Ubuntu 11.04/Natty, you can force the sixaxis to *always* work by:
1 - enable sixad at boot:
```
sudo sixad --boot-yes
```
2 - remove bluez completely:
```
sudo apt-get remove bluez bluetooth
```
You won't be able to do any bluetooth stuff this way, but it makes the sixaxis *always* work.
*(Again, it will NOT work on Natty)*

Complete documentation coming soon!

---

### Post by kruykaze on 2011-05-25
Is there a command to disconnect sixaxis ? (I did a quick search and did not find an answer) 
Thanks.

---

### Post by falkTX on 2011-05-25
> **kruykaze said:**
> Is there a command to disconnect sixaxis ? (I did a quick search and did not find an answer) 
Thanks.

You can use 'hcitool'

simple usage: *(requires root/sudo)*
```
hcitool dc <mac-address>
```

to get the list of macs, use:
```
hcitool con
```

---

### Post by kimangroo on 2011-05-28
Hello,

I was wondering if you can use a DS3 to emulate a mouse and keyboard shortcuts on ubuntu with QtSixA?

Thx.

---

### Post by DeathFire on 2011-06-03
Thanks for the info falkTX.  I got it kind of working.  I will just be patient until you get everything updated! :)

---

### Post by kruykaze on 2011-06-03
i found it easier to have 2 scripts :

1 connect sixaxis
#!/bin/bash
echo password | sudo -S hcitool  dc XX:XX:XX:XX:XX:XX
echo password | sudo -S killall sixad-bin
echo password | sudo -S killall sixad
echo password | sudo -S sixad -s

2 kill off some distractions while playing mame and restart them and disconnect the controller when done.
#!/bin/bash
purple-remote setstatus?status=away
killall pithos
killall gwibber-service
mame
echo password | sudo -S hcitool  dc XX:XX:XX:XX:XX:XX
screen -d -m pithos
screen -d -m gwibber-service
purple-remote setstatus?status=available


But is there a better way to do this without saving my password in a script file?

---

### Post by Sebatian on 2011-06-04
I got my Sixaxis' to work yesterday, which was nice since I tried to get the bluetooth working for some time now. The problem is that today, it doesn't work anymore and I'm not sure were the problem lies.

There is a bluetotth connection and QtSixA displays the controller, but it doesn't seem to work as an input device anymore. There is, for example, no item in /dev/input for the controller.

The controller still works fine when connected through USB.

Anyone knows what could've gone wrong?

---

### Post by us3598 on 2011-06-04
Greetings FalkTX!

I am having an issue with compiling your driver, and although the solution may be somewhere in these 80+ pages, I figured I would just ask again. The device to install is a PowerA wired ps3 controller, OS is fresh 11.04 with all restricted-extras installed. Steps followed were at [https://help.ubuntu.com/community/Sixaxis](https://help.ubuntu.com/community/Sixaxis)

sixpair.c was downloaded into /home/user/sixpair
Output of gcc
> 
root@RYNO-CL38:/home/user/sixpair# gcc sixpair.c -lusb
sixpair.c:9:17: fatal error: usb.h: No such file or directory
compilation terminated.

Command was run with controller plugged in, as indicated by aforementioned community link.

Thank you in advance for your assistance, and your awesome contribution to the open source community!

---

### Post by falkTX on 2011-06-04
> **us3598 said:**
> Greetings FalkTX!

I am having an issue with compiling your driver, and although the solution may be somewhere in these 80+ pages, I figured I would just ask again. The device to install is a PowerA wired ps3 controller, OS is fresh 11.04 with all restricted-extras installed. Steps followed were at [https://help.ubuntu.com/community/Sixaxis](https://help.ubuntu.com/community/Sixaxis)

sixpair.c was downloaded into /home/user/sixpair
Output of gcc


Command was run with controller plugged in, as indicated by aforementioned community link.

Thank you in advance for your assistance, and your awesome contribution to the open source community!


please try:

```
gcc ... (stuff)  ... `pkg-config --libs --cflags libusb-1.0`
```
notice the new "pkg-config" stuff.

if this still fails, install libusb-dev and try again

---

### Post by us3598 on 2011-06-04
> **falkTX said:**
> please try:

```
gcc ... (stuff)  ... `pkg-config --libs --cflags libusb-1.0`
```
notice the new "pkg-config" stuff.

if this still fails, install libusb-dev and try again

> 
root@RYNO-CL38:/home/user/sixpair# gcc sixpair.c -lusb pkg-config --libs -cflags libusb-1.0
gcc: pkg-config: No such file or directory
gcc: libusb-1.0: No such file or directory
gcc: unrecognized option '-cflags'
cc1: error: unrecognized command line option "-flibs"


libusb-dev is installed, though I may be doing something wrong.

---

### Post by falkTX on 2011-06-04
> **us3598 said:**
> libusb-dev is installed, though I may be doing something wrong.

You're missing pkg-config...

---

### Post by us3598 on 2011-06-04
No it's installed on the system; when run independently it tells me to specify packages on the command line...hmm. Sorry to be a pain!

---

### Post by falkTX on 2011-06-04
> **us3598 said:**
> No it's installed on the system; when run independently it tells me to specify packages on the command line...hmm. Sorry to be a pain!

Then run:
```
pkg-config --libs --cflags libusb-1.0
```
copy the stuff printed and append it to the sixpair compile process.

---

### Post by us3598 on 2011-06-04
> **falkTX said:**
> Then run:
```
pkg-config --libs --cflags libusb-1.0
```
copy the stuff printed and append it to the sixpair compile process.

Okay that worked. Now when I run ./

> 
root@RYNO-CL38:/home/user/sixpair# ./sixpair
No controller found on USB busses.


The controller is plugged in.

---

### Post by us3598 on 2011-06-04
When we get this working, I will create a HOW-TO with a step by step process for users encountering similar issues, if that is alright with you. I figure that might give you a little break on troubleshooting!

---

### Post by falkTX on 2011-06-04
> **us3598 said:**
> Okay that worked. Now when I run ./
(...)
The controller is plugged in.

does 'lsusb' shows a Sony USB device? (Id is 054c:0368, or very similar).

If by any chance you've got a "Gasia Gamepad" (check 'dmesg'), you're out of luck...

---

### Post by us3598 on 2011-06-04
There are only two usb devices plugged in, output of lsusb is

> Bus 005 Device 002: ID 0f0d:0009 Hori Co., Ltd 
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 046d:c52e Logitech, Inc. 
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

The Hori device would be the controller. DMESG output for game controller:

> 
[  435.135214] input: HORI CO.,LTD. BDA GP1 as /devices/pci0000:00/0000:00:1d.3/usb5/5-2/5-2:1.0/input/input11

[  435.135490] generic-usb 0003:0F0D:0009.0003: input,hidraw2: USB HID v1.10 Gamepad [HORI CO.,LTD. BDA GP1] on usb-0000:00:1d.3-2/input0
 

---

### Post by falkTX on 2011-06-04
> **us3598 said:**
> There are only two usb devices plugged in, output of lsusb is



The Hori device would be the controller. DMESG output for game controller:

Of course this will not work, this is not a sixaxis...

Why did you though it would?

---

### Post by us3598 on 2011-06-04
I was under the impression that PS3 controllers were all sixaxis due to technology included in the controllers. All of the research I attempted led me to the Sixaxis community how-to; hence my confusion. I apologize for the waste of your time, and thank you greatly for your efforts. I have been out of the community for a very long time with the Army, and am still getting back into the swing of things.

---

### Post by falkTX on 2011-06-04
> **us3598 said:**
> I was under the impression that PS3 controllers were all sixaxis due to technology included in the controllers. All of the research I attempted led me to the Sixaxis community how-to; hence my confusion. I apologize for the waste of your time, and thank you greatly for your efforts. I have been out of the community for a very long time with the Army, and am still getting back into the swing of things.

my bad...

You can still make it work, just probably not over bluetooth I guess.

Does it work right away when you connect it over USB?

---

### Post by disturbedite on 2011-06-04
is there a cvs, svn, or git repository available to the public? i can't seem to find one.

---

### Post by falkTX on 2011-06-05
> **disturbedite said:**
> is there a cvs, svn, or git repository available to the public? i can't seem to find one.

it's the one provided by sourceforge:
qtsixa.git.sf.net

I think the command to clone is:
git clone git://qtsixa.git.sf.net/gitroot/qtsixa/qtsixa/

---

### Post by disturbedite on 2011-06-06
> **falkTX said:**
> it's the one provided by sourceforge:
qtsixa.git.sf.net

I think the command to clone is:
git clone git://qtsixa.git.sf.net/gitroot/qtsixa/qtsixa/

thanks.

---

### Post by jwebbdroid on 2011-06-07
Just spent like 4 hours trying to get this to do something. 

All I want is for the controller to move the mouse and click, etc. VERY BASIC

Connected with USB not Bluetooth.

From what I can tell it recognizes the the controller but does absolutely nothing.

A full step by step from install to end would be awesome since this thread is a mess of information. You even have permission to treat me like a complete idiot... as long as your info makes it work. ;)


Thanks,

---

### Post by kruykaze on 2011-06-07
> **jwebbdroid said:**
> Just spent like 4 hours trying to get this to do something. 

All I want is for the controller to move the mouse and click, etc. VERY BASIC

Connected with USB not Bluetooth.

From what I can tell it recognizes the the controller but does absolutely nothing.

A full step by step from install to end would be awesome since this thread is a mess of information. You even have permission to treat me like a complete idiot... as long as your info makes it work. ;)


Thanks,

Installation is covered in post 1 , after that i would run : sudo qtsixa in a terminal and go to setup device and choose "use as keyboard and mouse" and I would choose gnome as a profile.

---

### Post by falkTX on 2011-06-07
> **jwebbdroid said:**
> Connected with USB not Bluetooth.

A full step by step from install to end would be awesome since this thread is a mess of information. You even have permission to treat me like a complete idiot... as long as your info makes it work.

ok then...

You don't need anything in here to make it work on USB!
If you don't have bluetooth in your system, you can forget this thread at all...
(err, topic title is "HOW-TO: Connect Sixaxis to Ubuntu trough **bluetooth** mode")

For USB, just connect the device and press the PS button
(just need to press it once to activate it. This is "not needed" in bluetooth since you already press PS to connect it ;))

If it will work or not depends on Linux itself, *QtSixA does not do anything about USB drivers*.

I hope this is clear enough.

---

### Post by samguili on 2011-06-15
> **falkTX said:**
> ok then...

You don't need anything in here to make it work on USB!
If you don't have bluetooth in your system, you can forget this thread at all...
(err, topic title is "HOW-TO: Connect Sixaxis to Ubuntu trough **bluetooth** mode")

For USB, just connect the device and press the PS button
(just need to press it once to activate it. This is "not needed" in bluetooth since you already press PS to connect it ;))

If it will work or not depends on Linux itself, *QtSixA does not do anything about USB drivers*.

I hope this is clear enough.

Hello and sorry to bother but i have the very same goal as [kruykaze]("http://ubuntuforums.org/member.php?u=662686") and no matter what i try, i just cannot make it work. I can see and select my device in the main window but when i right clik to configure default profile and hidraw profile and give them "enable input" and gnome profile, nothing happens. Also, when i select "no Ied", the leds still keep blinking. I use ubuntu natty. Thanks for ur help !

---

### Post by kruykaze on 2011-06-15
> **samguili said:**
> Hello and sorry to bother but i have the very same goal as [kruykaze]("http://ubuntuforums.org/member.php?u=662686") and no matter what i try, i just cannot make it work. I can see and select my device in the main window but when i right clik to configure default profile and hidraw profile and give them "enable input" and gnome profile, nothing happens. Also, when i select "no Ied", the leds still keep blinking. I use ubuntu natty. Thanks for ur help !

If you connect the usb it will keep blinking untill it's fully charged. did you try to test using jstest ?

---

### Post by samguili on 2011-06-16
> **kruykaze said:**
> If you connect the usb it will keep blinking untill it's fully charged. did you try to test using jstest ?
i meant blinking quickly, like the pad do when it does not find the ps3, not when its charging. I did not use jstest, i will give it a try, thanks

---

### Post by samguili on 2011-06-16
ok, jstest show me that my pad is well recognize by ubuntu. Everything seem to work fine, so why all the settings in qtsixa doesn't have any effects ?

---

### Post by falkTX on 2011-06-16
> **samguili said:**
> ok, jstest show me that my pad is well recognize by ubuntu. Everything seem to work fine, so why all the settings in qtsixa doesn't have any effects ?

for usb, No.


I really need to finish the full-tutorial/doc thing.
Next week, it's a promise!

---

### Post by samguili on 2011-06-16
> **falkTX said:**
> for usb, No.


I really need to finish the full-tutorial/doc thing.
Next week, it's a promise!

oh well, ok...thanks for ur reply and for ur great job

---

### Post by kruykaze on 2011-06-16
> **samguili said:**
> oh well, ok...thanks for ur reply and for ur great job

You can use qjoypad to modify the inputs

---

### Post by gregory_38 on 2011-06-17
Hello,

I'm a linux dev of PCSX2. I want to support sixaxis in our applications. All joystick input code is handled by libsdl (1.3 but 1.2 is probably the same). I have an issue with axis 16 to 23 which are recognized as HAT and not axis by SDL.

My understanding: you defined a 1(ds3) :1 (linux) mapping axes inside the uinput_open function. However some axes have special meaning. Here an extract of linux/input.h
```

#define ABS_HAT0X        0x10
#define ABS_HAT0Y        0x11
#define ABS_HAT1X        0x12
#define ABS_HAT1Y        0x13
#define ABS_HAT2X        0x14
#define ABS_HAT2Y        0x15
#define ABS_HAT3X        0x16
#define ABS_HAT3Y        0x17

```SDL considers these axes as HAT and handle them differently.  One idea could be to add a hole when you register axes in the uinput_open function (16 -> 29 will become to 16+8 -> 29+8 ).  I do not know the impact in others place of qtsixa. What is your opinion?

Thanks,
Gregory

---

### Post by techmad on 2011-06-17
Hi Guys,

I'm having trouble connecting my controller (Sony PS3) to my computer (Ubuntu 11.04). It is detected and pairs fine when I have it connected via USB. When its disconnected and I press the PS button it shows in the sixad GUI and displays connection strength etc, but doesn't connect. When I tail the log file and try to connect the controller  this is what I see:

```
sixad-bin[1614]: sixad started, press the PS button now
sixad-bin[1614]: Server mode active, will start search now
sixad-bin[1614]: One event received
sixad-bin[1614]: unable to connect to sdp session
sixad-bin[1614]: Creating new device using the default driver...
sixad-bin[1614]: unable to connect to sdp session
sixad-bin[1614]: HID create error 112 (Host is down)
sixad-bin[1614]: One event proccessed
```I pressed the PS button multiple times during the above log events as the controller was turning off (lights stopped blinking). I've tried stopping/starting and forcing the connection but I get the same results. 

This is whats displayed when I run lsusb while the controllers connected:

```

Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 004: ID 054c:0268 Sony Corp. Batoh Device
Bus 005 Device 003: ID 0bc7:0006 X10 Wireless Technology, Inc. Wireless Transceiver (ACPI-compliant)
Bus 005 Device 002: ID 0a12:0001 Cambridge Silicon Radio, Ltd Bluetooth Dongle (HCI mode)
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 05af:0630 Jing-Mold Enterprise Co., Ltd 
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```Is there anything I can do to get it working? Any help is appreciated - thanks.

---

### Post by falkTX on 2011-06-17
> **gregory_38 said:**
> Hello,

I'm a linux dev of PCSX2. I want to support sixaxis in our applications. All joystick input code is handled by libsdl (1.3 but 1.2 is probably the same). I have an issue with axis 16 to 23 which are recognized as HAT and not axis by SDL.

My understanding: you defined a 1(ds3) :1 (linux) mapping axes inside the uinput_open function. However some axes have special meaning. Here an extract of linux/input.h
```

#define ABS_HAT0X        0x10
#define ABS_HAT0Y        0x11
#define ABS_HAT1X        0x12
#define ABS_HAT1Y        0x13
#define ABS_HAT2X        0x14
#define ABS_HAT2Y        0x15
#define ABS_HAT3X        0x16
#define ABS_HAT3Y        0x17

```SDL considers these axes as HAT and handle them differently.  One idea could be to add a hole when you register axes in the uinput_open function (16 -> 29 will become to 16+8 -> 29+8 ).  I do not know the impact in others place of qtsixa. What is your opinion?

Thanks,
Gregory

Well, I was kinda expecting something like this to happen...
I just use +1 for the axis number.

so your suggestion is to, on axis 16, skip the number 8 times?
like this:

```

axis-number <--> mapped-value
 1 <--> 1
 2 <--> 2
 ....
 16 <--> 16+8
 17 <--> 17+8
 ...

```
am I correct?

afaik, this has no side-effects whatsoever.

---

### Post by falkTX on 2011-06-17
> **techmad said:**
> Hi Guys,

I'm having trouble connecting my controller (Sony PS3) to my computer (Ubuntu 11.04). It is detected and pairs fine when I have it connected via USB. When its disconnected and I press the PS button it shows in the sixad GUI and displays connection strength etc, but doesn't connect.
(...)
Is there anything I can do to get it working? Any help is appreciated - thanks.

There's quite a few issues with the bluetooth on 11.04, but I think I found a way to make sixad work.

open a terminal and run this:
```
sixad -s
#ctrl+c to stop
sixad --stop
sixad -s
#ctrl+c to stop
sixad --stop
sixad -s
# now press the PS button, and leave this terminal open
```

This will force the bluetooth to activate and reload.

Natty seems a really bad release for me, not very production friendly. :(
(I had a lot of issues with it already, and I'm not referring to Unity...)

---

### Post by techmad on 2011-06-17
Thanks for your help, but no luck I'm afraid :(

I get a slightly different error this time though - instead of:

```
HID create error 112 (Host is down)
```
I get:

```
HID create error 114 (Operation already in progress)
```I'm going to keep at it so if I manage to get it working I'll let you know how, I'm stuck with Natty unfortunately so I've no other choice :(

---

### Post by gregory_38 on 2011-06-18
> **falkTX said:**
> Well, I was kinda expecting something like this to happen...
I just use +1 for the axis number.

so your suggestion is to, on axis 16, skip the number 8 times?

Yes exactly. I attach a small patch as example. I move them of 10 but 8 will be fine I think.
It work on my use case but others place in the code might need the sifth.

---

### Post by gregory_38 on 2011-06-18
Another topic, force feedback feature.

If I'm correct you only register the FF_RUMBLE feature. SDL checks all features but FF_RUMBLE.

An extract of the linux kernel doc: Documentation/input/ff.txt
> [FONT=monospace]
[/FONT]3.1 Querying device capabilities........

Note: In most cases you should use FF_PERIODIC instead of FF_RUMBLE. All      devices that support FF_RUMBLE support FF_PERIODIC (square, triangle,
      sine) and the other way around.
If I understand correctly the note, the driver must register both FF_PERIODIC and FF_RUMBLE (so application can properly query both). Then the difficult part respond to the new FF events.

---

### Post by benemorius on 2011-06-18
I was unable to get sixad working in natty until I added the following to /etc/bluetooth/main.conf
```
DisablePlugins = input
```

Otherwise, it seems that bluetoothd intercepts the connections before sixad can handle them, resulting in errors like "setup in progress." 

So on a fresh ubuntu natty install (assuming my sixaxis was already paired using sixpair) I can get a sixaxis working like this:
```

add-apt-repository ppa:falk-t-j/qtsixa
apt-get update
apt-get install -y sixad joystick
echo "DisablePlugins = input" >> /etc/bluetooth/main.conf
/etc/init.d/sixad start
while [ 1 ]; do jstest /dev/input/js0; sleep 1; done

```
At this point, I can push the ps button and it works, as verified by the #1 LED on the sixaxis and the output of jstest.

@falkTX
Thanks very much for sharing your work on the sixaxis. I'm now one very happy user.:D

---

### Post by falkTX on 2011-06-18
> **gregory_38 said:**
> Yes exactly. I attach a small patch as example. I move them of 10 but 8 will be fine I think.
It work on my use case but others place in the code might need the sifth.

Thanks.

I'll update the GIT page later when I have more free time.

As I said before, I'm about to release the complete docs of sixad/QtSixA, so this might be a good time to get 1.5.0 out, even with some small issues though (but still better than 1.2.1 anyway).

---

### Post by gregory_38 on 2011-06-18
> **falkTX said:**
> Thanks.

I'll update the GIT page later when I have more free time.

As I said before, I'm about to release the complete docs of sixad/QtSixA, so this might be a good time to get 1.5.0 out, even with some small issues though (but still better than 1.2.1 anyway).
Do not worry take your time.

By the way, here a more interesting patch for rumble. The patch register periodic effect (Square, triangle and sine). I test the sdl forcefeedback test and I was able to run a sine effect, which is a good new because it allows me to improve the forcefeedback support in PCSX2 :) I do not know if the effect play by the pad is correct but it is better than nothings

Enjoy,
Gregory

---

### Post by falkTX on 2011-06-18
> **gregory_38 said:**
> Do not worry take your time.

By the way, here a more interesting patch for rumble. The patch register periodic effect (Square, triangle and sine). I test the sdl forcefeedback test and I was able to run a sine effect, which is a good new because it allows me to improve the forcefeedback support in PCSX2 :) I do not know if the effect play by the pad is correct but it is better than nothings

Enjoy,
Gregory

Thanks again.

The rumble feature in linux is a complex thing, and can lead to several issues.
For example, if an application is writing FF effects and crashes, the FF effect will not be closed properly, leaving the joystick/device unusable.
I got an even worse scenario where the app did not register the FF correctly and cause a system lockup...
We need to be very careful when coding FF stuff.

I'll look into your patch, but sadly my PC is no good for running PCSX2 (crappy intel GPU).
I did my tests with pSX, evtest and the n64 emulator (don't remember the name now...).

Is there "soft" game a I can try with PCSX2?
(a game with very low graphics, even for PS2?)

---

### Post by falkTX on 2011-06-18
> **benemorius said:**
> I was unable to get sixad working in natty until I added the following to /etc/bluetooth/main.conf
```
DisablePlugins = input
```

Otherwise, it seems that bluetoothd intercepts the connections before sixad can handle them, resulting in errors like "setup in progress." 

So on a fresh ubuntu natty install (assuming my sixaxis was already paired using sixpair) I can get a sixaxis working like this:
```

add-apt-repository ppa:falk-t-j/qtsixa
apt-get update
apt-get install -y sixad joystick
echo "DisablePlugins = input" >> /etc/bluetooth/main.conf
/etc/init.d/sixad start
while [ 1 ]; do jstest /dev/input/js0; sleep 1; done

```
At this point, I can push the ps button and it works, as verified by the #1 LED on the sixaxis and the output of jstest.

@falkTX
Thanks very much for sharing your work on the sixaxis. I'm now one very happy user.:D

I'll surely try this, thanks!

But won't this ruin the connection for normal devices..?

---

### Post by techmad on 2011-06-18
Thanks for your help benemorius, but still no joy. My device is paired:

```
Current Bluetooth master: ae:2d:22:00:ff:00
Setting master bd_addr to ae:2d:22:00:ff:00
```I've also added the line to my main.conf file, when I start sixad I get the following message:

```
Can't read version info hci0: Connection timed out (110)
sixad-bin[18267]: sixad started, press the PS button now
```Then nothing happens, the controller doesnt connect :(

---

### Post by benemorius on 2011-06-18
> **falkTX said:**
> I'll surely try this, thanks!

But won't this ruin the connection for normal devices..?

Yes I expect it will break other input devices. The only other bluetooth device I have handy is an rfcomm device, which still works of course. I have a keyboard somewhere around here I could try, but I assume it won't be picked up by bluetoothd now.

Is your sixaxis actually working with natty or no? I see only limited talk of it being broken in natty, but I can't see how anyone could have it working without going through what I went through unless there's a degree of random timing involved.

---

### Post by benemorius on 2011-06-18
> **techmad said:**
> Thanks for your help benemorius, but still no joy. My device is paired:

```
Current Bluetooth master: ae:2d:22:00:ff:00
Setting master bd_addr to ae:2d:22:00:ff:00
```I've also added the line to my main.conf file, when I start sixad I get the following message:

```
Can't read version info hci0: Connection timed out (110)
sixad-bin[18267]: sixad started, press the PS button now
```Then nothing happens, the controller doesnt connect :(

Is there anything else in syslog from bluetoothd or networkmanager? Was there anything before editing main.conf? Do you have DEBUG=1 in /etc/default/sixad?

> **techmad said:**
> 

```
HID create error 114 (Operation already in progress)
```
Where did this output come from? It sounds similar to what I was getting in syslog from bluetoothd when it was interfering with things. In any case, it would seem to imply some kind of interference at least.

---

### Post by falkTX on 2011-06-18
Let me try to clarify the situation in Natty (Ubuntu 11.04, latest release).

This release has several issues that prevents 'sixad' (the QtSixA background driver) from working correctly.


**Issue #1** - Bluetooth not activated on boot.
The bluetooth driver and interface will not be enabled during boot, causing the auto-connect udev rule to fail (no more "just press PS anytime-to connect").
You can force bluetooth activation by running "sixad --stop" (bluez required)

**Issue #2** - hcid does not work
This is a kernel issue present at least on 2.6.37 and 2.6.38, that makes 'hcid' completely useless.
This little app is used by sixad for blocking the normal bluetooth (bluetoothd) events.
The "DisablePlugins = input" may do the trick here, but I haven't tested it yet.
Other solution is to _not_ use 2.6.38 (default on Natty), but an older kernel.
This one works -> [http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.36.4-natty/](http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.36.4-natty/)

I made some changes recently that allow sixad to work without bluez installed, but it doesn't work on Natty since we need bluez to activate bluetooth...

so, resuming, if you really want to make sure this always works on Natty (bluetooth only, usb always works!), do this:
1 - install an older kernel, like this one - [http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.36.4-natty/](http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.36.4-natty/) (Make sure you boot from this kernel!)
2 - remove "bluetooth" and "bluez" packages completely
3 - run 'sixad --boot-yes' to activate sixad on boot.
(hm... reboot)

These 3 steps will get you 100% chance of sixad working, as long as the sixaxis is paired and it's not a fake, like "Gasia Gamepad".

---

### Post by techmad on 2011-06-18
Pardon my ignorance, but to install this kernel do I just install the two available deb files (headers and image)? Thanks!

---

### Post by falkTX on 2011-06-18
> **techmad said:**
> Pardon my ignorance, but to install this kernel do I just install the two available deb files (headers and image)? Thanks!

You can just install the *-image* if you don't have 3rd party drivers (ATI, NVIDIA, non-free Wireless or VirtualBox).
If you need them ^, install all that end with *_all.deb and i386 if you're 32bit or amd64 for 64bit.
You should install the headers first though.
After install, reboot from that kernel.

If you don't see the select-kernel-to-boot menu after restart, try this:
[http://kxstudio.sourceforge.net/mediawiki/index.php/Help:ShowGrub](http://kxstudio.sourceforge.net/mediawiki/index.php/Help:ShowGrub)

---

### Post by gregory_38 on 2011-06-19
> **falkTX said:**
> Thanks again.
I'll look into your patch, but sadly my PC is no good for running PCSX2 (crappy intel GPU).
I did my tests with pSX, evtest and the n64 emulator (don't remember the name now...).

Is there "soft" game a I can try with PCSX2?
(a game with very low graphics, even for PS2?)

Actually, forcefeedback in PCSX2 is WIP (aka nothing work yet :p, it only a matter to have enough free time) I bought the ds3 one week ago. However it would be interfaced with SDL1.3 like potentially many games. I personally compile & test the SDL example. It is easy to understand
File: SDL-1.3.0-5387/test/testhaptic.c

Note: PCSX2 have a pure software rendering plugin (libGSdx) if you have a not too slow cpu. For the moment I will do my test with colin mcrae rally 3 in the menu configuration of the game, you can configure the level of FF.

edit: 
I fix PCSX2 trunk. Forcefeedback begin to work. Thanks very much for qtsixa :)

---

### Post by falkTX on 2011-06-19
> **gregory_38 said:**
> Actually, forcefeedback in PCSX2 is WIP (aka nothing work yet :p, it only a matter to have enough free time) I bought the ds3 one week ago. However it would be interfaced with SDL1.3 like potentially many games. I personally compile & test the SDL example. It is easy to understand
File: SDL-1.3.0-5387/test/testhaptic.c

Note: PCSX2 have a pure software rendering plugin (libGSdx) if you have a not too slow cpu. For the moment I will do my test with colin mcrae rally 3 in the menu configuration of the game, you can configure the level of FF.

edit: 
I fix PCSX2 trunk. Forcefeedback begin to work. Thanks very much for qtsixa :)

I don't like SDL much (mainly the Audio on linux has several issues), but I've seen other projects using sdl for joystick and it seems to work...
What are the plans for PCSX2 regarding sdl - wait for 1.3 release, pre-compile a static version or what?
(It seems like v1.3 can take some time before release)

Anyway, I pushed your patches to the latest Git, get it with:
```
git clone git://qtsixa.git.sourceforge.net/gitroot/qtsixa/qtsixa
```

I haven't tested the new changes though, but I'll do it very soon.

---

### Post by gregory_38 on 2011-06-20
> **falkTX said:**
> I don't like SDL much (mainly the Audio on linux has several issues), but I've seen other projects using sdl for joystick and it seems to work...
What are the plans for PCSX2 regarding sdl - wait for 1.3 release, pre-compile a static version or what?
(It seems like v1.3 can take some time before release)

Anyway, I pushed your patches to the latest Git, get it with:
```
git clone git://qtsixa.git.sourceforge.net/gitroot/qtsixa/qtsixa
```I haven't tested the new changes though, but I'll do it very soon.

Thanks, yes it would love some testing.

Well we use SDL for joystick, and one graphic plugin uses it for the graphic rendering. For us, SDL is cross-platform MSW/linux so it is handy. Anyway, SDL was duplicated in your repository (snapshot actually). So ours users can compile it and link it statically, it only a matter of a cmake options. I only hope they did not need years to release the next version.

---

### Post by kruykaze on 2011-06-20
Sixad is working just fine for me on natty , I use a script to connect my sixaxis :

hcitool  dc 00:21:4F:05:3F:98 <-- you need to change this
sudo killall sixad-bin
sudo killall sixad
sudo sixad -s


once in a while bluetooth picks up the sixaxis before sixad but running the script again fixes it :)

---

### Post by techmad on 2011-06-20
> **benemorius said:**
> Is there anything else in syslog from bluetoothd or networkmanager? Was there anything before editing main.conf? Do you have DEBUG=1 in /etc/default/sixad?

I'll enable debugging later on today and watch the logs when trying to connect the controller and let you know if anything shows up there.

[B]@ kruykaze

[/B]I'll give that a go later aswell and let you know how I get on - thanks[B].
[/B]

---

### Post by curryking1 on 2011-06-20
I'm trying to use my Dualshock 3 controller through USB using this program...

I can't get anything to work though. I can't configure controls in any of the Ubuntu programs such as SNES9x or Mupen64. I just installed using the method in the OP and followed it's instructions.

I am using 11.04 Ubuntu though, and I don't understand what I'm supposed to do for the 11.04 specific instructions.

I don't need to use the bluetooth capabilities (my laptop has bluetooth though), because I am comfortable connecting my Dualshock 3 via USB.

Is there a way I can just connect the controller via USB and use emulators that way using this program on 11.04?

---

### Post by falkTX on 2011-06-20
> **curryking1 said:**
> I'm trying to use my Dualshock 3 controller through USB using this program...

I can't get anything to work though. I can't configure controls in any of the Ubuntu programs such as SNES9x or Mupen64. I just installed using the method in the OP and followed it's instructions.

I am using 11.04 Ubuntu though, and I don't understand what I'm supposed to do for the 11.04 specific instructions.

I don't need to use the bluetooth capabilities (my laptop has bluetooth though), because I am comfortable connecting my Dualshock 3 via USB.

Is there a way I can just connect the controller via USB and use emulators that way using this program on 11.04?

Yes! (oh man, I've answered this question a lot of times now...)

Just connect the sixaxis and press the PS button (one time is enough).
The sixaxis will work as a regular joystick, even if the leds keep blinking.

---

### Post by curryking1 on 2011-06-20
Thanks for the quick reply.

I got it to work. I just had to use the 'Root Action --> Force Connection' option in the main menu of the program. It looks like it's working well now via USB, thanks for the help.

Is it possible to get a little diagnostic screen to see whether or not the controller is sending input and the PC is receiving it? Just like a little window which shows the user which buttons are being pressed or which axes are being used. I think that would be helpful for users to see whether or not their controller is connected or not very quickly.

Thanks for the program :)

---

### Post by falkTX on 2011-06-20
> **curryking1 said:**
> Thanks for the quick reply.

I got it to work. I just had to use the 'Root Action --> Force Connection' option in the main menu of the program. It looks like it's working well now via USB, thanks for the help.

:lolflag:
QtSixA only manages bluetooth stuff. QtSixA hasn't done anything at all to help your sixaxis work in USB mode...
 
> **curryking1 said:**
> 
Is it possible to get a little diagnostic screen to see whether or not the controller is sending input and the PC is receiving it? Just like a little window which shows the user which buttons are being pressed or which axes are being used. I think that would be helpful for users to see whether or not their controller is connected or not very quickly.

Thanks for the program :)

Use 'jstest', like this:
```
jstest /dev/input/js0
```

---

### Post by techmad on 2011-06-22
> **kruykaze said:**
> Sixad is working just fine for me on natty , I use a script to connect my sixaxis :

hcitool  dc 00:21:4F:05:3F:98 <-- you need to change this
sudo killall sixad-bin
sudo killall sixad
sudo sixad -s


once in a while bluetooth picks up the sixaxis before sixad but running the script again fixes it :)

No luck I'm afraid, got no output at all when I tried to connect. I think I'm going to go back to 10.1 and hopefully get alsa working (thats why I went to 11 in the first place).

Thanks for all the help anyway :)

---

### Post by falkTX on 2011-07-01
Good news!

I (may had) found a way to make this work on Natty, issues free.
The new method does not require hcid anymore; instead sixad will temporarily rename 'bluetoothd', so that it doesn't run and blocks sixaxis events.

From this point forward, there's no more udev rule, so you need to manually start sixad to make it work.

Put it simple, install the latest updates and run:
```
sixad --stop #Natty only
sixad --start
# Press the PS button on the sixaxis
```
If you need regular bluetooth, run this after connecting the sixaxis:
```
sixad --restore
```

Let me know of any issues!

In any case, I started the new manual, please take a look:
[http://qtsixa.git.sourceforge.net/git/gitweb.cgi?p=qtsixa/qtsixa;a=blob_plain;f=manual.pdf;hb=master](http://qtsixa.git.sourceforge.net/git/gitweb.cgi?p=qtsixa/qtsixa;a=blob_plain;f=manual.pdf;hb=master)

The 'known issues' section is missing, on purpose.
I want to know what issues users find *after* this latest update.

---

### Post by techmad on 2011-07-01
No change here Im afraid, same thing as before:

```
:~$ sixad --stop
:~$ sixad --start
sixad-bin[4349]: sixad started, press the PS button now
sixad-bin[4349]: Server mode active, will start search now
sixad-bin[4349]: One event received
sixad-bin[4349]: unable to connect to sdp session
sixad-bin[4349]: Creating new device using the default driver...
sixad-bin[4349]: unable to connect to sdp session
sixad-bin[4349]: HID create error 110 (Connection timed out)
sixad-bin[4349]: One event proccessed
sixad-bin[4349]: One event received
```These are the exact steps I took on a fresh install of Natty:

[LIST=1]
[*]Installed qtsixa
[*]Rebooted (just incase)
[*]Started qtsixa, added myself to the sixad group when prompted, then and logged off and on
[*]Started qtsixa, connected the sixaxis via USB and paired it
[*]Disconnected the sixaxis and tried to connect. I now see this which I wasnt seeing before:

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=196504&stc=1&d=1309551181[/IMG]
[*]By the time I grant access the sixaxis stops trying to connect (lights stop flashing)
[*]I then closed qtsixa, opened a terminal and stopped sixad as instructed (sixad --stop)
[*]Started sixad (sixad --start) and pressed the PS button.
[/LIST]
If you need any more info let me know!

---

### Post by falkTX on 2011-07-01
I have the exact this same error:
> **techmad said:**
> ```
:~$ sixad --stop
:~$ sixad --start
sixad-bin[4349]: sixad started, press the PS button now
sixad-bin[4349]: Server mode active, will start search now
sixad-bin[4349]: One event received
sixad-bin[4349]: unable to connect to sdp session
sixad-bin[4349]: Creating new device using the default driver...
sixad-bin[4349]: unable to connect to sdp session
sixad-bin[4349]: HID create error 110 (Connection timed out)
sixad-bin[4349]: One event proccessed
sixad-bin[4349]: One event received
```

But when using a Gasia gamepad, not a real sixaxis...

Please connect your joystick via USB, and post here the output of 'lsusb'.
Thanks

---

### Post by techmad on 2011-07-01
Here you go:

```
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 003: ID 0a12:0001 Cambridge Silicon Radio, Ltd Bluetooth Dongle (HCI mode)
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 003: ID 054c:0268 Sony Corp. Batoh Device
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 004: ID 0b97:7762 O2 Micro, Inc. Oz776 SmartCard Reader
Bus 002 Device 003: ID 0b97:7761 O2 Micro, Inc. Oz776 1.1 Hub
Bus 002 Device 002: ID 413c:a005 Dell Computer Corp. Internal 2.0 Hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
```

---

### Post by falkTX on 2011-07-01
> **techmad said:**
> Here you go:

```
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 003: ID 0a12:0001 Cambridge Silicon Radio, Ltd Bluetooth Dongle (HCI mode)
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 003: ID 054c:0268 Sony Corp. Batoh Device
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 004: ID 0b97:7762 O2 Micro, Inc. Oz776 SmartCard Reader
Bus 002 Device 003: ID 0b97:7761 O2 Micro, Inc. Oz776 1.1 Hub
Bus 002 Device 002: ID 413c:a005 Dell Computer Corp. Internal 2.0 Hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
```

Hm... seems good (you even have the same bluetooth adapter as I do :p)

Please post the output of 'dmesg | tail', just after connecting your joystick.
Thanks

---

### Post by techmad on 2011-07-01
```
[ 3783.698033] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[ 3793.984024] wlan0: no IPv6 routers present
[ 4847.576190] usb 3-2: USB disconnect, address 3
[ 4873.296149] usb 3-2: new full speed USB device using uhci_hcd and address 4
[ 4873.470601] input: Gasia Co.,Ltd PS(R) Gamepad as /devices/pci0000:00/0000:00:1d.1/usb3/3-2/3-2:1.0/input/input12
[ 4873.470993] sony 0003:054C:0268.0003: input,hiddev0,hidraw0: USB HID v1.11 Joystick [Gasia Co.,Ltd PS(R) Gamepad] on usb-0000:00:1d.1-2/input0
[ 4876.096159] usb 3-2: USB disconnect, address 4
[ 4925.940042] usb 3-2: new full speed USB device using uhci_hcd and address 5
[ 4926.110574] input: Gasia Co.,Ltd PS(R) Gamepad as /devices/pci0000:00/0000:00:1d.1/usb3/3-2/3-2:1.0/input/input13
[ 4926.110968] sony 0003:054C:0268.0004: input,hiddev0,hidraw0: USB HID v1.11 Joystick [Gasia Co.,Ltd PS(R) Gamepad] on usb-0000:00:1d.1-2/input0

```

Your right!!! Sorry if I had of known it was a Gasia gamepad I wouldnt have  been bugging you :( I bought this supposed 'official' Sony PS3 controller on ebay, going to get onto him about it. Thanks!

---

### Post by falkTX on 2011-07-01
> **techmad said:**
> ```
[ 3783.698033] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[ 3793.984024] wlan0: no IPv6 routers present
[ 4847.576190] usb 3-2: USB disconnect, address 3
[ 4873.296149] usb 3-2: new full speed USB device using uhci_hcd and address 4
[ 4873.470601] input: Gasia Co.,Ltd PS(R) Gamepad as /devices/pci0000:00/0000:00:1d.1/usb3/3-2/3-2:1.0/input/input12
[ 4873.470993] sony 0003:054C:0268.0003: input,hiddev0,hidraw0: USB HID v1.11 Joystick [Gasia Co.,Ltd PS(R) Gamepad] on usb-0000:00:1d.1-2/input0
[ 4876.096159] usb 3-2: USB disconnect, address 4
[ 4925.940042] usb 3-2: new full speed USB device using uhci_hcd and address 5
[ 4926.110574] input: Gasia Co.,Ltd PS(R) Gamepad as /devices/pci0000:00/0000:00:1d.1/usb3/3-2/3-2:1.0/input/input13
[ 4926.110968] sony 0003:054C:0268.0004: input,hiddev0,hidraw0: USB HID v1.11 Joystick [Gasia Co.,Ltd PS(R) Gamepad] on usb-0000:00:1d.1-2/input0

```

Your right!!! Sorry if I had of known it was a Gasia gamepad I wouldnt have  been bugging you :( I bought this supposed 'official' Sony PS3 controller on ebay, going to get onto him about it. Thanks!

no problem at all.

I want to support this device too, but it stupidly doesn't follow the standards...
MotionJoy in Windows is able to connect it (but with several issues), so I know it's possible.

Those Gasia guys did a pretty good job copying the sixaxis... =D>

---

### Post by techmad on 2011-07-04
It's virtually indistinguishable from an official controller, although it seems a little heavier. I'm getting an official one later so I'll give it a go and let you know how I get on.

---

### Post by falkTX on 2011-07-04
> **techmad said:**
> It's virtually indistinguishable from an official controller, although it seems a little heavier. I'm getting an official one later so I'll give it a go and let you know how I get on.

If you got a rumble sixaxis (dualshock3) they will weight basically the same.
The quality is not the same though, and the Gasia one doesn't have the small 'reset' button.

The official ones work with no problem at all. I have a sixaxis (no rumble) and one with rumble, both working fine.
I also have a NPlay sixaxis-like joystick (needs own USB radio thing), which also works.
Oh, plus a Keypad and a BD Remote, they all work.

I guess the main difference with this Gasia gamepad is that it doesn't work... :(

---

### Post by ophanim on 2011-07-05
I'm having a problem syncing PS3 controller.

I've got qtsixa installed on Mint 10 with the 2.6.35-22-generic-pae kernel and I'm using a rocketfish RF-MRBTAD bluetooth adapter.  I can sync my phone up with my computer so I assume the setup works.  I'm also using a real PS3 controller that came right out of the box with the PS3.

However, when I try to sync the PS3 controller up I get a prompt to "Grant access".  No matter how many times I press "Grant" (or when I was trying to use blueman, "allow") it wont sync up.  If I press grant, the same prompt will pop up a few seconds later as if the controller was asking for permission again.  This will continue until the controller gives up.

I've tried forcing the connection through qtsixa, I've tried manually syncing in qtsixa, I've tried different bluetooth managers, etc.  Am I missing something?  

Please help!  This is a rather frustrating little problem. :(

---

### Post by falkTX on 2011-07-05
> **ophanim said:**
> I'm having a problem syncing PS3 controller.

I've got qtsixa installed on Mint 10 with the 2.6.35-22-generic-pae kernel and I'm using a rocketfish RF-MRBTAD bluetooth adapter.  I can sync my phone up with my computer so I assume the setup works.  I'm also using a real PS3 controller that came right out of the box with the PS3.

However, when I try to sync the PS3 controller up I get a prompt to "Grant access".  No matter how many times I press "Grant" (or when I was trying to use blueman, "allow") it wont sync up.  If I press grant, the same prompt will pop up a few seconds later as if the controller was asking for permission again.  This will continue until the controller gives up.

I've tried forcing the connection through qtsixa, I've tried manually syncing in qtsixa, I've tried different bluetooth managers, etc.  Am I missing something?  

Please help!  This is a rather frustrating little problem. :(

hm... did you missed the news about the new "release" ?

In any case, please read the QtSixA manual:
[http://qtsixa.git.sourceforge.net/git/gitweb.cgi?p=qtsixa/qtsixa;a=blob_plain;f=manual.pdf;hb=master](http://qtsixa.git.sourceforge.net/git/gitweb.cgi?p=qtsixa/qtsixa;a=blob_plain;f=manual.pdf;hb=master)


To put it simply, connecting a fresh new Sixaxis to the PC requires:
1 - Get a USB cable, and connect the Sixaxis via USB. Make sure the bluetooth adapter is on, and run:
```
sudo sixpair
```

2 - Remove the Sixaxis from USB, then run this:
```
sixad --stop
sixad --start
```
Now press the PS button on the sixaxis.

If you need regular bluetooth, run this after connecting the sixaxis:
```
sixad --restore
```

Simple enough I think ;)

---

### Post by techmad on 2011-07-06
> **falkTX said:**
> no problem at all.

I want to support this device too, but it stupidly doesn't follow the standards...
MotionJoy in Windows is able to connect it (but with several issues), so I know it's possible.

Those Gasia guys did a pretty good job copying the sixaxis... =D>

I got an official controller and all is well now, I just have to stop and start sixad as you said to get it to work, thanks for your help!

---

### Post by redesigner on 2011-07-06
Hello, I seem to be having a bit of a problem with QTSixA. I don't have bluetooth adapters, but I am connecting my SixAxis through the usb cable. QTSixA recognizes it, but nothing recognizes my input whether it be keyboard and mouse or joystick enabled games. I'm sorry for being so vague, if anyone has any idea on how to get the input working properly, that would be great! I've been trying to get it working for hours and hours.

---

### Post by falkTX on 2011-07-06
> **redesigner said:**
> Hello, I seem to be having a bit of a problem with QTSixA. I don't have bluetooth adapters, but I am connecting my SixAxis through the usb cable. QTSixA recognizes it, but nothing recognizes my input whether it be keyboard and mouse or joystick enabled games. I'm sorry for being so vague, if anyone has any idea on how to get the input working properly, that would be great! I've been trying to get it working for hours and hours.

Have you read the manual?

Anyway, let me explain.
QtSixA (err, sixad), doesn't handle USB devices by default.
The driver used for USB will be the system generic one.

If you want QtSixA features on USB, use 'sixad-raw'.
After you configured the stuff properly in the GUI as needed, connect your sixaxis via USB.
Now run:
```
dmesg | tail
```
You'll see something like this:
```
[16484.325306] input: Sony PLAYSTATION(R)3 Controller as /devices/pci0000:00/0000:00:1a.1/usb4/4-1/4-1:1.0/input/input16
[16484.325560] sony 0003:054C:0268.0004: input,hiddev96,hidraw1: USB HID v1.11 Joystick [Sony PLAYSTATION(R)3 Controller] on usb-0000:00:1a.1-1/input0
[16484.326161] sony 0003:054C:0268.0004: can't set operational mode
[16484.345011] sony: probe of 0003:054C:0268.0004 failed with error -71
[16484.580086] usb 4-1: USB disconnect, address 5
[16484.820049] usb 4-1: new full speed USB device using uhci_hcd and address 6
[16485.023316] usb 4-1: configuration #1 chosen from 1 choice
[16485.109286] input: Sony PLAYSTATION(R)3 Controller as /devices/pci0000:00/0000:00:1a.1/usb4/4-1/4-1:1.0/input/input17
[16485.109480] sony 0003:054C:0268.0005: **input,hiddev96,hidraw1**: USB HID v1.11 Joystick [Sony PLAYSTATION(R)3 Controller] on usb-0000:00:1a.1-1/input0

```
Notice the values I put on bold, it tells you which hidraw device the sixaxis is using.

Now using that, simply run:
```
sudo sixad-raw /dev/hidrawX
```
And replace 'X' by the appropriate number, as you found before.


PS: If you got an uinput error with sixad-raw, run 'sudo modprobe uinput' and try again.

---

### Post by redesigner on 2011-07-06
> **falkTX said:**
> Have you read the manual?

Anyway, let me explain.
QtSixA (err, sixad), doesn't handle USB devices by default.
The driver used for USB will be the system generic one.

If you want QtSixA features on USB, use 'sixad-raw'.
After you configured the stuff properly in the GUI as needed, connect your sixaxis via USB.
Now run:
```
dmesg | tail
```You'll see something like this:
```
[16484.325306] input: Sony PLAYSTATION(R)3 Controller as /devices/pci0000:00/0000:00:1a.1/usb4/4-1/4-1:1.0/input/input16
[16484.325560] sony 0003:054C:0268.0004: input,hiddev96,hidraw1: USB HID v1.11 Joystick [Sony PLAYSTATION(R)3 Controller] on usb-0000:00:1a.1-1/input0
[16484.326161] sony 0003:054C:0268.0004: can't set operational mode
[16484.345011] sony: probe of 0003:054C:0268.0004 failed with error -71
[16484.580086] usb 4-1: USB disconnect, address 5
[16484.820049] usb 4-1: new full speed USB device using uhci_hcd and address 6
[16485.023316] usb 4-1: configuration #1 chosen from 1 choice
[16485.109286] input: Sony PLAYSTATION(R)3 Controller as /devices/pci0000:00/0000:00:1a.1/usb4/4-1/4-1:1.0/input/input17
[16485.109480] sony 0003:054C:0268.0005: **input,hiddev96,hidraw1**: USB HID v1.11 Joystick [Sony PLAYSTATION(R)3 Controller] on usb-0000:00:1a.1-1/input0

```Notice the values I put on bold, it tells you which hidraw device the sixaxis is using.

Now using that, simply run:
```
sudo sixad-raw /dev/hidrawX
```And replace 'X' by the appropriate number, as you found before.


PS: If you got an uinput error with sixad-raw, run 'sudo modprobe uinput' and try again.

I've tried doing the steps for the manual, but the Gui remains faded out and I cannot change the advanced settings for hidraw. When I run dmesg it gives me this output: ```
[21775.917416] input: Sony PLAYSTATION(R)3 Controller as /devices/pci0000:00/0000:00:1d.1/usb7/7-1/7-1:1.0/input/input32
[21775.917602] sony 0003:054C:0268.0017: input,hiddev0,hidraw0: USB HID v1.11 Joystick [Sony PLAYSTATION(R)3 Controller] on usb-0000:00:1d.1-1/input0
[22040.672076] usb 7-1: USB disconnect, address 24
[22112.592052] usb 7-1: new full speed USB device using uhci_hcd and address 25
[22112.955191] input: Sony PLAYSTATION(R)3 Controller as /devices/pci0000:00/0000:00:1d.1/usb7/7-1/7-1:1.0/input/input33
[22112.955378] sony 0003:054C:0268.0018: input,hiddev0,hidraw0: USB HID v1.11 Joystick [Sony PLAYSTATION(R)3 Controller] on usb-0000:00:1d.1-1/input0
[22116.312058] usb 7-1: USB disconnect, address 25
[22118.040036] usb 7-1: new full speed USB device using uhci_hcd and address 26
[22118.413179] input: Sony PLAYSTATION(R)3 Controller as /devices/pci0000:00/0000:00:1d.1/usb7/7-1/7-1:1.0/input/input34
[22118.413367] sony 0003:054C:0268.0019: input,hiddev0,hidraw0: USB HID v1.11 Joystick [Sony PLAYSTATION(R)3 Controller] on usb-0000:00:1d.1-1/input0

```
When I run sixad-raw /dev/hidraw0 It outputs nothing until I unplug the controller.

---

### Post by falkTX on 2011-07-07
> **redesigner said:**
> I've tried doing the steps for the manual, but the Gui remains faded out and I cannot change the advanced settings for hidraw. When I run dmesg it gives me this output: ```
[21775.917416] input: Sony PLAYSTATION(R)3 Controller as /devices/pci0000:00/0000:00:1d.1/usb7/7-1/7-1:1.0/input/input32
[21775.917602] sony 0003:054C:0268.0017: input,hiddev0,hidraw0: USB HID v1.11 Joystick [Sony PLAYSTATION(R)3 Controller] on usb-0000:00:1d.1-1/input0
[22040.672076] usb 7-1: USB disconnect, address 24
[22112.592052] usb 7-1: new full speed USB device using uhci_hcd and address 25
[22112.955191] input: Sony PLAYSTATION(R)3 Controller as /devices/pci0000:00/0000:00:1d.1/usb7/7-1/7-1:1.0/input/input33
[22112.955378] sony 0003:054C:0268.0018: input,hiddev0,hidraw0: USB HID v1.11 Joystick [Sony PLAYSTATION(R)3 Controller] on usb-0000:00:1d.1-1/input0
[22116.312058] usb 7-1: USB disconnect, address 25
[22118.040036] usb 7-1: new full speed USB device using uhci_hcd and address 26
[22118.413179] input: Sony PLAYSTATION(R)3 Controller as /devices/pci0000:00/0000:00:1d.1/usb7/7-1/7-1:1.0/input/input34
[22118.413367] sony 0003:054C:0268.0019: input,hiddev0,hidraw0: USB HID v1.11 Joystick [Sony PLAYSTATION(R)3 Controller] on usb-0000:00:1d.1-1/input0

```
When I run sixad-raw /dev/hidraw0 It outputs nothing until I unplug the controller.

If there's a problem with the GUI, run it on a terminal ('qtsixa'), make the issue appear and post the output of the terminal here.

sixad-raw will not print anything until an error occurs. If nothing gets printed, then it's working fine.
Note: On USB you have to press the PS button at least once, even for sixad-raw

---

### Post by redesigner on 2011-07-07
> **falkTX said:**
> If there's a problem with the GUI, run it on a terminal ('qtsixa'), make the issue appear and post the output of the terminal here.

sixad-raw will not print anything until an error occurs. If nothing gets printed, then it's working fine.
Note: On USB you have to press the PS button at least once, even for sixad-raw
In that case, everything seems to be working properly, except the actual ouput of the controller. The output of the terminal is normal, although I have to run it as root because one of the profile permissions isn't working properly.  ```
$ sudo qtsixa
Qt version: 4.7.2
PyQt version: 4.8.3
QtSixA version: 1.5.0
Will use 'gksu' for root actions

```I was thinking it was possibly a conflicting driver or package, so I have uninstalled all of my joystick packages aside from QtSixA.
Attached are some screenshots of QtSixA if that will help at all.

Thanks for all of your help so far!

---

### Post by falkTX on 2011-07-07
> **redesigner said:**
> In that case, everything seems to be working properly, except the actual ouput of the controller. The output of the terminal is normal, although I have to run it as root because one of the profile permissions isn't working properly.  ```
$ sudo qtsixa
Qt version: 4.7.2
PyQt version: 4.8.3
QtSixA version: 1.5.0
Will use 'gksu' for root actions

```I was thinking it was possibly a conflicting driver or package, so I have uninstalled all of my joystick packages aside from QtSixA.
Attached are some screenshots of QtSixA if that will help at all.

Thanks for all of your help so far!

Note that sixad-raw will create a **new** joystick and still keep the old one (the original sixaxis USB).

hm... please make sure your joystick works in USB first (ie, test with 'jstest /dev/input/js0' or similar).

---

### Post by inferno91 on 2011-07-17
I'm at my wit's end with getting my Sixaxis (actually Dualshock 3) to work via bluetooth in (K)Ubuntu. Previously, I could get it to work by "disabling bluetooth" in qtsixa, pressing the PS button on the sixaxis to connect, and finally, re-enabling bluetooth in qtsixa so my other bluetooth devices can work again. I understand what "disabling bluetooth" in qtsixa does - it kills the bluez bluetooth stack so sixad - a patched bluetooth stack which allows the sixaxis to connect can load. But now it seems this no longer works. Bluez's bluetoothd in Ubuntu 11.04 seems to be aggressively relaunching whenever a bluetooth device (including the sixaxis) tries to connect, thus blocking sixad and therefore my sixaxis won't connect. Is there ANY workaround for this whatsoever (other than connecting my sixaxis via USB which is not an option?)

Using qtsixa 1.4.97+git20110701-0~natty1 from falktx's ppa
Kubuntu 11.04 "natty" fully updated

---

### Post by falkTX on 2011-07-17
> **inferno91 said:**
> I'm at my wit's end with getting my Sixaxis (actually Dualshock 3) to work via bluetooth in (K)Ubuntu. Previously, I could get it to work by "disabling bluetooth" in qtsixa, pressing the PS button on the sixaxis to connect, and finally, re-enabling bluetooth in qtsixa so my other bluetooth devices can work again. I understand what "disabling bluetooth" in qtsixa does - it kills the bluez bluetooth stack so sixad - a patched bluetooth stack which allows the sixaxis to connect can load. But now it seems this no longer works. Bluez's bluetoothd in Ubuntu 11.04 seems to be aggressively relaunching whenever a bluetooth device (including the sixaxis) tries to connect, thus blocking sixad and therefore my sixaxis won't connect. Is there ANY workaround for this whatsoever (other than connecting my sixaxis via USB which is not an option?)

Using qtsixa 1.4.97+git20110701-0~natty1 from falktx's ppa
Kubuntu 11.04 "natty" fully updated

The usual way to do this now is:
```
sudo sixad --stop
sudo sixad -s
# Press the PS button
```

After connecting, run in another terminal to restore bluetooth
```
sudo sixad --restor
```

Try it and let me know if it works

---

### Post by inferno91 on 2011-07-17
It works, thank you! It does leave sixad running in the terminal, so I used [FONT="monospace"]sudo service sixad [start|stop][/FONT]. This causes sixad to run in the background, but it still prints stuff to my terminal, so I had to modify the init script at [FONT="monospace"]/etc/init.d/sixad[/FONT]. I changed ```
$DAEMON --start &
```
to
```
$DAEMON --start &>>/var/log/sixad &
```
and now all output from sixad goes to a log file instead of my terminal. I can run [FONT="monospace"]sudo sixad --restore[/FONT] to get my bluetooth back as usual.

So basically, what I was doing wrong was using the gui, which is apparently not working anymore? I don't really mind using the command line, though, in fact I might actually prefer it, but it might really irritate others. Now that I know to use the command line for sixad, I read the docs to figure out how to disable sensible buttons and accelerometers (Anything that has a GUI control configurator doesn't like the latter) and now I got that working too. It beats MotionInJoy on Windows, which kills bluetooth (and even if it didn't, Windows doesn't support my Bluetooth A2DP headset.)

---

### Post by falkTX on 2011-07-18
> **inferno91 said:**
> I had to modify the init script at [FONT="monospace"]/etc/init.d/sixad[/FONT]. I changed ```
$DAEMON --start &
```
to
```
$DAEMON --start &>>/var/log/sixad &
```
and now all output from sixad goes to a log file instead of my terminal.

Thanks for pointing this out; got removed by accident when doing some cleanup.
I'll update it soon

> **inferno91 said:**
> So basically, what I was doing wrong was using the gui, which is apparently not working anymore? I don't really mind using the command line, though, in fact I might actually prefer it, but it might really irritate others. Now that I know to use the command line for sixad, I read the docs to figure out how to disable sensible buttons and accelerometers (Anything that has a GUI control configurator doesn't like the latter) and now I got that working too. It beats MotionInJoy on Windows, which kills bluetooth (and even if it didn't, Windows doesn't support my Bluetooth A2DP headset.)

I just don't have the motivation to rework the GUI at this time...
QtSixA is soon to be deprecated by real drivers (official sixaxis support in the kernel and BlueZ), and my laptop isn't exactly a game machine...

I'll do it someday though, just not sure when.

---

### Post by Mvd126 on 2011-08-26
Hello! Is it possible to connect Gasia gamepad? If not, will this be fixed?

---

### Post by falkTX on 2011-08-26
> **Mvd126 said:**
> Hello! Is it possible to connect Gasia gamepad? If not, will this be fixed?

No, not at this time. The gamepad won't even work on USB.

This is not a software flaw, it's hardware (blame Gasia).
Even on windows it doesn't work correctly...

I'm not sure what I can do about this, the usual way to connect a sixaxis fails (probably because sixpair itself doesn't work for it).

I'll try to get them working again next month (got some new stuff to try), but I can't promise results.


Can someone tell if it works ok on a PS3? (a video demo will be great)

---

### Post by Mvd126 on 2011-08-28
> **falkTX said:**
> 
Can someone tell if it works ok on a PS3? (a video demo will be great)
[http://www.dealextreme.com/feedbacks/BrowseReviews.dx/sku.53716](http://www.dealextreme.com/feedbacks/BrowseReviews.dx/sku.53716)

---

### Post by Efaustus9 on 2011-09-11
Using the Qtsixa 1.5 gui interface I cant seem to disable the axis and accelerometer functions under configure this specific device. I uncheck the boxes and click finish but nothing changes. I go back at the boxes are still checked. Some emulators will not let me configure the buttons because they are picking up on the motion sensing ability of the controller. Is there a file I can manually edit or some command I can use to kill thoughs to functions of my dualshock3?

---

### Post by kruykaze on 2011-09-11
> **Efaustus9 said:**
> Using the Qtsixa 1.5 gui interface I cant seem to disable the axis and accelerometer functions under configure this specific device. I uncheck the boxes and click finish but nothing changes. I go back at the boxes are still checked. Some emulators will not let me configure the buttons because they are picking up on the motion sensing ability of the controller. Is there a file I can manually edit or some command I can use to kill thoughs to functions of my dualshock3?

I had to use sudo qtsixa to do that.

---

### Post by falkTX on 2011-09-11
Probably a permission issue.

This can be easily fixed with:
```
sudo chmod 777 -R /var/lib/sixad
```

---

### Post by Efaustus9 on 2011-09-11
That did the trick alright. Much appreciated.

---

### Post by Efaustus9 on 2011-09-11
Ok, new issue. I can seem to get emulators to register my analog sticks on the ds3. Any ideas as to why that would be? Thanks in advance.

---

### Post by Mvd126 on 2011-09-25
Hello again! Gasia gamepad not supported SDP. I insert "return 0" in first string function get_sdp_device_info and all perfect working! :D

---

### Post by falkTX on 2011-09-25
> **Mvd126 said:**
> Hello again! Gasia gamepad not supported SDP. I insert "return 0" in first string function get_sdp_device_info and all perfect working! :D

Thanks for the heads up.
But when I tried that, I got a nasty kernel crash...


I've been pretty busy with other projects, so I decided to set a deadline for QtSixA - October 13th (same day Oneiric is out).
Expect a fully working beta/RC by then

---

### Post by quequotion on 2011-09-30
Can sixad's force feedback work in WINE?

[According to the WINE Wiki]("http://wiki.winehq.org/ForceFeedback"), there is support for force feedback using DirectInput on top of evdev.

[In the WINE Forums]("http://forum.winehq.org/viewtopic.php?p=66963&sid=1e30c3ff7e7a744c529e1d000c1bbf17") I found some advice on making it work, which I have not tried.

> To get as close as possible to working, remove /dev/js* and /dev/input/js* files to force Wine using evdev driver for joysticks. Also make sure that you have read-write permissions on corresponding evdev device for your joystick (one of /dev/input/event*).

I only have one application to test the force feedback, ePSXe 1.7.0, in which it is definitely not working, but WINE seems to have some trouble with sixad. All of the input works, but the analog controls get mapped to extra, imaginary controllers.

---

### Post by falkTX on 2011-09-30
> **quequotion said:**
> Can sixad's force feedback work in WINE?

[According to the WINE Wiki]("http://wiki.winehq.org/ForceFeedback"), there is support for force feedback using DirectInput on top of evdev.

[In the WINE Forums]("http://forum.winehq.org/viewtopic.php?p=66963&sid=1e30c3ff7e7a744c529e1d000c1bbf17") I found some advice on making it work, which I have not tried.



I only have one application to test the force feedback, ePSXe 1.7.0, in which it is definitely not working, but WINE seems to have some trouble with sixad. All of the input works, but the analog controls get mapped to extra, imaginary controllers.

The force feedback *does* work in Wine, but it depends on the games.

Windows has support for custom FF effects, which linux doesn't (the base is there, but since no driver uses it, no one cares about it too).

ePSXe is one game that uses custom FF effects, so it's rumble won't work with any linux joystick.

---

### Post by quequotion on 2011-10-02
> **falkTX said:**
> The force feedback *does* work in Wine, but it depends on the games.

Thank you for giving the good news first!

---

### Post by stoke451 on 2011-10-08
Hi falkTX, thanks for all your work on this. I have everything working, sixaxis works great as either joystick or input... but I'd like to be able to switch between the two on the fly.

Or even simpler than that, I'd like the controller to be in joystick mode while XBMC is running, and input mode when it's not. Would a game profile accomplish this? Is it possible for me to make custom game profiles?

My end goal here is an HTPC controlled by sixaxis only.

---

### Post by falkTX on 2011-10-08
> **stoke451 said:**
> Hi falkTX, thanks for all your work on this. I have everything working, sixaxis works great as either joystick or input... but I'd like to be able to switch between the two on the fly.

Or even simpler than that, I'd like the controller to be in joystick mode while XBMC is running, and input mode when it's not. Would a game profile accomplish this? Is it possible for me to make custom game profiles?

My end goal here is an HTPC controlled by sixaxis only.

You can make your own profile, either by using the GUI or modifying the files directly.
For modifying the files, the manual explains how it works:
[http://qtsixa.git.sourceforge.net/git/gitweb.cgi?p=qtsixa/qtsixa;a=blob_plain;f=manual.pdf;hb=refs/heads/master](http://qtsixa.git.sourceforge.net/git/gitweb.cgi?p=qtsixa/qtsixa;a=blob_plain;f=manual.pdf;hb=refs/heads/master)

It's not possible to change input/joystick modes on the fly.
BUT, you can use the "disable mouse/key using l3/r3" which works as nicely.

Simply activate joystick and input, and the l3/r3 option. When you don't need the axis, press L3; for buttons it's R3. Revert by using l3 or r3 again (joystick mode always works).
(L3/R3 are the axis buttons. You can press them down, it's a button)

---

### Post by stoke451 on 2011-10-08
> **falkTX said:**
> You can make your own profile, either by using the GUI or modifying the files directly.

I understand the device profiles, but the manual doesn't mention game profiles, which I was thinking I could create one for XBMC.

> **falkTX said:**
> BUT, you can use the "disable mouse/key using l3/r3" which works as nicely.

I'll give this a try, it sounds like what I'm looking for.

---

### Post by quequotion on 2011-10-09
I don't give up easily ;)

I read somewhere that xserver-xorg-input-joystick can wrap force feedback calls from WINE and feed them to events.

As a test I ran sixad in a terminal while playing a game in ePSXe 1.7.0

With xserver-xorg-input-joystick, sixad reports feedback calls, but no vibration occurs on the controller.

Without xserver-xorg-input-joystick sixad reports nothing about feedback in this scenario.

Also, I experienced some bad behavior from sixad last night (linux always seems to act up when I have parties...). The controllers were not connecting properly by bluetooth (possibly due to low battery) so I tried cables.

Usually, one plugs in the USB cable and then preses the PS button to get the HID driver to pick up the controller, but it wasn't working.. None of them would operate in USB mode (jstest showed no movement at all) and when I disconnected them they each connected by Bluetooth immediately, but displayed strange LED ...combinations? (2 *and* 4 / 3 *and* 4).

It may have something to do with the connection, since I used an un-powered USB2.0 splitter to connect four controllers to one port, but neither sixad nor ubuntu gave any warning and the controllers do recharge properly with the splitter.

---

### Post by RominuX on 2011-10-23
Hy everyone,
I read some forum without found some interesting solution to my problem.
I've install QtSixA without any problem, and i see my controller on USB mode (led blinking, and stop when batteries is full), so I go to the menu for pairing my controller and no problem, but when i disconnect from USB, led blinking 10sec (i can see my sixaxis on the QtSixA window) but Sixaxis will shut down after.
I've tried a 'sixad --stop ; sixad --start' to force the connection in vain.

I've read that is possible that my PS3 controller is not the 'official' by SONY.

Did anyone have a solution for me ?

RominuX

---

### Post by falkTX on 2011-10-23
> **RominuX said:**
> Hy everyone,
I read some forum without found some interesting solution to my problem.
I've install QtSixA without any problem, and i see my controller on USB mode (led blinking, and stop when batteries is full), so I go to the menu for pairing my controller and no problem, but when i disconnect from USB, led blinking 10sec (i can see my sixaxis on the QtSixA window) but Sixaxis will shut down after.
I've tried a 'sixad --stop ; sixad --start' to force the connection in vain.

I've read that is possible that my PS3 controller is not the 'official' by SONY.

Did anyone have a solution for me ?

RominuX

I did my best trying to make those non-Sony controllers to work, but failed.
If you know how to code, you can hack it and try to make it work. Get the code with:
```
apt-get source qtsixa
```

note sixad/bluetooth.cpp, I used GASIA_GAMEPAD_HACKS macro for trying to make it work.

But basically, when support for this is enabled (bypassing bluetooth SDP request) we get a nasty kernel crash...

---

### Post by RominuX on 2011-10-23
Thx for your reply,
a 'cat /proc/bus/input/devices' show me: Name="SHENGHIC 2009/0708ZXW-V1Inc. PLAYSTATION(R)3Conteroller"

I don't know how to code in C, but I will look the source.

Is this a problem with the internal firmware of the controller, or the bluetooth ? (if you know)

Thx
Bye



Sorry for my imperfect english (I'm french ;-)

---

### Post by falkTX on 2011-10-23
> **RominuX said:**
> Thx for your reply,
a 'cat /proc/bus/input/devices' show me: Name="SHENGHIC 2009/0708ZXW-V1Inc. PLAYSTATION(R)3Conteroller"

I don't know how to code in C, but I will look the source.

Is this a problem with the internal firmware of the controller, or the bluetooth ? (if you know)

Thx
Bye



Sorry for my imperfect english (I'm french ;-)

If you don't know how to code, just ignore this. I don't even fully understand what's going on there.

The device doesn't work currently because it lacks SDP session support, which is required in the current driver (based on the old 'hidd' one).

---

### Post by RominuX on 2011-10-23
If I understand your 'GASIA_GAMEPAD_HACKS', I have to replace the 4 files in your 'Experimental Gasia Gamepad hacks, force disconnect on battery low' in the source and build the new package, and test (but there is a chance my linux kernel crash) ??

I'll try, but how do it work ?

I'm trying some stuff before buying a real SONY controller, and to put back the fake one in the dust ;-)

RominuX

---

### Post by falkTX on 2011-10-23
> **RominuX said:**
> If I understand your 'GASIA_GAMEPAD_HACKS', I have to replace the 4 files in your 'Experimental Gasia Gamepad hacks, force disconnect on battery low' in the source and build the new package, and test (but there is a chance my linux kernel crash) ??

I'll try, but how do it work ?

I'm trying some stuff before buying a real SONY controller, and to put back the fake one in the dust ;-)

RominuX

I can't recommend this for you. You seem to not have the necessary experience for this, and chances it will work are very very minimal.

There's nothing better than the original Sixaxis anyway ;)

---

### Post by RominuX on 2011-10-23
I make my way, I wrote some shell script, and tried the C in console and I stopped because I had no time to continue, but I like make test, install/uninstall and try new software (my ubuntu won't lol ;-)

---

### Post by Mvd126 on 2011-10-24
In Gasia recv function don't work and for enabled need other array.

I got the result by doing:

In shared.cpp change function enable_sixaxis
```

void enable_sixaxis(int csk)
{
    char buf[128];

    unsigned char enable[] = {0xA2, 0x01, 0x00, 0x96, 0x01, 0x96, 0xFF, 0x00, 0x00, 0x00, 0x00, 0x10, 0xFF, 0x27, 0x10, 0x00, 0x32, 0xFF, 0x27, 
0x10, 0x00, 0x32, 0xFF, 0x27, 0x10, 0x00, 0x32, 0xFF, 0x27, 0x10, 0x00, 0x32, 0x00, 0x00, 0x00, 0x00, 0x00, 0x00, 0x00, 0x00, 0x00, 0x00, 0x00, 0x00, 0x00, 0x00,  
0x00, 0x00, 0x00, 0x00
    };

    /* enable reporting */
    send(csk, enable, sizeof(enable), 0);
    //recv(csk, buf, sizeof(buf), 0);
}

```In sixad-sixaxis.cpp string 262
```
//led_n = set_sixaxis_led(csk, settings.led, settings.rumble.enabled);
```cd sixad
make all
sudo make install
/etc/init.d/sixad start
Press PS3
Wait rumble Gasia
cat /dev/input/js1

---

### Post by falkTX on 2011-10-24
> **Mvd126 said:**
> In Gasia recv function don't work and for enabled need other array.

I got the result by doing:

In shared.cpp change function enable_sixaxis
```

void enable_sixaxis(int csk)
{
    char buf[128];

    unsigned char enable[] = {0xA2, 0x01, 0x00, 0x96, 0x01, 0x96, 0xFF, 0x00, 0x00, 0x00, 0x00, 0x10, 0xFF, 0x27, 0x10, 0x00, 0x32, 0xFF, 0x27, 
0x10, 0x00, 0x32, 0xFF, 0x27, 0x10, 0x00, 0x32, 0xFF, 0x27, 0x10, 0x00, 0x32, 0x00, 0x00, 0x00, 0x00, 0x00, 0x00, 0x00, 0x00, 0x00, 0x00, 0x00, 0x00, 0x00, 0x00,  
0x00, 0x00, 0x00, 0x00
    };

    /* enable reporting */
    send(csk, enable, sizeof(enable), 0);
    //recv(csk, buf, sizeof(buf), 0);
}

```In sixad-sixaxis.cpp string 262
```
//led_n = set_sixaxis_led(csk, settings.led, settings.rumble.enabled);
```cd sixad
make all
sudo make install
/etc/init.d/sixad start
Press PS3
Wait rumble Gasia
cat /dev/input/js1

Nice! I can see it working now :)

Where did you get these values?
Now I need a way to make this work with and without Gasia hacks (detecting a Gasia gamepad somehow...)

---

### Post by RominuX on 2011-10-24
Ok,

Thx for your answer Mvd126, but when I make, I have some error (some missing files).

   I'll let the professionals do until I go put my eyes on a C programming book ;-)



Thx both of you.

---

### Post by falkTX on 2011-10-24
> **RominuX said:**
> Ok,

Thx for your answer Mvd126, but when I make, I have some error (some missing files).

   I'll let the professionals do until I go put my eyes on a C programming book ;-)



Thx both of you.

I added this latest changes (and a bit more, to fix rumble and led number) to qtsixa git code.

I'm still doing tests though.
The main problem now is that the gamepad doesn't want to disconnect... LED 4 is always on, and the usual 'holding PS for 15secs' doesn't work. So I'll have to wait until the battery gets fully used, charge it a bit, and re-test.

I'll let you know of any updated on this.

---

### Post by RominuX on 2011-10-24
Thx for your work.

I keep an eye on this.

---

### Post by Mvd126 on 2011-10-24
> **falkTX said:**
> 
The main problem now is that the gamepad doesn't want to disconnect... LED 4 is always on, and the usual 'holding PS for 15secs' doesn't work. So I'll have to wait until the battery gets fully used, charge it a bit, and re-test.

For me help this button.

---

### Post by falkTX on 2011-10-25
> **Mvd126 said:**
> For me help this button.

I know about that, but the Gasia gamepads (or at least mine) don't have it.
That tiny space is just a hole... :(

---

### Post by extradessert on 2011-10-25
OK a few problems:

 First, I've been trying to figure out the right buttons in the input profile to set as mouse scroll wheel, with no success.  I can get the left and right mouse buttons working on the controller, but not the scroll wheel. What is the right button for that, or does qtsixa support using it anymore?  
I did this before with 'button 4' and 'button 5' in qtsixa 1.2.1 on 9.10, but even since I upgraded to 10.04  with qtsixa 1.4.97+ I cant figure this out.  

2nd: For some odd reason Qtsixa freezes up when trying to disconnect the controller, and it seems to come back to life after asking for my password. 1.4.97 never used to do this...  (BTW when I upgraded to 1.5.1 from 1.4.97, I had to reinstall BlueZ after installing qtsixa, as it was acting like bluez was never installed on the system.)

 Using qtsixa 1.5.1, ubuntu 10.04, genuine DS3 controller.

---

### Post by falkTX on 2011-10-25
> **extradessert said:**
> OK a few problems:

 First, I've been trying to figure out the right buttons in the input profile to set as mouse scroll wheel, with no success.  I can get the left and right mouse buttons working on the controller, but not the scroll wheel. What is the right button for that, or does qtsixa support using it anymore?  
I did this before with 'button 4' and 'button 5' in qtsixa 1.2.1 on 9.10, but even since I upgraded to 10.04  with qtsixa 1.4.97+ I cant figure this out.  

2nd: For some odd reason Qtsixa freezes up when trying to disconnect the controller, and it seems to come back to life after asking for my password. 1.4.97 never used to do this...  (BTW when I upgraded to 1.5.1 from 1.4.97, I had to reinstall BlueZ after installing qtsixa, as it was acting like bluez was never installed on the system.)

 Using qtsixa 1.5.1, ubuntu 10.04, genuine DS3 controller.

The previous versions were a bit problematic, and the update may damage bluez installation yes (but won't happen again).
I needed a way to prevent normal bluetooth from starting, so I simply renamed the bluetoothd binary file (kinda nasty, yes...). Now it just runs a simple python script that block bluez DBus, making the normal bluetooth unable to start for some seconds (enough to connect the sixaxis).

I'm not sure about the wheel though, things changed drastically since 1.2.x versions (no more HAL).

The GUI is crap, I know that. I don't really have the motivation to rework it...
It works fine for creating new profiles, and see what's connected, but otherwise, let's say it, it sucks.

The driver itself was my focus for this release. The manual:
[http://qtsixa.sourceforge.net/manual.pdf](http://qtsixa.sourceforge.net/manual.pdf)
gives you all the information to create your own profiles, so you don't actually need the GUI.
Check the manual and confirm if your sixaxis profile (generated by QtSixA) is correct please.

---

### Post by extradessert on 2011-10-25
> **falkTX said:**
> The previous versions were a bit problematic, and the update may damage bluez installation yes (but won't happen again).
I needed a way to prevent normal bluetooth from starting, so I simply renamed the bluetoothd binary file (kinda nasty, yes...). Now it just runs a simple python script that block bluez DBus, making the normal bluetooth unable to start for some seconds (enough to connect the sixaxis).

I'm not sure about the wheel though, things changed drastically since 1.2.x versions (no more HAL).
A weird script that doesnt work...I still have to run 'sixad --stop' and 'sixad --start' anytime I need to connect the controller, if I don't then it either wont recognize it or spams the classic "Grant access to '00001124-0000-1000-8000-00805f9b34fb'" window.
I miss the old 1.4.97 from May.. last version that actually worked right (aka didnt need sixad start/stop)

You don't know of anything for the mouse wheel?? Bummer :(

> **falkTX said:**
> 
The GUI is crap, I know that. I don't really have the motivation to rework it...
It works fine for creating new profiles, and see what's connected, but otherwise, let's say it, it sucks.

The driver itself was my focus for this release. The manual:
[http://qtsixa.sourceforge.net/manual.pdf](http://qtsixa.sourceforge.net/manual.pdf)
gives you all the information to create your own profiles, so you don't actually need the GUI.
Check the manual and confirm if your sixaxis profile (generated by QtSixA) is correct please.

I have edited the profile myself, in order to get L3 and R3 working as buttons (another feature the gui is missing), its fine.

---

### Post by falkTX on 2011-10-25
> **extradessert said:**
> A weird script that doesnt work...I still have to run 'sixad --stop' and 'sixad --start' anytime I need to connect the controller, if I don't then it either wont recognize it or spams the classic "Grant access to '00001124-0000-1000-8000-00805f9b34fb'" window.
I miss the old 1.4.97 from May.. last version that actually worked right (aka didnt need sixad start/stop)

I removed the udev rule (auto-start sixad) on purpose, it was just bad and couldn't even connect 2 sixaxis at the same time. Plus, it doesn't work on recent kernels.

you can still use 'sixad --boot-yes' to start sixad on boot, so it will "just work", although any other bluetooth devices won't work.

---

### Post by extradessert on 2011-10-25
> **falkTX said:**
> I removed the udev rule (auto-start sixad) on purpose, it was just bad and couldn't even connect 2 sixaxis at the same time. Plus, it doesn't work on recent kernels.

you can still use 'sixad --boot-yes' to start sixad on boot, so it will "just work", although any other bluetooth devices won't work.

Ah, makes sense. Will have to try the boot option.

---

### Post by ThyMYthOS on 2011-10-30
> **falkTX said:**
> Nice! I can see it working now :)

Where did you get these values?
Now I need a way to make this work with and without Gasia hacks (detecting a Gasia gamepad somehow...)

Should be possible to select by the BT MAC. My Gasia is registered by "00265C	Hon Hai Precision Ind. Co.,Ltd.".

By the way, I have another 3rd party controller, that works with USB out of the box, but sixpair won't work.

I will try to see what the PS3 actually does with the controller by writing a USB gadgetfs driver for my pandaboard.

---

### Post by abudabi on 2011-11-12
wow **falkTX**
 
Thanks for this great app.. Looks like it's just what I'm needing. I see there is an oneiric version of your ppa out... is everything fine under 11.10? Do I just follow the guide on the 1st page?
 
I've read the last few pages of this thread hoping to find some mention of oneiric but alas.. no such luck.
 
Please advise and thanks again!

---

### Post by abudabi on 2011-11-12
OK.. so I've read the manual. For ease of use It seems I need to run it with boot-yes argument. I understand that this breaks other BT equipment. Only other device I have is the PS3 remote (would be nice to use this but not a deal breaker). So my quesiton is ... will the boot-yes argument prevent PS3 remote from working?
 
Thanks in advance

---

### Post by falkTX on 2011-11-12
> **abudabi said:**
> wow **falkTX**
 
Thanks for this great app.. Looks like it's just what I'm needing. I see there is an oneiric version of your ppa out... is everything fine under 11.10? Do I just follow the guide on the 1st page?
 
I've read the last few pages of this thread hoping to find some mention of oneiric but alas.. no such luck.
 
Please advise and thanks again!

I'm running Oneiric 64bit and all works fine.

You should take the time to read the manual:
[http://qtsixa.sourceforge.net/manual.pdf](http://qtsixa.sourceforge.net/manual.pdf)

Everything is explained there

---

### Post by falkTX on 2011-11-13
> **abudabi said:**
> OK.. so I've read the manual. For ease of use It seems I need to run it with boot-yes argument. I understand that this breaks other BT equipment. Only other device I have is the PS3 remote (would be nice to use this but not a deal breaker). So my quesiton is ... will the boot-yes argument prevent PS3 remote from working?
 
Thanks in advance

For now, yes. (I still need a better way to deal with the remote)
You should first connect the remote, then sixaxis.

I'll try to address this on a future release.

---

### Post by abudabi on 2011-11-13
Some good .. some bad.
 
I installed the ap and it's super easy to configure... Ran the sixad command and got it up and running with mame. AWESOME!! 
 
Then I thought I'd try the start at boot option to make it nice and simple. After rebooting i did a ps -ef and sure enough sixad was running. I pressed the PS button and voila.. it got the no 1 LED and connected. I then held in the PS button to turn it off and immediately pressed it again to turn it back on.
 
It then did the LED dance and as soon as it locked no 1 LED the while system froze. I had to do a hard reboot. Below is the sixad log file : 
 
 
```
sixad-bin[1651]: started
sixad-bin[1651]: sixad started, press the PS button now
sixad-sixaxis[2236]: started
sixad-sixaxis[2236]: Connected 'PLAYSTATION(R)3 Controller (00:19:C1:3C:EE:78)'$
sixad-sixaxis[2236]: Bad Sixaxis buffer (out of battery?), disconneting now...
sixad-sixaxis[2246]: started
sixad-sixaxis[2246]: Connected 'PLAYSTATION(R)3 Controller (00:19:C1:3C:EE:78)'$
Can't read version info hci0: Network is down (100)
sixad-bin[1677]: started
```
 
So is there something I'm doing wrong or what else do you think could be at fault?

---

### Post by falkTX on 2011-11-13
> **abudabi said:**
> Some good .. some bad.
 
I installed the ap and it's super easy to configure... Ran the sixad command and got it up and running with mame. AWESOME!! 
 
Then I thought I'd try the start at boot option to make it nice and simple. After rebooting i did a ps -ef and sure enough sixad was running. I pressed the PS button and voila.. it got the no 1 LED and connected. I then held in the PS button to turn it off and immediately pressed it again to turn it back on.
 
It then did the LED dance and as soon as it locked no 1 LED the while system froze. I had to do a hard reboot. Below is the sixad log file : 
 
 
```
sixad-bin[1651]: started
sixad-bin[1651]: sixad started, press the PS button now
sixad-sixaxis[2236]: started
sixad-sixaxis[2236]: Connected 'PLAYSTATION(R)3 Controller (00:19:C1:3C:EE:78)'$
sixad-sixaxis[2236]: Bad Sixaxis buffer (out of battery?), disconneting now...
sixad-sixaxis[2246]: started
sixad-sixaxis[2246]: Connected 'PLAYSTATION(R)3 Controller (00:19:C1:3C:EE:78)'$
Can't read version info hci0: Network is down (100)
sixad-bin[1677]: started
```
 
So is there something I'm doing wrong or what else do you think could be at fault?

Well, I need to ask you to try it again and see if it still happens.
The 'Can't read version info hci0: Network is down (100)' message is kinda suspicious (bluetooth turned itself off?).

You can also try to disable rumble if this keeps happening.

---

### Post by abudabi on 2011-11-14
Cool.. will do when I get home.. I did it last night... and I seem to recall my box crashing when I activated the controller with sixad NOT active... just normal BT going. is that possible?
 
I was pretty tired when doing it.. so maybe I made a mistake. Will let you know how it goes.
 
Thanks for the prompt responses!

---

### Post by falkTX on 2011-11-14
> **abudabi said:**
> Cool.. will do when I get home.. I did it last night... and I seem to recall my box crashing when I activated the controller with sixad NOT active... just normal BT going. is that possible?
 
I was pretty tired when doing it.. so maybe I made a mistake. Will let you know how it goes.
 
Thanks for the prompt responses!

I would suspect this is a bt driver problem, or hardware.
It's probably not a problem with qtsixa, but something else in the system causing the freeze.

You should try with a different bt adapter later.

---

### Post by jabryl on 2011-11-14
Hello.

I've been trying to get my ds3 working with Ubuntu and have run into a couple of problems.

First, I've been getting the "Grant access" popup when trying to connect.
I've been using the "sixad --stop" and "sixad --start" commands posted earlier in this thread and that does work, but I have to do it after every reboot. Is there a more permanent fix?

Second, I cannot seem to disable the accelerators. I've tried disabling them in the profiles in QtSixA, but it doesn't seem to have any effect.

I'm using Ubuntu 10.04 and QtSixA 1.5.1.

---

### Post by falkTX on 2011-11-14
> **jabryl said:**
> Hello.

I've been trying to get my ds3 working with Ubuntu and have run into a couple of problems.

First, I've been getting the "Grant access" popup when trying to connect.
I've been using the "sixad --stop" and "sixad --start" commands posted earlier in this thread and that does work, but I have to do it after every reboot. Is there a more permanent fix?

Second, I cannot seem to disable the accelerators. I've tried disabling them in the profiles in QtSixA, but it doesn't seem to have any effect.

I'm using Ubuntu 10.04 and QtSixA 1.5.1.

'sixad --boot-yes' enables sixad on boot.

you should edit the default profile and really make sure the setting applies (re-show the config dialog and check if it changed).
you can always edit the profiles manually, stored in /var/lib/sixad/profiles, the manual provides full-info for this.

---

### Post by Arkadius on 2011-11-16
I have been fiddling around with Qtsixa / Sixad for a fair amount of time now, and I have managed to getting both of my PS3 remotes (one factory standard that came with the PS3, and one DS3 that I bought a little later. Both were bought around in ~2008).

(I am currently at work and do not have the specific models of the controllers, but I can provide the specifics when I get home.)

The thing is that I can't get either to work without the LEGACY support which is what would be ideal. 

I did manage to get the LEDs to work on both controllers, and the Devices show in /dev/input/js0 and /dev/input/js1 after running sixpair, sixad -stop, sixad -s and pressing the ps button. Howver, running JSTest posts negative results and shows that no buttons on the remote appear to be active, the battery and signal strengh show 0% in QTsixa and no commands register when any buttons are pressed. 

(I'll post, exactly, what Jstest shows when I get home)

I've looked up the manual several times, and roamed on this thread multiple times. 

I've been trying since I had NATTY, but quickly gave up as it had compatibility issues with it, but I have now recently upgraded to oneiric ocelot which supposedly works well, and I am still having issues with it, although it is just recently (yesterday) that I got the Legacy drivers to, at least, work.

Any insight on this?

Please advise,
Thank you in advance

---

### Post by falkTX on 2011-11-16
> **Arkadius said:**
> I have been fiddling around with Qtsixa / Sixad for a fair amount of time now, and I have managed to getting both of my PS3 remotes (one factory standard that came with the PS3, and one DS3 that I bought a little later. Both were bought around in ~2008 ).

(I am currently at work and do not have the specific models of the controllers, but I can provide the specifics when I get home.)

The thing is that I can't get either to work without the LEGACY support which is what would be ideal. 

I did manage to get the LEDs to work on both controllers, and the Devices show in /dev/input/js0 and /dev/input/js1 after running sixpair, sixad -stop, sixad -s and pressing the ps button. Howver, running JSTest posts negative results and shows that no buttons on the remote appear to be active, the battery and signal strengh show 0% in QTsixa and no commands register when any buttons are pressed. 

(I'll post, exactly, what Jstest shows when I get home)

I've looked up the manual several times, and roamed on this thread multiple times. 

I've been trying since I had NATTY, but quickly gave up as it had compatibility issues with it, but I have now recently upgraded to oneiric ocelot which supposedly works well, and I am still having issues with it, although it is just recently (yesterday) that I got the Legacy drivers to, at least, work.

Any insight on this?

Please advise,
Thank you in advance

So you're saying that, even with the original Sony sixaxis, the custom driver is still not working for you?
If that is the case, please try a different bluetooth adapter (internal ones are usually problematic).

Specific model/info will be appreciated (from the sixaxis and yours bluetooth adapter too).

---

### Post by quequotion on 2011-11-28
What's your opinion of this? [http://www.pabr.org/sixlinux/sixlinux.en.html](http://www.pabr.org/sixlinux/sixlinux.en.html)

I think it was mentioned somewhere in this thread before that a kernel driver for sixaxis is in the works. According to this documentation, the basic functions of the sixaxis should already be working without sixad. This is not true as far as I can tell (only testing in Ubuntu, currently 11.10 with kernel 3.0.0-14-generic). Furthermore this driver is rather incomplete: no accelerometers, no pressure sensitivity, no leds, etc.

I don't really understand the complexity involved, but why is this wheel being re-invented? With some modification, couldn't sixad become a kernel module itself?

---

### Post by falkTX on 2011-11-28
> **quequotion said:**
> What's your opinion of this? [http://www.pabr.org/sixlinux/sixlinux.en.html](http://www.pabr.org/sixlinux/sixlinux.en.html)

I think it was mentioned somewhere in this thread before that a kernel driver for sixaxis is in the works. According to this documentation, the basic functions of the sixaxis should already be working without sixad. This is not true as far as I can tell (only testing in Ubuntu, currently 11.10 with kernel 3.0.0-14-generic). Furthermore this driver is rather incomplete: no accelerometers, no pressure sensitivity, no leds, etc.

I don't really understand the complexity involved, but why is this wheel being re-invented? With some modification, couldn't sixad become a kernel module itself?

As you might guess, writing a kernel driver requires low-level kernel knowledge, which  I don' have.
sixad/QtSixA is here _right now_, as we wait for the proper sixaxis support to be implemented in the kernel. I don't see this happening any time soon though.

---

### Post by simonb530 on 2011-11-29
First, I would like to thank falkTX for the Qtsixa program. It's wonderful, but I'm having a few problems and was hoping you could help. I'm using Ubuntu 10.04

1) If I enable sixaxis boot (sixad --boot-yes), I lose sound on restart. I can get sound back by disabling and restarting.

2) Do you know how to use the PS3 controller in XBMC?

Any input would greatly be appreciated.

Thank You

---

### Post by falkTX on 2011-11-30
> **simonb530 said:**
> First, I would like to thank falkTX for the Qtsixa program. It's wonderful, but I'm having a few problems and was hoping you could help. I'm using Ubuntu 10.04

1) If I enable sixaxis boot (sixad --boot-yes), I lose sound on restart. I can get sound back by disabling and restarting.

2) Do you know how to use the PS3 controller in XBMC?

Any input would greatly be appreciated.

Thank You

1) You probably have bluez-alsa installed, remove it.

2) I never used it, but I assume it works by default (connect the sixaxis first, then start XBMC). afaik, it has pre-set joysticks configurations, and sixaxis is one of them.
If it doesn't work, just create an input profile that matches XBMC keys.

---

### Post by simonb530 on 2011-11-30
Thanks for the quick response. After I posted I figured it out a way around the sixad --boot-yes just set the command (sixad -s) up in start up application, but i will look into bluez-alsa. I also figured out the profiles and got control through xbmc, but one more problem lingered if possible.

I know the qtsixa wasnt setup for the sony BD remote but is there away to auto sync the remote on boot up like the --boot-yes or start up application. I have tried using the start up application but didnt think it was possible since the command sixad -remote required input (press ENTER and SELECT) at that time. Is there any way around this like having the sixad -remote program running constant in the background.

Thanks for any input.

---

### Post by falkTX on 2011-11-30
> **simonb530 said:**
> Thanks for the quick response. After I posted I figured it out a way around the sixad --boot-yes just set the command (sixad -s) up in start up application, but i will look into bluez-alsa. I also figured out the profiles and got control through xbmc, but one more problem lingered if possible.

I know the qtsixa wasnt setup for the sony BD remote but is there away to auto sync the remote on boot up like the --boot-yes or start up application. I have tried using the start up application but didnt think it was possible since the command sixad -remote required input (press ENTER and SELECT) at that time. Is there any way around this like having the sixad -remote program running constant in the background.

Thanks for any input.

Sadly there's no way to get auto-remote working.
The remote finding process makes bluetooth barely usable (heavy usage when searching for devices), so all the other devices in the system will appear 'stuck'.
Sixaxis search is not a real search at all (instead of looking for new connections, we wait for them). As you might have noticed, sixaxis is not a regular bluetooth device, it doesn't just sit doing nothing and wait for connections, it actually send requests to the computer/PS3.

Anyway, there's no easy/auto way of doing this, sorry.

---

### Post by Pano89 on 2011-12-08
Hi falkTX, I have download QtSixA and it works perfectly;
but, is it possible to "see" string that DS3 send to the pc??

thanks

---

### Post by falkTX on 2011-12-08
> **Pano89 said:**
> Hi falkTX, I have download QtSixA and it works perfectly;
but, is it possible to "see" string that DS3 send to the pc??

thanks

Just use 'hcidump', the whole bluetooth is "dumped" to terminal.

---

### Post by Pano89 on 2011-12-08
> **falkTX said:**
> Just use 'hcidump', the whole bluetooth is "dumped" to terminal.
ok thanks, using hcidump -x I see them

but if I need to read it, save in a array and use it? 

thanks
regards

---

### Post by falkTX on 2011-12-08
> **Pano89 said:**
> ok thanks, using hcidump -x I see them

but if I need to read it, save in a array and use it? 

thanks
regards

then use some script (awk or grep magic or whatever)

---

### Post by Pano89 on 2011-12-09
when DS3 is connect by bluetooth the hidrawX file is not created, why??
(when DS3 is connect by usb it is created)

I'm trying to use 
[sudo] hidraw-dump /dev/hidrawX
[sudo] sixad-raw /dev/hidrawX

but in /dev there is just a hidraw0 and it is about my mouse :|

thanks

---

### Post by falkTX on 2011-12-09
> **Pano89 said:**
> when DS3 is connect by bluetooth the hidrawX file is not created, why??
(when DS3 is connect by usb it is created)

I'm trying to use 
[sudo] hidraw-dump /dev/hidrawX
[sudo] sixad-raw /dev/hidrawX

but in /dev there is just a hidraw0 and it is about my mouse :|

thanks

You don't need the hidraw device when using sixad (all the functionality is there...).
If you want the hidraw device, edit /etc/default/sixad, set LEGACY=1 and reconnect your joysticks.

---

### Post by Pano89 on 2011-12-10
> **falkTX said:**
> You don't need the hidraw device when using sixad (all the functionality is there...).
If you want the hidraw device, edit /etc/default/sixad, set LEGACY=1 and reconnect your joysticks.ah ok, thanks

and a last qustion; what is main function who call the functions in file sixaxis.cpp?? (functions do_joystick, do_input, do_rumble, set_sixaxis_led)

---

### Post by falkTX on 2011-12-10
> **Pano89 said:**
> ah ok, thanks

and a last qustion; what is main function who call the functions in file sixaxis.cpp?? (functions do_joystick, do_input, do_rumble, set_sixaxis_led)

sixad-sixaxis.cpp:172, void process_sixaxis(...)

Just remember - the code is GPL v2. So if you make changes and release binaries to the public, you have to send me the changes you made to the source code.

---

### Post by fennol on 2011-12-16
hello falk
sry for my bad english...

it dont work for now (well, ~2 months ago), after update sixad on my debian squeeze (unfortunately dont remember version before update). im used launchpad for software install.

i try run server, it says thats all ok, waiting but nothing happens. when i stop server with ctrl+c it post this
```
Traceback (most recent call last):
  File "/usr/sbin/sixad-dbus-blocker", line 25, in <module>
    sleep(1)

```
sixad-dbus-blocker try to check ("/tmp/.sixad-dbus-blocker.pid")
else - break, so, file does not exist. 
whats wrong? maybe some libs old version?

---

### Post by falkTX on 2011-12-16
> **fennol said:**
> hello falk
sry for my bad english...

it dont work for now (well, ~2 months ago), after update sixad on my debian squeeze (unfortunately dont remember version before update). im used launchpad for software install.

i try run server, it says thats all ok, waiting but nothing happens. when i stop server with ctrl+c it post this
```
Traceback (most recent call last):
  File "/usr/sbin/sixad-dbus-blocker", line 25, in <module>
    sleep(1)

```
sixad-dbus-blocker try to check ("/tmp/.sixad-dbus-blocker.pid")
else - break, so, file does not exist. 
whats wrong? maybe some libs old version?

This is normal, you can safely ignore it.
the sixad-dbus-blocker is a simple python script that blocks normal bluetooth from starting up (and displaying those annoying permission dialogs).
This used to be the task of hcid, but it no longer works on new kernels, so this script takes it's place.

---

### Post by supercheetah on 2011-12-29
It seems that whatever QTSixA uses for invoking sudo isn't working because in order for me to get this working correctly, I need to run it with sudo from the command line, otherwise it just rejects my password.

---

### Post by falkTX on 2011-12-29
> **supercheetah said:**
> It seems that whatever QTSixA uses for invoking sudo isn't working because in order for me to get this working correctly, I need to run it with sudo from the command line, otherwise it just rejects my password.

I believe it's a bug with gksu, I've seen it happening a couple of times.
Nothing in QtSixA gui has changed recently, and it was working before, so...

Does 'gksu gedit' works?

---

### Post by supercheetah on 2011-12-29
> **falkTX said:**
> I believe it's a bug with gksu, I've seen it happening a couple of times.
Nothing in QtSixA gui has changed recently, and it was working before, so...

Does 'gksu gedit' works?
Yes.

---

### Post by falkTX on 2011-12-29
> **supercheetah said:**
> Yes.

Assuming you get:
> Will use 'gksu' for root actions
when starting 'qtsixa' from a terminal, try this now:
```
gksu --description /usr/share/applications/qtsixa.desktop -- gedit
```
and report back if it works (gedit opens)

---

### Post by supercheetah on 2011-12-29
It works without any issues.

---

### Post by johnnyrico on 2012-01-17
Hi Falk,

Thanks for the great app, I've had it working well with a friends genuine PS3 controller, however sadly mine is a Gasia one. 
Looking back through the thread I see there are some hacks for it. Do they work at present? I've managed to get it to compile and install with the Gasia hacks enabled but haven't had any luck so far getting it to work.

Any help or pointers greatly appreciated. :)

Brian

---

### Post by falkTX on 2012-01-17
> **johnnyrico said:**
> Hi Falk,

Thanks for the great app, I've had it working well with a friends genuine PS3 controller, however sadly mine is a Gasia one. 
Looking back through the thread I see there are some hacks for it. Do they work at present? I've managed to get it to compile and install with the Gasia hacks enabled but haven't had any luck so far getting it to work.

Any help or pointers greatly appreciated. :)

Brian

Getting it to work is not worth it. With the hacks enabled it does work for some time, but you may have a kernel panic/crash randomly, and the device may also randomly disconnect itself.
That is just a bad device, stay away from it...

---

### Post by Khudsa on 2012-01-18
I have bought a generic ps3 gamepad expecting that it will work on usb, I don't know anything related to gasia. Now I find that it's gasia one. It cannot work even on usb? jtest-gtk detetect it, but it doesn't work. Anybody knows how to get it working at least connected by usb cable?

Thanks.

---

### Post by falkTX on 2012-01-18
> **Khudsa said:**
> I have bought a generic ps3 gamepad expecting that it will work on usb, I don't know anything related to gasia. Now I find that it's gasia one. It cannot work even on usb? jtest-gtk detetect it, but it doesn't work. Anybody knows how to get it working at least connected by usb cable?

Thanks.

This Gasia device will not even work on USB, sorry if I forgot to mention that.

You should replace it/trade it ASAP.

---

### Post by verbtim on 2012-01-23
Hi, 

I have a German keyboard on my laptop (Xubuntu 11.10), so my default layout is the German one (de). Whenever I connect the Dualshock 3 with the USB the layout gets changed to English (us). This also happens when I use Bluetooth. 

I also configured the controller to act as input (keyboard/mouse), could this be the problem?

(QtSixA version: 1.5.1 from the ppa, with 64bit 3.0.0 kernel)

---

### Post by falkTX on 2012-01-23
> **verbtim said:**
> Hi, 

I have a German keyboard on my laptop (Xubuntu 11.10), so my default layout is the German one (de). Whenever I connect the Dualshock 3 with the USB the layout gets changed to English (us). This also happens when I use Bluetooth. 

I also configured the controller to act as input (keyboard/mouse), could this be the problem?

(QtSixA version: 1.5.1 from the ppa, with 64bit 3.0.0 kernel)

I use a portuguese keyboard layout here, and never had any issues. (I've been using it like this since I first started with Linux),
I say you have something not properly configured.

If you say 'This also happens when I use Bluetooth.', then it's not a problem with the sixaxis driver.

---

### Post by dartmusic on 2012-02-06
I've installed Qtsixa via the PPA on 11.10 64bit and am not able to get a Sixaxis PS3 controller to connect via bluetooth.  I get zero response from the GUI and when I start it via the terminal, it connects, I get a rumble from the controller and then a line that says:

Bad Sixaxis buffer (out of battery?), disconneting now...

(Misspelling is from the CLI.)

I've searched the web and this thread and can't come up with anything.  Anyone have any ideas?

Thanks.

---

### Post by falkTX on 2012-02-06
> **dartmusic said:**
> I've installed Qtsixa via the PPA on 11.10 64bit and am not able to get a Sixaxis PS3 controller to connect via bluetooth.  I get zero response from the GUI and when I start it via the terminal, it connects, I get a rumble from the controller and then a line that says:

Bad Sixaxis buffer (out of battery?), disconneting now...

(Misspelling is from the CLI.)

I've searched the web and this thread and can't come up with anything.  Anyone have any ideas?

Thanks.

Can you share the id of this device (the info on the back), please?

Does it work for usb? If yes, connect it, and run:
```
sudo hidraw-dump /dev/hidrawX
# X is the hidraw interface number reported by 'dmesg'
```

That should give me enough info to make it work.

---

### Post by dartmusic on 2012-02-06
> **falkTX said:**
> Can you share the id of this device (the info on the back), please?

Does it work for usb? If yes, connect it, and run:
```
sudo hidraw-dump /dev/hidrawX
# X is the hidraw interface number reported by 'dmesg'
```

That should give me enough info to make it work.

Thanks for the quick response!  I'm at work, but I'll do this and post the info as soon as I get home.

---

### Post by dartmusic on 2012-02-06
> **falkTX said:**
> Can you share the id of this device (the info on the back), please?

Does it work for usb? If yes, connect it, and run:
```
sudo hidraw-dump /dev/hidrawX
# X is the hidraw interface number reported by 'dmesg'
```

That should give me enough info to make it work.

OK, I'm not sure which ID you're referring to, but on the back there's an FCC ID:

AK8CECHZC2UA1

There's also an ID showing in the Qtsixa GUI:

054c:0268

I can plug it in and it is recognized, but when I play a game, the controls aren't right.  For instance, in GTA3 my character runs in circles without me touching any controls. When I try SuperTux Cart the controller is listed as available, but pressing any buttons does nothing.

I did the hidraw-dump and the terminal window showed blocks of 2 digit hex? characters that would change as I manipulated the controls.  Not sure if you wanted to see anything else?

Thanks for looking into this!

---

### Post by falkTX on 2012-02-07
> **dartmusic said:**
> I did the hidraw-dump and the terminal window showed blocks of 2 digit hex? characters that would change as I manipulated the controls.  Not sure if you wanted to see anything else?

That info is exactly what I need right now. run hidraw-dump again, give it some time (~5secs), kill it, then post here the last blocks of data.
thanks

---

### Post by dartmusic on 2012-02-07
> **falkTX said:**
> That info is exactly what I need right now. run hidraw-dump again, give it some time (~5secs), kill it, then post here the last blocks of data.
thanks

Here's the last 4 blocks:

01 00 00 00 00 00 84 82 7B 83 00 00 00 00 00 00 
00 00 00 00 00 00 00 00 00 00 00 00 00 02 EE 12 
00 00 00 00 12 FE 77 01 C0 02 07 02 1E 01 95 00 
02 01 
 
01 00 00 00 00 00 84 82 7B 83 00 00 00 00 00 00 
00 00 00 00 00 00 00 00 00 00 00 00 00 02 EE 12 
00 00 00 00 12 FE 77 01 C0 02 07 02 1E 01 95 00 
02 01 
 
01 00 00 00 00 00 84 82 7B 83 00 00 00 00 00 00 
00 00 00 00 00 00 00 00 00 00 00 00 00 02 EE 12 
00 00 00 00 12 FE 77 01 C0 02 07 02 1F 01 95 00 
02 01 
 
01 00 00 00 00 00 84 82 7B 83 00 00 00 00 00 00 
00 00 00 00 00 00 00 00 00 00 00 00 00 02 EE 12 
00 00 00 00 12 FE 77 01 C0 02 07 02 1F 01 95 00 
02 01 


Thanks again for your help!

---

### Post by xBkS on 2012-02-11
This is probably a silly question but how do I get my DS3 to do the mouse movements? I've installed Bluez, and QtSixA, configured the controller for all the PS3 actions like accelerometers etc, but I won't move the cursor? 

Secondly, how do I get the DS3 to work via Bluetooth? My laptop came with a bluetooth adapter via PCI as standard, I'm just unsure of how to set that up. Instructions weren't very clear, not enough info. 

I'm on Natty with the 2.6.39 kernel.

---

### Post by xBkS on 2012-02-12
> **xBkS said:**
> This is probably a silly question but how do I get my DS3 to do the mouse movements? I've installed Bluez, and QtSixA, configured the controller for all the PS3 actions like accelerometers etc, but I won't move the cursor? 

Secondly, how do I get the DS3 to work via Bluetooth? My laptop came with a bluetooth adapter via PCI as standard, I'm just unsure of how to set that up. Instructions weren't very clear, not enough info. 

I'm on Natty with the 2.6.39 kernel.

Anyone?

---

### Post by verbtim on 2012-02-14
About connecting via bluetooth see here: [http://ubuntuforums.org/showpost.php?p=11017352&postcount=908](http://ubuntuforums.org/showpost.php?p=11017352&postcount=908)

---

### Post by wily6 on 2012-02-25
Hey I'm having some difficulties...
running 11.04

I got everything to work, it's connected (solid light, rumbled when connected) and I have configured the profiles... but I can't seem to get any input from the controller whether it be from the mouse or the keyboard... I enabled input (mouse and keyboard) and selected a profile and even disabled joystick which it recommended (doesn't work with it on either)

jstest does show input for all the buttons and stuff I press though...

Any ideas? Any help is greatly appreciated!



figured it out =]
needed to map the buttons via the controller in the emulator

---

### Post by jorwex on 2012-02-27
anyone ever use this on an omap device?

---

### Post by abhiraj on 2012-03-01
> **falkTX said:**
> Hi, sorry for the late reply

Don't care about the ubuntu documentation, it's very old (could be a fossil by now...)
Installing 'joystick' is *not* required.

Basically, here are the steps required to use Sixaxis, in bluetooth mode:

1 - Pair the Sixaxis to your bluetooth dongle
This is made by connecting the sixaxis over USB, with the bluetooth dongle on USB too (unless it's internal, of course).
You can check if the sixaxis is properly connected with 'lsusb', and the bluetooth dongle with 'hcitool dev'.
If all is ok, run:
```
sudo sixpair
```And the sixaxis will be paired, first step completed. You can now remove the sixaxis from USB.

2 - Connect over bluetooth
Usually, if the sixaxis is paired, pressing the PS button should auto-connect the sixaxis (it has a udev rule).
If that doesnt happen, wait until it stops blinking (you can force it by using 'hcitool dc <mac>' [get <mac> using 'hcitool con']).
Then run:
```
sixad --stop
sixad --start
```And press the PS button again. It *must* connect now. If not, consider it a bug and please report back to me.

One thing worth trying is edit '/etc/default/sixad' and change debug mode to 1 (DEBUG=1), so you can get more messages out of the sixad.

You can do all this without even starting the GUI. (QtSixA).
Use the GUI if you need to change profiles, or maybe to disconnect stuff.


btw, you may ask 'how do I know when the sixaxis is connected?'.
If you ran 'sixad --start' from the terminal, a message will printed everytime a device connects (sixaxis or keypad).
Unless you changed the default profile, the sixaxis should animate the leds (and rumble if supported).


I hope this clears up something ;)

i too had the same problem, tried everything mentioned , ubuntu 10.4, i tried everything i could.!!please help me. thank you

---

### Post by jorwex on 2012-03-01
> **falkTX said:**
> Can you share the id of this device (the info on the back), please?

Does it work for usb? If yes, connect it, and run:
```
sudo hidraw-dump /dev/hidrawX
# X is the hidraw interface number reported by 'dmesg'
```

That should give me enough info to make it work.


I was able to compile sixad for the omap3 architecture for the Beagleboard!

I am having this same problem as described above. If it helps, here is the result of my hidraw-dump:

```
01 00 00 00 00 00 85 80 7B 7F 00 00 00 00 00 00 
00 00 00 00 00 00 00 00 00 00 00 00 00 02 EE 12 
00 00 00 00 12 BE 77 01 C0 FF 01 EC 01 91 01 EE 
01 9F 
 
01 00 00 00 00 00 85 80 7B 7F 00 00 00 00 00 00 
00 00 00 00 00 00 00 00 00 00 00 00 00 02 EE 12 
00 00 00 00 12 BE 77 01 C0 FF 01 EC 01 91 01 EE 
01 9F 
 
01 00 00 00 00 00 85 80 7B 7F 00 00 00 00 00 00 
00 00 00 00 00 00 00 00 00 00 00 00 00 02 EE 12 
00 00 00 00 12 BE 77 01 C0 FF 01 ED 01 91 01 EF 
01 9F 
 
01 00 00 00 00 00 85 80 7B 7F 00 00 00 00 00 00 
00 00 00 00 00 00 00 00 00 00 00 00 00 02 EE 12 
00 00 00 00 12 BE 77 01 C0 FF 01 EC 01 91 01 EE 
01 9F 
 
01 00 00 00 00 00 85 80 7B 7F 00 00 00 00 00 00 
00 00 00 00 00 00 00 00 00 00 00 00 00 02 EE 12 
00 00 00 00 12 BE 77 01 C0 FF 01 EC 01 91 01 EE 
01 9F
```

Also, here is my FCC ID (not sure if this is what you were asking for): **AK8CECHZC2**

Looking at [http://wiki.ps2dev.org/ps3:hardware:sixaxis]("http://wiki.ps2dev.org/ps3:hardware:sixaxis"), the first two bytes should be "A1 01" and the 32nd byte should indicate battery power. Possible values are 05, 02, and 01, or EE for charging.

It looks like my 31st byte corresponds to the battery status (EE), however, the following byte (12), which should represent the operating status, is NOT one of the possibilities listed on ps2dev (10, 14, or 16). 

***It appears that the whole message is shifted left by one byte, and the last byte (9F) is junk?***

Thanks for the help.

-Jordan

---

### Post by jorwex on 2012-03-12
All,

The problem was my BT dongle. If you run:
```
sudo hcidump -v
```

Your BT dongle's BT version prints out. Mine was less than 2.0, and according to pabr's [website]("http://www.pabr.org/sixlinux/sixlinux.en.html#todo"):
> A 2.0 Bluetooth adapter is recommended. Otherwise, incoming input reports may be truncated to 12 bytes.

After entering some debug print statements in sixad-sixaxis.cpp, it was determined that only 13 bytes were being captured. After obtaining a BT 2.0 dongle, all was well.

Thanks all

---

### Post by Bugy6 on 2012-03-25
Hello,

I would like to use my DS3 to play Minecraft, but at the moment I can't get any input with it.

I have connected the controller through Bluetooth and it has the one LED lit, but when I use Qjoypad to map the keyboard commands the the controller I cant get any input from the controller.

Any help would be much appreciated.

Thanks in advance.

---

### Post by xREDEMPTIONx on 2012-04-02
Have you tried using the profile creator within qtsixa? Go to settings-manage devices/profiles-input profiles-add. Create your profile here, then to apply it go to the settings-manage devices/profiles-devices tab and click on the "default" device and hit edit. Follow the wizard to apply your profile to the controller. If you try to apply the profile while the controller is connected it won't work. So make sure you're disconnected before applying and then after connecting it should work.

---

### Post by nzsmartie on 2012-04-16
Hey Guys,

This may be relevant to the development of QtSixA.
I've modified a bluetooth stack to support Playstation 3 Controllers on a 16bit MCU (PIC24FJ256DA210) using a usb bluetooth module. The controller I was testing with is in fact a Gasia GamePad, it frustrated me for a while as to why It wouldn't work. That was until a user in this thread had posted a different HID Report that enables the fake controller. I've modified my code to support this and it works. 
I went on to see If I could detect the difference between a real and a fake controller. Not too sure how well this works but when you send "0xf4, 0x42, 0x03, 0x00, 0x00" over the HID Control, A single byte will be sent back (0x00) over the HID Control. This doesn't happen when I send the rather long (0xA2,0x01,0x00, 0x00, ...) to enable the Fake controller. So I've decided that when I read a single 0x00 byte on the HID Control, I'll then send the enable gasia report, and well, it works.
I don't have a real controller on me atm to test if it works with that but I hope this might help in detecting a real to a fake controller.

Cheers
Roman

---

### Post by Smakone on 2012-05-01
anyone that figured out how to get qtsixa working outside game applications or managed to acess keyboard or mouse thru the sixaxis 

Since Ive tryed creating my own game profiles for the games I would like to play but this goes beyond my knowledge of this application.

I was thinking if it was possible to add new profiles like the implemented neverball and extreme tux racing and the other profiles in order to get these applications working within our outside the box

Most games downloaded thru the application or program center seems to be working with qtsixaxis without having to do anything else then pressing the middle button on the sixaxis and then editing some of the keybinds ingame I've succesfully played some fps game with a big N on it that worked fine untill I updated ubuntu to my current version

also mailed falk for more information on this issues

---

### Post by falkTX on 2012-05-01
It's possible to configure your own profiles using the QtSixA GUI.
Last time I tried you just used the menus to add a new profile, then set a joystick to use that profile (and re-connect).

It's been a long time since I've used QtSixA or worked on it though, I don't have the motivation to work much on it right now...
(Laptop sucks for games, I have too much work and not much free time to enjoy games)

---

### Post by Smakone on 2012-05-02
Aight....

I dont really get how to use the GUI for profiles since there's nowhere to apply them like the existing ones. Just a window for ubuntu would solve it like the existing ones for neverball and tux extreme racing. But I get that you have other things to do

The problem is not in creating profiles but actually applying them to the controller. This might work differently on different computers and versions of ubuntu. A window for an ubuntu game profile would solve this period

---

### Post by falkTX on 2012-05-02
> **Smakone said:**
> Aight....

I dont really get how to use the GUI for profiles since there's nowhere to apply them like the existing ones. Just a window for ubuntu would solve it like the existing ones for neverball and tux extreme racing. But I get that you have other things to do

The problem is not in creating profiles but actually applying them to the controller. This might work differently on different computers and versions of ubuntu. A window for an ubuntu game profile would solve this period

no, you're confusing **game profiles** with **input profiles**.
The first just creates a game config with the joystick already mapped (ie, neverball with axis and buttons pre-mapped).
To map keyboard/mouse actions the GUI is in a different place - Menu 'settings' -> 'Manage Device/Profiles'. Then on the 'Input profiles' tab, add a new one. When done, switch over to the 'Devices' tab again, and either set the default profile to the one you just created, or from a list of connected sixaxis.

---

### Post by Smakone on 2012-05-02
Ok

so this is how I set up the profile

[http://oi46.tinypic.com/14vtuzm.jpg](http://oi46.tinypic.com/14vtuzm.jpg)

and this is how to set it up

[http://oi49.tinypic.com/qrjh1h.jpg](http://oi49.tinypic.com/qrjh1h.jpg)

But as you can see I've opened up wines notepad and I cant get the sixaxis to acess the notepad 

Might have been me that misunderstood something

---

### Post by falkTX on 2012-05-02
> **Smakone said:**
> Ok

so this is how I set up the profile

[http://oi46.tinypic.com/14vtuzm.jpg](http://oi46.tinypic.com/14vtuzm.jpg)

and this is how to set it up

[http://oi49.tinypic.com/qrjh1h.jpg](http://oi49.tinypic.com/qrjh1h.jpg)

But as you can see I've opened up wines notepad and I cant get the sixaxis to acess the notepad 

Might have been me that misunderstood something

oh, are you using USB?
that won't work just like that... (the manual explains it).

but anyway, for USB, use 'sixad-raw', like:
```
sudo sixad-raw /dev/hidrawX
```
watch 'dmesg' after connecting a sixaxis to see what the 'X' value is.
in the GUI make sure you apply the profile to the 'hidraw' device.

---

### Post by Smakone on 2012-05-02
terminal:

jocke@jocke-K53SV:~$ sudo sixad-raw /dev/hidrawX
[sudo] password for jocke: 
sixad-raw::open(hidrawX) - failed to open hidraw device
jocke@jocke-K53SV:~$ 


I'm connected with bluetooth thru the usb wire. The company that sold this computer to me helped me set it up

Got full acess to the sixaxis in neverball so this shouldnt be the problem

this is where I want to add my profile

[http://oi49.tinypic.com/2zebj7l.jpg](http://oi49.tinypic.com/2zebj7l.jpg)

[http://www.youtube.com/watch?v=xtJOWL2I4sE](http://www.youtube.com/watch?v=xtJOWL2I4sE)

tryed his software but without luck

---

### Post by nlz242 on 2012-05-02
I recently installed Ubuntu 12.04 (Precise Pangolin) and i am having a hard time getting my PS3 controler to work.

I was using 11.10 before + the package from the PPA and it was working fine, so i know my hardware isn't the cause. For testing purposes i have re installed 11.10 and tested again, with succes.

Ive tried installing using 2 differents methods. After i upgraded my old 11.10 to 12.04, i noticed there were no Precise Pangolin packages in the PPA so i grabbed the source and built it.
The other method i tried was installing the Oneiric Ocelot .deb files directly (sixad first, then qtsixa).

I can pair my device without any issues.
Once paired, i run "sudo sixad --stop" then "sudo sixad --start", then i open up qtsixa (just to see what is happening) and after that i push my "PS" button. 
On my fresh install + .deb, i get constant connects/disconnects in the UI and a popup that asks if i want to grant acces to the bluetooth device. I check the "Always grant acces" box then i click "grant" but the popups comes back for the whole duration of the controler's connection process. Once the controler gives up, i stop getting the popups. My terminal with "sixad --start" doesn't detect the controler.

On my upgraded install, i get constant connects/disconnects in the UI.
My terminal with "sixad --start" doesn't detect the controler. (No popups on this one).

Any idea? I can provide more documentation (logs, screenshots, etc), just tell me what you need.

Thanks in advance and also thank you for making sixad and supporting it, i used it alot in me previous HTPC setups. :p

---

### Post by Smakone on 2012-05-02
how many controls connects when you connect it with usb?
Cos here I get two controls connected with only 1 control connected and one constantly pops and dissapears for a while but the other one stays up and the only way to properly test if its working or not is in tux racer or neverball by just pressing the middle ps3 button when ingame

If it works in those games then you should be able to play ubuntu based applications games like nexuiz by rebinding some of the keys to the "gamepad"

this is how my system reacts to pulling out the usb cable and putting it back into the controler or the other way around by pulling out the usb of the computer and back in

[http://tinypic.com/view.php?pic=2w4loy1&s=6](http://tinypic.com/view.php?pic=2w4loy1&s=6)

to play with it after you let it connect thru the bluetooth just go into game profiles and choose an option for tux or neverball by what buttons to be accesible on the sixaxis, if the sixaxis works in tux racer or neverball you pretty much have acess to the whole sixaxis and afterwards you can probably keybind it to work in games like yellowblod goes to war or nexuiz and perhaps even other games

solution: the gamepad might be conneted without sixaxis noticing it if you get the bluetooth pop, try tux racer or neverball to see if its a bug withing qtsixa or something else

the bluetooth acessing spams a bit and you might get more then 1 message

---

### Post by nlz242 on 2012-05-02
> **Smakone said:**
> how many controls connects when you connect it with usb?
Cos here I get two controls connected with only 1 control connected and one constantly pops and dissapears for a while but the other one stays up and the only way to properly test if its working or not is in tux racer or neverball by just pressing the middle ps3 button when ingame

When connecting in USB, i only get one device and it's rock solid. If i push the "PS" button, it doesnt try to connect. If i disconnect the usb cable, the controler disapears from QtSixA and when i press the "PS" button, it tries to connect. I see it appear/disappear in QtSixA, it even has time to read the properties  displayed in the "Bluetooth" frame (Address, signal quality, battery status). However, it doesnt stay long enough to be usable and then i get the "grant" popup (same as your screenshot, but less swedish, heh). The grant popup comes up about 9 times and it doesnt care if i check the "always grant" box. After the 9th time, the controler gives up and stops trying to connect, so now i see 0 controlers in QtSixA.

I never get to a point where the controler is actually usable, while using bluetooth. (I tried with neverball).

---

### Post by Smakone on 2012-05-04
Update

Handed in my computer to a computer company

The Sixaxis now works in ubuntu as a mouse and I can play texas hold em with it

Using the gnome profile and I can rebind keys to other functions but the mouse steering seems locket to the axises, using axis 1 as mouse and axis 2 as scroll

The "Gamepad" also works wireless 

Perhaps this could be integrated with further layers, I have to use the terminal to start the Gamepad In order to acess it wireless

---

### Post by andriod2388 on 2012-05-04
I'm having problems with sixad. i go to pair my ps3 controller and it rumbles and the LEDs light up but then fails and i get this in the terminal.


andy@andy-Presario-CQ56-Notebook-PC:~$ sixad --start
sixad-bin[15782]: started
sixad-bin[15782]: sixad started, press the PS button now
sixad-bin[15782]: Server mode active, will start search now
sixad-bin[15782]: One event received
sixad-bin[15782]: Will initiate Sixaxis now
sixad-bin[15782]: One event proccessed
sixad-sixaxis[15784]: started
sixad-sixaxis[15784]: Connected 'PLAYSTATION(R)3 Controller (60:38:0E:C4:A0:15)' [Battery 00]
sixad-sixaxis[15784]: Bad Sixaxis buffer (out of battery?), disconneting now...
sixad-sixaxis[15784]: Read loop was broken on the Sixaxis process
sixad-sixaxis[15784]: Closing uinput...
sixad-sixaxis[15784]: uinput_close()::ioctl(UI_DEV_DESTROY) - success!
sixad-sixaxis[15784]: uinput_close()::close(fd) - success!
sixad-sixaxis[15784]: Done

I have no idea what to do or what the problem is. thank you for any help

---

### Post by Smakone on 2012-05-05
Are you sure that the battery is loaded.

Cos thats how the sixaxis reacts on Sony playstation when the battery is depleted

The terminal also says that the battery status on your gamepad is 0 of 0

Supposed t be 0 of 5

---

### Post by andriod2388 on 2012-05-05
yes the battery is in and has a full charge. it works fine on my ps3 and the ps3 says its charged. i have tried both of my controllers and i get the same message for both. thank you for the fast response

---

### Post by Rexmundie on 2012-05-11
> **nlz242 said:**
> I recently installed Ubuntu 12.04 (Precise Pangolin) and i am having a hard time getting my PS3 controler to work.

I was using 11.10 before + the package from the PPA and it was working fine, so i know my hardware isn't the cause. For testing purposes i have re installed 11.10 and tested again, with succes.

Ive tried installing using 2 differents methods. After i upgraded my old 11.10 to 12.04, i noticed there were no Precise Pangolin packages in the PPA so i grabbed the source and built it.
The other method i tried was installing the Oneiric Ocelot .deb files directly (sixad first, then qtsixa).

I can pair my device without any issues.
Once paired, i run "sudo sixad --stop" then "sudo sixad --start", then i open up qtsixa (just to see what is happening) and after that i push my "PS" button. 
On my fresh install + .deb, i get constant connects/disconnects in the UI and a popup that asks if i want to grant acces to the bluetooth device. I check the "Always grant acces" box then i click "grant" but the popups comes back for the whole duration of the controler's connection process. Once the controler gives up, i stop getting the popups. My terminal with "sixad --start" doesn't detect the controler.

On my upgraded install, i get constant connects/disconnects in the UI.
My terminal with "sixad --start" doesn't detect the controler. (No popups on this one).

Any idea? I can provide more documentation (logs, screenshots, etc), just tell me what you need.

Thanks in advance and also thank you for making sixad and supporting it, i used it alot in me previous HTPC setups. :p

Hi there,

I've got the same problem here...:(

This is what my Hcidump gave me.... atleast till i broke it, cuase it will repeat it like 6 or 7 times before the sixasses gives up.

```
HCI sniffer - Bluetooth packet analyzer ver 2.2
device: hci0 snap_len: 1028 filter: 0xffffffff
> HCI Event: Connect Request (0x04) plen 10
    bdaddr 00:1B:FB:33:A3:47 class 0x000508 type ACL
< HCI Command: Accept Connection Request (0x01|0x0009) plen 7
    bdaddr 00:1B:FB:33:A3:47 role 0x00
    Role: Master
> HCI Event: Command Status (0x0f) plen 4
    Accept Connection Request (0x01|0x0009) status 0x00 ncmd 1
> HCI Event: Role Change (0x12) plen 8
    status 0x00 bdaddr 00:1B:FB:33:A3:47 role 0x00
    Role: Master
> HCI Event: Connect Complete (0x03) plen 11
    status 0x00 handle 11 bdaddr 00:1B:FB:33:A3:47 type ACL encrypt 0x00
< HCI Command: Read Remote Supported Features (0x01|0x001b) plen 2
    handle 11
> HCI Event: Command Status (0x0f) plen 4
    Read Remote Supported Features (0x01|0x001b) status 0x00 ncmd 1
> HCI Event: Read Remote Supported Features (0x0b) plen 11
    status 0x00 handle 11
    Features: 0xfc 0x07 0x82 0x7e 0x08 0x18 0x00 0x80
< HCI Command: Remote Name Request (0x01|0x0019) plen 10
    bdaddr 00:1B:FB:33:A3:47 mode 2 clkoffset 0x0000
> HCI Event: Command Status (0x0f) plen 4
    Remote Name Request (0x01|0x0019) status 0x00 ncmd 1
> ACL data: handle 11 flags 0x02 dlen 12
    L2CAP(s): Connect req: psm 17 scid 0x02f5
< ACL data: handle 11 flags 0x00 dlen 16
    L2CAP(s): Connect rsp: dcid 0x0040 scid 0x02f5 result 1 status 0
      Connection pending - No futher information available
< ACL data: handle 11 flags 0x00 dlen 10
    L2CAP(s): Info req: type 2
> HCI Event: Number of Completed Packets (0x13) plen 5
    handle 11 packets 2
> ACL data: handle 11 flags 0x02 dlen 16
    L2CAP(s): Info rsp: type 2 result 0
      Extended feature mask 0x0000
< ACL data: handle 11 flags 0x00 dlen 16
    L2CAP(s): Connect rsp: dcid 0x0040 scid 0x02f5 result 0 status 0
      Connection successful
< ACL data: handle 11 flags 0x00 dlen 12
    L2CAP(s): Config req: dcid 0x02f5 flags 0x00 clen 0
> HCI Event: Number of Completed Packets (0x13) plen 5
    handle 11 packets 2
> HCI Event: Remote Name Req Complete (0x07) plen 255
    status 0x00 bdaddr 00:1B:FB:33:A3:47 name 'PLAYSTATION(R)3 Controller'
> ACL data: handle 11 flags 0x02 dlen 12
    L2CAP(s): Config req: dcid 0x0040 flags 0x00 clen 0
< ACL data: handle 11 flags 0x00 dlen 18
    L2CAP(s): Config rsp: scid 0x02f5 flags 0x00 result 0 clen 4
      MTU 672 
> ACL data: handle 11 flags 0x02 dlen 14
    L2CAP(s): Config rsp: scid 0x0040 flags 0x00 result 0 clen 0
      Success
< ACL data: handle 11 flags 0x00 dlen 5
    L2CAP(d): cid 0x02f5 len 1 [psm 17]
      HIDP: Control: Virtual cable unplug
< ACL data: handle 11 flags 0x00 dlen 12
    L2CAP(s): Disconn req: dcid 0x02f5 scid 0x0040
> HCI Event: Number of Completed Packets (0x13) plen 5
    handle 11 packets 2
> HCI Event: Number of Completed Packets (0x13) plen 5
    handle 11 packets 1
> ACL data: handle 11 flags 0x02 dlen 12
    L2CAP(s): Connect req: psm 19 scid 0x02f6
< ACL data: handle 11 flags 0x00 dlen 16
    L2CAP(s): Connect rsp: dcid 0x0041 scid 0x02f6 result 1 status 2
      Connection pending - Authorization pending
> ACL data: handle 11 flags 0x02 dlen 12
    L2CAP(s): Disconn rsp: dcid 0x02f5 scid 0x0040
> HCI Event: Number of Completed Packets (0x13) plen 5
    handle 11 packets 1
< ACL data: handle 11 flags 0x00 dlen 16
    L2CAP(s): Connect rsp: dcid 0x0041 scid 0x02f6 result 0 status 0
      Connection successful
< ACL data: handle 11 flags 0x00 dlen 12
    L2CAP(s): Config req: dcid 0x02f6 flags 0x00 clen 0
> HCI Event: Number of Completed Packets (0x13) plen 5
    handle 11 packets 2
> ACL data: handle 11 flags 0x02 dlen 36
    L2CAP(s): Config req: dcid 0x0041 flags 0x00 clen 24
      QoS 0x02 (Guaranteed) 
< ACL data: handle 11 flags 0x00 dlen 18
    L2CAP(s): Config rsp: scid 0x02f6 flags 0x00 result 0 clen 4
      MTU 672 
> ACL data: handle 11 flags 0x02 dlen 14
    L2CAP(s): Config rsp: scid 0x0041 flags 0x00 result 0 clen 0
      Success
< ACL data: handle 11 flags 0x00 dlen 12
    L2CAP(s): Disconn req: dcid 0x02f6 scid 0x0041
> HCI Event: Number of Completed Packets (0x13) plen 5
    handle 11 packets 2
> ACL data: handle 11 flags 0x02 dlen 12
    L2CAP(s): Disconn rsp: dcid 0x02f6 scid 0x0041
< HCI Command: Disconnect (0x01|0x0006) plen 3
    handle 11 reason 0x13
    Reason: Remote User Terminated Connection
> HCI Event: Command Status (0x0f) plen 4
    Disconnect (0x01|0x0006) status 0x00 ncmd 1
> HCI Event: Disconn Complete (0x05) plen 4
    status 0x00 handle 11 reason 0x16
    Reason: Connection Terminated by Local Host
> HCI Event: Connect Request (0x04) plen 10
    bdaddr 00:1B:FB:33:A3:47 class 0x000508 type ACL
< HCI Command: Accept Connection Request (0x01|0x0009) plen 7
    bdaddr 00:1B:FB:33:A3:47 role 0x00
    Role: Master
> HCI Event: Command Status (0x0f) plen 4
    Accept Connection Request (0x01|0x0009) status 0x00 ncmd 1
> HCI Event: Role Change (0x12) plen 8
    status 0x00 bdaddr 00:1B:FB:33:A3:47 role 0x00
    Role: Master
> HCI Event: Connect Complete (0x03) plen 11
    status 0x00 handle 12 bdaddr 00:1B:FB:33:A3:47 type ACL encrypt 0x00
< HCI Command: Read Remote Supported Features (0x01|0x001b) plen 2
    handle 12
> HCI Event: Command Status (0x0f) plen 4
    Read Remote Supported Features (0x01|0x001b) status 0x00 ncmd 1
> HCI Event: Read Remote Supported Features (0x0b) plen 11
    status 0x00 handle 12
    Features: 0xfc 0x07 0x82 0x7e 0x08 0x18 0x00 0x80
< HCI Command: Remote Name Request (0x01|0x0019) plen 10
    bdaddr 00:1B:FB:33:A3:47 mode 2 clkoffset 0x0000
> HCI Event: Command Status (0x0f) plen 4
    Remote Name Request (0x01|0x0019) status 0x00 ncmd 1
> ACL data: handle 12 flags 0x02 dlen 12
    L2CAP(s): Connect req: psm 17 scid 0x02f7
< ACL data: handle 12 flags 0x00 dlen 16
    L2CAP(s): Connect rsp: dcid 0x0040 scid 0x02f7 result 1 status 0
      Connection pending - No futher information available
< ACL data: handle 12 flags 0x00 dlen 10
    L2CAP(s): Info req: type 2
> HCI Event: Number of Completed Packets (0x13) plen 5
    handle 12 packets 2
> ACL data: handle 12 flags 0x02 dlen 16
    L2CAP(s): Info rsp: type 2 result 0
      Extended feature mask 0x0000
< ACL data: handle 12 flags 0x00 dlen 16
    L2CAP(s): Connect rsp: dcid 0x0040 scid 0x02f7 result 0 status 0
      Connection successful
< ACL data: handle 12 flags 0x00 dlen 12
    L2CAP(s): Config req: dcid 0x02f7 flags 0x00 clen 0
> HCI Event: Number of Completed Packets (0x13) plen 5
    handle 12 packets 2
> HCI Event: Remote Name Req Complete (0x07) plen 255
    status 0x00 bdaddr 00:1B:FB:33:A3:47 name 'PLAYSTATION(R)3 Controller'
> ACL data: handle 12 flags 0x02 dlen 12
    L2CAP(s): Config req: dcid 0x0040 flags 0x00 clen 0
< ACL data: handle 12 flags 0x00 dlen 18
    L2CAP(s): Config rsp: scid 0x02f7 flags 0x00 result 0 clen 4
      MTU 672 
> ACL data: handle 12 flags 0x02 dlen 14
    L2CAP(s): Config rsp: scid 0x0040 flags 0x00 result 0 clen 0
      Success
< ACL data: handle 12 flags 0x00 dlen 5
    L2CAP(d): cid 0x02f7 len 1 [psm 17]
      HIDP: Control: Virtual cable unplug
< ACL data: handle 12 flags 0x00 dlen 12
    L2CAP(s): Disconn req: dcid 0x02f7 scid 0x0040
> HCI Event: Number of Completed Packets (0x13) plen 5
    handle 12 packets 2
> ACL data: handle 12 flags 0x02 dlen 12
    L2CAP(s): Connect req: psm 19 scid 0x02f8
< ACL data: handle 12 flags 0x00 dlen 16
    L2CAP(s): Connect rsp: dcid 0x0041 scid 0x02f8 result 1 status 2
      Connection pending - Authorization pending
> HCI Event: Number of Completed Packets (0x13) plen 5
    handle 12 packets 2
> ACL data: handle 12 flags 0x02 dlen 12
    L2CAP(s): Disconn rsp: dcid 0x02f7 scid 0x0040
< ACL data: handle 12 flags 0x00 dlen 16
    L2CAP(s): Connect rsp: dcid 0x0041 scid 0x02f8 result 3 status 0
      Connection refused - security block
> HCI Event: Number of Completed Packets (0x13) plen 5
    handle 12 packets 1
> HCI Event: Disconn Complete (0x05) plen 4
    status 0x00 handle 12 reason 0x13
    Reason: Remote User Terminated Connection
> HCI Event: Connect Request (0x04) plen 10
    bdaddr 00:1B:FB:33:A3:47 class 0x000508 type ACL
< HCI Command: Accept Connection Request (0x01|0x0009) plen 7
    bdaddr 00:1B:FB:33:A3:47 role 0x00
    Role: Master
> HCI Event: Command Status (0x0f) plen 4
    Accept Connection Request (0x01|0x0009) status 0x00 ncmd 1
> HCI Event: Role Change (0x12) plen 8
    status 0x00 bdaddr 00:1B:FB:33:A3:47 role 0x00
    Role: Master
> HCI Event: Connect Complete (0x03) plen 11
    status 0x00 handle 11 bdaddr 00:1B:FB:33:A3:47 type ACL encrypt 0x00
< HCI Command: Read Remote Supported Features (0x01|0x001b) plen 2
    handle 11
> HCI Event: Command Status (0x0f) plen 4
    Read Remote Supported Features (0x01|0x001b) status 0x00 ncmd 1
> HCI Event: Read Remote Supported Features (0x0b) plen 11
    status 0x00 handle 11
    Features: 0xfc 0x07 0x82 0x7e 0x08 0x18 0x00 0x80
< HCI Command: Remote Name Request (0x01|0x0019) plen 10
    bdaddr 00:1B:FB:33:A3:47 mode 2 clkoffset 0x0000
> HCI Event: Command Status (0x0f) plen 4
    Remote Name Request (0x01|0x0019) status 0x00 ncmd 1
> ACL data: handle 11 flags 0x02 dlen 12
    L2CAP(s): Connect req: psm 17 scid 0x02f9
< ACL data: handle 11 flags 0x00 dlen 16
    L2CAP(s): Connect rsp: dcid 0x0040 scid 0x02f9 result 1 status 0
      Connection pending - No futher information available
< ACL data: handle 11 flags 0x00 dlen 10
    L2CAP(s): Info req: type 2
> HCI Event: Number of Completed Packets (0x13) plen 5
    handle 11 packets 2
> ACL data: handle 11 flags 0x02 dlen 16
    L2CAP(s): Info rsp: type 2 result 0
      Extended feature mask 0x0000
< ACL data: handle 11 flags 0x00 dlen 16
    L2CAP(s): Connect rsp: dcid 0x0040 scid 0x02f9 result 0 status 0
      Connection successful
< ACL data: handle 11 flags 0x00 dlen 12
    L2CAP(s): Config req: dcid 0x02f9 flags 0x00 clen 0
> HCI Event: Number of Completed Packets (0x13) plen 5
    handle 11 packets 2
> HCI Event: Remote Name Req Complete (0x07) plen 255
    status 0x00 bdaddr 00:1B:FB:33:A3:47 name 'PLAYSTATION(R)3 Controller'
> ACL data: handle 11 flags 0x02 dlen 12
    L2CAP(s): Config req: dcid 0x0040 flags 0x00 clen 0
< ACL data: handle 11 flags 0x00 dlen 18
    L2CAP(s): Config rsp: scid 0x02f9 flags 0x00 result 0 clen 4
      MTU 672 
> ACL data: handle 11 flags 0x02 dlen 14
    L2CAP(s): Config rsp: scid 0x0040 flags 0x00 result 0 clen 0
      Success
< ACL data: handle 11 flags 0x00 dlen 5
    L2CAP(d): cid 0x02f9 len 1 [psm 17]
      HIDP: Control: Virtual cable unplug
< ACL data: handle 11 flags 0x00 dlen 12
    L2CAP(s): Disconn req: dcid 0x02f9 scid 0x0040
> HCI Event: Number of Completed Packets (0x13) plen 5
    handle 11 packets 2
> HCI Event: Number of Completed Packets (0x13) plen 5
    handle 11 packets 1
> ACL data: handle 11 flags 0x02 dlen 12
    L2CAP(s): Disconn rsp: dcid 0x02f9 scid 0x0040
> ACL data: handle 11 flags 0x02 dlen 12
    L2CAP(s): Connect req: psm 19 scid 0x02fa
< ACL data: handle 11 flags 0x00 dlen 16
    L2CAP(s): Connect rsp: dcid 0x0040 scid 0x02fa result 1 status 2
      Connection pending - Authorization pending
< ACL data: handle 11 flags 0x00 dlen 16
    L2CAP(s): Connect rsp: dcid 0x0040 scid 0x02fa result 3 status 0
      Connection refused - security block
> HCI Event: Number of Completed Packets (0x13) plen 5
    handle 11 packets 2
> HCI Event: Disconn Complete (0x05) plen 4
    status 0x00 handle 11 reason 0x13
    Reason: Remote User Terminated Connection

```Any idea's ?? 

Keep on trying offcourse:)

---

### Post by Smakone on 2012-05-12
Might be abit simple but if you havent paired the sixaxis with the computers bluetooth thru a usb cable and qtsixas interface menu /pair device etc

The bluetooth will keep popping and the "gamepad" will blink but never connect. Once its paired you can just start it with terminal

Might be 2 easy but sometimes the simplest solutions are the best

altho if you havent missed this part you need another solution

---

### Post by deadcatt on 2012-06-24
rannaf@crying atm :/

with QtSixA i cannot connect the controller i recognizes it with usb (but cannot move mouse or anyting, if it is suppose to work that way i dont know)

after pairing and force connect and stuff i unplugg and press ps button and it blinks for a while and brings up the adress of the controller but constantly "connects/disconnects" and is not usable and i cannot recive the battery status 

so here's what happens when i try to start PS3 controller manually

rannaf@bt:~$ sudo sixpair
Current Bluetooth master: 00:19:7e:e1:fe:ca
Setting master bd_addr to 00:19:7e:e1:fe:ca
rannaf@bt:~$ sixad --start
sixad-bin[20177]: started
sixad-bin[20177]: Can't open HIDP control socket  

Assuming that his is the main problem that QtSixA does not work

My little pee that's suppose to be a brain does not figure out how to fix this and google did not help me much

im using QtSixA 1.5.1

---

### Post by Orbital_sFear on 2012-07-08
Finding these sites got mine working.
Don't forget rfkill, it is possible that your bluetooth is simply off.

[http://wiki.xbmc.org/index.php?title=HOW-TO:Setup_PS3_BD_Remote](http://wiki.xbmc.org/index.php?title=HOW-TO:Setup_PS3_BD_Remote)
[http://kitlaan.twinaxis.com/projects/bluez-ps3remote/](http://kitlaan.twinaxis.com/projects/bluez-ps3remote/)

-Orbital

---

### Post by tarff on 2012-07-17
> **andriod2388 said:**
> I'm having problems with sixad. i go to pair my ps3 controller and it rumbles and the LEDs light up but then fails and i get this in the terminal.


andy@andy-Presario-CQ56-Notebook-PC:~$ sixad --start
sixad-bin[15782]: started
sixad-bin[15782]: sixad started, press the PS button now
sixad-bin[15782]: Server mode active, will start search now
sixad-bin[15782]: One event received
sixad-bin[15782]: Will initiate Sixaxis now
sixad-bin[15782]: One event proccessed
sixad-sixaxis[15784]: started
sixad-sixaxis[15784]: Connected 'PLAYSTATION(R)3 Controller (60:38:0E:C4:A0:15)' [Battery 00]
sixad-sixaxis[15784]: Bad Sixaxis buffer (out of battery?), disconneting now...
sixad-sixaxis[15784]: Read loop was broken on the Sixaxis process
sixad-sixaxis[15784]: Closing uinput...
sixad-sixaxis[15784]: uinput_close()::ioctl(UI_DEV_DESTROY) - success!
sixad-sixaxis[15784]: uinput_close()::close(fd) - success!
sixad-sixaxis[15784]: Done

I have no idea what to do or what the problem is. thank you for any help


I'm having the same problem. The LEDs on the sixaxis flash in succession and it rumbles but then i get the same error as andriod2388. The batteries are fully charged and the sixaxis works fine on the ps3. 

Any ideas?

Thanks

---

### Post by xREDEMPTIONx on 2012-07-29
I have been using qtsixa for a while now with much success but there are a couple things bugging me that I can't seem to figure out-

1.) When using the mouse emulation on the right analog stick the mouse is always slow and choppy and changing the axis multiplier speed has no effect whatsoever.(haven't tested on left stick yet but wouldn't use that anyway) This used to work perfectly for me but at some point something happened and now its unusable because its just too slow

2.) When using qtsixa with wine the right joystick isn't recognized properly. i.e. with San Andreas I use the "Joystick" option in qtsixa, no mouse+keys checked, and everything works perfect except I can't look up or down on the right joystick. This happens in other games as well. I don't know if this a bug in wine or if there is something else that could be tweaked in qtsixa to fix this. I was using the right joystick as mouse at one time to work around the problem but that isn't working right due to the problem I mentioned above.

Any help on these would be much appreciated!
btw I am using  qtsixa 1.5.1 from the kxstudio ppa on Ubuntu 12.04

---

### Post by BlackDynamite on 2012-09-05
I was just wondering if the project was dead or not. Because I noticed decline in numbers of Dualshock 3 in the stores, with some of them just saying that it has been discontinued.

---

### Post by falkTX on 2012-09-05
> **BlackDynamite said:**
> I was just wondering if the project was dead or not. Because I noticed decline in numbers of Dualshock 3 in the stores, with some of them just saying that it has been discontinued.

the project is not exactly dead, but it's true I've lost interest on it.
I'll do some update at a later time, very likely before the ubuntu-12.10 release.

---

### Post by MattMatan on 2012-09-15
Hello, i have problem with BT connection ubuntu-DS3.
What's the problem? Let me show You.

I have Ubuntu 12.04 LTS with Linux Kernel 3.2.0-31-generic. Version of QtSixA is 1.5.1.
That is my lsusb and lspci:
[http://wklej.org/id/829261/](http://wklej.org/id/829261/)
[http://wstaw.org/m/2012/09/15/Zrzut_ekranu_z_2012-09-15_105025.png](http://wstaw.org/m/2012/09/15/Zrzut_ekranu_z_2012-09-15_105025.png)

QtSixA found DualShock3 (via USB)
[http://wstaw.org/m/2012/09/15/Zrzut_ekranu_z_2012-09-15_105324.png](http://wstaw.org/m/2012/09/15/Zrzut_ekranu_z_2012-09-15_105324.png)

And PCSX found DS3 (via USB) as "Gasia Co., Ltd PS(R) Gamepad" ?
[http://wstaw.org/m/2012/09/15/Zrzut_ekranu_z_2012-09-15_110253.png](http://wstaw.org/m/2012/09/15/Zrzut_ekranu_z_2012-09-15_110253.png)
(but I can't set buttons configuration, buttons from DS3 are not working via USB in PCSX)

Sixpair (working)
[http://wklej.org/id/829267/](http://wklej.org/id/829267/)

Led status when connect via USB (blinking all leds [slow])

And now I'm unplug DS3 from USB and try to connect via BlueTooth.

Starting SixAD
[http://wklej.org/id/829276/](http://wklej.org/id/829276/)
[http://wstaw.org/m/2012/09/15/Zrzut_ekranu_z_2012-09-15_112004.png](http://wstaw.org/m/2012/09/15/Zrzut_ekranu_z_2012-09-15_112004.png)
I'm  pressing PSButton (all leds blinking [faster]) but a few seconds later  DS3 is turning off. I'm pressing PSButton 3 times, no response from  SixAD. Forse quit and stopping SixAD.

QtSixA found DS3 via  BlueTooth when I'm pressed PSButton but only for time when leds are  blinking. When DS3 stopped trying to connect DS3 from QtSixA gone.
[http://wstaw.org/m/2012/09/15/Zrzut_ekranu_z_2012-09-15_112606.png](http://wstaw.org/m/2012/09/15/Zrzut_ekranu_z_2012-09-15_112606.png)

Ubuntu found new Bluetooth device and asking for access permission. (when DS3 try to connect with QtSixA)
[http://wstaw.org/m/2012/09/15/Zrzut_ekranu_z_2012-09-15_112625.png](http://wstaw.org/m/2012/09/15/Zrzut_ekranu_z_2012-09-15_112625.png)
I'm pressing PSButton again and Ubuntu found DS3 (leds blinking).
[http://wstaw.org/m/2012/09/15/Zrzut_ekranu_z_2012-09-15_112657.png](http://wstaw.org/m/2012/09/15/Zrzut_ekranu_z_2012-09-15_112657.png)
Connecting...
[http://wstaw.org/m/2012/09/15/Zrzut_ekranu_z_2012-09-15_112707.png](http://wstaw.org/m/2012/09/15/Zrzut_ekranu_z_2012-09-15_112707.png)
And failed.
[http://wstaw.org/m/2012/09/15/Zrzut_ekranu_z_2012-09-15_112741.png](http://wstaw.org/m/2012/09/15/Zrzut_ekranu_z_2012-09-15_112741.png)

So  I can't connect with my DualShock3 via USB and via BlueTooth. None  emulator or QJoyPad can't find and configure device or keys via USB and  BlueTooth. DS3 can't synchronize with Ubuntu via BlueTooth. Someone have  good solve for my problem?

---

### Post by falkTX on 2012-09-15
well, you just need this:

1 - sixpair
2 - run sixad, like this:
```
sixad --stop
sixad -s
```
While you press the PS button to connect, run this on a different terminal:
```
sudo killalll -KILL bluetoothd
```
run it several times until the sixaxis connect.
(That command prevents normal bluetooth from catching events needed in sixad).

---

### Post by lozdawney on 2012-10-01
Hi falkTX :)
Just a note to say please do update qtsixa!! I love my sixaxis pad but have not been able to use it since switching to kubuntu from windows7. I love kubuntu and dont want to switch back just to be able to use my gamepad, especially since the games I use run so well in linux (via wine of course) 
If the few bugs in your driver were ironed out so it worked properly in kubuntu it would be an amazing utility! If you are willing to fix it then im willing to make a donation ;)

The trouble im having is as follows: To begin with it worked ok (connecting by command line only, but worked) but recently it wont connect at all. Ive tried a different bluetooth manager, different bluetoth dongle and even a different controller (cost me £35 for nothing DX) I tried purging all bluetooth and sixaxis software and reinstalling too, but still no joy. I know (from youtube vids) that in ubuntu (and I assume kubuntu) 10.10 this driver worked flawlessly, even connecting/auto-connecting via gui. I'm guessing updates to the linux kernel or bluetooth stack must have broken it? Either way an updated and fixed version of qtsixa/sixad would be a lifesaver for me :)
Please please please please please fix it!!

---

### Post by macau on 2012-10-03
> **nzsmartie said:**
> Hey Guys,

This may be relevant to the development of QtSixA.
I've modified a bluetooth stack to support Playstation 3 Controllers on a 16bit MCU (PIC24FJ256DA210) using a usb bluetooth module. The controller I was testing with is in fact a Gasia GamePad, it frustrated me for a while as to why It wouldn't work. That was until a user in this thread had posted a different HID Report that enables the fake controller. I've modified my code to support this and it works. 
I went on to see If I could detect the difference between a real and a fake controller. Not too sure how well this works but when you send "0xf4, 0x42, 0x03, 0x00, 0x00" over the HID Control, A single byte will be sent back (0x00) over the HID Control. This doesn't happen when I send the rather long (0xA2,0x01,0x00, 0x00, ...) to enable the Fake controller. So I've decided that when I read a single 0x00 byte on the HID Control, I'll then send the enable gasia report, and well, it works.
I don't have a real controller on me atm to test if it works with that but I hope this might help in detecting a real to a fake controller.

Cheers
Roman

Hi all! I have a fake ps3 controller (CHECHZ2U) and have common problem with blinking led's and unable wireless data transfer.
I tryed vanilla qtsixa 1.5.1-6 and patched for sdp version, but no luck.
my controller info:

> Bus 002 Device 004: ID 054c:0268 Sony Corp. Batoh Device / PlayStation 3 Controller

> [ 7030.886834] sony 0003:054C:0268.0005: Fixing up Sony Sixaxis report descriptor
[ 7030.892867] input: Gasia Co.,Ltd PS(R) Gamepad as /devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1:1.0/input/input13
[ 7030.893261] sony 0003:054C:0268.0005: input,hiddev0,hidraw3: USB HID v1.11 Joystick [Gasia Co.,Ltd PS(R) Gamepad] on usb-0000:00:1d.0-1/input0

sixad log:
> 
sixad -s
sixad-bin[1241]: started
sixad-bin[1241]: sixad started, press the PS button now
sixad-bin[1241]: Server mode active, will start search now
sixad-bin[1241]: One event received
sixad-bin[1241]: unable to connect to sdp session
sixad-bin[1241]: Creating new device using the default driver...
sixad-bin[1241]: unable to connect to sdp session
sixad-bin[1241]: HID create error 110 (Connection timed out)

Also i can post any "usb-magick" dump for devs.
Any one can help me plz?

---

### Post by macau on 2012-10-04
yeah. paired it successfully with sixad! 
default 1.5.1 version dont work with fake gasia gamepads, so i used latest git version
thanks for all devs!

---

### Post by cantruchd on 2012-10-19
> **macau said:**
> yeah. paired it successfully with sixad! 
default 1.5.1 version dont work with fake gasia gamepads, so i used latest git version
thanks for all devs!
Hi macau, could you show me where to get the latest git version?

 I have the same controller with you and after connecting it vibrate non stop. Do you have this issue?

---

### Post by macau on 2012-10-21
> **cantruchd said:**
> Hi macau, could you show me where to get the latest git version?

 I have the same controller with you and after connecting it vibrate non stop. Do you have this issue?

Hi! i use archlinux and i build package from aur. it named as qtsixa-gasia. It use official source packages with specific patches
[http://aur.archlinux.org/packages.php?ID=63437](http://aur.archlinux.org/packages.php?ID=63437)

---

### Post by cantruchd on 2012-10-23
> **macau said:**
> Hi! i use archlinux and i build package from aur. it named as qtsixa-gasia. It use official source packages with specific patches
[http://aur.archlinux.org/packages.php?ID=63437](http://aur.archlinux.org/packages.php?ID=63437)

Thanks macau, that's really helpful. I can connect the gasia to my laptop now. Now I just need to connect it to my N900 :-).

---

### Post by shohart on 2012-10-31
Hey there! 
first thank you, falkTX for your work. it is realy fantastic.

second i have two issues with qtsixa, my archlinux (gnome3) and my fake ps3 controller.
1. issue - sixad -s command provokes gnome 3.4 hanging and crash error as a result.
2. issue i cannot make my controller to assosiate with sixad via bluetooth. even with gasia hacks. maybe it is possible to modify hack somehow to make my controller as capable as gasia controllers?

here is dmesg:

```
input: SHENGHIC 2009/0708ZXW-V1Inc. PLAYSTATION(R)3Conteroller as /devices/pci0000:00/0000:00:1a.0/usb1/1-1/1-1.2/1-1.2.1/1-1.2.1.3/1-1.2.1.3:1.0/input/input19
[ 2489.861261] sony 0003:054C:0268.0004: >input,hiddev0,hidraw1: USB HID v1.11 Joystick [SHENGHIC 2009/0708ZXW-V1Inc. PLAYSTATION(R)3Conteroller] on usb-0000:00:1a.0-1.2.1.3/input0

```
and here is lsusb -vv
```
Bus 001 Device 024: ID 054c:0268 Sony Corp. Batoh Device / PlayStation 3 Controller
Couldn't open device, some information will be missing
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               2.00
  bDeviceClass            0 (Defined at Interface level)
  bDeviceSubClass         0 
  bDeviceProtocol         0 
  bMaxPacketSize0        64
  idVendor           0x054c Sony Corp.
  idProduct          0x0268 Batoh Device / PlayStation 3 Controller
  bcdDevice            1.00
  iManufacturer           1 
  iProduct                2 
  iSerial                 0 
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength           41
    bNumInterfaces          1
    bConfigurationValue     1
    iConfiguration          0 
    bmAttributes         0x80
      (Bus Powered)
    MaxPower              500mA
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       0
      bNumEndpoints           2
      bInterfaceClass         3 Human Interface Device
      bInterfaceSubClass      0 No Subclass
      bInterfaceProtocol      0 None
      iInterface              0 
        HID Device Descriptor:
          bLength                 9
          bDescriptorType        33
          bcdHID               1.11
          bCountryCode            0 Not supported
          bNumDescriptors         1
          bDescriptorType        34 Report
          wDescriptorLength     148
         Report Descriptors: 
           ** UNAVAILABLE **
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x02  EP 2 OUT
        bmAttributes            3
          Transfer Type            Interrupt
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0040  1x 64 bytes
        bInterval               1
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x81  EP 1 IN
        bmAttributes            3
          Transfer Type            Interrupt
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0040  1x 64 bytes
        bInterval               1
```

here some guy named RominuX is havin same problems with the same gamepad... but i did not found his problem solved anywhere...
> **RominuX said:**
> Thx for your reply,
a 'cat /proc/bus/input/devices' show me: Name="SHENGHIC 2009/0708ZXW-V1Inc. PLAYSTATION(R)3Conteroller"

I don't know how to code in C, but I will look the source.

Is this a problem with the internal firmware of the controller, or the bluetooth ? (if you know)


so i can provide additional info if it is required... if it is possible, i beg for help)) it is not really cool to use a wireless controller as a wired one...

---

### Post by shohart on 2012-11-21
.... anyone? at least please tell me where can i find gasia controller? preferably on ebay.... thanx

---

### Post by Mvd126 on 2012-11-23
> **cantruchd said:**
> Thanks macau, that's really helpful. I can connect the gasia to my laptop now. Now I just need to connect it to my N900 :-).
My Gasia gamepad connected to Ubuntu, but not connected with N900. I think because kernel or bluez have wrong version in maemo. Maybe you have success?

---

### Post by NewAmercnClasic on 2012-11-28
I would like to see a raring ppa for this.  Trying to get it to work now...

---

### Post by NewAmercnClasic on 2012-11-28
after trying to apt-get every possible related dependency I am still receiving this 

```
: Entering directory `/home/newamericanclassic/Downloads/qtsixa-1.5.0/utils/hcid'
cc -DHAVE_CONFIG_H -I. -I./mod   -I/usr/include/dbus-1.0 -I/usr/lib/dbus-1.0/include   -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include   -g -O2 -g -Wall -O2 -D_FORTIFY_SOURCE=2 -c common/oui.c
cc -DHAVE_CONFIG_H -I. -I./mod   -I/usr/include/dbus-1.0 -I/usr/lib/dbus-1.0/include   -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include   -g -O2 -g -Wall -O2 -D_FORTIFY_SOURCE=2 -c common/dbus.c
In file included from common/dbus.c:38:0:
/usr/include/dbus-1.0/dbus/dbus.h:29:33: fatal error: dbus/dbus-arch-deps.h: No such file or directory
compilation terminated.
make[2]: *** [common_so] Error 1
make[2]: Leaving directory `/home/newamericanclassic/Downloads/qtsixa-1.5.0/utils/hcid'
make[1]: *** [hcid_bin] Error 2
make[1]: Leaving directory `/home/newamericanclassic/Downloads/qtsixa-1.5.0/utils'
make: *** [build] Error 2

```

I tried EVERY raring package at  [http://packages.ubuntu.com/search?suite=all&section=all&arch=any&searchon=sourcenames&keywords=dbus](http://packages.ubuntu.com/search?suite=all&section=all&arch=any&searchon=sourcenames&keywords=dbus) I was still unable to get it working.

---

### Post by ntzrmtthihu777 on 2012-12-22
[FONT=courier]Ubuntu 12.04 x64
genuine PS3 sixaxis controller
qtsixa installed.
sixpair works fine.
sixadd --start appears to work but doesn't accept the ps button press. A little help please?

Ok, managed to get it to work, had to install a [patched bluez .deb.](https://iwilcox.me.uk/2012/sixaxis-ubuntu) I can now use it as a mouse and some keypresses, how would I configure it to work with an emulator, say zsnes? I tried using zsnes's built in configurer, but it does not accept my keypresses.
[/FONT]

---

### Post by quequotion on 2013-01-29
> **ntzrmtthihu777 said:**
> [FONT=courier]Ubuntu 12.04 x64
genuine PS3 sixaxis controller
qtsixa installed.
sixpair works fine.
sixadd --start appears to work but doesn't accept the ps button press. A little help please?

Ok, managed to get it to work, had to install a [patched bluez .deb.]("https://iwilcox.me.uk/2012/sixaxis-ubuntu") I can now use it as a mouse and some keypresses, how would I configure it to work with an emulator, say zsnes? I tried using zsnes's built in configurer, but it does not accept my keypresses.
[/FONT]You're going to have trouble if you want to use it as a mouse/keyboard *and* a joystick. I *recommend* that you don't.```
apt-get remove --purge xserver-xorg-input-joystick
```------------------------------
Sounds like you've gotten a couple of tutorials mixed up. The custom deb you've installed is intended to make the controllers pair over USB, then connect over bluetooth *without* sixad--using the linux kernel drivers.

Development on the kernel driver has come to a halt, approximately 2 years ago,  at this point:> The accelerometer and gyro axis do not work but can be used by reading the raw device.
The rumble feature is not supported. 
The LEDs keep blinking and do not report the chosen input device. 
Multiple gamepads on the same system have not been tested. If you want a more sensible experience, you need sixad, which is also less than ideal--it works well, and supports all the sixaxis/dualshock3 features, but requires that ordinary bluetooth be disabled. Furthermore, SUID is required to disable bluetooth and to enable sixad.
------------------------------
Lately I've had trouble with sixad not disabling bluetooth and I don't know why. It sounds like you might have the same problem.

To make sure bluetooth is disabled before starting sixad, I wrote a simple script to replace the complex sixad script:```
#!/bin/bash

    if [ -n "`pgrep sixad`" ]; then #true when sixad is running
        gksudo "sh -c '/etc/init.d/sixad stop; service bluetooth restart'"
    else
        gksudo "sh -c 'service bluetooth stop; /etc/init.d/sixad restart'"
    fi

    exit 0;
```I'm still not sure why I have to do this, but it works for me. I assigned a keyboard shortcut to run the script (Super+KP Enter) to avoid the terminal.
*UPDATE*
changed the script to use "service" for stopping and restarting bluetooth, which interacts with blueman-applet better.
also, using "restart" instead of "start" covers the case when the service is already running in a broken state.

---

### Post by installboi on 2013-02-11
Well, I have some problem with qtsixa i could not find any solution for by searching this thread.

I'm using Ubuntu 12.04.1 64-bit, a genuine PS3 Sixaxis Controller and the onboard bluetooth Controller of my Asus P8Z68-V Mainboard.

Basically the software works fine, pairing and everything without any problem. But if I use the controller as Joystick device it only works like for five second after connecting. Then it seems to be dead.

Any hints for this problem?

---

### Post by quequotion on 2013-02-16
> **installboi said:**
> Basically the software works fine, pairing and everything without any problem. But if I use the controller as Joystick device it only works like for five second after connecting. Then it seems to be dead.

Any hints for this problem?

Are you using the kernel sixaxis drivers or the sixad driver?

How did you pair?
-[I]The only way that actually works is to connect the controllers by USB cable, then run sixpair. **You cannot pair with any bluetooth utilty software; even if it says you did.** This is Sony's hardware design.
[/I]
Do you have xserver-xorg-input-joystick installed?
-*Remove it, because you probably don't need it anyway and it complicates things. See my post above for removal procedure.*

Have you checked functionality with jstest?```
jstest /dev/input/js0
```*Note, **js0** is the default name if you have no other joysticks.*

Are there any known issues with your bluetooth tranciever?
-*the bluez project seems unresponsive to support requests and bug reports (in fact, there is no place for bug reports in the bluez project), but you might find out in the IRC channel or by a lot of googling*

Especially you should test if the joystick is working with **jstest**, which will narrow down what could be wrong.

---

### Post by Aoko on 2013-03-05
Question, is it possible to get a profile or something that basically emulates the xbox360 controller for the PS3 sixaxis(similar to MotionJoy) ?

---

### Post by RabblerouserGT on 2013-03-07
[FONT=arial][SIZE=2]So I've uninstalled QTSixA via sudo apt-get remove qtsixa. And now the controller will not work in USB mode. It would work in USB apparently when I first started using QTSixA, but after I paired a controller via Bluetooth, it seems USB SIXAXIS no longer works.

I don't like pairing my controller to my computer if the PS3 is going to be the main controller-usage device.
Not to mention at least with USB, I could emulator an Xbox 360 controller with xboxdrv.

As it stands right now, I can only use the PS3 controller in Bluetooth mode, which I DO NOT like.

[SIZE=3]**[jstest-gtk screenshot]("http://i.imgur.com/FJK4r2i.png")**[/SIZE]
Everything seems frozen at these values, no matter what buttons I press. The only way to "unfreeze" them is to go to Bluetooth mode.

I just want to restore my USB functionality and say goodbye to Bluetooth forever.
[/SIZE][/FONT]

---

### Post by greniesa on 2013-03-31
> **Aoko said:**
> Question, is it possible to get a profile or something that basically emulates the xbox360 controller for the PS3 sixaxis(similar to MotionJoy) ?

I'm interest in this me too!

---

### Post by Tsume90 on 2013-04-04
I've been trying to get my sixaxis controller to connect via bluetooth for days. It's paired, when I press the PS button it shows up in the qtsixa, but eventually the lights stop blinking. I've been trying to get this to work, but I'm at a stand still. I've tried everything from different patches to reinstalling the OS altogether. Same thing every time.

Would really love some help.

---

### Post by pinkpuff on 2013-05-04
I'm trying to get my PS3 controller working on my computer by any means possible (bluetooth, USB, doesn't matter). My computer doesn't seem to recognize that I have the PS3 controller plugged in via USB. When I run sixpair it tells me "No controller found on USB busses" and when I run qtsixa it can't detect that I have anything plugged in. The lights flash on the controller when it is plugged in, but it does not otherwise acknowledge anything. I've tried it in every USB port on the computer, and other USB devices seem to work fine. Any ideas? Thanks.

---

### Post by Ranko Kohime on 2013-05-08
> **pinkpuff said:**
> I'm trying to get my PS3 controller working on my computer by any means possible (bluetooth, USB, doesn't matter). My computer doesn't seem to recognize that I have the PS3 controller plugged in via USB. When I run sixpair it tells me "No controller found on USB busses" and when I run qtsixa it can't detect that I have anything plugged in. The lights flash on the controller when it is plugged in, but it does not otherwise acknowledge anything. I've tried it in every USB port on the computer, and other USB devices seem to work fine. Any ideas? Thanks.
You have a much more serious issue then.  Run "lsusb" and see if it mentions anything about Sony (with the controller plugged in, of course).  If not, then you're looking at either a bad cable, a bad controller, or some kind of incompatibility that simply will not be resolved without serious tweaking, if at all.

---

### Post by pinkpuff on 2013-05-09
> **Ranko Kohime said:**
> You have a much more serious issue then.  Run "lsusb" and see if it mentions anything about Sony (with the controller plugged in, of course).  If not, then you're looking at either a bad cable, a bad controller, or some kind of incompatibility that simply will not be resolved without serious tweaking, if at all.

With some help from a friend I managed to get it working. It was a problem with the cord after all. When we tried hooking it up with a different cord, lsusb picked it up no problem and then I was able to get it set up with bluetooth without any issues. Thank you though.

---

### Post by pinkpuff on 2013-06-02
Ok so the controller is working but now I'm having a somewhat different issue. The select button seems to be recognized as a mouse click, even if I uncheck the "Enable Input (mouse/keyboard)" flag in the device profile in qtsixa. Unchecking "Enable buttons" seems to work except that then it doesn't acknowledge the joystick buttons either.

Is there any way to have joystick buttons enabled but none of them be recognized as mouse clicks?

---

### Post by Aze6778 on 2013-08-11
First you must pair the controller for me is much easier via command line 1.sixpair should give a message like this: 
[COLOR=#000000]Current Bluetooth master: 00:09:dd:50:5a:a4[/COLOR]
[COLOR=#000000]Setting master bd_addr to 00:09:dd:50:5a:a4[/COLOR] 

then enter sixad --start that is going to give this: sixad-bin[22374]: startedsixad-bin[22374]: sixad started, press the PS button now then you just have to press the ps button and wait for the controller to vibrate

---

### Post by funkbuqet on 2013-08-11
FalkTX, thanks for all of your work on this. 

I have used your program on my ubuntu machine for quite a while. I recently have been trying to get it up and running on my raspberry pi (Debian Wheezy based PiMAME image). I got sixad compiled and installed fine and the controller connects and is recognized as a joystick. The problem is that the emulators that I have tried (AdvanceMAME and MAME4all) do not recognize the cross, circle, or triangle buttons as inputs. When i try jstest or hidraw-dump the buttons clearly are working. 

My solution was to create a /var/lib/sixad/profiles/default config file and specify that i wanted to use input instead of joystick mode. i then specified all of the keypresses i wanted to use for input. But everytime i connect it is still seen as a joystick. It is like sixad is not reading my config files and only using the internal defaults. i tried copying my default file to a mac address specific one and it did not help. i have inluded the contents of my default config below. 

```
# ##########################
# sixad configuration file #
########################## #

# Features
enable_leds 1
enable_joystick 0
enable_input 1
enable_remote 0
enable_rumble 0
enable_timeout 1

# LED
led_n_auto 1
led_n_number 1
led_anim 1

# Joystick
enable_buttons 1
enable_sbuttons 1
enable_axis 1
enable_accel 0
enable_accon 0
enable_speed 0
enable_pos 0

# Input - None
key_select 25
key_l3 6
key_r3 15
key_start 28
key_up 103
key_right 106
key_down 108
key_left 105
key_l2 47
key_r2 46
key_l1 45
key_r1 44
key_tri 42
key_cir 56
key_squ 57
key_cro 29
key_ps 1
axis_left_type 2
axis_left_up 18
axis_left_right 33
axis_left_down 32
axis_left_left 31
axis_right_type 2
axis_right_up 23
axis_right_right 38
axis_right_down 37
axis_right_left 36
axis_speed 6
use_lr3 0

# Remote
remote_numberic 1
remote_dvd 1
remote_directional 1
remote_multimedia 1

# Rumble
old_rumble_mode 0

# Timeout
timeout_mins 30

# Misc
out_of_reach_disconnects 0


```

Also, when i run sixad in the for ground I get the following message:
```
pi@raspberrypi ~ $ sudo sixad --start
sixad-bin[2494]: started
sixad-bin[2494]: sixad started, press the PS button now
sixad-bin[2494]: unable to connect to sdp session
sixad-bin[2494]: Connected Sony Computer Entertainment Wireless Controller (60:38:0E:75:A1:D4)
```

I do not know is the sdp session error is causing sixad to use it's internal defaults or if this is unrelated.

Sorry i had to post this in the Ubunut forums, but this was the only place to get help mentioned on your website and I have not been able to find a solution on the rPi forums or Google. Thanks for any help you can provide.

---

### Post by Spartoi on 2013-08-17
Can someone explain to me how to use profiles? I just want to use my DS3 as a controller for emulators/PCSX & PCSX2.

---

### Post by Bolli1983 on 2013-10-25
Hi!

I, too have a little problem getting the controller to work via bt and i fear that the line marked red could indicate a problem? :> i am a linux noob though, so i'm hoping to find some help here. Thanks in advance!

root@xbmc:/home/bolli# sixad --stop
root@xbmc:/home/bolli# sixad --start
[COLOR=#ff0000]D-Bus setup failed: Name already in use[/COLOR]
sixad-bin[2310]: started
sixad-bin[2310]: sixad started, press the PS button now
sixad-sixaxis[2312]: started
sixad-sixaxis[2312]: Connected 'PLAYSTATION(R)3 Controller (04:76:6E:46:81:06)' [Battery 00]
sixad-sixaxis[2312]: Bad Sixaxis buffer (out of battery?), disconneting now...
sixad-sixaxis[2312]: Force disconnect of "04:76:6E:46:81:06"



Edit: Problem solved, i bought a new bluetooth adapter today and now everything works like a charm.

---

### Post by jvalen on 2013-12-28
Could you tell us wich one (brand, model) did you get? 

I just bought today an unbranded bluetooth dongle and I cannot make it work. The regular bluetooth features works great and I can pair the ps3 gamepad but cannot connect it by "sixad", the controller lights dont stop blinking (btw: I know how "qtsixa" works because I can use it perfectly in my laptop, what I cant do is use it in my desktop pc).

Thanks!

---

### Post by danramos on 2014-01-10
Will there be support for the PS3 Sony Navigation Controller (CECH-ZCS1U)?

Here's what dmesg has to say when I plug it in:
[292066.016653] input: Sony Navigation Controller as /devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.3/2-1.3.4/2-1.3.4:1.0/input/input55
[292066.019948] sony 0003:054C:042F.000E: input,hiddev0,hidraw5: USB HID v1.11 Joystick [Sony Navigation Controller] on usb-0000:00:1d.0-1.3.4/input0
[292243.035187] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[292243.035192] Bluetooth: BNEP filters: protocol multicast
[292243.035200] Bluetooth: BNEP socket layer initialized
[292245.138818] Bluetooth: HIDP (Human Interface Emulation) ver 1.2
[292245.138829] Bluetooth: HIDP socket layer initialized
[292266.279897] usb 2-1.3.4: USB disconnect, device number 84
[292289.766285] usb 2-1.3.4: new full-speed USB device number 85 using ehci-pci
[292289.974543] usb 2-1.3.4: New USB device found, idVendor=054c, idProduct=042f
[292289.974548] usb 2-1.3.4: New USB device strings: Mfr=1, Product=2, SerialNumber=0
[292289.974551] usb 2-1.3.4: Product: Navigation Controller
[292289.974553] usb 2-1.3.4: Manufacturer: Sony
[292290.009369] sony 0003:054C:042F.000F: Fixing up Sony Sixaxis report descriptor
[292290.052499] input: Sony Navigation Controller as /devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.3/2-1.3.4/2-1.3.4:1.0/input/input56
[292290.052795] sony 0003:054C:042F.000F: input,hiddev0,hidraw5: USB HID v1.11 Joystick [Sony Navigation Controller] on usb-0000:00:1d.0-1.3.4/input0

sixpair nor qtsixa are working at all with it near as I can tell, although "sixad-raw /dev/hidraw5" seems to read it fine:
root@shockwave:~# sixad-raw /dev/hidraw5
sixad-raw[2750]: Connected 'PLAYSTATION(R)3 Controller (hidraw)' [Battery EE]
sixad-raw[2750]: Notice: non-standard Sixaxis buffer size (49)
^C

Let me know if there's anything I can do to help.

---

### Post by nadia-xy on 2014-05-01
If anyone is interested I've built the sixaxis pairing patch for bluez on trusty and uploaded it to a ppa at [https://launchpad.net/~nadia-xy/+archive/ppa](https://launchpad.net/~nadia-xy/+archive/ppa). This patch doesn't require qtsixa installing and just uses the normal kernel driver (which supports everything but the LED's at this point I believe). It should let you use other bluetooth devices at the same time too rather than the adapter being dedicated to sixaxis and dualshock 3. Just install the new bluez and connect your controller and it should pair automatically.

---

### Post by danramos on 2014-05-04
> **nadia-xy said:**
> If anyone is interested I've built the sixaxis pairing patch for bluez on trusty and uploaded it to a ppa at [https://launchpad.net/~nadia-xy/+archive/ppa](https://launchpad.net/~nadia-xy/+archive/ppa). This patch doesn't require qtsixa installing and just uses the normal kernel driver (which supports everything but the LED's at this point I believe). It should let you use other bluetooth devices at the same time too rather than the adapter being dedicated to sixaxis and dualshock 3. Just install the new bluez and connect your controller and it should pair automatically.

Does this solve the problem of getting the PS3 Sony Navigation Controller (CECH-ZCS1U) to pair?  If it's a bluez patch, how do I get the USB pairing to happen before it will work over bluetooth since sixpair refuses to recognize this device?

---

### Post by juanmanuelagueda on 2014-05-08
> **nadia-xy said:**
> If anyone is interested I've built the sixaxis pairing patch for bluez on trusty and uploaded it to a ppa at [https://launchpad.net/~nadia-xy/+archive/ppa](https://launchpad.net/~nadia-xy/+archive/ppa). This patch doesn't require qtsixa installing and just uses the normal kernel driver (which supports everything but the LED's at this point I believe). It should let you use other bluetooth devices at the same time too rather than the adapter being dedicated to sixaxis and dualshock 3. Just install the new bluez and connect your controller and it should pair automatically.



Hi! Nadia-xy!

I am highly interested :D I have joust bought a fake ps3 controller, and I am able to use it with my Nexus 7 using sixaxis controller without problem. Now, I am trying to use it with in my Ubuntu trusty and I am finding some issues. It is working out of the box when I use the usb cable, but when I try to synchronize the gamepad via bluetooth the lights always keep on blinking. I have tried the PPA and the guide at the beginning of this thread without luck. I have also tried your PPA, but bluetooth seems to stop working: the app indicator disappears and I am not able to re-enable the bluetooth service until I purge your ppa :(. I guess I am doing something wrong, but now I am completely lost.

Any help would be appreciated.

Thanks!

---

### Post by nadia-xy on 2014-05-14
> **juanmanuelagueda said:**
> Hi! Nadia-xy!

I am highly interested :D I have joust bought a fake ps3 controller, and I am able to use it with my Nexus 7 using sixaxis controller without problem. Now, I am trying to use it with in my Ubuntu trusty and I am finding some issues. It is working out of the box when I use the usb cable, but when I try to synchronize the gamepad via bluetooth the lights always keep on blinking. I have tried the PPA and the guide at the beginning of this thread without luck. I have also tried your PPA, but bluetooth seems to stop working: the app indicator disappears and I am not able to re-enable the bluetooth service until I purge your ppa :(. I guess I am doing something wrong, but now I am completely lost.

Any help would be appreciated.

Thanks!

I've not tested with any fake controllers, I only have an official sixaxis and ds3, so it could just be that the patch doesn't support the unofficial ones correctly or the kernel module itself doesn't. This is just a port of the patch found at [https://iwilcox.me.uk/2012/sixaxis-ubuntu](https://iwilcox.me.uk/2012/sixaxis-ubuntu) to the version of bluez trusty includes and although I can package it, I might not be able to debug it. Can you post the output of lsusb and dmesg with your controller connected via usb and the output of dmesg when you try and pair over bluetooth (with the patched bluez installed)? The lights flashing is normal, the kernel version that ubuntu ships with doesn't handle the LED's correctly yet, you would need to install mainline for those to work but it shouldn't break bluetooth.

Regarding the navigation controller, again I have no idea as I don't have one and didn't write the patch, I just applied it against the current ubuntu bluez sources. This should all hopefully resolved when ubuntu moves to Bluez 5 and sony peripheral support is built in by default.

---

### Post by mthoring on 2015-01-10
I've forked the qtsixa repository and hacked the code a bit to make sixad work with original and fake GASIA controllers at the same time (tested with one original and one fake).
I'm using it for RetroPie. Posting it here in case anyone is interested.

[https://github.com/supertypo/qtsixa.git](https://github.com/supertypo/qtsixa.git)

---

### Post by abunene2 on 2015-02-01
hi i tried to use my ps3 controller on my ibm thinkpad t43 notebook build in bluetooth and this is what i get

```

t43:~$ sudo sixpair
Current Bluetooth master: 34:31:11:51:65:78
Setting master bd_addr to 00:14:a4:df:86:09
t43:~$  sixad --start
D-Bus setup failed: Name already in use
sixad-bin[24397]: started
sixad-bin[24397]: sixad started, press the PS button now
sixad-bin[24397]: sdp_read_rsp: Client timed out


sixad-bin[24397]: sdp_service_search_attr_req: Unexpected end of packet
sixad-bin[24397]: sdp_read_rsp: Client timed out


sixad-bin[24397]: sdp_service_search_attr_req: Unexpected end of packet
sixad-bin[24397]: unable to get device information
sixad-bin[24397]: unable to connect to sdp session
sixad-bin[24397]: HID create error 115 (Operation now in progress)

```

any idea how to make it work?

---

### Post by laurence2 on 2015-02-04
> **nadia-xy said:**
> If anyone is interested I've built the sixaxis pairing patch for bluez on trusty and uploaded it to a ppa at [https://launchpad.net/~nadia-xy/+archive/ppa](https://launchpad.net/~nadia-xy/+archive/ppa). This patch doesn't require qtsixa installing and just uses the normal kernel driver (which supports everything but the LED's at this point I believe). It should let you use other bluetooth devices at the same time too rather than the adapter being dedicated to sixaxis and dualshock 3. Just install the new bluez and connect your controller and it should pair automatically.
Nadia-xy

so after installing your repository and re-installing bluez where do i go from there to get the controller to pair and function?

Do I need the sixad repository atall?

I've tried searching for a bluetooth device after installing your repository bluez version but it finds nothing....

---

### Post by laurence2 on 2015-02-04
Hi


I'm having some issues getting my sixaxis controller working with ubuntu trusty 14.04.


I've installed sixad from the ppa


the sixpair part seems to work, but after pressing the PS button I never get the expected vibrate, the lights eventually stop flashing and I have to kill the sixad


```
loz@gravity:~$ sudo sixpair
Current Bluetooth master: 00:19:15:60:0e:d9
Setting master bd_addr to 00:19:15:60:0e:d9
loz@gravity:~$ sixad --start
sixad-bin[20990]: started
sixad-bin[20990]: sixad started, press the PS button now
sixad-bin[20990]: Done
loz@gravity:~$
```


My Bluetooth is enables and my bluetooth adapter comes up as "Broadcom Corp. Bluetooth 2.0+eDR dongle" in lsusb?


Anyone got any ideas that might help me?

---

### Post by j00hn on 2015-02-26
hello :)

is there a way to control rumble/vibration with a python script  ? (currently i'm using pygame to retrieve the control input)

Thanks

---

### Post by lollo78 on 2015-03-31
> **mthoring said:**
> I've forked the qtsixa repository and hacked the code a bit to make sixad work with original and fake GASIA controllers at the same time (tested with one original and one fake).
I'm using it for RetroPie. Posting it here in case anyone is interested.

[https://github.com/supertypo/qtsixa.git](https://github.com/supertypo/qtsixa.git)

@mthoring
Hi, I send you a PM. Please let me know. thx a lot.
;)

---

### Post by swimmer1 on 2015-04-03
yup, it works for me with fake controller, however only with 1, second controller will not connect :mad:

---

### Post by SA6 on 2015-05-01
I'm trying to use the fake controller too. Here's my dmesg after plugging in my controller. 

```
[ 6828.060162] usb 3-10.4: new full-speed USB device number 14 using xhci_hcd
[ 6828.165730] usb 3-10.4: New USB device found, idVendor=054c, idProduct=0268
[ 6828.165750] usb 3-10.4: New USB device strings: Mfr=1, Product=2, SerialNumber=0
[ 6828.165752] usb 3-10.4: Product: PS(R) Gamepad
[ 6828.165753] usb 3-10.4: Manufacturer: Gasia Co.,Ltd
[ 6828.167045] sony 0003:054C:0268.0008: Fixing up Sony Sixaxis report descriptor
[ 6828.168056] input: Gasia Co.,Ltd PS(R) Gamepad as /devices/pci0000:00/0000:00:14.0/usb3/3-10/3-10.4/3-10.4:1.0/0003:054C:0268.0008/input/input24
[ 6828.168330] sony 0003:054C:0268.0008: input,hiddev0,hidraw2: USB HID v1.11 Joystick [Gasia Co.,Ltd PS(R) Gamepad] on usb-0000:00:14.0-10.4/input0

```

Now when I start sixad I'm unable to connect to the controller: 

```
sixad --start
sixad-bin[10658]: started
sixad-bin[10658]: sixad started, press the PS button now
sixad-bin[10658]: unable to connect to sdp session
sixad-bin[10658]: unable to connect to sdp session
sixad-bin[10658]: HID create error 110 (Connection timed out)

```

I tried using mthoring's fork but that didn't work either. 
Any ideas?

---

### Post by maslourenco on 2015-06-27
I just make:
```
[FONT=monospace][COLOR=#000000]sudo apt-get install sixad-gasia[/COLOR][/FONT]
```
```
sudo sixad --stop
sudo sixad --start

```
And it work,
```

[FONT=monospace][COLOR=#000000]sixad-sixaxis[3268]: started [/COLOR]
sixad-sixaxis[3268]: Connected 'PLAYSTATION(R)3 Controller (00:26:5C:03:E2:EA)' [Battery 05] 
sixad-bin[2906]: Done[/FONT]

```

I hope it works for you! :)

---

### Post by nadia-xy on 2015-06-30
> **laurence2 said:**
> Hi


I'm having some issues getting my sixaxis controller working with ubuntu trusty 14.04.


I've installed sixad from the ppa


the sixpair part seems to work, but after pressing the PS button I never get the expected vibrate, the lights eventually stop flashing and I have to kill the sixad


My Bluetooth is enables and my bluetooth adapter comes up as "Broadcom Corp. Bluetooth 2.0+eDR dongle" in lsusb?


Anyone got any ideas that might help me?

I've never been able to successfully pair with a Bluetooth 2.0 dongle, it has always had to be 2.1 or higher. This is probably why the patched Bluez ppa didn't work for you either, you probably need a dongle that supports at least 2.1. Sorry for the time it took to reply, I don't visit these forums that often.

---

### Post by MMihon on 2016-05-02
In Ubuntu 16.04 not connect :(

---

### Post by rolfUser on 2016-09-14
[http://qtsixa.sourceforge.net/](http://qtsixa.sourceforge.net/)

Using Ubuntu 16.04...
followed directions for installation, but was wondering if anyone can have a look at what was outputted. I don't understand what went wrong. 

```

carlos@F3D15AA:~$ sudo add-apt-repository ppa:falk-t-j/qtsixa
[sudo] password for carlos: 
 Packages for QtSixA and sixad software


 More info: https://launchpad.net/~falk-t-j/+archive/ubuntu/qtsixa
Press [ENTER] to continue or ctrl-c to cancel adding it


gpg: keyring `/tmp/tmp0rzsj3ov/secring.gpg' created
gpg: keyring `/tmp/tmp0rzsj3ov/pubring.gpg' created
gpg: requesting key 736E4F0B from hkp server keyserver.ubuntu.com
gpg: /tmp/tmp0rzsj3ov/trustdb.gpg: trustdb created
gpg: key 736E4F0B: public key "Launchpad PPA for falktx" imported
gpg: Total number processed: 1
gpg:               imported: 1  (RSA: 1)
OK


carlos@F3D15AA:~$ sudo apt-get update
Hit:1 http://us.archive.ubuntu.com/ubuntu xenial InRelease
Ign:2 http://dl.google.com/linux/chrome/deb stable InRelease                   
Get:3 http://us.archive.ubuntu.com/ubuntu xenial-updates InRelease [95.7 kB]   
Get:4 http://dl.google.com/linux/chrome/deb stable Release [1,189 B]           
Ign:5 http://ppa.launchpad.net/falk-t-j/qtsixa/ubuntu xenial InRelease         
Get:6 http://security.ubuntu.com/ubuntu xenial-security InRelease [94.5 kB]    
Get:7 http://dl.google.com/linux/chrome/deb stable Release.gpg [916 B]         
Hit:8 http://ppa.launchpad.net/fossfreedom/rhythmbox/ubuntu xenial InRelease   
Hit:9 http://us.archive.ubuntu.com/ubuntu xenial-backports InRelease           
Hit:10 http://ppa.launchpad.net/libreoffice/ppa/ubuntu xenial InRelease        
Get:11 http://ppa.launchpad.net/lucioc/sayonara/ubuntu xenial InRelease [17.5 kB]
Hit:12 http://ppa.launchpad.net/maateen/battery-monitor/ubuntu xenial InRelease
Hit:13 http://ppa.launchpad.net/nicola-onorata/desktop/ubuntu xenial InRelease
Hit:14 http://ppa.launchpad.net/webupd8team/sublime-text-3/ubuntu xenial InRelease
Get:15 http://dl.google.com/linux/chrome/deb stable/main amd64 Packages [1,373 B]
Ign:16 http://ppa.launchpad.net/falk-t-j/qtsixa/ubuntu xenial Release          
Ign:17 http://ppa.launchpad.net/falk-t-j/qtsixa/ubuntu xenial/main amd64 Packages
Ign:18 http://ppa.launchpad.net/falk-t-j/qtsixa/ubuntu xenial/main i386 Packages
Get:19 http://us.archive.ubuntu.com/ubuntu xenial-updates/main Sources [187 kB]
Ign:20 http://ppa.launchpad.net/falk-t-j/qtsixa/ubuntu xenial/main all Packages
Ign:21 http://ppa.launchpad.net/falk-t-j/qtsixa/ubuntu xenial/main Translation-en_US
Ign:22 http://ppa.launchpad.net/falk-t-j/qtsixa/ubuntu xenial/main Translation-en
Get:23 http://security.ubuntu.com/ubuntu xenial-security/main Sources [38.7 kB]
Get:24 http://us.archive.ubuntu.com/ubuntu xenial-updates/universe Sources [93.3 kB]
Ign:25 http://ppa.launchpad.net/falk-t-j/qtsixa/ubuntu xenial/main amd64 DEP-11 Metadata
Ign:26 http://ppa.launchpad.net/falk-t-j/qtsixa/ubuntu xenial/main DEP-11 64x64 Icons
Get:27 http://us.archive.ubuntu.com/ubuntu xenial-updates/multiverse Sources [3,220 B]
Get:28 http://us.archive.ubuntu.com/ubuntu xenial-updates/main amd64 Packages [383 kB]
Get:29 http://security.ubuntu.com/ubuntu xenial-security/universe Sources [9,340 B]
Get:30 http://security.ubuntu.com/ubuntu xenial-security/multiverse Sources [728 B]
Get:31 http://security.ubuntu.com/ubuntu xenial-security/main amd64 Packages [138 kB]
Ign:17 http://ppa.launchpad.net/falk-t-j/qtsixa/ubuntu xenial/main amd64 Packages
Ign:18 http://ppa.launchpad.net/falk-t-j/qtsixa/ubuntu xenial/main i386 Packages
Get:32 http://security.ubuntu.com/ubuntu xenial-security/main i386 Packages [134 kB]
Ign:20 http://ppa.launchpad.net/falk-t-j/qtsixa/ubuntu xenial/main all Packages
Ign:21 http://ppa.launchpad.net/falk-t-j/qtsixa/ubuntu xenial/main Translation-en_US
Get:33 http://security.ubuntu.com/ubuntu xenial-security/main amd64 DEP-11 Metadata [80.6 kB]
Ign:22 http://ppa.launchpad.net/falk-t-j/qtsixa/ubuntu xenial/main Translation-en
Get:34 http://security.ubuntu.com/ubuntu xenial-security/main DEP-11 64x64 Icons [62.9 kB]
Ign:25 http://ppa.launchpad.net/falk-t-j/qtsixa/ubuntu xenial/main amd64 DEP-11 Metadata
Get:35 http://security.ubuntu.com/ubuntu xenial-security/universe amd64 Packages [41.5 kB]
Get:36 http://security.ubuntu.com/ubuntu xenial-security/universe i386 Packages [41.4 kB]
Get:37 http://ppa.launchpad.net/lucioc/sayonara/ubuntu xenial/main amd64 Packages [644 B]
Get:38 http://ppa.launchpad.net/lucioc/sayonara/ubuntu xenial/main i386 Packages [648 B]
Ign:26 http://ppa.launchpad.net/falk-t-j/qtsixa/ubuntu xenial/main DEP-11 64x64 Icons
Ign:17 http://ppa.launchpad.net/falk-t-j/qtsixa/ubuntu xenial/main amd64 Packages
Ign:18 http://ppa.launchpad.net/falk-t-j/qtsixa/ubuntu xenial/main i386 Packages
Ign:20 http://ppa.launchpad.net/falk-t-j/qtsixa/ubuntu xenial/main all Packages
Ign:21 http://ppa.launchpad.net/falk-t-j/qtsixa/ubuntu xenial/main Translation-en_US
Get:39 http://us.archive.ubuntu.com/ubuntu xenial-updates/main i386 Packages [378 kB]
Ign:22 http://ppa.launchpad.net/falk-t-j/qtsixa/ubuntu xenial/main Translation-en
Get:40 http://security.ubuntu.com/ubuntu xenial-security/universe amd64 DEP-11 Metadata [2,266 B]
Get:41 http://security.ubuntu.com/ubuntu xenial-security/multiverse amd64 Packages [1,176 B]
Get:42 http://security.ubuntu.com/ubuntu xenial-security/multiverse i386 Packages [1,340 B]
Get:43 http://security.ubuntu.com/ubuntu xenial-security/multiverse amd64 DEP-11 Metadata [201 B]
Ign:25 http://ppa.launchpad.net/falk-t-j/qtsixa/ubuntu xenial/main amd64 DEP-11 Metadata
Ign:26 http://ppa.launchpad.net/falk-t-j/qtsixa/ubuntu xenial/main DEP-11 64x64 Icons
Ign:17 http://ppa.launchpad.net/falk-t-j/qtsixa/ubuntu xenial/main amd64 Packages
Ign:18 http://ppa.launchpad.net/falk-t-j/qtsixa/ubuntu xenial/main i386 Packages
Ign:20 http://ppa.launchpad.net/falk-t-j/qtsixa/ubuntu xenial/main all Packages
Ign:21 http://ppa.launchpad.net/falk-t-j/qtsixa/ubuntu xenial/main Translation-en_US
Ign:22 http://ppa.launchpad.net/falk-t-j/qtsixa/ubuntu xenial/main Translation-en
Ign:25 http://ppa.launchpad.net/falk-t-j/qtsixa/ubuntu xenial/main amd64 DEP-11 Metadata
Ign:26 http://ppa.launchpad.net/falk-t-j/qtsixa/ubuntu xenial/main DEP-11 64x64 Icons
Ign:17 http://ppa.launchpad.net/falk-t-j/qtsixa/ubuntu xenial/main amd64 Packages
Ign:18 http://ppa.launchpad.net/falk-t-j/qtsixa/ubuntu xenial/main i386 Packages
Get:44 http://us.archive.ubuntu.com/ubuntu xenial-updates/universe amd64 Packages [325 kB]
Ign:20 http://ppa.launchpad.net/falk-t-j/qtsixa/ubuntu xenial/main all Packages
Ign:21 http://ppa.launchpad.net/falk-t-j/qtsixa/ubuntu xenial/main Translation-en_US
Ign:22 http://ppa.launchpad.net/falk-t-j/qtsixa/ubuntu xenial/main Translation-en
Ign:25 http://ppa.launchpad.net/falk-t-j/qtsixa/ubuntu xenial/main amd64 DEP-11 Metadata
Ign:26 http://ppa.launchpad.net/falk-t-j/qtsixa/ubuntu xenial/main DEP-11 64x64 Icons
Err:17 http://ppa.launchpad.net/falk-t-j/qtsixa/ubuntu xenial/main amd64 Packages
  404  Not Found
Get:45 http://us.archive.ubuntu.com/ubuntu xenial-updates/universe i386 Packages [321 kB]
Ign:18 http://ppa.launchpad.net/falk-t-j/qtsixa/ubuntu xenial/main i386 Packages
Ign:20 http://ppa.launchpad.net/falk-t-j/qtsixa/ubuntu xenial/main all Packages
Ign:21 http://ppa.launchpad.net/falk-t-j/qtsixa/ubuntu xenial/main Translation-en_US
Ign:22 http://ppa.launchpad.net/falk-t-j/qtsixa/ubuntu xenial/main Translation-en
Ign:25 http://ppa.launchpad.net/falk-t-j/qtsixa/ubuntu xenial/main amd64 DEP-11 Metadata
Get:46 http://us.archive.ubuntu.com/ubuntu xenial-updates/multiverse amd64 Packages [5,492 B]
Get:47 http://us.archive.ubuntu.com/ubuntu xenial-updates/multiverse i386 Packages [4,280 B]
Ign:26 http://ppa.launchpad.net/falk-t-j/qtsixa/ubuntu xenial/main DEP-11 64x64 Icons
Fetched 2,465 kB in 12s (205 kB/s)                                             
Reading package lists... Done
W: The repository 'http://ppa.launchpad.net/falk-t-j/qtsixa/ubuntu xenial Release' does not have a Release file.
N: Data from such a repository can't be authenticated and is therefore potentially dangerous to use.
N: See apt-secure(8) manpage for repository creation and user configuration details.
E: Failed to fetch http://ppa.launchpad.net/falk-t-j/qtsixa/ubuntu/dists/xenial/main/binary-amd64/Packages  404  Not Found
E: Some index files failed to download. They have been ignored, or old ones used instead.
carlos@F3D15AA:~$ sudo apt-get install qtsixa
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package qtsixa

```

---

### Post by howefield on 2016-09-14
> **rolfUser said:**
> followed directions for installation, but was wondering if anyone can have a look at what was outputted. I don't understand what went wrong.

It means that there is no xenial option for that repository resulting in you querying a non existent source. Looks like it stops at Vivid (15.04).

---

