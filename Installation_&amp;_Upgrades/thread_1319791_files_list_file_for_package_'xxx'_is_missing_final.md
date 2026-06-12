---
title: "files list file for package 'xxx' is missing final newline"
date: 2009-11-08
forum: Installation &amp; Upgrades
---

### Post by pokerbirch on 2009-11-08
Ok, i've had this error for several weeks now and have not been able to install ANY updates. Did some searching and couldn't find much info, so decided to check it out myself. The 'missing final newline' was a bit of a giveaway really, so i created a python script to check how many files inside /var/lib/dpkg/info/ were actually missing the final newline character.

I then modified my script to append a newline to the files that were missing it, which fixed my problem. Not sure how these files managed to get corrupted but hey-ho. Is this a satisfactory answer or will i be misleading new users by posting this script???

[PHP]
#!/usr/bin/python


# 8th November, 2009
# update manager failed, giving me the error:
#       'files list file for package 'xxx' is missing final newline' for every package.
# some Googling revealed that this problem was due to corrupt files(s) in /var/lib/dpkg/info/
# looping though those files revealed that some did not have a final new line
# this script will resolve that problem by appending a newline to all files that are missing it
# NOTE: you will need to run this script as root, e.g. sudo python newline_fixer.py

import os

dpkg_path = '/var/lib/dpkg/info/'
paths = os.listdir(dpkg_path)
for path in paths:
    path = dpkg_path + path
    f = open(path, 'a+')
    data = f.read()
    if len(data) > 1 and data[-1:] != '\n':
        f.write('\n')
        print 'added newline character to:', path
    f.close()
[/PHP]

---

### Post by Quantek on 2009-11-15
Hello!!!

[FONT=Arial]I got the error described as[/FONT] "**files list file for package 'xxx' is missing final newline"**because an accidental blackout while doing an ubuntu(Hardy) updatewith package manager.

No updates were possibles after that, and not too much information through google, even some programs presented strange operation.

I ran your script and all went smooth, and all problems were fixed. And python script magics were done.

You should consider, not consider your scripts as misleading.
By far ultra satisfactory answer.
Thank you!

---

### Post by talatnat on 2009-12-05
I had the same missing final newline problem -- after my RAM died and some fsck problems -- but the script fixed it. I got this error at the end:
-----------
added newline character to: /var/lib/dpkg/info/python-django.md5sums
added newline character to: /var/lib/dpkg/info/python-django.list
added newline character to: /var/lib/dpkg/info/console-setup.templates
Traceback (most recent call last):
  File "/home/jc/Desktop/newline_fixer.py", line 18, in <module>
    f = open(path, 'a+')
IOError: [Errno 13] Permission denied: '/var/lib/dpkg/info/file-roller.shlibs'
-----------

Still, everything worked, and I could install some new programs. Thanks.

---

### Post by Scol-R-LEA on 2009-12-19
I recently had this problem myself; however, in my case, the file was corrupted rather than simply truncated, so just adding a newline wasn't sufficient. For anyone with this problem who can't get it to work after running the script above (or getting errors afterwards), I recommend renaming or deleting the old list file and purging the package. You'll get a missing file error from dpkg, but it will let you remove the problem package. 

Either way, I'd recommend that you either purge or reinstall the package once you've cleared the dpkg failure, as there may be subtle faults in the truncated list file that wouldn't be evident immediately.

---

### Post by André Nascimento on 2010-07-19
Thank you for the script. He solved the same problem what happened in my debian lenny.

Regards

---

### Post by potrick on 2012-04-19
Meanwhile, in 2012, this script is still helping people. Thanks!

---

### Post by oldos2er on 2012-04-19
Old thread closed.

---

