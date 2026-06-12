---
title: "Problems installing php5-gd on ubuntu 8.04"
date: 2008-08-16
forum: General Help
---

### Post by vildrik on 2008-08-16
Hi all,

I've got apache2 + php5 set up on my computer, and I'm trying to get the php gd libraries installed so that the server can handle image uploading and manipulation.

I have installed the php5-gd package and restarted apache. But now when I go to my local server and ask for a php file (Something like 'http://localhost/index.php'), it doesn't run the php script but instead asks me if I want to download the php file unless the file has a reference to phpinfo() anywhere inside of it. My guess is that when I install php5-gd, it screws something up in either the php or the apache configuration files that makes it not recognize that the file is a php script. Unfortunately, I have no idea how the php/apache config files handle this sort of thing or how to fix it.

Thanks in advance for any advice.

Oh, and here's the gd section of phpinfo():

```
GD Support 		enabled
GD Version 		2.0 or higher
FreeType Support 	enabled
FreeType Linkage 	with freetype
FreeType Version 	2.3.5
T1Lib Support 		enabled
GIF Read Support 	enabled
GIF Create Support 	enabled
JPG Support 		enabled
PNG Support 		enabled
WBMP Support 		enabled
```

---

### Post by vildrik on 2008-08-17
Anyone?

---

### Post by cpetercarter on 2008-08-17
The GD section of your phpinfo() file looks fine.

As for Firefox trying to download the script instead of running it, some of the more obvious things to try are:

- check that the script is executable (find it in nautilus, right click, properties, permissions)

- clear the Firefox cache (Tools > Clear private data > uncheck everything except 'cache' > clear private data now)

- read the bit on Troubleshooting php5 in [https://help.ubuntu.com/community/ApacheMySQLPHP]("https://help.ubuntu.com/community/ApacheMySQLPHP")

---

### Post by Francewhoa on 2008-11-21
[FONT=Arial][SIZE=2]Same issue here on [/SIZE][/FONT][FONT=Arial][SIZE=2]Ubuntu Server 8.04.1 and PHP5.[/SIZE][/FONT][FONT=Arial][SIZE=2] The following worked for me:
[http://ubuntuforums.org/showthread.php?p=6226611#post6226611](http://ubuntuforums.org/showthread.php?p=6226611#post6226611)
[/SIZE][/FONT]

---

