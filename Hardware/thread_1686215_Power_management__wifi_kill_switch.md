---
title: "Power management / wifi kill switch"
date: 2011-02-12
forum: Hardware
---

### Post by Tinfoil Hat on 2011-02-12
Hi all,

Having recently invested in a Lenovo X200s that came infected with Windows Vista, I finally decided to run Ubuntu on a laptop that I use on a daily basis. I was of course pleasantly surprised how well it runs with a straight install of 64 bit 10.04. Fantastic stuff. 
Finally making this transition on the laptop as well, there was something I wasn't too familiar with however - namely power management. I use my laptop on the road and I've been tinkering trying to maximize my battery life. 

I start out by disabling bluetooth, resulting in a quite nice power usage drop. Hardly ever use it anyway. Then on to the intel 5100 Wlan. Doing *iwconfig wlan0 power on *gives me yet another dramatic battery life increase. With the screen reasonably dimmed powertop tells me i'm using around 8,5W and I find myself quite happy. Then, just for the hell of it, I decide to check what happens if I kill the wifi (using the hardware switch on the side). This is where I start scratching my head. Power usage goes UP ½ watt, in spite of iwlagn not causing constant wakeups anymore. Tried everything I could think of now, unloading drivers for it and whatnot. Used rfkill to monitor the hardware block on the adapter, and yep, blocked. Soft blocking it does not change anything either.

Soo. Does anyone have any experience with this kind of thing? Or any ideas how on earth it's possible to have better battery life with wireless on and associated than with wireless disabled through the kill switch? I'm stumped.

Help.

---

### Post by Tinfoil Hat on 2011-02-15
Alright, so I've been experimenting. At work, we have a temperature chamber, nice and constant in there. I've stuck the laptop in there, disabled the fan and used the hardware sensor applet to display the mini-pcie temperature. Did five on-stabilize-off-stabilize kill switch cycles. The mini-pcie temperature goes up 1-2 degrees whenever i disable wifi, drops back whenever i enable and connect to the network. 

Come on guys, what am I missing here? Anyone have any clues? Ideas?

---

