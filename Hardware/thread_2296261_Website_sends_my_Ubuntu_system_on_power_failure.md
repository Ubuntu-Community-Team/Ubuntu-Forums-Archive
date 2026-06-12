---
title: "Website sends my Ubuntu system on power failure"
date: 2015-09-24
forum: Hardware
---

### Post by Claudio81 on 2015-09-24
I'm using Ubuntu 14.04 installed in a Dell Inspiron 1525.
 I was browsing with my life companion Firefox a multitude of broadband provider's websites, opening multiple tabs, comparing them for the best deal.
 These websites definitely don't care about your cpu performances, all they care about is the catchy look.
 The incident occurred when I had to open sky.com homepage.
 A few days earlier I actually visited that page and I was overwhelmed seeing the graphics in that page, really something never seen before. Massive images overlapping and moving one against the other when scrolling the page, giving the feeling of windows looking outwards.
 Going back to my story, I open sky homepage in a new tab, the page appears and keeps loading, a second later the screen is off/black, laptop is still on.
 I try then to blindly reach the terminal and "sudo shutdown -r now".
 I enter the root password, the pc definitely doesn't restart, but a few seconds later I hear the Ubuntu drum, as usually happens in the login screen.
 I then enter the password again, a few seconds and drum again.
 I enter the password again, and I could go on with this forever...
 Hold the power button and hard shutdown, restart the pc.
 I restart my broadband quest again, worrying about my pc health.
 I knew that a website cannot mess up with your system, especially in a safe browser like Firefox.
 After a while I decide to prove this to myself, I enter the feared webpage again and... same thing happens again.
 As described, the incident happened twice so far, since then I circumnavigated the problem just avoiding the cursed homepage.
 
 A possible explanation I came up with, is that the graphic card may be close to failure and that heavy webpage could be pointing it out.
 I'm not much familiar with log files, if you guys tell me where to look I'd be happy to report here.
 
 A few maybe useful notes:
 - Since an update of 1 or 2 weeks ago, Firefox keeps crushing very often.
 - A few minutes before the first "power failure" incident, the usb keyboard which I always use, plugged into a cheap usb hub, stopped working. I then plugged it directly in an usb port and everything was fine. This never happened before and now it's back in the usb hub with no further problems.
 
 Thanks in advance for your help.

---

### Post by TheFu on 2015-09-25
Swap the PSU or take it to a place to be tested.
Also, check the RAM - at boot, there is memtest. Run for 24hrs.
Also, check the look files for other failures - especially disk and disk controller issues. /var/log/* and in subdirs there. There might be a log viewer GUI tool - do'nt use it.

And reseat the GPU, check any extra power connections to it.

And blow out any dust inside the case which could be causing a short.

---

### Post by tgalati4 on 2015-09-25
Try turning off plug-ins in firefox or run in safe mode:

```
firefox -safe-mode
```

or 

```
firefox --debug
```

Also check your hard drive's SMART status.  A failing hard drive can cause firefox's cache to fail and strange browser behavior.  Install *google-chrome* and try the websites.  Note the differences in behavior.

Both browsers have experimental hardware acceleration that you can turn on and off.  Search the web for how to do that.  Understand that some graphics cards will lock up with some of these features enabled, so be prepared for some hard reboots.

---

### Post by Claudio81 on 2015-10-01
This is a multitude of great hints
Thankx guys
You definitely gave me a load of homework.
Sadly now I know that even Firefox can fail :( (who is perfect?)
Thanks again for your help
Claudio

---

### Post by dino99 on 2015-10-01
you said opening lot of tabs; but which graphic card/chipset is used ? how much video ram on it ?

---

### Post by Claudio81 on 2015-10-01
Hope this is what you are asking for:
```
  *-display:0             
       description: VGA compatible controller
       product: Mobile GM965/GL960 Integrated Graphics Controller (primary)
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 0c
       width: 64 bits
       clock: 33MHz
       capabilities: msi pm vga_controller bus_master cap_list rom
       configuration: driver=i915 latency=0
       resources: irq:45 memory:fea00000-feafffff memory:e0000000-efffffff ioport:eff8(size=8)
  *-display:1 UNCLAIMED
       description: Display controller
       product: Mobile GM965/GL960 Integrated Graphics Controller (secondary)
       vendor: Intel Corporation
       physical id: 2.1
       bus info: pci@0000:00:02.1
       version: 0c
       width: 64 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list
       configuration: latency=0
       resources: memory:feb00000-febfffff
```

---

### Post by tgalati4 on 2015-10-01
Try a new power brick.  If your USB keyboard is acting up, your 5 VDC may not be 5 VDC and that can cause lockup issues.

Shut the machine down completely.  Pull the battery out.  Plug in the power cord.  Boot without the battery.  See how long your system runs and if the graphics are stable.

---

