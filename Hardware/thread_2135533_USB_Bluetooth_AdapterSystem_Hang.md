---
title: "USB Bluetooth Adapter/System Hang"
date: 2013-04-14
forum: Hardware
---

### Post by stevesy on 2013-04-14
Hi guys, I've just bought a "Dynamode" Bluetooth v2.0 dongle for my Dell mini/Lubuntu 12.04.   It's a cheapo brand and not on the compatibility list but from what I heard most dongles work fine with Ubuntu so thought I'd give it a go.  

Anyways, I've been trying to pair it with my Vodafone 858 Smartphone and no luck so far.  Both devices can detect one another but neither one will pair with the other.  Smartphone just times out trying to pair with the Bluetooth adapter and when I select the Smartphone in Bleuz and try to pair to it (or do anything else for that matter) bluez and the entire system hang.   So, I end up having to power cycle my PC after each attempt.   Very frustrating..  I've gone through quite a few threads, a lot of people in a similar situations but no solution to my problem as of yet. Not sure whether there are some Bluetooth packages I need to install or whether the adapter is simply incompatible with Ubuntu.  Any ideas?

---

### Post by ahallubuntu on 2013-04-14
~

---

### Post by stevesy on 2013-04-18
> **ahallubuntu said:**
> I use bluetooth dongles on a couple of 12.04 machines.  Mine are cheap mini-dongles purchased from eBay for about $1.50 USD each (from Asia).  I have no problem at all pairing devices - my phone for one (to tether for internet access on my laptop or netbook) and also a bluetooth mouse.  There are a few issues with bluetooth in 12.04.1 (not sure about 12.04.2 yet) for sure.  Sometimes when I suspend/resume my laptop too many times, bluetooth is just "gone" and cannot be re-enabled in any way I can find without rebooting.  I'm hoping 12.04.2 fixes this, when I eventually upgrade to it.  But it's an annoying, no debilitating problem like yours.

I'm sorry that doesn't help you with your problem, except that you might go ahead and order one of those cheapy dongles like mine from eBay or Amazon in the meantime.  As cheap as they are, you might as well have an extra one anyway - and maybe when you finally get it it it will work better than the one you have.  Mine work very well (worked better in 10.04).

Hey ahallubuntu, thanks for your input. Still having problems  with pairing...but more importantly with blueman crashing.  Tried to find some support on sourceforge but there's none availabe.. I'm on 12.04.2 LTS fyi
Can anyone help?

---

### Post by stevesy on 2013-04-20
For newbies like myself who are experiencing similar difficulties have a look at:

[http://blog.projectnibble.org/2010/08/08/how-ubuntus-broken-bluetooth-support-came-to-be/](http://blog.projectnibble.org/2010/08/08/how-ubuntus-broken-bluetooth-support-came-to-be/)
[ http://devasive.blogspot.ie/2012/11/ubuntu-1204-persistent-bluetooth-pairing.html]("http://devasive.blogspot.ie/2012/11/ubuntu-1204-persistent-bluetooth-pairing.html")

Might give you some ideas

---

### Post by stevesy on 2013-04-27
Finally got bluetooth working!  I decided to return my Dynamode dongle  and swapped it for a slightly less cheapo dongle, a Hantol v2.0 which is  around &#8364;10/$13. This solved the system hang problem.  So, if you're  experiencing crashing like I was then from my experience it's most  likely the dongle you're using.  Maybe consider upgrading it.  

I  used blueman bluetooth manager 1.23 that ships with Lubuntu 12.04 to  pair/connect my bluetooth devices.  I'll tell you the process I went  through to get my K810 keyboard working..

Open a terminal (ctrl & alt & T) and enter in *blueman-manager* to open up the bluetooth manager.

Click "enable bluetooth" on the gui that pops up.

Make  sure your K810 keyboard is discoverable and then click on the "search"  button.  When the keyboard is detected it'll appear on the devices  list.  Once it does, highlight it and click on "setup" to access the  setup assistant and get pairing set up

Click on custom  pin/passkey code and enter whatever you like (e.g.0000 ) then quickly  enter this same code into the K810 keyboard (and hit enter).  You may  need to try this a few times before it works, I got "pairing failed"  quite a bit before succeeding.  Power cycling the keyboard and pc may  also be worth a go if you're having no luck pairing.  Once paired and  the device added click on "input service" and you're good to go.  If you  trust the device which I assume you will as it's your keyboard, click  on the yellow star to add it as such. Done.  

If none of that works try another app e.g. gnome bluetooth and/or command-line workarounds like [http://devasive.blogspot.ie/2012/11/ubuntu-1204-persistent-bluetooth-pairing.html](http://devasive.blogspot.ie/2012/11/ubuntu-1204-persistent-bluetooth-pairing.html)

Just to mention, PC-Smartphone bluetooth works fine for me.
Still looking into Keyboard-Smartphone, devices pair but won't connect.

Hope this is of some help to those suffering from the same headache as i was.

---

