---
title: "Lucid Sleep/Hibernate Bug on a LOT of laptops"
date: 2010-05-22
forum: Hardware
---

### Post by saveryquinn on 2010-05-22
Dear Ubuntu.

This is not a flame.  It is a Dear John letter.

I have used Ubuntu on and off since forever ago.  Usually quite pleasantly, at first.  Then usually I get distro wanderlust and head off for another lover.  

This time, I came back to you for Lucid.  Our time together was so brief I can't even call it a fling.  You installed fine and felt familiar.  I wasn't sure about the whole interior design thing, kind of rearranged your living room with those window buttons on the left now.  But it was okay, I didn't mind.  And the purple?  Well, it was a change.  

But then I tried to close the lid and go to sleep with you and you really, really let me down.  My fan just kept running and that cute little moon kept flashing.  You left my screen all aglow.  

So that's it.  I'm leaving you.  I'm through.  These days, with laptops having a majority share of the market, there's just no excuse for a release with a show-stopping bug on my little Thinkpad.  And from hundreds of posts I've found on forums around the internet, it seems you're doing the same thing to Dell and Toshibas.  You obviously don't care for my feelings.

If you need me, I'll be at Debian's.

---

### Post by hufemj on 2010-05-27
I have the same problem on my Dell Latitude D600 with 10.04. Suspend worked fine on Karmic. Then I upgraded to Lucid and suspend stopped working. It's particularly annoying since my wife will pick up my laptop to check her email. When she's done she closes the lid. It's pointless to tell (okay, ask) not to. That would be a criticism. But, that's for another post.

Anyway, when I next find my laptop the fan the lid is closed, the fan is running like mad, and it's disturbingly warm. Opening the lid for resume doesn't work, probably because suspend didn't work in the first place.

Manual suspend doesn't work either. If I select suspend from the shutdown menu, the screen will go black with the backlight remaining on and an underline cursor blinks in the upper left. But that's as far as it goes. I can get out of it with a ctrl-alt-f5 which will bring me to a command line prompt. From there I can do a sudo reboot.

Anybody have any ideas? I've found lots of posts related to failure-to-resume (though no fixes), but none related to failure to suspend.

---

### Post by corelulos on 2010-05-27
> **hufemj said:**
> I have the same problem on my Dell Latitude D600 with 10.04. Suspend worked fine on Karmic. Then I upgraded to Lucid and suspend stopped working. It's particularly annoying since my wife will pick up my laptop to check her email. When she's done she closes the lid. It's pointless to tell (okay, ask) not to. That would be a criticism. But, that's for another post.

Anyway, when I next find my laptop the fan the lid is closed, the fan is running like mad, and it's disturbingly warm. Opening the lid for resume doesn't work, probably because suspend didn't work in the first place.

Manual suspend doesn't work either. If I select suspend from the shutdown menu, the screen will go black with the backlight remaining on and an underline cursor blinks in the upper left. But that's as far as it goes. I can get out of it with a ctrl-alt-f5 which will bring me to a command line prompt. From there I can do a sudo reboot.

Anybody have any ideas? I've found lots of posts related to failure-to-resume (though no fixes), but none related to failure to suspend.

My Toshiba L505D GS6000 has the same bug with hibernate too. Well it seems to power down the system but you can't wake it.

---

### Post by oiler920 on 2010-05-28
My D600 has the exact same problem with Lucid. Worked on Karmic, not on Lucid. Funny thing, I was actually running a modded version of OS X 10.5.6, but switched back to Ubuntu because I missed sleep mode. Then I find out that, surprise!, there's been a regression, and Lucid no longer wakes from sleep on the D600. :(

---

### Post by texadactyl on 2010-05-28
Truly funny first post.

My sad story: I am a long time Ubuntu user/developer so I won't leave.  My file/media server is running well with Lucid up-to-date.  My workstation, an HP Pavilion Slimline s3100n that I got through an equipment swap, is running fine except for one issue:

[LIST]
[*]Suspend and hibernate work fine without any diagnostics.
[*]Resume from either is impossible.
[/LIST]
Sigh.  This has happened so many times over the years with various types of hardware that its really annoying.  Keep in mind, these comments are not a complaint about Ubuntu, the kernel, or anything else.  As a developer, I know that it is difficult to stay current with a kernel on 1000s of motherboard chipsets.

I am not leaving, John!  I shall continue my quest for a solution.  Should I find one, I'll post it here.

---

### Post by efflandt on 2010-05-28
By default Lucid uses kernel mode setting (KMS) video driver for certain brands of cards, instead of the previous user space video modules.

Have any of you tried the **nomodeset** kernel boot parameter?  My desktop had some rather slow video on its ATI X1300.  Suspend seemed to shut off the hard drive, but blank video screen remained on (my HDTV did not say no signal) and power remained on.  Hibernate would appear to save RAM to disk, but left everything powered up including the hard drive and blank video still on.  The nomodeset parameter made video as responsive as 9.10, and fixed suspend/hibernate.

I had somewhat different occasional scrambled boot graphics hang with Radeon Mobility X1300 in a work Dell Inspiron 6400 laptop booted from USB hd.  The nomodeset option seems to resolve that, but I don't recall if I tested suspend/hibernate on that.

---

### Post by hufemj on 2010-05-30
> **efflandt said:**
> By default Lucid uses kernel mode setting (KMS) video driver for certain brands of cards, instead of the previous user space video modules.

Have any of you tried the **nomodeset** kernel boot parameter?  My desktop had some rather slow video on its ATI X1300.  Suspend seemed to shut off the hard drive, but blank video screen remained on (my HDTV did not say no signal) and power remained on.  Hibernate would appear to save RAM to disk, but left everything powered up including the hard drive and blank video still on.  The nomodeset parameter made video as responsive as 9.10, and fixed suspend/hibernate.

I had somewhat different occasional scrambled boot graphics hang with Radeon Mobility X1300 in a work Dell Inspiron 6400 laptop booted from USB hd.  The nomodeset option seems to resolve that, but I don't recall if I tested suspend/hibernate on that.

Here's where it gets really frustrating. I've seen mention in lots of posts about nomodeset. I'd love to try it. But try and find information about how to set it!? This page doesn't mention it at all and it doesn't appear in the 'exhaustive list of kernel boot parameters':

[https://help.ubuntu.com/community/BootOptions#Common%20Boot%20Options](https://help.ubuntu.com/community/BootOptions#Common%20Boot%20Options)

I tried editing the kernel line in menu.lst (even though I'm running Lucid, it was through an upgrade and still have the old grub). But given that I don't see the exact syntax for nomodeset in any documentation anywhere, I can't be sure that I have it right. For example, is it that nomodeset is simply appended to the kernel line, or should it be modeset=0 or something else? How can I verify that I have it right?

Thanks.

---

### Post by hufemj on 2010-05-30
> **hufemj said:**
> Here's where it gets really frustrating. I've seen mention in lots of posts about nomodeset. I'd love to try it. But try and find information about how to set it!? This page doesn't mention it at all and it doesn't appear in the 'exhaustive list of kernel boot parameters':

[https://help.ubuntu.com/community/BootOptions#Common%20Boot%20Options](https://help.ubuntu.com/community/BootOptions#Common%20Boot%20Options)

I tried editing the kernel line in menu.lst (even though I'm running Lucid, it was through an upgrade and still have the old grub). But given that I don't see the exact syntax for nomodeset in any documentation anywhere, I can't be sure that I have it right. For example, is it that nomodeset is simply appended to the kernel line, or should it be modeset=0 or something else? How can I verify that I have it right?

Thanks.

Here's what I have in menu.lst:

title           Ubuntu 10.04 LTS, kernel 2.6.32-22-generic
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.32-22-generic root=UUID=23c90b06-db81-4cff-be57-565f0b39862f ro quiet splash nomodeset
initrd          /boot/initrd.img-2.6.32-22-generic
quiet

If that's the way nomodeset is supposed to be set, then it's not solving the problem.

When I choose suspend, a password dialog box briefly appears but goes away before I can respond. It's replaced by a black backlit screen with a flashing underline cursor in the upper left. I can ctrl-alt-f5 to a command prompt and then reboot. This is on a Dell Latitude D600, upgraded to Lucid and now using the open source ATI drivers. With Karmic, I used the proprietary drivers and had no problem with suspend. If I try the proprietary drivers with Lucid, I get the ATI Control Center and ATI Administrative Control Center in System->Preferences, but neither of them work. Each fails with a message saying that either the driver isn't working or the adapter cannot be found. System->administration->hardware shows an empty list of proprietary drivers. I believe that fglrxinfo seg-faulted.

---

### Post by timosha on 2010-05-30
On my Thinkpad R51 - 2887 suspend worked excellent on Lousy Lynx until a few days ago. Update Manager offered me regular updates, I installed them and since then, yes since then suspend doesn't work anymore. The moon is blinking and the fan is driving mad.

But no problem: as Lousy Lynx is of Jaguar Car quality I have two of them. One in the garage for maintenance (installation with updates on partition 2) and one to drive (installation without updates on partition 1).

---

### Post by harshads on 2010-05-31
I have similar problems. And I think I have isolated it.

Suspend/Resume works fine. However, if I close my laptop's screen (and then open it) during the suspend process or while the laptop is suspended it recovers to a blinking cursor.

This is weird - I have used gconf-editor to disable all operations on lid-close or lid-open and it still happens.

I can hit ctrl-alt-f4, enter my username and password and get a fully functional command prompt.

I tried top and found that all the various processes I have are still running.

I tried startx and it said that X was already running on display 0.

And suggestions? Even a way to start Gnome/X would we fine until a permanent fix is found...

---

### Post by harshads on 2010-05-31
I think I might have found a solution.

I disabled the lid in /proc/acpi/wakeup using

sudo -i
echo "LID0" > /proc/acpi/wakeup

And it seems to work fine now. 

This is a less than perfect solution but its fine as I don't use the lid for sleep/wakeup.

Still hoping for something more permanent.

---

### Post by harshads on 2010-05-31
[LEFT]Ok, no this problem is back.

I don't know why its happening now :(

Will wait for the kernel update
[/LEFT]

---

### Post by harshads on 2010-06-02
ROFL ROFL ROFL!

The 'solution' to this 'problem' is ctrl-alt-f7

That reloads the GUI

Wonder what it was though :D

---

### Post by stevenmansour on 2010-06-02
Same problem, though not consistent - Lenovo T500 here with Radeon restricted drivers.

Suspend / resume worked fine on 9.10, now on 10.04 (clean install) sometimes it doesn't go to sleep at all (flashing moon icon syndrome), sometimes it does but doesn't wake up (black screen), sometimes it works fine.

---

### Post by blueflame on 2010-06-02
I had the same problem on an Asus G50vt, but I found the problem that was preventing my laptop from sleeping and hibernating:

If you have an SD card in your laptop, take it out.


- Dave.

---

### Post by Sonador on 2010-06-02
LOL ctrl-alt-f7 works for me too.

What a pity I still have one problem, after this resume from suspend,  process **vbetool **take ~98% of a CPU...

---

### Post by harshads on 2010-06-02
> **blueflame said:**
> I had the same problem on an Asus G50vt, but I found the problem that was preventing my laptop from sleeping and hibernating:

If you have an SD card in your laptop, take it out.


- Dave.

Does this happen even if the card is not mounted? What if you manually mount it to, say, /mnt

---

### Post by Isaacgallegos on 2010-06-02
I swear I had this problem, and when I saw this thread I decided to start toying with the bug.... 

Now I can't get it to crash or misbehave in any way!

---

### Post by foureyesboy on 2010-06-16
Yes, I have the same problem with my Thinkpad X22.  It runs Ubuntu since 9.04 and it suspended/hibernated perfectly before Lucid.

Well, at first I thought something was broken when I did the upgrade from 9.10.  But later I took the time to backup everything and did a clean install but the problem persists.  I've tried a couple of workaround that I managed to google (like using of uswsusp) but failed.  I have even tried unplugging the WLAN before suspension/hibernation (which was not required in the past).  And the problem not only happens on my laptop.  I turned to my desktop and did a suspend and it failed in pretty much the same way.  So I can dare say that the suspension/hibernation is completely broken in Lucid.

And it is surprising to see that those bug reports in launchpad are still not marked as duplicate of any, which indicates that they still consider them as individual cases.  Many of these cases are still marked undecided, and no further action is taken for months.

When they are busy with the Alpha 1 of 10.10, I wonder how many of them really pay attention to this fundamental but crucial problem, especially for laptops.  In the past I stood by the 6 months schedule against those who criticize the strategy.  Now they get my vote.  Please fix the problem first before moving on to the next version.

---

### Post by ginbas on 2010-06-20
R51 thinkpad with the same problem. This needs to be fixed or a work around needs to be established. It is effecting far too many users. I will say that the dell e6400 works flawless.

---

### Post by ken631 on 2010-06-26
Could this be an X thing. I am having the same problem with my old laptop Dell D600 with suspending and hibernating are fine but coming back up from those states not so much. 

Alt Ctrl f7 sounds like a good work around i guess until its fixed

now for the touchpad that refuses to disable lol. ongoing.

---

### Post by stevesnz on 2010-06-27
As a work around System/Preferences/Power Management and under Battery change close lid to blank screen till they fix the bug.

---

### Post by Karl10 on 2010-07-04
ME TOO !!!    I was running Jaunty on my desktop, with no problems whatever.  Bought a brand-new ASUS G73JH-A1 laptop from XoticPC.  Installed Lucid Lynx, and have been having one problem after another: my Win7 install crashed and will NOT repair (I know, I know ... but until gaming improves in Linux in general, I'll keep running Windows just for gaming); issues with the ATI drivers not working properly, Suspend/Hibernate not resuming (CTRL-ALT-F7 does NOT work, by the way; have to hold the power button until it shuts down, then restart.  After restart, I find that I can't connect to the internte; I find that the "Enable Networking" setting has been unchecked... this happens only with a failed suspend/hibernate resume.  Sudden cessation of right-click function (everywhere, not just in one app).

Overall, I'm underwhelmed by this latest iteration of Ubuntu.  I'm seriously considering stepping back to Jaunty until  Lucid gets fixed.  I see no compelling reason to upgrade to Lucid even without all the glitches; given that there ARE all these glitches... my own choice is clear.

EDIT:  Running the 64-bit version, by the way; all prior experience was with the 32-bit versions.

It's Official:   Putrid Lynx !!

---

### Post by waynefoutz on 2010-07-04
My sleep, hibernate works fine, but I don't see much advantage in hibernating on my laptop. It takes about the same amount of time to wake up as it does to boot up fresh. I'm up and running in about 15 seconds either way.

---

### Post by echo6 on 2010-07-04
> **blueflame said:**
> If you have an SD card in your laptop, take it out.

Hmm, thanks this solved the issue when shutting the lid.  Going to suspend always caused a black screen and started the fan going wild.  Hibernation also works, when I remove the SD card!

Could this be a problem with udev/udisk?

---

### Post by dfrandin on 2010-07-04
> **waynefoutz said:**
> My sleep, hibernate works fine, but I don't see much advantage in hibernating on my laptop. It takes about the same amount of time to wake up as it does to boot up fresh. I'm up and running in about 15 seconds either way.

I have a Dell Vostro 1400 with 10.04 on it, and I can't get sleep/hibernate to work either. It never worked on the previous install of 8.04 either (never tried 9.04 or 9.10, only do LTS versions). But with 10.04, the system boots up and shuts down so fast, I really don't care one way or the other if the devs bother to fix this....

---

### Post by laserman on 2010-07-07
After having closed the lid on my HP Mini, opened it back up, noted the black screen...well, sort of. You could vaguely make out something on the screen, kind of like the older screens that had a burn in them. 

I pushed button after button, but nothing seemed to "wake up" the screen.

Finally, after pressing the 'fn' key and f4 (the icon for increasing the video illumination), the screen came back to life.

I have seen several blogs about this, hope this helps anyone who experiences this and hope this is inline with what all of you are frustrated with.

---

### Post by Karl10 on 2010-07-07
To those of you who don't care if the developers fix this or not:  Have you noticed that when you power back up from this glitch, your networking has been disabled, and all your settings from when it went down are also gone? No, it doesn't exactly crash the system, but it's damned inconvenient to have to reset everything back to where you had it every time you fire it up.

Maybe I'm in the minority here, but when I browse, I frequently have several different windows opened, each with many tabs opened.  As long as I shut down properly, it's all still there when I power back up.  IF , however, I wander off for a moment and get busy with something, and the system times out, when I come back and have to use the power button to off/on the system again, all that is gone, too; only the "Top" window (first one opened) is there, and all of the tabs read, "trouble loading page..." and I have to go up to networking, re-check the "enable networking" selection, wait for the connection to establish, then manually click each tab and CTRL-R it to force a reload.  I suppose I could just shut the browser down and restart it, but this whole upgrade has been so buggy that I'd probably lose all those tabs too... I don't wanna find out.  There's other stuff too, all minor, but collectively, massively annoying.  I'm just about ready to nuke both drives, and re-install everything except Putrid Lynx; I'll go back to "jaunty" instead.

It's not the severity of the bug that's at issue here; suspend/resume is not a minor feature for a laptop, and it's kind of a major oops to have released this version with such a bug in it.  Can you imagine the tsunami of outcry if Windows7 had shipped with this kind of bug in it?  Ain't we supposed to be better??  This, and other incidents like it, are the reason that Linux is in the place it's in right now; pretty nice, but not ready for prime time yet, not for "just users," anyway.  If you don't mind crawling around under the hood and making adjustments and stuff, it's okay, but Linux will never be "mainstream" (read: overtake Windows) until this goes away.

Start caring.

---

### Post by tamashumi on 2010-07-08
Hi guys,

I had no problem with hibernate/suspend just after fresh install (and some time it was ok).
I've upgraded RAM and extended SWAP partition so it's like ~100MB bigger than RAM (like before the upgrade).

Now I can't hibernate nor suspend. It seems like preparing to suspend, screen goes black, leds flashes and that's all. I can't even bring it back without hard reset by long power button pushing.

WTF? Booted from live CD still works. I'm not 100% sure if RAM upgrade itself has anything to do with it as I didn't use hibernation/suspend often. Besides I don't think swap is necessary to suspend (not hibernate)

What can I do besides fresh install which I would really like to avoid?

I'm on [this]("http://www.mobiletechreview.com/notebooks/Sony-Vaio-SZ650.htm") laptop, running integrated GPU this time.

---

### Post by mohammedsk on 2010-07-08
Same here, I have ASUS G73JH-A3 and when I hibernate or suspend the screen goes black, but I can see the backlight, keyboard backlight turns off, both fans stay on. I have to force shutdown and when it comes back on, the Network Connection is disabled. Basically, same story you guys have. Before I had Dell D830 and Ubuntu 10.04 and everything was working fine.

---

### Post by jssilva on 2010-07-15
> **blueflame said:**
> I had the same problem on an Asus G50vt, but I found the problem that was preventing my laptop from sleeping and hibernating:

If you have an SD card in your laptop, take it out.


Same with Asus A8Js and lucid.

Furthermore, it works flawlessly on the same hardware, using a parallel debian squeeze on another partition, with more or less the same software, without the need to take out the SD.

Rgds,
jss

---

### Post by teripittman on 2010-07-15
I just discovered that the sound issue on my Thinkpad T23 is also related to the "sleep" bug. Sound works if I reboot the laptop. If it goes into sleep mode, I lose the sound. I am also getting the issue where the fan runs hard, but that's very intermitant.

---

### Post by hugo_koopmans on 2010-07-22
Same here on a Sony Vaio SZ61. On Karmic no issues

ALso on Lucid veru slow boot, were on Karmic super fast(<15 sec) but that is a different subject?

hugo

---

### Post by hugo_koopmans on 2010-07-22
Guys,

I found something interesting, seems that the suspend DOES work for me only after 2 minutes it kicks in.

Tested several times on the console with 
sudo pm-suspend

in dmesg i get:

[ 8101.167130] PM: suspend of drv:sd dev:2:0:0:0 complete after 2147.045 msecs
[ 8101.586932] PM: suspend of drv:psmouse dev:serio1 complete after 406.807 msecs
[ 8101.780047] PM: suspend of drv:atkbd dev:serio0 complete after 193.108 msecs
[ 8222.530066] tpm_tis 00:09: tpm_transmit: tpm_send: error -62
[ 8222.530073] PM: suspend of drv:tpm_tis dev:00:09 complete after 120749.212 msecs
[ 8222.700329] PM: suspend devices took 123.800 seconds

does anyone know what tpm_tis is?

hugo

---

### Post by hugo_koopmans on 2010-07-22
[http://www.spinics.net/lists/mm-commits/msg79331.html](http://www.spinics.net/lists/mm-commits/msg79331.html)

says there is a patch for this...but don't want to build my kernel, gues I have to wait for next kernel release?

now on 2.6.32 ...

hugo

---

### Post by Am Elder on 2010-07-24
I'm also having a suspend / hibernate problem on my Dell E6400 with an nvidia gpu, using the proprietary driver.  I understand sometimes in the past the graphics card has been related to suspend and hibernate problems.  The suspend options stopped working in Jaunty and I'm just now getting around to trying to fix it.  I searched Launchpad and couldn't find an appropriate bug, has anyone here filed one?

When I tell the laptop to suspend or hibernate, the laptop goes to an illuminated black screen and keeps producing heat.  I'm not knowledgeable enough to say what internal components are on or off, but in general the computer stays on. Then when I press a key or touch the  trackpad,  the Log On dialog box appears.  Unlike many of the people posting to this thread I come back from an attempt to put the computer to sleep without a hitch.

This problem appeared in  autumn last  year after I had been running Jaunty for several months.  This spring, I  updated to Karmic and then straight through to Lucid and  the problem  remains.

I've attached a text file with the last two log reports from my   /var/log/pm-suspend.log.  One records me trying to suspend, the second   trying to hibernate.

It looks to my untrained eye that the important lines in both cases are:
```
/usr/lib/pm-utils/sleep.d/98tuxoniceui suspend   suspend:/usr/lib/pm-utils/sleep.d/98tuxoniceui: 10: cannot create   /sys/power/tuxonice/user_interface/enable_escape: Directory nonexistent
Returned exit code 2.
Thu Jul 22 04:47:58 CEST 2010: Inhibit found, will not perform   suspend
```

**Edit:** I found the [bug report on Launchpad]("https://bugs.launchpad.net/ubuntu/+source/hibernate/+bug/582025") that pertains to this bug.

---

### Post by riprowan on 2010-08-19
** BUMP **

I also have this problem intermittently on my Lenovo T400.

I see several posts with ideas about solutions.  Anything definitive yet?

---

### Post by JustLikeYouImagined on 2010-08-19
can anybody please explain to a newbie how to apply this patch?

I have a HP Pavillion laptop and it won't go into 'Suspend' mode.

---

### Post by dkados on 2010-08-20
I have similar problems with an Asus G60J:
Suspend & Hibernate blanks the screen(with sometimes some cursor there), after a few seconds the disk light is activated and the fan is at max speed. The only way to finish this state is to hold the power button long enough to switch the laptop off...

---

### Post by mastablasta on 2010-08-20
i have to take out the batery (very old notebook). Suspend doesn't work, hibernate does.

---

### Post by xircon on 2010-08-20
Me too, Dell Inspiron N5010, suspends OK, will not resume and it kills the network, I have to:

```
sudo gedit /var/lib/NetworkManager/NetworkManager.state 

```

And change false to true on the NetworkEnabled line to get it back.

---

### Post by dkados on 2010-08-21
Steps needed to make it work for Asus G60J:

According to thread "[B]Cannot suspend or hibernate Asus N61J Laptop"
(thx. John Diaz & ipsi)

- find ehci devices
[/B]```
# ls /sys/bus/pci/drivers/ehci_hcd/
0000:00:1a.0  bind    new_id     uevent
0000:00:1d.0  module  remove_id  unbind

```- Create suspend script, (replace XXXX:XX:XX.X for all found devices above)
```
#!/bin/sh
# File: "/etc/pm/sleep.d/20_custom-ehci_hcd".
case "${1}" in
        hibernate|suspend)
              # Unbind ehci_hcd for first device XXXX:XX:XX.X:
               echo -n "XXXX:XX:XX.X" | tee /sys/bus/pci/drivers/ehci_hcd/unbind
              # Unbind ehci_hcd for second device XXXX:XX:XX.X:
               echo -n "XXXX:XX:XX.X" | tee /sys/bus/pci/drivers/ehci_hcd/unbind
        ;;
        resume|thaw)
              # Bind ehci_hcd for first device XXXX:XX:XX.X:
              echo -n "XXXX:XX:XX.X" | tee /sys/bus/pci/drivers/ehci_hcd/bind
              # Bind ehci_hcd for second device XXXX:XX:XX.X:
              echo -n "XXXX:XX:XX.X" | tee /sys/bus/pci/drivers/ehci_hcd/bind
        ;;
esac

```- Unload module xhci
```
#File: "/etc/pm/config.d/usb3-suspend-workaround".
SUSPEND_MODULES="xhci"

```- make script executable
```
sudo chmod +x /etc/pm/sleep.d/20_custom-ehci_hcd

```- modify GRUB2 /boot/grub/grub.cfg (or better scripts in /etc/default/grub, /etc/grub.d)
  find your "linux" line.
```
#File: "/boot/grub/grub.cfg".

        linux /boot/vmlinuz-2.6.32-24-generic root=/dev/mapper/ROOT-root_ubuntu 
resume=/dev/mapper/ROOT-swap ro nomodeset quiet splash

```
"nomodeset" is required for Nvidia graphic cards
resume=.... should point to a swap device with min. size of system main memory
others will depend on your current installation and should not be changed

---

### Post by Dusenberg on 2010-08-29
I also have power management probs on Philips x66 laptop since moving to 10.04 from 9.10 with clean install. 

Several issues:
a) If I boot on battery the system goes to hibernate immediately I hit return after entering my password at the GUI login. Then when I press the power button the login screen re-appears very quickly complete with the password (dotted) so I hit return and I'm in.....
b)...then I get "battery critical" message popup even if right click on battery icon displays 82% full (that was last night) and suddenly the laptop goes into hibernate.  
c) if I disconnect ac while using the laptop the system goes into hibernate immediately even with a full battery - no messages or anything.....

This means the laptop is pretty well unusable on battery.

However the system suspends and resumes ok, and hibernates and returns ok. It's just doing it at the wrong times!

I had no problems on 9.10. I've also checked that there's nothing wrong with battery by booting into Vista (dual boot setup) and the battery status shown there is the same as in 10.04 +/- a couple percent, and vista just keeps running if I disconnect ac. 

I've tried several things from this thread but nothing changes the problem.  Look forward to a new kernel as I generally like 10.04..............

---

### Post by anjames on 2010-08-30
Hey guys, this probably won't work for everyone (it sounds like some of you might have different problems...), but if you had hibernate working, then upgraded your kernel then I would put my money that it's the new kernel messing you up.

The system scripts and user software in Ubuntu are increasingly polished and excellent in my experience, but any given developer has a finite number of machines that they work on (probably just ONE!), so they can't test new kernels on different hardware. This inevitably introduces problems when you change kernels, and that's why we keep old ones installed still (hopefully!).

Just by reverting to my old kernel I fixed the hibernate problem I had:
[http://ubuntuforums.org/showthread.php?p=9785198#post9785198](http://ubuntuforums.org/showthread.php?p=9785198#post9785198)

It seems like people often overlook this simple fix when hibernate USED to work, but then stops after an upgrade. Give that a try and I bet you'll be pleasantly surprised!

---

### Post by Iananan on 2010-09-08
I have found, that suspend/resume and hibernate work perfectly on 10.04, and 10.10 beta, UNTIL I install ndiswrapper, which causes a kernel error, and breaks the sleep functionality.

I've taken to using an external WLAN card with open source drivers now, it's a bit annoying, but it works.

---

### Post by Goatrancer on 2010-09-09
I have a very intermittent problem on my acer 1410 su2300 running UNR 10.04. I have power management set to hibernate on lid close, but sometimes my laptop gets very hot after closing the lid. When I open the lid, my password lock screen is there, suggesting to me that the computer thought it was suspended. This is only a very intermittent behavior, so I haven't been able to discern any pattern to give me a clue to what might be causing it.

---

### Post by dkados on 2010-09-11
Are you using something like Vmware Workstation on your Ubuntu box?

---

### Post by Goatrancer on 2010-09-12
I have virtualBox right now but this started happening long before I installed it, so it can't be solely related to it.

---

### Post by utkjamie on 2010-09-24
My gripe is that I have nothing in my power settings that gives Kubuntu permission to suspend, yet it does it anyway if I'm on battery and close the lid. It suspends fine but the screen does not come back on when I wake it up, which means I have to kill the power to be able use my laptop again. The problem with that is that I'm using the EXT4 filesystem, which has delayed writing, so these improper reboots almost always cause some form of data loss or corruption.

It would be one thing if I knew the problems and still enabled suspend, but to turn it off and still have the laptop go into suspend mode is completely unacceptable especially with the consequences aren't merely annoyances but lost and corrupted data.

---

### Post by Goatrancer on 2010-09-27
> **Goatrancer said:**
> I have a very intermittent problem on my acer 1410 su2300 running UNR 10.04. I have power management set to hibernate on lid close, but sometimes my laptop gets very hot after closing the lid. When I open the lid, my password lock screen is there, suggesting to me that the computer thought it was suspended. This is only a very intermittent behavior, so I haven't been able to discern any pattern to give me a clue to what might be causing it.

Additional info:
I had this problem again today, when I took the burning hot laptop out of my backpack, I noted that:
1) The power light was blue, as if the computer were in use, instead of orange, like when the computer is hibernating
2) The WiFi light was flashing, but is normally off when suspend works correctly.
3) The fan was blowing like crazy
4) I did NOT have any virtual machines running (although the VirtualBox application was launched)

Anyone have any ideas as to why hibernate would randomly fail?

---

