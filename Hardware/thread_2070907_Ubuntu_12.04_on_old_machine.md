---
title: "Ubuntu 12.04 on old machine"
date: 2012-10-14
forum: Hardware
---

### Post by bugsvoid on 2012-10-14
Hello everybody,

I have and old machine with [D101GGC]("http://www.intel.com/support/motherboards/desktop/d101ggc/sb/CS-029351.htm") motherboard & P4 2.66GHz CPU. I had installed Ubuntu 11.04. The machine was slow but still usable. I had 512MB or memory at that time.

Later, I added another 1GB memory to this machine and then installed Ubuntu 12.04. But now the machine is much more slower. I was exepcting that with the memory upgrade & probable performance fixes of Unity in 12.04, the machine would be more responsive. But the actual experience is opposite. Simple opening of the dash takes some time to load & populate all the lists. I have not measured accurate time but its a general comparision between 11.04 & 12.04 on the same machine.

Is this config too old now for Ubuntu 12.04 or it is a general observation that 12.04 is observably slower. Would installing 12.04.1 help? I saw some performance related fixes in the change list.

BTW, unity-2d works better, as expected.

Thanks & regards.

---

### Post by Karlchen on 2012-10-14
Hello, bugsvoid.

Ubuntu 12.04.1 is Ubuntu 12.04 SP1 (service pack 1).
Therefore, whenever you do a fresh installation, install Ubuntu 12.04.1 directly. Why would you want to install an outdated edition of Ubuntu 12.04?

About the experienced speed:
The main problem on most old machines will be the poor graphics performance.

The default desktop engine of Ubuntu 12.04(.1) is Unity. Unity works fine provided your graphics card is powerful enough and provided it has got enough dedicated video RAM.

On older machines and on machines with feable graphics cards, I would recommend not to use Unity, but to use a more lightweight desktop engine like e.g. Xfce.

Kind regards,
Karl

---

### Post by JRV on 2012-10-14
On my 2.4 GHz P4 LXDE is noticably faster than Unity2d.

I didn't do a complete re-install.
I just installed the LXDE session with the command:
```

sudo apt-get install lubuntu-desktop

```

---

### Post by Santaman on 2012-10-14
I'm using Xubuntu 12.04 on a P-4 2Ghz machine with and on-board Intel Extreme gfx card (845Gl) and 768 Mb RAM, I'm using a LCD screen at 1680x1050, just switch off all eye candy and it will run okay, some large programs a tad slow here and there but nothing too agravating.

Lubuntu indeed would be even more suitable and running faster than Xubuntu.

---

### Post by iGeekiHackiMatt on 2012-10-14
For that machine I would probably use Puppy linux or wary puppy linux for more speed

---

### Post by offgridguy on 2012-10-14
I use ubuntu 12.04, am satisfied with the speed, but this thread makes me wonder, what would be
considered normal or average on a laptop with 3 gb ram,  I haven't used any other linux system to
compare it with.  It is faster than windows 7, though not remarkably so.

---

### Post by PhilGil on 2012-10-14
> **offgridguy said:**
> I use ubuntu 12.04, am satisfied with the speed, but this thread makes me wonder, what would be
considered normal or average on a laptop with 3 gb ram,  I haven't used any other linux system to
compare it with.  It is faster than windows 7, though not remarkably so.

I think the benchmark is whether you're satisfied with the responsiveness of the system.

KDE (with effects), Gnome Shell and Unity are all going to be less responsive than lighter desktops such as LXDE or XFCE. On a machine with sufficient resources the difference will be small. On older or low-resource machines the difference will be very noticeable.

---

### Post by bootedguy on 2012-10-14
Lubuntu is an other option that requires little in graphics resources.

---

### Post by offgridguy on 2012-10-16
Thanks PhilGil.

---

