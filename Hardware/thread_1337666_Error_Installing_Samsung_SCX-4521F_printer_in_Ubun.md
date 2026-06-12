---
title: "Error Installing Samsung SCX-4521F printer in Ubuntu 9.10"
date: 2009-11-25
forum: Hardware
---

### Post by testmiss123 on 2009-11-25
I am trying to install Samsung SCX-4521F printer on ubuntu 9.10.  Ubuntu was a brand new clean install.  I downloaded the driver (UnifiedLinuxDriver_V1.01.tar.gz) from Samsung's website and followed the instructions.

The instructions were to extract the driver from the zip file and then perform:

**sudo cdroot/autorun.**  This command gave me the following error:

cdroot/Linux/install.sh: 11: source: not found
[: 670: unexpected operator

So I did this:

**sudo ./cdroot/Linux/install.sh**

and I still got the same error.  The error was:

./cdroot/Linux/install.sh: 11: source: not found
[: 670: unexpected operator

Can someone help me?

---

### Post by HappyFeet on 2009-11-25
Put the cdroot folder in your home folder. Then do: ```
sudo cdroot/autorun
```
Then:
```
sudo ln -s /usr/share/cups/model/samsung /usr/share/ppd/custom/samsung
```

Then go to system>administration>printing and add printer.

---

### Post by testmiss123 on 2009-11-25
I did what you said and I am still getting the same error:

I used the mv command to move cdroot folder to my home directory and I am still getting the error:

Here's the error:

eilangko@Ilangko-laptop:~$ pwd
/home/eilangko
eilangko@Ilangko-laptop:~$ [B]sudo cdroot/autorun
cdroot/Linux/install.sh: 11: source: not found
[: 670: unexpected operator[/B]

---

### Post by HappyFeet on 2009-11-25
You could have just dragged and dropped the folder into home, but anyway, try:

```
sudo sh cdroot/Linux/install.sh
```

You must always follow the path to the desired file. To launch **install.sh**, you must use **sh**.

If the directory was on your desktop, you would
```
sudo sh /home/your_user_name/Desktop/cdroot/Linux/install.sh
```

---

### Post by testmiss123 on 2009-11-25
Again I did what you said and I am getting the same error:

**sudo sh cdroot/Linux/install.sh**
cdroot/Linux/install.sh: 11: source: not found
[: 670: unexpected operator

---

### Post by bcrook88 on 2009-11-26
I am having exactly the same issue with exactly the same setup. I have another computer using an older version of the driver, on 9.10. I think Samsung updated the driver and messed up the script, I am not qualified to fix it up though...

---

### Post by testmiss123 on 2009-11-26
I changed the line #! /bin/sh to #! /bin/bash in cdroot/Linux/install.sh file and the installation worked fine.  However, while installing it gave me the following messages:

CUPS that is required for driver package to work properly was not
detected on your system. Please exit installation procedure and install
CUPS package from your Linux distribution CD-ROM or from Linux distribution

So I did: sudo apt-get install cupsys cupsys-client

But the message still remained the same.  I ignored it and moved on to the next line and the warning was:

SANE that is required for driver package to work properly was not
detected on your system. Please exit installation procedure and install
SANE package from your Linux distribution CD-ROM or from Linux distribution
vendor web site

So I did: sudo apt-get install libsane-extras

I still get the same message (and the same 2 messages).  Can I proceed by ignoring these messages?

---

### Post by testmiss123 on 2009-11-26
The easiset way is to go to the bin directory and follow the steps below:

cd /bin
sudo rm sh
sudo ln -s bash sh

This would have removed the link that was pointing to dash and will now point to bash.  This works!!!

---

### Post by bcrook88 on 2009-11-26
Thanks a lot. This helped me, the install process is still messed up but at least the drivers are installed. Hopefully Samsung realizes and fixes it. Once you get one that works, save it and never switch.

---

