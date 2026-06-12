---
title: "Error installing Asterisk"
date: 2005-11-12
forum: General Help
---

### Post by marcw on 2005-11-12
All of the Asterisk dependencies install without problems.  It's only Asterisk itself that returns the following error:

Preconfiguring packages ...
Selecting previously deselected package asterisk.
(Reading database ... 77836 files and directories currently installed.)
Unpacking asterisk (from .../asterisk_1%3a1.0.9.dfsg-1_i386.deb) ...
Setting up asterisk (1.0.9.dfsg-1) ...
adduser: Warning: The home dir you specified already exists.
Adding system user `asterisk'...
Adding new group `asterisk' (114).
Adding new user `asterisk' (114) with group `asterisk'.
Home directory `/var/lib/asterisk' already exists.
adduser: No more than two names.
dpkg: error processing asterisk (--configure):
 subprocess post-installation script returned error exit status 255
Errors were encountered while processing:
 asterisk
E: Sub-process /usr/bin/dpkg returned an error code (1)

What does it mean?  What can I do?  I beilieve this comes from Universe...

---

### Post by Xian on 2005-11-12
[QUOTE=marcw]What does it mean?  What can I do?[/QUOTE]
It means you need to create a sym link.
Issue the commands below from a terminal.

Then edit (if needed) /etc/default/asterisk for prefs.

```
$ sudo ln -s /usr/share/asterisk /var/lib/asterisk
$ sudo apt-get install asterisk
```

---

### Post by marcw on 2005-11-13
[QUOTE=Xian]It means you need to create a sym link.
Issue the commands below from a terminal.

Then edit (if needed) /etc/default/asterisk for prefs.

```
$ sudo ln -s /usr/share/asterisk /var/lib/asterisk
$ sudo apt-get install asterisk
```[/QUOTE]

I did this with the exact same results as my first post.  Please advise.  Thanks!

---

### Post by dghundt on 2005-11-19
I received the same error.
did you install libpri first.  this is required to install asterisk.

---

### Post by marcw on 2005-11-20
[QUOTE=dghundt]I received the same error.
did you install libpri first.  this is required to install asterisk.[/QUOTE]

Short answer: Yes.
Longer answer.  It shouldn't matter if I did or not because apt-get should resolve all dependancies.

In the meantime, I uninstalled all of the asterisk packages I had installed and installed asterisk from source.  Worked great.

---

### Post by dghundt on 2005-11-20
great!

i'm in a bit of a mess trying to install it myself.  I would greatly appreciate your help since you figured it all out!!!!!!
I followed the instructions that came with the tdm400P card but had to use sudo in front of some of the commands below:

cd /usr/src
export CVSROOT=:pserver:anoncvs@cvs.digium.com:usr/cvsroot
cvs login  (password is anoncvs)
cvs checkout zaptel libpri asterisk

cd /usr/src/zaptel
make clean  -    (at this point, these commands did not work)
make install       (but im supposed to do this for libpri and asterisk)

so i used
sudo apt-get install zaptel

and it seemed to work

tried this with libpri and it did not
I tried to download the files from the digium web site.  i pointed to extract them to the /usr/src/libpri folder but received error that i did not have permission to do this.  I would like to down load the latest release version.


HELP?!?
thanks

---

### Post by marcw on 2005-11-20
I simply grabbed all of the 1.2 release versions from the asterisk home page, extracted them to a temp dir and built according to the enclosed READMEs and the Asterisk book (online pdf).  Everything went pretty much according to Hoyle.  I built libpri first, the zaptel (just for ztdummy), asterisk and finally asterisk sounds.  I don't recall doing anything strange for compiling except that for zaptel I used 'make linux26' instead of just 'make' and since I have an older AMD system I modified my asterisk Makefile as per instructions.

One thing of note that I do recall - my compile of zaptel placed the modules zaptel and ztdummy in the wrong directory for some reason.  As such, they couldn't be found or loaded.  Once I discovered this and placed them in the correct dir, everything worked.

One tip I can give you is to read, read, and read some more.  Once you think you've read everything there is to read about asterisk, trust me, you haven't.

---

### Post by fizgig on 2006-02-18
I'm having the same problem as marcw above.  Thing is, I don't have the problem on a regular Breezy install.  I just installed a "server" Breezy install on another machine and I keep getting that message.  Solution offered by Xian doesn't work.  :(

---

### Post by fizgig on 2006-02-19
According to [this]("https://launchpad.net/distros/ubuntu/+source/asterisk/+bug/4731") bug report, I'm supposed to:

>  modify line 23 of postint file and change it from: adduser asterisk audio dialout
 to:
 adduser asterisk audio
adduser asterisk dialout


Can anyone tell me how to do that?  I don't know where the postint file is.  I didn't see it in the contents of the asterisk deb file in my cache.

---

### Post by fizgig on 2006-02-25
Screw it.  Installed it from source.

---

### Post by Michael_N on 2006-03-02
[QUOTE=marcw]I simply grabbed all of the 1.2 release versions from the asterisk home page, extracted them to a temp dir and built according to the enclosed READMEs and the Asterisk book (online pdf).  Everything went pretty much according to Hoyle.  I built libpri first, the zaptel (just for ztdummy), asterisk and finally asterisk sounds.  I don't recall doing anything strange for compiling except that for zaptel I used 'make linux26' instead of just 'make' and since I have an older AMD system I modified my asterisk Makefile as per instructions.

One thing of note that I do recall - my compile of zaptel placed the modules zaptel and ztdummy in the wrong directory for some reason.  As such, they couldn't be found or loaded.  Once I discovered this and placed them in the correct dir, everything worked.

One tip I can give you is to read, read, and read some more.  Once you think you've read everything there is to read about asterisk, trust me, you haven't.[/QUOTE]



Ok

I think i have the same problems with zaptel placed the modules in wrong directory.

So what is the correct directory?

---

### Post by fizgig on 2006-03-02
See my asterisk compile howto: [http://ubuntuforums.org/showthread.php?t=136785](http://ubuntuforums.org/showthread.php?t=136785)

---

### Post by Michael_N on 2006-03-02
[QUOTE=fizgig]See my asterisk compile howto: [http://ubuntuforums.org/showthread.php?t=136785](http://ubuntuforums.org/showthread.php?t=136785)[/QUOTE]
I get root@c-fa4670d5:/usr/src/zaptel# modprobe ztdummy
FATAL: Module ztdummy not found.
FATAL: Error running install command for ztdummy
root@c-fa4670d5:/usr/src/zaptel#

---

### Post by fizgig on 2006-03-02
If you're using a 2.6.x kernel, you don't need the ztdummy module.

---

### Post by Michael_N on 2006-03-02
[QUOTE=fizgig]If you're using a 2.6.x kernel, you don't need the ztdummy module.[/QUOTE]
Yes i use 2.6 kernel,  what makes the timming then?

---

### Post by fizgig on 2006-03-02
From the [free O'Reilly Asterisk book]("http://voipspeak.net/index.php?/content/view/33/2/"):

> On a 2.6 kernel–based distribution, ztdummy does not require the use of the USB controller. (As of v2.6.0, the kernel now provides 1-kHz timing with which the driver can interface; thus, the USB controller hardware requirement is no longer necessary.)

---

### Post by Michael_N on 2006-03-02
So i dont need to worry about ztdummy if i dont have zaptel card?

---

### Post by fizgig on 2006-03-02
Sigh....  From one paragraph earlier to the one I quoted you 10 min ago:

> In Asterisk, certain applications and features require a timing device in order to operate (Asterisk won’t even compile them if no timing device is found).

I suggest you stop all asterisk installation until you read that book cover to cover.

---

