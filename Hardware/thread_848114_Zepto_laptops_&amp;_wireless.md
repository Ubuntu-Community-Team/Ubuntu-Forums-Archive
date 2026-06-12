---
title: "Zepto laptops &amp; wireless"
date: 2008-07-03
forum: Hardware
---

### Post by Big_Croc7 on 2008-07-03
Hi, just thinking of buying a laptop from Zepto and wondering if anyone has any experience of them?

In general anything about them would be good.

A specific question is, they have the option of either a Zpro2 N-standard wireless adaptor or an Intel 4965AGN, will the Zpro2 work do you think or is it worth paying 30 quid extra for the Intel version (which I think should work easily)?

---

### Post by Tobis84 on 2008-08-10
Hi
I just got my Znote 6025WD in the mail - with the Zpro2 wireless.
After installing Hardy Heron on it (64bit version) I learned that it could not detect either the Zpro2 nor the DVD-drive. 
My advise should be the Intel version, though I don't know if it will work.
My Znote requiers a little work though.
I will hopefully return with answers.

---

### Post by Tavathlon on 2008-08-16
Personally, I am _very_ content with my Znote 6625WD that I bought last year. It's a really good machine.

Some advice that I can give you:
- Go for the Intel wireless - that one works out of the box, but as Tobis is saying, the Zpro does not (a friend of mine that got the Zpro have still not managed to get it to work). I have a contact at Zepto though, I could tell him about this problem - he's not a linux user himself, but he is rather pro-linux. =)   I will get back to you when I've talked to him, although it might take a while due to vacation.
- You might have problem with the sound to begin with. I had problem with my sound in the beginning, but following the guide that is in post #14 in this thread gave me sound: [http://ubuntuforums.org/showthread.php?t=545318&page=2](http://ubuntuforums.org/showthread.php?t=545318&page=2). I am however not sure if this is still needed, or if it works out of the box in Hardy.
- The webcam that is integrated in my 6625 still doesn't have any driver. There is a dev team on it, and they are doing some really nice progress, but they are not done yet. I do not know if it's the same webcam chipset in other models - I told Zepto about this issue, but I don't know if they've done anything about it.
- My general rule whenever I pick a computer is to always go for those with nVidia graphics cards, but the integrated ones should also work well nowadays. I can't help you with anything on those, though. If you want to get your TV-out working and you have nVidia, follow this guide: [http://ubuntuforums.org/showthread.php?t=98456](http://ubuntuforums.org/showthread.php?t=98456) with the tweak that I mention here: [http://ubuntuforums.org/showthread.php?t=875042](http://ubuntuforums.org/showthread.php?t=875042)
- Tobis, I also had a problem with my DVD in the beginning. It was solved by changing the cdrom setting in BIOS from "auto" to "user". Have you tried that?  =)

So, those things that I have had problem with have all been solved, except the webcam. However, it works fine with an external usb-cam that have a chipset that works out of the box until the internal one will get support.  =)

---

### Post by Tavathlon on 2008-08-16
Btw, you might want to take a look at this page: [http://atlas.hasselbalch.com/znote6625wd/](http://atlas.hasselbalch.com/znote6625wd/)

=)

---

### Post by Tobis84 on 2008-08-17
Thanks for the tip with the disc-drive. Now it works like a charme.. now I just need that internet-connection. 
I try to connect my Ubuntu-laptop with my XP desktop pc via crossover cable. I have come as far as getting the connection going, but the repository can't translate the name 'dk.archive.ubuntu.com' any other names

---

### Post by Tavathlon on 2008-08-18
Tobis, are you Swedish, Danish or Norwegian? If you are, then I assume you will be able to follow this guide that I found, and if you are not then tell me and I'll translate it for you. I intend to translate it anyway, but it would be nice to know for sure that it actually works first.

You see, I happened to come across this little guide on how to get that wireless card to work: [http://xodeus.dk/?page_id=141](http://xodeus.dk/?page_id=141) (after the guide on how to manually install alsa). It's written for Gutsy though, but could you please try it out?

---

### Post by terrax on 2008-08-18
> **Big_Croc7 said:**
> Hi, just thinking of buying a laptop from Zepto and wondering if anyone has any experience of them?

In general anything about them would be good.

A specific question is, they have the option of either a Zpro2 N-standard wireless adaptor or an Intel 4965AGN, will the Zpro2 work do you think or is it worth paying 30 quid extra for the Intel version (which I think should work easily)?


Take the 4965AGN! Trust me. I am danish, and have had a zepto recently. I took the Zpro and you have to fetch a unstable driver from madwifi.org. Thats not worth it, because they are not updating their "normal" driver anymore, because new opensource driver will come to that card. But again, Its in very early stages.

Instead I actually bought 4965AGN, and replaced the zpro card. Not because the madwifi driver didn't work, but it disconnected very often and made kernel lockups.

---

### Post by Tobis84 on 2008-08-19
Hey Tavathlon
Yes I'm danish and understood the guide.
I found it through a search on Google in addition to an english version on Notebookreview.com
[http://forum.notebookreview.com/showthread.php?t=230283]("http://forum.notebookreview.com/showthread.php?t=230283")
so the translation has been done.
Thanks anyway. It seems to be working. I'll try it some time soon and post back with the result.

---

### Post by Tobis84 on 2008-08-21
Hey Tavathlon
Jeg har prøvet din guide som du henviser til, men jeg får nogle advarsler under 'make'-kommandoen. Som om der er fejl i koden, noget med nogle pointere der er gået galt i byen.

> make -C tools
make[1]: Går til katalog '/home/hje/2008_0108_RT2860_Linux_STA_v1.5.0.0/tools'
gcc -g bin2h.c -o bin2h
make[1]: Forlader katalog '/home/hje/2008_0108_RT2860_Linux_STA_v1.5.0.0/tools'
/home/hje/2008_0108_RT2860_Linux_STA_v1.5.0.0/tools/bin2h
cp -f os/linux/Makefile.6 /home/hje/2008_0108_RT2860_Linux_STA_v1.5.0.0/os/linux/Makefile
make  -C  /lib/modules/2.6.24-19-generic/build SUBDIRS=/home/hje/2008_0108_RT2860_Linux_STA_v1.5.0.0/os/linux modules
make[1]: Går til katalog '/usr/src/linux-headers-2.6.24-19-generic'
  CC [M]  /home/hje/2008_0108_RT2860_Linux_STA_v1.5.0.0/os/linux/../../common/md5.o
  CC [M]  /home/hje/2008_0108_RT2860_Linux_STA_v1.5.0.0/os/linux/../../common/mlme.o
  CC [M]  /home/hje/2008_0108_RT2860_Linux_STA_v1.5.0.0/os/linux/../../common/rtmp_wep.o
  CC [M]  /home/hje/2008_0108_RT2860_Linux_STA_v1.5.0.0/os/linux/../../common/action.o
  CC [M]  /home/hje/2008_0108_RT2860_Linux_STA_v1.5.0.0/os/linux/../../common/ba_action.o
/home/hje/2008_0108_RT2860_Linux_STA_v1.5.0.0/os/linux/../../common/ba_action.c: In function &#8216;convert_reordering_packet_to_preAMSDU_or_802_3_packet&#8217;:
/home/hje/2008_0108_RT2860_Linux_STA_v1.5.0.0/os/linux/../../common/ba_action.c:1380: advarsel: assignment makes integer from pointer without a cast
  CC [M]  /home/hje/2008_0108_RT2860_Linux_STA_v1.5.0.0/os/linux/../../common/cmm_data.o
  CC [M]  /home/hje/2008_0108_RT2860_Linux_STA_v1.5.0.0/os/linux/../../common/rtmp_init.o
  CC [M]  /home/hje/2008_0108_RT2860_Linux_STA_v1.5.0.0/os/linux/../../common/rtmp_tkip.o
  CC [M]  /home/hje/2008_0108_RT2860_Linux_STA_v1.5.0.0/os/linux/../../common/cmm_sync.o
  CC [M]  /home/hje/2008_0108_RT2860_Linux_STA_v1.5.0.0/os/linux/../../common/eeprom.o
  CC [M]  /home/hje/2008_0108_RT2860_Linux_STA_v1.5.0.0/os/linux/../../common/cmm_sanity.o
  CC [M]  /home/hje/2008_0108_RT2860_Linux_STA_v1.5.0.0/os/linux/../../common/cmm_info.o
  CC [M]  /home/hje/2008_0108_RT2860_Linux_STA_v1.5.0.0/os/linux/../../common/cmm_wpa.o
  CC [M]  /home/hje/2008_0108_RT2860_Linux_STA_v1.5.0.0/os/linux/../../common/dfs.o
  CC [M]  /home/hje/2008_0108_RT2860_Linux_STA_v1.5.0.0/os/linux/../../sta/assoc.o
  CC [M]  /home/hje/2008_0108_RT2860_Linux_STA_v1.5.0.0/os/linux/../../sta/aironet.o
  CC [M]  /home/hje/2008_0108_RT2860_Linux_STA_v1.5.0.0/os/linux/../../sta/auth.o
  CC [M]  /home/hje/2008_0108_RT2860_Linux_STA_v1.5.0.0/os/linux/../../sta/auth_rsp.o
  CC [M]  /home/hje/2008_0108_RT2860_Linux_STA_v1.5.0.0/os/linux/../../sta/sync.o
  CC [M]  /home/hje/2008_0108_RT2860_Linux_STA_v1.5.0.0/os/linux/../../sta/sanity.o
  CC [M]  /home/hje/2008_0108_RT2860_Linux_STA_v1.5.0.0/os/linux/../../sta/rtmp_data.o
  CC [M]  /home/hje/2008_0108_RT2860_Linux_STA_v1.5.0.0/os/linux/../../sta/connect.o
  CC [M]  /home/hje/2008_0108_RT2860_Linux_STA_v1.5.0.0/os/linux/../../sta/wpa.o
  CC [M]  /home/hje/2008_0108_RT2860_Linux_STA_v1.5.0.0/os/linux/../../os/linux/rt_linux.o
/home/hje/2008_0108_RT2860_Linux_STA_v1.5.0.0/os/linux/../../os/linux/rt_linux.c: In function &#8216;duplicate_pkt&#8217;:
/home/hje/2008_0108_RT2860_Linux_STA_v1.5.0.0/os/linux/../../os/linux/rt_linux.c:548: advarsel: passing argument 1 of &#8216;memmove&#8217; makes pointer from integer without a cast
/home/hje/2008_0108_RT2860_Linux_STA_v1.5.0.0/os/linux/../../os/linux/rt_linux.c:550: advarsel: passing argument 1 of &#8216;memmove&#8217; makes pointer from integer without a cast
/home/hje/2008_0108_RT2860_Linux_STA_v1.5.0.0/os/linux/../../os/linux/rt_linux.c: In function &#8216;ClonePacket&#8217;:
/home/hje/2008_0108_RT2860_Linux_STA_v1.5.0.0/os/linux/../../os/linux/rt_linux.c:634: advarsel: assignment makes integer from pointer without a cast
/home/hje/2008_0108_RT2860_Linux_STA_v1.5.0.0/os/linux/../../os/linux/rt_linux.c: In function &#8216;update_os_packet_info&#8217;:
/home/hje/2008_0108_RT2860_Linux_STA_v1.5.0.0/os/linux/../../os/linux/rt_linux.c:656: advarsel: assignment makes integer from pointer without a cast
/home/hje/2008_0108_RT2860_Linux_STA_v1.5.0.0/os/linux/../../os/linux/rt_linux.c: In function &#8216;wlan_802_11_to_802_3_packet&#8217;:
/home/hje/2008_0108_RT2860_Linux_STA_v1.5.0.0/os/linux/../../os/linux/rt_linux.c:676: advarsel: assignment makes integer from pointer without a cast
/home/hje/2008_0108_RT2860_Linux_STA_v1.5.0.0/os/linux/../../os/linux/rt_linux.c: In function &#8216;send_monitor_packets&#8217;:
/home/hje/2008_0108_RT2860_Linux_STA_v1.5.0.0/os/linux/../../os/linux/rt_linux.c:868: advarsel: format &#8216;%d&#8217; expects type &#8216;int&#8217;, but argument 3 has type &#8216;long unsigned int&#8217;
/home/hje/2008_0108_RT2860_Linux_STA_v1.5.0.0/os/linux/../../os/linux/rt_linux.c:915: advarsel: assignment makes integer from pointer without a cast
/home/hje/2008_0108_RT2860_Linux_STA_v1.5.0.0/os/linux/../../os/linux/rt_linux.c:923: advarsel: assignment makes integer from pointer without a cast
  CC [M]  /home/hje/2008_0108_RT2860_Linux_STA_v1.5.0.0/os/linux/../../os/linux/rt_profile.o
/home/hje/2008_0108_RT2860_Linux_STA_v1.5.0.0/os/linux/../../os/linux/rt_profile.c:223: advarsel: &#8216;rtinet_aton&#8217; defined but not used
  CC [M]  /home/hje/2008_0108_RT2860_Linux_STA_v1.5.0.0/os/linux/../../os/linux/rt_main_dev.o
/home/hje/2008_0108_RT2860_Linux_STA_v1.5.0.0/os/linux/../../os/linux/rt_main_dev.c: In function &#8216;rt28xx_open&#8217;:
/home/hje/2008_0108_RT2860_Linux_STA_v1.5.0.0/os/linux/../../os/linux/rt_main_dev.c:537: fejl: &#8216;SA_SHIRQ&#8217; undeclared (first use in this function)
/home/hje/2008_0108_RT2860_Linux_STA_v1.5.0.0/os/linux/../../os/linux/rt_main_dev.c:537: fejl: (Each undeclared identifier is reported only once
/home/hje/2008_0108_RT2860_Linux_STA_v1.5.0.0/os/linux/../../os/linux/rt_main_dev.c:537: fejl: for each function it appears in.)
/home/hje/2008_0108_RT2860_Linux_STA_v1.5.0.0/os/linux/../../os/linux/rt_main_dev.c:537: advarsel: passing argument 2 of &#8216;request_irq&#8217; from incompatible pointer type
/home/hje/2008_0108_RT2860_Linux_STA_v1.5.0.0/os/linux/../../os/linux/rt_main_dev.c: In function &#8216;rt_ieee80211_if_setup&#8217;:
/home/hje/2008_0108_RT2860_Linux_STA_v1.5.0.0/os/linux/../../os/linux/rt_main_dev.c:624: advarsel: assignment from incompatible pointer type
/home/hje/2008_0108_RT2860_Linux_STA_v1.5.0.0/os/linux/../../os/linux/rt_main_dev.c:647: advarsel: passing argument 1 of &#8216;dev_get_by_name&#8217; from incompatible pointer type
/home/hje/2008_0108_RT2860_Linux_STA_v1.5.0.0/os/linux/../../os/linux/rt_main_dev.c:647: fejl: too few arguments to function &#8216;dev_get_by_name&#8217;
/home/hje/2008_0108_RT2860_Linux_STA_v1.5.0.0/os/linux/../../os/linux/rt_main_dev.c: In function &#8216;rt28xx_probe&#8217;:
/home/hje/2008_0108_RT2860_Linux_STA_v1.5.0.0/os/linux/../../os/linux/rt_main_dev.c:1103: fejl: implicit declaration of function &#8216;SET_MODULE_OWNER&#8217;
make[2]: *** [/home/hje/2008_0108_RT2860_Linux_STA_v1.5.0.0/os/linux/../../os/linux/rt_main_dev.o] Fejl 1
make[1]: *** [_module_/home/hje/2008_0108_RT2860_Linux_STA_v1.5.0.0/os/linux] Fejl 2
make[1]: Forlader katalog '/usr/src/linux-headers-2.6.24-19-generic'
make: *** [LINUX] Fejl 2


---

### Post by Tavathlon on 2008-08-21
Alright, then let's discard that one. I'm just a user, don't know anything about coding..  =S

Check this up instead: [http://www.sweclockers.com/forum/showthread.php?threadid=723208&perpage=30&pagenumber=1](http://www.sweclockers.com/forum/showthread.php?threadid=723208&perpage=30&pagenumber=1)

There's a guide in the first post on how to use the windows-drivers with ndiswrapper instead. However, note that there is another post on page 3 with some useful info (use your browsers search function and search for zpro2. That other user tells about a linux driver that has been developed but that does not work very well, and recommends to use ndiswrapper - but with two other files than the ones referred to in the first post, and there are links to those two other files.

Could you try this, Tobis?

---

### Post by Tobis84 on 2008-08-23
hi again
Searching for the RT2860 driver online lead me på the RALINK website.
They have released a 1.7 version of the driver instead of the 1.5 I tried to compile, and it compiled with only small warnings and no errors. Now I just need to know how to install WICD on Hardy Heron.
Any suggestions? 
In your guide it says something about gutsy extras...? 
Is that for hardy too?

---

### Post by Tavathlon on 2008-08-23
Hm, is WICD needed when installed with ndiswrapper? As far as I can tell from the guide on sweclockers, you just reboot once you've installed and modprobed, and then there should be a wireless connection visible in System / Administration / Network. Perhaps it didn't work as it should?

I also noticed now, btw, that there is also another guide in the second post, same thread, on how to get it to work with madwifi. If the first one doesn't work, perhaps you could try that one instead? I'm not completely sure it's the same card though.

---

### Post by Tobis84 on 2008-08-23
Now I got it to work.
I found the new driver at the RaLink-website (RT2860 v1.7) which compiled ok.
and made me able to complete the guide you showed me, adding Wicd to my system.
It needed a little adjustment though. I am using Hardy heron and not Gutsy Gibbon as shown in the guide.
Now I just need to get home to my wlan-connection to try it out.

EDIT: I found this thread on how to get to work on startup: [http://ubuntuforums.org/showthread.php?p=5634480]("http://ubuntuforums.org/showthread.php?p=5634480")

---

### Post by Tavathlon on 2008-08-23
Great, tell us how it goes  =)

---

### Post by Tobis84 on 2008-08-24
this is not promising. It jumps on and off... can't explain it.. though I got it online with WEP encryption and all
any suggestions?
I got the RT2860 v1.7 driver 
WICD network manager

---

### Post by Tavathlon on 2008-08-25
Nope, this is beyond me. Sorry..  =/
My friend with the same card is back from his travels now though, so I guess he will begin looking at it again.

---

### Post by E-mol on 2008-09-01
I have searched a little around.
And i found a tutorial by LAW-Mastermind (a great man).

This one:
[http://ubuntuforums.org/showthread.php?t=683085&highlight=zepto+zpro2&page=5]("http://ubuntuforums.org/showthread.php?t=683085&highlight=zepto+zpro2&page=5")

I tried that, it worked a little. But i have managed to do it, so it works, and an easier way:

First of all, make sure it is Network-Manager you are using. Install if it isn't.
Then download the newest driver from ralink's site.
Or here:
[http://www.ralinktech.com.tw/data/drivers/2008_0708_RT2860_Linux_STA_v1.7.0.0.tar.bz2]("http://www.ralinktech.com.tw/data/drivers/2008_0708_RT2860_Linux_STA_v1.7.0.0.tar.bz2")

Unpack the folder.

Open the file <folder of the driver>/os/linux/config.mk

Search for:

```
# Support Wpa_Supplicant
HAS_WPA_SUPPLICANT=n

# Support Native WpaSupplicant for Network Manager
HAS_NATIVE_WPA_SUPPLICANT_SUPPORT=n
```

Replace it with this:

```
# Support Wpa_Supplicant
HAS_WPA_SUPPLICANT=y

# Support Native WpaSupplicant for Network Manager
HAS_NATIVE_WPA_SUPPLICANT_SUPPORT=y
```

Open the terminal, navigate to the root of the drivers folder and type:

```
sudo make && sudo make install
```

(REMEMBER TO HAVE BUILD-ESSENTIAL INSTALLED!)

Restart, and then it should work :)

Unfortunately i got a failure when a shut down the computer. Can't remember the exact fail, something with network-manager. (I don't have the computer at home right now, my girlfriend is using it at her boarding-school)

E-mol :)

---

### Post by Tavathlon on 2008-10-25
Hey everyone!

It seems my friend with that network card got it working now, at last - by installing Kubuntu 8.10 Intrepid Ibex. I would assume that the same goes for Ubuntu 8.10, but it would be good if someone could confirm it.  =)

---

### Post by E-mol on 2009-03-02
I know it is late.. but i will try on mine :)

---

