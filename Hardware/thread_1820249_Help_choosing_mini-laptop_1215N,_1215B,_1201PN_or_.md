---
title: "Help choosing mini-laptop: 1215N, 1215B, 1201PN or 1215P"
date: 2011-08-07
forum: Hardware
---

### Post by rodrigo.toste.gomes on 2011-08-07
I'm thinking of buying a small laptop for travelling and school.
I'll only be using linux on this laptop. However, the ones who seemed best for me seem to all have compatibility or performance problems.
First, I thought of buying the ASUS 1215N netbook. However, it uses optimus technology, and I wanted to buy it mainly for the ION2 chipset.
Then, I thought of buying the ASUS 1215B laptop, but it has an AMD graphics card, and I don't know how it would perform with linux (I switched to using only NVIDIA, since it provided the best compatibility when I started using linux). Anyone has any opinions?
Then, I though of the ASUS 1201PN, but the fact that the CPU is single core, I don't know how well the drivers for ION2 are in terms of performance and that it isn't easy to find a store selling it have put me off.
I read in these forums that the 1215P has great compatibility with linux, but I don't really like the intel graphics card because of its performance.

I'd like a laptop that can at least run games made with the source engine (for example, Half Life 2 or CS:Source) with wine, play at least 720p video (not on flash - I know the plugin doesn't yet work very well :/) and have at least an 11.6" and at most a 13.3" screen size. At most, I can pay 600$ for it.
Although all the laptops I listed are ASUS, I'm open to other brands, I only listed these because they were the ones I found that best suited what I want so far.

Thanks for your time!
Rodrigo

---

### Post by SalHelder on 2011-08-07
As far as I've seen the ION doesn't seem to work well under Linux, it seems that it works only without acceleration rendering. Anyway what store do you intend to buy the laptop from? It would help giving a place to see available options that you can buy.

---

### Post by rodrigo.toste.gomes on 2011-08-07
> **SalHelder said:**
> As far as I've seen the ION doesn't seem to work well under Linux, it seems that it works only without acceleration rendering. Anyway what store do you intend to buy the laptop from? It would help giving a place to see available options that you can buy.

Thanks for the response.
So I should stay away from Ion. What about AMD graphic cards?
I don't have a preference for a particular store. Until now, I've only checked Amazon, Newegg and ebay, but I'm open to buying from any store.

---

### Post by SalHelder on 2011-08-07
Amazon.com? I'm just asking because you'd better get a store that sells to your country without having to pay shipments or at least high price shipments.

---

### Post by rodrigo.toste.gomes on 2011-08-07
> **SalHelder said:**
> Amazon.com? I'm just asking because you'd better get a store that sells to your country without having to pay shipments or at least high price shipments.

Right now I'm only checking US stores, since I'm moving to the US next week, so shipment isn't an issue, and I'd like to get a laptop with an US keyboard.
Thanks for the concern anyway.

Does anyone know if I'd be OK with the AMD card, or if the Intel GMA 3150 (on the 1215P) is enough for my needs? Or do you have any idea of a laptop from another brand that would be good?

Something I forgot to mention, although I don't really need it, but I'd like a laptop with either at least 6h battery life under low usage, or with easy/cheap to get extra batteries.

---

### Post by SalHelder on 2011-08-07
Low end Ati/AMD (particularly some new models) might give some problems likely to be solved at the time of the next Ubuntu release. The intel GMA also seems kind of a little trouble there, as far as I know something like a GMA 450 or 950 or even the Intel HD, will work better. Essentially AMD cards in the long run will tend to be better than Intel cards.

And don't keep big expectations on gaming with Wine, just saying.

---

### Post by rodrigo.toste.gomes on 2011-08-07
I've been doing some research, and it seems that a laptop the AMD Fusion chipset with the Radeon HD 6310 would be the best choice for me.
Does anyone know if the Radeon HD 6310 is currently working well with linux, or is expected to work well in the near future (gaming in wine isn't very important for me, I'm more concerned with video performance, and I want it to at least handle 720p videos well)?

---

### Post by Björn on 2011-08-08
Hi, i'm in your position as well, the problem is that it seems like people have been having problems with getting the fusion to suspend and wake up properly. Some have had success with disabling something called C6 in bios but it hasn't worked for everyone afaik. ION on the other hand seems to have problems switching between different onboard graphics.

Björn

---

### Post by rodrigo.toste.gomes on 2011-08-08
> **Björn said:**
> Hi, i'm in your position as well, the problem is that it seems like people have been having problems with getting the fusion to suspend and wake up properly. Some have had success with disabling something called C6 in bios but it hasn't worked for everyone afaik. ION on the other hand seems to have problems switching between different onboard graphics.

Björn

I'm not concerned with the sleep issues. For me, the most important is knowing if it performs well, and if I can watch videos and maybe play some simple 3D games.

---

### Post by SalHelder on 2011-08-08
On New Egg I found three that are likely to work well under Ubuntu:

ASUS Eee PC 1015T-MU17-BU | AMD HD 4250 at 280 $: [http://www.newegg.com/Product/Product.aspx?Item=N82E16834220854](http://www.newegg.com/Product/Product.aspx?Item=N82E16834220854)

HP ENVY 13-1030NR | AMD HD 4330 at 600 $:[http://www.newegg.com/Product/Product.aspx?Item=N82E16834157729](http://www.newegg.com/Product/Product.aspx?Item=N82E16834157729)

TOSHIBA Satellite T135D-S1325RD | AMD HD 3200 at 330 $: [http://www.newegg.com/Product/Product.aspx?Item=N82E16834114986](http://www.newegg.com/Product/Product.aspx?Item=N82E16834114986)

Anyway check for reviews to see how they deal with battery life and video playback, or anyother thing you guys might like them to do.

---

### Post by rodrigo.toste.gomes on 2011-08-08
Thanks for the help SalHelder, but I don't think I'm going to buy any of those.
The ASUS is just to small for me. The HP is attractive, although a bit heavy, and that together with the highest price makes it a bit unattractive xD (although I can keep it as a possibility).
The toshiba seems like a good possibility, I just don't like the red color, so I have to find it in another color (it seems, unfortunately, that the black version costs more :S).
I also found this:
[http://www.ubuntu.com/certification/hardware/201106-8092](http://www.ubuntu.com/certification/hardware/201106-8092)
It seems Ubuntu 11.04 should work with the Fusion hardware.
I'm thinking of either going for the black toshiba you showed me or an HP pavilion dm1z. The HP seems like a better long run investment, but I'd like it to work well at least in the short run.
Does anyone with have a similar laptop and can share experiences about graphics performance (videos and output of glxgears for example)? I don't care about the sleep issues.

Thanks for your time!

---

### Post by SalHelder on 2011-08-08
I'm also going to buy one, the thing is here in the old continent with your price range I seem to get much better laptops, the thing is mine will be bigger with the 15,4" screen. Well, I'll probably post here how it went after I acquire it and test Ubuntu or Mint. 

Anyway I completely forgot about the certified hardware list, it seems that 10.10 Maverick seems to support more laptops than other versions, keep that in mind when looking.

---

### Post by SeijiSensei on 2011-08-08
> **SalHelder said:**
> As far as I've seen the ION doesn't seem to work well under Linux, it seems that it works only without acceleration rendering. Anyway what store do you intend to buy the laptop from? It would help giving a place to see available options that you can buy.

Our ASUS 1201N works fine using ION, the proprietary NVIDIA drivers in Linux, and VDPAU acceleration in mplayer.  1080p isn't really relevant since the screen maxes out at 1366x768.  The problem is that you can't buy pure ION machines any more.  NVIDIA in their "wisdom" has chosen to foist the Optimus platform on all of us without writing solid Linux drivers to support it.

Other than running hot, the 1201N is a fine little machine.  Maverick installs without a hitch, including support for wifi and the webcam.  There's a weird [microphone problem]("http://ubuntuforums.org/showpost.php?p=11068088&postcount=6") that requires some diddling to fix. 

There are still some 1201N's [available online]("http://www.google.com/products/catalog?hl=en&client=ubuntu&hs=30n&channel=fs&q=1201n+shopping&bav=on.2,or.r_gc.r_pw.&biw=896&bih=384&um=1&ie=UTF-8&tbm=shop&cid=6665548156432950391&sa=X&ei=bgpATrG8KYSutweK5dCfDA&ved=0CB8Q8wIwAQ") including brand-new ones.  Their prices haven't fallen either; if anything they cost more now than they did when we bought ours a year ago.  I suspect the Optimus issues may have something to do with that.

---

### Post by rodrigo.toste.gomes on 2011-08-08
> **SeijiSensei said:**
> Our ASUS 1201N works fine using ION, the proprietary NVIDIA drivers in Linux, and VDPAU acceleration in mplayer.  1080p isn't really relevant since the screen maxes out at 1366x768.  The problem is that you can't buy pure ION machines any more.  NVIDIA in their "wisdom" has chosen to foist the Optimus platform on all of us without writing solid Linux drivers to support it.

Other than running hot, the 1201N is a fine little machine.  Maverick installs without a hitch, including support for wifi and the webcam.  There's a weird [microphone problem]("http://ubuntuforums.org/showpost.php?p=11068088&postcount=6") that requires some diddling to fix. 

There are still some 1201N's [available online]("http://www.google.com/products/catalog?hl=en&client=ubuntu&hs=30n&channel=fs&q=1201n+shopping&bav=on.2,or.r_gc.r_pw.&biw=896&bih=384&um=1&ie=UTF-8&tbm=shop&cid=6665548156432950391&sa=X&ei=bgpATrG8KYSutweK5dCfDA&ved=0CB8Q8wIwAQ") including brand-new ones.  Their prices haven't fallen either; if anything they cost more now than they did when we bought ours a year ago.  I suspect the Optimus issues may have something to do with that.

That seems like a good choice for me.
Can you tell me anything about 720p video performance and games?
What about productivity? Does it become slow if you have a lot of programs open? I'm mainly planning to use this laptop for watching videos, surfing the web, some coding (I use eclipse for a lot of projects, which is a bit heavy on memory and CPU, do you know if it would handle it well?) and a very little bit of gaming for when I'm bored.

Thanks for your time!

---

### Post by SeijiSensei on 2011-08-08
> **rodrigo.toste.gomes said:**
> That seems like a good choice for me.
Can you tell me anything about 720p video performance and games?
What about productivity? Does it become slow if you have a lot of programs open?

My daughter played Dragon Age: Origins on the Win7 side with some success though she had to adjust the video settings to get decent performance.  We were using the proprietary driver from NVIDIA, too.  In Linux, it plays 720p H.264-encoded videos with *SS subtitles at full speed using the VDPAU driver with mplayer-based software like smplayer.

On the down side, the speakers are rather poor, and it does run pretty hot.  I've been looking for a utility for Ubuntu to control the fan, but I haven't found one yet that works.  We also had what appears to be a common problem with this machine. After a month or two, the power supply plug no longer fit correctly into the socket.  We had to send it back for repair, but ASUS handled the case well.  We got free shipping both ways because we had bought it from Amazon; we only needed to put it in a box and deliver it to FedEx with a form.  It was returned in about ten days as I recall.  You might consider buying a factory-refurbished model if you can find one.  It might have had this problem and been repaired like ours.  Since the repair it's worked flawlessly.

We have the standard 2GB of memory, and I have no problem running multiple applications in Kubuntu 10.10 upgraded to KDE 4.6.  I haven't much experience with the Windows side so I can't tell you about that.  You could always upgrade the memory; it supports 8GB with a 64-bit operating system.

As for overall performance, it is, after all, an Atom, though it is one of the dual-core models.  It's not as fast as my Q6600 desktop or my daughter's new i5 HP laptop, but for tasks like browsing, mail, videos, and the like it's excellent.  I don't use Eclipse so I can't comment on that.  I do all my coding in text-mode. which the ASUS handles well of course.

---

### Post by aphirst on 2011-08-09
Just to throw in my two cents:

As an owner of an ASUS 1215n, and with friends on Arch using new laptops using Optimus NG-ION chipsets, we've discovered a project called [bumblebee](https://github.com/MrMEEE/bumblebee), which allows you to run individual applications with its own **optirun** command, which enables the NG-ION hardware for that application. Nothing automatic *yet*, but still promising.

I think there's an Ubuntu PPA.

---

### Post by rodrigo.toste.gomes on 2011-08-18
Thanks for your help.
I ended up deciding to stay away from optimus and AMD cards and bought a Sandy Bridge laptop.
I bought the ASUS AS1830T-6651.
It has an excellent price for the performance you get.
It can easily handle 720p video, even in flash! (this surprised me, but it's the first time I use the flashplayer 11 beta, it may be because of that).
With ubuntu 11.04, almost everything works out of the box, but it required a lot of work before it worked well.
The wireless had some problems with network-manager, but I only had to blacklist acer-wmi, and solved it.
The battery lasts around 6h with moderate use, but I have to manually set the screen to minimum brightness (which is still quite bright).
The biggest problem is with the touchpad, since it is an ALPS touchpad, which means I can't even scroll with it (tried to apply some of the solutions around the web - to patch the alps.c file and use imps on the options of psmouse, but nothing worked).
Other than these issues, everything seems to be working properly so far. Now I'll see if I can configure the system to be more energy-efficient.

---

