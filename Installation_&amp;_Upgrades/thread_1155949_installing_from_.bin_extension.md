---
title: "installing from .bin extension"
date: 2009-05-11
forum: Installation &amp; Upgrades
---

### Post by shababhsiddique on 2009-05-11
Hello
I am a newbie ubuntu user. Can any one help me with installing from .bin extension?

---

### Post by pro003 on 2009-05-11
type **sudo sh name_of_the_package.bin**

---

### Post by shababhsiddique on 2009-05-11
> **pro003 said:**
> type **sudo sh name_of_the_package.bin**

Thanks! 
Just for curiosity I typed the name of the package only.
i.e 
/media/PortableFiles/Download/Softs/jdk-6u13-linux-i586.bin

 And it worked! is there any future problem I shall face?

---

### Post by 3rdalbum on 2009-05-11
It depends what you are installing. It looks like you've got a binary installer, and the most common thing that's in a binary installer is Google Earth; if you're trying to install Google Earth it's a better idea to add the Medibuntu repository ([www.medibuntu.org](www.medibuntu.org)) and just install Google Earth from there.

If it's something else and it's not available in the repositories, you need to make it executable by root:

```
sudo chmod u+x name_of_file
```

And then run it as root (installers need root permission, of course):

```
sudo su
./name_of_file
```

Either substitute "name_of_file" for the actual name or path of the file, or drag the file to the terminal and its path will be filled in for you.

---

### Post by shababhsiddique on 2009-05-16
Thanks

---

