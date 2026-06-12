---
title: "HPLIP Status Service, No System tray detected on this system, unable to start exiting"
date: 2011-09-13
forum: Hardware
---

### Post by Stephen Lilley on 2011-09-13
I just purchased HP Deskjet 1050 which is a combined scanner and printer. After reading some blogs on this printer I found that if I installed the latest hplip drivers (3.11.7.run) I should get the printer and scanner to work. After installing this driver, I found I would get the following error while booting up "HPLIP Status Service: No System tray detected on this system, unable to start exiting". 

Some additional information. If I reboot I get that error message. But then if I log out and in after booting up then I don't get this error message and the HP icon comes up in the panel and everything works fine. It seems that the HPLIP is too fast it is booted up before the panel is established and when that happens it gives this error report but when I log out and in the panel comes up first and then the HP icon appears on it and I don't get an error message. I saw something similar on a Ubuntu forum.

I would be very interested if someone knows how to stop this error message to appear when it first boots up and for the HP drivers to work as they should. I don't like the idea of logging out and then in to get it to work properly. Any Suggestions

I'm using Ubuntu 11.03 in the classic Ubuntu Desktop

By accident I found a solution. I installed Kubuntu and I saw while it was installing there was a settings for HPLIP. After I installed Kubuntu logged into KDE and out and then into Ubuntu I didn't get the problem any more.

---

