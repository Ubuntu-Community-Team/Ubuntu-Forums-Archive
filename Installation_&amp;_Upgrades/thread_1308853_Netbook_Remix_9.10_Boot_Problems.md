---
title: "Netbook Remix 9.10 Boot Problems"
date: 2009-10-31
forum: Installation &amp; Upgrades
---

### Post by mluntz on 2009-10-31
I have done some searching for this problem but have not found anything exactly like it.

On my WinXP machine I downloaded the ISO and burned a Live CD and then using the usb-creator executable that is on the CD I copied the disk to a new usb stick. But I have not been able to use the stick to boot with my Acer Aspire One 150, nor have I been able to use the live CD to boot from my desktop.

Both the CD and the usb stick pass the media test and the ISO has the correct MD5Sum. When the boot starts I get the menu of options and then, after selecting “Try Ubuntu without changing my system”, I get a white Ubuntu logo on a black screen and then the screen goes dark. There does not seem to be any activity on the usb stick for about 1.5 minutes, then there is a short burst of activity and then nothing until I finally turned off the power, having waited about 5-8 minutes. Booting the desktop from the CD results in a similar situation. 

I have also written the usb stick directly from the ISO using unetbootin with the same results as earlier on the netbook.

Does anyone have a solution for this problem?

---

### Post by mluntz on 2009-11-01
With some further research I found that booting with i915.modeset=0 at least changes the response. But now I eventually get bumped to an [initramfs] prompt. I have no idea what to do at that point. Any suggestions on what to try?

---

### Post by mluntz on 2009-11-01
Problem solved. Even though the md5sum checked and I tried two different types of writes of the usb stick using my windows machine I could not get the remix to boot to a desktop. I eventually downloaded the ISO again, this time to a laptop running Jaunty and wrote the stick with the Jaunty usb-creator application. This combination of operations worked.

Anyone having trouble getting a stick written using Windows to boot may want to try using Jaunty.

---

