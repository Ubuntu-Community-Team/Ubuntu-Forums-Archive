---
title: "Scanner Clone Xerox 2400"
date: 2010-12-09
forum: Hardware
---

### Post by DenisP on 2010-12-09
[SIZE=4]Hi all,

I have an oldish scanner, Xerrox 2400, which I have never been able to get working on Ubuntu, not recognised by Xsane. I came across an article on this community

  [https://help.ubuntu.com/community/CheckIfScannerIsClone](https://help.ubuntu.com/community/CheckIfScannerIsClone)

which used this scanner as an example of how to get a none listed scanner to work using supported scanner which are identical under the skin. Mine is a clone of a listed one.

This involved downloading files using the terminal and editing said files.....as follows
[/SIZE][I][FONT=Arial][SIZE=4]sudo apt-get install libusb-dev build-essential libsane-dev
sudo apt-get install git-core
git clone git://git.debian.org/sane/sane-backends.git[/SIZE][/FONT][/I]

[SIZE=4][FONT=Verdana]All went well until the last line when an error was reported   [I]error connection timed out.

[/I]My problem is that I don't understand what **git clone git://etc.** is doing.
Can anyone enlighten me on this and suggest a way forward.

If you check out the tutorial you will see this is only the start of the editing but I am stuck.

Regards

Denis


[/FONT][/SIZE]

---

### Post by IcarusR on 2010-12-09
[*_git web page_*]("http://git-scm.com/") 

Git enables one to download a clone of the latest version of a software project & keep it up to date, usually the unstable not yet released version.

So basicly git is trying to download the latest version of 'sane-backends' source code, which works for me.
You could download tarball from sane web site & use that. 
Or keep trying with git.

---

### Post by desertdog on 2011-06-14
Support for this scanner was recently added. Try compiling from source.

[https://help.ubuntu.com/community/CompileSaneFromSource](https://help.ubuntu.com/community/CompileSaneFromSource)

---

