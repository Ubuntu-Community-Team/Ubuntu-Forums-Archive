---
title: "NAVIT &amp; GPS woes"
date: 2009-05-09
forum: Hardware
---

### Post by upptown on 2009-05-09
Hey all!  I was recently given a M$ GPS module (PHAROS USA GPS-360 SiRF).  I figured I'd give it a go and see if I could use it with my HP Dx6650 running Jaunty.  Might be nice for those long road trips..right?  Checked out the most popular GPS mapping programs and chose NAVIT.

Anyways, long and short of is I have absolutely failed.  Program installed just fine with apt-get.  I have all the dependencies and I have followed the NAVIT WIKI to configure the thing with no success and haven't really found any other helpful posts in the many searches I've done.  

So I'm turning to you all for some insight or direction.  Is there anyone out there interested in "walking" me through configuring this beast?  Or is there a better easier to set up program for use on the road?

---

### Post by upptown on 2009-05-12
Bump

---

### Post by upptown on 2009-05-14
Last bump...Anyone got a suggestion for a good linux map program to use when on the road?

---

### Post by cgalpin on 2009-05-29
I use tangogps due to limited resources, but I have used navit, and just installed it on jaunty just fine. What problem are you having exactly?

The steps I took were


cgalpin@jaunty:~/tmp$ sudo apt-get install build-essential  pkg-config  automake  libglib2.0-dev libtiff-dev  libtool  libxmu-dev  libfribidi-dev  gettext  zlib1g-dev  cvs gpsd  gpsd-clients  libgps-dev libdbus-glib-1-dev libgtk2.0-dev  freeglut3-dev  glutg3-dev  libcegui-mk2-dev  libdevil-dev  libglc-dev  libpcre3-dev libmng-dev libfreeimage-dev 

cgalpin@jaunty:~/tmp$ wget [http://voxel.dl.sourceforge.net/sourceforge/navit/navit-0.1.0.tar.gz](http://voxel.dl.sourceforge.net/sourceforge/navit/navit-0.1.0.tar.gz)
cgalpin@jaunty:~/tmp$ tar xzf navit-0.1.0.tar.gz 
cgalpin@jaunty:~/tmp$ cd navit-0.1.0/
cgalpin@jaunty:~/tmp/navit-0.1.0$ ./configure
cgalpin@jaunty:~/tmp/navit-0.1.0$ make
cgalpin@jaunty:~/tmp/navit-0.1.0$ cd navit
cgalpin@jaunty:~/tmp/navit-0.1.0$ ./navit

---

### Post by BrownieMan on 2009-07-12
I had to make some updates to the code to get it to work


```
sudo apt-get install build-essential pkg-config automake libglib2.0-dev libtiff4-dev libtool libxmu-dev libfribidi-dev gettext zlib1g-dev cvs gpsd gpsd-clients libgps-dev libdbus-glib-1-dev libgtk2.0-dev freeglut3-dev glutg3-dev libcegui-mk2-dev libdevil-dev libglc-dev libpcre3-dev libmng-dev libfreeimage-dev

wget http://sourceforge.net/projects/navit/files/navit/navit-0.1.1.tar.gz/
tar xzf navit-0.1.1.tar.gz
cd navit-0.1.1/
./configure
make
cd navit
./navit
```

---

### Post by synace on 2009-07-13
[http://wiki.navit-project.org/index.php/Download_Navit#Debian](http://wiki.navit-project.org/index.php/Download_Navit#Debian)

---

