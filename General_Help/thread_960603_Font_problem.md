---
title: "Font problem"
date: 2008-10-27
forum: General Help
---

### Post by BenTheMan on 2008-10-27
Hello all---

I am running "Wubi", which is sort of a cop out to dual booting my laptop.  I don't know if there are any other important details.

Long story short, I'm trying to run Mathematica remotely (I'm currently in California, and my office is in Ohio).  I can ssh -Y into the remote machine, and type the command to run mathematica.

I then get several errors:

xset:  bad font path element (#101), possible causes are:
    Directory does not exist or has wrong permissions
    Directory missing fonts.dir
    Incorrect font server address or syntax

If you are thinking that this sounds like a mathematica problem, it is :)  So I went to Wolfram, and they gave me the following advice: download the correct fonts and put them in 

/usr/lib/X11/fonts

(Wolfram help page here: [http://support.wolfram.com/mathematica/systems/unix/general/fonterrors.html](http://support.wolfram.com/mathematica/systems/unix/general/fonterrors.html))

The problem is, this directory doesn't exist!  Rats!

So I tried to CREATE the directory, but I get a "Permission denied" error.

So the directory doesn't exist, and I can't create it.  And just willing the thing into existence has not proved fruitful...yet.

What do I do next?  Is it impossible to make this whole thing work?

Thanks in advance!
Ben D

---

### Post by dracayr on 2008-10-27
use ```
gksudo nautilus
```

dracayr

---

### Post by Zer0d on 2008-10-27
I'm not sure if this will make anything work better but you could try it out hehe
When you tried creating that directory did you login to root account by typing **sudo -s** and writing your password?
You could run the commands as I list here:
[B]
sudo -s
mkdir /usr/lib/X11/fonts
chmod 666 /usr/lib/X11/fonts
cd /usr/lib/X11/fonts
wget [http://support.wolfram.com/mathematica/systems/linux/general/files/Math_6_Linux.tar.gz](http://support.wolfram.com/mathematica/systems/linux/general/files/Math_6_Linux.tar.gz)
tar -zxvf Math_6_Linux.tar.gz
chmod 666 Fonts
fc-cache -f -v /usr/lib/X11/fonts
[/B]

---

### Post by BenTheMan on 2008-10-27
Thanks a ton!

---

### Post by dracayr on 2008-10-27
if you try to copy+paste Zer0d's code, note there's a typo in line 4: it shoul say lib, not liv

dracayr

---

### Post by BenTheMan on 2008-11-04
For posterity's sake, and to ensure that no one has to struggle as much as I have, here's what finally worked:

Mathematica suggests three different fixes at the website I linked to above.  The one that finally worked was the second one:

You can alternatively create an exact same directory structure on your local computer and place the fonts there. Even if you do not have Mathematica installed locally, they will be found and used. Here, $InstallationDirectory is the path to the directory where Mathematica is installed on the remote computer (for Mathematica version 4.2 and prior, use $TopDirectory). The default directory is:

The directory structure can be created by running the following commands:

```
    mkdir -p ${InstallationDirectory}/SystemFiles/

    scp -r user@remotemachine:${InstallationDirectory}/SystemFiles/Fonts/

    ${InstallationDirectory}/SystemFiles/
```

in the SystemFiles directory, I did 

```
wget http://support.wolfram.com/mathematica/systems/linux/general/files/Math_6_Linux.tar.gz

tar -zxvf Math_6_Linux.tar.gz
```

---

### Post by Quicksilver_Johny on 2008-11-21
> **BenTheMan said:**
> For posterity's sake, and to ensure that no one has to struggle as much as I have, here's what finally worked:

Mathematica suggests three different fixes at the website I linked to above.  The one that finally worked was the second one:

You can alternatively create an exact same directory structure on your local computer and place the fonts there. Even if you do not have Mathematica installed locally, they will be found and used. Here, $InstallationDirectory is the path to the directory where Mathematica is installed on the remote computer (for Mathematica version 4.2 and prior, use $TopDirectory). The default directory is:

The directory structure can be created by running the following commands:

```
    mkdir -p ${InstallationDirectory}/SystemFiles/

    scp -r user@remotemachine:${InstallationDirectory}/SystemFiles/Fonts/

    ${InstallationDirectory}/SystemFiles/
```

in the SystemFiles directory, I did 

```
wget http://support.wolfram.com/mathematica/systems/linux/general/files/Math_6_Linux.tar.gz

tar -zxvf Math_6_Linux.tar.gz
```

[http://support.wolfram.com/mathematica/systems/linux/general/files/Math_6_Linux.tar.gz](http://support.wolfram.com/mathematica/systems/linux/general/files/Math_6_Linux.tar.gz) is now down. You don't by any chance still have the file?

---

