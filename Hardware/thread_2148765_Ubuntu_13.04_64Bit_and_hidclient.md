---
title: "Ubuntu 13.04 64Bit and hidclient"
date: 2013-05-26
forum: Hardware
---

### Post by Serg86 on 2013-05-26
Hey,

I've been looking for a solution to connect my PCs USB-keyboard and mouse to my PS3 via bluetooth and found "[hidclient]("http://anselm.hoffmeister.be/computer/hidclient/index.html.en")".

I used the updated source and instructions at the bottom of the page (For Ubuntu 12.04). After installing the package "libbluetooth-dev" it compiled without any errors or output. I also made the changes to /etc/bluetooth/main.cfg as suggested and restarted my PC to make sure they take effect.

Running "sudo ./hidclient -l" lists all of my input devices correctly as far as I can tell. "sudo ./hidclient -e3" (Keyboard) didn't show any errors either. My PS3 is able to find the bluetooth device "ubuntu-0" (default name), but can't connect. It asks for a passkey, I tried 1234, 0000. 1111, 0001 but none worked.

I've also tested it with my android phone, it pairs, console output on the PC notified me of a successfully established connection and the icon is a keyboard. I opened up a text editor on my phone, but as soon as I start typing it says "Connection lost."

Adding the "-x" parameter does not appear to have any effect at all, all peripherals still work.

Am I doing something wrong?
Will it simply not work in Ubuntu 13.04?
Are there other solutions I could try to accomplish the same?

Thanks.

---

### Post by OctavioL on 2013-07-01
I finally got hidclient working with my PS3. I thought I'd share the steps I took to get it working and hopefully they work for you too.

First I replaced Ubuntu's default Bluetooth Manager with Blueman.
(I had previously gotten hidclient to work on Lubuntu 12.10 and Blueman was the default bluetooth manager. If it worked there, I thought it'd work in Ubuntu also)

Then in the terminal I ran:
sudo sdptool del 0x10000
sudo sdptool del 0x10001
.
.
.
sudo sdptool del 0x10008
(in hidclient.c it says you might have to remove any non-HID SDP records for picky devices. PS3 happens to be one of those picky devices)

Finally I ran sudo ./hidclient -e2 ,replace 2 with whatever you keyboard is on the device list.

And that's it, just pair like you normally would.

---

