---
title: "libopenal.so.0 error message PLEASE HELP!!!"
date: 2008-11-13
forum: General Help
---

### Post by agentsmith23 on 2008-11-13
This has become a pretty annoying bug for me. I have been trying to install/run X-Plane 8 for the last week and nothing seems to work. I just constantly get this error:

```
./X-Plane Installer 123 DVD Linux: error while loading shared libraries: libopenal.so.0: cannot open shared object file: No such file or directory
```

From posts I have been reading ioquake3 seems to be having the same problem. Is this a problem that will need to be resolved by the software developers or by the OS developers (I know they are both software:p).

Or is there any way around this error message right now?

Thanks for any help!

---

### Post by agentsmith23 on 2008-11-14
Any suggestions? :confused:

---

### Post by technoryt on 2008-12-28
Hi,
if you are using Hardy or previous, make sure that you have the package libopenal0a installed. To check, use synaptic or run in a terminal 

sudo apt-get install libopenal0a

If you are using Intrepid, there is a known bug ([https://bugs.launchpad.net/ubuntu/+source/openal-soft/+bug/273558]("https://bugs.launchpad.net/ubuntu/+source/openal-soft/+bug/273558")) In this case a simple workaround is to make a symbolic link from the old to the new library. In a terminal, run

sudo ln -s /usr/lib/libopenal.so.1 /usr/lib/libopenal.so.0

I had the same problem with mplayer and this has fixed it.

---

### Post by quantum64 on 2009-06-14
For those of you who are using 9.04 64 bit edition, don't forget that you must do this for the 32bit libraries. The command: sudo ln -s /usr/lib/libopenal.so.1 /usr/lib/libopenal.so.0 will only update the 64bit libraries.

To fix this in your 64bit version type:
sudo ln -s /usr/lib32/libopenal.so.1 /usr/lib32/libopenal.so.0

After doing this I was able to run the X-Plane installer.

---

### Post by Shockwav on 2009-07-04
Confirmed fix! Thanks for the tip!!!

---

### Post by Fl0ris on 2009-07-12
I'm on an up-to-date Ubuntu Jaunty, while trying to run [this blender build]("http://www.graphicall.org/builds/builds/showbuild.php?action=show&id=1023") the same error as agentsmith23's one was reported.

which I fixed by running technoryt's command in the terminal:
(first make sure you have the libopenal1 installed)
sudo ln -s /usr/lib/libopenal.so.1 /usr/lib/libopenal.so.0

Thanks, technoryt :)

---

### Post by evensuol on 2010-01-08
Thank you quantum64 for 64bit fix

---

