---
title: "Suspend/resume issues"
date: 2009-11-19
forum: Hardware
---

### Post by xeno_phile on 2009-11-19
I am posting this because the 64bit support forum has been closed down and the long active thread can no longer be added too!!!

If your problem with Suspend/hibernate & resume has not be solved yet, post your details here....together we will find an answer.

As an update, i have tried Linux-mint 8 (distro built on Ubuntu 9.10) and suspend/resume is broken on that one as well....it does partially resume, in that the image is returned (somewhat dimmed) and the mouse is active, but no interaction with the screen image is possible.

Slax v6.1.2 suspends and resumes correctly.

Have just updated to kernel 2.6.31-15 via "karmic-proposed" but this hasn't solved the problem.

xeno_phile

**note to moderators, if you feel this is not the right sub-forum for this thread, please feel free to move it to a forum that is more appropriate for this subject.

---

### Post by ROY.G.BIV on 2009-11-19
Suspend doesn't work for me in 9.04. Whenever I click "suspend" it has the same effect as shutdown.

---

### Post by xeno_phile on 2009-11-19
> **ROY.G.BIV said:**
> Suspend doesn't work for me in 9.04. Whenever I click "suspend" it has the same effect as shutdown.
Is 9.04 your first Ubuntu experience, or did suspend cease working correctly after upgrading from a previous release?

xeno_phile

---

### Post by xeno_phile on 2009-11-19
I have posted a similar inquiry on the Linux-Mint forum....
_[http://forums.linuxmint.com/viewtopic.php?f=49&t=36142](http://forums.linuxmint.com/viewtopic.php?f=49&t=36142)_
Don't know if it will get any response, but i think it is worth trying.

xeno_phile

---

### Post by lamaistres on 2009-11-19
I have a Presario v2000 laptop. My graphic chip is a radeon xpress 200m 5955 igp. So far, downgrading -ati and -radeon video packages has fixed my suspend and hibernate blank screen problem. I thought I would repost everything I have because the 64-bit forum was shutdown and my post was incomplete, so I hope you don't mind. I have tested this on the default 2.6.31-14 kernel and the latest ppa-mainline-rc7 kernel.

The name of the packages that I installed are;
xserver-xorg-video-radeon_6.12.1-0ubuntu2
xserver-xorg-video-ati_6.12.1-0ubuntu2

Here are the links for the two deb packages in launchpad. Download the package that fit your archetecture, ie. amd64, i386, ia64.

[https://launchpad.net/ubuntu/jaunty/+package/xserver-xorg-video-radeon]("https://launchpad.net/ubuntu/jaunty/+package/xserver-xorg-video-radeon")
[https://launchpad.net/ubuntu/jaunty/+package/xserver-xorg-video-ati]("https://launchpad.net/ubuntu/jaunty/+package/xserver-xorg-video-ati")

Remove the current packages from karmic.
sudo apt-get remove xserver-xorg-video-radeon
sudo apt-get remove xserver-xorg-video-ati

And then, install the downloaded jaunty packages;
sudo dpkg -i xserver-xorg-video-radeon
sudo dpkg -i xserver-xorg-video-ati

Reboot the computer.

Now, if this doesn't work, simply reinstall the default packages;
sudo apt-get remove xserver-xorg-video-radeon
sudo apt-get remove xserver-xorg-video-ati
sudo apt-get install xserver-xorg-video-radeon
sudo apt-get install xserver-xorg-video-ati

To lock the packages, open system > administration > synaptic package manager and search for these two packages, then highlight the package and go to "package" in the toolbar and click "lock version". Only do this if you know it works. Afterwords, the packages should not update with update manager.

Also if you use apt frequently like I do, then pinning these packages will prevent them from installing when upgrading your laptop. Edit or create the file "/etc/apt/preferences" and add the following;

> Package: xserver-xorg-video-radeon
Pin: version 1:6.12.1-0ubuntu2
Pin-Priority: 1000

Package: xserver-xorg-video-ati
Pin: version 1:6.12.1-0ubuntu2
Pin-Priority: 1000

That should prevent these package from being upgraded to versions from karmic.

This is everything I did to get suspend and hibernate to work with my radeon 200m graphic chip. I hope this information is helpful or useful.

---

### Post by xeno_phile on 2009-11-19
Thank you for getting in touch **lamaistres,** i was just going to post an appeal for you to give some more details of your success. 
I will read your post and see what happens with my laptop.

Praying to god and trusting to luck....

xeno_phile

---

### Post by xeno_phile on 2009-11-19
**lamaistres**...i have followed your instructions and i can confirm that Suspend/Hibernate and then Resume seem to function correctly. I have done various suspends and hibernates with some reboots and all seems to be well, apart from one small problem.....my screen will not resume to full brightness...it's about 50% reduced from normal.
You have paved the the way to a full solution, and for that, i thank you greatly.

xeno_phile

---

### Post by xeno_phile on 2009-11-19
Update..
I updated the two packages via synaptic and suspend/hibernate/resume were broken again.
**Lamaistres **has hit upon a solution, all i have to do is sort out my reduced brightness problem.....any suggestions?

xeno_phile

---

### Post by xeno_phile on 2009-11-20
Dimmed screen is now solved.
I opened "Power Manager" and clicked on the "brightness" slide and it just returned to normal!!
Just did a suspend part way through writing this and everything comes back the way it should.....FANTASTIC.
Thank you lamaistras.

xeno_phile

---

### Post by cutterjohn on 2009-11-20
I had problems with 9.04 and suspend/resume however that appeared to have been caused by using proprietary catalyst drivers AND having beryl/compiz (Desktop Effects) enabled.  Disabling compiz (via Desktop Effects pref panel) allowed it to suspend/resume normally.  [EDIT] By failing to function properly what I really mean is that oh yes it would suspend, but it would NEVER resume properly as though the video driver was never getting properly re-initialized/started again. [/EDIT]

At some point since last spring something changed that on my machine it now suspends/resumes with compiz enabled, but that may NOT be the case for you.

Intel P8600/4GB/4850 Mobility Radeon 512MB GDDR3
Ubuntu 9.10 x86-64
catalyst 9.11 (now, but IIRC suspend/resume + compiz started working around 9.08 or 9.09 for me)

Side note:  I ended up disabling compiz again anyways, as I found the more recent versions effects to be more annoying the useful/attractive(?).

OTOH now, when I reume from suspend I've been having MASSIVE thrashing, going from 0MB of vm used to 500MB or so on next resume and so on, until the entire system almost entirely fills vm -> incredibly sluggish -> reboot.  This problem has been around for a while now, IIRC even before I upgraded to 9.10 so it may be yet another catalyst related thing or something that catalyst is triggering as a side-effect.

---

### Post by xeno_phile on 2009-11-20
[SIZE=2]**cutterjohn**[/SIZE]...
When i launch Catalyst Control Center i get this message.... 

> 
                                              [SIZE=2]** Initialization error**[/SIZE]

There was a problem initializing Catalyst Control Center Linux edition. It could be caused by the following.

No ATI graphics driver is installed, or the ATI driver is not functioning properly.
Please install the ATI driver appropriate for your ATI hardware, or configure using aticonfig.
I am loath to mess with the drivers on my laptop, the ATI/Radeon stuff is a nightmare.
If there is a possible conflict with the ATI driver and the rest of the system i think i will live without it!!

Perhaps you need to follow the advice given by lamaistres but go back to the distro before Jaunty!?

---

### Post by cutterjohn on 2009-11-20
```
6072 pqrstuv    20   0 4301m 2.4g 1968 S    0 62.0   5:36.71 pulseaudio
```Notice anything odd here?  I think that I found what's causing that sucking sound as far as my memory usage goes... oh 4301 is vm, 2.4g is resident, 1968 is shared memory usages

Looks like catalyst/ATI is not the only problem child...

Anyways AFA ATI stuff goes,
If it's less than R600 based GPU (IIRC) you have to use catalyst 9.3 or less which doesn't support the X.org in Ubuntu 9.10 -> have to use Ubuntu 9.04 or lower
If it's newer(3XXX and above I believe) you need catalyst 9.10 or newer to support X.org 1.6 + kernel 2.6.29(?) and higher -> can use Ubuntu 9.10
[EDIT2] OR (if it's and R500 or older base video card/GPU)
If you really want Ubuntu 9.10 you CAN use the OSS radeon driver instead of catalyst.  Not sure hwo good it's 3D support is for older chips though, as it's almost non-existent for R600 and newer...

AMD seems to e pushing hard for their OSS driver and it sounds like they'd prefer home consumer, i.e. non-workstation users to use it over catalyst when the OSS driver is ready for use.  Comments I read several months ago mentioned something about a year before 3D was decent for R600 and newer GPUs, but, presumably, 3D support for older GPUs is a bit better already...
[/EDIT2]


So, he's right, you're stuck going back to an older version of Ubuntu or living with the OSS driver.

[EDIT=much later]
Ah! Hah! Found a bug filed about pulseaudio chewing through memory, [https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/424655](https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/424655)
in case anyone else is/was interested in it...
[/EDIT]

---

### Post by elatre on 2009-11-20
It works! Thank you!

---

### Post by bizzy123 on 2009-11-21
I just followed lamaistres instructions for downgrading Radeon on the previous page and everything now works fine on my HP Compaq nc6000 laptop.

Thanks to all for figuring this out!

:)

---

### Post by Zaphod69 on 2009-11-22
Hi,

I installed Ubuntu 9.10 on my Toshiba M70 with an ATI Radeon chipset.

If I unplug the laptop it goes immediately into suspend - and will not wake up, it's a full power off reboot.

If I tell it to suspend - same thing - black screen, not even a flashing cursor.

I've tried to do what [lamaistres]("http://ubuntuforums.org/member.php?u=61667") suggested but it made no difference.

Have not tried hibernate as I rarely do this. 

Any help would be appreciated.

TIA

Zaph

---

### Post by ikdot on 2009-11-23
> **lamaistres said:**
> I have a Presario v2000 laptop. My graphic chip is a radeon xpress 200m 5955 igp. So far, downgrading -ati and -radeon video packages has fixed my suspend and hibernate blank screen problem. I thought I would repost everything I have because the 64-bit forum was shutdown and my post was incomplete, so I hope you don't mind. I have tested this on the default 2.6.31-14 kernel and the latest ppa-mainline-rc7 kernel.

The name of the packages that I installed are;
xserver-xorg-video-radeon_6.12.1-0ubuntu2
xserver-xorg-video-ati_6.12.1-0ubuntu2

Here are the links for the two deb packages in launchpad. Download the package that fit your archetecture, ie. amd64, i386, ia64.

[https://launchpad.net/ubuntu/jaunty/+package/xserver-xorg-video-radeon](https://launchpad.net/ubuntu/jaunty/+package/xserver-xorg-video-radeon)
[https://launchpad.net/ubuntu/jaunty/+package/xserver-xorg-video-ati](https://launchpad.net/ubuntu/jaunty/+package/xserver-xorg-video-ati)

Remove the current packages from karmic.
sudo apt-get remove xserver-xorg-video-radeon
sudo apt-get remove xserver-xorg-video-ati

And then, install the downloaded jaunty packages;
sudo dpkg -i xserver-xorg-video-radeon
sudo dpkg -i xserver-xorg-video-ati

Reboot the computer.

Now, if this doesn't work, simply reinstall the default packages;
sudo apt-get remove xserver-xorg-video-radeon
sudo apt-get remove xserver-xorg-video-ati
sudo apt-get install xserver-xorg-video-radeon
sudo apt-get install xserver-xorg-video-ati

To lock the packages, open system > administration > synaptic package manager and search for these two packages, then highlight the package and go to "package" in the toolbar and click "lock version". Only do this if you know it works. Afterwords, the packages should not update with update manager.

Also if you use apt frequently like I do, then pinning these packages will prevent them from installing when upgrading your laptop. Edit or create the file "/etc/apt/preferences" and add the following;



That should prevent these package from being upgraded to versions from karmic.

This is everything I did to get suspend and hibernate to work with my radeon 200m graphic chip. I hope this information is helpful or useful.

thank you sir! works perfectly

---

### Post by ethos_dacapo on 2009-11-23
Ok, this is where it gets confusing. I'm running an acer aspire zg5. I searched for installed xserver-xorg-video- packages and found both ati and radeon as well as many others installed. Why would i have them all installed, i should only need one of them, right? I'm guessing i should only need the intel driver but am hesitant to remove any until i know for sure. Any help would be appreciated....

---

### Post by ikdot on 2009-11-27
> **ethos_dacapo said:**
> Ok, this is where it gets confusing. I'm running an acer aspire zg5. I searched for installed xserver-xorg-video- packages and found both ati and radeon as well as many others installed. Why would i have them all installed, i should only need one of them, right? I'm guessing i should only need the intel driver but am hesitant to remove any until i know for sure. Any help would be appreciated....

first of all, sorry for the late reply.
the other xserver-xorg-... packages are there for other video devices. don't worry about them, they don't screw up anything on your system.

the two packages we're talking about are the ones that are relevant. apparently, we need the older ones (the ones you can download from launchpad).

it is safe to go ahead and remove/replace the 2 packages. your laptop should suspend/resume properly after reboot. 

if you feel safe to have an easy way back to the current status of your system, skip this part:

> To lock the packages, open system > administration > synaptic package manager and search for these two packages, then highlight the package and go to "package" in the toolbar and click "lock version". Only do this if you know it works. Afterwords, the packages should not update with update manager.

if something goes wrong (it really shouldn't) you can execute the following commands, which will reinstall the original packages:

sudo apt-get update
sudo apt-get dist-upgrade

by locking the packages (described above), you tell apt to ignore the newer versions. it's safe to run the old versions of these drivers. if you don't lock them, apt will install the current versions, which do not work.

i hope this helps.

---

### Post by ethos_dacapo on 2009-11-27
Doesn't work for me probably because like i mentioned before i'm running a acer aspire zg5 which uses intel not ati or radeon. I tried installing the jaunty intel package and it broke my system. Anymore ideas?

---

### Post by ikdot on 2009-11-29
> **ethos_dacapo said:**
> Doesn't work for me probably because like i mentioned before i'm running a acer aspire zg5 which uses intel not ati or radeon. I tried installing the jaunty intel package and it broke my system. Anymore ideas?

this seems to be a common issue in the kernel. the new fedora release is affected too and they propose this workaround:

> Due to a known bug, on some laptops with Intel video adapters, if the display goes into sleep mode with the laptop lid closed, it will not be reactivated when the laptop lid is opened. The display will stay blank unless you reboot or use the following workaround. To workaround this problem, create a file with the following contents: 
 ```
#!/bin/bash
xrandr --output LVDS1 --off
xrandr --output LVDS1 --auto
``` and save it as ~/screenfix.sh. Make it executable, and assign it to a keyboard shortcut (the method for doing this depends on your desktop environment). Executing this script via the keyboard shortcut should bring the display back to life. Note that the output parameter may vary; you can see the appropriate value for your system by running xrandr at a console and examining the output. A fix for this issue has been committed to the upstream kernel and may be made available in a future Fedora 12 kernel update. 
[https://fedoraproject.org/wiki/Common_F12_bugs#Display_cannot_be_reactivated_if_it_enters_sleep_mode_with_laptop_lid_closed](https://fedoraproject.org/wiki/Common_F12_bugs#Display_cannot_be_reactivated_if_it_enters_sleep_mode_with_laptop_lid_closed)

EDIT: I haven't tried it

---

### Post by ethos_dacapo on 2009-11-29
Thanks for the workaround. I tried it and it does indeed bring the screen back to life. I also noticed after installing the jaunty packages it didn't fix the suspend/resume problem with the screen but it did fix the problem i was having of not being able to leave the lid open without the screen going to sleep even with all the settings set to "do nothing." 

I'm glad we were finally able to find a decent workaround for this issue!


*After restarting my screen is going to sleep again. I've restarted several times now and for some reason its back to the same old issue. I can use the workaround to bring the screen back to life but there are issues with that too. Once i use the workaround to bring the screen back it moves everything to the same workspace everything has to be minimised before it will respond properly. I can't minimise things like the clock so it remains stuck until restarting x. I hope they update the kernel again and get this stuff all worked out.

---

### Post by ikdot on 2009-12-01
> **ethos_dacapo said:**
> Thanks for the workaround. I tried it and it does indeed bring the screen back to life. I also noticed after installing the jaunty packages it didn't fix the suspend/resume problem with the screen but it did fix the problem i was having of not being able to leave the lid open without the screen going to sleep even with all the settings set to "do nothing." 

I'm glad we were finally able to find a decent workaround for this issue!


*After restarting my screen is going to sleep again. I've restarted several times now and for some reason its back to the same old issue. I can use the workaround to bring the screen back to life but there are issues with that too. Once i use the workaround to bring the screen back it moves everything to the same workspace everything has to be minimised before it will respond properly. I can't minimise things like the clock so it remains stuck until restarting x. I hope they update the kernel again and get this stuff all worked out.

well, sorry to hear that. but at least it "kinda works" now. anyways, i'm sure that there'll be a kernel update as several distros seem to be affected.

---

### Post by Exüberance on 2009-12-01
I'm using 64-bit Ubuntu 9.1 on an HP Pavilion dv7 laptop with an NVidia GeForce 9200M graphics card.

If I have the laptop set to go into standby when I close the lid, when I resume I get a black screen with my cursor. Restarting X using RAlt + PrintScrn + K just drops me back to the shell terminal and I get an infinite loop of 3 different errors and am unable to type anything. Using Ctrl+Alt+F[1..6] gives the same loop of errors. I have to hold down the power button to restart.

[s]If I choose "suspend" from the menu on my taskbar, when I restart I see a terminal for a second then the monitor turns off and won't turn back on. I haven't tried restarting the X server yet, but I assume either the monitor won't turn on or the same thing will happen with errors, but I haven't tried that yet.[/s]
EDIT: Nevermind. They appear to be doing the same thing now.

I've tried a few suggestions from this thread in the 64-bit forum, but they either didn't do anything or just changed which of the 2 errors I would get.

Typing **sudo pm-suspend --quirk-s3-bios --quirk-s3-mode --quirk-dpms-on --quirk-vbe-post --quirk-vbestate-restore **into the terminal gave... intersting ... results. The computer started up without a taskbar, I couldn't open any programs other than the terminal window which was already open, 99% of commands no longer worked (for example typing **sudo reboot** gave a message saying there's no program called sudo in this directory <_< *facepalm*). Hitting the power button to bring up the menu to shutdown, came up, but with all text replaced with boxes as if the font couldn't be loaded. None of the options actually did anything. Hitting Ctrl+Alt+F1 gave an infinite loop of errors, but different ones than I normally get. I didn't think to restart X, but I doubt that would work.

Simply typing **sudo pm-suspend** also does basically the same thing. The only difference is that the taskbar is there, but dissapears as soon as I mouse over it.

I previously got it to start up with the monitor off (or at least the backlight off, I don't remember exacetly) by using certain arguments to pm-suspend, but I don't remember what they are now or even if the result will be consistent.

All I know is that currently, suspend = set sail for epic fail

---

### Post by jdunn on 2009-12-01
> **xeno_phile said:**
> Dimmed screen is now solved.
I opened "Power Manager" and clicked on the "brightness" slide and it just returned to normal!!
Just did a suspend part way through writing this and everything comes back the way it should.....FANTASTIC.
Thank you lamaistras.

xeno_phile

I have the same problem with brightness on resume.  Changing the brightness level only fixes the problem until the next time you shutdown/reboot.  Does anyone know how to fix this?

---

### Post by acerqueti on 2009-12-02
I have a Dell Inspiron 510m. I've been using it with a Dell Docking station, happily running Ubuntu 9.10. After some upgrades and a 'dist-upgrade' this morning, it's stopped working with the Docking Station...

Figured out it's due to the screen being closed. Pressing the "screen close" switch as if the lid was closing causes the machine to completely freeze (screen freezes, no access via VNC/SSH, no response to keys).

I'm assuming this is all related to the new updates.
Display adaptor is Intel 855GM - driver auto-updated to xserver-xorg-video-intel 2:2.9.0-1ubuntu2. Also updated xserver-xorg-video-1740 1:1.3.0-1

Also read Pulseaudio might have an issue with it, it also updated: 1:0.9.19-0

If anyone can tell me what I need to install/remove, I'd be very grateful. Trying to work outwith my dock/KVM is an absolute nightmare.

Thanks,

AJ Cerqueti

---

### Post by alperyilmaz on 2009-12-09
I have HP Pavilion DV7 2180us with ATI Mobility Radeon HD 4650 and this workaround didn't work for me.

Machine can suspend but cannot resume.. It's black screen. I can switch to terminal by Ctrl+Alt+1 and what I see is error messages from EXT4-fs printing continuously on screen. I checked the log files after reboot but couldn't find the exact text of the error.

"Fix Suspend and Hibernate" was the top request in  [Ubuntu Brainstorm]("http://brainstorm.ubuntu.com/idea/94/") but it was not fixed yet.. It's sad and disappointing..

---

### Post by stu500 on 2009-12-12
I to had the suspend resume problems in both Ubuntu 9.10 and Mint 8  -  i am now using standard xubuntu 9.10  i don't know what had been done different in xubuntu but there is no problems with suspend/resume?

---

### Post by peakpc on 2009-12-13
I am very glad to finally known what files are causing the issue, not sure I want to regress though, suspend is not as important as compiz smoothness.  I do hope that Ubuntu with come up with a fix sooner rather than later.  10.04 Alpha is using the same bad drivers so far.  

Compaq v5000 with 2.2 turion 2gig ram ati 200m 9.10 32bit (did 64bit 9.04 but didn't see much advantage)

---

### Post by peakpc on 2009-12-13
Just for fun I made a backup image and then tried the regression as described. 
 
It did fix hibernation, which of course takes longer than a reboot and so is of no great value.

It did not fix suspend, which is the thing that I would use on occasion, however, all I get is a steady power and wireless light plus a blank screen.  from there my only option is to hold down the power button until power off.  

So..no real advantage for me at this time (reverted to backup image)just thought I'd post my results for what it's worth.:(

---

### Post by Naturally-Simple on 2009-12-13
So, I'd like to try that suggestion made a little while ago by ikdot regarding help for Intel graphics card users, but I'm confused by the one line, when they write:
> Note that the output parameter may vary; you can see the appropriate value for your system by running xrandr at a console and examining the output.

I ran xrandr in a terminal and it came up with this:
> Screen 0: minimum 320 x 200, current 1024 x 768, maximum 2048 x 2048
VGA1 unknown connection (normal left inverted right x axis y axis)
   1360x768       59.8  
   1152x864       60.0  
   1024x768       60.0  
   800x600        60.3  
   640x480        59.9  
LVDS1 unknown connection 1024x768+0+0 (normal left inverted right x axis y axis) 0mm x 0mm
   1024x768       60.0*+   85.0     75.0     70.1     60.0  
   832x624        74.6  
   800x600        85.1     72.2     75.0     60.3     56.2  
   640x480        85.0     72.8     75.0     59.9  
   720x400        85.0  
   640x400        85.1  
   640x350        85.1 

I'm assuming that asterisk next to the 60.0 means something, but how am I supposed to apply this to the directions given about the creation of that file? Furthermore, I don't understand where I'm supposed to save this file, nor how to make it executable or linked to a particular keystroke or shortcut.

I also don't know what a kernel is or what its function is. Can anyone update their kernel when an update comes out?

If I sound like a newbie, you got it, I'm as fresh and dumb as they come when it comes to Ubuntu. I like it so far, but it takes some getting used to. I apologize if beginners like me are supposed to post in the beginners' section, but it's a technical issue I have here--I just need beginner-speak to help me through. :)

Oh, and as for any specs to mention, the basics are: Ubuntu 9.10 on a Dell Inspiron 1100, and when I typed some command to get my kernel, it came up as 2.6.31-16-generic.

---

### Post by Ozdemon on 2009-12-22
lamaistres solution worked for me with Compaq nx6125 (ati). :) 
Suspend issue was really bugging me.

---

### Post by brettpim on 2009-12-22
I have a Dell Latitude XT2.  Suspend worked fine out of the box in Ubuntu 9.10 but Hibernate will shutdown the computer fine but freeze during the boot with a "waking up" message.
I tried various things suggested on the old 64bit thread for this issue (new kernel, "quirk" settings in pm-hibernate script) but nothing has worked.  Following some links I found this page:

[http://lxr.linux.no/#linux+v2.6.32/Documentation/power/basic-pm-debugging.txt](http://lxr.linux.no/#linux+v2.6.32/Documentation/power/basic-pm-debugging.txt)

There I was able to successfully perform all 5 tests so I am on to the minimal configuration with very few drivers. 

I tried all three hibernate modes in a minimal init=/bin/bash boot-up.  None of them successfully shutdown (which is the opposite of my normal hibernate problem) The error seems to be that CPU#0 is not able to shutdown.

---

### Post by dr.grant on 2009-12-28
> **lamaistres said:**
> I have a Presario v2000 laptop. My graphic chip is a radeon xpress 200m 5955 igp. So far, downgrading -ati and -radeon video packages has fixed my suspend and hibernate blank screen problem. I thought I would repost everything I have because the 64-bit forum was shutdown and my post was incomplete, so I hope you don't mind. I have tested this on the default 2.6.31-14 kernel and the latest ppa-mainline-rc7 kernel.

The name of the packages that I installed are;
xserver-xorg-video-radeon_6.12.1-0ubuntu2
xserver-xorg-video-ati_6.12.1-0ubuntu2

Here are the links for the two deb packages in launchpad. Download the package that fit your archetecture, ie. amd64, i386, ia64.

[https://launchpad.net/ubuntu/jaunty/+package/xserver-xorg-video-radeon]("https://launchpad.net/ubuntu/jaunty/+package/xserver-xorg-video-radeon")
[https://launchpad.net/ubuntu/jaunty/+package/xserver-xorg-video-ati]("https://launchpad.net/ubuntu/jaunty/+package/xserver-xorg-video-ati")

Remove the current packages from karmic.
sudo apt-get remove xserver-xorg-video-radeon
sudo apt-get remove xserver-xorg-video-ati

And then, install the downloaded jaunty packages;
sudo dpkg -i xserver-xorg-video-radeon
sudo dpkg -i xserver-xorg-video-ati

Reboot the computer.

Now, if this doesn't work, simply reinstall the default packages;
sudo apt-get remove xserver-xorg-video-radeon
sudo apt-get remove xserver-xorg-video-ati
sudo apt-get install xserver-xorg-video-radeon
sudo apt-get install xserver-xorg-video-ati

To lock the packages, open system > administration > synaptic package manager and search for these two packages, then highlight the package and go to "package" in the toolbar and click "lock version". Only do this if you know it works. Afterwords, the packages should not update with update manager.

Also if you use apt frequently like I do, then pinning these packages will prevent them from installing when upgrading your laptop. Edit or create the file "/etc/apt/preferences" and add the following;



That should prevent these package from being upgraded to versions from karmic.

This is everything I did to get suspend and hibernate to work with my radeon 200m graphic chip. I hope this information is helpful or useful.

Greetings, all. This is my first post. I installed ubuntu yesterday and the suspend/hibernate problem is the only problem I've experienced so far. In any case, I have a Gateway MD2614 Notebook with the 64 bit AMD chipset, and after following the above instructions I cannot get past the login screen! 

It asks me for my password, I type it, hear about half of the login music play and then it shuts down and cycles back to the login screen. HELP! I've scoured the forums and cannot find any help and I'm pretty close to scrapping the whole thing and going back to windows.

Thanks a million!

---

### Post by Naturally-Simple on 2009-12-28
Dr. Grant, I am by no means a programmer or very Linux/Ubuntu-savvy, so take what I write here with that in mind.

If you can't get past the login screen, you may have burned a bad .iso image from the download. Did you burn it on the slowest speed? I'd first check this issue. If you burn another cd from the .iso file and you get the same result, then try it out, it's worth the cost of one cd.

If that doesn't solve the problem, I'd look at reinstalling Ubuntu. Which reminds me to ask: this is 9.10 you're using, yes? I've gone down to 9.04 since first posting my problem here, and I'm happy to say the issues I had with 9.10 are mostly gone. I haven't been able to test all of the problems (currently installing the full thing instead of a partition sharing with 9.10), but the key for me so far has been that I can press ctrl-alt-F1 and get a terminal prompt when something freezes, and then do a troubleshoot or find out what's going on.

Now if only I knew how to do a troubleshoot and what commands to use to find out what's wrong! haha! :)

But I at least have the option, unlike when everything froze and I couldn't do ANYTHING with 9.10. Sometimes the newest thing out there isn't always the best for your particular machine.

I was told that my issue was entirely related to my specific Intel chipset and a bug(s): [I][Bug #466310]("https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/466310") and [Bug #456902]("https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/456902")
[/I]
This may not help you, especially considering you have a different chip, but I'd try a slightly older version of Ubuntu before giving up. Believe you me, I understand the frustrations of switching from Windows.

My analogy for Ubuntu is that it's like being given a really great car that you know will work excellently, but there are various mechanical issues that you have no idea how to solve, and finding a mechanic for your very specific part/problem is like finding a needle in a haystack (besides, a lot of the "mechanics" out there are trying to figure out their own problems).

To make that needle brighter and easier to see: a) don't mess around with the programming unless you know what it will do; and b) do searching based off of your specific hardware profile and you'll eventually find something (don't limit your searching to just these forums, either).

Wish I could help you. Hope you get the help you need!

---

### Post by poltr1 on 2009-12-28
I had the same problem on a Compaq Presario M2000 running karmic.  Suspending or hibernating the computer would result in the computer display not responding when I woke it up.  I tried the steps that lamaistres posted in this thread, and it appears to work for me now.  Thank you!

---

### Post by dr.grant on 2009-12-28
Kevin,

Thanks for your reply. I went ahead and re-installed. It still won't re-boot after "suspend", but at least it works now!

---

### Post by Ozdemon on 2009-12-31
I was back to square one today after doing an update.  Forgot to do the last step of lamaistres tutorial about preventing updates.  Re-did the tute, this time including the disable update step, and everything back to normal.
=D>

---

### Post by peakpc on 2010-01-02
bump! It seems no one is doing anything about this for 9.10

---

### Post by dr.grant on 2010-01-03
I'll second yer bump, peak. I wish like mad that the ubuntu programmer folks would fix this. Heck, I wish I had the knowledge to fix this. I've told 4 people about ubuntu and were it not for the suspend/hibernate/wake problems they'd like to sign on.

*sigh*

---

### Post by seenthelite on 2010-01-03
> **dr.grant said:**
> I'll second yer bump, peak. I wish like mad that the ubuntu programmer folks would fix this. Heck, I wish I had the knowledge to fix this. I've told 4 people about ubuntu and were it not for the suspend/hibernate/wake problems they'd like to sign on.

*sigh*

I agree, I removed Ubuntu and reinstalled Windows 7, I'll try again in April with 10.04. I find a laptop is hard to use without suspend working.

---

### Post by peakpc on 2010-01-07
No need to stop using Ubuntu all together just install 9.04 it suspended and Hibernated just fine.  And I would recommend it for all who need this feature for the time being.  though It seems sad that it has not been fixed.

---

### Post by Zaphod69 on 2010-01-07
Not sure why but since the last update I've been able to unplug my laptop form the power cable without it going into suspend mode and not waking up.

However I still cannot resume after suspending the computer.

---

### Post by peakpc on 2010-01-07
I had not even heard of this issue, mine runs just fine on battery or AC and does not suspend on the transition.  Just Updated to 2.6.31-17-generic however, after testing I still get a black screen on resume with no options but to power off and reboot. My frustration is that I don't know if anyone is even working on the problem.:(

---

### Post by Exüberance on 2010-01-10
I installed uswususp, and tried using s2ram from that, and it almost looked like it was working, but the taskbar, desktop background, and icons dissapear, and attempting to restart X fails, simply giving an infinite loop of error and forcing me to hold down the power button to start.

I did find this page, though, which may fix the problem. I haven't tried it yet, but I will when I have time (and am confident enough that I won't end up screwing up the computer :D).
[http://en.opensuse.org/NVidia_Suspend_HOWTO](http://en.opensuse.org/NVidia_Suspend_HOWTO)

---

### Post by ognum on 2010-01-10
The following message was posted by Renegade Lisp in the thread in the 64bit support forum (post #275):
> My Thinkpad T61 wouldn't suspend after I upgraded from 9.04 to 9.10. I've been able to fix it: The reason was that I had force-downgraded the Intel xserver to a previous version under 9.04 in order to work around the performance problems introduced in that release. This downgraded package was not upgraded during the 9.10 upgrade.

I have manually installed the package xserver-xorg-video-intel 2:2.9.0-1ubuntu2 now, and this fixed the suspend problem. Incidentally, this also fixed the problem of my desktop effects (compiz) not working under the new release.

I like Karmic much better now

I'm happy to say that this worked for my Lenovo Thinkpad X60. I had also previously downgraded the xserver on 9.04 (and forgotten about it).

---

### Post by dro0g on 2010-01-15
I've been able to get suspend working on a Dell Latitude D630 with Intel graphics and Broadcom wireless. Prior to suspending, I have to disable compiz. After resume, compiz can be re-enabled. If it's left on when the machine goes to suspend behavior is flaky (sometimes it fails to suspend, sometimes it hangs during resume, sometimes it resumes and then kernel panics within a minute or two)

---

### Post by peakpc on 2010-01-21
I tried disabling Compiz but, no change. still a blank (black) screen on resume with on option but to power down.

---

### Post by t4thfavor on 2010-01-21
Same boat folks, it appears that most machines don't wake up properly, with a better chance of not waking up if they are using ATI/Nvidia cards.I find the "downgrade" to be an unacceptable solution. If it wasn't for my Asus netbook working flawlessly, and a million posts like this [http://tech.slashdot.org/story/10/01/20/1359237/Newly-Found-Windows-Bug-Affects-All-Versions-Since-NT?from=rss&utm_source=feedburner&utm_medium=feed&utm_campaign=Feed:+Slashdot/slashdot+%28Slashdot%29&utm_content=Google+Feedfetcher]("http://tech.slashdot.org/story/10/01/20/1359237/Newly-Found-Windows-Bug-Affects-All-Versions-Since-NT?from=rss&utm_source=feedburner&utm_medium=feed&utm_campaign=Feed:+Slashdot/slashdot+%28Slashdot%29&utm_content=Google+Feedfetcher")

I would probably be back to an mostly windows shop (eww).

---

### Post by thecaptainzap on 2010-01-28
This is a half-bump/half-question...

So I've got an HP Pavilion dv6000 with an AMD64 chipset and an NVidia card. It's able to go to suspend, but when I try to wake it up, I get nothing but a blank, dark screen (not even backlit).

I'm new to Linux, but not computers in general. Any advice? I'd very much prefer to have a working system with standby options (since it IS a laptop). Would a downgrade to 9.04 work?

---

### Post by freonchill on 2010-01-28
adding to the mix

have an older dell d800 laptop

pentium mobile (not p4, but first-gen centrino) + nvidia geforce 4 4400
under ubuntu 8.x & 9.x, as well as fedora 11
[ubuntu - drivers that install themselves from restricted]
[fedora - drivers manually installed from nvidia's website]
[both are extremely old 96.xx series, as the gf4 is pretty much not supported from nvidia anymore; funny, just checked the nvidia site, they updated the drivers in november 2009... doubt they fixed it.]

i can suspend / hibernate
it works when i come back
but if i suspend / hibernate a second time
when i come back, i get the blank black screen, no backlight... nothing

i have tried the NvAGP "1" in the /etc/X11/xorg.conf file
i have tried both POST_VIDEO=false & SAVE_VBE_STATE=false in /etc/default/acpi-support

---

### Post by dinutu on 2010-01-29
i had this kind of issue on hp compaq nx6310 solved it by enlarging the swap space from 500mb to 1gb..

---

### Post by Darkz_Soul on 2010-02-10
Hello
I am trying to get my Hp dv6663us to suspend/hibernate.. several months ago i had a previous install of ubuntu running flawlessly and i reinstalled not long ago and bamm nothing as far as it goes.. Although i would like to note since my wifi had to be installed offine i also downloaded Nvidia drivers from Nvidia which is version 190 or something like that and when i got Internet i reverted to ubuntu's version... so if the "old" driver left stuff behind that might be causing the problem... i have a tread [here]("http://ubuntu-ky.ubuntuforums.org/showthread.php?p=8802912") [http://ubuntu-ky.ubuntuforums.org/showthread.php?p=8802912](http://ubuntu-ky.ubuntuforums.org/showthread.php?p=8802912)


Thanks

---

### Post by rjaguar3 on 2010-02-12
I can't find this issue anywhere in the thread, but my Thinkpad T61 does not even enter suspend with the nVIDIA drivers; the crescent moon indicator light just keeps on blinking forever, leaving me no choice but to cycle the power.

---

### Post by ugizz on 2010-03-08
Hp Dv5-1000ea: suspend feature not working!

---

### Post by poltr1 on 2010-03-12
I should mention that this workaround works for me most of the time.  There have been a few times where the mouse and keyboard are "locked" when coming out of suspend mode, and the only thing I can do is to power down and reboot.  

Any word on whether this is going to be fixed in Lucid?

---

### Post by Alex_W on 2010-03-14
...well... this is mostly a rant...

Today I tried several LiveCDs (including Karmic) on my wife's Vaio (VGN-FW275D) with a single goal: to see if the Power Management works... and it did. In LiveCD mode. _In full_ (well, obviously, I didn't test the "suspend to disk" feature). Without any tinkering. Same can be said about the rest of the system (HW detection, etc.)

Meanwhile, on my HP Pavilion dv4000, the situation is still the same: the system's reaction to AC disconnect is unpredictable (it may go into standby, for example, or may react correctly); suspend-to-RAM on lid close will work only after I suspend it once from the DE... The Sound is sort of hanging on a bunch of workarounds, and is merely acceptable. And no solution in sight.

It is obviously not a show stopper -- just an annoyance, -- and I still continue doing my daily computing in Ubuntu, trading off the flawless Power Management and Sound this laptop had under XP for the safety, tremendous UI flexibility, and all those things the Open Source is so famous for, of Ubuntu Karmic...

I just hope that on that sunny day when Lucid comes out, I boot up the Lucid LiveCD on my old Pavilion, and everything will "just work" the way it's supposed to...

end of rant.

cheers.

---

### Post by domi007 on 2010-03-15
I got an old Compaq Evo N800W laptop (P4-M 2.2 GHz, ATI FireGL V9000). Ubuntu works good, I had no suspend issues, but I used setkeycodes to set up my MultiMedia buttons.
After I did that my keyboard doesn't work after suspend-wakeup, so I just didn't use that feature (however it bothered me a lot).
Today I tried it again, and it got worse: now not only the keyboard, but the TouchPad and the TrackBall don't work either (so basically none of my input devices).

You have any advice?
Thank you,
DOMy

---

### Post by Alex_W on 2010-03-21
Lucid Beta 1 hasn't made my HP dv4000 happier... :-(

---

### Post by XxX_VLAD_XxX on 2010-03-21
Once i had that problem, try jus typing your password and press enter, worked for me

---

### Post by eater on 2010-03-28
I'm running 8.10 on a Thinkpad X200s. One out of every 5 or 10 times when I open the laptop to wake it, the mouse pointer is frozen in the middle of the screen. I can fix this by running "sudo modprobe psmouse". But then, at the end of that computing session, the machine won't suspend again -- closing the lid does nothing except start the screensaver, and I have to shut down the system instead.

Is there another module perhaps that I should modprobe that would let it suspend in those cases? Or any other solution?

I have 8.04 installed on another similar system (X200) and that machine never encounters this problem.

Thanks!

---

### Post by Guglielmo90 on 2010-03-28
I have a Vaio vgn-cs21s and my keyboard is frozen after resume from suspend... I hope you can help me.

---

### Post by a7j_72 on 2010-04-02
I had a blank black screen when resuming from suspend.

I was going to follow **lamaistres instructions **and he made me realize that it is a built in driver issue. I have an nVidia graphic card and the proprietary drivers from the manufacturer were easily accessible through  

*System >> Administration >> Hardware Drivers*.


Selecting the recommended propiatary drivers worked for me. I think if your driver is not listed there you might have to download the drivers just like lamaistres specified. 

Thanks lamaistres.

---

### Post by peakpc on 2010-05-05
for those of that might be wondering what happened to me and why I not still complaining It's because I bought a new Laptop with an Intel (i5) video... so with 10.04 life is good. though I still have very little reason to suspend let alone hibernate as boot times are now 25 seconds and shutdown times are about 5 seconds. I sold the old laptop so...sorry I woln't be able to test any more.

---

### Post by -jay- on 2010-05-05
my desktop specs in sig can't resume from suspend in 10.04 my keyboard & mouse do not power back up

i did the following unplugged all hds & plugged 1 at a time back in, changed video cards from ati 4650 silent to nvidia 9800gt, updated to latest bios which is a beta bios & still no luck

my board uses nforce4 amd

in 9.04 resumed worked wonders

---

### Post by TheHimself on 2010-05-06
I have a Lenovo X61t with Xubuntu 9.1. When I want to suspend, the 'suspend' LED keeps flashing and never stops. I have to force it shut down. That was not the case from the beginning.

---

### Post by jdunn on 2010-05-06
I have an HP Pavilion dv-1251nr notebook pc and I've had the following minor problem with Ubuntu 9.10 and 10.04 while using the dc adapter: When I close the lid, the laptop goes into Suspend mode, as it should. When I open the lid the laptop comes out of suspend but the brightness is minimum. I have to manually increase the brightness. The change remains affective until I reboot or shutdown.

---

### Post by Graysphere on 2010-05-13
My MSI S270 (MS-1013, SAM2000) is an early 64 bit system. I alsays used 32 bit Ubuntu. 9.04 would suspend and resume okay.

10.04 however would not resume. Power comes on, but no result for keypresses, nothing (not even caps lock led). And after installing Lucid, 9.04 had the same problem.

The only difference with booting 9.04 was grub2. However illogical, I downgraded from grub2 to grub legacy, and now my laptop again resumes!

I wonder what is different in grub2 versus grub-legacy to cause this. After all, Grub has nothing to do with the actual resume. It may however interact differently with the BIOS when booting, so the bios goes in adifferent mode.

---

### Post by dahlheim on 2010-05-24
i have 10.04 on a dell xps-m1210 and suspend/resume is working well, however i would like very much to be able to instruct my wireless card NOT to be enabled on resume.  each time i disable it and suspend, it becomes enabled again upon resume.  any help appreciated.

---

### Post by mktrejo on 2010-05-24
I have a W500 with fglrx since the video card is a FireGL Hd3650 latest kernel and updates. Problem is that sometimes when resuming from hibernate screen comes back I can see mouse pointer moving slowly and then normally but no more. Hovering over the place that lock windows should be changes pointer to writing cursor, but that's it. No other thing is rendered on the screen. Ctr+ALT+F1 works so I can restart gdm and get logged again but my session is gone.

Resume from suspend haven't showed that so far, but may show it since I almost don use suspend.

No hibernate option on GDM login screen but maybe unrelated. Please send suggestions on hot to troubleshoot.

---

### Post by biogerm on 2010-05-25
> **Graysphere said:**
> My MSI S270 (MS-1013, SAM2000) is an early 64 bit system. I alsays used 32 bit Ubuntu. 9.04 would suspend and resume okay.

10.04 however would not resume. Power comes on, but no result for keypresses, nothing (not even caps lock led). And after installing Lucid, 9.04 had the same problem.

The only difference with booting 9.04 was grub2. However illogical, I downgraded from grub2 to grub legacy, and now my laptop again resumes!

I wonder what is different in grub2 versus grub-legacy to cause this. After all, Grub has nothing to do with the actual resume. It may however interact differently with the BIOS when booting, so the bios goes in adifferent mode.

i will try your method :)

i have the similar problem with my desktop. i don't remember if it worked before in 9.04 or 9.10, probably not, and it doesn't work in 10.04 32bit Ubuntu. everything looks fine until the system goes to suspend or hibernate mode. led turns to yellow and system stops while suspend and everything goes off while hibernating. 

the problem is it never wakes up. if pressing power button or sleep button on keyboard while suspend, the system powers up but the screen is still off. you have no control on the system. keyboard doesn't react and even capslock doesn't work. i tried to ping the machine, however, it works. but ssh fails.

i tried use s2ram instead of system suspend. it fails on the default mode "s2ram -f". however if using "s2ram -f -a 2" or 3, the system comes back with screen signal. some command lines are shown on the screen and you can see the mouse pointer, even though it looks like tty screen and the pointer doesn't move.

later i tried uswsusp and added a module file on /etc/pm/config.d/ which is "SLEEP_MODE=uswsusp". it doesn't work.

**a very interesting thing is that if i turn the machine into sleep and wake it up with a very short time, it comes back alive!!!**

10 seconds after the led goes yellow is even too long for this.

any suggestions are appreciated. i will post anything i can if anyone thinks it helps. thanks in advance.

---

### Post by busymind on 2010-07-27
#WorkAround D800 Latitude 
Working
lspci
00:00.0 Host bridge: Intel Corporation 82855PM Processor to I/O Controller (rev 03)
00:01.0 PCI bridge: Intel Corporation 82855PM Processor to AGP Controller (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 (rev 01)
00:1d.2 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3 (rev 01)
00:1d.7 USB Controller: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 81)
00:1f.0 ISA bridge: Intel Corporation 82801DBM (ICH4-M) LPC Interface Bridge (rev 01)
00:1f.1 IDE interface: Intel Corporation 82801DBM (ICH4-M) IDE Controller (rev 01)
00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 01)
00:1f.6 Modem: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Modem Controller (rev 01)
01:00.0 VGA compatible controller: nVidia Corporation NV28 [GeForce4 Ti 4200 Go AGP 8x] (rev a1)
02:00.0 Ethernet controller: Broadcom Corporation NetXtreme BCM5705M Gigabit Ethernet (rev 01)
02:01.0 CardBus bridge: Texas Instruments PCI7510 PC card Cardbus Controller (rev 01)
02:01.1 CardBus bridge: Texas Instruments PCI7510,7610 PC card Cardbus Controller (rev 01)
02:01.2 FireWire (IEEE 1394): Texas Instruments PCI7410,7510,7610 OHCI-Lynx Controller
02:01.3 System peripheral: Texas Instruments PCI7410,7510,7610 PCI Firmware Loading Function
03:00.0 Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)

Etape 1

Go to SYSTEM -> Power Management
"On batery power" when laptop lid is closed - BLANK SCREEN
(because we use acpi to call the real suspend)
Also for "on AC Power"

Etape 2

sudo apt-get install uswsusp
And by typing the below command you check if the suspend function works now….
sudo s2ram
Same goes for hibernation
sudo s2disk (optional I don't test it yet)

Create a custom file action

touch /etc/acpi/lidsuspend-acustom.sh
nano /etc/acpi/lidsuspend-acustom.sh

# Start of file
#!/bin/sh
/usr/bin/xscreensaver-command -lock 2>/dev/nul
sleep 1
/usr/sbin/s2ram
/usr/bin/xscreensaver-command -deactivate 2>/dev/nul
# end of file

chmod a+x /etc/acpi/lidsuspend-acustom.sh

For my Dell D800 I change 2 files 
(I don't know at that time wich file is called from acpi on lid close, the good file is sleepbtn)

/etc/acpi/events/sleepbtn
/etc/acpi/events/lidbtn

nano /etc/acpi/events/sleepbtn
and change action

# .....
event=button[ /]sleep
action=/etc/acpi/lidsuspend-acustom.sh 

# end of file

nano /etc/acpi/events/lidbtn

# .....
event=button[ /]lid
action=/etc/acpi/lidsuspend-acustom.sh

service acpid start

---

