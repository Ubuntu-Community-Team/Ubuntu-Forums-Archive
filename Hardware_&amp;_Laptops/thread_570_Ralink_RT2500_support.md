---
title: "Ralink RT2500 support"
date: 2004-10-14
forum: Hardware &amp; Laptops
---

### Post by Guzeem on 2004-10-14
it would be nice if ubuntu had native support for this wifi card or an installable upgrade...

But now it's in there, i can see it in the hardware, but can't use it ...

---

### Post by pep-e on 2004-10-30
Read this: [http://61.222.76.235/phpbb2/viewtopic.php?t=165](http://61.222.76.235/phpbb2/viewtopic.php?t=165)
I'm on it now. Good luck!

---

### Post by Julian Bischof on 2006-12-30
hi, guys

i am totally new here and i ve a bad bad problem.... which is basicly the same as told before. but the link doesn't work anymore. when anyone know how i could solve this problem, i would be very happy to hear it.

thx

julian

---

### Post by mojoman on 2006-12-30
What exactly is the problem? I use a card with this chip for my Ubuntu server and it worked out of the box. Also, I used to run my laptop on both ubuntu and xubuntu, also with a card with this chip. It also worked out of the box. This was both with breezy and dapper but I haven't tested with edgy or feisty.

Post your output from ifconfig

/Mojoman

---

### Post by patrickfromspain on 2006-12-30
Using a raling rt2500 based card and no problems.. worked out of the box... Are you sure it's and rt2500?

---

### Post by damagedspline on 2006-12-30
this might be the annoying "led" hardware design...

if it works, well, congratulations.
make sure you have restricted-generic installed (check in synaptic) and works on i386 ubuntu install (wasn't tested on 64bit ubuntu)


```
sudo modprobe acerhk
echo 0 > /proc/driver/acerhk/wirelessled 
echo 1 > /proc/driver/acerhk/wirelessled
```

 now try login to a wireless network.

if it works, you can make it permanent - to be automatically performed on each restart/resume.

---

