---
title: "copy and restore home file permissions?"
date: 2008-10-31
forum: General Help
---

### Post by sdowney717 on 2008-10-31
I have been trying something
I created a login called 'test'

I then using root copied all home folders from one user to the home of test.
Of course then all files are owned by root so desktop does not work when logging in as 'test'

Is there a way to change all the files and folders ownership and group to 'test' in one command line?

[http://www.westwind.com/reference/OS-X/commandline/misc.html#find](http://www.westwind.com/reference/OS-X/commandline/misc.html#find)
I found this example
find -x / -user george -print0 | xargs -0 chown eva
    Search just the boot volume for files owned by George, and assign them to Eva instead.
    Note: you must be root to do this (otherwise, you'll get a lot of error messages).

so perhaps
find -x /home/test -user root -print0 | xargs -0 chown test


Well I tried this
in terminal typed sudo su

then I typed
find /home/test -user root -print0 | xargs -0 chown test

and that gave no errors, but I really dont know what I am doing here

---

### Post by ajgreeny on 2008-10-31
I think a more simple ```
sudo chown -R test:test /home/test
``` should work.  You don't say, but what is the situation now; is /home/test now owned and usable by user test?  I suspect all is well, but do let us know.

---

### Post by geirha on 2008-10-31
> **sdowney717 said:**
> 
then I typed
find /home/test -user root -print0 | xargs -0 chown test


"find /home/test" will recursively list all files and folders in /home/test
"find /home/test -user root" will do the same, but only files and folders owned by root
"find /home/test -user root -print0" This will print the filelist with a \0-character as delimiter, instead of a new-line (\n). The \0-character is one of the few characters not allowed in filenames on ext3, so it ensures that filenames with spaces and newlines will be treated properly.

"| xargs -0 chown test"
The output of that find is piped to xargs, which will turn this list of filenames into arguments for the command "chown test", which will thus change ownership of all files owned by root, to the user test. "The -0 option to xargs tells xargs to expect the list to be delimited by \0-characters, instead of the default, which is whitespace (' \t\n').


As for the other command you tried, with a -x. The find command in ubuntu is not the same as in Max OS-X. They generally do the same thing, but they are slightly different as to what options they accept. -x is probably the same as -xdev in ubuntu's find, though this is just a guess.

---

### Post by sdowney717 on 2008-10-31
sudo chown -R test:test /home/test
worked fine
I can log in as test and even the menu adjustments are there.
SO,
If I wanted to backup my home I would do this.

Login as another user to make sure my home files are not in use for copying
run gksudo Nautilus
select the home folder to backup
select hidden files options
copy the files and folders somewhere

To restore

create a login user 'test'
copy the backed up home files and folders into /home/test
run the command
sudo chown -R test:test /home/test

and everything is back like it was. (test is just a test name)

HOW well will this work if you upgrade using a fresh install, wipe partition, new install restore your home folders? OR across versions?

---

