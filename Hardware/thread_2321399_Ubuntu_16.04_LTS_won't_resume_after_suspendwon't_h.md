---
title: "Ubuntu 16.04 LTS won't resume after suspend/won't hybernate/log off"
date: 2016-04-22
forum: Hardware
---

### Post by redguy41 on 2016-04-22
There used to be a workaround with enabling suspending and hibernation, which worked for me at 14.04 LTS, but having cleanly installed 16.04 LTS I lost that, and now my computer won't come back from suspend.

I tried the tutorial listed here: [http://ubuntuhandbook.org/index.php/2014/04/enable-hibernate-ubuntu-14-04/](http://ubuntuhandbook.org/index.php/2014/04/enable-hibernate-ubuntu-14-04/) to enable hibernation but running

sudo pm-hibernate

Leaves me with black screen and processor running, I cannot restore the system, I can only manually shut it down and run again.

Yet my SWAP is bigger than my RAM (8.5 GB).

So I cannot hibernate nor suspend (the latter I can, but the computer doesn't wake up until restarted).

Please help?

Using Lenovo z50-71, i5 laptop with ATI /Intel hybrid graphics.

---

### Post by dFlyer on 2016-04-22
There is a suspend problem with 16.04. I've had a problem with suspend on my laptop with the suspend with lid closed. It will continue to run until the time set for it to suspend. It doesn't suspend on lid close only on suspend on when in-active time. My work around has been selecting suspend before I close the lid. I've had many issues with this release. Non major, but still I'm surprised they release it with this many bugs. My computer is an HP Pavilion g series. I've not tried hibernate so have no comment.

---

### Post by redguy41 on 2016-04-23
OK thanks for the insight. Do you plan to do any workarounds? Since I'm pretty much inexperienced with bugs and their patches, does the Ubuntu team solve this through updates, i.e. when can we expect a solution?

---

### Post by wanderer3 on 2016-04-23
> **dFlyer said:**
> There is a suspend problem with 16.04. I've had a problem with suspend on my laptop with the suspend with lid closed. It will continue to run until the time set for it to suspend. It doesn't suspend on lid close only on suspend on when in-active time. My work around has been selecting suspend before I close the lid. I've had many issues with this release. Non major, but still I'm surprised they release it with this many bugs. My computer is an HP Pavilion g series. I've not tried hibernate so have no comment.

I've been a user since the first Ubuntu release in 05. 16.04 is showing me no compelling reasons to upgrade from 14.04 at this time after having tried the liveCD. Have never seen so little apparent difference between distros as in the last few years. By that I mean functional differences  -  am aware of the under the hood stuff like systemd, snap, Python 3.5 ( and likely broken library dependencies ), ZFS etc. but what a yawn. They look and feel the same.

---

### Post by nls on 2016-04-23
I also have a problem with hibernation. 16.04 is the first desktop Ubuntu I'm planning to use permanently on my Lenovo G560 laptop. Hibernation used to work just fine in Windows 7, but whatever tricks I try I find on the net looking for solutions, nothing seems to work. It's pretty annoying since I can only choose between my battery depleted using standby or complete restart if I want to keep my workspace. Pretty much a repelling factor and makes me want to go back to Windows.

---

### Post by leonardo-pmascarenhas on 2016-04-26
Same here guys, I'm using a dell inspiron

---

### Post by pblanton on 2016-05-03
I have the same issue. I tried letting the PC (Desktop PC, Core I7 on a Gigabyte board. NOT a laptop) suspend after setting the timeout to 5 minutes and waiting. After it suspended, I pressed a key on the keyboard and the box hummed back to life, but the monitors never woke up. Their lights stayed yellow. I finally had to hard-reboot.

Then I tried "sudo pm-hibernate" at the terminal and it hibernated fine. When I pushed the power button, it sprung back to life and the monitors woke up fine. This time though the wifi adapter (TP-Link TL-WN851ND) wouldn't reconnect to the network. When I tried to reconnect, the wifi icon pulsed for about a minute, then I got a message that I have been disconnected from the network.

[IMG]http://i.imgur.com/gcGdTc7.png[/IMG]

Then I restarted the PC and the wifi worked again

[IMG]http://i.imgur.com/REEh5Cy.png[/IMG]

I have the same issue with suspend as I do with hibernate. 

I tried using my USB Alfa AWUS036NHA, but with it I get a message that my wifi has been disabled with a hardware switch. rfkill unblock all doesn't work to fix that. i have to do a hard-reboot in order to get the wifi interface back up. 

I'm bailing on 16.04 and going back to 15.10 because it works. It appears that 16.04 has shipped with a ton of problems. It is irresponsible to ship an LTS product with this many problems. I may bail on Ubuntu altogether and go back to Open Suse. I actually need my computer to work and having to troubleshoot a ton of new problems with old, standard hardware and functionality is unacceptable.

---

### Post by marin-purgar on 2016-05-05
I am also (sometimes) unable to reconnect to the wireless network after waking up from suspend but only when laptop is on battery (Lenovo G50-70).

My solution in this case is:

[FONT=courier new]$ sudo rfkill block all
$ sudo rfkill unblock all
$ iwlist wlan0 scan
[/FONT]
After the iwlist scan the wireless networks reconnects automatically.

Bye, Marin

---

### Post by mickeypop on 2016-05-07
marin-purgar your solution is easily automated
though mine was the monitor not turning on

put this bash script in your /etc/pm/sleep.d folder
with a name like 15_wifiup  NOTE the XX_ is needed where the XX is the highest number in the folder to insure it runs last 

NOTE check the paths to rfkill and iwlist, these are usually the path but some distros may move them

once in place every time you come out of suspend it will run 

#!/bin/bash

case "$1" in
    suspend | hibernate)
        # executed on suspend
        ;;
    resume | thaw) 
        # executed on resume
        /usr/sbin/rfkill block all
        /usr/sbin/rfkill unblock all
        /sbin/iwlist wlan0 scan
       ;;
    *)
        ;;
esac

---

### Post by mbrandt74 on 2016-06-18
THANK YOU for your Expert Opinion. I'm bailing back too. This is not ready yet.

---

### Post by blueh2o2 on 2016-08-28
If you have encrypted swap, you will not be able to resume unless you disable it or set a fixed key.

---

### Post by mattdt on 2016-09-04
Same issue here. I did a clean install of 16.04 only to find that the first 5 min. with no activity it put my monitor into suspend mode, since apparently the installed default power saving setting is 5 min. Then I discovered moving the mouse, hitting a keyboard key, or even a brief touch of the power button would not wake the monitor. Since I couldn't see the monitor with it suspended, I thought possibly the system was nevertheless waiting for a password to unlock and hopefully wake. Nope, that failed too. At that point I was forced to do a hard boot to recover. The only solution I have is to set the screen lock settings to never suspend and never lock, basically always on with no suspend. Then turn the monitor off from it's own power switch.

Hope there is a solution soon.

---

### Post by Goliath! on 2016-09-04
I have the same problem only worse. Ubuntu ignores my power settings. So if I set it to Don't suspend or suspend after 10 minutes, it makes no difference. After 5 minutes, the screen goes dark and I have no choice but hard reboot. This is truly awful.
Dell Inspiron 1501 (from the bronze age)
Ubuntu 16.04 LTS

---

### Post by Goliath! on 2016-09-06
I think my issue may have been hardware related. I unplugged my laptop and let it completely drain the battery. After I plugged it back in and restarted it, the issue went away.
Perhaps it may be time to buy a new laptop :(

---

### Post by thiago-taa on 2016-09-20
Same problem here, Desktop I3 w/ intel Graphics.
No workaround so far..?

---

### Post by victorcrimea on 2016-09-30
I experienced the same issue on my Dell XPS 15 9550. If I suspend the system, then upon the resume it hangs on the black screen with no any signs of life :( And need to force restart. Really annoyong thing.

---

### Post by JoeDaddy on 2016-11-14
This is what I discovered on two computers, one with Ubuntu 14.04 and  another with 16.04.  If there is a drive installed that is not enabled  in the CMOS settings OR if there is a drive or *device* missing  from the unit and it is enabled in the CMOS then Ubuntu will not recover  fully from suspend. I have no idea why this happens but both computers  would not recover.  One had a SATA drive installed and not enabled in  CMOS while the other had an optical device enabled that was not  installed.  Fixing the CMOS settings in both instances fixed the  problem.

---

### Post by supermohit on 2016-12-06
Found the solution on another forum. Please confirm if it works.
The problem is with two GPU's, Intel & nvidia. If nvdia is the default GPU, suspend and hibernate will have issues.


   Step1 : Run "nvidia-settings" on terminal.


   Step2 : In "PRIME Profiles" tab, select the GPU as "Intel" instead of "NVIDIA".


   Step3 : Save and restart your machine.




Lemme know if this solution works in Ubuntu 16.0.4. I tried this on 14.0.4 and it worked.

---

### Post by ardi2 on 2016-12-10
I have a desktop with GA Z170-HD3P mobo, and neither suspend nor hibernate work. I'm using NVIDIA proprietary drivers. The advice above about switching to Intel IGFX isn't an option for me (I need the NVIDIA GPU for my work).

I feel really disappointed about this. I've been out of Linux for almost a decade, and I thought the suspend/hibernate historical issues would be fixed, or would affect laptops only. Seeing that my desktop won't wake up from neither suspend nor hibernate is a serious drawback, because hibernate helps me a lot in my everyday work.

How much priority does this issue have? Is it likely to get fixed in 16.04 LTS, at least for desktops?

---

### Post by hpardoe on 2016-12-30
I'm having the same issue on my desktop machine, Intel Xeon processor

---

### Post by wildmanne39 on 2016-12-30
> **hpardoe said:**
> I'm having the same issue on my desktop machine, Intel Xeon processor

Hello, if you want help with this issue please start your own thread with a descriptive title in the appropriate sub-forum because you will be more likely to get the help you need.
Thanks

---

### Post by freshjos on 2017-01-02
Same problem, and solved installing netext73, launching app, check hibernate in the optimizer, reboot some times at least 2, resume is working now. 
solution based on [https://www.reddit.com/r/elementaryos/comments/382e76/how_to_fix_cannot_wake_up_from_suspend_issue/](https://www.reddit.com/r/elementaryos/comments/382e76/how_to_fix_cannot_wake_up_from_suspend_issue/)

---

### Post by mattdt on 2017-02-22
A workaround I've found that works is to download from the Ubuntu Software Repository the X11 Screen Saver, or possibly any other screen saver application. Within this screen saver you can independently set the screen to lock or go into standby mode independent of any default installed power and/or lock functions. Apparently the default Gnome install no longer includes the Gnome Screen Saver application so an outside screen saver is needed.

---

### Post by desiguy2447 on 2017-03-11
I just did an upgrade I had the same issue I could not resume from suspend or Hibernate. One thing I checked was booting into my Asus Bios after verify the clock and date in the bios were correct and saving changes I rebooted into Ubuntu 16.04 LTS and I notice on Boot I no longer got the error message of clearing orphaned Inode appearing line after line.

Once booted I suspended the computer and it worked still not convinced I let the machine sit idle for 10 minutes came back tapped on the wireless keyboard it came back to life. then tried again after 45 minutes and it worked

Not sure what was off in the Asus Bios but a quick boot into it and saving changes worked.

---

### Post by sasky84 on 2017-04-04
> **supermohit said:**
> 

   Step1 : Run "nvidia-settings" on terminal.
Step2 : In "PRIME Profiles" tab, select the GPU as "Intel" instead of "NVIDIA".
Step3 : Save and restart your machine.



worked for me! thanks!:D

---

### Post by florentins on 2017-12-20
I have spent several days to find a solution to the suspend/resume issue on Ubuntu (17.10) and Mint (18.3) which is based on Ubuntu 16.04. I'm using an Asus Vivobook Pro N752VX (i7-6700HQ)
These are the steps that seems to fix the suspend freeze / resume freeze or restart on Asus when using the Intel card and drivers (the nvidia driver causes screen tearing on my laptop):

* install the latest Intel drivers - i've used the Oibaf repo for this but you can probably use the Intel update tool from 01.org
     $ sudo add-apt-repository ppa:oibaf/graphics-drivers

* make sure intel-microcode is NOT installed (it comes installed on Ubuntu 17.10 by default)
     $ sudo apt-get purge intel-microcode

* use the latest possible kernel - i've installed 4.14.7 mainline kernel on both Mint 18.3 and Ubuntu 17.10

* (for Ubuntu 17.10) in order to avoid restarting after resume, you need to change the apm (advanced power management) settings before suspending:

create the file: /etc/pm/sleep.d/99_suspend 

case "$1" in
    suspend)
        # executed on suspend
        /etc/apm/event.d/20hdparm stop 

        ;;
    resume) 
        # executed on resume
        /etc/apm/event.d/20hdparm start
        ;;
    *)
        ;;
esac

make it executable
$ chmod +x /etc/pm/sleep.d/99_suspend

* for Mint 18, "tlp" is the advanced power management tool, use the following content and follow the same steps as described above:
case "$1" in
    suspend)
        # executed on suspend
        tlp ac 

        ;;
    resume) 
        # executed on resume
        tlp true
        ;;
    *)
        ;;
esac

---

### Post by sccman on 2017-12-20
Have you been able to solve your suspend problem? Whenever I have a problem with suspend and get a black screen I used this after reinstalling:

> ...[COLOR=#000000]install the updated "light-locker-settings" and "xfce4-power-manager" packages:[/COLOR][COLOR=#000000]Code:
```
sudo apt-get install light-locker-settings xfce4-power-manager
```[/COLOR]
[COLOR=#000000]Once you've got the latest packages installed, please restart your computer and perform the following test:[/COLOR]
[COLOR=#000000]Use light-locker-settings to toggle the setting.[/COLOR]
[COLOR=#000000]a) Disable "Lock on Suspend"[/COLOR]
[COLOR=#000000]b) Click "Apply"[/COLOR]
[COLOR=#000000]c) Enable "Lock on Suspend"[/COLOR]
[COLOR=#000000]d) Click "Apply"[/COLOR]

[COLOR=#000000]Once you have verified the fix, please leave a comment on the above bug.[/COLOR][COLOR=#000000]

[/COLOR][https://ubuntuforums.org/showthread.php?t=2220085](https://ubuntuforums.org/showthread.php?t=2220085)

---

