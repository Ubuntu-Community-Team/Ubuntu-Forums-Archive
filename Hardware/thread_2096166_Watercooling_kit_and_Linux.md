---
title: "Watercooling kit and Linux"
date: 2012-12-19
forum: Hardware
---

### Post by NHerby on 2012-12-19
Hi,
I plan to buy a water-cooling system in order to overclock my CPU.
I'm still hesitating between those 2 systems:
- [Thermaltake water 2.0 extreme]("http://www.thermaltake.com/products-model.aspx?id=C_00001876")[URL="http://fr.thermaltake.com/products-model.aspx?id=C_00001876"]
[/URL]- [Corsair H100i ]("http://www.corsair.com/us/hydro-series-h100i-extreme-performance-liquid-cpu-cooler.html")
Both of them are connected to the motherboard via USB and come with a software that adjust the fan speed according to the temperature of the CPU. And of course, they only propose windows version of this software.
My concern is how the fan speed is managed when the software is not installed.
For info, I have a dual boot Kubuntu/Win7 and I only use Win7 for gaming, meaning that the CPU will only heat up when using Win7.
I'd like to be sure that the fans remain at low speed when using Linux keeping the noise as low as possible.
If someone here uses one of those cooling systems, I'd be happy to hear from them.
Thanks,
Herby.

---

### Post by NHerby on 2013-01-15
To get an answer, I sent a mail to both Thermaltake and Corsair support.
No answer from Thermaltake...
And here's the answer from Corsair:
"It will run at default profile fan settings. Which is the lowest profile  and will react to the coolant's temp.  [http://www.corsair.com/us/blog/understanding-the-hydro-series-h80-and-h100-cooling-performance-profiles](http://www.corsair.com/us/blog/understanding-the-hydro-series-h80-and-h100-cooling-performance-profiles).  it'll be the quiet profile on this link."
I've also heard that it is possible to bypass Corsair's fan control on this kit by plugging the fans directly on the motherboard CPU fan slot. This way, the fan speed can be managed via fancontrol under Linux.

---

### Post by eenofonn on 2013-01-16
Another thought is where are you going to do your overclock.  Sometimes you can do a software overclock in windows meaning you leave your bios settings alone and then the software overrides them when windows is loaded. Seems to me that would leave you in a pretty safe position if you're not overclocking when using Linux in a dual boot setup. Just my $.02

---

### Post by NHerby on 2013-01-30
Your 2 cents raise a good quesion!
My motherboard comes with a nice software that allows to fine tune the overclocking within windows. On the other hand, many people says that overclocking should be managed in the BIOS and nowhere else. So, actually, I don't know how I will proceed. The only thing I know so far is that I will need help to do this and it will be one of the first question I will ask on a dedicated foum.

---

### Post by NHerby on 2013-02-05
A quick feedback now that this H100i is intalled:
With the fans plugged on the waterblock, there is no speed control at all. The fans remain @ 2200 RPM all the time and make an unbearable noise.
To avoid this, I've installed a 4 pin PWM Y cable and plugged the 2 fans directly on the MB.
My MB (Gigabyte Z77X-D3H) is very good in managing fan speed with many BIOS option for this purpose.
In the end, the fans run at a very quiet 1200 RPM on idle and go up to 2700 RPM as soon as the CPU starts to heat up. All this without any additional software.:)

---

