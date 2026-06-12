---
title: "[SOLVED] tpb in Thinkpad X60 Fluxbox"
date: 2008-04-06
forum: Hardware &amp; Laptops
---

### Post by ilych on 2008-04-06
I am trying to get my FN+home and FN+end brightness keys working in Fluxbox. They worked out of the box in GNOME and after installing tpb, tpb's display also shows up in GNOME but not in Fluxbox. Following this [tutorial]("http://www.marzocca.net/linux/ubuntux31.html"), I did the following:

lsmod | grep nvram (to check if the nvram group is running)
sudo adduser <your user> nvram (to add my user to the nvram group)
sudo apt-get install tpb (installed tpb)
sudo gedit /etc/tpbrc (do I need to edit this file for it work? I tried uncommenting #FN and #NVRAM /dev/nvram but all to no avail)

Then I added 'tpb &' to ~/.fluxbox/startup then ctrl+alt+backspace to restart X. In the list of processes (ps aux), I see tpb running, but FN+home and FN+end does not work. What else do I need to do so that tpb will work in fluxbox?

The [thinkwiki]("http://www.thinkwiki.org/wiki/How_to_get_special_keys_to_work#fluxbox") website that is suggested a lot on this forums has not been helpful (it doesn't provide any help on this subject).

Thanks,
ilych

---

### Post by ilych on 2008-04-09
Bump.

Anyone?

---

### Post by ilych on 2008-04-11
I found a solution here: [http://ubuntuforums.org/showthread.php?t=503233&page=4](http://ubuntuforums.org/showthread.php?t=503233&page=4)

---

