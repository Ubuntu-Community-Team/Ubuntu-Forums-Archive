---
title: "Soundgraph iMON 2.4G LT install"
date: 2008-03-20
forum: Hardware &amp; Laptops
---

### Post by WaverSwe on 2008-03-20
Hi!

I have the iMON 2.4G LT remote. I know it's an rf control.
Have anyone get it to work?
i've googled like crazy try to find, there are some clues, but haven't get it to work.

I would be happy if someone would help me.

lsusb finds the device

lsusb | grep iMON
Bus 002 Device 002: ID 15c2:ffdc SoundGraph Inc. iMON PAD Remote Controller

need help really bad

---

### Post by dimxfullv2 on 2008-05-13
i have the same device and i experience the exact same problem, my ubuntu recognize the device in

Bus 001 Device 004: ID 15c2:ffdc SoundGraph Inc. iMON PAD Remote Controller

i tested lirc ,imon patch but i can't do anything ,the only thing i've got is
hello msg after 

```
echo "Hello" > /dev/lcd0 
```

in LCD and in remote part with 

```
sudo mode2 -d /dev/lirc0 
```

i saw the code of buttons 
```

code: 0x68c281b7
code: 0x28b755b7
code: 0x6902f9b7
code: 0x6902f9b7
code: 0x6902b9b7
code: 0x6902b9b7
...
...

```
but nothing happens with totem or other programs
Please Help us!!!!!! :P

---

