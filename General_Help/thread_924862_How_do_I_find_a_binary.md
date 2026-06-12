---
title: "How do I find a binary?"
date: 2008-09-20
forum: General Help
---

### Post by Canadian_Psycho on 2008-09-20
I clicked on a video stream file recently and firefox asked me what program I wanted to use to open the file.  I went hunting for VLC media player and realized that I had no idea where the binary was for this program which I installed via the add/remove applications tool.

How do I find program binaries when firefox asks me for them?

Cheers

---

### Post by p_quarles on 2008-09-20
Most programs are installed in /usr/bin. To find out for sure, run:
```
which program_name
```

---

### Post by Mister.Vash on 2008-09-20
You can open a terminal window and usage the 'which' command

which vlc

should output something like the following:
/usr/bin/vlc

which is the path and the file

---

### Post by mb_webguy on 2008-09-20
The [file structure in Linux]("http://en.wikipedia.org/wiki/Filesystem_Hierarchy_Standard") is pretty straightforward once you get the hang of it.  

By default all installed applications are located in the /usr directory.  Executables are located in the /usr/bin or /usr/local/bin directories, while support files are located in the /usr/share or /usr/local/share directories, respectively.  The difference between the /usr and the /usr/local directories is that applications installed from the repositories are usually installed to /usr, while applications installed by other means, such as from source, are usually installed to the /usr/local directory.

And as Mister.Vash said, to find where a specific application is located, you can use the whereis command in the terminal.

---

