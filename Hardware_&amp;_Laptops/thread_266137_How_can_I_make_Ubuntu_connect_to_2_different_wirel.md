---
title: "How can I make Ubuntu connect to 2 different wireless networks automatically?"
date: 2006-09-26
forum: Hardware &amp; Laptops
---

### Post by OpticalIllusion on 2006-09-26
I want to have like two different wireless network profiles that Ubuntu will automatically connect to when they come into range, much like Windows does.  Basically, I don't want to have to go and reconfigure everything when I get to school and connect to their wireless network.  How can I do this?

---

### Post by K.Mandla on 2006-09-26
I'm not exactly sure, but I think if you use the Network panel you can configure a new "place" (is that right?) and switch between them through that menu. I think that's the general idea.

Sorry I can't be of more help on that one.

---

### Post by OpticalIllusion on 2006-09-26
I think I can set it up that way, but the network config control panel is so slow!  Any fix to that?

---

### Post by ltmon on 2006-09-26
Another solution is to use NetworkManager, which I've found to be really good.  It's not in by default because it's still quite new, but I haven't had any stability problems.

[https://help.ubuntu.com/community/WifiDocs/NetworkManager](https://help.ubuntu.com/community/WifiDocs/NetworkManager)

---

### Post by NooneReally on 2006-09-27
yup, network manager is definitely the way to go....and if your wireless isn't detected after a resume due to slowness awaking a quick sudo killall NetworkManager; sudo NetworkManager will solve the trick and get things back to normal without a reboot.

---

### Post by prana on 2006-09-27
Another vote for network manager but it can get a little flakey at times. I have had to uncheck the enable networks menu item and check it again to allow it to sense the new list of wireless networks from time to time.

---

### Post by OpticalIllusion on 2006-09-28
Well, I have network manager.  Now, I need to figure out how to configure it.  Right now, it's just at sitting in the top panel with a red X next to it.

---

### Post by NooneReally on 2006-09-28
sudo gedit /etc/network/interfaces

comment (#) out any mention of your wireless interface then restart NetworkManager. NM by default manages any non-managed interface.

---

### Post by OpticalIllusion on 2006-09-28
> **NooneReally said:**
> sudo gedit /etc/network/interfaces

comment (#) out any mention of your wireless interface then restart NetworkManager. NM by default manages any non-managed interface.
Thanks.  I'll give it a try.

---

### Post by eylisian on 2006-09-28
Network Manager is a cool tool. If for some reason you want to delve further into configuration you should look at the wireless-tools page;
 [http://www.hpl.hp.com/personal/Jean_Tourrilhes/Linux/Tools.html](http://www.hpl.hp.com/personal/Jean_Tourrilhes/Linux/Tools.html)
I am pretty certain (but not beyond a doubt) that wireless-tools is a dependancy for Network Manager as it most likely uses the iwtools suite.

If for some reason Network Manager flakes out on you you can bail out with the shell :)

peas.

---

### Post by OpticalIllusion on 2006-09-28
I got it working now.  Only thing I notice is that my signal strength is now only 85%, ±2%.  With the original one, my signal strength was about 98%-99%.  Why is this?

---

### Post by nosaj97 on 2006-09-29
> **NooneReally said:**
> sudo gedit /etc/network/interfaces

comment (#) out any mention of your wireless interface then restart NetworkManager. NM by default manages any non-managed interface.

ahh that helped me alot... thanks!
should i just comment out everything for good measure? so it manages everything??

---

### Post by ltmon on 2006-09-29
Comment out everything except the loopback interface ("lo").  It's still required.

Any wired or wireless interface should be commented out however.

---

### Post by NooneReally on 2006-09-29
> **ltmon said:**
> Comment out everything except the loopback interface ("lo").  It's still required.

Any wired or wireless interface should be commented out however.

yeah :) scuse me for not mentioning that...leave lo uncommented, any others are up to you.

---

### Post by radiobuzzer on 2006-12-27
A great trouble here, Atheros onboard wireless card. After upgrade to Edgy, the network manager cannot detect any wireless connections. This is the entire annoying procedure I follow to connect:

* I type 'iwlist scan' in a terminal
* I look at the list for the most powerful and open network
* Then I go to network settings and TYPE the SSID of the network I chose (after Edgy there is no more an SSID dropdown list to select from)
* Finally I create a new network profile, so that I can reconnect easily in case I am again at the same place at the future. 

Though, it is a long procedure, Windows would just have connected in a few seconds.

---

