---
title: "Pairing bluetooth headphones"
date: 2008-09-12
forum: Hardware
---

### Post by mash-bb on 2008-09-12
Hi!

I have trouble pairing my bluetooth headphones.

When I do sudo hcitool cc MA:CA:DR:ES:HE:RE; sudo hcitool auth MA:CA:DR:ES:HE:RE computer creates connection to my headphones and prompts for pin. However, after two seconds connection automatically terminates, and pin prompt disappears, and since I can't enter the pin in two seconds I am not able to pair headphones this way. My computer does this to all bluetooth machines so I can't pair any of them in this way.

Another way of pairing for me is graphically trough Gnome bluetooth utiles. However, I haven't found a dialog that would just pair the device. Bluetooth utiles pairs devices when I first try to use them, but only service that the graphical users interface seams to contain is obex-server, which my headphones don't have. So if I right click the bluetooth icon and try to pair device by using "browse device" bluetooth utiless just gives error message saying that the headphone device doesn't appear to have obex-service.

Still another way of pairing might be (of this I am not so sure of) to use btsco and see, if I'm prompted for pin then. This doesn't work either, because btsco MA:CA:DR:ES:HE:RE CHno returns: Error: control open (hw:1): No such file or directory; Error: Can't find device. Bail

I know that my bluetooth system works because I can use the OBX and PPP services over it with other devices. My bluetooth system should support multiple connections, but even if I don't have any active connections, the pairing doesn't work.
Any ideas?

At this point I'm not that interested in learning what is wrong with my btsco (I would prefer to use bluetooth-alsa anyway). Primarily I would like to know why do my bluetooth connections terminate after few seconds if I use hcitools to create them, and secondarily, if there are some other ways to pair devices besides hcitool auth. 

I'm running ubuntu 8 on laptop with usb bluetooth dongle. And my Headphones are Philips SHB7100


EDIT:
For some strange reason, right after I wrote this the headphones spontaneously wanted to initiate pairing with my computer and thus I was able to pair them. After pairing the headphones started working (I tested with skype) but the microphone build into them won't work.

---

