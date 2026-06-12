---
title: "installing Realtek wireless adapter RTL8188CE for toshiba satelite c50, tread"
date: 2013-11-01
forum: Hardware
---

### Post by moje_meno2000 on 2013-11-01
I tried everything on thred [http://ubuntuforums.org/showthread.php?t=1604101&page=6](http://ubuntuforums.org/showthread.php?t=1604101&page=6)  nothing helped.
I did: 
sudo apt-get update
sudo apt-get install build-essential
(after finding out)
(ubuntu@ubuntu:~$ uname -r)
(3.8.0-32-generic)
sudo apt-get install linux-image-3.8.0-32-generic
downloaded:  RTL8188CE 
from [http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=48&PFid=48&Level=5&Conn=4&DownTypeID=3&GetDown=false&Downloads=true](http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=48&PFid=48&Level=5&Conn=4&DownTypeID=3&GetDown=false&Downloads=true)
unpacked and entered in directory
sudo su
make clean
make
make install
but after make I get this massege:

ubuntu@ubuntu:~/Desktop/rtl_92ce_92se_92de_8723ae_88ee_linux_mac80211_0012.0207.2013$ make
make -C /lib/modules/3.8.0-32-generic/build M=/home/ubuntu/Desktop/rtl_92ce_92se_92de_8723ae_88ee_linux_mac80211_0012.0207.2013 modules
make[1]: Entering directory `/usr/src/linux-headers-3.8.0-32-generic'
  CC [M]  /home/ubuntu/Desktop/rtl_92ce_92se_92de_8723ae_88ee_linux_mac80211_0012.0207.2013/base.o
In file included from /home/ubuntu/Desktop/rtl_92ce_92se_92de_8723ae_88ee_linux_mac80211_0012.0207.2013/base.c:39:0:
/home/ubuntu/Desktop/rtl_92ce_92se_92de_8723ae_88ee_linux_mac80211_0012.0207.2013/pci.h:247:15: error: expected &#8216;=&#8217;, &#8216;,&#8217;, &#8216;;&#8217;, &#8216;asm&#8217; or &#8216;__attribute__&#8217; before &#8216;rtl_pci_probe&#8217;
make[2]: *** [/home/ubuntu/Desktop/rtl_92ce_92se_92de_8723ae_88ee_linux_mac80211_0012.0207.2013/base.o] Error 1
make[1]: *** [_module_/home/ubuntu/Desktop/rtl_92ce_92se_92de_8723ae_88ee_linux_mac80211_0012.0207.2013] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-3.8.0-32-generic'
make: *** [all] Error 2
ubuntu@ubuntu:~/Desktop/rtl_92ce_92se_92de_8723ae_88ee_linux_mac80211_0012.0207.2013$ 


my system information are:

see next post!

---

### Post by moje_meno2000 on 2013-11-01
my system looks like this:
   ubuntu@ubuntu:~$ cat /etc/lsb-release; uname -a 
 DISTRIB_ID=Ubuntu 
 DISTRIB_RELEASE=12.04 
 DISTRIB_CODENAME=precise 
 DISTRIB_DESCRIPTION="Ubuntu 12.04.3 LTS" 
 Linux ubuntu 3.8.0-32-generic #47~precise1-Ubuntu SMP Wed Oct 2 16:19:35 UTC 2013 x86_64 x86_64 x86_64 GNU/Linux 
 ubuntu@ubuntu:~$ sudo lshw -C network 
 [sudo] password for ubuntu:  
   *-network UNCLAIMED      
        description: Network controller 
        product: RTL8188EE Wireless Network Adapter 
        vendor: Realtek Semiconductor Co., Ltd. 
        physical id: 0 
        bus info: pci@0000:08:00.0 
        version: 01 
        width: 64 bits 
        clock: 33MHz 
        capabilities: pm msi pciexpress bus_master cap_list 
        configuration: latency=0 
        resources: ioport:3000(size=256) memory:d3400000-d3403fff 
   *-network 
        description: Ethernet interface 
        product: QCA8171 Gigabit Ethernet 
        vendor: Qualcomm Atheros 
        physical id: 0 
        bus info: pci@0000:09:00.0 
        logical name: eth0 
        version: 10 
        serial: 7c:05:07:ff:af:54 
        size: 100Mbit/s 
        capacity: 1Gbit/s 
        width: 64 bits 
        clock: 33MHz 
        capabilities: pm pciexpress msi msix bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation 
        configuration: autonegotiation=on broadcast=yes driver=alx driverversion=1.2.3 duplex=full firmware=N/A ip=10.0.0.4 latency=0 link=yes multicast=yes port=twisted pair speed=100Mbit/s 
        resources: irq:18 memory:d1000000-d103ffff ioport:2000(size=128) 
 ubuntu@ubuntu:~$ lspci -nn | grep -e 0280 -e 0200 
 08:00.0 Network controller [0280]: Realtek Semiconductor Co., Ltd. RTL8188EE Wireless Network Adapter [10ec:8179] (rev 01) 
 09:00.0 Ethernet controller [0200]: Qualcomm Atheros QCA8171 Gigabit Ethernet [1969:10a1] (rev 10) 
 ubuntu@ubuntu:~$ lsusb 
 Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub 
 Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub 
 Bus 003 Device 002: ID 0458:003a KYE Systems Corp. (Mouse Systems) NetScroll+ Mini Traveler / Genius NetScroll 120 
 Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub 
 Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub 
 Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub 
 Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub 
 Bus 001 Device 003: ID 058f:6366 Alcor Micro Corp. Multi Flash Reader 
 Bus 001 Device 004: ID 04f2:b3b1 Chicony Electronics Co., Ltd  
 ubuntu@ubuntu:~$ iwconfig 
 eth0      no wireless extensions. 
  
 lo        no wireless extensions. 
  
 ubuntu@ubuntu:~$ rfkill list all 
 ubuntu@ubuntu:~$ lsmod 
 Module                  Size  Used by 
 rfcomm                 47864  0  
 bnep                   18258  2  
 bluetooth             247165  10 rfcomm,bnep 
 parport_pc             28284  0  
 ppdev                  17113  0  
 nls_iso8859_1          12713  1  
 nvidia               9430169  39  
 uvcvideo               82214  0  
 videobuf2_core         40785  1 uvcvideo 
 joydev                 17613  0  
 i915                  620571  2  
 drm_kms_helper         49597  1 i915 
 videodev              130053  2 uvcvideo,videobuf2_core 
 drm                   287564  5 nvidia,i915,drm_kms_helper 
 coretemp               13596  0  
 snd_hda_codec_hdmi     37463  1  
 snd_hda_codec_idt      71153  0  
 alx                    73230  0  
 snd_hda_intel          44339  3  
 snd_hda_codec         141761  3 snd_hda_codec_hdmi,snd_hda_codec_idt,snd_hda_intel 
 videobuf2_vmalloc      13056  1 uvcvideo 
 sparse_keymap          13890  0  
 videobuf2_memops       13202  1 videobuf2_vmalloc 
 mac_hid                13253  0  
 mdio                   13807  1 alx 
 i2c_algo_bit           13564  1 i915 
 video                  19652  1 i915 
 wmi                    19256  0  
 kvm_intel             137899  0  
 snd_hwdep              13668  1 snd_hda_codec 
 kvm                   455932  1 kvm_intel 
 snd_pcm               102477  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec 
 mei                    41820  0  
 snd_seq_midi           13324  0  
 snd_rawmidi            30417  1 snd_seq_midi 
 psmouse                97873  0  
 lpc_ich                17144  0  
 serio_raw              13215  0  
 snd_seq_midi_event     14899  1 snd_seq_midi 
 snd_seq                61930  2 snd_seq_midi,snd_seq_midi_event 
 snd_timer              29989  2 snd_pcm,snd_seq 
 snd_seq_device         14497  3 snd_seq_midi,snd_rawmidi,snd_seq 
 snd                    69533  16 snd_hda_codec_hdmi,snd_hda_codec_idt,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device 
 soundcore              12680  1 snd 
 ghash_clmulni_intel    13259  0  
 cryptd                 20501  1 ghash_clmulni_intel 
 snd_page_alloc         18798  2 snd_hda_intel,snd_pcm 
 microcode              23017  0  
 lp                     17799  0  
 parport                46562  3 parport_pc,ppdev,lp 
 usb_storage            61749  0  
 hid_generic            12540  0  
 usbhid                 47346  0  
 hid                   105582  2 hid_generic,usbhid 
 ahci                   25879  4  
 libahci                31606  1 ahci 
 ubuntu@ubuntu:~$

Please anybody have a clue? This is torture. I am starting to  hate both Toshiba and Ubuntu.

---

### Post by kurt18947 on 2013-11-01
Here is a thread involving that chipset that is marked "solved".  It doesn't appear a common chip.

[http://ubuntuforums.org/showthread.php?t=2162026](http://ubuntuforums.org/showthread.php?t=2162026)

---

### Post by moje_meno2000 on 2013-11-01
I checked that out ([http://ubuntuforums.org/showthread.php?t=2162026](http://ubuntuforums.org/showthread.php?t=2162026)) also 

[http://ubuntuforums.org/showthread.php?t=2176052](http://ubuntuforums.org/showthread.php?t=2176052)
[http://ubuntuforums.org/showthread.php?p=12729812#post12729812](http://ubuntuforums.org/showthread.php?p=12729812#post12729812)
[http://ubuntuforums.org/showthread.php?t=1604101&page=3](http://ubuntuforums.org/showthread.php?t=1604101&page=3)
[http://askubuntu.com/questions/342076/step-by-step-ubuntu-12-04-install-of-realtek-rtl8188ce-driver](http://askubuntu.com/questions/342076/step-by-step-ubuntu-12-04-install-of-realtek-rtl8188ce-driver)

not helping

even hack in source code from 
[http://www.perseosblog.com/en/posts/solving-connection-problem-with-realtek-wifi-card-rtl8188ce-rtl8192ce-rtl8191se-and-rtl8192de-on-debian-ubuntu-and-derivatives/](http://www.perseosblog.com/en/posts/solving-connection-problem-with-realtek-wifi-card-rtl8188ce-rtl8192ce-rtl8191se-and-rtl8192de-on-debian-ubuntu-and-derivatives/)

did not help.

I gues I should not buy Toshiba? :)

---

### Post by moje_meno2000 on 2013-11-01
Ah yes, after hack in [http://www.perseosblog.com/en/posts/solving-connection-problem-with-realtek-wifi-card-rtl8188ce-rtl8192ce-rtl8191se-and-rtl8192de-on-debian-ubuntu-and-derivatives/](http://www.perseosblog.com/en/posts/solving-connection-problem-with-realtek-wifi-card-rtl8188ce-rtl8192ce-rtl8191se-and-rtl8192de-on-debian-ubuntu-and-derivatives/)
at least error mesage is diffrent:
root@ubuntu:/home/ubuntu/Desktop/Untitled Folder/rtl_92ce_92se_92de_8723ae_88ee_linux_mac80211_0012.0207.2013# make
make -C /lib/modules/3.8.0-32-generic/build M=/home/ubuntu/Desktop/Untitled Folder/rtl_92ce_92se_92de_8723ae_88ee_linux_mac80211_0012.0207.2013 modules
make[1]: Entering directory `/usr/src/linux-headers-3.8.0-32-generic'
/usr/src/linux-headers-3.8.0-32-generic/arch/x86/Makefile:103: CONFIG_X86_X32 enabled but no binutils support
make[1]: *** No rule to make target `Folder/rtl_92ce_92se_92de_8723ae_88ee_linux_mac80211_0012.0207.2013'.  Stop.
make[1]: Leaving directory `/usr/src/linux-headers-3.8.0-32-generic'
make: *** [all] Error 2
root@ubuntu:/home/ubuntu/Desktop/Untitled Folder/rtl_92ce_92se_92de_8723ae_88ee_linux_mac80211_0012.0207.2013# sudo make install
make -C /lib/modules/3.8.0-32-generic/build M=/home/ubuntu/Desktop/Untitled Folder/rtl_92ce_92se_92de_8723ae_88ee_linux_mac80211_0012.0207.2013 modules
make[1]: Entering directory `/usr/src/linux-headers-3.8.0-32-generic'
/usr/src/linux-headers-3.8.0-32-generic/arch/x86/Makefile:103: CONFIG_X86_X32 enabled but no binutils support
make[1]: *** No rule to make target `Folder/rtl_92ce_92se_92de_8723ae_88ee_linux_mac80211_0012.0207.2013'.  Stop.
make[1]: Leaving directory `/usr/src/linux-headers-3.8.0-32-generic'
make: *** [all] Error 2
root@ubuntu:/home/ubuntu/Desktop/Untitled Folder/rtl_92ce_92se_92de_8723ae_88ee_linux_mac80211_0012.0207.2013#

---

### Post by moje_meno2000 on 2013-11-01
root@ubuntu:/home/ubuntu/Desktop/Untitled Folder/rtl_92ce_92se_92de_8723ae_88ee_linux_mac80211_0012.0207.2013# make
make -C /lib/modules/3.8.0-32-generic/build M=/home/ubuntu/Desktop/Untitled Folder/rtl_92ce_92se_92de_8723ae_88ee_linux_mac80211_0012.0207.2013 modules
make[1]: Entering directory `/usr/src/linux-headers-3.8.0-32-generic'
/usr/src/linux-headers-3.8.0-32-generic/arch/[COLOR=#ff0000]x86[/COLOR]/Makefile:103: CONFIG_X86_X32 enabled but no binutils support
make[1]: *** No rule to make target `Folder/rtl_92ce_92se_92de_8723ae_88ee_linux_mac80211_0012.0207.2013'.  Stop.
make[1]: Leaving directory `/usr/src/linux-headers-3.8.0-32-generic'
make: *** [all] Error 2
root@ubuntu:/home/ubuntu/Desktop/Untitled Folder/rtl_92ce_92se_92de_8723ae_88ee_linux_mac80211_0012.0207.2013# 



x86?  I am on 64bit machine. Could be this problem?

---

### Post by kurt18947 on 2013-11-01
One alternative would be to buy a USB adapter known to be plug 'n' play, e.g. something based on an RT5370, Realtek RTL8192SU, RTL8192CU(with some tweaks) or certain Atheros chipsets.  Another alternative would be to replace the card in your laptop.  I don't know how fussy Toshiba is,  I know some vendors whitelist wireless cards in their BIOS so that only certain cards will be recognized.  Eventually your card will likely be supported, it may take a few months though.

---

### Post by moje_meno2000 on 2013-11-01
you thing swiching to ubuntu 13.04 would make any diffrence?

---

### Post by kurt18947 on 2013-11-01
> **moje_meno2000 said:**
> you thing swiching to ubuntu 13.04 would make any diffrence?

I don't know but I doubt it. Support for current production wifi devices usually improves over time.  You could always create a live CD/USB  and try it.

---

### Post by moje_meno2000 on 2014-02-16
ok I finaly manage to solve it. Thanks to this post on similary forum:

             The driver you're looking for is no longer maintained by  RealTek, so I've put it up on GitHub where I maintain it from version to  version so that it compiles and works.  So far, I as well as several  others have had good experience using this driver.  You can find the  driver [here]("https://github.com/FreedomBen/rtl8188ce-linux-driver") on Github:  [https://github.com/FreedomBen/rtl8188ce-linux-driver](https://github.com/FreedomBen/rtl8188ce-linux-driver)
  There are full instructions located on the project page (that link will take you there) and also in the README.md file that comes with the checkout.
  The commands you see in the instructions should be entered into a  terminal prompt, and enter should be pressed at the end of each line.
  Please let me know of any issues you encounter and I'll try to help.
      


It worked perfectly for me, shout out for autor: FreedomBen

---

