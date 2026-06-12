---
title: "I have a blank CD....."
date: 2009-04-19
forum: Installation &amp; Upgrades
---

### Post by Mister LinOx on 2009-04-19
[s]I just searched my house, and found a package of blank CD's. These CD's are 80 min., 700MB. I was wondering, will they be good enough to put a copy of Ubuntu or any variants on it?

Thank you in advanced. =D>[/s]


EDIT: Also, I started downloading the file just in case my CD is right, and it says an estimated 2 hours. Is that too long, or normal for the size of file the iso is?

2ndEDIT: Youn now, I really should have looked a little more thorough before wasting space. xP It turns out, my CD is right. BUT, the estimated time question is still open if you'd like to answer that for me. Hahah.

---

### Post by pytheas22 on 2009-04-19
Two hours is a reasonable download time for the Ubuntu CD image.  It's a large file.

---

### Post by Mister LinOx on 2009-04-19
> **pytheas22 said:**
> Two hours is a reasonable download time for the Ubuntu CD image.  It's a large file.

Thank you. That was what I had suspected, but I just wanted some reassurance.

---

### Post by Marlonsm on 2009-04-19
The Ubuntu .iso Image should fit pretty much any CD, so that ones will work (unless they are scratched or something). Also, many people don't like burning Ubuntu CDs at full speed, as any eroor they get means and error in the OS installed.

And the time it takes to download the .iso depends on what kind of connection you have. For me it takes about 5 hours, as it a ~650mb File

---

### Post by Mister LinOx on 2009-04-20
> **Marlonsm said:**
> The Ubuntu .iso Image should fit pretty much any CD, so that ones will work (unless they are scratched or something). Also, many people don't like burning Ubuntu CDs at full speed, as any eroor they get means and error in the OS installed.

And the time it takes to download the .iso depends on what kind of connection you have. For me it takes about 5 hours, as it a ~650mb File

Okay. I am at the InfraRecorder screen. I selected the iso, and it says to choose which speed and which write method. The default it has picked is Maximum and Session at Once. Is this what I want for a CD to install and maybe boot from Ubuntu, or do I need to change those?

---

### Post by SunnyRabbiera on 2009-04-20
> **Mister LinOx said:**
> Okay. I am at the InfraRecorder screen. I selected the iso, and it says to choose which speed and which write method. The default it has picked is Maximum and Session at Once. Is this what I want for a CD to install and maybe boot from Ubuntu, or do I need to change those?

you may want to change from max to a slower speed, nothing worse then a bad burn.

---

### Post by stanakis on 2009-04-20
the download time itself isn't something u can check if the iso is correct...u could take a look at the size of the file u downloading better XD or if u can't(wtf?) u can tell us the speed of your internet connection so that we see if it is ok...my internet connection needs something like 10 minutes to download the iso...;)

---

### Post by Mister LinOx on 2009-04-20
I attached an image to all the files in my burnt CD. Is this correct?

Also, when I ran CD integrity check this morning, it said no errors returned.

---

### Post by Eff3cTz on 2009-04-20
When I downloaded mine, it was 699 MB (designed specifically for 700MB discs, I suppose), and it took about 5-7 mins to download, and then an addition 2-3 mins to burn to a disc.

Good luck and have fun with Ubuntu!

---

### Post by Mister LinOx on 2009-04-20
Oh, and another question. 
When I boot form the disc, I select English and I want to try to get on without bothering anything first. So when I select that option, it goes to the loading screen and after a minute or so, the screen changes to a bright screen, then back to a dark purple/black like screen with just the movable cursor visible. Know how to fix this?

---

### Post by pytheas22 on 2009-04-20
> I attached an image to all the files in my burnt CD. Is this correct?

Also, when I ran CD integrity check this morning, it said no errors returned.

It looks fine to me, and if the integrity check passed, then you should definitely have a good copy.

> When I boot form the disc, I select English and I want to try to get on without bothering anything first. So when I select that option, it goes to the loading screen and after a minute or so, the screen changes to a bright screen, then back to a dark purple/black like screen with just the movable cursor visible. Know how to fix this?

This is using the same CD that you checked for errors previously, with no errors found?  If you wait a minute, does the desktop come up?  If not, it's possible that there's some kind of problem with your video card that will have to be worked around.  Do you know what kind of video device you have (be as specific as possible)?

---

### Post by Mister LinOx on 2009-04-20
> **pytheas22 said:**
> It looks fine to me, and if the integrity check passed, then you should definitely have a good copy.



This is using the same CD that you checked for errors previously, with no errors found?  If you wait a minute, does the desktop come up?  If not, it's possible that there's some kind of problem with your video card that will have to be worked around.  Do you know what kind of video device you have (be as specific as possible)?

Yes, it is the same disc I created this morning with zero scratches. It even happened this morning. 

The desktop does not come up even if I wait 30 minutes.

I don't know if my video card supports ubuntu, but I believe it is an Intel integrated chip set...

Ah. Here it is: Intel(R) 82845G/GL/GE/PE/GV Graphics Controller (Intel(R) 82845G Graphics Controller)

---

### Post by pytheas22 on 2009-04-20
Ah, according to this [bug report]("https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/281132"), your video card has some trouble in Ubuntu 8.10.  However, modifying the boot options is supposed to resolve the problem and allow you to use Ubuntu normally.

To change the boot options, boot to the live CD.  At the first screen, after selecting your language, press F6.  This will open a box where you can edit the boot options.  By default, they will look something like this:
```

initrd=/casper/initrd.gz quiet splash --
```

(Don't worry if they don't look exactly like that.)  You need to add these options:
```

noapic acpi=off nolapic
```

So simply type those options at the end of the boot line, so that the total line reads:
```

initrd=/casper/initrd.gz quiet splash -- noapic acpi=off nolapic
```

Then press enter to begin the boot.  If this does the trick and allows you to run Ubuntu normally, we can make the change permanent (for the time being, you will need to repeat this process each time you boot from the live CD).

---

### Post by Mister LinOx on 2009-04-20
> **pytheas22 said:**
> Ah, according to this [bug report]("https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/281132"), your video card has some trouble in Ubuntu 8.10.  However, modifying the boot options is supposed to resolve the problem and allow you to use Ubuntu normally.

To change the boot options, boot to the live CD.  At the first screen, after selecting your language, press F6.  This will open a box where you can edit the boot options.  By default, they will look something like this:
```

initrd=/casper/initrd.gz quiet splash --
```

(Don't worry if they don't look exactly like that.)  You need to add these options:
```

noapic acpi=off nolapic
```

So simply type those options at the end of the boot line, so that the total line reads:
```

initrd=/casper/initrd.gz quiet splash -- noapic acpi=off nolapic
```

Then press enter to begin the boot.  If this does the trick and allows you to run Ubuntu normally, we can make the change permanent (for the time being, you will need to repeat this process each time you boot from the live CD).

Okay. I'm going to write that down onto a post-it and get back to you in a moment.

---

### Post by Mister LinOx on 2009-04-20
Okay. I did what you said, booted it up, and it got past the old screen. Now, it continues on to a black command prompt like screen with multiple statements all ending with [OK].

Once it passes that, it goes to another dark purple screen, only this time it has to movable cursor. Just the screen. After a few seconds, it play a ding-like sound. About 10-20 seconds after that, it plays a short more orchestra-like sound. After that? Nothing. I waited about 10 minutes. So now we're on another problem. xP

By the way, I appreciate you trying to help me here.

---

### Post by pytheas22 on 2009-04-20
This sounds strange, but we can figure it out if we keep trying.

Please boot to the live CD again, adding the special options as you did before.  After it gets to the last screen, please do these things (in this order) and let me know what happens:

1. press control-alt-backspace
2. press control-alt-F2

Another (unlikely) possibility here is that for some reason your computer is trying to dump the video output to an external monitor.  On most laptops (assuming this is a laptop), there's a button or key-combination (like function+F12) that you press to toggle video output between the built-in and external monitors.  Please make sure that the system isn't trying to output only to an external monitor for some reason (I highly doubt that this is what's going on, but it's worth a check).

---

### Post by Mister LinOx on 2009-04-20
> **pytheas22 said:**
> This sounds strange, but we can figure it out if we keep trying.

Please boot to the live CD again, adding the special options as you did before.  After it gets to the last screen, please do these things (in this order) and let me know what happens:

1. press control-alt-backspace
2. press control-alt-F2

Another (unlikely) possibility here is that for some reason your computer is trying to dump the video output to an external monitor.  On most laptops (assuming this is a laptop), there's a button or key-combination (like function+F12) that you press to toggle video output between the built-in and external monitors.  Please make sure that the system isn't trying to output only to an external monitor for some reason (I highly doubt that this is what's going on, but it's worth a check).

That did not work. Same thing. Orchestra music at light background screen(very light-brown maybe? no picture or graphics), then dark purple screen. 

Oh, and, if it does matter, I am not on a laptop. I'm on an HP Pavilion a522n Desktop with some Dell monitor.

---

### Post by pytheas22 on 2009-04-20
Alright, please give this a try: at the white/brown screen, press control-alt-F2 (don't worry about passing the special boot options this time, since they don't seem to do anything).  This should bring you to a command prompt.  At the prompt, type:

```
sudo /etc/init.d/gdm stop
sudo nano /etc/X11/xorg.conf
```

At this point, a file will be open.  Scroll down using the arrow keys until you see a section that looks like this:

```
Section "Device"
	Identifier	"Configured Video Device"
EndSection

```

Add in a line so the section looks like:
```

Section "Device"
	Identifier	"Configured Video Device"
        **driver          vesa**
EndSection
```

Then press control-o to save the file, and control-x to exit.  Finally, type:
```

startx
```

Does this get you to a desktop?

Sorry your first taste of Ubuntu is proving so complicated--it's rarely this bad--and thanks for the patience.

---

### Post by Mister LinOx on 2009-04-20
> **pytheas22 said:**
> Alright, please give this a try: at the white/brown screen, press control-alt-F2 (don't worry about passing the special boot options this time, since they don't seem to do anything).  This should bring you to a command prompt.  At the prompt, type:

```
sudo /etc/init.d/gdm stop
sudo nano /etc/X11/xorg.conf
```

At this point, a file will be open.  Scroll down using the arrow keys until you see a section that looks like this:

```
Section "Device"
	Identifier	"Configured Video Device"
EndSection

```

Add in a line so the section looks like:
```

Section "Device"
	Identifier	"Configured Video Device"
        **driver          vesa**
EndSection
```

Then press control-o to save the file, and control-x to exit.  Finally, type:
```

startx
```

Does this get you to a desktop?

Sorry your first taste of Ubuntu is proving so complicated--it's rarely this bad--and thanks for the patience.

[s]Well, once I get to edit the file, there is nothing there in the file to edit. I've tried going to the next page and all of that, but there is still nothing there so I don't know where to go to find the peice of text to edit.

I've disable gnome like asked, now when I typed the next line you gave me to open the editor, it opens, but like I said above, it's just a blank control prompt-like text editor. 

Also, i typed /Xll/ for that one part in the line. Was it Xll or X11 or XII?[/s]

Should have looked a little closer.

Anyway, now I am finished editing the file, I believe, but now, after I've exited, when I type in startx, it gives me a long message saying some things about ubuntu, like version i think, then says fatal server error: no screens found.   near the bottom. Should I turn Gnome back on?

---

### Post by pytheas22 on 2009-04-20
Sorry that didn't help.  The next thing to try is to go into your BIOS and see if there's an option for giving more memory to the video card.  Some people in [this thread]("http://www.linuxquestions.org/questions/fedora-35/help-prob-w-fc6-install-xorg.conf-and-my-intel-82845g-graphics-card-514634/") say that this solved the problem for them using this graphics card.

Please let me know if you have an option in BIOS for allocating memory to video, and see if giving it the maximum amount allowed makes any difference.  If there are any other options related to video, please let me know what they are.

---

### Post by sharon.gmc on 2009-04-21
Thank you for posting this. It really helped me a lot.

---

### Post by Mister LinOx on 2009-04-21
> **pytheas22 said:**
> Sorry that didn't help.  The next thing to try is to go into your BIOS and see if there's an option for giving more memory to the video card.  Some people in [this thread]("http://www.linuxquestions.org/questions/fedora-35/help-prob-w-fc6-install-xorg.conf-and-my-intel-82845g-graphics-card-514634/") say that this solved the problem for them using this graphics card.

Please let me know if you have an option in BIOS for allocating memory to video, and see if giving it the maximum amount allowed makes any difference.  If there are any other options related to video, please let me know what they are.
Well, I tried, but the problem is that somehow there is a BIOS password protecting it. My grandmother MIGHT have set it, but I doubt it. I've been trying to find out how to reset it, but none works. 

Oh, and sharon.gmc, I'm glad it has helped you. Maybe, one day, I'll be lucky enough to log on ubuntu. xP

EDIT: Okay. I am in Ubuntu. Not in he normal mode, though. I tried Safe Graphics mode or something along those lines. 

Well, anyway, I was reading on some other forums about people having 82845G problems. So, I kept reading, and this one person fixed it by signing in as root, then typing: dhclient
then: apt-get upgrade
finally: reboot -n

Would this work?

---

### Post by pytheas22 on 2009-04-21
Glad you are at least now logged into Ubuntu.
> 
Well, anyway, I was reading on some other forums about people having 82845G problems. So, I kept reading, and this one person fixed it by signing in as root, then typing: dhclient
then: apt-get upgrade
finally: reboot -n

Those commands connect to the Internet (which should not be necessary because Ubuntu should already have connected you automatically), apply updates and reboot your computer (in that order).  If you're still running from the live CD, however, applying Ubuntu updates won't do much, because when you reboot they will all be lost.

At this point, I'd recommend that you go ahead and install Ubuntu to your hard disk while running in safe mode.  Once it's installed, we can work on fixing the system permanently.  Hopefully it will be as simple as applying updates.

---

### Post by Mister LinOx on 2009-04-21
> **pytheas22 said:**
> Glad you are at least now logged into Ubuntu.


Those commands connect to the Internet (which should not be necessary because Ubuntu should already have connected you automatically), apply updates and reboot your computer (in that order).  If you're still running from the live CD, however, applying Ubuntu updates won't do much, because when you reboot they will all be lost.

At this point, I'd recommend that you go ahead and install Ubuntu to your hard disk while running in safe mode.  Once it's installed, we can work on fixing the system permanently.  Hopefully it will be as simple as applying updates.

Okay. The only question I have about that(well, on the installation subject) is that I have no idea HOW to partition or how MUCH I should partition it. I believe I have about 145GB maximum on my hardrive and 134GB available. How much should I set the partition to? I'm on the live CD, and on the desktop, there's an installation icon. Do I press that and it gives me a slider or text area to input the partition?

---

### Post by pytheas22 on 2009-04-21
> Okay. The only question I have about that(well, on the installation subject) is that I have no idea HOW to partition or how MUCH I should partition it. I believe I have about 145GB maximum on my hardrive and 134GB available. How much should I set the partition to? I'm on the live CD, and on the desktop, there's an installation icon. Do I press that and it gives me a slider or text area to input the partition?

Yes, double-click the 'Install' icon and it will guide you through the process.  At the partitioning step, you can use a slider to tell the installer how much space to allocate to your new Ubuntu partition.  Alternatively, you can specify an exact amount of megabytes.

Your Ubuntu partition needs to be 3 gigabytes at the very minimum, but I would recommend at least 5.  The more the better.

Also, you should defragment in Windows, if you haven't already, in order to prevent problems trying to create the new partition.  And back up any important files just in case.

---

### Post by Mister LinOx on 2009-04-21
> **pytheas22 said:**
> Yes, double-click the 'Install' icon and it will guide you through the process.  At the partitioning step, you can use a slider to tell the installer how much space to allocate to your new Ubuntu partition.  Alternatively, you can specify an exact amount of megabytes.

Your Ubuntu partition needs to be 3 gigabytes at the very minimum, but I would recommend at least 5.  The more the better.

Also, you should defragment in Windows, if you haven't already, in order to prevent problems trying to create the new partition.  And back up any important files just in case.

Well, I defragged last night. It was looking pretty good, and I was barely on Windows doing anything so that should be okay. 

I was thinking about 6-10 GB. I'm wondering though, does the size of the partition limit what size programs I can download even if the free space is big?

---

### Post by pytheas22 on 2009-04-21
> 
I was thinking about 6-10 GB. I'm wondering though, does the size of the partition limit what size programs I can download even if the free space is big?

No, you can download files as large as you want so long as the file size isn't greater than your amount of free space.  10 gigabytes would allow you to install quite a few additional applications--and since Ubuntu comes by default with an office suite, web browser, etc. (all bundled into the initial 3 gigabytes that the system takes up), you will likely find that there's not much you need to add anyway.

---

### Post by Mister LinOx on 2009-04-21
> **pytheas22 said:**
> No, you can download files as large as you want so long as the file size isn't greater than your amount of free space.  10 gigabytes would allow you to install quite a few additional applications--and since Ubuntu comes by default with an office suite, web browser, etc. (all bundled into the initial 3 gigabytes that the system takes up), you will likely find that there's not much you need to add anyway.

Okay. Look at my attachment. I selected manual partition and I am bewildered(right word?) by this screen. Care to provide help? You seem to know exactly what to do. Hope I haven't been asking too much.

---

### Post by Godly on 2009-04-21
> **Mister LinOx said:**
> Oh, and another question. 
When I boot form the disc, I select English and I want to try to get on without bothering anything first. So when I select that option, it goes to the loading screen and after a minute or so, the screen changes to a bright screen, then back to a dark purple/black like screen with just the movable cursor visible. Know how to fix this?

Can you type on this screen?

---

### Post by Mister LinOx on 2009-04-21
> **Godly said:**
> Can you type on this screen?

Read the previous posts to understand what it is, please. =D

It's a dark purple screen with a cursor. No typing. It's a video card problem, I believe, because I'm in Ubuntu via Live CD via Safe Graphics boot.

---

### Post by pytheas22 on 2009-04-21
> 
Okay. Look at my attachment. I selected manual partition and I am bewildered(right word?) by this screen. Care to provide help? You seem to know exactly what to do. Hope I haven't been asking too much.

In the list, click on the entry for /dev/sda2.  Then click the button that says 'edit partition'.  That will open up a dialog where you can specify a size in megabytes that you want to shrink the partition to.

Alternatively, you should be able to shrink the partition by clicking the end of the green/orange tube and dragging your cursor to the left.

After you've instructed the installer to shrink the /dev/sda2 partition (which is your Windows one), click the entry in the list labeled 'free space', and then click the 'new partition' button.  You will want to create a partition formatted as ext3 with / as the mountpoint.  You should also leave a little room (500-1000 megabytes) of free space for creating a second partition, which will be formatted as swap and will not have a mountpoint.

---

### Post by Mister LinOx on 2009-04-21
> **pytheas22 said:**
> In the list, click on the entry for /dev/sda2.  Then click the button that says 'edit partition'.  That will open up a dialog where you can specify a size in megabytes that you want to shrink the partition to.

Alternatively, you should be able to shrink the partition by clicking the end of the green/orange tube and dragging your cursor to the left.

After you've instructed the installer to shrink the /dev/sda2 partition (which is your Windows one), click the entry in the list labeled 'free space', and then click the 'new partition' button.  You will want to create a partition formatted as ext3 with / as the mountpoint.  You should also leave a little room (500-1000 megabytes) of free space for creating a second partition, which will be formatted as swap and will not have a mountpoint.
Sort of like this?


Oh, and I tried installing earlier with just the swap and / partition, and when it got about 1 GB installed, it cut to a black screen with multiple strings(It's been awhile. The real name you'd say is on the tip of my finger)on different lines, each with [OK] after them, then the monitor switches off 6 times, and it cuts to a different screen saying the server crashed or system or something. So I just booted back to the CD to ask you guys and fix the partition a little.

---

### Post by pytheas22 on 2009-04-21
That partitioning scheme looks like it would work, but is there a reason why you were using gparted (the application at System>Administration>Partition Editor) to create it, rather than the partioner built into the installer?  Using the utility provided by the installer is a better way to go.

As for your screen failing halfway through the installation, that's strange.  You were still booted in failsafe graphics mode at that point, right?

---

### Post by Mister LinOx on 2009-04-21
> **pytheas22 said:**
> That partitioning scheme looks like it would work, but is there a reason why you were using gparted (the application at System>Administration>Partition Editor) to create it, rather than the partioner built into the installer?  Using the utility provided by the installer is a better way to go.

As for your screen failing halfway through the installation, that's strange.  You were still booted in failsafe graphics mode at that point, right?

I did it through the installation window this time and set it up just like earlier. It worked, and now it is permantly installed. I booted up regular mode, and it worked perfectly. I typed in my name and my pass, then I signed into my desktop. No problem.

I am now installing updates. 

Oh, the first time my uncle accidentally did something. No biggie.

Thank you for your help, and if you don't mind, may I PM you if anything else pops up? I really appreciate your three day support. MUCH better than any microsoft tech phone number. Hahaha.

---

### Post by pytheas22 on 2009-04-21
I'm glad you finally have it installed, and that it's working.  If you have any more questions related to this, it would actually be better if you could just post in this thread rather than send me a private message--it's easier to keep track of things that way, and it ensures that other people having the same problem can benefit from the discussion.  I'm subscribed to this thread, so I will receive a notice and check it whenever a new post is added.

---

