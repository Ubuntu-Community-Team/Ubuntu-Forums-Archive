---
title: "Computer Failed To Suspend Maverick Meerkat"
date: 2010-10-10
forum: Hardware
---

### Post by powerofpi on 2010-10-10
Hello,

After installing Ubuntu 10.10 x64 today, my laptop will not suspend. The suspend option no longer appears in my indicator applet. If I hit the suspend hotkey on my keyboard, I get the message:

Computer failed to suspend.

Failure was reported as: Cannot suspend

Any ideas? I didn't have a single problem with suspending on 10.04 x64. The ability to sleep is pretty important to me. My laptop is an Acer Aspire 6930.

[UPDATE] I found in another thread that installing laptop-mode-tools automatically removes the pm-utils package, without which my computer will not suspend. I reinstalled pm-utils, but unfortunately that uninstalls laptop-mode-tools. I suggest a bug be written for this, if it has not already.

---

### Post by lores on 2010-10-11
Any hope to continue to use laptop-mode-tools while being able to suspend? ...

---

### Post by powerofpi on 2010-10-11
> **lores said:**
> Any hope to continue to use laptop-mode-tools while being able to suspend? ...

Not that I can tell, but I hope someone posts back to the contrary.

---

### Post by lores on 2010-10-12
Not good... I'd suggest u delete the "SOLVED" tag.

---

### Post by kFYatek on 2010-10-12
On my Toshiba A200-1MB (C2D T5300, Intel 945 with integrated graphics), suspend also broke in Maverick (the 64-bit version). That is, it still works when I boot with 2.6.32 kernel which is a leftover from before the update. On the current 2.6.35-22-generic, when I try to either suspend or hibernate, the computer freezes, and I can only reboot it. Surprisingly (?), SysRq+B does the reboot, which hints that the kernel is still working quite properly.

Anyway, the current 2.6.35-22-generic kernel seems to be a bit "off" overall. First of all, the "quiet" kernel option is not working, and I still get all the boot messages until the splash shows up. Not that I care, I just treat it as a symptom that something is not right.

Nothing interesting in the logs, but when I try to use hibernate, I can see the kernel messages, and the last is:

```
Suspending console(s) (no_console_suspend to debug?)
```

When I booted the system with no_console_suspend appended to kernel options and tried to hibernate, it displayed a couple of messages, and then... was still working, at least I could Alt+Fx to the terminals. When I tried to Alt+F7 back to X, it hanged, though.

I hope for a kernel update in a couple of days... I can live without suspend and hibernation for a while, I don't use them that often, but it would be nice to have them back working.

---

### Post by rnamatrix on 2010-10-12
Yes.I have the same problem. After I reinstall pm-utils, the suspend option appear again. However, the laptop-mode-tools was automatically removed. 
Hope next kernel update would solve it.

---

### Post by lores on 2010-10-12
After removing the laptop-mode-tools package and reinstalling pm-utils and acpi-support, I actually managed to apply laptop-mode-tools directly from [http://samwel.tk/laptop_mode/packages/tarball](http://samwel.tk/laptop_mode/packages/tarball) , but there are multiple issues. At the moment, I am trying to make it "refresh" automatically when AC-state changes (if I run "service laptop-mode start", all settings seem to be applied correctly and the battery-life gain is obvious; but otherwise, the laptop-mode won't get activated nor deactivated).

@rnamatrix: just a few mins ago, there has been a kernel upgrade - nothing changed.

---

### Post by lores on 2010-10-12
OK. I think I got it to work. My quick workaround-howto follows. (Warning: it really is a **quick** workaround - this includes the possibility of multiple errors/omissions in my instructions, as I was recreating them after getting LMT to work).

(You need to have pm-utils and acpi-support installed). "Install" (fortunately, it's just copying over a few scripts, I suppose) LMT from [http://samwel.tk/laptop_mode/packages/tarball](http://samwel.tk/laptop_mode/packages/tarball) (nb: this is a newer version than the one available in the reps; it has one quite noticeable improvement):

```

wget http://samwel.tk/laptop_mode/tools/downloads/laptop-mode-tools_1.55.tar.gz
tar xzf laptop-mode-tools_1.55.tar.gz
su
cd laptop-mode-tools_1.55.tar.gz
./install.sh

```

This allows you to issue "laptop_mode" as root and have LMT automatically detect the AC-state and behave appropriately. If you want to automate this process (which you probably should, as it used to be done automatically in 10.04 with the repo's LMT version and config), you can use my approach. It is redundant, as I find it quite crucial for LMT to always kick in automatically - even if some of the soft fails. You can remvoe redundancy (or shorten the 2nd timeout), thus risking exposure to conflicts/overwrites resulting from pm-utils'/acpi-support's doing equivalent job as LMT.

```

su
nano /etc/acpi/power.sh

```
add 
```
/root/power.sh.4sec
/root/power.sh.70sec
```
directly after
```
#!/bin/sh
```
save with CRTL O and exit with CTRL X

```

nano /etc/pm/sleep.d/10_lm

```
insert
```
#!/bin/sh
sleep 4 && /usr/sbin/laptop_mode auto force > /root/4_pm_log_lm_reload &
```

```
chmod +x /etc/pm/sleep.d/10_lm
nano /etc/pm/sleep.d/10_lm70
```
insert
```
#!/bin/sh
sleep 70 && /usr/sbin/laptop_mode auto force > /root/70_pm_log_lm_reload &
```

```
chmod +x /etc/pm/sleep.d/10_lm70
ln -s /etc/pm/sleep.d/10_lm70 /etc/pm/power.d/10_lm70
ln -s /etc/pm/sleep.d/10_lm /etc/pm/power.d/10_lm

nano /root/power.sh.4sec
```
insert
```
#!/bin/sh
sleep 4 && /usr/sbin/laptop_mode auto force > /root/s4h_power_log_lm_reload &

```

```
nano /root/power.sh.70sec
```
insert
```
#!/bin/sh
sleep 70 && /usr/sbin/laptop_mode auto force > /root/s70h_power_log_lm_reload &

```

```
chmod +x /root/power.sh.*
```

This will force a LMT reload every time the PC changes it's power state (AC/bat) or goes to sleep/resumes. There are to delays: the first one of 4 s and the second one of 70 s, as I experienced LMT's settings' being overwritten after the initial (4 s) reload. Both of them are being executed by both PM and acpid, so there's 2x2x redundancy. After some testing or restricting PM-utils, it probably could be reduced significantly.

Go ahead and customise as you please. The humble "log" files in /root/ along with their timestamps are good for debugging. Check status with "laptop_mode status" (or a shortened version, e. g. "laptop_mode status|head -n 28|tail -n 10").


Let's hope to see a serious solution enter the repos soon...


EDIT:
After testing my workaround for some time, I concluded that it is enough to use pm only (no need for power.sh in acpi, so you can comment out the two lines) and that the second timeout can safely be lowered to 16 s. I'm looking into rerunning "laptop_mode" when the battery's state becomes critical in order to disable data-sensitive features - atm, it doesn't do that automatically.

---

### Post by powerofpi on 2010-10-12
Thank you for the workaround! I've been wondering, why the heck is LMT not installed by default with Ubuntu and integrated along with a nice GUI into the power settings? Without LMT my battery life is considerably worse than Windows, but with it (configured) it's comparable or better. Considering the number of laptops Ubuntu finds its way onto, I would expect this to be a standard feature...

---

### Post by lores on 2010-10-13
I agree. The argument against integrating LMT into Ubuntu used to be compatibility issues (LMT seemed to sometimes hang some PCs; some options didn't work as expected). However, there are multiple options it provides that are very safe while still providing considerable power savings. And even the "hard-core" options would be way easier to enable and test if the soft were installed by default...

BTW: After testing my workaround for some time, I concluded that it is enough to use pm only (no need for power.sh in acpi, so you can comment out the two lines) and that the second timeout can safely be lowered to 16 s. I'm looking into rerunning "laptop_mode" when the battery's state becomes critical in order to disable data-sensitive features - atm, it doesn't do that automatically.

---

### Post by alexyz on 2010-10-18
thanks lores!  worked for me on my new eee pc 1015PEM-PU17.  Just running since this afternoon but can tell already my battery is lasting longer.

one note for anyone trying this:  if you installed laptop-mode-tools (which you probably did if you're reading this), you need to remove that package and reinstall pm-utils and acpi-support, then do the manual install config described above.  I missed that first time through.

---

### Post by lores on 2010-10-19
Glad to have been of help. Any other omissions in my instructions? (I added the hint about pm-utils and acpi-support, thanks).

---

### Post by alexyz on 2010-10-19
one other thing, but probably because I had un-installed pm-utils and acpi-support.  I had to create the power.d directory before making the symlinks

```
sudo mkdir /etc/pm/power.d

```

and apparently, when using sudo chmod wildcards don't work??  never encountered that before...  anyhow to chmod the files in root using sudo I had to use the full filenames

```
sudo chmod +x /etc/pm/power.d/power.sh.4sec /etc/pm/power.d/power.sh.70sec

```

thanks again!

---

### Post by lores on 2010-10-21
OK. I actually advised using "su" instead of "sudo"; one of the reasons for that is exactly the reason why "sudo chmod /root/power.sh.*" didn't work - you don't have read permissions (here: for /root), so you can't enlist the files which would be chmodded with the wildcard.
Another possibility would be:
```

sudo sh -c "chmod +x /root/power.sh.*"

```

---

### Post by alexyz on 2010-10-21
yeah duh that makes sense.

I can't believe how much this improved battery life - it makes an ENORMOUS difference.  If the original poster sees this, you might change the thread name to include "laptop-mode" to make this how-to more findable.

---

### Post by powerofpi on 2011-01-10
> **alexyz said:**
> yeah duh that makes sense.

I can't believe how much this improved battery life - it makes an ENORMOUS difference.

I agree totally... have about 30% more battery life with laptop-mode-tools configured and Lores' workaround in place. :)

---

### Post by lores on 2011-01-10
So this is still an issue, even with the latest updates?

---

### Post by powerofpi on 2011-01-10
> **lores said:**
> So this is still an issue, even with the latest updates?

Yes, tried it this morning from the repos. laptop-mode-tools and pm-utils still remove one another, and I still can't suspend without pm-utils. However, your workaround works like a charm.

---

### Post by lores on 2011-01-10
heh

---

### Post by kotek on 2011-01-22
Great workaround!!

---

### Post by 2ge on 2011-03-11
Another workarround you can find on this site:
[https://bugs.launchpad.net/ubuntu/+source/laptop-mode-tools/+bug/638307](https://bugs.launchpad.net/ubuntu/+source/laptop-mode-tools/+bug/638307)

install this modified verson of pm-utils:
[https://bugs.launchpad.net/ubuntu/+source/laptop-mode-tools/+bug/638307/+attachment/1769623/+files/pm-utils_1.4.1-3_all.deb](https://bugs.launchpad.net/ubuntu/+source/laptop-mode-tools/+bug/638307/+attachment/1769623/+files/pm-utils_1.4.1-3_all.deb)

then install laptop-mode-tools. Probably you want to take this newer Version: [http://samwel.tk/laptop_mode/packages/ubuntu](http://samwel.tk/laptop_mode/packages/ubuntu) since .

At my computer everything is ok until i go to suspend-mode, but after the wake-up there is a significant higher power consumption. Maybe lmt is not working properly after wake up since the power consumption is comparable to the one without lmt. In addition the power-managment says that my battery has about 900Wh and my notebook is using 200W... powertop still gives the exact values, so this problem has to be one of the power-managment applet.

---

### Post by Kbloch on 2011-03-31
Thanks for the investigating this powerofpi. :popcorn:

It solved my problem very nicely, just had to reboot after installing the packages and now it works just fine again.

---

### Post by maxify on 2011-04-18
> **2ge said:**
> Another workarround you can find on this site:
[https://bugs.launchpad.net/ubuntu/+source/laptop-mode-tools/+bug/638307](https://bugs.launchpad.net/ubuntu/+source/laptop-mode-tools/+bug/638307)

install this modified verson of pm-utils:
[https://bugs.launchpad.net/ubuntu/+source/laptop-mode-tools/+bug/638307/+attachment/1769623/+files/pm-utils_1.4.1-3_all.deb](https://bugs.launchpad.net/ubuntu/+source/laptop-mode-tools/+bug/638307/+attachment/1769623/+files/pm-utils_1.4.1-3_all.deb)

then install laptop-mode-tools. Probably you want to take this newer Version: [http://samwel.tk/laptop_mode/packages/ubuntu](http://samwel.tk/laptop_mode/packages/ubuntu) since .

At my computer everything is ok until i go to suspend-mode, but after the wake-up there is a significant higher power consumption. Maybe lmt is not working properly after wake up since the power consumption is comparable to the one without lmt. In addition the power-managment says that my battery has about 900Wh and my notebook is using 200W... powertop still gives the exact values, so this problem has to be one of the power-managment applet.

That is my problem too, have you got any solution yet?
Say I turn on my laptop, it says 2:40 battery left, then I put it asleep and after waking it up I get 1:50, and this number is real - it just won't run for longer than that.

---

