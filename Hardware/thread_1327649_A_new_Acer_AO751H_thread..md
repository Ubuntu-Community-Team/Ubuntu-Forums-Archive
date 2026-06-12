---
title: "A new Acer AO751H thread."
date: 2009-11-15
forum: Hardware
---

### Post by Brii on 2009-11-15
I've been looking for a while around on how to fix the screen resolution to 1366x768 on the Acer AO751H and the threads I found that people said they got it to work. Most of the links did not work! They were down or the links only worked in 9.04.

So let this be the new thread to find out how fix it on 9.10. Please help I been trying so long to fix this.

Thanks
--Brian

---

### Post by Reverend G on 2009-11-15
[https://wiki.ubuntu.com/HardwareSupportComponentsVideoCardsPoulsbo](https://wiki.ubuntu.com/HardwareSupportComponentsVideoCardsPoulsbo)

Used this link on Wednesday to get my Ao751h running properly under Karmic. Just checked the page and it's up.

There were some differences in what I did compared to the instructions though. For some reason I wasn't able to append the sources lists with echo (kept coming up with permission denied regardless of whether it was sudo'd or not) so I just created the files with gedit and saved to the appropriate locations. Also just used Gdebi to install the downloaded deb files and modified the blacklist.conf through gedit again. However since I conducted the work I've had 1366x768 working perfectly.

---

### Post by Brii on 2009-11-15
> **Reverend G said:**
> [https://wiki.ubuntu.com/HardwareSupportComponentsVideoCardsPoulsbo](https://wiki.ubuntu.com/HardwareSupportComponentsVideoCardsPoulsbo)

Used this link on Wednesday to get my Ao751h running properly under Karmic. Just checked the page and it's up.

There were some differences in what I did compared to the instructions though. For some reason I wasn't able to append the sources lists with echo (kept coming up with permission denied regardless of whether it was sudo'd or not) so I just created the files with gedit and saved to the appropriate locations. Also just used Gdebi to install the downloaded deb files and modified the blacklist.conf through gedit again. However since I conducted the work I've had 1366x768 working perfectly.

I had the same problem with echo, how do you fix that?
and which one do you download from [http://swiss.ubuntuforums.org/showpost.php?p=7773647&postcount=13](http://swiss.ubuntuforums.org/showpost.php?p=7773647&postcount=13) and what do you do with it?

Thanks alot. I'm pretty new to linux so I'm having trouble. You're help is greatly appreciated. =)

---

### Post by Brii on 2009-11-15
> **Reverend G said:**
> [https://wiki.ubuntu.com/HardwareSupportComponentsVideoCardsPoulsbo](https://wiki.ubuntu.com/HardwareSupportComponentsVideoCardsPoulsbo)

Used this link on Wednesday to get my Ao751h running properly under Karmic. Just checked the page and it's up.

There were some differences in what I did compared to the instructions though. For some reason I wasn't able to append the sources lists with echo (kept coming up with permission denied regardless of whether it was sudo'd or not) so I just created the files with gedit and saved to the appropriate locations. Also just used Gdebi to install the downloaded deb files and modified the blacklist.conf through gedit again. However since I conducted the work I've had 1366x768 working perfectly.

Alright I'm up to here:

"Also just used Gdebi to install the downloaded deb files and modified the blacklist.conf through gedit again. However since I conducted the work I've had 1366x768 working perfectly"

And does it matter which one i download from here b/c theres like 4 links are they the same?
[http://swiss.ubuntuforums.org/showpost.php?p=7773647&postcount=13](http://swiss.ubuntuforums.org/showpost.php?p=7773647&postcount=13)

do you think I need to modify blacklist.conf?

---

### Post by Brii on 2009-11-15
hahaa Holy ****!

It worked thank you!!

---

### Post by Reverend G on 2009-11-16
No worries. I'm glad you were able to make sense of what I wrote. 
 
Just for completeness (and for others reading the thread) it was the three .deb files that required downloading from [[COLOR=#000000]http://swiss.ubuntuforums.org/showpo...7&postcount=13[/COLOR]]("http://swiss.ubuntuforums.org/showpost.php?p=7773647&postcount=13") ; there is a tarball there too but I didn't use it. I'm also not sure if it's absolutely necessary to modify the blacklist.conf but I did it just in case; I assume you did too.
 
As far as fixing the echo problem I'm looking into it; I'll post back when I find an answer.

---

### Post by Reverend G on 2009-11-16
WRT the echo problem: just learned something:
 
The instructions stated that the commands specified had to be sudo'd, but with the echo commands both the additional text AND the location have to be sudo'd: for example:
 
echo 'deb [http://ppa.launchpad.net/ubuntu-mobile/ppa/ubuntu](http://ppa.launchpad.net/ubuntu-mobile/ppa/ubuntu) jaunty main' >> /etc/apt/sources.list.d/ubuntu-mobile.list

when sudo'd should be:
 
**sudo** echo 'deb [http://ppa.launchpad.net/ubuntu-mobile/ppa/ubuntu](http://ppa.launchpad.net/ubuntu-mobile/ppa/ubuntu) jaunty main' >> **sudo** /etc/apt/sources.list.d/ubuntu-mobile.list

---

### Post by Marc Gottlieb on 2009-11-16
I just upgraded Jaunty to Karmic on my Acer ao751h.  I cannot get the full screen resolution of 1366x768.
 
With Jaunty 9.04, I got the full screen by:
1)  add the following to/etc/apt/sources.list:
    deb [http://ppa.launchpad.net/ubuntu-mobile/ppa/ubuntu](http://ppa.launchpad.net/ubuntu-mobile/ppa/ubuntu) jaunty main
2)  executing the following:
    sudo gpg -keyserver keyserver.ubuntu.com -recv 0×99d6b21cc6598a30
    sudo apt-get update
    sudo apt-get install xserver-xorg-video-psb
 
This wouldn't work after the upgrade.
I have spent all day following the advice on several Ubuntu forums, including the advice on this forum and at:
[https://wiki.ubuntu.com/HardwareSupportComponentsVideoCardsPoulsbo](https://wiki.ubuntu.com/HardwareSupportComponentsVideoCardsPoulsbo)
[http://ubuntuforums.org/showthread.php?p=8323658](http://ubuntuforums.org/showthread.php?p=8323658)
[https://launchpad.net/+help/soyuz/ppa-sources-list.html](https://launchpad.net/+help/soyuz/ppa-sources-list.html)

I have followed each line and done every detail suggested.  Each item seemed to execute properly (file updates, package download and install, etc), but in the end, my screen is stuck at 1024x768.  None of it has worked.  
 
If it cannot be resolved I will reinstall 9.04, but before doing that, I was hoping that someone who has cracked this nut might be able to post a more detailed or explicit set of instructions.
 
Thanks,  Marc

---

### Post by Reverend G on 2009-11-17
[FONT=Arial][B]PLEASE NOTE: Since this post was made things have moved on slightly; you will get better results if you follow the instructions here: 

[https://wiki.ubuntu.com/HardwareSupportComponentsVideoCardsPoulsbo](https://wiki.ubuntu.com/HardwareSupportComponentsVideoCardsPoulsbo)
[/B]


Unfortunately having taken a look at various forums regarding Karmic it seems that upgrades are more problematic than fresh installs. [/FONT]
 
[FONT=Arial]This is exactly what I did with a fresh install of 9.10 to get 1366x768. I'm far from a linux/ubuntu expert so there's probably far more elegant ways of doing this but I carried out these actions and it worked for me. If at any step it seems like I'm teaching you to suck eggs I apologise:[/FONT]
 
[FONT=Arial]**1:** Open up a terminal and type:[/FONT]
 
```
sudo gedit
```[FONT=Arial]Enter your password. Once gedit opens type the following lines:[/FONT]
 
```
 
deb http://ppa.launchpad.net/ubuntu-mobile/ppa/ubuntu jaunty main
deb-src http://ppa.launchpad.net/ubuntu-mobile/ppa/ubuntu jaunty main

```[FONT=Arial]Then save the file as **ubuntu-mobile.list** in **/etc/apt/sources.list.d**[/FONT]
 
[FONT=Arial]**2:** Delete the text in the gedit window and type the following lines:[/FONT]
 
```
 
deb http://ppa.launchpad.net/albertomilone/poulsbo-graphics/ubuntu jaunty main
deb-src http://ppa.launchpad.net/albertomilone/poulsbo-graphics/ubuntu jaunty main

```[FONT=Arial]Then save the file as **poulsbo-graphics-alberto-milone.list** in **/etc/apt/sources.list.d**[/FONT]
 
[FONT=Arial]**3:** Go back to the terminal and type the following commands:[/FONT]
 
```
 
sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys C6598A30
 
sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 99C0198F
 
sudo apt-get update
 
sudo apt-get install dkms fakeroot
 
sudo apt-get install libdrm-poulsbo1
 
sudo apt-get install poulsbo-driver-2d poulsbo-driver-3d psb-firmware

```[FONT=Arial]**4:** Download the three .deb files from [[COLOR=black]http://swiss.ubuntuforums.org/showpo...7&postcount=13[/COLOR]]("http://swiss.ubuntuforums.org/showpost.php?p=7773647&postcount=13") and ignore the tar.gz file.[/FONT]
 
[FONT=Arial]Once downloaded either double click on them to open them in gdebi or left click and select "Open with gdebi". You can then select to install them; install all three. AFAIK it doesn't matter what order they're installed in.[/FONT]
 
[FONT=Arial]**5:** Go back to gedit and delete the text in the gedit window. Type the following lines:[/FONT]
 
```
 
Section "Device" 
Identifier "GMA500"
Option "AccelMethod" "EXA" 
Option "DRI" "on" 
Option "MigrationHeuristic" "greedy" 
Option "IgnoreACPI" "yes" 
Driver "psb" 
EndSection
 
Section "DRI" 
Mode 0666 
EndSection

```[FONT=Arial]Then save the file as **xorg.conf** in** /etc/X11**[/FONT]
 
[FONT=Arial]**6:** In gedit[/FONT][FONT=Arial] open the file **/user/bin/compiz**[/FONT]
 
[FONT=Arial]Immediately save the file as **compiz.save** in** /usr/bin** for safety.[/FONT]
 
[FONT=Arial]Scroll down to the driver whitelist: there should be a series of terms in a set of quotes i.e.:[/FONT]
 
```
WHITELIST="nvidia intel ati radeon radeonhd i810 fglrx"
```[FONT=Arial]Change it to:[/FONT]
 
```
WHITELIST="psb nvidia intel ati radeon radeonhd i810 fglrx"
```[FONT=Arial]Save the file as **compiz** in **/usr/bin**[/FONT]
 
[FONT=Arial]gedit will ask you if you want to overwrite the original file: select "Overwrite".[/FONT]
 
[FONT=Arial]**7:** Close gedit and the terminal window and restart your computer. [/FONT]
 
[FONT=Arial]At this point I was pleasantly surprised to have 1366x768 working. Hopefully it&#8217;ll work for everyone else. If you do give it a try please report back and let us all know how it went.[/FONT]

---

### Post by Marc Gottlieb on 2009-11-18
To Reverend G,
Thanks so much for your excellent and detailed how-to.  I tried it, letter-by-letter, but no cigar.  I am going to wipe the partition and try a fresh install of 9.10, and see if that works.  If not, then back to 9.04.  I will post an update after I try this stuff.

---

### Post by Marc Gottlieb on 2009-11-18
To Reverend G,
 
IT WORKS!
 
The trick was the difference between an upgrade versus a fresh install.  I reinstalled 9.10 fresh from a CD, which wiped out the previous installation altogether, then reloaded a virgin version of the OS.
 
Then following your instructions step-by-step, it worked perfectly.  Now I have the full screen resolution again, 1366x768.  HUGE THANKS.
 
I am what you might call a Windows power user, and this machine is my first foray into Linux.  So, here is what I learned about this process, which hopefully will help someone else:
 
- When I started the clean reinstall, I worried that it would wipe my partitions and that all of my configurations, such as custom toolbars for OpeOffice apps would be gone.  So, I backed up those folders and config files.  I would recommend doing that anyway, but it turns out that the fresh Ubuntu 9.10 install does not wipe user files, just core OS files.  If you are a Win user, it is like reinstalling the System State.  The installation process will alert you that the old installation files are being deleted, but user and config files remain, so the partitions are not actually being wiped.  If you do a reinstall, DO NOT delete and reformat the partitions, just let the install process do its own thing.  So, if the fear of having to reconfigure a new installation from scratch is holding you back, don't worry.
 
- Then, follow Reverend G's notes exactly as he has written.
 
Thanks a whole bunch.

---

### Post by webofdallas on 2009-11-18
It worked for me too! Yippee! Thanks A Million! :popcorn:

I don't know if > sudo update-initramfs &#8211;u did anything because it said something about useage but it worked any way. I'm extremely happy. You're the man. Oh I even skipped the blacklisting too because I had to stop in the middle and then came back and finished it. After I finished and rebooted and it worked I logged in to post this thank you and realized I skipped the blacklisting 915 thing I went back and did it but didn't run the update-initramfs -u or anything. Do you think I should? It's working. Don't fix it if it's not broke, right?

---

### Post by Reverend G on 2009-11-19
It's funny you should mention the initramfs command; I'm sure I got some kind of negative message when I ran it. I'm going to install another copy of Karmic to another partition to try the procedure again but this time I'll leave the initramfs command out and see if it makes any difference. I'll also leave out the blacklisting. I shall report back when done and amend the SOP to fit if necessary.

EDIT: Just reinstalled and ran the procedure for 1366x768 without the initramfs and blacklist steps and it still works just fine; SOP edited!

---

### Post by Udibuntu on 2009-11-20
I also have a 751 with native resolution and Flash running; no HD capabilities yet though.

What worked for me was:

Lucazade's script, mentioned in post # 87 I think, [here]("http://ubuntuforums.org/showthread.php?t=1253406&page=9"):

Then installing recent Flash from Adobe and enabling Karmic Partner repository in Software Sources.

So far it works. I'll wait and see if kernel updates or other updates break this.

So far, my open issues with Karmic on 751 - no battery tab in power management so no indication on battery level. Resume from suspend/hibernate do not work.

Aaanndd - no sound... 2 days ago my 751 lost all sound besides the small drums just before login, so I know the card is there, the drivers are there... I'll look it up, but any help would be greatly appreciated..

---

### Post by Reverend G on 2009-11-26
Haven't had any problems with sound thus far but updating to 2.6.31-15 broke the screen resolution fix: update manager specified the update of the poulsbo drivers but once the update was complete and the machine was recycled the X Window system just wouldn't work. I don't recommend the update of the kernel if you want to keep the 1366x768 screen resolution but if you update and have the same problem as me do the following:

1 Hold down shift while booting to open up the grub 2 menu
2 Select the 2.6.31-14 kernel and load it up.
3 Once logged in download startup manager from Ubuntu Software Centre and open it up. Change the default operating system to the -14 kernel and close. System should then run as before.

Hopefully the -15 kernel will be updated/patched/fiddled with eventually to remedy the situation.

---

### Post by filipecamargo on 2009-11-26
> **Udibuntu said:**
> 

So far, my open issues with Karmic on 751 - no battery tab in power management so no indication on battery level. Resume from suspend/hibernate do not work.

Aaanndd - no sound... 2 days ago my 751 lost all sound besides the small drums just before login, so I know the card is there, the drivers are there... I'll look it up, but any help would be greatly appreciated..

Same 2 problems here! I have the battery tab but it shows always "fully charged" and my sound was working and stopped somehow...

---

### Post by Udibuntu on 2009-11-27
Sound is back on after I [removed and re-installed alsa files]("http://ubuntuforums.org/showthread.php?t=1334529&highlight=remove+alsa+files"). I then hit a snag with mute after boot but fixed that with setting the alsamixer right and fixating it with 'alsactl store'.

Look into it and see if this is the right solution for your sound problem.

---

### Post by chanklor on 2009-11-29
I have the same problem with sound, i hear the initial drums, but after that i hear nothing.
has anyone else tried that? reinstalling ALSA?
and, how do you do it?

---

### Post by miro_braun on 2009-12-01
Hi, 

I have a big problem with Ubuntu 9.10 on my Acer Aspire One 715h. When i try to boot into live mod, or start install, while booting, on the bare begining, my laptop just freezes, and I can't do anything then.. not even power button works..nor CTL+ALT+DEL

but oddest thing about this is that it doesn't happen regulary, it sometimes boots up normaly, and in most cases it freezes.. i don't know what is wrong or what to do. 

But, i have noticed that it always freezes on the line saying something about USB mangement, or wireless..

Has anyone experineced something like that ?

---

### Post by penguin10916 on 2009-12-01
I'm just wondering with sound... it's a pain and when I use headphones it only mutes the right speaker with sound coming from the right headphone, however sound comes from the left speaker and there is no sound from the left headphone... any suggestions?

---

### Post by Reverend G on 2009-12-01
I've been using a pair of Sony MDR-XD200 headphones and I can't replicate that problem: plugging them in mutes all sound coming from the netbook apart from the sound of the cooling fan and headphones sound great. What 'phones are you using?

With regard to miro_braun's problem have you got any USB peripherals plugged in while booting? SD card in the reader? What's the boot order specified in the bios?

---

### Post by Legendário on 2009-12-02
Is anyone using karmic netbook remix??? I had everything working fine but after a recent update I can`t see the menu anymore. Have to access all the programs using Alt+F2 key.

Can anyone help me with that?

---

### Post by Udibuntu on 2009-12-02
Updated to kernel .15 - native resolution is gone. will update on fix if i find one.

---

### Post by Udibuntu on 2009-12-02
> **Reverend G said:**
> Haven't had any problems with sound thus far but updating to 2.6.31-15 broke the screen resolution fix: update manager specified the update of the poulsbo drivers but once the update was complete and the machine was recycled the X Window system just wouldn't work. I don't recommend the update of the kernel if you want to keep the 1366x768 screen resolution but if you update and have the same problem as me do the following:

1 Hold down shift while booting to open up the grub 2 menu
2 Select the 2.6.31-14 kernel and load it up.
3 Once logged in download startup manager from Ubuntu Software Centre and open it up. Change the default operating system to the -14 kernel and close. System should then run as before.

Hopefully the -15 kernel will be updated/patched/fiddled with eventually to remedy the situation.

I'll try that and update on results. UPDATE - default is .14. Thanks.

This is one of the more crude workarounds I have ever needed to perform, bahh. I too hope a fix to kernel 2.6.31-15 will be out soon.

---

### Post by penguin10916 on 2009-12-02
> **Reverend G said:**
> I've been using a pair of Sony MDR-XD200 headphones and I can't replicate that problem: plugging them in mutes all sound coming from the netbook apart from the sound of the cooling fan and headphones sound great. What 'phones are you using?

With regard to miro_braun's problem have you got any USB peripherals plugged in while booting? SD card in the reader? What's the boot order specified in the bios?


I have two pairs of normal headphones. Both do the same things. This problem just came suddenly. Prior to, I was trying to fix the problem created by the timer line in the alsa-base.conf file. Afterwards, everyting worked, but the headphones problems just happened randomly. Also, I did build the alsa drivers source as a recommendation to fix this problem. However, it didn't do anything, but after commenting out the 2nd have of the timer line, everything worked for awhile.

---

### Post by miro_braun on 2009-12-02
> **Reverend G said:**
> With regard to miro_braun's problem have you got any USB peripherals plugged in while booting? SD card in the reader? What's the boot order specified in the bios?

Well, i am booting from USB flash drive ... :S but this also happens after succesfull installation, without USB drive inserted..

But, one other odd thing is that this doesn't happen with ubuntu 9.04, only with 9.10. Is it something about the version of the kernel ?


Boot order:

IDE CD
IDE HDD: name of hdd
USB HDD
PCI BEV
USB CDROM
USB FDC
USB KEY

---

### Post by penguin10916 on 2009-12-02
I fixed my own problem. Just had to upgrade the kernal... though the poulsbo drivers threw a small fit, otherwise, sound, video, wireless... just about everything is working except for power management as far as being able to tell when the power cord is and isn't plugged in... oh and the wifi indicator light doesn't work XD

---

### Post by Legendário on 2009-12-03
> **penguin10916 said:**
> I fixed my own problem. Just had to upgrade the kernal... though the poulsbo drivers threw a small fit, otherwise, sound, video, wireless... just about everything is working except for power management as far as being able to tell when the power cord is and isn't plugged in... oh and the wifi indicator light doesn't work XD

How did you update the kernel? Did you download and compiled it yourself? My hardware working status is exact the same as yours. I had a hard time trying to fix the netbook-launcher, which suddenly disappeared, but it was missing libGL.so.1 which I don't know why the hack was not there. But this is gone already.

---

### Post by penguin10916 on 2009-12-05
It's tricky. If you have the poulsbo driver installed, you need to delete your xorg.conf file and uninstall the packages. Reason being is that they don't upgrade well. They have to be reinstalled when the new kernal is running. I went into aptitude and found the generic linux package, and that just upgraded my kernal. Also, I am able to contantly upgrade the kernal (which can be careful) Anyways, look for the metapackage, install it, reboot, reinstall the poulsbo drivers in apt (they'll still be there if you used the ppa.??? repos) recreate the xorg.conf file and then you're done. Everythign works fine.

On another note, when (assuming that they are still being worked on) will the gallium drivers for the poulsbo be finished? Because I'm getting bored of partial acceleration... I can watch youtube full screen even high quality; I can watch 720p mp4s in totem. But I can't watch hulu vids fullscreen. Any suggestions?

---

### Post by penguin10916 on 2009-12-06
I think I found a holy grail of ubuntu/ubuntu-based linux distros for this netbook: Moon Os. It's relatively new, based off of Ubuntu 9.04, uses Enlightenment over Gnome, boots faster, power management works flawlessly, no sound problems, video works great if you install the poulsbo drivers... just about everything works. Just a few quarks with enligtenment. However, I'm updating packages right now. I'll comment on here to see if it helps and/or hurts the system. Also, Moon OS 4 will be released soon and will probably be based off of 9.10 (yuck)... in which case many of the problems may come back... Also, PcLinuxOs works well, however, RPM distros are a pain because of the lack of software, and also Sabayon won't boot because of X11... So at the moment, Ubuntu and it's spawns/bastards are the best so far.


*update: updating software turned the system into total crap... guess this is not the answer...

---

### Post by cyclopsface on 2009-12-07
Has anyone gotten suspend to work?  I tried adding the code from the Acer wiki to HAL .ins file but it didn't make a difference.  Is there a way forward?  Also, I tried glblur and got 15 fps in the window, but that drops to 2 or 3 fps if i go fullscreen - is that the expected performance

---

### Post by gdyne on 2009-12-08
before you do a kernel upgrade you need to run the following

sudo apt-get --purge remove xpsb-glx psb-modules psb-firmware poulsbo-driver-2d poulsbo-driver-3d xserver-xorg-video-psb libdrm-poulsbo1 psb-kernel-source
sudo perl -p -i -e "s/psb/vesa/" /etc/X11/xorg.conf

then re-run any of the scripted poulsbo installs such as this one...

wget [http://poulsbo-karmic.angelfire.com/files/poulsbo1.tar.gz](http://poulsbo-karmic.angelfire.com/files/poulsbo1.tar.gz)

tar -zxvf poulsbo1.tar.gz

cd poulsbo1

sudo ./install.pl

or this one

[http://ubuntuforums.org/showpost.php?p=8182373&postcount=87](http://ubuntuforums.org/showpost.php?p=8182373&postcount=87)

---

### Post by cyclopsface on 2009-12-08
Ok, I reinstalled Ubuntu (9.10) and got the driver and suspend working ok (suspend takes a while to resume but maybe "that's just how it is"

But Sound does not work.  I get the Ubuntu chimes when I boot, but nothing from, say, a youtube video.  Any advice?

---

### Post by pacoros on 2009-12-08
@cyclopsface Can you explain how did you get suspend working? I'm maintaining a post about AOS751h here: [http://pacoros.wordpress.com/2009/10/02/tips-to-make-acer-aspire-one-751h-ao751h-work-better-with-ubuntu/](http://pacoros.wordpress.com/2009/10/02/tips-to-make-acer-aspire-one-751h-ao751h-work-better-with-ubuntu/) and I can't make suspend work with Karmic.

Thanks in advance.

---

### Post by cyclopsface on 2009-12-08
I'm afraid I don't have anyhtingterribly useful to say.  I simply did a fresh install of Ubuntu 9.10 (standard, not NBR) and followed the instructions here: [https://wiki.ubuntu.com/HardwareSupportComponentsVideoCardsPoulsbo](https://wiki.ubuntu.com/HardwareSupportComponentsVideoCardsPoulsbo)

FWIW I used the ppa script (not the ftp one)

Then I followed the advice here: [https://help.ubuntu.com/community/AspireOne/AO751h](https://help.ubuntu.com/community/AspireOne/AO751h) for fixing suspend.

Now suspend works and sound doens't

Let me know if I could help you further

---

### Post by pacoros on 2009-12-09
> **cyclopsface said:**
> I'm afraid I don't have anyhtingterribly useful to say.  I simply did a fresh install of Ubuntu 9.10 (standard, not NBR) and followed the instructions here: [https://wiki.ubuntu.com/HardwareSupportComponentsVideoCardsPoulsbo](https://wiki.ubuntu.com/HardwareSupportComponentsVideoCardsPoulsbo)

FWIW I used the ppa script (not the ftp one)

That's what I (unsuccesfully) did.

> **cyclopsface said:**
> 
Then I followed the advice here: [https://help.ubuntu.com/community/AspireOne/AO751h](https://help.ubuntu.com/community/AspireOne/AO751h) for fixing suspend.

Now suspend works and sound doens't

Uh! I wrote that :-P And now it doesn't work for me.
I think I'll try again step by stem from a fresh install for the third time.

Thanks!

---

### Post by longpolelaxer on 2009-12-09
I have the psb drivers installed however I can not get the screen brightness to adjust using the function keys.  Is there any work-around around this?  I assume this is due to the '        Option          "IgnoreACPI" "yes"' and commenting that line out is a no go.  So is there another way to get around this?

---

### Post by penguin10916 on 2009-12-10
in the power manager thingy, you can adjust the brigtness. I usually have my system setup to dim the screen when it's idle for a small amount of time. The key thing is a keyboard issue, and of all the linux distros I tried on this system, the keys did not work.

---

### Post by cyclopsface on 2009-12-12
@pacoros did you get this working for you?  I had to reinstall Ubuntu and after an update to kernel .16 my laptop will lock up after suspend (it wakes up ok, but the nothing will move or happen and I have to power off manually) 

I tried booting in recover mode and reinstalling the driver (as suggested in the wiki page) but it didn't help.  

Any advice - I really would like to have suspend!!!

---

### Post by krasny on 2009-12-17
Hello

After installing psb driver i don´t have batery status or brightness settings, is there any fix for this problem?

thanks!

---

### Post by fred.warren on 2009-12-29
I have been able to resolve the no sound issue in Karmic with the 2.6.31-14 and 2.6.31-16 kernels. The power_save option for the snd-sda-intel driver needs to be disabled.

[FONT="Courier New"]sudo gedit /etc/modprobe.d/alsa-base.conf[/FONT]

At the bottom of the file you will find these two lines
[FONT="Courier New"]
# Power down HDA controllers after 10 idle seconds
options snd-hda-intel power_save=10 power_save_controller=N[/FONT]

Just comment out the 2nd line and save the file.

[FONT="Courier New"]
#options snd-hda-intel power_save=10 power_save_controller=N[/FONT]

---

### Post by Moichim on 2010-01-05
Oh now its too late... i was following a thread to try to fix the sound by getting rid of pulse audio and i did some stupid moves tring to go back to it, since it didnt help, and in the end i totally erased the desktop (the stupid newbi over here tried to delete esound thinking i installed it in vain hehe )...so any how i had too many problems with ubuntu in this machine: no sound no battery in power manager, the internal microphones didnt work, no compiz after fixing the resolution etc. So i am not going to try again for now. I did try joliclaud, that works out of the box for the GMA500, but i didnt like it too much and it didnt have batteries in the power manager either and the mic didnt work either. a good try was mandriva that worked out of the box but tottaly broke after the first update. well i still prefer ubuntu after all, but I can only hope for things to get better in the future so i can get back to it...

---

### Post by cyclopsface on 2010-01-05
I would recommend going back to 9.04 for the 741h.  I did a fresh install of 9.04, followed the advice in the wiki for installing poulsbo drivers etc., and everything works great: suspend, sound, compiz, etc.  This is the best solution until better drivers are released in the (hopefully near) future.

---

### Post by Reverend G on 2010-01-09
Just for the record I've updated to 2.6.31-17 and no improvement. The sound fix detailed by fred.warren persists after upgrade.

---

### Post by dipodo on 2010-01-09
> **krasny said:**
> Hello

After installing psb driver i don´t have batery status or brightness settings, is there any fix for this problem?

thanks!

I found a way to have the battery status back..... I installed Screenlets via Ubuntu Software Center and then I started "ACPIBattery" screenlet.... When it starts, I also have the battery status back on notification area. At the same time, the screen became less bright. So,  I added the brightness applet on the task bar to control the screen brightness and I made the acpi screenlet to auto start on login.... Now I have the battery status on my notification area every time I log on :)

---

### Post by lucazade on 2010-01-11
> **dipodo said:**
> I found a way to have the battery status back..... I installed Screenlets via Ubuntu Software Center and then I started "ACPIBattery" screenlet.... When it starts, I also have the battery status back on notification area. At the same time, the screen became less bright. So,  I added the brightness applet on the task bar to control the screen brightness and I made the acpi screenlet to auto start on login.... Now I have the battery status on my notification area every time I log on :)

Thanks.. installing "acpi" via apt-get i get back the battery status... great!

---

### Post by chanklor on 2010-01-13
Let's face it, Ubuntu sucks on the Acer AO751H.
And Linux too, I haven't found a good Linux distribution for this Acer model.
It's a shame.
:icon_frown:

---

### Post by Legendário on 2010-01-27
I had to give a presentation with my computer and could not add a second video output (projector). It seems I have to add a standard second projector output on xorg.conf.

Does anyone have an idea of it?

---

### Post by alvaro souza on 2010-02-19
finally after 5 months i made my acer runs ubuntu 9.10 - thanks for the posts.
i read in a brazilian blog about an OS based on Ubuntu 9.04 netbook remix called Jolicloud ([http://www.jolicloud.com/](http://www.jolicloud.com/)) that worked just fine with this netbook.
I didn't tried it, but the user is very satisfied with it.

Link to the page: [http://www.vivaolinux.com.br/dica/Aspire-One-751h-solucao-para-GMA500/](http://www.vivaolinux.com.br/dica/Aspire-One-751h-solucao-para-GMA500/)

---

### Post by Reverend G on 2010-02-20
Checked out Jolicloud; it is just UNR with some lipstick. No new functionality or support for the Ao751h hardware.

I've had similar problems to legendario only I'm trying to connect to a Toshiba 19DV555DB television: made several edits to xorg.conf but ended up just making a mess of the onboard display. I'm still trying though.

---

### Post by Legendário on 2010-03-11
> **Reverend G said:**
> Checked out Jolicloud; it is just UNR with some lipstick. No new functionality or support for the Ao751h hardware.

I've had similar problems to legendario only I'm trying to connect to a Toshiba 19DV555DB television: made several edits to xorg.conf but ended up just making a mess of the onboard display. I'm still trying though.

This happens  because Jolicloud is based on Jaunty, and everything worked well on Jaunty. It must be related to the karmic hal deprecation. Anyways, I want to use karmic on it and I think this topic was created to deal specifically with karmic usage on this hardware, cause all topics were related with jaunty usage.

After upgrading to 2.6.31-20 kernel version, I have been undergoing to a very picking problem. I just can`t uninstall the psb-kernel-headers, or maybe reinstall any other poulsbo related package. This is the error I`ve been going trough:

```
$ sudo aptitude purge psb-kernel-headers
Lendo listas de pacotes... Pronto
Construindo árvore de dependências        
Lendo informação de estado... Pronto
Lendo informações estendidas de estado       
Inicializando estados de pacotes... Pronto
Os pacotes a seguir serão REMOVIDOS:
  psb-kernel-headers{ap} 
0 pacotes atualizados, 0 novos instalados, 1 a serem removidos e 0 não atualizados.
É preciso obter 0B de arquivos. Depois do desempacotamento, 471kB serão liberados.
Você deseja continuar? [Y/n/?] y
Escrevendo informações estendidas de estado... Pronto
(Lendo banco de dados ... 287267 arquivos e diretórios atualmente instalados).
Removendo psb-kernel-headers ...
Nenhum desvio ("diversion") 'any diversion of /usr/include/drm/drm_sarea.h', nenhum removido
Nenhum desvio ("diversion") 'any diversion of /usr/include/drm/drm.h', nenhum removido
Nenhum desvio ("diversion") 'any diversion of /usr/include/drm/drm_hashtab.h', nenhum removido
Nenhum desvio ("diversion") 'any diversion of /usr/include/drm/i915_drm.h', nenhum removido
rm: não foi possível remover `/usr/include/drm-linux-libc': É um diretório
dpkg: erro processando psb-kernel-headers (--purge):
 sub-processo script post-removal instalado retornou estado de saída de erro 1
Erros foram encontrados durante o processamento de:
 psb-kernel-headers
E: Sub-process /usr/bin/dpkg returned an error code (1)
A instalação de um pacote falhou. Tentando recuperar:
Lendo listas de pacotes... Pronto                      
Construindo árvore de dependências       
Lendo informação de estado... Pronto
Lendo informações estendidas de estado       
Inicializando estados de pacotes... Pronto

```

Did anyone go through this problem, and the most important, could solve it well?

---

### Post by Reverend G on 2010-03-12
I didn't have this problem when upgrading to -20 but I was technically using a fresh install when I upgraded.

A few weeks ago I decided to install KDE and XFCE via synaptic to see if they'd run any better or faster than Gnome: it made a grand mess of the system and made me wish I hadn't bothered, so I loaded up my live USB of 9.10, reinstalled Ubuntu (wiping out all the changes I'd made to the OS over the last four months without deleting any of my mail, wireless or browser settings), updated the system to -19, fixed the audio and followed the simple instructions here to get the video working:

[https://wiki.ubuntu.com/HardwareSupportComponentsVideoCardsPoulsbo](https://wiki.ubuntu.com/HardwareSupportComponentsVideoCardsPoulsbo)

After all this the video performance is significantly better than it was before and resetting the video after a kernel update is another single instruction (see the link above again). If nobody has any better suggestions you could give this a try.

I wonder whether 10.04 will be better?

---

### Post by Legendário on 2010-03-15
Poulsbo is pretty sucks under Karmic. I`ve update de kernel and forgot to remove the psb related packages. Now I just can`t fix the video resolution. Is there a solution for that. I just can`t take with this slow video answer anymore. It`s driving me crazy and taking away my produtivity.

---

### Post by chanklor on 2010-03-21
Has anyone tried Lucid? I've tried it and it's the same, incorrect screen resolution.
I didn't update it, maybe after updating... maybe...

---

### Post by crgutierrez on 2010-05-28
anything new under 10.04??????

---

### Post by Reverend G on 2010-05-28
Upgraded (well, clean installed from a USB stick) to Lucid tonight and thus far improvements are minor. Battery monitor seems to be working which is a welcome change; I got rather fed up of not being given a warning before my computer battery fell over in Karmic. Applications I use on a daily basis (Firefox, Evolution, VLC, Gnucash & Rhythmbox) all seem to be running a little bit faster which I'm not going to complain about, and once the instructions are followed here:

[https://help.ubuntu.com/community/AspireOne/AO751h](https://help.ubuntu.com/community/AspireOne/AO751h)

the 1366 x 768 resolution works. One thing I noticed when following the instructions was that in all the script that flashed up while the appropriate files were installing there seemed to be a problem accessing some location or other; it doesn't seem to have made that much of a difference to the way 1366 x 768 works but I thought I'd mention it.

So far so good.

EDIT: Just a few more... niggles. Ubuntu splash screen doesn't display when loading up the OS which 'aint a deal breaker but it's [borg] imperfect [/borg]. Also full screen video playback is a wee bit worse than under fiddled 9.10; I don't think the poulsbo driver utilisation is as good under 10.04 yet but give 'em time and I'm sure it'll improve. Other than that everything seems to be business as usual.

---

### Post by hansvv1 on 2010-05-31
Hi.

I have Lubuntu running on my AA1-751. Pretty fast and much better than Xubuntu. I had problems with the 1368x768 screen, it stayed at 1024x768, a rather large font for every menu and the lack of speed to view video. I tried several forum tips without much effect. Yesterday I found an addition for this machine on the Acer Forum that worked, but I can't find it back again. Anyhow, I don't want you to miss it, since the effect is amazing. Now my Aspire One is a full working notebook with full screen video. 

This is what I did:
Open the terminal
# sudo su
(sudo apt-get upd..... didn't work, so I logged in as superuser.)
# apt-get update && apt-get dist-upgrade
# wget [http://dl.dropbox.com/u/1338581/Gma500/scripts/poulsbo_lucid.sh](http://dl.dropbox.com/u/1338581/Gma500/scripts/poulsbo_lucid.sh) && bash ./poulsbo_lucid.sh
(It will take some time, but that is worth it.)
Reboot. 

Have fun.

---

### Post by Reverend G on 2010-06-02
Logging in as superuser did away with the access problems I reported. After the script executes the resolution is fixed and 2D graphics run OK. 

However video performance is really ticking me off now. As I stated above the utilisation of the Poulsbo drivers in Lucid just isn't as good as under Karmic: after fiddling with VLC's myriad settings the full screen video is still choppy as hell and the Grub2 and Plymouth splash screens require a separate fix which I'm not happy about running. I'm going back to Karmic until some kind soul sorts out the mess.

EDIT: Downloaded and installed Karmic with kernel 2.6.31-14, ran the script to install the GMA500 .deb packages, edited alsa-base.conf to correct the sound problem, updated the system and kernel to 2.6.31-21 via the update manager, re-enabled the drivers for the GMA500 and installed my normal software and the OS is pretty much perfect. I have a working battery monitor and video's now perfect in full screen. Life is sweet.

---

### Post by Udibuntu on 2010-06-05
Guys,

Just tried the gma500 driver at 

[https://wiki.ubuntu.com/HardwareSupportComponentsVideoCardsPoulsbo/#Karmic%20%289.10%29](https://wiki.ubuntu.com/HardwareSupportComponentsVideoCardsPoulsbo/#Karmic%20%289.10%29) 

and broke native resolution.

tried to revert to psb driver, didnt work.

Is there a way to use this method on Karmic AND have native resolution?

---

### Post by Reverend G on 2010-06-11
Karmic and native resolution is certainly possible. What Kernel are you running? Have you upgraded the kernel recently, as this tends to break the native resolution until the psb-kernel-source package is reconfigured.

The instructions that you have linked to have changed recently as the appropriate drivers are now available from the GMA500 PPA: a week ago the instructions described a script to install drivers from another source, and this is what I used to get my system working.

---

### Post by m0dcm on 2010-06-11
> **Reverend G said:**
> Karmic and native resolution is certainly possible. What Kernel are you running? Have you upgraded the kernel recently, as this tends to break the native resolution until the psb-kernel-source package is reconfigured.

The instructions that you have linked to have changed recently as the appropriate drivers are now available from the GMA500 PPA: a week ago the instructions described a script to install drivers from another source, and this is what I used to get my system working.

Compiz isn't working with the new PPA in Karmic!
I still use  'wget [http://dl.dropbox.com/u/1338581/Gma500/scripts/poulsbo.sh](http://dl.dropbox.com/u/1338581/Gma500/scripts/poulsbo.sh) && sh ./poulsbo.sh' and it works nicely. If I need to watch a DVD in VLC or fullscreen video (Flash fullscren is choppy still!) I just disable Compiz and it works a treat

There's rumours that Intel will be releasing a new driver next month, but I am not holding my breath!!!!

---

### Post by hansvv1 on 2010-06-17
> **hansvv1 said:**
> Hi.

I have Lubuntu running on my AA1-751. Pretty fast and much better than Xubuntu. I had problems with the 1368x768 screen, it stayed at 1024x768, a rather large font for every menu and the lack of speed to view video. I tried several forum tips without much effect. Yesterday I found an addition for this machine on the Acer Forum that worked, but I can't find it back again. Anyhow, I don't want you to miss it, since the effect is amazing. Now my Aspire One is a full working notebook with full screen video. 

This is what I did:
Open the terminal
# sudo su
(sudo apt-get upd..... didn't work, so I logged in as superuser.)
# apt-get update && apt-get dist-upgrade
# wget [http://dl.dropbox.com/u/1338581/Gma500/scripts/poulsbo_lucid.sh](http://dl.dropbox.com/u/1338581/Gma500/scripts/poulsbo_lucid.sh) && bash ./poulsbo_lucid.sh
(It will take some time, but that is worth it.)
Reboot. 

Have fun.

Tried this method again since I screwed my Lubuntu. Fresh ISO install, then the update, dist upgrade, etc. This didn't work. Then I skipped the update and dist upgrade. Now everything works fine. Don't know why, but I wanted to let you know.

---

### Post by chanklor on 2010-06-22
> **hansvv1 said:**
> Tried this method again since I screwed my Lubuntu. Fresh ISO install, then the update, dist upgrade, etc. This didn't work. Then I skipped the update and dist upgrade. Now everything works fine. Don't know why, but I wanted to let you know.

I tried that too, now it's in the correct resolution, but the video is still choppy, does anyonw know how to fix that?

---

### Post by moonstar on 2010-09-26
> **fred.warren said:**
> I have been able to resolve the no sound issue in Karmic with the 2.6.31-14 and 2.6.31-16 kernels. The power_save option for the snd-sda-intel driver needs to be disabled.

[FONT="Courier New"]sudo gedit /etc/modprobe.d/alsa-base.conf[/FONT]

At the bottom of the file you will find these two lines
[FONT="Courier New"]
# Power down HDA controllers after 10 idle seconds
options snd-hda-intel power_save=10 power_save_controller=N[/FONT]

Just comment out the 2nd line and save the file.

[FONT="Courier New"]
#options snd-hda-intel power_save=10 power_save_controller=N[/FONT]

This worked for me in 9.10.  A shame the powersaving module is so busted it needs to be disabled, but having sound is appreciated.

Thanks you! ;)

---

### Post by Drojans on 2010-10-01
hi guys, i've been using ubuntu since 5.10 but never had to post a question... till now :|

And guess what... I'm trying to use poulsbo driver with my ao751h-1281 with Ubuntu UNR 9.10 Karmik, to install it I used this [guide]("https://wiki.ubuntu.com/HardwareSupportComponentsVideoCardsPoulsbo/"). I have everything working but the brightness fn keys (fn+left arrow, fn+right arrow). So far I've used the [shortcut keys troubleshooting guide]("https://wiki.ubuntu.com/Hotkeys/Troubleshooting") but that didnt help at all. The combinations doesn't even appear on the screen. Any ideas on what can i do?

PD: My xorg.conf looks like this:
```
Section "Device"
    Identifier "Configured Video Device"
    Option "IgnoreACPI"
    Option "AccelMethod" "uxa"
    Option "MigrationHeuristic" "greedy"
    Option "NoDDC"
    Option "DRI" "on"
    Option "Tiling" "true"
    Driver "psb"
EndSection

Section "DRI"
    Mode 0666
EndSection

Section "Monitor"
    Identifier "Configured Monitor"
EndSection

Section "Screen" 
    Identifier "Default Screen"
    Monitor "Configured Monitor"
    Device "Configured Video Device"
EndSection

```

---

