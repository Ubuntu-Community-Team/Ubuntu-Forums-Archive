---
title: "Medion Drivers"
date: 2009-05-06
forum: Hardware
---

### Post by Longshoreman on 2009-05-06
Hi installed Ubuntu on my Medion Laptop (MD 96625) Love 9.04 But !!!!!!! So Sound and No Wireless!!!!!!! I can without the Wireless But the silence is driving me mad!!!!! It's just like have had a stroke. No You Tube, No BBC iPlayer Please help. My Hardware set-upis as follow s.   00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 03) 00:01.0 PCI bridge: Intel Corporation Mobile PM965/GM965/GL960 PCI Express Root Port (rev 03) 00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 (rev 03) 00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 03) 00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 03) 00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03) 00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 03) 00:1c.2 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 3 (rev 03) 00:1c.3 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 4 (rev 03) 00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 03) 00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 03) 00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 03) 00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 03) 00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f3) 00:1f.0 ISA bridge: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller (rev 03) 00:1f.1 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller (rev 03) 00:1f.2 SATA controller: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA AHCI Controller (rev 03) 00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 03) 01:00.0 VGA compatible controller: nVidia Corporation GeForce 8600M GS (rev a1) 02:00.0 Network controller: RaLink RT2860 04:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 01)  Any help would be most appreciated.  Ta Longshoreman.

---

### Post by Longshoreman on 2009-05-08
Hi the first post I made to this forum looked a bit messy rushed!) so this is a follow-up which (I hope looks a bit more considered!)  I am running Ubuntu Jaunty 9.10 on a MEDION Notebook (MD 96625) and have no sound. (I had no sound with 8.04 either)  I am running the same on an ACER Notebook with no trouble)  Reading through various threads is would seem that Ubuntu does not take kindly to Medion devices.  I have checked my hardware and I think this is the device causing the problem (full list of hardware at end of post).  Audio device: Intel Corporation 82801H (ICH8 Family) HD  Audio Controller (rev 03) 00:1c.0 PCI bridge:  Intel Corporation 82801H (ICH8 Family)  Any fixes would be greatly appreciated!  Looking at other related treads I was wondering if this idea would work? [https://help.ubuntu.com/community/OpenSound](https://help.ubuntu.com/community/OpenSound) Which will replace ALSA with Open Sound  Can anyone help with this one please?  Thanks, David.  00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960  Memory Controller Hub (rev 03) 00:01.0 PCI bridge: Intel Corporation Mobile PM965/GM965/GL960 PCI  Express Root Port (rev 03) 00:1a.0  USB Controller: Intel Corporation 82801H (ICH8 Family)  USB UHCI Controller #4 (rev 03) 00:1a.1  USB Controller: Intel Corporation 82801H (ICH8 Family)  USB UHCI Controller #5 (rev 03) 00:1a.7  USB Controller: Intel Corporation 82801H (ICH8 Family)  USB2 EHCI Controller #2 (rev 03) 00:1b.0  Audio device: Intel Corporation 82801H (ICH8 Family) HD  Audio Controller (rev 03) 00:1c.0 PCI bridge:  Intel Corporation 82801H (ICH8 Family)  PCI Express Port 1 (rev 03) 00:1c.2 PCI bridge:  Intel Corporation 82801H (ICH8 Family)  PCI Express Port 3 (rev 03) 00:1c.3 PCI bridge:  Intel Corporation 82801H (ICH8 Family)  PCI Express Port 4 (rev 03) 00:1d.0 USB  Controller: Intel Corporation 82801H (ICH8 Family)  USB UHCI Controller #1 (rev 03) 00:1d.1  USB Controller: Intel Corporation 82801H (ICH8 Family)  USB UHCI Controller #2 (rev 03) 00:1d.2  USB Controller: Intel Corporation 82801H (ICH8 Family)  USB UHCI Controller #3 (rev 03) 00:1d.7  USB Controller: Intel Corporation 82801H (ICH8 Family)  USB2 EHCI Controller #1 (rev 03) 00:1e.0 PCI bridge:  Intel Corporation 82801 Mobile PCI Bridge (rev f3) 00:1f.0 ISA bridge:  Intel Corporation 82801HEM (ICH8M) LPC Interface Controller (rev 03) 00:1f.1 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller (rev 03) 00:1f.2 SATA controller:  Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA AHCI Controller (rev 03) 00:1f.3 SMBus:  Intel Corporation 82801H (ICH8 Family)  SMBus Controller (rev 03) 01:00.0 VGA compatible controller: nVidia Corporation GeForce 8600M GS (rev a1) 02:00.0  Network controller: RaLink RT2860 04:00.0  Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI  Express Fast Ethernet controller (rev 01)

---

### Post by Yellow Pasque on 2009-05-17
I can't really read that. In the future, use [ code ][ /code ] tags for command output. (no spaces between the brackets)

Anyway... it looks like you have a standard HDA Intel device. The driver should load automatically, but you could try manually with this:
```
sudo modprobe snd-hda-intel
```

Post output of:
```
sudo lshw -C multimedia
```
Also:
```
dmesg | grep ALSA
```

> Looking at other related threads I was wondering if this idea would work? [https://help.ubuntu.com/community/OpenSound](https://help.ubuntu.com/community/OpenSound) which will replace ALSA with Open Sound Can anyone help with this one please?
It's possible, but I would recommend using it as a last resort. OSS4 doesn't always have the best support for onboard HDA devices (your PCI ID may need added to the source, jack sensing probably won't work, etc.) Also, that guide needs polishing/updating. I keep meaning to do that, but I'm better at procrastinating.

---

### Post by Yellow Pasque on 2009-05-17
For your wireless, you need to build the module provided by the manufacturer, because no non-free kernel modules exists at the moment:
```
cd ~/
wget http://www.ralinktech.com.tw/data/drivers/2009_0424_RT2860_Linux_STA_V2.1.1.0.tgz
tar -xzf 2009_0424_RT2860_Linux_STA_V2.1.1.0.tgz
cd 2009_0424_RT2860_Linux_STA_V2.1.1.0/
gedit os/linux/config.mk
```
At this point, you will have an open text file. Towards the beginning/top of the file, you'll see a block of text:
```
#ifdef WPA_SUPPLICANT_SUPPORT
# Support Wpa_Supplicant
HAS_WPA_SUPPLICANT**=n**
#endif // WPA_SUPPLICANT_SUPPORT //

#ifdef NATIVE_WPA_SUPPLICANT_SUPPORT
# Support Native WpaSupplicant for Network Maganger
HAS_NATIVE_WPA_SUPPLICANT_SUPPORT**=n**
#endif // NATIVE_WPA_SUPPLICANT_SUPPORT //
```
Change the '=n' in both lines to '=y' . Save and quit (now you're back at the terminal).
```
sudo make
sudo make install
sudo modprobe rt2860
sudo /etc/init.d/networking restart
```

---

### Post by Longshoreman on 2009-05-18
Hi Temüjin, Still no joy. Output from terminal. Response to sudo modprobe snd-hda-intel:  sudo lshw -C multimedia    *-multimedia                    description: Audio device         product: 82801H (ICH8 Family) HD Audio Controller         vendor: Intel Corporation         physical id: 1b         bus info: pci@0000:00:1b.0         version: 03         width: 64 bits         clock: 33MHz         capabilities: pm msi pciexpress bus_master cap_list         configuration: driver=HDA Intel latency=0 module=snd_hda_intel   Response to None.  ========================================================================= Relating to the when I load System - Preferences - Default Sound Card : It cycles for a bit then dies. So it would seem that it is not being recognized.  Thanks for your Help ! David ;^)>

---

### Post by Longshoreman on 2009-05-18
Hi again ;) Just checked again at the ALSA website; [http://www.alsa-project.org/main/index.php/Matrix:Vendor-Intel:](http://www.alsa-project.org/main/index.php/Matrix:Vendor-Intel:) to see if my sound card is supported or not: =========================================== My sound card is; Audio device: Intel Corporation 82801H (ICH8 Family) HD  Audio Controller (rev 03) 00:1c.0 PCI bridge:  =========================================== From this readout =========================================== ICH southbridge AC97 audio 440MX i810 i810E i820 ICH4 ICH5 ICH6 ICH7: ============================================ or ============================================ ICH southbridge HD-audio and modem ICH6 ICH6M ICH7 ESB2 ============================================ It would seem not. (This could also be why my wireless is not working?) So I do not see any option for me at this time. I think the only way forwards is to hope that my card get supported!? Thanks, David :-/

---

### Post by Yellow Pasque on 2009-05-18
Try this: [http://ubuntuforums.org/showthread.php?p=6589810](http://ubuntuforums.org/showthread.php?p=6589810)

---

### Post by Longshoreman on 2009-07-06
Sound Problems – Solved!? :)  Hi, since my last visit to this Forum I have been doing a lot of work in order to get this situation sorted for me and I hope for you!  If your sound card is not working in Jaunty it is very likely that the ALSA (Advanced Linux Sound Architecture) drivers are at fault. They do-not support half as many sound cards as you would suppose so if yours is a little advanced (as is mine) your gonna have probs bro !! The solution that (eventually worked for me) I have listed below so that it may be of help to others such as yourselves   First we need to make ready the Ubuntu OS to receive the OSS packsge so we need to install the  Prerequisites  Open Terminal from the Taskbar (Applications > Accessories > Terminal) Copy and paste the below into the Terminal Box (without the "")  "sudo apt-get install linux-headers-generic linux-source build-essential"  It will ask you for your password (this you set-up when you installed Ubuntu)  The code will run and then go back to the prompt.  Then go to the OSS (Open Sound System) website and download oss:deb (distribution package)  [http://www.opensound.com/download.cgi](http://www.opensound.com/download.cgi)  There are several packages to chose from here.  I choose linux 2.6 - deb - x86  (It worked for me)  Right Click package. Select open with GDebi Package Installer.  When this installed open  System > Preferences > Sound In Sound Preferences in the Devices tab  select OSS in all the option boxes.  Next right click in the task bar and Add the Gnome Volume Control.  Now Open Gnome Volume Control Make sure that the Volume slide is set to max (to the right) and Mute is not selected (with a tick)  >  Click Volume Control Box > Volume Control Splash Box Opens > Click Preferences Box > Preferences Box Opens. > Tick All Boxes  > Close. This will open all the volume controls for all various sound outputs.  > First make sure all the volume slides are near the top  Then with and audio source playing (CD?)  >Make sure vmiz0 is up near the top to maximise the output sound.  > Tick and untick the Mute Boxes for each control. (It may seem daft, but even though a Mute Box may not show as muted it may still be!) You should be listening now for sound!!!!!!! Depending on the chip set and Audio Card in your machine one or more  of these outputs will control Right Internal Speaker Right Internal Speaker Headphone Jack (Green)  Others (and there are many) will control recording and other stuff – not as yet investigated!  In my case the choices below worked. *codec1 jack internal black shown twice  > controls left and right internal speakers *codec1 jack green > controls the Headphone socket (Green makes sense yes!) .*vmix0-outvol > is the main output volume control (this in universal I think) Now you should have sound from the outputs you desire and you can close the box.  Good Luck!

---

