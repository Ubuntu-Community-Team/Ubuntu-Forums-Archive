---
title: "HOWTO: Make brightness control Fn keys work correctly on HP DV2000 with Ubuntu Feisty"
date: 2007-07-14
forum: Hardware &amp; Laptops
---

### Post by jiasheng on 2007-07-14
Problem:
I've a hp dv2210us (one of the dv2000z series) laptop with feisty installed. Almost everything works fine, except that it is not easy to adjust the brightness easily. Fn keys don't work, no slider in Gnome Power Manager. The only way to adjust the brightness is "sudo echo" a correct value to /proc/acpi/video/VGA/LCD/brightness, which is quite inconvenient. More precisely, the Fn keys may sometimes turn the screen to either brightest or dimmest. A careful study shows that the problem resides in the kernel module "video". Whenever the keys are pressed, the module will try to adjust the brightness as well as trigger a signal might be caught by acpi daemon. However, for some reason that I don't know, the module cannot adjust the brightness correctly on my laptop.

Solution:
The idea is to adjust the brightness through acpi daemon rather than the kernel module. So what we are going to do is to modify the kernel module a bit and add some small scripts to the acpi daemon. Here we go. I hope this howto may help those who have the similar problems.

************Please remember to do the backup before any modification and file replacements.********

**1. Install the source package**
sudo apt-get install linux-source-2.6.20
cd /usr/src
sudo tar xvjf linux-source-2.6.20.tar.bz2

**2. Modify the kernel module.**
cd /usr/src/linux-source-2.6.20/drivers/acpi
sudo gedit video.c
**find the code block below:
[I]...
case ACPI_VIDEO_NOTIFY_INC_BRIGHTNESS: /* Increase brightness */
case ACPI_VIDEO_NOTIFY_DEC_BRIGHTNESS: /* Decrease brightness */
case ACPI_VIDEO_NOTIFY_ZERO_BRIGHTNESS: /* zero brightnesss */
case ACPI_VIDEO_NOTIFY_DISPLAY_OFF: /* display device off */
acpi_video_switch_brightness(video_device, event);
acpi_bus_generate_event(device, event, 0);
break;
default:
...[/I]
**edit this part according to below:
[I]...
case ACPI_VIDEO_NOTIFY_ZERO_BRIGHTNESS: /* zero brightnesss */
case ACPI_VIDEO_NOTIFY_DISPLAY_OFF: /* display device off */
acpi_video_switch_brightness(video_device, event);
acpi_bus_generate_event(device, event, 0);
break;
case ACPI_VIDEO_NOTIFY_INC_BRIGHTNESS: /* Increase brightness */
case ACPI_VIDEO_NOTIFY_DEC_BRIGHTNESS: /* Decrease brightness */
acpi_bus_generate_event(device, event, 0);
break;
default:
...[/I]
Save and quit.

**3. Recompile and replace the kernel module**
cd /usr/src/linux-source-2.6.20/drivers/acpi
sudo gedit makevideo
write the following code into the newly created file.

[I]KDIR := /lib/modules/$(shell uname -r)/build
PWD := $(shell pwd)

default:
$(MAKE) -C $(KDIR) SUBDIRS=$(PWD) modules[/I]

Save and quit.
sudo make -f makevideo
sudo cp video.ko /lib/modules/`uname -r`/kernel/drivers/acpi/

**4. Add acpi events**
cd /etc/acpi/events
sudo gedit hp-brightness-up
write the following contents into the newly created file:
[I]
event=video LCD 00000086 00000000
action=/etc/acpi/hpbrightnessup.sh[/I]

Save and quit.
sudo gedit hp-brightness-down (same as before)

[I]event=video LCD 00000087 00000000
action=/etc/acpi/hpbrightnessdown.sh[/I]

Save and quit.

**5. Add new acpi scripts to adjust the brightness**
cd /etc/acpi
cat /proc/acpi/video/VGA/LCD/brightness
please pay attention to the output of levels.
mine is : "levels: 100 60 20 28 36 44 52 60 68 76 84 92 100"
if yours is different you may have to change the numbers in the following scripts.
sudo gedit hpbrightnessup.sh

[I]#!/bin/sh
value="`cat /proc/acpi/video/VGA/LCD/brightness | grep current: | awk '{print $2;}'`"
if [ $value -eq 0 ]
then
value=92
fi
if [ $value -ge 92 ]
then
value=92
else
value=`expr $value + 8`
fi
echo $value > /proc/acpi/video/VGA/LCD/brightness[/I]

Save and quit.
sudo gedit hpbrightnessdown.sh
[I]
#!/bin/sh
value="`cat /proc/acpi/video/VGA/LCD/brightness | grep current: | awk '{print $2;}'`"
echo $value
if [ $value -eq 0 ]
then
value=92
fi
if [ $value -le 20 ]
then
value=20
else
value=`expr $value - 8`
fi
echo $value > /proc/acpi/video/VGA/LCD/brightness[/I]

Save and quit.
sudo chmod +x hpbrightness*.sh

**6. Done**
You may find the Fn keys work correctly after rebooting the computer.
I wish I made everything clear here, however, if any questions, plz let me know.

---

### Post by doutdes on 2007-07-30
sudo make -f makevideo
make: Nothing to be done for `default'.

so I cannot continue after that

---

### Post by jiasheng on 2007-08-04
1.  Make sure you have dir linux-headers-2.6.20-16-generic ( or sth. similar ) in /usr/src

2.  Confirm that you have already edited the video.c file and saved it successfully.

3.  The makevideo file should be in /usr/src/linux-source-2.6.20/drivers/acpi, and you should do the make step right in that dir.

4.  Maybe you can try sudo rm video.ko if there is already a video.ko under 
/usr/src/linux-source-2.6.20/drivers/acpi

Good luck.

---

### Post by jiasheng on 2007-08-04
BTW, makefile is tab sensitive.  So perhaps you can not simply copy and paste the contents in the post.  There should be a "tab" in front of the $(MAKE).  I think this may solve your problem coz I can repeat the error you met with an incorrectly formated makefile.  I am glad to send you the file if you really need it.

---

### Post by ggellner on 2007-09-01
Have you thought about trying to get this into the distribution? This was very helpful to me, though it is a major undertaking (in comparison to most ubuntu fixes . . .). A quick look through the forums shows that MANY other people with HP laptops are having this problem.

Anyway, great work . . . it was a very nice fix!

Gabriel

---

### Post by jiasheng on 2007-09-05
> **ggellner said:**
> Have you thought about trying to get this into the distribution? This was very helpful to me, though it is a major undertaking (in comparison to most ubuntu fixes . . .). A quick look through the forums shows that MANY other people with HP laptops are having this problem.

Anyway, great work . . . it was a very nice fix!

Gabriel

I'm very glad this works for you.  Ubuntu is really a great distro and I am willing to make any contribution that I can.  However, I am not clear about the steps for getting patches into distribution.  Moreover, I am not sure if this workaround is a general-purposed one for all the hp laptops or at least the dv series since there are no many replies here.  The problem is the numbers in the brightness file may vary among different laptops as I mentioned in the post.  Another problem is this method may lose some levels for adjusting the brightness since the screen in Windows Vista could be one level brighter than in Ubuntu apparently.  So I am also hoping for this problem can be solved on the kernel level, which should be a far better solution.

---

### Post by Prometheum on 2007-09-09
Thanks for this; I got my dv2000 about a year ago and when I did, these fn keys, the quickplay buttons, everything worked fine. I think HP updated the BIOS to screw with us, because when my mobo died and they replaced it, I couldn't bind the quickplay buttons anymore, the fn brightness didn't work and for some reason my CD tray keeps spitting out. Thanks for giving a fix for this.

---

### Post by jiasheng on 2007-09-12
For the quickplay keys, you can use keytouch and keytouch-editor to make it work perfectly.

---

### Post by Vajrapaat on 2007-10-06
Hi,
   
   I am getting the same message when i try to make video.c

sudo make -f makevideo
make: Nothing to be done for `default'.

  I  have already tried out the fixes posted above. Can you advise me on this? Thanks

---

### Post by jiasheng on 2007-10-06
I believe it's still the format issues with the makevideo.  I am more than happy to send you the correct file if you need, however, my laptop has some problems recently.  I am afraid that you have to figure it out yourself because it takes more than a week for my laptop getting repaired :(  I'll help you as soon as I get my laptop back if you still have problems at that time.  Besides, I have tried Gutsy live cd and it is now having the Fn keys work correctly, so perhaps we do not need this patch any more.

---

### Post by GavinZac on 2007-10-06
Wow, I have the same laptop, and honestly, had no idea i had those buttons until you pointed them out.

Anyway, they work perfectly **without** any modifications, with Ubuntu Gutsy :D

*goes off to test the other Fn buttons*

---

### Post by trannypunk on 2008-03-24
Hey there!

I had this same issue. Go into the makevideo file that you have just created. Should be 
cd /usr/src/linux-source-2.6.20/drivers/acpi
sudo gedit makevideo

A few lines down, you will find 
$(MAKE) -C $(KDIR) SUBDIRS=$(PWD) modules
Put your curson in front of that line, and hit the TAB key. Save and close.
 : : :
In other news; I have run through this whole tutorial, and the brightness keys are still not working. They tried to, but then failed. Thanks for the tutorial though!!!

---

### Post by []Milo on 2008-05-24
a wealth of stuf on HP pavillion laptops is available here

[http://aldeby.org/blog/index.php/howto-ubuntu-linux-on-hp-pavilion-dv2000-dv6000-dv9000-series-laptops]("http://aldeby.org/blog/index.php/howto-ubuntu-linux-on-hp-pavilion-dv2000-dv6000-dv9000-series-laptops")

.. which includes a link to this:
[http://ubuntuforums.org/showthread.php?t=673946]("http://ubuntuforums.org/showthread.php?t=673946")

---

