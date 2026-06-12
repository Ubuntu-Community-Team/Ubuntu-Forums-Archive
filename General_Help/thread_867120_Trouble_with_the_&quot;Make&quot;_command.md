---
title: "Trouble with the &quot;Make&quot; command"
date: 2008-07-22
forum: General Help
---

### Post by Allubz on 2008-07-22
Dear Ubuntu community,

I've started using Ubuntu just todaay and stumbled into a problem while trying to install cq. use aircrack.

The installation procedure is as following:

> cd /tools/wifi
tar zxvf aircrack-[version].tgz
cd aircrack-[version]
make
make install

I get stuck at the "make" part. When I enter Make for aircrack-ng-1.0-rc1, aircrack-2.41 and madwifi-0.9.4.

All programs do somehow start to work with the Make command but then return an amazing (full screen) amount of errors and there's no actual result (not to mention I'm not even sure what the exact result should be, but I suppose a compiled program, to run??)

Thanks for clearing up, if I'm terribly stupid in any way feel free to say so, I'd like to learn how to make proper use of Linux.

---

### Post by Potatoj316 on 2008-07-22
try installing build-essential
```
sudo aptitude install build-essential
```

are you installing aircrack?  I think thats in the repositories, try
```
aptitude search aircrack
```

---

### Post by Allubz on 2008-07-22
> **Potatoj316 said:**
> try installing build-essential
```
sudo aptitude install build-essential
```

are you installing aircrack?  I think thats in the repositories, try
```
aptitude search aircrack
```

Thank you for your quick reaction!

I tried installing the build essential but:
"Couldn't find any package whose name or description matched "build-essential""

Tried searching for aircrack but if I type it it simply acts as if I only gave a return:
albi@Lalbi:~$
albi@Lalbi:~$


-- Any ideas? Thanks!

---

### Post by Darkade on 2008-07-22
Go to System > Administration > Synaptic Package Manager

Find build-essential

Mark it and install it

The look for aircrak there also, if it isn't then continue where you left, but try **sudo make install**
```

cd /tools/wifi
tar zxvf aircrack-[version].tgz
cd aircrack-[version]
make
**sudo make install **

```

---

### Post by Potatoj316 on 2008-07-22
I think build-essential is in the online repositories but I know it is on the cd, just not installed by default.  Make sure your ubuntu cd is marked as a potential source for packages and try what I originally said again (assuming what other people told you dosent work)

also make sure you get the package name right it is build-essential (when replying to me you did get it right, im just making sure) it is not build-essential**s** (i did that once)

---

### Post by Darkade on 2008-07-22
> **Potatoj316 said:**
> I think build-essential is in the online repositories but I know it is on the cd, just not installed by default.
It's in the online repos, I just installed it yesterday in my girlfriend's laptop :lolflag:

You can also install it via
```
sudo apt-get install build-essential
```
I suggest this two methods (synaptic, apt) because I've bumped into some trouble using aptitude command before, I really dunno why

---

### Post by Allubz on 2008-07-22
I managed to install Build Essential by using the DVD for packages.

I couldn't find Aircrack in there.

It seems a part of the errors got fixed but I attached the report that I still get...

madwifi seems to have 'installed'  succesfully. Both aircracks have some problems.

EDIT: Please keep in mind I don't have an active internet connection on the laptop I'm installing on.

---

### Post by Allubz on 2008-07-23
Anyone?

---

### Post by Darkade on 2008-07-23
I've been through your error and I think you might not have installed openssl
try installing it and then compile again aircrack
```
sudo apt-get install openssl
```

---

### Post by Darkade on 2008-07-23
Hey this thread might help you also
[http://ubuntuforums.org/showthread.php?t=528276](http://ubuntuforums.org/showthread.php?t=528276)

EDIT: heeeey!! 200 Posts!!

---

