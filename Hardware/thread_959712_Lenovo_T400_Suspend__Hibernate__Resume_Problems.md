---
title: "Lenovo T400 Suspend / Hibernate / Resume Problems"
date: 2008-10-26
forum: Hardware
---

### Post by fongandrew on 2008-10-26
Was having trouble finding a thread discussing suspend / hibernate issues unique to my laptop configuration, so here goes. I've installed the 8.10 x64 RC on a Lenovo T400 with Intel X4500 integrated graphics and 4GB ram.

During the actual suspension / hibernation process (either from GNOME or by entering pm-suspend / pm-hibernate in a console), the screen flickers 3-10 times before the system goes to sleep. Sometimes, it flashes some text on the screen really quickly. It's too fast to see exactly what it said, but it looked something like this:

btusb_intr_complete failed to resubmit
btusb_send_frame submission failed

When I try to resume, things fail ~3/4 of the time. The desktop will come up but it will appear to be only half-drawn (e.g. window frames with buttons and content missing). Everything stays frozen for a few seconds, and then the system reboots.

Thoughts? Is there some log or config file that I should look at?

UPDATE: If I suspend or hibernate after I've dropped down to a console, then resume works fine. So it looks like it's a GNOME / X / Intel driver problem.

---

### Post by Lord Xeb on 2008-10-26
I used Ubuntu tweak to fix the suspend problem (but hibernate is still an issure, but I never do anyway)  but I am not sure if it will work on a T400.


[http://ubuntu-tweak.com/downloads](http://ubuntu-tweak.com/downloads)

---

### Post by fongandrew on 2008-10-27
Bump.

---

### Post by stefanadelbert on 2008-10-27
I'm also having erratic problems with suspend / hibernate / resume on my HP Pavilion dv6836tx. I would be very interested to hear opinions or recommendations on getting this working or at least advice on fault-finding the problem(s).

Haven't tried suspend /hibernate from the console. I'll give that a try.

---

### Post by fongandrew on 2008-10-27
Ubuntu-tweak doesn't do it for me =P. It just offers to turn hibernation / suspend on and off. I already have them on -- it's just that they're not working. It probably has something to do with the drivers for the Intel X4500.

---

### Post by rryan on 2008-10-29
Hi fongandrew, 

I have a T400 and on 8.10 RC, I have the same problems as you. When I come back from suspend, I see the mouse and sometimes a window that is half drawn, and then the system reboots. 

I haven't been able to fix it yet. I'll post here if I do.

(Hibernate also does not work for me).

---

### Post by bennywhere on 2008-10-31
Same here... Lenovo T400, Ubuntu 8.10.  It used to work fine with 8.04, although it took freaking forever to resume from suspend (easily 20s).
Now with 8.10 it resumes lightning fast, but 90% of the time it just sits there for 10 seconds with mouse pointer not reacting and the login window half drawn, then it reboots.
I noticed that it never resumes when the lid was closed, but sometimes it resumes just fine when the lid was not closed...
I'll be investigating and let you guys know.  My first suspicion was iwlagn, but that's not it.

Update: It IS indeed a gnome issue, as it works in kde.

---

### Post by alkamid on 2008-11-01
Hello,

I experience the same problem. It's not annoying for me as it is just a message (it suspends all right and wakes up smoothly as well), I just don't like errors in my Ubuntu (: Also, it started appearing after upgrade to 8.10 Intrepid Ibex. I have no idea what can cause this.

---

### Post by fstonedahl on 2008-11-03
Same situation, same problem.  T400 with Ubuntu 8.10.  From either hibernation or suspend, it comes back to a black screen with frozen white mouse cursor, sits for a while, then reboots.  :-(   (This is with no compiz-fusion stuff.  It seemed like I got some weird video artifacts instead, when I had a bunch of compiz effects enabled.)  I'm running with the integrated graphics, haven't tried with the discrete graphics, and haven't tried KDE (which sounds like it worked for someone else).

Just thought I'd offer one more data-point for the problem.  If there's anything I can do to help test a fix, etc, just let me know.

---

### Post by jango4 on 2008-11-03
Hi!
Same Problem with T400 and ubuntu 8.10 using Internal Graphic Intel 4500!
On wake up system freeze with black display and mouse pointer, after few seconds system reboots.

Got two error messages every time:

btusb_intr_complete: hci0 urb f4f02c00 failed to resubmit (19)
btusb_send_frame: hci0 urb f7efd800 submission failed

Sometimes there are more messages when trying to hibernate.
Switching in textmode and typing pm-suspend (or pm-hibernate) works without any problems.
Must be an gnome/X/Intel Driver error.

So i started the same system with Discrete Graphics, ATI 3470 with radeon driver.... and
Suspend and Hibernate, both work very well without errors!

It seems, that Intel Driver has a problem with gnome... if it works under KDE (as posted above) and also with radeon Driver!

Anybody opened an Launchpad Bug yet?

lg Jango

---

### Post by mulatu on 2008-11-04
I can confirm the above entries. Lenovo T400 under Ubuntu 8.10 Intrepid hibernates, but doesn't wake up under Gnome. Waking up to a console works.

---

### Post by petri0 on 2008-11-04
Hi!

This problem affects not just the Lenovo T400 but also for example the new Dell Latitude E4200, HP EliteBook 2530p, Sony Vaio VGN-TT1, Toshiba R600, or anything else with the "Mobile Intel® GM45 Express Chipset" or X4500. I have exactly the same symptoms on my E4200 running intrepid.

The bug most certainly resides in the xserver-xorg-video-intel code. The fact that is manifests itself only with gnome desktop and not with KDE or text mode gives some clue. It is not compiz related as disabling compiz has no effect. I would say that this is a classical multiprocessor concurrency control problem! Disabling all but one core makes the bug disappear.

Here is my suggestion for a workaround. Save in /etc/pm/sleep.d/00CPU with 755 permissions. Note that it has to be called 00CPU so that it gets executed before and after anything else.

```
#!/bin/sh
# Workaround for concurrency bug in xserver-xorg-video-intel 2:2.4.1-1ubuntu10.
# Save this as /etc/pm/sleep.d/00CPU

. "${PM_FUNCTIONS}"

case "$1" in
	hibernate|suspend)
		for i in /sys/devices/system/cpu/cpu*/online ; do
			echo 0 >$i
		done
		;;
	thaw|resume) 
		sleep 10	# run with one core for 10 secs
		for i in /sys/devices/system/cpu/cpu*/online ; do
			echo 1 >$i
		done
		;;
	*)
		;;
esac
```

Please report if this works for you! The sleep period can easily be made longer if necessary.

Petri K

---

### Post by jango4 on 2008-11-04
Hi!

Thank you for your workaround script.... tested it as you told, but unfortunately it does not work for me. Same problem, screen freezes!
Should i change sleeping period?

jango

---

### Post by jango4 on 2008-11-04
Changed sleeping period to 20 seconds, but without any effect.
I want Suspend working without troubles!

---

### Post by petri0 on 2008-11-04
You could try that. I tried first with 5 seconds but that wasn't enough.
Or just as a test you could forget the script and try running with just one core temporarily. Of course it's possible that the T400 problem is something else, this works for Dell E4200.

Petri K

---

### Post by jango4 on 2008-11-04
-

---

### Post by jango4 on 2008-11-04
You really got it! It works perfectly with only one CPU enabled in BIOS settings.

but why is your script not working for me?
typed: sudo gedit
pasted your code, saved in /etc/pm/sleep.d/00CPU
typed sudo chown 755 /etc/pm/sleep.d/00CPU
should work, or?

jango

---

### Post by jango4 on 2008-11-05
I am such a noob... chmod... not chown!
It works perfekt!
Thanks a lot for your help!

lg Jango

---

### Post by eeejay on 2008-11-05
I got resume/suspend working by simply disabling Bluetooth in BIOS...

---

### Post by afty on 2008-11-05
> **eeejay said:**
> I got resume/suspend working by simply disabling Bluetooth in BIOS...
My T400 doesn't have Bluetooth, but I do have the suspend problem.  It goes into suspend fine, but when you try to bring it out, the machine sits there for a minute and then reboots.

I found this suggestion over at [Notebook Review](http://forum.notebookreview.com/showthread.php?p=4109302#post4109302):
> 
Good news, i think i've just solved suspend/hibernation problem.

I cant paste url here, but on lkml Jassie Barnes wrote about similar issue:

"On many machines, we've found that re-POSTing the video device is incompatible with the i915 driver's suspend/resume functionality. So things like s3_bios and vbetool shouldn't be used if the i915 driver works by itself."

After deleting vbetool i have absolutely no problems with suspend and hibernation .

I haven't tried it yet, but maybe someone here could try and report back?

---

### Post by jan. on 2008-11-05
> **eeejay said:**
> I got resume/suspend working by simply disabling Bluetooth in BIOS...
Can you confirm this through several suspend- or hibernate-resume cycles?

---

### Post by homerhomer on 2008-11-05
You might have the same bug that I have.

If you have a single running the 64bit version and it reboots when you resume
you might want to follow this bug
[https://bugs.launchpad.net/ubuntu/+source/linux-meta/+bug/292515](https://bugs.launchpad.net/ubuntu/+source/linux-meta/+bug/292515)

---

### Post by anamorgan on 2008-11-05
I use acer aspire, and in it ,  dont even know why teh download resume takesa lot of freak time, what ever, going slow with ubuntu, aint even know why.

---

### Post by Nomar on 2008-11-06
Confirming this bug on a Lenovo Thinkpad T500. Your script works, thanks!

---

### Post by fongandrew on 2008-11-06
Afty, a number of other packages (acpi-support, powermanagement-interface, ubuntu-desktop) depend on vbetool, so I'm a little reluctant to remove it.

At any rate, petri's script works for me. The only problem is that while it's waiting, I get a string of "bad: sheduling for the idle thread" errors -- but then it suspends / hibernates just fine.

---

### Post by vicjang on 2008-11-09
Hello,
I don't use ubuntu but I also got a new T400 recently.
I am not quite sure what happen to this specific case but
I am sure that a large amount of T400 have the problem of
suspending or freezing after "Sleep", "Hibernation", and "Restart". Some of them even cannot be shutdown and turned on normally.
I believe that this is a hardware problem.

If you can't find any solution using tweak or other software configuration, just call Lenovo Support and have your motherboard changed. The problem will be solved.

Good luck :)

---

### Post by MagiSu on 2008-11-09
> **vicjang said:**
> Hello,
I don't use ubuntu but I also got a new T400 recently.
I am not quite sure what happen to this specific case but
I am sure that a large amount of T400 have the problem of
suspending or freezing after "Sleep", "Hibernation", and "Restart". Some of them even cannot be shutdown and turned on normally.
I believe that this is a hardware problem.

If you can't find any solution using tweak or other software configuration, just call Lenovo Support and have your motherboard changed. The problem will be solved.

Good luck :)

Does that mean it is the hardware problem? I have my computer hibernate, and now Ubuntu can NOT boot!

---

### Post by jan. on 2008-11-10
Well, I believe there is indeed a concurrency problem, since the script petri0 posted is working out for me.

I did not have any hardware related boot problems. I am using my T400 with all devices enabled and integrated graphics instead of discrete ATI.

---

### Post by softtower on 2008-11-11
Hibernation aside, what kind of performance are you guys getting out of your X4500-equipped Thinkpads? I have had Dell E6500 with this card for a week, and Compiz was so slow that machine was barely usable. I am hoping this was Dell-only issue and X4500-equipped Thinkpads work fine.

What's your glxgears score?

---

### Post by afty on 2008-11-11
> **softtower said:**
> Hibernation aside, what kind of performance are you guys getting out of your X4500-equipped Thinkpads? I have had Dell E6500 with this card for a week, and Compiz was so slow that machine was barely usable. I am hoping this was Dell-only issue and X4500-equipped Thinkpads work fine.

What's your glxgears score?
My T400 with the integrated graphics gets around 720 fps on glxgears.  Compiz runs reasonably well on this machine.

---

### Post by afty on 2008-11-12
Petri's script worked for me on my T400, and my system comes out of suspend now, but my sound isn't working after a resume.  I get no sound from applications like Rhythmbox or Flash Player (Youtube, etc.), either through the speakers or the headphone port.

Is anyone else having this problem?

Edit: Restarting pulseaudio after resume fixes the problem.

---

### Post by cdEWoozy on 2008-11-19
> **petri0 said:**
> Please report if this works for you! The sleep period can easily be made longer if necessary.

I just tried it with my Dell Latitude E6400 and it worked.

---

### Post by mikhmv on 2008-11-19
On Lenovo T500 doesn't work. Gave error message:
btsub_intr_complete: hci0 urb ffff88009c140600 failed to resubmit (19)
btusb_send_frame: hci0 urb ffff8800a245e180 submission failed

---

### Post by jan. on 2008-11-20
> **mikhmv said:**
> On Lenovo T500 doesn't work. Gave error message:
btsub_intr_complete: hci0 urb ffff88009c140600 failed to resubmit (19)
btusb_send_frame: hci0 urb ffff8800a245e180 submission failed

I get those warnings on my T400 too, but it doesn't crash my suspend/resume or hibernate/resume cycle.

---

### Post by entner on 2008-11-24
The CPU trick also works for my Dell Latitude E6400 with Intel 4500. The problem is I cannot properly set my CPU frequency scaling using the gnome-applet afterwards. It only seems to influence one CPU.

---

### Post by JohnEo on 2008-11-24
Sleep Problem with my trusty old Dell Inspiron 8200, with a new install of U-8.10: like me, it sleeps on command but wakes up black screen.I tried the little script/fix by petriO but no change in results. It's a nvidia X-server, but for moment the installation driver has not been modified for nvidia. Any suggestions?

---

### Post by slouse on 2008-11-24
Here is another dimension to it:
Similar problem on Dell Latitude D810, single processor, so turning off processors is not an option. :)
I get the ominous btusb_intr_complete etc. message during hibernation and when I resume, I see a weird stripe at the top of the desktop and the sound card does not work any more. This has only been happening since I upgraded to Ubuntu 8.10. Of course, I am running Gnome and haven't tried it with KDE yet.

Cheers
slouse

---

### Post by cjreynold on 2008-11-25
> **petri0 said:**
> Hi!

This problem affects not just the Lenovo T400 but also for example the new Dell Latitude E4200, HP EliteBook 2530p, Sony Vaio VGN-TT1, Toshiba R600, or anything else with the "Mobile Intel® GM45 Express Chipset" or X4500. I have exactly the same symptoms on my E4200 running intrepid.

The bug most certainly resides in the xserver-xorg-video-intel code. The fact that is manifests itself only with gnome desktop and not with KDE or text mode gives some clue. It is not compiz related as disabling compiz has no effect. I would say that this is a classical multiprocessor concurrency control problem! Disabling all but one core makes the bug disappear.

Here is my suggestion for a workaround. Save in /etc/pm/sleep.d/00CPU with 755 permissions. Note that it has to be called 00CPU so that it gets executed before and after anything else.

```
#!/bin/sh
# Workaround for concurrency bug in xserver-xorg-video-intel 2:2.4.1-1ubuntu10.
# Save this as /etc/pm/sleep.d/00CPU

. "${PM_FUNCTIONS}"

case "$1" in
	hibernate|suspend)
		for i in /sys/devices/system/cpu/cpu*/online ; do
			echo 0 >$i
		done
		;;
	thaw|resume) 
		sleep 10	# run with one core for 10 secs
		for i in /sys/devices/system/cpu/cpu*/online ; do
			echo 1 >$i
		done
		;;
	*)
		;;
esac
```

Please report if this works for you! The sleep period can easily be made longer if necessary.

Petri K

Thanks man this worked on me latitude e4200.

---

### Post by entner on 2008-11-25
There are also indications that a patch of the DRM code in the kernel itself solves the problem:
[http://linux.derkeiler.com/Mailing-Lists/Kernel/2008-11/msg03815.html](http://linux.derkeiler.com/Mailing-Lists/Kernel/2008-11/msg03815.html)

---

### Post by weezuhl on 2008-11-26
On my T500, I am using (a modification of) petri0's script, I am able to suspend, hibernate, and resume, but my computer will freeze whenever my second core is enabled, i.e., when echo 1 > online is executed.  I have increased the sleep timer, and eventually commented out all of the lines in the second case of the script, and the resume process works as expected and can be suspended/hibernated repeatedly, as long as it runs off of one core only.  However, in the terminal the command
```
echo 1 > sudo tee /sys/devices/system/cpu/cpu1/online
``` does not even return to the prompt before the computer locks up.  Diabling/Enabling the core when no suspends or hibernations have been performed since the previous reboot does not result in any problems.

I am hesitant to try the workaround in [http://www.mail-archive.com/ubuntu-bugs@lists.ubuntu.com/msg1028992.html]("http://www.mail-archive.com/ubuntu-bugs@lists.ubuntu.com/msg1028992.html").  

Any other suggestions?

---

### Post by rmcd on 2008-12-02
Petri0's script worked on my Thinkpad X200s! Thank you! Four successful hibernations in a row. Previously I could not do more than one without a lockup on the resume.

Update: Petri0's script prevented lockups, but the system was flaky after resuming (the processors were stuck at 800mhz, for example). Updating to the 2.6.27.10.13 kernel (from intrepid-proposed) fixed these issues. Hibernation and suspend now works as it should. (I have left Petri0's script in place.)

---

### Post by bennywhere on 2008-12-05
Does anybody have an idea on how to debug the suspend issue?

I'm running 8.10 on a t400 and while it used to work with the script provided in a previous post, it somehow ceased to work properly.

Any idea?

Thanks!

EDIT:
So far I have figured out that it does work ONCE when using pm-suspend.  After it resumes properly that one time, I can't suspend again but have to reboot first. It doesn't seem to work at all if I use the suspend feature in kpowersave.

EDIT2:
for testing purposes I have recompiled the kernel to NOT use SMP, but that doesn't fix it either... still no luck! 
Windows can successfully suspend and resume, so I'm convinced it's not a hardware issue.

EDIT3:
pm-hibernate works successfully every time. But pm-suspend still works only once, and then hangs with a black screen.

Am I really the only one where petri0's fix doesn't work?

Any help in figuring this out is greatly appreciated!

FINAL EDIT:
Ok, so I've got it figured (only for suspend; hibernate still doesn't work) out and post it here in the hope that this helps someone else:
Line 5 of petri0's script:

. "${PM_FUNCTIONS}"

has to be replaced with:

. "/usr/lib/pm-utils/functions"

for successful resume from suspend to work.  This is with Intel integrated graphics.

---

### Post by uljanow on 2008-12-11
Suspend/Hibernate works without modifications if dedicated graphic (fglrx) is set in the BIOS.

---

### Post by velmont on 2008-12-17
I've been bothered by only being able to make one suspend and then restart. I always carry my T400 with me, and I use it all over the place all the time. So I really need suspending.

So thank you bennywere for the fix, and of course petri0 which provided the fix which needed a small fix.

I've successfully resumed 3-4 times now with now problem. I'll report back if it breaks after a day of heavy usage. If else, it's smoking hot ;-)

---

### Post by shinew on 2008-12-25
hey, thank you guys for the excellent finding. it works flawlessly on my t400! :guitar:
now i just need to get the tp_smapi to work...

---

### Post by shinew on 2008-12-25
hmm... although this does work. I noticed that when the laptop wakes up, it needs to wake up twice before it resumes operation.
I meant when I wake it up from the sleep state, it turns on for few seconds, then without prompting me for the password, it goes back to sleep again. Then when I wake it up again, it prompts for password and I can resume desktop without any issues. This has been consistent with my last 3 tries on my T400. 

so could anyone take the work around a step further? thanks! :D

---

### Post by Neville Grech on 2008-12-27
The fix doesn't work for me. I have a T500 though.

---

### Post by sforces on 2008-12-31
> **entner said:**
> The CPU trick also works for my Dell Latitude E6400 with Intel 4500. The problem is I cannot properly set my CPU frequency scaling using the gnome-applet afterwards. It only seems to influence one CPU.
Same problem for me. I tried this on a ThinkPad x61 though. Have you resolved your issues with the second core in the gnome freq applet?

---

### Post by entner on 2008-12-31
> **sforces said:**
> Same problem for me. I tried this on a ThinkPad x61 though. Have you resolved your issues with the second core in the gnome freq applet?

No, I got used to it. There seems to be work done on this issues with Kernel patches and new Intel drivers, I will just wait.

---

### Post by sforces on 2008-12-31
> **entner said:**
> No, I got used to it. There seems to be work done on this issues with Kernel patches and new Intel drivers, I will just wait.
Someone suggested that there's a fix in the Kernel and/or Intel drivers (as you said) so I just installed a proposed Kernel - 2.6.27-11 and updated Intel driver and still same issues in it. :(

---

### Post by bterwijn on 2009-01-02
hi,

Atleast on my Thinkpad X200 with Intrepid Ibex I fixed the 'resume after suspend' problem by getting, making and installing the latest version of 'xf86-video-intel' (which requires libdrm-2.4.3 installed) with:

[INDENT]git clone git://git.freedesktop.org/git/xorg/driver/xf86-video-intel[/INDENT]
[INDENT]cd xf86-video-intel[/INDENT]
[INDENT]./autogen.sh[/INDENT]
[INDENT]./configure[/INDENT]
[INDENT]make[/INDENT]
[INDENT]sudo make install[/INDENT]
 
And adding the line

[INDENT]Driver     	"intel"[/INDENT]

to the file '/etc/X11/xorg.conf' like this:

Section "Device"
	Identifier	"Configured Video Device"
	Driver     	"intel"
EndSection

The script that temporarily disables all but one cpu didn't work for me.

kind regards,
Bas Terwijn

---

### Post by mce230 on 2009-01-05
Petri's single core on wakeup fix worked for me with Intrepid Ibex on a new ThinkPad T500.  Thanks.

---

### Post by Affejunge on 2009-01-06
> **bterwijn said:**
> hi,

Atleast on my Thinkpad X200 with Intrepid Ibex I fixed the 'resume after suspend' problem by getting, making and installing the latest version of 'xf86-video-intel' (which requires libdrm-2.4.3 installed) with:




I had to do the same thing on my Dell Studio 1537 with the Intel networking card and Intel 4500. 
The script did work, sorta.  When X resumed, I had no networking (lost the intel wireless driver) I suppose a modprobe would work...but a pain.

With the new driver, after several suspend cycles, the only issue I get, occasionally the screen will not initialize.  Not a huge deal, <ctrl><alt><backspace> and I am back in business.

Thanks for the tip, Bas.  Though compiling the libdrm and driver reminded me of why I hate Linux sometimes (endless package chasing)!! :)

Bas, did you also update MESA driver?

BTW, with the new libdrm and driver, glxgears jumped from 410 to 720! (still not as good as 32000 on my desktop..but hey, this machine is not for gaming)

Good luck to all...

---

### Post by DesertF0x on 2009-01-06
For me it Works now after some regular updates with intel graphics activated. Tested three times suspend to disk.

---

### Post by bterwijn on 2009-01-06
Also for me the new regular updates (of I think xserver-xorg-video-* or libdrm-intel1) seemed to solve the resume problem. I had to remove my manually installed xf86-video-intel and libdrm software as it caused problems after the new update and then 'sudo aptitude reinstall' the xserver-xorg-video-intel and libdrm2, libdrm-intel1 packages.

So Affejunge, no more need for manual tweaking :). And btw, I didn't touch the MESA driver.

[EDIT] see for additional info: [http://ubuntuforums.org/showpost.php?p=6513758&postcount=57](http://ubuntuforums.org/showpost.php?p=6513758&postcount=57)

greetings,
Bas

---

### Post by fstonedahl on 2009-01-07
Hmm, I don't think I've seen any of these updates go by on my T400 w/ intel graphics, and I've tried checking for new updates with synaptic.

Are you people using the standard repositories?  What version of the driver do you have installed?
```

aptitude show xserver-xorg-video-intel

```

I have:

Version: 2:2.4.1-1ubuntu10

I did Petri's fix earlier, and it worked pretty well for me.  Resuming from "sleep" seems to work every time, but resuming from "hibernation" still freezes (with a black screen and white cursor) perhaps 20% of the time.

So if there's something I can do to get hibernation working consistently, that would be great.

Thanks!

~Forrest

---

### Post by Affejunge on 2009-01-07
I too see no updated driver... Bas, do you have back-ports enabled for updates?

Well, compiling libdrm and the driver has worked like a charm for me, so I am happy, but I would like to get back to package-managed (the whole reason we use distributions like Ubuntu! :) )

Take care,
Mark

---

### Post by bterwijn on 2009-01-07
I found some non-standard sources in my /etc/apt/sources.list file below, see the bottom two. Maybe that did the trick. I tried many things to fix the problem, so not sure what exactly did the trick but I am happy now. This is what made me add them, I kind of forgot about it, sorry bout that:

[https://launchpad.net/~intel-gfx-testing/+archive](https://launchpad.net/~intel-gfx-testing/+archive)

After adding the sources to the file use 'sudo aptitude update' to update the package manager.

hope this helps,
Bas Terwijn



# deb cdrom:[Ubuntu 8.10 _Intrepid Ibex_ - Release amd64 (20081029.2)]/ intrepid main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) intrepid main restricted
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) intrepid main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) intrepid-updates main restricted
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) intrepid-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) intrepid universe
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) intrepid universe
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) intrepid-updates universe
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) intrepid-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) intrepid multiverse
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) intrepid multiverse
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) intrepid-updates multiverse
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) intrepid-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://nl.archive.ubuntu.com/ubuntu/](http://nl.archive.ubuntu.com/ubuntu/) intrepid-backports main restricted universe multiverse
# deb-src [http://nl.archive.ubuntu.com/ubuntu/](http://nl.archive.ubuntu.com/ubuntu/) intrepid-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) intrepid partner
deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) intrepid partner

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) intrepid-security main restricted
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) intrepid-security main restricted
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) intrepid-security universe
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) intrepid-security universe
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) intrepid-security multiverse
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) intrepid-security multiverse
deb [http://ppa.launchpad.net/surban/ubuntu](http://ppa.launchpad.net/surban/ubuntu) hardy main

## stuff to fix the xserver-xorg-video-intel to avoid freeze on resume 
## after sleeping
deb [http://ppa.launchpad.net/intel-gfx-testing/ubuntu](http://ppa.launchpad.net/intel-gfx-testing/ubuntu) intrepid main
deb-src [http://ppa.launchpad.net/intel-gfx-testing/ubuntu](http://ppa.launchpad.net/intel-gfx-testing/ubuntu) intrepid main

---

### Post by fstonedahl on 2009-01-09
I removed Petri's workaround 00CPU script.

And I edited my /etc/apt/sources.list to contain the intel-gfx-testing PPA that Bas mentioned:

> **bterwijn said:**
> ## stuff to fix the xserver-xorg-video-intel to avoid freeze on resume 
## after sleeping
deb [http://ppa.launchpad.net/intel-gfx-testing/ubuntu](http://ppa.launchpad.net/intel-gfx-testing/ubuntu) intrepid main
deb-src [http://ppa.launchpad.net/intel-gfx-testing/ubuntu](http://ppa.launchpad.net/intel-gfx-testing/ubuntu) intrepid main

Then I updated everything via Synaptic.

Result: both sleep & hibernate seem to be working now.  :)  

I've only tried it a couple times, but I'm hopeful.  I'll post again if problems recur.

---

### Post by entner on 2009-01-09
I think it is not necessary to use a PPA. I just used the new kernel from -proposed and suspend seems to work.

[https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/276943/comments/57](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/276943/comments/57)
[https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/276943](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/276943)

Burt

---

### Post by afty on 2009-01-09
I have also updated everything via Synaptic.  Sleep works now without Petri's script.  I don't know what was updated to fix it, but something must have changed.  I have not touched my sources file.

---

### Post by fstonedahl on 2009-01-09
Hmm, actually, after updating my intel graphics driver using the intel-gfx-testing PPA, my 3D graphics performance in some apps seems to have gotten seriously slow/clunky.  (e.g. Neverball is unplayable now, but worked fine before)  Compiz fusion still runs well though.

So if the resume problem can be fixed without fiddling with the graphics driver, then that seems better.

Does anyone know how (if?) I can use apt/aptitude/synaptic to revert to my previous driver version?

From the PPA, it updated these two packages:
libdrm2 (2.4.1-0ubuntu7~intrepid)
xserver-xorg-video-intel (2.4.1-0ubuntu7~intrepid)

And installed this one as new:
libdrm-intel1 (2.4.1-0ubuntu7~intrepid)

Thanks,

~Forrest

---

### Post by fstonedahl on 2009-01-10
Update:  I figured out how to roll back to my previous graphics driver (using force version in Synaptic, back to version "2:2.4.1-1ubuntu10), and my 3D performance is okay again.

However, the hibernation/resume freezing issue is still here.  My packages (from the standard repositories) are totally up to date.  I haven't tried the driver from the "-proposed" repository.  Should I dare?

It's seems to me like it is an Intel graphics driver issue, but I experienced enough bugs with the newer driver that I'll stick with the lesser of two evils -- Petri's workaround 00CPU script and the occasional freezing.

For people who've had success with newer graphics drivers, what version of the driver are you using and what hardware do you have?  I'm running intrepid on a Thinkpad T400 with an intel GMA 4500MHD card, and a 1440x900 screen resolution (if that even matters).

---

### Post by almikul on 2009-01-15
> **fstonedahl said:**
> However, the hibernation/resume freezing issue is still here.  My packages (from the standard repositories) are totally up to date.  I haven't tried the driver from the "-proposed" repository.  Should I dare?
Try **acpi-support_0.114-0intrepid1** update. It solved my long-lasting problems with hibernate and suspend on Gateway MT6705. And as far as I checked,  everything is functioning well on wake-up too. I got this update automatically with only regular updates allowed (no proposed/backports), so you should be able too. If not, then download it and install it manually.

---

### Post by phillme on 2009-02-03
Hello.
I own a t400 and resuming does not work any longer (it worked without dri before). The hd starts but the moon stays on and the display remains black. I guess a bios update may be the cause, as it worked with the kubuntu install cd 8.1 (only crash with freezed mouse pointer) when I installed the notebook.

So my question...
If anybody has a resuming t400 or t500 which BIOS version do you use?

Feedback is really appreciated. This problem is really driving me nuts.

Thanks in advance
phillme

---

### Post by fstonedahl on 2009-02-03
I have a T400, with working hibernate/resume.  

Bios version:  1.15
Bios date:     9/8/2008

Hope that helps.

---

### Post by phillme on 2009-02-03
> **fstonedahl said:**
> I have a T400, with working hibernate/resume.  

Bios version:  1.15
Bios date:     9/8/2008

Hope that helps.

Yeah it does indeed. Thanks. If I may ask...
Which kernel do you use? (2.6.27?)

Cheers,
phillme

---

### Post by fstonedahl on 2009-02-03
Yeah, I'm running intrepid 8.10, with this kernel: 2.6.27-11-generic

---

### Post by brngk on 2009-02-05
Similar problem on a T61p, with the NVIDIA 570m chipset.
Did not have the problem with 8.0. Uptodate on acpi 
patches, etc. Also, I'm getting this error in KDE 4.0 and 4.2.

---

### Post by phillme on 2009-02-08
> **brngk said:**
> Similar problem on a T61p, with the NVIDIA 570m chipset.
Did not have the problem with 8.0. Uptodate on acpi 
patches, etc. Also, I'm getting this error in KDE 4.0 and 4.2.

I found a solution. See [http://en.gentoo-wiki.com/wiki/Lenovo_ThinkPad_T400#Power_management](http://en.gentoo-wiki.com/wiki/Lenovo_ThinkPad_T400#Power_management) for details. Resuming now works flawlessly.

---

### Post by jeongmal on 2009-02-08
> **phillme said:**
> I found a solution. See [http://en.gentoo-wiki.com/wiki/Lenovo_ThinkPad_T400#Power_management](http://en.gentoo-wiki.com/wiki/Lenovo_ThinkPad_T400#Power_management) for details. Resuming now works flawlessly.

I can confirm that phillme's solution works on a T400 for both suspend to ram and suspend to disk. I made no other power management related changes besides changing the BIOS settings referenced on that page. It works in laptop mode also.

---

### Post by Affejunge on 2009-02-17
For Dell Studio 15 ...

I can confirm, with over a month running, compiling and installing the latest drivers from [http://intellinuxgraphics.org/](http://intellinuxgraphics.org/) (ver 2.6.0) fixes all issues.  Even when I tried the drivers from ```
deb http://ppa.launchpad.net/intel-gfx-testing/ubuntu intrepid main
deb-src http://ppa.launchpad.net/intel-gfx-testing/ubuntu intrepid main

```
I would get random lock ups on resume.  With over a month of testing I have had NO lockups, I can use XvMC for MPEG2 content and I have a glxgears of 740fps.

Hope this helps.

---

### Post by flo-alb on 2009-03-19
Hi,

i got the same messages on my T400:
btusb_intr_complete: hci0 urb f4f02c00 failed to resubmit (19)
btusb_send_frame: hci0 urb f7efd800 submission failed

Jango wrote in #10: > So i started the same system with Discrete Graphics, ATI 3470 with radeon driver.... and
Suspend and Hibernate, both work very well without errors!

How do you do this? i am yust a new linux guy so please be patient with me....

Thanks

---

### Post by jango4 on 2009-03-19
@ flo-alb

> i got the same messages on my T400:
btusb_intr_complete: hci0 urb f4f02c00 failed to resubmit (19)
btusb_send_frame: hci0 urb f7efd800 submission failed

You can ignore this messages. There are no disadvantages and in Jaunty they are gone. 
With a fully updated Ubuntu 8.10 you do not need Petri's workaround any more. Suspend/Hibernate is working correctly then. 

> 
How do you do this? i am yust a new linux guy so please be patient with me....

You can change your graphic card settings only in BIOS. There you can either choose the internal Intel card or the ATI card!

More informatins here: [http://www.thinkwiki.org/wiki/Install_Ubuntu_8.10_(Intrepid_Ibex)_on_a_Thinkpad_T400]("http://www.thinkwiki.org/wiki/Install_Ubuntu_8.10_(Intrepid_Ibex)_on_a_Thinkpad_T400")

jango

---

### Post by flo-alb on 2009-03-23
@Jango: Thanks for your reply.

But there is still a problem with hibernation at my T400. 
Yes, i have a fully updated Ubuntu 8.10 but Hibernation isn't working.
I have no problems with Suspend - works fine. I can also start Hibernation - but when i wake it up it just does a normal boot and all my windows and opened programs are gone.

since a few days i have also problems with sound: nothing comes out of my speakers - even not with connected headphones. I only can hear some cracking noise. I have to look now in the forum about that problem also.

CU

---

### Post by jango4 on 2009-03-23
Hi!

First your sound problem. I had the same problem after an update. You only have to open gnome-volume-control with pressing Alt + F2 and type  "gnome-volume-control"
Then you have to turn your PCM controller up. Finished!

Your hibernate problem: What BIOS Version are you running? There are brand new versions available! Maybe this solves your problem. When you go in hibernation, is your Moon-Led blinking? Is there an error message on resume?

jango

---

### Post by terdon on 2009-12-01
Hi all, I also have a t400 and have been having suspend/resume problems. It used to work at some point (under Jaunty I think, maybe intrepid also) but now when attempting to resume from suspend I get a blank (black) screen. I can hear the HDD spinning up but Ctrl+alt+del doesn't work and I have to do a hard reboot. 

I only use windows for games so I thought my problem was exclusive to linux. However, to my great surprise, I recently realised it was also there in windows...

So, any ideas on what can disable resume on an otherwise perfectly fine machine in 2 different operating systems? Some obscure BIOS option I have tweaked? Weirdly specific and limited hardware problem?

I am using the ATI card. I set up the intel one at some point but could not get suspend to work :) so I switched back to ATI.

---

### Post by jango4 on 2009-12-02
Sounds a lot like a bios problem. Do a bios update at first, i recommend.
With Jaunty and with Karmic i had no problems with Suspend/Hibernate neither with the Intel nor with the ATI card.

greetings,
jango

---

### Post by terdon on 2009-12-02
Well, I updated the BIOS. It broke my machine... I had to physically open it and remove the CMOS battery. After this everything is fine. I can resume from suspend with no problem.

However, since it DID first break my machine I would not recommend this path unless you are not afraid to open your computer...

---

### Post by jango4 on 2009-12-02
Sorry for that... but this shows, that there was something wrong with your Thinkpad anyway ;-)
In the worst case Lenovo Hotline and they will fix it! The support is great there.

greetings

---

### Post by terdon on 2009-12-02
Don't get me wrong, I appreciate the help! I did fix it after all. However, I spent an afternoon terrified that I killed my machine...

My warning is for people who are not comfortable with hardware. Or who have weak hearts...

In any case, BIOS seemed to be the way to go, thanks!

---

### Post by mynk on 2011-09-08
Is this problem fixed? I am seeing an issue with my T400 and also my desktop. It just returns to the lock screen. I am forced to use suspend which works better. I see some errors on the console when trying to hibernate. I will share the kern.log when I next see the messages.

---

### Post by mynk on 2011-09-08
Got the dmesg output after clearing it up fully before attempting the hibernate. I guess only the relevan messages should be there. The one of interest being Not enough swap space - is that a problem? I have put the details towards the end.

> ```
[FONT="Courier New"]
root@mayankr-T400:/var/log# dmesg
[24552.610289] EXT4-fs (sda8): re-mounted. Opts: errors=remount-ro,user_xattr,commit=0
[24557.236342] PM: Marking nosave pages: 000000000009e000 - 0000000000100000
[24557.236347] PM: Basic memory bitmaps created
[24557.236348] PM: Syncing filesystems ... done.
[24557.720024] Freezing user space processes ... (elapsed 0.09 seconds) done.
[24557.816139] Freezing remaining freezable tasks ... (elapsed 0.01 seconds) done.
[24557.832201] PM: Preallocating image memory... done (allocated 290982 pages)
[24592.961404] PM: Allocated 1163928 kbytes in 35.12 seconds (33.14 MB/s)
[24592.961406] Suspending console(s) (use no_console_suspend to debug)
[24593.008241] parport_pc 00:0b: disabled
[24593.008315] serial 00:0a: disabled
[24593.008709] serial 00:0a: wake-up capability disabled by ACPI
[24593.008985] pciehp 0000:00:1c.3:pcie04: pciehp_suspend ENTRY
[24593.009474] ACPI handle has no context!
[24593.009615] e1000e 0000:00:19.0: PME# enabled
[24593.009622] e1000e 0000:00:19.0: wake-up capability enabled by ACPI
[24593.016059] ACPI handle has no context!
[24593.112354] HDA Intel 0000:00:1b.0: PCI INT B disabled
[24593.128017] PM: freeze of drv:HDA Intel dev:0000:00:1b.0 complete after 119.002 msecs
[24593.368030] sd 0:0:0:0: [sda] Synchronizing SCSI cache
[24593.368415] PM: freeze of drv:sd dev:0:0:0:0 complete after 406.194 msecs
[24593.368425] PM: freeze of drv:scsi dev:target0:0:0 complete after 406.201 msecs
[24593.368434] PM: freeze of drv:scsi dev:host0 complete after 405.498 msecs
[24593.368556] PM: freeze of drv:ahci dev:0000:00:1f.2 complete after 359.646 msecs
[24594.024029] [drm] Disabling audio support
[24594.160498] PM: freeze of drv:radeon dev:0000:01:00.0 complete after 1151.623 msecs
[24594.160519] PM: freeze of drv:pcieport dev:0000:00:01.0 complete after 1150.836 msecs
[24594.160544] PM: freeze of drv: dev:pci0000:00 complete after 1150.829 msecs
[24594.160553] PM: freeze of devices complete after 1198.774 msecs
[24594.162124] PM: late freeze of devices complete after 1.569 msecs
[24594.162464] ACPI: Preparing to enter system sleep state S4
[24594.344052] PM: Saving platform NVS memory
[24594.345872] Disabling non-boot CPUs ...
[24594.448014] CPU 1 is now offline
[24594.448342] Extended CMOS year: 2000
[24594.448426] PM: Creating hibernation image:
[24594.452006] PM: Need to copy 204444 pages
[24594.452006] PM: Normal pages needed: 89774 + 1024, available pages: 178507
[24594.452006] PM: Hibernation image created (204444 pages copied)
[24594.452006] Extended CMOS year: 2000
[24594.452006] Enabling non-boot CPUs ...
[24594.452006] Booting Node 0 Processor 1 APIC 0x1
[24594.350066] Initializing CPU#1
[24594.536488] ACPI Exception: AE_BAD_PARAMETER, Returned by Handler for [EmbeddedControl] (20110112/evregion-474)
[24594.536493] ACPI Error: Method parse/execution failed [\_SB_.PCI0.LPC_.EC__.LPMD] (Node f4428738), AE_BAD_PARAMETER (20110112/psparse-536)
[24594.536499] ACPI Error: Method parse/execution failed [\_PR_.CPU0._PPC] (Node f4582000), AE_BAD_PARAMETER (20110112/psparse-536)
[24594.536504] ACPI Error: Method parse/execution failed [\_PR_.CPU1._PPC] (Node f45820d8), AE_BAD_PARAMETER (20110112/psparse-536)
[24594.536511] ACPI Exception: AE_BAD_PARAMETER, Evaluating _PPC (20110112/processor_perflib-144)
[24594.540013] Switched to NOHz mode on CPU #1
[24594.540056] CPU1 is up
[24594.541490] ACPI: Waking up from system sleep state S4
[24594.929053] PM: early thaw of devices complete after 1.019 msecs
[24594.929334] pciehp 0000:00:1c.3:pcie04: pciehp_resume ENTRY
[24594.929370] pci 0000:00:1e.0: setting latency timer to 64
[24594.929436] ahci 0000:00:1f.2: restoring config space at offset 0x1 (was 0x2b00403, writing 0x2b00407)
[24594.929475] ahci 0000:00:1f.2: setting latency timer to 64
[24594.929498] radeon 0000:01:00.0: power state changed by ACPI to D0
[24594.929502] radeon 0000:01:00.0: power state changed by ACPI to D0
[24594.929548] radeon 0000:01:00.0: setting latency timer to 64
[24594.943705] radeon 0000:01:00.0: WB enabled
[24594.955378] iwlagn 0000:03:00.0: RF_KILL bit toggled to disable radio.
[24594.955734] sd 0:0:0:0: [sda] Starting disk
[24594.955866] HDA Intel 0000:00:1b.0: BAR 0: set to [mem 0xfc620000-0xfc623fff 64bit] (PCI address [0xfc620000-0xfc623fff])
[24594.955883] HDA Intel 0000:00:1b.0: restoring config space at offset 0xf (was 0x200, writing 0x20b)
[24594.955903] HDA Intel 0000:00:1b.0: restoring config space at offset 0x3 (was 0x0, writing 0x10)
[24594.955909] HDA Intel 0000:00:1b.0: restoring config space at offset 0x1 (was 0x100000, writing 0x100102)
[24594.955931] HDA Intel 0000:00:1b.0: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[24594.955937] HDA Intel 0000:00:1b.0: setting latency timer to 64
[24594.955981] HDA Intel 0000:00:1b.0: irq 45 for MSI/MSI-X
[24594.956049] e1000e 0000:00:19.0: BAR 0: set to [mem 0xfc600000-0xfc61ffff] (PCI address [0xfc600000-0xfc61ffff])
[24594.956054] e1000e 0000:00:19.0: BAR 1: set to [mem 0xfc625000-0xfc625fff] (PCI address [0xfc625000-0xfc625fff])
[24594.956060] e1000e 0000:00:19.0: BAR 2: set to [io  0x1840-0x185f] (PCI address [0x1840-0x185f])
[24594.956075] e1000e 0000:00:19.0: restoring config space at offset 0xf (was 0x100, writing 0x10b)
[24594.956097] e1000e 0000:00:19.0: restoring config space at offset 0x1 (was 0x100000, writing 0x100107)
[24594.956183] e1000e 0000:00:19.0: irq 49 for MSI/MSI-X
[24594.968044] firewire_ohci 0000:15:00.1: BAR 0: set to [mem 0xf4301000-0xf43017ff] (PCI address [0xf4301000-0xf43017ff])
[24594.968077] firewire_ohci 0000:15:00.1: restoring config space at offset 0x3 (was 0x800000, writing 0x802010)
[24594.968085] firewire_ohci 0000:15:00.1: restoring config space at offset 0x1 (was 0x2100000, writing 0x2100106)
[24594.974924] [drm] ring test succeeded in 1 usecs
[24594.974937] [drm] ib test succeeded in 0 usecs
[24594.974939] [drm] Enabling audio support
[24594.993269] ACPI Error: f459881c is not a namespace node [UNDEFINED] (20110112/nsaccess-329)
[24594.993273] ACPI Error: ACPI Error: f459881c is not a namespace node [UNDEFINED] (20110112/nsaccess-329)
[24594.993277] [Could not get node by pathname][NULL NAME], AE_AML_INTERNAL (20110112/uteval-103)
[24594.993282] serial 00:0a: can't evaluate _CRS: 12303
[24594.993284] serial 00:0a: activation failed
[24594.993290] legacy_resume(): pnp_bus_resume+0x0/0x70 returns -5
[24594.993292] PM: Device 00:0a failed to thaw: error -5
[24594.993320] ACPI Error: f4598c1c is not a namespace node [UNDEFINED] (20110112/nsaccess-329)
[24594.993323] ACPI Error: ACPI Error: f4598c1c is not a namespace node [UNDEFINED] (20110112/nsaccess-329)
[24594.993327] [Could not get node by pathname][NULL NAME], AE_AML_INTERNAL (20110112/uteval-103)
[24594.993330] parport_pc 00:0b: can't evaluate _CRS: 12303
[24594.993332] parport_pc 00:0b: activation failed
[24594.993334] legacy_resume(): pnp_bus_resume+0x0/0x70 returns -5
[24594.993336] PM: Device 00:0b failed to thaw: error -5
[24594.993339] legacy_resume(): pnp_bus_resume+0x0/0x70 returns -19
[24594.993341] PM: Device 00:0c failed to thaw: error -19
[24595.032149] firewire_core: skipped bus generations, destroying all nodes
[24595.264091] ata2: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[24595.267473] ata2.00: ACPI cmd e3/00:1f:00:00:00:a0 (IDLE) succeeded
[24595.268465] ata2.00: ACPI cmd e3/00:02:00:00:00:a0 (IDLE) succeeded
[24595.272094] ata1: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[24595.274130] ata1.00: ACPI cmd ef/02:00:00:00:00:a0 (SET FEATURES) succeeded
[24595.274135] ata1.00: ACPI cmd f5/00:00:00:00:00:a0 (SECURITY FREEZE LOCK) filtered out
[24595.274139] ata1.00: ACPI cmd ef/10:03:00:00:00:a0 (SET FEATURES) filtered out
[24595.274524] ata2.00: ACPI cmd e3/00:1f:00:00:00:a0 (IDLE) succeeded
[24595.275525] ata2.00: ACPI cmd e3/00:02:00:00:00:a0 (IDLE) succeeded
[24595.277091] ata2.00: configured for UDMA/33
[24595.278434] ata1.00: ACPI cmd ef/02:00:00:00:00:a0 (SET FEATURES) succeeded
[24595.278439] ata1.00: ACPI cmd f5/00:00:00:00:00:a0 (SECURITY FREEZE LOCK) filtered out
[24595.278443] ata1.00: ACPI cmd ef/10:03:00:00:00:a0 (SET FEATURES) filtered out
[24595.280339] ata1.00: configured for UDMA/100
[24595.316312] PM: thaw of drv:sd dev:0:0:0:0 complete after 360.572 msecs
[24595.316340] PM: thaw of drv:scsi_disk dev:0:0:0:0 complete after 284.229 msecs
[24595.316344] PM: thaw of drv:scsi_device dev:0:0:0:0 complete after 360.572 msecs
[24595.456143] PM: thaw of drv:pcmcia_socket dev:pcmcia_socket0 complete after 139.724 msecs
[24595.532115] firewire_core: rediscovered device fw0
[24596.844126] PM: thaw of drv:radeon dev:0000:01:00.0 complete after 1914.626 msecs
[24596.844148] PM: thaw of drv:drm dev:controlD65 complete after 1386.795 msecs
[24596.844266] PM: thaw of devices complete after 1915.153 msecs
[24596.844752] PM: writing image.
[24596.844759] PM: Free swap pages: 89480
[24596.844760] PM: Not enough free swap
[24596.886648] Restarting tasks ... done.
[24596.890477] PM: Basic memory bitmaps freed
[24596.890483] video LNXVIDEO:00: Restoring backlight state
[24596.891412] video LNXVIDEO:01: Restoring backlight state
[24699.037040] EXT4-fs (sda8): re-mounted. Opts: errors=remount-ro,user_xattr,commit=0
[24700.816304] e1000e 0000:00:19.0: irq 49 for MSI/MSI-X
[24700.872125] e1000e 0000:00:19.0: irq 49 for MSI/MSI-X
[24700.872367] ADDRCONF(NETDEV_UP): eth0: link is not ready
[24702.420912] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: Rx/Tx
[24702.420918] e1000e 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[24702.421087] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[24712.688036] eth0: no IPv6 routers present
root@mayankr-T400:/var/log# 



root@mayankr-T400:/var/log# cat /proc/meminfo
MemTotal:        1955572 kB
MemFree:          279060 kB
Buffers:           18560 kB
Cached:           332172 kB
SwapCached:       262764 kB
Active:           550688 kB
Inactive:        1020696 kB
Active(anon):     511000 kB
Inactive(anon):   840704 kB
Active(file):      39688 kB
Inactive(file):   179992 kB
Unevictable:         120 kB
Mlocked:             120 kB
HighTotal:       1081776 kB
HighFree:           1596 kB
LowTotal:         873796 kB
LowFree:          277464 kB
SwapTotal:       1989628 kB
SwapFree:         797096 kB
Dirty:               224 kB
Writeback:             0 kB
AnonPages:        994268 kB
Mapped:            64412 kB
Shmem:            131064 kB
Slab:              35464 kB
SReclaimable:      13684 kB
SUnreclaim:        21780 kB
KernelStack:        4592 kB
PageTables:        22528 kB
NFS_Unstable:          0 kB
Bounce:                0 kB
WritebackTmp:          0 kB
CommitLimit:     2967412 kB
Committed_AS:    7429868 kB
VmallocTotal:     122880 kB
VmallocUsed:       46668 kB
VmallocChunk:      65020 kB
HardwareCorrupted:     0 kB
HugePages_Total:       0
HugePages_Free:        0
HugePages_Rsvd:        0
HugePages_Surp:        0
Hugepagesize:       4096 kB
DirectMap4k:      122872 kB
DirectMap4M:      786432 kB
root@mayankr-T400:/var/log# 


top - 18:34:32 up  9:03,  4 users,  load average: 0.25, 3.02, 2.12
Tasks: 192 total,   4 running, 187 sleeping,   0 stopped,   1 zombie
Cpu(s):  8.1%us,  4.0%sy,  0.8%ni, 86.5%id,  0.5%wa,  0.0%hi,  0.0%si,  0.0%st
Mem:   1955572k total,  1680568k used,   275004k free,    18668k buffers
Swap:  1989628k total,  1190340k used,   799288k free,   332976k cached
[/FONT]
```

---

### Post by terdon on 2011-09-08
Well, yes it should be fixed. However, your problem seems to be different. This thread is specifically for the t400 waking from suspend/hibernate issues. If you are returned to the lockscreen you are having a completely different problem.

---

### Post by mynk on 2011-09-08
I am sorry. My problem is that the laptop does not hibernate at all. I shall file a new bug. I think suspend works.

---

### Post by Travikat on 2011-09-23
I have issues with suspend since I updated to 11.04 . Laptop is suspending , no issue here but not coming out of it . :confused:

 ~ $ uname -a
Linux pandora 2.6.38-8-generic-pae #42-Ubuntu SMP Mon Apr 11 05:17:09 UTC 2011 i686 i686 i386 GNU/Linux

---

### Post by anairam on 2011-11-02
If you have Virtual Box installed, maybe worth to check:
[http://ubuntuforums.org/showpost.php?p=11419526&postcount=5](http://ubuntuforums.org/showpost.php?p=11419526&postcount=5)

Its a Virtual Box bug: [https://www.virtualbox.org/ticket/9305](https://www.virtualbox.org/ticket/9305)

---

