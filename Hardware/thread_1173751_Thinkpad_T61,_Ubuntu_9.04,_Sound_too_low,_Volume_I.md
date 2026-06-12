---
title: "Thinkpad T61, Ubuntu 9.04, Sound too low, Volume Issue"
date: 2009-05-30
forum: Hardware
---

### Post by Trentor on 2009-05-30
Hello there, I am running a Thinkpad T61, I used to have Ubuntu 8.10 on it and I had an issue with the sound, but thankfully with this fix from this link: [http://www.thinkwiki.org/wiki/Installing_Ubuntu_8.10_(Intrepid_Ibex)_on_a_ThinkPad_T61](http://www.thinkwiki.org/wiki/Installing_Ubuntu_8.10_(Intrepid_Ibex)_on_a_ThinkPad_T61)

Terminal:
```
gksudo gedit /etc/modprobe.d/alsa-base
```

Then Adding ```
options snd-hda-intel model=thinkpad power_save_controller=Y power_save=10
```
to the end of the file worked.


Now with my new Ubuntu 9.04 install I tried that and it did not work.

The odd thing:  Just today I reinstalled ubuntu completly new 9.04, but before hand I had ubuntu 8.10 and upgraded to 9.04 and did not have this problem.


I took a look at this post, [http://ubuntuforums.org/showthread.php?t=1059561&highlight=thinkpad+t61](http://ubuntuforums.org/showthread.php?t=1059561&highlight=thinkpad+t61) but was unable to extract much information from it because I donb't have dolby.


Thanks, looking to get my sound boosted to what it used to be.


Trent :D

---

### Post by Trentor on 2009-05-30
Apparently the only way this gets resolved is by the computer rebooting a few times, lol.

---

### Post by righdforsa on 2009-09-19
This trick worked for me. I've had low volume on my Thinkpad T61 since Hardy. Incidentally, my /etc/modprobe.d/alsa-base was completely blank, but I added the line and it's now a bit louder.

---

