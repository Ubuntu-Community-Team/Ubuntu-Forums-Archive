---
title: "Installing Ubuntu over Local Network"
date: 2008-12-28
forum: Installation &amp; Upgrades
---

### Post by arubislander on 2008-12-28
I often find myself installing Ubuntu on computers (mostly laptops) that either don't have a CD-ROM drive or the drive is defective. These machines typically cannot boot from usb so that isn't an option either. (Yes, I admit, I like to extend  the life of machines that would be considered obsolete for that other OS).
I have two tutorials that help me out each time: [this one]("http://ubuntu-tutorials.com/2007/10/11/how-to-configure-pxe-network-booting-on-ubuntu-for-network-based-installations/") and [this one]("http://myy.helia.fi/~karte/ubuntu_pxe.html"). But the information on them is somewhat dated and needs a little tweaking to get it to work. So I decided to try my hand at writing a clearer one.

If the computer you are targeting for installation cannot be coaxed to boot from a network then this post sadly won't be of any help to you.

You'll need:
[LIST]
[*]A working network and internet connection
[*]The Alternate CD image of your flavor of Ubuntu of choice
[*]Two computers: one to host and serve the boot files (the server), and packages and the installation target that will boot from network (the client).
[*]Some knowledge of how your network is configured.
[/LIST]

On the server you will need to install the following packages:
[LIST]
[*]tftpd-hpa
[*]tftp-hpa
[*]dhcp3-server
[*]apache2
[/LIST]

You could install them each individually but it is just as easy to open a terminal window (or use Guake in Ubuntu or Yakuake in Kubuntu, both highly recommended for their level of coolness) and enter:
```
$ sudo apt-get install tftpd-hpa tftp-hpa dhcp3-server apache2
```

You might get an error message when the dhcp server configures itself, but that's because we haven't configured any subnets yet. We'll get to that later on.

First off we'll mount the CD image. To save some disk space at the cost of a slight performance penalty we'll mount the disk image directly under our web directory. Let's create a directory under /var/www:
```
$ sudo mkdir /var/www/oneiric
```
Now we mount our cd image under our newly created directory:
```
$ sudo mount -o loop ubuntu-11.10-alternate-i386.iso /var/www/oneiric
```

Having done that we can test to see if the location is accessible. Open your browser of choice and enter this url:
[http://localhost/oneiric](http://localhost/oneiric)
You should see a listing of the contents of the CD.

Next we'll configure the Trivial File Transfer Protocol (tftp)
The configuration file for the service is located at /etc/default/tftpd-hpa. You'll need root privileges to edit this file:
```
$ sudo nano /etc/default/tftpd-hpa
```
Instead of nano you can use a gedit or vim or whatever of course.

Edit the file to look something like this:
```

#Defaults for tftpd-hpa
RUN_DAEMON="yes"
OPTIONS="-l -s /var/lib/tftpboot"
```

Make sure the RUN_DEAMON entry's value is "yes" (double quotes and lowercase.) It's probably best to leave the last entry alone, just be sure to make a note of the directory it points to (in the above case: /var/lib/tftpboot)

Now we have to populate the boot directory with with the right files. Copy the contents of the netboot directory of the CD image to /var/lib/tftpboot:
```
$ sudo cp -R /var/www/oneiric/install/netboot/* /var/lib/tftpboot/
```

Check to see if the tftp server has been setup correctly:
```
$ sudo /etc/init.d/tftpd-hpa restart
$ tftp localhost -c get pxelinux.0
$ ls -l pxelinux.0
```

Make sure the file listed is bigger than 0 bytes. If that is the case, then the setup has worked. If it has not, then please go over the above steps carefully. If all is well you can delete the file
```
$ rm pxelinux.0
```

Finally we setup our dhcp server to allow the client to boot via the network.
```
$ sudo nano /etc/dhcp3/dhcpd.conf
```

Add a subnet entry similar to the following:

```

subnet 10.0.0.0 netmask 255.255.0.0 {
    host install-server {
        # only give DHCP information to client computer:
        hardware ethernet 00:00:00:00:00:00; 
                          #Replace with the actual MAC address of the network card of the client computer
        # Basic DHCP info (see 'ifconfig', 'route', 'cat /etc/resolv.conf')
        fixed-address 10.0.0.13; 
                      #the ip address that the regular dhcp server (the router) issues to the client
        option subnet-mask 255.255.0.0;
        option routers  10.0.0.1; 
                        # the ip address of the router
        option domain-name-servers 172.28.1.67, 172.28.1.69; 
                                   #the domain name servers your router uses. Don't really know if these are necessary...

        # TFPT server for PXE boot
        next-server 10.0.0.5; 
                    # ip address of server (this computer)
        filename "pxelinux.0";
    }
}

```

Here's where your knowledge of the way your network is configured comes into play. Replace the ip addresses with the ones that are appropriate for your network setup.

Now start the dhcp server:
```
$ sudo /etc/init.d/dhcp3-server restart
```

Connect the client to the network (wired works best I find) and set it up to boot via the network.

When the Installer boot menu comes up choose Install (the default selection) and press ENTER.
Follow the prompts of the installer choosing the right options for you. When you come to the 'Choose a mirror of the Ubuntu archive' screen choose the option: 'enter information manually' (in my test it was the topmost option).
For the hostname enter the IP address of the computer you configured as the server.
For directory enter the directory to which you mounted the CD image (/oneiric/ in this example).
Leave the proxy entry blank, answer the additional prompts and sit back while your system installs.

The installation is slower than from CD, but much faster than installing over the internet.

HTH.

---

### Post by xtracool_protik on 2009-02-06
Hey arubislander,
 nice post it worked just as supposed to be. However here is a little addition:
 If somebody wants to install it through local network (without internet connection)
 1. Copy all the content of CD/iso image to /var/www/<any folder most probably ubuntu>/ on dhcp server - host
 $ sudo cp <iso>/* /var/www/ubuntu/ -R
 2. Start installation when ubuntu asks for country chose **"enter information manually"**. The first option in the list of countries.
 3. When hostname is asked - put the ip address where apache server is running host (dhcp server) ip address.
 4. path to publicly shared folder <folder under www> in this case /ubuntu/
 5. next step (proxy something) leave it blank.
 
 and done :D

Thanks to this post as well:
[http://ubuntu-tutorials.com/2007/10/11/how-to-configure-pxe-network-booting-on-ubuntu-for-network-based-installations/](http://ubuntu-tutorials.com/2007/10/11/how-to-configure-pxe-network-booting-on-ubuntu-for-network-based-installations/)

---

### Post by arubislander on 2009-02-06
Oops! A grave omission on my part.

You are right of course, that was the whole reason for setting up the webserver in the first place! I will add your comments in the main article at the earliest convenience.

---

### Post by xtracool_protik on 2009-02-11
My pleasure :) keep up the good work

---

