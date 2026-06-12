---
title: "&quot;Wake up&quot; USB device during boot"
date: 2009-03-24
forum: Installation &amp; Upgrades
---

### Post by kilian27 on 2009-03-24
Hi everyone!

I have an USB infrared (IR) receiver connected to my computer running Mythbuntu 8.10. The problem is that it does not "wake up" during system start and is therefore not automatically recognized by LIRC.
When I connect the receiver to my laptop running Ubuntu 8.04, what happens is the following: The receiver's power LED shows a short flickering during the BIOS messages, then turns off when GRUB starts and turns on about one second after the Ubuntu splash screen appears. Thus, the receiver is ON during system start.
On the Mythbuntu machine, it is the same that the receiver flickers while the BIOS messages are shown, turns off afterwards, but then does not turn on when Mythbuntu starts booting. What can I do to make Mythbuntu "wake up" the receiver? What happens on the Ubuntu laptop that the receiver gets activated?

Thanks in advance!
Kilian

---

### Post by miegiel on 2009-03-24
Does it work if you plug it into the mythbuntu machine when it's already booted up? And what have you tried so far to fix or find the problem?

---

### Post by kilian27 on 2009-03-25
> **miegiel said:**
> Does it work if you plug it into the mythbuntu machine when it's already booted up?

Yes, then it works without problems. I can even activate the receiver by pressing a button on the remote, but then only its power LED lights up. To have it recognized by the system, I need to call "lsusb", then it's available and working after about 1 second.

When I activate the receiver by pressing a button on the remote at the beginning of the system start (shortly after GRUB), then also everything works without problems. So it just needs to be ON during boot.

I tried some workarounds e.g. with a udev rule, but this did not really solve the problem. Then I found that the receiver works as expected on my laptop. This led me to the assumption that there must be some daemon or whatever which "sends a ping" to every USB device during system start.
I didn't find anything with google, but perhaps I just searched for the wrong term. So any hint to point me in the right direction would be appreciated!

---

### Post by miegiel on 2009-03-25
I'm guessing it's a kernel / modules thing too, I don't know much of that stuff yet :)

It could be a power thing. But usually, if it's power related, it sometimes works / sometimes doesn't. If you think it might be a power issue and you have a lot of usb devices connected, you could try booting after disconnecting all of them except for the IR receiver. You could also check if the +5VSB (or something like that) line of your power-supply meets the requirements of your motherboard. IIRC the +5VSB line provides power to the usb ports.

You haven't overclocked your media-center have you?

---

