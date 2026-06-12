---
title: "want to make a USB Wii sensor bar - looking for a good soldering iron.."
date: 2007-08-05
forum: Hardware &amp; Laptops
---

### Post by billdotson on 2007-08-05
I want to make a Wii sensor bar so that I can use my Wii in Windows using the GlovePie script.  

[http://terbidium.com/content/projects/wiihacks/usb_sensorbar.php]("http://terbidium.com/content/projects/wiihacks/usb_sensorbar.php")

[http://www.modpulse.com/articles/console-mods/usb-wii-sensor-bar/]("http://www.modpulse.com/articles/console-mods/usb-wii-sensor-bar/")

I do not have a soldering iron, nor do I have any experience with soldering or any type of hacking/modding.  How should I go about this?  I want to get a good soldering iron that I can use later on for bigger projects, but I do not want to spend a really large sum of money to do so.  Also, while I am up for a challenge, I do not want to go and buy the equipment I need to get this working and then come to realize that the putting together of the sensor bar and/or configuring the Wii remote to work (like it does with the console I assume) with GlovePIE and the other things needed to do so is out of my league and will ultimately end up wasting my time and money.

---

### Post by lolcats on 2007-08-05
Weller makes some good soldering irons... one they make is for students and runs 45$-- its tip sucks so you should get a higher quality tip. Also, before doing this kind of mod, learn some simple soldering techniques. I'd build this on a breadboard (kind of a proto board) and try small scale experiments.

Also, you can simply tape some remotes to your screen and have them run on volume up for whatever that helps to test your script.

---

### Post by billdotson on 2007-08-06
ugh that is pretty expensive.  $45 plus a new tip for it?  Also, what do you mean practice soldering techniques?  Just soldering together some wires to get the hang of it before I do the real project?  Also, what were you talking about taping remotes and volume and stuff?

---

### Post by GNUser on 2007-08-06
Do what I did, 8$ soldering pencil from RadioShack. They aren't good quality, but for your purposes (and mine) they work just fine. Just remember to have a wet sponge handy to wipe off the tip everytime you make a solder joint.

Good Luck :D

edit: Oh btw, I used wmd to set up my wiimote, works pretty well. Also, I've had the soldering pencil for over a year now. While you're at RadioShack you can also buy the rest of the parts : )

---

### Post by billdotson on 2007-08-07
So, from what I have seen the Wii sensor bar has 10 LEDs in it.  That must mean that the terbidium one with only 4 LEDs is not nearly as sensitive (and that translating to not as useful) as the official sensor bar that comes with the Wii.  Anyways, if this is not the case and it works almost as well, what exactly is required to do this?  From what I can gather, I need a bluetooth adapter, a bluetooth stack (not the Windows one, the bluesoleil one I think), GlovePIE, the IR script  for GlovePIE (to use the IR function obviously) and the USB sensor bar, right?

So, is the USB sensor bar even needed?  From some things I have been looking at people have been able to play the Wii by simply having 2 candles as the IR source and they are obviously not hooked up to the Wii.  If the USB sensor bar is hooked up to the PC waht does it do?  Get power for the LEDs and that is it?

 

Also, this is not directly related to Wii-mote, but if USB standards are 5 volts, how does that power things like controllers, or external hard drives?  I am not very knowledgable about electronics in terms of wiring, resistances, etc.

---

### Post by GNUser on 2007-08-08
Errmmmm.... I suppose you could go the two candles approach. If you are willing to have two melting wax buckets on top of your screen :D

In all seriousness, the voltage drop on 4 Infrared leds in series is almost 5V, leading to a perfectly safe circuit to plug into your computer. 

I don't know about GlovePie, I have been using WMB (we Wanna Mote something or other...).

---

