---
title: "Trouble Installing...."
date: 2009-08-30
forum: Installation &amp; Upgrades
---

### Post by RobDude16 on 2009-08-30
It's been a while since I've tried Linux (my last attempt ended when I couldn't get my wireless network adapter to work/get online).  But I've heard great things and I really want to be a part of Linux and Ubuntu.  

I downloaded 9.04 yesterday and created a bootable DVD this morning.  When I start up my PC I see the Ubuntu logo and I select 'Install'.  I ended up at a screen that had the Ubuntu logo and a little animated bar going back and forth...it sat there for a while.  When I came back to my PC I was at a command prompt of some sort.

Above the command prompt was something that looked like error information - it said something about the BIOS not reporting something in a way that Linux can understand.  

At the command prompt I could type 'Help' to get a list of commands but I didn't see anything that said, 'Install Ubuntu'.

Can anyone help me out?

---

### Post by PorkyPie on 2009-08-30
[https://help.ubuntu.com/7.04/installation-guide/i386/pre-install-bios-setup.html](https://help.ubuntu.com/7.04/installation-guide/i386/pre-install-bios-setup.html)

Make sure the settings are right.

Hope it helps and that you'll be able to use ubuntu.

Also, what are your system req's?

---

### Post by RobDude16 on 2009-08-30
> **PorkyPie said:**
> [https://help.ubuntu.com/7.04/installation-guide/i386/pre-install-bios-setup.html](https://help.ubuntu.com/7.04/installation-guide/i386/pre-install-bios-setup.html)

Make sure the settings are right.

Hope it helps and that you'll be able to use ubuntu.

Also, what are your system req's?

Thanks for the post.  After reading through that - I think I recognize the problem from the error message (in the future, I'll write down the complete text).  But yeah, I think I need to disable APM.

I'll give that a go.  Thanks for the help.

---

### Post by PorkyPie on 2009-08-30
> **RobDude16 said:**
> Thanks for the post.  After reading through that - I think I recognize the problem from the error message (in the future, I'll write down the complete text).  But yeah, I think I need to disable APM.

I'll give that a go.  Thanks for the help.

Oops! i actually gave instructions for 7.04, sorry! The link for Jaunty: [https://help.ubuntu.com/9.04/installation-guide/i386/pre-install-bios-setup.html](https://help.ubuntu.com/9.04/installation-guide/i386/pre-install-bios-setup.html)
I don't think it's much different to the 7.04 guide.

Sorry about that!

Hope you get it working!

---

### Post by RobDude16 on 2009-08-30
Alright - so, I went into my BIOS and I disabled the ACPI Functionality in the 'Power Management' menu.

I rebooted with the Ubuntu DVD in the drive and began the install, the same as last time.  After about 5-10 minutes this is what I saw....

--------------
6.412798 [firmware Bug]: powernow-k8:  Your BIOS does not provide ACPI_PSS objects in a way that Linux understands.  Please report this to the Linux ACPI maintainers and complain to your BIOS vendor.

Loading, please wait.

BusyBox v1.10.2.....(info about BusyBox and then a command prompt.
-------------- 

So, it seems like my BIOS setting change didn't help.  When I tried to reboot into Vista, it gave me an error message saying that Windows couldn't start up due to a recent hardware change or something.  I went back in the BIOS, turned on ACPI functionality and then was able to get back into Windows. 

Does anyone have any additional thoughts?

I found another person with the same problem who says they resolved it by turning on AMD Cool 'N quiet - so I'll be giving that a try.

---

### Post by PorkyPie on 2009-08-30
Could you tell me complete system req's?

Maybe you should try the alternate cd, [http://www.ubuntu.com/getubuntu/downloadmirrors#alternate](http://www.ubuntu.com/getubuntu/downloadmirrors#alternate) .

---

### Post by RobDude16 on 2009-08-30
After enabling the AMD Quiet N Cool setting in my BIOS - I tried the Ubuntu install again.  This time, I ended up at the command prompt - but I didn't see any error message above it.

So, yeah - I'm not sure what's going on.

It says 'BusyBox....' and the prompt says 'initramfs>' or something similar.

I'm trying to use the 32-bit Ubuntu 9.04 install.

I don't know if it helps - but I have an AMD Athlon 64 X2 with an EVGA nForce 590 SLI Am2 940Pin motherboard.  

I've installed Ubuntu before (6.something) and the install went smoothly.  I'm not sure what is going on.

---

### Post by RobDude16 on 2009-08-30
I'm running Vista x64 and have a 64-bit processor.  Should I be installing the 64bit version of Ubuntu?

I figured the 32bit would have better support since (and I'm just guessing) more people would have used it.  Could that be my problem?

---

### Post by raymondh on 2009-08-30
> **RobDude16 said:**
> I'm running Vista x64 and have a 64-bit processor.  Should I be installing the 64bit version of Ubuntu?

I figured the 32bit would have better support since (and I'm just guessing) more people would have used it.  Could that be my problem?

Not necessarily.  Your 64-bit can recognize 32-bit.  If you want to, you may also use 64-bit.

Back to the issue:

1.  Check [md5]("https://help.ubuntu.com/community/HowToMD5SUM")
2.  Check CD for defects

---

### Post by RobDude16 on 2009-08-30
> **raymondhenson said:**
> Not necessarily.  Your 64-bit can recognize 32-bit.  If you want to, you may also use 64-bit.

Back to the issue:

1.  Check [md5]("https://help.ubuntu.com/community/HowToMD5SUM")
2.  Check CD for defects

The MD5 for my downloaded .ISO matches the UbuntuHashes (66fa77789c7b8ff63130e5d5a272d67b - ubuntu-9.04-desktop-i386.iso)

I'm not sure how to check the CD for defects exactly.  I looked for any visible scratches and didn't see anything.

Er rather, I checked the DVD.  I burned the .ISO to a DVD and booted from that.  I'm not sure if that could be part of the problem.  I don't have any blank CDs here, but I can get some if you think this might be the problem.

Thanks again for all of the help everyone.  I do appreciate it.

---

### Post by raymondh on 2009-08-30
> **RobDude16 said:**
> The MD5 for my downloaded .ISO matches the UbuntuHashes (66fa77789c7b8ff63130e5d5a272d67b - ubuntu-9.04-desktop-i386.iso)

I'm not sure how to check the CD for defects exactly.  I looked for any visible scratches and didn't see anything.

Er rather, I checked the DVD.  I burned the .ISO to a DVD and booted from that.  I'm not sure if that could be part of the problem.  I don't have any blank CDs here, but I can get some if you think this might be the problem.

Thanks again for all of the help everyone.  I do appreciate it.

Aside from INSTALL, do you have other options like:
- TRY UBUNTU WITHOUT CHANGES
- CHECK CD FOR DEFECTS
when you boot into your DVD?

Just to eliminate the DVD, can you test it on another computer.  No need to install.

As for CD or DVD, if you do decide, I have seen threads suggesting the use of cd -R.  When you do burn, burn slow (like 8X or less) to minimize burning errors.

---

### Post by presence1960 on 2009-08-30
[Boot options]("https://help.ubuntu.com/community/BootOptions") for Live CD

scroll down to the section dealing with F6

---

### Post by RobDude16 on 2009-08-31
> **raymondhenson said:**
> Aside from INSTALL, do you have other options like:
- TRY UBUNTU WITHOUT CHANGES
- CHECK CD FOR DEFECTS
when you boot into your DVD?

Just to eliminate the DVD, can you test it on another computer.  No need to install.

As for CD or DVD, if you do decide, I have seen threads suggesting the use of cd -R.  When you do burn, burn slow (like 8X or less) to minimize burning errors.

Thanks for the clarification...I feel pretty silly.  When they said to check the disk for defects, I was like holding it up to the light and looking for scratches.

I tried the 'Check CD for Defects' option and it basically did the exact same thing...I saw the animated Ubuntu screen and then was kicked to the same command prompt as before.

Since the .ISO md5 matched correctly, I figured it would be pointless to download it again - but I am re-burning it right now, at x2 speed.

I did try playing with options available under the F6 menu but none of them seemed to affect the outcome.  Hopefully the new CD will work.

---

### Post by gordintoronto on 2009-08-31
> **RobDude16 said:**
> I'm running Vista x64 and have a 64-bit processor.  Should I be installing the 64bit version of Ubuntu?

I figured the 32bit would have better support since (and I'm just guessing) more people would have used it.  Could that be my problem?

I doubt if it is any part of your problem.  However, I've been using the 64-bit version since I built this AMD-based system three weeks ago.  There was one very minor issue due to 64-bit, which I easily overcame.  I suggest trying the 64-bit version.

---

### Post by raymondh on 2009-08-31
you can also try the alternate install.  It is text based instead of GUI.  It was meant for older, less powerful systems but can work on newer computers.

[http://www.ubuntu.com/getubuntu/downloadmirrors#alternate](http://www.ubuntu.com/getubuntu/downloadmirrors#alternate)

Good luck. Back up your files.  Post back success or errors.

---

### Post by presence1960 on 2009-08-31
> **RobDude16 said:**
> Thanks for the clarification...I feel pretty silly.  When they said to check the disk for defects, I was like holding it up to the light and looking for scratches.

I tried the 'Check CD for Defects' option and it basically did the exact same thing...I saw the animated Ubuntu screen and then was kicked to the same command prompt as before.

Since the .ISO md5 matched correctly, I figured it would be pointless to download it again - but I am re-burning it right now, at x2 speed.

I did try playing with options available under the F6 menu but none of them seemed to affect the outcome.  Hopefully the new CD will work.

Based on this info it definitely sounds like a bad burn. if that is true no options you would choose would matter.

---

### Post by RobDude16 on 2009-08-31
Hmmmpphhh....

I put the same .ISO onto a laptop and used that to burn the the disc.  I set the speed to 4x.  It verified the burn and said it was correct.  I did use the same burning software (Img Burn) on the laptop as I did on my desktop.

I'm still seeing the same problem though.  I keep ending up at that command prompt.  

Like I said before, I was able to install Ubuntu 6.something and the install was super easy - so I totally have faith that this will work.  I'm trying to think what is different with my system now compared to before. 

I have three hard-drives in my PC - two are configured in a RAID-0 and the third is sort of my backup area.  I have a partition on that 3rd drive that I'm intending to put Linux on.  I don't have a 'separate' RAID controller, it's just setup in my BIOS.

Could this be part of the problem?  I never get to the point where I can select where to install it, but I'm thought maybe it was related.

---

### Post by RobDude16 on 2009-08-31
Still no luck after playing around with various settings without really knowing what any of them do.

I guess I'll download the text-based installer and see if I can get that to work.

---

### Post by presence1960 on 2009-08-31
for software (fake) raid see here: [https://help.ubuntu.com/community/FakeRaidHowto](https://help.ubuntu.com/community/FakeRaidHowto)

---

### Post by RobDude16 on 2009-09-01
> **presence1960 said:**
> for software (fake) raid see here: [https://help.ubuntu.com/community/FakeRaidHowto](https://help.ubuntu.com/community/FakeRaidHowto)

It seems like the FakeRaid stuff would just allow Linux to see my two hard-drives as one single drive, or am I misunderstanding?

I'm not able to reach any part of the install that allows me to choose where I can install it.  I'm fine using my non-raided drive for Linux, if that's an option.

---

### Post by RobDude16 on 2009-09-01
Okay - I've downloaded the Alternate text-based installer and burned that to a CD.

I reboot and the Ubuntu install begins.  This time, once I select 'Install Ubuntu' or whatever it says, instead of the animated Ubuntu logo, I get a text-based screen and some more prompts about my keyboard.  After selecting my keyboard layout I get an error message saying that my CD-Rom cannot be mounted and that I need to insert the CD.

But the CD is inserted.  

I kept trying to continue but it kept repeating the same message.

For what it's worth the DVD drive I have works fine.  I've not had any other problems with it, until now, and I was successfully able to install Windows 7 on the very first attempt, from the same DVD drive the very same day I tried to install Ubuntu for the first time.

Can anyone offer any insight into what is going on?  

My DVD drive is an Optiaric DVD RW AD-7170A ATA device.  I only have the one so I can't try another.  I don't know offhand how it's jumper is configured as far as slave/master or whatever.  Could this be part of my problem?

---

### Post by RobDude16 on 2009-09-01
I know this thread is getting pretty long so I thought it might help if I consoldated everything into a single post so that people who see this don't have to read through all 3 pages of posts.

**[FONT="Arial Black"][SIZE="6"]Ubuntu 9.04 Install Problems Summary[/SIZE][/FONT]**
[LIST=1]
[*]**Download** the Ubuntu 9.04 i386 ISO
[*]**Burn** ISO to a blank DVD using IMG Burn
[*]**Reboot**, try to install Linux
[*]**Install fails** - I see an error message about ACPI and find myself at a command prompt.
[*]**Read - Edit BIOS** - I'm directed to [https://help.ubuntu.com/9.04/installation-guide/i386/pre-install-bios-setup.html](https://help.ubuntu.com/9.04/installation-guide/i386/pre-install-bios-setup.html) - I read and find that I didn't disable my 'Memory Hole' so I do that.
[*]**Reboot**, try to install Linux
[*]**Install fails** - I see an error message about ACPI and find myself at a command prompt.
[*]**Read - Edit BIOS** - After visiting this and other forums, I found that by enabling AMD Quiet N Cool the ACPI error would be resolved.  This information was not included in the 9.04 installation-guide linked to above.
[*]**Reboot**, try to install Linux
[*]**Install fails** - I see *no* error message - so that's a good sign (I think) - but I still end up at a command prompt.
[*]**Read** - At this point, it seems like the install disk itself is the most likely source of my problems.  I'm told to check the md5 of the download and the CD itself though the install screen.
[*]**Install winmd5sum** And use this to verify that my download was correct (and it was).
[*]**Reboot**, try to have the Ubuntu installer verify the disk.
[*]**Disk Check Fails** The same as with the install, I end up at the command prompt.  Unsure of what to do next I...
[*]**Re-Burned** ISO to a blank DVD using IMG Burn on a separate PC, hoping that the burn was bad.  As recommended, I use a low speed burn to reduce the chances of errors.  IMG Burn 'verifies' that the burn was successful (I'm not sure if that means anything or not).
[*]**Reboot**, try to install Linux (with the new disk)
[*]**Install fails** - Same as before, no error message that I can see - just the command prompt.
[*]**Read** the forums and end up directed to [https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions) - without really understanding the boot options in the F6 menu
[*]**Reboot - Install fails** Same sort of fail as before, did this a bunch of different times with the different options.
[*]**Read** the forums again.  I end up at [https://help.ubuntu.com/community/FakeRaidHowto](https://help.ubuntu.com/community/FakeRaidHowto) - I have three hard-drives two are configured in a RAID 0 though my BIOS.  I'm unsure if the FakeRaid would impact the installer or not (I'm trying to install to the un-raided hard-drive).
[*]**Read** the forums again.  It's suggested that I try the alternate download.
[*]**Download** the Ubuntu 9.04 i386 alternate installer ISO
[*]**Use winmd5sum** To verify that my download was correct (and it was).
[*]**Burned** ISO to a blank DVD using IMG Burn
[*]**Reboot**, try to install Linux
[*]**Install fails** - This time I end up stuck in an infinite loop.  The text based installer says it can't mount the CD and to insert the CD, but the CD is in.  My DVD drive seems to be functioning though - I used it to install Windows 7 two days ago without any problems.
[/LIST]

When I end up at the command prompt - I can do basic 'LS' and 'CD' type commands - but I don't really know much else.  Is there any way to diagnose why it is failing?  It takes quite a while before I get to the prompt - maybe an error log exists somewhere?  

When I use the alternate installer - it seems like it can't read the disk.  Are there any BIOS settings I might have missed that control how the DVD drive works - or possibly play with the pins/jumpers on the back of the drive?

I really do appreciate any help or suggestions you might have.

---

### Post by RobDude16 on 2009-09-02
Bump?

---

### Post by RobDude16 on 2009-09-02
Does anyone have any other thoughts on this?

I could pick up a cheap CD-ROM drive from Best Buy or something, if you guys think the hardware itself could be bad.

---

### Post by RobDude16 on 2009-09-02
Are there any commercial Ubuntu/Linux support companies I could contact?

I'm really very determined to get this to work.

---

### Post by RobDude16 on 2009-09-02
Does anyone think I'd have better luck with another distro?

---

### Post by RobDude16 on 2009-09-02
No idea what I should be doing here....so I'm off to download another .ISO - this time I'm trying Mint.  I'm told it's "practically" Ubuntu.  

I'll cross my fingers.....

---

### Post by RobDude16 on 2009-09-02
Mint install failed - nearly identically to how Ubuntu failed.  Just the icon and the color of the animated bar was different.

I spent some time playing at the command prompt - I did an 'ls' and I saw a file called **casper.log**.  I used 'cat' to open it up it said....

[I]/init: Line 1:  Cannot open /dev/sda: No such file
stdin: error 0
stdin: error 0
stdin: error 0
stdin: error 0
stdin: error 0
stdin: error 0
[/I]

etc.....

Can anyone tell me what /dev/sda is?

---

### Post by RobDude16 on 2009-09-02
Looks like someone else had this exact same problem back in 2007.

[http://ubuntuforums.org/archive/index.php/t-481690.html](http://ubuntuforums.org/archive/index.php/t-481690.html)

His solution was to use an additional external CD-ROM; but I don't have one of those.  Does anyone have any other suggestions?

---

### Post by linux_tech on 2009-09-02
When you boot to the ubuntu install cd it is one of the options in the on screen menu. Just select Check CD for defects with your arrow keys.

---

### Post by RobDude16 on 2009-09-03
> **linux_tech said:**
> When you boot to the ubuntu install cd it is one of the options in the on screen menu. Just select Check CD for defects with your arrow keys.

Thanks for the post....but I've already tried running the 'Check CD for Defects' option and it fails in the exact same way as running the installer.  

Beyond that, I've tried three completely different CDs, the 9.04 live-cd, the 9.04 alternate installer, and whatever the most recent version of Mint is.  All three CDs are exhibiting the same behavior.

---

### Post by RobDude16 on 2009-09-03
I know this thread is getting pretty long so I thought it might help if I consolidated everything into a single post so that people who see this don't have to read through all 4 pages of posts.

**[FONT="Arial Black"][SIZE="6"]Ubuntu 9.04 Install Problems Summary[/SIZE][/FONT]**
[LIST=1]
[*]**Download** the Ubuntu 9.04 i386 ISO
[*]**Burn** ISO to a blank DVD using IMG Burn
[*]**Reboot**, try to install Linux
[*]**Install fails** - I see an error message about ACPI and find myself at a command prompt.
[*]**Read - Edit BIOS** - I'm directed to [https://help.ubuntu.com/9.04/installation-guide/i386/pre-install-bios-setup.html](https://help.ubuntu.com/9.04/installation-guide/i386/pre-install-bios-setup.html) - I read and find that I didn't disable my 'Memory Hole' so I do that.
[*]**Reboot**, try to install Linux
[*]**Install fails** - I see an error message about ACPI and find myself at a command prompt.
[*]**Read - Edit BIOS** - After visiting this and other forums, I found that by enabling AMD Quiet N Cool the ACPI error would be resolved.  This information was not included in the 9.04 installation-guide linked to above.
[*]**Reboot**, try to install Linux
[*]**Install fails** - I see *no* error message - so that's a good sign (I think) - but I still end up at a command prompt.
[*]**Read** - At this point, it seems like the install disk itself is the most likely source of my problems.  I'm told to check the md5 of the download and the CD itself though the install screen.
[*]**Install winmd5sum** And use this to verify that my download was correct (and it was).
[*]**Reboot**, try to have the Ubuntu installer verify the disk.
[*]**Disk Check Fails** The same as with the install, I end up at the command prompt.  Unsure of what to do next I...
[*]**Re-Burned** ISO to a blank DVD using IMG Burn on a separate PC, hoping that the burn was bad.  As recommended, I use a low speed burn to reduce the chances of errors.  IMG Burn 'verifies' that the burn was successful (I'm not sure if that means anything or not).
[*]**Reboot**, try to install Linux (with the new disk)
[*]**Install fails** - Same as before, no error message that I can see - just the command prompt.
[*]**Read** the forums and end up directed to [https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions) - without really understanding the boot options in the F6 menu
[*]**Reboot - Install fails** Same sort of fail as before, did this a bunch of different times with the different options.
[*]**Read** the forums again.  I end up at [https://help.ubuntu.com/community/FakeRaidHowto](https://help.ubuntu.com/community/FakeRaidHowto) - I have three hard-drives two are configured in a RAID 0 though my BIOS.  I'm unsure if the FakeRaid would impact the installer or not (I'm trying to install to the un-raided hard-drive).
[*]**Read** the forums again.  It's suggested that I try the alternate download.
[*]**Download** the Ubuntu 9.04 i386 alternate installer ISO
[*]**Use winmd5sum** To verify that my download was correct (and it was).
[*]**Burned** ISO to a blank DVD using IMG Burn
[*]**Reboot**, try to install Linux
[*]**Install fails** - This time I end up stuck in an infinite loop.  The text based installer says it can't mount the CD and to insert the CD, but the CD is in.  My DVD drive seems to be functioning though - I used it to install Windows 7 two days ago without any problems.
[*]**Read** the forums again.  No suggestions, and without an 
[*]**Read** the forums again.  No suggestions, and without an error message to Google I'm pretty lost.
[*]**Read** the forums again.  No suggestions, and without an error message to Google I'm pretty lost.error message to Google I'm pretty lost.
[*]**Download Mint** I'm just shooting in the dark here, but I've heard Mint is just like Ubuntu, I thought maybe it would work better on my machine.  ([http://www.linuxmint.com/download.php](http://www.linuxmint.com/download.php))
[*]**Use winmd5sum** To verify that my download was correct (and it was).
[*]**Burned** ISO to a blank DVD using IMG Burn
[*]**Reboot**, try to install Mint Linux
[*]**Install fails** - In the exact same way as the Ubuntu Live-CD install does.  I'm kicked to the same command prompt.
[*]**Sit at the command prompt and play/pray** Having only the most basic understanding of *nix commands, I'm really just screwing around here.  Using the HELP command I can see a list of commands.  I had to reboot a time or two at this point because I'd typed a command and couldn't end it (ran 'cat' but couldn't figure out how to exit the cat program).  
[*]**Notice 'casper.log' file** In the directory I'm in by default after the failed install - there is only one file with a .log extension.  I do a 'cat casper.log' and I'm able to see the contents of the file - it says...
[i]/init: Line 1: Cannot open /dev/sda: No such file
stdin: error 0
stdin: error 0
stdin: error 0
stdin: error 0
stdin: error 0
stdin: error 0[/i]
[*]**Read** the internet.  Now that I've got some error message to work with, I find this page: [http://ubuntuforums.org/archive/index.php/t-481690.html](http://ubuntuforums.org/archive/index.php/t-481690.html) where someone is describing a very similar problem to mine (two years ago) and his solution was to make a 2nd install CD and plug in a 2nd CD-ROM and he reports that after the initial boot, the installer would read from the *other* drive.  My problem is that I do not have a 2nd cd-rom I can toss a duplicate CD into.
[/list]
If anyone can offer any insight into this problem, I would be very grateful.

---

### Post by PorkyPie on 2009-09-05
Hi again. Sorry that my previous solutions didn't work, but have you tried pressing F6 twice at the cd boot menu, and adding ```
acpi=off
``` at the end?

Or... if you have a usb memory stick handy, use [Unetbootin]("http://unetbootin.sourceforge.net/") to install it.

---

### Post by kiltedwonder on 2009-09-07
I'm having the same issue.  I'm using a live flash drive instead of a cd/dvd but am getting the same error.

A couple of interesting and maybe useful clues.  My old installation of Ubuntu still works fine, even with the new motherboard.  As long as I boot from my old, small drive it starts right up just like it always has.  

Also the first time I used the live flash drive it booted right up without the error.  Since then I've been getting the error.

---

### Post by kiltedwonder on 2009-09-07
Just made a new live flash drive with Ubuntu 8.04 rather than 9.04 and it worked right off the bat.  I successfully installed Ubuntu and it is working fine.  

The flash drive immediately stopped working though.  I tried to reboot to the flash drive and had no luck.  It didn't even think there was an OS on it at all.  I'm currently making a new one with 9.04 to see if it will work now.

---

### Post by ksprasad on 2009-09-09
Hi,
 Even I have some problem in installing ubuntu 9.04.
 For me,it gives error msg like this,
  
  Status: {DRDY ERR}
  error: {UNC}
  end_request: I/O error, dev sda, sector 5
  Buffer I/O error on device sda logical block 0
 
 Any idea about the problem?
 Thanks

---

### Post by PorkyPie on 2009-09-12
> **ksprasad said:**
> Hi,
 Even I have some problem in installing ubuntu 9.04.
 For me,it gives error msg like this,
  
  Status: {DRDY ERR}
  error: {UNC}
  end_request: I/O error, dev sda, sector 5
  Buffer I/O error on device sda logical block 0
 
 Any idea about the problem?
 Thanks

I would reccommend posting a thread about your problem.

Rgds,
PorkyPie

---

