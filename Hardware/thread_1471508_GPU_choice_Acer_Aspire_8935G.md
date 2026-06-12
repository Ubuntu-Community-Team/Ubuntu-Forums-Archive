---
title: "GPU choice Acer Aspire 8935G"
date: 2010-05-03
forum: Hardware
---

### Post by mrkazoodle on 2010-05-03
Hi

On my laptop I've got 2 GPU's a ATI HD 4670 (which Ubuntu does use) and a energy saving onboard GPU from Intel. When I press the button to switch to the Intel one, nothin happens.
What should I do to be able to use the Intel one?

I'm using Ubuntu 10.04

---

### Post by senycorp on 2010-07-02
Hi,

i have the same laptop as you and the same ubuntu version 32-Bit.
The GPU-switching is unavailable and acer don't offer  linux driver. So i think there is no possibility. I don't search for a linux-chipset Driver but i think the chipset switchs the  GPU.

I have a question too.
The first time after installing Ubuntu i havent any Problems. After a while  Ubuntu suggests me an ATI-Driver which i installed. And now if i select Ubuntu in BootMenu i get a black screen and the cpu-led doesn't  pulsing. Have you installed an ATI Driver too and any Problems by booting Ubuntu???

---

### Post by avilella on 2010-07-03
There is now a kernel module called acpi_call that will let you call ACPI methods on a running Linux session to switch on/off the discrete graphics card. For more information check the header info here:

[http://linux-hybrid-graphics.blogspot.com/](http://linux-hybrid-graphics.blogspot.com/)

---

### Post by Prometheus_IX on 2010-09-07
> **senycorp said:**
> Hi,
I have a question too.
The first time after installing Ubuntu i havent any Problems. After a while  Ubuntu suggests me an ATI-Driver which i installed. And now if i select Ubuntu in BootMenu i get a black screen and the cpu-led doesn't  pulsing. Have you installed an ATI Driver too and any Problems by booting Ubuntu???

I had exactly the same problem :-/ I think it's a clash with some upgrade that's happened since December as I used to run the ATI drive no problem (I work in computational biophysics so not having a decent GPU at my disposal is a massive plus)...

---

### Post by mondalaci on 2011-06-29
I'm also a (somewhat) happy owner of an Acer Aspire 8935G.

After buying this laptop it took 1 year (yes, that's one year!) to figure out how to use its ATI GPU with Linux instead of its low-performance integrated Intel GPU.

If I power on my laptop by pressing the upper left button of the right capacitive multimedia button block of the keyboard then Xorg is able to use the ATI GPU.  If I power on my laptop by pressing the standard power button then Xorg is only able to use the integrated Intel GPU.  If I reboot my laptop then the Intel GPU will be used so in order to use the ATI GPU I have to shut down my laptop and press the above mentioned capacitive button to start it up.  To my knowledge it's not possible to switch GPUs while Linux is running but I wouldn't even be interested in that.  I have a different problem...

Resume from suspend doesn't work for me.  This would be an essential feature for me because I really like to sleep in a quiet environment.  Currently when shutting down my laptop I cannot resume it.  I can hear the fan starting up but the screen stays blank.  I've debugged this problem a while ago and it seems that the graphics driver is the culprit.  When I was unaware of how to use the ATI GPU and used the Intel GPU resume worked fine, so I suspect that upon resuming the Intel GPU gets activated by default and the ATI driver gets screwed in such an environment.

I've recently bought an GeForce MXM card for about $250 and I still cannot resume, the same thing happens!  I wanna make resume happen so badly but I cannot seem to be able to do it.  Maybe my last resort is to buy another laptop with a single GPU.  This issue infuriates me beyond measure and makes me wanna explode with the power of a million Suns becuase setting up my (farily elaborate) session is the last thing I wanna do every morning!

Please let me know about your experiences with resume from suspend when the ATI GPU is used.

---

