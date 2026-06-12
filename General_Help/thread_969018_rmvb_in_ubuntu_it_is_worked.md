---
title: "rmvb in ubuntu it is worked"
date: 2008-11-03
forum: General Help
---

### Post by dapoor on 2008-11-03
[SIZE="4"]If you want to play rmvb in Ubuntu you have to do some easy steps, which i regularly forget about, so here is a description which will help me (and possibly you) to remember how it works.
One thing you should note is, that you will have to install non-free Components.

Only things needed should be a player like mplayer and the non-free package w32codecs.

Before you can install the last one you will have to add the medibuntu repository to your list:
> 
sudo wget [http://www.medibuntu.org/sources.list.d/gutsy.list](http://www.medibuntu.org/sources.list.d/gutsy.list) -O /etc/apt/sources.list.d/medibuntu.list


now add the gpg key:

> wget -q [http://packages.medibuntu.org/medibuntu-key.gpg](http://packages.medibuntu.org/medibuntu-key.gpg) -O- | sudo apt-key add - && sudo apt-get update


Now install my favorite rmvb player:

> sudo apt-get install mplayer


and finally the codecs:

> sudo apt-get install w32codecs




To start playing from the console just write something like this:

gmplayer video.rmvb



Note:
copy from

[http://my.opera.com/dduenker/blog/2007/11/03/how-to-play-rmvb-in-ubuntu-7-10-gutsy-gibbon](http://my.opera.com/dduenker/blog/2007/11/03/how-to-play-rmvb-in-ubuntu-7-10-gutsy-gibbon)[/SIZE]> 

---

