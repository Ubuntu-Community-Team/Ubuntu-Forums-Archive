---
title: "Asus u36jc wireless connects but cannot reach internet on 11.04"
date: 2011-05-22
forum: Hardware
---

### Post by AllNamesRTaken on 2011-05-22
Hi,

Im a very fresh linux user with an Asus u36jc laptop with a fresh install of Ubuntu 64bit 11.04, updated with all the latest recommended stuff using the update manager. Except all the "normal" issues with this laptop such as nvidia card, harddrive spindown etc. covered in this post: [http://ubuntuforums.org/showthread.php?t=1705406](http://ubuntuforums.org/showthread.php?t=1705406), I have problems with my wireless.

It does show in ifconfig & iwconfig and it asks for the wpa2 key and sais that it does connect to my router. But I cannot ping it, nor do I get namelookup to it or the internet, and naturaly I cannot get on the Internet. As I havent used linux for like 10 years or so I am a bit in the dark.

The card works fine when I run Windows 7 and if I connect using a cable everything flys just fine.

I dont know if it matter but I live in an area where it shows like 30 wlans in my wlan list where I pick which one to connect to.

Anyone feel like a guru and have a clue as of whats wrong with the setup (besides a newb behind the keys)? 

Thnx,
J

---

### Post by cayphed on 2011-05-22
I had a simaliar problem with a 3g usb wifi router, I ended up simpally reseting the router itself to factory delfaults then configuring how i want it from there...
To do this try reseting it with a reset button on the back of the router, or, linking directly with a LAN cable to log on to the router and reset it that way.
I later found out that this particular router I used to have was suspecting me to be "intruding" into the network....
Might have been just me, but hey, it's worth a shot.

---

### Post by AllNamesRTaken on 2011-05-22
Well its a router from my internet supplier so its kind of reset by default. I havent changed a thing since I got it.

Anything I can do to find out where the connection fails, like in tcp connection, IP transfer, name lookup, package transmission or assembly etc..

???

---

### Post by cayphed on 2011-05-22
In windows hit *super + R *(super is windows key), the run command will pop up, 
type *cmd* into the box and hit enter, it will take you to the command prompt,
next, enter the command *ipconfig /all *(include the space-slash-all) this will show you all the need's to know with your network,
my next piece of advice is to simply (I'm a newbie as well) copy and paste the list of jargen into notepad, save it somewhere you can grab it in ubuntu, then basicall try to get both the list of jargen and your ubuntu network to look the same.

---

