---
title: "Asus N80Vn No Sound!!! Please Help!!!!"
date: 2008-11-19
forum: Hardware
---

### Post by excite23 on 2008-11-19
Hi all,

I just bought an Asus N80Vn and I have been trying to get the sound to work for the last 3 days. I have tried to add options to the Modprobe file. I have tried removing pulse audio and installing esound ( which screwed my login up). I have the realtek 633 card. 

Any suggestion would be greatly appreciated. 

Regards
Tom

---

### Post by Unleaded12 on 2008-12-08
Question:  Is everything else running fine with your setup?  I'm thinking of getting the same model off of newegg ([http://www.newegg.com/Product/Product.aspx?Item=N82E16834220391](http://www.newegg.com/Product/Product.aspx?Item=N82E16834220391)).  
If it's only the sound that's not working it should be ok, but gfx and networking (at least) need to function.

Sorry I have no advice on your sound problem though :(

---

### Post by zeroepoch on 2008-12-29
My friend has this same laptop.  To get sound working on his laptop I had to specify the model.  I think the model of the card is detected when the module is loaded and certain channels are setup at certain addresses.  The Asus M51Va I thought would be similar and indeed it somewhat is.

I created the file "/etc/modprobe.d/hda-intel" with the line:

options snd-hda-intel model=m51va

I haven't been able to get any recordings to work.  To get WoW working I had to remove pulseaudio, but I'm sure there is a way to get it working with pulseaudio.  Using 32-bit would probably make the WoW situation easier.  I also had to use the nVidia 180 series beta drivers to get 3D working, for any one interested.  Everything seems to be working, expect wifi is sometimes flaky (have to reconnect), and recording isn't working.  This is all on Fedora 10, maybe Fedora 11 will work out of box.

---

