---
title: "Will upgrading my WLAN card to a/g/n take me from ~20Mbps to my full ~50Mps?"
date: 2014-11-21
forum: Hardware
---

### Post by travissparks1307 on 2014-11-21
Hello folks, I'm using a Dell Latitude E6400 with Ubuntu 14.04.1 and [this]("http://(http://www.amazon.com/DW1397-Broadcom-Wireless-802-11a-BCM94312HMG/dp/B0099IF5IQ") WiFi card, it's a Dell 1397. I'm currently only getting ~20Mbps on what's supposed to be ~50Mbps. I'm using the bcmwl-kernel-source driver, but I've tested this on Windows 7 Pro as well and it was only getting ~10Mbps (Windows 7 was only used for testing purposes, and is no longer installed, I don't care what it's issue was). I know that this card is a/b/g. I was wondering if I replaced the current WiFi card with [this one]("http://www.amazon.com/Broadcom-Wireless-Internet-Adapter-Netbooks/dp/B002OB0FPI") the Dell 1510, which is a/g/n would I get the full ~50Mbps? Thanks in advance!.

---

### Post by SeijiSensei on 2014-11-21
Are these speeds based on being physically near the router?  If not, go stand next the router and try the tests again to see if the problem has to do with signal strength.

---

### Post by oldsmobile_mike on 2014-11-21
You have an N-rated router?  How many other devices are connected to it?  I'd try plugging your laptop directly in to the router first to test it's speed directly with your ISP, then try with the wireless card, move further away, etc.  Wireless is a complex technology and can be affected by household construction, number of devices connected, interference, size of your antennas (some routers you can add a larger/more powerful antenna), etc.  You might want to look into one of the new AC-capable routers for best performance, and obviously upgrade your network card, too.  ;)

---

### Post by travissparks1307 on 2014-11-21
I have an Acer that's getting the full 50Mbps. The router is N-rated, and when I plug in via ethernet, I get the full 50Mbps. There are two laptops, both running 14.04, and a smartphone on the WiFi network. Distance seems to have no affect. When the Dell is connected via WiFi, the Acer and the Android drop down to ~20Mbps

---

### Post by oldsmobile_mike on 2014-11-21
Your router is dropping down to the speed of the slowest device.  Upgrade that and try again.

---

### Post by pqwoerituytrueiwoq on 2014-11-21
yes, assuming you are not using a wireless G router or have other wireless G devices using a single band router
Keep in mind that most laptop vendors are skumbag steve and put bios locks on laptops making you pick from a list of approved wifi cards, based on the age of the laptop this can prevent you from even getting wireless N capabilities unless you use a usb port for wifi

i paid 4$ for the intel 2230 chip i put in my laptop

wireless N is very finiky with the distance, at a distance worth not having a wire i cant get my full 60Mbps, i can get better at close rance
i fould to get wifi at certain distances i had to make my router using wireless N 150 or i got 10Mbps or less

---

### Post by travissparks1307 on 2014-11-22
So I went ahead and ordered the Dell 1510 I linked to since it's compatible with my Latitude E6400, and it's a/g/n compatible. It should arrive in a couple days. I'll see if that does anything, and post the results.

---

