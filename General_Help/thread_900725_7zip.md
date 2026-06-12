---
title: "7zip?"
date: 2008-08-25
forum: General Help
---

### Post by Exile666 on 2008-08-25
ok how do I use this. Stupid question I know, but I just installed this from Application -> Add/Remove, and I still can't view or extract .rar files. Is this app command line based? Little help please.

-- Exile --

---

### Post by -Zeus- on 2008-08-25
> **Exile666 said:**
> ok how do I use this. Stupid question I know, but I just installed this from Application -> Add/Remove, and I still can't view or extract .rar files. Is this app command line based? Little help please.

-- Exile --

can't you just use file-roller?

---

### Post by Exile666 on 2008-08-25
What's file-roller?

You must forgive me, I have only recent switched to Ubuntu.

---

### Post by ubuntu27 on 2008-08-25
You can not open or extract rar files you haven't instlled support for rar files YET.

You have to install  **unrar-free** from the terminal or synaptic package manager
The terminal is located at Applications menu/Accessories/Terminal

```
sudo apt-get install unrar-free
```

Then you should be able to "play" with rar files :)

---

### Post by jerome1232 on 2008-08-25
If you want to decrompress .rar files install unrar from the repos, also if you want to create .rar's, get rar while you are at it.
```
sudo apt-get install unrar rar
```

now file-roller should be able to decompress .rar's just like it does .gz's or .bzip2's

---

### Post by ubuntu27 on 2008-08-25
> **Exile666 said:**
> What's file-roller?

You must forgive me, I have only recent switched to Ubuntu.

File-Roller is the default Compressed File Manager for Ubuntu (it is installed by default). You can open, create a compression, and extract with it.

If you don't add support for rar files File-Roller and/or 7-Zip won't be able to open it.

```
sudo apt-get install unrar
```

---

### Post by Exile666 on 2008-08-25
That was the problem that I failed to mention. I have had unrar installed, but recently when I extract a .rar file, it always comes back asking for me to enter a password... and no... there wasn't a password.

---

### Post by ubuntu27 on 2008-08-25
> **Exile666 said:**
> That was the problem that I failed to mention. I have had unrar installed, but recently when I extract a .rar file, it always comes back asking for me to enter a password... and no... there wasn't a password.

Maybe someone other than you added a password...

---

### Post by forger on 2008-08-25
Try redownload the files, sometimes when you download them some of the parts break.

Can you post the links of the files? I'd like to check them out

---

### Post by Licurgo on 2008-08-25
Hey boy's:
I had down'ld a lot of rar's files and installed 7-zip and nothing happend, thank's a lost because I installed unrar and rar and now I can use 7-zip:)

---

