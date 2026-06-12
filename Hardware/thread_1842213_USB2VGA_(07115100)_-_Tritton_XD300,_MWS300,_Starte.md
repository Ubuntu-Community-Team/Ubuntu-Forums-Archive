---
title: "USB2VGA (0711:5100) - Tritton XD300, MWS300, Startech ..."
date: 2011-09-10
forum: Hardware
---

### Post by ironstorm on 2011-09-10
**[COLOR="SeaGreen"]2011-09-13 Update: I can confirm that video on the Tritton XD300 (0711:500 - Trigger 1+) functional w/ the drivers and configuration on MaX 6.5RC2 w/ max-multiseat package installed.    To make it work I had to use a USB to PS2 splitter in the USB port next to the sound input and output.[/COLOR]**

I bought an XD300 and I'd like to get it working with something other then Windows.   The key element that doesn't work out-of-the-box with Ubuntu is the USB2VGA video adapter.

**[SIZE="3"]The Hardware - MCT 0711:5100 Trigger 1+ chipset[/SIZE]**

That device is (see ***lsusb*** output):
> ID 0711:5100 Magic Control Technology Corp.
This chipset is also known as the MCT ***Trigger 1+***

The device is also used by a few other OEMs in a few other devices...  
[LIST]
[*] From MadCatz/Tritton as the [XD300]("http://www.trittonusa.com/index.php/products/usb_video_technology/xpress-dock/")
[*] Directly from MCT in the [UVAL-D8205]("http://www.mct-us.com/products/product_d8205.html") (generic XD300) and [MWS300]("http://www.mct-us.com/MWS300.html") (same as the UVAL-D8205 without the ethernet) and [USB VGA Adapter UVGA-A8201]("http://www.mct-us.com/products/product_A8201.html")
[*] Startech [  USB2VGAE2]("http://www.startech.com/AV/USB-Video-Adapters/USB-VGA-External-Multi-Monitor-Video-Adapter~USB2VGAE2")
[*] [USB 2.0 to WSXGA+ Adapter # UTV-100A1]("http://www.chipsetcomm.com.tw/products/product.aspx?main=0&sub=103")
[*] Others ???
[/LIST]

My goal with this thread is to hopefully weave together all of the other threads here and on launchpad with other folks who have done work on this in an effort to "concentrate our fire" and get a workable solution.

[SIZE="3"]**Timeline**
[/SIZE]
It looks like there was a driver that was started by MCT based off of the **sisusbvga** kernel (probably for another OEMs project) and that was provided to "Samir Saidani" (saidani at tuxfamily org), that effort [got the device to detect, but it was not usable]("http://lists.laptop.org/pipermail/peripherals/2009-January/000155.html") ([his wiki w/ instructions and driver tarballs]("http://wiki.laptop.org/go/User_talk:Samir/USB2VGA_UVT-100_dev")).

[SIZE="3"]**Emergence of support for MWS300 in a Debian-based distro**
[/SIZE]
Skip ahead some time and a number of commits by Mario Izquierdo (mariodebian at gmail com) [1]("http://max.educa.madrid.org:8000/changeset/691") [2]("http://max.educa.madrid.org:8000/changeset/692") [3]("http://max.educa.madrid.org:8000/changeset/902") appear on a educational Linux distro called MAX/EducaMadrid based out of Madrid, Spain which [COLOR="Blue"]**seems to suggest support for MWS300 multipoint workstations**[/COLOR] as well as DisplayLink based devices for classrooms (aka USBSeats).

Mario also posted a blog posting about another device powered by MCT Trigger 1+ [here]("http://mariodebian.com/post/1/697")

Here's a [video showing off  Trigger 1+ based MWS300 clients being used to power a classroom]("http://mediateca.educa.madrid.org/reproducir.php?id_video=9n1orim32f61z8tv"), 6-usb video cards per desktop server.

**[SIZE="3"]Stuff to hack on[/SIZE]**

There are some i386/AMD64 packages for XOrg.conf at these links, and there maybe kernel drivers for trigger usb, etc in the kernel of the distro itself which is downloadable from [http://www.educa2.madrid.org/web/max/descarga]("http://www.educa2.madrid.org/web/max/descarga")

[LIST]
[*] [http://max.educa.madrid.org:8000/max60/pool/main/x/xserver-xorg-video-tusb/]("http://max.educa.madrid.org:8000/max60/pool/main/x/xserver-xorg-video-tusb/")
[*] [http://max.educa.madrid.org:8000/max60/pool/extras/x/xserver-xorg-video-tusb/]("http://max.educa.madrid.org:8000/max60/pool/extras/x/xserver-xorg-video-tusb/") [COLOR="SeaGreen"]<-- newest X11 driver for TUSB (built on libusb)[/COLOR]
[*] [http://max.educa.madrid.org:8000/max60/pool/extras/m/max-multiseat/]("http://max.educa.madrid.org:8000/max60/pool/extras/m/max-multiseat/")[COLOR="SeaGreen"]<-- some multi-seat config including udev rules needed to load drivers I think[/COLOR]
[*] [http://max.educa.madrid.org:8000/svn/trunk/max-hardware/usr/share/max-hardware/EeePC/xorg-tusb-clone.conf]("http://max.educa.madrid.org:8000/svn/trunk/max-hardware/usr/share/max-hardware/EeePC/xorg-tusb-clone.conf")
[/LIST]

[SIZE="4"][COLOR="DarkRed"]Anyone game to have another go at getting this working?  :)
[/COLOR][/SIZE]

**[SIZE="2"]Other background reading[/SIZE]**
[LIST]
[*] [Launchpad Bug for Startech USB2VGAE2]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/517934")
[*][Userful multi workstation support page]("http://webcache.googleusercontent.com/search?q=cache:dURDVxHoVTsJ:support.userful.com/wiki/index.php/UMs/HowTo/Troubleshooting+Magic+Control+technology+Corporation+wiki&cd=26&hl=en&ct=clnk")
[/LIST]

---

### Post by qterm on 2011-09-22
Is there any measures to make Tritton XD300 working in Debian/Ubuntu system. Thanks.

---

### Post by ironstorm on 2011-09-22
> **qterm said:**
> Is there any measures to make Tritton XD300 working in Debian/Ubuntu system. Thanks.

Not at the moment, all the necessary bits do exist in the MaX Madrid Educational distro which is a debian based distro...  I've run the XD300 off of 6.5rc2 of that distro... so with work I have little doubt it could be done.

---

### Post by jhellen on 2012-09-29
Does it work with 12.04?

---

### Post by hackerseraph on 2012-10-19
> **jhellen said:**
> Does it work with 12.04?

i just picked one up from bestbuy, out of the box not working, but shows in lsusb 

toying with it now, will post back

---

### Post by ironstorm on 2012-10-19
A long time ago when I was playing with it,  I captured my history:

```
setxkbmap us
sudo aptitude update
sudo aptitude install max-multiseat
sudo aptitude install max-language-en
cd /etc/gdm
sudo nano gdm.conf-custom # set 0=localseat
cd /etc/ssh
sudo nano sshd_config # remove madrid from DenyUsers list
sudo service ssh restart
ssh localhost
cd /lib/udev
sudo mv xorg.conf.display0 xorg.conf.display0.disabled # disable default profile which wants to use a serial/PS2 mouse

```

I was using MaX 6.52, I recall having to plug in a usb-to-ps2 adapter into a specific USB port on the XD300 in order that it would detect and spawn an X session on the XD300.

I see there's an ISO for MaX 7.0, I wonder if it still works with MWS300 and if they might have packaged their support up (it's a debian-based distro like ubuntu)...  

Anyway, I don't have time to chase these things, so I will have to be content to wonder.

---

