---
title: "Latitude D610 and ipw2200/wpa_supplicant problems"
date: 2006-01-09
forum: Hardware &amp; Laptops
---

### Post by Kensey on 2006-01-09
I have a Latitude D610 which Ubuntu works great on.  However, I still have some weirdness with the built-in ipw2200 miniPCI card, and getting wpa_supplicant and dhclient to play nice with it.

I. Basically, when I start up in my default home environment (WPA-PSK secure 802.11g access point, no wired network attached), I get a long wait at "Configuring network interfaces".  Eventually it times out and boot proceeds normally.  When it finishes booting, the ipw2200 driver has associated to the access point but there is no DHCP lease.  If I manually run dhclient a lease is immediately acquired.  The network configurator has DHCP selected as the configuration option for eth1 (my wireless interface), but it also has the last unsecured wireless network I connected to as the ESSID (i.e. it's totally unaware of anything wpa_supplicant is doing).  How do I make wpa_supplicant call dhclient when it associates successfully?  Or is there a batter way to do what I want (which is for the wireless to come up and get a DHCP lease automatically)?

II. In an effort to get the nifty "WiFi" LED to light up like it does in Windows, I tried putting a file "ipw2200" in /etc/modutils with the line:

options ipw2200 led=1 hwcrypto=0

a) This doesn't appear to have any effect.  The LED does not light up when I associate.  If I modprobe -r ipw2200 and then modprobe ipw2200 led=1 hwcrypto=0 the LED does light after a few seconds.

b) Moving the ipw2200 file to /etc/modprobe.d broke the wireless interface -- if I monitored iwconfig output every few seconds, I would see it associate with a key, then unassociate, associate with a different key, unassociate, etc. ad infinitum.  dmesg shows "firmware error -- restarting" messages from the ipw2200 driver.  Again, unloading ipw2200 and modprobing it with the options listed in the file made it work normally and with the LED lit.

c) What exactly does "hwcrypto=0" mean to the ipw2200 driver?  Don't I *want* hardware crypto enabled?  Does ipw2200 just not support it yet?  I've experimented with leaving "hwcrypto=0" off when modprobing the driver myself and it seems to work (although on one occasion it stopped working after a few minutes and I started getting firmware errors), but leaving it off in the ipw2200 file seems to be the kiss of death.

III. (this is more a purely wpa_supplicant issue) How do I make wpa_supplicant let me connect to arbitrary unsecured networks?  Currently when I go roaming around washington DC, which is rife with public Wi-Fi, I have to stop the wpa_supplicant daemon before I can connect to an unsecured network.  I don't want to just turn it off because then I have to *start* it every time I boot the laptop at home.  Is there a way to tell it to allow me to connect to networks even if it doesn't know about them?  Even a default setting (i.e., "assume that if I set the SSID myself that I want to connect to that network as an unsecured network") would be useful.  I just don't want to have to specify every random coffeeshop access point I ever connect to in wpa_supplicant.conf.

Some of this automatic module configuration makes me long for the days of "put it in /etc/modules.conf if you want it to load on startup" :)

---

