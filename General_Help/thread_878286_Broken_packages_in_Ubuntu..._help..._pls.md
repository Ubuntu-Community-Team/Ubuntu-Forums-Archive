---
title: "Broken packages in Ubuntu... help... pls"
date: 2008-08-02
forum: General Help
---

### Post by lferree on 2008-08-02
Hello folks.  I'm not sure how to fix this, as I've tried fixing broken packages in synaptic and from boot.  I really was hoping to get freevo installed.  Please let me know what I can I try.  Thanks.


```
sudo apt-get install freevo
```

Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  freevo: Depends: python-freevo (= 1.7.6.1-1) but it is not going to be installed
E: Broken packages

```
sudo apt-get install python-freevo
```

The following packages have unmet dependencies:
  python-freevo: Depends: python-kaa-imlib2 (>= 0.2.2) but it is not going to be installed
                 Depends: python-kaa-metadata (>= 0.7.1) but it is not going to be installed
E: Broken packages

```
sudo apt-get install python-kaa-imlib2 python-kaa-metadata
```

The following packages have unmet dependencies:
  python-kaa-imlib2: Depends: python (< 2.5) but 2.5.2-0ubuntu1 is to be installed
                     Depends: python-kaa-base but it is not going to be installed
  python-kaa-metadata: Depends: python (< 2.5) but 2.5.2-0ubuntu1 is to be installed
                       Depends: python-kaa-base but it is not going to be installed
E: Broken packages

```
sudo apt-get install python-kaa-base
```

The following packages have unmet dependencies:
  python-kaa-base: Depends: python (< 2.5) but 2.5.2-0ubuntu1 is to be installed
E: Broken packages

---

### Post by tom66 on 2008-08-02
Open up System > Administration > Synaptic Package Manager, type your password (if necessary), and try Edit > Fix broken packages

---

### Post by prshah on 2008-08-02
> **lferree said:**
>   I really was hoping to get freevo installed.  Please let me know what I can I try.  Thanks.


Installing freevo in ubuntu with the repository version has a known problem. You can read more about it, as well as how to correctly install it [here.]("http://doc.freevo.org/FreevoAptUbuntu") (seems convoluted to me.)

---

### Post by lferree on 2008-08-05
Tom,

I did fix broken packages from both Synaptic and boot.  No dice.  :(

---

