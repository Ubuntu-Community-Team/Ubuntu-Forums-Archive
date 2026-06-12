---
title: "Installing Truecrypt with new Kernel?"
date: 2005-11-29
forum: General Help
---

### Post by carlos1 on 2005-11-29
I updated Kubuntu from the default Kernel to 2.6.12-10-386. 
THen when I went to install the ubuntu package for Truecrypt, it wouldn't install, and in the Readme it states to use the package I need the defult kernel (which I changed).
When I tried to isntall it from source, and use an install script that comes with it, it asked for the source directory of the 2.6.12-10 kernel.
This may sound stupid but how do I find the kernel source directory?

---

### Post by carlos1 on 2005-12-01
Bump... please someone help me find my kernel!

---

### Post by koni-ubuntu on 2005-12-14
Hi,

I "created" a package for the kernel 2.6.12-10-686.

pick it up from [http://rose.dis.unibz.it/~kohofer/linux/](http://rose.dis.unibz.it/~kohofer/linux/)

cheers, konrad

PS: Try to write a small howto what I did.

---

### Post by koni-ubuntu on 2005-12-14
Ok, quickly put together a few lines:

[http://rose.dis.unibz.it/~kohofer/linux/update-package-truecrypt.txt](http://rose.dis.unibz.it/~kohofer/linux/update-package-truecrypt.txt)

cheers, konrad

---

### Post by Franko30 on 2005-12-14
Thanks Konrad!

Any chance of this going to a 'howto'?

:-)

---

### Post by koni-ubuntu on 2005-12-22
Sorry, but it doesn't work, I get:

FATAL: Error inserting truecrypt (/lib/modules/2.6.12-10-686/extra/truecrypt.ko): Invalid module format
truecrypt: Failed to load TrueCrypt kernel module

regards, konrad

---

### Post by pjman on 2005-12-22
[QUOTE=koni-ubuntu]Sorry, but it doesn't work, I get:

FATAL: Error inserting truecrypt (/lib/modules/2.6.12-10-686/extra/truecrypt.ko): Invalid module format
truecrypt: Failed to load TrueCrypt kernel module

regards, konrad[/QUOTE]

I get the same error message.

Does anyone know how to compile it? I get another error for that, something about dm.h not being found...

```

user@home:~/downloads/truecrypt-4.1-source-code/Linux$ uname -r
2.6.12-10-68
user@home:~/downloads/truecrypt-4.1-source-code/Linux$ ls -l
total 20
-rwxr--r--  1 travis travis 1992 2005-11-23 15:59 build.sh
drwx------  3 travis travis 4096 2005-11-25 16:54 Cli
drwx------  2 travis travis 4096 2005-11-25 16:54 Common
-rwxr--r--  1 travis travis 2827 2005-11-20 07:50 install.sh
drwx------  3 travis travis 4096 2005-11-25 16:54 Kernel
user@home:~/downloads/truecrypt-4.1-source-code/Linux$ sudo ./build.sh
Checking build requirements...
Error: Kernel source code is incomplete - header file dm.h not found.
user@home:~/downloads/truecrypt-4.1-source-code/Linux$

```

Thanks,
pjman

---

### Post by X_FISH on 2005-12-27
I've tried the following steps (already had installed kernel headers):
_____

sudo apt-get install linux-source-2.6.12 

cd /usr/src/

sudo tar xvjf linux-source-2.6.12.tar.bz2

sudo make -C /usr/src/linux-source-2.6.12 config modules
*or errormessage will appear running truecrypt ./install.sh*
_____

cd /truecrypt-4.1-source-code/Linux

chmod 755 install.sh
chmod 755 build.sh

sudo ./install.sh

[COLOR="Red"]Linux kernel (2.6.12-10-686) source directory [/usr/src/linux]:[/COLOR] /usr/src/linux-source-2.6.12
*red means &#187;asked by script&#171;*

Output:

```
[COLOR="Blue"]sudo ./install.sh[/color]
Checking installation requirements...
Checking build requirements...
Linux kernel (2.6.12-10-686) source directory [/usr/src/linux]: /usr/src/linux-source-2.6.12
Error: Kernel not configured. You should run make -C /usr/src/linux-source-2.6.12 config modules
Error: Build failed - installation aborted
turanga@amy:/home/data/essentials/privacy/truecrypt-4.1-source-code/Linux$ sudo ./install.sh
Checking installation requirements...
Checking build requirements...
Linux kernel (2.6.12-10-686) source directory [/usr/src/linux]: [COLOR="Blue"]/usr/src/linux-source-2.6.12[/COLOR]
Building kernel module... Done.
Building truecrypt... Done.
Testing truecrypt... Done.

Install binaries to [/usr/local/bin]:
Install man page to [/usr/local/man]:
Allow non-admin users to run TrueCrypt [y/N]: [COLOR="Blue"]y[/COLOR]
Installing kernel module... Done.
Installing truecrypt to /usr/local/bin... Done.
Installing truecrypt man page to /usr/local/man/man1... Done.

```

*blue means &#187;typed by hand&#171;*

Regards, Martin

---

### Post by pjman on 2005-12-27
Thanks Martin,

When I do "sudo apt-get install linux-source-2.6.12" I do not get a linux-source-2.6.12.tar.bz2 file in /usr/src/. 


Here is my /usr/src directory:

```

user@home:/usr/src$ ls -l
total 8
lrwxrwxrwx   1 root src    37 2005-12-22 14:19 linux -> /usr/src/linux-headers-2.6.12-10-686/
drwxr-xr-x  18 root root 4096 2005-12-22 14:11 linux-headers-2.6.12-10
drwxr-xr-x   5 root root 4096 2005-12-27 15:33 linux-headers-2.6.12-10-686
travis@monkey:/usr/src$

```

Any other ideas?

Thanks

---

### Post by X_FISH on 2005-12-27
What kind of message is displayed when you tried to install the source? Any error messages?

Regards, Martin

---

### Post by pjman on 2005-12-27
It said it was already installed....

---

### Post by X_FISH on 2005-12-28
Hm... Try

find / -name linux-source-2.6.*

Something found?

Regards, Martin

---

### Post by pjman on 2005-12-28
Here is what I get.

Any other ideas?

Thanks

```

user@home:~$ sudo find / -name linux-source-2.6.*
Password:
/var/lib/dpkg/info/linux-source-2.6.12.postinst
/var/lib/dpkg/info/linux-source-2.6.12.list
/var/cache/apt/archives/linux-source-2.6.12_2.6.12-10.24_all.deb
/var/cache/apt/archives/linux-source-2.6.12_2.6.12-10.25_all.deb
/usr/share/doc/linux-source-2.6.12
find: WARNING: Hard link count is wrong for /proc: this may be a bug in your filesystem driver.  Automatically turning on find's -noleaf option.  Earlier results may have failed to include directories that should have been searched.
user@home:~$

```

---

### Post by X_FISH on 2005-12-28
linux-source-2.6.12_2.6.12-10.25_all.deb

<= try to install with dpkg -i /var/cache/apt/archives/linux-source-2.6.12_2.6.12-10.25_all.deb

The same package is what I have downloaded via apt... 

Regards, Martin

---

### Post by pjman on 2005-12-29
That worked. Thank you!

---

### Post by jackwhite on 2006-01-21
Hi Martin,

When I try to follow your steps I get s far as "sudo make -C /usr/src/linux-source-2.6.12 config modules".

When I enter that command the result I get is:

```
padraic@ubuntu:/usr/src$ sudo make -C /usr/src/linux-source-2.6.12 config modules
make: Entering directory `/usr/src/linux-source-2.6.12'
Makefile:485: .config: No such file or directory
/usr/src/linux-source-2.6.12/scripts/gcc-version.sh: line 11: gcc-3.4: command not found
/usr/src/linux-source-2.6.12/scripts/gcc-version.sh: line 12: gcc-3.4: command not found
make[1]: gcc-3.4: Command not found
make[1]: Nothing to be done for `Makefile'.
/usr/src/linux-source-2.6.12/scripts/gcc-version.sh: line 11: gcc-3.4: command not found
/usr/src/linux-source-2.6.12/scripts/gcc-version.sh: line 12: gcc-3.4: command not found
  HOSTCC  scripts/basic/fixdep
/bin/sh: gcc-3.4: command not found
make[2]: *** [scripts/basic/fixdep] Error 127
make[1]: *** [scripts_basic] Error 2
make: *** [config] Error 2
make: Leaving directory `/usr/src/linux-source-2.6.12'
```

I've no idea why this happens or what it means. Please help!

---

### Post by jackwhite on 2006-01-22
... and then I realised that it meant I had to install some software such as gcc etc etc.
 So I got that sorted and moved on a couple of more steps. However (I guess there had to be a however!) I ran into another problem.

When I enter this line:```
padraic@ubuntu:/media/usbdisk-1/jimmy/Linux$ sudo ./install.sh
```
The response I get is ```

sudo: unable to execute ./install.sh: Permission denied
```

AS you can see I changed the name of the folder (to jimmy - don't ask!) and i placed it on an external drive. But those shouldn't affect anything should they?

---

### Post by pjman on 2006-01-23
[QUOTE=jackwhite]... and then I realised that it meant I had to install some software such as gcc etc etc.
 So I got that sorted and moved on a couple of more steps. However (I guess there had to be a however!) I ran into another problem.

When I enter this line:```
padraic@ubuntu:/media/usbdisk-1/jimmy/Linux$ sudo ./install.sh
```
The response I get is ```

sudo: unable to execute ./install.sh: Permission denied
```

AS you can see I changed the name of the folder (to jimmy - don't ask!) and i placed it on an external drive. But those shouldn't affect anything should they?[/QUOTE]

Did you do these commands?

```
chmod 755 install.sh
chmod 755 build.sh
```

If it still doesn't work can you post the output of "ls -l" while in the Linux directory?

---

### Post by jackwhite on 2006-01-23
Hi.

Well i went back today and tried again, this time I redonloaded the truecrypt source code. 
I completeed all the steps and true crypt seemed to install ok. however when I finished and tried to mount my truecrypt volume this is the response i got:

```
Enter password for '/media/shared/badsanta.iso':
FATAL: Error inserting truecrypt (/lib/modules/2.6.12-10-386/extra/truecrypt.ko): Invalid module format
truecrypt: Failed to load TrueCrypt kernel module
padraic@ubuntu:~/Desktop/truecrypt-4.1-source-code/Linux$

```

At this stage i've gone through all the steps, many of them more than once so i think retracing my steps is probably pointless at this stage. What I'd like to do is uninstall truecrypt completely and start again. Is that possible at this stage? (I've had a look at this* thread but I'm not sure where the main tree or source directories are).

*[http://www.ubuntuforums.org/showthread.php?t=120477&highlight=uninstalling](http://www.ubuntuforums.org/showthread.php?t=120477&highlight=uninstalling)

---

### Post by foof on 2006-02-03
Hi!

I have reinstalled my system and now I can't install truecrypt any more?
I have followed X_FISH instructions.

But when I run sudo ./install.sh I get this:

root@htpc:/usr/src/truecrypt-4.1-source-code/Linux# sudo ./install.sh
Checking installation requirements...
Checking build requirements...
Error: Kernel source code is incomplete - header file dm.h not found.
Error: Build failed - installation aborted
root@htpc:/usr/src/truecrypt-4.1-source-code/Linux#

By the way, when I run:
sudo make -C /usr/src/linux-source-2.6.12 config modules

I get about 1000 questions, I just hold down enter to get the default for every question, is this the correct way of doing it?

Can someone help?

---

### Post by foof on 2006-02-03
I got it working, not sure but I think it did help to install the package:
linux-tree-2.6.12

Before trying to install Truecrypt again I also did upgrade the Linux Kernel following this guide:
[http://www.ubuntuforums.org/showthread.php?t=84174&highlight=howto+kernel](http://www.ubuntuforums.org/showthread.php?t=84174&highlight=howto+kernel)

After this I tried installing TC again and now it did work!

One thing I noticed after the Kernel upgrade was a failure at boot:
Mounting local filesystem failed I think!? Didn't got much time to read it, is there a way of seeing what failed at boot after booting? Everything seems to work though.

---

### Post by foof on 2006-02-07
No it wasn't the linux-tree-2.6.12 that did it. I have restored my system to 2.6.12 again and now I have the same problem again. I got other problems with the new kernel. Can someone help me install truecrypt on this kernel or I'll have to try upgrade my kernel again.

---

### Post by X_FISH on 2006-02-11
> Error: Kernel source code is incomplete - header file dm.h not found.
Error: Build failed - installation aborted

Try 

sudo apt-get install linux-kernel-headers

They have been installed on my system already, so I forgot to mention it.
_____

> make[1]: gcc-3.4: Command not found

gcc-4.0 is installed by default. So

sudo apt-get install gcc-3.4

Then open a console and type

export CC=gcc-3.4

then restart the process in this console - using gcc-3.4.

Regards,

Martin

---

### Post by Cannedbread on 2006-03-11
im getting an error inserting kernel module thing after installing the modified package. Anyone know what to do about that?

---

