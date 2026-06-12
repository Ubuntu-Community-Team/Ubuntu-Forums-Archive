---
title: "HP LaserJet Professional P1102w"
date: 2010-05-10
forum: Hardware
---

### Post by ethana2 on 2010-05-10
I didn't realize HP licensed problematic IP for use in their printers, and I've never had any trouble with HP printers or scanners at all... so I went to Office Depot and bought an HP printer.

HPLIP doesn't support my printer now, they have no email or phone support for ubuntu, and their Windows email and phone support can't really tell me anything I don't know.

I bought a two year replacement plan for it, all I need to know is
Will HPLIP support my printer at some point in the near future, or
should I get rid of it?

Is there any way I can use it over WiFi if I can't use it over USB?

---

### Post by Chromos on 2010-05-12
Hi,

Ive got the same printer and I dont know when HPLIP will support it. 

I get it working with this driver. Check this out [http://foo2zjs.rkkda.com/]("http://foo2zjs.rkkda.com/")

---

### Post by yaaarrrgg on 2010-05-17
I just installed this open source driver and it works great!  :)

Afterwards, I looked at HP's site again.  They say the printer is fully supported, but requires hplip version 3.10.4+.  That's a newer release than what's in the ubuntu repo (currently only 3.10.2).  Maybe that is the problem.  I possibly should have installed directly from:

[http://sourceforge.net/projects/hplip/](http://sourceforge.net/projects/hplip/)

----
ETA: Out of curiosity, I tested both drivers, and the HP driver works fine too.  

If you want to use the proprietary driver/plugin from HP, just download the latest hplip from sourceforce, give it execute permissions, and run it in a terminal.  It will run a wizard to set up everything.  

Disadvantage: some parts of the HP driver are proprietary.  HP driver takes longer to install.
Advantage: you get full printer support (like toner levels) with HP driver.

---

### Post by muriwo on 2010-07-10
I am thinking of buying this printer, specifically so that I can use it over wireless.  I currently use 10.04.   Could one of the posters who have got it working with Ubuntu, clarify whether they mean "working over USB" or "working over a WLAN"?

---

### Post by yaaarrrgg on 2010-07-10
Well, mine is connected to a computer via usb, then shared on the network, so my laptop can access it wirelessly too.  I hadn't tried the direct wireless mode yet.  Though, it would surprise me if if didn't work.  HP's driver support for linux is top-notch.

Actually, now that I think about it, I noticed that it didn't come with a USB cable and ordered it separately.  That was one common complaint with it.  Though it was probably a waste of money on my part to order the cable too ... I wasn't even thinking about using the direct wireless mode.  :)

---

### Post by muriwo on 2010-07-10
Thanks [yaaarrrgg]("http://ubuntuforums.org/member.php?u=49794") but in my house all the PCs are linux laptops, which are not always present at the same time, so I definitely need it to work via direct wireless access, not printer sharing.

---

### Post by yaaarrrgg on 2010-07-10
Hmm, I just checked the hplip page, and it doesn't indicate wifi support:

[http://hplipopensource.com/hplip-web/models/laserjet/hp_laserjet_professional_p1102w.html](http://hplipopensource.com/hplip-web/models/laserjet/hp_laserjet_professional_p1102w.html)

I didn't see an obvious way to set it up for wifi on mine either.  So it doesn't look likely.

---

### Post by ArgentSilver on 2010-07-24
> **yaaarrrgg said:**
> Hmm, I just checked the hplip page, and it doesn't indicate wifi support:

[http://hplipopensource.com/hplip-web/models/laserjet/hp_laserjet_professional_p1102w.html](http://hplipopensource.com/hplip-web/models/laserjet/hp_laserjet_professional_p1102w.html)

I didn't see an obvious way to set it up for wifi on mine either.  So it doesn't look likely.

FYI, the hplip driver works fine for wi-fi. Just go to hplip.net, click the button to download HPLIP, tell it which distro & version you have, download the appropriate file and follow the instructions to run/compile. It will then download the necessary PPD and filter files and automatically find the printer on your network.

I have my p1102w running via wi-fi just fine with PC's and laptops on Ubuntu 9.04 & 10.04, & Mint 8.

---

### Post by yaaarrrgg on 2010-07-24
Does that require an open wi-fi access point?  My wireless router is set up with WPA, and I didn't see a way to configure this in the printer.

---

### Post by muriwo on 2010-07-25
> **ArgentSilver said:**
> FYI, the hplip driver works fine for wi-fi. Just go to hplip.net, click the button to download HPLIP, tell it which distro & version you have, download the appropriate file and follow the instructions to run/compile. It will then download the necessary PPD and filter files and automatically find the printer on your network.

I have my p1102w running via wi-fi just fine with PC's and laptops on Ubuntu 9.04 & 10.04, & Mint 8.
Thanks [ArgentSilver]("http://ubuntuforums.org/member.php?u=171337"), that's just what I wanted to know. I will be buying the printer and will report here my experiences.    My WLAN is WPA2 so I'd also be interested to know the answer to yaaarrrgg's question above.     Perhaps you need to de-protect the WLAN just long enough to do the initial printer configuration, is that it?  Otherwise I see no way it could find out the WPA2 pre-shared key.   Or can you do this by first connecting to the printer via USB?

---

### Post by ArgentSilver on 2010-07-25
> **muriwo said:**
> Thanks [ArgentSilver]("http://ubuntuforums.org/member.php?u=171337"), that's just what I wanted to know. I will be buying the printer and will report here my experiences.    My WLAN is WPA2 so I'd also be interested to know the answer to yaaarrrgg's question above.     Perhaps you need to de-protect the WLAN just long enough to do the initial printer configuration, is that it?  Otherwise I see no way it could find out the WPA2 pre-shared key.   Or can you do this by first connecting to the printer via USB?

As I remember, the procedure for installing with hplip has one option to connect first with USB. And I believe there is a wireless configuration option during that process so you can tell it your WPA key via the USB connection. This is probably easiest, but I didn't do that!

I just took off my WPA key long enough for the printer to connect to my access point. Then I printed a configuration page (Hold the cancel key until the ready light flashes, then release). With the IP address on the config page, you can connect your web browser to the printers embedded web server at [http://ip_address](http://ip_address). Once there, you can go to the Network-> Wireless page and configure the WPA password, then re-enable WPA on your WAP. Once the printer is on your LAN you're good to go! Just install drivers on any computers on the LAN.

---

### Post by lex.online on 2010-08-10
Hi,
Ubuntu 10.04 here, I've just bought this printer and have some problems...
I'd like to use the wireless connection.

First I tried the foo2zjs driver with no luck: the printer is now recognized but I can't figure out how to set up the wifi connection.

So I installed the last version of hplip from [http://hplipopensource.com](http://hplipopensource.com), during the setup process I chose the automatic configuration. At the end, hp-setup gui starts but here come the problems: when I have to choose the connection type, after I select "wireless" (which requires a temporary usb connection), the printer is NOT in the list of "Discovered Wireless Capable Devices"...
I solved it by editing /usr/share/hplip/data/models setting "wifi-config=1" (default is 0) under [hp_laserjet_professional_p1102].

Now the printer is in the list, but when i select it, I get the message "An I/O error occured. Please chech the USB connection to your printer and try again. (Device I/O error)"

...Any ideas? ](*,)
Thanks in advance

(I apologize for any errors, I'm italian:-s)

---

### Post by ArgentSilver on 2010-08-11
> **lex.online said:**
> Hi,
Ubuntu 10.04 here, I've just bought this printer and have some problems...
I'd like to use the wireless connection.

First I tried the foo2zjs driver with no luck: the printer is now recognized but I can't figure out how to set up the wifi connection.

So I installed the last version of hplip from [http://hplipopensource.com](http://hplipopensource.com), during the setup process I chose the automatic configuration. At the end, hp-setup gui starts but here come the problems: when I have to choose the connection type, after I select "wireless" (which requires a temporary usb connection), the printer is NOT in the list of "Discovered Wireless Capable Devices"...
I solved it by editing /usr/share/hplip/data/models setting "wifi-config=1" (default is 0) under [hp_laserjet_professional_p1102].

Now the printer is in the list, but when i select it, I get the message "An I/O error occured. Please chech the USB connection to your printer and try again. (Device I/O error)"

...Any ideas? ](*,)
Thanks in advance

(I apologize for any errors, I'm italian:-s)

First of all, is the printer already wirelessly connected to your wireless access point? If so, you should be able to use a different HPLIP option that just says to connect via network (i.e. NOT wireless with a temporary USB connection). The software can find the printer on your LAN.

---

### Post by lex.online on 2010-08-12
Thanks ArgentSilver.
The printer is already wirelessly connected to my router (I had to install the printer on a windows machine to get it).
But when I select the "Network/Ethernet/Wireless network (direct connection or JetDirect)" connection type as you said, no device is found...
I wonder if I have an udp/tcp port used by the software blocked by my router settings.
I searched the web about this but I haven't found anything.

---

### Post by yaaarrrgg on 2010-08-12
On mine, I had to set up printer sharing (on the client end) to see it in the list of available printers.  Though mine is set up a little differently.

For example:
[http://blog.mypapit.net/2008/05/enable-printer-sharing-with-ubuntu-computers.html](http://blog.mypapit.net/2008/05/enable-printer-sharing-with-ubuntu-computers.html)

---

### Post by lex.online on 2010-08-12
Thanks yaaarrrgg, it works!!
I had to activate the option "Show printers shared by others systems" in the cups configuration page ([http://localhost:631/admin](http://localhost:631/admin))...

Thanks again guys :D

---

### Post by muriwo on 2010-10-08
ArgentSilver, I have now bought the printer but am getting nowhere fast (or slowly!).  I'd appreciate more detail about exactly how you got it to connect to your wlan in message #11.  I have disabled MAC Address filtering and other security on my WLAN router.     However the router's DHCP table is not showing any new devices getting allocated IP addresses.

The printer just continually flashes a fault sign.

Trying hplip via USB or either of the WLAN options also doesn't work... it installs everything including the HP Plugin and then the actual printer... but when it tries to print it claims a comms failure.

---

### Post by muriwo on 2010-10-08
Success!  What a palaver though...

1. The "printer not booting" problem was actually caused by something really stupid.  When I remove the safety tabs and stickers, one of them tore off from a plastic protective frame in the toner bay.  It looked so solid that I was sure it had to be a permanent fixture - despite being orange!  Eventually I read through the guide again and decided I had to take it out - as soon as I did this, the printer booted normally and hp-setup (from hplip-3.10.9, installed by download from sourceforge) connected to it via USB perfectly.

2. Then I tried to use hp-setup via USB to set it up to access my wlan.   Initially it didn't appear but after using a variant of lex.online's tip ( on my system it is  /usr/share/hplip/data/models/models.dat) it did appear.  However I then ran into exactly the same error message  "An I/O error occured. Please chech the USB connection to your printer and try again. (Device I/O error)".  So no joy.

3. Next I tried ArgentSilver's idea of disabling all protection on my wlan just long enough to get the printer initially connected.  That didn't work, as despite the blue wifi light flashing furiously when I pressed the wifi button, it didn't pick up my wlan, and my wireless AP did not show any new DHCP client.

4. Finally I tried directly connecting to it via ad-hoc wireless network.  No joy, either via hp-setup or via selecting the HPEE84ED wlan which mysteriously appeared in my NetworkManager wlan list.  Curiously, while my NetworkManager was unsuccessfully attempting to connect to this ad-hoc wlan, the wifi light on the printer lit up to a steady blue. 

5. There I tried deactivating "Connect Automatically" on all my other wlan configs in NetworkManager, and setting the "IPV4 addressing" option to "link-local" for the HPEE84ED connection.  This allowed my NetworkManager to actually establish the wlan connection.  Although from the first try I got allocated an address on the same subnet as the printer (according to its status page) I had to disconnect and reconnect several times until I could ping the printer's address.

6. Once I could ping it, it was easy to connect to the web-admin page of the printer and progressively re-secure my wlan.  Once during this the printer kind of "went to sleep" and I had to press the wifi button to get it to reconnect to the wlan.  Note that earlier on I had done lex.online's option of "Show printers shared by others systems" in the cups configuration page ([http://localhost:631/admin](http://localhost:631/admin))", so that may be relevant.

7. Finally I ran hp-setup again and selected the "Network/Ethernet/Wireless Network" option.  This time it worked perfickly!   Now I just have to go and apologise to my wife for dingying her for the last 4hrs to fanny about with this printer....

---

### Post by LukasF on 2010-11-26
> **ArgentSilver said:**
> FYI, the hplip driver works fine for wi-fi. Just go to hplip.net, click the button to download HPLIP, tell it which distro & version you have, download the appropriate file and follow the instructions to run/compile. It will then download the necessary PPD and filter files and automatically find the printer on your network.

I have my p1102w running via wi-fi just fine with PC's and laptops on Ubuntu 9.04 & 10.04, & Mint 8.

You are right ArgentSilver, it works perfectly!

I was really disappointed when found that hplip included in Ubuntu 10.04 doesn't work out of the box (and also found on the driver support page that it p1102w has not network/wireless support on Linux), but when found your post I tried and it works now perfectly.

---

### Post by dolphinsonar on 2011-01-03
> **Chromos said:**
> Hi,

Ive got the same printer and I dont know when HPLIP will support it. 

I get it working with this driver. Check this out [http://foo2zjs.rkkda.com/](http://foo2zjs.rkkda.com/)

Thanks, I have this printer and using your link worked great!

---

### Post by yaaarrrgg on 2011-01-21
I finally got around to setting a wireless connection rather than over USB, since I just got a new wireless router.  :)  Here are the steps I used to set up WPA (AES):

Press the wireless button on the printer and you should get a blinking blue light.

Push the x down and to print off a test page from the printer that shows all the default network configuration.  The default gateway is the location of the printer, which for me was 169.254.156.163.  It will also show an SSID.

By default the printer is set up as an ad hoc network, and you can connect directly to the printer at the wireless SSID HPEEE9F1.  It's open, no encryption.  After connecting to printer's access point, you should be able to view the printer admin pages at a url like:

    [http://PRINTER_DEFAULT_GATEWAY](http://PRINTER_DEFAULT_GATEWAY)

Then under Networking -> Wireless changes settings to:

    Infrastructure
    Change SSID to your wireless router
    Set security mode and passphrase

The wi-fi light should be solid blue now, and it will kick you off the access point HPEEE9F1.  Push the x down and printed off a test page again, if you want the new IP address of the printer.  

Now, for a standard internet connection, connect again to your wireless router.  You won't be able to connect to the internet via the printer.

Then I installed hplip (latest version from hp) and ran hp-setup

Select "network printer" (second option), not the wireless option, and you should see it in the list.

----

One other thing I noticed is that Bonjour (device discovery) is enabled by default, so if the printer's on the network you can access the printer's admin page directly at:

[http://npieee9f1.local./](http://npieee9f1.local./)

---

### Post by hubiedo on 2011-01-29
i was having all kinds of trouble with this printer install. i tried the generic drivers and it was a no go. i went to sourceforge and downloaded the newest hplip drivers as suggested above and it works great. thanks to all of you for the help and informations. i will try to return the favor sometime by posting my solutions to problems etc.

---

### Post by pgmer6809 on 2011-02-26
> **yaaarrrgg said:**
> Does that require an open wi-fi access point?  My wireless router is set up with WPA, and I didn't see a way to configure this in the printer.

I connected mine to a WinXP machine with the USB cable that came with it. I then followed the XP install process.
During that process I gave the printer the ssid and WEP/WPA keys for my wireless network.

I then disconnected the printer USB cable from the windows machine.

I then tried the built in Ubuntu (Lynx) method of setting up this printer. It could connect to the printer, and see it on the network, but it could not print a test page.

I downloaded the HPLIP from sourceforge, and followed instructions.
I chose 802.11/wireless as the connection method during setup.
I can now print test pages to the printer.

However my linux box is a desktop and not using wifi. it is a wired connection to a router with wifi and 802.11 ports. So the connection is 802.11 to the router, then wireless wifi from the router to the printer.  That works. At least for test pages.

If I can get my laptop to go direct wifi - wifi i will let the group know. (Have to install hplip on the laptop first.)

pgmer6809

PS -- OK it works wireless to wireless. Laptop to printer with no wires connected to either machine. test pages and openOffice writer.
pgmer6809

---

### Post by CDrewing on 2011-04-06
Well, there is a problem. But at first, thank you **yaaarrrgg** for this really good tutorial!

So I used a W32 netbook to connect wirelessly to the printer at first, because Ubuntu didn't want to do that with an unsecured connection. I registered the printer in my local wireless network. Everything was fine.

Now to the problem: When I try to register the printer (as "network connection" printer as described) hplip wants to download some driver stuff from HP, but it fails:

[IMG]http://img805.imageshack.us/img805/2723/bildschirmfoto1f.png[/IMG]

On hplipopensource I felt lost a little bit. So how can I install these binary additional files? hplip also offered me to use a local copy of the file(s) needed - so if anybody has it right now, don't be shy :P

Thanks a lot, seems to be a great printer. Does anyone want to have my old HP Laserjet 4P?

Rgds,
Christian



P.S.: Just found out that you can install this printer right through the system configuration menu, that's most easy. But it would be still nice to know how to solve the problem above.

---

### Post by yaaarrrgg on 2011-04-06
My instructions were not totally clear on a point... you can't access the internet while connected directly to the printer.  You'll need to connect back to your wireless router, to pull down the hplip binary driver.

Thank you for the feedback.  I updated my instructions. :)

---

### Post by CDrewing on 2011-04-07
Well, of course I am not trying to download the driver while being directly connected with the printer :lolflag:

I receive this dialogue box when the printer is already installed and connected with my local network. So internet access wouldn't be a problem.

I ran the gui command in the shell but see yourself:

[SIZE="3"]1: [/SIZE][[IMG]http://img508.imageshack.us/img508/3899/bildschirmfoto2j.th.png[/IMG]](http://img508.imageshack.us/i/bildschirmfoto2j.png/) [SIZE="3"]2: [/SIZE][[IMG]http://img854.imageshack.us/img854/1558/bildschirmfoto3.th.png[/IMG]](http://img854.imageshack.us/i/bildschirmfoto3.png/)

[SIZE="3"]3: [/SIZE][[IMG]http://img109.imageshack.us/img109/7403/bildschirmfoto4.th.png[/IMG]](http://img109.imageshack.us/i/bildschirmfoto4.png/) [SIZE="3"]4: [/SIZE][[IMG]http://img848.imageshack.us/img848/9476/bildschirmfoto6.th.png[/IMG]](http://img848.imageshack.us/i/bildschirmfoto6.png/)

[SIZE="3"]5: [/SIZE][[IMG]http://img716.imageshack.us/img716/3973/bildschirmfoto7c.th.png[/IMG]](http://img716.imageshack.us/i/bildschirmfoto7c.png/)

And this is my shell:

```
cdrewing@cdrewing-desktop:~$ sh -c 'STARTED_FROM_MENU=yes /usr/bin/hp-toolbox'

HP Linux Imaging and Printing System (ver. 3.10.6)
HP Device Manager ver. 15.0

Copyright (c) 2001-9 Hewlett-Packard Development Company, LP
This software comes with ABSOLUTELY NO WARRANTY.
This is free software, and you are welcome to distribute it
under certain conditions. See COPYING file for more details.


HP Linux Imaging and Printing System (ver. 3.10.6)
System Tray Status Service ver. 2.0

Copyright (c) 2001-9 Hewlett-Packard Development Company, LP
This software comes with ABSOLUTELY NO WARRANTY.
This is free software, and you are welcome to distribute it
under certain conditions. See COPYING file for more details.

/usr/lib/pymodules/python2.6/gtk-2.0/gtk/__init__.py:127: RuntimeWarning: PyOS_InputHook is not available for interactive use of PyGTK
  set_interactive(1)
ERROR:dbus.proxies:Introspect error on :1.396:/: dbus.exceptions.DBusException: org.freedesktop.DBus.Error.NoReply: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.
cdrewing@cdrewing-desktop:~$ 

```

Perhaps this can give you a hint where the problem is.

Doesn't anybody else have the same problem with hplip?

---

### Post by yaaarrrgg on 2011-04-07
> **CDrewing said:**
> Well, of course I am not trying to download the driver while being directly connected with the printer :lolflag:
...

Perhaps this can give you a hint where the problem is.

Doesn't anybody else have the same problem with hplip?

Hmm, it doesn't look like anything is wrong on your end then.  It *should* just download from the internet.  It just worked automatically when I ran it.  If your local internet connection is good, I would think a few things might be the problem:

1. hp is having a network issue and not providing the binary drivers.  this could be on hp's end.

2. try dropping to a older/newer version of hplip. maybe there is a bug in the version of hplip.

3. are you running any custom firewall/proxy configurations?  If you can peek at the driver url it's trying to hit (maybe with wireshark or router logs) I wonder if you can ping the address or pull it down via a web browser.  Or if something along the connection is blocking it.

---

### Post by Strandvasker on 2011-04-15
I got it to work.

First I visited [http://sourceforge.net/projects/hplip/](http://sourceforge.net/projects/hplip/) and downloaded hplip-3.11.3a.run to my home folder.

After looking a bit at the .run file, not sure what to do with it, I went to [http://hplipopensource.com/hplip-web/install_wizard/index.html](http://hplipopensource.com/hplip-web/install_wizard/index.html) and entered my version and all that stuff it asks for. I'm not sure, it might have downloaded hplip-3.11.3a.run once more, making my first download pointless. 

Once done with the download I followed the instructions, opened up a terminal, wrote sh hplip-3.11.3a.run and picked the automatic install. It spent 8-10 minutes installing and when I was asked if I wanted a restart or re-plugin I picked ignore as my printer is wireless. When the graphic UI popped up I picked Network/Ethernet/Wireless and basically rolled with the punches.

It asked me if I wanted to install some hp manager thingy too and I said yes.

It works like a charm, default install, nice and easy and now I'm printing over wifi.

---

### Post by ReckmanR on 2011-04-15
I had the same error with the binary plugin. After googling for 45 minutes, I figured it out.

1.) First Install hplip
2.) In terminal "Sudo hp-plugin"
3.) Follow instructions for the plugin
4.) "Sudo hp-setup" option 2 for direct wireless connection

---

### Post by lazki on 2011-05-12
> **ReckmanR said:**
> I had the same error with the binary plugin. After googling for 45 minutes, I figured it out.

1.) First Install hplip
2.) In terminal "Sudo hp-plugin"
3.) Follow instructions for the plugin
4.) "Sudo hp-setup" option 2 for direct wireless connection



Great!!!

It works flawlessly on Kubuntu 11.04.

---

### Post by Kate the Enthusiast on 2011-06-25
> **lazki said:**
> Great!!!

It works flawlessly on Kubuntu 11.04.

Yes, also used a win computer first to get an ip for the printer.
Then installed driver from hp official web page. Then >hp-setup and
have chosen the second option. 

Works (with wireless) great on an HP mini netbook and lenovo tablet, both ubuntu 11.04.

---

### Post by wojto on 2011-08-05
Hi,

I came up with a sort of tutorial to configure the HP  Laserjet p1102w wireless(wifi) printer, connected with USB cable, as  well over wifi. I am currently usig Ubuntu 11.04, but it shoud work  under older distributions too.

**Connecting over USB**

Is  no big deal. Just plug and the system should configure it  automatically. If not install the newest version of HPLIP```
sudo  apt-get install hplip hplip-gui
``` and then siply add a new printer  from MENU System > Administration > Printing or with Terminal  ```
sudo hp-setup -i 
```

**Connecting over wifi = wirelessly**

Wireless  printing uder ubuntu is a little tricky. The manufacter mostly supports  it for Windows, on the installation CD, but it can work on the Linux  the same way. Most of the job is to configure the ad-hoc connection.  Turn on your printer and on  and make a sweep for wireless networks. You  shoud find something like HP432CBA. Try to connect to it, but if will  probably fail. 

Therefore you have to edit this network : Edit  connections > Wireless > [choose the network], click Edit and  select the IPv4 Settings. Set Method to =Shared to other computers=,  Save and try to connect again. It should work now.

Now press the  button (x) on your printer for few seconds and wait until it prints the  configuration page. Remember the printer cant be in sleep mode, use (I)  to wake it. On this configuration page find the IPv4 address. Open your  browsver and put the address in there. You should see the printers  server page. If yes, it is almost done. 

Now we can add the  printer. At first install hplip-gui, if isnt installed on your machine.  ```
sudo apt-get install hplip-gui 
``` Then open System >  Administration > Printing, click to add a new printer, select =Find  network printer=, enter the IPv4 address into the Host column. It would  find Jetdirect, click foward, choose or download a proper driver and  print a test page.

Hope that it helped.

---

### Post by HandeH on 2011-08-08
The plugin (hplip-3.11.7-plugin.run) fails to install in Lucid Lynx 10.04. Also hp-wificonfig fails, so WiFi-connection cannot be established. Error logs: 

[https://bugs.launchpad.net/hplip/+bug/687404/+attachment/2261710/+files/hp-PLUGIN-fails-to-install.txt](https://bugs.launchpad.net/hplip/+bug/687404/+attachment/2261710/+files/hp-PLUGIN-fails-to-install.txt)

---

### Post by HandeH on 2011-08-10
The plugin can be installed if you change your locale to English, reboot/re-login and try again. But the hp-wificonfig still fails. 

So currently wireless printing is not possible in Lucid Lynx. There is  a [bug report]("https://bugs.launchpad.net/hplip/+bug/687404") currently in progress:

---

### Post by utnubuuser on 2011-09-19
I had issues with this printer too, and the solution was this:

install the foo2zjs driver from the link on page 1 of the thread, follow the instructions as far as you can, and if you get stuck at the proprietary-plugin stage 
open firefox and navigate to [http://localhost:631](http://localhost:631) which is your cups interface
then choose printers in the menu bar, then add new printer - your printer needs to be connected at this point - then select the printer from the list and in the driver-plugin option at the bottom, select browse, and find the plugin in @ $ /usr/share/ppd/foo2zjs/HP-LaserJet_Pro_P1102.ppd.gz
and that should take care of it.
The reason I'm posting this is that no matter which of the above suggestions I followed, I couldn't get any of the scripts to accept or even find the correct plugin

so again, here is where you'll find it: $ /usr/share/ppd/foo2zjs/HP-LaserJet_Pro_P1102.ppd.gz

thanks to the $ locate command

---

### Post by epicbattle on 2012-01-20
Ubuntu 11.04

Alright, I have everything downloaded. I am so close! I am at the part under HP Device Manager where it wants me to "Select from discovered devices" . The p1102w won't show up! 

I can get wireless to work on windows 7.I've tried it with the printer connected via USB. It will print. Just not with the wireless yet.I've done the System/Admin/Printer check stuff. 
To the best of my knowledge I have downloaded everything I need to download. 

Any idea what I may have missed to get this to work? 

Thanks for your help in advance.

---

### Post by berninghausen on 2012-07-29
You can hunt and hunt for a Linux solution, but it's a simple Windows/HP screwup.  There are two small programs in the Rom of the printer, Smart Install 32 and 64.  Run the setup disk/software and look for a configuration link to sinstall32.exe or sinstall64.exe.  You have to do this in windows, although it might be possible in Wine.

Anyway, these little programs make the printer look like a CD drive to all the Linux print stuff.  Running the appropriate configuration to DISable them is what works.  Silly me, I ran them, rebooted to Hybryde Ubuntu, and it still wouldn't see the printer.  Several days later I thought to powercycle the printer.  Duh, Hybryde Ubuntu immediately notice, registered, and set up the printer.

Now I should see if the dang thing still runs under Windows...

Good luck, all!

---

### Post by dooper on 2012-08-01
I also have this printer and struggle to make it work reliably under Ubuntu. I have had it working numerous times wirelessly and then it just loses its allocated ip address and thats it,,game over.

I have just logged on to my router and there is now no allocated ip address for the printer.

The other evening i had to print some DL envelopes and gave up with Ubuntu in the end as there was no way i could sort out the correct alignment.

I flipped over to Vista 7 and everything worked beautifully.

---

