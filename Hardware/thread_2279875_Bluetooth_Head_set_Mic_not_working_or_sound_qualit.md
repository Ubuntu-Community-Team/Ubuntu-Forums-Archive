---
title: "Bluetooth Head set Mic not working or sound quality really bad"
date: 2015-05-26
forum: Hardware
---

### Post by Thepinkgamer on 2015-05-26
Hello, I bought a wireless bluetooth headset today and so far it's been a bit of a struggel to get it to work on Linux. I had the standard problem of it being detected but not working.
After some googleing I found a guide that helped me to set it up by editing cd /etc/pulse/default.pa and adding load-module module-bluetooth-discover and now I can get sound. 
However the quality was much worse that it was on my Android phone and I knew something was up. I read that having the settings to A2DP would fix it and it sure did. So now I have great wireless headphones. However not headset. As the mic doesn't work when I have it on A2DP. So It feels like I have to pick between having it be a headset with poor quality and only mono or a good quality headphones. I could be fine with that but I want to know if there is a way to have both or maybe I should just invest in a weird headset next time.
I would love to get help. 
I am running Ubuntu Studio 15.04 on a Acer computer with and Intel corei5, Nvidia Graphics and 8 gig or Ram.

---

### Post by Vladlenin5000 on 2015-05-26
> **Thepinkgamer said:**
> As the mic doesn't work when I have it on A2DP. So It feels like I have to pick between having it be a headset with poor quality and only mono or a good quality headphones. I could be fine with that but I want to know if there is a way to have both or maybe I should just invest in a weird headset next time.

You just described what should be expected. Your Android phone toggles profiles whenever needed, here's a common scenario: You receive (or make) a call when you're listening to music (A2DP); the phone automatically stops or pauses the music player and switches to hand-free (HFP); when you're done with the call it usually resumes playing (A2DP again).
No, you can't have both at the same time, in a phone or in a PC, regardless of the OS.

---

### Post by Thepinkgamer on 2015-05-26
Okey thank you, I tought something was wrong :P 
Is there a way to make it toggle between the profiles on Ubuntu?

---

### Post by Vladlenin5000 on 2015-05-26
Unless the specific app you're using can do it, then no. There's no way to do it automatically. You must always do it manually at Sound Settings where the Bluetooth audio device should be already selected. There's a dropdown menu specifically for selecting the Bluetooth profile.

---

