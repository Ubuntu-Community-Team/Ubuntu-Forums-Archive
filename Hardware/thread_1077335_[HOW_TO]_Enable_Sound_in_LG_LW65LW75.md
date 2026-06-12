---
title: "[HOW TO] Enable Sound in LG LW65/LW75"
date: 2009-02-22
forum: Hardware
---

### Post by bluryfusion on 2009-02-22
As detainer of this laptop model, you already should know, this LG laptop model always had some issues to enable speakers over linux.

So, and after try many diferent ways, and searching in to many forums, this included, i found a working solution to the problem.

I tried this on a ubuntu clean instalation, but it should work in every linux instalations.

First of all you should download some alsa archives, the essential ones, are alsa-driver and alsa-lib:
```
wget ftp://ftp.alsa-project.org/pub/driver/alsa-driver-1.0.22.tar.bz2 ftp://ftp.alsa-project.org/pub/lib/alsa-lib-1.0.22.tar.bz2
```

Then, you need some packages from ubuntu repositories, i needed this ones (libncurses5 libncurses5-dev xmlto patch gettext) but you could need some more, use google and some good sense to find them:
```
sudo apt-get install libncurses5 libncurses5-dev xmlto patch gettext
```

Now, we need to unpack the tarballs dowloaded and install it:
```
tar -xf alsa-driver*.tar.bz2 && cd alsa-driver*/ && ./configure && make && sudo make install && cd .. && rm -r alsa-driver*/
tar -xf alsa-lib*.tar.bz2 && cd alsa-lib*/ && ./configure && make && sudo make install && cd .. && rm -r alsa-lib*/
```

You should get no errors.

Now we need to use alsaconf, alsaconf doesn't come anymore with ubuntu, so we need to compile it.

Now to compile alsa-utils, just run, as before:
```
wget ftp://ftp.alsa-project.org/pub/utils/alsa-utils-1.0.22.tar.bz2
tar -xf alsa-utils*.tar.bz2 && cd alsa-utils*/ && ./configure && make && sudo make install && cd .. && rm -r alsa-utils*/

```

With Karmic, if you have some issues with panelw libraries, you need to create this simbolic links:
```
sudo ln -s libpanelw.so.5 /usr/lib/libpanelw.so
sudo ln -s libformw.so.5 /usr/lib/libformw.so
sudo ln -s libmenuw.so.5 /usr/lib/libmenuw.so
sudo ln -s libncursesw.so.5 /lib/libncursesw.so
```

Now, just run alsaconf:
```
sudo alsaconf
```

This normally is a normal next, next, next configuration, but you could always change some parameters, if you know what you're doing.

Now, you should add your model to alsa configuration file, in lg lw series, the model is minimal, because they use c-media cards, instead of realtek, but you need to set the permissions before:
```
sudo chmod 666 /etc/modprobe.d/alsa-base.conf
```

Then edit the configuration file:
```
sudo gedit /etc/modprobe.d/alsa-base.conf
```

Comment the line:
```
[COLOR="Red"]#[/COLOR] options snd-hda-intel power_save=10 power_save_controller=N
```

And add this line:
```
options snd-hda-intel probe_mask=1 model=minimal
```

then reset the permissions:
```
sudo chmod 444 /etc/modprobe.d/alsa-base.conf
```

Then, force alsa to reload to enable sound:
```
sudo alsa force-reload
```

After configuring all, and running alsaconf, you should run alsamixer, and place all volumes unmute, shourtcut is 'm', after change to desired channel.
```
alsamixer
```


After that, test speakers, if everything is ok, you should hear now your speakers again like in windows old times (Ctrl+C to stop):
```
speaker-test -c2
```

If it doesn't work, reboot your system, and repeat the last 2 steps.

Some issues more, use this post to get your answers.

Tested in Hardy, Intrepid (with some issues compiling alsaconf), Jaunty and Karmic(use [this]("http://ubuntuforums.org/showthread.php?t=1292587") to compile alsa-utils on karmic if you still have problems).

---

### Post by skwex on 2009-06-23
Thanks you first of all, now the sound is working.
To be able to control the sound via computer buttons what should I do?

Thanks

---

### Post by bluryfusion on 2009-07-04
> **skwex said:**
> Thanks you first of all, now the sound is working.
To be able to control the sound via computer buttons what should I do?

Thanks

To control the volume with laptop volume buttons, you should right click on sound icon, next near the clock and choose settings, then set the device to control to HDA Intel (alsa mixer) and the channel PCM.

Now you should be able to control the sound with laptop buttons.

---

### Post by kingangel on 2009-11-10
After updating to karmic the sound was gone. Following to instructions (it was used alsa 1.0.21a) has not solved a problem. "speaker-test-c2" the sound is audible, in programs - silence, the list of sound cards in options is empty

---

### Post by bluryfusion on 2009-11-10
> **kingangel said:**
> After updating to karmic the sound was gone. Following to instructions (it was used alsa 1.0.21a) has not solved a problem. "speaker-test-c2" the sound is audible, in programs - silence, the list of sound cards in options is empty

I tested it on a clean installation of karmic, had some issues with volume keys on laptop, and it doesn't login with sound on, but if you can change it with alsamixer, and unmute them again, it will work.

Your problem, is probably with the alsa (i have some, described above), but if you configure the programs manually to use alsa, instead of system sound, out oss, it should work, in amarok, by example, i use xine-ui, as engine, output HDA Intel (CMI9880), and it works normal.

Found some [other working solution](http://ubuntuforums.org/showthread.php?t=1316634), i test it after the steps i described before, so i don't know the fewer steps to get it working on karmic, but you may test it, worked for me with a fewer alteration on snd-hda-intel to **minimal** model instead of hp.

---

### Post by kingangel on 2009-11-10
I have tried this variant and a sound have returned to system

/etc/modprobe.d/alsa-base-conf
[COLOR=Red]**#**[/COLOR] options snd-hda-intel power_save=10 power_save_controller=N
options snd-hda-intel probe_mask=1 model=allout

---

