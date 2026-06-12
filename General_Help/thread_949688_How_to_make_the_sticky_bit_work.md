---
title: "How to make the sticky bit work?"
date: 2008-10-16
forum: General Help
---

### Post by christian.convey on 2008-10-16
I'm trying to write a script that runs with someone else's permissions, but I can never get it to work.  In the example below, I've logged in as "cjc", but I want the script to run with "mary" 's permissions.  Can anyone spot what I'm doing wrong?

Thanks,
Christian

```
cjc@socrates:~/z$ ls -l
total 8
-rwx------ 1 mary cjc 13 2008-10-16 12:45 foo.txt
-rwsr-xr-x 1 mary cjc 27 2008-10-16 12:59 print-foo.sh
cjc@socrates:~/z$ sudo cat print-foo.sh
echo `whoami`
cat foo.txt

cjc@socrates:~/z$ ./print-foo.sh
cjc
cat: foo.txt: Permission denied
cjc@socrates:~/z$

```

---

### Post by SPr on 2008-10-16
```

su - mary -c /path/to/./print-foo.sh

```
You'll need mary's password though.

---

### Post by christian.convey on 2008-10-16
Thanks for the "su" suggestion, but I'm trying to avoid using that.  Especially because this is to be run by a cron job, so supplying a password isn't realistic.

From all of the documentation I can find, the "suid" permissions flag is the right way to accomplish my goal.  The problem is that my experiments seem to produce results that contradict everyone's documentation.

---

### Post by DGortze380 on 2008-10-16
> **christian.convey said:**
> this is to be run by a cron job, so supplying a password isn't realistic.


chown it to cjc. set permissions so everyone has read/execute (**5).
Set it in marys crontab.

on second thought, this may not work. Worth a try though. You could always just chown to mary and add it to her crontab

---

### Post by christian.convey on 2008-10-16
> **DGortze380 said:**
> chown it to cjc. set permissions so everyone has read/execute (**5).
Set it in marys crontab.

on second thought, this may not work. Worth a try though. You could always just chown to mary and add it to her crontab

Thanks, that sounds like a good solution to the problem at hand.

But I still have the problem about the apparent mismatch between the suid documentation and what I'm seeing with the experiment shown in my original post.

---

### Post by DGortze380 on 2008-10-16
> **christian.convey said:**
> Thanks, that sounds like a good solution to the problem at hand.

But I still have the problem about the apparent mismatch between the suid documentation and what I'm seeing with the experiment shown in my original post.

try chmod 750 foo.txt then run the script again. 

You are in the same group, so you have permissions for the script, but then the script tries to access a document you do not have access too (foo.txt).

I apologize if I totally misunderstand what you're trying to do.. just offering what I see in the output.

---

### Post by christian.convey on 2008-10-16
> **DGortze380 said:**
> try chmod 750 foo.txt then run the script again. 

You are in the same group, so you have permissions for the script, but then the script tries to access a document you do not have access too (foo.txt).

I apologize if I totally misunderstand what you're trying to do.. just offering what I see in the output.

Thanks, but that would defeat the point.  The idea is that if "suid" really works, than the script "print-foo.sh" should be running with mary's credentials, and thus be permitted to print out the content of foo.txt.

I gave this as a simplified example of my real problem.  My real problem is that I need to produce backups of a bunch of subversion repositories using the "svnadmin dump" command, and only one user has the needed authority to do that.  So I was going to have the my script that performs those backups run as that user.

An earlier poster suggested a solution that would work in my case (running a cron job as that particular user), but it still doesn't clear up the confusion about why the suid bit seems to not be working as expected.  I'm really keen to clear up that confusion.

---

### Post by bodhi.zazen on 2008-10-16
Break this into several steps.

First, get you script running under the user with permission.

Second allow other users to use the script. You do this with sudo :

sudo -u mary /path/to/script

You then configure sudo to allow users you wish to access the script.

[http://www.sudo.ws/sudo/man/sudoers.html](http://www.sudo.ws/sudo/man/sudoers.html)

The other option is to make a new group. Again make the script and set a SUID bit. Then change the permissions of the script to 1750. Members of the new group should then be able to run the script (make sure it is on their path, you *may* wish to place the script in /usr/local/bin).

[http://lokams.blogspot.com/2008/03/about-suid-sgid-and-sticky-bit.html](http://lokams.blogspot.com/2008/03/about-suid-sgid-and-sticky-bit.html)

---

### Post by geirha on 2008-10-16
Suid for scripts can be disabled in the kernel, and from what I understand from skimming through this thread, that's probably the case for ubuntu's kernel.

---

### Post by bodhi.zazen on 2008-10-16
> **geirha said:**
> Suid for scripts can be disabled in the kernel, and from what I understand from skimming through this thread, that's probably the case for ubuntu's kernel.

Thanks for the info, this is indeed the most likely problem.

I use sudo (as indicated in my post) and a google search shows :

[http://www.samag.com/documents/s=1149/sam0106a/0106a.htm](http://www.samag.com/documents/s=1149/sam0106a/0106a.htm)

[http://www.tuxation.com/setuid-on-shell-scripts.html](http://www.tuxation.com/setuid-on-shell-scripts.html)

(For the readers digest version, skip to the second link :) )

However I can also confirm the sudo -u works on a simple test script I wrote :

> #!/bin/bash

ID=`/usr/bin/id -u`
echo "$ID"Now test it (notice running as root :twisted: )

> [B][COLOR=red]root@hardy#./script
0[/COLOR][/B]

[COLOR=green][B]root@hardy#sudo -u bodhi ./script
1000[/B][/COLOR]

---

