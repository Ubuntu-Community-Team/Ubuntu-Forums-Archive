---
title: "Can't run Update Manager"
date: 2009-03-05
forum: Installation &amp; Upgrades
---

### Post by KMJones1 on 2009-03-05
On trying to run Update Manager I get:

'E:Type ‘--12:14:16--’ is not known on line 1 in source list /etc/apt/sources.list.d/medibuntu.list, E:The list of sources could not be read.'

Synaptic Package Manager gives this error:

E: Type ‘--12:14:16--’ is not known on line 1 in source list /etc/apt/sources.list.d/medibuntu.list
E: The list of sources could not be read.
Go to the repository dialogue to correct the problem.
E: _cache->open() failed, please report.

Any suggestions please?
I am on Ubuntu 8.04, and it had been running happily for some time. This started when I tried to install something (forget details)for getting video and audio to work in Firefox.

Thanks for any ideas.

---

### Post by taurus on 2009-03-05
Looks like you tried to add the Medibuntu's repos but screw it up in the process.

Read this, [https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu).

If you want to install the plug-ins for firefox, just install the ubuntu-restricted-extras package.

```
sudo apt-get update
sudo apt-get install ubuntu-restricted-extras
```
Of course, you need to fix the error in your /etc/apt/sources.list.d/medibuntu.list (Medibuntu) first though.

---

### Post by KMJones1 on 2009-03-05
Thanks for this.
Here is my file medibuntu.list; what needs changing?

"--12:14:16--  [http://www.medibuntu.org/sources.list.d/hardy.list](http://www.medibuntu.org/sources.list.d/hardy.list)
           => `hardy.list'
Resolving [www.medibuntu.org](www.medibuntu.org)... 87.98.242.110
Connecting to [www.medibuntu.org|87.98.242.110|:80](www.medibuntu.org|87.98.242.110|:80)... connected.
HTTP request sent, awaiting response... 200 OK
Length: 226 [text/plain]

    0K                                                       100%   53.39 MB/s

12:14:16 (53.39 MB/s) - `hardy.list' saved [226/226]"

The file it is trying to read at [http://www.medibuntu.org/sources.list.d/hardy.list](http://www.medibuntu.org/sources.list.d/hardy.list) is:

## Medibuntu - Ubuntu 8.04 LTS "hardy heron"
## Please report any bug on [https://bugs.launchpad.net/medibuntu/](https://bugs.launchpad.net/medibuntu/)
deb [http://packages.medibuntu.org/](http://packages.medibuntu.org/) hardy free non-free
#deb-src [http://packages.medibuntu.org/](http://packages.medibuntu.org/) hardy free non-free


Thanks for any help

---

### Post by taurus on 2009-03-05
> **KMJones1 said:**
> Thanks for this.
Here is my file medibuntu.list; what needs changing?

[B][COLOR="Red"]"--12:14:16--  [http://www.medibuntu.org/sources.list.d/hardy.list](http://www.medibuntu.org/sources.list.d/hardy.list)
           => `hardy.list'
Resolving [www.medibuntu.org](www.medibuntu.org)... 87.98.242.110
Connecting to [www.medibuntu.org|87.98.242.110|:80](www.medibuntu.org|87.98.242.110|:80)... connected.
HTTP request sent, awaiting response... 200 OK
Length: 226 [text/plain]

    0K                                                       100%   53.39 MB/s

12:14:16 (53.39 MB/s) - `hardy.list' saved [226/226]"

The file it is trying to read at [http://www.medibuntu.org/sources.list.d/hardy.list](http://www.medibuntu.org/sources.list.d/hardy.list) is:
[/COLOR][/B]
## Medibuntu - Ubuntu 8.04 LTS "hardy heron"
## Please report any bug on [https://bugs.launchpad.net/medibuntu/](https://bugs.launchpad.net/medibuntu/)
deb [http://packages.medibuntu.org/](http://packages.medibuntu.org/) hardy free non-free
#deb-src [http://packages.medibuntu.org/](http://packages.medibuntu.org/) hardy free non-free


Thanks for any help

Edit /etc/apt/sources.list.d/medibuntu.list

```
gksudo gedit /etc/apt/sources.list.d/medibuntu.list
```
and remove everything in red so you would end up with only these lines.

```

## Medibuntu - Ubuntu 8.04 LTS "hardy heron"
## Please report any bug on https://bugs.launchpad.net/medibuntu/
deb http://packages.medibuntu.org/ hardy free non-free
#deb-src http://packages.medibuntu.org/ hardy free non-free

```
Save it and then run

```
sudo apt-get update
sudo apt-get upgrade
```

---

### Post by KMJones1 on 2009-03-05
That worked fine - many thanks for your help.:)
There were a lot of updates waiting to be installed!

---

