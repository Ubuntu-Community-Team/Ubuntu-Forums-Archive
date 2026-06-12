---
title: "Facing many problems on HP 620 :("
date: 2011-07-03
forum: Hardware
---

### Post by urMohid on 2011-07-03
Yesterday I spent the whole day trying to make ubuntu 11.04 32bit version work on my HP 620. I installed it using pen drive alongside windows and here is what happened. I was able to boot it right after installation and when I restart it, or shut down and then start, after selecting ubuntu from grub menu screen went completely blank and nothing appeared even after 10 minutes. I reinstalled by different settings 4-5 times hoping it would work. I was freaked out at this point. But then by chance I figured it out, that problem was with the wifi, which I don't use, so had it turned off from windows. Tried different things and came to conclusion that I had to keep it on or ubuntu wouldn't load. In short this almost solved problem.
But at the same time when I was thinking that it is in fact a good operating system and maybe I'd shift completely by removing my windows, some more problem were discovered. So here is the list of current problems;

1. First of all, bluetooth behaved erratically. Strange behavior it shows and I haven't been able to send a single file from it.

2. A press of wireless key, which toggles wifi and bluetooth, would hang ubuntu. Have to use power button to turn off directly.

3. Not able to shutdown, restart, standby, nothing. Didn't try hibernate and suspend. For standby, screen goes black with all lights still on, and not able to recover from state. And for shutdown and restart, everything vanishes except wallpaper and it's stuck there. Have to use power button to turn off directly in all cases. In short, it's only method to turn off.

Now to smaller problems which I could live with but it's nicer to have bug free system.

4. When booting ubuntu, shows background and afterward shows ubuntu logo for 2-3 seconds and boots instead of showing logo entire times, and sometimes this screen becomes of small size and shifts to upper left corner.

5. Sometimes when I boot, resolution is disturbed and it is in ratio of 3:4, 1024x768 and I have to change it manually to get full screen.

6. While ubuntu is running, wifi indicator light keeps blinking alternating blue and orange lights, which otherwise is blue for on and orange for off. And when it is stuck while shutting down, it stays blue.

This all I experienced in only one day. Then I didn't try to install again or maybe I could have some other problems. Maybe someone could guide me how to make it work :confused:

PS: Thought about trying 64bit version but I don't have much capacity left in me to download 700mb more at the speed of 20kb, spend another day with it and still not see it work :(

edit: Forgot to mention that everything is working fine on my friend's acer aspire mini laptop (don't remember specific model). I myself installed ubuntu on it yesterday.

---

### Post by urMohid on 2011-07-04
No replies???????

---

### Post by yourzone on 2011-07-04
I tried to install Ubuntu 11.04 32 bit and 64 bit , it freezes up when booting. (even klicked the updated during install on , on each attempt)
Tried tot boot up the 32 bit and 64 bit Live CD /DVD , no problems. 
Tried to install from the running Live CD/DVD both 32 and 64 bit , installaing no problem, but when it boots , FREEZE at the ubuntu logo splash screen.
Finaly I tried to install an old 10.10 version of Kubuntu 32 bit , no problems.
Windows 7 runs with no problems.
 
What the hell is going on ? 
 
I will attemt to install the ubuntu 10.10 , if it runs then i will do a distro update and see what happens, i'll let you know.

---

### Post by urMohid on 2011-07-04
> **yourzone said:**
> I tried to install Ubuntu 11.04 32 bit and 64 bit , it freezes up when booting. (even klicked the updated during install on , on each attempt)
Tried tot boot up the 32 bit and 64 bit Live CD /DVD , no problems. 
Tried to install from the running Live CD/DVD both 32 and 64 bit , installaing no problem, but when it boots , FREEZE at the ubuntu logo splash screen.
Finaly I tried to install an old 10.10 version of Kubuntu 32 bit , no problems.
Windows 7 runs with no problems.
 
What the hell is going on ? 
 
I will attemt to install the ubuntu 10.10 , if it runs then i will do a distro update and see what happens, i'll let you know.
Yeah please let me know if it works. Then I'll try it too because it is difficult for me to try will a slow internet conn. Otherwise I may choose to stick with ubuntu 10.10 or wait for another update.

---

### Post by yourzone on 2011-07-04
Yes Finaly !
What is the reason ? I don't know, but for me that did the trick
It Works, after a succesful install of the 10.10 (32bit) and the distro update to 11.04 , Ubuntu boots and runs at first sight as it should. In 2 seconds the system was up and running (SSD instead of Harddisk - 4GB Ram).
 
Now I ll try if the trick works with the 64 bit version.

---

### Post by urMohid on 2011-07-05
That's good. Post the results for 64bit version too because that is better I think. And you are also using HP 620 right?
edit:why did you not install it on HDD?

---

### Post by yourzone on 2011-07-06
The 64-trick install did it also.
I swapped my HD (moving parts) for a Solid State Disc because I wanted quicker booting time and because I use the notebook a lot in the car. (longe battery life - more shock resistant ... )
To fix the wifi problems (both 32 bit and 64 bit) use this simple bypass : 
a) download the pre-built rt3090-dkms package here:
[http://stat.case.edu/~jrt32/how_to_build_rt3090_for_ubuntu_lucid/rt3090-dkms_2.3.1.4-0ubuntu0~ppa1_all.deb](http://stat.case.edu/~jrt32/how_to_build_rt3090_for_ubuntu_lucid/rt3090-dkms_2.3.1.4-0ubuntu0~ppa1_all.deb)
b) Blacklisted the current driver 
    i)sudo gedit /etc/modprobe.d/blacklist.conf
    ii)add Blacklist rt2800pci to the text file
    iii)save and reboot
 
Note : why is it that a Ubuntu 11.04 (Unity) will not work out of the Box on my HP 620 (Ubuntu 10.10 - Gnome did )? I think (not sure) that the Unity interface is the problem. Why ? I downloaded and installed succesfully a Kubuntu 11.04 (KDE) and a Pinguy OS 11.04 (Ubuntu / Mint based - Gnome) only had to fix the wifi drivers.
 
Anyone ?
 
 
[FONT=Liberation Serif][/FONT]

---

