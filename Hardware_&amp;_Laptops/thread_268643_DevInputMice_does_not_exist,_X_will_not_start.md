---
title: "Dev/Input/Mice does not exist, X will not start"
date: 2006-09-30
forum: Hardware &amp; Laptops
---

### Post by Ydirbut on 2006-09-30
After upgrading from 5.10 to 6.06, I rebooted my computer. It would not start x, saying it couldn't find module nvidia and GLcore. I switched nvidia to nv and commented out the GLcore line, but now It will not start because it can't find my mouse. I checked, and the input folder does not exist. Neither does psaux. This is the error message it gives me:

(EE) xf86OpenSerial: cannot open device /dev/input/mice
       No such file or directory.
(EE) Configured Mouse: Cannot open input device
(EE) PreInit failed for input device "Configured Mouse"
No core pointer.
Does anybody know how I could rebuild dev/input/mice?

---

### Post by tommcd on 2006-09-30
First backup xorg.conf:
'sudo cp /etc/X11xorg.conf /etc/X11/xorg.conf_backup
Then just reconfigure xorg:

'sudo dpkg-reconfigure xserver-xorg'. If that will not work, then:
'sudo dpkg-reconfigure -phigh xserver-xorg'.
This will allow you to reconfigure xorg. There is a section about your keyboard and mouse in there also. You will then have to reinstall the nvidia driver:
[http://ubuntuguide.org/wiki/Dapper#How_to_install_Graphics_Driver_.28NVIDIA.29](http://ubuntuguide.org/wiki/Dapper#How_to_install_Graphics_Driver_.28NVIDIA.29)
This should get you going again.

---

### Post by Ydirbut on 2006-09-30
> 
'sudo dpkg-reconfigure xserver-xorg'. If that will not work, then:
'sudo dpkg-reconfigure -phigh xserver-xorg'.
 When I try this, it says "xserver-xorg is broken or not fully installed.

---

### Post by tommcd on 2006-09-30
So X still does not start at all? Is that correct? Are you only able to boot to a terminal, with no GUI?
How exactly did you upgrade from breezy to dapper? It sounds like something got broke along the way. Here are some tutorials on upgrading from breezy to dapper:
[http://www.psychocats.net/ubuntu/dapper](http://www.psychocats.net/ubuntu/dapper)
[https://help.ubuntu.com/community/DapperUpgrades](https://help.ubuntu.com/community/DapperUpgrades)
Unfortunately, these may not help you now. You may be able to redo the upgrade following the tutorials I posted.
Also you may be able to install xorg like this:
'sudo apt-get install xserver-xorg' or:
'sudo apt-get install --reinstall xserver-xorg'

I've never done that though, so I am hesitant to recomend it. I can't be sure it will help in your case. Try it at your own risk. If none of this works, perhaps someone else has a better idea. If not, then I'm afraid a clean install may be in order.

---

### Post by Ydirbut on 2006-09-30
> So X still does not start at all? Is that correct? Are you only able to boot to a terminal, with no GUI? Yes.
> 
How exactly did you upgrade from breezy to dapper?
 I upgraded about a month ago, and I don't remember the exact method.
> 
'sudo apt-get install xserver-xorg' or:
'sudo apt-get install --reinstall xserver-xorg
 Whenever I try to Apt-get anything it says:
" the following module have unment dependancies:
python2.4twisted:depends:python2.4twisted-conch"

---

### Post by tommcd on 2006-09-30
I did not realize you upgraded a month ago. I was under the impression you just did it. Was everything working ok up until now? Or did this problem just happen today?
Anyway about the python2.4twisted dependancies, see if you can 'sudo apt-get install --fix-broken python2.4twisted-conch'. Then do the same for python2.4twisted. See if this will work. If not then 'sudo apt-get install --reinstall' both packages. This would be easier with synaptic, but without a GUI you won't be able to use that.
Sorry it took so long to get back, I'll be away from the computer for a bit, but I will return to this thread. Let me know how this goes.

---

### Post by Ydirbut on 2006-09-30
> 
I did not realize you upgraded a month ago. I was under the impression you just did it. Was everything working ok up until now? Or did this problem just happen today? No. The problem happened immediately after the upgrade, but I was too busy to work on it.
> 
Anyway about the python2.4twisted dependancies, see if you can 'sudo apt-get install --fix-broken python2.4twisted-conch'. Then do the same for python2.4twisted. See if this will work. If not then 'sudo apt-get install --reinstall' both packages. This would be easier with synaptic, but without a GUI you won't be able to use that. It appears as though my network card is fscked, as it can't access any internet sites or ping 127.0.0.1

---

### Post by tommcd on 2006-10-01
Ok. but how then are you posting here? I assume you are on a different PC, or is your system dual boot? If it is dual boot, does the system get internet with windows and not ubuntu? If that is the case, then perhaps eth0 just needs to be setup. Try 'ifconfig eth0'. If no response, try: 'sudo ifconfig eth0 up'. This may get you going.
If it is a failed network card, then (obviously) you will need a new one. At least they are cheap.
Sorry I can't be of more help.

---

