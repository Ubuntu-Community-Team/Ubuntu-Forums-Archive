---
title: "NVIDA 3D  Stereo problems"
date: 2007-08-29
forum: Hardware &amp; Laptops
---

### Post by Neil_Wilson on 2007-08-29
Hi,

I have a nvidia quadro FX 1400 card and I have been trying to enable 3D stereo,  but I just can't seem to get it working.   I Have searched around various forums and it seems all i should have to do is add the following line into my xorf.conf. 

 Option         "Stereo" "4"

I have tried this (and tried different numbers) and I still can't get glxgears to work with the stereo option.  Has anyone got this working, and if so have they any hints or tips.

Thanks

Neil

---

### Post by anonymousnobody on 2008-02-06
I am in the same boat. I am trying to get stereo working with the nvidia quadro fx 3500. I am running Ubuntu 7.10. I have tried adding:
Option "Stereo" "3" 
to the Devices Section of the xorg.conf file. I have also tried 0 through 2. But none of those work. I am using the restricted driver that Ubuntu provides. I was thinking of installing the driver from nvidia's website, but I am afraid it'll screw up something.

I am bumping this message to see if anyone has had any luck with stereo on linux specifically Ubuntu. I know this video card supports 3D stereo because other people who have run Linux are able to get stereo working.

---

