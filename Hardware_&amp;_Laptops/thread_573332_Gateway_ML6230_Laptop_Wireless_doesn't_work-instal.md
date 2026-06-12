---
title: "Gateway ML6230 Laptop Wireless doesn't work-installed driver"
date: 2007-10-11
forum: Hardware &amp; Laptops
---

### Post by homexyz1 on 2007-10-11
Hi All,

Just installed U-7.04, on GW ML6230, and everything seems to work fine (sound, internet, etc...), except can not get the wireless LAN working.

Downloaded the Realtek driver for linux

[http://152.104.125.41/downloads/down...Downloads=true](http://152.104.125.41/downloads/down...Downloads=true)

unzip and Untar
made driver (./makedrv) WORKED

tried to launch  ./wlan0up (doesn't work)

The script is trying to do:

-------------------
cd ieee80211/
insmod **ieee80211_crypt-rtl.ko**
insmod** ieee80211_crypt_wep-rtl.ko**
insmod ieee80211_crypt_tkip-rtl.ko
insmod ieee80211_crypt_ccmp-rtl.ko
insmod ieee80211-rtl.ko

cd ../rtl8187/
insmod r8187.ko

cd ../

ifconfig wlan0 up

---------------------end script ------------------------------------

None of the above files are in ieee80211 dir.

content of my ieee80211 dir is as follows:


rwxr-xr-x 1 asic1 asic1 7699 2007-01-14 18:00 readme
-rwxr-xr-x 1 asic1 asic1 18671 2007-01-14 18:00 license
-rwxr-xr-x 1 asic1 asic1 14136 2007-01-14 18:00 ieee80211_wx.c
-rwxr-xr-x 1 asic1 asic1 12029 2007-01-14 18:00 ieee80211_softmac_wx.c
-rwxr-xr-x 1 asic1 asic1 39547 2007-01-14 18:00 ieee80211_rx.c
-rwxr-xr-x 1 asic1 asic1 6299 2007-01-14 18:00 ieee80211_crypt_wep.c
-rwxr-xr-x 1 asic1 asic1 18944 2007-01-14 18:00 ieee80211_crypt_tkip.c
-rwxr-xr-x 1 asic1 asic1 3107 2007-01-14 18:00 ieee80211_crypt.h
-rwxr-xr-x 1 asic1 asic1 11324 2007-01-14 18:00 ieee80211_crypt_ccmp.c
-rwxr-xr-x 1 asic1 asic1 6138 2007-01-14 18:00 ieee80211_crypt.c
-rwxr-xr-x 1 asic1 asic1 920 2007-02-09 00:01 Makefile
drwxr-xr-x 5 asic1 asic1 4096 2007-10-10 16:40 ..
drwxr-xr-x 2 asic1 asic1 4096 2007-10-10 16:40 .tmp_versions
-rw-r--r-- 1 asic1 asic1 0 2007-10-10 16:40 .ieee80211_softmac.o.d
drwxr-xr-x 3 asic1 asic1 4096 2007-10-10 16:40 .
-rw-r--r-- 1 asic1 asic1 79142 2007-12-03 01:06 tags
-rwxr-xr-x 1 asic1 asic1 7871 2007-12-03 01:07 ieee80211_module.c
-rwxr-xr-x 1 asic1 asic1 70485 2007-12-05 00:26 ieee80211_softmac.c
-rwxr-xr-x 1 asic1 asic1 44361 2007-12-05 00:27 ieee80211.h
-rwxr-xr-x 1 asic1 asic1 16406 2007-12-05 00:53 ieee80211_tx.c[/color][/b]


------------------------------------------end dir. content----------------

Please help,

Regards,
__________________

---

### Post by bubbahotep on 2007-10-11
Same problem here.  You are not alone.

This is my first use of linux and Ubuntu.

The wireless is my only major problem.  I tried loading the 7.10 beta, but no change.


Were you able to ge the resolution to 1280x800?

When I try to rip a cd with soundjuicer it reads at like 1x. 

Other than that, I think everything else seems to be working ok.

---

### Post by homexyz1 on 2007-10-11
Hi,

I haven't tried writing CD or change resolution.
I will try and let you know.
THe problem with Wireless LAN is with the download script.

Regards,

---

### Post by hakey on 2007-10-12
homexyz1:  could you please post the download link for realtek driver? you 1st post has a broken link.

I use 915resolution to change to 1280x800, works pretty well.

Same problem with wireless on my ML6230. I found this nic card :

0dba:8189 via lsusb.

I can enable wireless with ndiswrapper using the W98 driver, not the WinXP as many others uses in dell notebooks. The problem: it seems that enabling this particular wireless driver can randomly freeze my computer and crash my filesystem! After I completely uninstall ndiswrapper, filesystem appears to be stable but I was left with no wireless. Any ideas from you guys are extremely appreciated.

---

### Post by Traxs on 2007-10-12
> **hakey said:**
> homexyz1:  could you please post the download link for realtek driver? you 1st post has a broken link.

hakey,

Here is all the mirrors to the realtek driver

[ftp://210.51.181.211/cn/wlan/rtl8187_linux_26.1025.0328.2007.tar.gz](ftp://210.51.181.211/cn/wlan/rtl8187_linux_26.1025.0328.2007.tar.gz)

or

[ftp://202.65.194.212/cn/wlan/rtl8187_linux_26.1025.0328.2007.tar.gz](ftp://202.65.194.212/cn/wlan/rtl8187_linux_26.1025.0328.2007.tar.gz)

or

[ftp://61.56.69.18/cn/wlan/rtl8187_linux_26.1025.0328.2007.tar.gz](ftp://61.56.69.18/cn/wlan/rtl8187_linux_26.1025.0328.2007.tar.gz)

Im having the same issue :(

---

### Post by Traxs on 2007-10-12
I found a wiki on how to patch the kernel to get the rtl8187 wireless card working:

[http://wiki.archlinux.org/index.php/Rtl8187_wireless](http://wiki.archlinux.org/index.php/Rtl8187_wireless)

But im not able to get it to work

I can get all the way to:

```

modprobe rtl8187
dmesg | grep rtl8187

```

and i get 

usbcore: registered new interface driver rtl8187 

but then I try

```

ifconfig wlan0 up

```

but it says that the wlan0 interface is not found

:confused::confused::confused::confused:

---

### Post by Traxs on 2007-10-12
Did a search and found some other topics about the 8187:


[http://ubuntuforums.org/showthread.php?t=546663&highlight=Realtek](http://ubuntuforums.org/showthread.php?t=546663&highlight=Realtek)

and

[http://ubuntuforums.org/showthread.php?t=493958&highlight=RealTek+8187](http://ubuntuforums.org/showthread.php?t=493958&highlight=RealTek+8187)

and

[http://ubuntuforums.org/showthread.php?t=491390&highlight=RealTek+8187](http://ubuntuforums.org/showthread.php?t=491390&highlight=RealTek+8187)

and many others

It looks like the ndiswrapper method does work - I am going to give it a try later

---

### Post by slaufer on 2007-10-14
Hi, I also bought this laptop during the sale at Best Buy, and happened across this topic.

The wireless adapter in the ML6230 does indeed use a RTL8187B chipset, HOWEVER, it is NOT supported by any of the native RTL8187B drivers as of this writing. That includes the experimental drivers available in the 2.6.23-rc9 kernel.

Under Gentoo, I have the wireless adapter working using ndiswrapper and the drivers available here:

[http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PFid=1&Level=6&Conn=5&ProdID=143&DownTypeID=3&GetDown=false&Downloads=true]("http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PFid=1&Level=6&Conn=5&ProdID=143&DownTypeID=3&GetDown=false&Downloads=true")

at the bottom of the page, under RTL8187B (obviously). I'm using the Win98 driver, however according to diff, they're all the same.

HOWEVER (again) I should mention that i tried to set this wireless adapter up in Debian, and it DID NOT function using the current Debian ndiswrapper package. The card would be recognized, but would refuse to be associated with an access point with iwconfig, or anything else for that matter. The current Gentoo ebuild (1.47) works just fine.

Worth noting is that, according to the ndiswrapper wiki, the ML6230's onboard wireless adapter identifies itself identically to the Trendnet TEW-424UB. (Source: [http://ndiswrapper.sourceforge.net/joomla/index.php?/component/option,com_openwiki/Itemid,33/id,list_o-z/]("http://ndiswrapper.sourceforge.net/joomla/index.php?/component/option,com_openwiki/Itemid,33/id,list_o-z/"))

I hope this post helps you set up your wireless adapter, and isn't TOO disjointed.

---

### Post by hakey on 2007-10-15
I just want to add that I can make this wireless card work, using ndiswrapper and W98 driver.

However, after this thing is working, my notebook randomly freezes up and I can only do a hard power down. After a while even the MBR is damaged. So I had to reinstall the entire OS again.

First I thought it was just bad luck, but after the third re-installation, I started to get a hint. Now I can make the OS recognize the NIC card, and it does see all available APs. The problem is, signal strength for all networks are zero, and it won't connect to any of them.

Second, it seems that the wireless card is on even if I turn it off using the function key (Fn + F2). Strange.

Oh, once more thing I noticed: when the wireless card is working (ndiswrapper), I distinctively noticed the little "send" pixel being lit. (I am talking about the little icon on the top-right corner, I suppose it is network manager applet?). With linux driver, however, the wireless card doesn't even seem to ATTEMPT to connect, because the little pixel was never lit.

If any of you have the wireless card working in a stable state please share it. Thank you very much!

---

### Post by llamabr on 2007-10-18
I'm having the same problem (as are some people on the suse list [http://www.suseforums.net/index.php?showtopic=40125&st=0&gopid=205592&#entry205592](http://www.suseforums.net/index.php?showtopic=40125&st=0&gopid=205592&#entry205592) )
Has anyone had a solution yet?  It looks like wrapping the win98 locks up and crashes the system.  I'm really looking forward to getting this machine going, but without wireless it's not so useful to most of us.

---

### Post by llamabr on 2007-11-29
Well, I bought a ZyXel g220, which worked flawlessly and immediately in ubuntu gutsy.  It was about 10 dollars, and took 5 minutes to get going.

I've quit messing around with the wireless card.  I tried it with Gentoo too, but with no luck.

I might try building ndiswrapper from source, but for now, the usb adapter works just fine.

---

### Post by llamabr on 2008-01-11
As seen in some of my other posts, I solved this by purchasing a ZyXel g-220 v2 usb wireless adapter.  I read about it here:

[http://www.murrayc.com/blog/permalink/2007/09/07/linux-compatible-wireless-usb-adaptor-slightly-better-in-ubuntu-gutsy/](http://www.murrayc.com/blog/permalink/2007/09/07/linux-compatible-wireless-usb-adaptor-slightly-better-in-ubuntu-gutsy/)

on ubuntu 7.10, it worked flawlessly out of the box.  Recently, I've had some errors from the USB, but I believe that's a problem with my machine, and not the adapter.  But I simply solved it by doing a

rmmod ehci-hcd

which removed the module which, I believe, is responsible for high speed 2.0 USB devices. Now my stick is running on the slow 1.1, but that's plenty fast enough.

There's a similar question on the SuSe board here:

[http://www.suseforums.net/index.php?showtopic=40125](http://www.suseforums.net/index.php?showtopic=40125)

I initially installed Suse to solve this problem as some users have had some minimal success with this, but with an Ubuntu workaround, I was the first to come back.

Ltr,

---

