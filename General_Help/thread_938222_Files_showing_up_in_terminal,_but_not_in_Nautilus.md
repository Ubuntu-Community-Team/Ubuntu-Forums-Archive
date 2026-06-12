---
title: "Files showing up in terminal, but not in Nautilus"
date: 2008-10-04
forum: General Help
---

### Post by elmer_42 on 2008-10-04
OK, so I installed Ubuntu 8.04 on a computer that was given to me by a friend. It's going to be used by my sister, and she needed to have all of her documents. Easy, just pull out the HDD in her (broken) machine and put it into this new one. It's working just fine, except for one oddity.

When I go to her "My Documents" folder (/media/disk/Documents and Settings/Owner/My Documents) in Nautilus there are supposedly no files. However, when go to her "My Documents" folder in the terminal and do an [FONT="Courier New"]ls[/FONT], all of her documents show up. What do you think is wrong?

---

### Post by elmer_42 on 2008-10-04
Hmm, nobody knows? Well, guess I'll try the best I can. =/

---

### Post by Vasto on 2008-10-05
I'm having this problem also on an External USB hard drive. If I figure anything out I'll post here.

It's strange. I can successfully unrar files in folders that don't show up in nautilus. So I don't think it is data corruption because I believe rar files have CRC checks

---

### Post by scouser73 on 2008-10-05
Could it possibly be hidden folders?, Just a guess like.

---

### Post by /////// on 2008-10-05
If its hidden folders, just go into the folder in nautilus and press ctrl+h

---

### Post by Vasto on 2008-10-05
It's not hidden folders. None of them have the . prefix. Also, they show up in a normal ls.

---

### Post by -Zeus- on 2008-10-05
could you post the output of at least one line from ls -l? (that's a l)

---

### Post by ad_267 on 2008-10-05
I think it could be the file permissions. The directory may not have read permissions set.

---

### Post by Mister.Vash on 2008-10-05
Did you setup two different accounts?  One for your sister and one for you?  Is the terminal an nautilus both running under the same account?

Like the previous poster, Zeus suggested, can you post the output of 'ls -la'

Also, what is the name you log on to use nautilus.

---

### Post by Vasto on 2008-10-06
For me at least it isn't file permissions. The files don't show up even when I "sudo nautilus". However one thing that did work was moving the files with the terminal. It worked for the one file I tried. I'm going to look up some bash commands tomorrow to see if I can move all the folders while keeping the folder names.

EDIT: Interesting note though. If I move the files back into the original directory, they dissappear again.

EDIT:: I fixed my problem. From the terminal:
```

mkdir Temporary
mv Problem_Directory Temporary

```

Then from the GUI you should be able to see those files. And you can cut and paste them to wherever you want. It is a strange bug that I'm not sure what it was caused by.

---

