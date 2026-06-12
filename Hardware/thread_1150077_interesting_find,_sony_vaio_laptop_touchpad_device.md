---
title: "interesting find, sony vaio laptop touchpad devices"
date: 2009-05-05
forum: Hardware
---

### Post by k3mist on 2009-05-05
After installing Jaunty, my touchpad did not work on my sony vaio laptop, I wasnt bothered by this at all since i use my wireless usb about 98% of the time. I thought that Jaunty didn't bother with it since I installed with the usb mouse connected and just skipped over it or had it disabled.

However, I did WANT to get it working. It's an ALPS touchpad and after about 4-6 hours of configuring, reading, etc etc, I still did not have it working. Tried the xorg method and newer hal method (what i am now using), neither of these worked.

I could see the device, every available command on linux you can think of showed the device connected and working. All the settings looked good, etc etc etc. Completely stumped and mentally exhausted at this point. I figured I was missing something. I'm a windows convert fyi just a couple weeks ago now and dual booting at the moment. (Loving linux btw) 

Anyway, I knew in vista through the sony vaio control panel I had the touchpad disabled. So on a hunch, I booted into vista and enabled the touchpad through sony's control panel. Boot back into Jaunty and boom, touchpad is working.

And my assumption at this point... the vaio control panel has a hardware/firmware level turn off for the touchpad??? Would be the ONLY thing that makes any logical sense right? Maybe someone can shed some light on this? And God knows what you would do if you removed vista before figuring that out?

Anyway, thought this was extremely interesting find, for myself anyway and decided to share.

---

### Post by dpezely on 2010-07-06
See /var/log/Xorg.0.log: 

"PNP: PS/2 appears to have AUX port disabled, if this is incorrect please boot with i8042.nopnp"

This turns out to be the correct advise for Sony VAIO laptops.

Here's the fix:

1. Edit /etc/default/grub to include GRUB_CMDLINE_LINUX="i8042.nopnp"
2. Run: sudo update-grub
3. Reboot.

(So then, booting into Windows is unnecessary.)

Tested on Sony Y-Series (VPCY2; Core i5; mid-2010 edition) running Ubuntu 10.04/amd64.

---

### Post by mapleb on 2010-07-14
dpezely, I love you.

I added i8042.nopnp to my GRUB_CMDLINE_LINUX_DEFAULT.

Works on the 2010 Sony Vaio P (VPC-P113KX).

---

### Post by mapleb on 2010-07-19
Update:

The i8042.nopnp option was only working intermittently.

After reading [https://bugs.launchpad.net/ubuntu/+bug/341094](https://bugs.launchpad.net/ubuntu/+bug/341094),

I added i8042.reset i8042.nomux i8042.nopnp i8042.noloop, and that seemed to do the trick.

---

### Post by West201 on 2010-09-25
> **dpezely said:**
> See /var/log/Xorg.0.log: 

"PNP: PS/2 appears to have AUX port disabled, if this is incorrect please boot with i8042.nopnp"

This turns out to be the correct advise for Sony VAIO laptops.

Here's the fix:

1. Edit /etc/default/grub to include GRUB_CMDLINE_LINUX="i8042.nopnp"
2. Run: sudo update-grub
3. Reboot.

(So then, booting into Windows is unnecessary.)

Tested on Sony Y-Series (VPCY2; Core i5; mid-2010 edition) running Ubuntu 10.04/amd64.usi

Thanks I love you too !!! I've had that issue since I first started using Linux. I've spent countless hours and nights trying to fix this. Your the man !

---

### Post by ranjithsiji on 2010-10-09
Great Post. I found this post after two days. My Sony Vaio VPCEA32EN worked fine using this tweak. I tested on Ubuntu 10.04, Ubuntu 10.10 and Fedora 13. All works fine. I updated this on [my Blog]("http://ranjith.zfs.in/sony-vaio-touch-pad-in-linux-fedora-and-ubuntu/"). You saved my Life 

I Love You --------------!!!!!!!!!!!!!!!1

Thanks a lot ... TK. [IMG]http://ubuntuforums.org/images/icons/icon10.gif[/IMG]

---

### Post by Xcorp on 2010-11-10
I manage to get the touchpad working, but i realy miss two-finger scroll, has anyone got it working, or got the touchpad to show up under mouse settings at all?

---

### Post by superbush on 2010-11-25
Thank you, dpezely!!! My new VPC3B3L1E is "full optional" now!! :popcorn:  Thanks thanks :D

---

### Post by nyvietvet on 2010-12-01
Re: Touchpad Not Working...
Here’s the fix:

1. Edit /etc/default/grub to include GRUB_CMDLINE_LINUX=”i8042.nopnp”
2. Run: sudo update-grub
3. Reboot.

After following the above, I got:

bill@bill-VPCEE3WFX:~$ !!
sudo update-grub
[sudo] password for bill: 
/etc/default/grub: 1: &#65279;#: not found
bill@bill-VPCEE3WFX:~$


What am I missing here?

---

### Post by pehden on 2011-02-23
> **nyvietvet said:**
> Re: Touchpad Not Working...
Here’s the fix:

1. Edit /etc/default/grub to include GRUB_CMDLINE_LINUX=”i8042.nopnp”
2. Run: sudo update-grub
3. Reboot.

After following the above, I got:

bill@bill-VPCEE3WFX:~$ !!
sudo update-grub
[sudo] password for bill: 
/etc/default/grub: 1: &#65279;#: not found
bill@bill-VPCEE3WFX:~$


What am I missing here?

I Agree I have this same laptop and would like to see a working config file for this solution.

---

### Post by andreisun on 2011-03-04
Hi,

I had a problem with my Acer 5630Z touchpad... and your solution helped!!! Million thanks!:popcorn:

---

### Post by MarjaE on 2011-06-20
It doesn't work on my Sony Vaio VPCEE42FX. I think this was one of the first fixes I tried ... and the touchpad keeps malfunctioning, even as I type this.

---

