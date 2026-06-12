---
title: "NVIDIA GeForce GT 540M"
date: 2011-03-04
forum: Hardware
---

### Post by charleetm on 2011-03-04
Guys, I have just ordered my dell XPS15 with this card in it. I have to run ubuntu for work reasons.. Tried all day to see if this card have the drivers for ubuntu. Any ideas? Really hope there is a way round this so I can keep the laptop :(

Anyone running a ubuntu laptop using this chip?

Thanks a million!
Charlie

---

### Post by C-raz on 2011-03-28
Hi,

I am running Dell XPS 15 using this chip. Seems to be working fine as long as I do not install the graphics card I am trying to find a way to install as well. Managed to get wireless working too but I updated the kernel. However, I am a noob  and I love the way Ubuntu is working on the laptop. I am trying to search for drivers direct from Nvidia heard that might help and I manged to play movies and all on the laptop only problem is I can't enable visual effects. I think you should be fine with this laptop.

---

### Post by rne1223 on 2011-03-29
I made the mistake of installing the "recommended driver" and now I get a black login screen that keeps telling me that my password is wrong. I have a couple of questions:

1. How do you restore the default driver?
2. Why is the current "recommended driver" giving me this issue?

Any help would be greatly appreciate it. Thanks

---

### Post by C-raz on 2011-03-29
Hi There,

It seems that there seems to always be a problem when you write the config file into the system. I managed to install the driver in but I still can't change the visual effects because when I went to on to do an nvidia-xconfig as root I will face the black screen checking battery state then it will give me a login prompt.

Meanwhile here is what I did to help me resolve the issue but still I am trying to figure a way out to get a correct way to populate xorg.con

When I see the black screen. I keyed in my username first. Hit enter then keyed in my password.
Now I will see my directory. I then typed the following
**sudo -i**
this helps me to be root, next I did
**mv /etc/X11/xorg.conf /etc/X11/xorg.bak**
Commands are case sensitive, you probably already knew, this should help you to rename the original xorg.conf and help you login normally again without a config file

I installed the driver following these steps and its activated
***[http://www.webupd8.org/2010/06/how-to-install-nvidia-25635-display.html](http://www.webupd8.org/2010/06/how-to-install-nvidia-25635-display.html)***
but left the nvidia-xconfig part in the end when I am actually supposed to do as it gives me problems. I can watch movies and all but can't do visual effects. I  will update here if I find out I hope anyone that reads this thread  does too


Furthermore, to get my wireless working on the dell XPS 15 i7, I updated my kernel to 2.6.38.2-candela
following these steps first. 
***[http://www.ramoonus.nl/2010/10/linux-kernel-2-6-36-installation-guide-ubuntu-linux/](http://www.ramoonus.nl/2010/10/linux-kernel-2-6-36-installation-guide-ubuntu-linux/)*** 
Then downloaded the lumen kernelchecker and did and upgrade hoping to get a working xorg.conf file
just in case you ran into this issue as well and don't mine upgrading. 

I hope this helps, pardon me if I make any mistakes as I only started  using Ubuntu for 2 days but I still love it despite no visual effects and this resolution works for me. . :smile:

---

### Post by QuimNuss on 2011-04-04
Damn, I have the same card. Is there any chance it'll work at least to increase the resolution? I'm running 1024x768 but you can see some blur as it's not enough.

---

### Post by beew on 2011-04-04
The card should be ok as long as it works alone. But OP is screwed because his laptop (DELL XPS15)is Optimus enabled. With Optimus the Nvidia card becomes a kind of hybrid with a cheap onbroad Intel card so the Linux driver for the Nvidia card no longer works. As for Nvidia, not only does it not support Optimus in Linux, it doesn't give Linux users the option to NOT use it. With Optimius enabled, you simply cannot use the Nvidia card you pay for, period (unless your laptop has a BIOS switch to turn off Optimus and choose the discrete card,--Nviida) But even worse, the unusable Nvidia card would still be sitting there eating your battery so it is worse than an expensive paper weight.

This is serious as more (most) new laptops with Nvidia have Optimus enabled, so Nvidia effectively no longer supports Linux laptops even though the chips are still "compatible" (unless you get something really expensive like a Thinkpad which has the said BIOS switch, or a performance system76 laptop which costs as much as a Mac book pro) Unfortunately Linux still can only count on Nvidia for the most reliable graphic performance (Intel is not meant for performance, ATI on Linux is still like playing roulette, it may or may not work depending on luck)  So if this is not resolved it would mean "Linux = crappy graphics on laptops" for a long time to come.

Check out this thread and write to Nvidia. And write to Dell too to request for the BIOS switch.
[http://ubuntuforums.org/showthread.php?t=1712278](http://ubuntuforums.org/showthread.php?t=1712278)

---

### Post by QuimNuss on 2011-04-04
According to the manual, I do have Optimus on as well. I'm not sure I'm getting it; there are two working modes, either using the intel card alone or both at the same time. Is that so? 

I'll check the bios, but I don't think I have that option either. Still, turning it off won't just disable the nvidia card? So in both cases the card is unusable.

Anyway, you seem to say that is somehow possible to use only the nvidia card, but there's no driver for it, ain't it? 

I'd like to increase the resolution, I can be happy ever after without HD movies =)

---

### Post by QuimNuss on 2011-04-04
Nope, no option present in the bios. Moreover, it seems there's no support either for XP, only Windows 7. I'm amazed by nvidia.

---

### Post by beew on 2011-04-04
> **QuimNuss said:**
> According to the manual, I do have Optimus on as well. I'm not sure I'm getting it; there are two working modes, either using the intel card alone or both at the same time. Is that so? 

I'll check the bios, but I don't think I have that option either. Still, turning it off won't just disable the nvidia card? So in both cases the card is unusable.

Anyway, you seem to say that is somehow possible to use only the nvidia card, but there's no driver for it, ain't it? 

I'd like to increase the resolution, I can be happy ever after without HD movies =)

If your machine is not Optimus enabled then the Nvidia card would work with the proprietary driver they provide (or Nouveau for that matter even though performance is crappy) 

But in an Optimus enabled machine the driver would no longer work because the chip has become a hybrid essentially. The only way to use the Nvidia card  would be through a switch in the BIOS but AFAIK the only optimus enabled laptops that have such a switch are the Thinkpads and perhaps some ASUS laptops (not sure about the latter)

If you are unlucky enough to have bought a laptop with Optimus and cannot return it the best thing you can do out of all horrible options would be to find a way to disable the Nvidia card and use the Intel card only. That way the expensive Nvidia card becomes just a paper weight but it doesn't eat your battery. There are several tutorials on the Ubuntu forum for doing just that, but you have to search for them.

There may also be more info in the thread I linked to above.

---

### Post by QuimNuss on 2011-04-04
So, it would not work at all and the fact that I get a crappy resolution with no dual-head or anything means that the nvidia is actually disabled, but the intel usable. Is that right?

Does somebody know any way to use the nvidia instead of the intel integrated card? (dreaming of a solution...)

---

### Post by beew on 2011-04-04
> **QuimNuss said:**
> So, it would not work at all and the fact that I get a crappy resolution with no dual-head or anything means that the nvidia is actually disabled, but the intel usable. Is that right?

Does somebody know any way to use the nvidia instead of the intel integrated card? (dreaming of a solution...)

That's right. But the Nvidia card is not disabled even though it is unusable, it is still draining your battery and heating up the machine. Those tutorials I mentioned was about disabling the Nvidia card so it won't eat your resources but you would end up still using the crappy Intel card. 

Also, you would need to uninstall the nvidia driver in order for the Intel card to work properly.

Here is a link to one of those tutorials

[http://ubuntuforums.org/showthread.php?t=1657660](http://ubuntuforums.org/showthread.php?t=1657660)



I don't believe anyone has figured out a way to use the Nvidia card in Linux for an Optimus enabled laptop, that's what people are asking Nvidia to provide.

---

### Post by QuimNuss on 2011-04-04
Indeed that worked. One of the leds is now indicating that it is using the integrated card as much as it can, the fan speed has decreased a lot and so does the heating and noise. I'm pretty sure the battery would last longer as well.

what worked for me is pointed out by user 3602 and it's pretty straight forward. Download some code from a git repo, build and execute.

Still, I hope I can return it since it's a shame I've paid for an unusable card. What's more surprising is that there's no support for it on Windows XP either, only Windows 7, unbelievable.

Crap.

---

### Post by beew on 2011-04-04
> **QuimNuss said:**
> Indeed that worked. One of the leds is now indicating that it is using the integrated card as much as it can, the fan speed has decreased a lot and so does the heating and noise. I'm pretty sure the battery would last longer as well.

what worked for me is pointed out by user 3602 and it's pretty straight forward. Download some code from a git repo, build and execute.

Still, I hope I can return it since it's a shame I've paid for an unusable card. What's more surprising is that there's no support for it on Windows XP either, only Windows 7, unbelievable.

Crap.

AFAIK it doesn't support Vista either. If you can return the machine go for it. You can get a cheaper laptop if you end up only using the low performance Intel card. Turning the high performance Nvidia card that you paid for into a paperweight doesn't sound like an acceptable solution to me, unless you are truly stuck.

This guy got a SamSung laptop with a Nvidia chip and Optimus free, he sounds pretty happy.
[URL="http://ubuntuforums.org/showthread.php?t=1718637"]http://ubuntuforums.org/showthread.php?t=1718637
[/URL]

---

### Post by bbrtk on 2011-07-21
To turn on/turn off   nvidia use [http://www.omgubuntu.co.uk/2011/05/bumbleebee-brings-nvidia-optimus-gpu-switching-to-linux-users/](http://www.omgubuntu.co.uk/2011/05/bumbleebee-brings-nvidia-optimus-gpu-switching-to-linux-users/)
Hope that help

---

