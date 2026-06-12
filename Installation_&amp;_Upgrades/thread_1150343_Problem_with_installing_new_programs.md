---
title: "Problem with installing new programs"
date: 2009-05-06
forum: Installation &amp; Upgrades
---

### Post by shababhsiddique on 2009-05-06
Hello,
I am very new to ubuntu. I downloaded a free NetbeansIDE recently. The file was in .sh format. I dont know how to install it. Can any one tell me?
 NetBeans community says -

you need to make the installer files executable by using the following command: 
chmod +x ./<*installer-file-name*>

if i save the file "netbeans-6.5.1-ml-cpp-linux.sh" on desktop
should i write -

chmod +x ./home/shabab/Desktop/netbeans-6.5.1-ml-cpp-linux.sh

in the terminal window? If i do so nothing happens.

[ATTACH]112628[/ATTACH]

please help :(

---

### Post by tommcd on 2009-05-06
This is normal. If a terminal command returns with no errors then it worked. If there was a problem it would report errors. You can verify if it is executable by running:
```
ls -l /home/shabab/Desktop/netbeans-6.5.1-ml-cpp-linux.sh
```
If it is executable the file permissions will have something like: rwxrwxrwx. The "x" means executable.
Netbeans is in the Ubuntu repositories. Read these links on adding repositories and installing software in Ubuntu:
[http://www.psychocats.net/ubuntu/sources](http://www.psychocats.net/ubuntu/sources)
[http://www.psychocats.net/ubuntu/installingsoftware](http://www.psychocats.net/ubuntu/installingsoftware)

Ans welcome to the Ubuntu forums!

---

### Post by shababhsiddique on 2009-05-06
> **tommcd said:**
> This is normal. If a terminal command returns with no errors then it worked. If there was a problem it would report errors. You can verify if it is executable by running:
```
ls -l /home/shabab/Desktop/netbeans-6.5.1-ml-cpp-linux.sh
```If it is executable the file permissions will have something like: rwxrwxrwx. The "x" means executable.
Netbeans is in the Ubuntu repositories. Read these links on adding repositories and installing software in Ubuntu:
[http://www.psychocats.net/ubuntu/sources](http://www.psychocats.net/ubuntu/sources)
[http://www.psychocats.net/ubuntu/installingsoftware](http://www.psychocats.net/ubuntu/installingsoftware)

Ans welcome to the Ubuntu forums!

Thanks!
It really worked. The file is executable but when i try to run it stays still.

:)
by the way from the links you given i found NetBeans and installing it. Package Manager is downloading it would take about 1.5 hours.

---

### Post by rannday on 2009-05-06
If you right-click on the file in the file's location folder, and click properties, and browse to the Permission's tab, and check the check-box which says Execute: Allow executing file as program, then the ease-of-installation will be easier.

---

### Post by shababhsiddique on 2009-05-07
Thanks everybody for your kind info

---

