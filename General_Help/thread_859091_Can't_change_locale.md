---
title: "Can't change locale"
date: 2008-07-14
forum: General Help
---

### Post by Majkijin on 2008-07-14
Hi,

I want to change my locale from en_US.UTF-8 to en_GB.UTF-8. I edited /etc/environment to:
```
$ cat /etc/environment
PATH="/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games"
LANG="en_GB.UTF-8"
LANGUAGE="en_GB:en"
```
but the locale is still en_US.UTF-8:
```
$ locale
LANG=en_US.UTF-8
LC_CTYPE="en_US.UTF-8"
LC_NUMERIC="en_US.UTF-8"
LC_TIME="en_US.UTF-8"
LC_COLLATE="en_US.UTF-8"
LC_MONETARY="en_US.UTF-8"
LC_MESSAGES="en_US.UTF-8"
LC_PAPER="en_US.UTF-8"
LC_NAME="en_US.UTF-8"
LC_ADDRESS="en_US.UTF-8"
LC_TELEPHONE="en_US.UTF-8"
LC_MEASUREMENT="en_US.UTF-8"
LC_IDENTIFICATION="en_US.UTF-8"
LC_ALL=
```
Anyone knows where I need to define the LANG and LANGUAGE variables to change my locale settings??

---

### Post by drs305 on 2008-07-14
Go to System > Administration > Language Support and you can change it there.
Select English in the top and tab the bottom options to English (United Kingdom).

If you don't see the various english options available, you might be able to restore these options by running:
```
sudo dpkg-reconfigure locales
```
This should 'repopulate' the english-based choices if you are starting from another english-based language. Then go back to Language Support to select "English - United Kingdom"

---

### Post by Majkijin on 2008-07-15
Thank you drs305 for your reply. I tryed to do as you wrote but although I can choose a "English - United Kingdom" from the list, just after clicking the "Apply" button it reverts automatically to "English - United States" and I still have a en_US.UTF-8 locale in my system.

After some time research I found that LANG and LANGUAGE variables are set not only in /etc/environment file but also in /etc/default/locale. I've changed their values to:
LANG=en_GB.UTF-8
LANGUAGE="en_GB:en"
in that file and I have now a en_GB.UTF-8 locale in my system.
My question is now what is the point to have a two different locations where localization variables takes their values during system start?

---

### Post by drs305 on 2008-07-15
> **Majkijin said:**
> 
My question is now what is the point to have a two different locations where localization variables takes their values during system start?

I can't really answer that. I can say that when I used the System > Admin > Lang option and rebooted it changed everything necessary on my machine and I didn't have to manually change anything. I checked the etc/default/locale file and it automatically changed after using the System option to change the language.

I also checked the default language after rebooting by running the "locale" command.

---

### Post by maximk on 2008-10-14
Have the same problem with freshly installed 8.04.1

I need different language UI and locale settings (english and russian correspondently).
Now I have totally russified system, but the translation is poor, so I prefer to switch to english UI but unable to!

In Language Selector I select English, then clicking Apply and it reverts back to Russian.

In /etc/environment I have:
```

LANGUAGE="en_US:en"
LANG="ru_RU.UTF-8"

```

In /etc/default/locale:
```

LANG=ru_RU.UTF-8
LANGUAGE="en_US:en"

```

But!!! LANGUAGE variable is totally unset. Even more - every Gnome/GTK application get its empty value before start, i.e. if I run gnome-terminal with custom environment:

```

env LANGUAGE=en_US:en gnome-terminal

```

Then in that new terminal window LANGUAGE still empty. On the other hand, xterm has no such problem, its environment stays preserved.

---

### Post by geirha on 2008-10-14
I haven't read up on how all these variables are supposed to work, but I often too prefer to start programs in english to avoid bad translations. I usually just open a terminal and do
```
LANG= program
```
which sets LANG to empty, which will turn off translations, and english is typically the untranslated language. LANG=en_US.utf8 works too of course, and gives you utf8, but longer to write :)

In the case of gnome-terminal though, the menu options are still translated to my default language. Not sure where it gets those strings from ... though all commands run from that terminal will be in english.

I think the language selector just sets the default language btw, so next time you log in, it will use the language you selected.

---

### Post by maximk on 2008-10-14
> **geirha said:**
> I haven't read up on how all these variables are supposed to work...

...skipped...

In the case of gnome-terminal though, the menu options are still translated to my default language. Not sure where it gets those strings from ... though all commands run from that terminal will be in english.


The problem is _all_ locale-specific environment variables get their default (in gnome point of view) values _every time_ gtk application starts.

This:
```

export LANG=en_US
gnome-terminal

```

Doesn't affect anything, because LANG in new terminal again has value "ru_RU.UTF-8". And I really confused _what_ makes it so.

---

### Post by geirha on 2008-10-14
Ah, indeed, I just tried again and it didn't work, I think I might have tested it on uxterm instead, in which it works.

Don't know where gnome-terminal gets its environment from, but I'd also like to know. If I figure it out, I'll post back.

---

### Post by maximk on 2008-10-20
Solution found.

gnome-terminal does not create separate process for each window. All share the one. So, running gnome-terminal without exporting environment variable doesn't affect anything.

But there is one another issue. GDM resets LANGUAGE varibale if it contains not the same language as GDM_LANG which in turn get its value from LANG or GDM-menu or ~/.dmrc

But, .dmrc does not allow to specify separate language for UI and locale. Neigther GDM menu does.

What did I do? Just added
```
export LANGUAGE=en_US.utf8
```
to ~/.gnomerc

.gnomerc runs before any gnome application (even panels etc) start, so all of them get correct value for LANGUAGE.

---

### Post by StuartN on 2009-12-16
I tried all the solutions in this thread, and none worked. My locale also became confused (i.e. appeared incorrectly as en_GB in locale) after manually installing packages.

What did work was to open System->Administration->Language Support, select another language setting and click OK, then reselect the original language setting and click OK. After this, the terminal reconfigure commands (sudo dpkg-reconfigure locales) worked as expected.

---

