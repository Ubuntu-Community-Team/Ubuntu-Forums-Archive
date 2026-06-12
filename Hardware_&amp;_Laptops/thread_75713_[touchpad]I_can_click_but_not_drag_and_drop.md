---
title: "[touchpad]I can click but not drag and drop"
date: 2005-10-14
forum: Hardware &amp; Laptops
---

### Post by szdavid on 2005-10-14
Hello,

I upgraded from hoary to breezy last night ; a lot of things works (great !) but i have got a problem with my touchpad :

I can click and double click without any problem but I cant drag'n drop...

My computer is a sony vaio VGN-A215M

Thanks for your help

---

### Post by John.Michael.Kane on 2005-10-14
Try this sudo sh -c "echo options psmouse proto=exps > /etc/modprobe.d/psmouse.modprobe"  

You must reboot after.

---

### Post by szdavid on 2005-10-14
And what about 
```
sudo dpkg-reconfigure xorg-driver-synaptics
```

---

### Post by John.Michael.Kane on 2005-10-14
all need to do is type the code i posted ,and reboot the machine and all should be fine..

---

### Post by UrbanFox on 2005-10-16
I had the same problem and your solution worked, szdavid. Thanks. Does this autodetect on a fresh install? If it doesn't it should probably be submitted as a bug.

---

### Post by GoodPanos on 2005-10-16
[QUOTE=szdavid]And what about 
```
sudo dpkg-reconfigure xorg-driver-synaptics
```[/QUOTE]
Indeed!!?? What about this code?  Can someone elaborate?:confused:

---

### Post by UrbanFox on 2005-10-16
[QUOTE=GoodPanos]Indeed!!?? What about this code?  Can someone elaborate?:confused:[/QUOTE]

My apologies, I meant SD-Plissken's solution worked. Szdavid's solution (the  ```
sudo dpkg-reconfigure xorg-driver-synaptics
```) was for those who use synaptic touchpads, which the Sony Vaio's (at least my particular model's) is not (to the best of my knowledge.)

Incidentally, if you want to use SD-Plissken's solution without rebooting, run the command he mentions, and then:```
sudo rmmod psmouse; sudo modprobe psmouse proto=exps
``` And then it should work. Be warned that the initial rmmod psmouse will disable your mouse momentarily, but it is necessary to change the parameters with which the mouse driver runs.

---

### Post by GoodPanos on 2005-10-16
That [QUOTE=SD-Plissken]sudo sh -c "echo options psmouse proto=exps > /etc/modprobe.d/psmouse.modprobe"[/QUOTE] just makes your touchpad work.  It doesn't do anything about the scrolling.

---

### Post by lhtown on 2005-10-20
[QUOTE=SD-Plissken]Try this sudo sh -c "echo options psmouse proto=exps > /etc/modprobe.d/psmouse.modprobe"  

You must reboot after.[/QUOTE]

Thanks. I can now drag and drop.

Acer TravelMate 290

For a similar thread see [http://ubuntuforums.org/showthread.php?t=75094&highlight=breezy+touchpad]("http://ubuntuforums.org/showthread.php?t=75094&highlight=breezy+touchpad")

---

### Post by Starman on 2005-10-22
Dell Latitude D400
Alps Touchpad.

sudo sh -c "echo options psmouse proto=exps > /etc/modprobe.d/psmouse.modprobe"

works to get the tap and double tap working properly after reboot but when I close the lid and sleep the system upon waking the tap and double tap no longer work. Have to reboot to get them working.

Anyone know what file(s) need to be touched to get the tap functionality back after wake up?

thanks...

---

### Post by Starman on 2005-10-28
refreshing this thread to the top

still no answer for drag & drop after coming out of sleep...

---

### Post by 23meg on 2005-10-28
I got mine working by inserting 
```
        Option "GuestMouseOff" "0"
```
to the InputDevice section of my ALPS.

---

### Post by Starman on 2005-10-29
I tried that but it didn't help. My problem is only after waking by opening the lid. Then I lose all tap functionality, single, double, the whole 9 yards.

From the time I boot until the first sleep, tap and double tap work fine. After waking up the first time; nothing...

---

### Post by Sethherd on 2006-10-10
I hope no one's still following this, but just in case, the fix this thread centered on 
was a dead end for me- it breaks scrolling and adjustable speeds by using a mouse driver instead of a touchpad driver.  Instead see

[http://gentoo-wiki.com/HARDWARE_Synaptics_Touchpad](http://gentoo-wiki.com/HARDWARE_Synaptics_Touchpad)

since the new kernel and driver are so much better, fixes aren't necessary.

Also bear in mind as I did not that tap to drag depends on you starting the dragging gesture quickly; setting the maxtaptime higher can help (use synclient or k g or qsynaptics once you have Option "SHMConfig" = "true" in the touchpad section of your xorg.conf file)

---

### Post by kutta on 2008-03-22
Thousand thanks to you.That without reboot code worked.

---

