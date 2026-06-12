---
title: "Sony VAIO FZ-Series and Hardy"
date: 2008-05-25
forum: Hardware
---

### Post by sojusnik on 2008-05-25
Hi,

I'm on Hardy 64-bit with a Sony Vaio FZ21E. Details about the hardware you can find [_here_]("http://www.box.net/shared/d0rfuonkck").


Some useful advices for the Vaio FZ21E user, but should also work with the whole FZ-Series:

If you want to activate the WLAN light, so that it will glow when you are on wireless, just simply run the following in terminal:
> sudo apt-get install linux-backports-modules-hardy

* Some other advices are to be [_found here_]("http://ubuntuforums.org/showpost.php?p=4937799&postcount=24").

* [_A thread about Brightness Control on FZs_]("http://ubuntuforums.org/showthread.php?t=702879"). Waiting for Nvidia to fix this issue.


But there are still some issues that are not working properly in Hardy:

* Gladly "they" have managed to get the "AV Mode" Button to work beside the "S1" Button that still doesn't work. How can I activate the "S1" Button?

* Is there a comfortable method to shut down the display with a key combination or to configure Ubuntu, that after 3 minutes of inactivity the display will shut down. Shut Down is not to turn black the screen like some screensavers do, but really shut down, like when the lid of the notebook is closed...

* If you have a 8XXX nvidia series card and are using compiz, then you have by chance a very annoying bug, that [_corrupts your display while scrolling_]("http://forum.compiz-fusion.org/showthread.php?t=6742"). This bug is also [_discussed here_]("http://ubuntuforums.org/showthread.php?t=671656"). Any idea how to fix this?

* From time to time, when I'm using deluge (a torrent client) or I'm downloading at high speed (from 100 Kb/s - 1900 Kb/s) my wireless connection drops, so that I manually have to reconnect to the router, to have a connection again. I'm using the "iwl3945" Driver with the ubuntu build-in Network Manager. Any fix to this one?


Every help appreciated!

---

### Post by hihihi on 2008-12-07
Hello!
Good News!
I can report, that brightness is working now on my Sony VAIO FZ31M.
thanks to the guide of "frank17" here (it is in italian):
 [http://www.frank17.it/linux/fz18m.htm](http://www.frank17.it/linux/fz18m.htm) from [http://www.linux-on-laptops.com/](http://www.linux-on-laptops.com/)

it is a real solution, nvclock from cvs provided in that site is able to control the brightness of my laptop.

check it out!

):P

---

### Post by hihihi on 2008-12-08
i wrote an how-to here:

[http://ubuntuforums.org/showthread.php?t=806630&highlight=Sony+FZ+brightness](http://ubuntuforums.org/showthread.php?t=806630&highlight=Sony+FZ+brightness)

---

