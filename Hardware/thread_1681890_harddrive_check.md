---
title: "harddrive check"
date: 2011-02-04
forum: Hardware
---

### Post by gcbzzzz on 2011-02-04
I have a system with two harddrives.

both are 20% for system (one linux root, the other another OS)
and 80% of both forming a Raid-1

Recently i can rear Clicking sounds coming from the drives.

looking into system>administration>disk utility I can see that SMART is green on both devices. The logs and numbers do not show anything that i think is out of the ordinary...

Question is:
what should I be looking in the SMART data to see if my clicking sounds are a sign of problem or not?

Any other sanity check I should run on the drives?

Would checkdisk do any good if the problem is not yet corrupting data?

---

### Post by tgalati4 on 2011-02-04
SMART only captures 2/3 of failure events.

Backup your data and run the manufacturer's tests.  They can be found on Ultimate Boot CD.

---

### Post by gcbzzzz on 2011-02-05
Had never heard of the ultimate boot CD. will give it a try right away!

thank you!

---

### Post by dralokyn on 2011-02-05
Where can this Ultimate Boot CD be found?

---

### Post by gcbzzzz on 2011-02-05
> **dralokyn said:**
> Where can this Ultimate Boot CD be found?

got it here [http://www.ultimatebootcd.com/](http://www.ultimatebootcd.com/)

i will try it out in a few minutes... mainly the seatools

Link for the torrent:
[http://www.ultimatebootcd.com/download/ubcd503.iso.torrent]("http://www.ultimatebootcd.com/download/ubcd503.iso.torrent")

Alternatively, you can use this magnet link:

  magnet:?xt=urn:btih:AOZHEVFVWX6IJOIABV3UMWM6ZBURVHK4


And here you can find how to make a USB disk instead:
[http://www.ultimatebootcd.com/customize.html#usb](http://www.ultimatebootcd.com/customize.html#usb)

---

### Post by gcbzzzz on 2011-02-06
seatools (seagate HDD diagnosis tool) works. i have no clue what it is testing... but running acoustic test (stop the spinning plater) in one drive and then testing the other was enough to understand which one had the clicking noises... good thing it's not both.

i'm still unsure if the short/Long testing are destructive to the data. so i'm testing one, booting into ubuntu, resyncing the raid even if not needed, and testing the other.

---

