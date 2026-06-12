---
title: "how to downgrade ubuntu?"
date: 2008-12-04
forum: Installation &amp; Upgrades
---

### Post by merlin666 on 2008-12-04
I was quite happy with Hardy, except that I was not able to get wireless to work. After reading reports about improved wireless I took the plunge of upgrading to 8.10 ) which did not go as well as going from 7.10 to 8.04. Anyway, Intrepid is not working out for me because:

[LIST]
[*]it takes considerably longer to boot than  Hardy or even XP
[*]no support for my ati mobility radeon card - fglrx kills xserver, and the display is choppy at best
[*]cursor/arrow keys do not work
[*]still no wireless
[/LIST]

I really would like to go back to reliable and functional 8.04 - can this be done without a clean install?

---

### Post by jenkinbr on 2008-12-04
I don't think so.  I think that making a backup of any personal files would be nessesary, then doing a fresh install is the way to go.

Wait around and see what others have to say, becasue I've been wrong before...

---

### Post by merlin666 on 2008-12-04
Now I don't even know how to make a clean install to be honest. A few years ago I started with one of the distribution CDs and since then have dist-upgraded. In the meantime my optical drive has stopped working so I am also wondering how to install without access to a CD drive.  My internet connection is also fairly slow - the upgrade to Intrepid took more than 30 hours, but I'm certainly willing to invest another couple of days to get a solid system back.

---

### Post by StooJ on 2008-12-04
I don't think you can downgrade either, so your best bet would be to reinstall.

Backup the contents of your home directory (including the hidden folders) first. You don't have to restore it all when you have finished reinstalling if you're not wanting to, but it's nice to know it's all available.

If your CD drive is dead, you can still install using a USB drive instead.
[https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)

---

### Post by sstusick on 2008-12-04
> **jenkinbr said:**
> I don't think so.  I think that making a backup of any personal files would be nessesary, then doing a fresh install is the way to go.

Wait around and see what others have to say, becasue I've been wrong before...
That's what I would do.

---

### Post by jerrykenny on 2008-12-04
Merlin i would really stick with your intrepid installation.

re Bootup times . . . try a custom kernel, got the source from kernel.org, or from ubuntu.  Bootup times will be much faster.

Keypad . . . should be accessible in the settings-preferences or administration section.

Wireless . . . probably needs the right firmware, usually "linux-restricted-modules" is the best bet.

Video . . . you probably need a decent xorg.conf file . . . Intrepid seems to have a very minimal xorg.cong, but if you can retrieve your old xorg.conf file from Hardy (from a backup ?) you could just try it out on intrepid

---

### Post by Mark Phelps on 2008-12-05
Just to set the record straight, it CAN be done -- but it's extremely hard to do and involves a great deal of low-level package manipulation.  If you're not comfortable compiling your own kernel, it should not even be attempted.

As others have said, re-install is really your only option.

Suggestion for the future is to check into backing up your Linux installation to an external drive so that, if you run into problems like this, you can restore from backup.  I use an app known as P.I.N.G (PartImage is Not Ghost) a front end for PartImage.  You might want to check that out as it is free, and will allow you to backup and restore your linux partitions.

---

### Post by mkvnmtr on 2008-12-05
I have always done reinstalls. But before you do anything I believe that if you have done upgrades then all those old kernals are still on your system. I am sure I have read in the forums that you can boot from an old one I just don't remember how because I never had to do it.  That might be your solution until 8.10 is ready for you.

---

### Post by merlin666 on 2008-12-05
> **mkvnmtr said:**
> I have always done reinstalls. But before you do anything I believe that if you have done upgrades then all those old kernals are still on your system. I am sure I have read in the forums that you can boot from an old one I just don't remember how because I never had to do it.  That might be your solution until 8.10 is ready for you.

Thank you for all the suggestions. I have a long list of kernels in the menu.lst, but I don't see how that would make a difference. But will give it a try when I get home.

BTW, editing the menu.lst to out-comment the old kernels was an arduous task without arrow keys. There is a bug report with some solutions, but none of them have worked for me thus far.

As for xorg.conf, I doubt an old one would be usable because I had fglrx in Hardy. When I install fglrx now, xserver does not start and I am left with tty. I am using the ati driver which is quite choppy, but at least I have a GUI.

I like the idea of booting from USB, unfortunately my laptop does not have a USB boot option in the BIOS. I am seriously considering getting a new optical drive, though (little xmas gift to myself).

---

### Post by jyaan on 2008-12-05
I would try using an older kernel. The newest one seems rather buggy (it doesn't work properly for me). When booting, press ESC and select an older kernel. Hopefully you have another 2.6.27; other problems might pop up with an even older version.

---

