---
title: "is xubuntu too much for 500mhz AMD geode umpc with 512mb of ram ? slow, no videos"
date: 2009-09-06
forum: Hardware
---

### Post by bjaz on 2009-09-06
hello all

i installed xubuntu jaunty on a 500mhx amd geode mini pc, with 512mb of ram, thinking it would run fine, yet to my surprise it is quite slow (firefox pages take ages to load) and not powerful enough to run a video through vlc, or stream a you tube flash movie

it:'s a big letdown. but i'm thinking maybe something is setup wrong. can anyone help ?
the manufacturer, kohjinsha, has issued linux drivers, which i downloaded, but i don't know what to do with them, how to install them

i really hope someone can help

thanks

ben

---

### Post by aysiu on 2009-09-06
Although Xfce (the desktop environment Xubuntu uses) is lighter than Gnome or KDE, it is still a full desktop environment.

If you find that too heavy, you can always use a lightweight window manager like IceWM, Fluxbox, OpenBox, or Enlightenment.

Here is a short guide to IceWM:
[http://www.psychocats.net/ubuntu/icewm](http://www.psychocats.net/ubuntu/icewm)

---

### Post by aysiu on 2009-09-06
Although Xfce (the desktop environment Xubuntu uses) is lighter than Gnome or KDE, it is still a full desktop environment.

If you find that too heavy, you can always use a lightweight window manager like IceWM, Fluxbox, OpenBox, or Enlightenment.

Here is a short guide to IceWM:
[http://www.psychocats.net/ubuntu/icewm](http://www.psychocats.net/ubuntu/icewm)

---

### Post by fela on 2009-09-06
Yes, Xubuntu is too much for that.

Run debian with a lightweight window manager.

---

### Post by blazemore on 2009-09-06
Is it a Vye?
I'd really recommend Crunchbang. I've run Crunchbang on one before, succesfully. it even runs Firefox!
From their website:
> CrunchBang Linux is an Ubuntu based distribution offering a great blend of speed, style and substance. Using the nimble Openbox window manager, it is highly customisable and provides a modern, full-featured GNU/Linux system without sacrificing performance.
[http://crunchbanglinux.org/](http://crunchbanglinux.org/)

---

### Post by bjaz on 2009-09-06
thanks for your answers, it's a 2008 second hand kohjinsha SA1F00,
don't get me wrong, xcfe is useable, if slightly slow, especially scrolling web pages in firefox.. i'm just surprised that it's not possible to read a movie file, since it was possible on the original windows xp version (which doesn't boot anymore)

i was thinking that maybe something was badly setup, as explained in this thread 
[http://ubuntuforums.org/showthread.php?t=1256960](http://ubuntuforums.org/showthread.php?t=1256960)

khojinsha has issued drivers for linux for this model, though i'm not sure what to do with them 
[http://www.kohjinsha.com.sg/products/drivers.htm](http://www.kohjinsha.com.sg/products/drivers.htm)

tonight i managed to stream some adsl tv in vlc on this machine, but it seems that youtube'se java and regular avi movie files won't work, which is a little surprising.

the rest seems fine. i haven't been able to fix the proper video definition though, and i really thimk this might be linked to the setup, since the machine was pretty much able to handle movie files on windos xp

here's some info on the machine

[http://www.engadget.com/2006/11/06/kohjishas-sa1f00-better-and-cheaper-than-a-umpc/](http://www.engadget.com/2006/11/06/kohjishas-sa1f00-better-and-cheaper-than-a-umpc/)

[http://www.kohjinsha.com.sg/products/sa1f00ks.htm](http://www.kohjinsha.com.sg/products/sa1f00ks.htm)

[http://www.biztoolbelt.com/2006/12/kohjinsha_sa1f00_umpc.html](http://www.biztoolbelt.com/2006/12/kohjinsha_sa1f00_umpc.html)

mine is a  non-touch screen japanese one, with a 500mhz amd geode processor.

i'm also wondering how i can access the two ntfs partitions that windows was installed on.
i haven't managed to reinstall windos so i might reformat them

---

### Post by binbash on 2009-09-06
I also recommend CrunchBang for that box.

---

### Post by Rockbuster on 2009-09-06
hate to say it, but on a notebook that weak (I have a Compaq Armada m700), you should stick with Windows. Say what you want about Windows, but without Visual Styles it's a LOT faster than Xfce. Xfce is almsot too much for the 700 mHz machine I'm typing on now, so it'd probably be painfully slow.

-Ben (haha I'm Ben too)

---

### Post by hockeytux on 2009-09-06
Crunchbang would run great on it for sure. Or Ubuntu Minimal with LXDE.

---

### Post by bjaz on 2009-09-07
i'll give CrunchBang a try then. 
edit, i'm looking into now. so far it's runing from the CD, which is slow, and i'm installing it to disk


thanks

ben

---

### Post by bjaz on 2009-09-07
ok, i did something radical and installed crunchbang, swiping off both windows (didn't boot anymore anyway, and couldn't find anyone to help fix the boot), AND the working xubuntu partition i had.



clicking on a movie file on an external hard disk doesn't seem to do much, which is the same issue i was having with xubuntu, and watching a you tube video is still too much.

i might go back to xubuntu, as i frankly don't see that much of a difference in multimedia support. i'm just a little disapointed as the original japanese windows xp version could read videos, and I had no clue that ubuntu based systems couldn't. as explained in the links i posted above, this is a recent machine, not an old one, and when i used it on the windows side i never saw such multimedia support issues, even thought the processor is only a 500mb geode.. now the windows side is gone, i'm a little dissapointed (and cannot reinstall windows since the machine didn't come with a CD)

i'll hang on with crunch for a moment, but have a few questions, as i'm feeling a little lost :

kohjinsha offers linux drivers for this machine here

[http://www.kohjinsha.com.sg/products/drivers.htm](http://www.kohjinsha.com.sg/products/drivers.htm)

. could they be of any use in this case, for multimedia support ? or anyway to use more of the 80gig on the drive to lighten up the processor's work ?

and also how could i get the display to 800x480, which i believe is what it should be.


and synaptic doesn't display the same apps as it did in xubuntu, what is this due to ?

thanks again



b

ben

---

### Post by blazemore on 2009-09-07
Can you get online with it?
Let's get an up-to-date xserver:
```

sudo -i
echo deb http://ppa.launchpad.net/ubuntu-x-swat/x-updates/ubuntu jaunty main >> /etc/apt/sources.list
echo deb-src http://ppa.launchpad.net/ubuntu-x-swat/x-updates/ubuntu jaunty main >> /etc/apt/sources.list
gpg --keyserver subkeys.pgp.net --recv AF1CDFA9 && gpg --export --armor AF1CDFA9  | sudo apt-key add -
apt-get update
apt-get dist-upgrade
exit

```

---

### Post by bjaz on 2009-09-07
yes it's online.
i'm doing the updates now following your commands.

thanks again for your help

b

---

### Post by bjaz on 2009-09-07
i did the updates, thanks, along with a system update.

 is there anything else I should update for the video files and resolution ?
 I understood it had to be 800x480 instead of 800x600, but haven't managed to do this.
and what of those kohjinsha linux video drivers, are they of any use or not necessary in this case ?

it's strange how the CPU usage is often jumping to 100%. I was thinking that with 512mb of ram, it would be a little more balanced.
the swap is only 2gigs, whereas the hdd is 80 gig. would increasing the swap size help ? and how would i do this in this situation ?

thanks

ben

---

### Post by gordintoronto on 2009-12-20
Increasing the swap on this computer will not help at all, it is already larger than optimum.  The computer may be fairly new, but it is very slow!

Earlier you asked about accessing Windows partitions.  With Karmic, you can click on Places/Computer, and you should see the Windows partitions.  Click on them, and you should have full access.

---

