---
title: "Dell Latitude D800"
date: 2006-04-17
forum: Hardware &amp; Laptops
---

### Post by jeffburg on 2006-04-17
Hey guys, i have a scenario here and I wanted to know if anyone could give me any insight.

I will start off by saying I'm a machead and have been for the past couple years after I gave up on Linux to replace windows.  However, I do have lots of experience both with windows and linux... although I'm still not a programmer and I often have a hard time compiling software in linux.  but it seems that some of the linux distros have really matured over the past few years.

so here is the scenario im in.  My girlfriend has a Dell Latitude D800.  A few weeks ago it could no longer function with all of the spyware and adware and crap on it and it kept crashing.  So I reformatted it and put windows xp on it and it has been having this weird ( i believe its the video drivers ) crashing error where you will be working and all of a sudden the screen goes all crazy and the computer just restarts.  I set her up as a limited user and we were gonna buy some antispyware and virus stuff for it.

but then i got to thinking.  All she does is browse the web, watch dvd's, check email, write essays, print, and use itunes.

so all of those are easy in linux except the itunes part.  I found a blog entry on installing itunes on linux with wine and im willing to try it.  But I just wanted to know if anyone here has run ubuntu on the D800 and what they had to say about it.  Was it a bitch to get the wireless working?  what bout the nvidia drivers, do those still have to compiled with the instructions on nvidia's site?  does ubuntu come preinstalled with vlc for dvd's?  and does it have wine preinstalled? or if not preinstalled are they available in an easily installable form.  I'm not sure how the package management works in ubuntu but i mean is there like the equivilant of an rpm of those for ubuntu?


sorry for the long post, but I thank anyone in advance that can help me.

---

### Post by catty0320 on 2006-04-17
i havnt tried with a d800 or any laptop or dell for that matter but i dont see why it woulnt run.  give it a try and submit the result to the laptop suppoort section on the wiki.  also check there if you havnt yet here is a link


      [https://wiki.ubuntu.com/LaptopTestingTeam](https://wiki.ubuntu.com/LaptopTestingTeam)   

  if you cant click it copy and paste it.

 :)

---

### Post by catty0320 on 2006-04-17
HOWTO: DELL Latitude D800 

try this link

---

### Post by catty0320 on 2006-04-17
[http://www.ubuntuforums.org/showthread.php?t=5464](http://www.ubuntuforums.org/showthread.php?t=5464)

try this

---

### Post by jimbren on 2006-04-17
That howto is pretty old, and I wouldn't use it as a step by step.  

I have a Latitude D400 that I can run (k)Ubuntu on with no issues.  Sound and wireless work out of the box--note that in the howto above you have to ndiswrapper.

The video card is different, and you will need to install the nvidia drivers.  I would recomend doing a default install and then running something like automatix, and you should be good.  It will also take care of the codecs you need to watch movies and play mp3s and such.

Automatix gives the option of installing Wine--I personally would not do it from there.  I've had problems with it that I've never fully fixed--I'm sure they could be worked through though, and there are excellent resources here to help you.

---

### Post by jeffburg on 2006-04-17
bizzarr, i searched for a good 1/2 hour on the site for dell latitude and just latitude and just dell and i never found that post.  Ok, i think I will try reformatting everything and installing this.  I think I will still dedicate 10gb or so to windows and then 20 to ubuntu.  If I install windows first will ubuntu play nice with it and give me a boot loader and stuff?

---

### Post by jimbren on 2006-04-17
Yeah, if you install windows first and then ubuntu, you'll be fine.

---

### Post by jeffburg on 2006-04-17
does the linux kernel in ubuntu come precompiled to read HFS+ and NTFS?  I know it can't write NTFS reliably but I didn't really want to recompile the kernel to read and write HFS +

---

### Post by K.Mandla on 2006-04-18
I can't speak for HFS+, but NTFS is accessible with few acrobatics. No compilation necessary. Search the forums for "mount Windows" and you should find about 3 million posts on how to do it. ;) Cheers!

---

### Post by mikitz on 2007-11-09
i installed gutsy on a dell latitude d800 that already had winxp on it, and everything worked fine. have to use the nvidia restricted driver, but it pops up and prompts you, so it should be easy for most.

---

