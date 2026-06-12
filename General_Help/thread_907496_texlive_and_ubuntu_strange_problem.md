---
title: "texlive and ubuntu strange problem"
date: 2008-09-01
forum: General Help
---

### Post by Kalidor on 2008-09-01
I just installed texlive 2008 from CD (not synaptic) and whenever i write 
sudo texhash or sudo mktexlsr it just says "command not found". 
WTF?

Thanks in advance

---

### Post by unutbu on 2008-09-01
It may be the case that the TeXLive CD installs executables in a non-Ubuntu-ish directory which is not in your PATH.

You can add it to your PATH after you find out where it is.

To find texhash, type
```

sudo updatedb  # Get a cup of coffee
locate texhash
```

---

### Post by Kalidor on 2008-09-02
it's located in /usr/bin/texhash. What now?

---

### Post by unutbu on 2008-09-02
Hm. 

/usr/bin/texhash is a symlink to mktexlsr:
```
  lrwxrwxrwx  1 root   root           8 2008-06-08 12:52 texhash -> mktexlsr
```

Is mktexlsr in /usr/bin too?

Please post```


ls -l /usr/bin/texhash
ls -l /usr/bin/mktexlsr
```

(PS. I was wrong about PATH being the problem. You must have /usr/bin in your PATH or else lots of common commands such as sudo would not work.)

---

### Post by Kalidor on 2008-09-02
"Command 'ls' is available in '/bin/ls'
The command could not be located because '/bin' is not included in the PATH environment variable."


Gotta say I fooled around with editing bashrc bash.bashrc and i also wrote source ~/.bashrc and source /root/.bashrc

Fooled around means I added the line PATH=/usr/bin; export PATH to those files. But I just deleted it and it still doesn't work.

---

### Post by unutbu on 2008-09-02
With no PATH lines in your ~/.bashrc, log out and log back in.
Then maybe texhash will work.

If not, type
```
echo $PATH
```

You should see
```

/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games

```
If you wish to add new paths to PATH, edit ~/.profile, instead of ~/.bashrc.
Add
```
PATH=$PATH:/new/path
export PATH
```

The problem with PATH=/usr/bin is that you lose all the other default paths.

---

### Post by Kalidor on 2008-09-02
ok. everything else is restored but the other things still don't work. The output of the requested commands is 
ls: cannot access /usr/bin/texhash: No such file or directory
ls: cannot access /usr/bin/mktexlsr: No such file or directory

---

### Post by unutbu on 2008-09-02
Please post the output of 
```

ls -ld /usr
ls -ld /usr/bin
```

---

### Post by Kalidor on 2008-09-02
drwxr-xr-x 12 root root 312 2008-04-24 21:38 /usr
drwxr-xr-x 2 root root 42752 2008-09-02 14:07 /usr/bin

---

### Post by tacutu on 2008-09-02
AFAIK, Texlive installs in /usr/local/texlive. When you install it, you have an option to create symbolic links, which are put in /usr/local/bin. Unless you changed the default option, texhash + friends shouldn't be in /usr/bin. Have you also installed the texlive from the ubuntu repositories?

If you dont't have the symlinks in /usr/local/bin, you can either create them or add to your .bashrc file:
```
export PATH=$PATH:/usr/local/texlive/2008/bin/i386-linux/
```
(the path may differ, depending on your system)
Also, I recommend adding the following line to .bashrc:
```
export TEXMFCNF=/usr/local/texlive/2008/texmf/web2c/
```
it saves some trouble with evince generating fonts.

---

### Post by Kalidor on 2008-09-02
Ok, what worked for me was reinstalling texlive choosing the option to add the symlinks to different paths but not actually changing the paths. I don't think this was the crucial part tho'. I probably just had to re install.
Thanks for your help.

---

### Post by gnwiii on 2008-12-27
> **tacutu said:**
> [...]
Also, I recommend adding the following line to .bashrc:
```
export TEXMFCNF=/usr/local/texlive/2008/texmf/web2c/
```
it saves some trouble with evince generating fonts.

What trouble?  Is it the "texmf.cnf not found"? warning:

$ evince story.dvi

warning: Configuration file texmf.cnf not found! Searched these directories:
/usr/share/texmf/web2c:/usr/share/texmf-texlive/web2c:/usr/local/share/texmf/web2c
Trying to proceed...

You would think it would look in /etc/texmf
There is a similar problem with tkdvi.  Both programs do create bitmaps for .pk fonts used in a .dvi file, using mktexpk from "real" TeX Live 2008 (RTL), but doesn't render the file using type 1 versions.  If it runs tools from Ubuntu's texlive (UTL), then there will be problems if UTL lacks some font installed for RTL, but if these fonts are installed in some user tree added via /usr/local/texlive/2008/texmf.cnf or elsewhere, your setting won't help, but would cause problems for RTL tools.

TeX Live 2008 has changed the way the texmf.cnf file is handled -- it reads multiple files, so it is easier to customize, e.g., where the 
main directory is r/o on a server.  The default setting is:

$ kpsewhich --expand-var=\$TEXMFCNF
{/usr/local/texlive/2008/bin,/usr/local/texlive/2008}{,{/share,}/texmf{-local,}/web2c}

evince doesn't handle this value, so the trick only works if all you
really use is /usr/local/texlive/2008/texmf/web2c/texmf.cnf

A better approach might be to create a wrapper script for evince
that sets TEXMFCNF just for evince, but it won't help people who use
the multiple texmf.cnf file capabilities in RTL.

$ cat /usr/local/bin/tlevince
#! /bin/bash
# tlevince -- set TEXMFCF to use the TeX Live 2008 texmf trees
export TEXMFCNF='{/usr/local/texlive/2008/bin,/usr/local/texlive/2008}{,{/share,}/texmf{-local,}/web2c}'
exec /usr/bin/evince "$@"

The portability problems for texlive binaries get much worse if you
want to include gui tools that don't use a cross-platform GUI environment, and people want to see versions that are consistent with the other tools they use.  It would be interesting to see if there are ways to tweak evince to support multiple distros.

---

### Post by gnwiii on 2008-12-28
> **tacutu said:**
> [...]
Also, I recommend adding the following line to .bashrc:
```
export TEXMFCNF=/usr/local/texlive/2008/texmf/web2c/
```
it saves some trouble with evince generating fonts.

What trouble?  Is it the "texmf.cnf not found"? warning:

$ evince story.dvi

warning: Configuration file texmf.cnf not found! Searched these directories:
/usr/share/texmf/web2c:/usr/share/texmf-texlive/web2c:/usr/local/share/texmf/web2c
Trying to proceed...

You would think it would look in /etc/texmf
There is a similar problem with tkdvi.  Both programs do create bitmaps for .pk fonts used in a .dvi file, using mktexpk from "real" TeX Live 2008 (RTL), but doesn't render the file using type 1 versions.  If it runs tools from Ubuntu's texlive (UTL), then there will be problems if UTL lacks some font installed for RTL, but if these fonts are installed in some user tree added via /usr/local/texlive/2008/texmf.cnf or elsewhere, your setting won't help, but would cause problems for RTL tools.

TeX Live 2008 has changed the way the texmf.cnf file is handled -- it reads multiple files, so it is easier to customize, e.g., where the 
main directory is r/o on a server.  The default setting is:

$ kpsewhich --expand-var=\$TEXMFCNF
{/usr/local/texlive/2008/bin,/usr/local/texlive/2008}{,{/share,}/texmf{-local,}/web2c}

evince doesn't handle this value, so the trick only works if all you
really use is /usr/local/texlive/2008/texmf/web2c/texmf.cnf

A better approach might be to create a wrapper script for evince
that sets TEXMFCNF just for evince, but it won't help people who use
the multiple texmf.cnf file capabilities in RTL.

$ cat /usr/local/bin/tlevince
#! /bin/bash
# tlevince -- set TEXMFCF to use the TeX Live 2008 texmf trees
export TEXMFCNF='{/usr/local/texlive/2008/bin,/usr/local/texlive/2008}{,{/share,}/texmf{-local,}/web2c}'
exec /usr/bin/evince "$@"

The portability problems for texlive binaries get much worse if you
want to include gui tools that don't use a cross-platform GUI environment, and people want to see versions that are consistent with the other tools they use.  It would be interesting to see if there are ways to tweak evince to support multiple distros.

---

