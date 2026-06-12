---
title: "[SOLVED] I need to install something using &amp;quot;make &amp;amp;&amp;amp; make install&amp;quot; command. I dont kno"
date: 2008-12-30
forum: Installation &amp; Upgrades
---

### Post by hibajugalala on 2008-12-30
I need to install something using "make && make install" command, or atleast thats what it tells me to use, but i don't know how to use it!!!

Can someone please help me!! I'm new to ubuntu.

---

### Post by vambo on 2008-12-30
Looks as if you need to install the build-essential package to get make

In terminal
```
sudo aptitude install build-essential
```

or via synaptic package manager, which might be easier if your new.

I take it you're building an app?

---

### Post by oldos2er on 2008-12-30
What program are you trying to compile?

---

### Post by hibajugalala on 2008-12-30
K i wanna install atlantis on my computer.
I read the read me and it says to compile with the usual "make && make install" command.

---

### Post by vambo on 2008-12-30
Assuming you have make installed. Go the the directory where atlantis source is - probably the same one as the README is in - then in terminal

```
sudo make
```

Assuming that runs with no errors then

```
sudo make install
```

BTW - I have no idea what atlantis is

---

### Post by oldos2er on 2008-12-30
> **hibajugalala said:**
> K i wanna install atlantis on my computer.
I read the read me and it says to compile with the usual "make && make install" command.

 Got a URL for it?

---

### Post by stderr on 2008-12-30
Typically, the app may or may not provide a 'configure' script - if so, it's best to run that first

```
./configure
```

If you're missing anything required to build the app, the configure script will likely give you a hint towards what you're missing.

Following that, you'd run 'make'

```
make
```

I wouldn't normally use the root account for either configure or make, though.

Then it's the matter of 'make install', which will need root priviledges.

```
sudo make install
```

So, make actually compiles the source code, and make install puts the compiled files in the correct places, as I understand it.

---

### Post by hibajugalala on 2008-12-30
> **oldos2er said:**
> Got a URL for it?

for atlantis?

---

### Post by hibajugalala on 2008-12-30
k when im in the directory and do the make command it says:

Makefile:48: *** [ERROR] Compiz not installed.  Stop.

I have compiz istalled so...ye

and a link for atlantis...heres a video of some guy doing it:
[http://www.youtube.com/watch?v=pTRsLW0eet0&feature=channel](http://www.youtube.com/watch?v=pTRsLW0eet0&feature=channel)

and heres a link where i downloaded it from:
[http://gitweb.compiz-fusion.org/?p=fusion/plugins/atlantis;a=commit;h=7084e9dff32ac147edc5b912588cbc468795ba35](http://gitweb.compiz-fusion.org/?p=fusion/plugins/atlantis;a=commit;h=7084e9dff32ac147edc5b912588cbc468795ba35)

and i pressed snapshot to download it.

---

### Post by stderr on 2008-12-30
You may need the dev files too; try

```
sudo apt-get install compiz-dev
```

---

### Post by oldos2er on 2008-12-30
Which version of Ubuntu are you running; and have you installed build-essential?

---

### Post by hibajugalala on 2008-12-31
k I installed compiz-dev and now this pops up:
Makefile:144: *** [ERROR] BCOP not installed but is needed to build plugin.  Stop.

---

### Post by hibajugalala on 2008-12-31
> **oldos2er said:**
> Which version of Ubuntu are you running; and have you installed build-essential?

k i forgot about build-essentials and i have ubuntu 8.10.. im installing build-essential atm.

---

### Post by hibajugalala on 2008-12-31
k i finished installing build-essentials and the same error pops up

---

### Post by oldos2er on 2008-12-31
Look around for a README and/or INSTALL file; you need to find a list of dependencies. 

 "Makefile:144: *** [ERROR] BCOP not installed but is needed to build plugin.  Stop."

 This is referring to compiz-fusion-bcop.

---

### Post by donkyhotay on 2008-12-31
> **hibajugalala said:**
> k I installed compiz-dev and now this pops up:
Makefile:144: *** [ERROR] BCOP not installed but is needed to build plugin.  Stop.

You just need to install the plugin which is in the ubuntu repos. You can install it with a simple
```
sudo apt-get install compiz-fusion-bcop
```
Or from synaptic. Installing with make/install can be frustrating your first time or two. However once you get the hang of it it's not that bad. The biggest problem is with missing dependencies (which is what you're running into now) and generally it's a matter of running ./configure and installing dependencies from the repos until it doesn't give any errors. As mentioned previously you usually need the -dev version when compiling from source like this. Now it's when a dependency isn't in the repos that things get really ugly (and about where I give up and find something else) because then you sometimes have to compile the libraries along with all of *it's* dependencies... thats when I usually give up and find another program.

---

### Post by stderr on 2008-12-31
Basically, for every missing dependency, it's just a matter of searching through the repositories and installing it. In *almost all* cases they should be in the repositories...

You can use

```
apt-cache search PACKAGE
```

to search the repositories (well, the sources you have enabled & updated anyway) for a package with PACKAGE in its name. You don't need to be root for that command. Of course, another alternative is to use Synaptic's search feature. What I like about the apt-cache command (and the other apt- commands) is you can use regex in your searches. In its simplest form, you could append a wildcard (*) to the end of a search term... but of course, regexes are very powerful for searching.

Sometimes it's also helpful to use apt-file in determining if you've identified the correct package to install. This command gives you the ability to see which files are in each package, and to search for specific files.

You need to update the file list cache first with

```
sudo apt-file update
```

which may take a few minutes, then you can use

```
apt-file search FILE_NAME
```

to get a list of packages containing the file FILE_NAME, and

```
apt-file list PACKAGE_NAME
```

to list all files in package PACKAGE_NAME.

To see a list of files for a package you already have installed, you can (more simply) use dpkg's file list feature:

```
sudo dpkg -L PACKAGE_NAME
```

---

### Post by hibajugalala on 2009-01-01
THANK YOU ALL SO MUCH...it finally works.

I love you guys:D!!!

---

