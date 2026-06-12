---
title: "wireless almost there..."
date: 2005-12-28
forum: Hardware &amp; Laptops
---

### Post by wwbdd on 2005-12-28
I need help getting the last bit of my wireless setup.  I installed the drivers with the ndiswrapper and was even able to connect to my neighbors unencrypted network on one occasion.  When i tried to enter the wep and use my own network everything broke and i haven't been able to connect to _ANY_ network since then.  I have been using the networking tools under system-administraton but i would like to learn to use the terminal to do this because i know it to be more reliable than gui apps.  Any help here would be greatly appreciated.

---

### Post by Lambert on 2005-12-28
You can find more help at the ndiswrapper wiki.

[http://ndiswrapper.sourceforge.net/mediawiki/index.php/Main_Page](http://ndiswrapper.sourceforge.net/mediawiki/index.php/Main_Page)

As far as command line you're looking at a couple different commands.

to bring up the interface and activatae it

```
sudo ifconfig wlan0 up
```

if you have proper settings in your /etc/network/interfaces this command is the same as clicking on activate and the rest of the commands I'm about to explain will not be necessary. look at man interfaces to see info about that file. (you can also look into the command ifup and ifdown as these commands are called on to accomplish the above command)

and of course to deativate just change up to down

Now once you're up you use the iwconfig command to configure

read the man page as this one is not as encryptic as others so it's understandable.

to connect to your router with open signal command would look like this

```
sudo iwconfig wlan0 essid ____ commit
```

a more complete command would include other stuff such as

```
sudo iwconfig wlan0 essid ____ ap __:__:__:__:__: mode managed channel __ commit
```

for a wep encryption you would add key _____ (look at man page for variations of how to enter for proper setting)

another comand is iwlist. This can scan for routers and show information about them. (not all drivers support this feature)

```
sudo iwlist wlan0 scan
```

---

### Post by wwbdd on 2005-12-28
Well now i'm closer, but i'm still not quite there yet.

There is a blue led power button for wireless (I guess it enables you to turn on the wireless if you are trying to conserve battery, yes i may be a newbie, but i'm smart enough to know to make sure that it is on, so that is NOT the issue). When I did the iwlist thing, the blue led blinked and i was able to see the networks available.  When i commited the wlan0 to the essid of a local unencrypted network, the blue led went on and stayed on, so we are making progress.  At this point i still cannot ping anything.  Next i tried the ifconfig wlan0 up command but i still could not ping anything, but the blue led stayed on.  I feel like i'm almost there and that there is just one thing missing before everything will work right.  Got any advice?

---

### Post by Lambert on 2005-12-28
After running the ifconfig wlan0 up command and the iwconfig ....commit comand run commands just like this

iwconfig

ifconfig

with the iwconfig command we need to look at the second line and see if the access point is populated with the mac of your router

with the ifconfig we need to see inet address: with an ip address assigned to the device (not the inet6 address one)

there might be one more command needed to get an ip from the router. run this after the iwconfig ....commit comand and then run iwconfig and ifconfig plain again and notice if they are different with either an association and ip assigned to the device.

```
sudo dhclient wlan0
```

if I'm speaking in foreign terms to you, you can post output of those commands here.

---

### Post by wwbdd on 2005-12-29
IT WORKS... kinda

I ran through the instructions given again and when i did the dhclient wlan0 thing it just ran for a minute or two and didn't find anything but when i redid all of the commands it found an IP.  At this point in time i was still trying to connect to my neighbors unencrypted network(for simplicity sake, neighbor), which was successful on try #2.  When i tried connecting to my own encrypted network everything once again fell apart and it wouldn't even go back to my old settings that worked to connect to neighbor.  I restarted the computer and again tried to connect to neighbor again and once again dhclient didn't find an ip so i ran it again, this time though i didn't run through the preceeding 3 or 4 steps, or in other words i ran dhclient twice in a row.  The second time it found an ip in a matter of a secord or less  wheras the first time it came back empty handed after more than a minute.

So then the only remaining questions are:
1) how do i configure it to connect to my encrypted network
2) a new one--When i boot up the computer it takes _FOREVER_ to get through the networking steps (there are two of them, i can't recal exactly what they are, but regardless it took 2:13 to get through them, i timed).  It seems like either there is some sort of configuration that i need to write to a file such as /etc/networking/interfaces so that it will find and connect to a network during the boot process instead of looking for one that doesn't exists and then hitting it's head against the wall for another 2 minutes wondering why it can't connect.  But then what is it to do if I am outside of my normal network range and i want to boot the computer, do i have to wait for the 2 minutes?

Thanks again for all the help.

---

