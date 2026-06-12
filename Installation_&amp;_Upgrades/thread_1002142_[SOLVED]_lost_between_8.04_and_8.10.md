---
title: "[SOLVED] lost between 8.04 and 8.10"
date: 2008-12-04
forum: Installation &amp; Upgrades
---

### Post by clearwood on 2008-12-04
Dear ubuntu supporters/users

While upgrading my portable pc from 8.04 to 8.10, the wireless dropped out and now there is no 'upgrade to 8.10' showing in the update manager. 

I sat up 'software sources' for 'normal', then started the upgrade and when it was 'fetching ...' the connection wireless was lost. 

Can anyone give some advice on where to start? So that I can start over the upgrade.

And I will use the wire the next time:)

Thank you

---

### Post by Therion on 2008-12-04
```
sudo apt-get update
sudo apt-get dist-upgrade
```

---

### Post by clearwood on 2008-12-04
Thank you. But I am still unable to upgrade to 8.10 from th update manager.

---

### Post by clearwood on 2008-12-05
Maybe there is some other comand line solution?

---

### Post by clearwood on 2008-12-05
If there was just some way to 'undo' what was done right before it was beginning to fetch...

---

### Post by zvacet on 2008-12-05
First check that you have interpid repos in your source list.You can do that with

```
cat /etc/apt/sources.list
```

If you still have **hardy **repos** replace it** with **interpid** like this

deb [http://hr.archive.ubuntu.com/ubuntu/](http://hr.archive.ubuntu.com/ubuntu/) hardy main restricted

to 

deb [http://hr.archive.ubuntu.com/ubuntu/](http://hr.archive.ubuntu.com/ubuntu/) interpid main restricted

```
gksudo gedit /etc/apt/sources.list
```

Make that changes in every line and when you are finish save and close file.
In terminal type


```
sudo apt-get update && sudo apt-get dist-upgrade && sudo apt-get dist-upgrade
```

```
sudo apt-get update && sudo apt-get dist-upgrade
  sudo apt-get -f install
  sudo dpkg --configure -a 
```

Reboot

---

### Post by clearwood on 2008-12-07
Hi zvacet

I thank you for your suggestion but...

I did what you suggested. with correcting the misspelling from interpid to intrepid.
Now I cannot boot the partition. It just shows an orange screen after logging in.

How do I mount the partition from the other ubuntu install that I have? I just want to rescue some files that I forgot to back up :)

Then I guess I'll do reinstall from a DVD that should be out from Linux-magazine. Maybe after accessing the partition from a live distro.

Or unless someone has a good idea.

Best regards

---

### Post by clearwood on 2008-12-07
OK thank you zvacet :)

Now it's working after I went into failsafe mode and chose repair packages.

So know I'm happy. I kan see that the system is upgraded. But where or whith what comand do I see that this is really 8.10?

I take it that it is 8.10 :popcorn:following the new graphic design.

---

### Post by zvacet on 2008-12-08
```
lsb_release -a

```

P.S. Sorry for misspelling.I´m not native English speaker.

---

