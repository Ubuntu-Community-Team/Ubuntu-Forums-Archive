---
title: "bluetooth problems after kernel upgrade maverick 10.10"
date: 2010-12-30
forum: Hardware
---

### Post by Claus7 on 2010-12-30
Hello,

after upgrading to 2.6.35-24-generic kernel, amd 64 bit for ubuntu maverick 10.10, the bluetooth system stopped working. Has anyone else featured such problem? 

With the previous kernel, bluetooth was working like a charm... 

Things tested:

hcitool scan
sudo hciconfig hci0 inqmode 0
sudo rmmod btusb && sudo modprobe btusb reset=1
hciconfig -a
hidd --search
sudo hciconfig hci0 up
sudo bluetoothd -u
sudo hciconfig hci0 reset

unfortunately nothing of these seems to work...

edit: think is a bug of the new kernel, pity cause it is really fast on booting and seems to behave really good.
just to say that this happens on ubuntu and not on lubuntu, that I accidentally chose...

Any ideas welcome,
regards!

---

### Post by Claus7 on 2011-01-22
Hello,

I installed manually, one by one the packages from here (watch out the row, as one of them is dependent on another one):
[https://launchpad.net/~brian-rogers/+archive/ppa/+buildjob/2136398](https://launchpad.net/~brian-rogers/+archive/ppa/+buildjob/2136398)

following the link found here:
[http://ubuntuforums.org/showthread.php?t=1647637&highlight=bluetooth](http://ubuntuforums.org/showthread.php?t=1647637&highlight=bluetooth)

I restarted, made my device available, and now is working like a charm once again.

Regards!

PS: This was done on ubuntu maverick 10.10 and not on lubuntu, as I accidentally chose, while creating this thread.

---

### Post by Claus7 on 2011-10-09
Hello,

also, I would like to add, that sometimes the contact the adapter has with the usb port, might not be the best, so taking it out and re-plugging it might solve some serious problems.

My adapter's light should be blinking in order for ubuntu to recognise it. I was typing:
lsusb

and the command output resulted in one blinking of the device, and then off again, and the output in the command line was somehow delayed. My device stopped being recognised. By moving the usb adapter a little, the blinking was continuous and the output of the command was quick, while showing my usb adapter's name:
Integrated System Solution Corp. Bluetooth Device

and the icon of bluetooth in the top panel reappeared with all my settings intact.

Regards!

---

