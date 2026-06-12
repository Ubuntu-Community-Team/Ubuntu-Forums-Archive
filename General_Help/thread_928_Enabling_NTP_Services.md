---
title: "Enabling NTP Services"
date: 2004-10-16
forum: General Help
---

### Post by CacheMonet on 2004-10-16
Hello.. I'm new to Ubuntu and I need some help... under the time and date settings, there's an option to enable 'synchronize clock'.. but when I click on it, I receive a message saying: "NTP support is not running

Please run NTP support in the system to enable synchronization of your local time server with internet time servers"

I've looked around and cannot find a place to enable it.. can someone please show me where it is??.. thanks for your help

---

### Post by bdoetsch on 2004-10-16
install the ntp server via synaptic. IMHO it's in the universe component.

---

### Post by CacheMonet on 2004-10-17
Thanks.. sometimes everyone needs another person to tell them the simple answer :)

---

### Post by ulefr01 on 2004-10-17
i think you have to adapt the /etc/ntp.con file and add a line likes :
server ntp.xxxxxxxxxxx

please use for ntp.xxxxxxxx here your ntp server of your internet provider

---

### Post by wayover13 on 2004-10-17
I think this advice is wrong.  NTP is installed on Ubuntu: what Ubuntu needs is a client program, not a server.  If you want to update system time from a time server, you need an NTP client, and one comes preinstalled with Ubuntu.  The problem is, Gnome doesn't know about it.  The NTP service in Ubuntu is not properly integrated with the Gnome desktop.  For example, if you select  computer &gt; system configuration &gt; time and date, then click the checkbox beside "synchronize clock with internet server," you get a popup that says > Please run NTP support in the system to enable synchronization of your local time server with internet time servers
But the Gnome interface gives you no way to "run NTP support in the system" so far as I can see.  It seems that somehow this needs to be done manualy--like maybe by editing ntp.conf or some such file.  So the problem here is not that you can't, by some means, make the system update time via the internet.  The problem is that the Gnome interface seems to offer such a thing (by giving a checkbox that can be ticked), but not giving any way to "run NTP support in the system" via the Gnome interface.  Please correct me if I've overlooked some Gnome applet/panel/whatever that lets you "run NTP support in the system."  If Ubuntu's aim is to provide an integrated desktop, it should have this feature fully (not partially, as it currently does) implemented in the UI.

---

### Post by ulefr01 on 2004-10-17
if you install the ntp-server with apt-get then you can use the option to enable 'synchronize clock' and it will possible to add a ntp server. Afterwards you can find this new entry in the ntp.conf file.

---

### Post by Richard Sr Musick on 2005-02-24
Thanks Much ,  after installing the ntp-server with apt-get, all is well. The NTP server was not already installed in my copy.

Rich

---

### Post by Defrector on 2007-07-31
I am a relative newbie but I also suspect that installing the server will not help the client function. I speculate that installing the server will automatically register your computer as a server for your ntp client, but as a result all your ntp client would do is sync your clock to itself! It would definitely stop complaining but I think the process would be somewhat trivial.

I believe the answer lies in the configuration file to register an ntp server. But I don't know where that file is in ubuntu. If anyone knows, I'd be grateful to know. I tried the /etc/ location and cannot find any conf for ntp.

---

### Post by Defrector on 2007-07-31
After some searching I think I figured it out. Using ntpdate one can call a sync of the clock to a remote time server. It was a matter of having the crontab execute:

ntpdate ntp.ubuntu.com pool.ntp.org 

...as root. So I'd suggest the root crontab (cron.daily) be the one calling this, not a secondary user's crontab. The source that told me how to do it: [http://doc.ubuntu.com/ubuntu/serverguide/C/NTP.html](http://doc.ubuntu.com/ubuntu/serverguide/C/NTP.html)

...and I THINK that works. Running the command straight in the terminal as sudo seemed to do it. I'm not sure if kde/gnome's clock automatically just follows ubuntu's linux clock but at least something's synching. If the GUIs don't indeed sync... well then our issue is outside the scope of NTP and is more of an X or KDE/Gnome thing. Probably. :P

On that website are instructions on installing and using ntp, which some might like a bit more. But the abovementioned will work right out of the box with no installs.

Learning as I go; caveat.

---

