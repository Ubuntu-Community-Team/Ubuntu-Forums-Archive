---
title: "Suggestions for self built desktop (14.04) for NAS &amp; asterisk with low power cons."
date: 2014-07-19
forum: Hardware
---

### Post by JohnyBeGood on 2014-07-19
Hi all,

I would like to build a desktop that wouldn't use much power. Right now I have [Acer AspireRevo]("http://upload.wikimedia.org/wikipedia/commons/5/53/2009_Taipei_IT_Month_Day1_Acer_Aspire_Revo.jpg") and its running latest standalone version of Elastix and its only using 16 watts.
I already have old case for the build (Antec P180) and would like to build system where I want to install 1 large HD and enable samba for storing surveillance videos from IP camera but at the same install FreePBX since I don't think its possible to install Elastix on Ubuntu. That would also give me ability to play and learn more about linux.
I do understand I will never get close to 16 watts of power consumption on any desktop but what would be the closest?
List of suggested parts would be much appreciated.

---

### Post by JohnyBeGood on 2014-07-24
Anyone? 
Why do posts here go unanswered? Is my question too confusing?
TIA

---

### Post by sjhupp on 2014-07-24
I don't know anything about asterisk (would like to - will google) but this sounds like a hardware question.
Low power boxes could be like your Asus eeepc type box, or anything with a pico psu.
I personally like the little microservers as you can configure any OS you like on them, and they're small and faily low power. Recent models have reasonable cpus, and there's a huge community and lots of forums for them and their capabilities. Using standard desktop psu and components would likely have much higher power usage.
EXSi, xen or kvm may be useful also.
My NAS chugs away on a microserver with 12.04 server running headless happily.

---

### Post by Bucky Ball on 2014-07-24
Power supply. That's about all I've got to add. A good one, name brand, 85+ efficiency, and no more powerful than you need. Use a PSU calculator to work out what you need (there was one on the Antec site from memory). 

One of the power wasting habits of many is to get a 1500W PSU when all they do is email and surf the net on a box that contains a hard drive, network card, motherboard, CPU and not a lot else. A 450W would do the job fine and save money over time (not to mention resources and the environment). 

NEVER go near a generic silver box PSU. They are 70% or less efficient generally (and can be dangerous when they explode because of lack of safety switches ... I speak from experience).

Though dated, there is plenty of food for thought in my rather long thread regarding building an energy efficient Linux box. The link is in my signature. Good luck.

---

### Post by Yellow Pasque on 2014-07-24
The Asus EB1036 looks nice for a complete, small box.
Otherwise, if you want to use the P180, look at something based on the Celeron J1900 (or its close relative, the Pentium J2900). AMD's Kabini/Mullins chips are alternatives too, but they use a few more Watts than the Bay Trail chips.
As for PSU, you can use a picoPSU or even just a power brick if you get a board with DC input like: [http://www.newegg.com/Product/Product.aspx?Item=N82E16813157495](http://www.newegg.com/Product/Product.aspx?Item=N82E16813157495)

---

### Post by Bucky Ball on 2014-07-24
The pico! Amazing. Never seen them. :-k

---

