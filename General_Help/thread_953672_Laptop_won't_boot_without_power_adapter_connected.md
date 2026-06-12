---
title: "Laptop won't boot without power adapter connected"
date: 2008-10-20
forum: General Help
---

### Post by sianxian on 2008-10-20
My laptop is Acer Aspire 5560 and it's pretty old, 2.5 years already. Dual boot (Windows XP & Ubuntu 8.04)

As the battery is very damaged due to improper usage (well i didn't know how to take care of my battery), every time i boot my laptop with battery fully charged without power adapter, it will say "WARNING, CRITICAL BATTERY".

My guess is that the full capacity of my battery detected by ubuntu on boot is within the critical battery range and it's preventing my laptop from booting. Before I installed Ubuntu, it was fine booting into Windows XP without power adapter.

Extra information: It takes less than 10 minutes for my battery to go from 100% to 0% (according to what the computer says), but at 0% it can last for another 40 minutes.

So my question is: is there any way to remove the battery check on boot so that I can start my laptop without the power adapter.

---

### Post by phidia on 2008-10-20
You can try the acpi=off or noapci boot option.

Look at the boot options guide [here]("https://help.ubuntu.com/community/BootOptions") and specifically the section titled > Change Boot Options Temporarily On An Existing Ubuntu System
Hope that's useful.

---

