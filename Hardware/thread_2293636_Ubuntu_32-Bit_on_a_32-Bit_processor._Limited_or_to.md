---
title: "Ubuntu 32-Bit on a 32-Bit processor. Limited or total available ram reported by Bios?"
date: 2015-09-06
forum: Hardware
---

### Post by hey2 on 2015-09-06
Hi.

I need to know if when i click in the system information of Ubuntu 14.04 32-bit, the memory reported will be the same that Bios recognizes or will it be capped like Windows Xp (3Gb) and Windows 7(3.5Gb)?

I'm asking because i want to install 4gb (maximum amount) on my old computer to run Ubuntu and i need to know if it will use the maximum possible, since, from what I've gathered, 32-bit computers cannot use all 4gb installed.

Thank you and sorry for my English.

---

### Post by Yellow Pasque on 2015-09-06
Some of the RAM will be used for hardware addressing, so it will not show in the total available. (64-bit systems will do that as well). I would expect the kernel to report about 3.8GB (or less if you have integrated graphics).

---

### Post by hey2 on 2015-09-06
> **Temüjin said:**
> Some of the RAM will be used for hardware addressing, so it will not show in the total available. (64-bit systems will do that as well). I would expect the kernel to report about 3.8GB (or less if you have integrated graphics).

Hi.

Thanks for your answer.

So it's not like the Windows xp where it always says that you have 3GB even if your Bios says that you have more than that.

Do you know why Ubuntu show more ram than Windows xp?

I'm expecting to have just a dedicated graphics card with 512mb, one hard drive and the integrated sound.

3.8 would be great, but i don't know...

Thanks again.

---

### Post by brian-mccumber on 2015-09-06
No it's not like Windows at all. I have 5 gigs of ram installed and Ubuntu see's and uses all of it.

It's because of the way Ubuntu utilizes [PAE]("https://en.wikipedia.org/wiki/Physical_Address_Extension"). 32bit Windows server editions can utilize more than 4 gigs of ram because of pae, Windows client versions can support pae but do not support addresses beyond the 4gb mark due to driver issues. Linux does not have this limitation and when Ubuntu see's +4gb of ram it automatically uses kernel with pae which supports up to 64gbs of ram so it pretty much gives 32bit machines 64bit memory. But at this point the 32bit hardware will limit how much ram can be used with Ubuntu not the OS.

---

### Post by hey2 on 2015-09-06
> **brian-mccumber said:**
> No it's not like Windows at all. I have 5 gigs of ram installed and Ubuntu see's and uses all of it.

It's because of the way Ubuntu utilizes [PAE]("https://en.wikipedia.org/wiki/Physical_Address_Extension"). 32bit Windows server editions can utilize more than 4 gigs of ram because of pae, Windows client versions can support pae but do not support addresses beyond the 4gb mark due to driver issues. Linux does not have this limitation and when Ubuntu see's +4gb of ram it automatically uses kernel with pae which supports up to 64gbs of ram so it pretty much gives 32bit machines 64bit memory. But at this point the 32bit hardware will limit how much ram can be used with Ubuntu not the OS.

Hi.

Thanks for your answer.

Does your Bios report the 5GB of ram?

That's another thing that i don't understand and I'm grateful you brought it up.

If you have 5gb, and your bios report that you have 3.5 due to 32bit limitation, would Ubuntu with PAE see the 5gb of ram?

Thanks again.

---

### Post by Yellow Pasque on 2015-09-06
> If you have 5gb, and your bios report that you have 3.5 due to 32bit limitation

Then the motherboard (and memory controller) does not support PAE and no operating system will be able to use more than that. Modern versions of Ubuntu will not even boot/install on such a system.

---

### Post by brian-mccumber on 2015-09-06
What Temujin said is right except for the part about it not installing on your hardware. The minimum specs for Ubuntu installation is 512mb of ram. A rule of thumb, if your computer ran windows xp-7 you can install and run Ubuntu. Here is a link to the official min specs for Ubuntu - [https://help.ubuntu.com/community/Installation/SystemRequirements](https://help.ubuntu.com/community/Installation/SystemRequirements)

If you are worried make an Ubuntu disk and try running Ubuntu Live on your computer without installing it first. When you make an installation disk for Ubuntu when you boot from the disk you will get a menu and you can try it live without installing it.

But for a better experience using Ubuntu on older hardware, I would suggest a lite version of Ubuntu like Lubuntu or Xubuntu and you don't have to limit yourself to Ubuntu distros there are many versions of Linux out there that are geared toward older computers.

---

### Post by Yellow Pasque on 2015-09-06
> **brian-mccumber said:**
> What Temujin said is right except for the part about it not installing on your hardware.

It's not the amount of memory; it's that the kernel is built with PAE enabled and requires the hardware to support PAE: [http://linux.softpedia.com/blog/i386-non-PAE-Kernel-To-Be-Removed-from-Ubuntu-12-04-234434.shtml](http://linux.softpedia.com/blog/i386-non-PAE-Kernel-To-Be-Removed-from-Ubuntu-12-04-234434.shtml)

---

### Post by hey2 on 2015-09-06
Hi.

Thank you all for your answers.

The computer works with Ubuntu. I already tried.

The thing is, right now the computer has 2gb of ram and a 32mb graphics card. As you might imagine it is very slow since Unity needs graphic acceleration.

That's why i was thinking about installing 4gb of ram and a 512mb graphic card.

But i started reading that not only windows xp would only see 3gb, but it could happen that the system itself will not see the whole 4gb of ram. So i was afraid that the same would happen with Ubuntu.

That's why i wanted to ask if Ubuntu, unlike xp, will use the whole amount of ram reported in the Bios. 

Thank you all once again.

---

### Post by brian-mccumber on 2015-09-06
I wasn't implying that the ram had anything to do with the kernel, I was letting the poster know that the min ram specs for Ubuntu is 512mb and he has more than that. There are older processors that can support pae and run Ubuntu but for some reason the manufacturers turned it off. See this article - [http://askubuntu.com/questions/117744/how-can-i-install-on-a-non-pae-cpu-error-kernel-requires-features-not-present](http://askubuntu.com/questions/117744/how-can-i-install-on-a-non-pae-cpu-error-kernel-requires-features-not-present)

It is possible that his cpu would support it but it's turned off. That is why I suggested installing Lubuntu or Xubuntu or another version of Linux that supports older hardware. I did not want to confuse him by saying that his processor could support pae but it may be turned off and there are many steps you have to take to get it to turn on in order to install Ubuntu.

Neither of us know what his actual hardware specs are and his original post wasn't about pae kernel support, he was just worried about how much ram Ubuntu could use.

---

### Post by brian-mccumber on 2015-09-06
[**[COLOR=#000000]hey2[/COLOR]**]("http://ubuntuforums.org/member.php?u=1972206"), I am glad you got it working. So apparently you could put more than 2 gigs of ram in it if you want and Ubuntu will use it. If your bios can see it then Ubuntu will use it.

Sorry for the confusion. I guess we were thinking you were trying to install it on an old 486 or something.

---

### Post by hey2 on 2015-09-06
> **brian-mccumber said:**
> [**[COLOR=#000000]hey2[/COLOR]**]("http://ubuntuforums.org/member.php?u=1972206"), I am glad you got it working. So apparently you could put more than 2 gigs of ram in it if you want and Ubuntu will use it. If your bios can see it then Ubuntu will use it.

Sorry for the confusion. I guess we were thinking you were trying to install it on an old 486 or something.

Hi.

Sorry if I'm confusing you. It's my bad English.

I didn't bought the components yet.

I was just saying that it works with what i have now (2gb and 32mb graphics card), but for obvious reasons it's very slow.

Sorry again.

---

### Post by brian-mccumber on 2015-09-06
It's no problem and it was partially my fault too because sometimes I can overcomplicate things, I am just trying to  help because I love this kind of stuff and it's Sunday and I don't have  to work.

Lets just simplify this, if you put ram in your computer and your bios recognizes it and your motherboard supports it then Ubuntu will use all of it. Ubuntu does not have the 4gb limitation like Windows. If you were to increase your ram to 4gb you would probably notice a huge increase in the performance. My laptop has 4gb of ram and integrated Intel graphics and it runs Ubuntu very well. This is my opinion.

---

### Post by hey2 on 2015-09-07
> **brian-mccumber said:**
> It's no problem and it was partially my fault too because sometimes I can overcomplicate things, I am just trying to  help because I love this kind of stuff and it's Sunday and I don't have  to work.

Lets just simplify this, if you put ram in your computer and your bios recognizes it and your motherboard supports it then Ubuntu will use all of it. Ubuntu does not have the 4gb limitation like Windows. If you were to increase your ram to 4gb you would probably notice a huge increase in the performance. My laptop has 4gb of ram and integrated Intel graphics and it runs Ubuntu very well. This is my opinion.

Thanks for your time.

I'm sure that your laptop processor is a lot better, though :D. Let's hope that it works.

If after the upgrade the performance is similar to what i have now running Windows, i'm happy.

Like i said in previous posts, the problem with windows is not the 4gb limitation. That, i understand. The problem is that Windows xp is capped at 3gb.

Thank you once again.

---

### Post by brian-mccumber on 2015-09-07
The cpu in my Toshiba Satellite L455 laptop is a Celeron 900 @2.20ghz and it's about 6 years old and it's been dropped about 3 times which didn't hurt it at all surprisingly. The battery is crap and it won't run over 2 minutes if I unplug it and my adapter is actually part toshiba adapter and part acer adapter that I wired together and it's taped up with duct tape. But I just don't have the money right now to replace these things so I keep patching it up with bubblegum and duct tape in the meantime. I have upgraded the ram in it from 2gb to 4gb tho, but that was a long time ago when the battery was still good. But this thing still runs like a champ. I disassemble it from time to time to clean the crap out of it and I blow out the fan with an air-compressor once every three months or so.

---

### Post by hey2 on 2015-09-07
> **brian-mccumber said:**
> The cpu in my Toshiba Satellite L455 laptop is a Celeron 900 @2.20ghz and it's about 6 years old and it's been dropped about 3 times which didn't hurt it at all surprisingly. The battery is crap and it won't run over 2 minutes if I unplug it and my adapter is actually part toshiba adapter and part acer adapter that I wired together and it's taped up with duct tape. But I just don't have the money right now to replace these things so I keep patching it up with bubblegum and duct tape in the meantime. I have upgraded the ram in it from 2gb to 4gb tho, but that was a long time ago when the battery was still good. But this thing still runs like a champ. I disassemble it from time to time to clean the crap out of it and I blow out the fan with an air-compressor once every three months or so.

Maybe you're like me. I only substitute things when they are completely dead 

Taking the risk of looking like a fisherman, but my processor is a Pentium 4 3.0 :D

---

