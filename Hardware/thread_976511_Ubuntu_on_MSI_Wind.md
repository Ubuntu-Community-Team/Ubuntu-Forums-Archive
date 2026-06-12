---
title: "Ubuntu on MSI Wind"
date: 2008-11-09
forum: Hardware
---

### Post by NoobToast on 2008-11-09
Im looking at buying a [MSI Wind]("http://www.newegg.com/Product/Product.aspx?Item=N82E16834152074"), i wanna whip out the hard drive and put ubuntu on it, i have the previous version of ubuntu not the new one. Im wondering will i lose any functionality of the laptop if i do that, like will i lose support of the wireless card, bluetooth, etc....


thanks
toast

---

### Post by Saghaulor on 2009-01-02
Apparently there is an issue with the touchpad driver. Unfortunately, I do not know if it is resolved.

See these threads for more info.

[http://ubuntuforums.org/showthread.php?t=961324&highlight=msi+wind](http://ubuntuforums.org/showthread.php?t=961324&highlight=msi+wind)

[http://ubuntuforums.org/showthread.php?t=977046&highlight=msi+wind](http://ubuntuforums.org/showthread.php?t=977046&highlight=msi+wind)

---

### Post by Gadgetech on 2009-01-02
I just got a Wind for Christmas and have Hardy running on it dual booting with XP.  I initially got the wireless (RT2860) working with ndiswrapper, but today I succeeded with compiling the drivers from [Ralink's source package]("http://www.ralinktech.com/ralink/Home/Support/Linux.html").  Bluetooth works fine. Webcam works with Cheese, but I haven't had any luck capturing sound with the built-in microphone yet.

---

### Post by GhettoYhetti on 2009-01-03
I came across this on forums.msiwind.net while getting my wireless working on a u100-432US w/160GB.  I was able to get this working even running Live-CD using sudo insmod rt2860sta (again this was complements of Bingo).  The persons name is Bingo . . . . 

=====================================================

Just spend the last 5 hours playing with the wireless b/g/n adapter on my new wind (160GB U100-436NE)

I think i got it all working now 

Get these packages , compiler & linux-kernel headers for the curent running version
**Code:**
 sudo apt-get install build-essential linux-headers-`uname -r`
 

Get the RT-2700E source (included in the 2860 driver)
**Code:**
 wget [http://www.ralinktech.com.tw/data/drivers/2008_0918_RT2860_Linux_STA_v1.8.0.0.tar.bz2](http://www.ralinktech.com.tw/data/drivers/2008_0918_RT2860_Linux_STA_v1.8.0.0.tar.bz2)
 

Extract the source
**Code:**
 tar xvjf 2008_0918_RT2860_Linux_STA_v1.8.0.0.tar.bz2
 

"cd" to source dir (now called SRC)
**Code:**
 cd 2008_0918_RT2860_Linux_STA_v1.8.0.0
 

You have to change 2 parameters in the subdir file os/linux/config.mk 

**Code:**
 gedit os/linux/config.mk 
 

This will enable WPA , and use Ubuntu's native supplicant.

This is the original contents
**Code:**
 # Support Wpa_Supplicant
HAS_WPA_SUPPLICANT=n

# Support Native WpaSupplicant for Network Maganger
HAS_NATIVE_WPA_SUPPLICANT_SUPPORT=n

 

This is the changed contents
**Code:**
 # Support Wpa_Supplicant
HAS_WPA_SUPPLICANT=y

# Support Native WpaSupplicant for Network Maganger
HAS_NATIVE_WPA_SUPPLICANT_SUPPORT=y

 

Save the new contents.
Now you are done , configuring.

do a : 
**Code:**
 sudo make 
 

Now the kernel 2.6.x driver called rt2860sta.ko , has been build , and is ready to be installed.

do a : 
**Code:**
 sudo cp os/linux/rt2860sta.ko /lib/modules/`uname -r`/kernel/drivers/net/wireless/
 

then 

**Code:**
 sudo depmod -a
sudo modprobe rt2860sta
 

Reboot , and the wireless is now known and handled bu the gnome Networkmanager.

Ohh keep the roaming on the interface , if you want to be able to select wireless lans , that are awailable "in the air".

I have experienced once or twice that i had to do a : ifdown ra0 and then a ifup ra0 . in order to get a dhcp address , after booting.

/Bingo
 

Last edited by [Bingo]("http://forums.msiwind.net/member4583/") on Thu Oct 30, 2008 1:16 pm, edited 5 times in total.

=====================================================

---

### Post by GhettoYhetti on 2009-01-03
I came across this on forums.msiwind.net while getting my wireless working on a u100-432US w/160GB.  I was able to get this working even running Live-CD using sudo insmod rt2860sta (again this was complements of Bingo).  The persons name is Bingo . . . . 

=====================================================

Just spend the last 5 hours playing with the wireless b/g/n adapter on my new wind (160GB U100-436NE)

I think i got it all working now 


Get these packages , compiler & linux-kernel headers for the curent running version
**Code:**
 sudo apt-get install build-essential linux-headers-`uname -r`
 

Get the RT-2700E source (included in the 2860 driver)
**Code:**
 wget [http://www.ralinktech.com.tw/data/drivers/2008_0918_RT2860_Linux_STA_v1.8.0.0.tar.bz2](http://www.ralinktech.com.tw/data/drivers/2008_0918_RT2860_Linux_STA_v1.8.0.0.tar.bz2)
 

Extract the source
**Code:**
 tar xvjf 2008_0918_RT2860_Linux_STA_v1.8.0.0.tar.bz2
 

"cd" to source dir (now called SRC)
**Code:**
 cd 2008_0918_RT2860_Linux_STA_v1.8.0.0
 

You have to change 2 parameters in the subdir file os/linux/config.mk 

**Code:**
 gedit os/linux/config.mk 
 

This will enable WPA , and use Ubuntu's native supplicant.

This is the original contents
**Code:**
 # Support Wpa_Supplicant
HAS_WPA_SUPPLICANT=n

# Support Native WpaSupplicant for Network Maganger
HAS_NATIVE_WPA_SUPPLICANT_SUPPORT=n

 

This is the changed contents
**Code:**
 # Support Wpa_Supplicant
HAS_WPA_SUPPLICANT=y

# Support Native WpaSupplicant for Network Maganger
HAS_NATIVE_WPA_SUPPLICANT_SUPPORT=y

 

Save the new contents.
Now you are done , configuring.

do a : 
**Code:**
 sudo make 
 

Now the kernel 2.6.x driver called rt2860sta.ko , has been build , and is ready to be installed.

do a : 
**Code:**
 sudo cp os/linux/rt2860sta.ko /lib/modules/`uname -r`/kernel/drivers/net/wireless/
 

then 

**Code:**
 sudo depmod -a
sudo modprobe rt2860sta
 

Reboot , and the wireless is now known and handled bu the gnome Networkmanager.

Ohh keep the roaming on the interface , if you want to be able to select wireless lans , that are awailable "in the air".

I have experienced once or twice that i had to do a : ifdown ra0 and then a ifup ra0 . in order to get a dhcp address , after booting.

/Bingo
 

Last edited by [Bingo]("http://forums.msiwind.net/member4583/") on Thu Oct 30, 2008 1:16 pm, edited 5 times in total.

=====================================================

---

