---
title: "Intrepid 8.10 RC acer aspire one wireless and other trouble"
date: 2008-10-29
forum: Hardware
---

### Post by arglborps on 2008-10-29
Using [[COLOR="Red"]these excellent directions[/COLOR]]("https://help.ubuntu.com/community/AspireOne") to set up Ubuntu on an Acer aspire one, I was able to get have a fully working machine after a few hours with hardy heron (8.04.1).

Once I heard Intrepid has support in the kernel for the aspire one's wireless card, I jumped ship and installed the then beta for 8.10. After disabling a few uneccessary drivers everything worked just fine.

However, ever since the release candidate I have the problem that wireless is working sometimes and when it does it's flawless, but every other reboot or even when waking the machine from sleep sometimes wireless completely stops working (i.e. no networks show up in the panel for wireless, even using the hardware switch on the front won't help). When this happens the only thing to get it working again is simply shutting the machine down, pulling the power plug, removing the battery for a few minutes and then booting up again.

I'm getting the feeling that the current (ath5k) drivers for some reason might leave the wireless hardware in an unstable state when sleeping or rebooting. Anyone else having similar trouble with wireless on the aspire one on Intrepid RC?

Another Issue I found is that the power button of the aspire one ever since RC sometimes ceases to work (it always works for powering the machine up, though), so hitting it when the machine is running sometimes brings up the panel to choose whether to reboot etc., but sometimes nothing happens at all.

If you have any ideas what could cause the wireless instability and the button weirdness I'd be very happy about any comments.

---

### Post by kesman on 2008-11-01
EDIT: So I found a solution that works for me. There are just a couple of steps to make wireless work on my pc.
1. Make sure **acer_wmi** module is loaded. To do this, run
```

lsmod | more

```
and scroll trough it to find it. If it isn't there, then you will need to modprobe it:
```

sudo modprobe acer_wmi

```
after this, you have to enable the hardware radio button with
```

sudo echo 1 > /sys/devices/platform/acer_wmi/wireless

```
and you should be clear to go!
just add that line to /etc/rc.local BEFORE the exit 0 -line and it will be ran on every boot. This worked for me, hope it works for you too.


It's weird, my ancient Aspire 5020 seems to be suffering from this too. I've got 8.10 installed and it worked perfectly yesterday, but now as I boot the pc up, nothing. Before, with 8.04.1 I was able to do:
```

sudo echo 1 > /proc/acpi/acer/wireless

```
to enable the wireless (the button has never worked for me), but now there isn't such a directory. With dmesg I get only this:
```

[  384.108061] b43-phy0: Radio hardware status changed to DISABLED
[  384.192063] b43-phy0: Radio turned on by software
[  384.192081] b43-phy0: The hardware RF-kill button still turns the radio physically off. Press the button to turn it on.

```
whichs indicates a problem with the button of some kind. I'll be searching for a solution, I bet there is at least one, and when I found one, I'll be posting here.

See ya around!

---

### Post by teaker1s on 2008-11-01
there is quite an active aspireone intrepid thread also worth a look

---

