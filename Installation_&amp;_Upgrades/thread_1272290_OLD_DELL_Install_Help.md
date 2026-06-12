---
title: "OLD DELL Install Help"
date: 2009-09-22
forum: Installation &amp; Upgrades
---

### Post by mattevandavis on 2009-09-22
I have a Dell Inspiron 2650 that i can not seem to gt running with ubuntu.  i have tried xubuntu too.  when it gets to where the os should load it just has a flashing cursor.  i assume its my video card?

HELP.

---

### Post by tommcd on 2009-09-22
First you should rule out a bad CD. How did you burn the CD? If you are burning the CD from Windows, use Iso Recorder or Infra Recorder:
[https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)
Be sure to burn the CD at the slowest possible speed. Then when you boot up from the CD choose the option "check disc for defects". This takes a minute or 2 to run. If it passes the disc is good.
Also check the md5sum of the iso image you downloaded to make sure the downloaded image is good:
[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM) 

Second, according to this:
[http://reviews.zdnet.co.uk/hardware/notebooks/0,1000000333,10001414,00.htm](http://reviews.zdnet.co.uk/hardware/notebooks/0,1000000333,10001414,00.htm)
your laptop only has 256mb RAM. If that is all the RAM you have then that is just barely enough for the live CD. You may have better luck with the alternate install CD:
[http://www.ubuntu.com/getubuntu/downloadmirrors#alternate](http://www.ubuntu.com/getubuntu/downloadmirrors#alternate)
This is text based Ubuntu install CD that will run better on a PC with just 256mb RAM. It will also avoid any potential problems with the video card. According to the link above though your computer uses nVidia GeForce2 Go 100, which should work ok I would think.
You may want to use the Xubuntu alternate install CD with only 256mb RAM.

And welcome to the Ubuntu forums!!

---

### Post by Hellishcross on 2009-12-06
I have an inspiron 2650 too. Add this to your boot options **acpi=off**. It should boot then.

---

### Post by Hellishcross on 2009-12-10
I tried **acpi=ht** and it seems to work a little better than acpi=off.

---

### Post by tommcd on 2009-12-11
For how to apply those boot options, and many others that you can try, see this:
[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)
Write back if you need more help.

---

### Post by afrodeity on 2010-03-22
You can also try pci=noacpi

---

### Post by afrodeity on 2010-04-15
wondering if any of you 2^50 users with a working install could assist me by dumping the keymap into a file?

see [http://manpages.ubuntu.com/manpages/intrepid/man1/dumpkeys.1.html](http://manpages.ubuntu.com/manpages/intrepid/man1/dumpkeys.1.html)

my keymap is completey kludged and i need to restore it and remap keys using a working keymap

---

### Post by quadproc on 2010-04-15
> **mattevandavis said:**
> I have a Dell Inspiron 2650 that i can not seem to gt running with ubuntu.  i have tried xubuntu too.  when it gets to where the os should load it just has a flashing cursor.  i assume its my video card?

HELP.
I tried Xubuntu with 256 MB of RAM in my old Dell GX110 desktop and it did function.  I did see a lot of things that indicated that it was having troubles, though; programs crashing, failing to run, and so forth.  I believe that the video system I have is Intel but I don't remember which model.

On the other hand, I tried Puppy Linux on that same old machine by means of CDROM and it works well.  In the near future I plan to do some more comprehensive testing of it; if that goes well then I'll apply a "scorched earth" approach to the old OS on its disk and replace it with Puppy.  Puppy is easy to install because it does a lot of hardware probing and automatically configures most things.

Good luck.

quadproc

---

### Post by afrodeity on 2010-04-16
i've created an ubuntu 2650 group for discussion and support issues related to the Dell Inspiron 2650 and Ubuntu

mailto:ubuntu2650laptop@googlegroups.com

---

