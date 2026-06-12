---
title: "Can't get Creative SB X-FI Extreme Audio(PCI) working in Ubuntu 8.04"
date: 2008-07-06
forum: Hardware
---

### Post by EvoKing on 2008-07-06
Hi everybody. I've got a little but very frustrating problem. The problem is that I can't get my Creative SB(Sound Blaster) X-FI Extreme Audio(Interface:PCI) working in Ubuntu 8.04. In the Swedish forum I found a How To-guide explaining how to install and get the Creative Sound Blaster X-FI Extreme Audio working. First, I downloaded the alsa-driver 1.0.16.tar.bz2 from this site: [http://www.alsa-project.org/main/index.php/Main_Page]("http://www.alsa-project.org/main/index.php/Main_Page") . Than I install the drivers by typing in the folowing commands in the terminal:

Commando 1:     sudo apt-get install build-essential

Commando 2:     cd where_you_have_downloaded_the_drivers

Commando 3:     tar xvf alsa-driver-1.0.16.tar.bz2

Commando 4:     cd alsa-driver-1.0.16

Commando 5:     sudo ./configure

Commando 6:     make

Commando 7:     sudo make install

when It was finished I restarted my computer. When you have restarted your computer the sound card is going to work BUT it doesen't. Somebody know what I am doing wrong and what can I do to get it working. Because I know I have got it working one time before but the thing is that I really don't remember if I used OSS(Open Sound System)-drivers or if I used Alsa-drivers.


Sorry for my bad engalish. I'm Swedish

---

### Post by EvoKing on 2008-07-06
come on damnit!! can nobody help me:confused:

---

