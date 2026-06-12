---
title: "Karmic Koala, REALTEK RTL8101E/RTL8102E driver"
date: 2009-11-16
forum: Hardware
---

### Post by angellika on 2009-11-16
Hello,

My Wi-Fi card is not working with Karmic Koala. It was also not working with Jaunty. I have REALTEK RTL8101E/RTL8102E. I followed this thread but got stucked during instalation 

[http://ubuntuforums.org/showthread.php?t=1319785](http://ubuntuforums.org/showthread.php?t=1319785)


So I need some driver for my baby to work without cable.

Hope somebody will know how to do it,

Jaro

---

### Post by angellika on 2009-12-30
> **angellika said:**
> Hello,

My Wi-Fi card is not working with Karmic Koala. It was also not working with Jaunty. I have REALTEK RTL8101E/RTL8102E. I followed this thread but got stucked during instalation 

[http://ubuntuforums.org/showthread.php?t=1319785](http://ubuntuforums.org/showthread.php?t=1319785)


So I need some driver for my baby to work without cable.

Hope somebody will know how to do it,

Jaro

So As I found later after great communication with realtek  technical support RTL8101E/RTL8102E is wired card. I managed to install new driver that can be found here:

[http://www.realtek.com/downloads/downloadsView.aspx?Langid=1&PNid=7&PFid=7&Level=5&Conn=4&DownTypeID=3&GetDown=false#7](http://www.realtek.com/downloads/downloadsView.aspx?Langid=1&PNid=7&PFid=7&Level=5&Conn=4&DownTypeID=3&GetDown=false#7)

I manged to installed driver using these commands in terminal:

[I]sudo apt-get install build-essential linux-headers-`uname -r`
sudo -E make clean modules
sudo make install
sudo depmod -a[/I]

I blacklisted r8169 (sudo rmmod r8169) and loaded r8101 (sudo modprobe r8101). Here is very nice tutorial :

[http://en.alessiotreglia.com/articles/realteks-modules-new-version-has-been-released/#more-8/install](http://en.alessiotreglia.com/articles/realteks-modules-new-version-has-been-released/#more-8/install) Reatlek driver for Karmic

My wifi card is  RTL8192E WLAN. The driver can be downloaded from rapid (just 10 times), so write me if u will need it.

[http://rapidshare.com/files/327944041/rtl8192e_linux_2.6.0012.1210.2009.tar.gz.html](http://rapidshare.com/files/327944041/rtl8192e_linux_2.6.0012.1210.2009.tar.gz.html)

I installed it as follow (according to readme.txt):

        0. Change to Super User
	*sudo su*

	1. Build up the drivers from the source code
	*make*

	2. Install the driver to the kernel
        *make install*
          reboot

	3. bring up wlan if nic 
        *ifconfig wlan0 up* 

My thanks belongs to great Realtek technician support :h

---

