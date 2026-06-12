---
title: "Hardware suggestions?"
date: 2015-05-04
forum: Hardware
---

### Post by kooldino on 2015-05-04
I'm currently running on 12.04 LTS on some old, but very stable hardware.  

I'm looking to upgrade my hardware and run either 14.04 LTS or maybe 15.04, but I'm not sure how stable the latter is.

My primary concern is system stability (between hardware and software).  I also need it to be reasonably quick, and QUIET.  So I'd like to minimize the number of fans needed for cooling.

So I'm looking for the following pieces of hardware, and I need to be sure that they are not only kubuntu compatible, but that they have very good driver support which won't render my machine inoperable should I decide to upgrade to a newer driver version, etc.

[LIST]
[*]Motherboard / CPU / RAM
[*]Passively cooled video card.  In the past, I've had mixed luck with Nvidia cards on linux.  What is the most well supported, stable card that is passively cooled?  How is the support and performance for the newer intel on-die graphics?
[*]Audio - This can be on board if it's good hardware
[/LIST]

---

### Post by grahammechanical on 2015-05-04
15.04 only has 9 months support. This means that you will have to upgrade to 15.10 when it comes out and then to 16.04 when it comes out. Whereas, if you install 14.04 LTS you can directly upgrade to 16.04 LTS when it comes out or even delay until 18.04 LTS comes out. Just so that you know.

Hardware support is more a function of Linux than of the distribution. The latest versions of the Ubuntu family have the latest Linux kernels and hardware/firmware stacks. LTS releases get this upgrade some months after a new version is released. For example, 14.04 has now reached 14.04.2 which has the same kernel and hardware stack as 14.10.

The same kernel and hardware stack as in 15.04 will not get into 14.04 until 14.04.3 is released sometime during this coming August.

If you purchase the very latest hardware then be prepared for the Linux developers to take a little time to catch up. This is the traditional situation in Linux.

Regards.

---

### Post by mörgæs on 2015-05-04
Are you saying that you have decided to buy new hardware before you have even tried 14.04 and/or 15.04 on the old?

---

### Post by Yellow Pasque on 2015-05-05
You don't say how much 3D power you need. In fact, you didn't tell us what you plan to do with your hardware at all....

---

### Post by SeijiSensei on 2015-05-05
I doubt the hardware demands of 14.04 will be any greater than 12.04.  If you want stability, you should stick with LTS releases.  Kubuntu in particular is moving to KDE5 with plasma in 15.04.  I'd wait until 16.04 so they can iron out the bugs.

If you're in the market for a desktop, I'm very happy with this: [http://www.newegg.com/Product/Product.aspx?Item=N82E16883220835](http://www.newegg.com/Product/Product.aspx?Item=N82E16883220835).  It's back on sale at NewEgg for $450.  I thought I might buy a GTX 750 card for it, but the on-board Intel chips for both video and audio work fine with an HDMI connection to my AV components.  It can also play a couple of Windows games I tried like FF XIV and Dragon Age: Origins, too.

---

### Post by kooldino on 2015-05-06
> **grahammechanical said:**
> 15.04 only has 9 months support. This means that you will have to upgrade to 15.10 when it comes out and then to 16.04 when it comes out. Whereas, if you install 14.04 LTS you can directly upgrade to 16.04 LTS when it comes out or even delay until 18.04 LTS comes out. Just so that you know.

Hardware support is more a function of Linux than of the distribution. The latest versions of the Ubuntu family have the latest Linux kernels and hardware/firmware stacks. LTS releases get this upgrade some months after a new version is released. For example, 14.04 has now reached 14.04.2 which has the same kernel and hardware stack as 14.10.

The same kernel and hardware stack as in 15.04 will not get into 14.04 until 14.04.3 is released sometime during this coming August.

If you purchase the very latest hardware then be prepared for the Linux developers to take a little time to catch up. This is the traditional situation in Linux.

Regards.

Good info.  Looks like I'll stick with 14.04.x LTS.

---

### Post by kooldino on 2015-05-06
> **Temüjin said:**
> You don't say how much 3D power you need. In fact, you didn't tell us what you plan to do with your hardware at all....

Nothing special really.  I don't game on this machine, but having moderate gaming capabilities would be nice.

---

### Post by kooldino on 2015-05-06
> **SeijiSensei said:**
> I doubt the hardware demands of 14.04 will be any greater than 12.04.  If you want stability, you should stick with LTS releases.  Kubuntu in particular is moving to KDE5 with plasma in 15.04.  I'd wait until 16.04 so they can iron out the bugs.

If you're in the market for a desktop, I'm very happy with this: [http://www.newegg.com/Product/Product.aspx?Item=N82E16883220835](http://www.newegg.com/Product/Product.aspx?Item=N82E16883220835).  It's back on sale at NewEgg for $450.  I thought I might buy a GTX 750 card for it, but the on-board Intel chips for both video and audio work fine with an HDMI connection to my AV components.  It can also play a couple of Windows games I tried like FF XIV and Dragon Age: Origins, too.

I don't want an entire machine, since I have a good case, PSU, HDD, etc.

How is linux support for the Iris integrated graphics?  Are there 3D driveres fort them etc?

---

### Post by mastablasta on 2015-05-06
Intel opensources it's drivers and works with Linux devs. so drivers are already in kernel.

---

### Post by kooldino on 2015-05-06
Sweet, so maybe an Intel reference board is the way to go.

---

### Post by mastablasta on 2015-05-07
Intel or AMD APU's (CPU with GPU on it) work fine in Linux.

---

