---
title: "xrandr --listproviders shows odd detail"
date: 2017-08-21
forum: Hardware
---

### Post by rdragonrydr on 2017-08-21
Hello.

When I run the above command, my new PC shows a modesetting provider and a nouveau provider. Attempts to run [COLOR=#2E1A05]xrandr --setprovideroutputsource nouveau Intel fail, since there is no Intel device. Replacing Intel with the ID 0 of the non-nvidia driver works, but attempts at running glmark2 with DRI_PRIME=1 have WORSE performance, likely due to the modesetting. However, the system info states that it is using the Intel card otherwise.

The computer is a Dell laptop with a Nvidia Mobile 960M and an Intel 530 embedded card.

Please advise.[/COLOR]

---

### Post by Yellow Pasque on 2017-08-22
modesetting = intel in this case: [https://www.phoronix.com/scan.php?page=news_item&px=Ubuntu-Debian-Abandon-Intel-DDX](https://www.phoronix.com/scan.php?page=news_item&px=Ubuntu-Debian-Abandon-Intel-DDX)

> Nvidia Mobile 960M

nouveau does not support reclocking that GPU (it's running at min clocks, even under load), so "worse" performance is not surprising
[https://www.phoronix.com/scan.php?page=news_item&px=Nouveau-Thermal-Throttling](https://www.phoronix.com/scan.php?page=news_item&px=Nouveau-Thermal-Throttling)

---

### Post by rdragonrydr on 2017-08-24
Ah, joy. I was hoping that something was simply not yet set up correctly. 

Good to know those facts. I am sorry that I did not already know this, since it seems to be answered already, but those were never things I thought to look at.

I assume that the modesetting driver works fine then? I had been confusing it with framebuffer; that's part of the reason for this post.


Do you know if the discrete AMD cards in laptops work any better, esp. with the radeon or the open version of the AMDgpu driver? How do those implement GPU switching?

---

### Post by Yellow Pasque on 2017-08-26
> I assume that the modesetting driver works fine then?
It should in theory. As long as you're not seeing screen corruption or experiencing slow 2D operations (like lag when moving windows), you should be good to go.

> Do you know if the discrete AMD cards in laptops work any better, esp. with the radeon or the open version of the AMDgpu driver? How do those implement GPU switching?

If you're asking me directly, I don't have personal experience with hybrid graphics laptops.

---

