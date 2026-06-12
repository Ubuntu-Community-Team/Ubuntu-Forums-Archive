---
title: "Secure Boot Violation"
date: 2016-12-13
forum: Hardware
---

### Post by paulh1252 on 2016-12-13
Hello Everyone,

I'm a novice Ubuntu user, having changed over from Windows a couple of months ago. Everything has been working fine up to now. Last night I wanted to update my version of Kodi to their latest nightly. The instructions on their wiki page are to simply enter:
```

sudo apt-get update 
sudo apt-get upgrade

```


I did this and the terminal span through a lot of updates. When I next turned on my computer I got the message: "Secure Boot Violation - Invalid signature detected. Check secure boot policy in set up." I ok'd that screen and everything booted up as normal and I'm logged in now with no noticeable problems. Having searched these forums I understand it's often to do with video drivers, but I'm surprised that this was caused by my upgrading Kodi. The other thing that happened was I kept getting a message about ttf-mscorefonts-installer failing to install properly, so I followed the forum guidance to use the Synaptics program to install that program and the error message has stopped appearing.

So my question is whether there is any way I can see what updates installed when I upgraded Kodi last night and what other updates may have caused the conflict with my UEFI secure boot. 
Is there any way to check what unsigned programs I may have on my system. In the process of changing over from Windows to Ubuntu I obviously had to install a lot of packages, and to be honest didn't keep copious notes about how I did it.
Alternatively, should I worry about the error message I'm not dual booting. I don't really understand UEFI and whether I need to use it or secure mode if I'm no longer using Windows and not dual booting.

I'm using an MSI CX61 laptop with Ubuntu 16.04 LTS as the operating system. I hope that's enough information, but please do ask if you need more.

Thanks

---

### Post by oldfred on 2016-12-13
Secure Boot violation is from UEFI.
With UEFI you have three ways to boot.
UEFI with Secure boot
Standard UEFI.
BIOS/CSM/Legacy

Only if you have Secure boot on in UEFI will you get that violation. Or if you installed Ubuntu with signed grub & Kernels and then reinstall with the standard grub & kernels.

Probably best/easiest to turn off Secure boot in UEFI. It may just be called "Windows" or "Other" but notes will say if using Windows 7 use "Other" as Windows 7 is not UEFI Secure boot either.

---

### Post by ajgreeny on 2016-12-13
As you have synaptic installed you may be able to see what has been updated in the synaptic ->File ->History listing, but I'm not sure if it shows packages updated using **sudo apt-get update ** and **sudo apt-get upgrade**.

If not run command ```
grep -i " upgrade " /var/log/dpkg.log.1 /var/log/dpkg.log
``` and in the listing that shows you will be able to, see everything upgraded by date. 
Depending on how long you have had this system up and running you may get an error message saying that the file **/var/log/dpkg.log.1** does not exist, but don't worry about that.

The alternative solution to your problem is simply to disable secure boot inn the BIOS/UEFI setup.

---

### Post by paulh1252 on 2016-12-15
Thanks ajgreeny. This command resulted of about 100 lines of upgrade within about 2 minutes, of which only 2 seem to be Kodi related. So, I don't think I have much chance of working out which one caused the issue. I'm not really too happy turning off secure boot without really understanding what it does, so maybe I should just put up with the warning on start up. It's a shame you can't selectively choose what to update on Ubuntu.

---

### Post by Bucky Ball on 2016-12-15
> **paulh1252 said:**
> I'm not really too happy turning off secure boot without really understanding what it does ....

Extremely easy to find out. Just do a search for 'secure boot' and you'll get a ton of information. Like this.

> Microsoft Secure Boot is a component of Microsoft's Windows 8 operating system that relies on the UEFI specification's secure boot functionality to help prevent malicious software applications and "unauthorized" operating systems from loading during the system start-up process.

[From here.]("https://technet.microsoft.com/en-us/library/hh824987.aspx")

'Secure boot' can consider Ubuntu to be an '"unauthorized" operating system' and prevent it installing. There was terrific fun to be had with secure boot when it first appeared on the scene (that and UEFI, a joyful duo for all Linux users ... not). The stench lingers as evidenced by the persistent flow of support requests these forums still get about UEFI/secure boot. No positives, it just presented a further hurdle to potential Linux users and 'made Linux harder' (which simply reinforced the stereotype, perhaps one of the outcomes MS was aiming for).

As far as switching it off goes, read through some links, the rest is up to you. oldfred is the expert on all things 'secure boot' if you have a hunt for one of his threads regarding it.

---

### Post by mastablasta on 2016-12-15
> **paulh1252 said:**
> . It's a shame you can't selectively choose what to update on Ubuntu.

what do you mean you can't ? sure you can. you can also lock a package to a certain version.

---

### Post by oldfred on 2016-12-15
Oldfred is not a fan of UEFI Secure Boot. In future we may need it.

What if you are a large corporation trying to sell trying to sell software that is in the news daily with issues of virus and other security issues. You come out with a product that has Secure in the title, so people think it is new & better, and has eliminated the security issues.

It just is boot virus are rare. Main boot virus historically was released by Sony so you could not play music that you did not own.

Microsoft then did include a better virus checker in Windows which helps reduce issues, so it seems the Secure Boot has improved system. It mostly has just made it more complicated.

 [http://www.zdnet.com/torvalds-clarifies-linuxs-windows-8-secure-boot-position-7000011918/](http://www.zdnet.com/torvalds-clarifies-linuxs-windows-8-secure-boot-position-7000011918/)
 the whole UEFI thing is more about control than security

---

### Post by paulh1252 on 2016-12-15
> **mastablasta said:**
> what do you mean you can't ? sure you can. you can also lock a package to a certain version.

I said that because like I said up top I'm a new user of Ubuntu. I'm not a programmer, heavy computer user or industry insider, and nor do I have any desire to be so. Therefore, like your average user I try to follow the instructions when installing or updating software. Virtually every program I've come across tells you to do the whole 'apt-get update' thing when installing or updating (such as Kodi [here]("http://kodi.wiki/view/HOW-TO:Install_Kodi_for_Linux#Upgrading")). This appears to update everything, not just the program you're interested in.

---

