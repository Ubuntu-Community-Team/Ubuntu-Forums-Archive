---
title: "Cannot uninstall Mathematica 5.0 ??"
date: 2005-11-10
forum: General Help
---

### Post by jeftones on 2005-11-10
I cannot seem to uninstall Mathematica 5.0 ? anyone who knows how this is done ?

Cannot find any uninstall script anywhere.... 

Thanks,
Jeftones (new to the linux world... but here to stay :-))

---

### Post by invalid on 2005-11-10
This depends on how you went about installing it.

If you installed this program through synaptic, apt-get, or a debian file, you can use this command:
```
sudo apt-get remove <program name>
```

If you installed this program through a tarball, you will need to follow the directions in the README file. Often it is something like:
```
make uninstall
```

Cheers,
Cb

---

### Post by jeftones on 2005-11-10
I installed by changing to root (su), and run the installer by:
"sh Mathinstaller" from the Install directory on the CD.

Then I choose 1 from the menu > full install and then It completed the installation by itself...

There seems to be no uninstaller anywhere... not on the CD and not in the directory where Mathematica 5 is installed : /usr/local/Wolfram/Mathematica/5.0/

---

### Post by ow50 on 2005-11-10
[QUOTE=jeftones]There seems to be no uninstaller anywhere... not on the CD and not in the directory where Mathematica 5 is installed : /usr/local/Wolfram/Mathematica/5.0/[/QUOTE]
Delete the whole "/usr/local/Wolfram" directory. Delete "mathematica" and some other scripts starting with the letter "m" in "/usr/local/bin" (Check the file contents with a text editor). After that you should probably be done. Maybe someone who has Mathematica installed can be more precise.

---

