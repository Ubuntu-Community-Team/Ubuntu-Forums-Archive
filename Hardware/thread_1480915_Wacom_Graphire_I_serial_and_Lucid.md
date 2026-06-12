---
title: "Wacom Graphire I serial and Lucid"
date: 2010-05-12
forum: Hardware
---

### Post by gwi on 2010-05-12
I have a Wacom Graphire I serial tablet, that was working well.
After installing Lucid it stopped working completely. The tablet is not even listed as an X input device.

[**_Here_**]("http://ubuntuforums.org/showthread.php?p=6546012") I read that serial Wacom tablets are no longer supported. If this is true, this is a big &**&@#$ (which I would expect from a commercial OS company, but not in the open source world)! :mad:

Is there some kind of workaround possible?

---

### Post by Favux on 2010-05-12
Hi gwi,

I don't know about the workaround.  Maybe adding the serial Wacom sections to xorg.conf and otherwise setting it up like old times, serial conf etc.?  Without support in the code I'm dubious.

The only update on serial tablets I've seen is the answer to this post:  [https://sourceforge.net/mailarchive/forum.php?thread_name=w2v167e8a331005091751zc6376389v19e9f5bc574872a7%40mail.gmail.com&forum_name=linuxwacom-discuss](https://sourceforge.net/mailarchive/forum.php?thread_name=w2v167e8a331005091751zc6376389v19e9f5bc574872a7%40mail.gmail.com&forum_name=linuxwacom-discuss)

So that's interesting.  It looks like it wasn't a policy change but a lack of developer resources.  My guess is Peter thought serial tablets are old enough that there aren't that many still around so why spend the time adding serial support for xf86-input-wacom?  Many things with higher priority to do first.

---

### Post by Favux on 2010-05-12
Hi gwi,

Just posted on linuxwacom-discuss is a link to a patch that purports to add serial wacom back into xf86-input-wacom!  It was made against 0.10.6.  It's by Sebastian Berthold and company.  See:  [https://sourceforge.net/mailarchive/forum.php?thread_name=4BEB198B.9030809%40sleif.de&forum_name=linuxwacom-discuss](https://sourceforge.net/mailarchive/forum.php?thread_name=4BEB198B.9030809%40sleif.de&forum_name=linuxwacom-discuss)  So you should be able to download xf86-input-wacom, apply the patch, compile it and enable your tablet.  How about that!

The original patch the new patch is based on is here on Nuclear's blog:  [http://codelab.wordpress.com/2010/02/21/wacom-hacking/](http://codelab.wordpress.com/2010/02/21/wacom-hacking/)

I downloaded both and looked at them.  Looks like the real deal.

---

### Post by turquoiserabbit on 2010-05-13
Hi Favux,

I'm in the same boat as gwi, upgraded to lucid and now no serial tablet.. I got as far as downloading the source for xf86-input-wacom, and the patch file but all the sites I've been on that explain how to apply a patch file have been frustratingly vague. Any chance you could give a short step by step?

I mean, my tablet is ancient by tech standards, but if I can save myself from having to spend 400 bones on a new one just to get it working with lucid that would be wonderful:).


*edit* Having the patch file in the same folder as the xf86-input-wacom-0.10.5 folder and running it results in "hunk failed" about 20 times.*edit*
*edit2* got it to succeed just had to rename the xf86-input-wacom_0.10.5 folder to just xf86-input-wacom. Now all I have to do is compile and test. I'll post if it works *edit2*

---

### Post by Favux on 2010-05-13
Hi turquoiserabbit,

Welcome to Ubuntu forums!

I can sure understand not wanting to buy a new tablet when you already have a perfectly good one.

OK, copy or move the patch into the downloaded xf86-input-wacom file, whether the unpacked 0.10.6 tar or the git clone.  Then, for e.g., in a terminal:
```
cd Desktop

cd xf86-input-wacom-0.10.6

patch -p1 < xf86-input-wacom_git-20100511.patch
```
I'm pretty sure that will work for you.

Hope this helps.

---

### Post by turquoiserabbit on 2010-05-13
Well I managed to patch successfully, and compile and install but my tablet still isn't working. I'm getting this in my /var/log/Xorg.0.log:

```

(II) LoadModule: "wacom"
(WW) Warning, couldn't open module wacom
(II) UnloadModule: "wacom"
(EE) Failed to load module "wacom" (module does not exist, 0)
```

my xorg.conf still has the settings in it from before I updated to lucid. The wacom entries were commented out by the update, but I uncommented them all in again. Still nothing.

Did you get it working gwi?

---

### Post by Favux on 2010-05-14
Hi turquoiserabbit,

Well it shouldn't be talking about the wacom.ko, which is the usb kernel driver/module so it must be talking about the wacom_drv.so which is the X driver.  I think it should be located at /usr/lib/xorg/modules/input/.  I'd check and see if the install placed it there.  If not copy it there from the source code.  If there weren't any errors on the compile it should have been made.

---

### Post by royleith on 2010-05-22
@Favux

I have a Wacom Intuos serial A4 tablet which used to work well on Kubuntu with the modified xorg.conf file. Since Kubuntu 10.4 I have been chasing your useful comments all over the interweb and have (after countless stumbles) done the following,

reinstalled xserver-xorg-input-wacom

sudo apt-get update
sudo apt-get build-dep xf86-input-wacom

extracted xf86-input-wacom-0.10.6 and copied the patch into the folder
successfully run the patch

I had to do a new install of Kubuntu, so my old xorg.conf file was lost. However, I had the old wacom entries saved elsewhere. I created a new xorg.conf based on xorg.conf.failsafe.

I logged-out and restarted the xserver.

I won't bore you with the resulting xwindow disaster, but I did get xwindow running.

The tablet did not work, but /var/log/Xorg.0,log contains the following;

(II) XKB: generating xkmfile /tmp/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
(**) Option "Device" "/dev/ttyS0"
(**) Option "SendCoreEvents"
(**) stylus: always reports core events
(II) XINPUT: Adding extended input device "stylus" (type: STYLUS)
(**) Option "StopBits" "1"
(**) Option "DataBits" "8"
(**) Option "Parity" "None"
(**) Option "Vmin" "1"
(**) Option "Vtime" "10"
(**) Option "FlowControl" "Xoff"
(WW) stylus: Waited too long for answer (failed after 3 tries).
(WW) stylus: Waited too long for answer (failed after 3 tries).
(WW) stylus: Waited too long for answer (failed after 3 tries).
(II) stylus: serial tablet id 0x90.
(EE) Couldn't init device "stylus"
(II) UnloadModule: "wacom"
(**) Option "Device" "/dev/ttyS0"
(**) Option "SendCoreEvents"
(**) eraser: always reports core events
(II) XINPUT: Adding extended input device "eraser" (type: ERASER)
(**) Option "StopBits" "1"
(**) Option "DataBits" "8"
(**) Option "Parity" "None"
(**) Option "Vmin" "1"
(**) Option "Vtime" "10"
(**) Option "FlowControl" "Xoff"
(WW) eraser: Waited too long for answer (failed after 3 tries).
(WW) eraser: Waited too long for answer (failed after 3 tries).
(WW) eraser: Waited too long for answer (failed after 3 tries).
(II) eraser: serial tablet id 0x90.
(EE) Couldn't init device "eraser"
(II) UnloadModule: "wacom"
(**) Option "Device" "/dev/ttyS0"
(II) UnloadModule: "wacom"

So, the serial wacom driver seemed to find the tablet, but was unable to communicate with it. I am wondering if it is something to do with the serial port being set to Xon/off flow control. 

I will do a reboot to see if that helps, but my previous attempts with homebrew xorg.conf files resulted in a lockup. I am still very encouraged by the progress so far.

Regards
Roy Leith

---

### Post by Favux on 2010-05-22
Hi royleith,

Nice work!  :)

First we should probably fix your xorg.conf so you don't have any more lock ups.  Can you post it?

The serial patch was rejected because it disables ISD4 support.  But you can tell the LWP dev.s were excited about it because they took the time to comment on it within a few days.  Hopefully the submitter and crew are working on the changes suggested.  Haven't seen a response yet.

So one thing to do is make sure that ISD4 is commented out in xorg.conf and/or in the 10-wacom.conf serial snippet.  Just in case, even though the patch disables it.
> I am wondering if it is something to do with the serial port being set to Xon/off flow control.

Could be, and there are some other parameters you can play with.  But I'd leave everything default for now until we get the xorg.conf fixed.

---

### Post by royleith on 2010-05-22
Hi Favux,

Promise not to laugh!

Section "Device"
	Identifier	"Configured Video Device"
	Driver		"fbdev"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "stylus"
#  Option        "Device"        "/dev/input/wacom" # USB ONLY?
  Option        "Device"        "/dev/ttyS0"      # SERIAL ONLY
  Option        "Type"          "stylus"
#  Option        "ForceDevice"   "ISDV4"           # Tablet PC ONLY
#  Option        "USB"           "on"               # USB ONLY
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "eraser"
#  Option        "Device"        "/dev/input/wacom" # USB ONLY?
  Option        "Device"        "/dev/ttyS0"      # SERIAL ONLY
  Option        "Type"          "eraser"
#  Option        "ForceDevice"   "ISDV4"           # Tablet PC ONLY
#  Option        "USB"           "on"               # USB ONLY
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "cursor"
#  Option        "Device"        "/dev/input/wacom" # USB ONLY?
  Option        "Device"        "/dev/ttyS0"      # SERIAL ONLY
  Option        "Type"          "cursor"
#  Option        "ForceDevice"   "ISDV4"           # Tablet PC ONLY
#  Option        "USB"           "on"               # USB ONLY
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "pad"
#  Option        "Device"        "/dev/input/wacom"    # USB ONLY
  Option        "Device"        "/dev/ttyS0"         # SERIAL ONLY
  Option        "Type"          "pad"
#  Option        "USB"           "on"                  # USB ONLY
EndSection

# Uncomment the following section if you you have a TabletPC that supports touch
# Section "InputDevice"
#  Driver        "wacom"
#  Identifier    "touch"
#  Option        "Device"        "/dev/ttyS0"       # SERIAL ONLY
#  Option        "Device"        "/dev/input/wacom" # USB ONLY
#  Option        "Type"          "touch"
#  Option        "ForceDevice"   "ISDV4"            # Serial Tablet PC ONLY
#  Option        "USB"           "on"               # USB ONLY
# EndSection

Section "ServerLayout"
  Identifier    "Default Layout"
  Screen        "Default Screen"
  InputDevice   "stylus"  "SendCoreEvents"
  InputDevice   "eraser"  "SendCoreEvents"
  InputDevice   "cursor"  "SendCoreEvents" # For non-LCD tablets only
#  InputDevice   "pad"                      # For Intuos3/CintiqV5/Graphire4/Bamboo tablets
# InputDevice   "touch"   "SendCoreEvents" # Only a few TabletPCs support this type
EndSection

The lockups and failures are all to do with the video. The log file reports loads of what seem to be framebuffer failures and xwindow either does not start up, but will start with startx, or it loads incorrectly configured. In both cases, it loads with the highest resolution setting and with no alternative resolutions and it also loads with a refresh rate of 0Hz! As a rescue mode, it is fine (when wearing glasses), but I will have to find a way of getting the default to work under normal startup conditions.

I seem to remember there is a way of forcing the generation of a default xorg.conf file, but I cannot remember the command.

One last thing for those who have tried and not got this far. Sourceforge is proudly announcing the xf86-input-wacom-0.10.6 for download and then delivering 0.10.5. I gave that a try, but some patch modules failed. I may have still been missing some dependancies, though.

And, finally, its an Intuos graphics pad I am trying to get to work rather than a tablet computer.

Regards
Roy Leith

---

### Post by Favux on 2010-05-22
Alright, I know you have a stylus and eraser.  How many buttons on the stylus?  Do you have a Wacom tablet mouse?  Does your Wacom Intuos serial A4 tablet have a pad?  A cluster of buttons on the tablet?

I believe the command is:
```
sudo dpkg-reconfigure -phigh xserver-xorg
```
but I wouldn't run it yet.

What chipset is the 'Driver "fbdev"' for?  Is that the video chipset Intel licensed?  Any chance you made a back up of the original xorg.conf or was there no xorg.conf when you started and you made one?

---

### Post by royleith on 2010-05-23
Hi Favux,

I tried something else. I logged in, in console mode as root. I then tried,

X -configure

Which created a file called xorg.conf.new in /root. I added the wacom serial pad lines and put it in /etc/X11 as xorg.conf.

I have tried this method to create an xorg.conf on two machines and, in both cases, the file stops xwindow from initiating.

When booting from cold, the system locks on the Kubuntu animated splash screen.

The file is rather long so I provide it as an attachment.

---

### Post by royleith on 2010-05-23
Hi Favux,

I have one, 2-way button on the pen i.e. either the top or the bottom of the elongated button can be clicked which is seen by the software as two separate buttons.

I have a tablet mouse, as well.

There are no hardware buttons on the pad, itself. It is the original Intuos design.

There was no xorg.conf as this was a fresh install of Lucid. There is, however, an xorg.conf.failsafe file and this was the one I used as the basis for an xorg.conf file. I suspect that the fbdev is to try to get a high resolution, frame-buffer display under failsafe conditions. If the normal drivers load correctly, I don't think the failsafe file would be used. IIRC, the computer has a fairly old and lowly ATI video card in it.

Would your,

sudo dpkg-reconfigure -phigh xserver-xorg

actually generate an xorg.conf file? I suspect it no longer does so in Lucid. In my latest email in this thread I mentioned the 

X -configure

command which was suggested for Lucid in another forum. However, it produces an xorg.conf.new file in /root which fails completely when transferred to /etc/X11 as xorg.conf. The modified version with the wacom additions is attached to my previous message. I can, at least, get xwindow up and running after a fashion with my xorg.conf.failsafe derivative, so perhaps some small tweaks might do the trick. I notice the video settings are more or less referring to other init settings and this was the sort of thing that went on in 9.10. xorg.conf.

I wonder if turquoiserabbit might be good enough to send us a copy of his xorg.conf file as a guide. I suspect that if he gets a true version of xf86-input-wacom-0.10.6 rather than 0.10.5 he might be close to success, especially if he starts from a clean slate, as I did.

Regards
Roy Leith

---

### Post by Favux on 2010-05-23
Hi royleith,

OK, X-configure made a mess.  Your first xorg.conf looked better.  I tried to clean out most of the cruft.

It looks like you are using Xorg's noveau driver for nvidia.  Was there even an xorg.conf on your fresh Lucid install?  And while noveau has come a long ways the proprietary nvidia drivers are still better.  Do you have an objection to them?

So let's concentrate on fixing video, that may be what is breaking X.  As always backup your working xorg.conf and be prepared to restore it from the command line if we break X.

---

### Post by royleith on 2010-05-24
Hi Favux,

Because I had problems with an upgrade, I installed Lucid from scratch. There is no xorg.conf in the new install.

I thought I was using the non-free video driver. When I found that I had not installed it on this distribution (there is both Ubuntu Studio and Kubuntu on this computer) I installed it. When I checked, it had added an xorg.conf file for the non-free driver. Since it required a restart, I took the opportunity to add my serial wacom lines and then restart.

xwindow did not start, but I could login and start xwindow with startx. That was fine, but the wacom did not work. I tried with your xorg.conf, but xwindow would not start and gave the warning that 'no screens were found'. I have seen this before in my experiments so it was not a surprise.

Then I took the xorg.conf for the proprietary driver and added your lines for the serial wacom. The computer booted normally into xwindow, but the wacom did not work. I checked Xorg.0.log and there were no references to the wacom driver. I tried with the lines at the start and at the end of the xorg.conf file with the same result.

Only with the following added does a reference to the wacom driver appear;

> 
Section "ServerLayout"
  Identifier    "Default Layout"
  Screen        "Default Screen"
  InputDevice   "stylus"  "SendCoreEvents"
  InputDevice   "eraser"  "SendCoreEvents"
EndSection

I added all the serial wacom lines to the end of the xorg.conf file since I guessed that the screen had to be set up before the wacom driver was added.

As a final check, I changed from serial port 0 to serial port 1, but with no change.

In summary, I now have an xorg.conf file that will start Lucid correctly with the non-free video driver. The wacom driver is not detected unless the ServerLayout section is added. The wacom pad does not seem to be responding to attempts to set up serial communications.

I attach xorg.conf and Xorg.0.log.

Regards
Roy Leith

The xorg.conf and the

---

### Post by Favux on 2010-05-24
Good, video is straightened out.

Correct, need "ServerLayout" for Wacom detection.  But with Xserver 1.7 I don't think you need "SendCoreEvents" any longer.  Plus I added your cursor (Wacom tablet mouse) back in.  You can check Xorg.0.log and see if you're still getting the same errors, and now also with cursor.

This should be the correct Lucid xorg.conf for you.

We should see what the 10-wacom.conf in /usr/lib/X11/xorg.conf.d/ looks like.

---

### Post by royleith on 2010-05-25
Hi Favux,

I am just about to try the modified xorg.conf, but I thought I would report another little experiment I carried out. I was hoping to generate an xorg.conf that defaulted to the free driver for those who want free-only drivers or do not use an NVidia card.

I uninstalled the non-free driver. That promptly deleted xorg.conf. 

It looks as though we need to look elsewhere for an xorg.conf file for non-nvidia users.

Regards
Roy Leith

---

### Post by royleith on 2010-05-25
Hi, Favux,

I tried your xorg.conf and it drops back to a console login, as before. I log in as root and start xwindow and the wacom is not working (the driver is still not communicating with the wacom). I attach Xorg.0.log.txt to show this.

I then searched for 10-wacom.conf and neither folder nor file were there. I copied the new version from the HowTo (10-wacom.conf.txt) and it failed in much the same way (Xorg.0.log.xorg.conf.d.txt). However, as long as 10-wacom.conf was in place, it disabled the mouse and the keyboard while in xwindow. You can see in the log file that it does not load the KVM input devices. With the mouse and keyboard directly connected to the computer and the working xorg.conf with just the screen settings in place, it does the same thing: it disables the mouse and keyboard. I have not attached the log file as it does not add new information.

With some playing with a rescue CD and midnight commander I am now back to normal. Can you suggest a Linux equivalent to the Windows Hyperterminal as I would like to see if I can set up terminal communication with the wacom and see what async parameters make it happy. If you know how to set the async parameters in the xwindow, wacom, serial driver, that would also be a help.

Thanks for your support. I can't believe we are too far away from getting it working.

Regards
Roy Leith

---

### Post by Favux on 2010-05-25
Hi royleith,

First the good news.  Sebastian Berthold resubmitted the serial patch as two patches yesterday.  He's thinks he's fixed some of the issues the LWP dev.s pointed out but needs their help on a couple more:  [https://sourceforge.net/mailarchive/forum.php?thread_name=4BFAD268.7010608%40sleif.de&forum_name=linuxwacom-discuss](https://sourceforge.net/mailarchive/forum.php?thread_name=4BFAD268.7010608%40sleif.de&forum_name=linuxwacom-discuss)  So the serial fix is still under active development!  Again it looks like the patches apply to xf86-input-wacom 0.10.6 or the current git.

I don't understand how the xorg.conf I posted could have broken X.  All it did was add the cursor line to "ServerLayout" and remove SendCoreEvents.  I don't think Xserver 1.7 needs SendCoreEvents, and in earlier Xservers it would just have disabled communication to the devices, not broken X.  So it must be the cursor that broke X.  Which seems to imply a problem with the original serial patch.

Further supporting a problem with the serial patch is the problems you had with 10-wacom.conf.  I'm pretty sure none of that would have happened with the standard wacom drivers.

Yes I know how to set some of the serial parameters.  Let me introduce you to the [Linux Serial "bible"]("http://tldp.org/HOWTO/Serial-HOWTO.html").

---

### Post by royleith on 2010-05-25
Hi Favux,

I think there might be a problem with xf86-input-wacom 0.10.6. When I clicked on the download from sourceforge, 0.10.5 actually downloaded. I found my version of xf86-input-wacom 0.10.6 on a Japanese site and it extracted to a folder named xf86-input-wacom 0.10.6. However, I notice that the log file says,

(II) Module wacom: vendor="X.Org Foundation"
	compiled for 1.7.6, module version = 0.10.5
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 7.0

Even though the patch was successful, I am beginning to suspect that the download was the wrong version. I shall have another search, tomorrow. Thanks for the two links. I will follow those up, as well.

Regards
Roy Leith

---

### Post by Favux on 2010-05-25
That could be.  Here's the download sites for the xf86-input-wacom tars:  [https://sourceforge.net/projects/linuxwacom/files/](https://sourceforge.net/projects/linuxwacom/files/)  And to clone the git see Appendix 5 on the [linuxwacom HOW TO]("http://ubuntuforums.org/showpost.php?p=6546012&postcount=1").

---

### Post by royleith on 2010-05-26
Hi Favux,

I downloaded the correct xf86-input-wacom, extracted, patched with original patch file, compiled and then copied wacom_drv.so to the correct location.

I also remembered what you wrote about ISD4 and commented out the forcedevice command in 10-wacom.conf.

The summary is that the driver will not now load,

> (II) LoadModule: "wacom"
(II) Loading /usr/lib/xorg/modules/input/wacom_drv.so
dlopen: /usr/lib/xorg/modules/input/wacom_drv.so: undefined symbol: gWacomSerialDevice
(EE) Failed to load /usr/lib/xorg/modules/input/wacom_drv.so
(II) UnloadModule: "wacom"

Any thoughts on how to define that symbol? Perhaps it is a line in the source code.

The new module is much bigger than the original so I think it must be the .6 version and not the .5. Is there a linux command to check the version number of an xmodule?

As you will see, 10-wacom.conf still disables the mouse and keyboard whether or not xorg.conf has the wacom driver lines. I am wondering if it is an either/or choice and that I need to use the xorg.conf solution in order to use the non-free nvidia driver. My last experiment will be to see what happens if I remove the xorg.conf file and leave the 10-wacom.conf file in place.

Thanks for the link to the Linux-serial-HowTo. I used a terminal program and happily watched the wacom send signals on TTYS0 without flow control. If flow control is set by the new driver then this needs to be changed, but getting the driver to load is the first issue.

Regards
Roy Leith

---

### Post by royleith on 2010-05-26
Hi Favux,

I tried booting without xorg.conf, but with 10-wacom.conf and the keyboard and mouse were again disabled. There is one possibility. When the serial wacom stopped working, I installed the drivers for a USB wacom Bamboo. I am wondering if that is getting in the way of the serial pad. I will consider restoring an earlier version of Lucid and starting the serial driver patching procedure from scratch. 

I think that's it for today while I wonder about that undefined symbol in the patched driver.

Regards
Roy Leith

---

### Post by TheW4rden on 2010-05-26
> **royleith said:**
> 
I think that's it for today while I wonder about that undefined symbol in the patched driver.


I think you need to do a "autoreconf" after applying the patch and then do the "configure" and "make".

I'm still getting the:

stylus: Waited too long for answer (failed after 3 tries).

problem with the lastest patches.

---

### Post by TheW4rden on 2010-05-26
I had forgotten to add the "Option" "ForceDevice" "SERIAL" to the Xorg.conf (with latest patches). All working now.

---

### Post by Favux on 2010-05-26
Hi TheW4rden,

Outstanding!  So with the latest patches all you needed to do was add:
```
Option "ForceDevice" "SERIAL"
```
to (I'm assuming) xorg.conf and it works with the latest patches.  Cool.  Or did you add that to the serial snippet in 10-wacom.con?

Also which model of serial tablet do you have?

---

### Post by turquoiserabbit on 2010-05-27
Hey all,

Sorry, I've been following this thread but I didn't have anything useful to add since I needed to use my tablet immediately, so I just did a clean install of karmic koala. I'd had it working on that guy just fine and although I'm still interested in potentially keeping current with distro upgrades, from what I saw, lucid didn't offer me anything new that I don't have with Karmic.

Sorry I can't be of more help, maybe I'll do a lucid install on a fresh partition to test the wacom waters once I get the time.

Sounds like at least theW4rden got a serial tablet working :). Is there a way still to configure the pen buttons? Because without being able to do that it makes my tablet efficiency drop to almost un-usable anyway.

---

### Post by royleith on 2010-05-27
WooHoo Favux!

I can, now, report that the Wacom Intuos A4 serial pad (the first series) is working, following the advice from TheW4rden.

The stylus, eraser and cursor all appear to work. The worthless pad mouse controls the cursor position, but no buttons work. This is an advantage as it is horrible. 

The process I used was,

apt-get build-dep xf86-input-wacom
cd xf86-input-wacom-0.10.6
patch -p1 < xf86-input-wacom_git-20100511.patch
autoreconf
./configure
make
copy wacom_drv.so from the hidden .libs folder to 
/usr/lib/xorg/modules/input/wacom_drv.so

I attach the xorg.conf I used, but it is specific to the non-free driver for nvidia cards. 

No file 10-wacom.conf was used in wacom.conf.d.

This still leaves a problem for the non-nvidia video card users or those who wish to use the 'free' driver as no xorg.conf file is available for modification.

I notice that the X -configure command may not produce a usable xorg.conf file, but it does produce the necessary Screen, Module and Device values for xorg.conf and I would have thought a little experimentation with the  file I am using and the output of that command might generate a working file for those without a starting point for xorg.conf.

Many thanks to Favux and TheW4rden.


Regards
Roy Leith

---

### Post by Favux on 2010-05-27
Hi royleith,

Fantastic!  :)

So you still used the first patch.  So both sets worked.  I was surprised to see:
```
Option "ForceDevice" "SERIAL"
```
works in "ServerLayout".  I thought that would have to be added to each Wacom section, namely stylus, eraser, and cursor.  Learn something new every day.

Not a problem for folks with non-proprietary nvidia or whatever.  They just won't have video sections in their xorg.conf.  They'll just add the Wacom sections and a "ServerLayout" like:
```
Section "ServerLayout"
  Identifier	"X.org Configured"
  InputDevice   "stylus"
  InputDevice   "eraser"
  InputDevice   "cursor"
EndSection
```
To create the xorg.conf file all they need to do is:
```
gksudo gedit /etc/X11/xorg.conf
```
And then they can experiment where to add the 'Option "ForceDevice" "SERIAL"'.  Personally I would have thought like:
```
Section "InputDevice"
  Driver        "wacom"
  Identifier    "stylus"
#  Option        "Device"        "/dev/input/wacom"
  Option        "Device"        "/dev/ttyS0"      # SERIAL ONLY
  Option        "Type"          "stylus"
  Option "ForceDevice" "SERIAL"
#  Option        "ForceDevice"   "ISDV4"           # Tablet PC ONLY
EndSection
```
Again, great work!

---

### Post by babuhumi on 2010-05-30
I found another post [http://ubuntuforums.org/showthread.php?t=1485180](http://ubuntuforums.org/showthread.php?t=1485180) discussed the problem in fujitsu T4010. I just followed his instruction and the problem was solved on my fujitsu T4210. However, everything goes back once I reboot the pc. The pen works properly if I restart X 

code
sudo /etc/init.d/gdm restart
Any better way to solve it?

---

### Post by Favux on 2010-05-30
Hi babuhumi,

I saw that post too.  To me it looks like the coordinates are in the wrong section, the n-trig.  Maybe that's the problem?  If you want to post your 10-wacom.conf and I'll see if I can "fix" it.

---

### Post by babuhumi on 2010-05-30
Thank you for you help. The file is attached. Now I run my pc in this way--> reboot(pen works poor)-->restart X server--> tablet pen works fine.

---

### Post by Favux on 2010-05-30
Hi babuhumi,

And before I forget, welcome to Ubuntu forums!

Alright, I switched the coordinates to the serial tablet snippet/section where I think they should be.  We'll see.

By the way other Fujitsu's report having to do what you are doing to get the stylus to work.  When we looked at their Xorg.0.log in /var/log it turned out the Wacom driver wasn't picking up the digitizer on boot but was picking it up after the restart of X.  We never figured out why, but at least it was working.  The LWP (linux wacom project) has added some Fujitsu support in recently.  I'm not sure though that it is enough to make it worthwhile to compile xf86-input-wacom 0.10.6 or clone the git.

---

### Post by babuhumi on 2010-05-30
Thank you Favux!! It is wonderful we have people like you to help our beginner~ 

As you suggested, I just trim my 10-wacom-conf. And use my t4210 in this way-->boot-->restart X-->enjoy tablet-->avoid rebooting....

---

### Post by edam on 2010-09-02
Hi Guys,

I've finally got round to trying to get my serial Intuos working again, but I'm stuck. I wondered if anyone could shed some light on the problem?

I've applied the second patch (the one in two parts) to xf86-input-wacom-0.10.6, rebuilt wacom_drv.so and copied that to /usr/lib/xorg/modules/input. I can also use wacdump (the one from linuxwacom-0.8.4-4 worked) which detects my serial Intuos just fine on /dev/ttyUSB0 (a usb-to-serial adapter). All good so far.

Then, the Xorg.0.log shows this (repeated 3 times, for stylus, eraser, cursor):
```
(**) Option "Device" "/dev/ttyUSB0"
(EE) stylus: wcmDeviceTypeKeys unable to ioctl USB key bits.
(**) stylus: always reports core events
(II) XINPUT: Adding extended input device "stylus" (type: STYLUS)
(**) Option "StopBits" "1"
(**) Option "DataBits" "8"
(**) Option "Parity" "None"
(**) Option "Vmin" "1"
(**) Option "Vtime" "10"
(**) Option "FlowControl" "Xoff"
(EE) stylus: usbDetect: can not ioctl version
(EE) stylus: wcmOpen found undetectable  /dev/ttyUSB0 
(EE) Couldn't init device "stylus"
(II) UnloadModule: "wacom"
```
Any ideas what's causing this?

Edit: Also, has there been any more activity in restoring support for serial Wacoms? The [linuxwacom-discuss thread]("http://sourceforge.net/mailarchive/forum.php?thread_name=4BEB198B.9030809%40sleif.de&forum_name=linuxwacom-discuss") seems to have ended in May and I can't find any more info on it.

---

### Post by Favux on 2010-09-02
Hi edam,

What does your 10-wacom.conf look like?
> Also, has there been any more activity in restoring support for serial Wacoms?
Unfortunately I haven't seen anything.

---

### Post by edam on 2010-09-02
Hi Favux, thanks for the quick reply!

I've attached my 10-wacom.conf and my xorg.conf. I should have done that in the first place!

> **Favux said:**
> Unfortunately I haven't seen anything.
That's a shame.  :o(

---

### Post by Favux on 2010-09-02
Alright, we probably should start by commenting out the Wacom sections in xorg.conf along with the Wacom lines in "ServerLayout".  You should use either xorg.conf or wacom.conf, not both.  Then reboot.

Then check what's happening in Xorg.0.log.  I'm guessing the attempt by the wacom driver to attach is due to the xorg.conf.  If so then try changing the serial snippet from:
```
Section "InputClass"
	Identifier "Wacom serial class"
	MatchProduct "Serial Wacom Tablet"
	Driver "wacom"
#	Option "ForceDevice" "ISDV4"
EndSection
```
to
```
Section "InputClass"
	Identifier "Wacom serial class"
	MatchProduct "Serial Wacom Tablet"
	MatchDevicePath "/dev/input/ttyUSB*"
	Driver "wacom"
#	Option "ForceDevice" "ISDV4"
EndSection
```

---

### Post by LostAndFound on 2010-10-23
Thanks for all the info above, and in particular Favux.

I was able to get my Intuos 2 Serial tablet to work on Ubuntu 10.4, but upon upgrade to 10.10 the tablet no longer works. I tried various patches against various downloads but X always fails (using previously working xorg.conf file). I think the X log shows that the serial tablet is not found.

Has anyone got their serial tablet to work with 10.10? If so, which patch (if any) was needed against which package?

I assume that the xf86-input-wacom package is needed for serial tablets rather than linuxwacom which is a kernel module for USB tablets? - Is that right?

---

### Post by Favux on 2010-10-23
Hi LostAndFound,

It looks like you can't apply the patches to any xf86-input-wacom higher than 0.10.6.  At least that's what JRBASTIEN found.  He also supplies the patch set he used:  [http://ubuntuforums.org/showthread.php?t=1593973](http://ubuntuforums.org/showthread.php?t=1593973)  Since Maverick has 0.10.8 as the default I guess you have to try overwriting it with the 0.10.6 tar.

I don't think I've seen anyone post about having success on Maverick yet.

---

### Post by indri on 2010-11-02
Hallo,
thanks for this thread!
I have Wacom Intuos (1) Serial connected to /dev/ttyS0 and  my tablet is not working.
My system is 10.04 LTS Lucid Lynx (64bit). X -version  is X.Org X Server 1.7.6
Core is 2.6.32-25-generic x86_64.
I downloaded xf86-input-wacom-0.10.6.tar.bz2 and xf86-input-wacom_git-20100511.patch.
Then: 
$ patch -p1 -i xf86-input-wacom_0.10.6-git-20100511.patch
$ aclocal && automake && autoconf
$ ./configure
$ make
$ sudo make install
$ ./wacdump /dev/ttyS0   in  /linuxwacom-0.8.8-10/prebuilt/64  show perhaps correct values from tablet.

My /etc/X11/xorg.conf and parts of /var/log/Xorg.0.log are in attachmenst.
After Ubuntu reboot is in Xorg.0.log: (EE) Couldn't init device "stylus" ...
And tablet is not working.
After reboot only X is there: (--) stylus: Wacom General ISDV4 tablet speed=38400 ...  tilt=disabled  ... It is completly wrong (ISDV4, speed, tilt).

I have checked-out some varians of xorg.conf and now I don't know what to do better.

Edit: $ ./wacdump /dev/ttyS1 -> $ ./wacdump /dev/ttyS0

---

### Post by Favux on 2010-11-02
Hi indri,

Welcome to Ubuntu forums!

Do you know what speed your tablet is suppose to be at?

Try the attached xorg.conf and see if it makes any difference.

This thread might also be of interest:  [http://ubuntuforums.org/showthread.php?t=1593973](http://ubuntuforums.org/showthread.php?t=1593973)

---

### Post by indri on 2010-11-02
Hi Favux, nice to see your answer.

> **Favux said:**
> Do you know what speed your tablet is suppose to be at?
I think it should be 19200kBd. I will verify it.

> **Favux said:**
> Try the attached xorg.conf and see if it makes any difference.
Some litle difference after reboot X: in Xorg.0.log isn't line with ISDV4. So your variant could be better. (But tablet is not working.)

> **Favux said:**
> This thread might also be of interest:  [http://ubuntuforums.org/showthread.php?t=1593973](http://ubuntuforums.org/showthread.php?t=1593973)
When I see [Xorg.0.logFavuxHelp.txt]("http://ubuntuforums.org/attachment.php?attachmentid=172073&d=1286882953") there is interesting module version = 0.10.6:
(II) Loading /usr/lib/xorg/modules/input/wacom_drv.so
(II) Module wacom: vendor="X.Org Foundation"
    compiled for 1.7.6, module version = 0.10.6
    
In my Xorg.0.log is module version = 0.10.5 ...?
Maybe I have wrong sources. Archive xf86-input-wacom-0.10.6.tar.bz2 is from [http://sourceforge.net/projects/linuxwacom/files/](http://sourceforge.net/projects/linuxwacom/files/) .

Patch proces was with some notes:
.../xf86-input-wacom-0.10.6$ patch -p1 -i xf86-input-wacom-git-20100511.patch 
patching file src/Makefile.am
patching file src/wcmConfig.c
patching file src/wcmISDV4.c
patching file src/wcmSerial.c
patching file src/wcmSerial.h
patching file src/wcmUSB.c
patching file src/wcmValidateDevice.c
Hunk #1 succeeded at 542 (offset -72 lines).
patching file src/xf86Wacom.c
Hunk #1 succeeded at 956 (offset 6 lines).
patching file src/xf86WacomDefs.h
Hunk #3 succeeded at 273 (offset -11 lines).
Hunk #4 succeeded at 354 (offset -11 lines).
Hunk #5 succeeded at 423 (offset -12 lines).
patching file src/xf86Wacom.h
Hunk #1 succeeded at 52 (offset 2 lines).
Hunk #2 succeeded at 107 (offset 2 lines).
Hunk #3 succeeded at 137 (offset 2 lines).


Other interesting in [Xorg.0.logFavuxHelp.txt]("http://ubuntuforums.org/attachment.php?attachmentid=172073&d=1286882953") is line: (**) Option "BaudRate" "9600".
In my Xorg.0.log isn't "BaudRate" information.
Parts of /var/log/Xorg.0.log are in attachmenst.

---

### Post by Favux on 2010-11-02
If I recall correctly he verified the last xf86-input-wacom version the patch set worked on was 0.10.6.  The reason that's important is that 0.10.5 was an early version and there have been a lot of fixes and improvements since.  It's on 0.10.8 now and 0.10.9 is about to be released.
> I think it should be 19200kBd. I will verify it.
Could you, that's what I'm waiting for.

---

### Post by indri on 2010-11-02
> **Favux said:**
> If I recall correctly he verified the last xf86-input-wacom version the patch set worked on was 0.10.6.  The reason that's important is that 0.10.5 was an early version and there have been a lot of fixes and improvements since.  It's on 0.10.8 now and 0.10.9 is about to be released.
I downloaded 0.10.6 - I will check my downloaded files.

> **Favux said:**
> Could you, that's what I'm waiting for.
Speed is not 19200Bd - I'm sorry.

I connected 2 ports in my PC and now I see init sequence.

Speed is 9600Bd, 8bits, no parity, 1 stop bit.
Init sequence, [hex], <- PC2Wacom, -> Wacom2PC:

<- [EC FD 10 FE 91 0D]
<- $[24]  [0D]
<- #[23]  [0D]  [0D]
<- SP[53 50]  [0D]
<- ~#[7E 23]  [0D]
-> ~#GD-0608-R00,V1.2-7  [0D]
<- ~C[7E 43]  [0D]
-> ~C20320,16240  [0D]
<- MT1[4D 54 31]  [0D]
<- ID1[49 44 31]  [0D]
<- IT0[49 54 30]  [0D]
<- ST[53 54]  [0D]

wacdump v0.8.2:
MODEL=Wacom Intuos 6x8               ROM=1.2-7
CLS=Serial VNDR=Wacom DEV=Intuos SUB=GD-0608-R

16240 is maxY, 20320 is maxX

---

### Post by Favux on 2010-11-02
Everything sure looks OK, it seems to be identifying and initializing the tablet correctly.  So still not working?

---

### Post by indri on 2010-11-02
Unfortunately still not working.

Now I see that patch xf86-input-wacom-git-20100511.patch is to date May 5, 2010.
My achive xf86-input-wacom-0.10.6.tar.bz2 from [http://sourceforge.net/projects/linuxwacom/files/](http://sourceforge.net/projects/linuxwacom/files/) is to date 2010-04-27 !

So I need version to May 5, 2010 from git.
I don't know why. Now I need git address and how to setup git command.
Hope google helps... :)

---

### Post by indri on 2010-11-02
On [http://sourceforge.net/apps/mediawiki/linuxwacom/index.php?title=Xf86-input-wacom](http://sourceforge.net/apps/mediawiki/linuxwacom/index.php?title=Xf86-input-wacom)
are this steps to get the latest version from git and installs it into the given prefix:
```
git clone git://linuxwacom.git.sourceforge.net/gitroot/linuxwacom/xf86-input-wacom
cd xf86-input-wacom
./autogen.sh --prefix=/usr
make && make install
```How to get version to date May 5, 2010?

---

### Post by indri on 2010-11-02
In patch is date and also time:
2010-05-11 23:17:30.000000000 +0200

---

### Post by indri on 2010-11-02
I have it from [http://linuxwacom.git.sourceforge.net/git/gitweb.cgi?p=linuxwacom/xf86-input-wacom;a=shortlog;h=refs/tags/xf86-input-wacom-0.10.7](http://linuxwacom.git.sourceforge.net/git/gitweb.cgi?p=linuxwacom/xf86-input-wacom;a=shortlog;h=refs/tags/xf86-input-wacom-0.10.7)
- line with date 2010-05-11 -> snapshot.

---

### Post by Favux on 2010-11-02
I don't know how to set the git branch date to a specific time.  I think I've read something about setting a specific commit as a cutoff.

I think your OK with your 0.10.6 source tar.  Just because the patch date is a few days later doesn't mean they used the git from that date does it?


Edit:  Cool!  You found it.

---

### Post by indri on 2010-11-03
Hi Favux,
my Wacom Intuos is working!:guitar:
Main "error" was that I thought that driver is updated when I write: sudo make install.

cd /usr/lib/xorg/modules/input
$ ls -l wacom_drv.so 
-rw-r--r-- 1 root root 84288 2010-04-22 22:59 wacom_drv.so
/git2010-05-11/xf86-input-wacom-aa95e13/src/.libs$ sudo **cp wacom_drv.so /usr/lib/xorg/modules/input/**
$ cd /usr/lib/xorg/modules/input
$ ls -l wacom_drv.so
-rwxr-xr-x 1 root root 452474 2010-11-02 23:05 wacom_drv.so
$ sudo chmod 644 wacom_drv.so

Note to compile files from git: command $ aclocal && automake && autoconf
need files config.guess, config.sub, install-sh, ltmain.sh, missing, depcomp, config.h.in .
I used copy of this files from archive xf86-input-wacom-0.10.6.tar.bz2 at [http://sourceforge.net/projects/linuxwacom/files/](http://sourceforge.net/projects/linuxwacom/files/) .

Last  questions: In old linuxwacom-0.8.8-10/prebuilt/64 was programs xidump  and mainly wacomcpl-exec for setting up tablets parameters.
In git version git2010-05-11/xf86-input-wacom-aa95e13/tools is only program xsetwacom. So **wacomcpl** is not available?

I see in your script good commands for **set 2 buttons (Button2 and Button3) on stylus**:
$ xsetwacom set stylus Button2 "3"  # right mouse click
$ xsetwacom set stylus Button3 "key ctrl v" #or other combinations: "key alt u"

**How to set double click to Button3?**
$ xsetwacom set stylus Button3 **"dblclick 1**" #still do Alt-U or **do nothing new at all**

$ xsetwacom set stylus Button3 "key backspace" #still do Alt-U
$ xsetwacom set stylus Button3 "2" #still do Alt-U
$ xsetwacom set stylus Button3 "key tab" #still do Alt-U

$ xsetwacom set stylus Button3 "key Next" #PageDown
$ xsetwacom set stylus Button3 "key Prior" #PageUp
$ xsetwacom set stylus Button3 "key shift" #may be good in GIMP...
$ xsetwacom set stylus Button3 "key ctrl" #may be good in GIMP...
$ xsetwacom set stylus Button3 "key ctrl shift" #may be good in GIMP...$ xsetwacom $ xsetwacom set stylus Mode "Relative" #as mouse
$ xsetwacom set stylus Mode "Absolute" #as tablet
...


[COLOR=RoyalBlue]**Thanks for help!**[/COLOR]

---

### Post by Favux on 2010-11-03
Outstanding work!!!  :)

> Main "error" was that I thought that driver is updated when I write: sudo make install.
It's suppose to.  So for some reason the Make file isn't updating the wacom_drv.so.  Interesting.  I wonder if that's due to the patch.  So you need to use the copy command:
```
sudo cp /xf86-input-wacom-aa95e13/src/.libs/wacom_drv.so /usr/lib/xorg/modules/input/wacom_drv.so
```
Nice find.

Right the Xorg dev. Peter dropped wacomcpl, wacdump, and xidump from xf86-input-wacom.  He feels those are user land programs and don't belong ina driver.  I gather it was a bit of a struggle to convince him to include xsetwacom, which he had to rewrite.  So that's part of the problem, xsetwacom only really matured for xf86-input-wacom with 0.10.8.

I don't believe you could ever put a double click on a stylus button.  Basically for a scroll or something like that you want to use Tom Jaeger's EasyStroke program.

---

### Post by turquoiserabbit on 2010-11-18
Quick question - would using a serial to usb adaptor make any difference? I'm considering just upgrading to a new tablet (with presumably better compatibility). But an adaptor worth a couple dollars would be better than spending the 400 or so for a brand new tablet.

---

### Post by Favux on 2010-11-18
Hi turquoiserabbit,

I'm not sure.  What I've seen with the USB adaptors is the device node changes from:
```
/dev/ttyS0
```
to
```
/dev/ttyUSB
```
I assume there's some udev rule doing that, so I'm not positive it applies to all adaptors.

---

### Post by sticmann on 2011-01-08
Hello all,
I know this is an old thread, but after following the methods listed here I've hit a wall.
> **royleith said:**
> 
(II) LoadModule: "wacom"
(II) Loading /usr/lib/xorg/modules/input/wacom_drv.so
dlopen: /usr/lib/xorg/modules/input/wacom_drv.so: undefined symbol: gWacomSerialDevice
(EE) Failed to load /usr/lib/xorg/modules/input/wacom_drv.so
(II) UnloadModule: "wacom"


I get stuck here. Following TheW4rden, I used autoreconf and I get this:
> configure.ac:25: warning: AC_INIT: not a literal: [https://bugs.freedesktop.org/enter_bug.cgi?product=xorg](https://bugs.freedesktop.org/enter_bug.cgi?product=xorg)
configure.ac:25: warning: AC_INIT: not a literal: [https://bugs.freedesktop.org/enter_bug.cgi?product=xorg](https://bugs.freedesktop.org/enter_bug.cgi?product=xorg)
configure.ac:25: warning: AC_INIT: not a literal: [https://bugs.freedesktop.org/enter_bug.cgi?product=xorg](https://bugs.freedesktop.org/enter_bug.cgi?product=xorg)
configure.ac:25: warning: AC_INIT: not a literal: [https://bugs.freedesktop.org/enter_bug.cgi?product=xorg](https://bugs.freedesktop.org/enter_bug.cgi?product=xorg)
configure.ac:25: warning: AC_INIT: not a literal: [https://bugs.freedesktop.org/enter_bug.cgi?product=xorg](https://bugs.freedesktop.org/enter_bug.cgi?product=xorg)
src/Makefile.am:28: Libtool library used but `LIBTOOL' is undefined
src/Makefile.am:28:   The usual way to define `LIBTOOL' is to add `AC_PROG_LIBTOOL'
src/Makefile.am:28:   to `configure.ac' and run `aclocal' and `autoconf' again.
src/Makefile.am:28:   If `AC_PROG_LIBTOOL' is in `configure.ac', make sure
src/Makefile.am:28:   its definition is in aclocal's search path.
autoreconf: automake failed with exit status: 1


My tablet's been down for a while and I'd love to get this thing running again. Any ideas?

Thank you,
-Joshua

EDIT: Got it. I didn't have libtool installed. I still got the AC_INIT warnings, but it all worked. Yay!

---

### Post by Favux on 2011-01-08
Hi sticmann,

Wow, great!  Sorry I took so long to respond but I'm happy you figured it out on your own.  Good job.

---

