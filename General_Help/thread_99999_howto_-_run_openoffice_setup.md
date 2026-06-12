---
title: "howto - run openoffice setup???"
date: 2005-12-06
forum: General Help
---

### Post by mboto on 2005-12-06
Hi, I want install the mobile devices filter in openoffice (i am using 1.9.129) 
i found out that for this - i need to run oenoffice setup - there i can modify and install the device.

now i tried hard - and searched a lot - but i can`t find out how to start the openoffice setup

So, how do I do this (on linux kubuntu breezy)? I have looked for a file called 'oosetup' or 'ooosetup' but found none.

Any help would be great.

Will

---

### Post by Joe_CoT on 2005-12-06
Most programs in unix don't *have* installers. If they do, Ubuntu, for the most part, doesn't use them. That's what the package system is for.

the [xmerge](http://xml.openoffice.org/xmerge/downloads/) pack seems to be what you're looking for. You need to have the java virtual machine installed to use it ([How do I install java from apt repositories ?](https://wiki.ubuntu.com/forum/software/JavaApt)). then, in the console, cd to the directory you downloaded it to, and type
```
sudo java -jar XMergeInstall.jar
```

that should install the feature

---

### Post by mboto on 2005-12-07
doesn`t work - alway some .ini files missing... and the message "are you sure that staroffice is installed" .

i am sure - but i guess i found the answer on the link you send...

> The Mobile Device Support Pack is designed to work with OpenOffice 1.0. It should also work with OpenOffice 642 and OpenOffice 643. It has also been tested with StarOffice 6.0. There isn't currently a way to make it work with other builds. If there's a demand for supporting other builds then we'll make the necessary updates.

guess i use 1.9.129 - should be the reason for this.

thanks for your help... guess i have to wait

---

