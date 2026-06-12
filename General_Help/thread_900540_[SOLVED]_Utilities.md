---
title: "[SOLVED] Utilities?"
date: 2008-08-25
forum: General Help
---

### Post by Yezinki on 2008-08-25
Hi there,

1. How is disk clean up......like temp files, restores etc cleaned in Ubuntu variants?

2. Does Ubuntu have a registry & how can it be accused/modified,errors removed etc?

Thanks!

---

### Post by soxs on 2008-08-25
> **Yezinki said:**
> Hi there,

2. Does Ubuntu have a registry & how can it be accused/modified,errors removed etc?

Simple: There is none.

I am not quite sure about #1...

---

### Post by Yezinki on 2008-08-25
I appreciate the input!

Regards!

---

### Post by WRDN on 2008-08-25
If I understand your first request correctly, then the following commands may be useful:

```

sudo apt-get autoremove
sudo apt-get autoclean

```

These will remove unneeded packages. You can also use "sudo apt-get clean" to remove all downloaded packages in the cache (/var/cache/apt/archives)

---

### Post by Yezinki on 2008-08-25
Wow WRDN you are a Linux OS genius.......your knowledge is comparable to the ocean depth!

---

### Post by Yezinki on 2008-08-25
Thanks WRDN again ......System is less bloated now........i can feel it........4 variants of Ubuntu & KD4.1........i can feel the difference after I ran those commands in the Terminal.........simply super IQ man.

---

### Post by mssever on 2008-08-25
> **Yezinki said:**
> 1. How is disk clean up......like temp files, restores etc cleaned in Ubuntu variants? In addition to the package cleanup commands given above, here are some things to note:

[LIST=1]
[*]Well behaved programs keep temporary files in /tmp. That directory is automatically cleaned on boot.
[*]Programs usually keep user-specific settings in files and directories whose names begin with a dot, and these live in your home directory (in Nautilus, hit <Ctrl>H to see all files, since dotfiles are hidden by default). If you no longer use a program, you can look for these dotfiles and delete the dotfiles created by that program. In general, it should be safe to delete those dotfiles at anytime, but if you do so, all the settings that the deleted file controls will revert to their defaults.
[/LIST]
 
> 2. Does Ubuntu have a registry & how can it be accused/modified,errors removed etc?No, but Gnome uses gconf which is vaguely similar to a registry (but far superior). Run gconf-editor to access it.

---

### Post by Yezinki on 2008-08-25
Thanks for the info,

1. How does one delte those dot files?

---

### Post by WRDN on 2008-08-25
> **Yezinki said:**
> Thanks for the info,

1. How does one delte those dot files?

Just open the directory, and press Ctrl + H (or click View > Show Hidden Files). Then, delete the settings you no longer want, using the normal file deleting procedure (select and press Delete).

---

### Post by Yezinki on 2008-08-25
Thanks WRDN again & again..........

---

### Post by Yezinki on 2008-08-25
Have a History of 4 days how do I delete all with 1 command?

Rt Click & delete?

---

### Post by soxs on 2008-08-26
> **Yezinki said:**
> Have a History of 4 days how do I delete all with 1 command?

Rt Click & delete?

What history??? Plx explain

---

### Post by Yezinki on 2008-08-26
Ctrl + H.........History!

---

### Post by WRDN on 2008-08-26
> **Yezinki said:**
> Ctrl + H.........History!

That still doesn't explain what history you are trying to Delete. If you mean the history in Firefox, then either right click on the day/ entry and select Delete, or click Tools > Clear Private Data, and check the "Browsing History" box.

---

### Post by Yezinki on 2008-08-26
Exactly Super Genius man.

Regards!

---

