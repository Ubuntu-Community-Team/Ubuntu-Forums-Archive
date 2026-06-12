---
title: "Cannot Access /usr/local/bin"
date: 2008-07-27
forum: General Help
---

### Post by Samizdat on 2008-07-27
I run Ubuntu 8.04.  I've downloaded a package (fftexplorer) in the form of an .sh file, but cannot install because the /usr/local/bin directory, in which the author says to place the file, is inaccessible.  I cannot cut & paste, copy & paste, nor drag & drop the file where instructed, so I ask here before poring over a few hundred Linux man pages for a command line solution.

If Ubuntu requires me to use root to move the .sh file into /usr/local/bin, but root is not recommended, where does this leave me, a Windows orphan who's used Ubuntu for all of about a week?  How, in layman's terms, please, do I proceed?

---

### Post by braddcadd on 2008-07-27
> **Samizdat said:**
> If Ubuntu requires me to use root to move the .sh file into /usr/local/bin, but root is not recommended, where does this leave me

Put "sudo" in front of any command in the terminal.  This will execute a single command as the root user.

Your command should look something like this:
```

sudo cp file.sh /usr/local/bin/

```

If you are replacing a file there make sure you create a backup first:
```

sudo cp /usr/local/bin/file.sh /usr/local/bin/file.sh.old

```

---

### Post by Samizdat on 2008-07-27
Thanks for your help, braddcadd.

This thread may fast become hopelessly confused, but better to straighten course early if possible.  I was mistaken: fftexplorer's author states the file is binary.  However, the file has no extension.  The author's page may help straighten this out for those of you who know light-years more than I about translating generic Linux instructions to Ubuntu.

Therefore, I link the page (which you will note has both the source and binary download links): [http://www.arachnoid.com/FFTExplorer/]("http://www.arachnoid.com/FFTExplorer/")

Again, please bear in mind that I'm barely (pun) out the Ubuntu womb and would appreciate extremely simple install instructions.

---

### Post by dexter.deepak on 2008-07-27
@Samizdat
you can simply try the following steps for binary :
```
sudo cp you_file.sh /usr/local/bin/
sudo chmod a+x your_file.sh
```

check your PATH variable:
```
echo $PATH
```
if there is a line containing "/usr/local/bin" (which would be there by default), then you can issue this command from anywhere to run your_file.sh
```
your_file.sh
```

if /usr/local/bin is not in the PATH variable,you should first do:
```
PATH=$PATH:/usr/local/bin
```
and then try running your_file.sh as explained above.

---

### Post by caljohnsmith on 2008-07-27
Samizdat, the method that dexter.deepak gave will surely work, but an easier way might be to follow the directions on that website you gave a link to, since it comes with its own installer and will do all the work for you. First "cd" into the directory that has the fftexplorer.tar.bz2 file you downloaded and run the following:
```
tar -xjf fftexplorer.tar.bz2
cd fftexplorer.dist
sudo ./auto_install.sh
```

---

### Post by darren09 on 2010-04-26
Hi,
 
im trying to copy the execute file (wish.exe, hpnpf.exe, ioconfig.exe & iosend.exe)to /usr/local/bin but after copy the execution file to the above directory, execution file type will change to unknown...... so how to copy the execution file to the directory?
 
darren

---

