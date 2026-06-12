---
title: "no driver support for my laptop"
date: 2008-05-16
forum: Hardware
---

### Post by Snappo on 2008-05-16
Ok, I'm starting to re-think my move to linux as ubuntu's support and hardware support is crazy... Don't get me wrong I love how unique it is etc but i can even use it.

I have a packard bell easynote r1

The resolution is fine when i run the live cd but when i run it on dual boot it puts me in gfx safe mode. My wifi chip doesn't have any support...

I have a ar5005g and i have tried madwifi etc but that has all failed. I'm on my last straw and asking for any help with both the screen resolution and my wifi chip.

Thanks etc...

---

### Post by overdrank on 2008-05-16
> **Snappo said:**
> Ok, I'm starting to re-think my move to linux as ubuntu's support and hardware support is crazy... Don't get me wrong I love how unique it is etc but i can even use it.

I have a packard bell easynote r1

The resolution is fine when i run the live cd but when i run it on dual boot it puts me in gfx safe mode. My wifi chip doesn't have any support...

I have a ar5005g and i have tried madwifi etc but that has all failed. I'm on my last straw and asking for any help with both the screen resolution and my wifi chip.

Thanks etc...

HI and I am sorry you are having so many issue but not all hardware is compatible with linux in general. What is the model on graphics card? I have a laptop that had some issue with the atheros wireless ar5007 and  are you certain of the chipset as that was my issue. Ubuntu was detecting it as a 5006 and windows was 5007. This maybe a similar issue.

---

### Post by Snappo on 2008-05-16
> **overdrank said:**
> HI and I am sorry you are having so many issue but not all hardware is compatible with linux in general. What is the model on graphics card? I have a laptop that had some issue with the atheros wireless ar5007 and  are you certain of the chipset as that was my issue. Ubuntu was detecting it as a 5006 and windows was 5007. This maybe a similar issue.

windows says it is a 5005 and i get nothing on linux and i don't have a clue how to pull up my gfx card version :(

---

### Post by overdrank on 2008-05-16
> **Snappo said:**
> windows says it is a 5005 and i get nothing on linux and i don't have a clue how to pull up my gfx card version :(
Hi and you can use the command ```
lspci
```in the terminal. This will list your hardware. It should list your wireless also.

---

### Post by Snappo on 2008-05-16
> 
sudo modprobe ath_pci







To run a command as administrator (user "root"), use "sudo <command>".
See "man sudo_root" for details.

snappo@Snappo-Linux:~$ lspci
00:00.0 Host bridge: VIA Technologies, Inc. CN400/PM880 Host Bridge
00:00.1 Host bridge: VIA Technologies, Inc. CN400/PM880 Host Bridge
00:00.2 Host bridge: VIA Technologies, Inc. CN400/PM880 Host Bridge
00:00.3 Host bridge: VIA Technologies, Inc. CN400/PM880 Host Bridge
00:00.4 Host bridge: VIA Technologies, Inc. CN400/PM880 Host Bridge
00:00.7 Host bridge: VIA Technologies, Inc. CN400/PM880 Host Bridge
00:01.0 PCI bridge: VIA Technologies, Inc. VT8237 PCI Bridge
00:06.0 Ethernet controller: Atheros Communications Inc. AR5212/AR5213 Multiprotocol MAC/baseband processor (rev 01)
00:10.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 80)
00:10.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 80)
00:10.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 80)
00:10.3 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 82)
00:11.0 ISA bridge: VIA Technologies, Inc. VT8235 ISA Bridge
00:11.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 06)
00:11.5 Multimedia audio controller: VIA Technologies, Inc. VT8233/A/8235/8237 AC97 Audio Controller (rev 50)
00:11.6 Communication controller: VIA Technologies, Inc. AC'97 Modem Controller (rev 80)
00:12.0 Ethernet controller: VIA Technologies, Inc. VT6102 [Rhine-II] (rev 74)
01:00.0 VGA compatible controller: VIA Technologies, Inc. S3 Unichrome Pro VGA Adapter (rev 02)
snappo@Snappo-Linux:~$ 



Here is your results

---

### Post by overdrank on 2008-05-16
> **Snappo said:**
> Here is your results

Hi and I have highlighted the items
```
snappo@Snappo-Linux:~$ lspci
00:00.0 Host bridge: VIA Technologies, Inc. CN400/PM880 Host Bridge
00:00.1 Host bridge: VIA Technologies, Inc. CN400/PM880 Host Bridge
00:00.2 Host bridge: VIA Technologies, Inc. CN400/PM880 Host Bridge
00:00.3 Host bridge: VIA Technologies, Inc. CN400/PM880 Host Bridge
00:00.4 Host bridge: VIA Technologies, Inc. CN400/PM880 Host Bridge
00:00.7 Host bridge: VIA Technologies, Inc. CN400/PM880 Host Bridge
00:01.0 PCI bridge: VIA Technologies, Inc. VT8237 PCI Bridge
[COLOR="Red"]00:06.0 Ethernet controller: Atheros Communications Inc. AR5212/AR5213 Multiprotocol MAC/baseband processor (rev 01)[/COLOR]
00:10.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 80)
00:10.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 80)
00:10.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 80)
00:10.3 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 82)
00:11.0 ISA bridge: VIA Technologies, Inc. VT8235 ISA Bridge
00:11.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 06)
00:11.5 Multimedia audio controller: VIA Technologies, Inc. VT8233/A/8235/8237 AC97 Audio Controller (rev 50)
00:11.6 Communication controller: VIA Technologies, Inc. AC'97 Modem Controller (rev 80)
00:12.0 Ethernet controller: VIA Technologies, Inc. VT6102 [Rhine-II] (rev 74)
[COLOR="Red"]01:00.0 VGA compatible controller: VIA Technologies, Inc. VGA Adapter (rev 02)[/COLOR]
snappo@Snappo-Linux:~$ 
```
As for the wireless did a quick search and did not find anything helpful. The unichome is also not supported well in linux
[http://ubuntuforums.org/search.php?searchid=41362520](http://ubuntuforums.org/search.php?searchid=41362520)
Sorry I could not be of more assistants.

---

### Post by Snappo on 2008-05-16
> **overdrank said:**
> Hi and I have highlighted the items
```
snappo@Snappo-Linux:~$ lspci
00:00.0 Host bridge: VIA Technologies, Inc. CN400/PM880 Host Bridge
00:00.1 Host bridge: VIA Technologies, Inc. CN400/PM880 Host Bridge
00:00.2 Host bridge: VIA Technologies, Inc. CN400/PM880 Host Bridge
00:00.3 Host bridge: VIA Technologies, Inc. CN400/PM880 Host Bridge
00:00.4 Host bridge: VIA Technologies, Inc. CN400/PM880 Host Bridge
00:00.7 Host bridge: VIA Technologies, Inc. CN400/PM880 Host Bridge
00:01.0 PCI bridge: VIA Technologies, Inc. VT8237 PCI Bridge
[COLOR="Red"]00:06.0 Ethernet controller: Atheros Communications Inc. AR5212/AR5213 Multiprotocol MAC/baseband processor (rev 01)[/COLOR]
00:10.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 80)
00:10.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 80)
00:10.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 80)
00:10.3 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 82)
00:11.0 ISA bridge: VIA Technologies, Inc. VT8235 ISA Bridge
00:11.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 06)
00:11.5 Multimedia audio controller: VIA Technologies, Inc. VT8233/A/8235/8237 AC97 Audio Controller (rev 50)
00:11.6 Communication controller: VIA Technologies, Inc. AC'97 Modem Controller (rev 80)
00:12.0 Ethernet controller: VIA Technologies, Inc. VT6102 [Rhine-II] (rev 74)
[COLOR="Red"]01:00.0 VGA compatible controller: VIA Technologies, Inc. VGA Adapter (rev 02)[/COLOR]
snappo@Snappo-Linux:~$ 
```
As for the wireless did a quick search and did not find anything helpful. The unichome is also not supported well in linux
[http://ubuntuforums.org/search.php?searchid=41362520](http://ubuntuforums.org/search.php?searchid=41362520)
Sorry I could not be of more assistants.

As for the video driver what i am reading is just going over my head :(

---

### Post by overdrank on 2008-05-16
Ok have you tried to reconfigure your xorg with this command 
```
sudo dpkg-reconfigure -phigh xserver-xorg
```
And what version of ubuntu are you using, Hardy 8.04, Gusty 7.10?

---

### Post by Snappo on 2008-05-16
> **overdrank said:**
> Ok have you tried to reconfigure your xorg with this command 
```
sudo dpkg-reconfigure -phigh xserver-xorg
```
And what version of ubuntu are you using, Hardy 8.04, Gusty 7.10?

hardy 8.04 going to try that command just now but i was reading 3d affects still wouldn't work if i get it working but it is worth a try!

---

### Post by Snappo on 2008-05-16
Ok i tried what you said then it took me to a keyboard edit then i got by that then it errored on battery something :(

---

### Post by Snappo on 2008-05-17
bump

---

### Post by pikseli@work on 2008-05-28
You are going to have to provide quotes of what errors or output was printed or no-one will be able to help you.

---

