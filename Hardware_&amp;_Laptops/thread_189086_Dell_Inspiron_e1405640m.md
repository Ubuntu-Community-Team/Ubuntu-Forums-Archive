---
title: "Dell Inspiron e1405/640m"
date: 2006-06-04
forum: Hardware &amp; Laptops
---

### Post by MarioFuentes on 2006-06-04
Hi

I installed Ubuntu Dapper on my 640m laptop, It's Ok, but have small problems, and I create this post for sharing the knowledge about this laptop.

List of knowledge problems viewed by me:
[LIST]
[*]Installation process: during the installation, when X is probed, screen is put black and keyboard not response, but installation process continue, patience. 
[*]Graphic Driver for 945GM: XV not work, play big videos with XV support cause an error "X11 error: BadAlloc (insufficient resources for operation)".
[*]Sound Blaster Audigy Advanced HD: optional sound card on this laptop (I have this), Ubuntu uses "snd_hda_intel" module, but I don't know if this module uses the sound blaster or the integrated sound.
[*]Hibernate (suspend to disk): this option appears in the logout menu, but resume the hibernate isn't possible.
[*]Sleep (suspend to ram): not supported.
[*]Touchpad: sensibility of the touch click is bad.
[/LIST]

If any have this laptop, or know how fix that problems, please share your knowledge.

---

### Post by bjtuna on 2006-08-23
When I ran the installation, my screen also went black when X was probed. I could tell from the HDD lights that the installation was continuing but the screen never came back, even after activity stopped. How did you complete the installation?


> **MarioFuentes said:**
> Hi

I installed Ubuntu Dapper on my 640m laptop, It's Ok, but have small problems, and I create this post for sharing the knowledge about this laptop.

List of knowledge problems viewed by me:
[LIST]
[*]Installation process: during the installation, when X is probed, screen is put black and keyboard not response, but installation process continue, patience. 
[*]Graphic Driver for 945GM: XV not work, play big videos with XV support cause an error "X11 error: BadAlloc (insufficient resources for operation)".
[*]Sound Blaster Audigy Advanced HD: optional sound card on this laptop (I have this), Ubuntu uses "snd_hda_intel" module, but I don't know if this module uses the sound blaster or the integrated sound.
[*]Hibernate (suspend to disk): this option appears in the logout menu, but resume the hibernate isn't possible.
[*]Sleep (suspend to ram): not supported.
[*]Touchpad: sensibility of the touch click is bad.
[/LIST]

If any have this laptop, or know how fix that problems, please share your knowledge.

---

### Post by NooneReally on 2006-08-24
I just got one of these a week or so ago and the installation went completely without a hitch. I used the 6.06-1 dvd release.


> **MarioFuentes said:**
> Hi
[*]Installation process: during the installation, when X is probed, screen is put black and keyboard not response, but installation process continue, patience. 


the screen is widescreen therefore it throws X for a loop. install in safe mode and theres no problems.


> **MarioFuentes said:**
> Hi
[*]Graphic Driver for 945GM: XV not work, play big videos with XV support cause an error "X11 error: BadAlloc (insufficient resources for operation)".


yup, graphic driver is shiite...but luckily intel has OSS drivers for the chipset now and they work very nicely. You might try and bump up your shared memory as well, mine defaulted to 8MB so I knocked it up to 256.

> **MarioFuentes said:**
> Hi
[*]Sound Blaster Audigy Advanced HD: optional sound card on this laptop (I have this), Ubuntu uses "snd_hda_intel" module, but I don't know if this module uses the sound blaster or the integrated sound.


lol...ok, you realize the audigy advanced hd junk is just software thats installed for windoze right? I imagine your settings are fine here ;) 

> **MarioFuentes said:**
> Hi
[*]Hibernate (suspend to disk): this option appears in the logout menu, but resume the hibernate isn't possible.
[*]Sleep (suspend to ram): not supported.


these worked perfect for me right away. Suspend works in every fashion resuming in a few seconds. Hibernation however is a bit different and took me an extra reboot to notice how it works....I select hibernation and in about 20s the machine shuts off, then upon power-up the machine appears to be doing a normal boot but stops at 'mounting root file system' and at this point loads the hibernated session whereby you're greeted (or i am at least) with a locked screensaver.

> **MarioFuentes said:**
> Hi
[*]Touchpad: sensibility of the touch click is bad.


i hate touchpad click so i shut that off immediately:D 
add "MaxTapTime" "0"
on the line below "Driver "synaptics"

---

### Post by alan53 on 2006-08-29
I have the subject system and am re-installing Ubuntu after finding  it will permit me to do whatever I used to do in Windows.

Initially, I had to use the terminal to get X to recognize a generic (vesa)monitor:
sudo dpkg-reconfigure xserver-xorg

Other than adding the monitor and telling it to go for the highest resolution possible, everything else I left to default.

I've changed the kernel from 386 to 686 (via Synaptic) and have just installed the package called 915resolution.  So far so good.  I re-started X (ctrl-alt-backspace) and my resolution is what it is supposed to be.

I'll add more when and if I run across more problems.  I'm sure I will as I also need to add wine and have found upgraded (Linux) Intel drivers [HERE]("http://tinyurl.com/kcvln") which I have not yet discovered how to unpack or install.

Can this thread be combined with [THIS ONE?]("http://ubuntuforums.org/showthread.php?t=244628") or did I just do that?

Alan

---

### Post by el3ktro on 2006-09-06
I have an Averatec 2460, it has an Intel 945GM chipset, Intel GMA 950 graphics, onboard RealTek 8193 NIC and Intel 3945ABG wireless - and I can't install Ubuntu on it - it always hangs. This sucks so much. I've finally got Gentoo to install on it, and my NIC, graphics & wireless work but damn I want Ubuntu!! This is so annoying because all my hardware works perfectly now, it's just that the installer of Ubuntu does something strange and won't boot. Has anyone experienced the same with an Intel 945GM & Core Duo?

Tom

---

### Post by alan53 on 2006-09-06
!. Your machine boots from CD first?
2. CD is dirty/borked? (Scan disk?)
3. Absolutely nothing happens when you try to boot from CD?

Sorry, no answers, just questions that may lead somewhere.

Alan

---

### Post by arijarot on 2006-09-06
could you guys update your experiences/opinions of using ubuntu on your 640m ... i'm looking into this laptop for dapper ([http://ubuntuforums.org/showthread.php?t=252106](http://ubuntuforums.org/showthread.php?t=252106) ; i have a poll setup8) )

thanks :D

---

### Post by el3ktro on 2006-09-07
> **alan53 said:**
> !. Your machine boots from CD first?
2. CD is dirty/borked? (Scan disk?)
3. Absolutely nothing happens when you try to boot from CD?

Sorry, no answers, just questions that may lead somewhere.

Alan

Hi,
well as I said, the install CD hangs at hardware detection. When I try the alternate install CD, it also hangs at hardware detection (when detecting network hardware). When I skip networking setup then it hangs at harddisk detection (before loading the partitioning tool).

On Gentoo, the system freezes when I load the 8139too module which is needed for my onboard NIC - soI *think* it's this module. I managed to install Gentoo networklessand compiled my own kernel afterwards. When I compile 8139too with the "MMAP" option then it loads and works perfectly.

So it seems that all my hardware is perfectly supported, it's just that this damn installer does something wrong and doesn't let me install Ubuntu. I didn't found a way to tell the installer to NOT load this one single module - I bet this would solve all my problems. Is there any other alternative Ubuntu installation method?

Tom

---

### Post by alan53 on 2006-09-07
Dang, I forgot about that.  Mine hung there as well, then said something about not finding a network/internet connection, "Do you want to try to configure it manually?"  Yes, I gave it my IP address, the address of the Domain Name Server along with the security settings and we were off to the races.

Alan

---

### Post by arijarot on 2006-09-07
NooneReally: Since you seem to report a positive install on the 640m, would you say that your experiences with the 640m are the same?

---

### Post by luzmala on 2006-09-16
Hi all,
I have installed ubuntu with no pain, the 386 kernel, then changed to 686, 915 resolution, is all fine and working.....but my ipw3945 only works with open networks, no wep, if you put a wep key the signal disapers, iven if still detects the nets arrownd.
After much reading aparently the only solution is to compyle the driver manualy, but there are some problems....to much for my knowledge, will see. If any other solution will be happy to learn!!

---

### Post by mejrum on 2006-10-10
Iuzmala:
Try to install "Network Manager". With that I have perfect wireless functionality with WEP.
(Dell Inspiron e1405/640m, duo core)

---

### Post by johnnyloot on 2006-12-05
network manager really helps for general connections (including wep) 

Connecting to networks (i.e. University) that require a login in the browser are a whole other issue I could not conquer

---

### Post by Quillz on 2007-01-01
> **johnnyloot said:**
> network manager really helps for general connections (including wep) 

Connecting to networks (i.e. University) that require a login in the browser are a whole other issue I could not conquer
I have an E1405 that I was considering running Ubuntu 6.10 on. When you refer to the "network manager," are you referring to a program within Ubuntu? Is the included wireless card within the notebook computer compatible with Ubuntu? If not, is it possible to find a Linux-based driver that would make it compatible? Also, you can't connect to your university's network at all? That's bad news for me, as I would need to be able to connect to my university's network for a myriad of reasons.

---

### Post by tschneiter on 2007-02-01
> **Quillz said:**
> I have an E1405 that I was considering running Ubuntu 6.10 on. When you refer to the "network manager," are you referring to a program within Ubuntu? Is the included wireless card within the notebook computer compatible with Ubuntu? If not, is it possible to find a Linux-based driver that would make it compatible? Also, you can't connect to your university's network at all? That's bad news for me, as I would need to be able to connect to my university's network for a myriad of reasons.

The wireless card varies within the 640m/e1405, however, you should be able to find a driver for all of them. I had to use ndiswrapper with mine (dell draft n wifi minicard), after which I installed wifi-radar to set up the connections. Network Manager is another extra piece of software, not the one within ubuntu, but found in synaptic. Havent tried wep, but wpa works perfectly. Also had no trouble connecting to my university network, but dont forget that you'll probably need to run VPN software.

---

### Post by bigfatdummy on 2007-03-28
I just installed 7.04 on my E1405 and it had the same graphics issue which was quickly resolved using the same fix listed above.  

sudo apt-get install 915resolution


Thanks a million. I tried 4 other versions of Linux but its just not Ubuntu.

---

