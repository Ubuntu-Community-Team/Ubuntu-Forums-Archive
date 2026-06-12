---
title: "Fn and multimedia keys on toshiba laptop"
date: 2006-08-24
forum: Hardware &amp; Laptops
---

### Post by lukasig on 2006-08-24
I have a Toshiba Satellite M45-S2692... I cannot get my Fn key to work... I installed from Synaptic Package Manager everything i found on "Toshiba" search:
fnfxd
toshset
toshutils

I was expecting it to add at least something in my menus somewhere... but nothing.. and still not working. My multimedia keys are not working either

If you use terminal in your answers... please be specific... I am a beginner in Linux...THX
Edit/Delete Message

---

### Post by daller on 2006-08-25
Follow this howto:

[https://help.ubuntu.com/community/MultimediaKeys](https://help.ubuntu.com/community/MultimediaKeys)

And for easy setup, you should have a look at KeyTouch:

[http://keytouch.sourceforge.net/](http://keytouch.sourceforge.net/)

---

### Post by daller on 2006-08-25
Haven't tried, but KeyTouch really seems like a nice application:

So in short, to get it installed: (not in the repository! - but don't let that scare you!)

Open a terminal, and run these commands:

Download the install-file:

```

wget http://heanet.dl.sourceforge.net/sourceforge/keytouch/keytouch_2.2.0-0ubuntu1_i386.deb

```

Install a package that it depends on: (Maybe only a Kubuntu issue!)

```

sudo apt-get install libgnome-menu2 

```

And install it:

```

sudo dpkg -i keytouch_2.2.0-0ubuntu1_i386.deb

```

Now you should be able to find it in the menues! (In Kubuntu, it's: K->System->KeyTouch)

Good luck!

---

### Post by lukasig on 2006-08-26
Thanx man.... but KeyTouch supports only one type of toshiba keyboard...which is not compatible with mine (M45 - S2692)

---

### Post by daller on 2006-08-27
Then you can install keytouch-editor

See:

[www.sf.net/projects/keytouch](www.sf.net/projects/keytouch)

...and setup your keyboard! - And contribute to the community, that way! (I just added "Dell Inspiron 8600")

Good luck!

---

### Post by mdmarmer on 2006-09-02
Most of these programs are written for Toshibas which have Toshiba BIOS --
newer Toshibas like yours have Phoenix BIOS, these programs don't work --
try this one

[http://tz.exit0.net/tecras1.html](http://tz.exit0.net/tecras1.html)

Also look here

[http://www.tuxmobile.com/toshiba.html](http://www.tuxmobile.com/toshiba.html)
[http://www.linux-on-laptops.com/toshiba.html](http://www.linux-on-laptops.com/toshiba.html)
[https://wiki.ubuntu.com/HardwareSupportMachinesLaptopsToshiba](https://wiki.ubuntu.com/HardwareSupportMachinesLaptopsToshiba)

Mike

---

