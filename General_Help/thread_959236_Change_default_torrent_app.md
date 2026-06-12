---
title: "Change default torrent app"
date: 2008-10-26
forum: General Help
---

### Post by small_sammy on 2008-10-26
Hi,

I have Xubuntu 8.04 and downloaded Vuze v4 (azureus).
I didnt install via apt-get because in the repositories the version of vuze is 2.5.

The application is very simple once you download it, there is no installation needed, just unpack and run the "azureus" script.

My problem is that i cannot set it as the default client for torrent files.

The ways I tried to do that are the following:

1. Save a torrent in my Desktop, right click, chose Open with, and since azureus does not appear as "registered" application, i just filled the command box on the bottom of the dialog with the full path to the azureus startup script, and checked the box to make it default. -- Didnt work, if i double click a torrent file just nothing happens

2. Went to Settings Manager-> Preffered Application but there is no option there to set it up...

I am very confused because if I launch a terminal and give the full path to the script (eg. /home/user/Applications/vuze/azureus) the app starts up normally.
But if for example I create a launcher in the desktop with the same command and I double click it nothing happens...

I have run out of ideas... :(

---

### Post by geirha on 2008-10-26
After double clicking a torrent file that should be opened in azureus (but doesn't), look at ~/.xsession-errors and see if it show any error messages regarding azureus.
```
cat ~/.xsession-errors
```

---

### Post by small_sammy on 2008-10-26
Well, nothing there.. here is the output..the last lines (but it goes like this from the beggining of file...just numbers)

```
41 56 6f 75 74 5f 6f 66 5f 72 
61 6e 67 65 40 73 74 64 40 40 
00 00 98 b9 40 00 00 00 00 00 
2e 3f 41 56 6c 65 6e 67 74 68 
5f 65 72 72 6f 72 40 73 74 64 
40 40 00 00 98 b9 40 00 00 00 
00 00 2e 3f 41 56 62 61 64 5f 
61 6c 6c 6f 63 40 73 74 64 40 

...Too much output, ignoring rest...

```

Also doing a 
```
tail -f /var/log/messages
```

didnt show anything related to azureus or vuze.

---

