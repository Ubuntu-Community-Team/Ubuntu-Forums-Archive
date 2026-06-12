---
title: "Audio problems with Nforce 4 audio"
date: 2005-10-05
forum: Hardware &amp; Laptops
---

### Post by ngottlieb on 2005-10-05
I have an epox 9npaj motherboard with an nforce 4 chipset. It has a builtin 5.1 sound system. That sound is, I believe, just the basic nforce 4 audio (it came with a windows cd with Realtek AC'97 drivers, though, if that changes things). Neither windows nor linux have recognized it. I've tried installing drivers in both, including the realtek drivers, the nforce drivers, etc. The drivers tend to install successfully, the computer just never recognizes them. I have alsa on ubuntu right now (it's what it installs set up witH) and it just doesn't see anything. 

It's possible (and likely, at this point) that it's a hardware failure, although I did check to see if there might be a short on the back of the board against the case, and there wasn't. Chances are, I'm giong to try and RMA the mobo, but I wanted to make sure there wasn't something I could do first, something I was missing.

If you can think of anything I might be doing wrong or not be doing, thanks a lot!

--Nick Gottlieb
AMD 3000+ Venice
Epox 9npaj+ mobo
Asus Geforce 6600 256mb 
4x256mb Kingston ValueRAM

---

### Post by Dennis Laumen on 2005-10-06
I really think this is a hardware problem!
I have an nForce 4 motherboard as well (including the Realtek audio, I believe it's called ALC850). It all runs perfectly here (out of the box).
If you can't get it to run on Windows with the drivers you got on CD with it, it is probably broken.

---

### Post by Biased turkey on 2005-10-06
I have an Nforce4 mobo ( Elitegroup KN1 ) and when installing Ubuntu the onboard sound was working right out of the box.

1) Did you enable the onboard sound in the BIOS ? ( I know that's an obvious suggestion )

And as Dennis mentioned, if it doesn't work on Windows with the CD drivers it's probably broken.

I had exactly the same problem 2 weeks ago with the Nforce2 onboard sound of my 2nd computer. It was a real hardware problem.I ended buying an Audigy2 soundcard.

---

### Post by ngottlieb on 2005-10-06
One more thing before I try to RMA the board...Do you guys think it might be that I don't hvae enough power? I'm using the case PSU which is decent, but nothing special (as well as a few years old). In addition, I'm uisng a 20-pin Power plug for the mobo in a 24-pin slot, although I believe that the extra 4 things are just for SLI...Could that be the problem?

Thanks, Nick

---

### Post by Dennis Laumen on 2005-10-06
I don know if it's an PSU problem. You could always check weither you have enough juice ;) with the eXtreme PSU Calculator: [http://www.extreme.outervision.com/index.jsp](http://www.extreme.outervision.com/index.jsp)

I ran my PC with a 20-pin PSU in 24-pin Motherboard for a while but it wasn unstable. I decided to by myself a 20 to 24-pin converter which was really cheap (approximately 2 - 3 euros) for that extra bit of security (just in case).

@Biased Turkey: Isn't the nForce 2 series the one which is equipped with the great soundstorm audio? Because that would be a shame!

---

