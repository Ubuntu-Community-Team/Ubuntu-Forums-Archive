---
title: "Embarrassed: Suspend/Sleep doesn't work on T42 after Edgy upgrade"
date: 2006-10-09
forum: Hardware &amp; Laptops
---

### Post by smoothridersean on 2006-10-09
Yeah, I know that 5% of the internet is made up of "how to make ibm laptops sleep in linux" tutorials, but this still has me stumped.  I've tried adding kernel params (acpi_sleep=s2_bios), uninstalling an reinstalling the power management packages, and still nothing.  I'm almost certain the problem is because my dist-upgrade crashed, though, so this may be a new one.

Some hints:

- Using the "ati" (opensource) graphics driver
- MySQL is installed and running, but the sleep script seems to be configured to stop it (this is corrent)
- The "failure" is that the screen dims, but the light doesn't shut off (nor does the fan).  The "sleep" (crescent moon) light just blinks.  The machine doesn't respond to pings in this state (admittedly, I've only tested this while connected wirelessly)

Now, as I mentioned, there were two dist-upgrade problems: the first is that I recall blindly answer "nah, use the package maintainer's version" to a few questions, and the second is that the upgrade failed in the middle of installing the packages.  On reboot, X didn't work claiming the driver was missing; the driver packages had been renamed, and one I figured this out, everything went fine.  Except suspend-to-ram.  Can anyone help, or offer some direction I should look in?  Is there a way to re-run the dist-upgrade script?  Thanks for your help!

---

### Post by mariner09 on 2006-10-15
I have a clean install of Edgy Knot3 on my T41 and suspend always gives me the flashing moon.  Hibernate will occasionally do this, probably every 3rd time.

I'm also looking for any pointers on this.  Suspend2 always worked for me in Dapper, so I may have to wait for them to build for Edgy.

---

### Post by david.vikstrom on 2006-10-20
Got the same problem, arghh, be back..

---

### Post by Deus42 on 2006-10-25
I'm having the same problem with a T60p. The moon just keeps flashing and I have to power the box down. 

The really bizar thing about this is that suspend was working with the RC release of edgy, but after running an apt-get upgrade a few days later, it broke!

I going to install the RC of edgy on a separate partition and try to figure out which package upgrade broke it.

---

### Post by zeusfaber on 2006-10-26
Suspend works for me when I close the lid but when I open it again it will not come out or sleep. Hibernate work as it should. Any ideas? 

IBM z60t and edgy installed and all upgrades applied.

---

### Post by Deus42 on 2006-10-26
Well my problem is fixed by just applying the patches yesterday.

Zeusfaber - I have never dealt with with any issues with my laptop coming out of suspend. Did you try setting some of the bios options that were suggested earlier in the thread?

---

### Post by zeusfaber on 2006-10-26
I added "acpi_sleep=s2_bios". But it didn't fix it.

---

### Post by perbu on 2006-10-26
zeusfaber,

I have exactly the same problem on my z60t. Suspend/resume worked beautifully but during the last two weeks it broke somehow and now my laptop won't resume. 

Hibernate works well, though.

---

### Post by awry on 2006-10-27
I was having the same problem with my t60p.  

For me, it seems like it was kernel related.  I was continuing to use my custom-built 2.6.16 kernel with a bunch of thinkpad-specific patches.  

When I booted from the (edgy default) 2.6.17 kernel, suspend worked normally.  May be related to this change: [http://lists.suspend2.net/lurker/message/20061004.131612.0915b4b7.en.html](http://lists.suspend2.net/lurker/message/20061004.131612.0915b4b7.en.html)

Now it's time to patch a new 2.17-series kernel.  Yay!  Gotta love non-standard hardware at upgrade time.

---

### Post by zeusfaber on 2006-10-27
With regards to the included email above:

ls -al /proc/suspend2
ls: /proc/suspend2: No such file or directory

ls -al /sys/power/suspend2
ls: /sys/power/suspend2: No such file or directory


are these in a third location in edgy?

---

### Post by jdunn on 2006-10-27
Interesting.  I can't get Display Power Management to work in Edgy but it worked well in Dapper.

---

### Post by zeusfaber on 2006-10-27
Scratch that... after a bit of testing I can say it does not work.

"It does indeed look like a kernel issue as I installed the 386 kernel and it seems to suspend as expected (as far as i can tell). So it looks like an issue exclusive to the new generic kernel."

---

### Post by zeusfaber on 2006-10-28
A bug has been filed by another user, check it:

[https://launchpad.net/distros/ubuntu/+source/linux-source-2.6.17/+bug/63967](https://launchpad.net/distros/ubuntu/+source/linux-source-2.6.17/+bug/63967)

---

### Post by perbu on 2006-11-01
> **perbu said:**
> zeusfaber,

I have exactly the same problem on my z60t. Suspend/resume worked beautifully but during the last two weeks it broke somehow and now my laptop won't resume. 

Hibernate works well, though.

Fixed it! :) I added the following lines to /etc/modprobe.d/blacklist-local:

[INDENT]```
blacklist mmc_core
blacklist sdhci

```[/INDENT]

It seems the SD-card-reader somehow messes up resume. No big surprise to me, really. I've had resume-issues with this thingy before.

---

### Post by zeusfaber on 2006-11-01
Looks like it works for me. I have tried it a couple times and it seems to do the trick.

---

### Post by Deus42 on 2006-11-02
Looks like my suspend problems were fixed by updating to the 8.30.3 fglrx driver. I was previously using the driver because I am running a firegl 5200 card.

---

### Post by zeusfaber on 2006-11-02
> Looks like it works for me. I have tried it a couple times and it seems to do the trick.


It doesn't look like it works 100% of the time for me. I am curious what it causing this...I suppose I may have to wait for a kernel update or two.

---

### Post by perbu on 2006-11-03
I'm also running with vga=normal. This might also help detect what is going on when your laptop wont resume properly - you might see a message.

---

### Post by N6546R on 2006-11-03
> **awry said:**
> 
Now it's time to patch a new 2.17-series kernel.  Yay!  Gotta love non-standard hardware at upgrade time.

I'm with you there...T42 running various releases of Kubuntu. One would think that the ThinkPads were some unusual piece of hardware...

Perry

---

### Post by niekko on 2006-11-05
> Looks like my suspend problems were fixed by updating to the 8.30.3 fglrx driver.

Same here. 8.30.3 fglrx driver fixed my suspend problem on Thinkpad T60 with ATI Mobility Radeon X1300.

---

### Post by giorgione on 2006-11-06
Hi there, 

I have also the same problem with suspend to RAM on my T60p with Edgy. Unfortunately I'm a newbie, could some one tell me how I update my fglrx driver drive. Right new I use version 8.28.8

Thank you very much.

---

### Post by Deus42 on 2006-11-10
try this:

[http://wiki.cchtml.com/index.php/Ubuntu_Edgy_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Edgy_Installation_Guide)

just ignore method one, and use method 2

---

### Post by Permafrost91 on 2006-11-12
Now, I haven't thoroughly tested this solution yet but so far I've got suspend/resume working again on my X30 running a clean Edgy install by blacklisting sdhci as perbu suggested. My X30 has an Intel chipset so updating fglrx would have been no good. Also, if I blacklisted mmc_core as well, I was not able to detect my USB Flash drives after resuming. Hibernate/resume worked out of the box for me.

And I agree with N6546R, this does make ThinkPads seem like something unusual!

---

### Post by emdeem on 2006-11-12
On my X60s, adding ec_intr=0 to grub oot options seems to help with suspend.

---

### Post by mgrusin on 2006-12-29
> **Deus42 said:**
> try this:

[http://wiki.cchtml.com/index.php/Ubuntu_Edgy_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Edgy_Installation_Guide)

just ignore method one, and use method 2

Hi another noob with a t60p and Edgy which won't suspend here.

I tried the steps at the above site (though I don't know what "method 2" refers to, I only see one set of steps on that page), and the shell reports that I'm already using the newest version (listed as 8.28.8 in synaptic package manager).

Maybe I don't understand what "enable restricted repository" means?  I can edit the /etc/apt/sources.list file but it's not obvious to this noob what to change.

Thanks for any help! -MG.

---

### Post by Deus42 on 2006-12-29
Try this:

[http://ubuntuforums.org/showthread.php?t=307731](http://ubuntuforums.org/showthread.php?t=307731)

Let me know if you have problems implementing this.

---

### Post by mgrusin on 2006-12-30
Thanks for the link but I don't -think- I have powernowd running (I don't recall installing it if it's separate).  The closest thing I see in ps is gnome-power-man.  Plus when I checked, it looks like my CPU throttling is always 1.0 on both battery and AC.

I also tried the note in [https://wiki.ubuntu.com/LaptopTestingTeam/ThinkpadT60?highlight=%28fglrx%29#fglrx-sleep](https://wiki.ubuntu.com/LaptopTestingTeam/ThinkpadT60?highlight=%28fglrx%29#fglrx-sleep) that says a T60 won't sleep with accelerated graphics without changes to etc/default/acpi-support, but those changes didn't do anything for me (display goes dark, moon LED blinks and machine never comes back w/o a hard reset).

I finally found how to enable the "restricted" repository but I still don't see a fglrx version in synaptic package manager > 8.28.8.  There is an installer for 8.32.5 on ATI's site, and some sandboxed instructions at [https://wiki.ubuntu.com/BinaryDriversHowto/Sandbox?highlight=%28fglrx%29#head-fbd2d88493fe907cd76455ab62bcc234050f55f2](https://wiki.ubuntu.com/BinaryDriversHowto/Sandbox?highlight=%28fglrx%29#head-fbd2d88493fe907cd76455ab62bcc234050f55f2) but I am wary of trying to do kernel patches etc.  I REALLY wish this worked out of the box. :-| 

One odd thing is that I'm now not sure my fglrx is working, I saw the command fglrxinfo mentioned, and it shows:

Xlib:  extension "XFree86-DRI" missing on display ":1.0".
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string:  Pentium 4 (SSE2) (FireGL) (GNU_ICD)
OpenGL version string: 2.0.6011 (8.28.8)

Maybe I should have tried 6.06 instead of 6.10?  Thanks for the help! -MG.

---

### Post by mgrusin on 2006-12-30
UPDATE - I was wrong, it does look like powernowd is installed (should have checked package manager).  How do I tell it to quit before suspend?

(Also, in package manager there is another uninstalled package called "powersaved" which mentions it can be used for suspend/resume, should that be installed as well?)

Thanks for the help, -MG.

---

### Post by strawman on 2007-01-02
ok, got it working on a hp nc8000 and running edgy.  on the /boot/grub/menu.lst i took out the 
splash and quiet from the defoptions line and added vga=0x342 (i'm running 1400x1050).  using the radeon driver (open source) not fglrx as i want to get aiglx going.  and in my 
/etc/default/acpi-support file the changes for me are:

SAVE_VBE_STATE=true
VBESTATE=/var/lib/acpi-support/vbestate
POST_VIDEO=false
SAVE_VIDEO_PCI_STATE=true
USE_DPMS=true
HIBERNATE_MODE=platform

this is part of my dmesg:
[17179612.324000] ACPI: Video Device [C0CF] (multi-head: yes  rom: no  post: no)
that is why i set POST_VIDEO=false

hope this helps some people

---

### Post by Deus42 on 2007-01-03
> **mgrusin said:**
> UPDATE - I was wrong, it does look like powernowd is installed (should have checked package manager).  How do I tell it to quit before suspend?

(Also, in package manager there is another uninstalled package called "powersaved" which mentions it can be used for suspend/resume, should that be installed as well?)

Thanks for the help, -MG.

You shouldn't need to install powersaved (I don't have it installed anyway)

First, try manually stopping the process before you suspend by typing:

/etc/init.d/powernowd stop

This will turn off your frequency scaling, then suspend your thinkpad and it should work (although it takes up to 15 sec on mine).

If that works, you can stop, then start the service every time your computer suspends by following the below instructions:

in the console, edit /etc/acpi/suspend.d/10-thinkpad-standby-led.sh and add "/etc/init.d/powernowd stop" (without the quotes) to the bottom of the file. 

Next, edit /etc/acpi/resume.d/90-thinkpad-unstandby-led.sh and add "/etc/init.d/powernowd start" (without the quotes) to the bottom of the file.

---

### Post by Deus42 on 2007-01-03
> **mgrusin said:**
> Hi another noob with a t60p and Edgy which won't suspend here.

I tried the steps at the above site (though I don't know what "method 2" refers to, I only see one set of steps on that page), and the shell reports that I'm already using the newest version (listed as 8.28.8 in synaptic package manager).

Maybe I don't understand what "enable restricted repository" means?  I can edit the /etc/apt/sources.list file but it's not obvious to this noob what to change.

Thanks for any help! -MG.

Sorry it took me so long to get back to you on this. 

I wouldn't try to install the latest drivers from ati, it can be a pain, and I still had some problems even after doing it. So before you go through all the trouble, try stopping the powernowd process before suspend like I described in my above post.

---

### Post by mgrusin on 2007-01-04
> **Deus42 said:**
> 
First, try manually stopping the process before you suspend by typing:

[COLOR="Red"]sudo[/COLOR] /etc/init.d/powernowd stop

This will turn off your frequency scaling, then suspend your thinkpad and it should work (although it takes up to 15 sec on mine).

If that works, you can stop, then start the service every time your computer suspends by following the below instructions:

in the console, edit /etc/acpi/suspend.d/10-thinkpad-standby-led.sh and add "/etc/init.d/powernowd stop" (without the quotes) to the bottom of the file. 

Next, edit /etc/acpi/resume.d/90-thinkpad-unstandby-led.sh and add "/etc/init.d/powernowd start" (without the quotes) to the bottom of the file.

That worked GREAT for suspend Deus42, thank you! (I added an extra [COLOR="Red"]sudo[/COLOR] above which I needed to test this out).

Hibernate doesn't seem to be working yet (it tries for a bit then comes back to life), but at least it doesn't lock up the system like it did before, and suspend is what I really wanted working. (Without it I was hesitant to commit to Linuxizing my life).

Thanks again for your help!  Virtual beer's on me.  -Mike G.

---

### Post by Deus42 on 2007-01-04
Your welcome.

And thanks for the correction, I'll make sure I include that next time.

---

