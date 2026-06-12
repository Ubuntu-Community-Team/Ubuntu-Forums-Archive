---
title: "Dell 530s Graphics card upgrade &amp; is the graphics card used for processing?"
date: 2015-06-05
forum: Hardware
---

### Post by nigel on 2015-06-05
I had a quick read of this post

[http://ubuntuforums.org/showthread.php?t=2280538](http://ubuntuforums.org/showthread.php?t=2280538)

Which is for the standard desktop model, my one is the slim model, so it has only a 250W power supply, but it did answer a number of my original questions

anyway the spec

Ubuntu 14.4
The specs i have are
Intel Core 2 Duo @ 2 GHz 
ATI Radeon X1300/1500 series 128MB GPU 
4GB DDR2 RAM 
250GB HDD 


This machine is normally used for running Krita(Graphics program), and it is well a bit sluggish,

There are a number of low profile cards going for less that $10 (inc shipping) on the local auction site
ATI HD2400XT 256MB
Quadro NVS 210 256

and yes I am aware they are old cards

*after these two cards the prices just seem to jump to $30 and up*

Both of which look like they would fit fine and are easily within my budget , (I don't really want to spend any money), Both have 256 rather than 128mb, the ati has a fan on it whereas the nvidia doesn't, But would they have an impact on performance of a graphics programme.

Also which works better with Linux Nvidia or Ati or is it a case of they should both be fine 

Cheers

---

### Post by grahammechanical on 2015-06-05
Some Linux distributions such as Ubuntu work better if the graphic adapter can do 3D rendering. Otherwise, the CPU has to do it. The more of its own memory that a graphic adapter has the better.

I am not sure if you will see much improvement by doubling the memory on the graphic adapter. My machine has an Intel core 2 Duo 2.40 GHz and only 1 GB RAM but I do have a Nvidia GT220 with 1GB of its own memory and I do not see any slowness. I admit that I might see some improvement if I have 2 GB or more of RAM. Especially when viewing PDF documents that are made up of scanned images.

The fact that you have 4 GB of RAM and say "it is a bit sluggish" points the finger, in my mind, to the graphic adapter. Having used a graphic adapter with 512 MB of its own memory and replaced it with an adapter with 1 GB of memory I would recommend spending the extra and getting an adapter with either 512 MB or 1GB of memory.

Regards.

---

### Post by Yellow Pasque on 2015-06-05
> ATI HD2400XT 256MB

You may be able to get some usefulness out of that one: [http://www.phoronix.com/scan.php?page=news_item&px=MTc3MTc](http://www.phoronix.com/scan.php?page=news_item&px=MTc3MTc)

---

### Post by mörgæs on 2015-06-07
Before adding hardware I suggest that you try a lighter desktop environment. If you add LXDE with the command ```
sudo apt-get install lxde
``` you will be able to choose between LXDE and Unity at boot.

---

### Post by Yellow Pasque on 2015-06-07
Oh, I missed the Krita part. I don't know if a GPU upgrade would help or not. I see their manual says Krita is not memory-efficient and recommends 4GB RAM minimum, so maybe you would be better off adding 4 more GB of RAM if possible.

---

### Post by nigel on 2015-06-09
Thanks for the response, Its SWMBOs computer, i have suggested a lighter desktop, but nope, I will try one of the graphics cards, apparently the lagging happens when using brushes or something like that. 
Mat also try more RAM as apparently depending on the bios, it can take up to 8gb, which provided its the 64 version of ubuntu may make a bit more difference

---

