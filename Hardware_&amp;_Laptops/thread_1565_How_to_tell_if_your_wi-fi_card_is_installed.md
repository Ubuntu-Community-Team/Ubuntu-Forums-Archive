---
title: "How to tell if your wi-fi card is installed"
date: 2004-10-21
forum: Hardware &amp; Laptops
---

### Post by tmccartney on 2004-10-21
After lots and lots of wrangling, I may or may not have gotten my Microsoft MN-520 wireless network PCMCIA card working.  It's not picking up my AP or anything wacky or useful like that, but I feel like I'm getting there.

What commands can I issue from the terminal to determine whether the card is actually installed?

And will I have to go into a config file somewhere and set up my AP, or should my card pick it up automagically if it's really working?

Thanks!

---

### Post by harvie_krumpet on 2004-10-22
Check the results of
```
iwconfig
```
It should result in something like this
```
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11b/g  ESSID&#58;&quot;XXXXXXXXXXX&quot;
          Mode&#58;Managed  Channel&#58;11  Access Point&#58; MM&#58;MM&#58;MM&#58;MM&#58;MM&#58;MM
          Bit Rate&#58;54Mb/s   Tx-Power=31 dBm   Sensitivity=20/200
          Retry min limit&#58;8   RTS thr&#58;2347 B   Fragment thr&#58;2346 B
          Link Quality=178/0  Signal level=-43 dBm  Noise level=-200 dBm
          Rx invalid nwid&#58;0  Rx invalid crypt&#58;0  Rx invalid frag&#58;0
          Tx excessive retries&#58;0  Invalid misc&#58;0   Missed beacon&#58;0

sit0      no wireless extensions.
```
where "XXXXXXXXXXX" is your APs' ESSID and MM:MM:MM:MM:MM:MM its MAC address.
Since your AP probably doesn't broadcast the ESSID for security reasons, you have to provide it in /etc/network/interfaces, which should look similar to this:
```
# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet dhcp
name Ethernet LAN-Karte

auto eth1
iface eth1 inet dhcp
name Drahlose LAN-Karte
wireless_essid XXXXXXXXXXX
wireless_key nnnnnnnnnn
wireless_mode Managed
```
where nnnnnnnnnn is a 10-digit number (!) for your WEP-key. You might have to adjust the settings on your AP for that - at least I had to...

Good luck!

---

### Post by sfw5000 on 2004-10-22
You can also do it through the GUI -- Under the Computer menu go to System Config--Network. If you don't see your card listed in there click ADD+ and see if this wizard picks it up. If it is listed, click Properties to enter the ESSID... In my experience Ubuntu is WAY better at picking up wireless cards than any other distro I've used, but I haven't tried it with your card.

Good luck, post back with the results!
Sam

---

### Post by jsgotangco on 2005-01-13
what should I do if my the wireless component of my centrino laptop isn't even detected? I am using an ECS G551 laptop. Centrino works on Mandrake flawlessly btw..but I want to use Ubuntu...

---

### Post by ubuntu-nerd on 2005-01-19
Did you ever get your MN-520 card working?  I am trying...and trying to get mine working but so far everything is no go.  I really don't want to go buy another card tomorrow.

---

### Post by ubuntu-nerd on 2005-01-19
To be honest I don't know what I did but my MN-520 is now working and I am posting this message from it.  Here is what i think happened that made the difference (hopefully this will help a Googler in the future):

Fixed up the /etc/pcmia/config file with 

card "Microsoft Wireless Notebook Adapter MN-520 1.0.3"
version "Microsoft", "Wireless Notebook Adapter MN-520", "", "1.0.3"
bind "orinoco_cs"

Then I went in the network config and added the card via the GUI

then edited the /etc/network/interfaces this way

auto eth0
iface eth0 inet dhcp
name Microsoft MN-520
wireless_essid wifiken


Then I restarted and left the card in -- when i booted back up i was stunned that I was actually able to connect to the internet.  Hope this helps.  But at any rate MN-520 is confirmed to WORK!

---

### Post by stormy on 2005-02-08
I am reasonably new to linux in general, and decided to have a bash at hoary after a month or two with warty.  Thanks to these posts I have managed to get my wireless card working!  Thanks!

Christina :-)

---

