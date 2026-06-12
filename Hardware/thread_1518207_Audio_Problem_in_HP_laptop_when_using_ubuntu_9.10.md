---
title: "Audio Problem in HP laptop when using ubuntu 9.10"
date: 2010-06-26
forum: Hardware
---

### Post by subbu2687 on 2010-06-26
Hi all,

  	 	 	 	 	 	  Im using HP DV3 lptop and i have installed ubuntu 9.10 linux in my machine. Im not able to play audio when using linux. It is always in mute.
 

 The touchpad shows that the sound control is always in MUTE(Red in colour). Im not able to play any sound. But the changes i make by touching the sound control are reflected in the screen but the sound isnt playing. I ve also checked my sound settings in System->Preferences->Sound and it is fine. 
 

 Also the same is the case with my WIFI connectivity. It shows that it is always connected(Blue in colour). But the changes i make by touching it are reflected in the screen and im able to connect and disconnect to a network.
 

 Please help me in resolving this issue. Im a new user to ubuntu linux and im confused.  
 Thanks in advance!!
 

 **Note: The above said features are working fine in Windows 7.**

---

### Post by lidex on 2010-06-27
For audio: Using a Terminal="Applications->Accessories->Terminal"
Open this file for editing:
```
 gksudo gedit /etc/modprobe.d/alsa-base.conf 
```
Insert this line at the bottom:
```
 options snd-hda-intel model=hp-dv5 enable_msi=1 
```
Save. Close. Reboot. Check your levels in alsamixer.
```
 alsamixer 
```
Press <F6> to select the correct soundcard.
Press <F3> to show playback levels. <F4> selects capture levels [or use <Tab>]
Use the left/right arrow keys to select and up/down arrow keys to change levels. <M> to mute/unmute.
Go to "System ->Preferences ->Sound" and make sure the correct soundcard is default and adjust your profile on the hardware tab.

For wireless look here:
[http://linux.aldeby.org/howto-ubuntu-linux-on-hp-pavilion-dv2000-dv6000-dv9000-series-laptops.html/4#wireless]("http://linux.aldeby.org/howto-ubuntu-linux-on-hp-pavilion-dv2000-dv6000-dv9000-series-laptops.html/4#wireless")

---

