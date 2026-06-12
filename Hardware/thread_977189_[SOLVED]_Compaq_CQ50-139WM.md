---
title: "[SOLVED] Compaq CQ50-139WM"
date: 2008-11-10
forum: Hardware
---

### Post by tradiuz on 2008-11-10
I ran the LiveCD to see what hardware issues I might run into before installing Ubuntu 8.10 and found two dealbreakers.

One, the wireless card was detected (it was showing under the hardware drivers tool), but it was not showing up under network manager (The wireless button on the machine stayed Orange, even if I pressed it).  I beleive it is an Atheros AR5007 wireless card (which I've read has issues with the madwifi driver).

That's problem one.  Problem two is probably a much easier fix.  I ran the installer (figuring I could make the wireless work later), and it hung at the partition menu.  It would get to the part about "resizing partitions" and hang at 0% for over an hour before I finally stopped it.

Any help would be much appreciated.

(In case any of you didn't know, this is the $298 laptop from Mal-Wart that comes with Vista Basic on it, which hit shelves Saturday, so it's a bit new on the market)

---

### Post by tradiuz on 2008-11-10
For some reason, when I tried it again, it did the auto partitioning just fine. *shrug*

The fix I ended up doing for the wifi was:

follow the instructions in [http://madwifi-project.org/ticket/1192](http://madwifi-project.org/ticket/1192)

of course, when I ran the updates immediately after, I had to do this all again... ](*,)

Something else, the wired ethernet drivers did not work until I downloaded the first batch of updates.

And I'd like to thank my $15 Edimax USB B/G wifi adapter for making all this possible (since it works out of the box in 5 seconds).

---

### Post by tradiuz on 2008-11-21
OK, I might seem totally crazy for replying to myself again.  But since this is the first hit on google at the moment, I figured I'd flesh this out a bit.


First, get a connection to the internet of some sort (ie a USB network adapter)

Make sure you have the prerequisites.
```

sudo apt-get install build-essential linux-headers-$(uname -r)

```

Disable the existing wireless driver by going to System > Administration > Hardware Drivers

Select the entry for "Support for Atheros 802.11 Wireless LAN cards"

Click Deactivate

As root (because I'm lazy and it's easy).

Get the source tarball, untar it, and get into the directory.
```

cd /usr/src

wget http://snapshots.madwifi-project.org/madwifi-hal-0.10.5.6/madwifi-hal-0.10.5.6-r3875-20081105.tar.gz
tar -xvzf madwifi-hal-0.10.5.6-r3875-20081105.tar.gz
cd madwifi-hal-0.10.5.6-r3875-20081105


```

Go to the scripts folder and run the two pertinent scripts.
```

cd scripts

./madwifi-unload

./find-madwifi-modules.sh $(uname -r)


```

Go back into the source directory, compile and install the driver.
```

cd ..
make
make install
modprobe ath_pci

```

Next you want to edit the /etc/modules so it turns on the atheros driver:

```
echo "ath_pci" >> /etc/modules
```

now restart and you should be good to go.

---

### Post by jokerj5000 on 2008-12-30
Hey you are a life saver im still kinda a new to linux
and your intructions made it where i can connect but i keep having problems with my wpa keys like when i turn on the laptop it connects and everything is fine tell i close the laptop or it sleeps it disconnects and wont reconnect and it shows that the password is long as hell but the real one is only 8 characters
are you having this problem too or im i doing something wrong


oh and another thing thats bothering me i messed with some setting and cant for the life of me figure out what i did but when i open something new the window doesnt come to the front it stays behind windows already open.....     do you know how to fix that

Thanks,
Joker

---

