---
title: "Different problem with suspend"
date: 2008-10-04
forum: General Help
---

### Post by leeko on 2008-10-04
Hi all,

I'm having some problems with suspend (s3) and hibernate. My system is as follows:

Asus P5N-E SLI motherboard (nforce)
Intel E6300 core2duo
3Gb RAM
Kubuntu 8.04 (fully up-to-date) with kde 3.5
Kernel 2.6.24.19-generic
Nvidia 7300GS gfx card
ATI HDTV wonder

My problem is:

Whenever I try to suspend (using gui option in kde), the display shuts off, but The power light stays lit and all the fans are still running. I'm unable to resume by pressing the power button, so I have to force a power-off. 

When I try to hibernate, I get a black screen with a cursor blinking in the top left corner, but it just freezes there and I have to force a power-off. 

In the bios, "suspend" is currently set to "S3", but I've also tried "S1&S3". 

I've tried following various online guides, blacklisting agpgart and nvidia_agp, changing settings in acpi-support etc, but I think these are all solutions for the problem of not being able to wake up properly. My machine doesn't appear to complete the process of going to sleep! 

If anyone can help me, I'd be very grateful. I'm not sure what additional information to provide - just let me know! 

Thanks,

Lee

---

### Post by leeko on 2008-10-05
bump :)

---

### Post by Vertoxic on 2008-10-05
hey bud im having a simular problem, but mine will suspend, and when i try to ring it back up it comes back to me with a frozen screen!

---

### Post by leeko on 2008-10-05
Hi Vertoxic,

your issue may be different to mine - my machine doesn't get as far as completely suspending. 

I've had problems similar to yours before, and they were related to the nvidia driver for the graphics card. I'm not sure if the ATI driver has similar issues. 

Hoping someone here can point me in the right direction.

Cheers,

Lee

---

### Post by svivian on 2008-10-06
I'm also having a problem with suspend/hibernate - my computer won't wake up! Can you point me towards the guides you mentioned in your first post?

---

### Post by leeko on 2008-10-06
Google is your friend. 

There are several threads covering this problem, on this forum and others. If you can't find it using the forum search here, use google. 

I can't remember the web addresses without googling them myself, and I don't have your hardware specifics, so you are better off doing it yourself. 

Regards,

Lee

---

