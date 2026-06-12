---
title: "CPU locked to lowest frequency with smaller power supply (various laptops)"
date: 2010-11-13
forum: Hardware
---

### Post by recluce on 2010-11-13
This problem has been described a couple of times in separate threads, never going anywhere. So I am trying to consolidate here.

**_The Issue_**
When using a laptop with a power supply that has less than the recommended power output (for example, a 65W power supply on a notebook that has a standard 90W power supply), the CPU gets locked to the lowest possible frequency and cannot be set to anything else. As soon as the system runs on batteries or you connect a stronger power supply, everything returns to normal.

**_Which systems are afflicted by this problem?**_
I know for certain that Dell Latitude D-series systems are affected, I have heard that Latitude E-series, Dell Precision based on the afore mentioned and certain Dell Inspiron / Studio systems share the same problem. There are also reports about some HP and Lenovo laptops sharing the same issue. 

**_Why is this an issue?_**
Some people may argue that you should just use an AC adaptor that is strong enough. Unfortunately, that is not always possible. Especially if you use a DC/DC inverter or an airplane power outlet, you may not have the luxury of connecting that super strong power supply. Also, the big brutes are often too heavy to lug around, so a smaller power supply may be desirable if you have to schlepp the thing around all day.

**_Why this is a regression_**
I could verify that the problem is **not present** in Ubuntu Jaunty (x64, kernel 2.6.28-19). Under Jaunty, the CPU scales as usual. If the power budget of the power supply is exhausted, charging the battery is disabled.  The problem is present in Lucid and Maverick (tested x64 kernels: 2.6.35-22 and 2.6.32-25 (Lucid), 2.6.35-22 (Maverick), I don't have Karmic to verify.

**_What I am looking for_**
1.) Get feedback from people with other brands/models of laptops and the same issue

2.) A possible workaround or solution?

3.) Against which package should I file a regression/bug report on Launchpad?

4.) Word from people with a Latitude D-series machine on Karmic if they have this issue - and what kernel they are using).

---

### Post by PRC09 on 2010-11-13
I have a Dell D610 and have a non-OEM power supply and the machine itself picks up the issue at the bios prompt saying non standard power supply and it wont run at maximum speed(cant remember the exact terminiology) until you plug in the proper one.This may be a machine itself issue and not an OS issue......

---

### Post by recluce on 2010-11-13
> **PRC09 said:**
> I have a Dell D610 and have a non-OEM power supply and the machine itself picks up the issue at the bios prompt saying non standard power supply and it wont run at maximum speed(cant remember the exact terminiology) until you plug in the proper one.This may be a machine itself issue and not an OS issue......

Sorry, but did you even bother to read my post? As I stated: **under Jaunty (and XP) the CPU is not locked to the lowest frequency**, so it is not the "machine" or BIOS. 

Also, the power requirement for a D830 running at full CPU speed is about 35W to 45W, so more than enough power in a 65W power supply (with battery charge disabled).

---

### Post by PRC09 on 2010-11-13
I did read your post......I was STATING WHAT HAPPENS WITH MINE ............

---

### Post by recluce on 2010-11-14
> **PRC09 said:**
> I did read your post......I was STATING WHAT HAPPENS WITH MINE ............

This is leading nowhere. You did not mention what version of Ubuntu you are using, so this is not very helpful.

I am well aware of the BIOS warning (which is configurable, btw) - but in spite of that BIOS warning, Jaunty can scale the CPU just fine, as can Windows XP. Lucid and Maverick cannot, thus: regression.

---

