---
title: "natty: vgaswitcheroo, blacklist and modprobing!"
date: 2011-04-30
forum: Hardware
---

### Post by mexicanseaf00d on 2011-04-30
Gentlemen, I require your help to do some automation!

I recently upgraded my notebook to 11.04 (fresh install), but cannot boot 2.6.38 kernel normally (blank screens, stuck in dmesg (?) output, no gui loads).

In 10.10 I used **vgaswitcheroo** to turn the dedicated ATI card off (it didnt work anyway, loud fans and terrible heat - useless!) and ran compiz+effects nicely with the Intel Core i5 gfxchip.

Now with the update, I cant boot without adding *radeon.modeset=0* to grub, which then disables vgaswitcheroo. After some googling I found a post, where the user blacklisted the radeon driver and loaded it back in when everything booted fine.

Now my actual question:
**How can i automate this process with a script that runs on login?**

Before Natty, I configured it like this in **rc.local**:
```
chown USER /sys/kernel/debug/vgaswitcheroo/switch
echo OFF > /sys/kernel/debug/vgaswitcheroo/switch
```Now, with blacklisted *radeon* this does not exist of course. After successful booting I have to run ```
modprobe radeon
``` and then (as ROOT, not with sudo) above lines to turn the ATI card off.

My first thought was something like this:
```
#!/bin/bash
sudo su &&
modprobe radeon &&
echo OFF > /sys/kernel/debug/vgaswitcheroo/switch

```..but that does not work. I know, I should read more about scripting and bash..

Any input would be much appreciated!

---

### Post by mexicanseaf00d on 2011-04-30
I'm such a fool..

just added ```
modprobe radeon
``` to the rc.local... doh ](*,)

---

### Post by aeronutt on 2011-04-30
> **mexicanseaf00d said:**
> I'm such a fool..

just added ```
modprobe radeon
``` to the rc.local... doh ](*,)

I'm a rookie when it comes to switcheroo, etc. But have been trying to get my i3 graphics and radeon discrete to work. So far, all I've done is add 'radeon.modeset=0' to grub list, which just turns it off completely.

If you could, what does putting modprobe radeon into the rc.local do? And how do you then turn on/off the graphics cards using switcheroo after booting? Thanks in advance!

---

### Post by mexicanseaf00d on 2011-04-30
If its in rc.local, i dont have to do it 'by hand' after login everytime I turn on the pc!

Now rc.local does the work for me -> re-loads the radoen driver, then powers the ati card down.

---

### Post by willsomebody on 2011-05-07
I am confused about what exactly you put in your rc.local. Would you mind posting the exact code that you put in to control the graphics?

Thanks in advance,
will

---

### Post by mexicanseaf00d on 2011-05-07
of course,

```
#!/bin/sh -e
#
# rc.local
#
# This script is executed at the end of each multiuser runlevel.
# Make sure that the script will "exit 0" on success or any other
# value on error.
#
# In order to enable or disable this script just change the execution
# bits.
#
# By default this script does nothing.
modprobe radeon
echo OFF > /sys/kernel/debug/vgaswitcheroo/switch
# chown mart /sys/kernel/debug/vgaswitcheroo/switch #does not work since 11.04, dont know why
exit 0
```

---

### Post by willsomebody on 2011-05-07
Thanks for posting that. When I put that code in my rc.local and put radeon.modeset=0 in my grub configuration, my ati card stays on and I get an error when I run cat /sys/kernel/debug/vgaswitcheroo/switch that says there is no such file. I get the same error when I try to do echo OFF > /sys/kernel/debug/vgaswitcheroo/switch in a terminal. Running modprobe radeon from the terminal does nothing for me, either. Any ideas?

---

### Post by willsomebody on 2011-05-07
Here is my Grub setup:

```
GRUB_DEFAULT=0
GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash acpi_osi=Linux radeon.modeset=0"
GRUB_CMDLINE_LINUX=""
```

---

### Post by mexicanseaf00d on 2011-05-07
yes, nomodeset or modeset=0 disables Kernel Mode Setting, as do the proprietary drivers btw. Vgaswitcheroo (and the "switch" file) exist only with KMS on.

that was my problem too, so i left grub alone and edited```
 /etc/modprobe.d/blacklist.conf
```
put **blacklist radeon** at the end of that file --> KMS will be enabled, but the problematic radeon driver will not load initially. After that, rc.local will reload radeon, but disable the card. Voila!

The downside of this is "drm atom bios error" message which slows down logout/shutdown process a bit. As far as I can tell it does no harm to the system, but can be annoying. To fix that, one would have to turn the dedicated card on again before shutting down. There was a script somewhere on the net for that. I dont use it personally tho.

---

### Post by sauthess on 2011-05-07
Hi,

Same problem here.

Solution that you want to put in place, I think you should put this in your rc.local file :
sleep 15
rmmod radeon
modprobe radeon modeset=1
echo OFF > /sys/kernel/debug/vgaswitcheroo/switch
# chown mart /sys/kernel/debug/vgaswitcheroo/switch #does not work since 11.04, dont know why
exit 0

I've added sleep as if this script is done before X start you can have troubles (I had so ...).

Last thing : with this solution I had kernel panic as well sometimes on sleep/hibernate....(you are warned). Even when I add script in /etc/pm/sleep.d that manage to remove radeon module before suspend and reenable it after...(sometimes, with echo ON > ... there are kernel panic on my laptop...)

Only good solution I've found is to use acpi_call  ([http://linux-hybrid-graphics.blogspot.com/2010/07/using-acpicall-module-to-switch-onoff.html]("http://linux-hybrid-graphics.blogspot.com/2010/07/using-acpicall-module-to-switch-onoff.html"))

Other solution : use fglrx (as radeon is blacklisted during install) and do not use sleep/hibernate (or give a solution ;) I didn't find...)

Hope this help,

Regards,

---

### Post by mexicanseaf00d on 2011-05-07
are you sure it was a kernel panic?

AFAIK you dont need the sleep option as rc.local (or the rc scripts in general) are run quite early in the bootprocess

---

### Post by sauthess on 2011-05-07
The bug that I have is :
[https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-ati/+bug/727620](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-ati/+bug/727620)

That is a kernel panic (and seams similar with that you described). 

If not, sorry....

---

### Post by mexicanseaf00d on 2011-05-07
i see what you mean - ```
Call Trace:
 [<ffffffffa022aba0>] evergreen_cp_resume+0x3a0/0x630 [radeon]
 [<ffffffffa022c8b7>] evergreen_startup+0x157/0x260 [radeon]
```
etc etc

thats what happened when booting without any 'fixes' - out of the box, so to say. It's the reason why we needed to blacklist the radeon driver in the first place

In my previous post i meant the errors like "atom bios stuck in looop..." etc, thats not a kernel panic

---

### Post by mexicanseaf00d on 2011-05-08
> **mexicanseaf00d said:**
> of course,

```
#!/bin/sh -e
#
# rc.local
#
# This script is executed at the end of each multiuser runlevel.
# Make sure that the script will "exit 0" on success or any other
# value on error.
#
# In order to enable or disable this script just change the execution
# bits.
#
# By default this script does nothing.
modprobe radeon
chown -R $USER:$USER /sys/kernel/debug
echo OFF > /sys/kernel/debug/vgaswitcheroo/switch
exit 0
```


(edited: working chown command)

---

### Post by willsomebody on 2011-05-08
Thanks to help from this forum, I have my graphics working very well. I seldom do anything in ubuntu that requires a fancy graphics card, so I like to use the intel chip all the time. I blacklisted the radeon module and the set up rc.local to enable it and turn off the ati chip on boot.

```
#!/bin/sh -e
#
# rc.local
#
# This script is executed at the end of each multiuser runlevel.
# Make sure that the script will "exit 0" on success or any other
# value on error.
#
# In order to enable or disable this script just change the execution
# bits.
#
# By default this script does nothing.

#sleep 15
#rmmod radeon
modprobe radeon modeset=1
sleep 2
echo OFF > /sys/kernel/debug/vgaswitcheroo/switch

exit 0
```

I then set up a script to turn on the ati chip on shutdown to fix the lag problem using suggestions from the below forum.

[http://ubuntuforums.org/showthread.php?t=185261](http://ubuntuforums.org/showthread.php?t=185261)

```
#!/bin/sh 

echo ON > /sys/kernel/debug/vgaswitcheroo/switch

exit 0
```


-----------------------------------
ACER TimelineX 3820TG | Intel Core i5-480M | Ati Radeon HD 6550M | 120GB Intel Series 320 SSD

---

### Post by mexicanseaf00d on 2011-05-08
funny, i just did the same (on shutdown/logout), but i used the configs in "/etc/gdm/PostSession" etc

also, after poking around in the forum, I found that **chown -R $USER:$USER /sys/kernel/debug** works again, so you dont have to be root to switch the cards on and off.

---

### Post by aeronutt on 2011-05-08
This thread is quite helpful. I've done the following with some luck:

Change /etc/default/grub back to original settings (eg removed radeon.modeset=0)

Added to  /etc/modprobe.d/blacklist.conf:
'blacklist radeon' 


Added  to /etc/rc.local:
'modprobe radeon
'echo OFF > /sys/kernel/debug/vgaswitcheroo/switch


And, full charged battery life went from 3 hours to 4:45 !!

However, I'm pretty sure the 
'echo OFF > /sys/kernel/debug/vgaswitcheroo/switch'
line in rc.local isn't doing anything.

---

### Post by aeronutt on 2011-05-08
> **mexicanseaf00d said:**
> funny, i just did the same (on shutdown/logout), but i used the configs in "/etc/gdm/PostSession" etc

also, after poking around in the forum, I found that **chown -R $USER:$USER /sys/kernel/debug** works again, so you dont have to be root to switch the cards on and off.

A few questions.
1) Are there any security issues with change that directory tree to user ownership? And, the Ubuntu hybridgraphics web site ([https://help.ubuntu.com/community/HybridGraphics](https://help.ubuntu.com/community/HybridGraphics)) says do this in rc.local (rather than 'user'): 
chown root : plugdev /sys/kernel/debug/vgaswitcheroo/switch
Is one better than the other?

2) And is this the right order for rc.local?

   modprobe radeon
   echo OFF > /sys/kernel/debug/vgaswitcheroo/switch
   chown -R $USER:$USER /sys/kernel/debug


Seems the echo command should be executed after the chown command?

---

### Post by mexicanseaf00d on 2011-05-09
I am not an expert, but I believe that owning the debug part does no obvious harm - root still overrules the user I think.

yes, I put the 'chown' line in the wrong place

---

### Post by aeronutt on 2011-05-09
Thanks. Setting owner to root : plugdev didn't work anyway, I couldn't see the debug/vgaswitcheroo/switch file using that. So I'm setting to user:user.

FYI, this doesn't completely work for me anyway. The good news is, I can turn off my discrete AMD radeon graphics card, increasing battery life by 2x. The bad news is, I can't switch to the AMD card, only the integrated card works. After running the switcheroo commands to switch to discrete, when I try to restart X, it hangs.

---

### Post by mexicanseaf00d on 2011-05-09
You used the scripts posted on hybridgraphics?

I just tried switching manually and it worked (to my surprise, even compositing with radeon worked)

Switching without the scripts is a bit uncomfortable:

- go to virtual console (ctrl+alt+f1)
- sudo service gdm stop (stops gnome)
- echo ON > etc.. -- both cards are ON
- I tried switching immediatly (with IGD or DIS options) - sometimes it fails with the message "client * refused to switch", then either do it again or used DIGD or DDIS (delayed switch)
- sudo service gdm start (restart gnome + X)

---

### Post by aeronutt on 2011-05-09
> **mexicanseaf00d said:**
> You used the scripts posted on hybridgraphics?

I just tried switching manually and it worked (to my surprise, even compositing with radeon worked)

Switching without the scripts is a bit uncomfortable:

- go to virtual console (ctrl+alt+f1)
- sudo service gdm stop (stops gnome)
- echo ON > etc.. -- both cards are ON
- I tried switching immediatly (with IGD or DIS options) - sometimes it fails with the message "client * refused to switch", then either do it again or used DIGD or DDIS (delayed switch)
- sudo service gdm start (restart gnome + X)

Thanks, no, I haven't tried with using the scripts. I'll check those out. Again, thanks for your help, I've spent far too much time searching and posting questions trying to figure all this out, and most of what I've needed is now here in this thread! Excellent.

---

### Post by mexicanseaf00d on 2011-05-09
cool :D

---

### Post by aeronutt on 2011-05-09
None of those scripts work for me. It either hangs, or simply reverts back to the Intel integrated graphics card. Oh well.  Here's to hoping the AMD fglrx driver works will all this sometime in the next few releases.

Which discrete graphics card do you have? I have AMD Radeon HD 6630M

---

### Post by mexicanseaf00d on 2011-05-10
I'm sure that it will work someday, it always does
Its a Mobility Radeon 5650 (redwood it says in lshw)

---

### Post by nosushi4you on 2011-05-11
I too have a Mobility Radeon 5650.

The blacklisting method is working perfectly for me, but I would like to fix the shutdown issue if at all possible. How exactly would I go about doing this? Currently, shutdown takes a solid twenty seconds.

---

### Post by willsomebody on 2011-05-11
I fixed the shutdown issue by making a script that turns the ati chip back on and making it run on shutdown and reboot. 

I got help from the following thread:

[http://ubuntuforums.org/showthread.php?t=185261](http://ubuntuforums.org/showthread.php?t=185261)


Use the following steps to fix the shutdown lag with radeon blacklisted:

From terminal run

```
sudo gedit /etc/init.d/DisOn
```

Put the following text into that file:

```
#!/bin/sh 

echo ON > /sys/kernel/debug/vgaswitcheroo/switch

exit 0
```

Save and exit.

Back in the terminal, do

```

sudo chmod +x /etc/init.d/DisOn 
sudo ln -s /etc/init.d/DisOn /etc/rc0.d/K10DisOn
sudo ln -s /etc/init.d/DisOn /etc/rc6.d/K10DisOn

```

Now shutdown and reboot should be much faster. The splash screen doesn't work on shutdown for me, but it is done very quickly, so I don't really care about that.

Hope that helps.

---

### Post by mexicanseaf00d on 2011-05-12
I use a different method, via gdm configs (i use gnome), inserted the echo ON command in

/etc/gdm/PostSession/Default

and echo OFF in
/etc/gdm/PostLogin/Default
(if you log out and back in for example)

willsomebody's method looks more elegant

---

### Post by Djhg2000 on 2011-05-31
> **aeronutt said:**
> 1) Are there any security issues with change that directory tree to user ownership? And, the Ubuntu hybridgraphics web site ([https://help.ubuntu.com/community/HybridGraphics](https://help.ubuntu.com/community/HybridGraphics)) says do this in rc.local (rather than 'user'): 
chown root : plugdev /sys/kernel/debug/vgaswitcheroo/switch
Is one better than the other?

Yes there is; suddenly any member of the group "user" can access all of the kernel debug features exposed through debugfs. This would be strongly discouraged in the Debian world as regular users could potentially exploit the debugfs interface as in the past to gain root access (like the [_2.6.33 ACPI exploit_]("http://www.securityfocus.com/bid/45408/exploit")).

The suggested line should be a lot more safe, but I don't see why we would want to change the permissions at all if the "OFF" command is issued as user root.

---

### Post by mexicanseaf00d on 2011-06-01
> **Djhg2000 said:**
> Yes there is; suddenly any member of the group "user" can access all of the kernel debug features exposed through debugfs. This would be strongly discouraged in the Debian world as regular users could potentially exploit the debugfs interface as in the past to gain root access (like the [_2.6.33 ACPI exploit_]("http://www.securityfocus.com/bid/45408/exploit")).

The suggested line should be a lot more safe, but I don't see why we would want to change the permissions at all if the "OFF" command is issued as user root.


Would that work over the net? I'm the only user on this machine, so I dont worry much about that, except if there was any malware around that would exploit that.

edit: should've read your link first... doh

---

### Post by Djhg2000 on 2011-06-01
> **mexicanseaf00d said:**
> Would that work over the net? I'm the only user on this machine, so I dont worry much about that, except if there was any malware around that would exploit that.

edit: should've read your link first... doh

From the short notes in the code I think you *might* be able to set it up remotely, but you'd need either physical access to trigger the ACPI event or a lot of patience for the user to unknowingly trigger it.

Since the sample code uses the LID device to trigger the exploit you would probably also loose your remote session as well since the default behavior in GNOME is to sleep on lid close, assuming your computer has a lid in the first place. On top of that, the sample code uses a 64-bit payload. This means it's supposedly useless on anything but 64-bit laptops with kernel 2.6.33 to 2.6.37-rc2.

In short; I don't think it would be remotely exploitable with most configurations, but the point is that this is just one of many exploits. Recursively making debugfs world-writable is still not a good idea.

---

### Post by mexicanseaf00d on 2011-06-02
What procedure would you suggest?
If I don't chown the path to my user, I am unable to view or change the vgaswitcheroo path, except with ```
sudo su
```. While it should work that way with shutdown/startup switching, I'd be interested in having more control/information.

Older method with root:plugdev permissions does not work anymore (group not recognized?)

Anyway, thanks for the warnings

---

### Post by Djhg2000 on 2011-06-03
> **mexicanseaf00d said:**
> What procedure would you suggest?
If I don't chown the path to my user, I am unable to view or change the vgaswitcheroo path, except with ```
sudo su
```. While it should work that way with shutdown/startup switching, I'd be interested in having more control/information.

Older method with root:plugdev permissions does not work anymore (group not recognized?)

Anyway, thanks for the warnings

Actually, I'm fine with only having access as root, since then there's a minimal risk of a glitch giving malicious code root access through vgaswitcheroo.

But if you absolutely must have access to it as yourself then maybe you should consider root:vgaswitcheroo as owner and then make yourself a member of that group. After next login you should find that you have write access to /sys/kernel/debug/vgaswitcheroo/switch. I think this makes more sense than plugdev since it's a very unique kind of device.

Thank you for taking time to understand the issue.

---

### Post by mexicanseaf00d on 2011-06-04
I'll try that!
Would have never thought of creating an extra group, thx

---

### Post by emzc on 2011-06-05
Hello all, I'm new to this forum,
And thank you, I've had a hard time going from 10.10 to 11.04 because of the switchable graphics in my hp envy 13 (intel+ati HD4330). Working fine now with your help. But there is a problem left : when choosing shutdown, blank screen and shutting down quickly : that's ok for me. Before, I had a message saying "i915 shutdown", and the screen start to flicker until actual shutdown. But I still have this message when I reboot (until actual reboot), and when I log off (message + perpetual flickering of the screen without going to log on screen). Do you have any clue on a way for preventing this i915 shutdown (knowing I applied [willsomebody]("http://ubuntuforums.org/member.php?u=187704") code ([http://ubuntuforums.org/showpost.php?p=10803370&postcount=27](http://ubuntuforums.org/showpost.php?p=10803370&postcount=27)) which is working great, but only on shutdown ?
Regards,
Emmanuel.

---

### Post by emzc on 2011-06-05
I should add that after several shutdown and restart, even with shutdown the problem is the same : "i915 shutdown" and flickering screen.

---

### Post by emzc on 2011-06-07
Still searching for the script switching off i915 on shutdown : it wasn't present on 10.10 latest kernel, and is still not present when I boot on this 10.10 kernel (2.6.35), but is present when I boot on 11.04 kernel ( 2.6.38 ). If any of you have a clue....

edit : avoid automatic smiley

---

### Post by emzc on 2011-06-15
I may add that the exact message is "i915 switched off" : so the problem is with switcheroo, but I can't find the script causing this. It works perfectly when i boot in 10.10.

---

### Post by ultimatebuster on 2011-06-18
Any idea how to check if ATI card is in fact turned off other than a 50C sensor reading at rest 

Bonus: WTF is this reading? (lm-sensors)

```
radeon-pci-0100
Adapter: PCI adapter
temp1:      +2147355.6°C 
```

---

### Post by mexicanseaf00d on 2011-06-19
```
cat /sys/kernel/debug/vgaswitcheroo/switch
```

depending on your settings, you might have to do this as root

mine would be:
```
0:DIS: :Off:0000:01:00.0
1:IGD:+:Pwr:0000:00:02.0
```

I cant use LM-sensors, but for approximate readings i use
```
acpi -t
```

---

### Post by ultimatebuster on 2011-06-24
Anyone solved the shutdown issue? 

I can't shutdown or reboot without hard resetting.

---

### Post by vedovatti on 2011-07-08
Do what is on the comment #27. It really worked for me.

By the way I tried the last driver 11.6 Catalyst ATI, and it supports switchable graphics (ATI/INTEL) and hibernation, suspend, resume, log-out, etc. worked really well, perfect to be honest. But it was too good to be true. When switching between cards, it doesn't change the xorg configuration so keeps the ATI configuration when you switch to Intel graphics so doesn't work the 3D acceleration (Unity, compiz, etc. neither). Beside, when you use the ATI graphics the flash video in full-screen doesn't work and changing resolution of the screen freezes the system. They are bug reported so let hope on the next version of the driver will be solved.

Anyway, just to let you know. If anyone has been able to configure a script to switch between card would be nice if you let me know because I have been trying without any success.

---

### Post by AION2009 on 2011-07-10
Hey!

I have been hassling around with Linux for a while and now I have a laptop with 2 GPU:s.

One is Radeon HD4200 and another is something like Radeon HD5430

I can't seem to find /sys/kernel/debug/switcheroo/ folder

And if it happened to create itself by some miracle would I be able to use AMD Catalyst drivers with these cards?

running Ubuntu 11.04 64bit

---

### Post by willsomebody on 2011-07-11
> **AION2009 said:**
> Hey!

I have been hassling around with Linux for a while and now I have a laptop with 2 GPU:s.

One is Radeon HD4200 and another is something like Radeon HD5430

I can't seem to find /sys/kernel/debug/switcheroo/ folder

And if it happened to create itself by some miracle would I be able to use AMD Catalyst drivers with these cards?

running Ubuntu 11.04 64bit

As far as I know, everybody else here has an ati/intel setup. If you look at the post before yours, it looks like the latest ati drivers might do the trick. His problems with them seemed to be his intel card. I don't think you would need any of the vgaswitcheroo stuff for the ati driver method, but I could be wrong. If you have not tried this already, find the additional drivers utility in the system settings and see if it gives you the option to install the proprietary ati drivers. If not, you can try to do it from the command line:```
sudo apt-get install fglrx
```If that makes things worse, to undo it do: ```
sudo apt-get remove fglrx
```Please post back how that works for you. Good luck!

---

### Post by mexicanseaf00d on 2011-07-11
AFAIK switching via vgaswitcheroo is not possible with fglrx. But at least they are working on a fix like **vedovatti** posted above.


Another thing: the init.d scripts for switching ON at reboot/shutdown stopped working - was there some update?

---

### Post by vedovatti on 2011-07-11
Hi I think it could be a bug. Vgaswitcheroo should be there and it supports switchable graphics (ATI/ATI) or (ATI/INTEL). Take a look to the blog: [http://asusm51ta-with-linux.blogspot.com/](http://asusm51ta-with-linux.blogspot.com/). He describes the process in Ubuntu 10.10 to switch cards ATI integrated / ATI dedicated. I have looked another forums that on their configuration, even with ATI/Intel, for some systems are missing vgaswitcheroo. So... it used to work better on Ubuntu 10.10. I would downgrade my system but I really like Unity. Try the latest Catalyst 11.6 from the AMD website. Maybe it is better supported ATI/ATI than ATI/Intel.

@AION2009
If you try the driver AMD with the ATI/ATI switchable it would be nice if you could give a feedback.

@mexicanseaf00d
I activated on the repositories the "Pre-released updates (natty proposed)" on the update manager and it installed new kernel version (2.6.38-10). I noticed (or maybe a bit paranoid) that the rc.local script doesn’t work anymore so I went back to use the 2.6.38-8 and unchecked the pre-released updates.

---

### Post by AION2009 on 2011-07-11
Hey!

I installed newest Catalyst (11.6) from AMD's site.
Now I have a new page in CCC which enables me to change graphics card.

Only two bad things, it requires reboot and it does not work.

Every time I reboot it has gone back to low-power one.

And I tried both, normal and adminstrative CCC.
No vgaswitcheroo still.

---

### Post by AION2009 on 2011-07-11
This is getting kind of interesting:

```

sopsaare@hp:~$ aticonfig --pxl
PowerXpress: Discrete GPU is active (High-Performance mode).
sopsaare@hp:~$ aticonfig --lsa
* 0. 00:00.0 ATI Mobility Radeon HD 5400 Series
  1. 00:01.0 ATI Mobility Radeon HD 5400 Series
  2. 00:03.0 ATI Mobility Radeon HD 5400 Series
  3. 00:04.0 ATI Mobility Radeon HD 5400 Series
  4. 00:05.0 ATI Mobility Radeon HD 5400 Series
  5. 00:11.0 ATI Mobility Radeon HD 5400 Series
  6. 00:12.0 ATI Mobility Radeon HD 5400 Series
  7. 00:13.0 ATI Mobility Radeon HD 5400 Series
  8. 00:14.0 ATI Mobility Radeon HD 5400 Series
  9. 00:18.0 ATI Mobility Radeon HD 5400 Series
 10. 01:05.0 ATI Mobility Radeon HD 5400 Series
 11. 02:00.0 ATI Mobility Radeon HD 5400 Series

* - Default adapter
sopsaare@hp:~$ sudo aticonfig --px-igpu
PowerXpress: Integrated GPU is selected (Power-Saving mode), please restart Xserver(s) for changes to take effect!


```


And I'm going to continue after restart :P

---

### Post by AION2009 on 2011-07-11
```
sopsaare@hp:~$ aticonfig --lsa
* 0. 00:00.0 ATI Mobility Radeon HD 5400 Series
  1. 00:01.0 ATI Mobility Radeon HD 5400 Series
  2. 00:03.0 ATI Mobility Radeon HD 5400 Series
  3. 00:04.0 ATI Mobility Radeon HD 5400 Series
  4. 00:05.0 ATI Mobility Radeon HD 5400 Series
  5. 00:11.0 ATI Mobility Radeon HD 5400 Series
  6. 00:12.0 ATI Mobility Radeon HD 5400 Series
  7. 00:13.0 ATI Mobility Radeon HD 5400 Series
  8. 00:14.0 ATI Mobility Radeon HD 5400 Series
  9. 00:18.0 ATI Mobility Radeon HD 5400 Series
 10. 01:05.0 ATI Mobility Radeon HD 5400 Series
 11. 02:00.0 ATI Mobility Radeon HD 5400 Series

* - Default adapter
sopsaare@hp:~$ aticonfig --pxl
PowerXpress: Integrated GPU is active (Power-Saving mode).
sopsaare@hp:~$ 

```

So what to make of this?
Only where it ever actually says that I'm running HD4200 is in the graphical control panel, it always says that there :D

And more:
```
sopsaare@hp:~$ lspci |grep VGA
01:05.0 VGA compatible controller: ATI Technologies Inc M880G [Mobility Radeon HD 4200]
02:00.0 VGA compatible controller: ATI Technologies Inc Manhattan [Mobility Radeon HD 5430 Series] (rev ff)
sopsaare@hp:~$ 

```

What utility would actually tell me which card is really running?

And to answear my own question: fglrxinfo :
```

sopsaare@hp:~$ fglrxinfo 
display: :0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: ATI Mobility Radeon HD 4200 Series
OpenGL version string: 3.3.10834 Compatibility Profile Context

sopsaare@hp:~$ aticonfig --pxl
PowerXpress: Integrated GPU is active (Power-Saving mode).
sopsaare@hp:~$ 

```

And to confirm that nothing really works:

```

sopsaare@hp:~$ fglrxinfo 
display: :0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: ATI Mobility Radeon HD 4200 Series
OpenGL version string: 3.3.10834 Compatibility Profile Context

sopsaare@hp:~$ aticonfig --pxl
PowerXpress: Discrete GPU is active (High-Performance mode).
sopsaare@hp:~$ aticonfig --list-adapters
* 0. 00:00.0 ATI Mobility Radeon HD 5400 Series
  1. 00:01.0 ATI Mobility Radeon HD 5400 Series
  2. 00:03.0 ATI Mobility Radeon HD 5400 Series
  3. 00:04.0 ATI Mobility Radeon HD 5400 Series
  4. 00:05.0 ATI Mobility Radeon HD 5400 Series
  5. 00:11.0 ATI Mobility Radeon HD 5400 Series
  6. 00:12.0 ATI Mobility Radeon HD 5400 Series
  7. 00:13.0 ATI Mobility Radeon HD 5400 Series
  8. 00:14.0 ATI Mobility Radeon HD 5400 Series
  9. 00:18.0 ATI Mobility Radeon HD 5400 Series
 10. 01:05.0 ATI Mobility Radeon HD 5400 Series
 11. 02:00.0 ATI Mobility Radeon HD 5400 Series

* - Default adapter
sopsaare@hp:~$ 

```


So aticonfig thinks that I have like 10 HD5400 cards in my latptop. It also gives me option to change between IGP and DGP and thinks that it makes some difference.

While fglrx shows that everytime I have HD4200.

(also I fear that the HD5430 is powered all the time)

---

### Post by AION2009 on 2011-07-11
Any ideas on how to continue?

---

### Post by willsomebody on 2011-07-11
@mexicanseaf00d
I have all updates installed (only one proposed, though) and mine still works. Are you using vgaswitcheroo or acpi call?

@AION2009
I poked around a little on the internet and found a site that I had been to before. It mentions using the ati driver for login/logout switching. Have you tried logging out and back in after changing your card without restarting?

[http://linux-hybrid-graphics.blogspot.com/2010/07/using-acpicall-module-to-switch-onoff.html]("http://linux-hybrid-graphics.blogspot.com/2010/07/using-acpicall-module-to-switch-onoff.html")

---

### Post by vedovatti on 2011-07-12
@AION2009

I think is really working for you.

The vgaswitcheroo just works with the open-source drivers. Once you install property drivers even if you have it installed it won't work at all. Vgaswitcheroo is just for open-source driver.

About the 11.6 Catalyst I think it works. The fact that restarts the whole system is normal. And with the command: aticonfig --pxl it shows two different cards active. Is a pity that cannot change without rebooting but maybe in future. So when you switch cards the CCC Catalyst should show on the graphic info, the card that is activated. Try to change and see the card that shows activated. And if you switch card restart and the CCC shows a different card than before and Unity works or compiz or 3D features, then congratulations you got it. About the fact that shows 10 cards, don't worry who knows what is doing that but as long as it doesn't affect the performance just ignore it. The Catalyst detects two cards and that’s what is important. I really have to accept that AMD at least is doing efforts supporting this feature in Linux.

---

### Post by AION2009 on 2011-07-12
I'm quit certain that it is not working. No matter what aticonfig --pxl shows, I get 250fps from fgl_gears (or what ever those gears were named)

So the card ain't changing. And besides it does not have any matter on battery performance either, so I'm concluding that it does not work. 

Also fglrxinfo shows (and Catalyst Control Panel) show always the HD4200. 


I have tries rebooting, logging out, restarting X with commands and ctrl + alt + backspace.

Edit: It does not modify xorg.conf to be precise. Though it has written there something, infact a line, which makes it use the integrated HD4200

```


sopsaare@hp:~$ lspci |grep ati
00:18.0 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor HyperTransport Configuration
01:05.0 VGA compatible controller: ATI Technologies Inc M880G [Mobility Radeon HD 4200]
02:00.0 VGA compatible controller: ATI Technologies Inc Manhattan [Mobility Radeon HD 5430 Series] (rev ff)
04:00.0 Network controller: Broadcom Corporation BCM4313 802.11b/g/n Wireless LAN Controller (rev 01)
sopsaare@hp:~$ cat /etc/X11/xorg.conf |grep BusID
	BusID       "PCI:1:5:0"
sopsaare@hp:~$ aticonfig --pxl
PowerXpress: Discrete GPU is active (High-Performance mode).
sopsaare@hp:~$ fglrxinfo 
display: :0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: ATI Mobility Radeon HD 4200 Series
OpenGL version string: 3.3.10834 Compatibility Profile Context

sopsaare@hp:~$


```

If I just change the bus id in the xorg.conf X want start, so what to do?

```



sopsaare@hp:~$ lspci |grep ati
00:18.0 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor HyperTransport Configuration
01:05.0 VGA compatible controller: ATI Technologies Inc M880G [Mobility Radeon HD 4200]
02:00.0 VGA compatible controller: ATI Technologies Inc Manhattan [Mobility Radeon HD 5430 Series] (rev ff)
04:00.0 Network controller: Broadcom Corporation BCM4313 802.11b/g/n Wireless LAN Controller (rev 01)
sopsaare@hp:~$ cat /etc/X11/xorg.conf |grep BusID
	BusID       "PCI:1:5:0"
sopsaare@hp:~$ aticonfig --pxl
PowerXpress: Integrated GPU is active (Power-Saving mode).
sopsaare@hp:~$ fglrxinfo 
display: :0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: ATI Mobility Radeon HD 4200 Series
OpenGL version string: 3.3.10834 Compatibility Profile Context

sopsaare@hp:~$ 

```

So it does not change anything else than the aticonfig --pxl value. 
How can I "trace" what the aticonfig really does when I change GPU?

---

### Post by AION2009 on 2011-07-12
I also seem to be having Xorg logs of failed tries to use HD5400 as primary?

When ever I start the computer it will flick the screen couple of times before getting X up.

But when I use aticonfig --px-whatever and restart X for example with ctrl + als + backspace it gets up instantly and does not even try to use HD5400 what ever I do :(

---

### Post by Saranya123 on 2011-07-12
Hi,
Am newbie to this website.. Fantastic idea sharing with us.. Thanks for sharing this solution..

---

### Post by vedovatti on 2011-07-12
I think you could be right. It just change the name but on the renderer string is the same card.

Take a look to this [http://ati.cchtml.com/show_bug.cgi?id=198](http://ati.cchtml.com/show_bug.cgi?id=198)

Seems like your problem. Maybe is the same xorg configuration problem when switching between cards it doesn't modify the xorg.conf so keeps the default one.

---

### Post by AION2009 on 2011-07-12
vedovatti:

That bug is exactly same as my case. 
Running HP dm3-2130so.

---

### Post by mexicanseaf00d on 2011-07-12
> **willsomebody said:**
> @mexicanseaf00d
I have all updates installed (only one proposed, though) and mine still works. Are you using vgaswitcheroo or acpi call?


It was just a typo in the script, still works (vgaswitcheroo)


I also want to add:

Before I gave up on my dedicated gfx card, I tried to write my own (sort of) xorg.conf which I thought would help to lift the confused fglrx driver to find a display after reboot (the black screen, 'no screens found' and similar errors).

First I booted with defaults, meaning both radeon and intel kernel modules loaded, the intel one by default the active card (the notebook seems to always boot from the integrated one, until the drivers tell it to hand over to the dedicated). Switching to tty1 and stopping xorg (*sudo service gdm stop*), then:
```
sudo su
Xorg -configure
```
This got me a 'clean' xorg.conf to work with. My plan was to install the fglrx driver and tell it EXACTLY what to do with displays etc, instead of letting it autoconfigure. This xorg.conf contained entries for both cards with their PCI ID's, which I wanted to route to the proper display entries (I assumed that there was confusion because of 'no screens found' error), but I obvously failed as you can see from this thread.

Maybe it would work better for you ATI/ATI guys?

However, I'm quite happy with the gfxchip on the i5 cpu, thank god that it works pretty good & cool!

---

### Post by j0hny on 2011-07-15
Hi guys, 
thanks a lot for all the info in this thread, very useful. After editing rc.local to switch off my ATI HD6600M right after boot I would like to do something like that automatically after suspend/hibernate. I tried to google a bit and added the "switch-off" command (echo OFF > ...) to some scripts in /usr/lib/pm-utils/sleep.d/ and /etc/pm/sleep.d/ but with no success. Does anyone use something like that or have any idea how to turn the dedicated card off after suspend/hibernate?

Once again, thanks for the help :)

---

### Post by willsomebody on 2011-07-15
@j0hny

Are you sure you need to do it on resume from suspend? I believe mine stays off when I suspend. Hibernate doesn't work at all for me, so I can't say about that.

---

### Post by j0hny on 2011-07-16
@willsomebody

Well, when I type *lshw -C video* after boot it shows only the integrated GPU, but if I do that after resume from suspend there is also the ATI card so from that I suppose it is turned on - correct me if I'm wrong.

And hibernation is now working for me too - I've made too small partition for swap (fixing that right after suspend is working :)).

---

### Post by vedovatti on 2011-07-16
I really think is not necessary to change anything in suspend or hibernate. I tried and is ok.
Try to run in a terminal: ```
sudo cat /sys/kernel/debug/vgaswitcheroo/switch
```
You should get something similar to this:
> 0:DIS: :Off:0000:01:00.0
1:IGD:+:Pwr:0000:00:02.0
The plus "+:Pwr" indicate that the IGD (Integrated Graphic) is powered and the DIS (discrete) is off. I just tried to run the same command  after suspending and hibernating and got the same result. Try it on yours and it should be the same. And with the command ```
lshw -C video
``` I got the same result. Try the other command: sudo cat.. and see what happens.

---

### Post by j0hny on 2011-07-16
@vedovatti

Thanks for the tip, it works, you're absolutely right :)

---

### Post by egandt on 2011-09-21
My problem stems from my HP DV6QE which has the Intel and an AMD 6770M switchable graphics adapter and no way to disable the Intel in favor of the ATI.


First both cards exist and are seen by the OS:
	root@HPDV6QE:~# lspci | grep VGA
	00:02.0 VGA compatible controller: Intel Corporation 2nd Generation Core Processor Family Integrated Graphics Controller (rev 09)
	01:00.0 VGA compatible controller: ATI Technologies Inc Device 6740

After installing Ubuntu 11.04 I have no /sys/kernel/debug/vgaswitcheroo/switch present on the system
	root@HPDV6QE:~# ls /sys/kernel/debug/
	bdi        extfrag  ieee80211  pktcdvd         tracing         x86
	bluetooth  gpio     kprobes    regulator       usb
	dri        hid      mce        sched_features  wakeup_sources

I thus removed the fglrx driver and reinstalled them as recommended in post 44 of this thread.   Then reinstalled it, and rebooted.  

Upon reboot I went to use the Control Panel, but it does not exist in the UI and under "Aditional Drivers" ATI is not installed.  So I activated it and now I have Control Panel, but it still says I have no ATI card, even after rebooting.  Yet if I go to the command line and run 'aticonfig --list adpaters' it shows 1 adapter: " * 0. 01:00.0 AMD RADEON HD 6770M Series". 

Next I quite X: service gdm stop 

Then I try to configure the card:

root@HPDV6QE:~# aticonfig --initial
Found fglrx primary device section
Fail to link to fglrx-libglx.so, please check whether driver is installed correctly
Using /etc/X11/xorg.conf
Saving back-up to /etc/X11/xorg.conf.fglrx-0

So that is not good.  Ok so it does not seem to like fglrx-libglx.so, hum let find it:
root@HPDV6QE:~# find / -name fglrx-libglx.so
root@HPDV6QE:~#  

Well it was not even installed, at this point I'm pissed off, so let remove all Ubuntu installed drivers and install ATI manually.  Luckily I backup up xorg.conf as aticonfig it broke it in the process, sad how this happens all the time with X.  

So now lets manually install ATI's driver from there website.  Oddly to do so I need to install from a Xterm as from the console crashes (don't ask I have no idea), but from an xterm I get:

```

Do you want to proceed with Recommended installation? [Y/n] 
 Preprocessing Install Requirements
Installing Install Requirements ...
 100% - //usr/share/doc/ati/LICENSE.TXT
 Copying uninstall files for Install Requirements
 Preprocessing Display and OpenGL Drivers
Installing Display and OpenGL Drivers ...
......
 Postprocessing Display and OpenGL Drivers
 Copying uninstall files for Display and OpenGL Drivers
 Preprocessing Kernel Module
Installing Kernel Module ...
......
 Postprocessing Kernel Module
 Copying uninstall files for Kernel Module
 Preprocessing Catalyst Control Center
Installing Catalyst Control Center ...
.....
 Postprocessing Catalyst Control Center
 Copying uninstall files for Catalyst Control Center
 100% - //usr/share/ati/LICENSE.TXT

Installation complete.
For further configuration of the driver, please run aticonfig from a terminal window or AMD CCC:LE from the Desktop Manager Menu.
System must be rebooted to avoid system instability and potential data loss.
See /usr/share/ati/fglrx-install.log for installation details.
Removing temporary directory: fglrx-install.2ur1aO

```


Then I reboot, now as I have not touch aticonfig we are still using the old drivers and running amdccle says no card was detected, so I exit X again and try again to run aticonfig --initial, which say "aticonfig: No supported adapters detected".

Well that sucks!, luckly lspci | grep VGA says it still exists, so its a driver issue.


So the moral is with my notebook an HP DT6QE-6100 I have no functional ATI card or Intel card and am stuck with a slide show for X as I'm running the very old SGVA driver.  Anyone have any idea what can be done, as otherwise I'm using my 30 day return on this device as it server no use if I can not use it under Linux.

Thanks,
ERIC

---

### Post by Antarell on 2011-10-02
I don't know about the DV6-61xx series but I have the DV6-60xx and I found 11.04 to be a PITA (black screens etc) but 11.10 works brilliantly. The trick is you have to pretend the ATI card isn't there. As ATI sold these as an OEM part they are being very un-helpful in supporting them.

[Here is what I have done]("http://help.stedman.net.au/2011/10/xubuntu-1110-on-hp-dv6-6023tx.html") to get a usable *Ubuntu working (I am using Xubuntu atm but might switch back to Ubuntu this arvo). The only issue I have at the moment is an update killed my backlight keys, but it seems to a known issue.

[edit: The Radeon now works! ]("http://help.stedman.net.au/2012/02/more-xubuntu-1110-on-hp-dv6-6023tx.html")

---

### Post by pedram.mehrdad on 2011-10-07
> **mexicanseaf00d said:**
> I'm such a fool..

just added ```
modprobe radeon
``` to the rc.local... doh ](*,)
Thanks a lot.you really really really saved my ***!!

---

### Post by kahwedyich on 2011-10-16
Well 11.10 is out, and this solution no longer works on my HP g62-a50sm (hybrid Intel/ATI graphic).

Any thoughts on how to fix it?

---

### Post by mexicanseaf00d on 2011-10-16
In the short time that I checked out 11.10, it appeared to work even without having to blacklist the driver (meaning, just "echo OFF" etc.). Apart from that, this release is horrible.

Got any error messages in the usual logs?

---

### Post by kahwedyich on 2011-10-16
Thanks for the quick reply :)

Actually, heres' the deal: I used this whole blacklisting-modprobing shabang because I was getting the black screen in 11.04 (more accurately, the display backlight wouldn't turn on)

Now I have the same black-screen issue, but this solution no longer works, and I'm stuck using "nomodeset"

---

### Post by mexicanseaf00d on 2011-10-16
As I wrote above, a clean install with the kernel 3.x did not bother me with blackscreens or the annoying atombios bug.



Have you upgraded or did you do a fresh install? Maybe try out a LiveCD/USB and see how it boots (maybe shutdown/start a couple of times).

Apart from the 'hacks' gathered in this thread I don't know much, but hopefully someone else will join in and help.

---

### Post by kahwedyich on 2011-10-16
Yeah, I hope so.

Here is what I did:

First, I (foolishly) upgraded via update manager. 
Well, that went down badly, so I download the image and do a clean install - still no good.

Even with the LiveCD I have to use nomodeset. :S

---

### Post by mexicanseaf00d on 2011-10-16
Meanwhile, browse through the phoronix-forums - [http://www.phoronix.com/forums/](http://www.phoronix.com/forums/)

---

### Post by bleedlinux on 2012-03-29
> **mexicanseaf00d said:**
> I'm such a fool..

just added ```
modprobe radeon
``` to the rc.local... doh ](*,)




this comment saved my laptop!!!! . awesme work !!!! thanks!!:guitar:

---

### Post by andrikos on 2012-04-23
My solution in order to have the Discrete ATI graphics always Off and only use the Integrated Intel card is to make the following changes:

[LIST]
[*] _Blacklisting of the radeon driver_:
Create **/etc/modprobe.d/vgaswitcheroo.conf** and add
```
blacklist radeon
```

[*] _Service that controls the card_
Create **/etc/init.d/vgaswitcheroo** and add
```
#!/bin/sh -e
#
# This script is executed at the end of each multiuser runlevel.
# Make sure that the script will "exit 0" on success or any other
# value on error.
#

COMMAND="$1"

case "$COMMAND" in
restart|start)
	echo "Switching off Radeon dedicated graphics"
	modprobe radeon
	echo OFF > /sys/kernel/debug/vgaswitcheroo/switch
	;;
stop)
	echo "Switching on Radeon dedicated graphics"
	echo ON > /sys/kernel/debug/vgaswitcheroo/switch
	;;
status)
	cat /sys/kernel/debug/vgaswitcheroo/switch
	;;
esac

exit 0
```

[*] _Make the service called by default_
Run these commands:
```
cd /etc/rc2.d
ln -s ../init.d/vgaswitcheroo S21vgaswitcheroo
```

[*] _Make sure it works on hibernate_
In **/etc/hibernate/common.conf** add the following line
```
RestartServices vgaswitcheroo
```


[/LIST]

---

### Post by lgp171188 on 2012-05-08
> **andrikos said:**
> My solution in order to have the Discrete ATI graphics always Off and only use the Integrated Intel card is to make the following changes:

[LIST]
[*] _Blacklisting of the radeon driver_:
Create **/etc/modprobe.d/vgaswitcheroo.conf** and add
```
blacklist radeon
```

[*] _Service that controls the card_
Create **/etc/init.d/vgaswitcheroo** and add
```
#!/bin/sh -e
#
# This script is executed at the end of each multiuser runlevel.
# Make sure that the script will "exit 0" on success or any other
# value on error.
#

COMMAND="$1"

case "$COMMAND" in
restart|start)
	echo "Switching off Radeon dedicated graphics"
	modprobe radeon
	echo OFF > /sys/kernel/debug/vgaswitcheroo/switch
	;;
stop)
	echo "Switching on Radeon dedicated graphics"
	echo ON > /sys/kernel/debug/vgaswitcheroo/switch
	;;
status)
	cat /sys/kernel/debug/vgaswitcheroo/switch
	;;
esac

exit 0
```

[*] _Make the service called by default_
Run these commands:
```
cd /etc/rc2.d
ln -s ../init.d/vgaswitcheroo S21vgaswitcheroo
```

[*] _Make sure it works on hibernate_
In **/etc/hibernate/common.conf** add the following line
```
RestartServices vgaswitcheroo
```


[/LIST]

Removing nomodeset and blacklisting radeon doesn't work for me as the display switches off without nomodeset

---

### Post by andrikos on 2012-05-08
> **lgp171188 said:**
> Removing nomodeset and blacklisting radeon doesn't work for me as the display switches off without nomodeset

I think nomodeset is essential for this to work.
The default ubuntu kernels already have this option enabled.

---

### Post by ndak on 2012-05-11
The procedure described by Andrikos worked for Lenovo g770 with Intel core i5-2410M with hybrid Integrated graphics + AMD Radeon HD6650M running Ubuntu v.12.04 LTS.  After making the script executable and rebooting, the Radeon graphics was powered off and computer/cpu temps went from 50-60 C to 30-40 C.  I was not able to complete the final hibernate step of the procedure because I could not save the file for some reason.  It still works fine.

Many thanks to all who spent considerable effort to solve this hybrid issue with Intel processors.

dal

---

### Post by vaporblock on 2012-06-05
Hey guys

I'm completely new with Ubuntu, and I have really very little experience with it. So I need a lot of HELP!!!

I have a sony vaio VPCSB with switchable graphics (intel HD 3000 and Radeon6410). I tried to install the drivers for the graphics cards by using the additional drivers function of Ubuntu, but that really didn't help anything. As Im a complete noob at these things, could you list the **exact** **steps** that I need to do to get the graphics working (at least intel). Without it Im unable to finish my assignment, so Its really urgent.

---

### Post by mexicanseaf00d on 2012-06-05
uninstall fglrx drivers (google how to do that)!

then

1) in a terminal: **sudo -i**
2)  edit **/etc/rc.local**, add following before "exit 0":
```
modprobe radeon
echo OFF > /sys/kernel/debug/vgaswitcheroo/switch
```3) edit **/etc/modprobe.d/blacklist.conf**, add
```
blacklist radeon
```0




Also look at this thread [http://ubuntuforums.org/showthread.php?t=1930450](http://ubuntuforums.org/showthread.php?t=1930450)

---

### Post by heidricha on 2013-04-26
I have got a HP ProBook 4740s
One of my problems with the NB was this overheating (60C in normal conditions - very incomfortable under my left wrist - now it's about 45C, still warm, but OK) and poor battery life (under 2 hours - now it is over 5).
Now both have been solved with the help of this topic and other resources, but I have got a new one:

system completely freezes after waking up from standby/sleep state, or when I press fn+f4 to change the monitor configuration.

I have read, that it should have been solved with the /etc/pm/sleep.d/whatever script, but it had not solved the problem at all. Anyone to advice anything?

Currently I have this in rc.local:

modprobe radeon
sleep 2
echo OFF > /sys/kernel/debug/vgaswitcheroo/switch

# grep radeon /etc/modprobe.d/blacklist.conf 
blacklist radeon

# cat /etc/pm/sleep.d/11_switcheroo_suspend 
#!/bin/bash
case "${1}" in
        hibernate|suspend)
		modprobe radeon
                echo ON > /sys/kernel/debug/vgaswitcheroo/switch
		;;
        resume|thaw)
                echo OFF > /sys/kernel/debug/vgaswitcheroo/switch
                 ;;
esac

The scripts are executable, and the VGA config is OK after a fresh boot. If I put the NB in standby state, it can wake up a few minutes later, but if I do this at night, the PC won't wake up in the morning! I can see the closed X11 screen, but mouse ptr doesn't move, even CapsLock doesn't work, so it is stoned perfectly.

Earlier I have also tried the closed-source driver from Ati. It was not bad at all, but there didn't exist a way to put the PC in sleep state at all! Now I think I know why ;) but I hope I'm wrong, and it should be possible somehow!

---

### Post by sauthess on 2013-04-26
Hi,

I think you should remove "modprobe radeon". 
Loading a module for a hardware that is stopped (you power on it just after) isn't a good idea...
EDIT : and you don't need the module, you only need that the card is powered on sleep time so modprobing isn't usefull

When I had a HP laptop, I had this bug :
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/966744](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/966744)

Possibly you have it ...

Solution was this command : chmod -x /etc/acpi/lid.sh

You can test it easily...

Hope this help,

BR,

---

