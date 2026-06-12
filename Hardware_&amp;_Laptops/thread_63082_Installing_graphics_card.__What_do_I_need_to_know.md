---
title: "Installing graphics card.  What do I need to know?"
date: 2005-09-06
forum: Hardware &amp; Laptops
---

### Post by tranquility base on 2005-09-06
Hi.  I am new to Linux and have been running it for 3 days now.  I am using a Shuttle SK41G, and the onboard graphics.  Because anything dealing with graphics (i.e. screensaver, DVDs, etc.) appeared choppy and slow, I ordered a new graphics card for the empty AGP slot.  I ordered a XFX GeForce MX4000 64MB DDR with 32-bit memory bus.

My question is how do I go about installing this?  It says it's compatible with Linux.  What do I need to do once this arrives?

---

### Post by John.Michael.Kane on 2005-09-06
Most likely you will just have to disable the onboard video controller, and install the agp one make sure you set you bios for agp. and you should be fine. at the worst you will have to install your drivers manualy...

---

### Post by tranquility base on 2005-09-06
[QUOTE=SD-Plissken]at the worst you will have to install your drivers manualy...[/QUOTE]

How do I do that?  Do I download a driver through Synaptic?  Which one should I get, if so?

---

### Post by John.Michael.Kane on 2005-09-06
driver support should be included in ubuntu. if it's not then this should be what you will need.

[http://www.nvidia.com/object/IO_18897.html](http://www.nvidia.com/object/IO_18897.html)
[http://www.nvidia.com/object/linux_display_ia32_1.0-7676.html](http://www.nvidia.com/object/linux_display_ia32_1.0-7676.html)

---

### Post by tranquility base on 2005-09-06
[QUOTE=SD-Plissken]driver support should be included in ubuntu. if it's not then this should be what you will need.

[http://www.nvidia.com/object/IO_18897.html](http://www.nvidia.com/object/IO_18897.html)
[http://www.nvidia.com/object/linux_display_ia32_1.0-7676.html](http://www.nvidia.com/object/linux_display_ia32_1.0-7676.html)[/QUOTE]


Many thanks for your helpful replies.

---

### Post by ltmon on 2005-09-06
[QUOTE=SD-Plissken]driver support should be included in ubuntu. if it's not then this should be what you will need.

[http://www.nvidia.com/object/IO_18897.html](http://www.nvidia.com/object/IO_18897.html)
[http://www.nvidia.com/object/linux_display_ia32_1.0-7676.html](http://www.nvidia.com/object/linux_display_ia32_1.0-7676.html)[/QUOTE]

Don't do it the way nvidia says (it'll work, but it's much easier the ubuntu way).

Do this: [https://wiki.ubuntu.com/BinaryDriverHowto/Nvidia](https://wiki.ubuntu.com/BinaryDriverHowto/Nvidia)

Cheers,

L.

---

### Post by tranquility base on 2005-09-07
[QUOTE=ltmon]Don't do it the way nvidia says (it'll work, but it's much easier the ubuntu way).

Do this: [https://wiki.ubuntu.com/BinaryDriverHowto/Nvidia](https://wiki.ubuntu.com/BinaryDriverHowto/Nvidia)

Cheers,

L.[/QUOTE]

Thank you very much, "mate".

---

### Post by GreyFox503 on 2005-09-07
Good choice on the nvidia card.  Before I knew about Ubuntu, I almost chose an ATI card, but decided against it.  That came back to be a very good thing  :smile: 

It'll probably give you the regular desktop immediately, but to enable 3d acceleration you might have to install nvidia's driver.  I got mine through the repository.   I followed the instructions here:

[http://www.ubuntuguide.org/#installnvidiadriver](http://www.ubuntuguide.org/#installnvidiadriver)

and it worked well.

I haven't tried the way described in the wiki but it looks pretty similar.  Maybe you should try that first, as it seems a little more "official", for lack of a better word.

---

### Post by tranquility base on 2005-09-07
[QUOTE=GreyFox503]Good choice on the nvidia card.  Before I knew about Ubuntu, I almost chose an ATI card, but decided against it.  That came back to be a very good thing  :smile: 

It'll probably give you the regular desktop immediately, but to enable 3d acceleration you might have to install nvidia's driver.  I got mine through the repository.   I followed the instructions here:

[http://www.ubuntuguide.org/#installnvidiadriver](http://www.ubuntuguide.org/#installnvidiadriver)

and it worked well.

I haven't tried the way described in the wiki but it looks pretty similar.  Maybe you should try that first, as it seems a little more "official", for lack of a better word.[/QUOTE]

Thanks.  It's good to have so much input from everyone.

---

