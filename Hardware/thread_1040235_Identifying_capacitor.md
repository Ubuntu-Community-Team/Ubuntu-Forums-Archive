---
title: "Identifying capacitor"
date: 2009-01-15
forum: Hardware
---

### Post by ebp on 2009-01-15
Hi i was hoping that you could help me identify this capacitor.


[http://www.myupload.dk/showfile/142385bdda3.jpg/]("http://www.myupload.dk/showfile/142385bdda3.jpg/")

---

### Post by ebp on 2009-01-15
I know that this might not be easy but i really hope you can help :)

---

### Post by electrogeist on 2009-01-15
The 532 means

53 pF + 2 more zeros = 5300pF = 5.3nF

(the third digit is a multiplier)

I am not sure about tolerance or voltage.  

That leaky capacitor made a mess, don't forget to clean it up.

---

### Post by AKADAP on 2009-01-15
Given that is a switching power supply there are a few more parameters you need to worry about.

ESR= equivalent series resistance. Depending on the design there may be maximum and minimum requirements for this.

Voltage rating: Since this is an electrolytic, you want a voltage rating at least twice the voltage you plan to put on the cap.

Power handling: Switching power supplies drive a significant ripple current through their capacitors. Combine that with a significant ESR, and you can end up dissipating a lot of power in a cap. That can cause them to overheat & leak or even explode.

The safest thing you can do is to buy a replacement power supply. Don't try and replace that cap unless you fully understand what you are doing.

---

### Post by ebp on 2009-01-16
> **electrogeist said:**
> The 532 means

53 pF + 2 more zeros = 5300pF = 5.3nF

(the third digit is a multiplier)

I am not sure about tolerance or voltage.  

That leaky capacitor made a mess, don't forget to clean it up.

Thanks for the answer, the mess is not from the capacitor but some old foam :)

---

### Post by electrogeist on 2009-01-16
Thats good 

but I would not dismiss what AKADAP is saying too... maybe at the least find some electronics forums and get some more info.

---

### Post by markbuntu on 2009-01-16
That is an electrolytic capacitor. it is probably 5300uf. You can probably replace it with anything that is at least 5000uf (microfarads) and at least whatever voltage that power supply is supposed to put out. You could put a 10,000 uf 20v capacitor in there and it would work just fine if that is a 12v p/s.

That cap is used for smoothing the output so its value is not critical and an electrolytic capacitor with larger values can actually work better if you can fit it in the case. If it is in a place that gets hot just make sure the temperature rating is at least 85c.

I used to fix stuff like that all the time.

---

### Post by Carlos Sevcik on 2009-01-16
> **ebp said:**
> Thanks for the answer, the mess is not from the capacitor but some old foam :)

There are no electrolytic capacitors of 5.3 nF, such a small capacitor would be ceramic or mylar or somthing like that, actually I doubt that nF capacitors are being built, nF are in the range of stray capacitances. Electrolytics are uF usually well above 1 uF. The red wire is positive and the black one is negative, its probably a low voltage capacitor (20V maximum) in the hundreds of uF. Since it seems a power supply its best being wrong by overshooting the values than by being low.

---

