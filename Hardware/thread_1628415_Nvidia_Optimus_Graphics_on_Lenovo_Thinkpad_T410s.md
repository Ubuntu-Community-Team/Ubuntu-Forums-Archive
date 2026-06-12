---
title: "Nvidia Optimus Graphics on Lenovo Thinkpad T410s"
date: 2010-11-22
forum: Hardware
---

### Post by fhsm on 2010-11-22
**Background** (with a lot of links & then three questions)
The [Lenovo Thinkpad T410s]("http://shop.lenovo.com/SEUILibrary/controller/e/web/LenovoPortal/en_US/catalog.workflow:category.details?current-catalog-id=12F0696583E04D86B9B79B0FEC01C087&current-category-id=996BA0BF589A40D489F5FC222AA15BDE") looks like a great laptop ([video review]("http://www.youtube.com/watch?v=F2_ECbal8hA"), [review]("http://www.anandtech.com/show/2976/lenovo-thinkpad-t410-built-for-business"), [review]("http://laptops-reviewed.com/2010/02/04/lenovo-thinkpad-t410s-review/"), [review]("http://www.thinkpadtoday.com/thinkpad-t410-and-t410s-launch-review-why-we-love-the-thinkpad-t410-and-t410s-and-why-you-should-buy-one.htm"), [review]("http://blogntech.com/new-lenovo-thinkpad-410s-t410-and-t510-laptops-announced.html"), [review]("http://www.pcmag.com/article2/0,2817,2367983,00.asp"), [specs(pdf)]("http://www.lenovo.com/pdf/us/en/ThinkPad_T410s.pdf")). I'd like to buy one to replace my aging Thinkpad. 

I started reading around about the T410s' Linux comparability and found references to the usual out of the box foibles - [finger-print reader]("http://cpbl.wordpress.com/2010/10/29/lenovo-thinkpad-t410s-and-ubuntu-10-10/"), [multi-touch]("http://ubuntuforums.org/showthread.php?t=1507907&highlight=t410s"), etc - while others reported [perfect performance]("http://blog.zawodny.com/2010/10/17/ubuntu-10-10-on-the-lenovo-thinkpad-t410s/") consistent with [Lenovo's certification of the T410s as compatible]("http://www-307.ibm.com/pc/support/site.wss/document.do?sitestyle=lenovo&lndocid=MIGR-48NT8D").

On further reading I found that the T410s comes with switchable [Nvidia Optimus]("http://www.nvidia.com/object/optimus_technology.html") NVS [3100M 512mb graphics]("http://www.nvidia.com/object/nvs_techspecs.html")([video demo]("http://www.youtube.com/watch?v=F2_ECbal8hA")). I found this concerning but was reassured to find that [this is the graphics setup]("http://developer.novell.com/yes/133030.htm") in the T410s ([2912-30X]("http://www-307.ibm.com/pc/support/site.wss/document.do?lndocid=MIGR-48NT8D&sitestyle=lenovo")) certified by Lenovo as Linux comparable. Unfortunately I've read a number of reports ([1]("http://ubuntuforums.org/showthread.php?t=1589109&highlight=t410s"), [2]("http://ubuntuforums.org/showthread.php?t=1586292&highlight=t410s"), [3]("http://ubuntuforums.org/showthread.php?t=1598531&highlight=t410s"), [4]("http://ubuntuforums.org/showthread.php?t=1586292&highlight=t410s")) of people having trouble with this chip set and the latest Ubuntu releases. There even seems to be a [new project for support of Optimus laptops]("https://launchpad.net/~hybrid-graphics-linux").

So far *thehero* seems to have the best fix ([here]("http://ubuntuforums.org/showpost.php?p=10064748&postcount=6"), [here]("http://ubuntuforums.org/showpost.php?p=10064710&postcount=7")): 
> **thehero said:**
> I just posted this in another thread ([http://ubuntuforums.org/showthread.php?t=1586292&highlight=t410s](http://ubuntuforums.org/showthread.php?t=1586292&highlight=t410s)) but I'll say it again for Lenovo Thinkpad T410s owners with Optimus technology that are having problems. 

If you have Nvidia Optimus and have installed the nvidia driver you don't need to reinstall to fix X.

If you want to use the Nvidia propretary driver go into your bios with supervisor/administrator level access. From here you can choose Optimus/Integrated/Discrete graphics. Choose discrete graphics to use the Nvidia card.

If you want to use the Intel integrated card to save batter life choose integrated.

Note: that if you installed the Nvidia proprietary driver the Intel driver will not load correctly and your screen will freeze before login.

To fix this boot into recovery mode from grub and start failsafe-X. Once X is started go to additional drivers under system > administration and uninstall the nvidia binary driver. You may have to remove the xorg.conf file as well. Move the file by typing "sudo mv /etc/X11/xorg.conf /etc/X11/xorg.conf.old". This will not delete the file but instead move it in case you want it later.

Now reboot and the Intel driver should be working again.

Hopefully I haven't missed any of the relevant background on the topic. 


**Questions**

Given that switching isn't really a possibility under Linux I'm wondering if:

1) Anyone can provide a review of graphics performance running on just the integrated Intel chipset? 

2) Anyone can comment on how hot the system runs and what the impact on battery life is running on just the Nvidia chip.

3) Anyone can suggest a way to make switching (accepting a reboot and a trip to the bios) between the two chips a smoother experience under Linux (perhaps custom per chipset options in the Grub menu or a way to auto detect the chipset and use the correct configurations at boot)?

---

### Post by mustang on 2010-11-23
Great questions. I'm in the same boat. Thank you for making this thread.

---

### Post by fhsm on 2010-11-29
I've found some additional information on the topic: 

[LIST]
[*][A forum post describing an approach to easier switching (Arch)]("http://forums.thinkpads.com/~thinkpad/forum/viewtopic.php?f=9&t=88340").
[*][Another forum post (Gentoo).]("http://forums.gentoo.org/viewtopic-p-6392405.html?sid=3aa6992b33ba45578a93e4d9a2b82087")

[*][A blog on linux support for switchable graphics.]("http://linux-hybrid-graphics.blogspot.com/") 

[*][Another thread with more active conversation about these issues.]("http://forum.notebookreview.com/lenovo-ibm/454357-t410-linux-4.html")
[/LIST]

I'd still be interested in answers to any of the three questions in the OP.

---

### Post by sethwoodworth on 2010-12-02
Crap... I ordered the T410s today under the impression that this was working a tad better than this, with at least scripted switching working in OS.  *sigh*

Well I guess I should help make it work then, huh?

---

### Post by fhsm on 2010-12-02
The Gentoo and Arch threads I linked to above are the best info I've seen on the topic. It'd be great if you could post your experence once it shows up.

---

### Post by dvfedele on 2010-12-03
I've seen some other laptops/netbooks that have had luck with switching graphics...

for instance asus 1215n with nvidia optimus ion2

[https://lists.launchpad.net/hybrid-graphics-linux/msg00254.html](https://lists.launchpad.net/hybrid-graphics-linux/msg00254.html)

what about this from ubunut? 

[https://help.ubuntu.com/community/HybridGraphics](https://help.ubuntu.com/community/HybridGraphics)

or this?

[http://asusm51ta-with-linux.blogspot.com/](http://asusm51ta-with-linux.blogspot.com/)

I too am considering a thinkpad t and hope these solutions work too!

---

### Post by fhsm on 2010-12-03
I think these are all switcheroo based and thus ATI specific. Hopefully I'm wrong?

---

### Post by durus on 2010-12-10
I just ordered a T410s and would be interested in a solution with two different grub entries for the two different graphic cards. Have anyone tried that?
A cool feature would as you mentioned be if grub somehow could read the BIOS setting and present which setting currently is used so that it would be easier to pick the right entry or to let grub auto select the right one.

I found that it is possible to do some scripting with grub at [http://grub.enbug.org/LUASupport](http://grub.enbug.org/LUASupport) . I will spend some time on this when I get my laptop to see if it is possible to read the BIOS settings or not. If it is this would be an easy solution to at least pick the right graphic settings based on the bios setting

---

### Post by fhsm on 2010-12-11
durus as I said to sethwoodworth a report on your experience would be much appreciated. 

For now I'd say the [Arch ]("http://forums.thinkpads.com/~thinkpad/forum/viewtopic.php?f=9&t=88340")& [Gentoo ]("http://forums.gentoo.org/viewtopic-p-6392405.html?sid=3aa6992b33ba45578a93e4d9a2b82087")solutions are the most promising options I've found. If you have any luck with either please post about it.

---

### Post by durus on 2011-02-07
I decided to go with Windows 7 instead of having a semi working computer. One interesting thing is that it seems like T410 at certified for Ubuntu, whatever that means since things doesn't work as they should. [http://www.ubuntu.com/certification/hardware/200912-4905](http://www.ubuntu.com/certification/hardware/200912-4905)

---

### Post by anshuiitk on 2011-03-29
fhsm,

This was a great help. nvidia works like a charm now.

---

### Post by fhsm on 2011-06-16
@anshuiitk what did you do to get it working?

Hopefully not [https://github.com/MrMEEE/bumblebee/commit/a047be85247755cdbe0acce6](https://github.com/MrMEEE/bumblebee/commit/a047be85247755cdbe0acce6)

---

