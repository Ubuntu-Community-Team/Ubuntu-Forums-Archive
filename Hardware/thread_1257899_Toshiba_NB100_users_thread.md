---
title: "Toshiba NB100 users thread"
date: 2009-09-04
forum: Hardware
---

### Post by jonick on 2009-09-04
Hi Guys,

I just thought I would start a thread to share common experiences of using the NB100.

I bought mine about two months ago as a 512Mb machine, that had Ubuntu 8.04 UNR pre-installed.

The first thing I did was to rip out the memory and replace it with a 2Gb stick - I have since found that although the machine is faster than it was with 512Mb, I hardly ever use more than 20 - 30 % of the available ram, so a 1Gb stick would have done just as well.

As for operating systems, the pre-installed version of Ubuntu 8.04 worked reasonably well, but I had trouble with the repostories and upgrades took for ever. I also had issues as the machine was configured as a low power device, and not i386, which caused issues when trying to install software such as Skype

I decided to give Ubuntu Jaunty 9.04 UNR a try, and downloaded the .img file from Ubuntu.com. The install worked fine, but I found that Jaunty had poor driver support for the intel video chipset, so flash was more or less useless, Skype also suffered from stutters due to the pulse audio.

I decided to try out some other distro's - So before proceeding any further I decided to buy an external DVD drive, so that I could get back to a factory install using the recovery disc if everything failed.

The first distro I tried was Open Suse, which installed well, and found the wireless straight away, but I found that it ran very slowly as compiz is enabled out of the box - I didn't like the feel of Open Suse, and it lasted about an hour on my drive before I trashed it.

Next I tried Debian Lenny. The live CD worked well and the system seemed quite responsive, but there was no wireless detected out of the box and with Debian you also need to add codecs and restricted bits and bobs after the install to get goodies like flash, DVD playback mp3 playback etc.... ALSO, PLEASE NOTE currently the install process on the Debian live CD is broken... it will not install correctly, you will need to use the standard istallation disc's if you want to install to HDD.

Next on the list was one of my favourite distro's PcLinuxOs. I hit some real issue's with this one. I tried to boot their live CD for a week before I discovered that a bug in my BIOS was stopping PcLinuxOs from recognising my HDD. You must have BIOS version 1.5 or above, and put your HDD into compatability mode, before PcLinuxOs will recognise the HDD.

Out of the box PcLinuxOs worked very well, and the system was very responsive, however the kernel they are currently using doesn't like our Atheros wifi card at all, and PclinuxOs fell back onto Mad-Wifi drivers (which were automatically added during the install). The Mad-Wifi drivers worked to a point, but I suffered from repeated drop-outs on the Atheros WiFi connection - I still haven't found a solution to this one.

So, Lastly, I decided to give Ubuntu Karmic UNR a go, I put Karmic Alpha 4 on about ten days ago, and upto now, apart from one or two glitches (which you would expect as it is Alpha) everything works great. The video performance with flash is greatly improved over Jaunty, and the alsa sound works much better too. I am using Skype V2 at the moment and I have perfect audio on both receive and transmit.

So, that's where I'm at up to now...... how about you?

Best regards,

Jonick.

---

### Post by zietbukuel on 2009-11-01
I've installed ubuntu 9.10 on my toshiba nb100, but it is REALLY slow, it is totally unusable. Previously I was using UNR 9.04 and it ran ok, but with the classic interface,not the UNR because the machine was soooo slow as it is now. I'm now reading the forums and now I see they have removed the desktop switching app... Now, what should I do to make my machine usable again??? maybe the graphic drivers are failing, etc I don't know... PLEASE HELP!
thanks.

---

### Post by jonick on 2009-11-03
Hi zietbukuel,

Karmic *Can[I]*[/I] run quite well on the NB100. The Intel video driver is better than on Jaunty.

I had the same experience as you when using Jaunty, and found that the NBR desktop was too slow, so ran the classic desktop instead.

I have been running Karmic since Alpha 3, and found that the NBR desktop became stable at alpha 4, and was certainly quite solid on the release candidate. I completely re-installed when the Release candidate was issued, and have just run the updates since then, and all works fine - the speed using the NBR desktop is quite acceptable, and flash player performance is a lot better than Jaunty.

What BIOS version are you running on the NB100 ? I find V1.9 works well. Anything lower than V1.7 could cause problems.

Did you do a clean install of Karmic, or did you upgrade from Jaunty? ... I have heard lots of horror stories regarding the upgrade process.

Are you dual booting with Windows?

If it's at all possible, I recommend backing up your data and doing a clean full install. I think you will find that its worth it if you can get Karmic.

Best regards,

Jonick

---

### Post by hhboyhh on 2009-11-03
I am using the Karmic Koala and every thing works fine. Its a really improve from Jaunty. But!! I have two big problems. First(and this problem seems to be kind off common) the UNR-launcher gets really slow, this happens sometimes and i have idea why. Then (and i have not seen anyone else with this problem) my netbook just frezzez(sorry for my bad english U.U). I tried UNR 9.10 BETA and I could only use it for a couple of minutes before it freezes. Now with the final release this problem is less common but its still there, now after half an hour or so my system just freezes. I am not sure what is cousing this, but the same happened to my when i was testing Moblin.

---

### Post by sandman652001 on 2009-11-04
I have had the nb100  since 8.4 came out. and have been running netbook remix in the various versions with no problems, if not sluggish graphics under jaunty. Personally I usually install the lpia port because it seems to give better battery performance. I have to say that karmic seems to be the best so far. I'm using bios version 2.10

---

### Post by hhboyhh on 2009-11-04
I Think the problem is that my BIOS is not fully updated U.U  I have searched for the updates but i cant find them :s can you tell me pls where can I download them??

Best Regards from Peru
Cesar

---

### Post by sandman652001 on 2009-11-05
You can find bios updates on the Toshiba site for your area that in your case I think is [http://www.csd.toshiba.com/cgi-bin/tais/support/jsp/home.jsp](http://www.csd.toshiba.com/cgi-bin/tais/support/jsp/home.jsp)

chose downloads>mini notebook>your model

> **hhboyhh said:**
> I Think the problem is that my BIOS is not fully updated U.U  I have searched for the updates but i cant find them :s can you tell me pls where can I download them??

Best Regards from Peru
Cesar

---

### Post by hhboyhh on 2009-11-05
I updated my BIOS yesterday but i still have the problem :(

---

### Post by sandman652001 on 2009-11-05
is it a clean install or an upgrade? I had a similar problem with one of the betas, but since my bios update I no longer have it

---

### Post by hhboyhh on 2009-11-05
It is a clean install, but i installed it when my BIOS was 2.0. Yesterday i updated it(using windows) to 2.1. Maye i should try a clean install one more time, hope this time works.

---

### Post by sandman652001 on 2009-11-06
it might be worth a try, good luck

---

### Post by hhboyhh on 2009-11-08
Nope, i still have the problem......... U.U
I will give a try with the desktop edition

---

### Post by Tuliku on 2009-11-09
Here's my 3 cents:

NB100, changed the mem from 1 GB to 2 GB, and the harddisk from 160 GB to 320 GB.
Had a triple boot running, Ubuntu 8.10, Win XP, and Mac OS 1.5.6.
Was nice but not great, removed all, and only installed Ubuntu 9.10.

First the UNR, but the desktop is so crappy. Was able to deactivate it with help on this forum, but things like right click on the desktop still didn't work.

Yesterday i installed the normal 9.10, and looks great.
After a few installations like adding medibuntu, ntfs prog, audacious, audacity, thunderbird, etc, it worked very nice.
Them some mandatory updates came which i did, and now the only issue i am having is that the powering off does not work... Suspend account does work.

I've checked now the link for the bios upgrade as i might have an old one, but in the link i starts with NB 105... I cant find anything for my NB 100.
Will search more tonight.

**--edit--**
Found the bios on the european toshiba website: [http://eu.computers.toshiba-europe.com/innovation/jsp/supportMyProduct.do?service=EU](http://eu.computers.toshiba-europe.com/innovation/jsp/supportMyProduct.do?service=EU)

**---edit---**
Re-installed the desktop version 9.10 (not the UNR) and tried to update the Bios, from 1.60 to 2.10 found on the link above.
The linux version gave me constantly the same error, module version not compatible.
So i booted up a windows cd, and ran the windows version ofth new bios, and all is working smoothly again.
Me just very careful now with the mandatory updates..

---

### Post by Tuliku on 2010-01-05
After installing many different versions, and setup ways, i finally have ti exactly like i want it.
If interested, click [**here**]("http://ubuntuforums.org/showthread.php?p=8612793#post8612793") for a full guide on how to setup and tweak your nb100

---

### Post by Extub on 2010-02-16
Hi
 
I was delighted with my NB 100 running Ubuntu 8.04. Everything ran pretty good. Then, without warning it slowed to a crawl. I was watching BBC Iplayer (which used to run perfectly) but now although the audio is OK, the video just shows a few frozen frames. Other progrms are now running slower - even slideshows. When I checked the system monitor, it showed both CPUs running anything between 50% and 90% even when only the system monitor was running. Eventually, in frustration, I loaded the recovery disc via external DVD but the problem is identical. Do I have a hardware problem??

---

### Post by JohnMoriarty on 2010-04-22
Like Extub, I've noticed a significant fall in performance on my NB100, and this is especially problematic when browsing scripted web pages and pages with flash content; BBC iplayer is almost unwatchable with a jerky picture.

Any ideas on what is causing this, or how it could be fixed?

---

