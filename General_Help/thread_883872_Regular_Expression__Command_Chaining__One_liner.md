---
title: "Regular Expression / Command Chaining / One liner"
date: 2008-08-08
forum: General Help
---

### Post by rahmath on 2008-08-08
I need to check, whether few packages are installed in the system or not. There are around 35 package names which is there in a text files called "check-pkgs". All the package names are mentioned in line by line.

How can i use a simple online command, to check whether these mentioned packages are installed in my system.

i tried the following, but didnt worked. 

$ dpkg -l | grep `cat check-pkgs`

according to my idea, this command should work!!! but its not working for me, So, can u plz explain to me why this is not working in this situation.


Thanks in advance...

NOTE: I had posted around 5 - 7 times, asking different questions, but i didnt received any answers for it. Hope this time, i will have one from you...

KMR

---

### Post by sdennie on 2008-08-08
Try:

```

dpkg -l | grep -f check-pkgs

```

---

### Post by ByteJuggler on 2008-08-08
try

```
dpkg -l | grep -f check-pkgs
```

---

### Post by rahmath on 2008-08-08
Thanks for your replies, 


And this command is working fine. But now i have one more doubt... from the output, i cant understand which are all the packages is actually installed and which are not...

this is the output when i run individually;

```
kmr@system5:~$ dpkg -l | grep libxv1
kmr@system5:~$ dpkg -l | grep libxss1
kmr@system5:~$ dpkg -l | grep libxext6
kmr@system5:~$ dpkg -l | grep libx11-6
kmr@system5:~$ dpkg -l | grep libstdc++6
ii  libstdc++6                                 4.2.3-2ubuntu7              The GNU Standard C++ Library v3
ii  libstdc++6-4.2-dev                         4.2.3-2ubuntu7              The GNU Standard C++ Library v3 (development
kmr@system5:~$ dpkg -l | grep libqt4-gui
kmr@system5:~$ dpkg -l | grep libqt4-core
kmr@system5:~$ dpkg -l | grep libgcc1
ii  libgcc1                                    1:4.2.3-2ubuntu7            GCC support library
kmr@system5:~$ dpkg -l | grep libc6
ii  libc6                                      2.7-10ubuntu3               GNU C Library: Shared libraries
ii  libc6-dev                                  2.7-10ubuntu3               GNU C Library: Development Libraries and Hea
ii  libc6-i686                                 2.7-10ubuntu3               GNU C Library: Shared libraries [i686 optimi
kmr@system5:~$ dpkg -l | grep libasound2

```

see this, from this i cant understand, which one among the files are installed. is there any tricky way to find out... i guess we need a script itself. if so, can anybody point to a script.

```

kmr@system5:~$ dpkg -l | grep -f check-depends 
ii  libc6                                      2.7-10ubuntu3               GNU C Library: Shared libraries
ii  libc6-dev                                  2.7-10ubuntu3               GNU C Library: Development Libraries and Hea
ii  libc6-i686                                 2.7-10ubuntu3               GNU C Library: Shared libraries [i686 optimi
ii  libgcc1                                    1:4.2.3-2ubuntu7            GCC support library
ii  libstdc++6                                 4.2.3-2ubuntu7              The GNU Standard C++ Library v3
ii  libstdc++6-4.2-dev                         4.2.3-2ubuntu7              The GNU Standard C++ Library v3 (development
kmr@system5:~$ cat check-depends 
libasound2
libc6
libgcc1
libqt4-core
libqt4-gui
libstdc++6
libx11-6
libxext6
libxss1
libxv1

```


NOTE: i didnt get an answer why my command dpkg -l | grep `cat check-depends` didnt worked like this grep -f.

Thanks for ur help...

---

### Post by damoxc on 2008-08-08
if the line starts with "ii" that means the package is installed.

I would guess that the way you put your command meant it was searched for the string output by cat, which inevitably won't exist if you've put more than one package in the file. Just guessing though.

---

### Post by rahmath on 2008-08-08
damo, thx for ur reply.

I know "ii" means it is installed. the problem here is, i cant understand, which among the packages in my check-depend files are installed and which are not installed.

Is there any way to know that... like

Package 1 - installed
Package 2 - installed
Package 3 - not installed
and so on... based on the no of lines in the check-depends file,.

---

### Post by mannheim on 2008-08-08
Scripts based on grep in this way may run into false positives, if you aren't careful. For example, you will get a false positive for an entry "foo-bar" in check-pkgs if your system has a package called "foo-bar-bazz" installed.

---

### Post by rahmath on 2008-08-09
any idea???

---

### Post by ByteJuggler on 2008-08-09
> **rahmath said:**
> 
NOTE: i didnt get an answer why my command dpkg -l | grep `cat check-depends` didnt worked like this grep -f.


Because it's simply wrong.  `cat check-depends` will put all the lines in "check-depends" onto the command line.  However, the syntax for grep doesn't allow you to pass multiple strings to search for on the command line like that.  You have to pass a single regular expression that will match them, e.g. probably using | symbol, or you have to use "-f <filename>". Read the "man" page.

---

### Post by mannheim on 2008-08-10
Something like
```
apt-cache  policy `cat check-pkgs` | grep -B1 Installed

```
should give you output like
```
tomboy:
  Installed: 0.11.1-0ubuntu1
--
nautilus:
  Installed: 1:2.22.3-0ubuntu2
--
aap-doc:
  Installed: (none)

```

---

### Post by rahmath on 2008-08-10
Really GREAT advice!!! Big Thanks....

now, can u just tell me one more thing... this is the test which i had...

```
kmr@KMRLapBEM:~/test$ apt-cache  policy `cat test` | grep -B1 Installed
skype:
  Installed: 2.0.0.72-1
--
gpm:
  Installed: 1.19.6-25ubuntu1
--
frozen-bubble:
  Installed: 2.1.0-2ubuntu2
--
deluge-torrent:
  Installed: 0.9.05-1
--
transmission:
  Installed: (none)
W: Unable to locate package kmr
kmr@KMRLapBEM:~/test$ cat test 
skype
gpm
frozen-bubble
deluge-torrent
transmission
kmr
kmr@KMRLapBEM:~/test$ dpkg -l | grep transmission
ii  transmission-common                        1.06-0ubuntu6                                              free, lightweight BitTorrent client
ii  transmission-gtk                           1.06-0ubuntu6                                              free, lightweight BitTorrent client (graphic
kmr@KMRLapBEM:~/test$ 

```


In this, transmission is having multiple out actually, but while we executed the apt-cache command it shows ;
```
transmission:
  Installed: (none)

```

why it is like that, and what we need to do, to get the output like; 
```
skype:
  Installed: 2.0.0.72-1
--
gpm:
  Installed: 1.19.6-25ubuntu1
--
frozen-bubble:
  Installed: 2.1.0-2ubuntu2
--
deluge-torrent:
  Installed: 0.9.05-1
--
[COLOR="Navy"]transmission:
  Installed: transmission-common
  Installed: transmission-gtk[/COLOR]
```


Hope that u will come back with an exact solution....

anyway for this itself... let me thank-you, and this is my first thanks in this group...

---

