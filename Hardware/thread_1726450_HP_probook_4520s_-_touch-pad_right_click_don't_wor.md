---
title: "HP probook 4520s - touch-pad right click don't work"
date: 2011-04-11
forum: Hardware
---

### Post by prohp on 2011-04-11
Hi, I'm using Ubuntu 10.10 with fluxbox.
for some reason only the right click in my touch-pad isn't working.
how can i solve this problem?
currently i'm using usb-mouse and the right click is working fine!
EDIT:
just tried with ubuntu 11.04 - right click still don't work.

---

### Post by ALIENDUDE5300 on 2011-04-12
Hi, I have the *exact* same laptop, an HP ProBook 4520s, and I am also experiencing the same problem. Right clicking doesn't work for me in 11.04 either when using the trackpad. With an HP MG-0133 wireless mouse, I can right click just fine.

---

### Post by HPA on 2011-04-14
I also have an HP Probook 4520s and I have also faced the same problem after my recent upgrade from Ubuntu 10.10 to Ubuntu 11.04 Beta 1.

---

### Post by ibogi on 2011-04-29
Me neither. It worked on 10.04, but it's kaput now.

---

### Post by tarek_ on 2011-04-30
hello
I have hp probook 4520s and i have the same problem 
the right click in touch pad and the touch pad lock button don't work in Ubuntu 
I installed windows 7 to check and it worked very well
 but the problem is that i decided to don't use microsoft products anymore
 so I use Ubuntu without right click and waiting for a solution  ..

---

### Post by prohp on 2011-05-02
> **ibogi said:**
> Me neither. It worked on 10.04, but it's kaput now.

how it worked for you in 10.04?
did you change something? or just install clean 10.04?

---

### Post by xape on 2011-05-03
hi guys,

I tried this  **[http://ubuntuforums.org/showthread.php?t=1586915](http://ubuntuforums.org/showthread.php?t=1586915)** and it works fine in Ubuntu 10.10 !:popcorn: .

I hope it works in Ubuntu 11.04 too... let me know if somebody will try it

Andrea

---

### Post by yurybondarau on 2011-05-05
Hi,

I have problem with key that enable/disable wireless connection on 4520s' HP. 
[http://ubuntuforums.org/showthread.php?t=1748051&highlight=hp+4520s](http://ubuntuforums.org/showthread.php?t=1748051&highlight=hp+4520s)
[URL="http://ubuntuforums.org/showthread.php?t=1748051&highlight=hp+4520s"]
[/URL] 
Somebody  faced this issue? If yes, please suggest how to fix it.


Solution in thread [http://ubuntuforums.org/showthread.php?t=1586915&page=2](http://ubuntuforums.org/showthread.php?t=1586915&page=2) fix right touchpad button for 2.6.35 kernel, what about 2.6.38 (Ubuntu 11.04).

Kind Regards

---

### Post by ibogi on 2011-05-07
> **prohp said:**
> how it worked for you in 10.04?
did you change something? or just install clean 10.04?
In 10.04 it worked out of the box.

---

### Post by xape on 2011-05-09
About, key that enable/disable wireless connection on 4520s' HP, try to run eth interface... 
What do you read with "ifconfig"?

I took up the interface and I solved the problem... 

ifconfig eth1 up 

and the key works fine.

Hope it helps

Andrea

---

### Post by HPA on 2011-05-21
> **xape said:**
> hi guys,

I tried this  **[http://ubuntuforums.org/showthread.php?t=1586915](http://ubuntuforums.org/showthread.php?t=1586915)** and it works fine in Ubuntu 10.10 !:popcorn: .

I hope it works in Ubuntu 11.04 too... let me know if somebody will try it

AndreaIt doesn't work in ubuntu 11.04, but I've found this patch for ubuntu 11.04 64bit:
[http://ompldr.org/vOGRtNQ/xserver-xorg-input-synaptics_1.3.99+git20110116.0e27ce3a-0ubuntu11_amd64.deb](http://ompldr.org/vOGRtNQ/xserver-xorg-input-synaptics_1.3.99+git20110116.0e27ce3a-0ubuntu11_amd64.deb)
and it solved the problem!
Attention: After the installation of this patch, you have to lock the xserver-xorg-input-synaptics_1.3.99+git20110116.0e27ce3a-0ubuntu11 package in the Synaptic Package Manager because there is a newer version ( xserver-xorg-input-synaptics_1.3.99+git20110116.0e27ce3a-0ubuntu12) available to download in the Update Manager.
Avoid this update because if you do it, the problem with the touchpad will appear again.

---

### Post by flop70 on 2011-06-09
The patch linked by HPA worked fine for me on a HP Probook 4520s under 11.04. Thank you! :p

I had to uninstall the xserver-xorg-input-synaptics package via apt first, as it was newer version, then i could install the linked one with the ubuntu software center. Afterwards I locked that version in the synaptic package manager. Hope these steps help other users with the same problem

---

### Post by jurij89 on 2011-06-22
hi, I am having the same problem, but I'm running 11.04 32 bit version...
does anyone know of a similar solution?

thanks in advance! :)

---

### Post by varunrajan on 2011-06-22
Cross reference from [http://ubuntuforums.org/showthread.php?p=10967868](http://ubuntuforums.org/showthread.php?p=10967868)
> **J4K4 said:**
> [ftp://ftp.hp.com/pub/softpaq/sp52501-53000/sp52904.tar](ftp://ftp.hp.com/pub/softpaq/sp52501-53000/sp52904.tar)

here is the driver...

This link gives a rpm package of the official synaptics driver. I tried to convert it to deb using alien but failed. Can someone who knows how to manually convert between rpm and deb please make the conversion?

Thanks

---

### Post by luberfly on 2011-07-22
Hi guys,
I have Ubuntu 10.04LTS and Ubuntu 11.04 32bit and I have the some problems: Multutouch doesn't work and right click doesn't work.
How I can fix the probelm?

I found in the HP web site the driver for SuSE Linux. It is possible to convert it into Ubuntu?

Best Regards

Luca

---

### Post by elinap on 2011-08-03
> **HPA said:**
> It doesn't work in ubuntu 11.04, but I've found this patch for ubuntu 11.04 64bit:
[http://ompldr.org/vOGRtNQ/xserver-xorg-input-synaptics_1.3.99+git20110116.0e27ce3a-0ubuntu11_amd64.deb](http://ompldr.org/vOGRtNQ/xserver-xorg-input-synaptics_1.3.99+git20110116.0e27ce3a-0ubuntu11_amd64.deb)
and it solved the problem!
Attention: After the installation of this patch, you have to lock the xserver-xorg-input-synaptics_1.3.99+git20110116.0e27ce3a-0ubuntu11 package in the Synaptic Package Manager because there is a newer version ( xserver-xorg-input-synaptics_1.3.99+git20110116.0e27ce3a-0ubuntu12) available to download in the Update Manager.
Avoid this update because if you do it, the problem with the touchpad will appear again.

But, what can I do if the update has already been done? 

Have the 4520s with ubuntu 11.04 64 bit, and synaptics does not work properly: 
1. no right click (only in combination with touching the pad), 
2. can not drag and move windows, 
3. can not disable touchpad when typing 
4. touchpad too sensitive: light touch moves the cursor.

help...

---

