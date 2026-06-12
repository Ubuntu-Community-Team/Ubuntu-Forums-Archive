---
title: "ATi Catalyst 9.6 is out"
date: 2009-06-15
forum: Hardware
---

### Post by Hund on 2009-06-15
Has anyone tried them yet?

**Release notes:** [https://a248.e.akamai.net/f/674/9206/0/www2.ati.com/drivers/linux/catalyst_96_linux.pdf](https://a248.e.akamai.net/f/674/9206/0/www2.ati.com/drivers/linux/catalyst_96_linux.pdf)
**Download:** [http://support.amd.com/us/gpudownload/Pages/index.aspx](http://support.amd.com/us/gpudownload/Pages/index.aspx)

There supose to be some issues for Ubuntu 9.04 fixed with the new driver. Would be nice if I could get back with 9.04 again.

---

### Post by dany74q on 2009-06-15
Once again ATI strikes,no support to 3870x2 gpu.
In the next couple of weeks I`m going to replace my 3870x2 to GTX285.
I guess Nvidia will give some more respect to her costumers.

---

### Post by oldrocker99 on 2009-06-15
As a Jaunty user with an ATI X1200 piece-o-cr@p (using the better-than-I-expected, but nowhere near as fast as the 9.03 drivers were under Intrepid open source ATI drivers), I will never, ever buy any product by ATI, and by extension, AMD again.

Ever.

:guitar:

---

### Post by ssri on 2009-06-15
Since Catalyst 9.4, AMD/ATI's release notes mention that _Mobility Radeon x2300_ chips are supported.  Has anyone managed to setup Catalyst 9.4+ on Jaunty using these chips on their laptops?  Thanks.

---

### Post by nolliecrooked on 2009-06-15
> **ssri said:**
> Since Catalyst 9.4, AMD/ATI's release notes mention that _Mobility Radeon x2300_ chips are supported.  Has anyone managed to setup Catalyst 9.4+ on Jaunty using these chips on their laptops?  Thanks.

last time I read, x2300s arent supported since 9.3.

---

### Post by ssri on 2009-06-15
> **nolliecrooked said:**
> last time I read, x2300s arent supported since 9.3.

Page 2 of the release notes (Catalyst 9.6, pdf in the first post) says otherwise.  It lists it (ATI Mobility Radeon x2300, M64-S) under supported chips.

---

### Post by shrndegruv on 2009-06-18
lspci reports

ATI Technologies Inc Radeon Mobility HD 3670

and i can't tell from the pdf if this card is included....can anyone clarify?

I see parts of what i posted above, for example Radeon HD 3600 series, without the mobility.  What does this mean?

---

### Post by doublemike on 2009-06-22
> **oldrocker99 said:**
> As a Jaunty user with an ATI X1200 piece-o-cr@p (using the better-than-I-expected, but nowhere near as fast as the 9.03 drivers were under Intrepid open source ATI drivers), I will never, ever buy any product by ATI, and by extension, AMD again.

Ever.

:guitar:

I've got the same piece of crap ATI X1200 and noticed a degradation my video quality when I upgraded from 8.10 to 9.4. The flicker is so bad at times that it is almost unwatchable. I'm fairly new to installing drivers, etc. What would you recommend from your experience? Do I need to go back and manually install the older drivers?

Thanks.

I guess I'll pay much more attention to the hardware I get on my next laptop. I've got ATI and Atheros on my Toshiba.

---

### Post by Th3_uN1Qu3 on 2009-06-22
> **shrndegruv said:**
> lspci reports

ATI Technologies Inc Radeon Mobility HD 3670

I see parts of what i posted above, for example Radeon HD 3600 series, without the mobility.  What does this mean?

I have the HD3470 in my laptop and it works, no reason not to work with yours.

> **oldrocker99 said:**
> As a Jaunty user with an ATI X1200 piece-o-cr@p (using the better-than-I-expected, but nowhere near as fast as the 9.03 drivers were under Intrepid open source ATI drivers), **I will never, ever buy any product by ATI, and by extension, AMD again.**

It is not my fault that you decided to buy one of the weakest cards ATi has made. Low cost = low performance. I can't afford the high end either, but i have always bought midrange cards which served me well. The only exception was when i bought a 8600GT, and had to swap it two times under warranty because the card's power circuitry blew. nVidia's low end isn't good either.

I currently have a HD3870 in my main computer running Vista, and a HD3470 in my new HP DV5 laptop running Ubuntu. They both work beautifully.

> **doublemike said:**
> I've got the same piece of crap ATI X1200 and noticed a degradation my video quality when I upgraded from 8.10 to 9.4. The flicker is so bad at times that it is almost unwatchable. I'm fairly new to installing drivers, etc. What would you recommend from your experience? Do I need to go back and manually install the older drivers?

Thanks.

I guess I'll pay much more attention to the hardware I get on my next laptop. I've got ATI and Atheros on my Toshiba.

Atheros wifi is the best, don't see why it bothers you. I have AMD, ATi and Atheros on my HP and it works well.

I recommend you to install the 9.6 drivers, i had flicker in most OpenGL games when running Compiz, now it's all gone. ;) Installation is easy, refer to [here](http://ubuntuforums.org/showpost.php?p=7496210&postcount=2).

---

### Post by doublemike on 2009-06-23
> **Th3_uN1Qu3 said:**
> I have the HD3470 in my laptop and it works, no reason not to work with yours.



It is not my fault that you decided to buy one of the weakest cards ATi has made. Low cost = low performance. I can't afford the high end either, but i have always bought midrange cards which served me well. The only exception was when i bought a 8600GT, and had to swap it two times under warranty because the card's power circuitry blew. nVidia's low end isn't good either.

I currently have a HD3870 in my main computer running Vista, and a HD3470 in my new HP DV5 laptop running Ubuntu. They both work beautifully.



Atheros wifi is the best, don't see why it bothers you. I have AMD, ATi and Atheros on my HP and it works well.

I recommend you to install the 9.6 drivers, i had flicker in most OpenGL games when running Compiz, now it's all gone. ;) Installation is easy, refer to [here]("http://ubuntuforums.org/showpost.php?p=7496210&postcount=2").

Atheros wifi works fine but was a bother to set up in 8.04. The install instructions are easy, but it doesn't look like there is a driver for the X1200 series.

---

### Post by shrndegruv on 2009-06-23
> **Th3_uN1Qu3 said:**
> I have the HD3470 in my laptop and it works, no reason not to work with yours.

you don't have any issues with maximizing/minimizing windows?

I was on the ATI irc forums and the dev there was pretty sure that the performance issue is an xserver issue.  I have seen forum posts around how to get a patched xserver instance installed.  Point being if it is an xserver issue, why would driver update resolve the issue?

---

### Post by @ntonius on 2009-06-23
I have seen some improvement for my HD 2400 in 9.04 with the new drivers (fewer flickering , catalyst works right away).
However a flickering at startup is still visible but stops when 9.04 is completely loaded.
it also appears for a few seconds when i open totem.


(p.s. for some strange reason the system speaker started to beeep after the installation of the drivers...lol....so i blacklisted it and i am ok now)

---

### Post by proxess on 2009-06-28
Anyone with the x2300 ventured to try this out, or do I have to do it?

Edit: Tried it, balls. Must be a typo or something. Damn them getting my hopes up. I tried with my old xorg.conf and a clean one, nothing. aticonfig doesn't recognize my GPU.

Edit again: Tried a bunch of ways, including removing the ati and radeonhd driver. In the end tho, it's apparent by the fact that aticonfig doesn't recognize the X2300 that it's just a typo or they're just mocking us. The GPU isn't even 2 years old...

---

### Post by csab on 2009-06-29
Still doesn't work for me. With HD 2600 Pro I am getting random freezes on sleep/wake up, and playing music or videos with Totem.

---

### Post by proxess on 2009-06-30
Try Using VLC for Video and Audacious for Audio. Sleep/Wake issues are everywhere so, you should check out your case.

---

### Post by csab on 2009-07-02
I'm (almost) content using mplayer for video and audacious for audio, but the sleep/wake up problem is killing me. I've spent days on it now, searched a lot, and nothing seems to work. See this thread about my latest experiment:

[http://ubuntuforums.org/showthread.php?t=1202621](http://ubuntuforums.org/showthread.php?t=1202621)

---

### Post by ilmorris on 2009-07-07
> Note: The ATI Radeon™ HD 3870 X2 series of product is currently 
not supported by the ATI Catalyst™ Linux software suite.

Still no reason for me to try the new release.  :(

---

### Post by zzarko on 2009-07-19
I tried 9.6, but in games it gives me same as the previous versions - it doesn't work for more than 5-20 minutes ([http://ubuntuforums.org/showthread.php?t=1207577](http://ubuntuforums.org/showthread.php?t=1207577))

---

### Post by learners permit on 2009-07-20
Man it pains me to see so much discontent for ATI driver support since they have put a lot of effort into them recently. Albeit quite late in the game as far as linux distros are concerned. Please be patient the last thing we need is an Nvidia monoply in the graphics card sector.

---

### Post by ssri on 2009-07-20
> **proxess said:**
> Anyone with the x2300 ventured to try this out, or do I have to do it?

Edit: Tried it, balls. Must be a typo or something. Damn them getting my hopes up. I tried with my old xorg.conf and a clean one, nothing. aticonfig doesn't recognize my GPU.

Edit again: Tried a bunch of ways, including removing the ati and radeonhd driver. In the end tho, it's apparent by the fact that aticonfig doesn't recognize the X2300 that it's just a typo or they're just mocking us. The GPU isn't even 2 years old...

I have the chip too and it pains me to say that it is not supported, even though it is on their supported list...  Read here:

[http://www.phoronix.com/forums/showthread.php?t=17736](http://www.phoronix.com/forums/showthread.php?t=17736)


This is the sole reason why I'm sticking with intrepid for now..

---

