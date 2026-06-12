---
title: "Ubuntu-eee 8.04.1 to Xubuntu-only?"
date: 2008-10-06
forum: Hardware
---

### Post by Inane_Asylum on 2008-10-06
I'm trying to find a suitable OS for my wife's Asus eee 900, so obviously the default Xandros is out 

I tried both the 8.04 and 8.04.1 distros, and it was running a little sluggish. Other distros such as gOS didn't really work well at all with the hardware, so I decided the best thing is to grab a kernel specifically made for this computer...namely, Adam's Ubuntu-eee kernel.

My question is, how would I go about changing the window manager to XFCE and (preferably) removing GNOME?

---

### Post by roger_1960 on 2008-10-06
Hi

Have a look at [http://forum.eeeuser.com/](http://forum.eeeuser.com/)

---

### Post by michaelkahl on 2008-10-15
I just did

```
sudo apt-get install xfce4
```

Look under synaptic package manager, xfce4 is listed, and there are also a few other packages, listed under xfce4, that you can choose at your own discretion.
Good luck and let us know if you need more assistance.

---

### Post by Inane_Asylum on 2008-10-15
Thanks.  I got it all set up, but still not happy with the performance.  Only having Firefox open running XFCE sustains my CPU load at 50-60%, with **regular** spikes to 100%.

I guess my options are limited with OS choice on this little thing.  Now I'm looking at trying to turn off simple interface with Xandros, or possibly *shudder* Puppy Linux.

I just need something with a fair amount of simple games (tetravex, at the very least), that I can install a MUD client on, and that has basic Office software, that runs at least **fairly** smoothly.

---

### Post by michaelkahl on 2008-10-15
You may be experiencing cpu throttling if you are running on battery.  I know my CPU seems to clock down to 112MHz according to /proc/cpuinfo.

```
cat /proc/cpuinfo
```

If your cpu is slowing down try this.

```
sudo cpufreq-selector -g performance
```

This should hold cpu performance at 900MHz.  Also remember that this is basically a celeron 900, I ran an 800MHz Athlon just 8+ years ago.  This definitely isn't your top of the line Core 2 Quad or Phenom.  I guess everyone has a difference in how they want their desktop to respond, but for me it feels very snappy.  
You can try Arch Linux.  It's harder to setup, but I've heard good things about it.  Also Debian is supposed to have a decent distro that is known to be quick.

---

### Post by Inane_Asylum on 2008-10-15
I get
```
sudo: cpufreq-selector: command not found
```
back

---

### Post by michaelkahl on 2008-10-16
Hmm, maybe that was a package I installed while tinkering.  I'll have to investigate.

---

### Post by michaelkahl on 2008-10-16
> **Inane_Asylum said:**
> I get
```
sudo: cpufreq-selector: command not found
```
back

Are you trying to issue the command with the colons?  copy and paste this.

```
sudo cpufreq-selector -g performance
```

---

