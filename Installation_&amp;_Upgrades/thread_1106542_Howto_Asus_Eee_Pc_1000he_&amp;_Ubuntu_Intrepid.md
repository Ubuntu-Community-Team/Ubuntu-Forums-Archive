---
title: "Howto: Asus Eee Pc 1000he &amp; Ubuntu Intrepid"
date: 2009-03-25
forum: Installation &amp; Upgrades
---

### Post by dddaidl on 2009-03-25
First of all, I want to say that none of the techniques utilized are my own. I just found it a bit annoying that there wasn't a single place that I could go to get my 1000he working properly, and here is my attempt to do that and make it easier for everyone else.

I also cannot say that I am entirely adept at ubuntu, or linux in general, and there may be better ways to get the 1000he working. If there are, let me know.

This guide assumes you have the wireless chipset NE771, at least for the section on wireless. You can check this by taking the battery out and looking at the sticker. If you are not having problems with wireless, skip those steps.

So here it goes...

1. First, make sure you have Intrepid installed. Jaunty runs most things beautifully, but you cannot get the power-saving/hotkey utilities working without manually injecting eeepc modules into the jaunty kernel. I would just wait until it is stable and supported.

_EEE Kernel Install_

2. Go to [http://array.org/ubuntu/setup-intrepid.html]("http://array.org/ubuntu/setup-intrepid.html") and follow the instructions to add their repository to apt. Alternately, you could download the deb's from the site, but using apt to keep things up to date is the best way to go.

3. Run: "sudo apt-get install linux-eeepc linux-headers-eeepc" 

(The headers are necessary. Also, there is no need to install linux-eeepc-lean because of issues with compiling the updated wifi driver to fix wireless issues. If someone knows how to fix the issue, let me know!)

4. Reboot into the eeepc kernel at the grub menu. You may need to hit "esc" to access the list.

(You can make this kernel load by default if you edit "/boot/grub/menu.lst" moving the eeepc kernel section above the generic kernel)

_EEEPC Acpi Install (makes hotkeys/powersave functions work)_

5. Go to [http://sourceforge.net/project/platformdownload.php?group_id=248229]("http://sourceforge.net/project/platformdownload.php?group_id=248229") and scroll to the bottom of the page. You will see a link to download a deb of eeepc-acpi-script.

6. Install the package

(Installing this will enable all of the hotkeys and powersaving features, but only if you are running the eeepc kernel.)

_WIFI_

7. To get wifi working, you have to compile and install the latest drivers. The easiest way to do this is to go to [http://wireless.kernel.org/download/compat-wireless-2.6/]("http://wireless.kernel.org/download/compat-wireless-2.6/") and download the compat-wireless-2009-03-25.tar.bz2 or whatever the current date is.

Do not go any further at this point without rebooting into the eeepc kernel. If you go on to the next steps in the vanilla kernel, you will only be compiling and installing the drivers there. I recommend you do this to both kernels if you happen to use the vanilla kernel every once in a while. 

8. Next, go to [http://linuxwireless.org/en/users/Download]("http://linuxwireless.org/en/users/Download") and at the bottom you will see instructions to compile and install the drivers.

Once you finish the make, make install, and make unload, you can load the wireless module by typing: "sudo modprobe ath9k". This will save you a restart.

Note: Each time you upgrade your kernel, you will need to recompile the wireless drivers, at least until the drivers themselves are updated in the ubuntu repositories.

_Touchpad Toggle Fix_

9. The only hotkey that does not work at this point is the touchpad enable/disable toggle. To get this working, you will have to edit xorg as follows: *Pay attention to the sections following "##Added"

# xorg.conf (X.Org X Window System server configuration file)

Section "Device"
    Identifier    "Configured Video Device"
    Driver    "intel"
    Option    "HWCursor"    "False"
    Option "MigrationHeuristic" "greedy"
    Option "AccelMethod" "XAA"
    Option "XAANoOffscreenPixmaps" "true"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

##Added
Section "InputDevice"
    Identifier  "ETPS/2 Elantech Touchpad"
    Driver      "synaptics"
    Option      "SendCoreEvents"    "true"
    Option      "Device"        "/dev/psaux"
    Option      "Protocol"      "auto-dev"
    Option      "HorizScrollDelta"  "0"
    Option      "MaximumTapTime"        "200"
    Option      "ClickTime"     "50"
    Option      "MaxTapMove"    "320"
    Option      "MaximumDoubleTapTime"  "5"
    Option      "VertTwoFingerScroll"   "1"
    Option      "VertEdgeScroll"    "0"
    Option      "HorizEdgeScroll"   "0"
    Option      "SingleTapTimeout"  "1"
    Option      "FastTabs"          "1"
    Option      "VScrollEmuOff"     "1"
    Option      "VertScrollDelta"   "80"
    Option      "SHMConfig"         "1"
    Option      "CircularScrolling" "1"
    Option      "CircScrollTrigger" "8"
    Option      "CircScrollDelta"   "0.14"
    Option      "TapButton3"        "3"
    Option      "TapButton2"        "2"
EndSection  

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
EndSection

#Added
Section "InputDevice"
    Identifier    "Configured Mouse"
    Driver        "ExplorerPS2"
EndSection

##Added
Section "ServerLayout"
    Identifier    "Default Layout"
    Screen        "Default Screen"
    InputDevice    "Configured Mouse"
        InputDevice     "ETPS/2 Elantech Touchpad"
EndSection

10. The next thing you need to do is create a document at "/etc/modprobe.d/psmouse" and insert the text "options psmouse elantech=1"

At this point you will have a fully functional ubuntu running on your 1000he!

Hope this helps someone!

---

### Post by Kheradruakh on 2009-03-28
u freekin rock i spent all afternoon trying to get all the little features to work and it took me about 15 min with your guide thanks so much

---

### Post by Lybic on 2009-03-29
hey  this post is great, thanx for the help

I still have an issue with my wireless though, when i close the lid and open it back up the wireless says its working but it will not actualy go on-line until i reboot. Perhaps I installed the drivers wrong, any help with this would be great 
thanx
Lybic

---

### Post by dddaidl on 2009-03-29
> **Lybic said:**
> hey  this post is great, thanx for the help

I still have an issue with my wireless though, when i close the lid and open it back up the wireless says its working but it will not actualy go on-line until i reboot. Perhaps I installed the drivers wrong, any help with this would be great 
thanx
Lybic

I'm not sure why you are having this problem. Suspend (I assume you enter when you close the lid) works fine on my computer. Did you check to see whether or not you have the NE771 chipset? Also, did you make sure you were running the eeepc kernel when you compiled the drivers? Beyond that, i'm not sure what the problem would be.

---

### Post by Lybic on 2009-03-29
seems to be working now. i think I may have been using the wrong kernel.
Thanks again, this post helped me get my machine up and running in maybe ten minutes.

---

### Post by prykej on 2009-03-30
Thank you for an incredibly useful post. In the week since I got my 1000HE, I've spent many hours trying to make everything work with linux. Most of the "solutions" I found introduced new problems. (For example, I installed the new 2.6.29 kernel, making the wireless connection reliable, but knocking out the gsynaptics utility that I was using to adjust the touch pad settings.) 

With the aid of this howto, I was finally able to get everything working on my CrunchBang Linux (Intrepid based) install.


I did run into two glitches that took me a bit of time to figure out. In case anyone else encounters the same problems, I feel  that I should mention them and how I solved them.

My first problem was with the wireless download. I downloaded compat-wireless-2009-03-30.tar.bz2 from [http://wireless.kernel.org/download/compat-wireless-2.6/](http://wireless.kernel.org/download/compat-wireless-2.6/). I got an error after running "make" and "sudo make install" failed as well. I eventually followed the directions here: 
[http://blog.securism.com/2009/01/how-to-cutting-edge-wireless-drivers-in-ubuntu/](http://blog.securism.com/2009/01/how-to-cutting-edge-wireless-drivers-in-ubuntu/)
which allowed me to download and install the software for my wireless connection.

I noticed another, more minor problem. When I tried to turn off the screen back-light using the function-F7 keys, I was briefly shown an error message and then logged out. I was able to correct this by changing the eeepc-acpi file in the /etc/default directory to make it run scripts I found here:
[http://article.gmane.org/gmane.linux.debian.devel.eeepc/1550](http://article.gmane.org/gmane.linux.debian.devel.eeepc/1550)
When I press Fn-F7 the screen now blanks as I expect it to, returning as soon as I press a key or use the touch pad.

I'm very pleased to have everything working under linux on me 1000HE now. I purchased it mainly to do Ruby on Rails development, and linux is a more stable environment for that sort of work than the Windows XP that Asus bundles with this model. Thanks again for the helpful article posted above.

---

### Post by fukr on 2009-04-06
I just picked up a 1000HE yesterday and installed Eeebuntu 2.0 via bootable USB, which I created using Unetbootin on my Debian 5 system.

Very disappointed to find this distribution was unable to properly connect to my WAP out of the box, even though a list of APs was displayed in the drop-down menu.

Thanks to your Howto, dddaidl, I discovered compat-wireless was the missing link. I've been through Madwifi hell in the past; trying to get the Atheros card in my MacbookPro 3,1 to function properly in Linux was a real nightmare. This, however, was a breeze.

_Please note:_
Rather than getting the EEE kernel and Intrepid separately (as in the original post), Eeebuntu is a much simpler one-shot solution to the same effect. My procedure was as follows:

[Download Eeebuntu Netbook Remix ("Nbr").]("http://www.eeebuntu.org/index.php?page=nbr")

Record the disk image (*.iso) to USB stick using [Unetbootin]("http://unetbootin.sourceforge.net/") in Linux or Windows; Mac users can do it [from the Mac OS terminal]("http://macosx.com/forums/unix-x11/293698-making-bootable-usb-drive-os-x.html").

While your Eee PC 1000HE is powered down, attach the USB stick. Turn it on, quickly press Esc at the prompt, and select the USB drive (usually labeled "Removable storage") from the boot menu.

Install Eeebuntu; remove the USB stick at the end of the installation where it instructs you to remove the CD and press Enter.

You may want to test your wireless networking capabilities once you've booted into Linux. If you're able to connect to your WAP, great; I was not. If you can't connect, you'll need a wired (ethernet) connection to complete this process. Here's what I did:

From Eeebuntu's default launcher: Administration > Synaptic Package Manager. Click "Reload" for good measure.

Mark the following for installation:
build-essential
linux-headers-eeepc
wicd
(*Be sure gcc is also marked as a dependency, if not already installed. I had a bizarre experience with this once...)
Click "Apply."

Now that you have what you'll need to compile the latest drivers on your system, [head over to Linux Wireless and download the newest compat-wireless]("http://linuxwireless.org/en/users/Download"); their building and installation instructions should suffice.

Press the power button; click "Restart."

You should now have a functional wireless networking interface on your Eee PC 1000HE.


_Notes:_
lspci returns
...Network Controller: Atheros AR928X Wireless Network Adapter...

lsmod confirms ath9k is in use.

---

### Post by Paulo Wageck on 2009-04-26
Thanks for the useful post!

The eee pc kernel and the touchpad fix worked like a charm.

The Wifi compilation didn't work with either way (compiling from source or using the GIT tree). Anyways... WIFI started working after the last update of the system.... now everything works.... (but the Webcam... )...


Let's try to make the camera work.....


Cheers,

Paulo

---

### Post by timeslip on 2009-04-26
The wireless (ATH9k) has worked for me right out of the box with the latest 9.04 and 8.10 install.  However, when I go into standby, and power back on, it stops working.  I still have an IP, but I can't seem to get the wireless driver to work until I do a full reboot.

Any suggestions?

Also looking for ways to disable mouse clicks on the touchpad.  I noticed with 9.04, there is an option for it in the Preferences / Mouse.

---

### Post by chief_officer on 2009-04-27
Friends,

I am considering to purchase 1000 HE to run Eeebuntu.
Did anyone install it and got everything working? It is reported to work with 1000H but I am not so sure about the Bluetooth and the wireless b/g/n that 1000HE has. [OK, OK. No flaming, this is not the Eeebuntu forum I know.]

@dddaidl: Did you check the Bluetooth? Does it function fully? It has been reported to have reported to have [_some issues _]("http://www.linlap.com/wiki/asus+eee+pc+1000he")under openSUSE 11.1. Not sure if this is the case with Jaunty/Eeebuntu.

Regards,
chief

---

### Post by MagicMintFever on 2009-05-01
I am having trouble with step 8. I follow the link and enter this line into terminal "
tar jxvf compat-wireless-$(date -I).tar.bz2" or more so tar jxvf compat-wireless-2009-05-01.tar.bz2

and it returns with

tar: compat-wireless-2009-05-01.tar.bz2: Cannot open: No such file or directory
tar: Error is not recoverable: exiting now
tar: Child returned status 2
tar: Error exit delayed from previous errors

can anyone help me with this? my wireless is really acting up with all this. I never know if it will or won't work and have to constantly restart in hopes it will

---

### Post by 42bsk on 2009-05-12
Many thanks for typing this up - it worked (mostly) like a dream for me.

One small problem remaining is that the hotkey that's supposed to turn off the lcd backlight now toggles the touchpad instead. I'm also having a weird networking bottleneck whereby I can't access web pages while downloading package files - the packages are going at max speed for my line. I did not follow your wireless instructions as mine worked out of the box - does anyone know if doing so is a likely solution?

---

