---
title: "Install help on a Gateway LT3103u (AMD)"
date: 2009-08-07
forum: Installation &amp; Upgrades
---

### Post by Sweyn on 2009-08-07
Hello there,
I recently purchased a Gateway LT3103u which has Windows Vista installed on it. I installed the BETA of Windows 7 to try it out, found it lacking and I am now trying to install Ubuntu on the lil guy. I downloaded it, mounted the image, and ran the program (The LT3103u doesn't have a disk drive.)
After trying that, I tried booting it off of a thumb drive, but I kept getting an error message that forced a reboot on the computer. Whenever I try to boot linux I get the following message.

```
[ 0.784002]..MP-BIOS bug: 8254 timer not connected to IO-APIC
[ 3.284012] ata1: softreset failed (device not ready)
[ 5.099842]Power now-k8:BIOS error-no PSB or ACPI-PSS objects
BusyBox v.1.10.2 (Ubuntu 1:1.10.2-2ubuntu7) built-in shell (ash)
```

If anyone can point me in the direction of any drivers that need to be downloaded, or any BIOS things needed to be fiddled with it would be greatly appreciated. I'm new to Linux, and fiddling with computers so I don't want to screw anything up.

Thanks a million,
Sweyn

---

### Post by rspangler on 2009-08-09
I have the same issue.  I've trying to install from SD.

---

### Post by petersra on 2009-08-10
I have submitted a bug report on this issue.

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/411412](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/411412)

---

### Post by brhokla on 2009-08-11
I was able to install Ubuntu on my little Gateway LT3103u and worked fine.  I love it but I can't get the wifi to work.  Not sure how to install drivers or whatever I need on Ubuntu.  It's like a foreign language to me.

---

### Post by petersra on 2009-08-12
I believe that the earlier LT3103's worked OK with the original Phoenix BIOS Phoenix v1.3103. However, later units have the Phoenix BIOS v1.3201, and I believe that is where the problem is. It is interesting that ubuntu 8.04 boots OK with the live CD

---

### Post by antimat82 on 2009-08-13
Hello, I'm new to these forums.

For what it is worth, I believe this is a mounting issue with the USB drive for this particular distro and netbook, going through verbose install it was hanging up when attempting to mount (I had to add "noapic" and disable "quiet" to get that far in verbose).  If you want to get 9.04 on the LT3103u, I would highly suggest doing a network install, as that is how I got it onto my LT3103u after numerous attempts.  

Still getting the same errors as stated above on every successive boot of the OS, but adding the command "noapic" usually will get rid of those errors for me.

---

### Post by antimat82 on 2009-08-13
> **brhokla said:**
> I was able to install Ubuntu on my little Gateway LT3103u and worked fine.  I love it but I can't get the wifi to work.  Not sure how to install drivers or whatever I need on Ubuntu.  It's like a foreign language to me.

Open up a terminal and type:

```
sudo apt-get install linux-backports-modules-jaunty
```

Might have to require a reboot, but it should activate your wireless for you, just make sure it is on.

---

### Post by ufoDziner on 2009-08-17
I can get mine to boot fine from the USB stick, and have installed the backports.  However, I still cannot get the wireless to come up.  It has been many years sincec I have run linux, so I'm a bit sketchy on the commands, etc...  Any help is appreciated.

---

### Post by sg_57 on 2009-08-19
> **petersra said:**
> I believe that the earlier LT3103's worked OK with the original Phoenix BIOS Phoenix v1.3103. However, later units have the Phoenix BIOS v1.3201, and I believe that is where the problem is. It is interesting that ubuntu 8.04 boots OK with the live CD

Initially was having the same issue with my little machine, but I think I found a workaround. (not very elegant,but it got me there)
For the benefit of those who may have this machine, here is a brief step-by-step of what I did.

**OS Install Solution:** Went for it the roundabout way, first installing 8.10 from external DVD, and then upgrading it to 9.04 once the OS is installed.
GRUB works OK, basic Bluetooth on external Rocketfish dongle, USB mouse functional with scrolling as well, X configuration detected correctly, but no joy 
on the Atheros ar5b95 wireless. Then added all of the Medibuntu stuff, including Flash, Acrobat Reader, codecs, and so on....

**Wireless Network Adaptor:** Just needed to add the backports repository to sources list, and install *linux-backports-modules-jaunty* and after a 
reboot the wireless network adaptor is functional and appears to be detecting and connecting to networks immediately, hopefully this will stay that way! 

**Sound, Skype, Camera:** Just installed Skype-static from Medibuntu, and once again everything just worked right out of the box, (wow!)
using Plantronics USB headset as sound device, with [USB-headphones-OSS] selected in the 'Sound' control panel as input and playback devices. 
Passed Skype Test Call with flying colors the first time I tried.  Regular music is playing to the destination I am sending it to in media player as well. 

Not sure about ACPI, it is definitely not looking like it is supported, so I wonder how much life one could squeeze out of a battery?
Also, I guess that I should look into the Synaptics trackpad, to see if gestures are supported?

Overall, really well done!! Very impressed. Things feel reasonably snappy, especially when compared to the default Windows Vista install.
I wonder what a Jaunty 64-bit install would have been like?

sg

---

### Post by Minimalist360 on 2009-08-23
I've posted this on one other thread, I hope I'm not going to upset anyone. Here is some additional information about power management.

			 		   		 		 		re: power management...

Apparently [this guy]("http://www.pow.za.net/index.html") figured out how to get power management working on the Gateway LT3103u under Linux (Gentoo). He doesn't say whether he's submitted his changes, and I don't know enough about Linux to know where power management resides, but I'd imagine it's a kernel level thing. I'd love to see that incorporated into future kernels or appropriate modules, but I have no idea how to go about doing that.

So I thought I'd post the info here in case someone else can handle that.

---

### Post by Footer on 2009-08-28
> **sg_57 said:**
> I wonder what a Jaunty 64-bit install would have been like?

sg

Thanks for your step-by-step.  I picked up one of these little gems this week and saw your comment and thought I'd add my .02.  As for a 64-bit Jaunty install ... no go.  I first tried Kubuntu 9.04 64-bit from memory stick (using UNetbootin) and had the ACPI issues.  Tried passing several different kernel parameters but it wouldn't boot.

Then I read somewhere that 9.10 Karmic works so I tried Kubuntu 9.10 64-bit and was still having the non-boot issue.  So I decided to just go with Ubuntu 9.10 64-bit (Alpha 4) and it worked!  Since I'm a KDE fan, I installed kubuntu-desktop and now have what I want except ...

The wireless doesn't work and there is the power mgmt. issues as reported here and in other threads.

So long story slightly longer, I'm going to try your steps, get to 9.04 (praying 64-bit works) and then try the the power mgmt. workaround in the previous post.

Thanks!

---

### Post by Minimalist360 on 2009-08-28
That's odd. I was able to install 64-bit 9.04 from a stick with ZERO problems other than the wireless not working, and the backports fixed that up. Had the same problem when I upgraded the kernel, had to reboot intot he old kernel and get the newer backports. Everything else appears to work properly out of the box, and I had no problems during boot or install. The only question is power management, I get an error about that on boot and it appears that there is no real power management going on.

Is this a BIOS version issue? Mine reports 1.3103, I figured that was due to the model number. Here are the numbers from the BIOS:

System BIOS version: v1.3103
VGA BIOS Version: ATi 010.055.000.051.033092
Product Name: LT31

---

### Post by ufoDziner on 2009-08-28
[Minimalist360]("http://ubuntuforums.org/member.php?u=899030") could you please expand on what you had to do to get the wireless to work?  I'm currently running the liver version booting from a usb stick.  I plugged in a network cable and did an "apt-get install linux-backports-modules-jaunty" I believe it was.  That downloaded a package and presumably installed it.  However, I can't get the wireless to work.  Thanks.

---

### Post by Minimalist360 on 2009-08-28
Once you install the backports and reboot, make sure after booting to move the switch on the front of the laptop to the right once and release to turn on the wireless card. You should see a light come on when you do this.

---

### Post by ufoDziner on 2009-08-28
My light doesn't come on when I slide the switch over.  I am still booting from the usb-stick if this makes a difference.  I will try re-installing the backports now, and try again.  Any further advice?

Edit: Reinstalled backports with no luck.  When I slide the switch, the wifi light doesn't illuminate.  I tried both plugged in and on battery power with no luck.

---

### Post by Minimalist360 on 2009-08-28
Nah, that's all I got. This is what I did:


[LIST=1]
[*] Booted Vista. Ran the disk management and shrunk the Vista partition to as small as it would go, about half the disk.
[*]Booted from USB stick with Ubuntu 64 bit 9.04 on it.
[*]Installed to the hard drive in the free space from 1.
[*]Booted into Ubuntu. All seemed to work, but no wireless.
[*]Applied all available updates including a kernel update. Still no wireless.
[*]Used another computer to determine why this was happening. Installed backports. Rebooted ubuntu. Still no wireless. Slid switch to right (you have to push it kind of hard) and released, and wireless activated.
[*]Used laptop for a few days, new kernel came out (2.6.28-15). Upgraded to new kernel. Rebooted and there was no wireless. Rebooted to older kernel version and used that for a few days.
[*]Installed newer version of backports and then rebooted to (2.6.28-15). Wireless was working again.
[*]Removed all older kernel versions.
[/LIST]

So that's all I have for you.

The only thing I wish I could figure out is how to have Ubuntu use the wireless and connect to ANY memorized wireless network when I turn it on, not when I log in. As it sits, the wireless only connects when you log in. You can make it connect to wireless on boot, but only with a hardcoded name. But this is a different issue.

---

### Post by ufoDziner on 2009-08-28
Ok.  Thanks for the rundown.  The only difference between our installs is that I haven't installed to the hard drive, nor all the updates.  I'll have to look up the command to do this (I haven't used linux in more than 5 years, and I was a Slack guy then).  I'll give all the updates a shot first.  If that doesn't solve the problem, I'll try a had disk install.  Thanks for your help.

---

### Post by Footer on 2009-08-28
For what it's worth, I have the 3103u with Kubuntu 9.04 installed on the hard drive, all updates including backports.  The wireless light is on but I still get no wireless.  Wired works fine ... So you're not the only one  ufoDziner!

Thanks.

EDIT:  I just had to configure my connection (DOH!).  Guess I've never had to do that before in Kubuntu 9.04 so it took me a bit to figure it out.  Thanks for the tip on the switch and light though Minimalist360!  I wasn't even paying attention to that (DOH #2!).

EDIT 2:

System BIOS version: v1.3201
VGA BIOS Version: ATi 010.055.000.051.033431
Product Name: LT31

---

### Post by Minimalist360 on 2009-08-28
Glad I could help.

It's weird that there's a system BIOS update in the machines and it's not available on their site, or at least I don't see it. I wonder if they changed some components and needed a BIOS update but aren't making it available for some reason. Then of course I wonder what that reason is.

---

### Post by ufoDziner on 2009-08-28
Well guys...  Here I am posting from my netbook.  With my out of date skillset, it takes a install on the hard drive in order to get the wifi to work.  Thanks for all the help, info, etc...

BTW, there is a good thread here as well.

[http://ubuntuforums.org/showthread.php?p=7805935](http://ubuntuforums.org/showthread.php?p=7805935)

---

### Post by Footer on 2009-08-28
Congrats ufoDziner!  Weird that you couldn't get it to work with the live version but oh well.  I too was very happy to get wi-fi working.  Now I'm looking into the power mgmt. issue (from the link in post #10).  Looks complicated.  I guess we'll see how good I am at kernel hacking.  Good weekend project.  :)

Nice way to start your weekend, again, congrats!

---

### Post by breaky9973 on 2009-08-31
For what it's worth...I got the same issues but with a different AMD netbook...in this case a Medion E1315. It has similar specs as the Gateway LT3103 and I was only able to install Ubuntu 9.04 through Wubi. 

I have a Powernow! option in my bios which is enabled and in Windows XP it works fine.

Hopefully a solution for the Gateway also might be a solution for the Medion E1315

---

### Post by petersra on 2009-09-05
I just tried the Alpha 5 Karmic Koala live CD and it worked.  And, wireless and sound all were there.

---

### Post by Minimalist360 on 2009-09-05
> **petersra said:**
> I just tried the Alpha 5 Karmic Koala live CD and it worked.  And, wireless and sound all were there.

Do you know if the power management changes have made it into the Alpha 5?


Release date on 9.10 is October 29th - I would imagine by then the power mgmt will be in place for sure and the whole thing will be good out of the box.

---

### Post by yoshiki2 on 2009-09-12
have any1 else tried the 9.10 alpha 5. am about to buy this netbook

---

### Post by yoshiki2 on 2009-10-13
Are power managment and gpu drivers working?

---

### Post by AutoStatic on 2009-10-16
Power management works with 9.04 and with a custom kernel CPU scaling works also. GPU works quite well with the open source Radeon drivers (see attachment).

---

### Post by Minimalist360 on 2009-10-29
I just upgraded to 9.10 and the first thing I notice is the fan is running like crazy.

---

### Post by Footer on 2009-10-30
I guess 9.10 is not good 'out of the box' then?  :(

I suppose we'll have to wait then for another update to this new kernel.  Hopefully someone following this thread will get busy and give us the customized kernel for 9.10 and the LT31!

:)

---

### Post by sxmjohn on 2009-11-04
9.10 runs fine on mine, only complaint is with the wifi it seams to drop off at times other than that all is good:popcorn:

---

### Post by Footer on 2009-11-06
> **sxmjohn said:**
> 9.10 runs fine on mine, only complaint is with the wifi it seams to drop off at times other than that all is good:popcorn:

Which 9.10 are you running?  Full blown Ubuntu 9.10, Kubuntu 9.10 or the 9.10 Netbook Remix?

I'm still wondering how the power stuff is working on the stock kernel (2.6.31).  Under 9.04, it required tweaking.

Thanks!

---

### Post by yoshiki2 on 2009-11-08
wifi dropping? specially if your network is slow?

---

### Post by spaceballl on 2009-11-12
Has there been any update on this? We got this for my brother, but he's not getting it until Christmas. Hopefully by xmas a default install will just work "out of the box." Or... out of the box + updates :D.

---

### Post by boxie on 2009-11-13
i have been running 9.10 for a little while. the wireless is really annoying, i can't do anything for more than a few minutes.

people said that it's load dependant. is there a way to force the wireless to only accept 50kb/s?

i'm running windows XP on this as well, and the wireless drivers work fine on that (got them from gateways labyrinth of a website.

---

### Post by cyberey66 on 2009-11-19
I'm getting the same errors on my netbook, I am going to try installing 8.10 and then  upgrading to 9.04.  The question is how do I upgrade to 9.04?  Since 9.10 is out, i assume it will force me to use 9.10.  Is there a way to manually force an upgrade to 9.04?

---

### Post by cyberey66 on 2009-11-19
nevermind, it upgrades to 9.04 from 8.10.

I have 9.04 installed and working now.

- I installed 8.10 from a usb stick
- From the 8.10 installation I ran "update-manager -d"

---

### Post by cyberey66 on 2009-11-30
Another update in case anyone is following this.  I successfully have Karmic working with everything, including CPU scaling

I first installed 8.10 from a flash drive then upgraded to 9.04.  I compiled the karmic kernel 2.6.31 from source with the corrected DSDT table and verified cpu scaling works.  I then upgraded to 9.10 and continued to use the previously compiled 2.6.31 kernel.  Everything works.

Information on compiling the DSDT into the karmic kernel here:
[http://ubuntuforums.org/showthread.php?t=1341580](http://ubuntuforums.org/showthread.php?t=1341580)

and here is the thread I got the idea from, I just did exactly what the author described but for the new kernel.

[http://ubuntuforums.org/showthread.php?t=1253365](http://ubuntuforums.org/showthread.php?t=1253365)

I'm interested to see if other people are having success as well.

---

### Post by Footer on 2010-01-10
> **cyberey66 said:**
> 

[http://ubuntuforums.org/showthread.php?t=1253365](http://ubuntuforums.org/showthread.php?t=1253365)

I'm interested to see if other people are having success as well.

At the end of the above thread, you will see that a new kernel has been provided (post #54).  I tried it and it broke my wireless so I'm back to the old kernel.  Haven't tried going to karmic with the working kernel from 9.04 (2.6.30.5-acpifx.1) as you've done but I'm not real keen on karmic due to the new grub ... I've been running 9.10 on my desktop since it came out and I'm less than thrilled about the new grub ... but otherwise, 9.10 is great!

Thanks.

---

### Post by Lennon V C on 2010-02-10
So I am using 9.10 64-bit and my wifi drops every so often. Is there any fixes for this out?

---

### Post by Lennon V C on 2010-02-13
> **Lennon V C said:**
> So I am using 9.10 64-bit and my wifi drops every so often. Is there any fixes for this out?

installation of linux-backports-modules-karmic seemed to fix it.

---

### Post by Footer on 2010-02-13
> **Lennon V C said:**
> installation of linux-backports-modules-karmic seemed to fix it.

Is your power management working?  And what kernel version are you running on karmic?

Thanks.

---

### Post by Lennon V C on 2010-02-14
> **Footer said:**
> Is your power management working?  And what kernel version are you running on karmic?

Thanks.
I am a very new user of linux, but I have not had any problems with power management yet. I have not been really looking for issues though. I think I have surfed the internet on Google Chrome for a couple hours without being plugged in.

I am not using the netbook remix.
Linux lennonvc-netbook 2.6.31-19-generic #56-Ubuntu SMP Thu Jan 28 02:39:34 UTC 2010 x86_64 GNU/Linux
I been updating every day and am using backports and ia32-libs. I might be having the same problem as you are i just don't know it since I almost always have my netbook plugged in.

---

