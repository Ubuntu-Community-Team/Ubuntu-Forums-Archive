---
title: "How Do I Get My PC Serial Number?"
date: 2012-06-11
forum: Hardware
---

### Post by oldefoxx on 2012-06-11
All the lables on the bottom of my Toshiba Satellite Laptom hav smeared
and smudged so much that I can't make out any information on them.  I
found my model number here on these forums because I used it in some
early-on posts about trying to get my wireless going under Ubuntu (the
wireless adapter turns out to be USB connnected internally).

What I am looking for now is some way to get the serial number either off
the laptop directly, or with the help of some software.  I run Windows
2000 as a client on this PC with the help of Oracle's VirtualBox VM (a
great product I may add), so either a method of getting the serial number
via Ubuntu or Windows would do.  I intend to keep a file on hand against
any future needs that has all this info in it, but I have to get the info
first.

Any help would be appreciated.

Oh, the laptop came originally with a 250 GB hard drive.  I bought a WD
750 GB drive and put it in instead.  Great fit, and I love the added
storage.  I noted in my search that the 1 TB drives were too thick to
go into the drive compartment and be closed in.  Too bad, as the price
of 1 TB drives are just a couple of dollars more than I paid for the
750 GB version.

---

### Post by N0oki3 on 2012-06-11
check in bios. It should be visible there

---

### Post by matt_symes on 2012-06-11
Hi

Open a terminal and type

```
sudo apt-get install dmidecode
```

Enter your password. It will not be echoed to the screen.

```
sudo dmidecode -t 1 | grep -i serial
```

I think this is the serial number you are after.

Kind regards

---

