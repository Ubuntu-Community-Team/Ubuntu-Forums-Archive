---
title: "Horrible Battery life with ubuntu"
date: 2009-06-24
forum: Hardware
---

### Post by wcdune on 2009-06-24
I used to get 3 hours of battery in vista with backlight dim but with ubuntu 9.0 i get at best 15 minutes    its impossible for me to go anywhere with my laptop and i cant even figure out how to even turn the backlight off. I deleted my vista partition too.
I have a Sony Vaio laptop model  FZ340e           My computer always has a fan on and is very noisy.
It also runs very hot.  [SIZE=3]  [/SIZE][SIZE=7]_***[SIZE=3]Please help[/SIZE] ***_[/SIZE]
also the battery life with ubuntu used to be an hour but over the last few months has gotten worse and worse

---

### Post by m0rph3us2009 on 2009-06-27
Battery life getting worse over a few months is usually down to battery memory, not your operating system.

To dim your display while running on battery power, go to System > Preferences > Power Management, and then select the battery tab to tune your system to be a little more efficient.

As for your battery life dropping to 15 minutes gradually...

Do you plug your laptop in to AC power while battery is partially charged? This is the main cause of battery memory problems.

To fix a bad battery you could try the following, although it is slightly risky.

1. Go into power management and tell Ubuntu not to do anything when battery level gets critical.
you may also want to set backlight to 100% and not dim display to drain battery quicker while you carry out this process. 
You should also check your BIOS to make sure there is no power management built in to your chipset, if so, then you should disable this.

2. Run your laptop until the battery is completely drained, and the laptop powers down. (Not ideal but has to be done to completely drain battery)
Continue to attempt to turn on the laptop until there isn't any power left in the battery.

3. Charge the laptop for 12 hours, without powering on the laptop. Last time I used this method I discharged during the day and left to charge over-night. 

Once the battery has been fully discharged, start from step 2 again. You may need to repeat several times to get your battery life back to what it should be. (6 times in my case on my Acer Aspire 5920)

After you have completed this process and are happy with the results, you can put your power management back to what it was before you started. 

Don't forget, don't charge your battery unless it is empty. (I usually plug mine in at 5% power, which keeps my battery capacity around about 98% of what it was origonaly)

WARNING: Sudden power loss to your hard disk may cause loss of data or damage to the platers within, continue at your own risk!

Good luck :)

m0rph...

---

### Post by jward3010 on 2009-06-27
What Morpheus is saying above is completely correct and possibly something should be stuck into "Notifications" highlighting these couple of things, as they are basic practice and not everybody knows them. 

Consider also the fact that bad usage of the battery over time may have destroyed the Lithium Ion cells in the battery permanently and the above technique may or may not do a lot for you. Although give it a blast as it might revive a sleepy battery that just needs a good technique for it to be fit and healthy again.

---

### Post by wcdune on 2009-06-28
Thanks SOOOO much for helping
Also could u tell me how to check bios for power management things.
I will try your technique soon, but could the problem also be that the computer uses more power on battery than when charging.
After disconnecting the power history goes completely crazy with massive spikes and dips

---

### Post by wcdune on 2009-06-28
oh yeah 

um the computer also runs very hot and the fans are constantly on.
None of the tools in power preferences do any good and the backlit control does not work for me. My screen stays at the same brightness permanently.

---

### Post by wcdune on 2009-06-28
LAst thing is that my computer is fairly new , only from 08, and my sister who has a 4 year old computer, has almost the same battery capacity as she had in the begining. Also ubuntu reports the battery as having the same amount capacity so i am a bit confused.

---

