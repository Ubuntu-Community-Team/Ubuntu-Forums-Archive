---
title: "Hoary and Zaurus 5600 issues"
date: 2005-04-13
forum: Hardware &amp; Laptops
---

### Post by sethmahoney on 2005-04-13
I'm trying to get Hoary to sync with my Zaurus 5600 running OpenZaurus 3.5.3, and am having issues.  I followed the instructions here:

[http://www.openzaurus.org/web/index.php?option=com_content&task=view&id=29&Itemid=44](http://www.openzaurus.org/web/index.php?option=com_content&task=view&id=29&Itemid=44)

and now when I try to ping the Zaurus I get

ping: sendmsg: Operation not permitted

Any ideas?

---

### Post by sethmahoney on 2005-04-23
*bump*

---

### Post by sethmahoney on 2005-04-23
Actually, I got pinging working, but now I can't use multisync.  Something is obviously being blocked, but I can't think of what.

---

### Post by grakhul on 2005-05-22
I have a Zaurus sl5500 with the sl5600 sharp OS on it.  I am trying to get my ubuntu box to synch with it.  I have not really dedicated any effort to it, but I am about to.  I want to get my Ubuntu box to detect my Sharp without going over to another Zaurus OS such as Opie.  Any updates on your issue?  It seemed interesting and I wanted to know how you have been fairing.

---

### Post by sethmahoney on 2005-05-22
Well, going to OPIE or GPE or OpenZaurus or whatever doesn't really help the issue, it complicates it.  But I know that if you're running Firestarter it will block any sync or pinging attempts to the Z by default.  The only way I found to stop that is to shut down Firestarter (apparently there's some bug or something).  I got pinging working that way, but even then MultiSync doesn't work.  I haven't gotten past that part, unfortunately.

The link in my first post on this thread is OpenZaurus specific, but it might get you started syncing with the Sharp ROM.

---

### Post by grakhul on 2005-05-23
In my ubuntu box I added to /etc/network/interfaces:
[b]/etc/network/interfaces and add following lines:

mapping hotplug
script grep
map usb0

iface usb0 inet static
address 192.168.129.1
netmask 255.255.255.0
[/b]

I plugged my zaurus into my boxes USB port and went into the networking and under
"Advanced TCP over USB" I entered the address 192.168.129.1[b](though I
think that this is incorrect)[/b]

I commented out cdcether from /etc/directoryThatEscapesMeAtTheMoment

I performed a "upddate-modules" to bring everything up to date.

I performed an **lsusb** and could see that the zaurus was 
being detected by the hotplug usb port.  An **lspci**and
**lsmod**also indicated that my box detected a zaurus on the usb
interface.

I pinged the address and received sucessfull replies.


Now I want to know how to mount my zaurus since my box has a connection.
I have tried using "mount" I have checked the /dev directory and no luck 
as of yet.  I know I am missing something since the UBUNTU box does even list
the hotplugged device as a Sharp Zaurus 5*00.

---

### Post by grakhul on 2005-05-23
I also found this on the SuSe Linux page:

[b]
Zaurus connection:

    * Connect the cradle to the PC.
    * Switch on the Zaurus and place it in the cradle. 

The system should now detect the Zaurus automatically. Check it with the command
tail -f /var/log/messages. The output should be similar to:

Oct 9 13:53:12 tux kernel: usb 2-1: Product: SL-5500
Oct 9 13:53:12 tux kernel: usb 2-1: Manufacturer: Sharp
Oct 9 13:53:12 tux kernel: usb 2-1: SerialNumber: ************
Oct 9 13:53:12 tux kernel: usb0: register usbnet at usb-0000:00:10.1-1,Sharp Zaurus SL-5x00
Oct 9 13:53:12 tux /etc/hotplug/usb.agent[13134]: need a device for this command

Note that the network device usb0 is used in this case (line 4). The name of the device may be different in other circumstances.

Network configuration:

Start a console and log in as root user with the command su. Enter the following commands:

cd /etc/sysconfig/network
# (if the device displayed in /var/log/messages was not usb0 but a
# different device, use it instead of usb0 (e.g. ifcfg-usb1)
touch ifcfg-usb0
echo \# usb0 config for Zaurus > ifcfg-usb0
echo IPADDR=\'192.168.129.200\' >> ifcfg-usb0
echo NETMASK=\'255.255.255.0\' >> ifcfg-usb0
echo NETWORK=\'192.168.129.0\' >> ifcfg-usb0
echo BROADCAST=\'192.168.129.255\' >> ifcfg-usb0
echo STARTMODE=\'hotplug\' >> ifcfg-usb0
echo 192.168.129.201 zaurus >> /etc/hosts
[/b]


I will try a variation of it when I get home.


SIDE NOTE:
On the same page I discovered this:
[b]
Internet setup on the Zaurus:

Enter the following values in the Zaurus' network settings:

IP address: 192.168.129.201
Netmask:  255.255.255.0
Standard gateway: 192.168.129.200

If you are already connected to the Internet with your PC, ask for the name servers with the command cat /etc/resolv.conf and enter them in your Zaurus, too.

Sync with Qtopia Desktop:

Download the QTopia Desktop from the Trolltech page:

wget --passive-ftp
[ftp://ftp.trolltech.com/qtopia/desktop/SuSE8.2/qtopia-desktop-1.7.0-1su82.i386.rpm](ftp://ftp.trolltech.com/qtopia/desktop/SuSE8.2/qtopia-desktop-1.7.0-1su82.i386.rpm)

Note: This version also works with SUSE 9.1/9.2. The software rights for Qtopia Desktop are retained by Trolltech.

Install the package with:

rpm -Uhv qtopia-desktop-1.7.0-1su82.i386.rpm

After the installation, Qtopia Desktop will be available in the directory /opt/Qtopia/. You can create a link to Qtopia Desktop on KDE by clicking with the right mouse button on the desktop and selecting "Create new / Link to application". Enter e.g. Qtopia Desktop as name. Select the tab "Application" and enter /opt/Qtopia/bin/qtopiadesktop as command.

Many thanks to Jens Köke for this article!
[/b]

---

### Post by rioki on 2005-06-04
There ist to note that Sharp has alterd QTopia in such a way that the default QTopia Tools can't sysnc. They changed from FTP to Samba. I do not know if there have been fixes / patches for that out.
I have never got to sync my Zaurus 5600 with my Linux boxes. File transfer works fine; over Samba.

---

### Post by jasmuz on 2005-07-04
I do my file transfers via ssh ( i actaually installed the ssh server into my SL-5500 )  :) 

I just mount my Zaurus to my Gnome desk with  the Places menu -> Connect to server, just fill out my info and presto!  \\:D/

---

### Post by ericvmazzone on 2005-07-23
I can't get this dog gone thing working.  On either windows or Hoary.  I've followed ALL the guides I can find, and it will not do anything.  I can ping the Zaurus but that's it.  HELP PLEASE!!!   ;-)

---

### Post by invalid on 2005-08-10
I am going to bump this thread, due to the fact I am trying to work with the same issues.

After hours of playing, I managed to get Ubuntu to recognize the Zaurus (5600). I am now able to ping it. I can also access the webserver of the Ubuntu computer by going to 192.168.129.1 through Opera. I used this method to transfer files to it.

My concern now, it getting it to connect to remote addresses, outside of the local webserver. This page ([http://www.openzaurus.org/web/index.php?option=com_content&task=view&id=29&Itemid=44](http://www.openzaurus.org/web/index.php?option=com_content&task=view&id=29&Itemid=44)) says that in the Network settings of the Zaurus, there should be a usbd0 interface. However, all I see in the settings are a Wireless connection and a Lan connection that I attempted to get working. If I do 'ifconfig usbd0' in the terminal, I do indeed see that it exists.

Does anyone have any more suggestions as to what to do in order to get it to connect to the actual www?

Thanks,
Cb

---

### Post by jasmuz on 2005-08-10
If your Zaurus already is able to ping your PC and your PC ping your Zaurus, then you have an able Ethernet over USB connection. In order to mnake your Zaurus see the internet used by your PC, do the following:

sudo apt-get install guidedog dnsmasq 

Guidedog is a GUI for iptables wich easily will let you route & masquerade packets from and to the Zaurus.(WARNING: this program is KDE based)

Dnsmasq is a DNS resolver, for any machine that uses your PC as a gateway to the internet.

Properly configure those, and you will be well on your way to having internet on your Zaurus USB cradle.

---

### Post by invalid on 2005-08-10
Thanks for the quick reply.

I installed and configured Guidedog, this seems to be exactly what I need to get it working. However, even though it should, it still does not want to go outside the lan.

I can ping the host computer fine still, but it doesn't reach anywhere else:

bash-2.05$ ping -c 5 someIP
PING someIP (someIP): 56 data bytes
ping: sendto: Network is unreachable

Is there a setting somewhere I am missing? Did I forget to do something simple? I can attach my ifconfig output if it may help any.

Thanks,
Cb

---

### Post by invalid on 2005-08-13
Ok here is the deal:
Follow the directions in this thread up to this point. If you are where I am at now, here are the final steps to get the internet operating on the ethernet over usb connection.

```
edit /etc/resolv.conf and adapt to your config
nameserver YOUR-DNS
```( mine would be the linux box (192.168.129.1) )

```
edit /etc/hotplug/usbdnet.conf
```adapt to your needs, but ADD the GATEWAY line, and disable DHCPS and DHCPC```
IP=192.168.129.201
NETMASK=255.255.255.0
GATEWAY=192.168.129.1
DHCPS=no
DHCPC=no
```

```
edit /etc/hotplug/usbd.func
```
and put at the end of usbd_net_if_up() function this lines
```
# if DHCP client and serveur not set
# set the default route from $GATEWAY
if [ "$DHCPC" = "no" ] && [ "$DHCPS" = "no" ]; then
if [ ! -z "$GATEWAY" ]; then
/sbin/route add default gw $GATEWAY
fi
fi 
```

Open up Opera, with the terminal still open in the background
Go back to the terminal, and type (not as root, as your user)
```
qcop QPE/Network "up()" 
```

Go back to Opera, and surf away!

Hope this helps,
I probably won't be able to help with much more support, but if you don't get it working then post a reply, maybe someone can assist.

Cheers
Cb.

adapted from: [http://64.233.187.104/search?q=cache:lLFydlM0e34J:externe.net/zaurus/forum/viewtopic.php%3Ft%3D102+sl-5600+internet+ethernet+over+usb&hl=en](http://64.233.187.104/search?q=cache:lLFydlM0e34J:externe.net/zaurus/forum/viewtopic.php%3Ft%3D102+sl-5600+internet+ethernet+over+usb&hl=en)

---

