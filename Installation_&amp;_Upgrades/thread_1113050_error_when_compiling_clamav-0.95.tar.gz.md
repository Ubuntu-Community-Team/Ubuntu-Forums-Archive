---
title: "error when compiling clamav-0.95.tar.gz"
date: 2009-04-01
forum: Installation &amp; Upgrades
---

### Post by sadicote on 2009-04-01
When doing sudo freshclam, i used to get that "your clamav installation is outdated. Don't Panic" message. So i downloaded the latest clamav, removed and purged the old clamav, made the prescribed additions to Software sources, and updated. When installing the tarball I had no problems till i came to the './configure' step. After that i got some error which i believe had something to do with having a clamav user account. Please excuse my vague descriptions, it stems from my limited knowledge. I went to Users and groups, unlocked all users including root, and created a new user called clamav. Still no joy. Could someone please help me to install this, clamav is the only protection that i intend to use.

I am running Jaunty, and sudo apt-get install clamav still gives me the outdated clamav-0.94.

---

### Post by sadicote on 2009-04-01
"Err http: //ppa.launchpad.net/ubuntu-clamav/ppa/ubuntu/jaunty Packages         
  Unable to connect to  http:
Err http: //ppa.launchpad.net/ubuntu-clamav/ppa/ubuntu/main Packages           
  Unable to connect to  http:
Err http: //ppa.launchpad.net/ubuntu-clamav/ppa/ubuntu/jaunty Sources          
  Unable to connect to  http:"

Why? Why? Every time...

---

### Post by Partyboi2 on 2009-04-01
> **sadicote said:**
> "Err http: //ppa.launchpad.net/ubuntu-clamav/ppa/ubuntu/jaunty Packages         
  Unable to connect to  http:
Err http: //ppa.launchpad.net/ubuntu-clamav/ppa/ubuntu/main Packages           
  Unable to connect to  http:
Err http: //ppa.launchpad.net/ubuntu-clamav/ppa/ubuntu/jaunty Sources          
  Unable to connect to  http:"

Why? Why? Every time...
Are you using a proxy?

---

### Post by sadicote on 2009-04-02
> **Partyboi2 said:**
> Are you using a proxy?

No, and I am able to "Hit" all the other sources in my list.

---

### Post by jra456 on 2009-04-02
Sadicote,

If you are trying to compile from source, you need to tell configure the username and group, e.g.

$ ./configure --with-user=clamav --with-group=clamav

Of course, you have to create a clamav group and put the clamav user in it before you do this :)

---

### Post by lloyd_b on 2009-04-02
> **sadicote said:**
> "Err http: //ppa.launchpad.net/ubuntu-clamav/ppa/ubuntu/jaunty Packages         
  Unable to connect to  http:
Err http: //ppa.launchpad.net/ubuntu-clamav/ppa/ubuntu/main Packages           
  Unable to connect to  http:
Err http: //ppa.launchpad.net/ubuntu-clamav/ppa/ubuntu/jaunty Sources          
  Unable to connect to  http:"

Why? Why? Every time...
Just something I noticed - there appears to be a space between the "http:" and the "//ppa...".  Is that a typo, or do you have an extra space in those lines in "sources.list"?

Lloyd B.

---

### Post by sadicote on 2009-04-02
Thanks guys, you have hit the nail i think. About "```
Of course, you have to create a clamav group and put the clamav user in it before you do this
```", could you please tell me how?

and yes, thanks, i see it (the extra space) now!:redface::redface:

Edited: I did manage to add clamav group and user, but the compile command you suggested "./configure --with-user=clamav --with-group=clamav" gave me an error, so i deleted the clamav user and did a sudo apt-get install clamav (thanks to my corrected apt lines) and everything went okay till this:

Setting up clamav-freshclam (0.95+dfsg-2ubuntu1) ...
 * Reloading AppArmor profiles ...                                       [ OK ] 
 * Starting ClamAV virus database updater freshclam                      [ OK ] 

Setting up clamav (0.95+dfsg-2ubuntu1) ...
sade@sade-desktop:~$ sudo freshclam
ClamAV update process started at Fri Apr  3 12:46:37 2009
main.cvd is up to date (version: 50, sigs: 500667, f-level: 38, builder: sven)
ERROR: chdir_tmp: Can't create directory ./clamav-1e5c877a6220eca344250ef287200b70
WARNING: Incremental update failed, trying to download daily.cvd
ERROR: getfile: Can't create new file /usr/local/share/clamav/clamav-2cea4032c7cf0cda33d940d827b3541c in /usr/local/share/clamav
Hint: The database directory must be writable for UID 113 or GID 127
WARNING: Can't download daily.cvd from database.clamav.net
sade@sade-desktop:~$ 

Please shed some light.

---

### Post by jra456 on 2009-04-03
Sadicote,

"Hint: The database directory must be writable for UID 113 or GID 127"

It looks as if /usr/local/share/clamav has incorrect permissions or ownership. Did you delete the clamav group as well as the user before doing the apt-get? If not, you may have caused something to get confused.

Do the user & group specified in /usr/local/etc/clamd.conf match User ID 113 and Group ID 127 as specified in /etc/passwd and /etc/group? What are the permissions on the directory?

Did you actually try to build from source (make install)?. If so you need to do "make uninstall" before trying to install the package.

Jon

---

### Post by sadicote on 2009-04-04
I had deleted the user clamav and group clamav that i had created earlier. My /usr/local/etc/clamd.conf shows: 
# This option allows you to save a process identifier of the listening
# daemon (main thread).
# Default: disabled
#PidFile /var/run/clamd.pid

# Optional path to the global temporary directory.
# Default: system specific (usually /tmp or /var/tmp).
#TemporaryDirectory /var/tmp

# Path to the database directory.
# Default: hardcoded (depends on installation options)
#DatabaseDirectory /var/lib/clamav


I removed clamav, then did a sudo apt-get install clamav. Clamav, clamav-base and clamav-freshclam did get installed this time (clamav-0.95) as indicated in the terminal but sudo freshclam gives "can't change dir to /var/clamav" and Virus scanner does not show in Applications. I am prepared to remove the whole thing and try it all over again, please stay with me on this. I have installed avast as a temporary measure, but i believe that something made especially for Ubuntu will function a lot better.
When i tried changing permissions i got "you are not the owner", but i am!

Also freshclam.conf has 'Example' uncommented, When i commented it and tried to save--"Could not save...you do not have the permissions necessary to save this file"

Edited: I have now removed clamav and reinstalled it from Synaptic along with all dependencies. Sudo freshclam still gives "Can't change dir to /var/clamav"

---

### Post by gnosoz on 2010-04-08
Hi guys,
thanks for the help as I had the same issue this morning and your informations helped me a lot. Now I totally sorted the issue and here below you can find all details from scratch up to the update.

Here we go the solution that worked for me:

----------------------------------------------------------------
$ sudo tar xvf /kekko/clamav-0.95.3.tar.gz 
$ cd clamav-0.95.3/
$ ./configure
$ make

@@@@@ trouble on output missing zlib
@@@@@ installed libraries for zlib

$ make

@@@@@ trouble on output missing user and group clamav

$ ./configure --with-user=clamav --with-group=clamav
$ make

@@@@@ still same error = trouble on output missing user and group clamav
@@@@@ I created them using the GUI provided "System/Administration/Users & Groups" with UID 113 and GID 127 (Obviously I gave to the user the group clamav that should be created as first and the password for the user I used is clamav so that I wont forget btw is this a possible threat??)

$ ./configure --with-user=clamav --with-group=clamav
$ make
$ sudo make install
$ cd ..
$ clamscan -r -l test.txt clamav-0.95.3 

@@@@@ it gave me an error as a library is wrongly located as it was happening in the previous versions I discovered in another forum and the solution suggested was to run ldconfig to solve the problem

$ cd /clamav-0.95.3
$ sudo ldconfig
$ cd ..
$ clamscan -r -l test.txt clamav-0.95.3 

@@@@@ Finally it makes the test scan finding the test viruses that have been placed there for the test after installation so it works!!! :)
@@@@@ obviously clamav is telling me that the definitions are older than 7 days and to update them I need to run freshclam but this will work only if I configure it and the file is located in /usr/local/etc/freshclam.conf
@@@@@ you will need to edit it and uncomment all lines you are interested in but remember to comment the line in which is written Example else it will give you an error when running freshclam command

$ sudo freshclam

@@@ To discover commands and other interesting thing on how to use it you can read below link
[https://help.ubuntu.com/community/ClamAV#Using%20ClamAV](https://help.ubuntu.com/community/ClamAV#Using%20ClamAV)

I hope it helps :-))

---

