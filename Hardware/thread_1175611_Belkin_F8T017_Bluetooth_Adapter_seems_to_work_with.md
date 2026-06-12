---
title: "Belkin F8T017 Bluetooth Adapter seems to work with Jaunty, but not. :S"
date: 2009-06-01
forum: Hardware
---

### Post by masterpingvin on 2009-06-01
Hi!

I have a Belkin F8T017 Bluetooth Adapter. When i connect it to the USB hub, Jaunty realise it, and push the blue icon on the bar.
Then everything looks good, but....

When i start searching for bluetotth devices the list is red, and Adapter led does not blink.

So Jaunty not find any device. If I scan in terminal it says "connection timed out".

So Adapter looks working, led is on, but cant search and connect.

So can somebody help me?

Masterpingvin.

---

### Post by OpenFish on 2009-06-08
**BUMP**

i saw a load of belkin stuff with ubuntu suport so i went and got a belkin bluetooth dongle

i when for the 'F8T017' too and have exacly the same problem!

when puged in the gnome bluetooth aplet fires up and lets u change some settings but cant see any other devices

tryed to use hcitools but that just says every thing is fine and then cant find anything when i try to pair it up 

[PHP]will@ubuntu:~$ hcitool scan
Scanning ...
Inquiry failed: Connection timed out
[/PHP]

in windows xp the suplided drivers work a treat and bluetooth can pair.. i think they added some furmware 2 but the dongle still dosnt work in ubuntu plus i now have even more useless drivers on my windows box.. slowing it down even more.. for me 2 clean up :(

btw windows thinks that it is made by broadcom and that the chip is called BCM2046.. i googled this and got more unhappy ubuntu fans and broadcom says that the seller/maker of the finshed hardwear should deal with drivers

any help greatly apriciated

will

---

### Post by OpenFish on 2009-06-10
got it at last...

[http://ubuntuforums.org/showthread.php?t=446422](http://ubuntuforums.org/showthread.php?t=446422)

dont worry about all the coments just follow the first post i know it says about dells but they use exacly the same bluetooth chip from broadcom

mine is workin now


a very happy
will

---

