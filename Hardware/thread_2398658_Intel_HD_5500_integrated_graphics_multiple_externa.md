---
title: "Intel HD 5500 integrated graphics multiple external monitor issues"
date: 2018-08-15
forum: Hardware
---

### Post by mvaaltola on 2018-08-15
Hello,

I recently bought a dock for my Thinkpad T450s work machine so I could connect it to my two main monitors at home. The laptop has an integrated Intel HD5500 graphics card. The monitors are rated 2560x1440@144hz and 2560x1440@60hz.

The setup works fine on the same machine in Windows 7. I simply connect both external monitors to the dock with Displayport cables, and after fiddling some settings in the Intel driver manager I can display video on all 3 monitors simultaneously. The 144hz monitor only runs at 100hz, but this is not a huge deal. However, I have not been able to achieve the same setup on Ubuntu 16.04.

The first issue I noticed when booting to Ubuntu is the 144hz monitor does not output any video when connected. I determined this is due to the high refresh rate, and after setting rate to 60 via xrandr the monitor displays video. Other supported modes listed by xrandr include 2560x1440@120hz and 100hz, but neither of those rates work, only 60hz.

 I can also get video output on the second monitor, but when I connect both monitors simultaneously, only one of them shows video and the other one remains blank. This is my main issue currently, any ideas on how to get this working? I can deal with 60hz video output on all monitors, but only being able to use 1 out of the 2 external monitors is really disappointing.

As I mentioned, this works fine on Windows, so the hardware is definitely capable. I tried searching for updated Intel graphics drivers for Linux but didn't find anything useful. Hope there's just something simple I have missed!

Best regards,
Mikael

---

