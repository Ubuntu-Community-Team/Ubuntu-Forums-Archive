---
title: "Read movie dvd with xps1330"
date: 2007-10-03
forum: Hardware &amp; Laptops
---

### Post by atlas95 on 2007-10-03
Hello,

I have install all necessary package i think for read dvd (libdvdcss2 w32codecs), but with my dell xps 1330 this doesn't work !

I can read a dvd data but not movie.

I think they are a problem with the buil-in dvd ?

I must config something hith hdparm?

Could you help me please

sorry for my english

---

### Post by atlas95 on 2007-10-04
Up!:guitar:

---

### Post by lksdot on 2007-12-14
Hi atlas95,

I have had the same problem with the same computer, but the solution was very simple... the region of the dvd player is not set, as reported from
 [http://john.leidel.googlepages.com/opensuse10.3ondellxpsm1330]("http://john.leidel.googlepages.com/opensuse10.3ondellxpsm1330")

(see under the "DVD Reading [movies]" section).

Since the dvd players can play only the dvd-movies with the same region, this means that only dvds with no protection can be played.

You can check if it's also your problem just installing the package "regionset" from synaptic or your favourite apt-get frontend. 

Then put a dvd in the drive and type from shell:

```
sudo regionset /dev/scd0 
```

where scd0 should be your dvd-player device.

The correct ouput should be similar to:

```

regionset version 0.1 -- reads/sets region code on DVD drives
Current Region Code settings:
RPC Phase: II
type: SET
vendor resets available: 4
user controlled changes resets available: 4
drive plays discs from region(s): 2, mask=0xFD

Would you like to change the region setting of your drive? [y/n]:      

```

If your problem is that the region has not been set, a line similar to:

```
drive plays discs from region(s):, mask=0xFD
```

should apper. If this is the case, you can follow the instructions to set the right region: if you live in France, as appears in your profile, your region is the same as mine, the region "2".

**[COLOR="Red"]**** ATTENTION ****: Don't change the region if you are not sure: only 4 or 5 changes are allowed for each dvd-drive.[/COLOR]**

You can also change the region via Vista if it is installed, from the hardware properties of the dvd drive.

If this solves your problem, please add "[SOLVED]" to the title of the post.

Good luck!

---

### Post by drsaamah on 2008-02-06
i have this same problem and STILL can't get dvd's to play.  ive installed everything that has 'dvd' 'xine' 'read' 'lib' possible.  i installed the regionset as well and set my region to '1' (since i live in the US) and my computer STILL wont play a dvd.
ive set this up just fine on my old computer.  i dont know what im doing wrong now.
any suggestions?

---

### Post by rje_nc on 2008-02-06
What software are you using to play the DVD?  I personally have had better luck using VLC.  I sometimes need to change the Video output option in the advanced preferences, but then it plays things very well.

Might be worth installing and see if it works better than Totem or MPlayer.

Bob

---

