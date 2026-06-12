---
title: "Installing Sane Backends"
date: 2008-07-12
forum: Hardware
---

### Post by Fatfool on 2008-07-12
Hello,

I would like to know how to Install the Sane CVS backends for Hardy.

[http://mp610.blogspot.com/2008_02_01_archive.html](http://mp610.blogspot.com/2008_02_01_archive.html)

Apparently the source is here:
[http://www.sane-project.org/snapshots/](http://www.sane-project.org/snapshots/)

and instructions here:
[http://mp610.blogspot.com/2008/04/give-your-scanner-new-freshly-sane.html](http://mp610.blogspot.com/2008/04/give-your-scanner-new-freshly-sane.html)

But I get lost along the way :confused:

has the Sane backends in Ubuntu stalled? it seems quite far back at 0.995 or something like that and it can't detect my MP220

---

### Post by matt$2 on 2008-07-12
This should be easy.
Firstly bring up synaptic package manager.
Make sure the package list is up to date.
Do a search on the key word sane.
It will list packages related and indicate whether or not they're installed.
I would think they will be there on offer to install.

If you can't follow the source path, tell us what and where you can't follow, and post.
We're left clueless

---

### Post by Fatfool on 2008-07-12
> **matt$2 said:**
> This should be easy.
Firstly bring up synaptic package manager.
Make sure the package list is up to date.
Do a search on the key word sane.
It will list packages related and indicate whether or not they're installed.
I would think they will be there on offer to install.

If you can't follow the source path, tell us what and where you can't follow, and post.
We're left clueless
erm the usual Sane backends are there but not the CVS (think these are the development versions)

and i get stuck on:
> Then, on both distributions, run the ./configure command like this:

$ ./configure --prefix=/usr --sysconfdir=/etc --localstatedir=/var

This will choose /usr/lib/sane as SANE lib directory, /etc/sane.d as SANE config files dir, and /var/lock/sane as state directory: The ones that are used by Mandriva and Ubuntu.

Check in the logs coming in the terminal window, at the end of the configure, that it will compile with usb support.

mine returns:
```
jeffery@Roomcomp:~$ ./configure --prefix=/usr --sysconfdir=/etc --localstatedir=/var
bash: ./configure: No such file or directory
jeffery@Roomcomp:~$ 
jeffery@Roomcomp:~$ 

```

---

### Post by matt$2 on 2008-07-12
You're simply located in the wrong place.
You trying to compile the source.  Once the source package is opened, you change to the top level directory of the package.
So if you are in /home and the package is too, then you should enter in a console
  ls
and it will list the contents of your home folder including the sane-version.tar.gz.
Once it's opened, there is a folder something like 
sane-version

cd to that folder. Enter 
ls
to confirm and observe the content.  There you should find the ./configure shell script.
Then carry on.

---

### Post by Fatfool on 2008-07-12
dang. no indication that I should do that. guess they expected me to do it.

now this portion:
> Set non-root users permissions

Now, permissions for non root users to access the scanners need to be set up, as not achieved by the “make install” statement.

These permission settings depend also on the Linux distribution: whether it uses hotplug, udev, …

Ubuntu and Mandriva both use udev to detect USB devices.

SANE compilation produces a udev rules file, covering all scanners handled.
It is named: sane-backends/tools/udev/libsane.rules
You'll need to install it, by simply replacing the current installed file (coming from the SANE package installed by your Linux distribution), with this new one.

    * Locate first this file
      in the /etc/udev/rules.d directory, it should be called XX-libsane.rules

I've gone to that directory but:

```
jeffery@Roomcomp:~$ cd /etc/udev/rules.d
jeffery@Roomcomp:/etc/udev/rules.d$ ls
[COLOR="Cyan"]025_libsane-extras.rules  [/COLOR]         70-persistent-cd.rules
05-options.rules                   70-persistent-net.rules
05-udev-early.rules                75-cd-aliases-generator.rules
20-names.rules                     75-persistent-net-generator.rules
30-cdrom_id.rules                  80-programs.rules
40-basic-permissions.rules         85-alsa.rules
40-permissions.rules               85-brltty.rules
45-fuse.rules                      85-hdparm.rules
45-libmtp7.rules                   85-hplj10xx.rules
50-libpisock9.rules                85-hwclock.rules
50-xserver-xorg-input-wacom.rules  85-ifupdown.rules
55-hpmud.rules                     85-pcmcia.rules
60-persistent-input.rules          90-modprobe.rules
60-persistent-storage.rules        95-hal.rules
60-persistent-storage-tape.rules   95-udev-late.rules
60-symlinks.rules                  README
61-persistent-storage-edd.rules
jeffery@Roomcomp:/etc/udev/rules.d$ 


```

XX-libsane.rules isn't there so i'll use 025_libsane-extras.rules instead?

I have the libsane extras package installed btw

---

### Post by Fatfool on 2008-07-12
I went ahead and used the libsane-extra.rules:

```
jeffery@Roomcomp:~/Desktop/sane-scm-2008-07-12/sane-backends$ cp /etc/udev/rules.d/025_libsane-extras.rules ~/Desktop
jeffery@Roomcomp:~/Desktop/sane-scm-2008-07-12/sane-backends$ sudo cp tools/udev/libsane.rules /etc/udev/rules.d/025_libsane-extras.rules
[sudo] password for jeffery: 
jeffery@Roomcomp:~/Desktop/sane-scm-2008-07-12/sane-backends$ scanimage -V
scanimage (sane-backends) 1.1.0-cvs; backend version 1.1.0
jeffery@Roomcomp:~/Desktop/sane-scm-2008-07-12/sane-backends$ scanimage -L
device `pixma:04A91722' is a CANON Canon PIXMA MP220 multi-function peripheral
jeffery@Roomcomp:~/Desktop/sane-scm-2008-07-12/sane-backends$ scanimage –T
scanimage: open of device pixma:04A91722 failed: Access to resource has been denied
jeffery@Roomcomp:~/Desktop/sane-scm-2008-07-12/sane-backends$ scanimage -L
device `pixma:04A91722' is a CANON Canon PIXMA MP220 multi-function peripheral
jeffery@Roomcomp:~/Desktop/sane-scm-2008-07-12/sane-backends$ scanimage –T
scanimage: open of device pixma:04A91722 failed: Access to resource has been denied
jeffery@Roomcomp:~/Desktop/sane-scm-2008-07-12/sane-backends$ 


```

seems it can detect... but can't access the scanner?

---

### Post by matt$2 on 2008-07-12
I'm fairly sure you need to do one more thing that the instructions missed, or you missed in the instructions.

Go to the Admin categories and bring up Users and groups.
Find a group called scanners or something like it.
Make yourself a member.
Save.
You should be sweet.

Try again, then post.

---

### Post by Fatfool on 2008-07-12
> **matt$2 said:**
> I'm fairly sure you need to do one more thing that the instructions missed, or you missed in the instructions.

Go to the Admin categories and bring up Users and groups.
Find a group called scanners or something like it.
Make yourself a member.
Save.
You should be sweet.

Try again, then post.
this one?

[IMG]http://img300.imageshack.us/img300/3341/admingrouphs6.png[/IMG]

ticked that box but it still gives the same message....

---

### Post by matt$2 on 2008-07-12
yep.

---

### Post by Fatfool on 2008-07-12
> **matt$2 said:**
> yep.
erm yes but it still goes:

```
jeffery@Roomcomp:~/Desktop/sane-scm-2008-07-12/sane-backends$ scanimage &#8211;T
scanimage: open of device pixma:04A91722 failed: Access to resource has been denied
```

---

### Post by matt$2 on 2008-07-12
Perhaps you missed entering yourself.  Double check.
Not being in the group will lead to exactly that.

If you're desperate, prefix your entry with a 
sudo

That should at least get you there

---

### Post by Fatfool on 2008-07-12
> **matt$2 said:**
> Perhaps you missed entering yourself.  Double check.
Not being in the group will lead to exactly that.

If you're desperate, prefix your entry with a 
sudo

That should at least get you there
sorry had to go out for a while.

hmm... entering myself? but i'm using checking the box on the my 'jeffery' account.

as you can see:
[IMG]http://img254.imageshack.us/img254/8725/scannergroupig4.png[/IMG]

sudo doesn't work either.....

---

### Post by Fatfool on 2008-07-12
> **Fatfool said:**
> sorry had to go out for a while.

hmm... entering myself? but i'm using checking the box on the my 'jeffery' account.

as you can see:
[IMG]http://img254.imageshack.us/img254/8725/scannergroupig4.png[/IMG]

sudo doesn't work either.....
AH!

ok it works now. apparently, the Comp needs to be restarted. it scans quite loudly though....

thanks for your help matt!

btw can i get rid of the source code files + all the compiled stuff thingy on my desktop?

---

### Post by matt$2 on 2008-07-13
excellent.

yep you sure can.  Up to you but I'd keep the core package-version.tar.gz and delete the compiled source folders.

Happy scanning

can you edit your thread to a resolved state???

bye

---

### Post by Fatfool on 2008-07-13
> **matt$2 said:**
> excellent.

yep you sure can.  Up to you but I'd keep the core package-version.tar.gz and delete the compiled source folders.

Happy scanning

can you edit your thread to a resolved state???

bye
dang. How's that done? do I just put [Resolved] before the title?

oh and one last question, I ticked the box to use the scan button on the scanner itself in Xsane but it couldn't scan after that so i need to untick it or reset the settings. Problem is, I can't find the page to disable the scan button. (it lists the device as busy)

edit: found it, it was under standard options.

---

### Post by matt$2 on 2008-07-13
I haven't done it myself on this forum, but go back to the original thread you created.  You'll see two command buttons in the corner.
Select edit.  Go to your title.  Hit the drop box to the left of your title and it's hopefully in there.  Otherwise, look hard. Be inventive.

---

### Post by Fatfool on 2008-07-13
> **matt$2 said:**
> I haven't done it myself on this forum, but go back to the original thread you created.  You'll see two command buttons in the corner.
Select edit.  Go to your title.  Hit the drop box to the left of your title and it's hopefully in there.  Otherwise, look hard. Be inventive.
isn't there.... arg.......

have you seen any resolved tags in this forum?

---

### Post by matt$2 on 2008-07-13
go back to the original thread you created. You'll see two command buttons in the corner.
Select edit. Go to your title.  Just add   [Resolved}  to the end of the title.

---

### Post by Fatfool on 2008-07-13
> **matt$2 said:**
> go back to the original thread you created. You'll see two command buttons in the corner.
Select edit. Go to your title.  Just add   [Resolved}  to the end of the title.
nope, ain't working.

---

