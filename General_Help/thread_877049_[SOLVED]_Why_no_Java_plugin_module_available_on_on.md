---
title: "[SOLVED] Why no Java plugin module available on one computer"
date: 2008-08-01
forum: General Help
---

### Post by mikex on 2008-08-01
The Java(TM) Plug-in, Java SE 6 is an available option on one of my computers in the synaptics package manager, but no matter what I do it never will show up in the other computer's list (I just installed the 64 bit Ubuntu on it). 

I also ran sudo apt-get install sun-java6-plugin and it says the package is not available, has been obsoleted, or is only available from another source.

As far as I can tell all the package manager details are the same on both computers. Why have I been able to install this on one of my computers, but the other one simply refuses to acknwoledge this package exists for installation?

---

### Post by overdrank on 2008-08-01
> **mikex said:**
> The Java(TM) Plug-in, Java SE 6 is an available option on one of my computers in the synaptics package manager, but no matter what I do it never will show up in the other computer's list (I just installed the 64 bit Ubuntu on it). 

I also ran sudo apt-get install sun-java6-plugin and it says the package is not available, has been obsoleted, or is only available from another source.

As far as I can tell all the package manager details are the same on both computers. Why have I been able to install this on one of my computers, but the other one simply refuses to acknwoledge this package exists for installation?
Hi and you may check your repos 
[https://help.ubuntu.com/community/Repositories/Ubuntu](https://help.ubuntu.com/community/Repositories/Ubuntu)
And you can use add and remove  just set to all available applications.

---

### Post by mikex on 2008-08-01
The same repositories are loaded on both computers, but only one will display the java plugin as available for installation.

This is what is confusing me.

---

### Post by mrmorris on 2008-08-01
I am curious. What happens if you use apt from a command line?

sudo apt-get install sun-java6-jre sun-java6-fonts sun-java6-plugin

Update: Oops had allrady been suggested. Sorry.

---

### Post by mikex on 2008-08-01
> **mikex said:**
> 
I also ran sudo apt-get install sun-java6-plugin and it says the package is not available, has been obsoleted, or is only available from another source.

^^^ did that for the missing package. The other packages are in the synaptics list.

Put it this way... where exactly does the sun-java6-plugin package come, from-which repository?

---

### Post by bollix47 on 2008-08-01
There is no sun-java6-plugin for 64-bit.  It's supposedly coming in version 7 but that may be a while off.

---

### Post by mikex on 2008-08-01
> **bollix47 said:**
> There is no sun-java6-plugin for 64-bit.  It's supposedly coming in version 7 but that may be a while off as of yet.

OK that's a good explanation!

---

### Post by overdrank on 2008-08-01
Thats funny I am using the 64 bit and

---

### Post by bollix47 on 2008-08-01
If you had highlited the plugin instead of the runtime you would have seen that it's not supported for 64-bit.

---

### Post by LowSky on 2008-08-01
it might not be 64bit but it will run as a ported 32bit app. Same thing with flash.

[http://www.lockergnome.com/linux/2008/05/21/java-and-flash-on-ubuntu-heron-64-bit-linux/](http://www.lockergnome.com/linux/2008/05/21/java-and-flash-on-ubuntu-heron-64-bit-linux/)

---

### Post by bollix47 on 2008-08-01
> **LowSky said:**
> it might not be 64bit but it will run as a ported 32bit app. Same thing with flash.

[http://www.lockergnome.com/linux/2008/05/21/java-and-flash-on-ubuntu-heron-64-bit-linux/](http://www.lockergnome.com/linux/2008/05/21/java-and-flash-on-ubuntu-heron-64-bit-linux/)

Again, that's talking about the JRE not the plugin.

The best alternative for getting a plugin to work in 64-bit right now is to use IcedTea.

OR

A 32-bit browser using [Kilz's Script]("http://ubuntuforums.org/showthread.php?t=202537&highlight=kiltz").

---

