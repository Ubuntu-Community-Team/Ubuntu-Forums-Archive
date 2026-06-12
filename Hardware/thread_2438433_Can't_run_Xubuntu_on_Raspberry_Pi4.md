---
title: "Can't run Xubuntu on Raspberry Pi4"
date: 2020-03-12
forum: Hardware
---

### Post by sgy939 on 2020-03-12
Newbie to Ubuntu forums.
A note to Moderators,  if I'm posting in the wrong forum, please move it as appropriate.

I'm trying to get Xubuntu run on a Raspberry Pi4.
Steps taken so far
Downloaded Ubuntu Server 18.04.4 for Raspberry Pi.  64-bit, to my laptop.
[https://ubuntu.com/download/raspberry-pi/thank-you?version=18.04.4&architecture=arm64+raspi3](https://ubuntu.com/download/raspberry-pi/thank-you?version=18.04.4&architecture=arm64+raspi3)

Copied image to a 32gb microSD card using
[https://ubuntu.com/tutorials/create-an-ubuntu-image-for-a-raspberry-pi-on-ubuntu#2-on-your-ubuntu-machine](https://ubuntu.com/tutorials/create-an-ubuntu-image-for-a-raspberry-pi-on-ubuntu#2-on-your-ubuntu-machine)

Noticed that there was a lot of  unallocated space to the right of the writable partition.
Opened Gparted and expanded the writable partition to the right, almost all of the available space.

Booted Ubuntu Server 18.04.4 for Raspberry Pi.  64-bit on my Raspberry Pi4,  4GB RAM. With the Ethernet port connected.  It opened up in terminal mode.  Changed password as required on first boot.
Downloaded  xubuntu using
sudo apt-get install xubuntu-desktop and ran update.

Shutdown using, shutdown now, command.
Rebooted.  Hoping that it would boot to Xubuntu desktop. Still in terminal.
This is where I'm stuck.
How do I start the Xbuntu desktop?  What command do I use to do so?  Make it to automatically boot to the desktop?

When I check the SD card on my laptop and searched for Xbuntu in the writable partition  there are a lot of folders and files.
It looks like all of it is there, I just can't get it to run.

Thanks in advance for all replies.

---

### Post by guiverc on 2020-03-12
I don't have a r.pi.4 so haven't tried, but I'll provide the following from a key Xubuntu developer

[https://bluesabre.org/2019/10/20/install-xubuntu-19-10-on-a-raspberry-pi-4/](https://bluesabre.org/2019/10/20/install-xubuntu-19-10-on-a-raspberry-pi-4/)

---

### Post by sgy939 on 2020-04-12
Thanks for your reply guiverc
Got Ubuntu 19.10 running on my raspberry PI4.
A lot hiccups but it's up and running!

---

### Post by cybrsaylr on 2020-04-12
Been curious about getting a Raspberry Pi4 with 4GB of RAM.
How would you rate Raspberry Pi4 performance either with its native linux OS or with one of the Ubuntu flavors installed? 
Been told to expect it to run and have the performance of laptops from 10-15 years ago.  Is this true or does  Raspberry Pi4 run better?

---

