---
title: "Atheros AR242x on 8.10"
date: 2008-12-07
forum: Hardware
---

### Post by phiredesign on 2008-12-07
This is an absolutely huge subject on the web, but I have tried everything and still cannot get it to work. I a very new linux user, but I am following directions word for word.
I am using the guide on [http://wireless.kernel.org](http://wireless.kernel.org) on installing the latest build compat-wireless-2008-12-06.tar.bz2. But once I get to the "sudo make install" portion, it prompts me for my password, yet won't let me enter it at all, it wont let me enter anything. Does anyone know of any other possible solution?
I have an emachines d620 and have found people online who have used various methods with a high rate of success, but for some reason it just wont work for me. Thank you very much for any help. I am a graphic designer looking to switch completely to linux in the future, so I really hope I get the hang of this.
Thanks Again.

---

### Post by bl4hbl4hbl4h on 2008-12-08
enter this in the terminal
sudo wget [http://snapshots.madwifi.org/madwifi-hal-0.10.5.6-current.tar.gz](http://snapshots.madwifi.org/madwifi-hal-0.10.5.6-current.tar.gz)

after the download finishes, type in tar zxvf madwifi-hal-0.10.5.6-current.tar.gz

then type in cd madwifi-hal-0.10.5.6-r3879-20081204

then sudo make

finally sudo make install

note: when it prompts you for your password, it doesnt show it but you're actually typing it in

dang it...darn hyperlink...its supposed to be [http://snapshots](http://snapshots). madwifi.org/ madwifi-hal-0.10.5.6-current.tar.gz without the spaces

---

### Post by phiredesign on 2008-12-08
That worked great, thank you very much. I am however having another problem at the moment. My network is installed (I am using ATT and a 2wire wireless modem), but I still cannot connect. I have pinged the router and it turns out fine, and I think my setting are right, but still no connection.
SSID: 2WIRE927
Mode: Infrastructure
BSSID: blank
MAC Address: blank
Security: WEP 40/128-bit Key
Key: 6767676767 (custom key for testing connection)
WEP Index: 1
Authentication: Shared Key


Should any of this be changed? Thank you for all of the help.

---

### Post by squidx on 2009-02-06
To anyone who is having Atheros 242z problems on 8.10 intrepid, I would recommend using the "backports" drivers from the standard repositories, which worked great for me and I didn't have to compile anything or rely on madwifi, which I have to say looks a bit sketchy given the state of their website.

It's just a single apt-get, and then using the Hardware Drivers control panel.

Here's a reference to doing it: 
[http://unsharptech.com/2008/10/31/atheros-wireless-in-ubuntu-810-intrepid-ibex/](http://unsharptech.com/2008/10/31/atheros-wireless-in-ubuntu-810-intrepid-ibex/)

It took almost no time with my emachines E520 from woot!, except for 2 reboots and my wireless was up and running painlessly.

---

### Post by Jimro on 2009-02-06
The backport worked for me until I installed some kernel updates, after that the backport install didn't fix the problem.

These instructions worked [http://blog.hyperandy.com/2008/11/01/atheros-ar242x-ubuntu-810-ibex/]("http://blog.hyperandy.com/2008/11/01/atheros-ar242x-ubuntu-810-ibex/")

If you are new to Linux, don't be intimidated by the terminal, just follow the instructions and remember to change the date stamp on the files to the the newest date stamp.  For example:

cd madwifi-hal-0.10.5.6-r3879-20081204

You would change the date stamp from 20081204 to to 20090205 (you can find the exact timestamp by opening the madwifi websight).

If the backport works for you then that is awesome.

Jimro

DOH: Same reference as above.

---

