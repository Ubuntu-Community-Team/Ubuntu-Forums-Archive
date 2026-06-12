---
title: "sloow with 1024 ram, fast with 512"
date: 2005-11-15
forum: Hardware &amp; Laptops
---

### Post by philsstar on 2005-11-15
HEy everyone,
im running across a strange problem after my breezy install.
My System takes about 7-8 minutes to boot and gnome is ugly slow and screen refreshs lag. Everythings so slow. 
I have 1gig of ram and when i took out one of my 512mb's, its really fast again. 
I had no problems with 1gig and hoary nor warty though.

may this be a kind of kernel issue? maybe u know whats the prob. 
I would like to run my laptop with all its ram and not only 512. 

thank you
phil

---

### Post by AWAL on 2005-11-15
As a newcomer to Ubuntu Linux, I had a similar issue.

Yesterday I added 512 mb to my Dell Latitude C400/PIII-866/256 and it froze several times. I changed the speed settings in the BIOS, but it still froze up.  Breezy was running very well and was very stable until I inserted the additional RAM.  This morning I took out the RAM and everything was fine.

My question is whether the recommended RAM specs from Dell is correct or should I go to a different type of RAM if my processor speed is under 1GHz.

Again, I'm new to Linux, but I would like to run it as fast as I can on my laptop.

Hope someone can help us!
AWAL.

---

### Post by philsstar on 2005-11-15
as i see it it must be a kernel related problem becaue everything worked great in hoary which uses another kernel. 
hmm looking for a ubuntu kernel howto now. any help is appreciated. 
btw is there a source and config file that outputs the breezy kernel if compiled? If so i could try changing some ram related setting in hope of solving this mystery.

thanks

---

### Post by az on 2005-11-15
Why don't you just install the Hoary kernel in Breezy?

---

### Post by jasplund on 2005-11-15
have you tried the 686-kernel or the k7 kernel?

---

### Post by AWAL on 2005-11-18
FYI,

After reading the following replies, and philsstar's concern that it was a kernel issue, I loaded the 686 kernel with the extra RAM and was back up and running.  It's much much faster than before.

Thanks for the suggestions.

---

### Post by tseliot on 2005-11-18
[QUOTE=philsstar]as i see it it must be a kernel related problem becaue everything worked great in hoary which uses another kernel. 
hmm looking for a ubuntu kernel howto now. any help is appreciated. 
btw is there a source and config file that outputs the breezy kernel if compiled? If so i could try changing some ram related setting in hope of solving this mystery.

thanks[/QUOTE]

You can use my guide if you wish: [HOWTO: Kernel Compilation for Newbies]("http://www.ubuntuforums.org/showthread.php?t=85064")

---

### Post by varunus on 2005-11-18
I'm pretty sure this is an issue with the 386 kernel which does not have 1G memory support.  Install the 686 with the 512 stick in, and then add the ram and boot with the 686.  You should be ok.

---

