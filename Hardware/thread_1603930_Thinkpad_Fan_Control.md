---
title: "Thinkpad Fan Control"
date: 2010-10-23
forum: Hardware
---

### Post by a-nubi-s on 2010-10-23
I'd like to get an application called Thinkpad Fan Control working in Maverick. 

The app in question -
[http://www.gambitchess.org/mediawiki/index.php/ThinkPad_Fan_Control](http://www.gambitchess.org/mediawiki/index.php/ThinkPad_Fan_Control)

It's worked brilliantly in previous releases but hasn't been updated in ages, the developer's email is disabled, and it now has an unmet dependency.
> the following packages have unmet dependencies:
tpfan-admin: Depends: python-gnome2-desktop (>= 2.22) but it is not installable

Does anybody know of an updated tpfan package or would anyone like to take a crack at repackaging it? 

I've searched PPAs and threads but only found one for Lucid, still doesn't work in Maverick - 
[https://launchpad.net/~jcollins/+archive/jaminppa](https://launchpad.net/~jcollins/+archive/jaminppa)

If there aren't any updated packages out there I'd appreciate some help on building from source.

---

### Post by lunatico on 2010-11-13
I upgraded today and I'm also looking for this. Did you ever got it working?

---

### Post by lunatico on 2010-11-13
Found the solution.

Download these files:
[tpfan-admin_0.96-ubuntu1_all.deb]("http://ppa.launchpad.net/tp-fan/ppa/ubuntu/pool/main/t/tpfan-admin/tpfan-admin_0.96-ubuntu1_all.deb")
[tpfand_0.95-ubuntu1_all.deb]("http://ppa.launchpad.net/tp-fan/ppa/ubuntu/pool/main/t/tpfand/tpfand_0.95-ubuntu1_all.deb")

Double-click tpfand_0.95-ubuntu1_all.deb and install it.

Right-click tpfan-admin_0.96-ubuntu1_all.deb and 'Extract Here'.

Rename the file tpfan-admin_0.96-ubuntu1_all.deb with tpfan-admin_0.96-ubuntu1_all.deb.old.

Now go into the 'tpfan-admin_0.96-ubuntu1_all' folder and then into the DEBIAN folder and open the file called 'control'.

Replace 'python-gnome2-desktop' with 'python-gnome2-desktop-dev'. Save and close.

Open a terminal and run this command:
```
dpkg-deb -D --build tpfan admin_0.96-ubuntu1_all
```

This will create a new admin_0.96-ubuntu1_all.deb. Double-click and install.

Now in the terminal again:
```
sudo gedit /usr/lib/python2.6/dist-packages/tpfand/settings.py
```

Find the lines 170-174 and replace:
```
self.product_id = None
self.product_name = None
self.product_pretty_vendor = None
self.product_pretty_name = None
self.product_pretty_id = None
```

With:
```
self.product_id = ""
self.product_name = ""
self.product_pretty_vendor = ""
self.product_pretty_name = ""
self.product_pretty_id = ""
```

Save and close.
	
```
sudo service tpfand restart
```

It should work now, go System -> Administrator -> Thinkpad Fan Control.

---

### Post by wilee-nilee on 2010-11-13
Check out gkrellm it is in the repos it works perfectly. If you need help setting it up just ask. Actually I mixed this up with dell computers never mind I have a think pad and a dell laptop.

---

### Post by OBIEKTYWNY on 2010-11-29
> **lunatico said:**
> Found the solution.

Download these files:
[tpfan-admin_0.96-ubuntu1_all.deb]("http://ppa.launchpad.net/tp-fan/ppa/ubuntu/pool/main/t/tpfan-admin/tpfan-admin_0.96-ubuntu1_all.deb")
[tpfand_0.95-ubuntu1_all.deb]("http://ppa.launchpad.net/tp-fan/ppa/ubuntu/pool/main/t/tpfand/tpfand_0.95-ubuntu1_all.deb")

Double-click tpfand_0.95-ubuntu1_all.deb and install it.

Right-click tpfan-admin_0.96-ubuntu1_all.deb and 'Extract Here'.

Rename the file tpfan-admin_0.96-ubuntu1_all.deb with tpfan-admin_0.96-ubuntu1_all.deb.old.

Now go into the 'tpfan-admin_0.96-ubuntu1_all' folder and then into the DEBIAN folder and open the file called 'control'.

Replace 'python-gnome2-desktop' with 'python-gnome2-desktop-dev'. Save and close.

Open a terminal and run this command:
```
dpkg-deb-D - build-tpfan admin_0.96-ubuntu1_all
```

This will create a new admin_0.96-ubuntu1_all.deb. Double-click and install.

Now in the terminal again:
```
sudo gedit /usr/lib/python2.6/dist-packages/tpfand/settings.py
```

Find the lines 170-174 and replace:
```
self.product_id = None
self.product_name = None
self.product_pretty_vendor = None
self.product_pretty_name = None
self.product_pretty_id = None
```

With:
```
self.product_id = ""
self.product_name = ""
self.product_pretty_vendor = ""
self.product_pretty_name = ""
self.product_pretty_id = ""
```

Save and close.
	
```
sudo service tpfand restart
```

It should work now, go System -> Administrator -> Thinkpad Fan Control.

That's work, but something is wrong in that line:
```
dpkg-deb-D - build-tpfan admin_0.96-ubuntu1_all
```
I used ```
dpkg-deb -b
```
but now I must to learn how to use that tool, because it doesn't recognize my T60?!

---

### Post by lunatico on 2010-11-29
> **OBIEKTYWNY said:**
> That's work, but something is wrong in that line:
```
dpkg-deb-D - build-tpfan admin_0.96-ubuntu1_all
```
I used ```
dpkg-deb -b
```
but now I must to learn how to use that tool, because it doesn't recognize my T60?!

Yes something was very wrong with that line... thanks for letting me know, I've fixed it.

---

### Post by Dreami78 on 2010-12-17
Hello

Im try to follow your instruction but when when i type 

```
dpkg-deb-D - build-tpfan admin_0.96-ubuntu1_all
```

I receive the following answer, eny error:

```
rina@rina-ThinkPad-T40:~$ dpkg-deb -D --build tpfan admin_0.96-ubuntu1_all
dpkg-deb: Cannot open information file »tpfan/DEBIAN/control« for reading: No such file or directory
```

(I translatet this in english because my system is installed in german :-), but i hope you understand to tell me where i make a mistake and why it says this error.

Can anyone help me?

Thanks for answering

Karin

---

### Post by tich on 2011-02-14
i get the same output from:

 dpkg-deb -D --build tpfan admin_0.96-ubuntu1_all

dpkg-deb: failed to open package info file `tpfan/DEBIAN/control' for reading: No such file or directory

has anyone figured out how to install this app?

---

### Post by lunatico on 2011-02-15
> **tich said:**
> 
has anyone figured out how to install this app?

Post #3 worked for me.

---

### Post by dave2001 on 2011-03-16
The PPA here mentioned by the OP now has versions for Lucid and Maverick
[https://launchpad.net/~jcollins/+archive/jaminppa]("https://launchpad.net/%7Ejcollins/+archive/jaminppa")

NOTE: You must use sudo or root authority when installing tpfand and tpfand_admin deb packages. Otherwise the installation may fail.

I have been using both these packages on my Thinkpad A20m since upgrading to Lucid and have had no problems.

---

### Post by Ninjapi on 2011-04-08
This works also for me under natty! 
I just installed the maverick packages. The important part is to change the python settings, as described in post #3

```

sudo gedit /usr/lib/python2.7/dist-packages/tpfand/settings.py

```(note: natty has already version 2.7)

---

### Post by unagimiyagi on 2011-05-04
Hi, for Natty, can you provide more detailed instructions on how you installed fan control for the thinkpad?  I can't get it to work on 11.04.

Thanks!

---

### Post by lunatico on 2011-05-05
> **unagimiyagi said:**
> Hi, for Natty, can you provide more detailed instructions on how you installed fan control for the thinkpad?  I can't get it to work on 11.04.

Thanks!

I haven't tried this on 11.04 and I'm not sure if I ever will... I'm a bit disappointed with it.

---

### Post by Allmighty_Lulala on 2011-06-24
Hello everybody,

I got the thinkpad fan control working (thanks to Lunatico's reply) but I can't do anything with it. The fan stays at the same rpm as before no matter how I change the settings. It just does not work at all. What's more I should do? Or does anybody know any other way how to control fan on thinkpad?

(T410i, 10.10)

big thanks in advance

---

### Post by Sicadastra on 2012-08-21
> **lunatico said:**
> Found the solution.

Download these files:
[tpfan-admin_0.96-ubuntu1_all.deb]("http://ppa.launchpad.net/tp-fan/ppa/ubuntu/pool/main/t/tpfan-admin/tpfan-admin_0.96-ubuntu1_all.deb")
[tpfand_0.95-ubuntu1_all.deb]("http://ppa.launchpad.net/tp-fan/ppa/ubuntu/pool/main/t/tpfand/tpfand_0.95-ubuntu1_all.deb")

Double-click tpfand_0.95-ubuntu1_all.deb and install it.

Right-click tpfan-admin_0.96-ubuntu1_all.deb and 'Extract Here'.

Rename the file tpfan-admin_0.96-ubuntu1_all.deb with tpfan-admin_0.96-ubuntu1_all.deb.old.

Now go into the 'tpfan-admin_0.96-ubuntu1_all' folder and then into the DEBIAN folder and open the file called 'control'.

Replace 'python-gnome2-desktop' with 'python-gnome2-desktop-dev'. Save and close.

Open a terminal and run this command:
```
dpkg-deb -D --build tpfan admin_0.96-ubuntu1_all
```This will create a new admin_0.96-ubuntu1_all.deb. Double-click and install.

Now in the terminal again:
```
sudo gedit /usr/lib/python2.6/dist-packages/tpfand/settings.py
```Find the lines 170-174 and replace:
```
self.product_id = None
self.product_name = None
self.product_pretty_vendor = None
self.product_pretty_name = None
self.product_pretty_id = None
```With:
```
self.product_id = ""
self.product_name = ""
self.product_pretty_vendor = ""
self.product_pretty_name = ""
self.product_pretty_id = ""
```Save and close.
    
```
sudo service tpfand restart
```It should work now, go System -> Administrator -> Thinkpad Fan Control.

Hello, will this work on 12.04 64-bit? Thank you.

---

### Post by lunatico on 2012-08-21
> **Sicadastra said:**
> Hello, will this work on 12.04 64-bit? Thank you.

To be honest I don't know, I haven't tried. I'm using Linux Mint 13 Cinnamon 32-bit which is based on Ubuntu 12.04 but I haven't tried to install this.

---

### Post by Sicadastra on 2012-08-21
> **lunatico said:**
> To be honest I don't know, I haven't tried. I'm using Linux Mint 13 Cinnamon 32-bit which is based on Ubuntu 12.04 but I haven't tried to install this.

I just managed to successfully install admin_0.96-ubuntu1_all.deb a few minutes ago, however when I try this (see below), a text file opens but without any data.

Now in the terminal again:
 	Code:
 	sudo gedit /usr/lib/python2.6/dist-packages/tpfand/settings.py 
So I cannot use your next instruction which is:

Find the lines 170-174 and replace:
 	Code:
 	self.product_id = None self.product_name = None self.product_pretty_vendor = None self.product_pretty_name = None self.product_pretty_id = None 
May I know if there's a solution for this? Thank you.

---

### Post by lunatico on 2012-08-21
> **Sicadastra said:**
> May I know if there's a solution for this? Thank you.

As I said, haven't tried so I don't know.
See if you find any useful info on any of this sites:
[http://www.thinkwiki.org/wiki/Fan_control_scripts](http://www.thinkwiki.org/wiki/Fan_control_scripts)
[http://www.gambitchess.org/mediawiki/index.php/ThinkPad_Fan_Control](http://www.gambitchess.org/mediawiki/index.php/ThinkPad_Fan_Control)
[https://launchpad.net/~tp-fan/+archive/ppa?field.series_filter=](https://launchpad.net/~tp-fan/+archive/ppa?field.series_filter=)

Good luck!

---

