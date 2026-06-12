---
title: "[SOLVED] Need help on explaining 'diff' command output"
date: 2008-09-23
forum: General Help
---

### Post by abcuser on 2008-09-23
Hi,
in Ubuntu 8.04 in bash environment I would like to compare two files using diff command. So I used the following command:
```
diff old_file new_file
```

The output is:
```

299,304d295
< 11    011        173479 P
< 11    018        173479 P
< 11    011        173480 P
< 11    018        173480 P
< 11    011        173481 P
< 11    018        173481 P

```
So if I understand correctly code "299,304d" means delete lines from 299 to 304 from old_file to get new_file. But what does 295 means from string 299,304d**295**?

Thanks,
Abcuser

---

### Post by abcuser on 2008-09-23
Hi,
I have found the meaning. "296,301d292" string means when deleting lines 296 to 301 from old file you will get the same output as begining of 292 row of new file.

Why is this logical? Because in my first post I have posted just last part of file the full output is:
```

1,3d0
< 01    011        173479 P                 6       48580           0       48580
< 01    018        173479 P                 6        2160           0        2160
< 01    011        173480 P                 6       10345           0       10345
296,301d292
< 11    011        173479 P                 6      267195           0      267195
< 11    018        173479 P                 6       31445           0       31445
< 11    011        173480 P                 6      143040           0      143040
< 11    018        173480 P                 6        6050           0        6050
< 11    011        173481 P                 6       99705           0       99705
< 11    018        173481 P                 6       36165           0       36165

```
Numbers get sense if whole rules are read at ones.
Rule 1,3d0 means: delete lines 1 to 3 from old file and you will get the same output as after 0 line in new file. Rule 296,301d292 means delete lines 296 to 301 from old file and you will get the same output as after row 292 from new file.

So bottom line. Number before d tells what to do. Number after d just explains what will be output after delete operation.

One more thing: interesting -e switch which can be used to get rules that transforms old file to new file. Read more: [http://www.ncsa.uiuc.edu/UserInfo/Resources/Hardware/IBMp690/IBM/usr/share/man/info/en_US/a_doc_lib/cmds/aixcmds2/diff.htm](http://www.ncsa.uiuc.edu/UserInfo/Resources/Hardware/IBMp690/IBM/usr/share/man/info/en_US/a_doc_lib/cmds/aixcmds2/diff.htm)
Thanks,
Abcuser

---

