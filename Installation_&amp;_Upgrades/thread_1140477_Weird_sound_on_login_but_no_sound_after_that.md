---
title: "Weird sound on login but no sound after that?"
date: 2009-04-27
forum: Installation &amp; Upgrades
---

### Post by DaneGrinder on 2009-04-27
Hi experts

I'm new to Linux and I'm having a sound problem.

Laptop: HP DV7/Intel/Nvidia. The newest Ubuntu (9.04 I think)

I can see others have problems with the sound too, but it seems I have a different problem.

On the Login screen I kind of have sound. It sounds like bongo drums beeing hit rapidly, This works both on the internal speakers and on the headphone jack.

BUT, as I said, it doesn't sound right and after login, I have NO sound.

Anybody that can help me?

---

### Post by DaneGrinder on 2009-04-28
Nobody ? :(

Please don&#7831; make me go back to windows ](*,)

---

### Post by adm1968 on 2009-04-28
[FONT="Georgia"]If you search for "no audio" or similar stuff, you'll see that this seems to be a major bug for 9.04

I have no sound either
Good luck![/FONT]

---

### Post by DaneGrinder on 2009-04-28
Yes I know (have searched), BUT the thing is, I HAVE sound !!! Both on the internal speakers and the headphone jack.

I just don't have working sound :confused:

---

### Post by cbender on 2009-05-02
Ok, i had the same Problem, I'm using the same Notebook.
Everything else works fine...

Here's the solution. Maybe you have to repeat it after a kernel update or so, so make sure you bookmark this Page or save it elsewhere :)

Open the alsa config-file

```
sudo gedit /etc/modprobe.d/alsa-base.conf
```

Add the following line to the end of the file

```
options snd-hda-intel model=hp-m4 enable_msi=1
```

Reboot and have fun!

---

### Post by Jakovasaur on 2009-05-20
@cbender

You are a champ sir; the line:

options snd-hda-intel model=hp-m4 enable_msi=1
Did the trick! :p

---

### Post by jdunn on 2009-05-24
Thanks cbender.  That worked for me.
However, the mic doesn't work now...This is a minor issue I can live with until 9.10 is out.  BTW, my laptop is an HP Pavilion v5

---

### Post by teapottvroof on 2009-09-12
Unfortunately this did not work for me. I have a hp pavilion dv3-2007tx
and I have no audio when running Ubuntu.

---

### Post by Walpy on 2011-02-28
> **teapottvroof said:**
> Unfortunately this did not work for me. I have a hp pavilion dv3-2007tx
and I have no audio when running Ubuntu.

Same problem here,
I installed Ubuntu 10.04 on my HP G62.

This did the thing for me

```

~$ sudo aptitude update
~$ sudo aptitude install linux-backports-modules-alsa-lucid-generic

```and reboot!

Should be working

(found the solution here: [http://www.uluga.ubuntuforums.org/showthread.php?t=1570060](http://www.uluga.ubuntuforums.org/showthread.php?t=1570060))

---

