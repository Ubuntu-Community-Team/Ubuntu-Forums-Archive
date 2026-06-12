---
title: "nautilus samba problem"
date: 2008-11-02
forum: General Help
---

### Post by linuxgr on 2008-11-02
Hello everybody!

I really need your help, i have been searching for days and no luck. I am using ubuntu with gnome and fluxbox. There is no problem with gnome, but when I am using nautilus with fluxbox I cannot access my samba shares. Giving smb:/ in the address bar returns something like "cannot handle network". I guess it is missing something from the gnome configuration since it works fine in gnome, do you know what it needs?

Alternatively, is there another gui app to access smb shares? Or another file manager capable of doing so?

Thank you

---

### Post by cariboo on 2008-11-02
Install **smbfs** and see if that helps mount shares in fluxbox.

Jim

---

### Post by linuxgr on 2008-11-02
ok , but how can I use smbfs except from using it in terminal (mount -t smbfs .....). I need a file manager with samba support. you think that installing smbfs will help my issue with nautilus?

Thanks for your response.

---

### Post by linuxgr on 2008-11-02
I also found out that there is a package: libgnomevfs2-extra.

Its description:
GNOME VFS is the GNOME virtual file system.  It is the foundation of the
Nautilus file manager.  It provides a modular architecture and ships with
several modules that implement support for local files, http, ftp and others.
It provides an URI-based API, a backend supporting asynchronous file
operations, a MIME type manipulation library and other features.

This package contains extra VFS modules for the GNOME Virtual
File System.  It includes:
 * the bzip2 module;
 * the ftp module;
 * the http module (which also includes support for WebDAV);
 * the smb module, to browse Windows shares.


Could this be what I am looking for? It is already installed but how can I use it to work in fluxbox? anybody knows?

---

### Post by bab1 on 2008-11-03
The browsing problem you have sounds like a gvfs libs problem.  Doesn't your system already have the libs.  You said you have Gnome installed.  I think it is more along the lines of fluxbox not using the libs rather than the libs not installed.

Edit:  I believe if you manually config Samba via the /etc/samba/smb.conf you will not have these problems.  When sharing is configured via the GUI the configuration files are located at /var/lib/samba  (the standard location for Gnome configs).

---

### Post by linuxgr on 2008-11-03
As I said the libs are intsalled allright, nautilus works fine when in Gnome. But I can't use those modules in gnome vfs when in fluxbox.

What kind of configuration are you talking about? I have configured general settings and share folders using /etc/samba/smb.conf, not nautilus or gnome.(I am not a complete newbie) I can mount shares using the terminal. It is the PLUGIN I need for nautilus, so I won't have to use terminal tools to browse and mount shares. Can I achieve that by adding configuration to smb.conf?(it doesn't sound possible or relevant to me).

The trick is to find a way to make the libs useful in fluxbox, but how????

---

### Post by bab1 on 2008-11-03
> **linuxgr said:**
> ...
What kind of configuration are you talking about? I have configured general settings and share folders using /etc/samba/smb.conf, not nautilus or gnome.(I am not a complete newbie) I can mount shares using the terminal. It is the PLUGIN I need for nautilus, so I won't have to use terminal tools to browse and mount shares. Can I achieve that by adding configuration to smb.conf?(it doesn't sound possible or relevant to me).

The trick is to find a way to make the libs useful in fluxbox, but how????
I can then assume you DID NOT do the "right click >>share this..." thing then.  I don't know of any PLUGIN to allow fluxbox (the minimalist window manager) to use the Gnome (Nautilus) libs.  There are no tricks in my setup of smb.conf.  IMHO you are out of luck on this issue.

---

### Post by linuxgr on 2008-11-04
No, I have never shared my folders using nautilus but even if I did it doesn't matter, problem is that I cannot see the whole network by writing smb:/// on the address bar. I cannot even see the computer devices(locations). Both of these useful functions do not work when using nautilus+fluxbox.

Thanks for trying to help me....

---

### Post by utnubuuser on 2008-11-14
Hello -- was a solution found to this problem?  I'm having a similar problem, but in Gnome.  Nautilus wont open the network: Error message: Nautilus cannot handle network:locations.

Thanks

---

### Post by linuxgr on 2008-11-14
No, I have not yet found a solution, but I use fluxbox. You shouldn't be having trouble with gnome. Check if 

libgnomevfs2-extra

package is installed in your system.

---

### Post by karth on 2008-11-15
When launching fluxbox, gvfsd (the GVFS daemon) and gnome-volume-manager (which I understand are handling the "odd" urls like *smb:///* or *computer:///*) aren't run by default.

You'll have to alter **~/.fluxbox/startup** and add a few lines in the "daemons launching" section.

Look for this:
```
# Applications you want to run with fluxbox.
# MAKE SURE THAT APPS THAT KEEP RUNNING HAVE AN ''&'' AT THE END.
```

Add this:
```
/usr/lib/gvfs/gvfsd &
/usr/lib/gnome-volume-manager/gnome-volume-manager &
```

Of course, you can add anything else you want being launched at fluxbox's startup.
This fixed the issue for me eventually. Hope this helps.

---

### Post by linuxgr on 2008-11-15
GREAT!!!! That's what I was looking for!!!! the gnome-volume-manager! I had tried to start it just by typing it but only gnome-volume-manager-gthumb existed when I pushed Tab. now running /usr/lib/gnome...... gnome-volume-manager starts and the plugin woprks! Gvfsd was already running, probably because I have set gnome-settings to start with fluxbox so I can have the special buttons(volume etc) working.


Thanks again!!!

---

