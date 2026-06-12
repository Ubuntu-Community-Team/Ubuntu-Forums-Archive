---
title: "Need to run the Synce config tool?"
date: 2008-07-22
forum: General Help
---

### Post by Kain000 on 2008-07-22
Hey everyone,
I've been looking arround for a way to connect to my win mobile 6 device, and found this thread about just that,
 [https://help.ubuntu.com/community/PortableDevices/WindowsMobile]("https://help.ubuntu.com/community/PortableDevices/WindowsMobile")  

however when I run the command 
sudo synce-serial-start  I get the following message
<sean@Inspiron:~$ sudo synce-serial-start

synce-serial-start was unable to find the file /etc/ppp/peers/synce-device:

Please run the synce-serial-config tool to create this file before running this
script again.>
and I cant find how to run the config tool anywhere.
any ideas?

when I run the command
sudo synce-serial-config I just get 

Syntax for synce-serial-config:

  synce-serial-config serial-device [local-ip-address:remote-ip_address [DNS-server-name]]

  The serial-device specifies the name of your serial port device.

  These are the port names on Linux:

    ttyS0  The first serial port
    ttyS1  The second serial port
    ...

  You can also connect via an infrared connection (IrDA). This requires
  that you already have irattach running.

    ircomm0  The first IrDA communication port

  Please send corrections and updates to the above information to the
  SynCE development mailing list: [email]synce-devel@lists.sourceforge.net[/email]

  If you do not provide the local_ip_address:remote_ip_address parameter,
  synce-serial-config will use 192.168.131.102:192.168.131.201.

  If you want to specify these addresses yourself, you may want to read
  about the same option on the man page for pppd.

I think that the serial port ttyso0 should be ttyusb0 but dont know how to change that.
and I am sorta lost.... any help?

---

