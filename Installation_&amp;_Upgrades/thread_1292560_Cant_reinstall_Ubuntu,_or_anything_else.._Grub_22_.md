---
title: "Cant reinstall Ubuntu, or anything else.. Grub 22 error"
date: 2009-10-16
forum: Installation &amp; Upgrades
---

### Post by CAcationu2 on 2009-10-16
A few weeks ago my computer restarted and when it tried to boot up, it just wouldn't. It stayed at the black screen.
I have searched this forum for those 3 weeks and tried everything on here, including but not limited to;
BIOS hardware scans; reinstall with Live cd (Error: Can not read boot cd); reinstall with original Vista CD (Error: Cannot read boot cd); Booting using USB in all the ways mentioned on the forum; alternate cd; Unetbootin simply won't work. It gets to the selection screen and when I select one, does the countdown, but doesn't do anything. CD's aren't corrupted, they work on other computers. 
I got Grub error 22, so I did everything the forums said for that. 

I've forgotten everything I have tried here, and I'm starting to go out of my mind. I think it's a cd drive issue, but how can I check? I took it too a store and they came back with a "i dont know".

Does anyone out there know ANYTHING i can do?? I can't afford a new computer, and I'm going insane trying to do this. 

I have an HP Pavilion DV2700, Intel Core Duo 2.0, 4 Gigs ram, 320GB 5200 SATA Hard Drive, came with Vista. If anyone has any ideas at all, please let me know.


Thanks.

__Forgot to mention: I do suspect it to be my cd drive, but before it went down for good I also tried reinstallation. It wouldn't take the cd's even though they worked in other computers. Nor the USB. But it would play dvd's and cd's. Does that make any sense?

---

### Post by BQAggie2006 on 2009-10-16
Have you tried re-burning your Ubuntu CD at the slowest speed you can? Also, have you tried to boot into another LiveCD distro?

---

### Post by earthpigg on 2009-10-16
im going to guess that:

1) your optical drive is dead.

2) you havent tried ALL methods to boot from USB. and you havent tried DIFFERENT thumb drives... some do not play nicely with Linux because vendors try to add windows 'features' to them.

2a) the dd command with an .img file: [http://wiki.archlinux.org/index.php/Beginners%27_Guide#USB_stick](http://wiki.archlinux.org/index.php/Beginners%27_Guide#USB_stick) (you will be using an ubuntu .img file, of course, but the process is identical.)

2b) unetbootin

2c) ubuntu's usb startup disk creator


double check your BIOS settings, of course.

try a different usb port... if it isnt working in a port on the front of the case, shove it in one of hte ports in the back.

2a above is the simplest and most 'correct' method, even though it is not the easiest. it has the LEAST chances of something going awry.

---

### Post by earthpigg on 2009-10-16
also, from now on while we are trying to fix this... please document or post ***exactly*** what you tried and ***exactly*** what happened.

---

### Post by ztomic on 2009-10-16
Sounds like a hardware problem. there's a small chance that you have a loose cable inside the computer. Try that first for a cheep fix. If you're intent on fixing the problem yourself, then try other hardware: CDROM, Hard Drive... etc. Sounds like you don't want to spend much but I would say you may have to call a Geek. I mean that's a pretty nice computer and probably well worth the expense.

---

### Post by CAcationu2 on 2009-10-16
@BQAggie2006 - Yes. At this time, I have made a few different basic Ubuntu cd's at different speeds. Even the lowest setting doesn't work. 
@earthpigg - **1) your optical drive is dead.** I would be okay with that. Simple answer, posible fix. Is there a way to verify?

**2) you havent tried ALL methods to boot from USB. and you havent tried DIFFERENT thumb drives... some do not play nicely with Linux because vendors try to add windows 'features' to them.** I have tried all I have seen on the forums, more than once for some of the options and yes on different thumb drives. However, you may know of options I have not yet tried.

**2a) the dd command with an .img file: [http://wiki.archlinux.org/index.php/...uide#USB_stick](http://wiki.archlinux.org/index.php/...uide#USB_stick) (you will be using an ubuntu .img file, of course, but the process is identical.)** Pretty sure i've doen the .img file, but I can give it another go.

**2b) unetbootin** tried for linux start up, grub repair, windows startup... nothing there.
**2c) ubuntu's usb startup disk creator** now that sounds like using both the usb and cd. Not sure I've tried it, but, what exactly do you mean?


**double check your BIOS settings, of course.** Been in BIOS a lot, settings are good.

**try a different usb port... if it isnt working in a port on the front of the case, shove it in one of hte ports in the back.** I have 3, I have tried them all, with different usbs, different types of install.
Also, sorry about the lack of details. As I said, this has been going on for 3 weeks; memory is fuzzy on what exactly the problems were. From now on however, details for sure.

@ztomic - It's not that I don't want to spend much, it's that I don't have the money to do so. Again, I'm kind of a noob when it comes to computer fixing so could you specify what you mean about a cable?

Now I am mostly getting the Grub 22 Error at the 1.5 load point, but I've tried all the forum options regarding that particular error. 

Keep in mind, I can't get to an OS at all. I am stuck on black screens, BIOS, and C, which I am not very literate in.
Thanks for the quick responses.

---

### Post by presence1960 on 2009-10-16
I would check the cable to the optical drive as well as the power connection on the optical drive. I had a problem burning CD/DVDs right after having my case open for it's monthly cleaning. Turns out the power connection was not seated properly.

Also try switching out the cables if you have a spare, they do go bad too.

CD/DVD drives are very cheap now. If it isn't the connections it may be the optical drive since your disks run in other machines.

---

### Post by earthpigg on 2009-10-16
2c) you will need to use a buddies computer. boot live cd. download or have available the origional .iso file (not stored on the target thumb drive, of course). system -> admin -> usb startup disk creator.

the cable fix:

protect your computer against ESD. open the case. make sure there are no loose cords.

---

### Post by CAcationu2 on 2009-10-18
@earthpigg - Unfortunately, I no longer have another computer I can  boot Linux on. I did have friend's computer, but I don't any longer and the one I use at home is a family member's who refuses. However I will save that for when I do have another computer available. Thanks.

@presence1960 - That's what I'm working on. There are 3 screws that myself and family members have been unable to get loose. I might just take it in when I get my next check and have someone open it for me and find out if it is the CDDrive. I am still leaning toward it being an optical issue.

Thanks very much for responding and giving some ideas. I'm kinda at a stand-still as it is and won't really be able to move forward until I get paid again. I will update with any new devleopments.

---

### Post by presence1960 on 2009-10-18
> **CAcationu2 said:**
> @earthpigg - Unfortunately, I no longer have another computer I can  boot Linux on. I did have friend's computer, but I don't any longer and the one I use at home is a family member's who refuses. However I will save that for when I do have another computer available. Thanks.

@presence1960 - That's what I'm working on. There are 3 screws that myself and family members have been unable to get loose. I might just take it in when I get my next check and have someone open it for me and find out if it is the CDDrive. I am still leaning toward it being an optical issue.

Thanks very much for responding and giving some ideas. I'm kinda at a stand-still as it is and won't really be able to move forward until I get paid again. I will update with any new devleopments.
No problem, if you need more help let us know back here.

---

### Post by earthpigg on 2009-10-19
> **CAcationu2 said:**
> @earthpigg - Unfortunately, I no longer have another computer I can  boot Linux on. I did have friend's computer, but I don't any longer and ***the one I use at home is a family member's who refuses***. However I will save that for when I do have another computer available. Thanks.


i must say, i would be rather frustrated in your shoes.

you explained to the family member that booting a live cd requires ***zero*** changes to his/her computer, right?

---

### Post by CAcationu2 on 2009-10-20
New development!

@earthpigg - On second thought, that sounds like what one would do to boot Linux using a USB. If that is correct, I have done it.

I bought a hard drive docking station and formatted it using the computer I am currently on. I put it back into my computer and tried to install Linux with a boot CD. It did not work, I still get the same error so when I tried to boot from the hard drive just for kicks (I was extremely frustrated, I know that doesn't make sense.) and it came up with a new error. Grub 17 instead of 22.

I did a search for that on the forums, but it looks as if the only options I have to fix that are if I have a Linux terminal available. If I'm way off base here, please enlighten me. 
This is getting to be way to much. This is why I just bought new computers when old ones start this crap. 
I'm at money v.s. sanity right now.
Any ideas?

---

### Post by rtyb on 2009-10-20
Seems like a problem with the MBR (well, it seemed.....now, with all you've done....totally screwed up....) .... xDDDD
i don't think you're gonna be able to fix it now with GRUB Error 17......

---

### Post by presence1960 on 2009-10-20
Let's get a better look at your setup & boot process. Boot the Ubuntu Live CD/USB. Choose "try ubuntu without any changes", when the desktop loads come back here and use the link in my signature to download the Boot Info Script 0.32 to the desktop. Once on desktop open a terminal and run this command ```
sudo bash ~/Desktop/boot_info_script*.sh
``` This will create a RESULTS.txt file on the desktop. Paste the entire contents of that file back here. Once pasted highlight all text and click the # sign on the toolbar to place code tags around the text.

---

### Post by CAcationu2 on 2009-10-21
@presence1960 - I can't even get that far. I still have the same problem when trying to boot from cd or usb. It say "error: cannot read disk". And then reboots.
I cannot get to the terminal. I currently have no way to get to any OS. 

The devices I have at this stage are Live cd's/usb that work on other computers, a Windows XP computer, and a hard drive docking station.

I know this is starting to get a bit McGiver, but those are my options. Does anyone have an idea of what I can do now? I thought there was a way to install Linux on my hard drive docking it to the windows computer. Am I mistaken?

@rtyb - As helpful as that observation may be to others, are you saying there is nothing I can do about the computer at all now?  :(

---

### Post by presence1960 on 2009-10-21
> **CAcationu2 said:**
> @presence1960 - I can't even get that far. I still have the same problem when trying to boot from cd or usb. It say "error: cannot read disk". And then reboots.
I cannot get to the terminal. I currently have no way to get to any OS. 

The devices I have at this stage are Live cd's/usb that work on other computers, a Windows XP computer, and a hard drive docking station.

I know this is starting to get a bit McGiver, but those are my options. Does anyone have an idea of what I can do now? I thought there was a way to install Linux on my hard drive docking it to the windows computer. Am I mistaken?

@rtyb - As helpful as that observation may be to others, are you saying there is nothing I can do about the computer at all now?  :(

Ok well you get GRUB errors when you boot your hard disk, so the hard disk may be OK. Even if your hard disk is bad you would still be able to boot from CD/USB. That is why I think the problem is with that hardware specifically or with the connections to that hardware. But if you can not boot your CDs or USBs you may have a problem with your hardware/cables.

Also try going into BIOS and try reloading the default or optimized settings. Then try rebooting again.

I would open my case and recheck every connection from motherboard to hardware and from power supply to hardware.

@rtyb- all GRUB errors are correctable.

P.S. when you boot your USB go into BIOS first and check to see if the USB is listed under hard disk in the hard disk boot order. When I use a flash disk 4 GB or larger it is listed with the hard disks under hard disk boot order. I have to move the flash disk up to #1 position to get it to boot.

---

### Post by CAcationu2 on 2009-10-22
SOLVED!! :P

I took the hard drive and docked it again to a windows machine, wiped it and made an NTFS partition. I then burned an 8.04 live cd (which is what I did for my first install ever) and loaded ubuntu on my comp. Downloaded updated NTFS locators and formatted, putting Ubuntu on the whole thing.

For some reason I couldn't make a 2nd partition for swap.. but I'm not worried about that. I'm up and running again!

Thanks to everyone here who helped me out with all their ideas. This helped me a lot. It also showed me how much of a n00b I really am with this, and how much more there is always to learn.

---

