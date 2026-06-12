---
title: "Wireless ipw3945 hangs boot on laptop (solution)"
date: 2007-01-05
forum: Hardware &amp; Laptops
---

### Post by pjstadig on 2007-01-05
I didn't seem to have trouble with this until recently, but I may just have been lucky.

I was having trouble with my wireless card hanging my laptop on boot. I tried the Live CD, I tried the Alternate CD, and they both hung when trying to boot. I tried booting with my wireless card enabled, and with it disabled.

I gather what was happening was that when I had my wireless card enabled the boot process would keep on trying to connect the wireless card even though I had a bogus SSID (I was at work; not home). However, when I disabled my wireless card I got this error:

BUG!: soft lockup on CPU#0

See: [http://ubuntuforums.org/showthread.php?t=321923]("http://ubuntuforums.org/showthread.php?t=321923")

I went into my BIOS and disabled multicore, and disabled my wireless card, and it booted up right away. Then I went in to my /etc/network/interfaces and commented out the line that activated my wireless at boot:

# auto eth1

Then I went back into my BIOS and enabled multicore and enabled my wireless card, and I was able to boot again. Now I just need to find a way to be able to boot with my wireless card configured and not have it hang on me. I'll post a follow up if I figure something out.

---

### Post by SaJellish on 2008-01-14
Hello ,

   I too have the same problem. Can you please tell me what finally solved the issue for you. My installation was smooth but after the first reboot I have never been able to boot into Linux. It always stops by posting ipw3945 error sending LEDS_CMS. Hell I dont even want wireless to work default. My primary concern is to boot my Linux isntallation. 
   Any help will be deeply appreciated.
Thanks and Regards,
           SaJe

---

### Post by pjstadig on 2008-01-15
I have not had any problems with the same laptop with the latest versions of Ubuntu (I'm running Gutsy now). I've never experienced the error you're talking about, so I don't think I can be much help.

If you want to just get your computer to boot, then try following the instructions in my original post (going into BIOS, disabling multicore, etc.)

---

