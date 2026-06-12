---
title: "amsn skin prob."
date: 2008-10-13
forum: General Help
---

### Post by drakoumel on 2008-10-13
hello , i am bck to ubuntu after some months weee :D
i am using amsn instead of WLM and i am trying to apply a  theme 
i go to /usr/share/amsn/skins but it doesnt give me any access i cant make a folder or delete or even to paste the theme i downloaded any ideas?



thank you

---

### Post by homemadejam on 2008-10-13
> **drakoumel said:**
> hello , i am bck to ubuntu after some months weee :D
i am using amsn instead of WLM and i am trying to apply a  theme 
i go to /usr/share/amsn/skins but it doesnt give me any access i cant make a folder or delete or even to paste the theme i downloaded any ideas?



thank you


you will need to do it as Root...
so

**sudo cp -r /home/username/Desktop/AMSN_Skin /usr/share/amsn/skins**

something like that :)

Jam

---

### Post by drakoumel on 2008-10-13
it says like the command is incomplete any suggestion?

---

### Post by homemadejam on 2008-10-13
> **drakoumel said:**
> it says like the command is incomplete any suggestion?

Incomplete? :S
Please can you post the exact error that it gives you?

Thanks,
Jam

---

### Post by drakoumel on 2008-10-13
drakoumel@drakoumel-desktop:~$ 
drakoumel@drakoumel-desktop:~$ sudo cp -r /home/username/Desktop/AMSN_Skin /usr/share/amsn/skins
[sudo] password for drakoumel: 
cp: cannot stat `/home/username/Desktop/AMSN_Skin': No such file or directory
drakoumel@drakoumel-desktop:~$ 
drakoumel@drakoumel-desktop:~$ sudo cp -r /home/username/Desktop/AMSN_Skin /usr/share/amsn/skins
cp: cannot stat `/home/username/Desktop/AMSN_Skin': No such file or directory
drakoumel@drakoumel-desktop:~$ 
drakoumel@drakoumel-desktop:~$ 
drakoumel@drakoumel-desktop:~$ 
drakoumel@drakoumel-desktop:~$ 
drakoumel@drakoumel-desktop:~$ sudo cp -r /home/username/Desktop/AMSN_Skin /usr/share/amsn/skins
cp: cannot stat `/home/username/Desktop/AMSN_Skin': No such file or directory
drakoumel@drakoumel-desktop:~$ sudo cp -r /home/drakoumel/Desktop/AMSN_Skin/usr/share/amsn/skins
cp: missing destination file operand after `/home/drakoumel/Desktop/AMSN_Skin/usr/share/amsn/skins'
Try `cp --help' for more information.
drakoumel@drakoumel-desktop:~$ sudo cp -r /home/drakoumel/Desktop/AMSN_Skin
cp: missing destination file operand after `/home/drakoumel/Desktop/AMSN_Skin'
Try `cp --help' for more information.
drakoumel@drakoumel-desktop:~$ sudo cp -r /usr/share/amsn/skins
cp: missing destination file operand after `/usr/share/amsn/skins'
Try `cp --help' for more information.
drakoumel@drakoumel-desktop:~$ sudo cp -r /home/username/Desktop/AMSN_Skin/usr/share/amsn/skins
cp: missing destination file operand after `/home/username/Desktop/AMSN_Skin/usr/share/amsn/skins'
Try `cp --help' for more information.
drakoumel@drakoumel-desktop:~$ sudo cp -r /home/username/Desktop/AMSN_Skin /usr/share/amsn/skins
cp: cannot stat `/home/username/Desktop/AMSN_Skin': No such file or directory
drakoumel@drakoumel-desktop:~$ sudo cp -r /home/drakoumel/Desktop/AMSN_Skin /usr/share/amsn/skins
cp: cannot stat `/home/drakoumel/Desktop/AMSN_Skin': No such file or directory


i mixed them up but i always got the same answer tho i went to see if it doesnt rly exists but i saw it usr/share etc still doesnt give me access

---

### Post by homemadejam on 2008-10-16
Okay mate, you will need to use the following command:
```
sudo cp -r /home/drakoumel/Desktop/AMSN_Skin /usr/share/amsn/skin
```

You have to be Root to copy / paste to the /usr directory.

Jam

---

