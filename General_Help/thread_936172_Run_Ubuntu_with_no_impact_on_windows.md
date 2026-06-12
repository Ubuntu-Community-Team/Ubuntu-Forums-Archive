---
title: "Run Ubuntu with no impact on windows"
date: 2008-10-02
forum: General Help
---

### Post by bellmarbob on 2008-10-02
Run Ubuntu without impacting windows
This is for anyone else that may want to try Ubuntu but is apprehensive about impacting their current windows sytem
I am new to Ubuntu but found a very easy way to install Ubuntu rather than running it thru Windows. My first concern was I did not want to partition my windows drive and load Ubuntu on that because then a hard drive failure would take both systems down and any problems I had with the Ubuntu install might impact my windows system. That is something you have to be very careful of when installing Ubuntu. I had a USB hard drive (you can buy one for $50) which I dedicated solely to Ubuntu. Before starting any of this you should also download and make a GRUB repair disk like system rescue CD. This is in case the Grub boot loader becomes corrupted during the install process.  The exact process I used was as follows:
 1. I set my boot sequence to boot from a CDROM followed by boot from the USB connection. My On-board hard drive (the one with windows)is the 3rd boot option
 2. I disconnected my hard drives in the PC that had windows on them. This is easily done by opening the case and pulling the power connection to the windows hard drives. Do this with the power OFF
 3. I then loaded the Ubuntu CDROM in and turned the PC on
 4. From this point just follow the instructions as they come up on the screen. 
 5. This fully installs Ubuntu on the USB hard drive.
 6. Boot the system up and see if it boots into Ubuntu. If it does skip step 7
 7. Use the system rescue disk to correct any boot problems you may have in booting into Ubuntu. 
 8. Shut system down and reconnect the windows drives  

some additional comments
  The result of this is that both windows and Ubuntu are totally independent of one another. Since both the windows MBR and Ubuntu's Grub want to load their system first, each will change the other's boot configuration if you do not disconnect the windows hard drives. Once installed though that is not an issue. To run Ubuntu you simply turn the USB hard drive on before turning your PC on. If you want to run windows just make sure your USB hard drive is turned off before you start the PC. My PC is a DELL with XP and an Intel processor. I do not know if there would be problems with an AMD processor although I do not think so 
 Bob

---

### Post by whizbaby on 2008-10-02
Good idea, but if you have a faster machine you could give virtualbox a try
[http://www.virtualbox.org/wiki/Downloads](http://www.virtualbox.org/wiki/Downloads)
If your purpose is to just test an os it is real easy to use and install. You can run Ubuntu in a virtual machine that runs on windows.
But for the long run or for production systems your way is the one to go.

---

### Post by LowSky on 2008-10-02
[quote=**bellmarbob**] Since both the windows MBR and Ubuntu's Grub want to load their system first, each will change the other's boot configuration if you do not disconnect the windows hard drives. [/quote] **Completely not true** HAs never happened to me while using two seperate drives with two seperate Operating systems

Other things to consider

1.use an extra internal hard drive (faster and cheaper than usb hard drives)
2. set up bios to boot Ubuntu drive first, this way the Windows Drive's MBR isn't touched and will still operate fine if the Ubuntu drive fails.
3. Ubuntu Drive's Grub menu will have an option for booting to the Windows drive, no fuss, no mess, and disconnecting windows drives.
4. If Ubuntu drive goes bad unplug and BIOS will auto pick the Windows drive to boot from. And it will boot, mine does!
5. Use a Super Grub disk or Ubuntu LiveCD only in the failure of the Ubuntu Grub menu

---

