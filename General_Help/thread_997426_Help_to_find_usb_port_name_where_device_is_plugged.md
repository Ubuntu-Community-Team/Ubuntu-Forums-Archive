---
title: "Help to find usb port name where device is plugged"
date: 2008-11-29
forum: General Help
---

### Post by ndefontenay on 2008-11-29
Hi,

I've got a cellphone connected to a USB port and I want to try the different sync / phone management available in the repository.

Quite surprisingly, they all ask me about my port name... Like I would know.
The program should tell me!

Anyway... Is there a way to find out which port has a device connected to it?
I've tried lshw but all I get is the type of hardware it is.

lspci | grep USB returns a list of USB device but not their names neither if there's anything (even unknown) connected to it.

Anybody has ever tried that?

thanks,

Nico

---

### Post by marshall.robert on 2008-11-29
how about lsusb?

---

### Post by ndefontenay on 2008-11-29
Yes that seems to work for the device plugged. I can see my samsung phone connected. But I still have no idea where it plugs. It tells me USB 6 but I think I need a name in the form of /dev/usb1 (or something like that)

---

### Post by soro2005 on 2008-11-29
As far as I am concerned, this depends on which driver/kernel module claims the device. A good candidate for a cellphone on USB seems to be /dev/ttyACM0 or something similar.

You could try to catch it as it happens: Plug in the cellphone while you read the system messages, for instances with
```
tail -f /var/log/messages
```

---

### Post by ndefontenay on 2008-11-29
It was indeed ttyACM0!!!

I did something though. I removed the phone from the front of my PC and switched it to a port on the rear.
Then I could see it in the list which was previously empty :)

Thanks a bunch mate

---

