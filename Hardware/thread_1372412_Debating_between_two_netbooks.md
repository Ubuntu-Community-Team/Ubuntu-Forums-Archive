---
title: "Debating between two netbooks"
date: 2010-01-04
forum: Hardware
---

### Post by Rumbl3 on 2010-01-04
Well I'm eye balling both of these netbooks.

Not sure really the thing that will get me is which one is better out of the box for ubuntu?

Acer 1410
[http://www.newegg.com/Product/Product.aspx?Item=N82E16834115655&cm_re=acer_1410-_-34-115-655-_-Product](http://www.newegg.com/Product/Product.aspx?Item=N82E16834115655&cm_re=acer_1410-_-34-115-655-_-Product)

Or

Asus 1201n
[http://www.newegg.com/Product/Product.aspx?Item=N82E16834220659&cm_re=1201n-_-34-220-659-_-Product](http://www.newegg.com/Product/Product.aspx?Item=N82E16834220659&cm_re=1201n-_-34-220-659-_-Product)

I heard only problem with 1201 is the wireless but it works after u use a older driver. 

Haven't seen to much on the 1410. 

Anyway any suggestions thx?

---

### Post by Rumbl3 on 2010-01-05
bump no one?

the 1201n has nvidia ion graphics but a slower dual core atom, the 1410 has a dual core celeron much faster but on board intel graphics. I tend to do light gaming like urban terror so i'm guessing i should go for the ion graphics?

---

### Post by Cabs21 on 2010-01-05
> **Rumbl3 said:**
> Well I'm eye balling both of these netbooks.

Not sure really the thing that will get me is which one is better out of the box for ubuntu?

Acer 1410
[http://www.newegg.com/Product/Product.aspx?Item=N82E16834115655&cm_re=acer_1410-_-34-115-655-_-Product](http://www.newegg.com/Product/Product.aspx?Item=N82E16834115655&cm_re=acer_1410-_-34-115-655-_-Product)

Or

Asus 1201n
[http://www.newegg.com/Product/Product.aspx?Item=N82E16834220659&cm_re=1201n-_-34-220-659-_-Product](http://www.newegg.com/Product/Product.aspx?Item=N82E16834220659&cm_re=1201n-_-34-220-659-_-Product)

I heard only problem with 1201 is the wireless but it works after u use a older driver. 

Haven't seen to much on the 1410. 

Anyway any suggestions thx?

I would guess that you are not looking to do any hi-end gaming with this laptop,  personally i like HPs but thats just me.

Here is a compare of your processors
[http://ark.intel.com/Compare.aspx?ids=42779,35641](http://ark.intel.com/Compare.aspx?ids=42779,35641)
(sorry if link doesn't work I am new at BB code)

Here is a review of each graphics card

Nvidia ion
[http://www.phoronix.com/scan.php?page=article&item=nvidia_ion_linux&num=1](http://www.phoronix.com/scan.php?page=article&item=nvidia_ion_linux&num=1)

Intel GMA X4500HD
[http://www.phoronix.com/scan.php?page=article&item=intel_x4500hd&num=1](http://www.phoronix.com/scan.php?page=article&item=intel_x4500hd&num=1)

hope this helps.

If you post what you are primarily using it for that will help also.

---

### Post by yelvington on 2010-01-05
I don't know anything about the Asus model, but I have the Acer 1410 with the dual-core Celeron (SU2300). Of the several options for the 1410, the SU2300 Celeron seems to be the best.

I specifically chose this model over some others because when I was looking I saw some posts suggesting that the Ion was not yet well-supported by Ubuntu (which may not be the case now). 

Nearly everything works great right out of the box; the exception is multitouch scrolling, which does not. 

I'm very happy with the ordinary-usage performance. It feels every bit as snappy as my work Macbook, which has nearly twice as much horsepower. HD video works great, even Flash.

Gaming, though, is marginal. Alien Arena drags badly. OpenArena works OK. Nexuiz has bizarre rendering problems.

---

### Post by Rumbl3 on 2010-01-05
Kool i might get one. I mainly going to use it for school type stuff coming up. Possibly some work of my own. Mostly I just play snes and neo geo roms little bit of urban terror but i can do that on my sons machine. I also like to play dofus just kinda got back into that but it's pretty easy to run.

So i'm thinking maybe i'll go with the acer. Processing power it looks like its way way faster then the dual core atom.

Right now I'm using a old 754 socket machine my old dual core 939 died, i'm on windows xp now also lol my mobo don't play nice with linux at all.

But hmm will see i just like the thought of a dedicated gpu, rather then onboard just because on my old p4 machine the onboard was so sluggish feeling but that was also a old machine too.

---

### Post by Rumbl3 on 2010-01-06
Also happen to see this on their site. Looks like the 1201n works just fine sept for wireless but that can be done manually.

[http://www.phoronix.com/scan.php?page=article&item=asus_eee_1201n&num=1](http://www.phoronix.com/scan.php?page=article&item=asus_eee_1201n&num=1)

---

### Post by hsoulen on 2010-04-07
Hi,

I have the 1201n and I love it.

Couple of things with Karmic:


[LIST]
[*]No microphone, still working on this one but the BT lets me use a BT headset so Skype works...
[*]Wireless, Realtek supports Linux and 2.6 kernels directly so you can download the newest driver from them "rtl8192se_linux_2.6.0015.0127.2010" is current. Have to rebuild it every time you install a new kernel but have to live with that until it is supported in the kernel
[*]Suspend, works about 50% of the time... I am 100% positive this is because of the wireless driver
[/LIST]
Couple of things with Lucid Beta 1:


[LIST]
[*]No microphone, still working on this one but the BT lets me use a  BT headset so...
[*]Wireless, Realtek supports Linux and 2.6 kernels directly so you  can download the newest driver from them "rtl8192se_linux_2.6.0015.0127.2010"  is current. Have to rebuild it every time you install a new kernel but  have to live with that until it is supported in the kernel
[*]Suspend, works about 50% of the time... I am 100% positive this is  because of the wireless driver (plus kernel panics because of the wireless driver)
[*]No volume FN keys... xev does not even register events for these keys so I am trying to figure out an ACPI work-around and praying that this gets backported since they worked fine in Karmic
[/LIST]
General:

[LIST]
[*]ION is pretty awesome for a netbook and the Atom 330 lets me play a bunch of older games at native resolution with no issue. Running NVIDIA 195.36 proprietary drivers and all compiz effects are nice
[*]Battery life is fairly crap, I get about 3 hrs MAX just surfing/email etc. play games with the brick plugged in! Also the charger takes WAY to long to charge the battery
[/LIST]
Hope this helps!

---

### Post by emoguitarist06 on 2010-05-04
I have the 1201N and I also Love it

Ubuntu 10.04 mic works perfectly just a few tweaks needed in pavucontrol

Wirless you download driver from realtek at
[[http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=21&PFid=48&Level=5&Conn=4&DownTypeID=3&GetDown=false&Downloads=true](http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=21&PFid=48&Level=5&Conn=4&DownTypeID=3&GetDown=false&Downloads=true)
choose RTL8191SE-VA2

nvidia works with propriety driver included in ubuntu

FN keys are fixed with a simple add in grub2 parameters
Adding "acpi_osi=Linux" to the grub's kernel boot parameters works.
fn-SPACE belongs to the "Super Hybrid Engine" throttle control, which does not exist on the linux side.
fn-V could work if bound to an application for the camera (like cheese).
fn-C is for the screensaver, so could be bound like the CTRL-L standard action.

p.s.
I play WOW perfectly on Ubuntu using wine

---

### Post by hsoulen on 2010-05-05
> **emoguitarist06 said:**
> I have the 1201N and I also Love it

Ubuntu 10.04 mic works perfectly just a few tweaks needed in pavucontrol

Wirless you download driver from realtek at
[[http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=21&PFid=48&Level=5&Conn=4&DownTypeID=3&GetDown=false&Downloads=true](http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=21&PFid=48&Level=5&Conn=4&DownTypeID=3&GetDown=false&Downloads=true)
choose RTL8191SE-VA2

nvidia works with propriety driver included in ubuntu

FN keys are fixed with a simple add in grub2 parameters
Adding "acpi_osi=Linux" to the grub's kernel boot parameters works.
fn-SPACE belongs to the "Super Hybrid Engine" throttle control, which does not exist on the linux side.
fn-V could work if bound to an application for the camera (like cheese).
fn-C is for the screensaver, so could be bound like the CTRL-L standard action.

p.s.
I play WOW perfectly on Ubuntu using wine

Here-here!

Have implemented all of the above since my last post, both on Karmic and now on Lucid. For me the the only difference is that I use the proprietary NVidia driver (from NVidia downloads) in addition to the Realtek wireless. Compile and install work with a few warning messages (not sure Lucid fully supports the install yet so it may be best for folks to sick with the official restricted driver from the Ubuntu repositories, just make sure "nvidia-current" is selected in Synaptic).

Only outstanding issue is that even with the "acpi_osi=Linux" to the kernel boot params I still see a message at boot about probing "SMB2" for the NForce chipset. No big deal, just annoying and heck my fn buttons are all working so I can live with the boot message.

All around I would say the 1201n is an awesome purchase and with VDPAU and SMPlayer, HD video is sweet! Compiz is working without issue, wireless is reliable and I am a happy camper.

Cheers,

Hank

---

### Post by emoguitarist06 on 2010-05-05
> **hsoulen said:**
> Here-here!

Only outstanding issue is that even with the "acpi_osi=Linux" to the kernel boot params I still see a message at boot about probing "SMB2" for the NForce chipset. No big deal, just annoying and heck my fn buttons are all working so I can live with the boot message.

Hank

The "acpi_osi=Linux" is only for the function keys
the "error probing SMB2" is a dmesg bug having to do with Nvidia as you know
Bug is filed here:
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/443113](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/443113)
here: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/560274](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/560274)
and here: [https://bugs.launchpad.net/ubuntu/+bug/561738](https://bugs.launchpad.net/ubuntu/+bug/561738)
It is easily suppressed with 
"acpi_enforce_resources=lax" in grub2

So my grub says this:
GRUB_CMDLINE_LINUX="acpi_enforce_resources=lax acpi_osi=Linux quiet splash"

---

### Post by hsoulen on 2010-05-06
> **emoguitarist06 said:**
> The "acpi_osi=Linux" is only for the function keys
the "error probing SMB2" is a dmesg bug having to do with Nvidia as you know
Bug is filed here:
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/443113](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/443113)
here: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/560274](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/560274)
and here: [https://bugs.launchpad.net/ubuntu/+bug/561738](https://bugs.launchpad.net/ubuntu/+bug/561738)
It is easily suppressed with 
"acpi_enforce_resources=lax" in grub2

So my grub says this:
GRUB_CMDLINE_LINUX="acpi_enforce_resources=lax acpi_osi=Linux quiet splash"

Thanks, been through the bug list for it but specifically left "acpi_enforce_resources=lax" out of my boot params hoping the latest kernel updates would have resolved.

Alas, it has not, nor is the realtek driver working "out of the box". There are several threads on launchpad about the driver and firmware being backported but even in 3.6.32-22 the driver loads but cant scan for networks (wlan0 says no networks found). Back to the Realtek driver but no big deal it will come.

Thanks for the feedback.

You are playing Wow on Wine, any other games? I would love to get rid of my Win 7 partition, but outside of the original COD I have not had much luck with games and Wine.

Hank

---

### Post by emoguitarist06 on 2010-05-06
> **hsoulen said:**
> 
You are playing Wow on Wine, any other games? I would love to get rid of my Win 7 partition, but outside of the original COD I have not had much luck with games and Wine.

Hank

No I actually haven't tried anything else. I'm not too much of a gamer but I like WoW :)
However at winehq.org there seems to be plenty of games that work flawlessly via Wine and most of them give you instructions to install it.

---

