---
title: "Re: Ubuntu on Dell Xps 15 9550 new Infinity display (i7 6gen 16gbr UHD 4k touch"
date: 2015-10-30
forum: Hardware
---

### Post by marco furio ferrario on 2015-10-30
Have anyone tried to install ubuntu on the last Dell xps 15 machine?

I'm pondering to buy it but I'm not expert enough to be a pioneer :-)

Please help.

Tnks

THANKS for your effort. I find it strange apparently the previous xps15 is exactly the model shown on the ubuntu website...

[http://www.ubuntu.com/desktop](http://www.ubuntu.com/desktop) it looks like it

---

### Post by jchedstrom on 2015-10-31
Haven't heard of anyone else doing this so I took the risk and purchased the Dell XPS 15 (9550) with the FHD 1920x1080 matt display, Intel Skylake i7-6700HQ,  512GB PCIe SSD, 16GB DDR4, 84Wh battery. My experience is that usually Dell's have pretty good Ubuntu support, though Optimus can be a pain. The summary is that it does NOT automatically work with Ubuntu 15.10. Some tweaking is necessary but not too bad. Here are my experiences and instructions to get it to work with a UEFI install.

0) Might not be necessary but did the following:

BIOS > Secure Boot > Disabled

1) The PCIe hard drive won't be recognized by live Ubuntu 15.10 by default. Change RAID to AHCI. When it works it will appear as /dev/nvme0n1.

BIOS>System Configuration>SATA Operation> switch RAID to AHCI

2) Random freezes will happen with the live Ubuntu 15.10. Symptoms are random freezes and infinite errors, something like the following: nouveau PFIFO SCHED_ERROR. Fix by pressing 'e' on grub menu during boot and add "nouveau.modeset=0" to the end of the line starting with "linux". Now boot live disk by pressing F10.

3) Touchpad might not work. For some reason it worked for me the first time and then never again. Easiest is to use a USB mouse temporarily. There's a fix for after install is finished.

4) Install should now work smoothly.

5) Reboot. Dell SupportAssist reports a failing component. "Error Code 2000-0151, Validation 106575, Hard Drive 1 incorrect status = 8000000000000003". Ignore this. Go into bios and setup the correct boot option.

There might be an automatically provided option to select under boot options. Otherwise manually set it up. BIOS>General>Boot Sequence > Add Boot Option > ubuntu > shimx64.efi (\EFI\ubuntu\shimx64.efi)

6) Try booting, but make sure you press SHIFT repeatedly during boot to get to grub menu. Repeat step (2) above.

7) On first successful boot edit /etc/default/grub, GRUB_CMDLINE_LINUX_DEFAULT="quiet splash nouveau.modeset=0". Then run "sudo update-grub". Now won't need to manually change grub settings on every boot.

8) Fix touchpad problem. Apparently the wrong kernel module (driver) is loaded. It's loading i2c_hid instead of i2c_designware_*.

lsmod | grep i2c #check what's loaded
echo "blacklist i2c_hid" | sudo tee -a /etc/modprobe.d/blacklist.conf
#apparently just blacklisting isn't good enough, for me it was also hiding in initramfs
sudo depmod -a
sudo update-initramfs -u
reboot

9) Graphics will be weird and flaky. The Nvidia drivers in the standard repositories are also a bit too old and will be flaky. I found that the new graphics-driver PPA worked well. Didn't try downloading from Nvidia directly. Bumblebee didn't work for me, giving a black screen, so Nvidia PRIME is recommended.

sudo apt-get purge nvida-*
sudo add-apt-repository ppa:graphics-drivers/ppa
sudo apt-get update
sudo apt-get install nvidia-355 nvidia-prime
sudo service lightdm restart


10) Add an indicator so you can tell whether Intel or Nvidia is being used.

sudo add-apt-repository ppa:nilarimogard/webupd8
sudo apt-get update
sudo apt-get install prime-indicator
prime-indicator

Tested and working:

- webcam works seemlessly, good color and resolution, but HORRIBLE un-useable placement at bottom of screen
- Cheese and Skype worked with webcam, Google Chrome PPA with Google Hangeouts didn't work
- speakers are a big step up from my Lenovo T430s

Remaining weird behavior not solved yet:

- HDMI output not always detected with Intel or Nvidia, hopefully small bug that will be fixed soon (VGA dongle working fine)
- laptop mic not detected by system, my headphone mic doesn't work either, probably a minor Ubuntu 15.10 bug and not a laptop driver issue
---- seems to work with Kernel v4.3
- bluetooth doesn't detect my external speaker, driver bug that should be fixed soon, I think it's related to this: [https://bugs.launchpad.net/ubuntu/+source/bluez/+bug/1448566](https://bugs.launchpad.net/ubuntu/+source/bluez/+bug/1448566)
- suspend/resume results in black screen
---- @parallelo fixed by installing kernel v4.3
- occasionally touchpad cursor jumps down/left because of using thumb for left-clicks, this shouldn't happen, probably some manual tweaks can fix this
- slow touchpad acceleration, system settings insufficient, need some manual tweaks
- login screen hangs until wifi connects
- both Intel and Nvidia are tearing, system is useable though, hopefully will improve over time with driver updates
- Sometimes switching graphics with 'nvidia-settings' doesn't work. Sometimes 'nvidia-select' works. My guess is that there is a minor Nvidia bug that will soon be fixed
- boot takes a long time, 20 seconds (old Lenovo 430s only took 10 seconds), i think this is just the slow Dell post

Otherwise the system seems to be woraking well. No crashing/freezing issues which is great. Hopefully this guide will save others a few hours (or days!) of pain. Please post your improvements/updates to this procedure to help us all out!

---

### Post by berk6 on 2015-11-01
@jchedstrom Nice guide man! I was also too thinking about a Dell laptop too since they are reliable and have reputable hardware!

---

### Post by andrewmatta on 2015-11-01
@jchedstrom - registered just to thank you :) This is exactly what I was looking for before deciding if I should buy that machine - exactly the configuration I'd go with too. Thank you for going through the work to figure things out - should be a real time saver.

If it's not too much trouble, do you have any information on battery life, and does the laptop seem to run cool and quiet enough in Linux? I used to have a dual-graphics laptop before that ran cool in Windows, but would burn up in Linux no matter what power/processor/video settings I tried, but that those were AMD cards.

---

### Post by Scott Deagan on 2015-11-01
Many thanks [**[COLOR=#000000]jchedstrom[/COLOR]**]("http://ubuntuforums.org/member.php?u=865321"). I'm still undecided. I currently have the Dell M3800 and can install Linux in around 30 minutes without any problems. I'm still leaning toward this XPS 9550 as I haven't seen any other Skylake laptops out there that are viable options.

---

### Post by astroman3001gt on 2015-11-02
Thanks for the fantastic info jchedstrom. It is really helpful. I am also still undecided. Did you try to connect the laptop to an external monitor / projector?

Edit: BTW, did you have any problems with the wifi card?

---

### Post by l1fe on 2015-11-02
I've been having a terrible time trying to get Dual Boot up and running. What I've done so far:

1. Reinstalled Windows 10 using an OEM disk and resized partitions
2. Set SATA mode to ACHI
3. Turned off SecureBoot (but kept UEFI mode)
4. Started the install of Xubuntu with nomodeset option
5. sudo gparted /dev/nvme0n1 my partitions for custom /, /home, /var, etc (had to use GParted because the install would freeze when trying to format /home) 
6. Finally clicked install and it's stuck on "Saving installed packages..."

Did you have to do anything special? How long did the install take? I'm waiting on 25 minutes and it's still just chilling. Running a separate terminal and nothing is really running in top...

[UPDATE]
It looks like a lot of this is related to [https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/875343](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/875343)

I did NOT mount a separate /var directory and I was able to move on. Just as an FYI, I had to set the Install Bootloader path to /dev/nvme0n1 since there's a known bug about the Ubuntu install not selecting the correct partition.

---

### Post by jchedstrom on 2015-11-02
@astroman: wifi card works well with good performance and range. The wifi connection rate seems to be reported incorrectly. External monitor support has been flaky and isn't always available. This is a HUGE problem for presentations. Going to try a VGA dongle today. Note that just discovered that bluetooth doesn't work.

A few people asked me about heat and battery life. Under typical light usage (email, web browsing, text editing, watching x264 encoded movies) the 84wh battery lasts ~6 hours if you use the Intel GPU only (Nvidia off). A short test makes me believe that using Nvidia gives similar battery life. They must be doing a good job of putting GPU in a low power state.

The laptop has nice air-flow design with a long intake the whole width of the bottom and a protected exit pointing into the hinge of the screen. It's unlikeally to block the air intake and impossible to block the air exit. Generally the fan is pretty quiet.  I did some numerical simulations which runs 8 threads at 100% CPU and was impressed that after 5 minutes didn't see any throttling. Heat and fan noise was acceptable.

Running Boarderlands 2 game with max graphic settings with Nvidia GPU made the fan roar. Power draw was about 74 watts according to battery report. Therefore only ~1 hour of battery life in this case. Bottom of laptop was hot but less than burning hot.

---

### Post by marco furio ferrario on 2015-11-02
Do you think Ubuntu 14.04.3 LTS is going to install smoother?

---

### Post by jchedstrom on 2015-11-02
I doubt 14.03 LTS will work. The main problems were with the new fancy GPU not having good nouveau compatibility and the new fancy Intel raid not displaying NVME hard drive. So an older OS release would likely be problematic. This laptop is on the bleeding edge of hardware so it's not surprising that a few tweaks are necessary. Actually the fact that I've had zero crashes/freezes so far is pretty impressive. You'll probably need to wait until 16.04 if you want to install without manually overcoming a few problems.

---

### Post by astroman3001gt on 2015-11-03
@[COLOR=#DD4814][COLOR=#000000][jchedstrom]("http://ubuntuforums.org/member.php?u=865321") Thanks again for posting all this info. I asked in Dell community foruns about linux compatability for this laptop, and the silent there is profund...

So from what I understood. Wifi seems to work well... 
The battery life seems a lot off from what they sell it for windows... specially for the one that you have (the largest one, right?)

Please let us know how the VGA [/COLOR][COLOR=#000000]dongle worked.[/COLOR][COLOR=#000000]

[/COLOR][/COLOR]

---

### Post by jchedstrom on 2015-11-03
VGA dongle worked perfectly. Makes sense since the driver is completely separate from the Nvidia/Intel stack and should be very mature and stable.

I have the largest battery (84wh). Hopefully someone will do a Windows test for us :-) Have you seen any 3rd party test with this hardware setup? I don't trust the 11-16 hours Dell claims.

---

### Post by shamil.si on 2015-11-04
Hi @jchedstrom

Thanks for nice guide. I'm facing 2 problems right now.
- Suspend doesn't work
- If I reboot the computer the BIOS doesn't detect the SSD drive. Only If I do full power-off and power-on the SSD got detected

Did you experience similar problems?

---

### Post by jchedstrom on 2015-11-04
@shamil.si

Confirm that suspend doesn't work on mine either.

Reboot works perfectly on mine. Did you change any drive settings in the bios? What version of bios are you on? From memory I think mine is 1.0.0.5.

---

### Post by shamil.si on 2015-11-04
@jchedstrom,

The restart stopped to work after I upgraded BIOS to version 01.00.03, after downgrading it back to 01.00.00 the restart started to work again! Go figure ...
Other stuff seems to work fine, the only thing is Suspend :(

---

### Post by astroman3001gt on 2015-11-06
Hi,

@jchedstrom Thanks for the feedback.

What about mic, webcam, etc...? Did you test it how they are performing?

---

### Post by parallelo on 2015-11-06
[COLOR=#000000]@[/COLOR][COLOR=#DD4814][COLOR=#000000][jchedstrom]("http://ubuntuforums.org/member.php?u=865321") and friends - Thanks to all for the very useful tips.  Much appreciated!  

After going through those steps in a UEFI dual-boot setup, I'm hitting a couple issues.  The main one is this:  

After the install, Ubuntu booted perfectly, once.  But, every successive boot has given the "Dell SupportAssist Error Code: 2000-0151" that you mentioned in your post.  I'm not able to ignore this error because it forces an immediate reboot after pressing "Continue."  So, I have not been able to get back into Ubuntu.  


[LIST]
[*]Any idea what causes this?
[*]Did it only happen to you once?
[*]How did you get around it?
[/LIST]

Thanks again!  

[/COLOR][/COLOR]

---

### Post by parallelo on 2015-11-06
Just a quick update..  My guess is that the Dell error message simply means is that it couldn't find the .efi path that was specified in the BIOS.  I just took another look and I can no longer find any \EFI\ubuntu\shimx64.efi.  Still investigating...

---

### Post by 7ql6 on 2015-11-06
It seems that [Dell/Canonical currently is focussed on the XPS 13 and not the XPS 15 yet]("https://twitter.com/danjared_/status/652205594036703236").
But there is an [installation summary]("http://digitaltopo.net/o/?p=243") that doesn't sound so bad.

If I understand you right the current state is far away from keeping the fan silent - right?

---

### Post by parallelo on 2015-11-06
Just wanted to thank @jchedstrom again for the really useful tips!  Well done!  

I had to use boot-repair to get a functioning system, but now I'm writing this post from a Ubuntu 15.10 partition on a new XPS 15 :-)

---

### Post by jchedstrom on 2015-11-07
@parallelo: Nice work! Weird that .efi disappeared. Hopefully this was do to a stray cosmic ray and not a nasty bug. Before I saw you fixed it, I was going to mention that I have Dell SupportAssist feature turned off in bios.

@astroman3001gt: Just tested. Webcam works and has good color/resolution. The location at the bottom of the screen makes it almost completely un-useable. If you do a lot of video conferencing I wouldn't suggest this laptop. Personally I'll use a USB one that clips to the top of the screen on the very rare conference call. Note that Skype and Cheese worked seemlessly. For some reason Google Chrome (from ppa) hangouts did't work, but something that should be fixed soon.

@astroman3001gt: Just tested. Unfortunately the mic isn't detected. Headphone mic doesn't work either so this looks like an Ubuntu 15.10 bug, not a driver issue.

---

### Post by parallelo on 2015-11-08
On the topic of suspend/resume, upgrading Ubuntu 15.10 to the new 4.3 kernel seemed to add support for it on my system

[http://ubuntuhandbook.org/index.php/2015/11/linux-kernel-4-3-released](http://ubuntuhandbook.org/index.php/2015/11/linux-kernel-4-3-released)

---

### Post by jchedstrom on 2015-11-09
@paralleo on that link the person claims that the newer kernel has "Intel Skylake enabled by default". Any idea what that means? Are you noticing any other performance or battery life improvements?

---

### Post by parallelo on 2015-11-09
I have seen that it better supports the Skylake iGPU:  [http://www.phoronix.com/scan.php?page=article&item=linux-43-features&num=1](http://www.phoronix.com/scan.php?page=article&item=linux-43-features&num=1)

And some more specifics:  [http://blog.ffwll.ch/2015/09/neat-drmi915-stuff-for-43.html](http://blog.ffwll.ch/2015/09/neat-drmi915-stuff-for-43.html)

---

### Post by Tyler_Kellogg on 2015-11-09
Thanks so much for this thread!  The battery life results convinced me not to buy an XPS 15 and I was about to put the order in (Hearing it would get 17 hours was a huge selling point for me as I assumed it'd be at least 12 in Ubuntu).  <10 is a deal breaker for me, so glad work was put into investigating this.

---

### Post by astroman3001gt on 2015-11-10
@[COLOR=#DD4814][COLOR=#000000][Tyler_Kellogg]("http://ubuntuforums.org/member.php?u=1955520")[/COLOR][/COLOR]  For me it is not only the battery life time. It is all the little things that it is currently not working... I guess in time there will be some improvement. I have being facing all these problems in my latest laptops buys... (Worse case was my small netbook asus 1025c which still today there is no good and east driver available for the atom N2800)...

Anyway, this time I would like to buy a laptop that is 100% (or very close) with linux. I though DELL was making these kind of computer. There were a few from DELL in the last years that were even sold with ubuntu... (as examples you have the previous xps 13, the m3800). But currently there is none... or is there?

Do you guys know any nice new ultrabook that is 100% compatible with Ubuntu? Maybe there is no new computer...

---

### Post by Annihil on 2015-11-10
> [COLOR=#404040][FONT=Open Sans]Don&#8217;t Turn RAID On back on&#8230; [/FONT][/COLOR]**Reinstall Windows**[COLOR=#404040][FONT=Open Sans][/FONT][/COLOR]
[LIST]
[*]Enable AHCI in Windows: Reinstall Windows, it will now detect you&#8217;re in AHCI mode and install properly.
[/LIST]


When you install Windows on AHCI mode, does the SSD is used in AHCI mode instead of NVMe mode ?

---

### Post by jchedstrom on 2015-11-10
@BobAdams (he's been trying to gett Arch to work [https://bbs.archlinux.org/viewtopic.php?id=204862](https://bbs.archlinux.org/viewtopic.php?id=204862))

Here's my xorg.conf file when using Nvidia-PRIME to switch to the Nvidia GPU. When switched to Intel GPU there is no xorg.conf... no idea why that is.

```

Section "ServerLayout"
    Identifier "layout"
    Screen 0 "nvidia"
    Inactive "intel"
EndSection


Section "Device"
    Identifier "intel"
    Driver "modesetting"
    BusID "PCI:0@0:2:0"
    Option "AccelMethod" "None"
EndSection


Section "Screen"
    Identifier "intel"
    Device "intel"
EndSection


Section "Device"
    Identifier "nvidia"
    Driver "nvidia"
    BusID "PCI:1@0:0:0"
    Option "ConstrainCursor" "off"
EndSection


Section "Screen"
    Identifier "nvidia"
    Device "nvidia"
    Option "AllowEmptyInitialConfiguration" "on"
    Option "IgnoreDisplayDevices" "CRT"
EndSection

```

Tried out the v4.3 kernel. I can verify that it fixed the Suspend issue. Surprisingly it also fixed the microphone issue, both built-in and connect to headphones. Unfortunately in a short test it didn't look like it had an effect on power draw or battery life.

---

### Post by astroman3001gt on 2015-11-11
@[COLOR=#DD4814][COLOR=#000000][jchedstrom]("http://ubuntuforums.org/member.php?u=865321"):[/COLOR][/COLOR] Nice news. So right now the only problem that you have is the battery life? Or is there more unsolved issues?

---

### Post by Annihil on 2015-11-11
Sorry to ask again, I'm willing to install Ubuntu, and I need to know if switching from RAID On to AHCI in BIOS change the way the SSD is used ?
Is it still used with NVMe instruction, or it will use the old AHCI standard, and therefore will affect performance ?
Thanks

---

### Post by fallenpwr on 2015-11-12
Hey guys, I'm having serious issues with trying to dual boot:  
  
My initial attempt to follow the #2 poster here resulted in this error when I tried to boot into my install:  
ALERT! /dev/disk/... does not exist.
Dropping to a shell! Busybox v1.21.1 ...

BUT! Today I reinstalled, this time specifying swap and bios-grub partition. And it booted! Except, in AHCI, not NVMe (RAID in BIOS). 
So I turned on RAID, and lo it gave me a Hard Drive Not Installed error (Dell SupportAssist). Whoo. 

I then proceeded to delete the swap and bio_grub partitions and reinstall, and the same problem persisted (I was unable to get the first problem back). I also checked with `modinfo nvme` to see if I had an nvme driver, and it looked fine. I should mention that Windows won't boot in AHCI, which is also slower than NVMe. 

I was so looking forward to having a nice dual boot workstation... This is so insanely frustrating and honestly makes me wonder why I'm even in tech.

I ran CrystalDiskMark before and after doing that; pretty sure it still uses NVMe since the benchmarks weren't affected.

---

### Post by Annihil on 2015-11-12
> **fallenpwr said:**
> I ran CrystalDiskMark before and after doing that; pretty sure it still uses NVMe since the benchmarks weren't affected.
That's good news. And is it possible to switch back to Raid On and boot Windows ?

---

### Post by fallenpwr on 2015-11-12
Yes, that's what I've done.

---

### Post by Annihil on 2015-11-12
> **fallenpwr said:**
> Yes, that's what I've done.
Cool. And are you also able to boot Ubuntu in Raid On mode ?
Basically you just used AHCI mode to install both OS, then you switched back to Raid On, am I right ?

By the way, do you know how to recover the Dell logo on Windows boot ?

---

### Post by parallelo on 2015-11-12
Regarding the questions/comments on dual-booting with Raid vs AHCI..  

If you have a pre-installed Windows partition and a newly installed Ubuntu partition, then you are probably currently in AHCI mode.  In this case, Ubuntu will boot fine, but Windows always gives blue-screen "unbootable" errors.  

Here's the solution:  **leave it in AHCI mode and reboot Windows in Safe-Mode once **-- only one time is necessary.  When you are in Windows Safe-Mode, then simply restart.  After that step, Windows will boot up fine regularly using AHCI. 

Using this trick, I have a functional Windows 10 + Ubuntu 15.10 dual-boot that is selectable via the grub menu.

Credit:  [silverhaul]("https://www.reddit.com/user/silverhaul") from [SIZE=2]https://www.reddit.com/r/Dell/comments/3r9a5t/linux_on_the_dell_xps_15_late2015/
[/SIZE]

---

### Post by fallenpwr on 2015-11-12
Hey, thanks for the reply, totes forgot about that thread. However, that solution means abandoning NVMe; would there not be a noticeable performance hit compared to NVMe? 

I cannot boot Ubuntu in Raid On.  

How do I get into Safe Mode if I can't boot Windows 10?

---

### Post by Annihil on 2015-11-12
> **fallenpwr said:**
> Hey, thanks for the reply, totes forgot about that thread. However, that solution means abandoning NVMe; would there not be a noticeable performance hit compared to NVMe? 

I cannot boot Ubuntu in Raid On.  

How do I get into Safe Mode if I can't boot Windows 10?

> [FONT=verdana]You can try booting in secure mode under ahci.[/FONT]
[LIST]
[*]change to ahci
[*]intall linux and all
[*]boot windows - failed: not recognized boot partition something
[*]try booting into windows again(or several times) until windows try to find the boot error(of course it doesn't work), but on advanced boot options, you can set to reboot into safe mode: Troubleshoot - Advanced options - startup settings
[*]booting into windows - this time in safe mode - works fine
[*]normal reboot - voila, windows now can successfully boot!
[/LIST]
[FONT=verdana]Windows seems to be loading a preset list of drivers during boot every time, that is why drive are not recognized first. Safe mode will try to load more drivers, and then write to the loading list,[/FONT]
[FONT=verdana]However, the is still a glitch. Windows freezes sometime, especially when I play Heroes Of The Storm: it will freeze every time when I'm ~ 9mins in game. I'm guessing it is possible that the Intel RST is messing up and deleting the driver or reinstalling windows may help, but I haven't tried either. Setting to RAID again will revert everything, have to go through all the reboots again to get Windows boot again.[/FONT]

Try booting into Windows again (or several times) until windows try to find the boot error(of course it doesn't work), but on advanced boot options, you can set to reboot into safe mode: Troubleshoot - Advanced options - startup settings.

By the way, are you sure you cannot go back to NVMe (RAID On) mode to boot ubuntu after that ?

---

### Post by fallenpwr on 2015-11-13
I am now running dual boot successfully under AHCI. No, I cannot revert to NVMe without breaking Ubuntu boot, even after my AHCI dual boot was working.

I Shift+Restarted Windows with Safe Mode options before changing to AHCI so I could easily boot into safe mode.  

Findings on disk speed: With CrystalDiskMark and a Queue Depth of 32 and 1 thread, no noticeable difference was found. That being said, no idea how a larger queue depth might impact scores (I would assume AHCI would start losing), and I'm not even sure how that translates to real world usage.

---

### Post by anhdle on 2015-11-13
Hi, I just wonder if anyone manages to run a second screen via HDMI port. I can't get Ubuntu to detect my second screen even with the new NVIDIA driver and latest kernel.

---

### Post by fallenpwr on 2015-11-13
"prime-indicator" package that tells whether Intel or Nvidia is being used conflicts with google-chrome-stable for some reason. Dang.

---

### Post by rocco5 on 2015-11-13
I purchased this exact system with the only intention of installing either ubuntu or opensuse leap.   Your post is 100% the reason why I have linux running after days of bashing my face on the desk. I wanted to add to your awesome post a few extras that gave me a working trackpad and video immediately. I'll start by confirming what exactly worked for me. 

1. BIOS SETTINGS
-AHCI was a must.
-Under Performance - C-STATEs - OFF
-Virtualization Support - Disabled both options
-System Configuration - USB/Thunderbolt Configuration - Always Allow Dell Docks - Disabled (unchecked)
-I also disabled the webcam.
-Auto OS Recovery Threshold - OFF
-Bios recover from hard drive and downgrade both unchecked
-Fastboot set to minimal

2. To install from live disk the setting nouveau.modeset=0 was a must.

3. I installed kbuntu via live disk. I chose kbuntu for plasma 5 and my familiarity to opensuse using plasma 5. Using kbuntu I had exactly the same issues as the instructions for ubuntu. However, by making more changes int he bios I was able to both break the track-pad and fix it. 
4. I tried adding the nouvea.modeset=0 to the grub file, however sudo update-grub yielded an error. Luckily, I'm able to boot without issue after a serious of updates, one of which was the system detected a better nvidia driver, occurred. 

So far, system is working perfectly for the last 5 hours. Power management is working, even though I disabled C-States. I never received any hard drive erros, slowness, screen tearing, or trouble with the above settings (I did run sudo apt-get update somewhere in the mix).


I apologize for not putting together the cleanest post. However, I wanted to get my thoughts out before I forgot them and also further help anyone make the decision to purchase this awesome Dell XPS 9550 and run ubuntu on it. 

**** Special thanks to jchedstrom **** because without your post I would still be bashing my face on the desk, and by now on the walls and floor. The nouveau.modeset=0 was the exact piece of information that saved the next week of my life. Thank you!



> **jchedstrom said:**
> Haven't heard of anyone else doing this so I took the risk and purchased the Dell XPS 15 (9550) with the FHD 1920x1080 matt display, Intel Skylake i7-6700HQ,  512GB PCIe SSD, 16GB DDR4, 84Wh battery. My experience is that usually Dell's have pretty good Ubuntu support, though Optimus can be a pain. The summary is that it does NOT automatically work with Ubuntu 15.10. Some tweaking is necessary but not too bad. Here are my experiences and instructions to get it to work with a UEFI install.

0) Might not be necessary but did the following:

BIOS > Secure Boot > Disabled

1) The PCIe hard drive won't be recognized by live Ubuntu 15.10 by default. Change RAID to AHCI. When it works it will appear as /dev/nvme0n1.

BIOS>System Configuration>SATA Operation> switch RAID to AHCI

2) Random freezes will happen with the live Ubuntu 15.10. Symptoms are random freezes and infinite errors, something like the following: nouveau PFIFO SCHED_ERROR. Fix by pressing 'e' on grub menu during boot and add "nouveau.modeset=0" to the end of the line starting with "linux". Now boot live disk by pressing F10.

3) Touchpad might not work. For some reason it worked for me the first time and then never again. Easiest is to use a USB mouse temporarily. There's a fix for after install is finished.

4) Install should now work smoothly.

5) Reboot. Dell SupportAssist reports a failing component. "Error Code 2000-0151, Validation 106575, Hard Drive 1 incorrect status = 8000000000000003". Ignore this. Go into bios and setup the correct boot option.

There might be an automatically provided option to select under boot options. Otherwise manually set it up. BIOS>General>Boot Sequence > Add Boot Option > ubuntu > shimx64.efi (\EFI\ubuntu\shimx64.efi)

6) Try booting, but make sure you press SHIFT repeatedly during boot to get to grub menu. Repeat step (2) above.

7) On first successful boot edit /etc/default/grub, GRUB_CMDLINE_LINUX_DEFAULT="quiet splash nouveau.modeset=0". Then run "sudo update-grub". Now won't need to manually change grub settings on every boot.

8) Fix touchpad problem. Apparently the wrong kernel module (driver) is loaded. It's loading i2c_hid instead of i2c_designware_*.

lsmod | grep i2c #check what's loaded
echo "blacklist i2c_hid" | sudo tee -a /etc/modprobe.d/blacklist.conf
#apparently just blacklisting isn't good enough, for me it was also hiding in initramfs
sudo depmod -a
sudo update-initramfs -u
reboot

9) Graphics will be weird and flaky. The Nvidia drivers in the standard repositories are also a bit too old and will be flaky. I found that the new graphics-driver PPA worked well. Didn't try downloading from Nvidia directly. Bumblebee didn't work for me, giving a black screen, so Nvidia PRIME is recommended.

sudo apt-get purge nvida-*
sudo add-apt-repository ppa:graphics-drivers/ppa
sudo apt-get update
sudo apt-get install nvidia-355 nvidia-prime
sudo service lightdm restart


10) Add an indicator so you can tell whether Intel or Nvidia is being used.

sudo add-apt-repository ppa:nilarimogard/webupd8
sudo apt-get update
sudo apt-get install prime-indicator
prime-indicator

Tested and working:

- webcam works seemlessly, good color and resolution, but HORRIBLE un-useable placement at bottom of screen
- Cheese and Skype worked with webcam, Google Chrome PPA with Google Hangeouts didn't work
- speakers are a big step up from my Lenovo T430s

Remaining weird behavior not solved yet:

- HDMI output not always detected with Intel or Nvidia, hopefully small bug that will be fixed soon (VGA dongle working fine)
- laptop mic not detected by system, my headphone mic doesn't work either, probably a minor Ubuntu 15.10 bug and not a laptop driver issue
---- seems to work with Kernel v4.3
- bluetooth doesn't detect my external speaker, driver bug that should be fixed soon, I think it's related to this: [https://bugs.launchpad.net/ubuntu/+source/bluez/+bug/1448566](https://bugs.launchpad.net/ubuntu/+source/bluez/+bug/1448566)
- suspend/resume results in black screen
---- @parallelo fixed by installing kernel v4.3
- occasionally touchpad cursor jumps down/left because of using thumb for left-clicks, this shouldn't happen, probably some manual tweaks can fix this
- slow touchpad acceleration, system settings insufficient, need some manual tweaks
- login screen hangs until wifi connects
- both Intel and Nvidia are tearing, system is useable though, hopefully will improve over time with driver updates
- Sometimes switching graphics with 'nvidia-settings' doesn't work. Sometimes 'nvidia-select' works. My guess is that there is a minor Nvidia bug that will soon be fixed
- boot takes a long time, 20 seconds (old Lenovo 430s only took 10 seconds), i think this is just the slow Dell post

Otherwise the system seems to be woraking well. No crashing/freezing issues which is great. Hopefully this guide will save others a few hours (or days!) of pain. Please post your improvements/updates to this procedure to help us all out!

---

### Post by jchedstrom on 2015-11-13
Does anyone know what "AHCI" or "RAID" actually means in the bios? I've always assumed that Dell's RAID was just AHCI plus some useless features that cause problems. My system detects the drive as a NVMe drive and loads the nvme module when the bios is set to AHCI. That seems to match what @fallenpwr has found with the CrystalDiskMark benchmarks being unchanged.

---

### Post by fallenpwr on 2015-11-13
Interesting. However in Windows, I'm getting crashes now, very likely attributable to using AHCI.

---

### Post by Annihil on 2015-11-14
Me too, I used the safe mode trick and now I get BSOD when using Windows in AHCI mode.

---

### Post by allanr on 2015-11-14
Hi guys,
I also got this laptop and I wish that I had found this topic before. This week took me 4 days to be able to install Lubuntu. So I had to take the same steps as jchedstrom pointed out, I did not get the raid mode working on ubuntu at all, so I had to change my windows to AHCI mode using the safe boot. I have not installed the NVIDIA driver yet, anyone tried to install the drives directly from the NVIDIA website?

---

### Post by nate-quicksketch on 2015-11-15
Yay! Add my thanks to the list! I'd tried getting Ubuntu installed for 3 days. Thank you jchedstrom and rocco5!!!

For newbies to Linux like myself, you may also find this guide to upgrading your kernel helpful to get to 4.3 to resolve the microphone and suspend issues (confirmed both are fixed in the 4.3 kernel). [https://github.com/GM-Script-Writer-62850/Ubuntu-Mainline-Kernel-Updater](https://github.com/GM-Script-Writer-62850/Ubuntu-Mainline-Kernel-Updater)

The only thing I'd add here is reporting that the optional USB-C to Ethernet adapter works like a dream. Even in recovery mode or initial installation, Ubuntu detects the dongle as if it were a native Ethernet port. I also dabbled with Fedora 23 while trying to get this working and confirmed the Ethernet adapter works there just as well. The video card issues were nearly the death of me. I'm happy to back using Ubuntu as it seems like it has the best Nvidia driver support thanks to the new graphics-drivers PPA.

---

### Post by rvanderwerf on 2015-11-15
I have external monitor working. Sometimes if I plug in and unplug and plug back it it doesn't see its connected until I reboot.
This is what I did (linuxmint 17.2 but should be same for 15.10 since its a derivative.
1) fresh install 17.2 (I get no issues first boot, after updates touchpad and video have problem if you stay on stock kernel)
2) install 4.3 kernel with skylake support (this makes wireless work although for me only 2.4g)  [http://ubuntuhandbook.org/index.php/2015/11/linux-kernel-4-3-released/](http://ubuntuhandbook.org/index.php/2015/11/linux-kernel-4-3-released/)
3) touchpad will stop working, do touchpad blacklist fix as listed here
4) install nvidia 355 drivers & prime as listed earlier in thread
5) install the prime indicator (I just use it to tell what mode I'm in switching will break stuff)

This was the only route I could consistency get the 'software rendering mode' warning not to pop up on login. It's stuck in nvidia mode but it seems stable. Mic and webcam in chrome hangouts works. Monitor brightness, audio controls on and keyboard backlight controls work too. HDMI external monitor works. Touchpad works. I can't switch between intel and nvidia video without fouling stuff up though - really I just can't get the skylake video to work without errors in the system log and going into software rendering even with 4.3 kernel installed. Nvidia video working well enough until Dell gets better support.

Does anyone have the broadcom wireless drivers for 5g working? mine only sees 2.4 APs. At least that works without futzing on 3.4 kernel. The most annoying part is the hidpi support with an external monitor - if I make the 4k display readable with hidpi the 1920x1200 dell monitor (u2412m) I have looks like it configured for blind people. From I understand that's an X11 problem that cannot be fixed until wayland is incorporated (I've tried some manual stuff with xrandr I've seen posted but they either give me errors or do nothing at all).

Such a beautiful machine, I actually found this model (10000SLV) with 4k disp, i7, and 1tb ssd, 87wh battery at best buy of all places (not out on display but if you search their website some stores have it for pick up). Everything is better than the m3800 except the placement of the webcam!

Has anyone gotten thunderbolt 3/usbc port to work with anything? I honestly don't have anything to even try seems it is so new its hard to find stuff. In theory it might work with 4.3 kernel.

---

### Post by anhdle on 2015-11-15
> **rvanderwerf said:**
> I have external monitor working. Sometimes if I plug in and unplug and plug back it it doesn't see its connected until I reboot.
This is what I did (linuxmint 17.2 but should be same for 15.10 since its a derivative.
1) fresh install 17.2 (I get no issues first boot, after updates touchpad and video have problem if you stay on stock kernel)
2) install 4.3 kernel with skylake support (this makes wireless work although for me only 2.4g)  [http://ubuntuhandbook.org/index.php/2015/11/linux-kernel-4-3-released/](http://ubuntuhandbook.org/index.php/2015/11/linux-kernel-4-3-released/)
3) touchpad will stop working, do touchpad blacklist fix as listed here
4) install nvidia 355 drivers & prime as listed earlier in thread
5) install the prime indicator (I just use it to tell what mode I'm in switching will break stuff)


Unfortunately, I still can't detect external screen (via HDMI) with exactly same procedure on 15.10. I also try to reboot like you say, but still can't :(.

---

### Post by jchedstrom on 2015-11-15
@rvanderwerf, I'm still on kernel 4.2 and have never had any problems with the wifi and use 5GHz regularly. To help diagnose your problem, try installing "wavemon" and run "sudo wavemon" using F3 to switch to scan list. Can you see 5 GHz networks? Also check to make sure the right driver is being loaded. Graphically you can go to network indicator > Connection Information > Interface: 801.aa WiFi (wlp2s0), Driver: brcmfmac. Or in command line "lsmod | grep brcmfmac". Maybe try dropping back to kernel 4.2 and check these things as well. Check 'dmesg' for messages related to error/cfg80211/wlp2s0/brcm/wireless.

While checking my own dmesg, found these messages related to the bluetooth issue:

[   12.833127] bluetooth hci0: Direct firmware load for brcm/BCM-0a5c-6410.hcd failed with error -2
[   12.833129] Bluetooth: hci0: BCM: Patch brcm/BCM-0a5c-6410.hcd not found

[   12.894445] brcmfmac 0000:02:00.0: enabling device (0000 -> 0002)
[   12.902203] brcmfmac 0000:02:00.0: Direct firmware load for brcm/brcmfmac43602-pcie.txt failed with error -2

---

### Post by Annihil on 2015-11-16
I installed kernel 4.3 doing this:
```
wget \
kernel.ubuntu.com/~kernel-ppa/mainline/v4.3-wily/linux-headers-4.3.0-040300_4.3.0-040300.201511020949_all.deb \
kernel.ubuntu.com/~kernel-ppa/mainline/v4.3-wily/linux-headers-4.3.0-040300-generic_4.3.0-040300.201511020949_amd64.deb \
kernel.ubuntu.com/~kernel-ppa/mainline/v4.3-wily/linux-image-4.3.0-040300-generic_4.3.0-040300.201511020949_amd64.deb
sudo dpkg -i linux-headers-4.3*.deb linux-image-4.3*.deb
```

While on kernel 4.3, when I log into the desktop, unity does't load (crash) and return me to the logging screen.
I tried with and without nvidia driver (from the ppa), but with no success.
I've already added nouveau.modeset=0 in the grub, so it cannot be the cause.
By the way it works with kernel 4.2.0-18 and nvidia-355.
What am I doing wrong ?
How did you manage to get kernel 4.3 ?

---

### Post by allanr on 2015-11-16
I think I did exactly what you did, I just followed these steps from [http://ubuntuhandbook.org/index.php/2015/11/linux-kernel-4-3-released/](http://ubuntuhandbook.org/index.php/2015/11/linux-kernel-4-3-released/) 
Right now I am using kernel 4.3, however instead of using nvidia-355 from additional drivers I switched that to nvidia-358. 
Even though my HDMI image is working the sound part is not. Also I tried to download the drives from Intel and use the Intel graphics installer for linux but until now intel only gives support to ubuntu 15.04.

---

### Post by jchedstrom on 2015-11-16
@Annihil, what you're doing seems correct and the same as what a few of us have done to install kernel 4.3. Maybe an update since then has broken it... after testing 4.3 I immediately went back to 4.2. Another possibility is that it has something to do with the order. I did 1) add graphics-drivers/ppa, 2) install nvidia-355 + nvidia-prime 3) install kernel 4.3 (with lots of reboots inbetween).

FYI, I recently started having a  problem where using nivida-prime to switch to Intel graphics results in a blackscreen lockup requiring holding the power button. But it then starts up correctly in Intel.

Still happily using Ubuntu on the laptop despite these issues. Played "War for the Overworld" with Intel GPU for a few hours without issue.

---

### Post by allanr on 2015-11-18
Intel released yesterday the graphics driver for ubuntu 15.10 [https://01.org/linuxgraphics/downloads](https://01.org/linuxgraphics/downloads)
I am testing this right now and even though it is working my screen keep blinking between two and two seconds roughly. Any idea about what it can be?

---

### Post by kjano on 2015-11-18
The tread reminds me why I love the linux community. Laptop is out since a few days and there is already so much information, willingness to help, and fixes. Thanks guys!

I just got my machine to replace my broken macbook pro. 

**Works**:
[LIST]
[*]The screen is super, super glossy but the touchscreen works great.
[*]Mic works after installing kernel 4.3
[*]webcam works but it totally pointless due to its positioning
[*]switching between GPUs works after logging in again
[*]lm-sensors finds some of the sensors
[*]nvidia 355 drivers work okay
[*]hdmi works well
[*]fans work (but see below :-( )
[*] TLP works nicely and should help with the battery.
[/LIST]



**Problems so far**:
[LIST]
[*]Sometimes the screen goes black during login or rebook or if it enters the interactive mode and it will not come back. This is a serious issue for me. Any ideas?
[*]My machine has a very light coil whine. Dell promised so solve this for their xps 13 and m3800 many many times, but my xps 15 still has it. It is pretty light so you really need to focus to hear it. Still, it may turn out to be annoying in the long run.
[*]lm-sensors cannot find the fans, this is certainly concerning and unsurprisingly the fan is rather noisy. It is noticeable when using the intel cpu and I find it distracting. In case of the 960M, it is too loud for me. Especially if you are used to a Macbook Pro where the fan is not audible most of the time. Any ideas how to gain control over the fans? 
[/LIST]

---

### Post by allanr on 2015-11-19
Right now I am having the two following problems:

- Have you guys tested the hdmi with a vga using a projector? When I go to  "Displays" I can verify that ubuntu detected other screen however It does not work. The projector does not detect that there is a computer plugged in. 
- Also using kernel 4.3 my intel graphics is unstable. Even though it mostly works, once a while it blinks. I have noticed that sometimes this blinking pattern increases or decreases depending on what I am doing.

Any ideas about these problems?

---

### Post by zeratul2 on 2015-11-19
Just got my XPS 15 today and started installing Ubuntu 15.10 dual boot with Win 10.
nvidia drivers 355 and 358 are all beta and testing show that. I need a stable system.
I found that nvidia released 352.63 on Nov 13. This one has in the release spec:
> 
Fixed a regression that prevented DPMS from working correctly on some DisplayPort displays.
Fixed a bug that could prevent X from starting when configured with multiple X screens, some of which scan out to display devices, and some of which do not.
Fixed a bug that could cause texture corruption in some OpenGL applications when video memory is exhausted by a combination of simultaneously running graphical and compute workloads.

And it officially supports GeForce GTX 960M. See here: [http://www.nvidia.com/download/driverResults.aspx/95159/en-us](http://www.nvidia.com/download/driverResults.aspx/95159/en-us)
It is now part of the official Ubuntu 15.10 updates repository.
So for step 8 of the guide, simply open 'drivers' and install the proposed nvidia driver 352.63 or run 
sudo apt-get update && sudo apt-get install nvidia-352
My system is on 352 and it's working fine. Will continue testing.

Update: I have to stay on kernel 4.2 for 352, doesn't seem to be 4.3 compatible .. black screen.
I also got black screen with 355 and 358 on any kernel.

---

### Post by kjano on 2015-11-19
> **zeratul2 said:**
> 
I also got black screen with 355 and 358 on any kernel.

I have the black screen issue from time to time as well, see my post above with kernel 4.3 and nvidia 355. A hard off (not restart) will fix this. You can also simply key in your password and press enter and unity will show up. Alternatively, you can connect an external screen via hdmi as this will also bring back the notebook screen...don't ask me why. The microphone does not work on 4.2 so this is not an option for me.

Edit: okay, here are some updates. There are cases in which a hard off and restart will not fix the issue and where the only way seems to be to add the hdmi screen. Since today, I also cannot switch the resolution any more when using the nvidia card. Nvidia-settings does not provide this option at all (but I know it is there) and just using the display setting makes the screen turn black. For me, this is a more or less a killer. Any ideas?

@jchedstrom: any updates form your side?

Okay, some first updates. This seems to be a common problem for the xps13 as well which does not have an nvidia card, see, e.g., :

[http://en.community.dell.com/support-forums/laptop/f/3519/t/19644781](http://en.community.dell.com/support-forums/laptop/f/3519/t/19644781)
[http://askubuntu.com/questions/654482/dell-xps-13-2015-black-screen](http://askubuntu.com/questions/654482/dell-xps-13-2015-black-screen)
[http://askubuntu.com/questions/668479/dell-xps-13-2015-qhd-black-screen-with-linux](http://askubuntu.com/questions/668479/dell-xps-13-2015-qhd-black-screen-with-linux)

One idea is to blindly open a shell and type xset dpms force off but this is hardly a good solution. 

An askubuntu user writes:

> 
I have actually put a custom script and associated that to ctrl+super+s to restart the screen. 'xset dpms force off; sleep 1; xset dpms force on' – Omer Akram Sep 6 at 14:37

Okay, I just tried this with and created my custom script. It works 50% of the time but not always :-(. I also updated the BIOS, still no progress.

Edit: okay, just to keep everybody posted, here is the bug report: bugs.launchpad.net/ubuntu/+source/linux/+bug/1507073 and a topic on the same issue for the ArchLinux community [https://bbs.archlinux.org/viewtopic.php?pid=1577415#p1577415](https://bbs.archlinux.org/viewtopic.php?pid=1577415#p1577415) .

Edit 2: okay, here is a 'solution': Make sure suspend is set as action for closing the lid in the power settings. Next time when you run in the black screen problem during boot or when changing display settings, simply close the lid and open it again. You may have to do this 1-3 times but it seems to work. Far from perfect but better than nothing.

---

### Post by rvanderwerf on 2015-11-20
yes I installed wavemon and when I see 2.4 ghz aps only. 4.2 doesn't seem to make any diff on the wifi.

here the output from lsmod
rvanderwerf@rvanderwerf-XPS-15-9550 ~ $ lsmod |grep brcmfmac
brcmfmac              278528  0 
brcmutil               16384  1 brcmfmac
cfg80211              536576  1 brcmfmac

I'm wondering if I can just ditch the installed dell 1830 for an intel card?

also I grabbed 1.0.7 firmware today and loaded it. Also installed the elan touch FW A00_ZPE as well. 


> **jchedstrom said:**
> @rvanderwerf, I'm still on kernel 4.2 and have never had any problems with the wifi and use 5GHz regularly. To help diagnose your problem, try installing "wavemon" and run "sudo wavemon" using F3 to switch to scan list. Can you see 5 GHz networks? Also check to make sure the right driver is being loaded. Graphically you can go to network indicator > Connection Information > Interface: 801.aa WiFi (wlp2s0), Driver: brcmfmac. Or in command line "lsmod | grep brcmfmac". Maybe try dropping back to kernel 4.2 and check these things as well. Check 'dmesg' for messages related to error/cfg80211/wlp2s0/brcm/wireless.

While checking my own dmesg, found these messages related to the bluetooth issue:

[   12.833127] bluetooth hci0: Direct firmware load for brcm/BCM-0a5c-6410.hcd failed with error -2
[   12.833129] Bluetooth: hci0: BCM: Patch brcm/BCM-0a5c-6410.hcd not found

[   12.894445] brcmfmac 0000:02:00.0: enabling device (0000 -> 0002)
[   12.902203] brcmfmac 0000:02:00.0: Direct firmware load for brcm/brcmfmac43602-pcie.txt failed with error -2

---

### Post by zeratul2 on 2015-11-20
> **rvanderwerf said:**
> yes I installed wavemon and when I see 2.4 ghz aps only. 4.2 doesn't seem to make any diff on the wifi.

I am on stock kernel 4.2 (-18) and the broadcom card sees and connects to 5Ghz access points just fine (as well as 2.4Ghz).

Perhaps this is an issue with channels (wrong country setting?)?

As for the black screen issue, when I first installed 355 or 358 I really had it 100% of the time. I never managed to get the login screen. Note that I am using Ubuntu gnome, which uses gdm instead of lightdm for login management. No I never tried logging in blindly, but it's no acceptable solution for me.

I must say that both nouveau and 352.63 are more stable than the beta 355 and beta 358. Those drivers are older and only add support for new graphics cards, which we don't have, so why bother?

---

### Post by rvanderwerf on 2015-11-20
hmm how do I tell what country my driver thinks its on?

---

### Post by zeratul2 on 2015-11-20
Allright good progress:

Still on Nvidia 352.63.  Installed the Intel drivers (link above). Upgraded bios from Windows.
Nothing noticably changed, expect intel driver now has hardware decoding (VAAPI).
Tried again with the 4.3 kernel listed above, black screen.

But using the 4.3 kernel I found (link below), all problems went away: no more black screen, and suspend/resume works perfect. Systems boots perfect, tried already 10 times.
It works perfect with NVidia Prime, intel or nvidia card active.

[http://kernel.ubuntu.com/~kernel-ppa/mainline/drm-intel-nightly/2015-11-13-wily/](http://kernel.ubuntu.com/~kernel-ppa/mainline/drm-intel-nightly/2015-11-13-wily/)
so download and install
cd /tmp
wget [http://kernel.ubuntu.com/~kernel-ppa/mainline/drm-intel-nightly/2015-11-13-wily/linux-headers-4.3.0-994_4.3.0-994.201511122102_all.deb](http://kernel.ubuntu.com/~kernel-ppa/mainline/drm-intel-nightly/2015-11-13-wily/linux-headers-4.3.0-994_4.3.0-994.201511122102_all.deb) [http://kernel.ubuntu.com/~kernel-ppa/mainline/drm-intel-nightly/2015-11-13-wily/linux-headers-4.3.0-994-generic_4.3.0-994.201511122102_amd64.deb](http://kernel.ubuntu.com/~kernel-ppa/mainline/drm-intel-nightly/2015-11-13-wily/linux-headers-4.3.0-994-generic_4.3.0-994.201511122102_amd64.deb) [http://kernel.ubuntu.com/~kernel-ppa/mainline/drm-intel-nightly/2015-11-13-wily/linux-image-4.3.0-994-generic_4.3.0-994.201511122102_amd64.deb](http://kernel.ubuntu.com/~kernel-ppa/mainline/drm-intel-nightly/2015-11-13-wily/linux-image-4.3.0-994-generic_4.3.0-994.201511122102_amd64.deb)
sudo dpkg -i *deb 
If you still had the previous 4.3 kernel, uninstall it because it remains the default or select Other linux in grub menu to try this kernel first.

I will continue testing.

---

### Post by Annihil on 2015-11-21
Had the same problem, black screen with 4.3 from mainline release (link I posted), so I decided to went back to 4.2.
But indeed kernel 4.3 from drm-intel-nightly works like a charm, even with nvidia-358 driver.
Suspend also works out of the box, didn't experienced blackscreen since :)
Thank you !

---

### Post by parallelo on 2015-11-21
Anyone having luck with Bluetooth yet?  I've seen some MacBook Ubuntu users with the same BCM hardware modifying the driver source code and building custom kernel modules.  Can't find the link I was reading yesterday...

But overall, the XPS 15 9550 has turned out to be a really nice Linux machine!

---

### Post by Tachyon on 2015-11-21
I have the 9550 with touch, UHD, but i5 processor and 8 GB of RAM on 256 GB SSD. I'm really glad I found this topic, because I was very frustrated by the weird experience of not seeing my SSD in the live environment! Like many of you, I ordered the XPS 15 because of Dell's track record with Ubuntu. (I am upgrading from an 8-year-old *Inspiron 6400*!)

I followed the steps here (switched SATA mode, turned off Auto OS Recovery Threshold, added [font=courier]nouveau.modeset=0[/font]) and now have 15.10 installed successfully alongside Windows 10. I was able to boot back into Windows after cycling through safe mode like others have reported. I had one BSOD and one boot where the sound wasn't working. However, in subsequent boots, Windows seems stable. (And I made a system image before anyway.)

Here's some observations to add to the record. Nothing new, really, but I wanted to add another data point and express my gratitude for all the information here that helped me get Ubuntu working.

[jschedstrom's original post](http://ubuntuforums.org/showthread.php?p=13382949#post13382949) mentions it, but just to reiterate: after installing Ubuntu, you must go back into the BIOS and manually add the boot option and path to Ubuntu's boot file. The BIOS is not going to pick this up for you; this confused me at first until I went back and reread the post in more detail. ;)

Upgrading to 4.3 also fixed suspend/resume and mic for me. As others reported above, I needed a more recent nightly (4.3.0-994) to avoid getting a black screen on boot. I'm using Nvidia Prime 355.11 per jschedstrom's original post. I don't seem to have any problems with external HDMI output. Bluetooth also giving errors in dmesg for me.

Projected battery life wasn't great (a little under 4 hours), but that might be partly because I was downloading/installing a bunch of kernels and rebooting a whole bunch. And to be honest after a couple of years of having a heavy computer with a battery that lasts about 30 minutes (on a good day), 4 hours seems like forever to me. :P

One difference from other reports here: **my touchpad worked out of the box, albeit intermittently**. On some boots it was fine; on others it was absent. (Touchscreen always worked, yay!) Following the steps for fixing the touchpad per jschedstrom's post resolved this issue, so even if your touchpad works on first boot, I recommend still doing that

Also, after upgrading to 4.3 I receive a "system problem" when rebooting. It seems to be related to plymouthd, and I found [an existing bug report](https://bugs.launchpad.net/ubuntu/+source/plymouth/+bug/1223714).

I'm going to try installing some of my favourite programs and playing around now. Will report back if I find anything new.

Anyone know how to get the 4K device scaling to work on the login screen on first boot? I notice it works after resume from suspend (presumably because I'm already logged in). Not a huge deal

---

### Post by zeratul2 on 2015-11-22
I'm on the intel GPU (nvidia-prime) and manage 7 hours of battery life with light usage.. web browsing, some terminal work, etc.I've only disabled bluetooth (which was working fine btw)
I will optimize further power management of usb, sound, wifi etc, but there's no hurry. I guess 8-9 hours should be doable.

---

### Post by allanr on 2015-11-22
I installed the new intel drives using *Intel graphics installer for linux* and now when I am using Unity with Intel graphics, once a while I get a black screen (it blinks). I tried to reinstall but without success. I also tested the opengl and it seems the intel drives only give supports to opengl 3, however it should be opengl 4, following the intel specification for the skylake processor. I do not know if it is only a problem related to the version of mesa-drivers. Does anyone have an idea about these problems?

---

### Post by joshuabc on 2015-11-23
I've been using my 9550 daily for the past 2 weeks. Most of the solutions posted here were caveats I had anticipated, having some familiarity with Dell's particular EFI implementation. The Nouveau modeset flag took a minute - I wish I had read OP's post! 

This machine's EFI implementation is a very good one, as a matter of fact. However unfriendly it may seem, the simple inclusion of a hotkey to boot into EFI configuration is a huge bonus over certain other brands. Mine came gift-wrapped from my employer, but it appears to be the same one sold in the Microsoft store - no bloatware. Not that I kept the Windows partition or anything. But that can often determine which EFI options one has access to - specifically the TPM defeat, configurable boot target and "secure" boot. 

On as side note here, enabling AHCI does NOT make a difference in performance. Not at all. AHCI emulation enables some OSs to recognize the drive at boot time (or inside a rescue env), but any modern Linux kernel or Windows version will see the device as a directly-connected PCIe flash device and recognize the NVMe extensions. It should be possible to disable AHCI and still boot Linux, though with no real motivation to do so, I have not. It's really, stupid fast!

As for the 4.3 kernel found in the "mainline" ppa, it should not be expected to work if you are using any DKMS at all. That's because the mainline kernel binaries in that PPA are built against the most recent LTS release, while DKMS are built on the installation target (hence the D for Dynamic). So unless you are running LTS, you won't be able to use such things as Nvidia's closed-source drivers, OpenZFS or whatever else you might need. The best solution, of course, is to simply build the same kernel yourself, with Ubuntu's big patches applied, using the default config. This will give you, for all intents and purposes, the same kernel with exactly the same features enabled. The David Arlie branch (called "DRM" and linked to above) may show considerably more instability. His branch contains a lot of patches to the open-source ATI drivers, Intel graphics drivers and others. It is always under heavy development and can never be considered production-ready, interesting as it may be.

Since my primary focus is, in fact, kernel development (Thunderbolt, Infiniband and whatnot, specifically), I don't even hope for stability half of the time. When I need it on this box, I use the mainline 4.3 built under Wily. It's been extremely solid. No wireless issues on 5GHz bands. Power consumption seems par for the course with p_states and thermald enabled. Turning off turbo boost makes a difference, but turning down the display makes a huge difference. I think it's too pretty to turn down, myself, so I just plug the thing in.

---

### Post by Annihil on 2015-11-23
> **joshuabc said:**
> the simple inclusion of a hotkey to boot into EFI configuration is a huge bonus over certain other brands.
What do you mean, are you talking about the one-time boot menu (F12 hotkey) which let you select UEFI boot (Windows Boot Manager / Linux) ?
Or you can bind an hotkey for each entry without having to go throught that menu and I am not aware of that possibility ?

---

### Post by joshuabc on 2015-11-23
> **Annihil said:**
> ...are you talking about the one-time boot menu (F12 hotkey) which let you select UEFI boot (Windows Boot Manager / Linux) ?
Or you can bind an hotkey for each entry...

No, unfortunately, that would take some effort. I was talking about the F12 boot menu. There are a bunch of newer devices that require you to boot into an OS, then instruct the system to boot into "maintenance" or "recovery" mode in order to access anything other than the default. In addition, I have not seen any notebook with a more feature-complete EFI setup interface. The ability to select targets within the EFI boot partition makes customization entirely possible - perhaps a hotkey setup as you mentioned or an alternative GUI for Grub. Or a new bootloader. It just requires some motivated, young programmer with some extra time on their hands. That would not be me.

---

### Post by kjano on 2015-11-23
> **Annihil said:**
> Had the same problem, black screen with 4.3 from mainline release (link I posted), so I decided to went back to 4.2.
But indeed kernel 4.3 from drm-intel-nightly works like a charm, even with nvidia-358 driver.
Suspend also works out of the box, didn't experienced blackscreen since :)
Thank you !

Hmm, it fixed the black screen problem for me but switching between two screens and using two screens is still a nightmare. I get many error messages, the screen sometimes turns  black of flickers,and in about 1 of 4 cases the entire system will freeze. On restart I will also get error messages that the saved screen configuration is not valid. This is really a huge issue for me as I need two screens and regularly connect to a projector. Which kernel exactly are you using, can you send a link? Btw, I am using Nvidia 352.63. In nvidia-settings I cannot change the resolution but have to use the default unity application for that.

---

### Post by joshuabc on 2015-11-24
> **allanr said:**
> ...it seems the intel drives only give supports to opengl 3, however it should be opengl 4, following the intel specification for the skylake processor.

Mesa is, in theory, feature-complete up to GL4.2. The open-source drivers, for the most part, do not implement all of GL4.0, let alone 4.4 or 4.5. See [http://mesamatrix.net/](http://mesamatrix.net/) for details.

---

### Post by zeratul2 on 2015-11-24
> **joshuabc said:**
> 
Since my primary focus is, in fact, kernel development (Thunderbolt, Infiniband and whatnot, specifically), I don't even hope for stability half of the time. When I need it on this box, I use the mainline 4.3 built under Wily. It's been extremely solid. No wireless issues on 5GHz bands. Power consumption seems par for the course with p_states and thermald enabled. Turning off turbo boost makes a difference, but turning down the display makes a huge difference. I think it's too pretty to turn down, myself, so I just plug the thing in.
What do you mean with "mainline 4.3"?
Is it the link from earlier in this topic? Because that is very unstable for me, no suspend, black screen etc. I wonder were the differences originate from.

---

### Post by kjano on 2015-11-24
Can anybody confirm that they got HDMI working to a degree where it is possible to connect to external displays and projectors and change the resolution without running into serious issues 50% of the time?

---

### Post by joshuabc on 2015-11-24
> **zeratul2 said:**
> What do you mean with "mainline 4.3"?
Is it the link from earlier in this topic? Because that is very unstable for me, no suspend, black screen etc. I wonder were the differences originate from.

There were 2 links earlier in the thread - one for the "mainline" 4.3.x kernel binaries and one for the "drm" kernel binaries. The problem with the "mainline" kernel is that it is not built with the same version of GCC that is shipped with Ubuntu 15.10. It is built against the most recent LTS release. At least that has been the case historically - it's always possible they have changed their practices since it is not meant for end-user consumption. The problem there is what's called the ABI - the interface used by the 15.10 kernel is different from that of the LTS kernel. There is a bit of code in every DKMS module that must target the specific kernel you are running. This acts as an intermediary between the proprietary Nvidia binary blob and your running kernel. If they don't quite speak the same language, you get no graphics. Bummer.

The "drm" kernel is a kernel.org development branch used primarily for open-source graphics driver development. I do not know which version of GCC/Ubuntu those binaries were built against. It sounds like it must be native to 15.10, since there are reports of people using Nvidia drivers. I would not expect stability from that kernel branch, but if you find it stable enough, go right ahead and use it.

What I opted for was the "mainline" kernel, but I compiled it on my notebook. I used the default Ubuntu 15.10 config file from the latest 4.2.x kernel and added or subtracted options as I felt necessary. I then installed the latest Nvidia 358 drivers, the latest Intel drivers from 01.org, the latest Intel microcode from the same place, along with thermald. It has been 100% stable under both graphics cards. It will suspend and resume. Wifi and bluetooth work. The touchpad is still an issue, so I turned it off. Removing i2c_hid did not fix it. A quick HDMI test worked just fine - at the same 4k resolution, but at 30Hz. 

I'm happy to share my kernel config file. There are plenty of howtos out there to help as well. It's not half as daunting as it sounds to build a kernel.

---

### Post by zeratul2 on 2015-11-25
> **joshuabc said:**
> There were 2 links earlier in the thread - one for the "mainline" 4.3.x kernel binaries and one for the "drm" kernel binaries. The problem with the "mainline" kernel is that it is not built with the same version of GCC that is shipped with Ubuntu 15.10. It is built against the most recent LTS release. At least that has been the case historically - it's always possible they have changed their practices since it is not meant for end-user consumption. The problem there is what's called the ABI - the interface used by the 15.10 kernel is different from that of the LTS kernel. There is a bit of code in every DKMS module that must target the specific kernel you are running. This acts as an intermediary between the proprietary Nvidia binary blob and your running kernel. If they don't quite speak the same language, you get no graphics. Bummer.

The "drm" kernel is a kernel.org development branch used primarily for open-source graphics driver development. I do not know which version of GCC/Ubuntu those binaries were built against. It sounds like it must be native to 15.10, since there are reports of people using Nvidia drivers. I would not expect stability from that kernel branch, but if you find it stable enough, go right ahead and use it.

What I opted for was the "mainline" kernel, but I compiled it on my notebook. I used the default Ubuntu 15.10 config file from the latest 4.2.x kernel and added or subtracted options as I felt necessary. I then installed the latest Nvidia 358 drivers, the latest Intel drivers from 01.org, the latest Intel microcode from the same place, along with thermald. It has been 100% stable under both graphics cards. It will suspend and resume. Wifi and bluetooth work. The touchpad is still an issue, so I turned it off. Removing i2c_hid did not fix it. A quick HDMI test worked just fine - at the same 4k resolution, but at 30Hz. 

I'm happy to share my kernel config file. There are plenty of howtos out there to help as well. It's not half as daunting as it sounds to build a kernel.

Thank you for this clear update. I've compiled and updated kernels many times in the past. Should be no issue. But perhaps we could investigate setting up a xps-15-9550 ppa repository, so everyone immediately benefits when we make a new kernel or patch a bug. I guess we'll all use this laptop for a couple of years - definitely worth it.

---

### Post by Brad_Harris on 2015-11-25
> **joshuabc said:**
> There were 2 links earlier in the thread - one for the "mainline" 4.3.x kernel binaries and one for the "drm" kernel binaries. The problem with the "mainline" kernel is that it is not built with the same version of GCC that is shipped with Ubuntu 15.10. It is built against the most recent LTS release. At least that has been the case historically - it's always possible they have changed their practices since it is not meant for end-user consumption. The problem there is what's called the ABI - the interface used by the 15.10 kernel is different from that of the LTS kernel. There is a bit of code in every DKMS module that must target the specific kernel you are running. This acts as an intermediary between the proprietary Nvidia binary blob and your running kernel. If they don't quite speak the same language, you get no graphics. Bummer.

The "drm" kernel is a kernel.org development branch used primarily for open-source graphics driver development. I do not know which version of GCC/Ubuntu those binaries were built against. It sounds like it must be native to 15.10, since there are reports of people using Nvidia drivers. I would not expect stability from that kernel branch, but if you find it stable enough, go right ahead and use it.

What I opted for was the "mainline" kernel, but I compiled it on my notebook. I used the default Ubuntu 15.10 config file from the latest 4.2.x kernel and added or subtracted options as I felt necessary. I then installed the latest Nvidia 358 drivers, the latest Intel drivers from 01.org, the latest Intel microcode from the same place, along with thermald. It has been 100% stable under both graphics cards. It will suspend and resume. Wifi and bluetooth work. The touchpad is still an issue, so I turned it off. Removing i2c_hid did not fix it. A quick HDMI test worked just fine - at the same 4k resolution, but at 30Hz. 

I'm happy to share my kernel config file. There are plenty of howtos out there to help as well. It's not half as daunting as it sounds to build a kernel.

Yes please! Could you share your kernel config file? I am running mainline 4.3 kernel and it is fairly unstable, I am hoping if I also compile it myself I will reap the rewards!

---

### Post by linxaddict2 on 2015-11-25
I tried to install Ubuntu on my dell, but unfortunately installer doesn't see my disk and its partitions. I switched to AHCI and disabled secure boot but it didn't help and there was no /dev/nvme0n1. What could be the cause? GParted see all the partitions. I'd be grateful if someone could help me with this one.

---

### Post by rvanderwerf on 2015-11-25
> **kjano said:**
> Can anybody confirm that they got HDMI working to a degree where it is possible to connect to external displays and projectors and change the resolution without running into serious issues 50% of the time?

yes but only in nvidia driver mode. Intel seems OK if I am single screen but goes bonkers quite a bit with 2 displays. Since I am plugging in when using my external display it's not a big deal for me.

btw I installed ubuntu 15.10 with the 4.3 nightly kernel links for 994 and everything works. Linuxmint was packaging an older wireless driver and it didn't see 5G hotspots, but ubuntu's newer one works fine. I'm sticking with Ubuntu until LM/cinnamon gets sorted out. At least everything is working on ubuntu now. (Nvidia 352-updates, lintel drivers listed above and prime-indicator all work).

when you boot off the USB stick be sure to pick the USB stick from under the 'UEFI' options and not the legacy ones. After install if you cannot boot to grub boot off the livecd again, and install the boot-repair tool and it should fix you up. [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

### Post by anhdle on 2015-11-25
Do you have to anything extra to get the second screen to be detected? I'm in nvidia mode, kernel 4.3, Ubuntu 15.10 but can't detect the second screen at all. I tried both 355 and 352 nvidia drivers.

---

### Post by linxaddict2 on 2015-11-26
> **rvanderwerf said:**
> when you boot off the USB stick be sure to pick the USB stick from under the 'UEFI' options and not the legacy ones. After install if you cannot boot to grub boot off the livecd again, and install the boot-repair tool and it should fix you up. [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

I boot off usb stick using the UEFI option. After the ubuntu live launches, I can see my disks in gparted (/dev/sda /dev/sdb), partitions are correctly detected (/dev/sdb1, /dev/sdb2 and so on) and I can mount them, but the Ubuntu installer doesn't see them.

---

### Post by rvanderwerf on 2015-11-26
hmm if I disable secure boot, check enable legacy rom, boot 15.10 off UEFI options, I see them. If I boot usb legacy 15.10, the partition tool in installer behaves like you say. Not sure what to say, I've installled and re-installed ubuntu 15.10 and LM 7.2 a dozen times and didn't see that. I did have to do boot-repair after an ubuntu 15.10 install though.

---

### Post by JohnReid on 2015-11-26
I had some problems following the above method to install Ubuntu 15.10 on my new XPS15. I did manage to install it inside Windows on a VMware workstation. This isn't my preferred option but it is working. I wonder if anyone here knows if there will be any major drawbacks with this approach?

Thanks in advance,
John.

---

### Post by anhdle on 2015-11-26
I've been using VMWare workstation pro for over a year for Ubuntu but I have to buy a new laptop to install real ubuntu on cos of its horror. It freezes a lot especially after exiting and can only use half of your total RAM. For testing, VMWare is ok, but for development, hell no!

---

### Post by allanr on 2015-11-28
> **joshuabc said:**
> Mesa is, in theory, feature-complete up to GL4.2. The open-source drivers, for the most part, do not implement all of GL4.0, let alone 4.4 or 4.5. See [http://mesamatrix.net/](http://mesamatrix.net/) for details.

Thank you for clarifying. I think it will take a while until it supports GL 4.0.

> **linxaddict2 said:**
> I boot off usb stick using the UEFI option. After the ubuntu live launches, I can see my disks in gparted (/dev/sda /dev/sdb), partitions are correctly detected (/dev/sdb1, /dev/sdb2 and so on) and I can mount them, but the Ubuntu installer doesn't see them.

Did you disable the fast boot? [http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html](http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html)
When fast boot is turned on, it does not even allow me to mount the windows partition from my ubuntu. Make sure it is turned off.

I do not know where you are creating your bootable usb, but you have created several (ubuntu mate, lubuntu, ubuntu) and it detects my ssd drive in all the cases. Try to use the win32 disk imager [http://sourceforge.net/projects/win32diskimager/](http://sourceforge.net/projects/win32diskimager/)

---

### Post by quickdry21 on 2015-11-29
To start, thank you so much to the people in this thread, because of you I have Ubuntu running on the only laptop I could find that is a viable alternative to a MBP. The guides / comments in this thread got my XPS 15 9550 i7, 16GB ram, QHD+ touch screen laptop working amazingly (equal to or better than my previous setup, Ubuntu 15.04 on a 2014 MBP) - this machine has been truly awesome so far, great for development.

Now, I would like to add my observations / issues. 

Bluetooth is very spotty. I was able to pair+connect my Nexus 6 once - after that it would no longer connect. Tried unpairing and now they won't even see each other - this is probably more driver related but it's not a huge issue for me, was mostly hoping to use it for Trusted Devices.

The main issue / annoyance I'm running into is warm boots (restarting). Whenever I restart the laptop, the hard drive is not recognized by the BIOS during POST. Initially on a restart, the laptop would enter Auto OS Recovery (SupportAssist). The first screen would display "Initializing PCIe" and then automatically move to a screen that said "Hard Drive - Not Installed". When hitting the only button, "Continue", another screen would flash that I couldn't quite make out the contents of and the computer would shut off. When turning it back on, it would boot normally, without issues.

I've tried setting fastboot to auto, didn't make a difference.

I tried disabling the BIOS Auto OS Recovery option - now, instead of SupportAssist showing up it shows a screen that says something like Hard drive not found and has a few options, one of them being F2 to boot to settings. After booting to settings and exiting again, it again boots normally.

What leads me to believe this is a warm vs. cold boot issue is that when restarting from Ubuntu, the power button light remains on throughout shutdown and into POST. When the bad reboots happened, going into SupportAssist or the black hard drive not found error screen, when an option is selected the computer shuts off (power button light goes out) and then comes back on and booting into grub works fine.

I was wondering if anyone else has witnessed anything like this. I'm hoping I don't have to worry about it as it seems so far to be completely deterministic, shutting down then starting up never has the issue, where as a reboot from Ubuntu causes it to happens every time - I assume this is a software issue. I'm not a wizard at lower level Linux OS stuff such as this so I'm curious to hear others input.

One last thing, as previously mentioned in this thread, the POST time is noticeably **slow**. The time before starting and when the Dell logo displays takes 5-10 seconds, don't think this is related to grub / Linux / Ubuntu. It does seem to be much worse when rebooting as opposed to a cold boot.

EDIT: Wanted to mention I followed the [original guide]("http://ubuntuforums.org/showthread.php?t=2301071&p=13382949#post13382949") by [jchedstrom]("http://ubuntuforums.org/member.php?u=865321") to a tee.

---

### Post by shamil.si on 2015-11-29
I've exactly same problem. Downgrading the BIOS to version 1.0.0 fixes the reboot issue for  me.
Also, try to run Diagnostics utility, do you get any Hard-Drive errors? I do, maybe it's related...

---

### Post by kjano on 2015-11-30
> **anhdle said:**
> Do you have to anything extra to get the second screen to be detected? I'm in nvidia mode, kernel 4.3, Ubuntu 15.10 but can't detect the second screen at all. I tried both 355 and 352 nvidia drivers.

Boot, then connect over hdmi, if this does not work, press FN+F8 (you may have to press it multiple times). You can also go into Ubuntu's display settings tool and click on detect display.

---

### Post by quickdry21 on 2015-11-30
Apparently I should have knocked on wood when I said I only had one issue. 

As mentioned by some others here, I can't get HDMI working for the life of me. Whenever I plug my monitor in with HDMI both the laptop and external monitors go dark (flicker a wee bit). Exact same issue when booting up with it plugged in as well as plugging it in after boot. I'm able to CTRL+ALT+F1 into a terminal, and looking at syslog it looks like a kernel crash, something about Tainted Xorg and a few stack traces. 

I'm running Ubuntu Gnome with the stock 4.2 kernel - I haven't tired 4.3. For those of you reporting HDMI working - I assume you are on 4.3? Is there anyone out there with 4.2 and working HDMI?

When booting up and shutting down the Gnome loading and exiting screens show up fine.

I closely followed the original guide, the attempts so far have only been with Prime selecting the NVIDIA GPU. I've tried NVIDIA 352 and 355, neither seemed to make any difference.

Can anyone point me in the right direction - any of you with working HDMI have to take extra steps?

---

### Post by rvanderwerf on 2015-12-01
I have same setup as you EXCEPT I have the 4.3 994 nightly installed in the link earlier in the thread. I would try that. I've also gotten files borked up enough and couldn't find them all I did a fresh re-install to get nvidia working again.

UPDATE: well I spoke too soon. After the latest updates I can no longer get dual monitors with NVIDIA 352.63 working without Xorg crashing and sending me back to the login screen. Even plugging in the monitor does this. I am using Intel drivers with 2 monitors now, but they are very buggy and have painting issues in chrome here and there. They also hard-freeze the system sometimes with dual monitors or crash upon resuming when the screensaver kicks in. Argh.
- update after some tinkering and back and forth with prime-switch 2 monitors on nvidia is working again. I'm not sure what I did but definitely don't boot with the second display attached I am guessing. It could be some X display settings that's crashing stuff maybe. I guess you'd say the situation is 'unstable' lol. Has anyone tried the newer intel-drm-nightly 4.3 kernels? I'm temped but it's playing with fire ](*,)

---

### Post by kjano on 2015-12-02
I am using  kernel 4.3 994 and nvidia 352.63. I have huge HDMI issues when switching between screens and connecting a projector. Sometimes it will work very well other times it will not. Often this can be resolved by clicking FN+F8 a few times and changing the display settings in Unity back and forth. Other times, I have to rebook (often more than one time)....: -(

---

### Post by 7ql6 on 2015-12-03
Can anybody tell me whether or how often the fans start on regular "office work"?
Is the XPS 15 silent, noisy or inbetween?

I'm usually looking for notebooks that are, also under Linux, silent but it seems that not many people are talking about XPS 15 when it goes about "noisyness".

Thank you in advance

---

### Post by anthony-towler on 2015-12-03
> **7ql6 said:**
> Can anybody tell me whether or how often the fans start on regular "office work"?
Is the XPS 15 silent, noisy or inbetween?

I'm usually looking for notebooks that are, also under Linux, silent but it seems that not many people are talking about XPS 15 when it goes about "noisyness".

Thank you in advance

I've never heard the fans kick in while web browsing or programming. I compiled the mainline 4.3 kernel (which pegged all 4 cores for about 45 minutes) and the fans of course kicked in, but they are very quiet. In fact, I could barely hear the fans, even in the quiet office I work in.

---

### Post by quickdry21 on 2015-12-03
> **7ql6 said:**
> Can anybody tell me whether or how often the fans start on regular "office work"?
Is the XPS 15 silent, noisy or inbetween?

I'm usually looking for notebooks that are, also under Linux, silent but it seems that not many people are talking about XPS 15 when it goes about "noisyness".

Thank you in advance

I can confirm that this is a very silent machine. Running a not small software stack (~25-30 processes), IntelliJ, Chrome and Firefox all day, I haven't yet noticed hearing the fans.

Running the same setup on a Mackbook Pro (2014 - 11,2), my previous machine, was *loud* compared to this.

---

### Post by kjano on 2015-12-03
> **7ql6 said:**
> Can anybody tell me whether or how often the fans start on regular "office work"?
Is the XPS 15 silent, noisy or inbetween?

I'm usually looking for notebooks that are, also under Linux, silent but it seems that not many people are talking about XPS 15 when it goes about "noisyness".

Thank you in advance

I am very sensitive to noise as it distracts me from working and was worrying about exactly this. I had a Macbook Pro before and for everyday work (programming, latex, etc) the XPS 15 is silent but not as silent as a Macbook Pro. Essentially, you will hear the fans most of the time but they are (typically) not distracting. Under heavy workload the system will become increasingly loud but the level is (almost) always acceptable. Summing up, noise is not a major issue on this machine but if you are super sensitive to noise, you will notice it.

---

### Post by quickdry21 on 2015-12-03
> **rvanderwerf said:**
> I have same setup as you EXCEPT I have the 4.3 994 nightly installed in the link earlier in the thread. I would try that. I've also gotten files borked up enough and couldn't find them all I did a fresh re-install to get nvidia working again.

UPDATE: well I spoke too soon. After the latest updates I can no longer get dual monitors with NVIDIA 352.63 working without Xorg crashing and sending me back to the login screen. Even plugging in the monitor does this. I am using Intel drivers with 2 monitors now, but they are very buggy and have painting issues in chrome here and there. They also hard-freeze the system sometimes with dual monitors or crash upon resuming when the screensaver kicks in. Argh.
- update after some tinkering and back and forth with prime-switch 2 monitors on nvidia is working again. I'm not sure what I did but definitely don't boot with the second display attached I am guessing. It could be some X display settings that's crashing stuff maybe. I guess you'd say the situation is 'unstable' lol. Has anyone tried the newer intel-drm-nightly 4.3 kernels? I'm temped but it's playing with fire ](*,)

Could you (or anyone) point me towards installing 4.3 994 nightly? I'm guessing this isn't a simple .deb install (or at least I couldn't find any such .deb), but a compile? If it's a .deb install, I can figure it out if you can point me towards the files. If not, pointing me at a guide or set of steps to compile would be awesome. 

I haven't compiled Linux myself before, but I'm competent enough to figure it out (or my overconfidence will lead to the following :D)

EDIT: to clarify, compile for Ubuntu 15.10

[IMG]https://imgs.xkcd.com/comics/success.png[/IMG]

---

### Post by kjano on 2015-12-04
Hi quickdry21,

we have been discussing different kernels here. I assume you are interested in 4.3.0-994-generic, right? You should still be able to get it from [http://kernel.ubuntu.com/~kernel-ppa...-intel-nightly](http://kernel.ubuntu.com/~kernel-ppa...-intel-nightly). I think you can try this one first: [http://kernel.ubuntu.com/~kernel-ppa...15-11-21-wily/](http://kernel.ubuntu.com/~kernel-ppa...15-11-21-wily/) .

Next, open a terminal and then type:

wget [http://kernel.ubuntu.com/~kernel-ppa...intel-nightly/](http://kernel.ubuntu.com/~kernel-ppa...intel-nightly/)[XYZ]/linux-headers-[XYZ]_amd64.deb

wget [http://kernel.ubuntu.com/~kernel-ppa...intel-nightly/](http://kernel.ubuntu.com/~kernel-ppa...intel-nightly/)[XYZ]/linux-headers-[XYZ]_all.deb

wget [http://kernel.ubuntu.com/~kernel-ppa...intel-nightly/](http://kernel.ubuntu.com/~kernel-ppa...intel-nightly/)[XYZ]/linux-image-[XYZ]_amd64.deb

sudo dpkg -i *.deb

These are the packages for 64 bit systems, otherwise use the i386 packages.

Don't remove your other kernels. In case you run into problems, boot the old kernels and then type:

sudo apt-get remove linux-headers-4.3* linux-image-4.3*.

I hope this helps.

---

### Post by jyrinx on 2015-12-04
> **kjano said:**
> Hi quickdry21,

we have been discussing different kernels here. I assume you are interested in 4.3.0-994-generic, right? You should still be able to get it from [http://kernel.ubuntu.com/~kernel-ppa/mainline/drm-intel-nightly](http://kernel.ubuntu.com/~kernel-ppa/mainline/drm-intel-nightly). I think you can try this one first: [http://kernel.ubuntu.com/~kernel-ppa/mainline/drm-intel-next/2015-11-21-wily/](http://kernel.ubuntu.com/~kernel-ppa/mainline/drm-intel-next/2015-11-21-wily/) .

The 994 one is gone now (they must only keep a few weeks' nightlies). I can vouch for 997, though (the 2015-11-21 one), which by the looks of it should stick around longer (seems it's a weekly build?). (The very latest in the drm-intel-next directory seems to be a failed build.)

Has anyone else had trouble with the touchpad after doing the blacklist thing? It now works (it didn't at all pre-blacklist), but two-finger scrolling doesn't work, and if I hold down the bottom-left corner, the cursor won't move (so I have to remember to drag from the middle of the touchpad).

I suppose it could be the 4.3.0-997 kernel, which I may be the first one here to use ...

**EDIT:** Urk. Also I can't suspend and resume. Maybe I spoke too soon about the 997 kernel being good, though OTOH it hasn't been freezing on me.

---

### Post by anthony-towler on 2015-12-04
> **quickdry21 said:**
> Could you (or anyone) point me towards installing 4.3 994 nightly? I'm guessing this isn't a simple .deb install (or at least I couldn't find any such .deb), but a compile? If it's a .deb install, I can figure it out if you can point me towards the files. If not, pointing me at a guide or set of steps to compile would be awesome. 

I haven't compiled Linux myself before, but I'm competent enough to figure it out (or my overconfidence will lead to the following :D)

EDIT: to clarify, compile for Ubuntu 15.10


There are .debs here:
[http://kernel.ubuntu.com/~kernel-ppa/mainline/v4.3-wily/](http://kernel.ubuntu.com/~kernel-ppa/mainline/v4.3-wily/)

Specifically you'll want the following:
[http://kernel.ubuntu.com/~kernel-ppa/mainline/v4.3-wily/linux-headers-4.3.0-040300-generic_4.3.0-040300.201511020949_amd64.deb](http://kernel.ubuntu.com/~kernel-ppa/mainline/v4.3-wily/linux-headers-4.3.0-040300-generic_4.3.0-040300.201511020949_amd64.deb)
[http://kernel.ubuntu.com/~kernel-ppa/mainline/v4.3-wily/linux-headers-4.3.0-040300_4.3.0-040300.201511020949_all.deb](http://kernel.ubuntu.com/~kernel-ppa/mainline/v4.3-wily/linux-headers-4.3.0-040300_4.3.0-040300.201511020949_all.deb)
[http://kernel.ubuntu.com/~kernel-ppa/mainline/v4.3-wily/linux-image-4.3.0-040300-generic_4.3.0-040300.201511020949_amd64.deb](http://kernel.ubuntu.com/~kernel-ppa/mainline/v4.3-wily/linux-image-4.3.0-040300-generic_4.3.0-040300.201511020949_amd64.deb)

I like to compile from source so I followed this guide:
[https://wiki.ubuntu.com/KernelTeam/GitKernelBuild](https://wiki.ubuntu.com/KernelTeam/GitKernelBuild)

Basically, do the following:
1.) Install git
sudo apt-get install git

2.) Create a directory to put the kernel code in
mkdir ~/Source && cd ~/Source

3.) Pull the source code from git
git clone [COLOR=#000000]git://git.launchpad.net/~ubuntu-kernel-test/ubuntu/+source/linux/+git/mainline-crack v4.3

4.) Change into the new directory
cd v4.3

5.) Checkout the commit hash in the COMMIT file
git checkout [/COLOR][COLOR=#000000]6a13feb9c82803e2b815eca72fa7a9f5561d786

6.) Download .patch files
wget [/COLOR]http://kernel.ubuntu.com/~kernel-ppa/mainline/v4.3-wily/0001-base-packaging.patch
[COLOR=#000000]wget [/COLOR]http://kernel.ubuntu.com/~kernel-ppa/mainline/v4.3-wily/0002-debian-changelog.patch
[COLOR=#000000]wget [/COLOR]http://kernel.ubuntu.com/~kernel-ppa/mainline/v4.3-wily/0003-configs-based-on-Ubuntu-4.3.0-0.6.patch

[COLOR=#000000]7.) Apply the patches
patch -p1 < *.patch

8.) Copy the existing kernel config
[/COLOR][COLOR=#333333]cp /boot/config-`uname -r` .config

9.) Bring the config file up to date
[/COLOR]yes '' | make oldconfig

10.) Clean the kernel source directory
make clean

11.) Compile the kernel and build .deb packages
make -j `getconf _NPROCESSORS_ONLN` deb-pkg LOCALVERSION=-custom

12.) The .deb files for the new kernel will be up one directory
cd ..

13.) Install the packages
sudo dpkg -i <package name>

You'll want to install the linux-headers and the linux-image .debs

14.) Reboot and cross your fingers!

Anyone who knows more than me, please, feel free to provide additional info or alternatives to the above process.

EDIT: 
I also recommend installing the latest Intel graphics driver from here:
[https://01.org/linuxgraphics/downloads/intel-graphics-installer-linux-1.2.1](https://01.org/linuxgraphics/downloads/intel-graphics-installer-linux-1.2.1)

---

### Post by kjano on 2015-12-04
> **jyrinx said:**
> 
**EDIT:** Urk. Also I can't suspend and resume. Maybe I spoke too soon about the 997 kernel being good, though OTOH it hasn't been freezing on me.

I am using the 4.3 994 kernel, the newest intel drivers from [https://01.org/](https://01.org/) and the 352.63 drivers from nvidia and suspend and resume work great for me.

---

### Post by jyrinx on 2015-12-05
> **kjano said:**
> I am using the 4.3 994 kernel, the newest intel drivers from [https://01.org/](https://01.org/) and the 352.63 drivers from nvidia and suspend and resume work great for me.

Mine seems to be okay now; I may have just been used to having a laptop with a latch, so it'd wake up just by opening it. Could've sworn the keyboard wasn't helping at some point earlier, too, though ...

---

### Post by simone22 on 2015-12-05
[FONT=comic sans ms]Hi, I am an owner of a machine with the same hardware as the dell Xps 15 9550, I have an acer nitro vn7-592g with i7-6700hq and gtx960m, I have had your same issues installing ubuntu 15.10 (even the touchpad) , after that I finally ended with a correct installation of ubuntu 15.10 and currenty I am on kernel 4.3, with the correct booting parameters for the integrated graphics card [/FONT](i915.preliminary_hw_support=1[FONT=comic sans ms]nouveau.modeset=0), and I use the integrated graphics card not the Nvidia gtx960m.
Even if everything seems to work fine, I am experiencing issues about temperatures, the laptop seems to heat a lot consequently the battery lasts few hours compared to windows 10 where the laptop remains cool (without fans!!) for most of the every-day tasks (surfing the internet, editing documents) and also the battery lasts up to 7 hours...
At the same time on Ubuntu I find my cpu work a lot! if I open[/FONT] [FONT=comic sans ms]the[/FONT] [FONT=comic sans ms]system monitor I can see there 8 cores (even if in reality there are 4) and all of them working strangely a lot during the normal surfing the internet activity for example they pass from 30% to 50-100% and then go down to 20% or 0%, but on average they work much more than in windows 10 in witch I can work for 8 hours on my laptop without hearing the fans! with temperatures on average of 38°C for the cores. In ubuntu the temperatures are on average 47°C but when you open one applications they go up even reaching 65-70 °C and then going down again, in Windows 10 is difficult for my laptop to exceed the 55 °C whit a lot of applications opened.
Anyone of you that uses ubuntu in your laptop are experiencing similar problems?
Thank you.[/FONT]

---

### Post by kjano on 2015-12-05
Hi simone22, have you followed these steps?
[https://help.ubuntu.com/community/PowerManagement/ReducedPower](https://help.ubuntu.com/community/PowerManagement/ReducedPower)

---

### Post by quickdry21 on 2015-12-05
> **anthony-towler said:**
> There are .debs here:
[http://kernel.ubuntu.com/~kernel-ppa/mainline/v4.3-wily/](http://kernel.ubuntu.com/~kernel-ppa/mainline/v4.3-wily/)

Specifically you'll want the following:
[http://kernel.ubuntu.com/~kernel-ppa/mainline/v4.3-wily/linux-headers-4.3.0-040300-generic_4.3.0-040300.201511020949_amd64.deb](http://kernel.ubuntu.com/~kernel-ppa/mainline/v4.3-wily/linux-headers-4.3.0-040300-generic_4.3.0-040300.201511020949_amd64.deb)
[http://kernel.ubuntu.com/~kernel-ppa/mainline/v4.3-wily/linux-headers-4.3.0-040300_4.3.0-040300.201511020949_all.deb](http://kernel.ubuntu.com/~kernel-ppa/mainline/v4.3-wily/linux-headers-4.3.0-040300_4.3.0-040300.201511020949_all.deb)
[http://kernel.ubuntu.com/~kernel-ppa/mainline/v4.3-wily/linux-image-4.3.0-040300-generic_4.3.0-040300.201511020949_amd64.deb](http://kernel.ubuntu.com/~kernel-ppa/mainline/v4.3-wily/linux-image-4.3.0-040300-generic_4.3.0-040300.201511020949_amd64.deb)


Bleh, I tried the 4.3 994 .deb files out, and it was a disaster. Booting into 4.3 exhibited some strange behaviour:

* Majority of boots the screen would flicker, couldn't even drop into a virtual console.
* Very infrequently I would get to the login screen, entering login info would bring me right back to login screen (gdm crashing I guess).
* I was able to actually login once, but it was between long waits and much screen flickering. 

I checked the kernel and syslog and saw some log messages relating to the NVIDIA driver not loading (didn't save them anywhere unfortunately). I tried out 352 and 355, neither seemed to make much of a difference. Going out on a limb, I thought maybe it was related to installing the NVIDIA drivers while running 4.2, so on one of the login attempts to 4.3 where I was able to get to the login screen, I dropped into a VT, purged nvidia-* and reinstalled nvidia-352 (seems people running 4.3 are having the most success with 352). 

Upon reboot, my problems got worse - logging into 4.3 and 4.2 were then completely impossible:

 4.2 would hard lock displaying boot messages, the latest one being Starting Gnome Desktop (something like that).
4.3 the previous problems were amplified, I couldn't get to the login screen any more, just screen flickering. 

Booting into recovery for 4.2 *and* 4.3 provided no useful ways to fix the NVIDIA driver install - minimal X server failed on both. 

I'm proud of myself on this one - to recover the install I ended up using the initial problem of HDMI causing gdm (or was it X? not sure) to crash that I was trying to resolve in the first place: by booting into 4.3 (4.2 was completely locked) and attaching an HDMI monitor, gdm/X crashed, causing some more flickering, but at least I could drop into a VT and purge the NVIDIA drivers. Then I could boot back into 4.2. 

> **anthony-towler said:**
> 
EDIT: 
I also recommend installing the latest Intel graphics driver from here:
[https://01.org/linuxgraphics/downloads/intel-graphics-installer-linux-1.2.1](https://01.org/linuxgraphics/downloads/intel-graphics-installer-linux-1.2.1)

I have installed the Intel drivers using that link prior to installing kernel 4.3.

I'm at a bit of a loss at this point for what's preventing 4.3 from booting, but it seems graphics related, specifically the Intel Skylake support - IIRC there were some kernel traces in the logs related to i915.

Some things I have left to speculate on that I haven't ruled out:

* Installing [https://01.org/linuxgraphics/downloads/intel-graphics-installer-linux-1.2.1](https://01.org/linuxgraphics/downloads/intel-graphics-installer-linux-1.2.1) before 4.3?
* Installing NVIDIA drivers prior to 4.3?
* Is it related to mainline .deb files? Would compiling it myself using @anthony-towler guide make any difference? @[joshuabc]("http://ubuntuforums.org/member.php?u=612994") mentioned that there might be some compatibility issues: [http://ubuntuforums.org/showthread.php?t=2301071&p=13396394#post13396394](http://ubuntuforums.org/showthread.php?t=2301071&p=13396394#post13396394)

I'm hesitant to install the drm-intel-nightly as this is my work machine and I need stability. Rereading @[joshuabc]("http://ubuntuforums.org/member.php?u=612994")'s post (specifically the DKMS part) leads me to believe this may be related to using the pre-compiled 4.3 mainline .deb files pasted a few times in this post, however it is unclear if other posters are having success with pre-packaged .deb files or self-compiled .deb files.

---

### Post by kjano on 2015-12-05
@quickdry21. Sorry to hear about your problems. The only thing I can really recommend is to backup your home folder and make a clean install following the initial posting in this thread but using 4.3 994 and nvidia 352.63. Also, do not forget to add the GRUB parameter. The HDMI troubles aside, my system works perfectly and I am getting about 6+ hours of battery runtime. I am sure you cen get your system working as well. 

In case it helps, this is what I did:

FROM **jchedstrom**:
0) Might not be necessary but did the following:

BIOS > Secure Boot > Disabled

1) The PCIe hard drive won't be recognized by live Ubuntu 15.10 by default. Change RAID to AHCI. When it works it will appear as /dev/nvme0n1.

BIOS>System Configuration>SATA Operation> switch RAID to AHCI

2) Random freezes will happen with the live Ubuntu 15.10. Symptoms are random freezes and infinite errors, something like the following: nouveau PFIFO SCHED_ERROR. Fix by pressing 'e' on grub menu during boot and add "nouveau.modeset=0" to the end of the line starting with "linux". Now boot live disk by pressing F10.

3) Touchpad might not work. For some reason it worked for me the first time and then never again. Easiest is to use a USB mouse temporarily. There's a fix for after install is finished.

4) Install should now work smoothly.

5) Reboot. Dell SupportAssist reports a failing component. "Error Code 2000-0151, Validation 106575, Hard Drive 1 incorrect status = 8000000000000003". Ignore this. Go into bios and setup the correct boot option.

There might be an automatically provided option to select under boot options. Otherwise manually set it up. BIOS>General>Boot Sequence > Add Boot Option > ubuntu > shimx64.efi (\EFI\ubuntu\shimx64.efi)

6) Try booting, but make sure you press SHIFT repeatedly during boot to get to grub menu. Repeat step (2) above.

7) On first successful boot edit /etc/default/grub, GRUB_CMDLINE_LINUX_DEFAULT="quiet splash nouveau.modeset=0". Then run "sudo update-grub". Now won't need to manually change grub settings on every boot.


**Next:**

Install kernel 4.3 994, see my posting about how to do this above.

**Next:**

sudo apt-get purge nvida-*
sudo add-apt-repository ppa:graphics-drivers/ppa
sudo apt-get update
sudo apt-get install nvidia-352 nvidia-prime  **//---> not 355**
sudo service lightdm restart

sudo add-apt-repository ppa:nilarimogard/webupd8
sudo apt-get update
sudo apt-get install prime-indicator
prime-indicator

**Next:** 
Installing [https://01.org/linuxgraphics/downloa...er-linux-1.2.1](https://01.org/linuxgraphics/downloa...er-linux-1.2.1)

---

### Post by quickdry21 on 2015-12-06
> **kjano said:**
> @quickdry21. Sorry to hear about your problems. The only thing I can really recommend is to backup your home folder and make a clean install following the initial posting in this thread but using 4.3 994 and nvidia 352.63. Also, do not forget to add the GRUB parameter. The HDMI troubles aside, my system works perfectly and I am getting about 6+ hours of battery runtime. I am sure you cen get your system working as well. 

In case it helps, this is what I did:

FROM **jchedstrom**:
0) Might not be necessary but did the following:

BIOS > Secure Boot > Disabled

1) The PCIe hard drive won't be recognized by live Ubuntu 15.10 by default. Change RAID to AHCI. When it works it will appear as /dev/nvme0n1.

BIOS>System Configuration>SATA Operation> switch RAID to AHCI

2) Random freezes will happen with the live Ubuntu 15.10. Symptoms are random freezes and infinite errors, something like the following: nouveau PFIFO SCHED_ERROR. Fix by pressing 'e' on grub menu during boot and add "nouveau.modeset=0" to the end of the line starting with "linux". Now boot live disk by pressing F10.

3) Touchpad might not work. For some reason it worked for me the first time and then never again. Easiest is to use a USB mouse temporarily. There's a fix for after install is finished.

4) Install should now work smoothly.

5) Reboot. Dell SupportAssist reports a failing component. "Error Code 2000-0151, Validation 106575, Hard Drive 1 incorrect status = 8000000000000003". Ignore this. Go into bios and setup the correct boot option.

There might be an automatically provided option to select under boot options. Otherwise manually set it up. BIOS>General>Boot Sequence > Add Boot Option > ubuntu > shimx64.efi (\EFI\ubuntu\shimx64.efi)

6) Try booting, but make sure you press SHIFT repeatedly during boot to get to grub menu. Repeat step (2) above.

7) On first successful boot edit /etc/default/grub, GRUB_CMDLINE_LINUX_DEFAULT="quiet splash nouveau.modeset=0". Then run "sudo update-grub". Now won't need to manually change grub settings on every boot.


**Next:**

Install kernel 4.3 994, see my posting about how to do this above.

**Next:**

sudo apt-get purge nvida-*
sudo add-apt-repository ppa:graphics-drivers/ppa
sudo apt-get update
sudo apt-get install nvidia-352 nvidia-prime  **//---> not 355**
sudo service lightdm restart

sudo add-apt-repository ppa:nilarimogard/webupd8
sudo apt-get update
sudo apt-get install prime-indicator
prime-indicator

**Next:** 
Installing [https://01.org/linuxgraphics/downloa...er-linux-1.2.1](https://01.org/linuxgraphics/downloa...er-linux-1.2.1)

Thanks for the help kjano, going to try this out tomorrow. If this series of steps works out, it sounds like the order in which the graphics drivers are installed matter - specifically, having the nvidia-352 and the Intel drivers installed *before* installing 4.3 might be causing the issue.

I love these challenges with Linux, I always come out the other side knowing more than when I started :)

EDIT: Technically, if this is the case, I should be able to remove nvidia and the Intel driver packages and 4.3 would work, might try that out. Either way my /home is on a separate partition so it's not too expensive to reinstall.

So, after doing a bunch of fresh installs and playing around with different setups, I can get HDMI working on a fresh install of Ubuntu Gnome 15.10, before installing any nvidia-* or the intel graphics installer drivers. Went through the steps of installing, then adding nouveau.modeset=0 to the boot options and blacklisting the i2c_hid touchpad driver. After a fresh install, I can get HDMI working *only* after switching my monitor to HDMI and plugging in the cable right away. If I plug in the cable while the monitor is set to DVI or DisplayPort or w/e, then switching the input to HDMI, it won't work, I tried F8 to cycle display modes, unplugging and replugging HDMI. 

I tried kernel 4.3 (was noticeably unstable) and nvidia-352, couldn't get a stable setup let alone HDMI working. 

I've yet to exhaust all combinations of kernel 4\.[23] && nvidia-3\d{2} && intel drivers, so I'm still hoping I can get HDMI working with proper NVIDIA drivers.

Regardless, I beg for mercy, anyone who is using this laptop running Ubuntu with an external monitor via HDMI please reveal your secrets/setup!

---

### Post by simone22 on 2015-12-06
> **kjano said:**
> Hi simone22, have you followed these steps?
[https://help.ubuntu.com/community/PowerManagement/ReducedPower](https://help.ubuntu.com/community/PowerManagement/ReducedPower)

Hi kjano, thank you for your reply. Of course I have set properly powertop, and thermalid but the problem remained.
Anyway I actually found a solution! I have installed the kernel 4.4 rc3 ( I previously tried 4.3 and then 4.4 rc 2 but I had the identical heating problems), now whit this kernel I can experience the same temperatures as Windows 10! Even lower... No fans.. And temperatures about 38 degrees. Ufortunately the only thing is that the wifi connection doesn't work with this new kernel ( I have an atheros QCA6174)

---

### Post by Annihil on 2015-12-06
Indeed, kernel 4.3.0-994 from drm-intel-nightly is now gone.
But kernel 4.3.0-997 can be found in drm-intel-next :

```
wget \
[http://kernel.ubuntu.com/~kernel-ppa/mainline/drm-intel-next/2015-11-21-wily/linux-headers-4.3.0-997-generic_4.3.0-997.201511202100_amd64.deb]("http://kernel.ubuntu.com/~kernel-ppa/mainline/drm-intel-nightly/2015-11-13-wily/linux-headers-4.3.0-994_4.3.0-994.201511122102_all.deb") \
[http://kernel.ubuntu.com/~kernel-ppa/mainline/drm-intel-next/2015-11-21-wily/linux-headers-4.3.0-997_4.3.0-997.201511202100_all.deb]("http://kernel.ubuntu.com/~kernel-ppa/mainline/drm-intel-nightly/2015-11-13-wily/linux-headers-4.3.0-994-generic_4.3.0-994.201511122102_amd64.deb") \
[http://kernel.ubuntu.com/~kernel-ppa/mainline/drm-intel-next/2015-11-21-wily/linux-image-4.3.0-997-generic_4.3.0-997.201511202100_amd64.deb]("http://www.mediafire.com/download/126g8w3dffvoveo/linux-image-4.3.0-994-generic_4.3.0-994.201511122102_amd64.deb") \
[FONT=Verdana]sudo dpkg -i *.deb[/FONT]
```

This kernel works with nvidia-358 driver, sleep/wake works and HDMI also works :

[IMG]http://i.imgur.com/fVkpCEth.jpg[/IMG]

By the way, I tested kernel 4.4.0-994-generic from intel-drm-nightly, and 4.4-rc3 from wily mainline and the system didn't boot with both.

---

### Post by fab3 on 2015-12-06
Hi all,

first of all thanks to all of you who have contributed here. I managed to get Linux Mint 17.3 running on my XPS 15 and it seems to be running fine for the moment. :-)

There's an issue that's driving me mad, though. I'm used to rest my left finger on the left button of the touchpad and use the right finger to point. The synaptics driver seems to be buggy, because whenever my right finger touches the touchpad, the pointer freezes.

I have configured the touchpad by copying the synaptics config:

```
sudo cp /usr/share/X11/xorg.conf.d/50-synaptics.conf /usr/share/X11/xorg.conf.d/51-synaptics-userdefined.conf

```

and then added

```
Section "InputClass"
        Identifier "Default clickpad buttons"
        MatchDriver "synaptics"
#                                 RB: Left right top bottom  MB: Left right top bottom
#       Option "SoftButtonAreas" "50% 0 82% 0 0 0 0 0"
#       Option "SoftButtonAreas" "0 50% 82% 0 50% 0 82% 0"  # bottom:right 50% middle 50%
        Option "SoftButtonAreas" "60% 0 82% 0 41% 59% 82% 0" #bottom: left(40%) middle(20%) right (40%)
#       To disable the bottom edge area so the buttons only work as buttons,
#       not for movement, set the AreaBottomEdge
        Option "AreaBottomEdge" "82%"
#       synclient PalmDetect=1
        Option "PalmDetect" "1"


EndSection

```

but no luck.

I found this thread stating there's an error in the synaptics driver:

[https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-input-synaptics/+bug/1026046](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-input-synaptics/+bug/1026046)

Is anyone experiencing the same issue? I'm desperately searching for a solution to this annoying issue.

For the moment I'm using this workaround:

```

[COLOR=#333333][FONT=monospace]sudo modprobe psmouse proto=imps
[/FONT][/COLOR]
```

which disables the capability of scrolling with the touchpad :-/

Any help would be highly appreciated!

Thanks and regards,

Fab

---

### Post by kjano on 2015-12-06
I cannot get any 4.4 kernel working. The HDMI issue aside I am happy with the machine despite the screen being super glossy and the webcam being totally pointless. The HDMI situation is super frustrating and it may take like 5 min just to connect a screen or projector. I hope we will see some improvements over the next weeks. Maybe it is worth to post a bug report.

---

### Post by jyrinx on 2015-12-06
> **Annihil said:**
> By the way, I tested kernel 4.4.0-994-generic from intel-drm-nightly, and 4.4-rc3 from wily mainline and the system didn't boot with both.

What was the issue? I just tried the 994 from intel-drm-nightly and the kernel couldn't find the SSD (presumably some issue with NVMe, which is getting a lot of attention, judging by the changelogs), so I wound up at a BusyBox prompt in the initrd. (Which is actually kind of cool. Last time I remember hacking on a Linux box like this, I don't think the initrd had BusyBox on it. Or maybe it's just that I wasn't trying to get a brand-new storage architecture working so I never saw it …)

Also, I'm now thinking that for some reason I can resume *but* only if the machine isn't suspended very long. If I close the lid, open it again, then hit a key, it comes back to life, but if I leave and come back it won't wake up. Annoying because it means I can't test it quickly …

---

### Post by quickdry21 on 2015-12-06
In the process of trying out intel-drm-nightly 997 and still no HDMI - at least this time I'm getting new errors: *ERROR* 5.4 Gbps link rate without HBR2/TPS3 support. Screen flickers a bunch when plugging in HDMI then nothing, tried nvidia-352 and nvidia-358, no difference. 

Starting to give up hope on HDMI. I have a USB-C to DisplayPort cable in the mail right now, I'm hoping it will support DP 1.2 MST so I can use both of my external monitors, but at this point I would be happy to just get one going :/

---

### Post by kjano on 2015-12-06
> **quickdry21 said:**
> 
Starting to give up hope on HDMI. I have a USB-C to DisplayPort cable in the mail right now, I'm hoping it will support DP 1.2 MST so I can use both of my external monitors, but at this point I would be happy to just get one going :/

I was told that USB-C to HDMI and Display port cables are not well supported by Linux in general, which product did you buy?

---

### Post by quickdry21 on 2015-12-06
> **kjano said:**
> I was told that USB-C to HDMI and Display port cables are not well supported by Linux in general, which product did you buy?

[http://www.monoprice.com/product?p_id=12908](http://www.monoprice.com/product?p_id=12908)

Starting to worry this is HW related, can't switch to Intel graphics, HDMI refuses to work.

---

### Post by satcom66 on 2015-12-07
Thought I would share my experience with this machine (4K display) and Kubuntu 15.10

I followed jchedstrom instructions and everything worked fine.  No problems with wireless or nvidia-355.   I found that bumblebee did not work and had to boot into 'init 3' to fix that.  The prime-select tool however worked very well.  Of note, after install the system defaulted to running the nvidia drivers and battery life reported at 2 hours.  When I switched to the intel drivers, battery life went up to 6 hours and the machine was very much cooler.

Had some intermittent problem with the the graphics where the screen would get unstable (garbage appearing at top of screen).  After a couple of reboots, this seems to have gone away.  However, when using the intel drivers it was not possible to watch a video on full-screen; the frame rate drops to about 0.2fps and it looks more like a slideshow than a video.  Works totally fine at smaller resolutions.

Have not found a good solution for the DPI issues other than changing all the default font selections I can find.  The tool bar at the bottom of the screen is incredibly small, but sharp as hell.  ;-)

Biggest issue was that the keyboard started acting weird.  I would type a few characters and it would then puke out a whole bunch of garbage including non-printable characters.  Thought at first this was a linux problem but it persisted even when running Windows 10.  USB keyboard works fine.  I note all the problems the XPS13 has had with keyboards and wonder if this is related.  Contacted Dell Support and after diagnosing remotely they concluded the keyboard was bad.  Certainly not a good thing on a three-day old $2K machine.  They are sending another keyboard.  If you are having keyboard issues, definitely check it with USB and bang Dell if that works.

Will report more after keyboard is replaced.

---

### Post by kjano on 2015-12-07
> **quickdry21 said:**
> 
[...]can't switch to Intel graphics.

And you are using prime to do so, right?

---

### Post by quickdry21 on 2015-12-07
> **kjano said:**
> And you are using prime to do so, right?

I tried using prime-indicator as well as NVIDIA settings. Both times I would get to the login screen, and attempts to login failed (brought me right back).

---

### Post by anthony-towler on 2015-12-07
> **satcom66 said:**
> I found that bumblebee did not work and had to boot into 'init 3' to fix that.

Can you elaborate on what you did in that runlevel to help with Bumblebee?

---

### Post by satcom66 on 2015-12-07
When I installed bumblebee and rebooted I got no graphics in init 5, so I rebooted and forced it to init 3.  Once there I removed the bumblebee package and undid the blacklists.  Then, rebooted to init 5 and graphics worked fine again.  nvidea-prime seems to work just fine although the indicator is so small on my screen I can't see what it is doing.

---

### Post by michele20 on 2015-12-07
Hello,

firstly, thank you all for the very useful discussion and tips.

I'll hopefully get my Dell XP 15 on January 6th, meanwhile I am following this discussion.

Anyone will try to install Ubuntu 16.04 Alpha 1 (gnome or other) in the next month? I was wondering if we could get less issues with the new release.

---

### Post by satcom66 on 2015-12-07
Just tried daily build of 16.04 and it didn't work for beans.  Black screen without 'nomodeset' argument; with the argument it gets a little further then starts compiaining it can't load i915.  Shortly after that the screen starts flashing.  All in all, not ready for prime time.

---

### Post by michele20 on 2015-12-07
@satcom66, thank you so much for trying!!

I really hope Dell will create a "developer version" of the XPS so that all these troubles will end.

---

### Post by bertusrex on 2015-12-07
I've finally gotten my Logitech MX Anywhere 2 to work via Bluetooth on my XPS 15 9550 with DW1830 wifi/BT card. The mouse is pretty stable now, everything works, including back/forward  navigation buttons. The mouse is detected and connected automatically  at boot now. Tested with kernel 4.2 and 4.3 both on Wily (15.10).

These are the steps I took. They're a bit hacky, suggestions for improvement welcome.

**1)** enable bluetoothd experimental features with -E parameter. To make the -E parameter permanent across boots, I did this:
```
sudo nano /etc/init.d/bluetooth
```

and around line 39 replace 
```
NOPLUGIN_OPTION=""
```
  with
```
NOPLUGIN_OPTION="-E"
```

CTRL-X to save and exit
(The NOPLUGIN_OPTION is abused a bit here to exec "/usr/sbin/bluetoothd -E")

reboot, and see if you can pair now.

You may need to pair manually using bluetoothctl, put mouse in pairing mode (Logitech MX Anywhere 2: press connect button)
```
$ bluetoothctl
[NEW] Controller 18:4F:32:F7:F2:E8 steady-XPS-15-9550 [default]
[NEW] Device D8:C2:11:ED:57:26 MX Anywhere 2
[bluetooth]# power off
Changing power off succeeded
[CHG] Controller 18:4F:32:F7:F2:E8 Powered: no
[CHG] Controller 18:4F:32:F7:F2:E8 Discovering: no
[CHG] Controller 18:4F:32:F7:F2:E8 Class: 0x000000
[bluetooth]# power on
[CHG] Controller 18:4F:32:F7:F2:E8 Class: 0x0c010c
Changing power on succeeded
[CHG] Controller 18:4F:32:F7:F2:E8 Powered: yes
[bluetooth]# scan on
Discovery started
[CHG] Controller 18:4F:32:F7:F2:E8 Discovering: yes
[NEW] Device D8:C2:11:ED:57:28 MX Anywhere 2
[bluetooth]# trust D8:C2:11:ED:57:28
[CHG] Device D8:C2:11:ED:57:28 Trusted: yes
Changing D8:C2:11:ED:57:28 trust succeeded
[bluetooth]# pair D8:C2:11:ED:57:28
Attempting to pair with D8:C2:11:ED:57:28
[CHG] Device D8:C2:11:ED:57:28 Connected: yes
[CHG] Device D8:C2:11:ED:57:28 UUIDs: 00001800-0000-1000-8000-00805f9b34fb
[CHG] Device D8:C2:11:ED:57:28 UUIDs: 00001801-0000-1000-8000-00805f9b34fb
[CHG] Device D8:C2:11:ED:57:28 UUIDs: 0000180a-0000-1000-8000-00805f9b34fb
[CHG] Device D8:C2:11:ED:57:28 UUIDs: 0000180f-0000-1000-8000-00805f9b34fb
[CHG] Device D8:C2:11:ED:57:28 UUIDs: 00001812-0000-1000-8000-00805f9b34fb
[CHG] Device D8:C2:11:ED:57:28 UUIDs: 00010000-0000-1000-8000-011f2000046d
[CHG] Device D8:C2:11:ED:57:28 Paired: yes
Pairing successful
[CHG] Device D8:C2:11:ED:57:28 Modalias: usb:v046DpB013d0007
[MX Anywhere 2]# 

```

Paring/trusting only has to be done once.

** 2)** If connecting still fails, update the DW1830 Bluetooth firmware by downloading [this zip]("http://bit.ly/1IBWfKp"), and copying the firmware file to your Ubuntu installation (see included README). 
Reboot and try again. dmesg should now contain something like 
```
 [    2.221830] Bluetooth: hci0: BCM (001.001.005) build 0422
```

repeat 1) if pairing/connecting didn't work the first time.

After these steps, if mouse is not connecting try switching off and on the BT device:
```
$ bluetoothctl
[bluetooth]# power off
Changing power off succeeded
[bluetooth]# power on

```

The Logitech MX anywhere 2 mouse has support for multiple devices, and has a button on the bottom to activate one of them.  I'm using this mouse in a dual boot config, and it seems the mouse thinks that the BT adapter has a different ID under Windows than under Linux (or at least some of the time). You sometimes need to re-pair because of that, but during re-pairing the mouse chooses a new BT ID itself, despite it using the same mouse profile (1, 2 or 3) as before. You then need to re-pair under the other OS again too. Long story short: you're probably best off selecting 1 mouse profile on the mouse for Ubuntu (pairing with that profile active), and a second one for Windows (pairing with the second profile). So when you switch OS, switch profile on your mouse too.


Something unrelated to Bluetooth and Logitech mouse:

I'm attempting to tune power management under 15.10, and I'm seeing strange numbers when using powertop:

When running with Intel graphics (1.2.1 drivers from 01.org) power usage  is about 15-20 W when idle, with wifi and bluetooth on, brightness at  50% (FHD panel). My 56kWh battery lasts only about 3 hours that way.  When using the 960M GPU (nvidia 358.16 driver), power consumption drops  to 9-10W. 

It's supposed to be the other way around, Intel should be the power saving option of the two. Anyone else notice this?

---

### Post by kjano on 2015-12-08
> **bertusrex said:**
> I'm attempting to tune power management under 15.10, and I'm seeing strange numbers when using powertop:

When running with Intel graphics (1.2.1 drivers from 01.org) power usage is about 15-20 W when idle, with wifi and bluetooth on, brightness at 50% (FHD panel). My 56kWh battery lasts only about 3 hours that way. When using the 960M GPU (nvidia 358.16 driver), power consumption drops to 9-10W. 

It's supposed to be the other way around, Intel should be the power saving option of the two. Anyone else notice this?

While the numbers certainly look strange, 3 hours is exactly the value reported by a recent review of the FHD/56 version for Windows. Other reviews (for windows) report 6+ hours for the 4K/84 version and I am getting a similar runtime on my machine. I have not tried to run down the battery to zero often enough to really report meaningful numbers here but I can get 6 hours of careful use. I also got the external battery pack from Dell which should add some more hours.  I have a (power) rate of 14.8 right now with the 4K screen and the 960M turned on while watching a youtube video (and typing this posting) and the screen set to about 40%. This would give me a bit more than 5 1/2 hours on the nvidia. If I reduce the screen to about 30% brightness (which is still absolutely fine indoors), I get a rate of 13.2. Setting the screen to 100% brings me to 18.1. I hope this helps.

---

### Post by michele20 on 2015-12-08
Question: when you do not force the use of a specific GPU, does the system switch it automatically and gracefully? (e.g., intel to nvidia when opening a full hd youtube video)

Do you usually force one of them during your daily usage?

---

### Post by kjano on 2015-12-08
hmm, my headphone sound just stopped working. Does it still work for you guys?

---

### Post by rvanderwerf on 2015-12-08
> **kjano said:**
> hmm, my headphone sound just stopped working. Does it still work for you guys?

it does that to me a lot, if I unplug it, sounds works through speakers, and I re-plug in headphones and it starts working again.

> **michele20 said:**
> Question: when you do not force the use of a specific GPU, does the system switch it automatically and gracefully? (e.g., intel to nvidia when opening a full hd youtube video)

Do you usually force one of them during your daily usage?

I force it to nvidia while plugged, intel when not. I'm not getting 15w during idle, best I have gotten is with screen super dim on intel around 19w

I need to try the 358 driver, it sounds like magic. I don't see this on the 352 driver.

---

### Post by bertusrex on 2015-12-09
> **kjano said:**
> While the numbers certainly look strange, 3 hours  is exactly the value reported by a recent review of the FHD/56 version  for Windows. Other reviews (for windows) report 6+ hours for the 4K/84  version and I am getting a similar runtime on my machine. I have not  tried to run down the battery to zero often enough to really report  meaningful numbers here but I can get 6 hours of careful use. I also got  the external battery pack from Dell which should add some more hours.  I  have a (power) rate of 14.8 right now with the 4K screen and the 960M  turned on while watching a youtube video (and typing this posting) and  the screen set to about 40%. This would give me a bit more than 5 1/2  hours on the nvidia. If I reduce the screen to about 30% brightness  (which is still absolutely fine indoors), I get a rate of 13.2. Setting  the screen to 100% brings me to 18.1. I hope this helps.

Thanks for the numbers, always good to compare and to hear some real life experience. I must say I'm usually working plugged in, and with heavier software (e.g. compilers, VM's and IDE's) the battery doesn't last long at all.

As a small (and mostly meaningless) test I left my XPS 15/FHD/56Wh idling in Ubuntu 15.10 with 960M active, screen always on at 50%, it ran for 6:30 hours before shutting down. Not too bad IMO with this battery, although not representative of normal use.

---

### Post by astroman3001gt on 2015-12-09
First of all, Thanks to everybody that is sharing information on this laptop. I have finally decided to move on and order this laptop. I hope I don't regret it. My last laptop choices were not very good when it concerns linux but I am really hopping that this laptop will be 100% compatible for the next LTS ubuntu in April.

Anyway, I will not stick with Windows until April. So I will try to follow some of your suggestions to make the most out of the laptop
as possible with linux. Btw, since there is much spread info in this thread, does any one of you have a good updated summary of the steps to do in?

---

### Post by kjano on 2015-12-10
Battery runtime, CPU update: Here is some interesting info from noteboockcheck.com. It looks like there is a bug in the Dell firmware when you unplug and run on battery, the firmware tries to put your CPU in a 1.6 Ghz power saving mode but it does not reliably wake up from that mode when you plug in again. I observed another effect about the power usage, if you run into a high power rate and your battery discharges quickly and the fan stays on, just plug in and unplug again (or the reverse) and in many cases the fan will stop and the battery power rate will fall again to about 13-20W. Anyway, if you get a rate of more than 20W over longer periods, follow the power management link I posted a few postings above. I have the 4K display with the 84WHr battery and 5+ hours of productive working a not a problem (including software development, latex, email, surfing, music). I typically run the display on 30-40% which is still a lot. Six hours are doable, 7 are not. I also have the external DELL battery which is pretty small and should give me some more hours/

---

### Post by bertusrex on 2015-12-11
> **astroman3001gt said:**
>  Btw, since there is much spread info in this thread, does any one of you have a good updated summary of the steps to do in?

I see a noble task in your future... ;-)

---

### Post by BeeOnRope on 2015-12-12
Has anyone gotten this working in a dual-boot configuration with Windows 10, with the windows side of things being stable? My understanding from this thread and discussions on other forums is that you must switch to AHCI mode (from RAID) in the BIOS but that this leads to frequent BSODs on the Windows side. 

Anyone have both OSes working stably? Is it feasible to just switch to RAID mode just when booting into Windows?

---

### Post by bertusrex on 2015-12-12
I found an older but still usefull power consumption indicator (for the status bar) python script. Instead of using powertop, you can see current consumption in the status bar.

It looks like this (in between other indicators):
 [IMG]http://i64.tinypic.com/2hnxbat.png[/IMG]

For information and downloading the python script, see [this thread]("http://ubuntuforums.org/showthread.php?t=1959162&p=11846180#post11846180").

One small tweak I did prevents the width of the indicator from constantly changing when consumption hoovers around 10W (the text shrinks a digit when below, expands again when above). This tweak just adds a zero in front of it in that case (09W) so that width does not change.

change line 239 to:
```
                rate = str(int(round(props['EnergyRate'] if self.prefs['watts'] else props['EnergyRate'] * 1000 / props['Voltage'])))**.rjust(2,"0")** + (' W' if self.prefs['watts'] else ' mA');
```
and keep the spacing in front of the line the same as before (python depends on this).

You can start it automatically by including it in "Startup Applications"  (super key, type "startup applications" to start it). Select Add  button, type the path and a name for it, confirm, and log back in.

---

### Post by Annihil on 2015-12-12
> **BeeOnRope said:**
> Has anyone gotten this working in a dual-boot configuration with Windows 10, with the windows side of things being stable? My understanding from this thread and discussions on other forums is that you must switch to AHCI mode (from RAID) in the BIOS but that this leads to frequent BSODs on the Windows side. 

Anyone have both OSes working stably? Is it feasible to just switch to RAID mode just when booting into Windows?
To avoid BSOD on Windows 10 when on AHCI mode, you must install Samsung NVMe 950 Pro driver (even if you have a PM951 SSD).
You can download it on this page : [http://www.samsung.com/global/business/semiconductor/minisite/SSD/global/html/support/downloads.html](http://www.samsung.com/global/business/semiconductor/minisite/SSD/global/html/support/downloads.html) (Samsung NVMe Driver Installer heading)
The only downside is that when you reboot using Windows, sometimes it will say Drive not detected.
So avoid rebooting, you won't issue this with cold boot.

---

### Post by quickdry21 on 2015-12-13
Well, still been struggling to get HDMI working. 

* Started from a fresh install, followed the steps to get Ubuntu Gnome installed and working properly.
* Installed drm-intel-nightly 997
* Installed Intel drivers graphics drivers from 01.org
* Installed nvidia-358, nvidia-prime, prime-indicator

Tried with NVIDIA enabled, no HDMI:

* Screen flickers multiple times 
* Logs looks like gdm is trying to start up and crashing, multiple kernel traces related to i915

Tried switching to Intel graphics:

* Back to login screen, trying to login boots me back to login screen

Figured out that when using prime-indicator to change GPUs restarting gdm allowed actually switching:

* prime-indicator -> Quick Switch -> Go to login screen
* Drop into VT (ctrl+alt+f2) and login
* sudo service gdm restart
* Will boot you back to login screen with the selected GPU

Started trying combinations of GPU + nvidia-35\d.

NVIDIA GPU on all of 352, 355, 358

* Can login (although usually the first attempt fails) 
* HDMI results in usual flickering / gdm crash / kernel traces every time - can be fixed by dropping into a VT, unplugging HDMI and restarting gdm

nvidia-358: 

* login screen + after login resolution is low, opening Gnome's Display settings causes the resolution to readjust without doing anything, sometimes on the first open, sometimes on the second
* on Intel GPU plugging in HDMI the monitor is actually detected (yay!), but the system hard locks before anything can be done (no VT's, needs hard off)
* need to restart gdm after switching GPUs with prime-indicator

nvidia-355 and nvidia-352:

* On Intel GPU HDMI worked a few times, there is graphical corruption for about 5-10 seconds and then either the system locks up or you can proceed as normal
* Switching GPU's usually requires gdm restart, otherwise can't get past login, was able to switch without gdm restart a couple times

All in all things are highly unstable when trying to use HDMI to HDMI on drm-intel-nightly 997. It seems some people are having some success with HDMI, but I have a feeling they are using a different combination than I am (HDMI->HDMI, QHD+, Ubuntu Gnome).

Anyone having better luck than me?

---

### Post by thananop.k on 2015-12-13
I also experienced the same problem with HDMI & Display Port on ASUS UX303LNB (Intel HD 5500 & NVIDIA 840M). After many hour of searching on google,it lead me to this topic. My best bet is to use **_bumblebee_** combining with nvidia-358, it make all external monitor run through Intel card and we can use nvidia card through primusrun command. FPS may not as good as run through nvidia-prime method but all external monitor work as it should be

---

### Post by bertusrex on 2015-12-15
I still have tearing with nvidia-358.16 (e.g. when moving windows around, or scrolling in a browser). On Intel it's gone now (with the 1.2.1 drivers from 01.org). Anyone fixed the nvidia tearing yet?

---

### Post by rvanderwerf on 2015-12-15
I have 994 nightly, similar issues. It nvidia dual monitor worked for a while until I got some kind of update, now if I even plug in a hdmi monitor it kicks me back to the login screen. Sometimes intel drivers works with 2 monitors, sometimes after a screen saver or modeswitch it doesn't come back right and the main laptop display will flicker and the machine will hard-freeze. I've given up for now, I'm bummed I don't have a stable 2 monitor setup yet. I'm hoping dell will get on it soon - this is a way better developer machine than the xps13. Not sure why the think a ultrabook is a better choice than this.

---

### Post by quickdry21 on 2015-12-15
> **rvanderwerf said:**
> I have 994 nightly, similar issues. It nvidia dual monitor worked for a while until I got some kind of update, now if I even plug in a hdmi monitor it kicks me back to the login screen. Sometimes intel drivers works with 2 monitors, sometimes after a screen saver or modeswitch it doesn't come back right and the main laptop display will flicker and the machine will hard-freeze. I've given up for now, I'm bummed I don't have a stable 2 monitor setup yet. I'm hoping dell will get on it soon - this is a way better developer machine than the xps13. Not sure why the think a ultrabook is a better choice than this.

This exactly describes the issues I am having. Glad someone else is having the same issue, I thought I was going crazy with people here saying they have HDMI working!

The USB-C -> DisplayPort cable (not adapter) I ordered arrived and it didn't help at all, more or less the exact same issues with HDMI -> HDMI.

---

### Post by kjano on 2015-12-15
I am using the 994 kernel with the nvidia 352.63 driver and prime for switching. The switching works great and HDMI works 90% of the time, it just takes a few seconds and pressing F8 a few times to connect. I am fine with this at home and work but it it a real pain when connecting to a projector and having to hope that it is not one of those 10% where you have to rebook your machine like 5 x.

---

### Post by satcom66 on 2015-12-17
So the Dell folks replaced my keyboard and that works perfectly now.  It feels different from the last one, much more precise and less mushy.  Plus, no weird characters appearing.

I reverted it to Windows so Dell could work on it without getting distracted and then tried going back to Kubuntu with a clean install.  Definitely much harder this time around and not sure why.  Seemed to be some new packages installed that were causing me some grief.  Finally got most everything running again but a couple of differences.  Most notably, audio no longer works.  Not sure what happened there.  

On the video side, when I use prime-select it seems to be saying it is doing the same thing whether I select 'intel' or 'nvidia'.   Specifically, it always says that the "current alternatives in use are: " ['nvidia-355-prime', 'nvidia-355-prime']".  It says that no matter whether I select intel or nvidia though a prime-select query shows the correct selection.   Most interesting is that powertop shows the exact same power consumption of about 13W no matter which one I select.  It was definitely toggling before, but not now.  Also interesting is that the screen flicker I was getting when I selected 'intel' before is gone; works great now.  So totally not sure what is going on here.  

Other than that, operation seems stable.  It sleeps just fine and wakes up as expected.  Managed to get most of the fonts scaled up where needed to pretty readable.  Machine seems pretty snappy, I installed MATE 15.10 in virtualbox on it and it is real snappy.  Screen is dazzling.  Now if I could only get the Audio to work!

---

### Post by kjano on 2015-12-17
In my case kernel 994 fixed the audio issues. Also, have you tried playing around with alsamixer?

---

### Post by Calin Balaurul on 2015-12-17
Hi @kjano, your close the lid trick helps out a lot, thank you, any other updates on this issue?

Simply edit /etc/default/crda

Hi,

I managed to install Ubuntu 15.10, have suspend/resume and hdmi work with both intel and nvidia

I get black screen at login if no hdmi plugged, work around without hdmi is to login in the dark and close open the lid.
If the wireless is not working edit /etc/default/crda and set your region, get the iso code from /usr/share/zoneinfo/zone.tab.

Build in mic does now work

**Installation**
Change from raid to achi
Boot from the live usb
Press 'e' on the first entry and add 'set nouveau.modeset=0'
Boot and install (for me the installer freezes if I selected extra repositories, don't worry you can get those later)

**After installation**
install kernel-4.3.3 [http://linuxg.net/install-kernel-4-3-on-ubuntu/](http://linuxg.net/install-kernel-4-3-on-ubuntu/)
add oibaf ppa for intel [https://launchpad.net/~oibaf/+archive/ubuntu/graphics-drivers](https://launchpad.net/~oibaf/+archive/ubuntu/graphics-drivers) and update intel drivers via `apt-get dist-update`
install graphics ppa [https://launchpad.net/~graphics-drivers/+archive/ubuntu/ppa](https://launchpad.net/~graphics-drivers/+archive/ubuntu/ppa) and install the latest nvidia 358 and nvidia prime and prime indicator

Hope this saves someone time.

---

### Post by bertusrex on 2015-12-18
> **Calin Balaurul said:**
> Hi,

I managed to install Ubuntu 15.10, have suspend/resume and hdmi work with both intel and nvidia


What about tearing, still present on both nvidia and Intel? (e.g. when dragging windows or scrolling in browser)

---

### Post by indigo00862 on 2015-12-19
I ass the noveau.modeset=0 and when I boot it doesn't necessarily hang on the ubuntu logo but just shows the progress dots running indefinitely,

---

### Post by quickdry21 on 2015-12-19
> **jyrinx said:**
> What was the issue? I just tried the 994 from intel-drm-nightly and the kernel couldn't find the SSD (presumably some issue with NVMe, which is getting a lot of attention, judging by the changelogs), so I wound up at a BusyBox prompt in the initrd. (Which is actually kind of cool. Last time I remember hacking on a Linux box like this, I don't think the initrd had BusyBox on it. Or maybe it's just that I wasn't trying to get a brand-new storage architecture working so I never saw it …)

Also, I'm now thinking that for some reason I can resume *but* only if the machine isn't suspended very long. If I close the lid, open it again, then hit a key, it comes back to life, but if I leave and come back it won't wake up. Annoying because it means I can't test it quickly …

To anyone experiencing the issue of being dropped to BusyBox after installing 4.4 - it's caused by this bug: [http://comments.gmane.org/gmane.linux.debian.devel.bugs.general/1310268](http://comments.gmane.org/gmane.linux.debian.devel.bugs.general/1310268)

To fix this you just need to add the nvme module to the initramfs.

I installed rc5 mainline .deb files here:

[http://kernel.ubuntu.com/~kernel-ppa/mainline/v4.4-rc5-wily/](http://kernel.ubuntu.com/~kernel-ppa/mainline/v4.4-rc5-wily/)

Then, add the nvme module:

```

echo nvme | sudo tee -a /etc/initramfs-tools/modules
sudo update-initramfs -u

```

Running well so far with nvidia-358.

Now to test if this makes a difference with HDMI -> HDMI and USB-C -> DisplayPort - already seeing less error messages in dmesg.

---

### Post by Calin Balaurul on 2015-12-21
> **bertusrex said:**
> What about tearing, still present on both nvidia and Intel? (e.g. when dragging windows or scrolling in browser)

None that I've seen.

> **indigo00862 said:**
> I ass the noveau.modeset=0 and when I boot it doesn't necessarily hang on the ubuntu logo but just shows the progress dots running indefinitely,

If you press esc, you should see a lot of IO errors.

The good news is that once you update to kernel 4.3.3 there is no need for that flag.

---

### Post by michele20 on 2015-12-21
For those worried about the effect on the performance of switching from RAID to AHCI (like I was),  I found that it should have **no effect at all** if you have only one drive (so you actually do not exploit the RAID).

Source (post for Windows on Dell XPS 15): [http://forum.notebookreview.com/threads/dell-xps-15-9550-list-of-hardware-and-software-problems.784691/](http://forum.notebookreview.com/threads/dell-xps-15-9550-list-of-hardware-and-software-problems.784691/)

---

### Post by joshuabc on 2015-12-21
A while back I promised to share my kernel config, which has been quite stable. It's not at all different from other mainline or DRM 4.4 solutions, but if you feel like eliminating modules or features that don't apply to your hardware, you can. For my own laptop, I took out all non-intel CPU support, exotic networking stuff and 95% of all device drivers. For this example, I've left that stuff intact. What you will get is is NVMe support at boot without issue. You won't need AHCI unless you actually have a sata drive. You will have working suspend. You'll have zSwap enabled by default if you use swap - much kinder to SSDs. You'll have better TRIM support as well. You might have better PCIe power management - I'm looking into it. My 1TB Samsung 951 tends to get really, really hot, even at idle. Neither Intel NVMe drives under Linux, nor Samsung NVMe drives under other OSs seem to have any such problem, so there must be a fix.

Note that I'm using drm-intel-next here, not mainline, but this applies to any 4.4 Ubuntu kernel that has available binaries on the mainline ppa. I do not use the headphone jack. USB-C 3.1b support is in its infancy and Thunderbolt3 support will be a while. I do not have an adapter to test DP support over USB-C/TB3. I know for certain that some of the dynamic current adjustment stuff is totally broken. So don't expect miracles just yet.
I'll also list the firmware I've been using along with quick instructions, but you should check out [https://wiki.ubuntu.com/Kernel/BuildYourOwnKernel](https://wiki.ubuntu.com/Kernel/BuildYourOwnKernel) for reference, too. The actual config change happens in line 8 below.

1- Get The Source: [FONT=courier new]git clone git://git.launchpad.net/~ubuntu-kernel-test/ubuntu/+source/linux/+git/mainline-crack cod/tip/drm-intel-next/daily[/FONT]
2 - [COLOR=#ff0000]Don't get the latest firmware from Vinod Koul's Skylake branch[/COLOR]:[FONT=courier new]git clone git://git.kernel.org/pub/scm/linux/kernel/git/vkoul/firmware.git --branch=skl skylake-firmware
[/FONT][COLOR=#00ff00]**EDIT**: Use the mainline linux-firmware git repo, as the skylake-audio changes have been pulled. The necessary Intel skl_dmc_ver1_23 and skl_guc_ver4_3 GPU scheduling and power states firmware blobs are also current there[/COLOR]: git clone git://git.kernel.org/pub/scm/linux/kernel/git/firmware/linux-firmware.git skylake-firmware
3 - Get the Debian/Ubuntu build patches for the kernel you want to build and put them in [FONT=courier new]cod/tip/drm-intel-next/daily[/FONT]: [0001-base-packaging.patch]("http://kernel.ubuntu.com/~kernel-ppa/mainline/drm-intel-next/2015-12-19-wily/0001-base-packaging.patch")   [0002-debian-changelog.patch]("http://kernel.ubuntu.com/~kernel-ppa/mainline/drm-intel-next/2015-12-19-wily/0002-debian-changelog.patch")  [0003-configs-based-on-Ubuntu-4.4.0-0.7.patch]("http://kernel.ubuntu.com/~kernel-ppa/mainline/drm-intel-next/2015-12-19-wily/0003-configs-based-on-Ubuntu-4.4.0-0.7.patch") are what I used today, but check [http://kernel.ubuntu.com/~kernel-ppa/mainline/drm-intel-next/current/](http://kernel.ubuntu.com/~kernel-ppa/mainline/drm-intel-next/current/) to make sure the nightly is actually producing a build before using. Same goes for mainiline or other DRM branches.
4 - Apply them in order: [FONT=courier new]cd cod/tip/drm-intel-next/daily; cat 0001* | patch -p1 && cat 0002* | patch -p1 && cat 0003* | patch -p1[/FONT] 
5 - Change some permissions: [FONT=courier new]chmod -R 755 debian/scripts* && chmod -R 755 debian/rules*[/FONT]
6 - Clean up, just in case: [FONT=courier new]fakeroot debian/rules clean[/FONT]
7 - disable the spl/zfs support. You don't want it. (this seems like a bug, too):[FONT=courier new] 'sed -i "s/do_zfs),false/do_zfs),true/g" debian/rules.d/2-binary-arch.mk'[/FONT]
8 - Cause NVMe to be built into the kernel, not as a module:[FONT=courier new] sed -i "s/CONFIG_BLK_DEV_NVME=m/CONFIG_BLK_DEV_NVME=y/g" debian.master/config/amd64/config.*
[FONT=tahoma]9 ** Optional ** edit your kernel config - this invokes make menuconfig for each supported architecture and variant. The only relevant one is amd64-generic. Lowlatency is buggy with new nvidia drivers and possibly others. Be careful!: [/FONT][COLOR=#333333]fakeroot debian/rules editconfigs
[FONT=tahoma]10- build (wait):[/FONT]fakeroot debian/rules binary-headers binary-generic
[FONT=tahoma]11 - While waiting, back up your existing firmware and install the new stuff:[FONT=courier new] pushd /lib/; sudo tar -cjvf firmware-backup.tar.bz2 ./firmware; popd; sudo cp -pr ../../../skylake-firmware/* /lib/firmware/; sudo chown -R root:root /lib/firmware 
[FONT=tahoma]12 - Check for a new Broadcom driver at kernel.org or broadcom.com. This is the most recent one I've pulled, which is scpecifically there to support the card in this laptop: [https://git.kernel.org/cgit/linux/kernel/git/firmware/linux-firmware.git/plain/brcm/brcmfmac43602-pcie.bin?id=77024948dd0dd43af2c53fe85f04eb18af16e3c4](https://git.kernel.org/cgit/linux/kernel/git/firmware/linux-firmware.git/plain/brcm/brcmfmac43602-pcie.bin?id=77024948dd0dd43af2c53fe85f04eb18af16e3c4) 
[/FONT][FONT=tahoma]13 - Copy that file to /lib/firmware/brcm/ and chown root:root it
[/FONT][FONT=tahoma]14 - If your kernel build has completed successfully, you should see several deb files one directory below your kernel source. Install all of them except for the cloud-tools and linux-tools packages. 
[/FONT][FONT=tahoma]15 - If you are running the proprietary nvidia drivers, you must reinstall: [FONT=courier new]dpkg-reconfigure [/FONT][/FONT][/FONT][/FONT][/COLOR]nvidia-358[/FONT], or whatever version you are using. If you have used Intel's graphics driver installer, run[FONT=courier new] &#8203;intel-linux-graphics-installer [FONT=tahoma]as well. It is possible you may need to boot with the Intel GPU enabled the first time you use the new kernel. I have not investigated this.
[/FONT][COLOR=#333333][FONT=tahoma][FONT=courier new][FONT=tahoma]16 - Running this after a new kernel install never hurts: [FONT=courier new]grub-mkconfig && update-grub2 [FONT=tahoma]- ** unless you are not using grub, of course
[/FONT][/FONT][/FONT][FONT=tahoma]17 - Reboot. Hope. Profit.
I hope this helps someone and doesn't just waste space.

Thanks
[/FONT][/FONT][/FONT]
[/COLOR][/FONT]

---

### Post by datigonachukamzlobno on 2015-12-21
@jchedstorm I registered specially to thank you for all the information you've pointed out in your post! I have been experiencing most of the listed problems on OpenSUSE Leap 42.1 as well. Many of your suggestions managed to solve my problems. I still have some strange issues and random freezes, though. Will try the 4.3.3 kernel soon and I hope that solves everything. At this point I only have to fix the suspend/hibernate issue and I have some flickering if my display goes black to save power. Once I move my mouse - the screen goes crazy and soon after the machine freezes.

I managed to solve the long booting problem. My current overall booting time is around 25-30 seconds which includes logging into my account in gnome. I was suspecting it had to do with the legacy boot options. That's why I decided to install OpenSUSE using a UEFI bootable USB drive. I created a special partition for UEFI in FAT. I also disabled "Legacy boot" in the bios and left only the UEFI boot. After the installation everything was working considerably faster. This might be some kind of a bug in the bios, even though I upgraded to the latest official version 01.00.07.

I hope this helps somebody else.

---

### Post by kjano on 2015-12-21
Just FYI, I am running kernel 4.3.3-040303-generic right now

---

### Post by quickdry21 on 2015-12-22
> **joshuabc said:**
> A while back I promised to share my kernel config, which has been quite stable. It's not at all different from other mainline or DRM 4.4 solutions, but if you feel like eliminating modules or features that don't apply to your hardware, you can. For my own laptop, I took out all non-intel CPU support, exotic networking stuff and 95% of all device drivers. For this example, I've left that stuff intact. What you will get is is NVMe support at boot without issue. You won't need AHCI unless you actually have a sata drive. You will have working suspend. You'll have zSwap enabled by default if you use swap - much kinder to SSDs. You'll have better TRIM support as well. You might have better PCIe power management - I'm looking into it. My 1TB Samsung 951 tends to get really, really hot, even at idle. Neither Intel NVMe drives under Linux, nor Samsung NVMe drives under other OSs seem to have any such problem, so there must be a fix.

Note that I'm using drm-intel-next here, not mainline, but this applies to any 4.4 Ubuntu kernel that has available binaries on the mainline ppa. I do not use the headphone jack. USB-C 3.1b support is in its infancy and Thunderbolt3 support will be a while. I do not have an adapter to test DP support over USB-C/TB3. I know for certain that some of the dynamic current adjustment stuff is totally broken. So don't expect miracles just yet.
I'll also list the firmware I've been using along with quick instructions, but you should check out [https://wiki.ubuntu.com/Kernel/BuildYourOwnKernel](https://wiki.ubuntu.com/Kernel/BuildYourOwnKernel) for reference, too. The actual config change happens in line 8 below.

1- Get The Source: [FONT=courier new]git clone git://git.launchpad.net/~ubuntu-kernel-test/ubuntu/+source/linux/+git/mainline-crack cod/tip/drm-intel-next/daily[/FONT]
2 - [COLOR=#ff0000]Don't get the latest firmware from Vinod Koul's Skylake branch[/COLOR]:[FONT=courier new]git clone git://git.kernel.org/pub/scm/linux/kernel/git/vkoul/firmware.git --branch=skl skylake-firmware
[/FONT][COLOR=#00ff00]**EDIT**: Use the mainline linux-firmware git repo, as the skylake-audio changes have been pulled. The necessary Intel skl_dmc_ver1_23 and skl_guc_ver4_3 GPU scheduling and power states firmware blobs are also current there[/COLOR]: git clone git://git.kernel.org/pub/scm/linux/kernel/git/firmware/linux-firmware.git skylake-firmware
3 - Get the Debian/Ubuntu build patches for the kernel you want to build and put them in [FONT=courier new]cod/tip/drm-intel-next/daily[/FONT]: [0001-base-packaging.patch]("http://kernel.ubuntu.com/~kernel-ppa/mainline/drm-intel-next/2015-12-19-wily/0001-base-packaging.patch")   [0002-debian-changelog.patch]("http://kernel.ubuntu.com/~kernel-ppa/mainline/drm-intel-next/2015-12-19-wily/0002-debian-changelog.patch")  [0003-configs-based-on-Ubuntu-4.4.0-0.7.patch]("http://kernel.ubuntu.com/~kernel-ppa/mainline/drm-intel-next/2015-12-19-wily/0003-configs-based-on-Ubuntu-4.4.0-0.7.patch") are what I used today, but check [http://kernel.ubuntu.com/~kernel-ppa/mainline/drm-intel-next/current/](http://kernel.ubuntu.com/~kernel-ppa/mainline/drm-intel-next/current/) to make sure the nightly is actually producing a build before using. Same goes for mainiline or other DRM branches.
4 - Apply them in order: [FONT=courier new]cd cod/tip/drm-intel-next/daily; cat 0001* | patch -p1 && cat 0002* | patch -p1 && cat 0003* | patch -p1[/FONT] 
5 - Change some permissions: [FONT=courier new]chmod -R 755 debian/scripts* && chmod -R 755 debian/rules*[/FONT]
6 - Clean up, just in case: [FONT=courier new]fakeroot debian/rules clean[/FONT]
7 - disable the spl/zfs support. You don't want it. (this seems like a bug, too):[FONT=courier new] 'sed -i "s/do_zfs),false/do_zfs),true/g" debian/rules.d/2-binary-arch.mk'[/FONT]
8 - Cause NVMe to be built into the kernel, not as a module:[FONT=courier new] sed -i "s/CONFIG_BLK_DEV_NVME=m/CONFIG_BLK_DEV_NVME=y/g" debian.master/config/amd64/config.*
[FONT=tahoma]9 ** Optional ** edit your kernel config - this invokes make menuconfig for each supported architecture and variant. The only relevant one is amd64-generic. Lowlatency is buggy with new nvidia drivers and possibly others. Be careful!: [/FONT][COLOR=#333333]fakeroot debian/rules editconfigs
[FONT=tahoma]10- build (wait):[/FONT]fakeroot debian/rules binary-headers binary-generic
[FONT=tahoma]11 - While waiting, back up your existing firmware and install the new stuff:[FONT=courier new] pushd /lib/; sudo tar -cjvf firmware-backup.tar.bz2 ./firmware; popd; sudo cp -pr ../../../skylake-firmware/* /lib/firmware/; sudo chown -R root:root /lib/firmware 
[FONT=tahoma]12 - Check for a new Broadcom driver at kernel.org or broadcom.com. This is the most recent one I've pulled, which is scpecifically there to support the card in this laptop: [https://git.kernel.org/cgit/linux/kernel/git/firmware/linux-firmware.git/plain/brcm/brcmfmac43602-pcie.bin?id=77024948dd0dd43af2c53fe85f04eb18af16e3c4](https://git.kernel.org/cgit/linux/kernel/git/firmware/linux-firmware.git/plain/brcm/brcmfmac43602-pcie.bin?id=77024948dd0dd43af2c53fe85f04eb18af16e3c4) 
[/FONT][FONT=tahoma]13 - Copy that file to /lib/firmware/brcm/ and chown root:root it
[/FONT][FONT=tahoma]14 - If your kernel build has completed successfully, you should see several deb files one directory below your kernel source. Install all of them except for the cloud-tools and linux-tools packages. 
[/FONT][FONT=tahoma]15 - If you are running the proprietary nvidia drivers, you must reinstall: [FONT=courier new]dpkg-reconfigure [/FONT][/FONT][/FONT][/FONT][/COLOR]nvidia-358[/FONT], or whatever version you are using. If you have used Intel's graphics driver installer, run[FONT=courier new] &#8203;intel-linux-graphics-installer [FONT=tahoma]as well. It is possible you may need to boot with the Intel GPU enabled the first time you use the new kernel. I have not investigated this.
[/FONT][COLOR=#333333][FONT=tahoma][FONT=courier new][FONT=tahoma]16 - Running this after a new kernel install never hurts: [FONT=courier new]grub-mkconfig && update-grub2 [FONT=tahoma]- ** unless you are not using grub, of course
[/FONT][/FONT][/FONT][FONT=tahoma]17 - Reboot. Hope. Profit.
I hope this helps someone and doesn't just waste space.

Thanks
[/FONT][/FONT][/FONT]
[/COLOR][/FONT]


joshuabc, Thanks again for taking the time to help those of us out who don't have this sort of experience (such as myself). After compiling 4.4 from drm-intel-nightly using the steps above, I was able to get HDMI->HDMI working. Unfortunately, this only worked when using the Intel gpu; NVIDIA had the usual problems, plugging in HDMI crashed gdm / X, and when it came back up the login flashed, then black, then the backlight flickering a couple times until stopping on black - dropping into a VT, unplugging HDMI and restarting gdm fixes things. As much as I would like to keep it on NVIDIA, I'm more than happy having to use Intel to get an external display going.

On this kernel suspend + resume worked, tearing was fairly noticeable but tolerable.

Couples notes on the build process in case any others newbs try it out:

* Definitely read over Ubuntu's build your own kernel guide - you need at the least to install some dependencies
* I had to install libssl-dev, build process complained about missing headers
* Step 7 caused the build to fail for me, not sure why do_zfs is different on my system but it was easy to tell this was the culprit, there was a comment about SPL/ZFS at the error. IIRC rsync was complaining about a directory not existing.
* I compiled from 4.4rc5, so dpkg-reconfigure nvidia-35* wouldn't target the new kernel to build modules for. Switching to Intel, booting into the new kernel and running dpkg-reconfigure caused nvidia modules being built for both current and newest kernel versions.
* Re running intel-linux-graphics-installer didn't seem to do anything, harmless step but I'm wondering what it was supposed to do.

Anyways, thanks again. I'm off for the holidays now but when I get back I'm really looking forward to being able to use one of my two external monitors! Who knows, maybe I'll even be able to get the other one going with USB-C -> DisplayPort. Hopefully in the mean time I will be able to get it all going with the nvidia gpu.

EDIT: added a couple steps

---

### Post by mflores3 on 2015-12-22
@joshuabc  can you share the *.hcd file you generated?  I'm having a hard time getting both bluetooth and wifi working at the same time. 

[SIZE=4]**Background:**[/SIZE]

I'm on XPS 15 9550 i5/1TB SSD SATA (I swapped in)/QHD - dual booting Linux Mint 17.3 and Windows 10

Earlier in this thread, @bertusrex provided a .hcd he compiled.  I copied to [COLOR=#696969][FONT=courier new]/lib/firmware/brcm[/FONT][/COLOR], but then noticed this dmesg output

```

[    4.631773] EXT4-fs (sda5): re-mounted. Opts: errors=remount-ro
[    4.744448] int3402 thermal: probe of INT3402:00 failed with error -22
[    5.016364] bluetooth hci0: Direct firmware load for brcm/BCM2045A0-0a5c-6410.hcd failed with error -2
[    5.016368] Bluetooth: hci0: BCM: patch brcm/BCM2045A0-0a5c-6410.hcd not found
```

So then I tried [COLOR=#696969][FONT=courier new]sudo cp  BCM-0a5c-6410.hcd BCM2045A0-0a5c-6410.hcd[/FONT][/COLOR] - bluetooth works perfectly, but this kills the wifi somehow.  I have to reload factory bios settings to get it to work again, then of course, my bluetooth is not working again.  I tried the 

I tried the bcmwl-kernel-source_6.30.223.248+bdcom package in the driver manager, but my laptop just freezes attempting to apply and the broadcom option disappears from my driver manager.

[SIZE=4]**FYI For others:**[/SIZE]

Other users: Linux mint 17.3 worked out of the box w/ the [COLOR=#696969][FONT=courier new]nouveau.modeset=0[/FONT][/COLOR] trick others mentioned.  Graphics were slow, but after install proper nvidia and intel drivers others mentioned, no problem.  - graphics drivers can be found here: [https://01.org/linuxgraphics/downloads/skylake-dmc-1.23](https://01.org/linuxgraphics/downloads/skylake-dmc-1.23). HDMI worked no issue. I ran into additional issues when i attempted upgrades to kernel 4.2 or 4.3, so I just kept the default 3.19.  Still issues: headphone jack doesn't work and bluetooth issue mentioned above.

---

### Post by joshuabc on 2015-12-22
Hi,

Actually, I did not go that route myself. I don't know that it's absolutely necessary with this particular card in 4.4. I have extracted the hcd file for another broadcom bluetooth/wifi combo card in the past, though. Basically, you need to do this: 
1- download the Windows driver from Broadcom.
2 - run the self-extracting exe under Windows or use cabextract under Linux
3 - Find the device id using[FONT=Courier New] lspci -nn [/FONT]- you'll see a pair of 4-digit hex numbers. The first is the Manufacturer ID, the second is the device ID. For this machine it's 43ba
4 - grep for the device ID in the extracted Windows drivers' .inf files - [FONT=courier new]find ./extracted-drivers-dir -iname "*.inf" -exec grep -i "43ba" {} + [/FONT] 
5 - grab the hcd file corresponding to the output of the above command. There should be only one match.
6 - chown it root:root and put it under /lib/firmware/ or /lib/firmware/brcm/ ** I'm not sure which, but having 2 copies won't do any harm. 

That said, I am getting basic BT support without any additional firmware. I don't rely on it for anything, so I certainly can't say it's "working," but if loading an hcd is killing wifi, I'd call that a bad sign. Sorry I can't help more... last work day before the holidays.

Cheers,

---

### Post by marco furio ferrario on 2015-12-23
Many users claims RAID mode is faster for this configuration and gives less problems (in fact dell sends it in raid): can you prove AHCI is better?
in my understanding pm951 is NVMe which is newer than both AHCI and RAID but it is not currently supported by xps 9550 bios (in fact there is no option to boot from NVMe, so if RAID works better why bother trying AHCI if is not even its native setting?

These are my speculations but I would kindly welcome any better explanation from someone more experienced than me.
Best

---

### Post by joshuabc on 2015-12-23
> **quickdry21 said:**
> 
* Step 7 caused the build to fail for me, not sure why do_zfs is different on my system but it was easy to tell this was the culprit, there was a comment about SPL/ZFS at the error. IIRC rsync was complaining about a directory not existing.


That's interesting... it actually *should* cause the build to fail, but with the last several ubuntu patch sets and the drm source, it would try to build zfs support when I didn't have the zfs/spl source present. That was the quickest one-liner I could come up with to fix it.

> * I compiled from 4.4rc5, so dpkg-reconfigure nvidia-35* wouldn't target the new kernel to build modules for. Switching to Intel, booting into the new kernel and running dpkg-reconfigure caused nvidia modules being built for both current and newest kernel versions.
* Re running intel-linux-graphics-installer didn't seem to do anything, harmless step but I'm wondering what it was supposed to do.

The nvidia driver does install for me once I've installed all the 4.4 debs, without rebooting. As for the intel drivers, you're absolutely correct - the step isn't necessary. If there *were* an update available, however, you'd get it by running[FONT=Courier New] sudo intel-linux-graphics-installer[/FONT]

Thanks for the feedback... Good Luck.
Cheers

---

### Post by indigo00862 on 2015-12-24
What is everyone averaging on battery life. On intel mode I'm getting well under 5 hours.  Not really what I was looking for.

---

### Post by jyrinx on 2015-12-25
> **quickdry21 said:**
> To anyone experiencing the issue of being dropped to BusyBox after installing 4.4 - it's caused by this bug: [http://comments.gmane.org/gmane.linux.debian.devel.bugs.general/1310268](http://comments.gmane.org/gmane.linux.debian.devel.bugs.general/1310268)

To fix this you just need to add the nvme module to the initramfs.

I installed rc5 mainline .deb files here:

[http://kernel.ubuntu.com/~kernel-ppa/mainline/v4.4-rc5-wily/](http://kernel.ubuntu.com/~kernel-ppa/mainline/v4.4-rc5-wily/)

Then, add the nvme module:

```

echo nvme | sudo tee -a /etc/initramfs-tools/modules
sudo update-initramfs -u

```

Many thanks! Worked like a charm. 4.4.0-997 (on intel-drm-next) seems to have fixed my suspend/resume *and* the trackpad!

> **marco furio ferrario said:**
> Many users claims RAID mode is faster for this configuration and gives less problems (in fact dell sends it in raid): can you prove AHCI is better?
in my understanding pm951 is NVMe which is newer than both AHCI and RAID but it is not currently supported by xps 9550 bios (in fact there is no option to boot from NVMe, so if RAID works better why bother trying AHCI if is not even its native setting?

AFAICT, AHCI mode is a misnomer nowadays; it really just means “no RAID but not stone-age mode.” By every indication, I'm still using NVMe even though “AHCI mode” is on:

```
luke@velvetspoon ~ $ mount | grep nvme
/dev/nvme0n1p6 on / type ext4 (rw,relatime,errors=remount-ro,data=ordered)
/dev/nvme0n1p1 on /boot/efi type vfat (rw,relatime,fmask=0022,dmask=0022,codepage=437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)
```

---

### Post by Jan_Drewes on 2015-12-26
Hello,

just wanted to share my 5cents. I am using a Precision 5510, which is identical to the XPS 9550 in many ways, except it has a Xeon CPU, intel wifi/bluetooth and a Quadro M1000M graphics (which runs with the same nvidia driver, however). Thanks to quickdry21's tip with the nvme module, I am now running on mainline kernel 4.4rc5, where so far everything seems to work; however sometimes, the intel drivers give me some flicker in the upper half of the screen (4k). Switching screen compositing in Kubuntu form OpenGL 3.1 to 2 and back (or the other way, doesn't matter) fixes it.

I had some trouble during my initial install, as somehow the Kubuntu installer managed to corrupt the EFI partition (fixed easily enough by fsck, but that took a while to figure out). I do not know how exactly that happened, there was no error message etc. until I couldn't boot any more.

I have a PM951 Samsung SSD installed - what do other people have? Is it always a Samsung?

Cheers and enjoy the remaining holidays

---

### Post by joshuabc on 2015-12-26
> **marco furio ferrario said:**
> Many users claims RAID mode is faster for this configuration and gives less problems (in fact dell sends it in raid): can you prove AHCI is better?


It's not that one is necessarily "better" than the other. In my configuration, with the stock 512G Samsung NVMe and the sata bay occupied by a battery, switching from "RAID" to "AHCI" is actually just enabling AHCI emulation at boot time. This is still necessary for the Ubuntu live image/installer to run correctly. Once a modern OS, be it Windows or Linux, is running, you are accessing the device via its native interface and should experience absolutely no difference in function or performance. The AHCI emulation is basically presenting your SSD as a traditional "block device" using an industry-standard interface which requires no device driver. In reality, an NVM device is not a block device at all, but a Non-Volatile Memory device - with the e meaning it's attached via PCIe. It's a bit more like RAM than a hard drive, but it retains state in the absence of power. Other NVM devices actually replace main memory with non-volatile memory to implement "stateful" systems, which can power off without rebooting... but that's probably a bit more computer science than you were looking for.

Intel's RAID is actually software RAID, not the kind of thing you might find in a big RAID array. I'm actually not sure what Dell is using it for, since my Windows partition was backed up and wiped on day 1. It's extremely unlikely to give you any additional performance, even with both the 2.5" bay and the little M.2 bay filled with fast SSDs. What it could be used for is something akin to Apple's Fusion Drive idea (via JBOD), or to provide redundant copies (via RAID 1) of the EFI boot area. I really don't know...

But the performance issue is, well, not an issue.

Cheers,

---

### Post by mlippert on 2015-12-27
joshuabc,
Just wanted to say thanks for your initial post about building a kernel (I haven't tried it yet, but it was definitely NOT wasted space, I learned a lot just reading it), and also for your extremely informative replies to other questions here. All of them have taught me new stuff that I hadn't known and would have taken a fair amount of time searching to learn on my own, assuming I knew enough to narrow my search!

I haven't gotten an XPS 15 9550 yet, but it's at the top of my list, mostly because the Dell XPS line seems to have better linux support (eventually anyway ;)). I'm following this thread to see what the current state is, because I don't really want Win 10 (it's too invasive). I suspect that I'll get an XPS 15 once the usb-c docking station is available from Dell, so hopefully soon.

Meantime I'll be lurking on this thread, to see how things are progressing.

---

### Post by Calin Balaurul on 2015-12-29
Anyone had any luck getting the card reader to work?

---

### Post by zeratul2 on 2015-12-29
Yes it just works. Haven't done anything.

---

### Post by zeratul2 on 2015-12-29
Who managed to get his touchpad up to the level where it is really as good as it is under windows and comparable to a macbook?
I mean, thumb detection, three finger swipe gestures, ...?
Still struggling with it

---

### Post by anthony-towler on 2015-12-29
I'm using a KDE based Ubuntu derivative named Netrunner, so I'm not sure if Ubuntu/Kubuntu users are seeing the same thing, but when I select the Nvidia profile through prime and reboot I randomly get dropped to a black/blank screen. I'd say maybe 1 out of 10 times I actually get the login screen. It works fine when I do get the login prompt (sddm), but it's highly inefficient to have to reboot a bunch of times before I can use it. Intel seems to work fine (I was seeing a bunch of tearing and flickering, but the 4.4-rc7 kernel seems to have solved that). I'm seeing the black screen on boot with all the Nvidia drivers from the PPA (352/355/358). Anyone have any ideas? Is this a known bug? Is anyone else seeing this?

---

### Post by jyrinx on 2015-12-29
> **joshuabc said:**
> The AHCI emulation is basically presenting your SSD as a traditional "block device" using an industry-standard interface which requires no device driver. In reality, an NVM device is not a block device at all, but a Non-Volatile Memory device - with the e meaning it's attached via PCIe.

Interesting—I didn't realize they're not block devices:

```
luke@velvetspoon ~ $ ls -l /dev/nvme0
crw------- 1 root root 248, 0 Dec 29 20:34 /dev/nvme0

```

Looks like the partitions *are* block devices, but that must be some sort of shim at the kernel level (partitions aren't really devices anyway).

---

### Post by Johannes_Stickel on 2015-12-30
I've setup my new XPS 15 9550 with Kubuntu 15.10 and a 4.4.0-994-generic kernel (201512232104). Most things seem to work properly.

However, my sound card is missing. It seems to be completely undetected. And lspci does not return any sound card either.  Reading the other responses I've got the notion that the sound card should be working without any issues.

Does anybody have an idea, how to fix it? Shouldn't it be listed by lspci? Which kernel modules are needed?

---

### Post by anthony-towler on 2015-12-30
> **Johannes_Stickel said:**
> I've setup my new XPS 15 9550 with Kubuntu 15.10 and a 4.4.0-994-generic kernel (201512232104). Most things seem to work properly.

However, my sound card is missing. It seems to be completely undetected. And lspci does not return any sound card either.  Reading the other responses I've got the notion that the sound card should be working without any issues.

Does anybody have an idea, how to fix it? Shouldn't it be listed by lspci? Which kernel modules are needed?

Sound works for me. Do headphones and speakers both not work? Do you see an output device selected in your audio settings? Try running alsamixer and pavucontrol in the terminal to make sure nothing is muted. This is what 'lspci' returns for me on Netrunner 17, which is a KDE distro based on Ubuntu 15.10:

00:00.0 Host bridge: Intel Corporation Sky Lake Host Bridge/DRAM Registers (rev 07)
00:01.0 PCI bridge: Intel Corporation Sky Lake PCIe Controller (x16) (rev 07)
00:02.0 VGA compatible controller: Intel Corporation Device 191b (rev 06)
00:04.0 Signal processing controller: Intel Corporation Device 1903 (rev 07)
00:14.0 USB controller: Intel Corporation Sunrise Point-H USB 3.0 xHCI Controller (rev 31)
00:14.2 Signal processing controller: Intel Corporation Sunrise Point-H Thermal subsystem (rev 31)
00:15.0 Signal processing controller: Intel Corporation Sunrise Point-H LPSS I2C Controller #0 (rev 31)
00:15.1 Signal processing controller: Intel Corporation Sunrise Point-H LPSS I2C Controller #1 (rev 31)
00:16.0 Communication controller: Intel Corporation Sunrise Point-H CSME HECI #1 (rev 31)
00:17.0 SATA controller: Intel Corporation Sunrise Point-H SATA Controller [AHCI mode] (rev 31)
00:1c.0 PCI bridge: Intel Corporation Sunrise Point-H PCI Express Root Port #1 (rev f1)
00:1c.1 PCI bridge: Intel Corporation Sunrise Point-H PCI Express Root Port #2 (rev f1)
00:1d.0 PCI bridge: Intel Corporation Sunrise Point-H PCI Express Root Port #9 (rev f1)
00:1d.4 PCI bridge: Intel Corporation Sunrise Point-H PCI Express Root Port #13 (rev f1)
00:1d.6 PCI bridge: Intel Corporation Sunrise Point-H PCI Express Root Port #15 (rev f1)
00:1f.0 ISA bridge: Intel Corporation Sunrise Point-H LPC Controller (rev 31)
00:1f.2 Memory controller: Intel Corporation Sunrise Point-H PMC (rev 31)
00:1f.3 Audio device: Intel Corporation Sunrise Point-H HD Audio (rev 31)
00:1f.4 SMBus: Intel Corporation Sunrise Point-H SMBus (rev 31)
01:00.0 3D controller: NVIDIA Corporation GM107M [GeForce GTX 960M] (rev a2)
02:00.0 Network controller: Broadcom Corporation BCM43602 802.11ac Wireless LAN SoC (rev 01)
03:00.0 Unassigned class [ff00]: Realtek Semiconductor Co., Ltd. Device 525a (rev 01)
04:00.0 Non-Volatile memory controller: Samsung Electronics Co Ltd Device a802 (rev 01)

---

### Post by Johannes_Stickel on 2015-12-31
> **anthony-towler said:**
> Sound works for me. Do headphones and speakers both not work? Do you see an output device selected in your audio settings? Try running alsamixer and pavucontrol in the terminal to make sure nothing is muted.

Both do not work. There is no output and no input device. pavucontrol does only show a "dummy output" and alsamixer says "cannot open mixer: No such file or directory"

Running lscpi gives me exactly the same output, except the line
```
00:1f.3 Audio device: Intel Corporation Sunrise Point-H HD Audio (rev 31)
```
is missing.
 
Which kernel do you use? Did you have to do anything to get sound working? Do you know, which kernel modules have to be loaded?

---

### Post by Jan_Drewes on 2015-12-31
anthony-towler,

I am seeing the same thing here. In fact I can't remember ever seeing anything but black with nvidia selected, I only use intel. I gave up on nvidia for the time being. You might want to try using recovery mode, then select resume to see if that gets you anywhere?

Cheers,
Jan

---

### Post by anthony-towler on 2016-01-01
> **Johannes_Stickel said:**
> Both do not work. There is no output and no input device. pavucontrol does only show a "dummy output" and alsamixer says "cannot open mixer: No such file or directory"

Running lscpi gives me exactly the same output, except the line
```
00:1f.3 Audio device: Intel Corporation Sunrise Point-H HD Audio (rev 31)
```
is missing.
 
Which kernel do you use? Did you have to do anything to get sound working? Do you know, which kernel modules have to be loaded?

I compiled the 4.4-rc7 kernel from source from [http://kernel.ubuntu.com/~kernel-ppa/mainline/v4.4-rc7-wily/](http://kernel.ubuntu.com/~kernel-ppa/mainline/v4.4-rc7-wily/)

There are .debs at the address above as well. Assuming you have a 64-bit installation you'd want the following:

[http://kernel.ubuntu.com/~kernel-ppa/mainline/v4.4-rc7-wily/linux-headers-4.4.0-040400rc7-generic_4.4.0-040400rc7.201512272230_amd64.deb](http://kernel.ubuntu.com/~kernel-ppa/mainline/v4.4-rc7-wily/linux-headers-4.4.0-040400rc7-generic_4.4.0-040400rc7.201512272230_amd64.deb)
[http://kernel.ubuntu.com/~kernel-ppa/mainline/v4.4-rc7-wily/linux-headers-4.4.0-040400rc7_4.4.0-040400rc7.201512272230_all.deb](http://kernel.ubuntu.com/~kernel-ppa/mainline/v4.4-rc7-wily/linux-headers-4.4.0-040400rc7_4.4.0-040400rc7.201512272230_all.deb)
[http://kernel.ubuntu.com/~kernel-ppa/mainline/v4.4-rc7-wily/linux-image-4.4.0-040400rc7-generic_4.4.0-040400rc7.201512272230_amd64.deb](http://kernel.ubuntu.com/~kernel-ppa/mainline/v4.4-rc7-wily/linux-image-4.4.0-040400rc7-generic_4.4.0-040400rc7.201512272230_amd64.deb)

Then install them with:

sudo dpkg -i linux-*.deb

I didn't have to do any kernel config to get sound to work. I'm not sure which kernel modules need to be loaded. I can check what I have loaded when I am at that machine again.

EDIT

I checked what I have loaded and these are what are loaded relating to sound:

```

[FONT=monospace][COLOR=#1818B2]->[/COLOR][COLOR=#5454FF]** %**[/COLOR][COLOR=#000000] lsmod | grep snd[/COLOR]
[COLOR=#FF5454]**snd**[/COLOR][COLOR=#000000]_hda_codec_hdmi     49152  1[/COLOR]
[COLOR=#FF5454]**snd**[/COLOR][COLOR=#000000]_hda_codec_realtek    81920  1[/COLOR]
[COLOR=#FF5454]**snd**[/COLOR][COLOR=#000000]_hda_codec_generic    73728  1 [/COLOR][COLOR=#FF5454]**snd**[/COLOR][COLOR=#000000]_hda_codec_realtek[/COLOR]
[COLOR=#FF5454]**snd**[/COLOR][COLOR=#000000]_hda_intel          36864  5[/COLOR]
[COLOR=#FF5454]**snd**[/COLOR][COLOR=#000000]_hda_codec         135168  4 [/COLOR][COLOR=#FF5454]**snd**[/COLOR][COLOR=#000000]_hda_codec_realtek,[/COLOR][COLOR=#FF5454]**snd**[/COLOR][COLOR=#000000]_hda_codec_hdmi,[/COLOR][COLOR=#FF5454]**snd**[/COLOR][COLOR=#000000]_hda_codec_generic,[/COLOR][COLOR=#FF5454]**snd**[/COLOR][COLOR=#000000]_hda_intel[/COLOR]
[COLOR=#FF5454]**snd**[/COLOR][COLOR=#000000]_hda_core           65536  5 [/COLOR][COLOR=#FF5454]**snd**[/COLOR][COLOR=#000000]_hda_codec_realtek,[/COLOR][COLOR=#FF5454]**snd**[/COLOR][COLOR=#000000]_hda_codec_hdmi,[/COLOR][COLOR=#FF5454]**snd**[/COLOR][COLOR=#000000]_hda_codec_generic,[/COLOR][COLOR=#FF5454]**snd**[/COLOR][COLOR=#000000]_hda_codec,[/COLOR][COLOR=#FF5454]**snd**[/COLOR][COLOR=#000000]_hda_intel[/COLOR]
[COLOR=#FF5454]**snd**[/COLOR][COLOR=#000000]_hwdep              16384  1 [/COLOR][COLOR=#FF5454]**snd**[/COLOR][COLOR=#000000]_hda_codec[/COLOR]
[COLOR=#FF5454]**snd**[/COLOR][COLOR=#000000]_pcm               102400  5 [/COLOR][COLOR=#FF5454]**snd**[/COLOR][COLOR=#000000]_hda_codec_hdmi,[/COLOR][COLOR=#FF5454]**snd**[/COLOR][COLOR=#000000]_hda_codec,[/COLOR][COLOR=#FF5454]**snd**[/COLOR][COLOR=#000000]_hda_intel,[/COLOR][COLOR=#FF5454]**snd**[/COLOR][COLOR=#000000]_hda_core[/COLOR]
[COLOR=#FF5454]**snd**[/COLOR][COLOR=#000000]_seq_midi           16384  0[/COLOR]
[COLOR=#FF5454]**snd**[/COLOR][COLOR=#000000]_seq_midi_event     16384  1 [/COLOR][COLOR=#FF5454]**snd**[/COLOR][COLOR=#000000]_seq_midi[/COLOR]
[COLOR=#FF5454]**snd**[/COLOR][COLOR=#000000]_rawmidi            32768  1 [/COLOR][COLOR=#FF5454]**snd**[/COLOR][COLOR=#000000]_seq_midi[/COLOR]
[COLOR=#FF5454]**snd**[/COLOR][COLOR=#000000]_seq                69632  2 [/COLOR][COLOR=#FF5454]**snd**[/COLOR][COLOR=#000000]_seq_midi_event,[/COLOR][COLOR=#FF5454]**snd**[/COLOR][COLOR=#000000]_seq_midi[/COLOR]
[COLOR=#FF5454]**snd**[/COLOR][COLOR=#000000]_seq_device         16384  3 [/COLOR][COLOR=#FF5454]**snd**[/COLOR][COLOR=#000000]_seq,[/COLOR][COLOR=#FF5454]**snd**[/COLOR][COLOR=#000000]_rawmidi,[/COLOR][COLOR=#FF5454]**snd**[/COLOR][COLOR=#000000]_seq_midi[/COLOR]
[COLOR=#FF5454]**snd**[/COLOR][COLOR=#000000]_timer              32768  2 [/COLOR][COLOR=#FF5454]**snd**[/COLOR][COLOR=#000000]_pcm,[/COLOR][COLOR=#FF5454]**snd**[/COLOR][COLOR=#000000]_seq[/COLOR]
[COLOR=#FF5454]**snd**[/COLOR][COLOR=#000000]                    81920  20 [/COLOR][COLOR=#FF5454]**snd**[/COLOR][COLOR=#000000]_hda_codec_realtek,[/COLOR][COLOR=#FF5454]**snd**[/COLOR][COLOR=#000000]_hwdep,[/COLOR][COLOR=#FF5454]**snd**[/COLOR][COLOR=#000000]_timer,[/COLOR][COLOR=#FF5454]**snd**[/COLOR][COLOR=#000000]_hda_codec_hdmi,[/COLOR][COLOR=#FF5454]**snd**[/COLOR][COLOR=#000000]_pcm,[/COLOR][COLOR=#FF5454]**snd**[/COLOR][COLOR=#000000]_seq,[/COLOR][COLOR=#FF5454]**snd**[/COLOR][COLOR=#000000]_rawmidi,[/COLOR][COLOR=#FF5454]**snd**[/COLOR][COLOR=#000000]_hda_codec_generic,[/COLOR][COLOR=#FF5454]**snd**[/COLOR][COLOR=#000000]_hda_codec,[/COLOR][COLOR=#FF5454]**snd**[/COLOR][COLOR=#000000]_hda_intel,[/COLOR][COLOR=#FF5454]**snd**[/COLOR][COLOR=#000000]_seq_device[/COLOR]
soundcore              16384  1 [COLOR=#FF5454]**snd**[/COLOR]
[/FONT]
```

Does 'aplay -l' say no soundcards are installed also?

---

### Post by Johannes_Stickel on 2016-01-02
Changing the kernel did not help. However after I turned off the audio  controller in the BIOS settings, rebooted and turned it on again, it  suddenly worked :)

---

### Post by bertusrex on 2016-01-02
There's a new bios version for the XPS 15 9550: 1.15. It's probably not yet available as a stand-alone file from the Dell support download section, but you can get it by booting Windows, going to device manager, right-clicking firmware, and select update drivers. After a full reboot your bios is updated to 1.15.

This version seems to fix the ac->battery->ac speed cap on my **i5**. However I have the impression that under Windows the CPU speed is now limited to 2.3GHz 

edit: Mistake on my part: original Windows scores I mentioned were with powersave profile, the ones below are with high performance profile enabled, and are a lot closed to eachother:
[Here's my Geekbench 3 scores ]("http://browser.primatelabs.com/geekbench3/compare/4762378?baseline=4762957") (free 32 bit version), both from my own laptop with Bios .15

---

### Post by rvanderwerf on 2016-01-03
bertusrex - any difference you noticed yet under ubuntu? I'm on 1.05 and reboots take a very long time. Like it's rebooting 2-3 times before it's done.

---

### Post by bertusrex on 2016-01-03
> **rvanderwerf said:**
> bertusrex - any difference you noticed yet under ubuntu? I'm on 1.05 and reboots take a very long time. Like it's rebooting 2-3 times before it's done.

Power consumption under Ubuntu seems about the same as before to me. I'm inclined to say that under Windows it has  slightly improved with 1.15, but that's subjective. As a test I left my i5/FHD/56kWh running idle, 30% brightness, no sleep, firefox on google.com, wireless and bluetooth on, and it ran for about 9 hours (this is not typical use though). A 1080p movie on repeat in Windows media player lasted about 6 hours (30% brightness, file from SSD, wireless and BT on, screen on).

I don't suffer from long boot times (not before 1.15 either). I'm probably booting slightly different than you: from a mSata SSD (not in the M.2 slot, but in the sata  1TB harddisks spot, with SSD bracket). I've got a GPT partition table on it, with EFI partition with grub2. Boots pretty quickly (except for the Dell logo delay before booting).

---

### Post by rvanderwerf on 2016-01-03
I only get the long boots when doing a soft reboot from ubuntu. If I power off, it's much faster. It's very odd for sure, seems like a bios bug of some sort! I only have the p951 1tb in the m.2 slot not sure if that is related or not.

---

### Post by bertusrex on 2016-01-05
There's a [new beta nvidia driver (361.16)]("http://www.nvidia.com/download/driverResults.aspx/97303/en-us"). It's not yet in the graphics-drivers ppa, but maybe someone here already tried installing it manually?

---

### Post by quickdry21 on 2016-01-05
I see there is a new bios available: 01.01.15. Anyone tried it out yet?

---

### Post by bertusrex on 2016-01-06
> **quickdry21 said:**
> I see there is a new bios available: 01.01.15. Anyone tried it out yet?

See a few posts back...

---

### Post by Calin Balaurul on 2016-01-07
> **zeratul2 said:**
> Yes it just works. Haven't done anything.

What ubuntu and kernel version are you running?

---

### Post by bertusrex on 2016-01-07
Today I had a kind of glitch that I haven't seen before:

After resuming my XPS 15 (i5) from suspend it felt very sluggish. It turned out that the cpu frequency was locked around a very slow 400-500 MHz. This is outside of the specified range from 800-3200 MHz:

```
$ cat /proc/cpuinfo | grep MHz
cpu MHz        : 418.042
cpu MHz        : 415.886
cpu MHz        : 442.839
cpu MHz        : 417.593
$ cat /sys/devices/system/cpu/cpu0/cpufreq/scaling_m??_freq 
3200000
800000
$ cat /sys/devices/system/cpu/cpu0/cpufreq/cpuinfo_m??_freq
3200000
800000

```

What I tried to get cpu back to normal (in the same session) without succes:
- Changing governors (powersave/performance) 
- Stressing the CPU
- suspending and waking again

cpu freq, stays between 400 and 500 MHz all the time. I had to reboot to get it back to normal. 

Running Ubuntu 15.10 with kernel 4.4.0-040400rc7-generic #201512272230 SMP, with the newest Dell bios 1.15

---

### Post by kjano on 2016-01-08
Did anybody manage to get HDMI work reliably?  I can get it working but it takes 1-3 minutes on average and in some cases requires multiple restarts. This is totally unacceptable when having to connect to a projector in front of a large group or when you have to switch between different external screens regularly. I have similar issues with a HDMI to VGA converter. I also ordered a USB-C to HDMI cable and hope that this will help.

---

### Post by quickdry21 on 2016-01-09
> **kjano said:**
> Did anybody manage to get HDMI work reliably?  I can get it working but it takes 1-3 minutes on average and in some cases requires multiple restarts. This is totally unacceptable when having to connect to a projector in front of a large group or when you have to switch between different external screens regularly. I have similar issues with a HDMI to VGA converter. I also ordered a USB-C to HDMI cable and hope that this will help.

I finally managed to get both HDMI -> HDMI and USB-C -> DisplayPort (using the cable from monoprice), at the same time. I'm using 4.4-rc7 of intel-drm-nightly and nvidia-355 (pretty sure) and nvidia-prime. I couldn't for the life of me get anything working on the nvidia gpu, so I'm forced to use the integrated intel gpu. As I have the QHD hidpi version, I'm using xrandr to scale the resolution on the two external monitors.

Before scaling the resolution everything runs great, no crashes, but unusable on the external displays due to Gnome scaling the gui. Once I scale the resolution using xrandr I get X crashes galore. Usually I get a crash or two when calling the xrandr command, usually a crash or two when opening up applications (slack and chrome seem to be the worst), dragging applications across monitors becomes almost impossible. Starting applications first and putting them on the proper monitor before calling xrandr seems to be the most reliable. Once I get everything up and running and the resolution scaled using xrandr, everything is (mostly) stable throughout the day - I may get a crash or two in an 8 hour period.

A crash is the desktop environment dying, screen flickering black a few times and then dropping me back to the login. Usually when this happens the login will be the wrong resolution, dropping into a virtual terminal and restarting gdm is required. 

A few other notes:

* When using the intel gpu tearing is *significantly* noticeable - new messages in slack can take a second or two to display. This gets worse after scaling the resolution. I really hope to find a way to use the nvidia gpu with nvidia-prime - I'm plugged in all day so the power savings bring no benefit. That or reduce the tearing.
* Hot plugging seems to crash every time. The external displays need to be plugged in before starting up the laptop. 
* Running on battery seems to cause lots of issues when running external monitors scaled with xrandr. I am running TLP, this might be related / the cause. 
* Tried daisy chaining two Dell U2414H monitors with MST - hard restart required, booting plugged in caused kernel panic. Didn't try too hard on this.
* Tried without resolution scaling with xrandr, setting chrome's --force-device-scaling-factor 1 provided ok results but the text in the gui is too big.

Anyways, I have a mostly working setup but I'm in the same boat as you, it takes a few attempts before everything is working. If you are using gnome I do have one suggestion, you don't have to restart, you can restart gdm from a virtual terminal: 

1. <ctrl>+<alt>+<F1> brings you to a virtual terminal
2. Login
3. sudo service gdm restart

At this point I've given up trying to improve the situation. Things are mostly working and this is a work laptop so I can't afford losing more time having to reinstall the os if things go south again. I'm hoping as time passes the Linux kernel will improve support and people with more experience hacking on Ubuntu will figure out the issues and share their knowledge. 

EDIT: clarifications

---

### Post by oolong2 on 2016-01-09
I got the non-NVIDIA version of the XPS 15 9550, and I added a M.2 256 GB 950 Pro SSD and 2.5" 256 GB 850 Pro SSD (with the goal of having Ubuntu on the M.2 and Win10 on the 2.5" SSD). Thanks to @jchedstrom for the good info for getting started. So far my main issue is with the Broadcom wifi card [14e4:43a3] (rev 08) not working.

So far I have:

[LIST]
[*]updated to BIOS v01.01.15
[*]set to AHCI mode in BIOS
[*]turned on Legacy mode
[*]used @jchedstrom's touchpad fix
[*]installed ubuntu 15.10
[*]installed GNOME v3.16.4
[*]upgraded the kernel version from 4.2.0-23-generic to 4.4.0-040400rc8-generic
[/LIST]

One thing during the kernel upgrade. When running 'dpkg -i *.deb', it showed the following warning: ```
W: Possible missing firmware /lib/firmware/i915/skl_guc_ver4.bin for module i915
``` so I downloaded sklgucver43.tar.bz2 from [https://01.org/linuxgraphics/downloads/sklgucver43](https://01.org/linuxgraphics/downloads/sklgucver43) and ran the install file as well as rerunning 'dpkg' (no more warning). I rebooted but came across an initramfs error (something like "gave up waiting for root device"). Turns out I forgot to add "nvme" to the '/etc/initramfs-tools/modules' file and run 'update-initramsf -u'. 

After rebooting, things were fine (boot from M.2 SSD, Ethernet via USB working, Bluetooth working, 2.5" SSD recognized, full battery estimation at 5:27). Have not tested Thunderbolt or HDMI yet. Still wifi is not working though; it shows up in 'lspci' but network interface for wlan does not show up.

I tried 'git clone git://git.kernel.org/pub/scm/linux/kernel/git/dwmw2/linux-firmware.git' and copying the 'brcmfmac4350-pcie.bin' file to '/live/firmware/brcm/' but no luck.

Is there something I'm missing? I've read that kernel version 4.4 should work but perhaps I missed a step during kernel upgrade. Thanks in advance for any help, and let me know if someone needs more details on how I installed/upgraded.

[UPDATE Jan. 11, 2016]

Thank you to @bertusrex and @mflores3 for the help. 

@mflores3, I successfully followed your steps for the Bluetooth driver (turns out it *was* failing to load). I also found the file on the original Windows at 'C:\Windows\System32\drivers\BCM4350C5_003.006.007.0095.1703.hex', converted to *.hcd, and put it in /lib/firmware/brcm/. This fixed the firmware loading error, although I have not thoroughly tested Bluetooth.

For the wifi fix, I cloned linux-firmware with 'git clone git://git.kernel.org/pub/scm/linux/kernel/git/firmware/linux-firmware.git' and made sure that I had the /brcm/ files in my /lib/firmware/brcm/ (most importantly that I had 'brcmfmac4350-pcie.bin'). Finally, I ran 'apt-get purge bcmwl-kernel-source broadcom-sta-common broadcom-sta-source b43-fwcutter firmware-b43legacy-installer' to get rid of any old Broadcom drivers. This apt-get purging also fixed ubuntu hanging at shutdown. After rebooting, wifi finally worked!

Unfortunately I did not try @bertusrex's suggestion about the BIOS flashing so I don't know if this will or will not work for anyone else.

---

### Post by bertusrex on 2016-01-11
> **oolong2 said:**
> I got the non-NVIDIA version of the XPS 15 9550, and I added a M.2 256 GB 950 Pro SSD and 2.5" 256 GB 850 Pro SSD (with the goal of having Ubuntu on the M.2 and Win10 on the 2.5" SSD). Thanks to @jchedstrom for the good info for getting started. So far my main issue is with the Broadcom wifi card [14e4:43a3] (rev 08) not working.
...
Is there something I'm missing? I've read that kernel version 4.4 should work but perhaps I missed a step during kernel upgrade. Thanks in advance for any help, and let me know if someone needs more details on how I installed/upgraded.

You can try resetting bios to factory defaults, or reflashing the Dell XPS 15 1.1.15 bios. The latter procedure helped me out a while ago when the wifi on my XPS 15  stopped functioning correctly (at the time I reflashed 1.0.7 over existing 1.0.7).

---

### Post by Calin Balaurul on 2016-01-11
Hi all,

Update to kernel 4.4

Using 15.10, kernel 4.4, xorg-edgers for intel and nvidia-358 from graphics-drivers, 

- black screen issues is fixed so now I don't have to suspend/resume as a work around, 
- usb-c still does not work, or at least the adapter I have does not, sometimes if I restart with the usb-c plugde it will recognize my device
- build in mic works
- hdmi plug in and out works
- headphones did not work, but using [http://askubuntu.com/a/237710/101363](http://askubuntu.com/a/237710/101363) got it fixed.

Update to nvidia 361 and graphics broke, unity was freezing on nvidia it was not starting on intel.

Intel graphics performance is really poor, I get 1200 points in glmark, compared to ~1900 with my previous build in intel HD 5500 (previous generation intel chip). On top of that I vlc video playback does not work with acceleration enabled.

What is your experience so far with the intel and the new kernel?

---

### Post by mflores3 on 2016-01-11
[FONT=arial]Hey @oolong2,  

I also had bluetooth/wifi issues.  Is [COLOR=#333333] `[FONT=courier new]dmesg | grep error[/FONT]` showing you any firmware files that failed to load?

[/COLOR][COLOR=#333333]To get both wifi and bluetooth working, I did the following. (*UPDATE:* adding some things I did, but forgot to mention[/COLOR][/FONT].
[LIST=1]
[*][FONT=arial][COLOR=#333333][/COLOR][/FONT]purge old drivers `[FONT=courier new]apt-get purge bcmwl-kernel-source broadcom-sta-common broadcom-sta-source b43-fwcutter firmware-b43legacy-installer`[/FONT]
[*]Copy [FONT=courier new]brcmfmac43602-pcie.bin[/FONT] and [FONT=courier new]brcmfmac43602-pcie.ap.bin[/FONT] from [https://git.kernel.org/cgit/linux/kernel/git/firmware/linux-firmware.git/tree/brcm](https://git.kernel.org/cgit/linux/kernel/git/firmware/linux-firmware.git/tree/brcm) and place into [FONT=courier new]/lib/firmware/brcm[/FONT]
[*][FONT=arial][COLOR=#333333]Pull latest bluetooth driver from my windows 10 partition: [FONT=courier new]c:\Windows\System32\Drivers\BCM20703A1_001.001.005.0214.0403.hex[/FONT]
[/COLOR][/FONT]
[*][FONT=arial][COLOR=#333333]converted to hcd format w/ [FONT=courier new]hex2hcd[/FONT] (found it on github [here]("https://github.com/jessesung/hex2hcd")) - output of this process is [/COLOR][here on google drive]("https://drive.google.com/uc?export=download&id=0B81TkJhZh39rMTJuXzlBbUZsUEE")[COLOR=#333333].
[/COLOR][/FONT]
[*][FONT=arial][COLOR=#333333]saw where firmware was failing to load in `dmesg | grep error` and copied the new hcd file to the file name where my linux distro was looking for the right driver in dmesg.
[/COLOR][/FONT]
[*][FONT=arial][COLOR=#333333]Bluetooth worked! On reboot wifi failed (only on kernel 3.17)
[/COLOR][/FONT]
[*][FONT=arial][COLOR=#333333]I looked at dmesg again, saw another failed firmware load. Copied the same hex file to that new location dmesg was failing (I saw this on my linux mint on kernel 3.17, on 4.4 I did not need to do this step).
[/COLOR][/FONT]
[*][FONT=arial][COLOR=#333333]Both Wifi and Bluetooth worked. (On reboot wifi failed to load one time, but then came back on subsequent reboots, haven't had another issue since then)[/COLOR][/FONT]
[/LIST]

---

### Post by slize_12 on 2016-01-11
First of all I want to thank everybody who took the time to provide others with some valuable information in order to install DELL XPS 15 2015 (Full HD Display, i5, 512 Samsung M.2, 16GB Ram here). 

As far as I followed the initial howto, I managed to install Xubuntu 15.10. Things making trouble still
* no sound (similar to the cases described earlier, lspci shows the device, but nothing happens when playing audio files), I will pay more attention to this later -->> solved (see bottom)
* HDMI connectivity; in the beginning it did not work at all. So I installed the ppa nvidia drivers (361) and kernel 4.3.3 (see kernel.ubuntu.com).  I was not able to get the 4.4. kernel running. It always lacked the intel i915 driver support as outlined earlier. I will have a look into this later. --> Now I can at least attach external screens. However, the highest resolution I had running as of yet was full HD (got a screen with 2560x1600 standing in front of me). I hope this will be worked on soon. -->> partially solved (see bottom)
* When starting up, the system always seems to take a break when starting lightdm, everytime I restarted it (because of, for instance, HDMI problems or so, the systems takes like 10 seconds or so, changes some graphics modes, and then the login appears)
* Touchpad working smoothly but not perfect, some gestures are still missing.
* dmesg says that the bluetooth firmware could not be loaded, however, the tray icon says bluetooth is working, on the other hand I did not test bluetooth properly.
```
[    9.852095] brcmfmac 0000:02:00.0: Direct firmware load for brcm/brcmfmac43602-pcie.txt failed with error -2
[    9.942311] ifquery[413]: segfault at 1 ip 0000000000403187 sp 00007ffe33c25fd0 error 4 in ifup[400000+d000]
[    9.976311] bluetooth hci0: Direct firmware load for brcm/BCM-0a5c-6410.hcd failed with error -2
```

* Wifi currently working out of the box
* No flickering and freezes

To sum up my current config:
* Xubuntu 15.10 - initial installation kernel 4.2.0.16 
* Kernel: 4.4.0-994-generic (drm-intel-nightly) from mainline PPA (see below)
* Sound works
* Nvidia: 361 from PPA
* Latest Intel driver installed via intel-linux-graphics-installer

The thing that bugs me most is that I currently am not able to use my external screen properly. Was anyone able to get more than full HD out of the HDMI port or out of the USB-C port (may be using an USB-C to DisplayPort adapter)?

[EDIT]
I managed to install the intel-drm-nightly kernel. During installation of the kernel the following warning came up:
```
[COLOR=#111111][FONT=Consolas]Possible missing firmware [/FONT][/COLOR][COLOR=#111111][FONT=Consolas]/lib/firmware/i915/skl_guc_ver4.bin for module i915[/FONT][/COLOR]
```

I stated that the initramfs did not contain the module for loading the intel graphics driver. The solution is to manually list the module to be included in the initramfs as follows:
```

sudo bash -c "echo 'i915 nvme' >> /etc/initramfs-tools/modules"
sudo update-initramfs -u -k all
```
[/EDIT]

[EDIT2]
Sound works ->> For whatever reason the speakers were disabled in the BIOS ->> Enabling them solved the problem.
[/EDIT2]


[EDIT3]
External Display on HDMI port with 4K is working. I tested it with a 4K television and it worked right away. I did not need to change resolution or something different, I just plugged in the cable, logged in, and set, display to external screen (via Windows/Super + P menu). The only thing which still confuses me is the fact, that my colleague with his MacBook is able to supply my external screen with 2560x1600 via HDMI and I am not !? ... It will only register as Full HD screen!? 
[/EDIT3]

---

### Post by quickdry21 on 2016-01-11
> **slize_12 said:**
> 
[EDIT]
I managed to install the intel-drm-nightly kernel. During installation of the kernel the following warning came up:
```
[COLOR=#111111][FONT=Consolas]Possible missing firmware [/FONT][/COLOR][COLOR=#111111][FONT=Consolas]/lib/firmware/i915/skl_guc_ver4.bin for module i915[/FONT][/COLOR]
```

I stated that the initramfs did not contain the module for loading the intel graphics driver. The solution is to manually list the module to be included in the initramfs as follows:
```

sudo bash -c "echo 'i915 nvme' >> /etc/initramfs-tools/modules"
sudo update-initramfs -u -k all
```
[/EDIT]


Install GUC from 01.org: [https://01.org/linuxgraphics/downloads/sklgucver43](https://01.org/linuxgraphics/downloads/sklgucver43) - it puts the 4.3 GUC firmware blobs in /lib/firmware/i915/

> **slize_12 said:**
> 
[COLOR=#000000][EDIT3][/COLOR]
[COLOR=#000000]External Display on HDMI port with 4K is working. I tested it with a 4K television and it worked right away. I did not need to change resolution or something different, I just plugged in the cable, logged in, and set, display to external screen (via Windows/Super + P menu). The only thing which still confuses me is the fact, that my colleague with his MacBook is able to supply my external screen with 2560x1600 via HDMI and I am not !? ... It will only register as Full HD screen!? [/COLOR]
[COLOR=#000000][/EDIT3]
[/COLOR][COLOR=#000000]

IIRC the new XPS series uses HDMI 1.4 - you can run FHD at a refresh rate of 60hz, anything greater you will have to run at 30hz. This could be the issue.[/COLOR]

---

### Post by bertusrex on 2016-01-12
I installed nvidia driver 361.16 (beta) from ubuntu graphics ppa, and the nvidia part works ok. However if I switch to Intel, (using prime-indicator) I cannot log in (get kicked back to the login screen ofter logging in). Switching to nvidia again (from vt: "prime-select nvidia") allowed me to log back in with nvidia enabled, however without a window manager or dash. For others who have this: correct the situation by: right-click on desktop to start a terminal, then type: "
dconf reset -f /org/compiz/ && setsid unity". (To be clear: this will reset unity so that it's usable with nvidia again, but will not correct the problem with switching to Intel)

---

### Post by kjano on 2016-01-12
> **slize_12 said:**
> 
* Kernel: 4.4.0-994-generic (drm-intel-nightly) from mainline PPA (see below)



Interestingly I cannot get kernel 4.4 to work. It just results in some errors during the boot process and that is it. I was able to get my hdmi issues fixed using a CableCreation USB-C to HDMI cable (and a converter to VGA on top of that for some other cases). Everything else works fine.

BIOS: Unfortunately, the laptop is significantly more noisy since installing the new bios version. The fans are running most of the time :-(.

---

### Post by slize_12 on 2016-01-12
> **kjano said:**
> Interestingly I cannot get kernel 4.4 to work. It just results in some errors during the boot process and that is it. I was able to get my hdmi issues fixed using a CableCreation USB-C to HDMI cable (and a converter to VGA on top of that for some other cases). Everything else works fine.

BIOS: Unfortunately, the laptop is significantly more noisy since installing the new bios version. The fans are running most of the time :-(.

Did you try one of the proposed solutions to solve this:
[LIST]
[*]```
[COLOR=#000000][FONT=Ubuntu Mono]sudo bash -c "echo 'i915 nvme' >> /etc/initramfs-tools/modules"
[/FONT][/COLOR][COLOR=#000000][FONT=Ubuntu Mono]sudo update-initramfs -u -k all[/FONT][/COLOR]
```
[*]> [COLOR=#000000]Install GUC from 01.org: [/COLOR][https://01.org/linuxgraphics/downloads/sklgucver43](https://01.org/linuxgraphics/downloads/sklgucver43)[COLOR=#000000] - it puts the 4.3 GUC firmware blobs in /lib/firmware/i915/[/COLOR]

[/LIST]

I also solved my HDMI issues. Actually I set the refresh rate for my HDMI connected screen (2560x1600 / 2560x1440) to 30 hertz and everything works wine. Thanks for pointing out quickdry, this made my search much more precise and probably saved me a lot of time. As alternative I found an USB C -> DisplayPort adapter on amazon which actually has all but one positive evaluations. All of those (only 5) evaluations are written by Dell XPS owners. So I guess, if anybody is going for high resolutions with more then 30 hertz this will be an appropriate option. One of the guys even used the very nice feature of DP 1.2 by forwarding the displayport signal. She/he connected two screens via one usb-c displayport adapter. Another friend of mine already uses this with his dual screen setup. So this is also support by the XPS.

Below is the xrandr commands once you dont want to go for new hardware and want to stick to standard HDMI with 30 hertz.

```
xrandr --newmode "2560x1600_30.00"  164.25  2560 2696 2960 3360  1600 1603 1609 1630 -hsync +vsyncxrandr --addmode HDMI-1-0 "2560x1600_30.00" 
xrandr --output HDMI-1-0 --mode "2560x1600_30.00" 
xrandr --output eDP-1-0 --off
```

Respectively

```
xrandr --newmode "2560x1440_30.00"  146.25  2560 2680 2944 3328  1440 1443 1448 1468 -hsync +vsync
xrandr --addmode HDMI-1-0 "2560x1440_30.00" 
xrandr --output HDMI-1-0 --mode "2560x1440_30.00"
xrandr --output eDP-1-0 --off
```

---

### Post by kjano on 2016-01-13
> **slize_12 said:**
> Did you try one of the proposed solutions to solve this:
[LIST]
[*]```
[COLOR=#000000][FONT=Ubuntu Mono]sudo bash -c "echo 'i915 nvme' >> /etc/initramfs-tools/modules"
[/FONT][/COLOR][COLOR=#000000][FONT=Ubuntu Mono]sudo update-initramfs -u -k all[/FONT][/COLOR]
```
[*]
[/LIST]


Thanks. Unfortunately this totally broke my system :-(.

[LIST=1]
[*]If I use the intel card and connect to an external monitor, my laptop screen will turn off whenever the mouse cursor moves into it and the screen will turn on again if the mouse cursor is on the external screen. 
[*]Suspend stopped working
[*]I also tried using the nvidia card again but something got broken and the system is freezing randomly and unity has all sorts of issues that make me type unity --replace every few minutes. I am sure this will be an easy fix. [EDIT: partially fixed]
[/LIST]

:popcorn:

Maybe the problem is that I am still using kernel 4.3 994. The other kernels just result in a black screen while booting. Any idea?

---

### Post by jhouse2 on 2016-01-15
thanks @mflores3  -- your good instructions and pre-made hcd file for fixing bluetooth was very handy!

---

### Post by slize_12 on 2016-01-15
> [COLOR=#000000]Thanks. Unfortunately this totally broke my system [/COLOR]:sad:[COLOR=#000000].[/COLOR]


[LIST=1]
[*]If I use the intel card and connect to an external monitor, my laptop screen will turn off whenever the mouse cursor moves into it and the screen will turn on again if the mouse cursor is on the external screen.
[*]Suspend stopped working
[*]I also tried using the nvidia card again but something got broken and the system is freezing randomly and unity has all sorts of issues that make me type unity --replace every few minutes. I am sure this will be an easy fix. [EDIT: partially fixed]
[/LIST]


:popcorn:

[COLOR=#000000]Maybe the problem is that I am still using kernel 4.3 994. The other kernels just result in a black screen while booting. Any idea?[/COLOR]

Actually, I don't. I tried updating the 4.4.0 kernel which was a bad idea. I had the one from 11th of Jan installed and tried to update it to the one from the 15th of Jan. It completely broke my system. So last night I was busy reinstalling my system. On the other hand, as I went through the advises here before and had my home partition separate it only took about 1.5 hours to an operational state to support daily business again. I can't tell you actually how it worked for the first time. Once I reinstalled my XPS I tried to install the working version of 4.4.0 again and I didn't manage to do. So currently, I sticked to the 4.3.3 Version. It's not working as good as the 4.4.0 version (second screens and resolution change + running dhclient trying to connect to a network tend to freeze lightdm), but it will do for the next weeks. By then I hope for official 4.4 support ;). 

About your system, I'm really sorry. I didn't intend to guide somebody into bugs with my notes. Somewhat I must have been lucky when I was playing around with the kernels. Normally, I use Gentoo and there compiling and changing kernels isn't such a problem (once you know what you do ofc :D). However, under Gentoo I didn't get the Nvidia-Card to work. I'll try again in a few weeks. ;)

---

### Post by maxweld on 2016-01-16
Hi - Great Thread - Thanks. I am on the verge of ordering one of these great machines and will install Ubuntu/Windows dual boot at first, but would like eventually to run Windows in a VM under Ubuntu. 

At the same time, I want to purchase a means of connecting the laptop to my network, dual Dell 23" monitors and several USB devices whilst at home.

Clearly the Thunderbolt Dock TB13 would be preferable, if it works, but as it is not yet available which is a pity.

The[ USB 3.0 Ultra HD Triple Video Docking Station D3100]("http://accessories.euro.dell.com/sna/productdetail.aspx?c=ie&l=en&s=dhs&cs=iedhs1&sku=452-bboo") looks next best and is available. Does anybody have experience of this device in conjunction with Linux on the XPS 15 9550. 

I will also want a more portable adaptor when away from home and needing to connect to networks and displays/projectors. Does anybody have any experience with the [DA100]("http://accessories.euro.dell.com/sna/productdetail.aspx?c=uk&l=en&s=bsd&cs=ukbsdt1&sku=492-bbnu") or [DA200]("http://accessories.euro.dell.com/sna/productdetail.aspx?c=uk&l=en&s=dhs&cs=ukdhs1&sku=470-ABRY") adaptors?

I am keen to get this ordered ASAP, so any views that might permit me to avoid hassles with the wrong adaptors would be a big help. Thanks

---

### Post by dgriver on 2016-01-17
Anyone else having issues with very slow wifi?
I'm getting 1.5 Megabit download speed, if I tether to my phone that’s connected to the same network I get 20.
Kernel: 4.4.0-040400-generic
Steps:
Wiped windows
installed ubuntu 15.10
dist-upgrade, upgrade
updated to bios 1.0.5
installed kernel 4.4 from [http://kernel.ubuntu.com/~kernel-ppa/mainline/](http://kernel.ubuntu.com/~kernel-ppa/mainline/)
installed GUC from [URL="https://01.org/linuxgraphics/downloads/sklgucver43"]https://01.org/linuxgraphics/downloads/sklgucver43

[/URL]```
[COLOR=#000000][FONT=Ubuntu Mono]sudo bash -c "echo 'i915 nvme' >> /etc/initramfs-tools/modules"
[/FONT][/COLOR][COLOR=#000000][FONT=Ubuntu Mono]sudo update-initramfs -u -k all[/FONT][/COLOR]
```[URL="https://01.org/linuxgraphics/downloads/sklgucver43"]
[/URL]Rebooted
WiFi didn't work
Downloaded [http://en.community.dell.com/cfs-file/__key/telligent-evolution-components-attachments/00-4613-01-00-20-84-05-08/brcmfmac4350_2D00_pcie.zip](http://en.community.dell.com/cfs-file/__key/telligent-evolution-components-attachments/00-4613-01-00-20-84-05-08/brcmfmac4350_2D00_pcie.zip)
unzipped
ran sudo mv brcmfmac4350-pcie.bin /lib/firmware/brcm
sudo chmod 600 /lib/firmware/brcm/brcmfmac4350-pcie.bin
rebooted
WiFi works but very very slow and often drops, any ideas?

---

### Post by eagledrc2 on 2016-01-17
mflores - I followed these instructions (I skipped #3-5 because I don't care about Bluetooth right now) and I can now see all of the WiFi networks but I can't connect to mine. It keeps asking for the password and never connects. Here is the output of dmesg | grep error:

[   11.501041] usb 1-1: device descriptor read/all, error -110
[   12.831608] bluetooth hci0: Direct firmware load for brcm/BCM-0a5c-6410.hcd failed with error -2
[   12.927896] brcmfmac 0000:02:00.0: Direct firmware load for brcm/brcmfmac43602-pcie.txt failed with error -2
[   13.028445] i2c_hid i2c-DLL06E4:01: error in i2c_hid_init_report size:6 / ret_size:4
[   21.105317] EXT4-fs (sda2): re-mounted. Opts: errors=remount-ro
[  120.611544] brcmf_cfg80211_scan: scan error (-11)

Any ideas? Thanks for your help.

---

### Post by bertusrex on 2016-01-18
> **eagledrc2 said:**
> mflores - I followed these instructions (I skipped #3-5 because I don't care about Bluetooth right now) and I can now see all of the WiFi networks but I can't connect to mine. It keeps asking for the password and never connects. Here is the output of dmesg | grep error:

[   11.501041] usb 1-1: device descriptor read/all, error -110
[   12.831608] bluetooth hci0: Direct firmware load for brcm/BCM-0a5c-6410.hcd failed with error -2
[   12.927896] brcmfmac 0000:02:00.0: Direct firmware load for brcm/brcmfmac43602-pcie.txt failed with error -2
[   13.028445] i2c_hid i2c-DLL06E4:01: error in i2c_hid_init_report size:6 / ret_size:4
[   21.105317] EXT4-fs (sda2): re-mounted. Opts: errors=remount-ro
[  120.611544] brcmf_cfg80211_scan: scan error (-11)

Any ideas? Thanks for your help.

I've reccommended it here before: try a bios factory reset or reflash your current bios. Then put back your bios settings, especially important settings like correct AHCI/RAID setting. 

My BT mouse stopped working this morning, reboots didn't make a difference but a bios factory reset fixed it. Bios reflash has worked for me once before when I had wifi connecting issues (similar to yours), maybe a factory reset would have been enough in that case too. For some reason every now and then a BT or wifi issue seems to remain persistent across boots, and a factory reset fixes that.

It only takes a few minutes to try.

PS If the 2 files with the -2 errors above DO exist on the filesystem (not likely as you skipped some steps), then you can do a chmod 644 on those files, I think firmware files with too broad permissions are refused to load.

---

### Post by jhouse2 on 2016-01-18
WebCam in Virtualbox (5.0) guest?

WebCam is working fine in ubuntu 15.10.   However when running a windows guest in Virtualbox I can't even get the camera to show up as a device.

Has anyone yet had luck with this?

lshw gives me these details:

              *-usb:2
                   description: Video
                   product: Integrated_Webcam_HD
                   vendor: CN045G28724875B2B4XDA01
                   physical id: c
                   bus info: usb@1:c
                   version: 56.05
                   capabilities: usb-2.00
                   configuration: driver=uvcvideo maxpower=500mA speed=480Mbit/s

I have gotten VirtualBox to enable sharing the USB device "CN045G28724875B2B4XDA01" , but Windows 7 doesn't seem to acknowledge it at all -  doesn't detect a webcam, doesn't detect any new device and ask for drivers, or etc..

---

### Post by kjano on 2016-01-18
> **slize_12 said:**
> Actually, I don't. I tried updating the 4.4.0 kernel which was a bad idea. I had the one from 11th of Jan installed and tried to update it to the one from the 15th of Jan. It completely broke my system. So last night I was busy reinstalling my system. On the other hand, as I went through the advises here before and had my home partition separate it only took about 1.5 hours to an operational state to support daily business again. I can't tell you actually how it worked for the first time. Once I reinstalled my XPS I tried to install the working version of 4.4.0 again and I didn't manage to do. So currently, I sticked to the 4.3.3 Version. It's not working as good as the 4.4.0 version (second screens and resolution change + running dhclient trying to connect to a network tend to freeze lightdm), but it will do for the next weeks. By then I hope for official 4.4 support ;). 

About your system, I'm really sorry. I didn't intend to guide somebody into bugs with my notes. Somewhat I must have been lucky when I was playing around with the kernels. Normally, I use Gentoo and there compiling and changing kernels isn't such a problem (once you know what you do ofc :D). However, under Gentoo I didn't get the Nvidia-Card to work. I'll try again in a few weeks. ;)

Don't worry. I got my system fixed and working again for the most parts. After all, breaking your OS is one of the great joys of running Linux. Anyway, good to know that I am not the only person that cannot get kernel 4.4 working.

---

### Post by eXorus on 2016-01-19
[B]:popcorn:Finally Ubuntu 15.10 working fine with my new Dell XPS 9550 (wifi, hdmi with external monitor)

[/B]
For that I'm using the Kernel 4.4 (4.3 is working better than 4.2 but less than 4.4)
[http://kernel.ubuntu.com/~kernel-ppa/mainline/v4.4-wily/](http://kernel.ubuntu.com/~kernel-ppa/mainline/v4.4-wily/)

```

cd /tmp
wget http://kernel.ubuntu.com/~kernel-ppa/mainline/v4.4-wily/linux-headers-4.4.0-040400-generic_4.4.0-040400.201601101930_amd64.deb
wget http://kernel.ubuntu.com/~kernel-ppa/mainline/v4.4-wily/linux-headers-4.4.0-040400_4.4.0-040400.201601101930_all.deb
wget http://kernel.ubuntu.com/~kernel-ppa/mainline/v4.4-wily/linux-image-4.4.0-040400-generic_4.4.0-040400.201601101930_amd64.deb
sudo dpkg -i linux-headers-4.4.0*.deb linux-image-4.4.0*.deb

```

If you have an Warning about sklguc you need to fix it and relaunch sudo dpkg ... To fix it download the bin from Intel Open Source
```

cd /tmp
wget https://01.org/sites/default/files/downloads/intelr-graphics-linux/sklgucver43.tar.bz2
tar -zxvf sklgucver43.tar.bz2
sudo sh install

```

After we need to add more module to boot at the begin of the kernel (solve all my issue about boot with Kernel 4.4)
```

echo nvme | sudo tee -a /etc/initramfs-tools/modules
echo i915 | sudo tee -a /etc/initramfs-tools/modules
echo dm-crypt,aes,xts,sha512 | sudo tee -a /etc/initramfs-tools/modules

```
nvme it's for the detection of SSD
i915 it's about the intel chipset
dm-crypt it's about the encrypted disk (If you have one if you don't it's not necessary to use this command line)

Finally we need to reconfigure the Kernel with this 3 lines or 2 depends of your configuration
```

sudo update-initramfs -k 4.4.0-040400-generic -u

```
It's very important to do -k instead -all I saw early in this post. -k will edit only the kernel 4.4 and don't touch to the kernel 4.2 that is working at the moment in your laptop. So if something wrong with 4.4 you will be happy to come back to 4.2.

That's all reboot and go to 4.4. Enjoy

More command to manage kernel is like me you try a lot :
"dpkg -l | grep linux-image" to see all kernel installed or removed in the laptop (rc=deleted, ii= installed you can delete it)
always keep the last kernel that working (4.2) and try to install 4.4.
"sudo dpkg --remove linux-imagexxxxxxx" pour supprimer un kernel installé (le passer de ii à rc)
"uname -r" to know the kernel that working now and don't delete this one.

Last thing I bought the Mouse Dell WM615 but I can't install it (it's a blueetooh mouse) if you have an idea.
And I can't keep my full resolution (UHD) on my laptop because Ubuntu can't manage two monitor with different resolution. It's working but it's so big for external monitor(1920*1080) and so small in the internal monitor. So I put both the same resolution (1920*1080). Is it possible to do something in Ubuntu for that ?

For information my firmware for video card is : xserver-xorg-video-nouveau

---

### Post by svea2 on 2016-01-19
There's a couple of typos in the last command, if anybody like me is lazy and do copy and paste ;)

```
sudo update-initramfs -k 4.4.0-040400-generic -u
```

---

### Post by eXorus on 2016-01-20
Thanks, fixed in my post also

---

### Post by bertusrex on 2016-01-20
> **eXorus said:**
> [B]:popcorn:Finally Ubuntu 15.10 working fine with my new Dell XPS 9550 (wifi, hdmi with external monitor)
...
[/B]Last thing I bought the Mouse Dell WM615 but I can't install it (it's a blueetooh mouse) if you have an idea.
...

I've struggled with a Logitech MX Anywhere 2 Bluetooth mouse before, and got it to work eventually. Maybe it will work for your mouse as well, see [here]("http://ubuntuforums.org/showthread.php?t=2301071&p=13403372#post13403372").

---

### Post by Imran_Ashraf on 2016-01-20
Thanks for the help. I can finally use 4.4 kernel peacefully. :p
A small comment,  you still did not fix the typos as mentioned by svea2. It should be **4.4.0-040400-generic** and not **4.4.0.040400-generic** in the **update-initramfs** command.

---

### Post by raufjawaid on 2016-01-20
what nvidia version you using?

Thanks for the info

---

### Post by eXorus on 2016-01-21
> **bertusrex said:**
> I've struggled with a Logitech MX Anywhere 2  Bluetooth mouse before, and got it to work eventually. Maybe it will  work for your mouse as well, see [here]("http://ubuntuforums.org/showthread.php?t=2301071&p=13403372#post13403372").

It's not working :
```
[bluetooth]# pair F7:49:CB:58:48:E1
Attempting to pair with F7:49:CB:58:48:E1
[CHG] Device F7:49:CB:58:48:E1 Connected: yes
Failed to pair: org.bluez.Error.AuthenticationFailed
[CHG] Device F7:49:CB:58:48:E1 Connected: no
[CHG] Device F7:49:CB:58:48:E1 RSSI: -87
```


> **Imran_Ashraf said:**
> Thanks for the help. I can finally use 4.4 kernel peacefully. :razz:
A small comment,  you still did not fix the typos as mentioned by svea2. It should be **4.4.0-040400-generic** and not **4.4.0.040400-generic** in the **update-initramfs** command.
Thanks again my post is updated



> **raufjawaid said:**
> what nvidia version you using?

Thanks for the info
Like I said I'm on "xserver-xorg-video-nouveau"

---

### Post by juancarlos2 on 2016-01-21
Many thanks eXorus, I got it working with your config!!!

---

### Post by quickdry21 on 2016-01-21
> **eXorus said:**
> And I can't keep my full resolution (UHD) on my laptop because Ubuntu can't manage two monitor with different resolution. It's working but it's so big for external monitor(1920*1080) and so small in the internal monitor. So I put both the same resolution (1920*1080). Is it possible to do something in Ubuntu for that ?

For information my firmware for video card is : xserver-xorg-video-nouveau

I'm using xrandr to scale my two 1920x1080 external monitors:

| eDP1 (3840x2160) | DP2 (1920x1080) | HDMI1 (1920x1080 |


The idea is to scale the lower resolution displays.

```

xrandr --query # get the name of your displays, for me it is eDP1 (internal display), DP2 (USBC -> DisplayPort) and HDMI1 (HDMI -> HDMI)


eDP1_WIDTH=3840
eDP1_HEIGHT=2160
DP2_WIDTH=1920
HDMI_WIDTH=1920

xrandr --fb $((eDP1_WIDTH + (DP2_WIDTH * 2) + (HDMI_WIDTH * 2)))x${eDP1_HEIGHT}
xrandr --output eDP1 --auto --pos 0x0 --primary --output DP2 --auto --scale 2x2 --pos ${eDP1_WIDTH}x0 --output HDMI1 --auto --scale 2x2 --pos $((eDP1_WIDTH + (DP2_WIDTH * 2)))x0

```

Note: I am on Ubuntu Gnome, not sure how well Unity would cooperate with this.

---

### Post by eXorus on 2016-01-22
The issue is about the scale for menu and title bars.
If I put 1920x1080 on my external monitor and 3840x2160 on my laptop, it's good I can do it on Unity.
But If I open Firefox on the both, the font will be good for external and too small to my laptop.
For that when I have only one monitor I'm using the scale for menu and title bars to x2 and it's good.
But with two monitor if I do that the scale is shared between the two monitor so the laptop will be good in firefox and too big for the external monitor.
It will be nice to have different value for the scale, one for each monitor.

---

### Post by betterwithchemistr on 2016-01-26
@[**[COLOR=#000000]jchedstrom[/COLOR]**]("http://ubuntuforums.org/member.php?u=865321") Thank you very much! Your guide has been extremely helpful!

---

### Post by mflores3 on 2016-01-26
> **eagledrc2 said:**
> 
[   12.831608] bluetooth hci0: Direct firmware load for brcm/BCM-0a5c-6410.hcd failed with error -2


@eagledrc2 That is your error. You need the firmware hcd to live in that location.  Copy it to there with that filename.  It is missing.

---

### Post by Ji_Balcar on 2016-01-27
Hello all,
I want to thank you for your helpful posts.
I succesfully installed Ubuntu on my XPS - i7, 16GB RAM, 512SSD, UHD touch display.

I installed it by @jchedstrom[COLOR=#000000] post with couple of differences:
- Secure boot ON
- Touchpad worked out of the box without blacklisting
- Installed nvidia-352 instead of 355
- Installed kernel 4.4.0

The system working fine except couple of issues:
- after resuming from suspend, the WiFi indicator shows that is disconnected and does not show any WiFi networks (does not shot the WiFi networks block at all) [/COLOR][COLOR=#000000]but in fact is connected and working[/COLOR][COLOR=#000000]
- when using nvidia, sometimes graphic glitches occures (For example opening some chrome extension does not show any content) - with intel it works.
- changing touchpad speed does not have any effect, thumb detection not working

Does anyone have any tips about the WiFi indicator issues?

Battery lasts about 5hrs with medium usage (Sublime Text, Pycharm, couple terminal windows, node+gulp, chrome with couple tabs open).
[/COLOR]

---

### Post by bertusrex on 2016-01-28
> **Ji_Balcar said:**
> [COLOR=#000000]
...
Battery lasts about 5hrs with medium usage (Sublime Text, Pycharm, couple terminal windows, node+gulp, chrome with couple tabs open).
[/COLOR]

Did you try powertop yet? It may help to squeeze some extra time from the battery.

To test if it makes a difference, start your session with e.g.:
 ```
$ sudo powertop --auto-tune
``` 
If you want to make powertop settings permanent, [see here]("http://askubuntu.com/questions/112705/how-do-i-make-powertop-changes-permanent") for hints.

---

### Post by raufjawaid on 2016-01-28
Hello guys, any updates which nvidia driver is working on kernel 4.4. I'm using "xserver-xorg-video-nouveau" but animation are not smooth.  For example in firefox scrolling is laggy.  Windows animation were laggy too but I managed to fix them by changing setting is composite to opengl.  By the way I'm using kubuntu plasma and new to linux/kubuntu.

---

### Post by Decorum_Velox on 2016-01-30
Following these directions has worked well here:

Steps 0 to 7 from [http://ubuntuforums.org/showthread.php?t=2301071&p=13382949#post13382949](http://ubuntuforums.org/showthread.php?t=2301071&p=13382949#post13382949)

Installing Kernel 4.4 from [http://ubuntuforums.org/showthread.php?t=2301071&page=21&p=13425368#post13425368](http://ubuntuforums.org/showthread.php?t=2301071&page=21&p=13425368#post13425368)

External 4k monitor with HDMI is working and haven't noticed any tearing issues.

---

### Post by Mobman02 on 2016-01-31
> **raufjawaid said:**
> Hello guys, any updates which nvidia driver is working on kernel 4.4. I'm using "xserver-xorg-video-nouveau" but animation are not smooth.  For example in firefox scrolling is laggy.  Windows animation were laggy too but I managed to fix them by changing setting is composite to opengl.  By the way I'm using kubuntu plasma and new to linux/kubuntu.

I'm running Nvidia 355.11 full time, as battery is not an issue for me,
with kernel 4.4.0-040400-generic, and so far it works great. Go for it :KS

[HR][/HR]
I switched to Kernel 4.4 in the hope of being able to use the USB-C / Thunderbolt port, but still no luck. I bought this [USB-C to Ethernet + USB]("http://www.amazon.fr/adaptateur-Ethernet-Chromebook-ordinateur-portable/dp/B00ZV9P8O8/ref=cm_cr_pr_product_top?ie=UTF8") adapter,
when I plug it in, nothing appears in lsusb, dmesg or journal...

It doesn't act like a real USB so maybe I'm not using the right tools... Any idea or feedback about the USB-C port?

EDIT: If I boot with the device pluged-in, it works and I see it in the lsusb response.

---

### Post by markdueck-bz on 2016-01-31
Hi everyone.  Thanks to all the help in this forum, I have Ubuntu running fairly smoothly using kernel 4.4.0 using the NVidia 361.18 driver (it just updated to that).   I would like to now force it to use the intel graphics only as I care more for battery than graphics.  I have tried this previously with nvidia-prime, but that made my system so I could not log in.    Any pointers?  

I do have the system running with btrfs, so I can easily revert with snapshots.

---

### Post by Chad.S on 2016-01-31
The best luck I've had so far is installing the drm-intel-nightly 4.5 kernel ([http://kernel.ubuntu.com/~kernel-ppa/mainline/drm-intel-nightly/](http://kernel.ubuntu.com/~kernel-ppa/mainline/drm-intel-nightly/)) and the nvidia-361 driver. I have been unable to reproduce the annoying random black screens during the boot process. Nvidia Prime seems to work fine too. The only strange part is that when using the intel graphics it seems to take a bit for the screen resolution to adjust properly after it boots. Though I'm sure there is probably an easy way to fix that.

---

### Post by bertusrex on 2016-02-01
I'm having similar trouble switching to intel (mainline kernel 4.4rc8, nvidia 361.18) I found no solution yet. 

Apart from that, with an earlier install when switching graphics still worked, I noticed that with intel graphics active, the laptop actually consumed MORE energy than with nvidia active.

---

### Post by everc on 2016-02-01
Hello everyone, I hope you can offer me some guidance because I'm about to lose it!

After following this thread for the past months and seeing that things started to work fine I decided to get this machine for work, where I will mainly use Linux. The main specs:
[FONT=Museo For Dell Regular]
6th Generation Intel(R) Core (TM) i7-6700HQ Quad Core (6M Cache, up to 3.5 GHz) 
15.6" 4K Ultra HD (3840 x 2160) InfinityEdge touch
16GB (2x8GB) 2133MHz DDR4 Memory
Module,DD,1T,S3,5.4,7MM,SEAHAWK
NVIDIA GTX960M 2Go DDR5
[/FONT]
So, first day, I arrived to the office and found this beautiful thing on my desk. I boot it up, enter the Windows 10 configuration, select English language, click next aaaand... Blue Screen Of Death!! (I kid you not) The machine restarts, and never goes beyond the Dell logo. Either freezes there (when some balls are going in circles), or simply enters a restart infinite loop.

I've got no desire to deal with Dell's technical support and, since I plan to exclusively use Linux, I want to completely delete Windows and install Ubuntu.

So, USB stick with Ubuntu 15.10. I configure the BIOS with: disabled Secure Boot, AHCI, and boot the live version with nomodeset (without it often freezes, as reported by others). [B]When I enter the installation no device is found. With gparted I see:
[/B]

[LIST]
[*]/dev/sda: unallocated 29.82GB
[*]/dev/sdb1: fat32 - ESP - 500MB
[*]/dev/sdb2: unknown - MS reserved partition - 128MB
[*]/dev/sdb3: ntfs - OS - 918.39 GB
[*]/dev/sdb4: ntfs - WINRETOOLS - 893MB
[*]/dev/sdb5: ntfs - image - 11.64GB
[*]/dev/sdc1: usb stick
[/LIST]

My questions are:
[LIST]
[*]Can I delete all the sdb* partitions safely? Should I keep the Dell recovery partition? Which one is it btw?
[*]How can I get to see the partitions from the installer?
[/LIST]

---

### Post by bertusrex on 2016-02-01
> **everc said:**
> Hello everyone, I hope you can offer me some guidance because I'm about to lose it!

After following this thread for the past months and seeing that things started to work fine I decided to get this machine for work, where I will mainly use Linux. The main specs:
[FONT=Museo For Dell Regular]
6th Generation Intel(R) Core (TM) i7-6700HQ Quad Core (6M Cache, up to 3.5 GHz) 
15.6" 4K Ultra HD (3840 x 2160) InfinityEdge touch
16GB (2x8GB) 2133MHz DDR4 Memory
Module,DD,1T,S3,5.4,7MM,SEAHAWK
NVIDIA GTX960M 2Go DDR5
[/FONT]
So, first day, I arrived to the office and found this beautiful thing on my desk. I boot it up, enter the Windows 10 configuration, select English language, click next aaaand... Blue Screen Of Death!! (I kid you not) The machine restarts, and never goes beyond the Dell logo. Either freezes there (when some balls are going in circles), or simply enters a restart infinite loop.

I've got no desire to deal with Dell's technical support and, since I plan to exclusively use Linux, I want to completely delete Windows and install Ubuntu.

So, USB stick with Ubuntu 15.10. I configure the BIOS with: disabled Secure Boot, AHCI, and boot the live version with nomodeset (without it often freezes, as reported by others). [B]When I enter the installation no device is found. With gparted I see:
[/B]

[LIST]
[*]/dev/sda: unallocated 29.82GB 
[*]/dev/sdb1: fat32 - ESP - 500MB 
[*]/dev/sdb2: unknown - MS reserved partition - 128MB 
[*]/dev/sdb3: ntfs - OS - 918.39 GB 
[*]/dev/sdb4: ntfs - WINRETOOLS - 893MB 
[*]/dev/sdb5: ntfs - image - 11.64GB 
[*]/dev/sdc1: usb stick 
[/LIST]

My questions are:
[LIST]
[*]Can I delete all the sdb* partitions safely? Should I keep the Dell recovery partition? Which one is it btw? 
[*]How can I get to see the partitions from the installer? 
[/LIST]


If it's BSOD-ing right out of the box before Windows is even configured, I'd run diagnostics first (press F12 at Dell boot logo, then choose diagnostics from boot menu). If you've got a faulty laptop, running Ubuntu is not going to fix that.

---

### Post by everc on 2016-02-02
> **bertusrex said:**
> If it's BSOD-ing right out of the box before Windows is even configured, I'd run diagnostics first (press F12 at Dell boot logo, then choose diagnostics from boot menu). If you've got a faulty laptop, running Ubuntu is not going to fix that.

That's true. I did the test, everything seems to be ok

> **allanr said:**
> Did you disable the fast boot? [http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html](http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html)
When fast boot is turned on, it does not even allow me to mount the windows partition from my ubuntu. Make sure it is turned off.

I wonder if this has something to do with it, but I cannot boot into windows.

> **linxaddict2 said:**
> I boot off usb stick using the UEFI option. After the ubuntu live launches, I can see my disks in gparted (/dev/sda /dev/sdb), partitions are correctly detected (/dev/sdb1, /dev/sdb2 and so on) and I can mount them, but the Ubuntu installer doesn't see them.

Did you manage to solve that?

---

### Post by alberink-stampfini on 2016-02-02
Did anyone get the Logitech MX Anywhere2 mouse to run on kernel 4.4? I'm trying to do this, but the guides posted before do not work for me. Which is sad, as I'm now blocking a precious USB port with a Unified Receiver dongle...

---

### Post by bertusrex on 2016-02-02
> **alberink-stampfini said:**
> Did anyone get the Logitech MX Anywhere2 mouse to run on kernel 4.4? I'm trying to do this, but the guides posted before do not work for me. Which is sad, as I'm now blocking a precious USB port with a Unified Receiver dongle...

I'm using this mouse with kernel 4.4 (4.4 rc8, but also 4.2, 4.3, other 4.4 rc's). I suppose you already found [this post]("http://ubuntuforums.org/showthread.php?t=2301071&p=13403372#post13403372")? If you describe how far you got and have some logs I might be able to compare it to my setup.

---

### Post by alberink-stampfini on 2016-02-02
> **bertusrex said:**
> I'm using this mouse with kernel 4.4 (4.4 rc8, but also 4.2, 4.3, other 4.4 rc's). I suppose you already found [this post]("http://ubuntuforums.org/showthread.php?t=2301071&p=13403372#post13403372")? If you describe how far you got and have some logs I might be able to compare it to my setup.
Yeah, found that post as well... But this is what I see:
```
[bluetooth]# power on[CHG] Controller 18:4F:32:F7:FF:EE Class: 0x4c010c
Changing power on succeeded
[CHG] Controller 18:4F:32:F7:FF:EE Powered: yes
[bluetooth]# scan on
Discovery started
[CHG] Controller 18:4F:32:F7:FF:EE Discovering: yes
[CHG] Device E0:33:3B:74:61:00 RSSI: -96
[CHG] Device E0:33:3B:74:61:00 TxPower: 4
[CHG] Device E0:33:3B:74:61:00 UUIDs: 00001812-0000-1000-8000-00805f9b34fb
[NEW] Device FB:C3:2A:4E:8D:FD One
[CHG] Device E0:33:3B:74:61:00 RSSI: -83
[CHG] Device FB:C3:2A:4E:8D:FD TxPower: -6
[bluetooth]# trust E0:33:3B:74:61:00 
Changing E0:33:3B:74:61:00 trust succeeded
[bluetooth]# pair E0:33:3B:74:61:00 
Attempting to pair with E0:33:3B:74:61:00
[CHG] Device E0:33:3B:74:61:00 Connected: yes
Failed to pair: org.bluez.Error.AuthenticationTimeout
[CHG] Device E0:33:3B:74:61:00 Connected: no
[bluetooth]# pair E0:33:3B:74:61:00 
Attempting to pair with E0:33:3B:74:61:00
[CHG] Device E0:33:3B:74:61:00 Connected: yes
Failed to pair: org.bluez.Error.AuthenticationFailed
[CHG] Device E0:33:3B:74:61:00 Connected: no
[CHG] Device E0:33:3B:74:61:00 RSSI: -73
[bluetooth]# pair E0:33:3B:74:61:00 
Attempting to pair with E0:33:3B:74:61:00
[CHG] Device E0:33:3B:74:61:00 Connected: yes
Failed to pair: org.bluez.Error.AuthenticationFailed
[CHG] Device E0:33:3B:74:61:00 Connected: no



```
AS you can see, authentication fails... Bluetoothd is started with the -E parameter, but not via a hack in the init file. That won't work if you use systemd.

---

### Post by bertusrex on 2016-02-02
> **alberink-stampfini said:**
> Yeah, found that post as well... But this is what I see:
```
[bluetooth]# power on[CHG] Controller 18:4F:32:F7:FF:EE Class: 0x4c010c
Changing power on succeeded
[CHG] Controller 18:4F:32:F7:FF:EE Powered: yes
[bluetooth]# scan on
Discovery started
[CHG] Controller 18:4F:32:F7:FF:EE Discovering: yes
[CHG] Device E0:33:3B:74:61:00 RSSI: -96
[CHG] Device E0:33:3B:74:61:00 TxPower: 4
[CHG] Device E0:33:3B:74:61:00 UUIDs: 00001812-0000-1000-8000-00805f9b34fb
[NEW] Device FB:C3:2A:4E:8D:FD One
[CHG] Device E0:33:3B:74:61:00 RSSI: -83
[CHG] Device FB:C3:2A:4E:8D:FD TxPower: -6
[bluetooth]# trust E0:33:3B:74:61:00 
Changing E0:33:3B:74:61:00 trust succeeded
[bluetooth]# pair E0:33:3B:74:61:00 
Attempting to pair with E0:33:3B:74:61:00
[CHG] Device E0:33:3B:74:61:00 Connected: yes
Failed to pair: org.bluez.Error.AuthenticationTimeout
[CHG] Device E0:33:3B:74:61:00 Connected: no
[bluetooth]# pair E0:33:3B:74:61:00 
Attempting to pair with E0:33:3B:74:61:00
[CHG] Device E0:33:3B:74:61:00 Connected: yes
Failed to pair: org.bluez.Error.AuthenticationFailed
[CHG] Device E0:33:3B:74:61:00 Connected: no
[CHG] Device E0:33:3B:74:61:00 RSSI: -73
[bluetooth]# pair E0:33:3B:74:61:00 
Attempting to pair with E0:33:3B:74:61:00
[CHG] Device E0:33:3B:74:61:00 Connected: yes
Failed to pair: org.bluez.Error.AuthenticationFailed
[CHG] Device E0:33:3B:74:61:00 Connected: no



```
AS you can see, authentication fails... Bluetoothd is started with the -E parameter, but not via a hack in the init file. That won't work if you use systemd.

Some quick suggestions: 
- Did you put your mouse in pairing mode when trying to pair? (connect button at the bottom). 
- I've had pairing problems under windows when wifi is enabled. Maybe try pairing with wifi disabled?

other options worth trying:
- update /lib/firmware from [http://git.kernel.org/cgit/linux/kernel/git/firmware/linux-firmware.git](http://git.kernel.org/cgit/linux/kernel/git/firmware/linux-firmware.git)
- reset bios to factory defaults

---

### Post by ghostcode on 2016-02-04
Any of you are having problem when press the space bar on the corner of the key? In my case it does not work (print the space) only when I press in the middle. I am not sure if it is a keyboard design problem or my key that is not working.

---

### Post by bertusrex on 2016-02-04
> **ghostcode said:**
> Any of you are having problem when press the space bar on the corner of the key? In my case it does not work (print the space) only when I press in the middle. I am not sure if it is a keyboard design problem or my key that is not working.

All 4 corners work on mine (although not all have the same 'feeling'). A 'sticky' spacebar is a common problem with XPS 15's, that might be related to yours. To see if anything is wrong underneath your spacebar you can remove it and put it back quite easily, see e.g. [here]("https://www.youtube.com/watch?v=R333HXzT7Ws") for a video.

---

### Post by maxweld on 2016-02-04
Sorry - removed to correct part of this Topic

---

### Post by Bowei_Zhao on 2016-02-04
Thanks!

But I'm also have issues. After installing Ubuntu, I switched back from UEFI mode to RAID because Windows will fail to boot if Dell XPS is set to UEFI.

I pretty much can only use Windows when I set it to RAID and  Ubuntu that I installed using 'Install Ubuntu Alongside Windows Bootloader' on UEFI.

---

### Post by ghostcode on 2016-02-05
> **bertusrex said:**
> All 4 corners work on mine (although not all have the same 'feeling'). A 'sticky' spacebar is a common problem with XPS 15's, that might be related to yours. To see if anything is wrong underneath your spacebar you can remove it and put it back quite easily, see e.g. [here]("https://www.youtube.com/watch?v=R333HXzT7Ws") for a video.

I will check it out, thank you and sorry for the off topic here.

> **Bowei_Zhao said:**
> Thanks!

But I'm also have issues. After installing Ubuntu, I switched back from UEFI mode to RAID because Windows will fail to boot if Dell XPS is set to UEFI.

I pretty much can only use Windows when I set it to RAID and  Ubuntu that I installed using 'Install Ubuntu Alongside Windows Bootloader' on UEFI.

I do not know if it is possible to use Ubuntu having the RAID activated, at least I did not manage to get it working. What you have to do is what was mentioned previously in this topic (if you go through the first 5 pages), activate the AHCI mode and change your windows from RAID to AHCI.

---

### Post by BeeOnRope on 2016-02-05
> **ghostcode said:**
> I do not know if it is possible to use Ubuntu having the RAID activated, at least I did not manage to get it working. What you have to do is what was mentioned previously in this topic (if you go through the first 5 pages), activate the AHCI mode and change your windows from RAID to AHCI.

The basic idea mentioned earlier is that if you start Windows once in safe mode after changing to AHCI, it will change something and you'll be able to boot after that. However, in AHCI mode, you'll get random BSODs in Windows (CRITICAL PROCESS DIED). The only solution to that seems to be to install some Samsung NVMe drivers for another drive (e.g., the 850) as no official drivers are available for the PM951 that comes in the XPS 15. The downside of that is that reboot may not work from windows, but I gather you can shut down and restart instead.

That's what I've gathered so far (I'm still waiting for my XPS 15 to arrive and plan on dual booting).

---

### Post by zafu on 2016-02-06
Hi,

Is it OK to remove both recovery partitions (one is 2G and the other 16G?)? Will windows still boot without those?

Also what is the minimal partition size needed by W10?

EDIT: OK, I figured those: both recoveries can go, as one can reinstall W10 easily without them, no activation key is needed, and the minimum disk for W10 seems to be around 50G (leaves 10G free on my default install).

Now a real ubuntu question :) When booting from usb  the QHD+ screen's native resolution makes text much too small, how can I scale things up at the boot stage (grub argument?) to make xterm's usable?

---

### Post by lelinolino on 2016-02-07
> **BeeOnRope said:**
> The basic idea mentioned earlier is that if you start Windows once in safe mode after changing to AHCI, it will change something and you'll be able to boot after that. However, in AHCI mode, you'll get random BSODs in Windows (CRITICAL PROCESS DIED).

This is exactly what I am experiencing.
I have a new dell precision 5510 (intel xeon, 16GB ram ddr4, 512GB pm951 samsung, quadro m1000m, FHD screen) and after updating windows 7 partition to windows 10, I installed ubuntu in dual boot (I have activated AHCI mode, therefore I rebooted windows in safe mode in order to install ahci drivers).
The environment seems to work well, but sometimes I have random BSODs screen on windows (one of them is 'KERNEL_DATA_IN_PAGE_ERROR' or 'CRITICAL_PROCESS_DIED'). Additionally, when I reboot the machine from windows, if I'll choose windows from the grub menu it will not reboot and I will need to shutdown and reboot manually in order to access.


Do you have ideas to solve the problem? (I would avoid to reinstall windows from the scratch :(


p.s. However this is a very beatiful and powerfull machine! :)

---

### Post by kjano on 2016-02-07
Can somebody give me a hand with the kernel? Whenever I try to install kernel 4.4 the system will only boot to busybox and alert me that /dev/disk/by-uuid/...../ does not exist. 

The UUID corresponds to my root partition, not boot or home. Kernel 4.2 works without any issues so does 4.3.0.994 nightly. I also checked boot-repair.

I am not sure whether this is related but running sudo update-initramfs -u returns.

update-initramfs: Generating /boot/initrd.img-4.4.1-040401-generic
W: Possible missing firmware /lib/firmware/i915/skl_guc_ver4.bin for module i915

---

### Post by lelinolino on 2016-02-07
Look at this post:

> **eXorus said:**
> [B]:popcorn:Finally Ubuntu 15.10 working fine with my new Dell XPS 9550 (wifi, hdmi with external monitor)

[/B]
For that I'm using the Kernel 4.4 (4.3 is working better than 4.2 but less than 4.4)
[http://kernel.ubuntu.com/~kernel-ppa/mainline/v4.4-wily/](http://kernel.ubuntu.com/~kernel-ppa/mainline/v4.4-wily/)

```

cd /tmp
wget http://kernel.ubuntu.com/~kernel-ppa/mainline/v4.4-wily/linux-headers-4.4.0-040400-generic_4.4.0-040400.201601101930_amd64.deb
wget http://kernel.ubuntu.com/~kernel-ppa/mainline/v4.4-wily/linux-headers-4.4.0-040400_4.4.0-040400.201601101930_all.deb
wget http://kernel.ubuntu.com/~kernel-ppa/mainline/v4.4-wily/linux-image-4.4.0-040400-generic_4.4.0-040400.201601101930_amd64.deb
sudo dpkg -i linux-headers-4.4.0*.deb linux-image-4.4.0*.deb

```

If you have an Warning about sklguc you need to fix it and relaunch sudo dpkg ... To fix it download the bin from Intel Open Source
```

cd /tmp
wget https://01.org/sites/default/files/downloads/intelr-graphics-linux/sklgucver43.tar.bz2
tar -zxvf sklgucver43.tar.bz2
sudo sh install

```

After we need to add more module to boot at the begin of the kernel (solve all my issue about boot with Kernel 4.4)
```

echo nvme | sudo tee -a /etc/initramfs-tools/modules
echo i915 | sudo tee -a /etc/initramfs-tools/modules
echo dm-crypt,aes,xts,sha512 | sudo tee -a /etc/initramfs-tools/modules

```
nvme it's for the detection of SSD
i915 it's about the intel chipset
dm-crypt it's about the encrypted disk (If you have one if you don't it's not necessary to use this command line)

Finally we need to reconfigure the Kernel with this 3 lines or 2 depends of your configuration
```

sudo update-initramfs -k 4.4.0-040400-generic -u

```
It's very important to do -k instead -all I saw early in this post. -k will edit only the kernel 4.4 and don't touch to the kernel 4.2 that is working at the moment in your laptop. So if something wrong with 4.4 you will be happy to come back to 4.2.

That's all reboot and go to 4.4. Enjoy

More command to manage kernel is like me you try a lot :
"dpkg -l | grep linux-image" to see all kernel installed or removed in the laptop (rc=deleted, ii= installed you can delete it)
always keep the last kernel that working (4.2) and try to install 4.4.
"sudo dpkg --remove linux-imagexxxxxxx" pour supprimer un kernel installé (le passer de ii à rc)
"uname -r" to know the kernel that working now and don't delete this one.

Last thing I bought the Mouse Dell WM615 but I can't install it (it's a blueetooh mouse) if you have an idea.
And I can't keep my full resolution (UHD) on my laptop because Ubuntu can't manage two monitor with different resolution. It's working but it's so big for external monitor(1920*1080) and so small in the internal monitor. So I put both the same resolution (1920*1080). Is it possible to do something in Ubuntu for that ?

For information my firmware for video card is : xserver-xorg-video-nouveau

;)

---

### Post by kjano on 2016-02-07
@lelinolino: **Yes**, yes, yes! Thank you very much for saving my weekend in just 5 min!

---

### Post by Chad.S on 2016-02-07
The last remaining thing I can't seem to fix is the jumpy cursor with the touchpad. When navigating with the touchpad it will often jump to the far bottom left of the screen. I don't think it's due to palm detection or anything like that. I found a thread regarding a kernel patch that supposedly solves the problem, but apparently never got merged :/ I can't seem to find the thread anymore though. It referenced a different version of the XPS.

---

### Post by astroman3001gt on 2016-02-08
Hi,

I finally got my machine. It took a while, since DELL shipped the wrong machine (different HD and battery). So the one that I know have is the Dell Xps 15 9550 (i7 6gen 16gbr UHD 4k touch) 512 SSD.

I followed the steps 1-8 from jchedstrom : [http://ubuntuforums.org/showthread.php?t=2301071&p=13382949#post13382949](http://ubuntuforums.org/showthread.php?t=2301071&p=13382949#post13382949)

Then I have installed kernel 4.4 from eXorus : [http://ubuntuforums.org/showthread.php?t=2301071&page=21&p=13425368#post13425368](http://ubuntuforums.org/showthread.php?t=2301071&page=21&p=13425368#post13425368)

Pretty much as reported by Decorum_Velox: [http://ubuntuforums.org/showthread.php?t=2301071&page=22&p=13431658#post13431658](http://ubuntuforums.org/showthread.php?t=2301071&page=22&p=13431658#post13431658)

So far almost everything is working fine. I did not try to fix Bluetooth since I don't really need it, and I don't want to risk messing with the wifi. Just a note I have updated the bios to:  Version 01.01.19.
I also did not risk to install any nvidea drivers yet. The xorg driver should be enough for now. I also have the issue with the tracking pad, however is no show stopper for me.

Together with the computer I also ordered the dell display lin DA100 (should be the DA200 but I guess they were wrong again with the shipping). Anyway, to make it work was quite simple. I got and installed the linux drivers from [http://www.displaylink.com/downloads/ubuntu](http://www.displaylink.com/downloads/ubuntu) and everything is working. Without the drivers the VGA port was not functional. (the HDMI I did not test it). Both usb and ethernet port worked even without the drivers.

Just as an extra note, before Ubuntu 15.10 I did tried Linux mint 17.3 (Rosa). It seemed to work everything fine from the very beginning, but when I updated the bios I lost wifi, and installed ubuntu from scratch following these instructions.

Thanks for everyone that continues to give feedback.

And now, to give a reply to zafu: You can change the resolution of grub in the same file where you add the extra option for the boot. look for the line: 
 #GRUB_GFXMODE=640x480 and you can change it for (example):GRUB_GFXMODE=1024x768

---

### Post by lelinolino on 2016-02-08
Ok, it seems that I have solved a lot of my windows problems, but one still remain and I don't know what to do in order to solve it.

In windows:
- if I shutdown the system the next time that I will access the windows partition I will log in without any problem.
- if I reboot the system the next time that I will access the windows partition I will have a black screen. The only method to exit is to manually shutdown the machine (hold down power button). Fortunally, after I will be able to log in into windows.

It is not a critical issue, but I would solve it.

Do you have any solution for this?

Thanks in advance

---

### Post by bertusrex on 2016-02-09
> **lelinolino said:**
> Ok, it seems that I have solved a lot of my **windows** problems, but one still remain and I don't know what to do in order to solve it.
In **windows**:
- if I shutdown the system the next time that I will access the **windows** partition I will log in without any problem.
- if I reboot the system the next time that I will access the **windows** partition I will have a black screen. The only method to exit is to manually shutdown the machine (hold down power button). Fortunally, after I will be able to log in into **windows**.
It is not a critical issue, but I would solve it.
Do you have any solution for this?
Thanks in advance

Can't help you, maybe you should try a less linux/Ubuntu oriented thread/forum than this one. (e.g. [here]("http://forum.notebookreview.com/threads/dell-xps-15-skylake-9550-owners-lounge.783377/")).

---

### Post by lelinolino on 2016-02-09
> **bertusrex said:**
> Can't help you, maybe you should try a less linux/Ubuntu oriented thread/forum than this one. (e.g. [here]("http://forum.notebookreview.com/threads/dell-xps-15-skylake-9550-owners-lounge.783377/")).

Thank you for the suggestion. ;)

---

### Post by maxweld on 2016-02-10
My XPS 15 9550 arrived last week, and frustratingly I have not managed to get Ubuntu to boot on it yet. Maybe someone has some ideas.

I am trying to set up a dual boot, Windows 10 and Ubuntu 15.10 machine. The spec is as per this thread with a 1TB SSD. I have upgraded the BIOS to 01.01.19, and shrunk the windows partition to make room for Ubuntu. I have followed @jchedstrom instructions except I jumped the first as he indicates it may not be necessary, and there are dire warnings given if you try to remove secure boot, so I thought I would try leaving it enabled. I manage to install Ubuntu but cannot seem to then boot it.

When I try, firstly I cannot avoid Windows screaming and wanting to use RAID mode.
I need to set Ubuntu as a boot option in the BIOS Setup, it boots into GRUB where is set the modeset, and then nothing.

1. I have not disabled secure boot, but Ubuntu should work with secure boot. Has anybody got this working?

2. I have selected the Windows Boot Partition for the bootloader during install, but then have to configure it to point at the correct file, as per Instruction 5 in @jchedstrom instructions. I get the Grub menu up and then edit the Ubuntu entry to add the nouveau.modeset=0 and Press f10. I just get a blank screen after that as though it does not find the next boot files?

Any thoughts or comments would be gratefully appreciated.

---

### Post by bertusrex on 2016-02-10
> **maxweld said:**
> My XPS 15 9550 arrived last week, and frustratingly I have not managed to get Ubuntu to boot on it yet. Maybe someone has some ideas.

I am trying to set up a dual boot, Windows 10 and Ubuntu 15.10 machine. The spec is as per this thread with a 1TB SSD. I have upgraded the BIOS to 01.01.19, and shrunk the windows partition to make room for Ubuntu. I have followed @jchedstrom instructions except I jumped the first as he indicates it may not be necessary, and there are dire warnings given if you try to remove secure boot, so I thought I would try leaving it enabled. I manage to install Ubuntu but cannot seem to then boot it.

When I try, firstly I cannot avoid Windows screaming and wanting to use RAID mode.
I need to set Ubuntu as a boot option in the BIOS Setup, it boots into GRUB where is set the modeset, and then nothing.

1. I have not disabled secure boot, but Ubuntu should work with secure boot. Has anybody got this working?

2. I have selected the Windows Boot Partition for the bootloader during install, but then have to configure it to point at the correct file, as per Instruction 5 in @jchedstrom instructions. I get the Grub menu up and then edit the Ubuntu entry to add the nouveau.modeset=0 and Press f10. I just get a blank screen after that as though it does not find the next boot files?

Any thoughts or comments would be gratefully appreciated.

Disabling secure boot is not necessary to install or run Ubuntu. I've also got a dual boot setup, installed and run with secure boot enabled. 

I should mention that I'm booting from an SSD that I've connected to the sata port (it replaced the original hdd), not the PCIe slot.

I did reinstall Windows though, and used a gpt partition layout instead of mbr to partition the disk. With secure boot enabled I think you can't use a Windows restore USB stick (created from an existing installation), but you can use a fresh windows ISO on a USB stick.

The system now boots to grub, installed on the efi partition (that partition was probably created by windows during install). It's quite clean, everything related to booting both OS-es is on the same efi partition this way, if I understand it correctly. Grub can find the windows bootloader and Ubuntu loader from there, also after OS updates everything remains intact. I did not have to manually configure boot options in bios.

Can't help with the Ubuntu black screen, did you try to boot into Ubuntu recovery mode? (Grub->advanced->recovery mode).

---

### Post by maxweld on 2016-02-10
Thanks @bertusrex

> **bertusrex said:**
> 

Can't help with the Ubuntu black screen, did you try to boot into Ubuntu recovery mode? (Grub->advanced->recovery mode).

I think my problems are to do with being unable to locate a file or partition. In recovery mode I get a lot of messages, but it then drops into a shell after the following messages

```
Give up waiting for boot device: Common problems
-Boot args (cat /proc/cmdline)
  - Check rootdelay= (did the system wait long enough?)
  - Check root= (did the system wait for the right device?)
- Missing modules (cat /proc/modules: ls /dev)
Alert /dev/disk/by-uuid/301a8194-08cc-4fa0-8152-f62659169923 does not exist. Dropping to a shell
```

and then it drops into BusyBox

Any ideas?

---

### Post by jsla7527 on 2016-02-11
> **maxweld said:**
> 

2. I have selected the Windows Boot Partition for the bootloader during install, but then have to configure it to point at the correct file, as per Instruction 5 in @jchedstrom instructions. I get the Grub menu up and then edit the Ubuntu entry to add the nouveau.modeset=0 and Press f10. I just get a blank screen after that as though it does not find the next boot files?
 

You should install grub into EFI (UEFI) partition. Then you can go to BIOS and actually browse for the correct file (\EFI\ubuntu\shimx64.efi). I am not completely sure if that's what you did.

For me, the boot is flaky - sometimes it ends up with black screen or grub itself crashes (when using external monitor). But more often then not it works. And yes, I have secure boot enabled though I turned if off for install.

---

### Post by jsla7527 on 2016-02-11
Thanks to this thread, I have nicely running Ubuntu on XPS 15. What I did to get there is similar to what Decorum_Velox did: [http://ubuntuforums.org/showthread.php?t=2301071&p=13431658#post13431658:](http://ubuntuforums.org/showthread.php?t=2301071&p=13431658#post13431658:)

Steps 0 to 7 from [http://ubuntuforums.org/showthread.php?t=2301071&p=13382949#post13382949](http://ubuntuforums.org/showthread.php?t=2301071&p=13382949#post13382949)

Installing Kernel 4.4 from [http://ubuntuforums.org/showthread.php?t=2301071&page=21&p=13425368#post13425368](http://ubuntuforums.org/showthread.php?t=2301071&page=21&p=13425368#post13425368)

This works for most part, but probably just uses ATI graphiscs (judging by speed of glxgears), so:

I also installed nvidia-352 and nvidia-prime from standard repositories:

sudo apt-get install nvidia-352 nvidia-prime
sudo service lightdm restart

And prime-indicator as per initial post:


sudo add-apt-repository ppa:nilarimogard/webupd8
sudo apt-get update
sudo apt-get install prime-indicator
prime-indicator

To get bluetooth working (it wouldn't pair otherwise), I copied firmware as per step 2 here: [http://ubuntuforums.org/showthread.php?t=2301071&p=13403372#post13403372](http://ubuntuforums.org/showthread.php?t=2301071&p=13403372#post13403372). Now it works both with mouse and headphones.

Few things to note:
- ubuntu won't detect windows during install unless you disable fast boot. I didn't know that and wanted to do manual install anyway, but it's probably good idea to have it disabled anyway. You can reenable it later after install.
- grub can be flaky with external hdmi monitor. It would just crash on me quite often. Best thing is probably to turn the monitor off during boot.
- chrome disables HW accleration but in my experience seems to work better with it enabled, so I just launch it with --ignore-gpu-blacklist parameter (then go to chrome://gpu to check it is working) . I actually feel some of the tearing issues can be attributed to HW acceleration being disabled, since I've seen those before I forced it on.

Problems that I noticed:
- nvidia with external monitor is still pretty moody. I cannot use ubuntu display tool to change monitor order for example (it would just crash every time) so I am forced to use laptop display on the left and monitor on the right. nvidia-settings app does not even see both monitors, it just sees the whole desktop as one screen, so it can't be used either. This is currently most annoying issue - I tried different nvidia drivers, I tried playing with xconfig, but could not get anywhere. I will explore it further, although it's not super pressing, but any help would be appreciated. If switch to intel GPU, everything works smoothly. As a side, rm ~/.config/monitors.xml saved me more then once after getting to configuration that would not even launch. I
- boot can sometimes result in black screen. No idea what causes this. So can restart. Suspend on the other hand is extremely reliable.

Overall, I am quite pleased with this laptop on ubuntu, it's completely usable, and I am hoping it will only get better. 

Most importantly, I'd like to thank everybody in this tread for making this relatively painless.:p

---

### Post by jsla7527 on 2016-02-12
For those who need displayport, I also can confirm that following USB-C Display port cable works under linux: [http://www.amazon.com/gp/product/B019MCD5SU](http://www.amazon.com/gp/product/B019MCD5SU). I would assume others will work too.

It works in exactly the same way as HDMI output - I am not able to change monitor order currently.

---

### Post by astroman3001gt on 2016-02-12
Just to report some problems that I have when using an extra monitor/projector with the [COLOR=#000000]dell display link DA100[/COLOR] with VGA.

Sometimes (many time lately) when I boot with the extra monitor connected I experience a login loop, and I am not able to log in easily. I have tried to mv/remove the .Xauthority file but it does not fix the problem. Workaround: I login as guest, and then once logged in guest I change the user to my account.

Also, when plugin and unpluging the extra monitor, the resolution always go to 4K in the monitor. Everytime I have to adjust it to the resolution that I want, in this case 1080h.

Edit: Another problem and fix:
I have experience problems with the video in skype. After a quick search I found a fix here: [https://github.com/linuxenko/ubuntu-skylake-i915-video-fix](https://github.com/linuxenko/ubuntu-skylake-i915-video-fix)

---

### Post by maxweld on 2016-02-12
> **jsla7527 said:**
> You should install grub into EFI (UEFI) partition. Then you can go to BIOS and actually browse for the correct file (\EFI\ubuntu\shimx64.efi). I am not completely sure if that's what you did.

Thanks @jsla7527 and also @bertusrex. I seem to have overcome my problems, as I am now booting into Ubuntu happily. I thought I was installing into the EFI Partition, as I seemed to be able to select the shimx64.efi file.

I had set the Sata Operation from Raid to AHCI, but had not bothered to use Safe Mode in Windows 10 to ensure Windows was going to use it. Thus Windows was trying to force a return to factory settings, and this may have been confusing the boot setup. Not really sure.

I therefore reset the Sata Operation to AHCI, and then used Windows in Safe Mode to confirm this setting and to force Windows to load AHCI drivers in future. With this done, I reinstalled Ubuntu, manually added Ubuntu to the top of the UEFI Boot sequence and all worked. So, I am not exactly sure what changed, but this resolved the problem. It now happily loads Grub, from where I can choose either Windows 10 or the default Ubuntu 15.10. UEFI 

Incidentally, not only did it now boot into Ubuntu, and uploaded the latest updates, I found more working than I expected after reading the early posts in this topic.:
Touchpad and touch screen work, USB ports work, camera works with Cheese, speakers work, wifi works (even during the install), suspend works so far, I even managed to get a Dell Bluetooth mouse working with nothing but the latest Ubuntu updates. (Mouse was a bit flaky and after a reboot did not reconnect.) I have a Dell DA200 dongle which connects to the USB-C port, and the USB and Ethernet ports are both working, but I have not yet tried the VGA or HDMI ports on the dongle or HDMI on the notebook, nor the SD card reader. I have not specifically installed any nVIDIA drivers, and the prime-indicator seems to suggest that the Intel graphics are being used. I need to work out how to test graphics properly, but for now the Graphics are fine, no issues whatsoever. I also need to check the audio port properly.

Issues detected:
The inbuilt microphone does not work, and the Liliputian Log-on prompt when you boot from scratch is amusing. Bluetooth, although initially promising, needs more work.

Now I can spend the weekend testing the other aspects, installing printers and software, setting up VMs and migrating files :-)))

Further issues detected after some additional testing:
Suspend seems not to be working as I thought earlier, and on later reboots the touchpad has proved not to work. I may have been over confident earlier.

---

### Post by jsla7527 on 2016-02-12
> **astroman3001gt said:**
> I have tried to mv/remove the .Xauthority file but it does not fix the problem.



Try removing ~/.config/monitors.xml for the user. It's where ubuntu stores monitor configuration for different monitors and sometimes it gets in a weird state. Of course it will go to default on all the monitors you might have setup...

---

### Post by ginlemon on 2016-02-15
Is anyone experiencing problems with USB type-c? my Nexus 5x is detected only if connected to the notebook during the boot. If I disconnect than connect it again, it doesn't appear is lsusb anymore. The same happens if I try to connect it in any moment after the boot. This happens with both kernel 4.2 and 4.4. Any idea?

---

### Post by bertusrex on 2016-02-15
> **ginlemon said:**
> Is anyone experiencing problems with USB type-c? my Nexus 5x is detected only if connected to the notebook during the boot. If I disconnect than connect it again, it doesn't appear is lsusb anymore. The same happens if I try to connect it in any moment after the boot. This happens with both kernel 4.2 and 4.4. Any idea?

I have the same issue (kernel 4.5rc4). when connected at boot (USB-C to USB type A cable with android device attached), this section is present in lshw, after dis- and reconnecting, it does not return.

```
          *-pci
                description: PCI bridge
                product: Intel Corporation
                vendor: Intel Corporation
                physical id: 0
                bus info: pci@0000:06:00.0
                version: 00
                width: 32 bits
                clock: 33MHz
                capabilities: pci pm msi pciexpress normal_decode bus_master cap_list
                configuration: driver=pcieport
                resources: irq:127 ioport:2000(size=4096) memory:c4000000-da0fffff ioport:80000000(size=570425344)
              *-pci:0
                   description: PCI bridge
                   product: Intel Corporation
                   vendor: Intel Corporation
                   physical id: 0
                   bus info: pci@0000:07:00.0
                   version: 00
                   width: 32 bits
                   clock: 33MHz
                   capabilities: pci pm msi pciexpress normal_decode bus_master cap_list
                   configuration: driver=pcieport
                   resources: irq:128 memory:da000000-da0fffff
              *-pci:1
                   description: PCI bridge
                   product: Intel Corporation
                   vendor: Intel Corporation
                   physical id: 1
                   bus info: pci@0000:07:01.0
                   version: 00
                   width: 32 bits
                   clock: 33MHz
                   capabilities: pci pm msi pciexpress normal_decode bus_master cap_list
                   configuration: driver=pcieport
                   resources: irq:129 ioport:2000(size=4096) memory:c4000000-d9efffff ioport:80000000(size=570425344)
              *-pci:2
                   description: PCI bridge
                   product: Intel Corporation
                   vendor: Intel Corporation
                   physical id: 2
                   bus info: pci@0000:07:02.0
                   version: 00
                   width: 32 bits
                   clock: 33MHz
                   capabilities: pci pm msi pciexpress normal_decode bus_master cap_list
                   configuration: driver=pcieport
                   resources: irq:130 memory:d9f00000-d9ffffff
                 *-usb
                      description: USB controller
                      product: Intel Corporation
                      vendor: Intel Corporation
                      physical id: 0
                      bus info: pci@0000:3e:00.0
                      version: 00
                      width: 32 bits
                      clock: 33MHz
                      capabilities: pm msi pciexpress xhci bus_master cap_list
                      configuration: driver=xhci_hcd latency=0
                      resources: irq:131 memory:d9f00000-d9f0ffff
                    *-usbhost:0
                         product: xHCI Host Controller
                         vendor: Linux 4.5.0-040500rc4-generic xhci-hcd
                         physical id: 0
                         bus info: usb@4
                         logical name: usb4
                         version: 4.05
                         capabilities: usb-3.00
                         configuration: driver=hub slots=2 speed=5000Mbit/s
                    *-usbhost:1
                         product: xHCI Host Controller
                         vendor: Linux 4.5.0-040500rc4-generic xhci-hcd
                         physical id: 1
                         bus info: usb@3
                         logical name: usb3
                         version: 4.05
                         capabilities: usb-2.00
                         configuration: driver=hub slots=2 speed=480Mbit/s
                       *-usb
                            description: Generic USB device
                            product: Android
                            vendor: Android
                            physical id: 1
                            bus info: usb@3:1
                            version: 2.32
                            serial: 168de311
                            capabilities: usb-2.10
                            configuration: driver=usbfs maxpower=500mA speed=480Mbit/s
```

---

### Post by ginlemon on 2016-02-15
I experienced the problem for the first time after a bios update (but I'm not sure two things were related). Did you have a similar experience?

---

### Post by bertusrex on 2016-02-15
> **ginlemon said:**
> I experienced the problem for the first time after a bios update (but I'm not sure two things were related). Did you have a similar experience?

Can't confirm, I've never seen it working correctly, since I just recently got a USB-C cable, so I've only tried with latest bios and USB3/thunderbolt firmware updates from Dell. (Windows works ok though with plugging/unplugging/replugging).

---

### Post by jsla7527 on 2016-02-16
> **bertusrex said:**
> I have the same issue (kernel 4.5rc4). when connected at boot (USB-C to USB type A cable with android device attached), this section is present in lshw, after dis- and reconnecting, it does not return.

I have the exact same issue.

In general, USB-C port is flaky at best. Currently it has following issues:
[LIST]
[*]hotplug doesn't work for usb type devices (it would work for displayport adapter, but that's pretty much just pass through). It doesn't work for ethernet cable or Nexus phone. I've tried different kernels, but to no avail. With the device plugged in at boot it works as expected.
[*]plugging anything in often prevents suspend from working (it would hang instead). This applies even to the cases when the device in question was not even detected by OS.
[*]also, there's a weird issue when plugging a device in there, even not connected to anything, increases fan speed. This has been reported on Windows as well: ([http://en.community.dell.com/support-forums/laptop/f/3518/t/19664735](http://en.community.dell.com/support-forums/laptop/f/3518/t/19664735) or [https://www.reddit.com/r/Dell/comments/40ltqo/can_someone_confirm_fan_speedd_with_usbc_on_the/](https://www.reddit.com/r/Dell/comments/40ltqo/can_someone_confirm_fan_speedd_with_usbc_on_the/)).
[/LIST]

I want to test new Dell dock. But this makes me kind of skeptical. At the same time, except for fan issues, I am pretty optimistic these will be eventually solved by newer kernels. It's just too brand new hardware.

---

### Post by bertusrex on 2016-02-16
> **jsla7527 said:**
> I have the exact same issue.

In general, USB-C port is flaky at best. Currently it has following issues:
[LIST]
[*]hotplug doesn't work for usb type devices (it would work for displayport adapter, but that's pretty much just pass through). It doesn't work for ethernet cable or Nexus phone. I've tried different kernels, but to no avail. With the device plugged in at boot it works as expected. 
[*]plugging anything in often prevents suspend from working (it would hang instead). This applies even to the cases when the device in question was not even detected by OS. 
[*]also, there's a weird issue when plugging a device in there, even not connected to anything, increases fan speed. This has been reported on Windows as well: ([http://en.community.dell.com/support-forums/laptop/f/3518/t/19664735](http://en.community.dell.com/support-forums/laptop/f/3518/t/19664735) or [https://www.reddit.com/r/Dell/comments/40ltqo/can_someone_confirm_fan_speedd_with_usbc_on_the/](https://www.reddit.com/r/Dell/comments/40ltqo/can_someone_confirm_fan_speedd_with_usbc_on_the/)). 
[/LIST]

I want to test new Dell dock. But this makes me kind of skeptical. At the same time, except for fan issues, I am pretty optimistic these will be eventually solved by newer kernels. It's just too brand new hardware.

I can't reproduce fan speed, but I do see a slight (3/4W) power consumption increase (powertop) when re-plugging an USB-C-to-type-A cable (without any device connected), that goes away again after unplugging.

---

### Post by kjano on 2016-02-17
Btw, do **not** install the latest intel drivers via intel-linux-graphics-installer. As you can read from the many reports online, this may render your unity desktop unusable as you will no longer be able to log in. Btw, Xfce will still work (and you can use it to fix your unity by switching to the intel card instead of the nivida card).

---

### Post by BeeOnRope on 2016-02-18
> **lelinolino said:**
> Ok, it seems that I have solved a lot of my windows problems, but one still remain and I don't know what to do in order to solve it.

In windows:
- if I shutdown the system the next time that I will access the windows partition I will log in without any problem.
- if I reboot the system the next time that I will access the windows partition I will have a black screen. The only method to exit is to manually shutdown the machine (hold down power button). Fortunally, after I will be able to log in into windows.

It is not a critical issue, but I would solve it.

Do you have any solution for this?

Thanks in advance

Did you install the Samsung 950 Pro drivers to solve the BSOD issue? In that case, a hang at reboot is a known issue and discussed at length on the notebook review forums. Some people don't have it, but most seem to and it's not clear how to fix it. Do you get a pure black screen or does it have a message like "no disk found"?

---

### Post by bertusrex on 2016-02-18
A headsup for people trying out the latest kernels: I've had 2 kernel panics (with flashing capslock led) on [mainline 4.5rc4 ]("http://kernel.ubuntu.com/~kernel-ppa/mainline/v4.5-rc4-wily/"). Once when leaving the laptop just idle, the other while working on it. This is over the course of several days, not a huge problem so far for me.

---

### Post by jsla7527 on 2016-02-18
> **jsla7527 said:**
> I have the exact same issue.

In general, USB-C port is flaky at best. Currently it has following issues:
[LIST]
[*]hotplug doesn't work for usb type devices (it would work for displayport adapter, but that's pretty much just pass through). It doesn't work for ethernet cable or Nexus phone. I've tried different kernels, but to no avail. With the device plugged in at boot it works as expected.
[/LIST]


I finally found solution for hotplugging USB-C devices, although it's not automated. [COLOR=#000000]This works with Plugable ethernet adapter, Nexus phone and Dell Dock (more on that in later post).[/COLOR] You need to run the following command after plugging anything into USB-C port
```

$ sudo sh -c "echo 1 > /sys/bus/pci/rescan"

```

You can then verify with lspci that there's new USB controller: Intel Corporation Device 15b5, which apparently is what Thunderbird controller is called these days.;)

I'd assume this will be fixed in later kernels - I believe usb-c/Thunderbird controller is shut down completely when nothing is plugged in so kernel cannot see it (this would also account for power consumption decrease), but once you plug something in, kernel should rescan PCI bus automatically.

---

### Post by bertusrex on 2016-02-19
> **jsla7527 said:**
> I finally found solution for hotplugging USB-C devices, although it's not automated. [COLOR=#000000]This works with Plugable ethernet adapter, Nexus phone and Dell Dock (more on that in later post).[/COLOR] You need to run the following command after plugging anything into USB-C port
```

$ sudo sh -c "echo 1 > /sys/bus/pci/rescan"

```

You can then verify with lspci that there's new USB controller: Intel Corporation Device 15b5, which apparently is what Thunderbird controller is called these days.;)

I'd assume this will be fixed in later kernels - I believe usb-c/Thunderbird controller is shut down completely when nothing is plugged in so kernel cannot see it (this would also account for power consumption decrease), but once you plug something in, kernel should rescan PCI bus automatically.

Thanks, seems to work.

Some notes though: The lspci output (including the 15b5 device, theUSB controller) remains unchanged even after unplugging on my system: 15b5 is always there. 

Your pci rescan workaround does make the sections in lshw output appear again though, so it seems to work. Quick 'n' dirty check: 
```
# count no of PCI bridge lines in lshw before
$ sudo lshw | grep "PCI bridge" | wc -l
# rescan pci
$ sudo sh -c "echo 1 > /sys/bus/pci/rescan"
# count afterwards
sudo lshw | grep "PCI bridge" | wc -l

```

Should show a difference.

I can't get my USB device to be recognised after rescanning ports though, but maybe that's another issue.

---

### Post by l1fe on 2016-02-22
I'm on kernel 4.4.1 with the latest nvidia-361 and intel linux graphics drivers. Lately, when on the intel graphics, the resolution at the login screen/initial login is very low. After signing in and waiting for ~10 seconds, the resolution goes back to normal. A, maybe unrelated, side-effect is that when I close the lid on my laptop, it sleeps maybe 50% of the time, and the other 50% it boots into grub again.

For what it's worth, this is a dual boot machine (win10, ubuntu 15.10), and my screen is 1080p, not 4k.

---

### Post by jsla7527 on 2016-02-22
> **l1fe said:**
> I'm on kernel 4.4.1 with the latest nvidia-361 and intel linux graphics drivers. Lately, when on the intel graphics, the resolution at the login screen/initial login is very low. After signing in and waiting for ~10 seconds, the resolution goes back to normal.

This happens on my machine too (with 4.5-rc4 kernel). I think it's bug with nvidia-361 drivers only. On the other hand, it doesn't happen when using nvidia card, and since glxgears runs about twice as fast as with 352 drivers and generally performance seem much better, I just tend to stick with nvidia full time (I also don't feel it's that much of a battery drag compared to Intel).

> A, maybe unrelated, side-effect is that when I close the lid on my laptop, it sleeps maybe 50% of the time, and the other 50% it boots into grub again.

I had reboot on resume happen a lot at one point, but then it went away. Not exactly sure why, though as I said, I don't really use intel drivers. One thing that I mentioned though is that after rebooting, it will happen again in 100% of the cases on next suspend unless I shutdown the notebook completely in between. I think it gets into some weird state and complete shutdown repairs it. Otherwise suspend has been pretty stable for me as long as I don't use USB-C port.

---

### Post by l1fe on 2016-02-23
Thanks! I'll give going nvidia a try. Curious to see if battery life is relatively on par...

---

### Post by patrick117 on 2016-02-24
I have a dell XPS 9550 with a 4K screen. GTX 960M. Here is the issue: ONE boot I was able to use "install updates" from ubuntu and it made everything work flawlessly. The function keys adjusted brightness, and the scale feature of unity "Scale for menu and title bars" scaled the resolution perfectly. 
After the crash, it went back to extremely small scaling and scaling no longer works. I press apply and the screen remains unchanged. I cannot figure this out, I am relatively new to Ubuntu. 
Some suggest installing nvidia 352 or 355, when I install them and restart lightdm, ubuntu does not let me log in, it reverts back to login screen like a login loop. I'm at a complete loss here. I've tried downloading the driver from 01.org and run the installation, when I reboot,no change. Either I am installing it wrong or it has no effect. I even change to it from the Ubuntu software additional drivers section, reboot, and it still does not let me log in. 
Currently, the screen brightness cannot be adjusted and the screen cannot be scaled. I'm thinking its the graphics driver but I'm not sure. 

I just want to adjust my brightness and scale ubuntu, everything else is perfect!! I have done 3 clean installs

I am on Ubuntu 15.10 kernel 4.2. I have tried kernel 4.3 to no avail. And once again NVidia drivers never let me log in and I cant quite figure out why.

---

### Post by kjano on 2016-02-25
> **patrick117 said:**
> 
After the crash, it went back to extremely small scaling and scaling no longer works. I press apply and the screen remains unchanged. I cannot figure this out, I am relatively new to Ubuntu. 
Some suggest installing nvidia 352 or 355, when I install them and restart lightdm, ubuntu does not let me log in, it reverts back to login screen like a login loop. 


--> [http://askubuntu.com/questions/736028/login-failure-redirects-to-login-after-enterning-password-in-ubuntu-14-04](http://askubuntu.com/questions/736028/login-failure-redirects-to-login-after-enterning-password-in-ubuntu-14-04)

---

### Post by rvanderwerf on 2016-02-25
> **kjano said:**
> Btw, do **not** install the latest intel drivers via intel-linux-graphics-installer. As you can read from the many reports online, this may render your unity desktop unusable as you will no longer be able to log in. Btw, Xfce will still work (and you can use it to fix your unity by switching to the intel card instead of the nivida card).

I think this bit me today for some reason. I upgraded to 32gb of ram which shouldn't matter at all but I couldn't log in anymore. I removed the intel and all nvidia, went back to nouveau, the re-installed intel and I'm back. I am about to add nvidia back into the mix. Is 361 the driver to run right now?


update I re installed nvidia 352 drivers, and everything is hosed again. It seems latest intel drivers are not playing nice with the nvidia ones. If I just install the intel drivers, everything comes back to life (had to force purge all the nvidia* and reinstall ubuntu-desktop) to get everything back.

Anyone here running 2 4k screens. I recently got a dell 4k 27" I'm using via usb-c-> displayport adapter because the panel can't do 60hz via hdmi. Is there a usb-c to dual DP that works in linux?

I tried my laptop 4k screen + usb-c 4k screen + u2412m at 1920x1200 and intel drivers completely crash. Before latest update nvidia would work, but system would freeze when coming back from a screen timeout.

---

### Post by sze5003 on 2016-02-27
What kind of battery life am I supposed to get on the i7 256gb model? I'm running Ubuntu 15.10 on a 1tb ssd which is in the 2.5 inch hard drive slot. Using latest nvidia 361 driver from the Additional drivers section. I'm on kernel 4.4.0. Brightness is set to very low and I can barely get 3 hours or so. I also notice the laptop is a lot warmer than in windows.

---

### Post by leepe on 2016-02-27
Has anyone loaded the 16.04 beta on this machine yet? I just got the i5, 256gb ssd and 4k panel option, curious to see if the 16.04 beta will fix any of the issues people are seeing on this machine

---

### Post by quickdry21 on 2016-02-27
> **leepe said:**
> Has anyone loaded the 16.04 beta on this machine yet? I just got the i5, 256gb ssd and 4k panel option, curious to see if the 16.04 beta will fix any of the issues people are seeing on this machine

Funny you mentioned. I installed 16.04 beta of Ubuntu **Gnome **last night, install didn't require any of the the extra steps (aside from BIOS configuration modifications) required for 15.10 (touchpad worked, didn't need nouveau.modeset, etc). 

Only change I made in the install process was the partition to install GRUB to: installer auto detected /dev/nvme, I changed it to /dev/nvme0n1. I'm not even sure if this is still necessary, I just recall doing it when installing 15.10.

Right now I'm in the process of experimenting with nvidia-prime and external display support, I had a challenging time getting external displays working in 15.10, after trying many different kernels (Ubuntu mainline, intel-drm-nightly), I was able to get them going only when using ```
prime-select intel
``` on 4.4.

Slightly off topic to the question, but this may be useful to anyone else using Ubuntu Gnome:

I'm slowly learning that the issues I'm having may be gnome related: it seems nvidia-prime was originally implemented to work with lightdm, with gdm support coming later.

It seems some combination of packages handle enabling/disabling prime in Ubuntu Gnome:

- nvidia-prime provides scripts for querying prime status (prime-supported), calling xrandr provider offloading (prime-offload), switching between the two GPUs (prime-select), a script that invokes gpu-manager (prime-switch) as well as upstart/systemd script for enabling discrete GPU on shutdown.
- ubuntu-drivers-common package installs gpu-manager, which as far as I can tell only deals with managing xorg.conf - when nvidia-prime is active, it writes xorg.conf, when inactive, it moves/removes xorg.conf (leaving Xorg to figure it out)
- gdm package installs scripts that use scripts installed by the nvidia-prime package: /etc/gdm/Prime/Default that calls prime-offload as well as /etc/gdm/PrimeOff/Default that calls gpu-manager

From what I understand the requirement to get PRIME working is to have properly configured xorg.conf (modesetting driver, etc) and to called xrandr --setprovideroutputsource prior to launching the display manager (following details [in the arch wiki]("https://wiki.archlinux.org/index.php/NVIDIA_Optimus#GDM")). 

Anyway, random tangent, been deep in this problem for a few days now, needed to do some rubber ducking.

---

### Post by leepe on 2016-02-27
Solid, good to hear that support is always improving. Man I love open source.

---

### Post by jolsz on 2016-02-29
I am waiting for my fresh new xps 15 so time to read about dual boot ... recently I've found this topic [http://forum.notebookreview.com/threads/dell-xps-15-9550-m-2-pcie-nvme-ssd-neither-raid-nor-ahci.788397/](http://forum.notebookreview.com/threads/dell-xps-15-9550-m-2-pcie-nvme-ssd-neither-raid-nor-ahci.788397/) . 
Has anyone already tried such bios setup while installing Ubuntu?

---

### Post by asaz989 on 2016-02-29
Just solved a weird issue I was having, so here's the solution in case anyone else has run into it.

If you tried at some point to get bumblebee working, and are now having trouble with [B]only[/B ]the NVIDIA card not working at all despite having the drivers installed, you may have been bitten by [this bug]("https://github.com/Bumblebee-Project/Bumblebee/issues/525"), where bumblebee's uninstall script fails to remove a file blacklisting the nvidia drivers. This bug is fixed, but the fix is not in the latest Ubuntu bumblebee packages.

To check if this problem applies to your system, run `lshw -c video`, note the "configuration: " line, then run `sudo modprobe nvidia` to ignore the blacklist and manually load the nvidia driver, then `lshw -c video` again and look at the "configuration: " line. If the first time the NVIDIA card doesn't have the 'driver=nvidia' entry, but the second time it does, then bumblebee is probably messing with you.

To solve the issue, first make sure bumblebee is not installed (sudo apt-get purge bumblebee); then, manually `sudo rm /etc/modprobe.d/bumblebee.conf`.

Hope this helps!

---

### Post by lkraav on 2016-03-01
I wonder if the nvidia-free version of the upcoming Latitude 13 is going to have less of these issues.

---

### Post by rvanderwerf on 2016-03-02
Anyone have nvidia working with intel drivers after latest updates? I cannot get any version nvidia to work. It crashes my desktop after login. Purge out all nvidia drivers, back to intel and it works fine.
Also anyone using usb-c to DP display(4k) + HDMI display (1.2k) + 4k laptop display? Plugging in the hdmi while everything is working on intel crashed my machine and I have to power it off.

---

### Post by Johannes_Stickel on 2016-03-03
I also had to switch to Intel drivers after the update.

External DP display (4k, 60 Hz) is working fine using usb-c. I can confirm that this cable ([http://www.amazon.de/gp/product/B00YODRY26](http://www.amazon.de/gp/product/B00YODRY26)) is working for me. 

The only issue is that in KDE you can only configure a system wide DPI setting. Thus the font is either to small on the notebook display or to large on the external one. A DPI setting for each display would be great. Not sure if there currently exists a Linux Desktop that can do this.

---

### Post by Cowlike on 2016-03-04
I just installed Xubuntu 16.04 beta1.  Two issues:

1.  Reverse scroll doesn't work consistently.  Very annoying.  It works in Firefox, but not in Google Chrome or Terminator (in various settings windows).

2.  Laptop seems to run warm.  The fans are consistently on.  I used to run Xubuntu 15.10 on the XPS 13, and it was silent most of the time.

Anyone come across these issues?  Any suggested fixes?

---

### Post by william104 on 2016-03-05
Installed Ubuntu Gnome 16.04 beta 1 on an encrypted volume. On the screen where the boot asks me to enter the password to decrypt the disk, the keyboard does not seem to respond when using kernel 4.4.0-10 (the default in the boot loader). Workaround is to select advanced options and boot Ubuntu with 4.4.0-7-generic instead.

Installation was done as dual boot with Windows and resulted in Windows boot breaking with "Inaccessible Boot Device". Workaround was to press F12 to use Windows boot loader and to navigate the repair screens to restart in Safe Mode. After restarting from Safe Mode once, Ubuntu's boot loader would start Windows normally.

---

### Post by michele20 on 2016-03-05
@quickdry21, @william104 thanks for sharing your experience and status with Ubuntu Gnome 16.04 beta!!

I'm waiting an "almost-stable" release of Ubuntu Gnome 16.04 and install it on my xps 15. It seems is going already better than the previous release! :)

---

### Post by Rob_Stevenson on 2016-03-06
Has anyone got suspend working properly? If so what steps are required? I'm on 15.10 and trying to resume from suspend I just get a lit power button but black screen and nothing responds (e.g. cannot toggle keyboard backlight). I have to hold the power button until the machine powers down and then do a normal power on. I've tried upgrading kernel to 4.3.4 but that hasn't helped

---

### Post by Rommel_Lapuz on 2016-03-06
Hey guys,

Thanks for the installation guide for this but I decided to install Ubuntu Mate 16.04 beta on my Dell XPS 15 (i7, 512gb SSD, GTX960m + Intel 530, 16gb RAM) and it is running smooth and no problems since then. Here's what I did:

1.) Download and Prepare USB for Ubuntu Mate 16.04 under Windows.
2.) Backup Windows, Just in case I screw up :D
3.) Flashed the latest BIOS off Dell Website then after install I restored to BIOS Default then change the following:
    - ACHI Mode
    - Secure Boot OFF
4.) Boot up the USB Live Preview ***No need to edit anything. Just hit Enter on GRUB
5.) Whats working so far on Live USB?
    - Wifi
    - Bluetooth
    - Touchpad and Keyboard
6.) Connect to internet via Wifi or USB-Ethernet
7.) Start installation
    - I deleted my whole partition and created a new one like this:
                - EFI = 200MB
                - SWAP = 16GB (End of Partition)
                - System Drive = 50GB (mount point: /)
                - Home Drive = The rest of GBs (mount point: /home)
8.) Point the bootloader on /nvme
9.) Install as normal
10.) Reboot
11.) Install Nvidia using PPA (I used 358 because I had problems with 361 when running Steam) ***Don't reboot yet
    - I only installed nvidia-358 and nvidia-prime (prime-indicator doesnt work for me for some reason but its not a big deal for me)
12.) Download Intel Graphics Linux (just google it and download the one for 64bit 15.10 version) and install it. ***Don't reboot yet
13.) Trick the installer that you are running 15.10 by typing this command in the terminal:
    ```

sudo cp /etc/lsb-release /etc/lsb-release.backup
sudo nano /etc/lsb-release

```

  - Edit the line where it says 16.04 to 15.10
  - Edit the line where it says xenial to wily
  - CTRL+X, CTRL+Y, Enter
12.) Now run the Driver Installer for Intel Graphics   ***Don't reboot yet
13.) Copy the original lsb-release by:

```

sudo cp /etc/lsb-release.backup /etc/lsb-release

```

14.) Restart
15.) Enjoy a stable system, well I think it is. 

Let me know below if you have any issues and lets figure it out together.

PS. Sorry if I am putting 16.04 installation into a 15.10 Installation Post.


What's working:
- Wifi
- Bluetooth
- Trackpad (need to tweak somehow to recognise palm when typing haha pretty sensitive)
- Suspend/Sleep, Reboot, Shutdown
- NVIDIA 960m and Intel 530 with HDMI either graphics works
- Sound

What's Annoying?
- Ubuntu Mate doesnt support HiDPi yet (or I just don't know how to), my default resolution is 1920x1080 still looks great
- prime-indicator (success on installation but everytime I select either NVIDIA or INTEL it doesn't log out automatically)


What do I have installed at the moment?
- Steam
- DOTA 2
- League of Legends via Play on Linux
- CS:GO
- MATLAB
- VirtualBox (Running Windows 7 - with more DEV Tools installed)

---

### Post by bertusrex on 2016-03-06
I'm trying out Ubuntu 16.04 (daily build of feb 29) on my XPS 15/FHD, and am able to finally get some good energy consumption with intel graphics active. It's on a par with Window now.

I installed to a separate partition, pointed bootloader installation to EFI partition, and 16.04 gets added to grub as a boot option.

I set brightness to about 20%, and after optimizing power usage by running 
```

$ sudo powertop --auto-tune
$ sudo powertop
```

And letting it idle for a minute, the consumption is about 6,5W (screen on, wifi on, BT on). On 15.10 I get around 15-18W with intel, and around 9-10W with nvidia in this case. There's a small glitch: the laptop display flashes every now and then (irregularly, about once every 20 sec).

Disabling wifi and BT drops it further from 6.5W to slightlly over 5W. When doing light work (such as typing this post, consumption goes up to 8-9W.

Can't get nvidia/prime to work properly yet (after logging in screen flashes black, then returns to login prompt. I have the same issue with 15.10 nonwadays, It used to work for me with different kernels/nvidia versions, not sure what changed.

Anyway, definitely an improvement in power consumption with 16.04 compared to 15.10, good news for owners like myself with a modest 56Wh battery...

```
$ uname -a
Linux xtest-XPS-15-9550 4.4.0-9-generic #24-Ubuntu SMP Mon Feb 29 19:33:19 UTC 2016 x86_64 x86_64 x86_64 GNU/Linux
```

---

### Post by sze5003 on 2016-03-06
> **bertusrex said:**
> I'm trying out Ubuntu 16.04 (daily build of feb 29) on my XPS 15/FHD, and am able to finally get some good energy consumption with intel graphics active. It's on a par with Window now.

I installed to a separate partition, pointed bootloader installation to EFI partition, and 16.04 gets added to grub as a boot option.

I set brightness to about 20%, and after optimizing power usage by running 
```

$ sudo powertop --auto-tune
$ sudo powertop
```

And letting it idle for a minute, the consumption is about 6,5W (screen on, wifi on, BT on). On 15.10 I get around 15-18W with intel, and around 9-10W with nvidia in this case. There's a small glitch: the laptop display flashes every now and then (irregularly, about once every 20 sec).

Disabling wifi and BT drops it further from 6.5W to slightlly over 5W. When doing light work (such as typing this post, consumption goes up to 8-9W.

Can't get nvidia/prime to work properly yet (after logging in screen flashes black, then returns to login prompt. I have the same issue with 15.10 nonwadays, It used to work for me with different kernels/nvidia versions, not sure what changed.

Anyway, definitely an improvement in power consumption with 16.04 compared to 15.10, good news for owners like myself with a modest 56Wh battery...

```
$ uname -a
Linux xtest-XPS-15-9550 4.4.0-9-generic #24-Ubuntu SMP Mon Feb 29 19:33:19 UTC 2016 x86_64 x86_64 x86_64 GNU/Linux
```

Hmm I tried 16.04 and it seems I downloaded the wrong version..it was in Chinese :/

Anyway, glad to hear that 16.04 gives you better battery life. I may try it out myself now. On 15.10 I only got about 3+ hours of use with intel graphics, nvidia 358 drivers, using prime and 4.4 kernel. I also installed tlp and it did not seem to make a difference. I don't know why on windows I can get 7+ hours on the 56w battery but in Ubuntu it was nothing close.

---

### Post by rvanderwerf on 2016-03-06
> **Rob_Stevenson said:**
> Has anyone got suspend working properly? If so what steps are required? I'm on 15.10 and trying to resume from suspend I just get a lit power button but black screen and nothing responds (e.g. cannot toggle keyboard backlight). I have to hold the power button until the machine powers down and then do a normal power on. I've tried upgrading kernel to 4.3.4 but that hasn't helped

It works for me, but only with intel or nouveau video drivers... nvidia and I haven't gotten along - not only has suspend/resume not work under nvidia, half the time my screensaver kicks in and I come back, I've got a black screen with no keyboard response (machine still running but I can't even switch to a text console to kill my session though).

The intel driver has gotten much more stable, now if only I can get it to place nice with nvidia (I seem to be able to do 3 screens in nvidia vs 2 on intel). I've actually been able to play Pillars of Eternity at 1080p ok with the Intel driver now, so I've just been doing that for the time being.

---

### Post by rvanderwerf on 2016-03-06
> **sze5003 said:**
> Hmm I tried 16.04 and it seems I downloaded the wrong version..it was in Chinese :/

Anyway, glad to hear that 16.04 gives you better battery life. I may try it out myself now. On 15.10 I only got about 3+ hours of use with intel graphics, nvidia 358 drivers, using prime and 4.4 kernel. I also installed tlp and it did not seem to make a difference. I don't know why on windows I can get 7+ hours on the 56w battery but in Ubuntu it was nothing close.

haha I did the same, make sure it's the GNOME, Xfce, or MATE edition not kylin (That's the chinese one). It seems to boot up and run fine enough, it looks like a fresh install will be much easier and cleaner than 15.10. I didn't think to try bluetooth on it.

---

### Post by Cowlike on 2016-03-06
> **Cowlike said:**
> I just installed Xubuntu 16.04 beta1.  Two issues:

1.  Reverse scroll doesn't work consistently.  Very annoying.  It works in Firefox, but not in Google Chrome or Terminator (in various settings windows).

2.  Laptop seems to run warm.  The fans are consistently on.  I used to run Xubuntu 15.10 on the XPS 13, and it was silent most of the time.

Anyone come across these issues?  Any suggested fixes?

Just to follow-up on my issues:

1.  By chance, v49 and v50 of Chrome just happen to have a bug where reverse scroll doesn't work.  [See here]("https://productforums.google.com/forum/#!msg/chrome/NV9uPe1UTVI/LTaXUdtMCQAJ").

2. Mostly solved by upgrading to 16.04.  As reported by bertusrex in #287, I see power usage of ~5.5W with BT off, screen at 20%.  Much, much better than on 15.10, where I saw > 15W idle.


A couple of new issues:

3.  Intel drivers cause flickering (rapidly varying brightness, like an old CRT with low refresh rate) at the very lowest brightness setting.  This does not occur when using NVIDIA (although that bumps idle power to ~7.5W).  (I'm on latest drivers per Rommel_Lapuz in #283.)

4.  Intel drivers also seem to cause "blinking" (screen going completely black for a fraction of a second; happens randomly in bursts of three or four times over a few seconds) after waking from suspend.  Don't see this on NVIDIA either.

5.  Touchpad gestures: can't get touchegg to recognize three-finger gestures.  It recognizes two fingers fine after disabling synclient for two fingers (although scroll speed is far too high), but can't get three fingers working.  Worked just fine on my XPS 13.

6.  Under both Intel and NVIDIA, VLC videos are "on top" of all other windows and UI elements, and generally cause tearing or freezing when moving or resizing.

Overall, looking very good.  Video drivers need a bit more work though.

---

### Post by sze5003 on 2016-03-06
> **rvanderwerf said:**
> haha I did the same, make sure it's the GNOME, Xfce, or MATE edition not kylin (That's the chinese one). It seems to boot up and run fine enough, it looks like a fresh install will be much easier and cleaner than 15.10. I didn't think to try bluetooth on it.

Yea I am trying the Mate version now. Going to see how my battery life turns out with this one. I would very much like to run Arch but I can't seem to get it to work when it comes to installing a desktop environment.

---

### Post by fgpapado on 2016-03-09
> **rvanderwerf said:**
> I think this bit me today for some reason. I upgraded to 32gb of ram which shouldn't matter at all but I couldn't log in anymore. I removed the intel and all nvidia, went back to nouveau, the re-installed intel and I'm back. I am about to add nvidia back into the mix. Is 361 the driver to run right now?


update I re installed nvidia 352 drivers, and everything is hosed again. It seems latest intel drivers are not playing nice with the nvidia ones. If I just install the intel drivers, everything comes back to life (had to force purge all the nvidia* and reinstall ubuntu-desktop) to get everything back.

Anyone here running 2 4k screens. I recently got a dell 4k 27" I'm using via usb-c-> displayport adapter because the panel can't do 60hz via hdmi. Is there a usb-c to dual DP that works in linux?

I tried my laptop 4k screen + usb-c 4k screen + u2412m at 1920x1200 and intel drivers completely crash. Before latest update nvidia would work, but system would freeze when coming back from a screen timeout.

Just had the same issue; intel-graphics (1.4.0) really doesn't play along with nvidia (both 358 and 361). I have now purged both drivers (working with the basic - nouveau), planning to go nvidia-only, but Unity is now lacking its dash and most of its features. I've reinstalled ubuntu-desktop and unity, but that didn't seem to work. Am I missing something? Any suggestions?

---

### Post by bertusrex on 2016-03-09
Today when messing with intel/nvidia switching problems in 15.10 I noticed that the nvidia card does not get powered off when Intel is active. That would explain the high (18W) consumption when running on Intel graphics. If you're 'suffering' from this, you can try the below:

verify that intel card is active:
```
$ prime-select query
intel

```

verify that nvidia card is (incorrectly) powered on:
```
$ cat /proc/acpi/bbswitch 
0000:01:00.0 **ON**

```
If it is on (and you're currently using the Intel card), you can turn nvidia off manually with the following:
```
$ sudo -i
$ rmmod nvidia_modeset
$ rmmod nvidia
$ echo OFF > /proc/acpi/bbswitch
$ cat bbswitch 
0000:01:00.0 **OFF**
$ exit

```
Consumption drops from about 18W to 9W, which is still higher than with 16.04 beta (6W), but it's way better than before.

> **fgpapado said:**
> Just had the same issue; intel-graphics (1.4.0) really doesn't play along with nvidia (both 358 and 361). I have now purged both drivers (working with the basic - nouveau), planning to go nvidia-only, but Unity is now lacking its dash and most of its features. I've reinstalled ubuntu-desktop and unity, but that didn't seem to work. Am I missing something? Any suggestions?

If you log in and see an empty desktop, but have a moving mousepointer, you can probably fix it like this:
1) right-click the desktop and start a terminal
2) start the CompizConfig Settings Manager: 
```
$ ccsm
```
If ccsm is not installed, first do this and try again:
```
$ sudo apt-get install compizconfig-settings-manager
```
3) type in filter field 'unity' the click the purple 'Ubuntu Unity Plugin'. On the left side of the screen check 'Enable Ubuntu Unity Plugin'. You'll then have to confirm several dependencies (like OpenGL) in dialogs.
Now the dash will pop back up, and new windows will be decorated again. If you're use to using multiple workspaces, you have to re-enable 'Desktop Wall' plugin too.

> **rvanderwerf said:**
> I think this bit me today for some reason. I upgraded to 32gb of ram which shouldn't matter at all but I couldn't log in anymore. I removed the intel and all nvidia, went back to nouveau, the re-installed intel and I'm back. I am about to add nvidia back into the mix. Is 361 the driver to run right now?

update I re installed nvidia 352 drivers, and everything is hosed again. It seems latest intel drivers are not playing nice with the nvidia ones. If I just install the intel drivers, everything comes back to life (had to force purge all the nvidia* and reinstall ubuntu-desktop) to get everything back.


I was having problems using nvidia GPU, after login the screen would go black and return to login screen. I had been using nvidia 361 and 358 succesfully, but probably after installing the Intel Graphics Driver installer v1.4.0 from 01.org it broke.

I had a hard time uninstalling those intel drivers, I finally succeeded with the steps below, and got prime switching working again (with nvidia-358, but 361 should probably work too). Maybe not all of the below steps are needed, and the instructions might even break your system, use at your own risk. If you have a nicer/cleaner way, please post.

I combined info from these sources:
[http://askubuntu.com/questions/280593/how-to-uninstall-intel-linux-graphics-installer-and-revert-to-default-drivers](http://askubuntu.com/questions/280593/how-to-uninstall-intel-linux-graphics-installer-and-revert-to-default-drivers)
[http://askubuntu.com/questions/539152/cannot-access-secondary-gpu-error-could-not-load-gpu-driver](http://askubuntu.com/questions/539152/cannot-access-secondary-gpu-error-could-not-load-gpu-driver)

The below assumes a 15.10 x64 install with nvidia-358, nvidia-prime and intel-linux-graphics-installer_1.4.0-0intel1_amd64.deb from 01.org are installed, and that you're having trouble logging in with nvidia activated.

```

sudo sh -c 'echo "\nPackage: *\nPin: release a=wily*\nPin-Priority: 1001\n\nPackage: *\nPin: origin download.01.org\nPin-Priority: -100\n" > /etc/apt/preferences.d/intel-removal'
sudo apt-get dist-upgrade
sudo rm /etc/apt/preferences.d/intel-removal
sudo rm /etc/apt/sources.list.d/intellinuxgraphics.list*
sudo apt-get update
sudo apt-get purge intel-linux-graphics-installer
sudo dpkg-reconfigure xserver-xorg
# other nvidia versions probably ok too
sudo apt-get install --reinstall nvidia-358
sudo dpkg-reconfigure bbswitch-dkms
sudo ldconfig -n
sudo update-initramfs -u
# optional
sudo reboot

```

I damaged my installation in the process leading up to the above solution by deleting some extra packages manually (now sound no longer working), so now going to try to fix that... 

Hope it helps someone!

---

### Post by sze5003 on 2016-03-10
> **bertusrex said:**
> Today when messing with intel/nvidia switching problems in 15.10 I noticed that the nvidia card does not get powered off when Intel is active. That would explain the high (18W) consumption when running on Intel graphics. If you're 'suffering' from this, you can try the below:

verify that intel card is active:
```
$ prime-select query
intel

```

verify that nvidia card is (incorrectly) powered on:
```
$ cat /proc/acpi/bbswitch 
0000:01:00.0 **ON**

```
If it is on (and you're currently using the Intel card), you can turn nvidia off manually with the following:
```
$ sudo -i
$ rmmod nvidia_modeset
$ rmmod nvidia
$ echo OFF > /proc/acpi/bbswitch
$ cat bbswitch 
0000:01:00.0 **OFF**
$ exit

```
Consumption drops from about 18W to 9W, which is still higher than with 16.04 beta (6W), but it's way better than before.

I noticed this too. Both cards remain on no matter which one you want to use. I was never able to get Bumblebee working though. Do you have to run this command each time you turn on the machine? I'm currently using intel but I want to test turning off intel and using nvidia and vice versa to see what the difference is. I normally get only about 3-4hrs of battery life in Ubuntu.

---

### Post by bertusrex on 2016-03-10
> **sze5003 said:**
> I noticed this too. Both cards remain on no matter which one you want to use. I was never able to get Bumblebee working though. Do you have to run this command each time you turn on the machine? I'm currently using intel but I want to test turning off intel and using nvidia and vice versa to see what the difference is. I normally get only about 3-4hrs of battery life in Ubuntu.

You could make a script based on the commands which you make run at startup or login, otherwise you'd have to do it manually each time.  

I think you can't turn off intel when using nvidia, the internal laptop display is always driven by the intel graphics. When nvidia is activated, the 960M renders and image and places it into a buffer that is displayed by the intel chipset on the internal display ([offloading]("https://wiki.archlinux.org/index.php/PRIME#PRIME_GPU_offloading")). Maybe turning Intel off could be done when connecting an external display which does not have to go offload to the intel GPU, but that would hardly be a 'portable' scenario where battery life is important.

---

### Post by rvanderwerf on 2016-03-10
Going to try this tonight thanks. I had just removed the packages with dpkg and it wen to noveau driver, but I still could just install/use nvidia. I hope this helps!


> **bertusrex said:**
> I was having problems using nvidia GPU, after login the screen would go black and return to login screen. I had been using nvidia 361 and 358 succesfully, but probably after installing the Intel Graphics Driver installer v1.4.0 from 01.org it broke.

I had a hard time uninstalling those intel drivers, I finally succeeded with the steps below, and got prime switching working again (with nvidia-358, but 361 should probably work too). Maybe not all of the below steps are needed, and the instructions might even break your system, use at your own risk. If you have a nicer/cleaner way, please post.

I combined info from these sources:
[http://askubuntu.com/questions/280593/how-to-uninstall-intel-linux-graphics-installer-and-revert-to-default-drivers](http://askubuntu.com/questions/280593/how-to-uninstall-intel-linux-graphics-installer-and-revert-to-default-drivers)
[http://askubuntu.com/questions/539152/cannot-access-secondary-gpu-error-could-not-load-gpu-driver](http://askubuntu.com/questions/539152/cannot-access-secondary-gpu-error-could-not-load-gpu-driver)

The below assumes a 15.10 x64 install with nvidia-358, nvidia-prime and intel-linux-graphics-installer_1.4.0-0intel1_amd64.deb from 01.org are installed, and that you're having trouble logging in with nvidia activated.

```

sudo sh -c 'echo "\nPackage: *\nPin: release a=wily*\nPin-Priority: 1001\n\nPackage: *\nPin: origin download.01.org\nPin-Priority: -100\n" > /etc/apt/preferences.d/intel-removal'
sudo apt-get dist-upgrade
sudo rm /etc/apt/preferences.d/intel-removal
sudo rm /etc/apt/sources.list.d/intellinuxgraphics.list*
sudo apt-get update
sudo apt-get purge intel-linux-graphics-installer
sudo dpkg-reconfigure xserver-xorg
# other nvidia versions probably ok too
sudo apt-get install --reinstall nvidia-358
sudo dpkg-reconfigure bbswitch-dkms
sudo ldconfig -n
sudo update-initramfs -u
# optional
sudo reboot

```

I damaged my installation in the process leading up to the above solution by deleting some extra packages manually (now sound no longer working), so now going to try to fix that... 

Hope it helps someone!

---

### Post by fgpapado on 2016-03-11
Worked like a charm, thanks!

I'll go nvidia-only until I figure out the intel binary drivers (or 16.04 hits).

---

### Post by holdfenytolvaj on 2016-03-12
Maybe many already knows, but was new to me. The touchpad palm detection was not on by default so i've ended up
adding these lines to ~/.xsessionrc:
```

xinput set-prop 13 318 1
xinput set-prop 13 319 1, 1

```

where 13 is the id of the touchpad
```

xinput | grep Touchpad

```

and 318 and 319 are the palm detection ids:
```

xinput list-props 13

```

---

### Post by holdfenytolvaj on 2016-03-12
I was a bit in rush with it. The issue became better, but not solved completely, so still had to add
```
syndaemon -i 1 -K -d
```
to disable the touchpad meanwhile typing

---

### Post by zeratul2 on 2016-03-13
> **holdfenytolvaj said:**
> I was a bit in rush with it. The issue became better, but not solved completely, so still had to add
```
syndaemon -i 1 -K -d
```
to disable the touchpad meanwhile typing

Thank you so much for these tips, this is really the thing that I was looking for for a long time. Finally I can work with the touchpad instead of carrying a mouse around.

apparently the syndaemon is launched with wrong parameters
[http://askubuntu.com/questions/709730/touchpad-problem-how-to-disable-default-syndaemon-auto-startup](http://askubuntu.com/questions/709730/touchpad-problem-how-to-disable-default-syndaemon-auto-startup)

I couldn't find where it is launched from by gnome-system-daemon, so I did
sudo mv /usr/bin/syndaemon /usr/bin/syndaemon2
en changed syndaemon -i 1 -K -d to syndaemon2 -i 1 -K -d to make it work at startup. A bit dirty but gets the job done on reboot.

Is someone writing an updated tutorial on all these new findings? Or do we have a summarizing wiki on the complete installation? This topic is getting long for someone new to read through.

---

### Post by bertusrex on 2016-03-15
> **zeratul2 said:**
> Thank you so much for these tips, this is really the thing that I was looking for for a long time. Finally I can work with the touchpad instead of carrying a mouse around.

apparently the syndaemon is launched with wrong parameters
[http://askubuntu.com/questions/709730/touchpad-problem-how-to-disable-default-syndaemon-auto-startup](http://askubuntu.com/questions/709730/touchpad-problem-how-to-disable-default-syndaemon-auto-startup)

I couldn't find where it is launched from by gnome-system-daemon, so I did
sudo mv /usr/bin/syndaemon /usr/bin/syndaemon2
en changed syndaemon -i 1 -K -d to syndaemon2 -i 1 -K -d to make it work at startup. A bit dirty but gets the job done on reboot.



It appears to be launched with hardcoded parameters from  /plugins/mouse/gsd-mouse-manager.c (and perhaps other locations, haven't looked further)
```
static int set_disable_w_typing (GsdMouseManager *manager, gboolean state)
{
        if (state && touchpad_is_present ()) {
                GError *error = NULL;
                GPtrArray *args;

                if (manager->priv->syndaemon_spawned)
                        return 0;

                if (!have_program_in_path ("syndaemon"))
                        return 0;

                args = g_ptr_array_new ();

                g_ptr_array_add (args, "syndaemon");
                g_ptr_array_add (args, "-i");
                g_ptr_array_add (args, "1.0");
                g_ptr_array_add (args, "-t");
                g_ptr_array_add (args, "-K");
                g_ptr_array_add (args, "-R");
                g_ptr_array_add (args, NULL);
```
In addition to your renaming syndaemon to syndaemon2, perhaps it could work to create /usr/bin/syndaemon as a shell script ignoring the supplied commandline parameters and using its own ones to invoke syndaemon2, to make gnome-system-daemon think it loaded syndaemon, while it will actually have loaded syndaemon2 with correct options.

---

### Post by micahgalizia on 2016-03-17
Hi,

This is a long thread so appologies if its been answered already. I updated to 16.10 and was able to get my bluetooth working by copying BCM-0a5c-6410.hcd into /lib/firmware/brcm.  I got that file from [https://www.dropbox.com/s/8goc4omhnzxij93/BCM-0a5c-6410.hcd?dl=0](https://www.dropbox.com/s/8goc4omhnzxij93/BCM-0a5c-6410.hcd?dl=0) (which I saw in this forum [https://bbs.archlinux.org/viewtopic.php?id=204739](https://bbs.archlinux.org/viewtopic.php?id=204739))

No idea where it came from or why its not in Ubuntu already, but it works and everything else appears to continue to work.

---

### Post by ckam032 on 2016-03-18
Maaan, I'm having some issues. My XPS doesn't even show the live USB. Work's fine on my desktop. Any ideas anyone???  I've been searching around and can't seem to find anything

---

### Post by bertusrex on 2016-03-18
> **micahgalizia said:**
> Hi,

This is a long thread so appologies if its been answered already. I updated to 16.10 and was able to get my bluetooth working by copying BCM-0a5c-6410.hcd into /lib/firmware/brcm.  I got that file from [https://www.dropbox.com/s/8goc4omhnzxij93/BCM-0a5c-6410.hcd?dl=0](https://www.dropbox.com/s/8goc4omhnzxij93/BCM-0a5c-6410.hcd?dl=0) (which I saw in this forum [https://bbs.archlinux.org/viewtopic.php?id=204739](https://bbs.archlinux.org/viewtopic.php?id=204739))

No idea where it came from or why its not in Ubuntu already, but it works and everything else appears to continue to work.

I've done the same thing before (extract firmware from Windows driver, see [here]("http://ubuntuforums.org/showthread.php?t=2301071&page=13&p=13403372#post13403372")) to fix BT problems with my Logitech MX Anywhere 2 mouse. The hcd file you're linking to is exactly the same as mine. 

I'm not sure why it's not in linux-firmware, but even with this file present, the system initially seems to load an older version, and after a few seconds it loads the version from /lib/firmware/brcm/BCM-0a5c-6410.hcd:

with /lib/firmware/brcm/BCM-0a5c-6410.hcd
```

...
Bluetooth: hci0: BCM (001.001.005) build 0000
... 
Bluetooth: hci0: BCM (001.001.005) build 0422 
```

BTW I used this Windows driver file: BCM20703A1_001.001.005.0214.0422.hex and converted with hex2hcd to hcd file.

PS Some info on BCM BT firmware loading mechanism in [this]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1065400") older bugreport.

---

### Post by ptsneves on 2016-03-19
```
#!/bin/sh

echo - | awk "{printf \"%.1f\", \
$(( \
  $(cat /sys/class/power_supply/BAT0/current_now) * \
  $(cat /sys/class/power_supply/BAT0/voltage_now) \
)) / 1000000000000 }"
 
``` 
I am getting the weirdest reports with the power consumption and I would like to know if anybody can relate. When I am on AC power on intel I have 4.9 Watts and when on battery I have 21.5. Are these numbers meaningful?

---

### Post by Javier_Macias-Guar on 2016-03-20
@[**[COLOR=#000000]Rommel_Lapuz[/COLOR]**]("http://ubuntuforums.org/member.php?u=2023506"), thank you very much for your great post. This and all the previous contributions in this thread made me decide on installing 16.04 beta to test my XPS 15 in a dual boot setup. The installation was successful although I still have some (minor) problems.

  One of the most annoying issues is the palm detection not workig properly. I tried with some tweaking without full success). Could you please give me details on the specific parameters/configuration you are using?...

  Your post, along with your comment on a specific thread on 16.04 made me start such a thread. You can find it at [http://ubuntuforums.org/showthread.php?t=2317843](http://ubuntuforums.org/showthread.php?t=2317843) 

  Regarding the hidpi support you mentioned as lacking in Ubuntu mate,  I'm currently using cinnamon, and I'm reasonably happy with it, although  there are also some problems (please [see my post for additional details]("http://ubuntuforums.org/showthread.php?t=2317843")).

  Thank you very much again!!


  Javi

---

### Post by bertusrex on 2016-03-20
I found what appears to be a newer firmware file for the BCM20703A1 Bluetooth module. I can't vouch for the origin though, but it does not appear to belong specifically to the Dell DW1830 card. I found the BCM20703A1_001.001.005.0214.0473.hex hex file on a somewhat shady [site]("http://m.ulozto.sk/xwUqAqHG/bcm20703a1-001-001-005-0214-0473-hex"), and converted it to hcd with hex2hcd.

It loads OK, but it presents itself with a different device name than the 422 version. e.g. in powertop, instead of a BCM20703A1 Bluetooth 4.1 device (or something along those lines), you'll see:
```
   Good          Autosuspend for USB device BCM2045A0 [Broadcom Corp]

```

The firmware appears to allow me to use bluetooth with the module's Autosuspend tunable set to Good in powertop (although I'm not sure it actually uses less energy). With the 422 firmware my Logitech Anywhere 2 BT mouse would randomly disconnect at that setting, and I would have to set the tunable to Bad (non-power saving) to prevent that. With this 473 firmware I can have it set to Autosuspend and it keeps working.

I can't recommend this bluetooth firmware wholeheartetly yet because of unknown origin and different presented device name, but if you're feeling brave and would like to try it: Download the hcd file [here]("https://www.dropbox.com/s/zco362szqgqj2v6/BCM-0a5c-6410.hcd?dl=0"), copy it to /lib/firmware/brcm (keeping the filename including upper/lowercase intact), reboot and post your findings :wink:. 

(tested with 15.10, kernel 4.5)

update: Some reboots later, the device identifies like before again, e.g. in powertop: 
```

Autosuspend for USB device BCM920703 Bluetooth 4.1 [Broadcom Corp])

```
dmesg reports the firmware loaded ok, but it seems to be loaded by default as well, as if the firmware is now permanently 'flashed' in the device. (both dmesg lines now report version 0473)
```

[    9.226547] Bluetooth: hci0: BCM (001.001.005) build 0473
[   10.315594] Bluetooth: hci0: BCM (001.001.005) build 0473

```

Anyway, it seems to work fine, and because it's a higher version than before, it might have some improvements... YMMV :rolleyes:

---

### Post by holdfenytolvaj on 2016-03-21
[https://github.com/advancingu/XPS13Linux/issues/3](https://github.com/advancingu/XPS13Linux/issues/3)
It might be the case that palm detection works with 4.5 anybody tried it?

---

### Post by rvanderwerf on 2016-03-22
I have 4.5. It's really not playing nice with the intel drivers and a usb-c -> displayport adapter. It keeps hard freezing the system after I plug it in. I didn't have problems like this on 4.4.0 and 4.4.1. Sometimes it even freezes while booting. Typing on 4.4.6 atm, but dual monitor freezes it up a lot too, but not as often.

---

### Post by rvanderwerf on 2016-03-22
finally got around to running this. Thanks a lot, I just made a shell script with your commands and I'm back on nvidia again!!!!!
update - this works good but a second monitor while in nvidia is a disaster. System hard-freezes and/or logs me off when I connect a dell 4k monitor via usb-c->displayport. It works fine on intel. I suppose when gaming I can disconnect my extra monitors and switch back to nvidia for that. It's so close to nice because for a while I can get 3 monitors going, but as soon as the screensaver kicks in the system freezes. I can't do that at all on intel settings. Still if things get messed up enough I just run my scripts with your commands and I can log in again :)

---

### Post by jhouse2 on 2016-03-23
Dell Thunderbolt Dock - TB15  --- ( [http://accessories.dell.com/sna/productdetail.aspx?c=us&l=en&s=dhs&cs=19&sku=450-AEVM](http://accessories.dell.com/sna/productdetail.aspx?c=us&l=en&s=dhs&cs=19&sku=450-AEVM) )

Has anyone yet tried this out?   I got one today, and first popped over into Windows and updated the bios of the machine and the firmware of the usb-c/thunderbolt port  (there was a note with the dock instructing to make sure this was done).  After rebooting (windows) the dock is working great.

Back to Ubuntu (15.10) - plug in the dock and nothing.   Well, the laptop with charge from it, but other than that it does not recognize anything in the dock - not the ethernet port, display ports, audio, usb ports, .. nothing at all.  ('lsusb' lists nothing different with it plugged in vs. without it plugged in).

I didn't yet spend any time looking into it - just wondered if anyone else has yet poked into this.

And on a related note, has anyone come up with a different solution for driving two external 4K displays?

---

### Post by bertusrex on 2016-03-24
> **jhouse2 said:**
> Dell Thunderbolt Dock - TB15  --- ( [http://accessories.dell.com/sna/productdetail.aspx?c=us&l=en&s=dhs&cs=19&sku=450-AEVM](http://accessories.dell.com/sna/productdetail.aspx?c=us&l=en&s=dhs&cs=19&sku=450-AEVM) )

Has anyone yet tried this out?   I got one today, and first popped over into Windows and updated the bios of the machine and the firmware of the usb-c/thunderbolt port  (there was a note with the dock instructing to make sure this was done).  After rebooting (windows) the dock is working great.

Back to Ubuntu (15.10) - plug in the dock and nothing.   Well, the laptop with charge from it, but other than that it does not recognize anything in the dock - not the ethernet port, display ports, audio, usb ports, .. nothing at all.  ('lsusb' lists nothing different with it plugged in vs. without it plugged in).

I didn't yet spend any time looking into it - just wondered if anyone else has yet poked into this.

And on a related note, has anyone come up with a different solution for driving two external 4K displays?

You could try booting with the dock already connected, see if that works better. There seems to be an issue with hot-plugging USB-c devices. (see [here]("http://ubuntuforums.org/showthread.php?t=2301071&p=13442316#post13442316"))

---

### Post by bertusrex on 2016-03-29
A small tip for anyone who wants to try out the newest nvidia-364 drivers on Ubuntu 16.04 (and maybe 15.10 too): 

uninstall nvidia-361 (or other currently installed version) first, otherwise nvidia versions will become mixed up, and you won't be able to log in anymore (at least that's what happened to me).

```

# switch to intel
sudo prime-select intel
<logout>
<login>

# uninstall 361
sudo apt-get purge nvidia-361 libcuda1-361 nvidia-opencl-icd-361
#may not be necessary, just to be sure
sudo depmod -a

# install nvidia-364
sudo apt-get install nvidia-364
```

On a sidenote: nvidia GPU now seems to be switched off automatically when activating intel graphics (Xenial).

---

### Post by gerald.quintana on 2016-03-29
Just to share my experience with Wily, upgrading to Kernel 4.5 solved some issues:
- Pluging in/out an HDMI projector/screen doesn't freeze the display anymore (X error).  I am not using the NVidia chipset/driver.
- The microphone now works properly
- The Broadcom Wifi chipset seems to behave better: less errors in logs and less connection loss

Yet, I still have some issues with:
- The touchpad doesn't disable  when I start typing
- The Dell Docking station D3100: wired networking is alright, but external screen and sound is not. I managed to install the DisplayLink stuff with [https://github.com/AdnanHodzic/displaylink-debian](https://github.com/AdnanHodzic/displaylink-debian) , sadly it doesn't work.
- Some Fn keys raise errors and don't behave as expected: Session Lock (Esc), Keyboard backlighting (F10), Airplane mode (Print Screen).

---

### Post by nitish2112 on 2016-04-02
Hi, I did the same and my Ubuntu 15.10 and Windows 10 are running, but after using Ubuntu for a while ( 30 min or so ) I get this error ( see pic attached ) [IMG]http://i.stack.imgur.com/LPHYi.jpg[/IMG]

---

### Post by bertusrex on 2016-04-04
> **nitish2112 said:**
> Hi, I did the same and my Ubuntu 15.10 and Windows 10 are running, but after using Ubuntu for a while ( 30 min or so ) I get this error ( see pic attached ) 

That doesn't look normal to me, especially if it happens every time after booting 15.10 and using it for a while. If you think it is caused by kernel 4.5, you can always revert to a previous kernel. 4.5 is pretty stable now, it may be something else. Try to check your root partition for errors like this (after saving all work):

```

sudo touch /forcefsck
sudo reboot

```

---

### Post by virgosun on 2016-04-04
> **mflores3 said:**
> @joshuabc  can you share the *.hcd file you generated?  I'm having a hard time getting both bluetooth and wifi working at the same time. 

[SIZE=4]**Background:**[/SIZE]

I'm on XPS 15 9550 i5/1TB SSD SATA (I swapped in)/QHD - dual booting Linux Mint 17.3 and Windows 10

Earlier in this thread, @bertusrex provided a .hcd he compiled.  I copied to [COLOR=#696969][FONT=courier new]/lib/firmware/brcm[/FONT][/COLOR], but then noticed this dmesg output

```

[    4.631773] EXT4-fs (sda5): re-mounted. Opts: errors=remount-ro
[    4.744448] int3402 thermal: probe of INT3402:00 failed with error -22
[    5.016364] bluetooth hci0: Direct firmware load for brcm/BCM2045A0-0a5c-6410.hcd failed with error -2
[    5.016368] Bluetooth: hci0: BCM: patch brcm/BCM2045A0-0a5c-6410.hcd not found
```

So then I tried [COLOR=#696969][FONT=courier new]sudo cp  BCM-0a5c-6410.hcd BCM2045A0-0a5c-6410.hcd[/FONT][/COLOR] - bluetooth works perfectly, but this kills the wifi somehow.  I have to reload factory bios settings to get it to work again, then of course, my bluetooth is not working again.  I tried the 

I tried the bcmwl-kernel-source_6.30.223.248+bdcom package in the driver manager, but my laptop just freezes attempting to apply and the broadcom option disappears from my driver manager.

[SIZE=4]**FYI For others:**[/SIZE]

Other users: Linux mint 17.3 worked out of the box w/ the [COLOR=#696969][FONT=courier new]nouveau.modeset=0[/FONT][/COLOR] trick others mentioned.  Graphics were slow, but after install proper nvidia and intel drivers others mentioned, no problem.  - graphics drivers can be found here: [https://01.org/linuxgraphics/downloads/skylake-dmc-1.23](https://01.org/linuxgraphics/downloads/skylake-dmc-1.23). HDMI worked no issue. I ran into additional issues when i attempted upgrades to kernel 4.2 or 4.3, so I just kept the default 3.19.  Still issues: headphone jack doesn't work and bluetooth issue mentioned above.

Can you share me what ever firmware hcd file you have for this bluetooth BCM2045A0? I extract hcd from Windows 10 but it not work.
I have this in my Lenovo Yoga 500. It work well under Windows and Hackintosh.
I don't know how you make it work but this card require a slightly different method to uplaod firmware. I confirm it works on Hackintosh without upload firmware.
See this [http://www.tonymacx86.com/network/150661-brcmpatchram-upload-firmware-into-broadcom-bluetooth-usb-devices-58.html#post1231644](http://www.tonymacx86.com/network/150661-brcmpatchram-upload-firmware-into-broadcom-bluetooth-usb-devices-58.html#post1231644)
Cheer

---

### Post by bertusrex on 2016-04-06
I may be wrong, but BCM20703A1 and BCM2045A0 seem to be different partnumbers for the same device. Depending on the firmware that's loaded, the device is called "BCM920703" or "BCM2045A0". 

[This small archive I put together]("https://mega.nz/#!b4AR3T6a!wsO3HktvYWBzPgGh2b_5MysH2iTY5IBGnVDf_JiG9hc") contains 3 hcd BT firmware files (*.422, *.473, *.481) All three are functional to drive the Broadcom BT module in the Dell DW1830 wireless card as far as I can tell.

**The 473 firmware seems to identify itself as BCM2045A0, despite the pid/vid being the same as before.**

To use a particular firmware file from this archive on Ubuntu 15.10/16.04, copy it to /lib/firmware/brcm:
# example:
```
$ sudo cp BCM20703A1_001.001.005.0214.0481.hcd /lib/firmware/brcm/BCM-0a5c-6410.hcd
```
(destination filename might be /lib/firmware/brcm/BCM2045A0-0a5c-6410.hcd for Linux Mint 17.3, look in dmesg for filename)

then make sure the permissions are OK afterwards, e.g.:```

$ ls -l /lib/firmware/brcm/BCM-0a5c-6410.hcd
-rw-r--r-- 1 root root 54734 apr  6 09:39 /lib/firmware/brcm/BCM-0a5c-6410.hcd
```

It might take TWO reboots for the new firmware to work succesfully. If you still have problems after two reboots (e.g. BT or wifi not working) try resetting the bios to factory defaults.

```
File:                                    Identifies as*)          Works on XPS 15 9550 with DW1830
1) BCM20703A1_001.001.005.0214.0422.hcd  BCM920703 Bluetooth 4.1  Yes
2) BCM20703A1_001.001.005.0214.0473.hcd  BCM2045A0                Yes
3) BCM20703A1_001.001.005.0214.0481.hcd  BCM920703 Bluetooth 4.1  Yes
```

Sources: (sources are hex files, not usable as-is with Linux, I converted them to the hcd files in the archive above for Ubuntu using hex2hcd)
1) Dell, from windows 10 windows/system32/drivers folder, original probably contained in http ://downloads.dell.com/FOLDER03358907M/1/Communications_Application_5PMW3_WN32_12.0.1.730_A01.EXE
2) unknown origin, dl from : http ://uloz.to/xwUqAqHG/bcm20703a1-001-001-005-0214-0473-hex
3) unknown origin, dl from : http ://uloz.to/x3K9UupB/bcm20703a1-001-001-005-0214-0481-hex

*) output of: (exact path may be different)
```
$ cat /sys/bus/usb/devices/1-4/product

```(product name also visible in e.g. powertop.)

---

### Post by virgosun on 2016-04-06
my prob is that the firmware loads but in fact it not works.
thank you, I'll try your hcd now.
```

[   11.363157] Bluetooth: hci0: BCM: chip id 86
[   11.363161] Bluetooth: hci0: BCM (003.001.009) build 0000
[   13.064259] Bluetooth: hci0 sending frame failed (-19)
[   15.066215] Bluetooth: hci0 command 0x0c03 tx timeout
[   23.078243] Bluetooth: hci0: BCM: Reset failed (-110)
```

---

### Post by virgosun on 2016-04-07
not work on my system Lenovo Yoga Broadwell. Chip combo Wifi/BT Brcm43ae/Brcm [B]BCM2045A0
Thank you anyway[/B]

---

### Post by bertusrex on 2016-04-12
[New bios version]("http://downloads.dell.com/FOLDER03659467M/1/XPS_9550_1.2.0.exe") available for XPS 15 9550:

                                                                                                                       Dell XPS 15 9550 A06 System BIOS                                                                                     

                                 
                              
                                                                                                                                       XPS 15 9550 01.02.00 BIOS                                
                             
                                                                                                                                                                                   
1. Improved the system stability 
2. Fixed system may not able to boot with external monitor with lid closed 
3. Fixed USB audio/mouse may be lag while connecting to Dell Thunderbolt Dock (TB15) and Dell Dock (WD15)
4. Fixed Fan may be noisy while connecting to Dell Thunderbolt Dock (TB15) and Dell Dock (WD15)
5. Fixed Bitlocker Malfunction or Keeps Prompting Recovery Key every time reboot

---

### Post by ianozsvald on 2016-04-15
Here is my log for a successful install of Linux Mint 17.3 (based on Ubuntu 14.04) on a Dell XPS 9550 (i7-6700HQ, 16GB, UHD 4k touch, 1TB Samsung NVMe SSD, GTX960M Dell Wireless 1830, 84W). 

[This guide]("http://ubuntuforums.org/showthread.php?t=2317843") by Javier was great. The fresh machine had an A05 BIOS, I upgrade to A06 via the default Windows 10. Next I used sysrescuecd (with the isohybrid command before writing to the USB stick) to image the 1TB disk. Next I used Window's Partition tool to shrink Windows to 60GB, first I had to disable Virtual Memory and turn off System Restore (otherwise it said the disk couldn't be shrunk by much).

After this I could boot with the Linux Mint 17.3 live desktop. Via the installer I added a 36GB swap partition (not sure if it is necessary but I figured it wouldn't hurt) and the rest was formatted as root (/) as ext4. The installation went smoothly, I opted to encrypt /home. My 2G wifi router was identified (I still don't have 5G).

The tiny fonts on the Mint desktop were hard work so "Preferences | General | Desktop Scaling | Normal->HiDPI". Nvidia was setup using the Driver Manager with  352.63. Kernel 3.19.0.32 was installed,  3.19.0.58 worked too. Swapping between Nvidia and Intel graphics was fine. Sound works fine. I didn't try Bluetooth.

I tried kernel's 4.2.0.35 and 4.4.0.18 but the system wouldn't boot (it stopped after a few lines of post-GRUB text, hung, then dropped to busybox), I've stuck with 3.19.0.58.

Suspend seems to work (I've tried several in a row inbetween boots, no problems yet). 

Some problems:
[LIST]
[*]Some GUI elements don't work so well with HiDPI (e.g. fixed size windows) 
[*]Powertop v2.5 only shows the C states POLL, C1, C2, C3 (I was expecting lots more, I guess this is a 3.19 kernel issue) 
[*]Powertop shows 27W at idle (no browser, wifi on, screen bright) 3hr projected life (this is probably lower compared to a newer 4.x kernel) 
[*]I've not added any proprietary firmware for the wifi 
[*]GRUB has slow keyboard response - using the down arrow takes approx 1/2 second per press - does anyone know how to solve this? 
[*]Using the nvidia control panel I can swap between nvidia and the Intel driver, after a logout with Intel Powertop reports 10W and 8 hours 
[/LIST]

I tried a live CD for Ubuntu 16.04beta2 and note that Powertop (v2.8) reports more states (C2, C3, C6, C7, C8, C9, C10), also both 2G+5G wifi worked immediately and on the nouveau driver Powertop reported 16W of power (fairly bright screen, wifi on, Firefox open).

 Probably the next sensible step is to wait for a couple of weeks until Linux Mint 18 is available and then I expect to reinstall. The machine seems to be working fine, I'll log any other problems in this post.

Update - I'm now running 4.4.0-22-generic and I'm still with Linux Mint 17.3. After switching to the new kernel the boot no longer works but the [edit with nvme]("https://bugzilla.kernel.org/show_bug.cgi?id=108981") noted here was all that was needed. I'm using the Intel GPU at present, I've been working for 4 hours and I still have plenty of battery. I've also Suspended once this session without a problem. The Intel GPU has screen glitches on occasion (an alt-tab away and back clears them), I'm not using any boot switches. Powertop 2.5 reports more power states with this kernel than before (C1E-SKL, C3-SKL, C7s-SKL, C8-SKL, C9-SKL, C10-SKL, RC6pp).

Update - for Windows 10 the dual-boot was unstable, I wasn't using at first, in the last few weeks I tried (to install the new Doom :-) and had BSODs every 30 minutes. It turns out the Microsoft AHCI drivers don't like AHCI mode. The Samsung 950 Pro driver linked by [Nekobai was the answer]("https://m.reddit.com/r/Dell/comments/3yueec/help_request_frequent_critical_process_died_error/"). I'd already used Windows Update and Dell Update to update all my drivers and that hadn't helped. With the Samsung 950 Pro driver I'm happily playing Doom.

Update - I've replaced the stock 16GB with [Crucial 32GB DDR4-2400]("http://uk.crucial.com/gbr/en/xps-15-%289550%29/CT7891570") and it works just fine.

Update - Now I'm trialling kernel 4.7.0-generic on Mint 18 (4.4.0 worked fine on Mint 18 too). powertop 2.8 reports *either* PC2/PC3 if I use the nvidia driver (361.42) or PC2-PC8 (much much better!) if I switched to nouveau ([COLOR=#000000][FONT=Arial]1:1.0.12), I'm sticking with the nouveau driver as I stick to the Intel GPU in Linux anyhow (I only use the nvidia GPU in Windows for Doom). The difference between the two is - using Intel GPU with nvidia driver installed powertop reports 25W, using Intel GPU with nouveau driver installed powertop reports 16W.
[/FONT][/COLOR]

---

### Post by loumray on 2016-04-17
Just took the risk to upgrade a bit early to 16.04 LTS from 15.10 kernel 4.2 yesterday and have to say I'm quite impressed so far.

Upgrade went pretty smoothly. Best thing is power usage has improved dramatically! Only minor issue I face so far was the clock could not auto sync, so I set it up manually for now.

Thank you so much for the infos lads! Keep it coming!

---

### Post by markdueck-bz on 2016-04-18
@loumray - I did the same a week ago, but now I'm having issues with my wireless and stand by not working.  It seems it was an update though because it stopped after a few reboots.  Hoping it will be fixed by coming updates.  

On a different topic, can someone tell me if the Thunderbolt ['firmware' update]("http://www.dell.com/support/home/us/en/19/Drivers/DriversDetails?driverId=GGDVY&fileId=3525384517&osCode=WT64A&productCode=xps-15-9550-laptop&languageCode=en&categoryId=DK") for windows is actually a hardware update, or is it just drivers?

---

### Post by bobwood2 on 2016-04-21
I'm on a XPS 9550, with a 500 GB HDD and a 32 GB SSD. The SSD shows up in the BIOS (as "m.2. PCIe SSD-0") but it isn't detected by Ubuntu. Any suggestions for how I can get Ubuntu to recognize my SSD? I remembered to disable secure boot in the BIOS, and to change from "RAID" to "AHCI". 

FWIW, I'm using Ubuntu 16.04 nightly (but I had the same problem with 15.10). I've also tried both the 4.4 kernel that comes with Ubuntu, as well as 4.6 beta mainline kernel.

Thanks!

---

### Post by loumray on 2016-04-22
@markdueck-bz - After a week of use, I have seen the wireless not working a few times after booting as well.  A quick "sudo service NetworkManager restart" seems to fix it every time . Hopefully the coming updates will provide a better stability to the NetworkManager

---

### Post by rvanderwerf on 2016-04-23
yep I am seeing the same. I couldn't even get to wifi on 4.4.8 but when I went back to 4.4.0 stock kernel it's working (but it makes weird popping noises in my external speakers)

update: I restarted 4.4.8 after 4.4.0-21 and wifi has been working ever since today. I've also got nvidia 368 working with 3 monitors (2 4k plus a 1200p) and it hasn't frozen all day after the lock screen kicked in. Every other kernel combo will freeze the system when you invoke the unlock screen after the system is idle.

So for me the magic combo is: 16.04 + 4.4.8 kernel (ubuntu version). So far I have the best of both worlds now between intel for low power usage while unplugged and nvidia + 3 monitors and performance when plugged in!

---

### Post by marco furio ferrario on 2016-04-23
Can someone sum up situation installing the new 16.04 LTS release on XPS 15 9550?
Does it work or does it need all the fixing of the prevoius version listed in this thread before?

Thanks

---

### Post by kylea on 2016-04-24
**16.04 LTS release on XPS 15 9550 - 1920 x 1080 - FHD Screen - Non Touch**

I have completed a new install of 16.04 LTS release on a XPS 15 9550, 16GB with 512GB SSD.

Installed Ubuntu Gnome basically following the first post in this thread and a few others ([http://wiki.yobi.be/wiki/Laptop_Dell_XPS_15):](http://wiki.yobi.be/wiki/Laptop_Dell_XPS_15):)

I updated to Dell BIOS : via XPS_9550_1.2.0.exe

Screen - I do see occasional artifacts from the mouse

Issues Resolved:

**1. Bluetooth** - would not recognise any device - copied the driver BCM-0a5c-6410.hcd into  /lib/firmware/brcm, the file is available on the web, see here: [https://www.dropbox.com/s/8goc4omhnzxij93/BCM-0a5c-6410.hcd?dl=0](https://www.dropbox.com/s/8goc4omhnzxij93/BCM-0a5c-6410.hcd?dl=0)

**2. Bluetooth **headset would not work in A2DP mode - refer to [https://bugs.launchpad.net/ubuntu/+source/bluez/+bug/1438510](https://bugs.launchpad.net/ubuntu/+source/bluez/+bug/1438510), comment #5

**3. Used Nvidia **364.15 instead of 361.42. 361.42 caused the system to loop and not load, actually using the Intel driver as it seems to work better with the Displaylink (more on that next)

**4. Occasionally WiFi** does not work - a reboot seems to fix that.

**5. TeamViewer** - I did "sudo dpkg --add-architecture i386" to get the i386 packages required and installed sudo dpkg -i teamviewer_11.0.57095_i386.deb. 

Had to run execute "sudo apt-get install -f" a few times to get all the required dependences loaded

**6. Installed Virtualbox**, virtualbox-5.0_5.0.18-106667~Ubuntu~xenial_amd64.deb

7. sudo gedit /etc/fstab - added these to the mount options: ,discard,noatime,nodiratime to reduce wear on the SSD.

[INDENT]/dev/mapper/ubuntu--gnome--vg-root /               ext4    errors=remount-ro,discard,noatime,nodiratime 0       1[/INDENT]

[INDENT]# /boot was on /dev/nvme0n1p2 during installation[/INDENT]
[INDENT]UUID=1642ea1f-1a2a-427c-9128-4f5375926083 /boot           ext2    defaults,discard,noatime,nodiratime        0       2[/INDENT]

**7. DisplayLink Dock **- this was pain. Followed these instructions: [https://github.com/AdnanHodzic/displaylink-debian](https://github.com/AdnanHodzic/displaylink-debian). I had to create my own xrandr files - used arandr to create the shell scripts. The trick I had to use was to plug in the USB 3 cable "**After"** the desktop is loaded, otherwise it will not work. Also Resume from Suspend does not reload the desktop, you have to reboot. Screen Lock is ok.

how to install arandr "sudo apt-get install arandr"

All Services in the Displaylink work. **However I expected the Displaylink to also charge my laptop - unfortunately that is not possible.** A type USB cannot deliver the required Watts to the laptop. So I have ordered another 130W power supply for use at the office. Apparently the Thunderbolt USB C socket will provide power - I have ordered 2 of these. However, at the moment they don't work properly either as the drivers are still under development and the Kernel is not ready yet (Linus has a Github project under development for Thunderbolt). Even the Windows guys cannot get it to work out of the box. Dell has promised to get it sorted.

systemctl status displaylink.service

&#9679; displaylink.service - DisplayLink Manager Service
   Loaded: loaded (/lib/systemd/system/displaylink.service; enabled; vendor preset: enabled)
   **[COLOR="#00FF00"]Active: active (running)[/COLOR]** since Sun 2016-04-24 08:15:08 AEST; 8h ago
  Process: 1287 ExecStartPre=/sbin/modprobe evdi (code=exited, status=0/SUCCESS)
 Main PID: 1294 (DisplayLinkMana)
    Tasks: 36 (limit: 512)
   CGroup: /system.slice/displaylink.service
           &#9492;&#9472;1294 /usr/lib/displaylink/DisplayLinkManager

Apr 24 08:15:08 xxxxxx-XPS-15-9550 systemd[1]: Starting DisplayLink Manager Service...
Apr 24 08:15:08 xxxxxx-XPS-15-9550 systemd[1]: Started DisplayLink Manager Service.

Here is the xrandr command to set my Dell as Primary

#!/bin/sh
xrandr --output VIRTUAL1 --off **--output eDP1 --mode 1920x1080 --pos 0x0 --rotate normal** --output DP1 --off --output HDMI2 --off --output HDMI1 --off **--output DVI-I-1 --primary --mode 2560x1440 --pos 1920x0 --rotate normal** --output DP2 --off

*xrandr*
Screen 0: minimum 8 x 8, current 4480 x 1440, maximum 32767 x 32767
**eDP1 connected 1920x1080+0+0 (normal left inverted right x axis y axis) 346mm x 194mm**
   1920x1080     59.93*+  59.93  
   1680x1050     59.95    59.88  
   1600x1024     60.17  
   1400x1050     59.98  
   1600x900      60.00  
   1280x1024     60.02  
   1440x900      59.89  
   1280x960      60.00  
   1368x768      60.00  
   1360x768      59.80    59.96  
   1152x864      60.00  
   1280x720      60.00  
   1024x768      60.00  
   1024x576      60.00  
   960x540       60.00  
   800x600       60.32    56.25  
   864x486       60.00  
   640x480       59.94  
   720x405       60.00  
   640x360       60.00  
DP1 disconnected (normal left inverted right x axis y axis)
DP2 disconnected (normal left inverted right x axis y axis)
HDMI1 disconnected (normal left inverted right x axis y axis)
HDMI2 disconnected (normal left inverted right x axis y axis)
VIRTUAL1 disconnected (normal left inverted right x axis y axis)

**DVI-I-1 connected primary 2560x1440+1920+0 597mm x 336mm**
   2560x1440     59.95*+
   1920x1200     59.88  
   1600x1200     60.00  
   1680x1050     59.95  
   1280x1024     75.02    60.02  
   1280x800      59.81  
   1152x864      75.00  
   1024x768      75.08    60.00  
   800x600       75.00    60.32  
   640x480       75.00    60.00  
   720x400       70.08  
  1680x1050 (0xcd) 146.250MHz -HSync +VSync
        h: width  1680 start 1784 end 1960 total 2240 skew    0 clock  65.29KHz
        v: height 1050 start 1053 end 1059 total 1089           clock  59.95Hz
  1280x1024 (0xd2) 108.000MHz +HSync +VSync
        h: width  1280 start 1328 end 1440 total 1688 skew    0 clock  63.98KHz
        v: height 1024 start 1025 end 1028 total 1066           clock  60.02Hz
  1024x768 (0xda) 65.000MHz -HSync -VSync
        h: width  1024 start 1048 end 1184 total 1344 skew    0 clock  48.36KHz
        v: height  768 start  771 end  777 total  806           clock  60.00Hz
  800x600 (0xdd) 40.000MHz +HSync +VSync
        h: width   800 start  840 end  968 total 1056 skew    0 clock  37.88KHz
        v: height  600 start  601 end  605 total  628 

Here is the command to set the Laptop screen as Primary:

#!/bin/sh
xrandr --output VIRTUAL1 --off **--output eDP1 --primary --mode 1920x1080 --pos 0x0 --rotate normal** --output DP1 --off --output HDMI2 --off --output HDMI1 --off **--output DVI-I-1 --mode 2560x1440 --pos 1920x0 --rotate normal** --output DP2 --off

---

### Post by kylea on 2016-04-24
> **markdueck-bz said:**
> @loumray - I did the same a week ago, but now I'm having issues with my wireless and stand by not working.  It seems it was an update though because it stopped after a few reboots.  Hoping it will be fixed by coming updates.  

On a different topic, can someone tell me if the Thunderbolt ['firmware' update]("http://www.dell.com/support/home/us/en/19/Drivers/DriversDetails?driverId=GGDVY&fileId=3525384517&osCode=WT64A&productCode=xps-15-9550-laptop&languageCode=en&categoryId=DK") for windows is actually a hardware update, or is it just drivers?

Its a Firmware update - not hardware, apparently Linus is working on a kernel update

---

### Post by mhwong2007-a on 2016-04-25
> **kylea said:**
> **16.04 LTS release on XPS 15 9550 - 1920 x 1080 - FHD Screen - Non Touch**

I have completed a new install of 16.04 LTS release on a XPS 15 9550, 16GB with 512GB SSD.

Installed Ubuntu Gnome basically following the first post in this thread and a few others ([http://wiki.yobi.be/wiki/Laptop_Dell_XPS_15):](http://wiki.yobi.be/wiki/Laptop_Dell_XPS_15):)

I updated to Dell BIOS : via XPS_9550_1.2.0.exe

Screen - I do see occasional artifacts from the mouse

Issues Resolved:

**1. Bluetooth** - would not recognise any device - copied the driver BCM-0a5c-6410.hcd into  /lib/firmware/brcm, the file is available on the web, see here: [https://www.dropbox.com/s/8goc4omhnzxij93/BCM-0a5c-6410.hcd?dl=0](https://www.dropbox.com/s/8goc4omhnzxij93/BCM-0a5c-6410.hcd?dl=0)

**2. Bluetooth **headset would not work in A2DP mode - refer to [https://bugs.launchpad.net/ubuntu/+source/bluez/+bug/1438510](https://bugs.launchpad.net/ubuntu/+source/bluez/+bug/1438510), comment #5

**3. Used Nvidia **364.15 instead of 361.42. 361.42 caused the system to loop and not load, actually using the Intel driver as it seems to work better with the Displaylink (more on that next)

**4. Occasionally WiFi** does not work - a reboot seems to fix that.

**5. TeamViewer** - I did "sudo dpkg --add-architecture i386" to get the i386 packages required and installed sudo dpkg -i teamviewer_11.0.57095_i386.deb. 

Had to run execute "sudo apt-get install -f" a few times to get all the required dependences loaded

**6. Installed Virtualbox**, virtualbox-5.0_5.0.18-106667~Ubuntu~xenial_amd64.deb

7. sudo gedit /etc/fstab - added these to the mount options: ,discard,noatime,nodiratime to reduce wear on the SSD.
[INDENT]/dev/mapper/ubuntu--gnome--vg-root /               ext4    errors=remount-ro,discard,noatime,nodiratime 0       1[/INDENT]
[INDENT]# /boot was on /dev/nvme0n1p2 during installation[/INDENT]
[INDENT]UUID=1642ea1f-1a2a-427c-9128-4f5375926083 /boot           ext2    defaults,discard,noatime,nodiratime        0       2[/INDENT]

**7. DisplayLink Dock **- this was pain. Followed these instructions: [https://github.com/AdnanHodzic/displaylink-debian](https://github.com/AdnanHodzic/displaylink-debian). I had to create my own xrandr files - used arandr to create the shell scripts. The trick I had to use was to plug in the USB 3 cable "**After"** the desktop is loaded, otherwise it will not work. Also Resume from Suspend does not reload the desktop, you have to reboot. Screen Lock is ok.

how to install arandr "sudo apt-get install arandr"

All Services in the Displaylink work. **However I expected the Displaylink to also charge my laptop - unfortunately that is not possible.** A type USB cannot deliver the required Watts to the laptop. So I have ordered another 130W power supply for use at the office. Apparently the Thunderbolt USB C socket will provide power - I have ordered 2 of these. However, at the moment they don't work properly either as the drivers are still under development and the Kernel is not ready yet (Linus has a Github project under development for Thunderbolt). Even the Windows guys cannot get it to work out of the box. Dell has promised to get it sorted.

systemctl status displaylink.service

&#9679; displaylink.service - DisplayLink Manager Service
   Loaded: loaded (/lib/systemd/system/displaylink.service; enabled; vendor preset: enabled)
   **[COLOR=#00FF00]Active: active (running)[/COLOR]** since Sun 2016-04-24 08:15:08 AEST; 8h ago
  Process: 1287 ExecStartPre=/sbin/modprobe evdi (code=exited, status=0/SUCCESS)
 Main PID: 1294 (DisplayLinkMana)
    Tasks: 36 (limit: 512)
   CGroup: /system.slice/displaylink.service
           &#9492;&#9472;1294 /usr/lib/displaylink/DisplayLinkManager

Apr 24 08:15:08 xxxxxx-XPS-15-9550 systemd[1]: Starting DisplayLink Manager Service...
Apr 24 08:15:08 xxxxxx-XPS-15-9550 systemd[1]: Started DisplayLink Manager Service.

Here is the xrandr command to set my Dell as Primary

#!/bin/sh
xrandr --output VIRTUAL1 --off **--output eDP1 --mode 1920x1080 --pos 0x0 --rotate normal** --output DP1 --off --output HDMI2 --off --output HDMI1 --off **--output DVI-I-1 --primary --mode 2560x1440 --pos 1920x0 --rotate normal** --output DP2 --off

*xrandr*
Screen 0: minimum 8 x 8, current 4480 x 1440, maximum 32767 x 32767
**eDP1 connected 1920x1080+0+0 (normal left inverted right x axis y axis) 346mm x 194mm**
   1920x1080     59.93*+  59.93  
   1680x1050     59.95    59.88  
   1600x1024     60.17  
   1400x1050     59.98  
   1600x900      60.00  
   1280x1024     60.02  
   1440x900      59.89  
   1280x960      60.00  
   1368x768      60.00  
   1360x768      59.80    59.96  
   1152x864      60.00  
   1280x720      60.00  
   1024x768      60.00  
   1024x576      60.00  
   960x540       60.00  
   800x600       60.32    56.25  
   864x486       60.00  
   640x480       59.94  
   720x405       60.00  
   640x360       60.00  
DP1 disconnected (normal left inverted right x axis y axis)
DP2 disconnected (normal left inverted right x axis y axis)
HDMI1 disconnected (normal left inverted right x axis y axis)
HDMI2 disconnected (normal left inverted right x axis y axis)
VIRTUAL1 disconnected (normal left inverted right x axis y axis)

**DVI-I-1 connected primary 2560x1440+1920+0 597mm x 336mm**
   2560x1440     59.95*+
   1920x1200     59.88  
   1600x1200     60.00  
   1680x1050     59.95  
   1280x1024     75.02    60.02  
   1280x800      59.81  
   1152x864      75.00  
   1024x768      75.08    60.00  
   800x600       75.00    60.32  
   640x480       75.00    60.00  
   720x400       70.08  
  1680x1050 (0xcd) 146.250MHz -HSync +VSync
        h: width  1680 start 1784 end 1960 total 2240 skew    0 clock  65.29KHz
        v: height 1050 start 1053 end 1059 total 1089           clock  59.95Hz
  1280x1024 (0xd2) 108.000MHz +HSync +VSync
        h: width  1280 start 1328 end 1440 total 1688 skew    0 clock  63.98KHz
        v: height 1024 start 1025 end 1028 total 1066           clock  60.02Hz
  1024x768 (0xda) 65.000MHz -HSync -VSync
        h: width  1024 start 1048 end 1184 total 1344 skew    0 clock  48.36KHz
        v: height  768 start  771 end  777 total  806           clock  60.00Hz
  800x600 (0xdd) 40.000MHz +HSync +VSync
        h: width   800 start  840 end  968 total 1056 skew    0 clock  37.88KHz
        v: height  600 start  601 end  605 total  628 

Here is the command to set the Laptop screen as Primary:

#!/bin/sh
xrandr --output VIRTUAL1 --off **--output eDP1 --primary --mode 1920x1080 --pos 0x0 --rotate normal** --output DP1 --off --output HDMI2 --off --output HDMI1 --off **--output DVI-I-1 --mode 2560x1440 --pos 1920x0 --rotate normal** --output DP2 --off

I did a fresh install of Ubuntu Gnome 16.04 LTS on my XPS 9550 too!
However, whenever I restart my laptop, the bios seems can't find my hard drive. I had to shutdown my laptop completely and then power it on every time I need reboot. Did you experience this issue?

---

### Post by rvanderwerf on 2016-04-25
thanks. I see the same sometimes and put in in a script I run after login and it works.

also update on 3 monitors after a day it started crashing when it woke up the monitors. I installed nvidia-364 and all the video weirdness with multiple displays is gone.  I followed these steps: [http://askubuntu.com/questions/760934/graphics-issues-after-installing-ubuntu-16-04-with-nvidia-graphics](http://askubuntu.com/questions/760934/graphics-issues-after-installing-ubuntu-16-04-with-nvidia-graphics). They seem much faster and I'm not seeing artifacts while browsing in chrome.

---

### Post by ernstp on 2016-04-27
> **rvanderwerf said:**
> yep I am seeing the same. I couldn't even get to wifi on 4.4.8 but when I went back to 4.4.0 stock kernel it's working (but it makes weird popping noises in my external speakers)

update: I restarted 4.4.8 after 4.4.0-21 and wifi has been working ever since today. I've also got nvidia 368 working with 3 monitors (2 4k plus a 1200p) and it hasn't frozen all day after the lock screen kicked in. Every other kernel combo will freeze the system when you invoke the unlock screen after the system is idle.

So for me the magic combo is: 16.04 + 4.4.8 kernel (ubuntu version). So far I have the best of both worlds now between intel for low power usage while unplugged and nvidia + 3 monitors and performance when plugged in!

Wait which kernels are you referring to exactly?
What is 4.4.8 ubuntu version? Do you mean this guy: [http://kernel.ubuntu.com/~kernel-ppa/mainline/v4.4.8-wily/](http://kernel.ubuntu.com/~kernel-ppa/mainline/v4.4.8-wily/) ?
Or just linux-image-4.4.0-21-generic_4.4.0-21.37 ?
(Weird popping noise in you speaker is good because it means power save... )

---

### Post by Sam_Nazarko on 2016-04-27
Hi

I've recently got the XPS 15 9550 and it seems to run fine with 16.04 out of the box. However, sometimes the touchpad seems to lock up,where only holding down the click and moving the mouse works. This seems to happen if my palm accidentally swipes the touchpad, and it takes several swipes while holding down the button to unfreeze the mouse.

Is there a solution for this? I remember similar problems with my Samsung laptop some time ago and having to use a Xorg edgers PPA.

I am on the 4.4 LTS kernel and would prefer to stick with this if possible as I have numerous kernel modules registered with DKMS for hardware enablement and don't fancy patching them regularly..

---

### Post by slize_12 on 2016-05-04
Status update: On one of the earlier pages I posted that I had my Xubuntu 15.10 running with kernel 4.4.something.

Recently I was able to acquire a Dell Thunderbolt Dock TB15. As some of you already asked about it, here my brief status update:

System environment:
[LIST]
[*]Xubuntu 16.10
[*]4.4.0-21-generic #37-Ubuntu SMP Mon Apr 18 18:33:37 UTC 2016 x86_64 x86_64 x86_64
[/LIST]

[LIST]
[*]Dell Thunderbolt Dock TB15
[/LIST]

Note:
[LIST]
[*]Once I unboxed my TB15 I recognized the plug was not marked with the usual USB 3.1 logos but rather with a Thunderbolt logo. Reading the notes from I Dell I found out that they do not have USB 3.1 cables ready yet. They will be available at a later time and can be easily replaced at the side of the dock. This has nothing to do with the physical form of the cable (USB type C), just with the protocol they use for communicating.
[/LIST]

Status:
[LIST]
[*]Checking the new Thunderbolt dock with Xubuntu 15.10 did reveal that the two didn't like each other at all. (I don't particularly remember the kernel version I had installed). With Xubuntu 16.10 the dock is at least recognized when booting up (as previously outlined, it is best to have the dock plugged in before you boot up!)
[*]What works:
[LIST]
[*]Power supply
[*]Displays connectivity (partially, the EDID files seems get lost underway. I am currently running a 2560x1600 screen which is not even recognized to manage FullHD)
[*]Power button
[/LIST]

[*]What does not work:
[LIST]
[*]USB (front and back)
[*]Audio jack
[*]Ethernet
[*]Additional thunderbolt plug
[/LIST]
[/LIST]

Tweaks:
[LIST]
[*]As I used this screen earlier with HDMI already, I had to manually add the corresponding xrandr modes. So I knew there is an easy workaround for the missing / scrambled  EDID files. Currently I have the screen attached to the thunderbolt dock and using the following few lines to make it show the supposed resolution:
[LIST]
[*]```
xrandr --newmode "2560x1600_30.00"  164.25  2560 2696 2960 3360  1600 1603 1609 1630 -hsync +vsync
xrandr --addmode DP-1-2 "2560x1600_30.00"
xrandr --output DP-1-2 --mode "2560x1600_30.00" 
xrandr --output eDP-1 --off
```
[*]I did not manage to make the screen show 60 Hertz, even though its attached via display port. For now I stick to 30 Hertz
[/LIST]

[*]In order to find the mode you require use:
[LIST]
[*]```
cvt [Resolution X axis] [Resolution Y axis] [refresh]
```
[*]e.g.,```
cvt 2560 1600 30
```
[/LIST]
[/LIST]
Summary:
The TB15 saved me 2 plugs (power + hdmi). However, now I can't use my USB 3.1 ethernet adapter anymore. I need to stick to Wifi for the time being (which is considerably slower in my office environment :( ). I am really looking forward for better Kernel support of Thunderbolt 3 protocol in order to use all the advantages of the new TB dock.

---

### Post by markdueck-bz on 2016-05-07
<rant> This will be OT, but I'm tired of this whole machine.  They keyboard is crap if you're used to a lenovo, and the Touchpad keeps being recongnized as a PS2 touchpad, so no multi-touch is supported using touchegg. (a apple magic track-pad works perfectly) Now I watched a movie the other night and one of my speakers is blown.  This laptop has awesome specs, but terrible support for Linux and quality of the hardware is lacking.  Wish I could try a Lenovo Thinkpad P50 to compare, but here in Belize you can't just 'try' things and send them back.  </rant>

---

### Post by quickdry21 on 2016-05-07
Whelp, after 5 months of battling with this laptop, I have it working in (mostly) the configuration I wanted:

- Ubuntu Gnome 16.04 (standard kernel in the repositories: 4.4.0.22)
- nvidia GPU running all the time (it stays plugged in) w/ nvidia driver (361), nvidia prime
- dual external monitors (Dell U2414H, 1080p): USB-C -> DisplayPort, HDMI -> HDMI

A few caveats:

- Have to run the internal display at 1920x1080 with external displays plugged: I could not get xrandr to scale the resolution of external displays under nvidia proprietary drivers
- Using lightdm as the display manager: historically, with this laptop I have had much better luck using lightdm vs. the default for Ubuntu Gnome: gdm. I did not even try gdm this time around: when installing nvidia-361 from the graphics-drivers ppa, lightdm gets installed as a recommends and you are asked to choose lightdm or gdm (or whatever other display manager you have installed)
- It can take a few attempts to successfully log in: I frequently get hard lock ups after logging in as gnome shell starts up. This only seems to happen when starting a new session; unlocking an existing session does not seem to experience the same issue.

Running on the nvidia gpu with nvidia prime makes a **night and day** difference for tearing, desktop responsiveness and general usability of the OS. It kind of sucks that I have to drop the resolution of the internal display down but it is ***so*** worth it. 

I was actually about to give this laptop up to a Windows using co-worker due to the overall flakiness when running with external monitors when I decided to try one last-ditch effort to get the nvidia gpu working. Needless to say, said co-worker is now disappointed.

---

### Post by slize_12 on 2016-05-08
Update on the Thunderbolt Dock:

I risked installing the lastest kernel and by now EDID files seem to be parsed correct! I got my 2560x1600 running on 60 Hertz again (connected via Displayport). It's a real relief! 

```
Linux workstation 4.6.0-040600rc6-generic #201605012031 SMP Mon May 2 00:33:26 UTC 2016 x86_64 x86_64 x86_64 GNU/Linux
```

All the other stuff is not working yet (ethernet, USB, additional thunderbolt plug)

> **slize_12 said:**
> Status update: On one of the earlier pages I posted that I had my Xubuntu 15.10 running with kernel 4.4.something.

Recently I was able to acquire a Dell Thunderbolt Dock TB15. As some of you already asked about it, here my brief status update:

System environment:
[LIST]
[*]Xubuntu 16.10
[*]4.4.0-21-generic #37-Ubuntu SMP Mon Apr 18 18:33:37 UTC 2016 x86_64 x86_64 x86_64
[/LIST]

[LIST]
[*]Dell Thunderbolt Dock TB15
[/LIST]

Note:
[LIST]
[*]Once I unboxed my TB15 I recognized the plug was not marked with the usual USB 3.1 logos but rather with a Thunderbolt logo. Reading the notes from I Dell I found out that they do not have USB 3.1 cables ready yet. They will be available at a later time and can be easily replaced at the side of the dock. This has nothing to do with the physical form of the cable (USB type C), just with the protocol they use for communicating.
[/LIST]

Status:
[LIST]
[*]Checking the new Thunderbolt dock with Xubuntu 15.10 did reveal that the two didn't like each other at all. (I don't particularly remember the kernel version I had installed). With Xubuntu 16.10 the dock is at least recognized when booting up (as previously outlined, it is best to have the dock plugged in before you boot up!)
[*]What works:
[LIST]
[*]Power supply
[*]Displays connectivity (partially, the EDID files seems get lost underway. I am currently running a 2560x1600 screen which is not even recognized to manage FullHD)
[*]Power button
[/LIST]

[*]What does not work:
[LIST]
[*]USB (front and back)
[*]Audio jack
[*]Ethernet
[*]Additional thunderbolt plug
[/LIST]
[/LIST]

Tweaks:
[LIST]
[*]As I used this screen earlier with HDMI already, I had to manually add the corresponding xrandr modes. So I knew there is an easy workaround for the missing / scrambled  EDID files. Currently I have the screen attached to the thunderbolt dock and using the following few lines to make it show the supposed resolution:
[LIST]
[*]```
xrandr --newmode "2560x1600_30.00"  164.25  2560 2696 2960 3360  1600 1603 1609 1630 -hsync +vsync
xrandr --addmode DP-1-2 "2560x1600_30.00"
xrandr --output DP-1-2 --mode "2560x1600_30.00" 
xrandr --output eDP-1 --off
```
[*]I did not manage to make the screen show 60 Hertz, even though its attached via display port. For now I stick to 30 Hertz
[/LIST]

[*]In order to find the mode you require use:
[LIST]
[*]```
cvt [Resolution X axis] [Resolution Y axis] [refresh]
```
[*]e.g.,```
cvt 2560 1600 30
```
[/LIST]
[/LIST]
Summary:
The TB15 saved me 2 plugs (power + hdmi). However, now I can't use my USB 3.1 ethernet adapter anymore. I need to stick to Wifi for the time being (which is considerably slower in my office environment :( ). I am really looking forward for better Kernel support of Thunderbolt 3 protocol in order to use all the advantages of the new TB dock.

---

### Post by gaijin03 on 2016-05-09
I've been a long time consumer of this thread. Thanks for everyone's input. I thought I would share my experience with 16.04.

With the latest KUbuntu 16.04, latest bios and drivers I can now get 2560x1600 @ 60Hertz through the TB Dock (with slight tinkering through Display Configuration in System Settings). Previously I could only get 30 Hertz. This is using the intel driver. nvidia361 doesn't work for me -- at least with the dock. Display has a hard time coming back after unplugging and plugging back in the dock (might have something to do with suspending as well). However, things seem to be working better out of the box with 16.04.

HTH

---

### Post by kylea on 2016-05-10
> **mhwong2007-a said:**
> I did a fresh install of Ubuntu Gnome 16.04 LTS on my XPS 9550 too!
However, whenever I restart my laptop, the bios seems can't find my hard drive. I had to shutdown my laptop completely and then power it on every time I need reboot. Did you experience this issue?

No I did not.

Also I am testing 4.6-RC6 with a WD15 Dell Dock (USB-C) - that mostly works too - other than for the rear audio Jack.

---

### Post by alberink-stampfini on 2016-05-10
> **kylea said:**
> No I did not.

Also I am testing 4.6-RC6 with a WD15 Dell Dock (USB-C) - that mostly works too - other than for the rear audio Jack.

Can you tell me if the ethernet port is working? I'm still on the fence with this one. I need a dock at work, but USB-C/TB3 has been reported as flaky. Is the laptop charging over USB? Also, does hotplugging work? As in: connecting the dock after having booted to Linux?

Thanks for your reply

---

### Post by kylea on 2016-05-10
Yes network works,  and it charges,  however the BIOS reports 95watts instead of 130 WATTS.  Hot seems to plugging work. Note RC6 works,  RC7 did not

---

### Post by kylea on 2016-05-12
Just an update - for some unknown reason RC6 stopped working properly so I tried RC7 again - and that is working ok.

---

### Post by rvanderwerf on 2016-05-26
> **ernstp said:**
> Wait which kernels are you referring to exactly?
What is 4.4.8 ubuntu version? Do you mean this guy: [http://kernel.ubuntu.com/~kernel-ppa/mainline/v4.4.8-wily/](http://kernel.ubuntu.com/~kernel-ppa/mainline/v4.4.8-wily/) ?
Or just linux-image-4.4.0-21-generic_4.4.0-21.37 ?
(Weird popping noise in you speaker is good because it means power save... )

yes this guy [http://kernel.ubuntu.com/~kernel-ppa...e/v4.4.8-wily/](http://kernel.ubuntu.com/~kernel-ppa...e/v4.4.8-wily/) ?

---

### Post by rvanderwerf on 2016-05-26
Try the 364 nvidia drivers. All of my problems went away with multi displays (I am using internal screen at 4k, external usbc->displayport 4k, and a 1200p via hdmi at once. The difference in the drivers was night and day. Also set the external monitors not to go to sleep when plugged in that helps too.

> **quickdry21 said:**
> Whelp, after 5 months of battling with this laptop, I have it working in (mostly) the configuration I wanted:

- Ubuntu Gnome 16.04 (standard kernel in the repositories: 4.4.0.22)
- nvidia GPU running all the time (it stays plugged in) w/ nvidia driver (361), nvidia prime
- dual external monitors (Dell U2414H, 1080p): USB-C -> DisplayPort, HDMI -> HDMI

A few caveats:

- Have to run the internal display at 1920x1080 with external displays plugged: I could not get xrandr to scale the resolution of external displays under nvidia proprietary drivers
- Using lightdm as the display manager: historically, with this laptop I have had much better luck using lightdm vs. the default for Ubuntu Gnome: gdm. I did not even try gdm this time around: when installing nvidia-361 from the graphics-drivers ppa, lightdm gets installed as a recommends and you are asked to choose lightdm or gdm (or whatever other display manager you have installed)
- It can take a few attempts to successfully log in: I frequently get hard lock ups after logging in as gnome shell starts up. This only seems to happen when starting a new session; unlocking an existing session does not seem to experience the same issue.

Running on the nvidia gpu with nvidia prime makes a **night and day** difference for tearing, desktop responsiveness and general usability of the OS. It kind of sucks that I have to drop the resolution of the internal display down but it is ***so*** worth it. 

I was actually about to give this laptop up to a Windows using co-worker due to the overall flakiness when running with external monitors when I decided to try one last-ditch effort to get the nvidia gpu working. Needless to say, said co-worker is now disappointed.

---

### Post by vantuzilla on 2016-06-01
On my dell 9550 problem
Some sites at work places the page will flash or flicker occurs only on certain pages where a lot of content, and only in Google Chrome

Disable all plug-ins, I went incognito, even reinstalled the program

if you disable hardware acceleration, the flicker disappears, but the page still works a little bad,
if the switch to the Nvidia graphics card, then everything works fine

Update Driver Intel and Nvidia
I tried to update the kernel to 4.4.8 and 4.6.0 will still remain a problem

Could this be a hardware problem in the video card Intel 530?

ubuntu 16.04

---

### Post by kylea on 2016-06-01
> **vantuzilla said:**
> On my dell 9550 problem
Some sites at work places the page will flash or flicker occurs only on certain pages where a lot of content, and only in Google Chrome

Disable all plug-ins, I went incognito, even reinstalled the program

if you disable hardware acceleration, the flicker disappears, but the page still works a little bad,
if the switch to the Nvidia graphics card, then everything works fine

Update Driver Intel and Nvidia
I tried to update the kernel to 4.4.8 and 4.6.0 will still remain a problem

Could this be a hardware problem in the video card Intel 530?

ubuntu 16.04

> **vantuzilla said:**
> 
[I]
Could this be a hardware problem in the video card Intel 530?[/I]

Maybe - however I had a heap of problems getting 4.6 to work - right now I boot the PC without the dock plugged in and then after I login successfully I plug in the USB C cable.

---

### Post by leepe on 2016-06-02
Hi everyone--

Been using ubuntu on this machine for a while now and am looking to make some battery optimizations. My current idle power usage is 16W (measured using powertop) , and it goes up to 20-30 under light load. What are everybody else's numbers, and any ideas as to how I can reduce power usage? I already have tlp running in laptop mode, and have put pm-powersave in powersaving mode as well using ```
sudo pm-powersave true
``` Beyond this extremely basic tuning, I'm stumped as to what processes I can kill off to reduce power usage. I've read some forum posts online with people claiming 6-8 watts idle with only these basic powersaving measures, and while a 4k panel surely won't allow for power consumption that low, I'm hoping to get closer...

---

### Post by bertusrex on 2016-06-05
> **leepe said:**
> Hi everyone--

Been using ubuntu on this machine for a while now and am looking to make some battery optimizations. My current idle power usage is 16W (measured using powertop) , and it goes up to 20-30 under light load. What are everybody else's numbers, and any ideas as to how I can reduce power usage? I already have tlp running in laptop mode, and have put pm-powersave in powersaving mode as well using ```
sudo pm-powersave true
``` Beyond this extremely basic tuning, I'm stumped as to what processes I can kill off to reduce power usage. I've read some forum posts online with people claiming 6-8 watts idle with only these basic powersaving measures, and while a 4k panel surely won't allow for power consumption that low, I'm hoping to get closer...

1) turn of nvidia card: enable intel graphics (e.g. with prime-indicator), then switch off nvidia card with a script like below (sorry, very crude):

```
#!/bin/bash
sudo rmmod nvidia_uvm
sudo rmmod nvidia_drm
sudo rmmod nvidia_modeset
sudo rmmod nvidia
echo OFF | sudo tee /proc/acpi/bbswitch

```

2) run this to set all/most tunable power saving items to 'good' in one go: 

```
sudo powertop --auto-tune

```
then reset individual items that cause trouble when powersaving  afterwards (like bluetooth mouse or external keyboard stuttering).
Start powertop, move to 'tunables' tab with tab key then cursor up/down to select the problem item, enter to change state to 'bad' (which in this case is actually pretty good). 

```
sudo powertop

```

example:
```

PowerTOP 2.8      Overview   Idle stats   Frequency stats   Device stats   Tunables                    


>> Bad           Autosuspend for USB device BCM920703 Bluetooth 4.1 [Broadcom Corp]
   Good          NMI watchdog should be turned off                                                     
   Good          VM writeback timeout
   Good          Enable SATA link power management for host0
   Good          Enable SATA link power management for host1
   Good          Enable Audio codec power management

```

---

### Post by leepe on 2016-06-05
> **bertusrex said:**
> 1) turn of nvidia card: enable intel graphics (e.g. with prime-indicator), then switch off nvidia card with a script like below (sorry, very crude):

```
#!/bin/bash
sudo rmmod nvidia_uvm
sudo rmmod nvidia_drm
sudo rmmod nvidia_modeset
sudo rmmod nvidia
echo OFF | sudo tee /proc/acpi/bbswitch

```

2) run this to set all/most tunable power saving items to 'good' in one go: 

```
sudo powertop --auto-tune

```
then reset individual items that cause trouble when powersaving  afterwards (like bluetooth mouse or external keyboard stuttering).
Start powertop, move to 'tunables' tab with tab key then cursor up/down to select the problem item, enter to change state to 'bad' (which in this case is actually pretty good). 

```
sudo powertop

```

example:
```

PowerTOP 2.8      Overview   Idle stats   Frequency stats   Device stats   Tunables                    


>> Bad           Autosuspend for USB device BCM920703 Bluetooth 4.1 [Broadcom Corp]
   Good          NMI watchdog should be turned off                                                     
   Good          VM writeback timeout
   Good          Enable SATA link power management for host0
   Good          Enable SATA link power management for host1
   Good          Enable Audio codec power management

```

Thanks for the tips; I noticed however than under a medium/light load (watching 4k on youtube) and in other scenarios like even just sitting idle or word processing, the nvidia GPU draws less power than the intel one. Watching 4K, using ```
sudo powerstat
``` to measure the average power drawn from battery over 10 mins shows that using Intel graphics the system draws 37W avg, but with nvidia it only uses 31W avg. Idle, using Intel the system draws 16W-ish and using Nvidia it only draws 10-ish. Am I missing something?
I did also use powertop previously, but now I'm avoiding using the --auto-tune option because it tunes the touchscreen to a powersaving mode that make it very difficult to interact with; it turns the touch sensors off after around 10s of non-use, and it takes multiple touches afterwards to wake it up again.

 What wattage numbers are you getting?

---

### Post by bertusrex on 2016-06-06
> **leepe said:**
> Thanks for the tips; I noticed however than under a medium/light load (watching 4k on youtube) and in other scenarios like even just sitting idle or word processing, the nvidia GPU draws less power than the intel one. Watching 4K, using ```
sudo powerstat
``` to measure the average power drawn from battery over 10 mins shows that using Intel graphics the system draws 37W avg, but with nvidia it only uses 31W avg.


The scenario I was targetting was light use with maximum battery  (reading, typing, browsing), watching 4K is at the other end of energy  consumption spectrum, nvidia may actually be better there. Running on nvidia is ok when idle, but it ramps up power consumption  quickly even after simple actions like scrolling a webpage, and remains  at high consumption for some time after that before ramping down again.

> **leepe said:**
> Idle, using Intel the system draws 16W-ish and using Nvidia it only draws 10-ish. Am I missing something?


Did you actually try to the disable nvidia with script from previous post? Should bring the 16W idle on Intel down quite a bit. 

> **leepe said:**
>  I did also use powertop previously, but now I'm avoiding using the --auto-tune option because it tunes the touchscreen to a powersaving mode that make it very difficult to interact with; it turns the touch sensors off after around 10s of non-use, and it takes multiple touches afterwards to wake it up again.
What wattage numbers are you getting?

For light use I get around 6-8W with intel+nvidia off+powertop --auto-tune

re. powertop --auto-tune: as I mentioned in the previous post, you can turn powersaving off for problematic individual items, so you can keep the rest of the system optimized while still enjoying your touchscreen.

---

### Post by artur20 on 2016-06-13
Hello all,

I've spent a while reading this thread after be kindly pointed towards here for my graphics issues. I am running Ubuntu 16.04 on a Dell Precission 5510 which has a very simliar hardware setup. Just for reference, I created this a few days ago in my desperate attempt to get everything working: [http://ubuntuforums.org/showthread.php?t=2327162&p=13500945#post13500945](http://ubuntuforums.org/showthread.php?t=2327162&p=13500945#post13500945)

All in all, I am still seeing flickering when I enable NVIDIA. I am not sure what else to try. So far I have been trying: 

* NVIDIA drivers (361, 364, 367)
* Gnome and Unity
* Using lightdm 
* changing xserver configs
* Some other things .. 

I am still seeing two main issues with my system which is: 

1. flickering/tearing when enabling nvidia, most notably when scrolling websites, typing in the terminal, watching videos 

2. When locking the system it hard freezes and I can't do anything anymore. I have the same log output as here: [http://superuser.com/questions/1080678/ubuntu-16-04-laptop-hanging-requires-powercycle](http://superuser.com/questions/1080678/ubuntu-16-04-laptop-hanging-requires-powercycle) However I am up to date with my BIOS. 

I'm hoping someone might have an answer or more recommendations. I hope I haven't overlooked an existing answer here, if so please point me to it :)

---

### Post by Jan_Drewes on 2016-06-14
[
Hi Artur,

When I was using Kernel 4.4xxx from Kubuntu 16.04, I remember my nvidia working normally although I never really tested it thoroughly as I have no use for it. I am currently running on linux 4.6.2 from [http://kernel.ubuntu.com/~kernel-ppa/mainline/v4.6.2-yakkety/ ]("http://kernel.ubuntu.com/~kernel-ppa/mainline/v4.6.2-yakkety/")and I have purged all nvidia and nouveau and I am just using bbswitch to turn the nvidia chip off at boot time. This way I have a reliable and smoothly tuned workstation, and it also saves battery. The current official ubuntu-nvidia packages don't dkms-compile with the 4.6x kernels. If one day I get some free minutes, I might try to use the edgers-ppa or another source to see how far I can get with 4.6.x and nvidia, but for now I am content and happy with intel-only (if the machine had been available without the nvidia chip, I would have bought it that way).

PS, with 4.6.2 USB-C/Thunderbolt hot plugging now works for me, at least with the included LAN adapter, as well as entering airplane mode with the special key (Fn+PrtScr) which is also good for power saving.

Cheers,
Jan

---

### Post by bertusrex on 2016-06-14
Like Jan, I'm currently using kernel 4.6.2. Flickering (whole screen going black briefly) should be gone with this kernel, but there's currently no solution to tearing as far as I know, except to use Intel graphics. 

"When prime is enabled, there is currently no synchronization between the  source device producing the pixels and the sink device reading them.   I.e., in a typical NVIDIA + Intel configuration, the Intel chip just  scans out the shared buffer constantly, without regard to when the  pixels are copied into it."

[link]("https://devtalk.nvidia.com/default/topic/775691/vsync-issue-nvidia-prime-ux32vd-with-gt620-m-/") to older issue, but still valid I think.

---

### Post by alberink-stampfini on 2016-06-15
> **bertusrex said:**
> Like Jan, I'm currently using kernel 4.6.2. Flickering (whole screen going black briefly) should be gone with this kernel, but there's currently no solution to tearing as far as I know, except to use Intel graphics. 


Unfortunately, with the USB-C dock I still get flickering after a while. A disconnect and reconnect of the dock fixes this, but alas it is still an issue. This is running the 4.6.2 kernel on the Intel chip. 

Disconnect and reconnect of USB-C seems to work better, but not always. Sometimes, I loose connectivity to the Ethernet port, at least in NetworkManager. I should try and pinpoint if the kernel looses track of it as well.

---

### Post by bertusrex on 2016-06-15
Ah, didn't know you were using a dock, I have no experience with USB-C docks.

---

### Post by vantuzilla on 2016-06-20
In general, those who have problems with flickering screen in google chrome helps if you add a shortcut to run the program the following commands  
[COLOR=#000000][FONT=sans-serif]--disable-gpu-driver-bug-[/FONT][/COLOR][COLOR=#000000][FONT=sans-serif]workarounds --enable-native-gpu-memory-[/FONT][/COLOR][COLOR=#000000][FONT=sans-serif]buffers[/FONT][/COLOR]

---

### Post by morhook on 2016-06-21
@Cowlike About 5, I've added the touchegg command to my $HOME/.xprofile startup file and I'm able to use three-finger and four-finger gestures on Unity (I suspect with Gnome the result will be the same). Good luck!

---

### Post by sergio62 on 2016-06-23
> **Jan_Drewes said:**
> [
Hi Artur,

When I was using Kernel 4.4xxx from Kubuntu 16.04, I remember my nvidia working normally although I never really tested it thoroughly as I have no use for it. I am currently running on linux 4.6.2 from [http://kernel.ubuntu.com/~kernel-ppa/mainline/v4.6.2-yakkety/ ]("http://kernel.ubuntu.com/~kernel-ppa/mainline/v4.6.2-yakkety/")and I have purged all nvidia and nouveau and I am just using bbswitch to turn the nvidia chip off at boot time. This way I have a reliable and smoothly tuned workstation, and it also saves battery. The current official ubuntu-nvidia packages don't dkms-compile with the 4.6x kernels. If one day I get some free minutes, I might try to use the edgers-ppa or another source to see how far I can get with 4.6.x and nvidia, but for now I am content and happy with intel-only (if the machine had been available without the nvidia chip, I would have bought it that way).

PS, with 4.6.2 USB-C/Thunderbolt hot plugging now works for me, at least with the included LAN adapter, as well as entering airplane mode with the special key (Fn+PrtScr) which is also good for power saving.

Cheers,
Jan

Hi, do you have an external monitor working ok with that usb-c dock, kernel 4.6.2 and intel driver?
Have you test with the hdmi output port?
If not, what dock are you using? Maybe I have to buy one for be able to use my external monitor.

Here with 4.4.24 does not work, intel or nvidia drivers 364 (and others)

Thank you in advanced

---

### Post by alberink-stampfini on 2016-06-24
> **sergio62 said:**
> Hi, do you have an external monitor working ok with that usb-c dock, kernel 4.6.2 and intel driver?
Have you test with the hdmi output port?
If not, what dock are you using? Maybe I have to buy one for be able to use my external monitor.

Here with 4.4.24 does not work, intel or nvidia drivers 364 (and others)

Thank you in advanced

Ik have that exact configuration. I have the Dell USB-C dock attached over USB-C, an external monitor connected via DisplayPort running on Kernel 4.6.2 using the Intel driver. So far, so good. I get infrequent blinking of the external display, which is a nuisance, but a disconnect and reconnect fixes that. I have found out that my windows dual-boot has the same problem, so this may not be linux's fault. All in all I'm fairly happy.

On kernel 4.6.2 I do have issues with audio-switching, specifically to the headset port. Switching to external audio on the dock is no problem, I sometimes have to toggle between internal and dock audio manually, but that works. However, when I plug in my headphones all audio becomes silent, and will remain so. I do hope the 4.7 kernel will fix that issue for me.

---

### Post by sergio62 on 2016-06-24
> **alberink-stampfini said:**
> Ik have that exact configuration. I have the Dell USB-C dock attached over USB-C, an external monitor connected via DisplayPort running on Kernel 4.6.2 using the Intel driver. So far, so good. I get infrequent blinking of the external display, which is a nuisance, but a disconnect and reconnect fixes that. I have found out that my windows dual-boot has the same problem, so this may not be linux's fault. All in all I'm fairly happy.

On kernel 4.6.2 I do have issues with audio-switching, specifically to the headset port. Switching to external audio on the dock is no problem, I sometimes have to toggle between internal and dock audio manually, but that works. However, when I plug in my headphones all audio becomes silent, and will remain so. I do hope the 4.7 kernel will fix that issue for me.

Thank you for your response.

Finally, I achieved to use external HDMI with intel driver. 
For extend the desktop to the secondary monitor, I use "xrandr", but the graphics have less quality. For use only the secondary screen as primary, I disable the notebook screen and works fine.

---

### Post by zafu on 2016-07-09
Hi,

I've had this laptop for a few months now and appreciate the precious info in this thread for setting it up.

The system is now running debian testing/unstable.

A peculiar problem I'm having with this machine is memory exhaustion. Regardless of  kernel version (even 4.7-rc4) RAM usage creeps up over three days to fill the 16G available. htop and other tools show no obvious culprit. I'm running lightdm and openbox with mostly xterms and a firefox instance (shutting it down changes nothing). From there it's mostly game over as the machine slows to a crawl while the oom-killer does its thing. I have to reboot. Restarting X is of now help either.

Has anyone had this issue yet?

I have other setups with less RAM and lower specs that behave impeccably running the same apps (namely a Lenovo yoga2).

Thanks for any insight,

---

### Post by alberink-stampfini on 2016-07-20
Looking at the screenshot, I see that the first 5 or so commands require an awfull lot of virtual memory (1.4Gig per process). Are you sure you aren't looking at your culprits right there?
Other that that, I don't know. I have the same kernel and memory setup and I don't experience any issues.

---

### Post by astroman3001gt on 2016-07-20
Hi guys,

So everything was working almost perfectly, however today after an update and restart I lost the grub boot menu.

In the boot sequence I have the option for "[COLOR=#000000]\EFI\ubuntu\shimx64.efi" but still I cannot load grub. Did this happen to some of you before? Any ideas to fix this?
[/COLOR]

---

### Post by astroman3001gt on 2016-07-20
A quick fix. I changed the option in boot sequence from [COLOR=#000000]"[/COLOR][COLOR=#000000][COLOR=#000000]\EFI\ubuntu\shimx64.efi" to [/COLOR][/COLOR][COLOR=#000000]"[/COLOR][COLOR=#000000]\EFI\ubuntu\[/COLOR][COLOR=#000000][FONT=&quot]grubx64.efi"...

Still I am curious, anyone had the same problem?

[/FONT][/COLOR]

---

### Post by artur20 on 2016-07-29
> **Jan_Drewes said:**
> [
Hi Artur,

When I was using Kernel 4.4xxx from Kubuntu 16.04, I remember my nvidia working normally although I never really tested it thoroughly as I have no use for it. I am currently running on linux 4.6.2 from [http://kernel.ubuntu.com/~kernel-ppa/mainline/v4.6.2-yakkety/ ]("http://kernel.ubuntu.com/~kernel-ppa/mainline/v4.6.2-yakkety/")and I have purged all nvidia and nouveau and I am just using bbswitch to turn the nvidia chip off at boot time. This way I have a reliable and smoothly tuned workstation, and it also saves battery. The current official ubuntu-nvidia packages don't dkms-compile with the 4.6x kernels. If one day I get some free minutes, I might try to use the edgers-ppa or another source to see how far I can get with 4.6.x and nvidia, but for now I am content and happy with intel-only (if the machine had been available without the nvidia chip, I would have bought it that way).

PS, with 4.6.2 USB-C/Thunderbolt hot plugging now works for me, at least with the included LAN adapter, as well as entering airplane mode with the special key (Fn+PrtScr) which is also good for power saving.

Cheers,
Jan

Hi,

I am still running 4.4.0-31 as kernel now. When I talked on #ubuntu I was strongly advised to not manually upgrade the kernel which is why i haven't done that so far. 

I am using graphics-drivers-ubuntu-ppa-xenial.list as repository to get the drivers. I also did purge everything and reinstall it, however so far no luck (neither with 364 or 367 of the nvidia dirvers). I read on the nvidia page that optimus is simply not supported. 

However, on my laptop with Ubuntu 16.04 everything worked out of the box (hot plugging hdmi/usb c, no random freezes anymore). I did have to disable sleeping since the laptop required a hard-cycle when waking up (sometimes, not easily reproducible). I found some info on that and I believe this may be fixed. Since I don't really require the laptop to sleep I haven't properly tested this yet. 

You mentioned that you turn the NVIDIA chip off on startup - isn't that admitting defeat ;) You have a box with this great chip inside that you just can't use. I use nvidia-prime to set the laptop to power-safe-mode and this also produces a reliable system. I just don't accept Dell selling this laptop as Ubuntu laptop (that is the Precission 5510) with hardware that can't be used with ubuntu.

Thanks! 

Artur

---

### Post by Jan_Drewes on 2016-08-02
I just wanted to report a few issues I have recently run into. 

1) BIOS version 1.2.10 appears to have problems. With it, the backlight control essentially stops working after suspend/resume: you can still regulate many steps, but the screen really always stays at full brightness or completely zero brightness, depending on the setting. It seems to be unpredictable whether backlight after supsend will be on or off.

2) Kernel 4.7 from [http://kernel.ubuntu.com/~kernel-ppa/mainline/v4.7/](http://kernel.ubuntu.com/~kernel-ppa/mainline/v4.7/) is currently missing the dell_wmi and dell_laptop modules among others, causing lack of functionality (obviously). Apparently, this was a misconfiguration of the kernel build and is about to be fixed (I talked to someone in the ubuntu kernel IRC)

Ultimately, kernel 4.6.5 with BIOS 1.2.0 runs fine for me, suspend, hotkeys, backlight and all.

@artur20: I admitted defeat when I bought the machine with the power-wasting badly-supported proprietary-driver-needing nvidia chip installed. However, being able to just switch it off and forget about it feels like a minimal victory ;-)

I now also own a USB-C to VGA cable ([https://www.amazon.it/Adattatore-Alluminio-Trasferimento-Chromebook-Dispositivi/dp/B01DUCTKYQ/ref=sr_1_4?ie=UTF8&qid=1470175295&sr=8-4&keywords=usb+c+vga](https://www.amazon.it/Adattatore-Alluminio-Trasferimento-Chromebook-Dispositivi/dp/B01DUCTKYQ/ref=sr_1_4?ie=UTF8&qid=1470175295&sr=8-4&keywords=usb+c+vga)) which works as expected: it uses USBC-video, rather than being a USB-VGA-graphicscard-in-a-cable (it does not add another graphics card to the system). Under Kubuntu, however, plugging it in can cause the same problems as plugging in a HDMI cable - I sometimes have to try more than once before it works. When plugging it in before the Plasma session starts, everything is fine though. So, it might be a Plasma issue rather than a Linux/kernel issue.

Cheers

---

### Post by artur20 on 2016-08-03
> **Jan_Drewes said:**
> 
@artur20: I admitted defeat when I bought the machine with the power-wasting badly-supported proprietary-driver-needing nvidia chip installed. However, being able to just switch it off and forget about it feels like a minimal victory ;-)


Hi! 

you are right - it is better than nothing. And for my purposes of writing code and watching Netflix, that is completely fine. I am upset mainly because dell has a big fat screenshot on their website running ubuntu on this exact laptop. And I consider that false advertising since the Optimus chip just doesn't work. 

Having said that, I am thinking of nuking it again (after holiday), then go from scratch with 16.04 and try a later kernel. Or try a later kernel without erasing everything and hope for the best :) 
The issue is really that I tried so many things that I am not sure in which state I am in at this point. It might be a good choice to start from scratch. 

When I talked in #ubuntu though I was strongly advised not to manually update the kernel  to a later version. There is lack in support for the later kernels, is what they said. I have a bit of experience with ubuntu, though I have never installed new kernels. Might be an interesting experiment. 

I also found a different thread where someone with the equal Intel + Nvidia combo apparently made it work. The same config that worked for him though does not do anything for me. 

Thanks!

artur

---

### Post by seubri on 2016-08-18
Hi guys,

Thank all of you (in particular Jchedstrom) for helping with this thread.

I have an issue that I am hoping maybe I can get help with here.

I am using Ubuntu 16.04 on a laptop Dell XPS 15 9550. Current kernel is 4.4.0-34. Display resolution is 3840x2160. I am using nvidia prime and currently the nvidia driver 370, but I select "Intel" in the prime-indicator by default. I don't know what other information is relevant, please feel free to ask.

My system is mostly working but there are a few issues:
- Sometimes (most times) Ubuntu takes a long while to shut down, don't know why.
- Sometimes when I edit a text file (say in gedit text editor), my system "doesn't like it", it seems to be lagging for no reason.
- Some programs often crash (Firefox for instance)
- Sometimes I get error messages "System program error detected".

None of these problems are so frustrating that I really tried to do something about it. But recently I starting working again on a Qt/C++ project using Qt Creator, and Qt Creator crashes all the time, making it unusable. Here is what happens: as soon as I start editing a file such as main.cpp in Qt Creator, it crashes. If I run it from the terminal with strace, all I can read is:
[FONT=arial]--- SIGSEGV {si_signo=SIGSEGV, si_code=SI_KERNEL, si_addr=0} ---[/FONT]
[FONT=arial]+++ killed by SIGSEGV (core dumped) +++[/FONT]
[FONT=arial]Segmentation fault (core dumped)

At first I thought something may be wrong with my Qt Creator, but now I think the fault is on Ubuntu (I have tried several versions of Qt Creator, several install methods, all produce the same effect). Although I have no clue what is going on, I suspect maybe the problem is related to the graphics driver? As well as my other issues described above?

If you could help me with this, it'd be great.

Brice[/FONT]

---

### Post by eastingandnorthing on 2016-08-31
Hello,

New to this thread, and I assume having a FHD instead of UHD with 8GB ram doesn't really matter :)

I'm using Ubuntu 16.04 with kernel 4.7.0-040700-generic, having some trouble with my nvidia/optimus deal.

I've had nvidia-prime together with prime-indicator working when I first set it up...


So, A few days ago I've installed kernel 4.7. after doing this, I noticed that prime-indicator was showing the nvidia symbol, but actually using Intel graphics. Switching using nvidia-settings wasn't working either.


So, I decided to use bumblebee instead. Removed and purged nvidia* etc. Installed bumblebee like described here. Later, I also tried this method.


In both cases, optirun/primusrun tell me 'Could not load GPU driver'. So, I went to Bumblebee troubleshooting, and it seems like my nvidia .ko files are not present. (bumblebeed: Module 'nvidia' is not found.)


troubleshooting: "Then ensure that you the module is built."


How does one build these kernel modules?

Also: I've tried using dkms autoinstall for my nvidia drivers, this was its output:


```
Building module:
cleaning build area....
'make' -j8 NV_EXCLUDE_BUILD_MODULES='' KERNEL_UNAME=4.7.0-040700-generic IGNORE_XEN_PRESENCE=1 IGNORE_CC_MISMATCH=1 SYSSRC=/lib/modules/4.7.0-040700-generic/build LD=/usr/bin/ld.bfd modules.....(bad exit status: 2)
ERROR (dkms apport): kernel package linux-headers-4.7.0-040700-generic is not supported

Error! Bad return status for module build on kernel: 4.7.0-040700-generic (x86_64)



```

So, is the 4.7 kernel not supported by dkms?

Anyone having the same issues?

---

### Post by eastingandnorthing on 2016-08-31
Haha, so, I managed to fix it myself.

Check out my askubuntu thread:

[http://askubuntu.com/questions/819015/bumblebee-build-kernel-module/819219#819219](http://askubuntu.com/questions/819015/bumblebee-build-kernel-module/819219#819219)

---

### Post by ptsneves on 2016-09-21
Hey there. I finally got my XP15 UHD running at 11~13 Watts with Primus in 4.4.0-38. I followed the steps in this blog:

[http://www.webupd8.org/2016/08/how-to-install-and-configure-bumblebee.html](http://www.webupd8.org/2016/08/how-to-install-and-configure-bumblebee.html)

I also needed to create some aliases in /etc/modprobe.d/bumblebee.conf like the following:

```
alias nvidia-drm nvidia_370_drm
alias nvidia-uvm nvidia_370_uvm
alias nvidia-modeset nvidia_370_modeset
```

A very specific problem which I had with bumblebee, was that I mapped a static address to the loopback which caused the connection of bumblebee to X to not succeed.


Hope it is of use.

---

### Post by ptsneves on 2016-10-08
Another thing which I solved today is the bluetooth support. A firmware blob was required and the [bug is here]("https://bugs.launchpad.net/ubuntu/+source/bluez/+bug/1589889") and the firmware is [here]("https://bugs.launchpad.net/ubuntu/+source/bluez/+bug/1589889/+attachment/4683974/+files/BCM-0a5c-6410.hcd").

Just copy it to /lib/firmware/brcm with sudo and that's all. I think there are other posts about this subject but as this a central post about the XPS15 and my goto post I post here for reference.
[URL="https://bugs.launchpad.net/ubuntu/+source/bluez/+bug/1589889/+attachment/4683974/+files/BCM-0a5c-6410.hcd"]
[/URL]

---

### Post by 7ql6 on 2017-01-01
I reinstalled my system with Ubuntu 16.10. but now I'm not able to get nvidia prime working again. I purged and reinstalled all nvidia related things a few times already but I get none of the proprietary drivers (367, 370, 375) to work.
Switching to proprietary driver always results in a black screen. Anything I may have missed or any log file where I could look for hints?

---

### Post by jhouse2 on 2017-01-17
Does anyone know how to install bios updates without having windows bootable?

---

### Post by tobros91 on 2017-01-20
> **jhouse2 said:**
> Does anyone know how to install bios updates without having windows bootable?


Download the exe file and copy it to /boot/efi/ Then you restart your computer and press f12 during boot and select bios flash upgrade. 

```
sudo cp Downloads/XPS_9550_1.2.18.exe /boot/efi/
```

---

### Post by amit272 on 2017-01-22
Hi guys! I also have a Dell XPS 15 9550 

Can somebody help me with that:
[http://askubuntu.com/questions/874951/coolers-noise-at-dell-xps-15-9550-without-heavy-loading](http://askubuntu.com/questions/874951/coolers-noise-at-dell-xps-15-9550-without-heavy-loading)


Dell Support refuses to help, motivated it with this "We regret to inform, Ubuntu being an open source OS, our support is limited. As far as we are aware, there are no specialized distros for XPS 15.  "

---

### Post by Jan_Drewes on 2017-01-23
I'm using bumblebee/optirun and it works for me. Kubuntu 16.10, included nvidia-drivers (not from ppa), latest intel drivers (but the included ones worked too). I am running a Precision 5510 with nvidia quadro graphics, but that shouldn't make a difference.

---

### Post by Jan_Drewes on 2017-01-23
I had some fan issues on 16.04 as well. You may want to try to upgrade to 16.10 which includes a newer (="better") kernel, no more fan noise here. Also, which BIOS version are you running?

---

### Post by amit272 on 2017-01-23
> **Jan_Drewes said:**
> I had some fan issues on 16.04 as well. You may want to try to upgrade to 16.10 which includes a newer (="better") kernel, no more fan noise here. Also, which BIOS version are you running?

I'm not alone...

Bios version is 1.2.14

Update kernel at my 16.04 to 4.8.0 as at 16.10 version, but noise is still here. I think I'll try to update the distro version, not only kernel. Hope it will helps


UPD: Updated BIOS to 1.2.18 and Kernel to 4.8.0 at this moment use system for 5 minutes and no noise. Hope it will continue

UPD2: Noise returned. Will install Ubuntu 16.10

---

### Post by amit272 on 2017-01-23
> **Jan_Drewes said:**
> I had some fan issues on 16.04 as well. You may want to try to upgrade to 16.10 which includes a newer (="better") kernel, no more fan noise here. Also, which BIOS version are you running?

Tell me please Jan, do you have only Ubuntu on your machine or Windows also? I'm still have problems with fan noise at 16.10, may be it cause I have Dual Boot alongside Windows?

---

### Post by saroele on 2017-02-09
I have installed Ubuntu 16.04 in dual boot with windows 10 on my new dell xps15 9560 (4K touch display). One of the issues that I find very annoying is the (almost) constant fan noise.  I upgraded to 16.10  as suggested in this thread but that did not seem to solve anything.  However, as of writing this post, the fan suddenly stopped for the first time, but now it restarted with cpu temperatures around 48°C (measured with psensor).

I don't know what the expected fan noise should be for cpu temperatures around 50°C ?   How can i see the fan speed in order to do better logging of the relation between fan noise and cpu temperatures?

---

### Post by Jan_Drewes on 2017-02-11
saroele: I am running Ubuntu only, but I used to have windows on the machine as well, no changes back then. 
at 50C you should indeed have some fan noise. When doing programming, word processing and other low-demand tasks I am running around 35-40C, with fans mostly off. So the question would be why is your laptop running warmer?
-Did you install something like tlp (or laptop-mode-tools) to enhance powersaving? I am running tlp.
-Are you using the nvidia chip? I turn mine off by default (via bumblebee/bbswitch), otherwise you may have several watts extra consumption, which also heats your laptop up.
-You may check your power consumption (while on battery) with powertop. How many watts do you get for a resting desktop? With just-a-little-less than 50% brightness, I get around 13W.
Hope any of this helps...

---

### Post by saroele on 2017-02-13
Hi Jan,

your message definitely helps.  I think the basic issue is in fact that my power consumption is way too high. With screen brightness to the lowest value, powertop reports something like 26W.  I ran ```
sudo powertop --auto-tune
``` and that reduced the consumption to about 23W.    Would it make sense to post a html report from powertop here? 

I still have to figure out which graphic card is being used.  I read that NVIDIA can increase the power consumption by 10W compared to the built in graphic chip, so that's the first thing to check. 

As for the fan noise: i have been able to install i8kutils after forcing the load of kernel module with  ```
sudo modprobe i8k force=1
```
Now the** fan works in cyclic bursts**, and I think this is the same issue as reported here: [https://bugs.launchpad.net/i8kutils/+bug/410596](https://bugs.launchpad.net/i8kutils/+bug/410596)  In short, the i8kmon fan setting is quickly overturned by the bios and that leads to cycles of fan operation of a few seconds.  I had started a separate thread for that: [https://ubuntuforums.org/showthread.php?t=2352237](https://ubuntuforums.org/showthread.php?t=2352237)  I did not yet try the solution proposed there.  Did anyone else try it on a 9550 or 9560?

As of writing this message, I found another culprit for power consumption: I'm using a DA-200 adaptor with external monitor connected (VGA) and ethernet.  The adapter gets very hot, also the surface of the laptop left of my keyboard is very hot now.  Is this normal?
EDIT: I disconnected the DA-200, switched back on the wifi and after about 15 minutes, the power consumption automatically dropped to about 12W (with lowest screen brightness).  What a difference, and also the hot temperatures of the laptop surface left of my keyboard, right above the thunderbolt port, are gone.

---

### Post by Jan_Drewes on 2017-02-13
Hi saroele,

hm, I have the DA-200 too, but I use it rarely (arrived only last week). However, I have an external USB Harddisk (3.5", self-powered), and when I connect it to the USB-C port, that part of the laptop gets warm too (warm = uses power). If I connect it to the old-style USB port right next to the USB-C port, nothing warms up. I didn't check that with powertop yet. Thunderbolt in Linux appears to be buggy still - maybe a newer kernel will help here, but I'm gonna wait for the next (K)ubuntu release I think. (Yes, I think it's the thunderbolt part, not the USB part, because when I plug a USB device into the USB-C port, something happens on the PCI-E bus according to syslog. Also, I can connect the HDD only once - the next time it can't be mounted anymore, until I reboot)

You didn't mention if you have TLP installed - if not, I recommend that you do, it can help a lot.

Regarding your fan: IMHO, given your CPU temperature, your fan *IS SUPPOSED TO RUN*, so you shouldn't try to use i8kutils or any other fan control software to turn it off - your machine might overheat and get damaged.

---

### Post by tobros91 on 2017-02-15
Using this laptop for about 4 months now, had random mouse freezes and buggy screen on the USB-c output. 

Bios 1.2.18, kernel 4.9.10 and nvidia 375.39 finally seems to have fixed it. No mouse issues and both my external monitors works fine. (so far this morning... :))

Virtualbox broke going from 4.8 -> 4.9 tho. Got same issue going from 4.4 -> 4.8



[B]Update

[/B]Mouse freezes is back...

---

### Post by f(fanta) on 2017-03-10
As per your point 1 "The PCIe hard drive won't be recognized by live Ubuntu 15.10 by default.", consider installing Ubuntu server instead, as it should detect RAID 0. You can then add the desktop/unity later.

Thank you for your report!

---

### Post by sergio.leone on 2017-06-12
Hi All,

Just installed Ubuntu 16.04 on my XPS 15 9550 (4K). Could anyone tell me which tutorial should I follow for post-installation (drivers update, etc.) as many of them seem out of date and some are controversial (i.e. someone suggests using bumblebee, another person suggests nvidia-prime, etc.). Sorry for dumb question, this is my first Ubuntu experience outside of using it a bit on a VM.

---

