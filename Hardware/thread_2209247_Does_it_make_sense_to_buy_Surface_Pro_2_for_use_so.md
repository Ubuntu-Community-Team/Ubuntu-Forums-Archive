---
title: "Does it make sense to buy Surface Pro 2 for use solely with Ubuntu?"
date: 2014-03-04
forum: Hardware
---

### Post by Nickolai_Leschov on 2014-03-04
I'm considering buying [Microsoft Surface Pro 2]("http://www.microsoftstore.com/store/msusa/pdp/en_US/Surface-Pro-2/productID.286866600?WT.mc_id=surface_RTM_surfacepro2") (8GB RAM, 256GB SSD) for use solely with Ubuntu. Do you think it makes sense?

Surface Pro 2 users, please share your use cases and experiences with Ubuntu. (SP1 users are welcome too, though I think SP2 might have its own problems due to newer hardware)

I've read that models with 64 or 128 GB SSD have 4 GB RAM, while the ones with 256 or 512 GB SSD have 8 GB RAM. That's why I'm choosing 256 GB SSD: to get 8 GB RAM. I have 8 on my current Ubuntu laptop, and I don't want any less. However, I see some sellers on eBay advertise Surface Pro 2's as having 4GB and 256GB, which should not be available, according to my information. Are they mistaken or there is or was a model with 4GB and 256GB?

I've settled on using Type Cover 2 with the device, and I'm eyeing a [docking station]("http://www.microsoftstore.com/store/msusa/en_US/pdp/Docking-Station/productID.286866900"). What other accessories do you recommend (I see Microsoft has got [many]("http://www.microsoftstore.com/store/msusa/en_US/list/Accessories/parentCategoryID.66734700/categoryID.63338500?Icid=SurfaceCat_StickyNav_4_Accessories_11.10.13") of them, [like]("http://www.microsoftstore.com/store/msusa/en_US/pdp/Wedge-Touch-Mouse-Surface-Edition/productID.264828000") [mice]("http://www.microsoftstore.com/store/msusa/en_US/pdp/Arc-Touch-Mouse-Surface-Edition/productID.286866800"), sleeves or some supposedly superior styluses)

I'm using [ThinkPad X200]("http://en.wikipedia.org/wiki/ThinkPad_X_Series#X200") with a docking station as my main computer now. I've upgraded it with Intel 520 SSD and 8 GB RAM (that's max, good thing this platform got DDR3) At work I use it with keyboard, mouse and monitor connected through a docking station. I've long mulled over the idea to try a laptop with a touch interface, so I thought of using something like [X series Tablet]("http://shop.lenovo.com/us/en/laptops/thinkpad/x-series/x230t/"), ThinkPad Yoga or one of the similar Lenovo's touch screen offerings, but I always wanted my portable computer to become *more* portable over the years, and this is not the case: newer machines offer about the same, if not slightly larger, size and weight as ThinkPad X60s from 2005. Now, Surface Pro 2 looks like a true upgrade to me: I can get a much more portable computer that is solidly built and should have a decent battery life, I can use it both as my main computer and take with me, and it got touch screen to boot. I'm aware that Type Cover may not offer all the *lap top* typing convenience of a true *laptop,* but I'm willing to see if I can be ok with that.

Now, I understand that Canonical is focused on accommodating this class of devices (that's what they ditched perfectly fine Gnome 2 for, right?) but may be not quite working "out of the box" on them right now. How well can I expect Surface's hardware to be supported and how good of an overall user experience I can expect with 13.10? What can I expect hardware support and UI-wise from 14.04?

And a last little question: should I be able to use 32-bit Ubuntu? I'm using 32-bit on my 64-bit laptop CPU and I don't see a reason to switch.

---

### Post by goepfling on 2014-03-07
I have a Surface Pro 2 with 8Gb/256Gb. Great hardware, poor Linux support (I bet this is not a coincidence). You'd better look for a non-Microsoft product.

Yes, I've got one and have been using Ubuntu 13.10 for three months.
No, Microsoft Store never listed a 4Gb/256Gb unit.
Yes, its Microsoft docking station is pricey like Apple add-ons.
And yes, when you buy a Surface you are also paying for a Microsoft Windows license and one year of skype/skydrive/etc services.

To date, **Surface Pro 2 is not yet Linux friendly.** Most of (currently unresolved) issues are described in [another thread]("http://ubuntuforums.org/showthread.php?t=2183946").
Quick list of main issues:

[LIST]
[*]hardware issues: wifi and bluetooth do not work (driver and firmware somewhat broken), USB 3.0 support absent, touch covers and microSD slot do not work, etc
[*]a modified kernel (look the above thread for PointSource's recent posts) disables the USB 3.0 support (not 2.0/1.1 support) and adds touchcover/wifi/bluetooth support, but wifi/bt still crashes the kernel after some hours (sometime after minutes); I bet the patch won't enter the 14.04 LTS kernels, maybe we'll have to wait 14.10
[*]software issues: missing pen/touch integration (Ubuntu does not disable touch when you use the pen: this is very annoying), problems with suspend/resume and screen blanking, lots of small glitches (defaults to max display brightness at every reboot, etc, sometimes it requires "Enter" to be pressed at boot because the grub does not wait, etc: long story short: **lots of non-critical but annoying issues**)
[/LIST]

I use it "docked" most of the time, with an USB 2.0 hub with USB-to-ethernet adapter, USB keyboard, USB mouse, and a displayport full-hd monitor. When I get a call, I reboot to Windows and go.

You seem to ask for a powerful 10" notebook, not a 10" tablet. I think you need a good notebook, not a pricey Surface.
If you only work "docked home and docked office", you may want to consider a small form-factor computer, like the Intel D54250WYK with 16Gb RAM (I don't know its Ubuntu compatibility).

---

### Post by Nickolai_Leschov on 2014-03-08
Thank you very much for sharing your experience, **goepfling**!
> You seem to ask for a powerful 10" notebook, not a 10" tablet. I think you need a good notebook, not a pricey Surface.I already have a notebook that suits me well. I would love to have what Microsoft seems to be offering: a much more portable notebook that is also a pressure-sensitive tablet, that runs Linux decently. (I believe at this point in time this means x86) Or a tablet that can turn int a decent laptop with the addition of keyboard, if you will. I don't mind sacrificing power for battery life, but Surface Pro 2 seemed to have the best of both worlds. I know that 10.6" feels too small and Type Cover (2) does not quite equal a laptop's keyboard, but I thought it might be good enough and I was willing to try. I definitely want to be able to work not just "docked home and docked office", but on the go, too. And I hoped to use touch and pen input, USB3, Bluetooth - practically everything.

When I read about Microsoft's offering, I thought this might be just what I wanted, so I didn't mind paying a premium price tag for Microsoft's product. Sad to see that this is far from truth. Maybe 14.04 will fix the issue enough for Surface Pro 2 to become usable? I guess, with the release of Final Beta postponed until March, 27 it is too early to know.

> You'd better look for a non-Microsoft product.1. Do you know of a similar tablet/laptop with better Linux support? I don't know any.
2. How should I go about contacting Ubuntu/Linux developers if I decide to buy a Surface 2 and help debug Ubuntu on it?
3. I wonder if Ubuntu runs any better on first-gen Surface?

---

### Post by sblake on 2014-03-09
Surface Pro 2 users, who just recently got Ubuntu to work relatively well. Following the thread "[[COLOR=#dd4814]Will Ubuntu work on the Surface Pro 2 like it did on the original?[/COLOR]]("http://ubuntuforums.org/showthread.php?t=2183946&page=7")" and downloading and installing the latest kernel patches gets the touch cover working, trackpad, and WiFi (I had to download additionally the drivers following the instructions from PointSource's instructions at the bottom of page 6 to get the WiFi working at all, though).

I'm still having WiFi issues with the built in card. I can connect to networks for only about 5 minutes before it kicks me off, and then refuses to connect to anything (although I can still see and scan for them). So it's working, but not connecting. I instead carry around a USB wireless adapter.

To my knowledge, this is the only downfall ATM to using it productively with Ubuntu. 

I would certainly question buying the Pro 2 just for Ubuntu though. While I got it working, it still doesn't feel entirely stable (mainly I suppose because of the WiFi). You'll get much more for your money if you're only after a dedicated Ubuntu machine. 

I've got mine booting straight into ReFind, which then boots either into Windows 8 or Ubuntu. I find that setup works for me, as I need Ubuntu for coding, and I like Windows 8 because the user experience is just simply nice on a touch screen tablet (and I also find it easier to use at my work for network admin stuff).

I guess at the end of the day, given what you're after, I'd suggest against it. 

If, however, you want a tablet with Windows 8 and that can be dual booted to run Ubuntu well, then I'd say go for it. Hopefully the WiFi will be fixed (and I assume it will be, since a heap of these fixes to get it working in the first place have only come out in the recent weeks, so people are still working on it).

Touch screen works well. I've done some modifications to make things bigger though. A full 1080p resolution on 11 inches doesn't go too well with small icons :)

My two cents, for what it's worth :)

---

### Post by Nickolai_Leschov on 2014-03-10
Thank you very much for sharing your experience!
1. If the only thing that you couldn't make to work in Ubuntu is WiFi, and hopefully it will be fixed soon, why would you suggest against using? What kind of instability did you experience?
> I've got mine booting straight into ReFind, which then boots either into Windows 8 or Ubuntu.
2. Do you mean you *must* use ReFind instead of GRUB on Surface Pro, because it's a EFI system? Is GRUB unusable?
3. How do you go about installing ReFind - I believe, Ubuntu installer only installs GRUB? Probably you don't install any boot manager during installation and boot into Ubuntu until you install ReFind later?
4. How are you able to select an OS in ReFind: does touch input work? If keyboard works there, that would be an achievement, too: [here]("http://www.theregister.co.uk/2013/06/07/review_acer_aspire_p3_windows_8_tablet/") they were not able to install Ubuntu on Acer Aspire P3, because Bluetooth keyboard doesn't function at boot time.

5. **goepfling**, care to share how can I get better value for the money if I need a highly portable device like Surface Pro to use with Ubuntu? I'm not aware of any alternatives. Something like ThinkPad X220t/X230t/Yoga should be supported by Ubuntu, but it is not *that* portable.

---

### Post by dsm iv tr on 2014-03-11
Is there anyone working on rolling out a package set for the Surface Pro 2 hardware? If there isn't, I'd like to throw that idea out there. I'm thinking a package set could include automated kernel/fw fixes (avoiding install errors, could be done via a simple dpkg command + some minor scripting) touch-related tweaks, SSD-related tweaks, and, perhaps more frivolously, SP2-friendly utilities/artwork/iconsets/pointer sets for usability. I'm willing to lend a hand in almost anything, from coding to packaging to documentation. 

Gathering the various ideas and fixes might be a great idea, because it could show that there is enough interest/organization to get 14.04/14.10 to support the tablet OOTB.

---

### Post by javispedro2 on 2014-03-12
With a relatively recent Gentoo virtually everything works out of the box (only had to drop the updated Avastar firmware in /lib/firmware), so I suspect that in one or two Ubuntu releases most will also work OoTB.

Except the UI, of course. HiDPI is still horrible.

---

### Post by Nickolai_Leschov on 2014-03-13
> **javispedro2 said:**
> With a relatively recent Gentoo virtually everything works out of the box (only had to drop the updated Avastar firmware in /lib/firmware), so I suspect that in one or two Ubuntu releases most will also work OoTB.
I hope that things become better in 14.04 already, or at least there'll be less to tweaks needed.

> **javispedro2 said:**
> Except the UI, of course. HiDPI is still horrible.In Gentoo? Do you know of a Linux distribution or software that has better support for high-resolution screens? Again, maybe 14.04 and/or the new Mir will bring improvements?

---

### Post by Nickolai_Leschov on 2014-03-13
> **dsm iv tr said:**
> Is there anyone working on rolling out a package set for the Surface Pro 2 hardware? If there isn't, I'd like to throw that idea out there. I'm thinking a package set could include automated kernel/fw fixes (avoiding install errors, could be done via a simple dpkg command + some minor scripting) touch-related tweaks, SSD-related tweaks, and, perhaps more frivolously, SP2-friendly utilities/artwork/iconsets/pointer sets for usability. I'm willing to lend a hand in almost anything, from coding to packaging to documentation. 

Gathering the various ideas and fixes might be a great idea, because it could show that there is enough interest/organization to get 14.04/14.10 to support the tablet OOTB.
If noone else will do it, I'm going to start a new thread for that, when I'll get my Surface, based on 14.04. Hopefully, it will bring some improvements into base system.

---

### Post by javispedro2 on 2014-03-14
> **Nickolai_Leschov said:**
> In Gentoo? Do you know of a Linux distribution or software that has better support for high-resolution screens? Again, maybe 14.04 and/or the new Mir will bring improvements?
In Gentoo, albeit this is a desktop environment problem, not a distribution problem. The only DE I know that has shown some work on HIDPI is Gnome3, and it's hard to enable in current versions.

Typing from the touchcover1 on mine. Firefox actually works nicely on HiDPI.

---

### Post by monkeybrain20122 on 2014-03-14
It makes no sense whatsoever for two reasons
1) You won't be able to put Ubuntu or anything else other than Windows on it because these machines are completely locked down ('secure boot', except on the ARM machines it can't be disabled)
2) the money goes to MicroSoft.

---

### Post by javispedro2 on 2014-03-15
> **monkeybrain20122 said:**
> It makes no sense whatsoever for two reasons
1) You won't be able to put Ubuntu or anything else other than Windows on it because these machines are completely locked down ('secure boot', except on the ARM machines it can't be disabled).You got it wrong. It is completely locked only on ARM machines, and the Surface Pro 2 is, precisely, not an ARM machine. 
The SFPro is even less locked down than some Chromebooks (where you will never be able to remove the annoying developer mode warning+delay). 
As said, replying from my SFPro2 using Gentoo.

---

### Post by goepfling on 2014-03-31
You may want to check a 1800+ bucks beast like this one reviewed on Phoronix with Ubuntu 14.04:

 [http://www.phoronix.com/scan.php?page=article&item=asus_zenbook_ux301la&num=1](http://www.phoronix.com/scan.php?page=article&item=asus_zenbook_ux301la&num=1)

Fairly nice machine (core i7 with 8Gb, two SSD, and 2560x1440), but  battery and temperature captured my eye. It reports temperatures around  80-90°C even in non-stressing situations, and 3 to 4 hours battery life  before "extensive tweaking".

I've been running Ubuntu 13.10 on my Surface Pro 2 with the "indicator  applet" always running. In day-to-day usage, I rarely see all cores  working up to 100%, even when stressing it. Its small cooling fans are  almost always off; when I convert some video footage (requiring full  parallel cpu power), I finally hear a small noise coming from the two  fans, and the case is... just a bit warm (I guess on the 30-35°C side).

In Ubuntu I was able to watch two consecutive movies (with display  brightness on about 70%) and yet see 44% battery left (and secretly  laughing about people in the same express train grumbling about their  batteries). Yes, having lots of raw power is nice, but has its  drawbacks.

I think I involuntarily caught the sweet spot - using the Surface Pro 2  as a "desktop" machine (USB hub + ethernet + external keyboard/mouse/display), and almost always Windows when on the go.

---

