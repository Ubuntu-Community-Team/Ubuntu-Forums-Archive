---
title: "Wiring for HD44780"
date: 2009-04-19
forum: Hardware
---

### Post by alek66 on 2009-04-19
Hi everyone I am trying to build the lpt interface por a lcd display 16x2
There are many wirings... I wante to know wich one shuold I use ([http://lcdproc.sourceforge.net/docs/stable-0-5-x-user.html#hd44780-connections)if](http://lcdproc.sourceforge.net/docs/stable-0-5-x-user.html#hd44780-connections)if) wanted to use it to show me temperature, fan, disc usage, memory.

Am I confused or all the wirings are the same? Thanks in advance.-

LDC PROC does work un ubuntu?

---

### Post by ddrichardson on 2009-04-19
The second has a couple of op-amps in it and some sort of feedback loop which appears to be used in a keyboard attachment. The basic cct should suit your needs:

[http://lcdproc.sourceforge.net/docs/stable-0-5-x-user.html#hd44780-seriallpt.simple-circuit](http://lcdproc.sourceforge.net/docs/stable-0-5-x-user.html#hd44780-seriallpt.simple-circuit)

---

### Post by alek66 on 2009-04-19
> **ddrichardson said:**
> The second has a couple of op-amps in it and some sort of feedback loop which appears to be used in a keyboard attachment. The basic cct should suit your needs:

[http://lcdproc.sourceforge.net/docs/stable-0-5-x-user.html#hd44780-seriallpt.simple-circuit](http://lcdproc.sourceforge.net/docs/stable-0-5-x-user.html#hd44780-seriallpt.simple-circuit)

With that I can use to get that kind of info?

Whats with the_ 4094shift register.... i tought that this cuold be done with nothing more...just wiring.

---

### Post by ddrichardson on 2009-04-19
How do you mean, just wiring? You need an integrated circuit (4094), a 100nF capacitor and a 10kOhm resistor. You'd also need a 5V supply, not sure if you could pull that through a serial port and it needs to be relatively stable as does the signal earth.

---

### Post by alek66 on 2009-04-20
> **ddrichardson said:**
> How do you mean, just wiring? You need an integrated circuit (4094), a 100nF capacitor and a 10kOhm resistor. You'd also need a 5V supply, not sure if you could pull that through a serial port and it needs to be relatively stable as does the signal earth.


Thanks for replying!

I am trying to make it LPT(like this [http://www.overclockers.com.au/techstuff/a_diy_lcd/](http://www.overclockers.com.au/techstuff/a_diy_lcd/))... and many sites (thata propose this for win) they just wire directly to a db25.... and dont use any integrated.
Thats why i asked.

---

### Post by alek66 on 2009-04-21
BY the way i am using a 16x2 HD44780 and i want to connect it to a parallel port, perhaps that changes things and i can connect it directly to my lpt.

---

### Post by ddrichardson on 2009-04-21
I really don't know - I just read the cct diagrams you linked to!

---

### Post by alek66 on 2009-04-21
> **ddrichardson said:**
> I really don't know - I just read the cct diagrams you linked to!

I am completly lost... i dont know if i need the shift register o i can wire it directly.

---

### Post by tylersontag on 2010-05-12
Hi, i'm trying to wire up a HD44780 LCD screen (20x2) and i've looked at some wiring diagrams and i feel fairly comfortable that i can do the wiring, i am however curious what actual hardware i should use.  My Parallel port is male out, so i would be very wary (actually, i flat out woudln't) soder wires directly to a male out line.  Even a male-to-female 'save-a-port' device seems like more work than should be nessisary.  Ideally, I have some circuit wires from a circuits class i took in college, do they make a parallel port to circuit board adapter i could buy?  Even a female-to-female adapter would work (though i might have to buy new wires, since im not sure they would physically go that far in my case)

The end product here is to hook in with the LCDproc adapter in boxee/XBMC so i can display show information on the front of my media case (incase you'd like to recomend any specific wireing setup)

Thanks

---

### Post by alek66 on 2010-05-12
> **tylersontag said:**
> Hi, i'm trying to wire up a HD44780 LCD screen (20x2) and i've looked at some wiring diagrams and i feel fairly comfortable that i can do the wiring, i am however curious what actual hardware i should use.  My Parallel port is male out, so i would be very wary (actually, i flat out woudln't) soder wires directly to a male out line.  Even a male-to-female 'save-a-port' device seems like more work than should be nessisary.  Ideally, I have some circuit wires from a circuits class i took in college, do they make a parallel port to circuit board adapter i could buy?  Even a female-to-female adapter would work (though i might have to buy new wires, since im not sure they would physically go that far in my case)

The end product here is to hook in with the LCDproc adapter in boxee/XBMC so i can display show information on the front of my media case (incase you'd like to recomend any specific wireing setup)

Thanks

Im not quite understanding what is a parallel por to cicuit board adapter??

---

### Post by tylersontag on 2010-05-12
Well, since i haven't found one on google, i imagine they don't exist outside of my head :-)

I was thinking something along the lines of, a PP cable that connects to a PCB ([http://rsk.imageg.net/graphics/product_images/pRS1C-4949331w345.jpg](http://rsk.imageg.net/graphics/product_images/pRS1C-4949331w345.jpg)) and there would be a row of pins that are all bridged to ports 1-25 and you could just run some wires out of those pins to do, whatever it is that you needed.

But thats just the first way to wire it that popped in my head, i'd love to hear how others have done.

---

### Post by tylersontag on 2010-05-13
Anyone?  I'm not asking for a HOWTO on building the above rig, just any info on how YOU wired up your LCD device?  I'm not certain how little is ever documented in every wiring scheme how they actually wired the thing... 

Is it the case that most people usualy get a male to female adapter, soder a wire to each pin and do all the wiring that way?   I'm really open to any advice.

---

### Post by tylersontag on 2010-08-05
Just FYI, i found a really good writeup on Instructables on how to get started

[http://www.instructables.com/id/Beginning-LCDs/](http://www.instructables.com/id/Beginning-LCDs/)

---

