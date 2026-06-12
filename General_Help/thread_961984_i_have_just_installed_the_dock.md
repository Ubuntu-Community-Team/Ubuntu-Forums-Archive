---
title: "i have just installed the dock"
date: 2008-10-28
forum: General Help
---

### Post by dsjoes on 2008-10-28
i have just installed the dock and i keep getting this message
```

'E:Type ‘echo’ is not known on line 63 in source list /etc/apt/sources.list, E:The list of sources could not be read.'
```

---

### Post by cyfur01 on 2008-10-28
Sounds like your sources.list file has been modified. You can veryify this using the following command:```
cat /etc/apt/sources.list | grep echo
``` If that command outputs anything, then that confirms the file has been modified.

If so, try commenting out those lines (in a text editor, add a '#' to the beginning of each line that has an echo command on it) and see if that helps. Otherwise, post a copy of your sources.list file for further troubleshooting.

---

### Post by ad_267 on 2008-10-28
I'm going to guess you followed a guide for installing the dock incorrectly and added that line to the file instead of entering it as a command. You can use "cp /etc/apt/sources.list /etc/apt/sources.list.bak" to make a backup and then edit it with "gksu gedit /etc/apt/sources.list" to remove the lines you added.

---

### Post by dsjoes on 2008-10-28
i have attached the source file the very last 2 line are what have been added.
[here]("http://www.simplehelp.net/2007/05/31/how-to-install-setup-and-use-avant-window-navigator-awn-in-ubuntu-feisty/") is the guide i used it says add the two lines to the bottom and thats what i did

---

### Post by ad_267 on 2008-10-28
Ok it wasn't those lines that were the problem, it's the lines for reacocard-awn.

These lines need removing:
```

echo 'deb-src http://ppa.launchpad.net/reacocard-awn/ubuntu intrepid main'
 sudo tee -a /etc/apt/sources.list

```
```
echo 'deb http://ppa.launchpad.net/reacocard-awn/ubuntu hardy main'  |  sudo tee -a /etc/apt/sources.list
```

```
echo 'deb-src http://ppa.launchpad.net/reacocard-awn/ubuntu hardy main'
sudo tee -a /etc/apt/sources.list
```

It looks like you now have two sources for AWN in your sources.list file so you can probably remove one of them. Either the reacocard lines or the
tuxfamily ones. I would remove the tuxfamily ones because they look older, I was using the reacocard ppa in Hardy.

The "echo '...' | sude tee -a /etc/apt/sources.list" is actually a command that will append a line to the file.

---

### Post by dsjoes on 2008-10-28
thanks i remove all the text from the three boxes that you had put and it has stopped.
:biggrin:

---

### Post by dsjoes on 2008-10-28
i have just gone on to the add/remove applications and got the following error 
```
Failed to fetch http://download.tuxfamily.org/syzygy42/dists/feisty/avant-window-navigator/binary-i386/Packages.gz  404 Not Found
Failed to fetch http://download.tuxfamily.org/syzygy42/dists/feisty/avant-window-navigator/source/Sources.gz  404 Not Found
Some index files failed to download, they have been ignored, or old ones used instead.
```

---

### Post by dsjoes on 2008-10-28
never mind i think i have sorted it

---

### Post by ad_267 on 2008-10-28
You can probably remove those lines because the reacocard ppa is more up to date.

---

