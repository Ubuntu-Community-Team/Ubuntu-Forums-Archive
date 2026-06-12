---
title: "analog-digital converter, i/o board for Linux - Ubuntu"
date: 2008-03-11
forum: Hardware &amp; Laptops
---

### Post by maxino on 2008-03-11
Hiya all,

After having toyed for a while with a fun microcontroller named [[COLOR="RoyalBlue"]Arduino[/COLOR]]("http://www.arduino.cc/") and learned a few things about interfacing leds, photoresistors, servos and motors, I'd like to do the same using some old crappy laptop (that I could get almost for free).
I'd like to build a two-wheels robot, sit the laptop on it, and use the laptop to control its movements and react to the environment.
What I basically need is to interface an analog-digital converter (to read things like temperature, light, analog output from accelerometers/gyros/sonars), a input-output board (to read in buttons states, light leds, wheel encoders) and a pwm controller (to drive the motors).
Some program I've yet to design would poll the inputs (or via interrupt) and control the motors.
These boards should be:

1. Interfaced to a laptop (meaning through USB, perhaps serial, no parallel)
2. Working nicely with Linux (Ubuntu, of course!)

Can anyone suggest what kind/brand/model of boards/converters I should look for?

Thanks everyone

max(ino)

---

### Post by gregology on 2008-06-02
I also would like a i/o solution for Ubuntu. What program would you use to control your I/O card? is there any software already created for Ubuntu for this purpose?

Thanks

Greg.

---

### Post by optique on 2008-06-05
Glad to see some interest in Arduino in the Ubuntu world!

I am hooked on this, too. I am in the flashing lights, buttons, stage too.


Maxino, about controlling a robot via a laptop: If I read you right, you want to use the processing power of the laptop to control the robot. As opposed to controlling the robot just with the Arduino. Right so far?

Why are you abandoning the Arduino to try to find an interface card? I think either the Arduino or Wiring would make a fine start for the interface. 

I would think you could do this:

hardware: pc--->Arduino hardware--->Sensors
Software: Processing environment--->Wiring language--->Sensors

the pc could ride the robot (a rather mighty robot if I may so so), with the vast processing power of the pc running Processing, talking to the Arduino. 

See these links:

Processing Environment: [http://www.processing.org]("http://www.processing.org")

Wiring: [http://www.wiring.org.co]("http://www.wiring.org.co")
Wiring hardware: [http://www.sparkfun.com/commerce/product_info.php?products_id=744]("http://www.sparkfun.com/commerce/product_info.php?products_id=744")


I just bought a book today, "Making things Talk", by Tom Igoe. This book seems fantastic, and I think we all could benefit from it. 

Also, the current issue of nutsvolts.com mag for an article on bit banging with a breakout board for a ftdi usb serial chip. It's available from smiley micros or sparkfun. I think this technique has possibilities.

If I got all this wrong, or if you know it already, then I apologize.

Best of Luck,
Steve.

---

