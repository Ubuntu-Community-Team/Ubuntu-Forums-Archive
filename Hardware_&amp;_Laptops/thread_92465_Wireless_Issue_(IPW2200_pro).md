---
title: "Wireless Issue (IPW2200 pro)"
date: 2005-11-19
forum: Hardware &amp; Laptops
---

### Post by Matthias4444 on 2005-11-19
Im using the intel pro wireless chipset and i just made the switch from suse to ubuntu.  For the most part I'm liking ubuntu the ui is clean the install was really easy.  The only issue I'm having is with my wireless.  It is detecting the wireless card and I can see it in iwconfig and is connected to my AP but there is no internet.  At first it wasnt located in ifconfig but i fixed that with "sudo ifconfig eth1 up".  Still no internet.  My next step was to run a scan "sudo iwlist eth1 scanning" but it says no scan availible.  I'm confused... any help will be much appriciated.

---

### Post by akniss on 2005-11-19
This is a wild hunch,, but do you have an Actiontec residential gateway as your wireless router?

---

### Post by souki on 2005-11-19
[QUOTE=Matthias4444]My next step was to run a scan "sudo iwlist eth1 scanning" but it says no scan availible.  I'm confused... any help will be much appriciated.[/QUOTE]

Are you sure the eth1 is the right interface? on my system the wireless shows as eth1
under gnome it is quite easy to configure the network: "System > Administration > Network"

---

### Post by beijingjj on 2005-11-19
first, do an "iwconfig" just to make sure it recognizes the card.  Assuming it's eth1 configure the card with something like

```
iwconfig eth1 essid linksys key 0123456789 mode managed
```
(0123456789 is your key if you're using wep, otherwise leave the key part out)

issue the "iwconfig" command again.  You should see the MAC address of the AP you are associated with.  If so, and assuming you're using dhcp just issue:

```
dhclient eth1
```

you should now have an ip address if you type "ifconfig" and should be configured.

---

### Post by Lambert on 2005-11-19
have you tried to ping anything?
1. ping your router
2. ping an external site (66.249.64.49)
3. ping using common name ([www.google.com](www.google.com))

If you are ok using the ip addresses but not common name then check your dns settings in /etc/resolv.conf

---

### Post by Matthias4444 on 2005-11-19
The router is a linksys and its getting the ssid but not mac of the router.  Attempts to ping my router have come up saying im not connected and like I said the web browser isnt working so I haven't even tried an external ping yet.

---

### Post by Lambert on 2005-11-19
> I can see it in iwconfig and is connected to my AP but there is no internet 
Your first post said you were connected to the router so the pings were to check if ip address was assigned, and check to see if it was a dns problem. 

So if you're not connected at all then let's go back one step.
Have you checked the channel/freq?
If you 
sudo iwlist <device_identifier> scan
can you see the router?

Are you using any encryption (wep or wpa)?
If wep is it an open or shared encryption? ascii or hexadecimal?
If wpa have you installed wpasupplicant

I saw another post where this chipset was used and disabling the ethernet interface solved their problem.

---

### Post by Vorian on 2005-11-19
On hoary, I tried like heck to get my wifi to work.  After config and reconfig after reconfig, all it took was for me to hit fn f2 to turn on the card.  There is a bugzilla with the wifi led on some laptops, which is what confused me..

---

### Post by Matthias4444 on 2005-11-20
Ok if i do iwconfig it provides the ssid Carey (my routers name) i ran through and configured the settings by hand in iwconfig.  I tried to do "sudo iwlist eth1 scan" but it says no scans detected.  There is no encryption on the network as once this is corrected ill go back to my ssh encryption method (I'm not using the ssh tunneling deal at the moment so thats not the issue)  On my computer the wireless is configured by a switch and I've made sure its on.  Why do these things always happen to me...

---

### Post by raghav_p on 2005-11-20
First time I configured IPW2200 on my notebook, I had to disable and re-enable the "eth1" interface and then restart the computer. Worked ever since :)

---

### Post by Vorian on 2005-11-20
You also might try disabling the wep/wap.  If that helps you connect, you can reconfig your ap encryption, and restart your computer.  

Both hoary and breezy have this driver, I have the same card.  Like i posted earlier, it took me a little work to get it going, but in the end it had nothing to do with the card or the driver ~ it was a carbon based error:) 

I seem to have alot of those.....

---

### Post by Matthias4444 on 2005-11-20
I tried turning off and back on the eth1 but that didn't work. I tried to turn on the eth1 and then go into the gui Network Tools but it will not allow me to configure the connnection.  The protocol in eth1 is IPv6 which i know it shoulden't be....  So that could be the problem how do I set it up to only use IPv4 addressing via the terminal?

---

### Post by Matthias4444 on 2005-11-20
I tried turning off and back on the eth1 but that didn't work. I tried to turn on the eth1 and then go into the gui Network Tools but it will not allow me to configure the connnection.  The protocol in eth1 is IPv6 which i know it shoulden't be....  So that could be the problem how do I set it up to only use IPv4 addressing via the terminal?

---

### Post by Vorian on 2005-11-20
[QUOTE=Matthias4444]I tried turning off and back on the eth1 but that didn't work. I tried to turn on the eth1 and then go into the gui Network Tools but it will not allow me to configure the connnection.  The protocol in eth1 is IPv6 which i know it shoulden't be....  So that could be the problem how do I set it up to only use IPv4 addressing via the terminal?[/QUOTE]

first, what do you get when you use this?

```
dmesg | grep 'ipw'
```?

---

### Post by ruffneck on 2005-11-20
have you tried "Wifi-radar" ? It is a nifty little program that can allow you to setup your wireless interface and create profiles (ie. work, home etc.) 

You can find the program in the breezy repos. Alternatively, you can check out the link below for more info.

[http://www.bitbuilder.com/wifi_radar/](http://www.bitbuilder.com/wifi_radar/)

I've got ipw2200 myself in my Dell 700m and I installed Wifi-radar using Synaptic then from a terminal did ```
killall gnome-panel
``` Then you will find the program under...Applications....Internet. Run that and you should be good to go if you configure it correctly.

---

### Post by Matthias4444 on 2005-11-21
So that program is in the standard repos? sorry im new to the apt-get repo deals I'm used to doing it the make file way.  Also do you know where i can find the repos for kismet if this works?

---

### Post by Paul Chang on 2006-01-21
[QUOTE=Vorian]first, what do you get when you use this?

```
dmesg | grep 'ipw'
```?[/QUOTE]


I have a similar problem. When I tried "dmesg | grep 'ipw'", the last two lines look like:

" IPW2200: Detected Intel PRO/Wireless 2200BG Network Connection"
" IPW2200: Firmware error detected. Restarting".

---

