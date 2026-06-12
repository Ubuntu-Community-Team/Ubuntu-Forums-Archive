---
title: "New HP laptop advice/recommendation"
date: 2010-03-29
forum: Hardware
---

### Post by alicefred on 2010-03-29
[COLOR=#000000][FONT=Times New Roman, serif][SIZE=3]I am considering to buy a new mid range laptop and after going through some reviews I have narrowed my purchase decision down to HP G62t and HP Pavilion dv6t. Both laptops have almost same configuration and available at [http://www.dealrocker.com](http://www.dealrocker.com) with good discounts. I read somewhere that dv6t has Protectsmart hard drive protection feature. Wondering is the hard drive protection something to pay much attention to.?[/SIZE][/FONT][/COLOR]
 

 [COLOR=#000000][FONT=Times New Roman, serif][SIZE=3]Any help will be greatly appreciated.[/SIZE][/FONT][/COLOR]
 [COLOR=#000000][FONT=Times New Roman, serif][SIZE=3]Thanks..[/SIZE][/FONT][/COLOR]

---

### Post by schmo on 2010-03-30
I am very seriously thinking of purchasing the G62T also.  The very friendly HP sales rep suggested that if I wanted more power then give the DV6 a try.  I wonder about Ubuntu though.  I have heard that both the integrated Intel video adapters and the ATI adapters in general have lousy linux support.  But maybe things will be okay with these...?

Here is a post for a guy installing ubuntu on his acer with apparently similar video adapter:

[http://sishads.wordpress.com/2010/03/14/ubuntu-9-10-on-acer-5740intel-hd/]("http://sishads.wordpress.com/2010/03/14/ubuntu-9-10-on-acer-5740intel-hd/")

See also: 
[http://h30434.www3.hp.com/t5/tag/ubuntu/tg-p/board-id/OS]("http://h30434.www3.hp.com/t5/tag/ubuntu/tg-p/board-id/OS")
[http://h30434.www3.hp.com/t5/tag/ubuntu/tg-p/board-id/OS]("http://h30434.www3.hp.com/t5/tag/ubuntu/tg-p/board-id/OS")
[http://h30434.www3.hp.com/t5/Operating-systems-and-software/Ubuntu-and-dv6-Series/m-p/172472/highlight/true#M25919]("http://h30434.www3.hp.com/t5/Operating-systems-and-software/Ubuntu-and-dv6-Series/m-p/172472/highlight/true#M25919")

---

### Post by alicefred on 2010-03-31
Thanks for linking..! Very useful..

---

### Post by schmo on 2010-03-31
Please post what you decide to do and your experience.  I am considering running windows for a little while if I can't get Ubuntu to work right.  In other words, letting the Ubuntu and drivers catch up...

---

### Post by ram2500 on 2010-04-01
I have an HP Pavilion (I don't know the model number as I am at work, grading papers and I don't have it with me) but it has an Athlon dual core, runs Windows 7 (formerly Vista) with Ubuntu and has the Broadcom chipset, which requires activation through the restricted drivers application. It works well and I have had no hiccups with Ubuntu, and that's with wireless. I know that there's many variations with HP Pavilion (and any other laptop) across the board, but before you buy, pay particular attention to the wireless chipset and inquire about its ability to work without headaches.

---

### Post by schmo on 2010-04-01
Boom, I just pulled the trigger on the G62t.  It's relatively new so the reviews out on the web are basically garbage (they just recite the specifications and have a picture).  The only reviews were on the HP site itself.  They seemed legit.  I just hope Ubuntu works okay.  I will detail my experience.

---

### Post by NarcT on 2010-04-18
Hey guys I just got my G62t and it works great with Ubuntu 10.04 Beta 2....I was bummed at first with the 9.10 release with no screen response but so far my install of Beta 2 has been working really well.  I'll let ya know if theres any incompatibility but so far wireless, graphics, sound, everything works.

---

### Post by NarcT on 2010-04-19
Ok so everything except sound through the external speakers work.  Plugging in headphones works fine except w/o headphones nothing comes out.

---

### Post by Manyette on 2010-04-19
Have a look at this post.  It fixes many of the HP sound problems.  Note the mod to alsa-base.conf file.  It worked for my HP G71

[https://answers.launchpad.net/ubuntu/+source/alsa-driver/+question/91675](https://answers.launchpad.net/ubuntu/+source/alsa-driver/+question/91675)

Don

---

### Post by NarcT on 2010-04-19
Manyette...What version of Ubuntu are you running? I ask because when I search for "alsa-base.conf" it returns that there is no file.  I think this is because I'm running 10.04.  I'm currently looking for instructions to upgrade alsa for Ubuntu 10.04

---

### Post by Manyette on 2010-04-19
> **NarcT said:**
> Manyette...What version of Ubuntu are you running? I ask because when I search for "alsa-base.conf" it returns that there is no file.  I think this is because I'm running 10.04.  I'm currently looking for instructions to upgrade alsa for Ubuntu 10.04

Hi NarcT,

You may very well be correct, since I'm running 9.10 (Karmic).  That was the fix for that version, but I do understand that Lucid made some changes in that area.  Apologies if I caused you too much trouble.
Don

---

### Post by Kubro on 2010-05-05
I had successfully used this fix in 9.1, but when I upgraded to 10.04 I lost sound. tried this same fix, but it does not work. still no sound. Will keep looking. 10.04 LTS on an HP G71.

---

### Post by Manyette on 2010-05-05
Hi Kubro,
Well, now I do not understand.  I am now running 10.04, and it came up with the sound working perfectly.  This is on a HP G71-340US machine, and Lyric fixed the problem that I had to add the fix for in Karmic.

---

### Post by Kubro on 2010-05-05
> **Manyette said:**
> Hi Kubro,
Well, now I do not understand.  I am now running 10.04, and it came up with the sound working perfectly.  This is on a HP G71-340US machine, and Lyric fixed the problem that I had to add the fix for in Karmic.

Ok, I have the exact machine HP G71-340US. I booted off of a 10.04 USB key, and amazingly the sound works. So, I have obviously messed something up. I apologize for wasting your time here.

---

### Post by Manyette on 2010-05-05
Hi Kubro,
Certainly no waste. Sometimes it just helps to know what others have found.  I keep telling people that after downloading a file, you should check the MD5SUM to make sure the download was good.  I've never had a bad download, but I do know it can happen. And, I've never had K3B give me a bad burn either, but it can happen.  Good luck with the reinstall.

---

### Post by Welly Wu on 2010-06-15
Hello! I too am considering the purchase of an HP G62t notebook PC with these specifications:

biscotti
Genuine Windows 7 Home Premium 64-bit
Intel(R) Core(TM) i5-520M Dual Core processor (2.40GHz, 3MB L2 Cache) with Turbo Boost up to 2.93GHz
4GB DDR3 System Memory (2 Dimm)
500GB 7200RPM SATA Hard Drive
512MB ATI Mobility Radeon(TM) HD 5430 Graphics with 5-in-1 integrated Digital Media Reader and HDMI
15.6" diagonal High Definition HP LED Brightview Display (1366x768)
SuperMulti 8X DVD+/-R/RW with Double Layer Support
Microphone Only (no webcam) with 5-in-1 integrated Digital Media Reader and HDMI
Wireless-N Card with Bluetooth
HP Keyboard
6 Cell Lithium Ion Battery (standard)
No Modem
Microsoft(R) Office Starter 2010
HP Home & Home Office Store in-box envelope

My concern is compatibility with Ubuntu 10.04 Lucid Lynx LTS. Has anyone here recently purchased a similarly equipped PC and successfully installed with out of the box compatibility? Please reply with your experiences and opinions. Thank you.

---

### Post by Manyette on 2010-06-15
Hi Welly Wu,
Well, I have a close cousin to that machine.  A HP G71-340, and find it entirely compatible.  I would think you would be quite happy with it. But you might want to ask folks who have the Radeon video card.  That could be a problem.

---

### Post by Welly Wu on 2010-06-15
Thank you for your reply. I contacted Hewlett Packard today regarding their G62t notebook PC and the representative said that it is not compatible with Ubuntu 10.04 Lucid Lynx LTS 64 bit version. I am going to buy it next month. After I create system restore DVD(s), I am going to install Ubuntu on it side by side with Windows 7 Home Premium 64 bit edition. I will let the community know how it goes with further posts.

---

### Post by Manyette on 2010-06-15
Hi Again,
I can confirm that the system restore DVD's work well, I have used them to do a restore and they work perfectly.  If HP says it is not compatible, then I strongly suspect that it is the Radeon video that is the problem.  Hopefully someone using that particular video will chime in on their experiences.  Good luck.

---

### Post by mightyiam on 2010-07-17
I'm considering purchasing an HP G72T.

Hardware support I'm worried about is:

I'm quite certain that if I get the Intel HD option, then it will be fully supported. This is from my experience with Intel HD in Ubuntu.

The ATI Radeon HD 5430 should be somewhat stronger. I am not sure that I actually need it. There seems to be support for this card only in the proprietary driver and not in the RadeonHD driver, which only has preliminary HD 5000 series support.

And the future of RadeonHD isn't clear because Novell laid off some main developers who were working on it.

I'm not sure what the differences between the Intel HD (which one is it, anyway?) and the ATI Radeon HD cards will mean for me. I don't intend to play any games but I do intend to use *some* CAD.

The wireless card manufacturer isn't mentioned. Driver download page for this product has drivers for several different chips. Just about all WiFi chipsets on the market are listed there.

I guess that the card reader will work.

The webcam is a huge shot in the dark unless someone can say that it works on his G62t.

The G72T and the G62T seem related. I bet they have the same boards.

Can any G62T user provide details about his hardware constellation like the output of lspci -nn and lsusb, and also tell which parts of his system work or not? That would be great help.

Blessings,
Shahar

---

