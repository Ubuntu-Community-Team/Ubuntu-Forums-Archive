---
title: "ALSA driver rollback failed: ubuntu no longer boots!"
date: 2007-02-02
forum: Hardware &amp; Laptops
---

### Post by otakuj462 on 2007-02-02
Hello, I'm using ubuntu edgy eft release and I recently upgraded my alsa to the latest version, 14rc2. Unfortunately, this version did not work as well as the older version that came with Ubuntu, so I tried to roll the driver back according to the instructions found [here]("http://ubuntuforums.org/showthread.php?t=205449"). That is to say, I "make uninstall"ed the 14rc2 alsa-drivers, alsa-util, and alsa-lib packages, then did 
```

#sudo apt-get remove linux-sound-base alsa-base alsa-utils

```
and then:
```

sudo apt-get install linux-sound-base alsa-base alsa-utils

```
Unfortunately, this did not appear to reload the drivers, so I decided to grab the alsa-source package out of apt and reinstall it using the module-helper, exactly was described in the post referenced above. This compiled and installed successfully, and I rebooted my computer.
Unfortunately, Ubuntu would not boot after that. When I start it in normal mode, it gives me an error message:
```

udevd-event[*<some numbers here>*]: run_program: '/sbin/modprobe' abnormal exit

```
It also will not boot in the safe diagnostic mode.

Now, I need to digress a bit to explain what I have tried to do to fix it, and why it is perplexing that it has not worked:
I originally tried to roll back the driver using the alsa version 11 source packages downloaded from the alsa project page. I did this in a way similar to what was described above: I "make uninstalled" the alsa 14rc2 packages, then "make installed" the alsa 11 packages, all without incident. Then, when I went o reboot the system, I also received the exact same error message mentioned above. 
I was able to fix this problem by booting a knoppix CD, chrooting onto my linux partition, navigating to the directory where i kept my alsa 11 folder, and "make uninstall"ing the alsa 11 packages, then "make install"ing the alsa 14rc2 packages again. This fixed the problem, and I was able to boot into a fully-functional OS with a mostly-working sound system.
I have attempted to use this same technique with the source package taken out of apt: I boot into knoppix, chroot into /media/hda2, navigate to /usr/src/modules/alsa-driver, then done "make uninstall", then done "make install" with the alsa 14rc2 packages. Unfortunately, the problem persists.
At the moment, I am stumped. I really hope that the answer isn't to do a full reinstall of ubuntu... I would like to learn why this is not working and learn how to repair it, if possible.
I'd appreciate any advice anyone can give. Thanks.

-Jake

PS: Perhaps a temporary workaround might be simply blacklisting the audio modules so they aren't probed on boot. Unfortunately, I don't know much about Debian init. If anyone could tell me what would be involved in blacklisting these modules (for example, whether I can blacklist alsa-base all at once, or have to blacklist snd, snd-hda-intel, snd-hda-codec, etc. one by one) I would appreciate hearing it. Right now I just need a system that boots.

UPDATE:
I got my system to boot by removing snd-pcm-oss and snd-mixer-oss from /etc/modules. No sound system at the moment though. If anyone has any recommendations as to how I should go about rolling back to the 1.0.11 alsa-driver in a way that won't kill my install, I'd appreciate hearing it. Thanks!

---

### Post by roffo on 2007-02-08
I am also having this exact same problem :(

Will post if I make any progress, thanks for the livecd tip.

---

### Post by otakuj462 on 2007-02-08
I just recently got my sound system back up to fully functional status with the alsa14rc2 drivers and the alsa-utils, alsa-lib and alsa-tools from apt. Please note that I feel like getting it to work was a total fluke, but nevertheless, here's what I did to get it working again and you can try it yourself:
First, get your system bootable again. As I stated above, I managed to get my computer to boot by removing snd-pcm-oss and snd-mixer-oss from /etc/modules. Try that and see if it works.
You may want to run "make uninstall" on alsa-lib and alsa-utils packages... I don't remember if I did this though. Skip it  for now.
Next, run 
```
sudo apt-get --reinstall install linux-sound-base alsa-base alsa-utils libasound2
```
Finally, run "make; sudo make install" on the alsa 14rc2 drivers.
This worked for me; it's working as well as it was before I upgraded, and now it's using newer drivers.
Let me know if you have any success.

-Jake

---

### Post by takabailando on 2008-03-27
I just have this same problem on my HP laptop, which does not boot anymore. I can hear a bit of my HDD spinning slightly during the first few seconds of boot.  I tried the solution above, but nothing happened.... Should I use a rescue CD? I am afraid that it will delete my files...... I apprecaite any help...

---

