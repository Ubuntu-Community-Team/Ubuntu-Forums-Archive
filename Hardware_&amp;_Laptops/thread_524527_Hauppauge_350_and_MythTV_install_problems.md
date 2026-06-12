---
title: "Hauppauge 350 and MythTV install problems"
date: 2007-08-13
forum: Hardware &amp; Laptops
---

### Post by ChasMoe on 2007-08-13
I'm trying to get the PVR-350 TV card and MythTV working without success so far.  Linux seems to detect the card fine since I can do a "cat /dev/video0 > /tmp/blah.mpg" and play the resulting /tmp/blah.mpg in mplayer.

I installed the mythtv metapackage package and I didn't notice any errors.  The problem comes in when I try to run mythtv-setup.  When I try to select the capture card, it doesn't "take".  I try selecting the "MPEG2 -Encoder Card (PVR-x50, PVR-500)" with /dev/video0 and tuner 1 selected.  I then click "Finish".  When I get back to the add capture card screen, the card doesn't exist.

I can't figure out why mythtv-setup won't save the card (or allow me to select the card?).  

Does anyone have any idea how I can get this working or how to figure out what is wrong?

Thanks in advance.

---

### Post by praet on 2007-08-13
Take a look at the excellent howto by Jarod Wilson (for fedora, but still is helpful)
[http://www.wilsonet.com/mythtv/fcmyth.php](http://www.wilsonet.com/mythtv/fcmyth.php)
[http://www.wilsonet.com/mythtv/fcmyth.php#mysql](http://www.wilsonet.com/mythtv/fcmyth.php#mysql)

The official capture card section:
[http://www.mythtv.org/docs/mythtv-HOWTO-9.html](http://www.mythtv.org/docs/mythtv-HOWTO-9.html)

In particular, take a look at the mysql database settings and make sure that you have everything setup right.  mythtv-setup writes all its information to the database.

You will get some more information by running the mythtv-setup from a command line (terminal) and after trying to add your capture card, and failing, see what output/errors show up in the terminal.

---

### Post by ChasMoe on 2007-08-14
I think the problem was a problem with the database.  I followed these steps posted on another thread (unfortunately, I lost who posted and the thread, sorry):

First, get the which pkgs are for mythtv:
```
dpkg --get-selections|grep myth
```

Now, uninstall those packages:
```
sudo apt-get --purge remove mythpackageslistedabove
```

Then remove the mythconverg database and the ~/.mythtv directory
```

mysql -uroot -p
>drop database mythconverg;
>quit
rm ~/.mythtv

```

Now, reinstall what you need.  For example for a frontend, backend setup:
```

sudo apt-get install mythtv-common mythtv-database mythtv-backend mythtv-frontend mythtv-themes

```

Now add yourself to the mythtv group
```

sudo usermod -a -G mythtv youraccountname

```

Lastly, run the setup:
```
mythtv-setup
```

---

### Post by praet on 2007-08-14
Make sure that you have created the mythtvconverg database before running mythtv-setup
Check the second link above for the mysql stuff:
```
$ mysql -u root -p < /usr/share/doc/mythtv-0.20/database/mc.sql
```

There is also the detailed reference at mythtv.org
[http://www.mythtv.org/docs/mythtv-HOWTO-6.html](http://www.mythtv.org/docs/mythtv-HOWTO-6.html)

---

### Post by DanneUK on 2007-08-27
I had the same problem. Linux detected the card. But when I ran mythtv-setup. and  tried to select the capture card, it didn't "take" either. 

Then today I started afresh (and I mean afresh - I reinstalled Ubuntu!)

When I got to the select "MPEG2 -Encoder Card (PVR-x50, PVR-500)" card screen, I cursor-keyed down to the /dev/video0 box and press Enter

It took me back to the add capture card screen, and the card showed up!!

I think before I was choosing all the options, and then clicking Escape to get out of the menu.  Pressing Enter on the /dev/video0 box worked for me, and I really hope it fixes your problem too.

---

