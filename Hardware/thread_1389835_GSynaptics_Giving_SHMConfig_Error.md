---
title: "GSynaptics Giving SHMConfig Error"
date: 2010-01-24
forum: Hardware
---

### Post by bluefoxox on 2010-01-24
Hey All,

My touch pad works but as I type the cursor jumps to where the mouse pointer is.  I have tried many threads to have this resolved.  Obviously so far nothing has worked.  When I use the command sudo tpconfig I am informed that a synaptics touchpad with firmware ver 8.96 is present.  When I try to use sudo gsynaptics  an Error stating "GSynaptics could not initialize.  You have to set SHMConfig 'true' in xorg.conf or XF86Config to use GSynaptics".  There is no touchpad tab in the mouse preferences via System>Preferences>Mouse either.  I am sure the problems are somehow related. lsmod |grep evdev renders no output although I have placed evdev into the file /etc/modules.  My install is Ubuntu 9.10 64 bit (from a Wubi installation).  Below is my /etc/X11/xorg.conf file contents.

Section "Screen"
    Identifier    "Default Screen"
    DefaultDepth    24
EndSection

Section "Module"
    Load    "glx"
    Load    "synaptics"
EndSection

Section "Device"
    Identifier    "Default Device"
    Driver    "fglrx"
EndSection

Section "InputDevice"
    Identifier    "Configured Mouse"
    Driver        "mouse"
    Option        "CorePointer"
    Option        "Device"        "/dev/input/mice"
    Option        "Protocol"        "ImPS/2"
    Option        "Emulate3Buttons"    "true"
    Option        "ZAxisMapping"        "4 5"
EndSection

Section "InputDevice"
    Identifier    "Synaptics Touchpad"
    Driver        "synaptics"
    Option        "SendCoreEvents"    "true"
    Option        "Device"        "/dev/psaux"
    Option        "Protocol"        "auto-dev"
    Option  "LeftEdge"              "120"
    Option  "RightEdge"             "830"
    Option  "TopEdge"               "120"
    Option  "BottomEdge"            "650"
    Option  "FingerLow"             "14"
    Option  "FingerHigh"            "15"
    Option  "MaxTapTime"            "0"
    Option  "MaxTapMove"            "0"
    Option  "MaxDoubleTapTime"      "0"
    Option  "ClickTime"  "0"
    Option  "EmulateMidButtonTime"  "75"
    Option  "VertScrollDelta"       "10"
    Option  "HorizScrollDelta"      "0"
    Option  "MinSpeed"              "0.45"
    Option  "MaxSpeed"              "0.75"
    Option  "AccelFactor"           "0.020"
    Option  "EdgeMotionMinZ"    "30"
    Option  "EdgeMotionMaxZ"    "160"
    Option  "EdgeMotionMinSpeed"    "200"
    Option  "EdgeMotionMaxSpeed"    "200"
    Option  "EdgeMotionUseAlways"    "0"
    Option  "UpDownScrolling"       "1"
    Option "TouchpadOff" "0"
    Option "GuestMouseOff" "0"
    Option "LockedDrags" "0"
    Option "RTCornerButton" "2"
    Option "RBCornerButton" "3"
    Option "LTCornerButton" "0"
    Option "LBCornerButton" "0"
    Option "TapButton1" "0"
    Option "TapButton2" "0"
    Option "TapButton3" "0"
    Option  "CircularScrolling"     "0"
    Option  "CircScrollDelta"       "0.1"
    Option  "CircScrollTrigger"     "2"
    Option  "CircularPad"     "0"
    Option  "SHMConfig"  "true"
EndSection
 
Any help getting me on track would be appreciated typing is EXTREMELY irritating at the moment.  Disabling the touchpad is not a solution BTW, so please do not suggest it.

Thanks,
Patrick

---

### Post by pi/roman on 2010-01-25
Make sure your touchpad is being detected:
xinput list

If it is in the list then it is being detected and it should be configured through HAL see [https://wiki.ubuntu.com/X/Config/Input#Input%20Configuration%20with%20HAL.]("https://wiki.ubuntu.com/X/Config/Input#Input%20Configuration%20with%20HAL")

find your configuration file:
sudo find / -name '11-x11-synaptics.fdi'

Then put these lines in to enable SHMconfig and disable tapping:
<merge key="input.x11_options.SHMConfig" type="string">true</merge>
<merge key="input.x11_options.TapButton1" type="string">0</merge>
<merge key="input.x11_options.TapButton2" type="string">0</merge>
<merge key="input.x11_options.TapButton3" type="string">0</merge>

You should also either comment out or just delete the entire "Synaptics Touchpad" section in xorg.conf.

---

### Post by pi/roman on 2010-01-27
Did this work?

---

### Post by bluefoxox on 2010-01-27
I am getting an error which says Server is already active for display 0 If this server is no longer running, remove /tmp/.0X-lock and start again.
 
I really think that I am going to give linux up.  It is not very friend by any stretch of the imagination so far.  My speakers no longer work in windows or linux.  I called HP and installing Linux has voided my warantee.  I am simply getting tired of the endless hours it has taken just to get all this working.  Now I need to jerry rid my touchpad so that I can type correctly?  Probably not.  Thanks though.

---

### Post by AlexZaim on 2010-01-27
> I called HP and installing Linux has voided my warantee.

That's strange. They shouldn't normaly do that. I don't see why installing another OS voids a hardware waranty.

---

### Post by bluefoxox on 2010-01-27
I agree!  I am calling back later tonight.  Maybe I will try again later on the touchpad.  For the moment I am a little frustrated.   What did you think of the error I recieved?

---

### Post by AlexZaim on 2010-01-27
Can't say too much about the error myself... pi/roman looks to know way more than me in this field.

Other than, "install the driver", "google for the problem", "check other forums" i can't say anything .sorry (.

---

### Post by pi/roman on 2010-01-27
I am not sure what the "Server is already active for display 0" error means but it appears as though something is attempting to make a change to Xserver while it is running.  You could remove the server lock as it recommends with:
sudo rm /tmp/.X0-lock
but that probably would not fix the problem so probably the best thing to do would be to create a new xorg.conf file to ensure that is not what is causing the error.
Here is how to do it. Create a new file called xorg.conf.new with this line which will put it in your /home/*usrname* folder:
sudo X :2 -configure

then move it to your /etc/X11/ folder:
sudo mv ~/xorg.conf.new /etc/X11/

So now you can open nautilus and look in your /etc/X11/ folder where both your xorg.conf and the xorg.conf.new will be. Then you can open them both side by side and compare them.  I'm not sure if you posted your entire xorg.conf earlier, but if so you probably won't need anything out of it.  You may need to remove references to the touchpad such as Load    "synaptics" in the module section.  So then rename xorg.conf to xorg.conf.bak and rename xorg.conf.new to xorg.conf.  Normally I would recomend including modelines in it but since your other one did not have them it is probably nt necessary.
Then reboot and hopefully you don't get the error again.

---

### Post by bluefoxox on 2010-03-13
Hello again.  I got my notebook back from HP the sound is now repaired.  I am having the same issue with the touch pad obviously.  When I use xinit list at the command line the touch pad seems to be detected as a PS/2 mouse, and a MAC touch pad.  Still looking for a solution, and could use a hand. Thanks for the help so far!

---

