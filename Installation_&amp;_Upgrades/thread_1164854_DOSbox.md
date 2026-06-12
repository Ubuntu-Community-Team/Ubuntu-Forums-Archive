---
title: "DOSbox"
date: 2009-05-20
forum: Installation &amp; Upgrades
---

### Post by nickyn on 2009-05-20
Does anyone know where I could locate a DOSbox that would wourk with Ubuntu Linux?  On the DOSbox website, there is a download for Gentoo Linux...would that work on Ubuntu?
Or does anyone know of another DOS emulator, or Sierra game emulator I could download?  (I've got a hankering to play some games from my childhood.)

Thanks!

---

### Post by Kevbert on 2009-05-20
Please take a look at [[COLOR="Red"]this.[/COLOR]]("https://help.ubuntu.com/community/DOSBox")

---

### Post by nickyn on 2009-05-20
Oh, thank you!

---

### Post by nickyn on 2009-05-20
Okay, so, I'm going to be a bother again, and I'm terribly sorry.  I did all the repository stuff and installed the DOSbox...but it won't let me create a C:/
I type this in, like the instructions say:
> nicky@nicky-laptop:~$ mkdir ~/dos/c
And it says to me:
> mkdir: cannot create directory `/home/nicky/dos/c': No such file or directory
So then, I make a file there, and it says:
> mkdir: cannot create directory `/home/nicky/dos/c': File exists

I don't know what to do with this.  I believe I might be in over my head...maybe.

---

### Post by Kevbert on 2009-05-20
In terminal, please try 
```
rm ~/dos/c
mkdir ~/dos
cd dos
mkdir c
```
that will make a directory /home/nicky/dos/c
If you have any further questions please ask.

---

### Post by nickyn on 2009-05-20
Thank you!  I got it to work...one question, though, do I have to mount the C: everytime I use DOSbox, or will it stay mounted and I will only have to type C: in?  Thanks!

---

### Post by Kevbert on 2009-05-21
As far as I know you have to do this each time you run DOSbox, it may be possible to get around this with a bash script (but I'm not sure how to do this). 
The other thing you may want to do is run either ClamAv or BitDefender regularly as you may find you get a few Windows/DOS viruses (especially if you download games from the web). These viruses will only affect any Windows/DOS files that you have on the PC and not any Linux files. This is very important to do if you use shared partitions for data and are dual booting with any version of Windows.

---

### Post by rCXer on 2009-05-21
> **nickyn said:**
> Thank you!  I got it to work...one question, though, do I have to mount the C: everytime I use DOSbox, or will it stay mounted and I will only have to type C: in?  Thanks!

DOSBox can automatically mount drives at startup. To do this you have to create a configuration file.

Run DOSBox and type the following into its prompt...
```

config -writeconf dosbox.conf

```

This will create a configuration file, dosbox.conf, in /home/nicky/. Open dosbox.conf, scroll down the bottom and add the following as shown in red...
```

[autoexec]
# Lines in this section will be run at startup.
[COLOR="Red"]mount c "/home/nicky/dos/c"
c:[/COLOR]

```

Now DOSBox will always mount c as your folder and switch to it.

---

### Post by nickyn on 2009-05-26
Thanks you two, that was really helpful!

---

