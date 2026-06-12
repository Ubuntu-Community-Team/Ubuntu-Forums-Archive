---
title: "Installing to external HDD - booting problems"
date: 2009-03-16
forum: Installation &amp; Upgrades
---

### Post by Straakt on 2009-03-16
I did a quick search to see if anyone has had this issue... but sadly since I don't understand what is going on it makes it difficult to find similar cases.

For some background - I recently got rid of an old laptop. I took out the HDD and bought an external HDD case to put it in. It is a 2.5" drive, 7200RPM, 55GB, etc. So, not a flash drive. And I downloaded the latest version of Ubuntu, 8.10.

Using my desktop to do the install (and removing the internal HDD just in case) I tested my new external disk, cleared it off and created a Live CD. I then started the installation process. I managed to eek my way through that process via trial and error. I finally got the drive partitioned, formatted and finally completed installation. Then prompted to restart...

Here is where I get lost because I had no errors to indicate I did anything wrong. I removed the CD and modified my desktop BIOS to boot from USB-FDD first, CD second and disabled my third boot device option. After restarting... nothing happens.

Then I stumbled over an oddity - after resetting my boot device options back to normal (CD/DVD first, Internal HDD second, nothing third), leaving my external HDD connected and internal disconnected, then rebooting... I mistakenly hit the button to open my CD/DVD tray. I did this just as my desktop was about to begin the boot process and for some reason grub initialized from the external HDD. It booted no problem, but then when I restarted and didn't open the CD/DVD tray it did not boot back into ubuntu. I was instead informed that there was no system disk.

I was able to replicate the CD/DVD tray "trick" one or two more times just to confirm my own sanity. Also, I found that if I boot from the Live CD I am able to launch Ubuntu from my external HDD from that interface. I simply cannot boot into Ubuntu normally.

I also tried to boot from the external HDD on another PC after modified the boot device settings only to get the same results.

As I am new to Ubuntu and completely baffled I would appreciate any input. I thought it was an issue with the external HDD until I finally was able to boot normally, but only after I tied up my CD/DVD drive process.

Cheers

---

