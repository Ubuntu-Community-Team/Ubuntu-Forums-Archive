---
title: "Freezes after waking from sleep mode"
date: 2010-02-18
forum: Hardware
---

### Post by el_manaba on 2010-02-18
I set the Power Management Preferences to put the PC in sleep mode after 1 hr. It does - the computer appears to be off except the blinking system status LED. Even the mouse turns off in this mode! (see my unresolved problem in [http://ubuntuforums.org/showthread.php?t=1399730](http://ubuntuforums.org/showthread.php?t=1399730)) When I turn the system back on, I get a black screen and and the keyboard and mouse light up. But I get no response by pushing keyboard and mouse buttons (when I press Caps Lock, the corresponding LED on the keyboard doesn't light up). I have to resort to a hard kill.

Any ideas?

---

### Post by el_manaba on 2010-02-20
Nobody?  Did I say something wrong?

---

### Post by Jonodaigle on 2010-02-21
Same problem here, have no idea what's going on. this is on a HP pavilion laptop.

---

### Post by el_manaba on 2010-05-23
This problem persists after upgrading to 10.04.  Any ideas?

---

### Post by malkdude on 2010-06-10
Quote
 				 				**Freezes after waking from sleep mode** 			
 			 			 		   		 		 		I set the Power  Management Preferences to put the PC in sleep  mode after 1 hr. It does - the computer appears to be off except the  blinking system status LED. Even the mouse  turns off in this mode! (see my unresolved problem in [http://ubuntuforums.org/showthread.php?t=1399730](http://ubuntuforums.org/showthread.php?t=1399730))  When I turn the system back on, I get a black screen and and the  keyboard and mouse light up. But I get no  response by pushing keyboard and mouse  buttons (when I press Caps Lock, the corresponding LED on the keyboard  doesn't light up). I have to resort to a hard kill.

Any ideas?

Hi El_manaba, my workaround for this problem is to disable power saving. I know it is not really a solution, but at least you don't lose work this way. In a terminal, I entered:

sudo setterm -blank 0
sudo setterm -powerdown 0

Then I pressed <Ctrl>+<Alt>+<F1>. This takes you to terminal mode (or whatever it is really called, I don't know). There, after logging in, I typed

sudo setterm -powersave off

and then I pressed <Ctrl>+<Alt>+<F7> to go back to GUI mode. What these commands do is, they disable powersaving, so that the computer doesn't go to sleep after a while, because sleep/hibernate are buggy on my laptop (and for many other people, as you can see in the forums). After the computer sleeps and wakes up, the mouse draws itself but doesn't respond. The keyboard works fine though, but I need my mouse! It's probably a bug in pm-utils, where the developer(s) perhaps forgot to reload the mouse module after waking up... Hmm, at least it's my 2-cent after spending many hours reading about this problem on the internet... 

Oh, before trying this workaround, did you try pressing <Ctrl>+<Alt>+<F7> when the screen goes blank? Do you get a blinking small horizontal line at the top left corner? If so, then perhaps that simply pressing those keys might restart the GUI and solve your problem! Good luck!

---

### Post by malkdude on 2010-06-10
As an update, my laptop went fine for a long time but, after I shut it down, and rebooted, the system went to sleep again after about 20 minutes of inactivity, and the same problem occured (the mouse froze). Of course, it would be annoying to input these commands in my last post every time one logs in. There's got to be a way to add them to the standard boot process... My knowledge of linux is rather limited... Ideas anyone??

---

### Post by efflandt on 2010-06-10
You have given no clue what hardware you have.  Often it is related to video.  What video chip do you have (output of **lspci** or that section from **sudo lspci -v**).  And are you using default modules, or which proprietary module?

For older ATI X1300 video and default modules, I resolved my suspend/hibernate issues (and general video sluggishness) with **nomodeset** kernel boot option.

For an older laptop using nVidia(96) driver, I had to do something else.  See my suggestion in [http://ubuntuforums.org/showthread.php?t=1506393](http://ubuntuforums.org/showthread.php?t=1506393)

---

### Post by malkdude on 2010-06-11
I personally use an old ATI (xpress 200m), and I just created a script to be run during the boot process with the commands above. I think it works now (let's cross our fingers). Here is what I did. I typed in

sudo gedit /etc/init.d/powersaveoff

This will create and open an empty file called powersaveoff. There, I inputted:

#!/bin/bash
# a script to disable powersave because suspend is still buggy on my system

setterm -blank 0
setterm -powerdown 0
setterm -powersave off

saved and exited. Then I changed the permissions to that file, using:

sudo chmod 755 /etc/init.d/powersaveoff

Then I made powersaveoff run at boottime using:

sudo update-rc.d /etc/init.d/powersaveoff defaults

Then a simple reboot and you should be good to go (I think). This should disable powersaving automatically every time you log in... Please let me know if this helps anybody else...

---

### Post by malkdude on 2010-06-11
nope, the last thing I tried didn't really work, because when I removed the plug, and closed the lid, the system went to sleep again... I will now simply try to edit the gui for power management, rather than try to do things in a terminal... I got it from the KDE menu, by searching for power. It's called power management. It has some useful options. I tried playing around with those... Regarding the nomodeset boot option, it has some drawbacks with my ATI xpress 200m, because when I tried it, the ubuntu picture at the beginning when you log in doesn't have the right resolution... sighs... sometimes it's frustrating dealing with all the bugs, especially when you have an old ATI card... That being said, I still love ubuntu :p.

---

### Post by malkdude on 2010-06-14
As an update, after I went to the Kmenu (KDE menu) in Kubuntu, and searched for power management, opened it, and played with the options, I was able to set things up, so that the laptop doesn't go to sleep. It works. I left it on all night long for a download, and it didn't go to sleep (it was plugged in of course). Even when it's unplugged, I also set it up so that it never goes to sleep. That's my temporary fix for it for now.

One last remark though, in power management, make sure to check all tabs and options and set them to your liking.:guitar:

el_manaba, did this help you? Did you find another fix?

---

### Post by efflandt on 2010-06-14
I have a Compaq Presario V2000 with ATI Express 200M, and I could never get it to wake from suspend in 9.10.  I got hibernate to work once, and only once, while using an external keyboard/mousepad (diNovo Edge).  After that once, when it appeared to wake from hibernate, but would end up in the same black screen with no backlight.  Since nothing about those failures was in pm-suspend.log or any other logs, I did not know where to start looking.

So it was a surprise that suspend and hibernate work fine in 10.04 (fresh install, not upgrade).  Not sure if it is necessary, but I use **nomodeset** kernel boot parameter because I had trouble with suspend/hibernate and general video sluggishness with the new kernel mode setting with other older ATI video.

---

### Post by malkdude on 2010-06-15
I did some more testing... Here are the last few lines of dmesg right after a failed suspend/resume:

[  206.080497] PM: resume of drv:sd dev:0:0:0:0 complete after 1219.466 msecs
[  206.080895] PM: resume of devices complete after 2570.201 msecs
[  206.081025] PM: resume devices took 2.570 seconds
[  206.081067] PM: Finishing wakeup.
[  206.081070] Restarting tasks ... done.
[  206.400484] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[00e0b80300037229]
[  207.579899] sky2 eth0: enabling interface
[  207.581931] ADDRCONF(NETDEV_UP): eth0: link is not ready
[  207.830292] b43-phy0: Loading firmware version 351.126 (2006-07-29 05:54:02)
[  207.830303] b43-phy0 warning: You are using an old firmware image. Support for old firmware will be removed soon (official deadline was July 2008).
[  207.830309] b43-phy0 warning: You must go to [http://wireless.kernel.org/en/users/Drivers/b43#devicefirmware](http://wireless.kernel.org/en/users/Drivers/b43#devicefirmware) and download the correct firmware for this driver version. Please carefully read all instructions on this website.
[  207.893105] ADDRCONF(NETDEV_UP): wlan0: link is not ready

Could it be a Broadcom wireless thing? Note that PM said that the resume of devices is complete but seems to hang later, when not able to restart the wireless... :confused: hmm, I need to do some more testing...

---

### Post by malkdude on 2010-06-16
One last post on this, and after that I will move on. It seems that this is a common issue on many systems that were designed solely for windows, mainly because ACPI, which is responsible for power management, is often closed source. Please note that none other than Linus Torvalds worked on the issue and developed uswsusp package (and there are many variants for various distros). The webpage for this package is:

[http://suspend.sourceforge.net/](http://suspend.sourceforge.net/)

Check first in the repos! That being said, the package works for many machines out of the box, but unfortunately not for my laptop, which is a rather old Gateway machine. But there are various things one can try that are explained on that website. Good luck! Now if anyone with a Gateway MX6455 managed to get suspend working, then PLEASE post how! Otherwise, I'm happy with just disabling suspend using the Power Management GUI in Kubuntu for now... moving on...

---

### Post by el_manaba on 2010-07-07
No, disabling sleep mode doesn't resolve my concern.  I *want* the machine to sleep after a specified period of inactivity.  But I also want it to wake from sleep mode and return to full functionality.  As it is now, it wakes with a blank screen and doesn't respond to any input (except from the power button).

---

