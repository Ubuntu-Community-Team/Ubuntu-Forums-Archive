---
title: "Lenovo 3000 N200 - Suspend &amp; Hibernate Issues"
date: 2007-11-25
forum: Hardware &amp; Laptops
---

### Post by Keithamus on 2007-11-25
Hi all,

I recently purchased a Lenovo 3000 N200 0769 B2G, thats the one with the nVidia Go 7300 graphics card, and fingerprint reader. After about 3 months, Vista decided my legitimate serial was infact, not, and I couldn't use my lovely laptop. So I installed ubuntu, having followed it for the past few years.

I have to say, firstly, fantastic job guys. It feels so beautiful to use, almost everything worked out of the box. One issue was that the install CD commented out my sources.list, so I couldn't install anything, but that was easily fixed. Managed to install compiz, and... wow, its all amazing. Kudos to everyone who put their talents into this, it really shows, and its almost perfect...

Now for the problem, suspend doesnt work at all... Fn+F4 is meant to put it to sleep, and Fn+F12 is meant to suspend to disk. Sleep doesn't work, it just makes the screen go black, and then the lock-screen dialogue pops up. Closing the laptop lid actually sends it to sleep, but when I try and wake it up, i get a black screen and nothing else comes up, no matter what I press (even tried Ctrl Alt F1-7). Hibernate doesnt hybernate, and instead locks the computer, then when I unlock it, it comes up with "Your computer failed to hibernate."

I've looked on the forums and tried a couple of solutions, but I've kind of got lost where I am with it. Anyone have any suggestions?

P.S What is a decent program for getting desktop widgets? gdesklets seems a bit limited, and I see alot about screenlets, but the websites are all down.

P.P.S Is there anything to extend the functionality of the synaptics mouse, I have gsynaptics but it offers little functionality improvements. The windows driver allows you to select the scrollbar area, and have corner keys, and click-drag hold which I especially miss.

Cheers

---

### Post by CazperII on 2007-11-27
I have the exact same laptop. I also did not get suspend and hibernate working. Yesterday I spent several hours on this problem, but didn't have any succes. I was thinking about opening a topic here, but you beat me to it. :) If you resolve the problem please report and make me happy.



For the synaptics mouse, you can adjust the settings manually in /etc/X11/xorg.conf 

I believe the scroll area can be selected with the LeftEdge and RightEdge options in the Synaptics input device section.

Section "InputDevice"
        Identifier      "Synaptics Touchpad"
        Driver          "synaptics"
        Option          "SendCoreEvents"        "true"
        Option          "Device"        "/dev/psaux"
        Option          "Protocol"      "auto-dev"
        Option          "HorizEdgeScroll"       "0"
       [B] Option          "LeftEdge" "1700"
        Option          "RightEdge" "5300"[/B]
EndSection


For more synaptics options (2 finger scroll is really nice) look here:
[http://gentoo-wiki.com/HARDWARE_Synaptics_Touchpad](http://gentoo-wiki.com/HARDWARE_Synaptics_Touchpad)

P.S: Did you get the fingerprint reader working? I believe there are some beta drivers but I haven't tried them out yet.

---

### Post by Keithamus on 2007-11-27
CazperII

Apparently the only software, out of thinkfinger, biometics and fprint that works for our finger print reader (AES2501) is fprint, but it seems to be quite new. More info:

[http://reactivated.net/fprint/wiki/Supported_devices](http://reactivated.net/fprint/wiki/Supported_devices)
[http://reactivated.net/fprint/wiki/Main_Page](http://reactivated.net/fprint/wiki/Main_Page)

Thanks for the info about the touchpad.

Drilling down more into the suspend issue, I tried s2ram, doesnt work at all - went through all of these commands:
[http://en.opensuse.org/S2ram](http://en.opensuse.org/S2ram)

I **think**, for hibernate, you have to have the same amount of Swap as you do Ram, I upgraded mine to 2GB ram, and I just found that out so I've increased my swap to 2GB, and Im gonna hibernate to test; as for suspend...

I know alot of users with the N200 who have suspend issues, so if we can get it down it'd help alot; I'm sure it'd get my girlfriend switching too (she also has the same laptop).

Cheers

---

### Post by rivera151 on 2007-11-27
Start by checking the kernel log.  System-->Administration-->System Log-->kern.log

**Patiently** browse the kernel log.  See if there are any error messages.  This will clue you in about which modules you might need to disable before shutting/down and resuming.  I'd try debugging suspend before delving into hibernate.  If you see anything causing problems, post them here.

---

### Post by Keithamus on 2007-11-27
I have alot of these messages coming up:

ACPI: Looking for DSDT in initramfs... error, file /DSDT.aml not found.

but other than that, I can't see anything out of the ordinary, not that I know what to look for especially.

I'm really getting the idea that the issue is with nvidia drivers... but I'm a newbie really, so Im not sure.

---

### Post by Keithamus on 2007-11-27
Changing my swap space to 2gb did the trick, and I was able to successfully hibernate... atleast the shutting down part, switching on again and my xorg.conf was completely obliterated, luckily I had backed up because of the touchpad. But back to the drawing board I'd say...

---

### Post by rivera151 on 2007-11-27
> **Keithamus said:**
> Changing my swap space to 2gb did the trick, and I was able to successfully hibernate... atleast the shutting down part, switching on again and my xorg.conf was completely obliterated, luckily I had backed up because of the touchpad. But back to the drawing board I'd say...

If you have the "hibernate" package, you should look at the /etc/hibernate/common.conf file and set it to "UnloadModule name-of-nvidia-driver" and "LoadModules auto".

As for the DSDT error, see if [this]("https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.22/+bug/58386") helps.

---

### Post by dendy7h on 2007-11-27
I have an x60 tablet and have similar suspend/hibernate problems, usually ending with me holding down the power button.  I ran across this:

Suspend and Hibernate

The default Ubuntu suspend and resume cycle causes a kernel panic. I got my computer to flawlessly suspend and resume by installing pm-utils

```
sudo apt-get install pm-utils
```

then you can suspend using the command

```
sudo pm-suspend --quirk-s3-bios --quirk-s3-mode
```



which was taken from this website.

[http://www.thinkwiki.org/wiki/Installing_Ubuntu_7.04_(Feisty_Fawn)_on_an_X61_Tablet#Other_x61_install_guides_on_the_web](http://www.thinkwiki.org/wiki/Installing_Ubuntu_7.04_(Feisty_Fawn)_on_an_X61_Tablet#Other_x61_install_guides_on_the_web)

---

### Post by Keithamus on 2007-11-28
That command didnt work for me, don't know if my install is just a particularly screwed up one, or if the laptop is particularly obscure, but nothing seems to work :(

---

### Post by rivera151 on 2007-11-28
> **Keithamus said:**
> That command didnt work for me, don't know if my install is just a particularly screwed up one, or if the laptop is particularly obscure, but nothing seems to work :(

It's not clear if you are referring to the hibernate package or  the pm-utils package that didn't work.  Also, (just in case it wasn't clear in my previous post) make sure that in common.conf you replace "name-of-nvidia-driver" with the actual name of your nvidia driver.  You might also want to experiment with removing kernel modules related to USB, both LAN and WLAN, and sound.  These are common culprits.  Don't give up, it's not easy to get it working but not impossible also.

---

### Post by Keithamus on 2007-11-28
Sorry rivera151, I completely missed your post, I was reffering to the pm-suspend not working, tried all the different quirks and it doesnt work.

Just tried hibernate, had to install it but thought it might be worth trying. It says it cant load blacklisted modules (nvidia), so I put the line in you said about:

```
UnloadModules nvidia
```

Try again and it outputs the following:

```
Some modules failed to unload: nvidia.
```

Nvidia seems like its the **only** problem, as the screen goes black if I run hibernate --force, but throws me back to the desktop with that error, and looking at the logs, I can see it unloading all the other modules successfully.

Any ideas??

---

### Post by CazperII on 2007-11-28
If the Nvidia drivers is causing the lock up there might be some hope yet. In the beta driver (169.04) release of Nvidia I read the following:

...
Worked around a Linux kernel/toolchain bug that caused soft lockup errors when suspending on some Intel systems.
...

look here: [http://www.nvidia.com/object/linux_display_amd64_169.04.html](http://www.nvidia.com/object/linux_display_amd64_169.04.html)

I haven't tried the beta driver yet (kinda dodgy to install because you can't do it when running X), But maybe this could be the solution.

---

### Post by Keithamus on 2007-11-28
How hard is it to get the nvidia drivers working? Don't you have to recompile the kernel or something??

---

### Post by rivera151 on 2007-11-28
> **Keithamus said:**
> How hard is it to get the nvidia drivers working? Don't you have to recompile the kernel or something??

Try the driver fix; the issue seems to have been fixed.

You probably would have to compile a kernel module for it, not your kernel.  The initial setup might take some finetuning, but once you get it set up, compiling the kernel module is actually trivial.  

To get started print out the install instructions (it should be straight forward, its an installer) and see [this]("http://ubuntuforums.org/showthread.php?t=48482") post.

---

### Post by pietermeurs on 2007-11-29
Hey guys,

i've got the same laptop with the same problem. Suspend doesn't seem to work. Unfortunately i'm a complete noob so i don't dare to try these new things. I'll wait till one of you guys finds the solution. Thanks a lot by the way.

I did find this, maybe that helps (didn't try myself).

greetings

ps: the fingerprint-reader: i had software working that could read the fingerprint, but not yet verify if it was correct. Have a look at the 'totally disappointed with my lenovo 3000 n200'-topic. Some links there.

---

### Post by Keithamus on 2007-11-29
CazperII,

I just checked those drivers, and they're for AMD x86, the drivers for intel 32bit are only 100.something and don't list the suspend fix.

Isn't there an easy way to install the drivers, using envy or something?

---

### Post by pietermeurs on 2007-11-29
> **pietermeurs said:**
> 

I did find this, maybe that helps (didn't try myself).



I forgot the url: [http://blog.paulbetts.org/index.php/2007/02/11/fixing-software-suspend-hibernate-with-uswsusp-in-ubuntu-feisty-and-edgy/#comment-875](http://blog.paulbetts.org/index.php/2007/02/11/fixing-software-suspend-hibernate-with-uswsusp-in-ubuntu-feisty-and-edgy/#comment-875)

---

### Post by CazperII on 2007-11-29
The x86 drivers can be found here: [http://us.download.nvidia.com/XFree86/Linux-x86/169.04/NVIDIA-Linux-x86-169.04-pkg1.run](http://us.download.nvidia.com/XFree86/Linux-x86/169.04/NVIDIA-Linux-x86-169.04-pkg1.run)

I tried the Beta driver (amd64 version) and hibernate and suspend still don't work. As a matter of fact, my nvidia driver totally screwed up while installing and when the failsafe driver (VESA) was loaded, I tried to suspend and it still didn't work. My conclusion is that the problem lies elsewhere. 

If you install the Beta driver be sure to back up your Xorg.conf, and I recommend  staying with the stable driver.

---

### Post by Keithamus on 2007-11-30
Im still sure it is something to do with the nvidia drivers; both hibernate-ram and hibernate-disk complain that they can't unload the nvidia module, and the main problem (it seems) for s2ram/disk is that it comes back to a black screen. Some people have suggested doing the following:

```
gksudo gedit /etc/X11/xorg.conf
```

Find your nvidia driver bit, where it says "driver  "nvidia"", and underneath add:

```
Option "NvAGP" "1"
```

Save and close (obviously backing up is a good thing!)

Then go and edit your grub list.

```
gksudo gedit /boot/grub/menu.lst
```

In the bit right at the end, you'll have the 3 boot options, normal, recovery, and memtest; and any extra windows ones. With the normal boot for Ubuntu, you need to add "vga=775". Save and close.

Finally:

```
gksudo gedit /etc/modprobe.d/blacklist
```

Add to the end: ```
blacklist intel_agp
```.

This has got me a bit further, hibernate seems to almost go into hibernation, then bombs out for some other reason I think, s2ram still fails though, but I think we're getting closer.

---

### Post by Keithamus on 2007-12-04
Just thought I'd update and say hibernate is now WORKING for me, using the above guide, then restarting, and then using the default hibernate script.

Slight problem in that the sleep light flashes constantly, upon resume from hibernate.

Sleep is still not working

---

### Post by pietermeurs on 2007-12-04
Does your fan still work after waking up from hibernate?

---

### Post by Keithamus on 2007-12-04
Although I didnt pay attention to it, I'm sure it did work - I sat through an entire lecture with it having booted from hibernate, and it didnt feel hot, and didnt reset.

---

### Post by pietermeurs on 2007-12-04
Have you tried this: 

sudo apt-get install uswsusp
sudo dpkg-divert --rename --divert /usr/sbin/pmi-disabled /usr/sbin/pmi

?

I tried it, but it said something about my swap partition, and as i'm a noob to ubuntu i don't want to mess up things.

thanks!

---

### Post by Keithamus on 2007-12-04
What does it say about your swap partition?

Mine works like this, but I have the same swap as I do memory (2gb for both).

---

### Post by pietermeurs on 2007-12-04
i've got 2gb Ram and something like 2,8 GB swap too.

I cancelled last time when i typed sudo apt-get install uswsusp because i didn't know what to do. Because i tried it again now, it said: 

pieter@pieter-laptop:~$ sudo apt-get install uswsusp
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 

So know i completely don't know what to do.

any tips?

edit: the same when i try to start synaptic

---

### Post by Keithamus on 2007-12-04
Run the code

```
sudo dpkg --configure -a
sudo apt-get update
sudo apt-get install uswsusp
```

---

### Post by pietermeurs on 2007-12-04
so when i type sudo dpkg --configure -a, it says that the swappartition in the uswsusp.conf isn't activitated.

I have to an other swap-space. He asks me if i want to proceed without valid swap space.

What to do?

(thanks for the quick replies)

---

### Post by Keithamus on 2007-12-04
Not sure on this one, sounds like your swap space isnt initiated, but when it asks just continue, ignoring the message and see how far you get. You can always reconfigure it later.

---

### Post by pietermeurs on 2007-12-04
I choose NO and it just said: 
configuring uswsusp (0.6~cvs20070618-1ubuntu2) ...
update-initramfs: Generating /boot/initrd.img-2.6.22-14-generic


In the /etc/uswsusp.conf it says:

# /etc/uswsusp.conf(8) -- Configuration file for s2disk/s2both 
resume device = UUID=a3abf8db-b1d3-48f7-b22a-4f0246f8aa44
splash = y
compress = y
early writeout = y
image size = 977310023
RSA key file = /etc/uswsusp.key
shutdown method = platform

any ideas?

---

### Post by Keithamus on 2007-12-04
Looks fine to me, now try running some of these commands:

```
s2disk
s2ram
s2both
```

See what happens.

---

### Post by pietermeurs on 2007-12-04
nothing happens:

pieter@pieter-laptop:~$ s2disk
s2disk: Could not lock myself. Reason: Cannot allocate memory
pieter@pieter-laptop:~$ s2ram
bash: s2ram: command not found
pieter@pieter-laptop:~$ s2both
/dev/mem: Permission denied
s2both: Could not lock myself. Reason: Cannot allocate memory

I guess i should have chosen Yes in the menu about the valid swap space?

by the way: what's the difference between suspend and hibernate?

---

### Post by CazperII on 2007-12-04
Ok I did all the steps in the previous post (with the blacklist etc). Then installed uswsusp and now s2disk kinda works. I say kinda because it takes a long time to go into a hibernate state, and when waking the laptop back up, it takes almost as much time as a normal boot would take. But hey it's a start. The Default hibernate / sleep still doesn't work. 


pietermeurs: You probably have not activated your swapspace. To check this type in your console: 

```
$ free
```

Your output should look like this:

....
Swap:      2104472      12280    2092192


If total, used and free of swap equals 0 then your swap isn't activated. 

To activate your swap type

```
$ sudo swapon /dev/sdX 
```

with X the number of your swap partition.
If you want to mount your swap everytime you boot add it to /etc/fstab

Reconfigure the uswsusp package now with active swap:

```
$ sudo dpkg-reconfigure uswsusp
```

Finally try again:

```
$ sudo s2disk
```

Your laptop should now power down and when booting back up you should be in the same state as when you started the suspend script.

---

### Post by pietermeurs on 2007-12-05
I get the following:

pieter@pieter-laptop:~$ free
             total       used       free     shared    buffers     cached
Mem:       2074792     776208    1298584          0      64292     399036
-/+ buffers/cache:     312880    1761912
Swap:      2674812          0    2674812
pieter@pieter-laptop:~$ sudo swapon /dev/sd4
[sudo] password for pieter:
swapon: cannot stat /dev/sd4: No such file or directory
pieter@pieter-laptop:~$ sudo swapon /dev/sda4
swapon: /dev/sda4: Device or resource busy

not quite allright i guess...

---

### Post by gryzzly on 2007-12-16
Hi guys, just got my Lenovo 3000 N200, have the same issue with hibernating and sleep modes :(

Isn't it any solution yet? tryed some, nothing seems help;

Hope that somebody will figure it out finally... Thanks

---

### Post by Keithamus on 2007-12-16
Sorry, sleep still doesnt work for me. Hibernate does, you need to have the same swap as you do ram, so for 1gb RAM you need 1gb swap, then follow the instructions from the previous posts. Its still a bit dodgy though, when it wakes up from hibernate, some people have experienced a non-working fan, my laptop's sleep light keeps flashing when it wakes up from hibernate, which can be very irritating.

So short answer is no, sleep and hibernate are still pretty crappy on the N200. Hopefully a fix comes up soon. Enough users need it!

---

### Post by gryzzly on 2007-12-17
> **Keithamus said:**
> Sorry, sleep still doesnt work for me. Hibernate does, you need to have the same swap as you do ram, so for 1gb RAM you need 1gb swap, then follow the instructions from the previous posts. Its still a bit dodgy though, when it wakes up from hibernate, some people have experienced a non-working fan, my laptop's sleep light keeps flashing when it wakes up from hibernate, which can be very irritating.

So short answer is no, sleep and hibernate are still pretty crappy on the N200. Hopefully a fix comes up soon. Enough users need it!

Interesting how solution can come? Just some cool guys will fix it? :) ah, this cool guys. i am ready to pay 10$ to get this issue fixed :)

---

### Post by Keithamus on 2007-12-17
Interesting, maybe would could start a fund to get this sorted. I'd happily pay £10 ($20) to get it sorted. Still cheaper than vista!

Anyone else willing to pay to get it sorted??

---

### Post by gryzzly on 2007-12-19
> **Keithamus said:**
> Interesting, maybe would could start a fund to get this sorted. I'd happily pay £10 ($20) to get it sorted. Still cheaper than vista!

Anyone else willing to pay to get it sorted??

I think we should find users of different laptop, who have same issue. Cuz i am pretty sure that some guys that use IBM laptops, or some other Lenovo models could have same problem. So we could cooperate with them. what do u think?

---

### Post by Keithamus on 2007-12-19
Sounds like a good idea. Lenovo and IBM laptops are the same brand arent they?

I guess we should start a new thread for it.

---

### Post by CazperII on 2007-12-28
I installed the newly released Nvidia driver (169.07) and still the same. Why oh why won't this work? :(

---

### Post by seantm on 2008-01-12
I'm having the same issues with my Lenovo/IBM Thinkpad T61... Can't get hiberante, or suspend to work...If I try to hibernate it shuts down... Part way... When I resume it boots back up and tells that the machine failed to suspend... Sleep doesn't work at all either... Too bad this is otherwise a really solid distro -especially with IBM/Lenovo hardware...

---

### Post by Tharkun007 on 2008-01-13
Hello, Suspend and hibernate now works on my 3000 N200 after upgrading the kernel, by following these steps :
[http://ubuntuforums.org/showthread.php?t=646755](http://ubuntuforums.org/showthread.php?t=646755) . Unfortunately, the wlan doesn't wake up correctly. Maybe this could be easily solved ?
Upgrading solved other issues : Powermizer function now included with the new Nvidia driver, making the fan turn less often. Card Reader works ! Hangs I had with samba transfers disappeared.

A miracle for me !

---

### Post by seantm on 2008-01-13
I'll try it out ---tia!

---

### Post by seantm on 2008-01-13
ok so I went to the link you provided but found another two posts with troubles --not solutions -sorry but could you tell me the title or number of the post please -there are several dealing with kernal modifications... Thanks again... ~S

---

### Post by Tharkun007 on 2008-01-13
> **seantm said:**
> ok so I went to the link you provided but found another two posts with troubles --not solutions -sorry but could you tell me the title or number of the post please -there are several dealing with kernal modifications... Thanks again... ~S
The title of the post is : " Howto: Simple upgrade to Hardy's developing kernel - 2.6.24"

---

### Post by seantm on 2008-01-13
Right -- that helps, thank you!

---

### Post by CazperII on 2008-01-14
I can confirm that sleep works now! This made my day, thx.

---

### Post by pietermeurs on 2008-01-16
Did you simple have to use option #1 of the post? Or did you made other fixes to? I want to do this too, but i don't want to mess up my system.

thanks

---

### Post by Tharkun007 on 2008-01-16
> **pietermeurs said:**
> Did you simple have to use option #1 of the post? Or did you made other fixes to? I want to do this too, but i don't want to mess up my system.

thanks

I've applied the instructions of option #1 and only that. Everything worked after reboot.

---

### Post by pietermeurs on 2008-01-17
Thanks. 

I tried option 1 already and it works perfect. It seems to solve the sleep problem indeed. Wonderful!
Anyone notices other advantages?

---

### Post by CazperII on 2008-01-17
You should try the lsusb command. Apparently the kernel developers are phasing out /proc/bus/usb. If the command returns notihing you should add to fstab:

```

none                                            /proc/bus/usb   usbfs           defaults                        0       0

```

This will fix the problem until Hardy comes out.

---

### Post by gryzzly on 2008-01-19
hey guys, i tried both 1st and manual ( 2nd) option, but after both "sleep" didn't work. Ok, it was some change - now after it woke up it made SOME HORRIBLE SCARY noise (like you hear when microphone is somewhere very close to the speakers), and it didn't recognize my password (login form came and i couldn't login). Also wi-fi disappeared, so now i will try to go back... anyway, if anyone have suggestions, you are more than welcome;

---

### Post by gryzzly on 2008-01-19
wow, thats bad :( now i don't know how to get back and i don't have wi-fi. that's not nice :(

---

### Post by Keithamus on 2008-01-20
Just thought I'd mention than upgrading to hardy has fixed my suspend and hibernate issues!

---

### Post by seantm on 2008-01-20
Well thanks --that's certainly worth knowing... You're using alpha 1-2? --pre release?

---

### Post by seantm on 2008-01-20
Any progress on this issue?

---

### Post by Keithamus on 2008-01-21
Alpha 3. I have a feeling the newer kernel is what has helped, so if you want to keep Fiesty, then perhaps upgrading to the latest kernel will help the issue!

---

### Post by cywhale on 2008-02-15
Hi everybody.
Tried various solutions on my new Lenovo 3000 N200, 1.5Ghz Core Duo with Nvidia 7300. Suspend and resume seem to work depending on the kernel but one major problem persists: the fan does not come up after resuming (occasionally does but only at slow speed, 1 time happened here).

@Keithamus : Does your fan start again after resuming?
 
 **Gutsy kernel, driver "nvidia" (most recent via envy)**
   - Suspend results in black screen after resuming, reboot needed.
    - Hibernating works fine but fan does not come up again -> overheating

**- Gutsy kernel, driver "nv"**
    - Same as with driver "nvidia".

**- Hardy Kernel, driver "nvidia"**
    - Suspend works but fan does not come up again.
    - Hibernate works as in Gutsy, fan does not come up again.

**- uswsusp package. Gutsy kernel, driver "nv"**
    - same results as on Gutsy without uswsusp

Has anyone made any progress in tracking this bug and maybe could provide a solution? Any hints where to look ? 
Is there a _script or daemon we could use_ on resume _to start the fan_ again?

Any help would be appreciated

---

### Post by ekano on 2008-02-15
Hi

Ive got the Lenovo 3000 N200 1.46ghz core duo. I read here that people mention problems regarding the fan. Something about it stops working after reboot and the computer overheats?

I had plans to install win xp on my computer and i saw on lenovos homepage that there are drivers for xp. Do you think it will work to put in XP instead of Vista or will I get the same fan-problem with overheating as a result?

The graphic card is an intel GMA X3100.

Maybe I have missed something in the discussion here, found this site via google. Was this fan-problem only when using Ubuntu or is it the same thing with win XP?

Sorry if I sound like a complete noob.

mvh ekano

---

### Post by Ras1982hun on 2008-04-19
I have the same problem:
Linux Marathon 2.6.24-16-generic #1 SMP Thu Apr 10 13:23:42 UTC 2008 i686 GNU/Linux

N200 with latest BIOS

and fans working only after restart or switch off, after hibernate, not.

Anybody have any solution for this issue?

---

### Post by TadeoDiaz on 2008-06-03
I've been working on this all day and tried everything that I found with nothing working on my Lenovo 3000 v100. I can suspend but upon resume I get a black screen and the computer is unresponsive

I just updated today and still no good.

Who knew switching from windows would be so much work, but I really like this OS. 

Anyone has any other suggestions?

---

### Post by seantm on 2008-06-03
> **TadeoDiaz said:**
> I've been working on this all day and tried everything that I found with nothing working on my Lenovo 3000 v100. I can suspend but upon resume I get a black screen and the computer is unresponsive

I just updated today and still no good.

Who knew switching from windows would be so much work, but I really like this OS. 

Anyone has any other suggestions?
What kernel of Ubuntu have you upgraded to is it Hardy 8.04? 

It's difficult to understand your question: --you write: "I've been working on this all day and tried everything that I found with nothing working" 

Are you referring to the suspend, resume function itself or the entire OS?  Please clarify so we can try to help you.....

---

### Post by TadeoDiaz on 2008-06-04
> **seantm said:**
> What kernel of Ubuntu have you upgraded to is it Hardy 8.04? 

It's difficult to understand your question: --you write: "I've been working on this all day and tried everything that I found with nothing working" 

Are you referring to the suspend, resume function itself or the entire OS?  Please clarify so we can try to help you.....

Sorry, I'm completely new to linux (migrating from Vista) and got too excited while posting.

I am running Hardy 8.04.18 (started with 8.04.16 two days ago) on a Lenovo 3000 V100 0763-44U. I partitioned the hard drive and allocated 11GB to Ubuntu rest is to Vista for the moment (mostly as archive but hope to completely migrate to Linux). Ubuntu is the default startup OS

The problem I am having is with the suspend feature, I can go into suspend but cannot come back from it (get a black screen and unresponsive system). I tried adding ipw3945 to the MODULES variable in /etc/default/acpi-support ([http://blackhold.blogspot.com/2007/10/lenovo-3000-v100-ubuntu-704.html](http://blackhold.blogspot.com/2007/10/lenovo-3000-v100-ubuntu-704.html)) to no success, also tried switching the acpi suspend mode from "s3" to "suspend" and that didn't work either. I tried a few more things in between but I sincerely do not remember exactly what they were. Nothing has worked yet though.

I've yet to try Hibernating, but I figured tackle one problem at a time. Everything else in the system seems to be working right.

Thanks for your help

---

