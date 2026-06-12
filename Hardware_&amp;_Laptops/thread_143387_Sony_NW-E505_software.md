---
title: "Sony NW-E505 software"
date: 2006-03-12
forum: Hardware &amp; Laptops
---

### Post by esters on 2006-03-12
Hello there.
The problem is that,i have an Sony Network walkman E505 but i cannot find the software to upload music,sony says they only support Windows and no other OS.
p.s it's not a drag n drop walkman where u can easily drop your music into the mp3 walkman. :(
So has anyone tried something to similar sony products.

---

### Post by kittycatsexycat on 2006-03-12
i heard that sony products are a bit dodgy because they can only be supported by windows... i dont use sony...

thye make it so that you need to buy their drivers and stuff or it wont work.. its so annoying..


maybe someone has hacked it though...

if its a normal mp3 player try formatting it to fat32... but be careful...

---

### Post by neo-cortex on 2006-04-21
Well, I don't the problem is whether or not it recognizes the drive. Actually, when I plug it into the USB, it recognizes the drive and I can access the folders, but the problem is that you need to use this executable that comes with it in order to upload songs onto it... and I'm curious if there is a way to somehow wine it to work?

---

### Post by dmizer on 2006-05-03
please, for the love of god ... if you find out how let me know.

---

### Post by dmizer on 2006-05-09
okay ... here's what i finally ended up doing.

all my mp3's are naturally on my linux box.  but i put a win2000 box together from spare parts laying around.  it's just a 350mhz box with a 4gig hdd and only 256meg of ram, but it runs win2000 no problem.

i installed the connect player on the windows box and samba on the linux box.

i was able to upload 20+ gig of mp3's via a shared folder and updated my sony walkman hdd with it.

i have also been playing with qemu.  i was able to get linux to host the mp3's from the emulated windows in qemu as well as load the connect player, but the major hurdle i've been having a hard time with has been usb support in the emulated windows.

fat lot of good it does me if i can't get the emulation to even see the player. but i soldier on.

---

