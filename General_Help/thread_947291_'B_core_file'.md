---
title: "'B core file'"
date: 2008-10-14
forum: General Help
---

### Post by sulekha on 2008-10-14
Hi all,

This is what i have read in the book A practical guide to ubuntu Linux

sudo find / -type f -name core | xargs file | grep 'B core file' | sed 's/:ELF.*//g' | xargs rm -f


The find command lists all ordinary files named core and sends its output to xargs,which runs file on each of the files in the list. The file utility displays a string that includes B core file for files created as the result of a core dump. These files need to be removed. The grep command filters out from file any lines that do not contain this string. Finally sed removes everything following the colon so that all that is left on the line is the pathname of the core file; xargs then removes the file.

can any one explain me what exactly is meant by the string/search pattern
'B core file' ?

---

### Post by justleen on 2008-10-14
core files are normally created when your system crashes, or better : One the core is dumped. these file can contain vital clues as to wwhy the system chrashed

---

