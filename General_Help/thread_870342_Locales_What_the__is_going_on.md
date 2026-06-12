---
title: "Locales: What the *** is going on?"
date: 2008-07-25
forum: General Help
---

### Post by apmcd47 on 2008-07-25
If I use en_GB.utf8 I get weird characters in my man pages, eg from man ascii:
```
000   0     00    NUL **â**\0**â**                    100   64    40    @

``` (notice the characters (â) in bold - they should be **'** (single quote).

If I use en_GB I get eg:```
locale: Cannot set LC_CTYPE to default locale: No such file or directory
locale: Cannot set LC_MESSAGES to default locale: No such file or directory
locale: Cannot set LC_ALL to default locale: No such file or directory

```
What is going on? How do I fix this?

While I'm on a whinge about locales: nedit complains about locale not supported unless I set $LC_ALL to C, so I have a shell-wrapper to do that. Not Ideal, but it works. Thunderbird and Firefox both think I'm a Yank unless I start them from the command line. I also get this whenever I start k3b from the menu:```
System locale charset is ANSI_X3.4-1968

Your system's locale charset (i.e. the charset used to encode filenames)
is set to ANSI_X3.4-1968. It is highly unlikely that this has been done
intentionally. Most likely the locale is not set at all. An invalid
setting will result in problems when creating data projects.

Solution: To properly set the locale charset make sure the LC_*
environment variables are set. Normally the distribution setup tools
take care of this.

```Absolute rubbish - my locale IS set correctly, and I can't even find *ANSI_X3.4-1968* in my environment!

Can anyone shed some light on this? Obviously my locale is completely shite but I don't know enough about such things to fix it. I do have a /usr/lib/locale and inside there is an en_GB.utf8 directory but no en_GB directory.

System is:```
Distributor ID: Ubuntu
Description:    Ubuntu 7.10
Release:        7.10
Codename:       gutsy

```
My sanity is in your hands!

Andrew

---

### Post by apmcd47 on 2008-07-28
Just wondering if I should use the belocs-locales package to add en_GB to my system, and if so, how?

Andrew

---

### Post by redpotatoes on 2008-07-31
I also have the similar problem, when I tried to upgrade from gutsy to hardy, the upgrade got stock around "Generating locales...". Now I have a newly installed system fully upgraded with gutsy...


```
:~$ locale
LANG=
LC_CTYPE="POSIX"
LC_NUMERIC="POSIX"
LC_TIME="POSIX"
LC_COLLATE="POSIX"
LC_MONETARY="POSIX"
LC_MESSAGES="POSIX"
LC_PAPER="POSIX"
LC_NAME="POSIX"
LC_ADDRESS="POSIX"
LC_TELEPHONE="POSIX"
LC_MEASUREMENT="POSIX"
LC_IDENTIFICATION="POSIX"
LC_ALL=

```


I have the K3B error also:
```

System locale charset is ANSI_X3.4-1968

Your system's locale charset (i.e. the charset used to encode filenames)
is set to ANSI_X3.4-1968. It is highly unlikely that this has been done
intentionally. Most likely the locale is not set at all. An invalid
setting will result in problems when creating data projects.

Solution: To properly set the locale charset make sure the LC_*
environment variables are set. Normally the distribution setup tools
take care of this.
```

---

### Post by apmcd47 on 2008-08-13
I had a quick look on the Debian forums for my problem today. I didn't find a "real" solution, but someone mentioned changing the encoding on gnome-terminal. I'm actually using KDE and therefore konsole, but I checked the encoding on my home machine (the one I'm having problems with) and discovered that the encoding was set to "iso 8859-1". I changed this to "utf8" and set the locale env to en_GB.utf8 and '_man ascii_' works as expected! Save to default and login again, and the K3B problem seems to disappear too!

I may also have fixed *Thunderbird,* as well.

All I need to do now is fix the console font encoding ...

Andrew

---

