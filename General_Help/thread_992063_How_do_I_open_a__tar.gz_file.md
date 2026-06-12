---
title: "How do I open a  tar.gz file ?"
date: 2008-11-24
forum: General Help
---

### Post by circus_animals on 2008-11-24
I have downloaded a file for 'Real VNC'  and I don't know how to open it. I'm sure that's it a simple process when you know how. 
I would really appreciate it if someone could give me an idiots step by step guide or a link.I'm new to Linux , so please keep it simple.:confused:
Thanks for your help.

---

### Post by cmnorton on 2008-11-24
tar -xzf tar-file.tar.gz

tar -xjf tar-file.tar.bz2

---

### Post by unutbu on 2008-11-24
If you install archive manager (package name: file-roller), you can just double-click on the tar.gz and it will open.

If you like the command-line, then add this to your ~/.bashrc:
```

op () {
     if [ -f $1 ] ; then
        case $1 in
                *.tar.bz2)   tar xvjf $1        ;;
                *.tar.gz)    tar xvzf $1     ;;
                *.bz2)       bunzip2 $1       ;;
                *.rar)       unrar x $1     ;;
                *.gz)        gunzip $1     ;;
                *.tar)       tar xvf $1        ;;
                *.tbz2)      tar xvjf $1      ;;
                *.tgz)       tar xvzf $1       ;;
                *.zip)       unzip $1     ;;
                *.Z)         uncompress $1  ;;
                *.7z)        7z x $1    ;;
                *)           echo "'$1' cannot be extracted via extract()" ;;
        esac
     else
        echo "'$1' is not a valid file"
     fi
}
```

Then you can open any of the common archive formats from the command line with one simple command:
```

op file.tar.gz
```

for example.

---

### Post by redseventyseven on 2008-11-24
What sort of file is it? Is it an archive (like what is known in the Windows world as a zip file) or does it contain a program which you're trying to install?

---

### Post by circus_animals on 2008-11-24
Thanks for your help. Where do I get ' file-roller'?

---

### Post by circus_animals on 2008-11-24
> **redseventyseven said:**
> What sort of file is it? Is it an archive (like what is known in the Windows world as a zip file) or does it contain a program which you're trying to install?

This is the page : [http://www.realvnc.com/cgi-bin/download.cgi](http://www.realvnc.com/cgi-bin/download.cgi)

---

### Post by unutbu on 2008-11-24
circus_animals, one of the very best aspects of Ubuntu is its package management system. 
This guide, [http://www.psychocats.net/ubuntu/installingsoftware](http://www.psychocats.net/ubuntu/installingsoftware), explains how to install packages such as file-roller.

Having said that, I believe trying to install vnc for a tar.gz is most likely unnecessary.
(Thus you don't really need file-roller, at least for the moment).

If you are using Hardy or Intrepid, VNC is already installed. See
[http://maketecheasier.com/set-up-a-vnc-server-in-ubuntu-hardy-heron/2008/05/30](http://maketecheasier.com/set-up-a-vnc-server-in-ubuntu-hardy-heron/2008/05/30)

And here is a guide on using VNC:
[https://help.ubuntu.com/community/VNC](https://help.ubuntu.com/community/VNC)

It is true that tar.gzs may contain newer versions of software, but unless you know for sure that you need some newer feature, using the package supplied by the official repos will make life much easier.

---

### Post by circus_animals on 2008-11-24
> **unutbu said:**
> circus_animals, one of the very best aspects of Ubuntu is its package management system. 
This guide, [http://www.psychocats.net/ubuntu/installingsoftware](http://www.psychocats.net/ubuntu/installingsoftware), explains how to install packages such as file-roller.

Having said that, I believe trying to install vnc for a tar.gz is most likely unnecessary.
(Thus you don't really need file-roller, at least for the moment).

If you are using Hardy or Intrepid, VNC is already installed. See
[http://maketecheasier.com/set-up-a-vnc-server-in-ubuntu-hardy-heron/2008/05/30](http://maketecheasier.com/set-up-a-vnc-server-in-ubuntu-hardy-heron/2008/05/30)

And here is a guide on using VNC:
[https://help.ubuntu.com/community/VNC](https://help.ubuntu.com/community/VNC)

It is true that tar.gzs may contain newer versions of software, but unless you know for sure that you need some newer feature, using the package supplied by the official repos will make life much easier.

Thanks a lot for that. 
I'm using Kubuntu 8.04
There seems to be bits of info here and bits of info there about Linux. I think that I'll have to get myself a book and get a good overview .
Thanks again for the links .:popcorn:

---

### Post by oldos2er on 2008-11-24
In Kubuntu, Ark Manager is the program you want to look for.

---

### Post by philinux on 2008-11-24
> **circus_animals said:**
> I have downloaded a file for 'Real VNC'  and I don't know how to open it. I'm sure that's it a simple process when you know how. 
I would really appreciate it if someone could give me an idiots step by step guide or a link.I'm new to Linux , so please keep it simple.:confused:
Thanks for your help.

Mostly just double click the file to extract the contents. Archive managers are installed as default.

---

