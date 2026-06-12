---
title: "uswsusp and beryl"
date: 2007-05-18
forum: Hardware &amp; Laptops
---

### Post by hughes28105 on 2007-05-18
Hay  has anyone out there ever got uswsusp and beryl work with suspend or hibernation. i have tryed for weaks to suspend or hibernate properly with uswsusp while using beryl. it suspend works but when it resume the screen remains blank and stalls until i do a reboot. :confused::(:mad:

---

### Post by daspecster on 2007-05-18
I have this same problem on a Dell e1405

Specs:
video: Intel 945GM i810 drivers
Bios A10...latest as of 4/11

Ubuntu 7 final
Beryl

I put the laptop into suspend either by closing the lid or through shutdown options.
And I go to bring it back...and it's just a blank screen. 
I can cycle through the tty's but after a bit those don't work either.
and then the screen goes completely blank but with the power LED still on.
Nothing I do brings it back.

Any help on this would be great I've tried about everything on this forum and google.

---

### Post by hughes28105 on 2007-05-18
I am still trying everything i can to get this to work even a script i found but they still don't work i wondering if i did them wrong or not. give the instruction in this link a try and tell me if it works for you. here the link
[http://ubuntuforums.org/showthread.php?p=2568654]("http://ubuntuforums.org/showthread.php?p=2568654")

---

### Post by hughes28105 on 2007-05-19
Now i have bean trying to recompile my kernel with suspend2. I still wondering how you get suspend2 to work with initrd or initramfs. any suggestions.

---

### Post by daspecster on 2007-05-19
I tried the USR2 fix..and that didn't change anything.
The laptop appears to go into suspend however it cannot be resumed or woken up.
Is there a log that I can view to see if ubuntu is acknowledging the lid switch once it's opened?

---

### Post by hughes28105 on 2007-05-20
I am not sure if there is a way to log the lid closing but try and google it and see if there is. and suspend2 still trying to get it to work

---

### Post by reacocard on 2007-05-20
Trevino has compiled suspend2 kernels for feisty: [http://3v1n0.tuxfamily.org/dists/feisty/suspend2/index.html](http://3v1n0.tuxfamily.org/dists/feisty/suspend2/index.html)

To use them, add this your /etc/apt/sources.list
```
deb http://download.tuxfamily.org/3v1deb feisty suspend2
deb-src http://download.tuxfamily.org/3v1deb feisty suspend2
```
Save & exit, then from a terminal do
```
wget http://download.tuxfamily.org/3v1deb/DD800CD9.gpg
sudo apt-key add DD800CD9.gpg
sudo apt-get update
sudo apt-get upgrade
sudo apt-get install suspend2
```

Now, edit your /boot/grub/menu.lst and change
```
# defoptions=quiet splash
```
to
```
# defoptions=quiet splash resume2=swap:/dev/sdYX
```
replacing /dev/sdYX with your swap partition, and also add 'noresume2' to the end of the line that starts like this:
```
# altoptions=(recovery mode)
```

Now reboot. Hibernation should be handled by suspend2 instead of swsusp. I've been using suspend2 with beryl for quite a while now, and it works beautifully.

Post any problems you have with these packages in Trevino's suspend2 thread ( I know it says edgy, but it's for feisty too): [http://ubuntuforums.org/showthread.php?t=284994](http://ubuntuforums.org/showthread.php?t=284994)

---

