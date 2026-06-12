---
title: "Hardware Drivers won't Activate"
date: 2009-05-12
forum: Hardware
---

### Post by Dragonbite on 2009-05-12
I have a Dell Latitude D400 I use with Ubuntu 8.04 and 9.04 and am trying out Kubuntu 9.04. It has a braodcomm wireless mini pci card which Ubuntu finds and downloads the necessary drivers for without any problems.

With Kubuntu 9.04, though, when I check the Hardware Drivers (jockey-kde) I see the Broadcomm wireless driver but clicking Activate does nothing.

The Activate button is green and accessible but fades when I click it and nothing is downloaded, or run.

Heck, if I know what command it would run, I would run it in a terminal, that's not an issue.
```
$ lspci
01:03.0 Network controller: Broadcom Corporation BCM4309 802.11a/b/g (rev 03)
```
```
$ lsmod | grep b43
b43                   131484  0
mac80211              217208  1 b43
led_class              12036  1 b43
input_polldev          11912  1 b43
ssb                    41220  1 b43

```

Or is it just the Network manager isn't showing me any of the wireless access points (my home's or the neighbors)?

I know it's on because I just took the hard drive with Ubuntu installed where I could see mine and the neighbor's access points and replaced it with the Kubuntu hard drive. Did not even have to move the laptop (both hard drives are in cradles so it's slide-out-slide-next-one-in easy!)

---

### Post by Jeffonfire on 2009-07-18
I am having the same issue.

---

### Post by Luke Carrier on 2009-07-24
Exactly the same problem here - the activate button is not greyed out as if it were disabled but does nothing when clicked. This is on a Dell Studio 1555 laptop...trying to install the ATi fglrx drivers for the onboard Mobility Radeon to fix the GPU temperature issue. Any ideas?

---

### Post by Sxeptomaniac on 2009-07-24
I don't know if this is the same issue or not, but I found that I was having trouble activating my FGLRX driver, until I first clicked on the driver in the upper box of the dialogue.  It was highlighted like it was already selected when the hardware drivers box opened, but I still had to click on the item, then click activate.  A weird design flaw, I guess.

---

### Post by Luke Carrier on 2009-07-24
Thanks for the advice, Sxeptomaniac, but I already tried that. I installed the driver by hand from the packages a few seconds ago and rebooted to find the X server entirely broken, after a couple of reboots and attempts to fix it I gave up and removed it via the root shell in recovery mode...I guess the solution to this problem won't really help me anyway.

But anyway, the bug is still present.

---

