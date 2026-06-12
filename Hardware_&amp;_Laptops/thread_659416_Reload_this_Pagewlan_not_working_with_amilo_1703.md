---
title: "Reload this Page
wlan not working with amilo 1703"
date: 2008-01-05
forum: Hardware &amp; Laptops
---

### Post by gagatz on 2008-01-05
[this post has been moved from the absolute beginners talk] 

Hello,i have been trying desperatively to get the wlan working with this amilo la 1703, and some other posts suggest, that this is really possible. But anyhow none of those hints i read also in other forums nor the ubuntu wlan guide do work for me.

-   iwconfig gives me:

      lo no wireless extensions.

      eth0 no wireless extensions.

-   i tried this ndiswrapper install with the apropriate driver (which is sis163u) but      
    altough:

    ndiswrapper -l gives me:
    sis163u : driver installed
    device (0BF8:100F) present

-  lsusb suggests that there is at least something like a wlan: notice, that the ID is the 
    same as with the ndiswrapper thing:
   lsusb
   Bus 005 Device 002: ID 0bf8:100f Fujitsu Siemens Computers
   Bus 005 Device 001: ID 0000:0000
   Bus 004 Device 001: ID 0000:0000
   Bus 003 Device 001: ID 0000:0000
   Bus 002 Device 001: ID 0000:0000
   Bus 001 Device 001: ID 0000:0000

-   trying to configure the wlan with the standard tool system -> admin -> network, doesn't show the device anyhow.
What can i do to get it run after all?

thanks

---

### Post by gagatz on 2008-01-07
finally got the wlan running (at least for non encrypted wlans)

supposedly the windows driver (sis163u.inf) is a 32 bit version and does not work with this 64amd linux, try 

dmesg | grep ndiswrapper    : there might be an error suggesting this

----
reinstalled ubuntu gutsy with the 386 version instead of the 64amd: 

if the install does not proceed at initiating local scripts or so then

ctrl + alt +f1   might bring you to a console where you are ubuntu@ubuntu

sudo dpkg-reconfigure xserver-xorg

entering the correct resolution (1280x800)

and

sudo startx


then install the system, partitioning etc.

---

for the wlan:

synaptic:   ndiswrapper-utils ndiswrapper-common
then as suggested by j0lliyo:
download the apropriate driver at fujitsu-siemens.com for amilo la 1703 -> wlan !! winxp driver !!
sudo ndiswrapper -i  /path/to/driver/sis163u.inf   !! make sure that also the file SIS163u.sys is in the directory with the .inf file
then
sudo ndiswrapper -l  should bring something like

sis163u : driver installed 
device (0BF8:100F) present

then 
sudo ndiswrapper -m
sudo modprobe ndiswrapper

ok.

now make sure the wlan is switched on with fn+f2.
try
iwconfig     to see if something shows up (it should show the wlan0 with some informations) if not try rebooting and modprobe ndiswrapper (there could be something missing in the command ndiswrapper -m)

It is much easier to get the wlan working if you have control of a wlan router nearby for which you might switch encryption of for testing. Assume so. And assume further that this router sends its ssid or essid and is set to dhcp.
iwlist scanning     should bring up a list with the available networks
sudo iwconfig wlan0  essid  <youressid>  tells your aerial to search for this router
check
ifconfig for an assignment of an ip at the wlan0 adapter
if not : request an ip with
sudo dhclient wlan0   then the router should assign you an ip

done.

ping scroogle.org   or any other site to test wether wlan0 can reach the web.

----------------------

the sound problem can be solved with the drivers from opensound.org,

thanks to krychek

---------

not solved yet is the secondary monitor issue:  no secondary monitor :-(
and the problem that the onboard sound cannot be muted with the provided opensound driver. so if you plug in earplugs, there will still be the sound out of the onboard 'box'

---

### Post by gagatz on 2008-01-19
it is possible to adjust the sound of the earplugs and the onboardspeaker with

ossxmix (in an xterm)

if you have the opensound package installed properly as suggested above.

---

