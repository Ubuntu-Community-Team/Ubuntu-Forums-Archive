---
title: "ASUS 1008P SHMConfig disabled. Please Help!"
date: 2010-03-16
forum: Hardware
---

### Post by cmagrath82 on 2010-03-16
Hi, 

I have installed eeebuntu 4.0 on my Asus 1008P and everything works out of the box. However, I cannot get two finger scrolling to work. I have tried setting up a 11-synaptics.fdi file with the settings for two finger scrolling but the problem is that it does not seem to be read. Everytime I do

synclient -m 100

it tells me that SHMConfig is disabled. I just don't seem to be able to enable SHMconfig via the hal .fdi file. Does anyone have any ideas on what I should be editing since it is obvious the /etc/hal/fdi/policy/x11-synaptics.fdi file is not read.

I also installed gSynaptics. On the GUI I select two finger scrolling but it doesn't do anything.

Any help would be much appreciated.

Thanks!:D

---

### Post by gordintoronto on 2010-03-16
This might contain your solution:
[http://pages.cpsc.ucalgary.ca/~jnjackin/docs/two_finger_scrolling-linux.html](http://pages.cpsc.ucalgary.ca/~jnjackin/docs/two_finger_scrolling-linux.html)

---

### Post by cmagrath82 on 2010-03-18
Tried that link but it still doesn't fix the problem. :(

---

### Post by jrssystemsnet on 2010-03-18
Try my how-to for Dell Mini 10v netbooks: [http://ubuntuwiki.net/index.php/Dell_Mini_10v](http://ubuntuwiki.net/index.php/Dell_Mini_10v)

Obviously you don't need the part about deadening the button area of the touchpad, but the part about enabling SHMConfig should be the same for your eee as for the Mini 10v.

And please note that the instructions are a little different depending on whether you're using Jaunty or Karmic. :)

---

### Post by nashjc on 2010-03-22
I've been trying for a couple of hours to enable SHMConfig.

None of many .fdi file suggestions seems to work. Looks like someone has got a master override somewhere. I'm running 9.10 64 bit on an Asus UL30A.

Really want to turn off this jumpy touchpad!

JN

---

