---
title: "3rd monitor stopped working after driver &quot;update&quot;"
date: 2020-01-11
forum: Hardware
---

### Post by rafiqcombrinck on 2020-01-11
Hi All

So I loaded 18.04 on my office machine (dual boot) and I was quite impressed that all three my monitors were working. A few days later I realized that Google Earth Pro was not rendering properly and after some searching I found a solution that said I should load an older version of my NVIDIA driver (3.90 I think it was), which worked as I could then use GEP. Only problem is my 3rd monitor has now stopped working. I tried reverting back to the last/previous driver but it still wouldn't come on.

If I go into Display Settings it does not see the 3rd monitor, if I go into NVIDIA Settings I can see the 3rd monitor but it shows disabled. If I try and enable it it does not appear in Display Settings.

I'm running 2 x GeFroce GT710 cards, with 1 x monitor on HDMI and 1 x monitor on DVI and then on the second GeForce I have 1 x monitor in HDMI. Linux sees both cards (can even see card's status under NVIDIA Settings). If I boot into Windows all monitors work so it's definitely not hardware related. I read some posts about some settings, but found that I did not have the described folders/locations for the NVIDIA settings so I'm a tad lost.

Any ideas?

Thanks,
R

---

### Post by Autodave on 2020-01-11
Where did you get the drivers from?

---

### Post by rafiqcombrinck on 2020-01-11
I used this command ... **sudo apt install nvidia-driver-390 **... so it must be from the "normal" Ubuntu repositories.

---

### Post by rafiqcombrinck on 2020-01-15
Booted with a Live cd and all three monitors worked again, so long story short, I reloaded Ubuntu, set the latest NVIDIA driver and all is working fine again (even Google Earth).

PS. I did read quite a few posts saying there are generally issues running multiple GeForce cards so ended up using the onboard HDMI output and HDMI & DVI from the one card.

---

