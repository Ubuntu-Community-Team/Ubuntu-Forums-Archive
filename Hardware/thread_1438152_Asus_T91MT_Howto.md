---
title: "Asus T91MT Howto"
date: 2010-03-24
forum: Hardware
---

### Post by spl on 2010-03-24
Warning: this system is NOT fully supported yet. I still encounter crashes when using the touch screen and the 3D performance is unacceptable. Suspend is not working either.

You don't have to read the next paragraphs. If you like it quick and easy, just follow the code below.

I finally have my T91MT working with stable wireless, full 3D acceleration AND touch screen! I spend the last days (thank you Intel and Asus) trying to first get Arch Linux (which apparently didn't work out) and now Ubuntu to work. I have been digging in various forums and blogs and was smart enough to write down all the steps necessary to achieve the aforementioned results.
I first installed to an external hard disk because I didn't want to touch the internal SSD as long as I was unsure about the successful outcome. When I got things running, I performed a fresh install to the SSD and tested / cleared up the notes I took.

My sources (amongst others):
[http://setupguides.blogspot.com/2009_11_01_archive.html](http://setupguides.blogspot.com/2009_11_01_archive.html)
[https://wiki.ubuntu.com/HardwareSupportComponentsVideoCardsPoulsbo](https://wiki.ubuntu.com/HardwareSupportComponentsVideoCardsPoulsbo)
[http://ubuntuforums.org/showthread.php?t=1229345](http://ubuntuforums.org/showthread.php?t=1229345)
[http://ubuntuforums.org/showpost.php?p=8566880](http://ubuntuforums.org/showpost.php?p=8566880)

I summed up everything in a file where I tried to cover all the necessary steps (not EVERY single click and keystroke, but I hope enough for people who are not so familiar with the system). This is not supposed to be a save-and-execute script (this wouldn't work anyways as there are some reboots) but rather a summary of things that should be done manually.

I used [Ubuntu Netbook Remix](http://www.ubuntu.com/GetUbuntu/download-netbook) and usb-creator ```
sudo aptitude install usb-creator && usb-creator
``` with a 1GB stick. To boot from usb, either hold down escape or F2 during boot and select the medium.

As I still want to keep Windows 7, I chose to manually partition the SSD and shrunk the NTFS partition to 20GB. It's easier to access a NTFS partition from linux than a linux partition from windows for additional storage space. It is not recommended to use a journaling file system on a SSD as that causes additional writing access. I hence created a new primary partition formated with ext2 and set the partition's mount point to /. I did not provide any swap space, again for the same reason.

I left my notes from the installation at the beginning for the impatient ones who couldn't be bothered to read my above blah blah.

Sorry for the long lines, copy the text to an editor and toggle line wrapping...

```

# ubuntu unr
# usb-creator -> 1GB stick
# hold down esc during boot -> select usb stick to boot from
# start install
# manual partitioning
# resize win7 partition to desired size (can be used from linux, better than the other way around)
# create one new primary partition using all available free space
# format with ext2
# mount point /
# OMG NO SWAP!!!1 -> stfu, continue
# advanced -> install boot loader to /dev/sda (leave unchanged)
# reboot

# edit fstab to mount the parition noatime (less writes to the disk, yes I know this is hardly an issue nowadays, but why do any unnecessary writes?)
sudoedit /etc/fstab
# the last line should look something like this:
#UUID=b5325025-9da1-4d03-ba1c-6c6352672253 /               ext2    errors=remount-ro 0       1
# change it to (without the leading #)
#UUID=b5325025-9da1-4d03-ba1c-6c6352672253 /               ext2    errors=remount-ro,noatime 0       1

# set up network (best use wired connection first because wireless sucks with out of box drivers)

# update the newly installed system
sudo aptitude update
sudo aptitude upgrade

# get proper working wireless
sudo aptitude install linux-backports-modules-karmic
reboot

# add the following ppa (contains more up to date alsa versions): https://launchpad.net/~ricotz/+archive/ppa
sudo add-apt-repository ppa:ricotz/ppa
sudo aptitude update
sudo aptitude upgrade
# you can reboot now but don't have to

# install some prerequirements (build tools)
sudo aptitude install build-essential dkms fakeroot

# poulsbo driver (that f*cking biatch!)
# yes i know it's ugly to manually download debs and install them via dpkg, but i haven't found a repository that provides a working driver for karmic so far
wget http://dl.dropbox.com/u/1338581/Gma500/deb/libdrm-poulsbo1_2.3.0-0ubuntu3netbook7_i386.deb http://dl.dropbox.com/u/1338581/Gma500/deb/libva1_0.31.0-1+sds9_i386.deb http://dl.dropbox.com/u/1338581/Gma500/deb/poulsbo-config_0.1_all.deb http://dl.dropbox.com/u/1338581/Gma500/deb/poulsbo-driver-2d_1.1-0ubuntu1~904um1_all.deb http://dl.dropbox.com/u/1338581/Gma500/deb/poulsbo-driver-3d_1.1-0ubuntu1~904um1_all.deb http://dl.dropbox.com/u/1338581/Gma500/deb/psb-firmware_0.30-0ubuntu1netbook1_i386.deb http://dl.dropbox.com/u/1338581/Gma500/deb/misc/psb-kernel-source_4.41.6-0ubuntu1~1004jbs1_all.deb http://dl.dropbox.com/u/1338581/Gma500/deb/psb-modules_4.41.2-0ubuntu1~910um1_i386.deb http://dl.dropbox.com/u/1338581/Gma500/deb/xpsb-glx_0.18-0ubuntu1netbook1_i386.deb http://dl.dropbox.com/u/1338581/Gma500/deb/xserver-xorg-video-psb_0.31.0-0ubuntu1~904um1_i386.deb

# install the downloaded debs (yeh, security overkill!)
sudo dpkg -i libdrm-poulsbo1_2.3.0-0ubuntu3netbook7_i386.deb
sudo dpkg -i libva1_0.31.0-1+sds9_i386.deb
sudo dpkg -i poulsbo-config_0.1_all.deb
sudo dpkg -i psb-firmware_0.30-0ubuntu1netbook1_i386.deb
sudo dpkg -i psb-kernel-source_4.41.6-0ubuntu1~1004jbs1_all.deb
sudo dpkg -i psb-modules_4.41.2-0ubuntu1~910um1_i386.deb
sudo dpkg -i xpsb-glx_0.18-0ubuntu1netbook1_i386.deb
sudo dpkg -i xserver-xorg-video-psb_0.31.0-0ubuntu1~904um1_i386.deb
sudo dpkg -i poulsbo-driver-2d_1.1-0ubuntu1~904um1_all.deb
sudo dpkg -i poulsbo-driver-3d_1.1-0ubuntu1~904um1_all.deb

sudo echo -e "# disable loading of i915 module as it conflicts with poulsbo driver\nblacklist i915" >> /etc/modprobe.d/blacklist.conf

# append device section to xorg.conf. if you already use a xorg.conf (not the case with a fresh ubuntu install), check manually for conflicts with existing sections
sudo echo 'Section "Device"
	Identifier     "GMA500"
	Driver         "psb"
	Option         "IgnoreACPI" "true"
	Option         "MigrationHeuristic" "greedy"
	Option         "AccelMethod" "EXA"
	#Option         "DownScale" "false"
	#Option         "ExaNoComposite" "false"
	#Option         "ExaMem" "131072"
	#Option         "ExaScratch" "4"
	#Option         "ExaCached" "false"
	#Option         "LidTimer" "false"
	#Option         "NoAccel" "false"
	#Option         "NoFitting" "false"
	#Option         "NoPanel" "false"
	#Option         "ShadowFB" "false"
	#Option         "SWcursor" "false"
	#Option         "Vsync" "false"
EndSection

Section "DRI"
	Mode    0666
EndSection
' >> /etc/X11/xorg.conf

# restart X to see wether the changes were succesful: switch to terminal 1 (Ctrl+Alt+F1), login and issue
sudo /etc/init.d/gdm restart && exit

# log back in and fire up a terminal
glxinfo | grep -i direct
# should give you "direct rendering: Yes"

# update initial ramdisk
sudo update-initramfs -u

# and reboot to use the new ramdisk


# touch screen

# a quick initial test:
echo '#include <sys/types.h>
#include <fcntl.h>
#include <linux/input.h>
#include <stdio.h>
#include <errno.h>

main(int argc, char **argv)
{
    struct input_event ev;
    int fd=open(argv[1],O_RDONLY);

    for (;;) {
        int r=read(fd,&ev,sizeof(struct input_event));

        if (r==-1 && errno==EINTR) continue;
        if (r==-1) break;
        printf("Event: time %ld.%06ld, type %d, code %d, value %d\n",
                ev.time.tv_sec, ev.time.tv_usec, ev.type, ev.code, ev.value);
    }
    perror("read");
    close(fd);
}' > detect_touchscreen.c
gcc detect_touchscreen.c -o detect_touchscreen
sudo ./detect_touchscreen /dev/input/by-id/usb-AsusTek__Inc._MultiTouch-event-if00

# should output something like this when the screen is touched. just fyi: type 3, code 4 events are the x-, code 5 events are the y-coordinates. this is needed later on for calibration.
#Event: time 1269440981.748817, type 0, code 0, value 0
#Event: time 1269440981.756791, type 3, code 5, value 1850
#Event: time 1269440981.756809, type 0, code 0, value 0
#Event: time 1269440981.764793, type 3, code 4, value 110
#Event: time 1269440981.764811, type 3, code 5, value 1848
#Event: time 1269440981.764817, type 0, code 0, value 0

# /dev/input/by-id/usb-AsusTek__Inc._MultiTouch-event-if00 should point to the correct input device
ls -l /dev/input/by-id/usb-AsusTek__Inc._MultiTouch-event-if00
# on my T91MT: lrwxrwxrwx 1 root root 9 2010-03-24 10:54 /dev/input/by-id/usb-AsusTek__Inc._MultiTouch-event-if00 -> ../event5
# so /dev/input/event5 would be the touch screen

# the actual driver:
# download http://ohioloco.ubuntuforums.org/attachment.php?attachmentid=141954&d=1262310376

# extract archive
tar -xvzf xf86-input-evtouch-0.8.8-T91MT.tar.gz

# copy hal and udev configuration files
sudo cp 50-asustek.fdi /usr/share/hal/fdi/policy/20thirdparty/
sudo cp 69-touchscreen.rules /etc/udev/rules.d/

# append new device section to xorg.conf (this is only needed to be able to calibrate the touch screen, for me it worked without any changes to xorg.conf
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf_backup
sudo echo '
Section "InputDevice"
	Identifier "touchscreen"
	Driver "evtouch"
	Option "Device" "/dev/input/event5"
	Option "DeviceName" "touchscreen"
	Option "MinX" "0"
	Option "MinY" "0"
	Option "MaxX" "3475"
	Option "MaxY" "3475"
	Option "ReportingMode" "Raw"
	Option "Emulate3Buttons"
	Option "Emulate3Timeout" "50"
	Option "SendCoreEvents" "On"
	Option "Calibrate" "0"
EndSection

Section "InputDevice"
	Identifier "dummy"
	Driver "void"
	Option "Device" "/dev/input/mice"
EndSection

Section "Screen"
	Identifier    "Screen"
	Device        "GMA500"
	DefaultDepth    24
EndSection

Section "ServerLayout"
	Identifier    "Default Layout"
	Screen        "Screen"
	InputDevice "touchscreen" "SendCoreEvents"
	InputDevice "dummy"
EndSection
' >> /etc/X11/xorg.conf

# or use the xorg.conf provided in the archive
#sudo cp xf86-input-evtouch-0.8.8-T91MT/xorg.conf /etc/X11/

# now for the module
cd xf86-input-evtouch-0.8.8-T91MT/

# install the development version of xorg
sudo aptitude install xserver-xorg-dev

./configure
make
sudo make install # ugly, but i couldn't be bothered to build a deb - and apparently no one else could so far...

# you might have to manually copy the driver to the right location (i think it got overwritten by apt in my case)
sudo cp /usr/lib/xorg/modules/input/evtouch_drv.so /usr/lib/xorg/modules/input/evtouch_drv.so_backup
sudo cp .libs/evtouch_drv.so /usr/lib/xorg/modules/input/evtouch_drv.so

# restart X to see wether the changes were succesful: switch to terminal 1 (Ctrl+Alt+F1), login and issue
sudo /etc/init.d/gdm restart && exit

# the touch screen should be usable as soon as you see the login screen of gdm.
# on my T91MT I had to change the MinX/Y and MaxX/Y values in my xorg.conf to properly calibrate the touch screen.
# the cursor was dragging behind when i moved the stylus near the edges of the screen.
# for me MinX = MinY = 10 and MaxX = MaxY = 3465 provided an accurate touch screen.
# the theoretical resolution is 3475x3475.

# you can use the detect_touchscreen application from above:
# kill X (again from terminal 1, Ctrl+Alt+F1)
sudo /etc/init.d/gdm stop
# go wherever you compiled the app and start it as before, except we now filter out only the x- and y-coordinates
sudo ./detect_touchscreen /dev/input/by-id/usb-AsusTek__Inc._MultiTouch-event-if00 | grep -E "code 4|code 5"
# you can now move the stylus along all edges and note the minimum and maximum values for both coordinates
# when you're done, kill the app with Ctrl+C and put the values into your xorg.conf (do NOT set the Calibrate option to 1)
# bring back X and test check the results
sudo /etc/init.d/gdm start && exit

# things that do not work so far:
# - multi touch gestures
# - long click

# if you want to use compiz, you need to apply further changes that can be found in the poulsbo.sh script from the ubuntu forums. i don't use compiz and hence haven't tested these things.
# Compiz whitelist
#sudo sed -i 's/i810 fglrx/i810 fglrx psb/g' /usr/bin/compiz

# also from the poulsbo.sh script but not tested as my mplayer runs perfectly so far without any changes
# install mplayer-vaapi stuff
#wget http://dl.dropbox.com/u/1338581/Gma500/deb/mplayer-vaapi_20100114-1_i386.deb -O /tmp/mplayer-vaapi_20100114-1_i386.deb
#sudo dpkg -i /tmp/mplayer-vaapi_20100114-1_i386.deb
#sudo apt-get install -q=0 -y --force-yes mplayer-skins
#sudo ln -s /usr/X11R6/lib/modules/dri/psb_drv_video.so /usr/lib/va/drivers


```

I hope I didn't forget anything and have covered the most important issues. If there are questions, feel free to ask!

I might add to this howto later on because I haven't really gotten to use the netbook yet. There are also many things left to do because I don't intend to use the bloated Gnome GUI but rather something slim like fluxbox. Furthermore, I hope I can speed up the boot process because right now it lasts way too long. And there are of course plenty apps that need to be tested with the touch screen (which was the actual reason for buying that thing). So far I can recommend xournal: easy to use, quick and accurate - not like it's windows port or the other bullsh*t pdf annotators I came across on windows (yes, even the expensive commercial ones).

And if there is someone with even more time than me: feel free to add this to the wiki...

---

### Post by thises on 2010-04-03
thank you very much. I finaly managed to configure my T91MT with your very well done tutorial.

---

### Post by Roman Shuvalov on 2010-04-18
I've installed 9.10 before your post, all working fine but sometimes I catch random freezes. After disabling audio in BIOS it looks like all works wine. 

**spl**: What are you audio drivers? (ALSA packages versions etc...)

---

### Post by Goldstorm on 2010-05-01
I'm having trouble with the echo command working for the GMA500 drivers. It keeps saying permission denied.

---

### Post by spl on 2010-05-02
Sorry for the slow reply, I thought I'd automatically subscribe my own threads...

> **Goldstorm said:**
> I'm having trouble with the echo command working for the GMA500 drivers. It keeps saying permission denied.

Forgot some sudos, should be fixed now.


> **Roman Shuvalov said:**
> I've installed 9.10 before your post, all working fine but sometimes I catch random freezes. After disabling audio in BIOS it looks like all works wine. 

**spl**: What are you audio drivers? (ALSA packages versions etc...)

I forgot to mention that I installed alsa from a ppa ([https://launchpad.net/~ricotz/+archive/ppa](https://launchpad.net/~ricotz/+archive/ppa)). See above how to install it.

About the freezes: I'm encountering them too. However, only when using the touch screen. I'm still trying to find out where exactly the freeze occurs because, so far, I have not been able to systematically reproduce it, except exhaustive use of the touch screen...

---

### Post by Goldstorm on 2010-05-02
Hey thank you. I'll do a clean install and see how this works.

---

### Post by Goldstorm on 2010-05-02
It's giving me the same error as before even with the sudo command. Am i supposed to run it in root?

---

### Post by spl on 2010-05-02
> **Goldstorm said:**
> It's giving me the same error as before even with the sudo command. Am i supposed to run it in root?

Exactly which commands are you talking about and what errors do you receive?

---

### Post by Goldstorm on 2010-05-02
> **spl said:**
> Exactly which commands are you talking about and what errors do you receive?

sudo echo -e "# disable loading of i915 module as it conflicts with poulsbo driver\nblacklist i915" >> /etc/modprobe.d/blacklist.conf

I enter that and I get this

Bash: /etc/modprobe.d/blacklist.conf Permission Denied

Should I be in root when I do this?

---

### Post by spl on 2010-05-03
> **Goldstorm said:**
> sudo echo -e "# disable loading of i915 module as it conflicts with poulsbo driver\nblacklist i915" >> /etc/modprobe.d/blacklist.conf

I enter that and I get this

Bash: /etc/modprobe.d/blacklist.conf Permission Denied

Should I be in root when I do this?

Yes, you need to be root to modify this file. However, the "sudo" in front of the command should take care of that. So I don't really understand the cause of the error message...

---

### Post by CyberDem0n on 2010-05-04
What about resume/suspend on t91mt?
On 2.6.31-21-generic it hangs even with vesa driver (not psb). Even more, it hangs in strict console mode, without any modules loaded and without programs runned.
On 2.6.31-14-generic it works perfectly with vesa but hangs with psb :(
And another strange feature, resume/suspend works only when i go into bios setup and choose "load default settinng",  save and quit, and after that run ubuntu.
May be it depends on bios version? I have 0601.

---

### Post by CyberDem0n on 2010-05-05
Ok. I played with some options in BIOS setup. Now suspend/resume from without psb always works.
With psb, after resume i found in dmsg this lines
> [  600.788138] INFO: task Xorg:1845 blocked for more than 120 seconds.
[  600.788154] "echo 0 > /proc/sys/kernel/hung_task_timeout_secs" disables this message.
[  600.788168] Xorg          D c08195c0     0  1845   1840 0x00400004
[  600.788188]  f6911f30 00200086 ee9a0000 c08195c0 f697cdf8 c08195c0 34c7ccfb 0000002b
[  600.788218]  c08195c0 c08195c0 f697cdf8 c08195c0 00000000 0000002b c08195c0 ef8d28c0
[  600.788245]  f697cb60 f6911f64 f697cb60 ef8d28f8 f6911f5c c0574d45 ffffffff f6911f64
[  600.788272] Call Trace:
[  600.788302]  [<c0574d45>] rwsem_down_failed_common+0x75/0x1a0
[  600.788322]  [<c01e83af>] ? rw_verify_area+0x5f/0xe0
[  600.788339]  [<c0574e8d>] rwsem_down_write_failed+0x1d/0x30
[  600.788356]  [<c0574f26>] call_rwsem_down_write_failed+0x6/0x10
[  600.788372]  [<c05744af>] ? down_write+0x1f/0x30
[  600.788389]  [<c01c4aa2>] sys_mmap_pgoff+0xb2/0x170
[  600.788406]  [<c01033ac>] syscall_call+0x7/0xb
Edit: This morning i installed uswsusp. Now suspend/resume with "s2ram --force --vbe_post" works even with psb ;-)

---

### Post by Schakal_No1 on 2010-05-09
Hi,

while trying this tutorial on my T91MT with UNR 10.04, i got 2 problems:

first the more important problem:
sudo dpkg -i xserver-xorg-video-psb_0.31.0-0ubuntu1~904um1_i386.deb

this produces an error saying
xserver-xorg-core collides with xserver-xorg-video-5
xserver-xorg-video-psb gives xserver-xorg-video-5 and is going to be installed
Error while working on xserver-xorg-video-psb_0.31.0-0ubuntu1_i386.deb (--install):
colliding packages - did not install xserver-xorg-video-psb

The other problem is, that 
sudo aptitude install linux-backports-modules-karmic
does not find the package linux-backports-modules-karmic but wirless worked out of the box so i did not care.

But my first problem is realy an important one because all the following packages depend on that.

Please help me.

PS: The error-message is translated by me because i get it in german, so i'm not so sure if i translated everything correct.

---

### Post by kgingeri on 2010-05-11
@Spl, Nice HowTo.

@Schakal_No1, yeah Lucid (10.04) is a problem - just trying to get it working now too and having errors. 
I followed another thread for the Display - you start about [here]("http://ubuntuforums.org/showpost.php?p=9275056&postcount=723") but it's a very active thread so that link will likely be out-dated soon!  

Working now **without** mods on Lucid 10.04:
- sound - without a hitch (I am running a T91MT)
- wireless

What needs mods:
- display - work in progress (see above link)
- grub mods for brightness buttons
- rotate button
- touchscreen - yet to solve - looks like source issue :(
- trackpad to enable two finger scroll
- power stuff like suspend/resume

---

### Post by kgingeri on 2010-05-14
> **spl said:**
> Yes, you need to be root to modify this file. However, the "sudo" in front of the command should take care of that. So I don't really understand the cause of the error message...

@Spl: "sudo" in front will not work, as the ">>" is a commandline redirect and has presidence over the sudo getting executed.  For example...

```
$ sudo echo "bla" >>/bla.txt 
```
fails as you don't have right to create a file in "/" and that is what is done BEFORE sudo is executed...however...
```
$ sudo bash -c "echo 'bla' >> /bla.txt" 
```
will work as the redirect doesn't happen until sudo has started bash, with the redirect ">>" encapsulated in double quotes. 

@everyone: It will work if you are root to execute command - either sudo the whole script or do a ```
$ exec sudo bash
``` to gain a live root prompt ("#")
;)

---

### Post by kgingeri on 2010-05-14
> **Schakal_No1 said:**
> Hi,

while trying this tutorial on my T91MT with UNR 10.04, i got 2 problems:

first the more important problem:
sudo dpkg -i xserver-xorg-video-psb_0.31.0-0ubuntu1~904um1_i386.deb

this produces an error saying
xserver-xorg-core collides with xserver-xorg-video-5
xserver-xorg-video-psb gives xserver-xorg-video-5 and is going to be installed
Error while working on xserver-xorg-video-psb_0.31.0-0ubuntu1_i386.deb (--install):
colliding packages - did not install xserver-xorg-video-psb

The other problem is, that 
sudo aptitude install linux-backports-modules-karmic
does not find the package linux-backports-modules-karmic but wirless worked out of the box so i did not care.

But my first problem is realy an important one because all the following packages depend on that.

Please help me.

PS: The error-message is translated by me because i get it in german, so i'm not so sure if i translated everything correct.

@Schakal_No1:  Unfortunately Lucid 10.04 is a whole different animal :(
Only some of this works.  I've reverted back to Karmic 9.10 for now as I could not even see anything from the touch screen in /proc/bus/input/devices and therefore the /dev/input/by-id folder and therefore any of the test programs.  If you don't need the touch screen, you can get the display working by check this [thread]("http://ubuntuforums.org/showthread.php?t=1229345").  But no touch screen at all - I suspect the kernel driver is not working :(

---

### Post by kgingeri on 2010-05-28
BTW another resource not mentioned here but in my records is found [here]("http://wiki.eeeuser.com/ubuntu_9.10_on_the_t91_t91mt"): 
[http://wiki.eeeuser.com/ubuntu_9.10_on_the_t91_t91mt](http://wiki.eeeuser.com/ubuntu_9.10_on_the_t91_t91mt)

---

### Post by Goldstorm on 2010-06-11
Hey guys. I found this interesting article on engadget today.

[http://www.engadget.com/2010/06/11/canonical-making-full-fledged-ubuntu-tablet-push-in-early-2011/](http://www.engadget.com/2010/06/11/canonical-making-full-fledged-ubuntu-tablet-push-in-early-2011/)

This is fantastic! I wonder if it will work on the T91MT.

---

### Post by RGanB on 2010-06-18
hi I know it's been a while since this thread saw action.    I ran xinput and saw, that two touchscreen where registered in the system. One was the device configured in Xorg.conf , the other was automatically added according to these two rules (I think)   /usr/share/hal/fdi/policy/20thirdparty/50-asustek.fdi   /etc/udev/rules.d/69-touchscreen.rules    I commented the touchscreen configuration in the xorg.conf and it hasn't frozen since.  And I wrote this entire post sing the onscreen keyboard.  greets RGB

---

### Post by yigal.weinstein on 2010-07-15
First the touch screen is working [http://ubuntuforums.org/showthread.php?t=1507489]("http://ubuntuforums.org/showthread.php?t=1507489") and there is a good chance multitouch will be resolved soon.

Second suspend appears to work if one removes the package 'vbetool' - I'm not sure the reason for this but I'm a happy beneficiary on my T91MT.  After rebooting, or perhaps before, issue 'sudo s2ram --force', and if your device is like mine it will go to sleep happily and awake just as easily.  If someone more knowledgeable in this area would explain to me why this works I would be very appreciative.  I simply took the observation of Alan for his Acer 751h, [http://code.google.com/p/gma500/wiki/PPARepository]("http://code.google.com/p/gma500/wiki/PPARepository").

We shall veni vidi vici I have faith.

> **kgingeri said:**
> 
What needs mods:
- display - work in progress (see above link)
- grub mods for brightness buttons
- rotate button
- touchscreen - yet to solve - looks like source issue :(
- trackpad to enable two finger scroll
- power stuff like suspend/resume

---

### Post by tuxinator on 2011-01-20
I am having an issue with the poulsbo driver section.  I get a 404 error on each one of the files wget tries to download.  I put the url in Firefox and dropbox can't find the parent directory [http://dl.dropbox.com/u/1338581/Gma500/deb](http://dl.dropbox.com/u/1338581/Gma500/deb).  Have the debs been moved somewhere else?

---

### Post by tuxinator on 2011-01-20
I am having an issue with the poulsbo driver section.  I get a 404 error on each one of the files wget tries to download.  I put the url in Firefox and dropbox can't find the parent directory [http://dl.dropbox.com/u/1338581/Gma500/deb](http://dl.dropbox.com/u/1338581/Gma500/deb).  Have the debs been moved somewhere else?

---

### Post by jtjs on 2011-01-20
I suggest ignoring the above and checking out this thread instead: [http://ubuntuforums.org/showthread.php?t=1229345&highlight=t91mt](http://ubuntuforums.org/showthread.php?t=1229345&highlight=t91mt)

And for the touchscreen, check out the first post in this thread: [http://ubuntuforums.org/showthread.php?t=1507489&highlight=t91mt](http://ubuntuforums.org/showthread.php?t=1507489&highlight=t91mt)

---

