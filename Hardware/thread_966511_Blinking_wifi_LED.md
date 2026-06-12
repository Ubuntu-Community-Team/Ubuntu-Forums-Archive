---
title: "Blinking wifi LED"
date: 2008-11-01
forum: Hardware
---

### Post by Sir Galahad on 2008-11-01
Hi,

I know there have been several threads about the issue that I will be talking about, but studying any of these hasn't lead to a working solution for me.
I recently purchased a Dell Latitude E6400 and installed Intrepid on it today. Everything is working just fine, but unfortunately the wifi LED is constantly blinking to indicate network traffic rendering my laptop almost inoperable because it is so distracting.
As has been suggested in another thread I put the following script in /etc/network/if-up.d/ and made it executable. 

```

#!/bin/sh

if [ "$IFACE" = "wlan0" ]; then
	for dir in /sys/class/leds/iwl-phy*X; do
		echo none > $dir/trigger
	done
fi

```

This is what /sys/class/leds/iwl-phy0\:RX/trigger and /sys/class/leds/iwl-phy0\:TX/trigger look like after disabling and enabling networking:

```

xian@lothlorien:~$ cat /sys/class/leds/iwl-phy0\:TX/trigger 
[none] AC-online BAT0-charging-or-full BAT0-charging BAT0-full mmc0 phy0rx phy0tx phy0assoc phy0radio rfkill0 
xian@lothlorien:~$ cat /sys/class/leds/iwl-phy0\:RX/trigger 
[none] AC-online BAT0-charging-or-full BAT0-charging BAT0-full mmc0 phy0rx phy0tx phy0assoc phy0radio rfkill0

```

Before setting up the above script, "none" wasn't in square brackets, though I have no idea as to what that means.
However, the wifi LED is still blinking annoyingly.

Any suggestions will be greatly appreciated.

Regards,
Sir Galahad

---

### Post by Sir Galahad on 2008-11-01
For some obscure reason, after restarting X for the umpteenth time it seems to be working now.

---

### Post by Sir Galahad on 2008-11-01
I just realized that it blinks again after a reboot. It only stops to blink when I log out of Gnome and log in again.

Any ideas on this?

---

### Post by Baloo Bear on 2008-11-01
Hi 

I had a similar problem on a Dell Inspiron 1525.

I installed and ran the application luvcview. Once this had been executed, the problem was solved, apparently permanently.

Baloo

---

### Post by 4Play on 2008-11-03
I have the same problem, have tried using the trigger = none script, setting the brightness to zero manually...nothing worked.

I also installing luvcview (thought it was strange, since this is a webcam viewing application) and as expected, it didnt work for me...

I am *almost* going back to 8.04...this blinking led thing is one of the many problems I am having with intrepid :(

---

### Post by jpg_ny on 2008-11-08
I'm facing the same problem
The wifi led is blinking and on a laptop this is not very useful.
I tried a lot "tips" proposed so far I'm out of luck.

My wifi card is a Intel 3945ABG on a dell laptop D620.

---

### Post by lariosa42 on 2008-11-09
Same here with a Intel Corporation PRO/Wireless 3945ABG wireless card on a Dell Inspiron E1405 running Intrepid.  It is destroying my sanity.

Old school solution: Get some electrical tape and scissors, cut the tape the size of the flashing light.  Apply the tape to the flashing light and viola!  (This solution brought to you by the blinking 12:00 on VCRs in the 80's.)  A higher-tech solution would of course be appreciated.

---

### Post by caraboy on 2008-11-09
Just installed Intrepid on my HP530. I have the same problem with 3945ABG. And at this laptop the wifi led is blue and in front of the screen. :-P You can just imagine how annoying it is. :D

---

### Post by hchizkool on 2008-11-10
hi i can make the file on my desktop but not in etc/network/if-up.d because it says "you are not an owner, so you cannot change these permissions" anyone able to help?

---

### Post by hchizkool on 2008-11-11
hi i can make the file on my desktop but not in etc/network/if-up.d because it says "you are not an owner, so you cannot change these permissions" anyone able to help?

---

### Post by lariosa42 on 2008-11-11
It sounds like you just need the proper permissions.  Just open a terminal window and type 
```
gksudo nautilus
```
then enter your password.  This opens a window which has the proper permissions.  You should be about to browse from this window to the directory (folder) you want and simply drap and drop the file into it.

---

### Post by laptoplinux on 2008-11-11
Anyone know if this situation will be fixed eventually?  If not, please post if you find out anything.

I know blinking on activity is supposedly how the new driver was designed to work, but it would be great if there was an option to change the behavior to something more sane... 

maybe like this:  

off = wifi not working/ not on
blinking = only when making a connection
on solid = connected

The constant blinking is very distracting on my laptop.  That was one of the things that drove me back to Hardy for now, and I don't think I can run any linux distro that operates that way without a guaranteed way to change it.

---

### Post by lariosa42 on 2008-11-12
I'm surprised that more people are not totally irritated by this.  That blinking light is going to drive someone to murder.  My electrical tape trick (see above) is preserving my sanity for now, but it sure makes my laptop look tacky.

---

### Post by davidY on 2008-11-12
This is a very horrible feature, and I either stop using ubuntu after half an hour and switch to windows (dual boot yay) or I turn the computer off.

---

### Post by laptoplinux on 2008-11-12
I know this may sound a bit childish, but if that blinking wifi light remains a part of the kernels from now on, I will probably abandon Linux entirely for OSX.  That may sound a bit extreme, and I'm sure the light doesn't annoy some people as much as it does others (depending on hardware design and an individual's ability to tune it out), but I really can't stand it, and my abandonment would be for practical reasons more than anything else.  I just hope someone eventually corrects this in a future kernel.

Of course, there is yet hope.  If this gets fixed in Jackalope or a future Ibex update, or even in another Linux distro that proves suitable, all is forgiven.

---

### Post by iponeverything on 2008-11-12
> **laptoplinux said:**
> I know this may sound a bit childish, but if that blinking wifi light remains a part of the kernels from now on, I will probably abandon Linux entirely for OSX.  That may sound a bit extreme, and I'm sure the light doesn't annoy some people as much as it does others (depending on hardware design and an individual's ability to tune it out), but I really can't stand it, and my abandonment would be for practical reasons more than anything else.  I just hope someone eventually corrects this in a future kernel.

Of course, there is yet hope.  If this gets fixed in Jackalope or a future Ibex update, or even in another Linux distro that proves suitable, all is forgiven.

sound like a bug that intel driver and not a feature.  Why don't open a ticket on launchpad if you would like it fixed.

Just found this:
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/157418](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/157418)

You should post a followup to launchpad to say you can also confirm the bug.

---

### Post by davidY on 2008-11-12
It seems there is a bug filed for it
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/250211](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/250211) (this one is the main bug the above one is the duplicate)

My fix is to have a file in /etc/network/if-up.d/ with permission to execute as root (chmod +x as root) the file is as follows:

> david@user18:~$ cat /etc/network/if-up.d/stopblink 
#!/bin/sh
echo none > /sys/bus/pci/drivers/iwl3945/0000:0b:00.0/leds/iwl-phy0:assoc/trigger
echo none > /sys/bus/pci/drivers/iwl3945/0000:0b:00.0/leds/iwl-phy0:radio/trigger
echo none > /sys/bus/pci/drivers/iwl3945/0000:0b:00.0/leds/iwl-phy0:RX/trigger
echo none > /sys/bus/pci/drivers/iwl3945/0000:0b:00.0/leds/iwl-phy0:TX/trigger

echo none > /sys/class/leds/iwl-phy0:RX/trigger
echo none > /sys/class/leds/iwl-phy0:TX/trigger
echo none > /sys/class/leds/iwl-phy0:radio/trigger
echo none > /sys/class/leds/iwl-phy0:assoc/trigger

it is overkill, but i don't really care. It stops blinking

---

### Post by ant1060 on 2008-11-12
Overkill??? NEVER MIND!!!!! 
The light has finally stopped flashing and now I can start to enjoy Ubuntu again.
Thank you so much ... I was on the point of killing something myself!!!
:)

---

### Post by gjohn2 on 2008-11-12
thank you! i was getting ready to stab someone, because of this damn light.
the script works.

---

### Post by lariosa42 on 2008-11-12
laptoplinux - 

Seriously, using a little black tape is way less of a headache than going back to windows.  Time required to cut and apply tape: 30 seconds.  Time required to reinstall windows: way more than it's worth.  Plus you would be stuck with windows, which will make your computer far uglier than a little piece of black tape.

davidY - 

Thank you!  I want to try this, but first, how much overkill is this?  I admit I don't really understand what your script does (I tried), so I just want to know if I'm screwing something else up.

---

### Post by davidY on 2008-11-13
- lariosa42
Well the script was mashed from various sources which all looked similar to this. I think it tells the driver to blink on nothing - so it never blinks. Apparently there are many different things you can tell it to blink on.

You can make a file (eg stopblink) paste it in, go to commandline and "chmod +x stopblink", then do "sudo ./stopblink", and it will run the command once - put it into your /etc/network/if-up.d/ folder to make it run whenever the wifi connects up by "sudo mv stopblink /etc/network/if-up.d/."

---

### Post by iponeverything on 2008-11-13
> **lariosa42 said:**
> laptoplinux - 

Seriously, using a little black tape is way less of a headache than going back to windows.  Time required to cut and apply tape: 30 seconds.  Time required to reinstall windows: way more than it's worth.  Plus you would be stuck with windows, which will make your computer far uglier than a little piece of black tape.

davidY - 

Thank you!  I want to try this, but first, how much overkill is this?  I admit I don't really understand what your script does (I tried), so I just want to know if I'm screwing something else up.

Don't worry. It just a command line version of electrical tape.

To tell you the truth, I am big fan of the simple solution.

---

### Post by laptoplinux on 2008-11-14
Whoa, whoa, whoa.  Who said anything about going back to Windows?  I used to use Windows, like 3 years ago.  But besides being a primitive, clunky mess, Windows is entirely unsuited for the work that I currently do.

If anything, I'd go pickup a shiny new Macbook and carry on.  But until I am forced to move off of Hardy or replace my current computer, that's all moot.

(That script may work to fix the blinking.  If so, great.  But Ibex also had a bad habit of constantly dropping connections on me.)

We'll just see what happens.  Surely enough people will be annoyed by this that the devs will eventually correct it.... right?

---

### Post by oz-sco on 2008-11-15
Ok so i've created and run the script file

> #!/bin/sh
echo none > /sys/bus/pci/drivers/iwl3945/0000:0b:00.0/leds/iwl-phy0:assoc/trigger
echo none > /sys/bus/pci/drivers/iwl3945/0000:0b:00.0/leds/iwl-phy0:radio/trigger
echo none > /sys/bus/pci/drivers/iwl3945/0000:0b:00.0/leds/iwl-phy0:RX/trigger
echo none > /sys/bus/pci/drivers/iwl3945/0000:0b:00.0/leds/iwl-phy0:TX/trigger

echo none > /sys/class/leds/iwl-phy0:RX/trigger
echo none > /sys/class/leds/iwl-phy0:TX/trigger
echo none > /sys/class/leds/iwl-phy0:radio/trigger
echo none > /sys/class/leds/iwl-phy0:assoc/trigger 

and the wifi light is on, when nothing is happening, but when i say, load up a new web page it starts flashing again. I'd like it never to flash, have i done something wrong? or do i need another script?

cheers Oz

---

### Post by lariosa42 on 2008-11-17
I have the same results as oz-sco.  The light doesn't blink all the time anymore, but it still blinks often enough to be irratating.

(Note, to get the above script to work, I had to change all the "0000:0b:00.0" parts of the driver strings to "0000:0c:00.0".

---

### Post by corman on 2008-11-17
any possibility that this script could disable the light totally? I almost am ready to switch back to Hardy where the bug disabled it. I have a crazy bright blue light on the top of the lid and it drives me nuts. Thanks in advance for any help!

---

### Post by laptoplinux on 2008-11-23
oz-sco's script worked when I tested it on a live CD of Fedora 10, though I had to make one small change to this:

```
#!/bin/sh
echo none > /sys/bus/pci/drivers/iwl39450000:0c:00.0/leds/iwl-phy0:assoc/trigger
echo none > /sys/bus/pci/drivers/iwl39450000:0c:00.0/leds/iwl-phy0:radio/trigger
echo none > /sys/bus/pci/drivers/iwl39450000:0c:00.0/leds/iwl-phy0:RX/trigger
echo none > /sys/bus/pci/drivers/iwl39450000:0c:00.0/leds/iwl-phy0:TX/trigger

echo none > /sys/class/leds/iwl-phy0:RX/trigger
echo none > /sys/class/leds/iwl-phy0:TX/trigger
echo none > /sys/class/leds/iwl-phy0:radio/trigger
echo none > /sys/class/leds/iwl-phy0:assoc/trigger 
```

In other words, changing the "0b" to "0c" for each line of the first half.  I have no idea what the difference is.

After running this script, the light would be off when the wifi was off, blink for a couple of seconds when connecting, and stay solidly lit while connected.  (The way it should have been all along, in my opinion).

I guess to make it permanent I'd need to make this script automatically run at startup, or is that necessary?

---

### Post by sharon.gmc on 2008-11-23
I have the same problem with my Acer laptop

---

### Post by corman on 2008-11-24
Sweet, thanks alot laptoplinux, I changed the oc part to what it said on my machine, now no blinking. but i still dont know how to disable it totally.

---

### Post by jespdj on 2008-11-24
> **laptoplinux said:**
> I know this may sound a bit childish, but if that blinking wifi light remains a part of the kernels from now on, I will probably abandon Linux entirely for OSX.  That may sound a bit extreme, and I'm sure the light doesn't annoy some people as much as it does others (depending on hardware design and an individual's ability to tune it out), but I really can't stand it, and my abandonment would be for practical reasons more than anything else.  I just hope someone eventually corrects this in a future kernel.

Funny... I remember that with 8.04 people were complaining that the Wifi LED doesn't work (see for example bugs [176090](https://bugs.launchpad.net/linux/+bug/176090), [224488](https://bugs.launchpad.net/ubuntu/+source/linux-backports-modules-2.6.24/+bug/224488)), and now that's fixed and people start "threatening" that they are leaving Linux because the LED is working...

---

### Post by corman on 2008-11-24
> **jespdj said:**
> Funny... I remember that with 8.04 people were complaining that the Wifi LED doesn't work (see for example bugs [176090](https://bugs.launchpad.net/linux/+bug/176090), [224488](https://bugs.launchpad.net/ubuntu/+source/linux-backports-modules-2.6.24/+bug/224488)), and now that's fixed and people start "threatening" that they are leaving Linux because the LED is working...

HA! I never complained I had hoped the bug would be overlooked in Intrepid! but alas it was fixed...

---

### Post by oz-sco on 2008-11-26
ok with the scripts, i can get my light to stay on all the time, or off all the time, which is better, but i can't seem to get my script to run automatically..

As described by DavidY i have the script in my etc/network/if-up.d directory, and have typed the "chmod +x noblink.sh"
Am i missing something? running this script manually each time i boot is beginning to annoy me.

So anyone please, how do i run this, or perhaps any other script automatically.

cheers Oz

---

### Post by oz-sco on 2008-11-27
Anyone? I'd simply like to know how to make this script run automatically each time i boot my machine please?
The "just chmod xxxxx" type instructions don't appear to work, so clearly i need a little more information.
Or could someone at least point me to a basic guide to writing and running scripts of this sort in Linux?

cheers Oz

---

### Post by Muflon on 2008-11-27
After a few weeks I have become accustomed to the flashing and would miss it, if it disappeared. :)

Muflon

---

### Post by laptoplinux on 2008-12-01
> **jespdj said:**
> Funny... I remember that with 8.04 people were complaining that the Wifi LED doesn't work (see for example bugs [176090](https://bugs.launchpad.net/linux/+bug/176090), [224488](https://bugs.launchpad.net/ubuntu/+source/linux-backports-modules-2.6.24/+bug/224488)), and now that's fixed and people start "threatening" that they are leaving Linux because the LED is working...

I also never complained about the wifi light not working in Hardy.  In fact, I didn't even notice that the light wasn't working until I tried out Ibex and was incessantly reminded of the light's presence.  But anyway, there is a script now to fix it, and I'm still doing just fine on 8.04.  I'll just wait and see.  Upgrading every other release cycle is getting to be a tradition with me anyway.

---

### Post by lariosa42 on 2008-12-04
oz-sco:

Try System-->Preferences-->Sessions.  This allows you to create and edit startup commands.  Click the "Add" button and give it a name that will help you remember what it is.  For command, just try what you normally have to type to get it to execute.  On my system I would type

```

/etc/network/if-up.d/stopblink

```

I'm not totally sure if this will work since you may need the proper permissions to get it going, but this is one way to get something to execute on startup.

I am also fairly new to Linux.  I second your request for a basic guide to shell scripting.

---

### Post by Moz Holmes on 2008-12-07
Using oz-sco's script and laptoplinux's adaptation of it, the blinking has finally stopped on my Dell Inspiron 640m laptop. Thank you both!

It should be noted that the default behaviour of the LED on XP, the OS this laptop was originally (and unfortunately) designed around, is *not* for it to blink when wireless connectivity is up. 

I have had *no* problems with this blinking LED issue since first installing Ubuntu on this system, starting with Dapper Drake - only with Intrepid.

Not complaining, not threatening to leave Ubuntu... just trying to leave something constructive. ;)

Cheers

---

### Post by jsschreck on 2008-12-21
I can confirm also that oz-sco's script and laptoplinux's adaption of it worked for my Dell Inspiron 1525 (this was factory pre-installed with 8.04). Further, lariosa42's addition of the script into the boot-up routine ensures that the light stops blinking boot after boot. 

You will want to change around the first few lines in the script to match your directory set up. For me, the script is the following code: 

```

#!/bin/sh
echo none > /sys/bus/pci/drivers/iwl3945/0000:0b:00.0/leds/iwl-phy0:assoc/trigger
echo none > /sys/bus/pci/drivers/iwl3945/0000:0b:00.0/leds/iwl-phy0:radio/trigger
echo none > /sys/bus/pci/drivers/iwl3945/0000:0b:00.0/leds/iwl-phy0:RX/trigger
echo none > /sys/bus/pci/drivers/iwl3945/0000:0b:00.0/leds/iwl-phy0:TX/trigger

echo none > /sys/class/leds/iwl-phy0:RX/trigger
echo none > /sys/class/leds/iwl-phy0:TX/trigger
echo none > /sys/class/leds/iwl-phy0:radio/trigger
echo none > /sys/class/leds/iwl-phy0:assoc/trigger

```

John Schreck

---

### Post by lavarock on 2009-03-31
Just want to confirm that the above script fixed it for me as well.  I have a dell XPS M1210.

---

### Post by laptoplinux on 2009-04-11
I'm just coming back to this thread after working on this problem with Jaunty.... This is a "feature" of all the newer kernels for now.....](*,).

Anyway, To give credit where it's due, it was lariosa42's suggestion to change the 0b to 0c (post #25 of this thread).  All I did was try it and confirm that it worked for me.

I've done a little more digging with it in the Jaunty Beta.  I also played with it some in the Fedora 11 Beta.  This is a kernel issue, so the distro shouldn't affect things too much.  

At least with Fedora (and I'm assuming it would be the same on Jaunty--Fedora just happens to be what I tested under):

The /sys/bus/pci/drivers/iwl3945/0000:0c:00.0/leds/iwl* and /sys/class/leds/* settings appear to mirror each other; change on and the corresponding setting in the other area is changed.  Symbolic link maybe?
That being the case, I'd just go for changing the /sys/class/leds/iwl* triggers.  Less to type.  

Also, under the latest release betas, I found that changing the RX and TX triggers to "none" appeared to have no effect.  Changing the radio trigger to "none" made the light turn off completely, and changing the assoc trigger to "none" made the light remain solidly on.

In case anyone is wondering, the values of these triggers can be found by using cat (example):

cat /sys/class/leds/iwl-phy0\:assoc/trigger

This will produce a list of values, with the one in brackets being the currently selected one.  

Again, this is just some digging I did in preparation for giving Jaunty a shot later.  I don't really understand this stuff, and I can't guarantee it will work for any machine other than mine.

---

### Post by mobusby on 2009-04-22
The files you want to change are in /sys/class/leds and are symbolic links to the LED controls.  You can do
```

stat /sys/class/leds/* 
```
to see where the links point to, but it is unimportant.

TX and RX are for transfer and receive (respectively), and control behavior when transferring or receiving data; assoc takes over when the card connects to an access point; radio takes over before association takes place, and just lets you know if the card is active or not.

This script is perhaps a bit more elegant, and works if you have multiple effected wi-fi cards installed.  It only allows blinking when connecting.  The LED remains solid and on at all other times (when the wi-fi card is enabled or when it has a steady link).  I find this behavior minimally invasive but still useful for debugging and troubleshooting network issues.

```

#!/bin/bash

if [ "$IFACE" = "wlan0" ]; then
	for direc in /sys/class/leds/iwl-phy*X
	do
		echo none > $direc/trigger
		# never trigger blinking for TX, RX
	done
	
	for direc in /sys/class/leds/iwl-phy*radio
	do
		echo none > $direc/trigger
		# never trigger blinking for radio
	done

	# customize this loop to act on any relevant wi-fi cards
	for direc in /sys/class/leds/iwl-phy0:assoc
	do
		echo phy0assoc > $direc/trigger
		# do trigger blinking during association
	done
fi 
```

Place this script in /etc/network/if-up.d/ (call it whatever you want) and do
```

sudo chown root /etc/network/if-up.d/<script name>
sudo chmod a+x /etc/network/if-up.d/<script name> 
```

This worked for me with Intrepid and works now on Jaunty RC.  Hopefully it will work for other people, too!

---

### Post by Illusion65 on 2009-04-24
Hi mobusby,

I just posted in the [buglist]("http://bugs.launchpad.net/ubuntu/+source/linux/+bug/250211/") for this that the problem is with the phy0:assoc/trigger property -- even though it seems to be set to phy0assoc, it is not; but probably is set to phy0rx or phy0tx, causing the LED to blink when there is traffic.

Running:
```
sudo echo phy0assoc >/sys/class/leds/iwl-phy0\:assoc/trigger
```
will clear the problem until the next WiFi network connection is made.

I have not been able to find a way to clear the problem "automatically".  Even putting that line as a script in the /etc/network/if-up.d/ directory did not fix it for me (nor did putting your script there).

The /sys/class/leds/iwl-phy0* links are recreated when a new connection occurs, so I think the "fix" will be within the HAL or UDEV systems.

Doug

---

### Post by ptader on 2009-04-26
mobusby, thank you.  Your script worked for my Dell Precision, M90 with 9.04

One tip for everybody - test by clicking the "Enable Wireless" and/or "Enable Networking" on and off in the NetworkManager applet in the menu bar.  Better than rebooting or rerunning the network init script.

---

### Post by jmr1948 on 2009-04-26
Hi,

I just installed 9.04 and am experiencing this problem.  I created the file "stopblink" referenced above and it turns of the wireless led if I run it with the sudo command in terminal.  But I can't figure out a way to run it automatically at startup.  Just putting the command "etc/network/if-up.d/stopblink" as a startup command does nothing.  Tried a few other things involving the init.d directory, to no avail.

I actually know nothing about linux, so any help on this would be greatly appreciated.

BTW, I'm not averse to using a piece of black tape, but this solution seems so agonizingly close that I'd love to do it.

Thanks

---

### Post by ptader on 2009-04-26
Lets take a look.  What do the following commands (in bold) return?  Did you make your script "executable"?  I called my script wifi_led.


ptader@falcon:~$ **ls -l /etc/network/if-up.d/**
total 24
-rwxr-xr-x 1 root root  886 Mar 23 05:19 avahi-autoipd
-rwxr-xr-x 1 root root  504 Mar 23 05:19 avahi-daemon
-rwxr-xr-x 1 root root 4297 Mar 31 04:11 mountnfs
-rwxr-xr-x 1 root root 1171 Mar 20 19:49 ntpdate
**-rwxr-xr-x** 1 root root  547 Apr 26 11:20 wifi_led
lrwxrwxrwx 1 root root   32 Apr 24 13:38 wpasupplicant -> ../../wpa_supplicant/ifupdown.sh

ptader@falcon:~$ **cat /etc/network/if-up.d/wifi_led **
#!/bin/bash

if [ "$IFACE" = "wlan0" ]; then
    for direc in /sys/class/leds/iwl-phy*X
    do
        echo none > $direc/trigger
        # never trigger blinking for TX, RX
    done
    
    for direc in /sys/class/leds/iwl-phy*radio
    do
        echo none > $direc/trigger
        # never trigger blinking for radio
    done

    # customize this loop to act on any relevant wi-fi cards
    for direc in /sys/class/leds/iwl-phy0:assoc
    do
        echo phy0assoc > $direc/trigger
        # do trigger blinking during association
    done
fi

Hope this helps,
Paul

---

### Post by lavarock on 2009-04-28
> I have not been able to find a way to clear the problem "automatically". Even putting that line as a script in the /etc/network/if-up.d/ directory did not fix it for me (nor did putting your script there).

The /sys/class/leds/iwl-phy0* links are recreated when a new connection occurs, so I think the "fix" will be within the HAL or UDEV systems.

Same for me, and to Paul, I had the same script and set the right owner (root) etc but it still doesnt work. 
However manually do
```
# su
# echo phy0assoc >/sys/class/leds/iwl-phy0\:assoc/trigger
# exit
```
works (btw for me sudo doesn't work)

BTW found out the problem why the script is not working for me, since gnome Network Manager comes with Ubuntu 9.04 disconnects my wireless connection every 5 minutes, I had to switch to wicd, and wicd doesn't call these scripts in /etc/network/if-up.d/.  Once I add my script in wicd it works, btw my script is:
```
#!/bin/bash
echo none > /sys/class/leds/iwl-phy0\:assoc/trigger
```

---

### Post by ldjuda on 2009-05-28
> **mobusby said:**
> The files you want to change are in /sys/class/leds and are symbolic links to the LED controls.  You can do
```

stat /sys/class/leds/* 
```to see where the links point to, but it is unimportant.

TX and RX are for transfer and receive (respectively), and control behavior when transferring or receiving data; assoc takes over when the card connects to an access point; radio takes over before association takes place, and just lets you know if the card is active or not.

This script is perhaps a bit more elegant, and works if you have multiple effected wi-fi cards installed.  It only allows blinking when connecting.  The LED remains solid and on at all other times (when the wi-fi card is enabled or when it has a steady link).  I find this behavior minimally invasive but still useful for debugging and troubleshooting network issues.

```

#!/bin/bash

if [ "$IFACE" = "wlan0" ]; then
    for direc in /sys/class/leds/iwl-phy*X
    do
        echo none > $direc/trigger
        # never trigger blinking for TX, RX
    done
    
    for direc in /sys/class/leds/iwl-phy*radio
    do
        echo none > $direc/trigger
        # never trigger blinking for radio
    done

    # customize this loop to act on any relevant wi-fi cards
    for direc in /sys/class/leds/iwl-phy0:assoc
    do
        echo phy0assoc > $direc/trigger
        # do trigger blinking during association
    done
fi 
```Place this script in /etc/network/if-up.d/ (call it whatever you want) and do
```

sudo chown root /etc/network/if-up.d/<script name>
sudo chmod a+x /etc/network/if-up.d/<script name> 
```This worked for me with Intrepid and works now on Jaunty RC.  Hopefully it will work for other people, too!
Just informing users that this worked on my Dell XPS M1210 after I rebooted. Thanks mobusby!

---

### Post by giancaldo on 2009-08-28
works perfectly for me on the dell e6500. Thanks from me too mobusby

---

### Post by mobusby on 2009-10-15
It seems my little script needs updating for Karmic.  Now there is an extra ":" in the directory names.  This modified script should be a bit more flexible with names.

```
#!/bin/bash

if [ "$IFACE" = "wlan0" ]; then
    for direc in /sys/class/leds/iwl-phy*X
    do
        echo none > $direc/trigger
        # never trigger blinking for TX, RX
    done
    
    for direc in /sys/class/leds/iwl-phy*radio
    do
        echo none > $direc/trigger
        # never trigger blinking for radio
    done

    # customize this loop to act on any relevant wi-fi cards
    for direc in /sys/class/leds/iwl-phy*assoc
    do
        echo phy0assoc > $direc/trigger
        # do trigger blinking during association
    done
fi
```

Cheers!

---

### Post by arslano on 2009-10-24
hello

i'm very new at ubuntu, and i couldn't figure out how to do this.

i created an empty document and i gave blinking.sh as a name of the file. and then i copied the code into this file, and i put the file to if-up.d folder

but nothing chaned. my notebook is dell xps 1340.

furthermore i didnt understand how to run echo.. command in the terminal. for e.g i type

```
sudo echo phy0assoc >/sys/class/leds/iwl-phy0\:assoc/trigger
```onto terminal windows but it says no such file or directory

can  you please help me?

p.s. this is the output of stat /sys/class/leds/*

>   File: `/sys/class/leds/ath9k-phy0:assoc' -> `../../devices/pci0000:00/0000:00:16.0/0000:06:00.0/leds/ath9k-phy0:assoc'
  Size: 0             Blocks: 0          IO Block: 4096   symbolic link
Device: 0h/0d    Inode: 10868       Links: 1
Access: (0777/lrwxrwxrwx)  Uid: (    0/    root)   Gid: (    0/    root)
Access: 2009-10-24 23:56:59.381687188 -0400
Modify: 2009-10-24 23:48:03.737685179 -0400
Change: 2009-10-24 23:48:03.737685179 -0400
  File: `/sys/class/leds/ath9k-phy0:radio' -> `../../devices/pci0000:00/0000:00:16.0/0000:06:00.0/leds/ath9k-phy0:radio'
  Size: 0             Blocks: 0          IO Block: 4096   symbolic link
Device: 0h/0d    Inode: 10859       Links: 1
Access: (0777/lrwxrwxrwx)  Uid: (    0/    root)   Gid: (    0/    root)
Access: 2009-10-24 23:56:59.381687188 -0400
Modify: 2009-10-24 23:48:03.737685179 -0400
Change: 2009-10-24 23:48:03.737685179 -0400
  File: `/sys/class/leds/ath9k-phy0:rx' -> `../../devices/pci0000:00/0000:00:16.0/0000:06:00.0/leds/ath9k-phy0:rx'
  Size: 0             Blocks: 0          IO Block: 4096   symbolic link
Device: 0h/0d    Inode: 10886       Links: 1
Access: (0777/lrwxrwxrwx)  Uid: (    0/    root)   Gid: (    0/    root)
Access: 2009-10-24 23:56:59.381687188 -0400
Modify: 2009-10-24 23:48:03.737685179 -0400
Change: 2009-10-24 23:48:03.737685179 -0400
  File: `/sys/class/leds/ath9k-phy0:tx' -> `../../devices/pci0000:00/0000:00:16.0/0000:06:00.0/leds/ath9k-phy0:tx'
  Size: 0             Blocks: 0          IO Block: 4096   symbolic link
Device: 0h/0d    Inode: 10877       Links: 1
Access: (0777/lrwxrwxrwx)  Uid: (    0/    root)   Gid: (    0/    root)
Access: 2009-10-24 23:56:59.381687188 -0400
Modify: 2009-10-24 23:48:03.737685179 -0400
Change: 2009-10-24 23:48:03.737685179 -0400

thanks

---

### Post by arslano on 2009-10-25
now i change the code as 

```
sudo echo phy0assoc >/sys/class/leds/ath9k-phy0\:assoc/trigger
```

but it's written on the terminal windows is:

Permission denied

??

---

### Post by yunone on 2009-10-26
> **arslano said:**
> now i change the code as 

```
sudo echo phy0assoc >/sys/class/leds/ath9k-phy0\:assoc/trigger
```

but it's written on the terminal windows is:

Permission denied

??

its pretty straight forward and it did the trick for my Dell E6400

lets start

open terminal
type the following in terminal "sudo gedit"

you will notice it opens gedit, now with root privileges

paste the script from Mobusbys post into the text file
save the file as "blink" in the following folder "file system>etc>network>if-up.d

now close gedit

in terminal type the following 

sudo chown root /etc/network/if-up.d/blink

press enter

type the following in terminal

sudo chmod a+x /etc/network/if-up.d/blink

press enter


close terminal

restart machine


that should do the trick, if not post back


cheers

---

### Post by hcm2009 on 2009-10-26
> **laptoplinux said:**
> Whoa, whoa, whoa.  Who said anything about going back to Windows?  I used to use Windows, like 3 years ago.  But besides being a primitive, clunky mess, Windows is entirely unsuited for the work that I currently do.

If anything, I'd go pickup a shiny new Macbook and carry on.  But until I am forced to move off of Hardy or replace my current computer, that's all moot.

(That script may work to fix the blinking.  If so, great.  But Ibex also had a bad habit of constantly dropping connections on me.)

We'll just see what happens.  Surely enough people will be annoyed by this that the devs will eventually correct it.... right?

Hi all!
I've just visited this forum. Happy to get acquainted with you. Thanks.

---

### Post by ldjuda on 2009-10-29
> **mobusby said:**
> The files you want to change are in /sys/class/leds and are symbolic links to the LED controls.  You can do
```

stat /sys/class/leds/* 
```to see where the links point to, but it is unimportant.

TX and RX are for transfer and receive (respectively), and control behavior when transferring or receiving data; assoc takes over when the card connects to an access point; radio takes over before association takes place, and just lets you know if the card is active or not.

This script is perhaps a bit more elegant, and works if you have multiple effected wi-fi cards installed.  It only allows blinking when connecting.  The LED remains solid and on at all other times (when the wi-fi card is enabled or when it has a steady link).  I find this behavior minimally invasive but still useful for debugging and troubleshooting network issues.

```

#!/bin/bash

if [ "$IFACE" = "wlan0" ]; then
    for direc in /sys/class/leds/iwl-phy*X
    do
        echo none > $direc/trigger
        # never trigger blinking for TX, RX
    done
    
    for direc in /sys/class/leds/iwl-phy*radio
    do
        echo none > $direc/trigger
        # never trigger blinking for radio
    done

    # customize this loop to act on any relevant wi-fi cards
    for direc in /sys/class/leds/iwl-phy0:assoc
    do
        echo phy0assoc > $direc/trigger
        # do trigger blinking during association
    done
fi 
```Place this script in /etc/network/if-up.d/ (call it whatever you want) and do
```

sudo chown root /etc/network/if-up.d/<script name>
sudo chmod a+x /etc/network/if-up.d/<script name> 
```This worked for me with Intrepid and works now on Jaunty RC.  Hopefully it will work for other people, too!

This script worked on Ubuntu 9.04 installed on a Dell XPS M1210 but now it does not work on Ubuntu 9.10.

---

### Post by yunone on 2009-10-29
> **ldjuda said:**
> This script worked on Ubuntu 9.04 installed on a Dell XPS M1210 but now it does not work on Ubuntu 9.10.

i just did this last night on 9.10 on my E6400 and it works like a charm


can you step by step walk us through what you are doing?

---

### Post by ldjuda on 2009-10-29
> **yunone said:**
> i just did this last night on 9.10 on my E6400 and it works like a charm


can you step by step walk us through what you are doing?
```
sudo nano /etc/network/if-up.d/stopBlink
```paste the the script then save.

```
sudo chown root /etc/network/if-up.d/stopBlink
``````
sudo chmod a+x /etc/network/if-up.d/stopBlink
``````
sudo -i
``````
reboot
```

---

### Post by yunone on 2009-10-29
> **ldjuda said:**
> ```
sudo nano /etc/network/if-up.d/stopBlink
```paste the the script then save.

```
sudo chown root /etc/network/if-up.d/stopBlink
``````
sudo chmod a+x /etc/network/if-up.d/stopBlink
``````
sudo -i
``````
reboot
```


grab mobusbys new script right above and do the following...this is what i did and works great


its pretty straight forward and it did the trick for my Dell E6400

lets start

open terminal
type the following in terminal "sudo gedit"

you will notice it opens gedit, now with root privileges

paste the script from Mobusbys post into the text file
save the file as "blink" in the following folder "file system>etc>network>if-up.d

now close gedit

in terminal type the following

sudo chown root /etc/network/if-up.d/blink

press enter

type the following in terminal

sudo chmod a+x /etc/network/if-up.d/blink

press enter


close terminal

restart machine

---

### Post by ldjuda on 2009-10-29
> **yunone said:**
> grab mobusbys new script right above and do the following...this is what i did and works great


its pretty straight forward and it did the trick for my Dell E6400

lets start

open terminal
type the following in terminal "sudo gedit"

you will notice it opens gedit, now with root privileges

paste the script from Mobusbys post into the text file
save the file as "blink" in the following folder "file system>etc>network>if-up.d

now close gedit

in terminal type the following

sudo chown root /etc/network/if-up.d/blink

press enter

type the following in terminal

sudo chmod a+x /etc/network/if-up.d/

press enter


close terminal

restart machine
Appreciate the help but that method is the same as mine but the difference is you using gedit while I prefer using the console.  That method did not resolve my issue.  Also have in mind we both have different hardware.  I can get the wifi led to stop blinking by disconnecting and connecting back to my wireless network. But once I reboot I have to do the same process again which is tedious.

---

### Post by ldjuda on 2009-10-30
> **mobusby said:**
> It seems my little script needs updating for Karmic.  Now there is an extra ":" in the directory names.  This modified script should be a bit more flexible with names.

```
#!/bin/bash

if [ "$IFACE" = "wlan0" ]; then
    for direc in /sys/class/leds/iwl-phy*X
    do
        echo none > $direc/trigger
        # never trigger blinking for TX, RX
    done
    
    for direc in /sys/class/leds/iwl-phy*radio
    do
        echo none > $direc/trigger
        # never trigger blinking for radio
    done

    # customize this loop to act on any relevant wi-fi cards
    for direc in /sys/class/leds/iwl-phy*assoc
    do
        echo phy0assoc > $direc/trigger
        # do trigger blinking during association
    done
fi
```Cheers!
It's seems that I miss this post by mobusby patching the script for Karmic.  Thanks dude, this script works on my XPS-M1210 Laptop.  Much appreciated.

---

### Post by Cris(c) on 2009-11-03
The script not only stops the blinking but also kills the led. Now the led is always off in my Sony VAIO VGN-C240e laptop...is there something I'm missing?

UPDATE: Never mind. Now it's working perfectly....thanks!

---

### Post by picopir8 on 2009-11-05
This script works for a short period (<1 minute) after boot or wakeup from suspend but then begins flashing again.  I have wifi during the time when it is not flashing so I know the script must have run.  In order to stop the blinking I have to manually disable then re-enable wifi.

Also my led does not blink on/off it alternates between red/blue.  Normally it is red when wifi is disabled, blue when connecting, and alternating when connected. This script stopps the blinking but it is sometimes red when connected and othertimes blue.  It seems to be somewhat random.  It would be nice if it were always blue when connected.

---

### Post by spez on 2009-11-05
I've upgraded the script and it works with karmic. Using this script I can stop the led blinking when I'm connected on my home wi-fi, while when I connect at the University wi-fi (in wich use a script to authenticate myself) the led continues to blink, even if I run the script manually.
how can I solve?

---

### Post by squaregoldfish on 2009-11-08
Just been playing around with this one in Karmic on my Dell Inspiron 1525. If I echo 'none' into the trigger files, the wifi LED is switched off altogether. However, if I use 'phy0radio' instead, I get a solid LED when the network's active.

Steve.

---

### Post by yunone on 2009-11-09
edit..i should my own instructions better :)

---

### Post by arslano on 2009-11-11
> **yunone said:**
> its pretty straight forward and it did the trick for my Dell E6400

lets start

open terminal
type the following in terminal "sudo gedit"

you will notice it opens gedit, now with root privileges

paste the script from Mobusbys post into the text file
save the file as "blink" in the following folder "file system>etc>network>if-up.d

now close gedit

in terminal type the following 

sudo chown root /etc/network/if-up.d/blink

press enter

type the following in terminal

sudo chmod a+x /etc/network/if-up.d/blink

press enter


close terminal

restart machine


that should do the trick, if not post back


cheers


Thank you for the instructions. However, it didn't work for me.

My network adapter is 'ath9k', and I just replace 'iwl' with 'ath9k', and this is my 'blink' file in if-up.d directory:

```
if [ "$IFACE" = "wlan0" ]; then
    for direc in /sys/class/leds/ath9k-phy*X
    do
        echo none > $direc/trigger
        # never trigger blinking for TX, RX
    done
    
    for direc in /sys/class/leds/ath9k-phy*radio
    do
        echo none > $direc/trigger
        # never trigger blinking for radio
    done

    # customize this loop to act on any relevant wi-fi cards
    for direc in /sys/class/leds/ath9k-phy0:assoc
    do
        echo phy0assoc > $direc/trigger
        # do trigger blinking during association
    done
fi
```Is there any problem with the CODE? After I save this file, I can confirm that I entered the above commands which are:

> sudo chown root /etc/network/if-up.d/blink

sudo chmod a+x /etc/network/if-up.d/blink



Thank you

---

### Post by arslano on 2009-11-11
Hello

This is the last edit of mine, and still I can't stop blinking the led. Can you help me please?

```
if [ "$IFACE" = "wlan0" ]; then
    for direc in /sys/class/leds/ath9k-phy0::rx
    do
        echo none > /sys/class/leds/ath9k-phy0::rx/trigger
        # never trigger blinking for TX, RX
    done


    for direc in /sys/class/leds/ath9k-phy0::tx
    do
        echo none > /sys/class/leds/ath9k-phy0::tx/trigger
        # never trigger blinking for TX, RX
    done

    
    for direc in /sys/class/leds/ath9k-phy0::radio
    do
        echo none > /sys/class/leds/ath9k-phy0::radio/trigger
        # never trigger blinking for radio
    done

    # customize this loop to act on any relevant wi-fi cards
    for direc in /sys/class/leds/ath9k-phy0::assoc
    do
        echo phy0assoc > /sys/class/leds/ath9k-phy0::assoc/trigger
        # do trigger blinking during association
    done
fi
```

These are the directories in /leds:

ath9k-phy0::assoc  ath9k-phy0::radio  ath9k-phy0::rx  ath9k-phy0::tx  mmc0::

---

### Post by yunone on 2009-11-11
> **arslano said:**
> Hello

This is the last edit of mine, and still I can't stop blinking the led. Can you help me please?

```
if [ "$IFACE" = "wlan0" ]; then
    for direc in /sys/class/leds/ath9k-phy0::rx
    do
        echo none > /sys/class/leds/ath9k-phy0::rx/trigger
        # never trigger blinking for TX, RX
    done


    for direc in /sys/class/leds/ath9k-phy0::tx
    do
        echo none > /sys/class/leds/ath9k-phy0::tx/trigger
        # never trigger blinking for TX, RX
    done

    
    for direc in /sys/class/leds/ath9k-phy0::radio
    do
        echo none > /sys/class/leds/ath9k-phy0::radio/trigger
        # never trigger blinking for radio
    done

    # customize this loop to act on any relevant wi-fi cards
    for direc in /sys/class/leds/ath9k-phy0::assoc
    do
        echo phy0assoc > /sys/class/leds/ath9k-phy0::assoc/trigger
        # do trigger blinking during association
    done
fi
```

These are the directories in /leds:

ath9k-phy0::assoc  ath9k-phy0::radio  ath9k-phy0::rx  ath9k-phy0::tx  mmc0::

unfortunately i cant help with the code, sorry....maybe Mobusby will chime in

---

### Post by Ampi on 2009-11-12
I had problems with my LED light as well on an Acer Aspire One ZG5 while using UNR 9.04. 
But when I upgraded to UNR 9.10 the problems is fixed for 95%. Sometimes the light doesn't function most of the time it does, but blinking pretty much never.

---

### Post by laptoplinux on 2009-11-12
I have a Dell Latitude D820 on Ubuntu Karmic, and I've tried the Karmic-modified version of the script, but no luck.  Has anyone else with a similar laptop figured out how to keep the light either off or constant while connected to a wifi network?

---

### Post by laptoplinux on 2009-11-12
Ok, better question.  I've figured out how to make the script work, but I have to manually run it every time the computer connects to a wireless network.  Is there a way to make this script run automatically each and every time a wireless connection is made?

---

### Post by ClanClover on 2009-11-27
I have a Dell 6400 and just updated to 9.10 and the blinking LED problem re-appeared as it did when I updated to 9.04! Why can't this be sorted in the kernel? Anyway Mobusby's final code worked for me:

#!/bin/bash

if [ "$IFACE" = "wlan0" ]; then
    for direc in /sys/class/leds/iwl-phy*X
    do
        echo none > $direc/trigger
        # never trigger blinking for TX, RX
    done
    
    for direc in /sys/class/leds/iwl-phy*radio
    do
        echo none > $direc/trigger
        # never trigger blinking for radio
    done

    # customize this loop to act on any relevant wi-fi cards
    for direc in /sys/class/leds/iwl-phy*assoc
    do
        echo phy0assoc > $direc/trigger
        # do trigger blinking during association
    done
fi


But can we have this sorted next time there is an update?

---

### Post by john newbuntu on 2009-11-27
Mobusby's post #41 in this thread (April 23,2009) worked for me.  I have a Dell Inspiron E1505 laptop where I have recently installed Ubuntu Karmic 9.10 running the 2.6.31-15-generic linux kernel along with Windows XP media center edition.

Now, just a small tip here. When you place your script in /etc/network/if-up.d make sure that your script does not end with an extension.  For example "stopblink" will work but not "stopblink.bash".  Also, to ensure that your script is getting picked up at network startup time, run this command on a terminal:

```
sudo run-parts --list /etc/network/if-up.d
```

Thank you mobusby and everyone else who participated.

---

### Post by dmflad on 2009-12-12
Dell D620 LT running Ubuntu 9.10 32-bit. Used Mosby's script (post 41) and how-to but still blinking. Used the stat command [stat /sys/class/leds/*] to see where/what and then saw that I needed to add a second colon(:) at ln 18 col47 of script to match what STAT cmd shows. Bounced network connection and blinking has stopped. Thanks folks for all the work you do!

---

### Post by ant1060 on 2010-01-15
Hi :)
A big thank you to Mobusbys :D and to Yunone :D for their posts N°49 and N°52.  I followed these and now my wifi light has stopped blinking and sanity has been saved...
What would we do without the kind people who know the answers to problems and take the time to let us know how to fix them?
Cheers and thanks once more!

---

### Post by SamJack on 2010-02-23
Mobusby, 

Thank you very much.  You're a true savior of my sanity. The LED stopped blinking and with that my eye has stopped twitching finally while my facial tics have reduced. ;)

Thank you. It can get so difficult for someone beginning to use Linux. The first few months is where help from stalwarts keeps us newbies alive. 

best,
Sam

---

### Post by mobusby on 2010-03-02
Welcome to the community, Sam!

---

### Post by tacutu on 2010-03-27
darn, this doesn't work anymore in Lucid Lynx!

---

### Post by ptorpman on 2010-04-02
Hi!

Thanks for this script! I am now running Ubuntu 10.04 on my Inspiron 9400 and the blinking has disappeared!!! I am so happy ;-)

I just had to change the paths a bit... to 

  /sys/bus/pci/drivers/iwl3945/0000:0c:00.0/leds/iwl-phy0::assoc/trigger
  etc.

i.e add another colon and change 0b to 0c...

Once again, thanks!

/ Peter

---

### Post by heinzawin on 2010-04-10
ok, Can anyone tell me step by step? I am new to ubuntu.

---

### Post by yunone on 2010-04-18
> **ptorpman said:**
> Hi!

Thanks for this script! I am now running Ubuntu 10.04 on my Inspiron 9400 and the blinking has disappeared!!! I am so happy ;-)

I just had to change the paths a bit... to 

  /sys/bus/pci/drivers/iwl3945/0000:0c:00.0/leds/iwl-phy0::assoc/trigger
  etc.

i.e add another colon and change 0b to 0c...

Once again, thanks!

/ Peter

can you post a simple step by step for people please?


thanks in advance

---

### Post by mobusby on 2010-04-25
This fix is working on 10.04 RC (Lucid RC) with the following script:

```
#!/bin/sh

if [ "$IFACE" = "wlan0" ]; then
	for direc in /sys/class/leds/iwl-phy*X
	do
		echo none > $direc/trigger
		# never trigger blinking for TX, RX
	done
	
	for direc in /sys/class/leds/iwl-phy*radio
	do
		echo none > $direc/trigger
		# never trigger blinking for radio
	done

	for direc in /sys/class/leds/iwl-phy0*assoc
	do
		echo phy0assoc > $direc/trigger
		# do trigger blinking during association
	done
fi
```

As before, create the script in /etc/network/if-up.d/ (call it whatever you want, I named the script "iwl-no-blink").
```
sudo gedit /etc/network/if-up.d/iwl-no-blink
```
And give it the proper ownership and access rights
```
sudo chown root /etc/network/if-up.d/iwl-no-blink
sudo chmod a+x /etc/network/if-up.d/iwl-no-blink
```

---

### Post by OMFGitsme on 2010-05-23
[mobusby]("http://ubuntuforums.org/member.php?u=414630"), your script worked for me after I made a few modifications. I just needed to change the directories. 
```
#!/bin/sh

if [ "$IFACE" = "wlan0" ]; then
    for direc in /sys/class/leds/ath9k-phy0::rx
    do
        echo none > $direc/trigger
        # never trigger blinking for RX
    done
    
    for direc in /sys/class/leds/ath9k-phy0::radio
    do
        echo none > $direc/trigger
        # never trigger blinking for radio
    done

    for direc in /sys/class/leds/ath9k-phy0::assoc
    do
        echo phy0assoc > $direc/trigger
        # do trigger blinking during association
    done
    
    for direc in /sys/class/leds/ath9k-phy0::tx
    do
        echo phy0assoc > $direc/trigger
        # never trigger blinking for TX
    done
fi

```
Now my light only blinks when connecting to a network. 
Thank you.

---

### Post by Dolmio on 2010-08-24
> **mobusby said:**
> This fix is working on 10.04 RC (Lucid RC) with the following script:


Works great. Thanks a lot :D

/Dolmio

---

### Post by yunone on 2010-10-12
no more love on 10.10.... i have tried the three fixes but they no longer work for me on 10.10


thanks in advance

---

### Post by spez on 2010-10-13
yes I confirm this script is not working on 10.10
can anybody tell us how to fix?

---

### Post by jac_tict on 2010-10-14
Yes, not working on 10.10 :-(
No /sys/class/leds/iwl-phy* anymore.

---

### Post by cjsteele on 2010-10-14
I got this nailed in 10.10 -- to disable the blinking, you have to add the following line to /etc/modprobe/*iwlagn*.conf  (there should only be one file in there, on my HP EliteBook 8530w its /etc/modprobe.d/intel-5300-iwlagn-disable11n.conf)

options iwlcore led_mode=1


...once I did that, I simply did a `rmmod iwlagn` and `modprobe iwlagn`, and my blinking stopped!!!

w000t!

Cheers,
-C

---

### Post by cjsteele on 2010-10-14
> **cjsteele said:**
> options iwlcore led_mode=1


For the record, I figured that out by using `systool` a la:

```

# lsmod | grep -i iwl
iwlagn                202721  0 
iwlcore               146875  1 iwlagn
mac80211              266657  2 iwlagn,iwlcore
cfg80211              170293  3 iwlagn,iwlcore,mac80211
# systool -m iwlagn -av | grep led
# systool -m iwlcore -av | grep led
    led_mode = "0"
#

```

EUREKA!

I knew all I had to do was flip the bit... 

Cheers,
-C

---

### Post by nic-clark on 2010-10-15
> **cjsteele said:**
> I got this nailed in 10.10 -- to disable the blinking, you have to add the following line to /etc/modprobe/*iwlagn*.conf  (there should only be one file in there, on my HP EliteBook 8530w its /etc/modprobe.d/intel-5300-iwlagn-disable11n.conf)

options iwlcore led_mode=1


...once I did that, I simply did a `rmmod iwlagn` and `modprobe iwlagn`, and my blinking stopped!!!

w000t!

Cheers,
-C

Thanks for that... I might be being a bit thick, but what is a rmmod and modprobe and how do I do it - I'm a bit new! I have put the line in the right file already and saved it.

thanks!

---

### Post by cjsteele on 2010-10-15
> **nic-clark said:**
> Thanks for that... I might be being a bit thick, but what is a rmmod and modprobe and how do I do it - I'm a bit new! I have put the line in the right file already and saved it.

thanks!


Sure!  So, from a shell: 
```

# vi /etc/modprobe.d/iwl*
<make your change>
# rmmod iwlagn
# modprobe iwlagn

```

Those are the commands you use to manage/mangle the loadable kernel modules.  You'll want to know how to use these if you have to do too much with hardware.

Cheers,
-C

---

### Post by Evilandi666 on 2010-10-30
I tried that, but it doesn't work for my hp.

I have the same module as you, also iwlagn.

But options iwlcore led_mode=1 didn't do anything,

after reloading iwlagn, 

systool -m iwlcore -av | grep led 

says (same as before the changes):

led_mode            = "0"

and the led is blinking... :(

edit:

You have to do the following:
rmmod iwlagn
rmmod iwlcore
modprobe iwlcore
modprobe iwlagn

or reboot then it begins to work ;)
Sry guys!

---

### Post by Coreigh on 2010-12-17
Using 10.04 on an HP nc6320 this worked:
```
echo none > /sys/class/leds/iwl-phy0\:\:assoc/trigger
```

Notice there are TWO colons between [FONT="Courier New"]phy0[/FONT] and [FONT="Courier New"]assoc[/FONT]

I opened a terminal and ran the script manually and it returned an error that indicated a path problem, and then was able to resolve it.

I don't have anything running 10.10 right now to check.

I'll boot a 10.10 LiveCD and post here if I can get any results.

---

### Post by Coreigh on 2010-12-17
First thing I notice is that on the 10.10 LiveCD the led does NOT blink.
Second is that when I re-booted in to 10.04 I had to manually run the "no-blink" script to stop the blinking.
Third when in 10.10 the path [COLOR="Navy"]/sys/class/leds[/COLOR] leads to [COLOR="Red"]mmc0::[/COLOR] instead of [COLOR="Navy"]phys0::[/COLOR]

I hope someone find this helpful.

---

### Post by LK_gandalf_ on 2010-12-23
Hi, I have a Dell xps m1530 and freshly installed Kubuntu 10.10 64bit...and the damned blinking wifi-led problem.

I tried the script in the first page, but it's from a post written in 2008.....and it doesn't work. 
Quite disappointing I found that after 2 years the problem is still unsolved, or at least it seems like this. Have I miss something? :)

---

### Post by tanpopo_chan on 2011-01-11
For the sake of clarity, I'm going to repost my solution... This is taken from my reply here: [http://ubuntuforums.org/showpost.php?p=10342938&postcount=6](http://ubuntuforums.org/showpost.php?p=10342938&postcount=6)

By the way, I have an HP Pavillion dv6-2145es and I'm running Maverick (Ubuntu 10.10).


First, I looked up all of the possible solutions for the drivers available... Most are posted in this thread. (Thank you to OMFGitsme and mobusby!)

Then, I checked which driver I had by doing the following:

Open a terminal and put in:
```
sudo lshw -C Network
```

And this was my output:
```
*-network               
       description: **_Wireless interface_**
       product: AR9285 Wireless Network Adapter (PCI-Express)
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:08:00.0
       logical name: wlan0
       version: 01
       serial: c4:17:fe:74:70:5c
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes **_driver=ath9k_** driverversion=2.6.35-24-generic firmware=N/A ip=192.168.0.14 latency=0 link=yes multicast=yes wireless=IEEE 802.11bgn
       resources: irq:17 memory:f1200000-f120ffff
  *-network
       description: Ethernet interface
       product: RTL8111/8168B PCI Express Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:09:00.0
       logical name: eth0
       version: 03
       serial: c8:0a:a9:0e:22:af
       size: 10MB/s
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half latency=0 link=no multicast=yes port=MII speed=10MB/s
       resources: irq:45 ioport:2000(size=256) memory:f1004000-f1004fff memory:f1000000-f1003fff memory:f1010000-f101ffff
```
Notice how in the section "configuration" of my "Wireless interface" it says *driver=ath9k*? Welp! That's the solution to the problem! All you have to do is check which driver you've got and search the forum!

If you have the **iwlagn driver**, all you have to do is follow the solution from [http://ubuntuguide.net/stop-the-blinking-wireless-led-light-on-ubuntu-10-10-laptops](http://ubuntuguide.net/stop-the-blinking-wireless-led-light-on-ubuntu-10-10-laptops), and if you have the **ath5k driver**, follow the instructions posted at [http://ubuntuforums.org/showpost.php?p=9835897&postcount=7](http://ubuntuforums.org/showpost.php?p=9835897&postcount=7).
If you have the **ath9k driver** like me, here's what you do.

First, let's create a file where the code will execute. You can name it however you like, but just make sure you create it in the directory "/etc/network/if-up.d/". I named mine ath9k-no-blink.
So, let's go back to the terminal and type:
```
sudo gedit /etc/network/if-up.d/ath9k-no-blink
```


When gedit opens, paste the following, then save and close. This is us telling the led how to act. In other words, we're saying, "when the wifi's off, turn red, and when it's on, turn blue."
```
#!/bin/sh

if [ "$IFACE" = "wlan0" ]; then
    for direc in /sys/class/leds/ath9k-phy0::rx
    do
        echo none > $direc/trigger
        # never trigger blinking for RX
    done
    
    for direc in /sys/class/leds/ath9k-phy0::radio
    do
        echo none > $direc/trigger
        # never trigger blinking for radio
    done

    for direc in /sys/class/leds/ath9k-phy0::assoc
    do
        echo phy0assoc > $direc/trigger
        # do trigger blinking during association
    done
    
    for direc in /sys/class/leds/ath9k-phy0::tx
    do
        echo phy0assoc > $direc/trigger
        # never trigger blinking for TX
    done
fi
```


Now, after closing gedit, put in the following two lines in the terminal. Here we're making sure that only root can manipulate this file and giving it permission to execute.:
```
sudo chown root /etc/network/if-up.d/ath9k-no-blink
sudo chmod a+x /etc/network/if-up.d/ath9k-no-blink
```

Now, restart the computer and voilá! Problem fixed!


So just to wrap it up, if you have the ath9k driver, follow the instructions above.

For the ath5k driver, check this post: [http://ubuntuforums.org/showpost.php?p=9835897&postcount=7](http://ubuntuforums.org/showpost.php?p=9835897&postcount=7) 

If you have the iwlagn driver, follow the solution from [http://ubuntuguide.net/stop-the-blinking-wireless-led-light-on-ubuntu-10-10-laptops](http://ubuntuguide.net/stop-the-blinking-wireless-led-light-on-ubuntu-10-10-laptops).

---

### Post by cjsteele on 2011-01-11
so, yeah... I already solved this, you need to go ahead and sort-out what I showed you in my previous posts.  

Its real simple: you need to put two-and-two together, and solve it.

Cheers,
-C

---

### Post by slackhappy on 2011-01-12
cjsteele's method works fine for me (nice find!).  It is the option supported by the in-kernel driver, so if it isn't working for you, you are probably missing a step.  The other methods are really just hacks, and will probably vary by kernel release or dist release.

Here's a pointer to the lxr code:
[_module_param definition of led_mode_]("http://lxr.linux.no/linux+v2.6.37/drivers/net/wireless/iwlwifi/iwl-led.c#L46")

Note the intel dev's comments:
"led mode: 0=blinking, 1=On(RF On)/Off(RF Off), (default 0)"

Note, however, that in the future there probably won't automatically be a module config file is /etd/modules.d, so you will have to make it yourself.  

The reason it is there now is to disable the buggy 802.11n code, but this will probably be fixed soon.  You can track that here:

[_Ubuntu bug (with current workaround)_]("https://bugs.launchpad.net/ubuntu/maverick/+source/linux-firmware/+bug/630748")
[_Linux bug_]("https://bugzilla.kernel.org/show_bug.cgi?id=16691")

---

### Post by cjsteele on 2011-01-15
I'm glad someone found this useful... it was a bugger to sort-out the first time.  


Cheers,
-C

---

### Post by yunone on 2011-01-15
this worked for me in 10.04.1

Dell Latitude E6400 

thanks again Mobusby!!!!!!




> **mobusby said:**
> This fix is working on 10.04 RC (Lucid RC) with the following script:

```
#!/bin/sh

if [ "$IFACE" = "wlan0" ]; then
	for direc in /sys/class/leds/iwl-phy*X
	do
		echo none > $direc/trigger
		# never trigger blinking for TX, RX
	done
	
	for direc in /sys/class/leds/iwl-phy*radio
	do
		echo none > $direc/trigger
		# never trigger blinking for radio
	done

	for direc in /sys/class/leds/iwl-phy0*assoc
	do
		echo phy0assoc > $direc/trigger
		# do trigger blinking during association
	done
fi
```

As before, create the script in /etc/network/if-up.d/ (call it whatever you want, I named the script "iwl-no-blink").
```
sudo gedit /etc/network/if-up.d/iwl-no-blink
```
And give it the proper ownership and access rights
```
sudo chown root /etc/network/if-up.d/iwl-no-blink
sudo chmod a+x /etc/network/if-up.d/iwl-no-blink
```

---

### Post by mwsaz on 2011-03-12
Hi,

Just in case some people are having the same issue, there is a much simpler workaround (as posted above) :

Create /etc/modprobe.d/wlan.conf with this single line inside :
```
options iwlcore led_mode=1
```And the blinking is gone! :)

[http://www.linuxfocus.org/~guido/gentoo-x301/]("http://www.linuxfocus.org/%7Eguido/gentoo-x301/") (Annoying wifi led)

---

### Post by yunone on 2011-04-21
> **mwsaz said:**
> Hi,

Just in case some people are having the same issue, there is a much simpler workaround (as posted above) :

Create /etc/modprobe.d/wlan.conf with this single line inside :
```
options iwlcore led_mode=1
```And the blinking is gone! :)

[http://www.linuxfocus.org/~guido/gentoo-x301/]("http://www.linuxfocus.org/%7Eguido/gentoo-x301/") (Annoying wifi led)


in 10.04.1 and in 10.10 this caused my adapter to disappear completely and i no longer had the option to turn on wireless...i see it posted a lot on the webs, but cant figure out why its causing my adapter to disappear from the network icon

---

### Post by Bromden on 2012-05-01
wlan.conf is not working on 12.04.

How can i solve this problem?

---

