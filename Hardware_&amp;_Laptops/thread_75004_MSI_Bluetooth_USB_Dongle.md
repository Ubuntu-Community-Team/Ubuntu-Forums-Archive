---
title: "MSI Bluetooth USB Dongle"
date: 2005-10-13
forum: Hardware &amp; Laptops
---

### Post by daschl on 2005-10-13
Hi folks :)

I got this Bluetooth Dongle
[http://www.msicomputer.com/product/p_spec.asp?model=PC2PC_Bluetooth&class=com](http://www.msicomputer.com/product/p_spec.asp?model=PC2PC_Bluetooth&class=com)
but i dont know how to install it.

when i plug it in, dmesg says
```

[4295938.963000] usb 1-1: new full speed USB device using ohci_hcd and address 3

```

and lsusb
```

Bus 003 Device 001: ID 0000:0000
Bus 002 Device 001: ID 0000:0000
Bus 001 Device 003: ID 0db0:1967 Micro Star International Bluetooth Dongle
Bus 001 Device 001: ID 0000:0000

```

Finally, I want to use it with my Nokia 6600 (transfer images and so on..)

Which software is the best for this application?
Wich kernel module do i have to load? (Is there one?)

I hope you can help me :)

kind regards,
Mike

---

### Post by daschl on 2005-10-13
erm, well.

i used the Bluez stack, which comes with ubuntu 5.10.

when i scan the devices around my dongle:
```

mn@main:~$ hcitool scan
Scanning ...
        00:0E:6D:5E:E7:D1       MN_Bt keke

```

Ok, it finds it, so when i go to the next step:
```

mn@main:~$ rfcomm  connect hci0 00:0E:6D:5E:E7:D1
Can't connect RFCOMM socket: Connection refused

```

It shows me this. I inserted this Code, when the Popup on my mobile phone comes up:

```

mn@main:~$ cat /etc/bluetooth/pin
1234

```

but - as you see - the connection is still refused.

any suggestions?

kind regards,
mike

---

### Post by vitti on 2005-10-20
Me too I wish to use an usb bluetooth dongle and my phone nokia 6600!
And it was working before with hoary, but :confused:  now with breezy when I submit the command:
 [INDENT]root@trudyx:/home/vitti # hcitool scan[/INDENT]
I got this answer:
[INDENT]Device is not available: No such device[/INDENT]
and dmesg is:
[INDENT][4317056.680000] usb 1-1: new full speed USB device using uhci_hcd and address 4
[4317141.891000] hci_cmd_task: hci0 command tx timeout
[4317162.540000] Bluetooth: L2CAP ver 2.7
[4317162.540000] Bluetooth: L2CAP socket layer initialized
[4317162.566000] Bluetooth: RFCOMM ver 1.5
[4317162.566000] Bluetooth: RFCOMM socket layer initialized
[4317162.567000] Bluetooth: RFCOMM TTY layer initialized
[/INDENT]
and for lsub:
[INDENT]root@trudyx:/home/vitti #  lsusb
Bus 003 Device 001: ID 0000:0000
Bus 002 Device 001: ID 0000:0000
Bus 001 Device 004: ID 0a12:0001 Cambridge Silicon Radio, Ltd Bluetooth Dongle (HCI mode)
Bus 001 Device 003: ID 046d:c00c Logitech, Inc. Optical Wheel Mouse
Bus 001 Device 001: ID 0000:0000
[/INDENT]

Is there anyone that can help me?
Thanks!:smile:

---

### Post by Zonkle on 2005-12-19
Hey guys ;),

I have USB MSI bluetooth Pc2Pc (Not the exact same one in the web site above:?) and Nokia 6600 too :) and it works great!

Very easy. Just go to Synapatic (You to need enable the Universe and Multiverse stuff) and look for gnome-bluetooth and check it for install, after that just read this little helpfull article to see how to send and recieve [http://doc.gwos.org/index.php/GnomeBlueTooth](http://doc.gwos.org/index.php/GnomeBlueTooth) , and that's set :)

My MSI bluetooth worked much better and easier in Ubuntu than in Windows XP .... because you know you have to do the Authentication Key thing in XP to make the bluetooth enabled... and I was successfull with that only once :P

No need to do a single thing in the Terminal :)
But I'm looking around to see if I could like synchronize the Contacts and Calender. Any?

Cya ;)

---

### Post by iam10ninjas on 2005-12-19
[http://ubuntuforums.org/showthread.php?t=75978&highlight=bluetooth](http://ubuntuforums.org/showthread.php?t=75978&highlight=bluetooth)

The above thread will tell you how to install kdebluetooth. GNOME bluetooth is utter crap. KDE bluetooth is far more developed.

edit your /etc/bluetooth/hcid.conf so it matches the one I have that works. It might not work for you but it took me about a week of experimenting to get it to work. Now it works every time. You can find it here:

[http://ubuntuforums.org/showpost.php?p=582960&postcount=7](http://ubuntuforums.org/showpost.php?p=582960&postcount=7)

---

