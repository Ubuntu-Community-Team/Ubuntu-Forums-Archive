---
title: "Network issue with Kernel 2.6.27-11 update on MSI-WIND"
date: 2009-01-28
forum: Installation &amp; Upgrades
---

### Post by manuleka on 2009-01-28
i am currently connecting to the web using prior version to my upgrade to kernel 2.6.27-9 generic, when i ran the Ubuntu update a couple of hours ago my networking stopped functioning... i thought it was just a wireless card issue but then tried connecting using a cable with no luck

wireless doesn't showup which is an obvious reason for it not being detected somehow.. but when i connect the cable it doesn't connect at all :(

i'm using a MSI WIND with the following Network Chipsets/Adapters:

Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E
Ralink tech RT2700E WLan a/g/n

has anyone come across this issue before?

---

### Post by JSorroche on 2009-01-29
I've got the same problem with my MSI WIND. :(

No wireless or cable connection with 2.6.27-11 kernel but no problem with 2.6.27-9 ! It's really annoying !

---

### Post by simonz05 on 2009-01-29
Had the exact same problem with my MSI Wind.Everything was working fine until recently when I upgraded to the latest Kernel. Is there any solution for this problem anywhere?

---

### Post by manuleka on 2009-01-29
I manage to fix it by reinstalling wireless driver: I've got RT2700e chipset which is in the RT2860 dirver package:

[http://www.ralinktech.com/ralink/Home/Support/Linux.html](http://www.ralinktech.com/ralink/Home/Support/Linux.html)

RT2860: 
[http://www.ralinktech.com.tw/data/drivers/2008_0918_RT2860_Linux_STA_v1.8.0.0.tar.bz2](http://www.ralinktech.com.tw/data/drivers/2008_0918_RT2860_Linux_STA_v1.8.0.0.tar.bz2)

download the deb file run it and it will fix your wireless... also if you are using a different wireless card i suggest REINSTALLATION of Driver

---

### Post by simonz05 on 2009-01-30
Well, neither the wireless, nor the normal network card was working after this update. I have the same Wireless card as you, so I guess that should solve the problem for me. Or, well. I just re-installed ubuntu since my boot was less then a day old, and after that I haven't updated the system yet. Was waiting for a fix first. Did you have trouble with your normal wired network car as well? Or was it just the wireless which droped dead?

o/

---

### Post by manuleka on 2009-01-30
both Wired and Wireless... i dropped back to previous kernel and downloaded driver since networking worked - then reboot and reinstall wireless and it worked, i think my wired network is still not working properly... i'll have a look at it at some stage today and post...

---

### Post by manuleka on 2009-01-30
> **simonz05 said:**
> Well, neither the wireless, nor the normal network card was working after this update. I have the same Wireless card as you, so I guess that should solve the problem for me. Or, well. I just re-installed ubuntu since my boot was less then a day old, and after that I haven't updated the system yet. Was waiting for a fix first. Did you have trouble with your normal wired network car as well? Or was it just the wireless which droped dead?

o/

you do know you can drop back to previous kernel by hitting escape on bootup... that should bring up boot options and just pick previous kernel...

---

### Post by simonz05 on 2009-01-30
Hehe, well, now I know. I'm not to familiar with Ubuntu. I went on to downgrade each package first, but it didnt seem to help. So did it the quick and dirty way. Anyhow, I guess I should try to find some drivers for the wired network and see if it works. Thanks for the help so far, btw.

---

### Post by jepong on 2009-01-31
i do have the same issue. I upgraded to the new kernel and restart the wind and wired network is not working. I tried a LiveCD of 8.10 and funny it works.

---

### Post by simonz05 on 2009-01-31
I am now surfing with kernel 2.6.27-11, wired and wireless. SOLUTION for this issue is as follows:

[LIST]
[*]**Wireless network:** Reinstall drivers. Usually you just need to download the correct driver package and run it in your favourite package installer. [This]("http://forums.msiwind.net/debian/solution-drivers-for-ralink-card-t5864.html") is a helpful link if you dont know how. 
[*]**Wired network:** Well, same as before; reinstall drivers. It's abit more difficult to do this, but nothing fancy *pancy*.  Basically you'll need to download your drivers at either [r8101]("http://www.realtek.com.tw/Downloads/downloadsView.aspx?Langid=1&PNid=14&PFid=7&Level=5&Conn=4&DownTypeID=3&GetDown=false") or [r8169]("http://122.146.118.42/downloads/downloadsView.aspx?Langid=1&PNid=13&PFid=5&Level=5&Conn=4&DownTypeID=3&GetDown=false") depending on your LAN card. And then compile those sources. Follow [these steps]("http://en.alessiotreglia.com/articles/realteks-modules-new-version-has-been-released/") and you'll do ok. If you need internett access for anything; reboot and press ESC during boot to select the previus kernel. 
[/LIST]

Thanks to manuleka for the helpful tip.

---

### Post by manuleka on 2009-01-31
thanks simonz05 for the links, i've been trying to reinstall my LAN Wire driver with no luck... now both my Wired and Wireless are functioning :)

---

### Post by simonz05 on 2009-02-01
> **manuleka said:**
> thanks simonz05 for the links, i've been trying to reinstall my LAN Wire driver with no luck... now both my Wired and Wireless are functioning :)

I was getting a shutdown/reboot issue (ACPID:Exiting #CPU1 bug) thing when applying my fix for this so I've decided to just roll-back to 2.6.27-7 kernel which is working fine. Did you experience anything similar?

---

### Post by manuleka on 2009-02-01
no no reboot/shutdown issue... what's your network card?

---

### Post by Siúlóir on 2009-02-02
I also have an issue with the upgraded kernel 2.6.27-11.

On the road I'm using a built-in Ericsson UMTS modem which worked file using wvdial (network manager did not do the trick).

Today I booted  2.6.27-11 and **wvdial on** complained that there was no device /dev/ttyACM*.

I rebooted to 2.6.27-9 and, voila, everything worked again.

I guess the network stuff in 2.6.27-11 is pretty messed up.

Cheers

Siúlóir

---

### Post by manuleka on 2009-02-02
driver reinstallation should fix your issues Siuloir

---

### Post by hashbrowns on 2009-02-03
I have a similar-yet-different problem to report. I just did a fresh install onto a Wind with Intrepid, kernel version 2.6.27-7 and immediately, the RT2700e does not work at all. I installed the debian drivers provided by the nice person at msiwind.net, and then on my WPA2 encrypted network, I get the loop of authorization access requests. When I change the encryption to simple 128 bit WEP, then there's no problems and it connects without issue.

It sounds like there's lots of annoyances with -11 as well, but less with -9? Do you guys recommend that I should try to find the 2.6.27-9 kernel and try to get to that, but not yet 11 with this Wind?

At least I'm VERY happy that it's not a hardware problem :)

---

### Post by manuleka on 2009-02-04
> **hashbrowns said:**
> I have a similar-yet-different problem to report. I just did a fresh install onto a Wind with Intrepid, kernel version 2.6.27-7 and immediately, the RT2700e does not work at all. I installed the debian drivers provided by the nice person at msiwind.net, and then on my WPA2 encrypted network, I get the loop of authorization access requests. When I change the encryption to simple 128 bit WEP, then there's no problems and it connects without issue.

It sounds like there's lots of annoyances with -11 as well, but less with -9? Do you guys recommend that I should try to find the 2.6.27-9 kernel and try to get to that, but not yet 11 with this Wind?

At least I'm VERY happy that it's not a hardware problem :)

i have been using 9 before i upgraded to 11... although things seems to be sound i get this sometimes when i restart or shutdown my machine:

```

[xxxxx.xxxxxx] BUG: Soft Lockup - CPU#1 stuck for xxs! [NetworkManager:xxxx] xxxx

```
where x is a number

i will try reinstalling drivers again (i'm assuming it's a problem with network again)

---

### Post by hashbrowns on 2009-02-05
> **manuleka said:**
> i have been using 9 before i upgraded to 11... although things seems to be sound i get this sometimes when i restart or shutdown my machine:

```

[xxxxx.xxxxxx] BUG: Soft Lockup - CPU#1 stuck for xxs! [NetworkManager:xxxx] xxxx

```
where x is a number

i will try reinstalling drivers again (i'm assuming it's a problem with network again)

Silly question; but how do I install an older-than-current firmware? :P where do I get it from?

---

### Post by Shtirlits on 2009-02-07
Thanks!

The reinstall directions on first page fixed my network problem.

---

### Post by manuleka on 2009-02-07
no worries :)

---

### Post by jepong on 2009-02-08
there's an new kernel [2.6.27-12]("https://lists.ubuntu.com/archives/intrepid-changes/2009-February/009667.html"). I haben't tried it yet... hope it'll fix the network problem.

---

### Post by manuleka on 2009-02-09
i hope so... am running update now.. will post results

---

### Post by hashbrowns on 2009-02-12
> **manuleka said:**
> i hope so... am running update now.. will post results

How did it go? Did things become functional?

---

### Post by manuleka on 2009-02-12
how can i update ot 27-12? running update manager doesn't bring up kernel 2.6.27-12 updates... what other ways can i use to capture this update? can it be downloaded from somewhere? or maybe the latest stable version available

---

### Post by hashbrowns on 2009-02-14
> **manuleka said:**
> how can i update ot 27-12? running update manager doesn't bring up kernel 2.6.27-12 updates... what other ways can i use to capture this update? can it be downloaded from somewhere? or maybe the latest stable version available

Maybe this? I haven't tried it myself because I'm on my windows machine at the moment, but this looks promising...

[http://ftp.kaist.ac.kr/ubuntu/pool/restricted/l/linux-restricted-modules/](http://ftp.kaist.ac.kr/ubuntu/pool/restricted/l/linux-restricted-modules/)

---

### Post by Siúlóir on 2009-05-16
> **Siúlóir said:**
> I also have an issue with the upgraded kernel 2.6.27-11.

On the road I'm using a built-in Ericsson UMTS modem which worked file using wvdial (network manager did not do the trick).

Today I booted  2.6.27-11 and **wvdial on** complained that there was no device /dev/ttyACM*.


I solved the problem by blacklisting the USB-serial option module after reading the hint from [this ThinkWiki page]("http://www.thinkwiki.org/wiki/Ericsson_F3507g_Mobile_Broadband_Module").

It is now working with kernel 2.6.27-14.

Cheers

Siúlóir

---

