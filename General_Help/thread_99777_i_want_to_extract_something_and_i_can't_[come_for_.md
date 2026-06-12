---
title: "i want to extract something and i can't [come for details]"
date: 2005-12-06
forum: General Help
---

### Post by SkillZero on 2005-12-06
hi guys.
i downloaded something(forgot what but its important lol)
its a rar file, inclouding the "usr" dir.
i want to add the files in there to my existing usr directory, and i can't, because i dont have permission to write there.
anyone can help me?

---

### Post by daller on 2005-12-06
What command are you using?

rar-files can be a pain!

Are you extracting with superuser-priviledges?

---

### Post by redactech on 2005-12-06
Well,

use the console 

ls -la /path/to/the/file.rar

post the result here

that said usr directory is not something to fiddle with unless you really know what you're doing...

files for users should stay in /home/NameOfTheUser

---

### Post by SkillZero on 2005-12-06
-rw-r--r--  1 ori ori 7701403 2005-12-06 17:13 usr.zip

ori = my username..

look, i am trying to extract it with double click , then extract, then the folder.
i wanted to do it with the terminal , but i don't know the command.

---

### Post by redactech on 2005-12-06
move the file to your home directory then create a temporary directory and move it there.

then with the console : 

chmod 777 nameofthefile.zip 

unzip nameofthefile.zip



you should be able to see the content of usr.zip

---

### Post by SkillZero on 2005-12-07
i know the contents of the file, i made it myself
my problem is extracting it to **my existing usr folder!**

---

