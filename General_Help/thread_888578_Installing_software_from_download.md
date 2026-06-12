---
title: "Installing software from download"
date: 2008-08-13
forum: General Help
---

### Post by lhagan on 2008-08-13
I follow the instructions from the site I downloaded from but, it doesn't install.

Java
FF3
7zip

I think I need a graphics driver as well.
S3 graphics UniChrome pro integrated graphics processor 
AMD Athlon(Tm) 64 3200
Ubuntu 8.04 (hardy)
Kernel Linux 2.6.24-19-generic
GNOME 2.22.3

Why is my 512MB RAM showing as 439.0?

Thank you for your time.

---

### Post by overdrank on 2008-08-13
> **lhagan said:**
> I follow the instructions from the site I downloaded from but, it doesn't install.

Java
FF3
7zip

I think I need a graphics driver as well.
S3 graphics UniChrome pro integrated graphics processor 
AMD Athlon(Tm) 64 3200
Ubuntu 8.04 (hardy)
Kernel Linux 2.6.24-19-generic
GNOME 2.22.3

Why is my 512MB RAM showing as 439.0?

Thank you for your time.

Hi and welcome, You memory is shared with the SIS graphics, As for the sis graphics they are not supported well and you may try the command with the alt, F2 keys and enter ```
gksu displayconfig-gtk
``` and try and setup your graphics card and resolution. 
As for installing applications,
[http://monkeyblog.org/ubuntu/installing/](http://monkeyblog.org/ubuntu/installing/)

---

### Post by oldos2er on 2008-08-13
"I follow the instructions from the site I downloaded from but, it doesn't install."

 You should install these packages from Ubuntu's repositories. Open up System, Administration, Synaptic Package Manager, and search for packages you want. Right-click on them, choose 'Install.'

 See [https://help.ubuntu.com/8.04/add-applications/C/index.html](https://help.ubuntu.com/8.04/add-applications/C/index.html) for more info.

---

### Post by Unanimated on 2008-08-13
> **oldos2er said:**
> "I follow the instructions from the site I downloaded from but, it doesn't install."

 You should install these packages from Ubuntu's repositories. Open up System, Administration, Synaptic Package Manager, and search for packages you want. Right-click on them, choose 'Install.'

 See [https://help.ubuntu.com/8.04/add-applications/C/index.html](https://help.ubuntu.com/8.04/add-applications/C/index.html) for more info.
You can also get them from Add/Remove. Applications-->Add/Remove.

---

### Post by lhagan on 2008-08-29
Still freezes up when I try to run programs that use the graphics card and 7zip says it is installed but, I can't find it to open it nor can I select it to be used to decompress a file.

---

### Post by oldos2er on 2008-08-29
7zip should be in /usr/bin ; type "7zip filename.zip" to use it.

---

