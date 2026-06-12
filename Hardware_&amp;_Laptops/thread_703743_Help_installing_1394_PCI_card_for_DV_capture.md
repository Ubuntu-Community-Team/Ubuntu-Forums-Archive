---
title: "Help installing 1394 PCI card for DV capture"
date: 2008-02-21
forum: Hardware &amp; Laptops
---

### Post by myonta on 2008-02-21
Hey all.

Here's what's up. I'm running Gutsy 64 and I need to capture from my DV camcorder (Canon ZR60--it's about 4.5 years old). My camcorder uses IEEE 1394 (aka: firewire) for I/O with computers. I don't have firewire on my mainboard so I installed a PCI adapter when I built the computer. However, until now I have not tested to see if it works.

Lo and behold, it doesn't work. My computer doesn't even know the camera is there. I'm pretty sure it's a driver issue for the adapter.

***lspci*** shows the card as follows:

```
01:0a.0 FireWire (IEEE 1394): NEC Corporation uPD72874 IEEE1394 OHCI 1.1 3-port PHY-Link Ctrlr (rev 01)
```

I'm not even sure where to start with this one.

Thanks,
~Jon

---

### Post by graham-cracker on 2008-02-21
the lspci output makes me think the pci card is working.

try plugging in the camera and then running:

dmesg

maybe that will tell you something useful (also post the last few, maybe 10 or so lines). You should see some notification that you've plugged something into the firewire port.

---

### Post by myonta on 2008-02-21
Wow... I typed ***dmesg*** and got a lot of lines output. Most of them look something like this:
```
[ 1455.736183] powernow-k8: vid trans failed, vid 0x1c, curr 0x18
[ 1455.736187] powernow-k8: transition frequency failed

```

I'm pretty good with both hardware and software (jack of all trades--master of none), but I don't really know what to do with this data. Anyway, here's the last several lines as you requested:
```
[ 6874.383187] powernow-k8: vid trans failed, vid 0x1c, curr 0x18
[ 6874.383192] powernow-k8: transition frequency failed
[ 6880.743875] atkbd.c: Unknown key released (translated set 2, code 0x81 on isa0060/serio0).
[ 6880.743880] atkbd.c: Use 'setkeycodes e001 <keycode>' to make it known.
[ 6884.627662] atkbd.c: Unknown key pressed (translated set 2, code 0xd9 on isa0060/serio0).
[ 6884.627668] atkbd.c: Use 'setkeycodes e059 <keycode>' to make it known.
[ 6898.932704] powernow-k8: vid trans failed, vid 0x1c, curr 0x18
[ 6898.932708] powernow-k8: transition frequency failed
[ 6905.326513] powernow-k8: vid trans failed, vid 0x1c, curr 0x18
[ 6905.326518] powernow-k8: transition frequency failed
[ 6906.528328] ieee1394: Current remote IRM is not 1394a-2000 compliant, resetting...
[ 6907.723697] ieee1394: Current remote IRM is not 1394a-2000 compliant, resetting...
[ 6907.814778] ieee1394: Node resumed: ID:BUS[0-00:1023]  GUID[0000850000a86b58]
[ 6907.814796] ieee1394: Node changed: 0-00:1023 -> 0-01:1023
```

Just a note: I've had this firewire adapter working with this camera *and* other devices while installed in a Windows box in the past.
I'm all for learning how to get this working, but I'm also wiling to try and hunt down an Ubuntu compatible card if necessary.
~Jon

---

### Post by myonta on 2008-02-21
**UPDATE:**

As near as I can tell from querying the hardware and peering through my cpu's case windows with a flashlight, I have an NEC 3+1 IEEE 1394 PCI Adapter.

It's here: [http://www.st-lab.com/assign.asp?keyid=bd16]("http://www.st-lab.com/assign.asp?keyid=bd16")

---

### Post by graham-cracker on 2008-02-22
I think the powernow stuff is cpu frequency scaling and (hopefully) unrelated. 
The dmesg output makes me think that the computer is seeing the camera and assigning it a 'node'.

could you post the output of:
```

ls /dev | grep 1394

```

You should (I think) get something like this:
```

raw1394
video1394

```


From a quick google, it looks like kino should work with the camera you have. Are you using that program to talk to the camera? I have never tried it before so I don't think I can help with that.

I also ran into this:
[http://lwn.net/Articles/216157/](http://lwn.net/Articles/216157/)
it looks like a script that works similar to lspci except it lists firewire devices (the output for me was garbage because I did not download the oui.db that translates the garbage into human readable stuff)
The script returned this before plugging in a firewire webcam:
```

0:ffc0 4d5a900003000000 (local)

```
and this afterwards:
```

0:ffc0 0814436102637580
0:ffc1 4d5a900003000000 (local)

```

One final thing. Could you run:
```

dmesg | grep ieee1394

```
and post that output. I'm looking for something like this:
```

ieee1394: raw1394: /dev/raw1394 device initialized

```

---

### Post by myonta on 2008-02-22
Ok, here's that output:
```
jon@red-cube:~$ ls /dev | grep 1394
dv1394
raw1394
```
Though it seems to be the same whether the camera is plugged in or not.

I played around with Kino a little. It acts as though there's nothing there. So, I went checked the 1394 settings in Kino and got this:```

**The IEEE 1394 Subsystem is not responding.**
The raw1394 module must be loaded, and you must have read and write access to /dev/raw1394.
```
So, I changed the permissions of /dev/raw1394 to Read and Write and that error went away. Then...
**Voila:** Kino can suddenly see the camera's output!

I think, then, for now I will hold on trying those commands you suggested. But I will keep playing around with it to figure out if it's working consistently.

Thank you very much, btw. 
~Jon

---

