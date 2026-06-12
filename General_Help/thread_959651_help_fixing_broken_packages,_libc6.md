---
title: "help fixing broken packages, libc6"
date: 2008-10-26
forum: General Help
---

### Post by gnychis on 2008-10-26
Hi,

I installed libc6_2.8~20080505-0ubuntu6_i386.deb to get a program to work, but it ended up breaking a lot of things in my system.  I am trying to rid it and go back to normal life.

When I try to install build-essential, I get:
```

# sudo apt-get install build-essential
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  build-essential: Depends: libc6-dev but it is not going to be installed or
                            libc-dev
                   Depends: g++ (>= 4:4.1.1) but it is not going to be installed
E: Broken packages

```

Then, trying to install libc-dev:
```

# apt-get install libc6-dev
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  libc6-dev: Depends: libc6 (= 2.7-10ubuntu4) but 2.8~20080505-0ubuntu6 is to be installed
E: Broken packages

```

Any ideas?

Thanks!
George

---

### Post by gnychis on 2008-10-28
bump

---

### Post by mc4man on 2008-10-28
You may or may not be able to downgrade libc6 successfully or easily. (may depend on what you've installed, updated since installing the higher version.

You could search libc6 in synaptic, choose 'force version' (under packages tab) and **see** what it wants to uninstall to downgrade.

I remember 4 similar instances last year - 2 op's just reinstalled without attempting downgrade, 1 was able to downgrade, 1 ended up with alot of problems.

Also *check* what aptitude reports, try 

sudo aptitude install libc6-dev

See what it says and what the score is (lower the better

For instance I just installed intrepid's libc6 version on a hardy install and was easily able to downgrade. (nothing else had been installed to cause problems


synaptic may want to fix broken packages first, ck. and see (under edit tab

---

