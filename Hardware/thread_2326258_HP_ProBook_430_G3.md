---
title: "HP ProBook 430 G3"
date: 2016-05-30
forum: Hardware
---

### Post by UtnubuLap on 2016-05-30
Hello!

I have ordered a HP ProBook 430 G3 laptop, which will arrive in a couple of days. It comes with Windows 7, but I intend to completely wipe it off and install Ubuntu 16.04 LTS. I do however want to take a backup of Windows 7 on a USB, just incase I will need it for whatever reason. (The USB will most likely just be gathering dust in a drawer.)

I have a few questions:

1. Should I use "Control Panel - All Control Panel Items - Recovery - Create a recovery drive" (Windows tool) or "HP Recovery Manager - Create recovery media" (HP tool) to backup Windows 7? (These are options which are available on the laptop I am on right now. Not sure if the options are exactly the same on the HP ProBook 430 G3 laptop.) What is the difference between them, if any? I assume the first option will just take a backup of a vanilla Windows 7 install (Microsoft build), while the second option will backup HP's customized Windows 7 install with all drivers, etc in place. (HP factory build) If so, I guess I will opt for option 2. I intend to create this backup USB as soon as I have booted up the laptop, then proceed with downloading the latest HP updates and finally installing Ubuntu. Would it be wiser to get Windows and HP updates before making the recovery USB, or does it not matter? I believe the recovery image will be unaltered even if I download Windows and HP updates, and it won't matter.

2. As mentioned, I will download HP updates. (BIOS, etc) If HP releases new updates after I have wiped Windows and installed Ubuntu, will I need to reinstall Windows just to get the updates or will I somehow be able to download the .exe files and update HP in Ubuntu?

Question 1 might not be directly related to Ubuntu, however I want to figure this out before proceeding with Ubuntu. If it is not fit for this forum, pardon me.

Greatly appreciate any help I can get!

---

### Post by oldfred on 2016-05-30
With my new Dell that I had not planned on wanting Windows, I did three backups. One Windows, one Dell and one full backup with Macrium Reflect.
It took a while as I had to go by another flash drive and more DVDs. And then I made a Windows repair flash drive also. Of course with was Windows 8 and MS started nagging about free upgrade to Windows 10 and I did that. 
I shrank Windows to 50GB on a 1TB drive as I wanted to record TV with it. But Comcast allowed streaming and that only worked with Windows. So I had to expand back to 100GB, also so I had room for Windows 10 upgrade.

Many UEFI have three ways to update UEFI/BIOS. From Windows, from a DOS bootable flash drive and directly from a FAT32 formatted flash drive, where UEFI directly reads the update file. Check your manual on what is available with your system.  If only Windows I would keep it in a small partition. 

Most HP have not been UEFI dual boot friendly. And if you system is Windows 7 it may or maynot be UEFI. Windows 7 default install is BIOS, but installer can be converted to UEFI if on flash drive and some files moved around. Windows only boots in BIOS from MBR or only from gpt with UEFI. So if you keep Windows you must keep the partitioning type.

If erasing Windows I suggest gpt, but if Windows was BIOS/MBR best to stay with MBR as you would have to erase drive to reinstall Windows.

One user posted that he regularly gets new computer and sells old one. But he buys SSD to speed up system and before even booting, installs SSD. Then when he sells it, he just puts Windows drive back in. Then it is like brand new Windows and has none of his data.

For HP and many systems we have work arounds for their UEFI. They have modified UEFI to only boot Windows by description. And of course only valid description is "Windows Boot Manager". And that is a violation of the UEFI standard that specifically says not to use description.
If not booting Windows we can change description from Ubuntu to Windows and it thinks it boots Windows (by description) but really uses shim/grub. If dual booting there are several other alternatives.

---

### Post by UtnubuLap on 2016-05-30
Thanks for the info.

---

Been reading around on the net and it seems that I should use "HP Recovery Manager" to create the recovery media. I'll be using a USB stick as mentioned.

Thing is, once I have done so, and wiped the laptop drive, and installed Ubuntu, will I be able later down the road to insert the USB stick and boot from it to re-install Windows? In other words, does the recovery media (USB) contain everything required to re-install Windows aka get the laptop drive back to how it was when it was shipped from the manufactuer, including partition sizes, etc?

Also, how would I get back the original boot loader?

I suspect I should be asking these questions on another forum and not here.

---

### Post by UtnubuLap on 2016-05-30
Sorry, another quick question, this time strictly Ubuntu related though...

The laptop comes with a SSD (and 4 GB of RAM). I've read a bit about SSD and swap, and from what I can gather I should not be making a swap. So I am thinking of just formating the complete drive and having one partition for /. Does this sound reasonable? What will I lose out on if I don't have swap? (No loses except when RAM is full, RAM is full?)

---

### Post by sudodus on 2016-05-30
When RAM is full, and a program needs more RAM, it crashes.

It can be a good idea to plan for not using swap, but to have a small swap partition anyway, 1 or 2 GB, just as a buffer. You will notice that the computer is getting slow, (you can have a monitor program running but it is probably not necessary), and you can close a program, a tab or two in the web browser, and return within the RAM limit again (not write more to swap). In that case you will not cause too much wear of the flash memory of the SSD.

---

### Post by UtnubuLap on 2016-05-30
Alright.

If I understand you correctly, swap will not be used unless I exceed 4 GB of RAM, so as long as I stay under 4 GB of RAM, then the swap partition will not wear the SSD at all? Correct me if I am wrong.

If this is the case, I might just make a small swap partition, but then  again, I might just monitor RAM and not exceed 4 GB or just let some  program crash. Really not sure what to do, but thanks for the info! Any particular con's to not having swap, except a program crashing? (Guess this is a big enough con to justify using swap on SSD.)

(I got a spare RAM slot, so I could potentially get some RAM and therefor not need the swap, however I can't afford it as of right now.)

Another thing, I've read that having swap on an SSD and then hibernating is bad, as it will save everything exceeding RAM capacity in swap, and thereby reducing life-span. Is this the case? What about when suspending? (From my understanding this does not use swap.) When I lock screen or logout I assume neither hibernation or suspension takes place, but if I just close the lid of my laptop, does it hibernate or suspend? If it hibernates, then swap will be used. I frequently close my laptop lid and carry the machine wherever I am going.

My post is rather messy, hopefully it makes sense. Thanks!

EDIT:

From what I can figure, closing lid suspends and does not hibernate, and thefore doesn't use swap.

EDIT:

Seems Ubuntu will use swap before RAM runs out, if swapiness > 0, which it is by default in Ubuntu (and every other distro).

There doesn't seem to be a "right" or "wrong" way when it comes to having swap on an SDD or not. Read a couple of websites and forum discussions and there doesn't seem to be any agreement, some people say you should make swap, others not.

---

### Post by sudodus on 2016-05-31
Yes, you can change swappiness. I would not set it to 0, but a lower value than the default. Some people suggest 10 (I think default is 60).

---

### Post by UtnubuLap on 2016-06-02
I just went with "Erase disk and install Ubuntu" during install, and it created a 4gb swap partition. Think I'll just leave it at that and default swapiness, until I want to install Ubuntu fresh on again. I'll check RAM once in a while with "free -m", just too see how often (if at all) swap is used.

Installing Ubuntu went smooth, set it up to my liking now, however I have one concern...

When I open Firefox and open ~5 tabs, the fan comes on and it makes this "wavy sound", not sure how to describe it, it seems as if the fan rpm increases to x, then decreases to x/2, then increases to x, decreases to x/2, repeatedly for 20-30 seconds, before it stops. If I open another few tabs, the process repeats, but the fan stops after 20-30 seconds again. The laptop doesn't slow down at all, but I am a little worried that something is wrong, should the fan even start when I just launch firefox and rather quickly open 5 tabs? Does it opening 5 tabs really cause that much heat? Also the unstable rpm of the fan is a bit strange. Any thoughts?

EDIT: Maked this thread as solved, and will make a new thread for my current question as it is not related to main post. Thanks for help here!

---

### Post by sudodus on 2016-06-02
You are welcome, and thanks for sharing your result and marking this thread as solved :-)

And yes, it is a good idea to discuss the active fan in another thread.

---

