---
title: "a new PC - Intel or AMD for Ubuntu compatibility?"
date: 2015-04-24
forum: Hardware
---

### Post by palmgrower on 2015-04-24
Does Ubuntu 15.04 support both AMD and Intel well? I need to replace an older desktop with an entry level PC. Either AMD Kaveri or Intel i3/i5. I am going to use the built-in graphics. Is nVidia the only graphics that I should avoid? Thanks.

---

### Post by sgian on 2015-04-25
Intel is better supported and for a longer time.

---

### Post by kc1di on 2015-04-25
Intel at this time.

 I would avoid AMD/ATI Video, Most Nvidia cards are supported but require some additional work to get them going, once going they work well. 
If you want to be sure everything is compatible buy from one of the vendors that specialize in pre loaded Ubuntu System 76 or Zareason there are others also. 
Good Luck in your search.

---

### Post by oldfred on 2015-04-25
Last fall I built new desktop with Intel i5 and used an older nVidia card. It has worked without issue with both 14.04 and 15.04. But required a huge number of UEFI/BIOS setting changes to get it to install in UEFI mode correctly up front.

I also just purchased a Dell [FONT=Trebuchet MS][SIZE=2][COLOR=#444444]Inspiron 3647 SFF - small form factor that was on sale for about $300 with Intel Haswell i3 processor. May be clearing out older inventory as Broadwell [/COLOR][/SIZE][/FONT]is newer processor now.
I followed our own directions on backups which ended up taking several days has I had to go to store to get another flash drive. I used a smaller flash drive, a larger flash drive and 5 DVDs to do Dell recovery, Windows recovery/repair and full Windows backup.

But after partitioning in advance, I was able to install 15.04 in about 10 minutes and it just worked. I may have made a few settings in UEFI, and did some settings in Windows to turn off fast startup.

---

### Post by Keith_Helms on 2015-04-25
As far as processors go, either Intel or AMD will be fully supported.  I'd just compare which gives the best "bang for the buck" performance within your budget.  

> Intel is better supported and for a longer time.

I'm not sure what was meant by this.   Linux fully supports processors from both manufacturers and Ubuntu has no "processor dependent" support period associated with either.

---

### Post by palmgrower on 2015-04-25
Thank you for the replies. Good to know both are supported. I just had a trouble with an older nVidia card. That's why I asked the question. Thanks again.

---

### Post by QIII on 2015-04-25
The old "ATI is no good" mantra just never seems to die, does it?  It doesn't seem to matter that it's not at all true.  But, it is what it is.

Just like the "NVIDIA is no good" meme.

---

### Post by sgian on 2015-04-26
I have 5 computers ranging in age from 2007 to 2015, both Intel and AMD.  It has been my experience as well as that of many others if you google the issue that intel is better supported for a longer time.  For example my 2007 Intel computer runs Ubuntu 15.04 fine while one of my 2010 AMD computers stopped working at Ubuntu 14.10 and now is stuck with Ubuntu 13.10 and Windows 7 which still work.  So while AMD based computers do have some support, as they age they will lose support sooner and require more tweaking to work.  If you just want to install the OS and keep it up to date without having to tweak it to work, then my experience is to go with Intel.  On the other hand if you don't mind messing with drivers and keeping old versions of Ubuntu after AMD support withers away, then AMD is fine.

---

### Post by kurt18947 on 2015-04-26
The only negative I'm aware of with AMD video is that they dropped support for quite a few older video chipsets a few years ago. A result of the AMD's purchase of ATI?  SWMBO's machine is AMD running Xubuntu 14.04. A6 APU on an Asrock board using native video and no issues at all. I'm writing this on a 2007 vintage AMD Athlon II X2 powered Gigabyte system with Nvidia video. Again, no issues. We're not gamers so aren't trying to wring the last bit of video performance out of our machines.

---

### Post by Keith_Helms on 2015-04-26
> **sgian said:**
> I have 5 computers ranging in age from 2007 to 2015, both Intel and AMD.  It has been my experience as well as that of many others if you google the issue that intel is better supported for a longer time.  For example my 2007 Intel computer runs Ubuntu 15.04 fine while one of my 2010 AMD computers stopped working at Ubuntu 14.10 and now is stuck with Ubuntu 13.10 and Windows 7 which still work.  So while AMD based computers do have some support, as they age they will lose support sooner and require more tweaking to work.  If you just want to install the OS and keep it up to date without having to tweak it to work, then my experience is to go with Intel.  On the other hand if you don't mind messing with drivers and keeping old versions of Ubuntu after AMD support withers away, then AMD is fine.

I also had a dual Athlon system which I built in 2003 and it ran for 9  years until the hardware died.  I currently have 2 desktops with AMD  quad-core processors that are about 3 years old and 2 laptops with Intel processors, all running  Xubuntu 14.04.  My experience has been that it sometimes takes a while  for newer hardware to be fully supported in Linux, but support for older  hardware rarely gets removed.  It was just a couple of years ago that  Linux dropped support for the 386 processor.  I usually have to fiddle  with drivers more on newer hardware, whether Intel or AMD, than on older  hardware.  For example, one of my Intel laptops has something called a  clickpad where the touchpad and the "mouse" buttons are combined on a  single plate.  When I first got it about 3 years ago, it wasn't well  supported.  With the latest releases it has become tolerable to use.  My  laptops also have what is called hybrid graphics or Nvidia Optimus.   The latest 14.04 LTS has gotten to the point where I can use either the  Intel or the Nvidia graphics, but not automatically switch between them under the covers as I could if using  Windows.

I don't want to start a flame war and I have no idea what is peculiar to your 2010 AMD system that prevents you from upgrading to 14.10 (processor? chipset? graphics?), which is not an LTS release and therefore is more "experimental".  My experience has been that as long as you have the minimum "horsepower" to run the latest release, anything that worked on the previous release should continue to work.

---

### Post by Mike_Walsh on 2015-04-26
> **QIII said:**
> The old "ATI is no good" mantra just never seems to die, does it?  It doesn't seem to matter that it's not at all true.  But, it is what it is.

Just like the "NVIDIA is no good" meme.

It's unbelievable, isn't it? I use the built-in ATI Radeon Xpress200 graphics chip in this elderly Compaq desktop of mine. It's over 10-yrs old, and STILL going strong.....


Regards,

Mike. :)

---

### Post by Mike_Walsh on 2015-04-26
> **sgian said:**
> I have 5 computers ranging in age from 2007 to 2015, both Intel and AMD.  It has been my experience as well as that of many others if you google the issue that intel is better supported for a longer time.  For example my 2007 Intel computer runs Ubuntu 15.04 fine while one of my 2010 AMD computers stopped working at Ubuntu 14.10 and now is stuck with Ubuntu 13.10 and Windows 7 which still work.  So while AMD based computers do have some support, as they age they will lose support sooner and require more tweaking to work.  If you just want to install the OS and keep it up to date without having to tweak it to work, then my experience is to go with Intel.  On the other hand if you don't mind messing with drivers and keeping old versions of Ubuntu after AMD support withers away, then AMD is fine.

Can't agree with this. My old Compaq (from 2004/5) is AMD-based. It's never given me ANY problems at all. I've just upgraded the Athlon 64 single-core to an Athlon 64 X2 dual-core.....and it's working better than ever.

I also have a 13 yr-old, Intel-based Dell Inspiron 1100, from 2002.....which has been unable to run a single 'buntu-based distro until very recently, thanks to an 18-month old 'tip' I stumbled across by accident about a fortnight ago. The Intel 82845 'Extreme' graphics adapter it's fitted with is one of the worst things Intel ever produced; they threw the rulebook out of the window, and said 'Sod it' to VESA standards, when they produced these chips. I've come across scores of tales of woe from owners of the things..!

OK, so the 'fix' was actually pretty simple; just modifying a line in /etc/default/grub. But my point is, it **still had to be 'tweaked'** in order to make it work as it was intended to..! And the only reason I'm running 14.04.2 is because I like the stability of an LTS version.....and it's still got nearly four years of support. You'll not catch me installing the 'bleeding-edge' stuff every 6 months. Who needs it??

And I've not had to 'mess about' with one** single** driver for the old girl to 'just run' perfectly. Which to my way of thinking, says a **lot** about Canonical's developers; who deserve a big pat on the back.....and many thanks. 

Perhaps I've just got a 'good one'. Maybe you've just been unlucky enough to have 'bad ones'. Who can really know for sure? **I** think this is a case of YMMV.....


Regards,

Mike.

---

### Post by mattharris4 on 2015-04-27
I run Edubuntu on an Intel Pentium 4 (that computer is about eight years old now) and Lubuntu on a AMD E1-2100 processor and both work (that computer is about a year old).  That particular AMD processor is a bit slow and sticky whether running Linux or Windows but that is because it was designed to use minimal power and performance suffers greatly because of it.  I would recommend staying away from the AMD E1-2100 processor (maybe the whole E1 line) but the faster processors from them should work fine.  I have also heard bad things about the Atom and Celeron lines of processors from Intel (with the Atoms being worse) for the same reason but that does not apply to their other processors such as the i3, i5 or i7 which all have a good reputation.  

I recommend spending the extra $100 for a better processor or buying a refurbished computer if money is tight  and saving some cash that way (Tiger Direct and Newegg sell them) a desktop with 8GB of RAM and a mid-line processor is about $200 plus shipping.  If you go the refurb route make sure whatever computer you buy has a one-year warranty as a couple of refurbishers still insist on only guaranteeing their computers for 90 days which is not enough for a refurb where the chances of something going wrong are a bit higher than with a new computer.  Here is an example of a refurb in this category although at this time the refurbs with 8GB of RAM and the Intel Core 2 processor come with a DVD-ROM drive which you would likely need to replace with a DVD-RW drive which is about $30 and a bit of your time.  Computers with 4GB of RAM are available with varying specs, a good one is certainly less than $200, if you look carefully most of the time you can find one with a DVD-RW drive and a 500GB hard drive along with the mid-level processor (probably a Core 2 or AMD equivalent) for about $120 plus shipping (about $20 from Tiger Direct when I bought mine from them a few years ago) and will run Linux just fine -- as long as it comes with Win 7 and not Win 8/8.1 (most refurbs are HP and with their Win 8 computers they make it almost impossible for the average person to make Linux work properly, with Win 7 the computer should be old enough that it does not have the dreaded UEFI).

---

### Post by kurt18947 on 2015-04-27
MattHarris4 is gives good advice. I've purchased a couple off-lease Thinkpads and so far so good. I would recommend sticking with 'business-class' machines; they use better quality components that are likely to live longer and be better supported. If I have confidence in an older machine's peripherals - power supply is big enough and has modern outputs, hard drive/optical drive are adequate, I've done a 'brain transplant' and been happy with the result. Here is my most recent effort referenced earlier. Add memory as desired and I was in business.

[http://www.microcenter.com/site/products/amd_bundles.aspx](http://www.microcenter.com/site/products/amd_bundles.aspx)

[http://www.microcenter.com/single_product_results.phtml?product_id=0446578](http://www.microcenter.com/single_product_results.phtml?product_id=0446578)

[http://www.microcenter.com/single_product_results.phtml?product_id=0435028](http://www.microcenter.com/single_product_results.phtml?product_id=0435028)

$84.98 plus tax.

---

### Post by mattharris4 on 2015-04-27
Kurt, I can confirm that most off-lease refurbs (which most of Tiger's and Newegg's refurbs under $250 are) are business-class.  This is because home consumers generally do not lease computers anymore so consumer level computers don't get leased and therefore not returned after a lease expires.

---

### Post by Mike_Walsh on 2015-04-27
I tend to agree with Kurt. I think the sole reason why this old desktop of mine is still going strong is quite simple. Compaq haven't been an independent company for 10 yrs now (HP bought them out in 2004/5.....not sure exactly when), but in their day they built machines almost exclusively FOR the business market; people who don't want lots of messing about to set things up, and who want solid reliability. I understand that a couple of years after the buyout, HP either got hold of a bad batch of caps, or else began economising.....with the result being that for a while, the HP-Compaqs didn't have a very good rep. At the time this old girl was built, the motherboards were still old original Compaq stock, and they insisted on high-quality components for their PCs.

Whatever the reason, I haven't had a single problem with the hardware on her.....for which I've had good reason to be grateful. Apart from a partially faulty PCIe slot; but I don't need a graphics card for what I use her for.....and the 'top end' of the slot is in use by a USB 3.0 adapter card, which to me, is far more useful, since I regularly do a lot of back-and-forth file transfers. The added speed offered by USB 3.0 has made a huge difference.


Regards,

Mike. :)

---

