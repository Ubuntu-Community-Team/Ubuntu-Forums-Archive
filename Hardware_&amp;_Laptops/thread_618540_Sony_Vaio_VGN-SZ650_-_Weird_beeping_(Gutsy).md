---
title: "Sony Vaio VGN-SZ650 - Weird beeping (Gutsy)"
date: 2007-11-20
forum: Hardware &amp; Laptops
---

### Post by sthomas on 2007-11-20
Hi, I've been using Ubuntu on my home desktop for about a year now and I love it! I've had (almost) no problems at all on my desktop, and everything works great.

Just a few days ago I bought a Sony Vaio VGN-SZ650 from Fry's. The first thing I did was load Ubuntu on it, and everything either worked out of the box or I've gotten it to work without too much difficulty: wireless, graphics (including switching between the Intel and Nvidia chipsets), sound via the speakers,etc. There are a few problems I've been having though.

The biggest issue is that my laptop's hard drive emits a faint beep, maybe 5 - 8 times a minute. It's not terribly loud, but just loud and consistent enough to be extremely annoying. Here's some more info:
[LIST]
[*]The beeping doesn't occur under Windows.
[*]The beeping occurs even if I boot into the recovery console.
[*]When I'm in laptop mode and the hard drive spins down, the beeping stops.
[*]The disk light doesn't actually flicker, but the disk makes a bit of noise before each beep, like something is being written or read periodically.
[*]I found [bug 27323]("https://launchpad.net/ubuntu/+source/hal/+bug/27323") on Launchpad, but even following all the advice in the thread (including shutting down hald) doesn't stop the beeping, so I'm not sure if it's the same issue or not.
[/LIST]I don't really expect anyone to have a magical solution to this problem, but I'm wondering if any other Vaio owners are experiencing this. It's really annoying and I still have over a week to return the laptop, which I'm going to do if I can't get this fixed. On that note, can anyone recommend a good small laptop that tends to mostly work out of the box under Ubuntu?

Thanks for any help,
Steve

---

### Post by ljonesj on 2007-11-20
i say you may have a bad harddrive and it is going out but i may be wrong

---

### Post by sthomas on 2007-11-20
It's a brand new laptop (purchased three days ago), and the hard drive seems to function perfectly well other than the beeping. Also under Windows there is no beeping noise, so I'm skeptical that it's really a faulty drive. But it is a possibility I guess.

---

### Post by Convert on 2007-11-26
Steve, hi.  I also have a (relatively new) Sony VGN-SZ650N/C.  I can't help you with the beeping...my drive doesn't beep with Ubuntu (nor with XP nor Vista).

However, I have one problem that would be nice to fix and was wondering if you have the same issue -- the sound from the laptop will not play through headphones.  When I plug in any headphones, the headphones do not have sound and the sound continues to play through the laptop speaker.  Do you have the same issue?

---

### Post by sthomas on 2007-11-26
The beeping was caused by the same hard drive spin up/spin down cycling described in [this]("http://ubuntuforums.org/showthread.php?t=591503") thread. Apparently my Vaio emits a faint beep when the hard drive spins up or spins down, but the solution described by ubuntu_demon in the first post of that thread fixed the problem.[quote="Convert"]When I plug in any headphones, the headphones do not have sound and the sound continues to play through the laptop speaker. Do you have the same issue?[/quote]I can confirm that I have the same exact problem with the headphone jack: when I plug headphones in I continue to get sound from the speakers, but don't get sound from the headphones. I'll have to start researching a fix soon.

I also can't change the screen brightness at all: neither the Function keys nor the gnome panel work for me.

If I can get the headphone jack and the brightness working then I'll be a happy camper. Please post back if you find a solution, and I'll do the same :)

---

### Post by bontakun on 2007-11-26
I have the same VAIO, and I could only change the backlight with a program called xbacklight.  I think it's in the repos.  Haven't gotten the headphone jack to work yet.

Can I ask how you got the stamina/speed modes to work?

---

### Post by sthomas on 2007-11-26
[quote="bontakun"]I have the same VAIO, and I could only change the backlight with a program called xbacklight. I think it's in the repos.[/quote]That worked great, thanks! For anyone else reading this, just do 'sudo apt-get install xbacklight', then run 'xbacklight -set 50' to set the backlight to 50%. Of course you can replace the 50 with whatever you like. Run 'xbacklight -help' for more info.

[quote="bontakun"]Can I ask how you got the stamina/speed modes to work?[/quote]Take a look at [this](http://ariel.vardi.free.fr/ariel//vaiosz.html) page, where Ariel describes how to get the stamina/speed mode switch working in the "Video" section. Basically you create two xorg.conf files, one for the Intel card and one for the Nvidia card, and write a script that detects which card you have activated at startup and sets up the appropriate xorg.conf file.

I used nvidia-xconfig to create my xorg.conf.speed file, and copied Ariel's xorg.conf.stamina file. I'm attaching both files for reference. I needed to append '.txt' to the file names to attach them.

Steve

---

### Post by Convert on 2007-11-26
Well, I never use the stamina side of things as I'm always playing games, however now that you mention it I think I'll switch to see what happens.  I don't see xbacklight in the program list supported by Ubuntu but I may try it after trying everything else.

---

### Post by Convert on 2007-11-26
Well that didn't work too well.  Ubuntu would only boot to the command line.  It couldn't get the video going.  I must have to set up configuration to select the right drivers depending on the position of the switch.  I will tackle that once I get more comfortable with the command line.

---

### Post by sthomas on 2007-11-27
[quote="Convert"]I must have to set up configuration to select the right drivers depending on the position of the switch.[/quote]All I needed was to switch the xorg.conf file based on whether speed or stamina mode is activated, as described on Ariel's web page. You'll need a proper xorg.conf file for the Intel card. You can probably use the one I attached in this thread (which is pretty much the same as Ariel's).

Regarding xbacklight, it seems to work only when the Intel chipset is activated. When using the Nvidia chip I get the message "No outputs have backlight property".

---

### Post by sthomas on 2007-12-02
Some more findings...

I was able to get the headphones to work properly. I added the line "options snd-hda-intel model=vaio" to the end of the file /etc/modprobe.d/alsa-base (I got the idea from [this](http://ubuntuforums.org/showthread.php?p=3846996) thread). After that the headphones worked perfectly. The laptop's speakers are disabled when headphones are plugged in, and enabled when the headphones are unplugged. Sweet! :)

Also, after making that change both the internal microphone and an external microphone via the microphone jack work great.

Suspend/hibernate don't work properly. My laptop never wakes up. Installing kernel 2.6.23 via the instructions on the [master kernel thread](http://ubuntuforums.org/showthread.php?t=311158) fixed this, and both suspend and hibernate worked correctly. Unfortunately my wireless network card (which worked out of the box under Gutsy, possibly via the restricted drivers) doesn't work with the latest kernel, and my attempts to install wireless drivers failed, so I'm going to have to stick with the stock kernel in Gutsy for now. But it's nice to know that suspend/hibernate should be fixed in Hardy.

Some more resources regarding Ubuntu running on a Vaio SZ:
[http://ariel.vardi.free.fr/ariel//vaiosz.html](http://ariel.vardi.free.fr/ariel//vaiosz.html)
[http://moelhave.dk/gnulinux-ubuntu-gutsy-gibbon-710-on-the-sony-vaio-sz6-series/](http://moelhave.dk/gnulinux-ubuntu-gutsy-gibbon-710-on-the-sony-vaio-sz6-series/)

- Steve

---

### Post by thomasm on 2007-12-05
sthomas: I am the maintainer of the second website you linked to. I just wanted to let you know that (as I write on my site) it _is_ possible to make the wireless network adapter work  with 2.6.13, you just have to follow the rather complex installation instructions. What broke in your particular case?

---

### Post by sthomas on 2007-12-05
Hey Thomas, thanks for your excellent site!

[quote="thomasm"]What broke in your particular case?[/quote]
I pretty much just followed the [howto]("http://www.intellinuxwireless.org/index.php?p=iwlwifi&n=howto-iwlwifi"), but when I got to the line './load debug=0x43fff', I got an error from the load script about invalid parentheses. My laptop is at home so I don't have the exact error message on hand unfortunately. I think [other people]("http://ubuntuforums.org/showpost.php?p=2832381&postcount=3") have had this same problem actually. Did you get any errors, or did you use a different method to install the drivers?

Steve

---

### Post by thomasm on 2007-12-05
I don't think I bothered with the load script at all, the important thing is that all the modules is in place and then things should work after a reboot. I honestly don't remember what I did (I may have simply fixed the load script), I will post exact instructions if I install a new kernel sometime. Does
```

modprobe iwl4965

```
and
```

modprobe mac80211

```
work? (after make install and a reboot) If not, you can try adding "-v" to the modprobe command and see if the output gives you any extra information.


- Thomas

---

### Post by sthomas on 2007-12-05
I do recall that I was able to modprobe both iwl4965 and mac80211 with no errors. I think the main issue was that my wireless card wasn't detected. ifconfig didn't report any wlan devices.

---

### Post by bontakun on 2007-12-05
> **sthomas said:**
> 
Suspend/hibernate don't work properly. My laptop never wakes up. Installing kernel 2.6.23 via the instructions on the [master kernel thread](http://ubuntuforums.org/showthread.php?t=311158) fixed this, and both suspend and hibernate worked correctly. Unfortunately my wireless network card (which worked out of the box under Gutsy, possibly via the restricted drivers) doesn't work with the latest kernel, and my attempts to install wireless drivers failed, so I'm going to have to stick with the stock kernel in Gutsy for now. But it's nice to know that suspend/hibernate should be fixed in Hardy.


Thanks for the tip on the headphone jack issue.

I was also lead to the Master Kernel Thread, and after several tries have finally got most things seemingly working.  I wanted to use a 64-bit kernel, and I wanted tickless idle for better battery life, so it turns out I had to step up to kernel 2.6.24-rc3.  Besides that, I manually installed nvidia beta 169.04 drivers.  The kernel interface for that had to be compiled, as did the virtualbox vboxdrv module.  Now I think everything works, including the wireless.  For that, I just had to copy the firmware microcode to /lib/firmware/ and modprobe mac80211 first, then iwl4965.

Oh yeah, I followed the instructions [here](http://ubuntuforums.org/showpost.php?p=3822995) to get the graphics mode to work depending on the switch position.

Hope that helps, good luck.

---

### Post by sthomas on 2007-12-05
> **bontakun said:**
> Now I think everything works, including the wireless.  For that, I just had to copy the firmware microcode to /lib/firmware/ and modprobe mac80211 first, then iwl4965.Thanks. I'll give it another shot then.

> **bontakun said:**
> Oh yeah, I followed the instructions [here](http://ubuntuforums.org/showpost.php?p=3822995) to get the graphics mode to work depending on the switch position.Very cool! The nice thing about that setup is it allows both the Intel and Nvidia cards to use 3D properly. When I installed Ubuntu I did it in speed mode, so it set the Nvidia card up for 3D, but 3D doesn't work on the Intel card in stamina mode (which I use more often). So no Compiz, etc. I'll have to try the procedure in that post.

The one thing I'd really love to get working is brightness controls on the Nvidia card. xbacklight works on the Intel card, but not the Nvidia.

---

### Post by sthomas on 2007-12-06
Yeah I still couldn't get the wireless working under kernel 2.6.23.9. Here's what I did (mostly following the [howto](http://www.intellinuxwireless.org/index.php?p=iwlwifi&n=howto-iwlwifi)): downloaded the microcode and installed it to /lib/firmware. Ran 'modprobe mac80211', no errors. Downloaded the driver (version 1.2.22) and ran make and make install. No errors. Tried running the load script, but got an error: "./load: 4: Syntax error: "(" unexpected". Ran 'modprobe iwl4965', no errors. ifconfig doesn't report any wireless network card. Restarted. ifconfig still doesn't report a wireless card.

I'm not too concerned about it though, since the wireless works fine with the stock Gutsy kernel. The only thing the latest kernel fixed for me was suspend/hibernate, which I can live without for now.

---

### Post by sthomas on 2007-12-06
When using the Nvidia card I was getting a weird black screen flickering. It became more frequent when running Compiz in particular. [A fix](http://www.nvnews.net/vbulletin/showthread.php?t=96673) is described on the nvNews forums. Add ```
options nvidia_new NVreg_Mobile=1 NVreg_RegistryDwords="PerfLevelSrc=0x2222"
```to /etc/modprobe.d/nvidia-kernel-nkc, reboot, and it should be fixed.

---

### Post by Daelyn on 2007-12-06
> **sthomas said:**
> That worked great, thanks! For anyone else reading this, just do 'sudo apt-get install xbacklight', then run 'xbacklight -set 50' to set the backlight to 50%. Of course you can replace the 50 with whatever you like. Run 'xbacklight -help' for more info.

Take a look at [this](http://ariel.vardi.free.fr/ariel//vaiosz.html) page, where Ariel describes how to get the stamina/speed mode switch working in the "Video" section. Basically you create two xorg.conf files, one for the Intel card and one for the Nvidia card, and write a script that detects which card you have activated at startup and sets up the appropriate xorg.conf file.

I used nvidia-xconfig to create my xorg.conf.speed file, and copied Ariel's xorg.conf.stamina file. I'm attaching both files for reference. I needed to append '.txt' to the file names to attach them.

Steve

I suggest you use a more advanced version of the Xorg switch that Ariel describes, and use your own xorgs and not the Ariel ones.

[http://ubuntuforums.org/showthread.php?p=2614800#post2614800](http://ubuntuforums.org/showthread.php?p=2614800#post2614800)

---

### Post by sthomas on 2007-12-06
Yeah that setup is better, because you can get 3D working on both cards. I don't have 3D working on the Intel card now. I'll try it out, thanks.

[quote="Daelyn"]and use your own xorgs and not the Ariel ones.[/quote]I used nvidia-xconfig to generate a suitable xorg.conf for the Nvidia card. Is there a program I can use to generate a good xorg.conf for my Intel card? I installed Ubuntu while the Nvidia card was active, so it didn't make an xorg.conf for my Intel card.

---

### Post by sthomas on 2007-12-08
> **Daelyn said:**
> I suggest you use a more advanced version of the Xorg switch that Ariel describes, and use your own xorgs and not the Ariel ones.

[http://ubuntuforums.org/showthread.php?p=2614800#post2614800](http://ubuntuforums.org/showthread.php?p=2614800#post2614800)

I followed the instructions in that post, and now I have 3D working in both the speed and stamina modes. Thanks! The setup is very nice and simple. The only pain is that I have to remember to update the links when the Nvidia driver gets updated. I already know I'm going to forget.

Unfortunately my Intel card is blacklisted by Compiz (apparently playing videos while running Compiz on this card could crash X), so no Compiz under Intel for me, which isn't all that big a deal.

---

### Post by ntetreau on 2007-12-11
> **sthomas said:**
> Yeah I still couldn't get the wireless working under kernel 2.6.23.9. Here's what I did (mostly following the [howto](http://www.intellinuxwireless.org/index.php?p=iwlwifi&n=howto-iwlwifi)): downloaded the microcode and installed it to /lib/firmware. Ran 'modprobe mac80211', no errors. Downloaded the driver (version 1.2.22) and ran make and make install. No errors. Tried running the load script, but got an error: "./load: 4: Syntax error: "(" unexpected". Ran 'modprobe iwl4965', no errors. ifconfig doesn't report any wireless network card. Restarted. ifconfig still doesn't report a wireless card.

I'm not too concerned about it though, since the wireless works fine with the stock Gutsy kernel. The only thing the latest kernel fixed for me was suspend/hibernate, which I can live without for now.

You should check that the micro code file that you put in /lib/firmware has the right filename.  In my case (2.23.9), the file had to be named

iwlwifi-4965-1.ucode

and not

iwlwifi-4965.ucode

After a reboot, everything worked fine.

Nic

---

### Post by ntetreau on 2007-12-14
I compiled the kernel 2.6.24-rc5 to get the tickless kernel and although it works well, I can't seem to be able to compile the nvidia kernel against it.  I even tried Envy without sucess.  Have you guys been able to install the nvidia drivers against the 2.6.24 series?  Also, I tried the xorg.conf switching script but for some reason, it works when I run it from the terminal but not durin ghte boot sequence, any idea.  Let me know if you'd prefer that I start new thread with these problems.

Thanks!

---

