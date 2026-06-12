---
title: "boot up problem (help!)"
date: 2008-10-11
forum: General Help
---

### Post by eggybob on 2008-10-11
Hi i am generally new to ubuntu but have used it a while back before but this time i am haveing trouble installing it with wubi and getting it to boot up. 

ok to start with i will give you a complete background (fyi). i firstly installed linux mint on my seperate hdd and got that to work fine from a cd i burnt, after trying to install the ati drivers i had the white screen problem so i formatted the seperate hdd with linux mint on and restored the MBR useing xp repair console. since this i have tryed to install linux mint again and got errors on boot which unfortunantly i dont have at hand but are not important atm, i am now trying to install ubuntu useing wubi and i get through the installation and get asked to reboot , at the dual boot menu i have ubuntu and vista there to pick from vista works fine but when i chose ubuntu i get a blank screen breifly and then the following message pops up for 2 to 3 secounds before returning me to the boot menu:-

Booting 'vista loader'
FAT 12 BPB found with 0xEB (jmp) leading the boot sector.
Probed C/H/S = 80/2/18, Probed total sectors =2880
Starting MS-DOS ...

so basically i am a little stuck as to what the problem may be i have tryed formatting the hdd that i installed ubunutu on a couple of time and no luck the same thing each time. and i have tryed a system restore to before i tryed installing linux mint the first time and no luck.. any suggestions or even a guide to sorting this problem out would be great any links to similar threads on this problem may help me also. sorry if this problem has been referred to and sorted in a thread elsewhere.

thanks for any advice in advance.

-james

---

### Post by Bryan_nayrB on 2008-10-11
Have you let the message stay? It says "starting MS_DOS" which means it is trying to load windows. It seems that your directory is mislocated, and you need to go to linux.com to figure out how to download the version of linux you are trying to install on a dual boot system. If not, when that message appears, press "Esc" (escape) which should give you the boot menu. It should load, then you will get a task box that asks if you want to load from
1.cd drive
2.floppy drive
3.hard drive

select the correct option, and mandriva (or whatever downloader you used) should load, then you will have the option to boot from regular of safe mode.

---

