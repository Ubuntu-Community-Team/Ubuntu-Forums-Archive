---
title: "How can I have a built-from-source app recognised as a package dependency?"
date: 2009-02-15
forum: Installation &amp; Upgrades
---

### Post by the_uncle on 2009-02-15
I needed to build from source the latest release of ffmpeg, in order to have all the features I wanted. (And I successfully done it).
However now I'd like to install a package that requires ffmpeg as a dependency, but apt force me to install the ubuntu-repository version of ffmpeg because it can't detect the installed version.

Is there a way to set a built-from-source program as a satisfied dependency for a .deb package?

---

### Post by the_uncle on 2009-02-15
I'm adding some console output to give more information:

```
###@###:~$ ffmpeg -version
FFmpeg version SVN-r16086, Copyright (c) 2000-2008 Fabrice Bellard, et al.
  configuration: --prefix=/usr --enable [...]

###@###:~$ apt-cache policy ffmpeg
ffmpeg:
  Installed: (none)
  Candidate: 3:0.svn20080206-12ubuntu3
  Version table:
     3:0.svn20080206-12ubuntu3 0
        500 http://it.archive.ubuntu.com intrepid/main Packages
        100 /var/lib/dpkg/status

```


EDIT: I found a way to have both versions of ffmpeg (the one in the repositories and the one from the source code) together.
I built the source setting the installation path as a user directory (i.e. /home/foo/programs) and launched "make install" *without* root priviliges. In this way every resource is owned and available for a single user.
```
###@###:~/sources/ffmpeg$ ./configure --prefix=/home/foo/progs/ffmpeg && make && make install
```
Then I renamed the ffmpeg binary, (necessary to avoid conflicts) and added the path to the user's $PATH variable
```
###@###:~$ mv ~/progs/ffmpeg/bin/ffmpeg ~/progs/ffmpeg/bin/ffmpeg.svn
###@###:~$ echo PATH=$PATH:$HOME/progs/ffmpeg/bin >> .bashrc

```
After that I could install ffmpeg through apt without any problem, in order to have it as a dependency.

I still would like to know if there's a way to let apt detect the source-built program as a satisfied dependency, because sometimes I need those programs installed system-wide

---

