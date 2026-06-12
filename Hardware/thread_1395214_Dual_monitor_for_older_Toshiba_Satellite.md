---
title: "Dual monitor for older Toshiba Satellite?"
date: 2010-01-31
forum: Hardware
---

### Post by mpemburn on 2010-01-31
Hi All,

After doing a bit of searching around and not finding anything that addresses this exactly, I'm hoping someone here can tell me whether this can be done.

Recently, I acquired an approx. five-year-old Toshiba Satellite P25-S5262 laptop.  After replacing a defective hard drive, I now have a great platform for my first real Ubuntu machine (though I've created several Ubuntu VM's on my Mac over the years).  My plan is to wean my wife off of Windoze but I want to give her a machine that can do everything she needs/wants it to do.  Among these is the ability to run dual monitors.

Today, I tried plugging the Toshiba into a monitor and the only way I was able to get it to work *at all* was to boot up with the monitor attached and that cause it to display on the external monitor only.  The fn+F5 key combination caused the monitor to blink for a second but changed nothing.  In order to get the display back to the LCD, I needed to reboot again.  Does anyone know if there's a tweak to make dual monitoring work?

Thanks in advance,

Mark

Details:
Ubuntu Studio 9.10 with "Super OS" installed
Toshiba Satellite P25-S5262 
P-4 3.0 GHz
512 MB RAM
160 GB HD
Phoenix BIOS 4.0 Release 6.0

---

### Post by jharder01 on 2010-01-31
I think if you click System -> Preferences -> Display you'll be given the option to set both monitors up.  You might need to click the "Detect Monitors" button if you plugged the monitor in after booting up.

Something to consider... I've always had issues with external monitors and my Eee PC with Ubuntu.  If I have an external plugged in, prior to shutting down I have to do the above steps to disable the external and re-enable the laptop monitor (if I'm going to leave and go mobile). If I don't, then the machine reboots with standard out to a monitor that is no longer there.  You might not have issues with this but in the event that you do, just play with the process involved with resetting monitors. 

Let us know what you find!

---

### Post by mpemburn on 2010-02-01
Thanks for your reply, jharder01.  

No, I've actually tried what you suggested and it shows that monitor as "Unknown" both with the LCD and the external monitor.  Clicking "Detect Monitors" does nothing.

With stuff like this, I really understand why Apple keeps complete controls over the hardware -- all variables can be known.  The range of hardware that Ubuntu must run on is staggering and it's a credit to the developers how well they accomplish this!

Mark

---

