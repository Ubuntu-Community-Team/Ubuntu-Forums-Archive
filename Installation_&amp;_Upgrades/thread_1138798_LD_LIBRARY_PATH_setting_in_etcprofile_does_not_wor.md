---
title: "LD_LIBRARY_PATH setting in /etc/profile does not work after upgrading to jaunty"
date: 2009-04-26
forum: Installation &amp; Upgrades
---

### Post by microbug on 2009-04-26
Hi all,

When I used intrepid, I put the following statement in /etc/profile to set the LD_LIBRARY_PATH variable

export LD_LIBRARY_PATH=some_path

And it worked fine. However, after upgrading to jaunty, the above statement seems not to work any more. Under jaunty, if I open a new terminal and enter

echo $LD_LIBRARY_PATH

it gives a blank path, instead of the path that I have set in /etc/profile. Does anyone have similar problems? Thanks a lot!

Eric

---

### Post by microbug on 2009-04-26
I found some interesting things about the problem.

If I add the following statement to /etc/profile

export TEST_PATH=some_path

then typing   echo $TEST_PATH   in a terminal will prints out correctly some_path, which means the environment variable TEST_PATH is successfully set. But  the statement

export LD_LIBRARY_PATH=some_path

has no effect. It seems that after the system sets the variable LD_LIBRARY_PATH to some_path according to /etc/profile, it is unset somewhere else. But I can't find out how it is unset. Anyone knows how it happens? Thanks again!


Eric

---

### Post by jbo5112 on 2009-07-16
After /etc/profile, some other init scripts get run, like /etc/bash.bashrc and ~/.bashrc.  They're probably (incorrectly) resetting the variable (export LD_LIBRARY_PATH="<path_list>"), instead of appending (export LD_LIBRARY_PATH="$LD_LIBRARY_PATH:<path_list>") or prepending (export LD_LIBRARY_PATH="<path_list>:$LD_LIBRARY_PATH") to the variable.  Type "man bash" into a terminal (or google) and looking at the INVOCATION section, if you want more details on the files used and their order.

---

