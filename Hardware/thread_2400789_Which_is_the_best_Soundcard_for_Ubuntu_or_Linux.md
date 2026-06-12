---
title: "Which is the best Soundcard for Ubuntu or Linux?"
date: 2018-09-10
forum: Hardware
---

### Post by MariosFFX on 2018-09-10
Hello
I am an owner of a Sound Blaster Zx internal sound card which does not have support for Linux and I'm gonna switch it out.
Because I am going to change my main OS to Linux I would like to buy a new sound card and I'm looking for the best sound card which will  be best compatible with Linux.

I am using 5.1 Logitech Z-5500 and my ear has been used to sound quality in music, movies and all kind of stuff.
and I can notice changes between 56000b bit rate , 16 bit and 960000 bit rate and 24 bit

I'm mostly interested in USB cards since I will be able to use it on other systems as well.

---

### Post by conmanx360 on 2018-09-11
Hi!

I wrote the newest version of the ca0132 driver and added support for the Sound Blaster Z series. Try out a newer kernel version (4.18 is the first with the newer driver) and let me know if it works. I have been using my Z series card for awhile now on Linux.

---

### Post by MariosFFX on 2018-09-11
> **conmanx360 said:**
> Hi!

I wrote the newest version of the ca0132 driver and added support for the Sound Blaster Z series. Try out a newer kernel version (4.18 is the first with the newer driver) and let me know if it works. I have been using my Z series card for awhile now on Linux.


hey!!!
Do you also support features such as: 5.1, surround, crystalizer and all other stuff?

---

### Post by conmanx360 on 2018-09-11
I currently have surround sound working, but with effects on, it doesn't mix the channels properly, so surround is only really usable with effects disabled. The effects work with just stereo and headphone, though. I plan on fixing the surround sound with the output effects soon, I've just had a lot of work to do as I've also recently added AE-5 and ZxR support.

Let me know if you test it.

---

### Post by MariosFFX on 2018-09-17
> **conmanx360 said:**
> I currently have surround sound working, but with effects on, it doesn't mix the channels properly, so surround is only really usable with effects disabled. The effects work with just stereo and headphone, though. I plan on fixing the surround sound with the output effects soon, I've just had a lot of work to do as I've also recently added AE-5 and ZxR support.

Let me know if you test it.


Hello!
Sorry for the late reply, I just installed latest version of Ubuntu of My Desktop and unfortunately there is still no sound from the sound card.
What other options do I have?

---

### Post by mastablasta on 2018-09-18
what kernel are you using? you need to load the new kernel (you might need to add a ppa for that).

---

### Post by conmanx360 on 2018-09-20
> **MariosFFX said:**
> Hello!
Sorry for the late reply, I just installed latest version of Ubuntu of My Desktop and unfortunately there is still no sound from the sound card.
What other options do I have?

Sorry for not responding earlier, I don't check these forums too often.

You'll need to update to kernel 4.18. There are .deb packages to do so, I did it on a second system I built a few days ago. I also set up a DKMS to do it, if you'd rather do that let me know. Also let me know your kernel version if you want to do the dkms.

---

