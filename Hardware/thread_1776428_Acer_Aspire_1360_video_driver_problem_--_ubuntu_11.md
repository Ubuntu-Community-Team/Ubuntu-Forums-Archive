---
title: "Acer Aspire 1360 video driver problem -- ubuntu 11.10"
date: 2011-06-06
forum: Hardware
---

### Post by michael_brockway on 2011-06-06
I have been running an Acer Aspire 1360 laptop in Ubuntu for 3 or 4 years now but have on upgrading to 11.04 found two problems. 

(1) The highest screen resolution I am offered is 800 X 600 and this gives me a slightly screwed-up display in which the right-most 20% of the screen is black and the bottom-most 25% of the screen is a repeat of whatever is displayed at the top. The config tool claims not to recognise the hardware. There is no xorg.conf file although there are a number of .conf items in /usr/share/X11/xorg.conf.d

(2) I have always connected to WiFi using ndiswrapper. But now I have to run sudo modprobe ndiswrapper EVERY TIME I boot up, before WiFi wakes up; and sometimes, this causes usb to stop working properly. This has been a problem since ubuntu 10.04, actually. I thought I had installed ndiswrapper correctly: /etc/modprobe.d/ contains file ndiswrapper.conf containing "alias wlan0 ndiswrapper".
 
Previously I used the long-term support version (8.04) and everything worked out of the box with minimum hassle, with, if I remember correctly, 1024x786 resolution.

---

### Post by paulbuk on 2011-07-07
Hi, I've installed 11.04 on my sister's old Acer 1360 Aspire today to ween her off winXP and save her M$ dosh. The install went fine other than the resolution being only 800*600 and also leaving the black area to the right on the screen which I'd like to resolve.
Can anyone give any pointers on how to fix this issue, I'm DETERMINED not to her go back to M$ winXP as I jumped the M$ ship 24 months ago and have never looked back. Ubuntu there is NO OTHER way IMO!!

I also have an MSI wireless card which I want to get working on the above said laptop. (:

Thanks in advance.

PB

---

### Post by guypracy on 2012-10-11
I have a very similar issue.

I currently run 10.04 LTS Lucid Lynx on my Acer Aspire 1360 with no problems.  I have tried both 11.04 and 12.04 LTS and they BOTH exhibit chronic video corruption making the screen virtually unreadable.  I get 3/4 of the screen corrupt with the rest of the screen black.

It is not a video card problem as I can run Windows XP, Windows 7, Haiku Alpha 3 and Ubuntu 10.04 LTS with no issues.  Interestingly I also have the same graphic corruption with Linux Mint 13 Maya, Fedora 17 and (predictably) Kubuntu 11.04.

I have search the internet but still cannot find a solution to this problem - does any body here have the solution?

I would really like to get this sorted before the support for Lucid runs out in April 2013.

Thanks

---

### Post by Yellow Pasque on 2012-10-12
The Aspire 1360 came with different GPU options. I'm guessing you folks have the VIA  Unichrome GPU. What does this command tell you?:
```
lspci | grep VGA
```

---

