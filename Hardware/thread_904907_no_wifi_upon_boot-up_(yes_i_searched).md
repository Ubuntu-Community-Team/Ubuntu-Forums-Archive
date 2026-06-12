---
title: "no wifi upon boot-up (yes i searched)"
date: 2008-08-29
forum: Hardware
---

### Post by mustard675 on 2008-08-29
seems like its a very user-specific problem but i am a complete noob so bear with me please. after a lot of searching i managed to get my wireless card (Netgear Rangemax 240 WPNT511) operational with my network. i used ndiswrapper for the driver and some terminal commands to get it working. hope that was the hardest part.

my problem is, which i expected, that it will not keep whatever parameters I setup and start wifi on system reboot. here are the terminal commands in order for me to get it to work.

sudo iwconfig wlan1 essid MYESSID
sudo iwconfig wlan1 key MYWEPKEY
sudo ifconfig eth0 down
sudo ifdown wlan1
sudo ifup wlan1

any suggestions? i apologize in advance but i am new to ubuntu :oops:

thanks

---

### Post by nicedude on 2008-08-29
Try setting those parameters in network manager as anything you run at the command line will only last until reboot, or you can take those commands and add them to the system startup scripts to have them run at bootup.

If you don't like network manager you could also use WICD instead to manage your wifi connections as it works better for some than the standard network manager. Just google wicd and go to their site if you want to install it as they have directions there that are easy to follow.

Goodluck

---

### Post by mustard675 on 2008-08-29
> **nicedude said:**
> Try setting those parameters in network manager as anything you run at the command line will only last until reboot, or you can take those commands and add them to the system startup scripts to have them run at bootup.

If you don't like network manager you could also use WICD instead to manage your wifi connections as it works better for some than the standard network manager. Just google wicd and go to their site if you want to install it as they have directions there that are easy to follow.

Goodluck

thanks for the quick reply..

network manager doesn't do much with my wireless connection - never worked which is why i needed to do terminal commands

i did have wicd for a short while but even that was not able to make a connection. i was able to see the network with it though. removed once i used the terminal commands to get it to operate.

finally - how do i add my lines to the system startup scripts? that seems like my best option right now

---

### Post by nicedude on 2008-08-29
Here are a few links to how to do that.

[http://www.thekip.nl/2007/08/17/how-to-setup-startup-scripts-in-ubuntu/](http://www.thekip.nl/2007/08/17/how-to-setup-startup-scripts-in-ubuntu/)

[http://www.neohide.com/automatic-start-up-hamachi-for-ubuntu-hardy-heron](http://www.neohide.com/automatic-start-up-hamachi-for-ubuntu-hardy-heron)

Basicaly you just write a script ( which is just a text file with a certain first line and then your commands ) and then make it executable and put it in your /etc/init.d/ directory.

Here I will show you one of my scripts I use to change my wifi adapter into monitor mode and kill off any kismet wifi scanning servers and bring down my wifi even if it is has gotten assigned some other address then ath0 like usual. The first line in conjuction with making the text file executable is saying this is a script and it uses bash as its scripting language. Then you can use any commands you want but things are a little more tricky than at the command line and sometimes things after the sudo or in this case gksudo ( similar thing and worked better for me ) need to be wrapped in "" to work like if you have other varibles to sudo you want to pass and then the command itself. When I run this though it will ask me for my password one time and then do all these commands in about 5 seconds which is way faster than I could type them all. Also notice the second line is a comment line # followed by a space and then whatever you want to put to let you remmember why you wrote it :-) You can have as many comment lines as you want.

#!/bin/bash
# Kill All Kismet & restart monitor mode with madwifi wlanconfig
gksudo --preserve-env "killall -I kismet_client"
gksudo --preserve-env "killall -I kismet_server"
gksudo --preserve-env "wlanconfig ath0 destroy"
gksudo --preserve-env "wlanconfig ath1 destroy"
gksudo --preserve-env "wlanconfig kis0 destroy"
gksudo --preserve-env "wlanconfig kis1 destroy"
gksudo --preserve-env "ifconfig wifi0 down"
gksudo --preserve-env "wlanconfig ath0 create wlandev wifi0 wlanmode monitor"


Hope that helps you figure out how to get it done so to speak, I would make it for you but you should take this as a good lesson and figure it out ( hint you could just drop the sudo from each of your commands and put them inside my "" and delete any extra lines you don't need or copy them and make more :-)

Goodluck and let me know if you get it working

nicedude

---

