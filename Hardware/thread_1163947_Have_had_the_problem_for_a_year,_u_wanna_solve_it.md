---
title: "Have had the problem for a year, u wanna solve it?"
date: 2009-05-19
forum: Hardware
---

### Post by martuschka on 2009-05-19
Don't have correct screen resolution, my graphics are poor, although they should be good. Nothing comes up under hardware drives.

Previously i had the harddisk connected through usb to my laptop (was not working then either. But now its in my pc. I have a HP w 2408h 24 monitor 1920x1200. But the resolution shows as 800x600 AND IS NOT CHANGEABLE from the menu :(


horus@horus-laptop:~$ sudo lshw -C display
  *-display UNCLAIMED     
       description: VGA compatible controller
       product: 82915G/GV/910GL Integrated Graphics Controller
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 04
       width: 32 bits
       clock: 33MHz
       capabilities: pm vga_controller bus_master cap_list
       configuration: latency=0


Someone in another thread mentioned a package might be missing from my system. [http://ubuntuforums.org/showthread.php?t=1051276&page=2](http://ubuntuforums.org/showthread.php?t=1051276&page=2)

Would be great if anyone could help me out here, the one who does it gets a cookie ;)

Thanks in advance

---

### Post by b@sh_n3rd on 2009-05-19
Hi, I've the Intel 82845 and have a few similar probs but was able to solve em. But in my case, I've an older card and I'm using Jaunty...which version of Ubuntu are you using? 

Try *[this]("http://ubuntuforums.org/showthread.php?t=1130582")* thread...It's for Jaunty...But it *might* help...

---

### Post by martuschka on 2009-05-19
Well i have been thinking about updating my version. But i dont want any of my files to dissapear. And i want desktop to look the same.
Can i do the upgrade in the upgrade manager or synaptic in some way?

---

### Post by b@sh_n3rd on 2009-05-19
The only way *I* know on how to upgrade is to hit "ALT+F2" and type, "update-manager -d"... On top of the update manager it'd say, "New distribution release '9.04' available" followed by an "Upgrade" button...click that button to upgrade but make sure your system is fully "updated"...
Only thing I hate about this is that it takes quite some time...

---

### Post by kpkeerthi on 2009-05-19
Upgrade using the Alternate CD ISO. It much faster than online upgrade.

[http://www.ubuntu.com/getubuntu/upgrading#Upgrading%20Using%20the%20Alternate%20CD/DVD]("http://www.ubuntu.com/getubuntu/upgrading#Upgrading%20Using%20the%20Alternate%20CD/DVD")

---

### Post by timcredible on 2009-05-19
i would recommend NOT doing an upgrade.  backing up your data and reinstalling is usually better.  as for the graphics card, you can check to see if 9.04 runs it better by just booting the livecd, if it doesn't look any better, no reason to upgrade, but if it runs the graphics card properly, do a backup and re-install.

---

### Post by martuschka on 2009-05-19
> **timcredible said:**
> i would recommend NOT doing an upgrade.  backing up your data and reinstalling is usually better.  as for the graphics card, you can check to see if 9.04 runs it better by just booting the livecd, if it doesn't look any better, no reason to upgrade, but if it runs the graphics card properly, do a backup and re-install.


How do i reinstall 8.04? Without loosing all my files in home folder?
Will it delete everything from it?

---

### Post by b@sh_n3rd on 2009-05-19
> **kpkeerthi said:**
> Upgrade using the Alternate CD ISO. It much faster than online upgrade.

[http://www.ubuntu.com/getubuntu/upgrading#Upgrading%20Using%20the%20Alternate%20CD/DVD](http://www.ubuntu.com/getubuntu/upgrading#Upgrading%20Using%20the%20Alternate%20CD/DVD)

Hey cool...I was wondering if something like this was possible...

> **timcredible said:**
> i would recommend NOT doing an upgrade. backing up your data and reinstalling is usually better. as for the graphics card, you can check to see if 9.04 runs it better by just booting the livecd, if it doesn't look any better, no reason to upgrade, but if it runs the graphics card properly, do a backup and re-install.

Even *I *like this method. I did the same but didn't mention re-installation coz of the OP's data...The i915 should run better on Jaunty than on other distro's with a little bit of work...okay, not a *little* but the results thereafter are worth it... I mean, I'm running Jaunty at 100% after resolving the *same *issues the OP *might* witness in Jaunty...

martuschka, I think it's always best if we install Ubuntu into a separate "/home" partition...I do it all the time now after several "data loss" re-installs...spitty...but then again, luckily for me nothing important...:D. This partitioning mechanism is the greatest advantage with Ubuntu/Linux over winblows, *I* think...

---

### Post by martuschka on 2009-05-19
> **b@sh_n3rd said:**
> Hey cool...I was wondering if something like this was possible...



Even *I *like this method. I did the same but didn't mention re-installation coz of the OP's data...The i915 should run better on Jaunty than on other distro's with a little bit of work...okay, not a *little* but the results thereafter are worth it... I mean, I'm running Jaunty at 100% after resolving the *same *issues the OP *might* witness in Jaunty...

martuschka, I think it's always best if we install Ubuntu into a separate "/home" partition...I do it all the time now after several "data loss" re-installs...spitty...but then again, luckily for me nothing important...:D. This partitioning mechanism is the greatest advantage with Ubuntu/Linux over winblows, *I* think...

Mkay, yeah i know, i LOVE ubuntu...
EVEN with a crappy 600x800 resolution where i cant see s*it.
I downloaded that iso file.
But since i am a ubuntu retard i am worried i wont know how to put it on a separate /home partition...

I had someone at work help me partition this version, however i dont work there anymore. If you could give me a hand with this it would be very appreciated. Oh and winblows (lol)

Cheers

---

### Post by martuschka on 2009-05-19
> **b@sh_n3rd said:**
> Hi, I've the Intel 82845 and have a few similar probs but was able to solve em. But in my case, I've an older card and I'm using Jaunty...which version of Ubuntu are you using? 

Try *[this]("http://ubuntuforums.org/showthread.php?t=1130582")* thread...It's for Jaunty...But it *might* help...

B@sh, your the best, it worked !!
But i got another problem now ;)
The graphics are VERY poor...Frames per second...im guessing 2 :)

But resolution is back...
I have lost the "frames" around my window though..so i have to go to file and then close. if i want to close a window...


Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"se"
	Option		"XkbOptions"	"pc105"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
EndSection

Section "Device"
	Identifier	"Configured Video Device"
	Option		"AccelMethod"			"uxa"
	Option		"EXAOptimizeMigration"		"true"
	Option		"MigrationHeuristic"		"greedy"
	Option		"Tiling"			"true" 
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
EndSection

So any ideas on what to do now to get my graphics proper?

Cheers

---

### Post by b@sh_n3rd on 2009-05-20
> B@sh, your the best, it worked !! hehe, thanks...if only all these, "so-called-normal" ppl thought that...:D

Anyways...your xorg.conf is strange...I don't really know much about it but on my one, all *I* changed was the "Device" section...what method did you use from the thread? For you, I think "Safe" or "Optimal" oghta be fine...I started with optimal but now am using "Bleeding Edge", which is kinda risky (It's just the RC kernel actually), but works perfect on my system...Here's my xorg.conf for comparison...

```
Section "Device"
        Identifier      "Configured Video Device"
        Driver          "intel"
        BusId           "PCI:0:2"
        Option          "AccelMethod"                   "uxa"
        Option          "EXAOptimizeMigration"          "true"
        Option          "MigrationHeuristic"            "greedy"
        Option          "Tiling"                        "false"
EndSection

Section "Monitor"
        Identifier      "Configured Monitor"
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Monitor         "Configured Monitor"
        Device          "Configured Video Device"

```What you can do is this, I think you'd better backup your xorg.conf by running, ```
 cp /etc/X11/xorg.conf /etc/X11/xorg.conf.bak
```(I say, "xorg.conf.bak", just in case you've already got an, "xorg.conf.old"...but it's quite descriptive) Then, try running ```
sudo dpkg-reconfigure -phigh xserver-xorg
``` As you might know, this command resets your xorg.conf file to the default, so do it *only* if you *wanna*...It definitely *should* work without any probs though...Now after this, try what's mentioned in that thread from the top...I suggest you start with "Safe", then you can try "Optimal" (If you *want*) which really kicks all those silly bugs away...:D

I suppose, If you've already installed anything that's mentioned under "Safe", I don't think you'll need to do so again...

---

### Post by martuschka on 2009-05-20
> **b@sh_n3rd said:**
> hehe, thanks...if only all these, "so-called-normal" ppl thought that...:D

Anyways...your xorg.conf is strange...I don't really know much about it but on my one, all *I* changed was the "Device" section...what method did you use from the thread? For you, I think "Safe" or "Optimal" oghta be fine...I started with optimal but now am using "Bleeding Edge", which is kinda risky (It's just the RC kernel actually), but works perfect on my system...Here's my xorg.conf for comparison...

```
Section "Device"
        Identifier      "Configured Video Device"
        Driver          "intel"
        BusId           "PCI:0:2"
        Option          "AccelMethod"                   "uxa"
        Option          "EXAOptimizeMigration"          "true"
        Option          "MigrationHeuristic"            "greedy"
        Option          "Tiling"                        "false"
EndSection

Section "Monitor"
        Identifier      "Configured Monitor"
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Monitor         "Configured Monitor"
        Device          "Configured Video Device"

```What you can do is this, I think you'd better backup your xorg.conf by running, ```
 cp /etc/X11/xorg.conf /etc/X11/xorg.conf.bak
```(I say, "xorg.conf.bak", just in case you've already got an, "xorg.conf.old"...but it's quite descriptive) Then, try running ```
sudo dpkg-reconfigure -phigh xserver-xorg
``` As you might know, this command resets your xorg.conf file to the default, so do it *only* if you *wanna*...It definitely *should* work without any probs though...Now after this, try what's mentioned in that thread from the top...I suggest you start with "Safe", then you can try "Optimal" (If you *want*) which really kicks all those silly bugs away...:D

I suppose, If you've already installed anything that's mentioned under "Safe", I don't think you'll need to do so again...



Ok i also started with the optimal, but then i got the weird graphics problem..Then tried the bleeding edge but nothing really changed.
I am worried I´ll loose my files from the home folder if something happends now..If i backup the home folder and reinstall my version where should i put the backup? So it wont dissapear?

---

### Post by b@sh_n3rd on 2009-05-20
For bleeding edge, I don't think the difference would be noticable at once coz, the kernel is the main difference...Umm...this *is* a problem

This is what I'd have done *IF* I was reinstalling Jaunty on my PC (I did do something similar recently),

Start my PC from the LiveCD (Not the "Install" option), copy the "home" folder from the "root" partiton onto the Desktop or a Flashdrive, delete the remaining partitions using "GParted" then create a 100MiB partition for "/boot", 386MiB for "swap", 6-7GiB for "/home" and use the remaining for "/"...(This is my partitioning method on a 20GB HDD) then copy the "home" files onto the separate home partition I created...After that, install Jaunty and select "Manual" in the "Partitioning" section...Here, I have to select the "Mount Point"s for the created partitions...This may seem like a lot of gibberish but even *I* got the hang of it some time ago...(Ubuntu's what made me a *real* comp nerd actually...:D)

How big is *your* drive? I could tell you a proper partition table for that on Jaunty if you want...
I suppose, the fix wouldn't have worked as it should have, coz it's meant for Jaunty...

---

### Post by martuschka on 2009-05-20
> **b@sh_n3rd said:**
> For bleeding edge, I don't think the difference would be noticable at once coz, the kernel is the main difference...Umm...this *is* a problem

This is what I'd have done *IF* I was reinstalling Jaunty on my PC (I did do something similar recently),

Start my PC from the LiveCD (Not the "Install" option), copy the "home" folder from the "root" partiton onto the Desktop or a Flashdrive, delete the remaining partitions using "GParted" then create a 100MiB partition for "/boot", 386MiB for "swap", 6-7GiB for "/home" and use the remaining for "/"...(This is my partitioning method on a 20GB HDD) then copy the "home" files onto the separate home partition I created...After that, install Jaunty and select "Manual" in the "Partitioning" section...Here, I have to select the "Mount Point"s for the created partitions...This may seem like a lot of gibberish but even *I* got the hang of it some time ago...(Ubuntu's what made me a *real* comp nerd actually...:D)

How big is *your* drive? I could tell you a proper partition table for that on Jaunty if you want...
I suppose, the fix wouldn't have worked as it should have, coz it's meant for Jaunty...

Ok Gosh, since i am a noob, i am a bit worried, but if i follow your directions i should be alright, right? :)
I just dont want to loose my files.

I have 500 gb.

If there's any more information you need B@sh please let me know.
Your life is now in my hands..lol

Cheers

---

### Post by b@sh_n3rd on 2009-05-20
> Your life is now in my hands you mean the other way around right?? :D..now that's funny...umm...500GB...cool..a dream HDD but I wouldn't need so much space...

Do you have a good flash drive with alot of space? That'd be the easiest method for a backup...All you have to backup is your home folder and that would be err...several GB depending on what you've got in there...vids and music take alot of space which is the case on my PC..

Assuming you have a Flashdrive and your home folder can fit in there,
plug in your flashdrive onto your pc and just _***copy***_ the "home" folder through nautilus

To find out how big your home dir is, Right-click your "home" folder in nautilus and click properties, ahead of "Contents:" it'd say something like, "xxx items, totalling xxx GB" For example, My one says, "Contents: 2, 748 items, totalling 1.1GB"...If you don't have a big enough flashdrive or none at all, we'll have to use your hdd...(I hate this part! too cumbersome)

If you don't have one, I need to see your PC's partition table,

What you could do is, go to, "Add/Remove" and install "Partition Editor"...(thats GParted), launch it from, "System > Administration > Partition Editor" and after it loads grab a screenshot...attach that here and I'll err...simulate what to do next...I'm scared myself...Mind, don't mess around with GParted, only take the screenshot...

---

### Post by albinootje on 2009-05-20
> **martuschka said:**
> 
I just dont want to loose my files.


It's a good idea to make backups to an external usb drive. 
After doing that, you're ready to create a separate /home partition. 

See here to create a separate /home partition :
[http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)

And why don't you run a "live session" with an Ubuntu Jaunty desktop installation cdrom or usb stick ?
Jaunty has some performance problems for 3D graphics on Intel and ATI video cards, but it also has better video setting option.

A few days ago I let a colleague play with the display settings in Jaunty on his laptop (Instead of Gutsy or Hardy), and for the first time he could easily configure settings for an external monitor.

---

### Post by b@sh_n3rd on 2009-05-20
Yeah, there's a problem with Intel...BUT, there's a fix...with that, I can run my fav screensavers and even AWN!! :D

---

### Post by martuschka on 2009-05-25
Sorry i have been busy with my exams.
Now i am back (hopefully passed).

I still have the graphics problem..I have the right resolution but no contact with the graphics card.

(B@sh, we were talking about a reinstall, i don't have an extra memory, couse i use that as my hard drive..(Does it make sense)..I used to boot Ubuntu from my laptop and used that memory stick thing...
Its gonna take me a while to get some money for one...(being a poor student). 

Thanks so much in advance.

---

### Post by b@sh_n3rd on 2009-05-26
> **martuschka said:**
> Sorry i have been busy with my exams.
Now i am back (hopefully passed).

I still have the graphics problem..I have the right resolution but no contact with the graphics card.

(B@sh, we were talking about a reinstall, i don't have an extra memory, couse i use that as my hard drive..(Does it make sense)..I used to boot Ubuntu from my laptop and used that memory stick thing...
Its gonna take me a while to get some money for one...(being a poor student). 

Thanks so much in advance.

Hi, the memory stick was just an emergency door like to make it easier for you to reinstall Ubuntu. it's not really necessary. Reinstalling is not a prob in this case, but holding your data until the install is finished, and placing it in your /home dir thereafter.

---

