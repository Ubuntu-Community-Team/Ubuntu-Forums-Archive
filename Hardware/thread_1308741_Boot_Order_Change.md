---
title: "Boot Order Change"
date: 2009-10-31
forum: Hardware
---

### Post by blackholeinacan on 2009-10-31
Hey, everyone!

My problem isn't actually in Linux, but most people here seem to be pretty knowledgeable about computers as well, so I figured I'd ask.

I run Windows on my main hard drive, but I installed Ubuntu 9.10 onto my external USB hard drive. I've tried GRUB in the past, but it messes up the Master Boot Record on my computer, so now I just want to figure out how to boot to Ubuntu without making it my primary boot device.   

I can enter the bios and change the boot order by moving my external HD ahead of my internal HD by expanding the +Hard Drive option using the enter key, and everything seems to work fine. However, when I press the escape key at the startup screen, I can see my boot options, and the hard drive is shown as "+Hard Drive", but hitting the enter key just selects whatever the top drive is (that I set in the BIOS options). Does anyone know how I can expand "+Hard Drive" so I can boot to my external without going into the BIOS, changing the boot order, and restarting?

I'm running a Compaq Presario R4000 with AMD64 Athlon 3800+. My bios is PhoenixBIOS.

Any help is appreciated.

Thanks,
Andy

---

### Post by cariboo on 2009-10-31
If you have grub installed on your external drive, set the boot order so that the external drive boots first, and boot from the Windows disk second.

Then when you want to boot into Windows, just unplug the external drive, when the bios can't find the first drive, it will  boot from the second.

---

### Post by blackholeinacan on 2009-11-01
I don't have GRUB installed anywhere right now. I've just been switching the boot order and going straight into Ubuntu or Windows. How do I install GRUB on the external hard drive? Can I do that in Ubuntu, or do I need to run the LiveCD again?

---

