---
title: "Installation"
date: 2009-10-01
forum: Installation &amp; Upgrades
---

### Post by saroo on 2009-10-01
saravanan@saravanan-desktop:~$ chmod +x ./AdbeRdr9.1.0-1_i486linux_enu.bin
saravanan@saravanan-desktop:~$ ./AdbeRdr9.1.0-1_i486linux_enu.bin

Extracting files, please wait. (This may take a while depending on the configuration of your machine)

This installation requires 144 MB of free disk space.

Enter installation directory for Adobe Reader 9.1.0 [/opt]  

what i want to give now ?

---

### Post by -=hazard=- on 2009-10-01
/home/adobe   ?

---

### Post by saroo on 2009-10-01
Enter installation directory for Adobe Reader 9.1.0 [/opt]  /home/adobe

Directory  "/home/adobe"  does not exist.

Do you want to create it now? [y] y
ERROR: Cannot make directory "/home/adobe".

---

### Post by -=hazard=- on 2009-10-01
Try just by pressin Enter when asked for directory, maybe it has it's default one.

Or you can always install acroread from repo.

-Edit-

Or install the .deb one

[http://get.adobe.com/reader/otherversions/](http://get.adobe.com/reader/otherversions/)

---

### Post by saroo on 2009-10-01
same error only . . .

i have bin file and how to install in other way . . .

me doing in uduntu 9.04 tell the steps ....

---

### Post by Cato2 on 2009-10-01
It's best not to use the .bin file at all - it doesn't enable automatic security updates and Adobe Reader is a big target for attacks these days.

Instead, use the APT (apt-get) version - see [http://blogs.adobe.com/acroread/2009/04/adobe_reader_now_available_thr.html](http://blogs.adobe.com/acroread/2009/04/adobe_reader_now_available_thr.html)

Once you have the Canonical partner repository enabled, you can just do:

"sudo aptitude update && sudo aptitude install xyz" 

where xyz is the name of the package.  Then all future updates will include new versions of that package as needed.

Unless you need specific features of Adobe Reader, you can also just use evince, which should already be installed.

---

### Post by -=hazard=- on 2009-10-01
> **saroo said:**
> same error only . . .

i have bin file and how to install in other way . . .

me doing in uduntu 9.04 tell the steps ....

I repeat if you want adobe reader go and download the .deb file. Or install it with apt. Do this steps:

1 Open a terminal and do the following command:

sudo gedit /etc/apt/sources.list

2 Add the following 2 lines at the end of the file:

deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) jaunty partner
deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) jaunty partner

3 Save the file

4 On terminal enter the following commands:

sudo aptitude update
sudo aptitude install acroread


acroread is the bin that you have downloaded and you are trying to manually install, so this way I think you would not have problems.

---

### Post by saroo on 2009-10-01
thank you ...........

---

