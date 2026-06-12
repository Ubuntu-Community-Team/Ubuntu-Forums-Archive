---
title: "Annoying problem - shell scripts!"
date: 2008-07-13
forum: General Help
---

### Post by Sir.Storm25 on 2008-07-13
Hi All!!!

Ive only just started to get used to ubuntu, and, for some reason, shell scripts are no longer bring up a dialog with the Run in terminal, Display, Cancel etc...

Does anyone have any ideas on what program I should associate the .sh file type with???

Thanks, Sir.Storm25

---

### Post by jonlemur on 2008-07-13
You may first have to change the permissions to execute on the shell script.  From a terminal ```
sudo chmod +x /PATH/SHELLSCRIPT.sh
```  You can also run a shell script like that from a terminal just with ./SHELLSCRIPT.sh from its directory.

---

### Post by Squid Tamer on 2008-07-13
You can also right click on the script, select properties, select the permissions tab, and check "allow executing file as program".

I find it faster than navigating with the terminal to the correct directory.
(but whatever floats your boat:))

---

### Post by Sir.Storm25 on 2008-07-13
Wow! I never expected replies this quick!!!
Thanks for the help, its finally executing em again!
Thanks, Again!
Sir.Storm25.

---

