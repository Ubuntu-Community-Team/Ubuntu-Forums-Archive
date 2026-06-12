---
title: "Installed, activated nvidia drivers, but ubuntu still uses onboard card."
date: 2014-02-03
forum: Hardware
---

### Post by chaves.dennis on 2014-02-03
I apologize if something like this has already been posted. I've been searching around but haven't found any solutions. Let me walk you through my process so far.

I've got a machine running windows. 
Motherboard is a: Asus P8Z770V LK. 
Graphics card is: EVGA/Nvidia GeForce GTX 550 Ti which I was using with two monitors.

 I've been using ubuntu on my laptop for a year, I really like it, so I decided to dual-boot on this desktop machine. The graphics card was not playing nice with the installer, I couldn't get anywhere because I just a bunch of jumbled squares of colors on the screen. So this is what I've done to work around it:

[LIST]
[*]Disconnected graphics card, plugged main monitor into onboard video. 
[*]ran Ubuntu 12.04 installer, checked box to install third-party and proprietary drivers etc. 
[*]Installation goes fine. 
[*]Boot into ubuntu and download all updates. 
[*]downloaded and installed nvidia drivers by [following instructions on this post]("http://news.softpedia.com/news/How-to-Install-The-Latest-Nvidia-Driver-on-Ubuntu-12-04-295542.shtml"). 
[*]Shut down machine. 
[*]re-connect Nvidia card to motherboard. Hook-up monitors to video card. 
[*]Reboot. 
[*]Nothing shows up on screen, just blinking "_" but I did hear the ubuntu bongo start-up sound, so... 
[*]without rebooting, I disconnected a monitor and hooked it up to the onboard video. 
[*]Now I see the login screen. Ubuntu is still using the onboard video. 
[*]Opened system settings > additional drivers 
[*]Find that "NVIDIA accelerated graphics driver (post-release updates) (version 331-updates)" is not activated. So I activate and restart. 
[*]At this point I'm not sure what will be working, so I have one monitor in the NVIDIA card, and one monitor on the onboard card. 
[*]Upon reboot, video is still coming out of the onboard card. On that monitor I see my desktop. On the other monitor, hooked up to the card, I'm seeing a blinking "_" 
[/LIST]

When I go to display settings, it only detects the one monitor connected to the on-board card. And that's where I stand now... Help?

---

### Post by oldfred on 2014-02-03
I have not downloaded the nVidia drivers directly from nVidia or a ppa for many years. Back then it sometimes totally corrupted system and reinstall was only fix.
But you should only use the nVidia driver from the Ubuntu repository unless you have an extremely new video card and want the latest updates. Ubuntu is much better now at adding newer nVidia drivers to repository, so they are not as old as they used to be compared to most recent issued by nVidia.

And if you are using nVidia from any other place than repository you must reconfigure after every kernel update. That is automatic if from repository.

I always have to use nomodeset to boot installer and first boot after install. Then I install nVidia driver from repository using command line or System Settings.
If booting with Intel different boot parameters are usually required.

I would remove ppa and totally houseclean that nVidia.
Then install new nVidia drive from repository. 

       # only reason to purge is there are several versions, if you know you have different nVidia use that:
#To see available versions:
dpkg -l | grep -i nvidia*
#see details for version installed
sudo apt-cache policy nvidia*
sudo apt-cache policy nvidia-319-updates 

   sudo apt-cache search nvidia-sett*
# Houseclean out all old versions to avoid issues
sudo apt-get remove --purge < nvidiadriverpackagename>
# [ using the correct names] for each driver, before running:
sudo apt-get purge nvidia*
sudo mv /etc/X11/xorg.conf /etc/X11/xorg.conf.backup

   # Install version you prefer
# I used nvidia-current-updates & nvidia-settings-updates, example below is just nvidia-current
sudo apt-get install nvidia-current
sudo apt-get install nvidia-settings
sudo dpkg-reconfigure nvidia-current
sudo nvidia-xconfig
sudo reboot
May want nvidia-current, nvidia-current-updates or nvidia-current-experimental-XXX for most recent testing version.
apt-cache search nvidia-sett* 
nvidia-settings-experimental-310

   stop & restart
sudo service lightdm stop
sudo dpkg-reconfigure nvidia-current

I normally use System Settings now.
But these were from my history with one install, I think newest version is a lot different now.

 1995  sudo apt-get remove --purge nvidia*
 1996  apt-cache search nvidia
 1997  sudo apt-get install nvidia-319-updates
 1998  sudo reboot

---

### Post by chaves.dennis on 2014-02-04
Thanks very much for you reply oldfred! Pardon me for being a big ol newbie in this situation. I just want to make sure I understand your post and what each command is doing before I go and make more changes to my system.




```
dpkg-l | grep -i nvidia*
```
To see available versions of nvidia drivers.

```

sudo apt-cache policy nvidia*
sudo apt-cache policy nvidia-319-updates

```
These two are to see details of drivers I currently have installed? Is it necessary to run both of these lines?

```
sudo apt-cache search nvidia-sett*
```
This another command to find driver details?

```
sudo apt-get remove --purge <nvidiadriverpackagename>
```
replace <nvidiadriverpackagename> with a package I've found from using the previous 4 commands. And repeat with every nvidia package. This would be the housecleaning operation, correct?

```

sudo apt-get purge nvidia*
sudo mv /etc/X11/xorg.conf /etc/X11/xorg.conf.backup

```
Run these after I'm done purging all those packages in the previous step. The second one makes me nervous - are you sure I should be renaming that file, not copying it?

```

sudo apt-get install nvidia-current
sudo apt-get install nvidia-settings
sudo dpkg-reconfigure nvidia-current
sudo nvidia-xconfig
sudo reboot

```
Now these are installing and configuring drivers, and reboot.

```

sudo service lightdm stop
sudo dpkg-reconfigure nvidia-current

```
Stop lightdm service, reconfigure drivers?

These at the end confused me not sure if I'm supposed to run these commands after all the stuff above:
```

1995 sudo apt-get remove --purge nvidia*
1996 apt-cache search nvidia
1997 sudo apt-get install nvidia-319-updates
1998 sudo reboot 

```

Then, i'm guessing at this point, I should be done and the card should be working and both my monitors should be displaying my desktop. So, I should run all these commands, in the order shown? Or would I be ok just running the four commands at the end of your post?

Thanks for the help again, I just want to clarify what I should be doing.

---

### Post by LinuXXuniL on 2014-02-04
Have you tryed to install the nvidia driver from "Software & Updates" --> "Aditional Drivers" and select the driver that you want to use?

Is there a BIOS option to stop using the CPU graphic chip?

---

### Post by oldfred on 2014-02-04
I believe you have it correct.

Reinstall should recreate new xorg. At one time they wanted to totally do away with xorg file. But often needed with special configurations. You also mentioned two monitors. I think some of configuration is automatic, but you may have to manually review xorg to make sure each monitor is configured correctly.

The last 4 commands.
I just showed the summary commands I did. I skipped some of the details to see what was installed or what was available to install as I had check that much earlier or I knew what I had installed. I have not installed from ppa ever and not directly from nVidia for at least 5 years as it always seems to have some issues. But my video card is older so I have not needed the bleeding edge drivers either.

I have only one monitor but saved these links.
 ARandR Screen Layout Editor 0.1.4 - Dual screens
[http://christian.amsuess.com/tools/arandr/](http://christian.amsuess.com/tools/arandr/)
Dual nVidia cards - 2013
[http://ubuntuforums.org/showthread.php?t=2129190](http://ubuntuforums.org/showthread.php?t=2129190)
Three Monitors - nVidia
[http://ubuntuforums.org/showthread.php?t=1999966](http://ubuntuforums.org/showthread.php?t=1999966)

---

### Post by chaves.dennis on 2014-02-05
Alright, so I ran all those commands but the situation remains the same. I'll boot with my monitor plugged into the card and the bios screen shows up, grub shows up, but when I boot into Ubuntu I don't get anything except for two lines about some USB error. Then I hear the bongos, letting me know I'm at the login screen. Plug the monitor into the onboard card... Sure enough, it's still using the onboard video.

---

### Post by oldfred on 2014-02-05
Is your UEFI/BIOS set to boot with Intel?
Some are automatic and others have manual settings.

But now you are into all the issue Linus had his rant against nVidia about or dual video.
And I do not know anything about dual video, but most find bumblebee works.

 Updates to nVidia Prime with 14.04 (only)
[http://www.phoronix.com/scan.php?page=news_item&px=MTU0MDI](http://www.phoronix.com/scan.php?page=news_item&px=MTU0MDI)
Newest nVidia Prime with 13.10 testing may run hot, but option to bumblebee
[http://www.webupd8.org/2013/08/using-nvidia-graphics-drivers-with.html](http://www.webupd8.org/2013/08/using-nvidia-graphics-drivers-with.html)
[https://wiki.ubuntu.com/X/Config/HybridGraphics](https://wiki.ubuntu.com/X/Config/HybridGraphics)
nVidia Optimus and Ubuntu explained 
[http://ubuntuforums.org/showthread.php?t=1657660](http://ubuntuforums.org/showthread.php?t=1657660)
Bumblebee:
[https://wiki.ubuntu.com/Bumblebee](https://wiki.ubuntu.com/Bumblebee)
[http://www.webupd8.org/2013/04/set-up-bumblebee-with-bumblebee.html](http://www.webupd8.org/2013/04/set-up-bumblebee-with-bumblebee.html)
[http://askubuntu.com/questions/348614/bumblebee-on-ubuntu-13-04-with-geforce-750m-and-driver-319](http://askubuntu.com/questions/348614/bumblebee-on-ubuntu-13-04-with-geforce-750m-and-driver-319)
12.10 with bumblebee
[http://ubuntuforums.org/showthread.php?t=2077451](http://ubuntuforums.org/showthread.php?t=2077451)

---

### Post by chaves.dennis on 2014-02-06
I don't know oldfred. I don't know. I think I'm just goint to admit defeat at this point. Maybe in a few years when my graphics card is old and useless ubuntu will finally have a working driver for it.

Since my last post, I thought doing a clean install might be worth a shot. So I ran the installer again WITH the graphics card connected this time, and with both monitors on it. The installer actually ran, which I felt was promising since I didn't get that far before. So I ran the installer, had it download all the extra packages and drivers and what not. Installation seemed to proceed fine until it came time to reboot.

Rebooted and I got a black screen with a dialog window informing me the system was in low-graphics mode. Clicked okay and was presented a list of options one of which was to exit to a command line. I chose that, figure I might be able to run nvidia-xconfig or something. But I couldn't actually input any commands. So I rebooted. I stopped in the BIOS (which is UEFI by the way.) because of the question you just asked and searched around for anything graphics related. I found a parameter called "primary display" which had the options: Auto, iGPU, PCIe or PCI. It was set to auto. Since the graphics card is PCI, I switched to to PCI. This time I got the same window, but no mouse and no keyboard, so I wasn't able to click okay. So I hit the reboot again. This time I got nothing but black. Reboot once more and now it boots normally but using the on-board card.

At that point, I was in the normal Unity GUI, I headed over to the additional drivers in system preferences. There's 2 nvidia drivers in there, I activated one "nvidia_311," and rebooted. Same deal, on-board graphics only. I activated the other driver "nvidia_311_updates," and rebooted. Same deal. So here I am now. Back at square one.

And here's what really grinds my gears. How is it possible, that the live USB demo of Ubuntu runs on my graphics card, with both monitors, without issue. Yet only once it's installed, the problems come up? Doesn't make sense to me.

So I think I will just give up here. Clearly this card just doesn't have the proper support for linux yet. Which surprises me because this card is not new, bleeding-edge tech. It's at least 3 years old. So I'm just going to stop here and keep windows 7 on this machine. I will probably just remove it from this machine eventually.

Save for the wireless card being finicky, Ubuntu works perfectly on my laptop. So for now that's where my Ubuntu will stay.

Possibly in the future I may upgrade to [one of these cards]("https://wiki.ubuntu.com/HardwareSupportComponentsVideoCardsNvidia") or some other hardware documented as supported.

Again, thanks so much for the help. I just don't have the time to deal with this right now.

---

### Post by LinuXXuniL on 2014-02-06
Hey, don't give up so easly :D. I am using an nVidia Matrix GTX 580 and things are working perfect in Ubuntu 13.10 but the thing in my case is that I don't have an Intel CPU with graphics on it. I'm not using dual monitor setup, but sometimes I connect my TV to my GTX and things are working fine. I'm using nVidia proprietary 319 drivers, installed from "Software and Updates -> Additional drivers", because the Ubuntu nouveau driver is blocking my computer.
In your case I guess the problem derives from BIOS settings. There in the Graphic section you should select PCIE as primary video card and disable iGPU Multi Monitor. This will help you in windows as well, cause you'll loose a lot of heat generated by the CPU when processing video data in games and video demanding application (whatching Bluray's, encoding videos, etc). 
On the other hand there may be a speciffic way to disable the onboard integrated graphics for your motherboard (a jumper or another BIOS setting) and it will be a wise thing to ask people in Asus Forum.

Please let me know if you solve this problem because I intend to change my rig with a new one that has integrated graphics and is goot to know how things will work :D.

---

