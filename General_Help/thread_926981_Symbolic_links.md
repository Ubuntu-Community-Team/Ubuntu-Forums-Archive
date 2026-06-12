---
title: "Symbolic links?"
date: 2008-09-22
forum: General Help
---

### Post by xeriouxi on 2008-09-22
Hi!

I'm struggling to find any information about symbolic links in Ubuntu, or what they are for that matter.

To my basic knowledge they are like shortcuts, yes? When I install the game Doom 3, for example, I have to type 'doom3' into the terminal or place it in a launcher to get the game working. Where are these symbolic links stored? I assume they all have to be in one place so that they can be found, right? And how would I go about creating them if I needed to in the future?

Thanks for any help! =)

---

### Post by timcredible on 2008-09-22
they are pointers to other files.  they are stored wherever you create them.  open a terminal session and type ```
man ln
``` to learn more about how to create them.

---

### Post by retrow on 2008-09-22
In most cases, the symbolic links are stored under /usr/local/bin.

If you want to create a link for a particular application/script, use:

```
sudo ln -s PathOfRequiredApplication /usr/local/bin
```

---

### Post by Titan8990 on 2008-09-22
A symbolic link would be the equivalent of a Windows shortcut. It simply points to a file in a different directory.  

"Where are these symbolic links stored?"

When you type in a command to say launch a game it is not always a symbolic link. It just checks your system paths for files matching the name of the command you gave. Game executables are usually located in the /usr/games directory.

You can check your default path with the following command:

jordan@einstein:~$ echo $PATH
/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games


Another example is when you use the ifconfig command. When you type "ifconfig" in to the terminal it looks in the PATH directories for a file matching the name "ifconfig".

It will find it in /usr/sbin (or /sbin if using a non-debian based distro) and then execute the program ifconfig there.

I hope that explains it somewhat.

For more information you can check on the "ln" command which creates symbolic and hard links.

man ln

The -s argument needs to be given for a link to be symbolic.

---

### Post by dodle on 2008-09-22
You can also create [symbolic] links in the gui by right clicking an executable and selecting 'create link'.

---

