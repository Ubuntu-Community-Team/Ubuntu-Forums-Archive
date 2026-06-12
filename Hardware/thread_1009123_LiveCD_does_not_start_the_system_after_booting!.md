---
title: "LiveCD does not start the system after booting!"
date: 2008-12-12
forum: Hardware
---

### Post by crik91 on 2008-12-12
I'm sorry for my multiple-thread.I'm Italian and I don't speak English very well...

I have this laptop: TOSHIBA Satellite A60-332(160 GB HDD, Intel Pentium 4 2800 MHz L2 Cache 512K, 704 MB RAM with shared memory to video card, ATI RadeON Mobility 7000 IGP, Lastest TOSHIBA Proprietary BIOS)

I had many problems on your laptop with Ubuntu.I decided to format and resolve them in the order they appeared.
Canonical LTD sent me the CD of Ubuntu 8.10 (Intrepid Ibex) and I have inserted in the CD.I tried several times to start the LiveCD without success hangs on the loading bar only once without adding any parameter to the command bar initiation and actually has started but when it became the pointer was blocked everything. I tried with noapic nolapic, pci=noacpi...
I started with no splash screen and I noticed that hangs on:
```
Loading, please wait...
```

Someone can help me, please?

---

### Post by DieB on 2008-12-12
if you might delete the following from the boot-line:

> quite splah

it should print a lot of message and there (if you look very concentrated) u might catch the line with error report. sometimes a short google might give the help, or posting it up here ;)

---

### Post by crik91 on 2008-12-12
I've tried but it hangs himself:
```
Loading, please wait...
```
And now I have booting with:
```
noapic nolapic
```
and without:
```
splash
```

Now instead has started. I am installing. I know after you say.

---

### Post by crik91 on 2008-12-12
Sometimes the system does not start!
When the sistem is starting I have press: ALT+F1 and boot lock there:
```
Starting up ...
Loading, please wait...
```

---

### Post by DieB on 2008-12-12
delete quite too, u will then get mor information: u can do it persistent or just once:

**_once:_** at the grub-bootloader, where u are asked to hit Esc, do so. now u should have a kind a menu with different opportunities, stay on the first of list and hit 'e' for edit, now there is a three lined list with the second starting with kernel, mark go on that and hit e.
Now delete the 'quiet' at the end.

**_persistent_** 

start a terminal (e.g. Alt+F2: gnome-terminal) and type:

sudo gedit /boot/grub/menu.list

now edit the line starting with kernel= as mentioned above.

---

### Post by crik91 on 2008-12-12
Thank you!
Now just the latest problem, the sound does not work.I hear only two drums when the screen access then ever dumb!
What should I do?
HELP!

---

