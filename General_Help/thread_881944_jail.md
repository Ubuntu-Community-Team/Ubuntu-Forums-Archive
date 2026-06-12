---
title: "jail"
date: 2008-08-06
forum: General Help
---

### Post by 0perator on 2008-08-06
hi, i am trying to jail someone on my ssh, and i have, /jail/make_chroot_jail.sh

so i cd /jail

and do this

./make_chroot_jail.sh coke (for the user called coke)

and it comes out with this.

```


Release: 2007-10-19

Am I root?  
  OK
Checking distribution... 
  Supported Distribution found
  System is running Debian Linux
Checking for which... 
  OK
Checking for chroot...
  OK
Checking for sudo...
  OK
Checking for dirname...
  OK
Checking for awk...
  OK

Subsystem sftp /usr/lib/openssh/sftp-server

-----------------------------
User coke exists. 

Are you sure you want to modify the users home directory and lock him into the
chroot directory?
Are you REALLY sure?
Say only yes if you absolutely know what you are doing!
(yes/no) -> yes

-----------------------------
The file /bin/chroot-shell exists. 
Probably it was created by this script.

Are you sure you want to overwrite it?
(you want to say yes for example if you are running the script for the second
time when adding more than one account to the jail)
(yes/no) -> yes

Modifying /etc/sudoers

Not creating new User account
Modifying User "coke" 
Copying files in coke's $HOME to "/home/jail/home/coke"

Adding User coke to jail
Copying necessary library-files to jail (may take some time)
mv: missing destination file operand after `.bak'
Try `mv --help' for more information.
mv: missing destination file operand after `.bak'
Try `mv --help' for more information.
./make_chroot_jail.sh: 428: cannot create : Directory nonexistent
./make_chroot_jail.sh: 428: cannot create : Directory nonexistent
./make_chroot_jail.sh: 428: cannot create : Directory nonexistent
./make_chroot_jail.sh: 428: cannot create : Directory nonexistent
./make_chroot_jail.sh: 428: cannot create : Directory nonexistent
./make_chroot_jail.sh: 428: cannot create : Directory nonexistent
./make_chroot_jail.sh: 428: cannot create : Directory nonexistent
./make_chroot_jail.sh: 428: cannot create : Directory nonexistent
./make_chroot_jail.sh: 428: cannot create : Directory nonexistent
./make_chroot_jail.sh: 428: cannot create : Directory nonexistent
./make_chroot_jail.sh: 428: cannot create : Directory nonexistent
./make_chroot_jail.sh: 428: cannot create : Directory nonexistent
./make_chroot_jail.sh: 428: cannot create : Directory nonexistent
./make_chroot_jail.sh: 428: cannot create : Directory nonexistent
./make_chroot_jail.sh: 428: cannot create : Directory nonexistent
./make_chroot_jail.sh: 428: cannot create : Directory nonexistent
./make_chroot_jail.sh: 428: cannot create : Directory nonexistent

```
the script doesnt actually end, it just hangs there....

help much a ppreciated thanks.

---

### Post by furlabs on 2008-08-10
Where did you get make_chroot_jail.sh from? 

I've found [**_jailkit_**]("http://olivier.sessink.nl/jailkit/") to be a very good ssh jail, maybe give that a go.

---

