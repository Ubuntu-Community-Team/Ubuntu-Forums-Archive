---
title: "vifm 0.4"
date: 2008-08-10
forum: General Help
---

### Post by jetsabel on 2008-08-10
hello, i have recently got myself a laptop and have spent the past week setting up a nice fluxbox/ubuntu system. there are just a few things bothering me. when i get them fixed i look foward to sharing configs and participating in this forum!

i would like to use vifm for file management, but the version i get if i apt-get install vifm is 0.2 whuch does not display my japanese file names.

according to the [www.vifm.sourceforge.net](www.vifm.sourceforge.net), version 0.4 supports unicode. there is a link to a debian package but unfortunately it is broken.
i downloaded the source; it will ./configure but fails on make.
i am not sure what part of the make output is the problem so ive got it all here.

does anyone have vifm 0.4 running on ubuntu and if so, how?

```

root@jetsabel:/home/t/vifm-0.4# make
make  all-recursive
make[1]: Entering directory `/home/t/vifm-0.4'
Making all in src
make[2]: Entering directory `/home/t/vifm-0.4/src'
gcc -DHAVE_CONFIG_H -I. -I. -I..     -g -O2 -Wall -c vifm.c
vifm.c:21:20: error: ncurses.h: No such file or directory
In file included from bookmarks.h:22,
                 from vifm.c:28:
ui.h:77: error: expected specifier-qualifier-list before ‘WINDOW’
ui.h:110: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
ui.h:111: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
ui.h:112: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
ui.h:113: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
ui.h:114: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
ui.h:115: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
ui.h:116: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
ui.h:117: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
ui.h:118: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
ui.h:119: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
ui.h:120: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
vifm.c: In function ‘show_help_msg’:
vifm.c:49: warning: implicit declaration of function ‘printf’
vifm.c:49: warning: incompatible implicit declaration of built-in function ‘printf’
vifm.c: In function ‘main’:
vifm.c:77: error: ‘FileView’ has no member named ‘curr_line’
vifm.c:78: error: ‘FileView’ has no member named ‘top_line’
vifm.c:79: error: ‘FileView’ has no member named ‘list_rows’
vifm.c:80: error: ‘FileView’ has no member named ‘list_pos’
vifm.c:81: error: ‘FileView’ has no member named ‘selected_filelist’
vifm.c:82: error: ‘FileView’ has no member named ‘history_num’
vifm.c:83: error: ‘FileView’ has no member named ‘invert’
vifm.c:84: error: ‘FileView’ has no member named ‘color_scheme’
vifm.c:86: error: ‘FileView’ has no member named ‘curr_line’
vifm.c:87: error: ‘FileView’ has no member named ‘top_line’
vifm.c:88: error: ‘FileView’ has no member named ‘list_rows’
vifm.c:89: error: ‘FileView’ has no member named ‘list_pos’
vifm.c:90: error: ‘FileView’ has no member named ‘selected_filelist’
vifm.c:91: error: ‘FileView’ has no member named ‘history_num’
vifm.c:92: error: ‘FileView’ has no member named ‘invert’
vifm.c:93: error: ‘FileView’ has no member named ‘color_scheme’
vifm.c:126: error: ‘FileView’ has no member named ‘prev_invert’
vifm.c:126: error: ‘FileView’ has no member named ‘invert’
vifm.c:127: error: ‘FileView’ has no member named ‘hide_dot’
vifm.c:128: error: ‘FileView’ has no member named ‘regexp’
vifm.c:128: error: ‘FileView’ has no member named ‘regexp’
vifm.c:129: error: ‘FileView’ has no member named ‘prev_invert’
vifm.c:129: error: ‘FileView’ has no member named ‘invert’
vifm.c:130: error: ‘FileView’ has no member named ‘hide_dot’
vifm.c:131: error: ‘FileView’ has no member named ‘regexp’
vifm.c:131: error: ‘FileView’ has no member named ‘regexp’
vifm.c:155: warning: implicit declaration of function ‘snprintf’
vifm.c:155: warning: incompatible implicit declaration of built-in function ‘snprintf’
vifm.c:173: error: ‘FileView’ has no member named ‘curr_dir’
vifm.c:173: error: ‘FileView’ has no member named ‘curr_dir’
vifm.c:49: warning: implicit declaration of function ‘printf’
vifm.c:49: warning: incompatible implicit declaration of built-in function ‘printf’
vifm.c: In function ‘main’:
vifm.c:77: error: ‘FileView’ has no member named ‘curr_line’
vifm.c:78: error: ‘FileView’ has no member named ‘top_line’
vifm.c:79: error: ‘FileView’ has no member named ‘list_rows’
vifm.c:80: error: ‘FileView’ has no member named ‘list_pos’
vifm.c:81: error: ‘FileView’ has no member named ‘selected_filelist’
vifm.c:82: error: ‘FileView’ has no member named ‘history_num’
vifm.c:83: error: ‘FileView’ has no member named ‘invert’
vifm.c:84: error: ‘FileView’ has no member named ‘color_scheme’
vifm.c:86: error: ‘FileView’ has no member named ‘curr_line’
vifm.c:87: error: ‘FileView’ has no member named ‘top_line’
vifm.c:88: error: ‘FileView’ has no member named ‘list_rows’
vifm.c:89: error: ‘FileView’ has no member named ‘list_pos’
vifm.c:90: error: ‘FileView’ has no member named ‘selected_filelist’
vifm.c:91: error: ‘FileView’ has no member named ‘history_num’
vifm.c:92: error: ‘FileView’ has no member named ‘invert’
vifm.c:93: error: ‘FileView’ has no member named ‘color_scheme’
vifm.c:126: error: ‘FileView’ has no member named ‘prev_invert’
vifm.c:126: error: ‘FileView’ has no member named ‘invert’
vifm.c:127: error: ‘FileView’ has no member named ‘hide_dot’
vifm.c:128: error: ‘FileView’ has no member named ‘regexp’
vifm.c:128: error: ‘FileView’ has no member named ‘regexp’
vifm.c:129: error: ‘FileView’ has no member named ‘prev_invert’
vifm.c:129: error: ‘FileView’ has no member named ‘invert’
vifm.c:130: error: ‘FileView’ has no member named ‘hide_dot’
vifm.c:131: error: ‘FileView’ has no member named ‘regexp’
vifm.c:131: error: ‘FileView’ has no member named ‘regexp’
vifm.c:155: warning: implicit declaration of function ‘snprintf’
vifm.c:155: warning: incompatible implicit declaration of built-in function ‘snprintf’
vifm.c:173: error: ‘FileView’ has no member named ‘curr_dir’
vifm.c:173: error: ‘FileView’ has no member named ‘curr_dir’
vifm.c:174: error: ‘FileView’ has no member named ‘curr_dir’
vifm.c:174: error: ‘FileView’ has no member named ‘curr_dir’
vifm.c:175: error: ‘FileView’ has no member named ‘dir_entry’
vifm.c:176: error: ‘FileView’ has no member named ‘dir_entry’
vifm.c:177: error: ‘FileView’ has no member named ‘dir_entry’
vifm.c:178: error: ‘FileView’ has no member named ‘dir_entry’
vifm.c:179: error: ‘FileView’ has no member named ‘dir_entry’
vifm.c:180: error: ‘FileView’ has no member named ‘dir_entry’
vifm.c:197: warning: implicit declaration of function ‘endwin’
vifm.c:199: warning: incompatible implicit declaration of built-in function ‘printf’
vifm.c:212: error: ‘FileView’ has no member named ‘curr_dir’
vifm.c:212: error: ‘FileView’ has no member named ‘curr_dir’
vifm.c:220: error: ‘FileView’ has no member named ‘curr_dir’
vifm.c:220: error: ‘FileView’ has no member named ‘curr_dir’
vifm.c:243: error: ‘FileView’ has no member named ‘curr_dir’
vifm.c:247: warning: implicit declaration of function ‘mvwaddstr’
vifm.c:247: error: ‘FileView’ has no member named ‘win’
vifm.c:247: error: ‘FileView’ has no member named ‘curr_line’
vifm.c:248: warning: implicit declaration of function ‘wrefresh’
vifm.c:248: error: ‘FileView’ has no member named ‘win’
vifm.c:257: error: ‘FileView’ has no member named ‘curr_dir’
vifm.c:265: warning: implicit declaration of function ‘werase’
vifm.c:265: error: ‘status_bar’ undeclared (first use in this function)
vifm.c:265: error: (Each undeclared identifier is reported only once
vifm.c:265: error: for each function it appears in.)
vifm.c:266: warning: implicit declaration of function ‘wnoutrefresh’
make[2]: *** [vifm.o] Error 1
make[2]: Leaving directory `/home/t/vifm-0.4/src'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/t/vifm-0.4'
make: *** [all-recursive-am] Error 2

```

---

### Post by ajmorris on 2008-08-10
hi there,
try running:
```
sudo apt-get install build-essential
```

then running ./configure again

AJ

---

### Post by jetsabel on 2008-08-10
thanks for a quick response!
unfortunatley i have already installed build-essentials, it didn't change anything

---

### Post by ajmorris on 2008-08-10
hmm.. the ncurses header file appears to be at fault... you could try re-installing ncurses... i believe the ncurses package you want is the libncurses5-dev

---

### Post by jetsabel on 2008-08-10
thanks so much! that did the trick

but this new version also displays japanese characters as questionmarks. i must not have japanese terminal fornts in xterm...it does display korean characters correctly
i'll look into it.

---

### Post by ajmorris on 2008-08-10
> **jetsabel said:**
> thanks so much! that did the trick

but this new version also displays japanese characters as questionmarks. i must not have japanese terminal fornts in xterm...it does display korean characters correctly
i'll look into it.

I've no experience with japanese characters, however, you could try the xfonts-naga10  package, or language-support-fonts-ja, language-support-input-ja, language-support-ja  or some of the other japanese packages found from apt-cache search japanese :)

---

### Post by jetsabel on 2008-08-10
ok i figured it out, i was accessing the japanese files over SMB from a windows box.
it works fine if the files are local :D

hmmm, unicode over samba :/ thats a problem for another day

---

### Post by jetsabel on 2008-08-11
hmmm, looks like i spoke too soon.
when japanese files are local they display fine in bash and vim, but not vifm

unicode support is in the changelog for vifm0.4 but maybe it isn't enabled by default??
the usual way to enable/disable features at boot is something like ./configure --enable-unicode right? i cant find any documentation...

---

### Post by calumet on 2008-11-06
You need the ncursesw development package.  Debian and ubuntu seperate the ncurses program into ncurses and ncursesw packages.  The ncursesw package is the one that enables wide character support.  Vifm will use the ncursesw version if it is available and no configuration options are needed.

---

