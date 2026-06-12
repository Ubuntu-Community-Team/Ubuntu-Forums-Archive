---
title: "Unable to read any sort of DVD"
date: 2011-07-03
forum: Hardware
---

### Post by D.Cable_Guy on 2011-07-03
I installed Ubuntu 10.04 onto my MSI GT735 a couple of days ago and I am still ironing out the wrinkles. I have run into two major problems. One: I cannot get the sound to ONLY come out of the speakers or ONLY out of the headphone jack. Two: I am unable to play any DVDs. I can look into the DVD and see files there so I know that it is not a problem with mounting the drive. I have tried the stock DVD player and also VLC player both with the same results. It says that it cannot read from resource. Ripping the DVD doesn't work either, it just comes up with [ERROR]. I have looked into other posts about the same kind of problem and I also installed the Libdvdcss from Medibuntu and that doesn't help either. Any thoughts or comments would help.

---

### Post by soap1 on 2011-11-26
in the terminal try:

sudo apt-get install libdvdread4

then:

sudo /usr/share/doc/libdvdread4/install-css.sh

---

### Post by crazy bird on 2011-11-26
Check this site for multimedia completion: [https://sites.google.com/site/tipsandtricksforubuntu/how-to-add-multimedia](https://sites.google.com/site/tipsandtricksforubuntu/how-to-add-multimedia)

---

