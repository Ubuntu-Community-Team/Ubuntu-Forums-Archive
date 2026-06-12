---
title: "[SOLVED] Is there a list of commands installed by apt-get?"
date: 2008-09-27
forum: General Help
---

### Post by particleMan86 on 2008-09-27
I tend to use apt-get for installing programs because it is faster and easier (for me) than the guis, especially for installing command-line utilities. But I sometimes run into the problem that after I install a package, I don't know what the name of the new command(s) is/are (in the common case that it doesn't match the package name).

For example:

Last night I installed the gnu-smalltalk package, and wanted to start the interpreter. The tutorial I was following suggested "mst" was the name of the command, but that command did not exist. I did a 

apt-cache showpkg gnu-smalltalk

but that didn't give me any useful information. It was only by hunting through /usr/bin that I was able to even identify potential commands (turned out to be gst).

On the online package-search (packages.ubuntu.com) there is a short description of the package that happens to include the name of the executable installed, but I am wondering if there is an apt option or utility (preferably cli) that will retrieve that information for installed packages without having to resort to a web browser.

---

### Post by particleMan86 on 2008-09-27
Nevermind, I found a solution. dpkg -L does the job quite nicely

---

