---
title: "No Resume after Suspend on Dell Vostro 1000"
date: 2010-01-03
forum: Hardware
---

### Post by recluce on 2010-01-03
After installing 9.10 (AMD64 version) on a Dell Vostro 1000 for a friend, I found out that the system will not resume after suspend to RAM, all you get is the "Black Screen of Death", with no possibility to recover (hard power-off required). 

While I only tested the workaround on a Dell Vostro 1000, it could potentially help other laptops with ATI/Radeon graphics that exhibit the same kind of freeze after a suspend to RAM. Also, I tested the 64bit version only, reports from a German forum indicate that the solution should also work for 32bit installations.

In my search to a solution, I found this thread in the now closed x64 forum: [http://ubuntuforums.org/showthread.php?t=1307618&page=29](http://ubuntuforums.org/showthread.php?t=1307618&page=29)

Note **29 pages** of problem reports, with a sketchy solution.

Here now, step by step:

1.) Go to launchpad an download the most recent **Jaunty** driver for your ATI video card. Here is the link: [https://launchpad.net/ubuntu/+archive/primary/+sourcepub/538594/+listing-archive-extra](https://launchpad.net/ubuntu/+archive/primary/+sourcepub/538594/+listing-archive-extra)

Download the following:

_For 64bit systems:_
xserver-xorg-video-ati_6.12.1-0ubuntu2_amd64.deb
xserver-xorg-video-radeon_6.12.1-0ubuntu2_amd64.deb

_For 32bit systems:_
xserver-xorg-video-ati_6.12.1-0ubuntu2_i386.deb
xserver-xorg-video-radeon_6.12.1-0ubuntu2_i386.deb


2.) Now in your shell, type:

sudo dpkg -i --force-downgrade <xxx>/xserver-xorg-video-radeon_6.12.1-0ubuntu2_<yyy>.deb

sudo dpkg -i --force-downgrade <xxx>/xserver-xorg-video-ati_6.12.1-0ubuntu2_<yyy>.deb

**Note:** Replace "<xxx>" with the path to the folder where you stored the packages and replace "<yyy>" with "amd64" or "i386", depending on your architecture.


3.) Reboot the system and try to suspend and resume to see if the fix worked.

3a.) If it worked, you need to keep Synaptic from updating the drivers to the (broken) Karmic drivers. Do so by typing in your shell:

aptitude hold xserver-xorg-video-radeon
aptitude hold xserver-xorg-video-ati

3b.) If it did not work: Skip 3a) and startup the Update manager to replace the drivers with the current ones. This should restore your system to the point before following this little guide.

As always: before starting, clone your system partition with Clonezilla and have current backups of everything. If Murphy strikes, you want to be prepared.

No guarantees, of course, but it did work for me. You may have to move the cursor after resume for a second for the "Enter password" window to appear.

4.) Please report if this worked for you and include your laptop brand / model and if you use 32bit or 64bit.

---

### Post by powersurge360 on 2010-01-08
I think I love you. This got it working on my Vostro 1000 too! Think this would handle the 3d accelerator problems I faced in Jaunty? Probably not, seeing as how it's the same drivers, but I'll give it a try anyways and hope it'll work through some means I don't understand.

Thanks again, you're amazing.

---

### Post by recluce on 2010-01-08
> **powersurge360 said:**
> I think I love you. This got it working on my Vostro 1000 too! Think this would handle the 3d accelerator problems I faced in Jaunty? Probably not, seeing as how it's the same drivers, but I'll give it a try anyways and hope it'll work through some means I don't understand.

Thanks again, you're amazing.

Thank you for the praise! :redface:

Since you are using Jaunty drivers, you are also "importing" all issues you had under Jaunty, as long as they relate to the ATI drivers. So unfortunately, I would assume that your 3d accelerator problem will still be with you.

---

### Post by recluce on 2010-01-08
I found out that the two following commands in my guide:

aptitude hold xserver-xorg-video-radeon
aptitude hold xserver-xorg-video-ati

will not prevent Synaptic's Update Manager from offering to update to the (broken) newer packages, they only work for apt-get. In order to keep the Update Manager from causing mischief, you should rather use the following two commands:

sudo wajig hold xserver-xorg-video-radeon
sudo wajig hold xserver-xorg-video-ati

This will grey out the updates in Update Manager and prevent accidental update/breakage.

---

### Post by coffeeshawn on 2010-01-10
Many, many thanks!!  Been trying off and on for about a month to resolve this issue.

This worked on my wife's Dell Vostro 1000.  I've been trying to get her to switch to Ubuntu, and this was the only real problem encountered, and it's kind of a big deal for laptops.  We are using the amd64 version.  (Initially had the i386 version on there, and tried the amd64 version today to see if that would fix this problem.  It didn't and I decided to try yet another Google search, and this new post came up.)

I just hope that whatever the issue is, it'll be fixed in a later version so we don't have to keep using older drivers.

Again, thanks for your help.

---

### Post by wumbo on 2010-01-12
This worked on my 32 bit Presario V2000. Thank you!

---

### Post by thewooby on 2010-02-09
This also worked for me on my Compaq V2000 amd64 machine.  Thank you!

---

### Post by sensory on 2010-02-10
This worked on my HP Pavilion - thanks! It was getting frustrating not being able to suspend or hibernate.

---

### Post by sateeshpnv on 2010-02-13
Great. It solved the problem with hp Compaq nx6125 (ATI Radeon XPRESS 200M 5955) with Ubuntu Karmic.

But, the same solution did not help with Lucid alpha :-( dpkg throws the below error:

dpkg: regarding xserver-xorg-video-radeon_6.12.1-0ubuntu2_amd64.deb containing xserver-xorg-video-radeon:
 xserver-xorg-core conflicts with xserver-xorg-video-5
  xserver-xorg-video-radeon provides xserver-xorg-video-5 and is to be installed.
dpkg: error processing xserver-xorg-video-radeon_6.12.1-0ubuntu2_amd64.deb (--install):
 conflicting packages - not installing xserver-xorg-video-radeon

Is there a different solution for Lucid?

---

### Post by recluce on 2010-02-13
> **sateeshpnv said:**
> Great. It solved the problem with hp Compaq nx6125 (ATI Radeon XPRESS 200M 5955) with Ubuntu Karmic.

But, the same solution did not help with Lucid alpha :-( dpkg throws the below error:

dpkg: regarding xserver-xorg-video-radeon_6.12.1-0ubuntu2_amd64.deb containing xserver-xorg-video-radeon:
 xserver-xorg-core conflicts with xserver-xorg-video-5
  xserver-xorg-video-radeon provides xserver-xorg-video-5 and is to be installed.
dpkg: error processing xserver-xorg-video-radeon_6.12.1-0ubuntu2_amd64.deb (--install):
 conflicting packages - not installing xserver-xorg-video-radeon

Is there a different solution for Lucid?

I have no idea - don't forget that Lucid is in the **alpha** stage right now, x.org changes are loaded almost daily. Let's wait for the final release of Lucid first - and see if the problem still exists in April.

---

### Post by sateeshpnv on 2010-02-19
Starting the kernel 2.6.32-13 with "radeon.modeset=0" and using pm-suspend --quirk-radeon-off helped on Lucid.

To make it permanent, I updated /usr/lib/pm-utils/video-quirks/20-video-quirk-pm-hp.quirkdb and changed the lines under nx6125 to
   addquirk --quirk-radeon-off

I am not sure if that is the right way to do it, but that helped.

---

### Post by EamonSloane on 2010-03-05
noob question.  If I have an amd 64 processor, but am running 32 bit ubuntu, do i use the amd64 or the i386 version?

---

### Post by IanP7 on 2010-03-06
Afraid it didn't work for me! I'm running a desktop with Asus K8V-MX motherboard using the on-board AGP graphics and an AMD Sempron processor.
I have Ubuntu 9.10, Linux 2.6.31-19-generic, GNOME 2.28.1.
Dual boot system with Windows XP on primary master (sda) and Linux on primary slave (sdb).

I loaded the i386 versions.

What happens:
Machine appears to suspend after a few seconds (power light flashes).
I hit power button to restart.
Disc spins up.
Screen starts after about 30 secs - 'Black screen of death' with mouse pointer.
Does not respond to mouse (Logitech wireless on USB port). 
Alt+SysRq gives [   136.613311] end_request I/O error, dev sdb sector 282823.........

Numbers obviously vary - makes me wonder if the suspend actually completed correctly.

I've been looking for a possible solution for the last month - yours was the only one that sounded 'current' - if you can think of anything else I can try I would appreciate it. (Obviously its not a killer with a desktop machine - but it works in XP).

---

### Post by recluce on 2010-03-08
> **EamonSloane said:**
> noob question.  If I have an amd 64 processor, but am running 32 bit ubuntu, do i use the amd64 or the i386 version?

If you are running the 32bit version of Ubuntu, use the i386 files - no matter who manufactured your CPU.

---

### Post by recluce on 2010-03-08
> **IanP7 said:**
> Afraid it didn't work for me! I'm running a desktop with Asus K8V-MX motherboard using the on-board AGP graphics and an AMD Sempron processor.
I have Ubuntu 9.10, Linux 2.6.31-19-generic, GNOME 2.28.1.
Dual boot system with Windows XP on primary master (sda) and Linux on primary slave (sdb).

I loaded the i386 versions.

What happens:
Machine appears to suspend after a few seconds (power light flashes).
I hit power button to restart.
Disc spins up.
Screen starts after about 30 secs - 'Black screen of death' with mouse pointer.
Does not respond to mouse (Logitech wireless on USB port). 
Alt+SysRq gives [   136.613311] end_request I/O error, dev sdb sector 282823.........

Numbers obviously vary - makes me wonder if the suspend actually completed correctly.

I've been looking for a possible solution for the last month - yours was the only one that sounded 'current' - if you can think of anything else I can try I would appreciate it. (Obviously its not a killer with a desktop machine - but it works in XP).

It does not appear to be the same problem, if the graphics driver causes the "black screen of death", you will NOT see a mouse pointer, nor will you be able to escape into text mode.

I am hazarding a guess here, but to me it seems that the drive takes to long to spin up - Ubuntu accesses the drive while it is still "not ready", thus causing an I/O error. You could test this theory if you could swap the drive for something that spins up fast, like a notebook drive.

---

### Post by vtence on 2010-03-08
I can confirm that suspend resume works on Lucid alpha 3 on my HP Pavilion dv5000 (xpress200m 5955) using radeon.modeset=0 as a kernel parameter (it disables KMS).

With KMS active the laptop does not resume. With KMS off, it works great without modifying the quirk config. I could never make suspend/resume work under karmic on the same machine.

---

### Post by woody_green on 2010-03-09
Tried downgrading Grub but didn't work. Was too afraid to tweak the kernel. This works like a charm on my Acer Aspire 5100. Thank you vey much! Running Karmic btw. :D

---

### Post by jcalder on 2010-04-02
> I loaded the i386 versions.

What happens:
Machine appears to suspend after a few seconds (power light flashes).
I hit power button to restart.
Disc spins up.
Screen starts after about 30 secs - 'Black screen of death' with mouse pointer.
Does not respond to mouse (Logitech wireless on USB port). 
Alt+SysRq gives [   136.613311] end_request I/O error, dev sdb sector 282823.........

Numbers obviously vary - makes me wonder if the suspend actually completed correctly.

I've been looking for a possible solution for the last month - yours was the only one that sounded 'current' - if you can think of anything else I can try I would appreciate it. (Obviously its not a killer with a desktop machine - but it works in XP).I'm in the same situation.  My setup is a Dell Vostro 1000, but I recently installed a new hard drive, maybe this has something to do with it???

---

### Post by IanP7 on 2010-04-03
Hi jcalder. For what its worth I was not able to try swapping the hard drive (as suggested) so I'm just living with suspend NOT working!

---

### Post by CholericKoala on 2010-04-05
Original solution worked for me.  32-bit Compaq Presario V2000 with an ATI Xpress 200M


Thank you ^^

---

### Post by Donn on 2010-05-19
Thanks for the tips.  I was able to get my Gateway MX6447 to suspend and resume (and switch users) properly after using these tips, and adding my model number to the 20-video-quirk-pm-misc.quirkdb file.

The "Gateway" section of this file for me now looks like this:

> match system.hardware.vendor regex ^Gateway
 match system.hardware.product regex MT6707
  addquirk --quirk-s3-bios
  addquirk --quirk-s3-mode
 endmatch
 match system.hardware.product regex ^MT6920
  addquirk --quirk-vbe-post
 endmatch
 match system.hardware.product regex MX6922B
  addquirk --quirk-none
 endmatch

 match system.hardware.product regex MX6447
    addquirk --quirk-radeon-off
 endmatch
endmatch


---

### Post by GeorgeOfTheBush on 2010-05-20
For about a year, I thought the problem with my ubuntu system was Random Freezes related to a browser problem - for which NO solution existed!

My recent observations narrowed down the problem to a [COLOR=Red]**Suspend/Wakeup**[/COLOR] issue with [COLOR=Red]Ubuntu[/COLOR].

After so many months, I finally came across this thread which seems to have the solution to the problem I am facing.

My question is :
Will the solution work for laptops with [COLOR=Navy]**ATI cards ONLY**[/COLOR]? I have the following graphics card installed.

VGA compatible controller: [COLOR=Navy]**Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller**[/COLOR]

Thanks for your suggestions.

---

### Post by itkejser on 2010-06-16
Hi Everyone,

I have an IBM R40 that wasn't able to resume after suspend and disabling KMS worked perfect. Resume from hibernation also works now. This just makes my day :-).

BTW: I'm running lucid netbook edition.

Regards Troels.

---

### Post by Smart_Patrol on 2010-06-17
I have a similar problem that seems to have evolved from the "fixed"  problem on this thread.  It's a long story, as I lack some of the tech  lingo to make it shorter. (In fact, the Admin may want to fork this post into a new thread .)

I am running 10.04 on a Dell Vostro 1000, with the AMD 64 X2 chip (I  have the 64 bit version.) 

First of all, when the screen turns off after being idle, I cant get it  to turn back on.  I mean, it turns on technically, but it's still a  black screen.  Only closing the lid and thus suspending the computer can  I bring it back to the login screen.

Furthermore, the black screen of death appears whenever the screen  resolution changes, for example when I start up a game, or any program  that occupies the entire monitor.  I have not found a way to fix this  without restarting and losing my work.

Finally, the black screen appears during startup, around the time that  the purple Ubuntu screen with the loading progress dot things ought to  appear.  Again, this is fixed by closing the lid when the login screen comes up (indicated by the bongo sound), letting it hibernate  for a sec, and opening it again.  But occasionally, this results in  either the mouse pointer disappearing or networking becoming disabled.  

I submitted a bug report a while back, and was contacted by a canonical  rep, who told me that he was very surprised that I had this  problem.  He had me do a full bug report in the terminal, and went on to  say that I should test the "upstream kernel."  I have no clue what that  means, and I lack the technical vocab to even understand the Wikipedia  article on upstream kernels, let alone the instructions on how to test  one.  I wouldn't even know where to begin assembling such vocabulary.

I really want my computer to "Just Work" as  advertised, and if testing this so-called upstream kernel will facilitate killing this problem once and for all, I'd like to learn how.

---

### Post by Daug on 2010-08-31
I'm running 9.10 Karmic on an HP 6930p. I've had this issue ever since I installed (alongside XP) in late 2009. I have an "ATI Radeon HD 3400 Series" chip. I would get a black screen on resume (no cursor) every 8 times or so. I tried this solution, and thought it had worked, as I went about 15 successful resumes, until the dreaded black screen struck again. This has been the 1st time since I tried the solution, so I'm hoping it's a fluke, and the solution will still work, or at least work better with the Jaunty drivers. Also, I applied the aptitude hold commands provided, but Update Mgr still suggests the latest drivers. I guess I'll just avoid (uncheck) them at update time. Thanks for the solution, though; seems it's helped lots of us..

---

### Post by RaviPatel on 2010-10-31
Sorry to dig up an old thread, but I reckon that this solution will work for me, and I've been trying to find a solution for quite a while now, so I'm really desperate to make it work.

So I followed the instructions, but when trying to install the xserver-xorg-video-radeon_6.12.1-0ubuntu2_amd64.deb package, I get the following error.

(see attached image)

I have uninstalled the old version of xserver-xorg-video-radeon that was installed. I can't figure out what it means.

Anyone got any ideas whatsoever? Any suggestion would be great.

Thanks

---

### Post by RaviPatel on 2010-10-31
Please? Someone? Anyone? Really desperate to fix this.

---

### Post by RaviPatel on 2010-11-01
Sorry to bump again, but does anyone have any ideas at all. Pleeeease?

---

### Post by dcoston on 2011-02-14
This solution did not work for me.  I am using Ubuntu 10.10 64-bit on an Acer Aspire 1551-5448.  the graphics card is an ATI Mobility Radeon HD 4225 and CPU an AMD K625 Dual-Core.



If you have any suggestions please let me know! :)

thank you!

---

### Post by impink on 2011-06-20
I really hoped this was going to work but...
 inputting the commands I get 

Unpacking replacement xserver-xorg-video-radeon ...
dpkg: dependency problems prevent configuration of xserver-xorg-video-radeon:
 xserver-xorg-core (2:1.10.1-1ubuntu1.1) breaks xserver-xorg-video-5 and is installed.
  xserver-xorg-video-radeon (1:6.12.1-0ubuntu2) provides xserver-xorg-video-5.
dpkg: error processing xserver-xorg-video-radeon (--install):
 dependency problems - leaving unconfigured
Processing triggers for man-db ...
Errors were encountered while processing:
 xserver-xorg-video-radeon

I'm a complete noobie, I'm too scared to go on!

Any suggestions please?

---

### Post by bebopiiam on 2011-08-09
I'm having the same problem loading downgraded drivers on an MX6447 running 11.04 on the amd64.

The update manager wouldn't back out the partially installed driver reporting that the load was broken.  It instructed using 'sudo apt-get install -f' which did back out the changes.  I did put the suggested changes into 20-video-quirk-pm-misc.quirkdb and they didn't help but also didn't seem to hurt anything.

Is this a new problem for 11.04 and should I start a new thread?

Thanks for the help.

Steve S.

---

### Post by bebopiiam on 2011-08-09
Here is a little more info:
I discovered the pm-suspend.log on another thread and it says suspend worked.  The system seems to shut down correctly.  On power up it starts doing something -- the lights flicker and there is disk activity but I never get a display it doesn't return a ping.

Thanks again.

Steve S.

---

### Post by Liberator on 2011-10-09
Thanks Recluce this problem has plagued me on my Dell Vostro 1000 since I bought it 3 years ago.  I'm currently running Linux Mint 9 on it.

To clarify the issue for others:  The problem is that the display backlight would not come on during a resume.  Suspend is fine.  Resume is fine in all respects (network, etc.) except for the backlight.  Recluce's fix brings back up the backlight.  Without the backlight the display is theoretically showing an image, but you can't see it. ;)

I must have tried 5 different "fixes" until finding this one that actually works.  Many thanks!

---

