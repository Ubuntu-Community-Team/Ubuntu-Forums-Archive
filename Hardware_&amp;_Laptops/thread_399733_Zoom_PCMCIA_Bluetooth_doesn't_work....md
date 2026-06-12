---
title: "Zoom PCMCIA Bluetooth doesn't work..."
date: 2007-04-02
forum: Hardware &amp; Laptops
---

### Post by msikka on 2007-04-02
Hi all, I have a Panasonic CF-73 notebook with Ubuntu 6.10 and Windows XP on it. I have a Zoom PCMCIA bluetooth card that does not even seem to be detected by "hcitool dev". I just get a blank line as output on entering the above command. I've tried everything listed in the bluetooth help guides and nothing works. Also, the Ubuntu bluetooth guide claims that my Zoom card is supported by Linux.

I would really appreciate some help. I need to get everything working or else I can't rest!! :) Everything else works flawlessly on this laptop with Ubuntu.

Thanks

---

### Post by Permafrost91 on 2007-08-16
I would also like to know how to do this ... I bought a Zoom card because I thought it was supported but I'm having the same problems you describe.

---

### Post by eelliott999 on 2007-09-04
I'm most of the way there.  I can manually get a bluetooth mouse to work through the Zoom.  The remaining step is to get it to work automatically on a boot.

I've been working a long hard day on just this problem, so please excuse me if I just dump the notes I've been keeping:

eelliott@Toshiba:~$ sudo hciattach ttyS1 zoom	(zoom was not in any docs, but I was frustrated.)
eelliott@Toshiba:~$ hcitool dev			
Devices:
        hci0    00:10:60:AB:44:6D		(first time I ever got a positive result)
eelliott@Toshiba:~$ sudo hcitool scan             (after pressing the DISCOVER button on the mouse)
Scanning ...
        00:02:76:08:64:CE       Si670m Bluetooth Wireless Notebook Mouse
eelliott@Toshiba:/etc/init.d$ sudo /etc/init.d/bluetooth restart
 * Restarting Bluetooth services
--------------------                                             [ OK ] 
eelliott@Toshiba:/etc/init.d$ hcitool dev		(just making sure everything still OK)
Devices:
        hci0    00:10:60:AB:44:6D
eelliott@Toshiba:/etc/init.d$ sudo hidd --connect 00:02:76:08:64:CE
eelliott@Toshiba:/etc/init.d$ hcitool con			(display connections)
Connections:
        < ACL 00:02:76:08:64:CE handle 41 state 1 lm MASTER	(and the bluetooth mouse now moves the cursor)
---------------------
(if you issue a   $ sudo hidd --connect    command and receive the "Can't listen..." message, try the reset command on the next line)
Can't listen on HID control channel: Address already in use
eelliott@Toshiba:/etc/init.d$ sudo hciconfig hci0 reset  (good command to know in case of the "Can't listen" message)
------------------
To make changes permanent:
Modified  /etc/default/bluetooth to include HIDD_OPTIONS="--connect 00:02:76:08:64:CE"
--------------------
AFTER REBOOT, BLUETOOTH MOUSE NOT WORKING (hopefully because I forgot the echo command):
eelliott@Toshiba:~$ sudo hciattach ttyS1 zoom
eelliott@Toshiba:~$ sudo hcitool dev
Devices:
        hci0    00:10:60:AB:44:6D
eelliott@Toshiba:~$ sudo hidd --connect 00:02:76:08:64:CE
Can't get device information: Host is down
eelliott@Toshiba:~$ sudo /etc/init.d/bluetooth restart
 * Restarting Bluetooth services                                         [ OK ] 
eelliott@Toshiba:~$ hcitool con
Connections:
        < ACL 00:02:76:08:64:CE handle 41 state 1 lm MASTER 
eelliott@Toshiba:~$ echo hidp | sudo tee -a /etc/modules
hidp
eelliott@Toshiba:~$ 
--------------------
AFTER REBOOT, BLUETOOTH MOUSE STILL NOT WORKING
I think the problem is that nowhere in the boot process is "sudo hciattach ttyS1 zoom" executed.

Hope this helps.  When I solve the boot problem, I'll post that.

Ed

==============
20070905: My Zoom and the bluetooth mouse are now working after boot.

I went through a lot of false paths, but I think it boils down to this:

1) This step gets the Zoom working:
eelliott@Toshiba:/etc/bluetooth$ sudo gedit uart	(new file /etc/bluetooth/uart. Used by bluetooth script. Just contains 1 line: ttyS1 zoom  #you may need to use ttyS0 or ????). 

2) For the bluetooth device (not the Zoom):
 Edited /etc/default/bluetooth
	HIDD_OPTIONS="-i hc0 --connect 00:02:76:08:64:CE --master --server"                   # the address is unique to your bluetooth device (not the Zoom): $ hcitool con  OR $ hidd --show

3) For the bluetooth device (not the Zoom):
 This step may not be necessary. I did it early in the process and don't feel like testing without it:
	modified /etc/bluetooth/rfcomm.conf:
	rfcomm0 {
		bind yes;
		device 00:02:76:08:64:CE;                                                        # the address is unique to your bluetooth device (not the Zoom): $ hcitool con  OR $ hidd --show
		comment "Broadcom Bluetooth Wireless Mouse";                       # I used the Service Name from $ sdptool browse 00:02:76:08:64:CE
	}

---

### Post by cyberco on 2007-09-14
I have no luck getting my Zoom 4312 Bluetooth PC-Card working. 

The following command:
sudo hciattach ttyS1 zoom

results in:
"Can't initialize device: Illegal seek"

Bluetooth is running ('/etc/bluetooth restart' works and the PC-card is flashing).

I've searched all fora etc, but no luck yet.

What I've tried:
[https://answers.launchpad.net/ubuntu/+question/6438](https://answers.launchpad.net/ubuntu/+question/6438)
[https://help.ubuntu.com/community/BluetoothSetup](https://help.ubuntu.com/community/BluetoothSetup)

Cheers!

---

### Post by cyberco on 2007-09-16
My bad: I should've used ttyS0 instead. Now it works (partly).  What still doesn't work: listing broadcasted services. The sdptool doesn't list anything. In Windows XP PyBluez (the python module for bluetooth devices) the services are listed just fine.

---

### Post by aws910 on 2008-05-10
I'd just like to add something that helped me... I haven't gotten my device to work yet, but the command "hciattach -l" was something I just found: it tells you what device name to use - the people on this thread are using a zoom, but my device, by running "lsusb", is a "cambridge silicon radio".  I'm thinking I have to use "csr"

---

### Post by aws910 on 2008-05-11
finally got mine to work, with help from this site:
[http://www.klabs.be/~fpiat/linux/bluetooth/bluetooth_HOWTO.html](http://www.klabs.be/~fpiat/linux/bluetooth/bluetooth_HOWTO.html)

the command that saved me was "sudo hciconfig hci0 reset"

---

