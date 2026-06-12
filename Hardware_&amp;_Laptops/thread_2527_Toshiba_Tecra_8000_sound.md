---
title: "Toshiba Tecra 8000 sound"
date: 2004-10-29
forum: Hardware &amp; Laptops
---

### Post by rmdnet on 2004-10-29
Hi,

I have a Toshiba Tecra 8000 laptop (yes, a little bit old) and yesterday installed Ubuntu after trying Suse and Yoper on it. All the installation went fine, it detected my Xircom ethernet card and all the other hardware without problems except .... the soundcard. And that's the most important one, because I want to use it as a kind of mp3/ogg/mpg player. On Yoper and Suse happened the same but running alsaconf solved the problems. The sound card is a OPL3-SAx. How can I make it work. I know that alsaconf is not present so, how can I load the module (I suppose this must be the solution)

Thanks a lot

---

### Post by buellman on 2004-11-13
[QUOTE=][/QUOTE]
 hi...

a few days ago i had the same "problem". i wrote my solution to the ubuntu-mailinglist. here is the link. hope it helps:
[http://lists.ubuntu.com/archives/ubuntu-users/2004-November/009979.html](http://lists.ubuntu.com/archives/ubuntu-users/2004-November/009979.html)

greets. buellman

---

### Post by rmdnet on 2004-12-13
It works!

Thanks a lot, now my laptop goes like a charm with Ubuntu.

Rmdnet

---

### Post by buellman on 2004-12-13
cool that it works for you :-)

greets. buellman

---

### Post by rockycairns on 2004-12-21
hi, i have a toshiba tecra 8000 with yamaha sound as well.

being new to linux, my previous attempts to configure sound on my other system with a cs4237b were tricky and unsuccessful.  on my tecra 8000 i followed the instructions by buellman and was pleased to hear music play from my ogg library.

in order to edit the read-only files modules.conf and modules i had to open a terminal and type: "sudo gedit /etc/modules.conf" and "sudo gedit /etc/modules" therefore the only thing i would suggest to make the instructions completely new-user friendly would be to add that information to the instructions.

thanks very much,
rocky.

---

### Post by davros on 2005-01-17
The information above - is this for kernel2.6.x? 

I've been unable to get sound to work on the t8000 in 2.6.x.  I have not tried Ubuntu - I'm using Debian/unstable.

When I try the info above on my system, running aumix fails. some modules are loaded though - I see when I lsmod - prior to running aumix i see no sound related modules at all.

I had considered downgrading to 2.4.x - I'd rather have an older kernel with working sound...

What about the fan? I see a fan module running, but I don't know if the fan ever comes on - it's never running when I put my hand in front of it, and when I feel the hard drive after removing the cover on the side, it's quite hot...

Under 2.4.x, I used the fan utility and kept the fan ON at all times...

--davros

---

### Post by buellman on 2005-01-18
hi!

yep. the info above is for the 2.6.x kernel from ubuntu/warty.

about the rest of your questions i can't tell you to much. with ubuntu the fan works like it should. but i think in comparsion with win2k (same notebook) the fan runs more often and the notebook itself becomes more hot. don't know why.

sound: have you tried "modprobe snd-opl3sa2 dma1=1 dma2=0 fm_port=0x388 irq=5 isapnp=0 midi_port=0x330 port=0x538 sb_port=0x220 wss_port=0x530" at the cmd? that should bring up your module. 
have you checked your bios settings?
maybe ubuntu handles these things someway different than debian?!?

greets. buellman

---

### Post by davros on 2005-01-19
Thanks for the reply.

I was not able to get sound working in my setup, but I did get it working on the Ubuntu LiveCD! Good stuff!

Thanks - and, great distro from what I've seen and read thus far - you may not get me as a regular until Ubuntu officially supports KDE, but good stuff anyway!

The fan also runs fine and the hard drive feels nice and cool...:)

--davros

---

