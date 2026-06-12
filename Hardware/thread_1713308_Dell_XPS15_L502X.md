---
title: "Dell XPS15 L502X"
date: 2011-03-23
forum: Hardware
---

### Post by stunti on 2011-03-23
I think all the problem everybody had with the L501X are back with the L502X.
Of course the fixes on the L501X don t work on this new one.

I'll try to gather all the possible fixes and organize them in this post.

I got my new computer 2 days ago wit the following config:
 - Sandy Bridge i7 2720QM
 - NVidia GT540M (so with optimus)
 - Chipset Intel HM67
 - Intel Wireless-N 1030 
 
I think that's about it on what can cause trouble.

So far on windows everything works fine. Wifi N is working. I haven't tested optimus.

On Ubuntu (10.10) it's a different story. 
- Wifi is not working (card is not detected)
- Ethernet is working
- GT540M is visible but not working. But I can't switch it off using acpi call.
- trackpad is one finger only.

Since it's a new computer I can try a lot of things. I try to upgrade to natty but it failed for some reason. Will try to install natty from scratch to see I can get the wifi working.

The main problem right now is the wifi for me.
I tried to install the driver from intel but no luck.

Any tips, or things you want me to try let me know.

---

### Post by stunti on 2011-03-24
I tried to install 11.04 yesterday.
First on top of 10.10 but it didn't worked. Crash when replacing kernel image.
After that the computer wasn't booting at all, so I install a Fresh 11.04 but same result.
I used Alpha3 for that.
The interesting thing tho is that when booting in liveCD the computer was working and the LED for he Wifi was on. But the wifi wasn't usable.

I have downloaded the latest DVD image available and will try again.

---

### Post by ashikaga on 2011-03-24
Hi stunti,

I have an L502X on the way from the factory, hopefully should arrive in about a week. My plan is to eventually dual-boot with Windows 7 and Ubuntu, so when it arrives I'll post here with my Live CD experiences. I'll probably just stay with 10.10. Keep us updated with your efforts, much appreciated. :)

---

### Post by Yellow Pasque on 2011-03-24
Optimus? No, run.

---

### Post by stunti on 2011-03-24
Can you describe your set up?

---

### Post by ashikaga on 2011-03-24
Mine will be the same spec as yours (incl. same wireless chipset), but with the i7-2820QM CPU.

---

### Post by stunti on 2011-03-25
Okay I got natty installed from the latest daily dvd (19-03-2011).
Wifi is working although unstable.
Ethernet is working as well as the brightness control.

So far the only problem is the nvidia which is not disabled yet.
but beside draining the battery is not really a problem.
Unity desktop which is a pretty big change as well and need some practice.

---

### Post by Gilgha on 2011-03-28
Hi,

I also have a XPS 15 L502X and trying switch off the nvidia GPU (mine is 525M GT).

I think you don't have to install natty to fix the wifi issue. I don't have the same card as you but mine did not work out of the box too.
I installed the natty 2.6.38 kernel which you can download on kernel.ubuntu.com and now wifi works fine!

---

### Post by Tzbob on 2011-03-31
I've just shut down my GT540M with the following acpi_call:

\_SB.PCI0.PEG0.PEGP._OFF

---

### Post by desired username on 2011-04-01
Stunti,

Can you please post how you got the wifi to work?

Thanks,

---

### Post by sgb77 on 2011-04-01
Hey all,
I got one of these laptops as well (xps 15 L502X) mi wifi worked off the box, and my display works, but no way to get compiz working. I have tried many workarounds suggested for similar configuration laptops, but everytime I've come up empty handed. Do you guys know if there is something in the works for this video card?

Has anybody tried any of the video connections? I need to get this laptop working with an external monitor.

Webcam is not working
Card reader not working
HDMI ??
mini display port??

I really want to use this computer with ubuntu, do you guys think all these issues will be solved fast or should I just return and get a different computer?

---

### Post by stunti on 2011-04-01
> **Tzbob said:**
> I've just shut down my GT540M with the following acpi_call:

\_SB.PCI0.PEG0.PEGP._OFF

It seems to work but my system gets unstable after a few minutes.
@Tzbob: Is your system stable?

---

### Post by beew on 2011-04-01
> **sgb77 said:**
> Hey all,
I got one of these laptops as well (xps 15 L502X) mi wifi worked off the box, and my display works, but no way to get compiz working. I have tried many workarounds suggested for similar configuration laptops, but everytime I've come up empty handed. Do you guys know if there is something in the works for this video card?

Has anybody tried any of the video connections? I need to get this laptop working with an external monitor.

Webcam is not working
Card reader not working
HDMI ??
mini display port??

I really want to use this computer with ubuntu, do you guys think all these issues will be solved fast or should I just return and get a different computer?

This is because of Optimus.

See my reply on your old thread.[URL="http://ubuntuforums.org/showthread.php?t=1718188&page=4"]
http://ubuntuforums.org/showthread.php?t=1718188&page=4[/URL]

If I were you I would get a different computer if you still have that option. There are some tutorials on how to make an Optimus enabled laptop "works" on UF, but they aren't really worth the troubles if you can exchange for a different computer because they all consist of getting the intel graphic card to work while disabling the nvidia card somehow, but why would you want to pay more for a nvidia card that you cannot use? That is not an acceptable solution.

Remember to check for Optimus, any new laptop with a nvidia card may not work on Linux because of optimus (**even if the card has Linux driver from Nvidia**), it is pretty f-up.

Thinkpad T410 and T510 appear to work because they have a BIOS switch to turn off Optimus and use the discrete graphic card (Nvidia) exclusively but you'd better double check and those are expensive, you can also get a laptop with an older Nvidia card that may not be Optimus enabled, this guy got a Samsung which is apparently safe [http://ubuntuforums.org/showthread.php?t=1718637](http://ubuntuforums.org/showthread.php?t=1718637)

---

### Post by Tzbob on 2011-04-02
> **stunti said:**
> It seems to work but my system gets unstable after a few minutes.
@Tzbob: Is your system stable?

Define unstable,

I haven't encountered any problems so far.

---

### Post by ashikaga on 2011-04-04
> **Tzbob said:**
> Define unstable,

I haven't encountered any problems so far.

Likewise - I've installed Natty beta 1 from the DVD on my L502X yesterday, as a dual boot with Win 7. Wireless worked out of the box, seems fine so far. Only glitch I noticed was that turning bluetooth off also turned the wireless off.

Unity/compiz didn't work when I first loaded up Natty, but then I realised that the Nvidia binary drivers had been installed. Once I removed them and rebooted, Unity came up fine. I occasionally get messages popping up about system processes having problems, but at this stage I'm putting that down more to the beta-ness of Natty than anything else. (I haven't investigated what they actually are yet.) Overall, things work surprisingly well. Happy to test anything in particular (within reason!) if anyone's curious.

---

### Post by sunilm on 2011-04-04
Google Earth v6.0.2

System: Dell XPS L502x (i7-2720/8G/nvidia525M).
Nvidia GPU disabled using acpi_call.ko and shell script.

Installed Google Earth (64 bit .deb from google website).

I notice that the Google Earth performance is pretty choppy.

Has anybody tried Google earth on these new Dell systems ? Any way to improve performance ?

Thanks in advance.

---

### Post by beew on 2011-04-04
> **sunilm said:**
> Google Earth v6.0.2

System: Dell XPS L502x (i7-2720/8G/nvidia525M).
Nvidia GPU disabled using acpi_call.ko and shell script.

Installed Google Earth (64 bit .deb from google website).

I notice that the Google Earth performance is pretty choppy.

Has anybody tried Google earth on these new Dell systems ? Any way to improve performance ?

Thanks in advance.

Your system just doesn't play well with Linux because of Optimus. See my post above.

By disabling the Nvidia card you are basically using the onboard Intel card so poor performance is probably expected.

---

### Post by sunilm on 2011-04-05
> **beew said:**
> Your system just doesn't play well with Linux because of Optimus. See my post above.

By disabling the Nvidia card you are basically using the onboard Intel card so poor performance is probably expected.

The culprit is compiz. If compiz is disabled, google earth performance is quite decent. Found quite a few howtos to hack google-earth script to run metacity before launching googleearth-bin. and restore compiz after googleearth-bin exits.

BTW, I am guessing that the advantage of switching off nvidia card is  that this will improve battery life.

Another interesting observation: My old HP dv4t with Intel integrated graphics ran googleearth well without having to disable compiz.

Does anybody know a way to improve google-earth performance without disabling compiz ? Heard about Driconf utility. How can that be configured ?

I will post any solution/hack using Driconf, if its more elegant than disabling compiz.

---

### Post by beew on 2011-04-05
> **sunilm said:**
> 
BTW, I am guessing that the advantage of switching off nvidia card is  that this will improve battery life.


I wouldn't call it an advantage, just making the best out of a very bad situation. If the Nvidia card is not needed then you may as well buy a laptop without Nvidia instead of one that has it but you cannot use because of Optimus. It would be cheaper. 

I think something is not right. The machine is new and powerful and there is no reason why you need to disable Compiz to run ge. I have full compiz and ge running on some really old and crappy machines without a problem  (Intel graphic cards) and I am also able to do this on other machines using only the FOSS drivers (both ATI and Nvidia, the Nvidia machine is quite new, but the ATI one is old too and it is a netbook with very weak specs)

---

### Post by jamescr on 2011-04-05
I bought one of these laptops a couple of weeks ago and after installing 10.10 which had some problems I upgraded to 11.04 and am mostly happy with things.

But I can't seem to get it to work with an external monitor via the HDMI port.

Is this because the nvidia card is not being used and it is the only thing that will drive the hdmi port?

Has anyone had success getting the hdmi output working?

---

### Post by Gilgha on 2011-04-05
> **sunilm said:**
> Google Earth v6.0.2

System: Dell XPS L502x (i7-2720/8G/nvidia525M).
Nvidia GPU disabled using acpi_call.ko and shell script.

Installed Google Earth (64 bit .deb from google website).

I notice that the Google Earth performance is pretty choppy.

Has anybody tried Google earth on these new Dell systems ? Any way to improve performance ?

Thanks in advance.

How did you disable the Nvidia 525M GPU?

---

### Post by sunilm on 2011-04-05
I have ubuntu 11.04 beta1 + Google earth 6.0.2. May be compiz + unity is not stable yet.

---

### Post by sunilm on 2011-04-05
> **Gilgha said:**
> How did you disable the Nvidia 525M GPU?

I have compiled module acpi_call.ko. I then run the attached shell script. You may need to edit it for paths etc.

---

### Post by ashikaga on 2011-04-05
> **sunilm said:**
> I have ubuntu 11.04 beta1 + Google earth 6.0.2. May be compiz + unity is not stable yet.
You could test this hypothesis by logging out and logging back in with "Ubuntu Classic" selected at the bottom of the screen during logon, which boots Gnome instead of Unity.

If I remember tonight I'll try running Google Earth on my 11.04 beta 1.

---

### Post by sunilm on 2011-04-06
> **ashikaga said:**
> You could test this hypothesis by logging out and logging back in with "Ubuntu Classic" selected at the bottom of the screen during logon, which boots Gnome instead of Unity.

If I remember tonight I'll try running Google Earth on my 11.04 beta 1.

Well, its compiz I suppose. I logged in with Ubuntu Classic (no effects). Only then does google earth run smoothly.

---

### Post by sunilm on 2011-04-06
> **sunilm said:**
> Well, its compiz I suppose. I logged in with Ubuntu Classic (no effects). Only then does google earth run smoothly.

Its a regression in intel drivers for integrated graphics.

I see messages in /var/log/syslog like:
*[drm:i915_hangcheck_ring_idle] *ERROR* Hangcheck timer elapsed... render ring idle [waiting on 35043, at 35043], missed IRQ?*

A  bug reported in redhat (684097) corroborates my observations so far. 

The regression is fixed in kernel 2.6.39-rc1. So, I dont know if it will be picked up by ubuntu for 11.04 release. Hoping for the best.....

---

### Post by Gilgha on 2011-04-06
> **sunilm said:**
> I have compiled module acpi_call.ko. I then run the attached shell script. You may need to edit it for paths etc.

Thank you.

It works!

---

### Post by sunilm on 2011-04-07
> **sunilm said:**
> Its a regression in intel drivers for integrated graphics.

I see messages in /var/log/syslog like:
*[drm:i915_hangcheck_ring_idle] *ERROR* Hangcheck timer elapsed... render ring idle [waiting on 35043, at 35043], missed IRQ?*

A  bug reported in redhat (684097) corroborates my observations so far. 

The regression is fixed in kernel 2.6.39-rc1. So, I dont know if it will be picked up by ubuntu for 11.04 release. Hoping for the best.....

Opened a defect (753189) in launchpad for this

---

### Post by Damien B. on 2011-04-07
Hi,
Has anyone observed this?
I turn on the computer (L502x with GT540M), I run the script describe above: the card is turned off and the consumption greatly reduced. All good for now.
Then I do a clean restart from Ubuntu, and I get a failure of the same script (AE_NOT_FOUND).
Very strange. Will try to update the bios to A04 version from DELL to see if that makes a difference.
Damien

---

### Post by sunilm on 2011-04-07
> **Damien B. said:**
> Hi,
Has anyone observed this?
I turn on the computer (L502x with GT540M), I run the script describe above: the card is turned off and the consumption greatly reduced. All good for now.
Then I do a clean restart from Ubuntu, and I get a failure of the same script (AE_NOT_FOUND).
Very strange. Will try to update the bios to A04 version from DELL to see if that makes a difference.
Damien
Did you install a new version of the kernel ? If so, you may need to rebuild the kernel module.
(cd  <acpi_call_directory>; make)

---

### Post by criogix on 2011-04-15
Well,let me tell you my 2 day experience about turning off the nvidia card.I've managed today to call the acpi method(new ubuntu user so it was pretty hard for me).Surprise,everything worked an let's say my nvidia card was shutdown so it wont eat up my battery life.All good until the first shutdown/restart,the computer froze up so had to manually force shutdown(pressing the button).then it starts up,logs into ubuntu but nvidia card keeps on going and had to go through the steps again to stop the card(don't know if it really stops,it says it does but don't see an improvement like battery lasts longer or cooling fan stops acting crazy).So how can this method be implemented in the startup process for not having the need to go over and over again an the laptop stop freezing? Another workaround will be making a petition to Dell inc. to develop a bios in which we'd be given the option to change between intel/nvidia card or use both with the optimus system(only in windows) because i guess there are a lot of us out there who think linux is more of a operating system than windows,and i need to learn linux in school but my pocket doesn't let me to buy a new laptop if i screw this one up.Hope to hear for the best and if anyone likes my petition idea  please let me know and start the things up. THE END !!!

---

### Post by o----o on 2011-04-15
hello here is my experience.

**What I want:**
[LIST]
[*]Ubuntu
[*]Running Nvidia
[*]WIFI
[*]Realtime kernel
[/LIST]
(I do not want to use Optimus, or turn off the Nvidia, I just want the Nvidia run all the time!)

**What I have:**
[LIST]
[*]Ubuntu - 11.04 (64bit)
[*]Nvidia - 270.41.03-0ubuntu1 (this one should support our NV card GT 525 M [> READ MORE HERE]("https://launchpad.net/ubuntu/+source/nvidia-graphics-drivers/270.41.03-0ubuntu1/+buildjob/2476473"))
[*]Wifi works automatically (starts working after the lowlatency kernel)
[*]Realtime kernel - 2.6.38-8-lowlatency [> DOWNLOAD HERE]("https://launchpad.net/~abogani/+archive/ppa/?field.series_filter=natty")
[/LIST]

**experience:**
When I bought it I tried Ubuntu 10.10 installed system, with full update, then nvidia, then Lowlatency kernel(wifi didn't work until I installed lowlatency kernel). Everything seams to be OK, but then I realized I want different partition setup, so I have deleted everything.
and have stated from scratch..
From then I have spent tree days DJing with different Ubuntu versions, 10.04. 10.10, Ubuntu studio, nothing work.
Now I have 64bit Ubuntu natty 11.04 it all works pretty well, Ubuntu says that Nvidia drivers are currently active and in use..... I do not believe it. 

**Nvidia settings** always pops up saying "*You do not appear to be using the NVIDIA X driver.* " 
(then when I try to run the nvidia-xconfig, when I restart the only way how to get X up is to boot up in safe mode)
**Blender** says:
```
Xlib:  extension "GLX" missing on display ":0".
intern/ghost/intern/GHOST_WindowX11.cpp:177: X11 glxChooseVisual() failed for OpenGL, verify working openGL system!
X Error of failed request:  BadWindow (invalid Window parameter)
  Major opcode of failed request:  18 (X_ChangeProperty)
  Resource id in failed request:  0x348ee10
  Serial number of failed request:  21
  Current serial number in output stream:  22
```

**Unity** .. I'm not able to start it up

**lspci -v**
```
01:00.0 VGA compatible controller: nVidia Corporation Device 0df5 (rev a1) (prog-if 00 [VGA controller])
	Subsystem: Dell Device 04b6
	Flags: bus master, fast devsel, latency 0, IRQ 16
	Memory at f0000000 (32-bit, non-prefetchable) [size=16M]
	Memory at c0000000 (64-bit, prefetchable) [size=256M]
	Memory at d0000000 (64-bit, prefetchable) [size=32M]
	I/O ports at 3000 [size=128]
	Expansion ROM at f1000000 [disabled] [size=512K]
	Capabilities: <access denied>
	Kernel driver in use: nvidia
	Kernel modules: nvidia-current, nvidia, nouveau, nvidiafb
```

**glxinfo |grep rendering**
```
Xlib:  extension "GLX" missing on display ":0".
```

What do you think of it, where is my problem?... is the Nvidia really useless and we do not have slight chance to run the card or I'm I missing something?

thanks 2046

---

### Post by Yellow Pasque on 2011-04-15
> **o----o said:**
> What do you think of it, where is my problem?... is the Nvidia really useless and we do not have slight chance to run the card or I'm I missing something?

The Nvidia is useless. If you still can, return the system now.

---

### Post by o----o on 2011-04-15
I think NVidia is something I trust. I just have a good experience {things might not be as they were.}.

During that short time I have found couple news about this problem. First is the 11.04 is Alpha (indeed) and many people actually suffer with the same problem... that the system hangs during the normal boot "checking the battery  [ok]" even on computers without battery...it occurs mostly after the Nvidia activation. Hmm, will see.

I'll try my best to find a solution.

---

### Post by Yellow Pasque on 2011-04-15
Best solution is to return the system.
Next best is to use the Intel graphics and acpi_call method to disable Nvidia graphics card, so it doesn't suck battery and generate heat. You've then "succeeded" in making your Nvidia GPU an expensive paperweight.

---

### Post by NoVista on 2011-04-15
I would appreciate if someone would clarify this for me >>
If you own a Dell XPS15 L502X, with NV card GT 540m with Optimus, and run Ubuntu,  there is no method that works in order to get video out to work?

---

### Post by beew on 2011-04-15
> **NoVista said:**
> I would appreciate if someone would clarify this for me >>
If you own a Dell XPS15 L502X, with NV card GT 540m with Optimus, and run Ubuntu,  there is no method that works in order to get video out to work?

That's right if "getting video out to work" means using the Nvidia card. There are ways to disable the Nvidia card so that you use only the low performance Intel card without the Nvidia card sucking power, thus making it an expensive paperweight. But no way to use the Nvidia card.

You may want to write to Nvidia.

[http://ubuntuforums.org/showthread.php?t=1712278](http://ubuntuforums.org/showthread.php?t=1712278)

Some Optimus laptops have a BIO switch to disable Optimus, in that case Linux can use the Nvidia card if it has Linux driver, but this model is not one of them.

This Dell has the BIO switch and apparently works.
[http://ubuntuforums.org/showthread.php?t=1726575](http://ubuntuforums.org/showthread.php?t=1726575)

Maybe you can write to dell asking him to provide such a BIOS switch for your model too.
[ ]("http://ubuntuforums.org/showthread.php?t=1726575")

---

### Post by NoVista on 2011-04-15
Thanks for the reply.
Looks like I may have to send both of my new XPS's back then, which just arrived today.

Waiting around to see if they add a bios option to fix this on this model might be fruitless?

---

### Post by o----o on 2011-04-16
I have updated to last bios A04 but there were no visible changes.

(btw my last post disappeared... I was just basically expressing my last decision to return the computer to store, because none of the drivers I have tried works, not even Nouveau drivers. They are far from perfect(they were able to communicate with the Intel Graphic only))

---

### Post by rockorequin on 2011-04-20
So has anyone got HDMI working on this laptop via the Intel GPU?

---

### Post by rockorequin on 2011-04-24
My guess is that HDMI won't work at all on the XPS 15 L502 because it's connected to the nvidia card, not the Intel. See [https://lists.launchpad.net/hybrid-graphics-linux/msg00701.html](https://lists.launchpad.net/hybrid-graphics-linux/msg00701.html), where it says:

*Now it gets interesting... I have a display attached to HDMI which is not recognized by the intel driver. But after switching to nvidia (echo DIS > /sys/kernel/debug/vgaswitcheroo/switch) the Display starts working but the internal Display (LVDS) stops. The nvidia drivers are not installed, so nouveau is loaded. *

---

### Post by deere on 2011-04-28
Hey,

The new [Intel driver]("http://intellinuxgraphics.org/2011Q1.html") has support for Sandy Bridge graphics. Has anyone tried this driver? Is there anyone who succeeded in getting the HDMI working with this driver or any other way?

---

### Post by zeusi on 2011-04-30
I installed the 11.04 release (working with Gnome). My system completely freezes and I have to manually restart. I think this happen a few minutes after I turn off the Nvidia card. Now I'm keeping the card on to see if the problem returns. Other experiences with the script to turn off the card ?

---

### Post by rockorequin on 2011-05-04
The L502x has the HDMI connected to the nvidia card, so you can't use it at the same time as the laptop display, which is connected to the Intel iGPU. 

With the intel driver loaded and the internal screen working, xrandr --verbose shows there is nothing connected to its HDMI port (ie even when there is).

If you load the nouveau driver, the HDMI screen works but the laptop screen doesn't.

We're going to send our XPS 15s back. Dell promised that they would work with Ubuntu and pointed us to the latest nvidia drivers, but of course these don't support optimus, so they don't work. Dell's technical knowledge sucks almost as much as optimus does.

I wonder if microso$t has paid nvidia to not support optimus on linux? It's unbelievable how hard it is to find a high spec laptop these days that doesn't have an opticrap nvidia card on it.

---

### Post by cheapcomputers on 2011-05-04
Battery life on the 6 cell is excellent. I've been getting 3 and a half hours with heavy web surfing at full brightness. Also I watched Cars on Blu-ray (a 2 hour movie) with 50% screen brightness and still got 45 minutes out of it after the movie.

---

### Post by NoVista on 2011-05-04
It all means nuthin' if you can't use the video card you paid for, nor the HDMI.
I sent two of them back to Dell.

My only problem now is finding replacements for a system needing a
lighted keyboard, 2nd gen SBridge w/an I7, HD 1920 screen, killer sound, usb 3,0, blu-ray burner and HDMI, and of course a gaming fast video card without exceeding Dells current pricing.

If someone has a replacement puter for the xps15 please speak out and help me now :)
The ones from system76 are sadly too high priced.

---

### Post by beew on 2011-05-04
Someone claims he has a solution to the Optimnus problem on Nvidia's Linux forum.

[http://www.nvnews.net/vbulletin/showthread.php?t=162171](http://www.nvnews.net/vbulletin/showthread.php?t=162171)

Don't know if it works or how well it works. In the mean time you may want to write to Nvidia and Dell (for the BIOS switch to turn off Optimus)
[http://ubuntuforums.org/showthread.php?t=1712278](http://ubuntuforums.org/showthread.php?t=1712278)

---

### Post by iammeagain on 2011-05-05
> **zeusi said:**
> I installed the 11.04 release (working with Gnome). My system completely freezes and I have to manually restart. I think this happen a few minutes after I turn off the Nvidia card. Now I'm keeping the card on to see if the problem returns. Other experiences with the script to turn off the card ?

Try and see if Nvidia is still listed as being used. 
```
cat /var/log/Xorg.0.log
```
Mine still listed Nvidia, like this and a few other places:
> [     4.586] (II) Module glx: vendor="NVIDIA Corporation"
[     4.586] 	compiled for 4.0.2, module version = 1.0.0
[     4.586] 	Module class: X.Org Server Extension
[     4.586] (II) NVIDIA GLX Module  270.41.06  Mon Apr 18 15:10:15 PDT 2011
Yours could be listed elsewhere or in more than one place. I'd recommend copying it into gedit and using the find feature.

I had some crashing issues when trying to run some 3D programs because the xorg still wanted to use Nvidia. I'm not sure this will work for you but, what I ended up having to do is run the code below if it is still trying to use the Nvidia. I have an l501x though, and I disabled my nvidia because I just wanted battery life. The intel handles compiz fine for me. This just will make sure nvidia's drivers are no longer trying to be used.
```
sudo apt-get purge nvidia*
sudo apt-get install --reinstall xserver-xorg-video-intel libgl1-mesa-glx libgl1-mesa-dri xserver-xorg-core
sudo dpkg-reconfigure xserver-xorg
```


[Here]("http://ubuntuforums.org/showpost.php?p=10754116&postcount=25") is my info for the l501x to get nvidia turned off. Maybe you guys can apply it to the l502x. There is older info in the thread that could be of help, but as of May 5th that link should take you to my most recent info, it is the best way I have found to keep nvidia off and still have a fully functioning ubuntu install. Compiz does work for me just using the intel integrated graphics, but mine is a 1st gen i5, not 2nd gen.

---

### Post by beew on 2011-05-05
> [Here]("http://ubuntuforums.org/showpost.php?p=10754116&postcount=25") is my info for the l501x to get nvidia turned off. Maybe you guys can apply it to the l502x. There is older info in the thread that could be of help, but as of May 5th that link should take you to my most recent info, it is the best way I have found to keep nvidia off and still have a fully functioning ubuntu install. Compiz does work for me just using the intel integrated graphics, but mine is a 1st gen i5, not 2nd gen.
I fail to see how turning off the nvidia card you paid for and making it into an expensive paperweight a solution. It is probably the best among all bad scenarios, but it is not a workaround, much less a solution. Did you check out my link? It may or may not work but it is worth investigating.

---

### Post by iammeagain on 2011-05-06
I did check out your link. I'd like to try it out, but I need my computer usable at the moment for a project we need to present on shortly. Can't suffer any hiccups right now. It does look very promising, I hope a few people might be able to give feedback. I'll probably give it a try after a few weeks or so I'm hoping.

I don't really see the use of the nvidia on Ubuntu. The intel seems to handle the little bit I need throw at it. If I'm going to game then I have windows which I paid for by buying this laptop. If your trying to game through wine on ubuntu then doesn't your paperweight scenario apply to the Windows OS you spent money on?

I didn't say it was perfect, it was the best solution I have been able to find so far. I would like optimus working seamlessly, but the info is scarce so I am providing what I have in hopes people may be able to build off of it. There is the possibility of using the cuda processing while not using the nvidia for video from what I have read. I did place a link in my last post on that thread in case people needed it. Again this isn't something I need right now so I didn't give it priority. I am enjoying the great battery life that Ubuntu can give me running on the intel. With the brightness low and my 9 cell it estimates 6~7 hours. Some people may not care for trying to get optimus working on theirs until its known to be possible and working stably. So I'd like to provide them with another possibility to get their laptop functioning with a solution that has been tried and used successfully before.

---

### Post by rockorequin on 2011-05-06
The technique in that link is pretty cool. It provides acceleration in *almost* the same way as how optimus works in windoze by allowing you to specify which apps use the nvidia 3d acceleration. It's not quite perfect because you can't get acceleration in Gnome or KDE either through the intel or nvidia cards, so desktop effects are out of the question.

On a slightly different topic, has anyone managed to get the HDMI port working by configuring the Xorg.conf file with Xinerama? In theory X should support using the two graphics cards, the intel for the laptop screen and the nvidia for the HDMI output. I know someone who tried with nvidia-current but it crashed upon login. (Perhaps the nouveau driver would be more successful?) He was trying an /etc/X11/xorg.conf file along the lines of the following, although I'm not sure the BusID lines are accurate (you'd need to check with lspci):

```
Section "Device"
        Identifier  "intelgpu"
        Driver      "intel"
        BusID       "PCI:0:2:0"
EndSection

Section "Device"
        Identifier  "nvidia"
        Driver      "nvidia"
        BusID       "PCI:1:0:0"
	Option      "IgnoreEDID"
	# ConnectedMonitor "DFP-1" # Can uncomment this to try different options here (FPD, DFP, DFP-0, DFP-1) if it doesn't work
EndSection

Section "Screen"
    Identifier     "laptopscreen"   
    Device         "intelgpu"
    Monitor        "Monitor0"
    DefaultDepth    24
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection

Section "Screen"
    Identifier     "extscreen"   
    Device         "nvidia"
    Monitor        "Monitor1"
    DefaultDepth    24
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection


Section "ServerLayout"
    Identifier  "Default Layout"
    Screen "laptopscreen"
    Screen "extscreen" RightOf "laptopscreen"
    Option "Xinerama" "on"
    Option "Clone"    "off"
EndSection
```

---

### Post by rockorequin on 2011-05-09
Martin Juhl's software is even cooler now - it lets you use 3d accleration on the Intel chip as well! It now works almost exactly like in windoze except that you choose whether to run the application using nvidia acceleration instead of the driver choosing.

He's also made it into a self-installing app: [https://github.com/MrMEEE/bumblebee](https://github.com/MrMEEE/bumblebee)

Unfortunately it doesn't fix the HDMI problem. I did get the HDMI screen working in 2d only though using Xinerama and intel driving the laptop screen and nouveau driving the HDMI screen. The 2d part is I assume because Ubuntu 11.04 doesn't yet include the gallium3d support for nouveau. The screen turns on in 3d mode and the mouse gets drawn but when you drag windows to it, they disappear.

Dell thinks though that a mini-display-port-to-HDMI adapter might let you use HDMI as apparently the display port is attached to the intel chip, not the nvidia.

---

### Post by teczito on 2011-05-10
Nice that you got the HDMI working. Could you describe the steps that you took to get it working?

Currently I run Ubuntu 11.04 on a VM in the OS that was shipped with the computer, when I want to use the HDMI port. Would be nice to not have to boot into that OS at all !! 

Thanks in advance.

---

### Post by rockorequin on 2011-05-10
> **teczito said:**
> Nice that you got the HDMI working. Could you describe the steps that you took to get it working?

Currently I run Ubuntu 11.04 on a VM in the OS that was shipped with the computer, when I want to use the HDMI port. Would be nice to not have to boot into that OS at all !! 

Thanks in advance.


I used an /etc/X11/xorg.conf file similar to the one I posted above in comment #51, except that instead of Driver "nvidia" I used Driver "nouveau". Note that you need to uninstall nvidia-current if it is already installed.

I also had to add a 'Modes' line specifying the monitor resolution, as the nouveau driver didn't detect it properly:

```
Section "Screen"
    Identifier     "extscreen"   
    Device         "nvidia"
    Monitor        "Monitor1"
    DefaultDepth    24
    SubSection     "Display"
        Depth       24
	Modes      "1680x1050"
    EndSubSection
EndSection
```

Finally, note that this will only work if you login to classic mode (no effects) or unity2d because Ubuntu's nouveau is currently not supporting 3d.

BUT... an even better solution is to buy a mini-displayport-to-hdmi adapter. We checked it out just now and Ubuntu picked up the display connected to it automatically. And this means you get 3d effects *and* you can still use the bumblebee driver to use nvidia-optimus if you want nvidia acceleration.

Another point to note is that if I run kernel 2.6.39 (currently at 2.6.39-rc7) instead of the default 2.6.38 kernel, I get better Intel 3d acceleration in Unity (2.6.38 seems to pause every now and again).

---

### Post by asn_knight on 2011-05-11
Can anybody explain how can I turn Nvidia GPU off...??
I anyway use Ubuntu for light tasks and wouldnt mind working just on Intel card. The battery performance will also be better I hope.

And would Unity 3d work on the Intel card or would I have to install Unity-2D..??

---

### Post by deere on 2011-05-12
Hello,
Does this provide the ability to use multiple displays displaying different output?
I mean something like twin view which I used with my nvidia cards.
Does this work with the intel card using the mini display port as an output for a second display?


> **rockorequin said:**
> 
BUT... an even better solution is to buy a mini-displayport-to-hdmi adapter. We checked it out just now and Ubuntu picked up the display connected to it automatically. And this means you get 3d effects *and* you can still use the bumblebee driver to use nvidia-optimus if you want nvidia acceleration.


---

### Post by rockorequin on 2011-05-12
> **asn_knight said:**
> Can anybody explain how can I turn Nvidia GPU off...??
I anyway use Ubuntu for light tasks and wouldnt mind working just on Intel card. The battery performance will also be better I hope.

To turn off the nvidia card, you need to compile the acpi_call module for your kernel:

```
# Install dependencies
sudo apt-get update && sudo apt-get install build-essential git-core linux-headers-`uname -r`
# Get acpi_call from git
git clone http://github.com/mkottman/acpi_call.git
# Make and install it
cd acpi_call
make
# Install module
sudo insmod acpi_call.ko

```

To make the module load automatically at boot, you probably need to add acpi_call to /etc/modules. As well, I think you'd need to re-make and re-install the module if your kernel gets upgraded.

You can then use the script here: [http://ubuntuforums.org/showpost.php?p=10643195&postcount=23](http://ubuntuforums.org/showpost.php?p=10643195&postcount=23) to turn the card off and on (or you can use the test.sh script that comes with the code if you just want to turn it off).

Warning: I tried it and it seemed to work fine, but a minute or so later the entire machine hung. It could have had something to do with the fact that I was running the virtualgl server at the time, but I think people posted earlier in this thread that they had this issue.

> And would Unity 3d work on the Intel card or would I have to install Unity-2D..??

Normally Unity works just fine on the Intel card. If it doesn't, you probably need to uninstall the nvidia-current driver (with sudo apt-get remove nvidia-current) - the Ubuntu installer might have installed this for you when it saw the nvidia card.

---

### Post by rockorequin on 2011-05-12
> **deere said:**
> Hello,
Does this provide the ability to use multiple displays displaying different output?
I mean something like twin view which I used with my nvidia cards.
Does this work with the intel card using the mini display port as an output for a second display?

Yes, with an external monitor attached you can use either gnome-display-properties (the standard Ubuntu monitors tool - in the Dash, type 'monitor' and look for Monitors - you can then tell it to stay permanently in the indicator tray) or xrandr to detect and set the multiple monitor setup (left, right, above, below, or cloned).

I found that if you use a mini-displayport-to-HDMI adapter, gnome-display-properties auto-detects the available resolutions of the external monitor, but if it's mini-displayport-to-VGA you might have to manually tell Ubuntu the native resolution using xorg.conf or xrandr (eg with something like xrandr --addmode VGA1 1680x1050_60.00). I think that's pretty standard for VGA, though. I've had to do the same for VGA monitors using nvidia.

It does work with different resolutions (I had it running with the laptop at 1920x1080 and an external monitor at 1680x1050) but I found that sometimes Unity gets a bit confused when you try it. It might just be a refresh thing in compiz. I found that if it doesn't work first up, changing the resolution (eg both to 1680x1050) and then back again often fixes it.

---

### Post by jporta on 2011-05-12
I just had a chat with a Dell representative that confirmed me that the XPS 15 l502x HAS a BIOS setting to disable Optimus.

Find the chat pdf attached.

Hope this helps-

---

### Post by rockorequin on 2011-05-12
> **jporta said:**
> I just had a chat with a Dell representative that confirmed me that the XPS 15 l502x HAS a BIOS setting to disable Optimus.

Find the chat pdf attached.

Hope this helps-

And a Dell rep once told me that the L502x doesn't even have optimus! Unfortunately he was mistaken. Perhaps you could ask your rep for specifics: where exactly in the BIOS is this setting? I certainly can't find anything like that in my BIOS.

---

### Post by amemes on 2011-05-13
I also have a L502x since 1 day but I didn't find this setting in the bios. 
Btw I have the full hd display but when playing video files (720p,1080p or even just dvd quality) the video is sometimes lagging in fast scenes. Anybody else experiencing this problem? Seems like the intel driver performance isn't good enough.   I am running 64-bit 11.04.

---

### Post by Borgoz on 2011-05-14
Absolutely not.
In the xps is not possible to switch off the intel card in bios settings. This laptop doesn't have a mux, so the intel card is the only one connected to the screen, ergo you cannot turn it off.

---

### Post by amemes on 2011-05-16
FYI 1080p playback is working fine with "mplayer -vo gl -dr -noslices". 
Also spdif ac3 passthrough is working. 
Only thing that isn't working yet is fancontrol but that's not a big issue.

---

### Post by protagon on 2011-05-17
Hello Everyone !

I have question about full hd resolution.
Can we set 1920x1080 on intel video card in this laptop ?

---

### Post by rockorequin on 2011-05-17
> **protagon said:**
> Hello Everyone !

I have question about full hd resolution.
Can we set 1920x1080 on intel video card in this laptop ?

Yes, we can! Ubuntu 11.04 can display 1920x1080 through the mini displayport just fine as well (certainly with a mini-displayport-to-hdmi adapter. I'm not sure it works so well with a mini-displayport-to-VGA adapter, though).

---

### Post by rockorequin on 2011-05-20
If anyone's interested, the following script works with bumblebee and acpi_call on my L502x to (manually) turn off the nvidia card if you aren't using it and turn it back on automatically if you want to use 3d acceleration on the nvidia. I find power usage as reported by powertop drops from around 1.8-1.9W down to 1.4W-1.5W with the card off.

I keep it in /usr/bin/nv. It acts like optirun64 except that (1) the argument 'off' will turn off the nvidia card, (2) it will turn the card back on and restart bumblee if necessary when running an app, and (3) it runs the 32 bit version if you are running wine:

```
# Turn the nvidia card card off
nv off 
# Run glxgears using nvidia acceleration
nv glxgears
```

The trick to avoiding a kernel lockup is to offload the nvidia module before turning the card off.

For acpi_call, see [http://linux-hybrid-graphics.blogspot.com/2010/07/using-acpicall-module-to-switch-onoff.html:](http://linux-hybrid-graphics.blogspot.com/2010/07/using-acpicall-module-to-switch-onoff.html:)

```
git clone http://github.com/mkottman/acpi_call.git
cd acpi_call
make
sudo insmod acpi_call.ko
```

or see comment #67 below to try and install it permanently.

Script:

```
#!/bin/bash
# This must match the PIDFILE in /etc/init.d/bumblebee
BUMBLEBEE_PIDFILE=/tmp/.X1-lock

# Check if nvidia card is enabled.
NVIDIA=$(lsmod|grep nvidia)
# Test whether bumblebee thinks it is running
if [ -e $BUMBLEBEE_PIDFILE ]; then
  BUMBLEBEE=1
else
  BUMBLEBEE=0
fi

# XPS 15 ACPI command
COMMAND="\_SB.PCI0.PEG0.PEGP"

# This turns the nvidia card on or off using $COMMAND
# Pass ON or OFF as the argument
function nvidia_acpi {
  if ! [ -e "/proc/acpi/call" ]; then
    echo "ERROR: The acpi_call module must be available to turn the nvidia card $1"
    exit 1
  fi

  echo "Attempting to turn nvidia card $1"
  cmd="echo \"$COMMAND._$1\" > /proc/acpi/call"
  sudo sh -c "$cmd"
  result=$(cat /proc/acpi/call)
  case "$result" in
  Error*)
    echo "*** ACPI_CALL $result"
    exit 2
  ;;
  not*called)
    echo "*** Error calling ACPI_CALL"
    exit 3
  ;;
  *)
    echo "nvidia card is $1"
  ;;
  esac
}

# Are we being asked to turn it off?
if [ "$1" == "off" ]; then
  # Shutdown bumblebee
  if [ $BUMBLEBEE == 1 ]; then
    echo "Stopping bumblebee server"
    sudo /etc/init.d/bumblebee stop
  fi

  if [ "$NVIDIA" != "" ]; then
    if ! [ -e "/proc/acpi/call" ]; then
      echo "ERROR: acpi_call must be available"
      exit 1
    fi
    # Unload the module so it doesn't try to access the card
    echo "Unloading nvidia module"
    # Note you can't do it immediately because it's still in use until bumblebee stops completely
    retries=0
    while [ 1 ]; do
      sleep 0.5      
      # Note that you can't remove nvidia-current because the module calls itself nvidia.      
      sudo rmmod nvidia 2>/dev/null
      result=$?
      if [ $result == 0 ]; then break; fi
      ((retries=retries+1))
      if [ $retries == 5 ]; then
        echo "*** ERROR unloading nvidia module, aborting"
        exit 4
      fi
    done
  fi
  
  # Send command for XPS 15
  nvidia_acpi 'OFF'
  exit 0
fi

if [ "$NVIDIA" == "" ]; then
  nvidia_acpi 'ON'

  # Load the nvidia module
  set -e
  sudo modprobe nvidia-current
  set +e
fi

# Restart bumblebee if required
if [ $BUMBLEBEE == 0 ]; then
  echo "Starting bumblebee"
  set -e
  sudo /etc/init.d/bumblebee start
  set +e
fi

if [ "$1" == "on" ]; then
  # Don't run anything.
  exit 0
fi

if [ "$1" == "wine" ]; then
  # Run the 32 bit version instead
  vglrun -ld /usr/lib32/nvidia-current $1 $2 $3 $4 $5 $6 $7 $8
else
  vglrun -ld /usr/lib64/nvidia-current $1 $2 $3 $4 $5 $6 $7 $8
fi
```

---

### Post by rockorequin on 2011-05-20
Re the nv script that turns the nvidia card on and off for bumblebee, I think I've managed to install the acpi_call module permanently using dkms. You need a dkms.conf file like so:

```
PACKAGE_NAME="acpi_call"
PACKAGE_VERSION="0.0.1"
# In case this is included in the 2.6.40 kernel...
OBSOLETE_BY=2.6.40
CLEAN="make clean"
BUILT_MODULE_NAME[0]="acpi_call"
DEST_MODULE_NAME[0]="acpi_call"
MAKE[0]="make IGNORE_CC_MISMATCH=1 KDIR=$kernel_source_dir PWD=$dkms_tree/acpi_call/0.0.1/build"
DEST_MODULE_LOCATION[0]="/kernel/drivers/acpi"
AUTOINSTALL="yes"

```

Then to install it:

```
sudo apt-get install dkms
git clone [http://github.com/mkottman/acpi_call.git](http://github.com/mkottman/acpi_call.git)
mkdir /usr/src/acpi_call-0.0.1
```

Then edit the Makefile to contain:

```

obj-m := acpi_call.o

default: 
	$(MAKE) -C $(KDIR) SUBDIRS=$(PWD) modules

clean:
	rm acpi_call.mod.o acpi_call.o acpi_call.ko

load:
	-sudo /sbin/rmmod acpi_call
	sudo /sbin/insmod acpi_call.ko
```

and run the following commands to create a source folder for it, add it to dkms, build and install it:

```

cp -rp acpi_call/* /usr/src/acpi_call-0.0.1
cp dkms.conf /usr/src/acpi_call-0.0.1
dkms add -m acpi_call -v 0.0.1
dkms build -m acpi_call -v 0.0.1
dkms install -m acpi_call -v 0.0.1
```

If it all works, you should be able to add acpi_call to /etc/modules or add 'modprobe acpi_call' to the /usr/bin/nv script when it's needed.

---

### Post by asn_knight on 2011-05-20
> **rockorequin said:**
> To turn off the nvidia card, you need to compile the acpi_call module for your kernel:

```
# Install dependencies
sudo apt-get update && sudo apt-get install build-essential git-core linux-headers-`uname -r`
# Get acpi_call from git
git clone http://github.com/mkottman/acpi_call.git
# Make and install it
cd acpi_call
make
# Install module
sudo insmod acpi_call.ko

```

To make the module load automatically at boot, you probably need to add acpi_call to /etc/modules. As well, I think you'd need to re-make and re-install the module if your kernel gets upgraded.

You can then use the script here: [http://ubuntuforums.org/showpost.php?p=10643195&postcount=23](http://ubuntuforums.org/showpost.php?p=10643195&postcount=23) to turn the card off and on (or you can use the test.sh script that comes with the code if you just want to turn it off).

Warning: I tried it and it seemed to work fine, but a minute or so later the entire machine hung. It could have had something to do with the fact that I was running the virtualgl server at the time, but I think people posted earlier in this thread that they had this issue.


But isn't just Bumblebee setup enough?


PS : Also @rockorequin please post a step by step procedure I would need to off Nvidia - [[COLOR="Red"]_here_[/COLOR]]("http://ubuntuforums.org/showthread.php?t=1763271")

The acpi and bumblebee ideas keeps confusing for me! :)

---

### Post by rockorequin on 2011-05-20
> **asn_knight said:**
> But isn't just Bumblebee setup enough?


Not yet - at the moment bumblebee provides 3d acceleration, but the nvidia card is always on, so you need to install acpi_call and use it if you want to disable the card.

It's in bumblebee's issue list as a feature request, though.

If you just want to turn the nvidia card off, you don't need to install bumblebee or nvidia-currrent. You should be able to just install acpi_call and call the script above (or the relevant lines from it) to turn the card off ('nv off'). Or the test.sh script that comes with acpi_call should also do it. You could create an init.d script to call it at startup.

---

### Post by rockorequin on 2011-05-20
> **rockorequin said:**
> Not yet - at the moment bumblebee provides 3d acceleration, but the nvidia card is always on, so you need to install acpi_call and use it if you want to disable the card.

It's in bumblebee's issue list as a feature request, though.

If you just want to turn the nvidia card off, you don't need to install bumblebee or nvidia-currrent. You should be able to just install acpi_call and call the script above (or the relevant lines from it) to turn the card off ('nv off'). Or the test.sh script that comes with acpi_call should also do it. You could create an init.d script to call it at startup.

So, progress is moving along rapidly - now the acpi_call code to automatically turn the card on and off is in bumblebee!

You still need to install acpi_call (see comment #67) and edit two files, /usr/local/bin/bumblebee-enablecard and bumblebee-disablecard so they look like so:

bumblebee-enablecard:
```

#!/bin/bash
# This script should contain the command(s) nessesary to switch on the
# nVidia card.
# As an example i've included the script for my Alienware M11X R2..
# Please note that the acpi_call module is need for these operations:
#
# http://linux-hybrid-graphics.blogspot.com/2010/07/using-acpicall-module-to-switch-onoff.html

modprobe acpi_call

if ! lsmod | grep -q acpi_call; then
    echo "Error: acpi_call module not loaded"
    exit
fi

acpi_call () {
    # This is for XPS 15
    echo "\_SB.PCI0.PEG0.PEGP._ON" > /proc/acpi/call
    cat /proc/acpi/call
}

acpi_call
modprobe nvidia-current
```


bumblebee-disablecard:
```
#!/bin/bash
# This script should contain the command(s) nessesary to switch off the
# nVidia card.
# As an example i've included the script for my Alienware M11X R2..
# Please note that the acpi_call module is need for these operations:
#
# http://linux-hybrid-graphics.blogspot.com/2010/07/using-acpicall-module-to-switch-onoff.html

modprobe acpi_call
if ! lsmod | grep -q acpi_call; then
    echo "Error: acpi_call module not loaded"
    exit
fi

rmmod nvidia

if lsmod | grep -q nvidia; then
    echo "Error: failed to remove nvidia module"
    exit
fi

acpi_call () {
    # This is for XPS 15
    echo "\_SB.PCI0.PEG0.PEGP._OFF" > /proc/acpi/call
    cat /proc/acpi/call
}

acpi_call

```

---

### Post by siftu on 2011-05-24
Hi have installed this and got it working on Arch Linux but I'm not impressed with it's performance, but maybe its something in my setup. What figures are you guys getting with glxgears? I get like 500-600fps using the Nvidia which the onboard intel can do with the new kernels and disabling vblank.

---

### Post by Tos_Phoenix on 2011-05-26
> **siftu said:**
> Hi have installed this and got it working on Arch Linux but I'm not impressed with it's performance, but maybe its something in my setup. What figures are you guys getting with glxgears? I get like 500-600fps using the Nvidia which the onboard intel can do with the new kernels and disabling vblank.

glxgears isn't a benchmark tool!

use lightsmark for example, provided here: [http://www.dee.cz/lightsmark/](http://www.dee.cz/lightsmark/)

there i got an average of 82fps with the nvidia card and 22fps with my intel card

---

### Post by rockorequin on 2011-05-28
You can also display the frame rate in Alien Arena. I get 25-30fps at best with the intel, and 50fps or better with the nvidia card.

As an example of how glxgears is not a great comparison tool, if I run it on an old nvidia 8600M card on a core duo machine, I get around 3400fps in Ubuntu 11.04. The 540M shows anywhere between 200 and 800fps (not even 25% as high!) on an i7. Yet the 540M is considerably more powerful than the 8600M, which shows up as much better framerates in games.

Edit: with the latest drivers from the xorg edgers code, I can get 30-35fps with the intel gpu.

---

### Post by NoVista on 2011-06-07
I need clarification on these questions regarding the Dell XPS 15/17 >>
1. We can now turn either the integrated graphics, or the nVidia GT 555/540 on and off at will.
2. Will the HDMI out now work to clone the display to a larger screen?
I don't want to extend it, but clone it.
3. Will the HDMI also pass through the audio?

I ask because I returned two of these early on, when there was no way to use the dedicated card, but I presume now you can. I am considering re-buying this new again, as long as things are now working ok.
But I need to make sure, hence why I am asking :)

---

### Post by rockorequin on 2011-06-08
> **NoVista said:**
> I need clarification on these questions regarding the Dell XPS 15/17 >>
1. We can now turn either the integrated graphics, or the nVidia GT 555/540 on and off at will.
2. Will the HDMI out now work to clone the display to a larger screen?
I don't want to extend it, but clone it.
3. Will the HDMI also pass through the audio?

I ask because I returned two of these early on, when there was no way to use the dedicated card, but I presume now you can. I am considering re-buying this new again, as long as things are now working ok.
But I need to make sure, hence why I am asking :)


1. You can turn on both if you use bumblebee, and selectively use the nvidia card for acceleration. Output is still displayed on the intel gpu. You can turn the nvidia card off, but not the intel gpu.

2. The HDMI port will only work if you use the nouveau driver and configure your xorg.conf to use it on the nvidia card (and you can't use 3d effects or the nvidia driver if you do that). Search this thread for my posts on how that works.

However, a better solution is to use the mini-displayport and get an adapter cable for your HDMI monitor. The mini-displayport is connected to the intel chip so you'll need no special configuration to get it working.

---

### Post by NoVista on 2011-06-09
Thanks for clearing all that up for me.
Looks like this is still not the laptop for me then.

I've already taken a very bad view of Optimus.
All this time waiting on the I7's, then the fixed chip-sets,
but only to find out Optimus still gunks it up.
I am also hearing those on the Windows platform are having their own problems with it.
I had been waiting to finally switch back to an Intel system after over 10 years, but alas now AMD still looks better when they release their newer hardware this year, so I am still waiting on what to buy.
Very frustrating.

---

