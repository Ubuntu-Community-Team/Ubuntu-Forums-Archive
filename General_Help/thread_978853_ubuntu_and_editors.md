---
title: "ubuntu and editors"
date: 2008-11-11
forum: General Help
---

### Post by born2 on 2008-11-11
dose ubuntu have an editor like crimson editor built in or if not what is a good editor to use thanks

---

### Post by Portmanteaufu on 2008-11-11
gedit is a good, multi-purpose text editor with tabs. It does syntax highlighting for a lot of languages.

---

### Post by jespdj on 2008-11-11
gedit is the default editor that comes with Ubuntu. It works well and you can get plugins for it for additional functionality.

There are lots of text editors for Ubuntu (emacs, nano, vi, geany, ...).

---

### Post by spibou on 2008-11-11
Ubuntu has vim.tiny built-in and you can download the full version from the repositories. The most powerful editors are vim and emacs, both with many facilities for editing source code and both with their own programming language to enhance their already abundant capabilities. But with both you would need to invest a certain amount of time to become proficient and get advantage of their features. With vim in particular you won't be able to do even the most basic things without reading a tutorial first. There are also IDEs like Eclipse or Sun Studio 12; the latter also contains compilers.

If you need to edit a file "now" I suggest nano or gedit.

---

### Post by born2 on 2008-11-11
ok ill give them a go if i download a .tar.gz file witch way do i go about installing it

---

### Post by fballem on 2008-11-11
For vim and nano, just install from the repositories using Synaptic.

For NetBeans, download from the Sun site and save the file to your desktop. Then open a terminal and type:
```
cd Desktop
```
```
sudo sh xxx
```, where xxx is the exact name of the NetBeans file that you downloaded.

Don't know about the Sun Studio, but I'm pretty sure that there are a good set of instructions, either on the Sun website or contained within the download file.

---

### Post by spibou on 2008-11-11
> **born2 said:**
> ok ill give them a go if i download a .tar.gz file witch way do i go about installing it
As has been said already it's much easier to use the repositories. Apart from Synaptic, do also **man apt-get** For Sun Studio 12 you need to do it Sun's way; just google for it. You don't get source code either, but it's a free download.

If you want to install from source for some reason then you put the tar.gz file into its own directory. Then you do **gzip -dc *tar.gz | tar xf -**

You go to the subdirectory created and read the files README and possibly INSTALL and follow the instructions in there. Ask here if you don't understand something.

---

