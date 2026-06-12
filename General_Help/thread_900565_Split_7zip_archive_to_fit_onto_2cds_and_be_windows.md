---
title: "Split 7zip archive to fit onto 2cds and be windows compatible?"
date: 2008-08-25
forum: General Help
---

### Post by linuxisevolution on 2008-08-25
The title sums it up. How do i uncompress the two files in windows? I guess i would need to copy the two files to the hdd and recompile it in windows with *blank* program? What program would i use to join a xab and xaa file? Savy users will have to know how... i  will include the directions in the README file. Just tell me how. THANKS!

---

### Post by jerome1232 on 2008-08-25
From a comment on this posting [http://www.techiecorner.com/107/how-to-split-large-file-into-several-smaller-files-linux/](http://www.techiecorner.com/107/how-to-split-large-file-into-several-smaller-files-linux/)

Do you think that would work? (I don't have windows to try it on some random file)
> Just in case anybody needed (I did): if you use this command to split a binary file on *NIX and then copy the output to a DOS-aware system (Windows, for that matter) you can concatenate all the chunks using:
$> copy /B chunk* output

There's also this project which has ported cat to windows. [http://unxutils.sourceforge.net/](http://unxutils.sourceforge.net/)

Maybe also try cygwin which is sort of like wine for windows, of course providing an api layer for unix tools instead of windows programs.

Further googling looks like the dos command copy does it.
[http://www.ttlg.com/forums/showthread.php?t=80607](http://www.ttlg.com/forums/showthread.php?t=80607) another reference to copy.
this is the google search I did "how to concatenate files on windows"

---

