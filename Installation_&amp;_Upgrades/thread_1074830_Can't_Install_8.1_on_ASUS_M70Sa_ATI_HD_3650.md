---
title: "Can't Install 8.1 on ASUS M70Sa ATI HD 3650"
date: 2009-02-19
forum: Installation &amp; Upgrades
---

### Post by njsanders1 on 2009-02-19
I've run Ubuntu for a few months now with little problems, aside from minor inconveniences from time to time with Compiz or VirtualBox, on a couple of different machines, including a Dell Inspiron and a Thinkpad T42p.  Now that I have purchased a new laptop, however, I'm extremely frustrated.  I boot from the install distro (32-bit 8.10), and after picking a language and telling it to install, the orange bar completes its journey across the screen.  However, instead of the initial locale dialogues and such, I get a beige screen with flickering lines.  It's almost as if I were looking at a monitor with a bad refresh rate setting.  I've tried connecting an external monitor and I get the same output on both displays.  I've tried booting Ubuntu without installing it, and again the same result.  Vista runs absolutely fin-- well, as it runs and I don't have issues with the graphics/display.

Other than downloading the alternate install distro and trying a text-based installation, can anyone suggest anything to try?  Is there a boot param that I can use to specify a resolution?  

System Params:  ASUS M70a, 4GB RAM, 1GB Video RAM, ATI HD 3650, dual 500G HD's, Blu-Ray/CDRW/DVDRW

Thanks!

---

### Post by cariboo on 2009-02-19
Have you tried pressing F4 at the menu screen and selecting safe graphics mode?

Jim

---

### Post by njsanders1 on 2009-02-19
Using the F4 option for safe graphics mode only boots to a text prompt.  The kernel itself is loading, it would seem.  If I attempt to do an xstart from the command line I get the same result as before.

---

### Post by Uberman on 2009-02-22
Hey, guys.

I'm having the exact same issue: Ubuntu 8.10 (amd64) on the exact same notebook.  Regular graphics mode gives me an invalid refresh rate (hence, the buzzing lines).  The "safe graphics" mode just boots to a command prompt in both "Live" and "Install" modes.  No installation is initiated in either one.  :(

Is there a way to manually start the installation process from this command line?  Or, better yet, of specifying the resolution *and* refresh rate on the kernel options line?  I've Googled for it, but there's nothing out there that I can find.

---

### Post by shadab khan on 2009-02-22
even iam also suffering with this graphic problem my current vedeo not supporting atleast 256 colours . accidently computers screen resoluting and color depth are currently set to a very low level i have tried every option in the display setting menu but it shows same problem . please help....:(

---

### Post by Uberman on 2009-02-22
> **Uberman said:**
> Hey, guys.

I'm having the exact same issue: Ubuntu 8.10 (amd64) on the exact same notebook.  Regular graphics mode gives me an invalid refresh rate (hence, the buzzing lines).  The "safe graphics" mode just boots to a command prompt in both "Live" and "Install" modes.  No installation is initiated in either one.  :(

Is there a way to manually start the installation process from this command line?  Or, better yet, of specifying the resolution *and* refresh rate on the kernel options line?  I've Googled for it, but there's nothing out there that I can find.

Addendum: I just installed CentOS 5.2 (amd64) onto the machine, and the installation process was flawless.  When it was done, it even set the screen resolution properly (1920x1200).  So, it's not some issue with the hardware configuration of this particular notebook.  It's Ubuntu's installation proecess.

---

### Post by Uberman on 2009-02-23
Ubuntu Desktop 8.04.2 installed just fine on this machine (in full graphical mode), and as far as I can tell, it *looks* the same (graphically speaking).  So, I don't understand what the problem is with 8.10.

After some tweaking to correct the screen brightness, microphone, and speakers, and installing the ATI proprietary video drivers, I have what seems to be a properly functional system.  I even have VirtualBox installed with Vista 64-bit running.  Can't seem to get the fingerprint reader to work, but that's not a big deal.

I wish I knew what the problem is with 8.10, but I guess this version of Ubuntu will suffice for the moment.  If anybody gets lucky with Ubuntu 8.10 on this laptop, please let the rest of us know how you did it.  ;)

---

### Post by troegs on 2009-02-24
Another Asus owner here. Ran into an identical problem. I have a g50vt. I finally found a post that addressed the issue. Believe it or not all my install woes were solved by simply burning the install cd at lowest possible speeds. Sounds crazy I know. I'm a CS major and asked several professors how this could be. One finally had an answer, (he's one of those "you can have my linux when you pry it from my dead hands" types). Anyhow, he explained it to me and I'd love to write a short novel on why exactly it does matter, (for some computers, *ahem* ASUS *ahem*. Don't get my wrong, i love my Asus, but my Asus did not like the initial install of 8.10). I don't have the time nor the patience. Anyhow, give it a shot, burn at 2x or slowever if possible, I found anything faster than 4x resulted in a failed install for me. Good luck.

---

### Post by daedalas1981 on 2009-02-25
I've got the ASUS M70SA-X2 and also failed with 8.10. The 8.04LTS worked great.

As to the last post, I've burned all my disc's at 1x, and I still have the problem.

I have read on 3 other forums that you can install 8.04 and upgrade to 8.10 without problems. Another forum said they had it working with the VESA drivers for the 3650. Hmmmmm.......

Is there a way to default to the VESA drivers on a Live Distro without installing???

---

### Post by Uberman on 2009-02-26
> **daedalas1981 said:**
> I've got the ASUS M70SA-X2 and also failed with 8.10. The 8.04LTS worked great.

As to the last post, I've burned all my disc's at 1x, and I still have the problem.

I have read on 3 other forums that you can install 8.04 and upgrade to 8.10 without problems. Another forum said they had it working with the VESA drivers for the 3650. Hmmmmm.......

Is there a way to default to the VESA drivers on a Live Distro without installing???

Yes, I researched that.  You can select "Other options" at the boot screen, and append "xforcevesa" to the boot options to force the VESA drivers to be used.  However, I did that, and got the same problem.  I also added "vga=XXX", which is supposed to select a specific video mode (and if the number you choose isn't valid, it will give you a list to choose from), but that failed as well.

I'm guessing my problem is the refresh rate.  That's what I think is causing the screen to be unreadable.  I suppose it's possible that it's an invalid screen resolution, but my gut tells me 'refresh rate', and I cannot find a boot-option to set that.

---

### Post by njsanders1 on 2009-03-02
That's exactly what it looked like to me -- refresh rate.  There was output, but it looked exactly like what we used to see "in the old days" when an old, "slow" monitor got connected to a newer machine.

---

### Post by SMG_07 on 2009-03-09
hi there troubled guys !:D

i have the answer 4 ur Question's ;)

now i have a asus m70sa and i have been through hell to get these info so show some gratitude [-(

first of all the beige screeen of death LoL :
the only way so solve the is to install ubuntu 8.04 and install the ati card from the hardware driver.. and then upgrade to 8.10 if u want to ... i personally dont recommend it because u might have proplems with it .. trust me this is coming from a guy who tried installing ubuntu half a dozen times :lolflag:

now we have the other problems for those who already installed ubuntu... stuff like the light sensor and the sound jack and the camera and finger print .. this in the answer for all of it :[http://seethisnowreadthis.com/2008/05/19/how-to-install-ubuntu-804-hardy-heron-on-the-asus-m50sv-a1/](http://seethisnowreadthis.com/2008/05/19/how-to-install-ubuntu-804-hardy-heron-on-the-asus-m50sv-a1/)
this page is ment for the m50 but it work's with the m70:rolleyes:

by the way : i recommend installing the 32bit cos it has a lot of supporting programs :popcorn:

now i have the asus m70sa w/ubuntu 8.04 LTS and very happy with it..if u have any questions im here 4 u:KS

---

### Post by daedalas1981 on 2009-03-21
I found a few forums which say changing the Xorg.conf file within the iso can fix some issues. I just want to find a way to the ATI drivers installed. I have a 8.10 o/s running on my main comp. I love it and wish I could install it on my laptop. As to the guy in th last post about installing 8.04, its nice if you install it, but I just want to run live, And my impression is that everybody here wants a running 8.10 copy. There must be a way to create it. I'm thinking maybe we should mix some files from 8.04 to 8.10, or copy the Xorg.conf file, and put it in the 8.10 since the lingo is the same. Anybody try this?

---

### Post by daedalas1981 on 2009-03-21
...one more thing. Another individual says that they can enter the terminal (which I did), create a internet connection (i don't know how), sudo apt-get install updates, sudo apt-get install envy. And run the ATI drivers, then restart x server (startx). Has anybody tried this??

---

### Post by daedalas1981 on 2009-03-23
M70SA-X2 * SOLVED *

After lots of research, I found a way!

- You'll need a USB Pen with atleast 75MB of Free space.
- You'll need a running computer to download the ATI driver (currently version 9.2) for the Raedon HD 3xxx, from [www.amd.com/us-en/](www.amd.com/us-en/)
- Store the file on the USB Drive.
- You'll need the USB Mouse attached. (IMPORTANT). The Track pad drivers needs to be installed after screen fix. 

Boot with the Live CD/DVD with the USB drive In.

- When the screen blurs out, hit CTRL-ALT-F1. This will bring you to the terminal.
- type "sudo su" (add Super-User powers!)
- type "dir", (displays Directory Contents) Look for Desktop. You see it, thats good. If not, I dunno.
- type "cd /media/disk". (usually Media contains all devices, and disk is usually the first USB)
- type "dir". Do you see the ati file (like ati-driver-installer-9.2-x86.x86_64.run)?? Good, If not try "cd", then "cd /media", and look for other disk names.
- type "cd" (default back to filesystem)
- type "cd /home/ubuntu/Desktop" (the Desktop setup by Ubuntu during the crash)
- type "cp /media/disk/ati-driver-installer-9.2-x86.x86_64.run /home/ubuntu/Desktop" assuming that you used no folder, and that you have this version of the installer, if not replace the name with the one you have.
- Now if you've done everything right, you should now still be in the Desktop folder.
- type "sh ./ati-driver-installer-9.2-x86.x86_64.run" (sh is the instructions to activate the installation)
- Follow the on screen instructions. Install Generic 9.2, NOT Distribution Specific.
- Agree to the Terms; If all goes well you'll see a screen saying finished, and will return you to the terminal.
- Now we have to stop the old X server.
- type "sudo telinit 1"
- This should stop everything.
- Last but not least we will restart X server to load the ATI drivers, by typing "startx".

TODA! I think we are moving ahead. With some quick searches for the M50 fixes, for the Brightness, Finger reader, Camera, etc, BUT MORE IMPORTANTLY your MOUSE/TRACK PAD (unless you prefer the mouse). Apply these as they are the same as the M70.

** IN THE WORKS ** I'll try and find the instructions for the M50. Last but not least, I will find out how to create a internet connection, and do a Distribution Specific install.


[B]==================================================================|
===  THIS NEXT PART IS FOR ALL THE PERIPHERALS for the M70SA's  ==|||-->
==================================================================|[/B]

** INSTRUCTIONS ** [http://seethisnowreadthis.com/2008/05/19/how-to-install-ubuntu-804-hardy-heron-on-the-asus-m50sv-a1/](http://seethisnowreadthis.com/2008/05/19/how-to-install-ubuntu-804-hardy-heron-on-the-asus-m50sv-a1/)
** AS LISTED ON THE PAGE ABOVE -> **

1. Screen Brightness

The ambient light sensor is the cause of the dim screen, we&#8217;ll have to turn it off. To fix this we will have to create a shell script that will be run on boot up that will turn of the ambient light sensor.

A) Open Terminal (Menu->Accessories), and type the following:
sudo nano brightness

B) Now paste the following in the Terminal window:
#!/bin/sh
echo 0 > /sys/devices/platform/asus-laptop/ls_switch

C) Hit Ctrl-O to save and then Ctrl-X to exit.

D) Now we will copy our new shell script to the appropriate directory, make it executable and add the following links by typing the following in Terminal:
sudo mv brightness /etc/init.d
and then
sudo chmod 755 /etc/init.d/brightness
and then
sudo update-rc.d brightness defaults 90

E) Reboot, and you will have regained control of your brightness level.

2. Nvidia Driver (OMIT THIS ONE, the M70SA-X2 has the ATI driver that we already installed.)

3. Webcam Driver

The webcam if attempted to be used will crash any application that is trying to access it by default. Thanks to the great tutorial by Bill Giannikos the process of installing your Asus uvc webcam driver is relatively easy.

A) First we&#8217;ll need to install the files needed to build the driver by typing the following in Terminal:
sudo apt-get install build-essential subversion linux-headers-`uname -r`

B) Now we will build the driver by typing the following commands in Terminal:
cd /usr/src
and then
sudo svn checkout svn://svn.berlios.de/linux-uvc/linux-uvc/trunk
and then
cd trunk
and then
sudo make
and then
sudo cp -a uvcvideo.ko /lib/modules/`uname -r`/ubuntu/media/usbvideo/

C) Reboot, and your webcam will now be working.

4. Fingerprint Reader Driver

The fingerprint reader is especially useful in Linux as you are asked for your password before completing any change within the operating system. None the less, I would still not recommend for you to install the fingerprint reader driver due to its&#8217; unstable nature and poor quality. The guide provided by Karol Krizka solved the problem of installing this driver.

A) First we&#8217;ll need to add the driver source to our software repository by typing the following in Terminal to open the sources list:
sudo nano /etc/apt/sources.list

B) Now scroll to the end of the file and paste the following line there:
deb [http://ppa.launchpad.net/madman2k/ubuntu](http://ppa.launchpad.net/madman2k/ubuntu) hardy main restricted universe multiverse

C) Hit Ctrl-O to save and then Ctrl-X to exit.

D) Update the source list by typing the following in Terminal:
sudo aptitude update

E) Install the fingerprint reader driver by typing the following in Terminal:
sudo aptitude install fprint-demo libpam-fprint libfprint

F) Enroll your fingerprint by typing the following in Terminal:
sudo fprint_demo

G) Click on Enroll and swipe your finger.

H) Now we will have to tell Ubuntu when to use your fingerprint by editing the fingerprint reader driver&#8217;s configuration file by typing the following in Terminal:
sudo nano /etc/pam.d/common-auth

I) Paste the following in the file at the end:
auth sufficient pam_fprint.so
auth required pam_unix.so nullok_secure

J) Hit Ctrl-O to save and then Ctrl-X to exit.

H) Reboot, and you will be now scanning your finger instead of typing your password each time.

5. Email LED

Having a LED notifying you of incoming emails is quite handy, especially if you are not constantly by your computer. In this step I will provide you with instructions, showing you how to enable the email LED to work with the best Gmail notifier available - CheckGmail, a function that even Windows cannot even provide.

A) Follow the instructions provided by me in this tutorial to install CheckGmail:
[http://seethisnowreadthis.com/2008/05/20/checkgmail-linuxs-blackberry/](http://seethisnowreadthis.com/2008/05/20/checkgmail-linuxs-blackberry/)

B) Open the CheckGmail preferences and paste the following in the Command to execute on new mail field:
echo 1 > /sys/class/leds/asus:mail/brightness

C) Now paste the following in the Command to execute for no mail field:
echo 0 > /sys/class/leds/asus:mail/brightness

D) Without giving the right permissions CheckGmail will not be able to turn on the LED. To do this we must type the following in Terminal:
gksudo nautilus

E) Navigate to the following folder by pasting the following in Location field in the newly open File Browser:
/sys/class/leds/asus:mail
Press Enter.

F) Right-click on the file brightness, and select Properties.

G) Select the Permissions tab.

H) Click on root in the drop-down menu besides Owner and select yourself.

I) Without rebooting you should have now have the email LED notifying you of incoming email.

6. Microphone

By default the microphone is not enabled in enabled in the Volume Control menu. This problem will require the least effort.

A) Righ-click on the speaker in the task bar and select Open Volume Control.

B) Select Edit from the menu, and then select Preferences.

C) Click on the boxes besides Capture and Capture 1.

D) Now your microphone should be working.

7. Hard drive

The Seagate Momentus 5400.4 250 Gb hard drive has a firmware bug that makes Ubuntu park it every minute or so; the same problem exists in Vista. This parking is considered a load cycle, of which your hard drive was designed to complete 600,000 of such cycles. Without this fix your hard drive can prematurely fail after only 8 months. Thanks to jakon on ubuntuforums.org, we now have a fix that fully works with the Asus M50Sv-A1.

A) First we&#8217;ll have to adjust the hard drive&#8217;s power management settings by typing the following in Terminal:
sudo nano /etc/hdparm.conf

B) And by pasting the following three lines in the file:
/dev/sda {
apm = 254
}

C) Hit Ctrl-O to save and then Ctrl-X to exit.

D) Next we&#8217;ll have to tell the notebook to reactivate these settings after resuming from suspend mode by typing the following in Terminal:
sudo nano 30hdparm

E) And by pasting the following lines inside the file:
#!/bin/bash

# Run hdparm like on boot to restore hdparm.conf settings -
# hds lose them when going to standby.

resume_hdparm()
{
for x in /sys/bus/ide/devices/*/block* /sys/bus/scsi/devices/*/block*
do
# This check is required - x can contain
# literal &#8216;/sys/bus/ide/devices/*/block*&#8217;
# when the glob did not match anything.
if [ -e $x ]
then
drive=$(basename $(readlink $x))
DEVNAME=/dev/$drive /lib/udev/hdparm
fi
done
}

case &#8220;$1&#8243; in
thaw|resume)
resume_hdparm
;;
*)
;;
esac

exit $?

F) Hit Ctrl-O to save and then Ctrl-X to exit.

G) Finally we&#8217;ll have to install the file we just created by typing the following in Terminal:
sudo install 30hdparm /etc/pm/sleep.d/

H) Reboot and your hard drive should be working with Ubuntu as it should have from the start.

8. Speakers

With the thousands of different notebook sound configurations that are out there, it is no surprise to have yet another ALSA bug. Thanks to Petr Zemek (s3rvac), we now have the correct ALSA option switch that will cause the speakers to mute when the headphones are plugged in. Surprisingly after trying all the generic options, the same option that works for a Haier notebook works with the Asus M50.

A) First we&#8217;ll have to edit the ALSA configuration file via terminal:
sudo nano /etc/modprobe.d/alsa-base

B) Scroll down to the bottom and add this line:
options snd-hda-intel model=haier-w66

C) Hit Ctrl-O to save and then Ctrl-X to exit.

D) Reboot and your speakers will now automatically mute when you plug your headphones in.

This guide will now allow you to use your Asus M50Sv-A1 with the most secure and progressive operating system at the moment that thrives on the open source community which provides for a much more dynamic experience than anything else out there now. Due to the fact that the notebook is relatively new, not all of its&#8217; features could be fully exploited. Really, only some non-essential hotkeys cannot be used, but these are features that most of us are willing to trade for the privilidge of being on the Linux platform. If you find any other tweaks that could enhance Ubuntu on the Asus M50Sv-A1, please post below.

Good Luck, and I will let you all know if I find anything else out. 

**Daedalas1981**

---

