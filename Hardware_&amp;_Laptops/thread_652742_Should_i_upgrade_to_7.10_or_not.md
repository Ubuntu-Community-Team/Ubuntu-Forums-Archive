---
title: "Should i upgrade to 7.10 or not???"
date: 2007-12-29
forum: Hardware &amp; Laptops
---

### Post by soviet911 on 2007-12-29
I want to try and upgrade my xubunto 7.04 feisty fawn to 7.10 gutsy gibon, I got an old HP omnibook 6100 and i read that HP laptops got problems with 7.10 or is it just for the dv series, also if it doesnt work can i down grade without needing to format??? Thanks

---

### Post by PmDematagoda on 2007-12-29
If you are happy enough with Ubuntu 7.04, it really is not necessary to upgrade the system until support for Ubuntu 7.04 runs out. Also, if you have a failed upgrade, a downgrade, while being an option, is not a very good option since it is highly risky and could make your entire OS fail and hence, make you lose all your data.

---

### Post by hellion0 on 2007-12-29
I'm not sure about all HP laptops, as mine runs fine under 7.10 Studio. Of course, my laptop is a Pavilion ze4300.

As for downgrading, I'm honestly not sure (I've never tried), but the old rule of "always always ALWAYS back up first" applies even more with any upgrade or downgrade.

---

### Post by soviet911 on 2007-12-29
well then i will upgrade, this is my secondary laptop and got only 10 gigs of music i copied off my main pc wich is down right now since Im steping up the video card with eVGA, ok then i will try that, and if it wont work i will just instal ubunto 7.04 from fresh, dont care for any files on the laptop besides 2 so i will put them on a flash drive for now, thanks though

---

### Post by soviet911 on 2007-12-29
so while trying to update i got this error 
Failed to fetch [http://medibuntu.sos-sts.com/repo/dists/feisty/free/binary-i386/Packages.gz](http://medibuntu.sos-sts.com/repo/dists/feisty/free/binary-i386/Packages.gz) 404 Not Found
Failed to fetch [http://medibuntu.sos-sts.com/repo/dists/feisty/non-free/binary-i386/Packages.gz](http://medibuntu.sos-sts.com/repo/dists/feisty/non-free/binary-i386/Packages.gz) 404 Not Found
Failed to fetch [http://medibuntu.sos-sts.com/repo/dists/feisty/free/source/Sources.gz](http://medibuntu.sos-sts.com/repo/dists/feisty/free/source/Sources.gz) 404 Not Found
Failed to fetch [http://medibuntu.sos-sts.com/repo/dists/feisty/non-free/source/Sources.gz](http://medibuntu.sos-sts.com/repo/dists/feisty/non-free/source/Sources.gz) 404 Not Found
Failed to fetch [http://medibuntu.sos-sts.com/repo/dists/edgy/free/binary-i386/Packages.gz](http://medibuntu.sos-sts.com/repo/dists/edgy/free/binary-i386/Packages.gz) 404 Not Found
Failed to fetch [http://medibuntu.sos-sts.com/repo/dists/edgy/non-free/binary-i386/Packages.gz](http://medibuntu.sos-sts.com/repo/dists/edgy/non-free/binary-i386/Packages.gz) 404 Not Found
Failed to fetch [http://medibuntu.sos-sts.com/repo/dists/edgy/free/source/Sources.gz](http://medibuntu.sos-sts.com/repo/dists/edgy/free/source/Sources.gz) 404 Not Found
Failed to fetch [http://medibuntu.sos-sts.com/repo/dists/edgy/non-free/source/Sources.gz](http://medibuntu.sos-sts.com/repo/dists/edgy/non-free/source/Sources.gz) 404 Not Found

how do i fix that. (i tried twice, failed twice :mad: )

---

### Post by gaylapdancer on 2007-12-29
Those repositories are Feisty and Edgy ones, try deleting them from your sources and adding the gutsy repos with the following commands:
```
sudo wget http://www.medibuntu.org/sources.list.d/gutsy.list -O /etc/apt/sources.list.d/medibuntu.list
```

```
wget -q http://packages.medibuntu.org/medibuntu-key.gpg -O- | sudo apt-key add - && sudo apt-get update

```

The first command adds the repo to your 'sources.list' file, and the second gets the gpg key.

Good luck.

---

### Post by PmDematagoda on 2007-12-29
I would recommend that third-party repositories such as the Medibuntu ones be removed or disabled before an upgrade. To do this, open the sources.list for editing using:-
```
gksudo gedit /etc/apt/sources.list
```

You can disable the Medibuntu repositories by typing # in front of them or just delete them.
After the editing is done, do:-
```
sudo apt-get update
```

That should fix your problem completely.

---

