---
title: "[SOLVED] Ubuntu doesn't detect my iRiver u10"
date: 2007-06-20
forum: Hardware &amp; Laptops
---

### Post by Jaxilian on 2007-06-20
I have a iRiver u10 that I can't get to work with Ubuntu 7.04.

any tips on how to do? I read a couple of posts about it, but they are very incomplete and does not aim towards the average user.

So far it seems like a dead end

---

### Post by ukripper on 2007-06-20
have you tried this link [https://help.ubuntu.com/community/PortableDevices/iRiver?](https://help.ubuntu.com/community/PortableDevices/iRiver?)

---

### Post by Jaxilian on 2007-06-20
I dont have Windows on any computer so how can I do it without it?

---

### Post by Jaxilian on 2007-06-29
> **ukripper said:**
> have you tried this link [https://help.ubuntu.com/community/PortableDevices/iRiver?](https://help.ubuntu.com/community/PortableDevices/iRiver?)

Does not work. I don't get the button in the firmware updater to switch to UMS

How can I remove the MTP and switch over to UMS on my iRiver u10?

---

### Post by ntetreau on 2007-06-29
I don't know how you can switch to UMS from MTP, but in MTP mode your device should be very usable under ubuntu 7.04.  You can install libmtp, gnomad2 and amarok which will ensure you can transfer your music efficiently using either gnomad2 or amarok.  Rhythmbox will support MTP devices out of the box in Gutsy or you can always search the forum on how to install the latest version by hand (works well for me).

Nic

---

### Post by Jaxilian on 2007-06-29
> **ntetreau said:**
> I don't know how you can switch to UMS from MTP, but in MTP mode your device should be very usable under ubuntu 7.04.  You can install libmtp, gnomad2 and amarok which will ensure you can transfer your music efficiently using either gnomad2 or amarok.  Rhythmbox will support MTP devices out of the box in Gutsy or you can always search the forum on how to install the latest version by hand (works well for me).

Nic

Tried it, no luck.
Amarok, Rhytmbox doesn't support the iRiver u10

---

### Post by Jaxilian on 2007-06-29
SOLVED: found the correct updater on: [http://www.iriver.com/html/support/download/sudw_view.asp?idx=836](http://www.iriver.com/html/support/download/sudw_view.asp?idx=836)

---

### Post by Jaxilian on 2007-06-29
> **flodis said:**
> SOLVED: found the correct updater on: [http://www.iriver.com/html/support/download/sudw_view.asp?idx=836](http://www.iriver.com/html/support/download/sudw_view.asp?idx=836)

Hmmm after testing it well it actually doesn't work. I can't import any mp3:s to the U10. it says it "cannot load the music database".

I put it back to MTP and works again.

Still unsolved.

---

### Post by Jaxilian on 2007-06-30
ok here is what does not work

* changing to UMS works, but then I can't do anything with the player.
* Rhythmbox with MTP does not detect the player.
* Amarok with MTP does not detect the player
* Nautilus does not detect the player in MTP

basically I think I have to sell the friggin player or throw it away.

---

### Post by ukripper on 2007-07-02
If UMS works, aint you able to transfer mp3 to it?

---

### Post by Jaxilian on 2007-07-02
> **ukripper said:**
> If UMS works, aint you able to transfer mp3 to it?

I can transfer stuff to it,but it won't show up in the player when I turn it on.....so I don't know what's up with that.

---

### Post by ukripper on 2007-07-03
iRiver is really a pain, sometimes it works and sometime don't. i think you have to find a way to convert it to MTS within player or if i were you I would have bought a better mp3 player which doesn't create problems like MTP and UMS. i have mp3 player 4GB, no idea what make it is but still works as charm with ubuntu.

---

### Post by Jaxilian on 2007-07-16
> **ukripper said:**
> iRiver is really a pain, sometimes it works and sometime don't. i think you have to find a way to convert it to MTS within player or if i were you I would have bought a better mp3 player which doesn't create problems like MTP and UMS. i have mp3 player 4GB, no idea what make it is but still works as charm with ubuntu.

I had to reinstall Windows again on one of my computers to be able to transfer songs to it again.
Problem solved!!

---

### Post by ukripper on 2007-07-16
> **flodis said:**
> I had to reinstall Windows again on one of my computers to be able to transfer songs to it again.
Problem solved!!

I think if you would have created Virtualmachine still it would have solved your problem going down this route. I am glad it worked out for you either way.

---

