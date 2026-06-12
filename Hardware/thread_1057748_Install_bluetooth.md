---
title: "Install bluetooth"
date: 2009-02-02
forum: Hardware
---

### Post by eternalnewbee on 2009-02-02
Hi there.
Just installed Ubuntu 8.10 on my friend's Toshiba laptop, but the Bluetooth Device Wizard doesn't detect his Nokia mobile phone. It's a dual boot, and when using windows he can use Bluetooth. I don't know how else to describe this issue, as I myself have no experience with it. What can I do? Hope someone can help. 
Thanks.:)

---

### Post by Ice Man on 2009-02-02
This is the Toshiba guy he's talking about...

What it is I have a built in Blue Tooth in the Lap top but after installing Ubuntu to my laptop I can't set up the blue tooth to pair with my Nokia phone...
I use the phone as my internet.

Also at my office I use the wireless system and the printer I use works off the wireless something else I can't set up at the moment with Ubuntu...

Any help would be great thanks....

---

### Post by eternalnewbee on 2009-02-02
> **Ice Man said:**
> This is the Toshiba guy he's talking about...

What it is I have a built in Blue Tooth in the Lap top but after installing Ubuntu to my laptop I can't set up the blue tooth to pair with my Nokia phone...
I use the phone as my internet.

Also at my office I use the wireless system and the printer I use works off the wireless something else I can't set up at the moment with Ubuntu...

Any help would be great thanks....

Sure someone will reply, Iceman. I have no experience with either Blue Tooth & printing . . .

---

### Post by Ice Man on 2009-02-03
Well still can't get it to pair with my phone, when I click in the Blue Tooth Icon and it takes me to the Blue Tooth Device Wizard I hit the forward button which then goes to Select the device you want to set up But that's it nothing happens?????

Help guys.....

---

### Post by kimberlite on 2009-02-03
Hello, I have also a Toshiba A300 and a non-working built-in bluetooth device. I found this post, that can be interesting for you:

[http://ubuntuforums.org/showthread.php?t=316358](http://ubuntuforums.org/showthread.php?t=316358)

I have not tried it yet, because the recommended solution is based on a project which is no longer maintained.

---

### Post by gackt on 2009-02-03
here is what i do with my lenovo laptop

1. turn on the bluetooth in my laptop
2. turn on the bluetooth in my mobile
3. add device (do it with mobile phone)
4. give the passkey (you define it your self)
5. installing and bla bla
6. $ hcitool scan in terminal (record the address for example 00:1C:A9:4D:39:7E K700)
7.$ sudo gedit /etc/wvdial.conf (make new section with configuration of your phone and provider)
8.$ sdptool search DUN (record the channel number, in my case is 1)
9.$ sudo gedit /etc/bluetooth/rfcomm.conf (replace the macc address and channel with yours)
10. $ sudo rfcomm bind 0 "your address" "channel number" ( sudo rfcomm bind 1 00:0F:DE:49:94:D0 1 for example)
11. $ su
12. $ wvdial "your setting name, refer to wvdial.conf. Example wvdial orange3"

i'm sorry if this is not newbie friendly, play around with it. Ask me if you need further assistance.

---

### Post by eternalnewbee on 2009-02-03
Thanks Kimberlite. Thanks Gackt. Busy right now, but will get on it ASAP.
In the meantime any other suggestions are welcome. ;)

---

### Post by ajmctaggart on 2009-02-03
You said it works in Windows, do you still have Windows installed on that machine?  

If so, go into Windows, turn on the Bluetooth in there, scan, etc...

Do NOT Turn off the Bluetooth and then go back into Ubuntu...

I've had this type of problem with peripherals in the past, if you've still got Windows it's worth a shot...

---

### Post by Ice Man on 2009-02-03
Still can't get it to do anything in the Blue Tooth Wizard in ubuntu, it just goes to the first stage and then nothing, it doesn't do anything therefor I can't pair my Mobile with it..

The thing that [ajmctaggart]("http://ubuntuforums.org/member.php?u=234442") said didn't work as I have to re start the laptop to go into ubuntu...

---

### Post by ajmctaggart on 2009-02-03
So it is still working in Windows fine?  And there's no hardware switch or anything for the bluetooth?  

On my mac, after switching between so many OS's my bluetooth didn't work till I did a hard power reset on my machine.

Is there an equivalent for your machine?
 
That's what I was getting at with the "Check in Windows..."

---

### Post by eternalnewbee on 2009-02-05
bump

---

