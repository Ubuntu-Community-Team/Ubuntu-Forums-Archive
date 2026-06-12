---
title: "default amixer comands does not work on acer aspire 5253"
date: 2012-02-07
forum: Hardware
---

### Post by maniat1k on 2012-02-07
;)I was trying to figure it out with this question: [http://askubuntu.com/questions/100544/default-amixer-comands-does-not-work-on-acer-aspire-5253](http://askubuntu.com/questions/100544/default-amixer-comands-does-not-work-on-acer-aspire-5253) but I have an small issue:

when I do this:
```
lspci | grep Audio 
00:01.1 Audio device: ATI Technologies Inc Wrestler HDMI Audio [Radeon HD 6250/6310] 
00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia (Intel HDA) (rev 40)
```I can see that I have an Intel sound card, then @foosfreedom gave me a link [https://bbs.archlinux.org/viewtopic.php?id=43457](https://bbs.archlinux.org/viewtopic.php?id=43457) there it shows a couples of lines to add in the [FONT=Courier New][modprobe.conf]("http://manpages.ubuntu.com/manpages/hardy/man5/modprobe.conf.5.html")[/FONT] , but when I try to add that is not there,

```
~$ ls /etc/modprobe.d/
alsa-base.conf               blacklist-cups-usblp.conf    blacklist-modem.conf         blacklist-watchdog.conf
blacklist-ath_pci.conf       blacklist-firewire.conf      blacklist-oss.conf           fglrx.conf
blacklist.conf               blacklist-framebuffer.conf   blacklist-rare-network.conf  libpisock9.conf

```

---

### Post by maniat1k on 2012-02-08
I followed this thread: [http://ubuntuforums.org/showthread.php?t=1140667](http://ubuntuforums.org/showthread.php?t=1140667)

maybe I missing something, after I reload the alsa tryed to use the hot keys, but the does not work (that's the point of all this) Do I need to re-map them?

---

