---
title: "Can not get windows back"
date: 2010-01-24
forum: Hardware
---

### Post by fetanyl on 2010-01-24
ok so i am new to the whole ubuntu community and i want to thank everyone so far for helping me along you guys are really supportive but onto my problem.

[LEFT]i watched the movie Revolution OS and after watching this I decided that I wanted to try linux so i surfed the web a bit and figured I will try Ubuntu. So i burned Ubuntu to a disk and instead of partitioning my laptop for ubuntu and windows 7 i was impatient and installed ubuntu 100% balls to the wall never having used linux before and in the process deleted my backup partition containing vista (im so smart i know). well i only have the upgrade disk for windows 7 but have the full installation disk for windows xp. When i try to install windows xp from a dry boot i get the error [FONT=Georgia]ox0000007b. [/FONT]So I called microsoft up they said it was a hardware problem to call HP. I called HP up and they said that no one there knows how to use linux and that they can not help me unless I am running windows vista on my computer because my HP Pavilion dv7 1020us came with windows vista on it from the factory. I was looking around on the microsoft forums to a way to fix this problem but I have had no luck over the past 2 days and would like to know if anybody would be able to help me. I am going to try and get a set of windows vista xp disks and try and install that from a dry boot but other than trying that I can not think of a way to fix my computer. So if anybody has any advice on what to do feel free to share your ideas I am willing to try anything. I love ubuntu and plan on keeping a partition on my computer but i need windows to be able to do my school work.

Thanks for taking your time to help me and read this lengthy post also if you are feeling really nice and would like to sit and help my you can reach me on aim at irikrolalldaycuz and i havent looked into IRC yet but will be doing that tomorrow after i check this post.

Thank-you again
[/LEFT]

---

### Post by Greenwidth on 2010-01-24
I have not tried these, but might be worth a try:
[http://www.winsupersite.com/win7/clean_install_upgrade_media.asp](http://www.winsupersite.com/win7/clean_install_upgrade_media.asp)

---

### Post by fetanyl on 2010-01-25
yea i have tried installing windows 7 on a dry boot with the upgrade disc. but my computer does not recognize a disk in the cd drive on the boot up it gives me a system error: no emulation type 00

---

### Post by houseworkshy on 2010-01-25
There are some data recovery cd's on distrowatch.com but they are complicated.  I fear that as the drive has been formated you'd be unlikely to recover a whole working system anyway.
So, yes, probably it's start all over again time.  
In the short term, depending on what your schoolwork is, open office is a good set of applications and can read and save in windows compatable formats.

You could try running from the xp disc, as opposed to installing, then running fixmbr.  That would knock out your Ubuntu installation but if it worked would allow you to install windows.  That done, if you only use part of the hd, you could then install ubuntu into the unused part of the drive and end up with a duel boot machine.
 A lot of my friends are still on xp and without it's patches it is falling to bits online so untill you get vista I'd stick to Ubuntu for the web.

If the fixmbr doesn't work the best bet would probably be to run from the Ubuntu cd ( in the live cd mode .."try..") and use gparted.  First tell the whole drive to have an MSdos filesystem, it is the default, you will be told, correctly, that this will destroy all data on the drive.  Then format the whole lot to something windows can read, one of the fats or ntfs, make sure the bootable flag is checked ( right click on the drive after it is formated and choose manage flags).  Then try again.  For duel boot systems from scratch it is far easier to put windows on first, it can be done by editing the bootloader but that's a complication a newbie can do without.

As you currently have something which works,a guess but you've managed to post, and have work to do it is probably wisest to be cautious and leave it be for a while.  I'd wait for Vista to arrive and read up and use equivalent linux applictions in the meantime.  The following link is for a book, free to download, which would help you get started quickly if that is what you decide to do.

[http://www.ubuntupocketguide.com/download_main.html](http://www.ubuntupocketguide.com/download_main.html)

---

### Post by mihamil on 2010-01-25
What OS is the serial number on the bottom of the laptop for?  XP, Vista, or Windows 7.

---

### Post by Jefferythewind on 2010-01-25
It sounds to me like you should call windows, not HP.  Its not a hardware problem, you wanted to try a different OS on your hardware, and you didn't like it.  Windows should be able to look up your information and confirm you have purchased a genuine copy of the software, and give you a full installation CD...  but they probably won't do that.

So my advice would be to use Ubuntu, learn how to use it, you will be much happier in the long run, and you'll be laughing at those "windowz problems" in no time.

---

### Post by garvinrick4 on 2010-01-25
After you install Windows 7 the partition that says VISTA is not Vista anymore it is the image
of Windows 7. For some reason Microsoft has not changed its partition has a Label of Recovery
in "gparted" and in in "fdisk -l" linux reads as Vista. 

Any which way I agree with jefferythewind without the original  Vista disks you are not going
anywhere with Windows install.

---

### Post by fetanyl on 2010-01-28
yea i called hp they suck and i spent a lot of time on the phone with microsoft trying to get windows back and they can not help me but they said that i could buy a recovery cd for vista for $60 then upgrade to windows 7 which is what I want to do but I hate spending money. I think this is what I am going to do thank you for all the help and advice i will be posting back in a couple of days to let you guys know how everything went. 
 
Also my computer came with vista on it to answer the question to the person that asked and about the comment made about me liking ubuntu more than windows, i already love ubuntu more than windows. The way everything is set up and saposed to work on linux just makes more sense than windows and i have always disliked the way windows runs with all the problems it always has. It just sucks that people are so computer illiterate and do not want to learn so we are forced to live in a mainly windows only compatible world.
 
Thank you again guys for all the tips and advice

---

### Post by llawwehttam on 2010-01-28
Err try downloading windows 7. [Windows 7 ISO x86 and x64 Official Direct Download Links (Ultimate, Professional and Home Premium) » My Digital Life]("http://www.mydigitallife.info/2009/11/10/windows-7-iso-x86-and-x64-official-direct-download-links-ultimate-professional-and-home-premium/")

ultimate links are down now but the rest work. ( its legal as far as I know)

You will need to buy a license obviously. 

If its just vista you want I don't know any links for direct vista iso downloads.

---

### Post by redbook4574 on 2010-01-28
Just an idea but try downloading testdisk in linux, i have had good results recovering deleted partitions with this tool.

---

### Post by mihamil on 2010-01-28
> **fetanyl said:**
> yea i called hp they suck and i spent a lot of time on the phone with microsoft trying to get windows back and they can not help me but they said that i could buy a recovery cd for vista for $60 then upgrade to windows 7 which is what I want to do but I hate spending money. I think this is what I am going to do thank you for all the help and advice i will be posting back in a couple of days to let you guys know how everything went. 
 
Also my computer came with vista on it to answer the question to the person that asked and about the comment made about me liking ubuntu more than windows, i already love ubuntu more than windows. The way everything is set up and saposed to work on linux just makes more sense than windows and i have always disliked the way windows runs with all the problems it always has. It just sucks that people are so computer illiterate and do not want to learn so we are forced to live in a mainly windows only compatible world.
 
Thank you again guys for all the tips and advice



Fetynal, check your Private messages.

---

### Post by fetanyl on 2010-02-01
Well I fixed my computer thank you for all the help and advice. I was able to get a hold of recovery disks for Vista and was able to install windows back with no problems from the vista disk. I don't understand why it wouldn't let me download xp from the disks I guess it was something with drivers. But now I am finally dual booting windows 7 and ubuntu 9.10 and I gotta say Ubuntu kicks the **** out of Windows. Thank you again guys.

---

