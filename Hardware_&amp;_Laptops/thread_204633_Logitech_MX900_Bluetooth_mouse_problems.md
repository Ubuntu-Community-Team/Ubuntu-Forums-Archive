---
title: "Logitech MX900 Bluetooth mouse problems"
date: 2006-06-27
forum: Hardware &amp; Laptops
---

### Post by bertd on 2006-06-27
Hi,

I installed Ubuntu a few days ago and I'm getting the hang of it. However, there's something that I still can't quite put my finger on:

When I've just booted up Ubuntu, the bluetooth dongle / mouse cradle seems to be stuck. I can't push the button to reconnect, hence it doesn't recognize the mouse either and I can't do anything. The strange thing is, when I pull out the dongle/cradle from the usb port, and plug it back in, it works like it should work again...

Anybody have any idea how I could fix this? It's probably not a hardware failure, since it works perfectly on XP SP2.:-?

---

### Post by Underscore on 2006-07-26
It happens the same with my mx900. IThe only way to solve it is to remove the bluetooth utils...

do an "apt-get remove bluez-utils" and it should work with no problems. Problem is that as far as I know you wont be able to use the bt hub anymore (or any other bluetooth device :/). I'm still trying to find out a better way to solve this

---

### Post by maloo on 2007-10-04
Hi,

Same problem here too removing bluez-utils and kbluethooth seems to fix it thou. This seems to be a (k)ubuntu specific problem since fedora, suse, sabayon are fine. Fedora defiantly had bluez-utils installed not sure about the others. This is a bit of a drawback for ubuntu since its one of the first things you notice on first install:/. (it does work during installation and with grub however). Sorry I havent really solved anything here but here is my setup anyway:

Kubuntu 7.04, latest kernel and updates etc, diNovo keyboard, MX1000 mouse

---

