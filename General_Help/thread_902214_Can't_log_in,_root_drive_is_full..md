---
title: "Can't log in, root drive is full."
date: 2008-08-27
forum: General Help
---

### Post by martal on 2008-08-27
Kubuntu Hardy. This from my XP partition.

I have been downloading some big files for the last week or so. I eventually got errors when trying to move them to another partition. I think a tmp file relating to the downloads was full.

An XP partition manager tells me that / is full. 8KB left!

As a result, I can't log in. Last time I could there was no internet, couldn't save a file, capslock gone, numlock gone.

How can I clean up root from the command line?

---

### Post by iaculallad on 2008-08-27
> **martal said:**
> Kubuntu Hardy. This from my XP partition.

I have been downloading some big files for the last week or so. I eventually got errors when trying to move them to another partition. I think a tmp file relating to the downloads was full.

An XP partition manager tells me that / is full. 8KB left!

As a result, I can't log in. Last time I could there was no internet, couldn't save a file, capslock gone, numlock gone.

How can I clean up root from the command line?

```
sudo apt-get clean
sudo apt-get autoremove
```

---

### Post by blooddrunk on 2008-08-27
If I understood correctly, you should do the following:

When the login GUI comes out, press Ctrl+Alt+F1 (or any button between F1 and F6). Then login, then do "sudo su". Now, the only thing left is the command: "rm -r file" (where file is the name and the path of the file or directory you want to delete). Hope that helps!

---

### Post by martal on 2008-08-27
iacullalad, disk is almost completely full. No internet and no space for new apps.

blooddrunk, I don't know where the files that I need to delete are.

I am in the live CD now. Where are these huge temp files?

---

### Post by Elfy on 2008-08-27
Boot the recovery option, when you get the samll menu - pick the root prompt one and run iaculallad's commands, then type exit and you will be back at the menu - resume normal boot from there.


Once in - then run ```
df -h
``` and paste it here.

---

### Post by martal on 2008-08-27
forestpixie, at the recovery root prompt, running sudo apt-get clean resulted in nothing, autoremove resulted in 0 to install, 0 to remove etc.

Proceeding to normal boot, 'could not start kdestartupconfig'

When on the live CD, the / drive in question (not the live CD root) reports 8Kb remaining.

I am still locked out.

---

### Post by Elfy on 2008-08-27
Can you boot the livecd and move data off the drive or resize it?

You can run df -h from the recovery boot, if there was nothing in the apt cache then apt-get clean wouldn't make a difference.

---

### Post by martal on 2008-08-27
Resizing the partition is an option. How would I then find where these files are, or whatever is filling the disk?

I think they are from Firefox downloads, not from apt. Firefox private data is/was cleared, I am sure. I will have to check that, but there is a limit anyway on the Firefox cache, so it can't be that.

Need to finish some work on XP, then will resize. Only a couple of gigs up.

---

### Post by mssever on 2008-08-27
In the live CD, make sure the relevant partitions are mounted. Then, run baobab to get a graphical view of where your huge files are. Then you can delete as appropriate.

EDIT: Oh, you're using Kubuntu. Baobab is a Gnome app. Unless You've got an Ubuntu live CD hanging around, you might have to settle for using df -h at various places on the filesystem. Unless KDE has an equivalent to Baobab, or unless you install Baobab from the live CD.

---

### Post by martal on 2008-08-27
mssever, I have an ubuntu live CD also. Thanks for the tip.

---

### Post by martal on 2008-08-28
Well, baobab didn't reveal to me where the big files are. But there were limitations on what it was reporting from the live Cd. For example, .mozilla was reported empty. (It's not.)

I now have a Windows utility, Ext2IFS, which enables me to read and write to Linux file systems. This is reporting the same size for Root as gparted. I can't find the files/dark matter with a Windows Disk Analyser either.

Any idea where they might be hiding?

I used gparted to increase the size of root, giving me an extra 1.5 GB.

Now my wireless keyboard is working at login, but I still get 'could not start kdestartupconfig' and drop back to a command prompt.

---

### Post by unca.paka on 2008-08-28
What exactly were you downloading before all this happened?

---

### Post by mssever on 2008-08-28
The fact that baobab reported ~/.mozilla as empty is suspect. It might mean that your partition is partially corrupted. Try running fsck on it.

---

