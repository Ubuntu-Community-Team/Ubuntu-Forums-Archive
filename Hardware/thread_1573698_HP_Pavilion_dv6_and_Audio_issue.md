---
title: "HP Pavilion dv6 and Audio issue"
date: 2010-09-13
forum: Hardware
---

### Post by dedede on 2010-09-13
I was told to post this question here.

I have installed ubuntu 10.04 on HP Pavilion dv6 notebook.

Everything hardware related is fine, except when I plug a headphone, the sound continues to come from the speakers as well, which is very annoying. I have found out that other users do not experience this, so this is not the default behaviour of Ubuntu.

How can this be fixed? 

Also, I rather not start a terminal each time I reboot ,or launch a audio panel and move sliders around each time I reboot to fix this.

---

### Post by dedede on 2010-09-15
Any other info i should give?

---

### Post by dedede on 2010-09-19
Sady I use Windows now for this problem. I havent boothed ubuntu for weeks

---

### Post by lidex on 2010-09-19
> **dedede said:**
> Sady I use Windows now for this problem. I havent boothed ubuntu for weeks

Using a Terminal="Applications->Accessories->Terminal"
Open this file for editing:
```
 gksudo gedit /etc/modprobe.d/alsa-base.conf 
```
Insert this line at the bottom:
```
 options snd-hda-intel model=hp-dv5 enable_msi=1 
```
Save. Close. Reboot. 
Check your levels in alsamixer.
```
 alsamixer 
```
Press <F6> to select the correct soundcard.
Press <F3> to show playback levels. <F4> selects capture levels [or use <Tab>]
Use the left/right arrow keys to select and up/down arrow keys to change levels. <M> to mute/unmute.
Go to "System ->Preferences ->Sound" and make sure the correct soundcard is default and adjust your profile on the hardware tab. 
On the output tab choose the correct device.

---

### Post by dedede on 2010-09-21
Strange, I boothed Ubuntu today and made changes to the file as you said. Then I accessed alsamixer and changed the soundcard from -default to HP's. When I plugged my headphones the problem was gone. But then I switched the soundcard in alsamixer to -default again and the problem wasn't present as well! What might have fixed it??

---

### Post by lidex on 2010-09-21
> **dedede said:**
> Strange, I boothed Ubuntu today and made changes to the file as you said. Then I accessed alsamixer and changed the soundcard from -default to HP's. When I plugged my headphones the problem was gone. But then I switched the soundcard in alsamixer to -default again and the problem wasn't present as well! What might have fixed it??
What I asked you to do. Sometimes you need to toggle the settings to initialize them.

---

