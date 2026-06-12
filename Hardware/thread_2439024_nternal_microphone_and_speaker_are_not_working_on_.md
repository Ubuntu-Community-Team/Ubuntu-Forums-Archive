---
title: "nternal microphone and speaker are not working on hp spectre 360 `13 with Ubuntu18.04"
date: 2020-03-21
forum: Hardware
---

### Post by dejangrubisic on 2020-03-21
I installed the latest Ubuntu18.04 from scratch and the latest kernel  5.5.10. (5.5.10-050510-generic) with no problems. But for some reason  there is neither sound (Dummy output) or microphone works. 

 I tried also with Ubuntu 19.10 and at the beginning there are Sound on the speakers, but first time I suspend it it froze with black screen and when I did hard reset it lost sound on speakers (Dummy output). 

All these are strange as at least speakers worked well when I first install Ubuntu 18.04 and then the sound card was recognized by intel-hda as Realtek ALC285 Codec. 



In both cases It seems that the sound cart is not recognized.

**$ sudo aplay -l **

aplay: device_list:270: no soundcards found... 
**$ cat /proc/asound/cards  **

--- no soundcards --- 

**$ lspci | grep Audio  **

no answer

 

I tried this tutorial [https://help.ubuntu.com/community/SoundTroubleshootingGuide](https://help.ubuntu.com/community/SoundTroubleshootingGuide) and everything seems to be as expected. I come to section "AC" and after running the command refereed as 'big one', I got
**Sound cards recognized by the system:**
00:1f.3 Multimedia audio controller [0401]: Intel Corporation Device [8086:34c8] (rev 30)
**Sound cards recognized by ALSA:**
00:1f.3 Multimedia audio controller [0401]: Intel Corporation Device [8086:34c8] (rev 30)
**Sound cards recognized by ALSA, and activated:**
00:1f.3 Multimedia audio controller [0401]: Intel Corporation Device [8086:34c8] (rev 30)
 
When  I connect headset by Bluetooth I have sound and mic is working,  although when I connect headset by AudioJack neither microphone nor  audio is working.  I also checked BIOS and there was no option to  disable Sound Card. Do you have any idea what could be wrong?

I found some information for my model of laptop here  [https://wiki.archlinux.org/index.php/HP_Spectre_x360_-_13-ap0xxxx#Audio](https://wiki.archlinux.org/index.php/HP_Spectre_x360_-_13-ap0xxxx#Audio) , but I am not really sure what to do. 

Thanks !
PS. This shows up just for a second while booting.
[IMG]https://h30434.www3.hp.com/t5/image/serverpage/image-id/234909iD4B19A0B05D0C42F/image-size/large?v=1.0&px=999[/IMG]

---

### Post by dejangrubisic on 2020-03-21
Solution for Dummy output: [[FONT=Calibri]https://bbs.archlinux.org/viewtopic.php?id=251157[/FONT]]("https://bbs.archlinux.org/viewtopic.php?id=251157")[LEFT][COLOR=windowtext][FONT=Calibri] [/FONT][/COLOR][COLOR=#000000][FONT=Calibri] 
[/FONT][/COLOR][/LEFT][COLOR=#000000][FONT=&quot][LEFT][COLOR=windowtext][COLOR=windowtext][FONT=Calibri]I used to change /etc/default/grub to have this line[/FONT][/COLOR][FONT=Calibri] [/FONT][/COLOR][/LEFT][/FONT][/COLOR]
[COLOR=#000000][FONT=&quot][LEFT][COLOR=windowtext][COLOR=windowtext][FONT=Calibri]GRUB_CMDLINE_LINUX_DEFAULT="loglevel=3 quiet splash acpi_backlight=vendor acpi_osi='!Windows 2013' acpi_osi='!Windows 2012' snd_hda_intel.dmic_detect=0"[/FONT][/COLOR][FONT=Calibri] [/FONT][/COLOR][/LEFT][/FONT][/COLOR]
[COLOR=#000000][FONT=&quot][LEFT][COLOR=windowtext][COLOR=windowtext][FONT=Calibri]Then run in terminal[/FONT][/COLOR][FONT=Calibri] [/FONT][/COLOR][/LEFT][/FONT][/COLOR]
[COLOR=#000000][FONT=&quot][LEFT][COLOR=windowtext][COLOR=windowtext][FONT=Calibri]grub-mkconfig -o /boot/grub/grub.cfg[/FONT][/COLOR][FONT=Calibri] [/FONT][/COLOR][/LEFT][/FONT][/COLOR]
[COLOR=#000000][FONT=&quot][LEFT][COLOR=windowtext][COLOR=windowtext][FONT=Calibri]Then reboot.[/FONT][/COLOR][FONT=Calibri] 
[/FONT][COLOR=windowtext][FONT=Calibri]Audio is now working on HP Spectre X360[/FONT][/COLOR][FONT=Calibri] 
[/FONT][COLOR=windowtext][FONT=Calibri]Kernel 5.4.2 (Works also on Ubuntu 19.10)[/FONT][/COLOR][FONT=Calibri] 
[/FONT][/COLOR][/LEFT][/FONT][/COLOR]
[LEFT][COLOR=#000000][FONT=Calibri][/FONT][/COLOR][/LEFT]

---

