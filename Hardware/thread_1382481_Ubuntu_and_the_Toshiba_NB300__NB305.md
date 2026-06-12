---
title: "Ubuntu and the Toshiba NB300 / NB305"
date: 2010-01-16
forum: Hardware
---

### Post by exasperation on 2010-01-16
I recently got a Toshiba NB305 (the brand new model) and being of an Ubuntu persuasion, immediately put Ubuntu 9.10 on it.

What runs out of the box: 

* wifi
* sound
* graphics
* keyboard / mouse / usb / other small things which usually work

What does not work: 

* **sleep** - will not wake up
* hibernate - saves and powers off correctly but will not restore after wake up.  Hangs at the "waking up, please wait..." logo screen.
* bluetooth, though this can be enabled following [this post originally intended for the NB205]("http://ubuntuforums.org/showpost.php?p=8327841") (but it works with the NB305!) 
* software control or hardware keys to control brightness
* pressing the external monitor function key causes the display to not turn back on when you hit it again

What was not tested: 

* wired ethernet, though it seemed to recognize the driver, should work.
* the webcam

-----

Wifi seems to be unstable, and will disconnect under heavy load (Transferring a 400 MB file cut out about a third of the way through.).  It will not reconnect after disconnecting.

For me, the single most pressing issue will be getting sleep working, following that, control over screen brightness and so on would be nice.

By "not working" with sleep, I mean the machine seems to go to sleep correctly, and stays asleep.  When woken, the power button lights up, the fan and hard drive spin up but the screen does not turn on.  I haven't diagnosed it further than that.

---

### Post by sethg on 2010-01-20
Have you had any luck resolving the issues? I got this laptop today and would very much like to trade Windows 7 Starter for Ubuntu Remix, but I'd like at least the brightness controls and the sleep function to work.

Thanks for making at least this post! It's the only info on the net I could find about this awesome little netbook and Ubuntu.

---

### Post by NB305 on 2010-02-05
I also have a NB305 and while I can leave without the screen adjustment, it's pretty tough to live without the suspend/hibernate function working.

I have a feeling that all these may have to do with the driver for the Intel GMA 3150.

---

### Post by bama7474 on 2010-02-05
I just got the nb305-n410BL model and had the same weak wireless signal with frequent drops...I found on this forum how to fix this issue:  Open terminal and install the following backports, this will allow the AR9285 wireless to function properly using Ubuntu Netbook Remix.

sudo apt-get install linux-backports-modules-karmic-generic
sudo apt-get install linux-backports-modules-wireless-karmic-generic
Enjoy a more stable wireless connection!:P

---

### Post by wunna8 on 2010-02-06
When I install Unbuntu 9.10 in my Toshiba Laptop ,display show in small square.

---

### Post by danielius on 2010-02-09
anybody figured out a way to get around that intel card problem? i've noticed that s2disk would solve the hibernate issue, but s2ram doesn't work unfortunately..

---

### Post by hatemben on 2010-03-01
I have a Toshiba NB300 here, bluetooth issue fixed with previous NB205 thread.

I'm still having the same wakeup problem, the netbook take about 10min to wakeup from sleep (So lazy) ! Someone can help to get it fixed ?

---

### Post by bama7474 on 2010-03-01
If they would fix the sleep problem I would be completely satisfied...Not very interested in the hibernate function, but to be able to shut the lid and not use up my batt would be awesome!

---

### Post by hatemben on 2010-03-02
By the way issue confirmed with both Hibernate and Suspend functions.

---

### Post by iggeorgiev on 2010-03-02
Hi,
I have also Toshiba nb300. The susp/hibr problem is not only with the Ubuntu. I tried also Mandriva and that problem stays

---

### Post by linuxgr on 2010-03-08
I can also confirm the suspend/hibernate problem on nb305-n310 with ubuntu 9.10(not netbook remix).

I am not however experiencing connectivity problems with the wifi at all. Only thing, if you go into window$ and disable the wifi adapter (Fn+F8 ), logging in to ubuntu later has the adapter deactivated and unable to reactivate unless you re-login to window$ and do it.

Sound and sound controls work great, other Fn function keys do not work.

I agree that at least only fixing the suspend would be a delight....

Any news if that will happen on the upcoming ubuntu version?


EDIT: Can also confirm wifi instability;losing connection usually when there is a lot of traffic. The backports fix mentioned seems to work, haven't experienced problems since installing backport modules.

---

### Post by skittles86 on 2010-03-09
I've recently bought a toshiba nb305 and immediately put ubuntu karmic on it. I'm very new to this but im learning pretty well, i just have one issue that i cannot fix... I want to ad hoc to my other pc and share internet but everytime i try, it wont allow me to connect... it has the option in network manager and im pretty sure i updated everyting i needed to... any ideas?

---

### Post by ARCTURUS323 on 2010-03-10
I also have this laptop and would like to see a fix for this problem. 
"Hibernate and Suspend"

(for me web-cam works.)

---

### Post by skittles86 on 2010-03-11
i found out that my issue has to deal with encryption. Anytime i try to connect to an encrypted wireless network it asks me over and over again for the password. Occasionally it will completely kill network manager. any ideas anyone? 

> **skittles86 said:**
> I've recently bought a toshiba nb305 and immediately put ubuntu karmic on it. I'm very new to this but im learning pretty well, i just have one issue that i cannot fix... I want to ad hoc to my other pc and share internet but everytime i try, it wont allow me to connect... it has the option in network manager and im pretty sure i updated everyting i needed to... any ideas?

---

### Post by ARCTURUS323 on 2010-03-12
You can't connect to a encrypted network unless its your own or you have the key to use it.

---

### Post by mduffor on 2010-03-16
I just purchased an NB405-N410BL this weekend, and promptly installed Ubuntu Network Remix.  Installing the backpatches fixed the wireless for me.  Webcam works in Cheese, but I haven't tried it elsewhere.  Wired internet works fine of course.

I love the netbook, but wanted to chime in that I'm also running into the suspend/hibernate problem.  s2disk didn't work well for me either (I tested it a couple of times, but need to delve into it further when I have time).  I have not tried TuxOnlce, since it looks like it could take a while to install/compile and test it.  Has anyone tried TuxOnlce on these Toshiba netbooks?

Cheers,
Michael

---

### Post by rhettg on 2010-03-18
There is an open ticket for the suspend issue:
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/508516](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/508516)

Just needs to get some attention.

---

### Post by dusky on 2010-03-19
I followed the exact setup on creating a bootable USB on Mac. But when I put the USB in my Toshiba and tell it to boot from USB, it doesn’t, it goes straight to Windows 7. I checked the USB and it is does behave as an img in Mac so the mounting of the image is correct.

I used Terminal in Mac and followed instructions provided in Ubuntu documentation, so I think my USB is right, but there is some miss communication between USB and Toshiba. Please help!

---

### Post by sodivided on 2010-03-21
I just bought an NB305 and was excited to try out a Linux OS for the first time, but not being able to sleep properly is a deal-breaker... it's a bummer, I was really looking forward to Ubuntu Remix. And 7 Starter is ugh.

Here's hoping there's a fix soon!

---

### Post by seenthelite on 2010-03-22
> **sodivided said:**
> I just bought an NB305 and was excited to try out a Linux OS for the first time, but not being able to sleep properly is a deal-breaker... it's a bummer, I was really looking forward to Ubuntu Remix. And 7 Starter is ugh.

Here's hoping there's a fix soon!

Consider trying Ubuntu 10.04 Beta 1 it has better hardware support for my Laptop than 9.10, in 9.10 resume from suspend no,  in 10.04 yes.

---

### Post by skittles86 on 2010-03-23
even with the password im having issues... the only way for me to adhoc is to leave it open and without security.

---

### Post by DianeInChicoCA on 2010-04-05
Too bad I didn't find this thread before I ordered this Toshiba mini 300 series NB305-N310 today.  I plan to format the disk and install ubuntu netbook remix.

I'm assuming I shut down instead of suspend or hibernate, and then the problem doesn't show up.  Is that correct?

---

### Post by mduffor on 2010-04-09
That's what I'm doing currently; shutting down when I'm done and powering back up when I need to use the netbook again.  It is eating up a lot of my time waiting for it to boot back up from scratch each time, but it does work.  

I tried all the different flag combinations for s2ram, but nothing reliably worked.  I thought I found a combination that did work (S2RAM_OPTS="-f -p -s"), but that only worked once and I wasn't able to reproduce it again. I have not tried to compile and install tuxonice yet, since it seems like quite the pain in the butt to do so.  Has anyone tried tuxonice with the Toshiba NB305 yet?

Cheers,
Michael

---

### Post by hanky on 2010-04-11
I also find myself in this bind. I even thought about returning the netbook and getting another one that works with ubuntu/linux but the NB305 is just an all-around awesome netbook so I will keep it.

With that said, the suspend/sleep issue is pretty serious, and it does get rather hot  in the bottom to be used in one's lap. The solution I've found for the heat problem is to scale the processor down to 1Ghz. That seems to make it cool down some.

Subscribed to thread in case a solution/patch is found for suspend/sleep wakeup problem.

---

### Post by linuxgr on 2010-04-13
hanky, 
I also have the heating problem and it kinda worries me, does anybody know if that can become a big problem?

BTW, how did you reduce the cpu speed?

---

### Post by reuvenb on 2010-04-13
The lack of suspend and support for the hardware brightness keys is not limited to Ubuntu.  I'm currently running openSUSE 11.2 on my NB305 and neither works for me.  The closest I've gotten is to use s2ram -a 1.  That at least turns the display back on, but the kernel never wakes up, and I'm left at a screen with a blinking cursor.

---

### Post by edpare on 2010-04-13
+1 with Toshiba NB305-N410BN-G.  I installed 9.1 netbook remix (Canonical?) and _painfully_ updated over wireless!  Brightness controls do not work, nor does suspend/hibernate.  Will karmic wireless modules work on canonical?  (before I break something):confused:

---

### Post by spacelem on 2010-04-15
This is very annoying. I just bought an nb305 yesterday, only to discover it was hobbled in this way, and Toshiba have no interest in Linux, or fixing the problem.

I thought I had done my research properly. I'll try the beta later on and fingers crossed that it works.

---

### Post by NB305 on 2010-04-15
I've tried both 10.04 beta 1 and beta 2 (via USB) and the same problem - cannot adjust screen brightness and fail to wake - exist.

---

### Post by spacelem on 2010-04-16
Beta 2 didn't work either. I ended up taking it back to the shop (fortunately John Lewis are very understanding). It's a shame, the NB305 is a lovely netbook, but crippled by that flaw. I've now got to look at all the other netbooks, and compare them against the hardware compatibility list this time.

I'm considering the Acer Aspire One 532h, which has better battery life, and smaller, but a much less pleasant keyboard and trackpad (and poorer viewing angles on the screen). On the plus side, I had a look through the forums, and people seem to think it works much better in Linux.

---

### Post by Iscran on 2010-04-16
I was successfully able to install TuxOnIce on my NB300. I'm running ubuntu 9.10 Netbook Remix. How I did this is as follows.

Information in bold text is to be run from a linux terminal. You can find the terminal in the menu at (Applications->Terminal)

1) add the PPA for the tuxonice repo to your apt-get list and update apt
[B]sudo add-apt-repository ppa:tuxonice/ppa
sudo apt-get update
[/B]
2) Run 'uname -r' to get your kernel version. Since mine was running 2.6.31.20-generic unfortnately tuxonice hadn't compiled the kernel for this version yet (Just the patch, which I didn't want to run). So I downgraded to 2.6.31-19-generic by downloading their kernel and telling grub to load that by default.

[B]sudo apt-get install linux-headers-2.6.31-19-generic-tuxonice
[/B]** sudo apt-get install linux-image-2.6.31-19-****generic-****tuxonice**


My grub list didn't want to automatically update itself for some reason so I had to manually run 
[B]
sudo update-grub2[/B]

3) Locate your kernel in your grub list so you can set it to automatically boot to that new tuxonice kernel at boot time.

**sudo gedit /boot/grub/grub.cfg**

Press the pagedown button to locate the entry for "2.6.31-19-generic-tuxonice" near the bottom of the file and count its position in the grub list of other kernels. My value is 2 as my kernel was third in the list of available kernels  (third in the list = 2, first in the list would = 0). I have some other  kernels in there as well so your number may differer.

4) Next you need to edit your default grub boot selection so it automatically selects the correct kernel at boot time.

**sudo gedit /etc/default/grub**

At the top of the file there will be some configuration option which look like this : 

```

GRUB_DEFAULT=0
GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=10

```

Edit the GRUB_DEFAULT option to represent the kernel from earlier, this will make your grub picker automatically select this kernel for boot. If you want to see the option to enter the menu at boot time change the GRUB_TIMEOUT option to be a value in seconds. I find it handy so I set mine to "1" to give me 1 second to press the escape key at boot time and select a different kernel if I need, this is however not required.

5) Update your grub list again so it chooses the correct one at boot time.

**sudo update-grub2**

6) Reboot and run from the terminal (Applications->Terminal)
[B]
uname -r[/B]

It should display your kernel version as 2.6.31-19-generic-tuxonice. If not you didn't pick the correct default number above. You have to resolve this otherwise your hibernate functionality will not work.

7) Finally, install the tuxonice userui which will configure X to use tuxonice by default. 
[B]
sudo apt-get install tuxonice-userui[/B]

This should now install without issue. Change your ubuntu power settings to make your machine hibertnate under all situations instead of standby. 

**System -> Preferences -> Power Management**

Click the 'make default' button and close. 
Close the lid on your laptop. After a second or two you can open it again to see that linux has begun hibernating. Mine shows the ubuntu logo in the centre of the screen and tells me down the bottom what its progress is. 10 seconds later the machine will be off.


Open your lid and press the power button. If you're reading this, hibernate works!
:)

PS: Let me know if anyone gets stuck, I've typed this from memory from yesterdays messing around.


* I had to remove the password keyring file otherwise the nm-applet kept pestering me to put in my password each time I came out of hibernation (Wouldn't do it on normal boot). While this will remove the annoying keyring prompt if you get it, it is a security risk if you're worried about people reading your wifi keys in plain text if they access your laptop hard drive. Does anyone know a better way?
To do this, remove this file and reboot.

sudo rm .gnome2/keyrings/login.keyring

When you reboot, connect to your wifi and input the wifi encryption key (WEP, WPA etc). When prompted for a new keyring password, enter nothing and hit enter.

---

### Post by Iscran on 2010-04-18
Edit : Still working on getting brightness working.

---

### Post by johnlea on 2010-04-22
I tried Jolicloud on my NB300 (from a USB stick) and the brightness keys worked fine but none of the other Fn keys. Jolicloud, as I understand it, is based on earlier Ubuntu release. I checked the list of things loading at startup but found nothing of interest. I didn't check any other  files - totally new to Linux but determined to run it on my NB300!

---

### Post by Iscran on 2010-04-22
> **johnlea said:**
> I tried Jolicloud on my NB300 (from a USB stick) and the brightness keys worked fine but none of the other Fn keys. Jolicloud, as I understand it, is based on earlier Ubuntu release. I checked the list of things loading at startup but found nothing of interest. I didn't check any other  files - totally new to Linux but determined to run it on my NB300!

Checking out their information page it indicates they're running :


[LIST]
[*]Linux 2.6.32.4 (i386)
[*]Linux 2.6.32.4 (Atom Optimized)
[/LIST]
out of the box, that's newer than what ubuntu netbook remix comes with. I'm assuming they bundled the newest x86-intel drivers. I'll install it and have a play when I can.

---

### Post by sobolosrios on 2010-04-25
I also have an nb305 and have the resume from sleep issue.  I seem to have another problem as well, that may or may not be related.  When I boot into UNR it takes a really (as in REALLY) long time to start up.  Most of that time is spend with a blinking cursor in the upper left hand corner.  I haven't timed it exactly, but startup time is at least 5 minutes.  Has this been happening to anyone else?  

Also, my nb305 will awake from s2ram, but it takes 5-10 minutes to do so, much of that time with the wifi LED on, and the power LED indicating that the computer is not sleeping, but without the screen being lit.

ISCRAN,  did you ever successfully compile an alternative kernel?  Did it work?  I'd like to get this problem solved so I am happy to help debug/try things.

Thanks!

---

### Post by Iscran on 2010-04-26
I've got Jolicloud running on mine for the time being just because I need that brightness fix as I'll be traveling soon without access to electricity. TuxOnIce as listed above does get hibernate working perfectly however it's running the slightly older kernel. I didn't have any issues running that kernel with ubuntu netbook remix 9.10 and did so for a week.

Edit: I'm compiling 2.6.33.3 now, I'll see if I can load it under Jolicloud but I'm not sure how it will go as Jolicloud is 9.04 ubuntu. I probably should have kept both installs, oops.

Edit: If anyone else wants to give it a go follow the instructions at
[http://ubuntuforums.org/showthread.php?t=311158](http://ubuntuforums.org/showthread.php?t=311158) and for the step 7 apply the patch mentioned here [http://www.tuxonice.net/HOWTO-2.html#ss2.4](http://www.tuxonice.net/HOWTO-2.html#ss2.4) then skip to step 9.

---

### Post by sobolosrios on 2010-04-26
Hi Iscran,

I tried to compile 2.6.33.3 today using KernelCheck and it lead to a kernel panic (and subsequent usb-booting and chrooting to get the old kernel back) before anything boots.  I haven't had time to debug what went wrong, but I wonder if it has to do with KernelCheck assuming that I wanted to compile a 64bit kernel (since the n450 is 64bit) when in fact I wanted to compile a 32bit kernel.  I didn't even think to check on that.  

Would it be possible to take the compiled kernel from Jolicloud and us it in UNR?  I have a slight preference for  UNR over Jolicloud, but either way I would really like to get s2ram working.  If not, then I'll use tuxonice to get s2disk working.  

Like you I am going on a trip in about 2 weeks (across an ocean) and would like to get this working before that time.

Thanks for all of your help.

---

### Post by Iscran on 2010-04-27
I only have Joli loaded at the moment to see if I could find why it has working ACPI and ubuntu netbook doesn't (Screen brightness control). Unfortunately the s2ram doesn't work under Jolicloud either. Unlike UNR 9.10 it doesn't even wake up after about 10 minutes which is frustrating so I'm going to ditch it and give some debugging a go on Ubuntu 10.04 when it comes out in 3 days time.

As far as my debugging went earlier when I was running UNR 9.10 the log file for suspend was complaining that it couldn't bring the video drivers back online which seemed to be the cause of it coming out of s2ram and not waking up the LCD. I wonder if network activity comes online while you're waiting for the screen to turn on?

The next thing I was going to try after getting the brightness working on UNR 9.10 was to update the xf86 intel drivers to the latest. I'll blow away my joli install tonight and put UNR back on to do some testing of these intel drivers. I don't know if this will screw up the ubuntu intel drivers or not so I would advise not to try if you have any important data on your laptop.

If you don't mind experimenting though I was going to follow these instructions  [http://www.tuxfiles.org/linuxhelp/softinstall.html](http://www.tuxfiles.org/linuxhelp/softinstall.html) to install this update [http://xorg.freedesktop.org/archive/individual/driver/xf86-video-intel-2.11.0.tar.bz2](http://xorg.freedesktop.org/archive/individual/driver/xf86-video-intel-2.11.0.tar.bz2)


Edit: I finished my compiling and am running 2.6.33.3 on my normal laptop, all working ok so far though I never had any compatibility issues on this laptop to begin with. I'll transfer the kernel to the netbook and see if it boots shortly.

Edit: I compiled the above under ubuntu 8.04, however I didn't use the kernelcheck script. I compiled for i386, which is the flavor of 8.04 ubuntu I'm running, it chose that automatically during the make.

---

### Post by sobolosrios on 2010-04-27
I'm currently running the lucid release candidate, but I'll try the new intel drivers to see if those work.  Unfortunately, I don't have a usb with 9.10 on it so I can't go back to it very easily.

---

### Post by sobolosrios on 2010-04-27
fyi: I've found that one can get pre-compiled ubuntu kernels (including ones not in the official release) from here:

[http://kernel.ubuntu.com/~kernel-ppa/mainline/](http://kernel.ubuntu.com/~kernel-ppa/mainline/)

I'm trying one out now to try and fix a boot problem with the Lucid RC

---

### Post by Iscran on 2010-04-27
damn, I was compiling the kernel as a test on the NB300 and it ran out of power =(
I'll have to try again when I get home. Not having sleep or hibernate sucks

I was compiling mine to include the code for tuxonice just incase. I was using the kernel configuration from jolicloud as there may be a package included in the kernel it runs that isn't included in UNR 9.10 or 10.04 by default to give access to ACPI brightness control.

---

### Post by sobolosrios on 2010-04-27
Last post for tonight.

I've installed the new intel video driver and it doesn't solve the problem on the stock Lucid kernel (2.6.32-21-generic), although video does appear to be a bit snappier (I may be making that up.)

I'm a little skeptical that the new drivers will work on a newer kernel because the problem seems to be deeper than just video.  In particular, (at least with me) when I open the lid I can't get the Caps Lock LED to light before wake up, suggesting that the kernel is unresponsive and not just the video.  

Since my kids are sick, I'm up late running experiments on this.  Here is something interesting that I noted.  The /var/log/kern.log is appended below for completeness.

1.  At just after 1:21am (by the system clock) I put the system to sleep by closing the lid.  The start of the suspend process can be seen at 1:21:04.

2.  It took about 7 seconds for the led on the computer's front to begin blinking as though the computer were asleep.

3.  From the time the led began blinking I waited approximately sixty seconds and then opened the laptop lid and pressed the power button once, pressing no other buttons until the system awoke (and I was prompted to give my password).  This awakening happened at about 1:28 by the system's time.

It is interesting to note that if the times in kern.log are correct, the system didn't completely go to sleep until just before it awoke itself when the lid was opened.

I don't know what to make of the kernel warning given at 1:21, but that happens right before the 7 minute delay (actually about 6 from the time that I opened the lid) that transpires before the screen becomes backlit.







kern.log:


```
Apr 27 01:03:13 netbook kernel: [ 1123.316097] wlan0: no IPv6 routers present
Apr 27 01:21:04 netbook kernel: [ 2197.640933] CPU0 attaching NULL sched-domain.
Apr 27 01:21:04 netbook kernel: [ 2197.640945] CPU1 attaching NULL sched-domain.
Apr 27 01:21:05 netbook kernel: [ 2197.672182] CPU0 attaching sched-domain:
Apr 27 01:21:05 netbook kernel: [ 2197.672190]  domain 0: span 0-1 level SIBLING
Apr 27 01:21:05 netbook kernel: [ 2197.672197]   groups: 0 (cpu_power = 589) 1 (cpu_power = 589)
Apr 27 01:21:05 netbook kernel: [ 2197.672209]   domain 1: span 0-1 level MC
Apr 27 01:21:05 netbook kernel: [ 2197.672215]    groups: 0-1 (cpu_power = 1178)
Apr 27 01:21:05 netbook kernel: [ 2197.672225] CPU1 attaching sched-domain:
Apr 27 01:21:05 netbook kernel: [ 2197.672230]  domain 0: span 0-1 level SIBLING
Apr 27 01:21:05 netbook kernel: [ 2197.672235]   groups: 1 (cpu_power = 589) 0 (cpu_power = 589)
Apr 27 01:21:05 netbook kernel: [ 2197.672246]   domain 1: span 0-1 level MC
Apr 27 01:21:05 netbook kernel: [ 2197.672251]    groups: 0-1 (cpu_power = 1178)
Apr 27 01:21:05 netbook kernel: [ 2197.738946] ata1: exception Emask 0x10 SAct 0x0 SErr 0x50000 action 0xe frozen
Apr 27 01:21:05 netbook kernel: [ 2197.738958] ata1: irq_stat 0x00400000, PHY RDY changed
Apr 27 01:21:05 netbook kernel: [ 2197.738969] ata1: SError: { PHYRdyChg CommWake }
Apr 27 01:21:05 netbook kernel: [ 2197.738984] ata1: hard resetting link
Apr 27 01:21:05 netbook kernel: [ 2198.468121] ata1: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
Apr 27 01:21:05 netbook kernel: [ 2198.483729] ata1.00: configured for UDMA/100
Apr 27 01:21:05 netbook kernel: [ 2198.483743] ata1: EH complete
Apr 27 01:21:06 netbook kernel: [ 2198.892177] wlan0: deauthenticating from 00:1a:70:5a:64:72 by local choice (reason=3)
Apr 27 01:21:06 netbook kernel: [ 2198.944622] ------------[ cut here ]------------
Apr 27 01:21:06 netbook kernel: [ 2198.944655] WARNING: at /build/buildd/linux-2.6.32/net/wireless/core.c:614 wdev_cleanup_work+0xa7/0xd0 [cfg80211]()
Apr 27 01:21:06 netbook kernel: [ 2198.944662] Hardware name: TOSHIBA NB305
Apr 27 01:21:06 netbook kernel: [ 2198.944666] Modules linked in: binfmt_misc ppdev joydev snd_hda_codec_realtek snd_hda_intel fbcon tileblit font bitblit softcursor snd_hda_codec snd_hwdep snd_pcm_oss snd_mixer_oss vga16fb vgastate snd_pcm snd_seq_dummy snd_seq_oss snd_seq_midi arc4 snd_rawmidi snd_seq_midi_event snd_seq snd_timer snd_seq_device i915 ath9k drm_kms_helper mac80211 snd uvcvideo drm ath cfg80211 soundcore videodev v4l1_compat psmouse serio_raw led_class intel_agp snd_page_alloc agpgart i2c_algo_bit video output lp parport usb_storage r8169 mii ahci
Apr 27 01:21:06 netbook kernel: [ 2198.944746] Pid: 2269, comm: events/1 Tainted: G        W  2.6.32-21-generic #32-Ubuntu
Apr 27 01:21:06 netbook kernel: [ 2198.944752] Call Trace:
Apr 27 01:21:06 netbook kernel: [ 2198.944767]  [<c014c3d2>] warn_slowpath_common+0x72/0xa0
Apr 27 01:21:06 netbook kernel: [ 2198.944784]  [<f8551ea7>] ? wdev_cleanup_work+0xa7/0xd0 [cfg80211]
Apr 27 01:21:06 netbook kernel: [ 2198.944801]  [<f8551ea7>] ? wdev_cleanup_work+0xa7/0xd0 [cfg80211]
Apr 27 01:21:06 netbook kernel: [ 2198.944810]  [<c014c41a>] warn_slowpath_null+0x1a/0x20
Apr 27 01:21:06 netbook kernel: [ 2198.944828]  [<f8551ea7>] wdev_cleanup_work+0xa7/0xd0 [cfg80211]
Apr 27 01:21:06 netbook kernel: [ 2198.944837]  [<c016369e>] run_workqueue+0x8e/0x150
Apr 27 01:21:06 netbook kernel: [ 2198.944855]  [<f8551e00>] ? wdev_cleanup_work+0x0/0xd0 [cfg80211]
Apr 27 01:21:06 netbook kernel: [ 2198.944864]  [<c01637e4>] worker_thread+0x84/0xe0
Apr 27 01:21:06 netbook kernel: [ 2198.944872]  [<c0167740>] ? autoremove_wake_function+0x0/0x50
Apr 27 01:21:06 netbook kernel: [ 2198.944880]  [<c0163760>] ? worker_thread+0x0/0xe0
Apr 27 01:21:06 netbook kernel: [ 2198.944887]  [<c01674b4>] kthread+0x74/0x80
Apr 27 01:21:06 netbook kernel: [ 2198.944894]  [<c0167440>] ? kthread+0x0/0x80
Apr 27 01:21:06 netbook kernel: [ 2198.944903]  [<c0104087>] kernel_thread_helper+0x7/0x10
Apr 27 01:21:06 netbook kernel: [ 2198.944908] ---[ end trace 5be5e461fee0012f ]---
Apr 27 01:28:02 netbook kernel: [ 2199.401411] PM: Syncing filesystems ... done.
Apr 27 01:28:02 netbook kernel: [ 2199.437122] PM: Preparing system for mem sleep
Apr 27 01:28:02 netbook kernel: [ 2199.437130] Freezing user space processes ... (elapsed 0.00 seconds) done.
Apr 27 01:28:02 netbook kernel: [ 2199.438679] Freezing remaining freezable tasks ... (elapsed 0.00 seconds) done.
Apr 27 01:28:02 netbook kernel: [ 2199.440452] PM: Entering mem sleep
Apr 27 01:28:02 netbook kernel: [ 2199.440472] Suspending console(s) (use no_console_suspend to debug)
Apr 27 01:28:02 netbook kernel: [ 2199.501182] sd 0:0:0:0: [sda] Synchronizing SCSI cache
Apr 27 01:28:02 netbook kernel: [ 2199.912141] sd 0:0:0:0: [sda] Stopping disk
Apr 27 01:28:02 netbook kernel: [ 2202.147637] PM: suspend of drv:sd dev:0:0:0:0 complete after 2646.457 msecs
Apr 27 01:28:02 netbook kernel: [ 2202.635644] PM: suspend of drv:psmouse dev:serio1 complete after 459.534 msecs
Apr 27 01:28:02 netbook kernel: [ 2202.740109] PM: suspend of drv:atkbd dev:serio0 complete after 104.454 msecs
Apr 27 01:28:02 netbook kernel: [ 2202.744998] ath9k 0000:07:00.0: PCI INT A disabled
Apr 27 01:28:02 netbook kernel: [ 2202.840124] ehci_hcd 0000:00:1d.7: PCI INT A disabled
Apr 27 01:28:02 netbook kernel: [ 2202.840139] uhci_hcd 0000:00:1d.3: PCI INT D disabled
Apr 27 01:28:02 netbook kernel: [ 2202.840151] uhci_hcd 0000:00:1d.2: PCI INT C disabled
Apr 27 01:28:02 netbook kernel: [ 2202.840163] uhci_hcd 0000:00:1d.1: PCI INT B disabled
Apr 27 01:28:02 netbook kernel: [ 2202.840175] uhci_hcd 0000:00:1d.0: PCI INT A disabled
Apr 27 01:28:02 netbook kernel: [ 2202.944474] HDA Intel 0000:00:1b.0: PCI INT A disabled
Apr 27 01:28:02 netbook kernel: [ 2202.944526] ACPI handle has no context!
Apr 27 01:28:02 netbook kernel: [ 2202.960109] PM: suspend of drv:HDA Intel dev:0000:00:1b.0 complete after 119.911 msecs
Apr 27 01:28:02 netbook kernel: [ 2202.992329] PM: suspend of devices complete after 3551.581 msecs
Apr 27 01:28:02 netbook kernel: [ 2202.992337] PM: suspend devices took 3.556 seconds
Apr 27 01:28:02 netbook kernel: [ 2202.992862] r8169 0000:09:00.0: PME# enabled
Apr 27 01:28:02 netbook kernel: [ 2203.012106] r8169 0000:09:00.0: wake-up capability enabled by ACPI
Apr 27 01:28:02 netbook kernel: [ 2203.044408] PM: late suspend of devices complete after 52.062 msecs
Apr 27 01:28:02 netbook kernel: [ 2203.044457] ACPI: Preparing to enter system sleep state S3
Apr 27 01:28:02 netbook kernel: [ 2203.088025] Disabling non-boot CPUs ...
Apr 27 01:28:02 netbook kernel: [ 2203.088058] CPU0 attaching NULL sched-domain.
Apr 27 01:28:02 netbook kernel: [ 2203.088066] CPU1 attaching NULL sched-domain.
Apr 27 01:28:02 netbook kernel: [ 2203.152030] CPU0 attaching NULL sched-domain.
Apr 27 01:28:02 netbook kernel: [ 2203.256032] CPU 1 is now offline
Apr 27 01:28:02 netbook kernel: [ 2203.256037] SMP alternatives: switching to UP code
Apr 27 01:28:02 netbook kernel: [ 2203.261772] Extended CMOS year: 2000
Apr 27 01:28:02 netbook kernel: [ 2203.261772] Back to C!
Apr 27 01:28:02 netbook kernel: [ 2203.261772] CPU0: Thermal monitoring handled by SMI
Apr 27 01:28:02 netbook kernel: [ 2203.261772] Extended CMOS year: 2000
Apr 27 01:28:02 netbook kernel: [ 2203.261772] Enabling non-boot CPUs ...
Apr 27 01:28:02 netbook kernel: [ 2203.261772] SMP alternatives: switching to SMP code
Apr 27 01:28:02 netbook kernel: [ 2203.267006] Booting processor 1 APIC 0x1 ip 0x6000
Apr 27 01:28:02 netbook kernel: [ 2203.260967] Initializing CPU#1
Apr 27 01:28:02 netbook kernel: [ 2203.260967] CPU: L1 I cache: 32K, L1 D cache: 24K
Apr 27 01:28:02 netbook kernel: [ 2203.260967] CPU: L2 cache: 512K
Apr 27 01:28:02 netbook kernel: [ 2203.260967] CPU: Physical Processor ID: 0
Apr 27 01:28:02 netbook kernel: [ 2203.260967] CPU: Processor Core ID: 0
Apr 27 01:28:02 netbook kernel: [ 2203.260967] CPU1: Thermal monitoring enabled (TM1)
Apr 27 01:28:02 netbook kernel: [ 2203.356057] CPU1: Intel(R) Atom(TM) CPU N450   @ 1.66GHz stepping 0a
Apr 27 01:28:02 netbook kernel: [ 2203.356175] CPU0 attaching NULL sched-domain.
Apr 27 01:28:02 netbook kernel: [ 2203.384034] CPU0 attaching sched-domain:
Apr 27 01:28:02 netbook kernel: [ 2203.384042]  domain 0: span 0-1 level SIBLING
Apr 27 01:28:02 netbook kernel: [ 2203.384049]   groups: 0 (cpu_power = 589) 1 (cpu_power = 589)
Apr 27 01:28:02 netbook kernel: [ 2203.384064]   domain 1: span 0-1 level MC
Apr 27 01:28:02 netbook kernel: [ 2203.384070]    groups: 0-1 (cpu_power = 1178)
Apr 27 01:28:02 netbook kernel: [ 2203.384082] CPU1 attaching sched-domain:
Apr 27 01:28:02 netbook kernel: [ 2203.384087]  domain 0: span 0-1 level SIBLING
Apr 27 01:28:02 netbook kernel: [ 2203.384094]   groups: 1 (cpu_power = 589) 0 (cpu_power = 589)
Apr 27 01:28:02 netbook kernel: [ 2203.384107]   domain 1: span 0-1 level MC
Apr 27 01:28:02 netbook kernel: [ 2203.384113]    groups: 0-1 (cpu_power = 1178)
Apr 27 01:28:02 netbook kernel: [ 2203.388040] CPU1 is up
Apr 27 01:28:02 netbook kernel: [ 2203.388215] ACPI: Waking up from system sleep state S3
Apr 27 01:28:02 netbook kernel: [ 2203.412008] i915 0000:00:02.0: restoring config space at offset 0x1 (was 0x900007, writing 0x900407)
Apr 27 01:28:02 netbook kernel: [ 2203.412008] HDA Intel 0000:00:1b.0: restoring config space at offset 0x4 (was 0xf0500004, writing 0x80a00004)
Apr 27 01:28:02 netbook kernel: [ 2203.412008] HDA Intel 0000:00:1b.0: restoring config space at offset 0x1 (was 0x100006, writing 0x100002)
Apr 27 01:28:02 netbook kernel: [ 2203.412008] pcieport 0000:00:1c.0: restoring config space at offset 0x9 (was 0x1fff1, writing 0x80318021)
Apr 27 01:28:02 netbook kernel: [ 2203.412008] pcieport 0000:00:1c.0: restoring config space at offset 0x8 (was 0xfff0, writing 0x80108000)
Apr 27 01:28:02 netbook kernel: [ 2203.412008] pcieport 0000:00:1c.0: restoring config space at offset 0x7 (was 0x0, writing 0x3030)
Apr 27 01:28:02 netbook kernel: [ 2203.412008] pcieport 0000:00:1c.0: restoring config space at offset 0x1 (was 0x100000, writing 0x100407)
Apr 27 01:28:02 netbook kernel: [ 2203.412008] pcieport 0000:00:1c.1: restoring config space at offset 0x9 (was 0x1fff1, writing 0x80518041)
Apr 27 01:28:02 netbook kernel: [ 2203.412008] pcieport 0000:00:1c.1: restoring config space at offset 0x7 (was 0x200000f0, writing 0x4040)
Apr 27 01:28:02 netbook kernel: [ 2203.412008] pcieport 0000:00:1c.1: restoring config space at offset 0x1 (was 0x100007, writing 0x100407)
Apr 27 01:28:02 netbook kernel: [ 2203.412008] pcieport 0000:00:1c.2: restoring config space at offset 0x8 (was 0xfff0, writing 0x80908060)
Apr 27 01:28:02 netbook kernel: [ 2203.412008] pcieport 0000:00:1c.2: restoring config space at offset 0x1 (was 0x100007, writing 0x100407)
Apr 27 01:28:02 netbook kernel: [ 2203.412008] uhci_hcd 0000:00:1d.0: restoring config space at offset 0x1 (was 0x2800005, writing 0x2800001)
Apr 27 01:28:02 netbook kernel: [ 2203.412008] uhci_hcd 0000:00:1d.1: restoring config space at offset 0x1 (was 0x2800005, writing 0x2800001)
Apr 27 01:28:02 netbook kernel: [ 2203.412008] uhci_hcd 0000:00:1d.2: restoring config space at offset 0x1 (was 0x2800005, writing 0x2800001)
Apr 27 01:28:02 netbook kernel: [ 2203.412008] uhci_hcd 0000:00:1d.3: restoring config space at offset 0x1 (was 0x2800005, writing 0x2800001)
Apr 27 01:28:02 netbook kernel: [ 2203.412008] ehci_hcd 0000:00:1d.7: restoring config space at offset 0x4 (was 0xf0504000, writing 0x80a04000)
Apr 27 01:28:02 netbook kernel: [ 2203.412008] ehci_hcd 0000:00:1d.7: restoring config space at offset 0x1 (was 0x2900006, writing 0x2900002)
Apr 27 01:28:02 netbook kernel: [ 2203.412008] ahci 0000:00:1f.2: restoring config space at offset 0x9 (was 0xf0504400, writing 0x80a04400)
Apr 27 01:28:02 netbook kernel: [ 2203.412008] ahci 0000:00:1f.2: restoring config space at offset 0x1 (was 0x2b00007, writing 0x2b00407)
Apr 27 01:28:02 netbook kernel: [ 2203.412008] ath9k 0000:07:00.0: restoring config space at offset 0xf (was 0x1ff, writing 0x10b)
Apr 27 01:28:02 netbook kernel: [ 2203.412008] ath9k 0000:07:00.0: restoring config space at offset 0x4 (was 0x4, writing 0xf0100004)
Apr 27 01:28:02 netbook kernel: [ 2203.412008] ath9k 0000:07:00.0: restoring config space at offset 0x3 (was 0x0, writing 0x8)
Apr 27 01:28:02 netbook kernel: [ 2203.412008] ath9k 0000:07:00.0: restoring config space at offset 0x1 (was 0x100000, writing 0x100007)
Apr 27 01:28:02 netbook kernel: [ 2203.412008] r8169 0000:09:00.0: restoring config space at offset 0xf (was 0x1ff, writing 0x105)
Apr 27 01:28:02 netbook kernel: [ 2203.412008] r8169 0000:09:00.0: restoring config space at offset 0x8 (was 0xc, writing 0xf051000c)
Apr 27 01:28:02 netbook kernel: [ 2203.412008] r8169 0000:09:00.0: restoring config space at offset 0x6 (was 0xc, writing 0xf052000c)
Apr 27 01:28:02 netbook kernel: [ 2203.412008] r8169 0000:09:00.0: restoring config space at offset 0x4 (was 0x1, writing 0x2001)
Apr 27 01:28:02 netbook kernel: [ 2203.412008] r8169 0000:09:00.0: restoring config space at offset 0x3 (was 0x0, writing 0x8)
Apr 27 01:28:02 netbook kernel: [ 2203.412008] r8169 0000:09:00.0: restoring config space at offset 0x1 (was 0x100000, writing 0x100407)
Apr 27 01:28:02 netbook kernel: [ 2203.412008] PM: early resume of devices complete after 1.767 msecs
Apr 27 01:28:02 netbook kernel: [ 2203.596737] PM: resume of drv:battery dev:PNP0C0A:00 complete after 331.907 msecs
Apr 27 01:28:02 netbook kernel: [ 2203.597104] i915 0000:00:02.0: setting latency timer to 64
Apr 27 01:28:02 netbook kernel: [ 2203.597777] [drm] Big FIFO is enabled
Apr 27 01:28:02 netbook kernel: [ 2203.668109] [drm] Big FIFO is enabled
Apr 27 01:28:02 netbook kernel: [ 2203.668121] [drm] Big FIFO is enabled
Apr 27 01:28:02 netbook kernel: [ 2203.668246] [drm] Big FIFO is enabled
Apr 27 01:28:02 netbook kernel: [ 2203.692276] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
Apr 27 01:28:02 netbook kernel: [ 2203.692286] HDA Intel 0000:00:1b.0: setting latency timer to 64
Apr 27 01:28:02 netbook kernel: [ 2203.692334] uhci_hcd 0000:00:1d.0: PCI INT A -> GSI 23 (level, low) -> IRQ 23
Apr 27 01:28:02 netbook kernel: [ 2203.692343] uhci_hcd 0000:00:1d.0: setting latency timer to 64
Apr 27 01:28:02 netbook kernel: [ 2203.692369] usb usb2: root hub lost power or was reset
Apr 27 01:28:02 netbook kernel: [ 2203.692396] uhci_hcd 0000:00:1d.1: PCI INT B -> GSI 19 (level, low) -> IRQ 19
Apr 27 01:28:02 netbook kernel: [ 2203.692405] uhci_hcd 0000:00:1d.1: setting latency timer to 64
Apr 27 01:28:02 netbook kernel: [ 2203.692429] usb usb3: root hub lost power or was reset
Apr 27 01:28:02 netbook kernel: [ 2203.692453] uhci_hcd 0000:00:1d.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
Apr 27 01:28:02 netbook kernel: [ 2203.692462] uhci_hcd 0000:00:1d.2: setting latency timer to 64
Apr 27 01:28:02 netbook kernel: [ 2203.692485] usb usb4: root hub lost power or was reset
Apr 27 01:28:02 netbook kernel: [ 2203.692509] uhci_hcd 0000:00:1d.3: PCI INT D -> GSI 16 (level, low) -> IRQ 16
Apr 27 01:28:02 netbook kernel: [ 2203.692518] uhci_hcd 0000:00:1d.3: setting latency timer to 64
Apr 27 01:28:02 netbook kernel: [ 2203.692541] usb usb5: root hub lost power or was reset
Apr 27 01:28:02 netbook kernel: [ 2203.692565] ehci_hcd 0000:00:1d.7: PCI INT A -> GSI 23 (level, low) -> IRQ 23
Apr 27 01:28:02 netbook kernel: [ 2203.692574] ehci_hcd 0000:00:1d.7: setting latency timer to 64
Apr 27 01:28:02 netbook kernel: [ 2203.692610] pci 0000:00:1e.0: setting latency timer to 64
Apr 27 01:28:02 netbook kernel: [ 2203.692630] ahci 0000:00:1f.2: setting latency timer to 64
Apr 27 01:28:02 netbook kernel: [ 2203.692790] ath9k 0000:07:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
Apr 27 01:28:02 netbook kernel: [ 2203.693688] r8169 0000:09:00.0: wake-up capability disabled by ACPI
Apr 27 01:28:02 netbook kernel: [ 2203.693706] r8169 0000:09:00.0: PME# disabled
Apr 27 01:28:02 netbook kernel: [ 2203.824112] PM: resume of drv:usb dev:usb1 complete after 130.045 msecs
Apr 27 01:28:02 netbook kernel: [ 2203.940131] usb 1-4: reset high speed USB device using ehci_hcd and address 2
Apr 27 01:28:02 netbook kernel: [ 2204.012067] ata4: SATA link down (SStatus 0 SControl 300)
Apr 27 01:28:02 netbook kernel: [ 2204.012098] ata1: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
Apr 27 01:28:02 netbook kernel: [ 2204.012127] ata3: SATA link down (SStatus 0 SControl 300)
Apr 27 01:28:02 netbook kernel: [ 2204.012150] ata2: SATA link down (SStatus 0 SControl 300)
Apr 27 01:28:02 netbook kernel: [ 2204.064100] ata1.00: configured for UDMA/100
Apr 27 01:28:02 netbook kernel: [ 2204.081145] PM: resume of drv:usb dev:1-4 complete after 250.081 msecs
Apr 27 01:28:02 netbook kernel: [ 2204.192050] usb 1-8: reset high speed USB device using ehci_hcd and address 3
Apr 27 01:28:02 netbook kernel: [ 2204.352640] PM: resume of drv:usb dev:1-8 complete after 271.476 msecs
Apr 27 01:28:02 netbook kernel: [ 2204.352680] sd 0:0:0:0: [sda] Starting disk
Apr 27 01:28:02 netbook kernel: [ 2204.728129] PM: resume of drv:sd dev:0:0:0:0 complete after 375.447 msecs
Apr 27 01:28:02 netbook kernel: [ 2204.732712] PM: resume of devices complete after 1468.476 msecs
Apr 27 01:28:02 netbook kernel: [ 2204.732965] PM: resume devices took 1.324 seconds
Apr 27 01:28:02 netbook kernel: [ 2204.733041] PM: Finishing wakeup.
Apr 27 01:28:02 netbook kernel: [ 2204.733041] PM: Finishing wakeup.
Apr 27 01:28:02 netbook kernel: [ 2204.733047] Restarting tasks ... done.
Apr 27 01:28:02 netbook kernel: [ 2205.109365] r8169: eth0: link down
Apr 27 01:28:02 netbook kernel: [ 2205.109957] ADDRCONF(NETDEV_UP): eth0: link is not ready
Apr 27 01:28:02 netbook kernel: [ 2205.141726] ADDRCONF(NETDEV_UP): wlan0: link is not ready
Apr 27 01:28:03 netbook kernel: [ 2206.217066] CPU0 attaching NULL sched-domain.
Apr 27 01:28:03 netbook kernel: [ 2206.217078] CPU1 attaching NULL sched-domain.
Apr 27 01:28:03 netbook kernel: [ 2206.249195] CPU0 attaching sched-domain:
Apr 27 01:28:03 netbook kernel: [ 2206.249203]  domain 0: span 0-1 level SIBLING
Apr 27 01:28:03 netbook kernel: [ 2206.249210]   groups: 0 (cpu_power = 589) 1 (cpu_power = 589)
Apr 27 01:28:03 netbook kernel: [ 2206.249222]   domain 1: span 0-1 level MC
Apr 27 01:28:03 netbook kernel: [ 2206.249227]    groups: 0-1 (cpu_power = 117
Apr 27 01:28:03 netbook kernel: [ 2206.249238] CPU1 attaching sched-domain:
Apr 27 01:28:03 netbook kernel: [ 2206.249243]  domain 0: span 0-1 level SIBLING
Apr 27 01:28:03 netbook kernel: [ 2206.249248]   groups: 1 (cpu_power = 589) 0 (cpu_power = 589)
Apr 27 01:28:03 netbook kernel: [ 2206.249259]   domain 1: span 0-1 level MC
Apr 27 01:28:03 netbook kernel: [ 2206.249264]    groups: 0-1 (cpu_power = 117
Apr 27 01:28:09 netbook kernel: [ 2211.341758] wlan0: deauthenticating from 00:1a:70:5a:64:72 by local choice (reason=3)
Apr 27 01:28:09 netbook kernel: [ 2211.542853] wlan0: direct probe to AP 00:1a:70:5a:64:72 (try 1)
Apr 27 01:28:09 netbook kernel: [ 2211.545387] wlan0: direct probe responded
Apr 27 01:28:09 netbook kernel: [ 2211.545396] wlan0: authenticate with AP 00:1a:70:5a:64:72 (try 1)
Apr 27 01:28:09 netbook kernel: [ 2211.547455] wlan0: authenticated
Apr 27 01:28:09 netbook kernel: [ 2211.547495] wlan0: associate with AP 00:1a:70:5a:64:72 (try 1)
Apr 27 01:28:09 netbook kernel: [ 2211.550435] wlan0: RX AssocResp from 00:1a:70:5a:64:72 (capab=0x411 status=0 aid=1)
Apr 27 01:28:09 netbook kernel: [ 2211.550443] wlan0: associated
Apr 27 01:28:09 netbook kernel: [ 2211.551017] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
Apr 27 01:28:22 netbook kernel: [ 2222.340103] wlan0: no IPv6 routers present
```

---

### Post by sobolosrios on 2010-04-27
So I have retested the sleep issue whilst looking at the logs (including a few times while using a kernel that was meant to fix the WARNING: in my last post--the details on that bug and the kernel that fixes it can be found here: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/528688](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/528688)), but that WARNING appears to not be the problem.  The next two times I shut the lid the same thing occurs with a different statement before the large gap in time (although neither of these times did I get the previous WARNING, so the patched kernel may have fixed that issue).  It still appears however (in all my attempts) that the system actually goes to sleep just before it wakes up and presents me with a password prompt.

---

### Post by sobolosrios on 2010-04-27
I just put it to sleep again (this time with pm-suspend instead of closing the lid) and I got the warning on line 614 again.

Is there a way to turn on an even higher level of logging to see what is happening?  It seems the way that the display kicks in all of a sudden that there is timer ticking somewhere and that once it counts to zero the display turns on.  I don't know where that timer is however.

---

### Post by sobolosrios on 2010-04-27
That was a good idea (compiling using the build instructions from jolicloud).  I'm wondering if we can't just pull the kernel directly from jolicloud and boot from it into 9.10.  I'll look into how to create a .deb file from a pre-compiled kernel.

Have you tried debugging this problem through pm-utils?  I think I may add some debugging statements to the various scripts to try and narrow down exactly where the problem occurs.

P.S.  I have a fast internet connection today so I am going to axe my 10.04 installation (I would not suggest upgrading, even when the Lucid final appears as there is a bug in the boot process that likely will not be fixed by the 29th) and install 9.10.  I'll also download the jolicloud iso in case we can't get this solved, at least I'll have the brightness controls working.

---

### Post by Iscran on 2010-04-27
I'll host the deb files for this jolicloud kernel of 2.6.33.3 once I finish the compilation. I don't know if it will work for you but you can give it a try. Might get your brightness working in 9.10.

I'll reinstall 9.10 soon and do some more testing with the kernel in there as time permits. I can upload the jolicloud vmlinux kernel if you want, I think if you put it in your /boot/ folder and run update-grub you can boot from it. I'm not sure, I haven't done much messing with kernels in the past.

---

### Post by Iscran on 2010-04-27
bad news, the compiled kernel I made in Jolicloud stopped my ability to change the backlight. Bummer.

---

### Post by sobolosrios on 2010-04-27
I wonder what Jolicloud did to get brightness controls working.  

I have to admit, I installed Jolicloud today and actually am really liking it.  I don't really like the theme they have chosen, but as a whole the distribution has some really nice touches.  In particular, they have the more informative battery monitor and the cpu frequency scaling in the task-bar above.  All of these things are of course possible in UNR, but its nice to have them done for you.  

Its too bad that its based off an older version of Ubuntu so the package repositories are getting a little dated (OO.o is version 3.0), but I think I'll probably stay with Jolicloud for the time being.  At least until the brightness controls and sleep get working on UNR.  

All I was able to do today was get further confirmation that the bug appears to really be in the kernel.  At least, the bug comes after all of the pm-utils scripts get run.  I put debugging statements in each of the scripts in /usr/lib/pm-utils/sleep.d/ and it appears that each of the scripts gets run completely before the machine is put to sleep (i.e. before the big lapse in time while the machine is trying to wakeup) and the scripts get run in reverse after the machine has already been dead for those few minutes.  

So, whatever the problem is, it is occurring between the times when the pm-utils scripts are run.

I wonder how one gets the ear of a kernel dev either with Jolicloud or Ubuntu.  I'd pay $50 for an hour of their time to get this problem sorted out.

Too bad the 2.6.33.3 kernel messed up the backlight.  Thanks for trying.  BTW, did you compile on your netbook?  If so, did it take almost exactly 4 hours as it did for me?

---

### Post by Iscran on 2010-04-28
yeah I compiled on the netbook. took me around 3-4 hours. Painfully slow cpu in these thigns ;)
If only I had more experiance with kernels I could push it through my quad 3ghz xeon server which would be much much faster.

Edit: No luck running the Joli kernel in UNR, atleast I didn't try to debug it but it wouldn't boot up.

---

### Post by Iscran on 2010-04-28
Success, I got standby to ram working. Stanby at the moment takes me about 5 seconds to enter from within UNR 9.10 and after pressing the power button to bring it back up it's on within about 3 seconds.

I messed with a bunch of the bios settings so I'll do my best now to narrow down which option it was in bios that has got it working. Still no backlight control in UNR 9.10 though :(

Edit: Turns out it's the setting for CPU speed scaling. When set to "Always low" it has no problem entering suspend but when set to dynamic the issue returns. No other bios setting change I could find effected it. However after resuming from suspend ubuntu crashes after a minute or two. Memory corruption or perhaps?

Edit: Jolicloud boots remarkably faster with the Sata option set to compatibility for me.

---

### Post by sobolosrios on 2010-04-28
So, do you mind walking me through how to change those bios settings?  Is this F2 at startup, or something within UNR?

---

### Post by sobolosrios on 2010-04-28
I got it.  BTW, which SATA option did you select?

I'm going to look around now and see if there is a software solution to allow for suspend and dynamic cpu scaling.  Topping out at 1ghz might get a little frustrating sometimes (although 1.66 isn't that fast, its fast enough for the kinds of things I do with a netbook.)

No chance that changing that BIOS setting fixes the brightness keys?  I'm still on Jolicloud so I can't test it.

Were you using the stock 9.10 kernel or something else?

At least this will work for my long plane ride, thanks for figuring it out!

---

### Post by Iscran on 2010-04-28
To enable standby to work under UNR and Jolicloud with the most reliability I did the following (Under Jolicloud OS)

Set bios parameters to :

Dynamic CPU = always low
Execute bit = disabled
Built in lan = enabled
walke on land = disabled
wireless = on
wake on keyboard = disabled
Critical battery = enabled
usb sleep = typical
legacy USB = enabled
sata controller = ahci
sata interface = battery life.

I found if I had the sata options in any other order that coming out of suspend would either not work or ubuntu would crash moments later.No performance problems so far with the cpu running at 1ghz maximum. Atleast it will save battery life :confused:

I also had to add noapic to my kernel boot options in jolicloud otherwise sometimes I would get the error messages "Bug : soft lockup - CPU#0 stuck for 61s" when shutting down or sometimes when coming out of standby. 

Atleast it's a start.

---

### Post by sobolosrios on 2010-04-28
When it rains it pours.

After your solution seemed to work, I thought that we should update the Launchpad bug on this topic which can be found here:

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/508516](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/508516)

And someone had updated it to say that adding

nomodeset nohz=off highres=off

to the kernel boot parameters solves the suspend to ram problem.  

I have tried this and confirm that it works.  That is, I have CPU frequency set to dynamic in the BIOS and it still resumes from suspend immediately.  I also don't have any other kernel boot parameters set (except "quiet splash" that are already in the jolicloud menu.lst). 

I couldn't find a config file at /etc/default/grub as Ubuntu is currently doing so I had edited /boot/grub/menu.lst directly (apparently that is frowned upon currently).  

I'd love to hear if this works for others, especially under 9.10 and/or 10.04.

---

### Post by Iscran on 2010-04-28
haha damn what bad timing but I must say it's a great fix. I edit the menu.list file to :confused: works for me

---

### Post by sobolosrios on 2010-04-28
Now if only we could figure out how to get the brightness controls working I would update to either 9.10 or 10.04 to get some of the more recent packages.

---

### Post by Byzandula on 2010-04-28
I can confirm that appending nomodeset nohz=off highres=off fixes the suspend problem on the NB305-N310 on 10.04 Lucid. I really wish I had screen dimming capability. That is the only annoyance right now to an otherwise AWESOME experience thus far with this netbook running Lucid.

---

### Post by sobolosrios on 2010-04-29
@Byzandula

Strange, I tried to get this to work (admittedly running from the USB drive, so it wasn't a full install) and it didn't work for me.  Can you list all of your kernel boot parameters?

---

### Post by cschellenger on 2010-04-29
FYI, this isn't a great solution for the brightness, but it's better than nothing:

Before the kernel boots up, i.e. the BIOS setup, or boot menu, the netbook does seem to respond to the brightness keys.

---

### Post by Byzandula on 2010-04-29
This is what I have in /etc/default/grub:

GRUB_CMDLINE_LINUX_DEFAULT="nomodeset nohz=off highres=off quiet splash"

Try appending the above before "quiet splash"

Good luck!

---

### Post by sobolosrios on 2010-04-29
I'll try it and see how it goes.  Thanks!

---

### Post by sobolosrios on 2010-04-29
I got it.  Thanks for your help.  

Now, onto brightness...

---

### Post by Nocturnhabeo on 2010-04-30
hey sorry to be such a newb but I have never played around with Linux before i have used computers enough to kind of guess and ball park most of what you guys are talking about but it would rock if someone could put it all together in a laymen termed post I will be reading the all the material that i can but i would like to have my computer working better than it is I full installed ubuntu 10.04 cause I'm an idiot and a friend told me he got it working on his net book (acer) so i have all the problems with no windows 7 to go back to :( all I can add is that 10.04 netbook remix seems to have the same problems you guys were talking about with 9.10 also i can't seem to get the tuxonice to work it says it cant find it or something when i try to add it to apt get. *shrug* maybe I'm doing it wrong but I'm copy pasting so it should work. i would like for a response not a flame. adios

---

### Post by Iscran on 2010-04-30
> **Nocturnhabeo said:**
> hey sorry to be such a newb but I have never played around with Linux before i have used computers enough to kind of guess and ball park most of what you guys are talking about but it <snip> s

To update the boot parameters to allow suspend to work:
Open a terminal session (Applications menu->Terminal)
type in the commands in bold and hit enter.

1) **sudo gedit /etc/default/grub**
2) Change:  GRUB_CMDLINE_LINUX_DEFAULT="splash nohz=off  highres=off"
 3) **sudo update-grub**
4) **sudo reboot now**
5) after reboot, close the lid, wait for orange slow-blinking light
6) open lid, press power button once, enter password, click on unlock
7) It works :)



I found some typos in my guide to installing tuxonice so I rewrote it. Try following it again it should work ok for you now. Cheers
[http://www.uluga.ubuntuforums.org/showpost.php?p=9132794&postcount=31](http://www.uluga.ubuntuforums.org/showpost.php?p=9132794&postcount=31)

---

### Post by Iscran on 2010-04-30
@[sobolosrios]("http://www.uluga.ubuntuforums.org/member.php?u=1049835") : I added noapic to my boot line too which seemed to improve the stability. With the nohz, nomodeset and highres in there I was still getting the occasional time when it wouldn't go back into jolicloud and would crash. No issues since I added it 3 days ago.

---

### Post by Nocturnhabeo on 2010-05-01
the GRUB update that people posted works in 10.04 netbook remix. I haven't tried the tuxonice yet. Ty to [FONT=Arial]_Iscran _[/FONT]for the post on how to do it I am gonna try the other things you guys have suggested. i haven't tried hibernate yet but hopefully that is fixed as well

edit:
My hibernate function also works.

---

### Post by sobolosrios on 2010-05-01
I can confirm that hibernate works for me (without tuxonice) in 10.04 NBE.  I also have added (as Iscran mentioned) noapic as a kernel argument.  I just added it today as I had my first X crash.  I'll update when I have a better idea about its stability.

---

### Post by Nocturnhabeo on 2010-05-01
> **Iscran said:**
> To update the boot parameters to allow suspend to work:
Open a terminal session (Applications menu->Terminal)
type in the commands in bold and hit enter.

1) **sudo gedit /etc/default/grub**
2) Change:  GRUB_CMDLINE_LINUX_DEFAULT="splash nohz=off  highres=off"
 3) **sudo update-grub**
4) **sudo reboot now**
5) after reboot, close the lid, wait for orange slow-blinking light
6) open lid, press power button once, enter password, click on unlock
7) It works :)



I found some typos in my guide to installing tuxonice so I rewrote it. Try following it again it should work ok for you now. Cheers
[http://www.uluga.ubuntuforums.org/showpost.php?p=9132794&postcount=31](http://www.uluga.ubuntuforums.org/showpost.php?p=9132794&postcount=31)

hey so i tried to do the tuxonice install and i keep getting to the kernal update thing 
sudo apt-get install linux-headers-2.6.31-19-generic-tuxonice and i keep getting the error 
E: Couldn't find package linux-headers-2.6.31-19-generic-tuxonice
dunno what that means maybe because of the connection i am on it has a firewall that seems to hate me ill try another one but it may be something else so i figured i would post.

the hibernate function works so I am not gonna try tuxonice

---

### Post by sobolosrios on 2010-05-01
@Iscran:  Are you still on Jolicloud?  If so, can you tell me the output you get when you run

lsmod | grep toshiba

Thanks for your help.

---

### Post by jonesieboy on 2010-05-02
I can also confirm success with suspend on the NB300 after following lscran's instructions.  I have not changed the kernel.

Robert Jones

---

### Post by dweir on 2010-05-03
Hey folks,

Just bought a new NB305 and installed Ubuntu Netbook Remix 9.10. Functionally, this is great. The only complaint I have is the inability to adjust screen brightness. That high gloss screen combined with max brightness is harsh.

I installed the ACPI utilities but only the battery was detected. I also installed and configured "lm-sensors" but no sensors were discovered. This worries me somewhat given the overheating issues with Toshiba laptops in general. How serious of an issue is this? Enough that I have to switch back to Windows (Bite your tongue!) just to make sure this machine doesn't fry itself?

Cheers,
Dave

---

### Post by sobolosrios on 2010-05-03
I'm not sure how much of an issue it is to tell you the truth.  My nb305 gets warm, although I don't find it to be uncomfortable.  I would suspect that the difference between the highest and lowest screen settings probably would not be enough to put the temperature over the edge, but I guess if everything else was hot enough...

As for a fix, this thread has the current state of the art.  So far what we know is that Jolicloud (based on Ubuntu 9.04) has working brightness keys and that in 10.04 (and probably 9.10 as well) the brightness keys work on the Grub screen, but don't work inside Ubuntu itself.  Therefore, it seems to be something happening when you boot into Ubuntu that is causing the problem.  

When you say that you installed acpi utilities, have you modprobed the toshiba_acpi module?  I can't get that to work on 10.04 for some reason so if you were able to do it, it would be good to know.

---

### Post by kr0ots on 2010-05-05
Hey guys,

Just bought a NB300 too, i got some issues with the Fn keys which don't works at all but i also got a serious bug : my netbook takes about 5 min to boot !!!
I tried to install Ubuntu 10.04 & the netbook remix 10.04 same same, 5 f** long min to boot...

Do you guys have the same problems?

---

### Post by hatemben on 2010-05-05
@kr0ots change "Sata controller mode" in BIOS/Advanced to "compatibility" and boot issue should be fixed. I'm still looking for a way to fix the suspend/hibernate issue.

-Hatem

---

### Post by sobolosrios on 2010-05-05
@hatemben Have you tried the fixes for suspend/hibernate in this thread?  They have worked for me.  If they don't work for you, it would be good to know.

Thanks!

---

### Post by Iscran on 2010-05-05
> **sobolosrios said:**
> @Iscran:  Are you still on Jolicloud?  If so, can you tell me the output you get when you run

lsmod | grep toshiba

Thanks for your help.

Doesn't return anything, no module found. Still running Jolicloud. Had some issues coming out of Stanby after long periods (a day). Still investigating.

---

### Post by Iscran on 2010-05-05
*double post.

---

### Post by sobolosrios on 2010-05-05
> **Iscran said:**
> Doesn't return anything, no module found. Still running Jolicloud. Had some issues coming out of Stanby after long periods (a day). Still investigating.


Thanks Iscran. That is really helpful.  I thought that Jolicloud might have found a way to include the toshiba_acpi module into the kernel.  When I try to modprobe that module with the stock Lucid Kernel, it gives an error.  

It looks like Jolicloud isn't doing that.  I'll keep looking.

Thanks again.

---

### Post by Iscran on 2010-05-05
How many hours does everyone get out of their battery when running ubuntu? I'm getting an an estimated 5.5 out of a full charge. That's a bit disappointing.

---

### Post by Iscran on 2010-05-06
New Bios version is out: 1.40
[B]
match your model number from the sticker underneath[/B]

Australia : [http://www.mytoshiba.com.au/support/notebooks/nbseries/nb300/pll3ea-006007/download](http://www.mytoshiba.com.au/support/notebooks/nbseries/nb300/pll3ea-006007/download) (Select your laptop from the list at the top)
PLL3AU/PLL3EU/3FU : [http://www.csd.toshiba.com/cgi-bin/tais/support/jsp/modelContent.jsp?ct=SB&os=&category=&moid=2523338&rpn=PLL3FU&modelFilter=&selCategory=3&selFamily=2336267#](http://www.csd.toshiba.com/cgi-bin/tais/support/jsp/modelContent.jsp?ct=SB&os=&category=&moid=2523338&rpn=PLL3FU&modelFilter=&selCategory=3&selFamily=2336267#) under downloads
PLL3A/PLL3E : [http://www.toshiba-asia.com/portal/public/driverDlDetails.action?pgAction=driverDlDetails.action&a=driverDlDetails&itemId=30613&currentTab=service&type=Drivers](http://www.toshiba-asia.com/portal/public/driverDlDetails.action?pgAction=driverDlDetails.action&a=driverDlDetails&itemId=30613&currentTab=service&type=Drivers)

---

### Post by hatemben on 2010-05-06
@Iscran thx for the info, but you'll need windows to upgrade :-)

@sobolosrios I have tried previous fixes with 9.10 and it was not helpful. I'm running 10.04 now, and did not try any workaround yet.

---

### Post by linuxgr on 2010-05-06
NEW PROBLEM!

Hey guys, I just upgraded to 10.04 and I can't boot! After I select either of the two available kernels to boot, I get this:

```
Gave up waiting for root device. Common problems:
- Boot args (cat /proc/cmdline)
  - Check rootdelay= (did the system wait long enough?)
  - Check root= (did the system wait for the right device?)
- Missing modules (cat /proc/modules; ls /dev)
ALERT! /dev/disk/by-uuid/6d14e151-900f-4476-9418-d24542b49617 does not exist. Dropping to a shell!

BusyBox v1.13.3 (Ubuntu 1:1.13.3-1ubuntu11) built-in shell (ash)
Enter 'help' for a list of built-in commands.

(initramfs)
```

I used a bootable usb to boot with 9.10 and check, and the above uuid is the actual uuid of the root partition, nothing wrong there. I googled for solutions, none applied to me.

For example:
Someone said to add "rootdelay=90", I did, no result.
Others said wait for a while and type "exit" on the above prompt, again, no result.
Etc...


Here's what I found somewhere:
```
Users have reported slower than normal detection of SATA hard drives on systems with Intel D945 motherboards in Ubuntu 8.10. 
This may cause the system to drop to a busybox initramfs shell on boot with a "Gave up waiting for root device." error. 
Wait a minute or two and then exit the initramfs shell by typing 'exit'. 
Booting should proceed normally. If it doesn't, wait a bit longer and try again. 
Once the system boots, edit /boot/grub/menu.lst and add rootdelay=90 to the kernel stanza for your current kernel. (Bug 290153). 
```

Not sure if this is my motherboard (I have NB305), but the fix does not work...

Any ideas?

---

### Post by sobolosrios on 2010-05-06
That happened to me one time when I installed.  I reinstalled and it worked just fine.  I guess my installation had gotten messed up some how.  That's not a good answer I know, but I couldn't figure out the (initramfs)/long boot problem either.  

Is reinstallation an option?

---

### Post by kr0ots on 2010-05-06
@hatemben : Thx this works really nice now :) I can boot my netbook inna minute !! That's waaaay better.

I still got a major bug: my "Fn" keys don't works at all..Anybody got the same issue? 

Thx for helping ! ;)

---

### Post by sobolosrios on 2010-05-06
> **Iscran said:**
> New Bios version is out: 1.40
[B]
match your model number from the sticker underneath[/B]

Australia : [http://www.mytoshiba.com.au/support/notebooks/nbseries/nb300/pll3ea-006007/download](http://www.mytoshiba.com.au/support/notebooks/nbseries/nb300/pll3ea-006007/download) (Select your laptop from the list at the top)
PLL3AU/PLL3EU/3FU : [http://www.csd.toshiba.com/cgi-bin/tais/support/jsp/modelContent.jsp?ct=SB&os=&category=&moid=2523338&rpn=PLL3FU&modelFilter=&selCategory=3&selFamily=2336267#](http://www.csd.toshiba.com/cgi-bin/tais/support/jsp/modelContent.jsp?ct=SB&os=&category=&moid=2523338&rpn=PLL3FU&modelFilter=&selCategory=3&selFamily=2336267#) under downloads
PLL3A/PLL3E : [http://www.toshiba-asia.com/portal/public/driverDlDetails.action?pgAction=driverDlDetails.action&a=driverDlDetails&itemId=30613&currentTab=service&type=Drivers](http://www.toshiba-asia.com/portal/public/driverDlDetails.action?pgAction=driverDlDetails.action&a=driverDlDetails&itemId=30613&currentTab=service&type=Drivers)

Which BIOS did you have before?  I've been on the 1.40 bios since I bought it.  Although, that was only two weeks ago.

---

### Post by sobolosrios on 2010-05-06
> **kr0ots said:**
> @hatemben : Thx this works really nice now :) I can boot my netbook inna minute !! That's waaaay better.

I still got a major bug: my "Fn" keys don't works at all..Anybody got the same issue? 

Thx for helping ! ;)

That's pretty much the case for all of us.  I don't know the solution yet  however.

---

### Post by linuxgr on 2010-05-06
> **sobolosrios said:**
> That happened to me one time when I installed.  I reinstalled and it worked just fine.  I guess my installation had gotten messed up some how.  That's not a good answer I know, but I couldn't figure out the (initramfs)/long boot problem either.  

Is reinstallation an option?

Yes and no... Yes cause I don't have a lot of stuff or config that needs to be redone and no cause I dont really have the time right now.... But if everything else fails, I'll resort to that...

Thanks anyway...

---

### Post by vintageveloce on 2010-05-07
linuxgr
I'm seeing the same problem, exact same report by busybox, with a different uuid (of course). But after hitting a bunch of returns, and waiting about 5 minutes, the machine mysteriously boots. I ran the update manager, but that didn't help. I have the 1.40 BIOS and the machine is a NB305-410BL.
This is my first install on this machine, done with a 10.04 UNR USB stick, and I set it up to dual boot. Of course the windows partition won't boot at all. But it appears to be there. SO I'm concentrating on the ubuntu boot problem. 
Boots fine off of the USB stick. And sometimes eventually off of the hard drive. Something is fishy... ideas? bootloader? Grub?
Any ideas anyone?
Carl

---

### Post by portablevcb on 2010-05-07
Thanks for the hints on fixing the sleep problem.  Works fine for me now (9.04).

When I did the install grub would not boot properly into windows either.  I had to use the recovery disk to reinstall it and then it was fine.

I like the UNR for this little machine too.  I had the full version and it was OK but the interface and handling of graphics seems to be better with the netbook version.

---

### Post by linuxgr on 2010-05-07
@vintageveloce, @sobolosrios:

I just did a fresh install on the machine. Same problem. But I confirm it boots normally from a usb stick, so unless a different kernel is used for the liveCD, it's probably grub that does the damage.

In my case I tried everything, typing "exit", hitting returns, waiting for an hour: nothing. Hope it gets fixed soon

---

### Post by vintageveloce on 2010-05-07
[@linuxgr]("http://ubuntuforums.org/member.php?u=658779") and all...
Just to be clear, here is my problem. 
NB305, set up for dual boot with 10.04 UNR. Bios 1.40, Windows partitions boot fine. Can boot 10.04 from USB stick.
From grub menu select Ubuntu (firstoption).
After about a minute I get this:

Gave up waiting for root device. Common problems:
- Boot args (cat /proc/cmdline)
  - Check rootdelay= (did the system wait long enough?)
  - Check root= (did the system wait for the right device?)
- Missing modules (cat /proc/modules; ls /dev)
ALERT! /dev/disk/by-uuid/<myUUID> does not exist. Dropping to a shell!

BusyBox v1.13.3 (Ubuntu 1:1.13.3-1ubuntu11) built-in shell (ash)
Enter 'help' for a list of built-in commands.

(initramfs)

I type "exit" and hit enter. After about 6 minutes (really!) Ubuntu boots.
linuxgr, I suggest you try entering exit and waiting, like I did. Something is clearly wrong, but the pieces do seem to be there to boot. I'm going to run the update manager and then look at the boot process...
Carl

---

### Post by linuxgr on 2010-05-07
@vintageveloce

that's what I said.... "exit" and waited for an hour, nothing....

:-(

---

### Post by redsky009 on 2010-05-07
> **vintageveloce said:**
> [@linuxgr]("http://ubuntuforums.org/member.php?u=658779") and all...
Just to be clear, here is my problem. 
NB305, set up for dual boot with 10.04 UNR. Bios 1.40, Windows partitions boot fine. Can boot 10.04 from USB stick.
From grub menu select Ubuntu (firstoption).
After about a minute I get this:

Gave up waiting for root device. Common problems:
- Boot args (cat /proc/cmdline)
  - Check rootdelay= (did the system wait long enough?)
  - Check root= (did the system wait for the right device?)
- Missing modules (cat /proc/modules; ls /dev)
ALERT! /dev/disk/by-uuid/<myUUID> does not exist. Dropping to a shell!

BusyBox v1.13.3 (Ubuntu 1:1.13.3-1ubuntu11) built-in shell (ash)
Enter 'help' for a list of built-in commands.

(initramfs)

I type "exit" and hit enter. After about 6 minutes (really!) Ubuntu boots.
linuxgr, I suggest you try entering exit and waiting, like I did. Something is clearly wrong, but the pieces do seem to be there to boot. I'm going to run the update manager and then look at the boot process...
Carl

I have exactly the same issue - dual w7 and ubuntu NBR 10.04 - any solutions?

---

### Post by vintageveloce on 2010-05-07
I've made some progress. I think this might be a initrd issue, driver problem. I went into the bios and changed the SATA Controller Mode from AHCI to Compatibility. 
And then the machine successfully booted ubuntu! 
Of course, Win7 won't boot in this mode.
So I think maybe the AHCI driver is missing or broken in Ubuntu. But is it strange that ubuntu WILL eventually boot.
I'm trying to figure out how to get the proper AHCI driver...
AN
Any help from an expert out there? I'm just a newbie wandering in the woods..
Carl

---

### Post by linuxgr on 2010-05-08
> **vintageveloce said:**
> I've made some progress. I think this might be a initrd issue, driver problem. I went into the bios and changed the SATA Controller Mode from AHCI to Compatibility. 
And then the machine successfully booted ubuntu! 


Confirmed.

---

### Post by vintageveloce on 2010-05-08
I posted this in General too (sorry about the cross post) trying to get some more attention from the more knowledgeable people out here...

                                  **Troublesome boot, AHCI driver problem?**             
                                                                Here all I know about the problem so far:

In short, it takes forever (6 min), and lots of prodding to get Ubuntu  to boot.

Im running a Toshiba NB305 netbook (Bios 1.40), set up for dual boot  with 10.04 UNR.
Windows partitions boot fine. Can boot 10.04 from USB stick.

Here how I try to boot:
From grub menu select "Ubuntu, with Linux 2.6.32-22-generic"
If it doesn't work, I run the recovery version, and then run the regular  one again. Somehow that resets stuff.

After about a minute I sometimes get this:

         Gave up waiting for root device. Common problems:
         - Boot args (cat /proc/cmdline)
         - Check rootdelay= (did the system wait long enough?)
         - Check root= (did the system wait for the right device?)
         - Missing modules (cat /proc/modules; ls /dev)
         ALERT! /dev/disk/by-uuid/<myUUID> does not exist.  Dropping to a shell!

         BusyBox v1.13.3 (Ubuntu 1:1.13.3-1ubuntu11) built-in shell  (ash)
         Enter 'help' for a list of built-in commands.

         (initramfs)

I type "exit" and hit enter. 

     _ (curser flashes) And the machine looks stuck. 

Sometimes I hit return a few times in frustration.
After about 6 minutes (really!) Ubuntu boots. 

I've attached the output from boot_info_script055.sh

The drives look Ok to me? And it does eventually boot. So I was  suspecting a missing module/driver issue.

I've tried to find some stuff on the initrd.img, but haven't figured  anything out there.

Somewhere I read to try changing a setting in the BIOS: I changed the  SATA Controller Mode from "AHCI to Compatibility". Amazingly, Ubuntu  booted cleanly in about a minute. Of course, my other partition of  Windows 7 will not boot in this mode. So I really want AHCI to work.

I'm guessing that maybe the AHCI driver is missing or broken? Can this  be fixed/reinstalled? I've read that:
"In Karmic, the ahci driver was built in by default in the kernel.   However, in Lucid, this driver is now enabled as a module." (Bug  #570542)
Could this be the problem? Or am I missing something simpler?
Is there a useful log to look at that can show me what happens in that  dead 5 
minutes?

This newbie would appreciate your expert help! :wink:
Carl

---

### Post by vintageveloce on 2010-05-08
Well, I'll be a stuffed pumpkin.
I had been ignoring the sleep and hibernate issues everyone was talking about as I had the boot dual boot issues described above. But then I thought... what if the SATA issue is related somehow to the timers that people are disabling (nohz and highres) for sleep and hibernate. So I edited grub as described much earlier in the thread... and now my booting problems are solved, even with the BIOS set to AHCI.
So, I'm running 10.04 UNR, dual boot with Windows 7. Sata controller mode set to AHCI.
Dual boot works. Hibernate works, Sleep works.
Sleep key (FN F3) and volume keys (FN 3 FN 4) work.  The other F keys don't seem to, but I didn't try much.
Small issue: Brightness can only be set in Grub, or in Win7.
Carl
(happy dual boot UNR & 10.04 Win7 Starter)

---

### Post by linuxgr on 2010-05-10
@vintageveloce
I have not yet experimented with the sleep function, so I did not change any of these settings(nohz and highres) and yet it does not boot with the SATA option set to AHCI. Seems that whatever is causing this problem to be a mystery still...

Anyway, since you got it all working could you please post exactly what changes YOU made to get "sleep" working, out of all suggested here?

Thanks in advance...

---

### Post by vintageveloce on 2010-05-11
I did exactly as is described here:
[http://ubuntuforums.org/showpost.php?p=9199154&postcount=64](http://ubuntuforums.org/showpost.php?p=9199154&postcount=64)
(post 64 in this thread by Iscran)
And left the bios at AHCI.
C

---

### Post by mohi2k7 on 2010-05-11
hello i have been using ubuntu 10.04 netbook remix on my toshiba nb 300 for the most part it works fine... i had the slow boot up issue, when you just see a white cursor in the top left coner of the screen... can be fixed by pressing F2 during bios load up, under one of the menus you'll find a "hard drive option" change [achi] to [compatibility] save and exit you get fast boot up...

btw can someone please help me to adjust the screen brightness its the only thing annoying me the most because it drains the battery... theres two people to blame for no screen controls, firstly toshiba because they dont provide a linux "flash card" driver thats what makes your "fn key" work with the option along the top of your key board... however this dose not excuse unbuntu honestly why havent they intergrated display control features into the os? plus theres other functionality/tweaking that is required, this makes it a less enjoyable experience for the end user.

---

### Post by vintageveloce on 2010-05-11
The whole story.
I bought my NB305-N410BL about a week ago and played with it for a couple days optimizing Windows 7 Starter. And I updated to the latest BIOS 1.40. Then I decided it was time to load Ubuntu 10.04 Netbook Remix as a dual boot. I built an ISO CD and made a USB flash stick from that, per the directions. The USB flash worked fine, so I thought I'd move ahead.
I considered repartitioning with the windows tool, but was unsure what to set up. And I noticed the USB installer offered to do the partitioning, so I decided to do it that way. 
I did defrag the hard drive first. And then I Installed UNR as a dual boot from the USB flash. 
Right off the bat, nothing booted. Luckily, after a couple attempts Windows ran a chdsk repair, and somehow fixed itself. (If I were to do the install again I might do the repartitioning with the WIndows tool, hoping to avoid the problems.) So I could at that point boot Windows 7 Starter again. Three Windows partitions showed in the GRUB; a small 1st Windows partition (don't know what that is), the real Windows Starter partition and a Vista Recovery partition. All three worked. The Ubuntu partition and swap partition were there but had trouble booting. 
That story is posted earlier, but eventually I discovered that changing the BIOS SATA Controller Mode from AHCI to Compatibility allowed Ubuntu to boot, but then WIndows 7 would not. Further investigation showed that I could leave the BIOS SATA Controller Mode in AHCI if I made the suggested GRUB additions of "nohz=off highres=off" to the line GRUB_CMDLINE_LINUX_DEFAULT. I'm not completely sure what these do, but I think they effect some timing / clock paremeters in Ubuntu. But the rest of the FN keys and Brightness do not work. I'll note you can adjust the brighness at the GRUB screen before booting Ubuntu, so that helps.
So at that point the machine nicely booted WIndows 7 Starter or Ubuntu Netbook Remix 10.04. Suspend/Sleep and Hybernate worked. FN volume controls worked. Ubuntu does seem to boot a little faster than WIndows.
While my NB305 is running fine I do find that battery life seemed to be significantly less with UNR and the machine seemed to run a bit hotter (which makes me nervous). And the drive seems to keep spinning longer with UNR. I haven't measured this scientificly. It appears Ubuntu's battery life estimate is also much shorter than Windows. 
I often use my netbook in varying light conditions and run it on battery. Between the shorter battery life and the inability to change the screen brightness, I have decided to set my default boot to Windows 7 starter. I'm hoping future kernel releases improve both these issues, because I'd love to default to Ubuntu.
So thats my story so far!
Carl

---

### Post by esera on 2010-05-19
> **Iscran said:**
> To update the boot parameters to allow suspend to work:
Open a terminal session (Applications menu->Terminal)
type in the commands in bold and hit enter.

1) **sudo gedit /etc/default/grub**
2) Change:  GRUB_CMDLINE_LINUX_DEFAULT="splash nohz=off  highres=off"
 3) **sudo update-grub**
4) **sudo reboot now**
5) after reboot, close the lid, wait for orange slow-blinking light
6) open lid, press power button once, enter password, click on unlock
7) It works :)


Confirmed. Thanks, this works on Ubuntu Lynx 10.04 on nb300. Great help!

---

### Post by hatemben on 2010-05-19
> **esera said:**
> Confirmed. Thanks, this works on Ubuntu Lynx 10.04 on nb300. Great help!

Confirmed work like charm, Lynx 10.04 and nb300.

---

### Post by linuxgr on 2010-05-19
Thanks Carl, I'll give it a try...

---

### Post by edpare on 2010-05-19
Confirmed:  "Wake from suspend" works on NB305 running Ubuntu 10.04 netbook remix.  Thanks!

---

### Post by kingsrule5 on 2010-05-20
Ok so new ubuntu usr het with an NB305 and i am having an issue with bluetooth on NBR 10.04. i followed this post exactly to enable it:

[http://ubuntuforums.org/showpost.php?p=8327841](http://ubuntuforums.org/showpost.php?p=8327841)

and it works fine on boot but not from sleep(which i also enabled) but i cant get the last 2 lines from the above post for coming out of sleep when i run the code

```
nano /etc/pm/power.d/89bluetooth

```

i get ```
Error reading /home/jared/.nano_history: Permission denied

Press Enter to continue starting nano.

```

so i hit enter

but it still opens an editor and i
added the lines 
```
#!/bin/bash
rmmod -f omnibook
modprobe omnibook ectype=14
```

i try crlt-o crtl-x to save and exit nd get a permission denied message

i tried it as ```
sudo nano /etc/pm/power.d/89bluetooth

```

for this i get the editor but when i ctrl-0 ctlr-x i get

```
error writting /etc/pm/power.d/89bluetooth no such file exits
```

Am i missing a step somewhere please help. Thank you

---

### Post by PGScooter on 2010-05-20
> 1) sudo gedit /etc/default/grub
2) Change: GRUB_CMDLINE_LINUX_DEFAULT="splash nohz=off highres=off"
3) sudo update-grub
4) sudo reboot now
5) after reboot, close the lid, wait for orange slow-blinking light
6) open lid, press power button once, enter password, click on unlock
7) It works 

this worked for me as well -- it fixed the slow startup time and the suspend works fine (I don't know if it was broken before).

---

### Post by jim_charlton on 2010-05-23
Further to the Toshiba NB305 suspend/re-awaken and slow booting problems... presumably cured by adding nohz=off highres=off to the GRUB kernel command line.

I find that this "cure" craps up the sound.  See [https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/574137](https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/574137).  It took me a long time to figure out that the loss of sound quality is due to using those parameters.  The sound issues can be avoided by removing pulseaudio.... but that is hardly a solution.

---

### Post by Rodney9 on 2010-05-23
Did anyone ever get the brightness keys working ?

I'm using a Toshiba L500/08P with Xubuntu 10.4. Gnome in Lucid has a applet for brightness, but wireless failed after the last update.

---

### Post by ckcoolic on 2010-05-23
Hello, I am new to linux and am also experiencing the same problem as Jim with the audio.  
 
I did the Change: GRUB_CMDLINE_LINUX_DEFAULT="splash nohz=off highres=off" but did not change the BIOS SATA controller.
 
Audio is unrecognizable distortion playing .flac through Rythmbox.  Audio worked perfectly before I edted grub, but it did not suspend/hibernate.

---

### Post by Rodney9 on 2010-05-23
> **Rodney9 said:**
> Did anyone ever get the brightness keys working ?

I'm using a Toshiba L500/08P with Xubuntu 10.4. Gnome in Lucid has a applet for brightness, but wireless failed after the last update.

I installed xfce4-goodies and gnome-applets, I now have a laptop brightness applet in xubuntu. :)

---

### Post by ckcoolic on 2010-05-24
The sound problem has not been consistent for me.  Making no changes except for suspending for the night and coming back the next day, my sound worked.  Playing a .flac through Rythmbox while buffering a flash movie in Firefox later and the sound was distorted again.  Closing the flash movie and waiting 5 seconds, and I am listening to music again.  I dont know if this would be related to the computer being too busy, or running too warm.  It does seem to put off a lot of heat.  I also noticed the projected battery life is about half of what was projected running XP.  I would have expected more battery life, not less.

---

### Post by jim_charlton on 2010-05-24
The easiest test to see if the audio is working on the Toshiba NB305 is to go to preferences-> sound and make sure the ubuntu sound theme is selected.  Then open a terminal window (accessories->terminal) and when the CLI appears, press and hold the back arrow.  You will get a system "bong or ping" indicating an incorrect key entry) just hold it down and after 10 to 20 bongs the sound will distort.  It requires 6 seconds before you can get normal sound again.  Other programs that stress the sound system will cause this sudden distortion.

The problem can be avoided for many programs by removing pulseaudio (apt-get remove pulseaudio) and reboot.  You will lose the volume control applet (and other pulseaudio stuff) but you can use alsamixer to set volumes.  Like I said... it is hardly a solution.... but many programs will still work perfectly without pulseaudio installed.

It appears that pulseaudio requires the kernel highres timers in order to work reliably.  When you deactivate the timers by putting highres=off on the GRUB kernel command line, it dooms pulseaudio.  Or at least this has been my experience.  I tried it with a completely clean install, with and without the "nohz=off highres=off".  Without those parameters the sound is just fine.

What is really required is a patch to make the machine suspend and reawaken properly when the lid is closed... *without* ... deactivating the highres timers.

As always... take anything I say with a grain of salt.  It is just my interpretation of what I observe.

---

### Post by vintageveloce on 2010-05-24
What is really required is a patch to make the machine suspend and reawaken properly when the lid is closed... *without* ... deactivating the highres timers.

AGREED. My understanding is also that deactivating these timers is bad news for the battery life. Until the machine works with these timers the NB305 battery life will be relatively short. 
PLEASE POST TO THE BUGS ON LAUNCHPAD!
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/508516](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/508516)

and 

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/573287](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/573287)

Carl

---

### Post by jim_charlton on 2010-05-24
The kern.log entries noted by sobolosrios...

It is likely that the log messages are written to buffer and then transferred to disk.  When you suspend, the process is interrupted.  On resume the messages in the buffer get written to disk with the time they were transferred to disk... NOT the time that the message occurred.  Normally these times are the same but the suspend interrupted the process.  So the machine probably did go to sleep when the lid was closed.

I am not sure my explanation is perfect... but it is a likely scenario.

We still need to know why running with the highres times activated causes:
1>  the machine to boot slowly... if at all
2.  The machine won't resume from suspend.

These things are most likely related.  Any ideas out there???

---

### Post by stork123 on 2010-05-27
I've been following this thread and have 10.04 up and running a on a dual boot alongside 7 on my nb305. When I boot into ubuntu, my install takes me straight to the terminal. To get into the GUI I type startx? Does this sound normal? I think I may have opted to type my login info for each start during the install from USB. If I did so, would it take me to the terminal like this?

---

### Post by jim_charlton on 2010-05-27
> **stork123 said:**
> I've been following this thread and have 10.04 up and running a on a dual boot alongside 7 on my nb305. When I boot into ubuntu, my install takes me straight to the terminal. To get into the GUI I type startx? Does this sound normal? I think I may have opted to type my login info for each start during the install from USB. If I did so, would it take me to the terminal like this?
Stork123:  I rarely have the boot process stop at a terminal CLI.  If I leave the "nohz=off highres=off" off of the GRUB kernel line then the machine sometimes dumps me at a terminal CLI of the initramfs.  The hard disk is not even mounted so the only thing to do is reboot.  But with the nohz and highres parameters on the kernel command line, it always boots just fine right into the gnome desktop (gdm).

---

### Post by stork123 on 2010-05-28
I'll edit Grub in the morning.

This is what I have now.

menuentry 'Ubuntu, with Linux 2.6.32-21-generic' --class ubuntu --class gnu-linux --class gnu --class os {
recordfail
insmod ext2
set root='(hd0,5)'
search --no-floppy --fs-uuid --set 49024e15-119a-4339-ad23-f201ce4a6d1f
linux	/boot/vmlinuz-2.6.32-21-generic root=UUID=49024e15-119a-4339-ad23-f201ce4a6d1f ro quiet splash
initrd	/boot/initrd.img-2.6.32-21-generic



Where am I adding nohz=off highres=off after the splash?

I also need to play with my user account settings. Maybe I have it set to prompt for username and password on boot

---

### Post by jim_charlton on 2010-05-28
Add "nohz=off highres=off" after splash (or in place of "quiet splash"; it is what I do so that I can see the boot dialog) on the "linux" kernel line.  If you are using GRUB2 you put the parameters in /etc/default/grub on the GRUB_CMDLINE_LINUX_DEFAULT line (GRUB_CMDLINE_LINUX_DEFAULT=nohz=off highres=off" and then run update-grub.

Even if you ask the system to prompt you for a password, it will do so from a gnome dialog box.  Is it possible that you have only a partial install?  As soon as you can, run "update manager" and install updates (or go to a terminal CLI and type "apt-get update" and then "apt-get upgrade".

---

### Post by stork123 on 2010-05-29
I think I must have only a partial install... things are just too wacky to be otherwise. I'm gonna restore via Toshiba's media creator and then start over with a fresh download.

Thanks for all the suggestions.
I'm on the road and can't be with a dead machine - I'll wait until I return home this week to play.

---

### Post by stork123 on 2010-06-01
Reinstalled from usb and things are working great - well... as great as everyone on the above 12 pages.
A partial install was the problem... not sure how that happened.

---

### Post by slyrogue on 2010-06-06
The function keys (like the screen brightness) work in kernel    v2.6.28 (and maybe earlier), but not in 2.6.30.  

I found this out accidentally; I was playing around with crunchbang and the liveCD starts out with v2.6.28 on it.  To my surprise (I've had the fn key problem as well with other distros), the screen brightness and numlock functions both worked.  Those were the only ones I tested.

When I updated the kernel to 2.6.30 (wireless wasn't supported by .28), the function abilities stopped working.  I haven't tried compiling my own kernel yet, though I'm thinking about trying.

Hope this might spur others on to take a look.  BTW, I haven't seen a bug report submitted for the fn stuff; has anyone come across one yet?

-Hound, <Toshiba NB305 running (atm) crunchbang 9.04.01>

(Note: I know this thread has become focused on the sleep/hibernate issue, but I haven't found an off-shoot to focus on the FN issues.  If you know of one, please let me know and I'll post this there as well.)

---

### Post by mseymour on 2010-06-09
I can confirm the problems with suspend/hibernate, brightness keys, and audio (when nohz and highres is set to off) on Ubuntu 10.04 (Desktop) on my Toshiba NB305.

I just started using Ubuntu (officially) for the first time on Saturday, so there's not much else that I can do to help with diagnosing the pulseaudio problem. ;)

---

### Post by sobolosrios on 2010-06-10
The following does not work for fixing the suspend/resume problem.  I am including it here only so that others don't try.

I wondered if the problem could be that the tickless clock somehow had a bug in its relationship with ahci.  As such, I removed the ahci module, set the SATA controller to compatibility and then removed the "nohz=off highres=off" as boot parameters.  The boot time is fast (which is, I believe) just because I have the SATA controller set to compatibility.  The suspend/resume problem is the same however, i.e. it takes 5+ minutes to resume from suspend.

---

### Post by benstar on 2010-06-11
I have had similar issues with my NB 305.
After switching SATA mode to compatibility I was able to routinely boot successfully, as opposed to 1/3 times. Then I read the stuff about editing the grub value, changed it, and things seemed to work somewhat better.
Oh, and I changed the SATA mode back to AHCI and it seems fine, so the grub edit seems to be the important thing.

Here's where I'm at now: suspend works, but IFF I first disable networking. When I wake it back up it automatically re-enables networking and works fine.
Hardware buttons for screen brightness do not work.
Sound seems fine, haven't tried headphones yet. Just tried speakers, works fine.

So, the disable-network-before-suspend problem is my big bug. Otherwise very happy with UNR 10.04! Beats having to use Windows XP home by a long way.

-Ben

---

### Post by sobolosrios on 2010-06-11
> **benstar said:**
> I have had similar issues with my NB 305.
After switching SATA mode to compatibility I was able to routinely boot successfully, as opposed to 1/3 times. Then I read the stuff about editing the grub value, changed it, and things seemed to work somewhat better.
Oh, and I changed the SATA mode back to AHCI and it seems fine, so the grub edit seems to be the important thing.

Here's where I'm at now: suspend works, but IFF I first disable networking. When I wake it back up it automatically re-enables networking and works fine.
Hardware buttons for screen brightness do not work.
Sound seems fine, haven't tried headphones yet. Just tried speakers, works fine.

So, the disable-network-before-suspend problem is my big bug. Otherwise very happy with UNR 10.04! Beats having to use Windows XP home by a long way.

-Ben


How did you edit the grub line?  By adding "nohz=off highres=off"?  This is how I have it and I don't need to disable networking before I put it to sleep.

---

### Post by kdrakon on 2010-06-13
not that this is the best solution, but for those of you who are still concerned with the screen brightness and battery life on the nb300, i found out that FN+f6 and FN+f5 work fine when you're in the grub boot menu.  I've got some increase in battery life (also after installing laptop-mode-tools as well).  Also, beneficially, the brightness setting stays the same when you shutdown and reboot.

in case you don't have you're grub menu showing (which is by default in Ubuntu netbook), to do so, you need to comment out GRUB_HIDDEN_TIMEOUT=0 in /etc/default/grub and then update grub with 'sudo update-grub'

for me, this will suffice till we get an update to ubuntu/kernel

ps. forgive me if someone has already mentioned this, but ive only skimmed through this 13 page thread :)

---

### Post by misguided monkey on 2010-06-14
Adding the folowing line to /etc/default/grub worked for me

```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash nohz=off highres=off"
```

It solved the resume from suspend problem and also cured the very long bootup.

---

### Post by kdrakon on 2010-06-15
> **Iscran said:**
> How many hours does everyone get out of their battery when running ubuntu? I'm getting an an estimated 5.5 out of a full charge. That's a bit disappointing.

yeah, i get 5.5 to barely 6 with all the modifications mentioned in this thread.  it is disappointing considering the netbook is advertised with 9hrs battery life and almost all internet reviews confirm at least 8hrs with normal usage (with Windows i presume).

im gonna try the meego distro soon just to compare battery life since it is "supposed" to be optimised for the atom cpu and power usage.  im just wary cause i know it doesnt support 3G usb modems out of the box

---

### Post by sobolosrios on 2010-06-15
> **kdrakon said:**
> yeah, i get 5.5 to barely 6 with all the modifications mentioned in this thread.  it is disappointing considering the netbook is advertised with 9hrs battery life and almost all internet reviews confirm at least 8hrs with normal usage (with Windows i presume).

im gonna try the meego distro soon just to compare battery life since it is "supposed" to be optimised for the atom cpu and power usage.  im just wary cause i know it doesnt support 3G usb modems out of the box

I think a big portion of the low battery life can be explained by the nohz=off and highres=off.  These basically turn off the tickless kernel so the kernel wakes itself a lot every second.  This increases battery usage.  In a non-scientific test I booted without the kernel parameters above and I was able to get the watt usage down to about 8 whereas with those options it was around 12.5.  That's a 33% decrease in power consumption.  A 33% increase in battery life would take it from about 6 hours to about 8 hours, which is approximately what we would otherwise expect.

Just as an FYI.  I have upgraded to Maverick Meerkat alpha 1 which runs kernel 2.6.35.  This updated kernel doesn't fix the suspend/resumeI issue.  It appears that we really are on our own to fix this as the kernel maintainers don't seem to be noticing it.  

I wonder how big a pile of money one has to collect to get their attention.  I would put up at least $50.

---

### Post by kdrakon on 2010-06-15
interesting, thanks for the research sobolosrios.  with our current status, i guess it's just a matter of what you care about more: the ability to suspend/resume or generally lower power usage.

i think i may go for the latter.

---

### Post by benstar on 2010-06-17
> **sobolosrios said:**
> How did you edit the grub line?  By adding "nohz=off highres=off"?  This is how I have it and I don't need to disable networking before I put it to sleep.

Yep, to be precise mine says: "splash nohz=off highres=off"

And battery life does seem kinda shortish... I haven't tried using the ubuntu power settings yet. 
And FN-F6 does nothing. Oop, just noticed that they said only at the grub screen. Is there no other way to adjust screen brightness? I can't find one...

-Ben

---

### Post by sobolosrios on 2010-06-17
> **kdrakon said:**
> 
i think i may go for the latter.

That's the choice that I have made.

---

### Post by sobolosrios on 2010-06-17
> **benstar said:**
> Yep, to be precise mine says: "splash nohz=off highres=off"

And battery life does seem kinda shortish... I haven't tried using the ubuntu power settings yet. 
And FN-F6 does nothing. Oop, just noticed that they said only at the grub screen. Is there no other way to adjust screen brightness? I can't find one...

-Ben

As discussed previously, Jolicloud (which is based on Ubuntu 9.04) has the brightness keys working.  Iscran and I have made several attempts to figure out how to make this work in Ubuntu, but have been unsuccessful.

---

### Post by jim_charlton on 2010-06-22
A solution/workaround has been found for booting Ubuntu on a Toshiba nb305 without the "nohz=off highres=off" kernel parameters. See [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/508516](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/508516).  This includes a workaround to use hibernate instead of suspend for lid closed/open that doesn't work too bad for resuming running programs.  Pulseaudio also now works with no alteration.

---

### Post by cantech on 2010-06-23
hi .. i have nb205 and my only problem is the startup.. when the black cursor comes out it takes several minutes to see the UBUNTU screen. 

Im updating everything but it seems not going to change.. 

any ideas ?

thanks

---

### Post by ckcoolic on 2010-06-27
> **jim_charlton said:**
> A solution/workaround has been found for booting Ubuntu on a Toshiba nb305 without the "nohz=off highres=off" kernel parameters. See [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/508516](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/508516).  This includes a workaround to use hibernate instead of suspend for lid closed/open that doesn't work too bad for resuming running programs.  Pulseaudio also now works with no alteration.

Between the posts of what did work and what didnt, I'm having trouble understanding what exactly I'm supposed to do.  Is there a way to throw up either here or there some step-by-step instructions consolidated in one post?

---

### Post by sobolosrios on 2010-06-27
> **ckcoolic said:**
> Between the posts of what did work and what didnt, I'm having trouble understanding what exactly I'm supposed to do.  Is there a way to throw up either here or there some step-by-step instructions consolidated in one post?

What would you like to do in particular?  The instructions at the Launchpad link are a way to fix the suspend/resume issue.  Actually, they really fix the hibernate/resume issue.

The crux is you need to 

1.  Install uswsusp:

sudo apt-get install uswsusp


2.  Create the file 

/etc/pm/config.d/00sleep_module

and in the file make the first and only line

SLEEP_MODULE=uswsusp

That will make the machine hibernate and resume from hibernation (resume takes about 15 seconds)

3.  To configure so that this will happen when the lid closes, from a terminal type

gconf-editor

Then go to apps->gnome-power-manager->buttons and change lid_ac and lid_battery to hibernate instead of suspend.


On a related note, jim_charlton has put in _a lot_ of work on this problem.  He deserves some thanks either verbal or monetary, if you can find it in your heart.

---

### Post by ckcoolic on 2010-06-28
Do I change the grub command line back from "splash nohz=off highres=off" to what it was originally?  Does anyone remember what the original line was?  

Do I keep the SATA controller set at compatibility or do I revert back to what the default was?

OK, pretty basic but, how do I create a file?

---

### Post by ckcoolic on 2010-06-28
Oh, and dont think us non-computer sorts arent grateful to you and Jim and everyone else who has contributed solutions and fixes to these bugs.  You are the reason that open source programs are now usable by mainstream people.  Linux has come a long way since I watched my roommates play with it in college.

---

### Post by jta46 on 2010-06-28
First I would like to thank Jim Charlton for this fix.

I have been using 9.10 for ~1yr on an Acer with no problems. I just bought the Toshiba 
NB305 and was having the suspend/hibernate resume issue.

Post number 138 did the trick so thanks also to sobolosrios.

Now just need fn f6/f7 fix for screen brightness

---

### Post by ckcoolic on 2010-06-28
I think I have it figured out and so far it is working.   I think I like hibernate better than suspend anyway.  Thank you everyone.

---

### Post by sobolosrios on 2010-06-28
> **ckcoolic said:**
> I think I have it figured out and so far it is working.   I think I like hibernate better than suspend anyway.  Thank you everyone.

I'm glad it is working now.

---

### Post by jta46 on 2010-07-05
I just wanted to follow up. I'm still grateful for  the workaround as it is better than without. However, I've still been having intermittent issues with resume from hibernate??
Sometimes it works fine and other times it won't resume??
Cheers

---

### Post by BENthesoundman on 2010-07-07
hibernate works now thx, it's good as any other I guess. Anyone got a clue about the black light issues, mine seems to be stuck in minimal light mode; I'd love to be able to scale that up and down next.

---

### Post by jta46 on 2010-07-07
If you left the orig OS you could boot into Windows and try setting it there
I haven't tried this but it seems logical

---

### Post by MadTheologian on 2010-07-09
I've just installed 10.04 LTS as a dual-boot on my NB305 and my problem is with those low battery notices when I remove the power cord.  The power manager notified me that I have FOUR MINUTES left and the laptop battery is critically low-- although it is fully charged at 100%.  I do not think my battery went bad, as battery life with Windows 7 Starter is at 6 hours.  

Do I need to do an update or add an line to some file? If you can help, that would be great.  Thanks!

---

### Post by AltomineUK on 2010-07-09
I would suggest Ubuntu 10.04 as it will have the latest support for device drivers (such as bluetooth etc). As for the pre-mature low battery warning....can't remember how to solve it...there was a post somewhere around here addressing the same issue.

---

### Post by AndrewX192 on 2010-07-10
I found a better fix for suspend/hibernate that doesn't drain power down.
When the netbook is starting up, press F2 to enter the BIOS, goto the "Advanced" tab and select "Dynamic CPU Frequency Mode:" and set it to "Always low". I'm now working on a solution for the capslock light, and screen backlight controls. I've also made some changes which get me 8-9 hours of battery life, which is better but still a ways off of what Windows gets.

---

### Post by alitheia on 2010-07-10
> **AndrewX192 said:**
> I found a better fix for suspend/hibernate that doesn't drain power down.
When the netbook is starting up, press F2 to enter the BIOS, goto the "Advanced" tab and select "Dynamic CPU Frequency Mode:" and set it to "Always low". I'm now working on a solution for the capslock light, and screen backlight controls. I've also made some changes which get me 8-9 hours of battery life, which is better but still a ways off of what Windows gets.

Thanks Sobolosrios and Andrew! Andrew's fix works for my nb305 perfectly. Would you mind sharing how you tweaked the battery life?

---

### Post by AndrewX192 on 2010-07-10
> **alitheia said:**
> Thanks Sobolosrios and Andrew! Andrew's fix works for my nb305 perfectly. Would you mind sharing how you tweaked the battery life?
Great to here that it's working for you. I am currently changing my Ubuntu setup such that I have a hybrid SD/HDD boot for even better power management. I'l get the fixes up for power management once I have them all tested. You can try powertop for now and see what you can get.

Also, has anyone had success with the Toshiba HDD protection sensor?

---

### Post by jmesmon on 2010-07-15
I bisected the fn-key brightness adjustment failure.

Bug on the kernel's bugzilla:
[https://bugzilla.kernel.org/show_bug.cgi?id=16405](https://bugzilla.kernel.org/show_bug.cgi?id=16405)

First Bad commit:
[74a365b3f354fafc537efa5867deb7a9fadbfe27] ACPI: Populate DIDL before registering ACPI video device on Intel

Edit:
Temporary patch I've applied to git kernel to get brightness adjustment to work:

```

From ff3487138494a284542a8b25b083f332d4d75727 Mon Sep 17 00:00:00 2001
From: John Mesmon <jmesmon@gmail.com>
Date: Thu, 22 Jul 2010 23:41:12 -0400
Subject: [PATCH] acpi i915: be sure acpi video is registered

Even on error, intel_opregion_init needs to call acpi_video_register if
it has been defered due to the detection of opregion support in
drivers/acpi/video.c.
---
 drivers/gpu/drm/i915/i915_opregion.c |    3 +++
 1 files changed, 3 insertions(+), 0 deletions(-)

diff --git a/drivers/gpu/drm/i915/i915_opregion.c b/drivers/gpu/drm/i915/i915_opregion.c
index 8fcc75c..c92163c 100644
--- a/drivers/gpu/drm/i915/i915_opregion.c
+++ b/drivers/gpu/drm/i915/i915_opregion.c
@@ -533,6 +533,9 @@ int intel_opregion_init(struct drm_device *dev, int resume)
 	return 0;
 
 err_out:
+	if (!resume)
+		acpi_video_register();
+
 	iounmap(opregion->header);
 	opregion->header = NULL;
 	return err;
-- 
1.7.1.1

```

---

### Post by nedflenders on 2010-07-24
Hey Toshiba NB3005 owners,

Just wanted to drop a line on this.

In order to get bluetooth working, their are just a few simple steps now.
You no longer need to edit omnibook source and compile.

Just run this command and bluetooth will enable:
```
sudo modprobe omnibook ectype=14 
```You will also see the bluetooth icon appear on the taskbar.

You can make the module start on boot:

make a file called omnibook.modprobe in /etc/modprobe.d/ and place the  module options in it:

```
options omnibook ectype=14 userset=1 
```append “omnibook” to /etc/modules to load it at boot:

```

$ sudo su
# echo “omnibook” > /etc/modules

```My system info:
flenders@TOSH:~$ uname -a
Linux TOSH 2.6.32-23-generic #37-Ubuntu SMP Fri Jun 11 07:54:58 UTC 2010 i686 GNU/Linux
Lucid 10.04 LTS

---

### Post by AcidSyl on 2010-07-25
John, thanks a lot for finding out how to fix the brightness keys.

Since I am a Ubuntu beginner, I have no idea how to actually install the patch. Is there any easy way to do this?

---

### Post by slj on 2010-08-05
> **AndrewX192 said:**
> I found a better fix for suspend/hibernate that doesn't drain power down.
When the netbook is starting up, press F2 to enter the BIOS, goto the "Advanced" tab and select "Dynamic CPU Frequency Mode:" and set it to "Always low". I'm now working on a solution for the capslock light, and screen backlight controls. I've also made some changes which get me 8-9 hours of battery life, which is better but still a ways off of what Windows gets.

Just wanted to note that Andrew's fix worked for me--suspend/hibernate are now functional. My computer is a NB305-N310 running Ubuntu release 10.04.

Thanks!

---

### Post by zairulazwan on 2010-08-05
But if i only use ubuntu no other OS do i still need to edit GRUB

---

### Post by slj on 2010-08-05
> **zairulazwan said:**
> But if i only use ubuntu no other OS do i still need to edit GRUB
I didn't need to edit GRUB and I'm in your situation--no other OS is installed on my computer.

---

### Post by sobolosrios on 2010-08-06
> **AndrewX192 said:**
> I found a better fix for suspend/hibernate that doesn't drain power down.
When the netbook is starting up, press F2 to enter the BIOS, goto the "Advanced" tab and select "Dynamic CPU Frequency Mode:" and set it to "Always low". I'm now working on a solution for the capslock light, and screen backlight controls. I've also made some changes which get me 8-9 hours of battery life, which is better but still a ways off of what Windows gets.

Correct me if I'm wrong, but doesn't this make it so that the CPU always runs at 1.0Ghz?  While reasonable at times, this might not always be desirable performance wise.

---

### Post by Domin8 on 2010-09-01
> **sobolosrios said:**
> Correct me if I'm wrong, but doesn't this make it so that the CPU always runs at 1.0Ghz?  While reasonable at times, this might not always be desirable performance wise.

i found this

> For computers that are equipped with a mobile Pentium® processor with Intel® SpeedStepTM technology, you can set the CPU Frequency Mode as:

Dynamically Switchable —This mode is the default setting for your computer, and automatically changes the processor’s frequency depending on the power source:

&#10070;	AC Power — If your computer is connected to the AC adapter, the CPU frequency mode is set to High for faster processing.

&#10070;	Battery Power — If your computer is running on battery power, the CPU frequency mode is set to Low for slower processing, however, the processor will increase its speed when additional processing power is required. Switching the CPU to Low allows you to conserve power and extend the operating time of your battery.

Always High — Sets the CPU speed to High for both battery and AC power.

Always Low — Sets the CPU speed to Low for both battery and AC power.
By changing any of the options that appear in the dialog boxes and clicking Apply, you can reconfigure that function. Any options that you change will not take effect until after you restart your computer.

it seems as though always low would be better for battery life then, albeit not running at full speed. i wonder if its noticeable though...

---

### Post by Optimus Prime on 2010-09-01
> **Domin8 said:**
> it seems as though always low would be better for battery life then, albeit not running at full speed. i wonder if its noticeable though...

This is not quite true. Matthew Garrett has compiled some observations on power management which include this topic.

[http://www.codon.org.uk/~mjg59/power/good_practices.html](http://www.codon.org.uk/~mjg59/power/good_practices.html)

---

### Post by ufendou on 2010-09-07
Would you mind posting a step by step guidance on how to apply this patch? I am totally new to Ubuntu, much appreciated.

---

### Post by ufendou on 2010-09-07
> **jmesmon said:**
> I bisected the fn-key brightness adjustment failure.

Bug on the kernel's bugzilla:
[https://bugzilla.kernel.org/show_bug.cgi?id=16405](https://bugzilla.kernel.org/show_bug.cgi?id=16405)

First Bad commit:
[74a365b3f354fafc537efa5867deb7a9fadbfe27] ACPI: Populate DIDL before registering ACPI video device on Intel

Edit:
Temporary patch I've applied to git kernel to get brightness adjustment to work:

```

From ff3487138494a284542a8b25b083f332d4d75727 Mon Sep 17 00:00:00 2001
From: John Mesmon <jmesmon@gmail.com>
Date: Thu, 22 Jul 2010 23:41:12 -0400
Subject: [PATCH] acpi i915: be sure acpi video is registered

Even on error, intel_opregion_init needs to call acpi_video_register if
it has been defered due to the detection of opregion support in
drivers/acpi/video.c.
---
 drivers/gpu/drm/i915/i915_opregion.c |    3 +++
 1 files changed, 3 insertions(+), 0 deletions(-)

diff --git a/drivers/gpu/drm/i915/i915_opregion.c b/drivers/gpu/drm/i915/i915_opregion.c
index 8fcc75c..c92163c 100644
--- a/drivers/gpu/drm/i915/i915_opregion.c
+++ b/drivers/gpu/drm/i915/i915_opregion.c
@@ -533,6 +533,9 @@ int intel_opregion_init(struct drm_device *dev, int resume)
     return 0;
 
 err_out:
+    if (!resume)
+        acpi_video_register();
+
     iounmap(opregion->header);
     opregion->header = NULL;
     return err;
-- 
1.7.1.1

```


Would you mind posting a step by step guidance on how to apply this patch? I am totally new to Ubuntu, much appreciated.

---

### Post by Osios on 2010-09-10
Hello

Would you be so kind and summarize the situation about Ubuntu+Toshiba NB 300/305?
We have quite a lot pages here -> so, what works, what not? :)
I am novice at Ubuntu and I would like to try switch from Windows 7.

Thank you very much

(Sorry for my english, I am from Czech rep.)

---

### Post by exculuber on 2010-09-10
I agree with Osios. My netbook which is toshiba NB305, i've installed ubuntu netbook remix 10.4 and updated after installation. However, while it is booting, there is a single "_" charachter top of the screen for 2-3 minutes before ubuntu boots. At the same time, I could not find how to adjust brightness. It is always same and keyboard functions doesn't work.
I really appriciate if the people who fixed this problems answer.
Thanks

---

### Post by rapidDazz on 2010-09-17
The extremely slow boot times I've contributed (and solved for myself) via the BIOS and the Sata configuration setting.  Changing it to compatibility over AHCI did absolute wonders for boot speeds.

However I still can't get my wireless to turn on.  Reading particular posts it's suggested that I have to boot into windows, enable it, then come back to ubuntu.  I hope not, as I don't have windows installed on this anymore.

---

### Post by disc0tech on 2010-09-21
I did the below, now my laptop boots in < 30 secs 

1) sudo gedit /etc/default/grub
2) Change: GRUB_CMDLINE_LINUX_DEFAULT="splash nohz=off highres=off"
3) sudo update-grub (I don't know if I had to do this.)
4) restart

---

### Post by AndrewX192 on 2010-09-23
> **disc0tech said:**
> I did the below, now my laptop boots in < 30 secs 

1) sudo gedit /etc/default/grub
2) Change: GRUB_CMDLINE_LINUX_DEFAULT="splash nohz=off highres=off"
3) sudo update-grub (I don't know if I had to do this.)
4) restart

I recommend against doing this. Disabling nohz and highres will cause your netbook to draw a large amount of power, resulting in short battery life.

---

### Post by Optimus Prime on 2010-10-02
Here's a current status update for those who asked.

**Backlight control** Working! This is significant as it brings power usage on my NB305 from between 10 and 11 Watts to between 6 and 7 Watts, doubling the battery life! Thanks to jmesmon for the patch, it has been committed upstream. This patch won't show up in Ubuntu's kernel until Natty. The easiest way to enable this functionality now is to run the latest 2.6.36 from the mainline kernel PPA, with the caveat that this kernel is unsupported and lacks the Ubuntu drivers.

**Boot without hanging** Working! Using the "nohz=off highres=off" parameters in Grub boots without the CPU hanging from this computer's buggy acpi. Yes, the tickless kernel is more efficient, but with the ability to dim the screen, I can still get about 10 hours of battery life. The caveat to this is that Pulseaudio will lose sync at times and audio will become corrupted. The solutions to that are to either boot without the nohz and highres flags, or what has worked for me has been to keep volume levels below the maximum.

**Resume from suspend** Working on Lucid, broken on later kernels. This also requires the "nohz=off highres=off" parameters. Want to help? Take a look at [https://wiki.ubuntu.com/DebuggingKernelSuspend](https://wiki.ubuntu.com/DebuggingKernelSuspend)

In summary, it is currently possible to use the full functionality of your machine, but it requires some work to set up and will not work out of the box until at least Ubuntu 11.04, 6 months away.

---

### Post by unicycletim on 2010-10-06
I just installed 2.6.36.
Wow, I didn't realise how awesome being able to change the backlight brightness really is...

Thanks for all the awesome work you guys have done.

Does anyone know how to make the brightness in/decreases less obvious. It takes four or five presses between min and max brightness

---

### Post by Jacob111 on 2010-10-07
Oh great, I'm glad somebody figured out the screen brightness problem.  I'm going to try that soon.  Has somebody figured out how to turn the wireless on and off, thus saving further power?  Right now on my NB305, the wireless works and connects to networks, but the fctn key to toggle power doesn't do anything.  Maybe a solution was mentioned somewhere else in this thread, but this thread is also 17 pages long.

---

### Post by unicycletim on 2010-10-11
Hmmm. The new kernel seems to make the sound from some videos really jumpy, impossible to listen to. I just reverted to 2.6.35 and the same video played perfectly

---

### Post by hatemben on 2010-10-12
Upgraded to Maverick, and compiled Kernel 2.6.36-rc7.

All issues seems to be fixed : Suspend/Wakeup, Brightness F6/F7 keys, Startup time... Didn't add any additional settings (GRUB_CMDLINE_LINUX_DEFAULT="quiet splash")

Just need to tweak it to reduce power usage.

Tested on Toshiba NB300

---

### Post by odysseus2k7 on 2010-10-14
> **hatemben said:**
> Upgraded to Maverick, and compiled Kernel 2.6.36-rc7.

All issues seems to be fixed : Suspend/Wakeup, Brightness F6/F7 keys, Startup time... Didn't add any additional settings (GRUB_CMDLINE_LINUX_DEFAULT="quiet splash")

Just need to tweak it to reduce power usage.

Tested on Toshiba NB300

For those of us who are kind of new to Linux, would you mind giving instructions on how to install the new kernel?  I just downloaded it but have no clue what to do next and don't want to break my system...

Thanks,

:guitar:

---

### Post by hatemben on 2010-10-14
> **odysseus2k7 said:**
> For those of us who are kind of new to Linux, would you mind giving instructions on how to install the new kernel?  I just downloaded it but have no clue what to do next and don't want to break my system...

Thanks,

:guitar:

Instructions available here :
[https://help.ubuntu.com/community/Kernel/Compile#Alternate%20Build%20Method:%20The%20Old-Fashioned%20Debian%20Way](https://help.ubuntu.com/community/Kernel/Compile#Alternate%20Build%20Method:%20The%20Old-Fashioned%20Debian%20Way)

---

### Post by odysseus2k7 on 2010-10-14
> **hatemben said:**
> Instructions available here :
[https://help.ubuntu.com/community/Kernel/Compile#Alternate%20Build%20Method:%20The%20Old-Fashioned%20Debian%20Way](https://help.ubuntu.com/community/Kernel/Compile#Alternate%20Build%20Method:%20The%20Old-Fashioned%20Debian%20Way)

Thanks again.  I'll work on that tonight and see where I get. The instructions seem pretty clear.  I have downloaded the rc7 kernel and looked over the "README" and "Changes" files already, so I hope the new version solves my problems. (slow booting, poor battery life, hibernate/wake issues, etc.)

Thanks,
:guitar:

---

### Post by BSD_dad on 2010-10-15
kernel install instructions here also
[https://wiki.ubuntu.com/Kernel/MainlineBuilds?action=show&redirect=KernelTeam%2FMainlineBuilds](https://wiki.ubuntu.com/Kernel/MainlineBuilds?action=show&redirect=KernelTeam%2FMainlineBuilds)

---

### Post by BSD_dad on 2010-10-15
> **hatemben said:**
> Upgraded to Maverick, and compiled Kernel 2.6.36-rc7.

All issues seems to be fixed : Suspend/Wakeup, Brightness F6/F7 keys, Startup time... Didn't add any additional settings (GRUB_CMDLINE_LINUX_DEFAULT="quiet splash")

Just need to tweak it to reduce power usage.

Tested on Toshiba NB300

Running Maverick on NB305 with 2.3.6-rc7. Would not boot set as above, dropped to shell of some sort with cpu speed dynamic. 

Changed grub GRUB_CMDLINE_LINUX_DEFAULT="splash nohz=off highres=off" and get boot at right on 30 seconds from power switch press. CPU speed set to dynamic. 

Brightness works, hibernate works, suspend does not resume. Better than it was with cpu set always low! Looking forward to 11.04

---

### Post by BSD_dad on 2010-10-15
Setting the touchpad disable under System>Mouse doesn't seem to work, however found [this]("http://maketecheasier.com/13-ways-to-customize-ubuntu-netbook-remix-for-better-usability/2010/02/07") (see #12) and Syndaemon works fine.

---

### Post by odysseus2k7 on 2010-10-16
> **BSD_dad said:**
> Running Maverick on NB305 with 2.3.6-rc7. Would not boot set as above, dropped to shell of some sort with cpu speed dynamic. 

Changed grub GRUB_CMDLINE_LINUX_DEFAULT="splash nohz=off highres=off" and get boot at right on 30 seconds from power switch press. CPU speed set to dynamic. 

Brightness works, hibernate works, suspend does not resume. Better than it was with cpu set always low! Looking forward to 11.04


All these websites are great, but would someone be so kind as to post a complete set of instructions in one place for compiling and installing rc7 on the NB305?

---

### Post by nichopl83 on 2010-10-16
guys i have a problem
i got toshiba nb300 - ubuntu netbook edition 10.04 works good for me but ubuntu netbook edition 10.10 is completly unuseable - it's slow, on boot i must touch enter or else to boot ubuntu, divx/xvid & youtube movies are slow, unwatchable - what to hell is wrong with new ubuntu netbook edition distro? i know i can go back to 10.04 but i want to have new distro
please help

---

### Post by lrcvrino on 2010-10-16
> **nichopl83 said:**
> guys i have a problem
i got toshiba nb300 - ubuntu netbook edition 10.04 works good for me but ubuntu netbook edition 10.10 is completly unuseable - it's slow, on boot i must touch enter or else to boot ubuntu, divx/xvid & youtube movies are slow, unwatchable - what to hell is wrong with new ubuntu netbook edition distro? i know i can go back to 10.04 but i want to have new distro
please help
hi, try this:
on startup press F2
on bios > avanced > SATA controller Mode change AHCI to Compatibility

and that's it!

sorry for my english

---

### Post by odysseus2k7 on 2010-10-17
> **nichopl83 said:**
> guys i have a problem
i got toshiba nb300 - ubuntu netbook edition 10.04 works good for me but ubuntu netbook edition 10.10 is completly unuseable - it's slow, on boot i must touch enter or else to boot ubuntu, divx/xvid & youtube movies are slow, unwatchable - what to hell is wrong with new ubuntu netbook edition distro? i know i can go back to 10.04 but i want to have new distro
please help

I was getting the slow boot times too, having to hit "enter" multiple times to get it to progress.  I changed my CPU speed to "Always Low" instead of "Dynamic" in the BIOS, and it took care of that problem.  Of course, I'd like to run it Dynamic to get the best performance, but I can put up with it for now.  I've watched videos with no problems in this mode too.  

I still have the other problems of not being able to control screen brightness, the sleep/wake problem, and terrible battery life.  I gave up on compiling rc7.  It's really frustrating, and I wish the team had just held off on releasing it until they could use a better kernel.

---

### Post by eyesofibad on 2010-10-17
Not sure if this was the right way to do this, but it worked.  After downloading the rc7 kernel, I just right clicked it and installed it using ubuntu software manager.  Everything seems to be working, brightness, hibernate, normal boot.  Suspend isn't working but I'll deal.  I did take lrcvrino's suggestion to change the SATA controller Mode from AHCI to Compatibility. Didn't have to disable high res timers.

---

### Post by odysseus2k7 on 2010-10-19
> **eyesofibad said:**
> Not sure if this was the right way to do this, but it worked.  After downloading the rc7 kernel, I just right clicked it and installed it using ubuntu software manager.  Everything seems to be working, brightness, hibernate, normal boot.  Suspend isn't working but I'll deal.  I did take lrcvrino's suggestion to change the SATA controller Mode from AHCI to Compatibility. Didn't have to disable high res timers.

I may have to try that.  I've already done a clean install twice so nothing ventured, etc.

---

### Post by odysseus2k7 on 2010-10-19
What command did you use?  The only options I get are variations of "Open" and "Open with Other Application".  The list of applications does not include the Software Manager.  I have tried using the Synaptic Package Manager with no success, and the Update Manager doesn't see it at all.

---

### Post by brodiewells on 2010-10-19
> **rapidDazz said:**
> The extremely slow boot times I've contributed (and solved for myself) via the BIOS and the Sata configuration setting.  Changing it to compatibility over AHCI did absolute wonders for boot speeds.

However I still can't get my wireless to turn on.  Reading particular posts it's suggested that I have to boot into windows, enable it, then come back to ubuntu.  I hope not, as I don't have windows installed on this anymore.

Did you ever get this fixed?  I can't get my mouse to work and everything I have read says that I need to switch to windows to enable it also.

---

### Post by kingsrule5 on 2010-10-21
am I the only one who is now having issues where 10.10 seemed to install fine but then won't run and even a live cd from a usb drive won't boot?

[http://ubuntuforums.org/showthread.php?t=1595810](http://ubuntuforums.org/showthread.php?t=1595810)

---

### Post by odysseus2k7 on 2010-10-22
> **kingsrule5 said:**
> am I the only one who is now having issues where 10.10 seemed to install fine but then won't run and even a live cd from a usb drive won't boot?

[http://ubuntuforums.org/showthread.php?t=1595810](http://ubuntuforums.org/showthread.php?t=1595810)

I have given up on UNR 10.10.  I'm now running xubuntu 10.10 with no problems.  I still don't have the full functionality I'd expect (still can't adjust screen brightness, battery life still sucks) but it runs consistently and hibernates and wakes up normally after I close the lid.

Also, the Unity interface sucks.  Sorry, but there it is.  It's hard to use, it limits your screen space (even though it's supposed to be 'optimised') and it's slow.  I had better usability running it in Ubuntu desktop mode.  So, 10.10 is kind of a disappointment.  I thought 10.04 was brilliant, and that's what sold me on the OS.  I hope they fix all this in 11.04.

---

### Post by eyesofibad on 2010-10-23
> **odysseus2k7 said:**
> What command did you use?  The only options I get are variations of "Open" and "Open with Other Application".  The list of applications does not include the Software Manager.  I have tried using the Synaptic Package Manager with no success, and the Update Manager doesn't see it at all.

These instructions helped me.  I downloaded with Firefox, then just opened the files from the downloads window (right click, open).  [http://www.ramoonus.nl/2010/10/linux-kernel-2-6-36-installation-guide-ubuntu-linux/?utm_source=rss&utm_medium=rss&utm_campaign=linux-kernel-2-6-36-installation-guide-ubuntu-linux](http://www.ramoonus.nl/2010/10/linux-kernel-2-6-36-installation-guide-ubuntu-linux/?utm_source=rss&utm_medium=rss&utm_campaign=linux-kernel-2-6-36-installation-guide-ubuntu-linux)

---

### Post by Benchthug on 2010-10-24
I'm a new user of ubuntu but been playing with it for a month now I have a NB305 with 2gb ram. I installed UNR 10.10 and as it install i keep pressing the DEL key so the installation will progress. I also installed Kubuntu but Kubuntu has an option to type in nohz=off and highres=off. With UNR just hold down the del key to keep the installation going. after successfully installing UNR on login i changed the interface from UNR to desktop edition "the option is on the bottom when you click on your name" 

Bois setting
Lan - disable
sata- achi
cpu - always low
HD - battery life

so far i can get 6 1/2 hours of battery life and its long enough for school work and watching movies on class break. 

I also configured my startup application making sure it will only start what i need and im using Chromium. 

with my setup can hibernate and sleep but can't dim the screen.

future plan: will install SSD

---

### Post by odysseus2k7 on 2010-10-24
> **eyesofibad said:**
> These instructions helped me.  I downloaded with Firefox, then just opened the files from the downloads window (right click, open).  [http://www.ramoonus.nl/2010/10/linux-kernel-2-6-36-installation-guide-ubuntu-linux/?utm_source=rss&utm_medium=rss&utm_campaign=linux-kernel-2-6-36-installation-guide-ubuntu-linux](http://www.ramoonus.nl/2010/10/linux-kernel-2-6-36-installation-guide-ubuntu-linux/?utm_source=rss&utm_medium=rss&utm_campaign=linux-kernel-2-6-36-installation-guide-ubuntu-linux)

Okay, that was brilliant.  I went to the site and downloaded the latest stable version (2.6.36) and followed the instructions exactly.  My brightness controls work, and I'm stress-testing the hibernate/sleep functions now.  Battery life is about 6:44 with the screen dimmed about 50%.  Thanks very much!  UNR 10.10 is usable again!

---

### Post by seanluse on 2010-10-24
Wondering about how powersave affects cpu in 10.10 on an NB200.
I think it should be similar enough.

It seems that loading webpages, playing videos, or even starting applications requires constant mouse movement, otherwise the loading hangs.

Using kernel 2.6.35-22, with 2gb ram.

Anyone else, nb300 or otherwise have this problem?

---

### Post by odysseus2k7 on 2010-10-25
> **seanluse said:**
> Wondering about how powersave affects cpu in 10.10 on an NB200.
I think it should be similar enough.

It seems that loading webpages, playing videos, or even starting applications requires constant mouse movement, otherwise the loading hangs.

Using kernel 2.6.35-22, with 2gb ram.

Anyone else, nb300 or otherwise have this problem?

I had to switch my CPU speed from "Dynamic" to "Always Low".  

Now using a NB305, kernel 2.6.36, 1GB RAM.

---

### Post by eyesofibad on 2010-10-26
I tried the "always low" setting and found it unusably slow.  Holding Enter while booting is a small price to pay for the speed until someone gets this figured out.  I also dropped the netbook version of Ubuntu and went with the regular desktop version.  The unity interface was just bogging everything down too much.  The regular desktop version of Ubuntu seems much faster.  I usually put on Gnome Do so I don't worry too much about the interface anyway.

---

### Post by eyesofibad on 2010-10-27
This morning I got an invite to the Jolicloud 1.1 beta and hibernate and brightness work without any tweaking!  Right now the boot time is about 30 seconds without having to press anything, and about the same resuming from hibernate.  I'm getting 6.5 hours battery and it's blazing fast and responsive. The 1.1 beta isn't currently public, but it may be something to keep an eye on.   They have a Chromium OS type philosophy where everything is in the cloud, so it may not be to everyone's liking but it has been really nice as a duel boot when I need to do something quick -even more so now with the hibernate support.  [http://www.jolicloud.com/](http://www.jolicloud.com/)

---

### Post by BSD_dad on 2010-10-28
> **seanluse said:**
> It seems that loading webpages, playing videos, or even starting applications requires constant mouse movement, otherwise the loading hangs.

Using kernel 2.6.35-22, with 2gb ram.

Anyone else, nb300 or otherwise have this problem?

I saw some of those things. NB305, 10.10

Install RC7 (follow [this]("https://wiki.ubuntu.com/Kernel/MainlineBuilds?action=show&redirect=KernelTeam%2FMainlineBuilds#Mainline%20Kernels%20Archive"))
change grub:
> 1) sudo gedit /etc/default/grub
2) Change: GRUB_CMDLINE_LINUX_DEFAULT="splash nohz=off highres=off"
3) sudo update-grub
4) restart

In bios (F2 on restart, be quick about it!) set:
Advanced > SATA mode = Compatibility
Speed = Dynamic

---

### Post by Benchthug on 2010-10-30
I'm using NB305 CPU@Dynamic SATA@Compatible HD@performance
Using kernel 2.6.36 from 
[http://www.ramoonus.nl/2010/10/linux-kernel-2-6-36-installation-guide-ubuntu-linux/?utm_source=rss&utm_medium=rss&utm_campaign=linux-kernel-2-6-36-installation-guide-ubuntu-linux](http://www.ramoonus.nl/2010/10/linux-kernel-2-6-36-installation-guide-ubuntu-linux/?utm_source=rss&utm_medium=rss&utm_campaign=linux-kernel-2-6-36-installation-guide-ubuntu-linux)
so far i have 7 hours of battery life in regular use and it doesn't get that hot as to having nohz=off and highres=off
im using ubuntu 10.10 desktop edition :P i just don't like the interface in netbook edition
Brightness-working
volume key - working
hibernate and suspend - working
load time i guess normal less than 20 seconds its not that long :P besides i always hibernate now lol

Good luck to you all :P and please read the previous post for more info about our netbook :P

---

### Post by loungedaddy on 2010-10-30
> **Benchthug said:**
> I'm using NB305 CPU@Dynamic SATA@Compatible HD@performance
Using kernel 2.6.36 from 
[http://www.ramoonus.nl/2010/10/linux-kernel-2-6-36-installation-guide-ubuntu-linux/?utm_source=rss&utm_medium=rss&utm_campaign=linux-kernel-2-6-36-installation-guide-ubuntu-linux](http://www.ramoonus.nl/2010/10/linux-kernel-2-6-36-installation-guide-ubuntu-linux/?utm_source=rss&utm_medium=rss&utm_campaign=linux-kernel-2-6-36-installation-guide-ubuntu-linux)
so far i have 7 hours of battery life in regular use and it doesn't get that hot as to having nohz=off and highres=off
im using ubuntu 10.10 desktop edition :P i just don't like the interface in netbook edition
Brightness-working
volume key - working
hibernate and suspend - working
load time i guess normal less than 20 seconds its not that long :P besides i always hibernate now lol

Good luck to you all :P and please read the previous post for more info about our netbook :P


Fantastic! This fixed my problems also  :)

I'm so happy I want to sing. And now that the music and video isn't getting hung up and skipping all the time, I have something to sing to :guitar:

---

### Post by odysseus2k7 on 2010-10-31
> **loungedaddy said:**
> Fantastic! This fixed my problems also  :)

I'm so happy I want to sing. And now that the music and video isn't getting hung up and skipping all the time, I have something to sing to :guitar:

I just tried the "splash=nohz highres=off" and after I realized what the system was doing, I was pretty happy with it.  Now running in Dynamic CPU mode.

---

### Post by Benchthug on 2010-11-01
> **odysseus2k7 said:**
> I just tried the "splash=nohz highres=off" and after I realized what the system was doing, I was pretty happy with it.  Now running in Dynamic CPU mode.

hmmm is that really in your command line? if it is you don't need it and i don't how that splash=nohz will work... just delete "=nohz highres=off" and for your sata select compatible.

---

### Post by odysseus2k7 on 2010-11-01
> **Benchthug said:**
> hmmm is that really in your command line? if it is you don't need it and i don't how that splash=nohz will work... just delete "=nohz highres=off" and for your sata select compatible.

Sorry, I was typing from memory... of course, it's "splash nohz=off highres=off".  And when I checked it just now I found I'd entered "spash".  For some reason it still worked, though.

---

### Post by JohnTheLutheran on 2010-11-02
I'm thinking of buying an NB300, and have been reading this thread with some alarm. However, I get the impression from posts #191 and #197 that installing the 2.6.36 kernel and headers solves the problems people have been having, without needing to bother with the other "splash nohz=off"-type stuff (which I'm perfectly happy doing, but not happy spending £250+ and then *having* to do it, if you see what I mean). 

Can someone report back on this? If I do a clean install and then install the 2.6.36 kernel, will I be a happy bunny or will I still face having to implement various kludgy workarounds in order to get it to work? 

TIA.

---

### Post by brodiewells on 2010-11-03
> **JohnTheLutheran said:**
> I'm thinking of buying an NB300, and have been reading this thread with some alarm. 

I wouldn't buy it again if I had it to do over.  My mouse broke and Toshiba sucks to work with.  Plus all of these problems make this a piece of junk.

---

### Post by micromartyaka on 2010-11-04
> **JohnTheLutheran said:**
> I'm thinking of buying an NB300, and have been reading this thread with some alarm. However, I get the impression from posts #191 and #197 that installing the 2.6.36 kernel and headers solves the problems people have been having, without needing to bother with the other "splash nohz=off"-type stuff (which I'm perfectly happy doing, but not happy spending £250+ and then *having* to do it, if you see what I mean). 

Can someone report back on this? If I do a clean install and then install the 2.6.36 kernel, will I be a happy bunny or will I still face having to implement various kludgy workarounds in order to get it to work? 

TIA.

After installing the 2.6.36 kernel, Ubuntu runs like a charm on my nb305. Battery life is a little less than windows 7, but I still get about 6/7 hours. Still last through a full day of college class.

---

### Post by odysseus2k7 on 2010-11-04
> **JohnTheLutheran said:**
> I'm thinking of buying an NB300, and have been reading this thread with some alarm. However, I get the impression from posts #191 and #197 that installing the 2.6.36 kernel and headers solves the problems people have been having, without needing to bother with the other "splash nohz=off"-type stuff (which I'm perfectly happy doing, but not happy spending £250+ and then *having* to do it, if you see what I mean). 

Can someone report back on this? If I do a clean install and then install the 2.6.36 kernel, will I be a happy bunny or will I still face having to implement various kludgy workarounds in order to get it to work? 

TIA.

I've had good results from installing the 2.6.36 kernel.  I've waffled back and forth between running it in Dynamic CPU mode and Always Low mode, and to be perfectly honest, I can't tell the difference in performance.  The only difference I've noticed is that in "Always Low" I don't have to do the grub edit, I can leave it as "splash quiet".  There are still a few quirks about it, but overall I'm very happy with my NB305.  And using Ubuntu is better than using Windows any day.

Netbooks are all twitchy little things.  What you have to realize is you're replacing the original OS with what amounts to a non-spec OS.  The Toshiba was designed to run Windows 7; that's what it wants.  With a little tweaking you can make it run a better OS, and that's what we've done here.  

It's Linux.  Tweaking and hacking are part of the fun.

---

### Post by JohnTheLutheran on 2010-11-05
Right. I've just taken delivery of a shiny new NB300, installed Ubuntu Netbook 10.10, installed the 2.6.36-rc7 kernel and headers and... resume from suspend doesn't work. Or rather, it only resumes after loooooooooooooooooooooong delays (10+ minutes).

This applies whether or not I use the "nohz=off highres=off" options in Grub. (Though get the impression those were intended to resolve the booting problems on earlier kernels. It *boots* just fine.) I've also set SATA to Compatibility in the BIOS. 

I need to move quickly on this as I'll need to remove Ubuntu, restore the original Windows partitions and return it for a refund within the cooling-off period if I can't sort this out within 48 hours... 

I've been using Linux since 2004 so am comfortable with tweaking things to deal with teething troubles. But if it's a case of fundamental functionality where the only known fixes don't actually work, I'm going to have to try a different machine. :(

**Edit:** Changing the CPU speed from Dynamic to Always Low solves the Suspend problem, but makes the netbook unusably slow in many respects - YouTube videos can't even play smoothly in embedded form, let alone fullscreen.

---

### Post by odysseus2k7 on 2010-11-05
> **JohnTheLutheran said:**
> Right. I've just taken delivery of a shiny new NB300, installed Ubuntu Netbook 10.10, installed the 2.6.36-rc7 kernel and headers and... resume from suspend doesn't work. Or rather, it only resumes after loooooooooooooooooooooong delays (10+ minutes).

This applies whether or not I use the "nohz=off highres=off" options in Grub. (Though get the impression those were intended to resolve the booting problems on earlier kernels. It *boots* just fine.) I've also set SATA to Compatibility in the BIOS. 

I need to move quickly on this as I'll need to remove Ubuntu, restore the original Windows partitions and return it for a refund within the cooling-off period if I can't sort this out within 48 hours... 

I've been using Linux since 2004 so am comfortable with tweaking things to deal with teething troubles. But if it's a case of fundamental functionality where the only known fixes don't actually work, I'm going to have to try a different machine. :(

**Edit:** Changing the CPU speed from Dynamic to Always Low solves the Suspend problem, but makes the netbook unusably slow in many respects - YouTube videos can't even play smoothly in embedded form, let alone fullscreen.

Resume from suspend doesn't work on mine either.  I use "hibernate" instead.  I think everyone else does too, but I could be wrong.

---

### Post by fasgiu on 2010-11-08
Hi,
I have a toshiba nb305 with ubuntu 10.10 + kernel 2.6.37-rc1-maverick.

This kernel solved my problems: with 2.6.35 I had to move the mouse or press a key to work and brightness key didn't work; with 2.6.36 I had to move the mouse or press a key to work but brightness worked;

With 2.6.37-rc1 no problem running applications and video, fast boot, brightness key works, hibernation works; only suspend to ram doesn't work.

The only trick is to switch in compatibility mode in the bios. No boot parameters or "always low" cpu speed required.

Hope to be useful.
Giuseppe.

---

### Post by JohnTheLutheran on 2010-11-08
Thanks for the various replies. In the end I decided to cut my losses and send back the Toshiba. I'm typing this from my Packard Bell Dot SE, on which pretty much everything important worked out of the box (I dare say I'm going to have the usual fun with the microphone and card reader), and which is a nice shiny red colour, too! :P

---

### Post by AndrewX192 on 2010-11-09
I just turn my machine off every time when I'm done using it now.
I use full disk encryption so suspending poses a security risk.
Also, I ended up just leaving my screen brightness at the lowest setting, I don't really need to adjust it.
The machine is a lot faster when the CPU is allowed to do dynamic scaling.
So at least for me, I don't really have any issues anymore.

---

### Post by odysseus2k7 on 2010-11-10
> **fasgiu said:**
> Hi,
I have a toshiba nb305 with ubuntu 10.10 + kernel 2.6.37-rc1-maverick.

This kernel solved my problems: with 2.6.35 I had to move the mouse or press a key to work and brightness key didn't work; with 2.6.36 I had to move the mouse or press a key to work but brightness worked;

With 2.6.37-rc1 no problem running applications and video, fast boot, brightness key works, hibernation works; only suspend to ram doesn't work.

The only trick is to switch in compatibility mode in the bios. No boot parameters or "always low" cpu speed required.

Hope to be useful.
Giuseppe.

I just installed 2.6.37-rc1 and everything worked for a while, but now the disk isn't mounting at bootup and it won't hibernate.

---

### Post by amlamarra on 2010-11-19
I got myself an NB305 and decided to put Ubuntu 10.10 on it.  However, since I'm total Linux n00b, could anyone point me towards some instruction on how to install Kernel 2.6.37-rc1?

---

### Post by odysseus2k7 on 2010-11-23
> **amlamarra said:**
> I got myself an NB305 and decided to put Ubuntu 10.10 on it.  However, since I'm total Linux n00b, could anyone point me towards some instruction on how to install Kernel 2.6.37-rc1?

I'd stick with 2.6.36 until 2.6.37 has a stable release.  It's currently up to rc3 (natty) so expect four or five more before the final release, which will be 2.6.37.  Meanwhile, here's what you need to do:

1.  Visit the kernel-ppa site:
[http://kernel.ubuntu.com/~kernel-ppa/mainline/](http://kernel.ubuntu.com/~kernel-ppa/mainline/)

2.  Scroll through the list until you find the link to 2.6.36-maverick.  Click on that one.

3.  You will see a list of kernels and images.  Download and install them, using the Ubuntu Software Center, in this order:
v2.6.36-maverick/linux-headers-2.6.36-020636_2.6.36-020636.201010210905_all.deb (10Mb)
v2.6.36-maverick/linux-headers-2.6.36-020636-generic_2.6.36-020636.201010210905_i386.deb (750Kb)
v2.6.36-maverick/linux-image-2.6.36-020636-generic_2.6.36-020636.201010210905_i386.deb (32Mb)

I'd do it one at a time so you don't get lost in the process. The names are very similar so it may be confusing.

Once you're done with that, go into terminal and type "sudo update-grub".  Reboot and enjoy the benefits of the latest stable kernel.

-O2k7

I see now that the first natty kernel has been released, 2.6.36-1-natty.  Has anyone installed it yet?

---

### Post by odysseus2k7 on 2010-11-23
Just installed 2.6.36.1-natty.  Runs great, no need for kludgy grub edits.  Also, it's solved an pulse audio stuttering problem.

---

### Post by amlamarra on 2010-11-24
Great, thanks!  I'll have to try that as soon as my power cable arrives.  I'm currently deployed & the crappy transformers they have here blew my power adapter.  I ordered a new one but mail takes about a week to get here.  Should arrive today or tomorrow.
 
Does that kernel solve your resume from standby issue?  How about being able to adjust the screen brightness?

---

### Post by odysseus2k7 on 2010-11-24
> **amlamarra said:**
> Great, thanks!  I'll have to try that as soon as my power cable arrives.  I'm currently deployed & the crappy transformers they have here blew my power adapter.  I ordered a new one but mail takes about a week to get here.  Should arrive today or tomorrow.
 
Does that kernel solve your resume from standby issue?  How about being able to adjust the screen brightness?

The screen brightness adjustment works, hibernate works, suspend to RAM still doesn't, but I don't use that function.  It boots in about 35-40 seconds in Dynamic CPU mode.  Only thing that doesn't work is the webcam.

---

### Post by brodiewells on 2010-11-24
> **odysseus2k7 said:**
> The screen brightness adjustment works, hibernate works, suspend to RAM still doesn't, but I don't use that function.  It boots in about 35-40 seconds in Dynamic CPU mode.  Only thing that doesn't work is the webcam.

Did the webcam stop working because of that, or was it not working before?  My wife uses the webcam a lot and I will tell her not to upgrade if that is the case.

---

### Post by odysseus2k7 on 2010-11-24
> **brodiewells said:**
> Did the webcam stop working because of that, or was it not working before?  My wife uses the webcam a lot and I will tell her not to upgrade if that is the case.

It worked in 10.04; in 10.10 it's been unpredictable.  I haven't found the settings I need to get it working.  It's not much of an issue for me since I don't use it very often, but if your wife uses it I wouldn't do the upgrade yet.

---

### Post by brodiewells on 2010-11-24
> **odysseus2k7 said:**
> It worked in 10.04; in 10.10 it's been unpredictable.  I haven't found the settings I need to get it working.  It's not much of an issue for me since I don't use it very often, but if your wife uses it I wouldn't do the upgrade yet.

Thanks

---

### Post by odysseus2k7 on 2010-11-28
> **brodiewells said:**
> Did the webcam stop working because of that, or was it not working before?  My wife uses the webcam a lot and I will tell her not to upgrade if that is the case.

It turns out the webcam works; it's just the Cheese app that doesn't like it.  I downloaded Kamono and it seems to do the job.  Don't know how it handles videochats though.

---

### Post by amlamarra on 2010-12-06
Just got my power cable in the mail so I'm gonna try installing the maverick kernel. Can I follow the same procedure for the natty kernel if I want to install that later?
 
Also, will this fix the problem where my computer stops responding if I'm not moving the mouse or typing on the keyboard? I changed that one thing in the bios, that allowed me to install Ubuntu, but I still have problems using it.
 
EDIT: Apprently not. Also, I still have a problem returning from Standby mode. But at least I can adjust the brightness!
 
EDIT 2:  So yah, I installed the 2.6.36-maverick kernel AND changed SATA to Compatibility in the BIOS.  Still, the hard drive stops shortly after I stop typing or moving the mouse.  Also, the netbook doesn't recover from suspend mode.  I have a Toshiba NB305-N310.  Any help would be greatly appreciated!

---

### Post by amlamarra on 2010-12-08
So, can I try another Kernel?

---

### Post by odysseus2k7 on 2010-12-08
> **amlamarra said:**
> So, can I try another Kernel?

I've gotten good results from 2.6.36-1-natty.  I won't use any of the rc's though; every time I've installed them I've had problems.

---

### Post by JinzoBlaze on 2010-12-23
I have NB305-N442BL and I can't install 10.10 on this, with linux live USB creator i was able to get 10.04 without issue. Does anyone have 10.10 installed on their netbook yet? If so, what did you use?

The error message I received was "No default or UI configuration directive found!"

---

### Post by amlamarra on 2010-12-23
> **JinzoBlaze said:**
> I have NB305-N442BL and I can't install 10.10 on this, with linux live USB creator i was able to get 10.04 without issue. Does anyone have 10.10 installed on their netbook yet? If so, what did you use?

The error message I received was "No default or UI configuration directive found!"

I got it installed on my NB305-N310.  You have to go into the BIOS & change the SATA mode to Compatibility.  It's mentioned earlier in this thread.

---

### Post by jaronron10 on 2010-12-26
> **odysseus2k7 said:**
> I'd stick with 2.6.36 until 2.6.37 has a stable release.  It's currently up to rc3 (natty) so expect four or five more before the final release, which will be 2.6.37. 

Thank You all verry much. After getting a virus on windows (typical) and haveing no optical drive to reinstall it. I decided to give Linux another chance. I havent messed with it for almost 10 years. You all have made this verry easy.

Toshiba NB305-N442BL. Now running Ubuntu 10.10 with the 2.6.36 kernel.

---

### Post by amlamarra on 2010-12-26
Even after installing the 2.6.36 Kernel, I still couldn't get a bunch of stuff to work.  Ubuntu wouldn't come out of sleep mode and the most annoying part was that I had to keep moving the mouse or typing on the keyboard to get the hard drive to spin.

I switched back to Windows 7.  By the way, Microsoft Security Essentials is a great (and free) anti-virus.

---

### Post by brodiewells on 2010-12-27
> **amlamarra said:**
> I switched back to Windows 7.  By the way, Microsoft Security Essentials is a great (and free) anti-virus.

Nobody here cares.

---

### Post by amlamarra on 2010-12-27
> **brodiewells said:**
> Nobody here cares.

Nice... Way to represent the Linux community.

---

### Post by xilofono on 2011-01-04
Hello,
I just bought Toshiba NB305-10F. I can't install Ubuntu 10.10 from usb. The bootable usb works on another computer. I switched SATA controller mode to Compatibility, it was unsuccessful. All i get is a black screen printing

boot:
_

and a blinking underline for more than 5 minutes, no response to short press of power button. Am I missing something? What are the exact BIOS settings?

thanks

---

### Post by xilofono on 2011-01-05
> **xilofono said:**
> Hello,
I just bought Toshiba NB305-10F. I can't install Ubuntu 10.10 from usb. The bootable usb works on another computer. I switched SATA controller mode to Compatibility, it was unsuccessful. All i get is a black screen printing

boot:
_

and a blinking underline for more than 5 minutes, no response to short press of power button. Am I missing something? What are the exact BIOS settings?

thanks

Ok, I solved my issue. I changed no parameters in the BIOS, it was a matter of the bootloader on the usb.
- I made the usb bootable according to ubuntu's main page.
- On my ubuntu desktop computer, I changed a file in the usb
```
cp /usr/lib/syslinux/menu.c32 /media/MY_USB_DRIVE/syslinux/vesamenu.c32
```It seems to change the graphical boot menu into a simpler text menu. On my netbook apeared this menu and I could boot ubuntu in live mode and install normally.

Bye

---

### Post by brodiewells on 2011-01-05
> **xilofono said:**
> Ok, I solved my issue. I changed no parameters in the BIOS, it was a matter of the bootloader on the usb.
- I made the usb bootable according to ubuntu's main page.
- On my ubuntu desktop computer, I changed a file in the usb
```
cp /usr/lib/syslinux/menu.c32 /media/MY_USB_DRIVE/syslinux/vesamenu.c32
```It seems to change the graphical boot menu into a simpler text menu. On my netbook apeared this menu and I could boot ubuntu in live mode and install normally.

Bye

Thats good to know, Thanks!

---

### Post by cdubea on 2011-01-08
Just got a NB305-N442BL and want to install Ubuntu Netbook Remix.  Downloading and following the instructions from this page:

[http://www.ubuntu.com/netbook/get-ubuntu/download](http://www.ubuntu.com/netbook/get-ubuntu/download)

Attempting to boot up gives the following response:

graphics initialization failed
Error setting up gfxboot
boot:

Then it just recycles over and over.  I've plugged the USB stick in my Dell M6400 and it boots up just fine.  Is there a particular BIOS setting I should be using to get past this?

Thanks

chris

---

### Post by cdubea on 2011-01-08
> **cdubea said:**
> Just got a NB305-N442BL and want to install Ubuntu Netbook Remix.  Downloading and following the instructions from this page:

[http://www.ubuntu.com/netbook/get-ubuntu/download](http://www.ubuntu.com/netbook/get-ubuntu/download)

Attempting to boot up gives the following response:

graphics initialization failed
Error setting up gfxboot
boot:

Then it just recycles over and over.  I've plugged the USB stick in my Dell M6400 and it boots up just fine.  Is there a particular BIOS setting I should be using to get past this?

Thanks

chris

Tried the solution in the message above this one.  It made no difference.

Can anyone provide assistance?

Thanks

chris

---

### Post by vicmaxabc on 2011-01-12
> **cdubea said:**
> Tried the solution in the message above this one.  It made no difference.

Can anyone provide assistance?

Thanks

chris

I don't remember exactly..but just type 'help' and then at hit ESC or ENTER (I don't remember exactly).. Don't laugh ... I'm dead serious.

---

### Post by brodiewells on 2011-01-13
> **vicmaxabc said:**
> I don't remember exactly..but just type 'help' and then at hit ESC or ENTER (I don't remember exactly).. Don't laugh ... I'm dead serious.

Oh yeah, I remember now that I had to do that too.  I am laughing but not at you.  It's funny because it's true.

---

### Post by cdubea on 2011-01-14
> **vicmaxabc said:**
> I don't remember exactly..but just type 'help' and then at hit ESC or ENTER (I don't remember exactly).. Don't laugh ... I'm dead serious.

Type help where exactly?  Repeating, when I try to boot off of a USB stick I get a black screen with:

graphics initialization failed
Error setting up gfxboot
boot:

which repeats endlessly.

thanks

chris

---

### Post by cdubea on 2011-01-14
> **vicmaxabc said:**
> I don't remember exactly..but just type 'help' and then at hit ESC or ENTER (I don't remember exactly).. Don't laugh ... I'm dead serious.

Type help where exactly?  Repeating, when I try to boot off of a USB stick I get a black screen with:

graphics initialization failed
Error setting up gfxboot
boot:

which repeats endlessly.

thanks

chris

---

### Post by brodiewells on 2011-01-14
Here is where i found it.
[http://ubuntu-virginia.ubuntuforums.org/showthread.php?t=1594003](http://ubuntu-virginia.ubuntuforums.org/showthread.php?t=1594003)
I can't remember if you have to hit enter first to get it to stop or enter after you type it, but those directions were sufficient to help me figure it out.

---

### Post by cdubea on 2011-01-15
?

Amazing.  Booted right up....

Thanks!

chris

---

### Post by cdubea on 2011-01-15
?

Amazing.  Booted right up....

Thanks!

chris

---

### Post by Galvatronic on 2011-02-01
I keep getting the "gives up looking for bootable device" on my NB305-N310. I changed the root delay to 20, 35, and eventually 90 but that didn't work, and I don't know if i should edit root=

---

### Post by fasgiu on 2011-02-03
> **odysseus2k7 said:**
> Just installed 2.6.36.1-natty.  Runs great, no need for kludgy grub edits.  Also, it's solved an pulse audio stuttering problem.

How did you install a natty kernel on maverick? I want to tray it on my nb305
Thanks..

---

### Post by vfrank on 2011-02-05
Anyone have success reducing power consumption on the NB305? Many of the options indicated in powertop cannot be activated. Running Maverick w/ kernel 2.6.35-25-generic.

Thanks!

Vic

---

### Post by BBUCommander on 2011-02-19
I would not suggest installing the Natty kernel on Maverick.  However, I installed Natty Narwhal (11.04) Alpha 2 and am happy to report that everything is peachy on my NB305!  Make sure that at the login screen you choose "Ubuntu Classic desktop (no effects)" from the session menu at the bottom of the screen.  

While the new Ubuntu session does work in Natty Alpha 2, it is very buggy and slow.  You may also want to consider Xubuntu, which is much faster and less resource intensive on netbooks.  Right now I have both gnome (Ubuntu) and xfce (via the xubuntu-desktop package) installed on my Natty just in case Gnome starts giving me trouble in a  future update.

BTW, I got Xubuntu running on an ancient Pentium 233 MHz with 256 MB of RAM and a 5 GB hard drive. =)  I did not even have to tone down the visuals.  Quite impressive.

---

### Post by lost2 on 2011-03-10
Running Mint9 w/Fluxbox on a NB305 and found that screen bright can be managed by this simple script:

val=$(echo "obase=16; ($1*255/100)" | bc)
sudo setpci -s 00:02.0 F4.B=$val
exit

All you have to do is save it as ... "bright", make it executable by "chmod +x bright" and run it as:

bright 50      ---> to get 50% screen bright or
bright 100     ---> to get 100% screen bright

Hope that helps.
Cheers

---

### Post by thePowersGang on 2011-03-10
I've run into similar issues with suspend on my 2009 model NB300 (Atom N450, 2GiB RAM)

It goes into suspend aparently correctly, but does not resume. There is a pulse of harddisk activitiy for about 1/2 s when it resumes, but the screen does not turn back on (the fan spins up however, and seems to run at a high speed for a while, which would indicate to me a busy lock somewhere)

I have tried the suggestions on [https://wiki.ubuntu.com/DebuggingKernelSuspend](https://wiki.ubuntu.com/DebuggingKernelSuspend) (enabling pm_trace and then suspending, but it does not seem to alter the RTC (the clock maintains time, and no hash is found)

I will try to wait out the resume now, and edit this post (or repost) with the results, but I suspect it will not work.
Edit: Waited 30 mins for the machine to resume, no change, the fan sped up for about a min, but for the rest, it just sat there.

Hardware Details (lspci, cpuinfo):
Ubuntu 10.10
```

$ uname -a
Linux sonata 2.6.35-27-generic #48-Ubuntu SMP Tue Feb 22 20:25:46 UTC 2011 x86_64 GNU/Linux

$ lspci
00:00.0 Host bridge: Intel Corporation N10 Family DMI Bridge
00:02.0 VGA compatible controller: Intel Corporation N10 Family Integrated Graphics Controller
00:02.1 Display controller: Intel Corporation N10 Family Integrated Graphics Controller
00:1b.0 Audio device: Intel Corporation N10/ICH 7 Family High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 2 (rev 02)
00:1c.2 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 3 (rev 02)
00:1d.0 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation N10/ICH 7 Family USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation NM10 Family LPC Controller (rev 02)
00:1f.2 IDE interface: Intel Corporation N10/ICH7 Family SATA IDE Controller (rev 02)
00:1f.3 SMBus: Intel Corporation N10/ICH 7 Family SMBus Controller (rev 02)
07:00.0 Network controller: Atheros Communications Inc. AR9285 Wireless Network Adapter (PCI-Express) (rev 01)
09:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 02)

$ cat /proc/cpuinfo 
processor	: 0
vendor_id	: GenuineIntel
cpu family	: 6
model		: 28
model name	: Intel(R) Atom(TM) CPU N450   @ 1.66GHz
stepping	: 10
cpu MHz		: 1000.000
cache size	: 512 KB
physical id	: 0
siblings	: 2
core id		: 0
cpu cores	: 1
apicid		: 0
initial apicid	: 0
fpu		: yes
fpu_exception	: yes
cpuid level	: 10
wp		: yes
flags		: fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx lm constant_tsc arch_perfmon pebs bts rep_good aperfmperf pni dtes64 monitor ds_cpl est tm2 ssse3 cx16 xtpr pdcm movbe lahf_lm dts
bogomips	: 3324.99
clflush size	: 64
cache_alignment	: 64
address sizes	: 32 bits physical, 48 bits virtual
power management:

processor	: 1
vendor_id	: GenuineIntel
cpu family	: 6
model		: 28
model name	: Intel(R) Atom(TM) CPU N450   @ 1.66GHz
stepping	: 10
cpu MHz		: 1000.000
cache size	: 512 KB
physical id	: 0
siblings	: 2
core id		: 0
cpu cores	: 1
apicid		: 1
initial apicid	: 1
fpu		: yes
fpu_exception	: yes
cpuid level	: 10
wp		: yes
flags		: fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx lm constant_tsc arch_perfmon pebs bts rep_good aperfmperf pni dtes64 monitor ds_cpl est tm2 ssse3 cx16 xtpr pdcm movbe lahf_lm dts
bogomips	: 3325.03
clflush size	: 64
cache_alignment	: 64
address sizes	: 32 bits physical, 48 bits virtual
power management:

```

---

### Post by chadliness on 2011-04-04
I've been using natty beta 1 for about a week now and suspend works fine out of the box.  The brightness keys also work.  Hibernate is not quite working: the machine boots back up but the display is hopelessly corrupted and I had to type keyboard commands from memory to reboot.

I like the new interface a lot.  It's very quick and well thought-out.  In terms of usability it's by far the best netbook interface I've used.

---

### Post by thePowersGang on 2011-04-06
Yes, I have recently moved to kernel 2.6.38.2 (custom compile) and suspend and brightness work again. But I see the same issue as you do with hibernate. (Just a blinking VGA cursor, VT changing doesn't work.)

---

### Post by mcknight0219 on 2011-04-19
I recently bought a NB305-N600 and installed Ubuntu instantly (of course). Everything is fine
except that the fan is constantly on which is kinda noisy. 

Any suggestion for this ?

---

### Post by brodiewells on 2011-04-19
> **mcknight0219 said:**
> I recently bought a NB305-N600 and installed Ubuntu instantly (of course). Everything is fine
except that the fan is constantly on which is kinda noisy. 

Any suggestion for this ?

While mine has many problems, it does not have that problem.

---

### Post by mcknight0219 on 2011-04-20
> **brodiewells said:**
> While mine has many problems, it does not have that problem.

 That's weird, I have none but this problem ! Everything else works fine, sleep, wifi, keyboard shortcut, etc. When booted up, soon the heat roars and fan kicks in and never stop ! When I checked system monitor, no suspicious process spin out of control.

---

### Post by BSD_dad on 2011-04-20
If the bottom is warm/hot the fan should be on, if cool not. Mine will kick on once warmed up and then usually stays warm and on.

---

### Post by mcknight0219 on 2011-04-20
> **BSD_dad said:**
> If the bottom is warm/hot the fan should be on, if cool not. Mine will kick on once warmed up and then usually stays warm and on.

 The problem is once it's on, it never cools down even when I'm literately doing nothing. Does your machine behave like this ?

---

### Post by BSD_dad on 2011-04-22
Yes. If it's on long enough the heat builds up past the passive cooling point apparently so the fan has to stay on.

---

### Post by Gargintua on 2011-04-29
Just installed ubuntu 11.04 NATTY NARWHAL on my nb300


[LIST]

[*]when you unplug the power cord no matter how much power you have left it says "critical battery shutting down"
[*]No suspend
[/LIST]

on the other hand


[LIST]
[*]wireless is a bit slower but no real need for backports
[*]no need for "quiet *splash nohz*=off highres=off"
[/LIST]

---

### Post by brodiewells on 2011-04-30
> **Gargintua said:**
> Just installed ubuntu 11.04 NATTY NARWHAL on my nb300


[LIST]

[*]when you unplug the power cord no matter how much power you have left it says "critical battery shutting down"
[*]No suspend
[/LIST]

Mine was doing those things before the upgrade.

---

### Post by fasgiu on 2011-05-01
upgraded from 10-10 to 11.04 and:

bluethoot doesn't work.. it seems that there is a problem on loading omni_book module

hibernation with uswsusp doesn't work anymore.
Normal hibernation doesn't wark too.

suspend to ram doesn't work (never worked)

Can somebody confirm issues with a fresh install of 11.04?

thanks,
Giuseppe

---

### Post by 4manifold on 2011-05-01
I just upgraded from 10.10.  I am still using the boot parameters   
```
splash nohz=off  highres=off
```
in grub.

Suspend to ram and hibernate both work.  These parameters seem to no longer break pulseaudio, which is nice.  I tried disabling these parameters, and the computer didn't wake from suspend to ram, but it did wake from hibernate.  

If you look at [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/508516](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/508516), it seems that the devs are not going to fix this, as it is mainly a problem in the BIOS.  Hopefully Toshiba will fix it sometime.

---

### Post by BSD_dad on 2011-05-01
Has anyone updated the bios?
sudo dmidecode | less
shows me at v1.20
[toshiba site]("http://www.csd.toshiba.com/cgi-bin/tais/support/jsp/modelContent.jsp?ct=DL&os=&category=&moid=2523340&rpn=PLL3AU&modelFilter=&selCategory=2756709&selFamily=2336267") indicates latest is 1.70
I have a model NB305-N410BN

Steve

---

### Post by BSD_dad on 2011-05-02
Updated to 11.04 and resume from hibernate is wacked. Some have [reported]("http://ubuntuforums.org/showthread.php?p=10758295") no screen but random colors at top. I have right hand 20% of screen (full vertical) and left side is random pixels in top 25%. Seems default grub for 11.04 uses  GRUB_CMDLINE_LINUX_DEFAULT="splash nohz=off highres=off"
anyway. I'm on NB305-N401BN, bios v 1.20.

Any clues on how to fix hibernate?

---

### Post by fasgiu on 2011-05-05
ok an update of my situation:

I added the boot options GRUB_CMDLINE_LINUX_DEFAULT="splash nohz=off highres=off" (which are not default) and got suspension to work.

I updated with natty proposed and solved the bluethooth problem which was a bug affecting many laptops.

Hibernation didn't work at all so I installed uswsusp ad got resume from hibernation with only right 20% of screen visible. I managed to coexist with this problem by:
- blind login after hibernation by typing my password ad hitting enter.
- now I can see a little portion of my desktop.
- suspend to ram by fn key.
- resume from suspend and can see the full desktop

This is not a great solution but allows me to hibernate when really needed (i.e. when on very low battery).

Bye.
Giuseppe.

EDIT: I have 1.70 bios

---

### Post by rpremuz on 2011-05-10
On [https://bugs.launchpad.net/linux/+bug/657990](https://bugs.launchpad.net/linux/+bug/657990) you can find some other kernel options that can be used as a workaround for the issue of booting Linux on Toshiba netbooks with Intel Atom processors.

I got good results on a Toshiba nb300. In BIOS ver. 1.70 I used:
Dynamic CPU Frequency Mode: Dynamic
SATA Controller Mode: AHCI

In **Ubuntu 11.04 with Linux 2.6.38-9.43** I set the following kernel command line:
```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash nolapic_timer clocksource=jiffies"
```
in /etc/default/grub and then run
```
sudo update-grub
sudo reboot
```

There are no problems with playing multimedia.
The following hot keys work fine:
FN + ESC turns the volume on and off
FN + F3 switches the system to Sleep mode (suspend); resumes fine
FN + F5 changes the active display device (LCD or external display)
FN + F6/F7 decreases/increases the display brightness
FN + F10 turns on/off cursor control keys (with grey markings on the keyboard)
FN + F11 turns on/off numeric keypad keys (with grey markings on the keyboard)
FN + 3/4 decreases/increases the output sound volume

The hibernation mode can't be entered by pressing FN + F4 but it can be done through panel or by pressing Ctrl+Alt+Del and choosing "Hibernate". The resume from the hibernation mode also works fine.

Web camera works fine in cheese and Skype (not tested in other apps).

-- rpr.

---

### Post by 4manifold on 2011-05-16
[]("http://ubuntuforums.org/member.php?u=452415")__How did you update the BIOS?

---

### Post by 4manifold on 2011-05-18
> **4manifold said:**
> How did you update the BIOS?

Figured it out!  You can update the BIOS as follows:

[LIST=1]
[*]Download the new BIOS (a self-extracting zip file) from the Toshiba website.
[*]Extract it using the archive manager.  There is an iso file included.
[*]Use UNetBootin to create a bootable USB stick from the iso file.
[*]Turn off your computer, insert USB stick, turn on your computer.
[*]Hold down the "u" key to get it to boot from USB.
[*]The updater should start automatically.
[/LIST]
There was a choice at one point between "linux" and "local", I think: I chose linux, and that worked.

---

### Post by cantwait on 2011-05-18
4manifold, where did you download the new BIOS from? I've searched the Toshiba site but the only BIOS update I'm able to find is a Windows Installation, rather than any self-extracting zip (I downloaded it anyway and tried to unzip it to no avail - it tells me it's not a self-extracting zip). 

Might you be able to post the link where you downloaded the file?  :)

---

### Post by fasgiu on 2011-05-20
Is
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash nolapic_timer clocksource=jiffies"

better than

GRUB_CMDLINE_LINUX_DEFAULT="splash nohz=off highres=off"
??

If yes, why? thanks.
Giuseppe.

---

### Post by 4manifold on 2011-05-22
> **cantwait said:**
> 4manifold, where did you download the new BIOS from? I've searched the Toshiba site but the only BIOS update I'm able to find is a Windows Installation, rather than any self-extracting zip (I downloaded it anyway and tried to unzip it to no avail - it tells me it's not a self-extracting zip). 

Might you be able to post the link where you downloaded the file?  :)
I can't get the website to give me the link to the actual download page.  But you can just go here:
[http://www.csd.toshiba.com/cgi-bin/tais/support/jsp/modelContent.jsp?ct=SB&os=&category=&moid=2523340&rpn=PLL3AU&modelFilter=&selCategory=2756709&selFamily=2336267](http://www.csd.toshiba.com/cgi-bin/tais/support/jsp/modelContent.jsp?ct=SB&os=&category=&moid=2523340&rpn=PLL3AU&modelFilter=&selCategory=2756709&selFamily=2336267)
and then click on the "Downloads" tab, then choose "BIOS" in the "Refine search by" dropdown menu.

I adapted my instructions above from the readme file that was included with the download.

---

### Post by cantwait on 2011-05-26
Thank you 4manifold that worked perfectly! :)

---

### Post by rmwatson on 2011-06-16
Hi, I just signed up to thank-you all for the information provided in the forum. I have been able to get 10.04 working perfectly on my NB305. So thank-you very much!

Matthew

---

### Post by BSD_dad on 2011-07-13
Just ran updates. Kernel now:
2.6.38-10-generic #46-Ubuntu SMP Tue Jun 28 15:05:41 UTC 2011 i686 i686 i386 GNU/Linux

Hibernate seems to be working now.

edit: btw, 11.04

---

### Post by 4manifold on 2011-10-17
Anybody installed 11.10 yet?  Any comments, bugs, etc?

---

### Post by fasgiu on 2011-10-18
updated 11.04 to 11.10 and  works very well.
I also noticed that works pinch to zoom feature.

I don't like Mozilla thunderbird and Evolution has problems with the calendar but this is not due to my hardware.

---

### Post by Wollongong on 2011-12-05
I found the same slow boot problem with Ubuntu 10.10, 11.04 and 11.10:
 5 minutes to boot, instead of 45 seconds.

The problem disappears if the BIOS setting SATA AHCI is changed to Compatibility.

The problem with that is that Windows will not boot on 'Compatibility' setting, so if you want dual boot, you would have to change the BIOS setting each time.

This problem seems to be specific to Ubuntu.
It works fine with Kubuntu 11.10 when BIOS is set to AHCI - 45 seconds to boot!

---

### Post by bimasakti85 on 2011-12-22
> **Wollongong said:**
> I found the same slow boot problem with Ubuntu 10.10, 11.04 and 11.10:
 5 minutes to boot, instead of 45 seconds.

The problem disappears if the BIOS setting SATA AHCI is changed to Compatibility.

The problem with that is that Windows will not boot on 'Compatibility' setting, so if you want dual boot, you would have to change the BIOS setting each time.

This problem seems to be specific to Ubuntu.
It works fine with Kubuntu 11.10 when BIOS is set to AHCI - 45 seconds to boot!

Just do this instead changing the bios setting :
Edit "/etc/default/grub" and find this line :
GRUB_CMDLINE_LINUX="" changed to GRUB_CMDLINE_LINUX=acpi_skip_timer_override

then run update-grub .

After that, no need to change the AHCI setting become compatibity mode.

---

### Post by brodiewells on 2011-12-22
@bimasakti85 Thanks! That worked perfectly.

---

### Post by bimasakti85 on 2011-12-23
Is anyone having an issue with suspend mode in oneiric ? I've try the "nohz=off highres=off" mode, but still cant suspend (wont wake up). Is there any solution for this ?

---

### Post by maximilianh on 2012-01-03
With Oneiric, still no suspend, same issue as before. I suspect that there is no fix for this yet, as it is a BIOS problem.

I used this workaround for the slow wireless speed problem:
[http://linuxblog.avserver.info:8000/?p=327](http://linuxblog.avserver.info:8000/?p=327)

Here might be another workarond for the resume problem:
[http://us.generation-nt.com/answer/performance-resume-issues-toshiba-nb305-help-202304262.html](http://us.generation-nt.com/answer/performance-resume-issues-toshiba-nb305-help-202304262.html)

I'll keep investigating this...

---

### Post by tuxpromoter on 2012-01-17
Regarding problems with Suspend.

I've found a bios setting in my nb305-n410 that may apply to other Toshiba netbooks or similar.

I've found this works for any kernel version I've tried so far on 10.04 LTS.

It's my opinion that this is a bios issue because suspend works perfect for me so long as I choose "always low" under "Dynamic CPU frequency mode" in bios. When "dynamic" is chosen the netbook is faster overall, but suspend doesn't work properly. 

Assumptions: LTS 10.04 and Toshiba System Bios 1.70 is what I have, other versions may or may not work.



To test:

Remove the "nohz= off highres=off" appends if any from grub.conf.

Reboot , choose F2 to go into the bios. 

Navigate to the "Advanced" tab in bios.

Change the option under "Dynamic CPU Frequency Mode": from "Dynamic" to "Always Low"

Save and reboot and test your kernel versions and suspend options.


Notes. I keep my NB305 in "Always Low" anytime I'm mobile so that I can suspend ad resume fast. 
If I need more cpu power for some applications(mythtv for example) I reboot and change it to "Dynamic" and then I always choose "shutdown" when the bios option "Dynamic" is enabled. 
Since it's a low powered netbook I rarely change it to "Dynamic" anymore.
My only current exception is that when the bios option "Always Low" is choosen, mythfrontend can't keep up with HDTV frames and pauses/stutters. When in "Dynamic" mythfrontend works perfect for me with HDTV recordings or livetv.

---

### Post by tuxpromoter on 2012-01-19
edit/update

I forgot to add that you should run:

```
#/usr/bin/update-grub 
```

after changing /etc/default/grub

---

### Post by idelosestados on 2012-03-18
> **4manifold said:**
> I can't get the website to give me the link to the actual download page.  But you can just go here:
[http://www.csd.toshiba.com/cgi-bin/tais/support/jsp/modelContent.jsp?ct=SB&os=&category=&moid=2523340&rpn=PLL3AU&modelFilter=&selCategory=2756709&selFamily=2336267](http://www.csd.toshiba.com/cgi-bin/tais/support/jsp/modelContent.jsp?ct=SB&os=&category=&moid=2523340&rpn=PLL3AU&modelFilter=&selCategory=2756709&selFamily=2336267)
and then click on the "Downloads" tab, then choose "BIOS" in the "Refine search by" dropdown menu.

I adapted my instructions above from the readme file that was included with the download.

Is the file still there or am I missing something...?

---

### Post by 4manifold on 2012-03-19
I just checked and it seemed like it was still there... if not, repost with an email address and I'll send you the file.

---

### Post by idelosestados on 2012-03-21
> **4manifold said:**
> I just checked and it seemed like it was still there... if not, repost with an email address and I'll send you the file.

So it was the .exe file that was supposed to be extracted. Now I feel sort of stupid. :D Anyway, problem solved, BIOS updated. 

I won't keep my hopes too high though that this would fix my issue of crashing within some time with the dynamic CPU setting.

---

### Post by idelosestados on 2012-04-06
> **rpremuz said:**
> On [https://bugs.launchpad.net/linux/+bug/657990](https://bugs.launchpad.net/linux/+bug/657990) you can find some other kernel options that can be used as a workaround for the issue of booting Linux on Toshiba netbooks with Intel Atom processors.

I got good results on a Toshiba nb300. In BIOS ver. 1.70 I used:
Dynamic CPU Frequency Mode: Dynamic
SATA Controller Mode: AHCI

In **Ubuntu 11.04 with Linux 2.6.38-9.43** I set the following kernel command line:
```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash nolapic_timer clocksource=jiffies"
```
in /etc/default/grub and then run
```
sudo update-grub
sudo reboot
```

There are no problems with playing multimedia.
The following hot keys work fine:
FN + ESC turns the volume on and off
FN + F3 switches the system to Sleep mode (suspend); resumes fine
FN + F5 changes the active display device (LCD or external display)
FN + F6/F7 decreases/increases the display brightness
FN + F10 turns on/off cursor control keys (with grey markings on the keyboard)
FN + F11 turns on/off numeric keypad keys (with grey markings on the keyboard)
FN + 3/4 decreases/increases the output sound volume

The hibernation mode can't be entered by pressing FN + F4 but it can be done through panel or by pressing Ctrl+Alt+Del and choosing "Hibernate". The resume from the hibernation mode also works fine.

Web camera works fine in cheese and Skype (not tested in other apps).

-- rpr.

Just wanted to confirm that this works in my setup (Nb305-n310, Lubuntu 11.10). Suspend works and dynamic mode doesn't seem to crash anymore. Kudos to you rpremuz!

---

### Post by fredfsh on 2012-05-13
> **cdubea said:**
> Type help where exactly?  Repeating, when I try to boot off of a USB stick I get a black screen with:

graphics initialization failed
Error setting up gfxboot
boot:

which repeats endlessly.

thanks

chris

Hi Chris,

I'm experiencing the same problem as you. "boot:" repeats endlessly and there is no way for me stop it. (Neither hitting "Enter" or "ESC" works) Do you still remember how you solved it?
Thanks.

---

### Post by markean0703 on 2013-04-29
[COLOR=#000000]*1) *[/COLOR][B]sudo gedit /etc/default/grub
2) Change: GRUB_CMDLINE_LINUX_DEFAULT="splash nohz=off highres=off"
3) [B]sudo update-grub
4) [B]sudo reboot now
5) after reboot, close the lid, wait for orange slow-blinking light
6) open lid, press power button once, enter password, click on unlock
7) It works :smile:


this will work..like magic it also repair my media playing:)[/B][/B][/B]

---

### Post by Bucky Ball on 2013-04-29
[B][I]Thread Closed

Reason:[/I][/B] Necromancy. Old thread put to bed. 

If a thread hasn't seen any action for a year then post a new one rather than resurrecting it. Thanks. (10.04 LTS reaches end of life about now and 11.04 died awhile ago so all a bit redundant considering we are at 13.04 and the current LTS is 12.04.)

---

