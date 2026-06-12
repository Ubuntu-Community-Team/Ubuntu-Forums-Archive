---
title: "No more sound after an update? -&gt; Read this !"
date: 2008-09-02
forum: General Help
---

### Post by Kooothor on 2008-09-02
Hi folks, 

After getting back from holidays, I did one big update (it has been a month since I've started up my computer) and my sound went off !!!
I'm using Hardy on a new Macbook.

Finally, I managed to have sound again.
So here is the tip to get it back :

The update must somehow reinitialize your /etc/modprobe.d/options file.
So you must add whatever you used to add in order to get the sound working there again.

For a macbook santa rosa :
sudo gedit /etc/modprobe.d/options
then add : 
#sound
options snd-hda-intel model=mbp3

Reboot and the sound should work again.
Please post the link of this thread to others unresolved "I-have-no-more-sound" threads you may find :D

Bye.

---

### Post by Sycron on 2008-09-02
hda intel work out of box on the 8.10 intrepid ibex.

---

