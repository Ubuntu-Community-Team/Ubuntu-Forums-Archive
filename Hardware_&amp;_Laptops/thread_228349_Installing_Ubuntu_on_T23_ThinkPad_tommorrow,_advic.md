---
title: "Installing Ubuntu on T23 ThinkPad tommorrow, advice?"
date: 2006-08-03
forum: Hardware &amp; Laptops
---

### Post by Carbonfish on 2006-08-03
Hi all,

Tomorrow I am installing Dapper on an IBM ThinkPad T23 and am wondering if anybody has any hardware-specific caveats for me before I get started.

Haven't ever installed any Linux distro on a Laptop before and after reading the forums pretty carefully it is obvious that there are some issues that affect laptops that desktop users don't have to worry about as much (or at all), like power management, suspend/hibernate, temp control (fan speed), etc. 

So, I just thought that if anyone had any advice specific to the T23's, or to getting set up on Laptops in general, that would save me from trying to re-invent the wheel it would be greatly appreciated.

TIA for any and all advice.

KC

---

### Post by Orestes on 2006-08-03
Hi,

I've recently installed Ubuntu on a T22, and it worked fine with a few tweaks:

[LIST=1]
[*]Use the kernel parameter acpi=off
[*]After install, remove the package linux-image-386, because when you upgrade your packages, the new kernel package foobars your APM sleep.
[/LIST]

of course, it might be considerably different to your T23, but bear these things in mind in case you get any problems with ACPI.

---

### Post by Carbonfish on 2006-08-03
Thanks for the reply. Well, this is going to be a "leap of faith" for me when I get home from work and do the install as I plan on letting the installer wipe Windows 2000 off of the machine rather than doing a dual-boot and if something goes wrong, I have no way of re-installing Windows as I bought the ThinkPad factory re-furbed and it didn't include install disks. So once I boot to the live CD, I'm committed. ;) :twisted: 

UPS just dropped off the machine a couple of hours ago and it seems to be in good shape, although I haven't looked at the device manager yet (haven't had time), but so far it works fine in Windows. Now lets see if I can't "break it better"!

KC

---

### Post by Carbonfish on 2006-08-04
Install went great. Only a couple of things to figure out. I posted a question in the Installation forum about getting my internet connections figured out. If anybody has any suggestions regarding getting dial-up configured, I would appreciate them, but I don't want to ask the same question in two different forums.

Thanks,

Kent

---

### Post by Josue_ on 2006-08-04
This is a little bit out of topic, but have you tried playing some video clips yet? Did you notice jerky playback, I've that kind of problem on my T23.. just wondering if anyone else is experiencing the same.

I'm not using dial-up so can't help you with that issue :-/

---

### Post by Carbonfish on 2006-08-04
Josue,

The only video that I've played was the Ubuntu video in the examples folder, and it played fine.

As a matter of fact everything works so far except my DVD player and dial-up. but after reading the forums for a while I guess that this is a known issue. I'll keep reading.   ;-) 

I'm going somewhere with an open network this morning so I can try to get the wireless working.

KC

---

### Post by vfexx28 on 2006-08-06
> **Josue_ said:**
> This is a little bit out of topic, but have you tried playing some video clips yet? Did you notice jerky playback, I've that kind of problem on my T23.. just wondering if anyone else is experiencing the same.

I'm not using dial-up so can't help you with that issue :-/

yeah its a problem that I had too on my t23 , but it went away once I put the screen on full mode.

---

### Post by Gusher on 2006-08-10
Hi all, I am also trying to install Ubuntu LT on T23....am using LiveCD and only gets to Ubuntu Windows Manager banner and just stays there.......any pointers? I read above that i need to turn acpi off, but how do I do that? do I go to other options at initial installation? if so, what command do I need to get this going?

---

### Post by weekend warrior on 2006-08-11
ACPI on *should* work with the T23. I have it working on mine just fine. The only options I usually change are vga=792 (or 791) and floppy=thinkpad. But if you need to change some other options hit the F1 help on the Ubuntu boot screen, then F3 upwards for the options. Simply type them in at the end of the boot line at the bottom of the screen. 

Can't speak to the video problems since I haven't had any issues other than bad audio/video sync with a particular player. But, I have 768 megs of ram and a 7200 rpm drive which helps a great deal in multimedia (and overall) performance on the T23.


Edit: Almost forgot - Carbonfish, I'm not on dialup either so wouldn't know what to say. Your best bet finding others who can help on dialup is posting in the networking section if you haven't already. DVD playback info you'll find in the restricted formats docs.

[https://help.ubuntu.com/community/RestrictedFormats#dvd](https://help.ubuntu.com/community/RestrictedFormats#dvd)

---

### Post by Gusher on 2006-08-11
I see you are using a 7200rpm drive and more memory.....all my
specs are default from factory....perhaps I need more memory and a better drive...




> **weekend warrior said:**
> ACPI on *should* work with the T23. I have it working on mine just fine. The only options I usually change are vga=792 (or 791) and floppy=thinkpad. But if you need to change some other options hit the F1 help on the Ubuntu boot screen, then F3 upwards for the options. Simply type them in at the end of the boot line at the bottom of the screen. 

Can't speak to the video problems since I haven't had any issues other than bad audio/video sync with a particular player. But, I have 768 megs of ram and a 7200 rpm drive which helps a great deal in multimedia (and overall) performance on the T23.


Edit: Almost forgot - Carbonfish, I'm not on dialup either so wouldn't know what to say. Your best bet finding others who can help on dialup is posting in the networking section if you haven't already. DVD playback info you'll find in the restricted formats docs.

[https://help.ubuntu.com/community/RestrictedFormats#dvd](https://help.ubuntu.com/community/RestrictedFormats#dvd)

---

### Post by weekend warrior on 2006-08-11
Well it certainly helps, but I've also installed Ubuntu with less. Are you sure the install cd you have is ok? Did you check the md5sum? Have you booted it on another machine to see if it works ok?

Another option would be [www.xubuntu.org](www.xubuntu.org) 

XFCE will run just fine on a standard T23.

---

### Post by Gusher on 2006-08-11
The CD is a new one, from the ones I ordered for free...Ubuntu 6.06 LTS ....I did install it on a other 2 PCs just fine....will try [www.xubuntu.org](www.xubuntu.org)



> **weekend warrior said:**
> Well it certainly helps, but I've also installed Ubuntu with less. Are you sure the install cd you have is ok? Did you check the md5sum? Have you booted it on another machine to see if it works ok?

Another option would be [www.xubuntu.org](www.xubuntu.org) 

XFCE will run just fine on a standard T23.

---

### Post by weekend warrior on 2006-08-11
Also something to consider, a major update to Dapper was just released yesterday with quite a few fixes, including some install issues I believe. The release announcement is [here]("http://www.ubuntuforums.org/showthread.php?t=233444"). So make sure you get 6.06.1 and that may help you. 

If you have problems installing with the live cd utility, use the "alternate cd" for your install.

---

### Post by Gusher on 2006-08-11
> **weekend warrior said:**
> Also something to consider, a major update to Dapper was just released yesterday with quite a few fixes, including some install issues I believe. The release announcement is [here]("http://www.ubuntuforums.org/showthread.php?t=233444"). So make sure you get 6.06.1 and that may help you. 

If you have problems installing with the live cd utility, use the "alternate cd" for your install.

Okay, sounds great...will download the latest and burn to CD....btw, what do you mean by "alternate cd" ? Are you referring
to the LiveCD ?

---

### Post by weekend warrior on 2006-08-11
The "alternate cd" is an alternate to the live cd. The alternate cd is only for installing and uses the old installer but it worked better than the new live cd installer for quite a few people so keep it in mind when you're ready to install on your T23. 

There's an exlpanation of the two versions on the Xubuntu download page [here]("http://fr.releases.ubuntu.com/xubuntu/dapper/release/"). But make sure you download from the new release mirrors, I don't think the Xubuntu site has been updated with the new images yet.

---

### Post by Gusher on 2006-08-11
Thanks for clarifying this....will download using alternate cd....thanks again!

> **weekend warrior said:**
> The "alternate cd" is an alternate to the live cd. The alternate cd is only for installing and uses the old installer but it worked better than the new live cd installer for quite a few people so keep it in mind when you're ready to install on your T23. 

There's an exlpanation of the two versions on the Xubuntu download page [here]("http://fr.releases.ubuntu.com/xubuntu/dapper/release/"). But make sure you download from the new release mirrors, I don't think the Xubuntu site has been updated with the new images yet.

---

### Post by weekend warrior on 2006-08-11
Hope it works out for you this time.

Here's the link for the new Xubuntu release
[http://cdimage.ubuntu.com/xubuntu/releases/6.06.1/release.1/](http://cdimage.ubuntu.com/xubuntu/releases/6.06.1/release.1/)

---

### Post by Carbonfish on 2006-08-11
Weekend Warrior,

Thanks for the DVD advice. I found it independently and the DVD's play fine now. I have to use Gxine rather than totem, but that suits me fine as I hadn't ever used either one before so don't know what I might be missing. :-D  The one thing that's really jamming me up though is wireless networking. I have tried two different PCMCIA cards without success, and just went out and bought a Linksys WPC54G Notebook Adapter and searched the forums and found a couple of"how-to's" on getting the card configured. But I'm afraid that no matter how much I like Ubuntu that I might have to bail out and use another distro if i can't get the wireless to work on the T23. :neutral: I have a thread in the "Wireless" forum, but people seem to have sort of accepted that wireless is 'mostly' not supported in Ubuntu, and so are offering not-so-practical workarounds. 

Well, I guess I'll keep at it and see what happens. If I can't get it working after a few more hours of dinking with it, I'll have to move on.  *shrugs*   

To Gusher; I'm running everything on a factory re-furbed T23, and with the exception of being upgraded to 256 MB of RAM the thing is completely stock and everything works great (with the exception of the wireless networking and the modem of course!). So don't be discouraged. I used the Live CD and everything went as smooth as glass, so maybe you should try one of the other disks if you got more than one. Or, of course you could just do the alternate disk install thing.;) 

Later,

KC

---

### Post by weekend warrior on 2006-08-12
Oh no! don't give up - sounds like you've been given less than ideal advice. There are wireless cards that **will** work with hardly any effort at all!

Get one of the cards on this [list from the Free Software Foundation]("https://www.fsf.org/resources/hw/net/wireless/cards.html") and you won't be disappointed. They will work straight out of the box. I have a [Belkin F5D7010]("http://catalog.belkin.com/IWCatProductPage.process?Product_Id=136500") from that list and it works splendidly without any hassles at all, just plug it in and boot up - voila. 

Just remember to be very careful on the version numbers if there are any specified. Some card manufacturers change chips frequently and that's the key. You want to get cards that use the Ralink 2500/RT2400 chipsets.

eBay is the place to pick these up. There are usually some Belkins up for auction on the cheap. In fact I just checked and there are a few right now. Just search for F5D7010 and you'll find them.

HTH


Edit: Oh and as for Totem, don't worry you're not missing anything. that was the problematic "particular player" I mentioned before. Personally I think Totem is far and away inferior to VLC or MPlayer.

---

### Post by johnfarrow on 2006-08-12
Carbonfish,
   Where did you purchase the refurb T-23?:D \\:D/

---

### Post by Carbonfish on 2006-08-12
First off, Weekend Warrior, THANK YOU!, I am getting up as soon as I finish this post and taking back the Linksys WPC54G v.3 and buying the Belkin! Not only that but the Belkin is $15.00 less than I paid yesterday for the Linksys. It will be worth the 20 mile drive to get the right card (and save some money to boot!)

I will definately post back and let you know how things go.

Now on to you johnfarrow, I bought the T23 from an on-line vendor that calls themselves ThinkPad Depot. PLEASE, think twice before you buy from these people. My experience was a nightmare, although I am reasonably happy with the T23 (with a few exceptions that can be cheaply remedied). Their communication was *terrible*, they actually lied to me about when the product shipped and only admitted the lie when I treatened to "undo" the deal if they didn't provide me with a tracking number immediately, etc. 

I highly recommend that if you are looking for a ThinkPad that you go here:     [http://forum.thinkpads.com/index.php](http://forum.thinkpads.com/index.php)    first.
They are a great bunch of folks, and after you register (free to become a member) you can access the "Marketplace" and there are always good deals floating around. I wish that I had found that forum before I had bought my ThinkPad, but live-and-learn right?

Hope that helps, or maybe that's more than you needed?  :mrgreen: 

Thanks again W W, I can't wait to try this card!

Kent

---

### Post by weekend warrior on 2006-08-12
Good deal, hope all goes well.

and yes [thinkpads.com]("http://forum.thinkpads.com/index.php") is a great resource, as is [ThinkWiki]("http://thinkwiki.org/wiki/ThinkWiki") - quite a bit of useful Thinkpad info on these two sites.

---

### Post by johnfarrow on 2006-08-12
Carbonfish,
    You can't imagine how much you have helped me.  I was considering getting a replacement of myT-23 because the fan is failing.  Because of the link that you supplied,  I was able to log on to an IBM Thinkpad forum, learn the steps required to replace the fan and order the exact replacement from IBM for 40.50 + shipping.  I was thinking of buying a new or used IBM, but you have saved me so much.  Thank You So much....

John Farrow
[email]mauralae@gmail.com[/email]:-D

---

### Post by Carbonfish on 2006-08-12
Mr Farrow,

I am glad that I was able to do whatever little bit that I could and am genuinely pleased that things went well. IMHO that is the first best strength of these forums. To be able to tap into the "hive-mind" and benefit from the combined resources of the community. There is so much that I have to learn, that I don't even know what I don't know. But that said, I will gladly share the little bit that I *do* know.

Good luck, and fair winds.

Kent

---

### Post by marin.r on 2006-08-13
Hi guys,

sorry for hijacking your thread, but as we're the T23 users around I just wanted to ask you how is ACPI control working on your laptops ?
I made a thread yesterday about my first problem and nobody seems to know about it as there are still no replies there.
So far I found that with Dapper fresh installed yesterday and both before and after update things are NOT the way they should be.

I cannot "echo" anything to any file in /proc/acpi/ibm , nor /sys/platform/i8042/serio0/... if I recall where the trackpoint sensibility and speed settings are located and in the ibm directory where I've got LCD brightness. It just says permission denied (thats with sudo too), or in the case with trackpoint settings - doesn't output anything, just doesn't change the settings.

The LCD Brightness is a problem because everytime the laptop boots or enters gnome or resumes it gets resumed to higher level of brightness than I like it respectivelly left it at.

Please give me a hand on this, its very annoying:-k

---

### Post by Carbonfish on 2006-08-13
Hi marin.r

I wish that I could help you with your problem. I am rather new to the ThinkPad as I have owned mine less than a month. I can say that my "brightness" controls seem to work fine, but then again, I have only tried to make adjustments using the fn and brightness keys, which work fine. As to my trackpoint, I had never touched one before I installed Ubuntu, so I wouldn't know if something was amiss. I have never tried to make any of those changes so I am glad that I'm happy with what they are doing now.

Sorry I couldn't be more helpful, but perhaps someone will come along with better info.

You might try going to this Forum:
  
[http://forum.thinkpads.com/index.php](http://forum.thinkpads.com/index.php)

If you look in the forums list you will see a Linux forum listed. Those folks have a huge reservoir of knowledge to draw from and may very well have your answer. To post on the ThinkPad forum you will have to register, but don't worry, it's free and they don't require any really personal info.

Good luck!

KC

---

### Post by IcemanV9 on 2006-08-14
@marin.r: sudo su, then echo "whatever you need" to any file in /proc/acpi/ibm. exit when done using "sudo su".

---

### Post by marin.r on 2006-08-15
Thanks IcemanV9, it worked for /proc/acpi/ibm, but I really don't understand what is the difference between sudo something or doing it as root.
Anyway, I still can't echo anything to /sys/... where the Trackpoint settings are.

Carbonfish - its a real pain to use the trackpoint at default sensitivity, you'll notice the difference, the default can cause medical problems, I swear :)

---

### Post by weekend warrior on 2006-08-15
[configure-trackpoint]("http://tpctl.sourceforge.net/configure-trackpoint.html") may help avoid those nasty medical problems. ;) 

tpctl is in the repos and I'm assuming configure-trackpoint is bundled in that package but don't quote me as I haven't installed it since I mostly use a wireless mouse when I'm not on the keyboard. Let us know how it turns out for you.


HTH

---

### Post by marin.r on 2006-08-17
Hi again weekend warrior & all,

I installed tpctl however it's not working as it seems its looking in /dev/thinkpad for all the info etc.
Also configure-thinkpad is not included.
Anyway, I don't see how no matter what front-end could possibly write anything in the same place (/proc/blahblahblah/sensitivity or speed) where I fail to write as root :)

I do know there's no complete happiness, but this drives me nuts as I've made it work before, years ago perhaps, even on a bare slack (where I had bunch of other problems unresolved, but...)

---

