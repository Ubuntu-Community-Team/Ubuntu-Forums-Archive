---
title: "Beetel 100 CX Usb Adsl Modem"
date: 2011-01-09
forum: Hardware
---

### Post by upsla on 2011-01-09
Hello everyone.
I am newbie to Linux. I am using Maverick Meerkat 10.10.
I am using Beetel 100 CX USB ADSL Modem for internet connectivity in windows.
My problem is i cannot connect to internet using the same modem in Ubuntu.
I managed to get modem detected by Ubuntu.It is now listed in "lsusb" command.
The modem in on steadily.
I tried to connect to internet using pppd call conexant and pon etc, nothing worked.
So help me folks. :D

---

### Post by translator125 on 2011-01-09
Hi upsla,

At the outset, my hearty congratulations to you on getting the usb adsl modem detected by Ubuntu :)

Now, to connect to the Internet, follow these steps:

1. Go to Applications --> Ubuntu Software Center and type 'br2684ctl' in the search field. Install the utility.

2. Open a terminal by going to Applications --> Accessories --> Terminal and type (or copy-paste from here): 
sudo br2684ctl -c 0 -a 1.32
(For your information, 1 and 32 are the VPI and VCI values respectively. You may need to use different values, depending on your WAN configuration settings.)

3. Open another terminal and type:
sudo ifconfig nas0 192.168.1.1 netmask 255.255.255.0
(192.168.1.1 is the IP address and 255.255.255.0 is the (sub)netmask under your LAN configuration settings. Please feel free to use different values, depending on your LAN configuration settings.)

You will be prompted with several Yes/No options one after the other. Select 'Yes' each time.

In the same terminal, type:

sudo pppoeconf

Enter your user ID and password, when prompted.

4. Open your browser and voilà! You're connected to the Internet.

5. You may close both the terminals now, though a process may still be running in the first terminal.

Note: You will have to follow the same procedure each time you restart your system.

All the best!

- translator125

---

### Post by upsla on 2011-01-10
Hi [translator125 ]("http://ubuntuforums.org/member.php?u=1220975")
I tried your method. But when i type [FONT=&quot]sudo pppoeconf it says detecting eth0 devices and then nas0 devices , then the progress bar is stuck at 100 % . I[/FONT][FONT=&quot]t does not progress further. Help me.:confused: [/FONT]I am attaching the screen grab of the problem, i thought it might help you in better understanding it.[IMG]http://imagebin.org/131949[/IMG]

---

### Post by upsla on 2011-01-10
[IMG]http://imagebin.org/131949[/IMG]

---

### Post by upsla on 2011-01-10
Hi Translator
I am posting this image that describes about my problem.:confused:

---

### Post by translator125 on 2011-01-10
Hi upsla,
Thanks for the image. As far as I can see, the nas0 interface was successfully created, but incorrectly configured. You may want to confirm the IP address in your WAN configuration settings and the (sub)netmask details from your ISP. They may be different from the ones I've suggested in my reply, i.e., they need not be "...192.168.1.1 netmask 255.255.255.0".
Confirm the settings and try again.
Good luck this time, upsla :)
- translator125

---

### Post by translator125 on 2011-01-10
Hi again:
Just in case you're not sure of your WAN/LAN configuration settings, call up your ISP and ask.
- translator125

---

### Post by upsla on 2011-01-11
Hi its me again.
See i don't want to contact the isp.They take time to solve problem and i need to unnecessary questions.
So kindly provide me with another solution.

---

### Post by upsla on 2011-01-12
hi i contacted isp . they can't figure it out.

---

### Post by upsla on 2011-01-18
Hi translator here are the screens. see this and tell me something.

---

### Post by translator125 on 2011-01-18
Hi upsla:
Your ISP doesn't need to figure out anything. They just have to provide you the LAN/WAN configuration settings. That's all.
- translator125

---

### Post by translator125 on 2011-01-18
Hi upsla:
Thanks for the screenshots. Btw, what do you see when you click on the 'General' and 'Line setup' tabs in the third screenshot?
- translator125

---

### Post by upsla on 2011-01-18
Hi as i said this screen shots are taken from windows. the dialer is used in windows when connecting to internet. Finally. regarding your question , when i click on the general tab ,a dialog appears as shown on the screen shot one.

---

### Post by translator125 on 2011-01-18
Hello upsla,
Please take a look at the uploaded image. You should be able to see a similar TCP/IP settings page somehwhere in Windows, either in Network Connections or perhaps in the settings/properties of Internet Explorer. Unfortunately I don't have Windows, else I would've guided you step by step, but I'm sure you can find your way.
In the image uploaded by me the default gateway is 192.168.1.1. See what the default gateway is in your case and configure the nas0 interface accordingly.

In case that doesn't work, try this:
Go to [http://shortify.com/XEB](http://shortify.com/XEB) and look at the list of default IP addresses in the table. You'll have to try these one by one, which can be very tedious.

Once again, I'm most surprised that your ISP is not willing to give you the LAN/WAN configuration settings.
Anyway...

- translator125

---

### Post by upsla on 2011-01-19
> In case that doesn't work, try this:
Go to [http://shortify.com/XEB](http://shortify.com/XEB) and look at the list of default IP addresses in the table. You'll have to try these one by one, which can be very tedious.
Hi the link that you sent me gives default ip for configuring routers and modems. If you look closely at table under conexant the ip field is mentioned as n/a.

Regarding the screen shot that you sent me. I checked my settings and the obtain ip addresses automatically option is selected by default. I even unchecked it i the hope of finding the defaullt gateway, bu all i found was empty field. So kindly help me.

---

### Post by translator125 on 2011-01-19
Dear upsla,

Yes, I did send you the default gateway and IP settings for several modems and routers in the hope that one of these may fit in your case. It doesn't matter that there is nothing mentioned under the Conexant field.

Am so sorry you have to go through all this, upsla. All you need is the setting(s) used by your ISP and I feel bad you've not been able to get them so far. Do try again, I'd suggest. Tell your ISP that you don't want them to configure your modem in Linux and that you're doing it yourself. All you need is the default gateway / IP address and the (sub)netmask settings.

Good luck. Am sure you need lots of it :)

- translator125.

---

### Post by przemo_li on 2011-01-25
Hi

pppoe will NOT work for You

It is used IF (and only if) your device is conneted by ETHERNET cable (to your network card). But it is not! It is connected by USB right?

pppd is right path.

Do this:

check if kernel have loaded:
pppoatm    ("lsmod | grep pppoatm"  <- will display pppoatm if is loaded, if not load it manually "insmod pppoatm")

edit this file (but use your provider login !!)
# /etc/ppp/peers/internet:

user "LOGIN@yourprovider"
plugin pppoatm.so 0.35    <- this may be invalid for your modem so if it do not work google for it
usepeerdns
defaultroute
persist
noauth

edit
# /etc/ppp/chap-secrets:
"LOGIN@ISP_config" * "password"

then
cp -v /etc/ppp/chap-secrets /etc/ppp/pap-secrets


to activate your connection run:
pppd call internet

ping google.pl

if ping do not work try:
cp /etc/ppp/resolv.conf /etc/

---

### Post by upsla on 2011-01-26
unfortunately it did not work.

---

