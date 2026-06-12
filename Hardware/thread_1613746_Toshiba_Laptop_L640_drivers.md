---
title: "Toshiba Laptop L640 drivers"
date: 2010-11-04
forum: Hardware
---

### Post by njsharp on 2010-11-04
I have a Toshiba laptop L640 01H from Australia's "Richard" Smith company (Ha!  I used the usual abbreviation for Richard and it became ****!!).  It is a special for that shop, but is almost certainly very similar to the rest of Toshiba's L640 range.

The user manual is at:

[http://www.mytoshiba.com.au/file/download/resource/file/18118/tc70081500f.exe](http://www.mytoshiba.com.au/file/download/resource/file/18118/tc70081500f.exe)

use of which requires running that program with WINE or on real Windoze to extract the pdf.  Sigh...

U10.10 64 bit desktop installed without apparent problems, but I find the web cam microphone seems not to work, nor does the headphone socket.  Toshiba support advise this is probably a driver problem.  It is repeated on a second specimen, so that seems correct.

The web cam itself works OK with Cheese.

Can anybody help with relevant drivers and how to install them?  Perhaps they do not yet exist and need to be written - way beyond my NIX skill level!

System/Administration/Additional drivers reveals nothing.

Here are some hopefully useful outputs:

lspci
00:00.0 Host bridge: Intel Corporation Core Processor DRAM Controller (rev 02)
00:02.0 VGA compatible controller: Intel Corporation Core Processor Integrated Graphics Controller (rev 02)
00:16.0 Communication controller: Intel Corporation 5 Series/3400 Series Chipset HECI Controller (rev 06)
00:1a.0 USB Controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 05)
00:1b.0 Audio device: Intel Corporation 5 Series/3400 Series Chipset High Definition Audio (rev 05)
00:1c.0 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 1 (rev 05)
00:1c.4 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 5 (rev 05)
00:1c.5 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 6 (rev 05)
00:1d.0 USB Controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 05)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev a5)
00:1f.0 ISA bridge: Intel Corporation Mobile 5 Series Chipset LPC Interface Controller (rev 05)
00:1f.2 SATA controller: Intel Corporation 5 Series/3400 Series Chipset 4 port SATA AHCI Controller (rev 05)
00:1f.3 SMBus: Intel Corporation 5 Series/3400 Series Chipset SMBus Controller (rev 05)
00:1f.6 Signal processing controller: Intel Corporation 5 Series/3400 Series Chipset Thermal Subsystem (rev 05)
02:00.0 Network controller: Realtek Semiconductor Co., Ltd. RTL8191SEvB Wireless LAN Controller (rev 10)
03:00.0 Ethernet controller: Atheros Communications AR8152 v1.1 Fast Ethernet (rev c1)
ff:00.0 Host bridge: Intel Corporation Core Processor QuickPath Architecture Generic Non-core Registers (rev 02)
ff:00.1 Host bridge: Intel Corporation Core Processor QuickPath Architecture System Address Decoder (rev 02)
ff:02.0 Host bridge: Intel Corporation Core Processor QPI Link 0 (rev 02)
ff:02.1 Host bridge: Intel Corporation Core Processor QPI Physical 0 (rev 02)
ff:02.2 Host bridge: Intel Corporation Core Processor Reserved (rev 02)
ff:02.3 Host bridge: Intel Corporation Core Processor Reserved (rev 02)



lsusb
Bus 002 Device 004: ID 0bda:0158 Realtek Semiconductor Corp. USB 2.0 multicard reader
Bus 002 Device 003: ID 04f2:b1d6 Chicony Electronics Co., Ltd 
Bus 002 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 003: ID 046d:c05a Logitech, Inc. 
Bus 001 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

from dmidecode:

Handle 0x0001, DMI type 1, 27 bytes
System Information
    Manufacturer: TOSHIBA
    Product Name: Satellite L640
    Version: PSK0GA-01H003
    Serial Number: 7A150666W
    UUID: E0ADBED7-3B91-DF11-876A-C80AA9EC7AF3
    Wake-up Type: Power Switch
    SKU Number: PSK0GA-01H003
    Family: Intel_Mobile

Ask if you want more.  The dmesg is 57k so I didn't include that here!

---

### Post by julio prada on 2010-12-08
I have the same problem on my new Toshiba c645, the mic and ear jacks dont work and there is a flicker on an external 1080p monitor. None of these 3 problems happen on Windows 7, so it is not hardware.

---

### Post by samahar on 2010-12-08
Ubuntu Version: 10.04 Lucid Lynx (using 64 bit... not sure if I should)
Laptop Maker: Toshiba
Laptop Model: Satellite l500 -oow

-Lucid works fine accept that the wireless lan doesn't work.

Wireless card- Realtek RTL8192E Wireless LAN 802.11n PCI-E

trouble shooting steps taken:
-several updates and restarts

- tried apt get commands:
install wifi-radar, then
gksu wifi-radar.

sudo ifconfig wlan0 up
sudo iwlist scan


Any ideas what my problem is or any way to fix it. I am willing to use an older version of Ubuntu so long as I have Wireless internet. I use Ubuntu for my school work.
-currently have Windows Vista 64 bit and Ubuntu 10.04 dual booted on this machine. Wireless is important as I use my laptop all over campus for papers and classes.

---

### Post by moaoci on 2010-12-11
To Samahar,

Ubuntu rtl8192e staging driver doesn't work yet. But the driver provided by realtek do work. (The driver is not available from their download site...  ask for the most current rtl8192e 64bit linux driver by emailing to [email]wlanfae@realtek.com[/email] ).

After you get your driver, that comes with easy to follow instructions, you need first to delete the rtl8192e staging driver.  Open a terminal, sudo nautilus, go to  File system - lib - modules - (your current version) - kernel - driver - staging.  Find the rtl8192e directory and press delete.

Then follow instructions provided by realtek.  If it doesn't work, write back and they will help you. 

I have a Toshiba Satellite L505 with ubuntu 10.04 64 bit,  I also tested the Ubuntu 10.10 64bit on a usb pen and it works fine.  My internet speed is about 3 mbps and I don't have any problems with my rtl8192e.

Keep the driver files on your desktop as the driver has to be recompiled every time the linux kernel number changes.  It is a very small price to pay for freedom.

---

### Post by IcarusR on 2010-12-11
moaoci

> delete the rtl8192e staging driver

Better practice not to delete the module, you can prevent it from loading by adding it to /etc/modprobe.d/blacklist.conf

julio prada

Software modems can have an adverse effect on sound. If you do not use modem try blacklisting it's module. May help to get headphone jack to work.
Also if you have intel hda sound then maybe adding 'model=your model' to /etc/modprobe.d/alsa-base.conf as per these two threads will help.

[http://ubuntuforums.org/showthread.php?t=616845]("http://ubuntuforums.org/showthread.php?t=616845")
[http://ubuntuforums.org/showthread.php?t=1043568]("http://ubuntuforums.org/showthread.php?t=1043568")

---

### Post by jakenetch on 2011-01-04
-

---

### Post by jakenetch on 2011-01-04
-

---

### Post by jakenetch on 2011-01-04
[FONT=Times New Roman][SIZE=3]My solution is work for me (My machine is L640 too)[/SIZE][/FONT]
 
 [SIZE=3][FONT=Times New Roman, serif]1.install new alsa : 
[/FONT][/SIZE]
  [SIZE=2]
  [/SIZE]
  **[SIZE=2]*[FONT=Courier New]sudo add-apt-repository ppa:ubuntu-audio-dev/ppa[/FONT]*[/SIZE]**
  **[SIZE=2]*[FONT=Courier New]sudo apt-get update[/FONT]*[/SIZE]**
  **[SIZE=2]*[FONT=Courier New]sudo apt-get install linux-alsa-driver-modules-$(uname -r)[/FONT]*[/SIZE]**
  
 2.[SIZE=3][FONT=Times New Roman, serif]edit alsa-base.conf : sudo gedit /etc/modprobe.d/alsa-base.conf[/FONT][/SIZE][SIZE=3][FONT=Times New Roman, serif]
add this setting to bottom line:
  [I][FONT=Courier New][SIZE=2]
  **options snd-hda-intel model=ideapad**
      
    [/SIZE][/FONT][/I][FONT=Courier New][SIZE=2][FONT=Times New Roman][SIZE=3]3.restart[/SIZE][/FONT][/SIZE][/FONT][/FONT][/SIZE]

---

### Post by lidex on 2011-01-04
> **jakenetch said:**
> [FONT=Times New Roman][SIZE=3]My solution is work for me (My machine is L640 too)[/SIZE][/FONT]
 
 [SIZE=3][FONT=Times New Roman, serif]1.install new alsa : 
[/FONT][/SIZE]
  [SIZE=2]
  [/SIZE]
  **[SIZE=2]*[FONT=Courier New]sudo add-apt-repository ppa:ubuntu-audio-dev/ppa[/FONT]*[/SIZE]**
  **[SIZE=2]*[FONT=Courier New]sudo apt-get update[/FONT]*[/SIZE]**
  **[SIZE=2]*[FONT=Courier New]sudo apt-get install linux-alsa-driver-modules-$(uname -r)[/FONT]*[/SIZE]**
  
 2.[SIZE=3][FONT=Times New Roman, serif]edit alsa-base.conf : sudo gedit /etc/modprobe.d/alsa-base.conf[/FONT][/SIZE][SIZE=3][FONT=Times New Roman, serif]
add this setting to bottom line:
  [I][FONT=Courier New][SIZE=2]
  **options snd-hda-intel model=ideapad**
      
    [/SIZE][/FONT][/I][FONT=Courier New][SIZE=2][FONT=Times New Roman][SIZE=3]3.restart[/SIZE][/FONT][/SIZE][/FONT][/FONT][/SIZE]

Geez, could you format that a little bit? :wink:
My real question is does that allow the headphones and internal mic to work?

---

### Post by jakenetch on 2011-01-06
> **lidex said:**
> Geez, could you format that a little bit? :wink:
My real question is does that allow the headphones and internal mic to work?

That's the way to enable headphone (and ,perhaps, mic too). 
Just follow by copying & pasting all commands, line by line in Terminal. That's it. :p

1. Add new repository for newest alsa driver.

**[SIZE=2]*sudo add-apt-repository ppa:ubuntu-audio-dev/ppa*[/SIZE]**
  [B][SIZE=2][I]sudo apt-get update
[/I][/SIZE][/B]
2. Then install newest alsa driver by[B][SIZE=2][I]

[/I][/SIZE][/B]**[SIZE=2]*sudo apt-get install linux-alsa-driver-modules-$(uname -r)*[/SIZE]**

3. Once you get new driver installed properly then open alsa config file by

[SIZE=2]***sudo gedit /etc/modprobe.d/alsa-base.conf***[/SIZE][SIZE=3]
[/SIZE]
4. Add this line at the bottom of this file

[SIZE=3]*[SIZE=2]**options snd-hda-intel model=ideapad**[/SIZE]*[/SIZE]

5. Then restart.

Waiting for reply of your progression. ):P I hope this solution could solve your problem as it did for me.

PS. I can't remember where I took this solution. So whosever it is, thanks a lot.

---

### Post by lidex on 2011-01-07
What I want to know is does that fix allow the headphone and mic to work - is it a complete solution? Or if not, what does it fix specifically? I know what the fix is. Thanx.

---

### Post by jakenetch on 2011-01-07
Yes,it does.
Why don't you try it first? :confused:


PS. Could you tell me about definition of "complete solution" ? Do you mean "permanent solution" ? If yes, this is the fix you need.

---

### Post by lidex on 2011-01-07
> **jakenetch said:**
> Yes,it does.
Why don't you try it first? :confused:


PS. Could you tell me about definition of "complete solution" ? Do you mean "permanent solution" ? If yes, this is the fix you need.

Because I do not have that hardware. I need to know if it fixes everything so I can recommend it to others who may have the same hardware and their mic does not work. Savvy? Complete solution means it fixes everything.

---

### Post by jakenetch on 2011-01-07
> **lidex said:**
> Because I do not have that hardware. I need to know if it fixes everything so I can recommend it to others who may have the same hardware and their mic does not work. Savvy? Complete solution means it fixes everything.


Sorry, I'd got you wrong. I thought you owned L640 and looking for fix too. :tongue:

I've just double checked on built-in laptop mic and found out that all works well. (I don't have headphone which with mic to test but headphone alone works well too)

---

### Post by lidex on 2011-01-07
Thanks for following up with that :D

---

### Post by J. Ryan on 2011-04-09
> **jakenetch said:**
> That's the way to enable headphone (and ,perhaps, mic too). 
Just follow by copying & pasting all commands, line by line in Terminal. That's it. :p

1. Add new repository for newest alsa driver.

**[SIZE=2]*sudo add-apt-repository ppa:ubuntu-audio-dev/ppa*[/SIZE]**
  [B][SIZE=2][I]sudo apt-get update
[/I][/SIZE][/B]
2. Then install newest alsa driver by[B][SIZE=2][I]

[/I][/SIZE][/B]**[SIZE=2]*sudo apt-get install linux-alsa-driver-modules-$(uname -r)*[/SIZE]**

3. Once you get new driver installed properly then open alsa config file by

[SIZE=2]***sudo gedit /etc/modprobe.d/alsa-base.conf***[/SIZE][SIZE=3]
[/SIZE]
4. Add this line at the bottom of this file

[SIZE=3]*[SIZE=2]**options snd-hda-intel model=ideapad**[/SIZE]*[/SIZE]

5. Then restart.

Waiting for reply of your progression. ):P I hope this solution could solve your problem as it did for me.

PS. I can't remember where I took this solution. So whosever it is, thanks a lot.

Thanks for this. It seems to have worked perfectly for my Toshiba Satelite  T135D S1324.

---

### Post by listerdl on 2012-02-19
Do you think I should try this? I have the same issue but I do not have Toshiba, instead Panasonic Toughbook CF F9 - thanks!

---

