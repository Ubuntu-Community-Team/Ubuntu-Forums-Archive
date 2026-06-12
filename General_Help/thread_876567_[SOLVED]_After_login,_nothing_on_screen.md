---
title: "[SOLVED] After login, nothing on screen"
date: 2008-07-31
forum: General Help
---

### Post by Thrasonic on 2008-07-31
Hi all.  Something's happened and I can't seem to fix it.  I installed Ubuntu 8.04.1 tonight.  I uninstalled some applications and installed some applications through the Synaptic and Add/Remove.  I enabled hardware drivers.  I installed "automatic updates".  Everything seemed to be working fine.  I do want to say I rebooted once or twice during this process as well. 

However, I just rebooted a short while ago and when it came back up all I was getting was the wallpaper image after logging in.  No taskbars, no shut down button, just the wallpaper and a mouse pointer.  I held my power button in for a couple of seconds and did get the shut down screen so I chose to restart.

I than went into recovery mode and tried the x server auto fix option.  That didn't do it.  As a matter of fact, when I rebooted after that I didn't even have the wallpaper.  I only had a white screen and a mouse pointer.  So I shut off the PC and restarted it and went back into recovery mode.  This time I chose the console and I ran sudo dpkg-reconfigure xserver-xorg.  I went through the steps but that didn't fix the problem, either.  It didn't even give me the option to choose the video card or driver, the monitor specs, etc. like I've seen with older versions of Ubuntu.

So now I'm stuck.  I don't know what to do to fix this blank screen problem.  Any help would be great.

---

### Post by falcon61102 on 2008-07-31
The next time you boot up and get to the blank desktop, try either:
ALT+F1 and seeing if the run menu comes up.  At which time you can enter gnome-terminal or any other program to run.

or

CTRL+ALT+F1 or F2 and that should switch from the gnome desktop to a terminal only screen.

---

### Post by Thrasonic on 2008-07-31
Hi falcon.  ALT+F1 didn't work.  Ctrl+Alt+F1 took me a strange black and white screen with a bunch of lines of stuff that make no sense to me.  The last few lines read:

CailWriteATIRegister(6084,0)
CailReadATIRegister(60ec) = 100
CailWriteATIRegister(60ec,100)
Unblank CRTC 0 success

Any ideas on what I should aside from reinstall?

---

### Post by falcon61102 on 2008-07-31
Two things, when you boot up, try CTRL+ALT+BACKSPACE which will restart the GDM.

If that doesn't work, try CTRL+ALT+F1 again and if there is a command prompt available try:
```
sudo /etc/init.d gdm restart
```

Sometimes just refreshing the GDM can get it.  Also, do you have any older kernal version still available after running the updates.  If so, have you tried loading those instead of your most current version?

---

### Post by Thrasonic on 2008-07-31
Okay, from the weird black and white screen I was just on I went ahead and did Ctrl+Alt+Backspace just for fun.  That restarted the computer (gracefully).  

When it got to the bootloader menu I noticed only two kernels, the regular one and the recovery mode one.  The kernels were identical.

I booted into the normal kernel (generic, I think? I'm a newbie...) and came to the usual login screen, which looks fine every time.  On that screen I went ahead and hit Ctrl+Alt+Backspace and it did appear that the GDM (whatever that is) was restarted because the screen went black for a few seconds and than I was back at the login screen.

I went ahead and logged in and got the same thing again, a blank white screen and a mouse pointer.  So I just did the Ctrl+Alt+Backspace thing again to see what would happen and there was a flicker or reload of the screen and I was taken back to the login screen.  I logged in again as usual and got the same white screen with the mouse pointer.

Any other ideas?  I'm trying to figure out how to fix this without doing another reinstall...

---

### Post by falcon61102 on 2008-07-31
Something is definitely up with your xorg.conf.  What kind of graphics card or chipset do you have?

---

### Post by Thrasonic on 2008-08-01
Okay, I'm back.  I live on the east coast in the US so I just got to work (it's 8:40 a.m.).  Anyway, my card is an ATI Radeon x1600 PCIe card w/512 MB RAM.  If nothing else perhaps I can edit the xorg.conf file, but I don't know how to do that.

---

### Post by Thrasonic on 2008-08-01
Hi all.  So I saw in another thread to run this command - nano /var/log/Xorg.0.log - and see what the log shows.  Well, it's totally empty.  I don't know what that means.

But anyway, while I was at the command prompt I tried once again to get into the xorg.conf file and it actually let me!  Of course I can't copy and paste the info so I'm going to have to write it down and than post it by hand.  What a pain!  But maybe you can help me edit it to fix my current problem and get me back in with a GUI.

I'll be back shortly with the info.

---

### Post by Thrasonic on 2008-08-01
Okay, here's what's in my xorg.conf file.  It seems pretty empty to me.  I've seen these before and this one is definitely missing some stuff.  I didn't bother putting in all the lines at the top that are commented out and explain what the file is used for, etc.  Please help me out.  I'd love to not have to reinstall Ubuntu.

Section	"InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"us"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option	"CorePointer"
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
	Device 		"Configured Video Device"
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
EndSection

---

### Post by Thrasonic on 2008-08-01
Hi all.  I'm wondering if there's a generic xorg.conf setup that I could use to replace my existing xorg.conf?  Mine is obviously missing plenty of necessary information, as you can see from my post above.  The problem is that I don't know what's missing, what the values should be, etc.  I only know that important and necessary information is definitely missing.  So is there a basic or generic xorg.conf I can use in place of the one I have that will give me back my GUI?  I'm assuming if there is than once I get back into the GUI I can re-enable the ATI drivers and play around with the settings (and hopefully not screw up anything else).

---

### Post by Thrasonic on 2008-08-01
bump

---

### Post by TreeFinger on 2008-08-01
I believe you need to set your device driver.

Under the 'Device' Section:
```

Driver "driver"

```

As to what the value should be.. I have no idea. Try setting the value to "fglrx"

remember to keep the quotes around it.

--edit

I think your config is totally screwed. Do you have any backups of it? You can try just adding that Driver line and see if it does anything.

--edit

try this command
```

sudo dpkg-reconfigure xserver-xorg

```

---

### Post by Thrasonic on 2008-08-01
Is there anyone who hasn't installed the proprietary video drivers on their Ubuntu install yet that can give me what the settings should be in the xorg.conf file?

---

### Post by leomelo on 2008-08-01
Add the line:Driver   "vesa",like:

Section "Device"
Identifier "Configured Video Device"
Driver     "vesa"
EndSection

This is to get a graphic interface.

---

### Post by Thrasonic on 2008-08-01
Thanks.  Is there anything else I should add to to the xorg.conf file?

I'll go ahead and try this, reboot, and see what happens...

---

### Post by Thrasonic on 2008-08-01
> **leomelo said:**
> Add the line:Driver   "vesa",like:

Section "Device"
Identifier "Configured Video Device"
Driver     "vesa"
EndSection

This is to get a graphic interface.

So I just did this, rebooted, logged in, and now I have my wallpaper back but nothing else.  I must be missing something else.  Anyone?

---

### Post by falcon61102 on 2008-08-01
It's looks like you have about the most generic xorg.conf currently.  Based on that, it doesn't look like your graphics card is installed or configured properly.  

Besides running updates, did you install anything like Compiz or theme related?

---

### Post by Thrasonic on 2008-08-01
> **falcon61102 said:**
> It's looks like you have about the most generic xorg.conf currently.  Based on that, it doesn't look like your graphics card is installed or configured properly.  

Besides running updates, did you install anything like Compiz or theme related?

Nope, I hadn't yet installed all that stuff.  I wanted to, but hadn't gotten around to it.  My install was pretty vanilla; it was a brand new install.  I had activated or enabled the proprietary drivers, however.

---

### Post by falcon61102 on 2008-08-01
Do you have an integrated graphics chip besides the ATI board that you are using?  If so, you may be able to plug into that and use that just so you can get your system back to a useable state.  Then switch over to your ATI card again once you are stable.  

If you do have the integrated graphics chic, make sure it's enabled in the bios before you try to use it, otherwise you might run into some problems there.  Normally they are enabled by default but many times people disable them when using addon cards.

---

### Post by Thrasonic on 2008-08-01
I do, but it's not available when an add-on video card is installed on the mobo.  I'd never seen that before this mobo, but oddly enough that's how it is.  It's completely removed from the BIOS information and settings until I remove my ATI card.  Any other thoughts or should I just reinstall?

---

### Post by falcon61102 on 2008-08-01
Try running
```
lspci
```
and record the PCI address for your video card. ie Mine is "00:2:0"

Then go into your xorg.conf, lets try to manually edit it some more.  Copy this section of code, using your PCI Address that you just recorded in the Busid line:
```
Section "Device"
	Identifier	"Configured Video Device"
	Busid		"PCI:0:2:0"
	Driver		"vesa"
	Screen	0
	Vendorname	"ATI"
	Option		"XaaNoPixmapCache"
EndSection
```


Also, can you access the terminal inside the gnome now?  Which would allow you to run GUI apps.

---

### Post by Thrasonic on 2008-08-01
> **falcon61102 said:**
> Try running
```
lspci
```
and record the PCI address for your video card. ie Mine is "00:2:0"

Then go into your xorg.conf, lets try to manually edit it some more.  Copy this section of code, using your PCI Address that you just recorded in the Busid line:
```
Section "Device"
	Identifier	"Configured Video Device"
	Busid		"PCI:0:2:0"
	Driver		"vesa"
	Screen	0
	Vendorname	"ATI"
	Option		"XaaNoPixmapCache"
EndSection
```


Also, can you access the terminal inside the gnome now?  Which would allow you to run GUI apps.

Okay, I ran lspci and it spewed out a bunch of information.  Near the bottom I found this line:

03:00.0 VGA compatible controller: ATI Technologies Inc RV530LE [Radeon X1600]

So I added lines to make it look like this:

Section "Device"
	Identifier	"Configured Video Device"
	Busid		"PCI:3:0:0"
	Driver		"vesa"
	Screen	        0
	Vendorname	"ATI"
	Option		"XaaNoPixmapCache"
EndSection

I saved the file and rebooted.  I logged in and I'm still stuck at just my wallpaper.  I have no taskbars, icons, nothing.

What's your next idea?  I'm game to try something else.  :guitar:

I just realized you asked if I could access the terminal inside the gnome.  I'm having to do Ctrl+Alt+F1 to bring up a prompt.  How would I get to a terminal session within the GUI?

---

### Post by falcon61102 on 2008-08-01
Have you tried re-isntalling the drivers for you card?

Check the ATI website and see if they have drivers you can download and install for you card.

---

### Post by Thrasonic on 2008-08-01
> **falcon61102 said:**
> Have you tried re-isntalling the drivers for you card?

Check the ATI website and see if they have drivers you can download and install for you card.

Hmmm... I'm not sure how I'd do that or how to do that.  I mean, on the working computer I could go to their web site and download something, but than how would I install it on the Ubuntu computer that's not working?

---

### Post by falcon61102 on 2008-08-01
Download the drivers on the system that you have that is working and put them on a USB drive.  When you boot up, use the CTRL+ALT+F1 to get to the terminal and if necessary mount the USB drive.  Then copy the drivers to a folder on your ubuntu drive, extract and then install.  Normally they come with install directions that would walk you through it, so the hardest part would be getting them to your Ubuntu install.

---

### Post by Thrasonic on 2008-08-01
Intriguing idea.  I'll give it a shot.  How would I mount the drive?  And than what commands would I use to run the file?  I'm a newbie so I don't know what to do.  I'll go find the drivers for it now.

---

### Post by Thrasonic on 2008-08-01
Wow, I just saw my screen saver come on for the first time.  That was weird.  Nothing else works still, though...

---

### Post by Thrasonic on 2008-08-01
I've gone here to get the file:

[http://ati.amd.com/support/drivers/linux/linux-radeon.html](http://ati.amd.com/support/drivers/linux/linux-radeon.html)

It's a .run file.  Is that right?  It should be finished downloading in a minute.  Let me know what commands to run from the command prompt to mount the USB drive and execute the driver file.

Thanks a ton for all of your help, too.

---

### Post by Thrasonic on 2008-08-01
I'm looking at the installer info from the ATI web site now.  Sorry about missing that little part of your last post.

However, I still don't know how to mount the USB drive from the command line.  I've plugged in the drive but am now stuck.

---

### Post by falcon61102 on 2008-08-01
The .run file is pretty much equivilant to a .exe in windows so thats good.

As far as mounting your USB drive, try just plugging it in, it may automount as it should.  Once you plug the drive in and get to the terminal, run:
```
sudo df -a -h
```
That will list your partitions, so you can find out where your USB drive is mounted.  If you are unsure, post it here and I'll help you figure it out.  If you don't recognize your USB drive on that list, then also run and post:
```
sudo fdisk -l
```
-l being a lower case L

---

### Post by Thrasonic on 2008-08-01
Hi there.  Here's a new question.  I was able to mount the flash drive (YEAH!!!).  Very cool.  Anyway, I went into it by typing cd /media/kingston and ran the ls command against it.  I can see the file, which I named ati.run (it was going to save it as a .run file so I just shortened the name for easy execution from the command prompt).  So than I typed sudo ati.run and I get a command not found message.  Any thoughts?

---

### Post by Thrasonic on 2008-08-01
Maybe the .run file needs a GUI of some sort to run?  I can't figure out why the .run file won't execute.  It doesn't matter whether I type ati.run at the prompt or sudo ati.run - I get the same error message.

---

### Post by falcon61102 on 2008-08-01
You forgot one little part of the code:
```
sudo sh ati.run
```

---

### Post by Thrasonic on 2008-08-01
> **falcon61102 said:**
> You forgot one little part of the code:
```
sudo sh ati.run
```

Sweet.  I'm running it now.  I'll let you know shortly what happens...

---

### Post by Thrasonic on 2008-08-01
> **falcon61102 said:**
> You forgot one little part of the code:
```
sudo sh ati.run
```

That installation was very quick.  It finished with no errors so I rebooted the computer.  However, I'm still stuck at my wallpaper and no icons, taskbars, etc.  What's next?

---

### Post by falcon61102 on 2008-08-01
At this point, given the amount of time you've put into this vs the lack of progress you've gotten, it might be best to reinstall.  Save those drivers though, you can use them later.  Back anything you need up on the USB drive you've got and start fresh.  Hate to suggest that, but at this point that might be the best course of action.

---

### Post by Thrasonic on 2008-08-01
After installing the drivers I went into the xorg.conf file.  It now has two Device and Screen sections.  It has new stuff that was installed by the driver (I'm assuming) and the old stuff you and I put in there.  Should I remove the old stuff and restart the computer and see what happens?

---

### Post by Thrasonic on 2008-08-01
Well, that didn't work.  I removed the duplicated stuff and left what the driver installation put in but no go - same exact problem.  I'm going to reinstall.

Thanks a ton for your help.  Even though we didn't fix the problem I appreciate the time you took trying to help me fix it.

---

### Post by falcon61102 on 2008-08-01
Yeah, you could do that.  When you remove the old stuff, only remove the lines that are tabbed in.  Then copy the corresponding lines from the new and put them where the old is.  Otherwise when you restart, it won't read the new.  If that doesn't make and sense, post your xorg.conf and I'll show you what I mean

---

### Post by Thrasonic on 2008-08-01
Here's a question.  Should I install those ATI drivers I downloaded instead of using the ones, whatever they may be, that Ubuntu will download and install automatically when I enable the drivers?

---

### Post by falcon61102 on 2008-08-01
You could give the Ubuntu ones a try again, but it may lead to the issue you just had.  I normally try to stick with the Ubuntu distros as much as possible and only rely on other ones as a backup.  It could be that they just didn't install right last time and thats what led to this problem so I'd say go for the Ubuntu ones and fall back on the downloaded ones if you run into trouble.

---

### Post by Thrasonic on 2008-08-01
> **falcon61102 said:**
> You could give the Ubuntu ones a try again, but it may lead to the issue you just had.  I normally try to stick with the Ubuntu distros as much as possible and only rely on other ones as a backup.  It could be that they just didn't install right last time and thats what led to this problem so I'd say go for the Ubuntu ones and fall back on the downloaded ones if you run into trouble.

Great, than that's what I'll do.  Thanks for the advice.  My re-installation of Ubuntu is almost done...  \\:D/

---

### Post by Thrasonic on 2008-08-01
> **falcon61102 said:**
> At this point, given the amount of time you've put into this vs the lack of progress you've gotten, it might be best to reinstall.  Save those drivers though, you can use them later.  Back anything you need up on the USB drive you've got and start fresh.  Hate to suggest that, but at this point that might be the best course of action.

I honestly don't know what happened.  I uninstalled some applications, installed some new ones, enabled the proprietary drivers, etc.  I'm just not sure which thing I did broke the system.  Admittedly this is one of the things that ticks me off about Linux.  It seems like it breaks so easily.  Half the time I'm worried about installing or uninstalling something...

---

### Post by falcon61102 on 2008-08-01
It can be little frustrating when you're first trying to get it setup but once it's running it's worth all the little frustrations.  Just be patient when working with it.  I've also found that by doing things in smaller chunks, if I break something it's easier to figure out what exactly broke and then easier to fix it.  Takes a little longer initially but it helps the troubleshooting side.

---

### Post by Thrasonic on 2008-08-01
> **falcon61102 said:**
> It can be little frustrating when you're first trying to get it setup but once it's running it's worth all the little frustrations.  Just be patient when working with it.  I've also found that by doing things in smaller chunks, if I break something it's easier to figure out what exactly broke and then easier to fix it.  Takes a little longer initially but it helps the troubleshooting side.

Yeah, frustrating's a good word for it.  I've played around with Linux about every 1 1/2 years just to see how far it's come.  I've never felt like it could be a replacement for Windows (for me) until now.  I plan to stick with it, though.

Regarding doing things in smaller chunks, that's a good idea.  I assume you're referring to maybe installing one app at a time, rebooting in between to make sure nothing is broken?  And maybe uninstalling one thing at a time and going through the same types of motions?  If so, I get it and it makes sense.

---

### Post by falcon61102 on 2008-08-01
Yeah, if not one app at a time, maybe a 2-3.

---

