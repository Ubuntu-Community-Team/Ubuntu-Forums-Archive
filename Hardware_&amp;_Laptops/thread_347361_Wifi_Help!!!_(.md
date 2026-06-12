---
title: "Wifi Help!!! :("
date: 2007-01-27
forum: Hardware &amp; Laptops
---

### Post by ESPOiG on 2007-01-27
help i got my a wireless network just set up and i used windows and my laptop with a 54mbps g wireless card, it works fine and is perfect signal no problems

i have the ssid set to default "default" and a 64bit hex key of eg, cccccbbbbb

now i followed this tutorial [https://help.ubuntu.com/community/WifiDocs/Device/TRENDnet_TEW-421PC_H/W%3aB1_%28ndiswrapper%29?highlight=%28WifiDocs%2FDevice%29]("https://help.ubuntu.com/community/WifiDocs/Device/TRENDnet_TEW-421PC_H/W%3aB1_%28ndiswrapper%29?highlight=%28WifiDocs%2FDevice%29") and i have the car working and everything the lights show up and in networking controls it is show as a wireless device and i can set all the options, as in the first command of the tutorial is says to type this <lspci> so i did and got the exact same output as shown, now everything goes fine up until i get to Step 7 which is type "iwconfig" and after setting the settings for the wireless device you should see them show, and this is what you should get something like this

> user@ubuntu:~$  iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11b  ESSID:"My_Essid"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: 00:08:74:02:01:FC   
          Bit Rate:11 Mb/s   
          RTS thr:2432 B   Fragment thr:2432 B   
          Power Management:off
          Link Quality:95/100  Signal level:-35 dBm  Noise level:-96 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

and this is what i get with no settings that i have set to be shown

> rcollins@ubuntu-linuxbox-1:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

sit0      no wireless extensions.

wlan0     IEEE 802.11b  ESSID:off/any  
          Mode:Managed  Frequency:2.437 GHz  Access Point: Not-Associated   
          Bit Rate:1 Mb/s   Sensitivity=-200 dBm  
          RTS thr:2346 B   Fragment thr:2346 B   
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

this is annoying and i dont know whats going wrong or what i can do to fix it, the card appears to have the exact same chipset as the one in the tutorial but once i get to the step after setting the options nothing works :(

now i have set these options many times over and tried different false one and i have rebooted and made the hardware or whatever stick to the system

im just stuck now, any help would be gratefully appreciated thankyou

---

### Post by rmartz on 2007-01-27
I had to edit my interfaces file:

Open Terminal

sudo gedit /etc/metwork/interfaces

Comment out ( add # in front of the line) any line that does not contain lo or eth1 (this was the device ID of my wireless card).

Save the file. Restart your wireless card. 

Have something soft to hit if it still doesn't work.

Oh, yea. I had to install Wifi-radar. Then it worked. This was just my experience. Hope it helps.

---

### Post by ESPOiG on 2007-01-28
ill give it a go except wlan0 is my wifi device and eth0 is my ethernet i dunno what lo is, the strage thing is that when i scan for a wireless access point or whatever it can find it, it just cant figure out how to see my settings :(

thx ill give it a go

---

### Post by ESPOiG on 2007-01-28
i tried that program and it can detect my wireless network fine, but when i try to connect it fails even though i have entered my security key and set the network name

the network name is "default" could that be a problem :S

---

### Post by rmartz on 2007-01-28
I wouldn't think that would be a problem. Your router just broadcasts a name to identify it's signal. 

I had to # out the wlan stuff in the interfaces file also. 

Did you install Network-Manager-Gnome?

---

### Post by ESPOiG on 2007-01-28
isnt that just the default network manager in gnome, but yeh i didnt # out wlan0 in interfaces but i did do eth1, eth2, and my dialup modem, so i dont know but it is just strange that it wont work atallti sits and trys to connect using wifi radar but then just fails :(

i dunno what to do, but first ill try # out the wlan0

---

### Post by j0sh0 on 2007-01-28
Does the frequency/channel that iwconfig reports match the one your router is broadcasting on?
The essid needs to match the router's.
Also, presuming you're using WEP encrytpion, is the router set to open or shared?
From the top code you posted, you could try "sudo dhclient" (if your router is set up for DHCP), otherwise your have to set your IP address for wlan0 thru ifconfig.
Some more details would be helpful (eg try pinging your server, show the ifconfig output etc)

---

### Post by ESPOiG on 2007-01-29
ok i got it working and in reply to the last post - yes the router is set up to dhcp but for some reason this was the thing that was holding me back, in the end all i had to do was.

load wifiradar and set my options for the network there and then set my dns in the networking control, my interfaces config file is as it should be with lo, eth0 and wlan0 none # out, and all that is set is my ESSID for wlan0

and also when it wasnt working i had set my key and ESSID in the interfaces config, it just wouldnt, show up when i did <iwconfig> as you can see from post 1 and but now that the ip is set manually via wifiradar it works fine i can access the net and do what i wanted, im not sure why the dhcp didnt auto configure it just failed each time, and i only realised this when i tried the program gtkwifi and ran it via terminal and it came up with an error about dhcp

so i dont know i also set the channel via wifiradar program, not sure if that makes a difference but it works and thats all i need now so i aint gunna mess with it

also what is a command to show me signal strength :D

thankyou for your help guys

---

### Post by ESPOiG on 2007-01-29
dont worry im stupid iwconfig shows it, is there any apps that can sit in the sys tray and show me my wifi status or something because i would like to know how it  is running with out the command :D ??

---

### Post by marcthepunk on 2007-01-29
why dont you have a look at this program [NetworkManager]("http://www.gnome.org/projects/NetworkManager/").  it worked for me, easy like pie!

---

