---
title: "Mediatek AC 1200M (formerly Ralink) Ubuntu connecting issue"
date: 2015-11-02
forum: Hardware
---

### Post by aaron36 on 2015-11-02
You may try instructions from here it did not work for me.... see bottom of this post... answer there..

[http://ubuntuforums.org/showthread.php?t=2270202&highlight=0e8d%3A7612+MediaTek](http://ubuntuforums.org/showthread.php?t=2270202&highlight=0e8d%3A7612+MediaTek)

I downloaded the updated Software and using different Ubuntu and Linux forums.... I am very close to getting the sofware to install Linux mint 17.2 / Ubuntu 14.04 Trusty. 32 bit
Here is the hardware list from the Terminal command....  Installed the Wifi Dongle in a Windows Operating system works fine there.... (now I have to disinfect my hands)
  
here is the website and drivers... [http://www.szedup.com/showinfo.aspx?id=554](http://www.szedup.com/showinfo.aspx?id=554)

This Forum does not tell what file is to be patched....   [http://askubuntu.com/questions/457061/ralink-148f7601-wifi-adapter-installation/](http://askubuntu.com/questions/457061/ralink-148f7601-wifi-adapter-installation/)     It's easier if you spell it out clearly we are not all Software engineers here...

I am going to send another E-mail to the seller.... I have been to several ubuntu forums a couple state I have to "patch" a file ... will not tell me the file to patch. Computer sees the "USB dongle" 

See the note at the bottom of this page...

$ lsusb
Bus 002 Device 002: ID 0e8d:7612 MediaTek Inc. <<<<<................................ is the Device I am trying to get working...  from EDUP model EP-AC 1601 (driver same name..) Instructions are not clear what so ever... 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 003: ID 0bda:0151 Realtek Semiconductor Corp. Mass Storage Device (Multicard Reader)
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 002: ID 046d:c52b Logitech, Inc. Unifying Receiver
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

is the error I get after running 
$ make
make -C tools
make[1]: Entering directory `/home/akhj/Downloads/DPO/tools'
gcc -g bin2h.c -o bin2h
make[1]: Leaving directory `/home/akhj/Downloads/DPO/tools'
/home/akhj/Downloads/DPO/tools/bin2h
chipset = mt7662u
chipset = mt7632u
chipset = mt7612u
cp -f os/linux/Makefile.6 /home/akhj/Downloads/DPO/os/linux/Makefile
make -C /lib/modules/3.19.0-31-generic/build SUBDIRS=/home/akhj/Downloads/DPO/os/linux modules
make[1]: Entering directory `/usr/src/linux-headers-3.19.0-31-generic'
  CC [M]  /home/akhj/Downloads/DPO/os/linux/../../sta/sync.o
/home/akhj/Downloads/DPO/os/linux/../../sta/sync.c: In function &#8216;rtmp_dbg_sanity_diff&#8217;:
/home/akhj/Downloads/DPO/os/linux/../../sta/sync.c:1069:10: error: &#8216;SelReg&#8217; undeclared (first use in this function)
         &SelReg,
          ^
/home/akhj/Downloads/DPO/os/linux/../../sta/sync.c:1069:10: note: each undeclared identifier is reported only once for each function it appears in
/home/akhj/Downloads/DPO/os/linux/../../sta/sync.c: In function &#8216;PeerBeaconAtScanAction&#8217;:
/home/akhj/Downloads/DPO/os/linux/../../sta/sync.c:1425:4: warning: format &#8216;%d&#8217; expects argument of type &#8216;int&#8217;, but argument 4 has type &#8216;ULONG&#8217; [-Wformat=]
    DBGPRINT(RT_DEBUG_OFF, ("%s P2P_SCANNING: %s [%d]\n", __FUNCTION__, ie_list->Ssid, Idx));
    ^
/home/akhj/Downloads/DPO/os/linux/../../sta/sync.c: In function &#8216;PeerBeaconAtJoinAction&#8217;:
/home/akhj/Downloads/DPO/os/linux/../../sta/sync.c:1581:13: error: &#8216;SelReg&#8217; undeclared (first use in this function)
        if ( SelReg == 0 )
             ^
/home/akhj/Downloads/DPO/os/linux/../../sta/sync.c:1805:26: warning: format &#8216;%d&#8217; expects argument of type &#8216;int&#8217;, but argument 4 has type &#8216;ULONG&#8217; [-Wformat=]
                          DBGPRINT(RT_DEBUG_OFF, ("%s P2P_SCANNING: %s [%d]\n", __FUNCTION__, ie_list->Ssid, Idx));
                          ^
/home/akhj/Downloads/DPO/os/linux/../../sta/sync.c: In function &#8216;PeerBeacon&#8217;:
/home/akhj/Downloads/DPO/os/linux/../../sta/sync.c:1933:25: warning: format &#8216;%d&#8217; expects argument of type &#8216;int&#8217;, but argument 4 has type &#8216;ULONG&#8217; [-Wformat=]
                         DBGPRINT(RT_DEBUG_INFO, ("%s PASSIVE SCANNING: %s [%d]\n", __FUNCTION__, bcn_ie_list->Ssid, Bssidx));
                         ^
/home/akhj/Downloads/DPO/os/linux/../../sta/sync.c:2117:11: error: &#8216;SelReg&#8217; undeclared (first use in this function)
      if ( SelReg == 0 )
           ^
make[2]: *** [/home/akhj/Downloads/DPO/os/linux/../../sta/sync.o] Error 1
make[1]: *** [_module_/home/akhj/Downloads/DPO/os/linux] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-3.19.0-31-generic'
make: *** [LINUX] Error 2

any one want to tackle this one? Oh by the way it's an (STA) RT2870STA.dat  issue possibly or kernel defeating frustration..... could be a bad connecting driver from the manufacturer...

just got an update from the seller /manufacturer;

H[COLOR=#000000][FONT=arial]i dear friend,[/FONT][/COLOR][COLOR=#000000][FONT=Arial][FONT=arial]
[/FONT][/FONT][/COLOR]
[COLOR=#000000][FONT=Arial][FONT=arial]The solution methods will be upload to our official website in about 2days.[/FONT][/FONT][/COLOR]
[COLOR=#000000][FONT=Arial][FONT=arial]And we have also contact with the chipset producer and will offer solution complete methods soon.[/FONT][/FONT][/COLOR]
[COLOR=#000000][FONT=Arial][FONT=arial]
[/FONT][/FONT][/COLOR]
[COLOR=#000000][FONT=Arial][FONT=arial]Thanks and best regards[/FONT][/FONT][/COLOR]
[COLOR=#000000][FONT=Arial][FONT=arial]
[/FONT][/FONT][/COLOR]
[COLOR=#000000][FONT=Arial][COLOR=#333333][FONT=arial]**Rebecca**[/FONT][/COLOR]
[COLOR=#333333][FONT=arial]**[IMG]http://hz00.i.aliimg.com/img/pb/637/406/581/581406637_446.jpg[/IMG]**[/FONT][/COLOR]

[FONT=arial][B][[COLOR=#000000]Shenzhen EDUP Electronics Technology Co., Ltd.[/COLOR]]("http://edup.en.alibaba.com/")

MediaTeck is the company responsible for the driver and they are not keeping up with the Linux / Ubuntu kernels above 2.6... Using the guide lines above to see your chip set in linux, " lsusb gives you the 0e8d:76xx similar to above. Make sure it says MediaTek Inc.  Go to this website and using the drop down menu the wifi section is there everyone that  has one of these chipsets from MediaTek shoot them a message. MediaTek does not care about the individule consumer or in any way to update the driver for the current Linux / Ubuntu systems.  Send a message anyway  the more people that get their attention maybe they will be more consumer friendly.  This includes you NetGear built WiFi USB dongles as well...   

[/B][/FONT][/FONT][/COLOR]http://mediatek.com/en/about/contact/  >>>>>choose department scrol down until you see WiFi department<<<<< 

This seems to work....
[https://github.com/jurobystricky/Netgear-A6210](https://github.com/jurobystricky/Netgear-A6210) or open terminal and enter the commands below... make sure you are connected to internet. 

git clone [https://github.com/jurobystricky/Netgear-A6210](https://github.com/jurobystricky/Netgear-A6210)  
cd Netgear-A6210
 
make
sudo make install

be sure to remove all instances of the previous drivers does not seem to like to run two different drivers even after restart... checking to see if my dongle is broken on another pc / laptop... did not get the error messages like I did on the top of this  page...

---

### Post by poruki on 2015-12-17
what is the solution here? cant find anywhere..

---

### Post by aaron36 on 2016-04-03
For those of you who have a Linux / Ubuntu system... I HOPE THERE IS A FIX for the[COLOR=#000000] 0e8d:7612 MediaTek Railink ac1200[/COLOR] with someone at GitHub. Anyway I purchased a TP-Link ac600 and for those of you who have a MT7610u;  148f:761a Ralink chip set here is a fix to get 5Ghz working when you only have 2.4Ghz... I am using 32bit Linux / Ubuntu this only works for the chip set (MT7610u;  148f:761a Ralink) in this thread reply;      It is best to be root; for those novice OPEN A TERMINAL OR Hit [FONT=-apple-system] Ctrl+Alt+T;[/FONT]  (your user name)~$   (type)     su    (enter)     put your     "password"   in, (notice no characters or anything seems to happen when you do this); Now that you are "root" (your user name modified with blue name & the # symbol at the end); type these lines or copy past these lines one at a time and hit enter on each one... I was so happy I found this instruction to make the 5Ghz work as soon as I rebooted the system; CAUTION, MAY NOT WORK ON ALL SYSTEMS  & don't get excited if it takes a while on one or two of the commands.. this is normal; you should not see any error messages either; if you do sorry "No soup for you" final note it is ok to have the wifi dongle plugged in while running the driver setup; as well as Ethernet cable connected.. unplug cable before reboot.  (I had a 2.4g only driver on my wifi dongle working when I ran the commands & did not have Ethernet cable plugged in)  

(Caution) run either 2.4GHz or 5Ghz. if you run both the system seems confused. wants to default to 2.4GHz. I reloaded Linux Mint / Ubuntu 14.04.4 LTS Trusty & only loaded my 5GHz wifi.. on the PC. 

[LEFT][COLOR=#444444][FONT=Consolas][FONT=inherit]mkdir ~ / src[/FONT][/FONT][/COLOR]
[COLOR=#444444][FONT=Consolas][FONT=inherit]cd ~ / src[/FONT][/FONT][/COLOR]
[COLOR=#444444][FONT=Consolas][FONT=inherit][FONT=inherit]git clone [/FONT][/FONT][[FONT=inherit][FONT=inherit]https://github.com/Myria-de/mt7610u_wifi_sta_v3002_dpo_20130916.git[/FONT][/FONT]]("https://github.com/Myria-de/mt7610u_wifi_sta_v3002_dpo_20130916.git")[/FONT][/COLOR]
[COLOR=#444444][FONT=Consolas][FONT=inherit]cd mt7610u_wifi_sta_v3002_dpo_20130916[/FONT][/FONT][/COLOR]
[COLOR=#444444][FONT=Consolas][FONT=inherit]sudo make clean[/FONT][/FONT][/COLOR]
[COLOR=#444444][FONT=Consolas][FONT=inherit]sudo make[/FONT][/FONT][/COLOR]
[COLOR=#444444][FONT=Consolas][FONT=inherit][FONT=inherit]sudo make install

(this is now set up for those who might not be "root") 
(When I updated my system "blue shield lower corner mint" I seem to have lost my 5g wifi I will keep coming back with fixes as I get them, good luck) [/FONT][/FONT][/FONT][/COLOR]
[COLOR=#000000][FONT=inherit]
[/FONT][/COLOR][COLOR=#000000][FONT=monospace](don't forget to hit enter after each command and reboot when finished; try with dongle unplugged also during the "sudo" commands; If your own router has 2.4G and 5G set up, the system [/FONT][/COLOR][COLOR=#000000][FONT=monospace]should see both "Ubuntu can be an unforgiving.... " ; this has been updated since, sorry for those who have not returned to review) [/FONT][/COLOR]
[/LEFT]

---

### Post by aaron36 on 2016-04-03
Read the entire thread i am asking for help sorry if i don't have a solution yet...

---

### Post by jeremy31 on 2016-04-03
Have you tried [https://github.com/jurobystricky/Netgear-A6210](https://github.com/jurobystricky/Netgear-A6210) the code looks to support 0e8d:7612 

There may be a limited range of kernels it works on but should work in 3.19 or 4.2

---

### Post by aaron36 on 2016-04-03
reply to Jeremy31... It would seem if you keep your kernel within the 3.19 through 4.2 range should work ok I am checking the GitHub site now. if it works with the 5Ghz we have a winner...

---

### Post by Trent T on 2017-03-07
Hi all,

I had some luck with a variation on Chili555's answer from AskUbuntu.com.  Since that post, the driver has been updated with a 'u' suffix;
This procedure worked for me for a ralink-148f7601 wifi adapter, using Ubuntu 16.04 32-bit.

[http://askubuntu.com/questions/457061/ralink-148f7601-wifi-adapter-installation](http://askubuntu.com/questions/457061/ralink-148f7601-wifi-adapter-installation)

Thanks Chili555!  You're the greatest!

"
I suggest you get a temporary internet connection, ethernet, tethered or whatever is available. Then do:

[PHP]sudo apt-get install linux-headers-generic build-essential git
git clone [https://github.com/porjo/mt7601u.git](https://github.com/porjo/mt7601u.git) 
cd mt7601u/src
make
sudo make install
sudo mkdir -p /etc/Wireless/RT2870STA/
sudo cp RT2870STA.dat /etc/Wireless/RT2870STA/
sudo modprobe mt7601Usta
[/PHP]
Your wireless should now be working.
You have compiled the driver for your current kernel version only. When Update Manager installs a later linux-image, after the required reboot, you must re-compile:

[PHP]cd mt7601u/src
sudo make clean
sudo make
sudo make install
sudo modprobe mt7601Usta[/PHP]

Please retain the files and these instructions for that time.

chili555

Hope that helps someone
Trent T

---

