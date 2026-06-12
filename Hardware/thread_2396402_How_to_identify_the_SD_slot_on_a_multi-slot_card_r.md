---
title: "How to identify the SD slot on a multi-slot card reader??"
date: 2018-07-15
forum: Hardware
---

### Post by dazz100 on 2018-07-15
Hi
I have a requirement to write images to lots of SD cards.  To do this I have purchased three Bytecc U3-450 4-slot SD card readers.
I can use Etcher (Windows) or dd (Ubuntu)  to write to the cards simultaneously.  That all works.

The problem I have struck is that if a SD card is faulty, I can't tell what slot the faulty card is located in.
I need some way of figuring out which physical slot is associated with the drive letter allocated by the OS.

How would I begin to do that?  

Dazz

---

### Post by sudodus on 2018-07-15
if you plug in one of the card readers, and plug in an SD card, so that it will be seen as a mass storage device, you know which one it is, and can run some commands to identify it.

The following command works for me.
```

$ ls -l /dev/disk/by-id|grep usb
lrwxrwxrwx 1 root root  9 jul 15 16:16 usb-Generic-_Compact_Flash_058F63616476-0:0 -> ../../sdc
lrwxrwxrwx 1 root root  9 jul 15 16:22 usb-Multiple_Flash_Reader_058F63616476-0:1 -> ../../sdd
lrwxrwxrwx 1 root root 10 jul 15 16:22 usb-Multiple_Flash_Reader_058F63616476-0:1-part1 -> ../../sdd1
lrwxrwxrwx 1 root root 10 jul 15 16:22 usb-Multiple_Flash_Reader_058F63616476-0:1-part2 -> ../../sdd2

```

Now, if you are lucky, the manufacturer has created different id strings '058F63616476' for the three adapters, and you can stick a paper label on each of them with its ID string.

Otherwise you must keep track on the adapters, while they are connected, maybe put a temporary paper label (PostIT) with the device letter.

So after the first one is identified, connect the second one, identify it, put a paper label, and then do the same with the third one.

---

### Post by dazz100 on 2018-07-16
Hi
Thanks for that. 
The only problem I now have is that Etcher doesn't say (but must know) which slot has the faulty SD card.

I have posted [here ]("https://forums.resin.io/t/etcher-can-burn-a-single-image-to-multiple-sd-writers-but-if-a-card-fails-it-doesnt-say-which-slot-the-card-is-in/3528")but got no response yet.

---

### Post by sudodus on 2018-07-16
Maybe you can use another tool than Etcher to write the images. I guess that you are cloning. Usually I discourage people to use **dd**, and recommend mkusb, gnome-disks or usb-creator-gtk.

But maybe in your special case you can create a bash shellscript using dd in combination with some other commands in order to identify faulty cards.

How do you know, that a card is faulty? What commands are you using? What command line tools would 'see' it in a corresponding way?

---

### Post by dazz100 on 2018-07-16
Hi
A dd script is the way I am heading.  I am cloning.

Etcher says at the end after verification if any cards have failed, but only gives a count.  This is fine if you are only writing 1 card but I want to write up to 12 cards at a time.
If I insert a single failed card, it shows the hardware slot ID, not the /dev/sd? mapping.  I can move the failed card along the slots and it identifies each one.   So I know that Etcher knows exactly which card has failed.  It is just keeping it a secret.

I would much prefer to use an off-the-shelf solution but if one doesn't exist, I will cut my own.

---

### Post by sudodus on 2018-07-16
I understand that you have a few failed and several good SD cards.

Maybe you can do something like this to develop a good shellscript:

Let the shellscript

- identify the physical location of the SD cards and the device allocated, /dev/sdx,

- clone with dd, and check if it is successful or fails and let the script report it.

Then check how to make it possible to run several tasks at the same time within the same script or by starting several tasks by starting several processes running the script, for example

```

script /dev/sdc
script /dev/sdd
script /dev/sde
...

```

---

### Post by dazz100 on 2018-07-19
Hi
I am planning to start with a script like pishrink or piclone and convert that to my application.
At least I wouldn't have to start with a blank screen.

dazz

---

