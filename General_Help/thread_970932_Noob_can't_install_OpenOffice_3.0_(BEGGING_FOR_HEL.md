---
title: "Noob can't install OpenOffice 3.0 (BEGGING FOR HELP!)"
date: 2008-11-04
forum: General Help
---

### Post by redioactif on 2008-11-04
Hello...
Just moved to Linux so this might sound like A REAL NOOB question because I don't know how this works...

Ok.

So I followed a tutorial, and got stuck in installing Openoffice 3.0.
Here is the tutorial.
[http://www.tectonic.co.za/?p=3363](http://www.tectonic.co.za/?p=3363)

So what it says, is that I have to delete OpenOffice 2.4 from my PC (which I did with no problem), then had to download and extract OpenOffice 3.0 (which I did)..But then what?
There is a folder full of DEBS inside, but this isn't like windows with the exe...what should I do?
I went to terminal and tried this step from the tutorial:
"sudo dpkg -i *.deb"
but it just says something like no folder found (My linux is in french so can't really translate...).

If anyone can help me that'd be great.

---

### Post by drs305 on 2008-11-04
If the download went well, you probably didn't run the "sudo dpkg -i *.deb" from within the folder with the .debs inside. Make sure you start from within the same folder as the deb files. You can check by running the "ls" command. It should return a list of all the debs you need to install.

Then run "sudo dpkg -i *.deb" again.

---

### Post by redioactif on 2008-11-04
> **drs305 said:**
> If the download went well, you probably didn't run the "sudo dpkg -i *.deb" from within the folder with the .debs inside. Make sure you start from within the same folder as the deb files. You can check by running the "ls" command. It should return a list of all the debs you need to install.

Then run "sudo dpkg -i *.deb" again.

What? Where do I do this? Isn't in Terminal?? I'm sorry but I'm really confused about all this...I have deb files...what do I do exactly now?

---

### Post by redioactif on 2008-11-04
Anyone? Please!!

---

### Post by scouser73 on 2008-11-04
Here's an excellent tutorial on installing OpenOffice 3.
[http://tombuntu.com/index.php/2008/10/14/install-openofficeorg-30-in-ubuntu-804-and-810/]("http://tombuntu.com/index.php/2008/10/14/install-openofficeorg-30-in-ubuntu-804-and-810/")

---

### Post by thegreenblob on 2008-11-04
Just cd in to the directory with the debs and then install them.

Open the terminal and then...

cd /home/user/desktop/debs (Or where ever they're at, an easy way to type this would be to just drag the folder with the debs in the terminal)

Next you would: sudo dpkg -i *.deb

After you do this you should be able to just follow the rest of the tutorial. Hope this helps.

---

### Post by LowSky on 2008-11-04
in teminal do this

```
cd /path/to/openoffice.debs
```

then the code

```
sudo dpkg -i *.deb
```

then ```
cd /path/to/second folder/within/openoffice/folder
```

then


```
sudo dpkg -i *.deb
```

should all work

---

### Post by redioactif on 2008-11-04
Works like a charm thanks guys

---

