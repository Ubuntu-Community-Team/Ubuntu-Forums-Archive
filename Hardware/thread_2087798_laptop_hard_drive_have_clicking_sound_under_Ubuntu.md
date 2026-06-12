---
title: "laptop hard drive have clicking sound under Ubuntu. But quiet under win7"
date: 2012-11-24
forum: Hardware
---

### Post by musicpiano on 2012-11-24
Hi, everyone :)

I have a new Western Digital WD Scorpio Black 750 GB SATA 3 GB/s 7200 RPM 16 MB Cache Internal Bulk/OEM 2.5-Inch Mobile Hard Drive. I install it to my new lenovo e530 to form a duel-boot system with windows 7. 

I use HDD-scan under win7 to check it, it has no bad sector.  there is no clicking sound under win7, it is very quiet  . 

When I use it under Ubuntu 12.10, it produce clicking sound around every 5min. Only one sound , then go to quiet again.  another problem is the NTFS partition will lost data if I edit it under ubuntu.

I think it is not the hardware problem since it is working great in windows 7. 

I have tried these methods as suggest on internet
(1) modify /etc/hdparm.conf
/dev/sda {
spindown_time = 0 
apm=254 
apm_battery=254
}

(2) add these commands into /etc/rc.local 
hdparm -S 0 /dev/sda
hdparm -B 255 /dev/sda


(3) run in the terminal 
sudo hdparm -S 0 /dev/sda
sudo hdparm -B 255 /dev/sda

But all the method fail, any help? 

Thanks  :P

---

### Post by ahallubuntu on 2012-11-24
This may be similar to what you have tried - but check it out:

[http://ubuntuforums.org/showthread.php?t=1922642](http://ubuntuforums.org/showthread.php?t=1922642)

---

### Post by musicpiano on 2012-11-24
> **ahallubuntu said:**
> This may be similar to what you have tried - but check it out:

[http://ubuntuforums.org/showthread.php?t=1922642](http://ubuntuforums.org/showthread.php?t=1922642)

Thanks, But that doesn't help. I have tried three different method:

(1) modify /etc/hdparm.conf
/dev/sda {
spindown_time = 0   
apm=254             			 
 apm_battery=254
}

(2)  add these commands into  /etc/rc.local 
hdparm -S 0  /dev/sda
hdparm -B 255 /dev/sda


(3) run  in the terminal 
sudo hdparm -S 0  /dev/sda
sudo hdparm -B 255 /dev/sda


All of these methods fail, actually, my hard drive click every 5 minute, very worrying , and prevent me from using ubuntu until I can solve this .

---

