---
title: "How to share a Folder via the Command line"
date: 2008-10-26
forum: General Help
---

### Post by bmxmann on 2008-10-26
Hello,

I just installed Ubuntu server 8.0.4.1 and I am now starting to set up Apache.  I created a new folder specifically for my site, but would like to be able to browse to it from my desktop (which is running Ubuntu Hardy Desktop).  I do not have a GUI installed on the server, and perfer to keep it that way (trying to learn the CLI better).  I just do not know how to share this folder so I can browse to it from my desktop.  I can currently see the server from my desktop, and it comes up with a print folder, but I just have no idea on how this is done.

I want to be able to make my HTML files on my desktop then just copy them to the server.

I did a search online but was unable to find anything.

Thanks for the help, I am sure its something simple.

---

### Post by unutbu on 2008-10-26
One method is to use rsync:

To copy a file from desktop to server:```

rsync -a /path/to/file user@server:/path/to/target

```
To copy a directory from desktop to server:```

rsync -a /path/to/dir/ user@server:/path/to/target_dir
```

An alternative method is to use scp:
To setup scp:

Type on server:```

sudo apt-get install openssh-server
```

Type on desktop:```

sudo apt-get install openssh-client
```

To copy a file from desktop to server:```

scp /path/to/file user@server:/path/to/target

```
To copy a directory from desktop to server:```

scp -r /path/to/dir/* user@server:/path/to/target_dir
```

scp works a lot like cp, except that you can copy to other computers. The transfer is encrypted too.


The rsync and scp commands can also be used to transfer files from the server to the desktop; just reverse the order of the arguments.

---

