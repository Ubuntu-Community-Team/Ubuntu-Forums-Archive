---
title: "Flash memory vs SSD"
date: 2012-12-04
forum: Hardware
---

### Post by benbrockn on 2012-12-04
So I wanted to do a full install of Ubuntu 12.04 LTS on a flash drive (instead of the Live USB) so that I can have  Ubuntu with me and plug it in whenever I want to run it. But also, I am  tinkering with it because I would like to one day switch away from  Windows. 

But I read that flash memory has limited read/writes before the flash drive dies. I know that SSD uses flash memory, but wouldn't SSD also have limited read/writes as well?

I know that if I truly wanted a USB drive that would last, it cost a lot and I would have to look for one with SWL (Static Wear Leveling) and SLC (Single Level Cell) based memory. I'm not even sure these exist...

Anyway, I'm rambling... How can a flash drive be limited in this way and a SSD not? Just curious.

---

### Post by haqking on 2012-12-04
> **benbrockn said:**
> So I wanted to do a full install of Ubuntu 12.04 LTS on a flash drive (instead of the Live USB) so that I can have  Ubuntu with me and plug it in whenever I want to run it. But also, I am  tinkering with it because I would like to one day switch away from  Windows. 

But I read that flash memory has limited read/writes before the flash drive dies. I know that SSD uses flash memory, but wouldn't SSD also have limited read/writes as well?

I know that if I truly wanted a USB drive that would last, it cost a lot and I would have to look for one with SWL (Static Wear Leveling) and SLC (Single Level Cell) based memory. I'm not even sure these exist...

Anyway, I'm rambling... How can a flash drive be limited in this way and a SSD not? Just curious.

They say the same thing about SSD, personally I have never had issues with any USB/Flash or SSD.  I have had USB drives for years which have been in washing machine and still work.

SSD is open to conjecture as they havent been around long enough for any true stats on there life.

There are settings to optimise them and extend life such as flags in /etc/fstab to reduce writes, putting /tmp into RAM etc etc.

Personally i think it is hyperbole

---

### Post by oldfred on 2012-12-04
+ on        haqking comments.

I think the SSD and flash use different designs now, but unless you do an awful lot of writes it should not be an issue.

You can change settings on flash drive similar to SSD to reduce writes and if you have a newer system with lots of RAM, most activity will be in RAM.

       Pros & cons of persistent install over direct install to flashdrives - C.S.Cameron
[http://ubuntuforums.org/showthread.php?t=1655412](http://ubuntuforums.org/showthread.php?t=1655412)

       Full install of 12.04 to USB device C.S.Cameron post #5
[http://ubuntuforums.org/showthread.php?t=2060493](http://ubuntuforums.org/showthread.php?t=2060493)

       Ubuntu Encrypted Flash Memory Installation using alternative text based installer, if you do not want encryption you just use standard Desktop installer. 
Standard full install with screenshots to flash or SSD:
Ubuntu Encrypted Flash Memory Installation using alternative text based installer
[http://members.iinet.net/~herman546/p19.html](http://members.iinet.net/~herman546/p19.html)

With SSD or Flash drives, Use ext4 without journal:
sudo tune2fs -O ^has_journal /dev/sda1
sudo tune2fs -o discard /dev/sda1
No swap or set swapiness or install 'Dynamic Swap Space Manager' from the Ubuntu Software Center
After installing, change the fstab so that everything gets mounted with noatime.

---

