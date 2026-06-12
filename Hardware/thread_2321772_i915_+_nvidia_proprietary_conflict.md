---
title: "i915 + nvidia proprietary conflict"
date: 2016-04-24
forum: Hardware
---

### Post by bolvan2 on 2016-04-24
I'm in process of upgrading from 12.04 to 16.04 mate.
My system has builtin intel graphics (forcibly enabled in bios) and nvidia card.
I use multiseat configuration. One monitor connected to intel, another to nvidia.
It all worked fine in 12.04.
In 16.04 there's problem.
After short time after boot (~1.5 sec) kernel console messages disappear from the nvidia screen
and screen remains blank until xorg starts. If xorg does not start then system is unaccessible from console.
After xorg is started ctrl+alt+Fx successfully switches to nvidia framebuffer console.
It means problem occurs once during initialization.
With nouveau all works fine. With nvidia prop and intel disabled also works fine.
So I decided there's conflict between nvidia prop and i915.
I cant use nomodeset because intel does not work without it. I dont know how to push modeset=0 only to nvidia.
I'm on nvidia-340, my card is old and newer drivers do not support it

Problem starts far before Xorg startup, so its not X server misconfiguration.
Also searching for a tool that can set video mode with KMS (kernel modes setting)/DRI.
Such tool would be workaround.

---

### Post by bcschmerker on 2016-04-24
Unfortunately, multiple-GPU support has been deprecated in X.org since 2014.  What nVIDIA® GPU in your system as of 24 April 2016?  As I understand things, the Intel® i915 Express Set™ should have minimal trouble with cards as recent as the Fermi architecture, which I am working up in the form of a MicroStar® N610GT (GF119 GPU) in an eMachines®/Acer® EL1210-09 (AMD Athlon64®, nVIDIA® nForce® 785 chipset) with a Shuttle® PSU upgrade, under UbuntuGNOME® 16.04.0-LTS.  How powerful a Fermi your system can take depends on the +12VDC reserves of your current power supply.

---

### Post by bolvan2 on 2016-04-25
> **bcschmerker said:**
> Unfortunately, multiple-GPU support has been deprecated in X.org since 2014.  What nVIDIA® GPU in your system as of 24 April 2016?  As I understand things, the Intel® i915 Express Set&#8482; should have minimal trouble with cards as recent as the Fermi architecture, which I am working up in the form of a MicroStar® N610GT (GF119 GPU) in an eMachines®/Acer® EL1210-09 (AMD Athlon64®, nVIDIA® nForce® 785 chipset) with a Shuttle® PSU upgrade, under UbuntuGNOME® 16.04.0-LTS.  How powerful a Fermi your system can take depends on the +12VDC reserves of your current power supply.

I run 2 instances of xorg each for separate hardware and they work well.
As I said problem starts at early stage far before Xorg loading and happens even if display manager is disabled and Xorg never launches. Its not xorg problem. Its DRI driver problem related to modeswitching and framebuffer.
Framebuffer on nvidia part gets unusable.
I did  "dd if=/dev/urandom of=/dev/fb1" from ssh and intel display was filled with color garbage.
I did  "dd if=/dev/urandom of=/dev/fb0" and nvidia display remained blank.
After reset by Xorg (launch  and kill it) fb0 display data and get filled as fb1.
Nvidia monitor reports video mode is 1024x768 => it does not lose signal while fb0 is blank.
My card is 9600GT.

For workaround I created systemd service that runs shell script.
That script launches Xorg with special xorg.conf and kills it after 4 seconds.
Dirty hack but I have no idea how otherwise fix it. Only Xorg appear to heal the situation.
I'd rather have KMS tool to switch modes than launching heavy Xorg

---

### Post by roler2 on 2016-04-25
The i915 does not appear to work with Lubuntu 16.04. I am able to get to the Choice Screen. However, after that, nothing except a flashing cursor in the upper left corner and a completely black screen. Happens both in Live Mode and after Hard Drive Installation. I am able to install the entire system on the Hard Drive. I just can't boot to any type of Desktop at all.

I was able to boot to Desktop with the Beta Versions of 16.04. The font rendering was horrible, but at least I got something.

With the final release, I get nothing but a flashing cursor and a completely black screen. No messages. Nothing. My thought is that the newest Kernel does not support the i915 at all, given at least the Beta Versions I was able to access the Desktop.

Is there anything I can do to see if I can at least access the Desktop?

---

### Post by bolvan2 on 2016-04-25
> **roler2 said:**
> The i915 does not appear to work with Lubuntu 16.04.
Is there anything I can do to see if I can at least access the Desktop?

It works fine on my system. core i7 - 4770K  (hasswell)
Blinking cursor probably means X server was not started and you are stuck in console.

checklist :
Press alt-F1 alt-F2 ... to see if you can switch virtual terminals. If not then your best option is remote login via ssh.
Login as root.
lspci  and find out if you have only one VGA/display adapter. May have intel+nvidia on laptop and have my problem I described above.
View kernel cmdline. cat /proc/cmdline.  See there any "nomodeset" or "modeset=0". Intel does not work without modesetting.
 Check if i915 kmod is loaded : lsmod | grep i915.  If not then analyze dmesg for the reason.
 Check if framebuffer device is present : ls /dev/fb0
 Check if drm interface available : ls /dev/dri/card0
 Analyze why Xorg does not start. Log file is in /var/log

---

### Post by roler2 on 2016-04-25
Thank you for your advice. Unfortunately, I have absolutely no idea how to do any of the steps. All I get is a black screen with a blinking cursor in the upper left corner. How do I log in? How do I check anything via the terminal? When I press alt-F1 I get a reboot. I am wanting to check on what the issue is, and I am very willing to try, I just don't know how to do so being all I get is a black screen with a blinking cursor in the upper left corner and nothing else.

"Blinking cursor probably means X server was not started and you are stuck in console."


You are probably correct I just don't how to diagnose/fix the issue.

Please be aware that the issue occurs with Live Mode (no Install) or even after I have installed the OS to the Hard Drive. Doesn't matter. Same issue. I get to the Screen that offers a choice. After I make the choice, either Live Mode or I boot directly to the Hard Drive, I still get a completely black screen with the blinking cursor. So that is why I am thinking that the i915 Driver that is installed on the Dell P4 is not compatible with the updated Kernel or vice-versa. The only Kernel that has worked correctly on my P4 with the i915 is the 14.04 default Kernel, not any of the upgraded Kernels.

---

### Post by bcschmerker on 2016-04-26
> **roler2 said:**
> The i915 does not appear to work with Lubuntu 16.04. I am able to get to the Choice Screen. However, after that, nothing except a flashing cursor in the upper left corner and a completely black screen. Happens both in Live Mode and after Hard Drive Installation. I am able to install the entire system on the Hard Drive. I just can't boot to any type of Desktop at all.

I was able to boot to Desktop with the Beta Versions of 16.04. The font rendering was horrible, but at least I got something.

With the final release, I get nothing but a flashing cursor and a completely black screen. No messages. Nothing. My thought is that the newest Kernel does not support the i915 at all, given at least the Beta Versions I was able to access the Desktop.

Is there anything I can do to see if I can at least access the Desktop?
**Sounds particularly serious.**  So your rig started last under, I estimate, LinUX Kernel 3.8.0-*n*-generic?  In that case, GRUB needs configuration amendment if the problem with Kernel 4.4.0-*m*-generic is to be identified.  Were your rig capable of reaching the Login, sudo edit /etc/default/grub and sudo update-grub would be available; that, however, appears not the case.  I'm not advanced enough a hacker to make any recommendations concerning editing /boot/grub/grub.cfg to get a terminal output for monitoring the boot process.

On my own rig under Ubuntu® 16.04.0-LTS, I set the GRUB default configuration (from /etc/default/grub) as follows:
```
GRUB_DEFAULT=0
GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="debug"
GRUB_CMDLINE_LINUX=""

```At which point, sudo update-grub amends /boot/grub/grub.cfg and other files to carry out the amended default.

---

### Post by roler2 on 2016-04-26
Well. . .it is only serious with the Kernel releases after 14.04 default which I think is 3.13 Kernel? 14.04 with the default kernel worked perfectly. The beta versions of 16.04 were able to boot to the Desktop, although the Font rendering was horrible. The released version of 16.04 I am only able to get to a Black Screen with blinking cursor after selecting Live Mode or Install Mode. Both give same results. I don't know how to access anything else in terms of trying to identify the issue(s). Both yourself and bolvan2 gave some great advice and suggestions (Thank you!), I just don't how to implement those suggestions. There is no log in screen, there is nothing but a black screen with a blinking cursor. Nothing else happens. It just sits with a blinking cursor. If I reboot I get the same results.

---

### Post by Bucky Ball on 2016-04-26
[See this thread]("http://ubuntuforums.org/showthread.php?t=2314964&p=13445765&viewfull=1#post13445765"). Are you running a Baytrail?

---

### Post by roler2 on 2016-04-26
I don't know exactly what a Baytrail is but I am running the i915 Driver on a very old P4 Computer. 

This statement is absolutely true: "People running Ubuntu 14.04 LTS with the original 3.13 kernel are fine." 

I have posted the same thing within this Forum. The Default 3.13 Kernel is the only one that will work with the i915 Driver, especially on an old P4 with built-in graphics. However, some of the other Forum Members have had some success, so maybe the issue is restricted to very old Dell P4 computers with built-in i915 Graphics.  


With the 16.04 Beta Install the Computer did hang. That is what the problem was. I was able to get to Desktop then a freeze or a hang almost immediately. You could not do anything. The Font Rendering was also horrible.


With the 16.04 actual Release I cannot even access any type of Desktop in either Live Mode or Install Mode. Just a black screen with a blinking cursor. Not even any boot up info at all. Nothing.


In regards to the workaround: "intel_idle.max_cstate=1", I would have no idea how to apply the fix as I do not have access to the Desktop upon Booting. Am I supposed to put that fix in grub?

I was actually quite surprised being that I could at least access the Desktop with 16.04 Beta in that I could not access anything except a Black Screen/blinking cursor with the 16.04 actual release, neither in Live Mode nor Install Mode.

---

### Post by Bucky Ball on 2016-04-26
[This]("http://ark.intel.com/products/codename/55844/Bay-Trail#@All") may not be a comprehensive list.

---

### Post by roler2 on 2016-04-26
The BayTrail article appears to mention that Intel does not believe it is an Intel Driver issue, given that the default 14.04 Kernel works very well with the i915 (and it does). It is the upgraded Kernels that do not work with the i915 Driver, especially with Lubuntu. Could there be a possibility that it is also LXDE related, given that Xubuntu does not appear to have the same issues on a regular basis?

---

### Post by bcschmerker on 2016-04-26
> **Bucky Ball said:**
> [See this thread]("http://ubuntuforums.org/showthread.php?t=2314964&p=13445765&viewfull=1#post13445765"). Are you running a Baytrail?
Negatory on Bay Trail for roler2 - this problem involves an Intel® Pentium Processor® 4™ (PGA 775) and i915 Express Set™, rather than an Atom Processor™.  Boot has no DMesg from either the nVIDIA® G94 or the Intel® High Definition Graphics™ at last check, so roler2 is unable to read Kernel messages.  With do-grub-configure and update-grub not an option as of 26 April 2016, what needs be done to get a readable text output on any device, including a Boundless® VT500 or similar serial terminal if necessary?

---

### Post by Bucky Ball on 2016-04-26
> **bcschmerker]... this problem involves an Intel® Pentium Processor® 4&#8482 said:**
> 

Yep, I know, which is why I thought it could perchance be one of the ones on the link I provided to Bay Trail processors on the Intel site. There are Atoms, Celerons and these:

[QUOTE]Intel® Pentium® Processor N3540
(2M Cache, up to 2.66 GHz) 	Launched 	Q3'14 	4 	7.5 W 	TRAY: $161.00 	Intel® HD Graphics
Compare 	Intel® Pentium® Processor N3530
(2M Cache, up to 2.58 GHz) 	Launched 	Q1'14 	4 	7.5 W 	TRAY: $161.00 	Intel® HD Graphics
Compare 	Intel® Pentium® Processor N3520
(2M Cache, up to 2.42 GHz) 	Launched 	Q4'13 	4 	7.5 W 	TRAY: $161.00 	Intel® HD Graphics
Compare 	Intel® Pentium® Processor N3510
(2M Cache, 2.00 GHz) 	Launched 	Q3'13 	4 	7.5 W 	TRAY: $161.00 	Intel® HD Graphics
Compare 	Intel® Pentium® Processor J2900
(2M Cache, up to 2.67 GHz) 	Launched 	Q4'13 	4 	10 W 	TRAY: $94.00 	Intel® HD Graphics
Compare 	Intel® Pentium® Processor J2850
(2M Cache, 2.41 GHz) 	Launched 	Q3'13 	4 	10 W 	TRAY: $94.00 	Intel® HD Graphics
Compare 	Intel® Pentium® Processor A1020
(2M Cache, up to 2.66 GHz)

---

### Post by roler2 on 2016-04-26
Why don't the Ubuntu Developers, or most specifically the Lubuntu Developers, create a 16.04 ISO with the 3.13 Default Kernel series that was initially included with 14.04. It appears to me, that a lot of other Forum Members are having video issues, especially with 16.04, and select releases subsequent to 14.04. even outside of Intel Graphics. The 3.13 Kernel apparently works very well with almost all Graphics/Express Sets/NVidia, all Intel releases etc. It certainly works great with the i915. Clear and crisp Font Rendering too. Then, when the Kernel issue is fixed, instead of reinstalling the entire OS, the fixed Kernel update can be applied. Maybe the current 16.04 Kernel is more stable all-around than the 3.13 Series however, obviously with certain Graphics, it is not. Better than just continually getting stuck with a black screen and/or continuous freezes.

---

### Post by roler2 on 2016-04-26
oops! I see that one of the Forum Members had difficulty with NVidia and 14.04. However, that may have been from a 14.04 Kernel upgrade. The Graphics and/or Kernel issues started subsequent to the initial release of 14.04. I think they started with 14.04.2 when an upgraded Kernel was utilized.

---

### Post by Bucky Ball on 2016-04-26
> **roler2 said:**
> Why don't the Ubuntu Developers, or most specifically the Lubuntu Developers, create a 16.04 ISO with the 3.13 Default Kernel series that was initially included with 14.04.

As you'd have more chance of finding a hen's tooth on these forums than a Ubuntu dev, or a Lubuntu dev, I'll just say 'don't know' and advise that you approach the Lubuntu devs directly with your suggestions if you would seriously like Canonical to consider them. ;)

---

### Post by roler2 on 2016-04-27
I have actually had success posting on these Forums. A lot of success. Many of my own issues have been successfully resolved. There are some very very brilliant Forum Members. These Forums are tied into the Lubuntu Blogs. In fact, over at the Lubuntu Blogs one is encouraged to posts respective issues within these very same Forums. So the Lubuntu Dev's must read these Posts. I am sure some fix will eventually find its way on the Kernel issue(s). Too many Forum Members are having difficulties.

---

### Post by roler2 on 2016-04-27
This may or may not help others:

[https://answers.launchpad.net/ubuntu/+question/292402](https://answers.launchpad.net/ubuntu/+question/292402)

Please note when the OP was asked: What is the output of:


sudo lshw -C display


If you scroll down:


configuration: driver=i915 latency=0

---

### Post by bcschmerker on 2016-04-27
**Something popped into my head concerning GRUB!**  Press and hold a Shift key at the end of power-on self-test, and a GRUB menu should appear on the Console.  Select Rescue Mode to boot into single-user mode, and it should be possible to extract the DMesg after completing Filesystem Checks.  Unless the process hits a hard lockup or other fatal error short of fsck.ext4, that is.

---

