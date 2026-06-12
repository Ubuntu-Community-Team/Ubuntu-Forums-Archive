---
title: "WINE and RAR installed but not working"
date: 2009-03-17
forum: Installation &amp; Upgrades
---

### Post by mnellie on 2009-03-17
Hello,

I', running the last Ubuntu version and also it's 100% up to date according to the Update Manager application.

The issue:

I used the Ubuntu Add/Remove Applications menu to simultaneously install WINE and RAR. The download was successful and I received the message "new applications installed successfully" (or something alike), but even so these programs are not displayed in the Applications Menu. Also, although I can localize many executable files with the file browser's search tool, none of them related to these recent installed apps. works. They just don't run a thing. And there are also a lot of folders and files dated from today and the exactly hour I installed these applications WINE and RAR. So the files were downloaded, but it seems they were not installed correctly... I don't know for sure.

I had wine installed in this system before. It worked great, but it has the fault of not deleting the windows programs with the uninstall tool. Because of that, I unninstalled wine using the Ubuntu Add/Remove tool. But now that I want to install it again, I'm experiencing the above said issue.

In the other hand, I have never installed RAR in this system before. It was just installed for the first time and nothing, as said above too.

What should I do?

---

### Post by Partyboi2 on 2009-03-17
To use rar open a terminal (Applications>Accessories>Terminal) and type
```
rar
``` this will give you a list of commands and switches you can use with rar from the terminal.

With wine go to "Main Menu" (System>Pref>Main Menu) and on the right panel if you see "wine" listed untick then retick the box next to it. Then close 'Main Menu' and check if its now under the Applications menu.

---

### Post by mnellie on 2009-03-17
1) I've tried it before, but it does not work. There is a "wine" in the left panel. If i tick it, it will appear in the Applications menu, but when I click it, wine just don't run... So i think the best thing to solve this issue would be to know exactly what file is the executable one that will run WINE (not the file that will install it, but the file from which WINE runs after it is already installed in my Ubuntu Sys)

2) And in what concerns RAR, so you're telling me this application doesn't have a graphical interface like WINE? I ask because if this is correct, there is nothing wrong with RAR. But if it DOES have a graphical interface, it's important for me to know so I'll keep searching for a solution.

(yes, I like to keep things always organized and in its best performance... I'm just an organization freak, don't worry LoL)

Thanks.

---

### Post by oldos2er on 2009-03-17
Once you install rar and unrar, they are available graphically in Applications, Accessories, Archive Manager.

 Wine does nothing by itself; it's a programming layer for running Win* applications in Linux.

---

