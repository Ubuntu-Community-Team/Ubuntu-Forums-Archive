---
title: "How do I boot ubuntu from an External Hardrive(if I even can)"
date: 2008-09-18
forum: Hardware
---

### Post by Nitefang on 2008-09-18
I have decided that Ubuntu is still just a little bit to complicated for me to use as my main OS of choice. The only reason why I say this is because I can do a lot of things already in Ubuntu but there are things that i need to do fast and if I can't then it will screw up other parts of my life. Just as an example it took me forever today to write a report for school and print it. In fact I never even managed to print it, I had to put it on a thumb drive and go to the computer that the printer is plugged into. I still have a lot of work to do and I want to relax at some point today. So I will try to stay active on this forum, help people if I ever know the question(might happen eventually ;) ) and continue to experiment with Ubuntu.

  Now to my actual question. My hard drive is quite small 320gigs. I had filled it up and wiped my computer right before I started to really use Ubuntu. Well since I was dual booting with Vista I filled up the hard drive very quickly. So I want to put Ubuntu on an external harddrive. I realize that this is probably simple but I don't have a lot of time and I like to get things done before I move on. So is there anything that I need to know, any apps I need, and how exactly do I do it?


  Thank you for reading this long post and thank you even more for helping me. I will thank anyone that replies with useful info (I would anyway).

---

### Post by haydnc on 2008-09-18
Installing Ubuntu on an external hard drive should be fairly straight forward as long as the hard drive is turned on and plugged in.

I'm afraid I've never tried it so I can't answer with absolute certainty but if you boot from the Ubuntu CD and chose to install the OS it usually asks where you want to install to. Amongst the listed options you should see your external hard drive listed, although it probably won't be the one selected by default. It might be listed as /dev/sdg or something similar.

You'd need to be careful to install Grub to the same location you install Ubuntu to - again from memory that's an option you can pick while installing the OS though its normally an advanced option. Say, for the sake of argument that you're installing Ubuntu to /dev/sdg you'd want to install the boot information/grub/whatever to /dev/sdg1.

As far as booting from Ubuntu on the second hard drive goes you might find the easiest way is to use your Bios to set the external hard drive as the first boot device. The only down side to that I can think of is the boot loader (eg Grub) will probably freak out about Ubuntu being located in a different location from what it should be. You'd possibly need to edit the Grub menu to change /dev/sdg to /dev/sda once you modified the boot order.

My apologies for this all seeming a bit vague. I'm more or less forced to guess what I'd try if I were setting up the same thing as what you're describing.

---

### Post by Nitefang on 2008-09-18
Thank you, I'm sure that would work but since I am very new to ubuntu and it isn't my external HDD, its my friends from work and I don't want to mess it up or make it unavailable for him. I am also reading how to put it on a thumb drive and I may try that. Thank you though!

---

### Post by haydnc on 2008-09-18
> **Nitefang said:**
> I am also reading how to put it on a thumb drive and I may try that.

You'll probably find that using at Thumb drive is almost exactly the same process - only easier to start again if something goes wrong. Good luck and remember not to overwrite your existing hard drive (probably listed as /dev/sda or /dev/hda ).

---

