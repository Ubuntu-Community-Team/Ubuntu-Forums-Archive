---
title: "Lenovo C200 touchscreen problem"
date: 2012-11-22
forum: Hardware
---

### Post by Crazy Factory on 2012-11-22
Hello, 

we have some Lenovo C200 computers, and we have huge problems with the touchscreen when we install Ubuntu.
After we made the setup of Ubuntu on our computers, we switch to the desktop, and then we cant use the touchscreen.
Somehow we cant calibrate the touchscreen and when we pressing the touchscreen, the mouse is moving weird around on the screen.

My question is, how can we solve this problem?
We've also downloaded "Xinput" and tried to calibrate it with it, but also the same problem.
However, i hope someone can help us to fix this problem as soon as possible.

Thank you in advance.

---

### Post by Favux on 2012-11-23
Hi Crazy Factory,

Welcome to Ubuntu forums!


Are you actually using Raring alpha to set up your Lenovo all-in-ones?

Are they still single finger touch (1FGT)?

Do you know who makes the touchscreen, i.e. VID and PID?  Lets look at the output of the following terminal commands:
```
lsusb

xinput list

cat /proc/bus/input/devices
```

---

### Post by Crazy Factory on 2012-11-25
Thank you very much for your reply.

We are using the ubuntu 12.04 LTS version.
It's a single touch screen.
I have no experience about that system, because i just know the windows system.
I've just found a link about our computers here.

[http://hardwarebistro.com/?option=com_simple_review&Itemid=84&review=178-Lenovo-Essential-C200-Touchscreen-All-in-One-Review](http://hardwarebistro.com/?option=com_simple_review&Itemid=84&review=178-Lenovo-Essential-C200-Touchscreen-All-in-One-Review)

I will paste the terminal commands:

test@test-Lenovo-C200:~$ lsusb
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 005: ID 0ac8:c430 Z-Star Microelectronics Corp. 
Bus 002 Device 002: ID 17ef:602d Lenovo 
Bus 003 Device 002: ID 0461:4d80 Primax Electronics, Ltd 
Bus 004 Device 002: ID 0eef:0001 D-WAV Scientific Co., Ltd eGalax TouchScreen
test@test-Lenovo-C200:~$ 

test@test-Lenovo-C200:~$ xinput list
&#9121; Virtual core pointer                        id=2    [master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer                  id=4    [slave  pointer  (2)]
&#9116;   &#8627; USB Optical Mouse                           id=10    [slave  pointer  (2)]
&#9116;   &#8627; eGalax Inc. USB TouchController             id=11    [slave  pointer  (2)]
&#9123; Virtual core keyboard                       id=3    [master keyboard (2)]
    &#8627; Virtual core XTEST keyboard                 id=5    [slave  keyboard (3)]
    &#8627; Power Button                                id=6    [slave  keyboard (3)]
    &#8627; Power Button                                id=7    [slave  keyboard (3)]
    &#8627; Lenovo Lenovo Black Silk USB Keyboard       id=8    [slave  keyboard (3)]
    &#8627; Lenovo Lenovo Black Silk USB Keyboard       id=9    [slave  keyboard (3)]
    &#8627; Lenovo USB 2.0 UVC Camera                   id=12    [slave  keyboard (3)]
test@test-Lenovo-C200:~$ 

 cat /proc/bus/input/devices
I: Bus=0019 Vendor=0000 Product=0001 Version=0000
N: Name="Power Button"
P: Phys=PNP0C0C/button/input0
S: Sysfs=/devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input0
U: Uniq=
H: Handlers=kbd event0 
B: PROP=0
B: EV=3
B: KEY=100000 0 0 0

I: Bus=0019 Vendor=0000 Product=0001 Version=0000
N: Name="Power Button"
P: Phys=LNXPWRBN/button/input0
S: Sysfs=/devices/LNXSYSTM:00/LNXPWRBN:00/input/input1
U: Uniq=
H: Handlers=kbd event1 
B: PROP=0
B: EV=3
B: KEY=100000 0 0 0

I: Bus=0003 Vendor=0eef Product=0001 Version=0100
N: Name="eGalax Inc. USB TouchController"
P: Phys=usb-0000:00:1d.2-2/input0
S: Sysfs=/devices/pci0000:00/0000:00:1d.2/usb4/4-2/4-2:1.0/input/input2
U: Uniq=
H: Handlers=mouse0 event2 
B: PROP=0
B: EV=b
B: KEY=400 0 0 0 0 0 0 0 0 0 0
B: ABS=3

I: Bus=0003 Vendor=17ef Product=602d Version=0111
N: Name="Lenovo Lenovo Black Silk USB Keyboard"
P: Phys=usb-0000:00:1d.0-2/input0
S: Sysfs=/devices/pci0000:00/0000:00:1d.0/usb2/2-2/2-2:1.0/input/input3
U: Uniq=
H: Handlers=sysrq kbd event3 
B: PROP=0
B: EV=120013
B: KEY=10000 7 ff9f207a c14057ff febeffdf ffefffff ffffffff fffffffe
B: MSC=10
B: LED=7

I: Bus=0003 Vendor=17ef Product=602d Version=0111
N: Name="Lenovo Lenovo Black Silk USB Keyboard"
P: Phys=usb-0000:00:1d.0-2/input1
S: Sysfs=/devices/pci0000:00/0000:00:1d.0/usb2/2-2/2-2:1.1/input/input4
U: Uniq=
H: Handlers=kbd event4 
B: PROP=0
B: EV=13
B: KEY=2010000 397a d801d001 1e0000 0 0 0
B: MSC=10

I: Bus=0003 Vendor=0461 Product=4d80 Version=0111
N: Name="USB Optical Mouse"
P: Phys=usb-0000:00:1d.1-1/input0
S: Sysfs=/devices/pci0000:00/0000:00:1d.1/usb3/3-1/3-1:1.0/input/input5
U: Uniq=
H: Handlers=mouse1 event5 
B: PROP=0
B: EV=17
B: KEY=70000 0 0 0 0 0 0 0 0
B: REL=143
B: MSC=10

I: Bus=0003 Vendor=0ac8 Product=c430 Version=1006
N: Name="Lenovo USB 2.0 UVC Camera"
P: Phys=usb-0000:00:1d.7-8/button
S: Sysfs=/devices/pci0000:00/0000:00:1d.7/usb1/1-8/1-8:1.0/input/input6
U: Uniq=
H: Handlers=kbd event6 
B: PROP=0
B: EV=3
B: KEY=100000 0 0 0 0 0 0

I: Bus=0000 Vendor=0000 Product=0000 Version=0000
N: Name="HDA Intel Mic"
P: Phys=ALSA
S: Sysfs=/devices/pci0000:00/0000:00:1b.0/sound/card0/input7
U: Uniq=
H: Handlers=event7 
B: PROP=0
B: EV=21
B: SW=10

I: Bus=0000 Vendor=0000 Product=0000 Version=0000
N: Name="HDA Intel Headphone"
P: Phys=ALSA
S: Sysfs=/devices/pci0000:00/0000:00:1b.0/sound/card0/input8
U: Uniq=
H: Handlers=event8 
B: PROP=0
B: EV=21
B: SW=4

test@test-Lenovo-C200:~$ 


I hope it's helping you and i hope that there is a solution for it.
As i said, when i am touching the touschreen, the "mouse" is moving around and jumping.
I cant control it, also when i am trying to calibrate it with "Xinput", i cant find any solution for it.
Maybe there is a way to calibrate it manually.
I've tried to unplug the keyboard and the mouse, and then i was trying again to use use the touchscreen, but again, there
is still the same problem.
I would have no problem to use another ubuntu system if it helps to make this touchscreens working.
We need the touchscreens for our departments.

Thank you very much in advance!

I appreciate your help.

Best Regards

Markus Hoffmann
Crazy Factory Trading Co., Ltd.

---

### Post by Favux on 2012-11-25
**[SIZE="3"]Moderator, please move thread from Raring testing to Hardware.[/SIZE]**


Hi Markus,

Well I guess it should be on the evdev X driver.  Let's check:
```
xinput list-props "eGalax Inc. USB TouchController"
```
You could also check in /var/log/Xorg.0.log and see if it complains of any errors.

Did you install the eGalax kernel driver?
[http://home.eeti.com.tw/web20/eGalaxTouchDriver/linuxDriver.htm](http://home.eeti.com.tw/web20/eGalaxTouchDriver/linuxDriver.htm)

---

### Post by Crazy Factory on 2012-11-25
Hello, when i am entering in terminal

"xinput list-props "eGalax Inc. USB TouchController"
it shows:

> xinput list-props "eGalax" Inc. USB TouchController"
unable to find device eGalax
unable to find device Inc.
unable to find device USB
unable to find device TouchController
xinput list-props eGalax Inc. USB TouchController
test@test-Lenovo-C200:~$ 

I've didnt install the eGalax driver, ive tried to from your link, but somehow i cant install, or dont know how to install.
It just extract some files, but i cant really setup them.
I am sorry for my lack of experience.
There is a file which is called setup.sh, but when i click it, a editor is opening.

I may need a description of it.

Thank you in advance

Markus Hoffmann
Crazy Factory Trading Co., Ltd.

---

### Post by Crazy Factory on 2012-11-25
Hello, when i am entering in terminal

"xinput list-props "eGalax Inc. USB TouchController"
it shows:

> xinput list-props "eGalax" Inc. USB TouchController"
unable to find device eGalax
unable to find device Inc.
unable to find device USB
unable to find device TouchController
xinput list-props eGalax Inc. USB TouchController
test@test-Lenovo-C200:~$ 

I've didnt install the eGalax driver, ive tried to from your link, but somehow i cant install, or dont know how to install.
It just extract some files, but i cant really setup them.
I am sorry for my lack of experience.
I clicked on a file, then the message appears "No Touch Controller found", but it is a touchscreen..

I may need a description of it.

Thank you in advance

Markus Hoffmann
Crazy Factory Trading Co., Ltd.

---

### Post by Favux on 2012-11-25
It is one <device name> conained in quotes, i.e. "eGalax" Inc. USB TouchController".  Your adding the extra quote to the device name broke it up.  Interesting that evdev now treats each word as a keyword though.  Or it seems to now.

Right click on **setup.sh** and chose Properties.  Under the Permissions tab is the Execute box checked?  If not check it.  But don't install yet.

Not sure whether the default driver in the kernel's HID section can handle your touchscreen or whether you need the proprietary one.  Didn't find anything talking about models the driver supports.

By the way the 0eef:0001 in the **lsusb** output is the VID: PID, as in:
Vendor ID = 0eef = D-WAV Scientific Co., Ltd
Product ID (model) = 0001

---

### Post by Crazy Factory on 2012-11-26
I checked the execute box, "Allow executing files as program", but nothing works.
There is also always the sign "No Touchscreen Controller installed".
I have no clue..
I cant even install, because it just extract some files and offering me with what i want to open the setup file..terminal, display, run and so on.

---

### Post by Favux on 2012-11-26
I'd like to see the list-props before you install the driver.  Sometimes evdev just needs the coordinates to get a tablet/touchscreen working.

But looking at the install script it looks like you probably do need to install the driver.

The .sh extension on **setup.sh** indicates it is a shell script.  The shebang line at the top of the script:
```
#!/bin/sh
```
tells you which directory the sh (shell) executable binary is located.  In this case the /bin directory where bin is short for binary.
> offering me with what i want to open the setup file..terminal, display, run and so on.
It is suppose to.  You chose **Run** to execute the script.

The other way to run the script is to open a terminal and change directory to where the script is and then run:
```
sh setup.sh
```
as the readme says.  When you do that you do not need to make the script executable.

---

### Post by Crazy Factory on 2012-11-26
I see and know your meaning.

I dont know if i have all drivers updated here, but right now i am making a update, maybe it helps.
I tried to install the SH file, but when i click on "run" nothing happends.
When i go in the terminal and enter sh setup.sh, it says "Can't open setup.sh"

Hmm, sorry..i dont get into that :-/

---

### Post by cariboo on 2012-11-26
Moved to Hardware, as it has nothing to do with Raring.

---

### Post by Crazy Factory on 2012-11-26
unable to find device eGalax Inc. USB TouchControllerxinput
unable to find device list-props
unable to find device eGalax Inc. USB TouchControllerxinput
unable to find device list-props
unable to find device eGalax Inc. USB TouchControllerxinput
unable to find device list-props
Device 'eGalax Inc. USB TouchController':
    Device Enabled (134):    1
    Coordinate Transformation Matrix (136):    1.000000, 0.000000, 0.000000, 0.000000, 1.000000, 0.000000, 0.000000, 0.000000, 1.000000
    Device Accel Profile (257):    0
    Device Accel Constant Deceleration (258):    1.000000
    Device Accel Adaptive Deceleration (259):    1.000000
    Device Accel Velocity Scaling (260):    10.000000
    Device Product ID (251):    3823, 1
    Device Node (252):    "/dev/input/event2"
    Evdev Axis Inversion (261):    0, 0
    Evdev Axis Calibration (262):    0, 2047, 0, 2047
    Evdev Axes Swap (263):    0
    Axis Labels (264):    "Abs X" (278), "Abs Y" (279)
    Button Labels (265):    "Button Unknown" (254), "Button Unknown" (254), "Button Unknown" (254), "Button Wheel Up" (140), "Button Wheel Down" (141)
    Evdev Middle Button Emulation (266):    0
    Evdev Middle Button Timeout (267):    50
    Evdev Third Button Emulation (268):    0
    Evdev Third Button Emulation Timeout (269):    1000
    Evdev Third Button Emulation Button (270):    3
    Evdev Third Button Emulation Threshold (271):    20
    Evdev Wheel Emulation (272):    0
    Evdev Wheel Emulation Axes (273):    0, 0, 4, 5
    Evdev Wheel Emulation Inertia (274):    10
    Evdev Wheel Emulation Timeout (275):    200
    Evdev Wheel Emulation Button (276):    4
    Evdev Drag Lock Buttons (277):    0
test@test-Lenovo-C200:~$ 

Does it help you? I am still stuck..
Thank you in advance.

---

### Post by Favux on 2012-11-26
I am confused by your list-props output.  What you should see in the terminal just before you enter the command is:
```
test@test-Lenovo-C200:~$ xinput list-props "eGalax Inc. USB TouchController"
```
Is that what you are using?

Also you can box in your output on your posts.  In Advanced when posting click on the # at the top right of the posting window.  That will bring up the code tags.  Place your output between them.

Are you sure nothing happened when you ran setup.sh?  For example is there a file /etc/X11/xorg.conf that contains a new eGalax section?

Looking at the script it appears you have to run it as root which is probably part of the problem.  Furthermore you probably need build-essential and either the linux headers or kernel source or both.  Easy to do but lets hold off on doing that.

Looking at the Driver Guide.pdf it looks like we may not need to install anything.  We just may need to create a xorg.conf.d file to configure it.  It says: 
> It is highly recommended to use inbuilt kernel module instead of tkusb
kernel module for USB touch device, by doing this all users do NOT need
to compile any source code during driver installation. The user can identify
the USB class of touch device and check which kernel module is loaded
for USB touch device by the following.

And to run this command in a terminal:
```
lsusb &#8211;v &#8211;d 0eef:0001

```
Please post that output.

---

### Post by Favux on 2012-11-26
Oops, nevermind.  Sorry, I got confused and was looking at the 2010 driver's .pdf.

You did download the eGTouch_v2.5.2107.L-x driver, correct?

Looking at its .pdf it seems to want you to install the driver and doesn't give an option to use the current kernel's driver.  If you ran the setup.sh in a terminal it would have complained about you not being root.

So assuming you downloaded the driver and extracted it on your Desktop change directory into the driver folder.
```
cd Desktop

cd eGTouch_v2.5.2107.L-x
```
And run:
```
sudo sh setup.sh
```
What I do is copy and paste any output in the terminal in a text file and save the text file so I have it to review.  That way you can inspect any errors or whatever at your leisure without keeping the terminal open.  Then reboot/restart.

---

### Post by Crazy Factory on 2012-11-27
Hello, i appreciate really your help, but when i enter those commands, nothing happends, sometimes i have to enter a password, i think its the password of the computer, but by other commands it says "permission denied".
Maybe the Lenovo C200 series are not compatible with ubuntu?
Because the Lenovo C200 series is a single touch, not a multi touch..it's really harming us, that the touchscreens are not working under ubuntu.



Bus 004 Device 002: ID 0eef:0001 D-WAV Scientific Co., Ltd eGalax TouchScreen
Couldn't open device, some information will be missing
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               1.10
  bDeviceClass            0 (Defined at Interface level)
  bDeviceSubClass         0 
  bDeviceProtocol         0 
  bMaxPacketSize0        64
  idVendor           0x0eef D-WAV Scientific Co., Ltd
  idProduct          0x0001 eGalax TouchScreen
  bcdDevice            1.00
  iManufacturer           1 
  iProduct                2 
  iSerial                 0 
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength           34
    bNumInterfaces          1
    bConfigurationValue     1
    iConfiguration          1 
    bmAttributes         0xa0
      (Bus Powered)
      Remote Wakeup
    MaxPower              100mA
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       0
      bNumEndpoints           1
      bInterfaceClass         3 Human Interface Device
      bInterfaceSubClass      0 No Subclass
      bInterfaceProtocol      0 None
      iInterface              0 
        HID Device Descriptor:
          bLength                 9
          bDescriptorType        33
          bcdHID               1.00
          bCountryCode            0 Not supported
          bNumDescriptors         1
          bDescriptorType        34 Report
          wDescriptorLength     322
         Report Descriptors: 
           ** UNAVAILABLE **
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x81  EP 1 IN
        bmAttributes            3
          Transfer Type            Interrupt
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0010  1x 16 bytes
        bInterval               3
test@test-Lenovo-C200:~$ ^C
test@test-Lenovo-C200:~$

---

### Post by Favux on 2012-11-27
Entering sudo causes it to ask for your root password and then for the next 5 or 10 minutes you have root access.  Do you know the root/super user password?  For most individual machines they are the same thing.  Have you set it up to have multiple users?  So the user password isn't the root password?

When you use su the prompt changes from $ to #, with # indicating root.  But not with sudo. In fact su isn't set up with a default Ubuntu install.

Can you show me the terminal output of you changing directories and running sudo on setup.sh?

---

### Post by Crazy Factory on 2012-11-27
I think the password is the same as the users password. I've didnt setup any password actually, only the one on the setup, when ubuntu is asking me which setup i want to use, then i type it and it's done.
How can i find the terminal output?
I am really sorry, but i am in this system a newbie..
Is Teamviewer working on the ubunutu systems?
Or maybe there is a other way that you could check the system?
Because i am really clueless and just understand some parts..

---

### Post by Favux on 2012-11-27
So your user password should be the sudo password.

Alright.  Where did you download the driver to?  Did you extract or uncompress it?  If not right click on it and choose "Extract here".

Open a terminal and run this command:
```
pwd
```
print working directory or pwd will tell you where you are in the directory tree.  That gets you oriented.

---

### Post by Crazy Factory on 2012-11-27
Ok.
I entered "pwd" and it showed me

/home/test

but i moved the eDTouch_v2.5.2107.L-x folder to the home folder where are the other folders like desktop, downloads, pictures and so on.
Before it was on the desktop, before i was moving it.

---

### Post by Favux on 2012-11-28
[http://www.ubuntupocketguide.com/download_main.html](http://www.ubuntupocketguide.com/download_main.html)

[https://help.ubuntu.com/community/CommandLineResources](https://help.ubuntu.com/community/CommandLineResources)


/ is the root directory.  Open the file browser Nautilus and go to File System.  That shows you the directories in root.  Go into home.  In there you should see test.  Test is apparently your username.  In the terminal it would look like /home/test.  When in test run the list (ls) command:
```
ls
```
That will show you what is in there.

When you open a terminal it puts you in /home/username.  Or in your case /home/test which is why with pwd you see:
> /home/test

From what you've said you moved /home/test/Desktop/eDTouch_v2.5.2107.L-x to /home/test/eDTouch_v2.5.2107.L-x.

So in a newly opened terminal to change directory into the driver folder you just type cd (change directory) folder name:
```
cd eDTouch_v2.5.2107.L-x
```
Where you actually are now would be:  /home/test/eDTouch_v2.5.2107.L-x
Or ~ is the shortcut for /home/test so you can also write it as:  ~/eDTouch_v2.5.2107.L-x

But first eDTouch_v2.5.2107.L-x doesn't look like the right driver.  Isn't it suppose to be eGTouch_v2.5.2107.L-x?  Or is that a typo?  The sudo command won't work with a mispelling.  When you use the CLI (command line interface) in a terminal things have to be spelled exactly, including case (letters capitalized or not).  And a directory can not have spaces in its name unlike the gui which invisibly fills in the spaces.

---

### Post by Crazy Factory on 2012-11-28
Hi, yes i am much more far now. Thank you so much.

Is this right now?
I did it exactly like you told me.

test@test-Lenovo-C200:~$ ls
Desktop    Downloads              examples.desktop  Pictures  Templates
Documents  eGTouch_v2.5.2107.L-x  Music             Public    Videos
test@test-Lenovo-C200:~$ cd eGTouch_v2.5.2107.L-x
test@test-Lenovo-C200:~/eGTouch_v2.5.2107.L-x$ sudo sh setup.sh
[sudo] password for test: 


(*) Driver installer for touch controller 
(*) Script Version = 1.04.2013 

(I) Check user permission: root, you are the supervisor.
(I) Platform application binary interface = i686
(W) X server detected.

Declaration and Disclaimer
The programs, including but not limited to software and/or firmware (hereinafter referred to "Programs" or "PROGRAMS", are owned by eGalax_eMPIA Technology Inc. (hereinafter referred to EETI) and are compiled from EETI Source code. EETI hereby grants to licensee a personal, non-exclusive, non-transferable license to copy, use and create derivative works of Programs for the sole purpose in conjunction with an EETI Product, including but not limited to integrated circuit and/or controller. Any reproduction, copies, modification, translation, compilation, application, or representation of Programs except as specified above is prohibited without the express written permission by EETI.

Disclaimer: EETI MAKES NO WARRANTY OF ANY KIND, EXPRESS OR IMPLIED, WITH REGARD TO PROGRAMS, INCLUDING, BUT NOT LIMITED TO, THE IMPLIED WARRANTIES OF MERCHANTABILITY AND FITNESS FOR A PARTICULAR PURPOSE. EETI reserves the right to make changes without further notice to the Programs described herein. Licensee agrees that EETI does not assume any liability, damages or costs, including but not limited to attorney fees, arising out from Programs themselves or those arising out from the application or combination Programs into other products or circuit. The use or the inclusion of EETI's Programs implies that the Licensee assumes all risk of such use and in doing so indemnifies EETI against all charges, including but not limited to any claims to infringement of any third party's intellectual property right.

Do you agree with above patent declaration?
 [Y] Yes, I agree.  [N] No, I don't agree.
y

(Q) Which interface controller do you use?
(I) [1] RS232 [2] USB [3] PS2 :


Which interface controller i should use btw? Dont wanna do a mistake.. Thank you in advance.

I continued clicking and he was asking me how many usb devices i have plugged in.
I pressed 1.
After the reboot, the  touchscreen dont work anymore.. :-/



Do you agree with above patent declaration?
 [Y] Yes, I agree.  [N] No, I don't agree.
y

(Q) Which interface controller do you use?
(I) [1] RS232 [2] USB [3] PS2 : 2
(I) Please confirm the touch controller is linked with your device. Press [Enter] key to continue..........

(I) Found /etc/rc.local file.
(I) Found a HID compliant touch controller.
(I) X.Org X server 1.11.3
(I) X verion is 1.7.6 upwards
(I) Found uinput at path /dev/uinput
(I) Place eGTouch driver archive to /usr/local/eGTouch32withX.
(I) Create eGTouch daemon shortcut in /usr/bin.
(I) Create eGTouchU tool shortcut in /usr/bin.
(I) Create eCalib tool shortcut in /usr/bin.
(I) Detach eGTouchD daemon execution from /etc/rc.local.
(I) Append eGTouch daemon execution into /etc/rc.local.

(Q) How many controllers do you want to plug-in to system? [1-10]
(I) Default [1]:

---

### Post by Favux on 2012-11-28
Looking good!  Nice work.  :)

Your touchscreen is usb so I would guess you want to tell it to use the usb controller.  And it only has the built-in touchscreen so you want to tell it 1 controller I guess.

Are you rebooting after each install?

---

### Post by Crazy Factory on 2012-11-28
But when i pressed 1 and rebooted it, the touchscreen did not work anymore :P:confused:

---

### Post by Favux on 2012-11-28
Hmmm.  It sure looks like you now have the driver installed.  Try rebooting a few times.

Also run **lsmod** in a terminal and see if the kernel driver is now in the output.

Now what do you see with **xinput list** and so on?

---

### Post by Crazy Factory on 2012-11-28
Yes i did reboot it..
I've tried to calibrate it after, but now the touchscreen is not working anymore, which is actually positive, but i want to make that touchscreen work :P

---

### Post by Crazy Factory on 2012-11-28
test@test-Lenovo-C200:~$ /home/test
bash: /home/test: Is a directory
test@test-Lenovo-C200:~$ ls
Desktop    Downloads              examples.desktop  Pictures  Templates
Documents  eGTouch_v2.5.2107.L-x  Music             Public    Videos
test@test-Lenovo-C200:~$ cd eGTouch_v2.5.2107.L-x
test@test-Lenovo-C200:~/eGTouch_v2.5.2107.L-x$ sudo sh setup.sh
[sudo] password for test: 


(*) Driver installer for touch controller 
(*) Script Version = 1.04.2013 

(I) Check user permission: root, you are the supervisor.
(I) Platform application binary interface = i686
(W) X server detected.

Declaration and Disclaimer
The programs, including but not limited to software and/or firmware (hereinafter referred to "Programs" or "PROGRAMS", are owned by eGalax_eMPIA Technology Inc. (hereinafter referred to EETI) and are compiled from EETI Source code. EETI hereby grants to licensee a personal, non-exclusive, non-transferable license to copy, use and create derivative works of Programs for the sole purpose in conjunction with an EETI Product, including but not limited to integrated circuit and/or controller. Any reproduction, copies, modification, translation, compilation, application, or representation of Programs except as specified above is prohibited without the express written permission by EETI.

Disclaimer: EETI MAKES NO WARRANTY OF ANY KIND, EXPRESS OR IMPLIED, WITH REGARD TO PROGRAMS, INCLUDING, BUT NOT LIMITED TO, THE IMPLIED WARRANTIES OF MERCHANTABILITY AND FITNESS FOR A PARTICULAR PURPOSE. EETI reserves the right to make changes without further notice to the Programs described herein. Licensee agrees that EETI does not assume any liability, damages or costs, including but not limited to attorney fees, arising out from Programs themselves or those arising out from the application or combination Programs into other products or circuit. The use or the inclusion of EETI's Programs implies that the Licensee assumes all risk of such use and in doing so indemnifies EETI against all charges, including but not limited to any claims to infringement of any third party's intellectual property right.

Do you agree with above patent declaration?
 [Y] Yes, I agree.  [N] No, I don't agree.
y

(Q) Which interface controller do you use?
(I) [1] RS232 [2] USB [3] PS2 : 2
(I) Please confirm the touch controller is linked with your device. Press [Enter] key to continue..........

(I) Found /etc/rc.local file.
(I) Found a HID compliant touch controller.
(I) X.Org X server 1.11.3
(I) X verion is 1.7.6 upwards
(I) Found uinput at path /dev/uinput
(I) Place eGTouch driver archive to /usr/local/eGTouch32withX.
(I) Create eGTouch daemon shortcut in /usr/bin.
(I) Create eGTouchU tool shortcut in /usr/bin.
(I) Create eCalib tool shortcut in /usr/bin.
(I) Detach eGTouchD daemon execution from /etc/rc.local.
(I) Append eGTouch daemon execution into /etc/rc.local.

(Q) How many controllers do you want to plug-in to system? [1-10]
(I) Default [1]:1
1
(I) Device Nums is set to 1
(W) Found udev rule: 52-egalax-virtual.conf.
(I) Create eGTouchU shortcut in application list.

(I) Driver installation completed. Setup version 1.04.2013.
(I) Please reboot the system.








xintest@test-Lenovo-C200:~$ xinput list
&#9121; Virtual core pointer                        id=2    [master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer                  id=4    [slave  pointer  (2)]
&#9116;   &#8627; USB Optical Mouse                           id=10    [slave  pointer  (2)]
&#9116;   &#8627; EETI virtual device                         id=12    [slave  pointer  (2)]
&#9123; Virtual core keyboard                       id=3    [master keyboard (2)]
    &#8627; Virtual core XTEST keyboard                 id=5    [slave  keyboard (3)]
    &#8627; Power Button                                id=6    [slave  keyboard (3)]
    &#8627; Power Button                                id=7    [slave  keyboard (3)]
    &#8627; Lenovo Lenovo Black Silk USB Keyboard       id=8    [slave  keyboard (3)]
    &#8627; Lenovo Lenovo Black Silk USB Keyboard       id=9    [slave  keyboard (3)]
    &#8627; Lenovo USB 2.0 UVC Camera                   id=11    [slave  keyboard (3)]
test@test-Lenovo-C200:~$








test@test-Lenovo-C200:~$ lsmod
Module                  Size  Used by
nls_utf8               12493  1 
isofs                  39553  1 
hid_multitouch         12851  0 
bnep                   17830  2 
rfcomm                 38139  0 
parport_pc             32114  0 
bluetooth             158438  10 bnep,rfcomm
ppdev                  12849  0 
snd_hda_codec_realtek   174313  1 
snd_hda_intel          32765  3 
snd_hda_codec         109562  2 snd_hda_codec_realtek,snd_hda_intel
snd_usb_audio         101566  1 
nvidia               8556879  0 
arc4                   12473  2 
joydev                 17393  0 
snd_hwdep              13276  2 snd_hda_codec,snd_usb_audio
snd_usbmidi_lib        24603  1 snd_usb_audio
ath9k                 117326  0 
snd_pcm                80845  3 snd_hda_intel,snd_hda_codec,snd_usb_audio
snd_seq_midi           13132  0 
snd_rawmidi            25424  2 snd_usbmidi_lib,snd_seq_midi
snd_seq_midi_event     14475  1 snd_seq_midi
mac80211              436455  1 ath9k
snd_seq                51567  2 snd_seq_midi,snd_seq_midi_event
snd_timer              28931  2 snd_pcm,snd_seq
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
i915                  419110  2 
usbhid                 41906  1 hid_multitouch
mac_hid                13077  0 
ath9k_common           13781  1 ath9k
uvcvideo               67203  0 
psmouse                86486  0 
ath9k_hw              391554  2 ath9k,ath9k_common
ath                    19387  3 ath9k,ath9k_common,ath9k_hw
snd                    62064  19 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_usb_audio,snd_hwdep,snd_usbmidi_lib,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
hid                    77392  3 hid_multitouch,usbhid
soundcore              14635  1 snd
videodev               86588  1 uvcvideo
serio_raw              13027  0 
snd_page_alloc         14108  2 snd_hda_intel,snd_pcm
cfg80211              178679  3 ath9k,mac80211,ath
drm_kms_helper         45466  1 i915
drm                   197599  3 i915,drm_kms_helper
i2c_algo_bit           13199  1 i915
lp                     17455  0 
video                  19068  1 i915
parport                40930  3 parport_pc,ppdev,lp
e100                   36289  0 
test@test-Lenovo-C200:~$

---

### Post by Favux on 2012-11-28
Looks correct so far.
> &#9116; &#8627; EETI virtual device id=12 [slave pointer (2)]
Is what the .pdf says to look for.

Looking at lsmod (list kernel modules/drivers) I see:
> 
hid_multitouch 12851 0
usbhid 41906 1 hid_multitouch
hid 77392 3 hid_multitouch,usbhid

Is that the problem?  The driver is looking for a multitouch touchscreen and yours is single touch?  I guess we have to read through the .pdf.  May have to change the udev rule or .ini file in /etc or something.

---

### Post by Crazy Factory on 2012-11-28
Yes, we've got single touch, not multi touch.
So, i am reading the PDF too, just having no idea really.
I am sitting here at my work place for days, and thank of you we go step by step forward :).
I hope really that we find a solution for it.
Thank you really much for your great support so far.
I hope we can finish this together soon.
I appreciate that.


Btw, under Windows 7 the touchscreen is working perfect, but i dont prefer Windows 7.

---

### Post by Crazy Factory on 2012-11-28
Hi, did you find a solution?

Best Regards

Markus

---

### Post by Favux on 2012-11-29
Sorry Markus, busy on another project.

Check in /etc/eGTouchL.ini and see if SupportPoints is set to 1 for single finger instead of something else like:
```
SupportPoints			5
```
If it isn't you can edit it with:
```
gksudo gedit /etc/eGTouchL.ini
```

---

### Post by Crazy Factory on 2012-12-06
Hello Favux, it's me again.

I've tried to do it like you told me, but when i am changing the "support points" to 1 and then saving the file, it's still the same problem.
I cant use the touchscreen.
I've tried to upgrade Ubuntu to 12.10, but still the same problem.
Or may i do something wrong?
It still shows me "Multitouch 0"

Thank you in advance.

Best Regards

Markus~

---

