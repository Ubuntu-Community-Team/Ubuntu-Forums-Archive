---
title: "N-trig Driver for Dell Latitude XT2 on Ubuntu 9.10"
date: 2010-02-14
forum: Hardware
---

### Post by -TJ on 2010-02-14
Hello. I am a new to Ubuntu, and I am quite excited in helping the community out. This is my first thread and I think it is my first or second post. 

I do have some problems, however. I have been doing extensive research on how to run pen, touch, and multi-touch on my Dell Latitude XT2 running on Ubuntu 9.10 x64.

Yes, there are many threads that are out there (for example, [**here**]("http://ubuntuforums.org/showthread.php?t=1252492")), yet I am somehow not understanding what to do. If I had concrete step-by-step directions, it would make life a whole lot easier.

How should I start out? Should I compile everything from the beginning? How do I use the files that are attached on the other threads (such as the patches)? I can only open them similar to text files. How do I run them? Sorry; I am quite frustrated with this. Let's not get overwhelmed with questions and start from the complete beginning.

I want everything to work and I tried to do many things but it hasn't really worked out. Let me get started creating a tutorial below. I also created a Wave for this located [**[COLOR="Red"]here[/COLOR]**]("http://wavedirectory.appspot.com/init/default/wave/676f6f676c65776176652e636f6d21772b476f64554435567041"). This can allow multiple users to work on the list in real-time. I will also be updating it from time to time, so it would be up-to-date.

---

### Post by -TJ on 2010-02-14
I'm a big fan of nicely organized directions that would exactly tell what the user should do. 
Once again, I have also created a Wave for this located [**[COLOR="Red"]here[/COLOR]**]("http://wavedirectory.appspot.com/init/default/wave/676f6f676c65776176652e636f6d21772b476f64554435567041"). This can allow multiple users to work on the list in real-time.

So lets me get it started:



001. fire up terminal
[INDENT]Applications > Accessories > Terminal[/INDENT]
002. update and upgrade everything
```
sudo apt-get update
sudo apt-get upgrade
```
003. 
004. 
005. 
006. 
007.


001. fire up terminal

Applications > Accessories > Terminal

002. update and upgrade everything

sudo apt-get update

sudo apt-get upgrade

003. check the kernel version is 2.6.31-17-generic

uname -r

004. open up Synaptic Package Manager using terminal

gksudo synaptic

005. install wacom-tools

006. download the xserver-xorg-input-wacom deb here

007.  

[**[COLOR="Red"][THIS GUIDE IS STILL IN PROGRESS][/COLOR]**]("http://wavedirectory.appspot.com/init/default/wave/676f6f676c65776176652e636f6d21772b476f64554435567041")

---

### Post by Favux on 2010-02-14
Hi -TJ,

So you're in the Karmic (9.10) release.  Let's get your exact kernel version.  Enter (copy and paste) in a terminal:
```
cat /proc/version_signature
```
By the way the release number means the year and month the release was released.  So 9.10 is October 20009.

Do you want to try Rafi Rubin's newly released hid-ntrig.ko, which is experiental, in that we haven't yet quite figured out how to get everything working?  Or do you want to use an older hid-ntrig.ko that we know works, but maybe not as well as the new one?

The hid-ntig.ko is the usb kernel driver/module for the N-trig 'digitizers'.

---

### Post by -TJ on 2010-02-14
Is this what you were asking for?

```
tj@xt2:~$ cat /proc/version_signature
cat: /proc/version_signature: No such file or directory

```

Let's go with the latest one. We'll see how it works out.

---

### Post by Favux on 2010-02-14
Nope, your Karmic must not have the file.  Try:
```
uname -r
```
Let's see which kernel you have first.

---

### Post by -TJ on 2010-02-14
Okay, here it is.

```
tj@xt2:~$ uname -r
2.6.31.5
```

---

### Post by Favux on 2010-02-14
Hi -TJ,

I think Karmic is up to kernel 2.6.31-17 currently.  So go to Update Manager in System > Administration and run it.  And then let's see which kernel you have.

---

### Post by -TJ on 2010-02-14
Sorry, I guess I was in the wrong kernel from start up.
I also checked for updates, and there were none.

```
tj@xt2:~$ uname -r
2.6.31-20-generic

```

Okay. I think I am ready.

---

### Post by Favux on 2010-02-14
Wow, 2.6.31-20-generic out already?  In your kernel list at start up is kernel 2.6.31-17 available?

---

### Post by -TJ on 2010-02-14
Yea. Now I'm on it.

```
tj@xt2:~$ uname -r
2.6.31-17-generic

```

---

### Post by Favux on 2010-02-14
Ok, I know you wanted to try Rafi's new hid-ntrig.ko but my suggestion is try an earlier version that we know works and see if you can get it set up.  That way you could spend a few days learning more about Ubuntu before trying Rafi's new one.  You'd need to be sure you keep booting into the 2.6.31-17-generic kernel.  What do you think?

So the first thing we could do is setup linuxwacom to recognize n-trig.  First check in Synaptic Package Manager that wacom-tools is installed.  If it isn't go ahead and install it.  We will try to save time by using tekknokrat's pre-packaged patched linuxwacom 0.8.4-1 deb.  It's linked in the HOW TO but here's the direct link:  [http://ubuntuforums.org/showpost.php?p=8079237&postcount=317](http://ubuntuforums.org/showpost.php?p=8079237&postcount=317)

Download (Save) the xserver-xorg-input-wacom deb (you shouldn't need the wacom-tools deb) onto your desktop.  Then double click on it and the Debian installer should install it for you.  Then reboot choosing the correct kernel.

---

### Post by -TJ on 2010-02-14
Sure! I'm fine with that.

When I double click on the installer, it gives me the following message:
```
Error: A later version is already installed
```

Should I continue anyways?
Wait. I can't install it.

So what I did is I went into Synaptic Package Manager and found that xserver-xorg-input-wacom was already installed. I then removed it and installed the xserver-xorg-input-wacom that the website provided. I will now reboot into the proper kernel

---

### Post by Favux on 2010-02-14
Oops!  An update came through for xserver-xorg-input-wacom?  Check in Synaptic Package Manager what the version is.  You could also try uninstalling it and then installing the deb.  But you might run into a problem with the xserver-input-all dependency.  If it turns into a hassle we'll just go ahead and patch and compile it.

---

### Post by -TJ on 2010-02-14
But the download isn't the latest version right?
Should we just compile it though?
I do know a little about compiling.

Or should we just continue and then compile it later?

---

### Post by Favux on 2010-02-14
> But the download isn't the latest version right?
It sounds like the Debian installer doesn't think so.  That's why I suggested checking out what Synaptic says.  But for you any small difference won't matter.  Your main concern is getting the patch that makes linuxwacom recognize the N-trig 'digitizer' into linuxwacom.  And if you can use the deb I thought it would be quicker and easier.

---

### Post by -TJ on 2010-02-14
Okay, what is the next step?

---

### Post by Favux on 2010-02-14
I'm guessing you removed xserver-xorg-input-wacom through Synaptic and installed the deb?

So the next step is to download the pre-compiled patched hid-ntrig.ko (64-bit 2.6.31-17-generic kernel version) by xopher_mc.  It's in [post #467]("http://ubuntuforums.org/showpost.php?p=8734898&postcount=467").  Save it to your desktop.

---

### Post by -TJ on 2010-02-14
Okay. What's next?

---

### Post by Favux on 2010-02-14
Now right click on the downloaded hid-ntrig.ko tar on your desktop and tell it to Extract Here (onto your desktop).  A new file called hid-ntrig.ko should appear.

Then in a terminal enter the following commands:
```
cd ./Desktop

sudo cp hid-ntrig.ko /lib/modules/`uname -r`/kernel/drivers/hid/

sudo depmod -a

```

And then reboot.

cd ./Desktop - cd is change directory to Desktop

sudo cp hid-ntrig.ko /lib/modules/`uname -r`/kernel/drivers/hid/ - sudo makes you super user/root so you can change system files.  cp is the copy command and the rest is the file you want to copy and the directory it goes to.

sudo depmod -a - 'depmod -a' rebuilds all the kernel module dependencies.

---

### Post by -TJ on 2010-02-14
Okay. Everything worked out perfectly.

```
tj@xt2:~$ cd ./Desktop
tj@xt2:~/Desktop$ sudo cp hid-ntrig.ko /lib/modules/`uname -r`/kernel/drivers/hid/
[sudo] password for tj: 
tj@xt2:~/Desktop$ sudo depmod -a

```

---

### Post by Favux on 2010-02-14
Great!  You're there.  All you need is to make the modifications to xorg.conf.

Go over '3) The xorg.conf' especially paying attention to backing it up and restoring it.  Also look at the by-path for the XT2 based on firmware (windows version).  Then download the xorg.conf and eyeball it and compare it to what you have (if anything).  So I'm asking you to spend some time looking at all that before we do anything with it.

You could check your 10-linuxwacom.fdi and make sure there isn't any n-trig stuff in it.  I don't think there should be in Karmic.

---

### Post by -TJ on 2010-02-14
You said to go over to '3) The xorg.conf'. What does that mean? Where is it located? What by-path basted on the windows firmware? Where do I download xorg.conf? How do I compare it? Should I compare the versions?

How do I check my 10-linuxwacom.fdi? What is that, anyways?

Can you please give concrete directions?

---

### Post by Favux on 2010-02-14
Sorry.  '3) The xorg.conf' is a section on the [N-trig HOW TO]("http://ubuntuforums.org/showpost.php?p=7863677&postcount=1").  Let's start with that.

---

### Post by -TJ on 2010-02-14
Okay, so I did the following:

```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.bak
```

Then it is talking about a path change for the Dell Latitude XT2. I don't really understand what it being asked. What should I do?

---

### Post by Favux on 2010-02-14
Now you can use Nautilus/Places to navigate to where the xorg.conf should be since you now know the location '/etc/X11/xorg.conf'.  See if it is there and if so what's in it.  Then download the xorg.conf attached to the bottom of the HOW TO.  Take a look at it and decide what changes you'll need to make.  If you think you have a handle on it you can post your xorg.conf and proposed xorg.conf and we can review it.

Edit:  To look at a file in gedit (the text editor) just right click on it and tell it to open in gedit.  If the file ends in .txt you can just dbl-click on it and it should open in gedit automatically.

---

### Post by -TJ on 2010-02-14
It says "The xorg.conf, called "TX2z & XT's_Jaunty_xorg.conf" is attached below and should complete setting up the stylus and touch in Jaunty." That isn't for Karmic.

Edit:  What changes do I need to make anyways? I feel so confused. =(

By the way, can we temporarily use some other form of communication? Such as some chat thing or something? I can post what we discussed back onto this thread so others can see it.

Do you have a Google Wave account?

---

### Post by Favux on 2010-02-14
Hi -TJ,

Sorry, no Google Wave and I never use chat.  Ain't I a dinosaur?

Anyway that's the right xorg.conf.  It works for Karmic too, it was just developed in Jaunty before Karmic came out.  Speaking of dinosaurs.

Do you have an xorg.conf?  It seems like most folks with Intel video (that's what the XT2 has, correct?) don't have one in Karmic.

---

### Post by -TJ on 2010-02-14
> Do you have an xorg.conf?  It seems like most folks with Intel video (that's what the XT2 has, correct?) don't have one in Karmic.

What do you mean? It's in the /etc/X11 folder...

---

### Post by Favux on 2010-02-14
Hi -TJ,

Fine.  If it's there I need to see what's in it.  If you open it up in gedit you can copy everything in it and box the contents using the code tags (# on upper right).  Then I can help you modify it.  We're almost there!

---

### Post by -TJ on 2010-02-15
I tried to do it myself but I totally messed up! When I rebooted, the screen stayed blank with two white line segments on the top. So I had to go into the recovery mode thing and because I remembered the "sudo cp /etc/X11/xorg.conf.bak /etc/X11/xorg.conf" command to restore it, I am now safe and I can try it over again! Backing up the current xorg.conf was a smart idea. I never knew terminal could be so powerful!

Anyways...
My original xorg.conf that my XT2 has is the following:
```
Section "ServerLayout"
	Identifier     "X.org Configured"
	InputDevice    "stylus"
	InputDevice    "touch"
EndSection

Section "InputDevice"
	Identifier  "touch"
	Driver      "wacom"
	Option	    "Mode" "Absolute"
	Option	    "Type" "touch"
	Option	    "Device" "/dev/input/by-path/pci-0000:00:14.5-usb-0:2:1.1-event-mouse"
	Option	    "MaxX" "9600"
	Option	    "MaxY" "7200"
	Option	    "ResX" "1280"
	Option	    "ResY" "800"
	Option	    "Touch" "on"
	Option	    "USB" "on"
	Option	    "TopX" "0"
	Option	    "TopY" "0"
	Option	    "BottomX" "9600"
	Option	    "BottomY" "7200"
	Option	    "Buttons" "5"
	Option	    "Button1" "1"
	Option	    "Button10" "1"
EndSection

Section "InputDevice"
	Identifier  "stylus"
	Driver      "wacom"
	Option	    "Mode" "Absolute"
	Option	    "Type" "stylus"
	Option	    "Device" "/dev/input/by-path/pci-0000:00:14.5-usb-0:2:1.1-event-mouse"
	Option	    "MaxX" "9600"
	Option	    "MaxY" "7200"
	Option	    "ResX" "1280"
	Option	    "ResY" "800"
	Option	    "Button2" "3"
	Option	    "USB" "on"
EndSection
```

---

### Post by Favux on 2010-02-15
Outstanding work to recover!  I was going to remind you to write down the restore command so it was handy.

Very interesting because that is more like a Rafi Rubin XT xorg.conf.  Did you install this xorg.conf and forgot about it?  Looking at it, it seems to me your fresh Karmic install probably didn't have and xorg.conf.  Let me look at it and see what I can come up with.  And good job boxing the xorg.conf!  :)

Meanwhile it would help if you could post the output of the following command:
```
ls -l /dev/input/by-path
```

---

### Post by -TJ on 2010-02-15
Here you go.

```
tj@xt2:~$ ls -l /dev/input/by-path
total 0
lrwxrwxrwx 1 root root  9 2010-02-15 00:03 pci-0000:00:1a.0-usb-0:2.1:1.0-event-kbd -> ../event7
lrwxrwxrwx 1 root root  9 2010-02-15 00:03 pci-0000:00:1d.1-usb-0:2:1.0-event-mouse -> ../event8
lrwxrwxrwx 1 root root  9 2010-02-15 00:03 pci-0000:00:1d.1-usb-0:2:1.0-mouse -> ../mouse1
lrwxrwxrwx 1 root root  9 2010-02-15 00:03 pci-0000:00:1d.1-usb-0:2:1.1-event-mouse -> ../event9
lrwxrwxrwx 1 root root  9 2010-02-15 00:03 pci-0000:00:1d.1-usb-0:2:1.1-mouse -> ../mouse2
lrwxrwxrwx 1 root root  9 2010-02-15 00:03 platform-i8042-serio-0-event-kbd -> ../event4
lrwxrwxrwx 1 root root 10 2010-02-15 00:03 platform-i8042-serio-1-event-mouse -> ../event16
lrwxrwxrwx 1 root root  9 2010-02-15 00:03 platform-i8042-serio-1-mouse -> ../mouse3

```

What happened was that I tried to uncomment and comment the things by myself, and it didn't work right, so what you see is the original one, but the one that messed up is shown below:

```
# xorg.conf (X.Org X Window System server configuration file)
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

# Setup for HP TX2z.  Switch comments if you have the Dell Latitude XT or XT2.

Section "InputDevice"
	Identifier	"stylus"
	Driver		"wacom"
#   The by-path below is for the HP TX2z with Vista firmware
#	Option "Device" "/dev/input/by-path/pci-0000:00:14.5-usb-0:2:1.0-event-mouse"
#   The by-path below is for the Dell Latitude XT & XT2 with Vista firmware
	Option "Device" "/dev/input/by-path/pci-0000:00:13.1-usb-0:2:1.0-event-mouse"
	Option		"Type"		"stylus"
	Option		"USB"		"on"
	Option		"Button2"	"3"	# make stylus button R mouse click
EndSection

#   Remove the comments below if you have an eraser.  Dell XT & XT2?
Section "InputDevice"
	Identifier	"eraser"
	Driver		"wacom"
#   The by-path below is for the Dell Latitude XT & XT2 with Vista firmware
	Option "Device" "/dev/input/by-path/pci-0000:00:13.1-usb-0:2:1.0-event-mouse"
	Option		"Type"		"eraser"
	Option		"USB"		"on"
EndSection

Section "InputDevice"
	Identifier	"touch"
	Driver		"wacom"
#   The by-path below is for the HP TX2z with Vista firmware
#	Option "Device" "/dev/input/by-path/pci-0000:00:14.5-usb-0:2:1.0-event-mouse"
#   The by-path below is for the Dell Latitude XT & XT2 with Vista firmware
	Option "Device" "/dev/input/by-path/pci-0000:00:13.1-usb-0:2:1.0-event-mouse"
	Option		"Type"		"touch"
	Option		"USB"		"on"
	Option		"Touch"		"on"
	Option		"TopX"		"0"
	Option		"TopY"		"0"
	Option		"BottomX"	"9600"
	Option		"BottomY"	"7200"
EndSection

Section "Device"
	Identifier	"Configured Video Device"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	Identifier	"X.org Configured"
	InputDevice	"stylus"	"SendCoreEvents"
#   Remove the comment below if you have an eraser.
	InputDevice	"eraser"	"SendCoreEvents"
	InputDevice	"touch"		"SendCoreEvents"
EndSection

#   Developed with Ayuthia (using Rafi Rubin's Wacom sections as a starting point).
```

---

### Post by Favux on 2010-02-15
Thaks for the output.  We're about there.  Just one more question.  What was/is the latest version of Windows you have installed?  Vista, Win RC7, or Win7.  If you told me I forgot and I just skimmed through the thread.

The reason that xorg.conf works is that the usb pci by-paths aren't related to the XT2's according to your output, so they don't do anything.

---

### Post by -TJ on 2010-02-15
The last version I had was Win7 But my computer came with Vista.

---

### Post by Favux on 2010-02-15
OK, that was crucial.  If you had Win7 installed you have the Win7 firmware and unless you deliberately rolled the firmware version back that's what you have.  Alrighty, give me a couple of minutes.

---

### Post by -TJ on 2010-02-15
Oh okay. Because I did update my BIOS for Win7 and stuff. And I did update everything to Win7 when I was using it. (until Win7 crashed and then I switched to Ubuntu)

---

### Post by Favux on 2010-02-15
Here we go!  Be ready to restore from the command line like before if X breaks.

For this version only the stylus should work.  Touch is commented (#) out.  Notice it is also commented out in "ServerLayout" too.  I've also commented out "SendCoreEvents" for everything including the stylus.  That's because some systems seem to have trouble with it.  It should be the default and if your XT2 can handle it I think it makes things more stable.

Just replace the entire contents of your xorg.conf with this one.  And then reboot.

---

### Post by -TJ on 2010-02-15
The stylus works, but its really jerky and it can't go to the corners of the screen, like the top bottom left or right edges at all. When I hold the erase button, the thing freezes. And the right-click button doesn't work.

Can you make a "touch" only version?
And then can we try to make a "pen and touch" version?

---

### Post by Favux on 2010-02-15
No, don't worry, that's because the coordinates are in touch.  The important thing is:

**[SIZE="3"]It Works!!![/SIZE]**

Couple of more minutes everything should.  Now let's see if we can use "SendCoreEvents".  Change:
```
	InputDevice	"stylus"	#	"SendCoreEvents"
```
to
```
	InputDevice	"stylus"	"SendCoreEvents"
```
in "ServerLayout" and reboot.

---

### Post by -TJ on 2010-02-15
Okay. What is the next step?

---

### Post by Favux on 2010-02-15
Great!  Now touch.

In the touch section remove the comment from in front of the Win7 firmware usb pci by-path line.  So:
```
#	Option "Device" "/dev/input/by-path/pci-0000:00:1d.1-usb-0:2:1.1-event-mouse"
```
to
```
	Option "Device" "/dev/input/by-path/pci-0000:00:1d.1-usb-0:2:1.1-event-mouse"
```
And then in "ServerLayout" change:
```
#	InputDevice	"touch"		#	"SendCoreEvents"
```
to
```
	InputDevice	"touch"		"SendCoreEvents"
```
and reboot.

---

### Post by -TJ on 2010-02-15
The thing is really strange! When I did what you told me, after reboot, neither pen nor touch worked.

So I tinkered with the xorg.conf file. This time, instead of uncommenting the touch thing for Win7, I uncommented the Vista one.

So the xorg.conf file looks like this:

```
# xorg.conf (X.Org X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the xorg.conf manual page.
# (Type "man xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# Note that some configuration settings that could be done previously
# in this file, now are automatically configured by the server and settings
# here are ignored.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

# Setup for the Dell XT2 in Karmic.

Section "InputDevice"
	Identifier	"stylus"
	Driver		"wacom"
#   The by-path below is for the Dell Latitude XT2 with Vista firmware
#	Option "Device" "/dev/input/by-path/pci-0000:00:1d.1-usb-0:2:1.0-event-mouse"
#   The by-path below is for the Dell Latitude XT2 with Win7 firmware
	Option "Device" "/dev/input/by-path/pci-0000:00:1d.1-usb-0:2:1.1-event-mouse"
	Option		"Type"		"stylus"
	Option		"USB"		"on"
	Option		"Button2"	"3"	# make stylus button R mouse click
EndSection

#   Remove the comments below if you have an eraser.  Dell XT & XT2?
#Section "InputDevice"
#	Identifier	"eraser"
#	Driver		"wacom"
#   The by-path below is for the Dell Latitude XT2 with Vista firmware
#	Option "Device" "/dev/input/by-path/pci-0000:00:1d.1-usb-0:2:1.0-event-mouse"
#   The by-path below is for the Dell Latitude XT2 with Win7 firmware
#	Option "Device" "/dev/input/by-path/pci-0000:00:1d.1-usb-0:2:1.1-event-mouse"
#	Option		"Type"		"eraser"
#	Option		"USB"		"on"
#EndSection

Section "InputDevice"
	Identifier	"touch"
	Driver		"wacom"
#   The by-path below is for the Dell Latitude XT2 with Vista firmware
	Option "Device" "/dev/input/by-path/pci-0000:00:1d.1-usb-0:2:1.0-event-mouse"
#   The by-path below is for the Dell Latitude XT2 with Win7 firmware
#	Option "Device" "/dev/input/by-path/pci-0000:00:1d.1-usb-0:2:1.1-event-mouse"
	Option		"Type"		"touch"
	Option		"USB"		"on"
	Option		"Touch"		"on"
	Option		"TopX"		"0"
	Option		"TopY"		"0"
	Option		"BottomX"	"9600"
	Option		"BottomY"	"7200"
EndSection

Section "ServerLayout"
	Identifier	"X.org Configured"
	InputDevice	"stylus"		"SendCoreEvents"
#   Remove the comment below if you have an eraser.
#	InputDevice	"eraser"	#	"SendCoreEvents"
	InputDevice	"touch"			"SendCoreEvents"
EndSection

#   Developed with Ayuthia (using Rafi Rubin's Wacom sections as a starting point).
```

After reboot, the touch still doesn't work but the pen does again. Does this have any significance?

---

### Post by Favux on 2010-02-15
Good, I was worried cause that seemed to take longer than I thought.

It's telling us both channels are active.  It may be that we have to use a different line for touch or that something other than the linuxwacom driver has grabbed your digitizer and is messing with us.

What does the output of:
```
xinput --list
```
look like?  You could try both paths.

---

### Post by -TJ on 2010-02-15
Here it is:

```
tj@xt2:~$ xinput --list
"Virtual core pointer"	id=0	[XPointer]
	Num_buttons is 32
	Num_axes is 2
	Mode is Relative
	Motion_buffer is 256
	Axis 0 :
		Min_value is -1
		Max_value is -1
		Resolution is 0
	Axis 1 :
		Min_value is -1
		Max_value is -1
		Resolution is 0
"Virtual core keyboard"	id=1	[XKeyboard]
	Num_keys is 248
	Min_keycode is 8
	Max_keycode is 255
"stylus"	id=2	[XExtensionKeyboard]
	Type is Wacom Stylus
	Num_keys is 248
	Min_keycode is 8
	Max_keycode is 255
	Num_buttons is 5
	Num_axes is 6
	Mode is Absolute
	Motion_buffer is 256
	Axis 0 :
		Min_value is 0
		Max_value is 9600
		Resolution is 1122
	Axis 1 :
		Min_value is 0
		Max_value is 7200
		Resolution is 935
	Axis 2 :
		Min_value is 0
		Max_value is 256
		Resolution is 1
	Axis 3 :
		Min_value is -64
		Max_value is 63
		Resolution is 1
	Axis 4 :
		Min_value is -64
		Max_value is 63
		Resolution is 1
	Axis 5 :
		Min_value is 0
		Max_value is 1023
		Resolution is 1
"Dell WMI hotkeys"	id=3	[XExtensionKeyboard]
	Type is KEYBOARD
	Num_keys is 248
	Min_keycode is 8
	Max_keycode is 255
"HID 413c:8161"	id=4	[XExtensionKeyboard]
	Type is KEYBOARD
	Num_keys is 248
	Min_keycode is 8
	Max_keycode is 255
"Video Bus"	id=5	[XExtensionKeyboard]
	Type is KEYBOARD
	Num_keys is 248
	Min_keycode is 8
	Max_keycode is 255
"Video Bus"	id=6	[XExtensionKeyboard]
	Type is KEYBOARD
	Num_keys is 248
	Min_keycode is 8
	Max_keycode is 255
"AT Translated Set 2 keyboard"	id=7	[XExtensionKeyboard]
	Type is KEYBOARD
	Num_keys is 248
	Min_keycode is 8
	Max_keycode is 255
"Sleep Button"	id=8	[XExtensionKeyboard]
	Type is KEYBOARD
	Num_keys is 248
	Min_keycode is 8
	Max_keycode is 255
"Power Button"	id=9	[XExtensionKeyboard]
	Type is KEYBOARD
	Num_keys is 248
	Min_keycode is 8
	Max_keycode is 255
"PS/2 Generic Mouse"	id=10	[XExtensionPointer]
	Type is MOUSE
	Num_buttons is 5
	Num_axes is 2
	Mode is Relative
	Motion_buffer is 256
	Axis 0 :
		Min_value is -1
		Max_value is -1
		Resolution is 1
	Axis 1 :
		Min_value is -1
		Max_value is -1
		Resolution is 1
"Macintosh mouse button emulation"	id=11	[XExtensionPointer]
	Type is MOUSE
	Num_buttons is 5
	Num_axes is 2
	Mode is Relative
	Motion_buffer is 256
	Axis 0 :
		Min_value is -1
		Max_value is -1
		Resolution is 1
	Axis 1 :
		Min_value is -1
		Max_value is -1
		Resolution is 1
"HID 1b96:0001"	id=12	[XExtensionPointer]
	Type is TOUCHPAD
	Num_buttons is 5
	Num_axes is 8
	Mode is Absolute
	Motion_buffer is 256
	Axis 0 :
		Min_value is 0
		Max_value is 9600
		Resolution is 10000
	Axis 1 :
		Min_value is 0
		Max_value is 7200
		Resolution is 10000
	Axis 2 :
		Min_value is 0
		Max_value is 256
		Resolution is 10000
	Axis 3 :
		Min_value is 0
		Max_value is 1
		Resolution is 10000
	Axis 4 :
		Min_value is 0
		Max_value is 1
		Resolution is 10000
	Axis 5 :
		Min_value is 0
		Max_value is 1
		Resolution is 10000
	Axis 6 :
		Min_value is 0
		Max_value is 9600
		Resolution is 10000
	Axis 7 :
		Min_value is 0
		Max_value is 7200
		Resolution is 10000
"HID 1b96:0001"	id=13	[XExtensionKeyboard]
	Type is Wacom Stylus
	Num_keys is 248
	Min_keycode is 8
	Max_keycode is 255
	Num_buttons is 5
	Num_axes is 6
	Mode is Absolute
	Motion_buffer is 256
	Axis 0 :
		Min_value is 0
		Max_value is 9600
		Resolution is 1122
	Axis 1 :
		Min_value is 0
		Max_value is 7200
		Resolution is 935
	Axis 2 :
		Min_value is 0
		Max_value is 256
		Resolution is 1
	Axis 3 :
		Min_value is -64
		Max_value is 63
		Resolution is 1
	Axis 4 :
		Min_value is -64
		Max_value is 63
		Resolution is 1
	Axis 5 :
		Min_value is 0
		Max_value is 1023
		Resolution is 1

```

---

### Post by Favux on 2010-02-15
Hi -TJ,

OK, it looks like the Synaptic .fdi/driver is grabbing touch.  So change both by-path lines to the Win7 version.  I think stylus may be coming through that one.

We'll try altering the Synaptic .fdi so it isn't so grabby.  You nest a second set of match lines for the Synaptic .fdi.  It's called "11-x11-synaptics.fdi" and it's located at "/usr/share/hal/fdi/policy/20thirdparty/".  Add:
```
    <match key="info.product" contains="Synaptics">

    </match>
```
So it looks like:
```
<?xml version="1.0" encoding="ISO-8859-1"?>
<deviceinfo version="0.2">
  <device>
    <match key="info.capabilities" contains="input.touchpad">
    <match key="info.product" contains="Synaptics">

......

    </match>
    </match>
  </device>
</deviceinfo>
```

Use:
```
gksudo gedit /usr/share/hal/fdi/policy/20thirdparty/11-x11-synaptics.fdi
```
to edit, and then reboot.

---

### Post by -TJ on 2010-02-15
So does it look like this?

```
<?xml version="1.0" encoding="ISO-8859-1"?>
<deviceinfo version="0.2">
  <device>
    <match key="info.capabilities" contains="input.touchpad">
    <match key="info.product" contains="Synaptics">
        <merge key="input.x11_driver" type="string">synaptics</merge>
        <!-- Arbitrary options can be passed to the driver using
             the input.x11_options property since xorg-server-1.5. -->
        <!-- EXAMPLES:
        Switch on shared memory, enables the driver to be configured at runtime
	<merge key="input.x11_options.SHMConfig" type="string">true</merge>

	Maximum movement of the finger for detecting a tap
	<merge key="input.x11_options.MaxTapMove" type="string">2000</merge>

	Enable vertical scrolling when dragging along the right edge
	<merge key="input.x11_options.VertEdgeScroll" type="string">true</merge>

	Enable vertical scrolling when dragging with two fingers anywhere on the touchpad
	<merge key="input.x11_options.VertTwoFingerScroll" type="string">true</merge>

	Enable horizontal scrolling when dragging with two fingers anywhere on the touchpad
	<merge key="input.x11_options.HorizTwoFingerScroll" type="string">true</merge>

	If on, circular scrolling is used
	<merge key="input.x11_options.CircularScrolling" type="string">true</merge>

	For other possible options, check CONFIGURATION DETAILS in synaptics man page
        -->
        <match key="/org/freedesktop/Hal/devices/computer:system.hardware.product" string="Inspiron 1011">
            <merge key="input.x11_options.JumpyCursorThreshold" type="string">90</merge>
            <merge key="input.x11_options.AreaBottomEdge" type="string">4100</merge>
        </match>
        <match key="/org/freedesktop/Hal/devices/computer:system.hardware.product" string="Inspiron 1012">
            <merge key="input.x11_options.JumpyCursorThreshold" type="string">90</merge>
            <merge key="input.x11_options.AreaBottomEdge" type="string">4100</merge>
        </match>
        <match key="/org/freedesktop/Hal/devices/computer:system.hardware.product" string="HP MiniNote 1000">
            <merge key="input.x11_options.JumpyCursorThreshold" type="string">200</merge>
        </match>
    </match>
    </match>
  </device>
</deviceinfo>
```


If it does, what should I do after rebooting?

---

### Post by Favux on 2010-02-15
That looks good.  Well if you have stylus and touch both on the Win7 line I'm hoping they work after you reboot.  If not we can look at 'xinput --list' again.

---

### Post by -TJ on 2010-02-15
Nope. Touch still isn't working.

Hey, is it okay if we can continue tomorrow?
Ask me if you need any of my files or more information so you can look at it while I'm gone.

---

### Post by Favux on 2010-02-15
Darn!  Ok, then along with xinput we probably will need to look at Xorg.0.log.  It is in "/var/log".  To upload it right click on it and compress it with Create Archive.  Then use Manage Attachments (below) to upload it.

I doubt I'll get to it tonight.

---

### Post by -TJ on 2010-02-15
Don't worry. Take your time. Take as looong as you want. =]

Here is xinput:
```
tj@xt2:~$ xinput --list
"Virtual core pointer"	id=0	[XPointer]
	Num_buttons is 32
	Num_axes is 2
	Mode is Relative
	Motion_buffer is 256
	Axis 0 :
		Min_value is -1
		Max_value is -1
		Resolution is 0
	Axis 1 :
		Min_value is -1
		Max_value is -1
		Resolution is 0
"Virtual core keyboard"	id=1	[XKeyboard]
	Num_keys is 248
	Min_keycode is 8
	Max_keycode is 255
"stylus"	id=2	[XExtensionKeyboard]
	Type is Wacom Stylus
	Num_keys is 248
	Min_keycode is 8
	Max_keycode is 255
	Num_buttons is 5
	Num_axes is 6
	Mode is Absolute
	Motion_buffer is 256
	Axis 0 :
		Min_value is 0
		Max_value is 9600
		Resolution is 1122
	Axis 1 :
		Min_value is 0
		Max_value is 7200
		Resolution is 935
	Axis 2 :
		Min_value is 0
		Max_value is 256
		Resolution is 1
	Axis 3 :
		Min_value is -64
		Max_value is 63
		Resolution is 1
	Axis 4 :
		Min_value is -64
		Max_value is 63
		Resolution is 1
	Axis 5 :
		Min_value is 0
		Max_value is 1023
		Resolution is 1
"touch"	id=3	[XExtensionKeyboard]
	Type is Wacom Touch
	Num_keys is 248
	Min_keycode is 8
	Max_keycode is 255
	Num_buttons is 5
	Num_axes is 6
	Mode is Absolute
	Motion_buffer is 256
	Axis 0 :
		Min_value is 0
		Max_value is 9600
		Resolution is 0
	Axis 1 :
		Min_value is 0
		Max_value is 7200
		Resolution is 0
	Axis 2 :
		Min_value is 0
		Max_value is 256
		Resolution is 1
	Axis 3 :
		Min_value is -64
		Max_value is 63
		Resolution is 1
	Axis 4 :
		Min_value is -64
		Max_value is 63
		Resolution is 1
	Axis 5 :
		Min_value is 0
		Max_value is 1023
		Resolution is 1
"HID 413c:8161"	id=4	[XExtensionKeyboard]
	Type is KEYBOARD
	Num_keys is 248
	Min_keycode is 8
	Max_keycode is 255
"Sleep Button"	id=5	[XExtensionKeyboard]
	Type is KEYBOARD
	Num_keys is 248
	Min_keycode is 8
	Max_keycode is 255
"AT Translated Set 2 keyboard"	id=6	[XExtensionKeyboard]
	Type is KEYBOARD
	Num_keys is 248
	Min_keycode is 8
	Max_keycode is 255
"Video Bus"	id=7	[XExtensionKeyboard]
	Type is KEYBOARD
	Num_keys is 248
	Min_keycode is 8
	Max_keycode is 255
"Dell WMI hotkeys"	id=8	[XExtensionKeyboard]
	Type is KEYBOARD
	Num_keys is 248
	Min_keycode is 8
	Max_keycode is 255
"Power Button"	id=9	[XExtensionKeyboard]
	Type is KEYBOARD
	Num_keys is 248
	Min_keycode is 8
	Max_keycode is 255
"Video Bus"	id=10	[XExtensionKeyboard]
	Type is KEYBOARD
	Num_keys is 248
	Min_keycode is 8
	Max_keycode is 255
"PS/2 Generic Mouse"	id=11	[XExtensionPointer]
	Type is MOUSE
	Num_buttons is 5
	Num_axes is 2
	Mode is Relative
	Motion_buffer is 256
	Axis 0 :
		Min_value is -1
		Max_value is -1
		Resolution is 1
	Axis 1 :
		Min_value is -1
		Max_value is -1
		Resolution is 1
"Macintosh mouse button emulation"	id=12	[XExtensionPointer]
	Type is MOUSE
	Num_buttons is 5
	Num_axes is 2
	Mode is Relative
	Motion_buffer is 256
	Axis 0 :
		Min_value is -1
		Max_value is -1
		Resolution is 1
	Axis 1 :
		Min_value is -1
		Max_value is -1
		Resolution is 1
"HID 1b96:0001"	id=13	[XExtensionPointer]
	Type is TOUCHPAD
	Num_buttons is 5
	Num_axes is 8
	Mode is Absolute
	Motion_buffer is 256
	Axis 0 :
		Min_value is 0
		Max_value is 9600
		Resolution is 10000
	Axis 1 :
		Min_value is 0
		Max_value is 7200
		Resolution is 10000
	Axis 2 :
		Min_value is 0
		Max_value is 256
		Resolution is 10000
	Axis 3 :
		Min_value is 0
		Max_value is 1
		Resolution is 10000
	Axis 4 :
		Min_value is 0
		Max_value is 1
		Resolution is 10000
	Axis 5 :
		Min_value is 0
		Max_value is 1
		Resolution is 10000
	Axis 6 :
		Min_value is 0
		Max_value is 9600
		Resolution is 10000
	Axis 7 :
		Min_value is 0
		Max_value is 7200
		Resolution is 10000
"HID 1b96:0001"	id=14	[XExtensionKeyboard]
	Type is Wacom Stylus
	Num_keys is 248
	Min_keycode is 8
	Max_keycode is 255
	Num_buttons is 5
	Num_axes is 6
	Mode is Absolute
	Motion_buffer is 256
	Axis 0 :
		Min_value is 0
		Max_value is 9600
		Resolution is 1122
	Axis 1 :
		Min_value is 0
		Max_value is 7200
		Resolution is 935
	Axis 2 :
		Min_value is 0
		Max_value is 256
		Resolution is 1
	Axis 3 :
		Min_value is -64
		Max_value is 63
		Resolution is 1
	Axis 4 :
		Min_value is -64
		Max_value is 63
		Resolution is 1
	Axis 5 :
		Min_value is 0
		Max_value is 1023
		Resolution is 1

```

And the file full of logs are attached too.
Do you need anything else before I leave?

---

### Post by Favux on 2010-02-18
Hi -TJ,

Thanks for being so thorough.  Usually I'm just looking for the Xorg.0.log but your Xorg.0.log.old showed the Wacom driver not attaching when it seemed to on the Xorg.0.log.

Hmmm.  I think we've confirmed you do have the Win7 firmware.  Did you manage to figure out what Windows is calling your n-trig firmware in Control Panel?

Anyway when you boot do you have the option to select the 64-bit 2.6.31-16-generic kernel?  Ayuthia posted a pre-compiled hid-ntrig.ko for Win7 firmware for that kernel.  Otherwise you'll have to compile a hid-ntrig.ko for the 2.6.31-17-generic kernel.

Oh, and by the way to determine if you are on 32 or 64-bit:
```
uname -m
```

---

### Post by -TJ on 2010-02-19
What do you mean by "what Windows is calling your n-trig firmware in Control Panel"?
Do you mean what version did I use?

I can try using 2.6.31-16-generic ... 
but wouldn't it be better if we just compiled it?

```
tj@xt2:~$ uname -m
x86_64

```

---

### Post by Favux on 2010-02-19
I'm asking did you find out where in Control Panel your N-trig firmware version is listed (Devices?) and if so what is it?  For a list of firmware versions see the [ENAC site]("http://lii-enac.fr/en/projects/shareit/ntrig.html").
> wouldn't it be better if we just compiled it?
Yes.  Ayuthia's instructions are at:  [http://linuxfans.keryxproject.org/?page_id=23](http://linuxfans.keryxproject.org/?page_id=23)  It is my understanding that his ntrig-v6.tar.bz2 supports Win7 firmware.

---

### Post by -TJ on 2010-02-19
Here, I think this will help:

```
tj@xt2:~$ sudo lsusb -v
[sudo] password for tj: 

Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               2.00
  bDeviceClass            9 Hub
  bDeviceSubClass         0 Unused
  bDeviceProtocol         0 Full speed (or root) hub
  bMaxPacketSize0        64
  idVendor           0x1d6b Linux Foundation
  idProduct          0x0002 2.0 root hub
  bcdDevice            2.06
  iManufacturer           3 Linux 2.6.31-20-generic ehci_hcd
  iProduct                2 EHCI Host Controller
  iSerial                 1 0000:00:1a.7
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength           25
    bNumInterfaces          1
    bConfigurationValue     1
    iConfiguration          0 
    bmAttributes         0xe0
      Self Powered
      Remote Wakeup
    MaxPower                0mA
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       0
      bNumEndpoints           1
      bInterfaceClass         9 Hub
      bInterfaceSubClass      0 Unused
      bInterfaceProtocol      0 Full speed (or root) hub
      iInterface              0 
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x81  EP 1 IN
        bmAttributes            3
          Transfer Type            Interrupt
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0004  1x 4 bytes
        bInterval              12
Hub Descriptor:
  bLength               9
  bDescriptorType      41
  nNbrPorts             6
  wHubCharacteristic 0x000a
    No power switching (usb 1.0)
    Per-port overcurrent protection
  bPwrOn2PwrGood       10 * 2 milli seconds
  bHubContrCurrent      0 milli Ampere
  DeviceRemovable    0x00
  PortPwrCtrlMask    0xff
 Hub Port Status:
   Port 1: 0000.0100 power
   Port 2: 0000.0100 power
   Port 3: 0000.0100 power
   Port 4: 0000.0100 power
   Port 5: 0000.0100 power
   Port 6: 0000.0100 power
Device Status:     0x0003
  Self Powered
  Remote Wakeup Enabled

Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               1.10
  bDeviceClass            9 Hub
  bDeviceSubClass         0 Unused
  bDeviceProtocol         0 Full speed (or root) hub
  bMaxPacketSize0        64
  idVendor           0x1d6b Linux Foundation
  idProduct          0x0001 1.1 root hub
  bcdDevice            2.06
  iManufacturer           3 Linux 2.6.31-20-generic uhci_hcd
  iProduct                2 UHCI Host Controller
  iSerial                 1 0000:00:1d.0
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength           25
    bNumInterfaces          1
    bConfigurationValue     1
    iConfiguration          0 
    bmAttributes         0xe0
      Self Powered
      Remote Wakeup
    MaxPower                0mA
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       0
      bNumEndpoints           1
      bInterfaceClass         9 Hub
      bInterfaceSubClass      0 Unused
      bInterfaceProtocol      0 Full speed (or root) hub
      iInterface              0 
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x81  EP 1 IN
        bmAttributes            3
          Transfer Type            Interrupt
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0002  1x 2 bytes
        bInterval             255
Hub Descriptor:
  bLength               9
  bDescriptorType      41
  nNbrPorts             2
  wHubCharacteristic 0x000a
    No power switching (usb 1.0)
    Per-port overcurrent protection
  bPwrOn2PwrGood        1 * 2 milli seconds
  bHubContrCurrent      0 milli Ampere
  DeviceRemovable    0x00
  PortPwrCtrlMask    0xff
 Hub Port Status:
   Port 1: 0000.0100 power
   Port 2: 0000.0100 power
Device Status:     0x0003
  Self Powered
  Remote Wakeup Enabled

Bus 007 Device 002: ID 1b96:0001 N-Trig Duosense Transparent Electromagnetic Digitizer
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               1.10
  bDeviceClass            0 (Defined at Interface level)
  bDeviceSubClass         0 
  bDeviceProtocol         0 
  bMaxPacketSize0        64
  idVendor           0x1b96 N-Trig
  idProduct          0x0001 Duosense Transparent Electromagnetic Digitizer
  bcdDevice            0.00
  iManufacturer           0 
  iProduct                0 
  iSerial                 0 
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength           95
    bNumInterfaces          3
    bConfigurationValue     1
    iConfiguration          0 
    bmAttributes         0xe0
      Self Powered
      Remote Wakeup
    MaxPower              500mA
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       0
      bNumEndpoints           1
      bInterfaceClass         3 Human Interface Device
      bInterfaceSubClass      1 Boot Interface Subclass
      bInterfaceProtocol      2 Mouse
      iInterface              0 
      ** UNRECOGNIZED:  09 21 10 01 00 01 22 a1 00
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x81  EP 1 IN
        bmAttributes            3
          Transfer Type            Interrupt
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0010  1x 16 bytes
        bInterval               1
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        1
      bAlternateSetting       0
      bNumEndpoints           1
      bInterfaceClass         3 Human Interface Device
      bInterfaceSubClass      1 Boot Interface Subclass
      bInterfaceProtocol      2 Mouse
      iInterface              0 
      ** UNRECOGNIZED:  09 21 10 01 00 01 22 a1 00
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x82  EP 2 IN
        bmAttributes            3
          Transfer Type            Interrupt
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0010  1x 16 bytes
        bInterval               1
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        2
      bAlternateSetting       0
      bNumEndpoints           1
      bInterfaceClass         0 (Defined at Interface level)
      bInterfaceSubClass      0 
      bInterfaceProtocol      0 
      iInterface              0 
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x83  EP 3 IN
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0040  1x 64 bytes
        bInterval               0
        ** UNRECOGNIZED:  14 ff 42 49 53 54 00 01 01 01 10 00 00 00 00 00 01 03 02 02
Device Status:     0x0000
  (Bus Powered)

Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               1.10
  bDeviceClass            9 Hub
  bDeviceSubClass         0 Unused
  bDeviceProtocol         0 Full speed (or root) hub
  bMaxPacketSize0        64
  idVendor           0x1d6b Linux Foundation
  idProduct          0x0001 1.1 root hub
  bcdDevice            2.06
  iManufacturer           3 Linux 2.6.31-20-generic uhci_hcd
  iProduct                2 UHCI Host Controller
  iSerial                 1 0000:00:1d.1
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength           25
    bNumInterfaces          1
    bConfigurationValue     1
    iConfiguration          0 
    bmAttributes         0xe0
      Self Powered
      Remote Wakeup
    MaxPower                0mA
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       0
      bNumEndpoints           1
      bInterfaceClass         9 Hub
      bInterfaceSubClass      0 Unused
      bInterfaceProtocol      0 Full speed (or root) hub
      iInterface              0 
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x81  EP 1 IN
        bmAttributes            3
          Transfer Type            Interrupt
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0002  1x 2 bytes
        bInterval             255
Hub Descriptor:
  bLength               9
  bDescriptorType      41
  nNbrPorts             2
  wHubCharacteristic 0x000a
    No power switching (usb 1.0)
    Per-port overcurrent protection
  bPwrOn2PwrGood        1 * 2 milli seconds
  bHubContrCurrent      0 milli Ampere
  DeviceRemovable    0x00
  PortPwrCtrlMask    0xff
 Hub Port Status:
   Port 1: 0000.0100 power
   Port 2: 0000.0103 power enable connect
Device Status:     0x0003
  Self Powered
  Remote Wakeup Enabled

Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               1.10
  bDeviceClass            9 Hub
  bDeviceSubClass         0 Unused
  bDeviceProtocol         0 Full speed (or root) hub
  bMaxPacketSize0        64
  idVendor           0x1d6b Linux Foundation
  idProduct          0x0001 1.1 root hub
  bcdDevice            2.06
  iManufacturer           3 Linux 2.6.31-20-generic uhci_hcd
  iProduct                2 UHCI Host Controller
  iSerial                 1 0000:00:1d.2
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength           25
    bNumInterfaces          1
    bConfigurationValue     1
    iConfiguration          0 
    bmAttributes         0xe0
      Self Powered
      Remote Wakeup
    MaxPower                0mA
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       0
      bNumEndpoints           1
      bInterfaceClass         9 Hub
      bInterfaceSubClass      0 Unused
      bInterfaceProtocol      0 Full speed (or root) hub
      iInterface              0 
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x81  EP 1 IN
        bmAttributes            3
          Transfer Type            Interrupt
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0002  1x 2 bytes
        bInterval             255
Hub Descriptor:
  bLength               9
  bDescriptorType      41
  nNbrPorts             2
  wHubCharacteristic 0x000a
    No power switching (usb 1.0)
    Per-port overcurrent protection
  bPwrOn2PwrGood        1 * 2 milli seconds
  bHubContrCurrent      0 milli Ampere
  DeviceRemovable    0x00
  PortPwrCtrlMask    0xff
 Hub Port Status:
   Port 1: 0000.0100 power
   Port 2: 0000.0100 power
Device Status:     0x0003
  Self Powered
  Remote Wakeup Enabled

Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               2.00
  bDeviceClass            9 Hub
  bDeviceSubClass         0 Unused
  bDeviceProtocol         0 Full speed (or root) hub
  bMaxPacketSize0        64
  idVendor           0x1d6b Linux Foundation
  idProduct          0x0002 2.0 root hub
  bcdDevice            2.06
  iManufacturer           3 Linux 2.6.31-20-generic ehci_hcd
  iProduct                2 EHCI Host Controller
  iSerial                 1 0000:00:1d.7
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength           25
    bNumInterfaces          1
    bConfigurationValue     1
    iConfiguration          0 
    bmAttributes         0xe0
      Self Powered
      Remote Wakeup
    MaxPower                0mA
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       0
      bNumEndpoints           1
      bInterfaceClass         9 Hub
      bInterfaceSubClass      0 Unused
      bInterfaceProtocol      0 Full speed (or root) hub
      iInterface              0 
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x81  EP 1 IN
        bmAttributes            3
          Transfer Type            Interrupt
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0004  1x 4 bytes
        bInterval              12
Hub Descriptor:
  bLength               9
  bDescriptorType      41
  nNbrPorts             6
  wHubCharacteristic 0x000a
    No power switching (usb 1.0)
    Per-port overcurrent protection
  bPwrOn2PwrGood       10 * 2 milli seconds
  bHubContrCurrent      0 milli Ampere
  DeviceRemovable    0x00
  PortPwrCtrlMask    0xff
 Hub Port Status:
   Port 1: 0000.0100 power
   Port 2: 0000.0100 power
   Port 3: 0000.0100 power
   Port 4: 0000.0100 power
   Port 5: 0000.0100 power
   Port 6: 0000.0100 power
Device Status:     0x0003
  Self Powered
  Remote Wakeup Enabled

Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               1.10
  bDeviceClass            9 Hub
  bDeviceSubClass         0 Unused
  bDeviceProtocol         0 Full speed (or root) hub
  bMaxPacketSize0        64
  idVendor           0x1d6b Linux Foundation
  idProduct          0x0001 1.1 root hub
  bcdDevice            2.06
  iManufacturer           3 Linux 2.6.31-20-generic uhci_hcd
  iProduct                2 UHCI Host Controller
  iSerial                 1 0000:00:1a.1
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength           25
    bNumInterfaces          1
    bConfigurationValue     1
    iConfiguration          0 
    bmAttributes         0xe0
      Self Powered
      Remote Wakeup
    MaxPower                0mA
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       0
      bNumEndpoints           1
      bInterfaceClass         9 Hub
      bInterfaceSubClass      0 Unused
      bInterfaceProtocol      0 Full speed (or root) hub
      iInterface              0 
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x81  EP 1 IN
        bmAttributes            3
          Transfer Type            Interrupt
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0002  1x 2 bytes
        bInterval             255
Hub Descriptor:
  bLength               9
  bDescriptorType      41
  nNbrPorts             2
  wHubCharacteristic 0x000a
    No power switching (usb 1.0)
    Per-port overcurrent protection
  bPwrOn2PwrGood        1 * 2 milli seconds
  bHubContrCurrent      0 milli Ampere
  DeviceRemovable    0x00
  PortPwrCtrlMask    0xff
 Hub Port Status:
   Port 1: 0000.0100 power
   Port 2: 0000.0100 power
Device Status:     0x0003
  Self Powered
  Remote Wakeup Enabled

Bus 005 Device 002: ID 0a5c:5801 Broadcom Corp. 
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               1.10
  bDeviceClass            0 (Defined at Interface level)
  bDeviceSubClass         0 
  bDeviceProtocol         0 
  bMaxPacketSize0        64
  idVendor           0x0a5c Broadcom Corp.
  idProduct          0x5801 
  bcdDevice            1.02
  iManufacturer           1 Broadcom Corp
  iProduct                2 5880
  iSerial                 3 0123456789ABCD
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength           55
    bNumInterfaces          1
    bConfigurationValue     0
    iConfiguration          0 
    bmAttributes         0xc0
      Self Powered
    MaxPower              100mA
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       0
      bNumEndpoints           3
      bInterfaceClass       254 Application Specific Interface
      bInterfaceSubClass      0 
      bInterfaceProtocol      0 
      iInterface              4 Broadcom USH w/swipe sensor
      ** UNRECOGNIZED:  10 25 00 00 00 00 00 00 00 00 00 00 00 00 00 00
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x81  EP 1 IN
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0040  1x 64 bytes
        bInterval               0
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x01  EP 1 OUT
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0040  1x 64 bytes
        bInterval               0
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x85  EP 5 IN
        bmAttributes            3
          Transfer Type            Interrupt
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0010  1x 16 bytes
        bInterval               1
Device Status:     0x0000
  (Bus Powered)

Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               1.10
  bDeviceClass            9 Hub
  bDeviceSubClass         0 Unused
  bDeviceProtocol         0 Full speed (or root) hub
  bMaxPacketSize0        64
  idVendor           0x1d6b Linux Foundation
  idProduct          0x0001 1.1 root hub
  bcdDevice            2.06
  iManufacturer           3 Linux 2.6.31-20-generic uhci_hcd
  iProduct                2 UHCI Host Controller
  iSerial                 1 0000:00:1a.2
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength           25
    bNumInterfaces          1
    bConfigurationValue     1
    iConfiguration          0 
    bmAttributes         0xe0
      Self Powered
      Remote Wakeup
    MaxPower                0mA
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       0
      bNumEndpoints           1
      bInterfaceClass         9 Hub
      bInterfaceSubClass      0 Unused
      bInterfaceProtocol      0 Full speed (or root) hub
      iInterface              0 
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x81  EP 1 IN
        bmAttributes            3
          Transfer Type            Interrupt
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0002  1x 2 bytes
        bInterval             255
Hub Descriptor:
  bLength               9
  bDescriptorType      41
  nNbrPorts             2
  wHubCharacteristic 0x000a
    No power switching (usb 1.0)
    Per-port overcurrent protection
  bPwrOn2PwrGood        1 * 2 milli seconds
  bHubContrCurrent      0 milli Ampere
  DeviceRemovable    0x00
  PortPwrCtrlMask    0xff
 Hub Port Status:
   Port 1: 0000.0103 power enable connect
   Port 2: 0000.0100 power
Device Status:     0x0003
  Self Powered
  Remote Wakeup Enabled

Bus 003 Device 006: ID 413c:8160 Dell Computer Corp. 
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               2.00
  bDeviceClass          224 Wireless
  bDeviceSubClass         1 Radio Frequency
  bDeviceProtocol         1 Bluetooth
  bMaxPacketSize0        64
  idVendor           0x413c Dell Computer Corp.
  idProduct          0x8160 
  bcdDevice            1.73
  iManufacturer           1 Dell Computer Corp
  iProduct                2 Dell Wireless 365 Bluetooth Module
  iSerial                 0 
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength          216
    bNumInterfaces          4
    bConfigurationValue     1
    iConfiguration          0 
    bmAttributes         0xe0
      Self Powered
      Remote Wakeup
    MaxPower              100mA
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       0
      bNumEndpoints           3
      bInterfaceClass       224 Wireless
      bInterfaceSubClass      1 Radio Frequency
      bInterfaceProtocol      1 Bluetooth
      iInterface              0 
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x81  EP 1 IN
        bmAttributes            3
          Transfer Type            Interrupt
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0010  1x 16 bytes
        bInterval               1
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x82  EP 2 IN
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0040  1x 64 bytes
        bInterval               1
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x02  EP 2 OUT
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0040  1x 64 bytes
        bInterval               1
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        1
      bAlternateSetting       0
      bNumEndpoints           2
      bInterfaceClass       224 Wireless
      bInterfaceSubClass      1 Radio Frequency
      bInterfaceProtocol      1 Bluetooth
      iInterface              0 
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x83  EP 3 IN
        bmAttributes            1
          Transfer Type            Isochronous
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0000  1x 0 bytes
        bInterval               1
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x03  EP 3 OUT
        bmAttributes            1
          Transfer Type            Isochronous
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0000  1x 0 bytes
        bInterval               1
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        1
      bAlternateSetting       1
      bNumEndpoints           2
      bInterfaceClass       224 Wireless
      bInterfaceSubClass      1 Radio Frequency
      bInterfaceProtocol      1 Bluetooth
      iInterface              0 
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x83  EP 3 IN
        bmAttributes            1
          Transfer Type            Isochronous
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0009  1x 9 bytes
        bInterval               1
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x03  EP 3 OUT
        bmAttributes            1
          Transfer Type            Isochronous
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0009  1x 9 bytes
        bInterval               1
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        1
      bAlternateSetting       2
      bNumEndpoints           2
      bInterfaceClass       224 Wireless
      bInterfaceSubClass      1 Radio Frequency
      bInterfaceProtocol      1 Bluetooth
      iInterface              0 
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x83  EP 3 IN
        bmAttributes            1
          Transfer Type            Isochronous
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0011  1x 17 bytes
        bInterval               1
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x03  EP 3 OUT
        bmAttributes            1
          Transfer Type            Isochronous
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0011  1x 17 bytes
        bInterval               1
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        1
      bAlternateSetting       3
      bNumEndpoints           2
      bInterfaceClass       224 Wireless
      bInterfaceSubClass      1 Radio Frequency
      bInterfaceProtocol      1 Bluetooth
      iInterface              0 
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x83  EP 3 IN
        bmAttributes            1
          Transfer Type            Isochronous
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0020  1x 32 bytes
        bInterval               1
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x03  EP 3 OUT
        bmAttributes            1
          Transfer Type            Isochronous
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0020  1x 32 bytes
        bInterval               1
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        1
      bAlternateSetting       4
      bNumEndpoints           2
      bInterfaceClass       224 Wireless
      bInterfaceSubClass      1 Radio Frequency
      bInterfaceProtocol      1 Bluetooth
      iInterface              0 
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x83  EP 3 IN
        bmAttributes            1
          Transfer Type            Isochronous
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0040  1x 64 bytes
        bInterval               1
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x03  EP 3 OUT
        bmAttributes            1
          Transfer Type            Isochronous
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0040  1x 64 bytes
        bInterval               1
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        1
      bAlternateSetting       5
      bNumEndpoints           2
      bInterfaceClass       224 Wireless
      bInterfaceSubClass      1 Radio Frequency
      bInterfaceProtocol      1 Bluetooth
      iInterface              0 
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x83  EP 3 IN
        bmAttributes            1
          Transfer Type            Isochronous
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0040  1x 64 bytes
        bInterval               1
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x03  EP 3 OUT
        bmAttributes            1
          Transfer Type            Isochronous
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0040  1x 64 bytes
        bInterval               1
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        2
      bAlternateSetting       0
      bNumEndpoints           2
      bInterfaceClass       255 Vendor Specific Class
      bInterfaceSubClass    255 Vendor Specific Subclass
      bInterfaceProtocol    255 Vendor Specific Protocol
      iInterface              0 
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x84  EP 4 IN
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0020  1x 32 bytes
        bInterval               1
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x04  EP 4 OUT
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0020  1x 32 bytes
        bInterval               1
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        3
      bAlternateSetting       0
      bNumEndpoints           0
      bInterfaceClass       254 Application Specific Interface
      bInterfaceSubClass      1 Device Firmware Update
      bInterfaceProtocol      0 
      iInterface              0 
      Device Firmware Upgrade Interface Descriptor:
        bLength                             7
        bDescriptorType                    33
        bmAttributes                        7
          Will Not Detach
          Manifestation Tolerant
          Upload Supported
          Download Supported
        wDetachTimeout                   5000 milliseconds
        wTransferSize                      64 bytes
Device Status:     0x0001
  Self Powered

Bus 003 Device 004: ID 413c:8162 Dell Computer Corp. 
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               2.00
  bDeviceClass            0 (Defined at Interface level)
  bDeviceSubClass         0 
  bDeviceProtocol         0 
  bMaxPacketSize0         8
  idVendor           0x413c Dell Computer Corp.
  idProduct          0x8162 
  bcdDevice            1.00
  iManufacturer           0 
  iProduct                0 
  iSerial                 0 
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength           62
    bNumInterfaces          1
    bConfigurationValue     1
    iConfiguration          0 
    bmAttributes         0xe0
      Self Powered
      Remote Wakeup
    MaxPower                2mA
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       0
      bNumEndpoints           1
      bInterfaceClass         3 Human Interface Device
      bInterfaceSubClass      1 Boot Interface Subclass
      bInterfaceProtocol      2 Mouse
      iInterface              0 
      ** UNRECOGNIZED:  09 21 11 01 00 01 22 71 00
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x81  EP 1 IN
        bmAttributes            3
          Transfer Type            Interrupt
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0004  1x 4 bytes
        bInterval              10
        ** UNRECOGNIZED:  1c ff 42 49 53 54 00 01 03 08 05 00 00 00 00 00 01 09 f4 01 02 0a f4 01 03 0b f4 01
Device Status:     0x0001
  Self Powered

Bus 003 Device 003: ID 413c:8161 Dell Computer Corp. 
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               2.00
  bDeviceClass            0 (Defined at Interface level)
  bDeviceSubClass         0 
  bDeviceProtocol         0 
  bMaxPacketSize0         8
  idVendor           0x413c Dell Computer Corp.
  idProduct          0x8161 
  bcdDevice            1.00
  iManufacturer           0 
  iProduct                0 
  iSerial                 0 
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength           34
    bNumInterfaces          1
    bConfigurationValue     1
    iConfiguration          0 
    bmAttributes         0xe0
      Self Powered
      Remote Wakeup
    MaxPower                2mA
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       0
      bNumEndpoints           1
      bInterfaceClass         3 Human Interface Device
      bInterfaceSubClass      1 Boot Interface Subclass
      bInterfaceProtocol      1 Keyboard
      iInterface              0 
      ** UNRECOGNIZED:  09 21 11 01 00 01 22 38 00
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x81  EP 1 IN
        bmAttributes            3
          Transfer Type            Interrupt
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0008  1x 8 bytes
        bInterval              10
Device Status:     0x0001
  Self Powered

Bus 003 Device 002: ID 0a5c:4500 Broadcom Corp. 
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               2.00
  bDeviceClass            9 Hub
  bDeviceSubClass         0 Unused
  bDeviceProtocol         0 Full speed (or root) hub
  bMaxPacketSize0         8
  idVendor           0x0a5c Broadcom Corp.
  idProduct          0x4500 
  bcdDevice            1.00
  iManufacturer           1 Broadcom
  iProduct                2 BCM2046B1
  iSerial                 0 
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength           25
    bNumInterfaces          1
    bConfigurationValue     1
    iConfiguration          0 
    bmAttributes         0xe0
      Self Powered
      Remote Wakeup
    MaxPower               94mA
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       0
      bNumEndpoints           1
      bInterfaceClass         9 Hub
      bInterfaceSubClass      0 Unused
      bInterfaceProtocol      0 Full speed (or root) hub
      iInterface              0 
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x81  EP 1 IN
        bmAttributes            3
          Transfer Type            Interrupt
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0001  1x 1 bytes
        bInterval             255
Hub Descriptor:
  bLength               9
  bDescriptorType      41
  nNbrPorts             3
  wHubCharacteristic 0x0004
    Ganged power switching
    Compound device
    Ganged overcurrent protection
  bPwrOn2PwrGood       50 * 2 milli seconds
  bHubContrCurrent    100 milli Ampere
  DeviceRemovable    0x0e
  PortPwrCtrlMask    0xff
 Hub Port Status:
   Port 1: 0000.0103 power enable connect
   Port 2: 0000.0103 power enable connect
   Port 3: 0000.0103 power enable connect
Device Status:     0x0001
  Self Powered

Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               1.10
  bDeviceClass            9 Hub
  bDeviceSubClass         0 Unused
  bDeviceProtocol         0 Full speed (or root) hub
  bMaxPacketSize0        64
  idVendor           0x1d6b Linux Foundation
  idProduct          0x0001 1.1 root hub
  bcdDevice            2.06
  iManufacturer           3 Linux 2.6.31-20-generic uhci_hcd
  iProduct                2 UHCI Host Controller
  iSerial                 1 0000:00:1a.0
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength           25
    bNumInterfaces          1
    bConfigurationValue     1
    iConfiguration          0 
    bmAttributes         0xe0
      Self Powered
      Remote Wakeup
    MaxPower                0mA
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       0
      bNumEndpoints           1
      bInterfaceClass         9 Hub
      bInterfaceSubClass      0 Unused
      bInterfaceProtocol      0 Full speed (or root) hub
      iInterface              0 
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x81  EP 1 IN
        bmAttributes            3
          Transfer Type            Interrupt
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0002  1x 2 bytes
        bInterval             255
Hub Descriptor:
  bLength               9
  bDescriptorType      41
  nNbrPorts             2
  wHubCharacteristic 0x000a
    No power switching (usb 1.0)
    Per-port overcurrent protection
  bPwrOn2PwrGood        1 * 2 milli seconds
  bHubContrCurrent      0 milli Ampere
  DeviceRemovable    0x00
  PortPwrCtrlMask    0xff
 Hub Port Status:
   Port 1: 0000.0100 power
   Port 2: 0000.0103 power enable connect
Device Status:     0x0003
  Self Powered
  Remote Wakeup Enabled

```

---

### Post by Ayuthia on 2010-02-19
If you are still using Windows 7, there should be an item in the Control Panel called something like "N-trig Pen and Touch".  In that application, there should be a list of items where you can turn on/off the pen or the touch.  There should also be a tab called About.  Click on that tab and it will tell you which version you are using.

Another option to try is the following in Linux:
```
sudo xxd -g1 /dev/hidraw1
```
Touch the screen and then press control-c.  If there is any output, please post a few lines of it.

---

### Post by -TJ on 2010-02-19
The problem is that I am not currently using Win7... It crashed, and I have a lot of problems with the hardware, I think. So I will send my XT2 to repair really soon, so I can get my pen, touch and multi-touch back.

From what I recall (from saving previous installation files), the thing file name was called
DuoSense_MT_RTM_Win7_64bit_LatitudeXT2_2.172
, therefore the bundle version is 2.172, I think. Or that might be the firmware version. I'm pretty sure it might be the bundle version. I can't remember what the firmware version is.


Doing what you told me resulted in an error:
```
tj@xt2:~$ sudo xxd -g1 /dev/hidraw1
[sudo] password for tj: 
xxd: /dev/hidraw1: No such file or directory

```

---

### Post by Ayuthia on 2010-02-19
> **-TJ said:**
> The problem is that I am not currently using Win7... It crashed, and I have a lot of problems with the hardware, I think. So I will send my XT2 to repair really soon, so I can get my pen, touch and multi-touch back.

From what I recall (from saving previous installation files), the thing file name was called
DuoSense_MT_RTM_Win7_64bit_LatitudeXT2_2.172
, therefore the bundle version is 2.172, I think. Or that might be the firmware version. I'm pretty sure it might be the bundle version. I can't remember what the firmware version is.


Doing what you told me resulted in an error:
```
tj@xt2:~$ sudo xxd -g1 /dev/hidraw1
[sudo] password for tj: 
xxd: /dev/hidraw1: No such file or directory

```

The 2.172 bundle is the most recent version if I recall correctly.  Can you do me a favor and post the results of:
```
ls /dev/hidraw*
```
One of those hidrawX files contain the data that comes from the N-trig kernel module.  If we can read some of the data from that file, we can figure out which firmware version you are using.

---

### Post by -TJ on 2010-02-19
Yes, I'm sure it is the most recent one. Do you want the SDK files for it?

```
tj@xt2:~$ ls /dev/hidraw*
/dev/hidraw0  /dev/hidraw2  /dev/hidraw3

```

Here, I'll upload it.

---

### Post by Ayuthia on 2010-02-19
If you are sure that 2.172 is the current version, there is no need to confirm.

Can you do me a favor and do the following:
```

cd
gedit lshal.py

```
This will open an editor.  Please add the following:
```

#!/usr/bin/env python
from commands import getoutput

def contains(data):
    data = data.split("\n")
    found = 0
    for item in data:
        if item.startswith("  info.capabilities = {'input'"):
            found = 1
    return found

lshal_list = getoutput("lshal |grep 1b96|grep udi|grep -v info\.udi|cut -nb 7-")
lshal_list = lshal_list.split("\n")

for udi in lshal_list:
    lshal_data = getoutput("lshal -u " + udi)
    if contains(lshal_data):
        print lshal_data

```
and save the file.  Then do the following:
```

python lshal.py

```
It should produce some information about your N-trig device that we will temporarily block out so that we can use the xorg.conf to configure.  Please post those results and we can create a .fdi file that will prevent hal from configuring the device or maybe create some other files to prevent evdev from capturing the device.

---

### Post by -TJ on 2010-02-19
So this is what happened:

```
tj@xt2:~$ cd
tj@xt2:~$ gedit lshal.py
tj@xt2:~$ python lshal.py
udi = '/org/freedesktop/Hal/devices/usb_device_1b96_1_noserial_if1_logicaldev_input'
  info.capabilities = {'input', 'input.touchpad'} (string list)
  info.category = 'input'  (string)
  info.parent = '/org/freedesktop/Hal/devices/usb_device_1b96_1_noserial_if1'  (string)
  info.product = 'HID 1b96:0001'  (string)
  info.subsystem = 'input'  (string)
  info.udi = '/org/freedesktop/Hal/devices/usb_device_1b96_1_noserial_if1_logicaldev_input'  (string)
  input.device = '/dev/input/event11'  (string)
  input.originating_device = '/org/freedesktop/Hal/devices/usb_device_1b96_1_noserial_if1'  (string)
  input.product = 'HID 1b96:0001'  (string)
  linux.device_file = '/dev/input/event11'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'input'  (string)
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:1d.1/usb7/7-2/7-2:1.1/input/input11/event11'  (string)

udi = '/org/freedesktop/Hal/devices/usb_device_1b96_1_noserial_if0_logicaldev_input'
  info.capabilities = {'input', 'input.touchpad'} (string list)
  info.category = 'input'  (string)
  info.parent = '/org/freedesktop/Hal/devices/usb_device_1b96_1_noserial_if0'  (string)
  info.product = 'HID 1b96:0001'  (string)
  info.subsystem = 'input'  (string)
  info.udi = '/org/freedesktop/Hal/devices/usb_device_1b96_1_noserial_if0_logicaldev_input'  (string)
  input.device = '/dev/input/event9'  (string)
  input.originating_device = '/org/freedesktop/Hal/devices/usb_device_1b96_1_noserial_if0'  (string)
  input.product = 'HID 1b96:0001'  (string)
  input.x11_driver = 'wacom'  (string)
  input.x11_options.Type = 'stylus'  (string)
  linux.device_file = '/dev/input/event9'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'input'  (string)
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:1d.1/usb7/7-2/7-2:1.0/input/input9/event9'  (string)

```

---

### Post by Ayuthia on 2010-02-20
Is the stylus working now with the current configuration?  If so, we might need to check the data that is coming from hidraw.  If it is working with the current configuration, please check:
```
sudo xxd -g1 /dev/hidraw0
sudo xxd -g1 /dev/hidraw2
sudo xxd -g1 /dev/hidraw3
```
after each one, touch the screen and then press control-c.  As soon as you get data from one of them when you touch the screen, you can stop.  Please post that data and let us know which hidraw it came from.

I am asking this because usually the data does not come from if0 if it is Windows 7.  However, the Dell might be different because it looks like their firmware reports more fingers than the HP.

---

### Post by -TJ on 2010-02-20
My firmware might be corrupt for all I know... That is why I am sending my XT2 back to Dell so they can hopefully replace it.

Either way, I did the following:

```
tj@xt2:~$ sudo xxd -g1 /dev/hidraw0
[sudo] password for tj: 
^C
tj@xt2:~$ sudo xxd -g1 /dev/hidraw2
^C
tj@xt2:~$ sudo xxd -g1 /dev/hidraw2
^C

```

The files are attached.

---

### Post by Ayuthia on 2010-02-20
> **-TJ said:**
> My firmware might be corrupt for all I know... That is why I am sending my XT2 back to Dell so they can hopefully replace it.

Either way, I did the following:

```
tj@xt2:~$ sudo xxd -g1 /dev/hidraw0
[sudo] password for tj: 
^C
tj@xt2:~$ sudo xxd -g1 /dev/hidraw2
^C
tj@xt2:~$ sudo xxd -g1 /dev/hidraw2
^C

```

The files are attached.

Thanks.  The information that you show above looks like you did not try hidraw3 (you have hidraw2 on there twice).  Usually when you run the command you would get data like:
```

$ sudo xxd -g1 /dev/hidraw1                                                                   
0000000: 00 03 aa 16 07 00 00 42 0e e2 12 ce 01 1c 02 01  .......B........                                                
0000010: 00 00 0c 07 01 00 00 00 00 00 fa 00 96 00 00 0b  ................                                                
0000020: 00 0d 07 02 00 00 00 00 00 fa 00 96 00 00 0b 00  ................                                                
0000030: 0d 07 03 00 00 00 00 00 fa 00 96 00 00 0b 00 0d  ................                                                
0000040: 07 04 00 00 00 00 00 fa 00 96 00 00 0b 00 0d 07  ................                                                
0000050: 05 00 00 00 00 00 fa 00 96 00 00 0b 00 0d 01 00  ................    

```
You don't need to attach the actual file.  Those files don't really contain anything.  They just send data from a device to the system.  We are just able to monitor the data using things like xxd.

If you don't mind, please try hidraw3 and if possible, try the other two again and also try it with the stylus.  You should be able to get a response from either the finger or the stylus from one of them (since you were able to get the stylus to work earlier).

EDIT:  I forgot to explain the reason for all of this.  Right now, the Windows 7 firmware does not work with some of the kernel modules and patches that we have created in the past.  It looks like you are using the newest firmware so I just want to confirm that when Win 7 crashed, it did not send your touchscreen back to single touch mode.  If it did, I just need to make sure that the data that is coming over is correct.  It might also mean that we might need to use Rafi Rubin's more recent changes also.

---

### Post by -TJ on 2010-02-20
Okay. First let me redo the thing before; I accidentally ran "sudo xxd -g1 /dev/hidraw2" twice.

So I did everything once more (touching the screen and then pressing [ctrl]+[c]:
```
tj@xt2:~$ sudo xxd -g1 /dev/hidraw0
[sudo] password for tj: 
^C
tj@xt2:~$ sudo xxd -g1 /dev/hidraw2
^C
tj@xt2:~$ sudo xxd -g1 /dev/hidraw3
^C

```

As you see... It didn't give me anything. But the weird thing is that when I hold my stylus close to the screen and then touch the screen with another finger, the cursor freezes until I lift my finger again. But at some instances, when I let go of the stylus and repeatedly tap with my other finger, the cursor moves to my finger (even though touch isn't really working). This could be useful information (I just wanted to let everyone know).


Okay so I did the same procedure except with stylus only. I can see that there is something special about hidraw2:

```
tj@xt2:~$ sudo xxd -g1 /dev/hidraw0
^C
tj@xt2:~$ sudo xxd -g1 /dev/hidraw2
0000000: 00 01 01 ac 19 7f 13 00 00 00 00 00 01 01 ad 19  ................
0000010: 7a 13 00 00 00 00 00 01 01 aa 19 6b 13 00 00 00  z..........k....
0000020: 00 00 01 01 a7 19 58 13 00 00 00 00 00 01 01 a3  ......X.........
0000030: 19 3f 13 00 00 00 00 00 01 01 9e 19 29 13 00 00  .?..........)...
0000040: 00 00 00 01 01 9b 19 0a 13 00 00 00 00 00 01 01  ................
0000050: 94 19 ed 12 00 00 00 00 00 01 01 8d 19 cd 12 00  ................
0000060: 00 00 00 00 01 01 86 19 ac 12 00 00 00 00 00 01  ................
0000070: 01 7f 19 89 12 00 00 00 00 00 01 01 77 19 69 12  ............w.i.
0000080: 00 00 00 00 00 01 01 6e 19 41 12 00 00 00 00 00  .......n.A......
0000090: 01 01 65 19 1b 12 00 00 00 00 00 01 01 5e 19 f0  ..e..........^..
00000a0: 11 00 00 00 00 00 01 01 58 19 c7 11 00 00 00 00  ........X.......
00000b0: 00 01 01 52 19 9a 11 00 00 00 00 00 01 01 4c 19  ...R..........L.
00000c0: 6f 11 00 00 00 00 00 01 01 4d 19 4a 11 00 00 00  o........M.J....
00000d0: 00 00 01 01 4f 19 25 11 00 00 00 00 00 01 01 4d  ....O.%........M
00000e0: 19 01 11 00 00 00 00 00 01 01 55 19 af 10 00 00  ..........U.....
00000f0: 00 00 00 01 01 60 19 67 10 00 00 00 00 00 01 01  .....`.g........
0000100: 6c 19 24 10 00 00 00 00 00 01 01 7a 19 eb 0f 00  l.$........z....
0000110: 00 00 00 00 01 01 92 19 b8 0f 00 00 00 00 00 01  ................
0000120: 01 ab 19 8a 0f 00 00 00 00 00 01 01 c6 19 60 0f  ..............`.
0000130: 00 00 00 00 00 01 01 e1 19 3b 0f 00 00 00 00 00  .........;......
0000140: 01 01 fc 19 1a 0f 00 00 00 00 00 01 01 17 1a fd  ................
0000150: 0e 00 00 00 00 00 01 01 37 1a e2 0e 00 00 00 00  ........7.......
0000160: 00 01 01 58 1a cb 0e 00 00 00 00 00 01 01 79 1a  ...X..........y.
0000170: b6 0e 00 00 00 00 00 01 01 99 1a a4 0e 00 00 00  ................
0000180: 00 00 01 01 be 1a 91 0e 00 00 00 00 00 01 01 e0  ................
0000190: 1a 81 0e 00 00 00 00 00 01 01 04 1b 3a 0e 00 00  ............:...
00001a0: 00 00 00 01 01 26 1b f2 0d 00 00 00 00 00 01 01  .....&..........
00001b0: 48 1b b0 0d 00 00 00 00 00 01 01 67 1b 68 0d 00  H..........g.h..
00001c0: 00 00 00 00 01 01 81 1b 1b 0d 00 00 00 00 00 01  ................
00001d0: 01 8a 1b fb 0c 00 00 00 00 00 01 01 92 1b d5 0c  ................
00001e0: 00 00 00 00 00 01 01 97 1b b4 0c 00 00 00 00 00  ................
00001f0: 01 00 97 1b b4 0c 00 00 00 00 00 01 01 90 1d db  ................
0000200: 16 00 00 00 00 00 01 01 90 1d dd 16 00 00 00 00  ................
0000210: 00 01 03 96 1d fb 16 dc 00 00 00 00 01 03 96 1d  ................
0000220: fb 16 db 00 00 00 00 01 03 96 1d fb 16 d9 00 00  ................
0000230: 00 00 01 03 96 1d fb 16 d7 00 00 00 00 01 03 8f  ................
0000240: 1d ff 16 d5 00 00 00 00 01 03 8a 1d 02 17 bb 00  ................
0000250: 00 00 00 01 01 88 1d 03 17 00 00 00 00 00 01 01  ................
0000260: 87 1d 03 17 00 00 00 00 00 01 01 86 1d 03 17 00  ................
0000270: 00 00 00 00 01 01 84 1d 02 17 00 00 00 00 00 01  ................
0000280: 01 81 1d 02 17 00 00 00 00 00 01 01 7d 1d 05 17  ............}...
0000290: 00 00 00 00 00 01 01 77 1d 09 17 00 00 00 00 00  .......w........
00002a0: 01 01 72 1d 0d 17 00 00 00 00 00 01 01 6d 1d 14  ..r..........m..
00002b0: 17 00 00 00 00 00 01 01 6b 1d 17 17 00 00 00 00  ........k.......
00002c0: 00 01 01 69 1d 1a 17 00 00 00 00 00 01 00 69 1d  ...i..........i.
^C
tj@xt2:~$ sudo xxd -g1 /dev/hidraw3
^C

```


About the firmware: does it really matter what happened? I'm just saying that because I started using Ubuntu for a month or two, and I don't really know exactly what happened before I wiped out Win7 from my computer. I'm having a feeling that the firmware saved onto the hardware of the actual N-trig device. Am I right? If so, what information do you need? I will try giving you answers as accurate as I can remember. I'm afraid that if I say something wrong, by accident, everything might mess up.

I am absolutely sure that I was using the most recent firmware update. It still is the most recent firmware update (which is upsetting because N-trig is being lazy). At one point, everything was all working fine! I used to be so happy at first! Now everything so messed up! >=[

I'm really going to help you guys so we can all work together to fix all of this nonsense.


Let's give Rafi Rubin's latest driver things a try! I'm ready! =]


EDIT: OH MY GOD! When I touched the screen while running hidraw2, it gave me some ... of that gibberish! This must be a good thing!

---

### Post by Ayuthia on 2010-02-20
If you have the 64-bit version of Ubuntu, you can grab the 2.6.31-20-generic version from [here]("http://linuxfans.keryxproject.org/packages/ntrig/rafi/64bit/20100216/2.6.31-20-generic/hid-ntrig.ko"):
```
cd
mkdir hid-ntrig
cd hid-ntrig
wget http://linuxfans.keryxproject.org/packages/ntrig/rafi/64bit/20100216/2.6.31-20-generic/hid-ntrig.ko
sudo cp hid-ntrig.ko /usr/lib/modules/$(uname -r)/kernel/drivers/hid/

```
From there you should be able to reboot and the driver should then be in use.  Just to confirm that it is there, please post the results of lshal.py again:
```
python lshal.py
```
If it all looks correct, we can then go through the steps of configuring the linuxwacom driver for it.

---

### Post by -TJ on 2010-02-20
There seems to be an error:

```
tj@xt2:~$ cd
tj@xt2:~$ mkdir hid-ntrig
tj@xt2:~$ cd hid-ntrig
tj@xt2:~/hid-ntrig$ wget http://linuxfans.keryxproject.org/packages/ntrig/rafi/64bit/20100216/2.6.31-20-generic/hid-ntrig.ko--2010-02-20 23:06:40--  http://linuxfans.keryxproject.org/packages/ntrig/rafi/64bit/20100216/2.6.31-20-generic/hid-ntrig.ko
Resolving linuxfans.keryxproject.org... 69.163.163.159
Connecting to linuxfans.keryxproject.org|69.163.163.159|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 9880 (9.6K) [text/plain]
Saving to: `hid-ntrig.ko'

100%[===================================================================================================================>] 9,880       --.-K/s   in 0.1s    

2010-02-20 23:06:41 (91.6 KB/s) - `hid-ntrig.ko' saved [9880/9880]

tj@xt2:~/hid-ntrig$ sudo cp hid-ntrig.ko /usr/lib/modules/$(uname -r)/kernel/drivers/hid/
cp: cannot create regular file `/usr/lib/modules/2.6.31-20-generic/kernel/drivers/hid/': No such file or directory

```

---

### Post by Favux on 2010-02-20
Hi -TJ,

Maybe a little typo.  Try:
```
sudo cp hid-ntrig.ko /lib/modules/`uname -r`/kernel/drivers/hid/
```

---

### Post by -TJ on 2010-02-20
Okay, the following worked:

```
tj@xt2:~/hid-ntrig$ sudo cp hid-ntrig.ko /lib/modules/`uname -r`/kernel/drivers/hid/
[sudo] password for tj: 

```

One second. Let me reboot and then continue with the next step.

---

### Post by -TJ on 2010-02-20
Okay. Here it is:

```
tj@xt2:~$ python lshal.py
udi = '/org/freedesktop/Hal/devices/usb_device_1b96_1_noserial_if1_logicaldev_input_0'
  info.capabilities = {'input', 'input.touchpad'} (string list)
  info.category = 'input'  (string)
  info.parent = '/org/freedesktop/Hal/devices/usb_device_1b96_1_noserial_if1'  (string)
  info.product = 'N-Trig Touchscreen'  (string)
  info.subsystem = 'input'  (string)
  info.udi = '/org/freedesktop/Hal/devices/usb_device_1b96_1_noserial_if1_logicaldev_input_0'  (string)
  input.device = '/dev/input/event13'  (string)
  input.originating_device = '/org/freedesktop/Hal/devices/usb_device_1b96_1_noserial_if1'  (string)
  input.product = 'N-Trig Touchscreen'  (string)
  linux.device_file = '/dev/input/event13'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'input'  (string)
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:1d.1/usb7/7-2/7-2:1.1/input/input13/event13'  (string)

udi = '/org/freedesktop/Hal/devices/usb_device_1b96_1_noserial_if1_logicaldev_input'
  info.capabilities = {'input', 'input.tablet'} (string list)
  info.category = 'input'  (string)
  info.parent = '/org/freedesktop/Hal/devices/usb_device_1b96_1_noserial_if1'  (string)
  info.product = 'N-Trig Pen'  (string)
  info.subsystem = 'input'  (string)
  info.udi = '/org/freedesktop/Hal/devices/usb_device_1b96_1_noserial_if1_logicaldev_input'  (string)
  input.device = '/dev/input/event12'  (string)
  input.originating_device = '/org/freedesktop/Hal/devices/usb_device_1b96_1_noserial_if1'  (string)
  input.product = 'N-Trig Pen'  (string)
  input.x11_driver = 'evdev'  (string)
  linux.device_file = '/dev/input/event12'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'input'  (string)
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:1d.1/usb7/7-2/7-2:1.1/input/input12/event12'  (string)

udi = '/org/freedesktop/Hal/devices/usb_device_1b96_1_noserial_if0_logicaldev_input_0'
  info.capabilities = {'input', 'input.touchpad'} (string list)
  info.category = 'input'  (string)
  info.parent = '/org/freedesktop/Hal/devices/usb_device_1b96_1_noserial_if0'  (string)
  info.product = 'N-Trig Touchscreen'  (string)
  info.subsystem = 'input'  (string)
  info.udi = '/org/freedesktop/Hal/devices/usb_device_1b96_1_noserial_if0_logicaldev_input_0'  (string)
  input.device = '/dev/input/event11'  (string)
  input.originating_device = '/org/freedesktop/Hal/devices/usb_device_1b96_1_noserial_if0'  (string)
  input.product = 'N-Trig Touchscreen'  (string)
  linux.device_file = '/dev/input/event11'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'input'  (string)
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:1d.1/usb7/7-2/7-2:1.0/input/input11/event11'  (string)

udi = '/org/freedesktop/Hal/devices/usb_device_1b96_1_noserial_if0_logicaldev_input'
  info.capabilities = {'input', 'input.tablet'} (string list)
  info.category = 'input'  (string)
  info.parent = '/org/freedesktop/Hal/devices/usb_device_1b96_1_noserial_if0'  (string)
  info.product = 'N-Trig Pen'  (string)
  info.subsystem = 'input'  (string)
  info.udi = '/org/freedesktop/Hal/devices/usb_device_1b96_1_noserial_if0_logicaldev_input'  (string)
  input.device = '/dev/input/event10'  (string)
  input.originating_device = '/org/freedesktop/Hal/devices/usb_device_1b96_1_noserial_if0'  (string)
  input.product = 'N-Trig Pen'  (string)
  input.x11_driver = 'evdev'  (string)
  linux.device_file = '/dev/input/event10'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'input'  (string)
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:1d.1/usb7/7-2/7-2:1.0/input/input10/event10'  (string)

tj@xt2:~$ 


```

---

### Post by Favux on 2010-02-20
Hmmm.  You seem to be missing the new multi-touch entry "N-Trig MultiTouch" that should be there.  Maybe the python script is missing it somehow?

I'll look at your entire lshal:
```
lshal>-TJ_lshal.txt
```
That will show up in "/home/username/".  Compress and attach it like before.

---

### Post by -TJ on 2010-02-20
Hey guys, I will be sending this laptop for service soon. If you want me to test out your stuff, let's do it quick please. I'm sorry if I'm rushing you guys. =[

Please forgive me.

EDIT: Would you like me to try Lucid Lynx? Should I upgrade?

---

### Post by Favux on 2010-02-20
OK, to speed up you will next be compiling linuxwacom 0.8.5-10 after patching it for n-trig.  Be sure to change anything that says 0.8.4-4 to 0.8.5-10.

Go look at my N-trig HOW TO.

There are two HOW TO's for compiling linuxwacom you can follow.  Look over 1) Karmic b) i) or ii) and pick one.

Once that's done follow the instructions in 3) and 3) a) and use the attached xorg.conf, attached at the bottom, as referenced.

That should get it working.  Ask any questions you have.

---

### Post by -TJ on 2010-02-21
Is that for Lucid or Karmic? Is that Rubin's update?

---

### Post by -TJ on 2010-02-21
Here is the lshal>-TJ_lshal.txt file.

---

### Post by Favux on 2010-02-21
Linuxwacom 0.8.5-10 is for Karmic.  Going to Lucid would take too long.  Partly because it is still alpha and unstable.  It can be tough for someone like Ayuthia to work with.

From your lshal it looks like you don't have Rafi's new 2-16-10 hid-ntrig.ko installed.  Check to be sure you downloaded and copied the one Ayuthia linked you to.

You can verify the path to it with:
```
modinfo -n hid-ntrig
```

---

### Post by -TJ on 2010-02-21
Okay. The file is attached from that location that you wanted me to check out.
I hope it is the right file.

EDIT: If it isn't, what should I do with it? Did I need to replace it with the one that Ayuthia sent?

---

### Post by Favux on 2010-02-21
Hi -TJ,

It says it was modified on 10-20-10 which is the correct date of the one in Ayuthia's repository that you should have downloaded.  So that should be it.  Maybe the lshal doesn't look right because you haven't done the udev rules yet?  I'm not sure.

As long as you sure you copied the one you downloaded continue on with compiling linuxwacom 0.8.5-10 and the rest of the steps I outlined.  If it is the wrong hid-ntrig.ko Ayuthia will tell us and you can just copy the right one over it.

---

### Post by -TJ on 2010-02-21
Your HOWTO guide is really frustrating for me to follow. Is it okay if you can just give me step-by-step directions?

Or you can make an automated script for me to use?

---

### Post by Favux on 2010-02-21
Hi -TJ,

We're just on different wavelengths.  To me it is a step by step guide albeit with some explanations added.  It may be a case of information overload, which happens to us all.  You could look at Ayuthia's.  I assume we are talking about the compiling linuxwacom HOW TO.

One thing I found useful was copying out all the commands, in order, in a text file in gedit.  With a space between each command to remind me to hit enter after I copied and pasted them in the terminal.  Also in the text file you can edit 0.8.4-4 to 0.8.5-10 easier than you can in the terminal.  That takes a little while to get use to.  If you do that you'll see there really aren't that many commands.

---

### Post by -TJ on 2010-02-21
Something like this:
[http://ubuntuforums.org/showpost.php?p=8553701&postcount=406](http://ubuntuforums.org/showpost.php?p=8553701&postcount=406)

---

### Post by Favux on 2010-02-21
Hi -TJ,

We'd have to make enough changes to it, it wouldn't be worth it.  Besides a script is only useful when things are settled down and right now things are in flux.

First download n-trig.patch.txt (attached at the bottom of my N-trig HOW TO) onto your Desktop. Right click on it and rename it 'n-trig.patch' (without the quotes).

Open a terminal and copy and paste each line in separately and hit enter after each one.  Make sure you copy the entire line and don't cut it off.  The library (lib) line is especially long.  You can use the horizontal scroll bar to see what I mean.

```
cd ./Desktop

wget http://prdownloads.sourceforge.net/linuxwacom/linuxwacom-0.8.5-10.tar.bz2

sudo apt-get update

sudo apt-get install build-essential libx11-dev libxi-dev x11proto-input-dev xserver-xorg-dev tk8.4-dev tcl8.4-dev libncurses5-dev

sudo apt-get upgrade

sudo apt-get install libhal-dev

wget http://kernel.ubuntu.com/git-repos/ubuntu/linux-2.6/drivers/hid/hid-ids.h

sudo cp ./hid-ids.h /lib/modules/`uname -r`/build/drivers/hid/hid-ids.h

tar xjvf linuxwacom-0.8.5-10.tar.bz2

patch linuxwacom-0.8.5-10/src/xdrv/wcmUSB.c < n-trig.patch

cd linuxwacom-0.8.5-10

./configure --enable-wacom --prefix=/usr

make

sudo make install

```

And you are done with patching, compiling, and installing linuxwacom!

---

### Post by -TJ on 2010-02-21
That's much easier! Thanks. This is what happened:

```
tj@xt2:~$ cd ./Desktop
tj@xt2:~/Desktop$ wget http://prdownloads.sourceforge.net/linuxwacom/linuxwacom-0.8.5-10.tar.bz2
--2010-02-21 15:50:20--  http://prdownloads.sourceforge.net/linuxwacom/linuxwacom-0.8.5-10.tar.bz2
Resolving prdownloads.sourceforge.net... 216.34.181.59
Connecting to prdownloads.sourceforge.net|216.34.181.59|:80... connected.
HTTP request sent, awaiting response... 302 Found
Location: http://cdnetworks-us-2.dl.sourceforge.net/project/linuxwacom/linuxwacom-dev/0.8.5-10/linuxwacom-0.8.5-10.tar.bz2 [following]
--2010-02-21 15:50:22--  http://cdnetworks-us-2.dl.sourceforge.net/project/linuxwacom/linuxwacom-dev/0.8.5-10/linuxwacom-0.8.5-10.tar.bz2
Resolving cdnetworks-us-2.dl.sourceforge.net... 65.49.46.188
Connecting to cdnetworks-us-2.dl.sourceforge.net|65.49.46.188|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 1155642 (1.1M) [application/x-bzip2]
Saving to: `linuxwacom-0.8.5-10.tar.bz2'

100%[===================================================================================================================>] 1,155,642    157K/s   in 10s     

2010-02-21 15:50:33 (108 KB/s) - `linuxwacom-0.8.5-10.tar.bz2' saved [1155642/1155642]

tj@xt2:~/Desktop$ sudo apt-get update
[sudo] password for tj: 
Sorry, try again.
[sudo] password for tj: 
Get:1 http://dl.google.com stable Release.gpg [189B]                                                                                                        
Hit http://us.archive.ubuntu.com karmic Release.gpg                                                                                                         
Ign http://us.archive.ubuntu.com karmic/main Translation-en_US                                                                                              
Hit http://security.ubuntu.com karmic-security Release.gpg                                                                                                  
Ign http://security.ubuntu.com karmic-security/main Translation-en_US                                                                                       
Hit http://archive.ubuntu.com karmic Release.gpg                                                                                                            
Hit http://archive.canonical.com karmic Release.gpg                                                                                                         
Hit http://ppa.launchpad.net karmic Release.gpg                                                                                                             
Ign http://ppa.launchpad.net karmic/main Translation-en_US                                                                                                  
Ign http://archive.canonical.com karmic/partner Translation-en_US                                                                                           
Hit http://packages.medibuntu.org karmic Release.gpg                                                                                   
Ign http://packages.medibuntu.org karmic/free Translation-en_US                                                                        
Ign http://us.archive.ubuntu.com karmic/restricted Translation-en_US                                                                                        
Ign http://us.archive.ubuntu.com karmic/universe Translation-en_US                                                                                          
Ign http://us.archive.ubuntu.com karmic/multiverse Translation-en_US                                                                   
Hit http://us.archive.ubuntu.com karmic-updates Release.gpg                                                                            
Ign http://us.archive.ubuntu.com karmic-updates/main Translation-en_US                                                                                      
Ign http://us.archive.ubuntu.com karmic-updates/restricted Translation-en_US                                                                                
Ign http://security.ubuntu.com karmic-security/restricted Translation-en_US                                                                                 
Ign http://security.ubuntu.com karmic-security/universe Translation-en_US                                                              
Ign http://security.ubuntu.com karmic-security/multiverse Translation-en_US                                                            
Ign http://us.archive.ubuntu.com karmic-updates/universe Translation-en_US                                                             
Ign http://us.archive.ubuntu.com karmic-updates/multiverse Translation-en_US                                                           
Hit http://us.archive.ubuntu.com karmic-backports Release.gpg                                                                          
Hit http://security.ubuntu.com karmic-security Release                                                                                                      
Hit http://archive.ubuntu.com karmic Release                                                                                                                
Hit http://ppa.launchpad.net karmic Release                                                                                            
Hit http://archive.canonical.com karmic Release                                                                                                             
Ign http://us.archive.ubuntu.com karmic-backports/main Translation-en_US                                                               
Ign http://us.archive.ubuntu.com karmic-backports/restricted Translation-en_US                                   
Ign http://us.archive.ubuntu.com karmic-backports/universe Translation-en_US                                     
Ign http://us.archive.ubuntu.com karmic-backports/multiverse Translation-en_US                                                                              
Hit http://us.archive.ubuntu.com karmic-proposed Release.gpg                                                                                                
Ign http://packages.medibuntu.org karmic/non-free Translation-en_US                                                                                         
Hit http://packages.medibuntu.org karmic Release                                                                                                            
Hit http://security.ubuntu.com karmic-security/main Packages                                                                                               
Ign http://us.archive.ubuntu.com karmic-proposed/restricted Translation-en_US                                                          
Ign http://us.archive.ubuntu.com karmic-proposed/main Translation-en_US                                                                
Ign http://us.archive.ubuntu.com karmic-proposed/multiverse Translation-en_US                                                          
Ign http://us.archive.ubuntu.com karmic-proposed/universe Translation-en_US                                                            
Hit http://ppa.launchpad.net karmic/main Packages                                                                                                           
Hit http://archive.ubuntu.com karmic/main Sources                                                                                                           
Hit http://archive.canonical.com karmic/partner Packages                                                                               
Hit http://us.archive.ubuntu.com karmic Release                                                                  
Hit http://packages.medibuntu.org karmic/free Packages                                                                                                      
Hit http://security.ubuntu.com karmic-security/restricted Packages                                                                     
Hit http://security.ubuntu.com karmic-security/restricted Sources                                                                      
Hit http://security.ubuntu.com karmic-security/main Sources                                                                            
Hit http://security.ubuntu.com karmic-security/multiverse Sources                                                                      
Hit http://archive.canonical.com karmic/partner Sources                                                                                
Hit http://archive.ubuntu.com karmic/restricted Sources                                                                                
Hit http://us.archive.ubuntu.com karmic-updates Release                                                          
Hit http://us.archive.ubuntu.com karmic-backports Release                                                       
Hit http://us.archive.ubuntu.com karmic-proposed Release                                                        
Hit http://security.ubuntu.com karmic-security/universe Sources                                                 
Hit http://security.ubuntu.com karmic-security/universe Packages                           
Hit http://security.ubuntu.com karmic-security/multiverse Packages                         
Hit http://packages.medibuntu.org karmic/non-free Packages                                 
Hit http://packages.medibuntu.org karmic/free Sources                
Hit http://packages.medibuntu.org karmic/non-free Sources            
Hit http://us.archive.ubuntu.com karmic/main Packages                
Hit http://us.archive.ubuntu.com karmic/restricted Packages
Hit http://us.archive.ubuntu.com karmic/restricted Sources
Hit http://us.archive.ubuntu.com karmic/main Sources
Hit http://us.archive.ubuntu.com karmic/multiverse Sources
Hit http://us.archive.ubuntu.com karmic/universe Sources
Hit http://us.archive.ubuntu.com karmic/universe Packages
Hit http://us.archive.ubuntu.com karmic/multiverse Packages
Hit http://us.archive.ubuntu.com karmic-updates/main Packages
Hit http://us.archive.ubuntu.com karmic-updates/restricted Packages
Hit http://us.archive.ubuntu.com karmic-updates/restricted Sources
Hit http://us.archive.ubuntu.com karmic-updates/main Sources
Hit http://us.archive.ubuntu.com karmic-updates/multiverse Sources
Hit http://us.archive.ubuntu.com karmic-updates/universe Sources
Hit http://us.archive.ubuntu.com karmic-updates/universe Packages
Hit http://us.archive.ubuntu.com karmic-updates/multiverse Packages
Hit http://us.archive.ubuntu.com karmic-backports/main Packages
Hit http://us.archive.ubuntu.com karmic-backports/restricted Packages
Hit http://us.archive.ubuntu.com karmic-backports/universe Packages
Hit http://us.archive.ubuntu.com karmic-backports/multiverse Packages
Hit http://us.archive.ubuntu.com karmic-backports/main Sources
Hit http://us.archive.ubuntu.com karmic-backports/restricted Sources
Hit http://us.archive.ubuntu.com karmic-backports/universe Sources
Hit http://us.archive.ubuntu.com karmic-backports/multiverse Sources
Hit http://us.archive.ubuntu.com karmic-proposed/restricted Packages
Hit http://us.archive.ubuntu.com karmic-proposed/main Packages
Hit http://us.archive.ubuntu.com karmic-proposed/multiverse Packages
Hit http://us.archive.ubuntu.com karmic-proposed/universe Packages
Hit http://us.archive.ubuntu.com karmic-proposed/restricted Sources
Hit http://us.archive.ubuntu.com karmic-proposed/main Sources
Hit http://us.archive.ubuntu.com karmic-proposed/multiverse Sources
Hit http://us.archive.ubuntu.com karmic-proposed/universe Sources
99% [Waiting for headers]^C                                                                                                                                 
tj@xt2:~/Desktop$ sudo apt-get install build-essential libx11-dev libxi-dev x11proto-input-dev xserver-xorg-dev tk8.4-dev tcl8.4-dev libncurses5-dev
Reading package lists... Done
Building dependency tree       
Reading state information... Done
build-essential is already the newest version.
libx11-dev is already the newest version.
libxi-dev is already the newest version.
x11proto-input-dev is already the newest version.
xserver-xorg-dev is already the newest version.
tk8.4-dev is already the newest version.
tcl8.4-dev is already the newest version.
libncurses5-dev is already the newest version.
The following packages were automatically installed and are no longer required:
  ddccontrol libddccontrol0 python-reportlab libqt4-test ddccontrol-db python-renderpm libqt4-xmlpatterns libqt4-help python-qt4 python-sip4
  python-qt4-dbus libqt4-scripttools python-reportlab-accel
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
tj@xt2:~/Desktop$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
tj@xt2:~/Desktop$ sudo apt-get install libhal-dev
Reading package lists... Done
Building dependency tree       
Reading state information... Done
libhal-dev is already the newest version.
The following packages were automatically installed and are no longer required:
  ddccontrol libddccontrol0 python-reportlab libqt4-test ddccontrol-db python-renderpm libqt4-xmlpatterns libqt4-help python-qt4 python-sip4
  python-qt4-dbus libqt4-scripttools python-reportlab-accel
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
tj@xt2:~/Desktop$ wget http://kernel.ubuntu.com/git-repos/ubuntu/linux-2.6/drivers/hid/hid-ids.h
--2010-02-21 15:51:55--  http://kernel.ubuntu.com/git-repos/ubuntu/linux-2.6/drivers/hid/hid-ids.h
Resolving kernel.ubuntu.com... 91.189.94.216
Connecting to kernel.ubuntu.com|91.189.94.216|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 15683 (15K) [text/x-chdr]
Saving to: `hid-ids.h'

100%[===================================================================================================================>] 15,683      61.2K/s   in 0.3s    

2010-02-21 15:51:56 (61.2 KB/s) - `hid-ids.h' saved [15683/15683]

tj@xt2:~/Desktop$ sudo cp ./hid-ids.h /lib/modules/`uname -r`/build/drivers/hid/hid-ids.h
tj@xt2:~/Desktop$ tar xjvf linuxwacom-0.8.5-10.tar.bz2
linuxwacom-0.8.5-10/
linuxwacom-0.8.5-10/bootstrap
linuxwacom-0.8.5-10/AUTHORS
linuxwacom-0.8.5-10/Makefile.in
linuxwacom-0.8.5-10/config.sub
linuxwacom-0.8.5-10/configure.in
linuxwacom-0.8.5-10/src/
linuxwacom-0.8.5-10/src/Makefile.in
linuxwacom-0.8.5-10/src/wacomxi/
linuxwacom-0.8.5-10/src/wacomxi/Makefile.in
linuxwacom-0.8.5-10/src/wacomxi/wacomxi.c
linuxwacom-0.8.5-10/src/wacomxi/wacomcpl.in
linuxwacom-0.8.5-10/src/wacomxi/pkgIndex.tcl
linuxwacom-0.8.5-10/src/wacomxi/wacomcpl-exec
linuxwacom-0.8.5-10/src/wacomxi/Makefile.am
linuxwacom-0.8.5-10/src/wacomxi/wacomxi.h
linuxwacom-0.8.5-10/src/include/
linuxwacom-0.8.5-10/src/include/util-config.h.in
linuxwacom-0.8.5-10/src/include/kernel-config.h.in
linuxwacom-0.8.5-10/src/include/Xwacom.h
linuxwacom-0.8.5-10/src/include/xdrv-config.h.in
linuxwacom-0.8.5-10/src/2.6.14/
linuxwacom-0.8.5-10/src/2.6.14/Makefile.in
linuxwacom-0.8.5-10/src/2.6.14/hid-core.c
linuxwacom-0.8.5-10/src/2.6.15/
linuxwacom-0.8.5-10/src/2.6.15/wacom_sys.c
linuxwacom-0.8.5-10/src/2.6.15/Makefile.in
linuxwacom-0.8.5-10/src/2.6.15/hid-core.c
linuxwacom-0.8.5-10/src/2.6.19/
linuxwacom-0.8.5-10/src/2.6.19/wacom_sys.c
linuxwacom-0.8.5-10/src/2.6.19/Makefile.in
linuxwacom-0.8.5-10/src/2.6.19/wacom.h
linuxwacom-0.8.5-10/src/2.6.19/wacom_wac.c
linuxwacom-0.8.5-10/src/xdrv/
linuxwacom-0.8.5-10/src/xdrv/wcmFilter.c
linuxwacom-0.8.5-10/src/xdrv/Makefile.in
linuxwacom-0.8.5-10/src/xdrv/wcmValidateDevice.c
linuxwacom-0.8.5-10/src/xdrv/wcmSerial.c
linuxwacom-0.8.5-10/src/xdrv/wcmCompat.c
linuxwacom-0.8.5-10/src/xdrv/wcmSerial.h
linuxwacom-0.8.5-10/src/xdrv/wcmTouchFilter.c
linuxwacom-0.8.5-10/src/xdrv/wcmMapping.c
linuxwacom-0.8.5-10/src/xdrv/wcmTilt2Rotation.c
linuxwacom-0.8.5-10/src/xdrv/wcmFilter.h
linuxwacom-0.8.5-10/src/xdrv/wcmXCommand.c
linuxwacom-0.8.5-10/src/xdrv/xf86Wacom.h
linuxwacom-0.8.5-10/src/xdrv/wcmISDV4.c
linuxwacom-0.8.5-10/src/xdrv/wcmCommon.c
linuxwacom-0.8.5-10/src/xdrv/Makefile.am
linuxwacom-0.8.5-10/src/xdrv/wcmConfig.c
linuxwacom-0.8.5-10/src/xdrv/xf86WacomDefs.h
linuxwacom-0.8.5-10/src/xdrv/wcmUSB.c
linuxwacom-0.8.5-10/src/xdrv/xf86Wacom.c
linuxwacom-0.8.5-10/src/2.6.16/
linuxwacom-0.8.5-10/src/2.6.16/wacom_wac.h
linuxwacom-0.8.5-10/src/2.6.16/wacom_sys.c
linuxwacom-0.8.5-10/src/2.6.16/Makefile.in
linuxwacom-0.8.5-10/src/2.6.16/wacom.h
linuxwacom-0.8.5-10/src/2.6.16/hid-core.c
linuxwacom-0.8.5-10/src/2.6.16/wacom_wac.c
linuxwacom-0.8.5-10/src/2.6.9/
linuxwacom-0.8.5-10/src/2.6.9/Makefile.in
linuxwacom-0.8.5-10/src/2.6.9/hid-core.c
linuxwacom-0.8.5-10/src/2.6.9/wacom.c
linuxwacom-0.8.5-10/src/util/
linuxwacom-0.8.5-10/src/util/10-linuxwacom.fdi
linuxwacom-0.8.5-10/src/util/Makefile.in
linuxwacom-0.8.5-10/src/util/wacusb.h
linuxwacom-0.8.5-10/src/util/wacscrn.c
linuxwacom-0.8.5-10/src/util/wacdump.c
linuxwacom-0.8.5-10/src/util/hal-setup-wacom.c
linuxwacom-0.8.5-10/src/util/wacusb.c
linuxwacom-0.8.5-10/src/util/wacserial.h
linuxwacom-0.8.5-10/src/util/wcmAction.c
linuxwacom-0.8.5-10/src/util/wacomcfg.c
linuxwacom-0.8.5-10/src/util/xsetwacom.c
linuxwacom-0.8.5-10/src/util/60-wacom.rules
linuxwacom-0.8.5-10/src/util/wcmAction.h
linuxwacom-0.8.5-10/src/util/wactablet.h
linuxwacom-0.8.5-10/src/util/xidump.c
linuxwacom-0.8.5-10/src/util/Makefile.am
linuxwacom-0.8.5-10/src/util/wacomcfg.h
linuxwacom-0.8.5-10/src/util/wacscrn.h
linuxwacom-0.8.5-10/src/util/wacserial.c
linuxwacom-0.8.5-10/src/util/wactablet.c
linuxwacom-0.8.5-10/src/2.6.18/
linuxwacom-0.8.5-10/src/2.6.18/Makefile.in
linuxwacom-0.8.5-10/src/2.6.18/wacom.h
linuxwacom-0.8.5-10/src/2.6.10/
linuxwacom-0.8.5-10/src/2.6.10/Makefile.in
linuxwacom-0.8.5-10/src/2.6.10/hid-core.c
linuxwacom-0.8.5-10/src/2.6.10/wacom.c
linuxwacom-0.8.5-10/src/2.6.13/
linuxwacom-0.8.5-10/src/2.6.13/wacom_sys.c
linuxwacom-0.8.5-10/src/2.6.13/Makefile.in
linuxwacom-0.8.5-10/src/2.6.13/wacom.h
linuxwacom-0.8.5-10/src/2.6.13/hid-core.c
linuxwacom-0.8.5-10/src/2.6.26/
linuxwacom-0.8.5-10/src/2.6.26/wacom_sys.c
linuxwacom-0.8.5-10/src/2.6.26/Makefile.in
linuxwacom-0.8.5-10/src/2.6.26/wacom.h
linuxwacom-0.8.5-10/src/2.6.22/
linuxwacom-0.8.5-10/src/2.6.22/wacom_wac.h
linuxwacom-0.8.5-10/src/2.6.22/wacom_sys.c
linuxwacom-0.8.5-10/src/2.6.22/Makefile.in
linuxwacom-0.8.5-10/src/wacom.4x
linuxwacom-0.8.5-10/src/Makefile.am
linuxwacom-0.8.5-10/src/2.6.11/
linuxwacom-0.8.5-10/src/2.6.11/wacom_sys.c
linuxwacom-0.8.5-10/src/2.6.11/Makefile.in
linuxwacom-0.8.5-10/src/2.6.11/wacom.h
linuxwacom-0.8.5-10/src/2.6.11/hid-core.c
linuxwacom-0.8.5-10/src/2.6.24/
linuxwacom-0.8.5-10/src/2.6.24/wacom_sys.c
linuxwacom-0.8.5-10/src/2.6.24/Makefile.in
linuxwacom-0.8.5-10/src/2.6.24/wacom.h
linuxwacom-0.8.5-10/src/2.6.27/
linuxwacom-0.8.5-10/src/2.6.27/wacom_wac.h
linuxwacom-0.8.5-10/src/2.6.27/wacom_sys.c
linuxwacom-0.8.5-10/src/2.6.27/Makefile.in
linuxwacom-0.8.5-10/src/2.6.27/wacom.h
linuxwacom-0.8.5-10/src/2.6.27/wacom_wac.c
linuxwacom-0.8.5-10/ltmain.sh
linuxwacom-0.8.5-10/docs/
linuxwacom-0.8.5-10/docs/docs_files/
linuxwacom-0.8.5-10/docs/docs_files/null.gif
linuxwacom-0.8.5-10/docs/docs_files/sflogo.png
linuxwacom-0.8.5-10/docs/docs.html
linuxwacom-0.8.5-10/configure
linuxwacom-0.8.5-10/ChangeLog
linuxwacom-0.8.5-10/install-sh
linuxwacom-0.8.5-10/prebuilt/
linuxwacom-0.8.5-10/prebuilt/64/
linuxwacom-0.8.5-10/prebuilt/64/wacdump
linuxwacom-0.8.5-10/prebuilt/64/wacom_drv.o
linuxwacom-0.8.5-10/prebuilt/64/libwacomxi.la
linuxwacom-0.8.5-10/prebuilt/64/xsetwacom
linuxwacom-0.8.5-10/prebuilt/64/.libs/
linuxwacom-0.8.5-10/prebuilt/64/.libs/libwacomxi.a
linuxwacom-0.8.5-10/prebuilt/64/.libs/libwacomxi.lai
linuxwacom-0.8.5-10/prebuilt/64/.libs/libwacomcfg.a
linuxwacom-0.8.5-10/prebuilt/64/.libs/xsetwacom
linuxwacom-0.8.5-10/prebuilt/64/.libs/libwacomcfg.so.0.0.1
linuxwacom-0.8.5-10/prebuilt/64/.libs/libwacomxi.so.0.0.0
linuxwacom-0.8.5-10/prebuilt/64/.libs/libwacomcfg.lai
linuxwacom-0.8.5-10/prebuilt/64/libwacomcfg.la
linuxwacom-0.8.5-10/prebuilt/64/xidump
linuxwacom-0.8.5-10/prebuilt/64/wacom_drv.so
linuxwacom-0.8.5-10/prebuilt/64/wacomcpl
linuxwacom-0.8.5-10/prebuilt/64/pkgIndex.tcl
linuxwacom-0.8.5-10/prebuilt/64/wacomcpl-exec
linuxwacom-0.8.5-10/prebuilt/64/wacomcfg.h
linuxwacom-0.8.5-10/prebuilt/32/
linuxwacom-0.8.5-10/prebuilt/32/wacdump
linuxwacom-0.8.5-10/prebuilt/32/wacom_drv.o
linuxwacom-0.8.5-10/prebuilt/32/libwacomxi.la
linuxwacom-0.8.5-10/prebuilt/32/xsetwacom
linuxwacom-0.8.5-10/prebuilt/32/.libs/
linuxwacom-0.8.5-10/prebuilt/32/.libs/libwacomxi.a
linuxwacom-0.8.5-10/prebuilt/32/.libs/libwacomxi.lai
linuxwacom-0.8.5-10/prebuilt/32/.libs/libwacomcfg.a
linuxwacom-0.8.5-10/prebuilt/32/.libs/xsetwacom
linuxwacom-0.8.5-10/prebuilt/32/.libs/libwacomcfg.so.0.0.1
linuxwacom-0.8.5-10/prebuilt/32/.libs/libwacomxi.so.0.0.0
linuxwacom-0.8.5-10/prebuilt/32/.libs/libwacomcfg.lai
linuxwacom-0.8.5-10/prebuilt/32/libwacomcfg.la
linuxwacom-0.8.5-10/prebuilt/32/xidump
linuxwacom-0.8.5-10/prebuilt/32/wacom_drv.so
linuxwacom-0.8.5-10/prebuilt/32/wacomcpl
linuxwacom-0.8.5-10/prebuilt/32/pkgIndex.tcl
linuxwacom-0.8.5-10/prebuilt/32/wacomcpl-exec
linuxwacom-0.8.5-10/prebuilt/32/wacomcfg.h
linuxwacom-0.8.5-10/prebuilt/uninstall
linuxwacom-0.8.5-10/prebuilt/wacom.4x.gz
linuxwacom-0.8.5-10/prebuilt/install
linuxwacom-0.8.5-10/aclocal.m4
linuxwacom-0.8.5-10/depcomp
linuxwacom-0.8.5-10/mkxincludes.in
linuxwacom-0.8.5-10/autom4te.cache/
linuxwacom-0.8.5-10/autom4te.cache/output.0
linuxwacom-0.8.5-10/autom4te.cache/traces.0
linuxwacom-0.8.5-10/autom4te.cache/output.1
linuxwacom-0.8.5-10/autom4te.cache/requests
linuxwacom-0.8.5-10/autom4te.cache/traces.1
linuxwacom-0.8.5-10/missing
linuxwacom-0.8.5-10/GPL
linuxwacom-0.8.5-10/README
linuxwacom-0.8.5-10/Makefile.am
linuxwacom-0.8.5-10/config.guess
tj@xt2:~/Desktop$ patch linuxwacom-0.8.5-10/src/xdrv/wcmUSB.c < n-trig.patch
patching file linuxwacom-0.8.5-10/src/xdrv/wcmUSB.c
Hunk #1 FAILED at 507.
Hunk #2 FAILED at 527.
Hunk #3 FAILED at 550.
3 out of 3 hunks FAILED -- saving rejects to file linuxwacom-0.8.5-10/src/xdrv/wcmUSB.c.rej
tj@xt2:~/Desktop$ cd linuxwacom-0.8.5-10
tj@xt2:~/Desktop/linuxwacom-0.8.5-10$ ./configure --enable-wacom --prefix=/usr
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for a thread-safe mkdir -p... /bin/mkdir -p
checking for gawk... gawk
checking whether make sets $(MAKE)... yes
checking whether to enable maintainer-specific portions of Makefiles... no
checking for gcc... gcc
checking for C compiler default output file name... a.out
checking whether the C compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables... 
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ISO C89... none needed
checking for style of include used by make... GNU
checking dependency style of gcc... gcc3
checking for gawk... (cached) gawk
checking build system type... x86_64-unknown-linux-gnu
checking host system type... x86_64-unknown-linux-gnu
checking for a sed that does not truncate output... /bin/sed
checking for grep that handles long lines and -e... /bin/grep
checking for egrep... /bin/grep -E
checking for ld used by gcc... /usr/bin/ld
checking if the linker (/usr/bin/ld) is GNU ld... yes
checking for /usr/bin/ld option to reload object files... -r
checking for BSD-compatible nm... /usr/bin/nm -B
checking whether ln -s works... yes
checking how to recognize dependent libraries... pass_all
checking how to run the C preprocessor... gcc -E
checking for ANSI C header files... yes
checking for sys/types.h... yes
checking for sys/stat.h... yes
checking for stdlib.h... yes
checking for string.h... yes
checking for memory.h... yes
checking for strings.h... yes
checking for inttypes.h... yes
checking for stdint.h... yes
checking for unistd.h... yes
checking dlfcn.h usability... yes
checking dlfcn.h presence... yes
checking for dlfcn.h... yes
checking for g++... g++
checking whether we are using the GNU C++ compiler... yes
checking whether g++ accepts -g... yes
checking dependency style of g++... gcc3
checking how to run the C++ preprocessor... g++ -E
checking for g77... no
checking for xlf... no
checking for f77... no
checking for frt... no
checking for pgf77... no
checking for cf77... no
checking for fort77... no
checking for fl32... no
checking for af77... no
checking for xlf90... no
checking for f90... no
checking for pgf90... no
checking for pghpf... no
checking for epcf90... no
checking for gfortran... no
checking for g95... no
checking for xlf95... no
checking for f95... no
checking for fort... no
checking for ifort... no
checking for ifc... no
checking for efc... no
checking for pgf95... no
checking for lf95... no
checking for ftn... no
checking whether we are using the GNU Fortran 77 compiler... no
checking whether  accepts -g... no
checking the maximum length of command line arguments... 1572864
checking command to parse /usr/bin/nm -B output from gcc object... ok
checking for objdir... .libs
checking for ar... ar
checking for ranlib... ranlib
checking for strip... strip
checking if gcc supports -fno-rtti -fno-exceptions... no
checking for gcc option to produce PIC... -fPIC
checking if gcc PIC flag -fPIC works... yes
checking if gcc static flag -static works... yes
checking if gcc supports -c -o file.o... yes
checking whether the gcc linker (/usr/bin/ld -m elf_x86_64) supports shared libraries... yes
checking whether -lc should be explicitly linked in... no
checking dynamic linker characteristics... GNU/Linux ld.so
checking how to hardcode library paths into programs... immediate
checking whether stripping libraries is possible... yes
checking if libtool supports shared libraries... yes
checking whether to build shared libraries... yes
checking whether to build static libraries... yes
configure: creating libtool
appending configuration tag "CXX" to libtool
checking for ld used by g++... /usr/bin/ld -m elf_x86_64
checking if the linker (/usr/bin/ld -m elf_x86_64) is GNU ld... yes
checking whether the g++ linker (/usr/bin/ld -m elf_x86_64) supports shared libraries... yes
checking for g++ option to produce PIC... -fPIC
checking if g++ PIC flag -fPIC works... yes
checking if g++ static flag -static works... yes
checking if g++ supports -c -o file.o... yes
checking whether the g++ linker (/usr/bin/ld -m elf_x86_64) supports shared libraries... yes
checking dynamic linker characteristics... GNU/Linux ld.so
(cached) (cached) checking how to hardcode library paths into programs... immediate
appending configuration tag "F77" to libtool
checking for pkg-config... /usr/bin/pkg-config
checking pkg-config is at least version 0.9.0... yes
checking for HAL... yes
checking for arch type... x86_64-linux-gnu
checking for kernel type... Linux
checking for linux-based kernel... yes
checking for kernel source/headers... /lib/modules/2.6.31-20-generic/build
checking kernel version... 2.6.31-20-generic
checking for kernel module support... yes
checking for Xlib... yes
checking for XSERVER... yes
checking for xserver libc-wrapper header-files... no
checking if scaling tablet to screen size is needed... no
checking if Xorg server is version 1.4 or later... yes
checking if Xorg is 7.3 or earlier... no
checking if Xorg server is version 1.5.2 or later... yes
checking if Xorg server is version 1.6 or later... yes
checking if Xorg SDK defined IsXExtensionPointer... yes
checking if Xorg SDK defines dixScreenOrigins... yes
checking XInput extension version... >= 2.0
checking for lib xf86config... checking for X... libraries , headers 
checking for gethostbyname... yes
checking for connect... yes
checking for remove... yes
checking for shmat... yes
checking for IceConnectionNumber in -lICE... yes
checking for tclsh... /usr/bin/tclsh
checking for tcl version... 8.4
checking for tcl header files... found, /usr/include/tcl
checking for tk header files... found, /usr/include/tcl
checking ncurses.h usability... yes
checking ncurses.h presence... yes
checking for ncurses.h... yes
checking if libwacomcfg should/can be built... yes
checking if libwacomxi should/can be built... yes
checking if wacdump should/can be built... yes
checking if xidump should/can be built... yes
checking if xsetwacom should be built... yes
checking for Wacom X driver module path... /usr/lib/xorg/modules/input
checking for dynamic driver loading support... yes
checking if wacom_drv.{o,so} should be compiled... yes
checking if gcc accepts -fno-merge-constants... yes
checking if gcc accepts -fno-stack-protector... yes

configure: creating ./config.status
config.status: creating Makefile
config.status: creating mkxincludes
config.status: creating src/Makefile
config.status: creating src/util/Makefile
config.status: creating src/xdrv/Makefile
config.status: creating src/2.6.9/Makefile
config.status: creating src/2.6.10/Makefile
config.status: creating src/2.6.11/Makefile
config.status: creating src/2.6.13/Makefile
config.status: creating src/2.6.14/Makefile
config.status: creating src/2.6.15/Makefile
config.status: creating src/2.6.16/Makefile
config.status: creating src/2.6.18/Makefile
config.status: creating src/2.6.19/Makefile
config.status: creating src/2.6.22/Makefile
config.status: creating src/2.6.24/Makefile
config.status: creating src/2.6.26/Makefile
config.status: creating src/2.6.27/Makefile
config.status: creating src/wacomxi/Makefile
config.status: creating src/wacomxi/wacomcpl
config.status: creating src/include/xdrv-config.h
config.status: creating src/include/kernel-config.h
config.status: creating src/include/util-config.h
config.status: executing depfiles commands

----------------------------------------
  BUILD ENVIRONMENT:
       architecture - x86_64-linux-gnu
       linux kernel - yes 2.6.27
  module versioning - no 
      kernel source - yes /lib/modules/2.6.31-20-generic/build
     XFree86 source - no 
           Xorg SDK - yes /usr/include/xorg
          XSERVER64 - yes
           dlloader - yes
               XLib - yes /usr/lib
         xf86config - no
                TCL - yes /usr/include/tcl
                 TK - yes /usr/include/tcl
            ncurses - yes

  BUILD OPTIONS:
            wacom.o - yes
            wacdump - yes 
             xidump - yes 
        libwacomcfg - yes
         libwacomxi - yes
          xsetwacom - yes
              hid.o - no 
       wacom_drv.so - yes /usr/lib/xorg/modules/input 
        wacom_drv.o - no
  wacom*_drv quirks - hal IsXExtensionPointer key-events dixScreenOrigins
----------------------------------------
tj@xt2:~/Desktop/linuxwacom-0.8.5-10$ make
Making all in src
make[1]: Entering directory `/home/tj/Desktop/linuxwacom-0.8.5-10/src'
Making all in .
make[2]: Entering directory `/home/tj/Desktop/linuxwacom-0.8.5-10/src'
rm -f wacom.4x.gz
gzip -9c < ./wacom.4x > wacom.4x.gz
make[2]: Leaving directory `/home/tj/Desktop/linuxwacom-0.8.5-10/src'
Making all in wacomxi
make[2]: Entering directory `/home/tj/Desktop/linuxwacom-0.8.5-10/src/wacomxi'
/bin/bash ../../libtool --tag=CC   --mode=compile gcc -DHAVE_CONFIG_H -I. -I../../src/include    -Wall -g -O2 -D__amd64__ -I/usr/include/tcl -MT wacomxi.lo -MD -MP -MF .deps/wacomxi.Tpo -c -o wacomxi.lo wacomxi.c
mkdir .libs
 gcc -DHAVE_CONFIG_H -I. -I../../src/include -Wall -g -O2 -D__amd64__ -I/usr/include/tcl -MT wacomxi.lo -MD -MP -MF .deps/wacomxi.Tpo -c wacomxi.c  -fPIC -DPIC -o .libs/wacomxi.o
 gcc -DHAVE_CONFIG_H -I. -I../../src/include -Wall -g -O2 -D__amd64__ -I/usr/include/tcl -MT wacomxi.lo -MD -MP -MF .deps/wacomxi.Tpo -c wacomxi.c -o wacomxi.o >/dev/null 2>&1
mv -f .deps/wacomxi.Tpo .deps/wacomxi.Plo
/bin/bash ../../libtool --tag=CC   --mode=link gcc -Wall -g -O2 -D__amd64__ -I/usr/include/tcl -no-undefined  -o libwacomxi.la -rpath /usr/lib/TkXInput wacomxi.lo -L/usr/lib -lX11 -lXi 
gcc -shared  .libs/wacomxi.o  -L/usr/lib -lX11 -lXi  -Wl,-soname -Wl,libwacomxi.so.0 -o .libs/libwacomxi.so.0.0.0
(cd .libs && rm -f libwacomxi.so.0 && ln -s libwacomxi.so.0.0.0 libwacomxi.so.0)
(cd .libs && rm -f libwacomxi.so && ln -s libwacomxi.so.0.0.0 libwacomxi.so)
ar cru .libs/libwacomxi.a  wacomxi.o
ranlib .libs/libwacomxi.a
creating libwacomxi.la
(cd .libs && rm -f libwacomxi.la && ln -s ../libwacomxi.la libwacomxi.la)
make[2]: Leaving directory `/home/tj/Desktop/linuxwacom-0.8.5-10/src/wacomxi'
Making all in util
make[2]: Entering directory `/home/tj/Desktop/linuxwacom-0.8.5-10/src/util'
/bin/bash ../../libtool --tag=CC   --mode=compile gcc -DHAVE_CONFIG_H -I. -I../../src/include    -Wall -pedantic -I/usr/include/xorg  -DDBUS_API_SUBJECT_TO_CHANGE -I/usr/include/hal -I/usr/include/dbus-1.0 -I/usr/lib/dbus-1.0/include   -g -O2 -D__amd64__ -I/usr/include/tcl -MT wacomcfg.lo -MD -MP -MF .deps/wacomcfg.Tpo -c -o wacomcfg.lo wacomcfg.c
mkdir .libs
 gcc -DHAVE_CONFIG_H -I. -I../../src/include -Wall -pedantic -I/usr/include/xorg -DDBUS_API_SUBJECT_TO_CHANGE -I/usr/include/hal -I/usr/include/dbus-1.0 -I/usr/lib/dbus-1.0/include -g -O2 -D__amd64__ -I/usr/include/tcl -MT wacomcfg.lo -MD -MP -MF .deps/wacomcfg.Tpo -c wacomcfg.c  -fPIC -DPIC -o .libs/wacomcfg.o
 gcc -DHAVE_CONFIG_H -I. -I../../src/include -Wall -pedantic -I/usr/include/xorg -DDBUS_API_SUBJECT_TO_CHANGE -I/usr/include/hal -I/usr/include/dbus-1.0 -I/usr/lib/dbus-1.0/include -g -O2 -D__amd64__ -I/usr/include/tcl -MT wacomcfg.lo -MD -MP -MF .deps/wacomcfg.Tpo -c wacomcfg.c -o wacomcfg.o >/dev/null 2>&1
mv -f .deps/wacomcfg.Tpo .deps/wacomcfg.Plo
/bin/bash ../../libtool --tag=CC   --mode=link gcc -Wall -pedantic -I/usr/include/xorg  -DDBUS_API_SUBJECT_TO_CHANGE -I/usr/include/hal -I/usr/include/dbus-1.0 -I/usr/lib/dbus-1.0/include   -g -O2 -D__amd64__ -I/usr/include/tcl -no-undefined -version-info 0:1:0  -o libwacomcfg.la -rpath /usr/lib wacomcfg.lo -L/usr/lib -lX11 -lXi 
gcc -shared  .libs/wacomcfg.o  -L/usr/lib -lX11 -lXi  -Wl,-soname -Wl,libwacomcfg.so.0 -o .libs/libwacomcfg.so.0.0.1
(cd .libs && rm -f libwacomcfg.so.0 && ln -s libwacomcfg.so.0.0.1 libwacomcfg.so.0)
(cd .libs && rm -f libwacomcfg.so && ln -s libwacomcfg.so.0.0.1 libwacomcfg.so)
ar cru .libs/libwacomcfg.a  wacomcfg.o
ranlib .libs/libwacomcfg.a
creating libwacomcfg.la
(cd .libs && rm -f libwacomcfg.la && ln -s ../libwacomcfg.la libwacomcfg.la)
gcc -DHAVE_CONFIG_H -I. -I../../src/include    -Wall -pedantic -I/usr/include/xorg  -DDBUS_API_SUBJECT_TO_CHANGE -I/usr/include/hal -I/usr/include/dbus-1.0 -I/usr/lib/dbus-1.0/include   -g -O2 -D__amd64__ -I/usr/include/tcl -MT wacdump.o -MD -MP -MF .deps/wacdump.Tpo -c -o wacdump.o wacdump.c
mv -f .deps/wacdump.Tpo .deps/wacdump.Po
gcc -DHAVE_CONFIG_H -I. -I../../src/include    -Wall -pedantic -I/usr/include/xorg  -DDBUS_API_SUBJECT_TO_CHANGE -I/usr/include/hal -I/usr/include/dbus-1.0 -I/usr/lib/dbus-1.0/include   -g -O2 -D__amd64__ -I/usr/include/tcl -MT wacscrn.o -MD -MP -MF .deps/wacscrn.Tpo -c -o wacscrn.o wacscrn.c
mv -f .deps/wacscrn.Tpo .deps/wacscrn.Po
gcc -DHAVE_CONFIG_H -I. -I../../src/include    -Wall -pedantic -I/usr/include/xorg  -DDBUS_API_SUBJECT_TO_CHANGE -I/usr/include/hal -I/usr/include/dbus-1.0 -I/usr/lib/dbus-1.0/include   -g -O2 -D__amd64__ -I/usr/include/tcl -MT wactablet.o -MD -MP -MF .deps/wactablet.Tpo -c -o wactablet.o wactablet.c
mv -f .deps/wactablet.Tpo .deps/wactablet.Po
gcc -DHAVE_CONFIG_H -I. -I../../src/include    -Wall -pedantic -I/usr/include/xorg  -DDBUS_API_SUBJECT_TO_CHANGE -I/usr/include/hal -I/usr/include/dbus-1.0 -I/usr/lib/dbus-1.0/include   -g -O2 -D__amd64__ -I/usr/include/tcl -MT wacserial.o -MD -MP -MF .deps/wacserial.Tpo -c -o wacserial.o wacserial.c
wacserial.c: In function ‘WacomFlush’:
wacserial.c:1345: warning: ignoring return value of ‘read’, declared with attribute warn_unused_result
mv -f .deps/wacserial.Tpo .deps/wacserial.Po
gcc -DHAVE_CONFIG_H -I. -I../../src/include    -Wall -pedantic -I/usr/include/xorg  -DDBUS_API_SUBJECT_TO_CHANGE -I/usr/include/hal -I/usr/include/dbus-1.0 -I/usr/lib/dbus-1.0/include   -g -O2 -D__amd64__ -I/usr/include/tcl -MT wacusb.o -MD -MP -MF .deps/wacusb.Tpo -c -o wacusb.o wacusb.c
mv -f .deps/wacusb.Tpo .deps/wacusb.Po
/bin/bash ../../libtool --tag=CC   --mode=link gcc -Wall -pedantic -I/usr/include/xorg  -DDBUS_API_SUBJECT_TO_CHANGE -I/usr/include/hal -I/usr/include/dbus-1.0 -I/usr/lib/dbus-1.0/include   -g -O2 -D__amd64__ -I/usr/include/tcl   -o wacdump wacdump.o wacscrn.o wactablet.o wacserial.o wacusb.o -lncurses 
gcc -Wall -pedantic -I/usr/include/xorg -DDBUS_API_SUBJECT_TO_CHANGE -I/usr/include/hal -I/usr/include/dbus-1.0 -I/usr/lib/dbus-1.0/include -g -O2 -D__amd64__ -I/usr/include/tcl -o wacdump wacdump.o wacscrn.o wactablet.o wacserial.o wacusb.o  -lncurses  
gcc -DHAVE_CONFIG_H -I. -I../../src/include    -Wall -pedantic -I/usr/include/xorg  -DDBUS_API_SUBJECT_TO_CHANGE -I/usr/include/hal -I/usr/include/dbus-1.0 -I/usr/lib/dbus-1.0/include   -g -O2 -D__amd64__ -I/usr/include/tcl -MT xidump.o -MD -MP -MF .deps/xidump.Tpo -c -o xidump.o xidump.c
xidump.c: In function ‘RawRunAccel’:
xidump.c:770: warning: dereferencing pointer ‘pMove’ does break strict-aliasing rules
xidump.c:769: note: initialized from here
xidump.c:772: warning: dereferencing pointer ‘event.63’ does break strict-aliasing rules
xidump.c:772: note: initialized from here
xidump.c:774: warning: dereferencing pointer ‘event.63’ does break strict-aliasing rules
xidump.c:774: note: initialized from here
xidump.c: In function ‘RawRun’:
xidump.c:718: warning: dereferencing pointer ‘pAny.58’ does break strict-aliasing rules
xidump.c:718: note: initialized from here
xidump.c:717: warning: dereferencing pointer ‘pAny.58’ does break strict-aliasing rules
xidump.c:717: note: initialized from here
xidump.c:716: warning: dereferencing pointer ‘pAny.58’ does break strict-aliasing rules
xidump.c:716: note: initialized from here
xidump.c:711: warning: dereferencing pointer ‘pAny.58’ does break strict-aliasing rules
xidump.c:715: note: initialized from here
xidump.c:711: warning: dereferencing pointer ‘pAny.58’ does break strict-aliasing rules
xidump.c:714: note: initialized from here
xidump.c:711: warning: dereferencing pointer ‘pAny.58’ does break strict-aliasing rules
xidump.c:713: note: initialized from here
xidump.c:725: warning: dereferencing pointer ‘pBtn’ does break strict-aliasing rules
xidump.c:724: note: initialized from here
xidump.c:733: warning: dereferencing pointer ‘pKey’ does break strict-aliasing rules
xidump.c:732: note: initialized from here
xidump.c: In function ‘CursesRun’:
xidump.c:571: warning: dereferencing pointer ‘pAny.53’ does break strict-aliasing rules
xidump.c:572: note: initialized from here
xidump.c:580: warning: dereferencing pointer ‘pAny.53’ does break strict-aliasing rules
xidump.c:580: note: initialized from here
xidump.c:590: warning: dereferencing pointer ‘pAny.53’ does break strict-aliasing rules
xidump.c:590: note: initialized from here
xidump.c:625: warning: dereferencing pointer ‘pBtn’ does break strict-aliasing rules
xidump.c:623: warning: dereferencing pointer ‘pBtn’ does break strict-aliasing rules
xidump.c:620: note: initialized from here
xidump.c:642: warning: dereferencing pointer ‘pKey’ does break strict-aliasing rules
xidump.c:640: warning: dereferencing pointer ‘pKey’ does break strict-aliasing rules
xidump.c:638: note: initialized from here
mv -f .deps/xidump.Tpo .deps/xidump.Po
/bin/bash ../../libtool --tag=CC   --mode=link gcc -Wall -pedantic -I/usr/include/xorg  -DDBUS_API_SUBJECT_TO_CHANGE -I/usr/include/hal -I/usr/include/dbus-1.0 -I/usr/lib/dbus-1.0/include   -g -O2 -D__amd64__ -I/usr/include/tcl -L/usr/lib -lX11 -lXi -lm  -o xidump xidump.o wacscrn.o -lncurses 
gcc -Wall -pedantic -I/usr/include/xorg -DDBUS_API_SUBJECT_TO_CHANGE -I/usr/include/hal -I/usr/include/dbus-1.0 -I/usr/lib/dbus-1.0/include -g -O2 -D__amd64__ -I/usr/include/tcl -o xidump xidump.o wacscrn.o  -L/usr/lib -lX11 -lXi -lm -lncurses  
gcc -DHAVE_CONFIG_H -I. -I../../src/include    -Wall -pedantic -I/usr/include/xorg  -DDBUS_API_SUBJECT_TO_CHANGE -I/usr/include/hal -I/usr/include/dbus-1.0 -I/usr/lib/dbus-1.0/include   -g -O2 -D__amd64__ -I/usr/include/tcl -MT xsetwacom.o -MD -MP -MF .deps/xsetwacom.Tpo -c -o xsetwacom.o xsetwacom.c
mv -f .deps/xsetwacom.Tpo .deps/xsetwacom.Po
gcc -DHAVE_CONFIG_H -I. -I../../src/include    -Wall -pedantic -I/usr/include/xorg  -DDBUS_API_SUBJECT_TO_CHANGE -I/usr/include/hal -I/usr/include/dbus-1.0 -I/usr/lib/dbus-1.0/include   -g -O2 -D__amd64__ -I/usr/include/tcl -MT wcmAction.o -MD -MP -MF .deps/wcmAction.Tpo -c -o wcmAction.o wcmAction.c
mv -f .deps/wcmAction.Tpo .deps/wcmAction.Po
/bin/bash ../../libtool --tag=CC   --mode=link gcc -Wall -pedantic -I/usr/include/xorg  -DDBUS_API_SUBJECT_TO_CHANGE -I/usr/include/hal -I/usr/include/dbus-1.0 -I/usr/lib/dbus-1.0/include   -g -O2 -D__amd64__ -I/usr/include/tcl   -o xsetwacom xsetwacom.o wcmAction.o libwacomcfg.la 
gcc -Wall -pedantic -I/usr/include/xorg -DDBUS_API_SUBJECT_TO_CHANGE -I/usr/include/hal -I/usr/include/dbus-1.0 -I/usr/lib/dbus-1.0/include -g -O2 -D__amd64__ -I/usr/include/tcl -o .libs/xsetwacom xsetwacom.o wcmAction.o  ./.libs/libwacomcfg.so -L/usr/lib -lX11 -lXi 
creating xsetwacom
gcc -DHAVE_CONFIG_H -I. -I../../src/include    -Wall -pedantic -I/usr/include/xorg  -DDBUS_API_SUBJECT_TO_CHANGE -I/usr/include/hal -I/usr/include/dbus-1.0 -I/usr/lib/dbus-1.0/include   -g -O2 -D__amd64__ -I/usr/include/tcl -MT hal-setup-wacom.o -MD -MP -MF .deps/hal-setup-wacom.Tpo -c -o hal-setup-wacom.o hal-setup-wacom.c
hal-setup-wacom.c: In function ‘main’:
hal-setup-wacom.c:54: warning: ignoring return value of ‘asprintf’, declared with attribute warn_unused_result
hal-setup-wacom.c:137: warning: ignoring return value of ‘asprintf’, declared with attribute warn_unused_result
mv -f .deps/hal-setup-wacom.Tpo .deps/hal-setup-wacom.Po
/bin/bash ../../libtool --tag=CC   --mode=link gcc -Wall -pedantic -I/usr/include/xorg  -DDBUS_API_SUBJECT_TO_CHANGE -I/usr/include/hal -I/usr/include/dbus-1.0 -I/usr/lib/dbus-1.0/include   -g -O2 -D__amd64__ -I/usr/include/tcl   -o hal-setup-wacom hal-setup-wacom.o -L/lib -lhal -ldbus-1 -lpthread -lrt   
gcc -Wall -pedantic -I/usr/include/xorg -DDBUS_API_SUBJECT_TO_CHANGE -I/usr/include/hal -I/usr/include/dbus-1.0 -I/usr/lib/dbus-1.0/include -g -O2 -D__amd64__ -I/usr/include/tcl -o hal-setup-wacom hal-setup-wacom.o  -L/lib -lhal -ldbus-1 -lpthread -lrt  
make[2]: Leaving directory `/home/tj/Desktop/linuxwacom-0.8.5-10/src/util'
Making all in xdrv
make[2]: Entering directory `/home/tj/Desktop/linuxwacom-0.8.5-10/src/xdrv'
gcc -MM -g -O2 -D__amd64__ -I/usr/include/tcl  -I../include -I/usr/include/xorg   ./xf86Wacom.c ./wcmSerial.c ./wcmUSB.c ./wcmISDV4.c ./wcmXCommand.c ./wcmCommon.c ./wcmCompat.c ./wcmConfig.c ./wcmFilter.c ./wcmTilt2Rotation.c ./wcmTouchFilter.c ./wcmValidateDevice.c ./wcmMapping.c > .depend
make[2]: Leaving directory `/home/tj/Desktop/linuxwacom-0.8.5-10/src/xdrv'
make[2]: Entering directory `/home/tj/Desktop/linuxwacom-0.8.5-10/src/xdrv'
gcc -g -O2 -D__amd64__ -I/usr/include/tcl  -fPIC -pipe -std=c99 \
		-pedantic -Wall -Wpointer-arith -fno-merge-constants \
		-fno-stack-protector -I. -I../include -I/usr/include/xorg   \
		-D_XSERVER64 -I/usr/include/xorg -I/usr/include/pixman-1   \
		-o xf86Wacom.o -c ./xf86Wacom.c
In file included from ./xf86Wacom.h:27,
                 from ./xf86Wacom.c:102:
/usr/include/xorg/xorg-server.h:105:1: warning: "XKB" redefined
In file included from ./xf86Wacom.h:25,
                 from ./xf86Wacom.c:102:
./../include/xdrv-config.h:18:1: warning: this is the location of the previous definition
In file included from ./xf86Wacom.h:27,
                 from ./xf86Wacom.c:102:
/usr/include/xorg/xorg-server.h:195:1: warning: "XFree86LOADER" redefined
In file included from ./xf86Wacom.h:25,
                 from ./xf86Wacom.c:102:
./../include/xdrv-config.h:12:1: warning: this is the location of the previous definition
gcc -g -O2 -D__amd64__ -I/usr/include/tcl  -fPIC -pipe -std=c99 \
		-pedantic -Wall -Wpointer-arith -fno-merge-constants \
		-fno-stack-protector -I. -I../include -I/usr/include/xorg   \
		-D_XSERVER64 -I/usr/include/xorg -I/usr/include/pixman-1   \
		-o wcmSerial.o -c ./wcmSerial.c
In file included from ./xf86Wacom.h:27,
                 from ./wcmSerial.c:20:
/usr/include/xorg/xorg-server.h:105:1: warning: "XKB" redefined
In file included from ./xf86Wacom.h:25,
                 from ./wcmSerial.c:20:
./../include/xdrv-config.h:18:1: warning: this is the location of the previous definition
In file included from ./xf86Wacom.h:27,
                 from ./wcmSerial.c:20:
/usr/include/xorg/xorg-server.h:195:1: warning: "XFree86LOADER" redefined
In file included from ./xf86Wacom.h:25,
                 from ./wcmSerial.c:20:
./../include/xdrv-config.h:12:1: warning: this is the location of the previous definition
gcc -g -O2 -D__amd64__ -I/usr/include/tcl  -fPIC -pipe -std=c99 \
		-pedantic -Wall -Wpointer-arith -fno-merge-constants \
		-fno-stack-protector -I. -I../include -I/usr/include/xorg   \
		-D_XSERVER64 -I/usr/include/xorg -I/usr/include/pixman-1   \
		-o wcmUSB.o -c ./wcmUSB.c
In file included from ./xf86Wacom.h:27,
                 from ./wcmUSB.c:20:
/usr/include/xorg/xorg-server.h:105:1: warning: "XKB" redefined
In file included from ./xf86Wacom.h:25,
                 from ./wcmUSB.c:20:
./../include/xdrv-config.h:18:1: warning: this is the location of the previous definition
In file included from ./xf86Wacom.h:27,
                 from ./wcmUSB.c:20:
/usr/include/xorg/xorg-server.h:195:1: warning: "XFree86LOADER" redefined
In file included from ./xf86Wacom.h:25,
                 from ./wcmUSB.c:20:
./../include/xdrv-config.h:12:1: warning: this is the location of the previous definition
gcc -g -O2 -D__amd64__ -I/usr/include/tcl  -fPIC -pipe -std=c99 \
		-pedantic -Wall -Wpointer-arith -fno-merge-constants \
		-fno-stack-protector -I. -I../include -I/usr/include/xorg   \
		-D_XSERVER64 -I/usr/include/xorg -I/usr/include/pixman-1   \
		-o wcmISDV4.o -c ./wcmISDV4.c
In file included from ./xf86Wacom.h:27,
                 from ./wcmISDV4.c:20:
/usr/include/xorg/xorg-server.h:105:1: warning: "XKB" redefined
In file included from ./xf86Wacom.h:25,
                 from ./wcmISDV4.c:20:
./../include/xdrv-config.h:18:1: warning: this is the location of the previous definition
In file included from ./xf86Wacom.h:27,
                 from ./wcmISDV4.c:20:
/usr/include/xorg/xorg-server.h:195:1: warning: "XFree86LOADER" redefined
In file included from ./xf86Wacom.h:25,
                 from ./wcmISDV4.c:20:
./../include/xdrv-config.h:12:1: warning: this is the location of the previous definition
gcc -g -O2 -D__amd64__ -I/usr/include/tcl  -fPIC -pipe -std=c99 \
		-pedantic -Wall -Wpointer-arith -fno-merge-constants \
		-fno-stack-protector -I. -I../include -I/usr/include/xorg   \
		-D_XSERVER64 -I/usr/include/xorg -I/usr/include/pixman-1   \
		-o wcmXCommand.o -c ./wcmXCommand.c
In file included from ./xf86Wacom.h:27,
                 from ./wcmXCommand.c:34:
/usr/include/xorg/xorg-server.h:105:1: warning: "XKB" redefined
In file included from ./xf86Wacom.h:25,
                 from ./wcmXCommand.c:34:
./../include/xdrv-config.h:18:1: warning: this is the location of the previous definition
In file included from ./xf86Wacom.h:27,
                 from ./wcmXCommand.c:34:
/usr/include/xorg/xorg-server.h:195:1: warning: "XFree86LOADER" redefined
In file included from ./xf86Wacom.h:25,
                 from ./wcmXCommand.c:34:
./../include/xdrv-config.h:12:1: warning: this is the location of the previous definition
gcc -g -O2 -D__amd64__ -I/usr/include/tcl  -fPIC -pipe -std=c99 \
		-pedantic -Wall -Wpointer-arith -fno-merge-constants \
		-fno-stack-protector -I. -I../include -I/usr/include/xorg   \
		-D_XSERVER64 -I/usr/include/xorg -I/usr/include/pixman-1   \
		-o wcmCommon.o -c ./wcmCommon.c
In file included from ./xf86Wacom.h:27,
                 from ./wcmCommon.c:20:
/usr/include/xorg/xorg-server.h:105:1: warning: "XKB" redefined
In file included from ./xf86Wacom.h:25,
                 from ./wcmCommon.c:20:
./../include/xdrv-config.h:18:1: warning: this is the location of the previous definition
In file included from ./xf86Wacom.h:27,
                 from ./wcmCommon.c:20:
/usr/include/xorg/xorg-server.h:195:1: warning: "XFree86LOADER" redefined
In file included from ./xf86Wacom.h:25,
                 from ./wcmCommon.c:20:
./../include/xdrv-config.h:12:1: warning: this is the location of the previous definition
gcc -g -O2 -D__amd64__ -I/usr/include/tcl  -fPIC -pipe -std=c99 \
		-pedantic -Wall -Wpointer-arith -fno-merge-constants \
		-fno-stack-protector -I. -I../include -I/usr/include/xorg   \
		-D_XSERVER64 -I/usr/include/xorg -I/usr/include/pixman-1   \
		-o wcmCompat.o -c ./wcmCompat.c
In file included from ./xf86Wacom.h:27,
                 from ./wcmCompat.c:19:
/usr/include/xorg/xorg-server.h:105:1: warning: "XKB" redefined
In file included from ./xf86Wacom.h:25,
                 from ./wcmCompat.c:19:
./../include/xdrv-config.h:18:1: warning: this is the location of the previous definition
In file included from ./xf86Wacom.h:27,
                 from ./wcmCompat.c:19:
/usr/include/xorg/xorg-server.h:195:1: warning: "XFree86LOADER" redefined
In file included from ./xf86Wacom.h:25,
                 from ./wcmCompat.c:19:
./../include/xdrv-config.h:12:1: warning: this is the location of the previous definition
gcc -g -O2 -D__amd64__ -I/usr/include/tcl  -fPIC -pipe -std=c99 \
		-pedantic -Wall -Wpointer-arith -fno-merge-constants \
		-fno-stack-protector -I. -I../include -I/usr/include/xorg   \
		-D_XSERVER64 -I/usr/include/xorg -I/usr/include/pixman-1   \
		-o wcmConfig.o -c ./wcmConfig.c
In file included from ./xf86Wacom.h:27,
                 from ./wcmConfig.c:20:
/usr/include/xorg/xorg-server.h:105:1: warning: "XKB" redefined
In file included from ./xf86Wacom.h:25,
                 from ./wcmConfig.c:20:
./../include/xdrv-config.h:18:1: warning: this is the location of the previous definition
In file included from ./xf86Wacom.h:27,
                 from ./wcmConfig.c:20:
/usr/include/xorg/xorg-server.h:195:1: warning: "XFree86LOADER" redefined
In file included from ./xf86Wacom.h:25,
                 from ./wcmConfig.c:20:
./../include/xdrv-config.h:12:1: warning: this is the location of the previous definition
gcc -g -O2 -D__amd64__ -I/usr/include/tcl  -fPIC -pipe -std=c99 \
		-pedantic -Wall -Wpointer-arith -fno-merge-constants \
		-fno-stack-protector -I. -I../include -I/usr/include/xorg   \
		-D_XSERVER64 -I/usr/include/xorg -I/usr/include/pixman-1   \
		-o wcmFilter.o -c ./wcmFilter.c
In file included from ./xf86Wacom.h:27,
                 from ./wcmFilter.h:23,
                 from ./wcmFilter.c:20:
/usr/include/xorg/xorg-server.h:105:1: warning: "XKB" redefined
In file included from ./xf86Wacom.h:25,
                 from ./wcmFilter.h:23,
                 from ./wcmFilter.c:20:
./../include/xdrv-config.h:18:1: warning: this is the location of the previous definition
In file included from ./xf86Wacom.h:27,
                 from ./wcmFilter.h:23,
                 from ./wcmFilter.c:20:
/usr/include/xorg/xorg-server.h:195:1: warning: "XFree86LOADER" redefined
In file included from ./xf86Wacom.h:25,
                 from ./wcmFilter.h:23,
                 from ./wcmFilter.c:20:
./../include/xdrv-config.h:12:1: warning: this is the location of the previous definition
gcc -g -O2 -D__amd64__ -I/usr/include/tcl  -fPIC -pipe -std=c99 \
		-pedantic -Wall -Wpointer-arith -fno-merge-constants \
		-fno-stack-protector -I. -I../include -I/usr/include/xorg   \
		-D_XSERVER64 -I/usr/include/xorg -I/usr/include/pixman-1   \
		-o wcmTilt2Rotation.o -c ./wcmTilt2Rotation.c
In file included from ./xf86Wacom.h:27,
                 from ./wcmTilt2Rotation.c:19:
/usr/include/xorg/xorg-server.h:105:1: warning: "XKB" redefined
In file included from ./xf86Wacom.h:25,
                 from ./wcmTilt2Rotation.c:19:
./../include/xdrv-config.h:18:1: warning: this is the location of the previous definition
In file included from ./xf86Wacom.h:27,
                 from ./wcmTilt2Rotation.c:19:
/usr/include/xorg/xorg-server.h:195:1: warning: "XFree86LOADER" redefined
In file included from ./xf86Wacom.h:25,
                 from ./wcmTilt2Rotation.c:19:
./../include/xdrv-config.h:12:1: warning: this is the location of the previous definition
gcc -g -O2 -D__amd64__ -I/usr/include/tcl  -fPIC -pipe -std=c99 \
		-pedantic -Wall -Wpointer-arith -fno-merge-constants \
		-fno-stack-protector -I. -I../include -I/usr/include/xorg   \
		-D_XSERVER64 -I/usr/include/xorg -I/usr/include/pixman-1   \
		-o wcmTouchFilter.o -c ./wcmTouchFilter.c
In file included from ./xf86Wacom.h:27,
                 from ./wcmTouchFilter.c:19:
/usr/include/xorg/xorg-server.h:105:1: warning: "XKB" redefined
In file included from ./xf86Wacom.h:25,
                 from ./wcmTouchFilter.c:19:
./../include/xdrv-config.h:18:1: warning: this is the location of the previous definition
In file included from ./xf86Wacom.h:27,
                 from ./wcmTouchFilter.c:19:
/usr/include/xorg/xorg-server.h:195:1: warning: "XFree86LOADER" redefined
In file included from ./xf86Wacom.h:25,
                 from ./wcmTouchFilter.c:19:
./../include/xdrv-config.h:12:1: warning: this is the location of the previous definition
gcc -g -O2 -D__amd64__ -I/usr/include/tcl  -fPIC -pipe -std=c99 \
		-pedantic -Wall -Wpointer-arith -fno-merge-constants \
		-fno-stack-protector -I. -I../include -I/usr/include/xorg   \
		-D_XSERVER64 -I/usr/include/xorg -I/usr/include/pixman-1   \
		-o wcmValidateDevice.o -c ./wcmValidateDevice.c
In file included from ./xf86Wacom.h:27,
                 from ./wcmValidateDevice.c:19:
/usr/include/xorg/xorg-server.h:105:1: warning: "XKB" redefined
In file included from ./xf86Wacom.h:25,
                 from ./wcmValidateDevice.c:19:
./../include/xdrv-config.h:18:1: warning: this is the location of the previous definition
In file included from ./xf86Wacom.h:27,
                 from ./wcmValidateDevice.c:19:
/usr/include/xorg/xorg-server.h:195:1: warning: "XFree86LOADER" redefined
In file included from ./xf86Wacom.h:25,
                 from ./wcmValidateDevice.c:19:
./../include/xdrv-config.h:12:1: warning: this is the location of the previous definition
gcc -g -O2 -D__amd64__ -I/usr/include/tcl  -fPIC -pipe -std=c99 \
		-pedantic -Wall -Wpointer-arith -fno-merge-constants \
		-fno-stack-protector -I. -I../include -I/usr/include/xorg   \
		-D_XSERVER64 -I/usr/include/xorg -I/usr/include/pixman-1   \
		-o wcmMapping.o -c ./wcmMapping.c
In file included from ./xf86Wacom.h:27,
                 from ./wcmMapping.c:19:
/usr/include/xorg/xorg-server.h:105:1: warning: "XKB" redefined
In file included from ./xf86Wacom.h:25,
                 from ./wcmMapping.c:19:
./../include/xdrv-config.h:18:1: warning: this is the location of the previous definition
In file included from ./xf86Wacom.h:27,
                 from ./wcmMapping.c:19:
/usr/include/xorg/xorg-server.h:195:1: warning: "XFree86LOADER" redefined
In file included from ./xf86Wacom.h:25,
                 from ./wcmMapping.c:19:
./../include/xdrv-config.h:12:1: warning: this is the location of the previous definition
gcc -shared -nostdlib -o wacom_drv.so xf86Wacom.o wcmSerial.o wcmUSB.o wcmISDV4.o wcmXCommand.o wcmCommon.o wcmCompat.o wcmConfig.o wcmFilter.o wcmTilt2Rotation.o wcmTouchFilter.o wcmValidateDevice.o wcmMapping.o -Bstatic -lgcc
make[2]: Leaving directory `/home/tj/Desktop/linuxwacom-0.8.5-10/src/xdrv'
Making all in 2.6.27
make[2]: Entering directory `/home/tj/Desktop/linuxwacom-0.8.5-10/src/2.6.27'
    Building linuxwacom drivers for 2.6 kernel.
***Note: Drivers not enabled as modules in your kernel config but requested through configure are NOT built
make -C /lib/modules/2.6.31-20-generic/build M=/home/tj/Desktop/linuxwacom-0.8.5-10/src/2.6.27
make[3]: Entering directory `/usr/src/linux-headers-2.6.31-20-generic'
  LD      /home/tj/Desktop/linuxwacom-0.8.5-10/src/2.6.27/built-in.o
  CC [M]  /home/tj/Desktop/linuxwacom-0.8.5-10/src/2.6.27/wacom_wac.o
  CC [M]  /home/tj/Desktop/linuxwacom-0.8.5-10/src/2.6.27/wacom_sys.o
  LD [M]  /home/tj/Desktop/linuxwacom-0.8.5-10/src/2.6.27/wacom.o
  Building modules, stage 2.
  MODPOST 1 modules
  CC      /home/tj/Desktop/linuxwacom-0.8.5-10/src/2.6.27/wacom.mod.o
  LD [M]  /home/tj/Desktop/linuxwacom-0.8.5-10/src/2.6.27/wacom.ko
make[3]: Leaving directory `/usr/src/linux-headers-2.6.31-20-generic'
make[2]: Leaving directory `/home/tj/Desktop/linuxwacom-0.8.5-10/src/2.6.27'
make[1]: Leaving directory `/home/tj/Desktop/linuxwacom-0.8.5-10/src'
make[1]: Entering directory `/home/tj/Desktop/linuxwacom-0.8.5-10'
make[1]: Nothing to be done for `all-am'.
make[1]: Leaving directory `/home/tj/Desktop/linuxwacom-0.8.5-10'
tj@xt2:~/Desktop/linuxwacom-0.8.5-10$ sudo make install
Making install in src
make[1]: Entering directory `/home/tj/Desktop/linuxwacom-0.8.5-10/src'
Making install in .
make[2]: Entering directory `/home/tj/Desktop/linuxwacom-0.8.5-10/src'
make[3]: Entering directory `/home/tj/Desktop/linuxwacom-0.8.5-10/src'
make[3]: Nothing to be done for `install-exec-am'.
test -z "/usr/share/man/man4" || /bin/mkdir -p "/usr/share/man/man4"
 /usr/bin/install -c -m 644 'wacom.4x.gz' '/usr/share/man/man4/wacom.4x.gz'
make[3]: Leaving directory `/home/tj/Desktop/linuxwacom-0.8.5-10/src'
make[2]: Leaving directory `/home/tj/Desktop/linuxwacom-0.8.5-10/src'
Making install in wacomxi
make[2]: Entering directory `/home/tj/Desktop/linuxwacom-0.8.5-10/src/wacomxi'
make[3]: Entering directory `/home/tj/Desktop/linuxwacom-0.8.5-10/src/wacomxi'
make[3]: Nothing to be done for `install-exec-am'.
test -z "/usr/bin" || /bin/mkdir -p "/usr/bin"
 /usr/bin/install -c 'wacomcpl' '/usr/bin/wacomcpl'
 /usr/bin/install -c 'wacomcpl-exec' '/usr/bin/wacomcpl-exec'
test -z "/usr/lib/TkXInput" || /bin/mkdir -p "/usr/lib/TkXInput"
 /usr/bin/install -c -m 644 'pkgIndex.tcl' '/usr/lib/TkXInput/pkgIndex.tcl'
test -z "/usr/lib/TkXInput" || /bin/mkdir -p "/usr/lib/TkXInput"
 /bin/bash ../../libtool   --mode=install /usr/bin/install -c  'libwacomxi.la' '/usr/lib/TkXInput/libwacomxi.la'
/usr/bin/install -c .libs/libwacomxi.so.0.0.0 /usr/lib/TkXInput/libwacomxi.so.0.0.0
(cd /usr/lib/TkXInput && { ln -s -f libwacomxi.so.0.0.0 libwacomxi.so.0 || { rm -f libwacomxi.so.0 && ln -s libwacomxi.so.0.0.0 libwacomxi.so.0; }; })
(cd /usr/lib/TkXInput && { ln -s -f libwacomxi.so.0.0.0 libwacomxi.so || { rm -f libwacomxi.so && ln -s libwacomxi.so.0.0.0 libwacomxi.so; }; })
/usr/bin/install -c .libs/libwacomxi.lai /usr/lib/TkXInput/libwacomxi.la
/usr/bin/install -c .libs/libwacomxi.a /usr/lib/TkXInput/libwacomxi.a
chmod 644 /usr/lib/TkXInput/libwacomxi.a
ranlib /usr/lib/TkXInput/libwacomxi.a
PATH="$PATH:/sbin" ldconfig -n /usr/lib/TkXInput
----------------------------------------------------------------------
Libraries have been installed in:
   /usr/lib/TkXInput

If you ever happen to want to link against installed libraries
in a given directory, LIBDIR, you must either use libtool, and
specify the full pathname of the library, or use the `-LLIBDIR'
flag during linking and do at least one of the following:
   - add LIBDIR to the `LD_LIBRARY_PATH' environment variable
     during execution
   - add LIBDIR to the `LD_RUN_PATH' environment variable
     during linking
   - use the `-Wl,--rpath -Wl,LIBDIR' linker flag
   - have your system administrator add LIBDIR to `/etc/ld.so.conf'

See any operating system documentation about shared libraries for
more information, such as the ld(1) and ld.so(8) manual pages.
----------------------------------------------------------------------
make[3]: Leaving directory `/home/tj/Desktop/linuxwacom-0.8.5-10/src/wacomxi'
make[2]: Leaving directory `/home/tj/Desktop/linuxwacom-0.8.5-10/src/wacomxi'
Making install in util
make[2]: Entering directory `/home/tj/Desktop/linuxwacom-0.8.5-10/src/util'
make[3]: Entering directory `/home/tj/Desktop/linuxwacom-0.8.5-10/src/util'
test -z "/usr/lib" || /bin/mkdir -p "/usr/lib"
 /bin/bash ../../libtool   --mode=install /usr/bin/install -c  'libwacomcfg.la' '/usr/lib/libwacomcfg.la'
/usr/bin/install -c .libs/libwacomcfg.so.0.0.1 /usr/lib/libwacomcfg.so.0.0.1
(cd /usr/lib && { ln -s -f libwacomcfg.so.0.0.1 libwacomcfg.so.0 || { rm -f libwacomcfg.so.0 && ln -s libwacomcfg.so.0.0.1 libwacomcfg.so.0; }; })
(cd /usr/lib && { ln -s -f libwacomcfg.so.0.0.1 libwacomcfg.so || { rm -f libwacomcfg.so && ln -s libwacomcfg.so.0.0.1 libwacomcfg.so; }; })
/usr/bin/install -c .libs/libwacomcfg.lai /usr/lib/libwacomcfg.la
/usr/bin/install -c .libs/libwacomcfg.a /usr/lib/libwacomcfg.a
chmod 644 /usr/lib/libwacomcfg.a
ranlib /usr/lib/libwacomcfg.a
PATH="$PATH:/sbin" ldconfig -n /usr/lib
----------------------------------------------------------------------
Libraries have been installed in:
   /usr/lib

If you ever happen to want to link against installed libraries
in a given directory, LIBDIR, you must either use libtool, and
specify the full pathname of the library, or use the `-LLIBDIR'
flag during linking and do at least one of the following:
   - add LIBDIR to the `LD_LIBRARY_PATH' environment variable
     during execution
   - add LIBDIR to the `LD_RUN_PATH' environment variable
     during linking
   - use the `-Wl,--rpath -Wl,LIBDIR' linker flag
   - have your system administrator add LIBDIR to `/etc/ld.so.conf'

See any operating system documentation about shared libraries for
more information, such as the ld(1) and ld.so(8) manual pages.
----------------------------------------------------------------------
test -z "/usr/bin" || /bin/mkdir -p "/usr/bin"
  /bin/bash ../../libtool   --mode=install /usr/bin/install -c 'wacdump' '/usr/bin/wacdump'
/usr/bin/install -c wacdump /usr/bin/wacdump
  /bin/bash ../../libtool   --mode=install /usr/bin/install -c 'xidump' '/usr/bin/xidump'
/usr/bin/install -c xidump /usr/bin/xidump
  /bin/bash ../../libtool   --mode=install /usr/bin/install -c 'xsetwacom' '/usr/bin/xsetwacom'
/usr/bin/install -c .libs/xsetwacom /usr/bin/xsetwacom
test -z "/usr/libexec" || /bin/mkdir -p "/usr/libexec"
  /bin/bash ../../libtool   --mode=install /usr/bin/install -c 'hal-setup-wacom' '/usr/libexec/hal-setup-wacom'
/usr/bin/install -c hal-setup-wacom /usr/libexec/hal-setup-wacom
test -z "/usr/share/hal/fdi/policy/20thirdparty" || /bin/mkdir -p "/usr/share/hal/fdi/policy/20thirdparty"
 /usr/bin/install -c '10-linuxwacom.fdi' '/usr/share/hal/fdi/policy/20thirdparty/10-linuxwacom.fdi'
test -z "/usr/include/wacomcfg" || /bin/mkdir -p "/usr/include/wacomcfg"
 /usr/bin/install -c -m 644 'wacomcfg.h' '/usr/include/wacomcfg/wacomcfg.h'
make[3]: Leaving directory `/home/tj/Desktop/linuxwacom-0.8.5-10/src/util'
make[2]: Leaving directory `/home/tj/Desktop/linuxwacom-0.8.5-10/src/util'
Making install in xdrv
make[2]: Entering directory `/home/tj/Desktop/linuxwacom-0.8.5-10/src/xdrv'
make[3]: Entering directory `/home/tj/Desktop/linuxwacom-0.8.5-10/src/xdrv'
make[3]: Nothing to be done for `install-exec-am'.
test -z "/usr/lib/xorg/modules/input" || /bin/mkdir -p "/usr/lib/xorg/modules/input"
 /usr/bin/install -c -m 644 'wacom_drv.so' '/usr/lib/xorg/modules/input/wacom_drv.so'
make[3]: Leaving directory `/home/tj/Desktop/linuxwacom-0.8.5-10/src/xdrv'
make[2]: Leaving directory `/home/tj/Desktop/linuxwacom-0.8.5-10/src/xdrv'
Making install in 2.6.27
make[2]: Entering directory `/home/tj/Desktop/linuxwacom-0.8.5-10/src/2.6.27'
make[2]: Nothing to be done for `install'.
make[2]: Leaving directory `/home/tj/Desktop/linuxwacom-0.8.5-10/src/2.6.27'
make[1]: Leaving directory `/home/tj/Desktop/linuxwacom-0.8.5-10/src'
make[1]: Entering directory `/home/tj/Desktop/linuxwacom-0.8.5-10'
make[2]: Entering directory `/home/tj/Desktop/linuxwacom-0.8.5-10'
make[2]: Nothing to be done for `install-exec-am'.
make[2]: Nothing to be done for `install-data-am'.
make[2]: Leaving directory `/home/tj/Desktop/linuxwacom-0.8.5-10'
make[1]: Leaving directory `/home/tj/Desktop/linuxwacom-0.8.5-10'
tj@xt2:~/Desktop/linuxwacom-0.8.5-10$ 

```


If you look at it more closely, this piece of code was interesting:

```
tj@xt2:~/Desktop$ patch linuxwacom-0.8.5-10/src/xdrv/wcmUSB.c < n-trig.patch
patching file linuxwacom-0.8.5-10/src/xdrv/wcmUSB.c
Hunk #1 FAILED at 507.
Hunk #2 FAILED at 527.
Hunk #3 FAILED at 550.
3 out of 3 hunks FAILED -- saving rejects to file linuxwacom-0.8.5-10/src/xdrv/wcmUSB.c.rej
```

Did that have a problem?
I'll upload that file so you can look at it. I hope it isn't something significant.

---

### Post by Favux on 2010-02-21
OK, it looks like the n-trig.patch may have failed on linuxwacom.0.8.5-10:
```
tj@xt2:~/Desktop$ patch linuxwacom-0.8.5-10/src/xdrv/wcmUSB.c < n-trig.patch
patching file linuxwacom-0.8.5-10/src/xdrv/wcmUSB.c
Hunk #1 FAILED at 507.
Hunk #2 FAILED at 527.
Hunk #3 FAILED at 550.
3 out of 3 hunks FAILED -- saving rejects to file linuxwacom-0.8.5-10/src/xdrv/wcmUSB.c.rej
```
It did go onto build and install with some complaints.  But since there are only 3 hunks in n-trig.patch that I see linuxwacom probably won't accept your N-trig.  Darn.

So we're stumped unless Rafi's new patch for xf86-xinput-wacom in 1) Lucid b) will also work on linuxwacom 0.8.5-10.  Just download it and substitute it for n-trig.patch in the above command.  So change:
```
patch linuxwacom-0.8.5-10/src/xdrv/wcmUSB.c < n-trig.patch
```
to
```
patch linuxwacom-0.8.5-10/src/xdrv/wcmUSB.c < xf86-input-wacom_ntrig_2010_02_03.patch

```

Also to help Ayuthia or whoever to fix things it would be usefule to see the file wcmUSB.c.rej at "linuxwacom-0.8.5-10/src/xdrv/wcmUSB.c.rej".  I know Ayuthia is using 0.8.5-10 so he must already know how to get the patch to work.

---

### Post by Ayuthia on 2010-02-21
Right now I don't have the time to do the formal updates to the linuxfans site so here is a link to the updated source.  Do the following:
```

cd
mkdir lw-ntrig
cd lw-ntrig
wget http://linuxfans.keryxproject.org/packages/wacom/ntrig/source/linuxwacom-0.8.5-10.tar.bz2
tar -xvjf linuxwacom-0.8.5-10.tar.bz2
cd linuxwacom-0.8.5-10
./configure --enable-wacom --prefix=/usr
make
sudo make install

```
That should compile it for you.

Favux, feel free to link that file.  I will try to get the patch out soon and update the site to have some instructions for building things with Rafi Rubin's changes.

---

### Post by -TJ on 2010-02-21
Darn! I'm getting errors:

```
tj@xt2:~$ cd
tj@xt2:~$ mkdir lw-ntrig
tj@xt2:~$ cd lw-ntrig
tj@xt2:~/lw-ntrig$ wget http://linuxfans.keryxproject.org/packages/wacom/ntrig/source/linuxwacom-0.8.5-10.tar.bz2
--2010-02-21 17:42:45--  http://linuxfans.keryxproject.org/packages/wacom/ntrig/source/linuxwacom-0.8.5-10.tar.bz2
Resolving linuxfans.keryxproject.org... 69.163.163.159
Connecting to linuxfans.keryxproject.org|69.163.163.159|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 1136277 (1.1M) [application/x-bzip2]
Saving to: `linuxwacom-0.8.5-10.tar.bz2'

100%[===================================================================================================================>] 1,136,277    259K/s   in 4.4s    

2010-02-21 17:42:50 (252 KB/s) - `linuxwacom-0.8.5-10.tar.bz2' saved [1136277/1136277]

tj@xt2:~/lw-ntrig$ tar -xvjf linuxwacom-0.8.5-10.tar.bz2
linuxwacom-0.8.5-10/
linuxwacom-0.8.5-10/README
linuxwacom-0.8.5-10/autom4te.cache/
linuxwacom-0.8.5-10/autom4te.cache/output.0
linuxwacom-0.8.5-10/autom4te.cache/requests
linuxwacom-0.8.5-10/autom4te.cache/output.1
linuxwacom-0.8.5-10/autom4te.cache/traces.1
linuxwacom-0.8.5-10/autom4te.cache/traces.0
linuxwacom-0.8.5-10/config.guess
linuxwacom-0.8.5-10/GPL
linuxwacom-0.8.5-10/Makefile.in
linuxwacom-0.8.5-10/ltmain.sh
linuxwacom-0.8.5-10/Makefile.am
linuxwacom-0.8.5-10/mkxincludes.in
linuxwacom-0.8.5-10/prebuilt/
linuxwacom-0.8.5-10/prebuilt/32/
linuxwacom-0.8.5-10/prebuilt/32/libwacomxi.la
linuxwacom-0.8.5-10/prebuilt/32/wacom_drv.o
linuxwacom-0.8.5-10/prebuilt/32/pkgIndex.tcl
linuxwacom-0.8.5-10/prebuilt/32/xidump
linuxwacom-0.8.5-10/prebuilt/32/wacdump
linuxwacom-0.8.5-10/prebuilt/32/libwacomcfg.la
linuxwacom-0.8.5-10/prebuilt/32/wacomcfg.h
linuxwacom-0.8.5-10/prebuilt/32/wacom_drv.so
linuxwacom-0.8.5-10/prebuilt/32/.libs/
linuxwacom-0.8.5-10/prebuilt/32/.libs/libwacomxi.lai
linuxwacom-0.8.5-10/prebuilt/32/.libs/libwacomcfg.lai
linuxwacom-0.8.5-10/prebuilt/32/.libs/libwacomxi.so.0.0.0
linuxwacom-0.8.5-10/prebuilt/32/.libs/libwacomxi.a
linuxwacom-0.8.5-10/prebuilt/32/.libs/libwacomcfg.so.0.0.1
linuxwacom-0.8.5-10/prebuilt/32/.libs/xsetwacom
linuxwacom-0.8.5-10/prebuilt/32/.libs/libwacomcfg.a
linuxwacom-0.8.5-10/prebuilt/32/xsetwacom
linuxwacom-0.8.5-10/prebuilt/32/wacomcpl
linuxwacom-0.8.5-10/prebuilt/32/wacomcpl-exec
linuxwacom-0.8.5-10/prebuilt/wacom.4x.gz
linuxwacom-0.8.5-10/prebuilt/64/
linuxwacom-0.8.5-10/prebuilt/64/libwacomxi.la
linuxwacom-0.8.5-10/prebuilt/64/wacom_drv.o
linuxwacom-0.8.5-10/prebuilt/64/pkgIndex.tcl
linuxwacom-0.8.5-10/prebuilt/64/xidump
linuxwacom-0.8.5-10/prebuilt/64/wacdump
linuxwacom-0.8.5-10/prebuilt/64/libwacomcfg.la
linuxwacom-0.8.5-10/prebuilt/64/wacomcfg.h
linuxwacom-0.8.5-10/prebuilt/64/wacom_drv.so
linuxwacom-0.8.5-10/prebuilt/64/.libs/
linuxwacom-0.8.5-10/prebuilt/64/.libs/libwacomxi.lai
linuxwacom-0.8.5-10/prebuilt/64/.libs/libwacomcfg.lai
linuxwacom-0.8.5-10/prebuilt/64/.libs/libwacomxi.so.0.0.0
linuxwacom-0.8.5-10/prebuilt/64/.libs/libwacomxi.a
linuxwacom-0.8.5-10/prebuilt/64/.libs/libwacomcfg.so.0.0.1
linuxwacom-0.8.5-10/prebuilt/64/.libs/xsetwacom
linuxwacom-0.8.5-10/prebuilt/64/.libs/libwacomcfg.a
linuxwacom-0.8.5-10/prebuilt/64/xsetwacom
linuxwacom-0.8.5-10/prebuilt/64/wacomcpl
linuxwacom-0.8.5-10/prebuilt/64/wacomcpl-exec
linuxwacom-0.8.5-10/prebuilt/uninstall
linuxwacom-0.8.5-10/prebuilt/install
linuxwacom-0.8.5-10/bootstrap
linuxwacom-0.8.5-10/config.sub
linuxwacom-0.8.5-10/configure.in
linuxwacom-0.8.5-10/ChangeLog
linuxwacom-0.8.5-10/configure
linuxwacom-0.8.5-10/AUTHORS
linuxwacom-0.8.5-10/docs/
linuxwacom-0.8.5-10/docs/docs_files/
linuxwacom-0.8.5-10/docs/docs_files/sflogo.png
linuxwacom-0.8.5-10/docs/docs_files/null.gif
linuxwacom-0.8.5-10/docs/docs.html
linuxwacom-0.8.5-10/missing
linuxwacom-0.8.5-10/aclocal.m4
linuxwacom-0.8.5-10/depcomp
linuxwacom-0.8.5-10/src/
linuxwacom-0.8.5-10/src/2.6.10/
linuxwacom-0.8.5-10/src/2.6.10/Makefile.in
linuxwacom-0.8.5-10/src/2.6.10/wacom.c
linuxwacom-0.8.5-10/src/2.6.10/hid-core.c
linuxwacom-0.8.5-10/src/2.6.27/
linuxwacom-0.8.5-10/src/2.6.27/Makefile.in
linuxwacom-0.8.5-10/src/2.6.27/wacom.h
linuxwacom-0.8.5-10/src/2.6.27/wacom_sys.c
linuxwacom-0.8.5-10/src/2.6.27/wacom_wac.h
linuxwacom-0.8.5-10/src/2.6.27/wacom_wac.c
linuxwacom-0.8.5-10/src/Makefile.in
linuxwacom-0.8.5-10/src/wacomxi/
linuxwacom-0.8.5-10/src/wacomxi/wacomxi.c
linuxwacom-0.8.5-10/src/wacomxi/Makefile.in
linuxwacom-0.8.5-10/src/wacomxi/Makefile.am
linuxwacom-0.8.5-10/src/wacomxi/pkgIndex.tcl
linuxwacom-0.8.5-10/src/wacomxi/wacomxi.h
linuxwacom-0.8.5-10/src/wacomxi/wacomcpl.in
linuxwacom-0.8.5-10/src/wacomxi/wacomcpl-exec
linuxwacom-0.8.5-10/src/wacom.4x
linuxwacom-0.8.5-10/src/2.6.19/
linuxwacom-0.8.5-10/src/2.6.19/Makefile.in
linuxwacom-0.8.5-10/src/2.6.19/wacom.h
linuxwacom-0.8.5-10/src/2.6.19/wacom_sys.c
linuxwacom-0.8.5-10/src/2.6.19/wacom_wac.c
linuxwacom-0.8.5-10/src/Makefile.am
linuxwacom-0.8.5-10/src/xdrv/
linuxwacom-0.8.5-10/src/xdrv/wcmMapping.c
linuxwacom-0.8.5-10/src/xdrv/wcmTilt2Rotation.c
linuxwacom-0.8.5-10/src/xdrv/wcmXCommand.c
linuxwacom-0.8.5-10/src/xdrv/wcmTouchFilter.c
linuxwacom-0.8.5-10/src/xdrv/wcmUSB.c
linuxwacom-0.8.5-10/src/xdrv/xf86Wacom.c
linuxwacom-0.8.5-10/src/xdrv/Makefile.in
linuxwacom-0.8.5-10/src/xdrv/wcmCompat.c
linuxwacom-0.8.5-10/src/xdrv/Makefile.am
linuxwacom-0.8.5-10/src/xdrv/wcmSerial.c
linuxwacom-0.8.5-10/src/xdrv/wcmSerial.h
linuxwacom-0.8.5-10/src/xdrv/wcmValidateDevice.c
linuxwacom-0.8.5-10/src/xdrv/xf86WacomDefs.h
linuxwacom-0.8.5-10/src/xdrv/wcmISDV4.c
linuxwacom-0.8.5-10/src/xdrv/wcmFilter.h
linuxwacom-0.8.5-10/src/xdrv/xf86Wacom.h
linuxwacom-0.8.5-10/src/xdrv/wcmFilter.c
linuxwacom-0.8.5-10/src/xdrv/wcmCommon.c
linuxwacom-0.8.5-10/src/xdrv/wcmConfig.c
linuxwacom-0.8.5-10/src/2.6.9/
linuxwacom-0.8.5-10/src/2.6.9/Makefile.in
linuxwacom-0.8.5-10/src/2.6.9/wacom.c
linuxwacom-0.8.5-10/src/2.6.9/hid-core.c
linuxwacom-0.8.5-10/src/2.6.22/
linuxwacom-0.8.5-10/src/2.6.22/Makefile.in
linuxwacom-0.8.5-10/src/2.6.22/wacom_sys.c
linuxwacom-0.8.5-10/src/2.6.22/wacom_wac.h
linuxwacom-0.8.5-10/src/2.6.26/
linuxwacom-0.8.5-10/src/2.6.26/Makefile.in
linuxwacom-0.8.5-10/src/2.6.26/wacom.h
linuxwacom-0.8.5-10/src/2.6.26/wacom_sys.c
linuxwacom-0.8.5-10/src/2.6.24/
linuxwacom-0.8.5-10/src/2.6.24/Makefile.in
linuxwacom-0.8.5-10/src/2.6.24/wacom.h
linuxwacom-0.8.5-10/src/2.6.24/wacom_sys.c
linuxwacom-0.8.5-10/src/2.6.18/
linuxwacom-0.8.5-10/src/2.6.18/Makefile.in
linuxwacom-0.8.5-10/src/2.6.18/wacom.h
linuxwacom-0.8.5-10/src/2.6.15/
linuxwacom-0.8.5-10/src/2.6.15/Makefile.in
linuxwacom-0.8.5-10/src/2.6.15/hid-core.c
linuxwacom-0.8.5-10/src/2.6.15/wacom_sys.c
linuxwacom-0.8.5-10/src/2.6.14/
linuxwacom-0.8.5-10/src/2.6.14/Makefile.in
linuxwacom-0.8.5-10/src/2.6.14/hid-core.c
linuxwacom-0.8.5-10/src/2.6.13/
linuxwacom-0.8.5-10/src/2.6.13/Makefile.in
linuxwacom-0.8.5-10/src/2.6.13/wacom.h
linuxwacom-0.8.5-10/src/2.6.13/hid-core.c
linuxwacom-0.8.5-10/src/2.6.13/wacom_sys.c
linuxwacom-0.8.5-10/src/2.6.16/
linuxwacom-0.8.5-10/src/2.6.16/Makefile.in
linuxwacom-0.8.5-10/src/2.6.16/wacom.h
linuxwacom-0.8.5-10/src/2.6.16/hid-core.c
linuxwacom-0.8.5-10/src/2.6.16/wacom_sys.c
linuxwacom-0.8.5-10/src/2.6.16/wacom_wac.h
linuxwacom-0.8.5-10/src/2.6.16/wacom_wac.c
linuxwacom-0.8.5-10/src/2.6.11/
linuxwacom-0.8.5-10/src/2.6.11/Makefile.in
linuxwacom-0.8.5-10/src/2.6.11/wacom.h
linuxwacom-0.8.5-10/src/2.6.11/hid-core.c
linuxwacom-0.8.5-10/src/2.6.11/wacom_sys.c
linuxwacom-0.8.5-10/src/include/
linuxwacom-0.8.5-10/src/include/util-config.h.in
linuxwacom-0.8.5-10/src/include/xdrv-config.h.in
linuxwacom-0.8.5-10/src/include/kernel-config.h.in
linuxwacom-0.8.5-10/src/include/Xwacom.h
linuxwacom-0.8.5-10/src/util/
linuxwacom-0.8.5-10/src/util/Makefile.in
linuxwacom-0.8.5-10/src/util/wcmAction.h
linuxwacom-0.8.5-10/src/util/Makefile.am
linuxwacom-0.8.5-10/src/util/wacdump.c
linuxwacom-0.8.5-10/src/util/wacomcfg.h
linuxwacom-0.8.5-10/src/util/wacserial.c
linuxwacom-0.8.5-10/src/util/wacusb.c
linuxwacom-0.8.5-10/src/util/wactablet.c
linuxwacom-0.8.5-10/src/util/xsetwacom.c
linuxwacom-0.8.5-10/src/util/wacscrn.c
linuxwacom-0.8.5-10/src/util/wacomcfg.c
linuxwacom-0.8.5-10/src/util/wactablet.h
linuxwacom-0.8.5-10/src/util/xidump.c
linuxwacom-0.8.5-10/src/util/10-linuxwacom.fdi
linuxwacom-0.8.5-10/src/util/wcmAction.c
linuxwacom-0.8.5-10/src/util/wacusb.h
linuxwacom-0.8.5-10/src/util/hal-setup-wacom.c
linuxwacom-0.8.5-10/src/util/wacscrn.h
linuxwacom-0.8.5-10/src/util/wacserial.h
linuxwacom-0.8.5-10/src/util/60-wacom.rules
linuxwacom-0.8.5-10/install-sh
tj@xt2:~/lw-ntrig$ cd linuxwacom-0.8.5-10
tj@xt2:~/lw-ntrig/linuxwacom-0.8.5-10$ ./configure --enable-wacom --prefix=/usr
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for a thread-safe mkdir -p... /bin/mkdir -p
checking for gawk... gawk
checking whether make sets $(MAKE)... yes
checking whether to enable maintainer-specific portions of Makefiles... no
checking for gcc... gcc
checking for C compiler default output file name... a.out
checking whether the C compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables... 
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ISO C89... none needed
checking for style of include used by make... GNU
checking dependency style of gcc... gcc3
checking for gawk... (cached) gawk
checking build system type... x86_64-unknown-linux-gnu
checking host system type... x86_64-unknown-linux-gnu
checking for a sed that does not truncate output... /bin/sed
checking for grep that handles long lines and -e... /bin/grep
checking for egrep... /bin/grep -E
checking for ld used by gcc... /usr/bin/ld
checking if the linker (/usr/bin/ld) is GNU ld... yes
checking for /usr/bin/ld option to reload object files... -r
checking for BSD-compatible nm... /usr/bin/nm -B
checking whether ln -s works... yes
checking how to recognize dependent libraries... pass_all
checking how to run the C preprocessor... gcc -E
checking for ANSI C header files... yes
checking for sys/types.h... yes
checking for sys/stat.h... yes
checking for stdlib.h... yes
checking for string.h... yes
checking for memory.h... yes
checking for strings.h... yes
checking for inttypes.h... yes
checking for stdint.h... yes
checking for unistd.h... yes
checking dlfcn.h usability... yes
checking dlfcn.h presence... yes
checking for dlfcn.h... yes
checking for g++... g++
checking whether we are using the GNU C++ compiler... yes
checking whether g++ accepts -g... yes
checking dependency style of g++... gcc3
checking how to run the C++ preprocessor... g++ -E
checking for g77... no
checking for xlf... no
checking for f77... no
checking for frt... no
checking for pgf77... no
checking for cf77... no
checking for fort77... no
checking for fl32... no
checking for af77... no
checking for xlf90... no
checking for f90... no
checking for pgf90... no
checking for pghpf... no
checking for epcf90... no
checking for gfortran... no
checking for g95... no
checking for xlf95... no
checking for f95... no
checking for fort... no
checking for ifort... no
checking for ifc... no
checking for efc... no
checking for pgf95... no
checking for lf95... no
checking for ftn... no
checking whether we are using the GNU Fortran 77 compiler... no
checking whether  accepts -g... no
checking the maximum length of command line arguments... 1572864
checking command to parse /usr/bin/nm -B output from gcc object... ok
checking for objdir... .libs
checking for ar... ar
checking for ranlib... ranlib
checking for strip... strip
checking if gcc supports -fno-rtti -fno-exceptions... no
checking for gcc option to produce PIC... -fPIC
checking if gcc PIC flag -fPIC works... yes
checking if gcc static flag -static works... yes
checking if gcc supports -c -o file.o... yes
checking whether the gcc linker (/usr/bin/ld -m elf_x86_64) supports shared libraries... yes
checking whether -lc should be explicitly linked in... no
checking dynamic linker characteristics... GNU/Linux ld.so
checking how to hardcode library paths into programs... immediate
checking whether stripping libraries is possible... yes
checking if libtool supports shared libraries... yes
checking whether to build shared libraries... yes
checking whether to build static libraries... yes
configure: creating libtool
appending configuration tag "CXX" to libtool
checking for ld used by g++... /usr/bin/ld -m elf_x86_64
checking if the linker (/usr/bin/ld -m elf_x86_64) is GNU ld... yes
checking whether the g++ linker (/usr/bin/ld -m elf_x86_64) supports shared libraries... yes
checking for g++ option to produce PIC... -fPIC
checking if g++ PIC flag -fPIC works... yes
checking if g++ static flag -static works... yes
checking if g++ supports -c -o file.o... yes
checking whether the g++ linker (/usr/bin/ld -m elf_x86_64) supports shared libraries... yes
checking dynamic linker characteristics... GNU/Linux ld.so
(cached) (cached) checking how to hardcode library paths into programs... immediate
appending configuration tag "F77" to libtool
checking for pkg-config... /usr/bin/pkg-config
checking pkg-config is at least version 0.9.0... yes
checking for HAL... yes
checking for arch type... x86_64-linux-gnu
checking for kernel type... Linux
checking for linux-based kernel... yes
checking for kernel source/headers... /lib/modules/2.6.31-20-generic/build
checking kernel version... 2.6.31-20-generic
checking for kernel module support... yes
checking for Xlib... yes
checking for XSERVER... yes
checking for xserver libc-wrapper header-files... no
checking if scaling tablet to screen size is needed... no
checking if Xorg server is version 1.4 or later... yes
checking if Xorg is 7.3 or earlier... no
checking if Xorg server is version 1.5.2 or later... yes
checking if Xorg server is version 1.6 or later... yes
checking if Xorg SDK defined IsXExtensionPointer... yes
checking if Xorg SDK defines dixScreenOrigins... yes
checking XInput extension version... >= 2.0
checking for lib xf86config... checking for X... libraries , headers 
checking for gethostbyname... yes
checking for connect... yes
checking for remove... yes
checking for shmat... yes
checking for IceConnectionNumber in -lICE... yes
checking for tclsh... /usr/bin/tclsh
checking for tcl version... 8.4
checking for tcl header files... found, /usr/include/tcl
checking for tk header files... found, /usr/include/tcl
checking ncurses.h usability... yes
checking ncurses.h presence... yes
checking for ncurses.h... yes
checking if libwacomcfg should/can be built... yes
checking if libwacomxi should/can be built... yes
checking if wacdump should/can be built... yes
checking if xidump should/can be built... yes
checking if xsetwacom should be built... yes
checking for Wacom X driver module path... /usr/lib/xorg/modules/input
checking for dynamic driver loading support... yes
checking if wacom_drv.{o,so} should be compiled... yes
checking if gcc accepts -fno-merge-constants... yes
checking if gcc accepts -fno-stack-protector... yes

configure: creating ./config.status
config.status: creating Makefile
config.status: creating mkxincludes
config.status: creating src/Makefile
config.status: creating src/util/Makefile
config.status: creating src/xdrv/Makefile
config.status: creating src/2.6.9/Makefile
config.status: creating src/2.6.10/Makefile
config.status: creating src/2.6.11/Makefile
config.status: creating src/2.6.13/Makefile
config.status: creating src/2.6.14/Makefile
config.status: creating src/2.6.15/Makefile
config.status: creating src/2.6.16/Makefile
config.status: creating src/2.6.18/Makefile
config.status: creating src/2.6.19/Makefile
config.status: creating src/2.6.22/Makefile
config.status: creating src/2.6.24/Makefile
config.status: creating src/2.6.26/Makefile
config.status: creating src/2.6.27/Makefile
config.status: creating src/wacomxi/Makefile
config.status: creating src/wacomxi/wacomcpl
config.status: creating src/include/xdrv-config.h
config.status: creating src/include/kernel-config.h
config.status: creating src/include/util-config.h
config.status: executing depfiles commands

----------------------------------------
  BUILD ENVIRONMENT:
       architecture - x86_64-linux-gnu
       linux kernel - yes 2.6.27
  module versioning - no 
      kernel source - yes /lib/modules/2.6.31-20-generic/build
     XFree86 source - no 
           Xorg SDK - yes /usr/include/xorg
          XSERVER64 - yes
           dlloader - yes
               XLib - yes /usr/lib
         xf86config - no
                TCL - yes /usr/include/tcl
                 TK - yes /usr/include/tcl
            ncurses - yes

  BUILD OPTIONS:
            wacom.o - yes
            wacdump - yes 
             xidump - yes 
        libwacomcfg - yes
         libwacomxi - yes
          xsetwacom - yes
              hid.o - no 
       wacom_drv.so - yes /usr/lib/xorg/modules/input 
        wacom_drv.o - no
  wacom*_drv quirks - hal IsXExtensionPointer key-events dixScreenOrigins
----------------------------------------
tj@xt2:~/lw-ntrig/linuxwacom-0.8.5-10$ make
Making all in src
make[1]: Entering directory `/home/tj/lw-ntrig/linuxwacom-0.8.5-10/src'
Making all in .
make[2]: Entering directory `/home/tj/lw-ntrig/linuxwacom-0.8.5-10/src'
rm -f wacom.4x.gz
gzip -9c < ./wacom.4x > wacom.4x.gz
make[2]: Leaving directory `/home/tj/lw-ntrig/linuxwacom-0.8.5-10/src'
Making all in wacomxi
make[2]: Entering directory `/home/tj/lw-ntrig/linuxwacom-0.8.5-10/src/wacomxi'
/bin/bash ../../libtool --tag=CC   --mode=compile gcc -DHAVE_CONFIG_H -I. -I../../src/include    -Wall -g -O2 -D__amd64__ -I/usr/include/tcl -MT wacomxi.lo -MD -MP -MF .deps/wacomxi.Tpo -c -o wacomxi.lo wacomxi.c
mkdir .libs
 gcc -DHAVE_CONFIG_H -I. -I../../src/include -Wall -g -O2 -D__amd64__ -I/usr/include/tcl -MT wacomxi.lo -MD -MP -MF .deps/wacomxi.Tpo -c wacomxi.c  -fPIC -DPIC -o .libs/wacomxi.o
 gcc -DHAVE_CONFIG_H -I. -I../../src/include -Wall -g -O2 -D__amd64__ -I/usr/include/tcl -MT wacomxi.lo -MD -MP -MF .deps/wacomxi.Tpo -c wacomxi.c -o wacomxi.o >/dev/null 2>&1
mv -f .deps/wacomxi.Tpo .deps/wacomxi.Plo
/bin/bash ../../libtool --tag=CC   --mode=link gcc -Wall -g -O2 -D__amd64__ -I/usr/include/tcl -no-undefined  -o libwacomxi.la -rpath /usr/lib/TkXInput wacomxi.lo -L/usr/lib -lX11 -lXi 
gcc -shared  .libs/wacomxi.o  -L/usr/lib -lX11 -lXi  -Wl,-soname -Wl,libwacomxi.so.0 -o .libs/libwacomxi.so.0.0.0
(cd .libs && rm -f libwacomxi.so.0 && ln -s libwacomxi.so.0.0.0 libwacomxi.so.0)
(cd .libs && rm -f libwacomxi.so && ln -s libwacomxi.so.0.0.0 libwacomxi.so)
ar cru .libs/libwacomxi.a  wacomxi.o
ranlib .libs/libwacomxi.a
creating libwacomxi.la
(cd .libs && rm -f libwacomxi.la && ln -s ../libwacomxi.la libwacomxi.la)
make[2]: Leaving directory `/home/tj/lw-ntrig/linuxwacom-0.8.5-10/src/wacomxi'
Making all in util
make[2]: Entering directory `/home/tj/lw-ntrig/linuxwacom-0.8.5-10/src/util'
/bin/bash ../../libtool --tag=CC   --mode=compile gcc -DHAVE_CONFIG_H -I. -I../../src/include    -Wall -pedantic -I/usr/include/xorg  -DDBUS_API_SUBJECT_TO_CHANGE -I/usr/include/hal -I/usr/include/dbus-1.0 -I/usr/lib/dbus-1.0/include   -g -O2 -D__amd64__ -I/usr/include/tcl -MT wacomcfg.lo -MD -MP -MF .deps/wacomcfg.Tpo -c -o wacomcfg.lo wacomcfg.c
mkdir .libs
 gcc -DHAVE_CONFIG_H -I. -I../../src/include -Wall -pedantic -I/usr/include/xorg -DDBUS_API_SUBJECT_TO_CHANGE -I/usr/include/hal -I/usr/include/dbus-1.0 -I/usr/lib/dbus-1.0/include -g -O2 -D__amd64__ -I/usr/include/tcl -MT wacomcfg.lo -MD -MP -MF .deps/wacomcfg.Tpo -c wacomcfg.c  -fPIC -DPIC -o .libs/wacomcfg.o
 gcc -DHAVE_CONFIG_H -I. -I../../src/include -Wall -pedantic -I/usr/include/xorg -DDBUS_API_SUBJECT_TO_CHANGE -I/usr/include/hal -I/usr/include/dbus-1.0 -I/usr/lib/dbus-1.0/include -g -O2 -D__amd64__ -I/usr/include/tcl -MT wacomcfg.lo -MD -MP -MF .deps/wacomcfg.Tpo -c wacomcfg.c -o wacomcfg.o >/dev/null 2>&1
mv -f .deps/wacomcfg.Tpo .deps/wacomcfg.Plo
/bin/bash ../../libtool --tag=CC   --mode=link gcc -Wall -pedantic -I/usr/include/xorg  -DDBUS_API_SUBJECT_TO_CHANGE -I/usr/include/hal -I/usr/include/dbus-1.0 -I/usr/lib/dbus-1.0/include   -g -O2 -D__amd64__ -I/usr/include/tcl -no-undefined -version-info 0:1:0  -o libwacomcfg.la -rpath /usr/lib wacomcfg.lo -L/usr/lib -lX11 -lXi 
gcc -shared  .libs/wacomcfg.o  -L/usr/lib -lX11 -lXi  -Wl,-soname -Wl,libwacomcfg.so.0 -o .libs/libwacomcfg.so.0.0.1
(cd .libs && rm -f libwacomcfg.so.0 && ln -s libwacomcfg.so.0.0.1 libwacomcfg.so.0)
(cd .libs && rm -f libwacomcfg.so && ln -s libwacomcfg.so.0.0.1 libwacomcfg.so)
ar cru .libs/libwacomcfg.a  wacomcfg.o
ranlib .libs/libwacomcfg.a
creating libwacomcfg.la
(cd .libs && rm -f libwacomcfg.la && ln -s ../libwacomcfg.la libwacomcfg.la)
gcc -DHAVE_CONFIG_H -I. -I../../src/include    -Wall -pedantic -I/usr/include/xorg  -DDBUS_API_SUBJECT_TO_CHANGE -I/usr/include/hal -I/usr/include/dbus-1.0 -I/usr/lib/dbus-1.0/include   -g -O2 -D__amd64__ -I/usr/include/tcl -MT wacdump.o -MD -MP -MF .deps/wacdump.Tpo -c -o wacdump.o wacdump.c
mv -f .deps/wacdump.Tpo .deps/wacdump.Po
gcc -DHAVE_CONFIG_H -I. -I../../src/include    -Wall -pedantic -I/usr/include/xorg  -DDBUS_API_SUBJECT_TO_CHANGE -I/usr/include/hal -I/usr/include/dbus-1.0 -I/usr/lib/dbus-1.0/include   -g -O2 -D__amd64__ -I/usr/include/tcl -MT wacscrn.o -MD -MP -MF .deps/wacscrn.Tpo -c -o wacscrn.o wacscrn.c
mv -f .deps/wacscrn.Tpo .deps/wacscrn.Po
gcc -DHAVE_CONFIG_H -I. -I../../src/include    -Wall -pedantic -I/usr/include/xorg  -DDBUS_API_SUBJECT_TO_CHANGE -I/usr/include/hal -I/usr/include/dbus-1.0 -I/usr/lib/dbus-1.0/include   -g -O2 -D__amd64__ -I/usr/include/tcl -MT wactablet.o -MD -MP -MF .deps/wactablet.Tpo -c -o wactablet.o wactablet.c
mv -f .deps/wactablet.Tpo .deps/wactablet.Po
gcc -DHAVE_CONFIG_H -I. -I../../src/include    -Wall -pedantic -I/usr/include/xorg  -DDBUS_API_SUBJECT_TO_CHANGE -I/usr/include/hal -I/usr/include/dbus-1.0 -I/usr/lib/dbus-1.0/include   -g -O2 -D__amd64__ -I/usr/include/tcl -MT wacserial.o -MD -MP -MF .deps/wacserial.Tpo -c -o wacserial.o wacserial.c
wacserial.c: In function ‘WacomFlush’:
wacserial.c:1345: warning: ignoring return value of ‘read’, declared with attribute warn_unused_result
mv -f .deps/wacserial.Tpo .deps/wacserial.Po
gcc -DHAVE_CONFIG_H -I. -I../../src/include    -Wall -pedantic -I/usr/include/xorg  -DDBUS_API_SUBJECT_TO_CHANGE -I/usr/include/hal -I/usr/include/dbus-1.0 -I/usr/lib/dbus-1.0/include   -g -O2 -D__amd64__ -I/usr/include/tcl -MT wacusb.o -MD -MP -MF .deps/wacusb.Tpo -c -o wacusb.o wacusb.c
mv -f .deps/wacusb.Tpo .deps/wacusb.Po
/bin/bash ../../libtool --tag=CC   --mode=link gcc -Wall -pedantic -I/usr/include/xorg  -DDBUS_API_SUBJECT_TO_CHANGE -I/usr/include/hal -I/usr/include/dbus-1.0 -I/usr/lib/dbus-1.0/include   -g -O2 -D__amd64__ -I/usr/include/tcl   -o wacdump wacdump.o wacscrn.o wactablet.o wacserial.o wacusb.o -lncurses 
gcc -Wall -pedantic -I/usr/include/xorg -DDBUS_API_SUBJECT_TO_CHANGE -I/usr/include/hal -I/usr/include/dbus-1.0 -I/usr/lib/dbus-1.0/include -g -O2 -D__amd64__ -I/usr/include/tcl -o wacdump wacdump.o wacscrn.o wactablet.o wacserial.o wacusb.o  -lncurses  
gcc -DHAVE_CONFIG_H -I. -I../../src/include    -Wall -pedantic -I/usr/include/xorg  -DDBUS_API_SUBJECT_TO_CHANGE -I/usr/include/hal -I/usr/include/dbus-1.0 -I/usr/lib/dbus-1.0/include   -g -O2 -D__amd64__ -I/usr/include/tcl -MT xidump.o -MD -MP -MF .deps/xidump.Tpo -c -o xidump.o xidump.c
xidump.c: In function ‘RawRunAccel’:
xidump.c:770: warning: dereferencing pointer ‘pMove’ does break strict-aliasing rules
xidump.c:769: note: initialized from here
xidump.c:772: warning: dereferencing pointer ‘event.63’ does break strict-aliasing rules
xidump.c:772: note: initialized from here
xidump.c:774: warning: dereferencing pointer ‘event.63’ does break strict-aliasing rules
xidump.c:774: note: initialized from here
xidump.c: In function ‘RawRun’:
xidump.c:718: warning: dereferencing pointer ‘pAny.58’ does break strict-aliasing rules
xidump.c:718: note: initialized from here
xidump.c:717: warning: dereferencing pointer ‘pAny.58’ does break strict-aliasing rules
xidump.c:717: note: initialized from here
xidump.c:716: warning: dereferencing pointer ‘pAny.58’ does break strict-aliasing rules
xidump.c:716: note: initialized from here
xidump.c:711: warning: dereferencing pointer ‘pAny.58’ does break strict-aliasing rules
xidump.c:715: note: initialized from here
xidump.c:711: warning: dereferencing pointer ‘pAny.58’ does break strict-aliasing rules
xidump.c:714: note: initialized from here
xidump.c:711: warning: dereferencing pointer ‘pAny.58’ does break strict-aliasing rules
xidump.c:713: note: initialized from here
xidump.c:725: warning: dereferencing pointer ‘pBtn’ does break strict-aliasing rules
xidump.c:724: note: initialized from here
xidump.c:733: warning: dereferencing pointer ‘pKey’ does break strict-aliasing rules
xidump.c:732: note: initialized from here
xidump.c: In function ‘CursesRun’:
xidump.c:571: warning: dereferencing pointer ‘pAny.53’ does break strict-aliasing rules
xidump.c:572: note: initialized from here
xidump.c:580: warning: dereferencing pointer ‘pAny.53’ does break strict-aliasing rules
xidump.c:580: note: initialized from here
xidump.c:590: warning: dereferencing pointer ‘pAny.53’ does break strict-aliasing rules
xidump.c:590: note: initialized from here
xidump.c:625: warning: dereferencing pointer ‘pBtn’ does break strict-aliasing rules
xidump.c:623: warning: dereferencing pointer ‘pBtn’ does break strict-aliasing rules
xidump.c:620: note: initialized from here
xidump.c:642: warning: dereferencing pointer ‘pKey’ does break strict-aliasing rules
xidump.c:640: warning: dereferencing pointer ‘pKey’ does break strict-aliasing rules
xidump.c:638: note: initialized from here
mv -f .deps/xidump.Tpo .deps/xidump.Po
/bin/bash ../../libtool --tag=CC   --mode=link gcc -Wall -pedantic -I/usr/include/xorg  -DDBUS_API_SUBJECT_TO_CHANGE -I/usr/include/hal -I/usr/include/dbus-1.0 -I/usr/lib/dbus-1.0/include   -g -O2 -D__amd64__ -I/usr/include/tcl -L/usr/lib -lX11 -lXi -lm  -o xidump xidump.o wacscrn.o -lncurses 
gcc -Wall -pedantic -I/usr/include/xorg -DDBUS_API_SUBJECT_TO_CHANGE -I/usr/include/hal -I/usr/include/dbus-1.0 -I/usr/lib/dbus-1.0/include -g -O2 -D__amd64__ -I/usr/include/tcl -o xidump xidump.o wacscrn.o  -L/usr/lib -lX11 -lXi -lm -lncurses  
gcc -DHAVE_CONFIG_H -I. -I../../src/include    -Wall -pedantic -I/usr/include/xorg  -DDBUS_API_SUBJECT_TO_CHANGE -I/usr/include/hal -I/usr/include/dbus-1.0 -I/usr/lib/dbus-1.0/include   -g -O2 -D__amd64__ -I/usr/include/tcl -MT xsetwacom.o -MD -MP -MF .deps/xsetwacom.Tpo -c -o xsetwacom.o xsetwacom.c
mv -f .deps/xsetwacom.Tpo .deps/xsetwacom.Po
gcc -DHAVE_CONFIG_H -I. -I../../src/include    -Wall -pedantic -I/usr/include/xorg  -DDBUS_API_SUBJECT_TO_CHANGE -I/usr/include/hal -I/usr/include/dbus-1.0 -I/usr/lib/dbus-1.0/include   -g -O2 -D__amd64__ -I/usr/include/tcl -MT wcmAction.o -MD -MP -MF .deps/wcmAction.Tpo -c -o wcmAction.o wcmAction.c
mv -f .deps/wcmAction.Tpo .deps/wcmAction.Po
/bin/bash ../../libtool --tag=CC   --mode=link gcc -Wall -pedantic -I/usr/include/xorg  -DDBUS_API_SUBJECT_TO_CHANGE -I/usr/include/hal -I/usr/include/dbus-1.0 -I/usr/lib/dbus-1.0/include   -g -O2 -D__amd64__ -I/usr/include/tcl   -o xsetwacom xsetwacom.o wcmAction.o libwacomcfg.la 
gcc -Wall -pedantic -I/usr/include/xorg -DDBUS_API_SUBJECT_TO_CHANGE -I/usr/include/hal -I/usr/include/dbus-1.0 -I/usr/lib/dbus-1.0/include -g -O2 -D__amd64__ -I/usr/include/tcl -o .libs/xsetwacom xsetwacom.o wcmAction.o  ./.libs/libwacomcfg.so -L/usr/lib -lX11 -lXi 
creating xsetwacom
gcc -DHAVE_CONFIG_H -I. -I../../src/include    -Wall -pedantic -I/usr/include/xorg  -DDBUS_API_SUBJECT_TO_CHANGE -I/usr/include/hal -I/usr/include/dbus-1.0 -I/usr/lib/dbus-1.0/include   -g -O2 -D__amd64__ -I/usr/include/tcl -MT hal-setup-wacom.o -MD -MP -MF .deps/hal-setup-wacom.Tpo -c -o hal-setup-wacom.o hal-setup-wacom.c
hal-setup-wacom.c: In function ‘main’:
hal-setup-wacom.c:54: warning: ignoring return value of ‘asprintf’, declared with attribute warn_unused_result
hal-setup-wacom.c:137: warning: ignoring return value of ‘asprintf’, declared with attribute warn_unused_result
mv -f .deps/hal-setup-wacom.Tpo .deps/hal-setup-wacom.Po
/bin/bash ../../libtool --tag=CC   --mode=link gcc -Wall -pedantic -I/usr/include/xorg  -DDBUS_API_SUBJECT_TO_CHANGE -I/usr/include/hal -I/usr/include/dbus-1.0 -I/usr/lib/dbus-1.0/include   -g -O2 -D__amd64__ -I/usr/include/tcl   -o hal-setup-wacom hal-setup-wacom.o -L/lib -lhal -ldbus-1 -lpthread -lrt   
gcc -Wall -pedantic -I/usr/include/xorg -DDBUS_API_SUBJECT_TO_CHANGE -I/usr/include/hal -I/usr/include/dbus-1.0 -I/usr/lib/dbus-1.0/include -g -O2 -D__amd64__ -I/usr/include/tcl -o hal-setup-wacom hal-setup-wacom.o  -L/lib -lhal -ldbus-1 -lpthread -lrt  
make[2]: Leaving directory `/home/tj/lw-ntrig/linuxwacom-0.8.5-10/src/util'
Making all in xdrv
make[2]: Entering directory `/home/tj/lw-ntrig/linuxwacom-0.8.5-10/src/xdrv'
gcc -MM -g -O2 -D__amd64__ -I/usr/include/tcl  -I../include -I/usr/include/xorg   ./xf86Wacom.c ./wcmSerial.c ./wcmUSB.c ./wcmISDV4.c ./wcmXCommand.c ./wcmCommon.c ./wcmCompat.c ./wcmConfig.c ./wcmFilter.c ./wcmTilt2Rotation.c ./wcmTouchFilter.c ./wcmValidateDevice.c ./wcmMapping.c > .depend
make[2]: Leaving directory `/home/tj/lw-ntrig/linuxwacom-0.8.5-10/src/xdrv'
make[2]: Entering directory `/home/tj/lw-ntrig/linuxwacom-0.8.5-10/src/xdrv'
gcc -g -O2 -D__amd64__ -I/usr/include/tcl  -fPIC -pipe -std=c99 \
		-pedantic -Wall -Wpointer-arith -fno-merge-constants \
		-fno-stack-protector -I. -I../include -I/usr/include/xorg   \
		-D_XSERVER64 -I/usr/include/xorg -I/usr/include/pixman-1   \
		-o xf86Wacom.o -c ./xf86Wacom.c
In file included from ./xf86Wacom.h:27,
                 from ./xf86Wacom.c:102:
/usr/include/xorg/xorg-server.h:105:1: warning: "XKB" redefined
In file included from ./xf86Wacom.h:25,
                 from ./xf86Wacom.c:102:
./../include/xdrv-config.h:18:1: warning: this is the location of the previous definition
In file included from ./xf86Wacom.h:27,
                 from ./xf86Wacom.c:102:
/usr/include/xorg/xorg-server.h:195:1: warning: "XFree86LOADER" redefined
In file included from ./xf86Wacom.h:25,
                 from ./xf86Wacom.c:102:
./../include/xdrv-config.h:12:1: warning: this is the location of the previous definition
gcc -g -O2 -D__amd64__ -I/usr/include/tcl  -fPIC -pipe -std=c99 \
		-pedantic -Wall -Wpointer-arith -fno-merge-constants \
		-fno-stack-protector -I. -I../include -I/usr/include/xorg   \
		-D_XSERVER64 -I/usr/include/xorg -I/usr/include/pixman-1   \
		-o wcmSerial.o -c ./wcmSerial.c
In file included from ./xf86Wacom.h:27,
                 from ./wcmSerial.c:20:
/usr/include/xorg/xorg-server.h:105:1: warning: "XKB" redefined
In file included from ./xf86Wacom.h:25,
                 from ./wcmSerial.c:20:
./../include/xdrv-config.h:18:1: warning: this is the location of the previous definition
In file included from ./xf86Wacom.h:27,
                 from ./wcmSerial.c:20:
/usr/include/xorg/xorg-server.h:195:1: warning: "XFree86LOADER" redefined
In file included from ./xf86Wacom.h:25,
                 from ./wcmSerial.c:20:
./../include/xdrv-config.h:12:1: warning: this is the location of the previous definition
gcc -g -O2 -D__amd64__ -I/usr/include/tcl  -fPIC -pipe -std=c99 \
		-pedantic -Wall -Wpointer-arith -fno-merge-constants \
		-fno-stack-protector -I. -I../include -I/usr/include/xorg   \
		-D_XSERVER64 -I/usr/include/xorg -I/usr/include/pixman-1   \
		-o wcmUSB.o -c ./wcmUSB.c
In file included from ./xf86Wacom.h:27,
                 from ./wcmUSB.c:20:
/usr/include/xorg/xorg-server.h:105:1: warning: "XKB" redefined
In file included from ./xf86Wacom.h:25,
                 from ./wcmUSB.c:20:
./../include/xdrv-config.h:18:1: warning: this is the location of the previous definition
In file included from ./xf86Wacom.h:27,
                 from ./wcmUSB.c:20:
/usr/include/xorg/xorg-server.h:195:1: warning: "XFree86LOADER" redefined
In file included from ./xf86Wacom.h:25,
                 from ./wcmUSB.c:20:
./../include/xdrv-config.h:12:1: warning: this is the location of the previous definition
./wcmUSB.c:496: error: expected ‘}’ before ‘{’ token
make[2]: *** [wcmUSB.o] Error 1
make[2]: Leaving directory `/home/tj/lw-ntrig/linuxwacom-0.8.5-10/src/xdrv'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/tj/lw-ntrig/linuxwacom-0.8.5-10/src'
make: *** [all-recursive] Error 1
tj@xt2:~/lw-ntrig/linuxwacom-0.8.5-10$ sudo make install
[sudo] password for tj: 
Making install in src
make[1]: Entering directory `/home/tj/lw-ntrig/linuxwacom-0.8.5-10/src'
Making install in .
make[2]: Entering directory `/home/tj/lw-ntrig/linuxwacom-0.8.5-10/src'
make[3]: Entering directory `/home/tj/lw-ntrig/linuxwacom-0.8.5-10/src'
make[3]: Nothing to be done for `install-exec-am'.
test -z "/usr/share/man/man4" || /bin/mkdir -p "/usr/share/man/man4"
 /usr/bin/install -c -m 644 'wacom.4x.gz' '/usr/share/man/man4/wacom.4x.gz'
make[3]: Leaving directory `/home/tj/lw-ntrig/linuxwacom-0.8.5-10/src'
make[2]: Leaving directory `/home/tj/lw-ntrig/linuxwacom-0.8.5-10/src'
Making install in wacomxi
make[2]: Entering directory `/home/tj/lw-ntrig/linuxwacom-0.8.5-10/src/wacomxi'
make[3]: Entering directory `/home/tj/lw-ntrig/linuxwacom-0.8.5-10/src/wacomxi'
make[3]: Nothing to be done for `install-exec-am'.
test -z "/usr/bin" || /bin/mkdir -p "/usr/bin"
 /usr/bin/install -c 'wacomcpl' '/usr/bin/wacomcpl'
 /usr/bin/install -c 'wacomcpl-exec' '/usr/bin/wacomcpl-exec'
test -z "/usr/lib/TkXInput" || /bin/mkdir -p "/usr/lib/TkXInput"
 /usr/bin/install -c -m 644 'pkgIndex.tcl' '/usr/lib/TkXInput/pkgIndex.tcl'
test -z "/usr/lib/TkXInput" || /bin/mkdir -p "/usr/lib/TkXInput"
 /bin/bash ../../libtool   --mode=install /usr/bin/install -c  'libwacomxi.la' '/usr/lib/TkXInput/libwacomxi.la'
/usr/bin/install -c .libs/libwacomxi.so.0.0.0 /usr/lib/TkXInput/libwacomxi.so.0.0.0
(cd /usr/lib/TkXInput && { ln -s -f libwacomxi.so.0.0.0 libwacomxi.so.0 || { rm -f libwacomxi.so.0 && ln -s libwacomxi.so.0.0.0 libwacomxi.so.0; }; })
(cd /usr/lib/TkXInput && { ln -s -f libwacomxi.so.0.0.0 libwacomxi.so || { rm -f libwacomxi.so && ln -s libwacomxi.so.0.0.0 libwacomxi.so; }; })
/usr/bin/install -c .libs/libwacomxi.lai /usr/lib/TkXInput/libwacomxi.la
/usr/bin/install -c .libs/libwacomxi.a /usr/lib/TkXInput/libwacomxi.a
chmod 644 /usr/lib/TkXInput/libwacomxi.a
ranlib /usr/lib/TkXInput/libwacomxi.a
PATH="$PATH:/sbin" ldconfig -n /usr/lib/TkXInput
----------------------------------------------------------------------
Libraries have been installed in:
   /usr/lib/TkXInput

If you ever happen to want to link against installed libraries
in a given directory, LIBDIR, you must either use libtool, and
specify the full pathname of the library, or use the `-LLIBDIR'
flag during linking and do at least one of the following:
   - add LIBDIR to the `LD_LIBRARY_PATH' environment variable
     during execution
   - add LIBDIR to the `LD_RUN_PATH' environment variable
     during linking
   - use the `-Wl,--rpath -Wl,LIBDIR' linker flag
   - have your system administrator add LIBDIR to `/etc/ld.so.conf'

See any operating system documentation about shared libraries for
more information, such as the ld(1) and ld.so(8) manual pages.
----------------------------------------------------------------------
make[3]: Leaving directory `/home/tj/lw-ntrig/linuxwacom-0.8.5-10/src/wacomxi'
make[2]: Leaving directory `/home/tj/lw-ntrig/linuxwacom-0.8.5-10/src/wacomxi'
Making install in util
make[2]: Entering directory `/home/tj/lw-ntrig/linuxwacom-0.8.5-10/src/util'
make[3]: Entering directory `/home/tj/lw-ntrig/linuxwacom-0.8.5-10/src/util'
test -z "/usr/lib" || /bin/mkdir -p "/usr/lib"
 /bin/bash ../../libtool   --mode=install /usr/bin/install -c  'libwacomcfg.la' '/usr/lib/libwacomcfg.la'
/usr/bin/install -c .libs/libwacomcfg.so.0.0.1 /usr/lib/libwacomcfg.so.0.0.1
(cd /usr/lib && { ln -s -f libwacomcfg.so.0.0.1 libwacomcfg.so.0 || { rm -f libwacomcfg.so.0 && ln -s libwacomcfg.so.0.0.1 libwacomcfg.so.0; }; })
(cd /usr/lib && { ln -s -f libwacomcfg.so.0.0.1 libwacomcfg.so || { rm -f libwacomcfg.so && ln -s libwacomcfg.so.0.0.1 libwacomcfg.so; }; })
/usr/bin/install -c .libs/libwacomcfg.lai /usr/lib/libwacomcfg.la
/usr/bin/install -c .libs/libwacomcfg.a /usr/lib/libwacomcfg.a
chmod 644 /usr/lib/libwacomcfg.a
ranlib /usr/lib/libwacomcfg.a
PATH="$PATH:/sbin" ldconfig -n /usr/lib
----------------------------------------------------------------------
Libraries have been installed in:
   /usr/lib

If you ever happen to want to link against installed libraries
in a given directory, LIBDIR, you must either use libtool, and
specify the full pathname of the library, or use the `-LLIBDIR'
flag during linking and do at least one of the following:
   - add LIBDIR to the `LD_LIBRARY_PATH' environment variable
     during execution
   - add LIBDIR to the `LD_RUN_PATH' environment variable
     during linking
   - use the `-Wl,--rpath -Wl,LIBDIR' linker flag
   - have your system administrator add LIBDIR to `/etc/ld.so.conf'

See any operating system documentation about shared libraries for
more information, such as the ld(1) and ld.so(8) manual pages.
----------------------------------------------------------------------
test -z "/usr/bin" || /bin/mkdir -p "/usr/bin"
  /bin/bash ../../libtool   --mode=install /usr/bin/install -c 'wacdump' '/usr/bin/wacdump'
/usr/bin/install -c wacdump /usr/bin/wacdump
  /bin/bash ../../libtool   --mode=install /usr/bin/install -c 'xidump' '/usr/bin/xidump'
/usr/bin/install -c xidump /usr/bin/xidump
  /bin/bash ../../libtool   --mode=install /usr/bin/install -c 'xsetwacom' '/usr/bin/xsetwacom'
/usr/bin/install -c .libs/xsetwacom /usr/bin/xsetwacom
test -z "/usr/libexec" || /bin/mkdir -p "/usr/libexec"
  /bin/bash ../../libtool   --mode=install /usr/bin/install -c 'hal-setup-wacom' '/usr/libexec/hal-setup-wacom'
/usr/bin/install -c hal-setup-wacom /usr/libexec/hal-setup-wacom
test -z "/usr/share/hal/fdi/policy/20thirdparty" || /bin/mkdir -p "/usr/share/hal/fdi/policy/20thirdparty"
 /usr/bin/install -c '10-linuxwacom.fdi' '/usr/share/hal/fdi/policy/20thirdparty/10-linuxwacom.fdi'
test -z "/usr/include/wacomcfg" || /bin/mkdir -p "/usr/include/wacomcfg"
 /usr/bin/install -c -m 644 'wacomcfg.h' '/usr/include/wacomcfg/wacomcfg.h'
make[3]: Leaving directory `/home/tj/lw-ntrig/linuxwacom-0.8.5-10/src/util'
make[2]: Leaving directory `/home/tj/lw-ntrig/linuxwacom-0.8.5-10/src/util'
Making install in xdrv
make[2]: Entering directory `/home/tj/lw-ntrig/linuxwacom-0.8.5-10/src/xdrv'
gcc -g -O2 -D__amd64__ -I/usr/include/tcl  -fPIC -pipe -std=c99 \
		-pedantic -Wall -Wpointer-arith -fno-merge-constants \
		-fno-stack-protector -I. -I../include -I/usr/include/xorg   \
		-D_XSERVER64 -I/usr/include/xorg -I/usr/include/pixman-1   \
		-o wcmUSB.o -c ./wcmUSB.c
In file included from ./xf86Wacom.h:27,
                 from ./wcmUSB.c:20:
/usr/include/xorg/xorg-server.h:105:1: warning: "XKB" redefined
In file included from ./xf86Wacom.h:25,
                 from ./wcmUSB.c:20:
./../include/xdrv-config.h:18:1: warning: this is the location of the previous definition
In file included from ./xf86Wacom.h:27,
                 from ./wcmUSB.c:20:
/usr/include/xorg/xorg-server.h:195:1: warning: "XFree86LOADER" redefined
In file included from ./xf86Wacom.h:25,
                 from ./wcmUSB.c:20:
./../include/xdrv-config.h:12:1: warning: this is the location of the previous definition
./wcmUSB.c:496: error: expected ‘}’ before ‘{’ token
make[2]: *** [wcmUSB.o] Error 1
make[2]: Leaving directory `/home/tj/lw-ntrig/linuxwacom-0.8.5-10/src/xdrv'
make[1]: *** [install-recursive] Error 1
make[1]: Leaving directory `/home/tj/lw-ntrig/linuxwacom-0.8.5-10/src'
make: *** [install-recursive] Error 1

```

---

### Post by Favux on 2010-02-21
Shoot.  I just changed the HOW TO for it.  Let me look at it.  This may take a while.

Worst comes to worst I can just manually change wcmUSB.c.  It's not that big and only a few lines need to be changed.

---

### Post by -TJ on 2010-02-21
Okay. Once you get that done, you can tell me what to change. =]
Good thing I just tested it.

---

### Post by Favux on 2010-02-21
Darn good thing you tested it.

Let's see if he just accidentally left his makefile in.  Change his intructions to (since you've already downloaded it and unpacked it and made the new directory):
```
cd lw-ntrig
cd linuxwacom-0.8.5-10
make clean
make distclean
./configure --enable-wacom --prefix=/usr
make
sudo make install
```
Although why wcmUSB.c would be complaining?

---

### Post by -TJ on 2010-02-21
It happened again:

```
tj@xt2:~$ cd lw-ntrig
tj@xt2:~/lw-ntrig$ cd linuxwacom-0.8.5-10
tj@xt2:~/lw-ntrig/linuxwacom-0.8.5-10$ make clean
Making clean in src
make[1]: Entering directory `/home/tj/lw-ntrig/linuxwacom-0.8.5-10/src'
Making clean in 2.6.27
make[2]: Entering directory `/home/tj/lw-ntrig/linuxwacom-0.8.5-10/src/2.6.27'
rm -rf *.o *.ko *.mod.* .[a-z]* core *.i
make[2]: Leaving directory `/home/tj/lw-ntrig/linuxwacom-0.8.5-10/src/2.6.27'
Making clean in xdrv
make[2]: Entering directory `/home/tj/lw-ntrig/linuxwacom-0.8.5-10/src/xdrv'
rm -rf .libs _libs
rm -f *.lo
make[2]: Leaving directory `/home/tj/lw-ntrig/linuxwacom-0.8.5-10/src/xdrv'
Making clean in util
make[2]: Entering directory `/home/tj/lw-ntrig/linuxwacom-0.8.5-10/src/util'
 rm -f wacdump wacdump
 rm -f xidump xidump
 rm -f xsetwacom xsetwacom
test -z "libwacomcfg.la" || rm -f libwacomcfg.la
rm -f "./so_locations"
 rm -f hal-setup-wacom hal-setup-wacom
rm -rf .libs _libs
rm -f *.o
rm -f *.lo
make[2]: Leaving directory `/home/tj/lw-ntrig/linuxwacom-0.8.5-10/src/util'
Making clean in wacomxi
make[2]: Entering directory `/home/tj/lw-ntrig/linuxwacom-0.8.5-10/src/wacomxi'
rm -rf .libs _libs
test -z "libwacomxi.la" || rm -f libwacomxi.la
rm -f "./so_locations"
rm -f *.o
rm -f *.lo
make[2]: Leaving directory `/home/tj/lw-ntrig/linuxwacom-0.8.5-10/src/wacomxi'
Making clean in .
make[2]: Entering directory `/home/tj/lw-ntrig/linuxwacom-0.8.5-10/src'
rm -rf .libs _libs
rm -f *.lo
make[2]: Leaving directory `/home/tj/lw-ntrig/linuxwacom-0.8.5-10/src'
make[1]: Leaving directory `/home/tj/lw-ntrig/linuxwacom-0.8.5-10/src'
Making clean in .
make[1]: Entering directory `/home/tj/lw-ntrig/linuxwacom-0.8.5-10'
rm -rf .libs _libs
rm -f *.lo
make[1]: Leaving directory `/home/tj/lw-ntrig/linuxwacom-0.8.5-10'
tj@xt2:~/lw-ntrig/linuxwacom-0.8.5-10$ make distclean
Making distclean in src
make[1]: Entering directory `/home/tj/lw-ntrig/linuxwacom-0.8.5-10/src'
Making distclean in 2.6.27
make[2]: Entering directory `/home/tj/lw-ntrig/linuxwacom-0.8.5-10/src/2.6.27'
make[2]: Nothing to be done for `distclean'.
make[2]: Leaving directory `/home/tj/lw-ntrig/linuxwacom-0.8.5-10/src/2.6.27'
Making distclean in xdrv
make[2]: Entering directory `/home/tj/lw-ntrig/linuxwacom-0.8.5-10/src/xdrv'
rm -rf .libs _libs
rm -f *.lo
test -z "" || rm -f 
rm -f Makefile
make[2]: Leaving directory `/home/tj/lw-ntrig/linuxwacom-0.8.5-10/src/xdrv'
Making distclean in util
make[2]: Entering directory `/home/tj/lw-ntrig/linuxwacom-0.8.5-10/src/util'
 rm -f wacdump wacdump
 rm -f xidump xidump
 rm -f xsetwacom xsetwacom
test -z "libwacomcfg.la" || rm -f libwacomcfg.la
rm -f "./so_locations"
 rm -f hal-setup-wacom hal-setup-wacom
rm -rf .libs _libs
rm -f *.o
rm -f *.lo
rm -f *.tab.c
test -z "" || rm -f 
rm -f TAGS ID GTAGS GRTAGS GSYMS GPATH tags
rm -rf ./.deps
rm -f Makefile
make[2]: Leaving directory `/home/tj/lw-ntrig/linuxwacom-0.8.5-10/src/util'
Making distclean in wacomxi
make[2]: Entering directory `/home/tj/lw-ntrig/linuxwacom-0.8.5-10/src/wacomxi'
rm -rf .libs _libs
test -z "libwacomxi.la" || rm -f libwacomxi.la
rm -f "./so_locations"
rm -f *.o
rm -f *.lo
rm -f *.tab.c
test -z "wacomcpl" || rm -f wacomcpl
rm -f TAGS ID GTAGS GRTAGS GSYMS GPATH tags
rm -rf ./.deps
rm -f Makefile
make[2]: Leaving directory `/home/tj/lw-ntrig/linuxwacom-0.8.5-10/src/wacomxi'
Making distclean in .
make[2]: Entering directory `/home/tj/lw-ntrig/linuxwacom-0.8.5-10/src'
rm -rf .libs _libs
rm -f *.lo
test -z "" || rm -f 
rm -f TAGS ID GTAGS GRTAGS GSYMS GPATH tags
make[2]: Leaving directory `/home/tj/lw-ntrig/linuxwacom-0.8.5-10/src'
rm -f Makefile
make[1]: Leaving directory `/home/tj/lw-ntrig/linuxwacom-0.8.5-10/src'
Making distclean in .
make[1]: Entering directory `/home/tj/lw-ntrig/linuxwacom-0.8.5-10'
rm -rf .libs _libs
rm -f *.lo
test -z "mkxincludes src/2.6.9/Makefile src/2.6.10/Makefile src/2.6.11/Makefile src/2.6.13/Makefile src/2.6.14/Makefile src/2.6.15/Makefile src/2.6.16/Makefile src/2.6.18/Makefile src/2.6.19/Makefile src/2.6.22/Makefile src/2.6.24/Makefile src/2.6.26/Makefile src/2.6.27/Makefile" || rm -f mkxincludes src/2.6.9/Makefile src/2.6.10/Makefile src/2.6.11/Makefile src/2.6.13/Makefile src/2.6.14/Makefile src/2.6.15/Makefile src/2.6.16/Makefile src/2.6.18/Makefile src/2.6.19/Makefile src/2.6.22/Makefile src/2.6.24/Makefile src/2.6.26/Makefile src/2.6.27/Makefile
rm -f src/include/xdrv-config.h src/include/stamp-h1 src/include/kernel-config.h src/include/stamp-h2 src/include/util-config.h src/include/stamp-h3
rm -f libtool
rm -f TAGS ID GTAGS GRTAGS GSYMS GPATH tags
make[1]: Leaving directory `/home/tj/lw-ntrig/linuxwacom-0.8.5-10'
rm -f config.status config.cache config.log configure.lineno config.status.lineno
rm -f Makefile
tj@xt2:~/lw-ntrig/linuxwacom-0.8.5-10$ ./configure --enable-wacom --prefix=/usr
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for a thread-safe mkdir -p... /bin/mkdir -p
checking for gawk... gawk
checking whether make sets $(MAKE)... yes
checking whether to enable maintainer-specific portions of Makefiles... no
checking for gcc... gcc
checking for C compiler default output file name... a.out
checking whether the C compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables... 
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ISO C89... none needed
checking for style of include used by make... GNU
checking dependency style of gcc... gcc3
checking for gawk... (cached) gawk
checking build system type... x86_64-unknown-linux-gnu
checking host system type... x86_64-unknown-linux-gnu
checking for a sed that does not truncate output... /bin/sed
checking for grep that handles long lines and -e... /bin/grep
checking for egrep... /bin/grep -E
checking for ld used by gcc... /usr/bin/ld
checking if the linker (/usr/bin/ld) is GNU ld... yes
checking for /usr/bin/ld option to reload object files... -r
checking for BSD-compatible nm... /usr/bin/nm -B
checking whether ln -s works... yes
checking how to recognize dependent libraries... pass_all
checking how to run the C preprocessor... gcc -E
checking for ANSI C header files... yes
checking for sys/types.h... yes
checking for sys/stat.h... yes
checking for stdlib.h... yes
checking for string.h... yes
checking for memory.h... yes
checking for strings.h... yes
checking for inttypes.h... yes
checking for stdint.h... yes
checking for unistd.h... yes
checking dlfcn.h usability... yes
checking dlfcn.h presence... yes
checking for dlfcn.h... yes
checking for g++... g++
checking whether we are using the GNU C++ compiler... yes
checking whether g++ accepts -g... yes
checking dependency style of g++... gcc3
checking how to run the C++ preprocessor... g++ -E
checking for g77... no
checking for xlf... no
checking for f77... no
checking for frt... no
checking for pgf77... no
checking for cf77... no
checking for fort77... no
checking for fl32... no
checking for af77... no
checking for xlf90... no
checking for f90... no
checking for pgf90... no
checking for pghpf... no
checking for epcf90... no
checking for gfortran... no
checking for g95... no
checking for xlf95... no
checking for f95... no
checking for fort... no
checking for ifort... no
checking for ifc... no
checking for efc... no
checking for pgf95... no
checking for lf95... no
checking for ftn... no
checking whether we are using the GNU Fortran 77 compiler... no
checking whether  accepts -g... no
checking the maximum length of command line arguments... 1572864
checking command to parse /usr/bin/nm -B output from gcc object... ok
checking for objdir... .libs
checking for ar... ar
checking for ranlib... ranlib
checking for strip... strip
checking if gcc supports -fno-rtti -fno-exceptions... no
checking for gcc option to produce PIC... -fPIC
checking if gcc PIC flag -fPIC works... yes
checking if gcc static flag -static works... yes
checking if gcc supports -c -o file.o... yes
checking whether the gcc linker (/usr/bin/ld -m elf_x86_64) supports shared libraries... yes
checking whether -lc should be explicitly linked in... no
checking dynamic linker characteristics... GNU/Linux ld.so
checking how to hardcode library paths into programs... immediate
checking whether stripping libraries is possible... yes
checking if libtool supports shared libraries... yes
checking whether to build shared libraries... yes
checking whether to build static libraries... yes
configure: creating libtool
appending configuration tag "CXX" to libtool
checking for ld used by g++... /usr/bin/ld -m elf_x86_64
checking if the linker (/usr/bin/ld -m elf_x86_64) is GNU ld... yes
checking whether the g++ linker (/usr/bin/ld -m elf_x86_64) supports shared libraries... yes
checking for g++ option to produce PIC... -fPIC
checking if g++ PIC flag -fPIC works... yes
checking if g++ static flag -static works... yes
checking if g++ supports -c -o file.o... yes
checking whether the g++ linker (/usr/bin/ld -m elf_x86_64) supports shared libraries... yes
checking dynamic linker characteristics... GNU/Linux ld.so
(cached) (cached) checking how to hardcode library paths into programs... immediate
appending configuration tag "F77" to libtool
checking for pkg-config... /usr/bin/pkg-config
checking pkg-config is at least version 0.9.0... yes
checking for HAL... yes
checking for arch type... x86_64-linux-gnu
checking for kernel type... Linux
checking for linux-based kernel... yes
checking for kernel source/headers... /lib/modules/2.6.31-20-generic/build
checking kernel version... 2.6.31-20-generic
checking for kernel module support... yes
checking for Xlib... yes
checking for XSERVER... yes
checking for xserver libc-wrapper header-files... no
checking if scaling tablet to screen size is needed... no
checking if Xorg server is version 1.4 or later... yes
checking if Xorg is 7.3 or earlier... no
checking if Xorg server is version 1.5.2 or later... yes
checking if Xorg server is version 1.6 or later... yes
checking if Xorg SDK defined IsXExtensionPointer... yes
checking if Xorg SDK defines dixScreenOrigins... yes
checking XInput extension version... >= 2.0
checking for lib xf86config... checking for X... libraries , headers 
checking for gethostbyname... yes
checking for connect... yes
checking for remove... yes
checking for shmat... yes
checking for IceConnectionNumber in -lICE... yes
checking for tclsh... /usr/bin/tclsh
checking for tcl version... 8.4
checking for tcl header files... found, /usr/include/tcl
checking for tk header files... found, /usr/include/tcl
checking ncurses.h usability... yes
checking ncurses.h presence... yes
checking for ncurses.h... yes
checking if libwacomcfg should/can be built... yes
checking if libwacomxi should/can be built... yes
checking if wacdump should/can be built... yes
checking if xidump should/can be built... yes
checking if xsetwacom should be built... yes
checking for Wacom X driver module path... /usr/lib/xorg/modules/input
checking for dynamic driver loading support... yes
checking if wacom_drv.{o,so} should be compiled... yes
checking if gcc accepts -fno-merge-constants... yes
checking if gcc accepts -fno-stack-protector... yes

configure: creating ./config.status
config.status: creating Makefile
config.status: creating mkxincludes
config.status: creating src/Makefile
config.status: creating src/util/Makefile
config.status: creating src/xdrv/Makefile
config.status: creating src/2.6.9/Makefile
config.status: creating src/2.6.10/Makefile
config.status: creating src/2.6.11/Makefile
config.status: creating src/2.6.13/Makefile
config.status: creating src/2.6.14/Makefile
config.status: creating src/2.6.15/Makefile
config.status: creating src/2.6.16/Makefile
config.status: creating src/2.6.18/Makefile
config.status: creating src/2.6.19/Makefile
config.status: creating src/2.6.22/Makefile
config.status: creating src/2.6.24/Makefile
config.status: creating src/2.6.26/Makefile
config.status: creating src/2.6.27/Makefile
config.status: creating src/wacomxi/Makefile
config.status: creating src/wacomxi/wacomcpl
config.status: creating src/include/xdrv-config.h
config.status: creating src/include/kernel-config.h
config.status: creating src/include/util-config.h
config.status: executing depfiles commands

----------------------------------------
  BUILD ENVIRONMENT:
       architecture - x86_64-linux-gnu
       linux kernel - yes 2.6.27
  module versioning - no 
      kernel source - yes /lib/modules/2.6.31-20-generic/build
     XFree86 source - no 
           Xorg SDK - yes /usr/include/xorg
          XSERVER64 - yes
           dlloader - yes
               XLib - yes /usr/lib
         xf86config - no
                TCL - yes /usr/include/tcl
                 TK - yes /usr/include/tcl
            ncurses - yes

  BUILD OPTIONS:
            wacom.o - yes
            wacdump - yes 
             xidump - yes 
        libwacomcfg - yes
         libwacomxi - yes
          xsetwacom - yes
              hid.o - no 
       wacom_drv.so - yes /usr/lib/xorg/modules/input 
        wacom_drv.o - no
  wacom*_drv quirks - hal IsXExtensionPointer key-events dixScreenOrigins
----------------------------------------
tj@xt2:~/lw-ntrig/linuxwacom-0.8.5-10$ make
Making all in src
make[1]: Entering directory `/home/tj/lw-ntrig/linuxwacom-0.8.5-10/src'
Making all in .
make[2]: Entering directory `/home/tj/lw-ntrig/linuxwacom-0.8.5-10/src'
make[2]: Nothing to be done for `all-am'.
make[2]: Leaving directory `/home/tj/lw-ntrig/linuxwacom-0.8.5-10/src'
Making all in wacomxi
make[2]: Entering directory `/home/tj/lw-ntrig/linuxwacom-0.8.5-10/src/wacomxi'
/bin/bash ../../libtool --tag=CC   --mode=compile gcc -DHAVE_CONFIG_H -I. -I../../src/include    -Wall -g -O2 -D__amd64__ -I/usr/include/tcl -MT wacomxi.lo -MD -MP -MF .deps/wacomxi.Tpo -c -o wacomxi.lo wacomxi.c
mkdir .libs
 gcc -DHAVE_CONFIG_H -I. -I../../src/include -Wall -g -O2 -D__amd64__ -I/usr/include/tcl -MT wacomxi.lo -MD -MP -MF .deps/wacomxi.Tpo -c wacomxi.c  -fPIC -DPIC -o .libs/wacomxi.o
 gcc -DHAVE_CONFIG_H -I. -I../../src/include -Wall -g -O2 -D__amd64__ -I/usr/include/tcl -MT wacomxi.lo -MD -MP -MF .deps/wacomxi.Tpo -c wacomxi.c -o wacomxi.o >/dev/null 2>&1
mv -f .deps/wacomxi.Tpo .deps/wacomxi.Plo
/bin/bash ../../libtool --tag=CC   --mode=link gcc -Wall -g -O2 -D__amd64__ -I/usr/include/tcl -no-undefined  -o libwacomxi.la -rpath /usr/lib/TkXInput wacomxi.lo -L/usr/lib -lX11 -lXi 
gcc -shared  .libs/wacomxi.o  -L/usr/lib -lX11 -lXi  -Wl,-soname -Wl,libwacomxi.so.0 -o .libs/libwacomxi.so.0.0.0
(cd .libs && rm -f libwacomxi.so.0 && ln -s libwacomxi.so.0.0.0 libwacomxi.so.0)
(cd .libs && rm -f libwacomxi.so && ln -s libwacomxi.so.0.0.0 libwacomxi.so)
ar cru .libs/libwacomxi.a  wacomxi.o
ranlib .libs/libwacomxi.a
creating libwacomxi.la
(cd .libs && rm -f libwacomxi.la && ln -s ../libwacomxi.la libwacomxi.la)
make[2]: Leaving directory `/home/tj/lw-ntrig/linuxwacom-0.8.5-10/src/wacomxi'
Making all in util
make[2]: Entering directory `/home/tj/lw-ntrig/linuxwacom-0.8.5-10/src/util'
/bin/bash ../../libtool --tag=CC   --mode=compile gcc -DHAVE_CONFIG_H -I. -I../../src/include    -Wall -pedantic -I/usr/include/xorg  -DDBUS_API_SUBJECT_TO_CHANGE -I/usr/include/hal -I/usr/include/dbus-1.0 -I/usr/lib/dbus-1.0/include   -g -O2 -D__amd64__ -I/usr/include/tcl -MT wacomcfg.lo -MD -MP -MF .deps/wacomcfg.Tpo -c -o wacomcfg.lo wacomcfg.c
mkdir .libs
 gcc -DHAVE_CONFIG_H -I. -I../../src/include -Wall -pedantic -I/usr/include/xorg -DDBUS_API_SUBJECT_TO_CHANGE -I/usr/include/hal -I/usr/include/dbus-1.0 -I/usr/lib/dbus-1.0/include -g -O2 -D__amd64__ -I/usr/include/tcl -MT wacomcfg.lo -MD -MP -MF .deps/wacomcfg.Tpo -c wacomcfg.c  -fPIC -DPIC -o .libs/wacomcfg.o
 gcc -DHAVE_CONFIG_H -I. -I../../src/include -Wall -pedantic -I/usr/include/xorg -DDBUS_API_SUBJECT_TO_CHANGE -I/usr/include/hal -I/usr/include/dbus-1.0 -I/usr/lib/dbus-1.0/include -g -O2 -D__amd64__ -I/usr/include/tcl -MT wacomcfg.lo -MD -MP -MF .deps/wacomcfg.Tpo -c wacomcfg.c -o wacomcfg.o >/dev/null 2>&1
mv -f .deps/wacomcfg.Tpo .deps/wacomcfg.Plo
/bin/bash ../../libtool --tag=CC   --mode=link gcc -Wall -pedantic -I/usr/include/xorg  -DDBUS_API_SUBJECT_TO_CHANGE -I/usr/include/hal -I/usr/include/dbus-1.0 -I/usr/lib/dbus-1.0/include   -g -O2 -D__amd64__ -I/usr/include/tcl -no-undefined -version-info 0:1:0  -o libwacomcfg.la -rpath /usr/lib wacomcfg.lo -L/usr/lib -lX11 -lXi 
gcc -shared  .libs/wacomcfg.o  -L/usr/lib -lX11 -lXi  -Wl,-soname -Wl,libwacomcfg.so.0 -o .libs/libwacomcfg.so.0.0.1
(cd .libs && rm -f libwacomcfg.so.0 && ln -s libwacomcfg.so.0.0.1 libwacomcfg.so.0)
(cd .libs && rm -f libwacomcfg.so && ln -s libwacomcfg.so.0.0.1 libwacomcfg.so)
ar cru .libs/libwacomcfg.a  wacomcfg.o
ranlib .libs/libwacomcfg.a
creating libwacomcfg.la
(cd .libs && rm -f libwacomcfg.la && ln -s ../libwacomcfg.la libwacomcfg.la)
gcc -DHAVE_CONFIG_H -I. -I../../src/include    -Wall -pedantic -I/usr/include/xorg  -DDBUS_API_SUBJECT_TO_CHANGE -I/usr/include/hal -I/usr/include/dbus-1.0 -I/usr/lib/dbus-1.0/include   -g -O2 -D__amd64__ -I/usr/include/tcl -MT wacdump.o -MD -MP -MF .deps/wacdump.Tpo -c -o wacdump.o wacdump.c
mv -f .deps/wacdump.Tpo .deps/wacdump.Po
gcc -DHAVE_CONFIG_H -I. -I../../src/include    -Wall -pedantic -I/usr/include/xorg  -DDBUS_API_SUBJECT_TO_CHANGE -I/usr/include/hal -I/usr/include/dbus-1.0 -I/usr/lib/dbus-1.0/include   -g -O2 -D__amd64__ -I/usr/include/tcl -MT wacscrn.o -MD -MP -MF .deps/wacscrn.Tpo -c -o wacscrn.o wacscrn.c
mv -f .deps/wacscrn.Tpo .deps/wacscrn.Po
gcc -DHAVE_CONFIG_H -I. -I../../src/include    -Wall -pedantic -I/usr/include/xorg  -DDBUS_API_SUBJECT_TO_CHANGE -I/usr/include/hal -I/usr/include/dbus-1.0 -I/usr/lib/dbus-1.0/include   -g -O2 -D__amd64__ -I/usr/include/tcl -MT wactablet.o -MD -MP -MF .deps/wactablet.Tpo -c -o wactablet.o wactablet.c
mv -f .deps/wactablet.Tpo .deps/wactablet.Po
gcc -DHAVE_CONFIG_H -I. -I../../src/include    -Wall -pedantic -I/usr/include/xorg  -DDBUS_API_SUBJECT_TO_CHANGE -I/usr/include/hal -I/usr/include/dbus-1.0 -I/usr/lib/dbus-1.0/include   -g -O2 -D__amd64__ -I/usr/include/tcl -MT wacserial.o -MD -MP -MF .deps/wacserial.Tpo -c -o wacserial.o wacserial.c
wacserial.c: In function ‘WacomFlush’:
wacserial.c:1345: warning: ignoring return value of ‘read’, declared with attribute warn_unused_result
mv -f .deps/wacserial.Tpo .deps/wacserial.Po
gcc -DHAVE_CONFIG_H -I. -I../../src/include    -Wall -pedantic -I/usr/include/xorg  -DDBUS_API_SUBJECT_TO_CHANGE -I/usr/include/hal -I/usr/include/dbus-1.0 -I/usr/lib/dbus-1.0/include   -g -O2 -D__amd64__ -I/usr/include/tcl -MT wacusb.o -MD -MP -MF .deps/wacusb.Tpo -c -o wacusb.o wacusb.c
mv -f .deps/wacusb.Tpo .deps/wacusb.Po
/bin/bash ../../libtool --tag=CC   --mode=link gcc -Wall -pedantic -I/usr/include/xorg  -DDBUS_API_SUBJECT_TO_CHANGE -I/usr/include/hal -I/usr/include/dbus-1.0 -I/usr/lib/dbus-1.0/include   -g -O2 -D__amd64__ -I/usr/include/tcl   -o wacdump wacdump.o wacscrn.o wactablet.o wacserial.o wacusb.o -lncurses 
gcc -Wall -pedantic -I/usr/include/xorg -DDBUS_API_SUBJECT_TO_CHANGE -I/usr/include/hal -I/usr/include/dbus-1.0 -I/usr/lib/dbus-1.0/include -g -O2 -D__amd64__ -I/usr/include/tcl -o wacdump wacdump.o wacscrn.o wactablet.o wacserial.o wacusb.o  -lncurses  
gcc -DHAVE_CONFIG_H -I. -I../../src/include    -Wall -pedantic -I/usr/include/xorg  -DDBUS_API_SUBJECT_TO_CHANGE -I/usr/include/hal -I/usr/include/dbus-1.0 -I/usr/lib/dbus-1.0/include   -g -O2 -D__amd64__ -I/usr/include/tcl -MT xidump.o -MD -MP -MF .deps/xidump.Tpo -c -o xidump.o xidump.c
xidump.c: In function ‘RawRunAccel’:
xidump.c:770: warning: dereferencing pointer ‘pMove’ does break strict-aliasing rules
xidump.c:769: note: initialized from here
xidump.c:772: warning: dereferencing pointer ‘event.63’ does break strict-aliasing rules
xidump.c:772: note: initialized from here
xidump.c:774: warning: dereferencing pointer ‘event.63’ does break strict-aliasing rules
xidump.c:774: note: initialized from here
xidump.c: In function ‘RawRun’:
xidump.c:718: warning: dereferencing pointer ‘pAny.58’ does break strict-aliasing rules
xidump.c:718: note: initialized from here
xidump.c:717: warning: dereferencing pointer ‘pAny.58’ does break strict-aliasing rules
xidump.c:717: note: initialized from here
xidump.c:716: warning: dereferencing pointer ‘pAny.58’ does break strict-aliasing rules
xidump.c:716: note: initialized from here
xidump.c:711: warning: dereferencing pointer ‘pAny.58’ does break strict-aliasing rules
xidump.c:715: note: initialized from here
xidump.c:711: warning: dereferencing pointer ‘pAny.58’ does break strict-aliasing rules
xidump.c:714: note: initialized from here
xidump.c:711: warning: dereferencing pointer ‘pAny.58’ does break strict-aliasing rules
xidump.c:713: note: initialized from here
xidump.c:725: warning: dereferencing pointer ‘pBtn’ does break strict-aliasing rules
xidump.c:724: note: initialized from here
xidump.c:733: warning: dereferencing pointer ‘pKey’ does break strict-aliasing rules
xidump.c:732: note: initialized from here
xidump.c: In function ‘CursesRun’:
xidump.c:571: warning: dereferencing pointer ‘pAny.53’ does break strict-aliasing rules
xidump.c:572: note: initialized from here
xidump.c:580: warning: dereferencing pointer ‘pAny.53’ does break strict-aliasing rules
xidump.c:580: note: initialized from here
xidump.c:590: warning: dereferencing pointer ‘pAny.53’ does break strict-aliasing rules
xidump.c:590: note: initialized from here
xidump.c:625: warning: dereferencing pointer ‘pBtn’ does break strict-aliasing rules
xidump.c:623: warning: dereferencing pointer ‘pBtn’ does break strict-aliasing rules
xidump.c:620: note: initialized from here
xidump.c:642: warning: dereferencing pointer ‘pKey’ does break strict-aliasing rules
xidump.c:640: warning: dereferencing pointer ‘pKey’ does break strict-aliasing rules
xidump.c:638: note: initialized from here
mv -f .deps/xidump.Tpo .deps/xidump.Po
/bin/bash ../../libtool --tag=CC   --mode=link gcc -Wall -pedantic -I/usr/include/xorg  -DDBUS_API_SUBJECT_TO_CHANGE -I/usr/include/hal -I/usr/include/dbus-1.0 -I/usr/lib/dbus-1.0/include   -g -O2 -D__amd64__ -I/usr/include/tcl -L/usr/lib -lX11 -lXi -lm  -o xidump xidump.o wacscrn.o -lncurses 
gcc -Wall -pedantic -I/usr/include/xorg -DDBUS_API_SUBJECT_TO_CHANGE -I/usr/include/hal -I/usr/include/dbus-1.0 -I/usr/lib/dbus-1.0/include -g -O2 -D__amd64__ -I/usr/include/tcl -o xidump xidump.o wacscrn.o  -L/usr/lib -lX11 -lXi -lm -lncurses  
gcc -DHAVE_CONFIG_H -I. -I../../src/include    -Wall -pedantic -I/usr/include/xorg  -DDBUS_API_SUBJECT_TO_CHANGE -I/usr/include/hal -I/usr/include/dbus-1.0 -I/usr/lib/dbus-1.0/include   -g -O2 -D__amd64__ -I/usr/include/tcl -MT xsetwacom.o -MD -MP -MF .deps/xsetwacom.Tpo -c -o xsetwacom.o xsetwacom.c
mv -f .deps/xsetwacom.Tpo .deps/xsetwacom.Po
gcc -DHAVE_CONFIG_H -I. -I../../src/include    -Wall -pedantic -I/usr/include/xorg  -DDBUS_API_SUBJECT_TO_CHANGE -I/usr/include/hal -I/usr/include/dbus-1.0 -I/usr/lib/dbus-1.0/include   -g -O2 -D__amd64__ -I/usr/include/tcl -MT wcmAction.o -MD -MP -MF .deps/wcmAction.Tpo -c -o wcmAction.o wcmAction.c
mv -f .deps/wcmAction.Tpo .deps/wcmAction.Po
/bin/bash ../../libtool --tag=CC   --mode=link gcc -Wall -pedantic -I/usr/include/xorg  -DDBUS_API_SUBJECT_TO_CHANGE -I/usr/include/hal -I/usr/include/dbus-1.0 -I/usr/lib/dbus-1.0/include   -g -O2 -D__amd64__ -I/usr/include/tcl   -o xsetwacom xsetwacom.o wcmAction.o libwacomcfg.la 
gcc -Wall -pedantic -I/usr/include/xorg -DDBUS_API_SUBJECT_TO_CHANGE -I/usr/include/hal -I/usr/include/dbus-1.0 -I/usr/lib/dbus-1.0/include -g -O2 -D__amd64__ -I/usr/include/tcl -o .libs/xsetwacom xsetwacom.o wcmAction.o  ./.libs/libwacomcfg.so -L/usr/lib -lX11 -lXi 
creating xsetwacom
gcc -DHAVE_CONFIG_H -I. -I../../src/include    -Wall -pedantic -I/usr/include/xorg  -DDBUS_API_SUBJECT_TO_CHANGE -I/usr/include/hal -I/usr/include/dbus-1.0 -I/usr/lib/dbus-1.0/include   -g -O2 -D__amd64__ -I/usr/include/tcl -MT hal-setup-wacom.o -MD -MP -MF .deps/hal-setup-wacom.Tpo -c -o hal-setup-wacom.o hal-setup-wacom.c
hal-setup-wacom.c: In function ‘main’:
hal-setup-wacom.c:54: warning: ignoring return value of ‘asprintf’, declared with attribute warn_unused_result
hal-setup-wacom.c:137: warning: ignoring return value of ‘asprintf’, declared with attribute warn_unused_result
mv -f .deps/hal-setup-wacom.Tpo .deps/hal-setup-wacom.Po
/bin/bash ../../libtool --tag=CC   --mode=link gcc -Wall -pedantic -I/usr/include/xorg  -DDBUS_API_SUBJECT_TO_CHANGE -I/usr/include/hal -I/usr/include/dbus-1.0 -I/usr/lib/dbus-1.0/include   -g -O2 -D__amd64__ -I/usr/include/tcl   -o hal-setup-wacom hal-setup-wacom.o -L/lib -lhal -ldbus-1 -lpthread -lrt   
gcc -Wall -pedantic -I/usr/include/xorg -DDBUS_API_SUBJECT_TO_CHANGE -I/usr/include/hal -I/usr/include/dbus-1.0 -I/usr/lib/dbus-1.0/include -g -O2 -D__amd64__ -I/usr/include/tcl -o hal-setup-wacom hal-setup-wacom.o  -L/lib -lhal -ldbus-1 -lpthread -lrt  
make[2]: Leaving directory `/home/tj/lw-ntrig/linuxwacom-0.8.5-10/src/util'
Making all in xdrv
make[2]: Entering directory `/home/tj/lw-ntrig/linuxwacom-0.8.5-10/src/xdrv'
gcc -MM -g -O2 -D__amd64__ -I/usr/include/tcl  -I../include -I/usr/include/xorg   ./xf86Wacom.c ./wcmSerial.c ./wcmUSB.c ./wcmISDV4.c ./wcmXCommand.c ./wcmCommon.c ./wcmCompat.c ./wcmConfig.c ./wcmFilter.c ./wcmTilt2Rotation.c ./wcmTouchFilter.c ./wcmValidateDevice.c ./wcmMapping.c > .depend
make[2]: Leaving directory `/home/tj/lw-ntrig/linuxwacom-0.8.5-10/src/xdrv'
make[2]: Entering directory `/home/tj/lw-ntrig/linuxwacom-0.8.5-10/src/xdrv'
gcc -g -O2 -D__amd64__ -I/usr/include/tcl  -fPIC -pipe -std=c99 \
		-pedantic -Wall -Wpointer-arith -fno-merge-constants \
		-fno-stack-protector -I. -I../include -I/usr/include/xorg   \
		-D_XSERVER64 -I/usr/include/xorg -I/usr/include/pixman-1   \
		-o xf86Wacom.o -c ./xf86Wacom.c
In file included from ./xf86Wacom.h:27,
                 from ./xf86Wacom.c:102:
/usr/include/xorg/xorg-server.h:105:1: warning: "XKB" redefined
In file included from ./xf86Wacom.h:25,
                 from ./xf86Wacom.c:102:
./../include/xdrv-config.h:18:1: warning: this is the location of the previous definition
In file included from ./xf86Wacom.h:27,
                 from ./xf86Wacom.c:102:
/usr/include/xorg/xorg-server.h:195:1: warning: "XFree86LOADER" redefined
In file included from ./xf86Wacom.h:25,
                 from ./xf86Wacom.c:102:
./../include/xdrv-config.h:12:1: warning: this is the location of the previous definition
gcc -g -O2 -D__amd64__ -I/usr/include/tcl  -fPIC -pipe -std=c99 \
		-pedantic -Wall -Wpointer-arith -fno-merge-constants \
		-fno-stack-protector -I. -I../include -I/usr/include/xorg   \
		-D_XSERVER64 -I/usr/include/xorg -I/usr/include/pixman-1   \
		-o wcmSerial.o -c ./wcmSerial.c
In file included from ./xf86Wacom.h:27,
                 from ./wcmSerial.c:20:
/usr/include/xorg/xorg-server.h:105:1: warning: "XKB" redefined
In file included from ./xf86Wacom.h:25,
                 from ./wcmSerial.c:20:
./../include/xdrv-config.h:18:1: warning: this is the location of the previous definition
In file included from ./xf86Wacom.h:27,
                 from ./wcmSerial.c:20:
/usr/include/xorg/xorg-server.h:195:1: warning: "XFree86LOADER" redefined
In file included from ./xf86Wacom.h:25,
                 from ./wcmSerial.c:20:
./../include/xdrv-config.h:12:1: warning: this is the location of the previous definition
gcc -g -O2 -D__amd64__ -I/usr/include/tcl  -fPIC -pipe -std=c99 \
		-pedantic -Wall -Wpointer-arith -fno-merge-constants \
		-fno-stack-protector -I. -I../include -I/usr/include/xorg   \
		-D_XSERVER64 -I/usr/include/xorg -I/usr/include/pixman-1   \
		-o wcmUSB.o -c ./wcmUSB.c
In file included from ./xf86Wacom.h:27,
                 from ./wcmUSB.c:20:
/usr/include/xorg/xorg-server.h:105:1: warning: "XKB" redefined
In file included from ./xf86Wacom.h:25,
                 from ./wcmUSB.c:20:
./../include/xdrv-config.h:18:1: warning: this is the location of the previous definition
In file included from ./xf86Wacom.h:27,
                 from ./wcmUSB.c:20:
/usr/include/xorg/xorg-server.h:195:1: warning: "XFree86LOADER" redefined
In file included from ./xf86Wacom.h:25,
                 from ./wcmUSB.c:20:
./../include/xdrv-config.h:12:1: warning: this is the location of the previous definition
./wcmUSB.c:496: error: expected ‘}’ before ‘{’ token
make[2]: *** [wcmUSB.o] Error 1
make[2]: Leaving directory `/home/tj/lw-ntrig/linuxwacom-0.8.5-10/src/xdrv'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/tj/lw-ntrig/linuxwacom-0.8.5-10/src'
make: *** [all-recursive] Error 1
tj@xt2:~/lw-ntrig/linuxwacom-0.8.5-10$ sudo make install
[sudo] password for tj: 
Making install in src
make[1]: Entering directory `/home/tj/lw-ntrig/linuxwacom-0.8.5-10/src'
Making install in .
make[2]: Entering directory `/home/tj/lw-ntrig/linuxwacom-0.8.5-10/src'
make[3]: Entering directory `/home/tj/lw-ntrig/linuxwacom-0.8.5-10/src'
make[3]: Nothing to be done for `install-exec-am'.
test -z "/usr/share/man/man4" || /bin/mkdir -p "/usr/share/man/man4"
 /usr/bin/install -c -m 644 'wacom.4x.gz' '/usr/share/man/man4/wacom.4x.gz'
make[3]: Leaving directory `/home/tj/lw-ntrig/linuxwacom-0.8.5-10/src'
make[2]: Leaving directory `/home/tj/lw-ntrig/linuxwacom-0.8.5-10/src'
Making install in wacomxi
make[2]: Entering directory `/home/tj/lw-ntrig/linuxwacom-0.8.5-10/src/wacomxi'
make[3]: Entering directory `/home/tj/lw-ntrig/linuxwacom-0.8.5-10/src/wacomxi'
make[3]: Nothing to be done for `install-exec-am'.
test -z "/usr/bin" || /bin/mkdir -p "/usr/bin"
 /usr/bin/install -c 'wacomcpl' '/usr/bin/wacomcpl'
 /usr/bin/install -c 'wacomcpl-exec' '/usr/bin/wacomcpl-exec'
test -z "/usr/lib/TkXInput" || /bin/mkdir -p "/usr/lib/TkXInput"
 /usr/bin/install -c -m 644 'pkgIndex.tcl' '/usr/lib/TkXInput/pkgIndex.tcl'
test -z "/usr/lib/TkXInput" || /bin/mkdir -p "/usr/lib/TkXInput"
 /bin/bash ../../libtool   --mode=install /usr/bin/install -c  'libwacomxi.la' '/usr/lib/TkXInput/libwacomxi.la'
/usr/bin/install -c .libs/libwacomxi.so.0.0.0 /usr/lib/TkXInput/libwacomxi.so.0.0.0
(cd /usr/lib/TkXInput && { ln -s -f libwacomxi.so.0.0.0 libwacomxi.so.0 || { rm -f libwacomxi.so.0 && ln -s libwacomxi.so.0.0.0 libwacomxi.so.0; }; })
(cd /usr/lib/TkXInput && { ln -s -f libwacomxi.so.0.0.0 libwacomxi.so || { rm -f libwacomxi.so && ln -s libwacomxi.so.0.0.0 libwacomxi.so; }; })
/usr/bin/install -c .libs/libwacomxi.lai /usr/lib/TkXInput/libwacomxi.la
/usr/bin/install -c .libs/libwacomxi.a /usr/lib/TkXInput/libwacomxi.a
chmod 644 /usr/lib/TkXInput/libwacomxi.a
ranlib /usr/lib/TkXInput/libwacomxi.a
PATH="$PATH:/sbin" ldconfig -n /usr/lib/TkXInput
----------------------------------------------------------------------
Libraries have been installed in:
   /usr/lib/TkXInput

If you ever happen to want to link against installed libraries
in a given directory, LIBDIR, you must either use libtool, and
specify the full pathname of the library, or use the `-LLIBDIR'
flag during linking and do at least one of the following:
   - add LIBDIR to the `LD_LIBRARY_PATH' environment variable
     during execution
   - add LIBDIR to the `LD_RUN_PATH' environment variable
     during linking
   - use the `-Wl,--rpath -Wl,LIBDIR' linker flag
   - have your system administrator add LIBDIR to `/etc/ld.so.conf'

See any operating system documentation about shared libraries for
more information, such as the ld(1) and ld.so(8) manual pages.
----------------------------------------------------------------------
make[3]: Leaving directory `/home/tj/lw-ntrig/linuxwacom-0.8.5-10/src/wacomxi'
make[2]: Leaving directory `/home/tj/lw-ntrig/linuxwacom-0.8.5-10/src/wacomxi'
Making install in util
make[2]: Entering directory `/home/tj/lw-ntrig/linuxwacom-0.8.5-10/src/util'
make[3]: Entering directory `/home/tj/lw-ntrig/linuxwacom-0.8.5-10/src/util'
test -z "/usr/lib" || /bin/mkdir -p "/usr/lib"
 /bin/bash ../../libtool   --mode=install /usr/bin/install -c  'libwacomcfg.la' '/usr/lib/libwacomcfg.la'
/usr/bin/install -c .libs/libwacomcfg.so.0.0.1 /usr/lib/libwacomcfg.so.0.0.1
(cd /usr/lib && { ln -s -f libwacomcfg.so.0.0.1 libwacomcfg.so.0 || { rm -f libwacomcfg.so.0 && ln -s libwacomcfg.so.0.0.1 libwacomcfg.so.0; }; })
(cd /usr/lib && { ln -s -f libwacomcfg.so.0.0.1 libwacomcfg.so || { rm -f libwacomcfg.so && ln -s libwacomcfg.so.0.0.1 libwacomcfg.so; }; })
/usr/bin/install -c .libs/libwacomcfg.lai /usr/lib/libwacomcfg.la
/usr/bin/install -c .libs/libwacomcfg.a /usr/lib/libwacomcfg.a
chmod 644 /usr/lib/libwacomcfg.a
ranlib /usr/lib/libwacomcfg.a
PATH="$PATH:/sbin" ldconfig -n /usr/lib
----------------------------------------------------------------------
Libraries have been installed in:
   /usr/lib

If you ever happen to want to link against installed libraries
in a given directory, LIBDIR, you must either use libtool, and
specify the full pathname of the library, or use the `-LLIBDIR'
flag during linking and do at least one of the following:
   - add LIBDIR to the `LD_LIBRARY_PATH' environment variable
     during execution
   - add LIBDIR to the `LD_RUN_PATH' environment variable
     during linking
   - use the `-Wl,--rpath -Wl,LIBDIR' linker flag
   - have your system administrator add LIBDIR to `/etc/ld.so.conf'

See any operating system documentation about shared libraries for
more information, such as the ld(1) and ld.so(8) manual pages.
----------------------------------------------------------------------
test -z "/usr/bin" || /bin/mkdir -p "/usr/bin"
  /bin/bash ../../libtool   --mode=install /usr/bin/install -c 'wacdump' '/usr/bin/wacdump'
/usr/bin/install -c wacdump /usr/bin/wacdump
  /bin/bash ../../libtool   --mode=install /usr/bin/install -c 'xidump' '/usr/bin/xidump'
/usr/bin/install -c xidump /usr/bin/xidump
  /bin/bash ../../libtool   --mode=install /usr/bin/install -c 'xsetwacom' '/usr/bin/xsetwacom'
/usr/bin/install -c .libs/xsetwacom /usr/bin/xsetwacom
test -z "/usr/libexec" || /bin/mkdir -p "/usr/libexec"
  /bin/bash ../../libtool   --mode=install /usr/bin/install -c 'hal-setup-wacom' '/usr/libexec/hal-setup-wacom'
/usr/bin/install -c hal-setup-wacom /usr/libexec/hal-setup-wacom
test -z "/usr/share/hal/fdi/policy/20thirdparty" || /bin/mkdir -p "/usr/share/hal/fdi/policy/20thirdparty"
 /usr/bin/install -c '10-linuxwacom.fdi' '/usr/share/hal/fdi/policy/20thirdparty/10-linuxwacom.fdi'
test -z "/usr/include/wacomcfg" || /bin/mkdir -p "/usr/include/wacomcfg"
 /usr/bin/install -c -m 644 'wacomcfg.h' '/usr/include/wacomcfg/wacomcfg.h'
make[3]: Leaving directory `/home/tj/lw-ntrig/linuxwacom-0.8.5-10/src/util'
make[2]: Leaving directory `/home/tj/lw-ntrig/linuxwacom-0.8.5-10/src/util'
Making install in xdrv
make[2]: Entering directory `/home/tj/lw-ntrig/linuxwacom-0.8.5-10/src/xdrv'
gcc -g -O2 -D__amd64__ -I/usr/include/tcl  -fPIC -pipe -std=c99 \
		-pedantic -Wall -Wpointer-arith -fno-merge-constants \
		-fno-stack-protector -I. -I../include -I/usr/include/xorg   \
		-D_XSERVER64 -I/usr/include/xorg -I/usr/include/pixman-1   \
		-o wcmUSB.o -c ./wcmUSB.c
In file included from ./xf86Wacom.h:27,
                 from ./wcmUSB.c:20:
/usr/include/xorg/xorg-server.h:105:1: warning: "XKB" redefined
In file included from ./xf86Wacom.h:25,
                 from ./wcmUSB.c:20:
./../include/xdrv-config.h:18:1: warning: this is the location of the previous definition
In file included from ./xf86Wacom.h:27,
                 from ./wcmUSB.c:20:
/usr/include/xorg/xorg-server.h:195:1: warning: "XFree86LOADER" redefined
In file included from ./xf86Wacom.h:25,
                 from ./wcmUSB.c:20:
./../include/xdrv-config.h:12:1: warning: this is the location of the previous definition
./wcmUSB.c:496: error: expected ‘}’ before ‘{’ token
make[2]: *** [wcmUSB.o] Error 1
make[2]: Leaving directory `/home/tj/lw-ntrig/linuxwacom-0.8.5-10/src/xdrv'
make[1]: *** [install-recursive] Error 1
make[1]: Leaving directory `/home/tj/lw-ntrig/linuxwacom-0.8.5-10/src'
make: *** [install-recursive] Error 1
tj@xt2:~/lw-ntrig/linuxwacom-0.8.5-10$ 


```

---

### Post by Ayuthia on 2010-02-21
Sorry about that.  I forgot a comma.  I have fixed the source so please try the following:
```

cd
cd lw-ntrig
rm -r linuxwacom-0.8.5-10
rm linuxwacom-0.8.5-10.tar.bz2
wget http://linuxfans.keryxproject.org/packages/wacom/ntrig/source/linuxwacom-0.8.5-10.tar.bz2
tar -xvjf linuxwacom-0.8.5-10.tar.bz2
cd linuxwacom-0.8.5-10
./configure --enable-wacom --prefix=/usr
make
sudo make install

```
These commands will remove your previous build, download the updated version, and rebuild it.

---

### Post by -TJ on 2010-02-21
I think it worked! Here is what happened:
```
tj@xt2:~$ cd
tj@xt2:~$ cd lw-ntrig
tj@xt2:~/lw-ntrig$ rm -r linuxwacom-0.8.5-10
tj@xt2:~/lw-ntrig$ rm linuxwacom-0.8.5-10.tar.bz2
tj@xt2:~/lw-ntrig$ wget http://linuxfans.keryxproject.org/packages/wacom/ntrig/source/linuxwacom-0.8.5-10.tar.bz2
--2010-02-21 18:46:24--  http://linuxfans.keryxproject.org/packages/wacom/ntrig/source/linuxwacom-0.8.5-10.tar.bz2
Resolving linuxfans.keryxproject.org... 69.163.163.159
Connecting to linuxfans.keryxproject.org|69.163.163.159|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 1135880 (1.1M) [application/x-bzip2]
Saving to: `linuxwacom-0.8.5-10.tar.bz2'

100%[===================================================================================================================>] 1,135,880    147K/s   in 12s     

2010-02-21 18:46:36 (93.1 KB/s) - `linuxwacom-0.8.5-10.tar.bz2' saved [1135880/1135880]

tj@xt2:~/lw-ntrig$ tar -xvjf linuxwacom-0.8.5-10.tar.bz2
linuxwacom-0.8.5-10/
linuxwacom-0.8.5-10/README
linuxwacom-0.8.5-10/autom4te.cache/
linuxwacom-0.8.5-10/autom4te.cache/output.0
linuxwacom-0.8.5-10/autom4te.cache/requests
linuxwacom-0.8.5-10/autom4te.cache/output.1
linuxwacom-0.8.5-10/autom4te.cache/traces.1
linuxwacom-0.8.5-10/autom4te.cache/traces.0
linuxwacom-0.8.5-10/config.guess
linuxwacom-0.8.5-10/GPL
linuxwacom-0.8.5-10/Makefile.in
linuxwacom-0.8.5-10/ltmain.sh
linuxwacom-0.8.5-10/Makefile.am
linuxwacom-0.8.5-10/mkxincludes.in
linuxwacom-0.8.5-10/prebuilt/
linuxwacom-0.8.5-10/prebuilt/32/
linuxwacom-0.8.5-10/prebuilt/32/libwacomxi.la
linuxwacom-0.8.5-10/prebuilt/32/wacom_drv.o
linuxwacom-0.8.5-10/prebuilt/32/pkgIndex.tcl
linuxwacom-0.8.5-10/prebuilt/32/xidump
linuxwacom-0.8.5-10/prebuilt/32/wacdump
linuxwacom-0.8.5-10/prebuilt/32/libwacomcfg.la
linuxwacom-0.8.5-10/prebuilt/32/wacomcfg.h
linuxwacom-0.8.5-10/prebuilt/32/wacom_drv.so
linuxwacom-0.8.5-10/prebuilt/32/.libs/
linuxwacom-0.8.5-10/prebuilt/32/.libs/libwacomxi.lai
linuxwacom-0.8.5-10/prebuilt/32/.libs/libwacomcfg.lai
linuxwacom-0.8.5-10/prebuilt/32/.libs/libwacomxi.so.0.0.0
linuxwacom-0.8.5-10/prebuilt/32/.libs/libwacomxi.a
linuxwacom-0.8.5-10/prebuilt/32/.libs/libwacomcfg.so.0.0.1
linuxwacom-0.8.5-10/prebuilt/32/.libs/xsetwacom
linuxwacom-0.8.5-10/prebuilt/32/.libs/libwacomcfg.a
linuxwacom-0.8.5-10/prebuilt/32/xsetwacom
linuxwacom-0.8.5-10/prebuilt/32/wacomcpl
linuxwacom-0.8.5-10/prebuilt/32/wacomcpl-exec
linuxwacom-0.8.5-10/prebuilt/wacom.4x.gz
linuxwacom-0.8.5-10/prebuilt/64/
linuxwacom-0.8.5-10/prebuilt/64/libwacomxi.la
linuxwacom-0.8.5-10/prebuilt/64/wacom_drv.o
linuxwacom-0.8.5-10/prebuilt/64/pkgIndex.tcl
linuxwacom-0.8.5-10/prebuilt/64/xidump
linuxwacom-0.8.5-10/prebuilt/64/wacdump
linuxwacom-0.8.5-10/prebuilt/64/libwacomcfg.la
linuxwacom-0.8.5-10/prebuilt/64/wacomcfg.h
linuxwacom-0.8.5-10/prebuilt/64/wacom_drv.so
linuxwacom-0.8.5-10/prebuilt/64/.libs/
linuxwacom-0.8.5-10/prebuilt/64/.libs/libwacomxi.lai
linuxwacom-0.8.5-10/prebuilt/64/.libs/libwacomcfg.lai
linuxwacom-0.8.5-10/prebuilt/64/.libs/libwacomxi.so.0.0.0
linuxwacom-0.8.5-10/prebuilt/64/.libs/libwacomxi.a
linuxwacom-0.8.5-10/prebuilt/64/.libs/libwacomcfg.so.0.0.1
linuxwacom-0.8.5-10/prebuilt/64/.libs/xsetwacom
linuxwacom-0.8.5-10/prebuilt/64/.libs/libwacomcfg.a
linuxwacom-0.8.5-10/prebuilt/64/xsetwacom
linuxwacom-0.8.5-10/prebuilt/64/wacomcpl
linuxwacom-0.8.5-10/prebuilt/64/wacomcpl-exec
linuxwacom-0.8.5-10/prebuilt/uninstall
linuxwacom-0.8.5-10/prebuilt/install
linuxwacom-0.8.5-10/bootstrap
linuxwacom-0.8.5-10/config.sub
linuxwacom-0.8.5-10/configure.in
linuxwacom-0.8.5-10/ChangeLog
linuxwacom-0.8.5-10/configure
linuxwacom-0.8.5-10/AUTHORS
linuxwacom-0.8.5-10/docs/
linuxwacom-0.8.5-10/docs/docs_files/
linuxwacom-0.8.5-10/docs/docs_files/sflogo.png
linuxwacom-0.8.5-10/docs/docs_files/null.gif
linuxwacom-0.8.5-10/docs/docs.html
linuxwacom-0.8.5-10/missing
linuxwacom-0.8.5-10/aclocal.m4
linuxwacom-0.8.5-10/depcomp
linuxwacom-0.8.5-10/src/
linuxwacom-0.8.5-10/src/2.6.10/
linuxwacom-0.8.5-10/src/2.6.10/Makefile.in
linuxwacom-0.8.5-10/src/2.6.10/wacom.c
linuxwacom-0.8.5-10/src/2.6.10/hid-core.c
linuxwacom-0.8.5-10/src/2.6.27/
linuxwacom-0.8.5-10/src/2.6.27/Makefile.in
linuxwacom-0.8.5-10/src/2.6.27/wacom.h
linuxwacom-0.8.5-10/src/2.6.27/wacom_sys.c
linuxwacom-0.8.5-10/src/2.6.27/wacom_wac.h
linuxwacom-0.8.5-10/src/2.6.27/wacom_wac.c
linuxwacom-0.8.5-10/src/Makefile.in
linuxwacom-0.8.5-10/src/wacomxi/
linuxwacom-0.8.5-10/src/wacomxi/wacomxi.c
linuxwacom-0.8.5-10/src/wacomxi/Makefile.in
linuxwacom-0.8.5-10/src/wacomxi/Makefile.am
linuxwacom-0.8.5-10/src/wacomxi/pkgIndex.tcl
linuxwacom-0.8.5-10/src/wacomxi/wacomxi.h
linuxwacom-0.8.5-10/src/wacomxi/wacomcpl.in
linuxwacom-0.8.5-10/src/wacomxi/wacomcpl-exec
linuxwacom-0.8.5-10/src/wacom.4x
linuxwacom-0.8.5-10/src/2.6.19/
linuxwacom-0.8.5-10/src/2.6.19/Makefile.in
linuxwacom-0.8.5-10/src/2.6.19/wacom.h
linuxwacom-0.8.5-10/src/2.6.19/wacom_sys.c
linuxwacom-0.8.5-10/src/2.6.19/wacom_wac.c
linuxwacom-0.8.5-10/src/Makefile.am
linuxwacom-0.8.5-10/src/xdrv/
linuxwacom-0.8.5-10/src/xdrv/wcmMapping.c
linuxwacom-0.8.5-10/src/xdrv/wcmTilt2Rotation.c
linuxwacom-0.8.5-10/src/xdrv/wcmXCommand.c
linuxwacom-0.8.5-10/src/xdrv/wcmTouchFilter.c
linuxwacom-0.8.5-10/src/xdrv/wcmUSB.c
linuxwacom-0.8.5-10/src/xdrv/xf86Wacom.c
linuxwacom-0.8.5-10/src/xdrv/Makefile.in
linuxwacom-0.8.5-10/src/xdrv/wcmCompat.c
linuxwacom-0.8.5-10/src/xdrv/Makefile.am
linuxwacom-0.8.5-10/src/xdrv/wcmSerial.c
linuxwacom-0.8.5-10/src/xdrv/wcmSerial.h
linuxwacom-0.8.5-10/src/xdrv/wcmValidateDevice.c
linuxwacom-0.8.5-10/src/xdrv/xf86WacomDefs.h
linuxwacom-0.8.5-10/src/xdrv/wcmISDV4.c
linuxwacom-0.8.5-10/src/xdrv/wcmFilter.h
linuxwacom-0.8.5-10/src/xdrv/xf86Wacom.h
linuxwacom-0.8.5-10/src/xdrv/wcmFilter.c
linuxwacom-0.8.5-10/src/xdrv/wcmCommon.c
linuxwacom-0.8.5-10/src/xdrv/wcmConfig.c
linuxwacom-0.8.5-10/src/2.6.9/
linuxwacom-0.8.5-10/src/2.6.9/Makefile.in
linuxwacom-0.8.5-10/src/2.6.9/wacom.c
linuxwacom-0.8.5-10/src/2.6.9/hid-core.c
linuxwacom-0.8.5-10/src/2.6.22/
linuxwacom-0.8.5-10/src/2.6.22/Makefile.in
linuxwacom-0.8.5-10/src/2.6.22/wacom_sys.c
linuxwacom-0.8.5-10/src/2.6.22/wacom_wac.h
linuxwacom-0.8.5-10/src/2.6.26/
linuxwacom-0.8.5-10/src/2.6.26/Makefile.in
linuxwacom-0.8.5-10/src/2.6.26/wacom.h
linuxwacom-0.8.5-10/src/2.6.26/wacom_sys.c
linuxwacom-0.8.5-10/src/2.6.24/
linuxwacom-0.8.5-10/src/2.6.24/Makefile.in
linuxwacom-0.8.5-10/src/2.6.24/wacom.h
linuxwacom-0.8.5-10/src/2.6.24/wacom_sys.c
linuxwacom-0.8.5-10/src/2.6.18/
linuxwacom-0.8.5-10/src/2.6.18/Makefile.in
linuxwacom-0.8.5-10/src/2.6.18/wacom.h
linuxwacom-0.8.5-10/src/2.6.15/
linuxwacom-0.8.5-10/src/2.6.15/Makefile.in
linuxwacom-0.8.5-10/src/2.6.15/hid-core.c
linuxwacom-0.8.5-10/src/2.6.15/wacom_sys.c
linuxwacom-0.8.5-10/src/2.6.14/
linuxwacom-0.8.5-10/src/2.6.14/Makefile.in
linuxwacom-0.8.5-10/src/2.6.14/hid-core.c
linuxwacom-0.8.5-10/src/2.6.13/
linuxwacom-0.8.5-10/src/2.6.13/Makefile.in
linuxwacom-0.8.5-10/src/2.6.13/wacom.h
linuxwacom-0.8.5-10/src/2.6.13/hid-core.c
linuxwacom-0.8.5-10/src/2.6.13/wacom_sys.c
linuxwacom-0.8.5-10/src/2.6.16/
linuxwacom-0.8.5-10/src/2.6.16/Makefile.in
linuxwacom-0.8.5-10/src/2.6.16/wacom.h
linuxwacom-0.8.5-10/src/2.6.16/hid-core.c
linuxwacom-0.8.5-10/src/2.6.16/wacom_sys.c
linuxwacom-0.8.5-10/src/2.6.16/wacom_wac.h
linuxwacom-0.8.5-10/src/2.6.16/wacom_wac.c
linuxwacom-0.8.5-10/src/2.6.11/
linuxwacom-0.8.5-10/src/2.6.11/Makefile.in
linuxwacom-0.8.5-10/src/2.6.11/wacom.h
linuxwacom-0.8.5-10/src/2.6.11/hid-core.c
linuxwacom-0.8.5-10/src/2.6.11/wacom_sys.c
linuxwacom-0.8.5-10/src/include/
linuxwacom-0.8.5-10/src/include/util-config.h.in
linuxwacom-0.8.5-10/src/include/xdrv-config.h.in
linuxwacom-0.8.5-10/src/include/kernel-config.h.in
linuxwacom-0.8.5-10/src/include/Xwacom.h
linuxwacom-0.8.5-10/src/util/
linuxwacom-0.8.5-10/src/util/Makefile.in
linuxwacom-0.8.5-10/src/util/wcmAction.h
linuxwacom-0.8.5-10/src/util/Makefile.am
linuxwacom-0.8.5-10/src/util/wacdump.c
linuxwacom-0.8.5-10/src/util/wacomcfg.h
linuxwacom-0.8.5-10/src/util/wacserial.c
linuxwacom-0.8.5-10/src/util/wacusb.c
linuxwacom-0.8.5-10/src/util/wactablet.c
linuxwacom-0.8.5-10/src/util/xsetwacom.c
linuxwacom-0.8.5-10/src/util/wacscrn.c
linuxwacom-0.8.5-10/src/util/wacomcfg.c
linuxwacom-0.8.5-10/src/util/wactablet.h
linuxwacom-0.8.5-10/src/util/xidump.c
linuxwacom-0.8.5-10/src/util/10-linuxwacom.fdi
linuxwacom-0.8.5-10/src/util/wcmAction.c
linuxwacom-0.8.5-10/src/util/wacusb.h
linuxwacom-0.8.5-10/src/util/hal-setup-wacom.c
linuxwacom-0.8.5-10/src/util/wacscrn.h
linuxwacom-0.8.5-10/src/util/wacserial.h
linuxwacom-0.8.5-10/src/util/60-wacom.rules
linuxwacom-0.8.5-10/install-sh
tj@xt2:~/lw-ntrig$ cd linuxwacom-0.8.5-10
tj@xt2:~/lw-ntrig/linuxwacom-0.8.5-10$ ./configure --enable-wacom --prefix=/usr
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for a thread-safe mkdir -p... /bin/mkdir -p
checking for gawk... gawk
checking whether make sets $(MAKE)... yes
checking whether to enable maintainer-specific portions of Makefiles... no
checking for gcc... gcc
checking for C compiler default output file name... a.out
checking whether the C compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables... 
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ISO C89... none needed
checking for style of include used by make... GNU
checking dependency style of gcc... gcc3
checking for gawk... (cached) gawk
checking build system type... x86_64-unknown-linux-gnu
checking host system type... x86_64-unknown-linux-gnu
checking for a sed that does not truncate output... /bin/sed
checking for grep that handles long lines and -e... /bin/grep
checking for egrep... /bin/grep -E
checking for ld used by gcc... /usr/bin/ld
checking if the linker (/usr/bin/ld) is GNU ld... yes
checking for /usr/bin/ld option to reload object files... -r
checking for BSD-compatible nm... /usr/bin/nm -B
checking whether ln -s works... yes
checking how to recognize dependent libraries... pass_all
checking how to run the C preprocessor... gcc -E
checking for ANSI C header files... yes
checking for sys/types.h... yes
checking for sys/stat.h... yes
checking for stdlib.h... yes
checking for string.h... yes
checking for memory.h... yes
checking for strings.h... yes
checking for inttypes.h... yes
checking for stdint.h... yes
checking for unistd.h... yes
checking dlfcn.h usability... yes
checking dlfcn.h presence... yes
checking for dlfcn.h... yes
checking for g++... g++
checking whether we are using the GNU C++ compiler... yes
checking whether g++ accepts -g... yes
checking dependency style of g++... gcc3
checking how to run the C++ preprocessor... g++ -E
checking for g77... no
checking for xlf... no
checking for f77... no
checking for frt... no
checking for pgf77... no
checking for cf77... no
checking for fort77... no
checking for fl32... no
checking for af77... no
checking for xlf90... no
checking for f90... no
checking for pgf90... no
checking for pghpf... no
checking for epcf90... no
checking for gfortran... no
checking for g95... no
checking for xlf95... no
checking for f95... no
checking for fort... no
checking for ifort... no
checking for ifc... no
checking for efc... no
checking for pgf95... no
checking for lf95... no
checking for ftn... no
checking whether we are using the GNU Fortran 77 compiler... no
checking whether  accepts -g... no
checking the maximum length of command line arguments... 1572864
checking command to parse /usr/bin/nm -B output from gcc object... ok
checking for objdir... .libs
checking for ar... ar
checking for ranlib... ranlib
checking for strip... strip
checking if gcc supports -fno-rtti -fno-exceptions... no
checking for gcc option to produce PIC... -fPIC
checking if gcc PIC flag -fPIC works... yes
checking if gcc static flag -static works... yes
checking if gcc supports -c -o file.o... yes
checking whether the gcc linker (/usr/bin/ld -m elf_x86_64) supports shared libraries... yes
checking whether -lc should be explicitly linked in... no
checking dynamic linker characteristics... GNU/Linux ld.so
checking how to hardcode library paths into programs... immediate
checking whether stripping libraries is possible... yes
checking if libtool supports shared libraries... yes
checking whether to build shared libraries... yes
checking whether to build static libraries... yes
configure: creating libtool
appending configuration tag "CXX" to libtool
checking for ld used by g++... /usr/bin/ld -m elf_x86_64
checking if the linker (/usr/bin/ld -m elf_x86_64) is GNU ld... yes
checking whether the g++ linker (/usr/bin/ld -m elf_x86_64) supports shared libraries... yes
checking for g++ option to produce PIC... -fPIC
checking if g++ PIC flag -fPIC works... yes
checking if g++ static flag -static works... yes
checking if g++ supports -c -o file.o... yes
checking whether the g++ linker (/usr/bin/ld -m elf_x86_64) supports shared libraries... yes
checking dynamic linker characteristics... GNU/Linux ld.so
(cached) (cached) checking how to hardcode library paths into programs... immediate
appending configuration tag "F77" to libtool
checking for pkg-config... /usr/bin/pkg-config
checking pkg-config is at least version 0.9.0... yes
checking for HAL... yes
checking for arch type... x86_64-linux-gnu
checking for kernel type... Linux
checking for linux-based kernel... yes
checking for kernel source/headers... /lib/modules/2.6.31-20-generic/build
checking kernel version... 2.6.31-20-generic
checking for kernel module support... yes
checking for Xlib... yes
checking for XSERVER... yes
checking for xserver libc-wrapper header-files... no
checking if scaling tablet to screen size is needed... no
checking if Xorg server is version 1.4 or later... yes
checking if Xorg is 7.3 or earlier... no
checking if Xorg server is version 1.5.2 or later... yes
checking if Xorg server is version 1.6 or later... yes
checking if Xorg SDK defined IsXExtensionPointer... yes
checking if Xorg SDK defines dixScreenOrigins... yes
checking XInput extension version... >= 2.0
checking for lib xf86config... checking for X... libraries , headers 
checking for gethostbyname... yes
checking for connect... yes
checking for remove... yes
checking for shmat... yes
checking for IceConnectionNumber in -lICE... yes
checking for tclsh... /usr/bin/tclsh
checking for tcl version... 8.4
checking for tcl header files... found, /usr/include/tcl
checking for tk header files... found, /usr/include/tcl
checking ncurses.h usability... yes
checking ncurses.h presence... yes
checking for ncurses.h... yes
checking if libwacomcfg should/can be built... yes
checking if libwacomxi should/can be built... yes
checking if wacdump should/can be built... yes
checking if xidump should/can be built... yes
checking if xsetwacom should be built... yes
checking for Wacom X driver module path... /usr/lib/xorg/modules/input
checking for dynamic driver loading support... yes
checking if wacom_drv.{o,so} should be compiled... yes
checking if gcc accepts -fno-merge-constants... yes
checking if gcc accepts -fno-stack-protector... yes

configure: creating ./config.status
config.status: creating Makefile
config.status: creating mkxincludes
config.status: creating src/Makefile
config.status: creating src/util/Makefile
config.status: creating src/xdrv/Makefile
config.status: creating src/2.6.9/Makefile
config.status: creating src/2.6.10/Makefile
config.status: creating src/2.6.11/Makefile
config.status: creating src/2.6.13/Makefile
config.status: creating src/2.6.14/Makefile
config.status: creating src/2.6.15/Makefile
config.status: creating src/2.6.16/Makefile
config.status: creating src/2.6.18/Makefile
config.status: creating src/2.6.19/Makefile
config.status: creating src/2.6.22/Makefile
config.status: creating src/2.6.24/Makefile
config.status: creating src/2.6.26/Makefile
config.status: creating src/2.6.27/Makefile
config.status: creating src/wacomxi/Makefile
config.status: creating src/wacomxi/wacomcpl
config.status: creating src/include/xdrv-config.h
config.status: creating src/include/kernel-config.h
config.status: creating src/include/util-config.h
config.status: executing depfiles commands

----------------------------------------
  BUILD ENVIRONMENT:
       architecture - x86_64-linux-gnu
       linux kernel - yes 2.6.27
  module versioning - no 
      kernel source - yes /lib/modules/2.6.31-20-generic/build
     XFree86 source - no 
           Xorg SDK - yes /usr/include/xorg
          XSERVER64 - yes
           dlloader - yes
               XLib - yes /usr/lib
         xf86config - no
                TCL - yes /usr/include/tcl
                 TK - yes /usr/include/tcl
            ncurses - yes

  BUILD OPTIONS:
            wacom.o - yes
            wacdump - yes 
             xidump - yes 
        libwacomcfg - yes
         libwacomxi - yes
          xsetwacom - yes
              hid.o - no 
       wacom_drv.so - yes /usr/lib/xorg/modules/input 
        wacom_drv.o - no
  wacom*_drv quirks - hal IsXExtensionPointer key-events dixScreenOrigins
----------------------------------------
tj@xt2:~/lw-ntrig/linuxwacom-0.8.5-10$ make
Making all in src
make[1]: Entering directory `/home/tj/lw-ntrig/linuxwacom-0.8.5-10/src'
Making all in .
make[2]: Entering directory `/home/tj/lw-ntrig/linuxwacom-0.8.5-10/src'
rm -f wacom.4x.gz
gzip -9c < ./wacom.4x > wacom.4x.gz
make[2]: Leaving directory `/home/tj/lw-ntrig/linuxwacom-0.8.5-10/src'
Making all in wacomxi
make[2]: Entering directory `/home/tj/lw-ntrig/linuxwacom-0.8.5-10/src/wacomxi'
/bin/bash ../../libtool --tag=CC   --mode=compile gcc -DHAVE_CONFIG_H -I. -I../../src/include    -Wall -g -O2 -D__amd64__ -I/usr/include/tcl -MT wacomxi.lo -MD -MP -MF .deps/wacomxi.Tpo -c -o wacomxi.lo wacomxi.c
mkdir .libs
 gcc -DHAVE_CONFIG_H -I. -I../../src/include -Wall -g -O2 -D__amd64__ -I/usr/include/tcl -MT wacomxi.lo -MD -MP -MF .deps/wacomxi.Tpo -c wacomxi.c  -fPIC -DPIC -o .libs/wacomxi.o
 gcc -DHAVE_CONFIG_H -I. -I../../src/include -Wall -g -O2 -D__amd64__ -I/usr/include/tcl -MT wacomxi.lo -MD -MP -MF .deps/wacomxi.Tpo -c wacomxi.c -o wacomxi.o >/dev/null 2>&1
mv -f .deps/wacomxi.Tpo .deps/wacomxi.Plo
/bin/bash ../../libtool --tag=CC   --mode=link gcc -Wall -g -O2 -D__amd64__ -I/usr/include/tcl -no-undefined  -o libwacomxi.la -rpath /usr/lib/TkXInput wacomxi.lo -L/usr/lib -lX11 -lXi 
gcc -shared  .libs/wacomxi.o  -L/usr/lib -lX11 -lXi  -Wl,-soname -Wl,libwacomxi.so.0 -o .libs/libwacomxi.so.0.0.0
(cd .libs && rm -f libwacomxi.so.0 && ln -s libwacomxi.so.0.0.0 libwacomxi.so.0)
(cd .libs && rm -f libwacomxi.so && ln -s libwacomxi.so.0.0.0 libwacomxi.so)
ar cru .libs/libwacomxi.a  wacomxi.o
ranlib .libs/libwacomxi.a
creating libwacomxi.la
(cd .libs && rm -f libwacomxi.la && ln -s ../libwacomxi.la libwacomxi.la)
make[2]: Leaving directory `/home/tj/lw-ntrig/linuxwacom-0.8.5-10/src/wacomxi'
Making all in util
make[2]: Entering directory `/home/tj/lw-ntrig/linuxwacom-0.8.5-10/src/util'
/bin/bash ../../libtool --tag=CC   --mode=compile gcc -DHAVE_CONFIG_H -I. -I../../src/include    -Wall -pedantic -I/usr/include/xorg  -DDBUS_API_SUBJECT_TO_CHANGE -I/usr/include/hal -I/usr/include/dbus-1.0 -I/usr/lib/dbus-1.0/include   -g -O2 -D__amd64__ -I/usr/include/tcl -MT wacomcfg.lo -MD -MP -MF .deps/wacomcfg.Tpo -c -o wacomcfg.lo wacomcfg.c
mkdir .libs
 gcc -DHAVE_CONFIG_H -I. -I../../src/include -Wall -pedantic -I/usr/include/xorg -DDBUS_API_SUBJECT_TO_CHANGE -I/usr/include/hal -I/usr/include/dbus-1.0 -I/usr/lib/dbus-1.0/include -g -O2 -D__amd64__ -I/usr/include/tcl -MT wacomcfg.lo -MD -MP -MF .deps/wacomcfg.Tpo -c wacomcfg.c  -fPIC -DPIC -o .libs/wacomcfg.o
 gcc -DHAVE_CONFIG_H -I. -I../../src/include -Wall -pedantic -I/usr/include/xorg -DDBUS_API_SUBJECT_TO_CHANGE -I/usr/include/hal -I/usr/include/dbus-1.0 -I/usr/lib/dbus-1.0/include -g -O2 -D__amd64__ -I/usr/include/tcl -MT wacomcfg.lo -MD -MP -MF .deps/wacomcfg.Tpo -c wacomcfg.c -o wacomcfg.o >/dev/null 2>&1
mv -f .deps/wacomcfg.Tpo .deps/wacomcfg.Plo
/bin/bash ../../libtool --tag=CC   --mode=link gcc -Wall -pedantic -I/usr/include/xorg  -DDBUS_API_SUBJECT_TO_CHANGE -I/usr/include/hal -I/usr/include/dbus-1.0 -I/usr/lib/dbus-1.0/include   -g -O2 -D__amd64__ -I/usr/include/tcl -no-undefined -version-info 0:1:0  -o libwacomcfg.la -rpath /usr/lib wacomcfg.lo -L/usr/lib -lX11 -lXi 
gcc -shared  .libs/wacomcfg.o  -L/usr/lib -lX11 -lXi  -Wl,-soname -Wl,libwacomcfg.so.0 -o .libs/libwacomcfg.so.0.0.1
(cd .libs && rm -f libwacomcfg.so.0 && ln -s libwacomcfg.so.0.0.1 libwacomcfg.so.0)
(cd .libs && rm -f libwacomcfg.so && ln -s libwacomcfg.so.0.0.1 libwacomcfg.so)
ar cru .libs/libwacomcfg.a  wacomcfg.o
ranlib .libs/libwacomcfg.a
creating libwacomcfg.la
(cd .libs && rm -f libwacomcfg.la && ln -s ../libwacomcfg.la libwacomcfg.la)
gcc -DHAVE_CONFIG_H -I. -I../../src/include    -Wall -pedantic -I/usr/include/xorg  -DDBUS_API_SUBJECT_TO_CHANGE -I/usr/include/hal -I/usr/include/dbus-1.0 -I/usr/lib/dbus-1.0/include   -g -O2 -D__amd64__ -I/usr/include/tcl -MT wacdump.o -MD -MP -MF .deps/wacdump.Tpo -c -o wacdump.o wacdump.c
mv -f .deps/wacdump.Tpo .deps/wacdump.Po
gcc -DHAVE_CONFIG_H -I. -I../../src/include    -Wall -pedantic -I/usr/include/xorg  -DDBUS_API_SUBJECT_TO_CHANGE -I/usr/include/hal -I/usr/include/dbus-1.0 -I/usr/lib/dbus-1.0/include   -g -O2 -D__amd64__ -I/usr/include/tcl -MT wacscrn.o -MD -MP -MF .deps/wacscrn.Tpo -c -o wacscrn.o wacscrn.c
mv -f .deps/wacscrn.Tpo .deps/wacscrn.Po
gcc -DHAVE_CONFIG_H -I. -I../../src/include    -Wall -pedantic -I/usr/include/xorg  -DDBUS_API_SUBJECT_TO_CHANGE -I/usr/include/hal -I/usr/include/dbus-1.0 -I/usr/lib/dbus-1.0/include   -g -O2 -D__amd64__ -I/usr/include/tcl -MT wactablet.o -MD -MP -MF .deps/wactablet.Tpo -c -o wactablet.o wactablet.c
mv -f .deps/wactablet.Tpo .deps/wactablet.Po
gcc -DHAVE_CONFIG_H -I. -I../../src/include    -Wall -pedantic -I/usr/include/xorg  -DDBUS_API_SUBJECT_TO_CHANGE -I/usr/include/hal -I/usr/include/dbus-1.0 -I/usr/lib/dbus-1.0/include   -g -O2 -D__amd64__ -I/usr/include/tcl -MT wacserial.o -MD -MP -MF .deps/wacserial.Tpo -c -o wacserial.o wacserial.c
wacserial.c: In function ‘WacomFlush’:
wacserial.c:1345: warning: ignoring return value of ‘read’, declared with attribute warn_unused_result
mv -f .deps/wacserial.Tpo .deps/wacserial.Po
gcc -DHAVE_CONFIG_H -I. -I../../src/include    -Wall -pedantic -I/usr/include/xorg  -DDBUS_API_SUBJECT_TO_CHANGE -I/usr/include/hal -I/usr/include/dbus-1.0 -I/usr/lib/dbus-1.0/include   -g -O2 -D__amd64__ -I/usr/include/tcl -MT wacusb.o -MD -MP -MF .deps/wacusb.Tpo -c -o wacusb.o wacusb.c
mv -f .deps/wacusb.Tpo .deps/wacusb.Po
/bin/bash ../../libtool --tag=CC   --mode=link gcc -Wall -pedantic -I/usr/include/xorg  -DDBUS_API_SUBJECT_TO_CHANGE -I/usr/include/hal -I/usr/include/dbus-1.0 -I/usr/lib/dbus-1.0/include   -g -O2 -D__amd64__ -I/usr/include/tcl   -o wacdump wacdump.o wacscrn.o wactablet.o wacserial.o wacusb.o -lncurses 
gcc -Wall -pedantic -I/usr/include/xorg -DDBUS_API_SUBJECT_TO_CHANGE -I/usr/include/hal -I/usr/include/dbus-1.0 -I/usr/lib/dbus-1.0/include -g -O2 -D__amd64__ -I/usr/include/tcl -o wacdump wacdump.o wacscrn.o wactablet.o wacserial.o wacusb.o  -lncurses  
gcc -DHAVE_CONFIG_H -I. -I../../src/include    -Wall -pedantic -I/usr/include/xorg  -DDBUS_API_SUBJECT_TO_CHANGE -I/usr/include/hal -I/usr/include/dbus-1.0 -I/usr/lib/dbus-1.0/include   -g -O2 -D__amd64__ -I/usr/include/tcl -MT xidump.o -MD -MP -MF .deps/xidump.Tpo -c -o xidump.o xidump.c
xidump.c: In function ‘RawRunAccel’:
xidump.c:770: warning: dereferencing pointer ‘pMove’ does break strict-aliasing rules
xidump.c:769: note: initialized from here
xidump.c:772: warning: dereferencing pointer ‘event.63’ does break strict-aliasing rules
xidump.c:772: note: initialized from here
xidump.c:774: warning: dereferencing pointer ‘event.63’ does break strict-aliasing rules
xidump.c:774: note: initialized from here
xidump.c: In function ‘RawRun’:
xidump.c:718: warning: dereferencing pointer ‘pAny.58’ does break strict-aliasing rules
xidump.c:718: note: initialized from here
xidump.c:717: warning: dereferencing pointer ‘pAny.58’ does break strict-aliasing rules
xidump.c:717: note: initialized from here
xidump.c:716: warning: dereferencing pointer ‘pAny.58’ does break strict-aliasing rules
xidump.c:716: note: initialized from here
xidump.c:711: warning: dereferencing pointer ‘pAny.58’ does break strict-aliasing rules
xidump.c:715: note: initialized from here
xidump.c:711: warning: dereferencing pointer ‘pAny.58’ does break strict-aliasing rules
xidump.c:714: note: initialized from here
xidump.c:711: warning: dereferencing pointer ‘pAny.58’ does break strict-aliasing rules
xidump.c:713: note: initialized from here
xidump.c:725: warning: dereferencing pointer ‘pBtn’ does break strict-aliasing rules
xidump.c:724: note: initialized from here
xidump.c:733: warning: dereferencing pointer ‘pKey’ does break strict-aliasing rules
xidump.c:732: note: initialized from here
xidump.c: In function ‘CursesRun’:
xidump.c:571: warning: dereferencing pointer ‘pAny.53’ does break strict-aliasing rules
xidump.c:572: note: initialized from here
xidump.c:580: warning: dereferencing pointer ‘pAny.53’ does break strict-aliasing rules
xidump.c:580: note: initialized from here
xidump.c:590: warning: dereferencing pointer ‘pAny.53’ does break strict-aliasing rules
xidump.c:590: note: initialized from here
xidump.c:625: warning: dereferencing pointer ‘pBtn’ does break strict-aliasing rules
xidump.c:623: warning: dereferencing pointer ‘pBtn’ does break strict-aliasing rules
xidump.c:620: note: initialized from here
xidump.c:642: warning: dereferencing pointer ‘pKey’ does break strict-aliasing rules
xidump.c:640: warning: dereferencing pointer ‘pKey’ does break strict-aliasing rules
xidump.c:638: note: initialized from here
mv -f .deps/xidump.Tpo .deps/xidump.Po
/bin/bash ../../libtool --tag=CC   --mode=link gcc -Wall -pedantic -I/usr/include/xorg  -DDBUS_API_SUBJECT_TO_CHANGE -I/usr/include/hal -I/usr/include/dbus-1.0 -I/usr/lib/dbus-1.0/include   -g -O2 -D__amd64__ -I/usr/include/tcl -L/usr/lib -lX11 -lXi -lm  -o xidump xidump.o wacscrn.o -lncurses 
gcc -Wall -pedantic -I/usr/include/xorg -DDBUS_API_SUBJECT_TO_CHANGE -I/usr/include/hal -I/usr/include/dbus-1.0 -I/usr/lib/dbus-1.0/include -g -O2 -D__amd64__ -I/usr/include/tcl -o xidump xidump.o wacscrn.o  -L/usr/lib -lX11 -lXi -lm -lncurses  
gcc -DHAVE_CONFIG_H -I. -I../../src/include    -Wall -pedantic -I/usr/include/xorg  -DDBUS_API_SUBJECT_TO_CHANGE -I/usr/include/hal -I/usr/include/dbus-1.0 -I/usr/lib/dbus-1.0/include   -g -O2 -D__amd64__ -I/usr/include/tcl -MT xsetwacom.o -MD -MP -MF .deps/xsetwacom.Tpo -c -o xsetwacom.o xsetwacom.c
mv -f .deps/xsetwacom.Tpo .deps/xsetwacom.Po
gcc -DHAVE_CONFIG_H -I. -I../../src/include    -Wall -pedantic -I/usr/include/xorg  -DDBUS_API_SUBJECT_TO_CHANGE -I/usr/include/hal -I/usr/include/dbus-1.0 -I/usr/lib/dbus-1.0/include   -g -O2 -D__amd64__ -I/usr/include/tcl -MT wcmAction.o -MD -MP -MF .deps/wcmAction.Tpo -c -o wcmAction.o wcmAction.c
mv -f .deps/wcmAction.Tpo .deps/wcmAction.Po
/bin/bash ../../libtool --tag=CC   --mode=link gcc -Wall -pedantic -I/usr/include/xorg  -DDBUS_API_SUBJECT_TO_CHANGE -I/usr/include/hal -I/usr/include/dbus-1.0 -I/usr/lib/dbus-1.0/include   -g -O2 -D__amd64__ -I/usr/include/tcl   -o xsetwacom xsetwacom.o wcmAction.o libwacomcfg.la 
gcc -Wall -pedantic -I/usr/include/xorg -DDBUS_API_SUBJECT_TO_CHANGE -I/usr/include/hal -I/usr/include/dbus-1.0 -I/usr/lib/dbus-1.0/include -g -O2 -D__amd64__ -I/usr/include/tcl -o .libs/xsetwacom xsetwacom.o wcmAction.o  ./.libs/libwacomcfg.so -L/usr/lib -lX11 -lXi 
creating xsetwacom
gcc -DHAVE_CONFIG_H -I. -I../../src/include    -Wall -pedantic -I/usr/include/xorg  -DDBUS_API_SUBJECT_TO_CHANGE -I/usr/include/hal -I/usr/include/dbus-1.0 -I/usr/lib/dbus-1.0/include   -g -O2 -D__amd64__ -I/usr/include/tcl -MT hal-setup-wacom.o -MD -MP -MF .deps/hal-setup-wacom.Tpo -c -o hal-setup-wacom.o hal-setup-wacom.c
hal-setup-wacom.c: In function ‘main’:
hal-setup-wacom.c:54: warning: ignoring return value of ‘asprintf’, declared with attribute warn_unused_result
hal-setup-wacom.c:137: warning: ignoring return value of ‘asprintf’, declared with attribute warn_unused_result
mv -f .deps/hal-setup-wacom.Tpo .deps/hal-setup-wacom.Po
/bin/bash ../../libtool --tag=CC   --mode=link gcc -Wall -pedantic -I/usr/include/xorg  -DDBUS_API_SUBJECT_TO_CHANGE -I/usr/include/hal -I/usr/include/dbus-1.0 -I/usr/lib/dbus-1.0/include   -g -O2 -D__amd64__ -I/usr/include/tcl   -o hal-setup-wacom hal-setup-wacom.o -L/lib -lhal -ldbus-1 -lpthread -lrt   
gcc -Wall -pedantic -I/usr/include/xorg -DDBUS_API_SUBJECT_TO_CHANGE -I/usr/include/hal -I/usr/include/dbus-1.0 -I/usr/lib/dbus-1.0/include -g -O2 -D__amd64__ -I/usr/include/tcl -o hal-setup-wacom hal-setup-wacom.o  -L/lib -lhal -ldbus-1 -lpthread -lrt  
make[2]: Leaving directory `/home/tj/lw-ntrig/linuxwacom-0.8.5-10/src/util'
Making all in xdrv
make[2]: Entering directory `/home/tj/lw-ntrig/linuxwacom-0.8.5-10/src/xdrv'
gcc -MM -g -O2 -D__amd64__ -I/usr/include/tcl  -I../include -I/usr/include/xorg   ./xf86Wacom.c ./wcmSerial.c ./wcmUSB.c ./wcmISDV4.c ./wcmXCommand.c ./wcmCommon.c ./wcmCompat.c ./wcmConfig.c ./wcmFilter.c ./wcmTilt2Rotation.c ./wcmTouchFilter.c ./wcmValidateDevice.c ./wcmMapping.c > .depend
make[2]: Leaving directory `/home/tj/lw-ntrig/linuxwacom-0.8.5-10/src/xdrv'
make[2]: Entering directory `/home/tj/lw-ntrig/linuxwacom-0.8.5-10/src/xdrv'
gcc -g -O2 -D__amd64__ -I/usr/include/tcl  -fPIC -pipe -std=c99 \
		-pedantic -Wall -Wpointer-arith -fno-merge-constants \
		-fno-stack-protector -I. -I../include -I/usr/include/xorg   \
		-D_XSERVER64 -I/usr/include/xorg -I/usr/include/pixman-1   \
		-o xf86Wacom.o -c ./xf86Wacom.c
In file included from ./xf86Wacom.h:27,
                 from ./xf86Wacom.c:102:
/usr/include/xorg/xorg-server.h:105:1: warning: "XKB" redefined
In file included from ./xf86Wacom.h:25,
                 from ./xf86Wacom.c:102:
./../include/xdrv-config.h:18:1: warning: this is the location of the previous definition
In file included from ./xf86Wacom.h:27,
                 from ./xf86Wacom.c:102:
/usr/include/xorg/xorg-server.h:195:1: warning: "XFree86LOADER" redefined
In file included from ./xf86Wacom.h:25,
                 from ./xf86Wacom.c:102:
./../include/xdrv-config.h:12:1: warning: this is the location of the previous definition
gcc -g -O2 -D__amd64__ -I/usr/include/tcl  -fPIC -pipe -std=c99 \
		-pedantic -Wall -Wpointer-arith -fno-merge-constants \
		-fno-stack-protector -I. -I../include -I/usr/include/xorg   \
		-D_XSERVER64 -I/usr/include/xorg -I/usr/include/pixman-1   \
		-o wcmSerial.o -c ./wcmSerial.c
In file included from ./xf86Wacom.h:27,
                 from ./wcmSerial.c:20:
/usr/include/xorg/xorg-server.h:105:1: warning: "XKB" redefined
In file included from ./xf86Wacom.h:25,
                 from ./wcmSerial.c:20:
./../include/xdrv-config.h:18:1: warning: this is the location of the previous definition
In file included from ./xf86Wacom.h:27,
                 from ./wcmSerial.c:20:
/usr/include/xorg/xorg-server.h:195:1: warning: "XFree86LOADER" redefined
In file included from ./xf86Wacom.h:25,
                 from ./wcmSerial.c:20:
./../include/xdrv-config.h:12:1: warning: this is the location of the previous definition
gcc -g -O2 -D__amd64__ -I/usr/include/tcl  -fPIC -pipe -std=c99 \
		-pedantic -Wall -Wpointer-arith -fno-merge-constants \
		-fno-stack-protector -I. -I../include -I/usr/include/xorg   \
		-D_XSERVER64 -I/usr/include/xorg -I/usr/include/pixman-1   \
		-o wcmUSB.o -c ./wcmUSB.c
In file included from ./xf86Wacom.h:27,
                 from ./wcmUSB.c:20:
/usr/include/xorg/xorg-server.h:105:1: warning: "XKB" redefined
In file included from ./xf86Wacom.h:25,
                 from ./wcmUSB.c:20:
./../include/xdrv-config.h:18:1: warning: this is the location of the previous definition
In file included from ./xf86Wacom.h:27,
                 from ./wcmUSB.c:20:
/usr/include/xorg/xorg-server.h:195:1: warning: "XFree86LOADER" redefined
In file included from ./xf86Wacom.h:25,
                 from ./wcmUSB.c:20:
./../include/xdrv-config.h:12:1: warning: this is the location of the previous definition
gcc -g -O2 -D__amd64__ -I/usr/include/tcl  -fPIC -pipe -std=c99 \
		-pedantic -Wall -Wpointer-arith -fno-merge-constants \
		-fno-stack-protector -I. -I../include -I/usr/include/xorg   \
		-D_XSERVER64 -I/usr/include/xorg -I/usr/include/pixman-1   \
		-o wcmISDV4.o -c ./wcmISDV4.c
In file included from ./xf86Wacom.h:27,
                 from ./wcmISDV4.c:20:
/usr/include/xorg/xorg-server.h:105:1: warning: "XKB" redefined
In file included from ./xf86Wacom.h:25,
                 from ./wcmISDV4.c:20:
./../include/xdrv-config.h:18:1: warning: this is the location of the previous definition
In file included from ./xf86Wacom.h:27,
                 from ./wcmISDV4.c:20:
/usr/include/xorg/xorg-server.h:195:1: warning: "XFree86LOADER" redefined
In file included from ./xf86Wacom.h:25,
                 from ./wcmISDV4.c:20:
./../include/xdrv-config.h:12:1: warning: this is the location of the previous definition
gcc -g -O2 -D__amd64__ -I/usr/include/tcl  -fPIC -pipe -std=c99 \
		-pedantic -Wall -Wpointer-arith -fno-merge-constants \
		-fno-stack-protector -I. -I../include -I/usr/include/xorg   \
		-D_XSERVER64 -I/usr/include/xorg -I/usr/include/pixman-1   \
		-o wcmXCommand.o -c ./wcmXCommand.c
In file included from ./xf86Wacom.h:27,
                 from ./wcmXCommand.c:34:
/usr/include/xorg/xorg-server.h:105:1: warning: "XKB" redefined
In file included from ./xf86Wacom.h:25,
                 from ./wcmXCommand.c:34:
./../include/xdrv-config.h:18:1: warning: this is the location of the previous definition
In file included from ./xf86Wacom.h:27,
                 from ./wcmXCommand.c:34:
/usr/include/xorg/xorg-server.h:195:1: warning: "XFree86LOADER" redefined
In file included from ./xf86Wacom.h:25,
                 from ./wcmXCommand.c:34:
./../include/xdrv-config.h:12:1: warning: this is the location of the previous definition
gcc -g -O2 -D__amd64__ -I/usr/include/tcl  -fPIC -pipe -std=c99 \
		-pedantic -Wall -Wpointer-arith -fno-merge-constants \
		-fno-stack-protector -I. -I../include -I/usr/include/xorg   \
		-D_XSERVER64 -I/usr/include/xorg -I/usr/include/pixman-1   \
		-o wcmCommon.o -c ./wcmCommon.c
In file included from ./xf86Wacom.h:27,
                 from ./wcmCommon.c:20:
/usr/include/xorg/xorg-server.h:105:1: warning: "XKB" redefined
In file included from ./xf86Wacom.h:25,
                 from ./wcmCommon.c:20:
./../include/xdrv-config.h:18:1: warning: this is the location of the previous definition
In file included from ./xf86Wacom.h:27,
                 from ./wcmCommon.c:20:
/usr/include/xorg/xorg-server.h:195:1: warning: "XFree86LOADER" redefined
In file included from ./xf86Wacom.h:25,
                 from ./wcmCommon.c:20:
./../include/xdrv-config.h:12:1: warning: this is the location of the previous definition
gcc -g -O2 -D__amd64__ -I/usr/include/tcl  -fPIC -pipe -std=c99 \
		-pedantic -Wall -Wpointer-arith -fno-merge-constants \
		-fno-stack-protector -I. -I../include -I/usr/include/xorg   \
		-D_XSERVER64 -I/usr/include/xorg -I/usr/include/pixman-1   \
		-o wcmCompat.o -c ./wcmCompat.c
In file included from ./xf86Wacom.h:27,
                 from ./wcmCompat.c:19:
/usr/include/xorg/xorg-server.h:105:1: warning: "XKB" redefined
In file included from ./xf86Wacom.h:25,
                 from ./wcmCompat.c:19:
./../include/xdrv-config.h:18:1: warning: this is the location of the previous definition
In file included from ./xf86Wacom.h:27,
                 from ./wcmCompat.c:19:
/usr/include/xorg/xorg-server.h:195:1: warning: "XFree86LOADER" redefined
In file included from ./xf86Wacom.h:25,
                 from ./wcmCompat.c:19:
./../include/xdrv-config.h:12:1: warning: this is the location of the previous definition
gcc -g -O2 -D__amd64__ -I/usr/include/tcl  -fPIC -pipe -std=c99 \
		-pedantic -Wall -Wpointer-arith -fno-merge-constants \
		-fno-stack-protector -I. -I../include -I/usr/include/xorg   \
		-D_XSERVER64 -I/usr/include/xorg -I/usr/include/pixman-1   \
		-o wcmConfig.o -c ./wcmConfig.c
In file included from ./xf86Wacom.h:27,
                 from ./wcmConfig.c:20:
/usr/include/xorg/xorg-server.h:105:1: warning: "XKB" redefined
In file included from ./xf86Wacom.h:25,
                 from ./wcmConfig.c:20:
./../include/xdrv-config.h:18:1: warning: this is the location of the previous definition
In file included from ./xf86Wacom.h:27,
                 from ./wcmConfig.c:20:
/usr/include/xorg/xorg-server.h:195:1: warning: "XFree86LOADER" redefined
In file included from ./xf86Wacom.h:25,
                 from ./wcmConfig.c:20:
./../include/xdrv-config.h:12:1: warning: this is the location of the previous definition
gcc -g -O2 -D__amd64__ -I/usr/include/tcl  -fPIC -pipe -std=c99 \
		-pedantic -Wall -Wpointer-arith -fno-merge-constants \
		-fno-stack-protector -I. -I../include -I/usr/include/xorg   \
		-D_XSERVER64 -I/usr/include/xorg -I/usr/include/pixman-1   \
		-o wcmFilter.o -c ./wcmFilter.c
In file included from ./xf86Wacom.h:27,
                 from ./wcmFilter.h:23,
                 from ./wcmFilter.c:20:
/usr/include/xorg/xorg-server.h:105:1: warning: "XKB" redefined
In file included from ./xf86Wacom.h:25,
                 from ./wcmFilter.h:23,
                 from ./wcmFilter.c:20:
./../include/xdrv-config.h:18:1: warning: this is the location of the previous definition
In file included from ./xf86Wacom.h:27,
                 from ./wcmFilter.h:23,
                 from ./wcmFilter.c:20:
/usr/include/xorg/xorg-server.h:195:1: warning: "XFree86LOADER" redefined
In file included from ./xf86Wacom.h:25,
                 from ./wcmFilter.h:23,
                 from ./wcmFilter.c:20:
./../include/xdrv-config.h:12:1: warning: this is the location of the previous definition
gcc -g -O2 -D__amd64__ -I/usr/include/tcl  -fPIC -pipe -std=c99 \
		-pedantic -Wall -Wpointer-arith -fno-merge-constants \
		-fno-stack-protector -I. -I../include -I/usr/include/xorg   \
		-D_XSERVER64 -I/usr/include/xorg -I/usr/include/pixman-1   \
		-o wcmTilt2Rotation.o -c ./wcmTilt2Rotation.c
In file included from ./xf86Wacom.h:27,
                 from ./wcmTilt2Rotation.c:19:
/usr/include/xorg/xorg-server.h:105:1: warning: "XKB" redefined
In file included from ./xf86Wacom.h:25,
                 from ./wcmTilt2Rotation.c:19:
./../include/xdrv-config.h:18:1: warning: this is the location of the previous definition
In file included from ./xf86Wacom.h:27,
                 from ./wcmTilt2Rotation.c:19:
/usr/include/xorg/xorg-server.h:195:1: warning: "XFree86LOADER" redefined
In file included from ./xf86Wacom.h:25,
                 from ./wcmTilt2Rotation.c:19:
./../include/xdrv-config.h:12:1: warning: this is the location of the previous definition
gcc -g -O2 -D__amd64__ -I/usr/include/tcl  -fPIC -pipe -std=c99 \
		-pedantic -Wall -Wpointer-arith -fno-merge-constants \
		-fno-stack-protector -I. -I../include -I/usr/include/xorg   \
		-D_XSERVER64 -I/usr/include/xorg -I/usr/include/pixman-1   \
		-o wcmTouchFilter.o -c ./wcmTouchFilter.c
In file included from ./xf86Wacom.h:27,
                 from ./wcmTouchFilter.c:19:
/usr/include/xorg/xorg-server.h:105:1: warning: "XKB" redefined
In file included from ./xf86Wacom.h:25,
                 from ./wcmTouchFilter.c:19:
./../include/xdrv-config.h:18:1: warning: this is the location of the previous definition
In file included from ./xf86Wacom.h:27,
                 from ./wcmTouchFilter.c:19:
/usr/include/xorg/xorg-server.h:195:1: warning: "XFree86LOADER" redefined
In file included from ./xf86Wacom.h:25,
                 from ./wcmTouchFilter.c:19:
./../include/xdrv-config.h:12:1: warning: this is the location of the previous definition
gcc -g -O2 -D__amd64__ -I/usr/include/tcl  -fPIC -pipe -std=c99 \
		-pedantic -Wall -Wpointer-arith -fno-merge-constants \
		-fno-stack-protector -I. -I../include -I/usr/include/xorg   \
		-D_XSERVER64 -I/usr/include/xorg -I/usr/include/pixman-1   \
		-o wcmValidateDevice.o -c ./wcmValidateDevice.c
In file included from ./xf86Wacom.h:27,
                 from ./wcmValidateDevice.c:19:
/usr/include/xorg/xorg-server.h:105:1: warning: "XKB" redefined
In file included from ./xf86Wacom.h:25,
                 from ./wcmValidateDevice.c:19:
./../include/xdrv-config.h:18:1: warning: this is the location of the previous definition
In file included from ./xf86Wacom.h:27,
                 from ./wcmValidateDevice.c:19:
/usr/include/xorg/xorg-server.h:195:1: warning: "XFree86LOADER" redefined
In file included from ./xf86Wacom.h:25,
                 from ./wcmValidateDevice.c:19:
./../include/xdrv-config.h:12:1: warning: this is the location of the previous definition
gcc -g -O2 -D__amd64__ -I/usr/include/tcl  -fPIC -pipe -std=c99 \
		-pedantic -Wall -Wpointer-arith -fno-merge-constants \
		-fno-stack-protector -I. -I../include -I/usr/include/xorg   \
		-D_XSERVER64 -I/usr/include/xorg -I/usr/include/pixman-1   \
		-o wcmMapping.o -c ./wcmMapping.c
In file included from ./xf86Wacom.h:27,
                 from ./wcmMapping.c:19:
/usr/include/xorg/xorg-server.h:105:1: warning: "XKB" redefined
In file included from ./xf86Wacom.h:25,
                 from ./wcmMapping.c:19:
./../include/xdrv-config.h:18:1: warning: this is the location of the previous definition
In file included from ./xf86Wacom.h:27,
                 from ./wcmMapping.c:19:
/usr/include/xorg/xorg-server.h:195:1: warning: "XFree86LOADER" redefined
In file included from ./xf86Wacom.h:25,
                 from ./wcmMapping.c:19:
./../include/xdrv-config.h:12:1: warning: this is the location of the previous definition
gcc -shared -nostdlib -o wacom_drv.so xf86Wacom.o wcmSerial.o wcmUSB.o wcmISDV4.o wcmXCommand.o wcmCommon.o wcmCompat.o wcmConfig.o wcmFilter.o wcmTilt2Rotation.o wcmTouchFilter.o wcmValidateDevice.o wcmMapping.o -Bstatic -lgcc
make[2]: Leaving directory `/home/tj/lw-ntrig/linuxwacom-0.8.5-10/src/xdrv'
Making all in 2.6.27
make[2]: Entering directory `/home/tj/lw-ntrig/linuxwacom-0.8.5-10/src/2.6.27'
    Building linuxwacom drivers for 2.6 kernel.
***Note: Drivers not enabled as modules in your kernel config but requested through configure are NOT built
make -C /lib/modules/2.6.31-20-generic/build M=/home/tj/lw-ntrig/linuxwacom-0.8.5-10/src/2.6.27
make[3]: Entering directory `/usr/src/linux-headers-2.6.31-20-generic'
  LD      /home/tj/lw-ntrig/linuxwacom-0.8.5-10/src/2.6.27/built-in.o
  CC [M]  /home/tj/lw-ntrig/linuxwacom-0.8.5-10/src/2.6.27/wacom_wac.o
  CC [M]  /home/tj/lw-ntrig/linuxwacom-0.8.5-10/src/2.6.27/wacom_sys.o
  LD [M]  /home/tj/lw-ntrig/linuxwacom-0.8.5-10/src/2.6.27/wacom.o
  Building modules, stage 2.
  MODPOST 1 modules
  CC      /home/tj/lw-ntrig/linuxwacom-0.8.5-10/src/2.6.27/wacom.mod.o
  LD [M]  /home/tj/lw-ntrig/linuxwacom-0.8.5-10/src/2.6.27/wacom.ko
make[3]: Leaving directory `/usr/src/linux-headers-2.6.31-20-generic'
make[2]: Leaving directory `/home/tj/lw-ntrig/linuxwacom-0.8.5-10/src/2.6.27'
make[1]: Leaving directory `/home/tj/lw-ntrig/linuxwacom-0.8.5-10/src'
make[1]: Entering directory `/home/tj/lw-ntrig/linuxwacom-0.8.5-10'
make[1]: Nothing to be done for `all-am'.
make[1]: Leaving directory `/home/tj/lw-ntrig/linuxwacom-0.8.5-10'
tj@xt2:~/lw-ntrig/linuxwacom-0.8.5-10$ sudo make install
[sudo] password for tj: 
Making install in src
make[1]: Entering directory `/home/tj/lw-ntrig/linuxwacom-0.8.5-10/src'
Making install in .
make[2]: Entering directory `/home/tj/lw-ntrig/linuxwacom-0.8.5-10/src'
make[3]: Entering directory `/home/tj/lw-ntrig/linuxwacom-0.8.5-10/src'
make[3]: Nothing to be done for `install-exec-am'.
test -z "/usr/share/man/man4" || /bin/mkdir -p "/usr/share/man/man4"
 /usr/bin/install -c -m 644 'wacom.4x.gz' '/usr/share/man/man4/wacom.4x.gz'
make[3]: Leaving directory `/home/tj/lw-ntrig/linuxwacom-0.8.5-10/src'
make[2]: Leaving directory `/home/tj/lw-ntrig/linuxwacom-0.8.5-10/src'
Making install in wacomxi
make[2]: Entering directory `/home/tj/lw-ntrig/linuxwacom-0.8.5-10/src/wacomxi'
make[3]: Entering directory `/home/tj/lw-ntrig/linuxwacom-0.8.5-10/src/wacomxi'
make[3]: Nothing to be done for `install-exec-am'.
test -z "/usr/bin" || /bin/mkdir -p "/usr/bin"
 /usr/bin/install -c 'wacomcpl' '/usr/bin/wacomcpl'
 /usr/bin/install -c 'wacomcpl-exec' '/usr/bin/wacomcpl-exec'
test -z "/usr/lib/TkXInput" || /bin/mkdir -p "/usr/lib/TkXInput"
 /usr/bin/install -c -m 644 'pkgIndex.tcl' '/usr/lib/TkXInput/pkgIndex.tcl'
test -z "/usr/lib/TkXInput" || /bin/mkdir -p "/usr/lib/TkXInput"
 /bin/bash ../../libtool   --mode=install /usr/bin/install -c  'libwacomxi.la' '/usr/lib/TkXInput/libwacomxi.la'
/usr/bin/install -c .libs/libwacomxi.so.0.0.0 /usr/lib/TkXInput/libwacomxi.so.0.0.0
(cd /usr/lib/TkXInput && { ln -s -f libwacomxi.so.0.0.0 libwacomxi.so.0 || { rm -f libwacomxi.so.0 && ln -s libwacomxi.so.0.0.0 libwacomxi.so.0; }; })
(cd /usr/lib/TkXInput && { ln -s -f libwacomxi.so.0.0.0 libwacomxi.so || { rm -f libwacomxi.so && ln -s libwacomxi.so.0.0.0 libwacomxi.so; }; })
/usr/bin/install -c .libs/libwacomxi.lai /usr/lib/TkXInput/libwacomxi.la
/usr/bin/install -c .libs/libwacomxi.a /usr/lib/TkXInput/libwacomxi.a
chmod 644 /usr/lib/TkXInput/libwacomxi.a
ranlib /usr/lib/TkXInput/libwacomxi.a
PATH="$PATH:/sbin" ldconfig -n /usr/lib/TkXInput
----------------------------------------------------------------------
Libraries have been installed in:
   /usr/lib/TkXInput

If you ever happen to want to link against installed libraries
in a given directory, LIBDIR, you must either use libtool, and
specify the full pathname of the library, or use the `-LLIBDIR'
flag during linking and do at least one of the following:
   - add LIBDIR to the `LD_LIBRARY_PATH' environment variable
     during execution
   - add LIBDIR to the `LD_RUN_PATH' environment variable
     during linking
   - use the `-Wl,--rpath -Wl,LIBDIR' linker flag
   - have your system administrator add LIBDIR to `/etc/ld.so.conf'

See any operating system documentation about shared libraries for
more information, such as the ld(1) and ld.so(8) manual pages.
----------------------------------------------------------------------
make[3]: Leaving directory `/home/tj/lw-ntrig/linuxwacom-0.8.5-10/src/wacomxi'
make[2]: Leaving directory `/home/tj/lw-ntrig/linuxwacom-0.8.5-10/src/wacomxi'
Making install in util
make[2]: Entering directory `/home/tj/lw-ntrig/linuxwacom-0.8.5-10/src/util'
make[3]: Entering directory `/home/tj/lw-ntrig/linuxwacom-0.8.5-10/src/util'
test -z "/usr/lib" || /bin/mkdir -p "/usr/lib"
 /bin/bash ../../libtool   --mode=install /usr/bin/install -c  'libwacomcfg.la' '/usr/lib/libwacomcfg.la'
/usr/bin/install -c .libs/libwacomcfg.so.0.0.1 /usr/lib/libwacomcfg.so.0.0.1
(cd /usr/lib && { ln -s -f libwacomcfg.so.0.0.1 libwacomcfg.so.0 || { rm -f libwacomcfg.so.0 && ln -s libwacomcfg.so.0.0.1 libwacomcfg.so.0; }; })
(cd /usr/lib && { ln -s -f libwacomcfg.so.0.0.1 libwacomcfg.so || { rm -f libwacomcfg.so && ln -s libwacomcfg.so.0.0.1 libwacomcfg.so; }; })
/usr/bin/install -c .libs/libwacomcfg.lai /usr/lib/libwacomcfg.la
/usr/bin/install -c .libs/libwacomcfg.a /usr/lib/libwacomcfg.a
chmod 644 /usr/lib/libwacomcfg.a
ranlib /usr/lib/libwacomcfg.a
PATH="$PATH:/sbin" ldconfig -n /usr/lib
----------------------------------------------------------------------
Libraries have been installed in:
   /usr/lib

If you ever happen to want to link against installed libraries
in a given directory, LIBDIR, you must either use libtool, and
specify the full pathname of the library, or use the `-LLIBDIR'
flag during linking and do at least one of the following:
   - add LIBDIR to the `LD_LIBRARY_PATH' environment variable
     during execution
   - add LIBDIR to the `LD_RUN_PATH' environment variable
     during linking
   - use the `-Wl,--rpath -Wl,LIBDIR' linker flag
   - have your system administrator add LIBDIR to `/etc/ld.so.conf'

See any operating system documentation about shared libraries for
more information, such as the ld(1) and ld.so(8) manual pages.
----------------------------------------------------------------------
test -z "/usr/bin" || /bin/mkdir -p "/usr/bin"
  /bin/bash ../../libtool   --mode=install /usr/bin/install -c 'wacdump' '/usr/bin/wacdump'
/usr/bin/install -c wacdump /usr/bin/wacdump
  /bin/bash ../../libtool   --mode=install /usr/bin/install -c 'xidump' '/usr/bin/xidump'
/usr/bin/install -c xidump /usr/bin/xidump
  /bin/bash ../../libtool   --mode=install /usr/bin/install -c 'xsetwacom' '/usr/bin/xsetwacom'
/usr/bin/install -c .libs/xsetwacom /usr/bin/xsetwacom
test -z "/usr/libexec" || /bin/mkdir -p "/usr/libexec"
  /bin/bash ../../libtool   --mode=install /usr/bin/install -c 'hal-setup-wacom' '/usr/libexec/hal-setup-wacom'
/usr/bin/install -c hal-setup-wacom /usr/libexec/hal-setup-wacom
test -z "/usr/share/hal/fdi/policy/20thirdparty" || /bin/mkdir -p "/usr/share/hal/fdi/policy/20thirdparty"
 /usr/bin/install -c '10-linuxwacom.fdi' '/usr/share/hal/fdi/policy/20thirdparty/10-linuxwacom.fdi'
test -z "/usr/include/wacomcfg" || /bin/mkdir -p "/usr/include/wacomcfg"
 /usr/bin/install -c -m 644 'wacomcfg.h' '/usr/include/wacomcfg/wacomcfg.h'
make[3]: Leaving directory `/home/tj/lw-ntrig/linuxwacom-0.8.5-10/src/util'
make[2]: Leaving directory `/home/tj/lw-ntrig/linuxwacom-0.8.5-10/src/util'
Making install in xdrv
make[2]: Entering directory `/home/tj/lw-ntrig/linuxwacom-0.8.5-10/src/xdrv'
make[3]: Entering directory `/home/tj/lw-ntrig/linuxwacom-0.8.5-10/src/xdrv'
make[3]: Nothing to be done for `install-exec-am'.
test -z "/usr/lib/xorg/modules/input" || /bin/mkdir -p "/usr/lib/xorg/modules/input"
 /usr/bin/install -c -m 644 'wacom_drv.so' '/usr/lib/xorg/modules/input/wacom_drv.so'
make[3]: Leaving directory `/home/tj/lw-ntrig/linuxwacom-0.8.5-10/src/xdrv'
make[2]: Leaving directory `/home/tj/lw-ntrig/linuxwacom-0.8.5-10/src/xdrv'
Making install in 2.6.27
make[2]: Entering directory `/home/tj/lw-ntrig/linuxwacom-0.8.5-10/src/2.6.27'
make[2]: Nothing to be done for `install'.
make[2]: Leaving directory `/home/tj/lw-ntrig/linuxwacom-0.8.5-10/src/2.6.27'
make[1]: Leaving directory `/home/tj/lw-ntrig/linuxwacom-0.8.5-10/src'
make[1]: Entering directory `/home/tj/lw-ntrig/linuxwacom-0.8.5-10'
make[2]: Entering directory `/home/tj/lw-ntrig/linuxwacom-0.8.5-10'
make[2]: Nothing to be done for `install-exec-am'.
make[2]: Nothing to be done for `install-data-am'.
make[2]: Leaving directory `/home/tj/lw-ntrig/linuxwacom-0.8.5-10'
make[1]: Leaving directory `/home/tj/lw-ntrig/linuxwacom-0.8.5-10'
tj@xt2:~/lw-ntrig/linuxwacom-0.8.5-10$ 

```

---

### Post by Favux on 2010-02-21
You did it!

So you have the usb part, hid-trig.ko installed.  Although we haven't explained why multi-touch isn't showing up in your lshal.  It should with the 2-16-10 Rafi hid-ntri.ko and Win7 firmware, I think.

You've got the X driver part (linuxwacom), patched for ntrig, installed.

Almost there!  Now you just need the new udev rules and the new xorg.conf.

So start with 3) and 3)a on the [N-trig HOW TO]("http://ubuntuforums.org/showpost.php?p=7863677&postcount=1").

---

### Post by -TJ on 2010-02-21
Can't you just tell me what to do before I mess up? We're almost there, and I might ruin it.
There are many "1)"'s so how can I expect that I'm on the right "3)"? (its a matter of self confidence).

You combine explanations with directions. Some people don't understand the explanations because they are new to the entire thing! So if one part is not clear, the whole thing is unclear! I hope you understand...

---

### Post by Favux on 2010-02-21
Alright.

Open this file:
```
gksudo gedit /etc/udev/rules.d/90-n-trig.rules
```
It should be blank.  Copy and paste into it the entire following file and Save and close:
```
# udev rules for n-trig tablets.
#
# These rules were compiled for the Ubuntu/Debian GNU/Linux distribution, but others may,
# and indeed are encouraged to, use them also.
#
# Should you do so, PLEASE CO-ORDINATE ANY CHANGES OR ADDITIONS of new devices with ????
# so that we can try to present users with a standard set of device nodes which they can
# rely on across the board.

KERNEL!="event[0-9]*", GOTO="n-trig_end"

# To mirror linuxwacom, we keep the input/n-trig link as the generic stylus device.
ATTRS{name}=="N-Trig Touchscreen", SUBSYSTEM=="input", ENV{x11_driver}="wacom", SYMLINK+="input/n-trig-touch"
ATTRS{name}=="N-Trig MultiTouch", SUBSYSTEM=="input", ENV{x11_driver}="wacom", SYMLINK+="input/n-trig-mttouch"
ATTRS{name}=="N-Trig Pen", SUBSYSTEM=="input", ENV{x11_driver}="wacom", SYMLINK+="input/n-trig"

# Check and repossess the device if a module other than the n-trig one is already bound
# to it.
ATTRS{idVendor}=="1b96", ACTION=="add", RUN+="check_driver ntrig $devpath $env{ID_BUS}"

LABEL="n-trig_end"
```
Then open this file:
```
gksudo gedit /lib/udev/check_driver
```
If it has the contents below you're done with it.  If it is blank copy and paste the entire contents of the following file into it Save and close:
```
#!/bin/sh
#

#logger check_driver called with: $1 - $2 - $3 -

wanted=$1
devpath=$2
bustype=$3

device=$(readlink /sys/$devpath/device)
device=${device##*/}
driver=$(readlink /sys/$devpath/device/driver)
driver=${driver##*/}

logger device $device is bound to the $driver driver

if [ "$driver" != "$wanted" ]; then
    logger must rebind
    echo -n "$device" > /sys/$devpath/device/driver/unbind
    echo -n "$device" > /sys/bus/$bustype/drivers/$wanted/bind
else
    logger no need to rebind
fi
```
Then in a terminal do this:
```
sudo chmod +x /lib/udev/check_driver
```
Finally we want to see what is in your xorg.conf.  You can navigate to it and look or use:
```
gedit /etc/X11/xorg.conf
```
If it is there copy its entire contents and post on your next post.

---

### Post by -TJ on 2010-02-21
Here is the content:
```
# xorg.conf (X.Org X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the xorg.conf manual page.
# (Type "man xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# Note that some configuration settings that could be done previously
# in this file, now are automatically configured by the server and settings
# here are ignored.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

# Setup for the Dell XT2 in Karmic.

Section "InputDevice"
	Identifier	"stylus"
	Driver		"wacom"
#   The by-path below is for the Dell Latitude XT2 with Vista firmware
#	Option "Device" "/dev/input/by-path/pci-0000:00:1d.1-usb-0:2:1.0-event-mouse"
#   The by-path below is for the Dell Latitude XT2 with Win7 firmware
	Option "Device" "/dev/input/by-path/pci-0000:00:1d.1-usb-0:2:1.1-event-mouse"
	Option		"Type"		"stylus"
	Option		"USB"		"on"
	Option		"Button2"	"3"	# make stylus button R mouse click
EndSection

#   Remove the comments below if you have an eraser.  Dell XT & XT2?
#Section "InputDevice"
#	Identifier	"eraser"
#	Driver		"wacom"
#   The by-path below is for the Dell Latitude XT2 with Vista firmware
#	Option "Device" "/dev/input/by-path/pci-0000:00:1d.1-usb-0:2:1.0-event-mouse"
#   The by-path below is for the Dell Latitude XT2 with Win7 firmware
#	Option "Device" "/dev/input/by-path/pci-0000:00:1d.1-usb-0:2:1.1-event-mouse"
#	Option		"Type"		"eraser"
#	Option		"USB"		"on"
#EndSection

Section "InputDevice"
	Identifier	"touch"
	Driver		"wacom"
#   The by-path below is for the Dell Latitude XT2 with Vista firmware
#	Option "Device" "/dev/input/by-path/pci-0000:00:1d.1-usb-0:2:1.0-event-mouse"
#   The by-path below is for the Dell Latitude XT2 with Win7 firmware
	Option "Device" "/dev/input/by-path/pci-0000:00:1d.1-usb-0:2:1.1-event-mouse"
	Option		"Type"		"touch"
	Option		"USB"		"on"
	Option		"Touch"		"on"
	Option		"TopX"		"0"
	Option		"TopY"		"0"
	Option		"BottomX"	"9600"
	Option		"BottomY"	"7200"
EndSection

Section "ServerLayout"
	Identifier	"X.org Configured"
	InputDevice	"stylus"		"SendCoreEvents"
#   Remove the comment below if you have an eraser.
#	InputDevice	"eraser"	#	"SendCoreEvents"
	InputDevice	"touch"			"SendCoreEvents"
EndSection

#   Developed with Ayuthia (using Rafi Rubin's Wacom sections as a starting point).
```

---

### Post by Favux on 2010-02-21
Make a back up of your current working xorg.conf in case you have to reinstall it from the command line.  You remember what happened before!

Then open your xorg.conf with the following command:
```
gksudo gedit /etc/X11/xorg.conf
```
and replace the entire contents of it with the contents of the downloaded xorg.conf attached below.  Save, close and reboot.

Good luck!

---

### Post by -TJ on 2010-02-22
Okay rebooting. In the meanwhile, go on.

---

### Post by Favux on 2010-02-22
Oh, sorry, that should be it.  We'd be done if it works.

It would be good to look at the output of:
```
xinput --list
```

---

### Post by -TJ on 2010-02-22
Here it is:
```
tj@xt2:~$ xinput --list
"Virtual core pointer"	id=0	[XPointer]
	Num_buttons is 32
	Num_axes is 2
	Mode is Relative
	Motion_buffer is 256
	Axis 0 :
		Min_value is -1
		Max_value is -1
		Resolution is 0
	Axis 1 :
		Min_value is -1
		Max_value is -1
		Resolution is 0
"Virtual core keyboard"	id=1	[XKeyboard]
	Num_keys is 248
	Min_keycode is 8
	Max_keycode is 255
"Sleep Button"	id=2	[XExtensionKeyboard]
	Type is KEYBOARD
	Num_keys is 248
	Min_keycode is 8
	Max_keycode is 255
"Dell WMI hotkeys"	id=3	[XExtensionKeyboard]
	Type is KEYBOARD
	Num_keys is 248
	Min_keycode is 8
	Max_keycode is 255
"Video Bus"	id=4	[XExtensionKeyboard]
	Type is KEYBOARD
	Num_keys is 248
	Min_keycode is 8
	Max_keycode is 255
"Video Bus"	id=5	[XExtensionKeyboard]
	Type is KEYBOARD
	Num_keys is 248
	Min_keycode is 8
	Max_keycode is 255
"AT Translated Set 2 keyboard"	id=6	[XExtensionKeyboard]
	Type is KEYBOARD
	Num_keys is 248
	Min_keycode is 8
	Max_keycode is 255
"HID 413c:8161"	id=7	[XExtensionKeyboard]
	Type is KEYBOARD
	Num_keys is 248
	Min_keycode is 8
	Max_keycode is 255
"Power Button"	id=8	[XExtensionKeyboard]
	Type is KEYBOARD
	Num_keys is 248
	Min_keycode is 8
	Max_keycode is 255
"PS/2 Generic Mouse"	id=9	[XExtensionPointer]
	Type is MOUSE
	Num_buttons is 5
	Num_axes is 2
	Mode is Relative
	Motion_buffer is 256
	Axis 0 :
		Min_value is -1
		Max_value is -1
		Resolution is 1
	Axis 1 :
		Min_value is -1
		Max_value is -1
		Resolution is 1
"Macintosh mouse button emulation"	id=10	[XExtensionPointer]
	Type is MOUSE
	Num_buttons is 5
	Num_axes is 2
	Mode is Relative
	Motion_buffer is 256
	Axis 0 :
		Min_value is -1
		Max_value is -1
		Resolution is 1
	Axis 1 :
		Min_value is -1
		Max_value is -1
		Resolution is 1
"HID 1b96:0001"	id=11	[XExtensionPointer]
	Type is TOUCHPAD
	Num_buttons is 5
	Num_axes is 8
	Mode is Absolute
	Motion_buffer is 256
	Axis 0 :
		Min_value is 0
		Max_value is 9600
		Resolution is 10000
	Axis 1 :
		Min_value is 0
		Max_value is 7200
		Resolution is 10000
	Axis 2 :
		Min_value is 0
		Max_value is 256
		Resolution is 10000
	Axis 3 :
		Min_value is 0
		Max_value is 1
		Resolution is 10000
	Axis 4 :
		Min_value is 0
		Max_value is 1
		Resolution is 10000
	Axis 5 :
		Min_value is 0
		Max_value is 1
		Resolution is 10000
	Axis 6 :
		Min_value is 0
		Max_value is 9600
		Resolution is 10000
	Axis 7 :
		Min_value is 0
		Max_value is 7200
		Resolution is 10000
"HID 1b96:0001"	id=12	[XExtensionPointer]
	Type is TOUCHPAD
	Num_buttons is 5
	Num_axes is 8
	Mode is Absolute
	Motion_buffer is 256
	Axis 0 :
		Min_value is 0
		Max_value is 9600
		Resolution is 10000
	Axis 1 :
		Min_value is 0
		Max_value is 7200
		Resolution is 10000
	Axis 2 :
		Min_value is 0
		Max_value is 256
		Resolution is 10000
	Axis 3 :
		Min_value is 0
		Max_value is 1
		Resolution is 10000
	Axis 4 :
		Min_value is 0
		Max_value is 1
		Resolution is 10000
	Axis 5 :
		Min_value is 0
		Max_value is 1
		Resolution is 10000
	Axis 6 :
		Min_value is 0
		Max_value is 9600
		Resolution is 10000
	Axis 7 :
		Min_value is 0
		Max_value is 7200
		Resolution is 10000

```

---

### Post by Favux on 2010-02-22
It looks like it isn't working.  Are you sure you have the new xorg.conf installed?  Also check:
```
dmesg | grep ntrig
```

If both are ok we need to look at lshal and Xorg.0.log again.

---

### Post by -TJ on 2010-02-22
Here it is again:

```
tj@xt2:~$ dmesg | grep ntrig
[    4.055962] ntrig 0003:1B96:0001.0001: input,hiddev96,hidraw2: USB HID v1.10 Device [HID 1b96:0001] on usb-0000:00:1d.1-2/input0
[    4.072931] ntrig 0003:1B96:0001.0002: input,hiddev97,hidraw3: USB HID v1.10 Device [HID 1b96:0001] on usb-0000:00:1d.1-2/input1

```

Just to tell you, when I use my stylus, everything is shifted. My pointer is not in the correct location. And on top of that, touch is not working. Neither is multi-touch working.


EDIT:
Here is lshal:

```
tj@xt2:~$ cd
tj@xt2:~$ gedit lshal.py
tj@xt2:~$ python lshal.py
udi = '/org/freedesktop/Hal/devices/usb_device_1b96_1_noserial_if1_logicaldev_input'
  info.capabilities = {'input', 'input.tablet'} (string list)
  info.category = 'input'  (string)
  info.parent = '/org/freedesktop/Hal/devices/usb_device_1b96_1_noserial_if1'  (string)
  info.product = 'HID 1b96:0001'  (string)
  info.subsystem = 'input'  (string)
  info.udi = '/org/freedesktop/Hal/devices/usb_device_1b96_1_noserial_if1_logicaldev_input'  (string)
  input.device = '/dev/input/event10'  (string)
  input.originating_device = '/org/freedesktop/Hal/devices/usb_device_1b96_1_noserial_if1'  (string)
  input.product = 'HID 1b96:0001'  (string)
  input.x11_driver = 'evdev'  (string)
  linux.device_file = '/dev/input/event10'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'input'  (string)
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:1d.1/usb7/7-2/7-2:1.1/input/input10/event10'  (string)

udi = '/org/freedesktop/Hal/devices/usb_device_1b96_1_noserial_if0_logicaldev_input'
  info.capabilities = {'input', 'input.tablet'} (string list)
  info.category = 'input'  (string)
  info.parent = '/org/freedesktop/Hal/devices/usb_device_1b96_1_noserial_if0'  (string)
  info.product = 'HID 1b96:0001'  (string)
  info.subsystem = 'input'  (string)
  info.udi = '/org/freedesktop/Hal/devices/usb_device_1b96_1_noserial_if0_logicaldev_input'  (string)
  input.device = '/dev/input/event9'  (string)
  input.originating_device = '/org/freedesktop/Hal/devices/usb_device_1b96_1_noserial_if0'  (string)
  input.product = 'HID 1b96:0001'  (string)
  input.x11_driver = 'evdev'  (string)
  linux.device_file = '/dev/input/event9'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'input'  (string)
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:1d.1/usb7/7-2/7-2:1.0/input/input9/event9'  (string)

tj@xt2:~$ 

```

---

### Post by Favux on 2010-02-22
Ok, while you're getting the other stuff together I came up with another xorg.conf to try.

---

### Post by -TJ on 2010-02-22
Here is the Xorg.log that you wanted too:

---

### Post by -TJ on 2010-02-22
Just to tell you, the "linuxwacom-0.8.5-10" folder is located on my desktop for some reason when I was compiling what Ayuthia told me to do.

Okay I am now rebooting: continue on with your directions.

EDIT:
The pointer is still not in the correct location and when I tap with the stylus, it doesn't click anything. But there is touch! There is no multi-touch, though. THERE IS TOUCH!!!! FINALLY! FIRST TIME!

---

### Post by Favux on 2010-02-22
From the Xorg.0.log it sounds like your udev rules for the symlinks aren't there.  Check on them.  Make sure the file 90-n-trig.rules is at /etc/udev/rules.d/ and has the udev rules I posted in it.

---

### Post by -TJ on 2010-02-22
Did you hear that? Touch is working! But the pointer is not in the right locations...

EDIT: And the pointer goes crazy when I move it around. It flies everywhere around the screen.

---

### Post by -TJ on 2010-02-22
That file has the following:
```
# udev rules for n-trig tablets.
#
# These rules were compiled for the Ubuntu/Debian GNU/Linux distribution, but others may,
# and indeed are encouraged to, use them also.
#
# Should you do so, PLEASE CO-ORDINATE ANY CHANGES OR ADDITIONS of new devices with ????
# so that we can try to present users with a standard set of device nodes which they can
# rely on across the board.

KERNEL!="event[0-9]*", GOTO="n-trig_end"

# To mirror linuxwacom, we keep the input/n-trig link as the generic stylus device.
ATTRS{name}=="N-Trig Touchscreen", SUBSYSTEM=="input", ENV{x11_driver}="wacom", SYMLINK+="input/n-trig-touch"
ATTRS{name}=="N-Trig MultiTouch", SUBSYSTEM=="input", ENV{x11_driver}="wacom", SYMLINK+="input/n-trig-mttouch"
ATTRS{name}=="N-Trig Pen", SUBSYSTEM=="input", ENV{x11_driver}="wacom", SYMLINK+="input/n-trig"

# Check and repossess the device if a module other than the n-trig one is already bound
# to it.
ATTRS{idVendor}=="1b96", ACTION=="add", RUN+="check_driver ntrig $devpath $env{ID_BUS}"

LABEL="n-trig_end"
```

---

### Post by Favux on 2010-02-22
But touch is working because the evdev drivers have your digitizer.  Not linuxwacom.  Which is why the stylus doesn't work right.

Since your lshal didn't show "input/n-trig-mttouch" let see if it is what is breaking things.  Comment out this line:
```
ATTRS{name}=="N-Trig MultiTouch", SUBSYSTEM=="input", ENV{x11_driver}="wacom", SYMLINK+="input/n-trig-mttouch"

```
so it looks like:
```
#ATTRS{name}=="N-Trig MultiTouch", SUBSYSTEM=="input", ENV{x11_driver}="wacom", SYMLINK+="input/n-trig-mttouch"

```
And use the second xorg.conf I posted where mttouch is commented out.  Then reboot.

---

### Post by -TJ on 2010-02-22
Can you attach that Xorg.conf so that I won't accidentally use the wrong one?

---

### Post by Favux on 2010-02-22
That's why I label them.  It's the test2 in post #102.  And you'll see the mttouch stuff commented out.  After reboot let's look at "input --list" again.  But you'll know if it is working because stylus and touch will be working.

---

### Post by -TJ on 2010-02-22
The stylus is working, just not properly. Same for touch.

```
tj@xt2:~$ input --list
The program 'input' is currently not installed.  You can install it by typing:
sudo apt-get install yagiuda
input: command not found

```

```
tj@xt2:~$ sudo apt-get install yagiuda
[sudo] password for tj: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  ddccontrol libddccontrol0 python-reportlab libqt4-test ddccontrol-db
  python-renderpm libqt4-xmlpatterns libqt4-help python-qt4 python-sip4
  python-qt4-dbus libqt4-scripttools python-reportlab-accel
Use 'apt-get autoremove' to remove them.
The following NEW packages will be installed:
  yagiuda
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 109kB of archives.
After this operation, 385kB of additional disk space will be used.
Get:1 http://us.archive.ubuntu.com karmic/universe yagiuda 1.19-5 [109kB]
Fetched 109kB in 0s (118kB/s)  
Selecting previously deselected package yagiuda.
(Reading database ... 285452 files and directories currently installed.)
Unpacking yagiuda (from .../yagiuda_1.19-5_amd64.deb) ...
Processing triggers for man-db ...
Setting up yagiuda (1.19-5) ...
tj@xt2:~$ input --list
input: illegal option -- -
input: illegal option -- l
input: illegal option -- i
input: illegal option -- s
input: illegal option -- t

Yagi-Uda antenna analysis programs, version 1.19
Written by David Kirkby BSc MSc G8WRB (email:david.kirkby@onetel.net)

USAGE: input  [-h] 

Where the only option is:
   -h     Print this help screen


'input' is an interactive program, that asks the user for formation  about  
a  Yagi  design,  such as position of elements, spacing between elements,
frequency span of interest and a  filename to  save the data to. It then 
writes this information into an ASCII file, which can be read by 'yagi' or 
'optimise'. The file is  ASCII  and  it's format  is  easily  understood
by inspection (there are comments printed in it), so it can if necessary
be edited manually. After running 'input' and specifying a filename 
(for example 144e10) you should then type 'yagi 144e10' then 'output 144e10'
and then and optionally 'optimise 144e10'.
tj@xt2:~$ 

```

---

### Post by Favux on 2010-02-22
Maybe progress?

That was a typo use "xinput --list".

---

### Post by -TJ on 2010-02-22
Here it is:

```
tj@xt2:~$ xinput --list
"Virtual core pointer"	id=0	[XPointer]
	Num_buttons is 32
	Num_axes is 2
	Mode is Relative
	Motion_buffer is 256
	Axis 0 :
		Min_value is -1
		Max_value is -1
		Resolution is 0
	Axis 1 :
		Min_value is -1
		Max_value is -1
		Resolution is 0
"Virtual core keyboard"	id=1	[XKeyboard]
	Num_keys is 248
	Min_keycode is 8
	Max_keycode is 255
"Dell WMI hotkeys"	id=2	[XExtensionKeyboard]
	Type is KEYBOARD
	Num_keys is 248
	Min_keycode is 8
	Max_keycode is 255
"AT Translated Set 2 keyboard"	id=3	[XExtensionKeyboard]
	Type is KEYBOARD
	Num_keys is 248
	Min_keycode is 8
	Max_keycode is 255
"Video Bus"	id=4	[XExtensionKeyboard]
	Type is KEYBOARD
	Num_keys is 248
	Min_keycode is 8
	Max_keycode is 255
"HID 413c:8161"	id=5	[XExtensionKeyboard]
	Type is KEYBOARD
	Num_keys is 248
	Min_keycode is 8
	Max_keycode is 255
"Sleep Button"	id=6	[XExtensionKeyboard]
	Type is KEYBOARD
	Num_keys is 248
	Min_keycode is 8
	Max_keycode is 255
"Power Button"	id=7	[XExtensionKeyboard]
	Type is KEYBOARD
	Num_keys is 248
	Min_keycode is 8
	Max_keycode is 255
"Video Bus"	id=8	[XExtensionKeyboard]
	Type is KEYBOARD
	Num_keys is 248
	Min_keycode is 8
	Max_keycode is 255
"PS/2 Generic Mouse"	id=9	[XExtensionPointer]
	Type is MOUSE
	Num_buttons is 5
	Num_axes is 2
	Mode is Relative
	Motion_buffer is 256
	Axis 0 :
		Min_value is -1
		Max_value is -1
		Resolution is 1
	Axis 1 :
		Min_value is -1
		Max_value is -1
		Resolution is 1
"Macintosh mouse button emulation"	id=10	[XExtensionPointer]
	Type is MOUSE
	Num_buttons is 5
	Num_axes is 2
	Mode is Relative
	Motion_buffer is 256
	Axis 0 :
		Min_value is -1
		Max_value is -1
		Resolution is 1
	Axis 1 :
		Min_value is -1
		Max_value is -1
		Resolution is 1
"HID 1b96:0001"	id=11	[XExtensionPointer]
	Type is TOUCHPAD
	Num_buttons is 5
	Num_axes is 8
	Mode is Absolute
	Motion_buffer is 256
	Axis 0 :
		Min_value is 0
		Max_value is 9600
		Resolution is 10000
	Axis 1 :
		Min_value is 0
		Max_value is 7200
		Resolution is 10000
	Axis 2 :
		Min_value is 0
		Max_value is 256
		Resolution is 10000
	Axis 3 :
		Min_value is 0
		Max_value is 1
		Resolution is 10000
	Axis 4 :
		Min_value is 0
		Max_value is 1
		Resolution is 10000
	Axis 5 :
		Min_value is 0
		Max_value is 1
		Resolution is 10000
	Axis 6 :
		Min_value is 0
		Max_value is 9600
		Resolution is 10000
	Axis 7 :
		Min_value is 0
		Max_value is 7200
		Resolution is 10000
"HID 1b96:0001"	id=12	[XExtensionPointer]
	Type is TOUCHPAD
	Num_buttons is 5
	Num_axes is 8
	Mode is Absolute
	Motion_buffer is 256
	Axis 0 :
		Min_value is 0
		Max_value is 9600
		Resolution is 10000
	Axis 1 :
		Min_value is 0
		Max_value is 7200
		Resolution is 10000
	Axis 2 :
		Min_value is 0
		Max_value is 256
		Resolution is 10000
	Axis 3 :
		Min_value is 0
		Max_value is 1
		Resolution is 10000
	Axis 4 :
		Min_value is 0
		Max_value is 1
		Resolution is 10000
	Axis 5 :
		Min_value is 0
		Max_value is 1
		Resolution is 10000
	Axis 6 :
		Min_value is 0
		Max_value is 9600
		Resolution is 10000
	Axis 7 :
		Min_value is 0
		Max_value is 7200
		Resolution is 10000

```

---

### Post by Favux on 2010-02-22
Still evdev probably.  See?:
```
"HID 1b96:0001"	id=11	[XExtensionPointer]
	Type is TOUCHPAD

```
It would have [XExtensionKeyboard] if it was wacom and say stylus or touch not TOUCHPAD.

I need to see Xorg.0.log and lshal again.

Absent that what is going on?  I'm not sure.  Do you actually maybe have Vista firmware?  Because we're sure you installed Rafi's new hid-ntrig.ko from 2-16-10.

If so you would change the contents of 90-n-trig.rules to:
```
# udev rules for n-trig tablets (hid-ntrig.ko earlier than 2-5-10 i.e. multiplexed).
#
# These rules were compiled for the Ubuntu/Debian GNU/Linux distribution, but others may,
# and indeed are encouraged to, use them also.
#
# Should you do so, PLEASE CO-ORDINATE ANY CHANGES OR ADDITIONS of new devices with ????
# so that we can try to present users with a standard set of device nodes which they can
# rely on across the board.

# To mirror linuxwacom, we keep the input/n-trig link as the generic stylus device.
KERNEL=="event*", ATTRS{idVendor}=="1b96", ATTRS{idProduct}=="0001", ENV{x11_driver}="wacom", SYMLINK="input/n-trig"

# Check and repossess the device if a module other than the n-trig one is already bound
# to it.
ATTRS{idVendor}=="1b96", ACTION=="add", RUN+="check_driver ntrig $devpath $env{ID_BUS}"
```
and try the test3 xorg.conf attached.

But let's wait till we look at those files.

---

### Post by Favux on 2010-02-22
Oops, forgot to attach the test3 xorg.conf.

---

### Post by -TJ on 2010-02-22
Here is lshal:

```
tj@xt2:~$ python lshal.py
udi = '/org/freedesktop/Hal/devices/usb_device_1b96_1_noserial_if1_logicaldev_input'
  info.capabilities = {'input', 'input.tablet'} (string list)
  info.category = 'input'  (string)
  info.parent = '/org/freedesktop/Hal/devices/usb_device_1b96_1_noserial_if1'  (string)
  info.product = 'HID 1b96:0001'  (string)
  info.subsystem = 'input'  (string)
  info.udi = '/org/freedesktop/Hal/devices/usb_device_1b96_1_noserial_if1_logicaldev_input'  (string)
  input.device = '/dev/input/event11'  (string)
  input.originating_device = '/org/freedesktop/Hal/devices/usb_device_1b96_1_noserial_if1'  (string)
  input.product = 'HID 1b96:0001'  (string)
  input.x11_driver = 'evdev'  (string)
  linux.device_file = '/dev/input/event11'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'input'  (string)
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:1d.1/usb7/7-2/7-2:1.1/input/input11/event11'  (string)

udi = '/org/freedesktop/Hal/devices/usb_device_1b96_1_noserial_if0_logicaldev_input'
  info.capabilities = {'input', 'input.tablet'} (string list)
  info.category = 'input'  (string)
  info.parent = '/org/freedesktop/Hal/devices/usb_device_1b96_1_noserial_if0'  (string)
  info.product = 'HID 1b96:0001'  (string)
  info.subsystem = 'input'  (string)
  info.udi = '/org/freedesktop/Hal/devices/usb_device_1b96_1_noserial_if0_logicaldev_input'  (string)
  input.device = '/dev/input/event10'  (string)
  input.originating_device = '/org/freedesktop/Hal/devices/usb_device_1b96_1_noserial_if0'  (string)
  input.product = 'HID 1b96:0001'  (string)
  input.x11_driver = 'evdev'  (string)
  linux.device_file = '/dev/input/event10'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'input'  (string)
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:1d.1/usb7/7-2/7-2:1.0/input/input10/event10'  (string)


```

The Xorg.0.log is attached.
I also did the 90-n-trig.rules to whatever you told me to do.

EDIT: I also did the xorg.conf thing.

---

### Post by Favux on 2010-02-22
Hmmm.  Same problem in that Xorg.0.log.  New thoughts on it.  Try the test3 xorg.conf with the last udev rules I posted.

Edit:  What results?  "xinput --list"?

---

### Post by -TJ on 2010-02-22
What are the udev rules again?
Here is xinput --list:

EDIT: let me reboot

---

### Post by Favux on 2010-02-22
The latest ones are in post #114 above.  They are at "/etc/udev/rules.d/90-n-trig.rules" so use:
```
gksudo gedit /etc/udev/rules.d/90-n-trig.rules
```

---

### Post by -TJ on 2010-02-22
Here is xinput --list:
```
tj@xt2:~$ xinput --list
"Virtual core pointer"	id=0	[XPointer]
	Num_buttons is 32
	Num_axes is 2
	Mode is Relative
	Motion_buffer is 256
	Axis 0 :
		Min_value is -1
		Max_value is -1
		Resolution is 0
	Axis 1 :
		Min_value is -1
		Max_value is -1
		Resolution is 0
"Virtual core keyboard"	id=1	[XKeyboard]
	Num_keys is 248
	Min_keycode is 8
	Max_keycode is 255
"AT Translated Set 2 keyboard"	id=2	[XExtensionKeyboard]
	Type is KEYBOARD
	Num_keys is 248
	Min_keycode is 8
	Max_keycode is 255
"Dell WMI hotkeys"	id=3	[XExtensionKeyboard]
	Type is KEYBOARD
	Num_keys is 248
	Min_keycode is 8
	Max_keycode is 255
"HID 413c:8161"	id=4	[XExtensionKeyboard]
	Type is KEYBOARD
	Num_keys is 248
	Min_keycode is 8
	Max_keycode is 255
"Sleep Button"	id=5	[XExtensionKeyboard]
	Type is KEYBOARD
	Num_keys is 248
	Min_keycode is 8
	Max_keycode is 255
"Power Button"	id=6	[XExtensionKeyboard]
	Type is KEYBOARD
	Num_keys is 248
	Min_keycode is 8
	Max_keycode is 255
"Video Bus"	id=7	[XExtensionKeyboard]
	Type is KEYBOARD
	Num_keys is 248
	Min_keycode is 8
	Max_keycode is 255
"Video Bus"	id=8	[XExtensionKeyboard]
	Type is KEYBOARD
	Num_keys is 248
	Min_keycode is 8
	Max_keycode is 255
"PS/2 Generic Mouse"	id=9	[XExtensionPointer]
	Type is MOUSE
	Num_buttons is 5
	Num_axes is 2
	Mode is Relative
	Motion_buffer is 256
	Axis 0 :
		Min_value is -1
		Max_value is -1
		Resolution is 1
	Axis 1 :
		Min_value is -1
		Max_value is -1
		Resolution is 1
"Macintosh mouse button emulation"	id=10	[XExtensionPointer]
	Type is MOUSE
	Num_buttons is 5
	Num_axes is 2
	Mode is Relative
	Motion_buffer is 256
	Axis 0 :
		Min_value is -1
		Max_value is -1
		Resolution is 1
	Axis 1 :
		Min_value is -1
		Max_value is -1
		Resolution is 1
tj@xt2:~$ 

```

---

### Post by -TJ on 2010-02-22
I already replaced the contents of the file with the ones you wanted. What is the next direction?

EDIT: Nothing is working anymore; neither pen, touch, nor multi-touch.

---

### Post by Favux on 2010-02-22
Oops!  Your N-trig digitizer disappeared!

Check on the udev rules file, the 'check_driver' file, and the xorg.conf please.

---

### Post by -TJ on 2010-02-22
What is the "udev rules file"? Is that the one that is named 90-n-trig rules file? I already copied and pasted the stuff you told me to copy and paste.

For the check_driver file, here it is:

```
#!/bin/sh
#

#logger check_driver called with: $1 - $2 - $3 -

wanted=$1
devpath=$2
bustype=$3

device=$(readlink /sys/$devpath/device)
device=${device##*/}
driver=$(readlink /sys/$devpath/device/driver)
driver=${driver##*/}

logger device $device is bound to the $driver driver

if [ "$driver" != "$wanted" ]; then
    logger must rebind
    echo -n "$device" > /sys/$devpath/device/driver/unbind
    echo -n "$device" > /sys/bus/$bustype/drivers/$wanted/bind
else
    logger no need to rebind
fi

```

Here is the xorg.conf file:
```
# xorg.conf (X.Org X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the xorg.conf manual page.
# (Type "man xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# Note that some configuration settings that could be done previously
# in this file, now are automatically configured by the server and settings
# here are ignored.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

# Setup for the Dell XT2 in Karmic.

Section "InputDevice"
	Identifier	"stylus"
	Driver		"wacom"
	Option		"Device"	"/dev/input/n-trig"
	Option		"Type"		"stylus"
	Option		"USB"		"on"
	Option		"Button2"	"3"	# make stylus button R mouse click
	Option		"TopX"		"0"
	Option		"TopY"		"0"
	Option		"BottomX"	"9600"
	Option		"BottomY"	"7200"
EndSection

#   Remove the comments below if you have an eraser.  Dell XT & XT2?
#Section "InputDevice"
#	Identifier	"eraser"
#	Driver		"wacom"
#	Option		"Device"	"/dev/input/n-trig"
#	Option		"Type"		"eraser"
#	Option		"USB"		"on"
#EndSection

Section "InputDevice"
	Identifier	"touch"
	Driver		"wacom"
	Option		"Device"	"/dev/input/n-trig"
	Option		"Type"		"touch"
	Option		"USB"		"on"
	Option		"TopX"		"0"
	Option		"TopY"		"0"
	Option		"BottomX"	"9600"
	Option		"BottomY"	"7200"
EndSection

Section "ServerLayout"
	Identifier	"X.org Configured"
	InputDevice	"stylus"	"SendCoreEvents"
#   Remove the comment below if you have an eraser.
#	InputDevice	"eraser"	#"SendCoreEvents"
	InputDevice	"touch"		"SendCoreEvents"
EndSection

#   Developed with Ayuthia (using Rafi Rubin's Wacom sections as a starting point).

```

EDIT: Won't it be easier if you just controlled my computer using Remote Desktop?

---

### Post by Favux on 2010-02-22
Sure but I'm not set up for it.

I want you to go to check_driver with Places/Nautilus and right click on it and choose Properties.  Then go to the Permissions tab and see if the box in front of "Allow executing file as program" is checked.

---

### Post by -TJ on 2010-02-22
We will continue this tomorrow. Goodnight.

---

### Post by Favux on 2010-02-22
OK.  Good night.

I think you can go back to the test2 xorg.conf.

1) The udev rules are not the problem.  You can go back to the original one we installed (the same one as on the N-trig HOW TO).

2) I think your firmware, whatever it is, allows stylus and touch to be separated.  But it doesn't let touch be separated into touch and mttouch.

It was important and useful to establish that Rafi's new 2-16-10 hid-ntig.ko handles that firmware appropriately and so do the new udev rules.  Thank you.


Now we need to establish why linuxwacom 0.8.5-10 isn't accepting n-trig.  If check_driver is executable  that may be because we don't have check_driver in the right place.  Which would mean evdev is grabbing it, which in turn is why linuxwacom doesn't see it.  So do the same thing to install it as before but change the location.  Since you have a 64-bit system open the file in lib64 directory (instead of the lib directory) using:
```
gksudo gedit /lib64/udev/check_driver
```
Then install the contents:
```
#!/bin/sh
#

#logger check_driver called with: $1 - $2 - $3 -

wanted=$1
devpath=$2
bustype=$3

device=$(readlink /sys/$devpath/device)
device=${device##*/}
driver=$(readlink /sys/$devpath/device/driver)
driver=${driver##*/}

logger device $device is bound to the $driver driver

if [ "$driver" != "$wanted" ]; then
    logger must rebind
    echo -n "$device" > /sys/$devpath/device/driver/unbind
    echo -n "$device" > /sys/bus/$bustype/drivers/$wanted/bind
else
    logger no need to rebind
fi
```
Then make the new check_driver file in the new location executable by:
```
sudo chmod +x /lib64/udev/check_driver
```
then reboot.

Wouldn't it be nice if this fixes it?

---

### Post by Ayuthia on 2010-02-22
> **-TJ said:**
> Here is lshal:

```
tj@xt2:~$ python lshal.py
udi = '/org/freedesktop/Hal/devices/usb_device_1b96_1_noserial_if1_logicaldev_input'
  info.capabilities = {'input', 'input.tablet'} (string list)
  info.category = 'input'  (string)
  info.parent = '/org/freedesktop/Hal/devices/usb_device_1b96_1_noserial_if1'  (string)
  info.product = 'HID 1b96:0001'  (string)
  info.subsystem = 'input'  (string)
  info.udi = '/org/freedesktop/Hal/devices/usb_device_1b96_1_noserial_if1_logicaldev_input'  (string)
  input.device = '/dev/input/event11'  (string)
  input.originating_device = '/org/freedesktop/Hal/devices/usb_device_1b96_1_noserial_if1'  (string)
  input.product = 'HID 1b96:0001'  (string)
  input.x11_driver = 'evdev'  (string)
  linux.device_file = '/dev/input/event11'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'input'  (string)
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:1d.1/usb7/7-2/7-2:1.1/input/input11/event11'  (string)

udi = '/org/freedesktop/Hal/devices/usb_device_1b96_1_noserial_if0_logicaldev_input'
  info.capabilities = {'input', 'input.tablet'} (string list)
  info.category = 'input'  (string)
  info.parent = '/org/freedesktop/Hal/devices/usb_device_1b96_1_noserial_if0'  (string)
  info.product = 'HID 1b96:0001'  (string)
  info.subsystem = 'input'  (string)
  info.udi = '/org/freedesktop/Hal/devices/usb_device_1b96_1_noserial_if0_logicaldev_input'  (string)
  input.device = '/dev/input/event10'  (string)
  input.originating_device = '/org/freedesktop/Hal/devices/usb_device_1b96_1_noserial_if0'  (string)
  input.product = 'HID 1b96:0001'  (string)
  input.x11_driver = 'evdev'  (string)
  linux.device_file = '/dev/input/event10'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'input'  (string)
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:1d.1/usb7/7-2/7-2:1.0/input/input10/event10'  (string)


```

The Xorg.0.log is attached.
I also did the 90-n-trig.rules to whatever you told me to do.

EDIT: I also did the xorg.conf thing.

Based on the information here, it looks like you are not using Rafi's version of the kernel module.  The one that I provided gave you the N-Trig Touchscreen message in lshal.py (the one that you are using is showing 'HID 1b96:0001').  That is the one that you should be using.  From what I can tell, it looks like your system has reverted to the single-touch mode otherwise the N-Trig MultiTouch would have shown up.

The easiest way to see if you are using the same one as the one I provided is to do the following:
```
md5sum /lib/modules/$(uname -r)/kernel/drivers/hid/hid-ntrig.ko
```
The value should be 3ece350093dd8f669bfa598fa51b2205

---

### Post by -TJ on 2010-02-22
Here it is:
```
tj@xt2:~$ md5sum /lib/modules/$(uname -r)/kernel/drivers/hid/hid-ntrig.ko
80965d99268b7bc667f48a92750ea3c3  /lib/modules/2.6.31-20-generic/kernel/drivers/hid/hid-ntrig.ko

```
There seems to be something totally flawed. =/

---

### Post by Ayuthia on 2010-02-22
There must have been an update to the kernel.  The one that I built should be the most recent version so it should work with yours.  I would download the file again and reinstall it:
```

cd
wget http://linuxfans.keryxproject.org/packages/ntrig/rafi/64bit/20100216/2.6.31-20-generic/hid-ntrig.ko
md5sum hid-ntrig.ko

```
If that value matches up with what I provided earlier:
```

sudo cp hid-ntrig.ko /lib/modules/2.6.31-20-generic/kernel/drivers/hid/

``` 
Then restart.  Finally check:
```
python lshal.py
```

---

### Post by -TJ on 2010-02-22
It didn't do anything:
```
tj@xt2:~$ python lshal.py
tj@xt2:~$ 

```

---

### Post by Ayuthia on 2010-02-22
Can you run:
```
lshal>lshal.txt
```
and attach the lshal.txt file?

---

### Post by -TJ on 2010-02-22
Here it is.

---

### Post by Ayuthia on 2010-02-22
Either I am missing something or else the kernel module did not load.  Can you post the results of:
```

uname -r
ls -l /lib/modules/$(uname -r)/kernel/drivers/hid/hid-ntrig.ko
lsmod|grep hid

```

---

### Post by -TJ on 2010-02-23
Sure thing:
```
tj@xt2:~$ uname -r
2.6.31-20-generic
tj@xt2:~$ ls -l /lib/modules/$(uname -r)/kernel/drivers/hid/hid-ntrig.ko
-rw-r--r-- 1 root root 9880 2010-02-22 17:29 /lib/modules/2.6.31-20-generic/kernel/drivers/hid/hid-ntrig.ko
tj@xt2:~$ lsmod|grep hid
hid_ntrig               5280  0 
usbhid                 43968  0 

```

---

### Post by Ayuthia on 2010-02-23
Ok.  I guess we are going to have to backtrack and see what has blocked it.  Can you move the 90-ntrig.rules back to your home directory and restart:
```
sudo mv /etc/udev/rules.d/90-n-trig.rules $HOME
```
Once you restart, check and see if the following produces any results:
```
python lshal.py
```

Also, please post the results of:
```
dmesg|grep [Nn]-[Tt]rig
```

---

### Post by -TJ on 2010-02-23
Here it is:
```
tj@xt2:~$ python lshal.py
udi = '/org/freedesktop/Hal/devices/usb_device_1b96_1_noserial_if1_logicaldev_input_0'
  info.capabilities = {'input', 'input.touchpad'} (string list)
  info.category = 'input'  (string)
  info.parent = '/org/freedesktop/Hal/devices/usb_device_1b96_1_noserial_if1'  (string)
  info.product = 'N-Trig Touchscreen'  (string)
  info.subsystem = 'input'  (string)
  info.udi = '/org/freedesktop/Hal/devices/usb_device_1b96_1_noserial_if1_logicaldev_input_0'  (string)
  input.device = '/dev/input/event13'  (string)
  input.originating_device = '/org/freedesktop/Hal/devices/usb_device_1b96_1_noserial_if1'  (string)
  input.product = 'N-Trig Touchscreen'  (string)
  linux.device_file = '/dev/input/event13'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'input'  (string)
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:1d.1/usb7/7-2/7-2:1.1/input/input13/event13'  (string)

udi = '/org/freedesktop/Hal/devices/usb_device_1b96_1_noserial_if1_logicaldev_input'
  info.capabilities = {'input', 'input.tablet'} (string list)
  info.category = 'input'  (string)
  info.parent = '/org/freedesktop/Hal/devices/usb_device_1b96_1_noserial_if1'  (string)
  info.product = 'N-Trig Pen'  (string)
  info.subsystem = 'input'  (string)
  info.udi = '/org/freedesktop/Hal/devices/usb_device_1b96_1_noserial_if1_logicaldev_input'  (string)
  input.device = '/dev/input/event12'  (string)
  input.originating_device = '/org/freedesktop/Hal/devices/usb_device_1b96_1_noserial_if1'  (string)
  input.product = 'N-Trig Pen'  (string)
  input.x11_driver = 'evdev'  (string)
  linux.device_file = '/dev/input/event12'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'input'  (string)
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:1d.1/usb7/7-2/7-2:1.1/input/input12/event12'  (string)

udi = '/org/freedesktop/Hal/devices/usb_device_1b96_1_noserial_if0_logicaldev_input_0'
  info.capabilities = {'input', 'input.tablet'} (string list)
  info.category = 'input'  (string)
  info.parent = '/org/freedesktop/Hal/devices/usb_device_1b96_1_noserial_if0'  (string)
  info.product = 'N-Trig Pen'  (string)
  info.subsystem = 'input'  (string)
  info.udi = '/org/freedesktop/Hal/devices/usb_device_1b96_1_noserial_if0_logicaldev_input_0'  (string)
  input.device = '/dev/input/event10'  (string)
  input.originating_device = '/org/freedesktop/Hal/devices/usb_device_1b96_1_noserial_if0'  (string)
  input.product = 'N-Trig Pen'  (string)
  input.x11_driver = 'evdev'  (string)
  linux.device_file = '/dev/input/event10'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'input'  (string)
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:1d.1/usb7/7-2/7-2:1.0/input/input9/event10'  (string)

udi = '/org/freedesktop/Hal/devices/usb_device_1b96_1_noserial_if0_logicaldev_input'
  info.capabilities = {'input', 'input.touchpad'} (string list)
  info.category = 'input'  (string)
  info.parent = '/org/freedesktop/Hal/devices/usb_device_1b96_1_noserial_if0'  (string)
  info.product = 'N-Trig Touchscreen'  (string)
  info.subsystem = 'input'  (string)
  info.udi = '/org/freedesktop/Hal/devices/usb_device_1b96_1_noserial_if0_logicaldev_input'  (string)
  input.device = '/dev/input/event11'  (string)
  input.originating_device = '/org/freedesktop/Hal/devices/usb_device_1b96_1_noserial_if0'  (string)
  input.product = 'N-Trig Touchscreen'  (string)
  linux.device_file = '/dev/input/event11'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'input'  (string)
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:1d.1/usb7/7-2/7-2:1.0/input/input11/event11'  (string)

tj@xt2:~$ dmesg|grep [Nn]-[Tt]rig
tj@xt2:~$ 

```

---

### Post by Ayuthia on 2010-02-23
Ok.  We now need to figure out which event produces the touch events and which one produces the pen events.

Please try the following and let us know which one produces data.  As usual, to exit out of the application, you will need to press control-c:

Touch
```

sudo xxd -g1 /dev/input/event11
sudo xxd -g1 /dev/input/event13

```

Stylus
```

sudo xxd -g1 /dev/input/event10
sudo xxd -g1 /dev/input/event12

```

So just let us know whether event 11 or 13 produces any data for your finger and if 10 or 12 works with the stylus.  From there, we can create the proper xorg.conf or .fdi file to get it working.

---

### Post by -TJ on 2010-02-23
Here it is:
```
tj@xt2:~$ sudo xxd -g1 /dev/input/event11
[sudo] password for tj: 
^C
tj@xt2:~$ sudo xxd -g1 /dev/input/event13
^C
tj@xt2:~$ sudo xxd -g1 /dev/input/event10
0000000: ce 56 84 4b 00 00 00 00 72 e1 06 00 00 00 00 00  .V.K....r.......
0000010: 01 00 40 01 01 00 00 00 ce 56 84 4b 00 00 00 00  ..@......V.K....
0000020: 81 e1 06 00 00 00 00 00 03 00 00 00 ac 14 00 00  ................
0000030: ce 56 84 4b 00 00 00 00 85 e1 06 00 00 00 00 00  .V.K............
0000040: 03 00 01 00 36 10 00 00 ce 56 84 4b 00 00 00 00  ....6....V.K....
0000050: 8a e1 06 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
0000060: ce 56 84 4b 00 00 00 00 33 14 07 00 00 00 00 00  .V.K....3.......
0000070: 03 00 01 00 35 10 00 00 ce 56 84 4b 00 00 00 00  ....5....V.K....
0000080: 3a 14 07 00 00 00 00 00 00 00 00 00 00 00 00 00  :...............
0000090: ce 56 84 4b 00 00 00 00 7e 2f 07 00 00 00 00 00  .V.K....~/......
00000a0: 03 00 00 00 aa 14 00 00 ce 56 84 4b 00 00 00 00  .........V.K....
00000b0: 84 2f 07 00 00 00 00 00 03 00 01 00 36 10 00 00  ./..........6...
00000c0: ce 56 84 4b 00 00 00 00 87 2f 07 00 00 00 00 00  .V.K...../......
00000d0: 00 00 00 00 00 00 00 00 ce 56 84 4b 00 00 00 00  .........V.K....
00000e0: e1 4a 07 00 00 00 00 00 03 00 00 00 ab 14 00 00  .J..............
00000f0: ce 56 84 4b 00 00 00 00 ea 4a 07 00 00 00 00 00  .V.K.....J......
0000100: 00 00 00 00 00 00 00 00 ce 56 84 4b 00 00 00 00  .........V.K....
0000110: 22 6a 07 00 00 00 00 00 03 00 00 00 aa 14 00 00  "j..............
0000120: ce 56 84 4b 00 00 00 00 27 6a 07 00 00 00 00 00  .V.K....'j......
0000130: 03 00 01 00 37 10 00 00 ce 56 84 4b 00 00 00 00  ....7....V.K....
0000140: 2b 6a 07 00 00 00 00 00 00 00 00 00 00 00 00 00  +j..............
0000150: ce 56 84 4b 00 00 00 00 83 85 07 00 00 00 00 00  .V.K............
0000160: 03 00 00 00 ab 14 00 00 ce 56 84 4b 00 00 00 00  .........V.K....
0000170: 8d 85 07 00 00 00 00 00 03 00 01 00 38 10 00 00  ............8...
0000180: ce 56 84 4b 00 00 00 00 91 85 07 00 00 00 00 00  .V.K............
0000190: 00 00 00 00 00 00 00 00 ce 56 84 4b 00 00 00 00  .........V.K....
00001a0: b1 fa 07 00 00 00 00 00 03 00 00 00 ac 14 00 00  ................
00001b0: ce 56 84 4b 00 00 00 00 be fa 07 00 00 00 00 00  .V.K............
00001c0: 00 00 00 00 00 00 00 00 ce 56 84 4b 00 00 00 00  .........V.K....
00001d0: ed 19 08 00 00 00 00 00 03 00 00 00 ad 14 00 00  ................
00001e0: ce 56 84 4b 00 00 00 00 f6 19 08 00 00 00 00 00  .V.K............
00001f0: 00 00 00 00 00 00 00 00 ce 56 84 4b 00 00 00 00  .........V.K....
0000200: 42 35 08 00 00 00 00 00 03 00 00 00 af 14 00 00  B5..............
0000210: ce 56 84 4b 00 00 00 00 4a 35 08 00 00 00 00 00  .V.K....J5......
0000220: 00 00 00 00 00 00 00 00 ce 56 84 4b 00 00 00 00  .........V.K....
0000230: 76 54 08 00 00 00 00 00 03 00 00 00 b0 14 00 00  vT..............
0000240: ce 56 84 4b 00 00 00 00 81 54 08 00 00 00 00 00  .V.K.....T......
0000250: 00 00 00 00 00 00 00 00 ce 56 84 4b 00 00 00 00  .........V.K....
0000260: cf 6f 08 00 00 00 00 00 03 00 00 00 b2 14 00 00  .o..............
0000270: ce 56 84 4b 00 00 00 00 da 6f 08 00 00 00 00 00  .V.K.....o......
0000280: 00 00 00 00 00 00 00 00 ce 56 84 4b 00 00 00 00  .........V.K....
0000290: 28 8f 08 00 00 00 00 00 03 00 00 00 b5 14 00 00  (...............
00002a0: ce 56 84 4b 00 00 00 00 31 8f 08 00 00 00 00 00  .V.K....1.......
00002b0: 00 00 00 00 00 00 00 00 ce 56 84 4b 00 00 00 00  .........V.K....
00002c0: 6f aa 08 00 00 00 00 00 03 00 00 00 b7 14 00 00  o...............
00002d0: ce 56 84 4b 00 00 00 00 75 aa 08 00 00 00 00 00  .V.K....u.......
00002e0: 03 00 01 00 39 10 00 00 ce 56 84 4b 00 00 00 00  ....9....V.K....
00002f0: 78 aa 08 00 00 00 00 00 00 00 00 00 00 00 00 00  x...............
0000300: ce 56 84 4b 00 00 00 00 b9 c9 08 00 00 00 00 00  .V.K............
0000310: 03 00 00 00 ba 14 00 00 ce 56 84 4b 00 00 00 00  .........V.K....
0000320: c1 c9 08 00 00 00 00 00 03 00 01 00 3a 10 00 00  ............:...
0000330: ce 56 84 4b 00 00 00 00 c4 c9 08 00 00 00 00 00  .V.K............
0000340: 00 00 00 00 00 00 00 00 ce 56 84 4b 00 00 00 00  .........V.K....
0000350: 0b e5 08 00 00 00 00 00 03 00 00 00 bc 14 00 00  ................
0000360: ce 56 84 4b 00 00 00 00 14 e5 08 00 00 00 00 00  .V.K............
0000370: 00 00 00 00 00 00 00 00 ce 56 84 4b 00 00 00 00  .........V.K....
0000380: 53 04 09 00 00 00 00 00 03 00 00 00 bf 14 00 00  S...............
0000390: ce 56 84 4b 00 00 00 00 5d 04 09 00 00 00 00 00  .V.K....].......
00003a0: 03 00 01 00 3b 10 00 00 ce 56 84 4b 00 00 00 00  ....;....V.K....
00003b0: 61 04 09 00 00 00 00 00 00 00 00 00 00 00 00 00  a...............
00003c0: ce 56 84 4b 00 00 00 00 8e 1f 09 00 00 00 00 00  .V.K............
00003d0: 03 00 00 00 c1 14 00 00 ce 56 84 4b 00 00 00 00  .........V.K....
00003e0: 97 1f 09 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
00003f0: ce 56 84 4b 00 00 00 00 e9 3e 09 00 00 00 00 00  .V.K.....>......
0000400: 03 00 00 00 c4 14 00 00 ce 56 84 4b 00 00 00 00  .........V.K....
0000410: f1 3e 09 00 00 00 00 00 03 00 01 00 3c 10 00 00  .>..........<...
0000420: ce 56 84 4b 00 00 00 00 f5 3e 09 00 00 00 00 00  .V.K.....>......
0000430: 00 00 00 00 00 00 00 00 ce 56 84 4b 00 00 00 00  .........V.K....
0000440: 3f 5a 09 00 00 00 00 00 03 00 00 00 c6 14 00 00  ?Z..............
0000450: ce 56 84 4b 00 00 00 00 4b 5a 09 00 00 00 00 00  .V.K....KZ......
0000460: 00 00 00 00 00 00 00 00 ce 56 84 4b 00 00 00 00  .........V.K....
0000470: 84 79 09 00 00 00 00 00 03 00 00 00 c8 14 00 00  .y..............
0000480: ce 56 84 4b 00 00 00 00 8c 79 09 00 00 00 00 00  .V.K.....y......
0000490: 03 00 01 00 3d 10 00 00 ce 56 84 4b 00 00 00 00  ....=....V.K....
00004a0: 91 79 09 00 00 00 00 00 00 00 00 00 00 00 00 00  .y..............
00004b0: ce 56 84 4b 00 00 00 00 d2 94 09 00 00 00 00 00  .V.K............
00004c0: 03 00 00 00 ca 14 00 00 ce 56 84 4b 00 00 00 00  .........V.K....
00004d0: d9 94 09 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
00004e0: ce 56 84 4b 00 00 00 00 14 b4 09 00 00 00 00 00  .V.K............
00004f0: 03 00 00 00 cb 14 00 00 ce 56 84 4b 00 00 00 00  .........V.K....
0000500: 1e b4 09 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
0000510: ce 56 84 4b 00 00 00 00 71 cf 09 00 00 00 00 00  .V.K....q.......
0000520: 03 00 00 00 cc 14 00 00 ce 56 84 4b 00 00 00 00  .........V.K....
0000530: 7a cf 09 00 00 00 00 00 03 00 01 00 3c 10 00 00  z...........<...
0000540: ce 56 84 4b 00 00 00 00 7e cf 09 00 00 00 00 00  .V.K....~.......
0000550: 00 00 00 00 00 00 00 00 ce 56 84 4b 00 00 00 00  .........V.K....
0000560: 97 ee 09 00 00 00 00 00 03 00 00 00 cd 14 00 00  ................
0000570: ce 56 84 4b 00 00 00 00 9d ee 09 00 00 00 00 00  .V.K............
0000580: 03 00 01 00 3b 10 00 00 ce 56 84 4b 00 00 00 00  ....;....V.K....
0000590: a0 ee 09 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
00005a0: ce 56 84 4b 00 00 00 00 02 0a 0a 00 00 00 00 00  .V.K............
00005b0: 03 00 00 00 ce 14 00 00 ce 56 84 4b 00 00 00 00  .........V.K....
00005c0: 07 0a 0a 00 00 00 00 00 03 00 01 00 3a 10 00 00  ............:...
00005d0: ce 56 84 4b 00 00 00 00 0b 0a 0a 00 00 00 00 00  .V.K............
00005e0: 00 00 00 00 00 00 00 00 ce 56 84 4b 00 00 00 00  .........V.K....
00005f0: 48 29 0a 00 00 00 00 00 03 00 00 00 cf 14 00 00  H)..............
0000600: ce 56 84 4b 00 00 00 00 51 29 0a 00 00 00 00 00  .V.K....Q)......
0000610: 03 00 01 00 38 10 00 00 ce 56 84 4b 00 00 00 00  ....8....V.K....
0000620: 55 29 0a 00 00 00 00 00 00 00 00 00 00 00 00 00  U)..............
0000630: ce 56 84 4b 00 00 00 00 9c 44 0a 00 00 00 00 00  .V.K.....D......
0000640: 03 00 00 00 d0 14 00 00 ce 56 84 4b 00 00 00 00  .........V.K....
0000650: a6 44 0a 00 00 00 00 00 03 00 01 00 36 10 00 00  .D..........6...
0000660: ce 56 84 4b 00 00 00 00 aa 44 0a 00 00 00 00 00  .V.K.....D......
0000670: 00 00 00 00 00 00 00 00 ce 56 84 4b 00 00 00 00  .........V.K....
0000680: c7 63 0a 00 00 00 00 00 03 00 01 00 33 10 00 00  .c..........3...
0000690: ce 56 84 4b 00 00 00 00 cd 63 0a 00 00 00 00 00  .V.K.....c......
00006a0: 00 00 00 00 00 00 00 00 ce 56 84 4b 00 00 00 00  .........V.K....
00006b0: 33 7f 0a 00 00 00 00 00 03 00 00 00 d1 14 00 00  3...............
00006c0: ce 56 84 4b 00 00 00 00 3b 7f 0a 00 00 00 00 00  .V.K....;.......
00006d0: 03 00 01 00 30 10 00 00 ce 56 84 4b 00 00 00 00  ....0....V.K....
00006e0: 3f 7f 0a 00 00 00 00 00 00 00 00 00 00 00 00 00  ?...............
00006f0: ce 56 84 4b 00 00 00 00 7d 9e 0a 00 00 00 00 00  .V.K....}.......
0000700: 03 00 01 00 2d 10 00 00 ce 56 84 4b 00 00 00 00  ....-....V.K....
0000710: 86 9e 0a 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
0000720: ce 56 84 4b 00 00 00 00 d0 b9 0a 00 00 00 00 00  .V.K............
0000730: 03 00 01 00 29 10 00 00 ce 56 84 4b 00 00 00 00  ....)....V.K....
0000740: d9 b9 0a 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
0000750: ce 56 84 4b 00 00 00 00 0d d9 0a 00 00 00 00 00  .V.K............
0000760: 03 00 00 00 d2 14 00 00 ce 56 84 4b 00 00 00 00  .........V.K....
0000770: 12 d9 0a 00 00 00 00 00 03 00 01 00 25 10 00 00  ............%...
0000780: ce 56 84 4b 00 00 00 00 16 d9 0a 00 00 00 00 00  .V.K............
0000790: 00 00 00 00 00 00 00 00 ce 56 84 4b 00 00 00 00  .........V.K....
00007a0: 63 f4 0a 00 00 00 00 00 03 00 01 00 21 10 00 00  c...........!...
00007b0: ce 56 84 4b 00 00 00 00 69 f4 0a 00 00 00 00 00  .V.K....i.......
00007c0: 00 00 00 00 00 00 00 00 ce 56 84 4b 00 00 00 00  .........V.K....
00007d0: af 13 0b 00 00 00 00 00 03 00 00 00 d1 14 00 00  ................
00007e0: ce 56 84 4b 00 00 00 00 b9 13 0b 00 00 00 00 00  .V.K............
00007f0: 03 00 01 00 1e 10 00 00 ce 56 84 4b 00 00 00 00  .........V.K....
0000800: bc 13 0b 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
0000810: ce 56 84 4b 00 00 00 00 02 2f 0b 00 00 00 00 00  .V.K...../......
0000820: 03 00 01 00 1b 10 00 00 ce 56 84 4b 00 00 00 00  .........V.K....
0000830: 0d 2f 0b 00 00 00 00 00 00 00 00 00 00 00 00 00  ./..............
0000840: ce 56 84 4b 00 00 00 00 34 4e 0b 00 00 00 00 00  .V.K....4N......
0000850: 03 00 01 00 19 10 00 00 ce 56 84 4b 00 00 00 00  .........V.K....
0000860: 3a 4e 0b 00 00 00 00 00 00 00 00 00 00 00 00 00  :N..............
0000870: ce 56 84 4b 00 00 00 00 97 69 0b 00 00 00 00 00  .V.K.....i......
0000880: 03 00 00 00 d0 14 00 00 ce 56 84 4b 00 00 00 00  .........V.K....
0000890: 9e 69 0b 00 00 00 00 00 03 00 01 00 15 10 00 00  .i..............
00008a0: ce 56 84 4b 00 00 00 00 a2 69 0b 00 00 00 00 00  .V.K.....i......
00008b0: 00 00 00 00 00 00 00 00 ce 56 84 4b 00 00 00 00  .........V.K....
00008c0: d7 88 0b 00 00 00 00 00 03 00 00 00 cb 14 00 00  ................
00008d0: ce 56 84 4b 00 00 00 00 de 88 0b 00 00 00 00 00  .V.K............
00008e0: 03 00 01 00 12 10 00 00 ce 56 84 4b 00 00 00 00  .........V.K....
00008f0: e2 88 0b 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
0000900: ce 56 84 4b 00 00 00 00 31 a4 0b 00 00 00 00 00  .V.K....1.......
0000910: 03 00 01 00 0f 10 00 00 ce 56 84 4b 00 00 00 00  .........V.K....
0000920: 3b a4 0b 00 00 00 00 00 00 00 00 00 00 00 00 00  ;...............
0000930: ce 56 84 4b 00 00 00 00 6e c3 0b 00 00 00 00 00  .V.K....n.......
0000940: 03 00 01 00 0d 10 00 00 ce 56 84 4b 00 00 00 00  .........V.K....
0000950: 76 c3 0b 00 00 00 00 00 00 00 00 00 00 00 00 00  v...............
0000960: ce 56 84 4b 00 00 00 00 c6 de 0b 00 00 00 00 00  .V.K............
0000970: 03 00 01 00 0a 10 00 00 ce 56 84 4b 00 00 00 00  .........V.K....
0000980: cf de 0b 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
0000990: ce 56 84 4b 00 00 00 00 0a fe 0b 00 00 00 00 00  .V.K............
00009a0: 03 00 01 00 09 10 00 00 ce 56 84 4b 00 00 00 00  .........V.K....
00009b0: 12 fe 0b 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
00009c0: ce 56 84 4b 00 00 00 00 5e 19 0c 00 00 00 00 00  .V.K....^.......
00009d0: 03 00 00 00 c6 14 00 00 ce 56 84 4b 00 00 00 00  .........V.K....
00009e0: 67 19 0c 00 00 00 00 00 03 00 01 00 07 10 00 00  g...............
00009f0: ce 56 84 4b 00 00 00 00 6c 19 0c 00 00 00 00 00  .V.K....l.......
0000a00: 00 00 00 00 00 00 00 00 ce 56 84 4b 00 00 00 00  .........V.K....
0000a10: a0 38 0c 00 00 00 00 00 03 00 00 00 c2 14 00 00  .8..............
0000a20: ce 56 84 4b 00 00 00 00 a5 38 0c 00 00 00 00 00  .V.K.....8......
0000a30: 03 00 01 00 06 10 00 00 ce 56 84 4b 00 00 00 00  .........V.K....
0000a40: a9 38 0c 00 00 00 00 00 00 00 00 00 00 00 00 00  .8..............
0000a50: ce 56 84 4b 00 00 00 00 e9 53 0c 00 00 00 00 00  .V.K.....S......
0000a60: 03 00 00 00 be 14 00 00 ce 56 84 4b 00 00 00 00  .........V.K....
0000a70: f5 53 0c 00 00 00 00 00 00 00 00 00 00 00 00 00  .S..............
0000a80: ce 56 84 4b 00 00 00 00 2e 73 0c 00 00 00 00 00  .V.K.....s......
0000a90: 03 00 00 00 ba 14 00 00 ce 56 84 4b 00 00 00 00  .........V.K....
0000aa0: 37 73 0c 00 00 00 00 00 03 00 01 00 07 10 00 00  7s..............
0000ab0: ce 56 84 4b 00 00 00 00 3c 73 0c 00 00 00 00 00  .V.K....<s......
0000ac0: 00 00 00 00 00 00 00 00 ce 56 84 4b 00 00 00 00  .........V.K....
0000ad0: 86 8e 0c 00 00 00 00 00 03 00 00 00 b7 14 00 00  ................
0000ae0: ce 56 84 4b 00 00 00 00 8f 8e 0c 00 00 00 00 00  .V.K............
0000af0: 03 00 01 00 05 10 00 00 ce 56 84 4b 00 00 00 00  .........V.K....
0000b00: 92 8e 0c 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
0000b10: ce 56 84 4b 00 00 00 00 c8 ad 0c 00 00 00 00 00  .V.K............
0000b20: 03 00 00 00 b4 14 00 00 ce 56 84 4b 00 00 00 00  .........V.K....
0000b30: cf ad 0c 00 00 00 00 00 03 00 01 00 07 10 00 00  ................
0000b40: ce 56 84 4b 00 00 00 00 d2 ad 0c 00 00 00 00 00  .V.K............
0000b50: 00 00 00 00 00 00 00 00 ce 56 84 4b 00 00 00 00  .........V.K....
0000b60: 2b c9 0c 00 00 00 00 00 03 00 00 00 b1 14 00 00  +...............
0000b70: ce 56 84 4b 00 00 00 00 37 c9 0c 00 00 00 00 00  .V.K....7.......
0000b80: 00 00 00 00 00 00 00 00 ce 56 84 4b 00 00 00 00  .........V.K....
0000b90: 54 e8 0c 00 00 00 00 00 03 00 00 00 ae 14 00 00  T...............
0000ba0: ce 56 84 4b 00 00 00 00 5b e8 0c 00 00 00 00 00  .V.K....[.......
0000bb0: 03 00 01 00 06 10 00 00 ce 56 84 4b 00 00 00 00  .........V.K....
0000bc0: 5f e8 0c 00 00 00 00 00 00 00 00 00 00 00 00 00  _...............
0000bd0: ce 56 84 4b 00 00 00 00 b9 03 0d 00 00 00 00 00  .V.K............
0000be0: 03 00 00 00 ac 14 00 00 ce 56 84 4b 00 00 00 00  .........V.K....
0000bf0: c2 03 0d 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
0000c00: ce 56 84 4b 00 00 00 00 fa 22 0d 00 00 00 00 00  .V.K....."......
0000c10: 03 00 00 00 a9 14 00 00 ce 56 84 4b 00 00 00 00  .........V.K....
0000c20: 03 23 0d 00 00 00 00 00 00 00 00 00 00 00 00 00  .#..............
0000c30: ce 56 84 4b 00 00 00 00 54 3e 0d 00 00 00 00 00  .V.K....T>......
0000c40: 03 00 00 00 a8 14 00 00 ce 56 84 4b 00 00 00 00  .........V.K....
0000c50: 5b 3e 0d 00 00 00 00 00 03 00 01 00 05 10 00 00  [>..............
0000c60: ce 56 84 4b 00 00 00 00 60 3e 0d 00 00 00 00 00  .V.K....`>......
0000c70: 00 00 00 00 00 00 00 00 ce 56 84 4b 00 00 00 00  .........V.K....
0000c80: 98 5d 0d 00 00 00 00 00 03 00 00 00 a6 14 00 00  .]..............
0000c90: ce 56 84 4b 00 00 00 00 a0 5d 0d 00 00 00 00 00  .V.K.....]......
0000ca0: 03 00 01 00 01 10 00 00 ce 56 84 4b 00 00 00 00  .........V.K....
0000cb0: a5 5d 0d 00 00 00 00 00 00 00 00 00 00 00 00 00  .]..............
0000cc0: ce 56 84 4b 00 00 00 00 eb 78 0d 00 00 00 00 00  .V.K.....x......
0000cd0: 03 00 00 00 a4 14 00 00 ce 56 84 4b 00 00 00 00  .........V.K....
0000ce0: f2 78 0d 00 00 00 00 00 03 00 01 00 06 10 00 00  .x..............
0000cf0: ce 56 84 4b 00 00 00 00 f6 78 0d 00 00 00 00 00  .V.K.....x......
0000d00: 00 00 00 00 00 00 00 00 ce 56 84 4b 00 00 00 00  .........V.K....
0000d10: 2c 98 0d 00 00 00 00 00 03 00 00 00 a2 14 00 00  ,...............
0000d20: ce 56 84 4b 00 00 00 00 31 98 0d 00 00 00 00 00  .V.K....1.......
0000d30: 03 00 01 00 11 10 00 00 ce 56 84 4b 00 00 00 00  .........V.K....
0000d40: 34 98 0d 00 00 00 00 00 00 00 00 00 00 00 00 00  4...............
0000d50: ce 56 84 4b 00 00 00 00 89 b3 0d 00 00 00 00 00  .V.K............
0000d60: 03 00 01 00 19 10 00 00 ce 56 84 4b 00 00 00 00  .........V.K....
0000d70: 93 b3 0d 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
0000d80: ce 56 84 4b 00 00 00 00 db ce 0d 00 00 00 00 00  .V.K............
0000d90: 01 00 40 01 00 00 00 00 ce 56 84 4b 00 00 00 00  ..@......V.K....
0000da0: e9 ce 0d 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
^C
tj@xt2:~$ sudo xxd -g1 /dev/input/event12
^C
tj@xt2:~$ 

```

It doesn't seem like touch is working. =(

By the way, I received the box to put my xt2 in so I can send it back to Dell so they can hopefully replace the piece of junk with a new one. They better replace the entire duo sense display as well as the scroll buttons on the back and stuff... and some part on the bottom that is due to poor build quality.

---

### Post by Ayuthia on 2010-02-24
> **-TJ said:**
> Here it is:
```
tj@xt2:~$ sudo xxd -g1 /dev/input/event11
[sudo] password for tj: 
^C
tj@xt2:~$ sudo xxd -g1 /dev/input/event13
^C
tj@xt2:~$ sudo xxd -g1 /dev/input/event10
0000000: ce 56 84 4b 00 00 00 00 72 e1 06 00 00 00 00 00  .V.K....r.......
0000010: 01 00 40 01 01 00 00 00 ce 56 84 4b 00 00 00 00  ..@......V.K....
0000020: 81 e1 06 00 00 00 00 00 03 00 00 00 ac 14 00 00  ................
0000030: ce 56 84 4b 00 00 00 00 85 e1 06 00 00 00 00 00  .V.K............
0000040: 03 00 01 00 36 10 00 00 ce 56 84 4b 00 00 00 00  ....6....V.K....
0000050: 8a e1 06 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
0000060: ce 56 84 4b 00 00 00 00 33 14 07 00 00 00 00 00  .V.K....3.......
0000070: 03 00 01 00 35 10 00 00 ce 56 84 4b 00 00 00 00  ....5....V.K....
0000080: 3a 14 07 00 00 00 00 00 00 00 00 00 00 00 00 00  :...............
0000090: ce 56 84 4b 00 00 00 00 7e 2f 07 00 00 00 00 00  .V.K....~/......
00000a0: 03 00 00 00 aa 14 00 00 ce 56 84 4b 00 00 00 00  .........V.K....
00000b0: 84 2f 07 00 00 00 00 00 03 00 01 00 36 10 00 00  ./..........6...
00000c0: ce 56 84 4b 00 00 00 00 87 2f 07 00 00 00 00 00  .V.K...../......
00000d0: 00 00 00 00 00 00 00 00 ce 56 84 4b 00 00 00 00  .........V.K....
00000e0: e1 4a 07 00 00 00 00 00 03 00 00 00 ab 14 00 00  .J..............
00000f0: ce 56 84 4b 00 00 00 00 ea 4a 07 00 00 00 00 00  .V.K.....J......
0000100: 00 00 00 00 00 00 00 00 ce 56 84 4b 00 00 00 00  .........V.K....
0000110: 22 6a 07 00 00 00 00 00 03 00 00 00 aa 14 00 00  "j..............
0000120: ce 56 84 4b 00 00 00 00 27 6a 07 00 00 00 00 00  .V.K....'j......
0000130: 03 00 01 00 37 10 00 00 ce 56 84 4b 00 00 00 00  ....7....V.K....
0000140: 2b 6a 07 00 00 00 00 00 00 00 00 00 00 00 00 00  +j..............
0000150: ce 56 84 4b 00 00 00 00 83 85 07 00 00 00 00 00  .V.K............
0000160: 03 00 00 00 ab 14 00 00 ce 56 84 4b 00 00 00 00  .........V.K....
0000170: 8d 85 07 00 00 00 00 00 03 00 01 00 38 10 00 00  ............8...
0000180: ce 56 84 4b 00 00 00 00 91 85 07 00 00 00 00 00  .V.K............
0000190: 00 00 00 00 00 00 00 00 ce 56 84 4b 00 00 00 00  .........V.K....
00001a0: b1 fa 07 00 00 00 00 00 03 00 00 00 ac 14 00 00  ................
00001b0: ce 56 84 4b 00 00 00 00 be fa 07 00 00 00 00 00  .V.K............
00001c0: 00 00 00 00 00 00 00 00 ce 56 84 4b 00 00 00 00  .........V.K....
00001d0: ed 19 08 00 00 00 00 00 03 00 00 00 ad 14 00 00  ................
00001e0: ce 56 84 4b 00 00 00 00 f6 19 08 00 00 00 00 00  .V.K............
00001f0: 00 00 00 00 00 00 00 00 ce 56 84 4b 00 00 00 00  .........V.K....
0000200: 42 35 08 00 00 00 00 00 03 00 00 00 af 14 00 00  B5..............
0000210: ce 56 84 4b 00 00 00 00 4a 35 08 00 00 00 00 00  .V.K....J5......
0000220: 00 00 00 00 00 00 00 00 ce 56 84 4b 00 00 00 00  .........V.K....
0000230: 76 54 08 00 00 00 00 00 03 00 00 00 b0 14 00 00  vT..............
0000240: ce 56 84 4b 00 00 00 00 81 54 08 00 00 00 00 00  .V.K.....T......
0000250: 00 00 00 00 00 00 00 00 ce 56 84 4b 00 00 00 00  .........V.K....
0000260: cf 6f 08 00 00 00 00 00 03 00 00 00 b2 14 00 00  .o..............
0000270: ce 56 84 4b 00 00 00 00 da 6f 08 00 00 00 00 00  .V.K.....o......
0000280: 00 00 00 00 00 00 00 00 ce 56 84 4b 00 00 00 00  .........V.K....
0000290: 28 8f 08 00 00 00 00 00 03 00 00 00 b5 14 00 00  (...............
00002a0: ce 56 84 4b 00 00 00 00 31 8f 08 00 00 00 00 00  .V.K....1.......
00002b0: 00 00 00 00 00 00 00 00 ce 56 84 4b 00 00 00 00  .........V.K....
00002c0: 6f aa 08 00 00 00 00 00 03 00 00 00 b7 14 00 00  o...............
00002d0: ce 56 84 4b 00 00 00 00 75 aa 08 00 00 00 00 00  .V.K....u.......
00002e0: 03 00 01 00 39 10 00 00 ce 56 84 4b 00 00 00 00  ....9....V.K....
00002f0: 78 aa 08 00 00 00 00 00 00 00 00 00 00 00 00 00  x...............
0000300: ce 56 84 4b 00 00 00 00 b9 c9 08 00 00 00 00 00  .V.K............
0000310: 03 00 00 00 ba 14 00 00 ce 56 84 4b 00 00 00 00  .........V.K....
0000320: c1 c9 08 00 00 00 00 00 03 00 01 00 3a 10 00 00  ............:...
0000330: ce 56 84 4b 00 00 00 00 c4 c9 08 00 00 00 00 00  .V.K............
0000340: 00 00 00 00 00 00 00 00 ce 56 84 4b 00 00 00 00  .........V.K....
0000350: 0b e5 08 00 00 00 00 00 03 00 00 00 bc 14 00 00  ................
0000360: ce 56 84 4b 00 00 00 00 14 e5 08 00 00 00 00 00  .V.K............
0000370: 00 00 00 00 00 00 00 00 ce 56 84 4b 00 00 00 00  .........V.K....
0000380: 53 04 09 00 00 00 00 00 03 00 00 00 bf 14 00 00  S...............
0000390: ce 56 84 4b 00 00 00 00 5d 04 09 00 00 00 00 00  .V.K....].......
00003a0: 03 00 01 00 3b 10 00 00 ce 56 84 4b 00 00 00 00  ....;....V.K....
00003b0: 61 04 09 00 00 00 00 00 00 00 00 00 00 00 00 00  a...............
00003c0: ce 56 84 4b 00 00 00 00 8e 1f 09 00 00 00 00 00  .V.K............
00003d0: 03 00 00 00 c1 14 00 00 ce 56 84 4b 00 00 00 00  .........V.K....
00003e0: 97 1f 09 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
00003f0: ce 56 84 4b 00 00 00 00 e9 3e 09 00 00 00 00 00  .V.K.....>......
0000400: 03 00 00 00 c4 14 00 00 ce 56 84 4b 00 00 00 00  .........V.K....
0000410: f1 3e 09 00 00 00 00 00 03 00 01 00 3c 10 00 00  .>..........<...
0000420: ce 56 84 4b 00 00 00 00 f5 3e 09 00 00 00 00 00  .V.K.....>......
0000430: 00 00 00 00 00 00 00 00 ce 56 84 4b 00 00 00 00  .........V.K....
0000440: 3f 5a 09 00 00 00 00 00 03 00 00 00 c6 14 00 00  ?Z..............
0000450: ce 56 84 4b 00 00 00 00 4b 5a 09 00 00 00 00 00  .V.K....KZ......
0000460: 00 00 00 00 00 00 00 00 ce 56 84 4b 00 00 00 00  .........V.K....
0000470: 84 79 09 00 00 00 00 00 03 00 00 00 c8 14 00 00  .y..............
0000480: ce 56 84 4b 00 00 00 00 8c 79 09 00 00 00 00 00  .V.K.....y......
0000490: 03 00 01 00 3d 10 00 00 ce 56 84 4b 00 00 00 00  ....=....V.K....
00004a0: 91 79 09 00 00 00 00 00 00 00 00 00 00 00 00 00  .y..............
00004b0: ce 56 84 4b 00 00 00 00 d2 94 09 00 00 00 00 00  .V.K............
00004c0: 03 00 00 00 ca 14 00 00 ce 56 84 4b 00 00 00 00  .........V.K....
00004d0: d9 94 09 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
00004e0: ce 56 84 4b 00 00 00 00 14 b4 09 00 00 00 00 00  .V.K............
00004f0: 03 00 00 00 cb 14 00 00 ce 56 84 4b 00 00 00 00  .........V.K....
0000500: 1e b4 09 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
0000510: ce 56 84 4b 00 00 00 00 71 cf 09 00 00 00 00 00  .V.K....q.......
0000520: 03 00 00 00 cc 14 00 00 ce 56 84 4b 00 00 00 00  .........V.K....
0000530: 7a cf 09 00 00 00 00 00 03 00 01 00 3c 10 00 00  z...........<...
0000540: ce 56 84 4b 00 00 00 00 7e cf 09 00 00 00 00 00  .V.K....~.......
0000550: 00 00 00 00 00 00 00 00 ce 56 84 4b 00 00 00 00  .........V.K....
0000560: 97 ee 09 00 00 00 00 00 03 00 00 00 cd 14 00 00  ................
0000570: ce 56 84 4b 00 00 00 00 9d ee 09 00 00 00 00 00  .V.K............
0000580: 03 00 01 00 3b 10 00 00 ce 56 84 4b 00 00 00 00  ....;....V.K....
0000590: a0 ee 09 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
00005a0: ce 56 84 4b 00 00 00 00 02 0a 0a 00 00 00 00 00  .V.K............
00005b0: 03 00 00 00 ce 14 00 00 ce 56 84 4b 00 00 00 00  .........V.K....
00005c0: 07 0a 0a 00 00 00 00 00 03 00 01 00 3a 10 00 00  ............:...
00005d0: ce 56 84 4b 00 00 00 00 0b 0a 0a 00 00 00 00 00  .V.K............
00005e0: 00 00 00 00 00 00 00 00 ce 56 84 4b 00 00 00 00  .........V.K....
00005f0: 48 29 0a 00 00 00 00 00 03 00 00 00 cf 14 00 00  H)..............
0000600: ce 56 84 4b 00 00 00 00 51 29 0a 00 00 00 00 00  .V.K....Q)......
0000610: 03 00 01 00 38 10 00 00 ce 56 84 4b 00 00 00 00  ....8....V.K....
0000620: 55 29 0a 00 00 00 00 00 00 00 00 00 00 00 00 00  U)..............
0000630: ce 56 84 4b 00 00 00 00 9c 44 0a 00 00 00 00 00  .V.K.....D......
0000640: 03 00 00 00 d0 14 00 00 ce 56 84 4b 00 00 00 00  .........V.K....
0000650: a6 44 0a 00 00 00 00 00 03 00 01 00 36 10 00 00  .D..........6...
0000660: ce 56 84 4b 00 00 00 00 aa 44 0a 00 00 00 00 00  .V.K.....D......
0000670: 00 00 00 00 00 00 00 00 ce 56 84 4b 00 00 00 00  .........V.K....
0000680: c7 63 0a 00 00 00 00 00 03 00 01 00 33 10 00 00  .c..........3...
0000690: ce 56 84 4b 00 00 00 00 cd 63 0a 00 00 00 00 00  .V.K.....c......
00006a0: 00 00 00 00 00 00 00 00 ce 56 84 4b 00 00 00 00  .........V.K....
00006b0: 33 7f 0a 00 00 00 00 00 03 00 00 00 d1 14 00 00  3...............
00006c0: ce 56 84 4b 00 00 00 00 3b 7f 0a 00 00 00 00 00  .V.K....;.......
00006d0: 03 00 01 00 30 10 00 00 ce 56 84 4b 00 00 00 00  ....0....V.K....
00006e0: 3f 7f 0a 00 00 00 00 00 00 00 00 00 00 00 00 00  ?...............
00006f0: ce 56 84 4b 00 00 00 00 7d 9e 0a 00 00 00 00 00  .V.K....}.......
0000700: 03 00 01 00 2d 10 00 00 ce 56 84 4b 00 00 00 00  ....-....V.K....
0000710: 86 9e 0a 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
0000720: ce 56 84 4b 00 00 00 00 d0 b9 0a 00 00 00 00 00  .V.K............
0000730: 03 00 01 00 29 10 00 00 ce 56 84 4b 00 00 00 00  ....)....V.K....
0000740: d9 b9 0a 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
0000750: ce 56 84 4b 00 00 00 00 0d d9 0a 00 00 00 00 00  .V.K............
0000760: 03 00 00 00 d2 14 00 00 ce 56 84 4b 00 00 00 00  .........V.K....
0000770: 12 d9 0a 00 00 00 00 00 03 00 01 00 25 10 00 00  ............%...
0000780: ce 56 84 4b 00 00 00 00 16 d9 0a 00 00 00 00 00  .V.K............
0000790: 00 00 00 00 00 00 00 00 ce 56 84 4b 00 00 00 00  .........V.K....
00007a0: 63 f4 0a 00 00 00 00 00 03 00 01 00 21 10 00 00  c...........!...
00007b0: ce 56 84 4b 00 00 00 00 69 f4 0a 00 00 00 00 00  .V.K....i.......
00007c0: 00 00 00 00 00 00 00 00 ce 56 84 4b 00 00 00 00  .........V.K....
00007d0: af 13 0b 00 00 00 00 00 03 00 00 00 d1 14 00 00  ................
00007e0: ce 56 84 4b 00 00 00 00 b9 13 0b 00 00 00 00 00  .V.K............
00007f0: 03 00 01 00 1e 10 00 00 ce 56 84 4b 00 00 00 00  .........V.K....
0000800: bc 13 0b 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
0000810: ce 56 84 4b 00 00 00 00 02 2f 0b 00 00 00 00 00  .V.K...../......
0000820: 03 00 01 00 1b 10 00 00 ce 56 84 4b 00 00 00 00  .........V.K....
0000830: 0d 2f 0b 00 00 00 00 00 00 00 00 00 00 00 00 00  ./..............
0000840: ce 56 84 4b 00 00 00 00 34 4e 0b 00 00 00 00 00  .V.K....4N......
0000850: 03 00 01 00 19 10 00 00 ce 56 84 4b 00 00 00 00  .........V.K....
0000860: 3a 4e 0b 00 00 00 00 00 00 00 00 00 00 00 00 00  :N..............
0000870: ce 56 84 4b 00 00 00 00 97 69 0b 00 00 00 00 00  .V.K.....i......
0000880: 03 00 00 00 d0 14 00 00 ce 56 84 4b 00 00 00 00  .........V.K....
0000890: 9e 69 0b 00 00 00 00 00 03 00 01 00 15 10 00 00  .i..............
00008a0: ce 56 84 4b 00 00 00 00 a2 69 0b 00 00 00 00 00  .V.K.....i......
00008b0: 00 00 00 00 00 00 00 00 ce 56 84 4b 00 00 00 00  .........V.K....
00008c0: d7 88 0b 00 00 00 00 00 03 00 00 00 cb 14 00 00  ................
00008d0: ce 56 84 4b 00 00 00 00 de 88 0b 00 00 00 00 00  .V.K............
00008e0: 03 00 01 00 12 10 00 00 ce 56 84 4b 00 00 00 00  .........V.K....
00008f0: e2 88 0b 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
0000900: ce 56 84 4b 00 00 00 00 31 a4 0b 00 00 00 00 00  .V.K....1.......
0000910: 03 00 01 00 0f 10 00 00 ce 56 84 4b 00 00 00 00  .........V.K....
0000920: 3b a4 0b 00 00 00 00 00 00 00 00 00 00 00 00 00  ;...............
0000930: ce 56 84 4b 00 00 00 00 6e c3 0b 00 00 00 00 00  .V.K....n.......
0000940: 03 00 01 00 0d 10 00 00 ce 56 84 4b 00 00 00 00  .........V.K....
0000950: 76 c3 0b 00 00 00 00 00 00 00 00 00 00 00 00 00  v...............
0000960: ce 56 84 4b 00 00 00 00 c6 de 0b 00 00 00 00 00  .V.K............
0000970: 03 00 01 00 0a 10 00 00 ce 56 84 4b 00 00 00 00  .........V.K....
0000980: cf de 0b 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
0000990: ce 56 84 4b 00 00 00 00 0a fe 0b 00 00 00 00 00  .V.K............
00009a0: 03 00 01 00 09 10 00 00 ce 56 84 4b 00 00 00 00  .........V.K....
00009b0: 12 fe 0b 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
00009c0: ce 56 84 4b 00 00 00 00 5e 19 0c 00 00 00 00 00  .V.K....^.......
00009d0: 03 00 00 00 c6 14 00 00 ce 56 84 4b 00 00 00 00  .........V.K....
00009e0: 67 19 0c 00 00 00 00 00 03 00 01 00 07 10 00 00  g...............
00009f0: ce 56 84 4b 00 00 00 00 6c 19 0c 00 00 00 00 00  .V.K....l.......
0000a00: 00 00 00 00 00 00 00 00 ce 56 84 4b 00 00 00 00  .........V.K....
0000a10: a0 38 0c 00 00 00 00 00 03 00 00 00 c2 14 00 00  .8..............
0000a20: ce 56 84 4b 00 00 00 00 a5 38 0c 00 00 00 00 00  .V.K.....8......
0000a30: 03 00 01 00 06 10 00 00 ce 56 84 4b 00 00 00 00  .........V.K....
0000a40: a9 38 0c 00 00 00 00 00 00 00 00 00 00 00 00 00  .8..............
0000a50: ce 56 84 4b 00 00 00 00 e9 53 0c 00 00 00 00 00  .V.K.....S......
0000a60: 03 00 00 00 be 14 00 00 ce 56 84 4b 00 00 00 00  .........V.K....
0000a70: f5 53 0c 00 00 00 00 00 00 00 00 00 00 00 00 00  .S..............
0000a80: ce 56 84 4b 00 00 00 00 2e 73 0c 00 00 00 00 00  .V.K.....s......
0000a90: 03 00 00 00 ba 14 00 00 ce 56 84 4b 00 00 00 00  .........V.K....
0000aa0: 37 73 0c 00 00 00 00 00 03 00 01 00 07 10 00 00  7s..............
0000ab0: ce 56 84 4b 00 00 00 00 3c 73 0c 00 00 00 00 00  .V.K....<s......
0000ac0: 00 00 00 00 00 00 00 00 ce 56 84 4b 00 00 00 00  .........V.K....
0000ad0: 86 8e 0c 00 00 00 00 00 03 00 00 00 b7 14 00 00  ................
0000ae0: ce 56 84 4b 00 00 00 00 8f 8e 0c 00 00 00 00 00  .V.K............
0000af0: 03 00 01 00 05 10 00 00 ce 56 84 4b 00 00 00 00  .........V.K....
0000b00: 92 8e 0c 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
0000b10: ce 56 84 4b 00 00 00 00 c8 ad 0c 00 00 00 00 00  .V.K............
0000b20: 03 00 00 00 b4 14 00 00 ce 56 84 4b 00 00 00 00  .........V.K....
0000b30: cf ad 0c 00 00 00 00 00 03 00 01 00 07 10 00 00  ................
0000b40: ce 56 84 4b 00 00 00 00 d2 ad 0c 00 00 00 00 00  .V.K............
0000b50: 00 00 00 00 00 00 00 00 ce 56 84 4b 00 00 00 00  .........V.K....
0000b60: 2b c9 0c 00 00 00 00 00 03 00 00 00 b1 14 00 00  +...............
0000b70: ce 56 84 4b 00 00 00 00 37 c9 0c 00 00 00 00 00  .V.K....7.......
0000b80: 00 00 00 00 00 00 00 00 ce 56 84 4b 00 00 00 00  .........V.K....
0000b90: 54 e8 0c 00 00 00 00 00 03 00 00 00 ae 14 00 00  T...............
0000ba0: ce 56 84 4b 00 00 00 00 5b e8 0c 00 00 00 00 00  .V.K....[.......
0000bb0: 03 00 01 00 06 10 00 00 ce 56 84 4b 00 00 00 00  .........V.K....
0000bc0: 5f e8 0c 00 00 00 00 00 00 00 00 00 00 00 00 00  _...............
0000bd0: ce 56 84 4b 00 00 00 00 b9 03 0d 00 00 00 00 00  .V.K............
0000be0: 03 00 00 00 ac 14 00 00 ce 56 84 4b 00 00 00 00  .........V.K....
0000bf0: c2 03 0d 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
0000c00: ce 56 84 4b 00 00 00 00 fa 22 0d 00 00 00 00 00  .V.K....."......
0000c10: 03 00 00 00 a9 14 00 00 ce 56 84 4b 00 00 00 00  .........V.K....
0000c20: 03 23 0d 00 00 00 00 00 00 00 00 00 00 00 00 00  .#..............
0000c30: ce 56 84 4b 00 00 00 00 54 3e 0d 00 00 00 00 00  .V.K....T>......
0000c40: 03 00 00 00 a8 14 00 00 ce 56 84 4b 00 00 00 00  .........V.K....
0000c50: 5b 3e 0d 00 00 00 00 00 03 00 01 00 05 10 00 00  [>..............
0000c60: ce 56 84 4b 00 00 00 00 60 3e 0d 00 00 00 00 00  .V.K....`>......
0000c70: 00 00 00 00 00 00 00 00 ce 56 84 4b 00 00 00 00  .........V.K....
0000c80: 98 5d 0d 00 00 00 00 00 03 00 00 00 a6 14 00 00  .]..............
0000c90: ce 56 84 4b 00 00 00 00 a0 5d 0d 00 00 00 00 00  .V.K.....]......
0000ca0: 03 00 01 00 01 10 00 00 ce 56 84 4b 00 00 00 00  .........V.K....
0000cb0: a5 5d 0d 00 00 00 00 00 00 00 00 00 00 00 00 00  .]..............
0000cc0: ce 56 84 4b 00 00 00 00 eb 78 0d 00 00 00 00 00  .V.K.....x......
0000cd0: 03 00 00 00 a4 14 00 00 ce 56 84 4b 00 00 00 00  .........V.K....
0000ce0: f2 78 0d 00 00 00 00 00 03 00 01 00 06 10 00 00  .x..............
0000cf0: ce 56 84 4b 00 00 00 00 f6 78 0d 00 00 00 00 00  .V.K.....x......
0000d00: 00 00 00 00 00 00 00 00 ce 56 84 4b 00 00 00 00  .........V.K....
0000d10: 2c 98 0d 00 00 00 00 00 03 00 00 00 a2 14 00 00  ,...............
0000d20: ce 56 84 4b 00 00 00 00 31 98 0d 00 00 00 00 00  .V.K....1.......
0000d30: 03 00 01 00 11 10 00 00 ce 56 84 4b 00 00 00 00  .........V.K....
0000d40: 34 98 0d 00 00 00 00 00 00 00 00 00 00 00 00 00  4...............
0000d50: ce 56 84 4b 00 00 00 00 89 b3 0d 00 00 00 00 00  .V.K............
0000d60: 03 00 01 00 19 10 00 00 ce 56 84 4b 00 00 00 00  .........V.K....
0000d70: 93 b3 0d 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
0000d80: ce 56 84 4b 00 00 00 00 db ce 0d 00 00 00 00 00  .V.K............
0000d90: 01 00 40 01 00 00 00 00 ce 56 84 4b 00 00 00 00  ..@......V.K....
0000da0: e9 ce 0d 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
^C
tj@xt2:~$ sudo xxd -g1 /dev/input/event12
^C
tj@xt2:~$ 

```

It doesn't seem like touch is working. =(

By the way, I received the box to put my xt2 in so I can send it back to Dell so they can hopefully replace the piece of junk with a new one. They better replace the entire duo sense display as well as the scroll buttons on the back and stuff... and some part on the bottom that is due to poor build quality.

If you still want to try this out, please post your xorg.conf and we can get your stylus working or you can wait until you get your laptop back and we can try it then when it all works.

---

### Post by -TJ on 2010-02-24
I will try it out soon, if I have time. I will send it though, so I don't think we will have time to do that... I only wanted to test out Ubuntu because Windows 7 wasn't working. Thanks for your help, and I'll be contacting you whenever possible. It was a pleasure working with you guys. After my xt2 comes back, I may have to keep my Windows installation. I'll see if I can squeeze in Ubuntu. It will be a whole lot easier if I just ran Ubuntu on a virtual machine on Windows. That would make a lot more sense instead of having to go through all of this trouble.

---

### Post by dyslexia on 2010-02-24
Tried that a long time ago, it seems the "enhanced" vpc won't even detect the n-trig device (in either emulated windows OR ubuntu)!   (anyone else try this?)
[URL="http://ubuntuforums.org/showpost.php?p=8645195&postcount=127"]
Digitalchemicalmystery[/URL] figured out a way to get windows to recognise the device in KVM, I tried it but couldn't get the device back after exiting KVM!!!!!

---

### Post by -TJ on 2010-02-25
How is that not possible? The tablet will use the vista or win7 drivers to detect the position of the stylus, therefore it wouldn't be affected at all by the virtual machine. Just run the virtual machine on something like VMware and everything should be alright.

---

### Post by -TJ on 2010-03-08
Okay. So I send my XT2 on Wednesday or sometime around there and I'm curious as to when it will come back. Whether the Ntrig DuoSense and the hinge and the side controls are repaired or the whole is replaced is unknown. I just want an XT2 that works. =/

---

### Post by Saclaysien on 2010-03-18
Hello,

I have a Dell Latitude XT2, and I have been following this and other threads to get the touch and the pen to work under ubuntu. Finally, I got it to work. So, thanks to Ayuthia, Favux, Rafi, and many others who actually made it work. Since it took me quite a while to extract the right information from all the forum posts, I think it might be helpful for the unexperienced user to have a step-by-step in a single (and not too long) post.

What I did works for Ubuntu 9.10 (Karmic). I tested it for the kernels
2.6.31-14-generic   and 
2.6.31-20-generic

And here is what I did 
(most of this can already be found in this post: [http://ubuntuforums.org/showthread.php?t=1252492)]("http://ubuntuforums.org/showthread.php?t=1252492")

1. Step: install N-trig support by following the directions in this post: 
[http://linuxfans.keryxproject.org/?page_id=23](http://linuxfans.keryxproject.org/?page_id=23)

2. Step: installing linuxwacom-0.8.4-4 by following the directions in this post:
[http://linuxfans.keryxproject.org/?page_id=44](http://linuxfans.keryxproject.org/?page_id=44)

3. Step: take the xorg.conf from this post:
[http://ubuntuforums.org/showpost.php?p=8863748&postcount=115](http://ubuntuforums.org/showpost.php?p=8863748&postcount=115)
and replace the line

       Option          "Device"        "/dev/input/n-trig"

everywhere by 

       Option          "Device"        "/dev/input/by-path/pci-0000:00:1d.1-usb-0:2:1.1-event-mouse"

and copy it into /etc/X11/xorg.conf

4. Step: reboot.


Some feedback for the developers:

1) I have Windows 7 installed as parallel system, and I found the by-path by trying the various inputs in my /dev/ directory. This was quite a frustrating procedure, because the system crashes during boot if the device option is wrong, and I did not know that this was the reason. The by-path is right now linked to /dev/input/event9 .

2) I also tried linuxwacom-0.8.5-10 following the steps in 
[http://linuxfans.keryxproject.org/?page_id=73](http://linuxfans.keryxproject.org/?page_id=73)
But it always crashed when booting (even without any xorg.conf)

3) I don't know if multitouch is working because I don't know any software to test it.


I hope this is helpful for someone.

Best regards

---

### Post by -TJ on 2010-03-18
Hey everyone!
Guess what.

My computer is fixed! The touch and pen interface works alright.

I installed the Windows 7 driver and firmware, but then the pen didn't work correctly.

So I had to uninstall the driver and firmware and it worked normally again.

I don't have Ubuntu on my computer yet, but I will soon.
Maybe I should wait until Ubuntu 10.04 is released.

---

### Post by edika32 on 2011-04-05
I have a Dell XT2 that I can't enable multitouch on. The output from xinput is
 
```

c3@car1c:~$ xinput --list
&#9121; Virtual core pointer                        id=2    [master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer                  id=4    [slave  pointer  (2)]
&#9116;   &#8627; N-Trig Pen eraser                           id=9    [slave  pointer  (2)]
&#9116;   &#8627; N-Trig Pen pad                              id=10    [slave  pointer  (2)]
&#9116;   &#8627; N-Trig Pen stylus                           id=11    [slave  pointer  (2)]
&#9116;   &#8627; N-Trig Touchscreen                          id=12    [slave  pointer  (2)]
&#9116;   &#8627; PS/2 Generic Mouse                          id=14    [slave  pointer  (2)]
&#9116;   &#8627; N-Trig Pen eraser                           id=16    [slave  pointer  (2)]
&#9116;   &#8627; N-Trig Pen pad                              id=17    [slave  pointer  (2)]
&#9116;   &#8627; N-Trig Pen stylus                           id=18    [slave  pointer  (2)]
&#9116;   &#8627; N-Trig Touchscreen                          id=19    [slave  pointer  (2)]
&#9123; Virtual core keyboard                       id=3    [master keyboard (2)]
    &#8627; Virtual core XTEST keyboard                 id=5    [slave  keyboard (3)]
    &#8627; Video Bus                                   id=6    [slave  keyboard (3)]
    &#8627; Power Button                                id=7    [slave  keyboard (3)]
    &#8627; Sleep Button                                id=8    [slave  keyboard (3)]
    &#8627; AT Translated Set 2 keyboard                id=13    [slave  keyboard (3)]
    &#8627; Dell WMI hotkeys                            id=15    [slave  keyboard (3)]
c3@car1c:~$ 

```

Havn't changed anything in /etc/ginn/wishes.xml. Have seen that  some people have multitouch in the xinput output. I'm currently running  ubuntu 11.04. Have also tried to get this working with 10.04 and 10.10.

Best regards

---

