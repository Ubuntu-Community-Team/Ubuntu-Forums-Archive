---
title: "Copy V360 phonebook to K810i"
date: 2008-06-10
forum: Hardware
---

### Post by tboxmy on 2008-06-10
Having purchased an SE k810i, I needed to copy over the phonebook from the Motorola V360 phone. Here I list the steps taken using Ubuntu 7.10, and an updated detail can be found at tboxmy.blogspot.com

1. Install Kmobiletools.

2. In V360 choose;
Settings ->Connectivity ->Sync ->USB Settings ->Data/Fax Connection

3. In Linux, plugin the USB cable to phone and PC. Choose;

Applications ->Accessories ->KMobile Tools
Choose Phonebook ->All contacts from phone ->Refresh
(If there are many phone numbers, then have to wait longer)

Copy the phonebook from ~/.kde/share/apps/kmobiletools/kmobiletools.vcf to the PC.

4. In SE K810i, plug in the USB# In SE K810i
Unmount PHONE CARD media
Unplug the USB cable.
Select Phone mode
Choose Settings ->Contacts ->New Contact ->Options ->Advanced ->Restore from M.S.
# When prompted:
# Delete old contacts before new contacts are added?
Choose No

 cable and select Phone mode
Choose Settings ->Contacts ->Options ->Advanced ->Backup to M.S.

5. In Linux, copy the "/media/PHONE CARD/System/PIM/PB_Backup.vcf" to the PC.

# if there are same names in PB_Backup.vcf and kmobiletoos.vcf then remove them. Otherwise merge the two files. Of course if PB_Backup.vcf is blank then overwrite it with the kmobiletools.vcf file
#
# I take it that the phonebook in the phone is to be backed up and then renamed to PB_Backup.vcf.original

Edit the PB_Backup.vcf to contain all the phonebook entries from kmobiletoos.vcf

6. Copy PB_Backup.vcf to "/media/PHONE CARD/System/PIM".

7.In SE K810i, unmount PHONE CARD media and unplug the USB cable.
Select Phone mode
Choose Settings ->Contacts ->New Contact ->Options ->Advanced ->Restore from M.S.


And now I have the phonebook in my K810i. 

If you find this tip useful; I'd appreciate if you can point out how I can get the SMS/MMS copied to the K810i.

---

### Post by kumarkrishnan on 2008-06-11
Hi,
 Are u using it in Kubuntu or ubuntu? In thread topic it is mentioned as kubuntu, But, in thread, It is mentioned as Ubuntu7.10. 

  I got W810I and I tried to install kmobile tool (from source file i.e., .tar.gz file) in Ubuntu 8.04. But I got dependency problem and it asked "kde-config". I searched in net to get this package. But, I am not getting it. Since I dont have net connection at home, I have to download it from Net center and use it. Please let me know how you did and packages required?

With advanced Thanks,
KK

---

### Post by tboxmy on 2008-06-15
KK,

After installing Ubuntu 7.10, I connected to the Internet and installed all the KDE components. BTW, default was GNOME desktop. Command used was

sudo aptitude update && sudo aptitude install kubuntu-desktop

This installed the kde-config. Later I could remove KDE with the command

sudo aptitude remove kubuntu-desktop

But if you dont have access to the Internet to do an Aptitude install, then I suggest you look for the following packages:

kde-config is in package kdelibs4c2a
Other dependencies:
libacl1 (>= 2.2.11-1), libart-2.0-2 (>= 2.3.18), libarts1c2a (>= 1.5.0-1), libasound2 (>> 1.0.14), libaspell15 (>= 0.60), libattr1 (>= 2.4.4-1), libaudio2, libavahi-client3 (>= 0.6.13), libavahi-common3 (>= 0.6.10), libavahi-qt3-1 (>= 0.6.0), libbz2-1.0, libc6 (>= 2.6-1), libcomerr2 (>= 1.33-3), libcupsys2 (>= 1.3.0), libfontconfig1 (>= 2.4.0), libfreetype6 (>= 2.3.5), libgcc1 (>= 1:4.2.1), libgnutls13 (>= 1.6.3-0), libice6 (>= 1:1.0.0), libidn11 (>= 0.5.18), libjasper1 (>= 1.900.1), libjpeg62, libkrb53 (>= 1.6.dfsg.1), liblua50 (>= 5.0.3), liblualib50 (>= 5.0.3), libopenexr2c2a (>= 1.2.2), libpcre3 (>= 4.5), libpng12-0 (>= 1.2.13-4), libqt3-mt (>= 3:3.3.8really3.3.7), libsm6, libstdc++6 (>= 4.2.1), libtiff4, libx11-6, libxcursor1 (>> 1.1.2), libxext6, libxft2 (>> 2.1.1), libxi6, libxinerama1, libxml2 (>= 2.6.29), libxrandr2 (>= 2:1.2.0), libxrender1, libxslt1.1 (>= 1.1.20), libxt6, zlib1g (>= 1:1.2.3.3.dfsg-1), kdelibs-data (>> 4:3.5.8), kdelibs-data (<< 4:3.5.9), perl, xbase-clients, launchpad-integration, sudo

Well, its not a very detailed explanation but this gives you the idea of installing the kmobiletools  0.4.3.3-0ubuntu package. Let me know if it works out for you.

---

### Post by kumarkrishnan on 2008-06-16
Hi tboxmy,
  Thanks for your details. 
  Let me know, whether, most of the dependency packages are available in Ubuntu CD/DVD? Or I have to use Kubuntu CD. I have Kubuntu 7.10 CD. But, My present Ubuntu is 8.04(LTS).
  I will try and update you. If any, further help is required, I will post the reply in this thread.
Thanks,
KK

---

