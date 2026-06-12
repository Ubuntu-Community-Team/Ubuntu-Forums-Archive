---
title: "Bluetooth driver Asus AT3N7A-I NVidia ION Ubuntu 9.04"
date: 2009-09-12
forum: Installation &amp; Upgrades
---

### Post by erwinew on 2009-09-12
Hi all,

My Asus AT3N7A-I on-board bluetooth won't be recognized on Ubuntu 9.04 64-bit. Can you please give me some hints? Here is some addition info:

htpc@htpc:~$ sudo hciconfig
htpc@htpc:~$ sudo hcitool dev
Devices:
htpc@htpc:~$ sudo hidd --search
Searching ...
htpc@htpc:~$ 

htpc@htpc:~$ sudo hciconfig
htpc@htpc:~$ 

htpc@htpc:~$ locate bluez-utils
/usr/share/doc/bluez-utils
/usr/share/doc/bluez-utils/AUTHORS
/usr/share/doc/bluez-utils/README
/usr/share/doc/bluez-utils/changelog.Debian.gz
/usr/share/doc/bluez-utils/copyright
/var/cache/apt/archives/bluez-utils_4.32-0ubuntu4_all.deb
/var/lib/dpkg/info/bluez-utils.list
/var/lib/dpkg/info/bluez-utils.md5sums
/var/lib/dpkg/info/bluez-utils.postrm
/var/lib/dpkg/info/bluez-utils.preinst

Note: A simple Trust USB bluetooth adapter works fine, but the on-board won't...

Any ideas?

---

### Post by Fafler on 2009-09-12
Do
```
lspci
lsusb
```
and post results here.

---

### Post by Drikus on 2009-09-12
Is bluetooth enabled in bios ?

Onboard Bluetooth [Enabled]
Allows you to enable or disable the onboard Bluetooth controller.
Configuration options: [Enabled] [Disabled]

But the there seems to be some issue's with windows aswell. [http://www.anandtech.com/printarticle.aspx?i=3630](http://www.anandtech.com/printarticle.aspx?i=3630)

BTW Found this thread because I was acquiring information about the Asus AT3N7A-I and linux compatibility . Apart from the bluetooth does everything else works ?

---

### Post by erwinew on 2009-09-13
Hi all,

Thanks for your reply. Yes, bluetooth is enabled in the BIOS.

Here is the output of the requested commands:

> htpc@htpc:~$ **lspci**
00:00.0 Host bridge: nVidia Corporation MCP79 Host Bridge (rev b1)
00:00.1 RAM memory: nVidia Corporation MCP79 Memory Controller (rev b1)
00:03.0 ISA bridge: nVidia Corporation MCP79 LPC Bridge (rev b2)
00:03.1 RAM memory: nVidia Corporation MCP79 Memory Controller (rev b1)
00:03.2 SMBus: nVidia Corporation MCP79 SMBus (rev b1)
00:03.3 RAM memory: nVidia Corporation MCP79 Memory Controller (rev b1)
00:03.5 Co-processor: nVidia Corporation MCP79 Co-processor (rev b1)
00:04.0 USB Controller: nVidia Corporation MCP79 OHCI USB 1.1 Controller (rev b1)
00:04.1 USB Controller: nVidia Corporation MCP79 EHCI USB 2.0 Controller (rev b1)
00:06.0 USB Controller: nVidia Corporation MCP79 OHCI USB 1.1 Controller (rev b1)
00:06.1 USB Controller: nVidia Corporation MCP79 EHCI USB 2.0 Controller (rev b1)
00:08.0 Audio device: nVidia Corporation MCP79 High Definition Audio (rev b1)
00:09.0 PCI bridge: nVidia Corporation MCP79 PCI Bridge (rev b1)
00:0b.0 IDE interface: nVidia Corporation MCP79 SATA Controller (rev b1)
00:10.0 PCI bridge: nVidia Corporation MCP79 PCI Express Bridge (rev b1)
00:15.0 PCI bridge: nVidia Corporation MCP79 PCI Express Bridge (rev b1)
02:00.0 VGA compatible controller: nVidia Corporation Device 087d (rev b1)
03:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 03)

htpc@htpc:~$ **lsusb**
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 003: ID 0dc6:2301 Precision Squared Technology Corp. 
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 002: ID 0781:5406 SanDisk Corp. Cruzer Micro 1/4GB Flash Drive
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 002: ID 0cf3:3000 Atheros Communications, Inc. 
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

I'm currently looking for a bluetooth solution for Windows 7 RC1 as well, because I can't get it up and running. The rest of the hardware is fully operational with Windows 7 RC1. 

I'm also fighting with HDMI audio and bluetooth with Ubuntu 9.04. I tried the following drivers from the NVidia site, all with the same problem:
[Linux Display Driver Version 190.32]("http://www.nvidia.com/object/linux_display_amd64_190.32.html") BETA
[B][Linux Display Driver Version 185.18.36]("http://www.nvidia.com/object/linux_display_amd64_185.18.36.html")
[/B]I'd like to use this motherboard as a HTPC, but I can't use it as long as HDMI does not work with Ubuntu. The onboard 3,5mm jack audio sounds crap, so that's not a solution. I'll keep it dual boot for the time being.

---

### Post by Minzor on 2009-09-14
Hi all,

i recently bought this Board to build a Linux-based HTPC. As i can say the only thing that refused to work is the "onboard" bluetooth.
BT support is enabled in bios and activated in kernelconfig. However i did not test an other bt dongle now.

The Device seems to be the Atheros found in lsusb:
Bus 003 Device 002: ID 0cf3:3000 Atheros Communications, Inc. 

The inf from the Windowsdriver downloaded from Asus shows the same ID 0cf3.
I searched a lot and found that there is a AT3011 Chipset since 2007 that should work with the standard HCI Kernel Layer. 

Can someone verify that the Hardware is working on the Windows-Plattform with the Asus  Driver?

By the Way: The Sound from the 3,5 Jack sound well for me, try to update to the latest kernel, there is much work done to the HD audio Driver.

cu

jose

---

### Post by Drikus on 2009-09-14
3,5mm jack audio isn't an option for me either, but for the hdmi issues good chance that you might want to opt for a newer alsa version see [here]("https://answers.launchpad.net/ubuntu/+source/alsa-driver/+question/81970") and for the usb ids you might want to run sudo [update-usbids]("http://www.ubuntugeek.com/update-pciids-update-usbids-download-a-newer-version-of-the-pci-and-usb-id-list.html").

---

### Post by erwinew on 2009-09-17
The on-board bluetooth does not work with Windows 7 as well. I found a driver on the Asus CD, but that works only with Windows XP and Vista, not Ubuntu or Windows 7. Windows 7 does not display a bluetooth device in the Device manager. (Yes, it's turned on in the BIOS) So I've no idea if the bluetooth hardware works.

In the mean time I figured out that the on-board 3,5mm audio sounds beter than audio over HDMI (with Windows 7) and a Samsung LCD. The high frequencies sounds beter, however, there is a lot of noice on the 3,5mm audio plug. Especially by putting the amplifier at a high volume in combination with moving the mouse or start some heavy processing / graphics. It sounds stupid, but you can hear the mouse moving! I recognize this garbage on many motherboards. I think an external USB/Firewire/Optical audio card will be a solution.

Did you ever try to play a h.264 video, play a youtube HD video or play a HD .ts file (recorded with a Humax 5050c) with Ubuntu? No go. You're lucky if it displays a frame every second. The player does not matter: I tried Kino as well as VLC, different flash players etc. We cannot play video's from [http://www.sbs6gemist.nl](http://www.sbs6gemist.nl), because it uses Silverlight, a Microsoft product. All of this works perfect with Windows 7 and Media player out of the box. I think this is related to the full HDCP capability which is missing in Ubuntu. This is a major problem for me, so I think it's too early for Ubuntu now.

---

### Post by Minzor on 2009-09-17
I have to state that i am not using ubuntu. 
My distribution is Gentoo, but i dont see a difference.

If you have problems playing HD Videos pleas ensure that you have VDPAU activated in your programs.
I am using XBMC for playing/streaming Videos and streaming live TV over wlan via my VDR Server.
I did not try Windows but with Linux you can use all Power that this Hardware offers.
My only Problem is the Bluetooth but i can use a small usb adaptor for that.

---

### Post by Minzor on 2009-09-17
It seems that the USB-ID of the Atheros Device is missing in the Linux Kernel. I have submitted that Device ID here:
[http://www.linux-usb.org/usb-ids.html](http://www.linux-usb.org/usb-ids.html)

and hope for including in the next Kernel Release.

Here is a Guide for including the missind ID in Windows with widcom stack.
[http://www.jonsguides.com/bluetooth/devices.html](http://www.jonsguides.com/bluetooth/devices.html)

---

### Post by Drikus on 2009-09-17
> **erwinew said:**
> 

Did you ever try to play a h.264 video, play a youtube HD video or play a HD .ts file (recorded with a Humax 5050c) with Ubuntu? No go. You're lucky if it displays a frame every second. The player does not matter: I tried Kino as well as VLC, different flash players etc. We cannot play video's from [http://www.sbs6gemist.nl](http://www.sbs6gemist.nl), because it uses Silverlight, a Microsoft product. All of this works perfect with Windows 7 and Media player out of the box. I think this is related to the full HDCP capability which is missing in Ubuntu. This is a major problem for me, so I think it's too early for Ubuntu now.

For silverlight install [http://www.go-mono.com/moonlight/](http://www.go-mono.com/moonlight/) (1.99.3) after install update again to 1.99.3, then you able to play the sbs streams. The sbs6 streams are working fine here this is not on an a AT3N7A-I because I ordered the board yesterday evening. 

For the rest of your issues it's important to enable vdpau, for example mplayer -vo xv vpdau  /media/whatever.mkv. Maybe you may find [this]("http://www.strengholt-online.nl/xbmc-live-op-nvidia-ion/") resource helpful.

---

### Post by konni on 2009-11-19
any progress on bluetooth? 
can i add the pci-id to a module and recompile it?
tried with btusb, compiles fine but does not recognize the device.

---

### Post by Minzor on 2009-11-25
The same for me, no Progress here. 8(

---

### Post by erwinew on 2009-11-29
I'd like to share my (disaster) experiences with you.

1. Installing the latest Ubuntu 9.04 updates resolved the Bluetooth problems partially. Now I can connect to my Samsung M150 mobile, but I cannot browse in Ubuntu thru the pictures directory on my mobile phone. I cannot send pictures, video's or files from my mobile to Ubuntu, because it cannot connect.

2. Upgrading from Ubuntu 9.04 to 9.10 ends up in a disaster on the Asus AT3N7A-I motherboard. I only see a blinking text message (without a GUI) during the boot and no further commandline logins are accepted. Garbage, because Ubuntu became unusable without reinstalling it from scratch. I don't have time to look into that ****, it should work out of the box, Linux guru's! It's not user friendly as it looks like.

3. Another disaster of installing Ubuntu 9.10 on my brand new I7 computer with two harddisks in RAID 0 is the message: "Unable to install Grub in /dev/mapper/isw..." "This is a fatal error."  Ok, it's not usable on my second computer as well... Windows 7 64-bit works perfect on that machine.

4. The good news is that Bluetooth works perfect with Windows 7 (64-bit) after installing a new Bluetooth driver on the AT3N7A-I from the Asus website. Drivers are available for Windows XP, Vista and W7 in 32-bit as well as 64-bit.

Browse to: [http://support.asus.com/download/Download.aspx?SLanguage=en-us](http://support.asus.com/download/Download.aspx?SLanguage=en-us)
Product: Motherboard
Series: Intel CPU Onboard
Models: AT3N7A-I
Select your Windows version. (ASUS did _**NOT**_ create Linux Bluetooth drivers!)
Bluetooth > Bluetooth Driver V6.8.609.101 > Download

Double click on the downloaded file and install. Reboot after the installation. Then you'll see a bluetooth icon in the system tray beside the clock. Enable Bluetooth on your mobile phone and connect to the mobile by right clicking on this icon > Add a device. Follow the instructions and use Send a file and Receive a file to transfer files, or install the communication software delivered with your mobile phone. (Of cource, this is in my case Samsung PC Studio for Windows only)

5. My conclusion: The Bluetooth hardware on the Asus AT3N7A-I motherboard works fine with the correct driver. No Ubuntu driver = unusable Bluetooth. I'm unable to boot Ubuntu 9.10 after a simple upgrade from 9.04 to 9.10 and I cannot install it on my I7 computer, so I said exit to Ubuntu and switched back to Windows 7.

-- Erwin

---

### Post by xout on 2009-12-06
regarding bluetooth:

it could be that asus integrated a dongle that does not come along with its own firmware. therefore it would be necessary to load the firmware each time the device gets initialized. i researched a bit and found out that atheros submitted a kernel patch for firmware loading for their bluetooth devices a couple of days ago. this module is called ath3k.

see: [http://patchwork.kernel.org/patch/62409/]("http://patchwork.kernel.org/patch/62409/")

so far so good. what we need now is a firmware for our dongle, that should be found in the bluez-firmware package. seems like there isn't any yet. at least i could not find anything. but what i found out is that atheros is looking for a someone to build support/firmware for bluetooth on linux. 

see: [http://www.ventureloop.com/ventureloop/jobdetail.php?jobid=27358&utm_source=Indeed&utm_medium=organic&utm_campaign=Indeed](http://www.ventureloop.com/ventureloop/jobdetail.php?jobid=27358&utm_source=Indeed&utm_medium=organic&utm_campaign=Indeed)

so looks like we have to wait a "bit"...
i guess until then i'll have my ion2. XD

---

### Post by Dosch on 2009-12-07
It seems there is a firmware ready but it's just not released.
I found this thread discussing among other things the license of the firmware.

[http://www.spinics.net/lists/linux-bluetooth/msg03816.html](http://www.spinics.net/lists/linux-bluetooth/msg03816.html)

From that I gather that the linux-firmware tree is the one most likely they will commit it too.

---

### Post by xout on 2009-12-07
hey dosch, 

interesting. :)
i'm just about to read through the list. just have to say i love this comment in there XD:

> This is not an error. Just return -ENODEV. Stop spamming dmesg like crazy. This driver is suppose to load a firmware and not operate a nuclear reactor.


---

### Post by prevoj on 2010-01-02
I just managed to get Bluetooth on the ASUS AT3N7A-I working under Mythbuntu 9.10 using the upgraded Linux 2.6.31-16-generic x86_64 kernel. It can probably be done for other versions, this is the only one I have. What I did... I did a search and found this posting after searching on ar3011 linux:
 
[http://groups.google.com/group/linux.kernel/browse_thread/thread/d069d767ee39ce82/2bf7f3f50218ec86?lnk=raot](http://groups.google.com/group/linux.kernel/browse_thread/thread/d069d767ee39ce82/2bf7f3f50218ec86?lnk=raot)
 
I cut the code listed in the posting for ath3k.c and pasted it to a file with the same name. Then I removed all the leading plus signs from the code that were added by diff. I then created a simple Makefile and Kbuild for the ath3k module. Then I did a make followed by a make install. Of course, you all ready have to have your machine set up for building modules before doing the make commands. I then did a modprobe ath3k and then did a dmesg and actually saw the Atheros Bluetooth asking for firmware. I couldn't believe it.
 
I searched on the net and couldn't find any firmware. I went to my Windows machine popped in the AT3N7A-I Support DVD, ran \Drivers\BlueTooth\Vista32\setup.exe on the DVD, I clicked OK to pick my language, then I went to my temp folder while setup was still running and found the Bluetooth Vista Suite.msi that had been unpacked, then I opened the MSI with 7-zip, then I opened Data1.cab and extracted atherosbt.bin from the cab. I then renamed atherosbt.bin to ath3k-1.fw and copied it to the /lib/firmware folder on Mythbuntu.
 
I removed the module with modprobe -r ath3k and added it back with modprobe ath3k. Everything came up, I was shocked. Then I edited /etc/modules and added ath3k so that I have it after every reboot.
 
I'm now happily using my WII controller without an extra Bluetooth dongle.
 
I've attached the source files that I used to build the module. I haven't included the firmware since I didn't know if that's legal to distribute. I couldn't find an answer on the web if it was redistributable or not.

---

### Post by dholt on 2010-01-02
Holy crap man.. Thank you!  That worked flawlessly for me in 64-bit Arch Linux :biggrin:

---

### Post by JeromeL on 2010-01-03
Hi, I have Ubuntu 9.10

I have all files needed.

When I tried modprobe ath3k, i have :
FATAL: Module ath3k not found.


What do i need to do?

---

### Post by prevoj on 2010-01-04
JeromeL,
 
After you did the "make", did you do a "make install" as root or sudo? That should have copied the ath3k.ko module to the correct folder so that modprobe can find it. The default location it copies to should be good for Ubuntu. If you were running a different distribution you might need to change the INSTALL_MOD_DIR to point to a different module destination. By default, it will copy the module to:
 
/lib/modules/`uname -r`/kernel/drivers/bluetooth/

---

### Post by JeromeL on 2010-01-04
> **prevoj said:**
> JeromeL,
 
After you did the "make", did you do a "make install" as root or sudo? That should have copied the ath3k.ko module to the correct folder so that modprobe can find it. The default location it copies to should be good for Ubuntu. If you were running a different distribution you might need to change the INSTALL_MOD_DIR to point to a different module destination. By default, it will copy the module to:
 
/lib/modules/`uname -r`/kernel/drivers/bluetooth/
 
Yes i Did "sudo make install" and the ath3k.ko has been copied in : /lib/modules/`uname -r`/kernel/drivers/bluetooth
 
I use Ubuntu 9.10 karmic.

---

### Post by azkotoki on 2010-01-04
> **JeromeL said:**
> Yes i Did "sudo make install" and the ath3k.ko has been copied in : /lib/modules/`uname -r`/kernel/drivers/bluetooth
 
I use Ubuntu 9.10 karmic.

Same happening to me. Run the following:

  ```
sudo depmod -a
```And then it should load nicely.

---

### Post by JeromeL on 2010-01-04
> **azkotoki said:**
> Same happening to me. Run the following:

  ```
sudo depmod -a
```And then it should load nicely.

Thank you, I will try this afternoon when I come back home.
;)

---

### Post by Minzor on 2010-01-04
> **prevoj said:**
> I just managed to get Bluetooth on the ASUS AT3N7A-I working under Mythbuntu 9.10 using the upgraded Linux 2.6.31-16-generic x86_64 kernel.

Thank you for this nice Howto, i will try your soluton today.

> **prevoj said:**
> 
I'm now happily using my WII controller without an extra Bluetooth dongle.

Hope that my PS3 BT Remote will do the Job as well ;)


cu

---

### Post by JeromeL on 2010-01-04
> **JeromeL said:**
> Thank you, I will try this afternoon when I come back home.
;)

thank you It works good !! ;)

---

### Post by Dosch on 2010-01-04
> **Minzor said:**
> 
Hope that my PS3 BT Remote will do the Job as well ;)

It should do, mine works perfectly now. Although it took me a while to connect it the first time with the "new" BT controller. No idea what I did wrong first.


And thanks prevoj, for figuring out how to get the firmware binary!=D>

---

### Post by asea on 2010-01-05
Many thanks to Prevoj for providing this fix.  Now I can remove my old BT dongle and use the Asus built in one ... my Noah cased XBMC looks sleek again now :P

---

### Post by kamiubu on 2010-01-09
Thank you Prevoj, really nice work...

I follow your guide, everything looks fine, but still no bluetooth in bluetooth-properties :/

dmesg after modprobe ath3k:

[  922.249211] Bluetooth: Atheros AR30XX firmware driver ver 1.0
[  922.249278] usbcore: registered new interface driver ath3k

lsmodprobe | grep ath:
ath3k                   4000  0

uname -a
Linux kami-ht 2.6.31-17-generic #54-Ubuntu SMP Thu Dec 10 17:01:44 UTC 2009 x86_64 GNU/Linux

Any idea, what i miss ?
Thanks

---

### Post by Xian00 on 2010-01-13
Many thanks to prevoj!!
The solution you proposed works perfectly for my bluetooth dongle too!

I bought a [Dikom Micro USB Bluetooth Dongle]("http://www.dikom.it/catalogo.aspx?Prod=255"), which has the chip from Atheros AR3011.
...in fact I found this thread searching for the device usb id as reported by the command 'lsusb': 0cf3:3000

Now it works perfectly... I only had to give the command 'sudo depmod -a' as reported by others.

Thanks again!
Xian

---

### Post by ozzmantsjeh on 2010-01-17
Hi,

I am trying your solution, but when I look at dmesg I am getting:

[   15.827928] usb 3-6: firmware: requesting ath3k-1.fw
[   15.907422] ath3k: probe of 3-6:1.0 failed with error -5
[   15.907492] usbcore: registered new interface driver ath3k


I did make, make install and sudo depmod -a..

Any thoughts?


Edit: Sorry! Didn't read your post right and I didn't have the firmware file. It's working now, thanks!

---

### Post by tangundcash on 2010-01-20
> **kamiubu said:**
> Thank you Prevoj, really nice work...

I follow your guide, everything looks fine, but still no bluetooth in bluetooth-properties :/

dmesg after modprobe ath3k:

[  922.249211] Bluetooth: Atheros AR30XX firmware driver ver 1.0
[  922.249278] usbcore: registered new interface driver ath3k

lsmodprobe | grep ath:
ath3k                   4000  0

uname -a
Linux kami-ht 2.6.31-17-generic #54-Ubuntu SMP Thu Dec 10 17:01:44 UTC 2009 x86_64 GNU/Linux

Any idea, what i miss ?
Thanks

 I got the same problem, and lsusb didn't show "any" ath device.

---

### Post by kaaino on 2010-01-23
For those interested I have just created an open group to gather information on open issues on this motherboard
[https://launchpad.net/~at3n7a-i](https://launchpad.net/~at3n7a-i)

---

### Post by xout on 2010-01-23
> **prevoj said:**
> I just managed to get Bluetooth on the ASUS AT3N7A-I working under Mythbuntu 9.10 using the upgraded Linux 2.6.31-16-generic x86_64 kernel. It can probably be done for other versions, this is the only one I have. What I did... I did a search and found this posting after searching on ar3011 linux:
 
[http://groups.google.com/group/linux.kernel/browse_thread/thread/d069d767ee39ce82/2bf7f3f50218ec86?lnk=raot](http://groups.google.com/group/linux.kernel/browse_thread/thread/d069d767ee39ce82/2bf7f3f50218ec86?lnk=raot)
 
I cut the code listed in the posting for ath3k.c and pasted it to a file with the same name. Then I removed all the leading plus signs from the code that were added by diff. I then created a simple Makefile and Kbuild for the ath3k module. Then I did a make followed by a make install. Of course, you all ready have to have your machine set up for building modules before doing the make commands. I then did a modprobe ath3k and then did a dmesg and actually saw the Atheros Bluetooth asking for firmware. I couldn't believe it.
 
I searched on the net and couldn't find any firmware. I went to my Windows machine popped in the AT3N7A-I Support DVD, ran \Drivers\BlueTooth\Vista32\setup.exe on the DVD, I clicked OK to pick my language, then I went to my temp folder while setup was still running and found the Bluetooth Vista Suite.msi that had been unpacked, then I opened the MSI with 7-zip, then I opened Data1.cab and extracted atherosbt.bin from the cab. I then renamed atherosbt.bin to ath3k-1.fw and copied it to the /lib/firmware folder on Mythbuntu.
 
I removed the module with modprobe -r ath3k and added it back with modprobe ath3k. Everything came up, I was shocked. Then I edited /etc/modules and added ath3k so that I have it after every reboot.
 
I'm now happily using my WII controller without an extra Bluetooth dongle.
 
I've attached the source files that I used to build the module. I haven't included the firmware since I didn't know if that's legal to distribute. I couldn't find an answer on the web if it was redistributable or not.

thanks for the hint! haven't been checking the thread for a while. i just took the patch again and applied it to my kernel sources (2.6.32). afterwards i compiled the module into the kernel. i did that before, but didn't find any useable firmware. but your hint did it! just copied the extracted firmware and everything was immediately up && running after the next reboot.

---

### Post by xout on 2010-02-25
the driver is now included in the 2.6.33 kernel sources.

see: [http://git.kernel.org/?p=linux/kernel/git/stable/linux-2.6.33.y.git;a=tree;f=drivers/bluetooth;h=56ee716255873318b0e1985baaf5a6ac67f991ed;hb=HEAD](http://git.kernel.org/?p=linux/kernel/git/stable/linux-2.6.33.y.git;a=tree;f=drivers/bluetooth;h=56ee716255873318b0e1985baaf5a6ac67f991ed;hb=HEAD)

---

### Post by mac666 on 2010-02-27
> **xout said:**
> the driver is now included in the 2.6.33 kernel sources.

see: [http://git.kernel.org/?p=linux/kernel/git/stable/linux-2.6.33.y.git;a=tree;f=drivers/bluetooth;h=56ee716255873318b0e1985baaf5a6ac67f991ed;hb=HEAD](http://git.kernel.org/?p=linux/kernel/git/stable/linux-2.6.33.y.git;a=tree;f=drivers/bluetooth;h=56ee716255873318b0e1985baaf5a6ac67f991ed;hb=HEAD)

Nice info, how to upgrade to it? 
Im on Karmic x32

---

### Post by xout on 2010-02-27
sorry, can't help you at this point. i'm a 99% gentoo user.
i just checked the ubuntu repos in my vm. seems like there's no 2.6.33 kernel available. but i'm pretty sure there are ways to install it nevertheless. i'd check the forums.

---

### Post by mac666 on 2010-03-06
anyone who can upload the firmware? or host on rapidshare or something? I Cant browse the MSI package, only run in wine.

Or how to do it in Ubuntu? I have 7-zip installed....

---

### Post by sensorama on 2010-03-23
It worked.
Thanks a milion.

---

### Post by Thonyv on 2010-03-25
I am trying to use prevoj's method to install the BT firmware, but I get

  HOSTCC  scripts/basic/fixdep
  HOSTCC  scripts/basic/docproc
  HOSTCC  scripts/basic/hash
  HOSTCC  scripts/kconfig/conf.o
scripts/kconfig/conf.c: In function ‘conf_askvalue’:
scripts/kconfig/conf.c:105: warning: ignoring return value of ‘fgets’, declared with attribute warn_unused_result
scripts/kconfig/conf.c: In function ‘conf_choice’:
scripts/kconfig/conf.c:307: warning: ignoring return value of ‘fgets’, declared with attribute warn_unused_result
  HOSTCC  scripts/kconfig/kxgettext.o
  HOSTCC  scripts/kconfig/zconf.tab.o
  HOSTLD  scripts/kconfig/conf
scripts/kconfig/conf -s arch/x86/Kconfig
gcc   -m elf_i386  ath3k.c   -o ath3k
cc1: error: unrecognized command line option "-m"
make: *** [ath3k] Error 1


when I run the make command. Could there be something else I need to compile this file?

---

### Post by cubatilles on 2010-03-31
Hey dudes,

I've had the same problem with bluetooth in ubuntu 9.10. After some headaches, I've finally decided to try Windows7, to give it a try. But it was a bad decision. Windows is windows, and that's why I left it some years ago. Full of crap, unstable (explorer crashed 3 times in an hour), slow, and hard to find things and tools when you're familiarized with gnome and terminal.

So I decided to get back to ubuntu and try to find another solution for the bluetooth. The funny thing is, when I installed Windows7 I installed the AT3N7A-I bluetooth drivers from Asus website. And that was enough for Ubuntu to make Bluetooth work when I reinstalled it. Ubuntu just detected the bluetooth hardware and configured it just like any other device, so it was available when installation finished.

I guess when you install windows drivers it uplaods the firmware to the bluetooth hardware and it remains there. So then you can make a linux fresh install and it will work flawlessly.

I tried to pair a bluetooth device and Ubuntu detected it perfectly.

So I wanted to share my experience. If you have problems extracting the frmware and using the guide on this thread, just another method:

1-Install windows (I guess any version should do the work.
2-Install the bluetooth driver from the disc or downloaded fron the Asus website.
3-Bye bye windows, make a fresh Ubuntu install, you can delete completely the windows partition.
4-Ubuntu will detect and install the bluetooth dongle with no problems.

I don't know if this was obvious to you or not, but it surprised me, so here it is.

Anyways I have to solve my Audio problem yet. Any ideas? I'm using the analog 3,5mm jack cable and it works ok, but it makes a "crack" "plop" noise when I play a movie, boot ubuntu, play a music file... it's just on the beggining, then it plays fine. Anyways I'll try to install latest alsa package when I get home, but dunno if any of you had the same problem and solved it updating alsa?

cya.

---

### Post by furinkan on 2010-04-10
So once one upgrades to the new kernel, this mobo works perfectly? Has the sound issue been resolved with the HDMI?

I'm just curious because this is a nice mobo that I would like to use for a multimedia project.

---

### Post by DerLobi on 2010-05-10
I had it working under Karmic but soon didn't need the Bluetooth anymore.

Now I use Lucid and would like to use a bluetooth keyboard.

I have the firmware in /lib/firmware, i did ```
sudo make
``` and ```
sudo make install
``` without errors
I did ```
sudo depmod -a
``` but the .ko is not in the directory /lib/modules/2.6.32-22-generic/kernel/drivers/bluetooth

Did anything change in Lucid or what did I do wrong?

---

### Post by jd1024 on 2010-05-19
Installshield isn't exporting to my Temp or Installshield folder. I tried 7-zip and a couple exe extractors but nothing works. can someone email the firmware.

---

### Post by asea on 2011-11-25
Hi all,
 
I posted on page 3 of this thread that all was ok, however I've just upgraded to 11.10 and it's all broken again :(.
 
I've tried using the original fix of adding firmware, depmod etc. but no joy. It was working under 11.04, but 11.10 has the new 3.0 kernel. 
 
Anyone else got the same problem, or has everyone upgraded their HTPC mobo from this Asus one?
 
Cheers.

---

### Post by raav on 2011-12-30
Same here. It's broken in 11.10 and I can't find a way to get it working.

Edit: Well I found a solution... I can boot up Ubuntu 11.04 live CD. It loads all the drivers and uploads the firmware which stays there until the computer is powered off.
After rebooting into 11.10, bluetooth is working.

---

### Post by nedflenders on 2012-06-14
Since this post hasn't been updated for some time, I figured I let people know.
Got it working on Ubuntu 11.10.
kernel 3.0.0-21-generic

$ lsusb
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 0424:2524 Standard Microsystems Corp. USB MultiSwitch Hub
Bus 003 Device 002: ID 0471:20d9 Philips (or NXP) 
Bus 003 Device 003: ID 0cf3:3005 Atheros Communications, Inc. 
Bus 002 Device 003: ID 10d5:000d Uni Class Technology Co., Ltd 
Bus 002 Device 004: ID 045e:00dd Microsoft Corp. Comfort Curve Keyboard 2000 V1.0
Bus 002 Device 005: ID 046d:c066 Logitech, Inc. 

I can see the bluetooth device (this is a good sign):

$ sudo hciconfig 
hci0:    Type: BR/EDR  Bus: USB
    BD Address: 00:26:83:FF:F3:45  ACL MTU: 1022:8  SCO MTU: 121:3
    DOWN 
    RX bytes:11523 acl:111 sco:0 events:314 errors:0
    TX bytes:4653 acl:114 sco:0 commands:140 errors:0


sudo apt-get install bluez bluez-tools bluez-utils gnome-bluetooth

Once these packages were installed (with dependencies), I was able to connect to my blackberry phone for example.

:guitar:

Cheers

---

