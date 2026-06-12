---
title: "Installing a program"
date: 2009-06-17
forum: Installation &amp; Upgrades
---

### Post by jack53 on 2009-06-17
Hello
I am very new with Ubuntu and i have just downloaded sony bird and i am wanting to install it i have opened the .tar.gz file and got this

[IMG]http://i211.photobucket.com/albums/bb267/jacklikesbikes/Screenshot.png[/IMG]

But what do i do after i get this?

I am coming from using Mac OS X so it is very different

---

### Post by ricardofilipemoreira on 2009-06-17
double click on the "songbird" shell script and the program opens. alternatively you can download the songbird package from [www.getdeb.net](www.getdeb.net) and install it. then you can access it through the menu instead of having to create a launch file for it

---

### Post by ~sHyLoCk~ on 2009-06-17
Err...the screenshot is really small and unclickable. Anyway, assuming there is an INSTALL file you can proceed by installing build-essential first.

```
sudo apt-get build-essential
```
now do 
./configure
make
make install

---

### Post by oldos2er on 2009-06-17
You can download a deb file here: [http://www.getdeb.net/release.php?id=4215](http://www.getdeb.net/release.php?id=4215)
Then just double-click it to install.

---

### Post by hockeyhead019 on 2009-06-17
where does that .deb package install it to? because the deb said it installed correctly but it's not in my menu and i can't run it from a command window

nevermind... i always forget to restart my system after installin .deb packages haha found it right where it shoulda been

---

