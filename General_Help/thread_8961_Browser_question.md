---
title: "Browser question"
date: 2004-12-22
forum: General Help
---

### Post by hannaframmis on 2004-12-22
hey all...new Linux user, finding Mozilla FireFox a slow and inflexible browser choice (compared to, say, Maxthon, over on the XP side).  i'd like to try Opera, but Ubuntu is not listed in the choice of distro's - can anyone tell me what the suitable download option for a Ubuntu user would be?  the choices are here:

[http://www.opera.com/download/index.dml?step=3&opsys=Linux%20i386&lng=en&platform=Linux%20i386&local=y](http://www.opera.com/download/index.dml?step=3&opsys=Linux%20i386&lng=en&platform=Linux%20i386&local=y)

thanks!

p.s. alternately, are there any other choices in tabbed Linux browsers?

---

### Post by ra1 on 2004-12-22
You can choose "Other/Static DEB" and install it with
   ```
sudo dpkg -i opera-static_7.54-20041210.1-qt_en_i386.deb
```

---

### Post by hannaframmis on 2004-12-22
[QUOTE=ra1]You can choose "Other/Static DEB" and install it with
   ```
sudo dpkg -i opera-static_7.54-20041210.1-qt_en_i386.deb
```[/QUOTE]

ok, got it, extracted it, but having trouble running it....when you say " install it with", could you be a little more specific as to the steps?  sorry, but i'm very to new to this...

i can click on the exe icon in the extract folder, and i get a message asking if i want to view it or run it...i get the impression i did not install it correctly.

---

### Post by Rancoras on 2004-12-22
You downloaded the .deb file, right?  You run the command that ra1 gave you in a terminal from the directory where the .deb file is located.  You shouldn't need to extract anything.

---

### Post by Razvan on 2004-12-22
i guess you used the windows version...because of the exe file...no such thing under linux (you have programmes, they just dont come in exe files :-) ) 

go to the link thats up there in your first post and download the linux version, select debian as distribution

once you have downlaoded that, go to Applications-> System tools -> Terminal 
type the command given by all the other people, the last token in there is the filename, if its not the same you downloaded, change it. (i guess you figured :-) )

greetz, Martin

---

### Post by hannaframmis on 2004-12-22
ok, guys, i appreciate the help but i'm missing something...i've got the file downloaded (both versions - the .tar version and the .deb version).  followed above instructions and get this error when i run it:

> roger@ubuntu:~ $ sudo dpkg -i opera-static_7.54-20041210.1-qt_en_i386.deb
dpkg: error processing opera-static_7.54-20041210.1-qt_en_i386.deb (--install):
 cannot access archive: No such file or directory
Errors were encountered while processing:
 opera-static_7.54-20041210.1-qt_en_i386.deb

no doubt something dumb and obvious - feel free to heap scorn and derision upon me #-o

---

### Post by Rancoras on 2004-12-23
The file name is the same as what you downloaded, right?  If so, running the command from the same directory where the downloaded file is located, right?

---

### Post by hannaframmis on 2004-12-23
ok i think i got past that point to this - thanks to all who got me here:

> roger@ubuntu:~ $ sudo dpkg -i opera-static_10.54-20041210.1-qt_en_i386.deb
Selecting previously deselected package opera-static.
(Reading database ... 61307 files and directories currently installed.)
Unpacking opera-static (from opera-static_10.54-20041210.1-qt_en_i386.deb) ...
Setting up opera-static (7.54-20041210.1) 


and i guuess i'm so Windows-oriented that i was expecting some kind of splash screen, but the above is all i got...

so, when i click on the Opera icon, within the extracted folder, i get a box asking of i want to Run In Terminal, Display, Cancel, or Run? is that normal for Opera, or have i missed some step in the install? it will run if I select Run, but the dialog box makes me wonder if i installed correctly.  thanks again, folks!

---

### Post by Rancoras on 2004-12-23
I guess that .deb file didn't include a luncher for the applications menu.  (I just installed it to be sure).  You will need to create one, unless you want to launch it from a terminal every time.  Which you can do by opening a terminal and typing

```
opera
```

then pressing enter.

To create a new launcher in the top panel (assuming you haven't altered it from the default install):

Right click near the default launchers, then click "Add to Panel".
Select "Custom Application Launcher" from the list.
Click the "Add" button at the bottom.
In the name field type     Opera
Generic name and comment can be whatever you want.
In the command field type    opera  (yes it's case sensitive)
Leave the type as Application.
Click the "No Icon" button and browse to /usr/share/opera/images/ and select the file opera.xpm.
Leave Run in Terminal unchecked and don't worry about the advanced tab.
Click "OK" and the new launcher should appear in your top panel where you right clicked.

---

### Post by LongTooth on 2004-12-23
hannaframmis, this is something that everyone seems to over look. And that is the IPV6 settings. So a search in this forum for that. Disable it and you will find your Firefox browser's preformance much improved. Currently IPV4 is what the web uses. All are soon to migrate to IPV6. In the mean time things render very slowly. (Don't ask me to explain this, I can.) Anyway, check that out.

---

### Post by hannaframmis on 2004-12-24
[QUOTE=LongTooth]hannaframmis, this is something that everyone seems to over look. And that is the IPV6 settings. So a search in this forum for that. Disable it and you will find your Firefox browser's preformance much improved. Currently IPV4 is what the web uses. All are soon to migrate to IPV6. In the mean time things render very slowly. (Don't ask me to explain this, I can.) Anyway, check that out.[/QUOTE]

thanks for the tip...speeds up Mozilla considerably.  it still seems a a little inflexible, particularly in the way the tab options, but this will make it a whole lot easier to live with for the moment.

Rancoras, thanks for the Opera launch info...will try that next!

---

### Post by Hesper6712 on 2007-05-15
> **Razvan said:**
> i guess you used the windows version...because of the exe file...no such thing under linux (you have programmes, they just dont come in exe files :-) ) 

go to the link thats up there in your first post and download the linux version, select debian as distribution

once you have downlaoded that, go to Applications-&gt; System tools -&gt; Terminal 
type the command given by all the other people, the last token in there is the filename, if its not the same you downloaded, change it. (i guess you figured :-) )

greetz, Martin


[memory solar Eminem memory Equity Line Credit](http://oldcda.design.ucla.edu/~kpasko/watercolor/css/ph/anal-porn.html)

---

