---
title: "Thinking about an HP Latop dv7-1020us"
date: 2008-08-28
forum: Hardware
---

### Post by leodesol on 2008-08-28
[http://www.shopping.hp.com/product/computers/notebooks/dv7t_series/rts/4/computer_store/FF214UA%2523ABA](http://www.shopping.hp.com/product/computers/notebooks/dv7t_series/rts/4/computer_store/FF214UA%2523ABA)


I think I will just buy it with Vista, but I could get it OS free as well. Think I will have much trouble setting up an Linux partition or install on it?

My Linux experience is still pretty low, but I am loving it and want to have it on a new machine instead of the old PC I have it on now.

My technical (non-Linux) experience is advanced, and I troubleshoot/research well.

I noticed NVidia has the drive for the gfx card available, so I am thinking many of the other headaches would be minor like some issues with fingerprint scanner or other type things?

---

### Post by sergiom99 on 2008-08-28
well, most of the hardware is intel based, so it should work fine under hardy, at most you might have to work a little bit with the wireless card, but that laptop should be ok. nvidia works out of the box now.
Anyway, the golden-test is to go to a store and boot with an Ubuntu LiveCD.

Other useful links:
[http://www.ubuntuhcl.org/](http://www.ubuntuhcl.org/) (for the hardware parts)
[https://wiki.ubuntu.com/LaptopTestingTeam/HewlettPackard](https://wiki.ubuntu.com/LaptopTestingTeam/HewlettPackard)

---

### Post by Koufax on 2008-08-30
I have the dv7-1020us, and had some issues on first boot with Hardy.  I am going to be trying again and seeing what I can configure, but it was by far my worst start up experience with the first running of Ubuntu unfortunately :(

---

### Post by !! Shawn on 2008-09-07
> **Koufax said:**
> I have the dv7-1020us, and had some issues on first boot with Hardy.  I am going to be trying again and seeing what I can configure, but it was by far my worst start up experience with the first running of Ubuntu unfortunately :(

I am in total agreement. I have a dv7-1020, nothing but headaches. Its basically useless at this point. There are no wireless drivers for xp, I don't have a vista cd, and I wiped vista from the HD before testing if Ubuntu actually worked. 

It doesn't. I have this annoying sound looping problem, the wireless doesn't work, and I am sure that many other things on it don't work correctly. 

Ive been using Ubuntu for over a year on my other computers and I am really disappointed in the lack of support for this hardware. 

I even installed the latest version of Intrepid Ibex thinking that all the new support from the .27 kernel would solve my problems. 

It didn't. 

If you are going for a new laptop, learn from my mistake and check that it works with Ubuntu first.

---

### Post by lopata on 2008-09-13
i have  pavilion dv 7 1020el
and its working with hardy very well

sound dont work too :(
but wireless is working very good.

even the aircrack too :D

everything is explained here ( wireless)
[http://ubuntuforums.org/showthread.php?t=879134](http://ubuntuforums.org/showthread.php?t=879134)

Shawn -  you have a partition ( recovery )  from there you can reinstal your vista ;)
press F11 i think to start in recovery mode

---

### Post by Koufax on 2008-09-23
I had no luck with Wubi, but did a real install from the LiveCD without any issues.  Had to get the nvidia drivers (Envy wouldn't work).  I haven't gotten wireless and a few other things yet, but it seems overall to be working very well.

---

### Post by Jorge_C on 2008-09-24
For those of you who have sound problems (it kind of loops), try adding pci=noacpi as a boot option, as described in [this thread]("http://ubuntuforums.org/showthread.php?t=912896"). It worked for me in my HP dv7-1090es, and the specs are quite similar (same altec lansing speakers, for instance).
Have a look [here]("https://help.ubuntu.com/community/BootOptions") just in case you don't know how to test the boot option/make it permanent.

---

### Post by lagerman on 2008-09-24
!!Shawn did you delete the recovery partition?? If not try pressing f11 on boot-up. That should get you into the recovery side so at least you can reinstall vista. I recently purchase the 1020 as well. I made recovery disks as soon as I could (just in case I really !#?*@$ up my laptop). I hoped this helps a little...

---

