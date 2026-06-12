---
title: "Ubuntu compatibility over Intel graphics vs ATI graphics?"
date: 2011-03-15
forum: Hardware
---

### Post by alienreborn on 2011-03-15
[COLOR=#000000][FONT=Times New Roman][FONT=verdana]Hi, Linux noob here
I am torn between buying Asus Eee PC 1015P (comes with Intel Dual Core N550 and **Intel GMA 3150** graphics with Win7 pre-installed) and 1215T(comes with AMD Athlon II K125 with **ATI HD4250** graphics with DOS pre-installed)
I intend to use ubuntu (or it's derivatives lubuntu or linux mint) on my netbook. I would like to know if any one of you have experienced any problems with above mentioned graphic cards? 



If, in case, you are running ubuntu on Asus Eee PC's (specifically above mentioned models), is everything smooth and running as it supposed to be?
Thanks for your time, in advance!
[/FONT][/FONT][/COLOR]

---

### Post by coffeecat on 2011-03-15
I'm assuming you mean the Mobility Radeon 4250 which is a bit different from the Radeon 4250.  See:

[http://en.wikipedia.org/wiki/Comparison_of_ATI_Graphics_Processing_Units#Mobility_Radeon_HD_4xxx_Series](http://en.wikipedia.org/wiki/Comparison_of_ATI_Graphics_Processing_Units#Mobility_Radeon_HD_4xxx_Series)

And:

[http://en.wikipedia.org/wiki/Comparison_of_ATI_Graphics_Processing_Units#IGP_.28HD_3xxx.2C_HD_4xxx.29](http://en.wikipedia.org/wiki/Comparison_of_ATI_Graphics_Processing_Units#IGP_.28HD_3xxx.2C_HD_4xxx.29)

Both of those graphics cards *should* work just fine with the default drivers in Ubuntu. As a bonus you get compiz 3d gee-whiz special effects with the default drivers for both those cards. I have the Mobility Radeon 4200 on my laptop, which is almost identical to the 4250 according to that link, and Ubuntu, and desktop effects, are fine.

I've noticed you get a slightly crisper image with an ATI card (and the open source driver) than with an Intel. I've seen others mention this.

One warning: if you go for the ATI and install Ubuntu the system will prompt you to install the proprietary driver. My advice: if everything is working OK then **don't**. You will probably regret it if you do.

---

### Post by alienreborn on 2011-03-15
> **coffeecat said:**
> I'm assuming you mean the Mobility Radeon 4250 which is a bit different from the Radeon 4250.  See:

[http://en.wikipedia.org/wiki/Comparison_of_ATI_Graphics_Processing_Units#Mobility_Radeon_HD_4xxx_Series](http://en.wikipedia.org/wiki/Comparison_of_ATI_Graphics_Processing_Units#Mobility_Radeon_HD_4xxx_Series)

And:

[http://en.wikipedia.org/wiki/Comparison_of_ATI_Graphics_Processing_Units#IGP_.28HD_3xxx.2C_HD_4xxx.29](http://en.wikipedia.org/wiki/Comparison_of_ATI_Graphics_Processing_Units#IGP_.28HD_3xxx.2C_HD_4xxx.29)

Both of those graphics cards *should* work just fine with the default drivers in Ubuntu. As a bonus you get compiz 3d gee-whiz special effects with the default drivers for both those cards. I have the Mobility Radeon 4200 on my laptop, which is almost identical to the 4250 according to that link, and Ubuntu, and desktop effects, are fine.

I've noticed you get a slightly crisper image with an ATI card (and the open source driver) than with an Intel. I've seen others mention this.

One warning: if you go for the ATI and install Ubuntu the system will prompt you to install the proprietary driver. My advice: if everything is working OK then **don't**. You will probably regret it if you do.

Thanks Coffecat, 
so, intel integrated graphics are also supported by default in ubuntu installation?

---

### Post by coffeecat on 2011-03-15
> **alienreborn said:**
> Thanks Coffecat, 
so, intel integrated graphics are also supported by default in ubuntu installation?

Most. Some of the older chipsets (8** series mostly) are problematic in recent versions of Ubuntu and the dreaded Poulsbo chipset (GMA500 iirc) is best avoided completely, but the rest ought to work just fine.

I have Intel graphics in my other laptop, but not your GMA3150, and everything always works without any fiddling on my part. If you want to be sure, try searching the forum for GMA3150 and see if anyone has encountered any problems.

---

### Post by ario on 2011-07-30
It depends what do you mean by terms "Works" or "Compatible".
I have an Asus EeePC 1015px with Intel n570 CPU which contains the GMA3150 GPU integrated.
Everything works except something called Dynamic Rendering Clock.
If you don't know what is this, I just tell you that it's enabled on windows but disabled on Linux. As I searched till now, no one even knows that this function must be enabled on linux. So it's disabled and my laptop is very hot. GPU temperatures gets high up to 70C and battery life time reduces down to 7 hour which is 11 hour on Windows. I can not keep my netbook on my laps because it can burn my skin! All because of that ridiculous "Dynamic Rendering Clock".
I started several treads in several forums and sent a bunch of emails to Intellinuxgraphics.org and no one even sent me an "I don't know" message!
Still searching for a solution :(

---

