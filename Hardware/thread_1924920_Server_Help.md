---
title: "Server Help"
date: 2012-02-13
forum: Hardware
---

### Post by marksc on 2012-02-13
Hi, I am new at this and I would like to build my first Multi-Purpose Server. It is to do operations within the network and over the internet like Cloud File Storage as well as Network File Server jobs, Web-site hosting, and various other tasks. I will be using the newest version of Ubuntu Server that will come out at the time I finish it. 

Now, here's the question. What parts should I use to make a ***_GOOD SERVER BUT USES AS LITTLE ENERGY AS POSSIBLE._***

---

### Post by LinuxFan999 on 2012-02-13
For a low power server, a good motherboard to use would be the Intel D525MW. It comes with an Intel atom D525 dual core processor clocked at 1.8 GHZ, which only uses 13 watts. It accepts DDR3 memory at 800 or 1066 MHZ.  If you want more processing power, get the AMD Athlon II 270, which is a dual core processor clocked at 3.4 GHZ and uses 25 watts. It should work in any socket AM3 motherboard.

Link for the Intel D525MW: [http://www.intel.com/content/www/us/en/motherboards/desktop-motherboards/desktop-board-d525mw.html](http://www.intel.com/content/www/us/en/motherboards/desktop-motherboards/desktop-board-d525mw.html)

Link for the AMD Athlon II 270: [http://shop.amd.com/us/All/Detail/Processor/ADX270OCGMBOX#Details](http://shop.amd.com/us/All/Detail/Processor/ADX270OCGMBOX#Details)

You should get 4 GB of RAM at most.

You don't need a dedicated video card for a server, so get a motherboard with integrated graphics (The D525MW includes this).

For the hard drive, get the Western digital Caviar Green, which consumes less power than the Caviar Blue or Caviar black.

Link for the Western Digital Caviar Green: [http://wdc.com/en/products/products.aspx?id=120](http://wdc.com/en/products/products.aspx?id=120)

Make sure to get an energy efficient power supply.

With these parts, you can make a server that is energy efficient and quiet.

---

### Post by ahallubuntu on 2012-02-13
Yeah, I have an older Atom-based server that's been running (FreeBSD!) since 2009 - uptime 3+ years.  It's an older Atom 1.6GHZ dual core/dual threaded.  My server does web and email only, not local file serving.  It has worked pretty well, but occasionally I wish it had more CPU power.  Next build will probably be an Intel i3 35w TDP.  (Sorry, I'm not an AMD fan.)

For lowest possible power, use an SSD and not a regular hard drive.  Next best is probably a 5400RPM laptop hard drive, at least for the OS - that's what I have my FreeBSD server runs on.  You can totally use a laptop hard drive in a desktop server - the SATA connectors are identical.  The big reason NOT to use a laptop drive is performance - if that's important, pay extra and buy an SSD.

You could also buy a large desktop hard drive for storage, perhaps a "green" one as mentioned above.  Ubuntu should be able to put it to sleep when not in use so it will use little power unless it's being accessed - and if your OS is on an SSD or laptop drive, the main drive will not consume much power, either.

For the energy-efficient power supply, look for models that are "80+ certified" which means they are more efficient than regular power supplies and consume less power themselves.

---

