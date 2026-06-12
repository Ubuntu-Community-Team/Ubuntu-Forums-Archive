---
title: "FireWire card not found - worked in Dapper"
date: 2007-06-08
forum: Hardware &amp; Laptops
---

### Post by DFreeze on 2007-06-08
I've just bought a DV camcorder and thought I'd play with it for a while. But no play, since Kino gives the error

"WARNING dv1394 kernel module not loaded or failure to read/write to /dev/dv1394/0" 

I've followed some threads here on how to check if the modules are loaded, and all, but it turns out that my IEEE 1394 PCI card isn't even detected. lspci | grep 1394 gives me nothing.

How can this be. I thought IEEE 1394 was such a straightforward standard. It worked in Dapper (I skipped Edgy), but in Feisty it's gone again. Can anyone help me get it going?

::EDIT::

I've read through countless threads, including [this one]("http://http://ubuntuforums.org/showthread.php?t=454698&highlight=dv1394+camera"), and nothing seems to work. From the bash script /etc/init.d/firewire to changing the permissions, to switching to raw1394 or video1394 or back to /dev/dv1394/0. Nothing. Still the warning. Also when I load Kino as root, it doesn't fly. Pff, when the automagical detect doesn't work, it's such a pain to get things working...

---

### Post by DFreeze on 2007-06-10
So I've downloaded PCLinuxOS, just to see if the Kino thing is going well over there. Alas, also there I get the WARNING, cannot read/write to /dev/raw1394. Also after a modprobe and a chmod 777... Am I the only one having these problems? How hard can it be to get this right? Of all the hardware I have tested Ubuntu on, FireWire I would expect to work OOTB...

---

### Post by DFreeze on 2007-06-11
So now my last hope, adding myself to the 'disk' and 'video' group, and then trying if Kino worked, again resulted in the same warning. Why is this so hard! I've scoured through dozens of forumthreads, anywhere on the internet, and a lot of people seem to have trouble grabbing DV video. How come there's no straightforward fix for it?

---

### Post by DFreeze on 2007-06-12
Just today I had a hunch: my Motherboard has some FireWire connectors as well (Asus A7N8X Deluxe) so maybe the ieee1394 devices found are the onboard ones. Then it would make sense that I can never get Kino going. But can I discover from lspci which one is recognized? 
```

01:08.0 FireWire (IEEE 1394): Unknown device 0103:8210

```

Some help would be appreciated.

---

### Post by DFreeze on 2007-06-12
Mind you, I'm not always talking to myself ;-)

I've pulled the PCI FireWire card, but in my BIOS I already saw that it couldn't be my onboard 1394 connectors being seen. They were disabled in the BIOS. But I had already started the experiment, so I went on and enabled the 1394 connectors and started Ubuntu. This time lspci | grep 1394 showed the nVidia connectors all right, identified and all. But unfortunately I don't have the connectors to use the onboard FireWire. So I disabled them again, put the PCI card in yet another slot and booted again. This time lspci showed the card and identified it correctly. So I immediately fired up Kino and tried again ... AND IT WORKS!

So, despite noone chiming in, the problem is solved and documented here for anyone struggling with FireWire.

---

### Post by tgalati4 on 2007-06-12
Linux is not plug and play so it has to make guesses as to interrupt and I/O port addresses.  Sometimes it guesses wrong and the I'm sure the hardware detection algorithm has undergone extensive changes in the latest kernel.

Simply changing the card slot would force a different allocation of resources.  Sometimes turning off USB and serial/parallel ports (temporarily) will free up interrupts and ports so that your cards will be detected.

The alternative is to manually designate the resources in your BIOS, so the kernel won't have to guess.  It's not perfect, but it generally works 95% of the time.

---

### Post by shonisan on 2008-01-05
> **tgalati4 said:**
> Linux is not plug and play so it has to make guesses as to interrupt and I/O port addresses.  Sometimes it guesses wrong and the I'm sure the hardware detection algorithm has undergone extensive changes in the latest kernel.

Simply changing the card slot would force a different allocation of resources.  Sometimes turning off USB and serial/parallel ports (temporarily) will free up interrupts and ports so that your cards will be detected.

The alternative is to manually designate the resources in your BIOS, so the kernel won't have to guess.  It's not perfect, but it generally works 95% of the time.AND ... and I hate to say this ... this is why the rest of the world sees Linux as 'not ready for prime time'.:(

---

