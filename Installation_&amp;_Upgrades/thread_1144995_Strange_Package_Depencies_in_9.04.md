---
title: "Strange Package Depencies in 9.04"
date: 2009-05-01
forum: Installation &amp; Upgrades
---

### Post by Frozsyn on 2009-05-01
Hello everybody!

I have just installed Ubuntu 9.04 (a.k.a Jaunty Jackalope) and have some remarks about the package dependencies. My installation is classic: from the Desktop 386 CD-ROM, with internet enabled during the installation, english language, and updating of the packages directly after the installation.

At this point, I have rebooted my computer just to enjoy the fast boot, the difference being significant on my laptop (Thinkpad X31). And then I have done my traditional package dependencies arrangement.

My first question is: can I mark as "automatically installed" all installed packages that are required or recommended by other installed packages ?

```
$ sudo aptitude markauto '~i(~Rdepends:~i|~Rrecommends:~i)'
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
The following packages will be REMOVED:
  gnome-user-guide-en{u} language-pack-en{u} language-pack-en-base{u} 
  language-pack-gnome-en{u} language-pack-gnome-en-base{u} 
  language-support-en{u} language-support-writing-en{u} 
  openoffice.org-hyphenation{u} openoffice.org-hyphenation-en-us{u} 
  openoffice.org-thesaurus-en-au{u} openoffice.org-thesaurus-en-us{u} 
  wamerican{u} wbritish{u} 
0 packages upgraded, 0 newly installed, 13 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 54.4MB will be freed.
Do you want to continue? [Y/n/?] n
Abort

```

The answer is no, as usual. The only possible reason is that there are some recursive dependencies between those packages. So I need to identify the minimum set of packages that allow to keep all packages installed. For this, I examin the depencies of each of the above "will be REMOVED" packages:

```
$ PKGS="gnome-user-guide-en language-pack-en language-pack-en-base language-pack-gnome-en language-pack-gnome-en-base language-support-en language-support-writing-en openoffice.org-hyphenation openoffice.org-hyphenation-en-us openoffice.org-thesaurus-en-au openoffice.org-thesaurus-en-us wamerican wbritish"
$ for i in $PKGS; do
>     echo ">>> $i"
>     aptitude search "~i(~Rdepends:~n\"^$i\$\"|~Rrecommends:~n\"^$i\$\")" | egrep "${PKGS// /|}"
> done
>>> gnome-user-guide-en
>>> language-pack-en
language-pack-en-base
>>> language-pack-en-base
language-pack-en
>>> language-pack-gnome-en
gnome-user-guide-en
language-pack-gnome-en-base
>>> language-pack-gnome-en-base
language-pack-gnome-en
>>> language-support-en
language-support-writing-en
>>> language-support-writing-en
openoffice.org-hyphenation
openoffice.org-hyphenation-en-us
openoffice.org-thesaurus-en-au
openoffice.org-thesaurus-en-us
wamerican
wbritish
>>> openoffice.org-hyphenation
>>> openoffice.org-hyphenation-en-us
>>> openoffice.org-thesaurus-en-au
language-support-en
>>> openoffice.org-thesaurus-en-us
language-support-writing-en
>>> wamerican
>>> wbritish

```

After analysing the output, you can conclude that a solution is to not mark language-pack-en, language-pack-gnome-en and language-support-en. So you can now type:

```
$ sudo aptitude markauto '~i(~Rdepends:~i|~Rrecommends:~i)!(~n"^language-pack-en$"|~n"^language-pack-gnome-en$"|~n"^language-support-en$")' 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Writing extended state information... Done
Reading package lists... Done             
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done

```

Now let us take a look at the few packages that have not been marked:

```
$ aptitude -F '%p' search '~i!~M'
dash
diff
grep
hostname
language-pack-en
language-pack-gnome-en
language-support-en
linux-generic
login
mktemp
ncurses-base
ubuntu-desktop
ubuntu-minimal
ubuntu-standard

```

Here is the trick... dash, diff, grep, hostname, login, mktemps and ncurses-base are required or recommended by no package at all, not even ubuntu-minimal or ubuntu-standard for example. I'm a bit surprised by this fact, and I don't think it was the case in the previous versions of Ubuntu. I think it is a bug that should be signaled but I want to know what you people think about that.

Thanks in advance.

---

