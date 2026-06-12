---
title: "Instant Resume after Suspend"
date: 2009-09-15
forum: Hardware
---

### Post by l2e on 2009-09-15
I am running XBMC on top of a minimal Jaunty installation on a Zotac ION rev 2 board that supports Suspend properly. Anyway, my problem is using my MCE remote I can press the power button on the remote (within XBMC) and the system immediately suspends. Once suspended I press the power button on the remote and it resumes from suspend perfectly. Now here is where it goes haywire. If I press the power button on the remote again, it goes into suspend but then immediately resumes from suspend. It will do this until I reboot and after a reboot it will suspend properly once and then instant resume all other attempts.
 
I did mucho searching and found a post that said to put:
 
usbcore.autosuspend=-1 
 
as a boot parameter in grub. I did that but it gave me different problems. When I press the power button on the remote, the system suspends properly. However, when I press the power button on the remote ito resume the system it turns on for about 5 seconds (Power LED is lit) but then turns off. If I press the power button on the case it resumes properly.
 
This shouldn't be this difficult. Any suggestions?

---

