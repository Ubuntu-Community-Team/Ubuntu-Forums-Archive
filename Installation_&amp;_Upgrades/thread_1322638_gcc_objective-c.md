---
title: "gcc objective-c"
date: 2009-11-11
forum: Installation &amp; Upgrades
---

### Post by ducky101 on 2009-11-11
Hi, 
I downloaded the gcc objc libraries and the cc1obj (objective-c compiler).
My question is, how can I make gcc use the compiler, when it is located in my homedir. I now I can link against external libraries, but is it possible to use a an external compiler.

The reason for asking this, is that I want to try objective-c on my schools server, and the gcc objective-c compiler is not installed.

The whole process to add a supported gcc language to the schools system could take aprox. up to 2 months. The sys admin told me to work as much as possible from my home dir and modify my .bashrc to add the appropriate libs etc. Basically according to him, no one cares what you do in your home directory :icon_frown:

Anyway, I am not sure how to go about this.

Could someone help me.

Thanks

---

### Post by pullmoll on 2009-11-11
The pre-built packages most probably won't help you in your case, because they are intended to be installed in /usr/bin, /usr/lib etc.

Did you try setting **GCC_EXEC_PREFIX** to the path where you put the package?
```
export GCC_EXEC_PREFIX=/home/yourname/somedir
```

Otherwise I think you would have to build the package (cc1obj and libobjc.so.x.y.z) from source, and there *./configure --prefix=$(HOME)*. On the other hand building gcc + gobjc from source is nothing for the faint at heart. It **may** work out of the box, while I had several times where it gave me a serious headache.

Let's assume it works, then do the following: Install packages **wget**, **mpfr** and **gmp**, if you don't have them. Now open a terminal window an do:
```

Get a tar ball with a recent GCC version, e.g. 4.4.2 (60MB):

~$ wget http://gcc.cybermirror.org/releases/gcc-4.4.2/gcc-4.4.2.tar.bz2

Now extract the tarball (takes some time, be patient)

~$ tar xjf gcc-4.4.2.tar.bz2

Create a build directory where to build the beast:

~$ mkdir build
~$ cd build

Configure with a prefix of $(HOME)

~/build$ ../gcc-2.4.2/configure --prefix=$(HOME)

And compile (take a walk outside or a coffee break)

~/build$ make

When all went well, now install the files

~/build$ make install

```I have to check if gobjc is in the default build, or how you can reduce the build time by selecting only C and ObjC as languages.

Anyway, after installing you should find the GCC binaries in your ~/bin directory and the libs in ~/lib (where ~ is your home directory).

Edit: I just tried the steps on a Slackware64 13.0 and it fails to link a file at some point... no good sign :-/

HTH
pullmoll

---

### Post by ducky101 on 2009-11-11
Thanks for the reply,
I tried to compile gcc, but no joy. The build is to large for my homedir. The home directories are capped at 80MB :sad:

I tried a precompiled binary with objc enabled, and the libraries and cc1obj compiler.

But I get the following error ```
gcc: error trying to exec 'cc1obj': execvp: Permission denied
```

Anyway I think I'll just make an request for the school to add objc.

Thanks for the help though and for testing it on your system.

Ducky

---

