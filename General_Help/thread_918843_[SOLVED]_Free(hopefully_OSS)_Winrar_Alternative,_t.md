---
title: "[SOLVED] Free(hopefully OSS) Winrar Alternative, that has all of it's features"
date: 2008-09-13
forum: General Help
---

### Post by Predator106 on 2008-09-13
Hi, I would like a free (hopefully/possibly OSS) alternative to WinRar.

I could run WinRar under WINE, but does anybody know how well it works in WINE, any problems, have you used it and it's perfect? I need to be able to create split archives (partitioned archives) and need to be able to pack/unpack it. Please don't tell me download the 'unrar' and the 'rar' package, I want a GUI frontend, and I don't even think those have the features I need.

The reason I ask this is I am going to replace Windows XP Pro on a server I have that downloads files from the internet, etc. Having Winrar or an alternative to it makes me able to install Ubuntu on it, without it, I can't install it/there'd be no point.

---

### Post by bingoUV on 2008-09-13
Any doubt about any application's installability in wine, search it in [http://appdb.winehq.org/](http://appdb.winehq.org/). I see here that winrar has platinum support from wine (highest support possible, I think).

As for alternatives, 7zip ([http://www.7-zip.org/](http://www.7-zip.org/)) can unpack rar.

---

### Post by patrickfromspain on 2008-09-13
sudo apt-get install rar unrar

---

### Post by Predator106 on 2008-09-13
The funny part is, I just thought about it a few minutes after I had posted, heh. 

But as I said, I need both unpacking and packing, and multiple partitioning of archives (splitting), in which case 7-Zip wouldn't do for this.

Is there anything else? 

I'd prefer a "free" program, instead of using non-free programs.

---

### Post by patrickfromspain on 2008-09-13
sorry, just saw you want a gui XD

Anyway, you installing those you'll be able to unpack the .rar file right-clicking them an selecting extract here will extract the package. Also, you'll be able to open it as every other document, and file-roller will you the contents; with file-roller you can also make new rar packages and so. I've have very few problems with rar packages.

[http://www.ubuntu-unleashed.com/2008/05/howto-create-split-rar-files-in-ubuntu.html](http://www.ubuntu-unleashed.com/2008/05/howto-create-split-rar-files-in-ubuntu.html)

---

### Post by Neo_The_User on 2008-09-13
Unrar sucks up all the memory in my system in System Monitor and runs my CPU at 100% for about 5 minutes then it dies. I strongly advise you DO NOT USE unrar-free.

---

### Post by Nepherte on 2008-09-13
When you install the packages 'unrar' and 'rar' you can use the gui of the default archiver that comes preinstalled with Ubuntu: 'file-roller'.

---

### Post by Predator106 on 2008-09-13
But does it support archive splitting?

---

### Post by anjilslaire on 2008-09-13
I run Winrar under wine for the occasional passworded split archive. It works fine.

---

### Post by mikewhatever on 2008-09-13
Predator106, can you name all winrar's features you are interested in, apart from splitting, which you've already mentioned.

---

### Post by Predator106 on 2008-09-15
Well that's basically it, archive splitting and compression adjustment....Yeah, I think that's it. But I wanted to know if there were other GUI programs meant for Linux that did such. I don't want to have to go to the command line everytime I want to create, extract, or split a created archive...etc.

---

