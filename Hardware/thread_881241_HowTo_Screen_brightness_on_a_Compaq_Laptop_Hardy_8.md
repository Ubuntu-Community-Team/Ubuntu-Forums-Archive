---
title: "HowTo: Screen brightness on a Compaq Laptop Hardy 8.04"
date: 2008-08-05
forum: Hardware
---

### Post by countrylane on 2008-08-05
By the number of questions floating around these forums, laptop screen brightness issues seem to be a common problem. I tried several solutions addressed towards other makes/models of laptops. None worked.  I could not find any references to Compaq's either.

I was able, however, to modify 2 suggestions that I found and make them work with my laptop. I take no credit for the basic code. I found it in several locations.  All I did was modify a few things to make it work in my laptop. My how-to might get a bit long, but hopefully it makes sense once you read it through and helps some Compaq folks, or anybody else that has been frustrated by the inability to change screen brightness.

For reference my laptop is a new (August 2008) Compaq Presario A900 series (specifically A940AN). It came loaded with Win Vista. I repartitioned the HD and now dual-boot Ubuntu 8.04 and Vista. I also run WinXP inside Ubuntu using VirtualBox, primarily because I need to run MS Office Accounting 2008 that I purchased several months back. I bought the XP version and couldn't get it to load in Vista....so dual boot Ubuntu/Vista + VirtualBox = Works great.

Anyway...screen brightness. I found this suggestion in another thread:
--------
sudo -s
echo -n 50 > /proc/acpi/video/VGA/LCD/brightness
exit
--------
 (50 is 50% screen brightness...100 would be 100% screen brightness).

It didn't work because my directory structure is different. My Compaq has the following structure (not sure why its different):

/proc/acpi/video/OVGA/DD0X/brightness

so the command needs to look like this:
sudo -s
echo -n 50 > /proc/acpi/video/OVGA/DD0X/brightness
exit

Note that O in OVGA is like the capital letter O in the alphabet and 0 in DD0X is zero. Also X in DD0X is a number, since, on my PC I have several directories under the OVGA directory as follows: DD01, DD02, DD03, DD04, and DD05.

I first tried DD01, then DD02 in the command line
"echo -n 50 > /proc/acpi/video/OVGA/DD0X/brightness"
Neither worked. When I used DD03 as in echo -n 50 > /proc/acpi/video/OVGA/DD03/brightness, I immediately noticed a bump down in the brightness. You may need to try DD04 and DD05 if DD03 doesn't work. I then tried:
echo -n 100 > /proc/acpi/video/OVGA/DD03/brightness
and my screen immediately jumped to full-bright.

NOTE. In the help/how-to that I found this command in, the writer used the following values for percentages:
12 25 37 50 62 75 87 100
Except for 50 and 100, these DID NOT work on my Compaq. I had to use:
30 40 50 60 70 80 90 100.
Again, why the difference? I don't know, but mine is in multiples of 10 and works for me.

OK....so now I can change my brightness and is a decent solution, but it doesn't get your Fn (function) key + F7 and fn + F8 key combos to change the brightness.  Here is how to make them work. (Again, I found this code in several help forums and modified it to make it work for my Compaq). Make a backup of these files (video_brightnessup.sh and video_brightness_down.sh) so you can put things back the way they were if necessary.
------------THIS WORKED FOR ME---------------
sudo gedit /etc/acpi/video_brightnessup.sh
Replace everything in this file with:

#!/bin/bash

CURRENT=$(grep "current:" /proc/acpi/video/OVGA/DD03/brightness |awk '{print $2}')


case "$CURRENT" in

100)
echo -n 100 > /proc/acpi/video/OVGA/DD03/brightness;
;;
90)
echo -n 100 > /proc/acpi/video/OVGA/DD03/brightness;
;;
80)
echo -n 90 > /proc/acpi/video/OVGA/DD03/brightness;
;;
70)
echo -n 80 > /proc/acpi/video/OVGA/DD03/brightness;
;;
60)
echo -n 70 > /proc/acpi/video/OVGA/DD03/brightness;
;;
50)
echo -n 60 > /proc/acpi/video/OVGA/DD03/brightness;
;;
40)
echo -n 50 > /proc/acpi/video/OVGA/DD03/brightness;
;;
30)
echo -n 40 > /proc/acpi/video/OVGA/DD03/brightness;
;;
*)
echo -n 100 > /proc/acpi/video/OVGA/DD03/brightness ;
;;
esac

--------------END of VIDEO-BRIGHTNESS_UP---------

Now do the brightness_down file:

--------------BEGIN BRIGHTNESS_DOWN------------
sudo gedit /etc/acpi/video_brightnessdown.sh
Replace everything in this file with:

#!/bin/bash

CURRENT=$(grep "current:" /proc/acpi/video/OVGA/DD03/brightness |awk '{print $2}')


case "$CURRENT" in

30)
echo -n 30 > /proc/acpi/video/OVGA/DD03/brightness;
;;
40)
echo -n 30 > /proc/acpi/video/OVGA/DD03/brightness;
;;
50)
echo -n 40 > /proc/acpi/video/OVGA/DD03/brightness;
;;
60)
echo -n 50 > /proc/acpi/video/OVGA/DD03/brightness;
;;
70)
echo -n 60 > /proc/acpi/video/OVGA/DD03/brightness;
;;
80)
echo -n 70 > /proc/acpi/video/OVGA/DD03/brightness;
;;
90)
echo -n 80 > /proc/acpi/video/OVGA/DD03/brightness;
;;
100)
echo -n 90 > /proc/acpi/video/OVGA/DD03/brightness;
;;
*)
echo -n 60 > /proc/acpi/video/OVGA/DD03/brightness ;
;;
esac

----------END VIDEO=BRIGHTNESS_DOWN------------
Save both files.
Your FN +F7 for screen brightness down and Fn + F for screen brightness up should now work. (No reboot required).
Hope this helps somebody.

---

### Post by mattn on 2008-08-06
Thank you so much!  This worked to fix the brightness controls on my Compaq C751NR laptop, running Ubuntu 8.04

Many, many thanks!

Matt

---

### Post by ChrisMP1 on 2008-08-06
Many thanks! Didn't realize it.

Of cource, you can replace those long files with:

```

#!/bin/bash
## video_brightnessup.sh

CURRENT=`grep "current:" /proc/acpi/video/OVGA/DD03/brightness \
    | awk '{print $2}'`

if [[ "$CURRENT" -ge 100 ]]; then
    echo -n 100 > /proc/acpi/video/OVGA/DD03/brightness
else
    echo -n `expr $CURRENT + 10` > /proc/acpi/video/OVGA/DD03/brightness
fi

```

and

```

#!/bin/bash
## video_brightnessdown.sh

CURRENT=`grep "current:" /proc/acpi/video/OVGA/DD03/brightness \
    | awk '{print $2}'`

if [[ "$CURRENT" -le 30 ]]; then
    echo -n 30 > /proc/acpi/video/OVGA/DD03/brightness
else
    echo -n `expr $CURRENT - 10` > /proc/acpi/video/OVGA/DD03/brightness
fi

```

---

### Post by david819 on 2008-08-07
Not related:  Almost identical setup.  Dual booting Vista/Ubuntu 8.04 running XP in VB.  
Related:  Initially I was frustrated with brightness as well, and recently while altering my menu bar I found a solution.  When you right click on your menu bar, and go to "Add to Panel..."  you will find an applet called "Brightness Applet".  Not sure if this is related to what you guys are talking about.

---

### Post by countrylane on 2008-08-07
re david819 and the applet, I tried the applet and it didn't work for me.  I just tried the applet again after doing the suggestions in my original howto post and it still doesnt work, so whatever makes it work, must be pulling information from other/different config files.

---

### Post by Dalox on 2008-08-09
Thank you so much! This worked to fix the brightness controls on my Compaq Presario C700 laptop Ubuntu Hardy 8.04  :)

---

### Post by kspncr on 2008-08-12
Awesome dude! Works perfectly!

---

### Post by trevypoos on 2008-08-15
Thank you! I have just come back to Ubuntu with my new laptop, as my old one got stolen.

So far today I have cracked wireless and now this. Going well.

Thanks again.

---

### Post by Mikhaily on 2008-08-15
Thank you country lane and chrismp1! I've spend days searching forums and messing about with various codes. Huge thumbs up!

Thanks

---

### Post by skybro on 2008-08-26
This is exactly what I needed for my new Compaq Presario A940NR.  i bit the bullet and went full ubuntu 8.04 install, as I am unable to fathom the idea of Vista entering my house.  Lovin the full system now !!!!

Thanks SOOO much!

---

### Post by rafaelj on 2008-09-04
Yeah! Worked fine for my Compaq Presario C700.
Thank you a lot!

---

### Post by rafaelj on 2008-09-10
By the way guys, 

Since it seems that you all have Presario c700, do you have problem with suspension?

In may laptop it only works on the first time. See, I've even created a post in this forum. Take a look, if you will. 

[http://ubuntuforums.org/showthread.php?p=5765977](http://ubuntuforums.org/showthread.php?p=5765977)

We are trying to investigate this.

Best regards.

---

### Post by viduliya on 2008-09-14
Thank you very much for this tip.  I works very well on my Compaq Presario C776CA.  Now I only have one more porlbem to get fixed on this machine.  I cant seem to switch to a projector plugged in to the VGA port of the machine using Fn+F4.  Anyone found a solution for this yet?

---

### Post by fubar_too on 2008-09-17
Hi guys,

I've got a Compaq Presario v30xx (3020 i think) and I guess i'm kinda noob.  You're instructions point to /proc/acpi/video etc but I've got a problem.  I don't have a video directory within /proc/acpi.

Still trying to find screen brightness problem...

Thanks,
Sam

---

### Post by javafiend on 2008-09-17
I'm having some problems with this.  After I hit enter on the echo line, I get an "invalid argument" error.  And this is really difficult because the brightness is so low (or the backlight needs replaced).

This is exactly what I am typing in in Terminal:
```
echo -n 100 > brightness
```

I have already navigated to the correct path.

---

### Post by cjtech on 2008-10-14
I am also getting Invalid argument :-(

---

### Post by Megakazbek on 2008-10-15
I have problems with setting brightness on my HP Compaq 6530b laptop. Brightness control in Power Management doesn't work, as well as brightness applet. Brightness hotkeys (Fn+F9 and Fn+F10) don't work either. In my /proc/acpi/video directory I have a directory called GFX0 in which there are directories called DD01, DD02, DD03, DD04 and DD05, each of which contains a "brightness" file (as well as a couple of others). When I display contents of these files using the cat command, I get <not supported> from all files except the one in DD04 directory. The one that's in DD04 displays the following:
```
levels:  100 51 30 37 44 51 58 65 72 79 86 93 100
current: 100
```
I tried echoing some numbers (some of those that are listed after "levels: " as well as some arbitrary ones) into that file as described here, and while it changed the number displayed after "current: ", the actual display brightness did not change. Echoing a number into any other brightness files results in an "Invalid argument" error.
Any suggestions?
BTW, the situation is the same both in 8.04 and in 8.10 beta with latest updates.

---

### Post by jback2 on 2008-10-23
I use Intrepid Ibex because of the wlan card. But I have the same problem with my HP 6530b... While booting changing brightness works fine, afterwards not.

Has anyone an idea? Or Megakazbek, have you managed something?

---

### Post by Megakazbek on 2008-10-23
Nope, I haven't managed anything.
All solutions I've found on the Internet didn't go beyond writing numbers into the "brightness" file, and obviusly in our case it doesn't work. Unfortunately, I couldn't find even tiniest clues where to look further.
I would greatly appreciate ANY suggestions, even really technical ones. Any Linux gurus here who can point in the right direction?

---

### Post by flabdablet on 2008-10-25
I've been playing with this a bit on a new Compaq Presario C762VU (Presario C700 series) that I'm setting up for a friend.  Here's the brightness-setting script I'm currently testing:
```

#!/bin/sh
# Brightness control for Compaq laptops
# Invoke via video_brightnessup.sh or video_brightnessdown.sh symlinks in /etc/acpi

op=gt; test "${0##*/}" = video_brightnessdown.sh && op=lt
conf=/proc/acpi/video/OVGA/DD03/brightness
{
	read levels_line
	read current_line
} <$conf
set -- $current_line
if [ "$1" = current: ]
then
	current=$2
	new=
	set -- $levels_line
	if [ "$1" = levels: ]
	then
		while
			shift
			test $# -gt 0
		do
			if [ "$1" -$op "$current" ]
			then
				test ! "$new" -$op "$1" 2>/dev/null || new=$1
			fi
		done
	fi
	echo ${new:-$current} >$conf
fi

```
After saving this as /tmp/compaq-brightness.sh, I've done
```

sudo su -
cd /etc/acpi
cp /tmp/compaq-brightness.sh .
chmod +x compaq-brightness.sh
mv video_brightnessup.sh video_brightnessup.sh.original
mv video_brightnessdown.sh video_brightnessdown.sh.original
ln -s compaq-brightness.sh video_brightnessup.sh
ln -s compaq-brightness.sh video_brightnessdown.sh
exit

```
Advantages over what's been presented so far:
[list]
[*] Only one line needs changing to set which brightness file is read and written under /proc/acpi/video
[*] Writes only brightness values listed in the "levels:" line read from the brightness file, rather than assuming certain values will be valid
[*] Uses only sh and no subprocesses - small and quick
[/list]
Brightness control still isn't perfect - the Brightness Applet still doesn't work ("Cannot get laptop panel brightness") and sometimes the function keys do nothing (this may or may not have something to do with coming out of suspend; still collecting evidence there) until after video_brightness{up,down}.sh has been invoked once by hand.  But it's better than nothing.

The only way I can reproduce the "Invalid argument" error that some other people have seen is by attempting to write to a brightness file that reads "<not supported>" when read.  If you're going to try this on your laptop, make sure reading the brightness file you identify with conf= shows you something like
```

levels: 100 50 0 10 20 30 40 50 60 70 80 90 100
current: 50

```
I'd be interested to hear from people who try this on Compaq laptops that keep their brightness control file somewhere other than /proc/acpi/video/OVGA/DD03/brightness or have different levels: values.

Next job: getting Suspend to happen when the lid is closed, and Hibernate to do something different from Shut Down...

---

### Post by carleeldean on 2008-10-27
Thankyou very much .. woked for me

---

### Post by WaterDemon on 2008-10-27
I have also HP 6530b laptop and screen brightness do not work for me!
I have file /proc/acpi/video/GFX0/DD04/brightness, but echoing a number to it does not work!!!
Please help anyone! I don't know what to do!

---

### Post by flabdablet on 2008-10-27
WaterDemon, could you list the existing contents of your brightness file and the commands you've used to write a new number into the file, and could you also expand a little on what "doesn't work" means?  Are you seeing the same behavior as Megakazbek, where your write **does** change the number reported as "Current:" but **does not** change the actual backlight brightness?

---

### Post by WaterDemon on 2008-10-28
flabdablet, I have everything exactly as described in post of Megakazbek. Contents of brightness file is the same, I wirte number to it with "echo -n xx > brightness" command, Current number changes but brightness stays the same!

---

### Post by s3kt0r on 2008-11-02
ChrisMP1, tried your way, my brightness adjusting keys are now working perfectly, running 8.04 in a HP G7000 (low budget series). 

Thanks 4 sharing knowledge.

---

### Post by Megakazbek on 2008-11-03
Meanwhile, Ubuntu 8.10 is finally released, but the brightness issue still remains. I've been told that Ubuntu community is really helpful, so a whopping total of ZERO replies that I've received with my problem here over 2 weeks is really not at all what I expected. 
What's the problem, guys? Is there some additional information required to look into the issue? I'll be glad to provide it, just say what exactly is needed. Maybe I posted my problem in a wrong place? I'm not even looking for a super-detailed step-by-step resolution guide, I will gladly accept even the slightest hints, suggestions or ideas. I'm just really new to Linux, so I can't manually resolve such issues and don't understand some things. For example, how does 'brightness' file appear under /proc filesystem? Why it appears in different places on different machines? What exactly happens internally when I write a number to the brightness file, i.e. how this file communicates with the physical LCD display?
Is there some place where I could read about such things?

---

### Post by flabdablet on 2008-11-04
I think the problem is that this is a community forum, frequented by ordinary Ubuntu users just like you and me, and nobody who has the same model of laptop as you has yet figured out how to make it go.  The forums are really good for exchanging workarounds, but they're not so good at getting actual bugs fixed.

It looks like there are several current [color="Blue"]_[brightness-related kernel bugs](http://bugzilla.kernel.org/buglist.cgi?query_format=specific&order=relevance+desc&bug_status=__open__&product=&content=brightness)_[/color].  If I were you, I'd look through those for behaviour that matched what I was seeing, and track the appropriate bug; if nothing matches, report a new kernel bug.

---

### Post by super764 on 2008-11-25
Hi guys, got the HP 6530b like Megakazbek, WaterDemon.

I'm cracking my head on this hotkeys issue. 
But unfortunately I have only few time to dedicate to it. 

Any news?

---

### Post by super764 on 2008-11-25
Got something based on this bug: 

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/284319](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/284319)

Under my hp6530b I created this file ```
/usr/share/hal/fdi/information/20thirdparty/30-keymap-private.fdi
```

its content is:

```
<?xml version="1.0" encoding="ISO-8859-1"?> <!-- -*- SGML -*- -->

<deviceinfo version="0.2">
  <device>

    <match key="@input.originating_device:info.linux.driver" string="atkbd">
      <match key="/org/freedesktop/Hal/devices/computer:system.hardware.vendor" prefix="Hewlett-Packard">
        <match key="/org/freedesktop/Hal/devices/computer:system.hardware.product" contains="6530b">
          <!-- HP Compaq 6530b -->
          <append key="input.keymap.data" type="strlist">e012:brightnessdown</append> <!-- FnF9 (brightness down) -->
          <append key="input.keymap.data" type="strlist">e017:brightnessup</append> <!-- FnF10 (brightness up) -->
        </match>
      </match>
    </match>
  </device>
</deviceinfo>
```

Restarted and now I have the icon working when pressing brightness hotkeys, **but brightness still not works.**

Then in a shell tried to: 
```
xrandr --output LVDS --set BACKLIGHT_CONTROL native
```

And brightness with hotkeys is working.

The only problem now is that **[COLOR="Blue"]decreasing brightness to zero, breaks something and you can't raise brightness anymore[/COLOR]** on the laptop screen.

I was lucky that I had a 2nd monitor attached and **i could revert the problem** setting the control back to the kernel with this command:

```
xrandr --output LVDS --set BACKLIGHT_CONTROL kernel
```

Hope this helped a litte... still waiting for a final solution.

---

### Post by crimson on 2008-12-05
Thanks, super764! I've got an HP 2230s and that got the backlight controls working. But how do I make the xrandr setting permanent? The BACKLIGHT_CONTROL setting resets to kernel on restart.

However, I'm also seeing the spontaneous screen dimming problem mentioned in this thread: [http://ubuntuforums.org/showthread.php?t=972323]("http://ubuntuforums.org/showthread.php?t=972323") Kind of makes it unusable.

---

### Post by super764 on 2008-12-09
You're welcome... (please press use the thank button-- :D)..

Anyways:
You could ways put that command in your ~/.xprofile (like I did), but this doesn't resume the last brightness... 

I have no clue on how to do that, maybe some investigation.. :)

---

### Post by instantkarma on 2008-12-16
On my compaq it's 'fn' + 'f7' for less bright and 'fn' + 'f8' for brighter.

---

