---
title: "Ubuntu randomy freezes!"
date: 2008-11-29
forum: Hardware
---

### Post by ryclegman on 2008-11-29
hey,

I have had Ubuntu for a while now, and i really hate how it randomly freezes! It usually happens when Im watching a you tube video or on the web doing something! It also happens when i someone is uploading to my server.... My computer will freeze and my key board light will just flash,and then the files don't get uploaded. If there is any fix for this that would be great because this is really getting annoying!:mad::mad::mad::mad:

My computer:
nvidia 9600 gt
msi mother board
core 2 quad 64 bit
4 gigs of ram
500 gig sata

---

### Post by wandalalakers on 2008-11-30
Boot up your pc press ESC when you see the option on your screen and select memtest.  Maybe something is wrong with your ram or something else.
This might be reaching but try updating the bios for your motherboard.
[http://global.msi.com.tw/index.php?func=downloadindex](http://global.msi.com.tw/index.php?func=downloadindex)
What version of ubuntu are you using?

---

### Post by ryclegman on 2008-11-30
i am using hardy heron.. checking memtest now

---

### Post by ryclegman on 2008-11-30
all right i ran memtest and it came up with no errors!

---

### Post by ryclegman on 2008-12-02
I had it happen 3 times in a row just now.. and i was downloading something off the internet as well if that tells anyone anything?

---

### Post by ryclegman on 2008-12-02
I found this error in my sys log


> Dec 1 15:45:14 ryan-desktop avahi-daemon[5252]: Withdrawing address record for ******** on wlan0.
Dec 1 15:45:14 ryan-desktop avahi-daemon[5252]: Leaving mDNS multicast group on interface wlan0.IPv4 with address *********.
Dec 1 15:45:14 ryan-desktop avahi-daemon[5252]: Interface wlan0.IPv4 no longer relevant for mDNS.
Dec 1 15:45:14 ryan-desktop avahi-daemon[5252]: Withdrawing address record for fe80::218:f8ff:fe2d:f0f4 on wlan0.
Dec 1 15:45:14 ryan-desktop avahi-daemon[5252]: Joining mDNS multicast group on interface wlan0.IPv4 with address ************.
Dec 1 15:45:14 ryan-desktop avahi-daemon[5252]: New relevant interface wlan0.IPv4 for mDNS.
Dec 1 15:45:14 ryan-desktop avahi-daemon[5252]: Registering new address record for ******** on wlan0.IPv4.
Dec 1 15:45:15 ryan-desktop NetworkManager: <info> Clearing nscd hosts cache.
Dec 1 15:45:15 ryan-desktop NetworkManager: <WARN> nm_spawn_process(): nm_spawn_process('/usr/sbin/nscd -i hosts'): could not spawn process. (Failed to execute child process "/usr/sbin/nscd" (No such file or directory))

---

### Post by sergiom99 on 2008-12-02
check this other thread on the same topic:
[http://ubuntuforums.org/showthread.php?t=976287](http://ubuntuforums.org/showthread.php?t=976287)

---

### Post by ryclegman on 2008-12-04
I figured it out its a wireless issue, and i used [https://help.ubuntu.com/community/Wi...er/Ndiswrapper](https://help.ubuntu.com/community/Wi...er/Ndiswrapper) .... We will see if it works
!!!

---

### Post by ryclegman on 2008-12-05
well reverting back to hardy wont do anything.... My method did connect the hardware, but never would actually allow access to the internet. THE problem is the WIRELESS DRIVER! linksys does not provide linux drivers

---

