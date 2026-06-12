---
title: "My /etc/apt/sources.list is gone!"
date: 2008-07-18
forum: General Help
---

### Post by tomsa on 2008-07-18
I don't know why, but my repositories are broken.  When I go to System>Administration>Software Sources, nothing is marked
under the ubuntu tab.  I marked main, restricted, universe, and
multiverse and I get the following output:

"Could not download all Repository Indexes"

Followed by:

"E: Line 1 too long in source list /etc/apt/sources.list.
E: Unable to lock the list directory"

and then:

"E: Line 1 too long in source list /etc/apt/sources.list.
E: The list of sources could not be read.
Go to the repository dialog to correct the problem.
E: _cache->open() failed, please report."

I know that my network is working properly, so I checked the file itself with both gedit and nano.  It isn't there.   When I type the command in the terminal "sudo gedit
/etc/apt/sources.list"  I get the output "Could not open the file
/etc/apt/sources.list."

when I try the same with nano, I get a file with zero lines.  My medibuntu repositories are all there still, it seems at the moment.  does anyone know how I can restore my repositories?  I had been using main, universe, multiverse, and restricted.  Thanks!

---

### Post by hyper_ch on 2008-07-18
well, try this:

(1) find out the permissions on the sources.list
```

ls -al /etc/apt/sources.list

```

(2) move the sources.list
```

sudo mv /etc/apt/sources.list /etc/apt/sources.list.org

```

(3) create an empty one
```

sudo touch /etc/apt/sources.list

```

(4) set correct permissions
```

sudo chmod 0644 /etc/apt/sources.list

```

(5) start synaptic and check the according boxes

that should restore it (I think)

---

### Post by drs305 on 2008-07-18
If hyper_ch's method doesn't work, here's a hardy list to get you started if you want to use it:
```


deb http://archive.ubuntu.com/ubuntu/ hardy restricted multiverse universe main
# deb http://archive.linux.duke.edu/ubuntu/ hardy universe
## Uncomment the following two lines to add software from the 'backports'
## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
deb http://archive.canonical.com/ubuntu hardy partner
deb-src http://archive.canonical.com/ubuntu hardy partner
deb http://security.ubuntu.com/ubuntu/ hardy-security restricted multiverse universe main
# deb http://ppa.launchpad.net/fta/ubuntu hardy main
deb http://archive.ubuntu.com/ubuntu/ hardy-updates restricted multiverse universe main

```

---

### Post by tomsa on 2008-07-18
That did the trick-Thanks!

---

### Post by tomsa on 2008-07-30
Okay, I have new strange developments, now that I have finished driving the remote parts of the Alaska Highway and have returned to a place where I have internet access again. The process you listed for me worked, or so I thought when I last replied- it restored my repositories.  When I tried to update again after having restored my repositories, synaptic crashed and my repositories were broken again after restarting synaptic.  Do you have any ideas that might help?

---

### Post by tomsa on 2008-07-30
Pardon me, I should have given you better information than that. I tried repeating your process and running the recommended updates and got the following output:

```
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

```

So I ran ```
dpkg --configure -a
```

And got the following:

```
dpkg: dependency problems prevent configuration of hplip:
 hplip depends on hplip-data (>> 2.7.12); however:
  Package hplip-data is not installed.
 hplip depends on hplip-data (<< 2.7.12.1); however:
  Package hplip-data is not installed.
dpkg: error processing hplip (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 hplip

```

Is it just a matter of manually downloading and installing hplip-data and the running dpkg --configure -a again?

---

### Post by hyper_ch on 2008-07-30
try it with "sudo"

---

### Post by tomsa on 2008-07-30
I did do so with "sudo"  I may have fixed it- I'm not sure yet.  When I did run: 

```
sudo dpkg --configure -a
```

It told me that hplip and hplip-data were broken.  I thought I'd try running synaptic just to see if it would work and let me reinstall hplip and hplip-data.  When I tried to open synaptic, it gave me another error and told me to run:

```
 sudo apt-get install -f
```

So I did, and I restarted synaptic.  It seems to be working again- it is currently downloading updated packages for me, but I don't want to proclaim it fixed until the process is complete.  I will post again with the results!

---

### Post by hyper_ch on 2008-07-30
isn't it great that you actually get error messages that tell you what's wrong or what can be done to correct things?

---

### Post by tomsa on 2008-07-30
It is fantastic!  And it worked like a charm!!! Thanks!!!!!

---

### Post by derrick81787 on 2008-07-30
> **tomsa said:**
> It is fantastic!  And it worked like a charm!!! Thanks!!!!!

You should mark this thread as solved just as a courtesy to those who are looking to a solution to the same problem.

---

