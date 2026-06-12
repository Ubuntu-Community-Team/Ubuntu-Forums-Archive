---
title: "Keeps freezing on boot Ubuntu 20.04LTS"
date: 2020-10-27
forum: Hardware
---

### Post by bob101plod on 2020-10-27
Hi

I 'upgraded' from version 18.04LTS to 20.04LTS but since doing so my PC is taking ages to boot to the login screen (on average 4-5 minutes). Sometimes I get the Ubuntu spinning wheel but then that disappears and the PC simply freezes requiring a hard restart (hold in the power button to turn off the PC and then restart). Sometimes I have to go through the restart process a couple of times before the PC finally boots through to the login screen.

My PC is a Lenovo AIO 300, 8Gb RAM, intel 2.10 Ghz x 4 processor.

I never had these problems with v 18.04.

Any ideas please?

---

### Post by david-daking on 2020-10-27
Could be a graphics card/driver issue?

---

### Post by bob101plod on 2020-10-28
> **david-daking said:**
> Could be a graphics card/driver issue?

Hi

I don't have any other problems with the graphics chip (all-in-one PC so built in chip on the motherboard - Mesa Intel® HD Graphics 510 (SKL GT1)) and it's not throwing up any errors on boot and all system updates are up-to-date.

Bob

---

### Post by Deep_Peasant on 2020-10-28
It's just my idea, upgrading to 20.04 gave me enough headache allready. I've upgraded a 18.04 LTS pc to 20.04 LTS by command line, that gave me the same long boot problems. After that I decided to uprade with a fresh install with a live usb, boot times where halved. Then I got initramfs errors at boot and systemd at shutdown, not even mentioning another slew of program troubles :( I tried to find answers on the net, found similar problems but no answers. Since 18.04 LTS is supported to april 2021 I would suggest to use it until then, there's not enough stable in 20.04. I'm reverting back to 18.04 myself over the weekend, sick of the silly ' workarounds'  of things that just worked fine and now are broken!

---

### Post by bob101plod on 2020-10-29
> **Deep_Peasant said:**
> It's just my idea, upgrading to 20.04 gave me enough headache allready. I've upgraded a 18.04 LTS pc to 20.04 LTS by command line, that gave me the same long boot problems. After that I decided to uprade with a fresh install with a live usb, boot times where halved. Then I got initramfs errors at boot and systemd at shutdown, not even mentioning another slew of program troubles :( I tried to find answers on the net, found similar problems but no answers. Since 18.04 LTS is supported to april 2021 I would suggest to use it until then, there's not enough stable in 20.04. I'm reverting back to 18.04 myself over the weekend, sick of the silly ' workarounds'  of things that just worked fine and now are broken!

Hi

I think I'm going to give Groovy Gorilla a go. If that's no better then it will be back to 18.04 as well :(

---

### Post by Deep_Peasant on 2020-10-29
> **bob101plod said:**
> Hi

I think I'm going to give Groovy Gorilla a go. If that's no better then it will be back to 18.04 as well :(

You can always try different versions. Remember that Groovy Gorilla will also last you only 6 months till the next version. 
Let us know how it went. :)

---

