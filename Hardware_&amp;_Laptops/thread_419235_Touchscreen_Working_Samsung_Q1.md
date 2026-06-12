---
title: "Touchscreen Working: Samsung Q1"
date: 2007-04-22
forum: Hardware &amp; Laptops
---

### Post by wmadan on 2007-04-22
In this post, I present a how-to for getting the touchscreen working on my Samsung Q1P UMPC tablet. In reading through the forums here, touchscreens are an issue that ends for lots of people in failure rather than success. For me, the path to success was forged by many failures. :( 

Note: I am somewhat familiar with Linux, having used it for about 5 years. However, I am only decent with the command line, so my description of the steps I took might seem somewhat rudimentary to a linux pro who is expert at the command line.

After these system tweaks, I am basically able to achieve the result I wanted: the ability to run Ubuntu and use the touch interface as a mouse. This process does not enable any inking features like you have in Windows XP or Vista. For me, this limitation was acceptable given what I wanted to do with Ubuntu. If I want to ink, I just boot into Vista and use the excellent inking features Vista has.

I had the Samsung Q1 keyboard/integrated mouse pointer plugged into one of the USB ports. These installation instructions assume you are using the same keyboard/mouse combination, that you have a functioning Ubuntu 7.04 installation going and have installed all updates. Also of note, with this keyboard/mouse combination, I did not run into the problem with udev a lot of people were having. Evidently, by plugging in various USB devices, udev randomly reassigns various events to usb devices, which can wreak havoc with your touchscreen settings. Thus, the steps below do not have a section for setting udev rules to prevent this. (To be honest, this is where I got stumped. If anyone can chip in and help at this point, it would be great! :) )

I also installed 915resolution to get the native 800x480 resolution set for X. In addition, I used Synaptic to install linux-source, build-essential and tcl8.4dev.

**_Touchscreen Installation Steps_**
1.	Obtain the evtouch driver from [http://stz-softwaretechnik.com/~ke/touchscreen/evtouch.html]("http://stz-softwaretechnik.com/~ke/touchscreen/evtouch.html"). 

Unzip the file to your desktop (I downloaded version 0.8.4). Copy the file evtouch_drv.so to /usr/lib/xorg/modules/input (I typed “sudo nautilus” in a terminal and copied the file over using nautilus instead of using the command line.)

At the present time, the evtouch driver calibration utility is broken, so there’s no way to use it to help set the calibration for the screen. This leads us to the next step.

2.	Obtain calibration utility binary from [www.nextabyte.com/support/touchscreen]("www.nextabyte.com/support/touchscreen") (you want the file named “calibrator”). There's a good pdf how-to document in the directory you may also want to grab.

3.	Open a terminal and type ```
cat /proc/bus/input/devices
``` Look for the item with the name “Touchkit Touch.” In the line with the word “Handlers” note the output (for me it read: Handlers=mouse1 event2 ts1).

4.	Select the calibrator program on your desktop and right click on it. Select Properties. Click the Permissions tab and click the checkbox “Allow executing file as program.”

5.	Open a terminal and navigate to where the calibration program is found (e.g., cd /home/bill/Desktop for me). Type ```
sudo ./calibrator /dev/input/eventX
``` (where eventX = the event number identified in step 3 above. For me it was event2.). The calibration program should run and present you with bulls-eyes in each of the four corners of the screen. Tap the pulsating top left hand bulls-eye, then the top right hand, then bottom left and bottom right. The calibration program will end and in the terminal will be four sets of numerical coordinates for the screen representing minX, maxX, minY, maxY.

The calibration program will modify your xorg.conf file with a new section as follows:
```
Section	"InputDevice"
	Identifier	"touchscreen"
	Driver	"evtouch"
	Option	"Device"	"/dev/input/event2"
	Option	"DeviceName"	"touchscreen"
	Option	"MinX"		"82"
	Option	"MinY"		"3900"
	Option	"MaxX"		"3960"
	Option	"MaxY"		"195"
	Option	"SwapY"		"1"
	#Option	"SwapXY"	"1"
	Option	"ReportingMode"	"Raw"
	Option	"Emulate3Buttons"
	Option	"Emulate3Timeout"	"50"
	Option	"SendCoreEvents"
EndSection
```

If the calibration program does not work for you, you can simply copy this section and paste it into your xorg.conf file at the very end.
•	Note: the section snippet above contains my tweaked resolution values and not the original values returned by executing the calibration program. I found the calibration program values were a good starting point, but I needed to adjust the values slightly to achieve the best results. Getting the touchscreen calibration just right is a trial and error process.
•	Make sure to restart X by hitting Ctrl Alt Backspace after each change to see the results. 
•	Note: In the section: Option “Device”, I changed the line to read ```
Option "Device"		"/dev/input/mice"
```
•	Note: In the “Option ‘SwapY’” section, I had to replace “0” with “1” in order for my touch calibration settings to track properly.

The calibration program will also insert the following line at the top the section: Section “Server Layout”
```
InputDevice "touchscreen" "SendCoreEvents" 
```

If you want to use the pointer mouse along with being able to use the touchscreen, then this line should read as above. If you don’t want to use the mouse pointer but only the touchscreen, change the line to  ```
InputDevice "touchscreen" “CorePointer” 
```I found that with the setting “SendCoreEvents”, the touchscreen would work, but it wasn’t as smooth as when “CorePointer” was the setting. I found that the touch pointer was somewhat erratic, but it did work. If you do not need the mouse pointer, then you may want to set this line at the “CorePointer” setting.

The calibration program also modified the section of xorg.conf called: 
Section “Input Device’” for my mouse. I had to change the line to read:
```
Option "Device" "/dev/input/mice"
```

6.	So that I wouldn’t have to use the keyboard to log in to Ubuntu each time it started (helpful if you are operating in slate mode without the keyboard attached), I went to System>Administrator>Login Window. After typing in your password, click on the Security tab. Check the box “Enable Automatic Login.” In the User drop-down, select your username.

7.	To enable Ubuntu’s silk keyboard for tapping keyboard input without an attached keyboard, I went to System>Preferences>Accessibility>Assistive Technology Preferences. Under On-screen keyboard, click the checkbox “Start on-screen keyboard at log in.” The keyboard will appear as Ubuntu is loaded. You can resize the keyboard and click the Minimize button to minimize it. There will be an icon in the upper task bar that you can click or touch to bring up the keyboard when you need it, like when typing in a web address when surfing the Net while in bed. :) 

Ubuntu 7.04 has come a long way. I can remember when the major challenge for me in getting Ubuntu properly configured on a laptop was wireless networking. With this release, my wireless card was detected and worked right out of the box. We can only hope that with successive releases, the vexing challenges of touchscreens will become less problematic.

Enjoy,

Bill

---

### Post by lonce on 2007-04-22
I use a silverstone case with a 7 " touchscreen built into the case.  Ubuntu recognized it immediately with zero setup.  

Treated the screen as a USB input device.  I was really impressed.

---

### Post by neuropaco on 2007-05-06
Hi, I have followed ALL of your instructions to set up the touchscreen but I couldn't put it to work on my q1. There's a point where I found a difference between what you say and what my computer does; after typing cat /proc/bus/input/devices, I can't find any *item with the name “Touchkit Touch.”*. The most similar entry showed on shell is the following:

I: Bus=0003 Vendor=0eef Product=0001 Version=0100
N: Name="Touchkit HID-USB Touchscreen"
P: Phys=usb-0000:00:1d.1-1/input0
S: Sysfs=/class/input/input2
H: Handlers=event2 js0 
B: EV=b
B: KEY=30000 0 0 0 0 0 0 0 0
B: ABS=3

I do everything you say. I even get to callibrate, but after that, I reboot with ctrl+alt+backspace and then... nothing. The screen is as insensitive as usual. Any clue?:( I would really appreciate your help, thank you very much in advance.

---

### Post by wmadan on 2007-05-06
> **neuropaco said:**
> Hi, I have followed ALL of your instructions to set up the touchscreen but I couldn't put it to work on my q1. There's a point where I found a difference between what you say and what my computer does; after typing cat /proc/bus/input/devices, I can't find any *item with the name “Touchkit Touch.”*. The most similar entry showed on shell is the following:

I: Bus=0003 Vendor=0eef Product=0001 Version=0100
N: Name="Touchkit HID-USB Touchscreen"
P: Phys=usb-0000:00:1d.1-1/input0
S: Sysfs=/class/input/input2
H: Handlers=event2 js0 
B: EV=b
B: KEY=30000 0 0 0 0 0 0 0 0
B: ABS=3

I do everything you say. I even get to callibrate, but after that, I reboot with ctrl+alt+backspace and then... nothing. The screen is as insensitive as usual. Any clue?:( I would really appreciate your help, thank you very much in advance.

Neuropaco,

I will try to help, but can you post your xorg.conf file?

Bill

---

### Post by Ian Lynch on 2007-05-13
Hi,

First thanks for the information. I had been struggling to get anywhere before, now I had it working pretty well but its gone haywire again. I copied your section settings to my xorg.conf except when I did the event test it said event 5 so I edited where you had event  2 to be event 5. Saved and everything worked almost perfectly until I restarted X which then made it seem as if the calibration and completely broken. I checked the event allocation and it seemed to have moved to the same as yours at event 2 so I re-edited but still no joy. The frustrating thing is that I had it working and can't see how anything changed to stop it! Any chancy that you could e-mail me your xorg.conf file to check if there are any other differences I haven't spotted?

ian dot lynch at zmsl dot com

-- 
Ian

---

### Post by jjordan on 2007-05-14
wmadan,

I use a Fujitsu P1510, take a look at Jarnal for ink and rudimentary text recognition.  It may save you rebooting.  There is a windows version avaiable also and files are compatible.

-j

---

### Post by wmadan on 2007-05-19
> **Ian Lynch said:**
> Hi,

First thanks for the information. I had been struggling to get anywhere before, now I had it working pretty well but its gone haywire again. I copied your section settings to my xorg.conf except when I did the event test it said event 5 so I edited where you had event  2 to be event 5. Saved and everything worked almost perfectly until I restarted X which then made it seem as if the calibration and completely broken. I checked the event allocation and it seemed to have moved to the same as yours at event 2 so I re-edited but still no joy. The frustrating thing is that I had it working and can't see how anything changed to stop it! Any chancy that you could e-mail me your xorg.conf file to check if there are any other differences I haven't spotted?

ian dot lynch at zmsl dot com

-- 
Ian

Ian,

Udev might be changing event numbers on you. Sometimes when you plug in USB devices, this happens. I have not had to devise udev rules to keep the system from randomly reassigning event numbers. 

Bill

---

### Post by Ian Lynch on 2007-05-21
Yes the variation seems to suggest its something to do with things changing when devices change. I prefer using a mouse and keyboard anyway and bought the Q1 mainly because of its compact sze for use on planes where the space is really cramped. My old Psion netBook design suited me better but lack of wifi, USB etc was a bigger issue. I just wish someone would come up with a Psion netBook form factor with Ubuntu, USB, Wifi and blue tooth and the Psion's hours of battery life. Another device 10 years ahead of its time :-) Strikes me that Windows on the Samsung is what makes it slow and power hungry. 

Thanks for your comments. Maybe if we wait long enough Samsung or the good people at Ubuntu might come up with a relaible solution for the touchscreen. I really think screen config is a bit of an achilles heel for Ubuntu. We really need a graphical application like the one in Windows control panel so the user can experiment interactively with different settings without having to edit xorg.conf directly.

---

### Post by Quicksand on 2007-06-14
Is anyone still on this situation?  I positively LOVE how Feisty is running on my Q1, but the touchscreen is giving me fits.  Here's the output from five consecutive runs of the configuration program:

[INDENT]clarke@arthur:~/archives$ sudo ./calibrator /dev/input/event2
Trying to calibrate screen to: 800 x 480 resolution
Copy-Paste friendly, for evtouch XFree86 driver
        Option "MinX" "721"
        Option "MinY" "898"
        Option "MaxX" "1597"
        Option "MaxY" "-52"
721 1597 898 -52 inverted y: 0
clarke@arthur:~/archives$ sudo ./calibrator /dev/input/event2
Trying to calibrate screen to: 800 x 480 resolution
Copy-Paste friendly, for evtouch XFree86 driver
        Option "MinX" "177"
        Option "MinY" "528"
        Option "MaxX" "1565"
        Option "MaxY" "382"
177 1565 528 382 inverted y: 0
already edited xorg.conf before
scuttling mission...(please edit manually)
clarke@arthur:~/archives$ sudo ./calibrator /dev/input/event2
Trying to calibrate screen to: 800 x 480 resolution
Copy-Paste friendly, for evtouch XFree86 driver
        Option "MinX" "1757"
        Option "MinY" "1607"
        Option "MaxX" "369"
        Option "MaxY" "583"
1757 369 1607 583 inverted y: 0
already edited xorg.conf before
scuttling mission...(please edit manually)
clarke@arthur:~/archives$ sudo ./calibrator /dev/input/event2
Trying to calibrate screen to: 800 x 480 resolution
Copy-Paste friendly, for evtouch XFree86 driver
        Option "MinX" "387"
        Option "MinY" "528"
        Option "MaxX" "1483"
        Option "MaxY" "382"
387 1483 528 382 inverted y: 0
already edited xorg.conf before
scuttling mission...(please edit manually)
clarke@arthur:~/archives$ sudo ./calibrator /dev/input/event2
Trying to calibrate screen to: 800 x 480 resolution
Copy-Paste friendly, for evtouch XFree86 driver
        Option "MinX" "830"
        Option "MinY" "715"
        Option "MaxX" "976"
        Option "MaxY" "643"
830 976 715 643 inverted y: 0
already edited xorg.conf before
scuttling mission...(please edit manually)
clarke@arthur:~/archives$ [/INDENT]

It works -- i.e., it waits for me to touch each bullseye, which I do -- but the output seems almost random.  And if I actually try to use the touchscreen subsequently (after a ctrl-alt-bs, of course), the pointer jumps around maniacally.

Does anyone have any suggestions?

---

### Post by Quicksand on 2007-06-16
Problem solved!  Something got a little wonky with the udev rule I had set up.  Here's one that works on my Q1 (the original model with 900 MHz Celeron).

Create a file called **/etc/udev/rules.d/10-local.rules**, or open it if it already exists.

(For beginners, that would be **gksudo gedit /etc/udev/rules.d/10-local.rules**)

Enter the following in a single line, or if the file exists already, add a new line to what is already there:

**SUBSYSTEM=="input", KERNEL=="event*", ATTRS{name}=="Touchkit HID-USB Touchscreen", SYMLINK+="input/touchscreen"**

Save the file and reboot.  What this does is cause the touchscreen input device to have a node at /dev/input/touchscreen, regardless of what /dev/input/event# it started as, and regardless of what other USB input devices are plugged in.

So then, follow the instructions in the original post, but use **/dev/input/touchscreen** in the command line for the calibrator and in the xorg.conf configuration file.

These instructions are somewhat similar to what's in the PDF referenced in the original post, but the PDF isn't quite correct for the Q1.  So ignore that and do this instead!

:D

---

### Post by starttman on 2007-07-06
Ok, i've followed everyone's tips (thanks a lot!), and I'm really close to getting this to work!

After tweaking the x and y settings, the touchscreen works EXACTLY as it should when I'm at the Ubuntu login screen. The touch mouse is perfectly lined-up with my finger, I can double-click, and I can even select text using only the touchscreen. However, as soon as I login to my desktop, the cursor moves about an inch to the right and slightly below my finger.

So what happens from a config point-of-view between the login-screen and entering your desktop? Is some file running after the login that's screwing up my settings?

One other side note, that might be relevant: prior to installing the EvTouch drivers, I was trying the TouchKit drivers by following the manual instructions here ([http://www.touchkit.com/m/Manual_Linux-v1.0.2.pdf](http://www.touchkit.com/m/Manual_Linux-v1.0.2.pdf)).  I had no luck with this so I manually "undid" everything I could to avoid any interactions with the two drivers.  Touchkit should be completely uninstalled, but maybe I'm missing something?  Just food for thought, it may not be important.

---

### Post by tjvigil66 on 2007-08-07
I've just started looking into porting my Q1P to Linux.

Even if you do get the touchscreen working, do you still require a physical keyboard to log in?

...or is there anything available via the "Accessibility" apps menu that would work at log in?

---

### Post by Jaidee on 2007-08-12
I have the evtouch driver working with my Dialogue Flybook V33i, and plan on writing a guide for this system very soon. I am currently trying to get it working perfectly, but as it stands, I'm unable to use the touchscreen to write handwritten notes (using xournal for example), and the cursor position does not remain stable whilst the stylus is held stable - instead the cursor jumps around 50 pixels every few ms or so. This makes it fine for tapping icons and such, but when writing by hand, the cursor jumps cause the vectors to be drawn wildly, rendering the notes illegible.

Have you had any success with stabilizing the stylus? How is it when taking notes in this manner? (Try installing xournal if you haven't tried it already.)

Thanks for reading!

---

### Post by ZeroVerteX on 2007-11-24
Worked perfectly on my Fujitsu Lifebook B Series! THANKS!

---

### Post by loopfuzz on 2007-12-04
Hello, I'm trying to get your Linux-Touchscreen drivers to work on my  
unbutnu Samsung Q1 ULTRA machine.  I've read these articles and every other article relating to this on the web. still having some issues.

One thing I noticed is that if the touch screen device boots up and  
is set to /dev/input/event5, then  WILL WORK.  BUT if it  
goes to event2 or event3 then it DOES NOT WORK.  Do you know if there  
is anyway I could force it to be set to event5?   
It seems to be  random whenever I boot up.  I have tried  setting things in my /etc/ 

I think this could be some hardware conflict that happens.  Maybe IRQ or memory?

---

### Post by jhford on 2007-12-09
I tried to get this working on my Q1 Ultra but it failed. The only thing I can think of in terms not following the terrific instructions correctly is that although I downloaded the evtouch driver, I didn't copy it to the suggested directory, because it was already there immediately after the Ubuntu installation.

Should I try to copy the driver again, or is there some other problem?

BTW, after I did the calibration nothing was written to xorg.conf and I had to type the whole section by hand.

Thanks for any help.

---

### Post by l3th0x on 2007-12-23
Hi,

I had a r2h, and now a q1, and with the evtouch driver,  the "/etc/udev/rules.d/10-local.rule solution" and adding this:

# gestion TouchScreen Via drivers evtouch Xorg
blacklist usbtouchscreen


to the blacklist ( sudo gedit /etc/modprobe.d/blacklist ) you will not have more problems with touchscreen!!, just works!! jeje..

Best Regards!

---

### Post by analogred on 2008-04-07
I got this to work about a week ago now, and I must say I'm thoroughly pleased with the touch screen operation. The main thing to remember when working on this is to not have ANYTHING plugged into the USB ports when you boot the computer or Ctrl+Alt+Bksp. Anything plugged in will screw with the event number and cause the touch screen to act up or not work at all.

This thread was an excellent tutorial after all the feedback, and I couldn't be happier with Ubuntu fully functioning on my Q1.

---

### Post by l3th0x on 2008-04-07
Hi Analogred,

Your problem, will be resolved with this steps:

download evtouch
tar xvfz evtouchbla. 
cd evtouch..blabla, and copy  evtouch_drv.so to  /usr/lib/xorg/modules/input/ .

Add in your xorg this:

sudo vim /etc/X11/xorg.conf

Section	"InputDevice"
	Identifier	"touchscreen"
	Driver	"evtouch"
	Option	"Device"	"/dev/input/touchscreen"
	Option	"DeviceName"	"touchscreen"
	Option	"MinX"		"82"
	Option	"MinY"		"3900"
	Option	"MaxX"		"3960"
	Option	"MaxY"		"195"
	Option	"SwapY"		"1"
	#Option	"SwapXY"	"1"
	Option	"ReportingMode"	"Raw"
	Option	"Emulate3Buttons"
	Option	"Emulate3Timeout"	"50"
	Option	"SendCoreEvents"
EndSection

and in: Section "ServerLayout"

write:

InputDevice "touchscreen" "CorePointer"

then, 

sudo vim /etc/udev/rules.d/10-local.rules

and write:

SUBSYSTEM=="input", KERNEL=="event*", ATTRS{name}=="Touchkit HID-USB Touchscreen", SYMLINK+="input/touchscreen"

then, 

sudo gedit /etc/modprobe.d/blacklist

#TouchScreen evtouch 
blacklist usbtouchscreen

and when you restart your machine it will be okay.

Regards

---

