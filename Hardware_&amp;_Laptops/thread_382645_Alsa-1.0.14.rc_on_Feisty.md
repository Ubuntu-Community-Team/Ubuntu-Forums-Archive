---
title: "Alsa-1.0.14.rc* on Feisty"
date: 2007-03-12
forum: Hardware &amp; Laptops
---

### Post by t0m_ on 2007-03-12
Hello,
I run Kubuntu Feisty on my laptop (HP dv6242ea), and i have some issues related to Alsa. My Conexant HDA chipset is not well supported by the current Alsa version : my headphones doesn't work correctly (well, in fact i don't really care about that) and the microphones doesn't work at all. I really need to make the (external or internal) microphone work so I hope that upgrading Alsa will fix theses issues. It seems that Alsa-1.0.14-rc(1 or 2) fixes at least the headphones issue ([http://ubuntuforums.org/showthread.php?t=358001&page=3)](http://ubuntuforums.org/showthread.php?t=358001&page=3)).

According to [this bug report]("https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/76741"), Alsa-1.0.14.* was commited in git but i think it hasn't been released in the official Feisty tree. Does anyone know why? 

I've found a few howtos about compiling Alsa on Ubuntu but i'm a bit worried about compiling Alsa-1.0.14 over the Ubuntu version.:s
Actually it tried a french (yeah i'm french) howto which broke my Ubuntu. I want to try to do it again (because i really need to fix these issues) but this time i would like to upgrade it in a proper way.
Do you know howtos or means to upgrade Alsa correctly?
Alsa-1.0.14rc* is available in experimental Debian packages. Is backporting these packages a proper way to install an new Alsa version? 

Thank you. ;)

---

### Post by silas_irl on 2007-03-12
Actually I just installed the Alsa-1.0.14rc3 sources last night to fix the headphone issue (I have a HP Pavilion DV2197ea).  It also fixes the microphone issue as well.```

```

There's a page here that tells you how to do it, can't find it right now.  If you do a good search for "Headphone jack" it should pop up.

I'm afraid if you're looking for a nice .deb package that you can get to install with apt-get, then you're going to have a wait until 14rc3 comes out of rc, and ubuntu support it as a package in their repository.  Since they're at rc3 at the moment, this might be soon enough for the official release of Feisty or slightly after it.

If you are interested in installing the source packages, you need the driver, lib and utils archives .  Grab them from the [http://www.alsa-base.org/](http://www.alsa-base.org/). You basically install them like so: 
> 
# For the driver source, for the other packages just use ./configure, make, sudo make install
# decompress the archives and cd into the folder...
# and don't issue a make install if make returned any errors.
./configure --with-oss=yes --with-sequencer=yes --with-kernel=/lib/modules/`uname-r`/build
make
sudo make install

If any of the above breaks the system, then a simple sudo make uninstall from the folder the repective makefile is in, will remove the installation from the system.  Then just reinstall the old package from your CD or wherever it's handiest.

If you do install from source then be aware that the package manager will still think it's using the old alsa driver package.  But alsamixer will have new options for microphones and a separate PCM level.

---

### Post by t0m_ on 2007-03-12
> **silas_irl said:**
> Actually I just installed the Alsa-1.0.14rc3 sources last night to fix the headphone issue (I have a HP Pavilion DV2197ea).  It also fixes the microphone issue as well.
That's great! I hope it will works for me too. 
So I will try to compile it soon. ;)

> **silas_irl said:**
> 
If any of the above breaks the system, then a simple sudo make uninstall from the folder the repective makefile is in, will remove the installation from the system.  Then just reinstall the old package from your CD or wherever it's handiest.
Yes but in my case, it wasn't booting anymore. There was an issue during the modules loading. I will inquire about that to make it work correctly.

Thank you very much for your reply.

If anyone else has extra information, it would be great. ;)

---

### Post by mikewhatever on 2007-03-12
[https://help.ubuntu.com/community/HdaIntelSoundHowto?highlight=%28hda%29](https://help.ubuntu.com/community/HdaIntelSoundHowto?highlight=%28hda%29)

Had solved the microphone issue on HP 5269ea.

---

### Post by t0m_ on 2007-03-12
Thank you a lot!
It looks good : there is a part about the issue I had! I'll try it as soon as possible.

The following threads seem interesting too : 
- [http://ubuntuforums.org/showpost.php?p=2277145&postcount=13](http://ubuntuforums.org/showpost.php?p=2277145&postcount=13)
- [http://ubuntuforums.org/showthread.php?t=381795&highlight=alsa+mic](http://ubuntuforums.org/showthread.php?t=381795&highlight=alsa+mic)

:) 

Thank you.

---

### Post by pixeldotz on 2007-03-13
seems nobody listens to useful threads anymore :(

i made two threads on this very issue a few days ago but within minutes they are pushed 3 pages back.

my many unanswered posts.
[http://www.ubuntuforums.org/search.php?searchid=16184706](http://www.ubuntuforums.org/search.php?searchid=16184706)

the first one concerning the conexant chip - tobin davis released a patch for alsa1.0.14.rc3 that fixes mic and adds better support for sound with the hda-intel CONEXANT 5045 chip which is what i have in my laptop.

here's my unanswered post made so people with this chip would realize a patch was out.
[http://www.ubuntuforums.org/showthread.php?t=381795](http://www.ubuntuforums.org/showthread.php?t=381795)

luckily tobin emailed me back with step by step instructions on patching ALSA with his patch.

the other is concerning unbootable systems after an ALSA install. here's the thread i wrote explaining in detail how to come back from an unbootable system.
[http://www.ubuntuforums.org/showthread.php?t=379316](http://www.ubuntuforums.org/showthread.php?t=379316)

hopefully this helps you with your card.

---

### Post by t0m_ on 2007-03-14
Thank you for these links. ;)

Can you share the instructions on patching Alsa please? It would be great, thank you in advance. ;)

---

### Post by pixeldotz on 2007-03-14
sure thing. i'll re-write some of tobins instructions since alot of them are not needed anymore.

open a terminal.

backup your current driver.
```

tar -zcvf original-drivers.tgz /lib/modules/`uname -r`/kernel/sound
```

remember everything gets tossed into your /home/ directory.

now in the same terminal do.

```
wget ftp://ftp.alsa-project.org/pub/driver/alsa-driver-1.0.14rc3.tar.bz2
```
then
```
wget http://members.dsl-only.net/~tdavis/alsa-patches/conexant-latest-rc3.patch
```
then
```
wget http://members.dsl-only.net/~tdavis/alsa-patches/conexant-test19a.patch
```
then
```
tar -jxf alsa-driver-1.0.14rc3.tar.bz2
```

what this does is download all necessary files into your /home directory and extracts alsa rc3

now back in the terminal do
```

cp conexant-latest-rc3.patch alsa-driver-1.0.14rc3/alsa-kernel
```

then
```

cp conexant-test19a.patch alsa-driver-1.0.14rc3/alsa-kernel
```

this copies the conexant-latest-rc3.patch and conexant-test19a.patch into the alsa kernel folder

next

```
cd alsa-driver-1.0.14rc3/alsa-kernel
```

then

```
patch -p1 < conexant-latest-rc3.patch
```

then

```
cd ../../
```

last we backup alsa with the following code. this will be our base for patching.

```
tar -jcvf alsa-driver-1.0.14rc3_patched_latest.tar.bz2 alsa-driver-1.0.14rc3
```

and that's the patch to bring rc3 up to speed. now onto the actual patch :shock: 

**conexant-test19a.patch** was copied into the /alsa-kernel directory earlier so it should still be there.

again in your terminal

```
cd alsa-driver-1.0.14rc3/alsa-kernel/pci/hda
```

then

```
cp patch_conexant.c patch_conexant.c-base
```
this backups for patch testing.

onto

```
cd ../../
```

then

```
patch -p1 < conexant-test19a.patch
```

then

```
cd ..
```

then

```
./configure --with-debug=detect --with-cards=hda-intel --with-oss=yes --with-sequencer=yes
```

then

```
make
```

then

```
sudo make install
```

then

```
sudo depmod -a
```
this will update kernel dependencies

then

```
sudo dmesg -c >/dev/null
```
this will clear dmesg prior to loading the new driver

and that should be it. logout. reboot. login.

---

### Post by t0m_ on 2007-03-14
Ok it works !!!!!!!! That's so great : my headphones and my microphones work!!!!

Thank you a lot!! Thank you a lot!!  Thank you a lot!!

So i used [this howto]("https://help.ubuntu.com/community/HdaIntelSoundHowto?highlight=%28hda%29") expect for the alsa-driver. For this part, i used what pixeldotz wrote above.

Maybe, it will be great to add the pixeldotz's explanations on the wiki.

---

### Post by wonkycyber on 2007-03-16
hey; I get a 404 error when I try to wget  "conexant-test19a.patch" ; the  URL is "http://members.dsl-only.net/~tdavis/alsa-patches/conexant-test19a.patch", ritght? I've gotten the other files without a problem, but this one doesn't seem to be online. Can you someone reupload it somewhere, or am I doing something wrong? I'm a bit of a n00b, but I'd really like to try and get my headphones and external speakers working for my e1705.

---

### Post by t0m_ on 2007-03-16
I've just reuploaded it : [http://www.mediafire.com/?ctwyi0tnmzy](http://www.mediafire.com/?ctwyi0tnmzy)

Have fun. ;)

---

### Post by wonkycyber on 2007-03-16
Hey, thanks sir.

I'm a bit new with screwing with Linux, myself, though I've enjoyed using it for two or three years. Anyway, I've started following this tutorial, but as I'm actually cursed when it comes to working with technology, I ran into a problem fairly early on. 

~$ cp conexant-latest-rc3.patch alsa-driver-1.0.14rc3/alsa-kernel
~$ cp conexant-test19a.patch alsa-driver-1.0.14rc3/alsa-kernel
~$ cd alsa-driver-1.0.14rc3/alsa-kernel
~/alsa-driver-1.0.14rc3/alsa-kernel$ patch -p1 < conexant-latest-rc3.patch
can't find file to patch at input line 3
Perhaps you used the wrong -p or --strip option?
The text leading up to this was:
--------------------------
|--- pci/hda/patch_conexant.c.orig      2007-03-15 10:24:21.000000000 -0700
|+++ pci/hda/patch_conexant.c   2007-03-15 10:26:40.000000000 -0700
--------------------------
File to patch:

so, um, whatdoI put here?

---

### Post by singularterm on 2007-03-16
Thanks for the useful discussion (also pertinent to what I'm trying to do).  

However, your instructions stopped working at the same point for me (although with a different error).

Any suggestions?

---

### Post by singularterm on 2007-03-16
Oops.  Found my mistake with that one; but am now getting the same error.

---

### Post by t0m_ on 2007-03-18
Linux headers or source may be required to patch and compile alsa-kernel. ;)

---

### Post by singularterm on 2007-03-18
Now, using the aforementioned recipe, I've got the microphones working, external speakers working and the microphone jacks at least producing sound.

How did you get the external speakers to mute when the headphones are plugged in though?  Any advice on this one would be most appreciated.

---

### Post by t0m_ on 2007-03-19
There is a patch about that in one of the latest Ubuntu kernel (linux-image-2.6.20-10 i think). ;)

---

### Post by pixeldotz on 2007-04-03
after compiling alsa from rc2 (i beleive) the headphones just auto mute when headphones are installed.

with rc3 and test19a.patch you have to press the mute button 2 times i think. sorry i'm not at my laptop right now.

i'll find out for sure when i get home tonight.

---

### Post by pixeldotz on 2007-04-03
one thing i might've forgot to mention.

i think you need the linux build essentials package to be able to patch and compile without getting any errors.

---

### Post by Walkboss on 2007-07-17
I realize this topic is a bit old, but I am having some issues applying Tobin Davis' patch to any of the alsa drivers. I've tried RC3 and the final version available via alsa's website. When I follow the instructions listed on pg. 1, I get to the second patching and it says it is already patched. If I try to patch it, it says * of * HUNKS FAILED. I've tried skipping the second patch and ignoring the "HUNK" error. Both solutions leave me with no audio at all.

I've managed to install all the latest stable versions (1.0.14) of alsa-driver, lib, and utils, but the "jack sense" still does not seem to be working.

I've been searching and compiling and recompiling for over five straight hours.

Please assist!

---

### Post by Walkboss on 2007-07-25
Bump...

Pretty please?

---

### Post by hammer v2 on 2007-09-18
Hey man, I found the alsa drivers all debbed up here..
check it out...
H.

---

### Post by hammer v2 on 2007-09-18
oops!

here's the link
[http://falcon.landure.fr/dists/feisty/alsa/](http://falcon.landure.fr/dists/feisty/alsa/)

---

