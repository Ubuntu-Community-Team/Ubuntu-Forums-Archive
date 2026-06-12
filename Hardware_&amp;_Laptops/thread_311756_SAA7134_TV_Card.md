---
title: "SAA7134 TV Card"
date: 2006-12-03
forum: Hardware &amp; Laptops
---

### Post by Schnoid on 2006-12-03
Hey,

Have a SAA7134 TV card, just put it into my machine.

It's coming up in the device database as being installed OK, but, I'm having trouble getting it to work.  I've tried using Kdetv and Tvtime but neither of them seem to be able to use the card.

Any ideas?  I'm on Ubuntu Dapper AMD64.

Cheers.

Schnoid.

---

### Post by josesanders on 2006-12-04
There are a lot of saa7134 cards out there, so I can't guarantee that what I did will work, but if you are having the same problem that I had, you can try this:

$ dmesg

This will output any messages that were logged by the OS on bootup.  Since there are so many saa7134 cards, the OS needs to know which one you have, which can normally be detected automatically, but for some cheap cards, it can't be determined and you have to select the number yourself.  If your card is not recognized, then when you run dmesg, you will see an error about how it can't determine the card number, and it will give you a list of almost a hundred manufacturers and the respective card numbers.  If you can find the card number in the list, then edit the file /etc/modprobe.d/options by adding the following line, and then reboot:

Options saa7134 card=<card number>

If you can't find the card number on the list, as was the case for me, then you can just try some until you get one that works.  For my generic card, about a third of them worked for video, but only one worked for sound in TVTime, and I still can't get sound in MythTV.

To load the module without having to reboot, first locate the saa7134 module:

$ sudo updatedb
$ locate saa7134.ko

Go to that directory and execute the following:
$ sudo rmmod saa7134-alsa
$ sudo rmmod saa7134
$ sudo insmod saa7134.ko card=<card number>
$ sudo insmod saa7134-alsa.ko

Then open TVTime and see if you have video.  For me, it defaults to Composite input, so if you see a black screen, try switching from the Composite input to the Television input.

---

### Post by Mets on 2007-02-12
when I try the sudo insmod command, I get the following error:

insmod: error inserting 'saa7134.ko': -1 Invalid module format

I am in the directory, and I can see the file with ls.  What am I doing wrong?

---

### Post by larpon on 2007-02-12
try with just 'saa7134' (no .ko extension) and see if that helps? :)

try the same with the *-alsa module if you have the same problem there :)

---

### Post by daemmon on 2007-02-21
thanks josesanders! i was having the same problem, and now it works! one question though, is there any way to make it automatically choose the specific card at every boot? i hate having to type those lines every time i log in

---

### Post by josesanders on 2007-02-22
As I said in my first reply on this thread:

> ...If you can find the card number in the list, then edit the file /etc/modprobe.d/options by adding the following line, and then reboot:

Options saa7134 card=<card number>

---

### Post by the_mouse on 2007-04-02
I did all you said but when the tvtime-scanner starts it goes throught the frequences, but it says "No signal", and when I run TVtime I only see the same message on black/blue screen :( I'm having a Chronos Video Shuttle 2 and running Kubuntu Dapper
Is there any difference if I try modprobe saa7134, because if I haven't tried your mothods and just run 
sudo modprobe saa7134 card=3 
I get:
FATAL: Error inserting saa7134 (/lib/modules/2.6.15-27-386/kernel/drivers/media/video/saa7134/saa7134.ko): Unknown symbol in module, or unknown parameter (see dmesg)
FATAL: Error running install command for saa7134

---

