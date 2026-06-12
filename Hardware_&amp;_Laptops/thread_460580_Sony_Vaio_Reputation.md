---
title: "Sony Vaio Reputation"
date: 2007-05-31
forum: Hardware &amp; Laptops
---

### Post by tux_rox on 2007-05-31
What's the general consensus of Sony Vaio notebooks?

I was looking at Thinkpads, but those were a bit too boring for me.  The Vaios look good, and they are well equipped too.  I'm specifically looking at the C series if anybody cares... T7200 Core 2 Duo processor, 2 gigs RAM, 100+ gig hard drive, choose a fly color, free laser insription... doesn't get much better than that for 16 hundred bucks.

So anyway, how does Ubuntu generally work on these?

---

### Post by tgalati4 on 2007-05-31
I was looking at them at the Sony Styless store last week.  They seemed flimsy compared to my 2-year old aluminum powerbook.  The buttons were small and fiddly.  I just didn't like the overall feel.  The sound quality (built-in speakers) was OK, on par with the powerbook.  Of course Vista was giving me a headache.  All of the crapware barking at once--and Norton warning me about every mouse click.  What happened to Windows?  I haven't used it for a few years--it's as bad as FM radio.

Yes, Thinkpads are boring, but they are tough and are geared for business users.  Linux is well-supported on the the Thinkpad.  I'm not sure about how well supported on Vaio.  What does Vaio stand for anyway?

---

### Post by rabideau on 2007-06-01
Sony has some real problems running 7.04 Ubuntu (as well as with almost any Linux distro).  Keyboard Fn keys don't work... LCD out does not work... etc.

Generally you're better off with different HW.  I just ordered a Dell because fo $1200 I am able to get a guaranteed to work Ubuntu machine, without thousands of hours investment required on bending the machine to Linux.

---

### Post by kerry_s on 2007-06-01
to much proprietary crap.

---

### Post by lancest on 2007-06-01
Sony is made by ASUS. So I avoided Sony they are too proprietary and their quality is questionable. So I bought an ASUS W7J. It works pretty well with Linux. ACER,BENQ,ASUS (Taiwan) all work with Linux and are cheaper.

---

### Post by djorzgul on 2007-06-03
VAIO = Video Audio Input Output... in short nothing, although they claim that with docking station it really works well... I never tried
I have older model A317M and I must say it is good quality machine, I traveled a lot with it, on ships, bicycles, buses, even few times used it as a pillow in the bus :), and it still works and looks good... The only pain in the *** is dvd which is way tooo sensitive... just a little dirt/scratch and it won't read...  and "burn failed" fro dvds appears too often... 
Pretty much that was the only problem for almost two years... And battery life for mine 17'' model is way too short for anything then checking mail, and typing...
Ubuntu 7.04 works well with it pretty much out of the box...

But, next time I would definitely go with ibm/ati fireGL combo or Dell...

---

### Post by Depressed Man on 2007-06-03
Pretty happy with my VAIO on Windows Vista.. On Ubuntu it's slightly more troublesome. FN keys don't work (well that was fixed), built-in microphone doesn't work nor the microphone I plug in, built-in webcamera I had to fix (though it's still black and white and the image is cut down the middle), and hibernate/suspend doesn't work (which is important on a laptop!). Didn't have other troubles though besides those. My built-in card reader even works!

---

### Post by spier on 2007-06-03
Happy with my FS series. As a linux noob, everything was a chalenge to get working. Since breezy, every new release improved hardware support and now it works better than the original winXP I leave installed as my daughter still uses. 

Now, users who are uncomfortable tweaking linux installation files, there are some hardware suppliers that sell laptops with linux installed, like system76 and Dell (there is a dell support list in ubuntuforums!).

---

### Post by dougr on 2007-06-03
I just picked up a Thinkpad Z61, and yes, it is not flashy, but from my years in business, I know why most of the big companies issue thinkpad laptops to employees.  They rarely fail hardware wise, have AWESOME keyboards, and are built like tanks.
I could not believe how with my new thinkpad, everything worked out of the box with 7.04, right down to my wireless card with WPA...amazing coming from my last ATI nightmare laptop.

Yes, they are not flashy, in fact thinkpads may be considered downright ugly.  But to me, computing isn't about a fashion statement, it's about getting my work done.

Regarding the VAIO, I would avoid it.  Yes, they have attractive specs for the price, but if anything ever goes wrong with the laptop, it's a NIGHTMARE.  They have customer service on par with Averatec...which is to say, not very good.  Warranty's on thinkpads are awesome as well, and they will make sure you are satisfied.

If you don't want a thinkpad, but more like the styling of a VAIO, I would maybe lean toward a slimline Dell.

---

### Post by IntuitiveNipple on 2007-06-04
I was in the market recently to replace my two Sony Vaio SRX51P/B notebooks bought in 2002; both run Ubuntu Edgy perfectly. I posted in these forums how to build the WPA-enabled 2.6 kernel driver for the 802.11b WiFi (Hermes II orinoco_cs drivers) on them some time ago.

I was expecting a new Vaio to be a lot of trouble to sort out, but I have to say the build quality and reliability of the SRX51s was impressive - used daily, went everywhere with me, tossed about, used as hammers, etc., and behaved impeccably.

I wanted something to replace my desktop workstation so dual CPU, virtualisation, and plenty of storage and ooomph were key.

After searching these forums and checking specifications I decided on a Vaio VGN-FE41Z and so far I've been very pleased with how easy it has been to use all its features and hardware.

This has Intel Core 2 Duo T7200 CPU (VMX aka Virtualisation enabled), built-in Motion Eye video camera, WVGA screen (1400x1040?), 2GB RAM, 200GB SATA drive, DVD-RAM/-RW/+RW, Memory Stick, ExpressCard/34 adapter for 5-in-1 MMC/SD card support, Intel HDA audio, 802.11a/b/g, Nvidia GeForce Go 7600, Firewire, 3 x USB 2.0.

I've posted an article here in the [Desktop Hardware Compatibility List]("http://ubuntuforums.org/showpost.php?p=2702973&postcount=30") about it.

Ubuntu 7.04 Feisty (32-bit and 64-bit) installed out of the box with all major hardware supported. I had a little work to do to install the driver for the Motion Eye camera, and get the Linuxant drivers for the Conexant SoftModem.

Glidepad control for scroll-gestures and so on works fine.

I had to develop a small Gnome panel applet called [SmartDimmer]("http://ubuntuforums.org/showthread.php?t=451781") to control the Nvidia screen brightness, which uses the console program 'smartdimmer' and soon will support 'nvclock' too.

The minor niggles I'm working on are:

Sony Phoenix BIOS does not enable VMX. I have a hack for this, and am close to publishing a small utility program that will permanently enable VMX.

Blue Fn keys are not supported yet, but will be. They use the Sony Notebook Controller hardware, not the Sony PI used by most earlier Vaio models.

Suspend & Hibernate work, but on Resume the video fails to turn on the LCD backlight so the screen remains dark. This is an issue with ACPI and the NVidia proprietary drivers, and is likely to be solved soon. See bug [116553: Resume failure: Feisty + Sony Vaio VGN-FE41Z]("https://bugs.launchpad.net/ubuntu/+bug/116553") for updates on a solution.

Battery life on a standard 5,400milli-Amp-hour battery is around 3 hours. The high-capacity 7,800mAh battery from Sony is UK £279 but I've sourced two 7,400mAh batteries from Hong Kong for £78 total, inc. shipping.

As to Sony warranty support, it has been excellent. After a BIOS upgrade (done with the Sony/Phoenix WinPhlash program in Vista!) bricked the laptop a short call to Sony and they arranged for the laptop to be collected the following day, fixed, and returned in 5 days.

---

