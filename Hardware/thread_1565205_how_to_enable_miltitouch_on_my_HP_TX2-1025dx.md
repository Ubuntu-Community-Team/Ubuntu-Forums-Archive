---
title: "how to enable miltitouch on my HP TX2-1025dx"
date: 2010-08-31
forum: Hardware
---

### Post by limitless red on 2010-08-31
I've gotten my touch screen to work natively in lucid, however both screen rotation and miltitouch are not natively supported. I'd be glad to supply any information about the laptop as needed. 


How so I enable miltitouch and how do I rotate the ptouch input when I rotate screen?

---

### Post by Favux on 2010-08-31
Hi limitless red,

Welcome to Ubuntu forums!

First some background.  We need to know your N-trig firmware version.  Best way to get that is through Windows.  Are you dual booting?  Vista or Win7?

To get multi-touch you may need to update your hid-ntrig.ko.  More on that later.

Most likely with a default Lucid install your stylus is on the linuxwacom driver and touch is supplied by the evdev driver.  To confirm check Xorg.0.log /var/log.  So to rotate you need a hybrid rotation script that will handle linuxwacom and evdev.  See "4) Rotation to tablet b)" at the [N-trig HOW TO]("http://ubuntuforums.org/showpost.php?p=7863677&postcount=1").

---

### Post by limitless red on 2010-08-31
I dual boot windows 7. How would I check my ntrig firmware?

---

### Post by Favux on 2010-08-31
Not sure.  Look for something labeled N-trig and scout around.  Probably Control Panel or whatever it now is, in System or Devices or whatever.  Be interested in knowing where it's located when you find it.

---

### Post by limitless red on 2010-08-31
There is a recurring hardware thing called a human interface device, or HID. The hid driver on this one is 6.1.7600 maybe that's the firmware version?

---

### Post by Favux on 2010-08-31
That could be.  HID means human interface device.  Ayuthia recommends the 2.239 software bundle which contains the 4.6.5.8.5 firmware.  So maybe not quite right.  In Properties the device driver should mention N-trig.  So the other way to go is check the HP website for firmware updates and see if you can figure out where it wants to install.

Edit:  Meantime let's look at the output of 'xinput --list' in a terminal.

---

### Post by limitless red on 2010-08-31
my n-trig firmware is 2.184 A. ill post my xinput --list after i hop back onto ubuntu

---

### Post by Favux on 2010-08-31
Great!  So version 2.184, which I think was the first Win7 version.  It would help me if you could tell me how you determined that.  I can add that to the HOW TO.  That sounds like the software package version that contains the firmware.  I originally thought that was the firmware version, but apparently not.  Unless I got it wrong.  So the more info. about that the better.

So what you'll want to do is update to the 2.239 version from HP.  Ayuthia says that's the best and stablest he's seen so far.  If there's a later version it might be better but he hasn't tested it.  Afraid to lose the "good" version apparently.

---

### Post by limitless red on 2010-08-31
well, what i did was look it up on hp's website for drivers, and then i installed that driver. it said from hp's website that it was the most recent driver, so please help me find this ayuthia's driver. 

EDIT 32: hp's website i used: [http://h10025.www1.hp.com/ewfrf/wc/softwareDownloadIndex?softwareitem=ob-79640-1&lc=en&dlc=en&cc=us&product=3860702&sw_lang=&os=4062](http://h10025.www1.hp.com/ewfrf/wc/softwareDownloadIndex?softwareitem=ob-79640-1&lc=en&dlc=en&cc=us&product=3860702&sw_lang=&os=4062)
n-trig's website i used: [http://www.n-trig.com/Content.aspx?Page=Hints](http://www.n-trig.com/Content.aspx?Page=Hints)
EDIT: n-trig's website says that there are only DuoSense drivers for the 64-bit tx2's, while mine is a 32-bit tx2 (even though the amd sticker on the front has a 64 on it...)


here's my xinput --list:

xinpujc@jc-laptop:~$ xinput --list
&#9121; Virtual core pointer                        id=2    [master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer                  id=4    [slave  pointer  (2)]
&#9116;   &#8627; SynPS/2 Synaptics TouchPad                  id=11    [slave  pointer  (2)]
&#9116;   &#8627; Macintosh mouse button emulation            id=12    [slave  pointer  (2)]
&#9123; Virtual core keyboard                       id=3    [master keyboard (2)]
    &#8627; Virtual core XTEST keyboard                 id=5    [slave  keyboard (3)]
    &#8627; Power Button                                id=6    [slave  keyboard (3)]
    &#8627; Video Bus                                   id=7    [slave  keyboard (3)]
    &#8627; Power Button                                id=8    [slave  keyboard (3)]
    &#8627; Sleep Button                                id=9    [slave  keyboard (3)]
    &#8627; AT Translated Set 2 keyboard                id=10    [slave  keyboard (3)]
    &#8627; HP WMI hotkeys                              id=13    [slave  keyboard (3)]

---

### Post by Favux on 2010-08-31
OK, I'll try to figure that out.

The sticker means you have dual AMD 64-bit CPU's.  But they installed the 32-bit version of Win7, not the 64-bit version.  I believe there was a free upgrade to 64 from 32 bit at one point.  If no longer available I doubt it costs much.  Something to think about anyway.  Did you install 64-bit Ubuntu?

Don't see N-trig in xinput list at all.  So let's look at Xorg.0.log in /var/log.  Compress it by right clicking on it and choosing Create Archive.  Then use Manage Attachments below to attach it to your next post.

---

### Post by Favux on 2010-09-01
Hi limitless red,

OK, I found the 32-bit bundle for HP at the N-trig site:  [http://www.n-trig.com/Content.aspx?Page=Bulletin_Board](http://www.n-trig.com/Content.aspx?Page=Bulletin_Board)  Apparently at HP it's only available for 64-bit as yet.

---

### Post by limitless red on 2010-09-01
hmm. the bios doesn't mention anything about 64 bit architecture, and i've wondered that ever since i bought the laptop (used form ebay). it was advertizd as a 32bit laptop, but googleing and hp's website told me it was a 64bit laptop. i bought it just the same, even though the guy said he was running windows 7 32 bit. i couldn't get 10.04 to even boot from live disk in 64bit so i went with the 32 bit for now. that may or may not be making a difference :P

oh, and it only came with 1gb of ram :?

attached is my logfile you requested.

---

### Post by Favux on 2010-09-01
Hmmm.

On the back of the laptop there should be a backplate with model name and number.  It says TX2-1025dx?

Not seeing anything in Xorg.0.log that says N-trig.  Not really seeing anything that might be the digitizer.  Are pen and touch still working?  Let's look at:
```
lsusb
```
and
```
dmesg | grep [Nn]trig
```

---

### Post by limitless red on 2010-09-01
jc@jc-laptop:~$ lsusb
Bus 007 Device 002: ID 08ff:1600 AuthenTec, Inc. AES1600
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 005: ID 0a5c:2154 Broadcom Corp. 
Bus 003 Device 004: ID 0a5c:4503 Broadcom Corp. 
Bus 003 Device 003: ID 0a5c:4502 Broadcom Corp. 
Bus 003 Device 002: ID 0a5c:4500 Broadcom Corp. BCM2046B1 USB 2.0 Hub (part of BCM2046 Bluetooth)
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 003: ID 0bda:0158 Realtek Semiconductor Corp. Mass Storage Device
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub


and grepping that didn't return anything.

---

### Post by limitless red on 2010-09-01
after running that installation package, i now ave a tray icon that displays a bunch of n-trig functions in windows 7.

---

### Post by Favux on 2010-09-01
Alright, good.  When you boot to linux has:
```
xinput --list
```
changed?  Do you now see ntrig?

---

### Post by limitless red on 2010-09-01
well, HP's 2.138 bundle is working. everytime i try to install n-trig's updated version it throws a fatal error.

jc@jc-laptop:~$ xinput --list
&#9121; Virtual core pointer                        id=2    [master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer                  id=4    [slave  pointer  (2)]
&#9116;   &#8627; HID 0a5c:4503                               id=11    [slave  pointer  (2)]
&#9116;   &#8627; SynPS/2 Synaptics TouchPad                  id=13    [slave  pointer  (2)]
&#9116;   &#8627; Macintosh mouse button emulation            id=14    [slave  pointer  (2)]
&#9116;   &#8627; N-Trig Pen                                  id=16    [slave  pointer  (2)]
&#9116;   &#8627; N-Trig MultiTouch                           id=17    [slave  pointer  (2)]
&#9116;   &#8627; N-Trig Touchscreen                          id=18    [slave  pointer  (2)]
&#9123; Virtual core keyboard                       id=3    [master keyboard (2)]
    &#8627; Virtual core XTEST keyboard                 id=5    [slave  keyboard (3)]
    &#8627; Power Button                                id=6    [slave  keyboard (3)]
    &#8627; Video Bus                                   id=7    [slave  keyboard (3)]
    &#8627; Power Button                                id=8    [slave  keyboard (3)]
    &#8627; Sleep Button                                id=9    [slave  keyboard (3)]
    &#8627; HID 0a5c:4502                               id=10    [slave  keyboard (3)]
    &#8627; AT Translated Set 2 keyboard                id=12    [slave  keyboard (3)]
    &#8627; HP WMI hotkeys                              id=15    [slave  keyboard (3)]

---

### Post by Favux on 2010-09-01
Hi limitless red,

Well the 2.138 software bundle did the trick because we're now seeing:
```
&#9116; &#8627; N-Trig Pen id=16 [slave pointer (2)]
&#9116; &#8627; N-Trig MultiTouch id=17 [slave pointer (2)]
&#9116; &#8627; N-Trig Touchscreen id=18 [slave pointer (2)]
```
Somehow the N-trig firmware apparently wasn't installed.  And you're right, with 1 GB of RAM no reason to go 64-bit.  So I guess we can proceed.  I wish we could get the 2.239 software bundle to install though.  What is the whole fatal error message it's spitting out?

---

### Post by limitless red on 2010-09-01
I was able to install the latest drivers after some effort. And xinput still displays ntrig. What now?

---

### Post by Favux on 2010-09-01
Very good!  How did you manage that?  Did you happen to see the firmware version included in the 2.239 bundle?  I noticed the firmware version is included in the label for the Dell version of the bundle.
> And xinput still displays ntrig.
Just like before?  The three n-trig lines with no duplicates?

Next step is to update your hid-ntirg.ko from the default one in Lucid's 2.6.32 kernel to Rafi's latest 5-4-10 version.  Link to it is near the top of the [N-trig HOW TO]("http://ubuntuforums.org/showpost.php?p=7863677&postcount=1").  Instructions are in "1) Lucid: Patching hid-ntrig.c with... a)".

---

### Post by limitless red on 2010-09-02
> **Favux said:**
> Very good!  How did you manage that?  Did you happen to see the firmware version included in the 2.239 bundle?  I noticed the firmware version is included in the label for the Dell version of the bundle.

Just like before?  The three n-trig lines with no duplicates?

Next step is to update your hid-ntirg.ko from the default one in Lucid's 2.6.32 kernel to Rafi's latest 5-4-10 version.  Link to it is near the top of the [N-trig HOW TO]("http://ubuntuforums.org/showpost.php?p=7863677&postcount=1").  Instructions are in "1) Lucid: Patching hid-ntrig.c with... a)".


sorry for the delay, my work schedulee has been very funny.

when i was following the directiions, i encoountered a problem. im having a hard time compiling the drivers in the proper directory. can you shed any light on thatt?

---

### Post by Favux on 2010-09-02
I need a little more information.  What directory path are you using?  Is there an error message you can show me?  Etc.

---

### Post by limitless red on 2010-09-02
with step 4 of [http://linuxfans.keryxproject.org/?page_id=23](http://linuxfans.keryxproject.org/?page_id=23) it doesn't cd anywhere, saying that there is no directory of that name.

EDIT: i have a 2.6.28 directory, but for some reason i don't have the 2.6.31 or 2.6.32 that i need

EDIT AGAIN: i am running the 2.6.32 kernel according to uname -r

---

### Post by limitless red on 2010-09-02
i am also having problems building from the most recent ntrig.c file. i get a whole list of syntactial errors when i try to gcc it.

---

### Post by limitless red on 2010-09-02
sorry for the gross triple posting, but after some noodling around i got the patch and figured out how to use apt-get source. however, when i try to apply the patch, 6/8 hunks fail. 

jc@jc-laptop:~/linux-2.6.32$ sudo patch -p1 < .//hid-ntrig.c-confidence.patcharch/             firmware/         .mailmap          samples/
block/            fs/               MAINTAINERS       scripts/
COPYING           .gitignore        Makefile          security/
CREDITS           include/          mm/               sound/
crypto/           init/             net/              tools/
debian/           ipc/              ntrig-v6/         ubuntu/
debian.master/    Kbuild            ntrig-v6.tar.bz2  usr/
Documentation/    kernel/           README            virt/
drivers/          lib/              REPORTING-BUGS    
jc@jc-laptop:~/linux-2.6.32$ sudo patch -p1 < ./ntrig-v6/hid-ntrig.c-confidence.patch
patching file drivers/hid/hid-ntrig.c
Hunk #1 FAILED at 24.
Hunk #2 FAILED at 61.
Hunk #3 FAILED at 95.
Hunk #4 FAILED at 122.
Hunk #5 FAILED at 158.
Hunk #6 FAILED at 171.
Hunk #7 FAILED at 233.
Hunk #8 FAILED at 257.
8 out of 8 hunks FAILED -- saving rejects to file drivers/hid/hid-ntrig.c.rej
jc@jc-laptop:~/linux-2.6.32$ 


attached is the rejects file.

---

### Post by Favux on 2010-09-02
Alright, first thing is the hid-ntrig.c from [Rafi's link]("http://ubuntuforums.org/showpost.php?p=9236052&postcount=977") is already patched.  You don't have to patch it, just compile it.  That should help.

---

### Post by limitless red on 2010-09-02
thanks! i got to the end of the section for lucid from that post. so now what?

also, multitouch still isnt working :(

---

### Post by Favux on 2010-09-02
Excellent!

You rebooted, correct?  You could look at the output of:
```
xinput --list
```
and at Xorg.0.log in /var/log just to see where things are at now.

Next step is to update xf86-input-wacom.  That should give you the new n-trig ID patches and the gestures/multitouch patches.  See **II.** at the [Bamboo P&T HOW TO]("http://ubuntuforums.org/showpost.php?p=9496609&postcount=1") or Section 2 in the [linuxwacom HOW TO]("http://ubuntuforums.org/showpost.php?p=6546012&postcount=1").

---

### Post by Favux on 2010-09-02
And you're right.  I should update the HOW TO for compiling the hid-ntrig.ko in Lucid.

How does this look?  Obviously adapted from Ayuthia's.


How to Compile hid-ntrig.ko in Lucid

Preparation:  Open a terminal.
 
Step 1:  Install any missing kernel development tools
sudo apt-get build-dep linux

Step 2:  Install any missing dependencies needed for the source code
sudo apt-get build-dep linux-image-$(uname -r)

Step 3:  Change directory to the Desktop
cd Desktop

Building the kernel module

Step 1:  Download the Ubuntu kernel source code
apt-get source linux-image-$(uname -r)

Step 2:  Download Rafi Rubin's 5-4-10 version of hid-ntrig.c
wget [http://ofb.net/~rafi/2010_05_04_hid-ntrig.c](http://ofb.net/~rafi/2010_05_04_hid-ntrig.c)

Step 3:  Copy the 2010_05_04_hid-ntrig.c over the one in the kernel source code
cp 2010_05_04_hid-ntrig.c linux-2.6.32/drivers/hid/hid-ntrig.c

Step 4:  Go into the linux-2.6.32 source code HID folder directory to build the module
cd linux-2.6.32/drivers/hid

Step 5:  Compile the HID modules
sudo make -C/lib/modules/`uname -r`/build M=`pwd` modules

Step 6:  Copy the hid-ntrig.ko file to the proper place
sudo cp hid-ntrig.ko /lib/modules/`uname -r`/kernel/drivers/hid/

Step 7:  Update the module dependencies just in case
sudo depmod -a

---

### Post by limitless red on 2010-09-15
again, sorry for the delay. that set of instructions does look a lot easier to follow, and it is very precise. now on to your last post, and i will hopefully report back asap.

---

### Post by limitless red on 2010-09-15
when compiling the xf86-input-wacom make throws this error:

make[2]: Nothing to be done for `all'.

and somewhere in all this my n-trig isn't listed in the xinput --list anymore


i am using the test3 xorg.conf supplied by the post, and when i lsmod | grep ntrig it lists this:

hid_ntrig               3572  0 
usbhid                 36110  1 hid_ntrig
hid                    67032  2 hid_ntrig,usbhid


any ideas?

---

### Post by Favux on 2010-09-15
Usually:
```
make[2]: Nothing to be done for `all'.

```
doesn't indicate an error.  Were there additional errors associated with it?  Did you go on to do 'sudo make install'?
> and somewhere in all this my n-trig isn't listed in the xinput --list anymore
Did you try rebooting a few times?  What does the xinput --list show after that?  Check the properties of your compiled hid-ntrig.ko and find out its size.  That will help us sort out that output.
> i am using the test3 xorg.conf supplied by the post,
I kind of wanted to hold off on the xorg.conf in Lucid and see if we could get things working through the 10-wacom.conf.  That may be conflicting with the xorg.conf.

---

### Post by limitless red on 2010-09-15
alright so i'm gonna roll back my xorg.conf and see what i can do about getting ntrig back in my xinput.

how should i go about this?

---

### Post by Favux on 2010-09-15
Well, at this point since you have the xorg.conf entries (did you have an xorg.conf?), just comment out (#) the N-trig sections and lines in "ServerLayout".

Try rebooting several times and then let's look at the output of 'xinput --list'.  And of 'lsmod | grep hid-ntrig'.

---

### Post by limitless red on 2010-09-15
xinput --list has my n-trig stuff...only when i have the touchscreen enabled (ie: having it rotated down into tablet mode) so i now have those displayed. as far as lsmod | grep hid_ntrig:

hid_ntrig               3572  0 
usbhid                 36110  1 hid_ntrig
hid                    67032  2 hid_ntrig,usbhid

---

### Post by Favux on 2010-09-16
Ok, I think:
```
hid_ntrig 3572 0 
```
is your newly compiled hid-ntrig.ko.  Like I said you could check it by verifying the size (and date) in Properties.  Remember it is at linux-2.6.32/drivers/hid/hid-ntrig.ko and you copied it to /lib/modules/`uname -r`/kernel/drivers/hid/.
> xinput --list has my n-trig stuff...only when i have the touchscreen enabled (ie: having it rotated down into tablet mode) so i now have those displayed. as far as lsmod | grep hid_ntrig:
Sorry, I don't understand.  Is it there now?  Does your stylus work?  I assume this is after commenting out the xorg.conf entries, correct?

---

### Post by limitless red on 2010-09-16
> Sorry, I don't understand.  Is it there now?  Does your stylus work?  I  assume this is after commenting out the xorg.conf entries, correct?

yes, xinput --list only displays my n-trig stuff when i have the screen rotated down in "tablet" mode. when i was checking it before i had it in "notebook" mode, with the keyboard visible and the touch screen disabled. multitouch, however, is still not working. on step 3 of [http://ubuntuforums.org/showpost.php?p=6546012&postcount=1](http://ubuntuforums.org/showpost.php?p=6546012&postcount=1) i get this error:

jc@jc-laptop:~/Desktop/xf86-input-wacom$ ./autogen.sh --prefix=/usr
./autogen.sh: 9: autoreconf: not found


which means that the distribution file i got with git is possibly bad?

---

### Post by Favux on 2010-09-16
Well, I don't think xf86-input-wacom should make any difference on whether N-trig stuff shows up in xinput.  I'm puzzled as to why rotation to portrait mode causes it to appear.

I've run into;
```
./autogen.sh: 9: autoreconf: not found

```
once or twice before and haven't found a solution yet.  It seems to either mean a library or dependency is missing or there is a problem in the Makefile.  Yet I've tried all I can think of.  So it looks like we're stuck on xf86-input-wacom anyway.

So a couple mysteries/problems to solve.

---

### Post by limitless red on 2010-09-16
well, after doing some more noodling around, i read the README and it said somethign about executing it from a tarball. so i proceeded to find the tarball, and now i have it configured and "make"'d. i created a file "10-wacom.conf" in the /usr/lib/X11/xorg.conf.d/ directory (there wasn't one already...) and i used the sample you provided in [http://ubuntuforums.org/showthread.php?t=1515562](http://ubuntuforums.org/showthread.php?t=1515562) .

---

### Post by Favux on 2010-09-16
Can you explain how you got rid of "./autogen.sh: 9: autoreconf: not found" in a little more detail?

OK, with the sample 10-wacom.conf only the stylus should work.  Which is OK, for now.  With xf86-input-wacom now installed we want to see if we can use an xsetwacom script.  We'll use this whether we go the .conf route or the xorg.conf route.  Install it by:
> For Lucid you use a xsetwacom script file instead of wacomcpl and wacomcpl's .xinitrc (attached below).
To set it up to auto-start, download the attached file, and rename it .xsetwacom.sh (or whatever you want) and place it in your home directory. Remember it will be a hidden file. To enable the xsetwacom commands in the .xsetwacom.sh file to apply to Xserver through a reboot you enter in a terminal:
```
chmod +x ~/.xsetwacom.sh
```
or you could right click on the file and in Properties, in the Permission tab, check Execute as program. Then go to System->Preferences->Startup Applications and click on add and for the command write "sh /home/yourusername/.xsetwacom.sh" (without the quotes). You can also change your settings on the fly using the xsetwacom parameters in a terminal. They only apply during the current session.

---

### Post by limitless red on 2010-09-16
> Can you explain how you got rid of "./autogen.sh: 9: autoreconf: not found" in a little more detail?i didn't i worked around it. instead of cloning the file (git) which was providing me with that error, i downloaded the tarball of xf86-input-wacom and configured that instead.

your script, when i executed it myself in terminal threw a ton of errors, mostly dealing with naming. my xinput --list shows "N-trig Pen stylus" instead of "N-trig Pen" like you have in the script. but how should i revise it?

EDIT: xsetwacom itself does work however. i copied a random line and properly named my N-trig device, and it didn't give me any errors.





> jc@jc-laptop:~$ ./.xsetwacom.sh 
jc@jc-laptop:~$ ./.xsetwacom.sh 
Cannot find device 'N-Trig Pen'.
Cannot find device 'N-Trig Pen'.
Cannot find device 'N-Trig Pen'.
Cannot find device 'N-Trig Pen'.
Cannot find device 'N-Trig Pen'.
Cannot find device 'N-Trig Pen'.
Cannot find device 'N-Trig Pen'.
Cannot find device 'N-Trig Pen'.
Cannot find device 'N-Trig Pen'.
Cannot find device 'N-Trig Pen'.
Cannot find device 'N-Trig Pen'.
Cannot find device 'N-Trig Pen'.
Cannot find device 'N-Trig Pen'.
Cannot find device 'N-Trig Touchscreen'.
Cannot find device 'N-Trig Touchscreen'.
Cannot find device 'N-Trig Touchscreen'.
Cannot find device 'N-Trig Touchscreen'.
Cannot find device 'N-Trig Touchscreen'.
Cannot find device 'N-Trig Touchscreen'.
Cannot find device 'N-Trig Touchscreen'.
Cannot find device 'N-Trig Touchscreen'.
Cannot find device 'N-Trig Touchscreen'.
Cannot find device 'N-Trig Touchscreen'.



---

### Post by Favux on 2010-09-16
> instead of cloning the file (git) which was providing me with that error, i downloaded the tarball of xf86-input-wacom and configured that instead.
Ah, now I get it.  I hope you used 0.10.8.
> your script, when i executed it myself in terminal threw a ton of errors, mostly dealing with naming. my xinput --list shows "N-trig Pen stylus" instead of "N-trig Pen" like you have in the script. but how should i revise it?

EDIT: xsetwacom itself does work however. i copied a random line and properly named my N-trig device, and it didn't give me any errors.
Exactly, if 'xinput --list' is showing different "Device names" use those instead of the ones in the script.  What's your xinput output look like?

---

### Post by limitless red on 2010-09-16
> jc@jc-laptop:~$ xinput --list
&#9121; Virtual core pointer                        id=2    [master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer                  id=4    [slave  pointer  (2)]
&#9116;   &#8627; SynPS/2 Synaptics TouchPad                  id=11    [slave  pointer  (2)]
&#9116;   &#8627; Macintosh mouse button emulation            id=12    [slave  pointer  (2)]
&#9116;   &#8627; N-Trig MultiTouch                           id=14    [slave  pointer  (2)]
&#9116;   &#8627; N-Trig Pen eraser                           id=15    [slave  pointer  (2)]
&#9116;   &#8627; N-Trig Pen stylus                           id=16    [slave  pointer  (2)]
&#9116;   &#8627; N-Trig Touchscreen                          id=17    [slave  pointer  (2)]
&#9123; Virtual core keyboard                       id=3    [master keyboard (2)]
    &#8627; Virtual core XTEST keyboard                 id=5    [slave  keyboard (3)]
    &#8627; Power Button                                id=6    [slave  keyboard (3)]
    &#8627; Video Bus                                   id=7    [slave  keyboard (3)]
    &#8627; Power Button                                id=8    [slave  keyboard (3)]
    &#8627; Sleep Button                                id=9    [slave  keyboard (3)]
    &#8627; AT Translated Set 2 keyboard                id=10    [slave  keyboard (3)]
    &#8627; HP WMI hotkeys  


also, i noticed that when touching and dragging around, touching the screen should register a left mouse button, and dragging it around (like on a desktop) should make a multiple select box (like when you click and drag). however now it seems that the laptop is "losing" the left click, so that when i drag my finger it seems like it is constantly clicking along where im' dragging, instead of doing a click-drag

---

### Post by Favux on 2010-09-16
Hi limitless red,

Thanks for the 'xinput -llist'.  That helps orient me.  I don't know where the N-trig eraser line is coming from.  It's probably spurious so let's ignore it.

For the single finger touch we have active in the xsetwacom script currently the "Device Name" you probably should be using is "N-Trig Touchscreen".  If you're not using that one doing so may help straighten out the left click.

I'm very excited that you are able to get stylus and touch in Lucid with the 10-wacom.conf's N-trig snippet and the xsetwacom script.

A couple other parameters you could play with are ClickForce, and maybe Suppress and TapTime.

One other thing we should try is to change the N-trig snippet from selecting just the stylus to the tablet.  So in the N-trig snippet:
```
MatchProduct "HID 1b96:0001|N-Trig Pen"
```
would change to:
```
MatchProduct "HID 1b96:0001"
```
Experimenting with 10-wacom.conf can break X.  So be sure you have the current working wacom.conf backed up and are able to restore it from the command line.

I'm eager to test multitouch/gestures next!

---

### Post by Ayuthia on 2010-09-17
I hope you don't mind me jumping in, but I think that you might want to use N-Trig MultiTouch instead of N-Trig Touchscreen.  The Touchscreen device option always shows up with the MultiTouch, but not the other way around.  However, when the Touchscreen option shows up with the MultiTouch, the Touchscreen data does not provide anything.  At least that is what I have found with the various firmware versions.

---

### Post by Ayuthia on 2010-09-17
> **Favux said:**
> Well, I don't think xf86-input-wacom should make any difference on whether N-trig stuff shows up in xinput.  I'm puzzled as to why rotation to portrait mode causes it to appear.

I've run into;
```
./autogen.sh: 9: autoreconf: not found

```
once or twice before and haven't found a solution yet.  It seems to either mean a library or dependency is missing or there is a problem in the Makefile.  Yet I've tried all I can think of.  So it looks like we're stuck on xf86-input-wacom anyway.

So a couple mysteries/problems to solve.

I am currently trying to compile a package and just ran into it.  It looks like automake needs to be installed.  You might also need libtool if it is not already installed.

---

### Post by Favux on 2010-09-17
Did have automake and libtool installed.  Maybe a different version of automake?  They updated it and didn't tell us?  Isn't autoreconf.

---

### Post by Ayuthia on 2010-09-17
It could be.  I am currently on Maverick with a fairly clean install (I have not compiled any packages until a few minutes ago).  When I installed automake, it picked up the following packages:
```

autoconf{a} automake autotools-dev{a} m4{a}

```

---

### Post by Favux on 2010-09-17
I didn't try to compile xf86-input-wacom yet on Maverick because it came with 0.10.8 as the default version which is good enough for the Bamboo P&T.  But for the N-trig you would probably want to because Rafi's N-trig Vendor and Product ID patch was added 6 days after 0.10.8 came out.

---

### Post by Ayuthia on 2010-09-17
> **Favux said:**
> I didn't try to compile xf86-input-wacom yet on Maverick because it came with 0.10.8 as the default version which is good enough for the Bamboo P&T.  But for the N-trig you would probably want to because Rafi's N-trig Vendor and Product ID patch was added 6 days after 0.10.8 came out.

Actually, everything is working out of the box in Maverick for the N-trig device.  The only thing that I am doing is checking out the multitouch options in the Netbook Edition.  I am guessing that the developers backported the changes.

---

### Post by Favux on 2010-09-17
That's lucky!  You still have to compile a wacom.ko to get the Bamboo working!  Any progress on the autogen.sh error?

---

### Post by limitless red on 2010-09-18
> **Ayuthia said:**
> Actually, everything is working out of the box in Maverick for the N-trig device.  The only thing that I am doing is checking out the multitouch options in the Netbook Edition.  I am guessing that the developers backported the changes.


did i hear that right? multitouch is working for certain in Maverick? i will udpate fo sho :D

however, i do want it working in lucid, now simply for the sake of knowing how to do it. i want to eventually give back to the community that has given me so much

---

### Post by Ayuthia on 2010-09-18
> **limitless red said:**
> did i hear that right? multitouch is working for certain in Maverick? i will udpate fo sho :D

however, i do want it working in lucid, now simply for the sake of knowing how to do it. i want to eventually give back to the community that has given me so much

The multitouch gestures are taking shape in Maverick.  From what I have seen so far, only the Ubuntu Netbook Edition has it running in the Unity desktop.  However the [multitouch wiki]("https://wiki.ubuntu.com/Multitouch") has a couple of demos showing the pinch/zoom and scrolling in inkscape and evince.  I have not found out how to get them activated as of yet though.

So to answer your question, multitouch is there, but it is going to be in the very early stages.  At least that is my guess since there is only less than a month left.  I am thinking that 11.04 is where people will most likely see the multitouch in action.

---

### Post by Ayuthia on 2010-09-18
> **Favux said:**
> That's lucky!  You still have to compile a wacom.ko to get the Bamboo working!  Any progress on the autogen.sh error?

I am thinking that it has something to do with the autoconf package.  However, I have not tried it out in Lucid yet.  The strange part about it is that I tried to remove the autoconf package, but Maverick would not let me do it without removing automake.  

The wacom source from git does get through the autogen.sh portion though.  I am going to see if I can duplicate the issue in Lucid.

---

### Post by Ayuthia on 2010-09-18
I just tested it in Lucid and received the autoreconf message.  However, Lucid is just like Maverick where it will add autoconf when install automake.  If you install autoconf, it will pull automake also.

Once I installed the packages, I was able to go further.  I then ran into the xorg-macro version issue which I resolved by using git to get the most recent copy to build.  After that, the autogen.sh worked fine and I had a clean compile.

---

### Post by Favux on 2010-09-18
Awesome!  The dependency line in the Bamboo HOW TO includes autoconf.  I could swear I did an apt-get on automake also.  I'll have to check my notes to be for sure.  If I remembered to keep them.

---

