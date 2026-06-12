---
title: "Executeing shell files from virtual drive"
date: 2008-08-26
forum: General Help
---

### Post by elbarto_87 on 2008-08-26
Hi,
I think my question will be easy to solve, but I have been searching for the last hour and haven't had any luck.

I have used AcetoneISO2 to mount an image. I can see what is on the image if I got to "Places>Computer" it is listed as "1" {one}. Is "1" the drive letter of is that just the name of the drive? I am use to haveing an adress bar in "my computer" on windows that tells be where abouts I am on the hard drive but I haven't managed to find this feature in Ubuntu yet.

There is a shell file in drive "1" called "Install" that I beleive I have to run in order to install my software, However I do not know how to run it.

I thought I might be able to do something in terminal like change the current dirrectory and run the file.
something like:
```

cd  /1
install
```

But that doesn't work (probally not suppiseing that I am only a few days into my linux experience).

Thank You

Regards Elbarto

---

### Post by bulletxt on 2008-08-26
I'm sure there is a way in nautilus to have an editable bar.

Anyways, type this code in terminal:

cd $HOME/virtual-drives/1

then type:
ls

you should be inside the image you mounted. if by chance you are trying to run a windows *.exe game, then the command is:

wine namefile.exe

of course you first need to have wine installed so:

sudo apt-get install wine

If it is a linux install file, type instead:

./namefile

cheers

---

### Post by Too Late on 2008-08-26
> **bulletxt said:**
> I'm sure there is a way in nautilus to have an editable bar.
Yes there is. Press Ctrl+L or go to Go -> Location...

---

### Post by elbarto_87 on 2008-08-26
Bulletxt, i type in the forst 2 commands and I got this output

```
Desktop DB  install               inst_doc.pdf  mac_install_guide.pdf  update
Desktop DF  InstallForMacOSX.app  license.txt   readme.txt             utils

```

I then typed "./install" and got "Permission Dennied".


'Too Late', thank you for your tip, that is just what im looking for.


Regards Elbarto

---

### Post by bulletxt on 2008-08-27
> **elbarto_87 said:**
> Bulletxt, i type in the forst 2 commands and I got this output

```
Desktop DB  install               inst_doc.pdf  mac_install_guide.pdf  update
Desktop DF  InstallForMacOSX.app  license.txt   readme.txt             utils

```

I then typed "./install" and got "Permission Dennied".


'Too Late', thank you for your tip, that is just what im looking for.


Regards Elbarto

I'm glad to know you resolved your problem. I suggest however to learn terminal basics commands. Give also a quick read to permissions user/group on linux files/folders(everything in *nix is a file). you'll then understand what can "permission denied" mean.

---

