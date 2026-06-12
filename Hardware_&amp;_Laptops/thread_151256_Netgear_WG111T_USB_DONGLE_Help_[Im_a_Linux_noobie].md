---
title: "Netgear WG111T USB DONGLE Help [Im a Linux noobie]"
date: 2006-03-27
forum: Hardware &amp; Laptops
---

### Post by Kennyt on 2006-03-27
**BEGIN EDIT**
===================================================
Type: Help
Problem: Can't get WPA to work
Tried: wpasupplicant with ndiswrapper - Need help, unsuccessful
Wanting to try: madwifi - are they better than ndiswrapper? will it work with that dongle?
===================================================
**END EDIT**

I managed to successfully install gcc-3.4 which was needed to compile ndiswrapper1.10, followed by the installation of the ndiswrapper itself with 
the .inf drivers.

Ran sudo modprobe ndiswrapper, device went on, and could see it in Networking.
So far so good, got my internet up and working with that wireless dongle.

NOW.

1. I had to turn off WPA on my wireless router.
2. I don't know if ndiswrapper is good or madwifi is better?
3. I believe the WG111T has a atheros (think that's right spell) chipset or something?
4. I want to install wpasupplicant to work with ndiswrapper (Don't know how to, and I tried once but failed, because the guide was based on madwifi not ndiswrapper
and I tried to change ath0 to wlan0 and madwifi to ndiswrapper in the config but without result, can't connect with WPA..)

5. Help help plz.

---

### Post by colo on 2006-03-27
My Netgear 111-something boasts the prism2-chipset. You may want to try drivers from the linux-wlan-ng project.

---

### Post by Kennyt on 2006-03-27
been there...

[http://www.linux-wlan.org/docs/wlan_adapters.html.gz](http://www.linux-wlan.org/docs/wlan_adapters.html.gz)

doesn't seem to support my netgear wg111t usb dongle yet..

---

### Post by Kennyt on 2006-03-27
YAY!!!

After 1 day of trial and error I have finally get my WG111T USB dongle to work on Ubuntu, with WPA!

yay!

Steps I took:

1. Install gcc-3.4 (needed to compile ndiswrapper1.10
2. Install ndiswrapper1.10
3. Disable my WPA in my router so I can connect to the internet
4. Install wpasupplicant from the synaptic, I upgraded the kernel as well and others
5. Configure wpasupplicant
6. TADA!
7. Was that simple, don't know what I couldn't get it in the first place ](*,)

---

### Post by idiotseats on 2008-06-07
> **Kennyt said:**
> **BEGIN EDIT**
===================================================
Type: Help
Problem: Can't get WPA to work
Tried: wpasupplicant with ndiswrapper - Need help, unsuccessful
Wanting to try: madwifi - are they better than ndiswrapper? will it work with that dongle?
===================================================
**END EDIT**

I managed to successfully install gcc-3.4 which was needed to compile ndiswrapper1.10, followed by the installation of the ndiswrapper itself with 
the .inf drivers.

Ran sudo modprobe ndiswrapper, device went on, and could see it in Networking.
So far so good, got my internet up and working with that wireless dongle.

NOW.

1. I had to turn off WPA on my wireless router.
2. I don't know if ndiswrapper is good or madwifi is better?
3. I believe the WG111T has a atheros (think that's right spell) chipset or something?
4. I want to install wpasupplicant to work with ndiswrapper (Don't know how to, and I tried once but failed, because the guide was based on madwifi not ndiswrapper
and I tried to change ath0 to wlan0 and madwifi to ndiswrapper in the config but without result, can't connect with WPA..)

5. Help help plz.


 I know you need help well so do I, I know this Forum is old but I am a complete Linux newbie. I do not know how to install Ndiswrapper and  I could use a tip in installing it, I do not have the net on my dell with ubuntu and I need help please. I do not want to switch back to windows due to bad support. Right now I love Ubuntu except having no net on Ubuntu is like going out with no shoes please help  	:(

---

### Post by jblake on 2008-06-18
Hi idiotseats,
If ndiswrapper is not installed in your ubuntu distro, use the synaptic package manager to search for it then check the apply button to download and install. You will need to open konsole (Alt +F2 then type konsole to save searching). type 'ndiswrapper' without the quotes and you will see the options available. Whatever wireless card/dongle you have you will need to copy the .inf file from your windows driver cd to your desktop. To install at the  command prompt within console type 'sudo ndiswrapper -i /home/username/desktop/driver.inf to install the driver (you may need to unplug your dongle before this part and plug back in afterward - it may say device not found if not plugged in. Give it a whirl and see what happens - failing that look at the post above yours by kenny t who solved it.

---

