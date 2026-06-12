---
title: "Dvds Will Not Play On Totem"
date: 2008-05-09
forum: Hardware
---

### Post by Chris2691 on 2008-05-09
I have a Dell Inspiron 1720 laptop with a Blu-ray DVD burner. I can play CDs OK but when I try ordinary standard DVDs with Totem I get the message "An error occurred". "Could not read from resource". I have not even attempted playing a Blu-ray disk. I have no problems in Windows Vista playing either Blu-ray or DVD discs.

Has anyone got some advice for me on how to fix this.

Thanks

Chris

---

### Post by hermes0710 on 2008-05-09
First, add medibuntu reporitories (for hardy i guess):

```
sudo wget http://www.medibuntu.org/sources.list.d/hardy.list -O /etc/apt/sources.list.d/medibuntu.list
wget -q http://packages.medibuntu.org/medibuntu-key.gpg -O- | sudo apt-key add - && sudo apt-get update
```

Then install:
```
sudo apt-get install libdvdcss2 w32codecs
```

Try reading the dvd through another application like kaffeine or mplayer ```
sudo apt-get install kaffeine mplayer
``` if you don't have it already

---

### Post by Chris2691 on 2008-05-09
when i enter sudo apt-get install libdvdcss2 w32codecs I get the following message
"Package libdvdcss2 is not available, but is referred to by another package. This may mean that the package is missing, has been obsoleted, or is only available from another source."

---

### Post by hermes0710 on 2008-05-09
That's strange... Try libdvdcss without "2"...

Check this out:

[https://help.ubuntu.com/community/Medibuntu]("https://help.ubuntu.com/community/Medibuntu")

---

### Post by ubuntu-freak on 2008-05-09
You're running Hardy yeah? Take a look at my [sticky](http://ubuntuforums.org/showthread.php?t=766683) and complete at least part 1 and 4.
 
Nathan

---

### Post by bilbo.san on 2008-05-09
Hey,
You should try installing ELISA media center
Go to Add/Remove programs and look for it, select it and install it.
or go to [http://elisa.fluendo.com/](http://elisa.fluendo.com/)

That should work.
Let me know
b.

---

### Post by browneej on 2008-05-18
I have the exact same problem.  Were you able to figure it out?

Neither mplayer, totem, nor vlc will play my dvd's, although I can see the contents from nautilus or bash just fine.  xine will momentarily start the dvd then tell me I may not have enough permissions.  I have verified that my account is part of the cdrom group, and checked the properties on scd0 using nautilus.

Using a DVD-ROM in place of my Blu-Ray and everything is (mostly) fine--I've watched two movies that way, although I get an initial error message from mplayer.

Deeper background:  I could not even install Hardy with the Blu-Ray--the live cd's ended at an initramfs> prompt, and the alternate cd's failed verification each time.  To ease your mind, so did Mythdora 5.0.  I went through many cds and checked the MD5 sums multiple times to verify the cd's weren't actually corrupted.

I had installed Ubuntu 7.10 and earlier multiple times with this blu-ray drive.  WHen I first attempted to install Hardy, I was eventually forced to install 7.10 then upgrade.

thanks
browneej

---

