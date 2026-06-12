---
title: "Installing programs"
date: 2008-10-23
forum: General Help
---

### Post by chrismorris730 on 2008-10-23
Hi, I'm fairly new to Kubuntu, after a friend of mine recommended it when I told him I wanted to start getting into Linux. I'm probably going to be asking a whole bunch of questions here pretty soon so get ready :D

Anyway, I found a driver for my G15 keyboard and it's in a format where I'm guessing I have to compile it myself? (tar.gz) because when I double click on it (like I have with a couple applications and like I would with Windows) it wants me to open it with Ark, which I know is like WinRar. I would like to install this driver as I would like to be able to use the LCD screen on my keyboard, but like I said I have no idea how to do it.

---

### Post by snova on 2008-10-23
Well, you should prefer using the repository to building drivers yourself, but I'll assume you already checked there...

If it's a tarball, there are two likely kinds of content:

[LIST]
    [*] Source code. You'll have to compile it according to the instructions that should accompany it. Compilation might not succeed, as kernel modules can be tricky to build correctly.
    [*] Binary drivers. Install however it says to, but it may not work if they are for the wrong kernel version.
[/LIST]

(I Googled it- it's neat looking. Don't know what I would do with it, though!)

---

### Post by chrismorris730 on 2008-10-23
The repository? Sorry I'm fairly new and I know I haven't done much of my own legwork up to this point...

---

### Post by zvacet on 2008-10-23
To find out more about repositories read [this]("https://help.ubuntu.com/community/Repositories/Kubuntu").

For package you want to install (if it isa not in repos) type in terminal

```
tar -zxvf packagename
```

**packagename** = name of package you want to uncompress

anfter that you will get folder with similar name as your package.Go in it with 

```
cd foldername
```

Usual procedure for compile file is to type

1.configure
2.make
3.sudo make install

But you can read install file in folder and see what steps you have to take to compile.

---

### Post by snova on 2008-10-23
You will be glad to know that I did a quick search for "g15" and found that there are several packages relating to your keyboard. You'll have to decide how useful they are.

A repository is just a place where packages are stored. When I said to look in the repos I meant to search for useful-looking packages in the package manager.

---

### Post by chrismorris730 on 2008-10-23
> **snova said:**
> 
A repository is just a place where packages are stored. 

I think I found something similar to what you're talking about, I did a search as well and found about 4 or 5 different things people had written to talk to the LCD and extra keys.

@zvacet:
I typed in tar -zxvf g15lcd-1.2.tar.gz and it told me that the package didn't exist, and then I typed it again without the .tar.gz and it again told me it didn't exist. What exactly would the package name be?

---

### Post by snova on 2008-10-23
Tar is an archiver. It deals with the Linux equivalents of Zip files, not packages. apt-get is the command you want, it installs/removes/upgrades/everything else packages.

What to install depends on what you're trying to do. I discovered a program earlier today (called KeyTouch) that deals with special keys, which might be useful if you're trying to make buttons like Internet (or whatever you have) run particular programs.

But the LCD is another matter. It requires more specific support from applications, and I don't think very many do. The only program I can find that would make the LCD do anything useful is Audacious (it's in the g15daemon-audacious package).

So what are you trying to do? I can't give a very specific answer until I know some more about your objective.

---

### Post by oldos2er on 2008-10-23
You really should read the link that zvacet posted. Use a package manager to install software; either Synaptic Package Manager, or Adept.

---

### Post by chrismorris730 on 2008-10-23
Well Adept came with my particular distro of Kubuntu, but I don't know how to make Adept install it...

I need to know how to get the .tar.gz file working. I couldn't make it extract the way zvacet told me to so I right clicked it and hit extract. Then I typed in the next set of code and it didn't work again.

Even if I go through all this and find that the g15lcd driver isn't the one I want, I still need to know how to deal with .tar.gz files

---

### Post by snova on 2008-10-23
You don't need to build it yourself. It's in the repository, just install it from there.

The .gz part means that it is Gzip compressed, and the .tar means that it is a Tar archive. Tar only handles archiving, and Gzip only handles compression- they make a nice pair. Fortunately Tar handles compressed archives transparently.

Basic usage:

```
tar <options> archive.tar [files...]
```

Options (all stuck together in any order):

[LIST]
    [*] z - Compress with Gzip.
    [*] j - Compress with Bzip2.
    [*] x - Extract.
    [*] t - List files inside the archive.
    [*] c - Create archive
    [*] f - Use file (almost always needed, because tar can handle other ways of accessing the archive, like tape drives and stdin).
    [*] v - Verbose. Use twice for more information.
[/LIST]

Extract:

```
tar xf archive.tar
```

Extract compressed archive:

```
tar zxf archive.tar
```

Create Bzip2 compressed archive:

```
tar jcf archive.tar <consituent files>
```

---

### Post by chrismorris730 on 2008-10-23
Maybe I'm not explaining myself very well...

Even though the file I want to play with is sitting right there on the desktop, I can't seem to get the console to recognize it.

```

chris@chris-desktop:~$ tar xf g15lcd-1.2.tar.gz
tar: g15lcd-1.2.tar.gz: Cannot open: No such file or directory
```

It's sitting on my desktop!

```

tar: Error is not recoverable: exiting now
chris@chris-desktop:~$ 
```

This is very frustrating...I don't know why I can't understand it

---

### Post by snova on 2008-10-23
Because you aren't in your desktop. Type "cd Desktop", then try again. And don't forget the 'z' option to tar, or it won't do automatic decompression (and fail as a result).

In the command line you are always "in" a directory. Commands are executed relative to that directory. The "cd" command (short for Change Directory) moves around. Alternatively you could try "tar zxf Desktop/g15lcd-1.2.tar.gz", but then it would extract the files to your home directory instead of to your desktop.

I really must stress that this program you are trying to install from source is present in the repository and can thusly be installed with much less hassle from the package manager. Their home page leads me to believe the programs are resident in the "g15daemon" package.

I should also mention that there's probably not much you're going to be able to do with it anyway. Then again...

---

### Post by chrismorris730 on 2008-10-23
The main purpose of installing it was to use the resource monitor. It was a handy thing to be able to switch to when in Windows without bringing up task manager. I guess there's really not a purpose to have it.

I'm not sure how much I'll actually be using Linux as it is. I'm getting into programming in school and have taken 2 1/2 years of computer science courses and I figured Linux was something I should at least try. However, I like to play games and these two interests conflict in Linux :D

Thanks for your patience, by the way.

EDIT: Using cd Desktop and then the zxf g15lcd-1.2.tar.gz command I got it to extract the folder. I then cd'ed to the folder to start doing what zvacet was telling me to do and I've run into a problem. How do I use make? The readme in the file itself said "just use a make." I typed make --help and of course it gave me the help but I'm not sure how to use it

---

### Post by chrismorris730 on 2008-10-23
WOW using the repositories was WAY easier than this. However, even though I have my g15daemon installed now, I'm not exactly satisfied. 

Reasons:

It didn't have the one part I wanted, I guess I'll have to make it myself...at some point...

I still didn't exactly master anything.

---

### Post by zvacet on 2008-10-24
@ **chrismorris730**

Sorry for forget to say that you need **build-essential** package if you want to compile.Install in from synaptic.If you allready done that you should just type **make** after configure is done.Last step is sudo make install.

---

### Post by snova on 2008-10-24
make is a program for automating builds. When something changes, it automatically detects what needs to be rebuilt.

configure is a script that generates the files that make needs to run- after it runs some checks on your system.

"make" will build whatever the default is, which is usually everything. "make install" will install everything. It needs to be run with sudo when installing things to system directories (the default is /usr/local).

---

