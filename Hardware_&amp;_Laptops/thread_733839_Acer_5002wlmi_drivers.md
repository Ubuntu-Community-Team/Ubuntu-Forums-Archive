---
title: "Acer 5002wlmi drivers"
date: 2008-03-24
forum: Hardware &amp; Laptops
---

### Post by saabuldin on 2008-03-24
I think ubuntu is great but i have tried it several times on my laptop acer 5002wlmi without success which then leads me to give up altogether.

I cant seem to find drivers for my laptop, including the widescreen driver as my laptop is 15.4 inch.

I have also tried finding the wifi driver without success.

This is when i give up as if i cant find simple drivers than what other problems are going to come up later.

I am new to ubuntu and if anyone can help me, maybe il give it another shot.

PLEASE HELP SOMEONE!!!!!!!!!!!

---

### Post by jslman on 2008-03-24
Ok, I'll need some more detailed information. Like what kind of videocard do you have and what kind of wireless lan driver. 
There are several ways to get everything installed so don't despair yet!

Jeroen

---

### Post by saabuldin on 2008-03-24
Thanks alot for replying.

I have a SIS M760GX graphics
Broadcom 802.11g network adapter

---

### Post by jslman on 2008-03-24
Okay, 

for the broadcom drivers I would suggest using the ndiswrapper. You will need the windows drivers of the broadcom card. The do the following:

```

sudo apt-get install ndiswrapper-common ndiswrapper-utils-1.9

```

after this install do:

```

sudo ndiswrapper -i windowsdriver.inf
sudo modprobe ndiswrapper
sudo ndiswrapper -m

```

The wireless module should now be working. Just add ndiswrapper to the /etc/modules to have it working at boot.

For the graphics, well, did the restricted driver utillity have any suggestion for restricted drivers?

Jeroen

---

### Post by saabuldin on 2008-03-24
I will try the broadcom driver as you said.

im not sure about the graphics

---

### Post by jslman on 2008-03-24
For graphics you could try the command:

```

sudo dpkg-reconfigure xserver-xorg

```

Jeroen

---

### Post by saabuldin on 2008-03-24
thanks i will try both and let you know whats happening

---

### Post by saabuldin on 2008-03-24
how do i install broadcom wireless using diswrapper. Can i hav instructions in steps including where to put the codes

---

### Post by jslman on 2008-03-24
Install ndiswrapper

```

sudo apt-get install ndiswrapper-common ndiswrapper-utils-1.9

```

For this howto let's say the broadcom drivers are in /home/drivers and are called BCMXXX.inf
Install the drivers

```

sudo ndiswrapper -i /home/drivers/BCMWLX.inf

```

prepare the driver for modprobe

```

sudo ndiswrapper -m

```

The drivers are now installed, let's load them

```

sudo modprobe ndiswrapper

```

To check if the module is loaded correctly try the following command:

```

jeroen@portable-pinguin:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11g  ESSID:"Homenet"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: 00:0C:F6:31:FB:FE   
          Bit Rate:54 Mb/s   Tx-Power:15 dBm   
          Retry limit:15   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=84/100  Signal level=-51 dBm  Noise level=-52 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:16014   Missed beacon:0

```

The output is like what you should see if a wireless card is indeed installed. 

put ndiswrapper in the /etc/modules file so it looks like this:

```

# /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.

fuse
lp
sbp2
ndiswrapper

```

You should now be able to chose a wireless network via the network manager applet, it will ask you for the codes. 

If questions remain just put them down and I'll answer them.

Jeroen

---

### Post by saabuldin on 2008-03-24
it says it has to be an .inf file

There are alot of files with the windows driver

which one is it

---

### Post by jslman on 2008-03-24
Yep, you will need the .inf file. I don't know the exact name of the driver but it could be something link BCMWL5.inf If that file is not there could you please post a screenshot here with all the files you have for your driver, makes it easier to help

Jeroen

---

### Post by saabuldin on 2008-03-24
i also get this when installing ndiswrapper

E: Couldn't find package ndiswrappr-utils-1.9


it installs the first one but not this one

---

### Post by saabuldin on 2008-03-24
file:///home/shahab/Desktop/Screenshot-802BG%20-%20File%20Browser.png

---

### Post by saabuldin on 2008-03-24
here is screenshot

---

### Post by jslman on 2008-03-24
it should be ndiswrapper-utils-1.9, I made a typo, so the code:

```

sudo apt-get install ndiswrapper-common ndiswrapper-utils-1.9

```

Jeroen

---

### Post by jslman on 2008-03-24
Looking at the screenshot it should be bcmwl5.inf or bcmwl5a.inf.

---

### Post by saabuldin on 2008-03-24
i get this when i put the code in:

shahab@Acer:~$ sudo ndiswrapper -i /home/drivers/bcmwl5a.inf
couldn't open /home/drivers/bcmwl5a.inf: No such file or directory at /usr/sbin/ndiswrapper-1.9 line 219.
shahab@Acer:~$

---

### Post by jslman on 2008-03-24
When I look at your screenshot I see the drivers are not at the locations /home/drivers but at /home/shahab/drivers/802bg/

that means that the command has to be 

```

sudo ndiswrapper -i /home/shahab/drivers/802bg/bcmwl5a.inf

```

Jeroen

---

### Post by saabuldin on 2008-03-24
its done, it says forcing parameter 0-2

---

### Post by saabuldin on 2008-03-24
this is what i got now:

shahab@Acer:~$ sudo ndiswrapper -i /home/shahab/drivers/802bg/bcmwl5a.inf
[sudo] password for shahab: 
installing bcmwl5a ...
forcing parameter IBSSGMode from 0 to 2
forcing parameter IBSSGMode from 0 to 2
shahab@Acer:~$ sudo ndiswrapper -m
module configuration already contains alias directive

shahab@Acer:~$

---

### Post by jslman on 2008-03-24
ok, but if you do 

```

sudo modprobe ndiswrapper

```

What's the output?

Jeroen

---

### Post by djbsteart1 on 2008-03-24
I don't know if you have the widescreen working or not, but it is possible that there is a missed check box that puts the display into widescreen. If that is checked you should be ok.

---

### Post by saabuldin on 2008-03-24
im trying to check if module is loaded but it just says command not found

---

### Post by jslman on 2008-03-24
To see if the module is loaded do 

```

sudo lsmod | grep ndiswrapper

```

---

### Post by saabuldin on 2008-03-24
the modulae is instaaled.

now im on the part

put ndiswrapper in the /etc/modules file so it looks like this:

---

### Post by saabuldin on 2008-03-24
how do i put module in the /ext/modules file

---

### Post by jslman on 2008-03-24
ok, you need to open /etc/modules in an editor. I use nano

```

sudo nano /etc/modules

```

Now the file is openend, just go down with the arrow key and write ndiswrapper below the bottom word.
Now press ctrl+o and the ctrl+x (save and exit)

to check if it worked do 

```

cat /etc/modules

```

If you see ndiswrapper now you can reboot and the module will be loaded automatically.

If you left-click on the network manager applet (top right in your screen if it's loaded)you should be able to chose your wireless network.

Jeroen

---

### Post by saabuldin on 2008-03-24
i pressed ctrol+o

but when i press ctrol+x nothing happens

---

### Post by saabuldin on 2008-03-24
its ok ive done it


now how do i get connected through wireless

---

### Post by jslman on 2008-03-24
I attached a screenshot, in the terminal you see what you should see after issuing the command 

```

sudo nano /etc/modules

```

On the bottom of the terminal screen you can see that the combinations ctrl+x should exit nano and bring you back to the normal terminal screen.

is there any error shown on the bottom of the terminal screen after you do ctrl+o?

Jeroen

---

### Post by jslman on 2008-03-24
ok, if you go to system >> administration >> network you should see the wireless adapter. See the screenshots.

Put the wireless adapter on " roaming mode"  and then close.

Then you can click on the right-top of the screen on the network icon and your network should show up. Just chose it and enter the password for the network as is asked. Now it should work

Jeroen

---

### Post by saabuldin on 2008-03-24
its ok ive done it

how do i actually get connected to wireless internet

---

### Post by saabuldin on 2008-03-24
i dont have roaming mode, only enable this connection

---

### Post by saabuldin on 2008-03-24
this is what i get

---

### Post by jslman on 2008-03-24
Ok, so now fill out your essid, chose the type of encryption and fill out the encryption code. Chose automatic ip configuration and then ok and all should be working. 

If you're not sure about the name of your network do 

```

sudo iwlist scan

```

it will give you a list of available networks.

Jeroen

---

### Post by saabuldin on 2008-03-24
still not working plus the computer icon has disapeard from the corner of the screen

---

### Post by jslman on 2008-03-24
Also after a reboot? Are you sure you entered the right data in the network utility? Can you, after a reboot, give me the output of 

```

iwconfig

```

---

### Post by saabuldin on 2008-03-24
this is what i get in iwconfig

it still isnt working. ive tried all the wpa encryption

---

### Post by saabuldin on 2008-03-24
i somehow got the box where it says enable roaming mode. how do i connect from there

---

### Post by saabuldin on 2008-03-24
now its got the signal bars showing and it says 

wireless connection to din (0%)

---

### Post by jslman on 2008-03-25
Hmm, so roaming mode is on and you were able to connect to the network. That the bars say 0% indicates that you have got not enough signal to really connect or that there is something wrong with the encryption. Can you set the accespoint security to WEP instead of WPA and try again. Sometimes WPA gives you trouble.

Jeroen

---

