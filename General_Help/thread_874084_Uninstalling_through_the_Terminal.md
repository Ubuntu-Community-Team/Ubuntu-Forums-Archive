---
title: "Uninstalling through the Terminal"
date: 2008-07-29
forum: General Help
---

### Post by Kozy on 2008-07-29
Hello. The linux version of a program I use (Magic Set Editor) decided to crap out on me recently. This program doesn't have an uninstall file, but my brother said I could do it through the terminal but he didn't tell me how, as he was busy. So if someone here could inform me of how to do so, that would be great. I use Ubuntu. I'm not sure which version, however.

Hope you can help me.
Thank you.

---

### Post by Diabolis on 2008-07-29
```
sudo apt-get --purge remove *"application name"*
```

Not sure if that will work because I don't know how you installed it. Give it a try if it doesn't work, post back and tell us how you installed it.

---

### Post by Kozy on 2008-07-29
I installed it by running the install file that I got when I downloaded the program. I didn't run it in the terminal. My brother told me something about having to open the install file in the terminal and then some code to uninstall it. Anything like that ring a bell?

---

### Post by RuleMaker on 2008-07-29
Then it was probably a deb package, then use:
```
sudo dpkg -r <package name>
```

---

### Post by Diabolis on 2008-07-29
Just to be 100% sure. Are we talking about this application: [http://magicseteditor.sourceforge.net/](http://magicseteditor.sourceforge.net/) ?

---

### Post by Kozy on 2008-07-29
Yeah, the Linux Version.

---

### Post by Diabolis on 2008-07-29
Ok, I just downloaded it.

The readme says this:
> Magic Set Editor stores data only in the primary installation directory, a symlink to the executable at /usr/local/bin, and in ~/.magicseteditor. 
If you need to uninstall, removing these directories should completely purge your system.

and the installation script says this:
> # This script installs Magic Set Editor onto your system.
# If executed as root (including via sudo), it is installed to /usr/local/share/magicseteditor. (with an executable symlink in /usr/local/bin)

So what you need to uninstall it is this:
```
sudo rm -r /usr/local/share/magicseteditor
sudo rm -r .magicseteditor
```

Then go to this folder: **/usr/local/bin/**
find a file related to magic set editor, its a short cut. Once you know how its called, delete it with this command:
```
sudo rm /usr/local/bin/*"name of file"*
```

be very careful with this commands, because if you do it wrong you could wreck your whole system.

**rm** means remove
**rm -r** means remove recursively, this means that it will remove everything inside a folder including folders inside it.

[SIZE="4"]So never run this: **[COLOR="Red"]sudo rm -r /[/COLOR]** it will crash completely your system.

Recommended reading: [malicious commands]("http://ubuntuforums.org/announcement.php?f=326")
[/SIZE]

---

### Post by Kozy on 2008-07-29
Hmm. Something strange just happened. I entered in the code on the terminal, and it gave me this

> rm: cannot remove `/usr/local/share/magicseteditor': No such file or directory
kozyjames@Sleeky:~$ sudo rm -r .magicseteditor

But before I even entered that code, I looked to make sure the file was there. It is there, but there's some sort of arrow in the upper-right corner of the file. Does that change anything?

---

### Post by Diabolis on 2008-07-29
What do you mean with "some sort of arrow in the upper-right corner of the file"?

If its in the name of the file, then yes, add it to the command.

You can get the exact path to the file by "tabbing" to it.

Type in the terminal this:
```
/usr/local/share/m
```

Then press two times the tab key so it will show you all the possible options available in that directory.

---

### Post by Kozy on 2008-07-29
No, I mean of the Icon, sorry.

---

### Post by Diabolis on 2008-07-29
No, that doesn't matter. Just worry about the name of the files.

You can list the contents of a folder with this command:
```
ls
```

---

### Post by Kozy on 2008-07-29
Well the original command decided to work, suddenly. So thank you very much! I hope when i reinstall it, it works fine.

---

### Post by Diabolis on 2008-07-29
Ok, if everything goes well, don't forget to mark the thread as solved.

---

### Post by Kozy on 2008-07-29
Okay. Could you tell me quick here how to install it in the terminal? Or would I have to start another thread?

---

### Post by Diabolis on 2008-07-29
Yeah, **cd** to the folder in which the installation script is and make it executable with this command:
```
chmod +x install
```

Then execute it with this command:
```
sudo ./install
```

---

### Post by Kozy on 2008-07-29
how do you "CD" to the folder?

---

### Post by Diabolis on 2008-07-29
Lets suppose that the folder is in your desktop.

You would have to type:
```
cd Desktop
```

Then:
```
cd magicseteditor
```

You can also do it in one step:
```
cd Desktop/magicseteditor/
```

---

### Post by Kozy on 2008-07-29
well it worked just swimmingly. Thank you for all your help! I'll be sure to change my original post to "solved"

---

### Post by Diabolis on 2008-07-29
Great :guitar:

---

### Post by Kozy on 2008-07-29
although, I actually don't know how to change my thread prefix..

---

### Post by Diabolis on 2008-07-29
hehe at the top of the thread, Thread tools / mark as solved.

---

