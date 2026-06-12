---
title: "Using a USB attached to a router - is it really fraught with danger?"
date: 2016-06-26
forum: Hardware
---

### Post by makem2 on 2016-06-26
I have n Asus RT-AC68U router which has two USB ports, one being USB3.These can be configured for several purposes, one of which is as an ftp server.

I do a lot of traveling and sometimes need access to data which I could make available on an ftp server.[COLOR=#FFFFFF][FONT=Arial][/FONT][/COLOR] However, reading about how to go about this, I find that many people have trouble accessing the USB from Linux and there are notes that no matter how you configure the server it is open to abuse from the WAN and could allow a hacker to gain access to your LAN. Being relatively new to Linux, I would not know if was or was not secure.

I am aware that some information on the web is out of date and wondered if anyone was able to say that with the proper setup, it could today be made secure.

---

### Post by weatherman2 on 2016-06-26
Well...yes, if you don't know what you are doing, you could easily expose your data to risk by putting it on your router.

But there are safe ways to do it.

First of all, don't use FTP. Or at least, use SFTP (secure FTP) or ssh.

I have one router at a relative's house and use it to back up data remotely, using a flash drive in the router's USB port.  The way I secure it is to open up the router to ssh login over the WAN but require certificates and disable password login.  So you can't connect to it remotely without the right certificate. I suppose nothing is 100% secure, because there are always zero day vulnerabilities that aren't well known and not patched, but this is pretty secure, and I doubt I am a specific target - only a target to drive-bys who check for open servers that aren't secured.

To access my own data remotely, I use a VPN on my home network.  The VPN runs on my router, and I have my data on a server on my home network.  I can connect to the VPN and wake up the server remotely.  Then I can either access it via ssh or connect to the display using VNC.  My VPN uses certificates not passwords so, again, should be pretty secure.

I also use open source firmware on my routers.  I prefer Tomato firmware, which runs on your RT-AC68U if you want it.  Tomato has features built in to enable remote ssh, and I would certainly do that (with certificates) instead of the old, ancient non-encrypted FTP protocol.

 Note that flashing your router firmware can be dangerous (it could brick your router if you mess it up) - it's a major thing you are doing, though I've done it dozens of times on different routers.  Usually it's easy, but you need to proceed carefully and be aware of what you are doing.  Here's a guide to flashing yours using an Asus utility that seems to run on Windows - probably a way to do it via Linux, but usually I can flash without using any utility.  I prefer the Shibby flavor of Tomato firmware:

[http://www.shadowandy.net/2014/03/asus-rt-ac68u-flash-tomatousb-rt-ac68u.htm](http://www.shadowandy.net/2014/03/asus-rt-ac68u-flash-tomatousb-rt-ac68u.htm)

Tomato adds some sweet features such as VPN, file sharing from USB drives, etc.

---

### Post by makem2 on 2016-06-26
Thank you for that guidance.

Do you know where I can find up-to-date guidance on:

"To access my own data remotely, I use a VPN on my home network.  The VPN  runs on my router, and I have my data on a server on my home network.  I  can connect to the VPN and wake up the server remotely.  Then I can  either access it via ssh or connect to the display using VNC.  My VPN  uses certificates not passwords so, again, should be pretty secure"

The vpn runs on my router and the folders I want access to are on a usb plugged into the router.

---

### Post by weatherman2 on 2016-06-26
Well, my router uses Tomato firmware. and I use OpenVPN. Setting up the VPN in Tomato is very easy, but there's a more involved process of generating the certificates you need then pasting them into the Tomato VPN setup page and also getting your laptop or remote device to connect as a client can take some time.

If you have Tomato, it might be easier than setting up VPN to enable the remote ssh login like I did on one of my routers, but use certificates and disable password login.  Here's how you generate the certificate you need:

[https://linuxconfig.org/passwordless-ssh](https://linuxconfig.org/passwordless-ssh)

You'd paste the file id_rsa.pub created in the steps above into the router ssh config.  Then disable ssh password login.  Make sure you can connect by ssh first on your local network without a password.  If that works, then you can open it up on your WAN and connect remotely.

You can use ssh sort of like ftp and copy files securely.

But if you don't have Tomato (or DD-WRT or another open firmware) on your router, then I really can't help you further.  The manufacturer firmware in routers like your Asus tend to have very limited features only available in more expensive routers or in the Tomato/DD-WRT open firmwares.

---

### Post by makem2 on 2016-06-27
Merlin asuswrt software has been installed on my router and it has vpn capabilities. I am able to either export a file which contains the security information to client machines, or as you say manually produce the certificates.

What I am looking for is a source of up-to-date guidance on the method of instigating security and the means of accessing the usb remotely. I prefer not to introduce another unknown by installing (with risk), an alternative firmware. I have some knowledge of ssh and use putty to access raspberry pi's which I use.

---

### Post by kurt18947 on 2016-06-27
I'm using DD-WRT - similar to Tomato and other replacement firmware. I can't use it on my primary router but use it on a secondary machine. My primary router is used with Verizon FiOS and I use MOCA networking - it's very convenient and uses cables already in place. None of the 3rd party router firmwares support MOCA so no *wrt on that device. Other services use MOCA as well - often for shared DVR type services so something to be aware of.

---

