---
title: "Opening .sh Files"
date: 2008-07-12
forum: General Help
---

### Post by KeybladeSephi on 2008-07-12
Hello everyone; I have downloaded a number of .deb files and upon extracting them, the majority of the programs are shell script files. When I open these files, nothing happens. The default program to run these files is Wine. What program should I use to open these files? If there isn't a program to use, what is the command I should use in the terminal to open these files? Thank you =]

---

### Post by iaculallad on 2008-07-12
> **KeybladeSephi said:**
> Hello everyone; I have downloaded a number of .deb files and upon extracting them, the majority of the programs are shell script files. When I open these files, nothing happens. The default program to run these files is Wine. What program should I use to open these files? If there isn't a program to use, what is the command I should use in the terminal to open these files? Thank you =]

Set the SH file permission first to executable:

```
chmod u+x /path/some_linux_installation.sh
```

Then run it:
```

sh /path/some_linux_installation.sh
```

OR:

```
./some_linux_installation.sh
```

---

### Post by jonlemur on 2008-07-12
If you're trying to install .deb files, you should be able to just double click on the .deb file to install automatically.

Shell scripts you can usually run by ./scriptname.sh when you're in the directory the script is in.

---

### Post by dexter.deepak on 2008-07-12
if you are installind a .deb , you can simply double click it and the package installer opens. if it isnt installind , you need to install :
GDebi Package Installer
search for it in synaptic

---

### Post by KeybladeSephi on 2008-07-12
Yes, my problem isn't the deb file, but I didn't know how to open a .sh file. Thank you all for telling me how to open them =]. However, there is just one thing. iaculallad, when I tried to input "sudo chmod u+x /usr/bin/blahblahblah.sh", it said there was no such file or directory. Instead, I had to input "sudo chmod u+x /usr/bin/blahblahblah" without the ".sh" after it. So if anyone else can't find a problem and is typing that code, try it without the ".sh". Thanks again, everyone =D

---

### Post by latna on 2008-07-12
What are you trying to accomplish here? Open it how? Are you trying to see what's in it? Are you trying to run the command? Did you install the deb already?

I would understand better if you gave a step by step description of what you've done so far and what you expect to happen. How did you extract the deb and what do you mean by open the file? Those are 2 questions that come to mind.

---

### Post by kaiju on 2008-07-12
> **KeybladeSephi said:**
> [...]when I tried to input "sudo chmod u+x /usr/bin/blahblahblah.sh", it said there was no such file or directory. Instead, I had to input "sudo chmod u+x /usr/bin/blahblahblah" without the ".sh" after it. So if anyone else can't find a problem and is typing that code, try it without the ".sh". Thanks again, everyone =D

[deb]("http://en.wikipedia.org/wiki/Deb_(file_format") is the standard software package format on debian-based systems like ubuntu, which means that these systems open these files with a program that will *install* them on your system (like gdebi). however, a deb file is actually a regular archive, which means that you can *extract* it anywhere you want to, using an archive manager (like file-roller).

that said, your file can be in different places, depending on whether you installed or extracted it. installed software goes to /usr/bin (and/or several other directories), while extracted software goes wherever you extract it to.
generally, you shouldn't have to change any permissions in /usr/bin (packagers have already taken care of that for you), and if you want to change the permissions of any other file, you'll have to use chmod on that exact file (ex. if i extract a file to /home/bud/script.sh, i'll have to use chmod u+x /home/bud/script.sh and so forth)

[chmod]("http://en.wikipedia.org/wiki/Chmod") lets you change file permissions, and [sudo]("http://en.wikipedia.org/wiki/Sudo") gives you administrative rights so that you can change the settings of files outside your user directory.

i hope this makes things somewhat clearer.

---

