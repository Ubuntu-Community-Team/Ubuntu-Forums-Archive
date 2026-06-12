---
title: "easy switching between wireless networks??"
date: 2005-01-04
forum: Hardware &amp; Laptops
---

### Post by amandla on 2005-01-04
I was wonder if there is an easy way to switch between wireless networks? 
When I install ubuntu on my laptop, it detected the centrino without any trouble. It deteted my home network and I have been on the web since. However, I am starting school this week, and I normaly bounce around different coffee shops with wireless access. Is there any apps which would allow me to detect/switch network easily? Something similar to M$ XP ? 

Oh and any info on getting access to a LEAP/PEAP network would be nice too. My school is using LEAP/PEAP, however, their docs only cover windows and mac.  :( 

thankx

---

### Post by Shaggy on 2005-01-04
Using the command console you can scan and connect to whatever wireless networks you want.  You should have wireless tools installed automatically. If not apt-get it.

Then from the command line as root you can do

#>iwlist <wlan0 or whatever> scan
That'll give you a list of everything your wireless card can see.  Then

#>iwconfig <wlan whatever> essid <AP you want>

#>dhclient <wlan blah>

I know it's not as clean as the M$ way but the plus is if you switch distros anytime it'll work no matter what.

---

### Post by amandla on 2005-01-05
Thankx dude!
Now i just got to get leap working and i am fine ;)

---

### Post by az on 2005-01-05
waproamd is in universe.  Is that also helpful?

---

### Post by nehalem on 2005-01-06
Can anyone confirm if Hoary will include GUI tools for easy switching a la Mac OS X?

While command line isn't too bad it's really not that great either, this is really needed IMHO.

---

### Post by Shaggy on 2005-01-06
I'm sorry I don't need a GUI to connect my wireless set up and more importantly don't want one.  I like keeping it at command line using a universal package that is a base for wireless connection, for the reason that it is universal and if I ever change distro's I don't have to relearn something.  Also is more reliable for controlling it.

If a GUI for wireless became available in this I would much rather prefer it as an option  to use than to have it be the way it works.  I don't even use the GUI for getting the ethernet card up and running though.  So I might be wierd like that  :-k

---

### Post by nocturn on 2005-01-06
[QUOTE=amandla]I was wonder if there is an easy way to switch between wireless networks? 
When I install ubuntu on my laptop, it detected the centrino without any trouble. It deteted my home network and I have been on the web since. However, I am starting school this week, and I normaly bounce around different coffee shops with wireless access. Is there any apps which would allow me to detect/switch network easily? Something similar to M$ XP ? 

Oh and any info on getting access to a LEAP/PEAP network would be nice too. My school is using LEAP/PEAP, however, their docs only cover windows and mac.  :( 

thankx[/QUOTE]


There is a Gnome-applet to do that (saw it in an article,  but cannot remember the name), it is not installed on Ubuntu, but maybe you can find/use that one?

Good luck

---

### Post by amandla on 2005-01-06
GUI vs. cmd line = preference. You perfer GUI use GUI and vice versa
However, for mainstream desktop use there will need a GUI for as much stuff as possible ...IMO

waproamd is dead and replaced by wpa_supplicant, however it is not in the repositiories. an other alternative is xsupplicant, however, i still have not tried using it so i don't know if it will solve my problem.


i will keep everyone updated

---

### Post by jerome bettis on 2005-01-20
[QUOTE=amandla]GUI vs. cmd line = preference. You perfer GUI use GUI and vice versa
However, for mainstream desktop use there will need a GUI for as much stuff as possible ...IMO

waproamd is dead and replaced by wpa_supplicant, however it is not in the repositiories. an other alternative is xsupplicant, however, i still have not tried using it so i don't know if it will solve my problem.


i will keep everyone updated[/QUOTE]
 sudo apt-get install netenv

it's a little difficult to set up on a debian based distro, but it's sweet once you get it taken care of.  just read the doc, there's a good bit on debian setup.

basically when your laptop brings up the interface you get a menu with all of the network environments you've setup.  you select one, and it's pretty much just a shell script that links /etc/network/interfaces to the right one you selected.

it's really only useful if you regularly connect to networks.  if you're moving around from coffee shop to coffee shop, it's not worth it.  but i pretty much just use 2 different networks, at home, and at class.

before i found out about netenv i just left all of the interfaces but the one i was using at the moment commented out in the /etc/network/interfaces file and switched the comments as i moved around.

---

### Post by malmjako on 2005-01-21
I use WiFi Radar quite successfully. It gives you a list of available access points and lets you connect to them. Supports WEP keys. Get it at gnomefiles.org!

---

### Post by ming0 on 2005-01-23
Wifi Radar seems to work pretty well, thus far...

To get it going on ubuntu, you need to do some stuff:

Get the program at [http://www.bitbuilder.com/wifi_radar/](http://www.bitbuilder.com/wifi_radar/)

go to the directory you downloaded the tarball to and:

tar -xzvf wifi_radar-1.1.tar.gz

sudo mkdir /etc/conf.d/

sudo cp wifi_radar.svg /usr/share/pixmaps/wifi_radar.svg

Now use an editor on the file called wifi_radar.py

And make the top look like mine:

# Defaults, these could be different for your distro.
CONF_FILE               = "/etc/conf.d/wifi_radar.conf"
IWLIST_COMMAND  = "/sbin/iwlist"
IWCONFIG_COMMAND= "/sbin/iwconfig"
IFCONFIG_COMMAND= "/sbin/ifconfig"
DHCP_COMMAND    = "/sbin/dhclient"
ROUTE_COMMAND   = "/sbin/route"
SAY_COMMAND             = "/usr/local/bin/say"

Now you can run the file from wherever you want (as root):

sudo ./wifi_radar.py --config

and drag and drop to make networks take priority...

have fun!  (I still don't know how to make it stay in the taskbar, but if I figure that out, i'll make another post)

---

### Post by ceekay on 2005-01-24
I like wifi radar too- just a note though, the new version of gnome (2.9) that is included in the hoary distro has a gui for configuring wireless networks. It's still a little weird sometimes, but it's nice to know it's on its way. 

As for the dude who posted  a command-line for wifi networks, you must not use very many networks with WEP. I use 3-4/day and having a gui remember settings / see new networks / switch networks is invaluable (let alone less typing).

---

### Post by ming0 on 2005-01-24
I'm using the network config tool in Hoary, and I really don't like it... Also, it won't scan for networks like the radar will :)

(tho I have a link to radar on the taskbar, I still have the wifi/network widget there too)

---

### Post by J D Wijbenga on 2005-01-24
I use the Gnome Netapplet. This works pretty good in Warty.

Here is the applet in action from the blog of [Miguel de Icaza](http://primates.ximian.com/~miguel/activity-log.php) .
[IMG]http://primates.ximian.com/~miguel/images/wireless.png[/IMG] 

You can find it [here.](http://debian.experimentos.cl/debian/pool/main/n/netapplet) 

JD

---

### Post by ming0 on 2005-01-24
I'm trying it, and it isn't going well for me... I'm using hoary, and chose the .099.4-1 version of the package.

I don't have the icon in the panel (it's just a blank square), and it constantly resets my connection (once every 3 seconds).

Did you have to mess w/ anything in particular to get it going?

BTW, it looks perfect! Like the exact thing that I've been looking for :)

---

### Post by J D Wijbenga on 2005-01-24
[QUOTE=ming0]I'm trying it, and it isn't going well for me... I'm using hoary, and chose the .099.4-1 version of the package.

I don't have the icon in the panel (it's just a blank square), and it constantly resets my connection (once every 3 seconds).

Did you have to mess w/ anything in particular to get it going?

BTW, it looks perfect! Like the exact thing that I've been looking for :)[/QUOTE]
 I use it in Warty at home. I installed it. Went to Applications>Other> and selected the Networkselector which made it appear in the top panel. I has not workt as easily for me as it has for Miguel, but it has worked. Unfortunatly I do not have enough wireless networks in my suroundings to test it thoroughly.

At work I have installed the same netapplet you have used in Hoary. It works but sometimes better than at other times. I think this also has to do with the Network settings programma which is not realy stable or dependeble on my system.

JD

---

### Post by nivex on 2005-03-06
Hello folks!

I've done some tweaking on wifi-radar for work, mostly adding GUI feedback for when its doing something.  I've tried to send my patches back to the author but never got an answer.  My coworker started a SourceForge project to manage the revised code:

[http://sourceforge.net/projects/wifi-radar/](http://sourceforge.net/projects/wifi-radar/)

Feel free to suggest updates, bugs, etc.  And if you hear from the original author, let him know!  We want to work with him, not against him.

-- Kevin

---

### Post by ming0 on 2005-03-06
Awesome to hear--this is one thing that Linux really needs developed... I've been looking for a long time for wireless scanners and automation stuff for my laptop!!

I have a few suggestions, but I'm not much of a coder, so I don't know if I can help :(

The biggest suggestion would be to turn it into a panel applet that will autostart and sit in the task tray (panel). The other suggestion would be some sort of gui to select an interface, and an error pop-up if there are no interfaces that support scanning.

I am very interested in seeing a tool like this be developed, and if you need someone to be a package maintainer for an ubuntu version, I'd be glad to learn/teach myself how to do this.

The other thing I have to offer are my web design and graphics editing skills... Send me a PM if you need my help, or have any other side jobs or non-coding work you need done on this project :)

--Dean

---

### Post by alastair on 2005-03-06
This is the sort of thing that will be a big help - Network Manager :

[http://www.redhat.com/magazine/003jan05/features/networkmanager/](http://www.redhat.com/magazine/003jan05/features/networkmanager/)

I do not think it is quite ready for proper release - but works for some people.

---

### Post by yippy on 2005-03-08
I just wrote a simple shell script to swap interfaces.  I also change between dhcp networks at client locations and a static IP at home, and some of the DHCP networks like to overwrite my resolv.conf, so my script changes out the /etc/network/interfaces and /etc/resolv.conf for each network, then restarts networking if I'm moving to a static IP or lets me restart manually if I'm going to dhcp (so it doesn't sit forever looking for a dhcp server that isn't there), then shuts down the old interface if I'm going between wlan and eth.

I was surprised how seamless linux handles the switch.  Using AIM my contacts couldn't tell when I switched from wlan to eth, which is exactly what I hoped for.  Maybe I should have checked for a real solution first instead of writing a script, but it was easy anyway.

Joejoejoe

---

### Post by kermy on 2005-04-09
[QUOTE=nivex]
Feel free to suggest updates, bugs, etc.  And if you hear from the original author, let him know!  We want to work with him, not against him.
[/QUOTE]

It seems that the official project has been updated and the AUTHORS file lists you and your coworker as coauthors. The sourceforge page has not been updated yet though.

I have a bugreport, but don't know where to turn. Anyway, I updated the settings of my current connection and pressed connect. It found the ip address, but the interface did not get activated.

Also auto is not selected by default for options in profiles.

---

### Post by Vorian on 2005-07-06
Good info!  Helped me with a couple of issues!

---

### Post by phen on 2005-07-27
i just tried the suggestion wifi-radar, and i like it a lot! it connects me on startup to the available network. the next question is, whether it is able to automatically connect to a WEP secured network, after i saved its key in the profile, or not. i can try this next week. non encrypted networks are working perfect! 

wifi radar connects you on startup automatically, while you can still chose from different networks in gnome/kde. VERY NICE!

cheers,

kai

---

