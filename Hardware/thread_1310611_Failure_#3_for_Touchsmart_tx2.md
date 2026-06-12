---
title: "Failure #3 for Touchsmart tx2"
date: 2009-11-01
forum: Hardware
---

### Post by akand074 on 2009-11-01
Hello, 
I have tried twice before at two different times to follow instructions to get Touch to work on my laptop (Touchsmart tx2) both with epic fails. This time I tried following the instructions on "[http://ubuntuforums.org/showthread.php?p=7863677#post7863677](http://ubuntuforums.org/showthread.php?p=7863677#post7863677)". I scrolled down to the Karmic section and downloaded the patch and typed what I was told to type into the terminal from "[http://ubuntuforums.org/showpost.php?p=8135285&postcount=163"]("http://ubuntuforums.org/showpost.php?p=8135285&postcount=163") and then my laptop just started shutting down on its own but just flashed a screen where it shows the "user-laptop login:" when it shuts down thats new to karmic, or maybe its just me. Either way, does anyone know how I could fix this through the terminal by going into recovery so I can boot back in, I really don't feel like reinstalling ubuntu. Also, if anyone could explain what I'm doing wrong perhaps I just find that every single thread for getting touch to work on the laptop hasn't been very straight forward, its been throwing you from one site to another and its quite confusing. My main concern at the moment is simply getting my ubuntu to boot again, I'll work on the touch after. I just think it could be made a bit more straightforward, I would deffinately start a thread just simply explaining it very well after I manage to get it done myself but until then. I understand many people have been working hard on this and they have definitely been getting somewhere with it in comparison to when I tried a few months back. I'm very thankful to everyone working on it because as of now I have been using windows more than anything on my laptop. Anyways if anyone could help me boot back in it would be greatly appreciated, and maybe I'll try again some other day maybe after reading everything first before starting haha. 
Thank you very much!

PS: I'm running Karmic x64 with Kernal 2.6.31-14

---

### Post by Favux on 2009-11-02
Hi akand074,

Oh boy, I feel bad for you.  It really isn't that hard, I promise.

> I scrolled down to the Karmic section and downloaded the patch and typed what I was told to type into the terminal from
Is that all you did?  Install Nphyx's hid-ntrig.ko, and nothing else?  Did you notice that it's for a 64-bit install?  Do you have 64-bit or 32-bit?  If you look "1) Jaunty: The kernel patches" you see commands to determine the exact kernel you have and whether you're running 32 or 64 bit.

And you could post on the HOW TO you know.  Maybe more help and quicker.

---

### Post by akand074 on 2009-11-02
> **Favux said:**
> Hi akand074,

Oh boy, I feel bad for you.  It really isn't that hard, I promise.


Is that all you did?  Install Nphyx's hid-ntrig.ko, and nothing else?  Did you notice that it's for a 64-bit install?  Do you have 64-bit or 32-bit?  If you look "1) Jaunty: The kernel patches" you see commands to determine the exact kernel you have and whether you're running 32 or 64 bit.

And you could post on the HOW TO you know.  Maybe more help and quicker.

Hey thanks for the reply, yeah thats all I did before my laptop automatically shut itself down and commited suicide! haha I must be doing something wrong, yeah maybe I should try it there. Yeah I have 64 bit Karmic installed with kernel 2.6.31-14 I believe. I just followed the first step where I downloaded the hid-ntrig.ko and ran the code:

```
sudo cp hid-ntrig.ko /lib/modules/2.6.31-14-generic/kernel/drivers/hid
sudo depmod -a
sudo modprobe -r hid_ntrig
sudo modprobe hid_ntrig
```

after typing in the last set of code my Ubuntu shut down on its own and jumped off a cliff. I just want to get my ubuntu booting again and then I guess I'll give it another go and posting directly on that thread for help. Thanks again! Hopefully I won't have to reinstall Karmic, but I'm unaware of how to fix it myself, so it may have to be done :(.

---

### Post by Favux on 2009-11-02
Hi akand074,

Well get to a terminal and see if:
```
ls /lib/modules/2.6.31-14-generic/kernel/drivers
```
shows hid and/or hid-trig.ko.  Then check:
```
ls /lib/modules/2.6.31-14-generic/kernel/drivers/hid
```
and see if hid-ntrig.ko is there.

It looks like there's some typos, it should be hid-ntrig not hid_ntrig.  Do you know which you used?

---

### Post by akand074 on 2009-11-02
Yes I used exactly what I pasted, that may have been it, though how could I do that without being able to get into my ubuntu partition? through the recovery? Could I undo what I just did to fix it? I'll boot into the recovery now and try that. Thank you very much

EDIT:
Alright in the recovery mode I typed in the first set up code and it returned
acpi | dca | hwmon | md | net | rtc |usb
ata | dma | i2c | media | parport | scsi |uwb
atm | edac| idle | memstick | pci | serial |video
auxdisplay | firewire| ieee1394| message| pcmcia | net | spi | virtio
block | firmware | infiniband | mfd | platform | ssb |w1
bluetooth | gpio | input | misc | power | staging | watchdog
char | gpu | isdn | mmc | pps | telephony |xen
crypto | hid | leds | mtd | regulator | uio |

after I input the second set of code I got
hid-a4tech.ko | hid-ezkey.ko | hid-monterey.ko | hid-sunplus.ko
hid-apple.ko | hid- gaff.ko | hid-ntrig.ko | hid-tmff.ko
hid- belkin.ko | hid-gyration.ko | hid-petalynx.ko | hid-topseed.ko
hid-cherry.ko | hid-kensington.ko | hid-pl.ko | hid-wacom.ko
hid-chicony.ko | hid-kye.ko | hid-samsung.ko | hid-spff.ko
hid-cypress.ko | hid-logitech.ko | hid-sjoy.ko | [COLOR=Blue]**usbhid**[/COLOR]
hid-drff.ko |hid-microsoft.ko |hid-sony.ko

Sorry had to type that all out by hand, quite a hassle. What does all this mean? I see the hid-ntrig.ko in there. Should I try something now?

---

### Post by akand074 on 2009-11-02
I powered down my laptop, its very easy to get back to the previous stage if needed, I was going to look up ways to fix my ubuntu but I got caught up watching heroes those damn cliff hangers got me watching episode after episode! haha well I'm starting to think that I'm not going to have to reinstall ubuntu. I find it odd though I typed "hid_ntrig.ko" but what you told me to do showed "hid-ntrig.ko" I wonder what caused the crash.

---

### Post by Ayuthia on 2009-11-02
If you are unable to get into Ubuntu after you did the modprobe for hid-ntrig, I think that the system does not like the kernel module.  You might try the following:
```
sudo mv /lib/modules/$(uname -r)/kernel/drivers/hid/hid-ntrig.ko $HOME
sudo depmod -a
```
Then restart.  What this would do is remove the hid-ntrig kernel module and then rebuild the module list.  I think that since the module is gone, the Wacom driver for X will produce an error message in /var/log/Xorg.0.log, but it should not freeze your laptop.

You might also want to check /var/log/messages to see if there is an error message showing up right before it crashes.  The information might be in /var/log/messages or /var/log/messages.1

If that fixes the crash, you might either try reinstalling the hid-ntrig.ko file or you can try the hid-ntrig.ko file from this [guide]("http://linuxfans.keryxproject.org/?page_id=66").  You would only need the first two steps from the guide.  Instead of doing the modprobe commands, just restart.  Sometimes when X is running and you do the modprobe, it can lock up your computer.

Worst case, you can call Sylar to come and fix it.  Too bad we don't have a Smiles that can imitate that.

---

### Post by Favux on 2009-11-02
Hi Ayuthia,

That's my question.  So just doing a modprobe can break X?  Ok, but why does it persist through a reboot?


Hi akand074,

Using 'sudo' or super user/root can be dangerous because that let's you modify system files.

Using ls (list) lets you look at files before you do anything.  You do have 'hid-ntrig.ko' present where it's suppose to be.

When you're in a terminal or the CLI (command line interface) just type 'man' (manual) in front of the command.  For example "man depmod" shows you:
>        depmod  creates  a  list of module dependencies, by reading each module
       under /lib/modules/version and determining what symbols it exports, and
       what  symbols it needs.  By default this list is written to modules.dep
       in the same directory.
and
>        -a --all  Probe  all  modules.  This option is enabled by default if no
                 file names are given in the command-line.
And for 'man modprobe'
>        modprobe intelligently adds or removes a module from the Linux kernel: note  that  for
       convenience,  there  is no difference between _ and - in module names.
So it turns out that apparently it wasn't due to a typo.  You can also use 'info' before the command or '-h' or '-help' after.  One of those usually gives you info.

---

### Post by akand074 on 2009-11-02
It worked I'm in!! boot up looked a little buggy but booted in fine! I checked the logs and I don't really know how to read it, but nothing seemed out of the ordinary, but I got a red explanation mark that came up saying "sorry, the program "Xorg" closed unexpectedly" haha I'll send the report I guess then I'll try to just do the first two steps and hope it works! Thanks a lot. If it breaks again should I just do the same thing as before? 

Sylar can't help right now, Hiro just stabbed him! Though i think he dragged himself into a well I couldn't tell :S.. I'm not quite sure. Pretty awesome season though but I refuse to start the next one with midterms coming up haha.

---

### Post by akand074 on 2009-11-02
Thanks Favux! Yeah I knew about the -h, not about the manual. But it seemed to have worked out so far, I'm going to try reinstalling n-trig lets see how take 4 goes haha

---

### Post by akand074 on 2009-11-02
AWH no, I was so confident that would work! I followed steps one and two and there was no problems, it did its thing successfully. I restart, and again, won't boot the exact same way as last time haha. I wonder why this is happening if the same instructions have worked for others, I must be missing something. Well anyways back to step 1, fixing ubuntu!

Do you think I should do all the steps on the guide you gave me instead of just the first two?

---

### Post by Ayuthia on 2009-11-02
> **Favux said:**
> Hi Ayuthia,

That's my question.  So just doing a modprobe can break X?  Ok, but why does it persist through a reboot?


The modprobe can break X if the module is faulty in some way.  When the system boots back up and tries to load it again, it is going to crash again.

---

### Post by Ayuthia on 2009-11-02
> **akand074 said:**
> AWH no, I was so confident that would work! I followed steps one and two and there was no problems, it did its thing successfully. I restart, and again, won't boot the exact same way as last time haha. I wonder why this is happening if the same instructions have worked for others, I must be missing something. Well anyways back to step 1, fixing ubuntu!

So when is the system crashing?  Is it when it is about to come to the login?  You might try checking /var/log/Xorg.0.log and see if there is an error message there.

Can you post the results of:
```
uname -a
```It doesn't hurt to verify that it is 64-bit.

EDIT:  I just saw your updated post about whether to do the other steps.  I would wait on it until we can figure out why hid-ntrig is crashing the system.

---

### Post by akand074 on 2009-11-02
No it shows that glowing ubuntu symbol and then crashes before the login screen. I definitely installed a 64 bit version of jaunty, I don't know if maybe the upgrade installed a 32 bit version.. but I don't see why it would do that.

uname-a results in:

Linux andrew-laptop 2.6.31-14-generic #48-Ubuntu SMP Fri Oct 16 14:05:01 UTC 2009 x86_64 GNU/Linux

Also I checked the log, no errors at all, quite a number of warnings though with fglrx but doesn't seem serious.

---

### Post by Favux on 2009-11-02
Hi akand074,

Are you dual booting with Windows?  Is it Win 7?

---

### Post by akand074 on 2009-11-02
> **Favux said:**
> Hi akand074,

Are you dual booting with Windows?  Is it Win 7?

I'm dual booting with Windows Vista still.. it will be with 7 within a week or so whenever my copy gets in. Why would that have any effect? Windows why do you always cause me problems -_-'

---

### Post by Favux on 2009-11-03
Hi akand074,

Well the firmware changes from Vista to Win 7 rc which changes the usb pci by-path in the xorg.conf and causes some other changes according to Ayuthia.  I figure since the Win 7 rc firmware was a little wonky they'd probably change it again for Win 7.  Causing who know's what in Karmic.  Ayuthia?

So let me get this straight.  Both the 64-bit hid-ntrig.ko's from Nphyx and Ayuthia cause your system to crash on boot?

---

### Post by Ayuthia on 2009-11-03
> **Favux said:**
> Hi akand074,

Well the firmware changes from Vista to Win 7 rc which changes the usb pci by-path in the xorg.conf and causes some other changes according to Ayuthia.  I figure since the Win 7 rc firmware was a little wonky they'd probably change it again for Win 7.  Causing who know's what in Karmic.  Ayuthia?

The Vista and the Win 7 RC firmware work with the Wacom driver but the Win 7 RC version does not handle more than one finger.  The newest win 7 firmware does not work with what we currently have patched, but I have a patch ready that will make it work with one finger touch.  The newest firmware changes how the touch is reported, but it reports the two fingers as separate points (and it has space to report up to five fingers but it is not used yet) where the Vista firmware reports the second finger as the distance away from the first finger.

It might be helpful if you can post your /var/log/messages and your /var/log/Xorg.0.log just to see what is happening.  When it crashes and you go into recovery mode, you should copy those files to you home directory so that you can review or attach to the next post.

---

### Post by akand074 on 2009-11-03
> **Favux said:**
> Hi akand074,
 
Well the firmware changes from Vista to Win 7 rc which changes the usb pci by-path in the xorg.conf and causes some other changes according to Ayuthia. I figure since the Win 7 rc firmware was a little wonky they'd probably change it again for Win 7. Causing who know's what in Karmic. Ayuthia?
 
So let me get this straight. Both the 64-bit hid-ntrig.ko's from Nphyx and Ayuthia cause your system to crash on boot?
 
Right, both caused my system to crash on boot. Hmm odd, well I'm still running vista as of now, I'll find Ayuthia's fix after I install 7. 
 
> It might be helpful if you can post your /var/log/messages and your /var/log/Xorg.0.log just to see what is happening. When it crashes and you go into recovery mode, you should copy those files to you home directory so that you can review or attach to the next post. 
 
Alright I will do the two steps you asked me to try before and then when it crashes I'll go into recovery mode and copy the log file and paste it here. Thanks.

---

### Post by akand074 on 2009-11-03
I tried copying the files and apparently it didn't work. What I tried was:
```

cp /var/log/messages
cp /var/log/Xorg.0.log

```

both had errors and wouldn't copy so I put

```

mv /var/log/messages ~/Desktop
mv /var/log/Xorg.0.log ~/Desktop

```

which worked, so I fixed my ubuntu after that and booted in and couldn't find the files.. seems I'm just incompetent with the terminal still -_-' would my log file now be useless? Should I break it again and try to get the logs again?

---

### Post by Ayuthia on 2009-11-03
> **akand074 said:**
> I tried copying the files and apparently it didn't work. What I tried was:
```

cp /var/log/messages
cp /var/log/Xorg.0.log

```

both had errors and wouldn't copy so I put

```

mv /var/log/messages ~/Desktop
mv /var/log/Xorg.0.log ~/Desktop

```

which worked, so I fixed my ubuntu after that and booted in and couldn't find the files.. seems I'm just incompetent with the terminal still -_-' would my log file now be useless? Should I break it again and try to get the logs again?

I don't recall how recovery mode works because I have multiple Linux partitions where I just log into another Linux partition and grab what I want.  Does the recovery mode put you in admin mode automatically or do you just log in from a console prompt?

Next time you might try doing:
```
cp /var/log/messages /home/username/Desktop
cp /var/log/Xorg.0.log /home/username/Desktop
```
Just replace username with your username.  It should show up on your Desktop next time.  My guess is that if you log into the system in recovery mode, the files are still there in the Desktop folder.  I could be wrong about that though.

---

### Post by akand074 on 2009-11-03
I just did it your way and it worked! Yeah recovery mode your in as root automatically. Oh and guess what I wanted to open the files I just copied to my desktop so I went into nautilus as root and guess what I found.. the files I made! haha you were right again. Anyways the files are attached here. Though when I used your guide, my ubuntu didn't crash, its just after the restart it wouldn't boot anymore the same way as before. Does the log still help in this case? Anyways they are posted let me know, thanks a lot!

Sorry the files are exceeding the limit it won't let me attach them, so I put them on my server, here are the links: (I copy pasted them into a new text file because permission was denied otherwise)

[http://a.iyadk.com/Files/Xorg_log.txt](http://a.iyadk.com/Files/Xorg_log.txt)
[http://a.iyadk.com/Files/messages_log.txt](http://a.iyadk.com/Files/messages_log.txt)

Thanks again!

---

### Post by Ayuthia on 2009-11-03
Based on the logs you provided, /var/log/messages shows that the hid-ntrig module did load successfully and Xorg.0.log looks like it is running into problems.

So, the next question seems to be what have you done so far besides install the hid-ntrig.ko file and install the ATI drivers?  Did you remove the xserver-xorg-input-wacom and wacom-tools and installed the patched version?  Have you made any modifications to the .fdi, xorg.conf, or udev files?

---

### Post by akand074 on 2009-11-03
> **Ayuthia said:**
> Based on the logs you provided, /var/log/messages shows that the hid-ntrig module did load successfully and Xorg.0.log looks like it is running into problems.
 
So, the next question seems to be what have you done so far besides install the hid-ntrig.ko file and install the ATI drivers? Did you remove the xserver-xorg-input-wacom and wacom-tools and installed the patched version? Have you made any modifications to the .fdi, xorg.conf, or udev files?
 
No I have done none of that. Well I have on jaunty but it crashed both times I tried altering the Xorg file and removing some wacom.fdi file or something of the sort to get it to work, but it failed so I put back my other xorg file, never put back my wacom.fdi file but again that was all in jaunty before I upgraded. Is there something I should do first?

---

### Post by Ayuthia on 2009-11-03
> **akand074 said:**
> No I have done none of that. Well I have on jaunty but it crashed both times I tried altering the Xorg file and removing some wacom.fdi file or something of the sort to get it to work, but it failed so I put back my other xorg file, never put back my wacom.fdi file but again that was all in jaunty before I upgraded. Is there something I should do first?

If you already have the hid-ntrig.ko file removed from /lib/modules/`uname -r`/drivers/hid/, I am thinking that we might install the original back.  We can save the kernel module for the end.  The current kernel should be enough to make sure that all is ok.

Why don't you try reinstalling linux-image:
```
sudo dpkg-reconfigure linux-image-$(uname -r)
```
Then check and see if a new hid-ntrig.ko file is created:
```
ls -l /lib/modules/$(uname -r)/kernel/drivers/hid/hid-ntrig.ko
```

---

### Post by akand074 on 2009-11-03
Tried that, said that the file or directory could not be found for the second one. I don't think its there because when I went into the recovery and typed the code you told me to type, I think that removes it does it not? The guide you sent me wanted you to get wacom files and such should I just try the other steps as well?

---

### Post by Ayuthia on 2009-11-03
> **akand074 said:**
> Tried that, said that the file or directory could not be found for the second one. I don't think its there because when I went into the recovery and typed the code you told me to type, I think that removes it does it not? The guide you sent me wanted you to get wacom files and such should I just try the other steps as well?

The command does remove the hid-ntrig.ko file.  However, reinstalling the kernel image should have brought back the original hid-ntrig.ko module.  My concern is that the module is able to be loaded, but once it is accessed it ends up crashing the system.  Even if we installed the other items, if the kernel module isn't working, nothing else will either.

EDIT:  I will try to rebuild the original kernel module for you but it might be a little while because I a few errands that I have to get done.

---

### Post by akand074 on 2009-11-03
Thats fine, I have work this evening anyways I'll be leaving to work soon, I'm in no rush really at least I can get back into my linux. Just let me know what I need to do. Thank you very much you've been a great help!

---

### Post by Ayuthia on 2009-11-03
You can try this one.  It is for the 64-bit and the 2.6.31-14.48 (The current version) kernel so it should work for you.  Download the attached file and then:
```
tar -xvjf hid-ntrig-64-31-14.tar.bz2
sudo cp hid-ntrig-64-31-14/hid-ntrig.ko /lib/modules/$(uname -r)/kernel/drivers/hid/
sudo depmod -a
```
You can then restart and hopefully it will boot fine.

---

### Post by akand074 on 2009-11-03
Booted fine! I don't know if the touch screen was supposed to work after that though because it doesn't. But it booted! Was there something I'm supposed to do from here? And thanks again for spending all that time its greatly appreciated.

---

### Post by Ayuthia on 2009-11-03
> **akand074 said:**
> Booted fine! I don't know if the touch screen was supposed to work after that though because it doesn't. But it booted! Was there something I'm supposed to do from here?

That is good to see!  Right now, the touch screen should not be working yet.  The next step be to patch the wacom driver.  You can follow this guide:
[http://ubuntuforums.org/showthread.php?p=6546012#post6546012](http://ubuntuforums.org/showthread.php?p=6546012#post6546012)

That will get the wacom driver setup and configured.  After this portion, the touch screen should start working.  From there, we will need to see how to get the hid-ntrig.ko file working for you so that the touch will respond better.

---

### Post by akand074 on 2009-11-04
Sorry I had lots to do today! I just got through the first part okay, but the part where I had to edit the Xorg.conf file it stopped booting haha. Well what it does is show "andrew-laptop login: " in a black screen, and then I can type in my user name and it asks for a password, so I type that in and it logs me into the command line not as root. Very odd. I'm thinking boot back into live cd and put back my old Xorg.conf file and see what I did wrong. I added this to my file:

Section "InputDevice" 
      Identifier        "stylus" 
      Driver            "wacom" 
      Option "Device" "/dev/input/by-path/pci-0000:00:0b.1-usb-0:2.3:1.0-event-mouse" 
      Option            "Type"           "stylus"
      Option            "USB"            "on" 
      Option            "Button2"        "3"  # make side-switch a right button 
      Option            "TopX"           "225" 
      Option            "TopY"           "225" 
      Option            "BottomX"        "26300" 
      Option            "BottomY"        "16375" 
EndSection 

Section "InputDevice" 
      Identifier        "eraser" 
      Driver            "wacom" 
      Option "Device" "/dev/input/by-path/pci-0000:00:0b.1-usb-0:2.3:1.0-event-mouse" 
      Option            "Type"           "eraser"
      Option            "USB"            "on" 
EndSection 

Section "InputDevice" 
      Identifier        "touch" 
      Driver            "wacom" 
      Option "Device" "/dev/input/by-path/pci-0000:00:0b.1-usb-0:2.3:1.1-event-" 
      Option            "Type"           "touch"
      Option            "USB"            "on" 
      Option            "TopX"           "200" 
      Option            "TopY"           "225" 
      Option            "BottomX"        "4000" 
      Option            "BottomY"        "3875" 
EndSection

Inputdevice       "stylus"         "SendCoreEvents" 
      Inputdevice       "eraser"         "SendCoreEvents" 
      Inputdevice       "touch"          "SendCoreEvents"

---

### Post by Ayuthia on 2009-11-06
Sorry for the late reply.  I have been fixing bugs on my two-finger scroll driver.

There is a link in the post that contains an attached xorg.conf file.  Try this link:
[http://ubuntuforums.org/showpost.php?p=7863677&postcount=1](http://ubuntuforums.org/showpost.php?p=7863677&postcount=1)

and download the Favux_TX2z & XT's_Jaunty_xorg.conf.txt attachment.  That has the X and Y settings that could help.

---

### Post by akand074 on 2009-11-06
That is quite alright, you have been very kind dealing with my incompetence. I went to that thread and downloaded the "Favux_TX2z & XT's_Jaunty_xorg.conf.txt" and I read the thread a bit around that section and if I'm not mistaken its already configured for the TX2z, you would have to switch some things or remove comments for the XT, so I just copy and pasted his xorg.conf right before mine and rebooted. On boot the screen started flashing and thats all it continued doing. I tried just using his (copy pasting it over mine) and that as well did the same thing. I'm sorry I'm having so much trouble and taking up your time! Is there something I'm missing? 

I read a bit more earlier on how the wacom.fdi file should be edited, but it said if you used your method it should be removed all together and I looked in that folder and indeed, it was not there, so I think thats fine. I've been playing around, I wasn't sure if the wacom drivers were patched correctly, I also tried installing tekknokrat's .debs from   [http://ubuntuforums.org/showthread.php?t=996830&page=32](http://ubuntuforums.org/showthread.php?t=996830&page=32)

I changed my xorg.conf file after that, and it was a fail again, wouldn't boot. It must be that my wacom drivers aren't patched correctly. I'm at a point where I'm completely confused as to what has been done and what hasn't been. What I've done so far is everything I was told to try from post one to the last post in this thread. I saw a bunch of the wacom files to patch on my desktop, so I must have done something of the sort earlier, but when I tried to reproduce it I was coming up with "file or directory doesn't exist" errors, so I'm thinking maybe I need to do that correctly?

---

